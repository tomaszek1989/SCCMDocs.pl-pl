---
title: "Zalecany sprzęt"
titleSuffix: Configuration Manager
description: "Pobierz zalecenia dotyczące sprzętu, aby ułatwić skalowanie poza podstawowego wdrożenia środowiska System Center Configuration Manager."
ms.custom: na
ms.date: 05/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 5267f0af-34d3-47a0-9ab8-986c41276e6c
caps.latest.revision: "26"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 696dd4e1812954e78eca55881bd992e304caba32
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="recommended-hardware-for-system-center-configuration-manager"></a>Zalecany sprzęt dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Poniższe zalecenia to wytyczne do stosowania podczas skalowania środowiska programu System Center Configuration Manager w celu obsługi ponad wykraczającego poza podstawowe wdrażanie lokacji, systemami lokacji i klientów. Zalecenia te nie odnoszą się do wszystkich możliwych konfiguracji lokacji i hierarchii.  

 Skorzystaj z informacji w poniższych sekcjach przedstawiono wskazówki pomocne dla sprzętu, które mogą spełniać obciążeniem przetwarzania dla klientów i lokacji korzystających z dostępnych funkcji programu Configuration Manager z domyślnymi konfiguracjami.  


##  <a name="bkmk_ScaleSieSystems"></a>Systemy lokacji  
 Ta sekcja zawiera konfiguracje sprzętu zalecane dla programu Configuration Manager systemów lokacji w przypadku wdrożeń, które obsługuje maksymalną liczbę klientów i używać większości lub wszystkich funkcji programu Configuration Manager. Wdrożenia, które obsługuje mniej niż maksymalna liczba klientów i nie używać wszystkich dostępnych funkcji mogą wymagać mniejszej liczby zasobów komputera. Zasadniczo kluczowe czynniki ograniczające wydajność całego systemu są następujące (w podanej kolejności):  

1.  Wydajność we/wy dysku  

2.  Dostępna pamięć  

3.  CPU  

Aby uzyskać najlepszą wydajność należy używać konfiguracji RAID 10 dla wszystkich dysków danych oraz sieci Ethernet 1 GB.  

###  <a name="bkmk_ScaleSiteServer"></a>Serwery lokacji  

|Konfiguracja lokacji|Procesor CPU (rdzenie)|Pamięć (GB)|Alokacja pamięci dla programu SQL Server (%)|  
|-------------------------------|---------------|---------------|----------------------------------------|  
|Serwer autonomicznej lokacji głównej z rolą lokacji bazy danych na tym samym serwerze<sup>1</sup>|16|96|80|  
|Serwer autonomicznej lokacji głównej ze zdalną bazą danych lokacji|8|16|-|  
|Serwer zdalnej bazy danych dla autonomicznej lokacji głównej|16|72|90|  
|Serwer centralnej lokacji administracyjnej z rolą lokacji bazy danych na tym samym serwerze<sup>1</sup>|20|128|80|  
|Serwer centralnej lokacji administracyjnej ze zdalną bazą danych lokacji|8|16|-|  
|Serwer zdalnej bazy danych dla centralnej lokacji administracyjnej|16|96|90|  
|Podrzędna lokacja główna z rolą lokacji bazy danych na tym samym serwerze|16|96|80|  
|Serwer podrzędnej lokacji głównej ze zdalną bazą danych lokacji|8|16|-|  
|Serwer zdalnej bazy danych dla podrzędnej lokacji głównej|16|72|90|  
|Serwer lokacji dodatkowej|8|16|-|  

 <sup>1</sup> gdy serwer lokacji i programu SQL Server są zainstalowane na tym samym komputerze, wdrożenie obsługuje maksymalne liczby [rozmiaru i skali liczby](/sccm/core/plan-design/configs/size-and-scale-numbers) dla lokacji i klientów. Jednak ta konfiguracja może ograniczyć [opcje wysokiej dostępności programu System Center Configuration Manager](/sccm/protect/understand/high-availability-options), takie jak korzystanie z klastra programu SQL Server. Ponadto ze względu na wyższe wymagania we/wy, które są wymagane do obsługi programu SQL Server i serwer lokacji programu Configuration Manager, jeśli są uruchomione na tym samym komputerze, jest warto wziąć pod uwagę przy użyciu konfiguracji z komputera zdalnego programu SQL Server, w przypadku większych wdrożenia.  

###  <a name="bkmk_RemoteSiteSystem"></a>Serwery zdalnego systemu lokacji  
 Są następujące wskazówki dla komputerów, które pełnią rolę pojedynczego systemu lokacji. Zaplanuj wprowadzanie korekt, jeśli instalowanych jest wiele ról systemu lokacji na tym samym komputerze.  

