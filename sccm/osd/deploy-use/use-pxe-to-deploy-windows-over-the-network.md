---
title: "Użyj środowiska PXE do wdrażania systemu Windows za pośrednictwem sieci | Dokumentacja firmy Microsoft"
description: "Odśwież systemu operacyjnego lub zainstalować nową wersję systemu Windows na nowym komputerze, należy użyć wdrożenia systemu operacyjnego zainicjowanego przez środowisko PXE."
ms.custom: na
ms.date: 12/07/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: da5f8b61-2386-4530-ad54-1a5c51911f07
caps.latest.revision: 19
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f44505c977b511223a083a960f871371c0ff133
ms.openlocfilehash: b22cdbd42693078caa47f41182ce73ea881c3515
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="use-pxe-to-deploy-windows-over-the-network-with-system-center-configuration-manager"></a>Użyj środowiska PXE, aby wdrożyć system Windows przez sieć przy użyciu programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Wdrożenia systemu operacyjnego zainicjowanego przez środowisko PXE w programie System Center Configuration Manager pozwalają komputerom klienckim żądania i wdrażanie systemów operacyjnych za pośrednictwem sieci. W tym scenariuszu wdrażania systemu operacyjnego obraz systemu operacyjnego i obrazy rozruchowe systemu Windows PE (x86 i x64) są wysyłane do punktu dystrybucji skonfigurowanego do przyjmowania żądań rozruchu środowiska PXE.  

> [!NOTE]  
>  W przypadku tworzenia wdrożenia systemu operacyjnego przeznaczonego tylko dla komputerów z systemem BIOS typu x64 w punkcie dystrybucji muszą być dostępne obrazy rozruchowe dla platform x64 i x86.  

 Wdrożenia systemu operacyjnego inicjowane przez środowisko PXE mogą być używane w następujących scenariuszach wdrażania systemu operacyjnego:  

