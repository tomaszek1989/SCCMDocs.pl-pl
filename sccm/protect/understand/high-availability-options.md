---
title: "Wysoka dostępność | Dokumentacja firmy Microsoft"
description: "Informacje o sposobie wdrażania programu System Center Configuration Manager za pomocą opcje zapewniające wysoką dostępność usług."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1a38421d-24c1-4fef-bf6c-42fce53109ac
caps.latest.revision: 4
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 1a4a9da88caba55d9e340c7fb1f31f4e3b957f3e
ms.openlocfilehash: d3e9afb90cdc85bc7299626b642c52be659e3bdf
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="high-availability-options-for-system-center-configuration-manager"></a>Opcje wysokiej dostępności dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*



Można wdrożyć System Center Configuration Manager za pomocą opcje zapewniające wysoką dostępność usług.   

Opcje, które obsługują wysokiej dostępności:   

-   Lokacje obsługują wiele wystąpień serwerów systemu lokacji, które dostarczają klientom ważne usługi.  

-   Centralne Lokacje administracyjne i lokacje główne obsługują kopii zapasowej bazy danych lokacji. Baza danych lokacji zawiera wszystkie konfiguracje lokacji oraz klientów i jest udostępniana między lokacjami w hierarchii, które zawierają witryny administracji centralnej.  

-   Wbudowane opcje odzyskiwania lokacji pozwalają ograniczyć przestoje serwera i obejmują zaawansowane opcje, które ułatwiają odzyskiwanie w przypadku istnienia hierarchii z centralną lokacją administracyjną.  

-   Klienci mogą automatycznie rozwiązywać typowe problemy bez konieczności interwencji administratora.  

-   Lokacje generują alerty dotyczące klientów, którzy nie mogą przesłać najnowszych danych, informując administratorów o potencjalnych problemach.  

-   Menedżer konfiguracji zawiera kilka wbudowanych raportów, które pozwalają zidentyfikować problemy i trendy zanim obejmą operacje serwera lub klienta.  

 Menedżer konfiguracji nie dostarcza usługi w czasie rzeczywistym i należy spodziewać się pewnego opóźnienia przesyłania danych. Dlatego jest większości przypadków tymczasowe przerwanie usługi problem krytyczny rzadko. Podczas konfigurowania lokacji i hierarchii o wysokiej dostępności pozwala ograniczyć przestoje, zachować autonomię operacji zachowana, i podano wysokiego poziomu usługi.  

 Na przykład klientów programu Configuration Manager zazwyczaj działają autonomicznie, używając harmonogramów i konfiguracji dla operacji oraz harmonogramów przesyłania danych do lokacji w celu przetwarzania.  

-   Gdy klienci nie mogą skontaktować się z lokacji, ich w pamięci podręcznej dane do przesłania do momentu może nawiązać kontakt z lokacji.  

-   Klienci, którzy nie mogą skontaktować się z lokacji nadal działają, używając ostatnich znanych harmonogramów oraz buforowane informacje, na przykład wcześniej pobraną aplikację, którą klienci muszą uruchomić lub zainstalować, dopóki nie może skontaktować się z witryny i odebrania nowych zasad.  

-   Lokacja monitoruje swoje systemy lokacji oraz klientów pod kątem okresowych aktualizacji stanu i może generować alerty, gdy nie można zarejestrować tych danych.  

-   Wbudowane raporty zapewniają wgląd w trwające operacje, a także historyczne operacje i trendy. Program Configuration Manager obsługuje również komunikaty oparte na stanie, zapewniające niemalże w czasie rzeczywistym informacje o trwających operacjach.  

  Użyj informacji przedstawionych w tym temacie w połączeniu z informacjami znajdującymi się w następujących artykułach:
-   [Zalecany sprzęt](../../core/plan-design/configs/recommended-hardware.md)
-   [Obsługiwane systemy operacyjne dla serveres systemu lokacji](../../core/plan-design/configs/supported-operating-systems-for-site-system-servers.md)  

