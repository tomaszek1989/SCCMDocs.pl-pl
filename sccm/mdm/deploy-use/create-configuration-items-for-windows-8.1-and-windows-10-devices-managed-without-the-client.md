---
title: "Tworzenie elementów konfiguracji dla Windows 8.1 i Windows 10 urządzeń zarządzanych za pomocą usługi Intune"
titleSuffix: Configuration Manager
description: "Aby zarządzać ustawieniami komputerów z systemem Windows 10, należy użyć elementu konfiguracji System Center Configuration Manager systemu Windows 10."
ms.custom: na
ms.date: 07/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 23e1e4dc-623a-4521-ad04-ae9482927097
caps.latest.revision: "20"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 7f5a50ae6ea05af7e864cf94df3063d70bd737b4
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="how-to-create-configuration-items-for-windows-81-and-windows-10-devices-managed-without-the-system-center-configuration-manager-client"></a>Jak utworzyć elementy konfiguracji dla urządzeń z systemem Windows 8.1 lub Windows 10 zarządzanych bez klienta programu System Center Configuration Manager

  
 Użyj programu System Center Configuration Manager**Windows 8.1 i Windows 10** element konfiguracji do zarządzania ustawieniami Windows 8.1 i Windows 10 urządzeń, które są zarejestrowane w programie Microsoft Intune lub zarządzane lokalnie przez program Configuration Manager.  
  
### <a name="to-create-a-windows-81-and-windows-10-configuration-item"></a>Aby utworzyć element konfiguracji systemów Windows 8.1 i Windows 10  
  
1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność**.  
  
2.  W obszarze roboczym **Zasoby i zgodność** rozwiń węzeł **Ustawienia zgodności**, a następnie kliknij pozycję **Elementy konfiguracji**.  
  
3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij pozycję **Utwórz element konfiguracji**.  
  
4.  Na stronie **Ogólne** w **Kreatorze tworzenia elementu konfiguracji** podaj nazwę i opcjonalny opis elementu konfiguracji.  
  
5.  W obszarze **Określ typ elementu konfiguracji, który chcesz utworzyć** wybierz pozycję **Windows 8.1 i Windows 10**.  
  
6.  Kliknij przycisk **kategorii** możesz utworzyć i przypisać kategorie ułatwiające wyszukiwanie i filtrowanie elementów konfiguracji w konsoli programu Configuration Manager.  
  
7.  Na **obsługiwane platformy** strony kreatora wybierz platformy systemu Windows, które oceniać element konfiguracji.  
  