|Rola systemu lokacji|Procesor CPU (rdzenie)|Pamięć (GB)|Miejsce na dysku (GB)|  
|----------------------|---------------|---------------|--------------------|  
|Punkt zarządzania|4|8|50|  
|Punkt dystrybucji|2|8|Co jest wymagane przez system operacyjny i do przechowywania zawartości, którą można wdrożyć|  
|Katalog aplikacji z usługą sieci web i witryną sieci web na komputerze systemu lokacji|4|16|50|  
|Punkt aktualizacji oprogramowania<sup>1</sup>|8|16|Co jest wymagane przez system operacyjny i do przechowywania aktualizacji, które można wdrożyć|  
|Wszystkie inne role systemu lokacji|4|8|50|  

 <sup>1</sup> komputera, który jest hostem punktu aktualizacji oprogramowania wymaga następujących konfiguracji dla pul aplikacji usług IIS:  

-   Zwiększ **długość kolejki WsusPool** do **2000**.  

-   Zwiększ **limit pamięci prywatnej WsusPool** przez 4 godziny, lub ustaw ją na **0** (brak ograniczenia).  

###  <a name="bkmk_DiskSpace"></a>Miejsce na dysku dla systemów lokacji  
 Alokacja i konfiguracja dysku wpływa na wydajność programu Configuration Manager. Ponieważ każde środowisko programu Configuration Manager jest inny, wartości, które można zaimplementować może różnić się od przedstawionych w tym temacie.  

 Aby uzyskać najlepszą wydajność, wszystkie obiekty powinny być umieszczone na oddzielnych dedykowanych woluminach macierzy RAID. Wszystkie woluminy danych (Configuration Manager i jego pliki bazy danych) Aby uzyskać najlepszą wydajność w macierzy RAID 10.  

|Użycie danych|Minimalna przestrzeń dyskowa|25 000 klientów|50 000 klientów|100 000 klientów|150 000 klientów|700 000 klientów (centralna lokacja administracyjna)|  
|----------------|------------------------|--------------------|--------------------|---------------------|---------------------|-----------------------------------------------------|  
|System operacyjny|Patrz wskazówki dotyczące systemu operacyjnego.|Patrz wskazówki dotyczące systemu operacyjnego.|Patrz wskazówki dotyczące systemu operacyjnego.|Patrz wskazówki dotyczące systemu operacyjnego.|Patrz wskazówki dotyczące systemu operacyjnego.|Patrz wskazówki dotyczące systemu operacyjnego.|  
|Pliki dziennika i aplikacji programu Configuration Manager|25 GB|50 GB|100 GB|200 GB|300 GB|200 GB|  
|Plik *.mdf bazy danych lokacji|75 GB na każde 25 000 klientów|75 GB|150 GB|300 GB|500 GB|2 TB|  
|Plik *.ldf bazy danych lokacji|25 GB na każde 25 000 klientów|25 GB|50 GB|100 GB|150 GB|100 GB|  
|Tymczasowe pliki bazy danych (*.mdf i *.ldf)|W razie potrzeby|W razie potrzeby|W razie potrzeby|W razie potrzeby|W razie potrzeby|W razie potrzeby|  
|Zawartość (udziały punktu dystrybucji)|W razie potrzeby<sup>1</sup>|W razie potrzeby<sup>1</sup>|W razie potrzeby<sup>1</sup>|W razie potrzeby<sup>1</sup>|W razie potrzeby<sup>1</sup>|W razie potrzeby<sup>1</sup>|  

 <sup>1</sup> wskazówki dotyczące przestrzeni dyskowej nie uwzględniają przestrzeni wymaganej na zawartość znajdującą się w bibliotece zawartości w lokacji serwera i w punktach dystrybucji. Aby uzyskać informacje dotyczące planowania biblioteki zawartości, zobacz [The content library](../../../core/plan-design/hierarchy/the-content-library.md) (Biblioteka zawartości).  

 Oprócz tej wskazówki podczas planowania związanego z wymogami przestrzeni dyskowej należy także uwzględnić następujące wytyczne:  

-   Każdy klient wymaga około 5 MB miejsca.  

-   Podczas planowania rozmiaru tymczasowej bazy danych lokacji głównej, planowanie łącznego rozmiaru, 25% do 30% pliku MDF bazy danych lokacji. Rzeczywisty rozmiar może być znacznie mniejszy lub większy — jest zależna od wydajności serwera lokacji oraz objętości przychodzących danych za pośrednictwem zarówno krótkich i długich okresów.  

    > [!NOTE]  
    >  Jeśli masz 50 000 lub więcej klientów w lokacji, Zaplanuj użycie co najmniej czterema Temp plików .mdf bazą danych.  

-   Rozmiar tymczasowej bazy danych w centralnej lokacji administracyjnej jest zwykle znacznie mniejszy niż w lokacji głównej.  

-   Ograniczenia rozmiaru bazy danych lokacji dodatkowej są następujące:  

    -   Program SQL Server 2012 Express: 10 GB  

    -   Program SQL Server 2014 Express: 10 GB  

##  <a name="bkmk_ScaleClient"></a>Klienci  
 Ta sekcja zawiera konfiguracje sprzętu zalecane dla komputerów zarządzanych za pomocą oprogramowania klienckiego programu Configuration Manager.  

