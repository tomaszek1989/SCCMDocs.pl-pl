---
title: "Lista kontrolna dotycząca 1702 | System Center Configuration Manager"
description: "Więcej informacji na temat działania należy podjąć przed zaktualizowaniem programu System Center Configuration Manager 1702 wersji."
ms.custom: na
ms.date: 05/02/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b587779e-1bd3-4ee3-8146-8e31f53499bd
caps.latest.revision: 7
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 90775fcf2549080a43e9c1606caa79d9eb90a89c
ms.openlocfilehash: c4ace452d62d4fa08f4457cb1735718ca4bd016d
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="checklist-for-installing-update-1702-for-system-center-configuration-manager"></a>Lista kontrolna instalowania aktualizacji 1702 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Korzystając z bieżącej gałęzi programu System Center Configuration Manager, można zainstalować aktualizacji w konsoli dla wersji 1702 zaktualizować hierarchii z poprzedniej wersji.

> [!TIP]  
Jest również dostępna jako wersja 1702 [nośnika linii bazowej](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions) służącego do instalacji pierwszej lokacji nowej hierarchii.

Aby uzyskać aktualizacji wersji 1702, należy użyć roli systemu lokacji punktu połączenia usługi w lokacji najwyższego poziomu w hierarchii. Może to być w trybie online lub offline. Po hierarchii do pobrania pakietu aktualizacji firmy Microsoft, można znaleźć je w konsoli, w obszarze **Administracja &gt; Przegląd &gt; usług w chmurze &gt; aktualizacji i obsługi**.

