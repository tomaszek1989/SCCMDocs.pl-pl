---
title: "Wdrażanie systemu Windows za pośrednictwem sieci przy użyciu środowiska PXE"
titleSuffix: Configuration Manager
description: "Użyj wdrożeń systemu operacyjnego zainicjowanego przez środowisko PXE, aby odświeżyć systemu operacyjnego lub instalowanie nowej wersji systemu Windows na nowym komputerze."
ms.custom: na
ms.date: 06/15/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: da5f8b61-2386-4530-ad54-1a5c51911f07
caps.latest.revision: "19"
caps.handback.revision: "0"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 1ae9c9385abe90a38169f5d539be944f03817007
ms.sourcegitcommit: 08f9854fb6c6d21e1e923b13e38a64d0bc2bc9a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2017
---
# <a name="use-pxe-to-deploy-windows-over-the-network-with-system-center-configuration-manager"></a>Użyj środowiska PXE, aby wdrożyć system Windows przez sieć przy użyciu programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Wdrożenia systemu operacyjnego w kliencie let System Center Configuration Manager komputerów żądania i wdrażanie systemów operacyjnych za pośrednictwem sieci inicjowane ze środowiska wykonawczego przed uruchomieniem systemu (PXE). W tym scenariuszu wdrażania możesz wysłać obrazu systemu operacyjnego i obrazy rozruchowe Windows PE x86 i x64 do punktu dystrybucji skonfigurowanego do akceptowania żądań rozruchu środowiska PXE.

> [!NOTE]  
>  Podczas tworzenia wdrożenia systemu operacyjnego tego cele x64 tylko komputerów z systemem BIOS zarówno x64 rozruchu obrazu i x86 obrazu rozruchowego musi być dostępna w punkcie dystrybucji.

Wdrożenia systemu operacyjnego inicjowane przez środowisko PXE mogą być używane w następujących scenariuszach wdrażania systemu operacyjnego:

