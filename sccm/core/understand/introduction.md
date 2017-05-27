---
title: Wprowadzenie | Dokumentacja firmy Microsoft
description: Uzyskaj podstawowe informacje jako wprowadzenie do System Center Configuration Manager.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3343eccf-bf09-41cd-9e68-03e893c7f904
caps.latest.revision: 16
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 916aac9a8f724e37044884cd73de5fea1f1a8f97
ms.openlocfilehash: 76f907b17df0dd2f102e34ca3cfb3ffc813c0004
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="introduction-to-system-center-configuration-manager"></a>Wprowadzenie do programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Produkt pakietu Microsoft System Center rozwiązań do zarządzania programu System Center Configuration Manager może pomóc zarządzania urządzeniami i użytkownikami lokalnie i w chmurze.  

**Menedżer konfiguracji umożliwia pomóc:**   
-   Zwiększ produktywność IT i wydajność zmniejszenie ręcznego wykonania zadań i pozwolić skupić się na projektach wysokiej wartości.  
-   Maksymalizacji inwestycji w sprzęt i oprogramowanie.  
-   Zwiększenie możliwości dostępnych wydajność pracy użytkowników przez zapewnienie odpowiedniego oprogramowania w odpowiednim czasie.  

**Configuration Manager pomaga dostarczać skuteczniejszych usług informatycznych dzięki umożliwieniu:**  

-   Bezpieczne i skalowalne wdrażanie oprogramowania.  
-   Zarządzanie ustawieniami zgodności.  
-   Wszechstronne zarządzanie zasobami serwerów, komputerów stacjonarnych, laptopów i urządzeń przenośnych  

**Program Configuration Manager rozszerza i współpracuje z istniejących technologii firmy Microsoft i rozwiązania.**  

Na przykład programu Configuration Manager integruje się z:  

-   Microsoft Intune do zarządzania szeroką gamę platformy urządzeń przenośnych.  
-   Windows Server Update Services (WSUS) do zarządzania aktualizacjami oprogramowania.  
-   Usługi certyfikatów.  
-   Exchange Server i usługi Exchange Online.  
-   Zasady grupy systemu Windows.
-   W SYSTEMIE DNS.   
-   Zautomatyzowanej Deployment Kit (Windows ADK) i narzędzie migracji stanu użytkownika (USMT).  
-   Usługi wdrażania systemu Windows (WDS).  
-   Pomoc zdalna pulpitu i zdalnej.  

Configuration Manager używa również:  

-   usług domenowych Active Directory do zabezpieczeń, lokalizacji usług, konfiguracji oraz odkrywania użytkowników i urządzeń przeznaczonych do zarządzania;  
-   Microsoft SQL Server jako bazy danych zarządzania zmianami rozproszonej — oraz integruje się z programu SQL Server Reporting Services (SSRS) do generowania raportów pozwalających na monitorowanie i śledzenie działań zarządzania.  
-   Role systemu lokacji, które rozszerzają funkcje zarządzania i korzystać z usług sieci web programu Internetowe usługi informacyjne (IIS).
-   usług inteligentnego transferu w tle (BITS) i BranchCache ułatwiających zarządzanie dostępną przepustowością sieci.  

Aby skutecznie skorzystać z programu Configuration Manager, należy najpierw dokładnie zaplanować i przetestować funkcje zarządzania, przed użyciem programu Configuration Manager w środowisku produkcyjnym. Jako aplikacja zaawansowanego zarządzania programu Configuration Manager może potencjalnie wpłynąć na każdym komputerze w organizacji. Podczas wdrażania i zarządzania programu Configuration Manager dokładne zaplanowanie i kwestia wymagań biznesowych programu Configuration Manager można zmniejszyć narzutów administracyjnych i łącznego kosztu posiadania.  

Aby dowiedzieć się więcej o programie Configuration Manager, skorzystaj z następujących tematów i dodatkowe sekcje w tym temacie.  


**Tematy pokrewne w tej bibliotece dokumentacji:**  

-   [Funkcje i możliwości programu System Center Configuration Manager](../../core/plan-design/changes/features-and-capabilities.md)  
-   [Wybierz rozwiązanie do zarządzania urządzeniami programu System Center Configuration Manager](../../core/plan-design/choose-a-device-management-solution.md)  
-   [Co zostało zmienione w programie System Center Configuration Manager z programu System Center 2012 Configuration Manager](../../core/plan-design/changes/what-has-changed-from-configuration-manager-2012.md)
-   [Podstawowe założenia programu System Center Configuration Manager](../../core/understand/fundamentals.md)  
-   [Wypróbuj System Center Configuration Manager przez tworzenie aplikacji w środowisku laboratoryjnym](/sccm/core/get-started/set-up-your-lab)
-   [Znaleźć pomocy dla za pomocą programu System Center Configuration Manager](../../core/understand/find-help.md)  
-   [Funkcje usunięte i przestarzałe dla programu System Center Configuration Manager](../../core/plan-design/changes/removed-and-deprecated-features.md)  

