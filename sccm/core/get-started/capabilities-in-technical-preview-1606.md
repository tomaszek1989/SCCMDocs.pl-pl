---
title: Funkcje w wersji zapoznawczej Technical Preview 1606 programu Configuration Manager
description: "Dowiedz się więcej o funkcjach dostępnych w wersji zapoznawczej Technical Preview programu System Center Configuration Manager, wersja 1606."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 134a2f60-811e-4dc9-a8f5-1ce0018c5c12
caps.latest.revision: "31"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 08747ca981f6697e2bd621afe5df0e3bd06b332d
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="capabilities-in-technical-preview-1606-for-system-center-configuration-manager"></a>Funkcje w wersji Technical Preview 1606 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*

W tym artykule przedstawiono funkcje, które są dostępne w wersji Technical Preview programu System Center Configuration Manager, wersja 1606. Można zainstalować tę wersję, aby zaktualizować i dodać nowe funkcje do lokacji programu Configuration Manager technical preview.      Przed zainstalowaniem tej wersji technical Preview, przejrzyj temat wprowadzający [Technical Preview programu System Center Configuration Manager](../../core/get-started/technical-preview.md), aby zapoznać się z ogólne wymagania i ograniczenia dotyczące używania wersji technical preview, jak zaktualizować między wersjami i sposobu wyrazić swoją opinię na temat funkcji w wersji technical preview.    

**Znane problemy w tej wersji Technical Preview:**  
*  Podczas aktualizacji z wersji zapoznawczej Technical Preview 1604 do 1605, a następnie do wersji 1606, aktualizacji może zakończyć się niepowodzeniem i jest rejestrowany błąd podobny do następującego **cmupdate.log**:

       ERROR: Failed to execute SQL Server command:  ~ ~-- Create site boundary group ~IF  dbo.fnIsCasOrStandalonePrimary() = 1 ~BEGIN ~   PRINT N'Create site boundary group during upgrade' ~   EXEC dbo.spBuildDefaultBoundaryGroups @UserName = N'SYSTEM' ~END          

    W takim przypadku w **aktualizacje i obsługa** kliknij węzeł **Sprawdź aktualizacje**, a następnie **ponów** instalacji aktualizacji.
    ***

**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  

## <a name="dmp_category"></a>Automatycznie kategoryzowanie urządzeń do kolekcji
Możesz utworzyć kategorie urządzeń, które mogą być używane do automatycznego umieszczania urządzeń w kolekcji urządzeń, gdy używasz programu Configuration Manager w usłudze Microsoft Intune. Następnie użytkownicy muszą wybrać kategorię urządzenia, gdy rejestrują urządzenia w usłudze Intune. Ponadto można zmienić kategorię urządzenia z konsoli programu Configuration Manager.

**Ważne:** Ta funkcja działa z **czerwca 2016** wersji usługi Microsoft Intune. Upewnij się, że możesz zostały zaktualizowane do tej wersji przed wypróbowanie tych procedur.

### <a name="try-it-out"></a>Wypróbuj

### <a name="create-a-set-of-device-categories"></a>Utwórz zestaw kategorii urządzeń
1.  W **zasoby i zgodność** obszaru roboczego w konsoli programu Configuration Manager, rozwiń węzeł **omówienie**, następnie kliknij przycisk **kolekcje urządzeń**.
2.  Na **Home** karcie **kategorii** kliknij przycisk **Zarządzanie kategorie urządzeń**.
3.  W **Zarządzanie kategorie urządzeń** okno dialogowe, mogą tworzyć, edytować lub usuwać kategorie. Spróbuj utworzyć nową kategorię.

### <a name="associate-a-collection-with-a-device-category"></a>Skojarzenia kolekcji z kategorii urządzeń
Gdy kolekcja jest skojarzona z kategorii urządzeń, wszystkie urządzenia w tej kategorii, które określisz zostanie dodany do tej kolekcji.
1.  W **właściwości** okna dialogowego dla kolekcji urządzeń, kliknij przycisk **Dodaj regułę** > **regułę kategorii urządzenia**.
2.  W **tworzenia reguły członkostwa kategorii urządzeń** oknie dialogowym Wybierz kategorię, która zostanie zastosowana do wszystkich urządzeń w kolekcji.
3.  Zamknij **tworzenia reguły członkostwa kategorii urządzeń** okno dialogowe i okno dialogowe właściwości kolekcji.

