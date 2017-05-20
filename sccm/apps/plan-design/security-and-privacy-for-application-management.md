---
title: "Bezpieczeństwo i prywatność zarządzania aplikacjami | Dokumentacja firmy Microsoft"
description: "Bezpieczeństwo i prywatność najlepszych rozwiązań dotyczących zarządzania aplikacjami w programie System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d26deed-3b16-4116-b640-f618f2c20f5a
caps.latest.revision: 8
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 521b90b9d497818a4c1e546fca38cd15d4cab487
ms.openlocfilehash: 6ee99fa0c07676f004e41a50bf16d0d17604e790
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="security-and-privacy-for-application-management-in-system-center-configuration-manager"></a>Zabezpieczenia i prywatność zarządzania aplikacjami w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


##  <a name="security-best-practices-for-application-management"></a>Najlepsze rozwiązania dotyczące zarządzania aplikacjami  

|Najlepsze rozwiązanie w zakresie zabezpieczeń|Więcej informacji|  
|----------------------------|----------------------|  
|Skonfiguruj punkty katalogu aplikacji, aby używały połączeń przy użyciu protokołu HTTPS, i poinformuj użytkowników o zagrożeniach związanych ze złośliwymi witrynami sieci web.|Skonfiguruj punkty witryny sieci web oraz usługi sieci web katalogu aplikacji, aby akceptowały połączenia przy użyciu protokołu HTTPS. Pozwoli to na uwierzytelnianie serwera dla użytkowników oraz zapewni ochronę przesyłanych danych przed naruszeniem i wyświetlaniem. Aby zapobiec atakom przy użyciu inżynierii społecznej, należy poinformować użytkowników o konieczności łączenia się tylko z zaufanymi witrynami sieci web.<br /><br /> Nie należy używać znakowania opcje konfiguracji, które Pokaż nazwę organizacji w katalogu aplikacji jako dowodu tożsamości, gdy nie należy używać protokołu HTTPS.|  
|Zastosuj separację roli i zainstaluj punkty witryny sieci web oraz usługi katalogu aplikacji na oddzielnych serwerach.|W przypadku złamania zabezpieczeń punktu witryny sieci Web katalogu aplikacji, należy go zainstalować na oddzielnym serwerze z punktem usługi sieci web katalogu aplikacji. Zapewni to ochronę klientów programu Configuration Manager i infrastrukturę programu Configuration Manager. Jest to szczególnie ważne, gdy punkt witryny sieci web katalogu aplikacji akceptuje połączenia przez Internet, ponieważ przy takiej konfiguracji serwer jest narażony na ataki.|  
|Poinformuj użytkowników o konieczności zamykania okna przeglądarki po zakończeniu korzystania z katalogu aplikacji.|Jeżeli użytkownicy przeglądają zewnętrzną witrynę sieci web w oknie przeglądarki używanym w ramach katalogu aplikacji, przeglądarka nadal używa ustawień zabezpieczeń odpowiednich do zaufanych witryn w sieci intranet.|  
|Ręcznie określić koligację urządzenia użytkownika zamiast zezwoleniem użytkownikom na identyfikację ich urządzenia podstawowego. Nie należy włączać konfiguracji opartej na użyciu.|Nie należy traktować informacji zebranych od użytkowników lub z urządzenia jako autorytatywnych. Podczas wdrażania oprogramowania przy użyciu konfiguracji koligacji urządzenia użytkownika,nieokreślonej przez zaufanego użytkownika administracyjnego oprogramowanie może zostać zainstalowane na komputerach oraz dla użytkowników niemających uprawnień do jego otrzymania.|  
|Wdrożenia należy zawsze konfigurować tak, aby pobierały zawartość z punktów dystrybucji, a nie były uruchamiane z tych punktów.|Po skonfigurowaniu wdrożeń, aby pobrać zawartość z punktu dystrybucji i lokalnie, uruchom Menedżera konfiguracji klient sprawdza skrótu pakietu, po pobraniu zawartości. Jeśli skrót jest niezgodny ze skrótem określonym w zasadach, klient odrzuci pakietu. Porównując w przypadku skonfigurowania uruchamiania bezpośrednio z punktu dystrybucji wdrożenia klienta programu Configuration Manager nie weryfikuje skrót pakietu, co oznacza, że Menedżer konfiguracji klienta można zainstalować oprogramowania, które zostały naruszone.<br /><br /> W przypadku konieczności uruchamiania wdrożeń bezpośrednio z punktów dystrybucji, systemu plików NTFS co najmniej uprawnienia do pakietów w punktach dystrybucji i zabezpieczyć kanały między klientem a punktami dystrybucji oraz między punktami dystrybucji a serwerem lokacji, użyj zabezpieczeń protokołu internetowego (IPsec).|  
|Zezwala użytkownikom na interakcję z programami, gdy **Uruchom z prawami administracyjnymi** opcja jest wymagana.|Podczas konfigurowania programu można ustawić **Zezwalaj użytkownikom na interakcję z tym programem** opcję Tak, aby umożliwić użytkownikom reagowanie na wszystkie wymagane monity w interfejsie użytkownika. Jeżeli w programie skonfigurowano również ustawienie **Uruchom z prawami administracyjny**, osoba atakująca na komputerze z uruchomionym programem może przy użyciu interfejsu użytkownika eskalować uprawnienia na komputerze klienckim.<br /><br /> Użyj programów, używających Instalatora Windows dla instalacji użytkownika podniesienie uprawnień wdrożeń oprogramowania wymagających poświadczeń administracyjnych. Instalator musi działać w kontekście użytkownika, który nie ma poświadczeń administracyjnych. Instalator Windows na użytkownika podwyższony poziom uprawnień zapewniają najbezpieczniejszą metodą wdrażania aplikacji, które wymagają tej opcji.|  
|Zdecyduj, czy ograniczyć użytkownikom możliwość interaktywnego instalowania oprogramowania przy użyciu ustawienia klienta **Uprawnienia do instalacji** .|Skonfiguruj **Agent komputera** urządzenia klienckiego **uprawnienia do instalacji** ustawienie, aby określić typy użytkowników, którzy mogą instalować oprogramowanie przy użyciu katalogu aplikacji lub Centrum oprogramowania. Utwórz na przykład niestandardowe ustawienie klienta, wybierając w ustawieniu **Uprawnienia do instalacji** opcję **Tylko administratorzy**. Następnie Zastosuj to ustawienie w kolekcji serwerów, aby uniemożliwić użytkownikom bez uprawnień administracyjnych instalowanie oprogramowania na tych komputerach.|  
|Dla urządzeń przenośnych należy wdrażać tylko podpisane aplikacje.|Wdrażanie aplikacji urządzenia przenośnego, tylko wtedy, gdy są one kod podpisany przez urząd certyfikacji (CA), który jest zaufany dla urządzeń przenośnych. Na przykład:<br /><br /><ul><li>Aplikacja od dostawcy podpisana przez dobrze znany urząd certyfikacji, takich jak VeriSign.</li><li>Aplikacja wewnętrzna logowania niezależna od programu Configuration Manager przy użyciu wewnętrznego urzędu certyfikacji.</li><li>Aplikacja wewnętrzna podpisana przy użyciu programu Configuration Manager utworzenia typu aplikacji i używania certyfikatu podpisywania.</li></ul>|  
|Jeżeli aplikacje urządzenia przenośnego za pomocą **Kreatora tworzenia aplikacji** w programie Configuration Manager Zabezpiecz lokalizację pliku certyfikatu podpisywania oraz kanał komunikacyjny.|Aby zapewnić ochronę przed podniesieniem uprawnień i atakami man-in--middle, przechowuj plik certyfikatu podpisywania w zabezpieczonym folderze i używaj protokołu IPsec lub bloku komunikatów serwera (SMB) między następującymi komputerami:<br /><br /><ul><li>Komputer, na którym jest uruchomiona konsola programu Configuration Manager</li><li>Komputer, który przechowuje plik certyfikatu podpisywania</li><li>Komputer, na którym są przechowywane pliki źródłowe aplikacji</li></ul> Alternatywną metodą jest podpisanie aplikacji niezależnie od programu Configuration Manager i przed uruchomieniem **Kreatora tworzenia aplikacji**.|  
|Wdróż kontrolę dostępu w celu ochrony komputerów odniesienia.|Jeżeli użytkownik administracyjny skonfigurował w typie wdrożenia metodę wykrywania przez wskazanie lokalizacji komputera odniesienia, należy się upewnić, że zabezpieczenia tego komputera nie zostały naruszone.|  
|Ogranicz i monitoruj użytkowników administracyjnych, którym przyznano role zabezpieczeń opartych na rolach w ramach zarządzania aplikacjami:<br /><br /><ul><li>**Administrator aplikacji**</li><li>**Autor aplikacji**</li><li> **Menedżer wdrażania aplikacji**</li></ul>|Nawet w przypadku skonfigurowania administracji opartej na rolach użytkownicy administracyjni tworzący i wdrażający aplikacje mogą mieć większe uprawnienia niż zakładane. Na przykład użytkownicy administracyjni, którzy tworzenia lub zmiany aplikacji można wybrać aplikacje zależne nie znajdują się w ich zakresu zabezpieczeń.|  
|Podczas konfigurowania środowisk wirtualnych Microsoft Application Virtualization (App-V), wybierz aplikacje, które mają ten sam poziom zaufania w środowisku wirtualnym.|Ponieważ aplikacje w środowisku wirtualnym App-V mogą udostępniać zasoby, takie jak zawartość Schowka, środowisko to należy skonfigurować tak, aby wybrane aplikacje miały taki sam poziom zaufania.<br /><br /> Aby uzyskać więcej informacji, zobacz [środowisk wirtualnych App-V Utwórz](../../apps/deploy-use/create-app-v-virtual-environments.md).|  
|Podczas wdrażania aplikacji na komputerach Mac należy upewnić się, że pliki źródłowe pochodzą z wiarygodnego źródła.|Narzędzie CMAppUtil nie weryfikuje podpisu pakietu źródłowego, dlatego należy się upewnić, że pochodzi on z zaufanego źródła. Narzędzie CMAppUtil nie wykrywa, czy pliki zostały naruszone.|  
|Jeśli podczas wdrażania aplikacji dla komputerów Mac należy zabezpieczyć lokalizację **.cmmac** plików oraz kanał komunikacyjny używany podczas importowania tego pliku do programu Configuration Manager.|**.Cmmac** pliku przez narzędzie CMAppUtil i importowany do programu Configuration Manager nie został podpisany ani zweryfikowany. Aby zapobiec naruszeniu tego pliku, zapisać ją w zabezpieczonym folderze i używaj protokołu IPsec lub SMB między następującymi komputerami:<br /><br /><ul><li>Komputer, na którym jest uruchomiona konsola programu Configuration Manager</li><li>Komputer, który przechowuje **.cmmac** pliku</li></ul>.|  
|Konfigurując typ wdrożenia aplikacji sieci web, należy użyć protokołu HTTPS zamiast protokołu HTTP do zabezpieczenia połączenia.|Wdrożeniem aplikacji sieci web przy użyciu łącza HTTP zamiast łącza HTTPS urządzenie może zostać przekierowane na nieautoryzowany serwer, a dane przesyłane między urządzeniem a serwerem może być naruszone.|  

