---
title: "Bezpieczeństwo i prywatność zarządzania aplikacjami"
titleSuffix: Configuration Manager
description: "Zabezpieczenia i prywatność najlepsze rozwiązania dotyczące zarządzania aplikacjami w programie System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4d26deed-3b16-4116-b640-f618f2c20f5a
caps.latest.revision: "8"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.openlocfilehash: 7ca91443af58fc342380b819ca53e42b75556090
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="security-and-privacy-for-application-management-in-system-center-configuration-manager"></a>Zabezpieczenia i prywatność zarządzania aplikacjami w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


##  <a name="security-best-practices-for-application-management"></a>Najlepsze rozwiązania dotyczące zarządzania aplikacjami  

|Najlepsze rozwiązanie w zakresie zabezpieczeń|Więcej informacji|  
|----------------------------|----------------------|  
|Skonfiguruj punkty katalogu aplikacji, aby używały połączeń przy użyciu protokołu HTTPS, i poinformuj użytkowników o zagrożeniach związanych ze złośliwymi witrynami sieci web.|Skonfiguruj punkty witryny sieci web oraz usługi sieci web katalogu aplikacji, aby akceptowały połączenia przy użyciu protokołu HTTPS. Pozwoli to na uwierzytelnianie serwera dla użytkowników oraz zapewni ochronę przesyłanych danych przed naruszeniem i wyświetlaniem. Aby zapobiec atakom przy użyciu inżynierii społecznej, należy poinformować użytkowników o konieczności łączenia się tylko z zaufanymi witrynami sieci web.<br /><br /> Nie należy używać znakowania opcje konfiguracji, które Pokaż nazwę organizacji w katalogu aplikacji jako potwierdzenie tożsamości, gdy nie należy używać protokołu HTTPS.|  
|Zastosuj separację roli i zainstaluj punkty witryny sieci web oraz usługi katalogu aplikacji na oddzielnych serwerach.|W przypadku złamania zabezpieczeń punktu witryny sieci Web katalogu aplikacji, należy go zainstalować na innym serwerze niż punkt usługi sieci web katalogu aplikacji. Zapewni to ochronę klientów programu Configuration Manager i infrastruktury programu Configuration Manager. Jest to szczególnie ważne, gdy punkt witryny sieci web katalogu aplikacji akceptuje połączenia przez Internet, ponieważ przy takiej konfiguracji serwer jest narażony na ataki.|  
|Poinformuj użytkowników o konieczności zamykania okna przeglądarki po zakończeniu korzystania z katalogu aplikacji.|Jeżeli użytkownicy przeglądają zewnętrzną witrynę sieci web w oknie przeglądarki używanym w ramach katalogu aplikacji, przeglądarka nadal używa ustawień zabezpieczeń odpowiednich do zaufanych witryn w sieci intranet.|  
|Ręcznie określić koligację urządzenia użytkownika zamiast umożliwiając użytkownikom identyfikację ich urządzenia podstawowego. Nie należy włączać konfiguracji opartej na użyciu.|Nie należy traktować informacji zebranych od użytkowników lub z urządzenia jako autorytatywnych. Podczas wdrażania oprogramowania przy użyciu konfiguracji koligacji urządzenia użytkownika,nieokreślonej przez zaufanego użytkownika administracyjnego oprogramowanie może zostać zainstalowane na komputerach oraz dla użytkowników niemających uprawnień do jego otrzymania.|  
|Wdrożenia należy zawsze konfigurować tak, aby pobierały zawartość z punktów dystrybucji, a nie były uruchamiane z tych punktów.|Po skonfigurowaniu wdrożeń, aby pobrać zawartość z punktu dystrybucji i uruchamiały się lokalnie, programu Configuration Manager klient sprawdza, czy skrót pakietu po pobraniu zawartości. Klient odrzuca pakiet, jeśli skrót nie jest zgodny ze skrótem określonym w zasadach. Z kolei jeśli skonfigurować wdrożenie w celu uruchomienia bezpośrednio z punktu dystrybucji klienta programu Configuration Manager nie sprawdza skrótu pakietu, co oznacza, że Menedżer konfiguracji klienta można zainstalować oprogramowania, które zostały naruszone.<br /><br /> W przypadku konieczności uruchamiania wdrożeń bezpośrednio z punktów dystrybucji, należy użyć systemu plików NTFS co najmniej uprawnienia do pakietów w punktach dystrybucji i użyj zabezpieczeń protokołu internetowego (IPsec), aby zabezpieczyć kanał między klientem a punktami dystrybucji oraz między punktami dystrybucji a serwerem lokacji.|  
|Zezwala użytkownikom na interakcję z programami, gdy **Uruchom z prawami administracyjnymi** opcja jest wymagana.|Podczas konfigurowania programu można ustawić **Zezwalaj użytkownikom na interakcję z tym programem** opcję, aby umożliwić użytkownikom reagowanie na wszystkie wymagane monity w interfejsie użytkownika. Jeżeli w programie skonfigurowano również ustawienie **Uruchom z prawami administracyjny**, osoba atakująca na komputerze z uruchomionym programem może przy użyciu interfejsu użytkownika eskalować uprawnienia na komputerze klienckim.<br /><br /> Użyj programy, które dla instalacji i użytkownika podniesione uprawnienia w celu wdrożenia oprogramowania, które wymagają poświadczeń administracyjnych, używając Instalatora Windows. Instalator musi działać w kontekście użytkownika, który nie ma poświadczeń administracyjnych. Instalator Windows na użytkownika podwyższonego poziomu uprawnień Podaj najbezpieczniejszą metodą wdrażania aplikacji, które wymagają tej opcji.|  
|Zdecyduj, czy ograniczyć użytkownikom możliwość interaktywnego instalowania oprogramowania przy użyciu ustawienia klienta **Uprawnienia do instalacji** .|Skonfiguruj **Agent komputera** urządzenia klienckiego **uprawnienia do instalacji** ustawienie, aby określić typy użytkowników, którzy mogą instalować oprogramowanie przy użyciu katalogu aplikacji lub Centrum oprogramowania. Utwórz na przykład niestandardowe ustawienie klienta, wybierając w ustawieniu **Uprawnienia do instalacji** opcję **Tylko administratorzy**. Następnie Zastosuj to ustawienie w kolekcji serwerów, aby uniemożliwić użytkownikom bez uprawnień administracyjnych instalowanie oprogramowania na tych komputerach.|  
|Dla urządzeń przenośnych należy wdrażać tylko te aplikacje, które są podpisane.|Wdrażanie aplikacji urządzenia przenośnego, tylko wtedy, gdy są one kod podpisany przez urząd certyfikacji (CA), który jest zaufany dla urządzeń przenośnych. Na przykład:<br /><br /><ul><li>Aplikacja od dostawcy podpisana przez dobrze znany urząd certyfikacji, takich jak VeriSign.</li><li>Aplikacja wewnętrzna podpisanie niezależna od programu Configuration Manager za pomocą wewnętrznego urzędu certyfikacji.</li><li>Aplikacja wewnętrzna podpisana przy użyciu programu Configuration Manager w przypadku utworzenia typu aplikacji i używania certyfikatu podpisywania.</li></ul>|  
|Jeżeli aplikacje urządzenia przenośnego zostały podpisane za pomocą **Kreatora tworzenia aplikacji** w programie Configuration Manager Zabezpiecz lokalizację pliku certyfikatu podpisywania oraz kanał komunikacyjny.|Aby ułatwić ochronę przed podniesieniem uprawnień i przed atakami typu man-in--middle, przechowywania pliku certyfikatu podpisywania w zabezpieczonym folderze i używaj protokołu IPsec lub bloku komunikatów serwera (SMB) między następującymi komputerami:<br /><br /><ul><li>Komputer, na którym uruchomiona jest konsola programu Configuration Manager</li><li>Komputer, który przechowuje certyfikat podpisywania plików</li><li>Komputera, na którym są przechowywane pliki źródłowe aplikacji</li></ul> Alternatywną metodą jest podpisanie aplikacji niezależnie od programu Configuration Manager i przed uruchomieniem **Kreatora tworzenia aplikacji**.|  
|Wdróż kontrolę dostępu w celu ochrony komputerów odniesienia.|Jeżeli użytkownik administracyjny skonfigurował w typie wdrożenia metodę wykrywania przez wskazanie lokalizacji komputera odniesienia, należy się upewnić, że zabezpieczenia tego komputera nie zostały naruszone.|  
|Ogranicz i monitoruj użytkowników administracyjnych, którym przyznano role zabezpieczeń opartych na rolach w ramach zarządzania aplikacjami:<br /><br /><ul><li>**Administrator aplikacji**</li><li>**Autor aplikacji**</li><li> **Menedżer wdrażania aplikacji**</li></ul>|Nawet w przypadku skonfigurowania administracji opartej na rolach użytkownicy administracyjni tworzący i wdrażający aplikacje mogą mieć większe uprawnienia niż zakładane. Na przykład użytkownicy administracyjni, którzy tworzenia lub zmiany aplikacji można wybrać aplikacje zależne nie znajdują się w ich zakresie zabezpieczeń.|  
|Podczas konfigurowania środowisk wirtualnych Microsoft Application Virtualization (App-V), wybierz aplikacje, które mają taki sam poziom zaufania w środowisku wirtualnym.|Ponieważ aplikacje w środowisku wirtualnym App-V mogą udostępniać zasoby, takie jak Schowek, skonfiguruj środowisko wirtualne, aby wybrane aplikacje miały taki sam poziom zaufania.<br /><br /> Aby uzyskać więcej informacji, zobacz [środowisk wirtualnych App-V Utwórz](../../apps/deploy-use/create-app-v-virtual-environments.md).|  
|Podczas wdrażania aplikacji na komputerach Mac należy upewnić się, że pliki źródłowe pochodzą z wiarygodnego źródła.|Narzędzie CMAppUtil nie weryfikuje podpisu pakietu źródłowego, dlatego należy się upewnić, że pochodzi on z zaufanego źródła. Narzędzie CMAppUtil nie może wykryć, czy pliki zostały naruszone.|  
|W przypadku wdrażania aplikacji dla komputerów Mac należy zabezpieczyć lokalizację pliku **cmmac** plik i kanał komunikacyjny używany podczas importowania tego pliku do programu Configuration Manager.|**Cmmac** pliku przez narzędzie CMAppUtil i importowany do programu Configuration Manager nie został podpisany ani zweryfikowany. Aby zapobiec naruszeniu tego pliku, zapisz go w zabezpieczonym folderze i używaj protokołu IPsec lub SMB między następującymi komputerami:<br /><br /><ul><li>Komputer, na którym uruchomiona jest konsola programu Configuration Manager</li><li>Komputer, który przechowuje **cmmac** pliku</li></ul>.|  
|Konfigurując typ wdrożenia aplikacji sieci web, użyj protokołu HTTPS zamiast protokołu HTTP do bezpiecznego połączenia.|Jeśli wdrożysz aplikację sieci web przy użyciu łącza HTTP zamiast łącza HTTPS urządzenie może zostać przekierowane na nieautoryzowany serwer i może być zmodyfikowany dane przesyłane między urządzeniem a serwerem.|  

