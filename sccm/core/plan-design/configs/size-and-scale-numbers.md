---
title: Rozmiaru i skali | Dokumentacja firmy Microsoft
description: "Określ liczbę ról systemu lokacji i lokacji, które należy do obsługi urządzeń w środowisku programu System Center Configuration Manager."
ms.custom: na
ms.date: 07/24/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c5a42100-2f60-4952-b495-918025ea6559
caps.latest.revision: "4"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: f539e2d282b56e56a9c58c773788325b27ea6b37
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="size-and-scale-numbers-for-system-center-configuration-manager"></a>Numery rozmiaru i skali dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*



Dla każdego wdrożenia programu System Center Configuration Manager ma maksymalną liczbę lokacji, role systemu lokacji i urządzeń, które może obsługiwać. Te liczby różne w zależności od struktury hierarchii (jakie typy i liczby używanych lokacji) i role systemu lokacji, które można wdrożyć.  Informacje zawarte w następujących obszarach ułatwia określenie liczby ról systemu lokacji i lokacji, które należy do obsługi urządzeń, którymi będziesz zarządzać ze środowiskiem.

Informacje przedstawione w tym temacie w połączeniu z informacjami w następujących artykułach:
-   [Zalecany sprzęt](../../../core/plan-design/configs/recommended-hardware.md)
-   [Obsługiwane systemy operacyjne dla serwerów systemu lokacji](../../../core/plan-design/configs/supported-operating-systems-for-site-system-servers.md)  
-   [Obsługiwane systemy operacyjne dla klientów i urządzeń](../../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices.md)
-   [Wymagania wstępne dla lokacji i systemu lokacji](../../../core/plan-design/configs/site-and-site-system-prerequisites.md)


Następujące numery pomocy technicznej są oparte na użyciu zalecany sprzęt dla programu Configuration Manager i domyślne ustawienia dla wszystkich dostępnych funkcji programu Configuration Manager. Jeśli nie używasz zalecanego sprzętu lub użyj bardziej agresywną niestandardowych ustawień (takich jak uruchomionych spis sprzętu lub oprogramowania częściej niż domyślne co siedem dni), wydajność systemów lokacji może być niższa i może nie zapewniać deklarowanych poziomów obsługi.

##  <a name="bkmk_SiteSystemScale"></a>Typy lokacji  
 **Centralna lokacja administracyjna:**  

-   Centralna lokacja administracyjna obsługuje do 25 podrzędnych lokacji głównych.  

**Lokacja główna:**  

-   Każda lokacja główna obsługuje do 250 lokacji dodatkowych.  

