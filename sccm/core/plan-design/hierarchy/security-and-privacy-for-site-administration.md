---
title: "Witryny Administracja Zabezpieczenia i prywatność"
titleSuffix: Configuration Manager
description: "Optymalizuj zabezpieczeń i prywatności dotyczące administrowania lokacją w programie System Center Configuration Manager."
ms.custom: na
ms.date: 3/1/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1d58176e-abc0-4087-8583-ce70deb4dcf5
caps.latest.revision: "8"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 8ac421cca154f99251c13e1dcd0bed21e5b68078
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="security-and-privacy-for-site-administration-in-system-center-configuration-manager"></a>Zabezpieczenia i prywatność w kontekście administrowania lokacją w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Ten temat zawiera bezpieczeństwa i informacje o ochronie prywatności dotyczące programu System Center Configuration Manager lokacji i hierarchii.

##  <a name="BKMK_Security_Sites"></a>Najlepsze rozwiązania dotyczące administrowania lokacją  
 Użyj poniższe najlepsze rozwiązania ułatwiające bezpiecznych witryn programu System Center Configuration Manager i hierarchii.  

 **Uruchamiaj Instalatora tylko z zaufanego źródła i bezpieczny kanał komunikacji między nośnikiem z Instalatorem a serwerem lokacji.**  

 Aby zapobiec naruszeniu plików źródłowych, należy uruchomić Instalatora z zaufanego źródła. W przypadku składowania plików w sieci zabezpiecz lokalizację sieciową.  

 Jeśli użytkownik uruchamia Instalatora z lokalizacji sieciowej, aby zapobiec naruszeniu plików zgodnie z ich przesyłania przez sieć, osoba atakująca korzystać z protokołu IPsec lub bloku komunikatów serwera (SMB) podpisywania między lokalizację źródłową plików Instalatora a serwerem lokacji.  

 Ponadto jeśli używasz narzędzia pobierania Instalatora do pobierania plików, które są wymagane przez Instalatora, upewnij się, zabezpieczyć także lokalizacji, gdzie pliki te są przechowywane i po uruchomieniu Instalatora należy zabezpieczyć kanał komunikacji dla tej lokalizacji.  

 **Rozszerzenie schematu usługi Active Directory dla programu System Center Configuration Manager i Publikuj Lokacje w usługach domenowych w usłudze Active Directory.**  

 Rozszerzenia schematu nie są wymagane do uruchomienia programu System Center Configuration Manager, ale faktycznie tworzą one bezpieczniejsze środowisko, ponieważ klienci programu Configuration Manager i serwery lokacji mogą pobierać informacje z zaufanego źródła.  

 Jeśli klienci znajdują się w niezaufanej domenie, należy wdrożyć następujące role systemu lokacji w domenach klientów:  

-   Punkt zarządzania  

-   Punkt dystrybucji  

-   Punkt witryny sieci Web wykazu aplikacji  

> [!NOTE]  
>  Domenie zaufanej dla programu Configuration Manager wymaga uwierzytelniania Kerberos. Oznacza to, że jeśli klienci znajdują się w innym lesie, który nie ma zaufanie dwukierunkowe lasu z lasem serwera lokacji, klienci są uważane w niezaufanej domenie. Zaufanie zewnętrzne w tym przypadku nie jest wystarczające.  

 **Użyj protokołu IPsec do zabezpieczenia komunikacji między serwerami systemu lokacji a lokacjami.**  

 Mimo że programu Configuration Manager zabezpiecza komunikację między serwerem lokacji i komputerze z uruchomionym programem SQL Server, programu Configuration Manager nie zabezpieczenia komunikacji między rolami systemu lokacji i programu SQL Server. Używanie protokołu HTTPS do komunikacji wewnątrz danej lokacji można skonfigurować tylko w niektórych systemach lokacji (w punkcie rejestracji i punkcie usługi sieci Web Katalogu aplikacji).  

 Jeśli nie zabezpieczy się kanałów serwer-serwer dodatkowymi środkami, osoby atakujące mogą wykorzystać przeciwko systemom lokacji rozmaite rodzaje ataków fałszujących i ataków typu man-in-the-middle. Jeśli nie można użyć protokołu IPsec, należy użyć funkcji podpisywania SMB.  

> [!NOTE]  
>  Szczególnie ważne jest zabezpieczenie kanału komunikacyjnego między serwerem lokacji a serwerem źródłowym pakietu. Ta komunikacja wykorzystuje protokół SMB. Jeśli do zabezpieczenia tej komunikacji nie można użyć protokołu IPsec, użyj podpisywania SMB w celu upewnienia się, że pliki nie zostaną przez nikogo naruszone, zanim klienci pobiorą je i uruchomią.  

 **Nie zmieniaj grup zabezpieczeń, które program Configuration Manager tworzy i którymi zarządza w zakresie komunikacji systemu lokacji.**  

 Grupy zabezpieczeń:  

-   **SMS_SiteSystemToSiteServerConnection_MP_&lt;Kod_lokacji\>**  

-   **SMS_SiteSystemToSiteServerConnection_SMSProv_&lt;Kod_lokacji\>**  

-   **SMS_SiteSystemToSiteServerConnection_Stat_&lt;Kod_lokacji\>**  

