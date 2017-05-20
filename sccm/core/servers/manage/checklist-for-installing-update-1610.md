---
title: "Lista kontrolna dotycząca 1610 | System Center Configuration Manager"
description: "Więcej informacji na temat działania należy podjąć przed zaktualizowaniem programu System Center Configuration Manager 1610 wersji."
ms.custom: na
ms.date: 2/7/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b411cb0-4fd1-41f2-a2f6-33738a5bde96
caps.latest.revision: 7
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 30af3326578d39c6d995672071705bcaeb877e4d
ms.openlocfilehash: 640fc5ddb4e0a6828901b7f406ca72fc210b2970
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="checklist-for-installing-update-1610-for-system-center-configuration-manager"></a>Lista kontrolna instalowania aktualizacji 1610 dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Korzystając z bieżącej gałęzi programu System Center Configuration Manager, można zainstalować aktualizację w konsoli dla wersji 1610 aktualizacji z wersji 1606 hierarchii. Jeśli hierarchia działa w wersji 1511, 1602 lub 1606, można zaktualizować wersji 1610.

Aby uzyskać aktualizacji wersji 1610, należy użyć roli systemu lokacji punktu połączenia usługi w lokacji najwyższego poziomu w hierarchii. Może to być w trybie online lub offline. Po hierarchii do pobrania pakietu aktualizacji firmy Microsoft, można znaleźć je w konsoli, w obszarze **Administracja &gt; Przegląd &gt; usług w chmurze &gt; aktualizacji i obsługi**.