-   [Odśwież istniejącego komputera z nowej wersji systemu Windows](refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [Zainstaluj nową wersję systemu Windows na nowym komputerze (od zera)](install-new-windows-version-new-computer-bare-metal.md)  

 Wykonaj procedurę jednego ze scenariuszy wdrażania systemu operacyjnego, a następnie użyj poniższych sekcji w celu przygotowania się do wdrożeń inicjowanych przez środowisko PXE.  

##  <a name="BKMK_Configure"></a> Konfigurowanie co najmniej jednego punktu dystrybucji tak, aby akceptował żądania środowiska PXE  
 Do wdrażania systemów operacyjnych klientów programu Configuration Manager, uniemożliwiających żądania rozruchu środowiska PXE, należy użyć jednego lub więcej punktów dystrybucji skonfigurowanych do odpowiadania na żądania rozruchu środowiska PXE.  Kroki włączyć obsługę środowiska PXE w punkcie dystrybucji, można znaleźć w temacie [Konfigurowanie punktów dystrybucji do akceptowania PXE żądań](../get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_PXEDistributionPoint).  

## <a name="prepare-a-pxe-enabled-boot-image"></a>Przygotowanie obrazu rozruchowego obsługującego środowisko PXE  
 Aby używać środowiska PXE do wdrażania systemu operacyjnego, należy umieścić obrazy rozruchowe obsługujące środowisko PXE (zarówno te w wersji x86, jak i te w wersji x64) w co najmniej jednym punkcie dystrybucji z włączoną funkcją PXE. Korzystając z udostępnionych informacji, włącz obsługę środowiska PXE w obrazie rozruchowym i roześlij go do punktów dystrybucji:  

-   Aby włączyć obsługę środowiska PXE dla obrazu rozruchowego, wybierz pozycję  **Wdróż ten obraz rozruchowy z punktu dystrybucji obsługującego PXE** na karcie **Źródło danych** we właściwościach obrazu rozruchowego.  

-   Jeśli zmienisz właściwości obrazu rozruchowego, wykonaj jego ponowną dystrybucję do punktów dystrybucji. Aby uzyskać więcej informacji, zobacz [dystrybucji zawartości](../../core/servers/deploy/configure/deploy-and-manage-content.md#a-namebkmkdistributea-distribute-content).  

##  <a name="BKMK_PXEExclusionList"></a> Tworzenie listy wykluczeń dla wdrożeń środowiska PXE  
 Podczas wdrażania systemów operacyjnych przy użyciu środowiska PXE można utworzyć listę wykluczeń w każdym punkcie dystrybucji, która umożliwia ignorowanie żądań rozruchu środowiska PXE pochodzących z komputerów znajdujących się na tej liście. Lista wykluczeń zawiera adresy MAC komputerów, które mają być ignorowane przez punkt dystrybucji. Te komputery nie będą otrzymywać sekwencji zadań wdrażania, które program Configuration Manager używa wdrożenia w środowisku PXE.  

 Aby utworzyć listę wykluczeń PXE, należy wykonać poniższe czynności.  

#### <a name="to-create-the-exclusion-list"></a>Aby utworzyć listę wykluczeń  

1.  Utwórz plik tekstowy na punkcie dystrybucji, który ma włączoną funkcję PXE. Nazwij ten plik na przykład **pxeExceptions.txt**.  

2.  Użyj standardowego edytora tekstu, takiego jak Notatnik, i dodaj adresy MAC komputerów, które mają być ignorowane przez punkt dystrybucji z włączoną funkcją PXE. Oddziel wartości adresów MAC dwukropkami i wprowadzaj każdy adres w osobnym wierszu. Na przykład: `01:23:45:67:89:ab`  

3.  Zapisz plik tekstowy na serwerze systemu lokacji punktu dystrybucji z włączoną funkcją PXE. Plik tekstowy możesz zapisać w dowolnej lokalizacji na serwerze.  

4.  Edytuj rejestr punktu dystrybucji z włączoną funkcją PXE, aby utworzyć klucz rejestru **MACIgnoreListFile** zawierający wartość ciągu pełnej ścieżki do lokalizacji pliku tekstowego na serwerze systemu lokacji punktu dystrybucji z włączoną funkcją PXE. Użyj poniższej ścieżki rejestru:  

     **HKLM\Software\Microsoft\SMS\DP**  

    > [!WARNING]  
    >  Używanie Edytora rejestru w niewłaściwy sposób może spowodować poważne problemy, w wyniku których może być konieczna ponowna instalacja systemu operacyjnego. Firma Microsoft nie może zagwarantować użytkownikowi, że uda się rozwiązać problemy wynikające z niewłaściwego używania Edytora rejestru. Używasz Edytora rejestru na własne ryzyko.  

     Nie jest konieczne ponowne uruchomienie serwera po wprowadzeniu tej zmiany rejestru.  

##  <a name="BKMK_RamDiskTFTP"></a>Rozmiar bloku RamDisk TFTP i rozmiaru okna  
Można dostosować rozmiar bloku RamDisk TFTP, a począwszy od programu Configuration Manager w wersji 1606, rozmiar okna dla punktów dystrybucji z włączoną obsługą środowiska PXE. Jeśli skonfigurowano sieć, może to powodować niepowodzenie pobrania obrazu rozruchowego z błędem przekroczenia limitu czasu, ponieważ rozmiar bloku lub okna jest zbyt duży. Dostosowanie rozmiaru bloku i rozmiaru okna RamDisk TFTP umożliwia zoptymalizowanie ruchu TFTP w środowisku PXE w celu spełnienia określonych wymagań sieciowych. Aby określić najbardziej wydajne rozwiązanie, należy przetestować dostosowane ustawienia w swoim środowisku. Aby uzyskać więcej informacji, zobacz [dostosować rozmiar bloku RamDisk TFTP i rozmiaru okna w punktach dystrybucji z włączoną obsługą środowiska PXE](../get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_RamDiskTFTP).

## <a name="configure-deployment-settings"></a>Konfigurowanie ustawień wdrażania  
 Aby można było użyć wdrożenia systemu operacyjnego zainicjowanego przez środowisko PXE, należy skonfigurować wdrożenie w celu udostępnienia systemu operacyjnego na użytek żądań rozruchu środowiska PXE. Tę konfigurację można określić na stronie **Ustawienia wdrożenia** Kreatora wdrażania oprogramowania lub na karcie **Ustawienia wdrożenia** we właściwościach wdrożenia.  Dla ustawienia **Udostępnij dla następujących** wybierz jedną z poniższych wartości:  

-   Klienci programu Configuration Manager, nośniki i PXE  

-   Tylko nośniki i PXE  

-   Tylko nośniki i PXE (ukryte)  

##  <a name="BKMK_Deploy"></a> Wdrażanie sekwencji zadań  
 Wdróż system operacyjny w kolekcji docelowej. Aby uzyskać więcej informacji, zobacz [Wdrażanie sekwencji zadań](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS). Podczas wdrażania systemów operacyjnych za pomocą środowiska PXE możesz określić, czy wdrożenie jest wymagane, czy dostępne.  

-   **Wdrożenie wymagane**: Wdrożenia wymagane używają środowiska PXE bez jakiejkolwiek interwencji użytkownika. Użytkownik nie będzie mógł ominąć rozruchu PXE. Jeśli jednak użytkownik anuluje rozruch PXE przed odebraniem odpowiedzi z punktu dystrybucji, system operacyjny nie zostanie wdrożony.  

-   **Wdrożenie dostępne**: Dostępne wdrożenia wymagają, czy użytkownik jest obecny przy komputerze docelowym, tak aby nacisnąć klawisz F12 w celu kontynuowania procesu rozruchu PXE. Jeśli użytkownik na naciśnie klawisza F12, komputer uruchomi bieżący system operacyjny lub wykona rozruch z kolejnego dostępnego urządzenia rozruchowego.  

 Można ponownie wdrożyć wymagane wdrożenie PXE, czyszcząc stan poprzedniego wdrożenia PXE przypisanego do komputera lub kolekcji programu Configuration Manager. Ta akcja resetuje stan tego wdrożenia i ponownie wdraża ostatnie wymagane wdrożenie.  

> [!IMPORTANT]  
>  Protokół PXE nie jest bezpieczny. Upewnij się, że serwer PXE i klient PXE znajdują się w fizycznie zabezpieczonej sieci, na przykład w centrum danych, aby zapobiec nieautoryzowanemu dostępowi do lokacji.  

##  <a name="how-is-the-boot-image-selected-for-clients-booting-with-pxe"></a>Jak obraz rozruchowy jest zaznaczone dla klientów rozruchu w środowisku PXE
Gdy klient uruchamia się przy użyciu środowiska PXE, Configuration Manager udostępnia do użytku przez klienta z obrazem rozruchowym. Począwszy od programu Configuration Manager 1606 wersji programu Configuration Manager używa obrazu rozruchowego z architektura dokładne dopasowanie, jeśli jest dostępny. Jeśli obraz rozruchowy z architekturą dokładną nie jest dostępna, program Configuration Manager używa obraz rozruchowy z architekturą zgodne. Poniższa lista zawiera szczegółowe informacje dotyczące sposobu obraz rozruchowy jest zaznaczone dla klientów rozruchu w środowisku PXE.
1. Menedżer konfiguracji wygląda w bazie danych lokacji dla danego adresu MAC lub SMBIOS klienta, który próbuje uruchomić rekordu systemu.
    > [!NOTE]
    > Jeśli komputer, który jest przypisany do lokacji rozruchu w środowisku PXE witryny differenet, zasady nie są widoczne dla komputera. Na przykład jeśli klient jest już przypisany do lokacji A, punkt zarządzania i punktu dystrybucji w lokacji B nie będą mogli uzyskać dostęp do zasad z lokacji klienta i zostanie pomyślnie rozruchu w środowisku PXE.
2. Program Configuration Manager poszukuje sekwencje zadań, które są wdrażane do rekordu systemu znalezione w kroku 1.
3. Na liście w punkcie 2 sekwencji zadań obraz rozruchowy, który pasuje do architektury klienta, który próbuje uruchomić szuka programu Configuration Manager. Jeśli obraz rozruchowy zostanie znaleziony o takiej samej architekturze, ten obraz rozruchowy jest używany.

4. Jeśli nie można odnaleźć obrazu rozruchowego z tym samym architecuture, Configuration Manager szuka obrazu rozruchowego (z listy sekwencji zadań w punkcie 2) zgodny z architekturą klienta, który próbuje uruchomić. Na przykład 64-bitowego klienta jest zgodny z obrazów rozruchowych 32-bitowych i 64-bitowych. 32-bitowy klient jest zgodny z tylko obrazy rozruchowe 32-bitowych. Klient z interfejsem UEFI jest zgodny z tylko obrazy rozruchowe 64-bitowych.

