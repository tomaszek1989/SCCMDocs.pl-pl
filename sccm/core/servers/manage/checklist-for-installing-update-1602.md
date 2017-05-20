---
title: "Lista kontrolna dotycząca 1602 | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat działania należy podjąć przed zaktualizowaniem z System Center Configuration Manager w wersji 1511 do wersji 1602."
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b63ef197-01f0-4894-b929-5ef8403c5195
caps.latest.revision: 13
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 3e0de56b7a592b105e6a61b3d6654b1d0142584d
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="checklist-for-installing-update-1602-for-system-center-configuration-manager"></a>Lista kontrolna instalowania aktualizacji 1602 dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Przed aktualizacją z System Center Configuration Manager w wersji 1511 do wersji 1602, przejrzyj następujące informacje i Lista kontrolna dotycząca akcje do wykonania przed rozpoczęciem aktualizacji.  

 **Informacje dotyczące instalowania aktualizacji 1602:**  

 Aktualizację 1602 można zainstalować tylko w lokacji najwyższego poziomu w hierarchii. Oznacza to, inicjuje instalację z witryny Administracja centralna, jeśli posiadasz lub autonomicznej lokacji głównej.  

-   Podrzędne Lokacje główne należy zainstalować aktualizację automatycznie po zakończeniu witryny Administracja centralna instalacji aktualizacji. Okien obsługi do ustalania można użyć podczas instalowania aktualizacji lokacji. Począwszy od wersji aktualizacji 1602 okna obsługi zmieniono *usługi systemu windows*. Aby uzyskać więcej informacji, zobacz [usługi systemu windows dla serwerów lokacji](/sccm/core/servers/manage/service-windows).  

-   Po zakończeniu nadrzędnej lokacji głównej instalacji aktualizacji, należy ręcznie zaktualizować dodatkowej lokacji z konsoli programu Configuration Manager. Automatyczne aktualizacje serwerów lokacji dodatkowej nie są obsługiwane.  

Podczas instalowania aktualizacji serwera lokacji zostanie zaktualizowany ról systemu lokacji, które są zainstalowane na serwerze lokacji i tymi, które są automatycznie instalowane na komputerach zdalnych. W związku z tym przed zainstalowaniem aktualizacji, upewnij się, że każdy serwer systemu lokacji spełnia ewentualne nowe wymagania wstępne dla operacji w nowej wersji aktualizacji.  

Po raz pierwszy po zakończeniu aktualizacji za pomocą konsoli programu Configuration Manager będzie się monit o aktualizację tej konsoli. Aby to zrobić, należy uruchomić Instalatora programu Configuration Manager na komputerze, który jest hostem konsoli i wybierz opcję, aby zaktualizować konsolę. Zalecamy natychmiastowe instalowanie aktualizacji konsoli.  

 **Lista kontrolna:**  

 **Upewnij się, że wszystkie lokacje z obsługiwaną wersją programu System Center Configuration Manager:**  Każdy serwer lokacji w hierarchii, należy uruchomić System Center Configuration Manager w wersji 1511 przed rozpoczęciem instalacji aktualizacji 1602.  

 **Przejrzyj zainstalowane wersje programu Microsoft .NET na serwerach systemu lokacji:** Podczas instalowania aktualizacji 1602 lokacji, Configuration Manager automatycznie zainstaluje .NET Framework 4.5.2 na każdym komputerze, który obsługuje jeden z następujących ról systemu lokacji (Jeśli nie zainstalowano jeszcze .NET Framework 4.5 lub nowszy):  

-   Punkt proxy rejestracji  

-   Punkt rejestracji  

-   Punkt zarządzania  

-   Punkt połączenia usługi  

Ta instalacja można umieścić serwer systemu lokacji w ponowne uruchomienie do czasu stanu i raportowanie błędów do podglądu stan składnika programu Configuration Manager. Ponadto aplikacje .NET na serwerze mogą wystąpić błędy losowe do momentu ponownego uruchomienia serwera.  

 Aby uzyskać więcej informacji, zobacz [Site and site system prerequisites](../../../core/plan-design/configs/site-and-site-system-prerequisites.md) (Wymagania wstępne dotyczące lokacji i systemu lokacji).  

 **Sprawdź stan lokacji i hierarchii, a następnie sprawdź, czy nie występują żadne nierozwiązane problemy:** Przed aktualizacją lokacji należy rozwiązać wszystkie problemy z działaniem serwera lokacji, serwera bazy danych lokacji i ról systemu lokacji, które są zainstalowane na komputerach zdalnych. Problemy z działaniem mogą spowodować niepowodzenie aktualizacji lokacji.  

Aby uzyskać więcej informacji, zobacz [Korzystanie z alertów i systemu stanu w programie System Center Configuration Manager](../../../core/servers/manage/use-alerts-and-the-status-system.md).  

 **Sprawdź plik i dane replikacji między lokacjami:**  Upewnij się, że plik i replikacji bazy danych między lokacjami jest bieżących i operacyjnej. Opóźnienia lub zaległości albo można zapobiec pomyślnym, płynnym aktualizacji.    

