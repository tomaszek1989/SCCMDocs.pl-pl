---
title: "Informacje techniczne dotyczące formantów kryptograficznych"
titleSuffix: Configuration Manager
description: "Dowiedz się, jak podpisywania i szyfrowania może pomóc chronić ataków odczytywania danych w programie System Center Configuration Manager."
ms.custom: na
ms.date: 12/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 2c1ed6f4c93f74719ab3fe5d723f7dc01eb1ede7
ms.sourcegitcommit: 08f9854fb6c6d21e1e923b13e38a64d0bc2bc9a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2017
---
# <a name="cryptographic-controls-technical-reference"></a>Informacje techniczne dotyczące formantów kryptograficznych

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


System Center Configuration Manager korzysta z podpisywania i szyfrowania, aby ułatwić ochronę zarządzania urządzeniami w hierarchii programu Configuration Manager. Podpisywania, jeśli dane zostały zmienione podczas przesyłania, zostanie odrzucone. Szyfrowanie uniemożliwia osobie atakującej odczytanie danych przy użyciu analizatora protokołów sieciowych.  

 Podstawowy algorytmu wyznaczania wartości skrótu, który używa programu Configuration Manager do podpisywania jest algorytm SHA-256. Gdy dwie lokacje programu Configuration Manager komunikują się ze sobą, podpisują komunikację z algorytmu SHA-256. Podstawowym algorytmem szyfrowania zaimplementowany w programie Configuration Manager jest algorytm 3DES. Służy do przechowywania danych w bazie danych programu Configuration Manager i komunikacji klienta HTTP. Korzystając z komunikacji z klientem za pośrednictwem protokołu HTTPS, można skonfigurować infrastrukturę kluczy publicznych (PKI), aby używane były certyfikaty RSA z maksymalnymi algorytmami wyznaczania wartości skrótu i długościami kluczy udokumentowanymi w temacie [wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager](../../core/plan-design/network/pki-certificate-requirements.md).  

 Dla większości operacji kryptograficznych dla systemów operacyjnych opartych na systemie Windows program Configuration Manager używa algorytmów SHA-2, 3DES i AES oraz RSA z Windows CryptoAPI rsaenh.dll biblioteki.  

