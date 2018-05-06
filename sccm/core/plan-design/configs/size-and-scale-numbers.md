---
title: Rozmiaru i skali
titleSuffix: Configuration Manager
description: Określenie liczby ról systemu lokacji i lokacji, które należy do obsługi urządzeń w danym środowisku.
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: c5a42100-2f60-4952-b495-918025ea6559
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: b995687e330fe4beca26da83ee29ddc504c38e3a
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="size-and-scale-numbers-for-system-center-configuration-manager"></a>Numery rozmiaru i skali dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*



Dla każdego wdrożenia programu Configuration Manager ma maksymalną liczbę lokacji, role systemu lokacji i urządzeń, które może obsługiwać. Te liczby zależy od struktury hierarchii, jakie typy i liczby lokacji możesz użycia i role systemu lokacji, które można wdrożyć. Informacje przedstawione w tym artykule ułatwia określenie liczby ról systemu lokacji i lokacji, które są potrzebne do obsługi urządzeń, które chcesz zarządzać.

Informacje przedstawione w tym temacie w połączeniu z informacjami w następujących artykułach:
-   [Zalecany sprzęt](../../../core/plan-design/configs/recommended-hardware.md)
-   [Obsługiwane systemy operacyjne dla serwerów systemu lokacji](../../../core/plan-design/configs/supported-operating-systems-for-site-system-servers.md)  
-   [Obsługiwane systemy operacyjne dla klientów i urządzeń](../../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices.md)
-   [Wymagania wstępne dla lokacji i systemu lokacji](../../../core/plan-design/configs/site-and-site-system-prerequisites.md)


Te obsługi numerów są oparte na użyciu zalecany sprzęt dla programu Configuration Manager. Są one również oparte na wartości domyślne dla wszystkich dostępnych funkcji programu Configuration Manager. Jeśli nie używasz zalecanego sprzętu lub użyj bardziej agresywną ustawień niestandardowych, mogą obniżyć wydajność systemów lokacji. Systemy lokacji może nie zapewniać deklarowanych poziomów obsługi. (Przykład bardziej aktywnego ustawienia klienta działa spis sprzętu lub oprogramowania częściej niż domyślne co siedem dni.)

##  <a name="bkmk_SiteSystemScale"></a> Typy lokacji  

### <a name="central-administration-site"></a>Centralna lokacja administracyjna  

-   Centralna lokacja administracyjna obsługuje do 25 podrzędnych lokacji głównych.  


### <a name="primary-site"></a>Lokacja główna  

-   Każda lokacja główna obsługuje do 250 lokacji dodatkowych.  

