---
title: "Zadania sekwencji kroki, aby zarządzać systemu BIOS z interfejsem UEFI konwersji | Programu Configuration Manager"
description: "Dowiedz się, jak dostosować sekwencję zadań wdrażania systemu operacyjnego na przygotowanie partycji FAT32 przejścia do UEFI."
ms.custom: na
ms.date: 03/24/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bd3df04a-902f-4e91-89eb-5584b47d9efa
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 528ce515c86c4e778532290026a90a46476c4576
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="task-sequence-steps-to-manage-bios-to-uefi-conversion"></a>Kroki sekwencji zadań do zarządzania systemem BIOS do konwersji UEFI
Windows 10 udostępnia wiele nowych funkcji zabezpieczeń, które wymagają urządzenia z włączoną obsługą interfejsu UEFI. Konieczne może być nowoczesnych komputerów z systemem Windows, które obsługują interfejs UEFI, ale używana jest starszy system BIOS. Konwertowanie urządzenia na UEFI są wymagane przejdź do każdego komputera na partycje dysk twardy, a następnie ponownie skonfigurować oprogramowanie układowe. Za pomocą sekwencji zadań w programie Configuration Manager, można przygotować dysk twardy dla systemu BIOS do konwersji UEFI, konwertowanie systemu BIOS na UEFI w ramach procesu uaktualniania w miejscu i zbierać informacje z interfejsem UEFI w ramach spisu sprzętu.

## <a name="hardware-inventory-collects-uefi-information"></a>Spisu sprzętu zbiera informacje z interfejsem UEFI
Począwszy od wersji 1702, spisu sprzętu nowej klasy (**SMS_Firmware**), a właściwość (**UEFI**) są dostępne pomóc w określeniu, czy komputer jest uruchamiany w trybie UEFI. Gdy komputer jest uruchamiany w trybie UEFI, **UEFI** właściwość jest ustawiona na **TRUE**. Ta opcja jest włączona w spisie sprzętu, domyślnie. Aby uzyskać więcej informacji dotyczących zapasów sprzętu, zobacz [jak skonfigurować spis sprzętu](/sccm/core/clients/manage/inventory/configure-hardware-inventory).

## <a name="create-a-custom-task-sequence-to-prepare-the-hard-drive-for-bios-to-uefi-conversion"></a>Utwórz niestandardową sekwencję zadań do przygotowywanie dysku twardego systemu BIOS z interfejsem UEFI konwersji
Począwszy od programu Configuration Manager w wersji 1610 Dostosuj sekwencję zadań wdrażania systemu operacyjnego z nową zmienną TSUEFIDrive, dzięki czemu **Uruchom ponownie komputer** krok przygotuje FAT32 partycji na dysku twardym przejścia do UEFI. Poniższa procedura zawiera przykładowy sposób tworzenia kroków sekwencji zadań, aby przygotować dysk twardy dla systemu BIOS z interfejsem UEFI konwersji.

### <a name="to-prepare-the-fat32-partition-for-the-conversion-to-uefi"></a>Aby przygotować partycji FAT32 do konwersji na UEFI:
W istniejącej sekwencji zadań instalacji systemu operacyjnego doda nową grupę prostych kroków, czy system BIOS z interfejsem UEFI konwersji.

1. Utwórz grupę sekwencji zadań po wykonaniu kroków przechwytywania plików i ustawień, a przed kroki, aby zainstalować system operacyjny. Na przykład utworzyć grupę po **przechwytywania plików i ustawień** grupę o nazwie **systemu BIOS-UEFI**.
2. Na **opcje** kartę nowej grupy, należy dodać zmienną sekwencji zadań jako warunek gdzie **_SMSTSBootUEFI** jest **równa** do **true**. Zapobiega to uruchomiony, gdy komputer jest już w trybie UEFI kroków w grupie.

  ![System BIOS z interfejsem UEFI grupy](../../core/get-started/media/BIOS-to-UEFI-group.png)
3. W ramach nowej grupy, należy dodać **Uruchom ponownie komputer** krok sekwencji zadań. W **Określ, co uruchomić po ponownym uruchomieniu**, wybierz pozycję **obraz rozruchowy przypisany do tej sekwencji zadań jest zaznaczone** do uruchomienia komputera w środowisku Windows PE.  
4. Na **opcje** , Dodaj zmienną sekwencji zadań jako warunek gdzie **_SMSTSInWinPE jest równa false**. Zapobiega to uruchomiony, jeśli komputer jest już w systemie Windows PE w tym kroku.

  ![Uruchom ponownie komputer kroku](../../core/get-started/media/restart-in-windows-pe.png)
