---
title: Podstawy Lokacje i hierarchie | Dokumentacja firmy Microsoft
description: Uzyskaj podstawowe informacje o lokacji programu System Center Configuration Manager i hierarchii.
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4db1e15f-e832-4cf9-be33-d3971e635a55
caps.latest.revision: 6
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 68527c0e82861106b7ec28b34bffa8fd74b2dd4a
ms.openlocfilehash: f13f38be2a19ab8a1ead246e5272515dd0570984
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="fundamentals-of-sites-and-hierarchies-for-system-center-configuration-manager"></a>Podstawowe pojęcia dotyczące lokacji i hierarchii w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Wdrażanie programu System Center Configuration Manager musi być zainstalowany w domenie usługi Active Directory. Podstawa to wdrożenie obejmuje lokacji programu Configuration Manager, które tworzą hierarchię lokacji. Od jednej lokacji do hierarchii wielu lokacji — typ i lokalizacja instalowanych lokacji zapewniają możliwość skalowania (rozbudowy i rozszerzenia) wdrożenia w razie potrzeby i dostarczają kluczowe usługi dla zarządzanych użytkowników i urządzeń.

## <a name="hierarchies-of-sites"></a>Hierarchie lokacji
Po zainstalowaniu programu System Center Configuration Manager po raz pierwszy pierwszą instalowaną lokacją programu Configuration Manager określa zakres hierarchii. Pierwszej lokacji programu Configuration Manager jest foundation, z którego będzie zarządzać urządzeniami i użytkownikami w przedsiębiorstwie. Ten pierwszy lokacji musi być centralnej lokacji administracyjnej lub autonomicznej lokacji głównej.  

 A *witryny administracji centralnej* odpowiedni w przypadku wdrożeń na dużą skalę, oferuje centralny punkt administracji i zapewnia elastyczność do obsługi urządzeń wprowadzonych w globalnej infrastrukturze sieciowej. Po zainstalowaniu centralnej lokacji administracyjnej należy zainstalować jeden lub więcej lokacji głównych jako lokacji podrzędnych. Ta konfiguracja jest konieczne, ponieważ witryny administracji centralnej nie obsługuje bezpośrednio zarządzanie urządzeniami, czyli funkcja lokacji głównej. Witryna Administracja centralna obsługuje wiele lokacji podstawowej podrzędnych. Lokacje podstawowe podrzędne są używane do bezpośredniego zarządzania urządzeniami oraz sterowania przepustowością w przypadku zarządzanych urządzeń są w różnych lokalizacjach geograficznych.  

 A *autonomicznej lokacji głównej* jest przydatna przy mniejszych wdrożeniach i może służyć do zarządzania urządzeniami bez konieczności instalowania dodatkowych lokacji. Mimo że autonomicznej lokacji głównej można ograniczyć rozmiar wdrożenia, obsługuje scenariusza rozszerzania hierarchii w późniejszym czasie przez zainstalowanie nowej witryny Administracja centralna. W tym scenariuszu rozszerzania lokacji autonomicznej lokacji głównej staje się lokacją podrzędną.- i można zainstalować dodatkowe Lokacje podrzędną poniżej nowej witryny Administracja centralna. Następnie można rozwinąć wdrożeniu wstępnym do przyszłego rozwoju firmy.  

> [!TIP]  
>  Autonomiczną lokacją główną a lokacją podrzędną.-naprawdę są tego samego typu witryny: lokacji głównej. Różnica nazw wynika z relacji w hierarchii, tworzonej wówczas, gdy używana jest również centralna lokacja administracyjna. Ta relacja hierarchii można również ograniczyć instalacji niektórych ról systemu lokacji, które rozszerzają funkcje programu Configuration Manager. To ograniczenie ról występuje, ponieważ niektóre role systemu lokacji można zainstalować tylko w lokacji najwyższego poziomu w hierarchii, centralnej lokacji administracyjnej lub autonomicznej lokacji głównej.  

 Po zainstalowaniu pierwszej lokacji można zainstalować dodatkowe lokacje. Jeśli pierwszej lokacji centralnej lokacji administracyjnej, można zainstalować co najmniej jedną lokacją podrzędną. Po zainstalowaniu lokacji głównej (autonomiczny lub podrzędną.-), można zainstalować co najmniej jednej lokacji dodatkowej.  

 *Lokację dodatkową* można zainstalować tylko jako lokację podrzędną względem lokacji głównej. Lokacja tego typu rozszerza zasięg lokacji głównej w celu zarządzania urządzeniami z wolnym połączeniem sieciowym. Mimo że lokacja pomocnicza rozszerza lokacji podstawowej, lokacji głównej zarządza wszystkich klientów. Lokacja dodatkowa zapewnia obsługę urządzeń w lokalizacjach zdalnych. Zapewnia obsługę kompresji, a następnie zarządzania transfer informacji w sieci, który można wysłać (wdrażania) na klientach, i że klienci wysyłają do witryny.  

 Na poniższych diagramach przedstawiono przykładowe schematy lokacji.  

 ![Przykłady hierarchii](media/Hierarchy_examples.png)  

 Więcej informacji znajduje się w następujących tematach:  