-   Gdy aktualizacja jest wymieniony jako **dostępne**, aktualizacja jest gotowy do zainstalowania. Przed zainstalowaniem wersji 1702, przejrzyj następujące informacje [o instalowaniu aktualizacji 1702](#about-installing-update-1702) i [Lista kontrolna](#checklist) konfiguracji przed rozpoczęciem aktualizacji.

-   Jeśli aktualizacja będzie wyświetlana jako **pobieranie** i nie zmienić, przejrzyj **hman.log** i **dmpdownloader.log** błędy.

    -   Jeśli dmpdownloader.log wskazuje proces dmpdownloader jest w stanie uśpienia i oczekiwania na interwał przed sprawdzania dostępności aktualizacji, można ponownie uruchomić **SMS_Executive** usługi na serwerze lokacji do ponownego uruchamiania pobierania plików redystrybucji aktualizacji.

    -   Inny typowy problem pobierania występuje, gdy ustawienia serwera proxy uniemożliwiają pobieranie z <http://silverlight.dlservice.microsoft.com> i <http://download.microsoft.com>.

Aby uzyskać więcej informacji o instalowaniu aktualizacji, zobacz [-konsoli aktualizacje i obsługę](/sccm/core/servers/manage/updates#a-namebkmkinconsolea-in-console-updates-and-servicing).

Aby uzyskać informacje dotyczące wersji bieżącej gałęzi, zobacz [linii bazowej i aktualizacji wersji](/sccm/core/servers/manage/updates#bkmk_Baselines) w [aktualizacji dla programu System Center Configuration Manager](/sccm/core/servers/manage/updates).

## <a name="about-installing-update-1702"></a>Informacje dotyczące instalowania aktualizacji 1702

**Witryny:**  
Zainstaluj aktualizację 1702 w lokacji najwyższego poziomu w hierarchii. Oznacza to, inicjuje instalację z witryny Administracja centralna, jeśli posiadasz lub autonomicznej lokacji głównej. Po zainstalowaniu tej aktualizacji w lokacji najwyższego poziomu, Lokacje podrzędne mają następujące zachowanie aktualizacji:

-   Podrzędne Lokacje główne należy zainstalować aktualizację automatycznie po zakończeniu witryny Administracja centralna instalacji aktualizacji. Podczas instalowania aktualizacji lokacji, można użyć usługi systemu windows do formantu. Aby uzyskać więcej informacji, zobacz [usługi systemu windows dla serwerów lokacji](/sccm/core/servers/manage/service-windows).

-   Po zakończeniu nadrzędnej lokacji głównej instalacji aktualizacji, należy ręcznie zaktualizować każdej lokacji dodatkowej z konsoli programu Configuration Manager. Automatyczna aktualizacja serwerów lokacji dodatkowych nie jest obsługiwana.

**Role systemu lokacji:**  
Podczas instalowania aktualizacji serwera lokacji ról systemu lokacji, które są zainstalowane na komputerze serwera lokacji i tymi, które są zainstalowane na komputerach zdalnych, zostać zaktualizowane automatycznie. Przed zainstalowaniem aktualizacji, upewnij się, że każdy serwer systemu lokacji spełnia wymagania wstępne dla operacji w nowej wersji aktualizacji.

**Konsole programu Configuration Manager:**   
Po raz pierwszy po zakończeniu aktualizacji za pomocą konsoli programu Configuration Manager będzie się monit o aktualizację tej konsoli. Aby to zrobić, należy uruchomić Instalatora programu Configuration Manager na komputerze, który jest hostem konsoli, a następnie wybierz opcję, aby zaktualizować konsolę. Zalecamy natychmiastowe instalowanie aktualizacji konsoli.

> [!IMPORTANT]  
> Po zainstalowaniu aktualizacji w witrynie Administracja centralna, należy pamiętać o następujących ograniczeń i opóźnienia, które istnieją, dopóki wszystkie podrzędne Lokacje główne również ukończyć instalację aktualizacji:    
> - **Aktualizacje klienta** nie są uruchamiane. Obejmuje to automatyczne aktualizacje klientów i produkcji wstępnej. Ponadto do chwili zakończenia ostatniej witryny instalacji aktualizacji nie można podwyższyć poziomu produkcji wstępnej klientów do środowiska produkcyjnego. Po ukończeniu instalacji aktualizacji ostatnią lokacją uaktualnienia klienta rozpocznie się w oparciu o wybrane opcje konfiguracji.   
> - **Nowe funkcje** włączyć za pomocą aktualizacji nie są dostępne. Ma to zapobiec replikacji danych powiązanych z daną funkcją zostały wysłane do lokacji, który nie został jeszcze zainstalowany obsługi tej funkcji. Po wszystkich lokacji głównych zainstaluj aktualizację, funkcja będzie dostępna do użytku.   
> - **Łącza replikacji** między witryny administracji centralnej i podrzędnych lokacji głównych jest wyświetlany jako nie uaktualniony. Zostaną wyświetlone w stan instalacji pakietu aktualizacji jako stan ukończone z ostrzeżeniem dla inicjowania replikacji monitorowanie. W węźle monitorowanie konsoli zostanie wyświetlony jako *skonfigurowano łącze*.



## <a name="checklist"></a>Lista kontrolna

**Upewnij się, że wszystkie lokacje z wersją programu System Center Configuration Manager że obsługuje aktualizację do 1702:**   
Przed rozpoczęciem instalacji aktualizacji 1702, każdy serwer lokacji w hierarchii należy uruchomić tę samą wersję programu System Center Configuration Manager. Aby zaktualizować 1702, należy użyć wersji 1602, 1606 lub 1610.

**Sprawdź stan Software Assurance lub prawa równoważne subskrypcji:**   
Musisz mieć aktywne umowę Software Assurance (SA) Aby zainstalować aktualizację 1702. Po zainstalowaniu tej aktualizacji **licencjonowania** karta przedstawia opcję, aby potwierdzić swoje **Software Assurance Data wygaśnięcia**.

Jest to opcjonalna wartość, którą można określić jako wygodny przypomnienie od daty wygaśnięcia licencji. Ta data jest widoczna podczas instalowania przyszłych aktualizacji. Użytkownik może wcześniej określić tę wartość podczas instalacji lub instalacji aktualizacji lub za pomocą **licencjonowania** na karcie **ustawienia hierarchii**, z konsoli w programie Configuration Manager.

Aby uzyskać więcej informacji, zobacz [licencjonowania i gałęzie dla programu System Center Configuration Manager](/sccm/core/understand/learn-more-editions).

**Przejrzyj zainstalowane wersje programu Microsoft .NET na serwerach systemu lokacji:** Po zainstalowaniu tej aktualizacji w lokacji, Configuration Manager automatycznie zainstaluje .NET Framework 4.5.2 na każdym komputerze, który obsługuje jedną z następujących ról systemu lokacji, gdy .NET Framework 4.5 lub nowszy nie jest już zainstalowany:

-   Punkt proxy rejestracji
-   Punkt rejestracji
-   Punkt zarządzania
-   Punkt połączenia usługi

Ta instalacja można umieścić serwer systemu lokacji w ponowne uruchomienie do czasu stanu i raportuj o błędach w podglądzie stanu składnika programu Configuration Manager. Ponadto aplikacji .NET na serwerze mogą wystąpić błędy losowe ponownego uruchomienia serwera.

Aby uzyskać więcej informacji, zobacz [Site and site system prerequisites](/sccm/core/plan-design/configs/site-and-site-system-prerequisites) (Wymagania wstępne dotyczące lokacji i systemu lokacji).

**Sprawdź wersję systemu Windows Assessment and Deployment Kit (ADK) dla systemu Windows 10** The Windows 10 ADK powinien być wersji 1607 lub nowszej. Jeśli musisz zaktualizować ADK, zrobić przed rozpoczęciem aktualizacji programu Configuration Manager. Dzięki temu, że domyślne obrazy rozruchowe są automatycznie aktualizowane do najnowszej wersji środowiska Windows PE. (Niestandardowe obrazy rozruchowe należy zaktualizować ręcznie.)

Jeśli przed zaktualizowaniem ADK aktualizacji witryny, zobacz blog [programu Configuration Manager i systemu Windows ADK dla systemu Windows 10, wersja 1607](https://blogs.technet.microsoft.com/enterprisemobility/2016/09/09/configuration-manager-and-the-windows-adk-for-windows-10-version-1607/) dla skryptu, który może służyć do obrazów rozruchowych należy ponownie wygenerować.

**Sprawdź stan lokacji i hierarchii, a następnie sprawdź, czy nie występują żadne nierozwiązane problemy:** Przed aktualizacją lokacji należy rozwiązać wszystkie problemy z działaniem serwera lokacji, serwera bazy danych lokacji i ról systemu lokacji, które są zainstalowane na komputerach zdalnych. Problemy z działaniem mogą spowodować niepowodzenie aktualizacji lokacji.

Aby uzyskać więcej informacji, zobacz [Korzystanie z alertów i systemu stanu w programie System Center Configuration Manager](/sccm/core/servers/manage/use-alerts-and-the-status-system).

**Sprawdź plik i dane replikacji między lokacjami:**   
Upewnij się, że plik i replikacji bazy danych między lokacjami jest bieżących i operacyjnej. Opóźnienia lub zaległości albo można zapobiec pomyślnym, płynnym aktualizacji.
W przypadku replikacji bazy danych można skorzystać z Analizatora linków replikacji ułatwiającego rozwiązywanie problemów przed rozpoczęciem aktualizacji.

Aby uzyskać więcej informacji, zobacz [o analizator łącza replikacji](/sccm/core/servers/manage/monitor-hierarchy-and-replication-infrastructure#BKMK_RLA) w [monitorowanie hierarchii i replikacji infrastruktury w programie System Center Configuration Manager](/sccm/core/servers/manage/monitor-hierarchy-and-replication-infrastructure) tematu.

**Zainstaluj wszystkie odpowiednie aktualizacje krytyczne systemów operacyjnych na komputerach hostujących lokację, serwer bazy danych lokacji i role zdalnego systemu lokacji:** Przed zainstalowaniem aktualizacji programu Configuration Manager, należy zainstalować wszystkie krytyczne aktualizacje dla każdego systemu uaktualnianej lokacji. Instalowana aktualizacja może wymagać ponownego uruchomienia odpowiednich komputerów przed rozpoczęciem uaktualniania.

**Wyłącz repliki bazy danych dla punktów zarządzania w lokacjach głównych:**   
Program Configuration Manager pomyślnie nie można zaktualizować lokacji głównej, z repliką bazy danych dla punktów zarządzania włączone. Wyłącz replikację bazy danych przed:

-   Tworzenie kopii zapasowej bazy danych lokacji w celu sprawdzenia uaktualnienia bazy danych.
-   Instalowana aktualizacja dla programu Configuration Manager.

Aby uzyskać więcej informacji, zobacz [Repliki bazy danych dla punktów zarządzania programu System Center Configuration Manager](/sccm/core/servers/deploy/configure/database-replicas-for-management-points).

**Ustaw ręcznej pracy awaryjnej grup dostępności AlwaysOn programu SQL Server:**   
W przypadku używania grupy dostępności, upewnij się, że grupa dostępności jest równa ręcznej pracy awaryjnej przed rozpoczęciem instalacji aktualizacji. Po zaktualizowaniu witryny ma można przywrócić pracy awaryjnej automatycznego. Aby uzyskać więcej informacji, zobacz [AlwaysOn programu SQL Server dla bazy danych lokacji](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database).

**Skonfiguruj ponownie punkty aktualizacji oprogramowania, które korzystają z usługi równoważenia obciążenia sieciowego:**   
Menedżer konfiguracji nie może zaktualizować lokacji przy użyciu klastra (NLB), punkty aktualizacji oprogramowania hosta równoważenia obciążenia sieciowego.

Użycie klastrów równoważenia obciążenia Sieciowego dla punktów aktualizacji oprogramowania, należy użyć programu Windows PowerShell do usunięcia klastra równoważenia obciążenia Sieciowego.
Aby uzyskać więcej informacji, zobacz [Planowanie aktualizacji oprogramowania w programie System Center Configuration Manager](/sccm/sum/plan-design/plan-for-software-updates).

**Wyłącz wszystkie zadania obsługi lokacji w każdej lokacji na czas instalacji aktualizacji w tej witrynie:**   
Przed zainstalowaniem tej aktualizacji należy wyłączyć wszystkie zadania obsługi, które mogą zostać uruchomione w czasie, gdy proces aktualizacji jest aktywny. Dotyczy to m.in. następujących zadań:

-   Wykonaj kopię zapasową serwera lokacji
-   Usuń przedawnione operacje klienta
-   Usuń przedawnione dane odnajdywania

Instalowanie aktualizacji może zakończyć się niepowodzeniem, jeżeli w czasie jego trwania zostanie uruchomione zadanie konserwacji bazy danych lokacji. Przed wyłączeniem zadania Zarejestruj jego harmonogram zadań, aby przywrócić jego konfigurację po zainstalowaniu aktualizacji.

Aby uzyskać więcej informacji, zobacz [zadania konserwacji programu System Center Configuration Manager](/sccm/core/servers/manage/maintenance-tasks) i [odwołania do obsługi zadań programu System Center Configuration Manager](/sccm/core/servers/manage/reference-for-maintenance-tasks).

**Utwórz kopię zapasową bazy danych lokacji w centralnej lokacji administracyjnej oraz lokacjach głównych:** Przed aktualizacją lokacji, należy utworzyć kopię zapasową bazy danych lokacji, sprawdź, czy została pomyślnie wykonana kopia zapasowa na potrzeby odzyskiwania po awarii.

Aby uzyskać więcej informacji, zobacz [kopii zapasowych i odzyskiwania dla programu System Center Configuration Manager](/sccm/protect/understand/backup-and-recovery).

**Test uaktualnienia bazy danych na kopię najnowszej kopii zapasowej bazy danych lokacji:** Przed zaktualizowaniem witryny administracji centralnej programu System Center Configuration Manager lub lokacji głównej można przetestować procesu uaktualniania bazy danych lokacji na kopii bazy danych lokacji.

-   Zaleca się testowanie procesu uaktualniania bazy danych lokacji, ponieważ podczas uaktualniania lokacji może zmodyfikować bazy danych lokacji.

-   Testowego uaktualnienia bazy danych nie jest wymagane, jednak można zidentyfikować problemy związane z uaktualnieniem przed sieci produkcyjnej bazy danych.

-   Nieudane uaktualnienie bazy danych lokacji może uniemożliwić korzystanie z bazy danych lokacji i wymóc przeprowadzenie odzyskiwania lokacji w celu przywrócenia jej funkcjonalności.

-   Choć bazy danych lokacji jest udostępniana między lokacjami w hierarchii, należy zaplanować testowanie bazy danych w każdej uaktualnianej lokacji, przed uaktualnieniem tej lokacji.

-   Jeśli są używane repliki bazy danych dla punktów zarządzania w lokacji głównej, przed utworzeniem kopii zapasowej bazy danych lokacji należy wyłączyć replikację.

Menedżer konfiguracji nie obsługuje kopii zapasowych lokacji dodatkowych ani nie obsługuje testowego uaktualnienia bazy danych lokacji dodatkowej.

Nie uruchamiaj testowego uaktualnienia bazy danych na produkcyjną bazę danych lokacji. Wykonanie tej czynności powoduje zaktualizowanie bazy danych lokacji, przez co lokacja może przestać działać. Aby uzyskać więcej informacji, zobacz [krok 2: Test uaktualnienia bazy danych przed zainstalowaniem aktualizacji](/sccm/core/servers/manage/install-in-console-updates#bkmk_step2) z **przed zainstalowaniem aktualizacji w konsoli**.

**Planowanie pilotażowe klienta:**   
Po zainstalowaniu aktualizacji, która aktualizuje klienta przed wdraża i uaktualnia wszystkich aktywnych klientów można przetestować tej nowej aktualizacji klienta w produkcji wstępnej.

Aby skorzystać z tej opcji, należy skonfigurować lokację do obsługi automatycznych uaktualnień do produkcji wstępnej, przed rozpoczęciem instalacji aktualizacji.

Aby uzyskać więcej informacji, zobacz [uaktualnienie klientów w programie System Center Configuration Manager](/sccm/core/clients/manage/upgrade/upgrade-clients) i [jak przetestować uaktualnienia klienta w kolekcji przedprodukcyjnej w programie System Center Configuration Manager](/sccm/core/clients/manage/upgrade/test-client-upgrades).

**Planowanie pod kątem używania usługi systemu windows do sterowania podczas aktualizacji serwerów lokacji:**   
Usługi systemu windows służy do definiowania okres, podczas aktualizacji do lokacji, które można zainstalować serwera.

Może to ułatwić określenie, kiedy można zainstalować aktualizację w danej hierarchii. Aby uzyskać więcej informacji, zobacz [usługi systemu windows dla serwerów lokacji](/sccm/core/servers/manage/service-windows).

**Uruchom narzędzie sprawdzania wymagań wstępnych instalacji:**   
Gdy aktualizacja jest wyświetlana w konsoli jako **dostępne,** niezależnie uruchomieniem narzędzia sprawdzania wymagań wstępnych przed instalacją aktualizacji. (Po zainstalowaniu aktualizacji w witrynie Narzędzia sprawdzania wymagań wstępnych zostanie ponownie uruchomione.)

Aby uruchomić sprawdzanie wymagań wstępnych z konsoli, przejdź do **Administracja > Przegląd > usług w chmurze > aktualizacji i obsługi.** Obok, kliknij prawym przyciskiem myszy **pakiet aktualizacji programu Configuration Manager 1702**, a następnie wybierz **Uruchom sprawdzanie wymagań wstępnych**.

Aby uzyskać więcej informacji na temat uruchamiania i następnie monitorowania Sprawdzanie wymagań wstępnych, zobacz **krok 3: Uruchom narzędzie sprawdzania wymagań wstępnych przed zainstalowaniem aktualizacji** w temacie [zainstalować aktualizacji w konsoli programu System Center Configuration Manager](/sccm/core/servers/manage/install-in-console-updates).

> [!IMPORTANT]  
> Po uruchomieniu narzędzia sprawdzania wymagań wstępnych niezależnie lub w ramach instalacji aktualizacji proces aktualizacji niektórych plików źródłowych produktu, które są używane dla zadania obsługi lokacji. W związku z tym, po uruchomieniu narzędzia sprawdzania wymagań wstępnych, lecz przed instalacją aktualizacji, jeśli konieczne jest wykonanie zadania konserwacji lokacji, uruchom **Setupwpf.exe** (Instalator programu Configuration Manager) z dysku CD. Najnowszy folder na serwerze lokacji.

**Aktualizacja witryny:**   
Teraz można przystąpić do rozpoczęcia instalacji aktualizacji dla hierarchii. Aby uzyskać więcej informacji o instalowaniu aktualizacji, zobacz [instalowanie aktualizacji w konsoli.](/sccm/core/servers/manage/install-in-console-updates#a-namebkmkinstalla-install-in-console-updates)

Zaleca się zaplanowanie instalacji aktualizacji poza godzinach pracy dla każdej lokacji podczas procesu instalowania aktualizacji i jego akcji ponownego zainstalowania składników lokacji i ról systemu lokacji ma co najmniej wpływ na operacje biznesowe.

Aby uzyskać więcej informacji, zobacz [Aktualizacje programu System Center Configuration Manager](/sccm/core/servers/manage/updates).

## <a name="post-update-checklist"></a>Po aktualizacji listy kontrolnej
Przejrzyj następujące akcje do wykonania po zakończeniu instalacji aktualizacji.
1.    Upewnij się, że lokacja lokacja replikacji jest aktywne. W konsoli, wyświetlać **monitorowanie** > **hierarchii lokacji**, i **monitorowanie** > **replikacji bazy danych** dla objawy problemów lub potwierdzenie, że działają łącza replikacji.
2.    Upewnij się, że każdy serwer lokacji i rola systemu lokacji została zaktualizowana do wersji 1702. W konsoli, można dodać kolumny opcjonalne **wersji** do wyświetlania niektóre węzły w tym **witryny** i **punktów dystrybucji**.

 W razie potrzeby, rola systemu lokacji zostanie automatycznie ponownie aktualizacji do nowej wersji. Rozważ ponowne uruchomienie systemy lokacji zdalnej nie zostanie zaktualizowana pomyślnie.
3.    Skonfiguruj ponownie repliki bazy danych dla punktów zarządzania w lokacjach głównych, które zostały wyłączone przed rozpoczęciem aktualizacji.
4.  Skonfiguruj ponownie zadania konserwacji bazy danych, które zostały wyłączone przed rozpoczęciem aktualizacji.
5.    Jeśli klient jest skonfigurowany pilotażowe przed zainstalowaniem aktualizacji, Uaktualnij klientów na plan został utworzony.

