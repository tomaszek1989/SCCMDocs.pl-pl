---
title: "Planowanie zabezpieczeń w programie System Center Configuration Manager | Dokumentacja firmy Microsoft"
description: "Pobierz najlepszych rozwiązań i inne informacje dotyczące zabezpieczeń w programie System Center Configuration Manager."
ms.custom: na
ms.date: 01/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2a216814-ca8c-4d2e-bcef-dc00966a3c9f
caps.latest.revision: 6
caps.handback.revision: 0
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 6145cb69c69dba1eb1b9842079ee1a33686bb18a
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="plan-for-security-in-system-center-configuration-manager"></a>Planowanie zabezpieczeń w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

##  <a name="BKMK_PlanningForCertificates"></a>Planowanie certyfikatów (z podpisem własnym i PKI)  
 Program Configuration Manager korzysta z kombinacji certyfikatów z podpisem własnym i certyfikatów infrastruktury kluczy publicznych (PKI).  

 W ramach najlepszych praktyk w dziedzinie zabezpieczeń doradzamy korzystanie z certyfikatów PKI zawsze, o ile to tylko możliwe. Aby uzyskać więcej informacji o wymaganiach dotyczących certyfikatów PKI, zobacz [wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager](../../../core/plan-design/network/pki-certificate-requirements.md). Gdy program Configuration Manager żąda certyfikatów PKI, takich jak podczas rejestracji urządzeń przenośnych i udostępniania Intel technologii zarządzania aktywnego (AMT), należy użyć usług domenowych w usłudze Active Directory i urzędu certyfikacji przedsiębiorstwa. W przypadku innych certyfikatów PKI należy wdrażać je i zarządzać nimi niezależnie od programu Configuration Manager.  

 Certyfikaty PKI są także wymagane połączenie komputerów klienckich z systemami witryny internetowe i zaleca się używać certyfikatów PKI, gdy klienci łączą się systemów lokacji z usługami Internet Information Services (IIS). Aby uzyskać więcej informacji o komunikacji z klientem, zobacz [jak skonfigurować porty komunikacyjne klienta w programie System Center Configuration Manager](../../../core/clients/deploy/configure-client-communication-ports.md).  

 Gdy używana jest infrastruktura PKI, można korzystać protokołu IPsec do zabezpieczania serwera do komunikacji między systemami lokacji w lokacji, między lokacjami i do innych transferu danych między komputerami. Implementacja protokołu IPsec jest niezależna od programu Configuration Manager.  

 Program Configuration Manager może automatycznie generować certyfikaty z podpisem własnym, gdy certyfikaty PKI są niedostępne, a niektóre certyfikaty w programie Configuration Manager są zawsze z podpisem własnym. W większości przypadków programu Configuration Manager automatycznie zarządza certyfikatami z podpisem własnym i nie wymaga podejmowania żadnych dodatkowych działań. Jeden z dopuszczalnych wyjątków stanowi certyfikat podpisywania serwera lokacji. Certyfikat podpisywania serwera lokacji jest zawsze z podpisem własnym; gwarantuje on, że zasady klienta pobierane przez klientów z punktu zarządzania zostały faktycznie wysłane z serwera lokacji i nie zostały przez nikogo naruszone.  

### <a name="plan-for-the-site-server-signing-certificate-self-signed"></a>Planowanie certyfikatu podpisywania serwera lokacji (z podpisem własnym)  
 Klientów można bezpiecznie uzyskać kopię certyfikatu podpisywania serwera lokacji z usług domenowych w usłudze Active Directory i z instalacji wypychanej klienta. Jeśli klienci nie można uzyskać kopię certyfikatu podpisywania serwera lokacji za pomocą jednej z tych mechanizmów, ze względów bezpieczeństwa zainstalować kopię certyfikatu podpisywania serwera lokacji podczas instalowania klienta. Jest to szczególnie ważne, jeśli pierwszy komunikację klienta z lokacji z Internetu, ponieważ punkt zarządzania jest połączony z siecią niezaufaną i w związku z tym narażony na ataki. W przypadku niepodjęcia tego dodatkowego kroku klienci automatycznie pobierają kopię certyfikatu podpisywania serwera lokacji z punktu zarządzania.  

 Następujące scenariusze w przypadku klientów nie można bezpiecznie uzyskać kopię certyfikatu serwera lokacji:  

-   Klient nie jest instalowany metodą wypychania klienta i jest spełniony dowolny z następujących warunków:  

    -   Schemat usługi Active Directory nie został rozszerzony dla programu Configuration Manager.  

    -   Lokacja klienta nie jest publikowana w usługach domenowych w usłudze Active Directory.  

    -   Klient pochodzi z niezaufanego lasu lub grupy roboczej.  

-   Klient jest instalowany w trakcie połączenia z Internetem.  

##### <a name="to-install-clients-with-a-copy-of-the-site-server-signing-certificate"></a>Aby zainstalować klientów wraz z kopią certyfikatu podpisywania serwera lokacji  

