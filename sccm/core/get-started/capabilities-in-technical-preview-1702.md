---
title: "Możliwości w Technical Preview 1702 programu Configuration Manager"
description: "Informacje na temat funkcji dostępnych w Technical Preview programu System Center Configuration Manager, 1702 wersji."
ms.custom: na
ms.date: 02/24/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aedd608d-6db3-4ea5-851d-70f2dcda6bb5
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 8f4ec982a54cf3cefef310268a54850e70e2e63a
ms.openlocfilehash: 3bdbcd1a3c64a1d50f2f6219b2a5e17d60979864
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1702-for-system-center-configuration-manager"></a>Możliwości w Technical Preview 1702 System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (Technical Preview)*

Ten artykuł wprowadza do funkcji, które są dostępne w Technical Preview programu System Center Configuration Manager, 1702 wersji. Można zainstalować tę wersję, aby zaktualizować i dodawać nowe funkcje do lokacji programu Configuration Manager technical preview. Przed zainstalowaniem tej wersji technical preview, przejrzyj temat wprowadzające [Technical Preview dla programu System Center Configuration Manager](../../core/get-started/technical-preview.md), aby zapoznać się z ogólnym wymagania i ograniczenia dotyczące używania technical preview, jak zaktualizować między wersjami i jak Wyraź swoją opinię dotyczącą funkcji w technical preview.    


**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  

##  <a name="send-feedback-from-the-configuration-manager-console"></a>Wyślij opinię z konsoli programu Configuration Manager

Ta wersja zapoznawcza wprowadza nowe opcje opinii w konsoli programu Configuration Manager. Opcje opinii umożliwia wysyłanie opinii bezpośrednio do zespołu deweloperów i na opinie UserVoice Menedżera konfiguracji witryny sieci Web.  

>Można znaleźć **opinii** opcji:
-  Na Wstążce po lewej karcie głównej każdego węzła.  
   ![Wstążka](./media/feedback-home.png)

-  Po kliknięciu prawym przyciskiem myszy dowolnego obiektu w konsoli.   
    ![Prawej kliknięcia](./media/feedback-option.png)   

Wybieranie **opinii** otwiera w przeglądarce WWW opinii UserVoice programu Configuration Manager, w https://configurationmanager.uservoice.com/forums/300492-ideas.
##  <a name="changes-for-updates-and-servicing"></a>Zmiany aktualizacji i obsługi
Następujące są wprowadzane z tego podglądu.

**Prostsze opcje aktualizacji**  
Przy następnym infrastruktury kwalifikuje się do dwóch lub większej liczby aktualizacji, pobrać najnowszą aktualizację. Na przykład, jeśli bieżąca wersja lokacji wynosi dwa lub więcej starsze niż najnowszą wersję, która jest dostępna, tylko że najnowsza wersja aktualizacji jest pobierany automatycznie.  

Użytkownik może pobrać i zainstalować dostępne aktualizacje, nawet jeśli nie są one najbardziej aktualnej wersji. Jednakże otrzymasz ostrzeżenie, że aktualizacja została zastąpiona przez nowszej. Do pobierania aktualizacji, która jest *dostępne do pobrania*, wybierz aktualizację, w konsoli, a następnie kliknij przycisk **pobrać**.

**Ulepszone oczyszczanie starszych aktualizacji**   
Dodaliśmy funkcję automatycznego czyszczenia, która usuwa niepotrzebne pliki do pobrania z folderu "EasySetupPayload" na serwerze lokacji.  


## <a name="peer-cache-improvements"></a>Ulepszenia pamięci podręcznej elementu równorzędnego
Począwszy od tej wersji, komputer źródłowy pamięci podręcznej elementu równorzędnego będą odrzucać żądania zawartości, gdy komputer źródłowy pamięci podręcznej elementu równorzędnego spełnia żadnego z następujących warunków:  
 -     Jest w trybie niskim poziomie naładowania baterii.
 -  Obciążenie procesora CPU przekracza 80% w czasie żądania zawartości.
 -  We/Wy dysku ma *AvgDiskQueueLength* który przekracza 10.
 -  Nie ma ma więcej dostępnych połączeń z komputerem.   

Można skonfigurować te ustawienia przy użyciu klasy konfiguracji agenta klienta dla funkcji źródło elementu równorzędnego (*SMS_WinPEPeerCacheConfig*) używając System Center Configuration Manager SDK.

Gdy komputer odrzuci zawartość, komputera wysyłającego żądanie będzie wyszukiwać źródła alternatywne zawartości formularza w puli lokalizacji źródła zawartości.   

## <a name="azurediscovery"></a>Azure Active Directory Domain Services umożliwia zarządzanie urządzeniami, użytkowników i grup

Z tego technical preview można zarządzać urządzeń dołączonych do usług domenowych w usłudze Azure Active Directory (AD) w wersji zarządzane domeny. Za pomocą różnych metod odnajdywania programu Configuration Manager umożliwia również odnajdywanie urządzeń, użytkowników i grup w tej domenie.

Infrastruktura lokacji technical preview, klientów i domen usługi Azure AD domeny należy uruchomić w systemie Azure.