##  <a name="security-issues-for-application-management"></a>Problemy z bezpieczeństwem dotyczące zarządzania aplikacjami  

-   Użytkownicy z niskimi uprawnieniami mogą kopiować pliki z pamięci podręcznej klienta na komputer kliencki.  

     Użytkownicy mogą odczytywać pamięci podręcznej klienta, ale nie można zapisać. Dzięki uprawnieniom do odczytu użytkownik może kopiować pliki instalacyjne aplikacji między komputerami.  

-   Użytkownicy z niskimi uprawnieniami można zmienić pliki służące do rejestrowania historii wdrażania oprogramowania na komputerze klienckim.  

     Ponieważ informacje o historii aplikacji nie są chronione, użytkownik może zmienić pliki, które zgłaszają, czy aplikacja jest zainstalowana.  

-   Pakiety App-V nie są podpisane.  

     Pakiety App-V w programie Configuration Manager nie obsługują podpisywania w celu weryfikacji, czy zawartość pochodzi z zaufanego źródła i czy nie została zmodyfikowana podczas przesyłania. Środki zaradcze dla tego problemu nie istnieje. Upewnij się, że stosujesz najlepszym rozwiązaniem bezpieczeństwa próbę pobrania zawartości z zaufanego źródła i z bezpiecznej lokalizacji.  

