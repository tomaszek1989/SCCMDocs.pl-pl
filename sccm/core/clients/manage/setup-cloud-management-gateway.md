---
title: "Konfigurowanie bramy zarządzania chmury | Dokumentacja firmy Microsoft"
description: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/01/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-client
ms.assetid: e0ec7d66-1502-4b31-85bb-94996b1bc66f
ms.translationtype: Machine Translation
ms.sourcegitcommit: d5a6fdc9a526c4fc3a9027dcedf1dd66a6fff5a7
ms.openlocfilehash: 97e1bc6585cee0ff433da0ec0b60b9604cb7348f
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---

# <a name="set-up-cloud-management-gateway-for-configuration-manager"></a>Konfigurowanie bramy zarządzania chmury dla programu Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Począwszy od wersji 1610, proces konfigurowania bramy zarządzania chmury w programie Configuration Manager obejmuje następujące kroki:

## <a name="step-1-configure-required-certificates"></a>Krok 1: Skonfiguruj wymagane certyfikaty

## <a name="option-1-preferred---use-the-server-authentication-certificate-from-a-public-and-globally-trusted-certificate-provider-like-verisign"></a>Opcja 1 (preferowane) — Użyj certyfikatu uwierzytelniania serwera od dostawcy publicznych i globalny zaufanego certyfikatu (na przykład VeriSign)

Korzystając z tej metody, klienci będą automatycznie ufać certyfikatowi i nie trzeba samodzielnie utworzyć niestandardowego certyfikatu SSL.

1. Utwórz rekord nazwy kanonicznej (CNAME) w organizacji publiczną nazwę usługi (DNS), aby utworzyć alias usługi w chmurze zarządzania bramą do przyjaznej nazwy, które będzie używane w certyfikacie publicznych.
Na przykład Contoso nazwy usługi bramy zarządzania ich chmury **GraniteFalls** w Azure będzie **GraniteFalls.CloudApp.Net**. W firmy Contoso publicznego contoso.com obszar nazw DNS, DNS administrator tworzy nowy rekord CNAME dla **GraniteFalls.Contoso.com** dla nazwy hosta prawdziwe **GraniteFalls.CloudApp.net**.
2. Ponownie zażądać certyfikatu uwierzytelniania serwera od publicznego dostawcy przy użyciu typowych nazwa (CN) z aliasu CNAME.
Na przykład Contoso używa **GraniteFalls.Contoso.com** dla nazwa Pospolita certyfikatu.
3. Utwórz usługę bramy zarządzania chmury w konsoli programu Configuration Manager przy użyciu tego certyfikatu.
    - Na **ustawienia** strony Kreator tworzenia chmury zarządzania bramą podczas dodawania certyfikatu serwera dla tej usługi w chmurze (z **plik certyfikatu**), Kreator wyodrębniania nazwy hosta z certyfikatu CN nazwy usługi, a następnie dołącz do **cloudapp.net** (lub **usgovcloudapp.net** chmury Azure rządową USA) jako nazwa FQDN usługi, aby utworzyć usługę w systemie Azure.
Na przykład podczas tworzenia na Contoso, nazwa hosta bramy zarządzania chmury **GraniteFalls** są wyodrębniane z certyfikatu CN, tak aby rzeczywiste usługi w usłudze Azure zostanie utworzona jako **GraniteFalls.CloudApp.net**.

### <a name="option-2---create-a-custom-ssl-certificate-for-cloud-management-gateway-in-the-same-way-as-for-a-cloud-based-distribution-point"></a>Opcja 2 — Tworzenie niestandardowego certyfikatu SSL dla chmury zarządzania bramą w taki sam sposób jak w przypadku punktu dystrybucji w chmurze

Można tworzyć niestandardowe certyfikat SSL dla chmury zarządzania bramą w taki sam sposób, który należy do punktu dystrybucji w chmurze. Postępuj zgodnie z instrukcjami dotyczącymi [wdrażanie certyfikatu usługi dla chmurowych punktów dystrybucji](/sccm/core/plan-design/network/example-deployment-of-pki-certificates) , ale inaczej wykonać następujące czynności:

- Podczas konfigurowania nowego szablonu certyfikatu, nadaj ** odczytu ** i **rejestracja** uprawnień do grupy zabezpieczeń, którą można skonfigurować dla serwerów programu Configuration Manager.
- Podczas żądania certyfikatu serwera sieci web niestandardowe, podaj nazwę FQDN dla nazwa pospolita certyfikatu, który kończy się na **cloudapp.net** dla przy użyciu bramy zarządzania chmury w chmurze publicznej systemu Azure lub **usgovcloudapp.net** chmury Azure instytucji rządowych.


## <a name="step-2-export-the-client-certificates-root"></a>Krok 2: Eksportuj głównego certyfikatu klienta