W przypadku replikacji bazy danych można skorzystać z Analizatora linków replikacji ułatwiającego rozwiązywanie problemów przed rozpoczęciem aktualizacji.    

 Aby uzyskać więcej informacji, zobacz [o analizator łącza replikacji](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_RLA) w [monitorowanie hierarchii i replikacji infrastruktury w programie System Center Configuration Manager](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md) tematu.  

 **Zainstaluj wszystkie odpowiednie aktualizacje krytyczne systemów operacyjnych na komputerach hostujących lokację, serwer bazy danych lokacji i role zdalnego systemu lokacji:** Przed zainstalowaniem aktualizacji programu Configuration Manager, należy zainstalować wszystkie krytyczne aktualizacje dla każdego systemu uaktualnianej lokacji. Instalowana aktualizacja może wymagać ponownego uruchomienia odpowiednich komputerów przed rozpoczęciem uaktualniania.  

 **Wyłącz repliki bazy danych dla punktów zarządzania w lokacjach głównych:** Program Configuration Manager pomyślnie nie można zaktualizować lokacji głównej, z repliką bazy danych dla punktów zarządzania włączone. Wyłącz replikację bazy danych przed:  

-   Tworzenie kopii zapasowej bazy danych lokacji w celu sprawdzenia uaktualnienia bazy danych.  

-   Instalowana aktualizacja dla programu Configuration Manager.  

Aby uzyskać więcej informacji, zobacz [bazy danych repliki dla punktów zarządzania programu System Center Configuration Manager](../../../core/servers/deploy/configure/database-replicas-for-management-points.md).  

 **Skonfiguruj ponownie punkty aktualizacji oprogramowania, które korzystają z usługi równoważenia obciążenia sieciowego:** Menedżer konfiguracji nie może zaktualizować lokacji przy użyciu klastra równoważenia obciążenia sieciowego (NLB), punkty aktualizacji oprogramowania hosta.  Użycie klastrów równoważenia obciążenia Sieciowego dla punktów aktualizacji oprogramowania, należy użyć programu Windows PowerShell do usunięcia klastra równoważenia obciążenia Sieciowego.    

 Aby uzyskać więcej informacji, zobacz [Planowanie aktualizacji oprogramowania w programie System Center Configuration Manager](../../../sum/plan-design/plan-for-software-updates.md).  

 **Wyłącz wszystkie zadania obsługi lokacji w każdej lokacji na czas instalacji aktualizacji w tej witrynie:** Przed zainstalowaniem aktualizacji, należy wyłączyć wszystkie zadania obsługi, które mogą zostać uruchomione w czasie, gdy proces aktualizacji jest aktywny. Te zadania obejmują (ale nie wyłącznie) do następującego:  

-   Wykonaj kopię zapasową serwera lokacji  

-   Usuń przedawnione operacje klienta  

-   Usuń przedawnione dane odnajdywania  

Instalowanie aktualizacji może zakończyć się niepowodzeniem, jeżeli w czasie jego trwania zostanie uruchomione zadanie konserwacji bazy danych lokacji. Przed wyłączeniem zadania zarejestruj jego harmonogram, aby przywrócić jego konfigurację po ukończeniu instalowania aktualizacji.  

 Aby uzyskać więcej informacji, zobacz [zadania konserwacji programu System Center Configuration Manager](../../../core/servers/manage/maintenance-tasks.md) i [odwołania do obsługi zadań programu System Center Configuration Manager](../../../core/servers/manage/reference-for-maintenance-tasks.md).  

 **Utwórz kopię zapasową bazy danych lokacji w centralnej lokacji administracyjnej oraz lokacjach głównych:** Przed aktualizacją lokacji, należy wykonać kopię zapasową bazy danych lokacji, sprawdź, czy została pomyślnie wykonana kopia zapasowa do użycia podczas odzyskiwania po awarii.   

Aby uzyskać więcej informacji, zobacz [kopii zapasowych i odzyskiwania dla programu System Center Configuration Manager](../../../protect/understand/backup-and-recovery.md).  

 **Kopii zapasowej dostosowanych plików Configuration.mof:** Jeśli używasz dostosowanych plików Configuration.mof do definiowania klas danych, korzystających z spisu sprzętu, należy utworzyć kopię zapasową tego pliku przed aktualizacją lokacji. Po zainstalowaniu aktualizacji należy przywrócić ten plik do witryny 1602 wersji. Po zaktualizowaniu witryny bieżący plik został zastąpiony oryginalnej wersji pliku (domyślnie). Aby uzyskać więcej informacji o korzystaniu z tego pliku, zobacz [sposobach rozszerzania zapasów sprzętu w programie System Center Configuration Manager](../../../core/clients/manage/inventory/extend-hardware-inventory.md).  

 **Test uaktualnienia bazy danych na kopię najnowszej kopii zapasowej bazy danych lokacji:** Przed zaktualizowaniem witryny administracji centralnej programu System Center Configuration Manager lub lokacji głównej, testowanie procesu uaktualniania bazy danych lokacji na kopii bazy danych lokacji.  

