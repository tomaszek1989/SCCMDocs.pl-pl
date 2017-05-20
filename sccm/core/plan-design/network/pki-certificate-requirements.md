---
title: "Wymagania dotyczące certyfikatu PKI | Dokumentacja firmy Microsoft"
description: "Znajdź wymagania dotyczące certyfikatów PKI, które mogą wymagać programu System Center Configuration Manager."
ms.custom: na
ms.date: 04/24/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: d6a73e68-57d8-4786-842b-36669541d8ff
caps.latest.revision: 17
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: a99b58acef7448af2c9576bfa0ec2635f5a4f86f
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="pki-certificate-requirements-for-system-center-configuration-manager"></a>Wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

W poniższych tabelach wymieniono certyfikaty infrastruktury kluczy publicznych (PKI), które mogą być wymagane dla programu System Center Configuration Manager. Przedstawiając te informacje, oparto się na założeniu, że użytkownik dysponuje podstawową wiedzą na temat certyfikatów PKI. Wskazówki krok po kroku dotyczący wdrażania można znaleźć w temacie [przykład krok po kroku wdrożenia PKI certyfikatów dla programu System Center Configuration Manager: Urząd certyfikacji systemu Windows Server 2008](/sccm/core/plan-design/network/example-deployment-of-pki-certificates). Aby uzyskać więcej informacji o usługach certyfikatów w usłudze Active Directory dokumentacji:  