##  <a name="BKMK_Console"></a> Konsola programu Configuration Manager  
 Po zainstalowaniu programu Configuration Manager umożliwia konsoli programu Configuration Manager do konfigurowania ustawień lokacji i klientów i uruchamiać i monitorowania zadań zarządzania. Konsola jest głównym punktem administracyjnym, który pozwala na zarządzanie wieloma lokacjami.  

 Za pomocą konsoli można uruchomić konsole dodatkowe pozwalające na obsługę konkretnych zadań zarządzania klientami, takich jak:  

-   **Eksplorator zasobów**do wyświetlenia informacji o spisach sprzętu i oprogramowania.  
-   **Zdalne sterowanie**do zdalnego łączenia się z komputerami klienckimi i usuwania problemów.  

Można zainstalować konsolę programu Configuration Manager na dodatkowych komputerach i ograniczyć dostęp i ograniczyć, co użytkownicy administracyjni mogą wyświetlić w konsoli przy użyciu Menedżera konfiguracji administracji opartej na rolach.  

Aby uzyskać więcej informacji, zobacz [Instalowanie konsol programu System Center Configuration Manager](../../core/servers/deploy/install/install-consoles.md).

##  <a name="BKMK_ApplicationCatalog"></a> Katalog aplikacji, Centrum oprogramowania i Portal firmy  
 **Wykaz aplikacji** to witryna sieci Web, w której użytkownicy mogą wyszukiwać programy dla komputerów z systemem Windows i żądać ich. Aby ta strona była dostępna, w lokacji musisz zainstalować punkt usługi sieci Web wykazu aplikacji oraz punkt witryny sieci Web wykazu aplikacji.  

 **Centrum oprogramowania** jest aplikacja, która jest zainstalowana po zainstalowaniu klienta programu Configuration Manager na komputerach z systemem Windows. Użytkownicy uruchomić tę aplikację, aby zażądać oprogramowania i zarządzania oprogramowaniem Configuration Manager wdraża się do nich. Centrum oprogramowania pozwala na realizację następujących zadań:  

-   Przeglądanie i Instalacja oprogramowania z katalogu aplikacji.  
-   Wyświetlenie historii żądań oprogramowania.  
-   Skonfiguruj w przypadku programu Configuration Manager może instalować oprogramowanie na ich urządzeniach.  
-   Konfigurowanie ustawień dostępu do zdalnego sterowania, jeśli zdalne sterowanie włączone przez administratora.  

**Portal firmy** to aplikacja lub witryna sieci Web zapewniająca funkcje podobne do katalogu aplikacji, ale dla urządzeń przenośnych zarejestrowanych w programie Microsoft Intune.  

Aby uzyskać więcej informacji, zobacz [wprowadzenie do zarządzania aplikacjami w programie System Center Configuration Manager](../../apps/understand/introduction-to-application-management.md).  

###  <a name="BKMK_Client"></a>Właściwości programu Configuration Manager (na komputery z systemem Windows)  
 Po zainstalowaniu klienta programu Configuration Manager na komputerach z systemem Windows, Configuration Manager jest zainstalowany w Panelu sterowania. Zazwyczaj nie trzeba konfigurować tej aplikacji, ponieważ konfiguracja klienta jest wykonywana w konsoli programu Configuration Manager. Za pomocą tej aplikacji użytkownicy administracyjni oraz pomoc techniczna może rozwiązywać problemy u poszczególnych klientów.  

 Aby uzyskać więcej informacji dotyczących wdrażania klienta, zobacz [Metody instalacji klientów w programie System Center Configuration Manager](../../core/clients/deploy/plan/client-installation-methods.md).  

##  <a name="BKMK_ExampleScenarios"></a> Przykładowe scenariusze programu Configuration Manager  
 W poniższych scenariuszach została pokazana firma Trey Research, która za pomocą programu System Center Configuration Manager chce użytkowników:  

-   Można zwiększyć wydajność.  
-   Jednolite Zarządzanie zgodnością, usprawnić czynności administracyjne.
-   Uprościć zarządzanie urządzeniami w celu zredukowania kosztów działu IT.  

