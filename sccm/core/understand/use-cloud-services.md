---
title: "Użyj usług w chmurze z programem Configuration Manager | Dokumentacja firmy Microsoft"
description: "Udostępnianie zasobów w chmurze programu System Center Configuration Manager uzupełnienie infrastruktury lokalnej."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 24fca61e-9cdb-447a-ad7a-f4d2e4fd6704
caps.latest.revision: 10
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d7ddd48cc4e75b12f893e686b847d66058441e1
ms.openlocfilehash: 52f7c63d155d5c34f0f12e13020767dec1867dab
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="use-cloud-services-with-system-center-configuration-manager"></a>Korzystanie z usług w chmurze w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

System Center Configuration Manager obsługuje kilka opcji oparte na chmurze. Te można uzupełnić infrastruktury lokalnej i może pomóc w rozwiązywaniu problemów biznesowych, takich jak:  

-   Jak zarządzać PRZYNIEŚ (za pomocą usługi Intune do zarządzania urządzeniami przenośnymi).  

-   Jak udostępniać zasoby zawartości klientom izolowane lub zasobów w sieci intranet, poza zaporą firmy (przy użyciu punktów dystrybucji w chmurze).  

-   Jak skalować infrastruktury, gdy sprzętu fizycznego nie jest dostępna lub nie został umieszczony logicznie dla różnych potrzeb (przy użyciu maszyny wirtualne Microsoft Azure).  

Udostępnianie zasobów w chmurze nie jest coś, co należy zrobić przed wdrożeniem programu Configuration Manager, może być korzystne zrozumienie tych opcji przed postępu zbytnio w planie projektu hierarchii. Korzystanie z zasobów w chmurze mogą zaoszczędzić czas i pieniądze, podczas rozwiązywania problemów biznesowych nie infrastruktury lokalnej.  

## <a name="cloud-based-resources-you-can-use-with-configuration-manager"></a>Zasoby oparte na chmurze korzystania z programu Configuration Manager  
 Każda opcja charakteryzuje się innymi wymaganiami, w związku z czym należy zapoznać się szczegółowo z każdą z nich, aby zrozumieć związane z nią charakterystyczne wymagania, ograniczenia i potencjalne koszty dodatkowe.  

-   Informacji dotyczących punktów dystrybucji w chmurze, zobacz [zainstalować punkty dystrybucji w chmurze](/sccm/core/servers/deploy/configure/install-cloud-based-distribution-points-in-microsoft-azure).