-   [Wymagania wstępne systemu lokacji i lokacji](../../core/plan-design/configs/site-and-site-system-prerequisites.md)


##  <a name="bkmk_snh"></a>Wysokiej dostępności dla lokacji i hierarchii  
 **Używanie klastra programu SQL Server do obsługi bazy danych lokacji:**  

 Korzystając z klastra programu SQL Server dla bazy danych w centralnej lokacji administracyjnej lub lokacji głównej, użyj Obsługa Failover wbudowanej w program SQL Server.  

 Lokacje dodatkowe nie mogą używać klastra programu SQL Server, a nie obsługują tworzenia kopii zapasowej lub odzyskiwania swojej bazy danych lokacji. Odzyskiwanie lokacji dodatkowej przez ponowne zainstalowanie lokacji dodatkowej od nadrzędnej lokacji głównej.  

 **Użyj grupy dostępności AlwaysOn programu SQL Server do obsługi bazy danych lokacji:**  

 Począwszy od wersji 1602, można użyć grup dostępności AlwaysOn programu SQL Server do obsługi bazy danych lokacji w lokacji głównej i centralnej lokacji administracyjnej jako rozwiązań wysokiej dostępności i odzyskiwania po awarii. Aby uzyskać więcej informacji, zobacz [AlwaysOn programu SQL Server dla bazy danych lokacji wysokiej dostępności dla programu System Center Configuration Manager](../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md).  

 **Wdrażanie hierarchii lokacji z centralnej lokacji administracyjnej, a jeden lub więcej podrzędnych lokacji głównych:**  

 Ta konfiguracja zapewnia odporność na uszkodzenia, gdy lokacje zarządzają nakładającymi się segmentami sieci. Ponadto ta konfiguracja zapewnia dodatkową opcję odzyskiwania wykorzystać te informacje z udostępnionej bazy danych dostępnych w innej lokacji, aby odbudować bazy danych lokacji w odzyskanej lokacji. Można użyć tej opcji, aby zastąpić uszkodzoną lub niedostępną kopię zapasową bazy danych lokacji nie powiodło się.  

 **Regularne tworzenie kopii zapasowych w centralnych lokacjach administracyjnych i lokacjach głównych:**  

 Podczas tworzenia i testowania regularnych kopii zapasowej można upewnij się, że masz dane niezbędne do odzyskania lokacji oraz odzyskiwania lokacji skraca czas.  

 **Instalowanie wielu wystąpień ról systemu lokacji:**  

 Po zainstalowaniu wielu wystąpień najważniejszych ról systemu lokacji, takie jak punkt zarządzania i punkt dystrybucji zapewnia nadmiarowe punkty kontaktu dla klientów w przypadku, gdy określony serwer systemu lokacji jest niedostępny.  

 **Instalowanie wielu wystąpień dostawcy programu SMS w lokacji:** Dostawca programu SMS zapewnia punkt kontaktu administracyjnego dla co najmniej jeden konsoli programu Configuration Manager. W przypadku instalowania wielu dostawców programu SMS można zapewnić nadmiarowość punktów kontaktu w celu administrowania lokacją i hierarchią.  

##  <a name="bkmk_ssr"></a>Wysokiej dostępności dla ról systemu lokacji  
 W każdej lokacji można wdrażać role systemu lokacji do świadczenia usług, które mają klientów do używania w tej lokacji. Baza danych lokacji zawiera informacje o konfiguracji lokacji i wszystkich klientów. Zapewnia wysoką dostępność bazy danych lokacji i odzyskiwania lokacji i bazy danych lokacji, jeśli to konieczne, należy użyć co najmniej jedną z dostępnych opcji.  

 **Nadmiarowość ważnych ról systemu lokacji:**  

-   Punkt usługi sieci Web Wykaz aplikacji  

