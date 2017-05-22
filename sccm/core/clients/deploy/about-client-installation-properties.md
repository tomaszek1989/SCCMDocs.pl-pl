---
title: "Właściwości instalacji klienta | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat właściwości instalacji klienta w programie System Center Configuration Manager."
ms.custom: na
ms.date: 01/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c890fd27-7a8c-4f51-bbe2-f9908af1f42b
caps.latest.revision: 15
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4eee9731a4a27328c47c0d15931cab28cf520a18
ms.openlocfilehash: 11737bf2ff35dc9b04ec1d9690c0983ddd0c286a
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="about-client-installation-properties-in-system-center-configuration-manager"></a>Informacje o właściwościach instalacji klientów w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Aby ręcznie zainstalować klienta programu Configuration Manager za pomocą polecenia programu System Center Configuration Manager CCMSetup.exe.  

##  <a name="aboutCCMSetup"></a> CCMSetup.exe — informacje  
 Polecenie CCMSetup.exe pobiera pliki wymagane do zainstalowania klienta z punktem zarządzania lub lokalizacji źródłowej. Pliki te mogą obejmować:  

-   Pakiet Instalatora Windows Client.msi, który instaluje oprogramowanie klienta.  

-   Pliki instalacyjne Microsoft Background Intelligent Transfer Service (BITS).  

-   Pliki instalacyjne Instalatora Windows.  

-   Aktualizacje i poprawki dla klienta programu Configuration Manager.  

