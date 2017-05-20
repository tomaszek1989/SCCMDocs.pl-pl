---
title: Tworzenie aktualizacji | Dokumentacja firmy Microsoft
description: "Tworzenie i pakietu aktualizacji oprogramowania za pomocą programu System Center Updates Publisher"
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 46a1a8ac-126c-4ee6-ae09-32dfbdb83368
caps.latest.revision: 1
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31819a1df4e63e1114682490a9b3c3b4e5c99cfa
ms.openlocfilehash: 33b188f4a9c14091429d1f49e07f1f17fbf98516
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="create--software-updates-and-update-bundles-with-updates-publisher"></a>Tworzenie aktualizacji oprogramowania i zaktualizować pakiety z programem Updates Publisher

*Dotyczy: System Center Updates Publisher*

Z programem Updates Publisher służy **tworzenia aktualizacji** kreatora do tworzenia własnych aktualizacji i **Utwórz pakiet** kreatora, aby utworzyć pakiety aktualizacji.

Ponieważ te dwa kreatory mają podobne przepływu pracy, procedurę, aby utworzyć pakiet aktualizacji odwołuje się do procedury tworzenia aktualizacji, tylko istotne różnice szczegółowe.

## <a name="use-the-create-update-wizard"></a>Użyj Kreatora tworzenia aktualizacji
1.  W konsoli, przejdź do **obszar roboczy aktualizacje**, a następnie w **wprowadzenie** okienku wybierz **aktualizacji** z **Home** karty wstążki. Spowoduje to otwarcie **tworzenie aktualizacji** kreatora.

2.  Na **pakietu** strony, użyj poniższych informacji, aby skonfigurować aktualizacji:

    -   Wybierz **Przeglądaj** zlokalizować pakiet aktualizacji oprogramowania będzie używany jako źródło pakietu. Nieprawidłowa źródła obejmują. MSI. MSP, lub. Pliki EXE. Updates Publisher tworzy skrót pliku. Wyznaczania wartości skrótu i nazwa pliku są następnie używane w metadanych aktualizacji dla aktualizacji, które tworzysz.

    -   Określ lokalizację źródła zawartości dla tej aktualizacji. Gdy masz lokalną kopię zawartości, można wybrać pole wyboru **publikują zawartość aktualizacji oprogramowania przy użyciu lokalnego źródła** do używania [ścieżkę publikacji lokalne źródło](/sccm/sum/tools/updates-publisher-options#advanced) (i zaawansowanych opcji). Jeśli ta opcja nie jest zaznaczona, należy określić adres URL, gdzie aktualizacji można znaleźć w sieci web. Ta ścieżka lub adres URL jest dodawany do metadanych aktualizacji.

        Później po opublikowaniu aktualizacji na serwerze WSUS aktualizuje wydawcy pobiera pliki binarne aktualizacji w lokalizacji wskazanej źródłowej.

    -   Określ **binarny języka** aktualizacji oprogramowania.

    -   Określ **Powodzenie kody powrotne**, i **Powodzenie do czasu ponownego rozruchu kodów** aktualizacji. Oddziel wiele kodów powrotnych za pomocą przecinka. Kody powrotne służy do określenia podczas instalacji aktualizacji zakończyło się powodzeniem, i po ponownym uruchomieniu nie są wymagane.

        -   Pliki Instalatora Windows i poprawki (. MSI i. Pliki MSP) automatycznie ustawić te wartości, a nie może być modyfikowany.

        -   Dla. Aktualizuje EXE, kody domyślne zdefiniowane przez. Plik EXE są używane, jeśli są określone nie kody powrotu.

    -   Określ argumenty wiersza polecenia, które są wymagane do zainstalowania aktualizacji oprogramowania.

        -   Pliki Instalatora Windows i poprawki (. MSI i. Pliki MSP) automatycznie ustawić te wartości. Dla tych typów plików argumenty muszą być określone jako  **\[nazwa\]=\[wartość\]**. Dodatkowo, wszystkie opcje rozpoczynających się od  **/**  (takich jak **/qn**) nie jest obsługiwane. MSI lub. Aktualizacje oprogramowania MSP.

        -   Dla. Aktualizacje EXE wszystkie argumenty są prawidłowe.

