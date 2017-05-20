---
title: "Lista kontrolna dotycząca 1606 | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat działania należy podjąć przed zaktualizowaniem z System Center Configuration Manager w wersji 1511 lub 1602 1606 wersji."
ms.custom: na
ms.date: 2/7/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 75652cd2-a95a-46c5-91c1-6d43fc8e787e
caps.latest.revision: 7
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 30af3326578d39c6d995672071705bcaeb877e4d
ms.openlocfilehash: b0def6eb962d243a7ea5910b8d56bbb448b3a2e4
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="checklist-for-installing-update-1606-for-system-center-configuration-manager"></a>Lista kontrolna instalowania aktualizacji 1606 dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Aktualizacja, która służy do aktualizacji z wersji 1511 lub 1602 jest wersja 1606 dla bieżącej gałęzi System Center Configuration Manager.

Przed zainstalowaniem wersji 1606 jako aktualizację, przejrzyj następujące informacje i Lista kontrolna dotycząca akcje do wykonania przed rozpoczęciem aktualizacji.

Informacje o wersjach linii bazowej, zobacz [linii bazowej i aktualizacji wersji](../../../core/servers/manage/updates.md#bkmk_Baselines) w [aktualizacji dla programu System Center Configuration Manager](../../../core/servers/manage/updates.md).

 ## <a name="about-installing-update-1606"></a>Informacje dotyczące instalowania aktualizacji 1606

Jako *aktualizacji*, 1606 można zainstalować tylko w lokacji najwyższego poziomu w hierarchii. Oznacza to, inicjuje instalację z witryny Administracja centralna, jeśli posiadasz lub autonomicznej lokacji głównej.  

-   Podrzędne Lokacje główne należy zainstalować aktualizację automatycznie po zakończeniu witryny Administracja centralna instalacji aktualizacji. Podczas instalowania aktualizacji lokacji, można użyć usługi systemu windows do formantu. Przed wersją 1606 usługi systemu windows były nazywane okna obsługi. Aby uzyskać więcej informacji, zobacz [usługi systemu windows dla serwerów lokacji](/sccm/core/servers/manage/service-windows).  

-   Po zakończeniu nadrzędnej lokacji głównej instalacji aktualizacji, należy ręcznie zaktualizować dodatkowej lokacji z konsoli programu Configuration Manager. Automatyczna aktualizacja serwerów lokacji dodatkowych nie jest obsługiwana.  

Podczas instalowania aktualizacji serwera lokacji ról systemu lokacji, które są zainstalowane na serwerze lokacji i tymi, które są zainstalowane na komputerach zdalnych zostanie automatycznie zaktualizowany. W związku z tym przed zainstalowaniem aktualizacji, upewnij się, że każdy serwer systemu lokacji spełnia ewentualne nowe wymagania wstępne dla operacji w nowej wersji aktualizacji.  

Po raz pierwszy po zainstalowaniu aktualizacji za pomocą konsoli programu Configuration Manager będzie się monit o aktualizację tej konsoli.  Aby to zrobić, należy uruchomić Instalatora programu Configuration Manager na komputerze, który jest hostem konsoli, a następnie wybierz opcję, aby zaktualizować konsolę. Zalecamy natychmiastowe instalowanie aktualizacji konsoli.

 **Znane problemy dotyczące tej aktualizacji**   
  Podczas wyświetlania stanu instalacji pakietu aktualizacji, stosuje się następujące problemy:
  - Podczas aktualizacji z wersji 1602 do 1606 kroku **ładunku pakietu aktualizacji wyodrębniania** ma stan **nie uruchomiono**, nawet jeśli został pobrany.
  - Podczas aktualizacji z wersji 1511 do 1606, niektóre kroki będzie wyświetlany stan **Ukończono** , ale nie będzie wyświetlana wartość dla **godziny ostatniej aktualizacji**.


## <a name="checklist"></a>Lista kontrolna  

 **Upewnij się, że wszystkie lokacje z obsługiwaną wersją programu System Center Configuration Manager:**  Przed rozpoczęciem instalacji aktualizacji 1606 każdy serwer lokacji w hierarchii musi mieć tę samą wersję programu System Center Configuration Manager: danej wersji 1511 lub 1602.

 **Przejrzyj zainstalowane wersje Microsoft.NET na serwerach systemu lokacji:** Podczas instalowania aktualizacji 1606 lokacji, Configuration Manager automatycznie zainstaluje .NET Framework 4.5.2 na każdym komputerze, który obsługuje jeden z następujących ról systemu lokacji (Jeśli nie zainstalowano jeszcze .NET Framework 4.5 lub nowszy):  

-   Punkt proxy rejestracji  

-   Punkt rejestracji  

-   Punkt zarządzania  

-   Punkt połączenia usługi  

Ta instalacja można umieścić serwer systemu lokacji w ponowne uruchomienie do czasu stanu i raportuj o błędach w podglądzie stanu składnika programu Configuration Manager. Ponadto mogą losowo występować usterki aplikacji .NET na serwerze do momentu ponownego uruchomienia serwera.  

 Aby uzyskać więcej informacji, zobacz [lokacji i wymagań wstępnych systemu lokacji](../../../core/plan-design/configs/site-and-site-system-prerequisites.md).  

 **Sprawdź stan lokacji i hierarchii, a następnie sprawdź, czy nie występują żadne nierozwiązane problemy:** Przed aktualizacją lokacji należy rozwiązać wszystkie problemy z działaniem serwera lokacji, serwera bazy danych lokacji i ról systemu lokacji, które są zainstalowane na komputerach zdalnych. Problemy z działaniem mogą spowodować niepowodzenie aktualizacji lokacji.

 Aby uzyskać więcej informacji, zobacz [Korzystanie z alertów i systemu stanu w programie System Center Configuration Manager](../../../core/servers/manage/use-alerts-and-the-status-system.md).  

 **Sprawdź plik i dane replikacji między lokacjami:**  Upewnij się, że plik i replikacji bazy danych między lokacjami jest bieżących i operacyjnej. Opóźnienia lub zaległości albo można zapobiec pomyślnym, płynnym aktualizacji.    

W przypadku replikacji bazy danych można skorzystać z Analizatora linków replikacji ułatwiającego rozwiązywanie problemów przed rozpoczęciem aktualizacji. Aby uzyskać więcej informacji, zobacz [o analizator łącza replikacji](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_RLA) w temacie [monitorowanie hierarchii i replikacji infrastruktury w programie System Center Configuration Manager](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md).  

 **Zainstaluj wszystkie odpowiednie aktualizacje krytyczne systemów operacyjnych na komputerach hostujących lokację, serwer bazy danych lokacji i role zdalnego systemu lokacji:** Przed zainstalowaniem aktualizacji programu Configuration Manager, należy zainstalować wszystkie krytyczne aktualizacje dla każdego systemu uaktualnianej lokacji. Instalowana aktualizacja może wymagać ponownego uruchomienia odpowiednich komputerów przed rozpoczęciem uaktualniania.  

 **Wyłącz repliki bazy danych dla punktów zarządzania w lokacjach głównych:** Program Configuration Manager pomyślnie nie można zaktualizować lokacji głównej, z repliką bazy danych dla punktów zarządzania włączone. Wyłącz replikację bazy danych przed:  

-   Tworzenie kopii zapasowej bazy danych lokacji w celu sprawdzenia uaktualnienia bazy danych.  

-   Instalowana aktualizacja dla programu Configuration Manager.  

Aby uzyskać więcej informacji, zobacz [bazy danych repliki dla punktów zarządzania programu System Center Configuration Manager](../../../core/servers/deploy/configure/database-replicas-for-management-points.md).  

 **Ustaw ręcznej pracy awaryjnej grup dostępności AlwaysOn programu SQL Server:**  
 Przed zainstalowaniem aktualizacji, takich jak wersja 1606, upewnij się, że grupy dostępności jest ustawiona na ręcznej pracy awaryjnej. Po zaktualizowaniu witryny można przywrócić pracy awaryjnej automatycznego. Aby uzyskać więcej informacji, zobacz [AlwaysOn programu SQL Server dla bazy danych lokacji](../../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md).

 **Skonfiguruj ponownie punkty aktualizacji oprogramowania, które korzystają z usługi równoważenia obciążenia sieciowego:** Menedżer konfiguracji nie może zaktualizować lokacji przy użyciu klastra równoważenia obciążenia sieciowego (NLB), punkty aktualizacji oprogramowania hosta.  

Użycie klastrów równoważenia obciążenia Sieciowego dla punktów aktualizacji oprogramowania, należy użyć programu Windows PowerShell do usunięcia klastra równoważenia obciążenia Sieciowego.    

 Aby uzyskać więcej informacji, zobacz [Planowanie aktualizacji oprogramowania w programie System Center Configuration Manager](../../../sum/plan-design/plan-for-software-updates.md).  

 **Wyłącz wszystkie zadania obsługi lokacji w każdej lokacji na czas instalacji aktualizacji w tej witrynie:** Przed zainstalowaniem tej aktualizacji należy wyłączyć wszystkie zadania konserwacji lokacji, które mogą być uruchamiane w czasie procesu aktualizacji jest aktywny. Dotyczy to m.in. następujących zadań:  

-   Wykonaj kopię zapasową serwera lokacji  

-   Usuń przedawnione operacje klienta  

-   Usuń przedawnione dane odnajdywania  

Instalowanie aktualizacji może zakończyć się niepowodzeniem, jeżeli w czasie jego trwania zostanie uruchomione zadanie konserwacji bazy danych lokacji. Przed wyłączeniem zadania Zarejestruj jego harmonogram zadań, aby przywrócić jego konfigurację po zainstalowaniu aktualizacji.  

Aby uzyskać więcej informacji, zobacz [zadania konserwacji programu System Center Configuration Manager](../../../core/servers/manage/maintenance-tasks.md) i [odwołania do obsługi zadań programu System Center Configuration Manager](../../../core/servers/manage/reference-for-maintenance-tasks.md).  

 **Utwórz kopię zapasową bazy danych lokacji w centralnej lokacji administracyjnej oraz lokacjach głównych:** Przed aktualizacją lokacji, należy utworzyć kopię zapasową bazy danych lokacji, sprawdź, czy została pomyślnie wykonana kopia zapasowa do użycia podczas odzyskiwania po awarii.   

Aby uzyskać więcej informacji, zobacz [kopii zapasowych i odzyskiwania dla programu System Center Configuration Manager](../../../protect/understand/backup-and-recovery.md).  


 **Test uaktualnienia bazy danych na kopię najnowszej kopii zapasowej bazy danych lokacji:** Przed zaktualizowaniem witryny administracji centralnej programu System Center Configuration Manager lub lokacji głównej, testowanie procesu uaktualniania bazy danych lokacji na kopii bazy danych lokacji.  

-   Proces uaktualniania bazy danych lokacji należy przetestować, gdyż podczas uaktualniania lokacji może zmodyfikować bazy danych lokacji.  

-   Testowego uaktualnienia bazy danych nie jest wymagane, jednak można zidentyfikować problemy związane z uaktualnieniem przed sieci produkcyjnej bazy danych.  

-   Nieudane uaktualnienie bazy danych lokacji może uniemożliwić korzystanie z bazy danych lokacji i wymóc przeprowadzenie odzyskiwania lokacji w celu przywrócenia jej funkcjonalności.  

-   Mimo że bazy danych lokacji jest udostępniana między lokacjami w hierarchii, zaplanować testowanie bazy danych w każdej uaktualnianej lokacji przed uaktualnieniem tej lokacji.  

-   Jeśli są używane repliki bazy danych dla punktów zarządzania w lokacji głównej, przed utworzeniem kopii zapasowej bazy danych lokacji należy wyłączyć replikację.  

Menedżer konfiguracji nie obsługuje kopii zapasowych lokacji dodatkowych ani nie obsługuje testowego uaktualnienia bazy danych lokacji dodatkowej.   

Nie uruchamiaj testowego uaktualnienia bazy danych na produkcyjną bazę danych lokacji. Wykonanie tej czynności powoduje zaktualizowanie bazy danych lokacji, przez co lokacja może przestać działać. Aby uzyskać więcej informacji, aby uzyskać więcej informacji, zobacz [krok 2: Test uaktualnienia bazy danych przed zainstalowaniem aktualizacji](/sccm/core/servers/manage/install-in-console-updates#bkmk_step2) z **przed zainstalowaniem aktualizacji w konsoli**.

 **Planowanie pilotażowe klienta:** Po zainstalowaniu aktualizacji, która aktualizuje klienta przed wdraża i uaktualnia wszystkich aktywnych klientów można przetestować tej nowej aktualizacji klienta w produkcji wstępnej.   

 Aby móc korzystać z tej opcji, przed rozpoczęciem instalacji aktualizacji, należy skonfigurować lokację do obsługi automatycznych uaktualnień do produkcji wstępnej. Aby uzyskać więcej informacji, zobacz [Uaktualnianie klientów w programie System Center Configuration Manager](../../../core/clients/manage/upgrade/upgrade-clients.md) i   
[Jak przetestować uaktualnienia klienta w kolekcji przedprodukcyjnej w programie System Center Configuration Manager](../../../core/clients/manage/upgrade/test-client-upgrades.md).  

 **Planowanie pod kątem używania usługi systemu windows do sterowania podczas aktualizacji serwerów lokacji:** Aby zdefiniować okres, w którym można zainstalować aktualizacji na serwerze lokacji, można użyć usługi windows.

Może to ułatwić określenie, kiedy można zainstalować aktualizację w danej hierarchii.
Przed wersją 1606 usługi systemu windows były nazywane okna obsługi. Aby uzyskać więcej informacji, zobacz [usługi systemu windows dla serwerów lokacji](/sccm/core/servers/manage/service-windows).  

 **Uruchom narzędzie sprawdzania wymagań wstępnych instalacji:**  Przed zainstalowaniem aktualizacji 1606, należy uruchomić narzędzie sprawdzania wymagań wstępnych niezależnie od instalacji aktualizacji. Po zainstalowaniu aktualizacji w witrynie Narzędzia sprawdzania wymagań wstępnych zostanie ponownie uruchomione.  

Aby uzyskać więcej informacji, zobacz **krok 3: Uruchom narzędzie sprawdzania wymagań wstępnych przed zainstalowaniem aktualizacji** w [aktualizacji dla programu System Center Configuration Manager](../../../core/servers/manage/install-in-console-updates.md) tematu.  

> [!IMPORTANT]  
>  Po uruchomieniu narzędzia sprawdzania wymagań wstępnych niezależnie lub w ramach instalacji aktualizacji proces aktualizacji niektórych plików źródłowych produktu, które są używane dla zadania obsługi lokacji. W związku z tym, po uruchomieniu narzędzia sprawdzania wymagań wstępnych, lecz przed instalacją aktualizacji 1606, jeśli konieczne jest wykonanie zadania konserwacji lokacji, uruchom **Setupwpf.exe** (Instalator programu Configuration Manager) z dysku CD. Najnowszy folder na serwerze lokacji.  

 **Aktualizacja witryny:** Teraz można przystąpić do rozpoczęcia instalacji aktualizacji dla hierarchii.  
  Zaleca się zaplanowanie instalacji aktualizacji poza godzinach pracy dla każdej lokacji podczas procesu instalowania aktualizacji i jego akcji ponownego zainstalowania składników lokacji i ról systemu lokacji ma co najmniej wpływ na operacje biznesowe.

Aby uzyskać więcej informacji, zobacz [Aktualizacje programu System Center Configuration Manager](../../../core/servers/manage/updates.md).  