##  <a name="security-issues-for-application-management"></a>Problemy z bezpieczeństwem dotyczące zarządzania aplikacjami  

-   Użytkownicy z niskimi uprawnieniami mogą kopiować pliki z pamięci podręcznej klienta na komputer kliencki.  

     Użytkownicy mogą odczytywać pamięci podręcznej klienta, ale nie można zapisać. Dzięki uprawnieniom do odczytu użytkownik może kopiować pliki instalacyjne aplikacji między komputerami.  

-   Użytkownicy z niskimi uprawnieniami można zmienić pliki służące do rejestrowania historii wdrażania oprogramowania na komputerze klienckim.  

     Ponieważ informacje o historii aplikacji nie są chronione, użytkownik może zmienić pliki, które zgłaszają, czy aplikacja jest zainstalowana.  

-   Pakiety App-V nie są podpisane.  

     Pakiety App-V w programie Configuration Manager nie obsługują podpisywania w celu weryfikacji, czy zawartość pochodzi z zaufanego źródła i czy nie została zmodyfikowana podczas przesyłania. Nie ma środki zaradcze dla tego problemu. Upewnij się, należy wykonać najlepszym rozwiązaniem bezpieczeństwa do pobierania zawartości z zaufanego źródła i z bezpiecznej lokalizacji.  