-   Publikowane aplikacje App-V mogą instalować wszyscy użytkownicy na komputerze.  

     Po opublikowaniu aplikacji App-V na komputerze, wszyscy użytkownicy, którzy zalogować się na tym komputerze można zainstalować aplikację. Oznacza to, że nie można ograniczyć użytkowników, którzy mogą zainstalować aplikację po jej opublikowania.  

-   Nie można ograniczyć uprawnień do instalacji dla portalu firmy.  

     Mimo że można skonfigurować ustawienie klienta pozwalające ograniczyć uprawnienia do instalacji, na przykład aby użytkowników podstawowych urządzenia lub tylko administratorzy lokalni, to ustawienie nie działa w przypadku portalu firmy. Może to spowodować podniesienie uprawnień, ponieważ użytkownicy będą mogli instalować aplikację, która nie powinien być dozwolony do zainstalowania.  

##  <a name="BKMK_CertificatesSilverlight5"></a>Certyfikaty dla programu Microsoft Silverlight 5 i tryb podwyższonego zaufania wymagany przez katalog aplikacji  
 Klienci programu Configuration Manager wymagają programu Microsoft Silverlight 5 uruchomionego w trybie podwyższonego zaufania, aby umożliwić użytkownikom instalowanie oprogramowania z katalogu aplikacji. Domyślnie aplikacje programu Silverlight są uruchamiane w trybie częściowego zaufania, aby uniemożliwić aplikacjom uzyskiwanie dostępu do danych użytkownika. Jeśli nie jest już zainstalowany Configuration Manager automatycznie instaluje program Microsoft Silverlight 5 na klientach. Domyślnie program Configuration Manager ustawia Agent komputera **Pozwól na uruchamianie w trybie podwyższonego zaufania aplikacji Silverlight** ustawienia klienta dotyczącego **tak**. To ustawienie umożliwia podpisane i zaufane Silverlight aplikacji żądanie trybu podwyższonego zaufania.  

 Podczas instalowania roli systemu lokacji punktu witryny sieci Web katalogu aplikacji klient instaluje również podpisywania certyfikatu w magazynie certyfikatów komputera zaufanych wydawców na każdym komputerze klienckim programu Configuration Manager firmy Microsoft. Ten certyfikat umożliwia aplikacji Silverlight, które są podpisane przez ten certyfikat, uruchom w trybie podwyższonego zaufania, które komputery wymagają do instalacji oprogramowania z katalogu aplikacji. Menedżer konfiguracji automatycznie zarządza tym certyfikatem podpisywania. Aby zapewnić ciągłość działania usługi, nie należy ręcznie usuwać ani przenosić tego certyfikatu podpisywania firmy Microsoft.  

