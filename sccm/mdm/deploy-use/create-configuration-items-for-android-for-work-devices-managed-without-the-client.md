---
title: "Tworzenie elementów konfiguracji dla systemu Android dla pracy urządzeń zarządzanych za pomocą usługi Intune"
ms.custom: na
ms.date: 2017-03-28
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: e6170339b8f3354c549579f127a5c3c618833943
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="how-to-create-configuration-items-for-android-for-work-devices-managed-with-intune"></a>Tworzenie elementów konfiguracji dla systemu Android dla pracy urządzeń zarządzanych za pomocą usługi Intune
  
 Użyj programu System Center Configuration Manager **Android pracy** elementu konfiguracji do zarządzania ustawieniami urządzeń w pracy, które są zarejestrowane w usłudze Microsoft Intune lub lokalnych zarządzanych przez program Configuration Manager dla systemu Android.  
  
### <a name="to-create-an-android-for-work-configuration-item"></a>Aby utworzyć Android pracy elementu konfiguracji  
  
1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność**.  
  
2.  W obszarze roboczym **Zasoby i zgodność** rozwiń węzeł **Ustawienia zgodności**, a następnie kliknij pozycję **Elementy konfiguracji**.  
  
3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij pozycję **Utwórz element konfiguracji**.  
  
4.  Na stronie **Ogólne** w **Kreatorze tworzenia elementu konfiguracji**podaj nazwę i opcjonalny opis elementu konfiguracji.  
  
5.  W obszarze **określić typ elementu konfiguracji, który chcesz utworzyć**, wybierz opcję **Android pracy**.  
  
6.  Kliknij przycisk **kategorii** należy utworzyć i przypisać kategorie ułatwiają wyszukiwanie i filtrowanie elementów konfiguracji w konsoli programu Configuration Manager.  
  
7.  Na stronie **Ustawienia urządzenia** kreatora wybierz grupę ustawień, którą chcesz skonfigurować. Zobacz sekcję **Informacje dotyczące ustawień elementu konfiguracji systemów Android i Samsung KNOX** w tym temacie, aby uzyskać szczegółowe informacje, a następnie kliknij pozycję **Dalej**.  
  
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
  
 Możesz wyświetlić nowy element konfiguracji w węźle **Elementy konfiguracji** obszaru roboczego **Zasoby i zgodność** .  
  
##  <a name="android-for-work-configuration-item-settings-reference"></a>Android do pracy odwołanie do ustawienia elementu konfiguracji  
  
### <a name="password"></a>Hasło  
   
|Ustawienie|Szczegóły|  
|-------------|-------------|  
|**Wymagaj ustawień haseł na urządzeniach**|Wymagaj hasła na obsługiwanych urządzeniach.|  
|**Maksymalna długość hasła (w znakach)**|Minimalna długość hasła.|  
|**Wygaśnięcie hasła w dniach**|Liczba dni, po której należy zmienić hasło.|  
|**Liczba zapamiętanych haseł**|Zapobiega ponownemu użyciu hasła stosowanego wcześniej.|  
|**Liczba nieudanych prób logowania przed usunięciem zawartości urządzenia**|Czyści urządzenie po określonej liczbie prób logowania zakończonych niepowodzeniem.|  
|**Czas bezczynności przed zablokowaniem urządzenia**|Wybierz ilość czasu, przez jaki urządzenie może być bezczynne (nieużywane), zanim zostanie zablokowane.|
|**Jakość hasła**|Wybierz wymagany poziom złożoności hasła oraz określ, czy mogą być stosowane urządzenia biometryczne.|  
|**Zezwalaj na blokowanie inteligentnych i innych agentów zaufania**|Umożliwia kontrolowanie funkcji SmartLock na zgodnych urządzeniach z systemem Android. Ta funkcja telefonu, czasami znana jako funkcja agentów zaufania, umożliwia wyłączenie lub obejście hasła ekranu blokady urządzenia, jeśli urządzenie jest w zaufanej lokalizacji, np. gdy zostało podłączone do danego urządzenia Bluetooth lub znajduje się w pobliżu tagu NFC. Możesz użyć tego ustawienia, aby uniemożliwić użytkownikom końcowym konfigurowanie funkcji SmartLock.|
|**Odblokowywanie odciskiem linii papilarnych**||
  
###  <a name="work-profile"></a>Profil pracy  
 Te ustawienia dotyczą tylko urządzeń z rozwiązaniami Samsung KNOX.  
  
|Nazwa ustawienia|Szczegóły|  
|------------------|-------------|  
|**Zezwalaj na udostępnianie między pracą i profile osobiste danych**|Wybierz spośród opcji:<br>- **Nieskonfigurowane**<br>- **Zapobieganie udostępnianiu żadnych granic**<br>- **Aplikacje w profilu pracy może obsługiwać żądania z profilu osobistego**<br>- **Nie ograniczenia dotyczące udostępniania**<br>|  
|**Ukrywanie pracy profilu powiadomień, gdy urządzenie jest zablokowane (Android w wersji 6.0 +)**||
|**Ustawianie domyślnych zasad uprawnienia aplikacji (Android w wersji 6.0 +)**|Wybierz spośród opcji:<br>- **Nieskonfigurowane**<br>- **Zawsze monituj**<br>- **Udzielanie automatycznie**<br>- **Odmów automatycznie**|
  
 
## <a name="see-also"></a>Zobacz też  
 [Elementy konfiguracji dla urządzeń zarządzanych bez klienta programu System Center Configuration Manager](../../compliance/deploy-use/configuration-items-for-devices-managed-without-the-client.md)