### <a name="change-the-category-of-a-device"></a>Zmień kategorię urządzenia
1.  W **zasoby i zgodność** obszaru roboczego w konsoli programu Configuration Manager, rozwiń węzeł **omówienie**, następnie kliknij przycisk **urządzeń**.
2.  Wybierz urządzenie z **urządzeń** listy, a następnie w **Home** karcie **urządzenia** kliknij przycisk **Zmień kategorię**.
3.  W **edycji kategorii urządzeń** oknie dialogowym Wybierz kategorię, która ma zastosowanie do tego urządzenia, a następnie kliknij pozycję **OK**.

## <a name="dmp_grace"></a>Okres prolongaty wymuszania dla wymaganej aplikacji i wdrożenia aktualizacji oprogramowania

W niektórych przypadkach można umożliwić użytkownikom więcej czasu do instalacji wymagane wdrożenia aplikacji lub aktualizacji oprogramowania poza wszystkie terminy, które zostały skonfigurowane. To może być zwykle być wymagane, jeśli komputer został wyłączony przez dłuższy czas i musi zainstalować dużą liczbę wdrożeń aplikacji lub aktualizacji.
Na przykład jeśli użytkownik końcowy zwrócił się tylko z urlopu, ich może być konieczne Zaczekaj, aż do postaci długiej jako zaległe aplikacji są zainstalowane wdrożeń.
Aby rozwiązać ten problem, można zdefiniować okres prolongaty wymuszania przez wdrożenie ustawienia klienta programu Configuration Manager do kolekcji.

### <a name="try-it-out"></a>Wypróbuj

Aby skonfigurować okres prolongaty, należy wykonać następujące czynności:

1.  Na **Agent komputera** strony ustawień klienta, należy skonfigurować nową właściwość **okres prolongaty wymuszania po wdrożeniu terminu wdrożenia (godziny)** z wartością pomiędzy **1** i **120** godzin.
2.  W ramach nowego wdrożenia wymaganej aplikacji lub we właściwościach istniejącego wdrożenia na **Planowanie** strony, zaznacz pole wyboru **Opóźnij wymuszenie dotyczące tego wdrożenia zgodnie z preferencjami użytkownika**, do okresu prolongaty zdefiniowanego w ustawieniach klienta.
Wszystkie wdrożenia, które mają to pole wyboru zaznaczone i które są przeznaczone dla urządzeń, na których wdrożono również ustawienie klienta użyje okres prolongaty wymuszania.

Skonfiguruj okres prolongaty wymuszania, zaznacz pole wyboru, po osiągnięciu ostatecznego terminu instalacji aplikacji zostanie zainstalowany w pierwszym oknie-business skonfigurowanego przez użytkownika do tego okresu prolongaty. Jednak użytkownik może nadal otworzyć programu Software Center i zainstalować aplikację w dowolnym momencie, które mają. Po wygaśnięciu okresu prolongaty wymuszania wraca do normalnej zachowaniem wdrożeń zaległe.
Podobne opcje zostały dodane do Kreatora wdrażania aktualizacji oprogramowania, Kreator reguł wdrażania automatycznego i strony właściwości.

##  <a name="dmp_devg"></a>Jako zarządzane Instalatora przy użyciu funkcji Guard urządzenia przy użyciu programu Configuration Manager

Ochrona urządzeń jest funkcją systemu Windows 10, która używa sprzętu i oprogramowania funkcje ściśle kontrolować, co może działać na urządzeniu.