We wszystkich scenariuszach głównym administratorem programu Configuration Manager jest Adam.  

###  <a name="BKMK_ScenarioEmpower"></a>Przykładowy scenariusz: Zwiększenie możliwości dostępnych dla użytkowników przez zapewnienie im dostępu do aplikacji z dowolnego urządzenia  
 Firma Trey Research chce, aby wszyscy pracownicy mieli dostęp do aplikacji, które są im niezbędne tak efektywnie. Adam mapuje te wymagania firmy do następujących scenariuszy:  

|Wymaganie|Bieżący stan zarządzania klientami|Przyszły stan zarządzania klientami|  
|-----------------|-------------------------------------|------------------------------------|  
|Nowi pracownicy mogą być wydajni od pierwszego dnia w pracy.|Nowi pracownicy, mają one czekać na zainstalowanie po raz pierwszy znaku, aplikacji.|Nowi pracownicy, zaloguj się one i aplikacje są instalowane i gotowa do użycia.|  
|Pracownicy mogą szybko i wygodnie prosić o potrzebne dodatkowe programy.|Gdy pracownicy potrzebować dodatkowych programów, muszą założyć zgłoszenie w pomocy technicznej. Następnie zwykle oczekują dwóch dni na jego przetworzenie oraz zainstalowanie aplikacji.|Gdy pracownicy potrzebować dodatkowych programów, mogą ich zażądać bezpośrednio z witryny sieci Web. Są one instalowane natychmiast, jeśli nie ma żadnych ograniczeń licencyjnych. Jeśli występują takie ograniczenia, użytkownicy muszą najpierw uzyskać odpowiednią zgodę na instalację aplikacji.<br /><br /> Witryna sieci Web zawiera użytkowników tylko te aplikacje, które mogą zostać zainstalowane.|  
|Pracownicy mogą używać urządzeń przenośnych w pracy, o ile urządzenia te są zgodne z monitorowanymi i wymuszanymi zasadami bezpieczeństwa.<br /><br /> Zasady te obejmują wymuszania silne hasło, blokowanie urządzenia po okresie braku aktywności i zdalne czyszczenie zgubienia lub kradzieży.|Pracownicy łączą urządzeń przenośnych do serwera Exchange dla usługi poczty e-mail. Jednak funkcje raportowania, aby upewnić się, że są one zgodne z zasadami bezpieczeństwa skonfigurowanymi w domyślnych zasadach skrzynek pocztowych programu Exchange ActiveSync są ograniczone. Używanie prywatnych urządzeń przenośnych jest niedozwolone, chyba że dział IT potwierdzi ich zgodność z tymi zasadami.|Dział IT może sprawdzać zgodność urządzeń przenośnych z wymaganymi ustawieniami. Dzięki temu użytkownicy mogą nadal używać tych urządzeń w pracy. Użytkownicy mogą zdalnie wyczyścić swoje urządzenie przenośne utraty lub kradzieży i pomocy technicznej można czyścić każdy użytkownik urządzenia przenośnego, które ma być zgłaszane utraty lub kradzieży.<br /><br /> Rejestracja urządzeń przenośnych w środowisku PKI zwiększa bezpieczeństwo i poziom kontroli.|  
|Pracownicy mogą być produktywni nawet, jeśli nie są one przy własnym biurku.|Gdy pracownicy, którzy nie są przy własnym biurku i nie ma komputerów przenośnych, nie uzyskują dostęp do swoich aplikacji za pomocą komputerów publicznych, które są dostępne w całej firmy.|Pracownicy mogą korzystać z komputerów publicznych, aby uzyskać dostęp do aplikacji i danych.|  
|Ciągłość biznesowa ma z reguły pierwszeństwo przed instalowaniem wymaganych aplikacji i aktualizacji oprogramowania.|Wymagane aplikacje i aktualizacje oprogramowania są instalowane w ciągu dnia i zakłócają pracę użytkowników, ponieważ spowalniają komputer lub uruchamiają go ponownie w czasie instalacji.|Użytkownicy mogą skonfigurować godziny pracy, aby uniemożliwić instalowanie, podczas gdy w przypadku korzystania z komputera wymaganego oprogramowania.|  

 Aby spełnić te wymagania, Adam wykorzystuje te możliwości zarządzania programu Configuration Manager i opcje konfiguracji:  

-   Zarządzanie aplikacjami  
-   Zarządzanie urządzeniami przenośnymi  

Implementuje te wymagania przy użyciu kroków konfiguracji opisanych w poniższej tabeli:  

