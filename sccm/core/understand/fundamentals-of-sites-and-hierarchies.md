---
title: "Podstawowe pojęcia dotyczące lokacji i hierarchii"
titleSuffix: Configuration Manager
description: "Uzyskać podstawowe informacje o programie System Center Configuration Manager Lokacje i hierarchie."
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4db1e15f-e832-4cf9-be33-d3971e635a55
caps.latest.revision: "6"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: be4fb2b8d4c49981f7a801aff2175d4f0762e8c3
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="fundamentals-of-sites-and-hierarchies-for-system-center-configuration-manager"></a>Podstawowe pojęcia dotyczące lokacji i hierarchii w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Wdrażanie programu System Center Configuration Manager musi być zainstalowany w domenie usługi Active Directory. Foundation tego wdrożenia zawiera Lokacje programu Configuration Manager, które tworzą hierarchii lokacji. Od jednej lokacji do hierarchii wielu lokacji — typ i lokalizacja instalowanych lokacji zapewniają możliwość skalowania (rozbudowy i rozszerzenia) wdrożenia w razie potrzeby i dostarczają kluczowe usługi dla zarządzanych użytkowników i urządzeń.

## <a name="hierarchies-of-sites"></a>Hierarchie lokacji
Po zainstalowaniu programu System Center Configuration Manager po raz pierwszy, pierwszy instalowanej lokacji programu Configuration Manager określa zakres hierarchii. Pierwszej lokacji programu Configuration Manager to podstawę, z którego będą zarządzać urządzeniami i użytkownikami w przedsiębiorstwie. Pierwsza lokacja musi być centralnej lokacji administracyjnej lub autonomicznej lokacji głównej.  

 A *centralnej lokacji administracyjnej* jest przydatna przy dużych wdrożeniach, zapewnia centralny punkt administracji i zapewnia elastyczność do obsługi urządzeń rozproszonych w globalnej infrastrukturze sieciowej. Po zainstalowaniu centralnej lokacji administracyjnej, należy zainstalować jeden lub więcej lokacji głównych jako lokacji podrzędnych. Ta konfiguracja jest niezbędne, ponieważ centralna lokacja administracyjna nie obsługuje bezpośrednio zarządzania urządzeniami, ponieważ jest to funkcja lokacji głównej. Centralna lokacja administracyjna obsługuje wiele podrzędnych lokacji głównych. Podrzędnych lokacji głównych są używane do bezpośredniego zarządzania urządzeniami i sterowania przepustowością sieci w przypadku urządzeń zarządzanych znajdujących się w różnych lokalizacjach geograficznych.  

 A *autonomicznej lokacji głównej* jest przydatna przy mniejszych wdrożeniach i może służyć do zarządzania urządzeniami bez konieczności instalowania dodatkowych lokacji. Mimo że autonomiczna lokacja główna umożliwia ograniczenie rozmiaru wdrożenia, obsługuje scenariusza rozszerzania hierarchii w późniejszym czasie, instalując nową centralną lokację administracyjną. W tym scenariuszu rozszerzania lokacji autonomiczna lokacja główna staje się podrzędną lokacją główną, a można zainstalować dodatkowe podrzędnych lokacji głównych poniżej nowej centralnej lokacji administracyjnej. Następnie można rozszerzyć początkowe wdrożenie na potrzeby przyszłego rozwoju przedsiębiorstwa.  

> [!TIP]  
>  Autonomicznej lokacji głównej i lokacji podrzędnej naprawdę są tego samego typu lokacji: lokacji głównej. Różnica nazw wynika z relacji w hierarchii, tworzonej wówczas, gdy używana jest również centralna lokacja administracyjna. Relacja w hierarchii może również ograniczać instalację określonych ról systemu lokacji rozszerzających funkcje programu Configuration Manager. To ograniczenie ról występuje, ponieważ określone role systemu lokacji można zainstalować tylko w lokacji najwyższego poziomu w hierarchii, centralnej lokacji administracyjnej lub autonomicznej lokacji głównej.  

 Po zainstalowaniu pierwszej lokacji można zainstalować dodatkowe lokacje. Jeśli pierwsza lokacja była centralną lokację administracyjną, można zainstalować jeden lub więcej podrzędnych lokacji głównych. Po zainstalowaniu lokacji głównej (autonomicznej lub podrzędnej) można zainstalować co najmniej jednej lokacji dodatkowej.  

 *Lokację dodatkową* można zainstalować tylko jako lokację podrzędną względem lokacji głównej. Lokacja tego typu rozszerza zasięg lokacji głównej w celu zarządzania urządzeniami z wolnym połączeniem sieciowym. Mimo że lokacja dodatkowa rozszerza lokację główną, lokacji głównej zarządza wszystkich klientów. Lokacja dodatkowa zapewnia obsługę urządzeń w lokalizacjach zdalnych. Zapewnia obsługę kompresowania, a następnie zarządzanie transferem danych w sieci, który możesz wysłać (wdrażanych) do klientów, i że klienci wysyłają do witryny.  

 Na poniższych diagramach przedstawiono przykładowe schematy lokacji.  

 ![Przykłady hierarchii](media/Hierarchy_examples.png)  

 Więcej informacji znajduje się w następujących tematach:  