Możesz przeczytać szczegółowe omówienie ochrony urządzeń jest i jak działa na [ten artykuł w witrynie Technet](https://technet.microsoft.com/itpro/windows/whats-new/device-guard-overview).

W tej wersji programu Configuration Manager może współdziałać z ochrony urządzeń i [systemu Windows AppLocker](https://technet.microsoft.com/library/dd723678(v=ws.10).aspx) tak, aby plik wykonywalny i pliki DLL, które zostały wdrożone z programem Configuration Manager są automatycznie zaufane, ponieważ pochodzą z instalacji programu Managed, co oznacza, że ich będzie mogła działać na urządzeniu docelowym i innego oprogramowania będzie niemożliwe do uruchomienia, chyba że jawnie mogą być uruchamiane przez inne zasady funkcji AppLocker.  

Obecnie ta funkcja nie jest konfigurowane z poziomu konsoli programu Configuration Manager. Aby skonfigurować zasady wymaga skonfigurowania klucz rejestru na każdym komputerze klienckim i skonfigurowania usług systemu Windows na kliencie.
Po zakończeniu konfigurowania pliku zasad funkcji AppLocker. Po skonfigurowaniu pliku zasad można wdrożyć dowolnego urządzenia klienckiego zgodnego.


Podobnie jak wszystkie zasady funkcji AppLocker zasad przy użyciu reguły zarządzane Instalatora można uruchomić w dwóch trybach:

- Tryb inspekcji — Uwaga mogły być uruchamiane są aplikacje, ale wszystkie aplikacje, które będą blokowane są zgłaszane w pliku dziennika (będzie to możliwe w nowszej wersji programu Configuration Manager).
- Wymuszanie włączone — aplikacje są zablokowane, uruchamianie.

Dodatkowe informacje o korzystaniu z programu Configuration Manager ochrony urządzeń można znaleźć w [blogu dotyczącym pakietu Enterprise Mobility i zabezpieczeń](https://blogs.technet.microsoft.com/enterprisemobility/2016/06/20/configmgr-as-a-managed-installer-with-win10).

Dalsze informacje:

- [Wprowadzenie ochrona urządzeń](https://technet.microsoft.com/itpro/windows/keep-secure/introduction-to-device-guard-virtualization-based-security-and-code-integrity-policies)
- [Urządzenie Guard certyfikacji i zgodność](https://technet.microsoft.com/itpro/windows/keep-secure/device-guard-certification-and-compliance)
- [Przewodnik wdrażania ochrona urządzeń](https://technet.microsoft.com/itpro/windows/keep-secure/device-guard-deployment-guide)

 ##  <a name="dmp_onprem"></a>Wiele punktów zarządzania urządzeniami do zarządzania urządzeniami przenośnymi lokalnej  
 Z Technical Preview 1606, na\-lokalnego zarządzania urządzeniami przenośnymi (MDM) obsługuje nową funkcję systemu Windows 10 Anniversary aktualizację, która automatycznie konfiguruje zarejestrowane urządzenie ma więcej niż jeden zarządzania urządzeniami punktu dostępne do użycia. Ta funkcja umożliwia urządzeniu powrotu do innego punktu zarządzania urządzeniami, gdy który normalne używa nie jest dostępna. Ta funkcja działa tylko dla komputerów przy użyciu systemu Windows 10 Anniversary aktualizacja jest zainstalowana.  

### <a name="try-it-out"></a>Wypróbuj  

1.  Zainstaluj więcej niż jeden punkt zarządzania urządzeniami w hierarchii.  

2.  Rejestrowanie urządzenia z systemem Windows 10 Anniversary aktualizacji dla na\-lokalnych zarządzanie urządzeniami przenośnymi.  

Aby uzyskać informacje o przygotowaniu witryny i rejestrowania urządzeń na potrzeby na\-lokalnego zarządzania urządzeniami przenośnymi, zobacz [zarządzanie urządzeniami przenośnymi za pomocą infrastruktury lokalnej w programie System Center Configuration Manager](../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md).  

## <a name="cloud_proxy"></a>Usługa serwera Proxy w chmurze do zarządzania klientami przez Internet

Usługa serwera Proxy w chmurze zapewnia prosty sposób zarządzać klientami programu Configuration Manager w Internecie. Usługi, która została wdrożona do systemu Microsoft Azure i wymaga subskrypcji platformy Azure, nawiązuje połączenie z lokalnej infrastruktury programu Configuration Manager za pomocą nowej roli punkt łącznika serwera proxy w chmurze wywołuje. Gdy ma ona całkowicie wdrożone i skonfigurowane, klienci będą możliwość dostępu lokalnego role systemu lokacji programu Configuration Manager niezależnie od tego, czy są one połączone siecią wewnętrzną prywatnych lub w Internecie.

Konsola programu Configuration Manager umożliwia wdrażanie usługi Azure, dodania roli punkt łącznika serwera proxy chmury i skonfigurowanie ról systemu lokacji, aby zezwolić na ruch serwera proxy w chmurze. Usługa serwera Proxy w chmurze aktualnie obsługuje tylko punkt zarządzania, punktu dystrybucji i roli punktu aktualizacji oprogramowania.

Certyfikaty klienta i certyfikatów Secure Socket Layer (SSL) są wymagane do uwierzytelniania komputerów i szyfrowania komunikacji między warstwami innej usługi. Komputery klienckie otrzymują zwykle certyfikat klienta do wymuszania zasad grupy. Do szyfrowania komunikacji między klientami a serwerem systemu lokacji hostujących role, należy utworzyć niestandardowego certyfikatu SSL z urzędu certyfikacji. Oprócz tych dwóch typów certyfikatów możesz również muszą skonfigurować certyfikat zarządzania na platformie Azure, który umożliwia programowi Configuration Manager do wdrażania usługi serwera Proxy w chmurze.  

### <a name="requirements-for-cloud-proxy-service-in-tp-1606"></a>Wymagania dotyczące usługi serwera Proxy w chmurze w TP 1606
- Komputery klienckie i serwerze systemu lokacji uruchomione punkt łącznika serwera proxy w chmurze.
- Niestandardowe certyfikaty SSL z wewnętrznego urzędu certyfikacji — używany do szyfrowania komunikacji z komputerami klienckimi i uwierzytelniania tożsamości usługi serwera Proxy w chmurze.
- Subskrypcja platformy Azure dla usługi w chmurze.
- Certyfikat zarządzania platformy Azure — używany do uwierzytelniania programu Configuration Manager przy użyciu platformy Azure.

### <a name="limitations-of-cloud-proxy-service-in-tp-1606"></a>Ograniczenia usługi serwera Proxy w chmurze w TP 1606

- Obsługuje tylko punkt zarządzania, punktu dystrybucji i roli punktu aktualizacji oprogramowania.
- Zasady użytkownika nie są obsługiwane.
- Nie można używać z [na lokalnego zarządzania urządzeniami przenośnymi](../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md) w programie Configuration Manager.
- Obsługiwane tylko w platforma chmury publicznej Azure.


### <a name="try-it-out"></a>Wypróbuj

Proces wdrażania usługi serwera Proxy w chmurze obejmuje następujące kroki:

1. Utworzyć i wydać niestandardowy certyfikat SSL dla usługi serwera Proxy w chmurze.
1. Wyeksportuj głównego certyfikatu klienta.
2. Przekaż certyfikat zarządzania Azure.
3. Konfigurowanie usługi Serwer Proxy chmury w konsoli programu Configuration Manager.
4. Skonfiguruj główną lokację, aby użyć uwierzytelniania certyfikatu klienta.
5. Dodaj punkt łącznika serwera proxy w chmurze do witryny.
6. Konfigurowanie ról systemu lokacji do akceptowania ruchu serwera proxy w chmurze.

Więcej informacji na wykonanie tych kroków można znaleźć w poniższych sekcjach.

#### <a name="create-a-custom-ssl-certificate"></a>Tworzenie niestandardowego certyfikatu SSL

W ten sam sposób, który należy do punktu dystrybucji w chmurze, można utworzyć niestandardowego certyfikatu SSL dla usługi serwera Proxy w chmurze. Postępuj zgodnie z instrukcjami dotyczącymi [wdrażanie certyfikatu usługi dla chmurowych punktów dystrybucji](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_clouddp2008_cm2012) , ale inaczej wykonaj następujące czynności:

* Podczas konfigurowania nowego szablonu certyfikatu, nadaj **odczytu** i **Zarejestruj** uprawnień do grupy zabezpieczeń skonfigurowane dla serwerów programu Configuration Manager.

#### <a name="export-the-client-certificates-root"></a>Eksportuj głównego certyfikatu klienta

Najprostszym sposobem pobrania eksportu głównego certyfikatów klientów w sieci, należy otworzyć certyfikat klienta na jednym maszyn przyłączonych do domeny, które ma jeden i skopiować go.

>[!NOTE]
>Certyfikaty klienta są wymagane na każdym komputerze, który chcesz zarządzać za pomocą usługi serwera Proxy w chmurze i na serwerze systemu lokacji łącznika serwera proxy w chmurze hosting punktu. Jeśli musisz dodać certyfikat klienta do dowolnego z tych urządzeń, zobacz [wdrażanie klienta certyfikatu na komputerach z systemem Windows](/sccm/core/plan-design/network/example-deployment-of-pki-certificates#BKMK_clouddp2008_cm2012).

1. W oknie Uruchamianie wpisz **mmc** i naciśnij klawisz Return.
2. W menu Plik w konsoli zarządzania kliknij polecenie **Dodaj/Usuń przystawkę...** .
3. W oknie dialogowym Dodawanie lub usuwanie przystawek kliknij pozycję **certyfikaty**, kliknij przycisk **Dodaj >**, kliknij przycisk **konto komputera**, kliknij przycisk **dalej**, kliknij przycisk **komputera lokalnego**, a następnie kliknij przycisk **Zakończ**. Kliknij przycisk **OK** , aby zamknąć okno dialogowe.
4. Przejdź do **certyfikaty > osobiste > Certyfikaty**.
5. Kliknij dwukrotnie certyfikat uwierzytelniania klienta na komputerze, kliknij kartę ścieżki certyfikacji, a następnie kliknij dwukrotnie głównego urzędu certyfikacji (w górnej części ścieżki).
6.  Kliknij kartę Szczegóły, a następnie kliknij przycisk **Kopiuj do pliku...** .
7. Ukończ Kreatora eksportu certyfikatów przy użyciu domyślnego formatu certyfikatu. Upewnij się, zanotuj nazwę i lokalizację certyfikatu głównego, którą utworzysz. Będą potrzebne do skonfigurowania usługi serwera Proxy w chmurze w kolejnym kroku.

#### <a name="upload-the-management-certificate-to-azure"></a>Przekaż certyfikat zarządzania na platformie Azure

Certyfikat zarządzania platformy Azure jest wymagany dla programu Configuration Manager dostępu do interfejsu API Azure i skonfigurować usługę serwera Proxy w chmurze. Aby uzyskać więcej informacji oraz instrukcje przekazać certyfikat zarządzania zobacz następujące artykuły w dokumentacji platformy Azure:
- [Omówienie certyfikatów dla usług w chmurze Azure](https://azure.microsoft.com/documentation/articles/cloud-services-certs-create/)
- [Przekaż certyfikat zarządzania platformy Azure, interfejsu API zarządzania](https://azure.microsoft.com/documentation/articles/azure-api-management-certs/).

Upewnij się skopiować identyfikator subskrypcji skojarzonych z certyfikatem zarządzania. Będzie on potrzebny na temat konfigurowania usługi serwera Proxy w chmurze w konsoli programu Configuration Manager.

#### <a name="set-up-cloud-proxy-service"></a>Konfigurowanie usługi Serwer Proxy w chmurze

1. W konsoli programu Configuration Manager, przejdź do **Administracja > usługi w chmurze > Usługa serwera Proxy w chmurze**.
2. Kliknij przycisk **Utwórz usługę serwera Proxy w chmurze**.
3. W chmurze serwera Proxy usługi kreatora tworzenia wprowadź identyfikator subskrypcji platformy Azure (skopiowany z portalu zarządzania platformy Azure), kliknij przycisk Przeglądaj i wybierz plik certyfikatu używanego do przekazania jako certyfikat zarządzania platformy Azure. Kliknij przycisk **Dalej**. Poczekaj kilka chwil konsoli do nawiązania połączenia platformy Azure.
4. Wypełnianie dodatkowe szczegóły w Kreatorze:
    - Określ klucz prywatny (pfx) wyeksportowany z niestandardowego certyfikatu SSL.
    - Określ certyfikat główny wyeksportowane z certyfikatu klienta.
    - Określ taką samą nazwę usługi nazwy FQDN, która zostanie użyta podczas tworzenia nowego szablonu certyfikatu.
    - Usuń zaznaczenie pola obok **Sprawdź odwołania certyfikatu klienta** (o ile nie są publicznie publikowania danych listy CRL).
    - Kliknij przycisk **dalej** po zakończeniu.
5. Przejrzyj ustawienia, a następnie kliknij przycisk **dalej**. Configuration Manager rozpoczyna się ustawienie usługi. Gdy Kreator zakończy pracę, możesz kliknąć **Zamknij**, jednak potrwa od 5 do 15 minut do udostępniania usługi całkowicie na platformie Azure. Sprawdź **stan** kolumny dla nowo Instalatora usługi serwera Proxy w chmurze ustalenie, kiedy usługa jest gotowa.

#### <a name="configure-primary-site-for-client-certification-authentication"></a>Konfigurowanie lokacji głównej do uwierzytelniania klientów certyfikacji

1. W konsoli programu Configuration Manager, przejdź do **Administracja > Konfiguracja lokacji > witryny**.
2. Wybierz lokację główną dla klientów, o których chcesz zarządzać za pośrednictwem usługi Serwer Proxy w chmurze, a następnie kliknij przycisk **właściwości**.
3. Na karcie Komunikacja komputera klienta arkusza właściwości lokacji głównej, zaznacz pole wyboru obok pozycji **Użyj certyfikatu klienta PKI (uwierzytelnianie) Jeśli jest dostępna**.
4. Upewnij się, że Usuń zaznaczenie pola obok **klienci sprawdzają listę odwołania certyfikatów (CRL) dla systemów lokacji**. Ta opcja tylko będą wymagane, jeśli zostały publicznie publikowania z listy CRL.
5. Kliknij przycisk **OK**.

#### <a name="add-the-cloud-proxy-connector-point"></a>Dodaj punkt łącznika serwera proxy w chmurze

Punkt łącznika serwera proxy w chmurze jest nowa rola systemu lokacji do komunikowania się z usługą serwera Proxy w chmurze. Aby dodać punkt łącznika serwera proxy w chmurze, postępuj zgodnie z instrukcjami [Dodaj role systemu lokacji dla programu System Center Configuration Manager](../../core/servers/deploy/configure/add-site-system-roles.md).

#### <a name="configure-roles-for-cloud-proxy-traffic"></a>Konfigurowanie ról dla ruchu serwera proxy w chmurze

Ostatnim krokiem w konfiguracji usługi serwera Proxy w chmurze jest do konfigurowania ról systemu lokacji do akceptowania ruchu serwera proxy w chmurze. Techniczna wersja zapoznawcza 1606 tylko punkt zarządzania, punktu dystrybucji i roli punktu aktualizacji oprogramowania są obsługiwane dla usługi serwera Proxy w chmurze. Każda rola należy skonfigurować osobno.

1. W konsoli programu Configuration Manager, przejdź do **Administracja > Konfiguracja lokacji > serwery i role systemu lokacji**.
2. Kliknij serwer systemu lokacji dla roli, którą chcesz skonfigurować, czy ruch serwera proxy w chmurze.
3. Kliknij rolę, a następnie kliknij przycisk **właściwości**.
4. W arkuszu właściwości roli w obszarze połączenia klienta, wybierz **HTTPS**, zaznacz pole wyboru obok pozycji **ruchu Zezwalaj Menedżer konfiguracji serwera Proxy w chmurze**, a następnie kliknij przycisk **OK**. Powtórz te czynności dla pozostałych ról.

#### <a name="check-status-on-a-client-on-the-internet"></a>Sprawdź stan klienta w Internecie

Po skonfigurowaniu są całkowicie usługi i role, klientów wewnętrznych otrzyma lokalizacji usługi serwera Proxy w chmurze przy kolejnym żądaniu lokalizacji. Klientom informacji o lokalizacji zaktualizowane następnie może komunikować się z programem Configuration Manager w Internecie. Cykl sondowania żądań lokalizacji jest co 24 godziny. Jeśli nie chcesz czekać na żądanie zwykle zaplanowane lokalizacji, możesz wymusić żądanie przez ponowne uruchomienie usługi hosta agenta programu SMS (ccmexec.exe) na komputerze.

Po klienci mają nowych informacji o lokalizacji dla usługi serwera Proxy w chmurze, należy sprawdzić stan klientów, które nie są już w wewnętrznej sieci prywatnej, ale ma dostęp do Internetu. Można również monitorować ruch w chmurze usługi serwera Proxy, przechodząc do **Administracja > usługi w chmurze > Usługa serwera Proxy w chmurze**, wybierając usługę w okienku listy i wyświetlanie informacji o ruchu w okienku szczegółów.   

## <a name="manage_o365"></a>Zarządzanie agentem klienta usługi Office 365 w programie Configuration Manager  

Uruchamianie Technical Preview 1606, można użyć agenta klienta programu Configuration Manager ustawienie zamiast zasad grupy, aby umożliwić klientom usługi Office 365 otrzymywać aktualizacje programu Configuration Manager. Po skonfigurowaniu tego ustawienia i wdrażania aktualizacji usługi Office 365, agenta klienta programu Configuration Manager komunikuje się z agentem klienta usługi Office 365 do pobierania aktualizacji usługi Office 365 z punktu dystrybucji i zainstaluj je. Programu Configuration Manager również wykonuje spis ustawienie agenta klienta.

Aby uzyskać więcej informacji, zobacz [aktualizacji z zarządzania usługi Office 365 ProPlus](https://technet.microsoft.com/library/mt741983.aspx).

### <a name="set-the-configuration-manager-client-setting-to-manage-the-office-365-client-agent"></a>Ustawienia zarządzania agenta klienta usługi Office 365 klienta programu Configuration Manager
1.  W konsoli programu Configuration Manager kliknij **administracji** > **omówienie** > **ustawień klienta**.
2. Otwórz ustawienia odpowiedniego urządzenia, aby włączyć agenta klienta. Aby uzyskać więcej informacji na temat domyślne i niestandardowe ustawienia klienta, zobacz [sposób konfigurowania ustawień klienta w programie System Center Configuration Manager](../../core/clients/deploy/configure-client-settings.md).
3. Kliknij przycisk **aktualizacji oprogramowania** i wybierz **tak** dla **włączyć zarządzanie agenta klienta Office 365** ustawienie.  


## <a name="osdpreservedriveletter"></a>OSDPreserveDriveLetter zmienną sekwencji zadań, która została wycofana.
OSDPreserveDriveLetter zmienną sekwencji zadań, która określa, czy sekwencja zadań używa litery dysku przechwconej w pliku WIM obrazu systemu operacyjnego podczas stosowania obrazu na komputerze docelowym.
- Ta zmienna sekwencji zadań jest przestarzała w Technical Preview 1606.

Podczas wdrażania systemu operacyjnego domyślnie Instalatora systemu Windows teraz określa najlepsze literę dysku do użycia (zwykle C:). Jeśli chcesz określić inny dysk do użycia, możesz zmienić lokalizację, w kroku sekwencji zadań Zastosuj System operacyjny. Przejdź do **wybierz lokalizację, w której chcesz zastosować ten system operacyjny** wybierz pozycję **określona litera dysku logicznego**i wybierz dysk, który ma być używany. Musi być dyskiem przypisany literą, na komputerze docelowym. 

## <a name="updatesandservicing"></a>Zmiany dotyczące aktualizacji i obsługi węzła
Z Technical Preview 1606 kilka zmian wprowadzono mające zastosowanie do aktualizacji i obsługi w konsoli programu Configuration Manager:
- **Zmiana nazwy węzła:**

    W **monitorowanie** roboczym **stan obsługi lokacji** węzła została zmieniona na **aktualizacji i obsługi stanu**.
- **Więcej informacji o stanie instalacji:**

    Podczas wyświetlania stanu instalacji aktualizacji dla lokacji w konsoli są wyświetlane teraz oddzielne szczegóły następujące akcje:
    - **Pobierz** (ma zastosowanie tylko do lokacji najwyższego poziomu, w którym zainstalowano rolę systemu lokacji punktu połączenia usługi)
    - **Replikacja**
    - **Sprawdzanie wymagań wstępnych**
    - **Instalacja**

  Ponadto jest teraz bardziej szczegółowe informacje dla każdego kroku, w tym w pliku dziennika, które można wyświetlić więcej informacji.  
-   **Nową opcję, aby ponowić próbę błędy wymagań wstępnych:**

    W obu **administracji** i **monitorowanie** obszary robocze, **aktualizacje i obsługa** węzła obejmuje nowy przycisk na Wstążce o nazwie **Ignoruj ostrzeżenia dotyczące wymagań wstępnych**.

    Po zainstalowaniu aktualizacji bez użycia opcji ignorowania ostrzeżeń dotyczących wymagań wstępnych (z poziomu Kreatora aktualizacji), oraz że instalacji aktualizacji zatrzymuje się ze stanem **ostrzeżenia dotyczące wymagań wstępnych**, można wybrać **Ignoruj ostrzeżenia dotyczące wymagań wstępnych** na Wstążce, aby wyzwolić automatyczne kontynuacji tę instalację aktualizacji, który ignoruje ostrzeżenia dotyczące wymagań wstępnych.  



- **Czyszczący widok aktualizacji:**

    Po wyświetleniu **aktualizacje i obsługa** węzła, pojawi się tylko ostatnią zainstalowaną aktualizację oraz nowe aktualizacje, które są dostępne do zainstalowania. Aby wyświetlić wcześniej zainstalowane aktualizacje, kliknij przycisk Nowy **historii** przycisku, który jest wyświetlany na Wstążce.  

-   **Zmieniono nazwę opcji do produkcji wstępnej:**

    Aktualizacje i obsługa przycisku co miał nazwę **opcje klienta** teraz jest zmieniana na **promowanie klienta przedprodukcyjnego**.