-   Publikowane aplikacje App-V mogą instalować wszyscy użytkownicy na komputerze.  

     Gdy aplikacja App-V jest publikowana na komputerze, wszyscy użytkownicy, którzy Zaloguj się na tym komputerze można zainstalować aplikację. Oznacza to, że nie można ograniczyć użytkowników, którzy mogą instalować aplikację po jej opublikowania.  

-   Nie można ograniczyć uprawnień do instalacji dla portalu firmy.  

     Mimo że można skonfigurować ustawienie klienta pozwalające ograniczyć uprawnienia do instalacji, na przykład do użytkowników podstawowych urządzenia lub tylko administratorzy lokalni, to ustawienie nie działa dla portalu firmy. Może to spowodować podniesienie uprawnień, ponieważ użytkownicy mogą zainstalować aplikację, której nie powinni zainstalować.  

##  <a name="BKMK_CertificatesSilverlight5"></a>Certyfikaty programu Microsoft Silverlight 5 i tryb podwyższonego zaufania wymagany przez katalog aplikacji  
 Klienci programu Configuration Manager wymagają programu Microsoft Silverlight 5 uruchomionego w trybie podwyższonego zaufania, aby umożliwić użytkownikom instalowanie oprogramowania z katalogu aplikacji. Domyślnie aplikacje programu Silverlight są uruchamiane w trybie częściowego zaufania, aby uniemożliwić aplikacjom uzyskiwanie dostępu do danych użytkownika. Configuration Manager automatycznie zainstaluje Microsoft Silverlight 5 na komputerach klienckich, jeśli nie jest już zainstalowany. Domyślnie program Configuration Manager ustawia Agent komputera **Pozwól na aplikacji Silverlight w trybie podwyższonego zaufania** ustawienie klienta **tak**. To ustawienie umożliwia ze znakiem i zaufanych Silverlight aplikacje żądanie trybu podwyższonego zaufania.  

 Podczas instalowania roli systemu lokacji punktu witryny sieci Web katalogu aplikacji klient instaluje również podpisywania certyfikatu w magazynie certyfikatów zaufanych wydawców komputera na każdym komputerze klienta programu Configuration Manager firmy Microsoft. Ten certyfikat umożliwia aplikacji Silverlight, które są podpisane przez ten certyfikat, uruchom w trybie podwyższonego zaufania, wymaganym przez komputery do zainstalowania oprogramowania z katalogu aplikacji. Program Configuration Manager automatycznie zarządza tym certyfikatem podpisywania. Aby zapewnić ciągłość działania usługi, nie należy ręcznie usuwać ani przenosić tego certyfikatu podpisywania firmy Microsoft.  