-   Windows Server 2012: [Omówienie usług certyfikatów w usłudze Active Directory](http://go.microsoft.com/fwlink/p/?LinkId=286744)  

-   Windows Server 2008: [Usługi certyfikatów Active Directory w systemie Windows Server 2008](http://go.microsoft.com/fwlink/p/?LinkId=115018)  

> [!IMPORTANT]  
> System Center Configuration Manager obsługuje certyfikaty Secure 2 algorytmu wyznaczania wartości skrótu (SHA-2). Certyfikaty SHA-2 Przełącz korzyści ważne zabezpieczeń. Dlatego zaleca się następujące czynności:
> - Wydania nowego serwera i klienta certyfikaty uwierzytelniania, które są podpisane za pomocą algorytmu SHA-2, w tym między innymi algorytmu SHA-256 i SHA-512.
> - Wszystkie usługi z Internetem należy używać certyfikatu SHA-2. Na przykład jeśli kupisz publiczny certyfikatu do użycia z usługą bramy zarządzania chmury, upewnij się, zakup certyfikatu SHA-2.  
>
>Skuteczne 14 lutego 2017 systemu Windows nie jest już ufa certyfikatom niektórych podpisany przy użyciu algorytmu SHA-1. Ogólnie rzecz biorąc firma Microsoft zaleca w przypadku wystawiania certyfikatów uwierzytelniania klienta podpisany przy użyciu algorytmu SHA-2 (co obejmuje algorytmu SHA-256 i SHA-512, między innymi) i nowy serwer. Ponadto zalecane jest użycie certyfikatu SHA-2 usług połączony z Internetem. Na przykład jeśli kupisz publiczny certyfikatu do użycia z usługą bramy zarządzania chmury, upewnij się, zakup certyfikatu SHA-2."
>
> W większości przypadków zmiany certyfikatów SHA-2 nie ma wpływu na operacje. Aby uzyskać więcej informacji, zobacz [Windows wymuszania SHA1 certyfikatów](http://social.technet.microsoft.com/wiki/contents/articles/32288.windows-enforcement-of-sha1-certificates.aspx).

 Z wyjątkiem certyfikatów klienta, które System Center Configuration Manager rejestruje na urządzeniach przenośnych i komputerów Mac, certyfikatów automatycznie tworzonych przez Microsoft Intune do zarządzania urządzeniami przenośnymi i System Center Configuration Manager instaluje na komputerach opartych na technologii AMT certyfikatów do tworzenia, wdrażania i zarządzania poniższymi certyfikatami można użyć dowolnej infrastruktury PKI. Jednak gdy używasz usług certyfikatów w usłudze Active Directory i szablonów certyfikatów opisywane rozwiązanie Microsoft PKI może ułatwić zarządzanie certyfikatami. W zorientowaniu się, który szablon certyfikatu najdokładniej odpowiada wymaganiom związanym z certyfikatami, pomoże kolumna **Szablon certyfikatu Microsoft do użycia** w poniższych tabelach. Tylko z urzędu certyfikacji przedsiębiorstwa z systemem w wersji Enterprise Edition lub Datacenter Edition systemu operacyjnego serwera, takich jak Windows Server 2008 Enterprise i Windows Server 2008 Datacenter, można użyć certyfikatów na podstawie szablonu.  

> [!IMPORTANT]  
>  Użycie enterprise urzędu certyfikacji i certyfikat szablonów, nie należy używać szablonów w wersji 3. Te szablony certyfikatów tworzą certyfikaty niezgodne z System Center Configuration Manager. Zamiast tego użyć szablonów w wersji 2 za pomocą następujących instrukcji:  
>   
>  -   W przypadku urzędu certyfikacji w systemie Windows Server 2012: Na **zgodności** kartę we właściwościach szablonu certyfikatu określ **systemu Windows Server 2003** dla **urząd certyfikacji** opcji i **Windows XP / Server 2003** dla **odbiorca certyfikatu** opcji.  
> -   W przypadku urzędu certyfikacji w systemie Windows Server 2008: Podczas duplikowania szablonu certyfikatu pozostaw domyślnie zaznaczoną, **systemu Windows Server 2003 Enterprise**, po wyświetleniu monitu przez **duplikat szablonu** okno dialogowe. Nie wybieraj systemu **Windows Server 2008, Enterprise Edition**.  

 Poniższe sekcje służy do wyświetlania wymagań dotyczących certyfikatów.  

##  <a name="BKMK_PKIcertificates_for_servers"></a> Certyfikaty PKI dla serwerów  

|System Center Configuration Manager składnika|Cel certyfikatu|Szablon certyfikatu Microsoft do użycia|Określone informacje w tym certyfikacie|Jak ten certyfikat jest używany w programie System Center Configuration Manager|  
|-------------------------------------|-------------------------|-------------------------------------------|---------------------------------------------|----------------------------------------------------------|  
|Systemy lokacji z uruchomioną Internet Information Services (IIS), które są skonfigurowane do połączeń klienckich HTTPS:<br /><br /> <ul><li>Punkt zarządzania</li><li>Punkt dystrybucji</li><li>Punkt aktualizacji oprogramowania</li><li>punkt migracji stanu</li><li>Punkt rejestracji</li><li>Punkt proxy rejestracji</li><li>Punkt usługi sieci Web Wykaz aplikacji</li><li>Punkt witryny sieci Web wykazu aplikacji</li><li>Punkt rejestracji ACertificate</li></ul>|Uwierzytelnianie serwera|**Serwer sieci Web**|**Rozszerzone użycie klucza** musi zawierać wartość **Uwierzytelnianie serwera (1.3.6.1.5.5.7.3.1)**.<br /><br /> Jeśli system lokacji akceptuje połączenia z Internetem, nazwa podmiotu lub alternatywna nazwa podmiotu musi zawierać w pełni kwalifikowaną nazwę domeny (FQDN).<br /><br /> Jeśli system lokacji akceptuje połączenia z siecią intranet, nazwa podmiotu lub alternatywna nazwa podmiotu musi zawierać intranetową nazwę FQDN (zalecane) lub nazwę komputera, w zależności od sposobu skonfigurowania systemu lokacji.<br /><br /> Jeśli system lokacji akceptuje połączenia zarówno z Internetu i sieci intranet, zarówno internetowej nazwy FQDN i intranetową nazwę FQDN (lub nazwę komputera) jest wymagane przy użyciu ampersand (&) między obiema nazwami znak ogranicznika — symbol.<br /><br /> **Uwaga:** Kiedy punkt aktualizacji oprogramowania akceptuje połączenia klienckie tylko z Internetu, certyfikat musi zawierać zarówno Internetową, jak i intranetową nazwę FQDN.<br /><br /> Algorytm wyznaczania wartości skrótu SHA-2 jest obsługiwany.<br /><br /> System Center Configuration Manager nie określa, że maksymalna obsługiwana długość klucza dla tego certyfikatu. Zajrzyj do dokumentacji PKI oraz usług IIS, aby wszystkie problemy związane z rozmiaru klucza dla tego certyfikatu.|Ten certyfikat musi znajdować się w magazynie osobistym w magazynie certyfikatów komputera.<br /><br /> Ten certyfikat serwera sieci web jest używany do uwierzytelniania tych serwerów wobec klienta i do szyfrowania wszystkie dane przesyłane między klientem a tymi serwerami przy użyciu protokołu Secure Sockets Layer (SSL).|  
|Chmurowy punkt dystrybucji|Uwierzytelnianie serwera|**Serwer sieci Web**|**Rozszerzone użycie klucza** musi zawierać wartość **Uwierzytelnianie serwera (1.3.6.1.5.5.7.3.1)**.<br /><br /> Nazwa podmiotu musi zawierać nazwy zdefiniowane przez klientów usługi oraz nazwę domeny w formacie FQDN jako nazwę pospolitą konkretnego wystąpienia punktu dystrybucji w chmurze.<br /><br /> Klucz prywatny musi być eksportowalny.<br /><br /> Algorytm wyznaczania wartości skrótu SHA-2 jest obsługiwany.<br /><br /> Obsługiwane długości kluczy: 2048 bitów.|Ten certyfikat jest używany do uwierzytelniania usługi punktu dystrybucji w chmurze klientów programu Configuration Manager i do szyfrowania wszystkich danych przesyłanych między nimi przy użyciu protokołu Secure Sockets Layer (SSL). Ten certyfikat musi być eksportowany w formacie certyfikatu klucza publicznego (PKCS #12), a hasło musi być znane, aby można było zaimportować podczas tworzenia punktu dystrybucji w chmurze.<br /><br /> **Uwaga:** Ten certyfikat jest używany w połączeniu z certyfikatem zarządzania systemu Windows Azure. |  
|Serwery systemu lokacji z programem Microsoft SQL Server|Uwierzytelnianie serwera|**Web server**|**Rozszerzone użycie klucza** musi zawierać wartość **Uwierzytelnianie serwera (1.3.6.1.5.5.7.3.1)**.<br /><br /> Nazwa podmiotu musi zawierać sieci intranet w pełni kwalifikowaną nazwę domeny (FQDN).<br /><br /> Algorytm wyznaczania wartości skrótu SHA-2 jest obsługiwany.<br /><br /> Maksymalna obsługiwana długość klucza to 2048 bitów.|Ten certyfikat musi znajdować się w magazynie osobistym w magazynie certyfikatów komputera. System Center Configuration Manager automatycznie kopiuje go do magazynu osób zaufanych serwerów w hierarchii programu System Center Configuration Manager, które mogą potrzebować ustanowienia zaufania z tym serwerem.<br /><br /> Te certyfikaty służą do uwierzytelniania do serwera.|  
|Klaster programu SQL Server: Serwery systemu lokacji z programem Microsoft SQL Server|Uwierzytelnianie serwera|**Web server**|**Rozszerzone użycie klucza** musi zawierać wartość **Uwierzytelnianie serwera (1.3.6.1.5.5.7.3.1)**.<br /><br /> Nazwa podmiotu musi zawierać w pełni kwalifikowaną nazwę domeny intranetowej (FQDN) klastra.<br /><br /> Klucz prywatny musi być eksportowalny.<br /><br /> Certyfikat musi mieć co najmniej dwa lata, podczas konfigurowania programu System Center Configuration Manager do używania klastra programu SQL Server okres ważności.<br /><br /> Algorytm wyznaczania wartości skrótu SHA-2 jest obsługiwany.<br /><br /> Maksymalna obsługiwana długość klucza to 2048 bitów.|Po zażądaniu i zainstalować ten certyfikat w jednym węźle klastra wyeksportuj certyfikat i zaimportuj go do każdego dodatkowego węzła w klastrze programu SQL Server.<br /><br /> Ten certyfikat musi znajdować się w magazynie osobistym w magazynie certyfikatów komputera. System Center Configuration Manager automatycznie kopiuje go do magazynu osób zaufanych serwerów w hierarchii programu System Center Configuration Manager, które mogą potrzebować ustanowienia zaufania z tym serwerem.<br /><br /> Te certyfikaty służą do uwierzytelniania do serwera.|  
|Monitorowanie systemu lokacji obejmujące następujące role systemu lokacji:<br /><br /><ul><li>Punkt zarządzania</li><li>punkt migracji stanu</li></ul>|Uwierzytelnianie klienta|**Uwierzytelnianie stacji roboczej**|**Rozszerzone użycie klucza** musi zawierać wartość **Uwierzytelnianie klienta (1.3.6.1.5.5.7.3.2)**.<br /><br /> Komputery muszą mieć unikatową wartość w polu Nazwa podmiotu lub Alternatywna nazwa podmiotu.<br /><br /> **Uwaga:** Jeśli używasz wielu wartości w polu alternatywna nazwa podmiotu, używana jest tylko pierwsza wartość.<br /><br /> Algorytm wyznaczania wartości skrótu SHA-2 jest obsługiwany.<br /><br /> Maksymalna obsługiwana długość klucza to 2048 bitów.|Ten certyfikat jest wymagany na wymienionych serwerach systemu lokacji, nawet jeśli nie zainstalowano klienta programu System Center Configuration Manager. Taka konfiguracja zapewnia kondycję tych ról systemu lokacji, monitorowanie i raportować w lokacji.<br /><br /> Certyfikat dla tych systemów lokacji musi znajdować się w magazynie osobistym magazynu certyfikatów komputera.|  
|Serwery z systemem moduł zasad programu System Center Configuration Manager z usługą roli usługi rejestracji urządzeń sieciowych|Uwierzytelnianie klienta|**Uwierzytelnianie stacji roboczej**|**Rozszerzone użycie klucza** musi zawierać wartość **Uwierzytelnianie klienta (1.3.6.1.5.5.7.3.2)**.<br /><br /> Nie ma żadnych określonych wymagań dotyczących podmiotu certyfikatu lub alternatywnej nazwy podmiotu (SAN). Używając tego samego certyfikatu dla wielu serwerów z uruchomioną usługą rejestracji urządzeń sieciowych.<br /><br /> Są obsługiwane algorytmy wyznaczania wartości skrótu SHA-2 i SHA-3.<br /><br /> Obsługiwane długości kluczy: 1024 bity i 2048 bitów.||  
|Systemy lokacji z zainstalowanym punktem dystrybucji|Uwierzytelnianie klienta|**Uwierzytelnianie stacji roboczej**|**Rozszerzone użycie klucza** musi zawierać wartość **Uwierzytelnianie klienta (1.3.6.1.5.5.7.3.2)**.<br /><br /> Nie ma żadnych określonych wymagań dotyczących podmiotu certyfikatu lub alternatywnej nazwy podmiotu (SAN). Możesz użyć tego samego certyfikatu dla wielu punktów dystrybucji. Jest jednak warto użyć innego certyfikatu dla każdego punktu dystrybucji.<br /><br /> Klucz prywatny musi być eksportowalny.<br /><br /> Algorytm wyznaczania wartości skrótu SHA-2 jest obsługiwany.<br /><br /> Maksymalna obsługiwana długość klucza to 2048 bitów.|Ten certyfikat ma dwa cele:<br /><br /><ul><li>Uwierzytelnia punkt dystrybucji wobec punktu zarządzania z włączonym protokołem HTTPS przed wysłaniem przez dany punkt dystrybucji komunikatów o stanie.</li><li>Gdy **Włącz obsługę środowiska PXE dla klientów** wybrania opcji punktu dystrybucji, certyfikat zostanie wysłany do komputerów. Czy sekwencji zadań w procesie wdrażania systemu operacyjnego obejmują działania klientów, takie jak pobieranie zasad klienta lub wysyłanie informacji o zapasach, komputery klienckie mogą połączyć się z punktem zarządzania z włączoną obsługą protokołu HTTPS podczas wdrażania systemu operacyjnego.</li></ul> Ten certyfikat jest używany tylko podczas wdrożenia systemu operacyjnego i nie jest instalowany na kliencie. Związku z tymczasowym użytkiem ten sam certyfikat może służyć każdym wdrożeniem systemu operacyjnego, jeśli użytkownik nie chce używać wielu certyfikatów klienta.<br /><br /> Ten certyfikat musi być eksportowany w formacie certyfikatu klucza publicznego (PKCS #12). Hasło musi być znane, aby można było zaimportować do właściwości punktu dystrybucji.<br /><br /> **Uwaga:** Wymagania dotyczące tego certyfikatu są takie same jak w przypadku certyfikatu klienta dla obrazów rozruchowych wdrażania systemów operacyjnych. Ponieważ wymogi są takie same, można używać tego samego pliku certyfikatu.|  
|Punkt obsługi poza pasmem|Udostępnianie AMT|**Serwer sieci Web** (zmodyfikowany)|**Ulepszone użycie klucza** musi zawierać wartość **uwierzytelnianie serwera (1.3.6.1.5.5.7.3.1)** i następujący identyfikator obiektu: **2.16.840.1.113741.1.2.3**.<br /><br /> Pole nazwy podmiotu musi zawierać nazwę FQDN serwera, który jest hostem punktu Usługi poza pasmem.<br /><br /> **Uwaga:** Certyfikat udostępniania AMT, że żądanie z zewnętrznego urzędu certyfikacji zamiast od własnego wewnętrznego urzędu certyfikacji może nie obsługiwać identyfikatora obiektu udostępniania AMT., 2.16.840.1.113741.1.2.3. Można również określić następujący ciąg tekstowy jako atrybut jednostki organizacyjnej (OU) w nazwie podmiotu certyfikatu: **Intel(R) Client Setup Certificate**. W tej samej wielkości liter, bez końcowej kropki, należy użyć dokładnie ciągu tekstowego w języku angielskim, a dodatkowo nazwa FQDN serwera, który jest hostem punktu Usługi poza pasmem.<br /><br /> Obsługiwane długości kluczy: 1024 i 2048. AMT w wersji 6.0 i nowszych również jest obsługiwana długość klucza wynosząca 4096 bitów.|Ten certyfikat znajduje się w magazynie osobistym w magazynie certyfikatów komputera serwera systemu lokacji punktu Usługi poza pasmem.<br /><br /> Ten certyfikat udostępniania AMT służy do przygotowywania komputerów do zarządzania poza pasmem.<br /><br /> Należy zażądać tego certyfikatu od urzędu certyfikacji, który dostarcza certyfikaty udostępniania AMT. Rozszerzenia systemu BIOS na komputerach opartych na technologii Intel AMT należy skonfigurować do używania odcisk palca certyfikatu głównego (nazywana także jako skrót) dla tego certyfikatu.<br /><br /> Typowym przykładem zewnętrznego urzędu certyfikacji, który wystawia certyfikaty udostępniania AMT jest usługa VeriSign, ale można także użyć własnego, wewnętrznego urzędu certyfikacji.<br /><br /> Zainstaluj certyfikat na serwerze, który jest hostem punktu Usługi poza pasmem, który musi być w stanie z powodzeniem utworzyć łańcuch certyfikatów głównego urzędu certyfikacji. (Domyślnie certyfikat głównego urzędu certyfikacji i certyfikat pośredniego urzędu certyfikacji dla usługi VeriSign są instalowane podczas instalowania systemu Windows).|  
|Serwer systemu lokacji, uruchamiany łącznik Microsoft Intune|Uwierzytelnianie klienta|Nie dotyczy: Usługa Intune automatycznie tworzy ten certyfikat.|**Ulepszone użycie klucza** wartość zawiera **uwierzytelnianie klienta (1.3.6.1.5.5.7.3.2)**.<br /><br /> Niestandardowe rozszerzenia trzy jednoznacznie identyfikują subskrypcji usługi Intune klienta.<br /><br /> Rozmiar klucza to 2048 bitów i używa algorytmu wyznaczania wartości skrótu SHA-1.<br /><br /> **Uwaga:** Nie można zmienić te ustawienia. Ta informacje są udostępniane tylko w celach informacyjnych.|Ten certyfikat jest automatycznie żądany i instalowany w bazie danych programu Configuration Manager po zasubskrybowaniu Microsoft Intune. Po zainstalowaniu łącznika programu Microsoft Intune ten certyfikat jest instalowany na serwerze systemu lokacji, który jest uruchamiany łącznik Microsoft Intune. Jest on instalowany w magazynie certyfikatów komputera.<br /><br /> Ten certyfikat służy do uwierzytelniania hierarchii programu Configuration Manager w usłudze Microsoft Intune przy użyciu łącznika programu Microsoft Intune. Wszystkie dane przesyłane między nimi wykorzystują protokół Secure Sockets Layer (SSL).|  

###  <a name="BKMK_PKIcertificates_for_proxyservers"></a>Serwery proxy sieci web do zarządzania klientami  
 Jeśli dana lokacja obsługuje internetowe zarządzanie i korzystania z serwera proxy sieci web poprzez użycie kończenia żądań SSL (mostkowania) dla połączeń przychodzących z Internetu, serwer proxy sieci web ma wymagania dotyczące certyfikatów wymienione w poniższej tabeli.  

> [!NOTE]  
>  Jeśli używasz serwera proxy sieci web bez kończenia żądań SSL (z tunelowaniem), dodatkowych nie wymaga żadnych certyfikatów na serwerze proxy sieci web.  

|Składnik infrastruktury sieciowej|Cel certyfikatu|Szablon certyfikatu Microsoft do użycia|Określone informacje w tym certyfikacie|Jak ten certyfikat jest używany w programie System Center Configuration Manager|  
|--------------------------------------|-------------------------|-------------------------------------------|---------------------------------------------|----------------------------------------------------------|  
|Serwer proxy sieci Web akceptujący połączenia klienckie przez Internet|Uwierzytelnianie serwera i uwierzytelnianie klienta|1. <br />                        **Serwer sieci Web**<br /><br /> 2. <br />                        **Uwierzytelnianie stacji roboczej**|Internetowej nazwy FQDN w polu Nazwa podmiotu lub alternatywna nazwa podmiotu. Jeśli są używane szablony certyfikatu firmy Microsoft, alternatywna nazwa podmiotu jest dostępne tylko na szablonem stacji roboczej.<br /><br /> Algorytm wyznaczania wartości skrótu SHA-2 jest obsługiwany.|Ten certyfikat jest używany do uwierzytelniania poniższych serwerów wobec klientów internetowych i do szyfrowania wszystkich danych przesyłanych między klientem i serwerem przy użyciu protokołu SSL:<br /><br /><ul><li>Punkt zarządzania internetowego</li><li>Punkt dystrybucji internetowych</li><li>Punkt aktualizacji oprogramowania internetowego</li></ul> Uwierzytelnianie klienta jest używane do zestawiania połączeń między klientami programu System Center Configuration Manager i systemy lokacji internetowej.|  

##  <a name="BKMK_PKIcertificates_for_clients"></a>Certyfikaty PKI dla klientów  

|System Center Configuration Manager składnika|Cel certyfikatu|Szablon certyfikatu Microsoft do użycia|Określone informacje w tym certyfikacie|Jak ten certyfikat jest używany w programie System Center Configuration Manager|  
|-------------------------------------|-------------------------|-------------------------------------------|---------------------------------------------|----------------------------------------------------------|  
|Komputery klienckie z systemem Windows|Uwierzytelnianie klienta|**Uwierzytelnianie stacji roboczej**|**Rozszerzone użycie klucza** musi zawierać wartość **Uwierzytelnianie klienta (1.3.6.1.5.5.7.3.2)**.<br /><br /> Komputery klienckie muszą mieć unikatową wartość w polu Nazwa podmiotu lub alternatywna nazwa podmiotu.<br /><br /> **Uwaga:** Jeśli używasz wielu wartości w polu alternatywna nazwa podmiotu, używana jest tylko pierwsza wartość.<br /><br /> Algorytm wyznaczania wartości skrótu SHA-2 jest obsługiwany.<br /><br /> Maksymalna obsługiwana długość klucza to 2048 bitów.|Domyślnie program System Center Configuration Manager szuka certyfikatów komputera w magazynie osobistym w magazynie certyfikatów komputera.<br /><br /> Z wyjątkiem punktu aktualizacji oprogramowania i punkt witryny sieci Web katalogu aplikacji ten certyfikat uwierzytelnia klientów na serwerach systemu lokacji uruchomionymi usługami IIS i które są skonfigurowane do używania protokołu HTTPS.|  
|Klienci urządzeń przenośnych|Uwierzytelnianie klienta|**Sesja uwierzytelniona**|**Rozszerzone użycie klucza** musi zawierać wartość **Uwierzytelnianie klienta (1.3.6.1.5.5.7.3.2)**.<br /><br /> SHA-1<br /><br /> Maksymalna obsługiwana długość klucza to 2048 bitów.<br /><br /> **Uwagi:**<br /><br /><ul><li>Te certyfikaty muszą mieć format X.509 szyfrowany binarnie algorytmem DER.</li><li>Format X.509 szyfrowany algorytmem Base64 nie jest obsługiwany.</li></ul>|Ten certyfikat uwierzytelnia klientów urządzeń przenośnych na serwerach systemów lokacji, z którymi się komunikują, takich jak punkty zarządzania i punkty dystrybucji.|  
|Obrazy rozruchowe do wdrażania systemów operacyjnych|Uwierzytelnianie klienta|**Uwierzytelnianie stacji roboczej**|**Rozszerzone użycie klucza** musi zawierać wartość **Uwierzytelnianie klienta (1.3.6.1.5.5.7.3.2)**.<br /><br /> Nie istnieją określone wymagania dla pola Nazwa podmiotu lub alternatywnej nazwy podmiotu (SAN) i tego samego certyfikatu można użyć w przypadku wszystkich obrazów rozruchowych.<br /><br /> Klucz prywatny musi być eksportowalny.<br /><br /> Algorytm wyznaczania wartości skrótu SHA-2 jest obsługiwany.<br /><br /> Maksymalna obsługiwana długość klucza to 2048 bitów.|Certyfikat jest używany, gdy sekwencja zadań w procesie wdrażania systemu operacyjnego obejmują działania klientów, takie jak pobieranie zasad klienta lub wysyłanie informacji o spisie.<br /><br /> Ten certyfikat jest używany tylko podczas wdrożenia systemu operacyjnego i nie jest instalowany na kliencie. Związku z tymczasowym użytkiem ten sam certyfikat może służyć każdym wdrożeniem systemu operacyjnego, jeśli użytkownik nie chce używać wielu certyfikatów klienta.<br /><br /> Ten certyfikat musi być eksportowany w formacie certyfikatu klucza publicznego (PKCS #12), a hasło musi być znane, aby można było importować do obrazów rozruchowych programu System Center Configuration Manager.<br /><br /> Ten certyfikat jest tymczasowa dla sekwencji zadań i nie jest używany do instalacji klienta. W przypadku środowiska korzystającego tylko z protokołu HTTPS klient musi mieć ważny certyfikat, aby mógł się komunikować z lokacją i aby wdrożenie mogło być kontynuowane. Klient może automatycznie generować certyfikat, gdy klient jest połączony z usługą Active Directory lub certyfikat klienta można zainstalować przy użyciu innej metody.<br /><br /> **Uwaga:** Wymagania dotyczące tego certyfikatu są takie same jak w przypadku certyfikatu serwera dla systemów lokacji z zainstalowanym punktem dystrybucji. Ponieważ wymogi są takie same, można używać tego samego pliku certyfikatu.|  
|Komputery klienckie Mac|Uwierzytelnianie klienta|Dla programu System Center Configuration Manager rejestracji: **Sesja uwierzytelniona**<br /><br /> Instalacja certyfikatu niezależnego z programu System Center Configuration Manager: **Uwierzytelnianie stacji roboczej**|**Rozszerzone użycie klucza** musi zawierać wartość **Uwierzytelnianie klienta (1.3.6.1.5.5.7.3.2)**.<br /><br /> Programu System Center Configuration Manager, który tworzy certyfikat użytkownika, wartość pola podmiot certyfikatu jest automatycznie wypełniane nazwą użytkownika, który zarejestrował komputer Mac.<br /><br /> Instalacja certyfikatu nie korzysta z programu System Center Configuration Manager rejestracji, ale wdrażającej certyfikat komputera niezależnie od System Center Configuration Manager wartość pola podmiot certyfikatu musi być unikatowa. Na przykład określić nazwę FQDN komputera.<br /><br /> Alternatywna nazwa podmiotu nie jest obsługiwane.<br /><br /> Algorytm wyznaczania wartości skrótu SHA-2 jest obsługiwany.<br /><br /> Maksymalna obsługiwana długość klucza to 2048 bitów.|Ten certyfikat uwierzytelnia komputery klienckie Mac na serwerach systemów lokacji, z którymi się komunikują, takich jak punkty zarządzania i punkty dystrybucji.|  
|Komputery klienckie z systemami Linux i UNIX|Uwierzytelnianie klienta|**Uwierzytelnianie stacji roboczej**|**Rozszerzone użycie klucza** musi zawierać wartość **Uwierzytelnianie klienta (1.3.6.1.5.5.7.3.2)**.<br /><br /> Alternatywna nazwa podmiotu nie jest obsługiwane.<br /><br /> Klucz prywatny musi być eksportowalny.<br /><br /> Algorytm wyznaczania wartości skrótu SHA-2 jest obsługiwany, jeśli system operacyjny klienta obsługuje algorytm SHA-2. Aby uzyskać więcej informacji, zobacz [o Linux i UNIX systemy operacyjne, które nie obsługują algorytmu SHA-256 czy](../../../core/clients/deploy/plan/planning-for-client-deployment-to-linux-and-unix-computers.md#BKMK_NoSHA-256) w sekcji [Planowanie wdrożenia klientów na komputerach z systemem Linux i UNIX w programie System Center Configuration Manager](../../../core/clients/deploy/plan/planning-for-client-deployment-to-linux-and-unix-computers.md).<br /><br /> Obsługiwane długości kluczy: 2048 bitów.<br /><br /> **Uwaga:** Te certyfikaty muszą mieć format X.509 szyfrowany binarnie algorytmem DER. Format X.509 szyfrowany algorytmem Base64 nie jest obsługiwany.|Ten certyfikat uwierzytelnia komputery klienckie Linus lub UNIX na serwerach systemów lokacji, z którymi się komunikują, takich jak punkty zarządzania i punkty dystrybucji. Ten certyfikat musi być eksportowany w formacie certyfikatu klucza publicznego (PKCS #12), a hasło musi być znane, aby można je wprowadzić na kliencie podczas określania certyfikatu PKI.<br /><br /> Aby uzyskać dodatkowe informacje, zobacz [planowanie bezpieczeństwa i certyfikatów dla serwerów Linux i UNIX](../../../core/clients/deploy/plan/planning-for-client-deployment-to-linux-and-unix-computers.md#BKMK_SecurityforLnU) w sekcji [Planowanie wdrożenia klientów na komputerach z systemem Linux i UNIX w programie System Center Configuration Manager](../../../core/clients/deploy/plan/planning-for-client-deployment-to-linux-and-unix-computers.md).|  
|Certyfikatów głównych urzędów certyfikacji (CA) w następujących scenariuszach:<br /><br /><ul><li>Wdrożenie systemu operacyjnego</li><li>Rejestrowanie urządzeń przenośnych</li><li>Uwierzytelnianie serwera RADIUS dla komputerów opartych na technologii AMT firmy Intel</li><li> Uwierzytelnianie certyfikatu klienta</li></ul>|Łańcuch certyfikatów do zaufanego źródła|Nie dotyczy.|Standardowy certyfikat głównego urzędu certyfikacji.|Jeśli klienci muszą tworzyć łańcuchy certyfikatów komunikującego serwera do zaufanego źródła, należy udostępnić główny urząd certyfikacji. Dotyczy to następujących scenariuszy:<br /><br /><ul><li>Podczas wdrażania systemu operacyjnego, a punkt uruchamiania sekwencji zadań, które łączy komputer kliencki do zarządzania jest skonfigurowany do używania protokołu HTTPS.</li><li>Po zarejestrowaniu urządzeń przenośnych mają być zarządzane przez program System Center Configuration Manager.</li><li>Gdy używanie uwierzytelniania 802.1 X dla komputerów opartych na technologii AMT, a chcesz określenie pliku dla certyfikatu głównego serwera RADIUS.</li></ul> Ponadto certyfikat głównego urzędu certyfikacji dla klientów jest wymagany, jeśli certyfikaty klienta są wydawane przez inną hierarchię urzędu certyfikacji niż hierarchia wydająca zarządzania certyfikat punktu.|  
|Komputery z technologią Intel AMT|Uwierzytelnianie serwera.|**Serwer sieci Web** (zmodyfikowany)<br /><br /> Należy skonfigurować pole Nazwa podmiotu dla **Konstruuj z tej informacji usługi Active Directory**, a następnie wybierz **nazwa pospolita** dla **format nazwy podmiotu**.<br /><br /> Należy przyznać **odczytu** i **rejestracja** uprawnienia do uniwersalnej grupy zabezpieczeń określonej we właściwościach składnika zarządzania poza pasmem.|**Rozszerzone użycie klucza** musi zawierać wartość **Uwierzytelnianie serwera (1.3.6.1.5.5.7.3.1)**.<br /><br /> Pole Nazwa podmiotu musi zawierać nazwę FQDN komputera z technologią AMT. Jest ona dostarczana automatycznie z usług Active Directory Domain Services.|Ten certyfikat znajduje się w nieulotnej pamięci kontrolera zarządzania na komputerze i nie będzie widoczny w interfejsie użytkownika systemu Windows.<br /><br /> Każdy komputer z technologią Intel AMT żąda tego certyfikatu podczas udostępniania AMT oraz podczas kolejnych aktualizacji. Po usunięciu udostępniania informacji z tych komputerów AMT ten certyfikat zostanie odwołany.<br /><br /> Gdy ten certyfikat jest zainstalowany na komputerach opartych na technologii Intel AMT, jest również instalowany łańcuch certyfikatów do głównego urzędu certyfikacji. Komputery oparte na technologii AMT nie obsługują certyfikatów urzędu certyfikacji z kluczem o długości większej niż 2048 bitów.<br /><br /> Po zainstalowaniu certyfikatu na komputerach opartych na technologii Intel AMT ten certyfikat uwierzytelnia komputery oparte na technologii AMT, serwer systemu lokacji punktu Usługi poza pasmem i na komputerach z systemem konsoli zarządzania poza pasmem i szyfruje wszystkie dane przesyłane między nimi przy użyciu zabezpieczeń TLS (Transport Layer).|  
|Certyfikat klienta Intel AMT 802.1X|Uwierzytelnianie klienta|**Uwierzytelnianie stacji roboczej**<br /><br /> Należy skonfigurować pole Nazwa podmiotu dla **Konstruuj z tej informacji usługi Active Directory**, wybierz opcję **nazwa pospolita** dla **format nazwy podmiotu**, wyczyścić nazwę DNS, a następnie wybierz główna nazwa użytkownika (UPN) dla alternatywnej nazwy podmiotu.<br /><br /> Należy przyznać uniwersalnej grupy zabezpieczeń określisz we właściwościach składnika zarządzania poza pasmem **odczytu** i **rejestracja** uprawnienia do tego szablonu certyfikatu.|**Rozszerzone użycie klucza** musi zawierać wartość **Uwierzytelnianie klienta (1.3.6.1.5.5.7.3.2)**.<br /><br /> Pole nazwy podmiotu musi zawierać nazwę FQDN komputera opartego na technologii AMT i alternatywnej nazwy podmiotu musi zawierać nazwę UPN.<br /><br /> Maksymalna obsługiwana długość klucza: 2048 bitów.|Ten certyfikat znajduje się w nieulotnej pamięci kontrolera zarządzania na komputerze i nie będzie widoczny w interfejsie użytkownika systemu Windows.<br /><br /> Każdy komputer z technologią Intel AMT można zażądać tego certyfikatu podczas udostępniania AMT, ale komputer nie odwołuje certyfikatu w przypadku jego AMT usunięcia informacji o udostępnianiu.<br /><br /> Po zainstalowaniu certyfikatu na komputerach opartych na technologii AMT ten certyfikat uwierzytelnia komputery oparte na technologii AMT na serwerze RADIUS, aby następnie może być upoważnionych do dostępu do sieci.|  
|Urządzenia przenośne zarejestrowane przez program Microsoft Intune|Uwierzytelnianie klienta|Nie dotyczy: Usługa Intune automatycznie tworzy ten certyfikat.|**Ulepszone użycie klucza** wartość zawiera **uwierzytelnianie klienta (1.3.6.1.5.5.7.3.2)**.<br /><br /> Trzy niestandardowe rozszerzenia unikatowej identyfikacji klienta subskrypcji usługi Intune.<br /><br /> Użytkownicy mogą dostarczać wartość pola podmiot certyfikatu podczas rejestracji. Jednak Intune nie używa tej wartości do identyfikowania urządzenia.<br /><br /> Rozmiar klucza to 2048 bitów i używa algorytmu wyznaczania wartości skrótu SHA-1.<br /><br /> **Uwaga:** Nie można zmienić te ustawienia. Ta informacje są udostępniane tylko w celach informacyjnych.|Ten certyfikat jest automatycznie żądany i instalowany, gdy uwierzytelnieni użytkownicy rejestrują swoje urządzenia przenośne za pomocą programu Microsoft Intune. Wynikowy certyfikat na urządzeniu znajduje się w magazynie komputer i uwierzytelnia zarejestrowane urządzenie przenośne w usłudze Intune, dzięki czemu można następnie zarządzać.<br /><br /> Z powodu niestandardowych rozszerzeń w certyfikacie uwierzytelnianie jest ograniczone do subskrypcji usługi Intune, która została ustanowiona w organizacji.|