> [!NOTE]  
>  W programie Configuration Manager nie można uruchomić pliku Client.msi bezpośrednio.  

 Zawiera CCMSetup.exe [właściwości wiersza polecenia](#ccmsetup-exe-command-line-properties) dostosować instalację. Można również określać właściwości modyfikujące zachowanie się pliku Client.msi w wierszu polecenia CCMSetup.exe.  

> [!IMPORTANT]  
>  Przed określeniem właściwości pliku Client.msi, należy określić właściwości programu CCMSetup.  

 CCMSetup.exe i jego pliki pomocnicze znajdują się na serwerze lokacji programu Configuration Manager w **klienta** folderu do folderu instalacji programu Configuration Manager. Ten folder jest udostępniany w sieci jako  **&lt;nazwa serwera lokacji\>\SMS_&lt;kod lokacji\>\Client**.  

 W wierszu polecenia polecenie CCMSetup.exe posługuje się następującym formatem:  

 `CCMSetup.exe [&lt;Ccmsetup properties\>] [&lt;client.msi setup properties>]`  

 Przykład:  

 "CCMSetup.exe smsmp01/MP: / SMSSITECODE = S01 FSP = SMSFSP01"  

 W tym przykładzie wykonuje następujące czynności:  

-   Określa punkt zarządzania o nazwie smsmp01, który ma zażądać listy punktów dystrybucji, aby pobrać pliki instalacji klienta.  

-   Określa, że instalacja ma zostać zatrzymana, jeśli wersji klienta już istnieje na komputerze.  

-   Nakazuje plikowi client.msi przypisanie klienta do kodu lokacji S01.  

-   Nakazuje plikowi client.msi użycie rezerwowego punktu stanu o nazwie SMSFP01.  

> [!NOTE]  
>  Jeśli właściwość zawiera spacje, należy ująć ją w cudzysłów.  


> [!IMPORTANT]  
>  Jeśli schemat usługi Active Directory został rozszerzony dla programu Configuration Manager, wiele właściwości instalacji klienta są publikowane w usługach domenowych w usłudze Active Directory i odczytać automatycznie przez klienta programu Configuration Manager. Lista właściwości instalacji klienta publikowanych w Usługach domenowych Active Directory znajduje się w temacie [Informacje o właściwościach instalacji klienta publikowanych w Usługach domenowych Active Directory w programie System Center Configuration Manager](about-client-installation-properties-published-to-active-directory-domain-services.md)  

##  <a name="ccmsetupexe-command-line-properties"></a>Właściwości wiersza polecenia CCMSetup.exe  

### <a name=""></a>/?  

Otwiera okno dialogowe **CCMSetup**, w którym są wyświetlane właściwości wiersza polecenia ccmsetup.exe.  

Przykład: **ccmsetup.exe /?**  

### <a name="sourceltpath"></a>/ source:&lt;ścieżki\>  

 Określa lokalizację pobierania plików. Należy użyć ścieżki lokalnej lub ścieżki UNC. Pliki są pobierane przy użyciu protokołu bloku (komunikatów serwera SMB) komunikatów serwera.  Aby użyć **/source**, konto użytkownika systemu Windows do instalacji klienta musi mieć uprawnienia do odczytu do lokalizacji.

> [!NOTE]  
>  Można użyć **/source** właściwość wiele razy w wierszu polecenia do określenia lokalizacji alternatywnych pobierania.  

 Przykład: **ccmsetup.exe /source:"\\komputer\folder"**  

### <a name="mpltcomputer"></a>/MP:&lt;komputera\>

 Określa źródłowy punkt zarządzania dla komputerów nawiązać połączenie, dzięki czemu można znaleźć najbliższy punkt dystrybucji dla plików instalacyjnych. Jeśli nie ma żadnych punktów dystrybucji lub jeśli komputery nie mogą pobrać plików z punktów dystrybucji przez 4 godziny, klienci pobierają pliki z określonego punktu zarządzania.  

> [!IMPORTANT]  
>  Ta właściwość jest używana do określenia wstępnego punktu zarządzania dla komputerów, aby znaleźć źródła pobierania i może być dowolnym punktem zarządzania w dowolnej lokacji. Nie ma *przypisać* klienta z punktem zarządzania.   

 Komputery pobierają pliki w połączeniu HTTP lub HTTPS, zależnie od konfiguracji roli systemu lokacji dla połączeń klienckich. Pobieranie korzystają z usługi BITS ograniczania, jeśli skonfigurowane. Jeśli wszystkie punkty dystrybucji i punkty zarządzania są skonfigurowane dla tylko połączeń klienckich HTTPS, sprawdź, czy komputer kliencki ma prawidłowy certyfikat klienta.  

Właściwości **/mp** wiersza polecenia można użyć do określenia wielu punktów zarządzania, wówczas gdy komputerowi nie uda się połączyć z pierwszym punktem zarządzania, wypróbowuje się kolejny i tak dalej. Podczas określania wielu punktów zarządzania wartości należy rozdzielić średnikami.

Jeśli klient łączy się z punktem zarządzania przy użyciu protokołu HTTPS, zazwyczaj należy określić nazwę FQDN, a nie nazwę komputera. Wartość musi odpowiadać certyfikatu PKI podmiotu lub alternatywna nazwa podmiotu punktu zarządzania. Mimo że program Configuration Manager obsługuje używanie nazwy komputera w certyfikacie dla połączeń w intranecie, ze względów bezpieczeństwa zaleca się nazwy FQDN.

Przykład zastosowania nazwy komputera:`ccmsetup.exe /mp:SMSMP01`  

Przykład zastosowania nazwy FQDN:`ccmsetup.exe /mp:smsmp01.contoso.com`  

### <a name="retryltminutes"></a>/ Ponów:&lt;minut\>

Interwał ponawiania prób, jeśli CCMSetup.exe nie uda się pobrać plików instalacyjnych.  Program CCMSetup kontynuuje ponawianie prób, dopóki osiągnie limitu określonego w **downloadtimeout** właściwości.  

Przykład: `ccmsetup.exe /retry:20`  

### <a name="noservice"></a>/noservice

Zapobiega uruchamianiu, jako usługa, co jest ustawieniem domyślnym programu CCMSetup. Gdy program CCMSetup jest uruchamiany jako usługa, jest uruchamiany w kontekście konta System lokalny na komputerze, co może nie mieć wystarczających uprawnień dostępu do zasobów sieciowych wymaganych do instalacji. Z **/noservice**, CCMSetup.exe jest uruchamiany w kontekście konta użytkownika używanego do rozpoczęcia instalacji. Ponadto jeśli użyje się skryptu do uruchomienia CCMSetup.exe z **/service** właściwość CCMSetup.exe zostanie zakończony po uruchamiania i może nie raportować szczegółów instalacji prawidłowo.   

Przykład: `ccmsetup.exe /noservice`  

### <a name="service"></a>/service

Określa, że program CCMSetup ma być uruchomiony jako usługa z wykorzystaniem konta systemu lokalnego.  

Przykład: `ccmsetup.exe /service`  

### <a name="uninstall"></a>/uninstall

Określa, że można odinstalować oprogramowanie klienckie. Aby uzyskać więcej informacji, zobacz [Jak zarządzać klientami w programie System Center Configuration Manager](../manage/manage-clients.md).  

Przykład: `ccmsetup.exe /uninstall`  

### <a name="logon"></a>/logon

Określa, że instalacja klienta ma zostać zatrzymana, jeśli dowolna wersja klienta jest już zainstalowany.  

Przykład: `ccmsetup.exe /logon`  

### <a name="forcereboot"></a>/forcereboot

 Określa, że program CCMSetup ma wymusić ponowne uruchomienie w razie potrzeby w celu ukończenia instalacji komputera klienta. Jeśli nie zostanie określony, program CCMSetup zakończy działanie, gdy konieczne jest ponowne uruchomienie komputera i będzie je kontynuować dopiero po najbliższym ponownym uruchomieniu.  

 Przykład: `CCMSetup.exe /forcereboot`  

### <a name="bitspriorityltpriority"></a>/ BITSPriority:&lt;priorytet\>

 Określa priorytet pobieranie plików instalacji klienta w połączeniu HTTP. Dopuszczalne są następujące wartości:  

-   FOREGROUND (priorytet pierwszoplanowy)  

-   HIGH (priorytet wysoki)  

-   NORMAL (priorytet normalny)  

-   LOW (priorytet niski)  

 Wartość domyślna to NORMAL (priorytet normalny).  

 Przykład: `ccmsetup.exe /BITSPriority:HIGH`  

### <a name="downloadtimeoutltminutes"></a>/downloadtimeout:&lt;minut\>

Długość czasu w minutach, których program CCMSetup próbuje pobrać pliki instalacji przed zatrzymaniem. Wartość domyślna to **1440** minut (1 doba).  

Przykład: `ccmsetup.exe /downloadtimeout:100`  

### <a name="usepkicert"></a>/UsePKICert

 Gdy określona, klient używa certyfikatu PKI obejmującego uwierzytelnianie klienta. Jeśli nie można odnaleźć prawidłowego certyfikatu, klient korzysta z połączenia HTTP i certyfikatu z podpisem własnym, który jest również zachowanie, gdy ta właściwość nie jest używany.

> [!NOTE]  
>  W niektórych scenariuszach nie trzeba określać tej właściwości, podczas instalowania klienta i nadal używać certyfikatu klienta. Tego typu scenariuszy należą Instalowanie klienta za pomocą wypychania klienta i instalacja klienta oparta na punkcie aktualizacji oprogramowania. Należy jednak określić tę właściwość za każdym razem podczas ręcznej instalacji klienta i użycia właściwości **/mp** do określenia punktu zarządzania skonfigurowanego do akceptowania tylko połączeń klienckich HTTPS. Należy także określić tę właściwość podczas instalowania klienta komunikacji wyłącznie internetowej, używając właściwości CCMALWAYSINF=1 (wraz z właściwościami internetowego punktu zarządzania i kodu lokacji). Więcej informacji o internetowym zarządzaniu klientem znajduje się w sekcji [Uwagi dotyczące komunikacji klientów z Internetu lub niezaufanego lasu](../../plan-design/hierarchy/communications-between-endpoints.md#BKMK_clientspan) w temacie [Komunikacja między punktami końcowymi w programie System Center Configuration Manager](../../plan-design/hierarchy/communications-between-endpoints.md).  

 Przykład: `CCMSetup.exe /UsePKICert`  

### <a name="nocrlcheck"></a>/NoCRLCheck

 Określa, że klient ma nie sprawdzać listy odwołania certyfikatów (CRL), gdy komunikuje się za pośrednictwem protokołu HTTPS z certyfikatu PKI.  

 Gdy nie jest określony, klient sprawdza listy CRL, zanim nawiąże połączenie HTTPS.  

 Więcej informacji o sprawdzaniu listy CRL przez klienta znajduje się w sekcji [Planowanie odwoływania certyfikatów PKI](../../plan-design/security/plan-for-security.md#BKMK_PlanningForCRLs) w temacie [Planowanie zabezpieczeń w programie System Center Configuration Manager](../../plan-design/security/plan-for-security.md).  

 Przykład: `CCMSetup.exe /UsePKICert /NoCRLCheck`  

### <a name="configltconfiguration-file"></a>Właściwości instalacji/config:&lt;pliku konfiguracji\>

Określa nazwę pliku tekstowego zawierającego właściwości instalacji klienta.

- Jeśli nie określisz **/noservice** właściwość programu CCMSetup, ten plik musi znajdować się w folderze programu CCMSetup, którym jest % Windir %\\Ccmsetup dla 32-bitowych i 64-bitowych systemów operacyjnych.
- W przypadku określenia właściwości **/noservice** ten plik musi znajdować się w tym samym folderze, w którym jest uruchamiany program CCMSetup.exe.  

Przykład: `CCMSetup.exe /config:&lt;Configuration File Name.txt\>`  

Należy użyć pliku mobileclienttemplate.tcf &lt;katalogu programu Configuration Manager\>\\bin\\&lt;platformy\> folderu na komputerze serwera lokacji, aby zapewnić odpowiedni format pliku. Plik ten zawiera również komentarze o poszczególnych sekcjach i sposobach ich użycia. Określ właściwości instalacji klienta w sekcji [Client Install] po następującym tekście: **Zainstaluj = INSTALL = ALL**.  

Wpis w sekcji [Client Install] przykład:`Install=INSTALL=ALL SMSSITECODE=ABC SMSCACHESIZE=100`  

### <a name="skipprereqltfilename"></a>/skipprereq:&lt;nazwa pliku\>

 Określa, że CCMSetup.exe ma nie instalować określonego programu wymagań wstępnych, po zainstalowaniu klienta programu Configuration Manager. Ta właściwość obsługuje wprowadzanie wielu wartości. Wartości należy rozdzielać średnikiem (;).  


 Przykłady: `CCMSetup.exe /skipprereq:silverlight.exe` lub`CCMSetup.exe /skipprereq:dotnetfx40_client_x86_x64.exe;Silverlight.exe`  

### <a name="forceinstall"></a>/forceinstall

 Określ, że ewentualny istniejący klient zostanie odinstalowany i zostanie zainstalowany nowy klient.  

### <a name="excludefeaturesltfeature"></a>/ ExcludeFeatures:&lt;funkcji\>

Określa, że CCMSetup.exe ma nie instalować określonej funkcji, kiedy klient jest zainstalowany.  

Przykład: `CCMSetup.exe /ExcludeFeatures:ClientUI` Centrum oprogramowania nie można zainstalować na komputerze klienckim.  

> [!NOTE]  
>  W tej wersji **ClientUI** stanowi jedyną wartość obsługiwaną przez właściwość **/ExcludeFeatures** .  

##  <a name="ccmsetupReturnCodes"></a> Kody powrotne polecenia CCMSetup.exe  
 Polecenie CCMSetup.exe zapewnia następujące zwrócić kody ukończone. Rozwiązywanie problemów, można sprawdzić w pliku ccmsetup.log na komputerze klienckim kontekstu i dodatkowych szczegółów na temat kodów powrotnych  

|Kod powrotu|Znaczenie|  
|-----------------|-------------|  
|0|Powodzenie|  
|6|Błąd|  
|7|Wymagany ponowny rozruch|  
|8|Instalator jest już uruchomiony|  
|9|Błąd oceny wymagań wstępnych|  
|10|Błąd sprawdzania poprawności wartości skrótu manifestu instalacji|  

##  <a name="clientMsiProps"></a> Właściwości pliku Client.msi  
 Następujące właściwości mogą modyfikować zachowanie pliku client.msi związane z instalacją. W przypadku stosowania metody instalacji wypychanej klienta (instalacji w trybie push) właściwości można też określić na karcie **Klient** w oknie dialogowym **Właściwości instalacji wypychanej klienta** .  

### <a name="ccmadmins"></a>CCMADMINS  

Określa co najmniej jedno konto użytkownika lub grup użytkowników systemu Windows z dostępem do ustawień klienta i zasad. Jest to przydatne, gdy administrator programu Configuration Manager nie ma poświadczenia administratora lokalnego na komputerze klienckim. Określ listę kont oddzielonych średnikami.  

Przykład: `CCMSetup.exe CCMADMINS="Domain\Account1;Domain\Group1"`  

### <a name="ccmallowsilentreboot"></a>CCMALLOWSILENTREBOOT

Określa, czy komputer może zostać uruchomiony ponownie po instalacji klienta w razie potrzeby.  

> [!IMPORTANT]  
>  Komputer zostanie uruchomiony ponownie bez ostrzeżenia, nawet jeśli użytkownik jest zalogowany.  

Przykład: **CCMSetup.exe CCMALLOWSILENTREBOOT**  

### <a name="ccmalwaysinf"></a>CCMALWAYSINF

 Ustawienie wartości 1 oznacza, że klient będzie zawsze oparty na Internecie i nigdy nie będzie łączył się z intranetem. Typ połączenia klienta jest wyświetlany jako **Zawsze Internet**.  

 Tej właściwości powinno się używać w połączeniu z właściwością CCMHOSTNAME, która określa nazwę FQDN internetowego punktu zarządzania. Powinno się jej używać także z właściwością /UsePKICert programu CCMSetup i z kodem lokacji.  

 Więcej informacji o internetowym zarządzaniu klientem znajduje się w sekcji [Uwagi dotyczące komunikacji klientów z Internetu lub niezaufanego lasu](../../plan-design/hierarchy/communications-between-endpoints.md#BKMK_clientspan) w temacie [Komunikacja między punktami końcowymi w programie System Center Configuration Manager](../../plan-design/hierarchy/communications-between-endpoints.md).  

 Przykład: `CCMSetup.exe /UsePKICert  CCMALWAYSINF=1 CCMHOSTNAME=SERVER3.CONTOSO.COM SMSSITECODE=ABC`  

### <a name="ccmcertissuers"></a>CCMCERTISSUERS

 Określa listę wydawców certyfikatów, czyli listę zaufanych głównych certyfikatów certyfikacji (CA), które ufa lokacji programu Configuration Manager.  

 Więcej informacji o liście wydawców certyfikatów i sposobach jej użycia przez klientów w procesie wyboru certyfikatu znajduje się w sekcji [Planowanie wyboru certyfikatu klienta PKI](../../plan-design/security/plan-for-security.md#BKMK_PlanningForClientCertificateSelection) w temacie [Planowanie zabezpieczeń w programie System Center Configuration Manager](../../plan-design/security/plan-for-security.md).  

 To jest uwzględniające wielkość liter dopasowanie dotyczące atrybutów podmiotów z certyfikatu głównego urzędu certyfikacji. Atrybuty można rozdzielać przecinkiem (,) lub średnikiem (;). Można określić wiele certyfikatów głównego urzędu certyfikacji, używając separatora w postaci pionowej kreski. Przykład:  

 `CCMCERTISSUERS=”CN=Contoso Root CA; OU=Servers; O=Contoso, Ltd; C=US &#124; CN=Litware Corporate Root CA; O=Litware, Inc.”`  

> [!TIP]  
>  Odwołanie do pliku mobileclient.tcf &lt;katalogu programu Configuration Manager\>\bin\\&lt;platformy\> na komputerze serwera lokacji, aby skopiować folder **CertificateIssuers =&lt;ciąg\>**  skonfigurowaną dla lokacji.  

### <a name="ccmcertsel"></a>CCMCERTSEL

 Określa kryteria wyboru certyfikatu, jeżeli klient ma więcej niż jeden certyfikat do komunikacji HTTPS (ważny certyfikat, który obejmuje możliwość uwierzytelniania klienta).  

 Możesz wyszukać dokładne dopasowanie (Użyj **podmiotu:**) lub częściowe dopasowanie (Użyj **SubjectStr:)** w nazwie podmiotu lub alternatywna nazwa podmiotu. Przykłady:  

 `CCMCERTSEL="Subject:computer1.contoso.com"`Wyszukuje certyfikat dokładnie dopasowany do nazwy komputera "computer1.contoso.com" w nazwie podmiotu lub alternatywna nazwa podmiotu.  

 `CCMCERTSEL="SubjectStr:contoso.com"`Wyszukuje certyfikat zawierający ciąg "contoso.com" w nazwie podmiotu lub alternatywna nazwa podmiotu.  

 Dla atrybutów nazwy podmiotu lub alternatywnej nazwy podmiotu można także użyć atrybutów identyfikatora obiektu (OID) lub nazwy wyróżniającej, na przykład:  

 `CCMCERTSEL="SubjectAttr:2.5.4.11 = Computers"` wyszukuje atrybut jednostki organizacyjnej wyrażony jako identyfikator obiektu o nazwie Komputery.  

 `CCMCERTSEL="SubjectAttr:OU = Computers"` wyszukuje atrybut jednostki organizacyjnej wyrażony jako nazwa wyróżniająca Komputery.  

> [!IMPORTANT]  
>  Korzystając z pola Nazwa podmiotu **podmiotu:** jest uwzględniana wielkość liter, a **SubjectStr:** jest rozróżniana wielkość liter.  
>   
>  Korzystając z pola alternatywna nazwa podmiotu **podmiotu:**i **SubjectStr:** jest rozróżniana wielkość liter.  

 Pełna lista atrybutów używanych do wybierania certyfikatu znajduje się w temacie [Obsługiwane wartości atrybutów dotyczące kryteriów wyboru certyfikatów PKI](#BKMK_attributevalues).  

 Jeśli więcej niż jeden certyfikat spełnia kryteria wyszukiwania, a jako wartość właściwości CCMFIRSTCERT ustawiono 1, zostanie wybrany certyfikat o najdłuższym okresie ważności.  

### <a name="ccmcertstore"></a>CCMCERTSTORE

 Określa alternatywną nazwę magazynu certyfikatów, jeśli certyfikat klienta dla protokołu HTTPS nie znajduje się w domyślnym magazynie certyfikatów **osobiste** w magazynie komputera.  

 Przykład: `CCMSetup.exe /UsePKICert CCMCERTSTORE="ConfigMgr"`  

### <a name="ccmdebuglogging"></a>CCMDEBUGLOGGING

  Włącza funkcję rejestrowania debugowania. Wartości można ustawić na 0 (wyłączone, domyślnie) lub 1 (funkcja włączona). Powoduje to, że klient logowania niskiego poziomu informacji o rozwiązywaniu problemów. Najlepszym rozwiązaniem jest unikanie używania tej właściwości w lokacjach produkcyjnych, ponieważ może to skutkować rejestrowaniem nadmiernej ilości informacji, co z kolei może utrudnić wyszukiwanie istotnych informacji w plikach dziennika. Musi również być dla właściwości ccmenablelogging na wartość true, aby włączyć funkcję rejestrowania debugowania.  

  Przykład: `CCMSetup.exe CCMDEBUGLOGGING=1`  

### <a name="ccmenablelogging"></a>CCMENABLELOGGING

  Domyślnie ustawiona na wartość TRUE, aby włączyć rejestrowanie. Pliki dziennika są przechowywane w **dzienniki** folderu w folderze instalacji klienta programu Configuration Manager. Domyślna ścieżka tego folderu to %Windir%\CCM\Logs.  

  Przykład: `CCMSetup.exe CCMENABLELOGGING=TRUE`  

### <a name="ccmevalinterval"></a>CCMEVALINTERVAL  

 Częstotliwość u klienta uruchamiania narzędzia oceny kondycji (ccmeval.exe). Może być **1** do **1440** minut. Domyślnie uruchamiane raz dziennie.  

### <a name="ccmevalhour"></a>CCMEVALHOUR

 Godzinę uruchamiania narzędzia oceny kondycji klienta (ccmeval.exe), między **0** (północ) i **23** (godzina 23). Uruchamia o północy domyślnie.  

### <a name="ccmfirstcert"></a>CCMFIRSTCERT

 Jeśli jako wartość tej właściwości ustawiono 1, określa ona, że klient powinien wybrać certyfikat PKI o najdłuższym okresie ważności. To ustawienie może być wymagane w przypadku używania funkcji ochrony dostępu do sieci z wymuszaniem IPsec.  

 Przykład: `CCMSetup.exe /UsePKICert CCMFIRSTCERT=1`  

### <a name="ccmhostname"></a>CCMHOSTNAME

 Określa nazwę FQDN internetowego punktu zarządzania, jeśli zarządzanie klientem odbywa się za pośrednictwem sieci Web.  

 Nie należy określać tej opcji wraz z właściwością instalacyjną SMSSITECODE=AUTO. Klientów internetowych należy przypisać bezpośrednio do odpowiedniej lokacji internetowej.  

 Przykład: `CCMSetup.exe  /UsePKICert/ CCMHOSTNAME="SMSMP01.corp.contoso.com"`  

### <a name="ccmhttpport"></a>CCMHTTPPORT

 Określa port, którego powinien używać klient do komunikacji przy użyciu protokołu HTTP z serwerami systemu lokacji. Domyślnie do portu 80.  

 Przykład: `CCMSetup.exe CCMHTTPPORT=80`  

### <a name="ccmhttpsport"></a>CCMHTTPSPORT

Określa port, którego powinien używać klient do komunikacji przy użyciu protokołu HTTPS z serwerami systemu lokacji. Domyślnie numer portu 443.  

Przykład: `CCMSetup.exe /UsePKICert CCMHTTPSPORT=443`  

### <a name="ccminstalldir"></a>CCMINSTALLDIR

 Identyfikuje folder, w którym są zainstalowane pliki klienta programu Configuration Manager, *% Windir %*\CCM domyślnie. Niezależnie od tego, gdzie te pliki są zainstalowane, plik Ccmcore.dll będzie zawsze instalowana w *%Windir%\System32* folder. Ponadto w 64-bitowych systemach operacyjnych, kopia pliku Ccmcore.dll będzie zawsze instalowany w *% Windir %*\SysWOW64 folderu do obsługi 32-bitowych aplikacji, które używają 32-bitowej wersji interfejsów API klienta programu Configuration Manager z programu Configuration Manager programisty (SDK).  

 Przykład: `CCMSetup.exe CCMINSTALLDIR="C:\ConfigMgr"`  

### <a name="ccmloglevel"></a>CCMLOGLEVEL

Określa poziom szczegółów zapisywanych w plikach dziennika programu Configuration Manager. Określ liczbę całkowitą z zakresu od 0 do 3, gdzie 0 oznacza rejestrowanie najpełniejszych i 3 rejestruje tylko błędy. Domyślnym ustawieniem jest 1.  

Przykład: `CCMSetup.exe CCMLOGLEVEL=3`  

### <a name="ccmlogmaxhistory"></a>CCMLOGMAXHISTORY

Po osiągnięciu przez plik dziennika programu Configuration Manager 250 000 bajtów rozmiar (lub rozmiar określony we właściwości CCMMAXLOGSIZE), jego nazwa zostanie zmieniona na nazwę kopii zapasowej i zostanie utworzony nowy plik dziennika.  

Ta właściwość określa, ile poprzednich wersji pliku dziennika ma być przechowywanych. Wartość domyślna to 1. W przypadku wybrania wartości 0 nie będą przechowywane żadne stare pliki dziennika.  

Przykład: `CCMSetup.exe CCMLOGMAXHISTORY=0`  

### <a name="ccmlogmaxsize"></a>CCMLOGMAXSIZE

Maksymalny rozmiar pliku dziennika w bajtach. Gdy plik dziennika osiągnie określony rozmiar, jego nazwa zostanie zmieniona, plik zostanie zapisany jako plik historyczny i zostanie utworzony nowy plik. Minimalna wartość tej właściwości musi wynosić 10 000 bajtów. Domyślna wartość to 250 000 bajtów.  

Przykład: `CCMSetup.exe CCMLOGMAXSIZE=300000`  

### <a name="disablesiteopt"></a>DISABLESITEOPT

 Jeśli ustawiona na wartość PRAWDA, wyłącza możliwość zmiany programu Configuration Manager użytkownikom końcowym z poświadczeniami administracyjnymi na komputerze klienckim przypisanej lokacji w **programu Configuration Manager** Panelu sterowania na komputerze klienckim.  

 Przykład: **CCMSetup.exe DISABLESITEOPT = TRUE**  

### <a name="disablecacheopt"></a>DISABLECACHEOPT

Jeśli wartości TRUE uniemożliwi użytkownikom końcowym z poświadczeniami administracyjnymi na komputerze klienckim, aby zmienić klienta ustawień folderu pamięci podręcznej klienta programu Configuration Manager za pomocą programu Configuration Manager w Panelu sterowania komputera klienckiego.  

Przykład: `CCMSetup.exe DISABLECACHEOPT=TRUE`  

### <a name="dnssuffix"></a>DNSSUFFIX

 Określa domenę DNS dla klientów umożliwiającą lokalizowanie punktów zarządzania publikowanych w systemie DNS. Po zlokalizowaniu punktu zarządzania klient jest informowany o innych punktach zarządzania w hierarchii. Oznacza to, że punkt zarządzania zlokalizowany przy użyciu funkcji publikowania DNS nie musi znajdować się w lokacji klienta, lecz może być dowolnym punktem zarządzania w hierarchii.  

> [!NOTE]  
>  Nie trzeba określać tej właściwości, jeśli klient znajduje się w tej samej domenie co opublikowany punkt zarządzania. W takim przypadku domena klienta zostanie użyta automatycznie do wyszukiwania punktów zarządzania w systemie DNS.  

 Aby uzyskać więcej informacji o funkcji publikowania DNS jako metodzie lokalizowania usług dla klientów programu Configuration Manager, zobacz [usługa lokacji i metoda określania przypisanego punktu zarządzania przez klientów](../../plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md#BKMK_Plan_Service_Location) w [zrozumieć, jak klienci znaleźć zasoby witryny i usługi dla programu System Center Configuration Manager](../../plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md) .  

> [!NOTE]  
>  Domyślnie publikowania DNS nie jest włączona w programie Configuration Manager.  

 Przykład: `CCMSetup.exe SMSSITECODE=ABC DNSSUFFIX=contoso.com`  

### <a name="fsp"></a>FSP

Określa rezerwowy punkt stanu odbierający i przetwarzający komunikaty o stanie wysyłane przez komputery klienckie programu Configuration Manager.  

Aby uzyskać więcej informacji na temat rezerwowego punktu stanu, zobacz [ustalić, czy potrzebujesz rezerwowego punktu stanu](/sccm/core/clients/deploy/plan#determine-if-you-need-a-fallback-status-point).  

Przykład: `CCMSetup.exe FSP=SMSFP01`  

### <a name="ignoreappvversioncheck"></a>IGNOREAPPVVERSIONCHECK

 Określa, że obecność minimalnej wymaganej wersji programu Microsoft Application Virtualization (App-V) nie jest zaznaczone, przed zainstalowaniem klienta.  

> [!IMPORTANT]  
>  Po zainstalowaniu klienta programu Configuration Manager bez zainstalowania programu App-V, nie można wdrażać aplikacje wirtualne.  

 Przykład: `CCMSetup.exe IGNOREAPPVVERSIONCHECK=TRUE`  

### <a name="notifyonly"></a>NOTIFYONLY

Określa, że stan klienta będzie raportowany, ale nie będą korygowane wykryte w kliencie.  

Przykład: `CCMSetup.exe NOTIFYONLY=TRUE`  

Aby uzyskać więcej informacji, zobacz [Jak skonfigurować stan klienta w programie System Center Configuration Manager](configure-client-status.md).  

### <a name="resetkeyinformation"></a>RESETKEYINFORMATION

 Jeśli klient programu Configuration Manager ma nieprawidłowy klucz zaufanego głównego programu Configuration Manager i nie można skontaktować się z zaufanym punktem zarządzania w celu otrzymania nowego zaufanego klucza głównego, należy ręcznie usunąć stary zaufany klucz główny przy użyciu tej właściwości. Ta sytuacja może wystąpić w przypadku przeniesienia klienta z hierarchii jednej lokacji do innego. Ta właściwość dotyczy klientów komunikujących się za pośrednictwem protokołów HTTP i HTTPS.  

 Przykład: `CCMSetup.exe RESETKEYINFORMATION=TRUE`  

### <a name="sitereassign"></a>SITEREASSIGN

Włącza ponownego przypisania lokacji automatycznych uaktualnień klienta, gdy jest używane z [SMSSITECODE](#smssitecode)= AUTO.

Przykład: `CCMSetup.exe SMSSITECODE=AUTO SITEREASSIGN=TRUE`

### <a name="smscachedir"></a>SMSCACHEDIR

Określa lokalizację folderu pamięci podręcznej klienta na komputerze klienckim, służącym do przechowywania plików tymczasowych. Domyślna lokalizacja to *%Windir \ccmcache*.  

Przykład: `CCMSetup.exe SMSCACHEDIR="C:\Temp"`  

Ta właściwość może służyć w połączeniu z właściwością SMSCACHEFLAGS, aby kontrolować lokalizację folderu pamięci podręcznej klienta.  

Przykład: `CCMSetup.exe SMSCACHEDIR=Cache SMSCACHEFLAGS=MAXDRIVE` instaluje folder pamięci podręcznej klienta na największym dysku dostępna klienta.  

### <a name="smscacheflags"></a>SMSCACHEFLAGS

Określa dodatkowe szczegóły instalacji folderu pamięci podręcznej klienta. Właściwości SMSCACHEFLAGS można używać osobno lub razem, oddzielonych średnikami. W przypadku nieokreślenia tej właściwości folder pamięci podręcznej zostanie zainstalowany zgodnie z ustawieniem właściwości SMSCACHEDIR, nie będzie skompresowany, a wartość właściwości SMSCACHESIZE będzie oznaczała graniczną wielkość folderu w MB.  

To ustawienie zostanie zignorowane w przypadku uaktualniania istniejącego klienta.  

Właściwości:  

-   PERCENTDISKSPACE: Określa rozmiar folderu jako procent całkowitego miejsca na dysku. W przypadku określenia tej właściwości należy określić również właściwość SMSCACHESIZE oznaczającą, że ma być używana wartość procentowa.  

-   PERCENTFREEDISKSPACE: Określa rozmiar folderu jako procent wolnego miejsca na dysku. W przypadku określenia tej właściwości należy określić również właściwość SMSCACHESIZE oznaczającą, że ma być używana wartość procentowa. Jeśli na przykład na dysku znajduje się 10 MB wolnego miejsca, a wartość właściwości SMSCACHESIZE wynosi 50, rozmiar folderu będzie wynosił 5 MB. Nie można używać tej właściwości wraz z właściwością PERCENTDISKSPACE.  

-   MAXDRIVE: Określa, że folder zostanie zainstalowany na największym dostępnym dysku. Ta wartość zostanie zignorowana w przypadku określenia ścieżki przy użyciu właściwości SMSCACHEDIR.  

-   MAXDRIVESPACE: Określa, że folder zostanie zainstalowany na dysku, który ma najwięcej wolnego miejsca. Ta wartość zostanie zignorowana w przypadku określenia ścieżki przy użyciu właściwości SMSCACHEDIR.  

-   NTFSONLY: Określa, że folder może być zainstalowany wyłącznie na dyskach NTFS. Ta wartość zostanie zignorowana w przypadku określenia ścieżki przy użyciu właściwości SMSCACHEDIR.  

-   KOMPRESUJ: Określa, że folder powinien być stoed w postaci skompresowanej.  

-   FAILIFNOSPACE: Określa, że należy usunąć oprogramowanie klienta, jeśli jest zbyt mało miejsca na zainstalowanie folderu.  

Przykład: `CCMSetup.exe SMSCACHEFLAGS=NTFSONLY;COMPRESS`  


### <a name="smscachesize"></a>SMSCACHESIZE

> [!IMPORTANT]
> Począwszy od programu Configuration Manager 1606 wersji, nowe ustawienia klienta są dostępne do określania rozmiar folderu pamięci podręcznej klienta. Dodane ustawienia klienta skutecznie zastępują użycie właściwości SMSCACHESIZE jako właściwości pliku client.msi służącej do określania rozmiaru pamięci podręcznej klienta. Aby uzyskać więcej informacji, zobacz [ustawienia klienta dla rozmiaru pamięci podręcznej](about-client-settings.md#client-cache-settings).  

W wersji 1602 i starszych właściwość SMSCACHESIZE określa rozmiar folderu pamięci podręcznej klienta w megabajtach (MB) lub jako wartość procentową używaną wraz z właściwością PERCENTDISKSPACE lub PERCENTFREEDISKSPACE. Jeśli ta właściwość nie zostanie skonfigurowana, domyślny maksymalny rozmiar folderu będzie wynosił 5120 MB. Najniższa wartość, którą można określić, to 1 MB.  

> [!NOTE]  
>  Jeśli pobranie wymaganego nowego pakietu spowodowałoby przekroczenie maksymalnego rozmiaru folderu, którego nie można ponadto wyczyścić w celu zapewnienia odpowiedniej ilości wolnego miejsca, pobranie pakietu zakończy się niepowodzeniem, zaś program lub aplikacja nie zostaną uruchomione.  

To ustawienie zostanie zignorowane podczas uaktualniania istniejącego klienta oraz pobierania aktualizacji oprogramowania przez klienta.  

Przykład: `CCMSetup.exe SMSCACHESIZE=100`  

> [!NOTE]  
>  W przypadku ponownej instalacji klienta nie można użyć właściwości instalacji SMSCACHESIZE lub SMSCACHEFLAGS, aby zmniejszy dopuszczalny rozmiar pamięci podręcznej w stosunku do poprzedniego ustawienia. Próba tym wartość jest ignorowana, a rozmiar pamięci podręcznej zostanie automatycznie ustawiony rozmiar, które wcześniej były.  

### <a name="smsconfigsource"></a>SMSCONFIGSOURCE

Określa lokalizację i kolejność, które Instalator programu Configuration Manager sprawdza, czy ustawienia konfiguracji. Właściwość ma postać ciągu zawierającego co najmniej jeden znak definiujący określone źródło konfiguracji. Należy użyć znaków R, P, M oraz U, oddzielnie lub razem:  

-   R: Sprawdzenie ustawień konfiguracji w rejestrze.  

   Aby uzyskać więcej informacji, zobacz [informacji o zapisywaniu właściwości instalacji klienta w rejestrze.](https://technet.microsoft.com/library/gg712298.aspx#BKMK_Provision).  

-   P: Sprawdzenie ustawień konfiguracji we właściwościach instalacji podawanych w wierszu polecenia.  

-   M: Sprawdzenie istniejących ustawień podczas uaktualniania starszego klienta przy użyciu oprogramowania klienckiego programu Configuration Manager.  

-   U: Uaktualnienie zainstalowanego klienta do nowszej wersji (oraz użycie kodu przypisanej lokacji).  

 Domyślnie instalacja klienta używa ciągu `PU` w celu sprawdzenia właściwości instalacji, a następnie istniejących ustawień.  

 Przykład: `CCMSetup.exe SMSCONFIGSOURCE=RP`  

### <a name="smsdirectorylookup"></a>SMSDIRECTORYLOOKUP

 Określa, czy klient może używać usługi nazw internetowych systemu Windows (WINS) do znalezienia punktu zarządzania przyjmującego połączenia przy użyciu protokołu HTTP. Klienci używają tej metody, gdy nie mogą znaleźć punktu zarządzania w usługach domenowych w usłudze Active Directory lub systemie DNS.  

 Ta właściwość nie ma wpływu na, czy klient używa usługi WINS do rozpoznawania nazw.  

 Można skonfigurować dwa różne tryby tej właściwości:  

-   NOWINS: Jest to najbezpieczniejsze ustawienie tej właściwości i uniemożliwia klientom znalezienie punktu zarządzania w usłudze WINS.  W przypadku zastosowania tego ustawienia klienci muszą dysponować alternatywną metodą lokalizowania punktu zarządzania w intranecie, na przykład przy użyciu usług domenowych w usłudze Active Directory lub funkcji publikowania DNS.  

-   WINSSECURE (ustawienie domyślne): W tym trybie klient używający protokołu HTTP do komunikacji może używać usługi WINS do znajdowania punktu zarządzania. Aby jednak klient mógł pomyślnie nawiązać połączenie z punktem zarządzania, musi mieć kopię zaufanego klucza głównego. Aby uzyskać więcej informacji, zobacz sekcję [Planowanie zaufanego klucza głównego](../../plan-design/security/plan-for-security.md#BKMK_PlanningForRTK) w temacie [Planowanie zabezpieczeń w programie System Center Configuration Manager](../../plan-design/security/plan-for-security.md).  


 Przykład: `CCMSetup.exe SMSDIRECTORYLOOKUP=NOWINS`  

### <a name="smsmp"></a>SMSMP

Określa początkowy punkt zarządzania do użytku klienta programu Configuration Manager.  

> [!IMPORTANT]  
>  Jeśli punkt zarządzania akceptuje tylko połączenia klienta za pośrednictwem protokołu HTTPS, należy prefiks nazwy punktu zarządzania z https://.  

Przykład:`CCMSetup.exe SMSMP=smsmp01.contoso.com`  

Przykład: `CCMSetup.exe SMSMP=smsmp01.contoso.com`

Przykład: `CCMSetup.exe SMSMP=https://smsmp01.contoso.com`  

### <a name="smspublicrootkey"></a>SMSPUBLICROOTKEY

 Określa programu Configuration Manager zaufanego klucza głównego, gdy nie można pobrać z usług domenowych w usłudze Active Directory. Ta właściwość dotyczy klientów komunikujących się za pośrednictwem protokołów HTTP i HTTPS. Aby uzyskać więcej informacji, zobacz sekcję [Planowanie zaufanego klucza głównego](../../plan-design/security/plan-for-security.md#BKMK_PlanningForRTK) w temacie [Planowanie zabezpieczeń w programie System Center Configuration Manager](../../plan-design/security/plan-for-security.md).  

 Przykład: `CCMSetup.exe SMSPUBLICROOTKEY=&lt;key\>`  

### <a name="smsrootkeypath"></a>SMSROOTKEYPATH

 Służy do ponownego zainstalowania zaufanego klucza głównego programu Configuration Manager. Określa pełną ścieżkę i nazwę pliku zawierającego zaufany klucz główny. Ta właściwość dotyczy klientów komunikujących się za pośrednictwem protokołów HTTP i HTTPS. Aby uzyskać więcej informacji, zobacz sekcję [Planowanie zaufanego klucza głównego](../../plan-design/security/plan-for-security.md#BKMK_PlanningForRTK) w temacie [Planowanie zabezpieczeń w programie System Center Configuration Manager](../../plan-design/security/plan-for-security.md).  

 Przykład: "CCMSetup.exe SMSROOTKEYPATH =&lt;Pełna ścieżka i nazwa pliku\>`  

### <a name="smssigncert"></a>SMSSIGNCERT

 Określa pełną ścieżkę i nazwę pliku .cer wyeksportowanego certyfikatu z podpisem własnym na serwerze lokacji.  

 Ten certyfikat jest przechowywany w magazynie certyfikatów **SMS** i ma przypisane nazwę podmiotu **Serwer lokacji** oraz przyjazną nazwę **Certyfikat podpisywania serwera lokacji**.  

 Przykład: **CCMSetup.exe UsePKICert SMSSIGNCERT =&lt;pełną ścieżkę i nazwę pliku\>**  

### <a name="smssitecode"></a>SMSSITECODE

 Określa lokację programu Configuration Manager do przypisywania klientów programu Configuration Manager. Może to być kod trzech znaków lub słowo AUTO. Jeśli AUTO jest określony lub nie określono tej właściwości, klient spróbuje określić jego przypisania do lokacji programu Configuration Manager z usług domenowych w usłudze Active Directory lub z określonego punktu zarządzania. Aby włączyć automatyczne dla uaktualnienia klienta, należy również ustawić [SITEREASSIGN](#sitereassign) na wartość TRUE.    

> [!NOTE]  
>  Nie należy używać wartości AUTO, jeśli określono również internetowy punkt zarządzania (CCMHOSTNAME). W takim przypadku należy bezpośrednio przypisać klienta do lokacji.  

 Przykład: `CCMSetup.exe SMSSITECODE=XZY`  

##  <a name="BKMK_attributevalues"></a> Obsługiwane wartości atrybutów dotyczące kryteriów wyboru certyfikatów PKI  
 Program Configuration Manager obsługuje następujące wartości atrybutów dotyczące kryteriów wyboru certyfikatów PKI:  

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
