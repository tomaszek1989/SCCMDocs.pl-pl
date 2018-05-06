---
title: Utwórz aktualizacji
titleSuffix: Configuration Manager
description: Tworzenie i udostępnianie pakietów aktualizacji oprogramowania z programem System Center Updates Publisher
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.topic: conceptual
ms.assetid: 46a1a8ac-126c-4ee6-ae09-32dfbdb83368
author: aczechowski
ms.author: aaroncz
manager: dougeby
robots: NOINDEX, NOFOLLOW
ms.openlocfilehash: 3f22e7ed209496c2d679591a9c7b282f811f4ae1
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="create--software-updates-and-update-bundles-with-updates-publisher"></a>Utwórz aktualizacji oprogramowania i pakietów aktualizacji przez program Updates Publisher

*Dotyczy: System Center Updates Publisher*

Z programem Updates Publisher można użyć **utworzyć zaktualizować** kreatora w celu utworzenia własnych aktualizacji i **Tworzenie pakietu** kreatora, aby utworzyć pakiety aktualizacji.

Ponieważ tych dwóch kreatorów mają podobne przepływu pracy, procedura tworzenia pakietu aktualizacji odwołuje się do procedury tworzenia aktualizacji, tylko istotne różnice szczegółowe.

## <a name="use-the-create-update-wizard"></a>Użyj Kreatora tworzenia aktualizacji
1.  W konsoli przejdź do **roboczym aktualizacje**, a następnie w **wprowadzenie** okienku wybierz **aktualizacji** z **Home** karty wstążki. Spowoduje to otwarcie **utworzyć zaktualizować** kreatora.

2.  Na **pakietu** strony, skorzystaj z poniższych informacji w celu skonfigurowania aktualizacji:

    -   Wybierz **Przeglądaj** można znaleźć pakietu aktualizacji oprogramowania będzie używany jako źródło pakietu. Nieprawidłowa źródła obejmują. MSI. MSP, lub. Pliki EXE. Updates Publisher wymaga dostępu do pliku w celu utworzenia skrótu pliku. Skrót i nazwa pliku są następnie używane w metadanych aktualizacji dla tworzonego aktualizacji.

    -   Określ lokalizację źródła zawartości dla tej aktualizacji. Zwykle jest to lokalizacja, gdy dane binarne aktualizacji zostaną pobrane z podczas publikowania na serwerze WSUS.  Jeśli **publikowanie zawartości aktualizacji oprogramowania przy użyciu lokalnego źródła** opcja jest zaznaczona, a następnie ścieżka nie jest wymagana.

        Później po opublikowaniu aktualizacji na serwerze WSUS, Updates Publisher pobieranie plików binarnych aktualizacji w lokalizacji wskazanej źródłowej.  Jeśli ścieżka nie jest dostarczonego, przeszuka Update Publisher [lokalnego źródła ścieżkę publikacji](/sccm/sum/tools/updates-publisher-options#advanced) danych binarnych aktualizacji.

    -   Określ **binarne języka** aktualizacji oprogramowania.

    -   Określ **kody powrotne Powodzenie**, i **Powodzenie do czasu ponownego rozruchu kodów** aktualizacji. Oddziel wiele kodów powrotnych za pomocą przecinka. Kody powrotne służy do określenia podczas instalacji aktualizacji zakończyło się pomyślnie, a kiedy były wymagane ponowne uruchomienie.

        -   Pliki Instalatora systemu Windows i poprawki (. MSI i. Pliki MSP), automatycznie ustaw te wartości i nie może być modyfikowany.

        -   Aby uzyskać. Aktualizuje EXE, kody domyślne zdefiniowane przez. Plik EXE są używane, jeśli nie określono żadnych kodów powrotu.

    -   Określ argumenty wiersza polecenia, które są wymagane do zainstalowania aktualizacji oprogramowania.

        -   Pliki Instalatora systemu Windows i poprawki (. MSI i. Pliki MSP), automatycznie ustaw te wartości. Dla tych typów plików argumenty muszą być określone jako  **\[nazwa\]=\[wartość\]**. Ponadto wszystkie opcje rozpoczynających się od **/** (takich jak **/qn**) nie są obsługiwane dla. MSI lub. Aktualizacje oprogramowania MSP.

        -   Aby uzyskać. Aktualizacje EXE, wszystkie argumenty są prawidłowe.

