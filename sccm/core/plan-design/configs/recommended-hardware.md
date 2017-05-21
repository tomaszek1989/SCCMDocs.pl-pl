---
title: "Zalecany sprzęt | Dokumentacja firmy Microsoft"
description: "Uzyskaj zalecenia sprzętu, aby ułatwić skalowanie środowiska programu System Center Configuration Manager poza podstawowe wdrażanie."
ms.custom: na
ms.date: 05/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5267f0af-34d3-47a0-9ab8-986c41276e6c
caps.latest.revision: 26
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 212628639300e9c361f7cee61b3df6b1cb6874ce
ms.openlocfilehash: 8dac6df60b07461d6410d305723b3f03fb09fa16
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="recommended-hardware-for-system-center-configuration-manager"></a>Zalecany sprzęt dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Poniższe zalecenia znajdują się wytyczne ułatwiające skalowania środowiska programu System Center Configuration Manager do obsługi więcej niż wykraczającego poza podstawowe wdrażanie lokacji, systemami lokacji i klientów. Zalecenia te nie odnoszą się do wszystkich możliwych konfiguracji lokacji i hierarchii.  

 Zamieszczono informacje w poniższych sekcjach jako wytyczne ułatwiające Planowanie sprzętu, które mogą spełniać obciążenie przetwarzania dla klientów i witryn, które korzystają z domyślnymi konfiguracjami dostępne funkcje programu Configuration Manager.  


##  <a name="bkmk_ScaleSieSystems"></a>Systemy lokacji  
 Ta sekcja zawiera konfiguracje sprzętu zalecane dla programu Configuration Manager systemów lokacji w przypadku wdrożeń, które obsługują maksymalna liczba klientów i używać większości lub wszystkich funkcji programu Configuration Manager. Wdrożenia, które obsługują mniej niż maksymalna liczba klientów i nie używać wszystkich dostępnych funkcji mogą wymagać mniej zasobów komputera. Zasadniczo kluczowe czynniki ograniczające wydajność całego systemu są następujące (w podanej kolejności):  

1.  Wydajność we/wy dysku  

2.  Dostępna pamięć  

3.  CPU  

Aby uzyskać najlepszą wydajność należy używać konfiguracji RAID 10 dla wszystkich dysków danych i sieci Ethernet 1 GB.  

###  <a name="bkmk_ScaleSiteServer"></a>Serwery lokacji  

|Autonomiczna lokacja główna|Procesor (rdzenie)|Pamięć (GB)|Alokacja pamięci dla programu SQL Server (%)|  
|-------------------------------|---------------|---------------|----------------------------------------|  
|Serwer z rolą bazy danych lokacji na tym samym serwerze<sup>1</sup>|16|96|80|  
|Serwer autonomicznej lokacji głównej ze zdalną bazą danych lokacji|8|16|-|  
|Serwer zdalnej bazy danych dla autonomicznej lokacji głównej|16|72|90|  
|Serwer centralnej lokacji administracyjnej z rolą bazy danych lokacji na tym samym serwerze<sup>1</sup>|20|128|80|  
|Serwer centralnej lokacji administracyjnej ze zdalną bazą danych lokacji|8|16|-|  
|Serwer zdalnej bazy danych dla centralnej lokacji administracyjnej|16|96|90|  
|Podrzędna lokacja główna z rolą bazy danych lokacji na tym samym serwerze|16|96|80|  
|Serwer podrzędnej lokacji głównej ze zdalną bazą danych lokacji|8|16|-|  
|Serwer zdalnej bazy danych dla podrzędnej lokacji głównej|16|72|90|  
|Serwer lokacji dodatkowej|8|16|-|  

 <sup>1</sup> serwera lokacji i programu SQL Server są zainstalowane na tym samym komputerze, wdrożenie obsługuje maksymalną [numery zmiany rozmiaru i skali](/sccm/core/plan-design/configs/size-and-scale-numbers) lokacji oraz klientów. Jednak taka konfiguracja może ograniczyć [opcje wysokiej dostępności dla programu System Center Configuration Manager](/sccm/protect/understand/high-availability-options), podobnie jak przy użyciu klastra programu SQL Server. Ponadto ze względu na wyższe wymagania we/wy, które są potrzebne do obsługi programu SQL Server i serwer lokacji programu Configuration Manager, jeśli są uruchomione na tym samym komputerze, to warto rozważyć użycie konfiguracji z komputera zdalnego programu SQL Server, wdrożenie większych.  

###  <a name="bkmk_RemoteSiteSystem"></a>Serwery zdalnego systemu lokacji  
 Poniższe wskazówki jest przeznaczony dla komputerów, które mają jedną rolę systemu lokacji. Zaplanuj wprowadzanie korekt, jeśli instalowanych jest wiele ról systemu lokacji na tym samym komputerze.  