Najprostszym sposobem uzyskać eksportu głównych certyfikatów klientów w sieci, należy otworzyć certyfikat klienta na jednym maszyn przyłączonych do domeny, które ma jeden i skopiuj go.

> [!NOTE] 
>
> Certyfikaty klienta są wymagane na każdym komputerze, które mają być zarządzane za pomocą bramy zarządzania w chmurze i na serwerze systemu lokacji łącznika bramy zarządzania chmury hosting punktu. Jeśli zachodzi konieczność dodania certyfikat klienta do dowolnej z tych urządzeń, zobacz [wdrażanie certyfikatów dla systemu Windows komputery klienckie](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_client2008_cm2012).

1.  W oknie Uruchamianie wpisz **mmc** i naciśnij klawisz Return.

2.  Z menu Plik wybierz **Dodaj/Usuń przystawkę...** .

3.  W oknie dialogowym Dodawanie lub usuwanie przystawek wybierz **certyfikaty** > **Dodaj &gt;**   >  **konto komputera** > **dalej** > **komputera lokalnego** > **Zakończ**. 

4.  Przejdź do **certyfikaty** &gt; **osobiste** &gt; **certyfikaty**.

5.  Kliknij dwukrotnie certyfikat uwierzytelniania klienta na komputerze, wybierz kartę ścieżki certyfikacji, a następnie kliknij dwukrotnie główny urząd certyfikacji (w górnej części ścieżki).

6.  Na karcie Szczegóły, wybierz **kopii do pliku...** .