8.  Na stronie **Ustawienia urządzenia** kreatora wybierz grupę ustawień, którą chcesz skonfigurować. Zobacz sekcję [Informacje dotyczące ustawień elementu konfiguracji systemów Windows 8.1 i Windows 10](#BKMK_Setref) w tym temacie, aby uzyskać szczegółowe informacje, a następnie kliknij pozycję **Dalej**.  
  
    > [!TIP]  
    >  Jeśli danego ustawienia nie ma na liście, zaznacz pole wyboru **Konfiguruj dodatkowe ustawienia, nieobjęte domyślnymi grupami ustawień**.  
  
9. Na każdej stronie ustawień skonfiguruj odpowiednie ustawienia i określ, czy chcesz je skorygować w razie braku ich zgodności na urządzeniach (jeśli jest to obsługiwane).  
  
10. Dla każdej grupy ustawień można również skonfigurować ważność, który jest zgłaszany, gdy okaże się niezgodny z elementu konfiguracji:  
  
    -   **Brak** — urządzenia, które nie spełniają tej zasady zgodności nie będą zgłaszać ważności niepowodzenia dla raportów programu Configuration Manager.  
  
    -   **Informacje o** — urządzenia, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **informacji** dla raportów programu Configuration Manager.  
  
    -   **Ostrzeżenie** — urządzenia, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **ostrzeżenie** dla raportów programu Configuration Manager.  
  
    -   **Krytyczne** — urządzenia, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczne** dla raportów programu Configuration Manager.  
  
    -   **Krytyczne ze zdarzeniem** — urządzenia, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczne** dla raportów programu Configuration Manager. Ten poziom ważności jest też rejestrowany jako zdarzenie systemu Windows w dzienniku zdarzeń aplikacji.  
  
11. Na stronie **Możliwość zastosowania platformy** kreatora przejrzyj ustawienia, które nie są zgodne z wybranymi wcześniej obsługiwanymi platformami. Możesz wrócić i usunąć te ustawienia lub kontynuować.  
  
    > [!TIP]  
    >  Nieobsługiwane ustawienia nie są oceniane pod kątem zgodności.  
  
12. Ukończ pracę kreatora.  
  
 Możesz wyświetlić nowy element konfiguracji w węźle **Elementy konfiguracji** obszaru roboczego **Zasoby i zgodność**.  
  
##  <a name="windows-81-and-windows-10-configuration-item-settings-reference"></a>Informacje dotyczące ustawień elementu konfiguracji systemów Windows 8.1 i Windows 10  
  
### <a name="password"></a>Hasło  
 Te ustawienia dotyczą tylko urządzeń z systemem Windows 10 lub nowszym.  
  
|Ustawienie|Szczegóły|  
|-------------|-------------|  
|**Wymagaj ustawień haseł na urządzeniach**|Wymagaj hasła na obsługiwanych urządzeniach.|  
|**Maksymalna długość hasła (w znakach)**|Minimalna długość hasła.|  
|**Wygaśnięcie hasła w dniach**|Liczba dni, po której należy zmienić hasło.|  
|**Liczba zapamiętanych haseł**|Zapobiega ponownemu użyciu hasła stosowanego wcześniej.|  
|**Liczba nieudanych prób logowania przed usunięciem zawartości urządzenia**|Czyści urządzenie po określonej liczbie prób logowania zakończonych niepowodzeniem.|  
|**Czas bezczynności przed zablokowaniem urządzenia**|Określa ilości czasu, przez jaki urządzenie może być bezczynne (bez aktywacji wejść przez użytkownika), zanim zostanie zablokowane.|  
|**Złożoność hasła**|Wybierz, czy można określić numer PIN, taki jak 1234, czy też należy podać silne hasło.|  
|**Jakość hasła**|Wybierz wymagany poziom złożoności hasła oraz określ, czy mogą być stosowane urządzenia biometryczne.|  
|**Wyślij numer PIN odzyskiwania hasła do Exchange Server**|-|
|**Szyfrowanie urządzenia**|Włącz szyfrowanie na urządzeniach docelowych.|  
  
###  <a name="device"></a>Urządzenie  
  
|Nazwa ustawienia|Szczegóły|  
|------------------|-------------|  
|**Przechwytywanie ekranu**|Umożliwia wykonanie zrzutu ekranu urządzenia.<br /><br /> (Tylko system Windows 10)|  
|**Przesłanie danych diagnostycznych**|Umożliwia przesyłanie plików dzienników aplikacji.<br /><br /> (Tylko system Windows 8.1)|  
|**Przesłanie danych diagnostycznych (Windows 10)**|Umożliwia przesyłanie plików dzienników aplikacji.<br /><br /> (Tylko system Windows 10)|  
|**Geolokalizacja**|Umożliwia urządzeniu wykorzystanie danych usług lokalizacji.<br /><br /> (Tylko system Windows 10)|  
|**Kopiowanie i wklejanie**|Umożliwia stosowanie funkcji kopiuj i wklej do przenoszenia danych między aplikacjami.<br /><br /> (Tylko system Windows 10)|
|**Resetowanie do ustawień fabrycznych**|Umożliwia resetowanie urządzenia do ustawień początkowej użytkownika końcowego.<br /><br /> (Tylko system Windows 10)|  
|**Bluetooth**|Zezwalaj na korzystanie z funkcji Bluetooth urządzenia.|  
|**Tryb wykrywania urządzeń Bluetooth**|Zezwalaj na wykrywanie urządzenia przez inne urządzenia Bluetooth.<br /><br /> (Tylko system Windows 10)|  
|**Reklamy przez sieć Bluetooth**|Zezwala na reklamy przez sieć Bluetooth.<br /><br /> (Tylko system Windows 10)|  
|**Nagrywanie głosu**|Zezwalaj na używanie funkcji nagrywania głosu na urządzeniu.<br /><br /> (Tylko system Windows 10)|
|**Cortana**|Zezwalaj na używanie Asystenta głosowego Cortana.<br /><br /> (Tylko system Windows 10)|
|**Powiadomienia Centrum akcji**|Włącza lub wyłącza okienko powiadomień w systemie Windows 10. <br /><br /> (Tylko system Windows 10)|
|**Modyfikacja ustawień regionie (tylko wersja desktop)**|Uniemożliwia zmianę ustawienia regionu na urządzeniu użytkownika końcowego.|
|**Modyfikacja ustawień zasilania i uśpienia (tylko wersja desktop)**|Uniemożliwia zmianę ustawień zasilania i uśpienia na urządzeniu użytkownika końcowego.|
|**Modyfikacja ustawień języka (tylko wersja desktop)**|Uniemożliwia użytkownikowi zmienianie ustawień języka na urządzeniu.|
|**System czas modyfikacji**|Użytkownik końcowy uniemożliwia zmianę urządzenia datę i godzinę.|
|**Zmiana nazwy urządzenia**|Uniemożliwia zmianę nazwy urządzenia użytkownika końcowego.|
  
### <a name="email-management"></a>Zarządzanie pocztą e-mail  
 Te ustawienia dotyczą urządzeń z systemem Windows 8.1 lub Windows 10.  
  
|Ustawienie|Szczegóły|  
|-------------|-------------|  
|**Wiadomości e-mail POP i IMAP**|Umożliwia łączenie z kontami e-mail wykorzystującymi standardy POP i IMAP.|  
|**Maksymalny czas przechowywania wiadomości e-mail**|Czas przechowywania wiadomości e-mail przed usunięciem z serwera.|  
|**Dozwolone formaty wiadomości**|Określa, czy wiadomości e-mail użytkownika mogą zawierać kod HTML, czy tylko zwykły tekst.|  
|**Maksymalny rozmiar wiadomości e-mail w formacie zwykłego tekstu (pobieranych automatycznie)**|Określa maksymalny rozmiar wiadomości e-mail w formacie zwykłego tekstu pobieranych automatycznie.|  
|**Maksymalny rozmiar wiadomości e-mail w formacie HTML (pobieranych automatycznie)**|Określa maksymalny rozmiar wiadomości e-mail w formacie HTML pobieranych automatycznie.|  
|**Maksymalny rozmiar załącznika (automatycznie pobieranego)**|Określa maksymalny rozmiar wiadomości e-mail, który jest automatycznie pobierany.|  
|**Synchronizacja kalendarza**|Zezwala na synchronizację kalendarzy z urządzeniem.|  
|**Niestandardowe konto e-mail**|Umożliwia korzystanie na urządzeniu z konta innego niż Microsoft.|  
|**Ustaw konto Microsoft jako opcjonalne w aplikacji Poczta systemu Windows**|Skonfiguruj tę opcję, aby usunąć wymaganie konta Microsoft w aplikacji Poczta systemu Windows.|  
  
### <a name="store"></a>Magazyn  
 Te ustawienia dotyczą tylko urządzeń z systemem Windows 10 lub nowszym.  
  
|Ustawienie|Szczegóły|  
|-------------|-------------|  
|**Sklep z aplikacjami**|Umożliwia dostęp do sklepu z aplikacjami na urządzeniu.|  
|**Wprowadź hasło w celu dostępu do sklepu z aplikacjami**|Użytkownicy muszą wprowadzić hasło, aby uzyskać dostęp do sklepu z aplikacjami.|  
|**Zakupy w aplikacjach**|Umożliwia użytkownikom dokonywanie zakupów w aplikacjach.|
|**Automatyczna aktualizacja aplikacji ze sklepu**|Umożliwia aplikacje zainstalowane ze Sklepu Windows, które mają być aktualizowane automatycznie.|
|**Użyj tylko prywatnego magazynu**|Włącz to, aby Zezwalaj tylko użytkownikom pobieranie aplikacji ze sklepu prywatnych.|
|**Uruchamianie aplikacji zdalnych magazynu**|Umożliwia, wyłącz wszystkie aplikacje, które zostały wstępnie zainstalowane na urządzeniu lub pobrane ze Sklepu Windows.|
  
### <a name="browser"></a>Przeglądarka  
 Te ustawienia dotyczą urządzeń z systemem Windows 8.1 lub Windows 10.  
  
|Ustawienie|Szczegóły|  
|-------------|-------------|  
|**Zezwalaj na używanie przeglądarki sieci web**|Zezwala na używanie przeglądarki sieci Web na urządzeniu.|  
|**Autowypełnianie**|Użytkownik może zmienić ustawienia autowypełniania w przeglądarce.|  
|**Wykonywanie skryptów aktywnych**|Przeglądarka może uruchamiać skrypty, takie jak skrypty kontrolek ActiveX.|  
|**Dodatki plug-in**|Użytkownik może dodać dodatki plug-in do programu Internet Explorer.|  
|**Blokowanie wyskakujących okienek**|Włącza lub wyłącza blokowanie wyskakujących okienek w przeglądarce.|  
|**Plik cookie**|Zezwalaj na zapisywanie plików cookie na urządzeniu.|  
|**Ostrzeżenie o oszustwie**|Włącz lub wyłącz ostrzeżenia o potencjalnych fałszywych witrynach sieci Web.|  
  
###  <a name="internet-explorer"></a>Internet Explorer  
 Te ustawienia dotyczą urządzeń z systemem Windows 8.1 lub Windows 10.  
  
|Nazwa ustawienia|Szczegóły|  
|------------------|-------------|  
|**Zawsze wysyłaj nagłówek Nie śledź**|Zapobiega wysyłaniu informacji o przeglądaniu do witryn stron trzecich.|  
|**Strefa zabezpieczeń Intranet**|Przypisuje poziom zabezpieczeń do strefy zabezpieczeń Intranet.|  
|**Poziom zabezpieczeń strefy Internet**|Konfiguruje poziom zabezpieczeń strefy Internet.|  
|**Poziom zabezpieczeń strefy Intranet**|Konfiguruje poziom zabezpieczeń strefy Intranet.|  
|**Poziom zabezpieczeń strefy Zaufane witryny**|Konfiguruje poziom zabezpieczeń strefy zaufanych witryn.|  
|**Poziom zabezpieczeń strefy Witryny z ograniczeniami**|Konfiguruje poziom zabezpieczeń strefy witryn z ograniczeniami.|  
|**Obszary nazw strefy Intranet**|Konfigurowanie witryn sieci Web, które zostały dodane lub usunięte ze strefy intranetowej.|  
|**Przejdź do witryny intranetowej po wpisaniu jednowyrazowego słowa**|Włącza lub wyłącza ustawienie, które umożliwia programowi Internet Explorer automatyczne przejście do witryny intranetowej w przypadku wprowadzenia poprawnej nazwy witryny bez przedrostka HTTP:|  
|**Opcja menu Tryb przedsiębiorstwa**|Umożliwia użytkownikom włączanie i wyłączanie trybu przedsiębiorstwa w menu **Narzędzia** programu Internet Explorer.|  
|**Lokalizacja raportu rejestrowania (URL)**|Określ adres URL, w którym są rejestrowane odwiedzane witryny sieci Web, gdy będzie aktywny tryb przedsiębiorstwa.|  
|**Lokalizacja listy witryn trybu przedsiębiorstwa (URL)**|Określ lokalizację listy witryn sieci Web, które używać trybu przedsiębiorstwa, gdy będzie aktywny.|  
  
###  <a name="cloud"></a>Chmura  
 Te ustawienia dotyczą urządzeń z systemem Windows 8.1 lub Windows 10.  
  
|Nazwa ustawienia|Szczegóły|Windows 8.1|Windows 10|  
|------------------|-------------|-----------------|----------------|  
|**Synchronizacja ustawień**|Umożliwia synchronizację ustawień między urządzeniami.|Tak|Tak|  
|**Synchronizacja poświadczeń**|Umożliwia synchronizację poświadczeń między urządzeniami.|Tak|Tak|  
|**Konto Microsoft**|Umożliwia korzystanie na urządzeniu z konta Microsoft.|Tak|Tak|  
|**Synchronizacja ustawień przez połączenia taryfowe**|Zezwalaj na synchronizację ustawień przy taryfowych połączeniach internetowych.|Tak|Tak|  
  
###  <a name="security"></a>Zabezpieczenia  
  
|Nazwa ustawienia|Szczegóły|  
|------------------|-------------|  
|**Instalacja niepodpisanego pliku**|Umożliwia ładowanie niepodpisanych plików.<br /><br /> (Tylko system Windows 10)|  
|**Niepodpisane aplikacje**|Umożliwia ładowanie niepodpisanych aplikacji.<br /><br /> (Tylko system Windows 10)|  
|**Wiadomości SMS i MMS**|Zezwalaj na wysyłanie wiadomości SMS i MMS z urządzenia.<br /><br /> (Tylko system Windows 10)|  
|**Magazyn wymienny**|Zezwalaj na korzystanie na urządzeniu z magazynu wymiennego, takiego jak karta SD.<br /><br /> (Tylko system Windows 10)|  
|**Aparat fotograficzny**|Zezwalaj na korzystanie z aparatu fotograficznego urządzenia.<br /><br /> (Tylko system Windows 10)|  
|**Komunikacja zbliżeniowa (NFC)**|Zezwalaj na komunikację z wykorzystaniem technologii NFC na urządzeniu.<br /><br /> (Tylko system Windows 10)|  
|**Tryb Antykradzieżowy**|Pozwala określić, czy jest włączony tryb antykradzieżowy systemu Windows 10.<br /><br /> (Tylko system Windows 10)|  
|**Zezwalaj na połączenie USB**|Pozwala połączyć się z tym urządzeniem przy użyciu połączenia USB urządzenia.<br /><br /> (Tylko system Windows 10)|
|**Plik profilu**|Dostarcza profil VPN dla urządzeń z systemem Windows RT.<br /><br /> Tylko system Windows 8.1)|  
|**Nazwa profilu**|Dostarcza profil VPN dla urządzeń z systemem Windows RT.<br /><br /> Tylko system Windows 8.1)|  
|**Profil dla wszystkich użytkowników**|Dostarcza profil VPN dla urządzeń z systemem Windows RT.<br /><br /> Tylko system Windows 8.1)|  
  