3.  Na **informacji** Określ szczegółowe informacje o aktualizacji, które są zawarte w aktualizacji jest opublikowana ani eksportowane. Szczegółowe informacje zawierają zlokalizowanych właściwości, takie jak nazwa aktualizacji (tytuł) i opis. Następnie określ ogólne szczegóły, takie jak Klasyfikacja, dostawca, produktu i miejsca dowiedzieć się więcej o aktualizacji.

     __Zlokalizowane właściwości:__

    -   **Język**: Wybierz język, a następnie określ tytuł i opis. Następnie możesz wybrać dodatkowe języki, w czasie, z pomocniczych własny tytuł i opis każdego z języków.

    -   **Tytuł**: Wprowadź nazwę aktualizacji. Ta nazwa jest wyświetlana w obszarze roboczym aktualizacje z konsoli programu Updates Publisher.

    -   **Opis elementu**: Przyjazny opis aktualizacji. Może obejmować instaluje aktualizację i dlaczego lub gdy powinien być używany.

     **Klasyfikacji:** Poniżej przedstawiono opisy typowych różne klasyfikacje.

    -   **Aktualizacja**: Aktualizacja aplikacji lub pliku, który jest obecnie zainstalowany.

    -   **Krytyczne**: Szeroko rozpowszechnianej aktualizacji dotyczącej konkretnego problemu, którego dotyczy krytyczne usterkę, która nie jest związana z zabezpieczeniami.

    -   **Feature Pack**: Nowych funkcji produktów dystrybuowanych poza wydaniami oraz najczęściej uwzględnianych w następnym pełnym wydaniu produktu.

    -   **Zabezpieczenia**: Szeroko rozpowszechnianej aktualizacji dotyczącej problemu określonego produktu, który jest związana z zabezpieczeniami.

    -   **Pakiet zbiorczy aktualizacji**: Zbiorczego zestawu poprawek zebranych w jednym pakiecie w celu łatwiejszego wdrażania. Poprawki tego typu mogą obejmować aktualizacje zabezpieczeń, aktualizacje krytyczne, aktualizacje zwykłe i tak dalej. Pakiet zbiorczy aktualizacji na ogół dotyczy konkretnego obszaru, takiego jak zabezpieczenia czy funkcji produktu.

    -   **Z dodatkiem Service Pack**: Zbiorczego zestawu poprawek przeznaczonych do aplikacji. Poprawki tego typu mogą obejmować aktualizacje zabezpieczeń, aktualizacje krytyczne, aktualizacje oprogramowania i tak dalej.

    -   **Narzędzie**: Określa narzędzie lub funkcję, która ułatwia wykonywanie jednego lub więcej zadań.

     -   **Sterownik**: Aktualizacja oprogramowania sterownika.

    **Dostawcy:** Należy określić dostawcę dla aktualizacji. Aby użyć wartości aktualizacje, które znajdują się w repozytorium, można użyć listy rozwijanej. Po określeniu dostawcy, Kreator tworzy folder o tej nazwie dostawcy pod **wszystkie aktualizacje oprogramowania** w **roboczym aktualizacje** Jeśli wybrany folder nie istnieje. Poniżej przedstawiono systemu Windows Server Update Services (WSUS) zarezerwowanych nazw, które nie można wprowadzić aktualizacji, które można utworzyć:
 >*   Microsoft Corporation
 >*   Microsoft
 >*   Aktualizacja
 >*   Aktualizacja oprogramowania
 >*   Narzędzia
 >*   Narzędzie
 >*   Krytyczny
 >*   Aktualizacje krytyczne
 >*   Zabezpieczenia
 >*   Aktualizacje zabezpieczeń
 >*   Feature Pack
 >*   Pakiet zbiorczy aktualizacji
 >*   Dodatek Service Pack
 >*   Sterownik
 >*   Aktualizacja sterownika
 >*   Pakietu
 >*   Pakietu aktualizacji

**Produkt**: Określ typ produktu dla aktualizacji. Aby użyć wartości aktualizacje, które znajdują się w repozytorium, można użyć listy rozwijanej. Tę samą listę usług WSUS zarezerwowanych nazw, których nie można użyć dla **dostawcy**, nie może służyć do **produktu**.

 **Więcej informacji o adres URL**: Podaj adres URL, gdzie można znaleźć więcej informacji na temat tej aktualizacji. Należy użyć małymi literami **https** lub **http** po wprowadzeniu tego adresu URL.

