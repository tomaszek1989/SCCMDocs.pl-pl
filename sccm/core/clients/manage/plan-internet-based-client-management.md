---
title: "Zarządzanie klientami internetowymi | Dokumentacja firmy Microsoft"
description: "Tworzenie planu zarządzania klientów internetowych w programie System Center Configuration Manager."
ms.custom: na
ms.date: 05/16/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 83a7c934-3b11-435d-ba22-cbc274951e83
caps.latest.revision: 7
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: ae60eb25383f4bd07faaa1265185a471ee79b1e9
ms.openlocfilehash: 90c30bfb22735f73422f1547301552bf42022bb9
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="plan-for-internet-based-client-management-in-system-center-configuration-manager"></a>Planowanie zarządzania klientami w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Umożliwia zarządzanie (czasami nazywany IBCM) klienta internetowego zarządzania programu System Center Configuration Manager sieci klientów, gdy nie są one połączone z firmy, ale używają standardowego połączenia internetowego. Taki układ zapewnia kilka korzyści, takich jak mniejsze koszty ze względu na brak konieczności uruchomienia wirtualnych sieci prywatnych (VPN) oraz możliwość wdrażania aktualizacji oprogramowania w odpowiednim czasie.  

 Zarządzanie komputerami klienckimi w sieci publicznej wiąże się z większymi wymaganiami w zakresie zabezpieczeń, dlatego w ramach internetowego zarządzania klienci muszą łączyć się z serwerami systemu lokacji przy użyciu certyfikatów PKI. Dzięki temu połączenia są uwierzytelnianie przez niezależny urząd, a dane przesyłane między tymi systemami lokacji są szyfrowane przy użyciu protokołu SSL (Secure Sockets Layer).  

 W poniższych sekcjach znajdują się informacje ułatwiające planowanie internetowego zarządzania klientami.  

##  <a name="features-that-are-not-supported-on-the-internet"></a>Funkcje nieobsługiwane przez Internet  
 Nie wszystkich funkcji zarządzania klientami można używać za pośrednictwem Internetu; z tego powodu nie są one obsługiwane w przypadku zarządzania klientami przez Internet. Funkcje nieobsługiwane w przypadku zarządzania internetowego zazwyczaj są zależne od usług domenowych Active Directory lub nie można ich używać w sieci publicznej, na przykład odnajdywanie sieci i Wake-on-LAN (WOL).  

 Następujące funkcje nie są obsługiwane w przypadku zarządzania klientami przez Internet:  

-   Wdrażanie klientów przez Internet, na przykład instalacja wypychana i wdrażanie klienta oparte na aktualizacjach oprogramowania; klienta należy zainstalować ręcznie  

-   Automatyczne przypisanie lokacji  

-   Wake-on-LAN  

-   Wdrożenie systemu operacyjnego (istnieje jednak możliwość wdrożenia sekwencji zadań nie obejmujących wdrożenia systemu operacyjnego; na przykład sekwencji uruchamiających skrypty i zadania obsługi na kliencie)  

-   Zdalne sterowanie  

-   Wdrożenie oprogramowania dla użytkowników, jeżeli internetowy punkt zarządzania nie może uwierzytelnić użytkownika w usługach domenowych Active Directory za pomocą uwierzytelniania systemu Windows (Kerberos lub NTLM); jest to możliwe, gdy istnieje relacja zaufania między internetowym punktem zarządzania a lasem, w którym znajduje się konto użytkownika  

 Ponadto internetowe zarządzanie klientami nie obsługuje roamingu. Klienci mogą przy użyciu roamingu zawsze znaleźć najbliższe punkty dystrybucji z dostępna do pobrania zawartością. Klienci zarządzani przez Internet komunikują się z systemami lokacji z poziomu przypisanej im lokacji, jeśli systemy te zostały skonfigurowane do używania internetowej nazwy FQDN, a role systemu lokacji zezwalają na połączenia z klientem przez Internet. Klienci wybierają w sposób niejednoznaczny jeden z internetowych systemów lokacji niezależnie od przepustowości lub lokalizacji fizycznej.  

 Jeśli masz punkt aktualizacji oprogramowania skonfigurowany do akceptowania połączeń z Internetu, klienci internetowi programu Configuration Manager w Internecie będą zawsze skanowani względem tego punktu aktualizacji oprogramowania w celu określenia wymaganych aktualizacji oprogramowania. Jednak gdy ci klienci są połączeni z Internetem, najpierw próbują pobrać aktualizacje oprogramowania z usługi Microsoft Update, a nie z internetowego punktu dystrybucji. Dopiero, gdy to się nie powiedzie, zostanie podjęta próba pobrania niezbędnych aktualizacji oprogramowania z internetowego punktu dystrybucji. Klienci, którzy nie zostali skonfigurowani do internetowego zarządzania nigdy nie próbują pobrać aktualizacje oprogramowania z witryny Microsoft Update, ale zawsze używać punktów dystrybucji programu Configuration Manager.  

