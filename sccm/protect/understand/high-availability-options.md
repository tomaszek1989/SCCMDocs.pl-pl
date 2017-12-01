---
title: "Wysoka dostępność"
titleSuffix: Configuration Manager
description: "Informacje o sposobie wdrażania programu System Center Configuration Manager za pomocą opcje zapewniające wysoką dostępność usług."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1a38421d-24c1-4fef-bf6c-42fce53109ac
caps.latest.revision: "4"
author: mstewart
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 10d4cef1d753b8828be91a0dbfcba89025cd583f
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2017
---
# <a name="high-availability-options-for-system-center-configuration-manager"></a>Opcje wysokiej dostępności programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*



System Center Configuration Manager przy użyciu opcje zapewniające wysoką dostępność usług można wdrożyć.   

Opcje, które obsługują wysokiej dostępności:   

-   Lokacje obsługują wiele wystąpień serwerów systemu lokacji zapewniające ważne usługi dla klientów.  

-   Centralne Lokacje administracyjne i lokacje główne obsługują kopii zapasowej bazy danych lokacji. Baza danych lokacji zawiera wszystkie konfiguracje dla lokacji i klientów i jest udostępniana między lokacjami w hierarchii, które zawierają centralnej lokacji administracyjnej.  

-   Wbudowane opcje odzyskiwania lokacji pozwalają ograniczyć przestoje serwera i obejmują zaawansowane opcje, które ułatwiają odzyskiwanie w przypadku istnienia hierarchii z centralną lokacją administracyjną.  

-   Klienci mogą automatycznie rozwiązywać typowe problemy bez konieczności interwencji administratora.  

-   Lokacje generują alerty dotyczące klientów, którzy nie mogą przesłać najnowszych danych, informując administratorów o potencjalnych problemach.  

-   Configuration Manager udostępnia wiele wbudowanych raportów, które pozwalają zidentyfikować problemy i trendy zanim obejmą operacje serwera lub klienta.  

 Menedżer konfiguracji nie w czasie rzeczywistym usługi i należy spodziewać się pewnego opóźnienia przesyłania danych. W związku z tym jest rzadko w większości przypadków tymczasowe przerwanie usługi problem krytyczny. Po skonfigurowaniu lokacji i hierarchii pod kątem wysokiej dostępności na uwadze przestoju można zminimalizować, obsługiwane autonomię operacji i podać wysokiego poziomu usługi.  

 Na przykład klienci programu Configuration Manager zazwyczaj działają autonomicznie, przy użyciu znanych harmonogramów i konfiguracji w ramach operacji oraz harmonogramów przesyłania danych do lokacji w celu przetwarzania.  

-   Gdy klienci nie mogą skontaktować się z lokacji, buforują dane do przesłania może nawiązać kontakt z lokacji.  

-   Klienci, którzy nie może skontaktować się z lokacji kontynuują działanie, używając ostatnich znanych harmonogramów oraz buforowane informacje, na przykład wcześniej pobraną aplikację, którą klienci muszą uruchomić lub zainstalować, aż do kontaktowania się z witryną i odebrania nowych zasad.  

-   Lokacja monitoruje swoje systemy lokacji oraz klientów pod kątem okresowych aktualizacji stanu i może generować alerty, gdy nie można zarejestrować tych.  

-   Wbudowane raporty zapewniają wgląd w trwające operacje, a także w historyczne operacje i trendy. Configuration Manager również obsługuje komunikaty oparte na stanie, zapewniające niemalże w czasie rzeczywistym informacje o trwających operacjach.  

  Użyj informacji przedstawionych w tym temacie w połączeniu z informacjami znajdującymi się w następujących artykułach:
-   [Zalecany sprzęt](../../core/plan-design/configs/recommended-hardware.md)
-   [Obsługiwane systemy operacyjne dla serveres systemu lokacji](../../core/plan-design/configs/supported-operating-systems-for-site-system-servers.md)  

