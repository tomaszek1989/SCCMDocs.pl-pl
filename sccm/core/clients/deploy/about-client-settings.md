---
title: Ustawienia klienta
titleSuffix: Configuration Manager
description: Dowiedz się więcej o domyślnych i niestandardowych ustawień kontrolowania zachowania klienta
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: f7560876-8084-4570-aeab-7fd44f4ba737
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: a60e54ffac3ae029f07c2df555e905b55ca7b0b5
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="about-client-settings-in-system-center-configuration-manager"></a>Informacje o ustawieniach klienta w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersji current branch)*

Zarządzanie wszystkimi ustawieniami klienta w konsoli programu Configuration Manager z **ustawień klienta** w węźle **administracji** obszaru roboczego. Menedżer konfiguracji jest dostarczany z zestawem ustawień domyślnych. Zmiana domyślnych ustawień klienta, te ustawienia są stosowane do wszystkich klientów w hierarchii. Można również skonfigurować niestandardowe ustawienia klienta, które zastąpią domyślne ustawienia klienta po przypisaniu do kolekcji. Aby uzyskać więcej informacji, zobacz [sposób konfigurowania ustawień klienta](../../../core/clients/deploy/configure-client-settings.md).

W poniższych sekcjach opisano ustawienia i opcje bardziej szczegółowo.  
 

## <a name="background-intelligent-transfer-service-bits"></a>Usługa inteligentnego transferu w tle (BITS)  

### <a name="limit-the-maximum-network-bandwidth-for-bits-background-transfers"></a>Ogranicz maksymalną przepustowość sieci dla transferów w tle usługi BITS
Gdy ta opcja jest **tak**, klienci używają funkcji ograniczania przepustowości usługi BITS. Aby skonfigurować inne ustawienia w tej grupie, należy włączyć to ustawienie. 

### <a name="throttling-window-start-time"></a>Godzina rozpoczęcia okna ograniczenia przepustowości
Określ czas rozpoczęcia lokalnego oknie ograniczenia przepustowości usługi BITS.  

### <a name="throttling-window-end-time"></a>Godzina zakończenia okna ograniczenia przepustowości
Określ czas zakończenia lokalnego oknie ograniczenia przepustowości usługi BITS. Jeśli czas zakończenia jest równa **godzina rozpoczęcia okna ograniczenia przepustowości**, ograniczenia przepustowości usługi BITS jest zawsze włączona.  

### <a name="maximum-transfer-rate-during-throttling-window-kbps"></a>Maksymalna szybkość transferu w oknie (KB/s) ograniczenia przepustowości
Określ maksymalną szybkość transmisji używanego przez klientów podczas okna.  

### <a name="allow-bits-downloads-outside-the-throttling-window"></a>Zezwalaj na pobieranie usługi BITS poza oknem ograniczenia przepustowości
Zezwalaj klientom na użycie oddzielnych ustawień usługi BITS poza określonym oknem.  

### <a name="maximum-transfer-rate-outside-the-throttling-window-kbps"></a>Maksymalna szybkość transferu poza oknem ograniczenia przepustowości (KB/s)
Określ maksymalną szybkość transmisji używanego przez klientów poza oknem ograniczenia przepustowości usługi BITS.  



## <a name="client-cache-settings"></a>Ustawienia pamięci podręcznej klienta