|Kroki konfiguracji|Wynik|  
|-------------------------|-------------|  
|ADAM sprawdza, czy nowi użytkownicy mają konta użytkowników w usłudze Active Directory i tworzy nową kolekcję na podstawie kwerendy w programie Configuration Manager dla tych użytkowników. Następnie określa dla tych użytkowników koligację urządzenia użytkownika, tworząc plik mapujący te konta użytkowników na komputerach podstawowych, z których będą korzystali, a następnie importuje ten plik do programu Configuration Manager.<br /><br /> Aplikacje, które muszą mieć nowi użytkownicy, zostały już utworzone w programie Configuration Manager. Następnie wdraża aplikacje, których celem wymagane do kolekcji zawierającej nowych użytkowników.|Ze względu na informacje o koligacji urządzenia użytkownika aplikacje są instalowane na każdego użytkownika komputera podstawowego lub komputerach, zanim użytkownik loguje się.<br /><br /> Aplikacje są gotowe do użycia natychmiast po pomyślnym zalogowaniu użytkownika.|  
|Adam instaluje i konfiguruje role systemu lokacji katalogu aplikacji, aby użytkownicy mogli przeglądać w poszukiwaniu aplikacji, które mają być zainstalowane. Tworzy wdrożenia aplikacji, których cel to Dostępne, a następnie wdraża te aplikacje do kolekcji zawierającej nowych użytkowników.<br /><br /> Adam konfiguruje aplikacje z ograniczoną liczbą licencji tak, aby wymagały zatwierdzenia.|Użytkownicy mogą teraz używać katalogu aplikacji, aby przeglądać aplikacje, które mogą zostać zainstalowane. Użytkownicy mogą następnie natychmiast zainstalować aplikacje lub zażądać zatwierdzenia i wrócić do katalogu aplikacji, aby zainstalować je po zatwierdzeniu żądania przez dział pomocy technicznej.|  
|ADAM tworzy łącznik serwera Exchange w programie Configuration Manager do zarządzania urządzeniami przenośnymi łączącymi się z serwerem Exchange lokalnej firmy. Konfiguruje ten łącznik przy użyciu ustawień zabezpieczeń, które obejmują Wymaganie silnego hasła i blokowania urządzenia przenośnego po okresie braku aktywności.<br /><br /> Dodatkowe zarządzania dla urządzeń z systemem Windows Phone 8, Windows RT i iOS Adam uzyskuje subskrypcji usługi Microsoft Intune. Następnie instaluje rolę systemu lokacji punktu połączenia usługi. To rozwiązanie dotyczące zarządzania urządzeniami przenośnymi zwiększa możliwości firmy w zakresie obsługi zarządzania tymi urządzeniami. Obejmuje udostępnianie aplikacji użytkownicy mogą zainstalować na tych urządzeniach oraz rozbudowane Zarządzanie ustawieniami. Połączenia z urządzeniami przenośnymi są ponadto zabezpieczone za pomocą certyfikatów PKI, które są automatycznie generowanych i wdrażanych przez usługę Intune.<br /><br /> Po skonfigurowaniu punktu połączenia usługi i subskrypcji do użytku z programem Configuration Manager, Adam wysyła posiadaczom tych urządzeń przenośnych na ich kliknij łącze, aby rozpocząć proces rejestracji wiadomości e-mail.<br /><br /> Dla urządzeń przenośnych, które mają być zarejestrowane przez program Microsoft Intune Adam stosuje ustawienia zgodności, aby skonfigurować ustawienia zabezpieczeń tych urządzeń przenośnych. Te ustawienia obejmują Wymaganie silnego hasła i blokowania urządzenia przenośnego po okresie braku aktywności.|Te dwa rozwiązania w zakresie zarządzania urządzeniami przenośnymi umożliwiają działowi IT organizacji użytkownika dostarczanie informacji o raportowaniu dotyczących urządzeń przenośnych stosowanych w sieci firmowej i ich zgodności ze skonfigurowanymi ustawieniami zabezpieczeń.<br /><br /> Użytkownicy są wyświetlane w jaki sposób zdalnie czyścić zawartość urządzeń przenośnych za pomocą katalogu aplikacji lub portalu firmy w przypadku utracenia lub kradzieży urządzenia przenośnego. Pomoc techniczna jest również nakazał sposób zdalnie czyścić urządzeń przenośnych dla użytkowników za pomocą konsoli programu Configuration Manager.<br /><br /> Ponadto dla urządzeń przenośnych zarejestrowanych w programie Microsoft Intune Adam teraz można wdrażać aplikacje mobilne użytkownikom ich zainstalowanie, zbierać więcej danych dotyczących zapasów z tych urządzeń oraz lepszą kontrolę nad tymi urządzeniami dzięki dostępowi do większej liczby ustawień.|  
|Firma Trey Research ma kilka komputerów publicznych, z których korzystają pracownicy odwiedzający biuro. Pracownicy mają aplikacje były dostępne dla nich wszędzie tam, gdzie one logowania. Adam nie chce jednak instalować lokalnie wszystkich aplikacji na każdym komputerze.<br /><br /> Z tego względu Adam tworzy wymagane aplikacje z dwoma typami wdrożenia:<br /><br /> **Pierwszy:** Pełne, lokalnej instalacji aplikacji, która wymaga, aby go można zainstalować tylko na urządzeniu podstawowym użytkownika.<br /><br /> **Drugi:** Wersja wirtualna aplikacji, która zawiera wymagania, że nie należy go instalować na urządzeniu podstawowym użytkownika.|Podczas odwiedzania pracowników logowania do komputera publicznego, widzą aplikacje, które wymagają one wyświetlane jako ikony na pulpicie komputera publicznego. Po uruchomieniu aplikacji, jest ona przesyłana strumieniowo jako aplikację wirtualną. W ten sposób można je tak wydajnymi, tak jakby one są dostępne na pulpicie.|  
|Umożliwia ADAM użytkownicy wiedzieli, że ich mogą konfigurować godzin pracy w Centrum oprogramowania i można wybrać opcji uniemożliwiających wdrażanie oprogramowania w trakcie tego okresu i, gdy komputer jest w trybie prezentacji.|Ponieważ użytkownicy mogą kontrolować, kiedy wdraża oprogramowania programu Configuration Manager na ich komputerach, użytkownicy mogą pracować efektywniej w godzinach roboczych.|  

 Te czynności konfiguracyjne i wyniki sprawiają, że firma Trey Research może łatwo udostępniać pracownikom aplikacje na dowolnym urządzeniu.  

