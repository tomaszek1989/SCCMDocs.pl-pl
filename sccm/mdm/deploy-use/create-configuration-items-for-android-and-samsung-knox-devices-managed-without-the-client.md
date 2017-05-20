---
title: "Tworzenie elementów konfiguracji dla urządzeń z systemami Android i Samsung KNOX Standard zarządzane za pomocą usługi Intune | Dokumentacja firmy Microsoft"
description: "Użycie elementu konfiguracji programu System Center Configuration Manager Android i Samsung KNOX Standard do zarządzania ustawieniami urządzeń."
ms.custom: na
ms.date: 03/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b66f3c4-e3bb-4f6a-abd5-55be649ff90d
caps.latest.revision: 17
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4b9261db93c9bf72c492e3c9be5b30f81835134a
ms.openlocfilehash: c9961c2e9866199571a1b39a7b185cb6bb96f998
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-system-center-configuration-manager-client"></a>Jak utworzyć elementy konfiguracji dla urządzeń z systemem Android lub Samsung KNOX zarządzanych bez klienta programu System Center Configuration Manager

Użyj programu System Center Configuration Manager **Android i Samsung KNOX** elementu konfiguracji do zarządzania ustawieniami urządzenia Android i Samsung KNOX, które są zarejestrowane w usłudze Microsoft Intune lub lokalnych zarządzanych przez program Configuration Manager.  

#### <a name="to-create-an-android-and-samsung-knox-configuration-item"></a>Aby utworzyć element konfiguracji systemów Android i Samsung KNOX  

1. W konsoli programu Configuration Manager wybierz **zasoby i zgodność**.  

2. W **zasoby i zgodność** obszaru roboczego, rozwiń węzeł **ustawień zgodności**, a następnie wybierz **elementy konfiguracji**.  

3. Na **Home** w karcie **Utwórz** grupy, wybierz **utworzyć element konfiguracji**.  

4. Na **ogólne** strona kreatora tworzenia elementu konfiguracji, podaj nazwę i opcjonalny opis dla elementu konfiguracji.  

5. W obszarze **określić typ elementu konfiguracji, który chcesz utworzyć**, wybierz **Android i Samsung KNOX**.  

6. Wybierz **kategorii** należy utworzyć i przypisać kategorie ułatwiają wyszukiwanie i filtrowanie elementów konfiguracji w konsoli programu Configuration Manager.  

7. Na **obsługiwane platformy** strony kreatora wybierz określonej platformy Android i Samsung KNOX, które będą oceniać elementu konfiguracji.  

