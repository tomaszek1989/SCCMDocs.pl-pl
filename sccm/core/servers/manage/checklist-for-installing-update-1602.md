---
title: "Lista kontrolna dotycząca 1602"
titleSuffix: Configuration Manager
description: "Więcej informacji na temat działania należy podjąć przed zaktualizowaniem programu System Center Configuration Manager w wersji 1511 do wersji 1602."
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b63ef197-01f0-4894-b929-5ef8403c5195
caps.latest.revision: "13"
author: mestew
ms.author: mstewart
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.openlocfilehash: 6c13a6b2d1413788cef2796af322a777b2a4682c
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2017
---
# <a name="checklist-for-installing-update-1602-for-system-center-configuration-manager"></a>Lista kontrolna instalowania aktualizacji 1602 dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Przed zaktualizowaniem programu System Center Configuration Manager w wersji 1511 do wersji 1602, przejrzyj następujące informacje i listy kontrolnej czynności należy wykonać przed rozpoczęciem aktualizacji.  

 **Informacje dotyczące instalowania aktualizacji 1602:**  

 Aktualizację 1602 można zainstalować tylko w lokacji najwyższego poziomu w hierarchii. Oznacza to, należy zainicjować instalację, z witryny Administracja centralna, jeśli masz lub autonomicznej lokacji głównej.  

-   Podrzędne Lokacje główne instalują aktualizację automatycznie po zakończeniu centralnej lokacji administracyjnej, instalowania aktualizacji. Okien obsługi do ustalania można użyć podczas instalowania aktualizacji w lokacji. Począwszy od wersji aktualizacji 1602 okna obsługi zmieniono *usługi systemu windows*. Aby uzyskać więcej informacji, zobacz [usługi systemu windows dla serwerów lokacji](/sccm/core/servers/manage/service-windows).  

-   Należy ręcznie zaktualizować Lokacje dodatkowe przy użyciu konsoli programu Configuration Manager po zakończeniu nadrzędną lokację główną, instalowania aktualizacji. Automatyczne aktualizacje serwerów lokacji dodatkowych nie są obsługiwane.  

Serwer lokacji instaluje aktualizację, Pobierz zaktualizowany role systemu lokacji, które są zainstalowane na serwerze lokacji oraz te, które są instalowane automatycznie na komputerach zdalnych. W związku z tym przed zainstalowaniem aktualizacji, upewnij się, że każdy serwer systemu lokacji spełnia ewentualne nowe wymagania wstępne dla operacji przy użyciu nowej wersji aktualizacji.  

Użycie konsoli programu Configuration Manager po zakończeniu aktualizacji po raz pierwszy pojawi się monit zaktualizowanie tej konsoli. Aby to zrobić, należy uruchomić Instalatora programu Configuration Manager na komputerze, który jest hostem konsoli i wybierz opcję, aby zaktualizować konsolę. Zalecamy natychmiastowe instalowanie aktualizacji konsoli.  

 **Lista kontrolna:**  

 **Upewnij się, że we wszystkich lokacjach uruchomiona obsługiwana wersja programu System Center Configuration Manager:**  Każdy serwer lokacji w hierarchii należy uruchomić System Center Configuration Manager w wersji 1511 przed rozpoczęciem instalowania aktualizacji 1602.  

 **Przejrzyj wersje programu .NET firmy Microsoft są zainstalowane na serwerach systemu lokacji:** Podczas instalowania aktualizacji 1602 lokacji programu Configuration Manager automatycznie instaluje .NET Framework 4.5.2 na każdym komputerze hostującym jedną z następujących ról systemu lokacji (Jeśli nie zainstalowano jeszcze .NET Framework 4.5 lub nowszej):  

-   Punkt proxy rejestracji  

-   Punkt rejestracji  

-   Punkt zarządzania  

-   Punkt połączenia usługi  