-   Proces uaktualniania bazy danych lokacji należy przetestować, gdyż podczas uaktualniania lokacji może zmodyfikować bazy danych lokacji.  

-   Testowego uaktualnienia bazy danych nie jest wymagane, jednak można zidentyfikować problemy związane z uaktualnieniem przed sieci produkcyjnej bazy danych.  

-   Nieudane uaktualnienie bazy danych lokacji może uniemożliwić korzystanie z bazy danych lokacji i wymóc przeprowadzenie odzyskiwania lokacji w celu przywrócenia jej funkcjonalności.  

-   Choć bazy danych lokacji jest udostępniana między lokacjami w hierarchii, należy zaplanować testowanie bazy danych w każdej uaktualnianej lokacji, przed uaktualnieniem tej lokacji.  

-   Jeśli są używane repliki bazy danych dla punktów zarządzania w lokacji głównej, przed utworzeniem kopii zapasowej bazy danych lokacji należy wyłączyć replikację.  

Menedżer konfiguracji nie obsługuje kopii zapasowych lokacji dodatkowych ani nie obsługuje testowego uaktualnienia bazy danych lokacji dodatkowej.   
Nie uruchamiaj testowego uaktualnienia bazy danych na produkcyjną bazę danych lokacji. Wykonanie tej czynności powoduje zaktualizowanie bazy danych lokacji, przez co lokacja może przestać działać. Aby uzyskać więcej informacji, zobacz [krok 2: Test uaktualnienia bazy danych przed zainstalowaniem aktualizacji](/sccm/core/servers/manage/install-in-console-updates#bkmk_step2) z **przed zainstalowaniem aktualizacji w konsoli**.  

 **Planowanie pilotażowe klienta:** Po zainstalowaniu aktualizacji, która aktualizuje klienta przed wdraża i uaktualnia wszystkich aktywnych klientów można przetestować tej nowej aktualizacji klienta w produkcji wstępnej.   

 Aby skorzystać z tej opcji, należy skonfigurować lokację do obsługi automatycznych uaktualnień do produkcji wstępnej, przed rozpoczęciem instalacji aktualizacji. Aby uzyskać więcej informacji, zobacz [Uaktualnianie klientów w programie System Center Configuration Manager](../../../core/clients/manage/upgrade/upgrade-clients.md) i   
[Jak przetestować uaktualnienia klienta w kolekcji przedprodukcyjnej w programie System Center Configuration Manager](../../../core/clients/manage/upgrade/test-client-upgrades.md).  

 **Planowane jest używanie okien obsługi do ustalania, serwerach lokacji instalowania aktualizacji:** Konserwacja systemu windows umożliwia definiowanie pewien czas, w którym można zainstalować aktualizacji na serwerze lokacji. Może to ułatwić określenie, kiedy można zainstalować aktualizację w danej hierarchii.   

Począwszy od wersji aktualizacji 1602 okna obsługi zmieniono *usługi systemu windows*. Aby uzyskać więcej informacji, zobacz [usługi systemu windows dla serwerów lokacji](/sccm/core/servers/manage/service-windows).  

 **Uruchom narzędzie sprawdzania wymagań wstępnych instalacji:**  Przed zainstalowaniem aktualizacji 1602, należy uruchomić narzędzie sprawdzania wymagań wstępnych niezależnie od instalacji aktualizacji. Po zainstalowaniu aktualizacji w witrynie Narzędzia sprawdzania wymagań wstępnych zostanie ponownie uruchomione.  

Aby uzyskać więcej informacji, zobacz **krok 3: Uruchom narzędzie sprawdzania wymagań wstępnych przed zainstalowaniem aktualizacji** w [aktualizacji dla programu System Center Configuration Manager](../../../core/servers/manage/updates.md) tematu.  

> [!IMPORTANT]  
>  Po uruchomieniu narzędzia sprawdzania wymagań wstępnych niezależnie lub w ramach instalacji aktualizacji proces aktualizacji niektórych plików źródłowych produktu, które są używane dla zadania obsługi lokacji. W związku z tym, po uruchomieniu narzędzia sprawdzania wymagań wstępnych, lecz przed zainstalowaniem aktualizacji 1602, jeśli konieczne jest wykonanie zadania konserwacji lokacji, uruchom **Setupwfe.exe** (Instalator programu Configuration Manager) z dysku CD. Najnowszy folder na serwerze lokacji.  

 **Aktualizacja witryny:** Teraz można przystąpić do rozpoczęcia instalacji aktualizacji dla hierarchii. Zaleca się zaplanowanie instalacji aktualizacji poza godzinach pracy dla każdej lokacji podczas procesu instalowania aktualizacji i jego akcji ponownego zainstalowania składników lokacji i ról systemu lokacji ma co najmniej wpływ na operacje biznesowe.

Aby uzyskać więcej informacji, zobacz [Aktualizacje programu System Center Configuration Manager](../../../core/servers/manage/updates.md).  

## <a name="see-also"></a>Zobacz także  
 [Aktualizacje programu System Center Configuration Manager](../../../core/servers/manage/updates.md)

