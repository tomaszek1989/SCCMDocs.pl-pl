---
title: Listy kontrolne migracji | Dokumentacja firmy Microsoft
description: "Użyj listy kontrolne administratora ułatwiają Planowanie strategii migracji programu System Center Configuration Manager."
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 295fdf07-93cc-490c-acdd-ce3ee88cb36f
caps.latest.revision: 7
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5e6e8a18a8fc705c993177b3c5b4113a351a45a4
ms.openlocfilehash: 36f7c37e4da3f2bce64a25d266dae57d9fe98c36
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="administrator-checklists-for-migration-planning-in-system-center-configuration-manager"></a>Listy kontrolne administratora dotyczące planowania migracji w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Użyj poniższej listy kontrolne administratora ułatwiają Planowanie strategii migracji programu System Center Configuration Manager.

##  <a name="Checklist_Migraiton_Planning"></a>Lista kontrolna administratora dotycząca planowania migracji  
 Należy użyć poniższej listy kontrolnej przed migracją planowania.  

-   **Oceń bieżące środowisko:**  

     Zidentyfikuj istniejące wymogi biznesowe spełnione przez hierarchię źródłową i opracuj plany utrzymania zgodności z tymi wymogami w hierarchii docelowej.  

-   **Przejrzyj funkcje i zmiany, które są dostępne w wersji Menedżera konfiguracji, którego używasz i użyć tych informacji, aby ułatwić projektowanie hierarchii docelowej:**  

    Aby uzyskać więcej informacji, zobacz [Podstawowe informacje dotyczące programu System Center Configuration Manager](../../core/understand/fundamentals.md) i [Co nowego w programie System Center Configuration Manager](../../core/plan-design/changes/what-has-changed-from-configuration-manager-2012.md).  


-   **Określ model zabezpieczeń administracyjnych używany dla administracji opartej na rolach:**  

    Aby uzyskać więcej informacji, zobacz [podstawy administracji opartej na rolach dla programu System Center Configuration Manager](../../core/understand/fundamentals-of-role-based-administration.md).  

-   **Oceń sieć i topologię usługi Active Directory:** Przejrzyj istniejącą strukturę domeny i topologię sieci oraz uwzględnij ich wpływ na projekt hierarchii oraz zadania migracji.  

-   **Dokończ Projektowanie hierarchii docelowej:**  

    Podejmij decyzje dotyczące rozmieszczenia centralnej lokacji administracyjnej, lokacji głównych, lokacji dodatkowych oraz opcji dystrybucji zawartości.  

-   **Zmapuj hierarchię na komputery, które będą używane dla lokacji i serwerów lokacji w hierarchii docelowej:**  

    Zidentyfikuj komputery, które lokacji i serwerów systemu lokacji będzie używać w hierarchii docelowej, a następnie upewnij się, że mają wystarczającą pojemność do zgodne z istniejącymi i przyszłymi wymogami roboczymi.  