7.  Ukończ Kreatora eksportu certyfikatów przy użyciu domyślnego formatu certyfikatu. Upewnij się, zanotuj nazwę i lokalizację utworzony certyfikat główny. Konieczne będzie skonfigurowanie bramy zarządzania chmury w [później krok](#step-4-set-up-cloud-management-gateway).

## <a name="step-3-upload-the-management-certificate-to-azure"></a>Krok 3: Przekaż certyfikat zarządzania Azure

Certyfikat zarządzania Azure jest wymagany dla programu Configuration Manager do dostępu do interfejsu API Azure i skonfigurować bramę zarządzania chmury. Więcej informacji oraz instrukcje dotyczące sposobu przekazać certyfikat zarządzania zobacz następujące artykuły w dokumentacji platformy Azure:

- [Omówienie certyfikatów dla usług w chmurze Azure](https://azure.microsoft.com/documentation/articles/cloud-services-certs-create/)

- [Prześlij certyfikat zarządzania interfejsem API zarządzania Azure](https://azure.microsoft.com/documentation/articles/azure-api-management-certs/)

>[!IMPORTANT]
>Upewnij się skopiować identyfikator subskrypcji skojarzonego z certyfikatem zarządzania. Należy do konfiguracji bramy zarządzania chmury w konsoli programu Configuration Manager w [następnego kroku](#step-4-set-up-cloud-management-gateway).

### <a name="subordinate-ca-certificates-and-azure"></a>Podrzędnych urzędów certyfikacji i certyfikaty Azure

Jeśli certyfikat jest wystawiony przez podrzędny urząd certyfikacji (subCA) i infrastrukturę PKI przedsiębiorstwa nie jest połączony z Internetem, użyj tej procedury, aby przekazać certyfikat Azure. 

1. W portalu Azure, po skonfigurowaniu bramy zarządzania chmury, znajdź usługę bramy zarządzania w chmurze i przejdź do **certyfikatu** kartę. Przekaż swoje certyfikaty subCA istnieje. Jeśli masz więcej niż jeden certyfikat subCA, należy przekazać je wszystkie. 
2. Po przesłaniu certyfikatu, zapisz jego odcisku palca. 
3. Dodaj odcisk palca do bazy danych lokacji za pomocą tego skryptu:
    
```

    DIM serviceCName
    DIM subCAThumbprints

    ' Verify arguments
    IF WScript.Arguments.Count <> 2 THEN
    WScript.StdOut.WriteLine "Usage: CScript UpdateSubCAThumbprints.vbs <ServiceCName> <SubCA cert thumbprints, separated by ;>"
    WScript.Quit 1
    END IF

    'Get arguments
    serviceCName = WScript.Arguments.Item(0)
    subCAThumbprints = WScript.Arguments.Item(1)

    'Find SMS Provider
    WScript.StdOut.WriteLine "Searching for SMS Provider for local site..."
    SET objSMSNamespace = GetObject("winmgmts:{impersonationLevel=impersonate}!\\.\root\sms")
    SET results = objSMSNamespace.ExecQuery("SELECT * From SMS_ProviderLocation WHERE ProviderForLocalSite = true")

    'Process the results
    FOR EACH var in results
    siteCode = var.SiteCode
    NEXT

    IF siteCode = "" THEN
    WScript.StdOut.WriteLine "Failed to locate SMS provider."
    WScript.Quit 1
    END IF

    WScript.StdOut.WriteLine "SiteCode = " & siteCode 

    ' Connect to the SMS namespace
    SET objWMIService = GetObject("winmgmts:{impersonationLevel=impersonate}!\\.\root\sms\site_" & siteCode)

    'Get instance of SMS_AzureService
    DIM query
    query = "SELECT * From SMS_AzureService WHERE ServiceType = 'CloudProxyService' AND ServiceCName = '" & serviceCName & "'"
    WScript.StdOut.WriteLine "Run WQL query: " &  query
    SET objInstances = objWMIService.ExecQuery(query)

    IF IsNull(objInstances) OR (objInstances.Count = 0) THEN
    WScript.StdOut.WriteLine "Failed to get Azure_Service instance."
    WScript.Quit 1
    END IF

    FOR EACH var IN objInstances
    SET azService = var
    NEXT

    WScript.StdOut.WriteLine "Update [SubCACertThumbprint] to " & subCAThumbprints

    'Update SubCA cert thumbprints
    azService.Properties_.item("SubCACertThumbprint") = subCAThumbprints

    'Save data back to provider
    azService.Put_

    WScript.StdOut.WriteLine "[SubCACertThumbprint] is updated successfully."
```


## <a name="step-4-set-up-cloud-management-gateway"></a>Krok 4: Konfigurowanie chmury zarządzania bramą

>[!NOTE]
>W wersji 1610 chmury zarządzania bramą jest funkcją wersji wstępnej. Aby ją włączyć, zobacz [używać funkcji wersji wstępnej z aktualizacji](/sccm/core/servers/manage/install-in-console-updates#bkmk_prerelease).

1. W konsoli programu Configuration Manager, przejdź do **Administracja** > **usług w chmurze** > **brama zarządzania chmury**.
2. Wybierz **utworzyć bramę zarządzania chmury**.

3. W kreatorze tworzenia chmury zarządzania bramy, wprowadź identyfikator subskrypcji platformy Azure (skopiowany z portalu zarządzania Azure) i przejdź do pliku certyfikatu służącego do przesyłania jako certyfikat zarządzania Azure. Wybierz **dalej** i poczekaj kilka chwil konsoli nawiązać Azure.

4. Wypełnianie dodatkowych szczegółów w Kreatorze:

    - Określ nazwę usługi, która działa w systemie Azure. Nazwa usługi musi zawierać tylko znaki alfanumeryczne i 3 do 24 znaków.

    - Wybierz region platformy Azure, chcesz, aby usługa działała.

    - Określ liczbę maszyn wirtualnych, które mają być używane dla usługi. Wartość domyślna to 1, ale może uruchamiać maksymalnie 16 maszyn wirtualnych do usługi.

    >[!NOTE]
    >Jeśli używasz serwera proxy programu internet punktu połączenia chmury zarządzania bramą, należy zwiększyć liczbę portów na serwerze proxy przez liczbę maszyn wirtualnych, którego używasz, zaczynając od portu 10124.

    - Określ klucz prywatny (plik pfx) wyeksportowany z niestandardowego certyfikatu SSL.

    - Określ certyfikat główny wyeksportowane za pomocą certyfikatu klienta.

    -   Określ usługi o tej samej nazwie FQDN, którego użyto podczas tworzenia nowego szablonu certyfikatu. Należy określić jeden następujące sufiksów dla nazwy FQDN usługi na podstawie w chmurze Azure, której używasz:

    Chmura Azure | Prefiks nazwy FQDN
    --------------|-------------
    Chmura publiczna (komercyjnych) | . cloudapp.net    
    Chmura instytucji rządowych | . usgovcloudapp.net

  - Usuń zaznaczenie pola obok **odwołania certyfikatu klienta sprawdź** (chyba że publicznie podczas publikowania informacji listy CRL).

  - Wybierz **dalej** po zakończeniu.

5. Jeśli chcesz monitorować ruch w chmurze zarządzania bramy z progiem 14 dni, wybierz pole wyboru, aby włączyć próg alertu. Następnie określ próg i procent jaką pozyskiwania różnych poziomów alertów. Wybierz **dalej** po zakończeniu.

6. Przejrzyj ustawienia, a następnie wybierz **dalej**. Konfigurowanie usługi uruchamiania Menedżera konfiguracji. Po zamknięciu kreatora zajmie od 5 do 15 minut do udostępniania usług całkowicie w systemie Azure. Sprawdź **stanu** kolumny dla nowo ustawienia zarządzania brama chmury do określenia, kiedy usługa jest gotowa.

## <a name="step-5-configure-primary-site-for-client-certification-authentication"></a>Krok 5. Konfigurowanie lokacji głównej do uwierzytelniania klientów certyfikacji

1. W konsoli programu Configuration Manager, przejdź do **Administracja** > **konfiguracja lokacji** > **witryny**.

2. Wybierz lokację główną dla klientów, aby zarządzać za pośrednictwem bramy zarządzania chmury, a następnie wybierz **właściwości**.

3. Na karcie Komunikacja komputera klienta w arkuszu właściwości lokacji głównej Sprawdź **Użyj certyfikatu klienta PKI (uwierzytelnianie klienta) po ich udostępnieniu**.

4. Upewnij się wyczyścić **klientów sprawdzania listy odwołania certyfikatów (CRL) dla systemów lokacji**. Tę opcję tylko byłoby wymagane zostały publicznie publikowania Twojej listy CRL.


## <a name="step-6-add-the-cloud-management-gateway-connector-point"></a>Krok 6: Dodaj punkt łącznika chmury zarządzania bramą

Punkt łącznika chmury zarządzania bramą jest nowa rola systemu lokacji do komunikowania się z bramą zarządzania chmury. Aby dodać punkt łącznika chmury zarządzania bramą, postępuj zgodnie z instrukcjami [Dodaj role systemu lokacji dla programu System Center Configuration Manager](/sccm/core/servers/deploy/configure/add-site-system-roles).

## <a name="step-7-configure-roles-for-cloud-management-gateway-traffic"></a>Krok 7: Konfigurowanie ról dla ruchu w chmurze zarządzania bramą

Ostatnim krokiem w konfiguracji bramy zarządzania chmury jest skonfigurowanie ról systemu lokacji do akceptowania ruchu w chmurze zarządzania bramą. Dla Tech 1606 Podgląd tylko punktu zarządzania, punktu dystrybucji i roli punktu aktualizacji oprogramowania są obsługiwane dla chmury zarządzania bramą. Każda rola należy skonfigurować oddzielnie.

1. W konsoli programu Configuration Manager, przejdź do **Administracja** > **konfiguracja lokacji** > **serwery i role systemu lokacji**.

2. Wybierz serwer systemu lokacji dla roli, który chcesz skonfigurować, czy ruch w chmurze zarządzania bramą.

3. Wybierz rolę, a następnie wybierz **właściwości**.

4. W arkuszu właściwości ról w ramach połączeń klientów, wybierz **HTTPS**, zaznacz pole wyboru obok pozycji **programu Configuration Manager umożliwia chmury zarządzania bramy ruchu**, a następnie wybierz **OK**. Powtórz te czynności dla pozostałych ról.

## <a name="step-8-configure-clients-for-cloud-management-gateway"></a>Krok 8. Skonfigurować klientów do chmury zarządzania bramą

Po zarządzania chmury bramy a role systemu lokacji są całkowicie skonfigurowane i uruchomione, klienci otrzymają lokalizacji usługi w chmurze zarządzania bramą automatycznie przy następnym żądaniu lokalizacji. Klienci muszą znajdować się w sieci firmowej do odbierania lokalizacji usługi w chmurze zarządzania bramą. Cykl sondowania żądań lokalizacji jest co 24 godziny. Jeśli nie chcesz czekać na żądanie lokalizacji zwykle zaplanowane, można wymusić żądania przez ponowne uruchomienie usługi hosta agenta programu SMS (ccmexec.exe) na komputerze.

Lokalizacja usługi bramy zarządzania w chmurze skonfigurowane na kliencie go automatycznie ustalić, czy jest on w intranecie lub w Internecie. Jeśli klient może skontaktować się z kontrolerem domeny lub lokalnego punktu zarządzania, wykorzysta go do komunikowania się z programem Configuration Manager, w przeciwnym razie go będzie uważają, że jest w Internecie i użyj lokalizacji brama zarządzania chmury usługi do komunikacji.

>[!NOTE]
> Można wymusić klient zawsze używaj bramy zarządzania chmury, niezależnie od tego, czy jest w sieci intranet lub Internetem. Aby to zrobić, ustaw następujący klucz rejestru na komputerze klienckim: \
>
> `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\CCM\Security, ClientAlwaysOnInternet = 1`

Aby sprawdzić, czy klienci mogą się kontaktować z programu Configuration Manager, można uruchomić następujące polecenie programu PowerShell na komputerze klienckim:

`gwmi -namespace root\ccm\locationservices -class SMS_ActiveMPCandidate`

To polecenie wyświetla punkty zarządzania, które klient może nawiązać kontakt z tym Usługa bramy zarządzania chmury.

## <a name="next-steps"></a>Następne kroki

[Monitorowanie klientów dla chmury zarządzania bramą](monitor-clients-cloud-management-gateway.md)