|Rola systemu lokacji|Procesor (rdzenie)|Pamięć (GB)|Miejsce na dysku (GB)|  
|----------------------|---------------|---------------|--------------------|  
|Punkt zarządzania|4|8|50|  
|Punkt dystrybucji|2|8|Wymagany przez system operacyjny i do przechowywania zawartości, którą można wdrożyć|  
|Katalog aplikacji z usługą sieci web i witryną sieci web na komputerze systemu lokacji|4|16|50|  
|Punkt aktualizacji oprogramowania<sup>1</sup>|8|16|Wymagany przez system operacyjny i Zapisz aktualizacje, które można wdrożyć|  
|Wszystkie inne role systemu lokacji|4|8|50|  

 <sup>1</sup> komputer, który obsługuje punkt aktualizacji oprogramowania wymaga następującej konfiguracji dla puli aplikacji IIS:  

-   Zwiększ **długość kolejki WsusPool** do **2000**.  

-   Zwiększ **limit pamięci prywatnej WsusPool** przez 4 godziny, lub ustaw ją na **0** (nieograniczona).  

###  <a name="bkmk_DiskSpace"></a>Miejsce na dysku dla systemów lokacji  
 Przydział dysku i konfiguracji przyczynia się do wydajności programu Configuration Manager. Ponieważ każdego środowiska programu Configuration Manager są różne, wartości, które należy zaimplementować może różnić się od przedstawionych w tym temacie.  

 Aby uzyskać najlepszą wydajność, wszystkie obiekty powinny być umieszczone na oddzielnych dedykowanych woluminach macierzy RAID. Wszystkie woluminy danych (program Configuration Manager i jego pliki bazy danych) Aby uzyskać najlepszą wydajność w macierzy RAID 10.  

|Użycie danych|Minimalna przestrzeń dyskowa|25 000 klientów|50 000 klientów|100 000 klientów|150 000 klientów|Klienci 700,000 (centralnej lokacji administracyjnej)|  
|----------------|------------------------|--------------------|--------------------|---------------------|---------------------|-----------------------------------------------------|  
|System operacyjny|Patrz wskazówki dotyczące systemu operacyjnego.|Patrz wskazówki dotyczące systemu operacyjnego.|Patrz wskazówki dotyczące systemu operacyjnego.|Patrz wskazówki dotyczące systemu operacyjnego.|Patrz wskazówki dotyczące systemu operacyjnego.|Patrz wskazówki dotyczące systemu operacyjnego.|  
|Pliki dziennika i aplikacji programu Configuration Manager|25 GB|50 GB|100 GB|200 GB|300 GB|200 GB|  
|Plik *.mdf bazy danych lokacji|75 GB na każde 25 000 klientów|75 GB|150 GB|300 GB|500 GB|2 TB|  
|Plik *.ldf bazy danych lokacji|25 GB na każde 25 000 klientów|25 GB|50 GB|100 GB|150 GB|100 GB|  
|Tymczasowe pliki bazy danych (*.mdf i *.ldf)|W razie potrzeby|W razie potrzeby|W razie potrzeby|W razie potrzeby|W razie potrzeby|W razie potrzeby|  
|Zawartość (udziały punktu dystrybucji)|W razie potrzeby<sup>1</sup>|W razie potrzeby<sup>1</sup>|W razie potrzeby<sup>1</sup>|W razie potrzeby<sup>1</sup>|W razie potrzeby<sup>1</sup>|W razie potrzeby<sup>1</sup>|  

 <sup>1</sup> wskazówki dotyczące przestrzeni dyskowej nie obejmuje miejsca wymaganego dla zawartości, która znajduje się w bibliotece zawartości w punktach dystrybucji lub serwerze lokacji. Aby uzyskać informacje dotyczące planowania biblioteki zawartości, zobacz [The content library](../../../core/plan-design/hierarchy/the-content-library.md) (Biblioteka zawartości).  

 Oprócz tej wskazówki podczas planowania związanego z wymogami przestrzeni dyskowej należy także uwzględnić następujące wytyczne:  

-   Każdy klient wymaga około 5 MB miejsca.  

-   Podczas planowania rozmiaru tymczasowej bazy danych lokacji głównej, planowanie łączny rozmiar, 25% do 30% pliku *.mdf bazy danych lokacji. Rzeczywisty rozmiar może być znacznie mniejszy lub większy — zależy od wydajności serwera lokacji oraz objętości przychodzących danych za pośrednictwem długie i krótkie okresy.  

    > [!NOTE]  
    >  Podczas 50 000 lub więcej klientów w lokacji należy zaplanować używanie co najmniej cztery Temp pliki .mdf bazy danych.  

-   Rozmiar tymczasowej bazy danych w centralnej lokacji administracyjnej jest zwykle znacznie mniejszy niż w lokacji głównej.  

-   Ograniczenia rozmiaru bazy danych lokacji dodatkowej są następujące:  

    -   Program SQL Server 2012 Express: 10 GB  

    -   Program SQL Server 2014 Express: 10 GB  

##  <a name="bkmk_ScaleClient"></a>Klienci  
 Ta sekcja zawiera konfiguracje sprzętu zalecane dla komputerów, którymi można zarządzać przy użyciu oprogramowania klienckiego programu Configuration Manager.  