1.  Znajdź certyfikat podpisywania serwera lokacji na serwerze lokacji głównej klienta. Certyfikat jest przechowywany w **SMS** magazyn certyfikatów i ma przypisaną nazwę podmiotu **serwera lokacji** i przyjaznej nazwy, **certyfikat podpisywania serwera lokacji**.  

2.  Wyeksportuj certyfikat bez klucza prywatnego, Zapisz plik w bezpiecznym miejscu i uzyskać do niego dostęp tylko z kanału zabezpieczonego, na przykład za pomocą podpisywania bloku komunikatów serwera (SMB) lub protokołu IPsec.  

3.  Zainstaluj klienta za pomocą właściwości Client.msi **SMSSIGNCERT =***&lt;pełną ścieżkę i nazwę pliku\>*, z programem CCMSetup.exe.  

###  <a name="BKMK_PlanningForCRLs"></a>Planowanie odwołania certyfikatu PKI  
Korzystając z certyfikatów PKI z programu Configuration Manager, należy zaplanować w jak i tego, czy klienci i serwery będą korzystać z listy odwołania certyfikatów (CRL) do weryfikowania certyfikatu na łączącym się z nimi komputerze. Lista CRL jest plik, który tworzy urząd certyfikacji (CA) i znaki i ma listę certyfikatów urzędu certyfikacji został wystawiony, ale odwołanych. Administrator urzędu certyfikacji można odwołać certyfikaty, na przykład, jeśli wystawionym certyfikacie wiadomo lub podejrzewa, że został naruszony.  

> [!IMPORTANT]  
>  Ponieważ lokalizacja listy CRL jest dodawana do certyfikatu w przypadku problemów dotyczących urzędu certyfikacji go, upewnij się, czy planujesz listy odwołania certyfikatów przed wdrożeniem wszystkie certyfikaty PKI, które będą korzystały z programu Configuration Manager.  

Domyślnie usługi IIS zawsze sprawdzają listę CRL pod kątem certyfikatów klienta i nie można zmienić tej konfiguracji w programie Configuration Manager. Domyślnie klienci programu Configuration Manager zawsze sprawdzania listy CRL dla systemów lokacji. To ustawienie zostanie wyłączone, określając właściwość lokacji i właściwość programu CCMSetup. Podczas zarządzania komputerami opartymi na technologii Intel AMT poza pasmem, można także włączyć sprawdzanie listy CRL dla punktu Usługi poza pasmem i komputerów korzystających z konsoli zarządzania poza pasmem.  

Komputery, które korzystają ze sprawdzania odwołań certyfikatów, ale nie można zlokalizować listy CRL zachowują się tak, jakby wszystkie certyfikaty w łańcuchu certyfikacji były odwołane, ponieważ nie można zweryfikować ich braku na liście. W tej sytuacji wszystkie połączenia wymagające certyfikatów i korzystające z listy CRL kończą się niepowodzeniem.  

Sprawdzanie listy CRL przy każdorazowym użyciu certyfikatu zapewnia lepszą ochronę przed potencjalnym użyciem odwołanego certyfikatu, jednak wprowadza opóźnienie komunikacji i konieczność dodatkowego przetwarzania danych na kliencie. To dodatkowe wymaganie sprawdzania zabezpieczeń wydaje się bardziej pożądane, kiedy klienci znajdują się w Internecie lub w sieci niezaufanej.  

Przejrzyj administratorów PKI, przed podjęciem decyzji, czy należy sprawdzania listy CRL klientów programu Configuration Manager, a następnie Pomyśl o pozostawieniu tej opcji włączonej w programie Configuration Manager, gdy są spełnione oba poniższe warunki:  

-   Infrastruktura PKI obsługuje listę CRL, i jest publikowany, gdzie wszystkich klientów programu Configuration Manager mogą ją odnaleźć. Pamiętaj, że mogą być wśród nich także klienci z Internetu, jeśli korzystasz z internetowego zarządzania klientami, oraz klienci z lasów niezaufanych.  

-   Wymaganie sprawdzania listy CRL dla każdego połączenia systemu lokacji, który jest skonfigurowany do używania certyfikatu PKI jest większa niż wymaganie szybszych połączeń i wydajnego przetwarzania na kliencie i ryzyko nienawiązywania połączeń z serwerami, jeśli nie mogą zlokalizować listy CRL przez klientów.  

###  <a name="BKMK_PlanningForRootCAs"></a>Planowanie PKI zaufany główny certyfikatów i listy wystawców certyfikatów  
Jeśli w danych systemach lokacji z usługami IIS wykorzystuje się certyfikaty PKI klienta do uwierzytelniania klientów w połączeniach HTTP lub uwierzytelniania klientów i szyfrowania w połączeniach HTTPS, może zajść potrzeba zaimportowania certyfikatów głównego urzędu certyfikacji jako właściwości lokacji. Oto dwa scenariusze:  

-   Wdrażanie systemów operacyjnych za pomocą programu Configuration Manager i punkty zarządzania akceptują tylko połączenia klienckie HTTPS.  