###  <a name="BKMK_ScenarioUnify"></a>Przykładowy scenariusz: Jednolite Zarządzanie zgodnością urządzeń  
 Firma Trey Research oczekuje jednolitego rozwiązania w zakresie zarządzania klientami obejmującego aktualizowane automatycznie oprogramowanie antywirusowe. To znaczy:  

-   Zapora systemu Windows jest włączona.  
-   Krytyczne aktualizacje oprogramowania są instalowane.  
-   Określone klucze rejestru są ustawione.  
-   Zarządzanych urządzeń przenośnych nie można instalować ani uruchamiać niepodpisanych aplikacji.  

Ponadto firma chce rozszerzyć tę ochronę na komputery przenośne łączące się zarówno z siecią intranet jak i Internetem.  

Adam mapuje te wymagania firmy do następujących scenariuszy:  

|Wymaganie|Bieżący stan zarządzania klientami|Przyszły stan zarządzania klientami|  
|-----------------|-------------------------------------|------------------------------------|  
|Na wszystkich komputerach działa oprogramowanie chroniące przed złośliwym kodem z aktualnymi plikami definicji i jest włączona Zapora systemu Windows.|Na różnych komputerach działają różne ochrony przed złośliwym oprogramowaniem rozwiązania, które nie zawsze są aktualne. Mimo że Zapora systemu Windows jest domyślnie włączona, użytkownicy czasami ją wyłączają.<br /><br /> W przypadku wykrycia na komputerze złośliwego oprogramowania użytkownicy mają się kontaktować z działem pomocy technicznej.|Na wszystkich komputerach działa to samo oprogramowanie chroniące przed złośliwym kodem, automatycznie pobierające najnowsze pliki aktualizacji definicji i automatycznie włączające Zaporę systemu Windows w razie wyłączenia jej przez użytkownika.<br /><br /> W przypadku wykrycia złośliwego oprogramowania dział pomocy technicznej jest powiadamiany automatycznie za pomocą poczty elektronicznej.|  
|Krytyczne aktualizacje oprogramowania są instalowane na wszystkich komputerach w ciągu miesiąca od ich wydania.|Mimo że aktualizacje oprogramowania są instalowane na komputerach, wiele komputerów nie instaluj automatycznie krytyczne aktualizacje oprogramowania do dwóch lub trzech miesięcy od ich w przypadku wydania. Przez ten czas komputery są narażone na ataki.<br /><br /> Dla komputerów, które nie należy instalować krytyczne aktualizacje oprogramowania pomocy technicznej wysyła najpierw wiadomości e-mail, prosząc użytkowników do zainstalowania aktualizacji. W razie zignorowania tej prośby inżynierowie działu pomocy technicznej łączą się zdalnie z odpowiednimi komputerami i instalują brakujące aktualizacje oprogramowania ręcznie.|Zwiększona obecnego stopnia zgodności w danym miesiącu do ponad 95% bez wysyłania wiadomości e-mail lub proszenia działu pomocy technicznej o ręczne instalowanie aktualizacji.|  
|Ustawienia zabezpieczeń określonych aplikacji są regularnie sprawdzane i w razie potrzeby korygowane.|Na komputerach są zainstalowane złożone skrypty uruchamiania wymagające członkostwa w grupie komputerów w celu resetowania wartości rejestru określonych aplikacji.<br /><br /> Ponieważ skrypty są uruchamiane wyłącznie przy uruchamianiu, a niektóre komputery nie są wyłączane przez dni, dział pomocy technicznej nie może sprawdzić kilka konfiguracji z opóźnieniem.|Wartości rejestru są sprawdzane i automatycznie korygowane niezależnie od członkostwa w grupie komputerów lub ponownego uruchamiania komputera.|  
|Urządzenia przenośne nie może zainstalować lub uruchomić niebezpiecznych aplikacji.|Użytkownicy są proszeni o niepobieranie i nieuruchamianie potencjalnie niebezpiecznych aplikacji z Internetu. Nie ma jednak mechanizmów monitorowania i wymuszania tej reguły.|Urządzenia przenośne są zarządzane przy użyciu Microsoft Intune lub programu Configuration Manager automatycznie uniemożliwiają Instalowanie i uruchamianie niepodpisanych aplikacji.|  
|Komputery przenośne łączące się zarówno z siecią intranet jak i Internetem muszą być zabezpieczone.|Dla użytkowników, którzy podróżują często nie łączą za pośrednictwem połączenia VPN codziennie. Komputer przenośny staje się niezgodny z wymaganiami w zakresie zabezpieczeń.|Jedynym warunkiem, aby komputery przenośnie były zgodne z wymaganiami bezpieczeństwa, jest połączenie z Internetem. Użytkownicy nie mają zalogowanie się lub użyj połączenia sieci VPN.|  

 Aby spełnić te wymagania, Adam wykorzystuje te możliwości zarządzania programu Configuration Manager i opcje konfiguracji:  

