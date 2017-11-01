---
title: "Lista kontrolna dotycząca 1606"
titleSuffix: Configuration Manager
description: "Więcej informacji na temat działania należy podjąć przed zaktualizowaniem programu System Center Configuration Manager w wersji 1511 lub 1602 do wersji 1606."
ms.custom: na
ms.date: 6/6/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 75652cd2-a95a-46c5-91c1-6d43fc8e787e
caps.latest.revision: "7"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 1f3bb243c6c40a1c949b3c75aa4f8727f5ed42bd
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="checklist-for-installing-update-1606-for-system-center-configuration-manager"></a>Lista kontrolna dotycząca instalowania aktualizacji 1606 programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Wersja 1606 dla bieżącej gałęzi programu System Center Configuration Manager jest dostępna aktualizacja, służącego do aktualizacji z wersji 1511 lub 1602.

Przed zainstalowaniem wersji 1606 jako aktualizację, przejrzyj następujące informacje i listy kontrolnej czynności należy wykonać przed rozpoczęciem aktualizacji.

Aby uzyskać informacje o wersji linii bazowej, zobacz [wersje linii bazowej i aktualizacji](../../../core/servers/manage/updates.md#bkmk_Baselines) w [aktualizacji dla programu System Center Configuration Manager](../../../core/servers/manage/updates.md).

 ## <a name="about-installing-update-1606"></a>Informacje dotyczące instalowania aktualizacji 1606

Jako *aktualizacji*, 1606 można zainstalować tylko w lokacji najwyższego poziomu w hierarchii. Oznacza to, należy zainicjować instalację, z witryny Administracja centralna, jeśli masz lub autonomicznej lokacji głównej.  

-   Podrzędne Lokacje główne instalują aktualizację automatycznie po zakończeniu centralnej lokacji administracyjnej, instalowania aktualizacji. Można użyć usługi windows do formantu, gdy lokacja instaluje aktualizacje. Przed wersją 1606 usługi systemu windows były nazywane okna obsługi. Aby uzyskać więcej informacji, zobacz [usługi systemu windows dla serwerów lokacji](/sccm/core/servers/manage/service-windows).  

-   Należy ręcznie zaktualizować Lokacje dodatkowe przy użyciu konsoli programu Configuration Manager po zakończeniu nadrzędną lokację główną, instalowania aktualizacji. Automatyczna aktualizacja serwerów lokacji dodatkowych nie jest obsługiwana.  

Podczas instalowania aktualizacji serwera lokacji role systemu lokacji, które są zainstalowane na serwerze lokacji oraz te, które są zainstalowane na komputerach zdalnych aktualizowany automatycznie. W związku z tym przed zainstalowaniem aktualizacji, upewnij się, że każdy serwer systemu lokacji spełnia ewentualne nowe wymagania wstępne dla operacji przy użyciu nowej wersji aktualizacji.  

Użycie konsoli programu Configuration Manager po zainstalowaniu aktualizacji po raz pierwszy pojawi się monit zaktualizowanie tej konsoli.  Aby to zrobić, należy uruchomić Instalatora programu Configuration Manager na komputerze, który jest hostem konsoli i następnie wybierz opcję, aby zaktualizować konsolę. Zalecamy natychmiastowe instalowanie aktualizacji konsoli.

 **Znane problemy dotyczące tej aktualizacji**   
  Wyświetl stan instalacji pakietu aktualizacji obowiązują następujące problemy:
  - Podczas aktualizacji z wersji 1602 do 1606 kroku **ładunek pakietu aktualizacji wyodrębniania** ma stan **nie rozpoczęto**, nawet jeśli został pobrany.
  - Podczas aktualizacji z wersji 1511 do 1606, niektóre kroki będzie wyświetlany stan **Ukończono** , ale nie będą wyświetlane wartości **czas ostatniej aktualizacji**.


## <a name="checklist"></a>Lista kontrolna  

 **Upewnij się, że we wszystkich lokacjach uruchomiona obsługiwana wersja programu System Center Configuration Manager:**  Przed rozpoczęciem instalacji aktualizacji 1606 każdy serwer lokacji w hierarchii muszą korzystać z tej samej wersji programu System Center Configuration Manager: danej wersji 1511 lub 1602.

 **Przegląd zainstalowanych wersji Microsoft.NET na serwerach systemu lokacji:** Podczas instalowania aktualizacji 1606 lokacji programu Configuration Manager automatycznie instaluje .NET Framework 4.5.2 na każdym komputerze hostującym jedną z następujących ról systemu lokacji (Jeśli nie zainstalowano jeszcze .NET Framework 4.5 lub nowszej):  

-   Punkt proxy rejestracji  

-   Punkt rejestracji  

-   Punkt zarządzania  

-   Punkt połączenia usługi  

Ta instalacja można umieścić serwer systemu lokacji do na ponowne uruchomienie do czasu stanu i raport błędów w przeglądarce stanu składników programu Configuration Manager. Ponadto mogą losowo występować usterki aplikacji .NET na serwerze do momentu ponownego uruchomienia serwera.  

 Aby uzyskać więcej informacji, zobacz [lokacji i wymagania wstępne systemu lokacji](../../../core/plan-design/configs/site-and-site-system-prerequisites.md).  

 **Sprawdź stan lokacji i hierarchii, a następnie sprawdź, czy nie występują żadne nierozwiązane problemy:** Przed uaktualnieniem lokacji należy rozwiązać wszystkie problemy z działaniem serwera lokacji, serwera bazy danych lokacji i ról systemu lokacji, które są zainstalowane na komputerach zdalnych. Problemy z działaniem mogą spowodować niepowodzenie aktualizacji lokacji.

 Aby uzyskać więcej informacji, zobacz [Korzystanie z alertów i systemu stanu w programie System Center Configuration Manager](../../../core/servers/manage/use-alerts-and-the-status-system.md).  

 **Przejrzyj replikację plików i danych między lokacjami:**  Upewnij się, że plik i replikacji bazy danych między lokacjami jest operacyjne i bieżący. Opóźnień lub zaległości może uniemożliwić smooth aktualizacji powiodło się.    

W przypadku replikacji bazy danych można skorzystać z Analizatora linków replikacji ułatwiającego rozwiązywanie problemów przed rozpoczęciem aktualizacji. Aby uzyskać więcej informacji, zobacz [o analizator łącza replikacji](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_RLA) w temacie [Monitorowanie infrastruktury hierarchii i replikacji w programie System Center Configuration Manager](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md).  

 **Zainstaluj wszystkie odpowiednie aktualizacje krytyczne dla systemów operacyjnych na komputerach hostujących lokację, serwer bazy danych lokacji i role zdalnego systemu lokacji:** Przed zainstalowaniem aktualizacji programu Configuration Manager, należy zainstalować wszystkie aktualizacje krytyczne dla odpowiednich systemów lokacji. Instalowana aktualizacja może wymagać ponownego uruchomienia odpowiednich komputerów przed rozpoczęciem uaktualniania.  

 **Wyłącz repliki bazy danych dla punktów zarządzania w lokacjach głównych:** Menedżer konfiguracji nie może pomyślnie zaktualizować lokacji głównej, z repliki bazy danych dla punktów zarządzania włączone. Wyłącz replikację bazy danych, przed zainstalowaniem aktualizacji programu Configuration Manager.  

Aby uzyskać więcej informacji, zobacz [replik bazy danych dla punktów zarządzania programu System Center Configuration Manager](../../../core/servers/deploy/configure/database-replicas-for-management-points.md).  

 **Ustaw ręcznego przełączania trybu failover grupy dostępności AlwaysOn programu SQL Server:**  
 Przed zainstalowaniem aktualizacji, na przykład wersji 1606, upewnij się, że grupy dostępności jest ustawiona na ręcznego przełączania trybu failover. Po zaktualizowaniu lokacji można przywrócić trybu failover automatycznego. Aby uzyskać więcej informacji, zobacz [AlwaysOn programu SQL Server dla bazy danych lokacji](../../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md).

 **Skonfiguruj ponownie punkty aktualizacji oprogramowania, które używają usługi równoważenia obciążenia sieciowego:** Menedżer konfiguracji nie może zaktualizować lokacji korzystającej z klastra równoważenia obciążenia sieciowego (NLB), punkty aktualizacji oprogramowania.  

Korzystając z klastrami równoważenia obciążenia Sieciowego dla punktów aktualizacji oprogramowania, należy usunąć klaster równoważenia obciążenia Sieciowego za pomocą programu Windows PowerShell.    

 Aby uzyskać więcej informacji, zobacz [Planowanie aktualizacji oprogramowania w programie System Center Configuration Manager](../../../sum/plan-design/plan-for-software-updates.md).  

 **Wyłącz wszystkie zadania konserwacji lokacji w każdej lokacji w czasie trwania instalacji aktualizacji w tej witrynie:** Przed zainstalowaniem aktualizacji Wyłącz wszystkie zadania konserwacji lokacji, które mogą być uruchamiane w czasie procesu aktualizacji jest aktywny. Dotyczy to m.in. następujących zadań:  

-   Wykonaj kopię zapasową serwera lokacji  

-   Usuń przedawnione operacje klienta  

-   Usuń przedawnione dane odnajdywania  

Instalowanie aktualizacji może zakończyć się niepowodzeniem, jeżeli w czasie jego trwania zostanie uruchomione zadanie konserwacji bazy danych lokacji. Przed wyłączeniem zadania Zarejestruj jego harmonogram zadań, można przywrócić jego konfigurację po zainstalowaniu aktualizacji.  

Aby uzyskać więcej informacji, zobacz [zadania konserwacji programu System Center Configuration Manager](../../../core/servers/manage/maintenance-tasks.md) i [odwołania do obsługi zadań programu System Center Configuration Manager](../../../core/servers/manage/reference-for-maintenance-tasks.md).  

 **Utwórz kopię zapasową bazy danych lokacji w centralnej lokacji administracyjnej i lokacjach głównych:** Przed zaktualizowaniem lokacji Utwórz kopię zapasową bazy danych lokacji, upewnij się, że masz pomyślnego tworzenia kopii zapasowej do użycia podczas odzyskiwania po awarii.   

Aby uzyskać więcej informacji, zobacz [kopii zapasowych i odzyskiwania dla programu System Center Configuration Manager](../../../protect/understand/backup-and-recovery.md).  

<!-- Removed from update guidance 6/6/2017
 **Test the database upgrade on a copy of the most recent site database backup:** Before you update a System Center Configuration Manager central administration site or primary site, test the site database upgrade process on a copy of the site database.  

-   You should test the site database upgrade process because when you upgrade a site, the site database might be modified.  

-   Although a test database upgrade is not required, it can identify problems for the upgrade before your production database is affected.  

-   A failed site database upgrade can render your site database inoperable and might require a site recovery to restore functionality.  

-   Although the site database is shared between sites in a hierarchy, plan to test the database at each applicable site before you upgrade that site.  

-   If you use database replicas for management points at a primary site, disable replication before you create the backup of the site database.  

Configuration Manager does not support the backup of secondary sites nor does it support the test upgrade of a secondary site database.   

Do not run a test database upgrade on the production site database. Doing so updates the site database and could render your site inoperable. For more information, For more information, see [Step 2: Test the database upgrade before installing an update](/sccm/core/servers/manage/install-in-console-updates#bkmk_step2) from **Before you install an in-console update**.
-->

 **Zaplanuj pilotażowe wdrażanie klienta:** Podczas instalowania aktualizacji powodującej aktualizację klienta można przetestować tę nową aktualizację klienta w środowisku przedprodukcyjnym przed wdrożeniem i uaktualnieniem wszystkich aktywnych klientów.   

 Aby korzystać z tej opcji, przed rozpoczęciem instalacji aktualizacji, należy skonfigurować lokację do obsługi automatycznych uaktualnień w produkcji wstępnej. Aby uzyskać więcej informacji, zobacz [Uaktualnianie klientów w programie System Center Configuration Manager](../../../core/clients/manage/upgrade/upgrade-clients.md) i   
[Testowanie uaktualnień klienta w kolekcji przedprodukcyjnej w programie System Center Configuration Manager](../../../core/clients/manage/upgrade/test-client-upgrades.md).  

 **Zamierzasz używać okien obsługi do formantu, gdy serwery lokacji instalują aktualizacje:** Aby zdefiniować okres, w którym można zainstalować aktualizacji na serwerze lokacji, można użyć usługi windows.

Może to ułatwić określenie, kiedy można zainstalować aktualizację w danej hierarchii.
Przed wersją 1606 usługi systemu windows były nazywane okna obsługi. Aby uzyskać więcej informacji, zobacz [usługi systemu windows dla serwerów lokacji](/sccm/core/servers/manage/service-windows).  

 **Uruchom narzędzie sprawdzania wymagań wstępnych Instalatora:**  Przed zainstalowaniem aktualizacji 1606, możesz uruchomić narzędzie sprawdzania wymagań wstępnych niezależnie od instalacji aktualizacji. Po zainstalowaniu aktualizacji w lokacji zostanie ponownie uruchomione narzędzie sprawdzania wymagań wstępnych.  

Aby uzyskać więcej informacji, zobacz **krok 3: Uruchom narzędzie sprawdzania wymagań wstępnych przed instalacją aktualizacji** w [aktualizacji dla programu System Center Configuration Manager](../../../core/servers/manage/install-in-console-updates.md) tematu.  

> [!IMPORTANT]  
>  Po uruchomieniu narzędzia sprawdzania wymagań wstępnych niezależnie lub w ramach instalacji aktualizacji ten proces aktualizuje niektóre pliki źródłowe produktów, które są używane dla zadania obsługi lokacji. W związku z tym po uruchomieniu narzędzia sprawdzania wymagań wstępnych, lecz przed zainstalowaniem aktualizacji 1606, jeśli trzeba wykonać zadanie obsługi lokacji, uruchom **Setupwpf.exe** (Instalator programu Configuration Manager) z dysku CD. Najnowszy folder na serwerze lokacji.  

 **Zaktualizuj Lokacje:** Teraz można przystąpić do rozpoczęcia instalacji aktualizacji dla hierarchii.  
  Zaleca się zaplanowanie instalacji aktualizacji poza normalnymi godzinami pracy każdej lokacji, gdy proces instalacji aktualizacji i jego akcje, aby ponownie zainstalować składniki lokacji i role systemu lokacji będą miały jak najmniejszy wpływ na działania biznesowe.

Aby uzyskać więcej informacji, zobacz [Aktualizacje programu System Center Configuration Manager](../../../core/servers/manage/updates.md).  