###  <a name="peak-synchronization"></a>Synchronizacja w szczycie  
 Te ustawienia dotyczą tylko urządzeń z systemem Windows 10 lub nowszym.  
  
|Nazwa ustawienia|Szczegóły|  
|------------------|-------------|  
|**Określ godziny szczytu**|Konfiguruje godziny szczytu na potrzeby synchronizacji urządzeń przenośnych.|  
|**Częstotliwość synchronizacji w szczycie**|Konfiguruje częstotliwość synchronizacji w skonfigurowanych godzinach szczytu.|  
|**Częstotliwość synchronizacji poza szczytem**|Konfiguruje częstotliwość synchronizacji poza skonfigurowanymi godzinami szczytu.|  
  
###  <a name="roaming"></a>Roaming  
  
|Nazwa ustawienia|Szczegóły|  
|------------------|-------------|  
|**Zarządzanie urządzeniem podczas roamingu**|Umożliwia urządzenia, które mają być zarządzane przez program Configuration Manager, podczas roamingu.<br /><br /> (Tylko system Windows 10)|  
|**Pobieranie oprogramowania podczas roamingu**|Umożliwia pobieranie aplikacji i oprogramowania podczas roamingu.<br /><br /> (Tylko system Windows 10)|  
|**Pobieranie wiadomości e-mail podczas roamingu**|Umożliwia pobieranie wiadomości e-mail podczas roamingu.<br /><br /> (Tylko system Windows 10)|  
|**Roaming danych**|Umożliwia roaming między sieciami przy dostępie do danych.| 
|**Sieci VPN przez sieć komórkową**|Umożliwia połączenia sieci VPN dostępu urządzenia podczas połączenia z siecią komórkową.<br /><br /> (Tylko system Windows 10)|
|**Sieć VPN roamingu przez sieć komórkową**|Umożliwia urządzeniu połączenia VPN podczas roamingu w sieci komórkowej.<br /><br /> (Tylko system Windows 10)| 
  
