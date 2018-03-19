---
title: "Przygotowywanie serwerów z systemem Windows"
titleSuffix: Configuration Manager
description: "Upewnij się, że komputer spełnia wymagania wstępne dotyczące serwera lokacji lub serwer systemu lokacji dla programu System Center Configuration Manager."
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
caps.latest.revision: 
caps.handback.revision: 
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: a55322868d45cf1d2b3004e21d641ca5299aa957
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2017
---
# <a name="prepare-windows-servers-to-support-system-center-configuration-manager"></a>Przygotowywanie serwerów z systemem Windows do obsługi programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Przed użyciem komputerem z systemem Windows jako serwera systemu lokacji dla programu System Center Configuration Manager, komputer musi spełniać wymagania wstępne dotyczące jego planowanym użyciem jako serwera lokacji lub serwer systemu lokacji.  

-   Te wymagania wstępne często zawierają funkcje systemu Windows lub ról, które są włączane za pomocą Menedżera serwera komputerów.  

-   Ponieważ metody, aby włączyć role i funkcje systemu Windows różni się w różnych systemach operacyjnych, zapoznaj się z dokumentacją systemu operacyjnego, aby uzyskać szczegółowe informacje o sposobie konfigurowania systemu operacyjnego, którego używasz.  

Informacje przedstawione w tym artykule omówiono typy konfiguracji systemu Windows, które są wymagane do obsługi systemów lokacji programu Configuration Manager. Szczegółowe informacje dotyczące konfiguracji dla określonych ról systemu lokacji, zobacz [lokacji i wymagania wstępne systemu lokacji](/sccm/core/plan-design/configs/site-and-site-system-prerequisites).

##  <a name="BKMK_WinFeatures"></a>Role i funkcje systemu Windows  
 Po skonfigurowaniu funkcji systemu Windows i role na komputerze, może być konieczne ponowne uruchomienie komputera w celu ukończenia konfiguracji. W związku z tym jest dobrym rozwiązaniem, aby zidentyfikować komputery, które będą obsługiwać określonych ról systemu lokacji, przed zainstalowaniem lokacji programu Configuration Manager lub serwera systemu lokacji.
### <a name="features"></a>Funkcje  
 Następujące funkcje systemu Windows są wymagane przez niektóre serwery systemu lokacji i należy ją skonfigurować przed zainstalowaniem roli systemu lokacji na tym komputerze.  

-   **.NET framework**: W tym  

    -   Platforma ASP.NET  
    -   Aktywacja HTTP  
    -   Aktywacja bez HTTP  
    -   Usługi Windows Communication Foundation (WCF)  

    Różne role systemu lokacji wymagają różnych wersji programu .NET Framework.  

    .NET Framework 4.0 lub nowszy nie jest zgodne z wersjami 3.5 i starsze wersje, jeśli różne wersje są wymagane, należy zaplanować włączenie poszczególnych wersji na tym samym komputerze.  

-   **Usługi inteligentnego transferu (BITS) w tle**: Punkty zarządzania wymagają usługi BITS (i automatycznie wybieranych opcji) do obsługi komunikacji z zarządzanymi urządzeniami.  

-   **Usługa BranchCache**: Punkty dystrybucji można łączyć z usługą BranchCache do obsługi klientów korzystających z usługi BranchCache.  

-   **Funkcja deduplikacji danych**: Punkty dystrybucji można skonfigurować przy użyciu i korzystać z deduplikacji danych.  

-   **Remote Differential Compression (RDC)**: Każdy komputer obsługujący serwer lokacji lub punkt dystrybucji wymaga kompresji RDC.   
    Kompresja RDC służy do generowania podpisów pakietów i porównywania podpisów.  

