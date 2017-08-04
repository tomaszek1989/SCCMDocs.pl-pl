---
title: "Jak utworzyć elementy konfiguracji dla systemu Android dla pracy urządzeń zarządzanych za pomocą usługi Intune"
ms.custom: na
ms.date: 2017-07-31T00:00:00.000Z
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ab6784fd-8c57-4be9-858f-50fe39f2ff5f
caps.latest.revision: 17
caps.handback.revision: 0
author: robstackmsft
translation.priority.ht:
- cs-cz
- de-de
- en-gb
- es-es
- fr-fr
- hu-hu
- it-it
- ja-jp
- ko-kr
- nl-nl
- pl-pl
- pt-br
- pt-pt
- ru-ru
- sv-se
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: MT
ms.sourcegitcommit: 3c75c1647954d6507f9e28495810ef8c55e42cda
ms.openlocfilehash: 87b34f0a3cce87f6e2ba813957a69b743648c1ca
ms.contentlocale: pl-pl
ms.lasthandoff: 07/29/2017

---
# <a name="how-to-create-configuration-items-for-android-for-work-devices-managed-with-intune"></a>Jak utworzyć elementy konfiguracji dla systemu Android dla pracy urządzeń zarządzanych za pomocą usługi Intune

 Użyj programu System Center Configuration Manager **Android for Work** element konfiguracji do zarządzania ustawieniami urządzeń pracy, które są zarejestrowane w programie Microsoft Intune lub zarządzane lokalnie przez program Configuration Manager dla systemu Android.  

### <a name="to-create-an-android-for-work-configuration-item"></a>Aby utworzyć Android pracy elementu konfiguracji  

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność**.  

2.  W obszarze roboczym **Zasoby i zgodność** rozwiń węzeł **Ustawienia zgodności**, a następnie kliknij pozycję **Elementy konfiguracji**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij pozycję **Utwórz element konfiguracji**.  

4.  Na stronie **Ogólne** w **Kreatorze tworzenia elementu konfiguracji**podaj nazwę i opcjonalny opis elementu konfiguracji.  

5.  W obszarze **Określ typ elementu konfiguracji, który chcesz utworzyć**, wybierz pozycję **Android for Work**.  

6.  Wybierz **kategorii** możesz utworzyć i przypisać kategorie ułatwiające wyszukiwanie i filtrowanie elementów konfiguracji w konsoli programu Configuration Manager.  

  Kliknij przycisk **Dalej**.

7.  Na **ustawienia urządzenia** strony kreatora, zaznacz grupę ustawień, które chcesz skonfigurować. Zobacz [Android ustawień elementu konfiguracji pracy](#android-for-work-configuration-item-settings-reference) szczegółowe informacje, a następnie kliknij przycisk **dalej**.  

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

##  <a name="android-for-work-configuration-item-settings-reference"></a>Dla systemu android dla pracy odwołanie do ustawienia elementu konfiguracji  

### <a name="password"></a>Hasło  

|Ustawienie|Szczegóły|  
|-------------|-------------|  
|**Wymagaj ustawień haseł na urządzeniach**|Wymagaj hasła na obsługiwanych urządzeniach.|  
|**Maksymalna długość hasła (w znakach)**|Minimalna długość hasła.|  
|**Wygaśnięcie hasła w dniach**|Liczba dni, po której należy zmienić hasło.|  
|**Liczba zapamiętanych haseł**|Zapobiega ponownemu użyciu ostatnio używanych haseł.|  
|**Liczba nieudanych prób logowania przed usunięciem zawartości urządzenia**|Czyści urządzenie po określonej liczbie prób logowania zakończonych niepowodzeniem.|  
|**Czas bezczynności przed zablokowaniem urządzenia**|Wybierz ilość razem, gdy urządzenie jest nieużywany zablokowane.|
|**Jakość hasła**|Wybierz wymagany poziom złożoności hasła oraz określ, czy mogą być stosowane urządzenia biometryczne.|  
|**Zezwalaj na użycie blokady inteligentnej i innych agentów zaufania**|Umożliwia kontrolowanie funkcji SmartLock na zgodnych urządzeniach z systemem Android. Ta funkcja telefonu, czasami znana jako funkcja agentów zaufania, umożliwia wyłączenie lub obejście hasła ekranu blokady urządzenia, jeśli urządzenie jest w zaufanej lokalizacji, np. gdy zostało podłączone do danego urządzenia Bluetooth lub znajduje się w pobliżu tagu NFC. Możesz użyć tego ustawienia, aby uniemożliwić użytkownikom końcowym konfigurowanie funkcji SmartLock.|
|**Odblokowywanie odciskiem linii papilarnych**|&nbsp;|

###  <a name="work-profile"></a>Profil pracy  
 Te ustawienia dotyczą tylko urządzeń z rozwiązaniami Samsung KNOX.  

|Nazwa ustawienia|Szczegóły|  
|------------------|-------------|  
|**Zezwalaj na udostępnianie między pracą a Profile osobiste danych**|Wybierz spośród opcji:<br>- **Nieskonfigurowane**<br>- **Domyślne ograniczenia udostępniania**<br>- **Aplikacje w profilu pracy można obsłużyć żądania z osobistego profilu**<br>- **Aplikacje osobiste profilu można obsłużyć żądania z profilu pracy**<br><br>(Zobacz też [ustawienia kopiowania i wklejania](#copy-paste-configuration-item-settings) przy użyciu niestandardowych identyfikatora URI)|  
|**Ukrywanie pracy profilu powiadomień, gdy urządzenie jest zablokowane (Android 6.0 +)**||
|**Zestaw domyślnych zasad uprawnienia aplikacji (Android 6.0 +)**|Wybierz spośród opcji:<br>- **Nieskonfigurowane**<br>- **Zawsze monituj**<br>- **Automatycznie Przydziel**<br>- **Automatyczne odrzucanie**|

### <a name="copy-paste-configuration-item-settings"></a>Skopiuj i Wklej ustawień elementu konfiguracji
Żadna z **Zezwalaj na udostępnianie między pracą a Profile osobiste danych** opcje zapobiec kopiowania i wklejania. Użyj ustawienia niestandardowego, który można skonfigurować w celu zapobieżenia kopiowania i wklejania. Można to skonfigurować w niestandardowy identyfikator URI.

- OMA-URI: ./Vendor/MSFT/WorkProfile/DisallowCrossProfileCopyPaste
- Typ wartości: Boolean

Ustawienie DisallowCrossProfileCopyPaste true zapobiega zachowanie kopiowania i wklejania między Android for Work osobistych i profili pracy.

## <a name="see-also"></a>Zobacz też  
 [Elementy konfiguracji dla urządzeń zarządzanych bez klienta programu System Center Configuration Manager](../../compliance/deploy-use/configuration-items-for-devices-managed-without-the-client.md)