###  <a name="encryption"></a>Szyfrowanie  
  
|Nazwa ustawienia|Szczegóły|  
|------------------|-------------|  
|**Szyfrowanie karty pamięci**|Wymagaj szyfrowania wszystkich kart pamięci używanych z urządzeniem.<br /><br /> (Tylko system Windows 10)|  
|**Szyfrowanie plików na urządzeniu**|Wymaga szyfrowania plików na urządzeniu.|  
|**Wymaga podpisywania wiadomości e-mail**|Wymaga podpisania wiadomości e-mail przed ich wysłaniem.|  
|**Algorytm podpisywania**|Wybierz algorytm podpisywania dla podpisanych wiadomości e-mail.|  
|**Wymaga szyfrowania wiadomości e-mail**|Wymaga szyfrowania wiadomości e-mail przed ich wysłaniem.|  
|**Algorytm szyfrowania**|Wybierz algorytm szyfrowania wiadomości e-mail.|  
  
###  <a name="wireless-communications"></a>Komunikacja bezprzewodowa  
 Te ustawienia dotyczą tylko urządzeń z systemem Windows 10 lub nowszym.  
  
|Nazwa ustawienia|Szczegóły|  
|------------------|-------------|  
|**Połączenie sieci bezprzewodowej**|Włącz lub wyłącz możliwości Wi-Fi urządzenia.|  
|**Tethering Wi-Fi**|Umożliwia użytkownikom korzystanie z urządzeń jako hotspotów mobilnych.|  
|**Obsługa danych przez sieć Wi-Fi, kiedy to możliwe**|Skonfiguruj, aby na urządzeniu używać połączenia przez sieć Wi-Fi, gdy tylko jest to możliwe.|  
|**Zgłaszanie hotspotów Wi-Fi**|-|  
|**Ręczne konfigurowanie sieci Wi-Fi**|-|  
  