3.  Na **informacji** Określ szczegółowe informacje o aktualizacji, które są uwzględniane podczas aktualizacji jest opublikowana lub wyeksportować. Zlokalizowane właściwości, takich jak nazwa aktualizacji (tytuł) i opis znajdują się szczegółowe informacje. Następnie określ szczegóły bardziej ogólne, takie jak klasyfikacji, dostawca, produktu i gdzie można dowiedzieć się więcej na temat aktualizacji.

    ** Zlokalizowanych właściwości: **

    -   **Język**: Wybierz język, a następnie określ tytuł i opis. Następnie można wybrać dodatkowe języki, co w czasie, z każdego z języków obsługujących własny tytuł i opis.

    -   **Tytuł**: Wprowadź nazwę aktualizacji. Ta nazwa wyświetlana w obszarze roboczym aktualizacje konsoli Updates Publisher.

    -   **Opis**: Opis przyjazny aktualizacji. Można uwzględnić instaluje aktualizację, i dlaczego lub gdy powinna być używana.

  **Klasyfikacja:** Poniżej przedstawiono typowe opisy różnych klasyfikacji.

  -   **Aktualizacja**: Aktualizacja aplikacji lub pliku, który jest obecnie zainstalowany.

  -   **Krytyczne**: Szeroko rozpowszechnianej aktualizacji dotyczącej konkretnego problemu, którego dotyczy krytyczne usterkę, która nie jest związane z zabezpieczeniami.

  -   **Feature Pack**: Nowych funkcji produktów dystrybuowanych poza wydaniami oraz najczęściej uwzględnianych w następnym pełnym wydaniu produktu.

  -   **Zabezpieczenia**: Szeroko rozpowszechnianej aktualizacji dotyczącej problemu określonego produktu, który jest związane z zabezpieczeniami.

  -   **Pakiet zbiorczy aktualizacji**: Zbiorczego zestawu poprawek zebranych w jednym pakiecie w celu łatwiejszego wdrażania. Poprawki tego typu mogą obejmować aktualizacje zabezpieczeń, aktualizacje krytyczne, aktualizacje zwykłe i tak dalej. Pakiet zbiorczy aktualizacji na ogół dotyczy konkretnego obszaru, takiego jak zabezpieczenia czy funkcję produktu.

  -   **Z dodatkiem Service Pack**: Zbiorczego zestawu poprawek stosujących się do aplikacji. Poprawki tego typu mogą obejmować aktualizacje zabezpieczeń, aktualizacje krytyczne, aktualizacje oprogramowania i tak dalej.

  -   **Narzędzie**: Określa narzędzie lub funkcja, która pomaga zakończenie jednego lub więcej zadań.

  -   **Sterownik**: Aktualizacja oprogramowania sterownika.

 **Dostawca**: Określ dostawcę aktualizacji. Wartości z aktualizacji, które znajdują się w repozytorium, można użyć listy rozwijanej. Po określeniu dostawcy, Kreator tworzy folder o tej nazwie dostawcy pod **wszystkie aktualizacje oprogramowania** w **obszar roboczy aktualizacje** Jeśli ten folder nie istnieje. Windows Server Update Services (WSUS) zarezerwowanych nazw, które nie może zostać wprowadzone aktualizacje, które można utworzyć są następujące:
 -   Microsoft Corporation
 -   Microsoft
 -   Aktualizacja
 -   Aktualizacja oprogramowania
 -   Narzędzia
 -   Narzędzie
 -   Krytyczny
 -   Aktualizacje krytyczne
 -   Zabezpieczenia
 -   Aktualizacje zabezpieczeń
 -   Dodatek Feature Pack
 -   Pakiet zbiorczy aktualizacji
 -   Dodatek Service Pack
 -   Sterownik
 -   Aktualizacja sterownika
 -   Pakiet
 -   Aktualizacja pakietu  <br /><br />

 **Produkt**: Określ typ produktu dla aktualizacji. Wartości z aktualizacji, które znajdują się w repozytorium, można użyć listy rozwijanej. Tę samą listę WSUS zarezerwowanych nazw, które nie mogą być używane w **dostawcy**, nie można używać dla **produktu**.

 **Więcej informacji o adres URL**: Podaj adres URL, gdzie można znaleźć więcej informacji na temat tej aktualizacji. Należy użyć małymi literami **https** lub **http** po wprowadzeniu tego adresu URL.