-   Gdy aktualizacja jest wymieniony jako **dostępne**, aktualizacja jest gotowy do zainstalowania. Przed zainstalowaniem wersji 1610, przejrzyj następujące informacje [o instalowaniu aktualizacji 1610](#about-installing-update-1610) i [Lista kontrolna](#checklist) konfiguracji przed rozpoczęciem aktualizacji.

-   Jeśli aktualizacja będzie wyświetlana jako **pobieranie** i nie zmienić, przejrzyj **hman.log** i **dmpdownloader.log** błędy.

    -   Zazwyczaj można również uruchomić ponownie **SMS_Executive** usługi na serwerze lokacji do ponownego uruchamiania pobierania plików redystrybucji aktualizacji.

    -   Inny typowy problem pobierania występuje, gdy ustawienia serwera proxy uniemożliwiają pobieranie z <http://silverlight.dlservice.microsoft.com> i <http://download.microsoft.com>.

Aby uzyskać więcej informacji o instalowaniu aktualizacji, zobacz [-konsoli aktualizacje i obsługę](/sccm/core/servers/manage/updates#a-namebkmkinconsolea-in-console-updates-and-servicing).

Informacje o wersji bieżącej gałęzi, można znaleźć w temacie [linii bazowej i aktualizacji wersji](/sccm/core/servers/manage/updates#bkmk_Baselines) w [aktualizacje programu System Center Configuration Manager](/sccm/core/servers/manage/updates).

## <a name="about-installing-update-1610"></a>Informacje dotyczące instalowania aktualizacji 1610

**Witryny:**  
Aktualizacja 1610 można zainstalować tylko w lokacji najwyższego poziomu w hierarchii. Oznacza to, inicjuje instalację z witryny Administracja centralna, jeśli posiadasz lub autonomicznej lokacji głównej. Po aktualizacji są instalowane w lokacji najwyższego poziomu, Lokacje podrzędne mają następujące zachowanie aktualizacji:

-   Podrzędne Lokacje główne należy zainstalować aktualizację automatycznie po ukończeniu instalacji aktualizacji lokacji administracji centralnej. Podczas instalowania aktualizacji lokacji, można użyć usługi systemu windows do formantu. Przed wersją 1606 usługi systemu windows były nazywane okna obsługi. Aby uzyskać więcej informacji, zobacz [usługi systemu windows dla serwerów lokacji](/sccm/core/servers/manage/service-windows).

-   Po ukończeniu instalacji aktualizacji w lokacji głównej nadrzędnej, należy ręcznie zaktualizować dodatkowej lokacji z konsoli programu Configuration Manager. Automatyczna aktualizacja serwerów lokacji dodatkowych nie jest obsługiwana.

**Role systemu lokacji:**  
Podczas instalowania aktualizacji serwera lokacji zostanie zaktualizowany ról systemu lokacji, które są zainstalowane na serwerze lokacji i tymi, które są automatycznie instalowane na komputerach zdalnych. Przed zainstalowaniem tej aktualizacji, należy się upewnić, że każdy serwer systemu lokacji spełnia ewentualne nowe wymagania wstępne dla operacji w nowej wersji aktualizacji.

**Konsole programu Configuration Manager:**   
Po raz pierwszy po zakończeniu aktualizacji za pomocą konsoli programu Configuration Manager będzie się monit o aktualizację tej konsoli. Aby to zrobić, należy uruchomić Instalatora programu Configuration Manager na komputerze, który jest hostem konsoli, a następnie wybierz opcję, aby zaktualizować konsolę. Zalecamy natychmiastowe instalowanie aktualizacji konsoli.



## <a name="checklist"></a>Lista kontrolna

**Upewnij się, że wszystkie lokacje z obsługiwaną wersją programu System Center Configuration Manager:** Przed rozpoczęciem instalacji aktualizacji 1610 każdej lokacji w hierarchii musi być uruchomiona tę samą wersję programu System Center Configuration Manager: danej wersji 1511, 1602 lub 1606.

**Sprawdź stan Software Assurance lub prawa równoważne subskrypcji:**   
Należy zainstalować aktualizację 1610 active umowę Software Assurance (SA). Po zainstalowaniu wersji 1610 opcję będzie mieć na **licencjonowania** kartę, aby potwierdzić swoje **Software Assurance Data wygaśnięcia**.

Jest to opcjonalna wartość, która można określić jako wygodny przypomnienie od daty wygaśnięcia licencji, która jest widoczna podczas instalowania przyszłych aktualizacji. Po zainstalowaniu programu Configuration Manager z nośnika linii bazowej wersji 1606 wcześniej określono tę wartość podczas instalacji lub na **licencjonowania** na karcie **ustawienia hierarchii** po zainstalowaniu lokacji.

Aby uzyskać więcej informacji, zobacz [licencjonowania i gałęzie dla programu System Center Configuration Manager](/sccm/core/understand/learn-more-editions).

**Przejrzyj zainstalowane wersje programu Microsoft .NET na serwerach systemu lokacji:** Podczas instalowania aktualizacji 1610 lokacji programu Configuration Manager automatycznie instaluje .NET Framework 4.5.2 na każdym komputerze, który obsługuje jedną z następujących ról systemu lokacji, gdy .NET Framework 4.5 lub nowszy nie jest już zainstalowany:

-   Punkt proxy rejestracji
-   Punkt rejestracji
-   Punkt zarządzania
-   Punkt połączenia usługi

Ta instalacja można umieścić serwer systemu lokacji w ponowne uruchomienie do czasu stanu i raportuj o błędach w podglądzie stanu składnika programu Configuration Manager. Ponadto aplikacji .NET na serwerze mogą wystąpić błędy losowe ponownego uruchomienia serwera.

Aby uzyskać więcej informacji, zobacz [Site and site system prerequisites](/sccm/core/plan-design/configs/site-and-site-system-prerequisites) (Wymagania wstępne dotyczące lokacji i systemu lokacji).

**Sprawdź stan lokacji i hierarchii, a następnie sprawdź, czy nie występują żadne nierozwiązane problemy:** Przed aktualizacją lokacji należy rozwiązać wszystkie problemy z działaniem serwera lokacji, serwera bazy danych lokacji i ról systemu lokacji, które są zainstalowane na komputerach zdalnych. Problemy z działaniem mogą spowodować niepowodzenie aktualizacji lokacji.

Aby uzyskać więcej informacji, zobacz [Korzystanie z alertów i systemu stanu w programie System Center Configuration Manager](/sccm/core/servers/manage/use-alerts-and-the-status-system).

**Sprawdź plik i dane replikacji między lokacjami:**   
Upewnij się, że plik i replikacji bazy danych między lokacjami jest bieżących i operacyjnej. Opóźnienia lub zaległości albo można zapobiec pomyślnym, płynnym aktualizacji.
W przypadku replikacji bazy danych można skorzystać z Analizatora linków replikacji ułatwiającego rozwiązywanie problemów przed rozpoczęciem aktualizacji.

Aby uzyskać więcej informacji, zobacz [o analizator łącza replikacji](/sccm/core/servers/manage/monitor-hierarchy-and-replication-infrastructure#BKMK_RLA) w [monitorowanie hierarchii i replikacji infrastruktury w programie System Center Configuration Manager](/sccm/core/servers/manage/monitor-hierarchy-and-replication-infrastructure) tematu.

**Zainstaluj wszystkie odpowiednie aktualizacje krytyczne systemów operacyjnych na komputerach hostujących lokację, serwer bazy danych lokacji i role zdalnego systemu lokacji:** Przed zainstalowaniem aktualizacji programu Configuration Manager, należy zainstalować wszystkie krytyczne aktualizacje dla każdego systemu uaktualnianej lokacji. Jeśli aktualizacja może wymagać ponownego uruchomienia odpowiednich komputerów przed rozpoczęciem aktualizacji programu Configuration Manager.

**Wyłącz repliki bazy danych dla punktów zarządzania w lokacjach głównych:**   
Program Configuration Manager pomyślnie nie można zaktualizować lokacji głównej, z repliką bazy danych dla punktów zarządzania włączone. Wyłącz replikację bazy danych przed:

-   Tworzenie kopii zapasowej bazy danych lokacji w celu sprawdzenia uaktualnienia bazy danych.
-   Instalowana aktualizacja dla programu Configuration Manager.

Aby uzyskać więcej informacji, zobacz [Repliki bazy danych dla punktów zarządzania programu System Center Configuration Manager](/sccm/core/servers/deploy/configure/database-replicas-for-management-points).

**Ustaw ręcznej pracy awaryjnej grup dostępności AlwaysOn programu SQL Server:**   
Przed zainstalowaniem aktualizacji, takich jak wersja 1610, upewnij się, że grupy dostępności jest ustawiona na ręcznej pracy awaryjnej. Po zaktualizowaniu witryny można przywrócić pracy awaryjnej automatycznego. Aby uzyskać więcej informacji, zobacz [AlwaysOn programu SQL Server dla bazy danych lokacji](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database).

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

**Utwórz kopię zapasową bazy danych lokacji w centralnej lokacji administracyjnej oraz lokacjach głównych:** Przed aktualizacją lokacji, należy utworzyć kopię zapasową bazy danych lokacji, sprawdź, czy została pomyślnie wykonana kopia zapasowa do użycia podczas odzyskiwania po awarii.

Aby uzyskać więcej informacji, zobacz [kopii zapasowych i odzyskiwania dla programu System Center Configuration Manager](/sccm/protect/understand/backup-and-recovery).

**Test uaktualnienia bazy danych na kopię najnowszej kopii zapasowej bazy danych lokacji:** Przed zaktualizowaniem witryny administracji centralnej programu System Center Configuration Manager lub lokacji głównej, testowanie procesu uaktualniania bazy danych lokacji na kopii bazy danych lokacji.

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
Aby zdefiniować okres, w którym można zainstalować aktualizacji na serwerze lokacji, można użyć usługi windows.

Może to ułatwić określenie, kiedy można zainstalować aktualizację w danej hierarchii. Przed wersją 1606 usługi systemu windows były nazywane okna obsługi. Aby uzyskać więcej informacji, zobacz [usługi systemu windows dla serwerów lokacji](/sccm/core/servers/manage/service-windows).

**Uruchom narzędzie sprawdzania wymagań wstępnych instalacji:**   
Gdy aktualizacja jest wyświetlana w konsoli jako **dostępne,** niezależnie uruchomieniem narzędzia sprawdzania wymagań wstępnych przed instalacją aktualizacji. (Po zainstalowaniu aktualizacji w witrynie Narzędzia sprawdzania wymagań wstępnych zostanie ponownie uruchomione.)

Aby uruchomić sprawdzanie wymagań wstępnych z konsoli, przejdź do **Administracja > Przegląd > usług w chmurze > aktualizacji i obsługi.** Obok, kliknij prawym przyciskiem myszy **pakiet aktualizacji programu Configuration Manager 1610**, a następnie wybierz **Uruchom sprawdzanie wymagań wstępnych**.

Aby uzyskać więcej informacji na temat uruchamiania i następnie monitorowania Sprawdzanie wymagań wstępnych, zobacz **krok 3: Uruchom narzędzie sprawdzania wymagań wstępnych przed zainstalowaniem aktualizacji** w temacie [zainstalować aktualizacji w konsoli programu System Center Configuration Manager](/sccm/core/servers/manage/install-in-console-updates).

> [!IMPORTANT]  
> Po uruchomieniu narzędzia sprawdzania wymagań wstępnych niezależnie lub w ramach instalacji aktualizacji proces aktualizacji niektórych plików źródłowych produktu, które są używane dla zadania obsługi lokacji. W związku z tym, po uruchomieniu narzędzia sprawdzania wymagań wstępnych, lecz przed instalacją aktualizacji 1610, jeśli konieczne jest wykonanie zadania konserwacji lokacji, uruchom **Setupwpf.exe** (Instalator programu Configuration Manager) z dysku CD. Najnowszy folder na serwerze lokacji.

**Aktualizacja witryny:**   
Teraz można przystąpić do rozpoczęcia instalacji aktualizacji dla hierarchii. Aby uzyskać więcej informacji o instalowaniu aktualizacji, zobacz [instalowanie aktualizacji w konsoli.](/sccm/core/servers/manage/install-in-console-updates#a-namebkmkinstalla-install-in-console-updates)

Zaleca się zaplanowanie instalacji aktualizacji poza godzinach pracy dla każdej lokacji podczas procesu instalowania aktualizacji i jego akcji ponownego zainstalowania składników lokacji i ról systemu lokacji ma co najmniej wpływ na operacje biznesowe.

Aby uzyskać więcej informacji, zobacz [Aktualizacje programu System Center Configuration Manager](/sccm/core/servers/manage/updates).

