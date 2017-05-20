---
title: "Planowanie brama zarządzania w chmurze | Dokumentacja firmy Microsoft"
description: 
ms.date: 05/16/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-client
ms.assetid: 2dc8c9f1-4176-4e35-9794-f44b15f4e55f
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: ae60eb25383f4bd07faaa1265185a471ee79b1e9
ms.openlocfilehash: b1295891a5567e64b901c79100c2971e526dc874
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---

# <a name="plan-for-the-cloud-management-gateway-in-configuration-manager"></a>Planowanie zarządzania chmury bramy w programie Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Począwszy od wersji 1610, brama zarządzania chmury udostępnia prosty sposób zarządzać klientami programu Configuration Manager w Internecie. Usługa bramy zarządzania w chmurze jest wdrażana Microsoft Azure i wymaga subskrypcji platformy Azure. Łączy się z lokalnej infrastruktury programu Configuration Manager za pomocą nowej roli o nazwie punkt łącznik chmury zarządzania bramy. Po wdrożeniu i skonfigurowaniu klienci będą mogli uzyskać dostępu lokalnego Menedżera konfiguracji ról systemu lokacji niezależnie od tego, czy są one prywatnego wewnętrznej sieci lub w Internecie.

Użyj konsoli programu Configuration Manager do wdrażania usługi Azure, Dodaj rolę łącznika punkt chmury zarządzania bramą i konfigurowania ról systemu lokacji, aby zezwalała na ruch bramy zarządzania chmury. Brama zarządzania chmury aktualnie obsługuje tylko role punktu zarządzania i oprogramowania aktualizacji punktu.

Certyfikaty klientów oraz certyfikatów Secure Socket Layer (SSL) są wymagane do uwierzytelniania komputerów i szyfrowania komunikacji między różne warstwy usługi. Komputery klienckie zwykle otrzymywać certyfikat klienta w trybie wymuszania zasad grupy. Do szyfrowania ruchu między klientami a hosting role serwera systemu lokacji, należy utworzyć niestandardowe certyfikatu SSL z urzędu certyfikacji. Istnieje również muszą skonfigurowania certyfikatu zarządzania w systemie Azure, umożliwiająca programowi Configuration Manager do wdrożenia usługi bramy zarządzania chmury.

## <a name="requirements-for-cloud-management-gateway"></a>Wymagania dotyczące chmury zarządzania bramą

-   Komputery klienckie i serwera systemu lokacji uruchomione punkt łącznik chmury zarządzania bramy.

-   Niestandardowe certyfikaty SSL z wewnętrznego urzędu certyfikacji - używany do szyfrowania komunikacji z komputerami klienckimi i uwierzytelniania tożsamości usługi w chmurze zarządzania bramą.

-   Subskrypcji platformy Azure dla usług w chmurze.

-   Certyfikat zarządzania Azure — używany do uwierzytelniania programu Configuration Manager w systemie Azure.

## <a name="specifications-for-cloud-management-gateway"></a>Wymagania dotyczące chmury zarządzania bramą

- Każde wystąpienie bramy zarządzania chmury obsługuje 4000 klientów.
- Zaleca się utworzenie co najmniej dwa wystąpienia chmury brama zarządzania w celu zwiększenia dostępności.
- Brama zarządzania chmura obsługuje tylko role punktu zarządzania i oprogramowania aktualizacji punktu.
-   Następujące funkcje w programie Configuration Manager są obecnie nieobsługiwane chmury zarządzania bramy:

    -   Wdrażanie klientów
    -   Automatycznego przypisywania lokacji
    -   Zasady użytkownika
    -   Katalog aplikacji (w tym żądań zatwierdzenia oprogramowania)
    -   Wdrożenie pełnej wersji systemu operacyjnego (OSD)
    -   Konsola programu Configuration Manager
    -   Zdalne narzędzia
    -   Raportowanie witryny sieci Web
    -   Wake on LAN
    -   Mac, Linux i UNIX
    -   Menedżer zasobów systemu Azure
    -   Buforowanie równorzędne
    -   Lokalne zarządzanie urządzeniami przenośnymi

## <a name="cost-of-cloud-management-gateway"></a>Koszt chmury zarządzania bramą

>[!IMPORTANT]
>Informacje o kosztach poniżej jest tylko do celów szacowania. Środowisko może mieć inne zmienne, które mają wpływ na całkowity koszt używania bramy zarządzania chmury.

