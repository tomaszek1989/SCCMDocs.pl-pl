---
title: "Planowanie brama zarządzania chmurze | Dokumentacja firmy Microsoft"
description: 
ms.date: 06/07/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-client
ms.assetid: 2dc8c9f1-4176-4e35-9794-f44b15f4e55f
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: c6ee0ed635ab81b5e454e3cd85637ff3e20dbb34
ms.openlocfilehash: a7380ae781447880ffcba0778694ea62e10c4889
ms.contentlocale: pl-pl
ms.lasthandoff: 06/08/2017

---

# <a name="plan-for-the-cloud-management-gateway-in-configuration-manager"></a>Planowanie brama zarządzania chmury w programie Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Począwszy od wersji 1610, brama zarządzania w chmurze zapewnia prosty sposób zarządzać klientami programu Configuration Manager w Internecie. Usługi w chmurze zarządzania bramy został wdrożony do systemu Microsoft Azure i wymaga subskrypcji platformy Azure. Łączy się przy użyciu nowej roli wywołuje punkt łącznika bramy zarządzania chmury infrastruktury programu Configuration Manager lokalnie. Po wdrożeniu i skonfigurowaniu, klienci będą mogli uzyskać dostępu lokalnego Menedżera konfiguracji ról systemu lokacji niezależnie od tego, czy są one prywatnego wewnętrznej sieci lub w Internecie.

> [!TIP]  
> Brama zarządzania chmury, wprowadzonym w wersji 1610, jest to funkcja wersji wstępnej. Aby ją włączyć, zobacz [korzystanie z funkcji wersji wstępnej aktualizacje](/sccm/core/servers/manage/pre-release-features).

Użyj konsoli programu Configuration Manager, aby wdrożyć usługę Azure, dodania roli punkt łącznika chmury zarządzania bramy i skonfigurować role systemu lokacji, aby zezwolić na ruch bramy zarządzania chmury. Brama zarządzania chmury aktualnie obsługuje tylko punkt i oprogramowania aktualizacji roli zarządzania punktu.

Certyfikaty klienta i certyfikatów Secure Socket Layer (SSL) są wymagane do uwierzytelniania komputerów i szyfrowania komunikacji między warstwami innej usługi. Komputery klienckie otrzymują zwykle certyfikat klienta do wymuszania zasad grupy. Do szyfrowania komunikacji między klientami a serwerem systemu lokacji hostujących role, należy utworzyć niestandardowego certyfikatu SSL z urzędu certyfikacji. Można również muszą skonfigurować certyfikat zarządzania na platformie Azure, umożliwiająca programowi Configuration Manager, aby wdrożyć usługę bramy zarządzania w chmurze.

## <a name="requirements-for-cloud-management-gateway"></a>Wymagania dotyczące bramy zarządzania w chmurze

-   Komputery klienckie i serwerze systemu lokacji uruchomione punkt łącznika chmury zarządzania bramy.

-   Niestandardowe certyfikaty SSL z wewnętrznego urzędu certyfikacji — używany do szyfrowania komunikacji z komputerami klienckimi i uwierzytelniania tożsamości usługi bramy zarządzania w chmurze.

-   Subskrypcja platformy Azure dla usługi w chmurze.

-   Certyfikat zarządzania platformy Azure — używany do uwierzytelniania programu Configuration Manager przy użyciu platformy Azure.

## <a name="specifications-for-cloud-management-gateway"></a>Wymagania dotyczące bramy zarządzania w chmurze

- Każde wystąpienie bramy zarządzania chmury obsługuje 4000 klientów.
- Firma Microsoft zaleca utworzenie co najmniej dwa wystąpienia bramy zarządzania chmury w celu zwiększenia dostępności.
- Brama zarządzania chmury obsługuje tylko punkt i oprogramowania aktualizacji roli zarządzania punktu.
-   Następujące funkcje w programie Configuration Manager są obecnie obsługiwane dla bramy zarządzania chmury:

    -   Wdrażanie klientów
    -   Automatycznego przypisywania lokacji
    -   Zasady użytkownika
    -   Katalog aplikacji (w tym żądania zatwierdzenia oprogramowania)
    -   Wdrożenie pełnego systemu operacyjnego (OSD)
    -   Konsola programu Configuration Manager
    -   Zdalne narzędzia
    -   Witryny sieci Web raportowania
    -   Wake on LAN
    -   Mac, Linux i UNIX
    -   Usługa Azure Resource Manager
    -   Równorzędna pamięć podręczna
    -   Lokalne zarządzanie urządzeniami przenośnymi

