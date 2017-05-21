---
title: "Przygotowanie serwerów z systemem Windows | Dokumentacja firmy Microsoft"
description: "Upewnij się, że komputer spełnia wymagania wstępne w celu użycia jako serwer lokacji lub serwer systemu lokacji dla programu System Center Configuration Manager."
ms.custom: na
ms.date: 2/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 2aca914f-641e-4bc8-98d4-bbf0a2a5276f
caps.latest.revision: 10
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dd102603356864add4084c6881c39bebcbd635f2
ms.openlocfilehash: 9b97dedb5d2be0bd2e47260033e6e4361467dc4e
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="prepare-windows-servers-to-support-system-center-configuration-manager"></a>Przygotowywanie serwerów z systemem Windows do obsługi programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Przed użyciem komputer z systemem Windows jako serwera systemu lokacji dla programu System Center Configuration Manager, komputer musi spełniać wymagania wstępne dotyczące jego zamierzone użycie jako serwer lokacji lub serwera systemu lokacji.  

-   Te warunki wstępne są często zawierają jedną lub więcej funkcji systemu Windows lub ról, które są włączane przy użyciu Menedżera serwera komputerów.  

-   Ponieważ metody umożliwiające ról i funkcji systemu Windows różni się między systemami operacyjnymi, zapoznaj się z dokumentacją systemu operacyjnego, aby uzyskać szczegółowe informacje dotyczące sposobu konfigurowania systemu operacyjnego, którego używasz.  

Informacje przedstawione w tym artykule omówiono typy konfiguracji systemu Windows, które są wymagane do obsługi systemów lokacji programu Configuration Manager. Szczegółowe informacje dotyczące konfiguracji dla określonych ról systemu lokacji, zobacz [lokacji i wymagań wstępnych systemu lokacji](/sccm/core/plan-design/configs/site-and-site-system-prerequisites).

##  <a name="BKMK_WinFeatures"></a>Role i funkcje systemu Windows  
 Podczas konfigurowania funkcji systemu Windows i rolami komputera, może być konieczne ponowne uruchomienie komputera w celu ukończenia tej konfiguracji. Dlatego jest dobrym pomysłem jest identyfikację komputerów, które będą obsługiwać określonych ról systemu lokacji, przed zainstalowaniem lokacji programu Configuration Manager lub serwer systemu lokacji.
### <a name="features"></a>Funkcje  
 Następujące funkcje systemu Windows są wymagane na niektórych serwerach systemu lokacji i powinny zostać skonfigurowane przed zainstalowaniem roli systemu lokacji na tym komputerze.  

-   **.NET framework**: W tym  

    -   Platforma ASP.NET  
    -   Aktywacja HTTP  
    -   Aktywacja bez HTTP  
    -   Usługi Windows Communication Foundation (WCF)  

    Różne role systemu lokacji wymagają różnych wersji programu .NET Framework.  

    .NET Framework w wersji 4.0 lub nowszej nie jest zgodne z poprzednimi wersjami zastąpić 3.5 i wcześniejszych wersji, gdy wersje są wymienione jako wymagane, planowane jest udostępnienie każdej wersji na tym samym komputerze.  

-   **Usługi inteligentnego transferu (BITS) w tle**: Punkty zarządzania wymagają usługi BITS (i automatycznie wybrane opcje) do obsługi komunikacji z zarządzanych urządzeń.  

-   **Usługa BranchCache**: Punkty dystrybucji można ustawić za pomocą usługi BranchCache, do obsługi klientów korzystających z usługi BranchCache.  

-   **Funkcja deduplikacji danych**: Punkty dystrybucji można skonfigurować za pomocą i korzystać z funkcji deduplikacji danych.  

-   **Zdalna kompresja różnicowa (RDC)**: Każdy komputer, który jest hostem serwera lokacji lub punktu dystrybucji wymaga usługi Podłączanie pulpitu zdalnego.   
    Kompresja RDC służy do generowania podpisów pakietów i porównywania podpisów.  