> [!WARNING]  
>  Po włączeniu **Pozwól na uruchamianie w trybie podwyższonego zaufania aplikacji Silverlight** Uruchom wszystkie aplikacje Silverlight podpisane przez certyfikaty zaufanych wydawców certyfikatów są przechowywane w magazynie komputera lub użytkownika umożliwia ustawienie klienta w trybie podwyższonego zaufania. Ustawienia klienta nie można włączyć trybu podwyższonego zaufania, specjalnie dla katalogu aplikacji programu Configuration Manager lub do magazynu certyfikatów zaufanych wydawców w magazynie komputera. Jeżeli złośliwe oprogramowanie korzystające z własnej aplikacji Silverlight doda nieautoryzowany certyfikat do magazynu zaufanych wydawców, na przykład w magazynie użytkownika, to oprogramowanie również będzie mogło uruchamiać się w trybie podwyższonego zaufania.  

 Jeśli ustawisz **Pozwól na uruchamianie w trybie podwyższonego zaufania aplikacji Silverlight** ustawienia klienta dotyczącego **nr**, nie powoduje usunięcia certyfikatu podpisywania firmy Microsoft z klientów.  

 Aby uzyskać więcej informacji o zaufanych aplikacjach w programie Silverlight, zobacz [zaufane aplikacje](http://go.microsoft.com/fwlink/p/?LinkId=252842).  

##  <a name="privacy-information-for-application-management"></a>Informacje o ochronie prywatności dotyczące zarządzania aplikacjami  
 Zarządzanie aplikacjami umożliwia uruchamianie dowolnej aplikacji, program lub skrypt na każdym komputerze klienckim albo urządzeniu przenośnym w hierarchii. Menedżer konfiguracji nie ma kontroli nad typy aplikacji, programów lub skryptów, które zostanie uruchomione lub typ danych przesyłanych za ich pośrednictwem. Podczas procesu wdrażania aplikacji programu Configuration Manager może przesyłać informacji, które identyfikują urządzenie i konta logowania między klientami a serwerami.  

 Configuration Manager przechowuje informacjami o stanie procesu wdrażania oprogramowania. Informacje o stanie wdrażania oprogramowania nie są szyfrowane podczas przesyłania z wyjątkiem sytuacji, w której klient komunikuje się za pomocą protokołu HTTPS. Informacje o stanie nie są przechowywane w zaszyfrowanym formacie w bazie danych.  

 Użycie instalacji aplikacji programu Configuration Manager do zdalnego, interakcyjnego lub cichego instalowania oprogramowania na klientach może być postanowieniom licencyjnym dotyczącym tego oprogramowania. To są oddzielne od postanowień licencyjnych oprogramowania System Center Configuration Manager. Zawsze Przejrzyj i zaakceptuj postanowienia licencyjne dotyczące oprogramowania przed wdrożeniem oprogramowania za pomocą programu Configuration Manager.  

 Wdrożenie aplikacji nie odbywa się domyślnie i wymaga wykonania kilku czynności konfiguracyjnych.  

 Dwie opcjonalne funkcje, które ułatwiają efektywne wdrażanie oprogramowania, to koligacja urządzenia użytkownika i katalog aplikacji:  

-   Koligacja urządzenia użytkownika mapować użytkowników na urządzenia, aby administrator programu Configuration Manager można wdrażać oprogramowanie do użytkownika, a na co najmniej jeden komputer, na które użytkownik korzysta najczęściej automatycznie instalować to oprogramowanie.  

-   Katalog aplikacji to witryna sieci Web umożliwiająca użytkownikom żądanie oprogramowania do zainstalowania.  

 W poniższych sekcjach znajdują się informacje o ochronie prywatności związane z funkcją koligacji urządzenia użytkownika oraz z katalogiem aplikacji.  

 Przed skonfigurowaniem zarządzania aplikacjami należy wziąć pod uwagę wymogi związane z ochroną prywatności.  

##  <a name="user-device-affinity"></a>Koligacja urządzenia użytkownika  
-  Menedżer konfiguracji może przesyłać informacje między klientami i systemami lokacji punktu zarządzania. Informacje może zidentyfikować konta komputera i logowania oraz podsumowują wykorzystanie kont logowania.  
-  Informacje przesyłane między klientem a serwerem nie są szyfrowane, chyba że punkt zarządzania jest skonfigurowany do żądania klientów do komunikacji przy użyciu protokołu HTTPS.  
-  Informacje użycia konta komputera i logowania używany do mapowania użytkownika na urządzeniu jest przechowywane na komputerach klienckich, wysyłane do punktów zarządzania, a następnie przechowywane w bazie danych programu Configuration Manager. Stare informacje są usuwane z bazy danych domyślnie po 90 dniach. Sposób usuwania można skonfigurować za pomocą zadania konserwacji lokacji **Usuń przestarzałe dane koligacji urządzenia użytkownika** .
-  Configuration Manager przechowuje informacje o stanie o koligacji urządzenia użytkownika. Informacje o stanie nie są szyfrowane podczas przesyłania z wyjątkiem sytuacji, w której klienci są skonfigurowani do komunikowania się z punktami zarządzania za pomocą protokołu HTTPS. Informacje o stanie nie są przechowywane w zaszyfrowanym formacie w bazie danych.  
-  Komputer, informacje o wykorzystaniu konta logowania oraz informacje o stanie nie są wysyłane do firmy Microsoft.  
-  Informacje o wykorzystaniu komputera i logowania, które służy do ustanawiania koligacji użytkownika i urządzenia jest zawsze włączone. Ponadto informacje o koligacji urządzenia użytkownika mogą być dostarczane przez użytkowników i użytkowników administracyjnych.  

##  <a name="application-catalog"></a>Katalog aplikacji  
-  Katalog aplikacji pozwala administratorowi programu Configuration Manager opublikować dowolną aplikację lub program lub użytkownikom na uruchamianie skryptu. Menedżer konfiguracji nie ma kontroli nad rodzaje programów lub skryptów, które są publikowane w katalogu lub typ danych przesyłanych za ich pośrednictwem.    
-  Menedżer konfiguracji może przesyłać informacje między klientami i rolami systemu lokacji katalogu aplikacji. Informacje może zidentyfikować konta komputera i logowania. Informacje przesyłane między klientem i serwerami nie są szyfrowane, chyba że te role systemu lokacji są skonfigurowane do żądania od klientów nawiązywania połączenia za pomocą protokołu HTTPS.  
-  Informacje o żądaniu zatwierdzenia aplikacji są przechowywane w bazie danych programu Configuration Manager. Żądania, które są anulowane lub odrzucane i odnośnymi wpisami historii żądań są domyślnie usuwane po 30 dniach. Sposób usuwania można skonfigurować za pomocą zadania konserwacji lokacji **Usuń przestarzałe dane żądania aplikacji** . Żądania zatwierdzenia aplikacji, które są w zatwierdzone i do czasu stanów nigdy nie są usuwane.  
-  Informacje wysyłane do katalogu aplikacji oraz z niego nie są wysyłane do firmy Microsoft.  
-  Katalog aplikacji nie jest instalowany domyślnie. Jego instalacja wymaga wykonania kilku czynności konfiguracyjnych.  