Ta instalacja można umieścić serwer systemu lokacji do na ponowne uruchomienie do czasu stanu i błędów raport w przeglądarce stanu składników programu Configuration Manager. Ponadto aplikacji .NET na serwerze mogą wystąpić błędy losowe do ponownego uruchomienia serwera.  

 Aby uzyskać więcej informacji, zobacz [Site and site system prerequisites](../../../core/plan-design/configs/site-and-site-system-prerequisites.md) (Wymagania wstępne dotyczące lokacji i systemu lokacji).  

 **Sprawdź stan lokacji i hierarchii, a następnie sprawdź, czy nie występują żadne nierozwiązane problemy:** Przed uaktualnieniem lokacji należy rozwiązać wszystkie problemy z działaniem serwera lokacji, serwera bazy danych lokacji i ról systemu lokacji, które są zainstalowane na komputerach zdalnych. Problemy z działaniem mogą spowodować niepowodzenie aktualizacji lokacji.  

Aby uzyskać więcej informacji, zobacz [Korzystanie z alertów i systemu stanu w programie System Center Configuration Manager](../../../core/servers/manage/use-alerts-and-the-status-system.md).  

 **Przejrzyj replikację plików i danych między lokacjami:**  Upewnij się, że plik i replikacji bazy danych między lokacjami jest operacyjne i bieżący. Opóźnień lub zaległości może uniemożliwić smooth aktualizacji powiodło się.    

W przypadku replikacji bazy danych można skorzystać z Analizatora linków replikacji ułatwiającego rozwiązywanie problemów przed rozpoczęciem aktualizacji.    

 Aby uzyskać więcej informacji, zobacz [o analizator łącza replikacji](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_RLA) w [Monitorowanie infrastruktury hierarchii i replikacji w programie System Center Configuration Manager](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md) tematu.  

 **Zainstaluj wszystkie odpowiednie aktualizacje krytyczne dla systemów operacyjnych na komputerach hostujących lokację, serwer bazy danych lokacji i role zdalnego systemu lokacji:** Przed zainstalowaniem aktualizacji programu Configuration Manager, należy zainstalować wszystkie aktualizacje krytyczne dla odpowiednich systemów lokacji. Instalowana aktualizacja może wymagać ponownego uruchomienia odpowiednich komputerów przed rozpoczęciem uaktualniania.  

 **Wyłącz repliki bazy danych dla punktów zarządzania w lokacjach głównych:** Menedżer konfiguracji nie może pomyślnie zaktualizować lokacji głównej, z repliki bazy danych dla punktów zarządzania włączone. Wyłącz replikację bazy danych przed:  

-   Tworzenie kopii zapasowej bazy danych lokacji w celu sprawdzenia uaktualnienia bazy danych.  

-   Instalowanie aktualizacji programu Configuration Manager.  

Aby uzyskać więcej informacji, zobacz [replik bazy danych dla punktów zarządzania programu System Center Configuration Manager](../../../core/servers/deploy/configure/database-replicas-for-management-points.md).  

 **Skonfiguruj ponownie punkty aktualizacji oprogramowania, które używają usługi równoważenia obciążenia sieciowego:** Menedżer konfiguracji nie może zaktualizować lokacji korzystającej z klastra równoważenia obciążenia sieciowego (NLB), punkty aktualizacji oprogramowania.  Korzystając z klastrami równoważenia obciążenia Sieciowego dla punktów aktualizacji oprogramowania, należy usunąć klaster równoważenia obciążenia Sieciowego za pomocą programu Windows PowerShell.    

 Aby uzyskać więcej informacji, zobacz [Planowanie aktualizacji oprogramowania w programie System Center Configuration Manager](../../../sum/plan-design/plan-for-software-updates.md).  

 **Wyłącz wszystkie zadania konserwacji lokacji w każdej lokacji w czasie trwania instalacji aktualizacji w tej witrynie:** Przed zainstalowaniem aktualizacji Wyłącz wszystkie zadania konserwacji lokacji, które mogą zostać uruchomione w czasie, gdy proces aktualizacji jest aktywny. Te zadania obejmują (ale nie są ograniczone) do następującego:  