-   Liczba lokacji dodatkowych na lokację główną jest oparta na nieprzerwanych i niezawodnych rozległej połączeń sieci (rozległej WAN). W przypadku lokalizacji, które mają mniej niż 500 klientów należy wziąć pod uwagę punktu dystrybucji zamiast lokacji dodatkowej.  

 Aby uzyskać informacje o liczbie klientów i urządzeń, które lokacja główna może obsługiwać, zobacz [liczba klientów dla lokacji i hierarchii](#bkmk_clientnumbers).  


### <a name="secondary-site"></a>Lokacja dodatkowa  

-   Lokacje dodatkowe nie obsługują lokacji podrzędnych.  



## <a name="bkmk_roles"></a> Role systemu lokacji    


### <a name="application-catalog-web-service-point"></a>Punkt usługi sieci Web Wykaz aplikacji  

-   Można zainstalować wiele wystąpień punktu usługi sieci web katalogu aplikacji w lokacjach głównych.  

    > [!TIP]  
    >  Najlepszym rozwiązaniem zainstalować punkt witryny sieci Web katalogu aplikacji i punkt usługi sieci web wykazu aplikacji razem w tym samym systemie lokacji gdy udostępniają usługi klientom, którzy znajdują się w intranecie.  

    -   Aby poprawić wydajność Zaplanuj do obsługi maksymalnie 50 000 klientów dla każdego wystąpienia.  

    -   Każde wystąpienie tej roli systemu lokacji obsługuje maksymalną liczbę klientów obsługiwanych przez hierarchię.  


### <a name="application-catalog-website-point"></a>Punkt witryny sieci Web wykazu aplikacji  

-   Można zainstalować wiele wystąpień punktu witryny sieci Web katalogu aplikacji w lokacjach głównych.  

    > [!TIP]  
    >  Najlepszym rozwiązaniem zainstalować punkt witryny sieci Web katalogu aplikacji i punkt usługi sieci web wykazu aplikacji razem w tym samym systemie lokacji gdy udostępniają usługi klientom, którzy znajdują się w intranecie.  

    -   Aby poprawić wydajność Zaplanuj do obsługi maksymalnie 50 000 klientów dla każdego wystąpienia.  

    -   Każde wystąpienie tej roli systemu lokacji obsługuje maksymalną liczbę klientów obsługiwanych przez hierarchię.  


### <a name="bkmk_cmg"></a> Brama zarządzania w chmurze

- Można zainstalować wiele wystąpień bramy zarządzania chmury (CMG) w lokacjach głównych lub centralnej lokacji administracyjnej.  

    > [!Tip]  
    > W hierarchii należy utworzyć CMG w witrynie Administracja centralna.  

    - Jeden CMG obsługuje jeden do 16 wystąpień maszyn wirtualnych (VM) w usłudze w chmurze Azure.  

    - Każde wystąpienie maszyny Wirtualnej CMG obsługuje 6000 równoczesnych połączeń klientów. Gdy CMG jest mocno obciążony ze względu na więcej niż liczba obsługiwanych klientów, nadal obsługuje żądania, ale mogą występować opóźnienia.  

Aby uzyskać więcej informacji, zobacz CMG [wydajności i skalowania](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway#performance-and-scale)


### <a name="cloud-management-gateway-connection-point"></a>Punkt połączenia z chmurą zarządzania bramy

- Można zainstalować wiele wystąpień punktu połączenia CMG w lokacjach głównych.  

- Punkt połączenia z jednym CMG może obsługiwać CMG z maksymalnie cztery wystąpień maszyn wirtualnych. Jeśli CMG ma więcej niż czterech wystąpień maszyn wirtualnych, należy dodać drugi punkt połączenia CMG Równoważenie obciążenia sieciowego. CMG z 16 wystąpień maszyn wirtualnych powinna być połączona z czterech punktów połączenia CMG.

Aby uzyskać więcej informacji, zobacz CMG [wydajności i skalowania](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway#performance-and-scale)


### <a name="distribution-point"></a>Punkt dystrybucji  

-   Punkty dystrybucji na lokację:  

    -   Każda lokacja podstawowa i dodatkowa obsługuje do 250 punktów dystrybucji.  

    -   Każda lokacja podstawowa i dodatkowa obsługuje do 2000 dodatkowych punktów dystrybucji skonfigurowanych jako ściągające punkty dystrybucji. **Na przykład**, pojedyncza lokacja główna obsługuje 2250 punktów dystrybucji, gdy 2000 z tych punktów dystrybucji skonfigurowanych jako ściągające punkty dystrybucji.  

    -   Każdy punkt dystrybucji obsługuje połączenia od maksymalnie 4000 klientów.  

    -   Ściągający punkt dystrybucji działa jak klient, uzyskując dostęp do zawartości ze źródłowego punktu dystrybucji.  

-   Każda lokacja główna obsługuje łącznie do 5000 punktów dystrybucji. Łączna liczba obejmuje wszystkie punkty dystrybucji w lokacji głównej i wszystkich punktów dystrybucji, które należą do podrzędnych lokacji dodatkowych lokacji głównej.  

-   Każdy punkt dystrybucji obsługuje łącznie do 10 000 pakietów i aplikacji.  

> [!WARNING]  
>  Rzeczywista liczba klientów, którzy mogą obsługiwać jeden punkt dystrybucji zależy od szybkości sieci i konfiguracji sprzętu serwera.  
>   
>  Liczba ściągających punktów dystrybucji obsługujących jeden punkt dystrybucji podobnie zależy od szybkości sieci i konfiguracji sprzętowej źródłowego punktu dystrybucji. Jednak ta liczba wpływa także na ilość zawartości, która została wdrożona. Efekt jest, ponieważ w odróżnieniu od klientów, którzy zwykle uzyskują dostęp do zawartości w różnym czasie podczas wdrażania, wszystkie punkty dystrybucji ściągania żądanie zawartości w tym samym czasie. Ściągające punkty dystrybucji mogą żądać całej zawartości dostępna nie tylko zawartości, która ich dotyczy. Po umieszczeniu wysokie obciążenie przetwarzania w źródłowym punkcie dystrybucji może być nieoczekiwane opóźnienia w dystrybucji zawartości do punktów dystrybucji docelowej.  


### <a name="fallback-status-point"></a>Rezerwowy punkt stanu  

-   Każdy rezerwowy punkt stanu może obsługiwać do 100 000 klientów.  


### <a name="management-point"></a>Punkt zarządzania  

-   Każda lokacja główna obsługuje do 15 punktów zarządzania.  

    > [!TIP]  
    >  Nie należy instalować punktów zarządzania na serwerach korzystających z serwera lokacji podstawowej powolnego łącza lub na serwerze bazy danych lokacji.  

-   Każda lokacja dodatkowa obsługuje pojedynczy punkt zarządzania, który musi być zainstalowany na serwerze lokacji dodatkowej.  

 Aby uzyskać informacje o liczbie klientów i urządzeń obsługiwanych przez punkt zarządzania, zobacz [punktów zarządzania](#bkmk_mp) sekcji.  


### <a name="software-update-point"></a>Punkt aktualizacji oprogramowania  

-   Punkt aktualizacji oprogramowania, który jest zainstalowany na serwerze lokacji może obsługiwać do 25 000 klientów.   

-   Punkt aktualizacji oprogramowania, który jest zdalny z serwera lokacji może obsługiwać do 150 000 klientów, gdy komputer zdalny spełnia wymagania dotyczące systemu Windows Server Update Services (WSUS) dotyczące obsługi tej liczby klientów.  

-   Domyślnie program Configuration Manager nie obsługuje konfigurowania punktów aktualizacji oprogramowania jako klastrów równoważenia obciążenia sieciowego (NLB). Jednak można użyć zestawu SDK programu Configuration Manager do skonfigurowania do czterech punktów aktualizacji oprogramowania w klastrze równoważenia obciążenia Sieciowego.  



##  <a name="bkmk_clientnumbers"></a> Liczba klientów dla lokacji i hierarchii  
 Skorzystaj z poniższych informacji, aby określić liczbę klientów i jakie typy klientów mogą być obsługiwane w lokacji lub w hierarchii.  


###  <a name="bkmk_cas"></a> Hierarchia z centralną lokacją administracyjną  
Centralna lokacja administracyjna obsługuje łączna liczba urządzeń zawierającą maksymalnie liczbę urządzeń dla trzech następujących grup:  

-   700 000 komputerów stacjonarnych (komputerów z systemem Windows, Linux lub UNIX). Zobacz też, obsługę [urządzenia osadzone](#embedded).

-   25 000 urządzeń z systemem Mac lub Windows CE 7.0  

-   Jeden z następujących czynności, w zależności od sposobu wdrożenia obsługuje zarządzanie urządzeniami przenośnymi (MDM):  

    -   100 000 urządzeń, którymi można zarządzać za pomocą lokalnego zarządzania urządzeniami Przenośnymi  

    -   300 000 urządzeń opartych na chmurze  

 Na przykład w hierarchii można obsługiwać 700 000 komputerów stacjonarnych, maksymalnie 25 000 urządzeń Mac lub Windows CE 7.0 oraz maksymalnie 300 000 urządzeń opartych na chmurze podczas integracji programów Microsoft Intune. Ta hierarchia obsługuje łącznie 1 025 000 urządzeń. Jeśli w przypadku obsługi urządzeń, które są zarządzane przez lokalnego zarządzania urządzeniami Przenośnymi, łączna liczba w tej hierarchii jest 825 000 urządzeń.  

> [!IMPORTANT]  
>  W hierarchii, w której centralna lokacja administracyjna korzysta z wersji Standard programu SQL Server hierarchia obsługuje maksymalnie 50 000 komputerów stacjonarnych i urządzeń. Aby obsługiwać więcej niż 50 000 komputerów stacjonarnych i urządzeń, należy użyć wersji Enterprise programu SQL Server. To wymaganie dotyczy tylko centralną lokację administracyjną. Nie ma zastosowania do autonomicznej lokacji głównej lub podrzędnej lokacji głównej. Wersja programu SQL Server używane na potrzeby lokacji głównej nie ograniczyć jej zdolności do obsługi dla określonej liczby klientów.   


 Wersja programu SQL Server, który jest używany w autonomicznej lokacji głównej nie ograniczają pojemność tej lokacji do obsługi do określonej liczby klientów.  


###  <a name="bkmk_chipri"></a> Podrzędna lokacja główna  
Każda podrzędna lokacja główna w hierarchii z centralną lokacją administracyjną obsługuje następującą liczbę klientów:  

-   150 000 łącznej liczby klientów i urządzeń, które nie są ograniczone do określonej grupy lub typu, jak długo pomocy technicznej nie przekracza liczbę, która jest obsługiwana dla hierarchii. Zobacz też, obsługę [urządzenia osadzone](#embedded).

Na przykład lokacja główna obsługuje 25 000 urządzeń Mac lub Windows CE 7.0. Numer ten jest limit dla hierarchii. Ta lokacja główna może obsługiwać następnie dodatkowe 125 000 komputerów stacjonarnych. Całkowita liczba obsługiwanych urządzeń dla podrzędnej lokacji głównej jest obsługiwany limit maksymalną 150 000.


###  <a name="bkmk_pri"></a> Autonomicznej lokacji głównej  
Autonomiczna lokacja główna obsługuje następującą liczbę urządzeń:  

-   175 000 łącznej liczby klientów i urządzeń, nie może przekraczać:  

    -   150 000 komputerów stacjonarnych (komputerów z systemem Windows, Linux lub UNIX). Zobacz też, obsługę [urządzenia osadzone](#embedded).

    -   25 000 urządzeń z systemem Mac lub Windows CE 7.0

    -   Jeden z następujących czynności, w zależności od sposobu wdrożenia obsługuje zarządzanie urządzeniami przenośnymi:  

        -   50 000 urządzeń, którymi można zarządzać za pomocą lokalnego zarządzania urządzeniami Przenośnymi  

        -   150 000 urządzeń opartych na chmurze  


Na przykład autonomicznej lokacji głównej, która obsługuje 150 000 komputerów stacjonarnych i 10 000 komputerów Mac lub Windows CE 7.0 może obsługiwać tylko 15 000 dodatkowych urządzeń. Te urządzenia muszą być oparte na chmurze lub zarządzane przy użyciu lokalnego zarządzania urządzeniami przenośnymi.  


### <a name="embedded"></a> Lokacje główne i urządzeń z systemem Windows Embedded
Lokacje główne obsługują urządzeń Windows Embedded opartych na plikach włączone filtry zapisu (FBWF). Gdy urządzenia osadzone nie mają włączone filtry zapisu, lokacja główna może obsługiwać kilka urządzeń osadzonych maksymalnie dozwolonej liczbie urządzeń dla tej lokacji. Łączna liczba urządzeń obsługiwanych przez lokację główną może być maksymalnie 10 000 urządzeń z systemem Windows Embedded. Te urządzenia muszą być skonfigurowane dla wyjątków, na liście ważna uwaga w [Planowanie wdrożenia klientów na urządzeniach Windows Embedded](/sccm/core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices). Lokacja główna obsługuje tylko 3000 urządzeń Windows Embedded, które z włączonymi Rozszerzonymi filtrami, które nie są skonfigurowane dla wyjątków.


###  <a name="bkmk_sec"></a> Lokacje dodatkowe  
Lokacje dodatkowe obsługują następującą liczbę urządzeń:  

-   15 000 komputerów stacjonarnych (komputerów z systemem Windows, Linux i UNIX)  


###  <a name="bkmk_mp"></a> Punkty zarządzania  
Każdy punkt zarządzania może obsługiwać następującą liczbę urządzeń:  

-   25 000 łącznej liczby klientów i urządzeń, nie może przekraczać:  

    -   25 000 komputerów stacjonarnych (komputerów z systemem Windows, Linux i UNIX)  

    -   Jedną z następujących (nie obie):  

        -   10 000 urządzeń, które są zarządzane przy użyciu lokalnego zarządzania urządzeniami Przenośnymi  

        -   10 000 urządzeń z systemem Mac lub Windows CE 7.0 klientów
