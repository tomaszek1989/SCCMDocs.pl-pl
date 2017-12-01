---
title: "Lista kontrolna dotycząca 1702"
titleSuffix: Configuration Manager
description: "Więcej informacji na temat działania należy podjąć przed zaktualizowaniem do System Center Configuration Manager w wersji 1702."
ms.custom: na
ms.date: 06/06/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b587779e-1bd3-4ee3-8146-8e31f53499bd
caps.latest.revision: "7"
author: mstewart
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: bb09c9a52a548ac70acd878c9bec30afd711338d
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2017
---
# <a name="checklist-for-installing-update-1702-for-system-center-configuration-manager"></a>Lista kontrolna dotycząca instalowania aktualizacji 1702 programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Korzystając z bieżącej gałęzi programu System Center Configuration Manager, można zainstalować aktualizacji w konsoli dla wersji 1702 zaktualizować hierarchii z poprzedniej wersji.

> [!TIP]  
Jest również dostępna jako wersja 1702 [nośnika linii bazowej](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions) czy służy do instalowania pierwszej lokacji nowej hierarchii.

Umożliwia pobranie aktualizacji do wersji 1702, rola systemu lokacji punktu połączenia usługi należy użyć w lokacji najwyższego poziomu w hierarchii. Może to być w trybie online lub offline. Po hierarchii Pobieranie pakietu aktualizacji firmy Microsoft, można znaleźć je w konsoli w obszarze **administracji &gt; omówienie &gt; usługi w chmurze &gt; aktualizacje i obsługa**.