-   [Wprowadzenie do programu System Center Configuration Manager](../../core/understand/introduction.md)  

-   [Projektowanie hierarchii lokacji programu System Center Configuration Manager](../../core/plan-design/hierarchy/design-a-hierarchy-of-sites.md)  

-   [Instalowanie lokacji programu System Center Configuration Manager](/sccm/core/servers/deploy/install/installing-sites)  

## <a name="site-system-servers-and-site-system-roles"></a>Serwery systemu lokacji i role systemu lokacji  
 Każda lokacja programu Configuration Manager instaluje *role systemu lokacji* obsługujące operacje zarządzania. Następujące role są instalowane domyślnie podczas instalowania lokacji:

-   Rola serwera lokacji jest przypisana do komputera, w którym zostanie zainstalowana lokacja.

-   Rola serwera bazy danych lokacji jest przypisany do programu SQL Server, który jest hostem bazy danych lokacji.

Inne role systemu lokacji są opcjonalne i są używane tylko, jeśli chcesz korzystać z funkcji, który jest aktywny w roli systemu lokacji. Dowolny komputer hostujący rolę systemu lokacji jest określany jako serwer systemu lokacji.  

 Przypadku mniejszego wdrożenia programu Configuration Manager można początkowo uruchamiać wszystkie witryny role systemu bezpośrednio na komputerze serwera lokacji. Następnie jako zarządzanego środowiska i wzrostu potrzeb, można zainstalować dodatkowe serwery systemu lokacji do obsługi ról systemu lokacji dodatkowej w celu poprawy wydajności witryny w zapewnianiu usług dla większej liczby urządzeń.  

 Aby uzyskać informacje o różnych rolach systemu lokacji, zobacz [role systemu lokacji](../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md#bkmk_planroles) w [Planowanie serwerów systemu lokacji i ról systemu lokacji dla programu System Center Configuration Manager](../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md).

## <a name="publishing-site-information-to-active-directory-domain-services"></a>Publikowanie informacji o lokacji w Usługach domenowych Active Directory  
 Uproszczenie zarządzania programu Configuration Manager, można rozszerzyć schemat usługi Active Directory w celu obsługi szczegółów używanych przez program Configuration Manager, a następnie nakazać lokacjom publikowanie ich kluczowych informacji do usług domenowych w usłudze Active Directory (AD DS). Następnie komputery, które mają być zarządzane mogą bezpieczne pobieranie informacji dotyczących lokacji z zaufanego źródła, usług AD DS. Informacje dostępne do pobrania przez klienty identyfikują dostępne lokacje, serwery systemu lokacji i usługi udostępniane przez te serwery.  

 *Rozszerzanie schematu usługi Active Directory* odbywa się tylko jeden raz dla każdego lasu i może odbywać się przed lub po zainstalowaniu programu Configuration Manager.   Po rozszerzeniu schematu należy utworzyć nowy kontener usługi Active Directory o nazwie System zarządzania w każdej domenie. Kontener zawiera lokację programu Configuration Manager, która będzie publikować dane wyszukiwania przez klientów. Aby uzyskać więcej informacji, zobacz [Przygotowanie usługi Active Directory do publikowania witryny](../../core/plan-design/network/extend-the-active-directory-schema.md).  

 *Publikowanie danych lokacji* zwiększa bezpieczeństwo hierarchii programu Configuration Manager i zmniejsza narzuty administracyjne, ale nie jest wymagany do podstawowych funkcji programu Configuration Manager.  