Brama zarządzania chmury wykorzystuje następujące funkcje Microsoft Azure ponosi opłaty do konta subskrypcji platformy Azure:

-   Maszyna wirtualna

    -   Brama zarządzania chmury wymaga obecnie Standard\_A2 maszyny wirtualnej. Podczas tworzenia usługi, można wybrać liczbę maszyn wirtualnych do obsługi usługi (jest domyślnie).

    -   Podczas szacowania tylko do celów, oczekuje, że jeden standardowy Azure\_A2 maszyny wirtualnej może obsługiwać około 2000 jednoczesnych klientów internetowych.

    -   Zobacz [Azure Kalkulator cen](https://azure.microsoft.com/en-us/pricing/calculator/) w celu określenia potencjalnych kosztów.

      >[!NOTE]
      >Koszty maszyny wirtualnej różnią się zależnie od regionu.

-   Transfer danych wychodzących

    -   Jest obciążany przepływające z usługi danych... Zobacz [Azure przepustowości szczegóły cennika](https://azure.microsoft.com/en-us/pricing/details/bandwidth/) w celu określenia potencjalnych kosztów.

    -   Podczas szacowania tylko do celów, oczekują około 100 MB na klienta na miesiąc dla klientów internetowych, myśl odświeżanie zasad co godzinę.

    >[!NOTE]
    > Wykonywanie innych czynności obsługiwane za pośrednictwem bramy zarządzania chmury (np. wdrażanie aktualizacji oprogramowania lub aplikacji) większej ilości przesyłanych danych wychodzących z systemu Azure.

-   Magazyn zawartości

    -   Klienci internetowi zarządzane w chmurze bramy zarządzania zostanie pobrany z usługi Windows Update zawartość aktualizacji oprogramowania bez opłat.

    -   Niezbędne treść (na przykład aplikacje) musi zostać dystrybuowany do punktu dystrybucji w chmurze. Brama zarządzania chmura obsługuje obecnie, tylko punkt dystrybucji w chmurze do wysyłania zawartości do klientów.

    - Zobacz kosztów [dystrybucji w chmurze](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point#cost-of-using-cloud-based-distribution) więcej szczegółów.

## <a name="next-steps"></a>Następne kroki

[Konfigurowanie chmury zarządzania bramą](setup-cloud-management-gateway.md)


## <a name="frequently-asked-questions-about-the-cloud-management-gateway-cmg"></a>Często zadawane pytania dotyczące chmury zarządzania bramy (CMG)

### <a name="why-use-the-cloud-management-gateway"></a>Do czego służy brama zarządzania chmury?

Aby uprościć zarządzanie klientami w trzech krokach z konsoli programu Configuration Manager za pomocą tej roli.

1. Wdrażanie CMG w systemie Azure przy użyciu [utworzyć bramę zarządzania chmury](/sccm/core/clients/manage/setup-cloud-management-gateway) kreatora.
2. Skonfiguruj [chmury punktu połączenia bramy zarządzania](/sccm/core/servers/deploy/configure/install-site-system-roles) Rola systemu lokacji.
3. [Skonfigurowanie ról dla chmury ruch związany z zarządzaniem bramy](/sccm/core/clients/manage/setup-cloud-management-gateway#step-7-configure-roles-for-cloud-management-gateway-traffic), jak punkt zarządzania i punkt aktualizacji oprogramowania.

### <a name="how-does-the-cloud-management-gateway-work"></a>Jak działa brama zarządzania chmury?

- Punkt połączenia bramy zarządzania chmury umożliwia połączenie spójne i wysokiej wydajności z Internetu z bramą zarządzania chmury.
- Configuration Manager publikuje ustawienia CMG tym połączenia informacji i ustawień zabezpieczeń.
- CMG uwierzytelnianie i przekazuje żądania klientów programu Configuration Manager do punktu połączenia chmury zarządzania bramą. Żądania te są przesyłane dalej do ról w sieci firmowej, zgodnie z mapowania adresów URL.

### <a name="how-is-the-cloud-management-gateway-deployed"></a>Brama zarządzania chmury wdrażanie?

Składnik menedżera usługi chmury w ramach punktu połączenia usługi obsługuje wszystkie zadania wdrażania CMG. Ponadto monitoruje i raporty usługi kondycji i rejestrowanie informacji z usługi Azure AD.

#### <a name="certificate-requirements"></a>Wymagania certyfikatu

Należy zabezpieczyć CMG następujących certyfikatów:

- **Certyfikat zarządzania** — może to być dowolny certyfikat, w tym certyfikaty z podpisem własnym. Można użyć certyfikatu publicznego przekazane do usługi Azure AD lub [PFX z kluczem prywatnym](/sccm/mdm/deploy-use/create-pfx-certificate-profiles) zaimportowane do programu Configuration Manager do uwierzytelniania w usłudze Azure AD. 
- **Certyfikat usługi sieci Web** -zalecane jest użycie certyfikatu publicznego urzędu certyfikacji w celu uzyskania macierzystego zaufania przez klientów. CName musi zostać utworzona w publicznych registar DNS. Certyfikaty symbole wieloznaczne nie są obsługiwane.
- **Przekaż certyfikaty głównego/SubCA do CMG** -CMG musi przeprowadzić pełne sprawdzanie poprawności łańcucha certyfikatów PKI klienta. Jeśli używasz wydawania certyfikatów PKI klienta i ich głównego urzędu certyfikacji przedsiębiorstwa lub podrzędny urząd certyfikacji nie jest dostępny w Internecie, następnie należy przesłać go do CMG.

#### <a name="deployment-process"></a>Proces wdrażania

Dostępne są dwie fazy do wdrożenia:

- Wdrożona usługa w chmurze
    - Przekaż swoje [schematu definicji usługi Azure](https://msdn.microsoft.com/library/azure/ee758711.aspx) pliku (csdef)
    - Przekaż swoje [schemat konfiguracji usługi Azure](https://msdn.microsoft.com/library/azure/ee758710.aspx) pliku (cscfg).
- Konfigurowanie składnika CMG na serwerze usługi Azure AD i skonfigurować punkty końcowe, funkcje obsługi protokołu HTTP i usług w Internetowych usług informacyjnych (IIS)

Jeśli zmienisz konfigurację CMG CMG jest zainicjowane wdrożenie konfiguracji.

### <a name="how-does-the-cloud-management-gateway-help-ensure-security"></a>Jak brama zarządzania chmury pomaga zapewnić bezpieczeństwo?

CMG pomaga zapewnić bezpieczeństwo w następujący sposób:

- Akceptuje i zarządza połączeń z tym wzajemne uwierzytelnianie SSL przy użyciu certyfikatów wewnętrznych punkty połączenia CMG i połączenie identyfikatorów.
- Akceptuje i przekazuje żądania klienta
    - Wstępnie uwierzytelnia połączeń przy użyciu protokołu SSL wzajemnego certyfikatu PKI klienta.
    - Lista zaufania certyfikatów sprawdza głównego certyfikatu PKI klienta. Można określić tego ustawienia w kliencie komunikacji ustawień właściwości lokacji. Wykonuje również samo sprawdzanie poprawności jako punkt zarządzania dla klienta.
    - Sprawdza poprawność odebrane adresy URL
    - Filtry otrzymał adresy URL, aby sprawdzić, jeśli dowolny łączącego punkt połączenia CMG można zrealizować żądania adresu URL.  
    - Sprawdza długość zawartości wyboru dla każdego punktu końcowego publikowania.
    - Działanie okrężne '-' załadować równowagi między CMG punkty połączenia z tej samej lokacji.

- Zabezpiecza CMG punktu połączenia
    - Tworzy spójne połączenia HTTP/TCP wszystkie wirtualne wystąpienia CMG nawiązujący połączenie. Sprawdza, czy i utrzymywania połączenia co minutę.
    - Wzajemnie autheticates uwierzytelnianie SSL z CMG przy użyciu certyfikatów wewnętrznych.
    - Przekazuje HTTP na podstawie mapowania adresów URL.
    - Raporty stanu połączenia w celu określenia stanu kondycji usługi Administrator.
    - Raporty punkt końcowy raport o ruchu na punkt końcowy co 5 minut.

- Bezpieczne publikowanie punktu końcowego klienta programu Configuration Manager miała dostęp do ról, takich jak punkt zarządzania i oprogramowania aktualizacji punktu hosta punktów końcowych w usługach IIS do obsługi żądań klientów. Każdy punkt końcowy publikowane CMG ma mapowanie adresu URL.
Zewnętrzny adres URL jest ten, którego klient używa do komunikowania się z CMG.
Wewnętrzny adres URL jest używany do przesyłania żądań do wewnętrznego serwera punktu połączenia CMG. 

#### <a name="example"></a>Przykład:
Po włączeniu ruchu CMG w punkcie zarządzania programu Configuration Manager tworzy zestaw mapowań adresu URL wewnętrznie dla każdego serwera punktu zarządzania, takich jak ccm_system, ccm_incoming i sms_mp.
Zewnętrzny adres URL punktu końcowego ccm_system punktu zarządzania może wyglądać **https://<CMG service name>/CCM_Proxy_MutualAuth/<MP Role ID>/CCM_System**. Adres URL jest unikatowy dla każdego punktu zarządzania. Klient programu Configuration Manager, a następnie puts CMG włączone nazwa pakietu administracyjnego, takich jak  **<CMG service name>/CCM_Proxy_MutualAuth/<MP Role ID>**  do listy punktów zarządzania internetowego. Wszystkie opublikowane zewnętrznych adresów URL są przekazywane do CMG automatycznie CMG będzie można wykonać filtrowania adresu URL. Wszystkie mapowania adresów URL są replikowane do punktu połączenia CMG, dzięki czemu może przekazywać do serwerów wewnętrznych zgodnie z klient żąda zewnętrznego adresu URL.

### <a name="what-ports-are-used-by-the-cloud-management-gateway"></a>Jakie porty są używane przez tę bramę zarządzania chmury? 

- Nie przychodzącej porty wymagane w sieci lokalnych. Wdrożenie CMG utworzy grupę na CMG automatycznie. 
- Oprócz 443 Niektóre porty wyjściowe są wymagane przez punkt połączenia CMG.

|||||
|-|-|-|-|
|Przepływ danych|Serwer|Porty serwera|Klient|
|CMG wdrożenia|Azure|443|Punkt połączenia usługi programu Configuration Manager|
|Tworzenie kanału CMG|CMG|Wystąpienie maszyny Wirtualnej: 1 port: 443<br>Wystąpienie maszyny Wirtualnej: N (N > = 2 oraz N < = 16) porty: 10124 ~ N 10140 ~ N|Punkt połączenia CMG|
|Klient CMG|CMG|443|Klient|
|Łącznik CMG roli lokacji (obecnie punkty zarządzania i punkty aktualizacji oprogramowania)|Rola lokacji|Protokół/porty skonfigurowane w roli lokacji|Punkt połączenia CMG|

### <a name="how-can-you-improve-performance-of-the-cloud-management-gateway"></a>Jak można poprawić wydajność chmury brama zarządzania

- Jeśli to możliwe, skonfiguruj CMG, punkt połączenia CMG a serwerem lokacji programu Configuration Manager w samej sieci region, aby zmniejszyć czas oczekiwania.
- Obecnie połączenia między klientem programu Configuration Manager i CMG nie są znane regionu.
- W celu uzyskania wysokiej dostępności, zaleca się co najmniej 2 wystąpienia wirtualne CMG i dwoma punktami połączenia CMG każdej lokacji 
- Można skalować CMG obsługuje więcej klientów, dodając więcej wystąpień maszyny Wirtualnej. Są one przez usługę Azure AD równoważenia obciążenia z równoważeniem obciążenia.
- Utwórz więcej punktów połączenia CMG dystrybucję obciążenia między nimi. CMG będzie "okrężnego" ruchu do łączenia CMG punktów połączenia.
- Obsługa klienta numer każde wystąpienie CMG maszyny Wirtualnej jest 6k w wersji 1702. Kanał CMG jest wysokie obciążenie, jeśli żądanie będzie nadal obsługiwane, ale może trwać dłużej niż normalnie.

### <a name="how-can-you-monitor-the-cloud-management-gateway"></a>Jak można monitorować brama zarządzania chmury

Rozwiązywanie problemów z wdrażaniem, użyj **CloudMgr.log** i **CMGSetup.log**.
Rozwiązywanie problemów z kondycji usługi, użyj **CMGService.log** i **SMS_CLOUD_PROXYCONNECTOR.log**.
Rozwiązywanie problemów z ruch sieciowy klienta, użyj **CMGHttpHandler.log**, **CMGService.Log**, i **SMS_CLOUD_PROXYCONNECTOR.log**.

Aby uzyskać listę wszystkich plików dziennika związanych z CMG, zobacz [pliki dziennika w programie Configuration Manager](https://docs.microsoft.com/sccm/core/plan-design/hierarchy/log-files#cloud-management-gateway)


