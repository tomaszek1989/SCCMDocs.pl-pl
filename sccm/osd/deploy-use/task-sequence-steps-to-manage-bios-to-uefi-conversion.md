---
title: "W celu zarządzania systemu BIOS z interfejsem UEFI konwersji | Program Configuration Manager"
description: "Dowiedz się, jak dostosować sekwencję zadań wdrażania systemu operacyjnego przygotować partycji FAT32 do przejścia na UEFI."
ms.custom: na
ms.date: 03/24/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bd3df04a-902f-4e91-89eb-5584b47d9efa
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: ae008c91a7387ba76f2bfac13f8feb489a0cc558
ms.openlocfilehash: 528ce515c86c4e778532290026a90a46476c4576
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="task-sequence-steps-to-manage-bios-to-uefi-conversion"></a>Kroki sekwencji zadań w celu zarządzania systemu BIOS z interfejsem UEFI konwersji
System Windows 10 zawiera wiele nowych funkcji zabezpieczeń wymaganych przez urządzenia z obsługą interfejsu UEFI. Konieczne może być nowoczesnych komputery z systemem Windows, obsługiwać interfejs UEFI, ale są za pomocą starszego systemu BIOS. Konwertowanie urządzenia na UEFI musi przejść do każdego komputera, na partycje dysk twardy, a następnie skonfigurować oprogramowanie układowe. Za pomocą sekwencji zadań w programie Configuration Manager, można przygotować dysk twardy do systemu BIOS do konwersji UEFI, konwersji z systemu BIOS z interfejsem UEFI w ramach procesu uaktualniania w miejscu i zbierać informacje z interfejsem UEFI w ramach spisu sprzętu.

## <a name="hardware-inventory-collects-uefi-information"></a>Spis sprzętu zbiera informacje z interfejsem UEFI
Począwszy od wersji 1702, spisu sprzętu nowej klasy (**SMS_Firmware**) i właściwości (**UEFI**) są dostępne w celu określenia, czy komputer jest uruchamiany w trybie UEFI. Kiedy komputer jest uruchamiany w trybie UEFI, **UEFI** właściwość jest ustawiona na **TRUE**. To jest domyślnie włączona w programie spisu sprzętu. Aby uzyskać więcej informacji na temat zapasów sprzętu, zobacz [Konfigurowanie spisu sprzętu](/sccm/core/clients/manage/inventory/configure-hardware-inventory).

## <a name="create-a-custom-task-sequence-to-prepare-the-hard-drive-for-bios-to-uefi-conversion"></a>Utwórz niestandardową sekwencję zadań przed rozpoczęciem dysku twardego dla systemu BIOS z interfejsem UEFI konwersji
Począwszy od programu Configuration Manager w wersji 1610 teraz można dostosować sekwencję zadań wdrażania systemu operacyjnego za pomocą nowej zmiennej TSUEFIDrive, tak aby **Uruchom ponownie komputer** krok przygotuje FAT32 partycji na dysku twardym przejścia do UEFI. Poniższa procedura zawiera przykładowy sposób tworzenia kroki sekwencji zadań, aby przygotować dysk twardy do systemu BIOS z interfejsem UEFI konwersji.

### <a name="to-prepare-the-fat32-partition-for-the-conversion-to-uefi"></a>Aby przygotować partycji FAT32 do konwersji na UEFI:
W istniejącej sekwencji zadań w celu zainstalowania systemu operacyjnego dodasz nową grupę czynności BIOS z interfejsem UEFI konwersji.

1. Utwórz nową grupę sekwencji zadań, po kroki, aby przechwytywać pliki i ustawienia, a przed czynności w celu zainstalowania systemu operacyjnego. Na przykład utwórz grupę po **Przechwyć pliki i ustawienia** grupy o nazwie **z systemu BIOS z interfejsem UEFI**.
2. Na **opcje** kartę w nowej grupie, należy dodać zmienną sekwencji zadań jako warunek gdzie **_SMSTSBootUEFI** jest **jest równa** do **true**. Zapobiega to uruchomione, gdy komputer jest już w trybie UEFI czynności w grupie.

  ![System BIOS z interfejsem UEFI grupy](../../core/get-started/media/BIOS-to-UEFI-group.png)
3. W ramach nowej grupy, należy dodać **Uruchom ponownie komputer** sekwencji zadań. W **Określ, co uruchomić po ponownym uruchomieniu**, wybierz opcję **obraz rozruchowy przypisany do tej sekwencji zadań jest wybrane** do uruchomienia komputera w środowisku Windows PE.  
4. Na **opcje** , Dodaj zmienną sekwencji zadań jako warunek gdzie **_SMSTSInWinPE jest równa false**. Ten krok to zapobiega uruchamianiu, jeśli komputer jest już w środowisku Windows PE.

  ![Uruchom ponownie komputer](../../core/get-started/media/restart-in-windows-pe.png)
