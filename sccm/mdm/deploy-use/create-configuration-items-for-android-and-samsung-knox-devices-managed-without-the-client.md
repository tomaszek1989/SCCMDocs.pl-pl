---
title: Tworzenie elementów konfiguracji dla urządzeń z systemami Android i Samsung KNOX Standard zarządzanych za pomocą usługi Intune
titleSuffix: Configuration Manager
description: Element konfiguracji System Center Configuration Manager dla systemu Android i Samsung KNOX Standard umożliwia zarządzanie ustawieniami urządzeń.
ms.date: 03/27/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 7b66f3c4-e3bb-4f6a-abd5-55be649ff90d
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: fbfcc2189e2ce06e6348936caad6c68de51f5bdb
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-system-center-configuration-manager-client"></a>Jak utworzyć elementy konfiguracji dla urządzeń z systemem Android lub Samsung KNOX zarządzanych bez klienta programu System Center Configuration Manager

Użyj programu System Center Configuration Manager **Android i Samsung KNOX** element konfiguracji do zarządzania ustawieniami urządzenia Android i Samsung KNOX, które są zarejestrowane w programie Microsoft Intune lub zarządzane lokalnie przez program Configuration Manager.  

#### <a name="to-create-an-android-and-samsung-knox-configuration-item"></a>Aby utworzyć element konfiguracji systemów Android i Samsung KNOX  

1. W konsoli programu Configuration Manager wybierz **zasoby i zgodność**.  

2. W **zasoby i zgodność** obszaru roboczego, rozwiń węzeł **ustawień zgodności**, a następnie wybierz pozycję **elementy konfiguracji**.  

3. Na **Home** karcie **Utwórz** grupy, wybierz **tworzenia elementu konfiguracji**.  

4. Na **ogólne** strony kreatora tworzenia elementu konfiguracji, podaj nazwę i opcjonalny opis dla elementu konfiguracji.  

5. W obszarze **Określ typ elementu konfiguracji, który chcesz utworzyć**, wybierz **Android i Samsung KNOX**.  

6. Wybierz **kategorii** możesz utworzyć i przypisać kategorie ułatwiające wyszukiwanie i filtrowanie elementów konfiguracji w konsoli programu Configuration Manager.  

7. Na **obsługiwane platformy** strony kreatora należy wybrać określone platformy systemu Android i Samsung KNOX, które będą oceniać element konfiguracji.  