#### <a name="to-configure-a-wireless-network-connection"></a>Aby skonfigurować połączenie sieci bezprzewodowej  
  
1.  Na stronie **Konfiguruj ustawienia komunikacji bezprzewodowej urządzenia przenośnego** kliknij przycisk **Dodaj**.  
  
2.  W **połączenie sieci bezprzewodowej** okna dialogowego wprowadź następujące informacje dotyczące połączenia bezprzewodowego, które są udostępnione na urządzeniach przenośnych:  
  
|Ustawienie|Więcej informacji|  
|-------------|----------------------|  
|**Nazwa sieci (SSID)**|Wprowadź nazwę sieci Wi-Fi.|  
|**Połączenie sieciowe**|Wybierz opcję **Internet** lub **Praca**.|  
|**Uwierzytelnianie**|Wybierz metodę uwierzytelniania dla połączenia bezprzewodowego:<br /><br /> - **Otwórz**<br /><br /> - **Udostępnione**<br /><br /> - **WPA**<br /><br /> - **WPA-PSK**<br /><br /> - **WPA2**<br /><br /> - **WPA2-PSK**|  
|**Szyfrowanie danych**|Wybierz metodę szyfrowania używaną przez to połączenie. Można wybrać wartości są różne w zależności od **uwierzytelniania** wybranej metody:<br /><br /> - **Wyłączone**<br /><br /> - **WEP**<br /><br /> - **TKIP**<br /><br /> - **AES**|  
|**Indeks kluczy**|Wybierz indeks kluczy z **1** do **4** używana przez **szyfrowanie danych** ustawienie **WEP**.|  
|**Ta sieć łączy się z Internetem**|Wybierz tę opcję, jeśli chcesz podać ustawienia proxy umożliwiające urządzeniom przenośnym łączenie się z Internetem za pośrednictwem połączenia bezprzewodowego.|  
|**Ustawienia serwera proxy**|Określ zgodnie z wymaganiami ustawienia **Serwer** i **Port** dla opcji **HTTP**, **WAP** i **Sockets**.|  
|**Włącz dostęp do sieci 802.1X**|Wybierz tę opcję, aby zabezpieczyć połączenie przez określenie typu protokołu EAP.|  
|**Typ protokołu EAP**|Wybierz typ protokołu EAP do użycia:<br /><br /> - **PROTOKÓŁ PEAP**<br> - **Karta inteligentna lub certyfikat**|  
  
  
  
### <a name="certificates"></a>Certyfikaty  
 Umożliwia importowanie certyfikatów w celu instalacji na urządzeniach przenośnych.  
  
 Kliknij przycisk **Importuj** i określ następujące wartości:  
  
-   **Plik certyfikatu** — kliknij przycisk Przeglądaj, a następnie wybierz plik certyfikatu z rozszerzeniem **cer**, który chcesz zaimportować.  
  
-   **Magazyn docelowy** — wybierz co najmniej jeden Magazyn docelowy, w którym zaimportowany certyfikat zostanie dodany na urządzeniu przenośnym z:  
  
    -   **Główny**  
  
    -   **URZĄD CERTYFIKACJI**  
  
    -   **Normalny**  
  
    -   **Uprzywilejowany**  
  
    -   **SPC**  
  
    -   **Elementów równorzędnych**  
  
-   **Rola** — Jeśli **SPC** (certyfikat wydawcy oprogramowania) wybrano Magazyn docelowy, wybierz rolę, którą jest skojarzony z certyfikatem:  
  
    -   **Operator komórkowy**  
  
    -   **Menedżer**  
  
    -   **Użytkownik uwierzytelniony**  
  
    -   **IT Administrator**  
  
    -   **Użytkownik nieuwierzytelniony**  
  
    -   **Zaufany serwer dostarczania**  
  
### <a name="system-security"></a>Zabezpieczenia systemu  
  
|Ustawienie|Szczegóły|  
|-------------|-------------|  
|**Kontrola konta użytkownika**|Włącza lub wyłącza Kontrolę konta użytkownika systemu Windows na urządzeniu.|  
|**Zapora sieciowa**|Włącza lub wyłącza zaporę systemu Windows.<br /><br /> (Tylko system Windows 8.1)|  
|**Aktualizacje (Windows 8.1 i starszych)**|Wybierz, jak aktualizacje oprogramowania systemu Windows są pobierane na komputery. Możesz na przykład automatycznie pobierać aktualizacje, ale pozwolić użytkownikowi na wybranie momentu instalacji.|  
|**Minimalna klasyfikacja aktualizacji**|Wybierz minimalną klasyfikację aktualizacji, które są pobierane na komputery z systemem Windows, **Brak**, **ważne**, lub **zalecane**.|  
|**Aktualizacje (Windows 10)**|Wybierz, jak aktualizacje oprogramowania systemu Windows są pobierane na komputery. Możesz na przykład automatycznie pobierać aktualizacje, ale pozwolić użytkownikowi na wybranie momentu instalacji.<br /><br /> (Tylko system Windows 10)|  
|**Data instalacji**|Wybierz datę, kiedy aktualizacje są instalowane.<br /><br /> (Tylko system Windows 10)|  
|**Godzina instalacji**|Wybierz godzinę, kiedy aktualizacje są instalowane.<br /><br /> (Tylko system Windows 10)|  
|**SmartScreen**|Włącz lub wyłącz funkcję Windows SmartScreen.|  
|**Ochrona przed wirusami**|Wybierz, aby upewnić się, że oprogramowanie antywirusowe jest zainstalowane na urządzeniu.|  
|**Sygnatury ochrony przed wirusami są aktualne**|Wybierz, aby upewnić się, że pliki sygnatur oprogramowania antywirusowego są aktualne.|  
|**Funkcje wersji wstępnej**|Umożliwia firmie Microsoft wdrażanie na urządzeniu ustawień i funkcji w wersji wstępnej.<br /><br /> (Tylko system Windows 10)|  
|**Ręczna instalacja certyfikatu głównego**|(Tylko system Windows 10)| 
|**Zezwalaj na ręczne Wyrejestrowanie**|Umożliwia użytkownikowi wyrejestrować się z zarządzania przez rozwiązanie do zarządzania urządzeniami Przenośnymi.| 
  