-   **Zaplanuj strategię migracji obiektów:**  

    Zaplanuj użycie dostępnych zadań migracji do przeprowadzenia migracji różnych obiektów, w tym granic lokacji, kolekcji, anonsów i wdrożeń. Aby uzyskać więcej informacji, zobacz [rodzaje zadań migracji](../../core/migration/planning-a-migration-job-strategy.md#Types_of_Migration) w [Planowanie strategii zadania migracji w programie System Center Configuration Manager](../../core/migration/planning-a-migration-job-strategy.md)  

    Menedżer konfiguracji migruje tylko zaznaczone obiekty. Wszystkie obiekty, które nie są migrowane, ale są wymagane w hierarchii docelowej należy ponownie utworzyć w hierarchii docelowej.  

    Obiekty możliwe do zmigrowania są wyświetlane podczas konfigurowania zadań migracji.  

-   **Planowanie strategii migracji klienta:**  

    Zaplanuj migrację klientów do hierarchii docelowej w kontrolowany sposób, który wymaga małej przepustowości sieci i wydajności serwera. Aby uzyskać więcej informacji o planowaniu strategii migracji klienta, zobacz [Planowanie strategii migracji klienta w programie System Center Configuration Manager](../../core/migration/planning-a-client-migration-strategy.md).  

-   **Zaplanuj migrację danych spisu i zgodności:**  

    Menedżer konfiguracji nie obsługuje migracji spisu sprzętu, spisu oprogramowania ani danych zgodności zarządzania wymaganą konfiguracją dotyczących aktualizacji oprogramowania i klientów.  

    Zamiast tego, po zmigrowaniu do nowej lokacji w hierarchii docelowej i odebraniu zasady dla tych konfiguracji klient przesyła te informacje do swojej przypisanej lokacji. Ta akcja powoduje wypełnienie bazy danych lokacji docelowej bieżącym spisem i bieżącymi danymi zgodności.  

-   **Zaplanuj dokończenie migracji z hierarchii źródłowej:**  

    Zdecyduj, kiedy mają być migrowane obiekty i klienci. Po zakończeniu migracji zaplanuj likwidację serwerów lokacji w hierarchii źródłowej.  

##  <a name="Checklist_Hierarchy_for_migration"></a>Lista kontrolna administratora dotycząca migracji hierarchii  
Poniższa lista kontrolna ułatwia planowanie hierarchii docelowej przed rozpoczęciem migracji.  

-   **Zidentyfikuj komputery do użycia w hierarchii docelowej:**  

    Menedżer konfiguracji nie obsługuje uaktualnienie w miejscu infrastruktury programu Configuration Manager 2007. Zamiast tego użyj migracji do przenoszenia danych z programu Configuration Manager 2007 z programem System Center Configuration Manager. Należy użyć do wdrożenia side-by-side i zainstalować System Center Configuration Manager na nowe komputery.  

    Podobnie w przypadku migracji z innej hierarchii programu System Center Configuration Manager, należy zainstalować nową hierarchię docelową, która jest wdrożeniem side-by-side do hierarchii źródłowej.  

-   **Utwórz hierarchię docelową:**  

    Aby przygotować się do migracji, należy zainstalować i skonfigurować hierarchii docelowej programu System Center Configuration Manager, która obejmuje lokacji głównej. Na przykład:  

    -   Zainstaluj centralną lokację administracyjną, a następnie zainstaluj co najmniej jedną lokację podrzędną.  

    -   Zainstaluj autonomiczną lokację główną, jeśli nie zamierzasz korzystać z witryny administracji centralnej.  

-   **Jeśli chcesz zmigrować informacje dotyczące aktualizacji oprogramowania, skonfigurować punkt aktualizacji oprogramowania w hierarchii docelowej i synchronizować aktualizacje oprogramowania:**  

    Przed migracją informacji o aktualizacji oprogramowania z hierarchii źródłowej musisz skonfigurować i zsynchronizować aktualizacje oprogramowania w hierarchii docelowej.  


-   **Zainstaluj i skonfiguruj dodatkowe role systemu lokacji w hierarchii docelowej:**  

    Skonfiguruj dodatkowe role systemu lokacji i systemami lokacji, które są potrzebne.  

-   **Sprawdź funkcje operacyjne w hierarchii docelowej:**  

    Sprawdź następujące kwestie:  

    -   Jeśli hierarchia docelowa zawiera wiele lokacji, sprawdź, czy między lokacjami działa replikacja bazy danych. Replikacja bazy danych nie ma zastosowania do autonomicznych lokacji głównych.  

    -   Sprawdź, czy działają wszystkie zainstalowane role systemów lokacji.  

    -   Sprawdź, czy klienci programu Configuration Manager, który instalujesz do hierarchii docelowej mogą się komunikować z przypisanymi do nich lokacjami.  


##  <a name="Checklisit_Migration"></a>Lista kontrolna administratora dotycząca migracji  
Poniższa lista kontrolna umożliwia migrację danych z hierarchii źródłowej do hierarchii docelowej.  

-   **Włącz migrację w hierarchii docelowej:**  

    Skonfiguruj hierarchię źródłową, określając lokację najwyższego poziomu hierarchii źródłowej. Aby uzyskać więcej informacji o określaniu lokacji źródłowej, zobacz [Planowanie strategii hierarchii źródłowej w programie System Center Configuration Manager](../../core/migration/planning-a-source-hierarchy-strategy.md).  

-   **Po uruchomieniu programu Configuration Manager 2007 z dodatkiem SP2 do hierarchii źródłowej wybierz i skonfiguruj dodatkowe Lokacje w hierarchii źródłowej:**  

    Dla każdej dodatkowej lokacji w hierarchii źródłowej programu Configuration Manager 2007 z dodatkiem SP2, które chcesz zbierać dane należy skonfigurować poświadczenia zbierania danych. Po skonfigurowaniu każdej lokacji źródłowej, proces zbierania danych rozpocznie się natychmiast i jest kontynuowany przez cały czas migracji, aż do zatrzymania zbierania danych dla tej lokacji. Zbieranie danych zapewnia, że można migrować obiektów z hierarchii źródłowej, które są zaktualizowane lub dodane po utworzeniu poprzedniego procesu zbierania danych.

    > [!NOTE]  
    >  Gdy hierarchii źródłowej jest uruchomiony System Center 2012 Configuration Manager lub nowszego, nie musisz skonfigurować dodatkowe Lokacje źródłowe.  

-   **Skonfiguruj współużytkowanie punktów dystrybucji:**  

    Punkty dystrybucji można współużytkować między dwoma hierarchiami, aby zawartość migrowanych obiektów była dostępna dla klientów w hierarchii docelowej. Dzięki temu ta sama zawartość będzie dostępna dla klientów w obu hierarchiach i będzie można utrzymać tę zawartość dopiero po zatrzymaniu zbierania danych i zakończyć migrację.  

    Aby uzyskać informacje dotyczące współużytkowanych punktów dystrybucji, zobacz [udostępniać punktów dystrybucji między hierarchiami źródłową i docelową](../../core/migration/planning-a-content-deployment-migration-strategy.md#About_Shared_DPs_in_Migration) w [Planowanie strategii migracji wdrożenia zawartości w programie System Center Configuration Manager](../../core/migration/planning-a-content-deployment-migration-strategy.md).  

-   **Tworzenie i uruchamianie zadania migracji obiektów skojarzonych z klientami w hierarchii źródłowej:**  

    Utwórz zadania migracji, aby zmigrować obiekty między hierarchiami. Konfiguracja wymagana w przypadku poszczególnych zadań migracji zależy od typu migrowanych danych.  

    Jeśli na przykład migrujesz zawartość, niezależnie od używanego zadania migracji musisz przypisać lokację w hierarchii docelowej, która będzie zarządzać tą zawartością. Przypisana lokacja będzie mieć dostęp do lokalizacji oryginalnych plików źródłowych zawartości oraz będzie odpowiedzialna za dystrybucję tej zawartości do punktów dystrybucji w hierarchii docelowej.  

    Aby uzyskać więcej informacji, zobacz [tworzenie i edytowanie zadań migracji dla programu system center configuration manager](../../core/migration/operations-for-migration.md#Create_Edit_migration_Jobs) w [operacje migracji programu System Center Configuration Manager](../../core/migration/operations-for-migration.md).  

-   **Migrację klientów do hierarchii docelowej:**  

    Przebieg migracji klientów zależy od scenariusza migracji:  

    -   W przypadku migracji klientów, których wersja klienta, który nie jest taka sama jak w hierarchii docelowej, należy uaktualnić oprogramowanie klienckie. Uaktualnienie wymaga usunięcia bieżącego klienta programu Configuration Manager, a następnie zainstalowania nowej wersji klienta zgodnej z lokacją docelową.  

    -   Gdy migrujesz klientów, których wersja jest taka sama jak wersja w hierarchii docelowej, uaktualnienie ani ponowna instalacja klienta nie są konieczne. Klient przypisuje się wtedy ponownie do lokacji głównej w hierarchii docelowej.  

    Gdy migrujesz klienta do hierarchii docelowej, jest on kojarzony ze swoimi danymi, które zostały uprzednio zmigrowane do tej hierarchii docelowej.  

    Aby uzyskać więcej informacji, zobacz [Planowanie strategii migracji klientów w programie System Center Configuration Manager](../../core/migration/planning-a-client-migration-strategy.md).  

-   **Uaktualnić lub ponownie przypisać współużytkowane punkty dystrybucji:**  

    Jeśli masz już nie obsługuje klientów w hierarchii źródłowej, możesz uaktualnić współużytkowane punkty dystrybucji z lokacji źródłowej programu Configuration Manager 2007 lub ponownie przypisać współużytkowane punkty dystrybucji z lokacji źródłowej programu System Center 2012 Configuration Manager lub System Center Configuration Manager. Po uaktualnieniu lub ponownym przypisaniu punktu dystrybucji rola systemu lokacji zostanie przeniesiona do lokacji głównej w hierarchii docelowej, a punkt dystrybucji zostanie usunięty z lokacji źródłowej w hierarchii źródłowej. Po uaktualnieniu lub ponownym przypisaniu współużytkowanego punktu dystrybucji zawartość pozostaje na komputerze punktu dystrybucji i nie jest konieczne ponowne jej wdrożenie do nowych punktów dystrybucji w hierarchii docelowej.  

    Możesz również uaktualnić punkt dystrybucji, który znajduje się na serwerze lokacji dodatkowej programu Configuration Manager 2007. Spowoduje to usunięcie lokacji dodatkowej i pozostawienie w hierarchii docelowej wyłącznie punktu dystrybucji.  

    Aby uzyskać informacje dotyczące współużytkowanych punktów dystrybucji, zobacz [udostępniać punktów dystrybucji między hierarchiami źródłową i docelową](../../core/migration/planning-a-content-deployment-migration-strategy.md#About_Shared_DPs_in_Migration) w [Planowanie strategii migracji wdrożenia zawartości w programie System Center Configuration Manager](../../core/migration/planning-a-content-deployment-migration-strategy.md).  

-   **Zakończenie migracji:**  

    Po po migracji danych i klientów ze wszystkich lokacji w hierarchii źródłowej oraz uaktualnieniu odpowiednich punktów dystrybucji, można zakończyć migrację. Aby ukończyć migrację zatrzymaniu zbierania danych dla każdej lokacji źródłowej w hierarchii źródłowej. Następnie możesz usunąć niepotrzebne informacje o migracji i zlikwidować infrastrukturę hierarchii źródłowej. Aby uzyskać więcej informacji, zobacz [Planowanie kończenia migracji w programie System Center Configuration Manager](../../core/migration/planning-to-complete-migration.md).  

