---
title: "Klient zabezpieczenia i prywatność | Dokumentacja firmy Microsoft"
description: "Dowiedz się więcej o zabezpieczeniach i prywatności dla klientów w programie System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: c1d71899-308f-49d5-adfa-3a3ec0163ed8
caps.latest.revision: "10"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: b354155d83ce6f3a14b13b98fb54e1f3bd2f54da
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2017
---
# <a name="security-and-privacy-for-clients-in-system-center-configuration-manager"></a>Bezpieczeństwo i prywatność klientów w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Ten artykuł zawiera bezpieczeństwa i informacje o ochronie prywatności dla klientów w programie System Center Configuration Manager i dla urządzeń przenośnych, które są zarządzane przez łącznik serwera Exchange:  

##  <a name="BKMK_Security_Cliients"></a>Najlepsze rozwiązania dotyczące klientów  
 Kiedy programu Configuration Manager akceptuje dane od urządzeń z klientem programu Configuration Manager, powstaje ryzyko ataku lokacji czy klientów. Klienci mogą na przykład wysłać nieprawidłowe zapasy lub podjąć próbę przeciążenia systemów lokacji. Wdrażanie klienta programu Configuration Manager wyłącznie na zaufanych urządzeniach. Ponadto należy się stosować do następujących rozwiązań dotyczących zabezpieczeń, aby chronić lokację przed urządzeniami nieautoryzowanymi lub ze złamanymi zabezpieczeniami:  

 **Do komunikacji z klientami z systemami lokacji, na których działają usługi IIS, należy użyć certyfikatów infrastruktury kluczy publicznych (PKI).**  

-   Konfiguruj **Ustawienia systemu lokacji** wyłącznie do obsługi **protokołu HTTPS**.  

-   Instaluj klientów, określając właściwość **/UsePKICert** programu CCMSetup  