-   Używane są certyfikaty PKI klienta, które nie łączą się w łańcuch zaufania z certyfikatem głównego urzędu certyfikacji zaufanym z perspektywy punktów zarządzania.  

    > [!NOTE]  
    >  W przypadku wystawiania certyfikatów PKI klienta z tej samej hierarchii urzędu certyfikacji, która wystawia certyfikaty serwera wykorzystywane przez punkty zarządzania, nie ma potrzeby określania tego certyfikatu głównego urzędu certyfikacji. Jednak jeśli używasz wielu hierarchii urzędów certyfikacji i nie masz pewności, czy ufają one sobie wzajemnie, należy zaimportować główny urząd certyfikacji do hierarchii urzędu certyfikacji klientów.  

Jeśli zachodzi konieczność importu certyfikatów głównego urzędu certyfikacji dla programu Configuration Manager, należy je wyeksportować z wystawiającego urzędu certyfikacji lub z komputera klienckiego. W przypadku eksportowania certyfikatu z wystawiającego go urzędu certyfikacji, który jest przy tym głównym urzędem certyfikacji, należy zwrócić uwagę, żeby nie został wyeksportowany klucz prywatny. Zapisz plik wyeksportowanego certyfikatu w bezpiecznej lokalizacji, aby zapobiec modyfikowaniu. Musi być możliwe uzyskanie dostępu do pliku, podczas konfigurowania witryny. Jeśli dostęp do pliku za pośrednictwem sieci, upewnij się, ochronę komunikacji przed naruszeniami poprzez zastosowanie podpisywania protokołu SMB lub protokołu IPsec.  

Jeśli wszystkie certyfikat głównego urzędu certyfikacji, który można zaimportować zostanie przedłużona, należy zaimportować odnowionego certyfikatu.  

Te certyfikaty importowane głównego urzędu certyfikacji i certyfikat głównego urzędu certyfikacji każdego punktu zarządzania utworzyć listy wystawców certyfikatów komputerów używających programu Configuration Manager w następujący sposób:  

-   Gdy klienci łączą się z punktami zarządzania, punkt zarządzania weryfikuje, że certyfikat klienta tworzy łańcuch zaufany główny urząd certyfikacji certyfikatem z listy wystawców certyfikatów danej lokacji. Jeśli tak nie jest, certyfikat zostaje odrzucony, a połączenie PKI nie zostaje nawiązane.  

