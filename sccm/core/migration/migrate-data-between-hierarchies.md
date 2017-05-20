---
title: Migrowanie danych | Dokumentacja firmy Microsoft
description: "Dowiedz się, jak na przesyłanie danych z hierarchii źródłowej do hierarchii docelowej programu System Center Configuration Manager."
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cf014eb0-f8c2-4d37-b8d7-368d63a10b89
caps.latest.revision: 11
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: a8959c72608a1531fb323176c33a848a4a669b1c
ms.openlocfilehash: dface33392c2a2a662522656eabf0936b52b28fc
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="migrate-data-between-hierarchies-in-system-center-configuration-manager"></a>Migrowanie danych między hierarchiami w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Migracja umożliwia transfer danych z obsługiwanej hierarchii źródłowej do hierarchii docelowej programu System Center Configuration Manager.  Podczas migracji danych z hierarchii źródłowej:  

-   Dostęp do danych w bazie danych lokacji identyfikować infrastrukturę źródłową, a następnie dane te są przesyłane do bieżącego środowiska.  

-   Migracja nie powoduje zmiany danych w hierarchii źródłowej, lecz wykrycie danych i zachowanie ich kopii w bazie danych hierarchii docelowej.  

Planując strategię migracji, warto rozważyć następujące kwestie:  

-   Można migrować istniejącej infrastruktury programu Configuration Manager 2007 z dodatkiem SP2 programu System Center Configuration Manager.  

-   Można poddać migracji niektóre lub wszystkie obsługiwane dane z lokacji źródłowej.  

-   Można poddać migracji dane z pojedynczej lokacji źródłowej do wielu różnych lokacji w hierarchii docelowej.  

-   Można przenieść dane z wielu lokacji źródłowych do pojedynczej lokacji w hierarchii docelowej.  

##  <a name="BKMK_MigrationConcepts"></a> Pojęcia dotyczące migracji  
 Mogą wystąpić następujące pojęcia i warunki zastosowania migracji.  