### <a name="configure-branchcache"></a>Konfiguruj usługę BranchCache
Skonfiguruj komputer kliencki [usługi Windows BranchCache](/sccm/core/plan-design/configs/support-for-windows-features-and-networks#branchcache). Aby zezwolić na buforowanie usługi BranchCache na kliencie, **Włącz usługę BranchCache** do **tak**.

- **Enable BranchCache** </br>
    Włącza funkcję BranchCache na komputerach klienckich.

- **Maksymalny rozmiar pamięci podręcznej usługi BranchCache (część procentowa dysku)** </br>
    Wartość procentowa dysku, który umożliwia usługi BranchCache do użycia. 

### <a name="configure-client-cache-size"></a>Skonfiguruj rozmiar pamięci podręcznej klienta
Pamięci podręcznej klienta programu Configuration Manager na komputerach z systemem Windows są przechowywane tymczasowe pliki służące do instalacji aplikacji i programów. Jeśli ta opcja jest ustawiona na **nr**, domyślny rozmiar to 5,120 MB.

Jeśli wybierzesz **tak**, następnie określ:
- **Maksymalny rozmiar pamięci podręcznej (MB)**
- **Maksymalny rozmiar pamięci podręcznej (procent dysku)** </br>
Rozmiar pamięci podręcznej klienta rozwijany do maksymalny rozmiar w megabajtach (MB) lub wartość procentowa dysku, ta wartość jest mniejsza. 

### <a name="enable-configuration-manager-client-in-full-os-to-share-content"></a>Włącz klienta programu Configuration Manager w pełnej wersji systemu operacyjnego, aby udostępnić zawartość
Umożliwia [elementu równorzędnego pamięci podręcznej](/sccm/core/plan-design/hierarchy/client-peer-cache) klientów programu Configuration Manager. Wybierz **tak**, a następnie określ port, przez który klient komunikuje się z komputerem równorzędnym. 
- **Port początkowego rozgłaszania sieciowego** (domyślna 8004)
- **Port pobierania zawartości z elementu równorzędnego** (domyślna 8003) </br>
Menedżer konfiguracji automatycznie konfiguruje reguł zapory systemu Windows, aby zezwolić na ten ruch. Jeśli używasz innej zapory, należy ręcznie skonfigurować reguły zezwalające na ten ruch.




## <a name="client-policy"></a>Zasady klienta  

### <a name="client-policy-polling-interval-minutes"></a>Interwał sondowania zasad klienta (minuty)

Określa częstotliwość pobierania zasad klienta przez następujących klientów programu Configuration Manager:
-   Komputery z systemem Windows (na przykład komputery stacjonarne, serwery, komputery przenośne)  
-   Urządzenia przenośne, które rejestruje programu Configuration Manager  
-   Komputery Mac  
-   Komputery z systemem Linux lub UNIX  

### <a name="enable-user-policy-on-clients"></a>Włącz zasady użytkownika na klientach

Po ustawieniu tej opcji **tak**i użyj [odnajdywania użytkownika usługi](../../../core/servers/deploy/configure/about-discovery-methods.md#bkmk_aboutUser), następnie klienci odbierają aplikacje i programy przeznaczone dla zalogowanego użytkownika.  

Katalog aplikacji otrzymuje listę oprogramowania dostępnego dla użytkowników z serwera lokacji. W związku z tym to ustawienie nie ma być **tak** dla użytkowników wyświetlić aplikacje i zażądać ich z katalogu aplikacji. Jeśli to ustawienie jest **nr**, użytkownicy korzystają z katalogu aplikacji nie będą działać następujące zachowania:  

-   Użytkownicy nie mogą instalować aplikacji widocznych w wykazie aplikacji.  

-   Użytkownicy nie widzą powiadomień dotyczących ich żądań zatwierdzenia aplikacji. Zamiast tego muszą odświeżyć katalog aplikacji i sprawdzić stan zatwierdzenia.  

-   Użytkownicy nie otrzymywali poprawek i aktualizacji aplikacji, które są publikowane w katalogu aplikacji. Użytkownicy widzą zmiany informacji o aplikacjach w katalogu aplikacji.  

-   Po usunięciu wdrożenia aplikacji, po zainstalowaniu klienta aplikacji z katalogu aplikacji, klienci będą sprawdzać, czy aplikacja jest zainstalowana na maksymalnie dwa dni.  

Ponadto, jeśli to ustawienie jest **nr**, użytkownicy nie otrzymywali wymaganych aplikacji wdrażanych dla użytkowników. Użytkownicy również nie mają inne zadania zarządzania w zasadach użytkownika.  

To ustawienie dotyczy użytkowników, gdy komputer jest w intranecie lub Internecie. Musi to być **tak** Jeśli chcesz również włączyć zasady użytkownika w Internecie.  

### <a name="enable-user-policy-requests-from-internet-clients"></a>Włącz żądania zasad użytkownika od klientów internetowych

Ustaw tę wartość na **tak** użytkownikom będą otrzymywali zasady użytkownika na komputerach opartych na internet. Również mają zastosowanie następujące wymagania:  

-   Klienta i lokację skonfigurowano do [zarządzania klientami internetowymi](/sccm/core/clients/manage/plan-internet-based-client-management) lub [brama zarządzania chmury](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway).  

-   **Włącz zasady użytkownika na klientach** jest ustawienie **tak**.  

-   Punkt zarządzania internetowego pomyślnie uwierzytelnił użytkownika za pomocą uwierzytelniania systemu Windows (Kerberos lub NTLM). Aby uzyskać więcej informacji, zobacz [uwagi dotyczące komunikacji klientów z Internetu](../../../core/plan-design/hierarchy/communications-between-endpoints.md#BKMK_clientspan).  

-   Począwszy od wersji 1710 bramy chmury zarządzania pomyślnie uwierzytelnił użytkownika za pomocą usługi Azure Active Directory. Aby uzyskać więcej informacji, zobacz [wdrażać aplikacje dostępne dla użytkowników na urządzeniach przyłączonych do usługi AD platformy Azure](\sccm\apps\deploy-use\deploy-applications#deploy-user-available-applications-on-azure-ad-joined-devices).  

Jeśli ustawisz tę opcję, **nr**, lub wszelkie poprzednie wymagania nie są spełnione, a następnie komputer połączony z Internetem tylko otrzyma zasady komputera. W tym scenariuszu użytkownicy mogli nadal widzieć, żądanie i instalowanie aplikacji z katalogu aplikacji internetowych. Jeśli to ustawienie jest **nr**, ale **Włącz zasady użytkownika na klientach** jest **tak**, użytkownicy nie otrzymywali zasad użytkownika do momentu komputer jest połączony z intranetem.  

> [!NOTE]  
>  Do zarządzania klientami internetowymi żądania zatwierdzenia aplikacji od użytkowników nie wymagają zasad użytkownika ani uwierzytelnienia użytkownika. Brama zarządzania chmura nie obsługuje żądania zatwierdzenia aplikacji.   



## <a name="cloud-services"></a>Usługi w chmurze

### <a name="allow-access-to-cloud-distribution-point"></a>Zezwalaj na dostęp do punktu dystrybucji w chmurze
Ustaw tę wartość na **tak** dla klientów w celu uzyskania zawartości z punktu dystrybucji chmury. To ustawienie nie wymaga urządzeń internetowych.

### <a name="automatically-register-new-windows-10-domain-joined-devices-with-azure-active-directory"></a>Automatycznego rejestrowania nowych urządzeń przyłączonych do domeny systemu Windows 10 w usłudze Azure Active Directory 
Po skonfigurowaniu usługi Azure Active Directory do obsługi sprzężenia hybrydowe programu Configuration Manager konfiguruje urządzenia z systemem Windows 10 dla tej funkcji. Aby uzyskać więcej informacji, zobacz [jak do skonfigurowania hybrydowego przyłączonych do usługi Azure Active Directory urządzeń](https://docs.microsoft.com/azure/active-directory/device-management-hybrid-azuread-joined-devices-setup).

### <a name="enable-clients-to-use-a-cloud-management-gateway"></a>Umożliwia klientom używać bramy zarządzania chmury
Domyślnie używają dostępne wszystkich klientów mobilnych internet [brama zarządzania chmury](/sccm/core/clients/manage/plan-cloud-management-gateway). Kiedy należy skonfigurować to ustawienie, aby przykładem **nr** to zakres użycia usługi, na przykład podczas projektu pilotażowego lub w celu ograniczenia kosztów.



##  <a name="compliance-settings"></a>Ustawienia zgodności  

### <a name="enable-compliance-evaluation-on-clients"></a>Włącz ocenę zgodności na klientach
Ustaw tę wartość na **tak** skonfigurować inne ustawienia w tej grupie.
 
### <a name="schedule-compliance-evaluation"></a>Zaplanuj ocenę zgodności
Wybierz **harmonogram** Aby utworzyć domyślny harmonogram dla konfiguracji wdrożenia linii bazowej. Ta wartość jest można skonfigurować dla każdej podstawy w **wdrażanie podstawy konfiguracji** okno dialogowe.  

### <a name="enable-user-data-and-profiles"></a>Włącz dane użytkownika i profili
Wybierz **tak** Jeśli chcesz wdrożyć [dane użytkownika i profile](../../../compliance/deploy-use/create-user-data-and-profiles-configuration-items.md) elementów konfiguracji.



## <a name="computer-agent"></a>Agent komputera  

### <a name="user-notifications-for-required-deployments"></a>Powiadomienia użytkowników w celu dokonania wymaganych wdrożeń

Aby uzyskać więcej informacji na temat następujących ustawień, zobacz [powiadomienia użytkowników w celu dokonania wymaganych wdrożeń](/sccm/apps/deploy-use/deploy-applications#user-notifications-for-required-deployments):

-   **Termin ostateczny wdrożenia powyżej 24 godzin, Przypominaj użytkownikowi co (godziny)**
-   **Wdrożenie termin ostateczny mniej niż 24 godziny, Przypominaj użytkownikowi co (godziny)** 
-   **Wdrożenia ostatecznego terminu wdrożenia poniżej 1 godziny, Przypominaj użytkownikowi co (minuty)** 

### <a name="default-application-catalog-website-point"></a>Domyślny punkt witryny sieci Web katalogu aplikacji

Configuration Manager używa tego ustawienia, aby łączyć użytkowników z katalogiem aplikacji w Centrum oprogramowania. Wybierz **witryny sieci Web zestawu** umożliwia określenie serwera obsługującego punkt witryny sieci Web katalogu aplikacji. Wprowadź jego nazwę NetBIOS lub nazwę FQDN, automatyczne wykrywanie lub określ adres URL wdrożeń dostosowanych. W większości przypadków najlepszym rozwiązaniem jest automatyczne wykrywanie, ponieważ zapewnia następujące korzyści:  

-   Jeśli witryna ma punkt witryny sieci Web katalogu aplikacji, następnie klienci automatycznie otrzymują punkt witryny sieci Web katalogu aplikacji z ich lokacji.  

-   Klient preferuje tylko HTTP serwery punktów witryny sieci Web katalogu aplikacji z obsługą protokołu HTTPS w sieci intranet. Ta funkcja pomaga w ochronie przed serwerami nieautoryzowanymi.

-   Punkt zarządzania zapewnia Klienci internetowi internetowy punkt witryny sieci Web katalogu aplikacji. Punkt zarządzania zapewnia klienci intranetowi punkt witryny sieci Web katalogu aplikacji opartych na sieci intranet.  

Automatyczne wykrywanie nie gwarantuje, że klienci otrzymają najbliższy punkt witryny sieci Web katalogu aplikacji. Użytkownik może zrezygnować z funkcji **Wykryj automatycznie** z następujących przyczyn:  

-   Użytkownik chce ręcznie skonfigurować najbliższy serwer dla klientów lub upewnij się, że nie łączą się serwerem przez wolne połączenie sieciowe.  

-   Użytkownik chce kontrolować, którzy klienci łączą się z którym serwerem. Ta konfiguracja może być do testowania wydajności lub z przyczyn biznesowych.  

-   Nie chcesz czekać do 25 godzin lub na zmianę sieci, aby klienci mogli używać innej witryny sieci Web katalogu aplikacji punktu.  

Jeśli punkt witryny sieci Web katalogu aplikacji należy określić zamiast używać automatycznego wykrywania, określ nazwę NetBIOS zamiast intranetową nazwę FQDN. Ta konfiguracja ogranicza prawdopodobieństwo, że przeglądarka sieci web monituje użytkowników o poświadczenia podczas uzyskiwania dostępu do katalogu aplikacji opartych na sieci intranet. Aby korzystać z nazwy NetBIOS, muszą być spełnione następujące warunki:  

-   Nazwa NetBIOS została określona we właściwościach punktu witryny sieci Web katalogu aplikacji.  

-   Korzystanie z usługi WINS lub wszyscy klienci znajdują się w tej samej domenie co punkt witryny sieci Web katalogu aplikacji.  

-   Skonfiguruj punkt witryny sieci Web katalogu aplikacji dla połączeń klienckich HTTP, lub skonfigurować serwer do obsługi protokołu HTTPS i certyfikatu serwera sieci web ma nazwę NetBIOS.  

Zwykle użytkownicy są monitowani o podanie poświadczeń, gdy adres URL ma nazwę FQDN, a nie adres URL jest nazwą NetBIOS. Spodziewać się użytkowników zawsze się monit, gdy łączą się przez Internet, ponieważ to połączenie musi korzystać internet nazwy FQDN. Dla klienta internetowego gdy przeglądarka sieci web monituje użytkowników o poświadczenia, upewnij się, że punkt witryny sieci Web katalogu aplikacji połączenie z kontrolerem domeny dla konta użytkownika. Ta konfiguracja umożliwia użytkownikom uwierzytelnianie przy użyciu protokołu Kerberos.  

> [!NOTE]  
>  Oto jak automatyczne wykrywanie działa:  
>   
>  Klient wysyła żądanie lokalizacji usługi do punktu zarządzania. Jeśli w tej samej lokacji, w której znajduje się klient, istnieje punkt witryny sieci Web katalogu aplikacji, serwer zostanie przekazany klientowi jako serwer, który ma być wykorzystywany jako serwer katalogu aplikacji. Gdy więcej niż jeden punkt witryny sieci Web katalogu aplikacji jest dostępna w lokacji, z włączonym protokołem HTTPS serwera mają pierwszeństwo przed serwerem, który nie jest włączony dla protokołu HTTPS. Po powyższym filtrowaniu wszyscy klienci otrzymają jeden z serwerów, które ma być używana jako katalog aplikacji. Menedżer konfiguracji nie równoważy obciążenia między wieloma serwerami. Gdy lokacja klienta nie ma punkt witryny sieci Web katalogu aplikacji, punkt zarządzania zwróci w sposób niedeterministyczny punkt witryny sieci Web katalogu aplikacji z hierarchii.  
>   
>  W przypadku klientów opartych na sieci intranet, jeśli konfigurujesz punkt witryny sieci Web katalogu aplikacji przy użyciu nazwy NetBIOS dla adresu URL katalogu aplikacji, punkt zarządzania korzysta z to. Nie używa intranetową nazwę FQDN. Dla klientów internetowych punkt zarządzania uzyskuje internet FQDN tylko do klienta.  
>   
>  Klient wysyła to żądanie lokalizacji usługi co 25 godzin lub po wykryciu zmiany sieci. Na przykład jeśli klient jest przenoszony z sieci intranet do Internetu, to zmiany sieci. Jeśli klient następnie klient zlokalizuje punkt zarządzania internetowego, punkt zarządzania internetowego zapewnia internetowych serwerów punktu witryny sieci Web katalogu aplikacji do klientów.  

### <a name="add-default-application-catalog-website-to-internet-explorer-trusted-sites-zone"></a>Dodaj domyślną witrynę sieci Web katalogu aplikacji do strefy Zaufane witryny programu Internet Explorer

Jeśli ta opcja jest **tak**, klient automatycznie dodaje bieżący adres URL witryny sieci Web katalogu aplikacji domyślne do strefy Zaufane witryny programu Internet Explorer.  

To ustawienie zapewnia, że tryb chroniony programu Internet Explorer jest wyłączony. Jeśli tryb chroniony jest włączony, klient programu Configuration Manager nie może być mógł instalować aplikacji z katalogu aplikacji. Domyślnie strefy Zaufane witryny obsługuje również logowanie użytkownika do katalogu aplikacji, która wymaga uwierzytelniania systemu Windows.  

Jeśli opuścisz tę opcję **nr**, klientów programu Configuration Manager nie można instalować aplikacji z katalogu aplikacji. Alternatywną metodą jest konfigurowania tych ustawień programu Internet Explorer w innej strefie dla adresu URL katalogu aplikacji używanego przez klientów.  

> [!NOTE]  
>  Zawsze, gdy programu Configuration Manager dodaje domyślny adres URL katalogu aplikacji do strefy Zaufane witryny, programu Configuration Manager spowoduje usunięcie wszelkich poprzednio dodany adres URL katalogu aplikacji.  
>   
>  Jeśli adres URL został już określony w jednej ze stref zabezpieczeń, programu Configuration Manager nie może dodać adresu URL. Przy takim scenariuszu użytkownik musi usunąć adres URL z innej strefy lub ręcznie skonfigurować wymagane ustawienia programu Internet Explorer.  

### <a name="allow-silverlight-applications-to-run-in-elevated-trust-mode"></a>Zezwalaj na uruchamianie w trybie podwyższonego zaufania aplikacji Silverlight

To ustawienie musi być **tak** użytkownikom korzystania z katalogu aplikacji.  

Zmiana tego ustawienia będzie wprowadzona po użytkowników obok załadowaniu przeglądarki lub Odśwież swoje obecnie otwartego okna przeglądarki.  

Aby uzyskać więcej informacji o tym ustawieniu, zobacz [certyfikatów dla programu Microsoft Silverlight 5 i tryb podwyższonego zaufania wymagany przez katalog aplikacji](../../../apps/plan-design/security-and-privacy-for-application-management.md#BKMK_CertificatesSilverlight5).  

### <a name="organization-name-displayed-in-software-center"></a>Nazwa organizacji wyświetlana w Centrum oprogramowania

Wpisz nazwę wyświetlaną użytkownikom w Centrum oprogramowania. Te informacje o znakowaniu ułatwiają użytkownikom zidentyfikowanie tej aplikacji jako pochodzącej z zaufanego źródła.  

### <a name="use-new-software-center"></a>Użyj nowego centrum oprogramowania

Jeśli ustawisz to **tak**, a następnie wszystkie komputery klienckie używają programu Software Center. Program Software Center zawiera aplikacje dostępne dla użytkowników, które były wcześniej dostępne tylko w katalogu aplikacji. Katalog aplikacji wymaga programu Silverlight, która nie jest wymagane w przypadku programu Software Center. Począwszy od programu Configuration Manager 1802 ustawieniem domyślnym jest **tak**.  

Punkt witryny sieci Web katalogu aplikacji i usług sieci web katalogu aplikacji punktu systemu lokacji, które role są nadal wymagane dla aplikacje dostępne dla użytkowników, które mają być widoczne w Centrum oprogramowania.  

Aby uzyskać więcej informacji, zobacz [planowanie i Konfigurowanie zarządzania aplikacjami](../../../apps/plan-design/plan-for-and-configure-application-management.md).  

### <a name="enable-communication-with-health-attestation-service"></a>Włącz komunikację z usługą zaświadczania o kondycji

Ustaw tę wartość na **tak** dla urządzeń z systemem Windows 10 do użycia [zaświadczania o kondycji](/sccm/core/servers/manage/health-attestation). Gdy to ustawienie jest włączone, poniższe ustawienie jest również dostępny do konfiguracji.

### <a name="use-on-premises-health-attestation-service"></a>Użyj lokalnej usługi zaświadczania o kondycji

Ustaw tę wartość na **tak** urządzeń przy użyciu usługi lokalnej. Ustaw **nr** dla urządzeń, aby używać usług chmurowych firmy Microsoft.  

### <a name="install-permissions"></a>Uprawnienia do instalacji

> [!IMPORTANT]  
>  To ustawienie dotyczy katalogu aplikacji i Centrum oprogramowania. To ustawienie nie ma żadnego efektu, jeśli użytkownicy korzystają z portalu firmy.  

Konfigurowanie sposobu inicjowania instalacji oprogramowania, aktualizacji oprogramowania oraz sekwencji zadań przez użytkowników:  

-   **Wszyscy użytkownicy**: Użytkownicy z dowolnymi uprawnieniami oprócz gościa uprawnień.  

-   **Tylko Administratorzy**: Użytkownicy muszą być członkiem lokalnej grupy administratorów.  

-   **Tylko administratorzy i użytkownicy podstawowi**: Użytkowników musi być członkiem lokalnej grupy administratorów lub użytkownikiem podstawowym komputera.  

-   **Użytkownicy nie**: Użytkownicy zalogowany na komputerze klienckim nie mogą inicjować instalację oprogramowania, aktualizacji oprogramowania i sekwencji zadań. Wdrożenia wymagane dla komputera są zawsze instalować w terminie ostatecznym. Użytkownicy nie mogą inicjować instalację oprogramowania z katalogu aplikacji lub Centrum oprogramowania.  

### <a name="suspend-bitlocker-pin-entry-on-restart"></a>Zawieś wprowadzanie numeru PIN funkcji BitLocker przy ponownym uruchomieniu

Jeśli komputery wymagają wprowadzania numeru PIN funkcji BitLocker, ta opcja pomija konieczność podania numeru PIN, po ponownym uruchomieniu komputera po zainstalowaniu oprogramowania.  

-   **Zawsze**: Configuration Manager tymczasowo zawiesi funkcji BitLocker po zainstalowaniu oprogramowania wymagającego ponownego uruchomienia i zainicjował ponowne uruchomienie komputera. To ustawienie ma zastosowanie tylko do ponownego uruchomienia komputera zainicjowanych przez program Configuration Manager. To ustawienie nie wstrzymuje wymagania podania numeru PIN funkcji BitLocker po ponownym uruchomieniu komputera przez użytkownika. Wymaganie wprowadzania numeru PIN funkcji BitLocker zostanie wznowione po uruchomieniu systemu Windows.

-   **Nigdy nie**: Menedżer konfiguracji nie zawiesił funkcji BitLocker po zainstalowaniu oprogramowania wymagającego ponownego uruchomienia komputera. Przy takim scenariuszu instalowanie oprogramowania nie zostanie zakończone przed wprowadzeniem numeru PIN przez użytkownika w celu ukończenia standardowego procesu uruchamiania i załadowania systemu Windows.

### <a name="additional-software-manages-the-deployment-of-applications-and-software-updates"></a>Wdrażanie aplikacji i aktualizacji oprogramowania jest zarządzane dodatkowe oprogramowanie

Włącz tę opcję tylko wtedy, gdy jeden z następujących warunków:  

-   Użytkownik korzysta z rozwiązania dostawcy wymagającego, aby to ustawienie było włączone.  

-   Korzystając z programu Configuration Manager zestaw software development kit (SDK) w celu zarządzania powiadomieniami agentem klienta i instalacji aplikacji i aktualizacji oprogramowania.  

> [!WARNING]  
>  Jeśli wybierzesz tę opcję, jeśli żadna z tych warunków zastosować, nie można zainstalować klienta aktualizacji oprogramowania i wymaganych aplikacji. To ustawienie nie uniemożliwić użytkownikom instalowanie aplikacji z katalogu aplikacji lub pakietów, programów i sekwencji zadań instalacji.  

### <a name="powershell-execution-policy"></a>Zasady wykonywania programu PowerShell

Skonfiguruj sposób klientów programu Configuration Manager może uruchamiać skrypty programu Windows PowerShell. Skrypty te można użyć do wykrywania w elementach konfiguracji ustawień zgodności. Może także wysłać skrypty w ramach wdrożenia jako skrypty standardowe.  

-   **Obejście**: Klient programu Configuration Manager pomija konfigurację programu Windows PowerShell na komputerze klienckim, co umożliwia uruchamianie niepodpisanych skryptów.  

-   **Ograniczone**: Klient programu Configuration Manager korzysta z bieżącej konfiguracji programu PowerShell na komputerze klienckim. Ta konfiguracja Określa, czy można uruchamiać niepodpisane skrypty.  

-   **Wszystko podpisane**: Klient programu Configuration Manager uruchamia skrypty tylko wtedy, gdy podpisała ich zaufanego wydawcę. To ograniczenie obowiązuje niezależnie od bieżącej konfiguracji programu PowerShell na komputerze klienckim.  

Ta opcja wymaga co najmniej programu Windows PowerShell w wersji 2.0. Wartość domyślna to **wszystko podpisane**.  

> [!TIP]  
>  Jeśli nie ze względu na to ustawienie klienta uruchomienie niepodpisanych skryptów, program Configuration Manager zaraportuje ten błąd w następujący sposób:  
>   
> -   **Monitorowanie** w obszarze roboczym w konsoli wyświetlane identyfikator błąd stanu wdrożenia **0x87D00327**. Wyświetla również opis **skrypt nie jest podpisany**.  
> -   Raporty zawierają typ błędu **błąd odnajdywania**. Raporty zawierają albo kodu błędu, a następnie **0x87D00327** i opis **skrypt nie jest podpisany**, lub kod błędu **0x87D00320** i opis  **host skryptów nie został jeszcze zainstalowany**. Przykładowy raport jest: **Szczegóły błędów elementów konfiguracji w linii bazowej konfiguracji dla zasobu**.  
> -   **DcmWmiProvider.log** pliku wyświetli komunikat **skrypt nie jest podpisany (błąd: 87D 00327; Źródło: CCM)**.  

### <a name="show-notifications-for-new-deployments"></a>Pokaż powiadomienia o nowych wdrożeniach

Wybierz **tak** powiadomienia w przypadku wdrożeń dostępnych dla mniej niż tydzień mają być wyświetlane. Ten komunikat jest wyświetlany zawsze, gdy agent klienta uruchamia.

### <a name="disable-deadline-randomization"></a>Wyłącz losowe generowanie terminu ostatecznego

Po upływie ostatecznego terminu wdrożenia to ustawienie określa, czy klient stosuje maksymalnie dwugodzinne opóźnienie aktywacji w celu zainstalowania wymaganych aktualizacji oprogramowania. Opóźnienie aktywacji jest domyślnie wyłączone.  

W scenariuszach infrastruktury pulpitu wirtualnego (VDI) to opóźnienie pomaga w rozłożeniu przetwarzania procesora CPU i transfer danych do komputera hosta o wiele maszyn wirtualnych. Nawet wtedy, gdy infrastruktura VDI nie jest używana, posiadanie wielu klientów instalowanie te same aktualizacje, w tym samym czasie może to zwiększyć użycie procesora CPU na serwerze lokacji. To zachowanie można również spowolnić punkty dystrybucji i znacznie zmniejszyć dostępną przepustowość sieci.  

Jeśli klienci muszą zostać zainstalowane wymagane aktualizacje oprogramowania w terminie ostatecznym wdrożenia bez opóźnień, a następnie skonfiguruj to ustawienie, aby **tak**. 

### <a name="grace-period-for-enforcement-after-deployment-deadline-hours"></a>Okres prolongaty wymuszania po wdrożenia terminu wdrożenia (godziny)

Jeśli chcesz umożliwić użytkownikom więcej czasu, aby zainstalować wymaganej aplikacji lub wdrożenia aktualizacji oprogramowania po upływie terminu, ustaw tę wartość na **tak**. Tego okresu prolongaty jest wyłączona na dłuższy czas komputera, a użytkownik chce zainstalować wielu aplikacji lub wdrożenia aktualizacji. Na przykład to ustawienie jest przydatne, jeśli użytkownik zwraca z urlopu i oczekuje na przez długi czas, gdy klient jest instalowany wdrożenia aplikacji zaległe. 

Ustaw okres prolongaty 1 do 120 godzin. Użyj tego ustawienia, oraz właściwość wdrożenia **Opóźnij wymuszenie dotyczące tego wdrożenia zgodnie z preferencjami użytkownika**. Aby uzyskać więcej informacji, zobacz [wdrażania aplikacji](/sccm/apps/deploy-use/deploy-applications).


##  <a name="computer-restart"></a>Ponowne uruchomienie komputera  
Następujące ustawienia musi być krótszy czas trwania od najkrótszego okna obsługi zastosowane do komputera.  

-   **Wyświetl tymczasowe powiadomienie dla użytkownika, określające czas przed wylogowaniem lub komputer uruchamia ponownie (w minutach)**
-   **Wyświetl okno dialogowe, którego użytkownik nie może zamknąć, wyświetlające odliczanie przed wylogowaniem użytkownika lub ponownego uruchomienia komputera (minuty)**

Aby uzyskać więcej informacji o korzystaniu z okien obsługi, zobacz [Używanie okien obsługi w programie System Center Configuration Manager](../../../core/clients/manage/collections/use-maintenance-windows.md).



## <a name="delivery-optimization"></a>Optymalizacja dostarczania

<!-- 1324696 -->
Grupy granic w programie Configuration Manager służy do definiowania i uregulowanie dystrybucji zawartości w sieci firmowej i biurach zdalnych. [Optymalizacja dostarczania Windows](/windows/deployment/update/waas-delivery-optimization) jest oparta na chmurze, peer-to-peer technologii do udostępniania zawartości między urządzeniami z systemem Windows 10. Począwszy od wersji 1802 Konfigurowanie optymalizacji dostarczania do grup granic udostępniania zawartości między elementami równorzędnymi.

 > [!Note]
 > Optymalizacja dostarczania jest dostępna tylko na klientów systemu Windows 10

### <a name="use-configuration-manager-boundary-groups-for-delivery-optimization-group-id"></a>Grupy granic Użyj Menedżera konfiguracji dla Identyfikatora grupy optymalizacji dostarczania
 Wybierz **tak** dotyczyć identyfikator grupy granic jako identyfikator grupy optymalizacji dostarczania na kliencie. Gdy klient komunikuje się z usługą w chmurze optymalizacji dostarczania, używa tego identyfikatora można zlokalizować elementów równorzędnych o żądanej zawartości. 



##  <a name="endpoint-protection"></a>Program Endpoint Protection  
>  [!Tip]   
> Oprócz poniższych informacji, można znaleźć szczegółowe informacje o użyciu ustawień klienta programu Endpoint Protection w [przykładowy scenariusz: Używanie programu System Center Endpoint Protection do ochrony komputerów przed złośliwym oprogramowaniem w programie System Center Configuration Manager](/sccm/protect/deploy-use/scenarios-endpoint-protection).

### <a name="manage-endpoint-protection-client-on-client-computers"></a>Zarządzanie klientem programu Endpoint Protection na komputerach klienckich

Wybierz **tak** Jeśli chcesz zarządzać istniejącymi klientami programu Endpoint Protection i usługi Windows Defender na komputerach w hierarchii.  

Wybierz tę opcję, jeśli został już zainstalowany klient programu Endpoint Protection i chcesz, możesz nim zarządzać za pomocą programu Configuration Manager. Ta instalacja oddzielne obejmuje skryptową procesu, który używa Menedżera konfiguracji aplikacji lub pakietów i programów. Począwszy od programu Configuration Manager 1802 urządzeń z systemem Windows 10 nie musi być zainstalowany agent programu Endpoint Protection. Jednak te urządzenia będą nadal potrzebujesz **klienta zarządzania Endpoint Protection na komputerach klienckich** włączone. <!--503654-->

### <a name="install-endpoint-protection-client-on-client-computers"></a>Zainstaluj klienta programu Endpoint Protection na komputerach klienckich

Wybierz **tak** Aby zainstalować i włączyć klienta programu Endpoint Protection na komputerach klienckich, których klient nie jest już uruchomiony. Począwszy od programu Configuration Manager 1802 klientów systemu Windows 10 nie musi być zainstalowany agent programu Endpoint Protection.  

> [!NOTE]  
>  Jeśli jest już zainstalowany klient programu Endpoint Protection, wybierając **nr** nie powoduje odinstalowania klienta programu Endpoint Protection. Aby odinstalować klienta programu Endpoint Protection, **klienta zarządzania Endpoint Protection na komputerach klienckich** ustawienia klienta dotyczącego **nr**. Następnie należy wdrożyć pakiet i program, aby odinstalować klienta programu Endpoint Protection.  

### <a name="automatically-remove-previously-installed-antimalware-software-before-endpoint-protection-is-installed"></a>Automatycznie usuwaj wcześniej zainstalowane ochrony przed złośliwym oprogramowaniem, przed zainstalowaniem programu Endpoint Protection

Ustaw tę wartość na **tak** dla klienta programu Endpoint Protection spróbować odinstalować aplikacje innych ochrony przed złośliwym oprogramowaniem. Wielu klientów ochrony przed złośliwym kodem na tym samym urządzeniu mogą powodować konflikt i mieć wpływ na wydajność systemu.

### <a name="allow-endpoint-protection-client-installation-and-restarts-outside-maintenance-windows-maintenance-windows-must-be-at-least-30-minutes-long-for-client-installation"></a>Zezwalaj klienta programu Endpoint Protection instalacji oraz jego ponowne uruchamianie poza oknami obsługi. Okna obsługi muszą mieć przynajmniej 30 minut dla instalacji klienta

Ustaw tę wartość na **tak** zastąpić zachowania typowej instalacji z okien obsługi. To ustawienie spełnia wymagania biznesowe priorytetu konserwacji systemu ze względów bezpieczeństwa. 

### <a name="for-windows-embedded-devices-with-write-filters-commit-endpoint-protection-client-installation-requires-restarts"></a>W przypadku urządzeń Windows Embedded z filtrami zapisu należy zatwierdzić instalację klienta programu Endpoint Protection (wymaga ponownego uruchomienia)

Wybierz **tak** wyłączyć filtr zapisu na urządzeniu Windows Embedded, a następnie ponownie uruchomić urządzenie. Ta akcja zatwierdzenie instalacji na urządzeniu.  

Jeśli wybierzesz **nr**, klient jest instalowany na tymczasowej nakładce, która usuwa po ponownym uruchomieniu urządzenia. W tym scenariuszu klient programu Endpoint Protection nie pełni instaluje aż inna instalacja zatwierdza zmiany na urządzeniu. Ta konfiguracja jest ustawieniem domyślnym.  

### <a name="suppress-any-required-computer-restarts-after-the-endpoint-protection-client-is-installed"></a>Pomiń wszystkie wymagane ponowne uruchomienie komputera po zainstalowaniu klienta programu Endpoint Protection

Wybierz **tak** pominąć ponowne uruchomienie komputera po zainstalowaniu klienta programu Endpoint Protection.  

> [!IMPORTANT]  
>  Jeśli klient programu Endpoint Protection wymaga ponownego uruchomienia komputera, a to ustawienie jest **nr**, następnie komputer zostanie ponownie uruchomiony niezależnie od skonfigurowanych okien obsługi.  

### <a name="allowed-period-of-time-users-can-postpone-a-required-restart-to-complete-the-endpoint-protection-installation-hours"></a>Dozwolony okres czasu, użytkownicy mogą odłożyć ponowne uruchomienie w celu ukończenia instalacji programu Endpoint Protection (godziny)

Jeśli konieczne jest ponowne uruchomienie komputera, po zainstalowaniu klienta programu Endpoint Protection, to ustawienie określa liczbę godzin, który użytkownicy mogą odłożyć ponowne uruchomienie. To ustawienie wymaga, aby ustawienie **Pomiń wszystkie wymagane ponowne uruchomienie komputera po zainstalowaniu klienta programu Endpoint Protection** jest **nr**.  

### <a name="disable-alternate-sources-such-as-microsoft-windows-update-microsoft-windows-server-update-services-or-unc-shares-for-the-initial-definition-update-on-client-computers"></a>Wyłącz źródła alternatywne (takie jak Microsoft Windows Update, Microsoft Windows Server Update Services lub udziały UNC) dla wstępnej aktualizacji definicji na komputerach klienckich

Wybierz **tak** Jeśli program Configuration Manager do zainstalowania wyłącznie wstępną aktualizację definicji na komputerach klienckich. To ustawienie może być przydatne uniknąć niepotrzebnych połączeń sieciowych i zmniejszenia przepustowości sieci, podczas początkowej instalacji aktualizacji definicji.  



##  <a name="enrollment"></a>Rejestrowanie

### <a name="polling-interval-for-mobile-device-legacy-clients"></a>Interwał sondowania dla starszych klientów urządzeń przenośnych
Wybierz **Ustaw interwał** Aby określić czas, w minutach lub godzinach, które starszych urządzeń przenośnych sondowania zasad. Urządzenia te obejmują platformach, na przykład systemu Windows CE, Mac OS X i Unix lub Linux.

### <a name="polling-interval-for-modern-devices-minutes"></a>Interwał sondowania dla nowoczesnych urządzeń (w minutach)
Wprowadź liczbę minut nowoczesnych urządzeń sondowania zasad. To ustawienie dotyczy urządzeń z systemem Windows 10, które są zarządzane przy użyciu lokalnego zarządzania urządzeniami przenośnymi.

### <a name="allow-users-to-enroll-mobile-devices-and-mac-computers"></a>Zezwalaj użytkownikom na rejestrację urządzeń przenośnych i komputerów Mac.
Aby włączyć oparta na użytkowniku rejestracji starszych urządzeń, ustaw tę wartość na **tak**, a następnie skonfiguruj następujące ustawienia:

-   **Profil rejestracji** </br>
Wybierz **Ustaw profil** do tworzenia lub wybierz profil rejestracji. Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień klienta dla rejestracji](/sccm/core/clients/deploy/deploy-clients-to-macs#configure-client-settings-for-enrollment).

### <a name="allow-users-to-enroll-modern-devices"></a>Zezwalaj użytkownikom na rejestrowanie nowoczesnych urządzeń
Aby włączyć oparta na użytkowniku rejestracji nowoczesnych urządzeń, ustaw tę wartość na **tak**, a następnie skonfiguruj następujące ustawienia:

-   **Profil rejestracji nowoczesnego urządzenia** </br>
Wybierz **Ustaw profil** do tworzenia lub wybierz profil rejestracji. Aby uzyskać więcej informacji, zobacz [Utwórz profil rejestracji, który pozwala użytkownikom na rejestrowanie nowoczesnych urządzeń](/sccm/mdm/get-started/set-up-device-enrollment-on-premises-mdm#bkmk_createProf).



##  <a name="hardware-inventory"></a>Spis sprzętu  

### <a name="enable-hardware-inventory-on-clients"></a>Włącz spis sprzętu na klientach

Domyślnie to ustawienie jest **tak**. Aby uzyskać więcej informacji, zobacz [wprowadzenie do spisu sprzętu](/sccm/core/clients/manage/inventory/introduction-to-hardware-inventory).

### <a name="hardware-inventory-schedule"></a>Harmonogram spisu sprzętu

Wybierz **harmonogram** Aby dostosować częstotliwość cyklu klienci uruchamiali spisu sprzętu. Domyślnie ten cykl występuje co siedem dni.

### <a name="maximum-random-delay-minutes"></a>Maksymalne opóźnienie losowe (w minutach)

Określ maksymalną liczbę minut dla klienta programu Configuration Manager wygenerować losowy spisu sprzętu cykl ze zdefiniowanego harmonogramu. Losowe przez wszystkich klientów pomaga przetwarzanie spisu Równoważenie obciążenia na serwerze lokacji. Można określić dowolną wartość z zakresu od 0 do 480 minut. Domyślnie ta wartość jest równa 240 minut (4 godziny).

### <a name="maximum-custom-mif-file-size-kb"></a>Maksymalny rozmiar niestandardowego pliku MIF (KB)

Określ maksymalny rozmiar w kilobajtach (KB), dozwoloną dla każdego niestandardowego pliku Management Information Format (MIF), który klient zbiera podczas cyklu tworzenia spisu sprzętu. Agent inwentaryzacji sprzętu programu Configuration Manager nie może przetwarzać niestandardowe pliki MIF o większym rozmiarze. Można określić o rozmiarze 1 KB do 5,120 KB. Wartością domyślną jest 250 KB. To ustawienie nie wpływa na rozmiar standardowego pliku danych zapasów sprzętu.  

> [!NOTE]  
>  To ustawienie jest dostępne tylko w domyślnych ustawieniach klienta.  

### <a name="hardware-inventory-classes"></a>Klasy spisu sprzętu

Wybierz **Ustaw klasy** rozszerzyć informacje o sprzęcie zbierane od klientów bez konieczności ręcznego modyfikowania pliku sms_def.mof. Aby uzyskać więcej informacji, zobacz [jak skonfigurować spis sprzętu](../../../core/clients/manage/inventory/configure-hardware-inventory.md).  

### <a name="collect-mif-files"></a>Zbierz pliki MIF

To ustawienie umożliwia określenie, czy do zbierania plików MIF z klientów programu Configuration Manager podczas tworzenia spisu sprzętu.  

Plik MIF mają zostać zebrane przez spis sprzętu musi być w poprawnej lokalizacji na komputerze klienckim. Domyślnie pliki znajdują się w następujących ścieżkach:  

-   **Pliki IDMIF** powinien znajdować się w folderze Windows\System32\CCM\Inventory\Idmif. 

-   **Pliki NOIDMIF** powinien znajdować się w folderze Windows\System32\CCM\Inventory\Noidmif.

> [!NOTE]  
>  To ustawienie jest dostępne tylko w domyślnych ustawieniach klienta.

   

##  <a name="metered-internet-connections"></a>Mierzonych połączeń internetowych  
 Zarządzanie systemem Windows 8 i nowszych komputerach wykorzystania mierzonych połączeń internetowych do komunikowania się z programem Configuration Manager. Internetowi czasem naliczają opłaty wg ilości danych, które są wysyłane i odbierane z mierzonego połączenia internetowego.  

> [!NOTE]  
>  Skonfigurowane ustawienie klienta nie jest stosowane w następujących scenariuszach:  
>   
> -   Jeśli komputer znajduje się na połączenie danych mobilnych, klienta programu Configuration Manager wykonuje wszystkie zadania, które wymagają danych do przeniesienia do lokacji programu Configuration Manager.  
> -   Jeśli właściwości połączenia sieciowego systemu Windows są skonfigurowane jako nietaryfowe, klienta programu Configuration Manager zachowuje się tak, jakby połączenie jest nietaryfowe i transferuje dane do lokacji.  

### <a name="client-communication-on-metered-internet-connections"></a>Komunikacja klientów w mierzonych połączeń internetowych

Wybierz jedną z następujących opcji dla tego ustawienia:  

-   **Zezwalaj na**: Cała komunikacja z klientem są dozwolone przez taryfowe połączenie internetowe, chyba że urządzenie klienckie korzysta z połączenia danych w roamingu.  

-   **Limit**: Wyłącznie następująca komunikacja z klientem są dozwolone przez taryfowe połączenie internetowe:  

    -   Pobieranie zasad klienta  

    -   Komunikaty o stanie klienta, które będą wysłane do lokacji  

    -   Żądania instalacji oprogramowania wynikające z korzystania z katalogu aplikacji  

    -   Wymagane wdrożenia (po osiągnięciu ostatecznego terminu instalacji)  

    > [!IMPORTANT]  
    >  Klient zawsze zezwala na instalacje oprogramowania z programu Software Center ani katalogu aplikacji, niezależnie od Internetu naliczane ustawienia połączenia.  

    Jeśli klienta osiągnie limitu transferu danych mierzonego połączenia internetowego, klient nie próbuje nawiązać połączenia z lokacji programu Configuration Manager.  

-   **Blok**: Klient programu Configuration Manager nie będzie próbował komunikować się z lokacji programu Configuration Manager, gdy znajduje się w mierzonego połączenia internetowego. Jest to opcja domyślna.  



##  <a name="power-management"></a>Zarządzanie energią  

### <a name="allow-power-management-of-devices"></a>Zezwalaj na zarządzanie zasilaniem urządzeń

Ustaw tę wartość na **tak** umożliwienie zarządzania energią na komputerach klienckich. Aby uzyskać więcej informacji, zobacz [wprowadzenie do zarządzania energią](/sccm/core/clients/manage/power/introduction-to-power-management).

### <a name="allow-users-to-exclude-their-device-from-power-management"></a>Zezwalaj użytkownikom na wykluczanie swoich urządzeń z zarządzania zasilaniem

Wybierz **tak** aby umożliwić użytkownikom w programie Software Center wykluczenie ich komputera ze skonfigurowanych ustawień zarządzania energią.  

### <a name="enable-wake-up-proxy"></a>Włącz serwer proxy wznawiania

Określ **tak** aby uzupełnić ustawienie funkcji Wake On LAN lokacji, jeżeli została skonfigurowana dla pakietów emisji pojedynczej.  

Aby uzyskać więcej informacji o serwerze proxy wznawiania, zobacz [planowanie sposobu wznawiania działania klientów w programie System Center Configuration Manager](../../../core/clients/deploy/plan/plan-wake-up-clients.md).  

> [!WARNING]  
>  Nie należy włączać serwera proxy wznawiania w sieci produkcyjnej bez wcześniejszego zrozumienia sposobu jego działania i oceny w środowisku testowym.  

Następnie skonfiguruj następujące dodatkowe ustawienia, zgodnie z potrzebami:

-   **Numer portu serwera proxy wznawiania (UDP)**  </br>
         Numer portu używanego przez klientów do wysyłania pakietów wznawiania do komputerów w stanie uśpienia. Zachowaj domyślny port 25536 lub zmienić numer na wybraną wartość.  

-   **Numer portu funkcji Wake On LAN (UDP)** </br> 
         Należy zachować wartość domyślną 9, chyba że zmieniono numer portu Wake On LAN (UDP) na **porty** kartę witryny **właściwości**.  

    > [!IMPORTANT]  
    >  Ten numer musi być zgodny z wartością w oknie **Właściwości**lokacji. W przypadku zmiany tego numeru w jednym miejscu, nie jest aktualizowana w innym miejscu.  

-   **Wyjątek zapory systemu Windows Defender dla serwera proxy wznawiania** </br>
         Klient programu Configuration Manager automatycznie konfiguruje numer portu serwera proxy wznawiania na urządzeniach, na których działa Zapora systemu Windows Defender. Wybierz **Konfiguruj** do określania profilów żądanego zaporą.

    Jeżeli na klientach działa inna zapora, należy ręcznie skonfigurować go, aby umożliwić **numer portu serwera proxy wznawiania (UDP)**.  
        
-   **Prefiksy IPv6, jeśli jest to wymagane przez DirectAccess lub inne pośredniczące urządzenia sieciowe. Użyj przecinka, aby określić wiele wpisów** </br>
        Wprowadź niezbędne prefiksów IPv6 dla serwera proxy wznawiania działa w sieci.



##  <a name="remote-tools"></a>Zdalne narzędzia  

### <a name="enable-remote-control-on-clients-and-firewall-exception-profiles"></a>Włącz zdalne sterowanie na klientach i profile wyjątków zapory

Wybierz **Konfiguruj** do włączenia tej funkcji zdalnego sterowania programu Configuration Manager. Opcjonalnie skonfigurować ustawienia zapory, aby umożliwić zdalne sterowanie do pracy na komputerach klienckich.  

Zdalne sterowanie jest domyślnie wyłączone.  

> [!IMPORTANT]  
>  Jeżeli ustawienia zapory nie zostaną skonfigurowane, zdalne sterowanie może nie działać prawidłowo.  

### <a name="users-can-change-policy-or-notification-settings-in-software-center"></a>Użytkownicy mogą zmieniać zasady lub ustawienia powiadomień w programie Software Center

Wybierz, czy użytkownicy mogą zmieniać opcje zdalnego sterowania z programu Software Center.  

### <a name="allow-remote-control-of-an-unattended-computer"></a>Zezwalaj na zdalne sterowanie komputerem nienadzorowanym

Wybierz, czy administrator może użyć sterowania zdalnego dostępu do komputera klienta, który jest wylogowanego lub zablokowanego. Tylko zalogowanymi i odblokowanymi komputer można sterować zdalnie, gdy to ustawienie jest wyłączone.  

### <a name="prompt-user-for-remote-control-permission"></a>Monituj użytkownika o zezwolenie na zdalne sterowanie

Wybierz, czy komputer kliencki pokazuje komunikat z pytaniem o zezwolenie użytkownika przed zezwoleniem na sesję zdalnego sterowania.  

### <a name="prompt-user-for-permission-to-transfer-content-from-shared-clipboard"></a>Monituj użytkownika o zgodę na przesyłanie zawartości z udostępnionego Schowka

Zezwalaj użytkownikom możliwość zaakceptowania lub odrzucenia transferu plików przed przesyłania zawartości z udostępnionego Schowka podczas sesji zdalnego sterowania. Użytkownicy potrzebują tylko można udzielić uprawnienia raz na sesji i Podgląd ma możliwość udzielenia sobie uprawnień, aby kontynuować transfer plików.

### <a name="grant-remote-control-permission-to-local-administrators-group"></a>Przyznaj uprawnienie zdalne sterowanie do lokalnej grupy administratorów

Wybierz, czy Administratorzy lokalni na serwerze inicjującym połączenie zdalnego sterowania mogą nawiązywać sesje zdalnego sterowania na komputerach klienckich.  

### <a name="access-level-allowed"></a>Dozwolony poziom dostępu

Określ poziom dostępu zdalnego sterowania. Wybierz jedną z następujących ustawień:  
- **Brak dostępu**
- **Wyświetl tylko**
- **Pełna kontrola**  

### <a name="permitted-viewers-of-remote-control-and-remote-assistance"></a>Dopuszczone podglądy zdalnego sterowania i pomocy zdalnej

Wybierz **Ustaw podglądy** można określić nazwy użytkowników systemu Windows, którzy mogą nawiązywać sesje zdalnego sterowania na komputerach klienckich.  

### <a name="show-session-notification-icon-on-taskbar"></a>Pokaż ikonę powiadomienia sesji na pasku zadań

Skonfiguruj to ustawienie, aby **tak** ikona na pasku zadań systemu Windows klienta wskazująca aktywną sesję zdalnego sterowania.  

### <a name="show-session-connection-bar"></a>Pokaż pasek połączenia sesji

Ustaw tę wartość na **tak** pokazanie pasek połączenia sesji wysokiej widoczności na klientach, aby wskazać aktywną sesję zdalnego sterowania.  

### <a name="play-a-sound-on-client"></a>Odtwórz dźwięk na kliencie

Ustaw, aby użyć dźwięku sygnalizującego, kiedy sesja zdalnego sterowania jest aktywna na komputerze klienckim. Wybierz jedną z następujących opcji:
- **Brak dźwięku**
- **Początku i wysyłania sesji** (ustawienie domyślne)
- **Wielokrotnie podczas sesji**  

### <a name="manage-unsolicited-remote-assistance-settings"></a>Zarządzaj ustawieniami nieżądanej pomocy zdalnej

Skonfiguruj to ustawienie, aby **tak** aby umożliwić programowi Configuration Manager Zarządzanie sesjami nieżądanej pomocy zdalnej.  

W sesji nieżądanej pomocy zdalnej użytkownika na komputerze klienckim nie wysyłanie żądań pomocy do zainicjowania sesji.  

### <a name="manage-solicited-remote-assistance-settings"></a>Zarządzaj ustawieniami pomocy zdalnej na żądanie

Ustaw tę wartość na **tak** aby umożliwić programowi Configuration Manager Zarządzanie sesjami pomocy zdalnej na żądanie.  

W sesji Pomocy zdalnej na żądanie użytkownika na komputer kliencki wysłał żądanie do administratora o pomoc zdalną.  

### <a name="level-of-access-for-remote-assistance"></a>Poziom dostępu dla pomocy zdalnej

Wybierz poziom dostępu przypisany do sesji Pomocy zdalnej, inicjowanych w konsoli programu Configuration Manager. Wybierz jedną z następujących opcji:
- **Brak** (ustawienie domyślne)
- **Zdalne wyświetlanie**
- **Pełna kontrola**

> [!NOTE]  
>  Użytkownik przy komputerze klienckim musi zawsze udzielić zezwolenia, aby można było rozpocząć sesję pomocy zdalnej.  

### <a name="manage-remote-desktop-settings"></a>Zarządzaj ustawieniami pulpitu zdalnego

Ustaw tę wartość na **tak** aby umożliwić programowi Configuration Manager Zarządzanie sesjami pulpitu zdalnego dla komputerów.  

### <a name="allow-permitted-viewers-to-connect-by-using-remote-desktop-connection"></a>Zezwalaj dopuszczonym podglądom na połączenie za pomocą programu Podłączanie pulpitu zdalnego

Ustaw tę wartość na **tak** do dodawania użytkowników określonych na liście dopuszczonych podglądów do grupy użytkowników lokalnych usług pulpitu zdalnego na komputerach klienckich.  

### <a name="require-network-level-authentication-on-computers-that-run-windows-vista-operating-system-and-later-versions"></a>Wymagaj uwierzytelniania na poziomie sieci na komputerach z systemem operacyjnym Windows Vista i nowszymi wersjami

Ustaw tę wartość na **tak** na potrzeby uwierzytelniania na poziomie sieci (NLA) nawiązania połączeń pulpitu zdalnego na komputerach klienckich. NLA początkowo wymaga mniej zasobów na komputerze zdalnym, ponieważ zakończeniem uwierzytelnianie użytkownika przed nawiązaniem połączenia pulpitu zdalnego. Za pomocą uwierzytelniania na poziomie sieci jest bezpieczniejsza konfiguracja. NLA pomaga chronić komputer przed złośliwymi użytkownikami lub oprogramowaniem i zmniejsza zagrożenie atakami typu "odmowa usługi".  



## <a name="software-center"></a>Centrum oprogramowania

### <a name="select-these-new-settings-to-specify-company-information"></a>Wybierz te nowe ustawienia, aby określić informacje o firmie
Ustaw tę wartość na **tak**, a następnie określ następujące ustawienia, aby brand Centrum oprogramowania dla Twojej organizacji:

- **Nazwa firmy** </br>
Wprowadź nazwę organizacji wyświetlaną użytkownikom w programie Software Center.
- **Schemat kolorów w programie Software Center** </br>
Wybierz **wybierz kolor** do definiowania kolor podstawowy używany przez Centrum oprogramowania.
- **Wybierz logo, które w programie Software Center** </br>
Wybierz **Przeglądaj** wybrać obraz, który będzie wyświetlany w programie Software Center. Logo musi być JPEG, PNG lub BMP 400 x 100 pikseli, o maksymalnym rozmiarze 750 KB. Nazwa pliku logo nie powinna zawierać spacje.  
         
### <a name="bkmk_HideUnapproved"></a> Ukryj niezatwierdzonych aplikacji w programie Software Center
Począwszy 1802 wersji programu Configuration Manager, gdy ta opcja jest włączona, użytkownik dostępnych aplikacji, które wymagają zatwierdzenia są ukryte w programie Software Center.   <!--1355146-->

### <a name="bkmk_HideInstalled"></a> Ukryj zainstalowanych aplikacji w programie Software Center
Począwszy od programu Configuration Manager 1802 wersji aplikacji, które są już zainstalowane nie będą już wyświetlane na karcie aplikacje gdy ta opcja jest włączona. Ta opcja jest ustawiona domyślnie podczas instalacji lub uaktualnienia do programu Configuration Manager 1802.  Zainstalowane aplikacje są nadal dostępne do przeglądu na karcie Stan instalacji. <!--1357592-->   
  
### <a name="software-center-tab-visibility"></a>Widoczność kartę Centrum oprogramowania
Skonfiguruj dodatkowe ustawienia w tej grupie mają **tak** uwidocznić w programie Software Center następujące karty:
- **Aplikacje**
- **Aktualizacje**
- **Systemy operacyjne**
- **Stan instalacji**
- **Zgodność urządzeń**
- **Opcje**

Na przykład, jeśli Twoja organizacja nie korzysta z zasadami zgodności, i chcesz ukryć kartę zgodności urządzeń w programie Software Center, ustaw **włączyć zgodności urządzenia, na karcie** do **nr**.



## <a name="software-deployment"></a>Wdrażanie oprogramowania  

### <a name="schedule-re-evaluation-for-deployments"></a>Zaplanuj ponowną ocenę dla wdrożeń
Należy skonfigurować harmonogram, gdy program Configuration Manager ponownie ocenia reguły wymagań dla wszystkich wdrożeń. Wartość domyślna to co siedem dni.  

> [!IMPORTANT]  
>  Zaleca się, że nie zmienisz tę wartość na mniejszą wartość niż domyślne. Bardziej aktywnego harmonogramu ponownej oceny miało negatywny wpływ na wydajność sieci i klienta komputerów.  

Zainicjować tę akcję klienta w następujący sposób: w **programu Configuration Manager** kontrolować panelu z **akcje** wybierz opcję **cykl oceny wdrażania aplikacji**.  



##  <a name="software-inventory"></a>Zapasy oprogramowania  

### <a name="enable-software-inventory-on-clients"></a>Włącz spis oprogramowania na klientach

Ta wartość jest równa **tak** domyślnie. Aby uzyskać więcej informacji, zobacz [wprowadzenie do spisu oprogramowania](/sccm/core/clients/manage/inventory/introduction-to-software-inventory).

### <a name="schedule-software-inventory-and-file-collection"></a>Zaplanuj spis oprogramowania i plików zbieranie

Wybierz **harmonogram** można dostosować częstotliwość, że klienci mają uruchamiać oprogramowania cykle kolekcji spisu i plików. Domyślnie ten cykl występuje co siedem dni.

### <a name="inventory-reporting-detail"></a>Szczegóły raportowania spisu

Określ jedną z następujących poziomów informacje o pliku do magazynu:
- **Tylko plik**
- **Tylko produktu**
- **Pełne szczegóły** (ustawienie domyślne)

### <a name="inventory-these-file-types"></a>Następujące typy plików

Jeśli chcesz określić typy plików do spisu, wybierz **Ustaw typy**, a następnie skonfiguruj następujące opcje:  

> [!NOTE]  
>  Jeśli wielu niestandardowych ustawień klienta są stosowane do komputera, magazynu, która zwraca każdego ustawienia są scalane.  

-   Wybierz **nowy** można dodać do spisu nowy typ pliku. Następnie określ następujące informacje w **właściwości zinwentaryzowanych plików** okno dialogowe:  

    -   **Nazwa**: Podaj nazwę pliku, który chcesz dodać do spisu. Użyj gwiazdki (**&#42;**) symbolu wieloznacznego oznaczającego dowolny ciąg tekstu i znaku zapytania (**?**) do reprezentowania dowolny pojedynczy znak. Na przykład, jeśli chcesz dodać do spisu wszystkie pliki z rozszerzeniem doc, określ nazwę pliku  **\*doc**.  

    -   **Lokalizacja**: Wybierz **ustawić** otworzyć **właściwości ścieżki** okno dialogowe. Konfigurowanie spisu oprogramowania w celu wyszukania na dyskach twardych wszystkich klientów określonego pliku, określonej ścieżki (na przykład **C:\Folder**), lub Wyszukaj określonej zmiennej (na przykład *% windir %*). Można także przeszukać wszystkie podfoldery w określonej ścieżce.  

    -   **Wyklucz pliki zaszyfrowane i skompresowane**: Po wybraniu tej opcji pliki skompresowane lub zaszyfrowane nie są dodane do spisu.  

    -   **Wyklucz pliki zawarte w folderze systemu Windows**: Po wybraniu tej opcji pliki w folderze systemu Windows i jego podfolderach nie są dodane do spisu.  

    Wybierz **OK** zamknąć **właściwości zinwentaryzowanych plików** okno dialogowe. Dodaj wszystkie pliki, które mają być spisu, a następnie wybierz **OK** zamknąć **Konfiguruj ustawienie klienta** okno dialogowe.  

### <a name="collect-files"></a>Zbieranie plików

Aby zebrać pliki z komputerów klienckich, należy zaznaczyć **Ustaw pliki**, a następnie skonfiguruj następujące ustawienia:  

> [!NOTE]  
>  Jeśli wielu niestandardowych ustawień klienta są stosowane do komputera, magazynu, która zwraca każdego ustawienia są scalane.  

-   W **Konfiguruj ustawienie klienta** okno dialogowe, wybierz opcję **nowy** Aby dodać plik do zebrania.  

-   W oknie dialogowym **Właściwości zebranych plików** wprowadź następujące informacje:  

    -   **Nazwa**: Podaj nazwę pliku, który chcesz zebrać. Użyj gwiazdki (**&#42;**) symbolu wieloznacznego oznaczającego dowolny ciąg tekstu i znaku zapytania (**?**) do reprezentowania dowolny pojedynczy znak.  

    -   **Lokalizacja**: Wybierz **ustawić** otworzyć **właściwości ścieżki** okno dialogowe. Konfigurowanie spisu oprogramowania do wyszukania na dyskach twardych wszystkich klientów pliku do zebrania, określonej ścieżki (na przykład **C:\Folder**), lub Wyszukaj określonej zmiennej (na przykład *% windir %*). Można także przeszukać wszystkie podfoldery w określonej ścieżce.  

    -   **Wyklucz pliki zaszyfrowane i skompresowane**: Po wybraniu tej opcji pliki skompresowane lub zaszyfrowane nie są zbierane.  

    -   **Zatrzymaj zbieranie plików, gdy łączny rozmiar plików przekracza (KB)**: Określ rozmiar pliku w kilobajtach (KB), po którym klient zatrzymuje zbieranie określonych plików.  

    > [!NOTE]  
    >  Serwer lokacji zbiera pięć ostatnio zmienionych wersji zebranych plików i zapisuje je w  *&lt;katalog instalacyjny programu ConfigMgr\>* \Inboxes\Sinv.box\Filecol katalogu. Jeśli plik nie został zmieniony od ostatniego cyklu spisu oprogramowania, plik nie jest zebrany ponownie.  
    >   
    >  Spis oprogramowania nie zbiera pliki większe niż 20 MB.  
    >   
    >  Wartość **maksymalny rozmiar wszystkich zebranych plików (KB)** w **Konfiguruj ustawienie klienta** wyświetlane okno dialogowe maksymalny rozmiar wszystkich zebranych plików. Po osiągnięciu tego rozmiaru zatrzymuje zbieranie plików. Wszystkie już zebrane pliki są zachowywane i wysłane do serwera lokacji.  

    > [!IMPORTANT]
    >  Jeśli konfigurujesz zapasy oprogramowania w celu zebrania wielu dużych plików, ta konfiguracja może negatywnie wpłynąć na wydajność sieci i lokacji serwera.  

    Aby uzyskać informacje o sposobie wyświetlania zebranych plików, zobacz [jak używać Eksploratora zasobów do wyświetlania spisu oprogramowania](../../../core/clients/manage/inventory/use-resource-explorer-to-view-software-inventory.md).  

    Wybierz **OK** zamknąć **właściwości zebranych plików** okno dialogowe. Dodaj wszystkie pliki, które chcesz zebrać, a następnie wybierz **OK** zamknąć **Konfiguruj ustawienie klienta** okno dialogowe.  

### <a name="set-names"></a>Ustaw nazwy

Agent spisu oprogramowania pobiera producenta i nazw produktów z informacji w nagłówku pliku. Te nazwy nie zawsze są standardowe informacje nagłówka pliku. Podczas wyświetlania spisu oprogramowania w Eksploratorze zasobów, może się pojawić różne wersje tego samego producenta lub nazwy produktu. Aby ustandaryzować te nazwy wyświetlane, wybierz opcję **Ustaw nazwy**, a następnie skonfiguruj następujące ustawienia:  

-   **Nazwa typu**: Spis oprogramowania zbiera informacje o producentach i produktach. Wybierz, czy chcesz skonfigurować nazwy wyświetlane dla **producenta** lub **produktu**.  

-   **Nazwa wyświetlana**: Określ nazwę wyświetlaną, która ma być używany zamiast nazw na **zinwentaryzowane nazwy** listy. Aby określić nową nazwę wyświetlaną, zaznacz **nowy**.  

-   **Zinwentaryzowane nazwy**: Aby dodać nazwy zinwentaryzowanej, należy wybrać **nowy**. Ta nazwa zostanie zastąpiona w spisie oprogramowania przez nazwę wybraną w **Nazwa wyświetlana** listy. Można dodać wiele nazw w celu zastąpienia.  



##  <a name="software-metering"></a>Pomiar użytkowania oprogramowania

### <a name="enable-software-metering-on-clients"></a>Włącz zliczanie oprogramowania na klientach
To ustawienie ma wartość **tak** domyślnie. Aby uzyskać więcej informacji, zobacz [pomiaru użytkowania oprogramowania](/sccm/apps/deploy-use/monitor-app-usage-with-software-metering#configure-software-metering).

### <a name="schedule-data-collection"></a>Planowanie zbierania danych
Wybierz **harmonogram** można dostosować częstotliwość, że klienci mają uruchamiać cyklu zliczania oprogramowania. Domyślnie ten cykl występuje co siedem dni.



##  <a name="software-updates"></a>Aktualizacje oprogramowania  

### <a name="enable-software-updates-on-clients"></a>Włącz aktualizacje oprogramowania na klientach

To ustawienie umożliwia włączenie aktualizacji oprogramowania na klientach programu Configuration Manager. Gdy to ustawienie zostanie wyłączone, programu Configuration Manager usunie istniejące zasady wdrażania z klienta. Po ponownym włączeniu tego ustawienia klient pobierze bieżące zasady wdrażania.  

> [!IMPORTANT]  
>  Po wyłączeniu tego ustawienia zasad zgodności, które są oparte na aktualizacji oprogramowania nie będzie już działać.  

### <a name="software-update-scan-schedule"></a>Harmonogram skanowania w poszukiwaniu aktualizacji oprogramowania

Wybierz **harmonogram** Aby określić, jak często klient inicjuje skanowania oceny zgodności. To skanowanie Określa stan aktualizacji oprogramowania na kliencie (na przykład wymagane lub zainstalowane). Aby uzyskać więcej informacji na temat oceny zgodności, zobacz [oceny zgodności aktualizacji oprogramowania](../../../sum/understand/software-updates-introduction.md#BKMK_SUMCompliance).  

Domyślnie ten tryb skanowania używa prostego harmonogramu zainicjować co siedem dni. Można utworzyć harmonogram niestandardowy. Można określić dokładną dnia i godziny rozpoczęcia, użyj uniwersalnego czasu koordynowanego (UTC) lub czas lokalny i skonfigurować interwał powtarzania dla określonego dnia tygodnia.  

> [!NOTE]  
>  Jeśli w przypadku określenia interwału krótszego niż jeden dzień, programu Configuration Manager automatycznie domyślnie jeden dzień.  

> [!WARNING]  
>  Rzeczywista godzina uruchomienia na komputerach klienckich jest czas rozpoczęcia wydłużony o przypadkowy czas, maksymalnie do dwóch godzin. Losowe zapobiega komputery klienckie z Inicjowanie skanowania i jednocześnie nawiązywania połączenia z aktywnym punktem aktualizacji oprogramowania.  

### <a name="schedule-deployment-re-evaluation"></a>Zaplanuj ponowną ocenę wdrożenia

Wybierz **harmonogram** skonfigurować częstotliwość aktualizacji oprogramowania klienta agenta ponownie ocenia aktualizacje oprogramowania dla stanu instalacji na komputerach klienckich programu Configuration Manager. Po aktualizacji wcześniej zainstalowane oprogramowanie znajduje się już na klientach, ale nadal są wymagane, klient ponownie instaluje aktualizacje oprogramowania.

Dostosuj ten harmonogram zasadą firmową dotyczącą zgodności aktualizacji oprogramowania, i określa, czy użytkownicy można odinstalować aktualizacji oprogramowania. Każdy cykl ponownej oceny wdrożenia powoduje aktywności procesora komputera klienta i sieci. Domyślnie to ustawienie powoduje użycie prostego harmonogramu zainicjować skanowanie ponownej oceny wdrożenia co siedem dni.  

> [!NOTE]  
>  Jeśli w przypadku określenia interwału krótszego niż jeden dzień, programu Configuration Manager automatycznie domyślnie jeden dzień.  

### <a name="when-any-software-update-deployment-deadline-is-reached-install-all-other-software-update-deployments-with-deadline-coming-within-a-specified-period-of-time"></a>Po osiągnięciu ostatecznego terminu wdrożenia dowolnej aktualizacji oprogramowania zainstaluj wszystkie pozostałe wdrożenia aktualizacji oprogramowania z terminem wypadającym w danym okresie czasu

Ustaw tę wartość na **tak** Aby zainstalować wszystkie aktualizacje oprogramowania z wymaganych wdrożeń z terminami występujące w danym okresie czasu. Podczas wdrażania aktualizacji oprogramowania wymagane przez nią miejsce osiągnie termin, instalacja aktualizacji oprogramowania we wdrożeniu inicjowania przez klienta. To ustawienie określa, czy zainstalować aktualizacje oprogramowania z innych wymaganych wdrożeniach, które mają terminy w określonym czasie.  

To ustawienie umożliwia przyspieszenie instalacji wymaganych aktualizacji oprogramowania. To ustawienie ma także może zwiększyć bezpieczeństwo klientów, Zmniejsz powiadomień dla użytkownika oraz zmniejszeniu klienta zostanie ponownie uruchomiony. Domyślnie to ustawienie ma wartość **Nie**.  

### <a name="period-of-time-for-which-all-pending-deployments-with-deadline-in-this-time-will-also-be-installed"></a>Okres czasu, w którym wszystkie oczekujące wdrożenia z terminem wypadającym w tym okresie także zostaną zainstalowane

To ustawienie umożliwia określenie długości czasu dla poprzedniego ustawienia. Można wprowadzić wartość z zakresu od 1 do 23 godzin i z zakresu od 1 do 365 dni. Domyślne ustawienie to 7 dni.  

### <a name="enable-installation-of-express-installation-files-on-clients"></a>Włącz instalację plików instalacji ekspresowej na klientach

Ustaw tę wartość na **tak** do Zezwalaj klientom na użycie plików instalacji ekspresowej. Aby uzyskać więcej informacji, zobacz [instalacji zarządzania Express pliki aktualizacji systemu Windows 10](/sccm/sum/deploy-use/manage-express-installation-files-for-windows-10-updates).

### <a name="port-used-to-download-content-for-express-installation-files"></a>Port używany do pobierania zawartości plików instalacji ekspresowej

To ustawienie określa port lokalny dla odbiornika HTTP do pobierania zawartości express. Domyślnie jest ustawiona na 8005. Nie trzeba otworzyć ten port w zaporze klienta.

### <a name="enable-management-of-the-office-365-client-agent"></a>Włącz zarządzanie agenta klienta Office 365

Jeśli to równa **tak**, umożliwia konfigurację ustawień instalacji usługi Office 365. Umożliwia również pobierania plików z pakietu Office sieci dostarczania zawartości (CDN) i wdrażanie plików jako aplikacji w programie Configuration Manager. Aby uzyskać więcej informacji, zobacz [zarządzania usługi Office 365 ProPlus](/sccm/sum/deploy-use/manage-office-365-proplus-updates).

### <a name="enable-third-party-software-updates"></a>Włącz aktualizacje oprogramowania innych firm 

Jeśli to równa **tak**, ustawia zasady dla "Zezwalaj na podpisane aktualizacje z intranetowej lokalizacji usługi aktualizacji firmy Microsoft" i instaluje certyfikat podpisywania w magazynie zaufanego wydawcy na kliencie. To ustawienie klienta został dodany w 1802 wersji programu Configuration Manager.
## <a name="state-messaging"></a>Do obsługi komunikatów stanu

### <a name="state-message-reporting-cycle-minutes"></a>Komunikat o stanie raportowania cyklu (w minutach)
Określa, jak często klienci zgłaszania komunikatów o stanie. To ustawienie jest 15 minut domyślnie.



##  <a name="user-and-device-affinity"></a>Koligacja użytkowników i urządzeń  

### <a name="user-device-affinity-usage-threshold-minutes"></a>Próg użycia koligacji urządzenia użytkownika (w minutach)
Określ liczbę minut, zanim programu Configuration Manager tworzy mapowanie koligacji urządzenia użytkownika.  Domyślnie ta wartość jest 2880 minut (2 dni).

### <a name="user-device-affinity-usage-threshold-days"></a>Próg użycia koligacji użytkownika i urządzenia (dni)
Określ liczbę dni, przez jaką klient mierzy próg koligacji na podstawie użycia urządzeń.  Domyślnie ta wartość jest 30 dni.

> [!NOTE]  
>  Na przykład określić **próg użycia koligacji urządzenia użytkownika (w minutach)** jako **60** minut, a **próg użycia koligacji użytkownika i urządzenia (dni)** jako **5**  dni. Następnie użytkownik musi używać urządzenia przez 60 minut w okresie 5 dni na tworzenie koligacji automatyczne z urządzeniem.  

### <a name="automatically-configure-user-device-affinity-from-usage-data"></a>Automatycznie Konfiguruj koligację urządzenia użytkownika na podstawie danych użycia
Wybierz **tak** na tworzenie koligacji urządzenia użytkownika automatycznego na podstawie informacji użycia, która gromadzi programu Configuration Manager.  

### <a name="allow-user-to-define-their-primary-devices"></a>Zezwalaj użytkownikowi na definiowanie urządzeń podstawowych
Gdy to ustawienie jest **tak**, użytkownicy będą mogli identyfikować własne urządzenia podstawowe w Centrum oprogramowania.



## <a name="windows-analytics"></a>Module analiz systemu Windows

Aby uzyskać więcej informacji na temat tych ustawień, zobacz [skonfigurować klientów do danych raportu do analiz systemu Windows](/sccm/core/clients/manage/monitor-windows-analytics#configure-clients-to-report-data-to-windows-analytics).
    