##  <a name="considerations-for-client-communications-from-the-internet-or-untrusted-forest"></a>Uwagi dotyczące komunikacji klienta z Internetu lub niezaufanego lasu  
 Następujące role systemu lokacji zainstalowane w lokacjach głównych obsługują połączenia od klientów z lokalizacji niezaufanych, takich jak Internet lub niezaufany las (lokacje dodatkowe nie obsługują połączeń klientów z niezaufanych lokalizacji):  

-   Punkt witryny sieci Web wykazu aplikacji  

-   Moduł zasad programu Configuration Manager  

-   Punkt dystrybucji (protokół HTTPS jest wymagany przez punkty dystrybucji oparte na chmurze)  

-   Punkt proxy rejestracji  

-   Rezerwowy punkt stanu  

-   Punkt zarządzania  

-   Punkt aktualizacji oprogramowania  

 **Systemy lokacji dostępne w Internecie:**   
Chociaż nie jest wymagane ma relację zaufania między lasem klienta i serwera systemu lokacji, gdy las zawierający system lokacji dostępnymi przez Internet zaufanie między lasem zawierającym konta użytkowników, ta konfiguracja obsługuje zasady na podstawie użytkownika dla urządzeń w Internecie, po włączeniu **zasad klienta** ustawienia klienta **Włącz żądania zasad użytkownika od klientów internetowych**.  

 Następujące konfiguracje stanowią przykłady obsługi zasad użytkowników na urządzeniach połączonych z Internetem w ramach internetowego zarządzania klientami:  

-   Internetowy punkt zarządzania należy do sieci obwodowej, w której znajduje się kontroler domeny tylko do odczytu umożliwiający uwierzytelnianie użytkownika, a pośrednicząca zapora zezwala na pakiety usługi Active Directory.  

-   Konto użytkownika znajduje się w lesie A (sieć intranet), a internetowy punkt zarządzania znajduje się w lesie B (sieć obwodowa). Między lasem B a lasem A istnieje relacja zaufania i pośrednicząca zapora zezwala na pakiety uwierzytelniania.  

-   Konto użytkownika i internetowy punkt zarządzania znajdują się w lesie A (sieć intranet). Punkt zarządzania jest publikowany w Internecie przy użyciu serwera proxy sieci Web (na przykład Forefront Threat Management Gateway).  

> [!NOTE]  
>  W przypadku niepowodzenia uwierzytelniania przy użyciu Kerberos automatycznie zostanie podjęta próba uwierzytelniania NTLM.  

 Zgodnie z poprzednim przykładem internetowe systemy lokacji można umieścić w sieci intranet, gdy są publikowane w Internecie przy użyciu serwera proxy sieci web (na przykład ISA Server i Forefront Threat Management Gateway). Te systemy lokacji można skonfigurować do połączeń z klientem tylko przez Internet lub zarówno przez Internet, jak i sieć intranet. W przypadku używania serwera proxy sieci web można na nim skonfigurować mostkowanie SSL (bezpieczniejsza konfiguracja) lub tunelowanie SSL:  

-   **Mostkowanie do protokołu SSL:**   
    To zalecana konfiguracja w przypadku korzystania z serwerów proxy sieci Web do internetowego zarządzania klientami, która obejmuje kończenie żądań SSL z uwierzytelnianiem. Uwierzytelnianie komputerów klienckich musi odbywać się przy użyciu uwierzytelniania komputera, a uwierzytelnianie starszych klientów urządzeń przenośnych przy użyciu uwierzytelniania użytkownika. Urządzenia przenośne zarejestrowane przez program Configuration Manager nie obsługują mostkowania SSL.  

     Dzięki funkcji kończenia żądań SSL na serwerze proxy sieci web pakiety z Internetu są poddawane inspekcji przed przekazaniem ich do sieci wewnętrznej. Serwer proxy sieci web uwierzytelnia połączenie nawiązywane przez klienta, kończy je, a następnie nawiązuje nowe uwierzytelnione połączenie z internetowymi systemami lokacji. Jeżeli klienci programu Configuration Manager przy użyciu serwera proxy sieci web, tożsamość klienta (GUID) jest bezpiecznie przechowywana w ładunku pakietu, dzięki czemu punkt zarządzania nie traktuje serwera proxy sieci web jako klienta. Mostkowanie nie jest obsługiwane w programie Configuration Manager za pomocą protokołu HTTP i HTTPS HTTP.  