5. Dodaj krok, aby uruchomić narzędzie OEM przekonwertuje oprogramowanie układowe BIOS z interfejsem UEFI. Są to zazwyczaj **Uruchom wiersz polecenia** krok sekwencji zadań przy użyciu wiersza polecenia, aby uruchomić narzędzie OEM.
6. Dodaj krok sekwencji zadań Formatuj partycję dysk i partycje i sformatowanie dysku twardego. W kroku wykonaj następujące czynności:
  1. Utwórz partycję FAT32, który zostanie przekonwertowany na UEFI, przed zainstalowaniem systemu operacyjnego. Wybierz **GPT** dla **typ dysku**.
    ![Format i partycji dysku kroku](../media/format-and-partition-disk.png)
  2. Przejdź do właściwości partycji FAT32. Wprowadź **TSUEFIDrive** w **zmiennej** pola. Jeśli sekwencja zadań wykryje tej zmiennej, przygotuj przejścia z interfejsem UEFI przed ponownym uruchomieniem komputera.
    ![Właściwości partycji.](../../core/get-started/media/partition-properties.png)
  3. Utwórz partycję NTFS, używaną przez aparat sekwencji zadań można zapisać stanu i do przechowywania plików dziennika.
7. Dodaj **Uruchom ponownie komputer** krok sekwencji zadań. W **Określ, co uruchomić po ponownym uruchomieniu**, wybierz pozycję **obraz rozruchowy przypisany do tej sekwencji zadań jest zaznaczone** do uruchomienia komputera w środowisku Windows PE.  

## <a name="convert-from-bios-to-uefi-during-an-in-place-upgrade"></a>Konwertowanie systemu BIOS na UEFI podczas uaktualniania w miejscu
Windows 10 twórców aktualizacji wprowadzono narzędzie konwersji proste automatyzuje proces ponownego podziału dysku twardego z obsługą interfejsu UEFI sprzętu i integruje narzędzia konwersji system Windows 7 do procesu uaktualniania w miejscu systemu Windows 10. Połączenie to narzędzie z sekwencji zadań uaktualniania systemu operacyjnego i narzędzie OEM, który konwertuje oprogramowanie układowe BIOS z interfejsem UEFI, można przekonwertować komputerów z systemem BIOS na UEFI podczas uaktualniania w miejscu do systemu Windows 10 twórców aktualizacji.

**Wymagania dotyczące**:
- Aktualizacja twórców systemu Windows 10
- Komputery, które obsługują interfejs UEFI
- Narzędzie OEM, który konwertuje oprogramowania układowego komputera z systemem BIOS z interfejsem UEFI

### <a name="to-convert-from-bios-to-uefi-during-an-in-place-upgrade"></a>Aby przekonwertować z systemu BIOS z interfejsem UEFI podczas uaktualniania w miejscu
1. Tworzenie sekwencji zadań uaktualniania systemu operacyjnego, który wykonuje uaktualnienie w miejscu do systemu Windows 10 twórców aktualizacji.
2. Przeprowadź edycję sekwencji zadań. W **grupy przetwarzanie końcowe**, Dodaj następujące kroki sekwencji zadań:
   1. W ogólności, dodać **Uruchom wiersz polecenia** kroku. W wierszu polecenia zostaną dodane do MBR2GPT narzędzia tego konwertuje dysk z MBR na GPT bez modyfikowania lub usuwania danych z dysku. W wierszu polecenia wpisz następujące polecenie:  **MBR2GPT Defragmentuj /disk:0 /AllowFullOS**. Można również uruchomić MBR2GPT. Narzędzie EXE w przypadku systemu Windows PE, a nie w pełnym systemie operacyjnym. Można to zrobić, dodając krok ponownego uruchomienia komputera w środowisku WinPE przed wykonaniem kroku, aby uruchomić MBR2GPT. Narzędzie EXE i usunięcie /AllowFullOS opcji wiersza polecenia. Szczegółowe informacje na temat narzędzia i dostępnych opcjach, zobacz [MBR2GPT. EXE](https://technet.microsoft.com/itpro/windows/deploy/mbr-to-gpt).
   2. Dodaj krok, aby uruchomić narzędzie OEM przekonwertuje oprogramowanie układowe BIOS z interfejsem UEFI. Są to zazwyczaj krok sekwencji zadań Uruchom wiersz polecenia z wiersza polecenia, aby uruchomić narzędzie OEM.
   3. W ogólności, dodać **Uruchom ponownie komputer** kroku. Określ co uruchomić po ponownym uruchomieniu, wybierz opcję **aktualnie zainstalowany domyślny system operacyjny**.
3. Wdróż sekwencję zadań.
