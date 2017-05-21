---
title: Konfigurowanie lokacji | Dokumentacja firmy Microsoft
description: "Zapoznaj się z listą kontrolną, aby zapewnić, że należy wziąć pod uwagę najbardziej typowe konfiguracje, które wpływają na Lokacje i hierarchie."
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 9efb4061-f642-48bd-8332-3357ff5b3118
caps.latest.revision: 15
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5f1efaa776079b21d52b9936273380e9bb8963e9
ms.openlocfilehash: 862f420c063cb44c419d4904fbb4696efb739758
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="configure-sites-and-hierarchies-for-system-center-configuration-manager"></a>Konfigurowanie lokacji i hierarchii dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Po zainstalowaniu pierwszej lokacji programu System Center Configuration Manager lub dodać więcej lokacji do hierarchii, należy użyć poniższej listy kontrolnej, aby upewnić się, należy rozważyć najbardziej typowe konfiguracje, które wpływają na Lokacje i hierarchie.  

## <a name="checklist-of-common-configurations-for-new-and-additional-sites"></a>Lista kontrolna typowych konfiguracji dla nowych i dodatkowych lokacji  
Należy uwzględnić poniższe uwagi dotyczące konfiguracji, które stosują się do większości wdrożeń:

-   Niektóre opcje zależą od innych, takie jak grupy odnajdywania lasu usługi Active Directory, granice i granic.  

-   Niektóre konfiguracje mają przypisane wartości domyślne, których przynajmniej przez pewien czas nie trzeba zmieniać.  

-   Inne, takie jak grupy granic i grupy punktów dystrybucji, wymagają skonfigurowania przed rozpoczęciem używania.  