1.  Na **opcjonalne informacje o** strony, można skonfigurować szczegóły, które zawierają dodatkowe informacje na temat aktualizacji.

    -   **Identyfikator biuletynu**: Biuletyn identyfikatory są zwykle, ale nie zawsze dostarczane przez dostawców aktualizacji.

    -   **Identyfikator artykułu**: Jeśli artykuł aktualizacji oprogramowania jest dostępny, identyfikator artykułu może być przydatne osobom w poszukiwaniu dodatkowych informacji na temat aktualizacji.

    -   **Identyfikatory CVE:** Wyświetl listę znanych luk i zagrożeń CVE identyfikatory, które zapewniają informacji na temat aktualizacji zabezpieczeń lub zaktualizować pakiet. Podczas wyświetlania listy więcej niż jeden, użyj średnika, aby oddzielić CVEs, jak w poniższym przykładzie: *CVE1; CVE2.*

    -   **Adres URL pomocy technicznej:** Adres URL, który zawiera informacje o pomocy technicznej dla tej aktualizacji listy, jeśli jest dostępna. Należy użyć małymi literami **https** lub **http** po wprowadzeniu tego adresu URL.

    -   **Ważność:** Ustaw poziom ważności dla tej aktualizacji.

    -   **Wpływ:** Określić wpływ można użyć następujących opcji:
        -   **Normalny —** służy do wskazania aktualizacja wymaga instalacji standardowej procedury.
        -   **Minor —** służy do wskazania aktualizacja wymaga minimalnej instalacji procedur.
        -   **Wymaga obsługi wyłączny —** służy do wskazania, aktualizację należy zainstalować w sobie wyłączne z innymi aktualizacjami.   <br /><br />

    -   **Zachowanie ponownego uruchamiania:** Umożliwia uzyskanie informacji o zachowaniu ponownego uruchomienia aktualizacji. To ustawienie nie ma wpływu na rzeczywiste zachowanie instalacji aktualizacji.

        -   **Nigdy nie zostanie uruchomiony ponownie**: Komputer nigdy nie wykona ponowne uruchomienie systemu po zainstalowaniu aktualizacji oprogramowania.
        -   **Zawsze wymaga ponownego uruchomienia**: Komputer przeprowadzi zawsze ponowne uruchomienie systemu po zainstalowaniu aktualizacji oprogramowania.
        -   **Mogą poprosić o ponowne uruchomienie komputera**: Po zainstalowaniu aktualizacji oprogramowania, komputer żądań ponownego uruchomienia systemu, tylko wtedy, gdy konieczne jest ponowne uruchomienie. Użytkownik ma możliwość Odłóż ponowne uruchomienie. Jest to wartość domyślna. <br /><br />

2.  Na **wymagań wstępnych** Określ wymagania wstępne, które muszą być zainstalowane na komputerze przed zainstalowaniem tej aktualizacji. Reguły są nazywane **detectoids**. Detectoids to ogólne reguły podobny wymaga, aby komputery Procesora być 64-bitowy procesor. Detectoids można również określić określone aktualizacje, które należy zainstalować przed zainstalowaniem tej aktualizacji.

    -   Lepszą wydajność, użyj detectoids zamiast tworzyć *instalowalnych* i *zainstalowane reguły* które wykonują sprawdzanie tego samego lub akcji.

 Użyj opcji wyszukiwania dla **dostępne aktualizacje oprogramowania i detectoids** w celu znalezienia określonych detectoids. Na przykład, należy wyszukać frazę **Procesora** znaleźć detectoids umożliwiające ograniczenie instalacji na podstawie określonej architektury Procesora.

 Można wybrać co najmniej jeden detectoids w czasie, aby dodać jako warunek wstępny. Podczas dodawania wymagania wstępne, wybranych detectoids są dodawane jako jedną lub więcej grup. Aby kwalifikować się do instalacji, komputer musi spełniać wymagania co najmniej jednego członka z każdej grupy, które można skonfigurować:

 -   Po kliknięciu **Dodawanie wymagań wstępnych,** wszystkie detectoids wybrano są dodawane do oddzielnego, pojedyncze, grupy. Aby kwalifikować się do tej aktualizacji, komputer musi spełniają wymagania wstępne w tej grupie i przekazać wymagania dotyczące dodatkowe grupy, które są skonfigurowane.

 -   Po kliknięciu **Dodaj grupę** wszystkie detectoids wybrano są dodawane do jednej grupy. Aby kwalifikować się do tej aktualizacji, komputer musi spełniać co najmniej jeden z warunków wstępnych w tej grupie i przekazać wymagania dotyczące dodatkowe grupy, które są skonfigurowane.

1.  Na **zastępowania** Określ aktualizacje zastępowane (zastępowane) przez tę aktualizację. Po opublikowaniu tej aktualizacji programu Configuration Manager spowoduje oznaczenie każdej aktualizacji, który został zastąpiony jako **wygasłe**. Klienci zostanie zainstalowana ta aktualizacja zamiast zastąpionej aktualizacji.