-   Program Endpoint Protection  
-   Aktualizacje oprogramowania  
-   Ustawienia zgodności  
-   Zarządzanie urządzeniami przenośnymi  
-   Internetowe zarządzanie klientami  

Implementuje te wymagania przy użyciu kroków konfiguracji opisanych w poniższej tabeli:  

|Kroki konfiguracji|Wynik|  
|-------------------------|-------------|  
|ADAM konfiguruje ochronę punktu końcowego. ADAM umożliwia ustawienie klienta umożliwiające odinstalowywanie innych rozwiązań chroniących przed złośliwym kodem i włącza Zaporę systemu Windows. Konfiguruje zasady automatycznego wdrażania, aby komputery regularnie sprawdzały i instalowały najnowsze aktualizacje definicji.|Pojedyncze rozwiązanie chroniące przed złośliwym kodem pomaga chronić wszystkie komputery, obniżając koszty administracyjne do minimum. Dział pomocy technicznej jest powiadamiany automatycznie za pomocą wiadomości e-mail w przypadku wykrycia ochrony przed złośliwym oprogramowaniem można szybkie rozwiązanie problemów. i pomaga zapobiegać atakom na inne komputery.|  
|Aby zwiększyć stopień zgodności, Adam używa reguły automatycznego wdrażania, określa okna obsługi serwerów i sprawdza wady i zalety korzystania z funkcji Wake-on-LAN dla komputerów z włączoną hibernacją.|Zgodność w zakresie krytycznych aktualizacji oprogramowania zostaje zwiększona, przez co użytkownicy lub pracownicy działu pomocy technicznej muszą rzadziej instalować aktualizacje oprogramowania ręcznie.|  
|Adam korzysta z ustawień zgodności, aby sprawdzić, czy są obecne określone aplikacje. Po wykryciu aplikacji elementy konfiguracji sprawdzają wartości rejestru i korygują je automatycznie, gdy są one niezgodności.|Za pomocą elementów konfiguracji i linie bazowe konfiguracji, które są wdrożone na wszystkich komputerów i sprawdzania zgodności codziennie, nie są już potrzebne odrębne skrypty uzależnione od członkostwa komputera i ponowne uruchomienie komputera.|  
|Adam korzysta z ustawień zgodności przeznaczonych do zarejestrowanych urządzeń przenośnych i konfiguruje łącznik serwera Exchange w taki sposób, aby na urządzeniach przenośnych nie można było instalować i uruchamiać niepodpisanych aplikacji.|Ponieważ nie wolno niepodpisanych aplikacji, urządzenia przenośne są automatycznie chronione przed potencjalnie szkodliwymi aplikacjami.|  
|ADAM upewnia się, że serwery systemu lokacji i komputery mają certyfikaty PKI wymagane przez program Configuration Manager do połączeń HTTPS. Następnie instaluje dodatkowe role systemu lokacji w sieci obwodowej, które akceptują połączenia klienckie z Internetu.|Komputery łączące się zarówno z siecią intranet jak i Internetem będą nadal automatycznie zarządzane przez program Configuration Manager po uzyskaniu połączenia z Internetem. Te komputery nie należy polegać na użytkownikom zalogować się do swojego komputera lub nawiązywanie połączenia z siecią VPN.<br /><br /> Te komputery będą nadal zarządzane w zakresie ochrony przed złośliwym kodem, Zapory systemu Windows, aktualizacji oprogramowania i elementów konfiguracji, co przełoży się na automatyczne zwiększenie poziomów zgodności.|  

 Te czynności konfiguracyjne i wyniki sprawią, że firma Trey Research pomyślnie ujednolici zarządzanie zgodnością urządzeń.  