-   Wykonaj kopię zapasową serwera lokacji  

-   Usuń przedawnione operacje klienta  

-   Usuń przedawnione dane odnajdywania  

Instalowanie aktualizacji może zakończyć się niepowodzeniem, jeżeli w czasie jego trwania zostanie uruchomione zadanie konserwacji bazy danych lokacji. Przed wyłączeniem zadania zarejestruj jego harmonogram, aby przywrócić jego konfigurację po ukończeniu instalowania aktualizacji.  

 Aby uzyskać więcej informacji, zobacz [zadania konserwacji programu System Center Configuration Manager](../../../core/servers/manage/maintenance-tasks.md) i [odwołania do obsługi zadań programu System Center Configuration Manager](../../../core/servers/manage/reference-for-maintenance-tasks.md).  

 **Utwórz kopię zapasową bazy danych lokacji w centralnej lokacji administracyjnej i lokacjach głównych:** Przed uaktualnieniem lokacji należy utworzyć kopię zapasową bazy danych lokacji, aby upewnić się, że masz pomyślnego tworzenia kopii zapasowej do użycia podczas odzyskiwania po awarii.   

Aby uzyskać więcej informacji, zobacz [kopii zapasowych i odzyskiwania dla programu System Center Configuration Manager](../../../protect/understand/backup-and-recovery.md).  

 **Wykonaj kopię zapasową dostosowanego pliku Configuration.mof:** Jeśli dostosowany plik Configuration.mof umożliwia definiowanie klas danych, które używanych w spisie sprzętu, Utwórz kopię zapasową tego pliku przed zaktualizowaniem lokacji. Po aktualizacji Przywróć ten plik do witryny w wersji 1602. Podczas aktualizowania lokacji bieżący plik jest zastępowany oryginalną wersją (ustawienie domyślne) w pliku. Aby uzyskać więcej informacji na temat korzystania z tego pliku, zobacz [jak rozszerzyć spis sprzętu w programie System Center Configuration Manager](../../../core/clients/manage/inventory/extend-hardware-inventory.md).  

 **Test uaktualnienia bazy danych na kopii najnowszej kopii zapasowej bazy danych lokacji:** Przed uaktualnieniem programu System Center Configuration Manager centralnej lokacji administracyjnej lub lokacji głównej, przetestuj proces uaktualnienia bazy danych lokacji na kopii bazy danych lokacji.  

-   Należy przetestować proces uaktualniania bazy danych lokacji, ponieważ podczas uaktualniania lokacji może zmodyfikować bazy danych lokacji.  

-   Test uaktualnienia bazy danych nie jest wymagany, można zidentyfikować problemy z uaktualnieniem zanim dotkną produkcyjnej bazy danych ma wpływ.  

-   Nieudane uaktualnienie bazy danych lokacji może uniemożliwić korzystanie z bazy danych lokacji i wymóc przeprowadzenie odzyskiwania lokacji w celu przywrócenia jej funkcjonalności.  

-   Mimo że bazę danych lokacji jest udostępniana między lokacjami w hierarchii, warto zaplanować testowanie bazy danych w każdej uaktualnianej lokacji przed uaktualnieniem tej lokacji.  

-   W przypadku używania replik bazy danych dla punktów zarządzania w lokacji głównej, wyłącz replikację przed utworzeniem kopii zapasowej bazy danych lokacji.  