### <a name="client-for-windows-computers"></a>Klient dla komputerów z systemem Windows  
 Poniżej przedstawiono minimalne wymagania dotyczące komputerów z systemem Windows zarządzanych za pomocą programu Configuration Manager, w tym systemami operacyjnymi embedded:  

-   **Procesor i pamięć:** Zapoznaj się wymaganiami dotyczącymi procesora i pamięci RAM dla systemu operacyjnego.  

-   **Miejsce na dysku:** 500 MB dostępnego miejsca, 5 GB jest zalecane dla pamięci podręcznej klienta programu Configuration Manager. Mniej miejsca na dysku jest wymagany, jeśli używasz ustawienia dostosowane do zainstalowania klienta programu Configuration Manager:  

    -   Użyj/skipprereq właściwości wiersza polecenia programu CCMSetup, aby uniknąć instalowania plików, które nie są wymagane przez klienta. Na przykład uruchom **CCMSetup.exe /skipprereq:silverlight.exe** Jeśli klient nie korzystają z katalogu aplikacji.  

    -   Ustaw mniejszy niż domyślny (5120 MB) rozmiar pliku pamięci podręcznej za pomocą właściwości Client.msi SMSCACHESIZE. Rozmiar minimalny to 1 MB. Na przykład polecenie **CCMSetup.exe SMSCachesize=2** tworzy pamięć podręczną o rozmiarze 2 MB.  

    Aby uzyskać więcej informacji o tych właściwościach instalacji klienta, zobacz [Informacje o właściwościach instalacji klientów w programie System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties.md).  

    > [!TIP]  
    >  Zainstalowanie klienta z minimalną ilością wolnego miejsca jest przydatne w przypadku urządzeń z systemem Windows Embedded, które zazwyczaj mają mniejsze rozmiary dysku niż standardowe komputery z systemem Windows.  



 Poniżej przedstawiono dodatkowe minimalne wymagania sprzętowe dotyczące opcjonalnych funkcji w programie Configuration Manager.  

-   **Wdrożenie systemu operacyjnego:** 384 MB pamięci RAM  

-   **Software Center:** Procesor 500 MHz  

-   **Zdalne sterowanie:** Pentium 4 technologią Hyper-Threading 3 GHz (jeden rdzeń) lub porównywalny Procesor, co najmniej 1 GB pamięci RAM celu zapewnienia optymalnego działania  

### <a name="client-for-linux-and-unix"></a>Klient dla systemu Linux i UNIX  
 Poniżej przedstawiono minimalne wymagania dotyczące serwerów Linux i UNIX, którymi można zarządzać w programie Configuration Manager.  

|Wymaganie|Szczegóły|  
|-----------------|-------------|  
|Procesor i pamięć|Zapoznaj się wymaganiami dotyczącymi procesora i pamięci RAM dla systemu operacyjnego.|  
|Miejsce na dysku|500 MB dostępnego miejsca, 5 GB jest zalecane dla pamięci podręcznej klienta programu Configuration Manager.|  
|Łączność sieciowa|Komputery klienckie programu Configuration Manager musi mieć łączność sieciową z systemami lokacji programu Configuration Manager, aby włączyć zarządzanie.|  

##  <a name="bkmk_ScaleConsole"></a>Konsola programu Configuration Manager  
 Wymagania w poniższej tabeli dotyczą każdego komputera, na którym uruchomiona jest konsola programu Configuration Manager.  

 **Minimalna konfiguracja sprzętowa:**  

-   Procesor CPU Intel i3 lub porównywalny  

-   2 GB pamięci RAM  

-   2 GB miejsca na dysku  

|Ustawienie DPI|Minimalna rozdzielczość|  
|-----------------|------------------------|  
|96 / 100%|1024 x 768|  
|120 / 125%|1280 x 960|  
|144 / 150%|1600 x 1200 pikseli|  
|196 / 200%|2500 x 1600|  

 **Pomoc techniczna dla programu PowerShell:**  

 Po zainstalowaniu obsługi dla programu PowerShell na komputerze, na którym uruchomiona jest konsola programu Configuration Manager, można uruchomić poleceń cmdlet programu PowerShell na tym komputerze do zarządzania programu Configuration Manager.

 - PowerShell 3.0 lub nowszej jest obsługiwana.

Oprócz programu PowerShell Windows Management Framework (WMF) w wersji 3.0 lub nowszej jest obsługiwana.   


##  <a name="bkmk_ScaleLab"></a>Wdrożenia w środowisku laboratoryjnym  
 Używaj poniższych zaleceń minimalne wymagania dotyczące sprzętu w środowisku laboratoryjnym lub testowym wdrożeń programu Configuration Manager. Te zalecenia dotyczą wszystkich typów lokacji, maksymalnie 100 klientów:  

|Rola|Procesor CPU (rdzenie)|Pamięć (GB)|Miejsce na dysku (GB)|  
|----------|---------------|-------------------|-----------------------|  
|Serwer lokacji i bazy danych|2 - 4|7 - 12|100|  
|Serwer systemu lokacji|1 - 4|2 - 4|50|  
|Klient|1 - 2|1 - 3|30|  
