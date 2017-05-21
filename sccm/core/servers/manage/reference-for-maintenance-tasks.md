---
title: "Informacje dotyczące zadań związanych z konserwacją | Dokumentacja firmy Microsoft"
description: "Odczytać szczegółów dla każdego zadania konserwacji lokacji programu System Center Configuration Manager i tego, czy zadania te są domyślnie włączone."
ms.custom: na
ms.date: 3/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 68dc6acd-5848-47a4-b4c1-ffa40e47890b
caps.latest.revision: 16
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d94acac84f052a01de9d9c9f65f237c0006c45b8
ms.openlocfilehash: a2d4420c2274a9b1ceb47ffd267849fdb5a55a61
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="reference-for-maintenance-tasks-for-system-center-configuration-manager"></a>Informacje o zadaniach konserwacji programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Ten temat zawiera szczegółowe informacje dla każdego zadania konserwacji lokacji programu System Center Configuration Manager i określa typy lokacji, w którym zadanie będzie dostępne. Każdy wpis wskazuje także jeśli zadanie jest włączone lub nie jest domyślnie włączone. Aby uzyskać informacje dotyczące planowania i konfigurowania lokacji do uruchomienia zadania konserwacji, zobacz [zadania konserwacji programu System Center Configuration Manager](../../../core/servers/manage/maintenance-tasks.md).  

**Wykonaj kopię zapasową serwera lokacji**: To zadanie służy do przygotowania odzyskiwania kluczowych danych. Można utworzyć kopii zapasowej kluczowych informacji w celu przywrócenia lokacji i bazy danych programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [kopii zapasowych i odzyskiwania dla programu System Center Configuration Manager](../../../protect/understand/backup-and-recovery.md).  

-   **Witryna Administracja centralna**: Włączono    
-   **Lokacja główna**: Niewłączone    
-   Lokacja dodatkowa: Niedostępne  

**Sprawdź tytuł aplikacji z informacjami o spisie**: To zadanie służy do zapewniania spójności między tytułów oprogramowania, które są zgłaszane w spisie oprogramowania oraz w katalogu analizy zasobów. Aby uzyskać więcej informacji, zobacz [Wprowadzenie do analizy zasobów w programie System Center Configuration Manager](../../../core/clients/manage/asset-intelligence/introduction-to-asset-intelligence.md).  

-   **Witryna Administracja centralna**: Włączono    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Wyczyść flagę instalacji**: To zadanie służy do usuwania flagi instalacji w odniesieniu do klientów, którzy nie przesłali rekordu wykrywania interwału czasowego podczas **ponownego odnajdywania klienta** okresu. Flaga instalacji uniemożliwia automatyczną instalację wypychaną klienta na komputerze, który może być aktywnego klienta programu Configuration Manager.  

-   Witryna Administracja centralna: Niedostępne    
-   **Lokacja główna**: Niewłączone    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe dane żądania aplikacji**: To zadanie służy do usuwania przestarzałych żądań aplikacji z bazy danych. Aby uzyskać więcej informacji dotyczących żądań aplikacji, zobacz [tworzenia i wdrażania aplikacji z System Center Configuration Manager](/sccm/apps/get-started/create-and-deploy-an-application).  