Program Configuration Manager nie obsługuje kopii zapasowych lokacji dodatkowych ani nie obsługuje uaktualnienia testowego bazy danych lokacji dodatkowej.   
Nie należy uruchamiać test uaktualnienia bazy danych na produkcyjnych bazach danych lokacji. Wykonanie tej czynności powoduje zaktualizowanie bazy danych lokacji, przez co lokacja może przestać działać. Aby uzyskać więcej informacji, zobacz [krok 2: Test uaktualnienia bazy danych przed instalacją aktualizacji](/sccm/core/servers/manage/install-in-console-updates#bkmk_step2) z **przed zainstalowaniem aktualizacji w konsoli**.  

 **Zaplanuj pilotażowe wdrażanie klienta:** Podczas instalowania aktualizacji powodującej aktualizację klienta można przetestować tę nową aktualizację klienta w środowisku przedprodukcyjnym przed wdrożeniem i uaktualnieniem wszystkich aktywnych klientów.   

 Aby móc korzystać z tej opcji, należy skonfigurować lokację do obsługi automatycznych uaktualnień w produkcji wstępnej, przed rozpoczęciem instalacji aktualizacji. Aby uzyskać więcej informacji, zobacz [Uaktualnianie klientów w programie System Center Configuration Manager](../../../core/clients/manage/upgrade/upgrade-clients.md) i   
[Testowanie uaktualnień klienta w kolekcji przedprodukcyjnej w programie System Center Configuration Manager](../../../core/clients/manage/upgrade/test-client-upgrades.md).  

 **Zaplanuj używanie okien obsługi do formantu, gdy serwery lokacji instalują aktualizacje:** Aby zdefiniować okres czasu, w którym można zainstalować aktualizacji na serwerze lokacji, można użyć okna obsługi. Może to ułatwić określenie, kiedy można zainstalować aktualizację w danej hierarchii.   

Począwszy od wersji aktualizacji 1602 okna obsługi zmieniono *usługi systemu windows*. Aby uzyskać więcej informacji, zobacz [usługi systemu windows dla serwerów lokacji](/sccm/core/servers/manage/service-windows).  

 **Uruchom narzędzie sprawdzania wymagań wstępnych Instalatora:**  Przed zainstalowaniem aktualizacji 1602, należy uruchomić narzędzie sprawdzania wymagań wstępnych niezależnie od instalacji aktualizacji. Po zainstalowaniu aktualizacji w lokacji zostanie ponownie uruchomione narzędzie sprawdzania wymagań wstępnych.  

Aby uzyskać więcej informacji, zobacz **krok 3: Uruchom narzędzie sprawdzania wymagań wstępnych przed instalacją aktualizacji** w [aktualizacji dla programu System Center Configuration Manager](../../../core/servers/manage/updates.md) tematu.  

> [!IMPORTANT]  
>  Po uruchomieniu narzędzia sprawdzania wymagań wstępnych niezależnie lub w ramach instalacji aktualizacji ten proces aktualizuje niektóre pliki źródłowe produktów, które są używane dla zadania obsługi lokacji. W związku z tym po uruchomieniu narzędzia sprawdzania wymagań wstępnych, lecz przed zainstalowaniem aktualizacji 1602, jeśli trzeba wykonać zadanie obsługi lokacji, uruchom **Setupwfe.exe** (Instalator programu Configuration Manager) z dysku CD. Najnowszy folder na serwerze lokacji.  

 **Zaktualizuj Lokacje:** Teraz można przystąpić do rozpoczęcia instalacji aktualizacji dla hierarchii. Zaleca się zaplanowanie instalacji aktualizacji poza normalnymi godzinami pracy każdej lokacji, gdy proces instalacji aktualizacji i jego akcje, aby ponownie zainstalować składniki lokacji i role systemu lokacji będą miały jak najmniejszy wpływ na działania biznesowe.

Aby uzyskać więcej informacji, zobacz [Aktualizacje programu System Center Configuration Manager](../../../core/servers/manage/updates.md).  

## <a name="see-also"></a>Zobacz także  
 [Aktualizacje programu System Center Configuration Manager](../../../core/servers/manage/updates.md)