> [!WARNING]  
>  Po włączeniu **Pozwól na aplikacji Silverlight w trybie podwyższonego zaufania** umożliwia ustawienie klienta przechowywać wszystkie aplikacje Silverlight podpisane przez certyfikaty zaufanych wydawców certyfikatów w magazynie komputera lub użytkownika Uruchom w trybie podwyższonego zaufania. Ustawienia klienta nie można włączyć trybu podwyższonego zaufania, specjalnie dla katalogu aplikacji programu Configuration Manager lub magazynu certyfikatów zaufanych wydawców w magazynie komputera. Jeżeli złośliwe oprogramowanie korzystające z własnej aplikacji Silverlight doda nieautoryzowany certyfikat do magazynu zaufanych wydawców, na przykład w magazynie użytkownika, to oprogramowanie również będzie mogło uruchamiać się w trybie podwyższonego zaufania.  

 Jeśli ustawisz **Pozwól na aplikacji Silverlight w trybie podwyższonego zaufania** ustawienie klienta **nr**, nie powoduje usunięcia certyfikatu podpisywania firmy Microsoft z klientów.  

 Aby uzyskać więcej informacji o zaufane aplikacje w technologii Silverlight, zobacz [zaufane aplikacje](http://go.microsoft.com/fwlink/p/?LinkId=252842).  

##  <a name="privacy-information-for-application-management"></a>Informacje o ochronie prywatności dotyczące zarządzania aplikacjami  
 Zarządzanie aplikacjami umożliwia uruchamianie żadnych aplikacji, programów lub skryptu na każdym komputerze klienckim albo urządzeniu przenośnym w hierarchii. Menedżer konfiguracji nie może kontrolować typów aplikacji, programów lub skryptów, które można uruchomić lub typu informacji o przekazywaniu. Podczas procesu wdrażania aplikacji programu Configuration Manager może przesyłać informacji, które identyfikują urządzenie i konta logowania między klientami a serwerami.  

 Program Configuration Manager przechowuje informacjami o stanie procesu wdrażania oprogramowania. Informacje o stanie wdrażania oprogramowania nie są szyfrowane podczas przesyłania z wyjątkiem sytuacji, w której klient komunikuje się za pomocą protokołu HTTPS. Informacje o stanie nie są przechowywane w zaszyfrowanym formacie w bazie danych.  

 Korzystanie z instalacji aplikacji programu Configuration Manager do zdalnego, interakcyjnego lub cichego instalowania oprogramowania na klientach może podlegać postanowień licencyjnych dotyczących oprogramowania. Użyj tego jest niezależna od postanowienia licencyjne dotyczące oprogramowania System Center Configuration Manager. Zawsze należy przeczytać i zaakceptować postanowienia licencyjne dotyczące oprogramowania przed wdrożeniem oprogramowania za pomocą programu Configuration Manager.  

 Wdrożenie aplikacji nie jest realizowane domyślnie i wymaga wykonania kilku czynności konfiguracyjnych.  

 Dwie opcjonalne funkcje, które ułatwiają efektywne wdrażanie oprogramowania, to koligacja urządzenia użytkownika i katalog aplikacji:  

-   Koligacja urządzenia użytkownika mapować użytkowników na urządzeniach, aby administrator programu Configuration Manager można wdrażać oprogramowanie do użytkownika, a oprogramowanie jest automatycznie instalowany na co najmniej jeden komputer, z których użytkownik korzysta najczęściej.  

-   Katalog aplikacji to witryna sieci Web umożliwiająca instalacji oprogramowania żądania użytkowników.  

 W poniższych sekcjach znajdują się informacje o ochronie prywatności związane z funkcją koligacji urządzenia użytkownika oraz z katalogiem aplikacji.  

 Przed skonfigurowaniem zarządzania aplikacjami należy wziąć pod uwagę wymogi związane z ochroną prywatności.  

##  <a name="user-device-affinity"></a>Koligacja urządzenia użytkownika  
-  Menedżer konfiguracji może przesyłać informacje między klientami i systemami lokacji punktu zarządzania. Informacje może zidentyfikować konta komputera i zaloguj się i podsumowują wykorzystanie kont logowania.  
-  Informacje przesyłane między klientem i serwerem nie są szyfrowane, chyba że punkt zarządzania jest skonfigurowany do żądania klientów do komunikacji przy użyciu protokołu HTTPS.  
-  Informacji użycia konta komputera i logowanie służący do mapowania użytkownika na urządzeniu są przechowywane na komputerach klienckich, wysyłane do punktów zarządzania i następnie przechowywane w bazie danych programu Configuration Manager. Stare informacje są usuwane z bazy danych domyślnie po 90 dniach. Sposób usuwania można skonfigurować za pomocą zadania konserwacji lokacji **Usuń przestarzałe dane koligacji urządzenia użytkownika** .
-  Configuration Manager przechowuje informacje o stanie o koligacji urządzenia użytkownika. Informacje o stanie nie są szyfrowane podczas przesyłania z wyjątkiem sytuacji, w której klienci są skonfigurowani do komunikowania się z punktami zarządzania za pomocą protokołu HTTPS. Informacje o stanie nie są przechowywane w zaszyfrowanym formacie w bazie danych.  
-  Komputer, informacje o wykorzystaniu konta logowania i informacje o stanie nie są wysyłane do firmy Microsoft.  
-  Informacje o wykorzystaniu komputer i zaloguj się, które są używane do ustanawiania koligacji użytkownika i urządzenia jest zawsze włączone. Ponadto informacje o koligacji urządzenia użytkownika mogą być dostarczane przez użytkowników i użytkowników administracyjnych.  

##  <a name="application-catalog"></a>Katalog aplikacji  
-  Katalog aplikacji pozwala publikować dowolne aplikacji lub skryptu dla użytkowników, aby uruchomić administratora programu Configuration Manager. Menedżer konfiguracji nie może kontrolować typów programów lub skryptów, które są publikowane w katalogu lub typu informacji o przekazywaniu.    
-  Menedżer konfiguracji może przesyłać informacje między klientami a rolami systemu lokacji katalogu aplikacji. Informacje może zidentyfikować konta komputera i logowania. Informacje przesyłane między klientem i serwerami nie są szyfrowane, chyba że te role systemu lokacji są skonfigurowane do żądania od klientów nawiązywania połączenia za pomocą protokołu HTTPS.  
-  Informacje o żądaniu zatwierdzenia aplikacji są przechowywane w bazie danych programu Configuration Manager. Żądania, które są anulowane lub odrzucane i odnośnymi wpisami historii żądań są domyślnie usuwane po 30 dniach. Sposób usuwania można skonfigurować za pomocą zadania konserwacji lokacji **Usuń przestarzałe dane żądania aplikacji** . Żądania zatwierdzenia aplikacji, które mają stan zatwierdzony lub oczekujący nigdy nie są usuwane.  
-  Informacje wysyłane do katalogu aplikacji oraz z niego nie są wysyłane do firmy Microsoft.  
-  Katalog aplikacji nie jest instalowany domyślnie. Jego instalacja wymaga wykonania kilku czynności konfiguracyjnych.  