|Akcja|Szczegóły|  
|------------|-------------|  
|Konfigurowanie administracji opartej na rolach|Segregowanie przypisań administracyjnych do kontroli, którzy użytkownicy administracyjni można wyświetlać i zarządzać różnych obiektów i danych w środowisku programu Configuration Manager.<br /><br /> Konfiguracje dla administracji opartej na rolach są udostępniane wszystkim lokacjom w hierarchii.   <br/><br/>Aby uzyskać więcej informacji, zobacz [skonfigurowanie administracji opartej na rolach dla programu System Center Configuration Manager](../../../../core/servers/deploy/configure/configure-role-based-administration.md).|  
|Publikowanie danych lokacji w Usługach domenowych Active Directory (AD DS)|Ułatwia klientom znaleźć usług i efektywne wykorzystanie zasobów lokacji.<br /><br /> Należy najpierw [rozszerzyć schemat usługi Active Directory dla programu System Center Configuration Manager](../../../../core/plan-design/network/extend-the-active-directory-schema.md), i każdej lokacji musi być skonfigurowany indywidualnie do [publikowania danych lokacji programu System Center Configuration Manager](../../../../core/servers/deploy/configure/publish-site-data.md)|  
|Konfigurowanie punktu połączenia usługi|Planowanie zainstalować i skonfigurować punkt połączenia usługi w lokacji najwyższego poziomu w hierarchii. Aby uzyskać więcej informacji, zobacz [Informacje o punkcie połączenia z usługą w programie System Center Configuration Manager](../../../../core/servers/deploy/configure/about-the-service-connection-point.md).|  
|Dodawanie ról systemu lokacji|Zainstaluj co najmniej jeden dodatkowe role systemu lokacji dla poszczególnych witryn.  Aby uzyskać więcej informacji, zobacz [Dodaj role systemu lokacji dla programu System Center Configuration Manager](../../../../core/servers/deploy/configure/add-site-system-roles.md).|  
|Konfigurowanie granic lokacji i grup granic|Określ granice, które definiują lokalizacje sieciowe w sieci intranet, który może zawierać urządzeń, które mają być zarządzane. Następnie skonfiguruj grupy granic, dzięki czemu klientów w tych lokalizacjach sieciowych można znaleźć zasobów programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [zdefiniować granice lokacji i grup granic dla programu System Center Configuration Manager](../../../../core/servers/deploy/configure/define-site-boundaries-and-boundary-groups.md).|  
|Konfigurowanie grup punktów dystrybucji|Skonfiguruj logiczne grupy punktów dystrybucji, aby ułatwić zarządzanie wdrożeniami. Aby uzyskać więcej informacji, zobacz [umożliwia zarządzanie grupami punktów dystrybucji](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_manage) w [zainstalować i skonfigurować punkty dystrybucji programu System Center Configuration Manager](../../../../core/servers/deploy/configure/install-and-configure-distribution-points.md).|  
|Uruchamianie odnajdywania|Uruchom odnajdywanie w celu odnalezienia zasobów w sieci, w tym infrastruktury sieciowej, urządzeń i użytkowników.<br /><br /> Aby uzyskać więcej informacji, zobacz [Uruchamianie odnajdywania dla programu System Center Configuration Manager](../../../../core/servers/deploy/configure/run-discovery.md).|  
|Dodaj nadmiarowości i wydajności dla administratorów, którzy zarządzają infrastrukturą|Instalowanie dodatkowych dostawców programu SMS i konsole programu Configuration Manager w celu zwiększenia pojemności dla administratorów do zarządzania infrastrukturą:<br /><br /> **Instalowanie dodatkowych dostawców programu SMS** aby zapewnić nadmiarowość punktów kontaktu w celu administrowania lokacji i hierarchii. Aby uzyskać więcej informacji, zobacz [zarządzania dostawcą programu SMS](../../../../core/servers/manage/modify-your-infrastructure.md#BKMK_ManageSMSprovider) w [zmodyfikować infrastruktury programu System Center Configuration Manager](../../../../core/servers/manage/modify-your-infrastructure.md).<br /><br /> **Instalowanie dodatkowych konsol programu Configuration Manager** umożliwia dostęp do dodatkowych użytkowników administracyjnych. Aby uzyskać więcej informacji, zobacz [konsole Instalowanie programu Configuration Manager](../../../../core/servers/deploy/install/install-consoles.md).|  
|Konfigurowanie składników lokacji|Konfigurowanie składników lokacji w każdej lokacji, aby zmodyfikować zachowanie ról systemu lokacji oraz raportowania stanu lokacji. Aby uzyskać więcej informacji, zobacz [Składniki lokacji dla programu System Center Configuration Manager](../../../../core/servers/deploy/configure/site-components.md).|  
|Tworzenie kolekcji niestandardowych|Korzystając z informacji został wykryty dotyczące urządzeń i użytkowników, tworzenie kolekcji niestandardowych obiektów, aby uprościć zadania zarządzania przyszłych. Aby uzyskać więcej informacji, zobacz [tworzenie kolekcji w programie System Center Configuration Manager](../../../../core/clients/manage/collections/create-collections.md).|  
|Konfigurowanie ustawień w celu zarządzania wdrożeniami o wysokim ryzyku|Skonfiguruj ustawienia w lokacji, która ostrzega użytkowników administracyjnych, podczas tworzenia wdrożenia sekwencji zadań o wysokim ryzyku.  Aby uzyskać więcej informacji, zobacz [ustawienia do zarządzania wdrożeniami o wysokim ryzyku dla programu System Center Configuration Manager](../../../../protect/understand/settings-to-manage-high-risk-deployments.md).|  
|Konfigurowanie replik bazy danych dla punktów zarządzania|Konfigurowanie repliki bazy danych, aby zmniejszyć obciążenie Procesora, która jest umieszczona na serwerze bazy danych lokacji przez punkty zarządzania, zgodnie z ich żądania od klientów usługi. Aby uzyskać więcej informacji, zobacz [Repliki bazy danych dla punktów zarządzania programu System Center Configuration Manager](../../../../core/servers/deploy/configure/database-replicas-for-management-points.md).|  
|Skonfiguruj grupę dostępności AlwaysOn programu SQL Server do obsługi bazy danych lokacji|Począwszy od wersji 1602, konfigurowanie grup dostępności jako rozwiązań wysokiej dostępności i odzyskiwania po awarii do obsługi bazy danych lokacji w lokacji głównej i centralnej lokacji administracyjnej. Aby uzyskać więcej informacji, zobacz [AlwaysOn programu SQL Server dla bazy danych lokacji wysokiej dostępności dla programu System Center Configuration Manager](../../../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md).|  
|Modyfikowanie replikacji między lokacjami|Zobacz [Transfer danych między lokacjami w programie System Center Configuration Manager](../../../../core/servers/manage/data-transfers-between-sites.md), aby uzyskać informacje o następujących tematach:<br /><br /> Skonfiguruj [replikacji](../../../../core/servers/manage/data-transfers-between-sites.md#bkmk_fileroute) między lokacjami dodatkowymi<br /><br /> Skonfiguruj [bazy danych łącza replikacji](../../../../core/servers/manage/data-transfers-between-sites.md#bkmk_Dblinks)<br /><br /> Skonfiguruj [widoki rozproszone](../../../../core/servers/manage/data-transfers-between-sites.md#bkmk_distviews)|  