-   [Wymagania wstępne dla lokacji i systemu lokacji](../../core/plan-design/configs/site-and-site-system-prerequisites.md)


##  <a name="bkmk_snh"></a>Wysoka dostępność dla lokacji i hierarchii  
 **Używanie klastra programu SQL Server do hostowania bazy danych lokacji:**  

 Korzystając z klastra programu SQL Server dla bazy danych w centralnej lokacji administracyjnej lub lokacji głównej, należy użyć funkcji awaryjnej wbudowane w program SQL Server.  

 Lokacje dodatkowe nie można używać klastra programu SQL Server, a nie obsługują tworzenia kopii zapasowej lub przywracania swojej bazy danych lokacji. Odzyskiwanie lokacji dodatkowej przez ponowne zainstalowanie lokacji dodatkowej od nadrzędnej lokacji głównej.  

 **Użyj grupy dostępności AlwaysOn programu SQL Server do hostowania bazy danych lokacji:**  

 Począwszy od wersji 1602, można użyć grup dostępności AlwaysOn programu SQL Server do hostowania bazy danych lokacji w lokacjach głównych i centralnej lokacji administracyjnej jako rozwiązania wysokiej dostępności i odzyskiwania po awarii. Aby uzyskać więcej informacji, zobacz [AlwaysOn programu SQL Server dla bazy danych lokacji o wysokiej dostępności programu System Center Configuration Manager](../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md).  

 **Wdrażanie hierarchii lokacji z centralnej lokacji administracyjnej, a jeden lub więcej podrzędnych lokacji głównych:**  

 Ta konfiguracja zapewnia odporność na uszkodzenia, gdy lokacje zarządzają nakładającymi się segmentami sieci. Ponadto ta konfiguracja zapewnia dodatkową opcję odzyskiwania wykorzystanie informacji z udostępnionej bazy danych dostępne w innej lokacji, aby odbudować bazę danych w odzyskanej lokacji. Ta opcja umożliwia zastąpić uszkodzoną lub niedostępną kopię zapasową bazy danych lokacji nie powiodło się.  

 **Regularne tworzenie kopii zapasowych w centralnych lokacjach administracyjnych i lokacjach głównych:**  

 Podczas tworzenia i testowania kopii zapasowej lokacji regularnych można upewnij się, że dane niezbędne do odzyskania lokacji oraz skraca czas procesu odzyskiwania lokacji.  

 **Instalowanie wielu wystąpień ról systemu lokacji:**  

 Po zainstalowaniu wielu wystąpień najważniejszych ról systemu lokacji, takie jak punkt zarządzania i punkt dystrybucji, w przypadku, gdy określony serwer systemu lokacji jest offline musisz podać nadmiarowe punkty kontaktu dla klientów.  

 **Instalowanie wielu wystąpień dostawcy programu SMS w lokacji:** Dostawca programu SMS zapewnia punkt kontaktu administracyjnego dla co najmniej jeden konsoli programu Configuration Manager. W przypadku instalowania wielu dostawców programu SMS można zapewnić nadmiarowość punktów kontaktu w celu administrowania lokacją i hierarchią.  

##  <a name="bkmk_ssr"></a>Wysoka dostępność dla ról systemu lokacji  
 W każdej lokacji można wdrażać role systemu lokacji do świadczenia usług, których klienci mają używać w tej lokacji. Baza danych lokacji zawiera informacje o konfiguracji lokacji oraz wszystkich klientów. Zapewnienie wysokiej dostępności bazy danych lokacji i funkcji odzyskiwania lokacji i bazy danych lokacji, jeśli to konieczne, należy użyć co najmniej jeden z dostępnych opcji.  

 **Nadmiarowość ważnych ról systemu lokacji:**  

-   Punkt usługi sieci Web Wykaz aplikacji  

-   Punkt witryny sieci Web katalogu aplikacji  