###  <a name="windows-server-work-folders"></a>Foldery robocze systemu Windows Server  
 Te ustawienia dotyczą urządzeń z systemem Windows 8.1 lub Windows 10.  
  
|Nazwa ustawienia|Szczegóły|  
|------------------|-------------|  
|**Adres URL folderów roboczych**|Określa lokalizację folderu roboczego systemu Windows Server, z którym użytkownicy mogą łączyć się ze swojego urządzenia.|  
  
### <a name="allowed-and-blocked-apps-windows-phone-only"></a>Aplikacje dozwolone i zablokowane (tylko system Windows Phone)  
 Umożliwia utworzenie listy zgodnych lub niezgodnych w firmie aplikacji zarządzanych przez usługę Intune. System Windows Phone można zezwalać na instalację tych aplikacji lub blokować ich instalowanie.  
  
 W tym samym elemencie konfiguracji nie można określić zgodnych i niezgodnych aplikacji.  
  
#### <a name="to-specify-apps-that-are-allowed-or-blocked"></a>Aby określić aplikacje, które są dozwolone lub blokowane  
  
Na stronie **Lista dozwolonych i blokowanych aplikacji** podaj następujące informacje:  
  
|Ustawienie|Więcej informacji|  
    |-------------|----------------------|  
    |**Lista zablokowanych aplikacji**|Wybierz tę opcję, aby określić listę aplikacji, których użytkownicy nie mogą instalować.|  
    |**Lista dozwolonych aplikacji**|Wybierz tę opcję, aby określić listę aplikacji, które użytkownicy mogą instalować. Wszystkie inne aplikacje są blokowane.|  
    |**Dodaj**|Dodaje aplikację do wybranej listy. Wprowadź wybraną nazwę, opcjonalnie wydawcę aplikacji, a także adres URL aplikacji w sklepie z aplikacjami.<br /><br /> Aby określić adres URL, w sklepie Windows Store znajdź aplikację, której chcesz użyć.<br /><br /> Otwórz stronę instalacji aplikacji i skopiuj adres URL do schowka. Możesz teraz użyć tego adresu URL na liście dozwolonych lub zablokowanych aplikacji.<br /><br /> **Przykład:** Wyszukaj w sklepie **Skype** aplikacji. Adres URL jest **http://www.windowsphone.com/store/app/skype/c3f8e570-68b3-4d6a-bdbb-c0a3f4360a51**.|  
    |**Edytowanie**|Umożliwia edytowanie nazwy, wydawcy i adresu URL wybranej aplikacji.|  
    |**Usuń**|Usuwa wybraną aplikację z listy.|  
    |**Importujuj**|Importuje listę aplikacji wprowadzoną w pliku w formacie wartości rozdzielanych przecinkami. W pliku użyj formatu: nazwa aplikacji, wydawca, adres URL.|  
  
### <a name="windows-10-team"></a>Zespół ds. systemu Windows 10  
 Te ustawienia dotyczą tylko urządzeń z systemem Windows 10 Team.  
  
|Nazwa ustawienia|Szczegóły|  
|------------------|-------------|  
|**Zezwalaj na automatyczne wznowienie działania, gdy czujniki wykryją kogoś w pomieszczeniu ekranu**|Umożliwia automatyczne wznowienie działania urządzenia, gdy czujnik wykryje czyjąś obecność w pomieszczeniu.|  
|**Wymagaj numeru PIN dla projekcji bezprzewodowej**|Określa, czy do korzystania z funkcji projekcji bezprzewodowej na urządzeniu jest wymagane wprowadzenie numeru PIN.|  
|**Okno obsługi**|Konfiguruje czas, w którym można przeprowadzać aktualizacje na urządzeniu. Możesz skonfigurować czas rozpoczęcia i czas trwania tego okresu (od 1 do 5 godzin).|
|**Usługa Azure Operational Insights**|Usługa Azure Operational Insights, część programu Microsoft Operations Manager suite zbiera, przechowuje i analizowanie danych pliku dziennika z urządzeń z systemem Windows 10 Team.<br>Aby połączyć się z usługą Azure Operational insights, należy określić identyfikator obszaru roboczego i klucz obszaru roboczego.| 
|**Projekcję bezprzewodową Miracast**|Włącz tę opcję, jeśli chcesz umożliwić urządzenia z systemem Windows 10 Team na projektu przy użyciu urządzeń z włączoną technologią Miracast.<br>Po włączeniu tej opcji z **wybierz kanał Miracast** wybierz kanał Miracast używany dla zawartości projektu.|
|**Informacje o spotkaniu wyświetlane na ekranie powitalnym**|Jeśli ta opcja jest włączona, można wybrać informacje wyświetlane na **spotkań** kafelku **powitalnej** ekranu. Można:<br><br>- **Pokaż tylko organizatora i czas**<br>- **Pokaż organizatora, czas i temat (temat jest ukryty w przypadku spotkań prywatnych)**|
|**Adres URL obrazu tła ekranu blokady**|Użyj tego ustawienia, aby wyświetlić niestandardowe tło na **powitalnej** ekranu urządzenia z systemem Windows 10 Team z adresu URL.<br>Obraz musi być w formacie PNG, a adres URL musi rozpoczynać się od **https://**.| 
  
