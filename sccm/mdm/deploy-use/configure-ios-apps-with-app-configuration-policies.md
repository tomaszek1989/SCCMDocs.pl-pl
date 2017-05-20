---
title: "Konfigurowanie aplikacji za pomocą zasad konfiguracji aplikacji | Dokumentacja firmy Microsoft"
description: "Pomóc w wyeliminowaniu problemów z konfiguracją na urządzeniach z systemem iOS 8 lub nowszy przy wdrażaniu zasad konfiguracji aplikacji dla użytkowników, przed ich uruchomieniem aplikacji."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f0a78038-ea22-4826-9c07-1771b7dd2e8d
caps.latest.revision: 18
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 23b1d24e908d04b64c3bbfa518793a44e696d468
ms.openlocfilehash: 50aea2afaf34974ca92ac58b6569bff56403a9ab
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="apply-settings-to-ios-apps-with-app-configuration-policies-in-system-center-configuration-manager"></a>Zastosowanie ustawień do aplikacji systemu iOS z zasady konfiguracji aplikacji w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


Zasady konfiguracji aplikacji można użyć w System Center Configuration Manager (Menedżer konfiguracji) do rozpowszechniania ustawień, które mogą być wymagane, gdy użytkownik uruchomi aplikację. Na przykład aplikacja może wymagać użytkownika, aby określić te szczegóły:
- Niestandardowy numer portu
- Ustawienia języka
- Ustawienia zabezpieczeń
- Informacje o znakowaniu ustawienia, takie jak logo firmy

Jeśli użytkownik wprowadza ustawienia nieprawidłowo, obciążenia rozwiązywania tych problemów znajduje się w pomocy technicznej i wdrażania aplikacji jest powolne.
Aby uniknąć tych problemów, zasady konfiguracji aplikacji służy do wdrażania ustawienia wymagane dla użytkowników przed ich uruchomieniem aplikacji. Ustawienia są automatycznie skojarzone z użytkownikiem. Użytkownik nie trzeba podejmować żadnych działań.
Aby użyć zasad konfiguracji aplikacji w programie Configuration Manager zamiast wdrażanie zasad konfiguracji bezpośrednio do użytkowników i urządzeń, należy skojarzyć zasady z typu wdrożenia podczas wdrażania aplikacji. Ustawienia zasad są stosowane, gdy aplikacja sprawdza, czy ich (zazwyczaj przy pierwszym uruchomieniu aplikacji).

Zasady konfiguracji aplikacji są obecnie dostępne tylko na urządzeniach z systemem iOS 8 lub nowszy, a dla tych typów aplikacji:

- **pakiet aplikacji dla systemu iOS (*pliku .ipa)**
- **pakiet aplikacji dla systemu iOS ze sklepu z aplikacjami**

Aby uzyskać więcej informacji na temat typów instalacji aplikacji, zobacz [wprowadzenie do zarządzania aplikacjami](/sccm/apps/understand/introduction-to-application-management).

## <a name="create-an-app-configuration-policy"></a>Tworzenie zasad konfiguracji aplikacji

1. W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **zarządzania aplikacjami** > **zasady konfiguracji aplikacji**.
2. Na **Home** w karcie **zasady konfiguracji aplikacji** grupy, wybierz **tworzenie nowych zasad konfiguracji aplikacji**.
3. W przypadku tworzenia aplikacji zasad Kreatora konfiguracji na **ogólne** Ustaw informacje o zasadach:
  - **Nazwa**. Wprowadź unikatową nazwę zasady.
  - **Opis**. (Opcjonalnie) Aby ułatwić identyfikację zasad, można dodać opis.
  - **Przypisane kategorie, aby poprawić wyszukiwanie i filtrowanie**. (Opcjonalnie) Aby utworzyć i przypisać kategorie do zasad, wybierz **kategorii**. Kategorie łatwiejsze do sortowania i wyszukiwania elementów w konsoli programu Configuration Manager.