### <a name="client-for-windows-computers"></a>Klient dla komputerów z systemem Windows  
 Minimalne wymagania dla komputerów opartych na systemie Windows, którymi można zarządzać za pomocą Menedżera konfiguracji, w tym osadzone systemy operacyjne są następujące:  

-   **Procesora i pamięci:** Zobacz procesora i wymagania dotyczące pamięci RAM dla systemu operacyjnego na komputerze.  

-   **Miejsce na dysku:** 500 MB dostępnego miejsca na dysku, zalecane dla pamięci podręcznej klienta programu Configuration Manager 5 GB. Mniej miejsca na dysku jest wymagany, jeśli używasz dostosowane ustawienia do instalowania klienta programu Configuration Manager:  

    -   Aby uniknąć instalowania plików, które nie wymagają klienta, należy użyć /skipprereq właściwość wiersza polecenia programu CCMSetup. Na przykład uruchomić **CCMSetup.exe /skipprereq:silverlight.exe** , jeśli klient nie korzystają z katalogu aplikacji.  

    -   Ustaw mniejszy niż domyślny (5120 MB) rozmiar pliku pamięci podręcznej za pomocą właściwości Client.msi SMSCACHESIZE. Rozmiar minimalny to 1 MB. Na przykład polecenie **CCMSetup.exe SMSCachesize=2** tworzy pamięć podręczną o rozmiarze 2 MB.  

    Aby uzyskać więcej informacji o tych właściwościach instalacji klienta, zobacz [Informacje o właściwościach instalacji klientów w programie System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties.md).  

    > [!TIP]  
    >  Zainstalowanie klienta z minimalną ilością wolnego miejsca jest przydatne w przypadku urządzeń z systemem Windows Embedded, które zazwyczaj mają mniejsze rozmiary dysku niż standardowe komputery z systemem Windows.  



 Poniżej przedstawiono dodatkowe minimalne wymagania sprzętowe dla opcjonalne funkcje w programie Configuration Manager.  

-   **Wdrożenie systemu operacyjnego:** 384 MB pamięci RAM  

-   **Software Center:** Procesor 500 MHz  

-   **Zdalne sterowanie:** Pentium 4 Hyper-Threaded 3 GHz (jednym rdzeniu) lub porównywalny procesor CPU, z co najmniej 1 GB pamięci RAM dla możliwości optymalnego  

### <a name="client-for-linux-and-unix"></a>Klient dla systemu Linux i UNIX  
 Poniżej przedstawiono minimalne wymagania dotyczące serwerów Linux i UNIX, którymi można zarządzać za pomocą programu Configuration Manager.  

|Wymaganie|Szczegóły|  
|-----------------|-------------|  
|Procesor i pamięć|Zobacz procesora i wymagania dotyczące pamięci RAM dla systemu operacyjnego.|  
|Miejsce na dysku|500 MB dostępnego miejsca na dysku, zalecane dla pamięci podręcznej klienta programu Configuration Manager 5 GB.|  
|Łączność sieciowa|Komputery klienckie programu Configuration Manager musi mieć połączenie sieciowe do systemów lokacji programu Configuration Manager, aby włączyć zarządzanie.|  

##  <a name="bkmk_ScaleConsole"></a>Konsola programu Configuration Manager  
 Wymagania przedstawione w poniższej tabeli mają zastosowanie do każdego komputera, na którym jest uruchomiona konsola programu Configuration Manager.  

 **Minimalnej konfiguracji sprzętowej:**  

-   Procesor CPU Intel i3 lub porównywalny  

-   2 GB pamięci RAM  

-   2 GB miejsca na dysku  

|Ustawienie DPI|Minimalna rozdzielczość|  
|-----------------|------------------------|  
|96 / 100%|1024 x 768|  
|120 / 125%|1280 x 960|  
|144 / 150%|1600 x 1200|  
|196 / 200%|2500 x 1600|  

 **Pomoc techniczna dla programu PowerShell:**  

 Po zainstalowaniu obsługi środowiska PowerShell na komputerze, na którym jest uruchomiona konsola programu Configuration Manager, można uruchomić polecenia cmdlet programu PowerShell na tym komputerze do zarządzania programu Configuration Manager.

 - PowerShell 3.0 lub nowszej jest obsługiwana.

Oprócz programu PowerShell Windows Management Framework (WMF) w wersji 3.0 lub nowszej jest obsługiwana.   


##  <a name="bkmk_ScaleLab"></a>Wdrożenia laboratorium  
 Użyj poniższe zalecenia minimalne wymagania dotyczące sprzętu dla laboratorium i testowania wdrożenia programu Configuration Manager. Te zalecenia dotyczą wszystkich typów lokacji, maksymalnie 100 klientów:  

|Rola|Procesor (rdzenie)|Pamięć (GB)|Miejsce na dysku (GB)|  
|----------|---------------|-------------------|-----------------------|  
|Serwer lokacji i bazy danych|2 - 4|7 - 12|100|  
|Serwer systemu lokacji|1 - 4|2 - 4|50|  
|Klient|1 - 2|1 - 3|30|  