2.  Na **stosowania** przycisków **Edytor reguły** do zdefiniowania zestawu reguł, które określają, czy urządzenie wymaga tej aktualizacji. (Ta strona jest podobny do **zainstalowane** strony, który następuje po nim.)

    Aby dodać nową regułę, kliknij ![Nowa reguła](media/newrule.png). Spowoduje to otwarcie strony stosowania reguły konfigurowania reguł.

    Typy zasad, które można utworzyć:

    -   **Plik** — ta zasada umożliwia mieć urządzenia pliku z właściwościami, które spełniają jeden lub więcej kryteriów Określ przed tej aktualizacji można zastosować.

    -   **Rejestr —** ten typ umożliwia określenie szczegółów rejestru, które muszą być obecne przed urządzenie kwalifikuje się do zainstalowania tej aktualizacji.

    -   **System —** zasada używa szczegóły systemu do ustalenia możliwości zastosowania. Można wybrać Definiowanie wersji systemu Windows, Windows języka, architektury procesora lub określ kwerendę usługi WMI do identyfikowania urządzeń systemu operacyjnego.

    -   **Instalator systemu Windows —** ta reguła służy do określenia stosowania oparte na zainstalowany. Poprawka MSI lub Instalatora systemu Windows (. MSP). Można również określić, czy określone składniki lub funkcje są instalowane w ramach zapotrzebowania.

        > [!IMPORTANT]  
        > Na zarządzanych deices, usługa Windows Update Agent nie może wykryć pakiety instalacji systemu Windows, które są zainstalowane dla poszczególnych użytkowników. Korzystając z tego typu reguły, należy skonfigurować zasady stosowania dodatkowych, takich jak wartości klucza rejestru lub wersje plików, tak aby pakiet Instalatora Windows może prawidłowo wykrył niezależnie od konkretnego użytkownika lub całego systemu.

    -   **Zapisano regułę —** ta opcja umożliwia znaleźć i używać reguł można *utworzone w obszarze roboczym reguły*.

        Po utworzeniu reguły można używać innych ikon zmodyfikować reguły, a jeśli wiele reguł, aby zdefiniować relacje między tymi zasadami.

 Gdy wszystko jest gotowe, tworzenie i dodawanie reguł, kliknij przycisk **OK** w **Tworzenie zestawu reguł** okno dialogowe, aby zapisać ten zestaw. Następnie można utworzyć **New** regułę i dodaj ją do zestawu, jak również.

 Gdy istnieje wiele reguł lub zestawów reguł do dodania do aktualizacji, można użyć operatorów logicznych w **Edytor reguły** określenia warunków między reguły i w jakiej kolejności przetwarzania.

1.  Na **zainstalowane** przycisków **reguły w edytorze** definiują zestaw reguł, które określają, czy urządzenie ma już zainstalowana aktualizacja są konfigurowane. (Ta strona jest podobny do **stosowania** strony, że ta strona jest kontynuowana.)

    Ta strona kreatora obsługuje Konfigurowanie reguł o tej samej kryteriów, jak i opcje **stosowania** strony.

Po zakończeniu pracy Kreatora nowego aktualizacja została dodana do węzła w **aktualizacje obszaru roboczego** identyfikowane przez **dostawcy** nazwę używaną dla tej aktualizacji.

## <a name="use-the-create-bundle-wizard"></a>Użyj Kreatora tworzenia pakietu
Ponieważ ten kreator używa tego samego przepływu pracy jako [Kreatora tworzenia aktualizacji](#use-the-create-update-wizard), użyj tego przepływu pracy, ale następujące różnice dla pakiety:

1.  Aby uruchomić kreatora, w konsoli przejdź do **obszar roboczy aktualizacje**, a następnie wybierz **pakietu** z **Home** karty wstążki.

2.  W przeciwieństwie do kreatora Utwórz aktualizacji nie ma żadnej strony pakietu podczas tworzenia pakietu.

3.  Na **informacji** Określ szczegółowe informacje o pakiet aktualizacji, które są uwzględniane podczas publikowania aktualizacji lub wyeksportować.

4.  Na **opcjonalne informacje o** strony, można skonfigurować szczegóły, które zawierają dodatkowe informacje o pakiecie aktualizacji. Dostępne opcje są takie same jak w przypadku tworzenia aktualizacji. Jednak opcje wpływ i uruchom ponownie zachowanie nie są dostępne, jak nie dotyczą pakiety.

5.  Na **wymagań wstępnych** Określ wymagania wstępne, które muszą być zainstalowane na komputerze przed zainstalowaniem tego pakietu. Te zasady są takie same, jak dotyczące poszczególnych aktualizacji.

6.  Na **zastępowania** Określ aktualizacje zastępowane (zastąpiony) tego pakietu aktualizacji. Te zasady są takie same, jak dotyczące poszczególnych aktualizacji.

7.  Na **członków** strony, wybierz aktualizacje do dodania do pakietu aktualizacji. Dostępne są tylko aktualizacje zostały utworzone lub zaimportowane do Updates Publisher.

Po zakończeniu pracy Kreatora nowego pakietu aktualizacji jest dodawany do węzła w **aktualizacje obszaru roboczego** identyfikowane przez **dostawcy** nazwę używaną dla pakietu aktualizacji.