4.  Na **opcjonalne informacje o** strony, można skonfigurować szczegółowe informacje, które znajdują się dodatkowe informacje o aktualizacji.

    -   **Identyfikator biuletynu**: Identyfikatory biuletynu są zwykle, ale nie zawsze dostarczane przez dostawców aktualizacji.

    -   **Identyfikator artykułu**: Jeśli artykuł aktualizacji oprogramowania jest dostępny, identyfikator artykułu może być przydatne do osób, w poszukiwaniu dodatkowych informacji na temat aktualizacji.

    -   **Identyfikatory CVE:** Lista znanych luk i zagrożeń CVE identyfikatorów, które zapewniają zabezpieczenia informacji na temat aktualizacji lub pakietu aktualizacji. Podczas wyświetlania więcej niż jeden, użyj średnika do rozdzielenia CVEs jak w poniższym przykładzie: *CVE1; CVE2.*

    -   **Adres URL pomocy technicznej:** Wyświetl listę adres URL, który zawiera informacje o pomocy technicznej dla tej aktualizacji, jeśli jest dostępna. Należy użyć małymi literami **https** lub **http** po wprowadzeniu tego adresu URL.

    -   **Ważność:** Ustaw poziom ważności, dla tej aktualizacji.

    -   **Wpływ:** Następujące opcje mogą służyć do określenia wpływu:
        -   **Normalny —** użyć, aby wskazać, aktualizacja wymaga instalacji standardowej procedury.
        -   **Drobne —** użyć, aby wskazać, aktualizacja wymaga minimalnej instalacji procedur.
        -   **Wymaga wyłącznego Obsługa —** użyć, aby wskazać aktualizację mogą być instalowane przez samego wyłącznego z innymi aktualizacjami.   <br /><br />

    -   **Zachowanie ponownego uruchamiania:** Umożliwia uzyskanie informacji dotyczących zachowania ponownego uruchomienia aktualizacji. To ustawienie nie ma wpływu na zachowanie rzeczywistych instalacji aktualizacji.

        -   **Nigdy nie wykonuje ponowny rozruch**: Komputer nigdy nie wykonuje ponowne uruchomienie systemu, po zainstalowaniu aktualizacji oprogramowania.
        -   **Zawsze wymaga ponownego uruchomienia**: Komputer zawsze przeprowadza ponowne uruchomienie systemu, po zainstalowaniu aktualizacji oprogramowania.
        -   **Mogą żądać ponownego uruchomienia**: Po zainstalowaniu aktualizacji oprogramowania, komputer żądań ponownego uruchomienia systemu, tylko wtedy, gdy konieczne jest ponowne uruchomienie. Użytkownik ma możliwość Odłóż ponowne uruchomienie. Jest to wartość domyślna. <br /><br />

5.  Na **wymagań wstępnych** Określ wymagania wstępne, które muszą być zainstalowane na komputerze, zanim można zainstalować tej aktualizacji. Wymagania wstępne może być **detectoids** lub inne aktualizacje. Detectoids są wysokiego poziomu reguł, takich jak wymaga komputerów może być 64-bitowy procesor. Detectoids można również określić określone aktualizacje, które muszą zostać zainstalowane zanim można zainstalować tej aktualizacji.

    -   W celu poprawy wydajności użyj detectoids zamiast tworzenia *instalowalnych* i *zainstalowane reguły* które wykonują samego wyboru lub akcji.

    Użyj opcji wyszukiwania dla **dostępne aktualizacje oprogramowania i detectoids** w celu znalezienia określone aktualizacje lub detectoids. Na przykład wyszukiwania na **Procesora** można znaleźć detectoids umożliwiające ograniczać instalację określonych architektury Procesora.

    Jednocześnie można dodać jako warunek wstępny, można wybrać co najmniej jeden element. Podczas dodawania wymagania wstępne, wybranych detectoids są dodawane jako co najmniej jedną grupę. Aby zakwalifikować się do instalacji, komputer musi spełniać wymagania co najmniej jednego członka w każdej z grup, które można skonfigurować:

 -   Po kliknięciu **Dodawanie wymagań wstępnych,** wszystkie elementy wybrane są dodawane do oddzielnego, pojedyncze, grupy. Aby zakwalifikować się do tej aktualizacji, komputer musi spełniają wymagania wstępne w tej grupie i przekazać wymagania dotyczące dodatkowych grup, które są skonfigurowane.

 -   Po kliknięciu **Dodaj grupę** wszystkie elementy wybrane są dodawane do pojedynczej grupy. Aby zakwalifikować się do tej aktualizacji, komputer musi spełniać co najmniej jeden z warunków wstępnych w tej grupie i przekaż wymagania dotyczące dodatkowych grup, które są skonfigurowane.

6.  Na **zastępowania** Określ aktualizacje, które są zastępowane (zastępowane) przez tę aktualizację. Po opublikowaniu tej aktualizacji programu Configuration Manager spowoduje oznaczenie poszczególnych aktualizacji, które są zastępowane jako **wygasłe**. Klienci następnie zainstaluje tę aktualizację, zamiast zastąpionych aktualizacji.