-   **Tunelowanie**:   
    Jeśli serwer proxy sieci web nie spełnia wymagań dla mostkowania SSL lub użytkownik chce skonfigurować obsługę internetową urządzeń przenośnych zarejestrowanych przez program Configuration Manager, jest obsługiwane także tunelowanie SSL. To mniej bezpieczna opcja, ponieważ pakiety SSL z Internetu są przekazywane do systemów lokacji bez zakończenia żądań SSL, a tym samym nie można przeprowadzić ich inspekcji pod kątem złośliwej zawartości. W przypadku używania funkcji tunelowania SSL nie istnieją wymagania dotyczące certyfikatów serwera proxy sieci web.  

##  <a name="planning-for-internet-based-clients"></a>Planowanie obsługi klientów internetowych  
 Należy wybrać, czy komputery klienckie zarządzane za pośrednictwem Internetu mają zostać skonfigurowane do zarządzania w sieci intranet oraz w Internecie, czy tylko do zarządzania internetowego. Opcję zarządzania klientami można skonfigurować tylko podczas instalacji komputera klienckiego. Aby później zmienić tę opcję, należy ponownie zainstalować klienta.  

> [!NOTE]  
>  W przypadku skonfigurowania punktu zarządzania z dostępem do Internetu klient połączony z tym punktem zarządzania również uzyska dostęp do Internetu po odświeżeniu listy dostępnych punktów zarządzania.  

> [!TIP]  
>  Konfiguracja zarządzania klientami nie musi obejmować tylko zarządzania za pośrednictwem Internetu. Można również korzystać do tego celu z sieci intranet.  

 Klienci skonfigurowani wyłącznie do zarządzania internetowego komunikują się tylko z systemami lokacji skonfigurowanymi do połączeń z klientami za pośrednictwem Internetu. Ta konfiguracja jest odpowiednia w przypadku komputerów, które nigdy nie łączą się z firmową siecią intranet, na przykład komputerów w punktach sprzedaży w lokalizacjach zdalnych. Można ją również odpowiednie Chcąc ograniczyć komunikacji z klientem do HTTPS tylko (na przykład w celu obsługi zapory oraz zasad ograniczonych zabezpieczeń), a podczas instalowania systemów witryny internetowe w sieci obwodowej i chcesz zarządzać tymi serwerami przy użyciu klienta programu Configuration Manager.  

 Aby zarządzać klientami grupy roboczej w Internecie, należy zainstalować ich jako klientów zarządzanych tylko internetowo.  

> [!NOTE]  
>  Klienci urządzeń przenośnych są automatycznie konfigurowani do zarządzania tylko za pośrednictwem Internetu, gdy używają internetowego punktu zarządzania.  

 Pozostałe komputery klienckie można skonfigurować do zarządzania internetowego i intranetowego. Ci klienci mogą automatycznie wybierać internetowe lub intranetowe zarządzanie klientami po wykryciu zmiany sieci. Ci klienci po znalezieniu i połącz się z punktem zarządzania skonfigurowanym dla połączeń klienckich w sieci intranet, są zarządzani jako klienci sieci intranet, które mają pełną funkcjonalność zarządzania programu Configuration Manager. Jeżeli klienci nie mogą znaleźć lub połączyć się z punktem zarządzania skonfigurowanym do połączeń za pośrednictwem sieci intranet, próbują nawiązać połączenie z internetowym punktem zarządzania. Gdy połączenie zostanie pomyślnie nawiązane, zarządzanie tymi klientami odbywa się przy użyciu internetowych systemów lokacji w przypisanej do nich lokacji.  

 Korzyści w automatyczne przełączanie między zarządzania klientami internetowe lub intranetowe Zarządzanie klientami jest komputerom klienckim można automatycznie korzystać ze wszystkich funkcji programu Configuration Manager za każdym razem są podłączone do sieci intranet i nadal będą zarządzane dla podstawowych funkcji zarządzania, gdy są one połączone z Internetem. Ponadto pobieranie rozpoczęte w Internecie można bezbłędnie wznowić w sieci intranet i odwrotnie.  

##  <a name="prerequisites-for-internet-based-client-management"></a>Wymagania wstępne dotyczące internetowego zarządzania klientami  
 Zarządzanie klientami w programie Configuration Manager ma następującymi zależnościami zewnętrznymi:  