-   Liczba lokacji dodatkowych na lokację główną jest oparta na nieprzerwanych i niezawodnych rozległej połączeń sieci (rozległej WAN). W przypadku lokalizacji, które mają mniej niż 500 klientów należy wziąć pod uwagę punktu dystrybucji zamiast lokacji dodatkowej.  

 Aby uzyskać informacje o liczbie klientów i urządzeń, które lokacja główna może obsługiwać, zobacz [liczba klientów dla lokacji i hierarchii](#bkmk_clientnumbers) w tym temacie.  

**Lokacja dodatkowa:**  

-   Lokacje dodatkowe nie obsługują lokacji podrzędnych.  

-   Centralna lokacja administracyjna obsługuje do 25 podrzędnych lokacji głównych.  

**Punkt witryny sieci Web katalogu aplikacji:**  

-   Można zainstalować wiele wystąpień punktu witryny sieci Web katalogu aplikacji w lokacjach głównych.  

    > [!TIP]  
    >  Najlepszym rozwiązaniem zainstalować punkt witryny sieci Web katalogu aplikacji i punkt usługi sieci web wykazu aplikacji razem w tym samym systemie lokacji gdy udostępniają usługi klientom, którzy znajdują się w intranecie.  

    -   Aby poprawić wydajność Zaplanuj do obsługi maksymalnie 50 000 klientów dla każdego wystąpienia.  

    -   Każde wystąpienie tej roli systemu lokacji obsługuje maksymalną liczbę klientów obsługiwanych przez hierarchię.  

## <a name="bkmk_roles"></a>Role systemu lokacji    

**Punkt usługi sieci web katalogu aplikacji:**  

-   Można zainstalować wiele wystąpień punktu usługi sieci web katalogu aplikacji w lokacjach głównych.  

    > [!TIP]  
    >  Najlepszym rozwiązaniem zainstalować punkt witryny sieci Web katalogu aplikacji i punkt usługi sieci web wykazu aplikacji razem w tym samym systemie lokacji gdy udostępniają usługi klientom, którzy znajdują się w intranecie.  

    -   Aby poprawić wydajność Zaplanuj do obsługi maksymalnie 50 000 klientów dla każdego wystąpienia.  

    -   Każde wystąpienie tej roli systemu lokacji obsługuje maksymalną liczbę klientów obsługiwanych przez hierarchię.  

**Punkt dystrybucji:**  

-   Punkty dystrybucji na lokację:  

    -   Każda lokacja podstawowa i dodatkowa obsługuje do 250 punktów dystrybucji.  

    -   Każda lokacja podstawowa i dodatkowa obsługuje do 2000 dodatkowych punktów dystrybucji skonfigurowanych jako ściągające punkty dystrybucji. **Na przykład**, pojedyncza lokacja główna obsługuje 2250 punktów dystrybucji, gdy 2000 z tych punktów dystrybucji skonfigurowanych jako ściągające punkty dystrybucji.  

    -   Każdy punkt dystrybucji obsługuje połączenia od maksymalnie 4000 klientów.  

    -   Ściągający punkt dystrybucji działa jak klient, uzyskując dostęp do zawartości ze źródłowego punktu dystrybucji.  

-   Każda lokacja główna obsługuje łącznie do 5000 punktów dystrybucji. Łączna liczba obejmuje wszystkie punkty dystrybucji w lokacji głównej i wszystkich punktów dystrybucji, które należą do podrzędnych lokacji dodatkowych lokacji głównej.  

-   Każdy punkt dystrybucji obsługuje łącznie do 10 000 pakietów i aplikacji.  

> [!WARNING]  
>  Rzeczywista liczba klientów, którzy mogą obsługiwać jeden punkt dystrybucji zależy od prędkości sieci oraz konfiguracji sprzętowej komputera punktu dystrybucji.  
>   
>  Liczba ściągających punktów dystrybucji obsługujących jeden punkt dystrybucji podobnie zależy od prędkości sieci oraz konfiguracji sprzętowej komputera źródłowego punktu dystrybucji. Jednak ta liczba wpływa także na ilość zawartości, która została wdrożona. Wynika to z faktu, w odróżnieniu od klientów, którzy zwykle uzyskują dostęp do zawartości w różnym czasie podczas wdrażania, wszystkie punkty dystrybucji ściągania żądanie zawartości w tym samym czasie — i mogą żądać całej zawartości dostępna nie tylko zawartości, która ich dotyczy, jak klient. Gdy zbyt dużo obciążenie przetwarzania jest umieszczony w źródłowym punkcie dystrybucji, może być nieoczekiwane opóźnienia w dystrybucji zawartości do oczekujących punktów dystrybucji w danym środowisku.  


**Rezerwowy punkt stanu:**  

-   Każdy rezerwowy punkt stanu może obsługiwać do 100 000 klientów.  

**Punkt zarządzania:**  

-   Każda lokacja główna obsługuje do 15 punktów zarządzania.  

    > [!TIP]  
    >  Nie należy instalować punktów zarządzania na serwerach, które są przy użyciu wolnego połączenia z serwera lokacji głównej lub z serwera bazy danych lokacji.  

-   Każda lokacja dodatkowa obsługuje pojedynczy punkt zarządzania, który musi być zainstalowany na serwerze lokacji dodatkowej.  

 Aby uzyskać informacje o liczbie klientów i urządzeń obsługiwanych przez punkt zarządzania, zobacz [punktów zarządzania](#bkmk_mp) w tym temacie.  

**Punkt aktualizacji oprogramowania:**  

-   Punkt aktualizacji oprogramowania, który jest zainstalowany na serwerze lokacji może obsługiwać do 25 000 klientów.  

-   Punkt aktualizacji oprogramowania, który jest zdalny z serwera lokacji może obsługiwać do 150 000 klientów, gdy komputer zdalny spełnia wymagania dotyczące systemu Windows Server Update Services (WSUS) dotyczące obsługi tej liczby klientów.  

-   Domyślnie program Configuration Manager nie obsługuje konfigurowania punktów aktualizacji oprogramowania jako klastrów równoważenia obciążenia sieciowego (NLB). Jednak można użyć zestawu SDK programu Configuration Manager do skonfigurowania do czterech punktów aktualizacji oprogramowania w klastrze równoważenia obciążenia Sieciowego.  

##  <a name="bkmk_clientnumbers"></a>Liczba klientów dla lokacji i hierarchii  
 Skorzystaj z poniższych informacji, aby określić liczbę klientów i jakie typy klientów mogą być obsługiwane w lokacji lub w hierarchii.  

###  <a name="bkmk_cas"></a>Hierarchia z centralną lokacją administracyjną  
Centralna lokacja administracyjna obsługuje łączna liczba urządzeń zawierającą maksymalnie liczbę urządzeń dla trzech następujących grup:  

-   700 000 komputerów stacjonarnych (komputerów z systemem Windows, Linux lub UNIX). Zobacz też, obsługę [urządzenia osadzone](#embedded).

-   25 000 urządzeń z systemem Mac lub Windows CE 7.0  

-   Jeden z następujących czynności, w zależności od sposobu wdrożenia obsługuje zarządzanie urządzeniami przenośnymi (MDM):  

    -   100 000 urządzeń, którymi można zarządzać za pomocą lokalnego zarządzania urządzeniami Przenośnymi  

    -   300 000 urządzeń opartych na chmurze  

 Na przykład w hierarchii można obsługiwać 700 000 komputerów stacjonarnych, maksymalnie 25 000 komputerów Mac lub Windows CE 7.0 oraz maksymalnie 300 000 urządzeń opartych na chmurze podczas integracji programów Microsoft Intune — łącznie 1 025 000 urządzeń. Jeśli w przypadku obsługi urządzeń, które są zarządzane przez lokalnego zarządzania urządzeniami Przenośnymi, łączna liczba dla hierarchii jest 825 000 urządzeń.  

> [!IMPORTANT]  
>  W hierarchii, w której centralna lokacja administracyjna korzysta z wersji Standard programu SQL Server hierarchia obsługuje maksymalnie 50 000 komputerów stacjonarnych i urządzeń. Wersja programu SQL Server, który jest używany w autonomicznej lokacji głównej nie ograniczają pojemność tej lokacji do obsługi do określonej liczby klientów.  


###  <a name="bkmk_chipri"></a>Podrzędna lokacja główna  
Każda podrzędna lokacja główna w hierarchii z centralną lokacją administracyjną obsługuje następujące funkcje:  

-   150 000 łącznej liczby klientów i urządzeń, które nie są ograniczone do określonej grupy lub typu, jak długo pomocy technicznej nie przekracza liczbę, która jest obsługiwana dla hierarchii. Zobacz też, obsługę [urządzenia osadzone](#embedded).

Na przykład lokacji głównej, która obsługuje 25 000 komputerów z systemem Mac lub Windows CE 7.0 (ponieważ taki jest limit dla hierarchii), następnie może obsługiwać dodatkowe 125 000 komputerów stacjonarnych. Powoduje to całkowita liczba obsługiwanych urządzeń do podrzędnej lokacji głównej obsługiwany limit maksymalną 150 000.

###  <a name="bkmk_pri"></a>Autonomicznej lokacji głównej  
Autonomiczna lokacja główna obsługuje następującą liczbę urządzeń:  

-   175 000 łącznej liczby klientów i urządzeń, nie może przekraczać:  

    -   150 000 komputerów stacjonarnych (komputerów z systemem Windows, Linux lub UNIX). Zobacz też, obsługę [urządzenia osadzone](#embedded).

    -   25 000 urządzeń z systemem Mac lub Windows CE 7.0

    -   Jeden z następujących czynności, w zależności od sposobu wdrożenia obsługuje zarządzanie urządzeniami przenośnymi:  

        -   50 000 urządzeń, którymi można zarządzać za pomocą lokalnego zarządzania urządzeniami Przenośnymi  

        -   150 000 urządzeń opartych na chmurze  


Na przykład autonomicznej lokacji głównej, która obsługuje 150 000 komputerów stacjonarnych i 10 000 komputerów Mac lub Windows CE 7.0 może obsługiwać tylko 15 000 dodatkowych urządzeń. Te urządzenia muszą być oparte na chmurze lub zarządzane przy użyciu lokalnego zarządzania urządzeniami przenośnymi.  

### <a name="embedded"></a>Lokacje główne i urządzeń z systemem Windows Embedded
Lokacje główne obsługują urządzeń Windows Embedded opartych na plikach włączone filtry zapisu (FBWF). Gdy urządzenia osadzone nie mają włączone filtry zapisu, lokacja główna może obsługiwać kilka urządzeń osadzonych maksymalnie dozwolonej liczbie urządzeń dla tej lokacji. Łączna liczba urządzeń obsługiwanych przez lokację główną, maksymalnie 10 000 może być urządzeniach Windows Embedded podczas te urządzenia są skonfigurowane z uwzględnieniem wyjątków z ważna uwaga w [Planowanie wdrożenia klientów na urządzeniach Windows Embedded](/sccm/core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices). Lokacja główna obsługuje tylko 3000 urządzeń Windows Embedded, które z włączonymi Rozszerzonymi filtrami, które nie są skonfigurowane dla wyjątków.

###  <a name="bkmk_sec"></a>Lokacje dodatkowe  
Lokacje dodatkowe obsługują następujące czynności:  

-   15 000 komputerów stacjonarnych (komputerów z systemem Windows, Linux i UNIX)  

###  <a name="bkmk_mp"></a>Punkty zarządzania  
Każdy punkt zarządzania może obsługiwać następującą liczbę urządzeń:  

-   25 000 łącznej liczby klientów i urządzeń, nie może przekraczać:  

    -   25 000 komputerów stacjonarnych (komputerów z systemem Windows, Linux i UNIX)  

    -   Jedną z następujących (nie obie):  

        -   10 000 urządzeń, które są zarządzane przy użyciu lokalnego zarządzania urządzeniami Przenośnymi  

        -   10 000 urządzeń z systemem Mac lub Windows CE 7.0 klientów