-   Punkt dystrybucji  

-   Punkt zarządzania  

-   Punkt aktualizacji oprogramowania  

-   punkt migracji stanu  

 Można zainstalować wiele wystąpień roli punktu usług raportowania, aby zapewnić nadmiarowość również dla raportowania w lokacji i klientów.

 Można użyć programu PowerShell, aby zainstalować rolę systemu lokacji punktu aktualizacji oprogramowania w klastrze systemu Windows (Równoważenia sieciowego), aby zapewnić obsługę pracy awaryjnej  


 **Kopia zapasowa wbudowane witrynę:**  

 Programu Configuration Manager zawiera wbudowane zadanie kopii zapasowej, które ułatwia tworzenie kopii zapasowej lokacji i ważnych informacji zgodnie z ustalonym harmonogramem. Ponadto Kreator instalacji programu Configuration Manager obsługuje akcje odzyskiwania lokacji w celu przywrócenia lokacji do obsługi operacji.  

 **Publikowanie w usługach domenowych Active Directory i DNS:**  

 Każdą lokację można skonfigurować, aby publikowała dane dotyczące serwerów i usług systemu lokacji w usługach Active Directory Domain Services i w systemie DNS. Dzięki temu klienci największej dostępności serwera w sieci i ustalić, kiedy są dostępne nowe serwery systemu lokacji zapewniające ważne usługi, takie jak punkty zarządzania.  

 **Dostawca programu SMS i program Configuration Manager konsoli:**  

 Program Configuration Manager obsługuje instalowanie wielu dostawców programu SMS na innym komputerze, aby upewnić się, wiele punktów dostępu do konsoli programu Configuration Manager. Dzięki temu, że jeśli jeden komputer dostawcy programu SMS jest w trybie offline, nadal można wyświetlać i zmieniać konfigurację lokacji programu Configuration Manager i klienci.  

 Gdy konsola programu Configuration Manager łączy się z lokacją, nawiązuje połączenie z wystąpieniem dostawcy programu SMS w tej lokacji. Wystąpienie dostawcy programu SMS jest wybierane w sposób niedeterministyczny. Jeżeli wybrany dostawca programu SMS nie jest dostępna, masz następujące opcje:  

-   Ponownego podłączenia konsoli do lokacji. Do każdego nowego żądania połączenia jest przypisywane w niedeterministyczny sposób wystąpienie dostawcy programu SMS i jest możliwe, że nowe połączenie zostanie przypisany dostępnego wystąpienia.  

-   Połącz konsolę z inną lokację programu Configuration Manager i Zarządzaj konfiguracją za pośrednictwem tego połączenia. Powstaje niewielkie opóźnienie wprowadzania zmian w konfiguracji nie więcej niż kilka minut. Po dostawcy programu SMS dla lokacji jest w trybie online, można ponownie połączyć konsoli programu Configuration Manager bezpośrednio do lokacji, w której chcesz zarządzać.  

 Konsola programu Configuration Manager można zainstalować na wielu komputerach dla użytkowników administracyjnych. Każdy dostawca programu SMS obsługuje połączenia z wielu konsol programu Configuration Manager.  

 **Punkt zarządzania:**  

 Zainstaluj wiele punktów zarządzania w każdej lokacji głównej, a następnie włącz lokacji do publikowania danych lokacji, infrastrukturą usługi Active Directory i DNS.  

 Wiele punktów zarządzania ułatwić Równoważenie obciążenia użycie dowolnego jednego punktu zarządzania przez wielu klientów. Ponadto można zainstalować jeden lub więcej repliki bazy danych dla punktów zarządzania, aby zmniejszyć użycie Procesora CPU działania punktu zarządzania i zwiększyć dostępność tej ważnej roli systemu lokacji.  

 Ponieważ można zainstalować tylko jeden punkt zarządzania w lokacji dodatkowej, który musi znajdować się na serwerze lokacji dodatkowej, punkty zarządzania w lokacjach dodatkowych nie są uważane w konfiguracji wysokiej dostępności.  

