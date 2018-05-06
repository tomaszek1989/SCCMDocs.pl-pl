---
title: Konfigurowanie aplikacji systemu iOS przy użyciu zasad konfiguracji aplikacji
titleSuffix: Configuration Manager
description: Wyeliminować problemy z konfiguracją na urządzeniach z systemem iOS 8 lub nowszym, wdrażając zasady konfiguracji aplikacji dla użytkowników przed ich uruchomieniem aplikacji.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: f0a78038-ea22-4826-9c07-1771b7dd2e8d
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: e5d00b1efd02d3b096a0b64033b450f0da949eeb
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="apply-settings-to-ios-apps-with-app-configuration-policies-in-system-center-configuration-manager"></a>Zastosuj ustawienia aplikacji dla systemu iOS przy użyciu zasad konfiguracji aplikacji w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


Zasady konfiguracji aplikacji można użyć w programie System Center Configuration Manager (program Configuration Manager) do dystrybucji ustawień, które mogą być wymagane, jeśli użytkownik uruchamia aplikację. Na przykład aplikacja może wymagać użytkownikowi określ następujące informacje szczegółowe:
- Niestandardowy numer portu
- Ustawienia języka
- Ustawienia zabezpieczeń
- Ustawienia oznaczeń marki, takich jak logo firmy

Jeśli użytkownik wprowadzi ustawienia nieprawidłowo, obciążenia naprawione mieści się w pomocy technicznej i wdrażanie aplikacji jest powolne.
Aby uniknąć tych problemów, zasady konfiguracji aplikacji służy do wdrożenia wymagane ustawienia dla użytkowników, zanim uruchomią oni aplikację. Ustawienia są automatycznie skojarzone z użytkownikiem. Użytkownik nie musi wykonywać żadnych czynności.
Aby zamiast wdrażania zasad konfiguracji bezpośrednio do użytkowników i urządzeń, należy użyć zasad konfiguracji aplikacji w programie Configuration Manager, należy skojarzyć zasady z typem wdrożenia podczas wdrażania aplikacji. Ustawienia zasad są stosowane, gdy aplikacja sprawdza, czy je (zazwyczaj przy pierwszym uruchomieniu aplikacji).

Zasady konfiguracji aplikacji są obecnie dostępne tylko na urządzeniach z systemem iOS 8 lub nowszy, a w przypadku tych typów aplikacji:

- **pakiet aplikacji dla systemu iOS (.IPA)**
- **pakiet aplikacji dla systemu iOS ze sklepu z aplikacjami**

Aby uzyskać więcej informacji na temat typów instalacji aplikacji, zobacz [wprowadzenie do zarządzania aplikacjami](/sccm/apps/understand/introduction-to-application-management).

## <a name="create-an-app-configuration-policy"></a>Tworzenie zasad konfiguracji aplikacji

1. W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **Zarządzanie aplikacjami** > **zasady konfiguracji aplikacji**.
2. Na **Home** karcie **zasady konfiguracji aplikacji** grupy, wybierz **utworzyć nowe zasady konfiguracji aplikacji**.
3. W aplikacji konfiguracji kreatora tworzenia zasad na **ogólne** Ustaw informacje o zasadach:
  - **Nazwa**. Wprowadź unikatową nazwę zasady.
  - **Opis elementu**. (Opcjonalnie) Aby ułatwić identyfikację zasad, można dodać opis.
  - **Przypisane kategorie, aby poprawić wyszukiwanie i filtrowanie**. (Opcjonalnie) Aby utworzyć i przypisać kategorie do zasady, wybierz **kategorii**. Kategorie ułatwić sortowanie i znajdowanie elementów w konsoli programu Configuration Manager.
4. Na **zasady systemu iOS** zdecyduj, jak ustawić informacji o konfiguracji zasad:
  - **Określ nazwę i pary wartości**. Opcja ta pliki listy właściwości, które nie korzystają z zagnieżdżenia.

      *Aby określić pary nazw i wartości*
        1. Aby dodać nową parę, wybierz **nowy**.
        2. W **dodać pary nazwa/wartość** okna dialogowego polu, podaj następujące informacje:
            - **Typ**. Z listy wybierz typ wartości, który ma zostać określony.
            - **Nazwa**. Wprowadź nazwę klucza listę właściwości, dla którego chcesz określić wartość.
            - **Wartość**. Wprowadź wartość, która zostanie zastosowana do wprowadzony klucz.

  - **Przejdź do pliku listy właściwości**. Użyj tej opcji, jeśli masz już plik XML konfiguracji aplikacji lub bardziej złożonych plików, które korzysta z opcji zagnieżdżenia.

    *Aby przejść do pliku listy właściwości*

      1.  W **zasady konfiguracji aplikacji** wprowadź informacje dotyczące listy właściwości w poprawnym formacie XML.

      Aby dowiedzieć się więcej na temat list właściwości XML, zobacz [informacje na temat list właściwości XML](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) w bibliotece deweloperów systemu iOS.