4. Na **zasad systemu iOS** wybierz, jak ustawić informacje o konfiguracji zasad:
  - **Określ nazwę i pary wartości**. Opcja ta właściwość listy plików, które nie używają zagnieżdżenia.

      *Aby określić pary nazw i wartości*
        1. Aby dodać nową parę, wybierz **nowy**.
        2. W **dodać pary nazwa/wartość** okna dialogowego należy określić następujące czynności:
            - **Typ**. Z listy wybierz typ wartości, którą chcesz określić.
            - **Nazwa**. Wprowadź nazwę klucza listy właściwości, dla którego chcesz określić wartość.
            - **Wartość**. Wprowadź wartość, która zostanie zastosowana do wprowadzony klucz.

  - **Przejdź do pliku listy właściwości**. Użyj tej opcji, jeśli masz już pliku XML konfiguracji aplikacji lub dla bardziej złożonych plików, które używają zagnieżdżenia.

    *Aby przejść do pliku listy właściwości*

      1.  W **zasady konfiguracji aplikacji** wprowadź informacje listy właściwości w poprawnym formacie XML.

      Aby dowiedzieć się więcej na temat list właściwości XML, zobacz [listy właściwości XML opis](https://developer.apple.com/library/ios/documentation/Cocoa/Conceptual/PropertyLists/UnderstandXMLPlist/UnderstandXMLPlist.html) w sklepie iOS Biblioteka dla deweloperów.

Format listy właściwości XML różni się w zależności od aplikacji, który jest konfigurowany. Szczegółowe informacje o formacie do użycia, skontaktuj się z dostawcą aplikacji.
Usługa Intune obsługuje następujące typy danych na liście właściwości:
            
            ```
            <integer>
            <real>
            <string>
            <array>
            <dict>
            <true /> or <false />
            ```
Aby uzyskać więcej informacji na temat typów danych, zobacz [o zawiera listę właściwości](https://developer.apple.com/library/content/documentation/Cocoa/Conceptual/PropertyLists/AboutPropertyLists/AboutPropertyLists.html) w sklepie iOS Biblioteka dla deweloperów.
Intune również obsługuje następujące typy token na liście właściwości:
            
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

{{I}} znaków są używane przez tylko typy tokenów i nie może być używany do innych celów.
            
5. Aby zaimportować plik XML, który został utworzony wcześniej, wybierz **wybierz plik**.
6. Wybierz **dalej**. Jeśli wystąpią błędy w kodzie XML, należy je poprawić przed kontynuowaniem.
7. Zakończ czynności wyświetlane w kreatorze.

Nowe zasady konfiguracji aplikacji jest wyświetlana w **Biblioteka oprogramowania** obszaru roboczego, w **zasady konfiguracji aplikacji** węzła.

## <a name="associate-an-app-configuration-policy-with-a-configuration-manager-application"></a>Dodawanie skojarzenia zasad konfiguracji aplikacji z aplikacją programu Configuration Manager

Aby skojarzyć zasady konfiguracji aplikacji z wdrażaniem aplikacji dla systemu iOS, wdrożyć aplikację w zwykły sposób za pomocą procedury w [wdrażania aplikacji](/sccm/apps/deploy-use/deploy-applications) tematu.

W Kreatorze wdrażania oprogramowania na **zasady konfiguracji aplikacji** wybierz **nowy**. W **wybierz zasady konfiguracji aplikacji** okno dialogowe, wybierz typ wdrożenia aplikacji i zasady konfiguracji aplikacji, które chcesz skojarzyć je z.
Po zainstalowaniu typu wdrożenia jest automatycznie stosowane ustawienia zasad konfiguracji aplikacji.

## <a name="example-format-for-the-mobile-app-configuration-xml-file"></a>Przykładowy format pliku XML konfiguracji aplikacji mobilnej

Podczas tworzenia pliku konfiguracji aplikacji mobilnej można użyć tego formatu do określenia jednego lub więcej z następujących wartości:

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