###  <a name="BKMK_ScenarioSimplify"></a>Przykładowy scenariusz: Uprościć zarządzanie urządzeniami klienckimi  
 Firma Trey Research chce wszystkich nowych komputerach będzie automatycznie instalowany firmy podstawowy obraz komputera z systemem Windows 7. Po zainstalowaniu obrazu systemu operacyjnego na tych komputerach musi być zarządzane i monitorowane pod kątem dodatkowego oprogramowania instalowanego przez użytkowników. Komputery przechowujące poufne dane wymagają bardziej restrykcyjnych zasad zarządzania niż pozostałe komputery. Na przykład, inżynierowie działu pomocy technicznej nie mogą łączyć się z takimi komputerami zdalnie, w celu ich ponownego uruchomienia musi zostać wprowadzony numer PIN funkcji BitLocker i jedynie administratorzy lokalni mogą instalować na nich oprogramowanie.  

 Adam mapuje te wymagania firmy do następujących scenariuszy:  

|Wymaganie|Bieżący stan zarządzania klientami|Przyszły stan zarządzania klientami|  
|-----------------|-------------------------------------|------------------------------------|  
|Na nowych komputerach musi być zainstalowany system Windows 7.|Dział pomocy technicznej instaluje i konfiguruje system Windows 7 dla użytkowników, a następnie wysyła komputer do odpowiedniej lokalizacji.|Nowe komputery Przejdź wprost do miejsca przeznaczenia, zostają podłączone do sieci i automatycznego zainstalowania i skonfigurowania systemu Windows 7.|  
|Komputery muszą być zarządzane i monitorowane. W tym zbieranie danych spisu sprzętu i oprogramowania w celu określenia wymagań licencji.|Wdrożenie klienta programu Configuration Manager za pomocą automatyczną instalację wypychaną klienta. Dział pomocy technicznej sprawdza niepowodzenia instalacji i klientów, którzy nie wysyłaj danych dotyczących zapasów, gdy oczekuje się.<br /><br /> Dochodzi do awarii ze względu na zależności instalacji, które nie są spełnione i uszkodzenie usługi WMI na komputerze klienckim.|Dane dotyczące instalacji klienta i zapasów zbierane z komputerów są bardziej niezawodne i wymagają mniejszej liczby interwencji pracowników działu pomocy technicznej. Raporty zawierają dane użycia oprogramowania umożliwiające uzyskanie informacji o licencji.|  
|Niektóre komputery muszą mieć bardziej rygorystyczne zasady zarządzania.|Ze względu na bardziej rygorystyczne zasady zarządzania takie komputery obecnie nie są zarządzane przez program Configuration Manager.|Te komputery są zarządzane przy użyciu programu Configuration Manager, aby dopasować wyjątków, bez dodatkowych kosztów administracyjnych.|  

 Aby spełnić te wymagania, Adam wykorzystuje te możliwości zarządzania programu Configuration Manager i opcje konfiguracji:  

-   Wdrożenie systemu operacyjnego  
-   Wdrożenie klienta i stan klienta  
-   Ustawienia zgodności  
-   Ustawienia klienta  
-   Metody spisu i analizy zasobów  
-   Administracja oparta na rolach  