-   Korzystaj z listy odwołania certyfikatów (CRL) i sprawdź, czy klienci i serwery komunikujące się mają do niej zawsze dostęp.  

 Te certyfikaty są wymagane dla klientów urządzeń przenośnych oraz połączeń internetowych z komputerami klienckimi i są zalecane do wszystkich połączeń klientów w sieci intranet (z wyjątkiem punktów dystrybucji).  

 Aby uzyskać więcej informacji o wymaganiach dotyczących certyfikatów PKI oraz korzystania z nich w celu ochrony programu Configuration Manager, zobacz [wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager](../../../../core/plan-design/network/pki-certificate-requirements.md).  

 **Automatycznie zatwierdzać komputery klienckie z zaufanych domen i ręcznie Sprawdź i zatwierdzać inne komputery**  

 Zatwierdzenie dla hierarchii można skonfigurować jako ręczne, automatyczne dla komputerów w zaufanych domenach lub automatyczne dla wszystkich komputerów. Najbezpieczniejszą metodą zatwierdzenia jest automatyczne zatwierdzenie klientów należących do zaufanych domen, a następnie ręczne sprawdzenie i zatwierdzenie wszystkich pozostałych komputerów. Automatyczne zatwierdzenie wszystkich klientów nie jest zalecane, chyba że użytkownik dysponuje innymi kontrolami dostępu, aby uniemożliwić niezaufanym komputerom dostęp do sieci.  

 Zatwierdzenie identyfikuje komputer zaufany, który ma być zarządzane przez program Configuration Manager, gdy nie można używać uwierzytelniania infrastruktury kluczy publicznych.  

 Aby uzyskać więcej informacji o sposobie ręcznego zatwierdzania komputerów, zobacz [Zarządzanie klientami z węzła Urządzenia](../../../../core/clients/manage/manage-clients.md#BKMK_ManagingClients_DevicesNode).  

 **Nie należy używać blokowania, aby uniemożliwić klientom dostęp do hierarchii programu Configuration Manager**  

 Zablokowani klienci są odrzucani przez infrastrukturę programu Configuration Manager, tak aby nie mogli komunikować się z systemami lokacji w celu pobrania zasad, wysyłania danych zapasów lub wysłać lub komunikatów o stanie. Jednak nie należy używać blokowania, aby chronić hierarchię programu Configuration Manager przed niezaufanymi komputerami, jeśli systemy lokacji akceptują połączenia klienta HTTP. Przy takim scenariuszu zablokowany klient może dołączyć ponownie do lokacji przy użyciu nowego certyfikatu z podpisem własnym i identyfikatora sprzętu. Blokowanie jest przeznaczone do blokowania zagubionych nośników rozruchowych lub nośników rozruchowych ze złamanymi zabezpieczeniami w trakcie wdrażania systemu operacyjnego na klientach, gdy wszystkie systemy lokacji akceptują połączenia klientów HTTPS. W razie korzystania z infrastruktury kluczy publicznych (PKI) obsługującej listę odwołania certyfikatów (CRL), odwołanie certyfikatów powinno być zawsze główną linią obrony przed certyfikatami, które mogą mieć złamane zabezpieczenia. Blokowanie klientów w programie Configuration Manager stanowi drugą linię obrony w celu ochrony hierarchii.  

 Aby uzyskać więcej informacji, zobacz [Określanie, czy blokować klientów w programie System Center Configuration Manager](../../../../core/clients/deploy/plan/determine-whether-to-block-clients.md).  

 **Użyj najbezpieczniejszych metod instalowania klienta, które są w praktyce w środowisku użytkownika:**  

-   Instalacja klienta zasad grupy i instalacja klienta oparta na aktualizacji oprogramowania są bardziej bezpieczne dla komputerów w domenie niż instalacja klienta w trybie wypychania.  

-   W przypadku korzystania z kontroli dostępu i kontroli zmiany tworzenie obrazu i instalacja ręczna mogą być bardzo bezpiecznymi metodami.  

 Wśród wszystkich metod instalowania klienta instalacja klienta w trybie wypychania jest najmniej bezpieczna ze względu na wiele zależności, w tym lokalne uprawnienia administratora, udział Admin$ oraz wiele wyjątków zapory. Te zależności zwiększają obszar ataków.  

 Aby uzyskać więcej informacji o różnych metodach instalowania klientów, zobacz [Metody instalacji klientów w programie System Center Configuration Manager](../../../../core/clients/deploy/plan/client-installation-methods.md).  

 Ponadto wszędzie tam, gdzie to możliwe, należy wybrać metodę instalowania klienta wymagającą najmniej uprawnień zabezpieczeń w programie Configuration Manager i ograniczyć użytkowników administracyjnych, którym przypisano role zabezpieczeń zawierające uprawnienia, które mogą służyć do celów innych niż wdrażanie klienta. Automatyczne uaktualnienie klienta wymaga na przykład roli zabezpieczeń **Administrator o pełnych uprawnieniach** zapewniającej użytkownikowi administracyjnemu wszystkie uprawnienia zabezpieczeń.  

 Aby uzyskać więcej informacji na temat zależności i uprawnień zabezpieczeń wymaganych dla poszczególnych metod instalacji klienta, zobacz "Zależności metod instalacji" w [wymagania wstępne dla komputerów klienckich](../../../../core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers.md#BKMK_prereqs_computers).  

 **Jeśli musisz instalacji wypychanej klienta, należy wykonać dodatkowe czynności, aby zabezpieczyć konto instalacji wypychanej klienta**  

 Mimo że to konto musi należeć do lokalnej **Administratorzy** grupy na każdym komputerze, na którym zostanie zainstalowane oprogramowanie klienta programu Configuration Manager nigdy nie należy dodawać konta klienta do instalacji wypychanej do **Administratorzy domeny** grupy. lecz utworzyć grupę globalną i dodać ją do lokalnej grupy **administratorów** na komputerach klienckich. Można również utworzyć obiekt zasad grupy, aby dodać ustawienie grup z ograniczeniami w celu dodania konta instalacji klienta w trybie wypychania do lokalnej grupy **administratorów**.  

 Aby dodatkowo zwiększyć bezpieczeństwo, należy utworzyć wiele kont instalacji klienta w trybie wypychania, z których każde będzie miało dostęp administracyjny do ograniczonej liczby komputerów. W przypadku złamania zabezpieczeń jednego konta zostaną złamane wyłącznie zabezpieczenia komputerów klienckich, do których to konto ma dostęp.  

 **Należy usunąć certyfikaty przed utworzeniem obrazu komputera klienckiego**  

 Jeśli jest planowane wdrożenie klientów przez utworzenie obrazu, przed przechwyceniem obrazu należy zawsze usunąć certyfikaty, jak certyfikaty PKI zawierające uwierzytelnianie klienta oraz certyfikaty z podpisem własnym. Jeśli te certyfikaty nie zostaną usunięte, klienci będą się mogli wzajemnie personifikować, a użytkownik nie będzie mógł zweryfikować danych każdego klienta.  

 Więcej informacji o sposobie korzystania z programu Sysprep w celu przygotowania komputera do utworzenia obrazu znajduje się w dokumentacji wdrożeniowej systemu Windows.  

 **Upewnij się, że komputery klienckie programu Configuration Manager otrzymują autoryzowaną kopię tych certyfikatów:**  

-   Menedżer konfiguracji zaufanego klucza głównego  

     Jeśli użytkownik nie rozszerzył schematu usługi Active Directory dla programu Configuration Manager, a klienci nie korzystają z certyfikatów PKI podczas komunikowania się z punktami zarządzania, klienci korzystają z programu Configuration Manager zaufanego klucza głównego w celu uwierzytelniania prawidłowych punktów zarządzania. Przy takim scenariuszu klienci nie mogą zweryfikować, czy punkt zarządzania jest zaufanym punktem zarządzania dla hierarchii, chyba że skorzystają z zaufanego klucza głównego. Bez zaufanego klucza głównego doświadczona osoba atakująca może kierować klientów do nieautoryzowanego punktu zarządzania.  

     Jeśli klienci nie mogą pobrać programu Configuration Manager zaufany klucz główny z wykazu globalnego lub korzystając z certyfikatów PKI, wstępnie udostępnić klientom zaufany klucz główny aby upewnić się, że ich kierowaniu do nieautoryzowanego punktu zarządzania. Więcej informacji można znaleźć w sekcji [Planowanie zaufanego klucza głównego](../../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForRTK).  

-   Certyfikat podpisywania serwera lokacji  

     Klienci korzystają z certyfikatu podpisywania serwera lokacji, aby sprawdzić, czy serwer lokacji podpisał zasadę klienta pobraną z punktu zarządzania. Ten certyfikat ma podpis własny serwera lokacji i jest publikowany w usługach domenowych w usłudze Active Directory.  

     Jeśli klienci nie mogą pobrać certyfikatu podpisywania serwera lokacji z wykazu globalnego, certyfikat ten jest domyślne pobierany z punktu zarządzania. Jeśli punkt zarządzania ma połączenie z niezaufaną siecią (na przykład Internetem), należy ręcznie zainstalować certyfikat podpisywania serwera lokacji na klientach, aby zapobiec uruchamianiu przez klientów zasad klienta poddanych nieuprawnionej manipulacji przez punkt zarządzania ze złamanymi zabezpieczeniami.  

     Aby ręcznie zainstalować certyfikat podpisywania serwera lokacji, użyj właściwości **SMSSIGNCERT** programu CCMSetup clinet.msi. Aby uzyskać więcej informacji, zobacz [Informacje o właściwościach instalacji klientów w programie System Center Configuration Manager](../../../../core/clients/deploy/about-client-installation-properties.md).  

 **Nie należy używać automatycznego przypisania lokacji, jeśli klient pobierze zaufany klucz główny z pierwszego punktu zarządzania, z którym się skontaktuje.**  

 To rozwiązanie dotyczące zabezpieczeń jest związane z poprzednią sugestią. Aby uniknąć zagrożenia wynikającego z pobrania przez nowego klienta zaufanego klucza głównego z nieautoryzowanego punktu zarządzania, należy używać automatycznego przypisania lokacji wyłącznie przy następujących scenariuszach:  

-   Klient ma dostęp do informacji o lokacji programu Configuration Manager, publikowana w usługach domenowych w usłudze Active Directory.  

-   Użytkownik udostępnia wstępnie klientowi zaufany klucz główny.  

-   Użytkownik korzysta z certyfikatów PKI urzędu certyfikacji przedsiębiorstwa, aby ustanowić zaufanie między klientem i punktem zarządzania.  

 Aby uzyskać więcej informacji o zaufanym kluczu głównym, zobacz [Planowanie zaufanego klucza głównego](../../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForRTK).  

 **Instalować komputery klienckie z opcją CCMSetup Client.msi SMSDIRECTORYLOOKUP = NoWINS**  

 Najbezpieczniejszą metodą lokalizacji usługi dla klientów w celu znajdywania lokacji i punktów zarządzania jest korzystanie z usług Active Directory Domain Services. Jeśli nie jest to możliwe, na przykład, ponieważ nie można rozszerzyć schematu usługi Active Directory dla programu Configuration Manager lub klienci znajdują się w niezaufanym lesie lub niezaufanej grupie roboczej, należy można użyć publikowania DNS jako alternatywnej metody lokalizacji usługi. W przypadku, gdy obie metody zawiodą, klienci mogą wrócić do korzystania z usługi WINS, jeśli punkt zarządzania nie został skonfigurowany dla połączeń klienta HTTPS.  

 Publikowanie do usługi WINS jest mniej bezpieczne od innych metod publikowania. Z tego względu należy skonfigurować komputery klienckie tak, aby nie wracały do korzystania z usługi WINS, określając opcję SMSDIRECTORYLOOKUP=NoWINS. Korzystania z usługi WINS, należy w celu lokalizacji usługi, użyj opcji SMSDIRECTORYLOOKUP = WINSSECURE (ustawienie domyślne), który używa programu Configuration Manager zaufany klucz główny można sprawdzić poprawności certyfikatu z podpisem własnym punktu zarządzania.  

> [!NOTE]  
>  Jeśli klient jest skonfigurowany opcję smsdirectorylookup = WINSSECURE i klient znajdzie punkt zarządzania za pomocą usługi WINS, klient sprawdzi kopię programu Configuration Manager zaufanego klucza głównego w usłudze WMI. Jeśli podpis na zarządzanie punktu zgodny certyfikatu klienta kopię zaufanego klucza głównego, certyfikat zostanie zweryfikowany, a klient komunikuje się z punktem zarządzania znalezionym za pomocą usługi WINS. Jeśli podpis na certyfikacie punktu zarządzania nie jest zgodny z kopią zaufanego klucza głównego, certyfikat nie jest prawidłowy, a klient nie skomunikuje się z punktem zarządzania znalezionym za pomocą usługi WINS.  

 **Upewnij się, że okna obsługi są wystarczająco duże, aby wdrożyć krytyczne aktualizacje oprogramowania**  

 Można skonfigurować okna obsługi kolekcji urządzeń ograniczyć czas programu Configuration Manager może instalować oprogramowanie na tych urządzeniach. Jeśli wartość określona dla czasu trwania okna obsługi będzie zbyt mała, instalacja krytycznych aktualizacji oprogramowania przez klienta może nie być możliwa, co sprawi, że klient będzie narażony na atak, którego skuteczność została osłabiona przez aktualizację oprogramowania.  

 **Dla urządzeń z systemem Windows embedded z filtrami zapisu, zastosować dodatkowe zabezpieczenia, aby zmniejszyć obszar ataków, jeśli program Configuration Manager wyłączy filtry zapisu, aby utrwalić instalacje oprogramowania i zmiany**  

 Po włączeniu filtrów zapisu w urządzeniach Windows Embedded wszelkie instalacje oprogramowania lub zmiany będą wykonywane wyłącznie w odniesieniu do nakładki i nie zostaną utrwalone po ponownym uruchomieniu urządzenia. Jeśli używasz programu Configuration Manager w celu tymczasowego wyłączenia filtrów zapisu, aby utrwalić instalacje oprogramowania i zmiany, w tym okresie urządzenie osadzone jest narażone na zmiany we wszystkich woluminach, w tym w folderach udostępnionych.  

 Mimo że programu Configuration Manager blokuje komputer w tym okresie, tak aby tylko lokalni administratorzy mogą się zalogować, jeśli to możliwe, należy wykonać dodatkowe zabezpieczenia, aby pomóc chronić komputer. Należy na przykład włączyć dodatkowe ograniczenia zapory i odłączyć urządzenie od sieci.  

 Jeśli użytkownik używa okien obsługi do utrwalania zmian, należy dokładnie planować te okna, aby skrócić czas, przez który filtry zapisu mogą być wyłączone. Czas trwania okien powinien być jednak wystarczająco długi, aby można było ukończyć instalacje oprogramowania i ponowne uruchomienia.  

 **Jeśli instalacja klienta oparta na aktualizacji oprogramowania i instaluje późniejszą wersję klienta w lokacji, należy zaktualizować aktualizację oprogramowania opublikowaną w punkcie aktualizacji oprogramowania tak, aby klienci otrzymali najnowszą wersję.**  

 Jeśli użytkownik zainstaluje późniejszą wersję klienta w lokacji, na przykład uaktualniając lokację, aktualizacja oprogramowania wdrażania klienta opublikowana w punkcie aktualizacji oprogramowania nie zostanie automatycznie zaktualizowana. Będzie konieczne ponownie opublikowanie klienta programu Configuration Manager punkt aktualizacji oprogramowania oraz kliknięcie przycisku **tak** Aby zaktualizować numer wersji.  

 Aby uzyskać więcej informacji, zobacz procedurę "Aby opublikować klienta programu Configuration Manager w punkcie aktualizacji oprogramowania" w [jak instalować klientów programu Configuration Manager za pomocą instalacji opartej](../../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientSUP).  

 **Konfigurowanie ustawień wpisu zawiesić numeru PIN funkcji BitLocker po ponownym uruchomieniu komputera należy zawsze tylko dla komputerów, którym ufasz urządzenia klienta Agent komputera i z ograniczonym dostępem fizycznym**  

 Gdy ustawisz to ustawienie klienta **zawsze**, programu Configuration Manager może ukończyć instalację oprogramowania, aby zapewnić, że zainstalowano krytycznych aktualizacji oprogramowania i wznowienie usług. Jeśli jednak osoba atakująca przechwyci proces ponownego uruchamiania, może przejąć kontrolę nad komputerem. Tego ustawienia należy używać tylko w przypadku, gdy ten komputer jest zaufany, a fizyczny dostęp do niego jest ograniczony. To ustawienie może być odpowiednie na przykład dla serwerów w centrum danych.  

 **Nie należy konfigurować zasady wykonywania programu PowerShell ustawienie urządzenia klienta Agent komputera jako obejścia.**  

 To ustawienie klienta umożliwia klienta programu Configuration Manager uruchamiać niepodpisane skrypty programu PowerShell, co może spowodować uruchomienie złośliwego oprogramowania na komputerach klienckich. Jeśli wybranie tej opcji jest konieczne, należy użyć niestandardowego ustawienia klienta i przypisać je tylko do komputerów klienckich, które muszą uruchamiać niepodpisane skrypty powłoki PowerShell.  

##  <a name="bkmk_mobile"></a>Najlepsze rozwiązania dotyczące urządzeń przenośnych  
 **Dla urządzeń przenośnych, które rejestrowanie przy użyciu Menedżera konfiguracji i będą obsługiwane w Internecie: Zainstalowanie punktu proxy rejestracji w sieci obwodowej oraz punkt rejestracyjny w sieci intranet**  

 Ta separacja ról pomaga chronić punkt rejestracyjny przed atakiem. W przypadku złamania zabezpieczeń punktu rejestracyjnego osoba atakująca może uzyskać certyfikaty służące do uwierzytelniania i skraść poświadczenia użytkowników, którzy rejestrują swoje urządzenia przenośne.  

 **Dla urządzeń przenośnych: Konfiguruj ustawienia hasła w celu ochrony urządzeń przenośnych przed nieautoryzowanym dostępem**  

 Dla urządzeń przenośnych, które są zarejestrowane przez program Configuration Manager: Użyj elementu konfiguracji urządzenia przenośnego w celu skonfigurowania złożoności hasła jako numeru PIN oraz przynajmniej domyślną długość dla opcji minimalnej długości hasła.  

 Dla urządzeń przenośnych, które nie mają zainstalowanego klienta programu Configuration Manager, ale są zarządzane przez łącznik serwera Exchange: Skonfiguruj **ustawienia hasła** dla łącznika serwera Exchange złożoności hasła jako numeru PIN i określić przynajmniej domyślną długość dla opcji minimalnej długości hasła.  

 **Dla urządzeń przenośnych: Zapobiec próbom naruszenia informacji o spisie i stanie, zezwalając na uruchamianie tylko wtedy, gdy są podpisane przez producentów, którym ufasz, a nie zezwalaj na instalowanie niepodpisanych plików można zainstalować aplikacji**  

 Dla większa liczba urządzeń przenośnych zarejestrowanych przez program Configuration Manager: Użyj elementu konfiguracji urządzenia przenośnego, aby skonfigurować ustawienia zabezpieczeń **aplikacje niepodpisane** jako **zabronione** i skonfigurować **niepodpisanego pliku** na zaufane źródło.  

 Dla urządzeń przenośnych, które nie mają zainstalowanego klienta programu Configuration Manager, ale są zarządzane przez łącznik serwera Exchange: Skonfiguruj **ustawienia aplikacji** dla łącznika programu Exchange Server tak, aby **Instalacja niepodpisanego pliku** i **aplikacje niepodpisane** są skonfigurowane jako **zabronione**.  

 **Dla urządzeń przenośnych: Zapobiegać atakom powodującym podniesienie uprawnień poprzez zablokowanie urządzeń przenośnych, gdy nie jest używane**  

 Dla większa liczba urządzeń przenośnych zarejestrowanych przez program Configuration Manager: Użyć elementu konfiguracji urządzenia przenośnego w celu skonfigurowania ustawienia hasła **czas bezczynności w minutach przed zablokowaniem urządzenia przenośnego**.  

 Dla urządzeń przenośnych, które nie mają zainstalowanego klienta programu Configuration Manager, ale są zarządzane przez łącznik serwera Exchange: Skonfiguruj **ustawienia hasła** dla łącznika serwera Exchange skonfigurować **czas bezczynności w minutach przed zablokowaniem urządzenia przenośnego**.  

 **Dla urządzeń przenośnych: Zapobiegać podnoszeniu uprawnień poprzez ograniczenie użytkowników, którzy mogą rejestrować swoje urządzenia przenośne.**  

 Należy użyć niestandardowego ustawienia klienta zamiast domyślnych ustawień klienta, aby umożliwić rejestrowanie urządzeń przenośnych tylko przez autoryzowanych użytkowników.  

 **Dla urządzeń przenośnych: Nie należy wdrażać aplikacji dla użytkowników mających urządzenia przenośne zarejestrowane przez programu Configuration Manager lub Microsoft Intune w następujących scenariuszach:**  

-   Kiedy urządzenie przenośne jest używane przez więcej niż jedną osobę.  

-   Kiedy urządzenie jest rejestrowane przez administratora w imieniu użytkownika.  

-   Kiedy urządzenie jest przekazywane innej osobie bez wycofania, a następnie ponownego zarejestrowania urządzenia.  

 Relacja koligacji urządzenia użytkownika jest tworzona podczas rejestracji, która mapuje użytkownika wykonującego rejestrację na urządzenie przenośne. Jeśli inny użytkownik użyje urządzenia przenośnego, będzie mógł uruchamiać aplikacje wdrożone dla oryginalnego użytkownika, co może spowodować podniesienie uprawnień. Z kolei, jeśli administrator zarejestruje urządzenie przenośne dla użytkownika, nie zostaną zainstalowane aplikacje wdrożone dla użytkownika, ale aplikacje wdrożone dla administratora.  

 W przeciwieństwie do koligacji urządzenia użytkownika dla komputerów z systemem Windows nie można ręcznie zdefiniować informacji o koligacji urządzenia użytkownika dla urządzeń przenośnych zarejestrowanych w usłudze Microsoft Intune.  

 W przypadku przeniesienia własności urządzenia przenośnego, które zostało zarejestrowane przez usługę Intune, należy wycofać to urządzenie przenośne z usługi Intune, aby usunąć koligację urządzenia użytkownika, a następnie poprosić bieżącego użytkownika o ponowne zarejestrowanie urządzenia.  

 **Dla urządzeń przenośnych: Upewnij się, że użytkownicy rejestrują własne urządzenia przenośne w usłudze Microsoft Intune**  

 Relacja koligacji urządzenia użytkownika jest tworzona podczas rejestracji, która mapuje użytkownika wykonującego rejestrację na urządzenie przenośne. Jeśli więc administrator zarejestruje urządzenie przenośne dla użytkownika, nie zostaną zainstalowane aplikacje wdrożone dla użytkownika, ale aplikacje wdrożone dla administratora.  

 **Łącznik serwera Exchange: Upewnij się, że połączenie między serwerem lokacji programu Configuration Manager i komputerem serwera Exchange jest chroniony**  

 Należy użyć protokołu IPsec, jeśli serwer programu Exchange działa lokalnie; hostowany serwer programu Exchange automatycznie zabezpiecza połączenie przy użyciu protokołu SSL.  

 **Łącznik serwera Exchange: Używać reguły najniższych uprawnień dla łącznika**  

 Listę minimalnych poleceń cmdlet, których wymaga łącznik serwera Exchange, zawiera temat [Zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i Exchange](../../../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md).  

##  <a name="bkmk_macs"></a>Najlepsze rozwiązania dla komputerów Mac  
 **Dla komputerów Mac: Przechowywanie i dostęp do plików źródłowych klienta z bezpiecznej lokalizacji.**  

 Menedżer konfiguracji nie sprawdza, czy pliki źródłowe klienta zostały naruszone z przed zainstalowaniem lub zarejestrowaniem klienta na komputerze Mac. Takie pliki należy pobierać z wiarygodnego źródła, a także przechowywać je i uzyskiwać do nich dostęp w bezpieczny sposób.  

 **Dla komputerów Mac: Niezależnie od programu Configuration Manager, należy monitorować i śledzić okres ważności certyfikatu zarejestrowanego dla użytkowników.**  

 Aby zapewnić ciągłość pracy, należy monitorować i śledzić okres ważności certyfikatów używanych dla komputerów Mac. Configuration Manager nie obsługuje automatycznego odnawiania certyfikatu ani nie ostrzega o tym, że certyfikat jest wygaśnie. Typowy okres ważności wynosi 1 rok.  

 Aby uzyskać informacje dotyczące sposobu odnawiania certyfikatu, zobacz [Ręczne odnawianie certyfikatu klienta na komputery Mac](../../../../core/clients/deploy/deploy-clients-to-macs.md#renewing-the-mac-client-certificate).  

 **Dla komputerów Mac: Należy rozważyć skonfigurowanie certyfikatu zaufanego głównego urzędu certyfikacji, który jest zaufany dla protokołu SSL, co pomoże zapewnić ochronę przed podniesieniem uprawnień.**  

 Podczas rejestrowania komputerów Mac, certyfikat użytkownika służący do zarządzania klientem programu Configuration Manager jest instalowana automatycznie, także certyfikat zaufanego głównego, z którym jest powiązany ten certyfikat użytkownika. Aby ograniczyć zaufanie tego certyfikatu głównego tylko do protokołu SSL, można skorzystać z poniższej procedury.  

 Po zakończeniu tej procedury należy certyfikat główny nie będzie zaufany celu weryfikowania protokołów innych niż SSL — na przykład Secure Mail (S/MIME), Extensible Authentication (EAP) lub podpisywanie kodu.  

> [!NOTE]  
>  Można również Użyj tej procedury, jeśli zainstalowano certyfikat klienta niezależnie od programu Configuration Manager.  

 Aby ograniczyć certyfikat głównego urzędu certyfikacji tylko do protokołu SSL:  

1.  Na komputerze Mac otwórz okno terminala.  

2.  Wprowadź polecenie **sudo /Applications/Utilities/Keychain\ Access.app/Contents/MacOS/Keychain\ Access**  

3.  W oknie dialogowym **Dostęp do pęku kluczy** w sekcji **Pęki kluczy** kliknij pozycję **System**, a następnie w sekcji **Kategoria** kliknij pozycję **Certyfikaty**.  

4.  Znajdź i kliknij dwukrotnie certyfikat głównego urzędu certyfikacji dla certyfikatu klienta dla komputerów Mac.  

5.  W oknie dialogowym certyfikat głównego urzędu certyfikacji rozwiń sekcję **Opcje zaufania**, a następnie dokonaj następujących zmian:  

    1.  Na liście rozwijanej **Używając tego certyfikatu** zmień ustawienie domyślne **Zawsze ufaj** na **Użyj domyślnych ustawień systemowych**.  

    2.  Na liście rozwijanej **Secure Sockets Layer (SSL)** zmień ustawienie **brak wskazanej wartości** na **Zawsze ufaj**.  

6.  Zamknij okno dialogowe i po wyświetleniu monitu wprowadź hasło administratora, a następnie kliknij przycisk **ustawienia aktualizacji**.  

##  <a name="BKMK_SecurityIssues_Clients"></a>Problemy dotyczące zabezpieczeń klientów programu Configuration Manager  
 Następujące problemy dotyczące zabezpieczeń nie mają środków zaradczych:  

-   Komunikaty o stanie nie są uwierzytelniane  

     Uwierzytelnianie nie jest wykonywane dla komunikatów o stanie. Kiedy punkt zarządzania akceptuje połączenia klienta HTTP, dowolne urządzenie może wysyłać komunikaty o stanie do punktu zarządzania. Jeśli punkt zarządzania akceptuje tylko połączenia klienta HTTPS, urządzenie musi uzyskać prawidłowy certyfikat uwierzytelniania klienta z zaufanego głównego urzędu certyfikacji, ale następnie może także wysłać dowolny komunikat o stanie. Jeśli klient wyśle nieprawidłowy komunikat o stanie, zostanie on odrzucony.  

     Istnieje kilka potencjalnych ataków wykorzystujących tę lukę w zabezpieczeniach. Osoba atakująca może wysłać sfałszowany komunikat o stanie, aby uzyskać członkostwo w kolekcji na podstawie kwerend komunikatów o stanie. Dowolny klient może uruchomić atak typu „odmowa usługi” przeciwko punktowi zarządzania, zalewając go komunikatami o stanie. Jeśli komunikaty o stanie wyzwalają akcje w regułach filtru komunikatów o stanie, osoba atakująca może wyzwolić regułę filtru komunikatów o stanie. Ponadto osoba atakująca może wysłać komunikat o stanie, który sprawi, że informacje w raporcie będą niedokładne.  

-   Cel zasad może zostać zmieniony na innych klientów  

     Istnieje kilka metod, które osoby atakujące mogą wykorzystać w celu zmiany celu zasad klienta na zupełnie innego klienta. Na przykład osoba atakująca na zaufanym kliencie może wysłać fałszywe informacje o spisie lub dotyczące odnajdywania w celu dodania komputera do kolekcji, do której nie może należeć. W ten sposób klient będzie otrzymywać wszystkie wdrożenia dla tej kolekcji. Wprawdzie istnieją środki zapobiegawcze, które uniemożliwiają osobom atakującym bezpośrednie modyfikowanie zasad, ale osoba atakująca może wykorzystać istniejące zasady w celu ponownego sformatowania i wdrożenia systemu operacyjnego, a następnie wysłać je do innego komputera, tworząc atak typu „odmowa usługi”. Ataki tego rodzaju wymagają precyzyjnej synchronizacji czasu i doskonałej znajomości infrastruktury programu Configuration Manager.  

-   Dzienniki klienta umożliwiają dostęp użytkownika  

     Wszystkie pliki dziennika zapewniają użytkownikom uprawnienie dostępu Odczyt oraz dostęp typu Zapis dla użytkowników interaktywnych. Jeśli włączono pełne rejestrowanie, osoby atakujące mogą odczytać pliki dziennika w celu wyszukania informacji dotyczących zgodności lub luk w zabezpieczeniach systemu. Niektóre procesy wykonywane w kontekście użytkownika, takie jak instalacja oprogramowania, muszą mieć możliwość zapisywania dzienników przy użyciu konta użytkownika o niskich prawach. Oznacza to, że także osoba atakująca może zapisywać w dziennikach przy użyciu konta o niskich prawach.  

     Najpoważniejsze zagrożenie jest związane z tym, że osoba atakująca może usunąć z plików dziennika informacje, które mogą być wymagane przez administratora do audytu i wykrywania intruzów.  

-   Komputer może zostać użyty do uzyskania certyfikatu stworzonego na potrzeby rejestracji urządzenia przenośnego  

     W przypadku programu Configuration Manager przetwarza żądanie rejestracji, nie może zweryfikować, czy żądanie pochodzi z urządzenia przenośnego, a nie z komputera. Jeśli żądanie pochodzi z komputera, może zostać zainstalowany certyfikat PKI, który następnie umożliwi zarejestrowanie z programem Configuration Manager. Aby zapobiec atakom powodującym podniesienie uprawnień w tym scenariuszu, należy umożliwić rejestrowanie urządzeń przenośnych tylko przez zaufanych użytkowników oraz dokładnie monitorować działania rejestracji.  

-   Połączenie z klienta do punktu zarządzania nie zostaje przerwane po zablokowaniu klienta, jeśli zablokowany klient w dalszym ciągu będzie wysyłać do punktu zarządzania pakiety powiadomień klienta jako komunikaty utrzymywania aktywności  

     Jeśli zablokowany klient, który nie jest już zaufany, nawiązał komunikację powiadomień klienta, programu Configuration Manager nie rozłączy tej sesji. Zablokowany klient może kontynuować wysyłanie pakietów do swojego punktu zarządzania aż do momentu, gdy klient odłączy się od sieci. Te pakiety stanowią wyłącznie małe pakiety utrzymywania aktywności i Ci klienci nie mogą być zarządzane przez program Configuration Manager aż do ich odblokowania.  

-   Kiedy stosowane jest automatyczne uaktualnianie klienta, a klient zostaje skierowany do punktu zarządzania w celu pobrania plików źródłowych klienta, punkt zarządzania nie jest weryfikowany jako zaufane źródło  

-   Kiedy użytkownicy po raz pierwszy rejestrują komputery Mac, są narażeni na ataki metodą preparowania DNS  

     Kiedy podczas rejestracji komputer Mac nawiązuje połączenie z punktem proxy rejestracji, najprawdopodobniej ten komputer nie ma jeszcze certyfikatu głównego urzędu certyfikacji. Na tym etapie serwer nie jest zaufany przez komputer Mac i wyświetlany jest monit dla użytkownika o kontynuację. Jeśli w pełni kwalifikowana nazwa punktu proxy rejestracji zostanie rozwiązana przez złośliwy serwer DNS, komputer Mac może zostać skierowany do złośliwego punktu proxy rejestracji, przez co zostaną zainstalowane certyfikaty z niezaufanego źródła. Aby ograniczyć to ryzyko, należy stosować najlepsze rozwiązania w celu zapobiegania atakom metodą preparowania DNS w danym środowisku.  

-   Rejestracja komputerów Mac nie ogranicza liczby żądań certyfikatów  

     Użytkownicy mogą ponownie zarejestrować swoje komputery Mac, za każdym razem żądając nowego certyfikatu klienta. Menedżer konfiguracji nie Sprawdź dla wielu żądań lub ograniczenie liczby certyfikatów żądanych z jednego komputera. Złośliwy użytkownik może uruchomić skrypt, który powtarza żądania rejestracji w wierszu polecenia, wykonując atak typu „odmowa usługi” w sieci lub przeciwko urzędowi wystawiającemu certyfikaty. Aby ograniczyć to ryzyko, należy dokładnie monitorować urząd wystawiający certyfikaty pod kątem takiego złośliwego zachowania. Komputerze wykazujący tego zachowania, należy natychmiast zablokować w hierarchii programu Configuration Manager.  

-   Potwierdzenie wyczyszczenia nie sprawdza, czy urządzenie zostało pomyślnie wyczyszczone  

     Jeśli zainicjowano akcję czyszczenia urządzenia przenośnego i programu Configuration Manager Wyświetla stan czyszczenia do potwierdzenia, weryfikacja oznacza, że programu Configuration Manager pomyślnie wysłał wiadomość, a nie urządzenia podjęło. Ponadto w przypadku urządzeń przenośnych, które są zarządzane przez łącznik serwera Exchange, potwierdzenie wymazania weryfikuje otrzymanie polecenia przez serwer Exchange, a nie przez urządzenie.  

-   Jeśli używa się opcji do zatwierdzania zmian na urządzeniach z systemem Windows Embedded, konta mogą zostać zablokowane szybciej, niż można by się spodziewać.  

     Jeśli urządzenie Windows Embedded jest uruchomiony system operacyjny niż Windows 7, użytkownik próbuje się zalogować przy wyłączonych filtrach zapisu w celu zatwierdzenia zmian wprowadzonych przez program Configuration Manager, liczba nieudanych prób logowania dozwolona przed zablokowaniem konta jest dwukrotnie mniejsza. Jeśli na przykład opcja **Próg blokady konta** jest ustawiona na 6, a użytkownik błędnie wpisze hasło 3 razy, konto zostaje zablokowane, tworząc sytuację podobną do ataku typu „odmowa usługi”.  Jeśli użytkownicy w tym scenariuszu muszą się logować na urządzeniach z systemem osadzonym, należy ich ostrzec o potencjalnie zmniejszonym progu blokady konta.  

##  <a name="BKMK_Privacy_Cliients"></a>Informacje o ochronie prywatności klientów programu Configuration Manager  
 Podczas wdrażania klienta programu Configuration Manager konfigurujesz ustawienia klienta, dzięki czemu można użyć funkcji zarządzania programu Configuration Manager. Ustawienia, które są używane do konfigurowania funkcji mogą dotyczyć wszystkich klientów w hierarchii programu Configuration Manager, niezależnie od tego, czy ich są bezpośrednio podłączone do sieci firmowej, podłączeni za pomocą sesji zdalnej lub połączony z Internetem, ale obsługiwane przez program Configuration Manager.  

 Informacje o kliencie są przechowywane w bazie danych programu Configuration Manager i nie są wysyłane do firmy Microsoft. Informacje są przechowywane w bazie danych, aż do ich usunięcia przez uruchamiane co 90 dni zadania konserwacji lokacji **Usuń przestarzałe dane wykrywania**. Możesz skonfigurować interwał usuwania.  

 Przed skonfigurowaniem klienta programu Configuration Manager, należy wziąć pod uwagę wymagania dotyczące ochrony prywatności.  

### <a name="privacy-information-for-mobile-devices-that-are-enrolled-by-configuration-manager"></a>Informacje o ochronie prywatności dotyczące urządzeń przenośnych zarejestrowanych w programie Configuration Manager  
 Aby uzyskać informacje o ochronie prywatności dla po zarejestrowaniu urządzenia przenośnego przez program Configuration Manager, zobacz [poufności informacji programu System Center Configuration Manager — uzupełnienie dla urządzeń przenośnych](../../../../core/misc/privacy/privacy-statement-mobile-device-addendum.md).  

### <a name="client-status"></a>Stan klienta  
 Configuration Manager monitoruje aktywność klientów oraz okresowo ocenia i koryguje klienta programu Configuration Manager i jego zależności. Stan klienta jest domyślnie włączona i wykorzystuje metryki po stronie serwera kontroli działania klienta i działania po stronie klienta do samokontroli, korygowania i wysyłania stanu klienta informacji do lokacji programu Configuration Manager. Klient uruchamia samokontrole zgodnie z konfigurowalnym harmonogramem. Klient wysyła wyniki kontroli do lokacji programu Configuration Manager. Informacje te są szyfrowane podczas transferu.  

 Informacje o stanie klienta są przechowywane w bazie danych programu Configuration Manager i nie są wysyłane do firmy Microsoft. Informacje nie są przechowywane w zaszyfrowanym formacie w bazie danych lokacji. Te informacje są zachowywane w bazie danych do chwili ich usunięcia, zgodnie z wartością ustawienia stanu klienta **Zachowaj historię stanu klienta przez następującą liczbę dni**. Domyślna wartość tego ustawienia to 31 dni.  

 Przed zainstalowaniem klienta programu Configuration Manager z sprawdzanie stanu klienta, należy wziąć pod uwagę wymagania dotyczące ochrony prywatności.  

##  <a name="BKMK_Privacy_ExchangeConnector"></a>Informacje o ochronie prywatności urządzeń przenośnych, które są zarządzane przez łącznik serwera Exchange  
 Łącznik serwera Exchange umożliwia wyszukiwanie urządzeń przenośnych i zarządzanie urządzeniami przenośnymi, które łączą się z serwerem Exchange Server (lokalnie lub online), używając protokołu ActiveSync. Rejestry znalezione przez łącznik serwera Exchange są przechowywane w bazie danych programu Configuration Manager. Informacje są zbierane z serwera programu Exchange. Nie zawierają żadnych dodatkowych informacji wysyłanych przez urządzenia przenośne do serwera programu Exchange.  

 Informacje o urządzeniach przenośnych nie są wysyłane do firmy Microsoft. Informacje o urządzeniach przenośnych jest przechowywane w bazie danych programu Configuration Manager. Informacje są przechowywane w bazie danych, aż do ich usunięcia przez uruchamiane co 90 dni zadania konserwacji lokacji **Usuń przestarzałe dane wykrywania**. Możesz skonfigurować interwał usuwania.  

 Przed zainstalowaniem i skonfigurowaniem łącznika serwera Exchange musisz uwzględnić wymogi związane z ochroną prywatności.  