-   Witryna Administracja centralna: Niedostępne
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałą historię pobierania klienta**: To zadanie służy do usuwania danych historycznych dotyczących źródła pobierania używane przez klientów. Pobierz informacje o źródle są wykorzystywane do wypełniania [pulpitu nawigacyjnego źródeł danych klientów](/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed#client-data-sources-dashboard).  
-  Witryna Administracja centralna — nie jest dostępny
-     **Lokacja główna** — włączona
-  Lokacja dodatkowa — niedostępna

**Usuń przestarzałe operacje klienta**: To zadanie służy do usuwania wszystkich przestarzałych danych operacji klienta z bazy danych lokacji. Obejmują one na przykład dane dla przestarzałych lub wygasłych powiadomień klienta (takich jak żądania pobierania zasad komputera lub użytkownika) i dane programu Endpoint Protection (takie jak żądania użytkownika administracyjnego dla klientów w celu wykonania skanowania lub pobrania zaktualizowanych definicji).

-   **Witryna Administracja centralna**: Włączono    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałą historię obecności klienta**: To zadanie służy do usuwania informacji historii stanu online klientów (zarejestrowanych przez powiadomienia klienta), która jest starsza niż określony czas. Aby uzyskać więcej informacji na temat powiadomień klienta, zobacz [Jak monitorować klientów w programie System Center Configuration Manager](../../../core/clients/manage/monitor-clients.md).  

-   **Witryna Administracja centralna**: Włączono   
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe chmury zarządzania bramy ruch danych**: To zadanie służy do usuwania wszystkich przestarzałych danych dotyczących ruchu, który przechodzi przez [brama zarządzania chmury](/sccm/core/clients/manage/plan-cloud-management-gateway) z bazy danych lokacji. Na przykład w tym dane o liczbie żądania, żądania całkowita liczba bajtów, bajtów odpowiedzi, liczba nieudanych żądań i maksymalną liczbę równoczesnych żądań.  
- **Centralna lokacja administracyjna** — włączona
- **Lokacja główna** — włączona
- Lokacja dodatkowa — niedostępna


**Usuń przestarzałe zebrane pliki**: To zadanie służy do usuwania przestarzałych informacji na temat zbieranych plików z bazy danych. Umożliwia również usunięcie zebranych plików ze struktury folderów serwera lokacji w wybranej lokacji. Domyślnie pięć najnowsze kopii zebranych plików są przechowywane na serwerze lokacji w **Inboxes\sinv.box\FileCol** katalogu. Aby uzyskać więcej informacji, zobacz [wprowadzenie do spisu oprogramowania System Center Configuration Manager](/sccm/core/clients/manage/inventory/introduction-to-software-inventory).  

-   Witryna Administracja centralna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe dane powiązania komputera**: To zadanie służy do usuwania przestarzałych danych powiązania komputera wdrożenia systemu operacyjnego z bazy danych. Te informacje są używane w ramach przywracania stanu użytkowników. Aby uzyskać więcej informacji o skojarzeniach komputera, zobacz [Zarządzanie stanem użytkownika w programie System Center Configuration Manager](../../../osd/get-started/manage-user-state.md).  

-   Witryna Administracja centralna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe dane wykrywania usunięcia**: To zadanie służy do usuwania przestarzałych danych z bazy danych, który został utworzony przy użyciu funkcji widoków wyodrębniania. Widoków wyodrębniania są domyślnie wyłączone. Możesz tylko je włączyć za pomocą zestawu SDK programu Configuration Manager. Jeśli funkcja widoków wyodrębniania nie będzie włączona, nie będą istniały dane do usunięcia przez to zadanie.  

-   **Witryna Administracja centralna**: Włączono    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzały rekord wymazania urządzenia**: To zadanie służy do usuwania przestarzałych danych dotyczących akcji wymazania urządzenia przenośnego z bazy danych. Aby dowiedzieć się, jak czyszczenie urządzeń przenośnych, zobacz [ochrona danych za pomocą czyszczenia danych, blokowania lub resetowania za pomocą programu System Center Configuration Manager kodu dostępu](/sccm/mdm/deploy-use/wipe-lock-reset-devices).  

-   Witryna Administracja centralna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe urządzenia zarządzane przez łącznik serwera Exchange**: To zadanie służy do usuwania przestarzałych danych dotyczących urządzeń przenośnych, które są zarządzane przy użyciu łącznika serwera Exchange. Usuwanie danych odbywa się zgodnie z interwałem skonfigurowanym dla **Ignoruj urządzenia przenośne, które są nieaktywne przez ponad (dni)** opcja **odnajdywania** we właściwościach łącznika serwera Exchange. Aby uzyskać więcej informacji, zobacz [Zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i Exchange](../../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md).  

-   Witryna Administracja centralna: Niedostępne   
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe dane wykrywania**: To zadanie służy do usuwania przestarzałych danych odnajdywania z bazy danych. Dane te mogą obejmować rekordy wynikające z wykrywania interwału czasowego, odnajdywania sieci oraz metody odnajdywania usług domenowych w usłudze Active Directory (systemu, użytkownika i grupy). Gdy to zadanie zostanie uruchomione w lokacji, dane powiązane z tą lokacją zostaną usunięte, a zmiany zostaną zreplikowane do innych lokacji. Aby uzyskać informacje na temat odnajdywania, zobacz [Uruchamianie odnajdywania dla programu System Center Configuration Manager](../../../core/servers/deploy/configure/run-discovery.md).  

-   Witryna Administracja centralna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe dane użycia punktów dystrybucji**: To zadanie służy do usuwania z bazy danych przestarzałych danych dla punktów dystrybucji przechowywanych dłuższy niż określony czas.  

-   **Witryna Administracja centralna**: Włączono    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe dane historii stanu kondycji ochrony punktu końcowego**: To zadanie służy do usuwania przestarzałych informacji dotyczących ochrony punktu końcowego stanu z bazy danych. Aby uzyskać więcej informacji na temat informacji o stanie programu Endpoint Protection, zobacz [Jak monitorować program Endpoint Protection w programie System Center Configuration Manager](../../../protect/deploy-use/monitor-endpoint-protection.md).  

-   Witryna Administracja centralna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe zarejestrowane urządzenia**: Począwszy od aktualizacji 1602, to zadanie jest domyślnie wyłączona. To zadanie służy do usuwania z bazy danych lokacji przestarzałych danych dotyczących urządzeń przenośnych, które jeszcze nie zgłosił żadnych informacji o lokacji w wyznaczonym czasie.

To zadanie dotyczy urządzeń, które są zarejestrowane przy użyciu programu Microsoft Intune (hybrydowy) lub Configuration Manager lokalnego zarządzania urządzeniami przenośnymi. Informacje o systemach operacyjnych urządzeń, które są zarejestrowane przy użyciu programu Configuration Manager lub usługi Intune, zobacz [urządzeń przenośnych zarejestrowanych w usłudze Microsoft Intune](../../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices.md#mobile-devices-enrolled-by-microsoft-intune) w sekcji [obsługiwanych systemów operacyjnych dla urządzeń i klientów dla programu System Center Configuration Manager](../../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices.md).

-   Witryna Administracja centralna: Niedostępne    
-   **Lokacja główna**: Niewłączone    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałą historię spisu**: To zadanie służy do usuwania danych spisu przechowywanych dłuższy niż określony czas z bazy danych. Aby uzyskać informacje o historii spisu, zobacz [Jak używać Eksploratora zasobów do wyświetlania spisu sprzętu w programie System Center Configuration Manager](../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md).  

-   Witryna Administracja centralna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe dane dziennika**: To zadanie służy do usuwania przestarzałych danych dziennika, który jest używany do rozwiązywania problemów z bazy danych. Te dane nie dotyczą działań składników programu Configuration Manager.  

> [!IMPORTANT]  
> To zadanie jest domyślnie uruchamiane codziennie w każdej lokacji. W centralnej lokacji administracyjnej oraz lokacjach głównych zadanie usuwa dane starsze niż 30 dni. Jeśli używasz programu SQL Server Express w lokacji dodatkowej, upewnij się, że to zadanie wykonywane codziennie i usuwało dane nieaktywne od 7 dni.  

-   **Witryna Administracja centralna**: Włączono    
-   **Lokacja główna**: Włączono    
-   **Lokacja dodatkowa**: Włączono  

**Usuń przestarzałą historię zadań powiadamiania**: To zadanie służy do usuwania informacji o zadaniach powiadomień klientów z bazy danych lokacji, gdy nie zostało zaktualizowane przez określony czas. Aby uzyskać więcej informacji o powiadomieniach klienta, zobacz [zadania wdrażania klienta programu System Center Configuration Manager](../../../core/clients/manage/monitor-clients.md).  

-   Witryna Administracja centralna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe dane podsumowujące replikacji**: To zadanie służy do usuwania przestarzałych danych podsumowujących replikacji z bazy danych lokacji, gdy nie zostało zaktualizowane przez określony czas. Aby uzyskać więcej informacji, zobacz sekcję [Monitorowanie linków replikacji bazy danych i stanu replikacji](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_MonitorRepLinksAndStatuss) w temacie [Monitorowanie infrastruktury hierarchii i replikacji w programie System Center Configuration Manager](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md).  

-   **Witryna Administracja centralna**: Włączono    
-   **Lokacja główna**: Włączono    
-   **Lokacja dodatkowa**: Włączono  

**Usuń stare rekordy kodów dostępu**: To zadanie w lokacji najwyższego poziomu w hierarchii służy do usuwania przestarzałych danych Resetowanie kodu dostępu dla urządzeń z systemem Android i Windows Phone. Resetowanie kodu dostępu dane są szyfrowane, ale zawierają numer PIN dla urządzeń. Domyślnie to zadanie jest włączone i usuwa dane starsze niż jeden dzień.  

-   **Witryna Administracja centralna**: Włączono    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe dane śledzenia replikacji**: To zadanie służy do usuwania przestarzałych danych dotyczących replikacji bazy danych między lokacjami programu Configuration Manager z bazy danych. Zmiana konfiguracji tego zadania konserwacji powoduje zastosowanie tej konfiguracji do wszystkich odnośnych lokacji w hierarchii. Aby uzyskać więcej informacji, zobacz sekcję [Monitorowanie linków replikacji bazy danych i stanu replikacji](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_MonitorRepLinksAndStatuss) w temacie [Monitorowanie infrastruktury hierarchii i replikacji w programie System Center Configuration Manager](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md).  

-   **Witryna Administracja centralna**: Włączono    
-   **Lokacja główna**: Włączono    
-   **Lokacja dodatkowa**: Włączono  

**Usuń przestarzałe dane pomiaru oprogramowania**: To zadanie służy do usuwania przestarzałych danych pomiaru oprogramowania przechowywanych dłuższy niż określony czas z bazy danych. Aby uzyskać więcej informacji, zobacz [Pomiar użytkowania oprogramowania w programie System Center Configuration Manager](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md).  

-   Witryna Administracja centralna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe dane podsumowania pomiaru oprogramowania**: To zadanie służy do usuwania przestarzałych danych podsumowania pomiaru oprogramowania przechowywanych dłuższy niż określony czas z bazy danych. Aby uzyskać więcej informacji, zobacz [Pomiar użytkowania oprogramowania w programie System Center Configuration Manager](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md).  

-   Witryna Administracja centralna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe komunikaty stanu**: To zadanie służy do usuwania przestarzałych danych komunikatów stanu zgodnie z konfiguracją reguł filtru stanu z bazy danych. Aby uzyskać informacje, zobacz sekcję "Monitorowanie stanu systemu programu Configuration Manager" w temacie [używać alertów i stanu systemu dla programu System Center Configuration Manager](../../../core/servers/manage/use-alerts-and-the-status-system.md).  

-   **Witryna Administracja centralna**: Włączono    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe dane zagrożeń**: To zadanie służy do usuwania przestarzałych danych zagrożeń Endpoint Protection, przechowywanych dłuższy niż określony czas z bazy danych. Aby uzyskać więcej informacji na temat programu Endpoint Protection, zobacz [Program Endpoint Protection w programie System Center Configuration Manager](../../../protect/deploy-use/endpoint-protection.md).  

-   Witryna Administracja centralna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe nieznane komputery**: To zadanie służy do usuwania informacji o nieznanych komputerach z bazy danych lokacji, gdy nie zostało zaktualizowane przez określony czas. Aby uzyskać więcej informacji, zobacz [Przygotowywanie do wdrożenia na nieznanych komputerach w programie System Center Configuration Manager](../../../osd/get-started/prepare-for-unknown-computer-deployments.md).  

-   Witryna Administracja centralna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe dane koligacji urządzenia użytkownika**: To zadanie służy do usuwania przestarzałych danych koligacji urządzenia użytkownika z bazy danych. Aby uzyskać więcej informacji, zobacz [Łączenie użytkowników i urządzeń za pomocą koligacji urządzenia użytkownika w programie System Center Configuration Manager](../../../apps/deploy-use/link-users-and-devices-with-user-device-affinity.md).  

-   Witryna Administracja centralna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń wygasłe MDM zbiorczego rejestrowania rekordów pakietu**: To zadanie służy do usuwania starych certyfikatów rejestracji zbiorczej i odpowiednie profile po wygaśnięciu certyfikatu rejestracji. Aby uzyskać więcej informacji, zobacz [utworzyć profile certyfikatów](/sccm/protect/deploy-use/create-certificate-profiles).
-   **Witryny administracji centralnej**: Włączono
-   **Lokacja główna**: Włączono
-   Lokacja dodatkowa: Niedostępne

**Usuń nieaktywne dane wykrywania klienta**: To zadanie służy do usuwania danych odnajdywania nieaktywnych klientów z bazy danych. Klienci są oznaczane jako nieaktywne, gdy klient jest oznaczony jako przestarzały i które są skutek konfiguracji dotyczących stanu klienta.

To zadanie działa tylko z zasobów, które są klientów programu Configuration Manager. Różni się od **Usuń przestarzałe dane wykrywania** zadania, które usuwania wszystkich przestarzałych rekordów danych wykrywania. Uruchomienie tego zadania w jednej lokacji spowoduje usunięcie danych z bazy danych we wszystkich lokacjach w hierarchii. Aby uzyskać więcej informacji, zobacz [Jak skonfigurować stan klienta w programie System Center Configuration Manager](../../../core/clients/deploy/configure-client-status.md).  

> [!IMPORTANT]  
> Jeśli jest włączone, należy skonfigurować to zadanie, by było uruchamiane z większym interwałem niż **odnajdywania pulsu** harmonogram. Umożliwi to aktywnym klientom wysłanie rekordu wykrywania interwału czasowego, aby oznaczyć swój rekord klienta jako aktywny to zadanie nie powoduje ich usunięcia.  

-   Witryna Administracja centralna: Niedostępne    
-   **Lokacja główna**: Niewłączone    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe alerty**: To zadanie służy do usuwania wygasłych alertów, które były przechowywane dłużej niż przez określony czas z bazy danych. Aby uzyskać więcej informacji, zobacz [Korzystanie z alertów i systemu stanu w programie System Center Configuration Manager](../../../core/servers/manage/use-alerts-and-the-status-system.md).  

-   **Witryna Administracja centralna**: Włączono    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe dane wykrywania klienta**: To zadanie służy do usuwania przestarzałych rekordów klienta z bazy danych. Rekord oznaczony jako przestarzały jest zazwyczaj zastępowany przez nowszy rekord dotyczący tego samego klienta. Nowszy rekord staje się bieżącym rekordem klienta. Aby uzyskać informacje na temat odnajdywania, zobacz [Uruchamianie odnajdywania dla programu System Center Configuration Manager](../../../core/servers/deploy/configure/run-discovery.md).  

> [!IMPORTANT]  
> Gdy jest włączone, należy skonfigurować to zadanie, by było uruchamiane z większym interwałem niż harmonogram odnajdywania pulsu. Umożliwia to klientowi wysłanie rekordu wykrywania interwału czasowego, korygującego stan przedawnienia.  

-   Witryna Administracja centralna: Niedostępne    
-   **Lokacja główna**: Niewłączone    
-   Lokacja dodatkowa: Niedostępne  

**Usuń przestarzałe lasu Lokacje i podsieci wykrywania**: To zadanie służy do usuwania danych dotyczących lokacji usługi Active Directory, podsieci i domen, które nie zostały wykryte przez metodę odnajdywania lasu usługi Active Directory w ciągu ostatnich 30 dni. Usunięcie danych wykrywania, ale nie ma wpływu na granice utworzone na podstawie danych odnajdywania. Aby uzyskać więcej informacji, zobacz [Uruchamianie odnajdywania dla programu System Center Configuration Manager](../../../core/servers/deploy/configure/run-discovery.md).  

-   **Witryna Administracja centralna**: Włączono    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Usuwanie rekordów oddzielone stan wdrożenia klienta**: To zadanie służy do okresowego przeczyścić tabelę, która zawiera informacje o stanie wdrożenia klienta. To zadanie spowoduje wyczyszczenie rekordy skojarzone z zlikwidowana lub przestarzałe urządzenia.  
-   **Witryna Administracja centralna**: Włączono    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne

**Usuń nieużywane wersje aplikacji**: To zadanie służy do usuwania wersji aplikacji, które nie są już używane. Aby uzyskać więcej informacji, zobacz [Korygowanie i zastępowanie aplikacji w programie System Center Configuration Manager](../../../apps/deploy-use/revise-and-supersede-applications.md).  

-   Witryna Administracja centralna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Oceń członków kolejki**: Ocenę członkostwa kolekcji można skonfigurować jako składnik lokacji. Aby uzyskać więcej informacji na temat składników lokacji, zobacz [Składniki lokacji dla programu System Center Configuration Manager](../../../core/servers/deploy/configure/site-components.md).  

-   Witryna Administracja centralna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Monitoruj klucze**: To zadanie służy do monitorowania integralności kluczy podstawowych bazy danych programu Configuration Manager. Klucz podstawowy to kolumna (lub połączenie kolumn) który unikatowo identyfikuje jeden wiersz i odróżnia go od innych wierszy w tabeli bazy danych programu Microsoft SQL Server.  

-   **Witryna Administracja centralna**: Włączono    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Odbuduj indeksy**: To zadanie służy do odbudowywania indeksów bazy danych programu Configuration Manager. Indeks to struktura bazy danych tworzona w tabeli bazy danych w celu przyspieszenia pobierania danych. Na przykład wyszukiwanie w indeksowanej kolumnie odbywa się znacznie szybciej niż wyszukiwanie w kolumnie, która nie jest indeksowana.

Aby poprawić wydajność, indeksy bazy danych programu Configuration Manager są często aktualizowane, aby zachować synchronizację ze stale zmieniającymi danymi, które są przechowywane w bazie danych. To zadanie tworzy indeksy w kolumnach bazy danych, które są unikatowe co najmniej w 50 procentach, porzuca indeksy w kolumnach, które są unikatowe w mniej niż 50 procentach oraz odtwarza wszystkie istniejące indeksy spełniające kryteria unikatowości danych.  

-   **Witryna Administracja centralna**: Niewłączone    
-   **Lokacja główna**: Niewłączone    
-   **Lokacja dodatkowa**: Niewłączone  

**Podsumuj dane zainstalowanego oprogramowania**: To zadanie służy do podsumowania w jednym rekordzie ogólnym danych dotyczących zainstalowanego oprogramowania z wielu rekordów. Podsumowanie danych może skompresować ilość danych przechowywanych w bazie danych programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [wprowadzenie do spisu oprogramowania System Center Configuration Manager](../../clients/manage/inventory\introduction-to-software-inventory.md).  

-   Witryna Administracja centralna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Podsumuj dane użycia pliku pomiaru oprogramowania**: To zadanie służy do podsumowania danych z wielu rekordów pomiaru użycia pliku w jednym rekordzie ogólnym oprogramowania. Podsumowanie danych może skompresować ilość danych przechowywanych w bazie danych programu Configuration Manager.

Można użyć tego zadania z **Podsumuj miesięczne dane użycia pomiaru oprogramowania** zadań do podsumowywania danych pomiaru użytkowania oprogramowania oraz do oszczędzania przestrzeni dyskowej w bazie danych programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [Pomiar użytkowania oprogramowania w programie System Center Configuration Manager](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md).  

-   Witryna Administracja centralna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Podsumuj miesięczne dane użycia pomiaru oprogramowania**: To zadanie służy do podsumowania danych z wielu rekordów miesięcznego użytkowania w jednym rekordzie ogólnym oprogramowania. Podsumowanie danych może skompresować ilość danych przechowywanych w bazie danych programu Configuration Manager.

Można użyć tego zadania z **Podsumuj pliku dane użycia pomiaru oprogramowania** zadań do podsumowywania danych pomiaru użytkowania oprogramowania oraz do oszczędzania przestrzeni dyskowej w bazie danych programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [Pomiar użytkowania oprogramowania w programie System Center Configuration Manager](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md).  

-   Witryna Administracja centralna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Aktualizuj dostępny element docelowy aplikacji**: To zadanie służy do Menedżera konfiguracji ponownie Oblicz mapowanie wdrożenia zasad i aplikacji do zasobów w kolekcji. Podczas wdrażania zasad ani aplikacji do kolekcji, Configuration Manager tworzy wstępne mapowanie między obiektami, które można wdrożyć i członków kolekcji.

Te mapowania są przechowywane w tabeli, do której można się szybko odwołać. Gdy członkostwa kolekcji ulegają zmianom, przechowywane mapowania są aktualizowane, aby odzwierciedlać wprowadzone zmiany. Jest jednak możliwa te mapowania spadku zsynchronizowane. Przykładowo, jeśli lokacja nie przetworzy prawidłowo pliku powiadomienia, zmiana może nie zostać uwzględniona w zmianach mapowań. To zadanie odświeża mapowania na podstawie przynależności do bieżącej kolekcji.  

-   Witryna Administracja centralna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

**Aktualizacja tabel wykazu aplikacji**: To zadanie służy do synchronizacji pamięci podręcznej bazy danych witryny sieci Web katalogu aplikacji z najnowszymi informacjami o aplikacji. Zmiana konfiguracji tego zadania konserwacji powoduje zastosowanie tej konfiguracji do wszystkich lokacji głównych w hierarchii.  

-   Witryna Administracja centralna: Niedostępne    
-   **Lokacja główna**: Włączono    
-   Lokacja dodatkowa: Niedostępne  