-   [Wprowadzenie do programu System Center Configuration Manager](../../core/understand/introduction.md)  

-   [Projektowanie hierarchii lokacji programu System Center Configuration Manager](../../core/plan-design/hierarchy/design-a-hierarchy-of-sites.md)  

-   [Zainstalowanie lokacji programu System Center Configuration Manager](/sccm/core/servers/deploy/install/installing-sites)  

## <a name="site-system-servers-and-site-system-roles"></a>Serwery systemu lokacji i role systemu lokacji  
 Każda lokacja programu Configuration Manager instaluje *ról systemu lokacji* obsługujące operacji zarządzania. Następujące role są domyślnie instalowane podczas instalowania lokacji:

-   Rola serwera lokacji jest przypisana do komputera, gdzie zainstalowaniu lokacji.

-   Rola serwera bazy danych lokacji jest przypisany do programu SQL Server, który obsługuje bazę danych lokacji.

Inne role systemu lokacji są opcjonalne i są używane tylko, gdy użytkownik chce korzystać z funkcji jest aktywny w roli systemu lokacji. Dowolny komputer hostujący rolę systemu lokacji jest określany jako serwer systemu lokacji.  

 Mniejsze wdrożenia programu Configuration Manager można początkowo uruchamiać wszystkie witryny role systemu bezpośrednio na komputerze serwera lokacji. Następnie jako zarządzanego środowiska i potrzebuje zwiększania, można zainstalować dodatkowe serwery systemu lokacji do hosta dodatkowe role systemu lokacji zwiększa wydajność witryny w świadczeniu usług do większej liczby urządzeń.  

 Informacje o różne role systemu lokacji znajdują się w temacie [ról systemu lokacji](../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md#bkmk_planroles) w [Planowanie serwerów systemu lokacji i ról systemu lokacji dla programu System Center Configuration Manager](../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md).

## <a name="publishing-site-information-to-active-directory-domain-services"></a>Publikowanie informacji o lokacji w Usługach domenowych Active Directory  
 Aby uprościć zarządzanie programu Configuration Manager, rozszerzenie schematu usługi Active Directory w celu obsługi szczegółowe informacje, które są używane przez program Configuration Manager i następnie mają witryn publikowanie informacji o ich klucza usług domenowych w usłudze Active Directory (AD DS). Następnie komputery, które mają być zarządzane mogły bezpiecznie pobierać informacje dotyczące lokacji z zaufanego źródła usług AD DS. Informacje dostępne do pobrania przez klienty identyfikują dostępne lokacje, serwery systemu lokacji i usługi udostępniane przez te serwery.  

 *Rozszerzanie schematu usługi Active Directory* odbywa się tylko jeden raz dla każdego lasu i może odbywać się przed lub po zainstalowaniu programu Configuration Manager.   W przypadku rozszerzania schematu, należy utworzyć nowy kontener usługi Active Directory o nazwie System zarządzania w każdej domenie. Kontener zawiera lokacji programu Configuration Manager, która będzie publikować dane wyszukiwania przez klientów. Aby uzyskać więcej informacji, zobacz [Przygotowanie usługi Active Directory do publikowania witryny](../../core/plan-design/network/extend-the-active-directory-schema.md).  

 *Publikowanie danych lokacji* zwiększa bezpieczeństwo hierarchii programu Configuration Manager i zmniejsza narzuty administracyjne, ale nie jest wymagane dla podstawowych funkcji programu Configuration Manager.  