> [!IMPORTANT]  
>  Zobacz informacje o zalecanych zmianach w odpowiedzi na luki w zabezpieczeniach protokołu SSL [o SSL luk w zabezpieczeniach](#about-ssl-vulnerabilities).  

##  <a name="cryptographic-controls-for-configuration-manager-operations"></a>Formanty kryptograficzne operacji programu Configuration Manager  
 Informacje w programie Configuration Manager mogą być podpisane i zaszyfrowane, czy używać certyfikatów PKI z programem Configuration Manager.  

### <a name="policy-signing-and-encryption"></a>Podpisywanie i szyfrowanie zasad  
 Przypisania zasad klienta są podpisywane za pomocą certyfikatu podpisującego serwer lokacji z podpisem własnym w celu przeciwdziałania zagrożeniu bezpieczeństwa związanemu z wysyłaniem naruszonych zasad przez punkt zarządzania ze złamanymi zabezpieczeniami. Jest to ważne, jeśli używasz klienta internetowego zarządzania, ponieważ to środowisko wymaga punktu zarządzania obsługującego komunikację z Internetem.  

 Zasady jest szyfrowana za 3DES, gdy zawiera poufne dane. Zasady zawierające dane poufne są wysyłane wyłącznie do autoryzowanych klientów. Zasady nie zawierające danych poufnych nie są szyfrowane.  

 Jeśli zasady są przechowywane na komputerach klienckich, są szyfrowane z interfejsu programowania aplikacji ochrony danych (DPAPI).  

### <a name="policy-hashing"></a>Generowanie skrótów zasad  
 Gdy klienci programu Configuration Manager żądają zasad, otrzymują najpierw przypisanie zasad, aby wiedzieli, których zasady są stosowane do nich, a następnie żądają tylko tych treści zasad. Wszystkie przypisania zasad zawierają skrót obliczony dla odpowiedniej treści zasad. Klient pobiera odpowiednie treści zasad, a następnie oblicza skrót danej treści. Jeśli skrót pobranej treści zasad jest niezgodny ze skrótem w przypisaniu zasad, klient odrzuci treść zasad.  

 Algorytmami wyznaczania wartości skrótu dla zasad są algorytmy SHA-1 i SHA-256.  

### <a name="content-hashing"></a>Generowanie skrótów zawartości  
 Usługa menedżera dystrybucji na serwerze lokacji generuje skróty plików zawartości wszystkich pakietów. Dostawca zasad dołącza skrót do zasad dystrybucji oprogramowania. Gdy klient programu Configuration Manager pobiera zawartość, klient ponownie generuje skrót lokalnie i porównuje go do skrótu dostarczonego z zasadami. Jeśli skróty są zgodne, zawartość nie została zmodyfikowana i klient ją zainstaluje. Zmodyfikowanie nawet jednego bajtu zawartości spowoduje niezgodność skrótów, a oprogramowanie nie zostanie zainstalowane. Ta kontrola zapewnia zainstalowanie prawidłowego oprogramowania, ponieważ rzeczywista treść jest porównywana z zasadami.  

 Domyślnym algorytmem wyznaczania wartości skrótu zawartości jest algorytm SHA-256. Aby zmienić to ustawienie domyślne, zobacz dokumentację dla Configuration Manager Software Development Kit (SDK).  

 Nie wszystkie urządzenia obsługują generowanie skrótów zawartości. Do wyjątków należą:  

-   Klienci systemu Windows przesyłający strumieniowo zawartość App-V.  

-   Klienci Windows Phone, że ci klienci weryfikują podpis aplikacji podpisanej przez zaufane źródło.  

-   Klient z systemem Windows RT, że ci klienci weryfikują podpis aplikacji podpisanej przez zaufane źródło, a ponadto używają walidacji pełnej nazwy (PFN) dla pakietu.  

-   systemy iOS, że te urządzenia weryfikują podpis aplikacji podpisanej przez dowolny certyfikat dewelopera z zaufanego źródła.  

-   Klient Nokia, jednak ci klienci weryfikują podpis aplikacji korzystającej z certyfikatu z podpisem własnym. Podpis certyfikatu z zaufanego źródła i certyfikat mogą również podpisywać aplikacje SIS (Symbian Installation Source) firmy Nokia.  

-   Urządzenia z systemem Android. Te urządzenia nie stosują ponadto walidacji podpisu w celu instalowania aplikacji.  

-   Klienci korzystający z systemów Linux i UNIX w wersjach, które nie obsługują algorytmu SHA-256. Aby uzyskać więcej informacji, zobacz [Planowanie wdrożenia klientów na komputerach UNIX i Linux w programie System Center Configuration Manager](../../core/clients/deploy/plan/planning-for-client-deployment-to-linux-and-unix-computers.md).  

### <a name="inventory-signing-and-encryption"></a>Spis podpisywania i szyfrowania  
 Zapasy wysyłane przez klientów do punktów zarządzania są zawsze podpisane przez urządzenia, niezależnie od tego, czy komunikują się one z punktami zarządzania za pośrednictwem protokołu HTTP lub HTTPS. Jeśli korzystają z protokołu HTTP, użytkownik może zaszyfrować te dane, co jest najlepszym rozwiązaniem w zakresie zabezpieczeń.  

### <a name="state-migration-encryption"></a>Szyfrowanie migracji stanu  
 Dane przechowywane w punktach migracji stanu w celu wdrażania systemów operacyjnych są zawsze zaszyfrowane za pomocą narzędzia do migracji stanu użytkowników (USMT) i algorytmu 3DES.  

### <a name="encryption-for-multicast-packages-to-deploy-operating-systems"></a>Szyfrowanie pakietów multiemisji do wdrażania systemów operacyjnych  
 Szyfrowanie można włączyć dla każdego pakietu wdrożeniowego systemu operacyjnego, jeśli pakiet jest transferowany na komputery przy użyciu multiemisji. Szyfrowanie używa standardu AES (Advanced Encryption Standard). Po włączeniu szyfrowania dodatkowa konfiguracja certyfikatów nie jest wymagana. Punkt dystrybucji z obsługą multiemisji automatycznie generuje klucze symetryczne do szyfrowania pakietu. Każdy pakiet ma inny klucz szyfrowania. Klucz jest przechowywany w punkcie dystrybucji z obsługą multiemisji przy użyciu standardowych interfejsów API systemu Windows. Gdy klient nawiąże połączenie z sesją multiemisji, wymiana kluczy nastąpi przez kanał zaszyfrowany za pomocą certyfikatu uwierzytelniania klienta wystawionego przez infrastrukturę PKI (jeśli klient korzysta z protokołu HTTPS) lub certyfikatu z podpisem własnym (jeśli klient korzysta z protokołu HTTP). Klient przechowuje klucz w pamięci tylko przez okres trwania sesji multiemisji.  

### <a name="encryption-for-media-to-deploy-operating-systems"></a>Szyfrowanie nośników do wdrażania systemów operacyjnych  
 Jeśli systemy operacyjne za wdrażane za pomocą nośników, dla których określono hasło, zmienne środowiskowe są zaszyfrowane przy użyciu standardu AES (Advanced Encryption Standard). Inne dane na nośnikach, w tym pakiety i zawartość aplikacji, nie są zaszyfrowane.  

### <a name="encryption-for-content-that-is-hosted-on-cloud-based-distribution-points"></a>Szyfrowanie zawartości hostowanej w punktach dystrybucji w chmurze  
 Od programu System Center 2012 Configuration Manager SP1, korzystając z punktów dystrybucji w chmurze, zawartość wysyłana do tych punktów dystrybucji są szyfrowane przy użyciu standardowych AES (Advanced Encryption) 256-bitowym kluczem o rozmiarze. Zawartość jest ponownie szyfrowana po każdej aktualizacji. Gdy klienci pobierają zawartość, jest ona zaszyfrowana i chroniona za pomocą połączenia HTTPS.  

### <a name="signing-in-software-updates"></a>Podpisywanie aktualizacji oprogramowania  
 Wszystkie aktualizacje oprogramowania muszą być podpisane przez zaufanego wydawcę, aby chronić je przed naruszeniem. Usługa Windows Update Agent (WUA) skanuje katalog w poszukiwaniu aktualizacji na komputerach klienckich, nie zainstaluje ich jednak, jeśli nie będzie mogła zlokalizować certyfikatu cyfrowego w magazynie zaufanych wydawców na komputerze lokalnym. Jeśli w celu opublikowania katalogu aktualizacji użyto certyfikatu z podpisem własnym, na przykład certyfikatu WSUS Publishers Self-signed, certyfikat ten musi się również znajdować w magazynie certyfikatów zaufanych głównych urzędów certyfikacji na komputerze lokalnym w celu zweryfikowania jego ważności. Usługa WUA sprawdza również, czy ustawienie zasad grupy **Zezwalaj na podpisaną zawartość pochodzącą z intranetowej lokalizacji usługi aktualizacji firmy Microsoft** jest włączone na komputerze lokalnym. To ustawienie zasad musi być włączone, aby usługa WUA mogła skanować w poszukiwaniu aktualizacji utworzonych i opublikowanych za pomocą programu Updates Publisher.  

 Gdy aktualizacje oprogramowania są publikowane w programie System Center Updates Publisher, po ich opublikowania na serwerze aktualizacji zostaną one podpisane za pomocą certyfikatu cyfrowego. Można określić certyfikat PKI lub skonfigurować program Updates Publisher w taki sposób, aby generował on certyfikat z podpisem własnym w celu podpisania aktualizacji oprogramowania.  

### <a name="signed-configuration-data-for-compliance-settings"></a>Podpisane dane konfiguracji ustawień zgodności  
 Podczas importowania danych konfiguracji programu Configuration Manager weryfikuje podpis cyfrowy pliku. Jeśli pliki nie zostały podpisane lub sprawdzenie podpisu cyfrowego zakończy się niepowodzeniem, zostanie wyświetlone ostrzeżenie oraz monit, czy importowanie ma być kontynuowane. Importowanie danych konfiguracji należy kontynuować tylko wtedy, jeśli użytkownik jawnie ufa wydawcy i jest pewny co do integralności plików.  

### <a name="encryption-and-hashing-for-client-notification"></a>Szyfrowanie i generowanie skrótów funkcji powiadomienia klienta  
 W przypadku korzystania z funkcji powiadomienia klienta cała komunikacja jest oparta na protokole TLS oraz najwyższym standardzie szyfrowania, który mogą między sobą wynegocjować serwer i systemy operacyjne klienta. Na przykład, komputer kliencki z systemem Windows 7 i punkt zarządzania z systemem Windows Server 2008 R2 obsługują 128-bitowe szyfrowanie AES, podczas gdy komputer kliencki z systemem Vista połączony z tym samym punktem zarządzania wynegocjuje jedynie szyfrowanie 3DES. Taka sama negocjacja następuje w przypadku generowania skrótów pakietów transferowanych w ramach funkcji powiadomienia klienta przy użyciu algorytmu SHA-1 lub SHA-2.  

##  <a name="certificates-used-by-configuration-manager"></a>Certyfikaty używane przez program Configuration Manager  
 Lista certyfikatów infrastruktury kluczy publicznych (PKI), które mogą być używane przez Menedżera konfiguracji, żadnych specjalnych wymagań lub ograniczeń i sposobu używania certyfikatów znajdują się w temacie [wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager](../../core/plan-design/network/pki-certificate-requirements.md). Lista zawiera obsługiwane algorytmy wyznaczania wartości skrótu i długości kluczy. Większość certyfikatów obsługuje algorytm SHA-256 i klucze o długości 2048 bitów.  

> [!NOTE]  
>  Wszystkie certyfikaty używane przez program Configuration Manager musi zawierać tylko znaki jednobajtowe w nazwie podmiotu lub alternatywnej nazwy podmiotu.  

 Certyfikaty PKI są wymagane w następujących przypadkach:  

-   Podczas zarządzania klientami programu Configuration Manager w Internecie.  

-   Podczas zarządzania klientami programu Configuration Manager na urządzeniach przenośnych.  

-   Użytkownik zarządza komputerami Mac.  

-   Użytkownik korzysta z chmurowych punktów dystrybucji.  

-   Użytkownik zarządza komputerami opartymi na technologii Intel AMT poza pasmem.  

 Większość pozostałych komunikacji programu Configuration Manager, która wymaga certyfikatów do uwierzytelniana, podpisywania lub szyfrowania programu Configuration Manager automatycznie używa certyfikatów PKI, jeśli są one dostępne. Jeśli nie są one dostępne, program Configuration Manager generuje certyfikaty z podpisem własnym.  

 Menedżer konfiguracji korzystają z certyfikatów PKI gdy zarządza urządzeniami przenośnymi za pomocą łącznika serwera Exchange.  

### <a name="mobile-device-management-and-pki-certificates"></a>Zarządzanie urządzeniami przenośnymi a certyfikaty PKI  
 Jeśli urządzenie przenośne nie jest zablokowany przez operatora sieci komórkowej, można użyć programu Configuration Manager lub Microsoft Intune do żądania i instalowania certyfikatu klienta. Ten certyfikat umożliwia uwierzytelnianie wzajemne między klientem na urządzeniu przenośnym i systemy lokacji programu Configuration Manager lub usługi Microsoft Intune. Jeśli urządzenie przenośnie jest zablokowanie, nie można użyć programu Configuration Manager lub usługi Intune do wdrażania certyfikatów.  

 Po włączeniu spisu sprzętu dla urządzeń przenośnych programu Configuration Manager lub usługi Intune będą również inwentaryzować certyfikaty zainstalowane na urządzeniu przenośnym.  

### <a name="out-of-band-management-and-pki-certificates"></a>Zarządzanie poza pasmem a certyfikaty PKI  
 Do zarządzania poza pasmem komputerami opartymi na technologii Intel AMT używane są co najmniej dwa typy certyfikatów wystawionych przez infrastrukturę PKI: certyfikaty udostępniania AMT i certyfikaty serwera sieci Web.  

 Punkt obsługi poza pasmem korzysta z certyfikatu udostępniania AMT, aby przygotować komputery do zarządzania poza pasmem. Komputery oparte na technologii AMT, które będą udostępniane, muszą ufać certyfikatowi dostarczonemu przez punkt zarządzania poza pasmem. Komputery oparte na technologii AMT są domyślnie skonfigurowane przez producenta komputera w taki sposób, aby używały zewnętrznych urzędów certyfikacji, jak VeriSign, Go Daddy, Comodo i Starfield. Jeśli nabycia certyfikatu udostępniania od jednego z zewnętrznych urzędów certyfikacji i konfigurowanie programu Configuration Manager do korzystania z tego certyfikatu komputery oparte na technologii AMT będą ufać urzędowi certyfikacji, który wystawił certyfikat udostępniania, a udostępnienie będzie możliwe. Najlepszym rozwiązaniem w zakresie zabezpieczeń będzie jednak użycie własnego, wewnętrznego urzędu certyfikacji w celu wystawienia certyfikatu udostępniającego AMT.  

 Komputery oparte na technologii AMT używają składnika serwera sieci Web, który jest częścią oprogramowania układowego i szyfruje kanał komunikacyjny z punktem obsługi poza pasmem przy użyciu protokołu TLS (Transport Layer Security). System BIOS w komputerach opartych na technologii AMT nie ma interfejsu użytkownika umożliwiającego ręczne skonfigurowanie certyfikatu, jest więc wymagany urząd certyfikacji przedsiębiorstwa Microsoft, który automatycznie zatwierdza żądania certyfikatów od komputerów opartych na technologii AMT. Żądanie używa formatu PKCS#10 jako formatu żądania, który z kolei używa formatu PKCS#7 do transmitowania informacji o certyfikacie na komputer oparty na technologii AMT.  

 Komputer oparty na technologii AMT zostaje uwierzytelniony na komputerze, który nim zarządza, nie istnieje jednak odpowiedni certyfikat PKI klienta na komputerze, który nim zarządza. Tego rodzaju komunikacja używa zamiast tego uwierzytelniania Kerberos lub HTTP Digest. W przypadku uwierzytelniania HTTP Digest szyfrowanie następuje przy użyciu protokołu TLS.  

 Do zarządzania komputerami opartymi na technologii AMT poza pasmem może być wymagany dodatkowy typ certyfikatu: opcjonalny certyfikat klienta dla uwierzytelnianych sieci przewodowych i bezprzewodowych 802.1X. Komputer oparty na technologii AMT może wymagać certyfikatu klienta w celu uwierzytelnienia na serwerze RADIUS. Jeśli serwer RADIUS jest skonfigurowany do uwierzytelniania za pomocą protokołu EAP-TLS, certyfikat klienta jest zawsze wymagany. Jeśli serwer RADIUS jest skonfigurowany do uwierzytelniania za pomocą protokołów EAP-TTLS/MSCHAPv2 lub PEAPv0/EAP-MSCHAPv2, konfiguracja serwera RADIUS określa, czy jest wymagany certyfikat klienta. Komputer oparty na technologii AMT żąda tego certyfikatu przy użyciu tego samego procesu jak w przypadku żądania certyfikatu serwera sieci Web.  

### <a name="operating-system-deployment-and-pki-certificates"></a>Wdrożenie systemu operacyjnego a certyfikaty PKI  
 Jeśli używasz programu Configuration Manager do wdrażania systemów operacyjnych i punkt zarządzania wymaga połączeń klienckich HTTPS, komputer kliencki musi mieć certyfikat do komunikacji z punktem zarządzania również, nawet jeśli komputer jest na etapie przejściowym, takim jak rozruch z nośnika sekwencji zadań lub punktu dystrybucji obsługującego środowisko PXE. Tego scenariusza, należy utworzyć certyfikat uwierzytelniania klienta PKI i wyeksportować go przy użyciu klucza prywatnego, a następnie zaimportować go do właściwości serwera lokacji i również dodać € pointâ zarządzania™ s certyfikatu zaufanego głównego urzędu certyfikacji.  

 Tworząc nośnik rozruchowy, użytkownik importuje certyfikat uwierzytelniania klienta. Na nośniku rozruchowym należy skonfigurować hasło, co pomoże zapewnić ochronę klucza prywatnego i innych danych poufnych skonfigurowanych w sekwencji zadań. Wszystkie komputery uruchamiane z nośnika rozruchowego przedstawiają punktowi zarządzania ten sam certyfikat wymagany dla określonych funkcji klienckich, jak żądanie zasad klienta.  

 Używając rozruchu w środowisku PXE, użytkownik importuje certyfikat uwierzytelniania klienta do punktu dystrybucji z obsługą środowiska PXE, który korzysta z tego samego certyfikatu dla wszystkich klientów uruchamianych z tego punktu. Najlepszym rozwiązaniem w zakresie zabezpieczeń jest wymaganie od użytkowników łączących komputery z usługą środowiska PXE podania hasła, co pomoże zapewnić ochronę klucza prywatnego i innych danych poufnych w sekwencjach zadań.  

 Jeśli jeden z tych certyfikatów uwierzytelniania klienta zostanie naruszony, należy zablokować te certyfikaty w węźle **Certyfikaty** w obszarze roboczym **Administracja** , węzeł **Zabezpieczenia** . Zarządzanie tymi certyfikatami wymaga prawa **Zarządzaj certyfikatem wdrażania systemu operacyjnego** .  

 Po wdrożeniu systemu operacyjnego i programu Configuration Manager jest zainstalowany, klient zażąda własnego certyfikatu uwierzytelniania klienta PKI do komunikacji z klientem protokołu HTTPS.  

### <a name="isv-proxy-solutions-and-pki-certificates"></a>Rozwiązania proxy niezależnego dostawcy oprogramowania a certyfikaty PKI  
 Niezależni dostawcy oprogramowania (ISV) tworzyć aplikacje rozszerzające programu Configuration Manager. Niezależny dostawca oprogramowania możne na przykład stworzyć rozszerzenia obsługujące platformy klienta inne niż Windows, jak komputery Macintosh lub z systemem UNIX. Jednak jeśli systemy lokacji wymagają połączeń klienckich HTTPS, klienci muszą także używać certyfikatów PKI do komunikowania się z lokacją. Menedżer konfiguracji umożliwia przypisać certyfikat do proxy niezależnego dostawcy oprogramowania, co umożliwia komunikację między klientami serwera proxy niezależnego dostawcy oprogramowania a punktem zarządzania. Jeśli używane są rozszerzenia wymagające certyfikatów proxy niezależnego dostawcy oprogramowania, należy zapoznać się z dokumentacją danego produktu. Aby uzyskać więcej informacji o sposobie tworzenia certyfikatów proxy niezależnego dostawcy oprogramowania, zobacz Configuration Manager oprogramowania Developer Kit (SDK).  

 Jeśli certyfikat niezależnego dostawcy oprogramowania zostanie naruszony, należy go zablokować w węźle **Certyfikaty** w obszarze roboczym **Administracja** , węzeł **Zabezpieczenia** .  

### <a name="asset-intelligence-and-certificates"></a>Analiza zasobów a certyfikaty  
 Program Configuration Manager instaluje się za pomocą certyfikatu X.509, używanego przez punkt synchronizacji analizy zasobów połączenia z firmą Microsoft. Configuration Manager używa tego certyfikatu do żądania certyfikatu uwierzytelniania klienta z usługi certyfikatów Microsoft. Certyfikat uwierzytelniania klienta jest zainstalowany na serwerze systemu lokacji punktu synchronizacji analizy zasobów i służy do uwierzytelniania serwera wobec firmy Microsoft. Program Configuration Manager używa certyfikatu uwierzytelniania klienta do pobierania katalogu analizy zasobów i wysyłania tytułów oprogramowania.  

 Długość klucza tego certyfikatu wynosi 1024 bity.  

### <a name="cloud-based-distribution-points-and-certificates"></a>Punkty dystrybucji w chmurze i certyfikatów  
 Począwszy od programu System Center 2012 Configuration Manager SP1 punkty dystrybucji w chmurze wymagają certyfikatu zarządzania (z podpisem własnym lub PKI) przekazywanego do systemu Microsoft Azure. Ten certyfikat zarządzania wymaga funkcji uwierzytelniania serwera, a długość jego klucza musi wynosić 2048 bitów. Konieczne jest ponadto skonfigurowanie dla wszystkich chmurowych punktów dystrybucji certyfikatu usługi, który nie może mieć podpisu własnego oraz ma możliwość uwierzytelniania serwera, a minimalna długość jego klucza wynosi 2048 bitów.  

> [!NOTE]  
>  Certyfikat zarządzania z podpisem własnym służy wyłącznie do celów testowych i nie jest przeznaczony do użytku w sieciach produkcyjnych.  

 Klienci nie wymagają, aby certyfikat PKI klienta korzystał z chmurowych punktów dystrybucji, ponieważ uwierzytelnienie wobec punktu zarządzania następuje przy użyciu certyfikatu z podpisem własnym lub certyfikatu PKI klienta. Następnie punkt zarządzania wystawia token dostępu programu Configuration Manager do klienta, który klient przedstawia do punktu dystrybucji w chmurze. Token jest ważny przez 8 godzin.  

### <a name="the-microsoft-intune-connector-and-certificates"></a>Microsoft Intune Connector i certyfikatów  
 Po zarejestrowaniu urządzeń przenośnych Microsoft Intune można zarządzać tych urządzeń przenośnych w programie Configuration Manager przez utworzenie łącznika programu Microsoft Intune. Łącznik używa certyfikatu PKI z możliwością uwierzytelniania klienta do uwierzytelniania programu Configuration Manager w usłudze Microsoft Intune i przesłać między nimi przy użyciu protokołu SSL wszystkie informacje. Rozmiar klucza certyfikatu wynosi 2048 bitów, a certyfikat używa algorytmu wyznaczania wartości skrótu SHA-1.  

 Po zainstalowaniu łącznika zostanie utworzony certyfikat podpisujący, który jest przechowywany na serwerze lokacji kluczy ładowania bezpośredniego. Ponadto zostanie utworzony certyfikat szyfrowania, który jest przechowywany w punkcie rejestracji certyfikatu w celu zaszyfrowania żądania prostego protokołu rejestrowania certyfikatów (SCEP). Rozmiar klucza tych certyfikatów również wynosi 2048 bitów, a certyfikaty używają algorytmu wyznaczania wartości skrótu SHA-1.  

 Po zarejestrowaniu urządzeń przenośnych w usłudze Intune instaluje certyfikatu PKI na urządzeniu przenośnym. który ma możliwość uwierzytelniania klienta, korzysta z klucza o rozmiarze 2048 bitów i używa algorytmu wyznaczania wartości skrótu SHA-1.  

 Tych certyfikatów PKI automatycznie są wymagane, generowane i instalowane przez program Microsoft Intune.  

### <a name="crl-checking-for-pki-certificates"></a>Sprawdzanie listy CRL dla certyfikatów PKI  
 Lista odwołania certyfikatów PKI (CRL) zwiększa obciążenie administracyjne i obciążenie przetwarzaniem, jest jednak bezpieczniejsza. Jeśli jednak sprawdzanie listy CRL jest włączone, lecz lista CRL jest niedostępne, połączenie z certyfikatem PKI zakończy się niepowodzeniem. Aby uzyskać więcej informacji, zobacz [zabezpieczenia i prywatność programu System Center Configuration Manager](../../core/plan-design/security/security-and-privacy.md).  

 Sprawdzania listy odwołania certyfikatów jest domyślnie włączone w usługach IIS, dlatego jeśli używasz listę CRL z wdrożeniem infrastruktury kluczy publicznych, nie wymaga żadnej dodatkowej konfiguracji na większości systemów lokacji programu Configuration Manager z usługami IIS. Wyjątkiem są aktualizacje oprogramowania, które wymagają ręcznego włączenia sprawdzania listy CRL w celu zweryfikowania podpisów plików aktualizacji oprogramowania.  

 Sprawdzanie listy CRL jest domyślnie włączone dla komputerów klienckich, gdy korzystają z połączeń klienckich HTTPS. Sprawdzanie listy CRL nie jest domyślnie włączone w przypadku korzystania z konsoli zarządzania poza pasmem w celu łączenia się z komputerem opartym na technologii AMT, można jednak włączyć tę opcję. Nie można wyłączyć sprawdzanie listy CRL dla klientów na komputerach Mac w programie Configuration Manager z dodatkiem SP1 lub nowszym.  

 Sprawdzanie listy CRL nie jest obsługiwane dla następujących połączeń w programie Configuration Manager:  

-   Połączenia między serwerami  

-   Urządzenia przenośne, które są zarejestrowane przez program Configuration Manager.  

-   Urządzenia przenośne zarejestrowane przez program Microsoft Intune.  

##  <a name="cryptographic-controls-for-server-communication"></a>Formanty kryptograficzne komunikacji z serwerem  
 Configuration Manager korzysta z poniższych formantów kryptograficznych komunikacji z serwerem.  

### <a name="server-communication-within-a-site"></a>Komunikacja z serwerem w obrębie lokacji  
 Każdy serwer systemu lokacji używa certyfikatu na przesyłanie danych do innych systemów lokacji w tej samej lokacji programu Configuration Manager. Niektóre role systemu lokacji używają także certyfikatów do uwierzytelniania. Na przykład, jeśli punkt proxy rejestracji zostanie zainstalowany na jednym serwerze, a punkt rejestracyjny na innym serwerze, serwery mogą się wzajemnie uwierzytelniać przy użyciu tego certyfikatu tożsamości. W przypadku programu Configuration Manager używa certyfikatu dla tej komunikacji, jeśli jest dostępny, który ma możliwość uwierzytelniania serwera certyfikat PKI, programu Configuration Manager korzysta z niego automatycznie; Jeśli nie, program Configuration Manager generuje certyfikat z podpisem własnym. Ten certyfikat z podpisem własnym ma możliwość uwierzytelniania serwera, używa algorytmu SHA-256 i ma klucz o długości 2048 bitów. Menedżer konfiguracji kopiuje certyfikat do magazynu osób zaufanych na innych serwerach systemu lokacji, wypadek zaistnienia konieczności zaufania systemowi lokacji. Systemy lokacji mogą następnie ufać sobie wzajemnie przy użyciu tych certyfikatów i zaufania elementów równorzędnych.  

 Oprócz tego certyfikatu dla każdego serwera systemu lokacji programu Configuration Manager generuje certyfikat z podpisem własnym dla większości ról systemu lokacji. Jeśli jest wiele wystąpień roli systemu lokacji w tej samej lokacji, współużytkują one ten sam certyfikat. Może być na przykład wiele punktów zarządzania lub punktów rejestracyjnych w tej samej lokacji. Certyfikat z podpisem własnym również używa algorytmu SHA-256 i ma klucz o długości 2048 bitów. Jest on również kopiowany do magazynu osób zaufanych na serwerach systemu lokacji na wypadek zaistnienia konieczności zaufania temu certyfikatowi. Następujące role systemu lokacji generują ten certyfikat:  

-   Punkt usługi sieci Web Wykaz aplikacji  

-   Punkt witryny sieci Web katalogu aplikacji  

-   Punkt synchronizacji analizy zasobów  

-   Punkt rejestracji certyfikatu  

-   Punkt ochrony punktu końcowego  

-   Punkt rejestracji  

-   Rezerwowy punkt stanu  

-   Punkt zarządzania  

-   Punkt dystrybucji z obsługą multiemisji  

-   Punkt obsługi poza pasmem  

-   Punkt usług raportowania  

-   Punkt aktualizacji oprogramowania  

-   Punkt migracji stanu  

-   Punkt modułu sprawdzania kondycji systemu  

-   Łącznik usługi Microsoft Intune  

 Te certyfikaty są zarządzane przez program Configuration Manager automatycznie i w miarę potrzeby generowane automatycznie.  

 Configuration Manager używa również certyfikat uwierzytelniania klienta do wysyłania komunikatów o stanie z punktu dystrybucji do punktu zarządzania. Jeżeli punkt zarządzania jest skonfigurowany wyłącznie do korzystania z połączeń klienckich HTTPS, konieczne jest użycie certyfikatu PKI. Jeśli punkt zarządzania akceptuje połączenia HTTP, można użyć certyfikatu PKI lub wybrać opcję użycia certyfikatu z podpisem własnym i możliwością uwierzytelniania klienta, który używa algorytmu SHA-256 i ma klucz o długości 2048 bitów.  

### <a name="server-communication-between-sites"></a>Komunikacja z serwerem między lokacjami  
 Menedżer konfiguracji przesyła dane między lokacjami przy użyciu replikacji bazy danych i replikacji opartej na plikach. Aby uzyskać więcej informacji, zobacz [komunikacja między punktami końcowymi w programie System Center Configuration Manager](../../core/plan-design/hierarchy/communications-between-endpoints.md).  

 Program Configuration Manager automatycznie konfiguruje replikację bazy danych między lokacjami i używa certyfikatów PKI, które mają możliwość uwierzytelniania serwera, jeśli są one dostępne; Jeśli nie, Configuration Manager tworzy certyfikaty z podpisem własnym do uwierzytelniania serwera. W obu przypadkach uwierzytelnianie między lokacjami zostaje ustanowione przy użyciu certyfikatów w magazynie osób zaufanych korzystającego z zaufania elementów równorzędnych. Ten magazyn certyfikatów służy do zapewnienia, że tylko do komputerów programu SQL Server, które są używane przez hierarchię programu Configuration Manager uczestniczą w replikacji do lokacji. Podczas gdy lokacje główne i centralna lokacja administracyjna mogą replikować zmiany konfiguracji we wszystkich lokacjach w hierarchii, lokacje dodatkowe mogą replikować zmiany konfiguracji wyłącznie w lokacji nadrzędnej.  

 Serwery lokacji nawiązują komunikację między lokacjami przy użyciu wykonywanej automatycznie bezpiecznej wymiany kluczy. Serwer lokacji wysyłającej generuje skrót i podpisuje go kluczem prywatnym. Serwer lokacji odbierającej sprawdza podpis przy użyciu klucza publicznego i porównuje skrót z wartością wygenerowaną lokalnie. Jeśli wartości są zgodne, lokacja odbierająca zaakceptuje zreplikowane dane. Jeśli wartości nie są zgodne, programu Configuration Manager odrzuci dane replikacji.  

 Replikacja bazy danych w programie Configuration Manager korzysta z programu SQL Server Service Broker do transferu danych między lokacjami przy użyciu następujących mechanizmów:  

-   Program SQL Server do połączenia z serwerem SQL: Do podpisywania i szyfrowania danych przy użyciu standardowych AES (Advanced Encryption) używane są poświadczenia systemu Windows do uwierzytelniania serwerów i certyfikaty z podpisem własnym o długości 1024 bitów. Jeśli są dostępne certyfikaty PKI z możliwością uwierzytelniania serwera, zostaną one użyte. Certyfikat musi się znajdować w magazynie osobistym magazynu certyfikatów komputera.  

-   SQL Service Broker: To używa certyfikatów z podpisem własnym o długości 2048 bitów dla uwierzytelniania oraz podpisywania i szyfrowania danych przy użyciu standardowych AES (Advanced Encryption). Certyfikat musi się znajdować w bazie danych master programu SQL Server.  

 Replikacja oparta na plikach używa protokołu bloku komunikatów serwera (SMB) i algorytmu SHA-256 w celu podpisywania niezaszyfrowanych danych, które nie zawierają jednak żadnych poufnych informacji. Jeśli chcesz zaszyfrować te dane, można użyć protokołu IPsec i należy wdrożyć niezależnie od programu Configuration Manager.  

##  <a name="cryptographic-controls-for-clients-that-use-https-communication-to-site-systems"></a>Formanty kryptograficzne klientów korzystających z komunikacji protokołu HTTPS z systemów lokacji  
 Jeśli role systemu lokacji akceptują połączenia klienckie, można je skonfigurować w taki sposób, aby akceptowały połączenia HTTPS i HTTP lub tylko połączenia HTTPS. Role systemu lokacji akceptujące połączenia z Internetu akceptują wyłącznie połączenia klienckie za pośrednictwem protokołu HTTPS.  

 Połączenia klienckie za pośrednictwem protokołu HTTPS umożliwiają uzyskanie większego poziomu zabezpieczeń przez integrację z infrastrukturą kluczy publicznych (PKI), aby pomóc zapewnić ochronę komunikacji klient-serwer. Konfigurowanie połączeń klienckich za pośrednictwem protokołu HTTPS bez dogłębnej wiedzy w zakresie planowania, wdrażania i działania infrastruktury PKI może jednak sprawić, że użytkownik będzie nadal narażony na ataki. Na przykład, jeśli nie zostanie zabezpieczony główny urząd certyfikacji, osoby atakujące mogą naruszyć zaufanie całej infrastruktury PKI. Jeśli certyfikaty PKI nie będą wdrożone i zarządzane przy użyciu kontrolowanych i bezpiecznych procesów, konsekwencją mogą być klienci niezarządzani, którzy nie będą mogli otrzymywać krytycznych aktualizacji lub pakietów oprogramowania.  

> [!IMPORTANT]  
>  Certyfikaty PKI używane do komunikacji z klientem chronią wyłącznie komunikację między klientem i niektórymi systemami lokacji. Nie chronią kanału komunikacji między serwerem lokacji a systemami lokacji lub między serwerami lokacji.  

### <a name="communication-that-is-unencrypted-when-clients-use-https-communication"></a>Komunikacja niezaszyfrowana Jeśli klienci używają komunikacji protokołu HTTPS  
 Gdy klienci komunikują się z systemami lokacji przy użyciu protokołu HTTPS, komunikacja jest zazwyczaj zaszyfrowana za pośrednictwem protokołu SSL. W następujących sytuacjach klienci komunikują się jednak z systemami lokacji bez szyfrowania:  

-   Klient nie mógł nawiązać połączenia HTTPS w sieci intranet i wrócił do korzystania z protokołu HTTP, jeśli systemy lokacji zostały w ten sposób skonfigurowane.  

-   Komunikacja z następującymi rolami systemu lokacji:  

    -   Klient wysyła komunikaty o stanie do rezerwowego punktu stanu.  

    -   Klient wysyła żądania PXE do punktu dystrybucji obsługującego środowisko PXE.  

    -   Klient wysyła dane powiadomień do punktu zarządzania.  

 Punkty usług raportowania są skonfigurowane do używania protokołu HTTP lub HTTPS niezależnie od trybu komunikacji z klientem.  

##  <a name="cryptographic-controls-for-clients-chat-use-http-communication-to-site-systems"></a>Formanty kryptograficzne rozmów klienci używają komunikacji HTTP z systemów lokacji  
 Jeśli klienci używają komunikacji HTTP z rolami systemu lokacji, mogą korzystać z certyfikatów PKI do uwierzytelniania klienta lub certyfikatów z podpisem własnym, które program Configuration Manager generuje. Gdy program Configuration Manager generuje certyfikaty z podpisem własnym, mają one niestandardowy identyfikator obiektu dla podpisywania i szyfrowania, a te certyfikaty służą do unikatowej identyfikacji klienta. W przypadku wszystkich obsługiwanych systemów operacyjnych oprócz Windows Server 2003 te certyfikaty z podpisem własnym korzystają z algorytmu SHA-256 i mają klucz o długości 2048 bitów. W systemie Windows Server 2003 używany jest algorytm SHA1 z kluczem o długości 1024 bitów.  

### <a name="operating-system-deployment-and-self-signed-certificates"></a>Wdrażanie systemu operacyjnego a certyfikaty z podpisem własnym  
 Korzystając z programu Configuration Manager do wdrażania systemów operacyjnych z certyfikatami z podpisem własnym, komputer klienta musi także mieć certyfikat do komunikacji z punktem zarządzania, nawet jeśli komputer jest na etapie przejściowym, takim jak rozruch z nośnika sekwencji zadań lub punktu dystrybucji obsługującego środowisko PXE. Do obsługi tego scenariusza dla połączeń klienckich HTTP, program Configuration Manager generuje certyfikaty z podpisem własnym, które mają niestandardowy identyfikator obiektu dla podpisywania i szyfrowania, a te certyfikaty służą do unikatowej identyfikacji klienta. W przypadku wszystkich obsługiwanych systemów operacyjnych oprócz Windows Server 2003 te certyfikaty z podpisem własnym korzystają z algorytmu SHA-256 i mają klucz o długości 2048 bitów. W systemie Windows Server 2003 używany jest algorytm SHA1 z kluczem o długości 1024 bitów. W przypadku naruszenia zabezpieczeń tych certyfikatów z podpisem własnym, aby uniemożliwić osobom atakującym ich użycie w celu personifikacji zaufanych klientów, należy zablokować certyfikaty w węźle **Certyfikaty** w obszarze roboczym **Administracja** , w węźle **Zabezpieczenia** .  

### <a name="client-and-server-authentication"></a>Uwierzytelnianie klienta i serwera  
 Jeżeli klienci łączą się za pośrednictwem protokołu HTTP, uwierzytelniają punkty zarządzania, za pomocą usług domenowych Active Directory lub przy użyciu programu Configuration Manager zaufanego klucza głównego. Klienci nie uwierzytelniają innych ról systemu lokacji, takich jak punkty migracji stanu lub punkty aktualizacji oprogramowania.  

 Gdy punkt zarządzania po raz pierwszy uwierzytelnia klienta za pomocą certyfikatu klienta z podpisem własnym, ten mechanizm zapewnia minimalne bezpieczeństwo, ponieważ każdy komputer może wygenerować certyfikat z podpisem własnym. W tym scenariuszu proces identyfikacji klienta musi zostać rozszerzony o zatwierdzenie. Musi być zatwierdzony tylko zaufane komputery, automatycznie przez program Configuration Manager, albo ręcznie przez użytkownika administracyjnego. Aby uzyskać więcej informacji, zobacz sekcję zatwierdzenia w [komunikacja między punktami końcowymi w programie System Center Configuration Manager](../../core/plan-design/hierarchy/communications-between-endpoints.md).  

## <a name="about-ssl-vulnerabilities"></a>Temat luk w zabezpieczeniach protokołu SSL
Aby zwiększyć bezpieczeństwo serwerów oraz klientów programu Configuration Manager, wykonaj następujące czynności:

-   Włączenia protokołu TLS 1.2

    Aby włączyć protokół TLS 1.2 dla programu Configuration Manager, zobacz z następującym artykułem KB: [Włączanie protokołu TLS 1.2 dla programu Configuration Manager]( https://support.microsoft.com/en-us/help/4040243/how-to-enable-tls-1-2-for-configuration-manager).
-   Wyłączenie protokołu SSL 3.0 i TLS 1.0, TLS 1.1 
-   Zmiana kolejności mechanizmów szyfrowania związanych z protokołem TLS 

Aby uzyskać więcej informacji, zobacz [jak ograniczyć stosowanie niektórych protokołów w bibliotece Schannel.dll i algorytmów kryptograficznych](https://support.microsoft.com/en-us/kb/245030/) i [Priorytetyzowanie mechanizmy szyfrowania Schannel](https://msdn.microsoft.com/en-us/library/windows/desktop/bb870930.aspx). Te procedury nie wpływa na działanie programu Configuration Manager.