### <a name="windows-information-protection"></a>Rozwiązanie Windows Information Protection  

Wraz ze wzrostem liczby urządzeń należących do pracowników w przedsiębiorstwie zwiększa się również ryzyko przypadkowych wycieków danych za pośrednictwem aplikacji i usług, takich jak poczta e-mail, media społecznościowe i chmura publiczna, będących poza kontrolą przedsiębiorstwa. Dotyczy to na przykład sytuacji, gdy pracownik wysyła najnowsze zdjęcia projektu inżynieryjnego z osobistego konta e-mail, kopiuje i wkleja informacje o produkcie do wpisu w serwisie Twitter lub zapisuje opracowywany raport sprzedaży w magazynie w swojej chmurze publicznej.

Windows informacji ochrony (pracy w toku) ułatwia ochronę przed takimi potencjalnymi wyciekami danych bez zakłócania w inny sposób pracy pracownika. Pracy w toku pomaga również chronić aplikacje przedsiębiorstwa i dane przed przypadkowymi przeciekami danych z urządzeń należących do przedsiębiorstwa oraz urządzeń osobistych, które pracownik zabiera ze sobą do pracy bez konieczności wprowadzania zmian w Twoim środowisku lub innych aplikacji.

 Ustawienia elementu konfiguracji programu Configuration Manager pracy w toku zarządzają listą aplikacji chronionych przez rozwiązanie EDP, lokalizacjami sieciowymi przedsiębiorstwa, poziomem ochrony i ustawieniami szyfrowania.

Aby uzyskać informacje o konfigurowaniu ochrony danych przedsiębiorstwa z programu Configuration Manager, zobacz [Chroń dane przedsiębiorstwa przy użyciu systemu Windows informacji ochrony (pracy w toku)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip).


### <a name="microsoft-edge"></a>Microsoft Edge  
Te ustawienia dotyczą urządzeń z systemem Windows 10 lub nowszym.  
  
