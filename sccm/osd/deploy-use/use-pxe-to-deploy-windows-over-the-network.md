---
title: Użyj środowiska PXE do wdrożenia systemu operacyjnego za pośrednictwem sieci
titleSuffix: Configuration Manager
description: Wdrożenia inicjowane ze środowiska PXE systemu operacyjnego za pomocą Odśwież systemu operacyjnego lub instalowanie nowej wersji systemu Windows na nowym komputerze.
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: da5f8b61-2386-4530-ad54-1a5c51911f07
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: deb8321400eac4085cefca8686f2703cea5f659a
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="use-pxe-to-deploy-windows-over-the-network-with-system-center-configuration-manager"></a>Użyj środowiska PXE, aby wdrożyć system Windows przez sieć przy użyciu programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Środowisko wykonawcze przed uruchomieniem systemu (PXE)-inicjowane wdrożeń systemu operacyjnego w programie Configuration Manager zezwala klientom na żądanie i wdrażanie systemów operacyjnych za pośrednictwem sieci. W tym scenariuszu wdrażania możesz wysłać obrazu systemu operacyjnego i obrazy rozruchowe do punktu dystrybucji obsługującego środowisko PXE.

> [!NOTE]  
>  Podczas tworzenia wdrożenia systemu operacyjnego tego cele x64 tylko komputerów z systemem BIOS zarówno x64 rozruchu obrazu i x86 obrazu rozruchowego musi być dostępna w punkcie dystrybucji.

Wdrożenia inicjowane ze środowiska PXE systemu operacyjnego można użyć w następujących scenariuszach:

