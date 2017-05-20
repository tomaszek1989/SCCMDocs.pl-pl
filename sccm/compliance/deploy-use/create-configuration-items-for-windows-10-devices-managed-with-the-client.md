---
title: "Tworzenie elementów konfiguracji dla zarządzanych przez klienta systemu Windows 10 - programu Configuration Manager | Dokumentacja firmy Microsoft"
description: "Użycie elementu konfiguracji System Center Configuration Manager systemu Windows 10 do zarządzania ustawieniami dla komputerów z systemem Windows 10, zarządzanych przez klienta programu Configuration Manager."
ms.custom: na
ms.date: 03/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 14226fbe-dd07-4432-910b-130790624a4e
caps.latest.revision: 17
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: e0a42a1d4706ab29617f3b6f8960ece27672908b
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-create-configuration-items-for-windows-10-devices-managed-with-the-system-center-configuration-manager-client"></a>Tworzenie elementów konfiguracji dla urządzeń z systemem Windows 10 zarządzane przy użyciu klienta programu System Center Configuration Manager
Użyj programu System Center Configuration Manager **systemu Windows 10** elementu konfiguracji do zarządzania ustawieniami Windows 10 komputerów, które są zarządzane przez klienta programu Configuration Manager.  
  
> [!IMPORTANT]  
>  W tej wersji, jeśli utworzono **hasło** jako część elementu konfiguracji typu **systemu Windows 10** (dla urządzeń zarządzanych za pomocą klienta programu Configuration Manager), następnie, jeśli ustawienie nie istnieje lub nie został skonfigurowany na urządzeniu Windows 10, go niepoprawnie oceni jako zgodny.  
>   
>  Aby obejść ten problem, podczas tworzenia ustawienia dla tych urządzeń upewnij się, że na stronach ustawień Kreatora tworzenia elementu konfiguracji została wybrana opcja **Koryguj niezgodne ustawienia** . Ponadto podczas wdrażania linii bazowej konfiguracji zawierającej element konfiguracji systemu Windows 10 z ustawieniami hasła wybierz opcję **Koryguj niezgodne reguły, jeśli są obsługiwane** w oknie dialogowym wdrażania linii bazowych konfiguracji. Dzięki zastosowaniu tego rozwiązania ustawienie będzie monitorowane i korygowane w przypadku niezgodności. Po skorygowaniu ustawienie będzie prawidłowo raportowane jako **Zgodne** (chyba że pojawi się problem — w takim przypadku zostanie zgłoszona wartość **Błąd**).  
  
### <a name="to-create-a-windows-10-configuration-item"></a>Aby utworzyć element konfiguracji systemu Windows 10  
  
1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.  
  
2.  W obszarze roboczym **Zasoby i zgodność** rozwiń węzeł **Ustawienia zgodności**, a następnie kliknij pozycję **Elementy konfiguracji**.  
  
3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij pozycję **Utwórz element konfiguracji**.  
  
4.  Na stronie **Ogólne** w **Kreatorze tworzenia elementu konfiguracji**podaj nazwę i opcjonalny opis elementu konfiguracji.  
  
5.  W obszarze **Określ typ elementu konfiguracji, który chcesz utworzyć**wybierz pozycję **Windows 10**.  
  
6.  Kliknij przycisk **kategorii** należy utworzyć i przypisać kategorie ułatwiają wyszukiwanie i filtrowanie elementów konfiguracji w konsoli programu Configuration Manager.  
  
7.  Na stronie **Obsługiwane platformy** kreatora wybierz platformy systemu Windows 10, które będą oceniać element konfiguracji.  
  