-   Kiedy klienci wybierają certyfikat PKI i listy wystawców certyfikatów, wybierają certyfikat który tworzy łańcuch z zaufanym certyfikatem głównym z listy wystawców certyfikatów. Jeśli nie ma dopasowania, klient nie wybiera certyfikatu PKI. Aby uzyskać więcej informacji o procesie certyfikatu klienta, zobacz [planowanie wyboru certyfikatu klienta PKI](#BKMK_PlanningForClientCertificateSelection) sekcję w tym artykule.  

Niezależne od konfiguracji lokacji, może zajść do zaimportowania certyfikatu głównego urzędu certyfikacji podczas rejestrowania urządzeń przenośnych, rejestrować komputery Mac i konfigurowania komputerów opartych na technologii Intel AMT dla sieci bezprzewodowych.  

###  <a name="BKMK_PlanningForClientCertificateSelection"></a>Planowanie wyboru certyfikatu klienta PKI  
 Jeśli systemy lokacji usług IIS uzyskują certyfikaty PKI klienta do uwierzytelniania klientów za pośrednictwem protokołu HTTP lub uwierzytelniania klientów i szyfrowania za pośrednictwem protokołu HTTPS, Zaplanuj jak klientów z systemem Windows będą wybierali certyfikat do użycia dla programu Configuration Manager.  

> [!NOTE]  
>  Niektóre urządzenia obsługują metodę wyboru certyfikatu. Zamiast tego automatycznie wybierają pierwszy certyfikat spełniający wymagania certyfikatu. Na przykład klienci na komputerach Mac i urządzenia przenośne nie obsługują metodę wyboru certyfikatu.  

W wielu przypadkach domyślna konfiguracja i domyślne zachowanie okażą się wystarczające. Klient programu Configuration Manager na komputerach z systemem Windows filtruje większą liczbę certyfikatów przy użyciu tych kryteriów w następującej kolejności:  

1.  Lista wystawców certyfikatów: Certyfikat tworzy łańcuch z głównym urzędem certyfikacji, który jest traktowany jako zaufany przez punkt zarządzania.  

2.  Certyfikat znajduje się w domyślnym magazynie certyfikatów o nazwie **Osobisty**.  

3.  Certyfikat jest ważny, nieodwołany i niewygasły. Sprawdzanie poprawności weryfikuje, że klucz prywatny jest dostępny i że certyfikatu nie utworzono z szablonu certyfikatu w wersji 3, które nie są zgodne z programem Configuration Manager.  

4.  Certyfikat ma zdolność uwierzytelniania klienta lub jest wystawiony dla komputera o określonej nazwie.  

5.  Certyfikat ma najdłuższy okres ważności.  

Klientów można skonfigurować do korzystania z listy wystawców certyfikatów następującymi metodami:  

-   Jest publikowana jako informacje o lokacji programu Configuration Manager do usług domenowych w usłudze Active Directory.  

-   Klienci są instalowani przy użyciu instalacji wypychanej klienta.  

-   Po pomyślnym przypisaniu do swojej lokacji klienci pobierają listę z punktu zarządzania.  

-   Jest określana podczas instalacji klienta jako właściwość client.msi z CCMCERTISSUERS.  

Klienci, którzy nie ma listy wystawców certyfikatów podczas pierwszej instalacji, a nie zostały jeszcze przypisane do lokacji pomijania tego sprawdzania. Gdy klienci dysponują listą wystawców certyfikatów i nie mają certyfikatu PKI, tworzy łańcuch z zaufanym certyfikatem głównym z listy wystawców certyfikatów, wybór certyfikatu kończy się niepowodzeniem, a klienci nie kontynuują na podstawie innych kryteriów wyboru certyfikatu.  

W większości przypadków klienta programu Configuration Manager prawidłowo identyfikuje unikatowy i właściwy certyfikat PKI. Jednak gdy jest to inaczej, to zamiast wybierać certyfikat na podstawie zdolności uwierzytelniania klienta, możesz można skonfigurować dwie alternatywne metody wyboru:  

-   Częściowe dopasowanie ciągu do nazwy podmiotu certyfikatu klienta. To dopasowanie, które nie uwzględnia wielkości liter, jest odpowiednie w przypadku użycia w polu podmiotu nazwy komputera wyrażonej jako w pełni kwalifikowana nazwa domeny (nazwa FQDN), gdy chcesz wybrać certyfikat na podstawie sufiksu domeny, na przykład **contoso.com**. Można jednak wykorzystać tę metodę wyboru do identyfikacji w nazwie podmiotu certyfikatu dowolnego ciągu znaków wyróżniającego dany certyfikat spośród innych składowanych w magazynie certyfikatów klienta.  

    > [!NOTE]  
    >  W ramach ustawienia lokacji nie można określić częściowego dopasowania ciągu w alternatywnej nazwie podmiotu (SAN). Częściowe dopasowanie ciągu można określić dla nazwy SAN przy użyciu programu CCMSetup, lecz zostanie on zastąpiony przez właściwości lokacji w następujących scenariuszach:  
    >   
    >  -   Klienci pobierają informacje o lokacji publikowane w usługach domenowych Active Directory.  
    > -   Klienci zostali zainstalowani przy użyciu instalacji wypychanej klienta.  
    >   
    >  Użyj częściowe dopasowanie ciągu w sieci SAN, tylko w przypadku ręcznego instalowania klientów i nie pobierają informacji o lokacji z usług domenowych w usłudze Active Directory. Te warunki dotyczą na przykład tylko klientów internetowych.  

-   Dopasowanie w wartościach atrybutów nazwy podmiotu lub alternatywnej nazwy podmiotu (SAN) certyfikatu klienta. To jest rozróżniana wielkość liter dopasowanie, odpowiedni w przypadku używania X500 nazwy wyróżniającej lub równoważne identyfikatorów obiektów (OID) zgodnych ze standardem RFC 3280 gdy chce się wybrać certyfikat na podstawie wartości atrybutu. Istnieje możliwość określenia tylko atrybutów i ich wartości wymaganych do jednoznacznej identyfikacji lub weryfikacji certyfikatu i odróżnienia go od innych certyfikatów w magazynie.  

W poniższej tabeli przedstawiono wartości atrybutów, które obsługuje kryteria wyboru certyfikatu klienta programu Configuration Manager.  

|Atrybut identyfikatora OID|Atrybut nazwy wyróżniającej|Definicja atrybutu|  
|-------------------|----------------------------------|--------------------------|  
|0.9.2342.19200300.100.1.25|DC|Składnik domeny|  
|1.2.840.113549.1.9.1|E lub E-mail|Adres e-mail|  
|2.5.4.3|CN|Nazwa pospolita|  
|2.5.4.4|SN|Nazwa podmiotu|  
|2.5.4.5|SERIALNUMBER|Numer seryjny|  
|2.5.4.6|C|Kod kraju|  
|2.5.4.7|L|Miejscowość|  
|2.5.4.8|S lub ST|Nazwa województwa|  
|2.5.4.9|STREET|Ulica|  
|2.5.4.10|O|Nazwa organizacji|  
|2.5.4.11|OU|Jednostka organizacyjna|  
|2.5.4.12|T lub Title|Tytuł|  
|2.5.4.42|G lub GN lub GivenName|Imię|  
|2.5.4.43|I lub Initials|Inicjały|  
|2.5.29.17|(brak wartości)|Alternatywna nazwa podmiotu|  

Jeżeli po zastosowaniu kryteriów wyboru znajduje się więcej niż jeden odpowiedni certyfikatów, można zastąpić domyślną konfigurację, aby wybrać certyfikat o najdłuższym okresie ważności i określić czy Brak wybranego certyfikatu. W tym scenariuszu klient nie będzie mógł komunikować się z systemami lokacji usług IIS przy użyciu certyfikatu PKI. Klient wysyła komunikat o błędzie do przypisanego mu rezerwowego punktu stanu informować o nieprawidłowym wyborze certyfikatu, dzięki czemu można zmieniać lub uściślić kryteria wyboru certyfikatu. W takim przypadku zachowanie klienta zależy od tego, czy nie powiodło się połączenie za pośrednictwem protokołu HTTPS czy HTTP:  

-   Jeżeli nie powiodło się połączenie za pośrednictwem protokołu HTTPS: Klient próbuje połączyć się za pośrednictwem protokołu HTTP i używa certyfikatu klienta z podpisem własnym.  

-   Jeśli nie powiodło się połączenie za pośrednictwem protokołu HTTP: Klient podejmie próbę połączenia za pośrednictwem protokołu HTTP przy użyciu certyfikatu klienta z podpisem własnym.  

Aby ułatwić identyfikację unikatowego certyfikatu klienta PKI, można również określić magazyn niestandardowy, inny niż domyślny z **osobiste** w **komputera** przechowywania. Jednak należy utworzyć ten magazyn niezależnie od programu Configuration Manager i musi mieć możliwość wdrażanie certyfikatów do tego magazynu niestandardowego i odnawianie ich przed upływem okresu ważności.  

Informacje o sposobie konfigurowania ustawień certyfikatów klienta, zobacz [Konfigurowanie ustawień certyfikatów PKI klienta](../../../core/plan-design/security/configure-security.md#BKMK_ConfigureClientPKI) w sekcji [skonfigurować zabezpieczenia w programie System Center Configuration Manager](../../../core/plan-design/security/configure-security.md) artykułu.  

###  <a name="BKMK_PlanningForPKITransition"></a>Planowanie strategii przejścia dla certyfikatów PKI i internetowego zarządzania  
Opcje konfiguracji elastyczne w programie Configuration Manager umożliwiają stopniowe przejście klientów oraz lokacji do używania certyfikatów PKI, aby ułatwić zabezpieczenie punktów końcowych klienta. Certyfikaty PKI zapewniają większy poziom zabezpieczeń i umożliwiają zarządzanie klientów internetowych.  

Ze względu na liczbę opcji konfiguracji i dostępnych wyborów w programie Configuration Manager nie istnieje jeden sposób na przejście lokacji, tak aby wszyscy klienci używali połączeń HTTPS. W razie potrzeby postępuj zgodnie z następującymi wskazówkami:  

1.  Zainstaluj lokacji programu Configuration Manager i skonfigurować go tak, aby systemy lokacji akceptują połączenia klienta za pośrednictwem protokołu HTTPS i HTTP.  

2.  Skonfiguruj **komunikacja komputerów klienckich** karcie we właściwościach lokacji tak, że **ustawienia systemu lokacji** jest **protokołu HTTP lub HTTPS**i wybierz **klienta użyj infrastruktury klucza publicznego certyfikatu (możliwość uwierzytelniania klienta), jeśli jest dostępny**.  Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień certyfikatów PKI klienta](../../../core/plan-design/security/configure-security.md#BKMK_ConfigureClientPKI) w sekcji [skonfigurować zabezpieczenia w programie System Center Configuration Manager](../../../core/plan-design/security/configure-security.md) artykułu.  

3.  Przeprowadź wdrożenie certyfikatów PKI klienta. Przykład wdrożenia, zobacz *wdrażanie certyfikatów dla systemu Windows komputery klienckie* w sekcji [przykład krok po kroku wdrożenia PKI certyfikatów dla programu System Center Configuration Manager: Urząd certyfikacji systemu Windows Server 2008](/sccm/core/plan-design/network/example-deployment-of-pki-certificates) artykułu.  

4.  Zainstaluj klientów przy użyciu metody instalacji wypychanej klienta. Aby uzyskać więcej informacji, zobacz [jak instalować klientów programu Configuration Manager za pomocą wypychania klienta](../../../core/clients/deploy/deploy-clients-to-windows-computers.md#BKMK_ClientPush) w sekcji [wdrażanie klientów na komputerach z systemem Windows w programie System Center Configuration Manager](../../../core/clients/deploy/deploy-clients-to-windows-computers.md) artykułu.  

5.  Monitoruj wdrożenie klienta i stan za pomocą raportów i informacji w konsoli programu Configuration Manager.  

6.  Sprawdź liczbę klientów używających certyfikatu PKI klienta, wyświetlając w obszarze roboczym **Zasoby i zgodność** w węźle **Urządzenia** kolumnę **Certyfikat klienta** .  

     Można również wdrożyć narzędzie oceny gotowości protokołu HTTPS Menedżera konfiguracji (**cmHttpsReadiness.exe**) na komputerach i za pomocą raportów liczbę komputerów można używać klienta PKI certyfikacji z programu Configuration Manager.  

    > [!NOTE]  
    >  Po zainstalowaniu klienta programu Configuration Manager **cmHttpsReadiness.exe** narzędzie jest instalowane w *% windir %***\CCM** folder. Po uruchomieniu tego narzędzia w klientach można określić następujące opcje:  
    >   
    >  -   / Magazyn:&lt;nazwy\>  
    > -   / Wystawców:&lt;listy\>  
    > -   / Kryteria:&lt;kryteriów\>  
    > -   /SelectFirstCert  
    >   
    >  Te opcje umożliwiają mapowanie odpowiednio do właściwości Client.msi: **CCMCERTSTORE**, **CCMCERTISSUERS**, **CCMCERTSEL**i **CCMFIRSTCERT** . Aby uzyskać więcej informacji o tych opcjach, zobacz [o właściwościach instalacji klienta w programie System Center Configuration Manager](../../../core/clients/deploy/about-client-installation-properties.md).  

7.  Po upewnieniu się, że wystarczającej liczby klientów pomyślnie używa certyfikatu PKI klienta do uwierzytelniania za pośrednictwem protokołu HTTP, wykonaj następujące kroki:  

    1.  Wdróż certyfikat serwera sieci Web PKI do serwera członkowskiego, który będzie obsługiwał dodatkowy punkt zarządzania dla lokacji, a następnie skonfiguruj ten certyfikat w usługach IIS. Aby uzyskać więcej informacji, zobacz *wdrażanie certyfikatu serwera sieci Web dla systemów lokacji z uruchomionymi usługami IIS* w sekcji [przykład krok po kroku wdrożenia PKI certyfikatów dla programu System Center Configuration Manager: Urząd certyfikacji systemu Windows Server 2008](/sccm/core/plan-design/network/example-deployment-of-pki-certificates) artykułu.  

    2.  Zainstaluj na tym serwerze rolę punktu zarządzania i skonfiguruj opcję **Połączenia klientów** we właściwościach punktu zarządzania w ramach protokołu **HTTPS**.  

8.  Przeprowadź monitorowanie i sprawdź, czy klienci z certyfikatem PKI używają nowego punktu zarządzania za pośrednictwem protokołu HTTPS. W tym celu można użyć liczników wydajności lub rejestrowania usług IIS.  

9. Zmień konfigurację innych ról systemu lokacji, aby używały połączeń klientów za pośrednictwem protokołu HTTPS. Aby zarządzać klientami przez Internet, upewnij się, że systemy lokacji mają przypisane w pełni kwalifikowane nazwy domen internetowych i skonfiguruj indywidualne punkty zarządzania oraz punktu dystrybucji, aby akceptowały połączenia z Internetu.  

    > [!IMPORTANT]  
    >  Przed skonfigurowaniem ról systemu lokacji na akceptowanie połączeń z Internetu, przejrzyj informacje o planowaniu i wymagania wstępne dotyczące zarządzania klientami. Aby uzyskać więcej informacji, zobacz [komunikację między punktami końcowymi w programie System Center Configuration Manager](../../../core/plan-design/hierarchy/communications-between-endpoints.md).  

10. Rozszerz wdrożenie certyfikatu PKI dla klientów i dla systemów lokacji z usługami IIS i konfigurowanie ról systemu lokacji dla połączeń klienckich HTTPS i połączeń internetowych, zgodnie z potrzebami.  

11. Największa zabezpieczeń: Po upewnieniu się, że wszyscy klienci używają certyfikatu PKI klienta do uwierzytelniania i szyfrowania, zmień właściwości lokacji, aby używać tylko protokołu HTTPS.  

 Wykonanie tego planu w celu stopniowego wprowadzenia certyfikatów PKI, najpierw do uwierzytelniania tylko za pośrednictwem protokołu HTTP, a następnie do uwierzytelniania i szyfrowania za pośrednictwem protokołu HTTPS, ogranicza ryzyko, że przerwania zarządzania klientami. Ponadto umożliwi to zastosowanie optymalnych zabezpieczeń obsługującego programu Configuration Manager.  

##  <a name="BKMK_PlanningForRTK"></a>Planowanie zaufanego klucza głównego  
Menedżer konfiguracji zaufanego klucza głównego udostępnia mechanizm klientów programu Configuration Manager sprawdzić, czy systemy lokacji należą do ich hierarchii. Każdy serwer lokacji generuje klucz wymiany lokacji do komunikowania się z innymi lokacjami. Klucz wymiany lokacji z lokacji najwyższego poziomu w hierarchii jest nazywany zaufanym kluczem głównym.  

Funkcja zaufany klucz główny w programie Configuration Manager przypomina certyfikatu głównego w infrastrukturze kluczy publicznych, tzn. wszystkie elementy podpisane przez klucz prywatny zaufanego klucza głównego są objęte zaufaniem na wszystkich poziomach hierarchii. Na przykład dzięki podpisaniu certyfikatu punktu zarządzania za pomocą klucza prywatnego pary zaufanych kluczy głównych i udostępnieniu kopii klucz publiczny z pary kluczy klientom, klienci mogą oni odróżnić punkty zarządzania, które znajdują się w ich hierarchii i punkty zarządzania, które nie są w ich hierarchii. Klienci używają Instrumentacji zarządzania Windows (WMI) przechowują kopię zaufanego klucza głównego w **root\ccm\locationservices** przestrzeni nazw.  

Klienci mogą automatycznie pobierać publiczną kopię zaufanego klucza głównego przy użyciu dwóch następujących mechanizmów:  

-   Schemat usługi Active Directory został rozszerzony dla programu Configuration Manager, lokacja jest opublikowana w usługach domenowych w usłudze Active Directory i klienci mogą pobierać informacje o tej lokacji z serwerem wykazu globalnego.  

-   Klienci są instalowani przy użyciu instalacji wypychanej klienta.  

Jeżeli klienci nie mogą pobrać zaufanego klucza głównego przy użyciu jednego z tych mechanizmów, ufają kluczowi dostarczonemu przez pierwszy punkt zarządzania, z którym nawiążą połączenie. W tym scenariuszu klient może zostać nieprawidłowo skierowany do punktu zarządzania osoby atakującej, którego może pobrać zasady z nieautoryzowanego punktu zarządzania. To może być działanie doświadczonej osoby atakującej i może zdarzyć się tylko w ograniczonym czasie zanim klient pobierze zaufany klucz główny z prawidłowego punktu zarządzania. Jednak w celu ograniczenia tego ryzyka nieprawidłowego skierowania klientów do nieautoryzowanego punktu zarządzania, można wstępnie udostępnić klientom zaufany klucz główny.  

Aby wstępnie udostępnić i sprawdzić zaufany klucz główny dla klienta programu Configuration Manager, użyj następujących procedur:  

-   Wstępnie udostępnić klientowi zaufany klucz główny przy użyciu pliku.  

-   Wstępnie udostępnić klientowi zaufany klucz główny bez użycia pliku.  

-   Sprawdź zaufany klucz główny w kliencie.  

> [!NOTE]  
>  Nie masz wstępnie udostępnić klientowi przy użyciu zaufanego klucza głównego, jeśli można to uzyskać z usług domenowych w usłudze Active Directory lub zostali zainstalowani za pomocą wypychania klienta. Ponadto nie trzeba wstępnie udostępnić klientom przy korzystaniu komunikację HTTPS z punktami zarządzania, ponieważ relacja zaufania została ustanowiona przy certyfikatów PKI.  

Zaufany klucz główny można usunąć z klienta za pomocą właściwości Client.msi **RESETKEYINFORMATION = TRUE**, z programem CCMSetup.exe. Aby zastąpić zaufany klucz główny, zainstaluj ponownie klienta wraz z nowym zaufanym kluczem głównym, na przykład używając instalacji wypychanej klienta lub określając właściwość **SMSPublicRootKey** pliku Client.msi za pomocą programu CCMSetup.exe.  

#### <a name="to-pre-provision-a-client-with-the-trusted-root-key-by-using-a-file"></a>Aby wstępnie udostępnić klientowi zaufany klucz główny przy użyciu pliku  

1.  W edytorze tekstu Otwórz plik,  *&lt;katalogu programu Configuration Manager\>***\bin\mobileclient.tcf**.  

2.  Znajdź wpis, **SMSPublicRootKey =**, skopiuj klucz z tego wiersza i zamknij plik bez wprowadzania żadnych zmian.  

3.  Utwórz nowy plik tekstowy i Wklej informacje o kluczu, skopiowany z pliku mobileclient.tcf.  

4.  Zapisz plik i umieść go w lokalizacji, gdzie wszystkie komputery do niego dostęp, ale gdy plik jest zabezpieczony manipulacjami.  

5.  Zainstaluj klienta przy użyciu dowolnej metody instalacji właściwości pliku Client.msi, a następnie określ właściwość pliku Client.msi **SMSROOTKEYPATH =***&lt;pełną ścieżkę i nazwę pliku\>*.  

    > [!IMPORTANT]  
    >  Po określeniu zaufanego klucza głównego w celu zapewnienia dodatkowych zabezpieczeń podczas instalacji klienta, należy również określić kod lokacji, używając właściwości pliku Client.msi **SMSSITECODE =&lt;kod lokacji\>**.  

#### <a name="to-pre-provision-a-client-with-the-trusted-root-key-without-using-a-file"></a>Aby wstępnie udostępnić klientowi zaufany klucz główny bez użycia pliku  

1.  W edytorze tekstu Otwórz plik,  *&lt;katalogu programu Configuration Manager\>***\bin\mobileclient.tcf**.  

2.  Znajdź wpis SMSPublicRootKey =, zanotuj klucz z tego wiersza lub skopiuj go do Schowka, a następnie zamknij plik bez wprowadzania żadnych zmian.  

3.  Zainstaluj klienta przy użyciu dowolnej metody instalacji właściwości pliku Client.msi, a następnie określ właściwość pliku Client.msi **SMSPublicRootKey =***&lt;klucz\>*, gdzie  *&lt;klucz\>*  to ciąg skopiowany z pliku mobileclient.tcf.  

    > [!IMPORTANT]  
    >  Po określeniu zaufanego klucza głównego w celu zapewnienia dodatkowych zabezpieczeń podczas instalacji klienta, należy również określić kod lokacji, używając właściwości pliku Client.msi **SMSSITECODE =&lt;kod lokacji\>**.  

#### <a name="to-verify-the-trusted-root-key-on-a-client"></a>Aby sprawdzić zaufany klucz główny w kliencie  

1.  Na **Start** menu, wybierz **Uruchom**, a następnie wprowadź **Wbemtest**.  

2.  W **Tester oprzyrządowania Instrumentacji zarządzania Windows** okno dialogowe Wybierz **Connect**.  

3.  W **Connect** okna dialogowego, **Namespace** wprowadź **root\ccm\locationservices**, a następnie wybierz **Connect**.  

4.  W **Tester oprzyrządowania Instrumentacji zarządzania Windows** okna dialogowego, **IWbemServices** wybierz **Wylicz klasy**.  

5.  W **informacje o superklasie** okno dialogowe Wybierz **cyklicznego**, a następnie wybierz **OK**.  

6.  W oknie **Wynik kwerendy** przewiń listę do końca, a następnie kliknij dwukrotnie pozycję **TrustedRootKey ()**.  

7.  W **Edytor obiektów dla TrustedRootKey** okno dialogowe Wybierz **wystąpienia**.  

8.  W nowym **wynik kwerendy** okna, które zawiera wystąpienia **TrustedRootKey**, kliknij dwukrotnie **TrustedRootKey = @**.  

9. W **Edytor obiektów dla TrustedRootKey = @** okna dialogowego, **właściwości** sekcji, przewiń w dół do **TrustedRootKey CIM_STRING**. Ciąg w prawej kolumnie to zaufany klucz główny. Sprawdź, czy jest on zgodny **SMSPublicRootKey** wartość z pliku  *&lt;katalogu programu Configuration Manager\>***\bin\mobileclient.tcf**.  

##  <a name="BKMK_PlanningForSigningEncryption"></a>Planowanie podpisywania i szyfrowania  
 Gdy certyfikat PKI jest używany do całej komunikacji z klientem, nie trzeba planować podpisywania i szyfrowania korespondencji w celu zabezpieczenia danych klienta. Ale po skonfigurowaniu systemów lokacji, w których serwer IIS zezwala na połączenia klienckie HTTP należy zdecydować, jak zabezpieczyć komunikację z klientem dla lokacji.  

 Aby chronić dane wysyłane przez klientów do punktów zarządzania, może wymagać danych do podpisania. Dodatkowo można wymóc, aby wszystkie podpisane dane z klientów używających protokołu HTTP zostały podpisane algorytmem SHA-256. Mimo że to ustawienie jest bezpieczniejsze, nie należy włączać tej opcji, jeśli wszyscy klienci nie obsługują algorytmu SHA-256. Wiele systemów operacyjnych w sposób natywny obsługuje algorytm SHA-256, ale w przypadku starszych systemów konieczna może być aktualizacja lub poprawka. Przykładowo w komputerach z systemem Windows Server 2003 SP2 trzeba zainstalować poprawkę hotfix, do której podano odwołanie w [artykule KB 938397](http://go.microsoft.com/fwlink/p/?LinkId=226666).  

 Podpisywanie chroni dane przed naruszeniem, a szyfrowanie utrudnia ujawnienie informacji. Istnieje możliwość włączenia szyfrowania algorytmem 3DES dla danych spisu oraz komunikatów o stanie wysyłanych przez klientów do punktów zarządzania w lokacji. Nie masz zainstalować wszystkie aktualizacje na komputerach klienckich w celu obsługi tej opcji, ale należy wziąć pod uwagę wyższe obciążenie Procesora wymagane do szyfrowania i odszyfrowywania na klientach i punktach zarządzania.  

 Aby uzyskać więcej informacji o sposobie konfigurowania ustawień podpisywania i szyfrowania, zobacz [Konfiguracja podpisywania i szyfrowania](../../../core/plan-design/security/configure-security.md#BKMK_ConfigureSigningEncryption) w sekcji [skonfigurować zabezpieczenia w programie System Center Configuration Manager](../../../core/plan-design/security/configure-security.md) artykułu.  

##  <a name="BKMK_PlanningForRBA"></a>Planowanie administracji opartej na rolach  
 Te informacje można znaleźć w temacie [podstawy administracji opartej na rolach programu System Center Configuration Manager](../../../core/understand/fundamentals-of-role-based-administration.md).  

### <a name="see-also"></a>Zobacz także
[Formanty kryptograficzne techniczne dla programu System Center Configuration Manager](../../../protect/deploy-use/cryptographic-controls-technical-reference.md).  

