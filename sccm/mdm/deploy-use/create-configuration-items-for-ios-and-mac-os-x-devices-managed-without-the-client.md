---
title: "Tworzenie elementów konfiguracji dla systemów iOS i Mac OS X urządzeń zarządzanych za pomocą usługi Intune | Dokumentacja firmy Microsoft"
description: "Użycie elementu konfiguracji systemu Mac OS X i iOS programu System Center Configuration Manager do zarządzania ustawieniami dla systemów iOS i Mac OS X urządzeń."
ms.custom: na
ms.date: 03/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 613a48ac-c55d-4c4a-94ea-d3747a1b10cb
caps.latest.revision: 15
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 6e2cb628217598480973d4f728a9e0a7cd5873e7
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-create-configuration-items-for-ios-and-mac-os-x-devices-managed-with-intune"></a>Tworzenie elementów konfiguracji dla systemów iOS i Mac OS X urządzeń zarządzanych za pomocą usługi Intune
Użyj programu System Center Configuration Manager **iOS i Mac OS X** elementu konfiguracji do zarządzania ustawieniami dla systemów iOS i Mac OS X urządzeń, które są zarejestrowane w usłudze Microsoft Intune lub lokalnych zarządzanych przez program Configuration Manager.  
  
### <a name="to-create-an-ios-and-mac-os-x-configuration-item"></a>Aby utworzyć element konfiguracji systemów iOS i Mac OS X  
  
1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność**.  
  
2.  W obszarze roboczym **Zasoby i zgodność** rozwiń węzeł **Ustawienia zgodności**, a następnie kliknij pozycję **Elementy konfiguracji**.  
  
3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij pozycję **Utwórz element konfiguracji**.  
  
4.  Na stronie **Ogólne** w **Kreatorze tworzenia elementu konfiguracji** podaj nazwę i opcjonalny opis elementu konfiguracji.  
  
5.  W obszarze **Określ typ elementu konfiguracji, który chcesz utworzyć** wybierz pozycję **iOS i Mac OS X**.  
  
6.  Kliknij przycisk **kategorii** należy utworzyć i przypisać kategorie ułatwiają wyszukiwanie i filtrowanie elementów konfiguracji w konsoli programu Configuration Manager.  
  
7.  Na stronie **Obsługiwane platformy** kreatora wybierz platformy systemów iOS i Mac OS X, które będą oceniać element konfiguracji.  
  