7.  Na **zastosowania** strony użyj **Edytor reguł** do zdefiniowania zestawu reguł, które określają, czy urządzenie wymaga tej aktualizacji. (Ta strona jest podobny do **zainstalowana** strony, która następuje.)

    Aby dodać nową regułę, kliknij ![Nowa reguła](media/newrule.png). Spowoduje to otwarcie strony reguła zastosowania, w którym można skonfigurować reguły.

    Typy zasad, które można utworzyć:

    -   **Plik** — użycia tej reguły, aby mieć urządzenia pliku z właściwościami, które spełniają jeden lub więcej kryteria przed tę aktualizację można zastosować.

    -   **Rejestr —** tego typu umożliwia określenie szczegółów rejestru, które muszą być obecne zanim urządzenie kwalifikuje się do zainstalowania tej aktualizacji.

    -   **System —** ta zasada używa szczegóły systemu w celu określenia możliwości zastosowania. Można wybrać Definiowanie wersji systemu Windows, Windows języka, architektury procesora, lub określ kwerendę usługi WMI, aby zidentyfikować system operacyjny urządzenia.

    -   **Instalator Windows —** ta reguła służy do określenia zastosowania oparte na zainstalowanym. Poprawka MSI lub Instalatora systemu Windows (.MSP). Można również określić, czy określone składniki i funkcje są instalowane jako część wymagań.

        > [!IMPORTANT]  
        > Z zarządzanych deices, Windows Update Agent nie może wykryć pakietów instalacji systemu Windows, które są zainstalowane dla poszczególnych użytkowników. Korzystając z tego typu reguł, należy skonfigurować reguły stosowania dodatkowych, takich jak wersji plików lub wartości klucza rejestru, aby pakiet Instalatora Windows, które mogą być poprawnie wykrywane niezależnie od tego, bazując na użytkownika lub systemu.

    -   **Zapisano regułę —** ta opcja umożliwia znalezienia i użycia reguły można *utworzone w obszarze roboczym zasady*.

        Po utworzeniu reguły można inne ikony zmodyfikuj regułę, a jeśli wiele reguł, aby zdefiniować relacje między tymi zasadami.

    Gdy wszystko jest gotowe, tworzenie i dodawanie reguły, kliknij przycisk **OK** w **Tworzenie zestawu reguł** okno dialogowe, aby zapisać tego zestawu. Następnie możesz utworzyć **nowy** reguły i dodać go również w zestawie.

    Jeśli istnieje wiele reguł lub zestawów reguł do dodania do aktualizacji, możesz użyć operatory logiczne w **Edytor reguł** określenia warunków między reguły i w jakiej kolejności przetwarzania.

8.  Na **zainstalowana** strony użyj **Edytor reguł do** zdefiniować zestaw reguł, które określają, czy urządzenie ma już zainstalowany aktualizacji są konfigurowane. (Ta strona jest podobny do **zastosowania** strony, która będzie kontynuowana tej strony.)

    Ta strona kreatora obsługuje Konfigurowanie reguł o tych samych opcji i kryteria **zastosowania** strony.

    Po zakończeniu działania kreatora nowy aktualizacja została dodana do węzła w **aktualizacji obszaru roboczego** identyfikowane przez **dostawcy** i **produktu** nazwa używana dla tej aktualizacji.

## <a name="use-the-create-bundle-wizard"></a>Użyj Kreatora tworzenia pakietu
Ponieważ ten kreator używa tego samego przepływu pracy jako [kreatora Utwórz aktualizacji](#use-the-create-update-wizard), użyj tego przepływu pracy, ale następujące różnice dla pakietów:

1.  Aby uruchomić kreatora, w konsoli przejdź do **roboczym aktualizacje**, a następnie wybierz **pakietu** z **Home** karty wstążki.

2.  W przeciwieństwie do kreatora Utwórz aktualizacji nie ma żadnej strony pakietu podczas tworzenia pakietu.

3.  Na **informacji** Określ szczegóły pakietu aktualizacji, które są zawarte w aktualizacji jest opublikowana lub wyeksportować.

4.  Na **opcjonalne informacje o** strony, można skonfigurować szczegółowe informacje, które zapewniają dodatkowe informacje na temat pakietu aktualizacji. Dostępne opcje są takie same, jak w przypadku tworzenia aktualizacji. Jednak opcje wpływ i zachowania ponownego uruchomienia nie są dostępne, ponieważ nie mają zastosowania do pakietów.

5.  Na **wymagań wstępnych** Określ wymagania wstępne, które muszą być zainstalowane na komputerze, aby zainstalować ten pakiet. Te reguły są takie same, jak pokazano na poszczególne aktualizacje.

6.  Na **zastępowania** Określ aktualizacje, które są zastępowane (zastąpiona) tego pakietu aktualizacji. Te reguły są takie same, jak pokazano na poszczególne aktualizacje.

7.  Na **członków** strony, aktualizacje należy wybrać, aby dodać pakiet aktualizacji. Dostępne są tylko aktualizacje zostały utworzone lub zaimportować do programu Updates Publisher.

Po zakończeniu działania Kreatora nowego pakietu aktualizacji jest dodawany do węzła w **aktualizacji obszaru roboczego** identyfikowane przez **dostawcy** nazwę używaną dla pakietu aktualizacji.