Format listy właściwości XML różni się zależnie od konfigurowanej aplikacji. Skontaktuj się z dostawcą aplikacji, aby uzyskać szczegółowe informacje na temat formatu do użycia.
Usługa Intune obsługuje następujące typy danych na liście właściwości:
            
            ```
            <integer>
            <real>
            <string>
            <array>
            <dict>
            <true /> or <false />
            ```
Aby uzyskać więcej informacji na temat typów danych, zobacz [temat list właściwości](https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/PropertyLists/AboutPropertyLists/AboutPropertyLists.html) w bibliotece deweloperów systemu iOS.
Usługa Intune obsługuje również następujące typy tokenów na liście właściwości:
            
            ```
            {{userprincipalname}} - (Example: John@contoso.com)
            {{mail}} - (Example: John@contoso.com)
            {{partialupn}} - (Example: John)
            {{accountid}} - (Example: fc0dc142-71d8-4b12-bbea-bae2a8514c81)
            {{deviceid}} - (Example: b9841cd9-9843-405f-be28-b2265c59ef97)
            {{userid}} - (Example: 3ec2c00f-b125-4519-acf0-302ac3761822)
            {{username}} - (Example: John Doe)
            {{serialnumber}} - (Example: F4KN99ZUG5V2) for iOS devices
            {{serialnumberlast4digits}} - (Example: G5V2) for iOS devices
            ```

{{I}} znaków są używane tylko przez typy tokenów i nie mogą być używane do innych celów.
            
5. Aby zaimportować plik XML, który został utworzony wcześniej, wybierz **Wybieranie pliku**.
6. Wybierz **dalej**. Jeśli wystąpią błędy w kodzie XML, należy je poprawić, aby kontynuować.
7. Zakończ kroki opisane w kreatorze.

Nowe zasady konfiguracji aplikacji jest wyświetlany w obszarze **Biblioteka oprogramowania** obszaru roboczego w **zasady konfiguracji aplikacji** węzła.

## <a name="associate-an-app-configuration-policy-with-a-configuration-manager-application"></a>Dodawanie skojarzenia zasad konfiguracji aplikacji z aplikacją programu Configuration Manager

Aby skojarzyć zasady konfiguracji aplikacji do wdrażania aplikacji dla systemu iOS, Wdróż aplikację w zwykły sposób za pomocą procedury w [wdrażania aplikacji](/sccm/apps/deploy-use/deploy-applications) tematu.

W Kreatorze wdrażania oprogramowania na **zasady konfiguracji aplikacji** wybierz pozycję **nowy**. W **wybierz zasady konfiguracji aplikacji** okno dialogowe, wybierz typ wdrożenia aplikacji, a zasady konfiguracji aplikacji, które chcesz skojarzyć go z.
Po zainstalowaniu typu wdrożenia jest automatycznie stosowane ustawienia zasad konfiguracji aplikacji.

## <a name="example-format-for-the-mobile-app-configuration-xml-file"></a>Przykładowy format pliku XML konfiguracji aplikacji mobilnej

Podczas tworzenia pliku konfiguracji aplikacji mobilnej można użyć tego formatu, można określić jedną lub więcej z następujących wartości:

```
<dict>
  <key>userprincipalname</key>
  <string>{{userprincipalname}}</string>
  <key>mail</key>
  <string>{{mail}}</string>
  <key>partialupn</key>
  <string>{{partialupn}}</string>
  <key>accountid</key>
  <string>{{accountid}}</string>
  <key>deviceid</key>
  <string>{{deviceid}}</string>
  <key>userid</key>
  <string>{{userid}}</string>
  <key>username</key>
  <string>{{username}}</string>
  <key>serialnumber</key>
  <string>{{serialnumber}}</string>
  <key>serialnumberlast4digits</key>
  <string>{{serialnumberlast4digits}}</string>
  <key>udidlast4digits</key>
  <string>{{udidlast4digits}}</string>
</dict>
```