8. Na **ustawienia urządzenia** strony kreatora, wybierz grupę ustawień, które chcesz skonfigurować. Zobacz [odwołanie ustawienia elementu konfiguracji systemów Android i Samsung KNOX](#BKMK_setref) w tym temacie, aby uzyskać szczegółowe informacje, a następnie wybierz pozycję **dalej**.  

    > [!TIP]  
    >  Jeśli ustawienia, które mają nie jest wyświetlana, sprawdź **skonfigurować dodatkowe ustawienia, które nie są grupami ustawień domyślnych** pole.  

9. Na każdej stronie ustawień Skonfiguruj wymagane ustawienia. Ponadto wybrać, czy chcesz je skorygować w razie nie są zgodne na urządzeniach (jeśli jest to obsługiwane).  

10. Dla każdej grupy ustawień można również skonfigurować ważność, które będą zgłaszane, gdy okaże się niezgodny elementu konfiguracji:  

    - **Brak**. Urządzenia, które nie spełniają tej zasady zgodności nie będą zgłaszać ważności niepowodzenia dla raportów programu Configuration Manager.  

    - **Informacje o**. Urządzenia, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **informacji** dla raportów programu Configuration Manager.  

    - **Ostrzeżenie**. Urządzenia, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **ostrzeżenie** dla raportów programu Configuration Manager.  

    - **Krytyczne**. Urządzenia, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczny** dla raportów programu Configuration Manager.  

    - **Krytyczne ze zdarzeniem**. Urządzenia, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczny** dla raportów programu Configuration Manager. Ten poziom ważności jest rejestrowany także jako zdarzenie systemu Windows w dzienniku zdarzeń aplikacji.  

11. Na **możliwość zastosowania platformy** strony kreatora przejrzyj ustawienia, które nie są zgodne z obsługiwanych platform wybrano wcześniej. Możesz wrócić i usunąć te ustawienia lub kontynuować.  

    > [!TIP]  
    >  Nieobsługiwane ustawienia nie są oceniane pod kątem zgodności.  

12. Zakończ pracę kreatora.  

 Możesz wyświetlić nowy element konfiguracji w węźle **Elementy konfiguracji** obszaru roboczego **Zasoby i zgodność** .  

## <a name="android-and-samsung-knox-configuration-item-settings-reference"></a>Informacje dotyczące ustawień elementu konfiguracji systemów Android i Samsung KNOX  

### <a name="password"></a>Hasło  
Te ustawienia dotyczą zarówno urządzeń z systemem Android, jak i urządzeń z rozwiązaniami Samsung KNOX.  

|Ustawienie|Szczegóły|  
|-------------|-------------|  
|**Wymagaj ustawień haseł na urządzeniach**|Wymaga podania hasła na obsługiwanych urządzeniach.|  
|**Maksymalna długość hasła (w znakach)**|Określa minimalną długość hasła.|  
|**Wygaśnięcie hasła w dniach**|Określa liczbę dni, należy zmienić hasło.|  
|**Liczba zapamiętanych haseł**|Uniemożliwia ponowne używanie wcześniej używanych haseł.|  
|**Liczba nieudanych prób logowania przed usunięciem zawartości urządzenia**|Czyści urządzenie, jeśli jest to liczba prób zalogowania się niepowodzeniem.|  
|**Czas bezczynności przed zablokowaniem urządzenia**|Określa ilość czasu, zanim urządzenie zostanie zablokowane, jeśli nie jest on używany.|
|**Jakość hasła**|Określa wymagany poziom złożoności hasła i czy można używać urządzeń biometrycznych.|  
|**Zezwalaj na użycie blokady inteligentnej i innych agentów zaufania**|Umożliwia sterowanie funkcją blokady inteligentnej na zgodnych urządzeniach z systemem Android. Ta funkcja telefonu umożliwia wyłączenie lub obejście hasła ekranu blokady urządzenia, jeśli urządzenie jest w zaufanej lokalizacji, takich jak, gdy jest podłączone do danego urządzenia Bluetooth lub znajduje się w pobliżu tagu NFC. To ustawienie umożliwia uniemożliwić użytkownikom konfigurowanie funkcji blokady inteligentnej.|
|**Odcisków palców do odblokowywania (KNOX 5.0 +)**|Umożliwia korzystanie z linii papilarnych do odblokowania urządzeń zgodny.|

### <a name="device"></a>Urządzenie   

|Ustawienie|Szczegóły|  
|------------------|-------------|  
|**Wybieranie głosowe**|Włącza lub wyłącza funkcji wybierania głosowego na urządzeniu.|
|**Asystent głosowy**|Umożliwia korzystanie z oprogramowania Asystenta głosowego na urządzeniu.|
|**Przechwytywanie ekranu**|Zezwala użytkownikowi na Przechwytywanie zawartości ekranu w formie obrazu.|
|**Przesłanie danych diagnostycznych**|Zezwala urządzeniu na przesyłanie danych diagnostycznych do firmy Google.|
|**Geolokalizacja**|Umożliwia urządzeniu, użyj informacji o lokalizacji.|
|**Kopiowanie i wklejanie**|Umożliwia funkcji kopiowania i wklejania na urządzeniu.|
|**Resetowanie do ustawień fabrycznych**|Umożliwia użytkownikowi przeprowadzenie resetowania urządzenia ustawień fabrycznych.|  |
|**Udostępnianie Schowka między aplikacjami**|Umożliwia użytkownikowi Schowka do kopiowania i wklejania między aplikacjami.|  |
|**Bluetooth**|Umożliwia korzystanie z funkcji Bluetooth na urządzeniu.|

### <a name="store"></a>Magazyn

|Ustawienie|Szczegóły|  
|------------------|-------------|  
|**Sklep z aplikacjami**|Zezwala użytkownikowi na dostęp do sklepu Google Play na urządzeniu.|

### <a name="browser"></a>Przeglądarka

|Ustawienie|Szczegóły|  
|------------------|-------------|  
|**Zezwalaj na używanie przeglądarki sieci web**|Umożliwia urządzeniu domyślnej przeglądarki sieci web do użycia.|
|**Autowypełnianie**|Umożliwia automatyczne uzupełnianie funkcji przeglądarki sieci web do użycia.|
|**Wykonywanie skryptów aktywnych**|Umożliwia używanie aktywnych skryptów przeglądarki sieci web urządzenia.|
|**Blokowanie wyskakujących okienek**|Zezwala na korzystanie z blokowanie wyskakujących okienek w przeglądarce sieci web.|
|**Plik cookie**|Umożliwia używanie plików cookie przeglądarki sieci web urządzenia.|

### <a name="cloud"></a>Chmura  

|Ustawienie|Szczegóły|  
|-------------|-------------|  
|**Kopii zapasowej Google**|Umożliwia korzystanie z kopii zapasowej Google.|  
|**Automatyczna synchronizacja z kontem Google**|Zezwala na automatyczną synchronizację ustawień konta Google.|  

### <a name="security"></a>Zabezpieczenia  

|Ustawienie|Szczegóły|  
|-------------|-------------|  
|**Wiadomości SMS i MMS**|Umożliwia korzystanie z wiadomości SMS i MMS na urządzeniu.|
|**Magazyn wymienny**|Umożliwia urządzeniu Użyj magazynu wymiennego, takie jak karta SD.|
|**Aparat fotograficzny**|Zezwala na korzystanie z aparatu fotograficznego urządzenia.<br /><br /> Dotyczy urządzeń z systemem Android i z rozwiązaniami Samsung KNOX.|
|**Komunikacja zbliżeniowa (NFC)**|Umożliwia zadań, które używają komunikację zbliżeniową, jeśli urządzenie je obsługuje.|
|**YouTube**|Umożliwia korzystanie z aplikacji YouTube na urządzeniu.<br /><br /> Dotyczy tylko urządzeń z rozwiązaniami Samsung KNOX.|  
|**Wyłącz zasilanie**|Umożliwia wyłączanie urządzenia.<br /><br /> Dotyczy tylko urządzeń z rozwiązaniami Samsung KNOX.|  

### <a name="roaming"></a>Roaming

|Ustawienie|Szczegóły|  
|-------------|-------------|  
|Roaming połączeń głosowych|Umożliwia roaming, gdy urządzenie jest w sieci komórkowej głosu.|
|Roaming danych|Umożliwia roaming danych, gdy urządzenie jest w sieci komórkowej.|


### <a name="encryption"></a>Szyfrowanie  
 Te ustawienia dotyczą zarówno urządzeń z systemem Android, jak i urządzeń z rozwiązaniami Samsung KNOX.  

|Ustawienie|Szczegóły|  
|-------------|-------------|  
|**Szyfrowanie karty pamięci**|Wymaga szyfrowania jest karta pamięci urządzenia.|
|**Szyfrowanie plików na urządzeniu**|Wymaga szyfrowania plików na urządzeniu przenośnym.|  

### <a name="wireless-communications"></a>Komunikacja bezprzewodowa

|Ustawienie|Szczegóły|  
|-------------|-------------|  
|**Połączenie sieci bezprzewodowej**|Umożliwia korzystanie z funkcji Wi-Fi na urządzeniu.|
|**Tethering Wi-Fi**|Umożliwia użycie funkcji tetheringu Wi-Fi na urządzeniu.|


### <a name="compliant-and-noncompliant-apps-android"></a>Zgodne i niezgodne aplikacje (Android)  
Można określić listę aplikacji systemu Android, które są zgodne lub nie są zgodne w Twojej firmie. Można następnie użyć raportów do wyświetlenia urządzeń z zainstalowanymi niezgodnymi aplikacjami oraz skojarzonego użytkownika.  

W tym samym elemencie konfiguracji nie można określić zgodnych i niezgodnych aplikacji.  

#### <a name="to-specify-the-compliant-or-noncompliant-apps-list"></a>Aby określić listę zgodnych lub niezgodnych aplikacji  

Na stronie **Zgodne i niezgodne aplikacje (Android)** określ następujące informacje:  

|Ustawienie|Więcej informacji|  
|-------------|----------------------|  
|**Lista niezgodnych aplikacji**|Określa listę aplikacji, które będą zgłaszane jako niezgodne, jeśli zainstalowane przez użytkowników.|  
|**Lista zgodnych aplikacji**|Określa listę aplikacji, które użytkownicy mogą instalować. Wszystkie inne zainstalowane aplikacje będą zgłaszane jako niezgodne.|  
|**Dodaj**|Dodaje aplikację do wybranej listy. Wprowadź wybraną nazwę, opcjonalnie wydawcę aplikacji, a także adres URL aplikacji w sklepie z aplikacjami.<br /><br /> Aby określić adres URL z [sekcji aplikacji sklepu Google Play](https://play.google.com/store/apps), Wyszukaj aplikację, która ma być używany.<br /><br /> Otwórz stronę instalacji aplikacji i skopiuj adres URL do schowka. Możesz teraz użyć tego adresu URL na liście zgodnych lub niezgodnych aplikacji.<br /><br /> **Przykład:** Wyszukaj w sklepie Google Play aplikację **Microsoft Office Mobile**. Adres URL, którego używasz będzie **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub**.|  
|**Edytowanie**|Umożliwia edytowanie nazwy, wydawcy i adresu URL wybranej aplikacji.|  
|**Usuń**|Usuwa wybraną aplikację z listy.|  
|**Importujuj**|Importuje listę aplikacji, które zostały określone w pliku wartości rozdzielanych przecinkami. Użyj formatu: Nazwa aplikacji, wydawca, adres URL aplikacji w pliku.|  

## <a name="android-for-work-configuration-items"></a>Android pracy elementów konfiguracji
Android for Work ma dwie grupy ustawienie pozycji konfiguracji:

- **Hasło**. Takie same jak ustawienia dla systemu Android "klasycznym".

- **Profil pracy**. Umożliwia następujące Android pracy ustawień:
  - **Zezwalaj na udostępnianie między pracą a Profile osobiste danych**
  - **Ukrywanie pracy profilu powiadomień, gdy urządzenie jest zablokowane** (Android 6.0 +)
  - **Konfigurowanie domyślnych zasad uprawnienia aplikacji** (Android 6.0 +)

Aby utworzyć element konfiguracji w profilu systemu Android pracy, wybierz **Android for Work** na **ogólne** strony i skonfiguruj ustawienia dla każdej grupy ustawień. Dodaj element konfiguracji do linii bazowej i wdrażanie w zwykły sposób. Te ustawienia zostaną zastosowane tylko na urządzeniach zarejestrowanych jako Android for Work, a nie na urządzeniach zarejestrowanych jako Android.

### <a name="kiosk-mode-samsung-knox-only"></a>Tryb kiosku (tylko Samsung KNOX)  
Tryb kiosku umożliwia blokowanie urządzenia w celu zezwolenia tylko niektórych funkcji. Na przykład można zezwolić na uruchamianie tylko określonej zarządzanej aplikacji przez użytkownika na urządzeniu, lub można wyłączyć przyciski regulacji głośności na urządzeniu. Można użyć tych ustawień dla modeli pokazowych urządzenia. Lub może być używany dla urządzeń przeznaczonych do wykonywania tylko jednej funkcji, takich jak urządzeń w punkcie sprzedaży.  

#### <a name="to-configure-kiosk-mode-for-a-samsung-knox-device"></a>Aby skonfigurować tryb kiosku dla urządzenia z rozwiązaniem Samsung KNOX  

1. Na **Konfigurowanie ustawień trybu kiosku dla urządzenia KNOX Samsung** strony kreatora tworzenia elementu konfiguracji, podaj następujące informacje:  

   |Ustawienie|Więcej informacji|  
   |-------------|----------------------|  
   |**Wybierz aplikację**|Wybierz **Przeglądaj** aby wybrać aplikację systemu Android w programie Configuration Manager (z rozszerzeniem **apk**) która będzie mogła działać, gdy urządzenie jest w trybie kiosku. Na tym urządzeniu nie będzie można uruchamiać żadnych innych aplikacji.|  
   |**Przyciski regulacji głośności**|Włącza lub wyłącza przyciski regulacji głośności na urządzeniu.|  
   |**Ekran uśpienia i wznawiania przycisku**|Włącza lub wyłącza przycisk usypiania/budzenia ekranu na urządzeniu.|  

2. Gdy skończysz, wybierz pozycję **dalej**.  

## <a name="reports-for-monitoring"></a>Raporty dotyczące monitorowania
Jeden z następujących raportów umożliwia monitorowanie zgodnych i niezgodnych aplikacji:  

- **Lista niezgodnych aplikacji i urządzeń dla określonego użytkownika**. Przedstawia informacje o użytkownikach i urządzeniach mających zainstalowane aplikacje, które nie są zgodne z zasadami, które określiłeś.  

- **Podsumowanie użytkowników z niezgodnymi aplikacjami**. Przedstawia informacje dotyczące użytkowników, którzy mają zainstalowane aplikacje, które nie są zgodne z zasadami, które określiłeś.  

Aby uzyskać informacje na temat korzystania z raportów, zobacz [Raportowanie w programie System Center Configuration Manager](../../core/servers/manage/reporting.md).  

## <a name="see-also"></a>Zobacz także  
[Elementy konfiguracji dla urządzeń zarządzanych bez klienta programu System Center Configuration Manager](../../compliance/deploy-use/configuration-items-for-devices-managed-without-the-client.md)