-   Gdy aktualizacja jest wymienione jako **dostępne**, aktualizacja jest gotowa do zainstalowania. Przed zainstalowaniem wersji 1702, przejrzyj następujące informacje [informacje dotyczące instalowania aktualizacji 1702](#about-installing-update-1702) i [Lista kontrolna](#checklist) konfiguracji, które należy wykonać przed rozpoczęciem aktualizacji.

-   Jeśli aktualizacja będzie wyświetlany jako **pobieranie** i nie zmieniać, przejrzyj **hman.log** i **dmpdownloader.log** błędów.

    -   Jeśli dziennik dmpdownloader.log wskazuje proces dmpdownloader jest w stanie uśpienia i oczekiwania na interwał przed sprawdzania aktualizacji, można ponownie uruchomić **SMS_Executive** usługi na serwerze lokacji, aby ponownie uruchomić pobieranie plików ponownej dystrybucji aktualizacji.

    -   Inny problem pobierania wspólnej występuje, gdy ustawienia serwera proxy zapobiec pliki do pobrania z <http://silverlight.dlservice.microsoft.com> i <http://download.microsoft.com>.

Aby uzyskać więcej informacji o instalowaniu aktualizacji, zobacz [w konsoli aktualizacje i obsługa](/sccm/core/servers/manage/updates#a-namebkmkinconsolea-in-console-updates-and-servicing).

Informacje o wersji Current Branch, zobacz [wersje linii bazowej i aktualizacji](/sccm/core/servers/manage/updates#bkmk_Baselines) w [aktualizacji dla programu System Center Configuration Manager](/sccm/core/servers/manage/updates).

## <a name="about-installing-update-1702"></a>Informacje dotyczące instalowania aktualizacji 1702

**Lokacje:**  
Musisz zainstalować aktualizację 1702 w lokacji najwyższego poziomu w hierarchii. Oznacza to, należy zainicjować instalację, z witryny Administracja centralna, jeśli masz lub autonomicznej lokacji głównej. Po zainstalowaniu aktualizacji w lokacji najwyższego poziomu Lokacje podrzędne mają następujące zachowania aktualizacji:

-   Podrzędne Lokacje główne instalują aktualizację automatycznie po instalacji aktualizacji centralnej lokacji administracyjnej. Podczas instalowania aktualizacji w lokacji, można użyć usługi windows do formantu. Aby uzyskać więcej informacji, zobacz [usługi systemu windows dla serwerów lokacji](/sccm/core/servers/manage/service-windows).

-   Należy ręcznie zaktualizować każda lokacja dodatkowa z poziomu konsoli programu Configuration Manager po instalacji aktualizacji lokacji głównej. Automatyczna aktualizacja serwerów lokacji dodatkowych nie jest obsługiwana.

**Role systemu lokacji:**  
Podczas instalowania aktualizacji serwera lokacji role systemu lokacji, które są zainstalowane na komputerze serwera lokacji oraz te, które są zainstalowane na komputerach zdalnych, automatycznie aktualizowany. Przed zainstalowaniem aktualizacji, upewnij się, że każdy serwer systemu lokacji spełnia wymagania wstępne dotyczące działania z nową wersją aktualizacji.

**Konsole programu Configuration Manager:**   
Użycie konsoli programu Configuration Manager po zakończeniu aktualizacji po raz pierwszy pojawi się monit zaktualizowanie tej konsoli. Aby to zrobić, należy uruchomić Instalatora programu Configuration Manager na komputerze, który jest hostem konsoli i następnie wybierz opcję, aby zaktualizować konsolę. Zalecamy natychmiastowe instalowanie aktualizacji konsoli.

> [!IMPORTANT]  
> Po zainstalowaniu aktualizacji w centralnej lokacji administracyjnej, należy pamiętać o następujących ograniczeniach oraz opóźnienia, które istnieją, dopóki wszystkie podrzędne Lokacje główne również ukończenie instalacji aktualizacji:    
> - **Uaktualnienia klienta** nie uruchamiaj. Dotyczy to również aktualizacji automatycznych klientów oraz klientów przedprodukcyjnych. Ponadto przed ostatnią lokacją zakończeniem instalacji aktualizacji nie można podwyższyć poziomu klientów przedprodukcyjnego do środowiska produkcyjnego. Po zakończeniu instalacji aktualizacji ostatnią lokacją uaktualnienia klienta rozpocznie zależności od wybranych opcji konfiguracji.   
> - **Nowe funkcje** włączyć przy użyciu aktualizacji nie są dostępne. Ma to zapobiec replikacji danych dotyczących tej funkcji z są wysyłane do lokacji, który nie został jeszcze zainstalowany Obsługa tej funkcji. Po wszystkich lokacji głównych zainstaluj aktualizację, funkcja będzie dostępna do użycia.   
> - **Łącza replikacji** między centralną lokacją administracyjną i podrzędne Lokacje główne wyświetlane jako nie uaktualniony. Spowoduje to wyświetlenie w stan instalacji pakietu aktualizacji stanu ukończone z ostrzeżeniem na potrzeby inicjowania replikacji monitorowanie. W węźle Monitorowanie w konsoli jest wyświetlana *Trwa konfiguracja łącza*.



## <a name="checklist"></a>Lista kontrolna

**Upewnij się, że wszystkie lokacje z wersją programu System Center Configuration Manager czy obsługuje aktualizacji do 1702:**   
Każdy serwer lokacji w hierarchii muszą korzystać z tej samej wersji programu System Center Configuration Manager, przed rozpoczęciem instalacji aktualizacji 1702. Aby zaktualizować 1702, należy użyć wersji 1602, 1606 lub 1610.

**Sprawdź stan Software Assurance lub równoważne subskrypcji:**   
Musisz mieć aktywne umowę Software Assurance (SA) Aby zainstalować aktualizację 1702. Po zainstalowaniu tej aktualizacji **licencjonowania** możliwość sprawdzenia przedstawia informacje o karcie Twojej **Data wygaśnięcia Software Assurance**.

Jest to opcjonalna wartość, która może służyć jako wygodny monitu od daty wygaśnięcia licencji. Ta data jest widoczny podczas instalowania przyszłych aktualizacji. Użytkownik może wcześniej określić tę wartość podczas instalacji lub instalacji aktualizacji lub przy użyciu **licencjonowania** karcie **ustawienia hierarchii**, z konsoli w programie Configuration Manager.

Aby uzyskać więcej informacji, zobacz [licencjonowania i gałęzi programu System Center Configuration Manager](/sccm/core/understand/learn-more-editions).

**Przejrzyj wersje programu .NET firmy Microsoft są zainstalowane na serwerach systemu lokacji:** Po zainstalowaniu tej aktualizacji w lokacji, programu Configuration Manager automatycznie instaluje program .NET Framework 4.5.2 na każdym komputerze, który hostuje jedną z następujących ról systemu lokacji, gdy .NET Framework 4.5 lub nowszy nie jest już zainstalowany:

-   Punkt proxy rejestracji
-   Punkt rejestracji
-   Punkt zarządzania
-   Punkt połączenia usługi

Ta instalacja można umieścić serwer systemu lokacji do na ponowne uruchomienie do czasu stanu i raport błędów w przeglądarce stanu składników programu Configuration Manager. Ponadto aplikacji .NET na serwerze mogą wystąpić błędy losowe ponownego uruchomienia serwera.

Aby uzyskać więcej informacji, zobacz [Site and site system prerequisites](/sccm/core/plan-design/configs/site-and-site-system-prerequisites) (Wymagania wstępne dotyczące lokacji i systemu lokacji).

**Przejrzyj wersje systemu Windows Assessment and Deployment Kit (ADK) dla systemu Windows 10** Windows 10 ADK powinna być w wersji 1607 lub nowszej. Jeśli musisz zaktualizować ADK, to zrobić przed rozpoczęciem aktualizacji programu Configuration Manager. Dzięki temu domyślne obrazy rozruchowe są automatycznie aktualizowane do najnowszej wersji systemu Windows PE. (Niestandardowe obrazy rozruchowe należy zaktualizować ręcznie.)

Przed zaktualizowaniem ADK aktualizacji witryny, znajduje się we wpisie [programu Configuration Manager i Windows ADK dla systemu Windows 10, wersji 1607](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/09/configuration-manager-and-the-windows-adk-for-windows-10-version-1607/) skryptu, który można ponownie wygenerować obrazów rozruchowych.

**Sprawdź stan lokacji i hierarchii, a następnie sprawdź, czy nie występują żadne nierozwiązane problemy:** Przed uaktualnieniem lokacji należy rozwiązać wszystkie problemy z działaniem serwera lokacji, serwera bazy danych lokacji i ról systemu lokacji, które są zainstalowane na komputerach zdalnych. Problemy z działaniem mogą spowodować niepowodzenie aktualizacji lokacji.

Aby uzyskać więcej informacji, zobacz [Korzystanie z alertów i systemu stanu w programie System Center Configuration Manager](/sccm/core/servers/manage/use-alerts-and-the-status-system).

**Przejrzyj replikację plików i danych między lokacjami:**   
Upewnij się, że plik i replikacji bazy danych między lokacjami jest operacyjne i bieżący. Opóźnień lub zaległości może uniemożliwić smooth aktualizacji powiodło się.
W przypadku replikacji bazy danych można skorzystać z Analizatora linków replikacji ułatwiającego rozwiązywanie problemów przed rozpoczęciem aktualizacji.

Aby uzyskać więcej informacji, zobacz [o analizator łącza replikacji](/sccm/core/servers/manage/monitor-hierarchy-and-replication-infrastructure#BKMK_RLA) w [Monitorowanie infrastruktury hierarchii i replikacji w programie System Center Configuration Manager](/sccm/core/servers/manage/monitor-hierarchy-and-replication-infrastructure) tematu.

**Zainstaluj wszystkie odpowiednie aktualizacje krytyczne dla systemów operacyjnych na komputerach hostujących lokację, serwer bazy danych lokacji i role zdalnego systemu lokacji:** Przed zainstalowaniem aktualizacji programu Configuration Manager, należy zainstalować wszystkie aktualizacje krytyczne dla odpowiednich systemów lokacji. Instalowana aktualizacja może wymagać ponownego uruchomienia odpowiednich komputerów przed rozpoczęciem uaktualniania.

**Wyłącz repliki bazy danych dla punktów zarządzania w lokacjach głównych:**   
Menedżer konfiguracji nie może pomyślnie zaktualizować lokacji głównej, z repliki bazy danych dla punktów zarządzania włączone. Wyłącz replikację bazy danych, przed zainstalowaniem aktualizacji programu Configuration Manager.

Aby uzyskać więcej informacji, zobacz [Repliki bazy danych dla punktów zarządzania programu System Center Configuration Manager](/sccm/core/servers/deploy/configure/database-replicas-for-management-points).

**Ustaw ręcznego przełączania trybu failover grupy dostępności AlwaysOn programu SQL Server:**   
Używanie grupy dostępności, upewnij się, że grupa dostępności jest ustawiona na ręcznego przełączania trybu failover, przed rozpoczęciem instalacji aktualizacji. Po zaktualizowaniu lokacji ma można przywrócić trybu failover automatycznego. Aby uzyskać więcej informacji, zobacz [AlwaysOn programu SQL Server dla bazy danych lokacji](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database).

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
Before you update a System Center Configuration Manager central administration site or primary site, you can test the site database upgrade process on a copy of the site database.

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
Aby zdefiniować okres, podczas którego aktualizacji do lokacji można zainstalować serwera należy używać okien obsługi.

Może to ułatwić określenie, kiedy można zainstalować aktualizację w danej hierarchii. Aby uzyskać więcej informacji, zobacz [usługi systemu windows dla serwerów lokacji](/sccm/core/servers/manage/service-windows).

**Uruchom narzędzie sprawdzania wymagań wstępnych Instalatora:**   
Gdy aktualizacja jest wyświetlane w konsoli jako **dostępne,** niezależnie można uruchomić narzędzie sprawdzania wymagań wstępnych przed instalacją aktualizacji. (Po zainstalowaniu aktualizacji w witrynie Narzędzia sprawdzania wymagań wstępnych zostanie ponownie uruchomione.)

Aby uruchomić sprawdzanie wymagań wstępnych z konsoli, przejdź do **Administracja > Przegląd > usługi w chmurze > aktualizacje i obsługa.** Następnie kliknij prawym przyciskiem myszy **pakiet aktualizacji programu Configuration Manager 1702**, a następnie wybierz pozycję **sprawdzania wymagań wstępnych**.

Aby uzyskać więcej informacji na temat uruchamiania i następnie monitorowania Sprawdzanie wymagań wstępnych, zobacz **krok 3: Uruchom narzędzie sprawdzania wymagań wstępnych przed instalacją aktualizacji** w temacie [instalacja aktualizacji w konsoli programu System Center Configuration Manager](/sccm/core/servers/manage/install-in-console-updates).

> [!IMPORTANT]  
> Po uruchomieniu narzędzia sprawdzania wymagań wstępnych niezależnie lub w ramach instalacji aktualizacji ten proces aktualizuje niektóre pliki źródłowe produktów, które są używane dla zadania obsługi lokacji. W związku z tym po uruchomieniu narzędzia sprawdzania wymagań wstępnych, lecz przed zainstalowaniem aktualizacji, jeśli trzeba wykonać zadanie obsługi lokacji, uruchom **Setupwpf.exe** (Instalator programu Configuration Manager) z dysku CD. Najnowszy folder na serwerze lokacji.

**Zaktualizuj Lokacje:**   
Teraz można przystąpić do rozpoczęcia instalacji aktualizacji dla hierarchii. Aby uzyskać więcej informacji o instalowaniu aktualizacji, zobacz [instalacja aktualizacji w konsoli.](/sccm/core/servers/manage/install-in-console-updates#a-namebkmkinstalla-install-in-console-updates)

Zaleca się zaplanowanie instalacji aktualizacji poza normalnymi godzinami pracy każdej lokacji, gdy proces instalacji aktualizacji i jego akcje, aby ponownie zainstalować składniki lokacji i role systemu lokacji będą miały jak najmniejszy wpływ na działania biznesowe.

Aby uzyskać więcej informacji, zobacz [Aktualizacje programu System Center Configuration Manager](/sccm/core/servers/manage/updates).

## <a name="post-update-checklist"></a>Po aktualizacji listy kontrolnej
Przejrzyj następujące akcje do wykonania po zakończeniu instalacji aktualizacji.
1.  Upewnij się, że lokacja lokacja replikacji jest aktywne. W konsoli wyświetlić **monitorowanie** > **hierarchia lokacji**, i **monitorowanie** > **replikacji bazy danych** do wskazania problemów lub potwierdzenie, że łącza replikacji są aktywne.
2.  Upewnij się, że każdy serwer lokacji i ról systemu lokacji został zaktualizowany do wersji 1702. W konsoli, można dodać kolumny opcjonalne **wersji** do wyświetlenia niektóre węzły w tym **witryny** i **punktów dystrybucji**.

 Jeśli to konieczne, rola systemu lokacji ponownie zainstaluje automatycznie zaktualizować do nowej wersji. Należy rozważyć ponowne uruchomienie systemów lokacji zdalnych, które nie zostanie zaktualizowana pomyślnie.
3.  Skonfiguruj ponownie repliki bazy danych dla punktów zarządzania w lokacjach głównych, które zostały wyłączone przed rozpoczęciem aktualizacji.
4.  Skonfiguruj ponownie zadania konserwacji bazy danych, które zostały wyłączone przed rozpoczęciem aktualizacji.
5.  Jeśli skonfigurowano wdrażania pilotażowego przed zainstalowaniem aktualizacji klienta, należy uaktualnić klientów na planu, który został utworzony.