5. Dodaj krok, aby uruchomić narzędzie OEM, który przekonwertuje oprogramowania sprzętowego BIOS z interfejsem UEFI. Są to zazwyczaj **Uruchom wiersz polecenia** sekwencji zadań przy użyciu wiersza polecenia, aby uruchomić narzędzie OEM.
6. Dodaj krok sekwencji zadań Formatuj dysk partycji i podzielić na partycje i sformatuj dysk twardy. W kroku wykonaj następujące czynności:
  1. Utwórz partycję FAT32, który zostanie przekonwertowany na UEFI, przed zainstalowaniem systemu operacyjnego. Wybierz **GPT** dla **dysku typu**.
    ![Format i partycji dysku kroku](../media/format-and-partition-disk.png)
  2. Przejdź do właściwości partycji FAT32. Wprowadź **TSUEFIDrive** w **zmiennej** pola. Jeśli sekwencja zadań wykryje tej zmiennej, przygotuje przejścia UEFI przed ponownym uruchomieniem komputera.
    ![Właściwości partycji.](../../core/get-started/media/partition-properties.png)
  3. Utwórz partycję NTFS wykorzystującym aparat sekwencji zadań do zapisania stanu do przechowywania plików dziennika.
7. Dodaj **Uruchom ponownie komputer** sekwencji zadań. W **Określ, co uruchomić po ponownym uruchomieniu**, wybierz opcję **obraz rozruchowy przypisany do tej sekwencji zadań jest wybrane** do uruchomienia komputera w środowisku Windows PE.  

## <a name="convert-from-bios-to-uefi-during-an-in-place-upgrade"></a>Konwersji z systemu BIOS z interfejsem UEFI podczas uaktualnienia w miejscu
Windows 10 twórcy aktualizacji wprowadzono konwersji proste narzędzie, które automatyzuje proces na partycje dysk twardy sprzęt obsługujący UEFI i narzędzie konwersji integruje się z systemu Windows 7 do procesu uaktualniania w miejscu systemu Windows 10. Podczas tego narzędzia można połączyć z sekwencji zadań uaktualnienia systemu operacyjnego i narzędzia OEM, która konwertuje oprogramowania sprzętowego BIOS z interfejsem UEFI, można przekonwertować komputerów z systemem BIOS z interfejsem UEFI podczas uaktualniania w miejscu do usługi Windows Update twórców 10.

**Wymagania dotyczące**:
- Aktualizacja twórców systemu Windows 10
- Komputery, które obsługują UEFI
- Narzędzie OEM, który konwertuje oprogramowania układowego komputera z systemem BIOS z interfejsem UEFI

### <a name="to-convert-from-bios-to-uefi-during-an-in-place-upgrade"></a>Konwersji z systemu BIOS z interfejsem UEFI podczas uaktualnienia w miejscu
1. Tworzenie sekwencji zadań uaktualnienia systemu operacyjnego, która przeprowadza uaktualnienie w miejscu do usługi Windows Update twórców 10.
2. Edytowanie sekwencji zadań. W **przetwarzania końcowego grupy**, Dodaj następujące kroki:
   1. Z ogólne, dodać **Uruchom wiersz polecenia** kroku. Należy dodać wiersz polecenia dla MBR2GPT narzędzia tego opcja dysk z MBR na GPT bez modyfikowania lub usuwania danych z dysku. W wierszu polecenia wpisz następujące polecenie:  **MBR2GPT Defragmentuj /disk:0 /AllowFullOS**. Można również uruchomić MBR2GPT. Narzędzie EXE w przypadku systemu Windows PE, a nie w pełnym systemie operacyjnym. Można to zrobić, dodając krok, aby ponownie uruchomić komputer przed wykonaniem kroku do uruchamiania MBR2GPT środowiska WinPE. Narzędzie EXE i usunięcie opcji /AllowFullOS z wiersza polecenia. Szczegółowe informacje na temat narzędzia i dostępnych opcji, zobacz [MBR2GPT. EXE](https://technet.microsoft.com/itpro/windows/deploy/mbr-to-gpt).
   2. Dodaj krok, aby uruchomić narzędzie OEM, który przekonwertuje oprogramowania sprzętowego BIOS z interfejsem UEFI. Są to zazwyczaj sekwencji zadań Uruchom wiersz polecenia z wiersza polecenia, aby uruchomić narzędzie OEM.
   3. Z ogólne, dodać **Uruchom ponownie komputer** kroku. Określ co uruchomić po ponownym uruchomieniu, wybierz opcję **aktualnie zainstalowany domyślny system operacyjny**.
3. Wdrożenie sekwencji zadań.