Menedżer konfiguracji automatycznie tworzy i którymi zarządza tych grup zabezpieczeń. Obejmuje to między innymi usuwanie kont komputerów wraz z usunięciem roli systemu lokacji.  

W celu zapewnienia ciągłości usługi i najniższego stopnia uprawnień nie należy edytować tych grup ręcznie.  

**Jeśli klienci nie mogą wysyłać zapytań serwera wykazu globalnego o informacje programu Configuration Manager, Zarządzaj procesem udostępniania klucza zaufanych certyfikatów głównych.**  

Jeśli klienci nie mogą wysyłać zapytań wykazu globalnego informacji programu Configuration Manager, muszą polegać na zaufanego klucza głównego w celu uwierzytelniania prawidłowych punktów zarządzania. Zaufany klucz główny, który jest przechowywany w rejestrze klienta, można ustawiać za pomocą zasad grupy lub konfiguracji ręcznej.  

Jeśli klient nie ma kopii zaufanego klucza głównego, zanim po raz pierwszy skontaktuje się z punktem zarządzania, to ufa pierwszemu punktowi zarządzania, z którym się komunikuje. W celu ograniczenia ryzyka błędnego skierowania klientów do nieautoryzowanego punktu zarządzania przez osobę postronną można wstępnie udostępnić klientom zaufany klucz główny. Aby uzyskać więcej informacji, zobacz [planowanie zaufanego klucza głównego](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForRTK).  

**Używaj numerów portów innych niż domyślne.**  

Przy użyciu numerów portów innych niż domyślne można zapewnić dodatkową ochronę, ponieważ ich utrudnić osobom atakującym eksplorację środowiska i przygotowanie ataku. Jeśli zdecydujesz się używać portów innych niż domyślne, Zaplanuj je przed zainstalowaniem programu Configuration Manager i używaj ich konsekwentnie we wszystkich lokacjach w hierarchii. Porty żądań klientów i funkcji Wake On LAN to przykłady, których można użyć numerów portów innych niż domyślne.  

**Używaj separacji ról w systemach lokacji.**  

Choć można by zainstalować wszystkie role systemu lokacji na jednym komputerze, w sieciach produkcyjnych jest to rzadko praktykowane, ponieważ tworzy się w ten sposób pojedynczy punkt awarii.  

**Zredukuj zasięg potencjalnego ataku.**  

Izolowanie każdej roli systemu lokacji na innym serwerze zmniejsza ryzyko, że atak wykorzystujący lukę w systemie jedna lokacja może być używany dla systemu innej lokacji. Wiele ról systemu lokacji wymagają instalacji programu Internetowe usługi informacyjne (IIS) w systemie lokacji, i zwiększa obszar narażony na ataki. Jeśli w celu zmniejszenia inwestycji w sprzęt zachodzi potrzeba łączenia ze sobą niektórych ról systemu lokacji, należy łączyć role systemu lokacji wymagające usług IIS tylko z innymi rolami systemu lokacji wymagającymi usług IIS.  

> [!IMPORTANT]  
>  Wyjątek stanowi rola rezerwowego punktu stanu. Ponieważ ta rola systemu lokacji akceptuje od klientów dane nieuwierzytelnione, zalecamy nie kiedykolwiek przypisać rolę punktu stanu powrotu do żadnych innych Menedżera konfiguracji ról systemu lokacji.  


**Stosuj najlepsze rozwiązania w zakresie zabezpieczeń dotyczące systemu Windows Server i we wszystkich systemach lokacji uruchamiaj Kreatora konfiguracji zabezpieczeń.**  

Kreator konfiguracji zabezpieczeń pomaga utworzyć zasady zabezpieczeń, które można zastosować do dowolnego serwera w danej sieci. Po zainstalowaniu szablonu programu System Center Configuration Manager, Kreator konfiguracji zabezpieczeń rozpoznaje role systemu lokacji programu Configuration Manager, usługi, porty i aplikacje. Umożliwia ona następnie komunikacji, który jest wymagany dla programu Configuration Manager i blokuje komunikację niewymaganą.  

