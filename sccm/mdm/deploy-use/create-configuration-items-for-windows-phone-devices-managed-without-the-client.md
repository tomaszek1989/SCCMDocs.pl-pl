---
title: Jak utworzyć elementy konfiguracji dla urządzeń Windows Phone zarządzanych za pomocą usługi Intune
titleSuffix: Configuration Manager
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: df10dc4d-c9ff-4574-bb33-8d30eb14cfe3
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 4590077b303d5676aa72a816d785a0864fe2205f
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-create-configuration-items-for-windows-phone-devices-managed-without-the-system-center-configuration-manager-client"></a>Jak utworzyć elementy konfiguracji dla urządzeń z systemem Windows Phone zarządzanych bez klienta programu System Center Configuration Manager
Użyj programu System Center Configuration Manager**Windows Phone** element konfiguracji do zarządzania ustawieniami urządzeń Windows Phone, które są zarejestrowane w Microsoft Intune lub zarządzane lokalnie przez program Configuration Manager.  
  
### <a name="to-create-a-windows-phone-configuration-item"></a>Aby utworzyć element konfiguracji Windows Phone  
  
1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność**.  
  
2.  W obszarze roboczym **Zasoby i zgodność** rozwiń węzeł **Ustawienia zgodności**, a następnie kliknij pozycję **Elementy konfiguracji**.  
  
3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij pozycję **Utwórz element konfiguracji**.  
  
4.  Na stronie **Ogólne** w **Kreatorze tworzenia elementu konfiguracji**podaj nazwę i opcjonalny opis elementu konfiguracji.  
  
5.  W obszarze **Określ typ elementu konfiguracji, który chcesz utworzyć**, wybierz pozycję **Windows Phone**.  
  
6.  Kliknij przycisk **kategorii** możesz utworzyć i przypisać kategorie ułatwiające wyszukiwanie i filtrowanie elementów konfiguracji w konsoli programu Configuration Manager.  
  
7.  Na **obsługiwane platformy** strony kreatora wybierz platformy Windows Phone, które będą oceniać element konfiguracji.  
  