8.  Na stronie **Ustawienia urządzenia** kreatora wybierz grupę ustawień, którą chcesz skonfigurować. Szczegółowe informacje można znaleźć w sekcji [Windows 10 configuration item settings reference](#BKMK_Ref) w tym temacie. Następnie kliknij pozycję **Dalej**.  
  
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
  
##  <a name="windows-10-configuration-item-settings-reference"></a>Odwołanie do ustawienia elementu konfiguracji systemu Windows 10  
  
### <a name="password"></a>Hasło  
  
|Ustawienie|Szczegóły|  
|-------------|-------------|  
|**Wymagaj ustawień haseł na urządzeniach**|Wymagaj hasła na obsługiwanych urządzeniach.|  
|**Maksymalna długość hasła (w znakach)**|Minimalna długość hasła wyrażona w znakach.|  
|**Wygaśnięcie hasła w dniach**|Liczba dni, po której należy zmienić hasło.|  
|**Liczba zapamiętanych haseł**|Zapobiega ponownemu użyciu hasła stosowanego wcześniej.|  
|**Liczba nieudanych prób logowania przed usunięciem zawartości urządzenia**|Czyści urządzenie po określonej liczbie prób logowania zakończonych niepowodzeniem.|  
|**Czas bezczynności przed zablokowaniem urządzenia**|Określa, ile minut urządzenie musi być nieaktywne, zanim zostanie automatycznie zablokowane.|  
|**Złożoność hasła**|Wybierz, czy można określić numer PIN, taki jak 1234, czy też należy podać silne hasło.|
|**Liczba złożonych zestawów znaków wymaganych w haseł**|W przypadku wybrania **silnych** hasło, użyj tego ustawienia, aby skonfigurować liczbę zestawów znaków złożonych wymagane. Silne hasło, to powinna być równa co najmniej **3** wymagane są co oznacza liter i cyfr. Wybierz **4** Aby wymusić dodatkowo wymaga znaków specjalnych, takich jak hasło **(% $**.<br>(Tylko system Windows 10)  |
  
###  <a name="device"></a>Urządzenie  
  
|Nazwa ustawienia|Szczegóły|  
|------------------|-------------|  
|**Bluetooth**|Umożliwia korzystanie z funkcji Bluetooth na urządzeniu.|  
  
### <a name="cloud"></a>Chmura  
  
|Nazwa ustawienia|Szczegóły|  
|------------------|-------------|  
|**Synchronizacja ustawień**|Umożliwia synchronizację ustawień między urządzeniami.|  
|**Synchronizacja poświadczeń**|Umożliwia synchronizację poświadczeń między urządzeniami.|  
|**Synchronizacja ustawień przez połączenia taryfowe**|Zezwalaj na synchronizację ustawień przy taryfowych połączeniach internetowych.|  
  
### <a name="roaming"></a>Roaming  
  
|Nazwa ustawienia|Szczegóły|  
|------------------|-------------|  
|**Roaming danych**|Umożliwia roaming między sieciami przy dostępie do danych.|  
  
### <a name="encryption"></a>Szyfrowanie  
  
|Nazwa ustawienia|Szczegóły|  
|------------------|-------------|  
|**Szyfrowanie plików na urządzeniu**|Wymaga szyfrowania plików na urządzeniu.|  
  
### <a name="system-security"></a>Zabezpieczenia systemu  
  
|Nazwa ustawienia|Szczegóły|  
|------------------|-------------|  
|**Kontrola konta użytkownika**|Konfiguruje sposób działania Kontroli konta użytkownika systemu Windows na urządzeniu.<br />Na przykład można ją wyłączyć lub ustawić poziom powiadamiania użytkownika.|  
|**Zapora sieciowa**|Włącza lub wyłącza zaporę systemu Windows.|  
|**SmartScreen**|Włącz lub wyłącz funkcję Windows SmartScreen.|  
|**Ochrona przed wirusami**|Wymaga, aby oprogramowanie antywirusowe zostało zainstalowane i skonfigurowane.|  
|**Sygnatury ochrony przed wirusami są aktualne**|Wymaga, aby pliki podpisów dla oprogramowania antywirusowego na urządzeniu należy na bieżąco.|  
  
### <a name="windows-information-protection-wip"></a>Ochrona informacji systemu Windows (PWT)

Wraz ze wzrostem liczby urządzeń należących do pracowników w przedsiębiorstwie zwiększa się również ryzyko przypadkowych wycieków danych za pośrednictwem aplikacji i usług, takich jak poczta e-mail, media społecznościowe i chmura publiczna, będących poza kontrolą przedsiębiorstwa. Dotyczy to na przykład sytuacji, gdy pracownik wysyła najnowsze zdjęcia projektu inżynieryjnego z osobistego konta e-mail, kopiuje i wkleja informacje o produkcie do wpisu w serwisie Twitter lub zapisuje opracowywany raport sprzedaży w magazynie w swojej chmurze publicznej.

Ochrona informacji systemu Windows (wcześniej ochrony danych przedsiębiorstwa) ułatwia ochronę przed tym potencjalne zagrożenia wyciekiem danych bez zakłócania w inny sposób obsługi pracownika. PWT pomaga chronić aplikacje przedsiębiorstwa i dane przed przecieki przypadkowego danych urządzeń należących do organizacji oraz urządzeń osobistych zapewniające pracowników do pracy bez konieczności wprowadzania zmian w środowisku lub innych aplikacji.

 Elementy konfiguracji programu Configuration Manager systemu Windows o ochronie informacji zarządzania listę aplikacji chronionych przez PWT, lokalizacje sieciowe przedsiębiorstwa, poziom ochrony i ustawienia szyfrowania.
  

Aby uzyskać informacje o sposobie konfigurowania ochrony informacji o systemie Windows za pomocą programu Configuration Manager, zobacz [chronić dane organizacji przy użyciu ochrony informacji systemu Windows (PWT)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip).
  
## <a name="see-also"></a>Zobacz też  
 [Elementy konfiguracji dla urządzeń zarządzanych za pomocą klienta programu System Center Configuration Manager](../../compliance/deploy-use/configuration-items-for-devices-managed-with-the-client.md)