|Koncepcja lub termin|Więcej informacji|  
|---------------------|----------------------|  
|Hierarchia źródłowa|Hierarchia działa obsługiwana wersja programu Configuration Manager, który zawiera dane, które chcesz migrować. Podczas konfigurowania migracji można zidentyfikować hierarchii źródłowej podczas wskazywania lokacji najwyższego poziomu hierarchii źródłowej. Po określeniu hierarchii źródłowej lokacja najwyższego poziomu hierarchii docelowej zbiera dane z bazy danych wskazanej lokacji źródłowej w celu zidentyfikowania danych dostępnych do migracji.<br /><br /> Aby uzyskać więcej informacji, zobacz [hierarchii źródłowych](../../core/migration/planning-a-source-hierarchy-strategy.md#BKMK_Source_Hierarchies) w [Planowanie strategii hierarchii źródłowej w programie System Center Configuration Manager](../../core/migration/planning-a-source-hierarchy-strategy.md).|  
|Lokacje źródłowe|Lokacje w hierarchii źródłowej, które zawierają dane dostępne do migracji do hierarchii docelowej.<br /><br /> Aby uzyskać więcej informacji, zobacz [lokacji źródłowych](../../core/migration/planning-a-source-hierarchy-strategy.md#BKMK_Source_Sites) w [Planowanie strategii hierarchii źródłowej w programie System Center Configuration Manager](../../core/migration/planning-a-source-hierarchy-strategy.md).|  
|Hierarchia docelowa|Hierarchia programu System Center Configuration Manager, gdzie jest uruchamiany proces migracji do importowania danych z hierarchii źródłowej.|  
|Gromadzenie danych|Ciągły proces identyfikowania informacji zawartych w hierarchii źródłowej, które można poddać migracji do hierarchii docelowej. Program Configuration Manager sprawdza hierarchii źródłowej zgodnie z harmonogramem, aby zidentyfikować wszelkie zmiany w hierarchii źródłowej, które były wcześniej migrowane i które mogą zostać zaktualizowane w hierarchii docelowej.<br /><br /> Aby uzyskać więcej informacji, zobacz [zbierania danych](../../core/migration/planning-a-source-hierarchy-strategy.md#BKMK_Data_Gathering) w [Planowanie strategii hierarchii źródłowej w programie System Center Configuration Manager](../../core/migration/planning-a-source-hierarchy-strategy.md).|  
|Zadania migracji|Proces konfigurowania konkretnych obiektów przeznaczonych do migracji, a następnie zarządzania migracją tych obiektów do hierarchii docelowej.<br /><br /> Aby uzyskać więcej informacji, zobacz [Planowanie strategii zadania migracji w programie System Center Configuration Manager](../../core/migration/planning-a-migration-job-strategy.md)|  
|Migracja klienta|Proces transferu informacji używanych przez klientów z bazy danych lokacji źródłowej do bazy danych hierarchii docelowej. Po tej migracji danych następuje uaktualnienie oprogramowania klienta na urządzeniach do wersji oprogramowania z hierarchii docelowej.<br /><br /> Aby uzyskać więcej informacji, zobacz [Planowanie strategii migracji klientów w programie System Center Configuration Manager](../../core/migration/planning-a-client-migration-strategy.md).|  
|Współużytkowane punkty dystrybucji|Punkty dystrybucji z hierarchii źródłowej, które są współużytkowane z hierarchią docelową podczas migracji.<br /><br /> W czasie migracji klienci przypisani do lokacji w hierarchii docelowej można pobrać zawartość ze współużytkowanych punktów dystrybucji.<br /><br /> Aby uzyskać więcej informacji, zobacz [udostępniać punktów dystrybucji między hierarchiami źródłową i docelową](../../core/migration/planning-a-content-deployment-migration-strategy.md#About_Shared_DPs_in_Migration) w [Planowanie strategii migracji wdrożenia zawartości w programie System Center Configuration Manager](../../core/migration/planning-a-content-deployment-migration-strategy.md).|  
|Monitorowanie migracji|Proces monitorowania działań migracji. Można monitorować postęp i Powodzenie z migracji **migracji** w węźle **administracji** obszaru roboczego.<br /><br /> Aby uzyskać więcej informacji, zobacz [planowanie monitorowania działania migracji w programie System Center Configuration Manager](../../core/migration/planning-to-monitor-migration-activity.md).|  
|Zatrzymaj zbieranie danych|Proces zatrzymywania zbierania danych z lokacji źródłowych. Gdy nie chcesz juz migrować danych z hierarchii źródłowej lub chcesz wstrzymać działania związane z migracją, możesz skonfigurować hierarchię docelową do zatrzymania zbierania danych z hierarchii źródłowej.<br /><br /> Aby uzyskać więcej informacji, zobacz [zbierania danych](../../core/migration/planning-a-source-hierarchy-strategy.md#BKMK_Data_Gathering) w [Planowanie strategii hierarchii źródłowej w programie System Center Configuration Manager](../../core/migration/planning-a-source-hierarchy-strategy.md).|  
|Wyczyść dane migracji|Proces kończenia migracji z hierarchii źródłowej polegający na usunięciu informacji o migracji z baz danych hierarchii docelowych.<br /><br /> Aby uzyskać więcej informacji, zobacz [Planowanie kończenia migracji w programie System Center Configuration Manager](../../core/migration/planning-to-complete-migration.md).|  

## <a name="typical-workflow-for-migration"></a>Typowy przepływ pracy dla migracji  
Aby skonfigurować przepływ pracy dla migracji:

1.  Określ obsługiwaną hierarchię źródłową.  

2.  Konfigurowanie zbierania danych. Gromadzenie danych pozwala programu Configuration Manager do zbierania informacji o danych, które można migrować z hierarchii źródłowej.  

     Menedżer konfiguracji automatycznie powtarza proces zbierania danych na podstawie prostego harmonogramu, aż do zatrzymania procesu zbierania danych. Domyślnie proces zbierania danych powtarzany co cztery godziny, tak że program Configuration Manager może zidentyfikować zmiany danych w hierarchii źródłowej, które możesz chcieć zmigrować. Gromadzenie danych jest także niezbędne do współużytkowania punktów dystrybucji z hierarchii źródłowej do hierarchii docelowej.  

3.  Utwórz zadania migracji, aby zmigrować dane między hierarchią źródłową i docelową.  

4.  Proces zbierania danych można zatrzymać w dowolnej chwili za pomocą polecenia **Zatrzymaj zbieranie danych** . Po zatrzymaniu zbierania danych programu Configuration Manager nie jest już identyfikować zmiany danych w hierarchii źródłowej i nie może dłużej współużytkować punktów dystrybucji między hierarchiami źródłową i docelową. Zwykle z tej akcji należy korzystać, gdy nie planujesz już migracji danych ani współużytkowania punktów dystrybucji z hierarchii źródłowej.  

5.  Opcjonalnie, po zatrzymaniu zbierania danych we wszystkich lokacjach w hierarchii źródłowej, możesz wyczyścić dane migracji za pomocą polecenia **Wyczyść dane migracji** . To polecenie powoduje usunięcie z bazy danych hierarchii docelowej danych historycznych dotyczących migracji z hierarchii źródłowej.  

Po dokonaniu migracji danych z hierarchii źródłowej programu Configuration Manager, które nie są używane do zarządzania środowiskiem, można zlikwidować tej hierarchii źródłowej i infrastruktury.  

##  <a name="BKMK_MigrationScenarios"></a> Scenariusze migracji  
 Program Configuration Manager obsługuje następujące scenariusze migracji.  

> [!NOTE]  
>  Rozszerzenie hierarchii zawierającej autonomiczną lokacją w hierarchii zawierającej centralną lokację administracyjną nie jest traktowane jako migracja. Więcej informacji o rozszerzaniu hierarchii, zobacz [rozszerzyć autonomiczną lokację główną](../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md#bkmk_expand) w [Kreator instalacji umożliwia zainstalowanie lokacji](../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md).  

### <a name="migration-from-configuration-manager-2007-hierarchies"></a>Migracja z hierarchii programu Configuration Manager 2007  
 W przypadku migracji można użyć do migracji danych z programu Configuration Manager 2007, można ochronić inwestycję w istniejącą infrastrukturę lokacji i zyskać następujące korzyści:  

|Korzyść|Więcej informacji|  
|-------------|----------------------|  
|Ulepszenia bazy danych lokacji|Bazy danych programu System Center Configuration Manager zapewnia pełną obsługę standardu Unicode.|  
|Replikacja bazy danych między lokacjami|Replikacji w programie System Center Configuration Manager jest oparta na programie Microsoft SQL Server. Poprawia do wydajność transferu danych między lokacjami.|  
|Zarządzanie skoncentrowane na użytkowniku|Koncentrują się na użytkownikach zadań zarządzania w programie System Center Configuration Manager. Można na przykład dystrybuować oprogramowanie do użytkownika, nawet jeśli nie jest znana nazwa urządzenia tego użytkownika. Ponadto System Center Configuration Manager pozwala użytkownikom większą kontrolę nad tym, jakie oprogramowanie jest instalowane na ich urządzeniach i podczas instalacji tego oprogramowania.|  
|Uproszczenie hierarchii|W System Center Configuration Manager typ centralnej lokacji administracyjnej oraz zmiany zachowania lokacji głównej i dodatkowej pozwalają tworzyć prostsze hierarchie lokacji wykorzystujące mniej przepustowości sieci oraz wymagające mniejszej liczby serwerów.|  
|Administracja oparta na rolach|Ten centralny model zabezpieczeń w programie System Center Configuration Manager oferuje bezpieczeństwo w całej hierarchii oraz zarządzania, który odpowiada wymogami firmowymi i administracyjnymi.|  

> [!NOTE]  
>  Z powodu zmian projektowych, które zostały najpierw wprowadzone w programie System Center 2012 Configuration Manager nie może uaktualnić programu Configuration Manager 2007 infrastruktury programu System Center Configuration Manager. Uaktualnienie w miejscu jest obsługiwane z programu System Center 2012 Configuration Manager programu System Center Configuration Manager.  

### <a name="migration-from-configuration-manager-2012-or-another-system-center-configuration-manager-hierarchy"></a>Migracja z programu Configuration Manager 2012 lub innej hierarchii programu System Center Configuration Manager  
 Proces migracji danych z hierarchii programu System Center 2012 Configuration Manager lub System Center Configuration Manager jest taka sama. Obejmuje to migrację danych z wielu hierarchii źródłowych do jednej hierarchii docelowej, takich jak dyski po firmie pobiera dodatkowe zasoby, które są już zarządzane przez program Configuration Manager. Można również migrować dane ze środowiska testowego do środowiska produkcyjnego programu Configuration Manager. Pozwala to chronić inwestycję w środowisko testowe programu Configuration Manager.  

## <a name="additional-topics-for-migration"></a>Dodatkowe tematy dotyczące migracji:  

-   [Planowanie migracji programu System Center Configuration Manager](../../core/migration/planning-for-migration.md)  

-   [Konfigurowanie hierarchii źródłowych i lokacji źródłowych na potrzeby migracji programu System Center Configuration Manager](../../core/migration/configuring-source-hierarchies-and-source-sites-for-migration.md)  

-   [Operacje migracji programu System Center Configuration Manager](../../core/migration/operations-for-migration.md)  

-   [Bezpieczeństwo i ochrona prywatności podczas migracji programu System Center Configuration Manager](../../core/migration/security-and-privacy-for-migration.md)  

## <a name="see-also"></a>Zobacz też  
 [Rozpocząć korzystanie z programu System Center Configuration Manager](../../core/servers/deploy/start-using.md)