-   [Odświeżanie istniejącego komputera za pomocą nowej wersji systemu Windows](refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [Instalowanie nowej wersji systemu Windows na nowym komputerze (od zera)](install-new-windows-version-new-computer-bare-metal.md)  

Wykonaj kroki jednego ze scenariuszy wdrażania systemu operacyjnego, a następnie użyj sekcji w tym artykule w celu przygotowania do wdrożeń inicjowanych ze środowiska PXE.



##  <a name="BKMK_Configure"></a> Konfigurowanie co najmniej jednego punktu dystrybucji tak, aby akceptował żądania środowiska PXE
Aby wdrożyć systemy operacyjne klientów programu Configuration Manager, które żądania rozruchu środowiska PXE, należy skonfigurować co najmniej jeden punkt dystrybucji do akceptowania żądań PXE. Po skonfigurowaniu punktu dystrybucji ma odpowiadać na żądania rozruchu środowiska PXE i określa odpowiedniej akcji wdrażania do wykonania. Aby uzyskać więcej informacji, zobacz [zainstalować lub zmodyfikować punkt dystrybucji](../../core/servers/deploy/configure/install-and-configure-distribution-points.md#pxe).  



## <a name="prepare-a-pxe-enabled-boot-image"></a>Przygotowanie obrazu rozruchowego obsługującego środowisko PXE
Aby używać środowiska PXE do wdrażania systemu operacyjnego, musi mieć x x86 i x64 obrazy rozruchowe obsługujące środowisko PXE dystrybuowana do co najmniej jeden punkt dystrybucji z włączoną obsługą środowiska PXE. Korzystając z udostępnionych informacji, włącz obsługę środowiska PXE w obrazie rozruchowym i roześlij go do punktów dystrybucji:

-   Aby włączyć funkcję PXE dla obrazu rozruchowego, wybierz **Wdróż ten obraz rozruchowy z punktu dystrybucji z włączoną obsługą środowiska PXE** z **źródła danych** we właściwościach obrazu rozruchowego.

-   Jeśli zmienisz właściwości obrazu rozruchowego, należy ponownie rozesłać obraz rozruchowy do punktów dystrybucji. Aby uzyskać więcej informacji, zobacz [dystrybucji zawartości](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_distribute).



##  <a name="BKMK_PXEExclusionList"></a> Tworzenie listy wykluczeń dla wdrożeń środowiska PXE
Podczas wdrażania systemów operacyjnych w środowisku PXE, można utworzyć listę wykluczeń w każdym punkcie dystrybucji. Dodaj adresy MAC do listy wykluczeń komputery, które mają być ignorowane przez punkt dystrybucji. Wymienione komputery nie odbierają sekwencji zadań wdrożenia używanych do wdrożenia środowiska PXE programu Configuration Manager.

#### <a name="to-create-the-exclusion-list"></a>Aby utworzyć listę wykluczeń

1.  Utwórz plik tekstowy na punkcie dystrybucji, który ma włączoną funkcję PXE. Nazwij ten plik na przykład **pxeExceptions.txt**.

2.  Użyj edytora tekstowego, takiego jak Notatnik i Dodaj adresy MAC komputerów, które mają być ignorowane przez punkt dystrybucji z włączoną obsługą środowiska PXE. Oddziel wartości adresów MAC dwukropkami i wprowadzaj każdy adres w osobnym wierszu. Na przykład: `01:23:45:67:89:ab`

3.  Zapisz plik tekstowy na serwerze systemu lokacji punktu dystrybucji z włączoną funkcją PXE. Plik tekstowy może zapisać do dowolnej lokalizacji na serwerze.

4.  Edytuj rejestr punktu dystrybucji z włączoną obsługą środowiska PXE można utworzyć **MACIgnoreListFile** klucza rejestru. Dodaj wartość ciągu pełnej ścieżki do pliku tekstowego na serwerze systemu lokacji punktu dystrybucji z włączoną obsługą środowiska PXE. Użyj poniższej ścieżki rejestru:

     **HKLM\Software\Microsoft\SMS\DP**  

    > [!WARNING]  
    >  Używanie Edytora rejestru w niewłaściwy sposób może spowodować poważne problemy, które może być konieczna ponowna instalacja systemu operacyjnego. Firma Microsoft nie może zagwarantować użytkownikowi, że uda się rozwiązać problemy wynikające z niewłaściwego używania Edytora rejestru. Używasz Edytora rejestru na własne ryzyko.

     Nie jest konieczne ponowne uruchomienie serwera po wprowadzeniu tej zmiany rejestru.



## <a name="manage-duplicate-hardware-identifiers"></a>Zarządzanie sprzętu zduplikowane identyfikatory
Configuration Manager może rozpoznać wielu komputerów jako tego samego urządzenia, jeśli mają zduplikowane atrybuty SMBIOS lub użyj karty sieci udostępnionej. Aby uniknąć tych problemów, należy sprzętu zduplikowane identyfikatory w ustawieniach hierarchii zarządzania. Aby uzyskać więcej informacji, zobacz [Zarządzaj sprzętu zduplikowane identyfikatory](/sccm/core/clients/manage/manage-clients#manage-duplicate-hardware-identifiers).



##  <a name="BKMK_RamDiskTFTP"></a>Rozmiar bloku RamDisk TFTP i rozmiaru okna
Można dostosować rozmiar bloku i okna RamDisk TFTP dla punktów dystrybucji z włączoną obsługą środowiska PXE. Duży rozmiar bloku lub okna dostosowaną sieci, może spowodować pobrania obrazu rozruchowego z błędem przekroczenia limitu czasu. Dostosowywanie rozmiaru bloku i okna RamDisk TFTP pozwalają na zoptymalizowanie ruchu TFTP przy użyciu środowiska PXE w celu spełnienia określonych wymagań sieciowych. Aby ustalić, jakie konfiguracja jest najbardziej wydajnym, należy przetestować dostosowane ustawienia w danym środowisku. Aby uzyskać więcej informacji, zobacz [dostosować rozmiar bloku RamDisk TFTP i rozmiaru okna w punktach dystrybucji obsługujących środowisko PXE](../get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_RamDiskTFTP).



## <a name="configure-deployment-settings"></a>Konfigurowanie ustawień wdrażania
Aby użyć inicjowanych ze środowiska PXE wdrożenia systemu operacyjnego, należy skonfigurować wdrożenie w celu udostępnienia systemu operacyjnego dla żądań rozruchu środowiska PXE. Skonfiguruj dostępnych systemów operacyjnych na **ustawienia wdrażania** we właściwościach wdrożenia. Aby uzyskać **Udostępnij dla następujących** ustawienia, wybierz jedną z następujących opcji:

-   Klienci programu Configuration Manager, nośniki i PXE

-   Tylko nośniki i PXE

-   Tylko nośniki i PXE (ukryte)



##  <a name="BKMK_Deploy"></a> Wdrażanie sekwencji zadań
Wdrażanie systemu operacyjnego w kolekcji docelowej. Aby uzyskać więcej informacji, zobacz [Wdrażanie sekwencji zadań](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS). Podczas wdrażania systemów operacyjnych za pomocą środowiska PXE możesz określić, czy wdrożenie jest wymagane, czy dostępne.

-   **Wdrożenie wymagane**: Wymagane użycie wdrożeń środowiska PXE bez jakiejkolwiek interwencji użytkownika. Użytkownik nie może ominąć rozruchu PXE. Jednak jeśli użytkownik anuluje rozruch PXE przed punkt dystrybucji ma odpowiadać, system operacyjny nie jest wdrożony.

-   **Wdrożenie dostępne**: Wdrożeń dostępnych wymagają, aby użytkownik musi być obecny przy komputerze docelowym. Użytkownik musi nacisnąć klawisz F12 w celu kontynuowania procesu rozruchu PXE. Jeśli użytkownik nie jest na naciśnie klawisza F12, komputer jest uruchamiany na bieżący system operacyjny lub z kolejnego dostępnego urządzenia rozruchowego.

Można ponownie wdrożyć wymagane wdrożenie PXE, czyszcząc stan poprzedniego wdrożenia PXE przypisane do komputera lub kolekcji programu Configuration Manager. Aby uzyskać więcej informacji na temat **wyczyść wymagane wdrożenia PXE** akcji, zobacz [zarządzać klientami](/sccm/core/clients/manage/manage-clients#BKMK_ManagingClients_DevicesNode) lub [Zarządzanie kolekcjami](/sccm/core/clients/manage/collections/manage-collections#how-to-manage-device-collections). Ta akcja resetuje stan tego wdrożenia i instaluje ponownie ostatnie wymagane wdrożenie.

> [!IMPORTANT]
> Protokół PXE nie jest bezpieczny. Upewnij się, że serwer PXE i klient PXE znajdują się w fizycznie zabezpieczonej sieci, na przykład w centrum danych, aby zapobiec nieautoryzowanemu dostępowi do lokacji.



##  <a name="how-is-the-boot-image-selected-for-clients-booting-with-pxe"></a>Jak zaznaczono obraz rozruchowy dla klientów rozruchu w środowisku PXE
Gdy klient jest uruchamiany w środowisku PXE, Configuration Manager udostępnia klientowi korzystanie z obrazem rozruchowym. Program Configuration Manager używa obrazu rozruchowego z architektury dokładnego dopasowania. Jeśli obraz rozruchowy z architekturą dokładne nie jest dostępna, program Configuration Manager używa obrazu rozruchowego z architekturą zgodne. Poniższa lista zawiera szczegółowe informacje dotyczące sposobu obraz rozruchowy jest zaznaczone dla klientów rozruchu w środowisku PXE.
1. Menedżer konfiguracji wygląda w bazie danych lokacji dla danego adresu MAC lub SMBIOS klienta, który próbuje uruchomić rekordu systemu.  

    > [!NOTE]
    > Jeśli komputer, który jest przypisany do lokacji jest uruchamiany w środowisku PXE do innej lokacji, zasady nie są widoczne dla komputera. Na przykład jeśli klient jest już przypisany do lokacji A, punkt zarządzania i punkt dystrybucji dla lokacji B nie ma dostępu zasady z lokacji A. Klient nie pomyślnie rozruchu w środowisku PXE.

2. Configuration Manager poszukuje sekwencje zadań, które są wdrażane do rekordu systemu w kroku 1.

3. Na liście w punkcie 2 sekwencji zadań programu Configuration Manager szuka obrazu rozruchowego odpowiadającego architekturze klienta, która próbuje go uruchomić. Jeśli obraz rozruchowy zostanie znaleziony o takiej samej architekturze, że obraz rozruchowy jest używany.

4. Jeśli nie ma obrazu rozruchowego z taką samą architekturę, programu Configuration Manager szuka obraz rozruchowy, który jest zgodna z architekturą klienta. Wygląda na liście w punkcie 2 sekwencji zadań. Na przykład klient 64-bitowy jest zgodny z obrazów rozruchowych 32-bitowe i 64-bitowych. 32-bitowego klienta jest zgodny z tylko obrazy rozruchowe 32-bitowych. Klient z interfejsem UEFI jest zgodny z tylko obrazy rozruchowe 64-bitowych.
