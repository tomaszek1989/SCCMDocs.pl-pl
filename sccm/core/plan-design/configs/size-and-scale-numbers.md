---
title: Rozmiaru i skali | Dokumentacja firmy Microsoft
description: "Określ liczbę ról systemu lokacji i lokacji, które należy do obsługi urządzeń w środowisku programu System Center Configuration Manager."
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c5a42100-2f60-4952-b495-918025ea6559
caps.latest.revision: 4
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9c43e26758d5171a6ef56e827b4b054ebc8a5e5
ms.openlocfilehash: c7ad33339e65e6e00e88f98d6e13baceb98dae77
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="size-and-scale-numbers-for-system-center-configuration-manager"></a>Numery rozmiaru i skali dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*



Każdego wdrożenia programu System Center Configuration Manager ma maksymalną liczbę lokacji, ról systemu lokacji i urządzeń, które mogą obsługiwać. Numery różnią się w zależności od struktury hierarchii (jakie typy i liczby witryn używasz) i role systemu lokacji, które można wdrożyć.  Informacje w następujących obszarach może pomóc w zidentyfikowaniu liczby ról systemu lokacji i lokacji, które są potrzebne do obsługi urządzeń, potrzebne do zarządzania ze środowiskiem.

Informacje przedstawione w tym temacie w połączeniu z informacjami w następujących artykułach:
-   [Zalecany sprzęt](../../../core/plan-design/configs/recommended-hardware.md)
-   [Obsługiwane systemy operacyjne dla serwerów systemu lokacji](../../../core/plan-design/configs/supported-operating-systems-for-site-system-servers.md)  
-   [Obsługiwane systemy operacyjne klientów i urządzeń](../../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices.md)
-   [Wymagania wstępne systemu lokacji i lokacji](../../../core/plan-design/configs/site-and-site-system-prerequisites.md)


Następujące numery pomocy technicznej są oparte na użyciu zalecany sprzęt dla programu Configuration Manager i domyślne ustawienia dla wszystkich dostępnych funkcji programu Configuration Manager. Gdy nie używać zalecany sprzęt lub użyć bardziej aktywnego niestandardowych ustawień (takich jak uruchamianie spis sprzętu lub oprogramowania częściej niż co siedem dni ustawienia domyślne), wydajności systemów lokacji może być znacznie i nie spełnia określonych poziom obsługi.

##  <a name="bkmk_SiteSystemScale"></a>Typy lokacji  
 **Witryna Administracja centralna:**  

-   Centralna lokacja administracyjna obsługuje maksymalnie 25 podrzędnych lokacji głównych.  

**Lokacji głównej:**  

-   Każda lokacja główna obsługuje maksymalnie 250 Lokacje dodatkowe.  