|Nazwa ustawienia|Szczegóły|  
|------------------|-------------| 
|Microsoft Edge|Zezwalaj na używanie przeglądarki sieci web Edge na urządzeniu.| 
|**Zezwalaj na podpowiedzi wyszukiwania na pasku adresu**|Umożliwia wyszukiwarce proponowanie witryn podczas wpisywania fraz wyszukiwania.|  
|**Zezwalaj na wysyłanie ruchu intranetowego do programu Internet Explorer**||  
|**Zezwalaj na nagłówki nie Śledź**|Żądanie Nie śledź informuje witryny sieci Web, że nie chcesz, aby śledziły Twoje odwiedziny w witrynie.|  
|**Włącz filtr SmartScreen**|Umożliwia użycie filtru SmartScreen w celu sprawdzenia, czy pliki pobierane przez użytkowników nie zawierają złośliwego kodu.|  
|**Zezwalaj na wyskakujące okienka**|Zezwala lub wyłącza wyskakujące okienka w przeglądarce.|  
|**Zezwalaj na pliki cookie**|Zezwala na pliki cookie lub wyłącza je.|  
|**Zezwalaj na automatyczne uzupełnianie**|Zezwala na używanie funkcji automatycznego wypełniania w przeglądarce Edge.|  
|**Zezwalaj na działanie Menedżera haseł**|Zezwala na używanie funkcji menedżera haseł w przeglądarce Edge.|  
|**Lokalizacja listy witryn trybu przedsiębiorstwa**|Określa lokalizację listy witryn sieci web, które jest otwierane w trybie przedsiębiorstwa. Użytkownicy nie mogą edytować tej listy.|
|**Blokowanie dostępu do informacji o: flagi**|Blokowanie dostępu użytkownika końcowego dotyczących: flagi strony w programie Edge, zawierający ustawienia eksperymentalne i deweloperów.|
|**Filtr SmartScreen monitu o zastąpienie**|Zezwalaj użytkownikowi na pominięcie ostrzeżeń filtru SmartScreen o potencjalnie złośliwych witryn sieci Web.|
|**Filtr SmartScreen monitu o zastąpienie plików**|Zezwalaj użytkownikowi końcowych pomijanie ostrzeżeń filtru SmartScreen dotyczące pobierania plików mogą okazać się złośliwe.|
|**Adres IP hosta lokalnego WebRTC**|Blok adresu IP localhost użytkowników będą wyświetlane podczas wprowadzania połączeń telefonicznych za pomocą protokołu RTC sieci web.|
|**Domyślny aparat wyszukiwania**|Określ domyślny aparat wyszukiwania, która ma być używany. Użytkownicy końcowi tę wartość można zmienić w dowolnym momencie.|
|**Adres URL OpenSearch XML**|Plik OpenSearch XML służy do tworzenia usługi wyszukiwania Microsoft Edge.<br>Aby uzyskać więcej informacji, zobacz [OpenSearch](https://msdn.microsoft.com/library/windows/desktop/dd940337).|
|**Strony główne (tylko wersja desktop)**|Dodaj listę witryn, które ma być używany jako strony głównej w przeglądarce Edge (tylko wersja desktop).|  


### <a name="windows-defender"></a>Usługa Windows Defender
Te ustawienia dotyczą urządzeń z systemem Windows 10 lub nowszym.
 
|Nazwa ustawienia|Szczegóły|  
|------------------|-------------|  
|**Zezwalaj na monitorowanie w czasie rzeczywistym**|Umożliwia skanowanie w czasie rzeczywistym w poszukiwaniu złośliwego oprogramowania, programów szpiegujących i innego niepożądanego oprogramowania.|
|**Zezwalaj na monitorowanie zachowania**|Umożliwia usłudze Defender sprawdzanie określonych wzorców podejrzanej aktywności na urządzeniach.|
|**Włącz System inspekcji sieci**|System inspekcji sieci (NIS) pomaga chronić urządzenia przed sieciowymi programami wykorzystującymi luki za pomocą sygnatur znanych luk w zabezpieczeniach z Microsoft Endpoint Protection Center, co pomaga wykrywać i blokować złośliwy ruch.|
|**Skanuj wszystkie pobrane pliki**|Określa, czy usługa Defender skanuje wszystkie pliki, które są pobierane z Internetu.|
|**Zezwalaj na skanowanie skryptów**|Umożliwia usłudze Defender skanowanie skryptów, które są używane w programie Internet Explorer.|
|**Monitoruj działanie plików i programów**|Umożliwia usłudze Defender Monitorowanie działania plików i programów na urządzeniach.
|**Liczba dni śledzenia wykrytego złośliwego oprogramowania**|Umożliwia usłudze Defender kontynuowanie śledzenia wykrytego złośliwego oprogramowania, liczba dni zostanie określony, co pozwala ręcznie wyboru wcześniej wpływ na urządzenia. Jeśli liczba dni korzystania z jest ustawiona na 0, złośliwe oprogramowanie pozostanie w folderze kwarantanny i nie będzie automatycznie usuwane.|
|**Zezwalaj na dostęp do interfejsu użytkownika klienta**|Określa, czy interfejs użytkownika programu Windows Defender jest ukryty przez użytkowników.<br>Po zmianie tego ustawienia będzie wprowadzona przy następnym uruchomieniu komputera przez użytkownika.|
|**Zaplanuj skanowanie systemu**|Umożliwia zaplanowanie pełnego lub szybkiego skanowania systemu wykonywanego regularnie w wybranym dniu o wybranej godzinie.|
|**Zaplanuj codzienne szybkie skanowanie**|Umożliwia zaplanowanie szybkie skanowanie, która występuje codziennie o wybranej godzinie
|**Ogranicz użycie procesora CPU podczas skanowania**|Pozwala ograniczyć moc procesora CPU, które są dozwolone tylko skany do użycia (od 1 do 100).|
|**Skanuj pliki archiwum**|Umożliwia usłudze Defender na skanowanie plików archiwów, takich jak zip lub cab plików.|
|**Skanuj wiadomości e-mail**|Zezwala usłudze Defender na skanowanie wiadomości e-mail podczas ich odbierania na urządzeniu.|
|**Skanuj dyski wymienne**|Umożliwia usłudze Defender skanowanie dysków wymiennych, na przykład dysków USB.|
|**Skanuj zamapowane dyski**|Umożliwia usłudze Defender skanowanie plików na zamapowanych dyskach sieciowych.<br>Jeśli pliki na dysku tylko do odczytu, usługa Defender to nie można usunąć z nich wykrytego w nich złośliwego oprogramowania.|
|**Skanuj pliki otwierane z udostępnionych folderów sieciowych**|Umożliwia usłudze Defender skanowanie plików na udostępnionych dyskach sieciowych (na przykład te uzyskać dostępu do ścieżki UNC)<br>Jeśli pliki na dysku tylko do odczytu, usługa Defender to nie można usunąć z nich wykrytego w nich złośliwego oprogramowania.|
|**Interwał aktualizacji sygnatur**|Określa interwał, w których usługa Defender sprawdza nowe pliki sygnatur.
|**Zezwalaj na ochronę w chmurze**|Zezwala lub blokuje Microsoft Active Protection Service na odbieranie informacji o działaniu złośliwego oprogramowania z urządzeń, którymi zarządzasz. Te informacje jest używane do poprawy usługi w przyszłości.|
|**Pytaj użytkowników o przesyłane próbki**|Określa, czy pliki, które mogą wymagać dalszej analizy są automatycznie wysyłane do firmy Microsoft do określenia, czy są złośliwe.|
|**Wykrywanie potencjalnie niechcianych aplikacji**|Chroni zarejestrowanych urządzeń komputerowych z systemem Windows przed uruchamianiem oprogramowania, które jest sklasyfikowane przez usługę Windows Defender jako potencjalnie niechciane. Możesz chronić komputery przed uruchamianiem tych aplikacji lub używać trybu inspekcji, aby zgłaszać zdarzenia instalowania potencjalnie niechcianych aplikacji.|
|**Wykluczenia plików i folderów**|Dodaje jednego lub więcej plików i folderów, na przykład C:\Path lub %ProgramFiles%\Path\filename.exe do listy wykluczeń. Te pliki i foldery nie zostaną uwzględnione w czasie rzeczywistym ani zaplanowanego skanowania.|
|**Wykluczenia rozszerzenia plików**|Dodaj jeden lub więcej rozszerzeń plików, takich jak jpg lub txt do listy wykluczeń. Wszystkie pliki z tymi rozszerzeniami nie znajdują się w czasie rzeczywistym ani zaplanowanego skanowania.|
|**Wykluczenia procesu**|Dodaje jeden lub więcej procesów typu .exe, .com lub .scr do listy wykluczeń. Te procesy nie są uwzględniane w czasie rzeczywistym ani zaplanowanego skanowania.|

  
## <a name="see-also"></a>Zobacz też  
 [Elementy konfiguracji dla urządzeń zarządzanych bez klienta programu System Center Configuration Manager](../../compliance/deploy-use/configuration-items-for-devices-managed-without-the-client.md)