8.  Na stronie **Ustawienia urządzenia** kreatora wybierz grupę ustawień, którą chcesz skonfigurować. Zobacz sekcję [Informacje dotyczące ustawień elementu konfiguracji systemów iOS i Mac OS X](#BKMK_Setref) w tym temacie, aby uzyskać szczegółowe informacje, a następnie kliknij pozycję **Dalej**.  
  
    > [!TIP]  
    >  Jeśli danego ustawienia nie ma na liście, zaznacz pole wyboru **Konfiguruj dodatkowe ustawienia, nieobjęte domyślnymi grupami ustawień**.  
  
9. Na każdej stronie ustawień skonfiguruj odpowiednie ustawienia i określ, czy chcesz je skorygować w razie braku ich zgodności na urządzeniach (jeśli jest to obsługiwane).  
  
10. Dla każdej grupy ustawień można również skonfigurować ważność, która będzie zgłaszana w przypadku braku zgodności znalezionego elementu konfiguracji:  
  
    -   **Brak** -urządzeń, które nie spełniają tej zasady zgodności, będą zgłaszać ważności niepowodzenia dla raportów programu Configuration Manager.  
  
    -   **Informacje o** -urządzeń, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **informacji** dla raportów programu Configuration Manager.  
  
    -   **Ostrzeżenie** -urządzeń, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **ostrzeżenie** dla raportów programu Configuration Manager.  
  
    -   **Krytyczne** -urządzeń, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczny** dla raportów programu Configuration Manager.  
  
    -   **Krytyczne ze zdarzeniem** -urządzeń, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczny** dla raportów programu Configuration Manager. Ten poziom ważności jest też rejestrowany jako zdarzenie systemu Windows w dzienniku zdarzeń aplikacji.  
  
11. Na stronie **Możliwość zastosowania platformy** kreatora przejrzyj ustawienia, które nie są zgodne z wybranymi wcześniej obsługiwanymi platformami. Możesz wrócić i usunąć te ustawienia lub kontynuować.  
  
    > [!TIP]  
    >  Nieobsługiwane ustawienia nie są oceniane pod kątem zgodności.  
  
12. Ukończ pracę kreatora.  
  
 Możesz wyświetlić nowy element konfiguracji w węźle **Elementy konfiguracji** obszaru roboczego **Zasoby i zgodność**.  
  
##  <a name="ios-and-mac-os-x-configuration-item-settings-reference"></a>Informacje dotyczące ustawień elementu konfiguracji systemów iOS i Mac OS X  
  
###  <a name="password"></a>Hasło  
  
|Nazwa ustawienia|Szczegóły|  
|------------------|-------------|  
|**Wymagaj ustawień haseł na urządzeniach przenośnych**|Wymagaj hasła na obsługiwanych urządzeniach.|  
|**Maksymalna długość hasła (w znakach)**|Minimalna długość hasła.|  
|**Wygaśnięcie hasła w dniach**|Liczba dni, po której należy zmienić hasło.|  
|**Liczba zapamiętanych haseł**|Zapobiega ponownemu użyciu hasła stosowanego wcześniej.|  
|**Liczba nieudanych prób logowania przed usunięciem zawartości urządzenia**|Czyści urządzenie po określonej liczbie prób logowania zakończonych niepowodzeniem.<br /><br /> (dotyczy tylko urządzeń z systemem iOS)|  
|**Złożoność hasła**|Wybierz, czy można określić numer PIN, taki jak 1234, czy też należy podać silne hasło.| 
|**Zezwalaj na proste hasła**|Zezwalaj na proste hasła, takich jak **0000** i **1234**.|
|**Odblokowywanie odciskiem linii papilarnych**|Zezwalaj na odblokowywanie urządzenia przy użyciu linii papilarnych.|
|**Zmiana kodu dostępu** (tylko nadzorowane)|Zezwalaj na hasło urządzenia, aby dodać, zmienić lub usunąć.|
  
###  <a name="device"></a>Urządzenie  
 Te ustawienia dotyczą zarówno urządzeń z systemem iOS, jak i urządzeń z systemem Mac OS X.  
  
|Nazwa ustawienia|Szczegóły|  
|------------------|-------------|  
|**Dodaj przyjaciół Centrum gier**|Umożliwia dodanie znajomych w aplikacji Centrum gier.|
|**Wybieranie głosowe**|Umożliwia korzystanie z funkcji wybierania głosowego na urządzeniu.|  
|**Asystent głosowy**|Umożliwia korzystanie z aplikacji asystentów głosowych, takich jak Siri.|  
|**Asystent głosowy, gdy zablokowany**|Umożliwia korzystanie z aplikacji asystentów głosowych, takich jak Siri, gdy urządzenie jest zablokowane.|  
|**Przechwytywanie ekranu**|Umożliwia wykonanie zrzutu ekranu urządzenia.|  
|**Klient czacie wideo**|Umożliwia korzystanie z aplikacji rozmów wideo, takich jak Facetime.|  
|**Gry dla wielu graczy**|Umożliwia granie w gry z innymi osobami w Internecie.|  
|**Oprogramowanie osobistego portfela, gdy zablokowany**|Umożliwia korzystanie z oprogramowania osobistego portfela, takiego jak aplikacja Passbook.|  
|**Przesłanie danych diagnostycznych**|Umożliwia przesyłanie plików dzienników aplikacji.|  
|**Powiadomienia Centrum akcji**|Zezwalaj użytkownikowi na dostęp do widoku powiadomień bez odblokowywania urządzenia.|
|**Muzyka Apple** (tylko nadzorowane)|Zezwalaj na korzystanie z aplikacji muzyka firmy Apple.|
|**Transmisje podcast** (tylko nadzorowane)|Zezwalaj na korzystanie z aplikacji transmisje podcast.|
|**Komunikaty aplikacji** (tylko nadzorowane)|Zezwalaj na korzystanie z aplikacji wiadomości do wysyłania wiadomości SMS.|
|**Wallpaper modyfikacji** (tylko nadzorowane)|Zezwalaj użytkownikom na zmianę tapetę na urządzeniu.|
|**Wyszukiwanie definicji Word** (tylko nadzorowane)|Zezwalaj na funkcję iOS umożliwiający wyróżnić wyraz i wyszukać jego definicji.|
|**Wykrycie nadgarstka sparowanego obserwowanie firmy Apple**|Po włączeniu Apple Watch nie będzie wyświetlać powiadomienia, gdy nie trwa zużyte.|
|**Filtr niestosownych wyrażeń Siri** (tylko nadzorowane)|Zapobiega Siri z dyktowania lub mówić obsceniczne języka.|
|**Zmiana nazwy urządzenia** (tylko nadzorowane)|Zezwalaj użytkownikom na zmianę nazwy urządzenia.|
|**Modyfikacja ustawień przesyłania diagnostyki** (tylko nadzorowane)|Zezwalania lub blokowania urządzenia przesyłanie danych diagnostycznych do firmy Apple.|
|**Centrum gier** (tylko nadzorowane)|Zezwalaj na korzystanie z aplikacji Game Center.|
|**iTunes radiowych** (tylko nadzorowane)|Zezwalaj na korzystanie z aplikacji radiowych iTunes.|
|**Grupy dyskusyjne firmy Apple** (tylko nadzorowane)|Zezwalaj na korzystanie z aplikacji grup dyskusyjnych firmy Apple.|
|**Parowanie Apple Watch** (tylko nadzorowane)|Zezwalaj na urządzenie, aby skojarzyć Apple Watch.|
|**Korekty automatycznej** (tylko nadzorowane)|Służy do urządzenie automatycznie poprawić błędnie napisanych wyrazów.|
|**Modyfikacja Bluetooth** (tylko nadzorowane)|Umożliwia użytkownikowi zmianę ustawień Bluetooth na urządzeniu.|
|**Zmiany w ustawieniach użycia danych komórkowych aplikacji** (tylko nadzorowane)|Zezwalaj użytkownikowi na aplikacje, które mogą używać danych komórkowych formantu.|
|**Skróty klawiaturowe** (tylko nadzorowane)|Umożliwia używanie skrótów klawiaturowych.|
|**Klawiatury predykcyjnej** (tylko nadzorowane)|Zezwalaj na używanie klawiatury predykcyjnej, które sugerują wyrazy, które użytkownik może być.|
|**Sprawdzanie pisowni klawiatury** (tylko nadzorowane)|Umożliwia sprawdzania pisowni urządzenia.|
|**Modyfikacja ustawień powiadomień** (tylko nadzorowane)|Zezwalaj użytkownikom na zmianę ustawienia powiadomień urządzenia.|
|**Zwracają wyniki z Internetu w centrum uwagi wyszukiwania** (tylko nadzorowane)|Niech nawiązać połączenie z Internetem, aby dostarczyć więcej wyników wyszukiwania w centrum uwagi.|
|**Użyj Siri do zapytania generowane przez użytkownika zawartości z Internetu** (tylko nadzorowane)|Zezwalaj na Siri uzyskać dostęp do witryn sieci Web w odpowiedzi na pytania.|

  
###  <a name="store"></a>Magazyn  
 Te ustawienia dotyczą tylko urządzeń z systemem iOS.  
  
|Nazwa ustawienia|Szczegóły|  
|------------------|-------------|  
|**Sklep z aplikacjami**|Umożliwia dostęp do sklepu z aplikacjami na urządzeniu.|  
|**Wprowadź hasło w celu dostępu do sklepu z aplikacjami**|Użytkownicy muszą wprowadzić hasło, aby uzyskać dostęp do sklepu z aplikacjami.|  
|**Zakupy w aplikacjach**|Umożliwia użytkownikom dokonywanie zakupów w aplikacjach.|
|**Instalowanie aplikacji przy użyciu programu Apple Configurator i iTunes tylko** (tylko nadzorowane)|Włącza lub wyłącza sklepu z aplikacjami z ekranu głównego urządzenia. Użytkownicy mogą nadal używać do instalowania i aktualizowania aplikacji iTunes lub narzędzia Apple Configurator.|
|**Dostęp do magazynu iBooks** (tylko nadzorowane)|Zezwalaj użytkownikowi na przeglądanie i zakupu książki z magazynu iBooks.|
|**Pobieranie aplikacji automatyczne** (tylko nadzorowane)|Zezwalaj na aplikacje zakupione na innych urządzeniach do automatycznego pobierania do tego urządzenia. To ustawienie nie wpływa na aktualizacje aplikacji.|

  
###  <a name="browser"></a>Przeglądarka  
 Te ustawienia dotyczą tylko urządzeń z systemem iOS.  
  
|Nazwa ustawienia|Szczegóły|  
|------------------|-------------|  
|**Przeglądarka domyślna**|Użytkownik może zmienić domyślną przeglądarkę internetową.|  
|**Autowypełnianie**|Użytkownik może zmienić ustawienia autowypełniania w przeglądarce.|  
|**Wykonywanie skryptów aktywnych**|Przeglądarka może uruchamiać skrypty, takie jak skrypty kontrolek ActiveX.|  
|**Blokowanie wyskakujących okienek**|Włącza lub wyłącza blokowanie wyskakujących okienek w przeglądarce.|  
|**Plik cookie**|Zezwalaj na zapisywanie plików cookie na urządzeniu.|  
|**Ostrzeżenie o oszustwie**|Włącz lub wyłącz ostrzeżenia o potencjalnych fałszywych witrynach sieci Web.|  
  
###  <a name="content-rating"></a>Ocena zawartości  
 Te ustawienia dotyczą tylko urządzeń z systemem iOS.  
  
|Nazwa ustawienia|Szczegóły|  
|------------------|-------------|  
|**Zawartość dla dorosłych w sklepie z multimediami**|Określ, czy chcesz zezwolić na dostęp do zawartości dla dorosłych w sklepie z aplikacjami.|  
|**Region klasyfikacji**|Określa kraj, dla którego chcesz zastosować ograniczenia klasyfikacji.|  
|**Klasyfikacja filmu**|Określ maksymalny dozwolony poziom klasyfikacji treści filmu.|  
|**Pokaż TV klasyfikacji**|Określ maksymalny dozwolony poziom klasyfikacji treści programu TV.|  
|**Klasyfikacja aplikacji**|Określ maksymalny dozwolony poziom klasyfikacji treści aplikacji.| 
|**Zawartości z flagą "Erotyki" magazynu iBook** (tylko nadzorowane)|Zezwalaj użytkownikowi na pobieranie książki z kategorii "Erotyki".| 
  
> [!NOTE]  
>  Dostępne klasyfikacje różnią się w zależności od wybranej opcji ustawienia **Region klasyfikacji**.  
  
###  <a name="cloud"></a>Chmura  
 Te ustawienia dotyczą tylko urządzeń z systemem iOS.  
  
|Nazwa ustawienia|Szczegóły|  
|------------------|-------------|  
|**Kopia zapasowa w chmurze**|Zezwalaj na tworzenie kopii zapasowych w usłudze w chmurze, takiej jak iCloud.|  
|**Zaszyfrowanej kopii zapasowej**|Zezwalaj na szyfrowanie kopii zapasowych w usłudze w chmurze.|  
|**Synchronizacja dokumentów**|Zezwalaj na synchronizację dokumentów z usługą w chmurze.|  
|**Synchronizacja zdjęć**|Zezwalaj na synchronizację zdjęć z usługą w chmurze.| 
|**Biblioteka zdjęć iCloud**|Jeśli ustawiono **nr**, wyłącza używanie biblioteki zdjęć iCloud, która pozwala na przechowywanie zdjęć i klipów wideo w chmurze. Żadnych zdjęć nie są w pełni pobrane z usługi i cloud biblioteka fotografii na urządzeniu zostaną usunięte z urządzenia, jeśli wartość atrybutu to **nr**.|
|**Funkcje udostępniania w ramach usługi iCloud**|Ustaw **nr** wyłączyć funkcje udostępniania iCloud na urządzeniu.|
|**Oddania kontynuowanie działania na inne urządzenie**|Zezwalaj użytkownikowi na kontynuowanie pracy, które zostały rozpoczęte na urządzenia iOS w innym systemie iOS lub Mac OS X.|
|**Zsynchronizuj dane z zarządzanych aplikacji do usługi iCloud**|Zezwalaj na aplikacje, które można zarządzać za pomocą usługi Intune do synchronizacji danych do konta usługi i cloud.|

  
###  <a name="security"></a>Zabezpieczenia  
 Te ustawienia dotyczą tylko urządzeń z systemem iOS.  
  
|Nazwa ustawienia|Szczegóły|  
|------------------|-------------|  
|**Aparat fotograficzny**|Zezwalaj na korzystanie z aparatu fotograficznego urządzenia.| 
|**Zaufanie nowego autorzy aplikacji enterprise**|Umożliwia użytkownikowi wybranie zaufania aplikacji, które nie zostały pobrane ze sklepu z aplikacjami.| 
  
###  <a name="roaming"></a>Roaming  
 Te ustawienia dotyczą tylko urządzeń z systemem iOS.  
  
|Nazwa ustawienia|Szczegóły|  
|------------------|-------------|  
|**Roaming połączeń głosowych**|Umożliwia połączenia głosowe podczas roamingu.|  
|**Automatyczna synchronizacja podczas roamingu**|Umożliwia automatyczną synchronizację urządzenia podczas roamingu.|  
|**Roaming danych**|Umożliwia roaming między sieciami przy dostępie do danych.|  
  
###  <a name="system-security"></a>Zabezpieczenia systemu  
 Te ustawienia dotyczą tylko urządzeń z systemem iOS.  
  
|Nazwa ustawienia|Szczegóły|  
|------------------|-------------|  
|**Użytkownik zamierza zaakceptować niezaufane certyfikaty TLS**|Opcja **Dozwolone** umożliwia użytkownikowi akceptowanie tych certyfikatów. Opcja **Zabronione** powoduje automatyczne odrzucanie certyfikatów niezaufanych.|
|**Zezwalaj na blokadę aktywacji (tylko w trybie nadzorowanym)**|To ustawienie umożliwia włączanie blokady aktywacji w systemie iOS na **nadzorowanych** urządzeniach z systemem iOS, którymi możesz zarządzać. Aby uzyskać więcej informacji na temat blokady aktywacji, zobacz [Manage iOS Activation Lock with System Center Configuration Manager](../../mdm/deploy-use/manage-ios-activation-lock.md) (Zarządzanie blokadą aktywacji systemu iOS w programie System Center Configuration Manager).
|**Ekran blokady — centrum sterowania**|Określa, czy aplikacja Centrum sterowania jest dostępna, gdy urządzenie jest zablokowane.|  
|**Widok powiadomienia na ekranie blokady**|Określa, czy można wyświetlać powiadomienia, gdy urządzenie jest zablokowane.|  
|**Widoku dziś na ekranie blokady**|Określa, czy można wyświetlać widok Dzisiaj, gdy urządzenie jest zablokowane.|  
|**Zmodyfikuj ustawienia konta** (tylko nadzorowane)|Zezwalaj użytkownikom na zmianę ustawienia konta, takie jak konfiguracje wiadomości e-mail.|
|**Zmieniać ustawienia aplikacja Znajdź mój przyjaciół** (tylko nadzorowane)|Zezwalaj użytkownikom na zmianę ustawień aplikacji Znajdź mój znajomych.|
|**Użyj hosta parowania do sterowania urządzeniami można skojarzyć urządzenia z systemem iOS** (tylko nadzorowane)|Zezwalaj na hosta parowania umożliwi kontroli administratora urządzeń, które można skojarzyć urządzenia z systemem iOS.|
|**Wymaż całą zawartość i ustawienia** (tylko nadzorowane)|Zezwalaj użytkownikowi na za pomocą opcji wymazywanie całą zawartość i ustawienia na urządzeniu.|
|**Konfiguruj ograniczenia na urządzeniu** (tylko nadzorowane)|Zezwalaj użytkownikowi na konfigurowanie ograniczenia urządzenia (kontroli rodzicielskiej) na urządzeniu.|
|**Instalowanie konfiguracji profilów i certyfikaty** (tylko nadzorowane)|Zezwalaj użytkownikowi na instalowanie konfiguracji profilów i certyfikatów.|
|**Hasło dla AirPlay wychodzących żądań**|Wymagaj hasła parowania, gdy użytkownik korzysta z AirPlay do strumieniowego przesyłania zawartości do urządzeń firmy Apple.|
  
###  <a name="data-protection"></a>Ochrona danych  
 Te ustawienia dotyczą tylko urządzeń z systemem iOS.  
  
|Nazwa ustawienia|Szczegóły|  
|------------------|-------------|  
|**Otwieranie dokumentów zarządzanych aplikacji w innych aplikacjach niezarządzanych**|Do użytku z aplikacji zarządzanych przez Menedżera konfiguracji zasad zarządzania aplikacjami.|  
|**Otwórz dokumenty z niezarządzanych aplikacji w innych zarządzanych aplikacjach**|Do użytku z aplikacji zarządzanych przez Menedżera konfiguracji zasad zarządzania aplikacjami.| 
|**Traktuj AirDrop jako niezarządzane docelowej** (tylko nadzorowane)|Zatrzymuje aplikacje zarządzane mogą wysyłać dane przy użyciu. Airdrop.|
|**AirDrop** (tylko nadzorowane)|Zezwalaj na używanie funkcji AirDrop do wymiany zawartości z urządzeń w pobliżu.|
  
###  <a name="compliant-and-noncompliant-apps-ios"></a>Zgodne i niezgodne aplikacje (iOS)  
 Umożliwia określenie listy zgodnych i niezgodnych aplikacji systemu iOS w firmie. Następnie można użyć raportów w celu wyświetlenia urządzeń z zainstalowanymi niezgodnymi aplikacjami oraz skojarzonego użytkownika.  
  
 W tym samym elemencie konfiguracji nie można określić zgodnych i niezgodnych aplikacji.  
  
#### <a name="to-specify-the-compliant-or-noncompliant-apps-list"></a>Aby określić listę zgodnych lub niezgodnych aplikacji  
  
1.  Na stronie **Zgodne i niezgodne aplikacje (iOS)** podaj następujące informacje:  
  
    -   **Lista niezgodnych aplikacji** — wybierz tę opcję, aby określić listę aplikacji, które będą zgłaszane jako niezgodne, jeśli zostaną zainstalowane przez użytkowników.  
  
    -   **Lista zgodnych aplikacji** — wybierz tę opcję, aby określić listę aplikacji, które użytkownicy mogą instalować. Wszystkie inne zainstalowane aplikacje będą zgłaszane jako niezgodne.  
  
    -   **Dodaj** — dodaje aplikację do wybranej listy. Wprowadź wybraną nazwę, opcjonalnie wydawcę aplikacji, a także adres URL aplikacji w sklepie z aplikacjami.  
  
         Aby określić adres URL, w sklepie iTunes App Store znajdź aplikację, której chcesz użyć.  
  
         Otwórz stronę instalacji aplikacji i skopiuj adres URL do schowka. Możesz teraz użyć tego adresu URL na liście zgodnych lub niezgodnych aplikacji.  
  
         **Przykład:** Wyszukaj w sklepie **Microsoft Word for iPad** aplikacji. Adres URL, którego użyjesz, to **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8**.  
  
    -   **Edytuj** — umożliwia edytowanie nazwy, wydawcy i adresu URL wybranej aplikacji.  
  
    -   **Usuń** — usuwa wybraną aplikację z listy.  
  
    -   **Importuj** — importuje listę aplikacji wprowadzoną w pliku w formacie wartości rozdzielanych przecinkami. W pliku użyj formatu: nazwa aplikacji, wydawca, adres URL.  
  
2.  Po zakończeniu kliknij pozycję **Dalej**.  
  
 Aby monitorować zgodne i niezgodne aplikacje, możesz użyć jednego z następujących raportów:  
  
-   **Lista niezgodnych aplikacji i urządzeń dla określonego użytkownika** — zawiera informacje o użytkownikach i urządzeniach z zainstalowanymi aplikacjami niezgodnymi z określonymi zasadami.  
  
-   **Podsumowanie użytkowników z niezgodnymi aplikacjami** — zawiera informacje o użytkownikach z zainstalowanymi aplikacjami niezgodnymi z określonymi zasadami.  
  
 Aby uzyskać informacje na temat korzystania z raportów, zobacz [Raportowanie w programie System Center Configuration Manager](../../core/servers/manage/reporting.md).  
  
###  <a name="compliant-and-noncompliant-apps-mac-os-x"></a>Zgodne i niezgodne aplikacje (Mac OS X)  
 Umożliwia określenie listy zgodnych i niezgodnych aplikacji systemu Mac OS X w firmie. Następnie można użyć raportów w celu wyświetlenia urządzeń z zainstalowanymi niezgodnymi aplikacjami oraz skojarzonego użytkownika.  
  
 W tym samym elemencie konfiguracji nie można określić zgodnych i niezgodnych aplikacji.  
  
#### <a name="to-specify-the-compliant-or-noncompliant-apps-list"></a>Aby określić listę zgodnych lub niezgodnych aplikacji  
  
1.  Na stronie **Zgodne i niezgodne aplikacje (Mac OS X)** podaj następujące informacje:  
  
    -   **Lista niezgodnych aplikacji** — wybierz tę opcję, aby określić listę aplikacji, które będą zgłaszane jako niezgodne, jeśli zostaną zainstalowane przez użytkowników.  
  
    -   **Lista zgodnych aplikacji** — wybierz tę opcję, aby określić listę aplikacji, które użytkownicy mogą instalować. Wszystkie inne zainstalowane aplikacje będą zgłaszane jako niezgodne.  
  
    -   **Dodaj** — dodaje aplikację do wybranej listy. Określ nazwę, wydawcę aplikacji (opcjonalnie) i identyfikator pakietu aplikacji.  
  
        > [!TIP]  
        >  Aby znaleźć identyfikator pakietu aplikacji, wykonaj następujące czynności na komputerze Mac z zainstalowaną aplikacją:  
        >   
        >  1.  Otwórz folder, w którym zainstalowano aplikację (na przykład **/Aplikacje**).  
        > 2.  Wybierz pakiet *<Nazwa aplikacji>\>***.app**, a następnie wybierz pozycję **Pokaż zawartość pakietu**.  
        > 3.  Otwórz plik **Info.plist**.  
        > 4.  Sprawdź wartość skojarzoną z kluczem **CFBundleIdentifier**.  
        >   
        >  Identyfikator pakietu ma format **com.contoso.nazwa_aplikacji**.  
  
    -   **Edytuj** — umożliwia edytowanie nazwy, wydawcy i identyfikatora pakietu wybranej aplikacji.  
  
    -   **Usuń** — usuwa wybraną aplikację z listy.  
  
    -   **Importuj** — importuje listę aplikacji wprowadzoną w pliku w formacie wartości rozdzielanych przecinkami. W pliku użyj formatu: nazwa aplikacji, wydawca, identyfikator pakietu aplikacji.  
  
2.  Po zakończeniu kliknij pozycję **Dalej**.  
  
 Aby monitorować zgodne i niezgodne aplikacje, możesz użyć jednego z następujących raportów:  
  
-   **Lista niezgodnych aplikacji i urządzeń dla określonego użytkownika** — zawiera informacje o użytkownikach i urządzeniach z zainstalowanymi aplikacjami niezgodnymi z określonymi zasadami.  
  
-   **Podsumowanie użytkowników z niezgodnymi aplikacjami** — zawiera informacje o użytkownikach z zainstalowanymi aplikacjami niezgodnymi z określonymi zasadami.  
  
 Aby uzyskać informacje na temat korzystania z raportów, zobacz [Raportowanie w programie System Center Configuration Manager](../../core/servers/manage/reporting.md).  
  
### <a name="ios-and-mac-os-x-custom-profile-settings"></a>Niestandardowe ustawienia profilów dla systemów iOS i Mac OS X  
 **Profile niestandardowe systemów iOS i Mac OS X** umożliwiają wdrażanie ustawień utworzonych przy użyciu [narzędzia Apple Configurator](https://itunes.apple.com/us/app/apple-configurator-2/id1037126344?mt=12) na urządzeniach z systemem iOS lub Mac OS X. To narzędzie umożliwia tworzenie wielu ustawień do kontroli działania tych urządzeń oraz eksportowanie ich do profilu konfiguracji. Następnie można zaimportować ten profil konfiguracji do profilu niestandardowego systemów iOS i Mac OS X oraz wdrożyć ustawienia dla użytkowników i urządzeń w organizacji.  
  
> [!NOTE]  
>  Upewnij się, że ustawienia wyeksportowane z narzędzia Apple Configurator są zgodne z wersją systemu iOS lub Mac OS X na urządzeniach, na których jest wdrażany profil. Aby uzyskać informacje o sposobie postępowania w przypadku niezgodnych ustawień, wyszukaj dokumenty Configuration Profile Reference i Mobile Device Management Protocol Reference w witrynie sieci Web [Apple Developer](https://developer.apple.com/).  
  
#### <a name="to-create-an-ios-and-mac-os-x-custom-profile"></a>Aby utworzyć profil niestandardowy systemów iOS i Mac OS X  
  
1.  Na stronie **Konfigurowanie ustawień profilu niestandardowego systemów iOS i Mac OS X** **Kreatora tworzenia elementu konfiguracji** podaj następujące informacje:  
  
    -   **Nazwa niestandardowego profilu konfiguracji (wyświetlana dla użytkowników)** — Podaj nazwę zasad, która będzie wyświetlana na urządzeniu i w konfiguracji Menedżera raportów.  
  
    -   **Importuj** — wybierz plik wyeksportowany za pomocą narzędzia Apple Configurator.  
  
    -   **Szczegóły profilu konfiguracji** — wyświetla zaimportowany plik.  
  
    -   **Korygowanie niezgodnych ustawień** -  
  
         Wybierz tę opcję, jeśli chcesz skorygować niezgodne ustawienia konfiguracji (jeśli jest to obsługiwane).  
  
    -   **Waga niezgodności do raportów** — określ poziom ważności zgłaszany w przypadku oceny tych zasad zgodności jako niezgodnych. Poniżej przedstawiono dostępne poziomy ważności:  
  
        > [!NOTE]  
        >  Jeśli urządzenie z systemem Mac OS X jest w trybie uśpienia, nie można dostarczać zasad i profilów ani dodawać ich do spisu. W związku z tym konsoli programu Configuration Manager może tymczasowo wyświetlić ustawienia zasad stanu błędu aż do następnej urządzenie wznawia pracę z trybu uśpienia.  
  
        -   **Brak** urządzeń, które nie spełniają tej zasady zgodności, będą zgłaszać ważności niepowodzenia dla raportów programu Configuration Manager.  
  
        -   **Informacje o** urządzeń, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **informacji** dla raportów programu Configuration Manager.  
  
        -   **Ostrzeżenie** urządzeń, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **ostrzeżenie** dla raportów programu Configuration Manager.  
  
        -   **Krytyczne** urządzeń, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczny** dla raportów programu Configuration Manager.  
  
        -   **Krytyczne ze zdarzeniem** urządzeń, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczny** dla raportów programu Configuration Manager. Ten poziom ważności jest też rejestrowany jako zdarzenie systemu Windows w dzienniku zdarzeń aplikacji.  
  
#### <a name="how-to-create-a-configuration-profile-file"></a>Jak utworzyć plik profilu konfiguracji  
 Dostępne są dwa sposoby tworzenia pliku profilu konfiguracji używanego przez zasady niestandardowe:  
  
-   Wyeksportowanie pliku (z rozszerzeniem **mobileconfig**) z narzędzia Apple Configurator.  
  
-   Samodzielne utworzenie pliku przy użyciu odpowiedniego schematu ze [strony z informacjami o kluczach profilów konfiguracji firmy Apple](https://developer.apple.com/library/ios/featuredarticles/iPhoneConfigurationProfileRef/Introduction/Introduction.html).  
  
###  <a name="kiosk-mode-ios"></a>Tryb kiosku (iOS)  
 Tryb kiosku umożliwia blokowanie urządzenia w celu zezwolenia na działanie tylko niektórych funkcji. Na przykład można zezwolić na uruchamianie na urządzeniu tylko określonej zarządzanej aplikacji albo można wyłączyć przyciski regulacji głośności na urządzeniu. Można użyć tych ustawień dla modeli pokazowych urządzenia lub dla urządzeń przeznaczonych do wykonywania tylko jednej funkcji — na przykład urządzeń w punkcie sprzedaży.  
  
#### <a name="to-configure-kiosk-mode-for-ios-devices"></a>Aby skonfigurować tryb kiosku dla urządzeń z systemem iOS  
  
1.  Na stronie **Konfigurowanie ustawień trybu kiosku dla urządzeń z systemem iOS** **Kreatora tworzenia elementu konfiguracji** podaj następujące informacje:  
  
    -   **Wybierz aplikację** — wybierz aplikację, która będzie mogła działać na urządzeniu w trybie kiosku. Na tym urządzeniu nie będzie można uruchamiać żadnych innych aplikacji. Wybierz spośród opcji:  
  
        -   **Zarządzana aplikacja** — kliknij przycisk Przeglądaj, a następnie wybierz zarządzaną aplikację.  
  
        -   **Aplikacja ze sklepu** — podaj adres URL do aplikacji w sklepie z aplikacjami, a następnie kliknij pozycję **Pobierz identyfikator aplikacji**, aby wypełnić pole **Identyfikator aplikacji**.  
  
         Aby znaleźć adres URL aplikacji:  
  
        -   Korzystając z wyszukiwarki, znajdź w sklepie iTunes aplikację, której chcesz użyć, i otwórz jej stronę.  
  
        -   Skopiuj adres URL strony i użyj go jako adresu URL do określenia aplikacji, którą chcesz uruchomić w trybie kiosku.  
  
        -   **Przykład:** Wyszukaj **Microsoft Word for iPad**. Adres URL, którego użyjesz, to **https://itunes.apple.com/us/app/microsoft-word-for-ipad/id586447913?mt=8**.  
  
    -   **Dotknięcie** — włącza lub wyłącza ekran dotykowy na urządzeniu.  
  
    -   **Obracanie ekranu** — włącza lub wyłącza zmianę orientacji ekranu podczas obracania urządzenia.  
  
    -   **Przyciski regulacji głośności** — włącza lub wyłącza przyciski regulacji głośności na urządzeniu.  
  
    -   **Przełączanie dzwonka** — włącza lub wyłącza przełączanie dzwonka (wyciszanie) na urządzeniu.  
  
    -   **Przycisk usypiania/budzenia ekranu** — włącza lub wyłącza przycisk usypiania/budzenia ekranu na urządzeniu.  
  
    -   **Automatyczna blokada** — włącza lub wyłącza automatyczne blokowanie urządzenia.  
  
    -   **Dźwięk mono** — włącza lub wyłącza ustawienie ułatwień dostępu **Dźwięk mono**.  
  
    -   **VoiceOver** — włącza lub wyłącza funkcję ułatwień dostępu **VoiceOver**, która odczytuje na głos tekst wyświetlany na ekranie urządzenia.  
  
    -   **Ustawienia funkcji VoiceOver** — włącza lub wyłącza ustawienia funkcji VoiceOver (na przykład możliwość ustawienia tempa odczytywania tekstu z ekranu).  
  
    -   **Powiększenie** — włącza lub wyłącza funkcję ułatwień dostępu **Zoom** umożliwiającą powiększenie fragmentu ekranu urządzenia za pomocą gestu.  
  
    -   **Ustawienia funkcji powiększenia** — włącza lub wyłącza ustawienia funkcji Zoom.  
  
    -   **Odwróć kolory** — włącza lub wyłącza funkcję ułatwień dostępu **Odwróć kolory** dostosowującą wyświetlany obraz do potrzeb użytkowników niedowidzących.  
  
    -   **Ustawienia funkcji Odwróć kolory** — włącza lub wyłącza ustawienia funkcji Odwróć kolory.  
  
    -   **Obsługa dotykowa z ułatwieniami** — włącza lub wyłącza funkcję ułatwień dostępu **Assistive Touch**, która umożliwia użytkownikom wykonywanie trudnych dla nich gestów na ekranie.  
  
    -   **Ustawienia obsługi dotykowej z ułatwieniami** — włącza lub wyłącza ustawienia funkcji Assistive Touch.  
  
    -   **Wybór mowy** — włącza lub wyłącza funkcję ułatwień dostępu **wyboru mowy**, dzięki której zaznaczony tekst może zostać odczytany na głos przez urządzenie.  
  
    -   **Koryguj niezgodne ustawienia** — wybierz tę opcję, jeśli chcesz skorygować niezgodne ustawienia konfiguracji (jeśli jest to obsługiwane).  
  
    -   **Waga niezgodności do raportów** — określ poziom ważności zgłaszany w przypadku oceny tych zasad zgodności jako niezgodnych. Dostępne są następujące poziomy ważności:  
  
        -   **Brak** urządzeń, które nie spełniają tej zasady zgodności, będą zgłaszać ważności niepowodzenia dla raportów programu Configuration Manager.  
  
        -   **Informacje o** urządzeń, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **informacji** dla raportów programu Configuration Manager.  
  
        -   **Ostrzeżenie** urządzeń, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **ostrzeżenie** dla raportów programu Configuration Manager.  
  
        -   **Krytyczne** urządzeń, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczny** dla raportów programu Configuration Manager.  
  
        -   **Krytyczne ze zdarzeniem** urządzeń, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczny** dla raportów programu Configuration Manager. Ten poziom ważności jest też rejestrowany jako zdarzenie systemu Windows w dzienniku zdarzeń aplikacji.  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy konfiguracji dla urządzeń zarządzanych bez klienta programu System Center Configuration Manager](../../compliance/deploy-use/configuration-items-for-devices-managed-without-the-client.md)