-   Klienci zarządzani za pośrednictwem Internetu muszą mieć połączenie internetowe.  

     Program Configuration Manager używa istniejące połączenia przez Internet, który może być stałych lub tymczasowych połączeń usługodawcy internetowego (ISP). Klienckie urządzenia przenośne muszą mieć bezpośrednie połączenie internetowe, lecz komputery klienckie mogą oprócz tego połączenia łączyć się również przy użyciu serwera proxy sieci web.  

-   Systemy lokacji obsługujące internetowe zarządzanie klientami muszą mieć łączność z Internetem i należeć do domeny usługi Active Directory.  

     Internetowe systemy lokacji nie wymagają relacji zaufania z lasem usługi Active Directory serwera lokacji. Jeżeli jednak internetowy punkt zarządzania uwierzytelnia użytkownika za pomocą uwierzytelniania systemu Windows, obsługiwane są zasady użytkownika. W przypadku niepowodzenia uwierzytelniania systemu Windows obsługiwane są tylko zasady komputera.  

    > [!NOTE]  
    >  Aby umożliwić obsługę zasad użytkownika, należy również ustawić wartość **Prawda** w dwóch ustawieniach klienta **Zasady klienta**:  
    >   
    >  -   **Włącz sondowanie zasad użytkownika na klientach**  
    > -   **Włącz żądania dotyczące zasad użytkownika od klientów internetowych**  

     Internetowy punkt witryny sieci Web katalogu aplikacji również wymaga uwierzytelniania systemu Windows do uwierzytelniania użytkowników, gdy należący do niego komputer jest połączony z Internetem. To wymaganie jest niezależne od zasad użytkownika.  

-   Wymagana jest obsługiwana infrastruktura kluczy publicznych (PKI), która umożliwia wdrażanie i zarządzanie certyfikatami wymaganymi przez klientów, zarządzanymi za pośrednictwem Internetu oraz internetowych serwerów systemu lokacji.  

     Aby uzyskać więcej informacji na temat certyfikatów PKI, zobacz [Wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager](/sccm/core/plan-design/network/pki-certificate-requirements).  

-   internetowa w pełni kwalifikowana nazwa domeny (FQDN) systemów lokacji obsługujących internetowe zarządzanie klientami musi być zarejestrowana w ramach wpisów hosta na serwerach DNS.  

-   Pośredniczące zapory lub serwery proxy: muszą zezwalać na komunikację klienta skojarzonego z internetowymi systemami lokacji.  

     Wymagania dotyczące komunikacji z klientem:  

    -   Obsługa protokołu HTTP 1.1  

    -   Zezwalanie na typ zawartości HTTP wieloczęściowego załącznika MIME (wieloczęściowy/mieszany oraz aplikacja/strumień oktetu)  

    -   Zezwalanie na następujące czasowniki internetowego punktu zarządzania:  

        -   HEAD  

        -   CCM_POST  

        -   BITS_POST  

        -   GET  

        -   PROPFIND  

    -   Zezwalanie na następujące czasowniki internetowego punktu dystrybucji:  

        -   HEAD  

        -   GET  

        -   PROPFIND  

    -   Zezwalanie na następujące czasowniki internetowego rezerwowego punktu stanu:  

        -   POST  

    -   Zezwalanie na następujące czasowniki internetowego punktu witryny sieci Web katalogu aplikacji:  

        -   POST  

        -   GET  

    -   Zezwalanie na następujące nagłówki HTTP internetowego punktu zarządzania:  

        -   Zakres:  

        -   CCMClientID:  

        -   CCMClientIDSignature:  

        -   CCMClientTimestamp:  

        -   CCMClientTimestampsSignature:  

    -   Zezwalanie na następujący nagłówek HTTP internetowego punktu dystrybucji:  

        -   Zakres:  

     Informacje dotyczące konfiguracji zapewniającej obsługę tych wymagań znajdują się w dokumentacji zapory lub serwera proxy.  

     Informacje o podobnych wymaganiach dotyczących komunikacji w przypadku połączeń internetowych z klientami za pośrednictwem punktu aktualizacji oprogramowania znajdują się w dokumentacji usług Windows Server Update Services (WSUS). Na przykład dla programu WSUS w systemie Windows Server 2003, zobacz [Appendix D: Ustawienia zabezpieczeń](http://go.microsoft.com/fwlink/p/?LinkId=143368), zawierającym załącznik do wdrożenia dotyczący ustawień zabezpieczeń.