> [!NOTE]  
>  Urządzenia zarządzane przez lokalnego zarządzania urządzeniami przenośnymi nawiązać tylko jeden punkt zarządzania w lokacji głównej. Punkt zarządzania jest przypisany przez program Configuration Manager z urządzeniem przenośnym podczas rejestracji i nie ulega on zmianie. W przypadku zainstalowania wielu punktów zarządzania i włączenia więcej niż jednego dla urządzeń przenośnych, punkt zarządzania, który jest przypisany do klienta urządzenia przenośnego jest deterministyczna.  
>   
>  Punkt zarządzania, które używa klienta urządzenia przenośnego stanie się niedostępny, należy rozwiązać problem z tym punktem zarządzania lub wymazać urządzenie przenośne i ponownie zarejestrować urządzenie przenośne, dzięki czemu można przypisać operacyjny punkt zarządzania włączony dla urządzeń przenośnych.  

 **Punkt dystrybucji:**  

 Zainstaluj wiele punktów dystrybucji i wdróż zawartość do wielu punktów dystrybucji. Można skonfigurować grupy pokrywających się granic dla lokalizacji zawartości Aby upewnić się, że klienci w każdej podsieci dostęp do wdrożenia z dwóch lub więcej punktów dystrybucji. Zaleca się skonfigurowanie co najmniej jeden punkt dystrybucji jako lokalizacji rezerwowej dla zawartości.  

 Aby uzyskać więcej informacji na temat lokalizacji rezerwowych dla zawartości, zobacz [zarządzanie zawartością i infrastrukturą zawartości programu System Center Configuration Manager](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

 **Punkt usługi sieci web katalogu aplikacji i punkt witryny sieci Web katalogu aplikacji:**  

 Można zainstalować wiele wystąpień poszczególnych ról systemu lokacji, a także aby uzyskać najlepszą wydajność, wdrażania jednej z nich na tym samym komputerze systemu lokacji.  

 Każda rola systemu lokacji katalogu aplikacji zapewnia te same informacje co inne wystąpienia tej roli systemu lokacji bez względu na lokalizację roli serwera lokacji w hierarchii. W związku z tym gdy klient wysyła żądanie do katalogu aplikacji i skonfigurowaniu klienta urządzenia punktu witryny sieci Web katalogu aplikacji domyślne ustawienie automatycznie dla wykrywanie, klient może zostać skierowany do dowolnego dostępnego wystąpienia. Preferowane lokalnego katalogu aplikacji serwerów systemu lokacji, na podstawie bieżącej lokalizacji sieciowej klienta.  

 Aby uzyskać więcej informacji na temat tego klienta ustawienie i jak automatyczne wykrywanie znaleźć [Agent komputera](../../core/clients/deploy/about-client-settings.md#computer-agent) sekcji [informacje o ustawieniach klienta w programie System Center Configuration Manager](../../core/clients/deploy/about-client-settings.md) tematu.  

##  <a name="bkmk_client"></a>Wysoka dostępność dla klientów  
 **Operacje klienta są autonomiczne:**  

 Autonomia klienta programu Configuration Manager obejmuje następujące funkcje:  

-   Klienci nie wymagają ciągłego kontaktu z wszystkimi serwerami systemu lokacji określonych. Wykonują wstępnie skonfigurowane akcje zgodnie z harmonogramem przy użyciu znanych konfiguracji.  

-   Klienci mogą używać każdego dostępnego wystąpienia roli systemu lokacji, która zapewnia usługi dla klientów i podejmie próbę skontaktuj się z znanymi serwerami aż do zlokalizowania dostępnego serwera.  

-   Klienci mogą uruchamiać spis, wdrożenia oprogramowania i podobne Zaplanowane akcje bez konieczności bezpośredniego kontaktu z serwerami systemu lokacji.  

-   Klienci, którzy są skonfigurowane do używania rezerwowego punktu stanu można przesyłają dane do rezerwowego punktu stanu, gdy nie mogli komunikować się z punktem zarządzania.  

 **Klienci mogą samodzielnie się naprawiać:**  

 Klienci automatycznie rozwiązują większość typowych problemów bez konieczności bezpośredniej interwencji administratora:  

-   Klienci okresowo samodzielnie oceniają swój stan i podjąć działania w celu rozwiązania typowych problemów przy użyciu lokalnej pamięci podręcznej czynności zaradczych oraz plików źródłowych przeznaczonych do napraw.  

-   Gdy klient nie może przesłać informacji o stanie do swojej lokacji, lokacja może wygenerować alert. Użytkownicy administracyjni, którzy odbiorą te alerty mogą natychmiast podjąć akcje do przywrócenia normalnego działania klienta.  

 **Klienci pamięci podręcznej informacje do użytku w przyszłości:**  

 Gdy klient komunikuje się z punktem zarządzania, klient może uzyskać i pamięci podręcznej następujące informacje:  

-   Ustawienia klienta.  

-   Harmonogramy klienta.  

-   Informacje o wdrożeniach oprogramowania i pobierania oprogramowania klienta zostało zaplanowane do zainstalowania, gdy wdrożenie jest skonfigurowane dla tej akcji.  

 Gdy klient nie może skontaktować się z punktem zarządzania klienci lokalnie buforowanie tych informacji stanu, stanu i klienta, które zgłaszają do lokacji i przesyłają te dane, po nawiązaniu połączenia z punktem zarządzania.  

 **Klienci mogą przesyłać do rezerwowego punktu stanu:**  

 Podczas konfigurowania klienta do używania rezerwowego punktu stanu, musisz podać dodatkowy punkt kontaktu dla klienta może przesłać ważne dane dotyczące jego działania. Klienci, którzy są skonfigurowane do używania rezerwowego punktu stanu kontynuować wysyłanie dotyczących stanu ich operacji do tej roli systemu lokacji, nawet wtedy, gdy klient nie może komunikować się z punktem zarządzania.  

 **Centralne zarządzanie danymi i tożsamością klienta:**  

 Bazy danych lokacji, a nie poszczególnych klient zachowuje ważne informacje o tożsamości każdego klienta, a skojarza te dane do określonego komputera lub użytkownika. Oznacza to:  

-   Pliki źródłowe klienta na komputerze może być odinstalowania i ponownego zainstalowania bez wpływu na rekordy historyczne dla komputera, na którym jest zainstalowany klient.  

-   Awaria komputera klienckiego nie wpływa na integralność informacji przechowywanych w bazie danych. Te informacje mogą pozostać dostępne do raportowania.  

##  <a name="bkmk_nonHAoptions"></a>Opcje dla lokacji i ról systemu lokacji, które nie mają wysokiej dostępności  
 Kilka systemów lokacji nie obsługują wiele wystąpień w lokacji lub w hierarchii. Te informacje mogą pomóc w przygotowaniu się do tych systemów lokacji do trybu offline.  

 **Serwer lokacji (lokacja):**  

 Menedżer konfiguracji nie obsługuje instalacji serwera lokacji dla każdej lokacji klastra systemu Windows Server lub klastra równoważenia obciążenia Sieciowego.  

 Poniższe informacje mogą pomóc w przygotowaniu się na serwerze lokacji nie powiedzie się lub nie działa:  

-   Użyj wbudowanego zadania tworzenia kopii zapasowej do regularnego tworzenia kopii zapasowej lokacji. W środowisku testowym regularnie Ćwicz Przywracanie lokacji z kopii zapasowej.  

-   Wdróż wiele lokacji programu Configuration Manager głównej w hierarchii z centralną lokacją administracyjną uzyskania nadmiarowości. W przypadku niepowodzenia lokacji, należy rozważyć użycie skryptów zasad lub logowania grupy systemu Windows do ponownego przypisania klientów do lokacji funkcjonalności.  

-   Jeśli masz hierarchii z centralną lokacją administracyjną, można odzyskać centralnej lokacji administracyjnej lub podrzędnej lokacji głównej przy użyciu opcji, aby odzyskać bazę danych lokacji z innej lokacji w hierarchii.  

-   Lokacje dodatkowe nie można przywrócić i musi zostać ponownie zainstalowany.  

 **Punkt synchronizacji analizy zasobów (hierarchia):**  

 Ta rola systemu lokacji jest nie traktowana jako krytyczna i zapewnia opcjonalne funkcje w programie Configuration Manager. Jeśli ten system lokacji przejdzie do trybu offline, użyj jednej z następujących opcji:  

-   Rozwiąż przyczynę systemu lokacji do trybu offline.  

-   Odinstaluj rolę z bieżącego serwera, a instalacja roli na nowym serwerze.  

 **Punkt ochrony punktu końcowego (hierarchia):**  

 Ta rola systemu lokacji jest nie traktowana jako krytyczna i zapewnia opcjonalne funkcje w programie Configuration Manager. Jeśli ten system lokacji przejdzie do trybu offline, użyj jednej z następujących opcji:  

-   Rozwiąż przyczynę systemu lokacji do trybu offline.  

-   Odinstaluj rolę z bieżącego serwera, a instalacja roli na nowym serwerze.  

 **Punkt rejestracji (lokacja):**  

 Ta rola systemu lokacji jest nie traktowana jako krytyczna i zapewnia opcjonalne funkcje w programie Configuration Manager. Jeśli ten system lokacji przejdzie do trybu offline, użyj jednej z następujących opcji:  

-   Rozwiąż przyczynę systemu lokacji do trybu offline.  

-   Odinstaluj rolę z bieżącego serwera, a instalacja roli na nowym serwerze.  

 **Punkt proxy rejestracji (lokacja):**  

 Ta rola systemu lokacji jest nie traktowana jako krytyczna i zapewnia opcjonalne funkcje w programie Configuration Manager. Jednak można zainstalować wiele wystąpień tej roli systemu lokacji w lokacji oraz w wielu lokacjach w hierarchii. Jeśli ten system lokacji przejdzie do trybu offline, użyj jednej z następujących opcji:  

-   Rozwiąż przyczynę systemu lokacji do trybu offline.  

-   Odinstaluj rolę z bieżącego serwera, a instalacja roli na nowym serwerze.  

 Jeśli masz więcej niż jeden serwer proxy rejestracji w lokacji, Użyj aliasu DNS dla nazwy serwera. Jeśli używasz tej konfiguracji DNS działanie okrężne zawiera niektóre odporność na uszkodzenia i równoważenie obciążenia na użytkownicy rejestrują swoje urządzenia przenośne.  

 **Rezerwowy punkt stanu (lokacja lub hierarchia):**  

 Ta rola systemu lokacji jest nie traktowana jako krytyczna i zapewnia opcjonalne funkcje w programie Configuration Manager. Jeśli ten system lokacji przejdzie do trybu offline, użyj jednej z następujących opcji:  

-   Rozwiąż przyczynę systemu lokacji do trybu offline.  

-   Odinstaluj rolę z bieżącego serwera, a instalacja roli na nowym serwerze. Ponieważ klienci są przypisani rezerwowy punkt stanu podczas instalacji klienta, należy zmodyfikować istniejących klientów, aby użyć nowego serwera systemu lokacji.  

### <a name="see-also"></a>Zobacz także  
 [Obsługiwane konfiguracje programu System Center Configuration Manager](../../core/plan-design/configs/supported-configurations.md)
