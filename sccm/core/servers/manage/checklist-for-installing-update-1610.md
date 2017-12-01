---
title: "Lista kontrolna dotycząca 1610"
titleSuffix: Configuration Manager
description: "Więcej informacji na temat działania należy podjąć przed zaktualizowaniem do System Center Configuration Manager w wersji 1610."
ms.custom: na
ms.date: 6/6/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b411cb0-4fd1-41f2-a2f6-33738a5bde96
caps.latest.revision: "7"
author: mstewart
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 2ea2e7c5fa2ab400bfd3e95e9706f922744116b0
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2017
---
# <a name="checklist-for-installing-update-1610-for-system-center-configuration-manager"></a>Lista kontrolna dotycząca instalowania aktualizacji 1610 programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Korzystając z bieżącej gałęzi programu System Center Configuration Manager, można zainstalować aktualizacji w konsoli dla wersji 1610 aktualizacji z wersji 1606 hierarchii. Jeśli hierarchii działa w wersji 1511, 1602 lub 1606, możesz je zaktualizować do wersji 1610.

Umożliwia pobranie aktualizacji do wersji 1610, rola systemu lokacji punktu połączenia usługi należy użyć w lokacji najwyższego poziomu w hierarchii. Może to być w trybie online lub offline. Po hierarchii Pobieranie pakietu aktualizacji firmy Microsoft, można znaleźć je w konsoli w obszarze **administracji &gt; omówienie &gt; usługi w chmurze &gt; aktualizacje i obsługa**.