### <a name="roles"></a>Role  
 Następujące role systemu Windows są wymagane do obsługi określonych funkcji, takich jak aktualizacje oprogramowania i wdrożenia systemu operacyjnego, podczas gdy usługi IIS są wymagane przez najbardziej typowe role systemu lokacji.  

 -   **Usługi rejestracji urządzeń sieciowych** (w usługach certyfikatów usługi Active Directory):  Ta rola systemu Windows jest wymagana do używania profilów certyfikatów w programie Configuration Manager.  

 -   **Serwer sieci Web (IIS)**: W tym:  
    -   Wspólne funkcje HTTP >  
        -   Przekierowywanie HTTP  
    -   Projektowanie aplikacji >  
        -   Rozszerzenia platformy .NET  
        -   Platforma ASP.NET  
        -   Rozszerzenia ISAPI  
        -   Filtry ISAPI  
    -   Narzędzia zarządzania >  
        -   Zgodność z narzędziami zarządzania usługami IIS 6  
        -   Zgodność z metabazą usług IIS 6  
        -   Zgodność z usług IIS 6 w systemie Windows Management Instrumentation (WMI)  
    -   Zabezpieczenia >  
        -   Filtrowanie żądań  
        -   Uwierzytelnianie systemu Windows  

 Następujące role systemu lokacji należy użyć co najmniej jednego z wymienionych konfiguracji usług IIS:  
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

    Oprócz tych konfiguracji usług IIS, może być konieczne ustawienie [Filtrowanie żądań usług IIS w punktach dystrybucji](#BKMK_IISFiltering).  

-   **Usługi wdrażania systemu Windows**: Ta rola jest używana z wdrożeniem systemu operacyjnego.  
-   **Windows Server Update Services**: Ta rola jest wymagana przy wdrażaniu aktualizacji oprogramowania.  

##  <a name="BKMK_IISFiltering"></a>Filtrowanie żądań usług IIS dla punktów dystrybucji  
 Domyślnie usługi IIS używają Filtrowanie żądań do blokowania kilka rozszerzeń nazw plików i lokalizacji folderów dostępu przez komunikację HTTP lub HTTPS. W punkcie dystrybucji uniemożliwia to klientom pobieranie pakietów, które zostały zablokowane rozszerzenia lub lokalizacje folderów.  

 Gdy pliki źródłowe pakietu mają rozszerzenia blokowane przez konfigurację filtrowania żądań w usługach IIS, należy skonfigurować filtrowanie żądań umożliwia im. Można to zrobić przez [edytowanie funkcji filtrowania żądań](https://technet.microsoft.com/library/hh831621.aspx) w menedżerze usług IIS na komputerach punktów dystrybucji.  

 Ponadto następujące rozszerzenia nazw plików są używane przez program Configuration Manager pakietów i aplikacji. Upewnij się, że konfiguracje filtrowania żądań nie blokują następujących rozszerzeń plików:  

-   *.PCK  
-   *.PKG  
-   *.STA  
-   *.TAR  

Na przykład pliki źródłowe wdrożenia oprogramowania, może to folder o nazwie **bin** lub plik ma **.mdb** rozszerzenia nazwy pliku.  

-   Domyślnie Filtrowanie żądań usług IIS blokuje dostęp do tych elementów (**bin** jest blokowane jako Segment ukryty i **.mdb** jest blokowane jako rozszerzenie nazwy pliku).  

-   W przypadku używania domyślnej konfiguracji usług IIS w punkcie dystrybucji klienci używający usługi BITS nie będą mogli pobierać tego wdrożenia oprogramowania z punktu dystrybucji i wskazywać oczekiwania na zawartość.  

-   Aby umożliwić klientom pobieranie tej zawartości, na każdym odpowiednim punkcie dystrybucji, Edytuj **Filtrowanie żądań** w Menedżerze usług IIS, aby zezwolić na dostęp do rozszerzeń plików i folderów, które znajdują się w pakietach i aplikacjach, które można wdrożyć.  

> [!IMPORTANT]  
>  Edycja filtru żądań może zwiększyć podatność komputera na atak.  
>   
>  -   Zmiany wprowadzane w poziomie serwera dotyczą wszystkich witryn sieci Web na serwerze.  
> -   Zmiany wprowadzone w poszczególnych witrynach sieci Web dotyczą tylko tych witryn.  
>   
>  Najlepszym rozwiązaniem bezpieczeństwa jest uruchomienie programu Configuration Manager na dedykowanym serwerze sieci web. Jeśli na serwerze sieci web muszą być wykonywane inne aplikacje, należy użyć niestandardowej witryny sieci Web dla programu Configuration Manager. Aby uzyskać informacje, zobacz [Witryny sieci Web serwerów systemu lokacji w programie System Center Configuration Manager](../../../core/plan-design/network/websites-for-site-system-servers.md).  

## <a name="http-verbs"></a>Zlecenia HTTP
**Punkty zarządzania:** Aby upewnić się, że klienci mogą się komunikować z punktem zarządzania, na serwerze punktu zarządzania upewnij się, że są dozwolone na następujące czasowniki HTTP:  
 - GET
 - POST
 - CCM_POST
 - HEAD
 - PROPFIND

**Punkty dystrybucji:** Punkty dystrybucji wymagają, że mogą się z następujących zleceń HTTP jako:
 - GET
 - HEAD
 - PROPFIND

Aby uzyskać informacje o sposobie konfigurowania filtrowania żądań, zobacz [skonfigurować filtrowanie żądań w usługach IIS](https://technet.microsoft.com/library/hh831621.aspx#Verbs) w witrynie TechNet lub w podobnej dokumentacji, która ma zastosowanie do wersji systemu Windows Server, który jest hostem punktu zarządzania.