## <a name="cost-of-cloud-management-gateway"></a>Koszt brama zarządzania w chmurze

>[!IMPORTANT]
>Informacje o kosztach poniżej jest tylko do celów szacowania. Środowiska mogą mieć inne zmienne, które mają wpływ na całkowity koszt używania bramy zarządzania w chmurze.

Brama zarządzania chmury wykorzystuje następujące funkcje Microsoft Azure wiąże się z opłat do konta subskrypcji platformy Azure:

-   Maszyna wirtualna

    -   Brama zarządzania chmury wymaga obecnie Standard\_A2 maszyny wirtualnej. Podczas tworzenia usługi, można wybrać sposób wiele maszyn wirtualnych w celu obsługi usługi (co jest ustawieniem domyślnym).

    -   Podczas szacowania tylko do celów, oczekuje, że jeden standardowy Azure\_maszyna wirtualna A2 może obsługiwać około 2000 jednoczesnych klientów internetowych.

    -   Zobacz [Azure Kalkulator cen](https://azure.microsoft.com/en-us/pricing/calculator/) w celu określenia potencjalne koszty.

      >[!NOTE]
      >Koszty maszyny wirtualnej zależy od regionu.

-   Transfer danych wychodzących

    -   Jest obciążany dla dane przepływające z usługi. Zobacz [Azure przepustowości szczegóły cennika](https://azure.microsoft.com/en-us/pricing/details/bandwidth/) w celu określenia potencjalne koszty.

    -   Podczas szacowania tylko do celów, oczekiwano około 100 MB na klienta miesięcznie dla klientów internetowych podczas odświeżania zasad co godzinę.

    >[!NOTE]
    > Wykonywanie innych działań obsługiwane za pośrednictwem bramy zarządzania chmury (np. wdrażanie aktualizacji oprogramowania lub aplikacje) będą Zwiększ ilość transfer danych wychodzących z platformy Azure.

-   Magazyn zawartości

    -   Klienci internetowi zarządzanych za pomocą bramy zarządzania chmury pobierze zawartość aktualizacji oprogramowania z witryny Windows Update bez dodatkowych opłat.

    -   Niezbędne treść (na przykład aplikacje) musi zostać dystrybuowany do punktu dystrybucji w chmurze. Obecnie brama zarządzania chmura obsługuje tylko punkt dystrybucji w chmurze wysyłanie zawartości do klientów.

    - Zobacz kosztów [chmurowych punktów dystrybucji](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point#cost-of-using-cloud-based-distribution) więcej szczegółów.

## <a name="frequently-asked-questions-about-the-cloud-management-gateway-cmg"></a>Często zadawane pytania dotyczące chmury zarządzania bramy (CMG)

### <a name="why-use-the-cloud-management-gateway"></a>Dlaczego warto używać bramy zarządzania w chmurze?

Tej roli można użyć w celu uproszczenia zarządzania klientami internetowymi w trzy czynności z konsoli programu Configuration Manager.

1. Wdrażanie CMG do platformy Azure przy użyciu [Tworzenie bramy zarządzania chmury](/sccm/core/clients/manage/setup-cloud-management-gateway) kreatora.
2. Skonfiguruj [punktu połączenia bramy zarządzania w chmurze](/sccm/core/servers/deploy/configure/install-site-system-roles) Rola systemu lokacji.
3. [Konfigurowanie ról dla ruchu bramy zarządzania chmury](/sccm/core/clients/manage/setup-cloud-management-gateway#step-7-configure-roles-for-cloud-management-gateway-traffic), takie jak punkt zarządzania i punkt aktualizacji oprogramowania.

### <a name="how-does-the-cloud-management-gateway-work"></a>Jak działa brama zarządzania w chmurze?

- Punkt połączenia z chmurą zarządzania bramy umożliwia połączenie spójne i wysokiej wydajności z Internetu z bramą zarządzania w chmurze.
- Configuration Manager publikuje ustawienia CMG tym połączenia informacji i ustawień zabezpieczeń.
- CMG uwierzytelnianie i przekazuje żądania klientów programu Configuration Manager do punktu połączenia bramy zarządzania chmury. Te żądania są przekazywane do ról w sieci firmowej, zgodnie z mapowania adresów URL.

### <a name="how-is-the-cloud-management-gateway-deployed"></a>Sposób wdrażania bramy zarządzania w chmurze?

Składnik menedżera usługi chmury w punkcie połączenia usługi obsługuje wszystkie zadania wdrażania CMG. Ponadto monitoruje i raportuje usługi kondycji i rejestrowanie informacji z usługi Azure AD.

#### <a name="certificate-requirements"></a>Wymagania certyfikatu

Będą potrzebne do zabezpieczania CMG następujących certyfikatów:

- **Certyfikat zarządzania** — może to być dowolny certyfikat, tym certyfikaty z podpisem własnym. Można użyć certyfikatu publicznego przekazane do usługi Azure AD lub [PFX z kluczem prywatnym](/sccm/mdm/deploy-use/create-pfx-certificate-profiles) zaimportowane do programu Configuration Manager do uwierzytelniania za pomocą usługi Azure AD.
- **Certyfikat usługi sieci Web** -zalecane jest użycie certyfikatu publicznego urzędu certyfikacji do uzyskania natywnego zaufania przez klientów. CName musi zostać utworzone w publicznych registar DNS. Symbol wieloznaczny certyfikaty nie są obsługiwane.
- **Certyfikaty głównego/SubCA przekazać do CMG** -CMG musi przeprowadzić pełne sprawdzanie poprawności łańcucha certyfikatów PKI klienta. Jeśli używasz urzędu certyfikacji przedsiębiorstwa do wystawiania certyfikatów PKI klienta i jego główny lub podrzędny urząd certyfikacji nie jest dostępna w Internecie, użytkownik musi przekaż go do CMG.

#### <a name="deployment-process"></a>Proces wdrażania

Dostępne są dwie fazy do wdrożenia:

- Wdrażanie usługi w chmurze
    - Przekazywanie z [schematu definicji usługi Azure](https://msdn.microsoft.com/library/azure/ee758711.aspx) pliku (csdef)
    - Przekazywanie z [schemat konfiguracji usługi Azure](https://msdn.microsoft.com/library/azure/ee758710.aspx) pliku (cscfg).
- Konfigurowanie składników CMG na serwerze usługi Azure AD i skonfigurować punkty końcowe, programów obsługi HTTP i usług w Internet Information Services (IIS)

Jeśli zmienisz konfigurację CMG wdrożenia konfiguracji jest inicjowana na CMG.

### <a name="how-does-the-cloud-management-gateway-help-ensure-security"></a>Jak brama zarządzania chmury ułatwiają zapewnienie bezpieczeństwa?

CMG pomaga zapewnić bezpieczeństwo w następujący sposób:

- Akceptuje i zarządza połączenia z tym wzajemne uwierzytelnianie SSL przy użyciu certyfikaty wewnętrzne punkty połączenia CMG i identyfikatorów połączeń.
- Akceptuje i przekazuje żądania klientów
    - Wstępnie uwierzytelnia połączeń przy użyciu protokołu SSL wzajemne certyfikatu PKI klienta.
    - Lista zaufania certyfikatów sprawdza głównego certyfikatu klienta PKI. Można określić tego ustawienia w kliencie komunikacji ustawienia właściwości lokacji. Wykonuje także tego samego weryfikacji jako punkt zarządzania dla klienta.
    - Weryfikuje odebrane adresy URL
    - Filtry otrzymał adresów URL, aby sprawdzić, czy dowolnego punktu połączenia połączeń CMG może obsłużyć żądanie adresu URL.  
    - Sprawdza, czy sprawdzanie długości zawartości dla każdego publikowania punktu końcowego.
    - Działanie okrężne '-' załadować równowagi między CMG punkty połączenia z tej samej lokacji.

- Zabezpiecza CMG punktu połączenia
    - Tworzy spójne połączenia HTTP/TCP wszystkie wirtualne wystąpienia CMG nawiązującego połączenie. Sprawdza i obsługuje połączenia co minutę.
    - Wzajemnie autheticates uwierzytelniania SSL z CMG przy użyciu certyfikatów wewnętrznych.
    - Przekazuje HTTP na podstawie mapowania adresów URL.
    - Raport stanu połączenia w celu określenia stanu kondycji usługi administratora.
    - Raporty z raportu ruchu punktu końcowego na punkt końcowy co 5 minut.

- Zabezpiecz publikowania punktu końcowego klienta programu Configuration Manager po role, takie jak punkt zarządzania i oprogramowania aktualizacji punktu hosta punktów końcowych w usługach IIS do obsługi żądań klientów. Każdy punkt końcowy opublikowane CMG ma mapowanie adresu URL.
Zewnętrzny adres URL jest ten, który klient używa do komunikacji z CMG.
Wewnętrzny adres URL jest punkt połączenia CMG używany do przekazywania żądań do wewnętrznego serwera.

#### <a name="example"></a>Przykład:
Po włączeniu CMG ruchu w punkcie zarządzania programu Configuration Manager tworzy zbiór mapowania adresów URL wewnętrznie dla każdego serwera punktu zarządzania, takich jak ccm_system, ccm_incoming i sms_mp.
Zewnętrzny adres URL punktu końcowego ccm_system punkt zarządzania może wyglądać **https://<CMG service name>/CCM_Proxy_MutualAuth/<MP Role ID>/CCM_System**.
Adres URL jest unikatowy dla każdego punktu zarządzania. Klient programu Configuration Manager, a następnie naraża CMG włączone nazwa pakietu administracyjnego, takich jak  **<CMG service name>/CCM_Proxy_MutualAuth/<MP Role ID>**  do listy punktów zarządzania internetowego.
Wszystkie opublikowane zewnętrzne adresy URL są przekazywane do CMG automatycznie, a następnie CMG jest w stanie wykonać filtrowanie adresów URL. Wszystkie replikacja mapowanie adresu URL do CMG punktu połączenia, dzięki czemu może przekazywać do serwerów wewnętrznych, zgodnie z zewnętrznego adresu URL żądania klienta.

### <a name="what-ports-are-used-by-the-cloud-management-gateway"></a>Jakie porty są używane przez bramę zarządzania w chmurze?

- Nie portów przychodzących wymagana w sieci lokalnej. Wdrożenie CMG utworzy licznych na CMG automatycznie.
- Oprócz 443 Niektóre porty wyjściowe są wymagane przez punkt połączenia CMG.

|||||
|-|-|-|-|
|Przepływ danych|Serwer|Porty serwera|Klient|
|CMG wdrożenia|Azure|443|Punkt połączenia usługi programu Configuration Manager|
|Tworzenie kanału CMG|CMG|Wystąpienie maszyny Wirtualnej: 1 port: 443<br>Wystąpienie maszyny Wirtualnej: N (N > = 2 lub N < = 16) porty: 10124 ~ N 10140 ~ N|Punkt połączenia CMG|
|Klientowi CMG|CMG|443|Klient|
|Łącznik CMG do roli lokacji (obecnie punktów zarządzania i punkty aktualizacji oprogramowania)|Rola lokacji|Protokół/porty skonfigurowane w roli lokacji|Punkt połączenia CMG|

### <a name="how-can-you-improve-performance-of-the-cloud-management-gateway"></a>Jak można poprawić wydajność bramy zarządzania chmury

- Jeśli to możliwe, skonfiguruj CMG, punkt połączenia CMG a serwerem lokacji programu Configuration Manager w samym regionu w celu zmniejszenia opóźnień w sieci.
- Połączenie między klientem programu Configuration Manager i CMG nie jest obecnie obsługujący regionu.
- Aby uzyskać wysoką dostępność, zaleca się co najmniej 2 wystąpienia wirtualne CMG i dwoma punktami połączenia CMG dla każdej witryny
- Możesz skalować CMG w celu obsługi większej liczby klientów, dodając więcej wystąpień maszyny Wirtualnej. Są one równoważone przez moduł równoważenia obciążenia usługi Azure AD.
- Utwórz więcej punktów połączenia CMG rozłożenie obciążenia między nimi. CMG będzie "okrężnego" ruchu do łączenia CMG punktów połączenia.
- Numer pomocy technicznej klienta dla każdego wystąpienia CMG maszyny Wirtualnej jest k 6 w wersji 1702. Gdy kanał CMG jest mocno obciążony, żądanie będzie nadal obsługiwane, ale może trwać dłużej niż normalnie.

### <a name="how-can-you-monitor-the-cloud-management-gateway"></a>Jak można monitorować brama zarządzania w chmurze?

Rozwiązywanie problemów z wdrażaniem, użyj **CloudMgr.log** i **CMGSetup.log**.
Rozwiązywanie problemów z usługi kondycji, użyj **CMGService.log** i **SMS_CLOUD_PROXYCONNECTOR.log**.
Do rozwiązywania problemów klienta ruch, użyj **CMGHttpHandler.log**, **CMGService.Log**, i **SMS_CLOUD_PROXYCONNECTOR.log**.

Aby uzyskać listę wszystkich plików dziennika związanych z CMG, zobacz [pliki dziennika w programie Configuration Manager](https://docs.microsoft.com/sccm/core/plan-design/hierarchy/log-files#cloud-management-gateway)

## <a name="next-steps"></a>Następne kroki

[Konfigurowanie bramy zarządzania chmurą](setup-cloud-management-gateway.md)