-   Punkt witryny sieci Web katalogu aplikacji  

-   Punkt dystrybucji  

-   Punkt zarządzania  

-   Punkt aktualizacji oprogramowania  

-   punkt migracji stanu  

 Można zainstalować wiele wystąpień roli punktu usług raportowania, aby zapewnić nadmiarowość w ramach raportowania w lokacji i klientów.

 Można zainstalować rolę systemu lokacji punktu aktualizacji oprogramowania w klastrze systemu Windows (Równoważenia sieciowego), aby zapewnić obsługę pracy awaryjnej programu PowerShell  


 **Wbudowane kopii zapasowej:**  

 Menedżer konfiguracji zawiera wbudowane zadanie, które ułatwia tworzenie kopii zapasowej lokacji i ważnych informacji zgodnie z ustalonym harmonogramem. Ponadto Kreator instalacji programu Configuration Manager obsługuje akcje odzyskiwania lokacji ułatwiające przywrócenia lokacji do operacji.  

 **Publikowanie w usługach domenowych Active Directory i DNS:**  

 Każdą lokację można skonfigurować, aby publikowała dane dotyczące serwerów i usług systemu lokacji w usługach Active Directory Domain Services i w systemie DNS. Dzięki temu klienci mogą ustalić największej dostępności serwera w sieci oraz aby ustalić, czy są dostępne nowe serwery systemu lokacji zapewniające ważne usługi, takie jak punkty zarządzania.  

 **Konsola programu Configuration Manager i dostawcy programu SMS:**  

 Program Configuration Manager obsługuje instalowanie wielu dostawców programu SMS, każdy na innym komputerze, aby upewnić się, wiele punktów dostępu do konsoli programu Configuration Manager. Dzięki temu, gdy jeden komputer dostawcy programu SMS jest niedostępny, nadal możliwość wyświetlać i zmieniać konfigurację lokacji programu Configuration Manager i klientów.  

 Gdy konsola programu Configuration Manager łączy się z lokacją, łączy się z wystąpieniem dostawcy programu SMS w tej lokacji. Wystąpienie dostawcy programu SMS jest wybierane w sposób niejednoznaczny. Jeżeli wybrany dostawca programu SMS nie jest dostępna, masz następujące opcje:  

-   Połącz ponownie konsolę z lokacją. Do każdego nowego żądania połączenia jest przypisywane wystąpienie dostawcy programu SMS i jest możliwe, że nowe połączenie zostanie przypisana dostępnego wystąpienia.  

-   Połącz konsolę z innej lokacji programu Configuration Manager i Zarządzaj konfiguracją za pośrednictwem tego połączenia. Wprowadza małe opóźnienie zmian w konfiguracji nie więcej niż kilka minut. Po dostawcy programu SMS dla lokacji jest w trybie online, można ponownie połączyć konsola programu Configuration Manager bezpośrednio do lokacji, w której chcesz zarządzać.  

 Konsoli programu Configuration Manager można zainstalować na wielu komputerach dla użytkowników administracyjnych. Każdy dostawca programu SMS obsługuje połączenia z wielu konsol programu Configuration Manager.  

 **Punkt zarządzania:**  

 Zainstaluj wiele punktów zarządzania w każdej lokacji głównej i włączeniu lokacji do publikowania danych lokacji w infrastrukturze usługi Active Directory i DNS.  

 Wiele punktów zarządzania ułatwiają równoważenia obciążenia Użyj dowolnego jednego punktu zarządzania przez wielu klientów. Ponadto można zainstalować co najmniej jedną replikę bazy danych dla punktów zarządzania, aby ograniczyć liczbę operacji użycie Procesora CPU w punkcie zarządzania i zwiększyć dostępność tej ważnej roli systemu lokacji.  

 Ponieważ można zainstalować tylko jeden punkt zarządzania w lokacji dodatkowej, który musi znajdować się na serwerze lokacji dodatkowej, punkty zarządzania w lokacjach dodatkowych nie są uważane za konfiguracji o wysokiej dostępności.  