-   Liczba Lokacje dodatkowe w każdej lokacji głównej jest oparty na stale połączony i niezawodne rozległej połączenia sieci (rozległej WAN). Dla lokalizacji, które mają mniej niż 500 klientów należy wziąć pod uwagę punktu dystrybucji zamiast lokacji dodatkowej.  

 Aby uzyskać informacje o liczbie klientów i urządzeń obsługujących lokacji głównej, zobacz [numery klienta dla lokacji i hierarchii](#bkmk_clientnumbers) w tym temacie.  

**Lokacja dodatkowa:**  

-   Lokacje dodatkowe nie obsługują lokacji podrzędnych.  

-   Centralna lokacja administracyjna obsługuje maksymalnie 25 podrzędnych lokacji głównych.  

**Punkt witryny sieci Web katalogu aplikacji:**  

-   Można zainstalować wiele wystąpień punkt witryny sieci Web katalogu aplikacji w lokacjach głównych.  

    > [!TIP]  
    >  Najlepszym rozwiązaniem zainstalować punkt witryny sieci Web katalogu aplikacji i punkt usługi sieci web katalogu aplikacji razem w tym samym systemie lokacji podczas ich obsługi klientów znajdujących się w sieci intranet.  

    -   Aby poprawić wydajność planuje się obsługiwać do 50 000 klientów dla każdego wystąpienia.  

    -   Każde wystąpienie tej roli systemu lokacji obsługuje maksymalną liczbę klientów, które są obsługiwane przez hierarchię.  

## <a name="bkmk_roles"></a>Role systemu lokacji    

**Punkt usługi sieci web katalogu aplikacji:**  

-   Można zainstalować wiele wystąpień punktu usługi sieci web katalogu aplikacji w lokacjach głównych.  

    > [!TIP]  
    >  Najlepszym rozwiązaniem zainstalować punkt witryny sieci Web katalogu aplikacji i punkt usługi sieci web katalogu aplikacji razem w tym samym systemie lokacji podczas ich obsługi klientów znajdujących się w sieci intranet.  

    -   Aby poprawić wydajność planuje się obsługiwać do 50 000 klientów dla każdego wystąpienia.  

    -   Każde wystąpienie tej roli systemu lokacji obsługuje maksymalną liczbę klientów, które są obsługiwane przez hierarchię.  

**Punkt dystrybucji:**  

-   Punkty dystrybucji dla lokacji:  

    -   Każda lokacja podstawowa i pomocnicza obsługuje maksymalnie 250 punktów dystrybucji.  

    -   Każda lokacja podstawowa i pomocnicza obsługuje maksymalnie 2000 dodatkowych punktów dystrybucji skonfigurowanych jako ściągające punkty dystrybucji. **Na przykład**, jednej lokacji głównej obsługuje punktów dystrybucji 2250 2000 punkty dystrybucji są skonfigurowane jako ściągające punkty dystrybucji.  

    -   Każdy punkt dystrybucji obsługuje połączenia od klientów do 4000.  

    -   Punkt dystrybucji ściągania zachowuje się jak klient, uzyskując dostęp do zawartości ze źródłowego punktu dystrybucji.  

-   Każda lokacja główna obsługuje łącznego maksymalnie 5000 punktów dystrybucji. To podsumowanie obejmuje wszystkie punkty dystrybucji w lokacji głównej i wszystkie punkty dystrybucji, które należą do lokacji głównej podrzędnych lokacji dodatkowych.  

-   Każdy punkt dystrybucji obsługuje łącznego maksymalnie 10 000 pakiety i aplikacje.  

> [!WARNING]  
>  Rzeczywista liczba klientów obsługujących jednego punktu dystrybucji zależy od szybkości sieci i konfiguracji sprzętowej komputera punktu dystrybucji.  
>   
>  Liczba ściągające punkty dystrybucji obsługujące jednego źródłowego punktu dystrybucji podobnie zależy od szybkości sieci i konfiguracji sprzętowej komputera źródłowego punktu dystrybucji. Jednak ilości zawartości, który został wdrożony również dotyczy ten numer. Wynika to z faktu, w odróżnieniu od klientów, którzy zwykle dostęp do zawartości w różnym czasie podczas wdrażania, wszystkie punkty dystrybucji ściągania żądania zawartości w tym samym czasie — i może całą zawartość dostępna nie tylko zawartość, która ma zastosowanie do nich, co klient. Gdy zbyt duże obciążenie przetwarzaniem jest umieszczony w źródłowym punkcie dystrybucji, może istnieć nieoczekiwane opóźnienia w dystrybucji zawartości do punktów dystrybucji oczekiwanego w danym środowisku.  


**Rezerwowy punkt stanu:**  

-   Każdy punkt stanu powrotu może obsługiwać maksymalnie 100 000 klientów.  

**Punkt zarządzania:**  

-   Każda lokacja główna obsługuje maksymalnie 15 punktów zarządzania.  

    > [!TIP]  
    >  Nie należy instalować na serwerach, które są przez powolne łącze z serwera lokacji głównej lub z serwerem bazy danych lokacji punktów zarządzania.  

-   Każda lokacja dodatkowej obsługuje pojedynczy punkt zarządzania, który musi być zainstalowany na serwerze lokacji dodatkowej.  

 Aby uzyskać informacje o liczbie klientów i urządzeń obsługujących punktem zarządzania, zobacz [punktów zarządzania](#bkmk_mp) w tym temacie.  

**Punkt aktualizacji oprogramowania:**  

-   Punkt aktualizacji oprogramowania, który jest zainstalowany na serwerze lokacji może obsłużyć do 25 000 klientów.  

-   Punkt aktualizacji oprogramowania, które zdalnie z serwera lokacji może obsługiwać maksymalnie 150 000 klientów, gdy komputer zdalny spełnia wymagania dotyczące systemu Windows Server Update Services (WSUS) do obsługi tej liczby klientów.  

-   Domyślnie program Configuration Manager nie obsługuje Konfigurowanie punktów aktualizacji oprogramowania jako klastry równoważenia obciążenia sieciowego (NLB). Jednak można użyć zestawu SDK programu Configuration Manager w celu skonfigurowania maksymalnie cztery punkty aktualizacji oprogramowania w klastrze równoważenia obciążenia Sieciowego.  

##  <a name="bkmk_clientnumbers"></a>Numery klienta dla lokacji i hierarchii  
 Skorzystaj z poniższych informacji, aby określić, ilu klientów i jakie typy klienci mogą obsługiwać w lokacji lub w hierarchii.  

###  <a name="bkmk_cas"></a>Hierarchia z witryny Administracja centralna  
Centralna lokacja administracyjna obsługuje całkowita liczba urządzeń zawierającą maksymalnie liczbę urządzeń dla trzech następujących grup:  

-   700,000 pulpity (komputery z systemem Windows, Linux i UNIX)  

-   urządzenia 25 000, z systemem Mac i Windows CE 7.0  

-   Jeden z następujących elementów, w zależności od sposobu wdrożenia obsługuje zarządzanie urządzeniami przenośnymi (MDM):  

    -   100000 urządzeniami, którymi można zarządzać za pomocą lokalnych MDM  

    -   300 000 chmurze urządzeń  

 Na przykład w hierarchii, można obsługiwać 700,000 komputerów stacjonarnych, maksymalnie 25 000 komputerów Mac i Windows CE 7.0 i maksymalnie 300 000 chmurze urządzenia podczas integracji programów Microsoft Intune — łącznie 1,025,000 urządzenia. W przypadku obsługi urządzeń, które są zarządzane przez lokalną MDM, Suma dla hierarchii jest 825,000 urządzenia.  

> [!IMPORTANT]  
>  W hierarchii, w których witryny Administracja centralna używa wersji Standard programu SQL Server hierarchii obsługuje maksymalnie 50 000 komputerów stacjonarnych i urządzeń. Wersja programu SQL Server, który jest używany w autonomicznej lokacji głównej nie ogranicza zdolności tej lokacji do obsługi do określonej liczby klientów.  


###  <a name="bkmk_chipri"></a>Podrzędna lokacja główna  
Każda podrzędna lokacja główna w hierarchii z centralną lokacją administracyjną obsługuje następujące funkcje:  

-   150 000 łączna liczba klientów i urządzeń, które nie są ograniczone do określonej grupy lub typu, tak długo, jak obsługa nie może przekraczać liczba, która jest obsługiwana dla hierarchii.  

Na przykład lokacji głównej, która obsługuje 25 000 komputerów, z systemem Mac i Windows CE 7.0 (ponieważ jest to limit dla hierarchii), następnie może obsługiwać dodatkowe 125,000 komputerów stacjonarnych. Całkowita liczba obsługiwanych urządzeń do podrzędnej lokacji głównej obsługiwanych maksymalny limit 150,000 otwarte.

###  <a name="bkmk_pri"></a>Autonomicznej lokacji głównej  
Autonomiczna lokacja główna obsługuje następującej liczby urządzeń:  

-   175,000 łączna liczba klientów i urządzeń, nie może przekraczać:  

    -   150 000 komputerów stacjonarnych (komputery z systemem Windows, Linux i UNIX)  

    -   urządzenia 25 000, z systemem Mac i Windows CE 7.0

    -   Jeden z następujących elementów, w zależności od sposobu wdrożenia obsługuje zarządzanie urządzeniami przenośnymi:  

        -   50 000 urządzeń, którymi można zarządzać za pomocą lokalnych MDM  

        -   150 000 chmurze urządzeń  

Na przykład autonomicznej lokacji głównej, która obsługuje 150 000 komputerów stacjonarnych i 10 000 komputerów Mac lub Windows CE 7.0 może obsługiwać tylko dodatkowych urządzeń 15 000. Te urządzenia może być oparte na chmurze lub zarządzanych za pomocą lokalnego zarządzania urządzeniami przenośnymi.  

###  <a name="bkmk_sec"></a>Lokacje dodatkowe  
Lokacje dodatkowe obsługują następujące czynności:  

-   15 000 komputerów stacjonarnych (komputery z systemem Windows, Linux i UNIX)  

###  <a name="bkmk_mp"></a>Punkty zarządzania  
Każdy punkt zarządzania może obsłużyć następującej liczby urządzeń:  

-   25 000 łączna liczba klientów i urządzeń, nie może przekraczać:  

    -   25 000 komputerów stacjonarnych (komputery z systemem Windows, Linux i UNIX)  

    -   Jeden z następujących (nie oba):  

        -   10 000 urządzeń, które są zarządzane przy użyciu lokalnego MDM  

        -   10 000 urządzenia, z systemem Mac i Windows CE 7.0 klientów