### <a name="roles"></a>Role  
 Następujące role systemu Windows są wymagane do obsługi określonych funkcji, takich jak aktualizacje oprogramowania i wdrożenia systemu operacyjnego, podczas gdy usługi IIS są wymagane przez najbardziej typowe role systemu lokacji.  

 -   **Usługi rejestracji urządzeń sieciowych** (w ramach usługi certyfikatów Active Directory):  Ta rola systemu Windows jest warunkiem wstępnym warto zastosować profile certyfikatów w programie Configuration Manager.  

 -   **Serwer sieci Web (IIS)**: W tym:  
    -   Wspólne funkcje HTTP >  
        -   Przekierowywanie HTTP  
    -   Tworzenie aplikacji >  
        -   Rozszerzenia platformy .NET  
        -   Platforma ASP.NET  
        -   Rozszerzenia ISAPI  
        -   Filtry ISAPI  
    -   Narzędzia do zarządzania >  
        -   Zgodność z narzędziami zarządzania usługami IIS 6  
        -   Zgodność z metabazą usług IIS 6  
        -   Zgodność z usług IIS 6 w systemie Windows Management Instrumentation (WMI)  
    -   Zabezpieczenia >  
        -   Filtrowanie żądań  
        -   Uwierzytelnianie systemu Windows  

 Następujące role systemu lokacji należy użyć co najmniej jeden z wymienionych konfiguracji usług IIS:  
    -   Punkt usługi sieci Web Wykaz aplikacji  
    -   Punkt witryny sieci Web katalogu aplikacji  
    -   Punkt dystrybucji  
    -   Punkt rejestracji  
    -   Punkt proxy rejestracji  
    -   Rezerwowy punkt stanu  
    -   Punkt zarządzania  
    -   Punkt aktualizacji oprogramowania  
    -   Punkt migracji stanu     

    Minimalna wymagana wersja usług IIS to wersja dostarczana z systemem operacyjnym serwera lokacji.  

    Oprócz tych konfiguracji usług IIS, może być konieczne ustawienie [filtrowania żądań usług IIS dla punktów dystrybucji](#BKMK_IISFiltering).  

-   **Usługi wdrażania systemu Windows**: Ta rola jest używana z wdrożeniem systemu operacyjnego.  
-   **Windows Server Update Services**: Ta rola jest wymagana, gdy aktualizacje oprogramowania będą wdrażane.  

##  <a name="BKMK_IISFiltering"></a>Filtrowanie żądań usług IIS dla punktów dystrybucji  
 Domyślnie usługi IIS używa Filtrowanie żądań do zablokowania pewnych rozszerzeń nazw plików i lokalizacji folderów dostęp do komunikacji HTTP lub HTTPS. W punkcie dystrybucji to uniemożliwia klientom pobranie pakiety, które zostały zablokowane rozszerzenia lub lokalizacji folderu.  

 Gdy pliki źródłowe pakietu mają rozszerzenia blokowane przez konfigurację Filtrowanie żądań w usługach IIS, należy skonfigurować filtrowanie żądań umożliwia im. Można to zrobić przez [edytowanie funkcji filtrowania żądań](https://technet.microsoft.com/library/hh831621.aspx) w menedżerze usług IIS na komputerach punktów dystrybucji.  

 Ponadto następujące rozszerzenia nazw plików są używane przez program Configuration Manager pakiety i aplikacje. Upewnij się, Filtrowanie żądań konfiguracji nie należy blokować te rozszerzenia pliku:  

-   *.PCK  
-   *.PKG  
-   *.STA  
-   *.TAR  

Na przykład, pliki źródłowe dla wdrożenia oprogramowania może zawierać folder o nazwie **bin** lub plik, który ma **.mdb** rozszerzenie nazwy pliku.  

-   Domyślnie filtrowania żądań usług IIS blokuje dostęp do tych elementów (**bin** jest zablokowany jako Segment ukryty i **.mdb** jest zablokowany jako rozszerzenie nazwy pliku).  

-   W przypadku używania domyślnej konfiguracji usług IIS w punkcie dystrybucji klienci używający usługi BITS nie będą mogli pobierać tego wdrożenia oprogramowania z punktu dystrybucji i wskazywać oczekiwania na zawartość.  

-   Aby umożliwić klientom pobranie tej zawartości na każdym odnośnym punkcie dystrybucji, Edytuj **Filtrowanie żądań** w Menedżerze usług IIS, aby zezwolić na dostęp do rozszerzenia plików i folderów, które znajdują się w pakiety i aplikacje, które można wdrożyć.  

> [!IMPORTANT]  
>  Edycja filtru żądań może zwiększyć podatność komputera na atak.  
>   
>  -   Modyfikacje wprowadzone na poziomie serwera, mają zastosowanie do wszystkich witryn sieci Web na serwerze.  
> -   Zmiany wprowadzane w poszczególnych witryn sieci Web dotyczą tylko tej witryny sieci Web.  
>   
>  Najlepszym rozwiązaniem bezpieczeństwa jest uruchomienie programu Configuration Manager na dedykowanym serwerze sieci web. Jeśli inne aplikacje należy uruchomić na serwerze sieci web, należy użyć niestandardowej witryny sieci Web dla programu Configuration Manager. Aby uzyskać informacje, zobacz [Witryny sieci Web serwerów systemu lokacji w programie System Center Configuration Manager](../../../core/plan-design/network/websites-for-site-system-servers.md).  

## <a name="http-verbs"></a>Zleceń HTTP
**Punkty zarządzania:** Aby upewnić się, że klienci mogą się komunikować z punktem zarządzania, na serwerze punktu zarządzania upewnij się, że następujące zlecenia HTTP są dozwolone:  
 - GET
 - POST
 - CCM_POST
 - HEAD
 - PROPFIND

**Punkty dystrybucji:** Punkty dystrybucji wymagają, że następujące zlecenia HTTP jako dozwolone:
 - GET
 - HEAD
 - PROPFIND

Informacje o sposobie konfigurowania filtrowania żądań, zobacz [skonfigurować filtrowanie żądań w usługach IIS](https://technet.microsoft.com/library/hh831621.aspx#Verbs) w witrynie TechNet lub w podobnej dokumentacji, który ma zastosowanie do wersji systemu Windows Server, który jest hostem punktu zarządzania.