8. Na **ustawienia urządzenia** strony kreatora, wybierz grupę ustawień, które chcesz skonfigurować. Zobacz [odwołania ustawienia elementu konfiguracji systemu Android i Samsung KNOX](#BKMK_setref) w tym temacie, aby uzyskać szczegółowe informacje, a następnie wybierz **dalej**.  

    > [!TIP]  
    >  Jeśli ustawienie nie ma na liście, sprawdź, czy **skonfigurować dodatkowe ustawienia, które nie są grupami ustawień domyślnych** pole.  

9. Na każdej stronie ustawienia należy skonfigurować ustawienia, które są potrzebne. Wybierz, czy chcesz je skorygować, jeśli nie są one zgodne na urządzeniach (jeśli jest to obsługiwane).  

10. Dla każdej grupy ustawienia można również skonfigurować ważność, które będą zgłaszane, gdy okaże się niezgodny element konfiguracji:  

    - **Brak**. Urządzenia, które nie spełniają tej zasady zgodności, będą zgłaszać ważności niepowodzenia dla raportów programu Configuration Manager.  

    - **Informacje o**. Urządzenia, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **informacji** dla raportów programu Configuration Manager.  

    - **Ostrzeżenie**. Urządzenia, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **ostrzeżenie** dla raportów programu Configuration Manager.  

    - **Krytyczne**. Urządzenia, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczny** dla raportów programu Configuration Manager.  

    - **Krytyczne ze zdarzeniem**. Urządzenia, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczny** dla raportów programu Configuration Manager. Ten poziom ważności jest rejestrowany także jako zdarzenie systemu Windows w dzienniku zdarzeń aplikacji.  

11. Na **stosowania platformy** strony kreatora należy przejrzeć ustawienia, które nie są zgodne z obsługiwanych platform wybranymi. Możesz wrócić i usunąć te ustawienia lub kontynuować.  

    > [!TIP]  
    >  Nieobsługiwane ustawienia nie są oceniane pod kątem zgodności.  

12. Zakończ pracę kreatora.  

 Możesz wyświetlić nowy element konfiguracji w węźle **Elementy konfiguracji** obszaru roboczego **Zasoby i zgodność** .  

## <a name="android-and-samsung-knox-configuration-item-settings-reference"></a>Informacje dotyczące ustawień elementu konfiguracji systemów Android i Samsung KNOX  

### <a name="password"></a>Hasło  
Te ustawienia dotyczą zarówno urządzeń z systemem Android, jak i urządzeń z rozwiązaniami Samsung KNOX.  

|Ustawienie|Szczegóły|  
|-------------|-------------|  
|**Wymagaj ustawień haseł na urządzeniach**|Wymaga podania hasła na obsługiwanych urządzeń.|  
|**Maksymalna długość hasła (w znakach)**|Określa minimalną długość hasła.|  
|**Wygaśnięcie hasła w dniach**|Określa liczbę dni, musisz zmienić hasło.|  
|**Liczba zapamiętanych haseł**|Zapobiega uprzednio używanych haseł.|  
|**Liczba nieudanych prób logowania przed usunięciem zawartości urządzenia**|Jeśli ta liczba prób logowania awarii przetwarzający czyści urządzenie.|  
|**Czas bezczynności przed zablokowaniem urządzenia**|Określa czas, zanim urządzenie zostanie zablokowane, jeśli nie jest on używany.|
|**Jakość hasła**|Określa wymagany poziom złożoności hasła i czy mogą być używane urządzenia biometryczne.|  
|**Zezwalaj na blokowanie inteligentnych i innych agentów zaufania**|Umożliwia sterowanie funkcja inteligentnych blokady na urządzeniach zgodnych. Ta możliwość telefonu pozwala wyłączyć lub ominąć hasło ekranu blokady urządzenia, jeśli urządzenie znajduje się w zaufanej lokalizacji, takich jak po podłączeniu do określonego urządzenia Bluetooth lub znajduje się on w pobliżu NFC tag. To ustawienie umożliwia konfigurowanie blokady inteligentne uniemożliwi użytkownikom.|
|**Odcisk palca do odblokowywania (KNOX 5.0 +)**|Umożliwia korzystanie z odcisk palca do odblokowania urządzeń zgodnych.|

### <a name="device"></a>Urządzenie   

|Ustawienie|Szczegóły|  
|------------------|-------------|  
|**Wybieranie głosowe**|Włącza lub wyłącza funkcję wybierania głosowego na urządzeniu.|
|**Asystent głosowy**|Umożliwia korzystanie z oprogramowania Asystenta głosowego na urządzeniu.|
|**Przechwytywanie ekranu**|Pozwala użytkownikowi na Przechwytywanie zawartości ekranu jako obrazu.|
|**Przesłanie danych diagnostycznych**|Służy do urządzenie Prześlij informacje diagnostyczne do firmy Google.|
|**Geolokalizacja**|Służy do urządzenie użyć informacji o lokalizacji.|
|**Kopiowanie i wklejanie**|Umożliwia kopiowanie i wklejanie funkcji na urządzeniu.|
|**Resetowanie do ustawień fabrycznych**|Użytkownicy będą mogli przeprowadzić resetowanie urządzenia do ustawień fabrycznych.|  |
|**Udostępnianie Schowka między aplikacjami**|Użytkownicy będą mogli używać Schowka do kopiowania i wklejania między aplikacjami.|  |
|**Bluetooth**|Umożliwia korzystanie z połączenia Bluetooth na urządzeniu.|

### <a name="store"></a>Magazyn

|Ustawienie|Szczegóły|  
|------------------|-------------|  
|**Sklep z aplikacjami**|Pozwala użytkownikowi na dostęp do sklepu Google Play na urządzeniu.|

### <a name="browser"></a>Przeglądarka

|Ustawienie|Szczegóły|  
|------------------|-------------|  
|**Zezwalaj na używanie przeglądarki sieci web**|Umożliwia urządzenia domyślną przeglądarkę sieci web do użycia.|
|**Autowypełnianie**|Umożliwia automatyczne uzupełnianie funkcji przeglądarki sieci web, który ma być używany.|
|**Wykonywanie skryptów aktywnych**|Zezwala na wykonywanie aktywnych skryptów przeglądarki sieci web urządzenia.|
|**Blokowanie wyskakujących okienek**|Umożliwia korzystanie z funkcji blokowania wyskakujących okienek w przeglądarce sieci web.|
|**Plik cookie**|Pozwala używać plików cookie w przeglądarce sieci web urządzenia.|

### <a name="cloud"></a>Chmura  

|Ustawienie|Szczegóły|  
|-------------|-------------|  
|**Kopia zapasowa Google**|Umożliwia korzystanie z kopii zapasowej Google.|  
|**Automatyczną synchronizację konta Google**|Zezwala na automatyczną synchronizację ustawień konta Google.|  

### <a name="security"></a>Zabezpieczenia  

|Ustawienie|Szczegóły|  
|-------------|-------------|  
|**Wiadomości SMS i MMS**|Umożliwia korzystanie z programu SMS i MMS wiadomości na urządzeniu.|
|**Magazyn wymienny**|Służy do urządzenie używany Magazyn wymienny, takich jak karta SD.|
|**Aparat fotograficzny**|Zezwala na korzystanie z aparatu fotograficznego urządzenia.<br /><br /> Dotyczy urządzeń z systemem Android i z rozwiązaniami Samsung KNOX.|
|**Komunikacja zbliżeniowa (NFC)**|Umożliwia zadań wykonywanych za pomocą komunikację zbliżeniową, jeśli urządzenie obsługuje tę funkcję.|
|**YouTube**|Umożliwia korzystanie z aplikacji YouTube na urządzeniu.<br /><br /> Dotyczy tylko urządzeń z rozwiązaniami Samsung KNOX.|  
|**Wyłączenie zasilania**|Umożliwia wyłączanie urządzenia.<br /><br /> Dotyczy tylko urządzeń z rozwiązaniami Samsung KNOX.|  

### <a name="roaming"></a>Roaming

|Ustawienie|Szczegóły|  
|-------------|-------------|  
|Roaming połączeń głosowych|Umożliwia głosu mobilnych, gdy urządzenie jest w sieci komórkowej.|
|Roaming danych|Umożliwia danych mobilnych, gdy urządzenie jest w sieci komórkowej.|


### <a name="encryption"></a>Szyfrowanie  
 Te ustawienia dotyczą zarówno urządzeń z systemem Android, jak i urządzeń z rozwiązaniami Samsung KNOX.  

|Ustawienie|Szczegóły|  
|-------------|-------------|  
|**Szyfrowanie karty pamięci**|Wymaga się, że karty pamięci urządzenia są zaszyfrowane.|
|**Szyfrowanie plików na urządzeniu**|Wymaga szyfrowania plików na urządzeniu przenośnym.|  

### <a name="wireless-communications"></a>Komunikacja bezprzewodowa

|Ustawienie|Szczegóły|  
|-------------|-------------|  
|**Połączenie sieci bezprzewodowej**|Umożliwia korzystanie z możliwości sieci Wi-Fi urządzenia.|
|**Tethering Wi-Fi**|Umożliwia korzystanie z tethering Wi-Fi na urządzeniu.|


### <a name="compliant-and-noncompliant-apps-android"></a>Zgodne i niezgodne aplikacje (Android)  
Można określić listę aplikacji systemu Android, które są zgodne lub niezgodne w firmie. Można następnie użyć raportów, aby pokazywał urządzenia, które mają zainstalowane aplikacje niezgodne i skojarzonego z nim użytkownika.  

W tym samym elemencie konfiguracji nie można określić zgodnych i niezgodnych aplikacji.  

#### <a name="to-specify-the-compliant-or-noncompliant-apps-list"></a>Aby określić listę zgodnych lub niezgodnych aplikacji  

Na stronie **Zgodne i niezgodne aplikacje (Android)** określ następujące informacje:  

|Ustawienie|Więcej informacji|  
|-------------|----------------------|  
|**Lista niezgodnych aplikacji**|Określa listę aplikacji, które będą zgłaszane jako niezgodne, jeśli zainstalowane przez użytkowników.|  
|**Lista zgodnych aplikacji**|Określa listę aplikacji, które użytkownicy mogą instalować. Wszystkie inne zainstalowane aplikacje będą zgłaszane jako niezgodne.|  
|**Dodaj**|Dodaje aplikację do wybranej listy. Wprowadź wybraną nazwę, opcjonalnie wydawcę aplikacji, a także adres URL aplikacji w sklepie z aplikacjami.<br /><br /> Aby określić adres URL, z [części aplikacji Google Play](https://play.google.com/store/apps), Wyszukaj aplikację, która ma być używana.<br /><br /> Otwórz stronę instalacji aplikacji i skopiuj adres URL do schowka. Możesz teraz użyć tego adresu URL na liście zgodnych lub niezgodnych aplikacji.<br /><br /> **Przykład:** Wyszukaj w Google Play **Microsoft Office Mobile**. Adres URL, którego używasz będzie **https://play.google.com/store/apps/details?id=com.microsoft.office.officehub**.|  
|**Edytowanie**|Umożliwia edytowanie nazwy, wydawcy i adresu URL wybranej aplikacji.|  
|**Usuń**|Usuwa wybraną aplikację z listy.|  
|**Importujuj**|Importuje listę aplikacji, które zostały określone w pliku wartości rozdzielanych przecinkami. Użyj formatu: Nazwa aplikacji, wydawca, adres URL aplikacji w pliku.|  

## <a name="android-for-work-configuration-items"></a>Android pracy elementów konfiguracji
Android do pracy składa się z dwóch grup ustawienie pozycji konfiguracji:

- **Hasło**. Taka sama, jak ustawienia dla systemu Android "klasycznym".

- **Profil pracy**. Umożliwia Android następujących ustawień roboczych:
  -    **Zezwalaj na udostępnianie między pracą i profile osobiste danych**
  - **Ukrywanie pracy profilu powiadomień, gdy urządzenie jest zablokowane** (Android w wersji 6.0 +)
  -    **Konfigurowanie domyślnych zasad uprawnienia aplikacji** (Android w wersji 6.0 +)

Aby utworzyć element konfiguracji w profilu Android pracy, wybierz **Android pracy** na **ogólne** strony i skonfiguruj ustawienia dla każdej grupy ustawień. Dodaj element konfiguracji do linii bazowej i wdrożyć w zwykły sposób. Te ustawienia będą stosowane tylko do urządzeń zarejestrowane jako Android do pracy, a nie do urządzenia zarejestrowane jako Android.

### <a name="kiosk-mode-samsung-knox-only"></a>Tryb kiosku (tylko Samsung KNOX)  
Tryb kiosku służy do blokowania urządzenia tak, aby zezwolić tylko niektórych funkcji. Na przykład można zezwolić na urządzeniu do uruchamiania tylko jednej aplikacji zarządzanych, który określisz lub można wyłączyć przyciski regulacji głośności na urządzeniu. Można użyć tych ustawień dla modeli pokazowych urządzenia. Lub może być używany dla urządzeń przeznaczonych do wykonywania tylko jednej funkcji, takich jak urządzenia w punktach sprzedaży.  

#### <a name="to-configure-kiosk-mode-for-a-samsung-knox-device"></a>Aby skonfigurować tryb kiosku dla urządzenia z rozwiązaniem Samsung KNOX  

1. Na **konfigurowania ustawień trybu kiosku dla urządzeń Samsung KNOX** strona kreatora tworzenia elementu konfiguracji, podaj następujące informacje:  

   |Ustawienie|Więcej informacji|  
   |-------------|----------------------|  
   |**Wybierz aplikację**|Wybierz **Przeglądaj** aby wybrać aplikację Android programu Configuration Manager (z rozszerzeniem **.apk**) które mogą być uruchamiany, gdy urządzenie jest w trybie kiosku. Na tym urządzeniu nie będzie można uruchamiać żadnych innych aplikacji.|  
   |**Przyciski głośności**|Włącza lub wyłącza przyciski regulacji głośności na urządzeniu.|  
   |**Ekranu uśpienia i przycisku**|Włącza lub wyłącza przycisk usypiania/budzenia ekranu na urządzeniu.|  

2. Gdy skończysz, wybierz **dalej**.  

## <a name="reports-for-monitoring"></a>Raporty dotyczące monitorowania
Jeden z następujących raportów umożliwia monitorowanie zgodnych i niezgodnych aplikacji:  

- **Lista niezgodnych aplikacji i urządzeń dla określonego użytkownika**. Przedstawia informacje dotyczące użytkowników i urządzeń z zainstalowanymi aplikacjami, które nie są zgodne z zasadami określona.  

- **Podsumowanie użytkowników z niezgodnymi aplikacjami**. Przedstawia informacje dotyczące użytkowników, którzy mają zainstalowane aplikacje, które nie są zgodne z zasadami określona.  

Aby uzyskać informacje na temat korzystania z raportów, zobacz [Raportowanie w programie System Center Configuration Manager](../../core/servers/manage/reporting.md).  

## <a name="see-also"></a>Zobacz także  
[Elementy konfiguracji dla urządzeń zarządzanych bez klienta programu System Center Configuration Manager](../../compliance/deploy-use/configuration-items-for-devices-managed-without-the-client.md)