8.  Na stronie **Ustawienia urządzenia** kreatora wybierz grupę ustawień, którą chcesz skonfigurować. Szczegółowe informacje można znaleźć w sekcji [Informacje dotyczące ustawień elementu konfiguracji systemu Windows Phone](#BKMK_Setref) w tym temacie. Następnie kliknij pozycję **Dalej**.  
  
    > [!TIP]  
    >  Jeśli danego ustawienia nie ma na liście, zaznacz pole wyboru **Konfiguruj dodatkowe ustawienia, nieobjęte domyślnymi grupami ustawień**.  
  
9. Na każdej stronie ustawień skonfiguruj odpowiednie ustawienia i określ, czy chcesz je skorygować w razie braku ich zgodności na urządzeniach (jeśli jest to obsługiwane).  
  
10. Dla każdej grupy ustawień można również skonfigurować ważność, która będzie zgłaszana w przypadku braku zgodności znalezionego elementu konfiguracji:  
  
    -   **Brak** — urządzenia, które nie spełniają tej zasady zgodności nie będą zgłaszać ważności niepowodzenia dla raportów programu Configuration Manager.  
  
    -   **Informacje o** — urządzenia, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **informacji** dla raportów programu Configuration Manager.  
  
    -   **Ostrzeżenie** — urządzenia, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **ostrzeżenie** dla raportów programu Configuration Manager.  
  
    -   **Krytyczne** — urządzenia, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczne** dla raportów programu Configuration Manager.  
  
    -   **Krytyczne ze zdarzeniem** — urządzenia, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczne** dla raportów programu Configuration Manager. Ten poziom ważności jest też rejestrowany jako zdarzenie systemu Windows w dzienniku zdarzeń aplikacji.  
  
11. Na stronie **Możliwość zastosowania platformy** kreatora przejrzyj ustawienia, które nie są zgodne z wybranymi wcześniej obsługiwanymi platformami. Możesz wrócić i usunąć te ustawienia lub kontynuować.  
  
    > [!TIP]  
    >  Nieobsługiwane ustawienia nie są oceniane pod kątem zgodności.  
  
12. Ukończ pracę kreatora.  
  
 Możesz wyświetlić nowy element konfiguracji w węźle **Elementy konfiguracji** obszaru roboczego **Zasoby i zgodność** .  
  
##  <a name="windows-phone-configuration-item-settings-reference"></a>Informacje dotyczące ustawień elementu konfiguracji systemu Windows Phone  
  
### <a name="password"></a>Hasło  
 Te ustawienia dotyczą zarówno systemu Windows Phone 8 i Windows Phone 8.1.  
  
|Ustawienie|Szczegóły|  
|-------------|-------------|  
|**Wymagaj ustawień haseł na urządzeniach**|Wymagaj hasła na obsługiwanych urządzeniach.|  
|**Maksymalna długość hasła (w znakach)**|Minimalna długość hasła.|  
|**Wygaśnięcie hasła w dniach**|Liczba dni, po której należy zmienić hasło.|  
|**Liczba zapamiętanych haseł**|Zapobiega ponownemu użyciu hasła stosowanego wcześniej.|  
|**Liczba nieudanych prób logowania przed usunięciem zawartości urządzenia**|Czyści urządzenie po określonej liczbie prób logowania zakończonych niepowodzeniem.|  
|**Złożoność hasła**|Wybierz, czy można określić numer PIN, taki jak 1234, czy też należy podać silne hasło.|  
|**Wyślij numer PIN odzyskiwania hasła do Exchange Server**||  
  
### <a name="device"></a>Urządzenie  
  
|Ustawienie|Szczegóły|  
|-------------|-------------|  
|**Przechwytywanie ekranu**|Zezwalaj użytkownikowi na wykonanie zrzutu ekranu urządzenia.<br /><br /> (Tylko Windows Phone 8.1)|  
|**Przesłanie danych diagnostycznych**|Umożliwia przesyłanie plików dzienników aplikacji.|  
|**Geolokalizacja**|Umożliwia urządzeniu wykorzystanie danych usług lokalizacji.<br /><br /> (Tylko Windows Phone 8.1)|  
|**Kopiowanie i wklejanie**|Umożliwia stosowanie funkcji kopiuj i wklej do przenoszenia danych między aplikacjami.<br /><br /> (Tylko Windows Phone 8.1)|  
|**Bluetooth**|Zezwala na korzystanie z funkcji Bluetooth urządzenia.|  
  
### <a name="email-management"></a>Zarządzanie pocztą e-mail  
 Te ustawienia dotyczą zarówno systemu Windows Phone 8 i Windows Phone 8.1.  
  
|Ustawienie|Szczegóły|  
|-------------|-------------|  
|**Wiadomości e-mail POP i IMAP**|Umożliwia łączenie z kontami e-mail wykorzystującymi standardy POP i IMAP.|  
|**Maksymalny czas przechowywania wiadomości e-mail**|Czas przechowywania wiadomości e-mail przed usunięciem z serwera.|  
|**Dozwolone formaty wiadomości**|Określa, czy wiadomości e-mail użytkownika mogą zawierać kod HTML, czy tylko zwykły tekst.|  
|**Maksymalny rozmiar wiadomości e-mail w formacie zwykłego tekstu (pobieranych automatycznie)**|Określa maksymalny rozmiar wiadomości e-mail w formacie zwykłego tekstu pobieranych automatycznie.|  
|**Maksymalny rozmiar wiadomości e-mail w formacie HTML (pobieranych automatycznie)**|Określa maksymalny rozmiar wiadomości e-mail w formacie HTML pobieranych automatycznie.|  
|**Maksymalny rozmiar załącznika (automatycznie pobieranego)**|Określa maksymalny rozmiar wiadomości e-mail pobieranych automatycznie.|  
|**Synchronizacja kalendarza**||  
|**Niestandardowe konto e-mail**|Umożliwia korzystanie na urządzeniu z konta innego niż Microsoft.|  
|**Ustaw konto Microsoft jako opcjonalne w aplikacji Poczta systemu Windows**|Nie wymagają użycia konta Microsoft do logowania się do systemu Windows Mail.|  
  
### <a name="store"></a>Magazyn  
 Te ustawienia dotyczą tylko urządzeń systemu Windows Phone 8.1.  
  
|Ustawienie|Szczegóły|  
|-------------|-------------|  
|**Sklep z aplikacjami**|Umożliwia dostęp do sklepu z aplikacjami na urządzeniu.|  
  
### <a name="browser"></a>Przeglądarka  
 Te ustawienia dotyczą zarówno systemu Windows Phone 8 i Windows Phone 8.1.  
  
|Ustawienie|Szczegóły|  
|-------------|-------------|  
|**Zezwalaj na używanie przeglądarki sieci web**|Włącz lub wyłącz domyślnej przeglądarki internetowej.|  
|**Autowypełnianie**|Użytkownik może zmienić ustawienia autowypełniania w przeglądarce.|  
|**Wykonywanie skryptów aktywnych**|Przeglądarka może uruchamiać skrypty, takie jak skrypty kontrolek ActiveX.|  
|**Dodatki plug-in**|Użytkownik może dodać dodatki plug-in do programu Internet Explorer.|  
|**Blokowanie wyskakujących okienek**|Włącza lub wyłącza blokowanie wyskakujących okienek w przeglądarce.|  
|**Ostrzeżenie o oszustwie**|Włącz lub wyłącz ostrzeżenia o potencjalnych fałszywych witrynach sieci Web.|  
  
### <a name="internet-explorer"></a>Internet Explorer  
 Te ustawienia dotyczą zarówno systemu Windows Phone 8 i Windows Phone 8.1.  
  
|Ustawienie|Szczegóły|  
|-------------|-------------|  
|**Zawsze wysyłaj nagłówek Nie śledź**|Zapobiega wysyłaniu informacji o przeglądaniu do witryn stron trzecich.|  
|**Strefa zabezpieczeń Intranet**||  
|**Poziom zabezpieczeń strefy Internet**|Konfiguruje poziom zabezpieczeń strefy Internet.|  
|**Poziom zabezpieczeń strefy Intranet**|Konfiguruje poziom zabezpieczeń strefy Intranet.|  
|**Poziom zabezpieczeń strefy Zaufane witryny**|Konfiguruje poziom zabezpieczeń strefy zaufanych witryn.|  
|**Poziom zabezpieczeń strefy Witryny z ograniczeniami**|Konfiguruje poziom zabezpieczeń strefy witryn z ograniczeniami.|  
|**Obszary nazw strefy Intranet**||  
|**Przejdź do witryny intranetowej po wpisaniu jednowyrazowego słowa**|Włącza lub wyłącza ustawienie, które umożliwia programowi Internet Explorer automatyczne przejście do witryny intranetowej w przypadku wprowadzenia poprawnej nazwy witryny bez przedrostka HTTP:|  
|**Opcja menu Tryb przedsiębiorstwa**|Umożliwia użytkownikom włączanie i wyłączanie trybu przedsiębiorstwa w menu **Narzędzia** programu Internet Explorer.|  
|**Lokalizacja raportu rejestrowania (URL)**|Określ adres URL, pod którym będą rejestrowane odwiedzane witryny sieci Web, gdy będzie aktywny tryb przedsiębiorstwa.|  
|**Lokalizacja listy witryn trybu przedsiębiorstwa (URL)**|Określ lokalizację listy witryn sieci Web, które będą używać trybu przedsiębiorstwa, gdy będzie aktywny.|  
  
### <a name="cloud"></a>Chmura  
  
|Ustawienie|Szczegóły|  
|-------------|-------------|  
|**Synchronizacja ustawień**|Umożliwia synchronizację ustawień między urządzeniami.|  
|**Synchronizacja poświadczeń**|Umożliwia synchronizację poświadczeń między urządzeniami.|  
|**Konto Microsoft**|Umożliwia korzystanie na urządzeniu z konta Microsoft.<br /><br /> (Tylko Windows Phone 8.1)|  
|**Synchronizacja ustawień przez połączenia taryfowe**|Zezwalaj na synchronizację ustawień przy taryfowych połączeniach internetowych.|  
  
### <a name="security"></a>Zabezpieczenia  
  
|Ustawienie|Szczegóły|  
|-------------|-------------|  
|**Instalacja niepodpisanego pliku**|Umożliwia ładowanie niepodpisanych plików.|  
|**Niepodpisane aplikacje**|Umożliwia ładowanie niepodpisanych aplikacji.|  
|**Wiadomości SMS i MMS**|Zezwalaj na wysyłanie wiadomości SMS i MMS z urządzenia.|  
|**Magazyn wymienny**|Zezwalaj na korzystanie na urządzeniu z magazynu wymiennego, takiego jak karta SD.|  
|**Aparat fotograficzny**|Zezwalaj na korzystanie z aparatu fotograficznego urządzenia.|  
|**Komunikacja zbliżeniowa (NFC)**|Zezwalaj na komunikację z wykorzystaniem technologii NFC na urządzeniu.<br /><br /> (Tylko Windows Phone 8.1)|  
|**Zezwalaj na połączenie USB**|Zezwalaj na urządzenia peryferyjne nawiązać połączenia z tym urządzeniem USB.|
  
### <a name="peak-synchronization"></a>Synchronizacja w szczycie  
 Te ustawienia dotyczą zarówno systemu Windows Phone 8 i Windows Phone 8.1.  
  
|Ustawienie|Szczegóły|  
|-------------|-------------|  
|**Określ godziny szczytu**|Określić przedział czasu, który będzie używany przez następujące dwa ustawienia.|  
|**Częstotliwość synchronizacji w szczycie**|Wybierz, jak często urządzenie będzie synchronizować podczas godziny szczytu na określony.|  
|**Częstotliwość synchronizacji poza szczytem**|Wybierz, jak często urządzenie będzie synchronizować poza godziny szczytu na określony.|  
  
### <a name="roaming"></a>Roaming  
 Te ustawienia dotyczą zarówno systemu Windows Phone 8 i Windows Phone 8.1.  
  
|Ustawienie|Szczegóły|  
|-------------|-------------|  
|**Zarządzanie urządzeniem podczas roamingu**|Umożliwia urządzenia, które mają być zarządzane przez program Configuration Manager, podczas roamingu.|  
|**Pobieranie oprogramowania podczas roamingu**|Umożliwia pobieranie aplikacji i oprogramowania podczas roamingu.|  
|**Pobieranie wiadomości e-mail podczas roamingu**|Umożliwia pobieranie wiadomości e-mail podczas roamingu.|  
|**Roaming danych**|Umożliwia roaming między sieciami przy dostępie do danych.|  
  
### <a name="encryption"></a>Szyfrowanie  
 Te ustawienia dotyczą zarówno systemu Windows Phone 8 i Windows Phone 8.1.  
  
|Ustawienie|Szczegóły|  
|-------------|-------------|  
|**Szyfrowanie karty pamięci**|Wymagaj szyfrowania wszystkich kart pamięci używanych z urządzeniem.|  
|**Szyfrowanie plików na urządzeniu**|Wymaga szyfrowania plików na urządzeniu przenośnym.|  
|**Wymaga podpisywania wiadomości e-mail**|Wymagaj podpisania wiadomości e-mail przed ich wysłaniem.|  
|**Algorytm podpisywania**|Wybierz algorytm podpisywania wiadomości e-mail.|  
|**Wymaga szyfrowania wiadomości e-mail**|Wymagaj szyfrowania wiadomości e-mail przed ich wysłaniem.|  
|**Algorytm szyfrowania**|Wybierz algorytm szyfrowania wiadomości e-mail.|  
  
###  <a name="wireless-communications"></a>Komunikacja bezprzewodowa  
 Te ustawienia dotyczą zarówno systemu Windows Phone 8 i Windows Phone 8.1.  
  
|Nazwa ustawienia|Szczegóły|  
|------------------|-------------|  
|**Połączenie sieci bezprzewodowej**|Włącz lub wyłącz możliwości Wi-Fi urządzenia.|  
|**Tethering Wi-Fi**|Umożliwia użytkownikom korzystanie z urządzeń jako hotspotów mobilnych.|  
|**Obsługa danych przez sieć Wi-Fi, kiedy to możliwe**||  
|**Zgłaszanie hotspotów Wi-Fi**||  
  
##### <a name="to-configure-a-wireless-network-connection"></a>Aby skonfigurować połączenie sieci bezprzewodowej  
  
1.  Na stronie **Konfiguruj ustawienia komunikacji bezprzewodowej urządzenia przenośnego** kliknij przycisk **Dodaj**.  
  
2.  W oknie dialogowym **Połączenie sieci bezprzewodowej** określ następujące informacje na temat połączenia bezprzewodowego, które będzie obsługiwane na urządzeniach przenośnych:  
  
|Ustawienie|Więcej informacji|  
|-------------|----------------------|  
|**Nazwa sieci (SSID)**||  
|**Połączenie sieciowe**|Wybierz opcję **Internet** lub **Praca**.|  
|**Uwierzytelnianie**|Wybierz metodę uwierzytelniania dla połączenia bezprzewodowego:<br><br> - **Otwórz**<br> - **udostępnione**<br> - **WPA**<br> - **WPA-PSK**<br> - **WPA2**<br> - **WPA2-PSK**|  
|**Szyfrowanie danych**|Wybierz metodę szyfrowania używaną przez to połączenie. Dostępne wartości różnią się w zależności od wybranej metody **uwierzytelniania**:<br><br> - **wyłączone**<br> - **WEP**<br> - **TKIP**<br> - **AES**|  
|**Indeks kluczy**|Wybierz indeks kluczy z zakresu od **1** do **4** , który będzie używany z ustawieniem **WEP** opcji **Szyfrowanie danych**.|  
|**Ta sieć łączy się z Internetem**|Wybierz tę opcję, jeśli chcesz podać ustawienia proxy umożliwiające urządzeniom przenośnym łączenie się z Internetem za pośrednictwem połączenia bezprzewodowego.|  
|**Ustawienia serwera proxy**|Określ zgodnie z wymaganiami ustawienia **Serwer** i **Port** dla opcji **HTTP**, **WAP** i **Sockets**.|  
|**Włącz dostęp do sieci 802.1X**|Wybierz tę opcję, aby zabezpieczyć połączenie przez określenie typu protokołu EAP.|  
|**Typ protokołu EAP**|Wybierz typ protokołu EAP do użycia:<br><br> - **PROTOKÓŁ PEAP**<br> - **Karta inteligentna lub certyfikat**|  
    
  
###  <a name="certificates"></a>Certyfikaty  
 Umożliwia importowanie certyfikatów w celu instalacji na urządzeniach przenośnych.  
  
 Kliknij przycisk **Importuj** i określ następujące wartości:  
  
-   **Plik certyfikatu** — kliknij przycisk **Przeglądaj** , a następnie wybierz plik certyfikatu z rozszerzeniem **.cer** , który chcesz zaimportować.  
  
-   **Magazyn docelowy** – wybierz co najmniej jeden magazyn docelowy, w którym zaimportowany certyfikat zostanie dodany na urządzeniu przenośnym:  
  
    -   **główny**  
  
    -   **CA**  
  
    -   **Normalny**  
  
    -   **Uprzywilejowany**  
  
    -   **SPC**  
  
    -   **elementów równorzędnych**  
  
-   **Rola** — Jeśli wybrano magazyn docelowy **SPC** (certyfikat wydawcy oprogramowania), wybierz rolę do powiązania z certyfikatem:  
  
    -   **Operator komórkowy**  
  
    -   **Menedżer**  
  
    -   **Użytkownik uwierzytelniony**  
  
    -   **IT Administrator**  
  
    -   **Użytkownik nieuwierzytelniony**  
  
    -   **Zaufany serwer dostarczania**  
  
### <a name="system-security"></a>Zabezpieczenia systemu  
 Te ustawienia dotyczą zarówno systemu Windows Phone 8 i Windows Phone 8.1.  
  
|Ustawienie|Szczegóły|  
|-------------|-------------|  
|**Kontrola konta użytkownika**|Włącza lub wyłącza Kontrolę konta użytkownika systemu Windows na urządzeniu.|  
|**Zapora sieciowa**|Włącza lub wyłącza zaporę systemu Windows.|  
|**Aktualizacje**|Wybierz sposób pobierania aktualizacji oprogramowania systemu Windows na komputery. Możesz na przykład automatycznie pobierać aktualizacje, ale pozwolić użytkownikowi na wybranie momentu instalacji.|  
|**Minimalna klasyfikacja aktualizacji**|Wybierz minimalną klasyfikację aktualizacji, które będą pobierane na komputery z systemem Windows: **Brak**, **Ważne**lub **Zalecane**.|  
|**SmartScreen**|Włącz lub wyłącz funkcję Windows SmartScreen.|  
|**Ochrona przed wirusami**|Upewnij się, że urządzenie jest chronione przez oprogramowanie antywirusowe|  
|**Sygnatury ochrony przed wirusami są aktualne**|Upewnij się, że sygnatury oprogramowania antywirusowego są aktualne.|
|**Zezwalaj na ręczne Wyrejestrowanie**|Umożliwia użytkownikowi usunięcie ich urządzenia z zarządzania urządzeniami przenośnymi.|  
  
### <a name="windows-server-work-folders"></a>Foldery robocze systemu Windows Server  
 Te ustawienia dotyczą zarówno systemu Windows Phone 8 i Windows Phone 8.1.  
  
|Ustawienie|Szczegóły|  
|-------------|-------------|  
|**Adres URL folderów roboczych**|Określa lokalizację folderu roboczego systemu Windows Server, z którym użytkownicy mogą łączyć się ze swojego urządzenia.|  
  
### <a name="allowed-and-blocked-apps-list-windows-phone-81-only"></a>Lista dozwolonych i zablokowanych aplikacji (tylko Windows Phone 8.1)  
 Umożliwia określenie listy zgodnych i niezgodnych aplikacji systemu Windows Phone w firmie. Użytkownicy nie mogą instalować aplikacji określonych jako zablokowane. Jeśli określisz listę dozwolonych aplikacji, użytkownicy będą mogli instalować tylko aplikacje znajdujące się na liście.  
  
 Nie można określić dozwolonych i zablokowanych aplikacji w tym samym elemencie konfiguracji.  
  
> [!IMPORTANT]  
>  Jeśli określisz listę dozwolonych aplikacji, pamiętaj, że aplikacja portal firmy i wszystkie inne aplikacje wdrożone na urządzeniach Windows Phone 8.1 znajdują się w **dozwolone** listy aplikacji.  
  
##### <a name="to-specify-an-allowed-or-blocked-apps-list"></a>Aby określić listę dozwolonych lub zablokowanych aplikacji  
  
1.  Na **lista dozwolonych i blokowanych aplikacji (Windows Phone 8.1)** Podaj następujące informacje:  
  
|||  
|-|-|  
|Ustawienie|Więcej informacji|  
|**Lista zablokowanych aplikacji**|Wybierz tę opcję, aby utworzyć listę aplikacji, których użytkownicy nie mogą instalować.|  
|**Lista dozwolonych aplikacji**|Wybierz tę opcję, aby określić listę aplikacji, które użytkownicy mogą instalować.|  
|**Dodaj**|Dodaje aplikację do wybranej listy. Wprowadź wybraną nazwę, opcjonalnie wydawcę aplikacji, a także adres URL aplikacji w sklepie z aplikacjami.<br /><br /> Aby określić adres URL, na stronie Sklepu Windows Phone wyszukaj aplikację, której chcesz użyć.<br /><br /> **Przykład:** Wyszukaj w sklepie **Skype** aplikacji. Adres URL, którego będzie http://www.windowsphone.com/en-us/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51.<br /><br /> Dla aplikacji portal firmy lub aplikacji biznesowych nie trzeba określić pełny adres URL tylko identyfikator GUID aplikacji.|  
|**Edytowanie**|Umożliwia edytowanie nazwy, wydawcy i adresu URL wybranej aplikacji.|  
|**Usuń**|Usuwa wybraną aplikację z listy.|  
|**Importujuj**|Importuje listę aplikacji wprowadzoną w pliku w formacie wartości rozdzielanych przecinkami. W pliku użyj formatu: nazwa aplikacji, wydawca, adres URL.|  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy konfiguracji dla urządzeń zarządzanych bez klienta programu System Center Configuration Manager](../../compliance/deploy-use/configuration-items-for-devices-managed-without-the-client.md)