Implementuje te wymagania przy użyciu kroków konfiguracji opisanych w poniższej tabeli:  

|Kroki konfiguracji|Wynik|  
|-------------------------|-------------|  
|ADAM przechwytuje obraz systemu operacyjnego z komputera z zainstalowanym systemem Windows 7 i jest skonfigurowany zgodnie ze specyfikacją firmy. Następnie wdraża system operacyjny na nowych komputerach za pomocą obsługi nieznanych komputerów i środowiska PXE. Instaluje również klienta programu Configuration Manager w ramach wdrażania systemu operacyjnego.|Nowe komputery są gotowe do działania szybciej bez żadnej interwencji ze strony zespołu pomocy technicznej.|  
|ADAM konfiguruje automatyczną całej lokacji instalację wypychaną klienta do zainstalowania klienta programu Configuration Manager na wszystkich komputerach, które zostały wykryte. Dzięki temu, że wszystkie komputery, których nie utworzono z klientem, nadal instalują klienta, aby komputer mógł być zarządzany przez program Configuration Manager.<br /><br /> Adam konfiguruje stan klienta tak, aby automatycznie korygował wszystkie wykryte problemy z klientem. Konfiguruje także ustawienia klienta, które włączają zbieranie danych magazynu jest wymagany oraz konfigurowanie analizy zasobów.|Instalacja klienta razem z systemem operacyjnym jest szybsza i bardziej niezawodna niż oczekiwania programu Configuration Manager, aby odnaleźć komputer, a następnie próba instalacji plików źródłowych klienta na komputerze. Jednakże, pozostawiając automatycznej instalacji wypychanej opcja jest włączona, należy podać metodę tworzenia kopii zapasowej dla komputera, który ma już systemu operacyjnego, można zainstalować klienta, gdy komputer połączy się z siecią.<br /><br /> Ustawienia klienta zapewniają, że klienci regularnie wysyłają do lokacji informacje o magazynie. Oprócz badania stanu klienta ułatwia to utrzymanie działania klientów przy minimalnej interwencji pracowników działu pomocy technicznej. Na przykład są automatycznie wykrywane i usuwane uszkodzenia usługi WMI.<br /><br /> Raporty analizy zasobów ułatwiają monitorowanie wykorzystania i licencji oprogramowania.|  
|ADAM tworzy kolekcję komputerów, które muszą mieć bardziej rygorystyczne ustawienia zasad. Następnie tworzy niestandardowe ustawienia urządzenia klienckiego dla tej kolekcji, wyłącza zdalnego sterowania, który umożliwia wprowadzanie numeru PIN funkcji BitLocker i umożliwia tylko lokalni administratorzy instalowanie oprogramowania.<br /><br /> ADAM konfiguruje administracji opartej na rolach, aby inżynierowie działu pomocy technicznej nie widzieli tej kolekcji komputerów. Pomaga to zapewnić, że te komputery nie są przypadkowo zarządzane jak standardowe komputery.|Te komputery są teraz zarządzane przez program Configuration Manager, ale przy użyciu konkretnych ustawień, które nie wymagają nowej lokacji.<br /><br /> Kolekcja tych komputerów nie są widoczne, aby inżynierowie działu pomocy technicznej. Pozwala to zmniejszyć prawdopodobieństwo komputerów przypadkowo wysyłane wdrożeń i skryptów dla standardowych komputerów.|  

 Te czynności konfiguracyjne i wyniki sprawią, że firma Trey Research pomyślnie ujednolici zarządzanie urządzeniami klienckimi.  

##  <a name="BKMK_NextSteps"></a> Następne kroki  
 Przed zainstalowaniem programu Configuration Manager należy zaznajomić się z niektórymi podstawowymi koncepcjami i terminami specyficznymi dla programu Configuration Manager.  

-   Jeśli znasz System Center 2012 Configuration Manager, zobacz [co zostało zmienione w programie System Center Configuration Manager z programu System Center 2012 Configuration Manager](../../core/plan-design/changes/what-has-changed-from-configuration-manager-2012.md) Aby poznać nowe funkcje.  
-   Szczegółowe techniczne omówienie programu System Center Configuration Manager, można znaleźć w temacie [podstawy programu System Center Configuration Manager](../../core/understand/fundamentals.md).  

Jeśli znasz podstawowe koncepcje, korzystając z dokumentacji programu System Center Configuration Manager, aby ułatwić pomyślne wdrożenie i używanie programu Configuration Manager.  

