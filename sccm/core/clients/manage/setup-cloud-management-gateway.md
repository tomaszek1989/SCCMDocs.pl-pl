---
title: "Skonfiguruj bramę zarządzania chmurze | Dokumentacja firmy Microsoft"
description: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 05/01/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology: configmgr-client
ms.assetid: e0ec7d66-1502-4b31-85bb-94996b1bc66f
ms.openlocfilehash: 84b617b3e83636ab4578174ef40e786dcf1178cd
ms.sourcegitcommit: 06aef618f72c700f8a716a43fb8eedf97c62a72b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2017
---
# <a name="set-up-cloud-management-gateway-for-configuration-manager"></a>Konfigurowanie bramy zarządzania w chmurze programu Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Począwszy od wersji 1610, proces konfigurowania bramy zarządzania w chmurze w programie Configuration Manager obejmuje następujące kroki:

## <a name="step-1-configure-required-certificates"></a>Krok 1. Skonfiguruj wymagane certyfikaty

> [!TIP]  
> Przed wysłaniem żądania certyfikatu, upewnij się, że nazwa żądanej domeny platformy Azure (na przykład GraniteFalls.CloudApp.Net) jest unikatowa. Aby zrobić to Zaloguj do [portalu Microsoft Azure](https://manage.windowsazure.com), kliknij przycisk **nowy**, wybierz pozycję **usługi w chmurze** , a następnie **Utwórz niestandardowy**. W **adres URL** nazwy domeny żądany typ pola (nie kliknij znacznik wyboru, aby utworzyć usługę). Portalu będzie odzwierciedlać czy nazwa domeny jest niedostępna lub jest już używany przez inną usługę.

## <a name="option-1-preferred---use-the-server-authentication-certificate-from-a-public-and-globally-trusted-certificate-provider-like-verisign"></a>Opcja 1 (preferowane) - używać certyfikatu uwierzytelniania serwera od dostawcy publicznego i globalnie zaufanego certyfikatu (na przykład VeriSign)

Korzystając z tej metody, klienci będą automatycznie ufać certyfikatowi i nie trzeba samodzielnie utworzyć niestandardowego certyfikatu SSL.

1. Utwórz rekord nazwę kanoniczną (CNAME) w Twojej organizacji w domenie publicznej nazwy service (DNS), aby utworzyć alias przyjazną nazwę, która będzie używana w usłudze bramy zarządzania chmury w certyfikatu publicznego.
Na przykład Contoso nazwy usługi bramy zarządzania ich chmury **GraniteFalls** który na platformie Azure będzie **GraniteFalls.CloudApp.Net**. W firmy Contoso publicznego contoso.com obszar nazw DNS, administrator usługi DNS tworzy nowy rekord CNAME dla **GraniteFalls.Contoso.com** dla nazwy hosta rzeczywistych **GraniteFalls.CloudApp.net**.
2. Ponownie zażądać certyfikatu uwierzytelniania serwera z publicznego dostawcę przy użyciu nazwa pospolita (CN) aliasu CNAME.
Na przykład firma Contoso używa **GraniteFalls.Contoso.com** CN certyfikatu.
3. Tworzenie usługi bramy zarządzania chmury w konsoli programu Configuration Manager przy użyciu tego certyfikatu.
    - Na **ustawienia** utworzyć chmury zarządzania bramy kreatora po dodaniu certyfikatu serwera dla tej usługi w chmurze (z **plik certyfikatu**), Kreator wyodrębniania nazwy hosta z certyfikatu CN nazwy usługi, a następnie dołącz do **cloudapp.net** (lub **usgovcloudapp.net** chmury Azure instytucji rządowych Stanów Zjednoczonych) jako nazwa FQDN usługi można utworzyć usługi na platformie Azure.
Na przykład podczas tworzenia bramy zarządzania chmury w firmie Contoso, nazwa hosta **GraniteFalls** jest wyodrębniana z certyfikatu CN, dzięki czemu rzeczywiste usługi na platformie Azure, zostanie utworzona jako **GraniteFalls.CloudApp.net**.

### <a name="option-2---create-a-custom-ssl-certificate-for-cloud-management-gateway-in-the-same-way-as-for-a-cloud-based-distribution-point"></a>Opcja 2 — Tworzenie niestandardowego certyfikatu SSL dla bramy zarządzania w chmurze w taki sam sposób jak w przypadku punktu dystrybucji w chmurze

W ten sam sposób, który należy do punktu dystrybucji w chmurze, można utworzyć niestandardowego certyfikatu SSL dla bramy zarządzania w chmurze. Postępuj zgodnie z instrukcjami dotyczącymi [wdrażanie certyfikatu usługi dla chmurowych punktów dystrybucji](/sccm/core/plan-design/network/example-deployment-of-pki-certificates) , ale inaczej wykonaj następujące czynności:

- Podczas żądania certyfikatu serwera sieci web niestandardowego, podaj nazwę FQDN dla nazwa pospolita certyfikatu, który kończy się **cloudapp.net** dotyczące korzystania z bramy zarządzania chmury w chmurze publicznej systemu Azure lub **usgovcloudapp.net** chmury Azure dla instytucji rządowych.


## <a name="step-2-export-the-client-certificates-root"></a>Krok 2. Eksportuj głównego certyfikatu klienta

Najprostszym sposobem pobrania eksportu głównego certyfikatów klientów w sieci, należy otworzyć certyfikat klienta na jednym maszyn przyłączonych do domeny, które ma jeden i skopiować go.

> [!NOTE] 
>
> Certyfikaty klienta są wymagane na każdym komputerze, który chcesz zarządzać za pomocą bramy zarządzania w chmurze i na serwerze systemu lokacji hostującym łącznika bramy zarządzania w chmurze punktu. Jeśli musisz dodać certyfikat klienta do dowolnego z tych urządzeń, zobacz [wdrażanie klienta certyfikatu na komputerach z systemem Windows](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_client2008_cm2012).

1.  W oknie Uruchamianie wpisz **mmc** i naciśnij klawisz Return.

2.  W menu Plik wybierz **Dodaj/Usuń przystawkę...** .

3.  W oknie dialogowym Dodawanie lub usuwanie przystawek wybierz **certyfikaty** > **Dodaj &gt;**   >  **konto komputera** > **dalej** > **komputera lokalnego** > **Zakończ**. 

4.  Przejdź do **certyfikaty** &gt; **osobistych** &gt; **certyfikaty**.

5.  Kliknij dwukrotnie certyfikat uwierzytelniania klienta na komputerze, wybierz kartę ścieżki certyfikacji, a następnie kliknij dwukrotnie głównego urzędu certyfikacji (w górnej części ścieżki).

6.  Na karcie Szczegóły wybierz **Kopiuj do pliku...** .

7.  Ukończ Kreatora eksportu certyfikatów przy użyciu domyślnego formatu certyfikatu. Upewnij się, zanotuj nazwę i lokalizację certyfikatu głównego, którą utworzysz. Będą potrzebne, aby skonfigurować bramę zarządzania chmury w [później krok](#step-4-set-up-cloud-management-gateway).

>[!NOTE]
>Jeśli certyfikat klienta został wystawiony przez urząd certyfikacji podrzędnego należy powtórzyć ten krok dla każdego certyfikatu w łańcuchu.

## <a name="step-3-upload-the-management-certificate-to-azure"></a>Krok 3. Przekaż certyfikat zarządzania na platformie Azure

Certyfikat zarządzania platformy Azure jest wymagany dla programu Configuration Manager dostępu do interfejsu API Azure i skonfigurować bramę zarządzania w chmurze. Aby uzyskać więcej informacji oraz instrukcje przekazać certyfikat zarządzania zobacz następujące artykuły w dokumentacji platformy Azure:

- [Omówienie certyfikatów dla usług w chmurze Azure](https://azure.microsoft.com/documentation/articles/cloud-services-certs-create/)

- [Przekaż certyfikat zarządzania interfejsem API zarządzania platformy Azure](https://azure.microsoft.com/documentation/articles/azure-api-management-certs/)

>[!IMPORTANT]
>Upewnij się skopiować identyfikator subskrypcji skojarzonych z certyfikatem zarządzania. Będzie potrzebny do konfigurowania bramy zarządzania chmury w konsoli programu Configuration Manager w [następnego kroku](#step-4-set-up-cloud-management-gateway).



## <a name="step-4-set-up-cloud-management-gateway"></a>Krok 4. Skonfiguruj bramę zarządzania w chmurze

>[!NOTE]
>W wersji 1610 brama zarządzania chmury jest to funkcja wersji wstępnej. Aby ją włączyć, zobacz [korzystanie z funkcji wersji wstępnej aktualizacje](/sccm/core/servers/manage/install-in-console-updates#bkmk_prerelease).

1. W konsoli programu Configuration Manager, przejdź do **administracji** > **usługi w chmurze** > **brama zarządzania chmury**.
2. Wybierz **Utwórz bramę zarządzania chmury**.

3. W chmurze Kreatora tworzenia zarządzania bramy, wprowadź identyfikator subskrypcji platformy Azure (skopiowany z portalu zarządzania platformy Azure), a następnie przejdź do pliku certyfikatu służącego do przesyłania jako certyfikat zarządzania platformy Azure. Wybierz **dalej** , a następnie poczekaj kilka chwil konsoli do nawiązania połączenia platformy Azure.

4. Wypełnianie dodatkowe szczegóły w Kreatorze:

    - Określ nazwę usługi, która działa na platformie Azure. Nazwa usługi musi zawierać tylko znaki alfanumeryczne i 3 do 24 znaków długości.

    - Wybierz region platformy Azure, usługa ma uruchomić w.

    - Określ liczbę maszyn wirtualnych, które ma być używany dla usługi. Wartość domyślna to 1, ale może uruchamiać maksymalnie 16 maszyn wirtualnych dla usługi.

    >[!NOTE]
    >Jeśli używasz internetowy serwer proxy punktu połączenia bramy zarządzania chmury, należy zwiększyć liczbę portów na serwerze proxy przez liczbę maszyn wirtualnych, których używasz, zaczynając od portu 10124.

    - Określ klucz prywatny (pfx) wyeksportowany z niestandardowego certyfikatu SSL.

    - Określ certyfikat główny (i wszystkich certyfikatów podrzędnych) wyeksportowany z certyfikatu klienta. Kreator akceptuje maksymalnie dwóch certyfikatów głównych i certyfikatów cztery podrzędnych.

    -   Określ taką samą nazwę usługi nazwy FQDN, która zostanie użyta podczas tworzenia nowego szablonu certyfikatu. Należy określić jedną z następujących sufiksy nazw dla nazwy FQDN nazwy usługi w chmurze platformy Azure, którego używasz w oparciu:

    Chmura Azure | Prefiks nazwy FQDN
    --------------|-------------
    Chmura publiczna (komercyjnych) | . cloudapp.net    
    Chmury dla instytucji rządowych | . usgovcloudapp.net

  - Usuń zaznaczenie pola obok **Sprawdź odwołania certyfikatu klienta** (o ile nie są publicznie publikowania danych listy CRL).

  - Wybierz **dalej** po zakończeniu.

5. Jeśli chcesz monitorować ruch bramy zarządzania chmury z progiem 14 dni, wybierz pole wyboru, aby włączyć alertu progu. Następnie należy określić próg i procent w którego zostanie wywołane na różnych poziomach alertów. Wybierz **dalej** po zakończeniu.

6. Przejrzyj ustawienia, a następnie wybierz pozycję **dalej**. Configuration Manager rozpoczyna się ustawienie usługi. Po zamknięciu kreatora potrwa od 5 do 15 minut do udostępniania usługi całkowicie na platformie Azure. Sprawdź **stan** kolumny dla nowo ustawienia zarządzania bramy chmury ustalenie, kiedy usługa jest gotowa.

## <a name="step-5-configure-primary-site-for-client-certification-authentication"></a>Krok 5. Konfigurowanie lokacji głównej do uwierzytelniania klientów certyfikacji

1. W konsoli programu Configuration Manager, przejdź do **administracji** > **konfiguracja lokacji** > **witryny**.

2. Wybierz lokację główną dla klientów, o których chcesz zarządzać za pośrednictwem bramy zarządzania w chmurze, a następnie wybierz pozycję **właściwości**.

3. Na karcie Komunikacja komputera klienta w lokacji głównej arkusza właściwości sprawdź **Użyj certyfikatu klienta PKI (uwierzytelnianie) Jeśli jest dostępna**.

4. Upewnij się wyczyścić **klienci sprawdzają listę odwołania certyfikatów (CRL) dla systemów lokacji**. Ta opcja tylko będą wymagane, jeśli zostały publicznie publikowania z listy CRL.


## <a name="step-6-add-the-cloud-management-gateway-connector-point"></a>Krok 6. Dodaj punkt łącznika chmury zarządzania bramy

Punkt łącznika chmury zarządzania bramą jest nowa rola systemu lokacji do komunikowania się z bramą zarządzania w chmurze. Aby dodać punkt łącznika bramy zarządzania chmurze, postępuj zgodnie z instrukcjami [Dodaj role systemu lokacji dla programu System Center Configuration Manager](/sccm/core/servers/deploy/configure/add-site-system-roles).

## <a name="step-7-configure-roles-for-cloud-management-gateway-traffic"></a>Krok 7. Konfigurowanie ról dla ruchu w chmurze zarządzania bramy

Ostatnim krokiem w procesie konfigurowania bramy zarządzania w chmurze jest do konfigurowania ról systemu lokacji do akceptowania ruchu bramy zarządzania w chmurze. Tylko punkt i oprogramowania aktualizacji roli zarządzania punktu są obsługiwane dla bramy zarządzania w chmurze. Każda rola należy skonfigurować osobno.

1. W konsoli programu Configuration Manager, przejdź do **administracji** > **konfiguracja lokacji** > **serwery i role systemu lokacji**.

2. Wybierz serwer systemu lokacji dla roli, którą chcesz skonfigurować ruchu bramy zarządzania w chmurze.

3. Wybierz rolę, a następnie wybierz pozycję **właściwości**.

4. W arkuszu właściwości roli w obszarze połączenia klienta, zaznacz pole wyboru obok pozycji **ruch bramy zarządzania chmury programu Configuration Manager umożliwia**, a następnie wybierz pozycję **OK**. Powtórz te czynności dla pozostałych ról. Włączanie **HTTPS** opcja zaleca się najlepszym rozwiązaniem bezpieczeństwa, ale nie jest wymagana.

## <a name="step-8-configure-clients-for-cloud-management-gateway"></a>Krok 8. Skonfigurować klientów do chmury zarządzania bramy

Po zarządzania chmurą bramy a role systemu lokacji są w pełni skonfigurowany i uruchomiony, klienci otrzymają lokalizacji usługi bramy zarządzania w chmurze automatycznie przy kolejnym żądaniu lokalizacji. Klienci muszą być w sieci firmowej do odbierania lokalizacji usługi bramy zarządzania w chmurze. Cykl sondowania żądań lokalizacji jest co 24 godziny. Jeśli nie chcesz czekać na żądanie zwykle zaplanowane lokalizacji, możesz wymusić żądanie przez ponowne uruchomienie usługi hosta agenta programu SMS (ccmexec.exe) na komputerze.

Z lokalizacją usługi bramy zarządzania w chmurze skonfigurowany na komputerze klienckim automatycznie może ustalić, czy jest ono w intranecie lub Internecie. Jeśli klient może kontaktować się z kontrolerem domeny lub lokalnego punktu zarządzania, użyje on do komunikowania się z programem Configuration Manager, w przeciwnym razie go będzie uwzględniać go jest w Internecie i użyj lokalizacji bramy zarządzania chmury usługi do komunikacji.

>[!NOTE]
> Można wymusić klientowi zawsze używać bramy zarządzania chmury niezależnie od tego, czy jest w intranecie lub Internecie. Aby to zrobić, ustaw następujący klucz rejestru na komputerze klienckim: \
>
> `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\CCM\Security, ClientAlwaysOnInternet = 1`

Aby sprawdzić, czy klienci mogą kontaktować się z programu Configuration Manager, można uruchomić następujące polecenie programu PowerShell na komputerze klienckim:

`gwmi -namespace root\ccm\locationservices -class SMS_ActiveMPCandidate`

To polecenie wyświetla punkty zarządzania, które klient może nawiązać kontakt z tym usługi bramy zarządzania w chmurze.

## <a name="next-steps"></a>Następne kroki

[Monitorowanie klientów dla bramy zarządzania w chmurze](monitor-clients-cloud-management-gateway.md)