-   Aby uzyskać więcej informacji o systemie Azure, zobacz [Azure](http://go.microsoft.com/fwlink/p/?LinkId=262965) w bibliotece MSDN.  

### <a name="azure-virtual-machines-for-cloud-based-infrastructure"></a>Maszyny wirtualne platformy Azure (w przypadku infrastruktury opartej na chmurze)  
 Obsługa programu Configuration Manager za pomocą komputerów uruchamianych na maszynach wirtualnych platformy Azure, podobnie jak uruchamiania lokalnych w sieci firmowej fizycznych. Maszyn wirtualnych platformy Azure możesz używać w następujących scenariuszach:  

-   **Scenariusz 1:** Można uruchomić program Configuration Manager na maszynie wirtualnej i używany do zarządzania klientami instalowane w innych maszyn wirtualnych.  

-   **Scenariusz 2:** Można uruchomić program Configuration Manager na maszynie wirtualnej i używany do zarządzania klientami, które nie są uruchomione w systemie Azure.  

-   **Scenariusz 3:** Podczas przeprowadzania innych ról w sieci firmowej fizycznej (z połączeniem sieciowym odpowiednie dla komunikacji) można uruchomić różne role systemu lokacji programu Configuration Manager w maszynach wirtualnych.  

Te same wymagania dotyczące sieci, systemy operacyjne i wymagania sprzętowe, które dotyczą Instalowanie programu Configuration Manager w sieci firmowej fizycznych dotyczą również instalacji programu Configuration Manager w systemie Azure.  

Maszyny wirtualne platformy Azure przy użyciu subskrypcji platformy Azure jest wymagany. Pociągnąć za sobą koszty zależą od liczby maszyn wirtualnych, którego używasz, konfiguracji i użycia zasobów w chmurze.  

Ponadto lokacji programu Configuration Manager i klientów uruchamianych na maszynach wirtualnych Azure podlegają licencją lokalnej instalacji.  

### <a name="azure-services-for-cloud-based-distribution-points"></a>Usług Azure (dla punktów dystrybucji w chmurze)  
 Usługa Azure służy do obsługi punktu dystrybucji programu Configuration Manager, który nosi nazwę punktu dystrybucji w chmurze nosi nazwę. Możesz [użycia punktu dystrybucji w chmurze z System Center Configuration Manager](../../core/plan-design/hierarchy/use-a-cloud-based-distribution-point.md) obok lokalne punkty dystrybucji i punkty dystrybucji wdrożone w maszyny wirtualne platformy Azure.  

 Sytuacja ta różni się od korzystania z maszyny wirtualnej platformy Azure, na której wdrożono rolę systemu lokacji. Punkty dystrybucji w chmurze:  

-   Uruchom jako usługi w programie Azure, nie na maszynie wirtualnej.  

-   Automatyczne skalowanie w celu spełnienia zwiększone zawartości żądania od klientów.  

-   Obsługa klientów internetowych i intranetowych.  

Przy użyciu Azure do punktów dystrybucji hosta subskrypcji platformy Azure jest wymagany. Naliczone opłaty zależą od ilości danych transferowanych do i z usługi.  

### <a name="microsoft-intune-for-mobile-device-management"></a>Microsoft Intune (do zarządzania urządzeniami przenośnymi)  
 Subskrypcja Microsoft Intune można zintegrować z programem Configuration Manager umożliwiających zarządzanie urządzeniami przy użyciu usługi Intune. Integracja ta:  

-   Konfiguracja hybrydowych, jest nazywana i rozszerza program Configuration Manager (lub Intune, w zależności od Twojego perspektywy) obsługuje szeroką gamę urządzeń.  

-   Wymaga programu Microsoft Intune Connector Rola systemu lokacji.  

-   Wymaga posiadania oddzielnych subskrypcji usługi Intune z wystarczającą liczbę licencji dla urządzeń, które będą zarządzane za pomocą usługi Intune.  

Mimo że jest używana Azure, nie wymaga skonfigurowania niezależnie Azure nie podlegają dodatkowych kosztów poza tym subskrypcji usługi Intune.  

### <a name="additional-configuration-manager-capabilities"></a>Dodatkowe funkcje programu Configuration Manager  
 Niektóre funkcje programu Configuration Manager mogą łączyć się usług w chmurze, takich jak:  

-   Windows Server Update Services (WSUS).  

-   Menedżer konfiguracji usługi chmury, do pobierania aktualizacji dla programu Configuration Manager.  

Te dodatkowe możliwości nie wymagają posiadania subskrypcji platformy Azure. Nie trzeba skonfigurować określone połączenia, certyfikaty lub usług w chmurze. Zamiast tego one są zarządzane automatycznie przez program Configuration Manager dla Ciebie. Wszystko, co należy zrobić to systemy uaktualnianej lokacji upewnij się, a urządzenia mogą uzyskać dostęp do adresów URL internetowych.  

##  <a name="BKMK_CloudSec"></a>Zabezpieczenia dla usług w chmurze  
 Program Configuration Manager używa certyfikatów do udostępniania i zapewniania dostępu do zawartości Azure oraz do zarządzania usługami, których używasz. Menedżer konfiguracji szyfruje dane przechowywane w Azure, ale nie zapewnia dodatkowe kontrole zabezpieczeń lub dane poza tymi, które zapewnia Azure.  

 Aby uzyskać więcej informacji zobacz szczegóły w scenariuszach różnych zasobów chmurowych. Można również wyświetlić następujące tematy Azure zabezpieczeń:  

-   [Azure: Opis Security Account Management in Azure](http://go.microsoft.com/fwlink/p/?LinkId=262968)  

-   [Przegląd zabezpieczeń systemu Azure](http://go.microsoft.com/fwlink/p/?LinkId=262970)  

-   [Get Past skrzyżowaniach zabezpieczeń w migracji do chmury](http://go.microsoft.com/fwlink/p/?LinkId=262971)  

-   [Bezpieczeństwo danych w Azure część 1 z 2](http://go.microsoft.com/fwlink/p/?LinkId=262974)  