-   Gdy aktualizacja jest wymienione jako **dostępne**, aktualizacja jest gotowa do zainstalowania. Przed zainstalowaniem wersji 1610, przejrzyj następujące informacje [informacje dotyczące instalowania aktualizacji 1610](#about-installing-update-1610) i [Lista kontrolna](#checklist) konfiguracji, które należy wykonać przed rozpoczęciem aktualizacji.

-   Jeśli aktualizacja będzie wyświetlany jako **pobieranie** i nie zmieniać, przejrzyj **hman.log** i **dmpdownloader.log** błędów.

    -   Zazwyczaj można również uruchomić ponownie **SMS_Executive** usługi na serwerze lokacji, aby ponownie uruchomić pobieranie plików ponownej dystrybucji aktualizacji.

    -   Inny problem pobierania wspólnej występuje, gdy ustawienia serwera proxy zapobiec pliki do pobrania z <http://silverlight.dlservice.microsoft.com> i <http://download.microsoft.com>.

Aby uzyskać więcej informacji o instalowaniu aktualizacji, zobacz [w konsoli aktualizacje i obsługa](/sccm/core/servers/manage/updates#a-namebkmkinconsolea-in-console-updates-and-servicing).

Informacje o wersji Current Branch, zobacz [wersje linii bazowej i aktualizacji](/sccm/core/servers/manage/updates#bkmk_Baselines) w [aktualizacji dla programu System Center Configuration Manager](/sccm/core/servers/manage/updates).

## <a name="about-installing-update-1610"></a>Informacje dotyczące instalowania aktualizacji 1610

**Lokacje:**  
Aktualizacja 1610 można zainstalować tylko w lokacji najwyższego poziomu w hierarchii. Oznacza to, należy zainicjować instalację, z witryny Administracja centralna, jeśli masz lub autonomicznej lokacji głównej. Po aktualizacja zostanie zainstalowana w lokacji najwyższego poziomu, Lokacje podrzędne mają następujące zachowania aktualizacji:

-   Podrzędne Lokacje główne instalują aktualizację automatycznie po zakończeniu przez lokację administracji centralnej instalacji aktualizacji. Można użyć usługi windows do formantu, gdy lokacja instaluje aktualizacje. Przed wersją 1606 usługi systemu windows były nazywane okna obsługi. Aby uzyskać więcej informacji, zobacz [usługi systemu windows dla serwerów lokacji](/sccm/core/servers/manage/service-windows).

-   Należy ręcznie zaktualizować Lokacje dodatkowe przy użyciu konsoli programu Configuration Manager po nadrzędną lokację główną ukończy instalację aktualizacji. Automatyczna aktualizacja serwerów lokacji dodatkowych nie jest obsługiwana.

**Role systemu lokacji:**  
Serwer lokacji instaluje aktualizację, Pobierz zaktualizowany role systemu lokacji, które są zainstalowane na serwerze lokacji oraz te, które są instalowane automatycznie na komputerach zdalnych. Dlatego przed zainstalowaniem aktualizacji, upewnij się, że każdy serwer systemu lokacji spełnia ewentualne nowe wymagania wstępne dotyczące działania z nową wersją aktualizacji.

**Konsole programu Configuration Manager:**   
Użycie konsoli programu Configuration Manager po zakończeniu aktualizacji po raz pierwszy pojawi się monit zaktualizowanie tej konsoli. Aby to zrobić, należy uruchomić Instalatora programu Configuration Manager na komputerze, który jest hostem konsoli i następnie wybierz opcję, aby zaktualizować konsolę. Zalecamy natychmiastowe instalowanie aktualizacji konsoli.



## <a name="checklist"></a>Lista kontrolna

**Upewnij się, że we wszystkich lokacjach uruchomiona obsługiwana wersja programu System Center Configuration Manager:** Przed rozpoczęciem instalacji aktualizacji 1610 każdej lokacji w hierarchii musi być uruchomiona tej samej wersji programu System Center Configuration Manager: danej wersji 1511, 1602 lub 1606.

**Sprawdź stan Software Assurance lub równoważne subskrypcji:**   
Musisz mieć aktywne umowę Software Assurance (SA) Aby zainstalować aktualizację 1610. Po zainstalowaniu wersji 1610 mają opcję na **licencjonowania** kartę, aby upewnić się, Twoje **Data wygaśnięcia Software Assurance**.

Jest to wartość opcjonalna wskazanym jako wygodny monitu od daty wygaśnięcia licencji, która jest widoczna podczas instalowania przyszłych aktualizacji. Po zainstalowaniu programu Configuration Manager z wersji 1606 nośnika linii bazowej, użytkownik może wcześniej określić tę wartość podczas instalacji lub w **licencjonowania** karcie **ustawienia hierarchii** po zainstalowaniu lokacji.

Aby uzyskać więcej informacji, zobacz [licencjonowania i gałęzi programu System Center Configuration Manager](/sccm/core/understand/learn-more-editions).

**Przejrzyj wersje programu .NET firmy Microsoft są zainstalowane na serwerach systemu lokacji:** Podczas instalowania aktualizacji 1610 lokacji programu Configuration Manager automatycznie instaluje program .NET Framework 4.5.2 na każdym komputerze, który hostuje jedną z następujących ról systemu lokacji, gdy .NET Framework 4.5 lub nowszy nie jest już zainstalowany:

-   Punkt proxy rejestracji
-   Punkt rejestracji
-   Punkt zarządzania
-   Punkt połączenia usługi

Ta instalacja można umieścić serwer systemu lokacji do na ponowne uruchomienie do czasu stanu i raport błędów w przeglądarce stanu składników programu Configuration Manager. Ponadto aplikacji .NET na serwerze mogą wystąpić błędy losowe ponownego uruchomienia serwera.

Aby uzyskać więcej informacji, zobacz [Site and site system prerequisites](/sccm/core/plan-design/configs/site-and-site-system-prerequisites) (Wymagania wstępne dotyczące lokacji i systemu lokacji).

**Sprawdź stan lokacji i hierarchii, a następnie sprawdź, czy nie występują żadne nierozwiązane problemy:** Przed uaktualnieniem lokacji należy rozwiązać wszystkie problemy z działaniem serwera lokacji, serwera bazy danych lokacji i ról systemu lokacji, które są zainstalowane na komputerach zdalnych. Problemy z działaniem mogą spowodować niepowodzenie aktualizacji lokacji.

Aby uzyskać więcej informacji, zobacz [Korzystanie z alertów i systemu stanu w programie System Center Configuration Manager](/sccm/core/servers/manage/use-alerts-and-the-status-system).

**Przejrzyj replikację plików i danych między lokacjami:**   
Upewnij się, że plik i replikacji bazy danych między lokacjami jest operacyjne i bieżący. Opóźnień lub zaległości może uniemożliwić smooth aktualizacji powiodło się.
W przypadku replikacji bazy danych można skorzystać z Analizatora linków replikacji ułatwiającego rozwiązywanie problemów przed rozpoczęciem aktualizacji.

Aby uzyskać więcej informacji, zobacz [o analizator łącza replikacji](/sccm/core/servers/manage/monitor-hierarchy-and-replication-infrastructure#BKMK_RLA) w [Monitorowanie infrastruktury hierarchii i replikacji w programie System Center Configuration Manager](/sccm/core/servers/manage/monitor-hierarchy-and-replication-infrastructure) tematu.

**Zainstaluj wszystkie odpowiednie aktualizacje krytyczne dla systemów operacyjnych na komputerach hostujących lokację, serwer bazy danych lokacji i role zdalnego systemu lokacji:** Przed zainstalowaniem aktualizacji programu Configuration Manager, należy zainstalować wszystkie aktualizacje krytyczne dla odpowiednich systemów lokacji. Jeśli aktualizacja może wymagać ponownego uruchomienia odpowiednich komputerów przed rozpoczęciem aktualizacji programu Configuration Manager.

**Wyłącz repliki bazy danych dla punktów zarządzania w lokacjach głównych:**   
Menedżer konfiguracji nie może pomyślnie zaktualizować lokacji głównej, z repliki bazy danych dla punktów zarządzania włączone. Wyłącz replikację bazy danych, przed zainstalowaniem aktualizacji programu Configuration Manager.

Aby uzyskać więcej informacji, zobacz [Repliki bazy danych dla punktów zarządzania programu System Center Configuration Manager](/sccm/core/servers/deploy/configure/database-replicas-for-management-points).

**Ustaw ręcznego przełączania trybu failover grupy dostępności AlwaysOn programu SQL Server:**   
Przed zainstalowaniem aktualizacji, na przykład wersji 1610, upewnij się, że grupy dostępności jest ustawiona na ręcznego przełączania trybu failover. Po zaktualizowaniu lokacji można przywrócić trybu failover automatycznego. Aby uzyskać więcej informacji, zobacz [AlwaysOn programu SQL Server dla bazy danych lokacji](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database).

**Skonfiguruj ponownie punkty aktualizacji oprogramowania, które używają usługi równoważenia obciążenia sieciowego:**   
Menedżer konfiguracji nie może zaktualizować lokacji hostującej punkty aktualizacji oprogramowania (NLB) klastra równoważenia obciążenia sieciowego.

Korzystając z klastrami równoważenia obciążenia Sieciowego dla punktów aktualizacji oprogramowania, należy usunąć klaster równoważenia obciążenia Sieciowego za pomocą programu Windows PowerShell.
Aby uzyskać więcej informacji, zobacz [Planowanie aktualizacji oprogramowania w programie System Center Configuration Manager](/sccm/sum/plan-design/plan-for-software-updates).

**Wyłącz wszystkie zadania konserwacji lokacji w każdej lokacji w czasie trwania instalacji aktualizacji w tej witrynie:**   
Przed zainstalowaniem aktualizacji Wyłącz wszystkie zadania konserwacji lokacji, które mogą zostać uruchomione w czasie, gdy proces aktualizacji jest aktywny. Dotyczy to m.in. następujących zadań:

-   Wykonaj kopię zapasową serwera lokacji
-   Usuń przedawnione operacje klienta
-   Usuń przedawnione dane odnajdywania

Instalowanie aktualizacji może zakończyć się niepowodzeniem, jeżeli w czasie jego trwania zostanie uruchomione zadanie konserwacji bazy danych lokacji. Przed wyłączeniem zadania Zarejestruj jego harmonogram zadań, można przywrócić jego konfigurację po zainstalowaniu aktualizacji.

Aby uzyskać więcej informacji, zobacz [zadania konserwacji programu System Center Configuration Manager](/sccm/core/servers/manage/maintenance-tasks) i [odwołania do obsługi zadań programu System Center Configuration Manager](/sccm/core/servers/manage/reference-for-maintenance-tasks).

**Utwórz kopię zapasową bazy danych lokacji w centralnej lokacji administracyjnej i lokacjach głównych:** Przed zaktualizowaniem lokacji Utwórz kopię zapasową bazy danych lokacji, upewnij się, że masz pomyślnego tworzenia kopii zapasowej do użycia podczas odzyskiwania po awarii.

Aby uzyskać więcej informacji, zobacz [kopii zapasowych i odzyskiwania dla programu System Center Configuration Manager](/sccm/protect/understand/backup-and-recovery).

<!-- Removed from update guidance 6/6/2017
**Test the database upgrade on a copy of the most recent site database backup:** 
Before you update a System Center Configuration Manager central administration site or primary site, test the site database upgrade process on a copy of the site database.

-   We recommend that you test the site database upgrade process because when you upgrade a site, the site database might be modified.

-   Although a test database upgrade is not required, it can identify problems for the upgrade before your production database is affected.

-   A failed site database upgrade can render your site database inoperable and might require a site recovery to restore functionality.

-   Although the site database is shared between sites in a hierarchy, plan to test the database at each applicable site before you upgrade that site.

-   If you use database replicas for management points at a primary site, disable replication before you create the backup of the site database.

Configuration Manager does not support the backup of secondary sites nor does it support the test upgrade of a secondary site database.

Do not run a test database upgrade on the production site database. Doing so updates the site database and could render your site inoperable. For more information, see [Step 2: Test the database upgrade before installing an update](/sccm/core/servers/manage/install-in-console-updates#bkmk_step2) from **Before you install an in-console update**.
-->

**Zaplanuj pilotażowe wdrażanie klienta:**   
Podczas instalowania aktualizacji powodującej aktualizację klienta można przetestować tę nową aktualizację klienta w środowisku przedprodukcyjnym przed wdrożeniem i uaktualnieniem wszystkich aktywnych klientów.

Aby móc korzystać z tej opcji, należy skonfigurować lokację do obsługi automatycznych uaktualnień w produkcji wstępnej, przed rozpoczęciem instalacji aktualizacji.

Aby uzyskać więcej informacji, zobacz [uaktualniania klientów w programie System Center Configuration Manager](/sccm/core/clients/manage/upgrade/upgrade-clients) i [testowanie uaktualnień klienta w kolekcji przedprodukcyjnej w programie System Center Configuration Manager](/sccm/core/clients/manage/upgrade/test-client-upgrades).

**Zamierzasz używać okien obsługi do formantu, gdy serwery lokacji instalują aktualizacje:**   
Aby zdefiniować okres, w którym można zainstalować aktualizacji na serwerze lokacji, można użyć usługi windows.

Może to ułatwić określenie, kiedy można zainstalować aktualizację w danej hierarchii. Przed wersją 1606 usługi systemu windows były nazywane okna obsługi. Aby uzyskać więcej informacji, zobacz [usługi systemu windows dla serwerów lokacji](/sccm/core/servers/manage/service-windows).

**Uruchom narzędzie sprawdzania wymagań wstępnych Instalatora:**   
Gdy aktualizacja jest wyświetlane w konsoli jako **dostępne,** niezależnie można uruchomić narzędzie sprawdzania wymagań wstępnych przed instalacją aktualizacji. (Po zainstalowaniu aktualizacji w witrynie Narzędzia sprawdzania wymagań wstępnych zostanie ponownie uruchomione.)

Aby uruchomić sprawdzanie wymagań wstępnych z konsoli, przejdź do **Administracja > Przegląd > usługi w chmurze > aktualizacje i obsługa.** Następnie kliknij prawym przyciskiem myszy **pakiet aktualizacji programu Configuration Manager 1610**, a następnie wybierz pozycję **sprawdzania wymagań wstępnych**.

Aby uzyskać więcej informacji na temat uruchamiania i następnie monitorowania Sprawdzanie wymagań wstępnych, zobacz **krok 3: Uruchom narzędzie sprawdzania wymagań wstępnych przed instalacją aktualizacji** w temacie [instalacja aktualizacji w konsoli programu System Center Configuration Manager](/sccm/core/servers/manage/install-in-console-updates).

> [!IMPORTANT]  
> Po uruchomieniu narzędzia sprawdzania wymagań wstępnych niezależnie lub w ramach instalacji aktualizacji ten proces aktualizuje niektóre pliki źródłowe produktów, które są używane dla zadania obsługi lokacji. W związku z tym po uruchomieniu narzędzia sprawdzania wymagań wstępnych, lecz przed zainstalowaniem aktualizacji 1610, jeśli trzeba wykonać zadanie obsługi lokacji, uruchom **Setupwpf.exe** (Instalator programu Configuration Manager) z dysku CD. Najnowszy folder na serwerze lokacji.

**Zaktualizuj Lokacje:**   
Teraz można przystąpić do rozpoczęcia instalacji aktualizacji dla hierarchii. Aby uzyskać więcej informacji o instalowaniu aktualizacji, zobacz [instalacja aktualizacji w konsoli.](/sccm/core/servers/manage/install-in-console-updates#a-namebkmkinstalla-install-in-console-updates)

Zaleca się zaplanowanie instalacji aktualizacji poza normalnymi godzinami pracy każdej lokacji, gdy proces instalacji aktualizacji i jego akcje, aby ponownie zainstalować składniki lokacji i role systemu lokacji będą miały jak najmniejszy wpływ na działania biznesowe.

Aby uzyskać więcej informacji, zobacz [Aktualizacje programu System Center Configuration Manager](/sccm/core/servers/manage/updates).