### <a name="set-up-configuration-manager-to-use-azure-ad"></a>Skonfiguruj program Configuration Manager do używania usługi Azure AD
Aby korzystać z usługi Azure AD za pomocą programu Configuration Manager, będą potrzebne następujące czynności:
-    Subskrypcja platformy Azure.
-    Azure AD z usługami domenowymi (DS).
-    Lokacja programu Configuration Manager, która działa na maszynie Wirtualnej platformy Azure, który jest dołączony do usługi Azure AD.
-    Klientów programu Configuration Manager, które są uruchamiane w tym samym środowisku usługi Azure AD.

Aby skonfigurować usługę Azure AD domeny, zobacz [rozpoczęcie pracy z usługami Azure AD](https://docs.microsoft.com/azure/active-directory-domain-services/active-directory-ds-getting-started).

### <a name="discover-resources"></a>Odnajdywanie zasobów
Po Konfigurowanie programu Configuration Manager jest skonfigurowany do uruchamiania w usłudze Azure AD, można użyć następujących metod odnajdywania usługi Active Directory wyszukiwanie Azure AD dla zasobów:  
- Odnajdywanie systemu usługi Active Directory
- odnajdywanie użytkownika usługi Active Directory
- Odnajdywanie grupy usługi Active Directory  

Dla każdej używanej metody Edytowanie kwerendy LDAP do wyszukiwania struktury Azure AD OU zamiast kontenerów, które są typowe dla lokalnej usługi Active Directory. Wymaga to bezpośrednie zapytania wyszukiwania usługi Active Directory w Twojej subskrypcji platformy Azure.  

W poniższych przykładach użyto Azure AD z *contoso.onmicrosoft.com*:
 - **Odnajdywanie systemu**   
Azure AD przechowuje urządzeń w ramach **AADDC komputery** jednostki Organizacyjnej.  Skonfiguruj następujące ustawienia:  
  -    *Komputery LDAP://OU=AADDC, DC = contoso, DC = onmicrosoft, DC = com*  


- **Odnajdywanie użytkownika** AAD przechowuje użytkowników w ramach **AADDC użytkowników** jednostki Organizacyjnej.  Skonfiguruj następujące ustawienia:
  - *Użytkownicy LDAP://OU=AADDC, DC = contoso, DC = onmicrosoft, DC = com*


- **Odnajdywanie grupy**  
Azure AD nie ma jednostkę Organizacyjną, która przechowuje grup. Zamiast tego użyj taką samą strukturę ogólne jako kwerendy System lub użytkownik i skonfiguruj zapytanie LDAP wskaż jednostki Organizacyjnej, która zawiera grupy, że chcesz odnaleźć.

Zobacz następujące tematy, aby uzyskać więcej informacji na temat usługi Azure AD:  
 - [Azure Active Directory Domain Services](https://azure.microsoft.com/en-us/services/active-directory-ds) w witrynie azure.microsoft.com.
 - [Dokumentacja usługi domenowe Active Directory](https://docs.microsoft.com/azure/active-directory-domain-services) na docs.microsoft.com.

## <a name="conditional-access-device-compliance-policy-improvements"></a>Ulepszenia zasady zgodności urządzeń dostępu warunkowego

Dostępny jest nową regułę zasad zgodności urządzeń blokowania dostępu do zasobów firmy, które obsługują dostęp warunkowy, gdy użytkownicy korzystają z aplikacji, które są częścią listę niezgodnych aplikacji. Lista niezgodnych aplikacji może być zdefiniowany przez administratora podczas dodawania nowej reguły zgodne **aplikacji, których nie można zainstalować**. Ta reguła wymaga administratora, aby wprowadzić **Nazwa aplikacji**, **Identyfikatora aplikacji**i **wydawcę aplikacji** (opcjonalnie), dodając do listy niezgodnych aplikacji. To ustawienie dotyczy tylko systemów iOS i android.

Ponadto pomaga organizacjom uniknięcie wycieku danych za pośrednictwem niezabezpieczonej aplikacje i zapobiec zużycie nadmiernej ilości danych za pośrednictwem niektórych aplikacji.

- Dowiedz się więcej [działanie zasadami zgodności urządzeń](https://docs.microsoft.com/sccm/protect/deploy-use/device-compliance-policies).
- Dowiedz się więcej [Tworzenie zasad zgodności urządzeń](https://docs.microsoft.com/sccm/protect/deploy-use/create-compliance-policy).

### <a name="try-it-out"></a>Wypróbuj to

**Scenariusz:** Określenie aplikacji, które mogą być przyczyną wycieku danych, wysyłając dane firmowe spoza firmy lub powoduje zużycie nadmiernej ilości danych, następnie [Tworzenie zasad zgodności urządzeń dostępu warunkowego](https://docs.microsoft.com/sccm/protect/deploy-use/create-compliance-policy) który dodaje te aplikacje do listy niezgodnych aplikacji. Spowoduje to zablokowania dostępu do zasobów firmy, które obsługują dostęp warunkowy, dopóki użytkownik może usunąć zablokowanych aplikacji.

## <a name="antimalware-client-version-alert"></a>Alert wersji klienta ochrony przed złośliwym oprogramowaniem
Począwszy od tej wersji wstępnej, Configuration Manager Endpoint Protection zapewnia alert, jeśli więcej niż 20% (domyślnie) zarządzanych klientów korzysta z wersji wygasłe ochrony przed złośliwym oprogramowaniem klienta (tj. klienta usługi Windows Defender lub Endpoint Protection).

### <a name="try-it-out"></a>Wypróbuj to
Upewnij się, że program Endpoint Protection jest włączona na wszystkich klientach desktop i serwerów za pomocą zasad ustawień klienta. Teraz można wyświetlać **wersji klienta ochrony przed złośliwym oprogramowaniem** i **stan wdrożenia programu Endpoint Protection** przechodząc **zasoby i zgodność** > **Przegląd** > **urządzeń** > **wszystkie komputery stacjonarne i klienci służyć**. Aby sprawdzić, czy alert, należy wyświetlić **alerty** w **monitorowanie** obszaru roboczego. Ponad 20% zarządzanych klienci korzystający z wygasła wersja oprogramowania ochrony przed złośliwym oprogramowaniem, ochrony przed złośliwym oprogramowaniem wersja klienta jest nieaktualna zostanie wyświetlony alert. Ten alert nie jest wyświetlany na **monitorowanie** > **Przegląd** kartę. Do aktualizacji klientów wygasłe ochrony przed złośliwym oprogramowaniem, Włącz aktualizacje oprogramowania ochrony przed złośliwym oprogramowaniem klientów.

Aby skonfigurować wartość procentowa, o której alert jest generowany, rozwiń węzeł **monitorowanie** > **alerty** > **wszystkie alerty**, kliknij dwukrotnie **nieaktualny klienci ochrony przed złośliwym oprogramowaniem** i modyfikować **Zgłoś alert, jeśli procent zarządzanych klientów z nieaktualną wersją klienta przed złośliwym kodem jest więcej niż** — opcja.

## <a name="compliance-assessment-for-windows-update-for-business-updates"></a>Oceny zgodności dla usługi Windows Update aktualizacje biznesowe
Można teraz skonfigurować reguły zgodności zasad aktualizacji do uwzględnienia Windows Update wynik oceny biznesowych w ramach oceny dostępu warunkowego.
> [!IMPORTANT]
> Musi mieć Windows 10 Insider Preview kompilacji 15019 lub nowszej do używania oceny zgodności dla usługi Windows Update do aktualizacji firmy.

### <a name="allow-windows-update-for-business-to-manage-windows-10-updates"></a>Zezwalaj na usługi Windows Update w przedsiębiorstwie do zarządzania aktualizacjami systemu Windows 10
Aby zebrać informacje o oceny zgodności dla usługi Windows Update aktualizacje biznesowych, umożliwia skonfigurowanie ustawienia umożliwiające jawnie usługi Windows Update w przedsiębiorstwie do zarządzania aktualizacjami systemu Windows 10 agenta klienta poniższej procedury.
1. W konsoli programu Configuration Manager przejdź do obszaru **Administracja** > **Ustawienia klienta**.
2. We właściwościach ustawień klienta, przejdź do **aktualizacji oprogramowania**i wybierz **tak** dla **Zarządzanie systemem Windows 10 aktualizacji z usługi Windows Update dla firm** ustawienie.

### <a name="create-a-compliance-policy-for-windows-update-for-business-assessment"></a>Tworzenie zasad zgodności dla usługi Windows Update w celu oceny biznesowe
1. W konsoli programu Configuration Manager, przejdź do **zasoby i zgodność** > **ustawień zgodności** > **zasady zgodności**.
2. Kliknij przycisk **Utwórz zasady zgodności** lub wybierz istniejące zasady zgodności w celu modyfikowania.
3. Na stronie Ogólne, podaj nazwę i opis, wybierz **reguły zgodności dla urządzeń zarządzanych za pomocą klienta programu Configuration Manager**, Ustaw ważność niezgodności raportowania i kliknij przycisk **dalej**.
4. Na stronie obsługiwane platformy wybierz **systemu Windows 10**, a następnie kliknij przycisk **dalej**.
5. Na stronie reguły kliknij **nowy...** , a następnie dla **warunku** wybierz **usługi Windows Update wymaga zgodności Business**. **Wartość** ustawienie jest automatycznie ustawiana **True**.

Nowe zasady zostaną wyświetlone w węźle **Zasady zgodności** w obszarze roboczym **Zasoby i zgodność** .

### <a name="deploy-a-compliance-policy"></a>Wdrażanie zasad zgodności
1. W konsoli programu Configuration Manager, przejdź do **zasoby i zgodność** > **ustawień zgodności**, a następnie kliknij przycisk **zasady zgodności**.
2. Na karcie **Narzędzia główne** w grupie **Wdrażanie** kliknij przycisk **Wdróż**.
3. W oknie dialogowym **Wdrażanie zasad zgodności** kliknij przycisk **Przeglądaj** , aby wybrać kolekcję użytkowników, dla której chcesz wdrożyć zasady.
   Ponadto można wybrać opcje generowania alertów w przypadku niezgodności zasad, a także skonfigurować harmonogram oceny zasad pod kątem zgodności.
4. Gdy wszystko będzie gotowe, kliknij przycisk **OK**.

### <a name="monitor-the-compliance-policy"></a>Monitorowanie zasad zgodności
Po utworzeniu zasad zgodności, można monitorować wyniki zgodności w konsoli programu Configuration Manager. Aby uzyskać szczegółowe informacje, zobacz [monitorowanie zasad zgodności](https://docs.microsoft.com/en-us/sccm/protect/deploy-use/create-compliance-policy#monitor-the-compliance-policy).


## <a name="improvements-to-software-center-settings-and-notification-messages-for-high-impact-task-sequences"></a>Ulepszenia w ustawieniach Centrum oprogramowania i komunikatów powiadomień dla sekwencji zadań wysoki wpływ
Ta wersja zawiera następujące ulepszenia w ustawieniach Centrum oprogramowania i komunikatów powiadomień dla sekwencji zadań wdrażania wysoki wpływ:

- W oknie właściwości dla sekwencji zadań można teraz skonfigurować dowolnej sekwencji zadań, w tym sekwencji zadań systemu operacyjnego jako wdrożenie o wysokim ryzyku. Wszystkie sekwencje zadań, która spełnia określone warunki automatycznie jest zdefiniowany jako wysoki wpływ. Aby uzyskać szczegółowe informacje, zobacz [Zarządzanie wdrożeniami o wysokim ryzyku](http://docs.microsoft.com/sccm/protect/understand/settings-to-manage-high-risk-deployments).
- W oknie właściwości dla sekwencji zadań można użyć domyślnego komunikatu powiadomienia lub utworzyć własne niestandardowe powiadomienie wysoki wpływ wdrożenia.
- W oknie właściwości dla sekwencji zadań można skonfigurować właściwości, które obejmują wprowadzić wymagane ponowne uruchomienie Centrum oprogramowania rozmiar pobierania sekwencji zadań i szacowany czas wykonywania.
- Komunikat domyślny wysoki wpływ wdrożenia dla miejscowego uaktualnienia teraz stany automatycznie migracji aplikacji, danych i ustawień. Wcześniej, komunikat domyślny dla każdej instalacji systemu operacyjnego wskazane, że wszystkie aplikacje, dane i ustawienia zostałyby utracone, która nie obowiązuje dla uaktualnienia w miejscu.

### <a name="set-a-task-sequence-as-a-high-impact-task-sequence"></a>Ustawianie sekwencji zadań za pomocą sekwencji zadań wysoki wpływ
Użyj poniższej procedury do ustawienia sekwencji zadań jako wysoki wpływ.
> [!NOTE]
> Wszystkie sekwencje zadań, która spełnia określone warunki automatycznie jest zdefiniowany jako wysoki wpływ. Aby uzyskać szczegółowe informacje, zobacz [Zarządzanie wdrożeniami o wysokim ryzyku](http://docs.microsoft.com/sccm/protect/understand/settings-to-manage-high-risk-deployments).

1. W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** > **systemów operacyjnych** > **sekwencji zadań**.
2. Wybierz sekwencję zadań do edycji, a następnie kliknij przycisk **właściwości**.
3. Na **powiadomienie użytkownika** zaznacz **jest sekwencji zadań wysoki wpływ**.

### <a name="create-a-custom-notification-for-high-risk-deployments"></a>Utwórz niestandardowe powiadomienia dla wdrożenia o wysokim ryzyku
1. W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** > **systemów operacyjnych** > **sekwencji zadań**.
2. Wybierz sekwencję zadań do edycji, a następnie kliknij przycisk **właściwości**.
3. Na **powiadomienie użytkownika** zaznacz **użyć niestandardowego tekstu**.
>  [!NOTE]
>  Tekst powiadomienia użytkownika można ustawić tylko podczas **jest sekwencji zadań wysoki wpływ** jest zaznaczone.

4. Skonfiguruj następujące ustawienia (maksymalnie 255 znaków dla każdego pola tekstowego):

   **Tekst nagłówka powiadomienia użytkownika**: Określa niebieski tekst wyświetlany na powiadomienie użytkownika Centrum oprogramowania. Na przykład domyślny powiadomienie użytkowników, ta sekcja zawiera którąś "Potwierdź chcesz uaktualnić system operacyjny na tym komputerze".

   **Tekst komunikatu powiadomienia użytkownika**: Istnieją trzy pola tekstowe, które zawierają treści niestandardowe powiadomienia.
   - 1. pole tekstowe: Określa główną część tekstu, zazwyczaj zawierającej instrukcje dla użytkownika. Na przykład domyślny powiadomienie użytkowników, ta sekcja zawiera coś jak "Uaktualnianie systemu operacyjnego potrwa i komputer może być kilka razy ponownie."
   - pole tekstowe 2: Określa tekst czcionką pogrubioną w głównej części tekstu. Na przykład domyślny powiadomienie użytkowników, ta sekcja zawiera coś jak "to uaktualnienie w miejscu instalacji nowego systemu operacyjnego i automatycznie migruje aplikacje, dane i ustawienia".
   - pole tekstowe 3: Określa ostatni wiersz tekstu pogrubienie tekstu. Na przykład domyślny powiadomienie użytkowników, ta sekcja zawiera którąś "kliknij przycisk Zainstaluj, aby rozpocząć. W przeciwnym razie kliknij przycisk Anuluj."   

   Załóżmy, że skonfigurować następujące powiadomienie niestandardowych właściwości.

   ![Niestandardowe powiadomienia dla sekwencji zadań](.\media\user-notification.png)

   Następujący komunikat powiadomienia będą wyświetlane podczas instalacji zostanie otwarty przez użytkownika z Centrum oprogramowania.

   ![Niestandardowe powiadomienia dla sekwencji zadań](.\media\user-notification-enduser.png)

### <a name="configure-software-center-properties"></a>Konfigurowanie właściwości Centrum oprogramowania
Poniższa procedura służy do konfigurowania szczegóły sekwencji zadań wyświetlana w Centrum oprogramowania. Te informacje są wyłącznie w celach informacyjnych.  
1. W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** > **systemów operacyjnych** > **sekwencji zadań**.
2. Wybierz sekwencję zadań do edycji, a następnie kliknij przycisk **właściwości**.
3. Na **ogólne** kartę, dostępne są następujące ustawienia dla programu Software Center:
  - **Wymagane jest ponowne uruchomienie**: Powiadomi użytkownika, czy ponowne uruchomienie jest wymagane podczas instalacji.
  - **Pobierz rozmiar (MB)**: Określa, ile megabajtów jest wyświetlana w Centrum oprogramowania dla sekwencji zadań.  
  - **Szacowany czas wykonywania (minuty)**: Określa, że szacowany czas wykonywania w minutach, które jest wyświetlane w Centrum oprogramowania dla sekwencji zadań.


## <a name="check-for-running-executable-files-before-installing-an-application"></a>Sprawdź, czy uruchomiony pliki wykonywalne przed zainstalowaniem aplikacji

W  *<deployment type name>*  **właściwości** okno dialogowe typu wdrożenia, na karcie zachowanie instalacji można teraz określić jedną więcej plików wykonywalnych, które działa, spowoduje zablokowania instalacji typu wdrożenia. Użytkownik należy zamknąć plik wykonywalny jest uruchomiona (lub może zostać zamknięty w automatycznie w przypadku wdrożeń z celem wymagane) przed wdrożeniem typ może być instalowany.

### <a name="try-it-out"></a>Wypróbuj to.

1.    We właściwościach typu wdrożenia programu Configuration Manager wybierz **zainstalować zachowanie** kartę.
2.    Wybierz **Dodaj** dodać jedną lub więcej nazw pliku wykonywalnego chcesz sprawdzić. Można również dodać nazwę wyświetlaną, aby ułatwić użytkownikom zidentyfikować aplikacje na liście.
3.    Jeśli wdrożenie ma cel w Kreatorze wdrażania oprogramowania wymagane Opcjonalnie można **automatycznie Zamknij wszystkie uruchomione pliki wykonywalne określone na karcie zachowanie instalacji okna dialogowego właściwości typu wdrożenia**.

Jeśli aplikacja została wdrożona jako **dostępne**i użytkownik końcowy spróbuje zainstalować aplikację, zostanie wyświetlony monit do Zamknij wszystkie uruchomione plików wykonywalnych określona zanim można kontynuować instalacji.

Jeśli aplikacja została wdrożona jako **wymagane**, a opcja **automatycznie Zamknij wszystkie uruchomione pliki wykonywalne określone na karcie zachowanie instalacji okna dialogowego właściwości typu wdrożenia** jest zaznaczone, zobaczy okno dialogowe, które informuje, że określone pliki wykonywalne zostaną automatycznie zamknięte po osiągnięciu ostatecznego terminu instalacji aplikacji. Można zaplanować tych okien dialogowych w **ustawień klienta** > **Agent komputera**. Jeśli nie chcesz użytkownika końcowego, aby wyświetlić te wiadomości, wybierz **Ukryj w programie Software Center i wszystkie powiadomienia** na **środowisko użytkownika** kartę właściwości wdrożenia.

Jeśli aplikacja została wdrożona jako **wymagane** i opcję **automatycznie Zamknij wszystkie uruchomione pliki wykonywalne określone na karcie zachowanie instalacji okna dialogowego właściwości typu wdrożenia** nie jest zaznaczone, a następnie instalacja aplikacji zakończy się niepowodzeniem, jeśli jeden lub więcej określonych aplikacji są uruchomione.

## <a name="create-pfx-certificates-with-s-mime-support"></a>Tworzenie certyfikatów PFX z obsługą S MIME

Teraz można tworzyć profilu certyfikatu PFX, który obsługuje S/MIME i wdrożyć go dla użytkowników.  Ten certyfikat może być następnie używane S/MIME szyfrowania i odszyfrowywania różnych urządzeń zarejestrowanych przez użytkownika.

Ponadto można określić wiele urzędów certyfikacji (CA) na wiele ról systemu lokacji punktu rejestracji certyfikatu i następnie przypisz które przetwarzają żądania urzędów certyfikacji w ramach profilu certyfikatu.

Dla urządzeń z systemem iOS można skojarzyć profil certyfikatu PFX do profilu poczty e-mail i włączyć szyfrowania S/MIME.  Następnie to umożliwi S/MIME w klienta macierzystego poczty e-mail w systemie iOS i kojarzy prawidłowy certyfikat szyfrowania S/MIME do niego.

Aby uzyskać więcej informacji na temat certyfikatów w programie Configuration Manager, zobacz [wprowadzenie do profili certyfikatów w programie System Center Configuration Manager]( https://docs.microsoft.com/sccm/protect/deploy-use/introduction-to-certificate-profiles).


## <a name="new-compliance-settings-for-ios-devices"></a>Nowe ustawienia zgodności dla urządzeń z systemem iOS

Dodano nowe ustawienia, których można użyć w swoich elementów konfiguracji dla urządzeń z systemem iOS. Są to ustawienia, które wcześniej były dostępne w programie Microsoft Intune w konfiguracji autonomicznej i są teraz dostępne przy użyciu usługi Intune z programem Configuration Manager. Jeśli potrzebujesz pomocy przy użyciu tych ustawień, zobacz [ustawień zasad systemu iOS w programie Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/ios-policy-settings-in-microsoft-intune).

- **Zsynchronizuj dane z zarządzanych aplikacji do usługi iCloud**
- **Oddania kontynuowanie działania na inne urządzenie**
- **Funkcje udostępniania w ramach usługi iCloud**
- **Biblioteka zdjęć iCloud**
- **Zaufanie nowego autorzy aplikacji enterprise**
- **Zezwalaj użytkownikom na pobieranie zawartości z flagą "Erotyki" magazynu iBook** (tylko w trybie nadzorowanym)
- **Wymuszaj sparowanego obserwowanie firmy Apple, aby korzystać z nadgarstka wykrywania**
- **Hasło dla AirPlay wychodzących żądań**
- **Zmodyfikuj ustawienia konta** (tylko w trybie nadzorowanym)
- **Zmiany w ustawieniach użycia danych komórkowych aplikacji** (tylko w trybie nadzorowanym)
- **Wymaż całą zawartość i ustawienia** (tylko w trybie nadzorowanym)
- **Konfiguruj ograniczenia na urządzeniu** (tylko w trybie nadzorowanym)
- **Użyj hosta parowania do sterowania urządzeniami można skojarzyć urządzenia z systemem iOS** (tylko w trybie nadzorowanym)
- **Instalowanie konfiguracji profilów i certyfikaty** (tylko w trybie nadzorowanym)
- **Zmiana nazwy urządzenia** (tylko w trybie nadzorowanym)
- **Zmiana kodu dostępu** (tylko w trybie nadzorowanym)
- **Parowanie Apple Watch** (tylko w trybie nadzorowanym)
- **Modyfikacja ustawień powiadomień** (tylko w trybie nadzorowanym)
- **Wallpaper modyfikacji** (tylko w trybie nadzorowanym)
- **Modyfikacja ustawień przesyłania diagnostyki** (tylko w trybie nadzorowanym)
- **Modyfikacja Bluetooth** (tylko w trybie nadzorowanym)
- **AirDrop** (tylko w trybie nadzorowanym)
- **Użyj Siri do zapytania generowane przez użytkownika zawartości z Internetu** (tylko w trybie nadzorowanym)
- **Filtr niestosownych wyrażeń Siri** (tylko w trybie nadzorowanym)
- **Zwracają wyniki z Internetu w centrum uwagi wyszukiwania** (tylko w trybie nadzorowanym)
- **Wyszukiwanie definicji Word** (tylko w trybie nadzorowanym)
- **Klawiatury predykcyjnej** (tylko w trybie nadzorowanym)
- **Korekty automatycznej** (tylko w trybie nadzorowanym)
- **Sprawdzanie pisowni klawiatury** (tylko w trybie nadzorowanym)
- **Skróty klawiaturowe** (tylko w trybie nadzorowanym)
<!--- - **Enterprise app trust settings modification** --->
- **Instalowanie aplikacji przy użyciu programu Apple Configurator i iTunes tylko** (tylko w trybie nadzorowanym)
- **Pobieranie aplikacji automatyczne** (tylko w trybie nadzorowanym)
- **Zmieniać ustawienia aplikacja Znajdź mój znajomych** (tylko w trybie nadzorowanym)
- **Dostęp do magazynu iBooks** (tylko w trybie nadzorowanym)
- **Komunikaty aplikacji** (tylko w trybie nadzorowanym)
- **Transmisje podcast** (tylko w trybie nadzorowanym)
- **Muzyka Apple** (tylko w trybie nadzorowanym)
- **iTunes radiowych** (tylko w trybie nadzorowanym)
- **Grupy dyskusyjne firmy Apple** (tylko w trybie nadzorowanym)
- **Centrum gier** (tylko w trybie nadzorowanym)
- **Traktuj AirDrop jako miejsca docelowego niezarządzane**

## <a name="android-for-work-support"></a>Android obsługi pracy

Począwszy od wersji Technical Preview 1702, można powiązać z konta Google dzierżawcy MDM hybrydowego. Dzięki temu można wykonać następujące czynności:

- Rejestrowanie [obsługiwane urządzenia z systemem Android](https://support.google.com/work/android/answer/6174145?hl=en&ref_topic=6151012) jako Android pracy — Tworzenie profili pracy tych zarejestrowane urządzenia
- Zatwierdź aplikacje Play pracy magazynu, ich synchronizacji z konsoli programu Configuration Manager, a następnie wdrożyć je w profilach pracy urządzeń
- Tworzenie i wdrażanie elementów konfiguracji, aby skonfigurować ustawienia profilu i hasło pracy dla tych urządzeń
- Tworzenie i wdrażanie elementów zasady zgodności i profilów dostępu do zasobów dla systemu Android dla urządzeń w pracy, jak już dla urządzeń z systemem Android
- Przeprowadzić selektywne czyszczenie danych w systemie Android pracy urządzeń

Po zarejestrowaniu urządzenia zgodnie z Android do pracy tworzy profil pracy na urządzeniu Intune, które mogą zarządzać. Ten profil pracy istnieje side-by-side z profilem osobistych na urządzeniu Android. Użytkownicy mogą łatwo przełączać pracy profilu aplikacji i osobiste w profilu aplikacji. Nie można zarządzać elementów w profilu osobistym. Aplikacje osobiste i dane pozostają niezarządzane. Program Configuration Manager ma pełną kontrolę nad profilu pracy i jego zawartość i usunąć go z urządzenia.

Android pracy to platforma oddzielnych z Android i należy zdecydować, który formularz zarządzania dla urządzeń z systemem Android, które obsługują profile pracy.

### <a name="try-it-out"></a>Wypróbuj to!
W poniższych sekcjach opisano Android do zarządzania pracą.

#### <a name="enable-android-for-work-management"></a>Włącz Android do zarządzania pracą
1. Utwórz konto Google w https://accounts.google.com/SignUp do użycia jako Android Twoje konto administratora pracy, która zostanie skojarzona z wszystkich Android dla zadania zarządzania dla tej dzierżawy usługi Intune. Może to być konto Google współużytkowane przez administratorów, którzy zarządzają urządzeniami z systemem Android. To konto Google, używana do zarządzania i publikowania aplikacji w Play dla konsoli pracy w organizacji. Aby zatwierdzić aplikacje w grę dla sklepu pracy, więc śledzić wpisywane nazwę konta i hasło będzie używał tego konta.
2. Włączanie rejestracji Android przez powiązanie konta Google dzierżawcy Intune zarządzane w programie Configuration Manager:
  1. Przejdź do **Administracja** > **Przegląd** > **usług w chmurze** > **subskrypcje usługi Microsoft Intune** i wybierz subskrypcję usługi Intune.
  2. Na wstążce kliknij **Konfiguruj platformy** > **Android** i upewnij się, **rejestracji włączyć Android** jest zaznaczone.
  3. Na wstążce kliknij **Konfiguruj platformy** > **Android pracy**.
  4. W oknie dialogowym kliknij **skonfigurować Android do pracy w konsoli usługi Intune**. W przeglądarce sieci web zostanie otwarta konsola usługi Intune.
  5. Użyj poświadczeń administratora usługi Intune zalogować się do portalu usługi Intune.
  6. Kliknij przycisk **Konfiguruj** otworzyć Android Google Play dla pracy witryny sieci Web.
  7. Firmy Google logowania na stronie wprowadź poświadczenia konta Google z kroku 1, a następnie podaj informacje o firmie.
3. Po powrocie do portalu Intune Android pracy jest włączona i ma trzy opcje rejestracji dla systemu Android dla pracy urządzeń:
  - **Zarządzanie urządzeniami wszystkie jako Android** — (wyłączony) Android wszystkich urządzeń, w tym urządzeń, które obsługują Android do pracy, zostaną zarejestrowane jako konwencjonalne urządzenia z systemem Android
  - **Zarządzanie urządzeniami obsługiwane jako Android pracy** — (Enabled) zarejestrowane jako Android wszystkie urządzenia Android pracy dla pracy urządzeń. Wszelkie urządzenia Android, który nie obsługuje Android do pracy jest zarejestrowany jako urządzenie konwencjonalnych Android.
  - **Zarządzanie obsługiwane urządzenia dla użytkowników tylko w tych grupach jako Android pracy** -(testowanie) umożliwia Android są przeznaczone do pracy zarządzania ograniczony zestaw użytkowników. Tylko członkowie wybranej grupy, którzy rejestrują urządzenia obsługującego Android do pracy są rejestrowane jako Android dla urządzeń w pracy. Wszystkie inne zarejestrowane jako urządzenia z systemem Android.
  
> [!NOTE]
> Zapobiega to znany problem **Zarządzaj obsługiwane urządzenia dla użytkowników tylko w tych grupach jako Android pracy** opcję działać zgodnie z oczekiwaniami. Urządzenia użytkowników w określonej usłudze Azure AD będą rejestrować grup jako Android zamiast Android do pracy. Aby przetestować Android do pracy, należy użyć **Zarządzanie wszystkich obsługiwanych urządzeń jako Android pracy**.


  W celu umożliwienia Android do pracy rejestracji, należy wybierz jedną z opcji u dołu dwa. **Zarządzaj obsługiwane urządzenia dla użytkowników tylko w tych grupach jako Android pracy** opcja wymaga, należy najpierw zdefiniować grupy zabezpieczeń usługi Azure Active Directory.

Po zakończeniu powiązania; zostaną wyświetlone nazwę konta i nazwę organizacji w portalu usługi Intune w tym momencie możesz zamknąć obie przeglądarki.

#### <a name="approve-and-deploy-android-for-work-apps"></a>Zatwierdzanie i wdrażanie Android dla aplikacji do pracy
Wykonaj te kroki, aby zatwierdzić aplikacje w grę dla sklepu pracy, synchronizować je do konsoli programu Configuration Manager i wdrażanie ich Android zarządzanych urządzeń w pracy. Aby wdrożyć aplikacje profilów użytkowników pracy, musisz zatwierdzić aplikacje Play pracy, a następnie synchronizacji aplikacji za pomocą konsoli programu Configuration Manager.

1. Otwórz przeglądarkę i przejdź do: https://play.google.com/work.
2. Zaloguj się przy użyciu konta administratora Google związana z dzierżawą usługi Intune.
3. Przeglądanie w poszukiwaniu aplikacji, które chcesz wdrożyć w danym środowisku i kliknij przycisk **Zatwierdź** dla każdego z nich.
4. W konsoli programu Configuration Manager, przejdź do **administratora** > **Przegląd** > **usług w chmurze** > **Android pracy** i kliknij przycisk **synchronizacji**.
5. Poczekaj, aż do 10 minut dla aplikacji do synchronizacji, a następnie przejdź **Biblioteka oprogramowania** > **Przegląd** > **zarządzania aplikacjami** > **informacji o licencji dla aplikacji do sklepu**.
6. Kliknij aplikację zsynchronizowane z Play pracy, a następnie kliknij przycisk **tworzenie aplikacji**.
7. Zakończ pracę kreatora i kliknij przycisk **Zamknij**.
8. Przejdź do **Biblioteka oprogramowania** > **Przegląd** > **zarządzania aplikacjami** > **aplikacji**, wybierz Android dla aplikacji do pracy i wdrażania w zwykły sposób.

Aby zsynchronizować Play dla aplikacji do pracy z programem Configuration Manager, należy zatwierdzić co najmniej jedną aplikację na Play pracy witryny sieci Web.

#### <a name="enroll-an-android-for-work-device"></a>Rejestrowanie Android pracy urządzenia
Jak zarejestrować Android urządzeń pracy jest podobne do rejestracji dla systemu Android. Pobierz i uruchom aplikację Portal firmy dla systemu Android na urządzeniu przenośnym. Użytkownik jest monitowany utworzyć profil pracy w ramach procesu rejestracji.  Po utworzeniu profilu pracy, musisz przełączyć się do zarządzanego wersji portalu firmy. Zarządzanych aplikacji Portal firmy jest oznaczane małe Aktówki pomarańczowy w prawym dolnym rogu.

#### <a name="create-and-deploy-a-configuration-item"></a>Tworzenie i wdrażanie elementu konfiguracji
Android do pracy składa się z dwóch grup ustawienie pozycji konfiguracji:
- Hasło
- Profil pracy

Można skonfigurować zawartości udostępnianie między profili pracy, jak również następujące elementy konfiguracji na urządzeniach z systemem Android 6 lub nowszej:
- Zachowanie aplikacji z prośbą o określonych uprawnień
- Czy powiadomienia dla aplikacji w ramach profilu pracy są widoczne na ekranie blokady

To spróbować utworzyć element konfiguracji za pomocą standardowych przepływu pracy, wybierz polecenie **Android pracy** na **ogólne** strony i skonfiguruj ustawienia dla każdej grupy ustawień, dodawanie elementów konfiguracji do linii bazowej i wdrażanie w zwykły sposób. Te ustawienia będą stosowane tylko do urządzeń zarejestrowane jako Android na potrzeby pracy, a nie te, które zarejestrowane jako Android.

#### <a name="perform-selective-wipe"></a>Przeprowadzić selektywne czyszczenie danych
Urządzenia zarejestrowane jako Android do pracy tylko można selektywnie ponieważ tylko Zarządzanie profilu pracy. Chroni to ten profil z jest wyczyszczone. Wykonywanie selektywne czyszczenie danych w systemie Android pracy urządzenia Usuwa profil pracy, w tym wszystkie aplikacje i dane i unenrolls urządzenia.

Aby selektywnie wyczyść Android pracy urządzenia, użyj normalnych [proces selektywnego czyszczenia](https://docs.microsoft.com/sccm/mdm/deploy-use/wipe-lock-reset-devices#selective-wipe) w konsoli programu Configuration Manager.

#### <a name="known-issues-for-android-for-work"></a>Znane problemy dotyczące Android do pracy
**Konfigurowanie synchronizacji w Android o przyczynach profile poczty e-mail pracy były zaplanowane Niepowodzenie wdrażania** jest jedną z opcji w interfejsie użytkownika programu ConfigMgr dla systemu Android profili poczty e-mail pracy "Harmonogram". Na innych platformach dzięki temu administrator, aby skonfigurować harmonogram do synchronizowania poczty e-mail i innych danych konta poczty e-mail do urządzeń przenośnych, które wdrożenia. Nie działa dla systemu Android profili poczty e-mail w pracy i wybierając opcję żadnych innych niż "Nie skonfigurowano" spowoduje, że w profilu nie można wdrożyć na żadnych urządzeniach.