Kreator konfiguracji zabezpieczeń to element zestawu narzędzi programu System Center 2012 Configuration Manager, który można pobrać z Microsoft Download Center: [System Center 2012 — Configuration Manager dodatki i rozszerzenia składnika](http://go.microsoft.com/fwlink/p/?LinkId=251931).  

**Skonfiguruj dla systemów lokacji statyczne adresy IP.**  

Statyczne adresy IP jest łatwiej chronić przed atakami polegającymi na rozpoznawaniu nazw.  

Statyczne adresy IP również ułatwić konfigurację protokołu IPsec. Za pomocą protokołu IPsec jest najlepszą praktyką zabezpieczeń w zakresie zabezpieczania komunikacji między systemami lokacji w programie Configuration Manager.  

**Nie instaluj innych aplikacji na serwerach systemu lokacji.**  

Podczas instalowania innych aplikacji na serwerach systemu lokacji zwiększa obszar narażony na atak dla programu Configuration Manager i problemy z niezgodnością ryzyka.  

**Wymagaj podpisywania i włącz szyfrowanie jako opcję lokacji.**  

Włącz dla lokacji opcje podpisywania i szyfrowania. Upewnij się, że wszyscy klienci mogą obsługuje algorytm wyznaczania wartości skrótu SHA-256, a następnie włącz opcję **algorytm SHA-256 wymagany**.  

**Ogranicz i Monitoruj użytkowników administracyjnych programu Configuration Manager i użyć administracji opartej na rolach, aby przyznać Ci użytkownicy minimalne uprawnienia, których wymagają.**  

Przyznać dostęp administracyjny do programu Configuration Manager tylko do użytkowników, którym ufasz, a następnie przyznać im minimum uprawnień za pomocą wbudowanych ról zabezpieczeń lub dostosowując role zabezpieczeń. Użytkownicy administracyjni, którym można tworzyć, modyfikować i wdrażać aplikacji, sekwencji zadań, aktualizacje oprogramowania, elementy konfiguracji i linie bazowe konfiguracji, mogą potencjalnie sterować urządzeniami w hierarchii programu Configuration Manager.  

Przeprowadzaj okresowe inspekcje przypisań użytkowników administracyjnych oraz ich poziomu autoryzacji i weryfikuj wymagane zmiany.  

Więcej informacji o konfigurowaniu administracji opartej na rolach znajduje się w temacie [Konfigurowanie administracji opartej na rolach](../../../core/servers/deploy/configure/configure-role-based-administration.md).  

**Zabezpieczenie kopii zapasowych programu Configuration Manager i kanał komunikacyjny używany podczas tworzenia kopii i przywracania.**  

Podczas wykonywania kopii zapasowej programu Configuration Manager, informacje te obejmują certyfikaty i inne dane poufne, które mogłyby zostać użyte przez osobę atakującą do personifikacji.  

Używaj podpisywania protokołu SMB lub protokołu IPsec podczas transferu tych danych w sieci, a ponadto zabezpiecz lokalizację kopii zapasowych.  

**Zawsze, gdy eksportu lub importu obiektów z konsoli programu Configuration Manager do lokalizacji sieciowej, Zabezpiecz lokalizację i kanał sieciowy.**  

Ogranicz dostęp użytkowników do danego folderu sieciowego.  

Za pomocą podpisywania SMB lub protokołu IPsec między lokalizacją sieciową a serwerem lokacji oraz między komputerem z systemem Menedżer konfiguracji serwera konsoli i lokacji, aby zapobiec naruszeniu wyeksportowanych danych przez osobę atakującą. Używaj protokołu IPsec do szyfrowania danych w sieci, aby zapobiec ujawnieniu informacji.  

**Jeśli system lokacji nie jest poprawnie odinstalowany lub przestanie działać i nie można przywrócić, należy ręcznie usunąć certyfikaty programu Configuration Manager dla tego serwera przez inne serwery programu Configuration Manager.**  

Aby usunąć uległ awarii, które zostało ustanowione początkowo za pomocą systemu lokacji i ról systemu lokacji, Usuń ręcznie certyfikaty programu Configuration Manager na serwerze nie powiodło się w **zaufane osoby** magazynu certyfikatów na innych serwerach systemu lokacji. Jest to szczególnie istotne, jeśli zmienia się przeznaczenie serwera bez ponownego formatowania go.  

Aby uzyskać więcej informacji na temat tych certyfikatów, zobacz sekcję **formanty kryptograficzne komunikacji z serwerem** w [szyfrowania określa informacje techniczne dotyczące programu System Center Configuration Manager](../../../protect/deploy-use/cryptographic-controls-technical-reference.md).  

**Nie konfiguruj w internetowych systemach lokacji łączenia sieci obwodowej z intranetem.**  

Nie Konfiguruj serwerów systemu lokacji jako wieloadresowych, tak aby łączą się z siecią obwodową i intranetem. Choć tego typu konfiguracja pozwala internetowym systemom lokacji na akceptowanie połączeń klienckich zarówno z Internetu, jak i z intranetu, to eliminuje równocześnie granicę zabezpieczeń między siecią obwodową i intranetem.  

**Jeśli serwer systemu lokacji znajduje się w sieci niezaufanej (takiej jak sieć obwodowa), skonfiguruj serwer lokacji do inicjowania połączeń z systemem lokacji.**  

Domyślnie to systemy lokacji inicjują połączenia z serwerem lokacji w celu transferu danych, co może stanowić zagrożenie bezpieczeństwa, kiedy inicjowanie połączenia następuje z sieci niezaufanej do zaufanej. W przypadku gdy systemy lokacji akceptują połączenia przychodzące z Internetu lub znajdują się w lesie niezaufanym, skonfiguruj opcję systemu lokacji **Wymagaj inicjowania przez serwer lokacji połączeń z tym systemem lokacji** tak, aby po instalacji systemu lokacji i ewentualnych ról systemu lokacji wszystkie połączenia były inicjowane z sieci zaufanej.  

**W przypadku korzystania z serwera proxy sieci Web do internetowego zarządzania klientami stosuj mostkowanie SSL, które obejmuje kończenie żądań SSL z uwierzytelnianiem.**  

 Po skonfigurowaniu kończenia żądań SSL na serwerze proxy sieci Web pakiety z Internetu są poddawane inspekcji przed przekazaniem ich do sieci wewnętrznej. Serwer proxy sieci web uwierzytelnia połączenie nawiązywane przez klienta, kończy je, a następnie nawiązuje nowe uwierzytelnione połączenie z internetowymi systemami lokacji.  

 Gdy klientów programu Configuration Manager umożliwia łączą się z systemami lokacji internetowy serwer proxy sieci web, tożsamość klienta (identyfikator GUID) jest bezpiecznie przechowywana w ładunku pakietu, dzięki czemu punkt zarządzania nie traktuje serwera proxy sieci web jako klienta. Jeśli dany serwer proxy sieci Web nie spełnia wymagań pozwalających na obsługę mostkowania SSL, obsługiwane jest także tunelowanie SSL. To mniej bezpieczna opcja, ponieważ pakiety SSL z Internetu są przekazywane do systemów lokacji bez zakończenia żądań SSL, a tym samym nie można przeprowadzić ich inspekcji pod kątem złośliwej zawartości.  

 Jeśli dany serwer proxy sieci Web nie spełnia wymagań pozwalających na obsługę mostkowania SSL, możesz zastosować tunelowanie SSL. To jednak mniej bezpieczna opcja, ponieważ pakiety SSL z Internetu są przekazywane do systemów lokacji bez zakończenia żądań SSL, a tym samym nie można przeprowadzić ich inspekcji pod kątem złośliwej zawartości.  

> [!WARNING]  
>  Urządzenia przenośne, które są zarejestrowane przez program Configuration Manager nie można użyć mostkowania SSL i muszą korzystać z tunelowania SSL.  

**Konfiguracje, których należy używać w przypadku konfigurowania lokacji do wznawiania komputerów w celu zainstalowania oprogramowania.**  

-   Jeśli używasz tradycyjnych pakietów wznawiania, użyj emisji pojedynczej, a nie emisji skierowanych do podsieci.  

-   Jeśli należy użyć emisje skierowane do podsieci, skonfiguruj routery, aby zezwalały na emisje skierowane do adresu IP tylko z serwera lokacji i tylko na numer portu inny niż domyślny.  

Aby uzyskać więcej informacji o różnych technologiach Wake On LAN, zobacz [planowanie sposobu wznawiania działania klientów w programie System Center Configuration Manager](../../../core/clients/deploy/plan/plan-wake-up-clients.md).

**W przypadku używania powiadomień e-mail należy skonfigurować dostęp uwierzytelniony do serwera poczty SMTP.**  

Jeśli to możliwe, Użyj serwera poczty obsługującego dostęp uwierzytelniony, a konto komputera serwera lokacji na użytek uwierzytelniania. W przypadku konieczności określenia konta użytkownika do uwierzytelniania należy użyć konta o najniższych uprawnieniach.  

##  <a name="BKMK_Security_SiteServer"></a>Najlepsze rozwiązania dotyczące serwera lokacji  
 Użyj poniższe najlepsze rozwiązania, aby zabezpieczyć serwer lokacji programu Configuration Manager.  

 **Instalowanie programu Configuration Manager na serwerze członkowskim w kontrolerze domeny.**  

 Systemy serwera i witryny lokacji programu Configuration Manager nie wymagają instalacji w kontrolerze domeny. Kontrolery domeny nie mają innej bazy danych domeny niż lokalna baza danych zarządzania kontami zabezpieczeń (SAM). Po zainstalowaniu programu Configuration Manager na serwerze członkowskim, można zachować konta programu Configuration Manager w lokalnej bazie danych SAM zamiast w bazie danych domeny.  

 Takie rozwiązanie zmniejsza również obszar kontrolerów domeny narażony na ataki.  

 **Zainstaluj lokacje dodatkowe, unikając kopiowania plików na serwer lokacji dodatkowej za pośrednictwem sieci.**  

 Po uruchomieniu Instalatora i utworzeniu lokacji dodatkowej, nie wybieraj opcji, aby skopiować pliki z lokacji nadrzędnej do lokacji dodatkowej, a nie używać sieciowej lokalizacji źródłowej. Podczas kopiowania plików za pośrednictwem sieci doświadczona osoba atakująca może przejąć pakiet instalacyjny lokacji dodatkowej i naruszyć pliki przed ich zainstalowaniem, mimo że synchronizacja takiego ataku jest trudna. Aby zapobiec takim atakom, należy użyć protokołu IPsec lub SMB podczas przesyłania plików.  

 Zamiast kopiować pliki za pośrednictwem sieci, na serwerze lokacji dodatkowej, należy skopiować pliki źródłowe z folderu nośnika do folderu lokalnego. Następnie, po uruchomieniu Instalatora, aby utworzyć lokację dodatkową na **plików źródłowych instalacji** wybierz pozycję **Użyj plików źródłowych w następującej lokalizacji na komputerze lokacji dodatkowej (najbezpieczniejsza opcja)**, i określ ten folder.  

 Aby uzyskać więcej informacji, zobacz sekcję [Install a secondary site](../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md#bkmk_secondary)(Instalacja lokacji dodatkowej) w temacie [Use the SetupWizard to install sites](../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md) (Instalowanie lokacji za pomocą Kreatora instalacji).  

##  <a name="BKMK_Security_SQLServer"></a>Najlepsze rozwiązania dotyczące programu SQL Server  
 Configuration Manager używa programu SQL Server jako wewnętrznej bazy danych. W przypadku złamania zabezpieczeń bazy danych osoby atakujące mogą obejścia programu Configuration Manager i dostęp do programu SQL Server bezpośrednio do przeprowadzania ataków za pośrednictwem programu Configuration Manager. Należy wziąć pod uwagę ataków na program SQL Server do bardzo duże ryzyko i ograniczenia odpowiednio.  

 Aby zabezpieczyć program SQL Server dla programu Configuration Manager, należy użyć poniższe najlepsze rozwiązania.  

 **Nie należy używać serwera bazy danych lokacji programu Configuration Manager do uruchamiania innych aplikacji SQL Server.**  

 Wraz ze zwiększeniem dostępu do serwera bazy danych lokacji programu Configuration Manager wzrasta zagrożenie danych programu Configuration Manager. W przypadku złamania zabezpieczeń bazy danych lokacji programu Configuration Manager, inne aplikacje na tym samym komputerze serwera SQL są następnie również zagrożenie.  

 **Skonfiguruj program SQL Server, aby używał uwierzytelniania systemu Windows.**  

 Mimo że programu Configuration Manager ma dostęp do bazy danych lokacji przy użyciu konta systemu Windows i uwierzytelnianie systemu Windows, jest nadal możliwe skonfigurować program SQL Server do używania trybu mieszanego programu SQL Server. Tryb mieszany programu SQL Server umożliwia dodatkowe logowania SQL dostęp do bazy danych, która nie jest wymagane i zwiększa obszar narażony na ataki.  

 **Wykonaj dodatkowe czynności, aby zainstalować w lokacjach dodatkowych używających programu SQL Server Express najnowsze aktualizacje oprogramowania.**  

 Po zainstalowaniu lokacji głównej programu Configuration Manager pobiera z Microsoft Download Center SQL Server Express i kopiuje pliki na serwerze lokacji głównej. Po instalacji lokacji dodatkowej i wybraniu opcji instalacji programu SQL Server Express, programu Configuration Manager przeprowadza instalację wcześniej pobranej wersji, nie sprawdzając, czy są dostępne nowe wersje. Aby upewnić się, że w lokacji dodatkowej są najnowsze wersje, wykonaj jedną z następujących czynności:  

-   Po zainstalowaniu lokacji dodatkowej Uruchom usługę Windows Update na serwerze lokacji dodatkowej.  

-   Przed zainstalowaniem lokacji dodatkowej ręcznie zainstaluj najnowszą wersję programu SQL Server Express i wszystkie dostępne aktualizacje oprogramowania na komputerze obsługującym serwer lokacji dodatkowej. Następnie instalacji lokacji dodatkowej, a następnie wybierz opcję użycia istniejącego wystąpienia programu SQL Server.  

Okresowo uruchamiaj usługę Windows Update w ramach tych lokacji i wszystkich zainstalowanych wersji programu SQL Server w celu upewnienia się, że mają zainstalowane najnowsze aktualizacje oprogramowania.  

**Stosuj najlepsze rozwiązania w zakresie programu SQL Server.**  

Określ i stosuj najlepsze rozwiązania dla używanej wersji programu SQL Server. Jednak należy wziąć pod uwagę następujące wymagania dla programu Configuration Manager:  

-   Konto komputera serwera lokacji musi być członkiem grupy administratorów na komputerze z programem SQL Server. Jeśli wykonujesz zalecenie programu SQL Server "jawnego udostępniania podmiotów zabezpieczeń administratora", konto używane do uruchamiania Instalatora na serwerze lokacji musi być członkiem grupy użytkowników SQL.  

-   W przypadku instalowania programu SQL Server przy użyciu konta użytkownika domeny należy się upewnić, że konto komputera serwera lokacji ma skonfigurowaną główną nazwę usługi (SPN) publikowaną w usługach domenowych Active Directory. Bez nazwy SPN uwierzytelnianie Kerberos nie powiedzie się i Instalatora programu Configuration Manager zakończy się niepowodzeniem.  

##  <a name="BKMK_Security_IIS"></a>Najlepsze rozwiązania dotyczące systemów lokacji z usługami IIS  
Niektóre role systemu lokacji w programie Configuration Manager wymagają programu IIS. Proces zabezpieczania usług IIS umożliwia Configuration Manager, aby działać poprawnie i zmniejsza zagrożenie bezpieczeństwa. Gdy jest to przydatne zminimalizowanie liczby serwerów, które wymagają usług IIS. Uruchamiaj na przykład tylko punkty zarządzania niezbędne do obsługi bazy klientów, biorąc pod uwagę wysoką dostępność i izolację sieciową internetowego zarządzania klientami.  

 Aby zabezpieczyć systemy lokacji z uruchomionymi usługami IIS, należy stosować poniższe najlepsze rozwiązania w zakresie zabezpieczeń.  

 **Wyłącz funkcje usług IIS, które nie wymagają.**  

 Zainstaluj tylko minimalną wymaganą liczbę funkcji usług IIS w ramach instalowanej roli systemu lokacji. Aby uzyskać więcej informacji, zobacz [Site and site system prerequisites](../../../core/plan-design/configs/site-and-site-system-prerequisites.md) (Wymagania wstępne dotyczące lokacji i systemu lokacji).  

 **Skonfiguruj role systemu lokacji, aby wymagały połączenia za pośrednictwem protokołu HTTPS.**  

 Gdy klienci łączą się z systemem lokacji za pośrednictwem protokołu HTTP, a nie HTTPS, używają uwierzytelniania systemu Windows, co może spowodować powrót do uwierzytelniania przy użyciu protokołu NTLM zamiast protokołu Kerberos. W przypadku uwierzytelniania przy użyciu protokołu NTLM klienci mogą połączyć się z nieautoryzowanym serwerem.  

 Wyjątkiem od tego najlepszego rozwiązania w zakresie bezpieczeństwa mogą być punkty dystrybucji, ponieważ konta dostępu do pakietów nie działają w przypadku skonfigurowania dla punktu dystrybucji połączeń za pośrednictwem protokołu HTTPS. Konta dostępu do pakietów zapewniają autoryzację zawartości, dzięki czemu można określić użytkowników z uprawnieniami dostępu do danej zawartości. Aby uzyskać więcej informacji, zobacz [najlepsze rozwiązania dotyczące zarządzania zawartością](../../../core/plan-design/hierarchy/security-and-privacy-for-content-management.md#BKMK_Security_ContentManagement).  

**Skonfiguruj listę zaufania certyfikatów (CTL) w usługach IIS dla ról systemu lokacji.**  

Role systemu lokacji:  

-   Punkt dystrybucji, który jest skonfigurowany do obsługi protokołu HTTPS  

-   Punkt zarządzania, który jest skonfigurowany do obsługi protokołu HTTPS i włączyć do obsługi urządzeń przenośnych

Lista zaufania certyfikatów (CTL) to zdefiniowana lista zaufanych głównych urzędów certyfikacji. Korzystając z listy CTL z zasadami grupy i wdrażania infrastruktury kluczy publicznych (PKI), listy zaufania certyfikatów umożliwia uzupełnienie istniejących zaufanych głównych urzędów certyfikacji skonfigurowanych w sieci, takich jak te, które są automatycznie zainstalowane w systemie Microsoft Windows lub dodane przez główne urzędy certyfikacji przedsiębiorstwa z systemem Windows. Jednak po skonfigurowaniu listy CTL w usługach IIS definiuje ona podzestaw tych zaufanych głównych urzędów certyfikacji.  

Ten podzestaw zapewnia większą kontrolę zabezpieczeń, ponieważ lista CTL ogranicza akceptowane certyfikaty klienta wyłącznie do certyfikatów wystawionych przez urzędy certyfikacji znajdujące się na liście CTL. Na przykład system Windows jest dostarczany z liczbą certyfikatów urzędów certyfikacji dobrze znane, innych firm, takich jak VeriSign i Thawte.

Domyślnie komputer z uruchomionymi usługami IIS ufa certyfikatom powiązanym z tymi dobrze znanymi urzędami certyfikacji. Po skonfigurowaniu nie IIS listę CTL dla ról systemu lokacji, dowolne urządzenie z certyfikatem klienta wystawionym przez te urzędy certyfikacji jest akceptowane jako prawidłowy klient programu Configuration Manager. Konfigurowanie w usługach IIS listy CTL nie obejmującej tych urzędów certyfikacji spowoduje odrzucenie połączeń klienta, gdy jego certyfikat jest powiązany z tymi urzędami certyfikacji. Jednak dla klientów programu Configuration Manager, należy zaakceptować dla ról systemu lokacji na liście, można skonfigurować w usługach IIS listę CTL określającą urzędy certyfikacji, które są używane przez klientów programu Configuration Manager.  

> [!NOTE]  
>  Tylko role systemu lokacji na liście wymagają skonfigurowania w usługach IIS listy CTL. Z listy wystawców certyfikatów, który używa programu Configuration Manager dla punktów zarządzania zapewnia te same funkcje dla komputerów klienckich, gdy łączą się z punktami zarządzania HTTPS.  

Więcej informacji o sposobie konfigurowania listy zaufanych urzędów certyfikacji w usługach IIS znajduje się w dokumentacji usług IIS.  

**Nie umieszczaj serwera lokacji na komputerze z usługami IIS.**  

Rozdziele ról pozwala ograniczyć obszar narażony na ataki i ułatwia odzyskiwanie. Ponadto konto komputera serwera lokacji zwykle ma uprawnienia administracyjne, we wszystkich rolach systemu lokacji (i prawdopodobnie na klientach programu Configuration Manager, jeśli używasz instalacji wypychanej klienta).  

**Użyj dedykowanych serwerów usług IIS dla programu Configuration Manager.**  

Można hostować wiele aplikacji sieci web na serwerach usług IIS, które są również używane przez program Configuration Manager, takie rozwiązanie znacznie zwiększa obszar narażony na ataki. Nieprawidłowo skonfigurowane aplikacji umożliwia osobie atakującej przejąć kontrolę programu Configuration Manager z systemu lokacji, które osoba atakująca może przejąć kontrolę nad hierarchią.  

Jeśli inne aplikacje sieci Web muszą być wykonywane w systemach lokacji programu Configuration Manager, należy utworzyć niestandardową witrynę sieci web dla systemów lokacji programu Configuration Manager.  

**Użyj niestandardowej witryny sieci Web.**  

Dla systemów lokacji, na których działają usługi IIS można skonfigurować programu Configuration Manager do używania niestandardowej witryny sieci Web zamiast domyślnej witryny sieci Web dla usług IIS. Jeśli masz uruchamianie innych aplikacji sieci web w systemie lokacji, należy użyć niestandardowej witryny sieci Web. To ustawienie jest ustawienie całej lokacji, a nie ustawienia dla systemu określonej lokacji.  

Oprócz zapewnienia większego poziomu zabezpieczeń, niestandardowej witryny sieci web należy użyć w przypadku uruchamiania w systemie lokacji innych aplikacji sieci Web.  

**Jeśli po zainstalowaniu roli punktu dystrybucji zostanie wybrana niestandardowa witryna sieci web zamiast domyślnej, usuń domyślne katalogi wirtualne.**  

Jeśli zmienisz z domyślnej witryny sieci Web przy użyciu niestandardowej witryny sieci Web, programu Configuration Manager nie usuwa starych katalogów wirtualnych. Należy usunąć katalogi wirtualne, które utworzył jako domyślne witryny sieci Web programu Configuration Manager.  

Należy na przykład usunąć następujące katalogi wirtualne punktu dystrybucji:  

-   SMS_DP_SMSPKG$  

-   SMS_DP_SMSSIG$  

-   NOCERT_SMS_DP_SMSPKG$  

-   NOCERT_SMS_DP_SMSSIG$  

**Stosuj najlepsze rozwiązania w zakresie serwera usług IIS.**  

Określ i stosuj najlepsze rozwiązania dla używanej wersji serwera usług IIS. Jednak uwzględnia wszelkie wymagania, których dla określonych ról systemu lokacji programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [Site and site system prerequisites](../../../core/plan-design/configs/site-and-site-system-prerequisites.md) (Wymagania wstępne dotyczące lokacji i systemu lokacji).  

##  <a name="BKMK_Security_ManagementPoint"></a>Najlepsze rozwiązania dotyczące punktu zarządzania  
 Punkty zarządzania stanowią podstawowy interfejs między urządzeniami i programu Configuration Manager. Należy wziąć pod uwagę ataków na punkt zarządzania i serwera, który jest uruchamiany na bardzo duże ryzyko i odpowiednio ograniczyć. Zastosuj wszystkie odpowiednie najlepsze rozwiązania w zakresie zabezpieczeń i monitoruj działanie pod kątem nieprawidłowości.  

 Użyj poniższe najlepsze rozwiązania, aby zabezpieczyć punkt zarządzania w programie Configuration Manager.  

**Po zainstalowaniu klienta programu Configuration Manager w punkcie zarządzania przypisz go do lokacji tego punktu zarządzania.**  

 Unikaj scenariusz, w której jest przypisany klient programu Configuration Manager, który znajduje się w systemie lokacji punktu zarządzania do innej lokacji niż lokacja tego punktu zarządzania.  

 W przypadku migrowania z wcześniejszej wersji do programu System Center Configuration Manager, przeprowadź migrację oprogramowania klienckiego w punkcie zarządzania do programu System Center Configuration Manager tak szybko, jak to możliwe.  

##  <a name="BKMK_Security_FSP"></a>Najlepsze rozwiązania dotyczące rezerwowego punktu stanu  
 Jeśli zainstalujesz rezerwowy punkt stanu w programie Configuration Manager, należy użyć poniższe najlepsze rozwiązania.  

 Więcej informacji dotyczących zabezpieczeń w przypadku instalowania rezerwowego punktu stanu znajduje się w sekcji [Określanie, czy jest wymagany rezerwowy punkt stanu](../../../core/clients/deploy/plan/determine-the-site-system-roles-for-clients.md#determine-if-you-need-a-fallback-status-point).  


**Nie należy uruchamiać inne role systemu lokacji w systemie lokacji, a rezerwowego punktu stanu nie należy instalować na kontrolerze domeny.**  

 Rezerwowy punkt stanu umożliwia akceptowanie nieuwierzytelnionych połączeń z każdego komputera, dlatego uruchomienie tej roli systemu lokacji z innymi rolami lub w kontrolerze domeny znacznie zwiększa zagrożenie serwera.  

**Korzystając z certyfikatów PKI do komunikacji z klientem w programie Configuration Manager, należy zainstalować rezerwowy punkt stanu przed zainstalowaniem klientów.**  

 Jeśli systemy lokacji programu Configuration Manager nie akceptują połączeń HTTP klienta, może być niemożliwe klientów są zarządzane ze względu na problemy dotyczące certyfikatu PKI. Jeśli klienci są przypisywani do rezerwowego punkt stanu, te problemy dotyczące certyfikatu są zgłaszane przez rezerwowy punkt stanu.  

 Ze względów bezpieczeństwa nie można przypisać rezerwowego punktu stanu do klientów po ich zainstalowaniu. Zamiast tego tę rolę można przypisać tylko podczas instalacji klienta.  

**Unikaj korzystania z rezerwowego punkt stanu w sieci obwodowej.**  

 Zgodnie ze swoim przeznaczeniem rezerwowy punkt stanu akceptuje dane od każdego klienta. Mimo że rezerwowy punkt stanu w sieci obwodowej może ułatwiać rozwiązywanie problemów z klientami internetowymi, musisz również wziąć pod uwagę ryzyko akceptowania przez system lokacji nieuwierzytelnionych danych w publicznie dostępnej sieci.  

 Jeśli zainstalujesz rezerwowy punkt stanu w sieci obwodowej lub dowolnej niezaufanej sieci, należy skonfigurować serwer lokacji do inicjowania transferu danych, a nie przy użyciu domyślnego ustawienia umożliwia punktu stanu powrotu do nawiązania połączenia z serwerem lokacji.  

##  <a name="BKMK_SecurityIssues_Clients"></a>Problemy z bezpieczeństwem dotyczące administrowania lokacją  
 Przejrzyj następujące zagadnienia dotyczące zabezpieczeń programu Configuration Manager:  

-   Menedżer konfiguracji nie ma funkcji chroniącej przed autoryzowanym użytkownikiem administracyjnym, który używa programu Configuration Manager w celu przeprowadzania ataków na sieć. Nieautoryzowani użytkownicy administracyjni są duże zagrożenie dla bezpieczeństwa i mogą uruchamiać wiele ataków, które dotyczą następujących strategii:  

    -   Użycie funkcji wdrażania oprogramowania do automatycznego zainstalowania i uruchomienia złośliwego oprogramowania na każdym komputerze klienta programu Configuration Manager w przedsiębiorstwie.  

    -   Użyj zdalnego sterowania w celu przejęcia zdalnej kontroli klienta programu Configuration Manager bez pozwolenia.  

    -   Konfigurowanie krótkich interwałów sondowania i bardzo dużych magazynów w celu przeprowadzenia ataku typu „odmowa usługi” na klientów i serwery  

    -   Użycie jednej lokacji w hierarchii do zapisania danych w usłudze Active Directory w innej hierarchii  

    Hierarchia lokacji to granica bezpieczeństwa. Należy wziąć pod uwagę lokacjami wyłącznie jako granice zarządzania.  

    Nadzoruj wszystkie aktywności użytkowników administracyjnych i okresowo sprawdzaj dzienniki inspekcji. Wymagaj od wszystkich użytkowników administracyjnych programu Configuration Manager do poddania selekcji przed ich są sprawdzeni oraz Wymagaj okresowe umowy o pracę.  

-   W przypadku złamania zabezpieczeń punktu rejestracyjnego osoba atakująca może uzyskać certyfikaty służące do uwierzytelniania i skraść poświadczenia użytkowników, którzy rejestrują swoje urządzenia przenośne.  

    Punkt rejestracji komunikuje się z urzędem certyfikacji i może tworzyć, modyfikować i usuwać obiekty usługi Active Directory. Nigdy nie instaluj punktu rejestracyjnego w sieci obwodowej, a stałe monitorowanie pod kątem nietypowej aktywności.  

-   Jeśli zezwalasz na zasady użytkowników w ramach internetowego zarządzania klientami lub konfigurujesz punkt witryny sieci Web katalogu aplikacji dla użytkowników połączonych z Internetem, zwiększasz obszar narażony na ataki.  

    Oprócz używania certyfikatów PKI z połączeniami klient-serwer, te konfiguracje wymagają uwierzytelniania systemu Windows, co może spowodować powrót do uwierzytelniania przy użyciu protokołu NTLM zamiast protokołu Kerberos. Uwierzytelnianie NTLM jest narażone na podszywanie się i ataki przeprowadzane za pomocą metody powtórzeń. Aby pomyślnie uwierzytelnić użytkownika w Internecie, musisz zezwolić na połączenia z serwera internetowego systemu lokacji do kontrolera domeny.  

-   Na serwerach systemu lokacji jest wymagany udział Admin$.  

    Serwer lokacji programu Configuration Manager używa udziału Admin$ do nawiązania połączenia i wykonywać operacje usługi w systemach lokacji. Nie wyłączaj ani usuwaj udziału Admin$.  

-   Program Configuration Manager używa usług rozpoznawania nazw, do łączenia się z innymi komputerami, a te usługi są trudno ochronić przed takimi atakami, jak podszywanie się, naruszanie zawartości, możliwość wyparcia się, ujawnienie informacji, odmowę usługi i podniesienie uprawnień.  

    Zidentyfikuj najlepsze rozwiązania z zakresu bezpieczeństwa dotyczące wersji systemów DNS oraz WINS używanych z funkcją rozpoznawania nazw i przestrzegaj ich.  

##  <a name="BKMK_Privacy_Cliients"></a>Informacje o prywatności dotyczące odnajdywania  
 Odnajdywanie tworzy rekordy dotyczące zasobów sieciowych i przechowuje je w bazie danych programu System Center Configuration Manager. Rekordy danych odnajdywania zawierają informacje o komputerze, takie jak adresy IP, systemów operacyjnych i nazwy komputera. Metody odnajdowania dostępne w usłudze Active Directory można również skonfigurować do odnajdywania dowolnych informacji przechowywanych w usługach domenowych Active Directory.  

 Odnajdywanie pulsu to jedyna metoda odnajdowania jest domyślnie włączona, ale ta metoda tylko odnajduje komputery, które są już mieć zainstalowane oprogramowanie klienckie programu System Center Configuration Manager.  

 Informacje odnajdywania nie są wysyłane do firmy Microsoft. Zamiast tego jest ona przechowywana w bazie danych programu Configuration Manager. Informacje są przechowywane w bazie danych, dopóki zostanie usunięty co 90 dni przez zadanie obsługi lokacji **Usuń przestarzałe dane wykrywania**.  

 Przed skonfigurowaniem dodatkowych metod odnajdowania lub rozszerzenia metod odnajdowania w usłudze Active Directory należy wziąć pod uwagę wymogi związane z ochroną prywatności.  
