---
title: Konfigurowanie systemu Android dla aplikacji służbowych przy użyciu zasad konfiguracji aplikacji
titleSuffix: Configuration Manager
description: Wyeliminować problemy z konfiguracją na urządzeniach z systemem Android for Work przez wdrożenie zasad konfiguracji aplikacji dla użytkowników przed ich uruchomieniem aplikacji.
ms.custom: na
ms.date: 09/12/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9126d188-7780-45a4-b21d-7fcf4fad7da2
caps.latest.revision: 0
caps.handback.revision: 0
author: NathBarn
ms.author: NathBarn
manager: angrobe
ms.openlocfilehash: 0b1d4993e6ddb2301121a1e32b1672425e919dea
ms.sourcegitcommit: fb84bcb31d825f454785e3d9d8be669e00fe2b27
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="apply-settings-to-android-for-work-apps-with-app-configuration-policies-in-system-center-configuration-manager"></a>Ustawienia dotyczą systemu Android dla aplikacji służbowych przy użyciu zasad konfiguracji aplikacji w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Zasady konfiguracji aplikacji można użyć w programie System Center Configuration Manager do dystrybucji ustawień, które mogą być wymagane, jeśli użytkownik uruchamia aplikację. Na przykład aplikacja może wymagać użytkownikowi określ następujące informacje szczegółowe:
- Niestandardowy numer portu
- Ustawienia języka
- Ustawienia zabezpieczeń
- Ustawienia oznaczeń marki, takich jak logo firmy

Jeśli użytkownik wprowadzi ustawienia nieprawidłowo, obciążenia naprawione mieści się w pomocy technicznej i wdrażanie aplikacji jest powolne. Aby uniknąć tych problemów, zasady konfiguracji aplikacji służy do wdrożenia wymagane ustawienia dla użytkowników, zanim uruchomią oni aplikację. Ustawienia są automatycznie skojarzone z użytkownikiem. Użytkownik nie musi wykonywać żadnych czynności.
Zamiast wdrażać zasady konfiguracji bezpośrednio do użytkowników i urządzeń, należy skojarzyć zasady z typem wdrożenia podczas wdrażania aplikacji. Ustawienia zasad są stosowane, gdy aplikacja sprawdza, czy je, zwykle przy pierwszym uruchomieniu aplikacji.

Zasady konfiguracji aplikacji systemu android są dostępne tylko na urządzeniach z systemem Android for Work. Zasady konfiguracji aplikacji dotyczą zatwierdzonych aplikacji w sklepie Play pracy magazynu. Aby uzyskać więcej informacji o Android aplikacje nabyte zbiorczo, zobacz [sposobu wdrażania aplikacji w systemie Android pracy urządzeń](https://docs.microsoft.com/intune/deploy-use/android-for-work-apps).

Aby uzyskać więcej informacji na temat typów instalacji aplikacji, zobacz [wprowadzenie do zarządzania aplikacjami](/sccm/apps/understand/introduction-to-application-management).

## <a name="create-an-app-configuration-policy"></a>Tworzenie zasad konfiguracji aplikacji

1. W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **Zarządzanie aplikacjami** > **zasady konfiguracji aplikacji**.
2. Na **Home** karcie **zasady konfiguracji aplikacji** grupy, wybierz **Tworzenie zasad konfiguracji aplikacji**.
3. W aplikacji konfiguracji kreatora tworzenia zasad na **ogólne** Ustaw informacje o zasadach:
  - **Nazwa**. Wprowadź unikatową nazwę zasady.
  - **Opis elementu**. (Opcjonalnie) Aby ułatwić identyfikację zasad, można dodać opis.
  -  **Wybierz typ zasad konfiguracji**. Określ platformy docelowej zasady konfiguracji aplikacji: **Zasady konfiguracji dla systemu Android dla aplikacji służbowych**.
  -  **Przypisane kategorie, aby poprawić wyszukiwanie i filtrowanie**. (Opcjonalnie) Aby utworzyć i przypisać kategorie do zasady, wybierz **kategorii**. Kategorie ułatwić sortowanie i znajdowanie elementów w konsoli programu Configuration Manager.
4. Na **Android zasady pracy** zdecyduj, jak ustawić informacji o konfiguracji zasad:
  - **Określ nazwę i pary wartości**. Opcja ta pliki listy właściwości, które nie korzystają z zagnieżdżenia. Aby określić pary nazw i wartości:
        1. Aby dodać nową parę JSON, wybierz **nowy**.
        2. W **dodać pary nazwa/wartość** okna dialogowego wprowadź następujące informacje:
            - **Typ**. Z listy wybierz typ wartości, który ma zostać określony.
            - **Nazwa**. Wprowadź nazwę klucza listę właściwości, dla którego chcesz określić wartość.
            - **Wartość**. Wprowadź wartość, która zostanie zastosowana do wprowadzony klucz.

  - **Przejdź do pliku JSON listy właściwości**. Użyj tej opcji, jeśli masz już plik JSON konfiguracji aplikacji lub bardziej złożonych plików, które korzysta z opcji zagnieżdżenia. W **zasady konfiguracji aplikacji** wprowadź informacje dotyczące listy właściwości w poprawnym formacie JSON.
5. Aby zaimportować plik JSON, który został utworzony wcześniej, wybierz **Wybieranie pliku**.
6. Wybierz **dalej**. Jeśli wystąpią błędy w kodzie JSON, popraw je przed kontynuowaniem.
7. Zakończ kroki opisane w kreatorze.

Nowe zasady konfiguracji aplikacji jest wyświetlany w obszarze **Biblioteka oprogramowania** obszaru roboczego w **zasady konfiguracji aplikacji** węzła.

## <a name="associate-an-app-configuration-policy-with-a-configuration-manager-application"></a>Dodawanie skojarzenia zasad konfiguracji aplikacji z aplikacją programu Configuration Manager

Aby skojarzyć zasady konfiguracji aplikacji z wdrożeniem systemu android dla aplikacji do pracy, Wdróż aplikację w zwykły sposób za pomocą procedury w [wdrażania aplikacji](/sccm/apps/deploy-use/deploy-applications) tematu.

W Kreatorze wdrażania oprogramowania na **zasady konfiguracji aplikacji** wybierz pozycję **nowy**. W **wybierz zasady konfiguracji aplikacji** okno dialogowe, wybierz typ wdrożenia aplikacji, a zasady konfiguracji aplikacji, które chcesz skojarzyć go z.
Po zainstalowaniu typu wdrożenia jest automatycznie stosowane ustawienia zasad konfiguracji aplikacji.
