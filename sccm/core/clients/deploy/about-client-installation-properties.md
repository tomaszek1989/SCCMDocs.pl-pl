---
title: Właściwości instalacji klienta
titleSuffix: Configuration Manager
description: Więcej informacji o właściwościach wiersza polecenia ccmsetup w przypadku instalowania klienta programu Configuration Manager.
ms.date: 03/28/2018
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: c890fd27-7a8c-4f51-bbe2-f9908af1f42b
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 27479bf3db9ab0ed5d842f5cbf9db4e399a4168d
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="about-client-installation-properties-in-system-center-configuration-manager"></a>Informacje o właściwościach instalacji klientów w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Aby zainstalować klienta programu Configuration Manager, należy użyć polecenia CCMSetup.exe. Jeśli podasz te właściwości instalacji klienta w wierszu polecenia modyfikują zachowanie instalacji.



##  <a name="aboutCCMSetup"></a> CCMSetup.exe — informacje  
 Polecenie CCMSetup.exe pobiera pliki wymagane do zainstalowania klienta z punktem zarządzania lub lokalizacji źródła. Te pliki mogą być następujące:  

-   Client.msi pakietu Instalatora Windows, który instaluje oprogramowanie klienta.  

-   Pliki instalacyjne Microsoft Background Intelligent Transfer Service (BITS).  

-   Pliki instalacyjne Instalatora Windows.  

-   Aktualizacje i poprawki dla klienta programu Configuration Manager.  