> [!NOTE]  
>  Urządzenia zarządzane przez lokalnego zarządzania urządzeniami przenośnymi nawiązać tylko jeden punkt zarządzania w lokacji głównej. Punkt zarządzania przypisany przez program Configuration Manager do urządzeń przenośnych podczas rejestracji i nie ulega on zmianie. W przypadku zainstalowania wielu punktów zarządzania i włączenia więcej niż jednego dla urządzeń przenośnych, punkt zarządzania, który jest przypisany do klienta urządzenia przenośnego jest deterministyczna.  
>   
>  Punkt zarządzania używany przez klienta urządzenia przenośnego stanie się niedostępny, należy rozwiązać problem dotyczący tego punktu zarządzania lub wyczyścić urządzenie przenośne i ponownie zarejestrować urządzenia przenośnego, dzięki czemu można ją przypisać do operacyjny punkt zarządzania jest włączony dla urządzeń przenośnych.  

 **Punkt dystrybucji:**  

 Zainstaluj wiele punktów dystrybucji i wdróż zawartość do wielu punktów dystrybucji. Można skonfigurować grupy pokrywających się granic dla lokalizacji zawartości, aby zapewnić klientom w każdej podsieci dostęp do wdrożenia z dwóch lub więcej punktów dystrybucji. Zaleca się skonfigurowanie co najmniej jeden punkt dystrybucji jako lokalizacji rezerwowej dla zawartości.  

 Aby uzyskać więcej informacji o lokalizacjach rezerwowych dla zawartości, zobacz [Zarządzanie zawartości i infrastruktury dla programu System Center Configuration Manager](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

 **Punkt usługi sieci web katalogu aplikacji i punkt witryny sieci Web katalogu aplikacji:**  

 Można zainstalować wiele wystąpień poszczególnych ról systemu lokacji i w celu zapewnienia optymalnej wydajności, wdrażania jednej z nich na tym samym komputerze systemu lokacji.  

 Każda rola systemu lokacji katalogu aplikacji zapewnia te same informacje co inne wystąpienia tej roli systemu lokacji, niezależnie od miejsca danej roli serwera lokacji w hierarchii. W związku z tym gdy klient wysyła żądanie do katalogu aplikacji i skonfigurowano domyślny katalog aplikacji witryny sieci Web punktu ustawienie klienta urządzenia automatycznie wykryć, klient może zostać skierowany do dowolnego dostępnego wystąpienia. Preferowane do lokalnego katalogu aplikacji serwerów systemu lokacji, na podstawie bieżącej lokalizacji sieciowej klienta.  

 Aby uzyskać więcej informacji dotyczących tego klienta ustawienie i sposób automatycznego wykrywania znaleźć [Agent komputera](../../core/clients/deploy/about-client-settings.md#computer-agent) w sekcji [informacje o ustawieniach klienta w programie System Center Configuration Manager](../../core/clients/deploy/about-client-settings.md) tematu.  

##  <a name="bkmk_client"></a>Wysoka dostępność klientów programu  
 **Operacje klienta są autonomiczne:**  

 Autonomia klienta programu Configuration Manager obejmuje następujące funkcje:  

-   Klienci nie wymagają ciągłego kontaktu z żadnym serwerem systemu lokacji. Wykonują wstępnie skonfigurowane akcje zgodnie z harmonogramem przy użyciu znanych konfiguracji.  

-   Klienci mogą używać każdego dostępnego wystąpienia roli systemu lokacji, która zapewnia usługi dla klientów i podejmie próbę skontaktuj się z pomocą znanymi serwerami aż do zlokalizowania dostępnego serwera.  

-   Klienci mogą uruchamiać spis, wdrożenia oprogramowania i wykonywać podobne Zaplanowane akcje bez konieczności bezpośredniego kontaktu z serwerami systemu lokacji.  

-   Klienci skonfigurowani do używania rezerwowego punktu stanu mogą przesyłać do rezerwowego punktu stanu szczegółowe nie komunikują się z punktem zarządzania.  

 **Klienci mogą samodzielnie się naprawiać:**  

 Klienci automatycznie rozwiązują większość typowych problemów bez konieczności bezpośredniej interwencji administratora:  

-   Klienci okresowo samodzielnie oceniają swój stan i podjąć działania w celu rozwiązania typowych problemów przy użyciu lokalnej pamięci podręcznej czynności zaradczych oraz plików źródłowych przeznaczonych do napraw.  

-   Gdy klient nie może przesłać informacji o stanie do swojej lokacji, lokacja może wygenerować alert. Użytkownicy administracyjni, którzy odbiorą te alerty mogą natychmiast podjąć akcje w celu przywrócenia prawidłowego działania klienta.  

 **Klienci z pamięci podręcznej informacje do użytku w przyszłości:**  

 Gdy klient komunikuje się z punktem zarządzania, klient może uzyskać i pamięci podręcznej następujące informacje:  

-   Ustawienia klienta.  

-   Harmonogramy klienta.  

-   Informacje o wdrożeniach oprogramowania i pobierania oprogramowania klienta jest zaplanowane do zainstalowania, gdy wdrożenie jest skonfigurowane dla tej akcji.  

 Gdy klient nie może połączyć się z punktem zarządzania klienci lokalnie z pamięci podręcznej informacje o stanie, stan i klienta raportowane do lokacji, a po nawiązaniu połączenia z punktem zarządzania przesyłają te dane.  

 **Klienci mogą przesyłać do rezerwowego punktu stanu:**  

 Podczas konfigurowania klienta do używania rezerwowego punktu stanu należy podać dodatkowy punkt kontaktu, do którego klient może przesłać ważne dane dotyczące jego działania. Klienci skonfigurowani do używania rezerwowego punktu stanu kontynuować wysyłanie dotyczących stanu ich operacji do tej roli systemu lokacji, nawet wtedy, gdy klient nie może komunikować się z punktem zarządzania.  

 **Centralne zarządzanie danymi i tożsamością klienta:**  

 Bazy danych lokacji, a nie w poszczególnych klientach ważne informacje o tożsamości każdego klienta i kojarzy te dane do określonego komputera lub użytkownika. Oznacza to, że:  

-   Pliki źródłowe klienta na komputerze można odinstalować i ponownie zainstalowana bez wpływu na rekordy historyczne dla komputera, na którym jest zainstalowany klient.  

-   Awaria komputera klienckiego nie wpływa na integralność informacji przechowywanych w bazie danych. Te informacje mogą pozostać dostępne do raportowania.  

##  <a name="bkmk_nonHAoptions"></a>Opcje dotyczące lokacji i ról systemu lokacji, które nie są wysokiej dostępności  
 Kilka systemów lokacji nie obsługują wiele wystąpień w lokacji lub w hierarchii. Te informacje ułatwiają przygotowanie do tych systemów lokacji, przechodzi do trybu offline.  

 **Serwer lokacji (lokacja):**  

 Menedżer konfiguracji nie obsługuje instalacji serwera lokacji dla każdej lokacji klastra systemu Windows Server lub klastra równoważenia obciążenia Sieciowego.  

 Poniższe informacje ułatwiają przygotowanie do serwera lokacji nie powiedzie się lub nie działa.  

-   Korzystając z wbudowanego zadania tworzenia kopii zapasowej regularnego tworzenia kopii zapasowych lokacji. W środowisku testowym należy regularnie Ćwicz Przywracanie lokacji z kopii zapasowej.  

-   Wdróż wiele lokacji programu Configuration Manager głównej w hierarchii z centralną lokacją administracyjną w celu uzyskania nadmiarowości. W przypadku niepowodzenia lokacji, należy wziąć pod uwagę przy użyciu skryptów logowania lub zasad grupy systemu Windows do ponownego przypisania klientów do lokacji działającej.  

-   Jeśli masz hierarchii z centralną lokacją administracyjną, można odzyskać za pomocą opcji odzyskiwania bazy danych lokacji z innej lokacji w hierarchii witryny Administracja centralna lub podrzędnej lokacji głównej.  

-   Lokacje dodatkowe nie można przywrócić i musi zostać zainstalowany ponownie.  

 **Punkt synchronizacji analizy zasobów (hierarchia):**  

 Ta rola systemu lokacji jest nie traktowana jako krytyczna i zapewnia opcjonalne funkcje w programie Configuration Manager. Jeśli ten system lokacji przejdzie do trybu offline, użyj jednej z następujących opcji:  

-   Rozwiąż przyczynę przejścia systemu lokacji do trybu offline.  

-   Odinstaluj rolę z bieżącego serwera i zainstaluj rolę na nowym serwerze.  

 **Punkt ochrony punktu końcowego (hierarchia):**  

 Ta rola systemu lokacji jest nie traktowana jako krytyczna i zapewnia opcjonalne funkcje w programie Configuration Manager. Jeśli ten system lokacji przejdzie do trybu offline, użyj jednej z następujących opcji:  

-   Rozwiąż przyczynę przejścia systemu lokacji do trybu offline.  

-   Odinstaluj rolę z bieżącego serwera i zainstaluj rolę na nowym serwerze.  

 **Punkt rejestracji (lokacja):**  

 Ta rola systemu lokacji jest nie traktowana jako krytyczna i zapewnia opcjonalne funkcje w programie Configuration Manager. Jeśli ten system lokacji przejdzie do trybu offline, użyj jednej z następujących opcji:  

-   Rozwiąż przyczynę przejścia systemu lokacji do trybu offline.  

-   Odinstaluj rolę z bieżącego serwera i zainstaluj rolę na nowym serwerze.  

 **Punkt proxy rejestracji (lokacja):**  

 Ta rola systemu lokacji jest nie traktowana jako krytyczna i zapewnia opcjonalne funkcje w programie Configuration Manager. Można jednak zainstalować wiele wystąpień tej roli systemu lokacji w lokacji oraz w wielu lokacjach w hierarchii. Jeśli ten system lokacji przejdzie do trybu offline, użyj jednej z następujących opcji:  

-   Rozwiąż przyczynę przejścia systemu lokacji do trybu offline.  

-   Odinstaluj rolę z bieżącego serwera i zainstaluj rolę na nowym serwerze.  

 Jeśli masz więcej niż jeden serwer proxy rejestracji w lokacji, Użyj aliasu DNS dla nazwy serwera. Gdy używasz tej konfiguracji DNS okrężnego zawiera niektóre odporność na uszkodzenia i równoważenie obciążenia na okoliczność rejestracji urządzeń przenośnych.  

 **Rezerwowy punkt stanu (lokacja lub hierarchia):**  

 Ta rola systemu lokacji jest nie traktowana jako krytyczna i zapewnia opcjonalne funkcje w programie Configuration Manager. Jeśli ten system lokacji przejdzie do trybu offline, użyj jednej z następujących opcji:  

-   Rozwiąż przyczynę przejścia systemu lokacji do trybu offline.  

-   Odinstaluj rolę z bieżącego serwera i zainstaluj rolę na nowym serwerze. Ponieważ klienci są przypisywani rezerwowy punkt stanu podczas instalacji klienta, należy zmodyfikować istniejących klientów do używania nowego serwera systemu lokacji.  

### <a name="see-also"></a>Zobacz także  
 [Obsługiwane konfiguracje dla programu System Center Configuration Manager](../../core/plan-design/configs/supported-configurations.md)