-   [Odświeżanie istniejącego komputera za pomocą nowej wersji systemu Windows](refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [Instalowanie nowej wersji systemu Windows na nowym komputerze (od zera)](install-new-windows-version-new-computer-bare-metal.md)  

Wykonaj kroki jednego ze scenariuszy wdrażania systemu operacyjnego, a następnie użyj poniższych sekcji w celu przygotowania do wdrożeń inicjowanych ze środowiska PXE.

##  <a name="BKMK_Configure"></a> Konfigurowanie co najmniej jednego punktu dystrybucji tak, aby akceptował żądania środowiska PXE
Aby wdrożyć systemy operacyjne klientów, którzy tworzą żądania rozruchu środowiska PXE, należy użyć co najmniej jednego punktu dystrybucji skonfigurowanego do reagowania na żądania rozruchu środowiska PXE. Aby uzyskać instrukcje dotyczące włączania obsługi środowiska PXE w punkcie dystrybucji, zobacz [Konfigurowanie punktów dystrybucji do akceptowania PXE żądań](../get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_PXEDistributionPoint).

## <a name="prepare-a-pxe-enabled-boot-image"></a>Przygotowanie obrazu rozruchowego obsługującego środowisko PXE
Aby używać środowiska PXE do wdrażania systemu operacyjnego, należy umieścić obrazy rozruchowe obsługujące środowisko PXE (zarówno te w wersji x86, jak i te w wersji x64) w co najmniej jednym punkcie dystrybucji z włączoną funkcją PXE. Korzystając z udostępnionych informacji, włącz obsługę środowiska PXE w obrazie rozruchowym i roześlij go do punktów dystrybucji:

-   Aby włączyć funkcję PXE dla obrazu rozruchowego, wybierz **Wdróż ten obraz rozruchowy z punktu dystrybucji z włączoną obsługą środowiska PXE** z **źródła danych** we właściwościach obrazu rozruchowego.

-   Jeśli zmienisz właściwości obrazu rozruchowego, należy ponownie rozesłać obraz rozruchowy do punktów dystrybucji. Aby uzyskać więcej informacji, zobacz [dystrybucji zawartości](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_distribute).

##  <a name="BKMK_PXEExclusionList"></a> Tworzenie listy wykluczeń dla wdrożeń środowiska PXE
Podczas wdrażania systemów operacyjnych w środowisku PXE, można utworzyć listę wykluczeń w każdym punkcie dystrybucji. Dodaj adresy MAC do listy wykluczeń komputery, które mają być ignorowane przez punkt dystrybucji. Komputery z listy nie będzie odbierać sekwencje zadań wdrożenia używanych do wdrożenia środowiska PXE programu Configuration Manager.

#### <a name="to-create-the-exclusion-list"></a>Aby utworzyć listę wykluczeń

1.  Utwórz plik tekstowy na punkcie dystrybucji, który ma włączoną funkcję PXE. Nazwij ten plik na przykład **pxeExceptions.txt**.

2.  Użyj edytora tekstowego, takiego jak Notatnik i Dodaj adresy MAC komputerów, które mają być ignorowane przez punkt dystrybucji z włączoną obsługą środowiska PXE. Oddziel wartości adresów MAC dwukropkami i wprowadzaj każdy adres w osobnym wierszu. Na przykład: `01:23:45:67:89:ab`

3.  Zapisz plik tekstowy na serwerze systemu lokacji punktu dystrybucji z włączoną funkcją PXE. Plik tekstowy może zapisać do dowolnej lokalizacji na serwerze.

4.  Edytuj rejestr punktu dystrybucji z włączoną obsługą środowiska PXE można utworzyć **MACIgnoreListFile** klucza rejestru. Dodaj wartość ciągu pełnej ścieżki do pliku tekstowego na serwerze systemu lokacji punktu dystrybucji z włączoną obsługą środowiska PXE. Użyj poniższej ścieżki rejestru:

     **HKLM\Software\Microsoft\SMS\DP**  

    > [!WARNING]  
    >  Używanie Edytora rejestru w niewłaściwy sposób może spowodować poważne problemy, które może być konieczna ponowna instalacja systemu operacyjnego. Firma Microsoft nie może zagwarantować użytkownikowi, że uda się rozwiązać problemy wynikające z niewłaściwego używania Edytora rejestru. Używasz Edytora rejestru na własne ryzyko.

     Nie jest konieczne ponowne uruchomienie serwera po wprowadzeniu tej zmiany rejestru.

##  <a name="BKMK_RamDiskTFTP"></a>Rozmiar bloku RamDisk TFTP i rozmiaru okna
Można dostosować rozmiar bloku RamDisk TFTP, a począwszy od wersji programu 1606 wersji programu Configuration Manager, rozmiar okna dla punktów dystrybucji z włączoną obsługą środowiska PXE. Jeśli skonfigurowano sieć, może to powodować niepowodzenie pobrania obrazu rozruchowego z błędem przekroczenia limitu czasu, ponieważ rozmiar bloku lub okna jest zbyt duży. Dostosowanie rozmiaru bloku i rozmiaru okna RamDisk TFTP umożliwia zoptymalizowanie ruchu TFTP w środowisku PXE w celu spełnienia określonych wymagań sieciowych. Należy przetestować dostosowane ustawienia w danym środowisku, aby określić najbardziej wydajne. Aby uzyskać więcej informacji, zobacz [dostosować rozmiar bloku RamDisk TFTP i rozmiaru okna w punktach dystrybucji obsługujących środowisko PXE](../get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_RamDiskTFTP).

## <a name="configure-deployment-settings"></a>Konfigurowanie ustawień wdrażania
Aby można było użyć wdrożenia systemu operacyjnego zainicjowanego przez środowisko PXE, należy skonfigurować wdrożenie w celu udostępnienia systemu operacyjnego na użytek żądań rozruchu środowiska PXE. Istnieje możliwość skonfigurowania dostępnych systemów operacyjnych w **ustawienia wdrażania** strony Kreatora wdrażania oprogramowania lub **ustawienia wdrażania** we właściwościach wdrożenia. Dla ustawienia **Udostępnij dla następujących** wybierz jedną z poniższych wartości:

-   Klienci programu Configuration Manager, nośniki i PXE

-   Tylko nośniki i PXE

-   Tylko nośniki i PXE (ukryte)

##  <a name="BKMK_Deploy"></a> Wdrażanie sekwencji zadań
Wdróż system operacyjny w kolekcji docelowej. Aby uzyskać więcej informacji, zobacz [Wdrażanie sekwencji zadań](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS). Podczas wdrażania systemów operacyjnych za pomocą środowiska PXE możesz określić, czy wdrożenie jest wymagane, czy dostępne.

-   **Wdrożenie wymagane**: Wymagane użycie wdrożeń środowiska PXE bez jakiejkolwiek interwencji użytkownika. Użytkownik nie będzie mógł ominąć rozruchu PXE. Jednak jeśli użytkownik anuluje rozruch PXE przed punkt dystrybucji ma odpowiadać, nie będzie można wdrożyć system operacyjny.

-   **Wdrożenie dostępne**: Wdrożeń dostępnych wymagają, czy użytkownik musi być obecny przy komputerze docelowym, aby ich można nacisnąć klawisz F12 w celu kontynuowania procesu rozruchu PXE. Jeśli użytkownik na naciśnie klawisza F12, komputer uruchomi bieżący system operacyjny lub wykona rozruch z kolejnego dostępnego urządzenia rozruchowego.

Można ponownie wdrożyć wymagane wdrożenie PXE, czyszcząc stan poprzedniego wdrożenia PXE przypisane do komputera lub kolekcji programu Configuration Manager. Ta akcja resetuje stan tego wdrożenia i instaluje ponownie ostatnie wymagane wdrożenie.

> [!IMPORTANT]
> Protokół PXE nie jest bezpieczny. Upewnij się, że serwer PXE i klient PXE znajdują się w fizycznie zabezpieczonej sieci, na przykład w centrum danych, aby zapobiec nieautoryzowanemu dostępowi do lokacji.

##  <a name="how-is-the-boot-image-selected-for-clients-booting-with-pxe"></a>Jak zaznaczono obraz rozruchowy dla klientów rozruchu w środowisku PXE
Gdy klient jest uruchamiany w środowisku PXE, Configuration Manager udostępnia klientowi korzystanie z obrazem rozruchowym. Począwszy od programu Configuration Manager 1606 wersji programu Configuration Manager używa obrazu rozruchowego z architektury dokładnego dopasowania. Jeśli obraz rozruchowy z architekturą dokładne nie jest dostępna, program Configuration Manager używa obrazu rozruchowego z architekturą zgodne. Poniższa lista zawiera szczegółowe informacje dotyczące sposobu obraz rozruchowy jest zaznaczone dla klientów rozruchu w środowisku PXE.
1. Menedżer konfiguracji wygląda w bazie danych lokacji dla danego adresu MAC lub SMBIOS klienta, który próbuje uruchomić rekordu systemu.  

    > [!NOTE]
    > Jeśli komputer, który jest przypisany do lokacji jest uruchamiany w środowisku PXE do innej lokacji, zasady nie są widoczne dla komputera. Na przykład, jeśli klient jest już przypisany do lokacji A, punkt zarządzania i punkt dystrybucji dla lokacji B nie będzie można uzyskać dostępu do zasady z lokacji A. Klient nie będzie pomyślnie rozruchu w środowisku PXE.

2. Configuration Manager poszukuje sekwencje zadań, które są wdrażane do rekordu systemu w kroku 1.

3. Na liście w punkcie 2 sekwencji zadań programu Configuration Manager szuka obrazu rozruchowego odpowiadającego architekturze klienta, która próbuje go uruchomić. Jeśli obraz rozruchowy zostanie znaleziony o takiej samej architekturze, że obraz rozruchowy jest używany.

4. Jeśli nie ma obrazu rozruchowego z taką samą architekturę, programu Configuration Manager szuka obraz rozruchowy, który jest zgodna z architekturą klienta. Wygląda na liście w punkcie 2 sekwencji zadań. Na przykład klient 64-bitowy jest zgodny z obrazów rozruchowych 32-bitowe i 64-bitowych. 32-bitowego klienta jest zgodny z tylko obrazy rozruchowe 32-bitowych. Klient z interfejsem UEFI jest zgodny z tylko obrazy rozruchowe 64-bitowych.