> [!NOTE]  
>  W programie Configuration Manager nie można uruchomić pliku Client.msi bezpośrednio.  

 Udostępnia CCMSetup.exe [właściwości wiersza polecenia](#ccmsetup-exe-command-line-properties) dostosować instalację. Można również określić właściwości modyfikujące zachowanie się pliku client.msi w wierszu polecenia programu CCMSetup.exe.  

> [!IMPORTANT]  
>  Określ właściwości programu CCMSetup, aby określić właściwości pliku Client.msi.  

 CCMSetup.exe i pliki pomocnicze, które znajdują się na serwerze lokacji w **klienta** folderu w folderze instalacyjnym programu Configuration Manager. Ten folder jest udostępniany w sieci jako  **&lt;nazwa serwera lokacji\>\SMS_&lt;kod lokacji\>\Client**.  

 W wierszu polecenia polecenie CCMSetup.exe posługuje się następującym formatem:  

 `CCMSetup.exe [<Ccmsetup properties>] [<client.msi setup properties>]`  

 Na przykład:  

   `CCMSetup.exe /mp:SMSMP01 /logon SMSSITECODE=S01 FSP=SMSFSP01`  

 W tym przykładzie wykonuje następujące czynności:  

-   Określa punkt zarządzania o nazwie smsmp01, który ma zażądać listy punktów dystrybucji, aby pobrać pliki instalacji klienta.  

-   Określa, że instalacja ma zostać zatrzymana, jeśli wersji klienta już istnieje na komputerze.  

-   Nakazuje plikowi client.msi przypisanie klienta do kodu lokacji S01.  

-   Nakazuje plikowi client.msi użycie rezerwowego punktu stanu o nazwie SMSFP01.  

> [!NOTE]  
>  Jeśli właściwość zawiera spacje, należy ująć ją w znaki cudzysłowu.  


> [!IMPORTANT]  
>  W przypadku rozszerzenia schematu usługi Active Directory dla programu Configuration Manager lokacja publikuje wiele właściwości instalacji klienta w usługach domenowych w usłudze Active Directory. Klient programu Configuration Manager automatycznie odczytuje tych właściwości. Aby uzyskać więcej informacji, zobacz [o właściwościach instalacji klienta publikowanych w usługach domenowych w usłudze Active Directory](about-client-installation-properties-published-to-active-directory-domain-services.md)  



##  <a name="ccmsetupexe-command-line-properties"></a>Właściwości wiersza polecenia CCMSetup.exe  

### <a name=""></a>/?  

Otwiera okno dialogowe **CCMSetup**, w którym są wyświetlane właściwości wiersza polecenia ccmsetup.exe.  

Przykład: **ccmsetup.exe /?**  

### <a name="sourceltpath"></a>/ source:&lt;ścieżki\>  

 Określa lokalizację pobierania pliku. Użyj lokalną lub ścieżkę UNC. Pliki są pobierane przy użyciu protokołu serwera komunikat protokołu SMB. Aby użyć **/source**, konta użytkownika systemu Windows do instalacji klienta musi mieć uprawnienia do odczytu do lokalizacji.

> [!NOTE]  
>  Można użyć **/source** właściwości więcej niż raz w wierszu polecenia, aby określić alternatywne lokalizacje.  

 Przykład: **ccmsetup.exe /source:"\\komputer\folder"**  

### <a name="mpltserver"></a>/MP:&lt;serwera\>

 Określa punkt zarządzania źródła dla komputerów nawiązać połączenie. Komputery użycie tego punktu zarządzania, aby znaleźć najbliższy punkt dystrybucji dla plików instalacyjnych. Jeśli nie ma punktów dystrybucji lub komputery nie mogą pobrać pliki z punktów dystrybucji po upływie czterech godzin, będą oni mogli pobrać plików z określonym punktem zarządzania.  

> [!IMPORTANT]  
>  Ta właściwość służy do określania początkowy punkt zarządzania na komputerach w celu znalezienia źródła pobierania i może być dowolnym punktem zarządzania w dowolnej lokacji. Nie *przypisać* klienta z punktem zarządzania.   

 Komputery pobierają pliki w połączeniu HTTP lub HTTPS, zależnie od konfiguracji roli systemu lokacji dla połączeń klienckich. Jeśli skonfigurowana, procesy pobierania korzystają z ograniczenia przepustowości usługi BITS. Jeśli wszystkie punkty dystrybucji i punkty zarządzania są skonfigurowane dla tylko połączeń klienckich HTTPS, sprawdź, czy komputer kliencki ma prawidłowy certyfikat klienta.  

Można użyć **/mp** właściwości wiersza polecenia, aby określić więcej niż jeden punkt zarządzania. Jeśli komputer nie może połączyć się z pierwszym punktem, próbuje dalej na liście. Podczas określania wielu punktów zarządzania, poszczególne wartości należy rozdzielić średnikami.

Jeśli klient łączy się z punktem zarządzania przy użyciu protokołu HTTPS, zazwyczaj należy określić nazwę FQDN, a nie nazwa komputera. Wartość musi odpowiadać certyfikatu PKI podmiotu lub alternatywna nazwa podmiotu punktu zarządzania. Mimo że program Configuration Manager obsługuje przy użyciu nazwy komputera w certyfikacie dla połączeń w intranecie, nazwy FQDN jest najlepszą zalecaną praktyką zabezpieczeń.

Przykład zastosowania nazwy komputera: `ccmsetup.exe /mp:SMSMP01`  

Przykład zastosowania nazwy FQDN: `ccmsetup.exe /mp:smsmp01.contoso.com`  

Tej właściwości można określić adres URL zarządzania bramy chmury. Użyj tego adresu URL, aby zainstalować klienta na urządzeniu z systemem internetowym. Aby uzyskać wartość dla tej właściwości, wykonaj następujące kroki:
- Utwórz bramę zarządzania chmury.
- Na aktywnego klienta otwórz wiersz polecenia programu Windows PowerShell jako administrator. 
- Uruchom następujące polecenie: `(Get-WmiObject -Namespace Root\Ccm\LocationServices -Class SMS_ActiveMPCandidate | Where-Object {$_.Type -eq "Internet"}).MP`
- Dołącz prefiks "https://", który ma być używany z **/mp** właściwości.

Przykład zastosowania adres URL bramy zarządzania chmury: `ccmsetup.exe /mp:https://CONTOSO.CLOUDAPP.NET/CCM_Proxy_MutualAuth/72057598037248100`

 > [!Important]
 > Podczas określania adresu URL bramy zarządzania chmury dla **/mp** właściwości, musi rozpoczynać się **https://**.


### <a name="retryltminutes"></a>/ Ponów:&lt;minut\>

Interwał ponawiania, jeśli CCMSetup.exe nie uda się pobrać pliki instalacyjne. Program CCMSetup kontynuuje ponawianie prób, dopóki nie osiągnie limitu określonego we **downloadtimeout** właściwości.  

Przykład: `ccmsetup.exe /retry:20`  

### <a name="noservice"></a>/noservice

Zapobiega uruchamianiu jako usługa, która jest ustawiona domyślnie programu CCMSetup. Gdy program CCMSetup jest uruchamiany jako usługa, jest uruchamiany w kontekście konta systemu lokalnego komputera. To konto może nie mieć wystarczających praw dostępu do zasobów sieciowych wymaganych do instalacji. Z **/noservice**, CCMSetup.exe jest uruchamiany w kontekście konta użytkownika, którego używasz do rozpoczęcia instalacji. Ponadto jeśli używasz skryptu do uruchomienia CCMSetup.exe z **/service** , czyli CCMSetup.exe zostanie zakończony po uruchomieniu usługi i może nie raportować szczegółów instalacji prawidłowo.   

Przykład: `ccmsetup.exe /noservice`  

### <a name="service"></a>/service

Określa, że program CCMSetup ma być uruchomiony jako usługa z wykorzystaniem konta systemu lokalnego.  

Przykład: `ccmsetup.exe /service`  

### <a name="uninstall"></a>/uninstall

Określa, że można odinstalować oprogramowanie klienckie. Aby uzyskać więcej informacji, zobacz [jak zarządzać klientami](../manage/manage-clients.md).  

Przykład: `ccmsetup.exe /uninstall`  

### <a name="logon"></a>/logon

Jeśli jakakolwiek wersja klienta jest już zainstalowany, ta właściwość określa, że instalacja klienta ma zostać zatrzymana.  

Przykład: `ccmsetup.exe /logon`  

### <a name="forcereboot"></a>/forcereboot

 Określa, że program CCMSetup ma wymusić na komputerze klienckim, uruchom ponownie, jeśli jest to niezbędne do ukończenia instalacji. Jeśli ta właściwość nie jest określony, program CCMSetup zakończy działanie, gdy konieczne jest ponowne uruchomienie. Następnie kontynuuje po najbliższym ponownym uruchomieniu.  

 Przykład: `CCMSetup.exe /forcereboot`  

### <a name="bitspriorityltpriority"></a>/ BITSPriority:&lt;priorytet\>

 Określa priorytet pobieranie plików instalacji klienta w połączeniu HTTP. Dopuszczalne są następujące wartości:  

-   FOREGROUND (priorytet pierwszoplanowy)  

-   HIGH (priorytet wysoki)  

-   NORMAL (priorytet normalny)  

-   LOW (priorytet niski)  

 Wartość domyślna to NORMAL (priorytet normalny).  

 Przykład: `ccmsetup.exe /BITSPriority:HIGH`  

### <a name="downloadtimeoutltminutes"></a>/ downloadtimeout:&lt;minut\>

Długość czas w minutach, których program CCMSetup próbuje pobrać pliki instalacyjne przed zatrzymaniem. Wartość domyślna to **1440** minut (jeden dzień).  

Przykład: `ccmsetup.exe /downloadtimeout:100`  

### <a name="usepkicert"></a>/UsePKICert

 Jeśli określone, klient używa certyfikatu PKI obejmującego uwierzytelnianie klienta, jeśli jest dostępna. Jeśli klient nie może znaleźć prawidłowego certyfikatu, za pomocą połączeń HTTP i certyfikatu z podpisem własnym. To zachowanie jest takie same, jeśli ta właściwość nie jest używany.

> [!NOTE]  
>  W niektórych scenariuszach nie trzeba określić tę właściwość podczas instalowania klienta i nadal używać certyfikatu klienta. Tego typu scenariuszy należą Instalowanie klienta za pomocą wypychania klienta i instalacja klienta oparta na punkcie aktualizacji oprogramowania. Należy jednak określić tę właściwość za każdym razem podczas ręcznej instalacji klienta i użycia właściwości **/mp** do określenia punktu zarządzania skonfigurowanego do akceptowania tylko połączeń klienckich HTTPS. Należy również określić tę właściwość podczas instalowania klienta komunikacji wyłącznie internetowej. Użyj CCMALWAYSINF = 1 właściwości wraz z właściwościami punkt zarządzania internetowego i kod lokacji. Aby uzyskać więcej informacji dotyczących zarządzania klientami internetowymi, zobacz [uwagi dotyczące komunikacji klientów z Internetu lub niezaufanego lasu](../../plan-design/hierarchy/communications-between-endpoints.md#BKMK_clientspan).  

 Przykład: `CCMSetup.exe /UsePKICert`  

### <a name="nocrlcheck"></a>/NoCRLCheck

 Określa, że klient nie powinien sprawdzać listy odwołania certyfikatów (CRL) podczas komunikacji za pośrednictwem protokołu HTTPS przy użyciu certyfikatu PKI.  

 Jeśli nie zostanie określony, klient sprawdza listę CRL przed nawiązaniem połączenia HTTPS.  

 Aby uzyskać więcej informacji o sprawdzaniu listy CRL klienta, zobacz [planowanie odwoływania certyfikatów PKI](../../plan-design/security/plan-for-security.md#BKMK_PlanningForCRLs).  

 Przykład: `CCMSetup.exe /UsePKICert /NoCRLCheck`  

### <a name="configltconfiguration-file"></a>/ config:&lt;pliku konfiguracji\>

Określa nazwę pliku tekstowego zawierającego właściwości instalacji klienta.

- Jeśli nie określisz **/noservice** właściwość programu CCMSetup, ten plik musi znajdować się w folderze programu CCMSetup, którym jest % Windir %\\Ccmsetup dla 32-bitowych i 64-bitowych systemów operacyjnych.
- W przypadku określenia właściwości **/noservice** ten plik musi znajdować się w tym samym folderze, w którym jest uruchamiany program CCMSetup.exe.  

Przykład: `CCMSetup.exe /config:&lt;Configuration File Name.txt\>`  

Aby zapewnić odpowiedni format pliku, należy użyć pliku mobileclienttemplate.tcf z &lt;katalog programu Configuration Manager\>\\bin\\&lt;platformy\> folderu na serwerze lokacji. Ten plik zawiera również komentarzy o poszczególnych sekcjach i sposób ich używania. Określ właściwości instalacji klienta w sekcji [Client Install] po następującym tekście: **Zainstaluj = INSTALL = ALL**.  

Wpis w sekcji [Client Install] przykład: `Install=INSTALL=ALL SMSSITECODE=ABC SMSCACHESIZE=100`  

### <a name="skipprereqltfilename"></a>/ skipprereq:&lt;filename\>

 Określa, że CCMSetup.exe ma nie instalować określonego programu wymagań wstępnych, podczas instalowania klienta programu Configuration Manager. Ta właściwość obsługuje wprowadzanie wielu wartości. Wartości należy rozdzielać średnikiem (;).  


 Przykłady: `CCMSetup.exe /skipprereq:dotnetfx40_client_x86_x64.exe` lub `CCMSetup.exe /skipprereq:dotnetfx40_client_x86_x64.exe;windowsupdateagent30_x86.exe`  

### <a name="forceinstall"></a>/forceinstall

 Określ CCMSetup.exe odinstalowuje ewentualny istniejący klient i instaluje nowy klient.  

### <a name="excludefeaturesltfeature"></a>/ ExcludeFeatures:&lt;funkcji\>

Określa, że CCMSetup.exe nie instalować określonej funkcji podczas instalacji klienta.  

Przykład: `CCMSetup.exe /ExcludeFeatures:ClientUI` na kliencie nie instaluje się Centrum oprogramowania.  

> [!NOTE]  
>  **ClientUI** jest jedyną wartość obsługiwaną **/ExcludeFeatures** właściwości.  



##  <a name="ccmsetupReturnCodes"></a> Kody powrotne polecenia CCMSetup.exe  
 Polecenie CCMSetup.exe przekazuje następujące ukończone kody powrotne. Aby rozwiązać problemy, sprawdź plik ccmsetup.log na komputerze klienckim dla kontekstu i dodatkowych informacji na temat kodów powrotnych.  

|Kod powrotu|Znaczenie|  
|-----------------|-------------|  
|0|Powodzenie|  
|6|Błąd|  
|7|Wymagany ponowny rozruch|  
|8|Instalator jest już uruchomiony|  
|9|Błąd oceny wymagań wstępnych|  
|10|Błąd sprawdzania poprawności wartości skrótu manifestu instalacji|  



## <a name="ccmsetupMsiProps"></a> Właściwości Ccmsetup.msi  
 Następujące właściwości można zmodyfikować zachowanie instalacji określone ccmsetup.msi.

### <a name="ccmsetupcmd"></a>CCMSETUPCMD 

Określa właściwości wiersza polecenia, które są przekazywane do ccmsetup.exe, po jego zainstalowaniu, ccmsetup.msi. Mają inne właściwości wewnątrz cudzysłowów. Tej właściwości należy użyć, gdy uruchamianie klienta programu Configuration Manager przy użyciu metody instalacji Intune zarządzanie urządzeniami Przenośnymi. 

Przykład: `ccmsetup.msi CCMSETUPCMD="/mp:https://mp.contoso.com CCMHOSTNAME=mp.contoso.com"`

 > [!Tip]
 > Microsoft Intune ogranicza wiersza polecenia do 1024 znaków. 



##  <a name="clientMsiProps"></a> Właściwości pliku Client.msi  
 Następujące właściwości mogą modyfikować zachowanie pliku client.msi związane z instalacją. W przypadku stosowania metody instalacji wypychanej klienta (instalacji w trybie push) właściwości można też określić na karcie **Klient** w oknie dialogowym **Właściwości instalacji wypychanej klienta** .  


### <a name="aadclientappid"></a>AADCLIENTAPPID

Określa identyfikator aplikacji klienta usługi Azure Active Directory (Azure AD). Aplikacja kliencka jest tworzony lub zaimportowane, kiedy należy [Konfigurowanie usług Azure](/sccm/core/servers/deploy/configure/azure-services-wizard) do zarządzania chmurą. Administrator usługi Azure można uzyskać wartość dla tej właściwości przy użyciu portalu Azure. Aby uzyskać więcej informacji, zobacz [uzyskiwanie Identyfikatora aplikacji](/azure/azure-resource-manager/resource-group-create-service-principal-portal#get-application-id-and-authentication-key). Aby uzyskać **AADCLIENTAPPID** właściwości, ten identyfikator aplikacji jest typu "Native" aplikacja.

Przykład: `ccmsetup.exe AADCLIENTAPPID=aa28e7f1-b88a-43cd-a2e3-f88b257c863b`


### <a name="aadresourceuri"></a>AADRESOURCEURI

Określa identyfikator aplikacji serwera usługi Azure AD. Aplikacja serwera jest tworzony lub zaimportowane podczas możesz [Konfigurowanie usług Azure](/sccm/core/servers/deploy/configure/azure-services-wizard) do zarządzania chmurą. Podczas tworzenia aplikacji serwera, w oknie dialogowym Tworzenie aplikacji serwera, ta właściwość jest **identyfikator URI aplikacji**.

Administrator usługi Azure można uzyskać wartość dla tej właściwości przy użyciu portalu Azure. W **usługi Azure Active Directory** bloku znajdowanie aplikacji serwera w obszarze **rejestracji aplikacji**. Ta aplikacja jest "aplikacja sieci Web / interfejs API" typ aplikacji. Otwórz aplikację, kliknij przycisk **ustawienia**, a następnie **właściwości**. Użyj **identyfikator URI aplikacji** wartość tej właściwości instalacji klienta AADRESOURCEURI.

Przykład: `ccmsetup.exe AADRESOURCEURI=https://contososerver`


### <a name="aadtenantid"></a>AADTENANTID

Określa identyfikator dzierżawy usługi Azure AD. Tej dzierżawy jest połączony do programu Configuration Manager po możesz [Konfigurowanie usług Azure](/sccm/core/servers/deploy/configure/azure-services-wizard) do zarządzania chmurą. Aby uzyskać wartość dla tej właściwości, wykonaj następujące czynności:
- Na urządzeniu z systemem Windows 10, który jest dołączony do tej samej dzierżawy usługi Azure AD Otwórz wiersz polecenia.
- Uruchom następujące polecenie: `dsregcmd.exe /status`
- W sekcji stanu urządzenia, Znajdź **TenantId** wartości. Na przykład `TenantId : 607b7853-6f6f-4d5d-b3d4-811c33fdd49a`

 > [!Note]
 > Administrator usługi Azure można również uzyskać tę wartość w portalu Azure. Aby uzyskać więcej informacji, zobacz [uzyskanie Identyfikatora dzierżawy](/azure/azure-resource-manager/resource-group-create-service-principal-portal#get-tenant-id)

Przykład: `ccmsetup.exe AADTENANTID=607b7853-6f6f-4d5d-b3d4-811c33fdd49a`

<!-- 
### AADTENANTNAME

Specifies the Azure AD tenant name. This tenant is linked to Configuration Manager when you [configure Azure services](/sccm/core/servers/deploy/configure/azure-services-wizard) for Cloud Management. To obtain the value for this property, use the following steps:
- On a Windows 10 device that is joined to the same Azure AD tenant, open a command prompt.
- Run the following command: `dsregcmd.exe /status`
- In the Device State section, find the **TenantName** value. For example, `TenantName : Contoso`

Example: `ccmsetup.exe AADTENANTNAME=Contoso`
-->

### <a name="ccmadmins"></a>CCMADMINS  

Określa co najmniej jedno konto użytkownika lub grup użytkowników systemu Windows z dostępem do ustawień klienta i zasad. Ta właściwość jest przydatna, gdy administrator programu Configuration Manager nie dysponuje lokalnymi poświadczeniami administracyjnymi na komputerze klienckim. Określ listę kont oddzielonych średnikami.  

Przykład: `CCMSetup.exe CCMADMINS="Domain\Account1;Domain\Group1"`  

### <a name="ccmallowsilentreboot"></a>CCMALLOWSILENTREBOOT

Określa, czy komputer może zostać ponownie uruchom po instalacji klienta, jeśli to konieczne.  

> [!IMPORTANT]  
>  Komputer zostanie uruchomiony bez ostrzeżenia, nawet jeśli użytkownik jest zalogowany.  

Przykład: **CCMSetup.exe CCMALLOWSILENTREBOOT**  

### <a name="ccmalwaysinf"></a>CCMALWAYSINF

 Ustaw **1** do określenia, czy klient jest zawsze oparty na Internecie i nigdy nie nawiązuje połączenie z siecią intranet. Typ połączenia klienta jest wyświetlany jako **Zawsze Internet**.  

 Tej właściwości należy użyć w połączeniu z właściwością CCMHOSTNAME, która określa nazwę FQDN punktu zarządzania internetowego. Także używać z właściwością/usepkicert programu CCMSetup i z kodem lokacji.  

 Aby uzyskać więcej informacji dotyczących zarządzania klientami internetowymi, zobacz [uwagi dotyczące komunikacji klientów z Internetu lub niezaufanego lasu](../../plan-design/hierarchy/communications-between-endpoints.md#BKMK_clientspan).  

 Przykład: `CCMSetup.exe /UsePKICert  CCMALWAYSINF=1 CCMHOSTNAME=SERVER3.CONTOSO.COM SMSSITECODE=ABC`  

### <a name="ccmcertissuers"></a>CCMCERTISSUERS

 Określa listę wydawców certyfikatów, czyli listę zaufanych certyfikatów głównych certyfikatów certyfikacji (CA), które ufa lokacja programu Configuration Manager.  

 Aby uzyskać więcej informacji o liście wystawców certyfikatów i sposobie używania jej przez klientów w procesie wyboru certyfikatu, zobacz [planowanie wyboru certyfikatu klienta PKI](../../plan-design/security/plan-for-security.md#BKMK_PlanningForClientCertificateSelection).  

 Ta wartość jest rozróżniana wielkość liter dopasowanie dotyczące atrybutów podmiotów, które znajdują się w certyfikat głównego urzędu certyfikacji. Atrybuty można rozdzielać przecinkiem (,) lub średnikiem (;). Za pomocą separatora, można określić więcej niż jeden certyfikatów głównego urzędu certyfikacji. Przykład:  

 `CCMCERTISSUERS=”CN=Contoso Root CA; OU=Servers; O=Contoso, Ltd; C=US &#124; CN=Litware Corporate Root CA; O=Litware, Inc.”`  

> [!TIP]  
>  Aby skopiować **CertificateIssuers =&lt;ciąg\>**  dla witryny, Przywołaj plik mobileclient.tcf w &lt;katalog programu Configuration Manager\>\bin\\ &lt;platformy\> folderu na serwerze lokacji.  

### <a name="ccmcertsel"></a>CCMCERTSEL

 Określa kryteria wyboru certyfikatu, jeżeli klient ma więcej niż jeden certyfikat do komunikacji HTTPS. Ten certyfikat jest ważny certyfikat, który obejmuje możliwość uwierzytelniania klienta.  

 Można wyszukiwać dopasowania dokładne (Użyj **podmiotu:**) lub częściowe dopasowanie (Użyj **SubjectStr:)** w nazwie podmiotu lub alternatywna nazwa podmiotu. Przykłady:  

 `CCMCERTSEL="Subject:computer1.contoso.com"` Wyszukuje certyfikat dokładnie dopasowany do nazwy komputera "computer1.contoso.com" w nazwie podmiotu lub alternatywna nazwa podmiotu.  

 `CCMCERTSEL="SubjectStr:contoso.com"` Wyszukuje certyfikat zawierający ciąg "contoso.com" w nazwie podmiotu lub alternatywna nazwa podmiotu.  

 Dla atrybutów nazwy podmiotu lub alternatywnej nazwy podmiotu można także użyć atrybutów identyfikatora obiektu (OID) lub nazwy wyróżniającej, na przykład:  

 `CCMCERTSEL="SubjectAttr:2.5.4.11 = Computers"` wyszukuje atrybut jednostki organizacyjnej wyrażony jako identyfikator obiektu o nazwie Komputery.  

 `CCMCERTSEL="SubjectAttr:OU = Computers"` wyszukuje atrybut jednostki organizacyjnej wyrażony jako nazwa wyróżniająca Komputery.  

> [!IMPORTANT]  
>  Jeśli korzystasz z pola Nazwa podmiotu **podmiotu:** jest rozróżniana wielkość liter i **SubjectStr:** nie uwzględnia wielkości liter.  
>   
>  Jeśli w przypadku korzystania z pola alternatywna nazwa podmiotu **podmiotu:** i **SubjectStr:** jest rozróżniana wielkość liter.  

 Pełna lista atrybutów, których można użyć do wybrania certyfikatu ma na liście [obsługiwane wartości atrybutów dotyczące kryteriów wyboru certyfikatów PKI](#BKMK_attributevalues).  

 Jeśli więcej niż jeden certyfikat spełnia kryteria wyszukiwania, a jako wartość właściwości CCMFIRSTCERT ustawiono 1, zostanie wybrany certyfikat o najdłuższym okresie ważności.  

### <a name="ccmcertstore"></a>CCMCERTSTORE

 Określa alternatywną nazwę magazynu certyfikatów, jeśli certyfikat klienta dla protokołu HTTPS nie znajduje się w domyślnym magazynie certyfikatów **osobistych** w magazynie komputera.  

 Przykład: `CCMSetup.exe /UsePKICert CCMCERTSTORE="ConfigMgr"`  

### <a name="ccmdebuglogging"></a>CCMDEBUGLOGGING

  Włącza funkcję rejestrowania debugowania. Wartości można ustawić na 0 (wyłączone, ustawienie domyślne) lub 1 (włączone). Ta właściwość powoduje, że klienta informacji niskiego poziomu do rozwiązywania problemów. Najlepszym rozwiązaniem należy unikać używania tej właściwości w lokacjach produkcyjnych. Mogą wystąpić rejestrowaniem nadmiernej ilości, która może utrudnić wyszukiwanie istotnych informacji w plikach dziennika. Ponadto ustawiono CCMENABLELOGGING na wartość PRAWDA, aby włączyć funkcję rejestrowania debugowania.  

  Przykład: `CCMSetup.exe CCMDEBUGLOGGING=1`  

### <a name="ccmenablelogging"></a>CCMENABLELOGGING

  Domyślnie ta właściwość ma ustawioną wartość TRUE Aby włączyć rejestrowanie. Pliki dziennika są przechowywane w **dzienniki** folderu w folderze instalacji klienta programu Configuration Manager. Domyślna ścieżka tego folderu to %Windir%\CCM\Logs.  

  Przykład: `CCMSetup.exe CCMENABLELOGGING=TRUE`  

### <a name="ccmevalinterval"></a>CCMEVALINTERVAL  

 Częstotliwość w klienta uruchamiania narzędzia oceny kondycji (ccmeval.exe). Może być **1** do **1440** minut. Domyślnie jest uruchamiane raz dziennie.  

### <a name="ccmevalhour"></a>CCMEVALHOUR

 Godzina, kiedy narzędzia oceny kondycji klienta (ccmeval.exe) jest uruchamiana, między **0** (północ) i **23** (godzina 23). Uruchomień północy domyślnie.  

### <a name="ccmfirstcert"></a>CCMFIRSTCERT

 Jeśli jako wartość tej właściwości ustawiono 1, określa ona, że klient powinien wybrać certyfikat PKI o najdłuższym okresie ważności. To ustawienie może być wymagane, jeśli używasz ochrony dostępu do sieci z wymuszaniem IPsec.  

 Przykład: `CCMSetup.exe /UsePKICert CCMFIRSTCERT=1`  


### <a name="ccmhostname"></a>CCMHOSTNAME

 Jeśli klient jest zarządzany przez internet, ta właściwość określa nazwę FQDN punktu zarządzania internetowego.  

 Nie określać tej opcji wraz z właściwością instalacyjną SMSSITECODE = AUTO. Klienci internetowi muszą przypisanej bezpośrednio do swojej witryny internetowych.  

 Przykład: `CCMSetup.exe  /UsePKICert CCMHOSTNAME="SMSMP01.corp.contoso.com"`  

Tej właściwości można określić adres bramy zarządzania chmury. Aby uzyskać wartość dla tej właściwości, wykonaj następujące kroki:
- Utwórz bramę zarządzania chmury.
- Na aktywnego klienta otwórz wiersz polecenia programu Windows PowerShell jako administrator. 
- Uruchom następujące polecenie: `(Get-WmiObject -Namespace Root\Ccm\LocationServices -Class SMS_ActiveMPCandidate | Where-Object {$_.Type -eq "Internet"}).MP`
- Użyj wartości zwracane jako — z **CCMHOSTNAME** właściwości.

Na przykład: `ccmsetup.exe CCMHOSTNAME=CONTOSO.CLOUDAPP.NET/CCM_Proxy_MutualAuth/72057598037248100`

 > [!Important]
 > Podczas określania adresu bramy zarządzania chmury dla **CCMHOSTNAME** właściwości, czy *nie* takich jak dołączanie prefiks **https://**. Ten prefiks jest używany tylko z **/mp** adres URL zarządzania bramy chmury.



### <a name="ccmhttpport"></a>CCMHTTPPORT

 Określa port, którego powinien używać klient do komunikacji przy użyciu protokołu HTTP z serwerami systemu lokacji. Domyślnie z portu 80.  

 Przykład: `CCMSetup.exe CCMHTTPPORT=80`  

### <a name="ccmhttpsport"></a>CCMHTTPSPORT

Określa port, którego powinien używać klient do komunikacji przy użyciu protokołu HTTPS z serwerami systemu lokacji. Domyślnie jest ustawiony Port 443.  

Przykład: `CCMSetup.exe /UsePKICert CCMHTTPSPORT=443`  

### <a name="ccminstalldir"></a>CCMINSTALLDIR

 Identyfikuje folder, w którym są zainstalowane pliki klienta programu Configuration Manager, *% Windir %* \CCM domyślnie. Niezależnie od tego, w którym są zainstalowane te pliki, plik Ccmcore.dll będzie zawsze instalowany w *%Windir%\System32* folderu. Ponadto na 64-bitowego systemu operacyjnego, kopia pliku Ccmcore.dll będzie zawsze instalowany w *% Windir %* \SysWOW64 folderu. Ten plik obsługuje 32-bitowych aplikacji, korzystających z 32-bitowej wersji klienta interfejsy API z usługi SDK programu Configuration Manager.  

 Przykład: `CCMSetup.exe CCMINSTALLDIR="C:\ConfigMgr"`  

### <a name="ccmloglevel"></a>CCMLOGLEVEL

Określa poziom szczegółów zapisywanych w plikach dziennika programu Configuration Manager. Określ liczbą całkowitą z zakresu od 0 do 3, gdzie 0 oznacza rejestrowanie najpełniejszych i 3 oznacza rejestrowanie wyłącznie błędów. Domyślnym ustawieniem jest 1.  

Przykład: `CCMSetup.exe CCMLOGLEVEL=3`  

### <a name="ccmlogmaxhistory"></a>CCMLOGMAXHISTORY

Gdy plik dziennika programu Configuration Manager osiągnie maksymalny rozmiar, klient zmienia jego nazwę na nazwę kopii zapasowej i tworzy nowy plik dziennika. Maksymalny rozmiar to 250 000 bajtów domyślnie oraz wartości określonej we właściwości CCMMAXLOGSIZE.

Ta właściwość określa, ile poprzednich wersji pliku dziennika do zachowania. Wartość domyślna to 1. W przypadku wybrania wartości 0 nie będą przechowywane żadne stare pliki dziennika.  

Przykład: `CCMSetup.exe CCMLOGMAXHISTORY=0`  

### <a name="ccmlogmaxsize"></a>CCMLOGMAXSIZE

Maksymalny rozmiar pliku dziennika w bajtach. Gdy plik dziennika osiągnie określony rozmiar, klient zmienia jego nazwę, jako plik historyczny i tworzy nowy plik. Tej właściwości musi być równa co najmniej 10 000 bajtów. Wartość domyślna to 250 000 bajtów.  

Przykład: `CCMSetup.exe CCMLOGMAXSIZE=300000`  

### <a name="disablesiteopt"></a>DISABLESITEOPT

 Jeśli ustawiono wartość TRUE, ta właściwość wyłącza administracyjne użytkownikom zmianę przypisanej lokacji w **programu Configuration Manager** Panelu sterowania.  

 Przykład: **CCMSetup.exe DISABLESITEOPT = TRUE**  

### <a name="disablecacheopt"></a>DISABLECACHEOPT

Jeśli ustawiono wartość TRUE, ta właściwość wyłącza administracyjne użytkownikom zmianę ustawień folderu pamięci podręcznej klienta w **programu Configuration Manager** Panelu sterowania.  

Przykład: `CCMSetup.exe DISABLECACHEOPT=TRUE`  

### <a name="dnssuffix"></a>DNSSUFFIX

 Określa domenę DNS dla klientów umożliwiającą lokalizowanie punktów zarządzania publikowanych w systemie DNS. Po zlokalizowaniu punktu zarządzania klient jest informowany o innych punktach zarządzania w hierarchii. To zachowanie oznacza, że punkt zarządzania, który znajduje się przy użyciu publikowania DNS nie musi znajdować się w lokacji klienta, ale może być dowolnym punktem zarządzania w hierarchii.  

> [!NOTE]  
>  Nie trzeba określić tę właściwość, jeśli klient znajduje się w tej samej domenie co opublikowany punkt zarządzania. W takim przypadku domeny klienta automatycznie służy do wyszukiwania DNS dla punktów zarządzania.  

 Aby uzyskać więcej informacji o funkcji publikowania DNS jako metody lokalizacji usługi dla klientów programu Configuration Manager, zobacz [usługi lokalizacji oraz sposoby określania przypisanego punktu zarządzania przez klientów](../../plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md#BKMK_Plan_Service_Location).  

> [!NOTE]  
>  Domyślnie publikowania DNS nie jest włączona w programie Configuration Manager.  

 Przykład: `CCMSetup.exe SMSSITECODE=ABC DNSSUFFIX=contoso.com`  

### <a name="fsp"></a>FSP

Określa rezerwowy punkt stanu odbierający i przetwarzający komunikaty o stanie wysyłane przez komputery klienckie programu Configuration Manager.  

Aby uzyskać więcej informacji na temat rezerwowego punktu stanu, zobacz [stwierdzić, czy wymagane rezerwowy punkt stanu](/sccm/core/clients/deploy/plan/determine-the-site-system-roles-for-clients#determine-if-you-need-a-fallback-status-point).  

Przykład: `CCMSetup.exe FSP=SMSFP01`  

### <a name="ignoreappvversioncheck"></a>IGNOREAPPVVERSIONCHECK

 Określa, że obecność minimalnej wymaganej wersji oprogramowania Microsoft Application Virtualization (App-V) nie jest zaznaczone, przed zainstalowaniem klienta.  

> [!IMPORTANT]  
>  Po zainstalowaniu klienta programu Configuration Manager bez zainstalowania programu App-V, nie można wdrażać aplikacje wirtualne.  

 Przykład: `CCMSetup.exe IGNOREAPPVVERSIONCHECK=TRUE`  

### <a name="notifyonly"></a>NOTIFYONLY

Określa stanu klienta, ale nie Korygowanie problemów, które znajdzie.  

Przykład: `CCMSetup.exe NOTIFYONLY=TRUE`  

Aby uzyskać więcej informacji, zobacz [jak skonfigurować stan klienta](configure-client-status.md).  

### <a name="resetkeyinformation"></a>RESETKEYINFORMATION

 Jeśli klient ma nieprawidłowy klucz zaufanych certyfikatów głównych programu Configuration Manager i nie można skontaktować się z zaufanym punktem zarządzania do odbierania nowego zaufanego klucza głównego, używają tej właściwości, aby ręcznie usunąć stary zaufany klucz główny. Ta sytuacja może wystąpić w przypadku przeniesienia klienta z hierarchii jednej lokacji do innej. Ta właściwość dotyczy klientów komunikujących się za pośrednictwem protokołów HTTP i HTTPS.  

 Przykład: `CCMSetup.exe RESETKEYINFORMATION=TRUE`  

### <a name="sitereassign"></a>SITEREASSIGN

Umożliwia ponowne przypisanie lokacji automatycznych uaktualnień klienta w przypadku użycia z [SMSSITECODE](#smssitecode)= AUTO.

Przykład: `CCMSetup.exe SMSSITECODE=AUTO SITEREASSIGN=TRUE`

### <a name="smscachedir"></a>SMSCACHEDIR

Określa lokalizację folderu pamięci podręcznej klienta na komputerze klienckim, służącym do przechowywania plików tymczasowych. Domyślna lokalizacja to *%Windir%\ccmcache*.  

Przykład: `CCMSetup.exe SMSCACHEDIR="C:\Temp"`  

Tej właściwości można w połączeniu z właściwością SMSCACHEFLAGS, aby kontrolować lokalizację folderu pamięci podręcznej klienta.  

Przykład: `CCMSetup.exe SMSCACHEDIR=Cache SMSCACHEFLAGS=MAXDRIVE` instaluje folder pamięci podręcznej klienta na największym dysku dostępne klienta.  

### <a name="smscacheflags"></a>SMSCACHEFLAGS

Określa dodatkowe szczegóły instalacji folderu pamięci podręcznej klienta. Właściwości SMSCACHEFLAGS można używać osobno lub razem, oddzielonych średnikami. Jeśli ta właściwość nie jest określona, folder pamięci podręcznej klienta jest zainstalowana zgodnie z właściwością SMSCACHEDIR, nie jest skompresowany folder i wartość właściwości SMSCACHESIZE jest używany jako rozmiar w MB folderu.  

To ustawienie zostanie zignorowane w przypadku uaktualniania istniejącego klienta.  

Właściwości:  

-   PERCENTDISKSPACE: Określa rozmiar folderu jako procent całkowitej ilości miejsca. W przypadku określenia tej właściwości należy określić również właściwość SMSCACHESIZE oznaczającą, że ma być używana wartość procentowa.  

-   PERCENTFREEDISKSPACE: Określa rozmiar folderu jako procent wolnego miejsca na dysku. W przypadku określenia tej właściwości należy określić również właściwość SMSCACHESIZE oznaczającą, że ma być używana wartość procentowa. Jeśli na przykład na dysku znajduje się 10 MB wolnego miejsca, a wartość właściwości SMSCACHESIZE wynosi 50, rozmiar folderu będzie wynosił 5 MB. Nie można używać tej właściwości wraz z właściwością PERCENTDISKSPACE.  

-   MAXDRIVE: Określa, że folder zostanie zainstalowany na największym dostępnym dysku. Ta wartość jest ignorowana, jeśli ścieżka została określona przy użyciu właściwości SMSCACHEDIR.  

-   MAXDRIVESPACE: Określa, że folder zostanie zainstalowany na dysk o największej ilości wolnego miejsca. Ta wartość jest ignorowana, jeśli ścieżka została określona przy użyciu właściwości SMSCACHEDIR.  

-   NTFSONLY: Określa, że folder może być zainstalowany wyłącznie na dyskach systemu plików NTFS. Ta wartość jest ignorowana, jeśli ścieżka została określona przy użyciu właściwości SMSCACHEDIR.  

-   COMPRESS: Określa, że folder powinien być przechowywany w postaci skompresowanej.  

-   FAILIFNOSPACE: Określa, że należy usunąć oprogramowanie klienta, jeśli brak miejsca na zainstalowanie folderu.  

Przykład: `CCMSetup.exe SMSCACHEFLAGS=NTFSONLY;COMPRESS`  


### <a name="smscachesize"></a>SMSCACHESIZE

> [!IMPORTANT]
> Ustawienia klienta są dostępne do określania rozmiar folderu pamięci podręcznej klienta. Dodane ustawienia klienta skutecznie zastępują użycie właściwości SMSCACHESIZE jako właściwości pliku client.msi służącej do określania rozmiaru pamięci podręcznej klienta. Aby uzyskać więcej informacji, zobacz [ustawienia klienta dla rozmiaru pamięci podręcznej](about-client-settings.md#client-cache-settings).  

<!-- For 1602 and earlier, SMSCACHESIZE specifies the size of the client cache folder in megabyte (MB) or as a percentage when used with the PERCENTDISKSPACE or PERCENTFREEDISKSPACE property. If this property isn't set, the folder defaults to a maximum size of 5120 MB. The lowest value that you can specify is 1 MB.  -->

> [!NOTE]  
>  Jeśli nowy pakiet, który musi zostać pobrana spowodowałoby przekroczenie maksymalnego rozmiaru i nie można przeczyścić folderu, aby udostępnić wystarczającą ilość miejsca, pobranie pakietu zakończy się niepowodzeniem, a program lub aplikacja nie działa.  

To ustawienie jest ignorowane podczas uaktualniania istniejącego klienta i klient pobierze aktualizacje oprogramowania.  

Przykład: `CCMSetup.exe SMSCACHESIZE=100`  

> [!NOTE]  
>  W przypadku ponownej instalacji klienta, nie można użyć właściwości instalacji SMSCACHESIZE lub SMSCACHEFLAGS można ustawić rozmiar pamięci podręcznej może być mniejszy niż miało poprzednio. Jeśli spróbujesz wykonaj tę akcję, wartość jest ignorowana. Rozmiar pamięci podręcznej wynosi automatycznie poprzedniego rozmiaru.  

### <a name="smsconfigsource"></a>SMSCONFIGSOURCE

Określa lokalizację i kolejność kontroli ustawień konfiguracji przeprowadzanych Instalatora programu Configuration Manager. Właściwość jest ciągiem o co najmniej jeden znak definiujący określone źródło konfiguracji. Użyj wartości znaków R, P, M oraz U, pojedynczo lub w połączeniu:  

-   R: Sprawdź, czy ustawienia konfiguracji w rejestrze.  

   Aby uzyskać więcej informacji, zobacz [informacji na temat zapisywania właściwości instalacji klienta w rejestrze](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_Provision).  

-   P: Sprawdzenie ustawień konfiguracji we właściwościach instalacji podawanych w wierszu polecenia.  

-   M: Sprawdzenie istniejących ustawień podczas uaktualniania starszego klienta przy użyciu oprogramowania klienckiego programu Configuration Manager.  

-   U: Uaktualnienie zainstalowanego klienta do nowszej wersji (oraz użycie kodu przypisanej lokacji).  

 Domyślnie instalacja klienta używa ciągu `PU` w celu sprawdzenia właściwości instalacji, a następnie istniejących ustawień.  

 Przykład: `CCMSetup.exe SMSCONFIGSOURCE=RP`  

### <a name="smsdirectorylookup"></a>SMSDIRECTORYLOOKUP

 Określa, czy klient może używać usługi nazw internetowych systemu Windows (WINS) do znalezienia punktu zarządzania przyjmującego połączenia przy użyciu protokołu HTTP. Klienci używają tej metody, gdy nie może znaleźć punktu zarządzania, w usługach domenowych w usłudze Active Directory lub w systemie DNS.  

 Ta właściwość nie ma wpływu na, czy klient używa usługi WINS do rozpoznawania nazw.  

 Można skonfigurować dwa różne tryby tej właściwości:  

-   NOWINS: Ta wartość jest to najbezpieczniejsze ustawienie tej właściwości i uniemożliwia klientom znalezienie punktu zarządzania w usłudze WINS. W przypadku zastosowania tego ustawienia klienci muszą dysponować alternatywną metodą lokalizowania punktu zarządzania w intranecie, na przykład przy użyciu usług domenowych w usłudze Active Directory lub funkcji publikowania DNS.  

-   WINSSECURE (ustawienie domyślne): W tym trybie klient używający protokołu HTTP do komunikacji może używać usługi WINS do znajdowania punktu zarządzania. Aby jednak klient mógł pomyślnie nawiązać połączenie z punktem zarządzania, musi mieć kopię zaufanego klucza głównego. Aby uzyskać więcej informacji, zobacz [planowanie zaufanego klucza głównego](../../plan-design/security/plan-for-security.md#BKMK_PlanningForRTK).  


 Przykład: `CCMSetup.exe SMSDIRECTORYLOOKUP=NOWINS`  

### <a name="smsmp"></a>SMSMP

Określa wstępny punkt zarządzania dla klienta programu Configuration Manager do użycia.  

> [!IMPORTANT]  
>  Jeśli punkt zarządzania akceptuje tylko połączenia klienta za pośrednictwem protokołu HTTPS, należy prefiks nazwy punktu zarządzania z https://.  

Przykład: `CCMSetup.exe SMSMP=smsmp01.contoso.com`

Przykład: `CCMSetup.exe SMSMP=https://smsmp01.contoso.com`  


### <a name="smspublicrootkey"></a>SMSPUBLICROOTKEY

 Określa programu Configuration Manager zaufanego klucza głównego, gdy nie można pobrać z usług domenowych w usłudze Active Directory. Ta właściwość dotyczy klientów komunikujących się za pośrednictwem protokołów HTTP i HTTPS. Aby uzyskać więcej informacji, zobacz [planowanie zaufanego klucza głównego](../../plan-design/security/plan-for-security.md#BKMK_PlanningForRTK).  

 Przykład: `CCMSetup.exe SMSPUBLICROOTKEY=&lt;key\>`  

### <a name="smsrootkeypath"></a>SMSROOTKEYPATH

 Służy do ponownego zainstalowania zaufanego klucza głównego programu Configuration Manager. Określa pełną ścieżkę i nazwę pliku zawierającego zaufany klucz główny. Ta właściwość dotyczy klientów komunikujących się za pośrednictwem protokołów HTTP i HTTPS. Aby uzyskać więcej informacji, zobacz [planowanie zaufanego klucza głównego](../../plan-design/security/plan-for-security.md#BKMK_PlanningForRTK).  

 Przykład: "CCMSetup.exe SMSROOTKEYPATH =&lt;Pełna ścieżka i nazwa pliku\>`  

### <a name="smssigncert"></a>SMSSIGNCERT

 Określa pełną ścieżkę i nazwę pliku .cer wyeksportowanego certyfikatu z podpisem własnym na serwerze lokacji.  

 Ten certyfikat jest przechowywany w magazynie certyfikatów **SMS** i ma przypisane nazwę podmiotu **Serwer lokacji** oraz przyjazną nazwę **Certyfikat podpisywania serwera lokacji**.  

 Przykład: **CCMSetup.exe/UsePKICert SMSSIGNCERT =&lt;Pełna ścieżka i nazwa pliku\>**  

### <a name="smssitecode"></a>SMSSITECODE

 Określa lokację programu Configuration Manager można przypisać klientowi. Ta wartość może być kod trzyliterowy lokacji lub słowo AUTO. Jeśli Określ AUTO lub nieokreślenia tej właściwości klient spróbuje określić przypisania lokacji z usług domenowych w usłudze Active Directory lub z określonego punktu zarządzania. Aby włączyć automatyczne dla uaktualnienia klienta, należy także ustawić [SITEREASSIGN](#sitereassign) na wartość TRUE.    

> [!NOTE]  
>  Nie należy używać automatycznego, jeśli określisz punkt internetowego zarządzania (CCMHOSTNAME). W takim przypadku należy bezpośrednio przypisać klienta do lokacji.  

 Przykład: `CCMSetup.exe SMSSITECODE=XZY`  

##  <a name="BKMK_attributevalues"></a> Wartości atrybutów obsługiwanych kryteriów wyboru certyfikatów PKI  
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
