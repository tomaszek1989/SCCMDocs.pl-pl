---
title: "Użyj analizy zasobów"
titleSuffix: Configuration Manager
description: "Wykonywać typowe zadania analizy zasobów w programie System Center Configuration Manager."
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e8159bd9-5c2b-4d25-82f9-78fcfd732ba9
caps.latest.revision: 
caps.handback.revision: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 7838f087c18a2cfad6ff487ff987e638906faf6a
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="how-to-use-asset-intelligence-in-system-center-configuration-manager"></a>Jak używać analizy zasobów w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Ten temat zawiera informacje ułatwiające zarządzanie typowych zadań analizy zasobów w hierarchii programu System Center Configuration Manager:  

##  <a name="BKMK_ViewInformation"></a> Wyświetlanie informacji o analizie zasobów  
 Informacje dotyczące analizy zasobów możesz wyświetlać na stronie głównej **Analiza zasobów** oraz w raportach analizy zasobów.  

###  <a name="BKMK_AssetIntelligenceHomePage"></a> Strona główna Analiza zasobów  
 Na stronie głównej **Analiza zasobów** jest wyświetlany pulpit nawigacyjny podsumowania zawierający informacje o katalogu analizy zasobów. Na stronie głównej możesz wyświetlać informacje o synchronizacji katalogu i stanie spisanego oprogramowania. Strona główna **Analiza zasobów** jest podzielona na następujące sekcje:  

-   **Synchronizacja katalogu**: Informacje na temat tego, czy analiza zasobów jest włączona, bieżący stan punktu synchronizacji analizy zasobów, harmonogramie synchronizacji, czy zestawienie licencji klienta jest zaimportowane, ostatniej aktualizacji stanu i podczas następnej zaplanowanej aktualizacji oraz liczbę zmian, które wystąpiły po zainstalowaniu systemu lokacji punktu synchronizacji analizy zasobów.  

    > [!NOTE]  
    >  Sekcja synchronizacji katalogu analizy zasobów jest wyświetlana na stronie **Analiza zasobów** tylko wtedy, gdy zainstalowano rolę systemu lokacji punktu synchronizacji analizy zasobów.  

-   **Stan spisanego oprogramowania**: Zawiera ilość i odsetek spisanego oprogramowania, kategorie oprogramowania i rodziny oprogramowania, które są identyfikowane przez firmę Microsoft, zidentyfikowane przez użytkownika administracyjnego, będące w toku identyfikacji online lub niezidentyfikowane i nieoczekujące. Informacje wyświetlane w formacie tabeli zawierają liczbę elementów w każdej kategorii, natomiast informacje wyświetlane na wykresie przedstawiają odsetek dla każdej z nich.  

 Poniższa procedura umożliwia wyświetlenie informacji dotyczących analizy zasobów na stronie głównej **Analiza zasobów** .  

##### <a name="to-view-asset-intelligence-information-on-the-asset-intelligence-home-page"></a>Aby wyświetlić informacje dotyczące analizy zasobów na stronie głównej Analiza zasobów  

1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.  

2.  W obszarze roboczym **Zasoby i zgodność** kliknij pozycję **Analiza zasobów**. Zostaną wyświetlone raporty analizy zasobów.  

###  <a name="BKMK_AssetIntelligenceReports"></a> Raporty analizy zasobów  
 Istnieje ponad 60 raportów analizy zasobów, które przedstawiają informacje zebrane w ramach analizy zasobów. Wiele z tych raportów łączy się z bardziej szczegółowymi raportami, w których możesz znaleźć ogólne informacje, a następnie przejść do informacji bardziej szczegółowych. Raporty analizy zasobów znajdują się w konsoli programu Configuration Manager w **monitorowanie** obszaru roboczego, w obszarze **raportowania** węzła. Raporty zapewniają informacje dotyczące sprzętu, zarządzania licencjami oraz oprogramowania. Aby uzyskać więcej informacji o raportach w programie Configuration Manager, zobacz [raportowania w programie System Center Configuration Manager](../../../../core/servers/manage/reporting.md).  

> [!NOTE]  
>  Informacje o liczbach i licencjach zainstalowanych tytułów oprogramowania wyświetlane w raportach analizy zasobów mogą się różnić od rzeczywistej liczby zainstalowanych tytułów oprogramowania lub licencji używanych w środowisku z powodu złożonych zależności i ograniczeń występujących podczas tworzenia spisu informacji o licencjach dla tytułów oprogramowania zainstalowanych w środowiskach przedsiębiorstw. Raportów analizy zasobów nie należy używać jako jedynego źródła informacji podczas określania zgodności zakupionych licencji na oprogramowanie.  

 Poniższa procedura umożliwia wyświetlenie informacji dotyczących analizy zasobów za pomocą raportów analizy zasobów.  

##### <a name="to-view-collected-asset-intelligence-information-by-using-asset-intelligence-reports"></a>Aby wyświetlić zebrane informacje dotyczące analizy zasobów za pomocą raportów analizy zasobów  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W obszarze roboczym **Monitorowanie** rozwiń węzeł **Raportowanie**i węzeł **Raporty**, a następnie kliknij pozycję **Analiza zasobów**. Zostaną wyświetlone raporty analizy zasobów.  

    > [!WARNING]  
    >  Jeśli w węźle **Raporty** nie istnieją żadne foldery raportów, sprawdź, czy skonfigurowano raportowanie. Aby uzyskać więcej informacji, zobacz [konfigurowanie raportowania w programie System Center Configuration Manager](../../../../core/servers/manage/configuring-reporting.md).  

3.  Wybierz raport analizy zasobów, który chcesz uruchomić, a następnie na karcie **Narzędzia główne** w grupie **Grupa raportów** kliknij polecenie **Uruchom**.  

##  <a name="BKMK_SynchronizeTheCatalog"></a> Synchronizacja katalogu analizy zasobów  
 Możesz zsynchronizować lokalny katalog analizy zasobów z programem System Center Online, aby pobrać najnowszą kategoryzację tytułów oprogramowania. W przypadku ręcznego zażądania synchronizacji katalogu z programem System Center Online wykonanie procesu synchronizacji z programem System Center Online może zająć 15 minut lub dłużej. Aktualizacje programu Configuration Manager **Ostatnia pomyślna aktualizacja** ustawienie **analizy zasobów** strony głównej przy użyciu bieżącego czasu po pomyślnym zakończeniu synchronizacji.  

> [!NOTE]  
>  Przed użyciem procedur należy zainstalować rolę systemu lokacji punktu synchronizacji analizy zasobów. Aby uzyskać informacje o instalowaniu punktu synchronizacji analizy zasobów, zobacz [Konfigurowanie analizy zasobów w programie System Center Configuration Manager](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md).  

 Poniższa procedura umożliwia utworzenie harmonogramu synchronizacji katalogu analizy zasobów.  

#### <a name="to-create-a-synchronization-schedule-for-the-asset-intelligence-catalog"></a>Aby utworzyć harmonogram synchronizacji katalogu analizy zasobów  

1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.  

2.  W obszarze roboczym **Zasoby i zgodność** kliknij pozycję **Analiza zasobów**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij polecenie **Synchronizuj**, a następnie kliknij pozycję **Synchronizacja według harmonogramu**.  

4.  W oknie dialogowym **Harmonogram punktu synchronizacji analizy zasobów** wybierz polecenie **Włącz synchronizację według harmonogramu**, a następnie skonfiguruj harmonogram prosty lub niestandardowy.  

5.  Kliknij przycisk **OK** , aby zapisać zmiany.  

    > [!NOTE]  
    >  Informacje o harmonogramie synchronizacji, w tym o następnej zaplanowanej synchronizacji, zawiera węzeł **Analiza zasobów** w obszarze roboczym **Zasoby i zgodność** lokacji najwyższego poziomu w hierarchii.  

 Poniższa procedura umożliwia ręczne zsynchronizowanie katalogu analizy zasobów.  

> [!WARNING]  
>  Program System Center Online akceptuje tylko jedno żądanie ręcznej synchronizacji w okresie 12-godzinnym.  

###  <a name="BKMK_ManuallySynchronizeCatalog"></a> Aby ręcznie zsynchronizować katalog analizy zasobów  

1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.  

2.  W obszarze roboczym **Zasoby i zgodność** kliknij pozycję **Analiza zasobów**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij polecenie **Synchronizuj**, kliknij pozycję **Synchronizuj katalog analizy zasobów**, a następnie kliknij przycisk **OK**.  

##  <a name="BKMK_CustomizeCatalog"></a> Dostosowywanie katalogu analizy zasobów  
 Informacje o kategoryzacji katalogu analizy zasobów odebrane z programu System Center Online są przechowywane w bazie danych lokacji z uprawnieniami tylko do odczytu. Nie można ich modyfikować ani usuwać. Możesz jednak tworzyć, modyfikować i usuwać niestandardowe kategorie oprogramowania, rodziny oprogramowania, etykiety oprogramowania i informacje katalogu wymagań dotyczących sprzętu. Następnie możesz używać niestandardowych danych kategoryzacji zamiast informacji dostarczonych przez program System Center Online na potrzeby informacji o istniejących lub zdefiniowanych przez użytkownika tytułach oprogramowania. Po zmianie lub dodaniu informacji o kategoryzacji informacje katalogu są uznawane za zdefiniowane przez użytkownika. Informacje o kategoryzacji zdefiniowane przez użytkownika są przechowywane w innych tabelach bazy danych niż zweryfikowane informacje katalogu.  

###  <a name="BKMK_SoftwareCategories"></a> Kategorie oprogramowania  
 Kategorie oprogramowania analizy zasobów służą do ogólnego kategoryzowania spisanych tytułów oprogramowania i są również używane jako ogólne grupy dla bardziej konkretnych rodzin oprogramowania. Na przykład kategorią oprogramowania mogą być firmy z branży elektroenergetycznej, a rodziną oprogramowania w ramach tej kategorii oprogramowania — ropa naftowa i gaz lub elektrownie wodne. Wiele kategorii oprogramowania jest wstępnie zdefiniowanych w katalogu analizy zasobów, a użytkownik może utworzyć dodatkowe kategorie, aby lepiej zdefiniować spisane oprogramowanie. Stan sprawdzania poprawności dla wszystkich wstępnie zdefiniowanych kategorii oprogramowania to zawsze **Zweryfikowane**, a informacje o niestandardowych kategoriach oprogramowania dodane do katalogu analizy zasobów mają stan **Zdefiniowane przez użytkownika**.  

 Poniższa procedura umożliwia utworzenie zdefiniowanej przez użytkownika kategorii oprogramowania.  

##### <a name="to-create-a-user-defined-software-category"></a>Aby utworzyć zdefiniowaną przez użytkownika kategorię oprogramowania  

1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.  

2.  W obszarze roboczym **Zasoby i zgodność** kliknij pozycję **Analiza zasobów**, a następnie kliknij pozycję **Katalog**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij polecenie **Utwórz kategorię oprogramowania**.  

4.  Na stronie **Ogólne** wprowadź nazwę nowej kategorii oprogramowania i, opcjonalnie, opis.  

    > [!NOTE]  
    >  Stan sprawdzania poprawności dla wszystkich nowych niestandardowych kategorii oprogramowania ma zawsze wartość **Zdefiniowane przez użytkownika**.  

     Kliknij przycisk **Dalej**.  

5.  Sprawdź ustawienia na stronie **Podsumowanie** , a następnie kliknij przycisk **Dalej**.  

6.  Aby zamknąć kreatora, kliknij na stronie **Ukończenie** przycisk **Zamknij** .  

###  <a name="BKMK_SoftwareFamilies"></a> Rodziny oprogramowania  
 Rodziny oprogramowania analizy zasobów są używane do dokładniejszego definiowania spisanych tytułów oprogramowania w ramach kategorii oprogramowania. Na przykład kategorią oprogramowania mogą być firmy z branży elektroenergetycznej, a rodziną oprogramowania w ramach tej kategorii oprogramowania — ropa naftowa i gaz lub elektrownie wodne. Wiele rodzin oprogramowania jest wstępnie zdefiniowanych w katalogu analizy zasobów, a użytkownik może utworzyć dodatkowe rodziny, aby zdefiniować spisane oprogramowanie. Stan sprawdzania poprawności dla wszystkich wstępnie zdefiniowanych rodzin oprogramowania to zawsze **Zweryfikowane**, a informacje o niestandardowych rodzinach oprogramowania dodane do katalogu analizy zasobów mają stan **Zdefiniowane przez użytkownika**.  

 Poniższa procedura umożliwia utworzenie zdefiniowanej przez użytkownika rodziny oprogramowania.  

##### <a name="to-create-a-user-defined-software-family"></a>Aby utworzyć zdefiniowaną przez użytkownika rodzinę oprogramowania  

1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.  

2.  W obszarze roboczym **Zasoby i zgodność** kliknij pozycję **Analiza zasobów**, a następnie kliknij pozycję **Katalog**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij polecenie **Utwórz rodzinę oprogramowania**.  

4.  Na stronie **Ogólne** wprowadź nazwę nowej rodziny oprogramowania i, opcjonalnie, opis.  

    > [!NOTE]  
    >  Stan sprawdzania poprawności dla wszystkich nowych niestandardowych rodzin oprogramowania ma zawsze wartość **Zdefiniowane przez użytkownika**.  

5.  Sprawdź ustawienia na stronie **Podsumowanie** , a następnie kliknij przycisk **Dalej**.  

6.  Aby zamknąć kreatora, kliknij na stronie **Ukończenie** przycisk **Zamknij** .  

###  <a name="BKMK_SoftwareLabels"></a> Etykiety oprogramowania  
 Niestandardowe etykiety oprogramowania analizy zasobów pozwalają tworzyć filtry służące do grupowania tytułów oprogramowania i wyświetlania ich w raportach analizy zasobów. Możesz na przykład utworzyć etykietę oprogramowania o nazwie „shareware”, skojarzyć ją z kilkoma aplikacjami, a następnie uruchomić raport pokazujący wszystkie tytuły z etykietą oprogramowania „shareware”. Stan sprawdzania poprawności dla wszystkich niestandardowych etykiet oprogramowania dodanych do katalogu analizy zasobów to **Zdefiniowane przez użytkownika** .  

 Poniższa procedura umożliwia utworzenie zdefiniowanej przez użytkownika etykiety niestandardowej.  

##### <a name="to-create-a-user-defined-software-label"></a>Aby utworzyć zdefiniowaną przez użytkownika etykietę oprogramowania  

1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.  

2.  W obszarze roboczym **Zasoby i zgodność** kliknij pozycję **Analiza zasobów**, a następnie kliknij pozycję **Katalog**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij polecenie **Utwórz etykietę oprogramowania**.  

4.  Na stronie **Ogólne** wprowadź nazwę nowej rodziny oprogramowania i, opcjonalnie, opis.  

    > [!NOTE]  
    >  Stan sprawdzania poprawności dla wszystkich nowych niestandardowych etykiet oprogramowania ma zawsze wartość **Zdefiniowane przez użytkownika**.  

5.  Sprawdź ustawienia na stronie **Podsumowanie** , a następnie kliknij przycisk **Dalej**.  

6.  Aby zamknąć kreatora, kliknij na stronie **Ukończenie** przycisk **Zamknij** .  

###  <a name="BKMK_HardwareRequirements"></a> Wymagania sprzętowe  
 Informacje o wymaganiach sprzętowych mogą pomóc w sprawdzeniu, czy komputery spełniają wymagania sprzętowe tytułów oprogramowania zanim zostaną wyznaczone w celu wdrożenia oprogramowania. Wiele wymagań sprzętowych jest wstępnie zdefiniowanych w katalogu analizy zasobów, a użytkownik może utworzyć dodatkowe informacje o wymaganiach sprzętowych, aby spełnić wymagania niestandardowe. Stan sprawdzania poprawności dla wszystkich wstępnie zdefiniowanych wymagań sprzętowych to zawsze **Zweryfikowane**, a zdefiniowane przez użytkownika informacje o wymaganiach sprzętowych dodane do katalogu analizy zasobów mają stan **Zdefiniowane przez użytkownika**.  

> [!IMPORTANT]  
>  Wymagania sprzętowe wyświetlane w konsoli programu Configuration Manager są pobierane z katalogu analizy zasobów na komputerze lokalnym i nie są oparte na informacjach dotyczących tytułów oprogramowania spisanych z klientów programu System Center 2012 Configuration Manager. Informacje dotyczące wymagań sprzętowych nie są aktualizowane w ramach procesu synchronizacji z usługą System Center Online. Możesz utworzyć zdefiniowane przez użytkownika wymagania sprzętowe dla spisanego oprogramowania, które nie ma skojarzonych wymagań sprzętowych.  

 Poniższa procedura umożliwia utworzenie zdefiniowanych przez użytkownika wymagań sprzętowych.  

##### <a name="to-create-a-user-defined-hardware-requirements"></a>Aby utworzyć wymagania sprzętowe zdefiniowane przez użytkownika  

1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.  

2.  W obszarze roboczym **Zasoby i zgodność** kliknij pozycję **Analiza zasobów**, a następnie kliknij pozycję **Wymagania sprzętowe**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij polecenie **Utwórz wymagania sprzętowe**.  

4.  Na stronie **Ogólne** podaj następujące informacje:  

    1.  **Tytuł oprogramowania**: Określa tytuł oprogramowania, dla której są skojarzone wymagania sprzętowe. Tytuł oprogramowania nie może istnieć w katalogu analizy zasobów.  

    2.  **Stan sprawdzania poprawności**: Wyświetla stan sprawdzania poprawności jako **zdefiniowane przez użytkownika** wymagań sprzętowych. Nie można modyfikować tego ustawienia.  

    3.  **Minimalna szybkość CPU (MHz)**: Określa minimalną szybkość procesora w megahercach (MHz) wymaganą przez tytuł oprogramowania.  

    4.  **Minimalna ilość pamięci RAM (KB)**: Określa minimalną ilość pamięci RAM w kilobajtach (KB) wymaganą przez tytuł oprogramowania.  

    5.  **Minimalna ilość miejsca (KB)**: Określa minimalną ilość wolnego miejsca, w artykule bazy wiedzy wymaganą przez tytuł oprogramowania.  

    6.  **Minimalny rozmiar dysku (KB)**: Określa minimalny rozmiar dysku twardego, w artykule bazy wiedzy wymaganą przez tytuł oprogramowania.  

     Kliknij przycisk **Dalej**.  

5.  Sprawdź ustawienia na stronie **Podsumowanie** , a następnie kliknij przycisk **Dalej**.  

6.  Aby zamknąć kreatora, kliknij na stronie **Ukończenie** przycisk **Zamknij** .  

###  <a name="BKMK_ModifyCategorization"></a> Modyfikowanie informacji o kategoryzacji spisanego oprogramowania  
 Dla wstępnie zdefiniowanego oprogramowania w katalogu analizy zasobów skonfigurowano określone informacje o kategoryzacji, takie jak nazwa produktu, dostawca, kategoria oprogramowania i rodzina oprogramowania. Jeśli wstępnie zdefiniowane informacje o kategoryzacji nie spełniają Twoich wymagań, możesz je zmodyfikować we właściwościach tytułu oprogramowania. Po zmodyfikowaniu informacji o kategoryzacji wstępnie zdefiniowanego oprogramowania jego stan sprawdzania poprawności zmienia się z **Zweryfikowane** na **Zdefiniowane przez użytkownika**.  

> [!IMPORTANT]  
>  Informacje o kategoryzacji można modyfikować tylko w lokacji najwyższego poziomu.  

 Poniższa procedura umożliwia zmodyfikowanie informacji o kategoryzacji spisanego oprogramowania.  

##### <a name="to-modify-the-categorizations-for-software-titles"></a>Aby zmodyfikować kategoryzacje tytułów oprogramowania  

1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.  

2.  W obszarze roboczym **Zasoby i zgodność** kliknij pozycję **Analiza zasobów**, a następnie kliknij pozycję **Spisane oprogramowanie**.  

3.  Wybierz jeden lub większą liczbę tytułów oprogramowania, dla których chcesz zmodyfikować kategoryzacje.  

4.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**.  

5.  Na karcie **Ogólne** możesz zmodyfikować następujące informacje o kategoryzacji:  

    -   **Nazwa produktu**: Określa nazwę spisanego tytułu oprogramowania.  

    -   **Dostawcy**: Określa nazwę dostawcy, który opracował spisany tytuł oprogramowania.  

    -   **Kategoria**: Określa kategorię oprogramowania, która jest aktualnie przypisana do spisanego tytułu oprogramowania.  

    -   **Rodzina**: Określa rodziny oprogramowania, który jest aktualnie przypisana do spisanego tytułu oprogramowania.  

6.  Kliknij przycisk **OK** , aby zapisać zmiany.  

 Poniższa procedura umożliwia przywrócenie pierwotnych informacji o kategoryzacji danego oprogramowania.  

### <a name="revert-categorization-information-to-original-settings-for-software"></a>Przywracanie pierwotnych ustawień informacji o kategoryzacji danego oprogramowania  
 Program Configuration Manager przechowuje informacje o kategorii uzyskane z programu System Center Online w bazie danych. Tych informacji nie można usunąć. Po zmodyfikowaniu informacji o kategoryzacji można przywrócić informacje o kategoryzacji pochodzące z programu System Center Online. Pierwotne ustawienia można przywrócić również w przypadku spisanego oprogramowania, które nie znajduje się w katalogu analizy zasobów.  

 Poniższa procedura umożliwia przywrócenie pierwotnych ustawień informacji o kategoryzacji.  

##### <a name="to-revert-categorization-information-to-original-settings"></a>Aby przywrócić pierwotne ustawienia informacji o kategoryzacji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.  

2.  W obszarze roboczym **Zasoby i zgodność** kliknij pozycję **Analiza zasobów**, a następnie kliknij pozycję **Spisane oprogramowanie**.  

3.  Wybierz jeden lub większą liczbę tytułów oprogramowania, dla których chcesz przywrócić pierwotne ustawienia. Przywrócenie jest możliwe tylko w przypadku oprogramowania o stanie **Zdefiniowane przez użytkownika** .  

    > [!TIP]  
    >  Kliknij kolumnę **Stan** , aby posortować według stanu sprawdzania poprawności. Sortowanie pozwala wyświetlić całe oprogramowanie według stanu sprawdzania poprawności i szybko zaznaczyć wiele pozycji, aby przywrócić ich pierwotne ustawienia.  

4.  Na karcie **Narzędzia główne** w grupie **Produkt** kliknij polecenie **Przywróć**.  

5.  Kliknij przycisk **Tak** , aby przywrócić pierwotne informacje o kategoryzacji danego oprogramowania.  

6.  Po przywróceniu informacji o kategoryzacji oprogramowania znajdującego się w katalogu analizy zasobów jego stan sprawdzania poprawności zostanie zmieniony z **Zdefiniowane przez użytkownika** na **Zweryfikowane**. Po przywróceniu oprogramowania, które nie znajduje się w katalogu, jego stan sprawdzania poprawności zostanie zmieniony z **Zdefiniowane przez użytkownika** na **Bez kategorii**.  

##  <a name="BKMK_RequestCatalogUpdate"></a> Żądanie aktualizacji katalogu dla tytułów oprogramowania bez kategorii  
 Informacje o tytule oprogramowania bez kategorii można przesłać do programu System Center Online w celu zbadania i kategoryzacji. Po przesłaniu tytułu oprogramowania bez kategorii, gdy istnieją co najmniej 4 żądania kategoryzacji tego samego tytułu oprogramowania pochodzące od innych klientów, pracownicy naukowo-badawczy zidentyfikują i skategoryzują tytuł oprogramowania, a następnie udostępnią informacje o kategoryzacji tego tytułu dla wszystkich klientów korzystających z usługi System Center Online. Firma Microsoft daje najwyższy priorytet tytułom oprogramowania, dla których istnieje najwięcej żądań kategoryzacji. Oprogramowanie niestandardowe i aplikacje biznesowe najprawdopodobniej nie zostaną skategoryzowane, dlatego najlepiej nie przesyłać tych tytułów oprogramowania do firmy Microsoft w celu kategoryzacji.  

 Podczas przesyłania informacji o tytule oprogramowania do programu System Center Online w celu kategoryzacji mają zastosowanie następujące warunki:  

-   Do programu System Center Online są przesyłane tylko podstawowe informacje o tytule oprogramowania. Przed przesłaniem informacji o tytule oprogramowania, które ma zostać skategoryzowane, można przejrzeć te informacje.  

-   Nigdy nie są przesyłane informacje o licencji oprogramowania.  

-   Każdy przekazany tytuł oprogramowania staje się publicznie dostępny w ramach katalogu programu System Center Online i może być pobierany przez innych klientów.  

-   Źródło tytułu oprogramowania nie jest przechowywane w katalogu programu System Center Online. Jednak tytułów aplikacji zawierających informacje poufne lub zastrzeżone nie należy przesyłać do kategoryzacji przez program System Center Online.  

> [!NOTE]  
>  Aby uzyskać więcej informacji dotyczących prywatności analizy zasobów, zobacz [bezpieczeństwo i prywatność analizy zasobów w programie System Center Configuration Manager](../../../../core/clients/manage/asset-intelligence/security-and-privacy-for-asset-intelligence.md).  

 Poniższa procedura umożliwia zażądanie kategoryzacji tytułu oprogramowania w katalogu analizy zasobów przez program System Center Online.  

#### <a name="to-request-a-catalog-update-for-uncategorized-software-titles"></a>Aby zażądać aktualizacji katalogu dla tytułów oprogramowania bez kategorii  

1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.  

2.  W obszarze roboczym **Zasoby i zgodność** kliknij pozycję **Analiza zasobów**, a następnie kliknij pozycję **Spisane oprogramowanie**.  

3.  Wybierz jedną lub wiele nazw produktów do przesłania do programu System Center Online w celu kategoryzacji. Tylko tytuły oprogramowania bez kategorii można przesyłać do programu System Center Online w celu kategoryzacji. Jeśli spisany tytuł oprogramowania został skategoryzowany przez administratora i, w wyniku tego, ma stan Zdefiniowane przez użytkownika, przed przesłaniem do programu System Center Online w celu kategoryzacji kliknij prawym przyciskiem myszy spisany tytuł oprogramowania, a następnie kliknij polecenie **Przywróć** , aby przywrócić tytuł oprogramowania do stanu **Bez kategorii** .  

    > [!NOTE]  
    >  Menedżer konfiguracji może przetwarzać maksymalnie 100 tytułów oprogramowania do kategoryzacji naraz. Jeśli wybierzesz więcej niż 100 tytułów oprogramowania, tylko pierwsze 100 tytułów zostanie przetworzonych. Aby skategoryzować pozostałe tytuły oprogramowania, należy je przesłać w partiach zawierających mniej niż 100 tytułów.  

    > [!TIP]  
    >  Kliknij kolumnę **Stan** , aby posortować według stanu sprawdzania poprawności. Pozwala to wyświetlić wszystkie nazwy produktów bez kategorii i szybko wybrać wiele pozycji, aby je przesłać w celu kategoryzacji.  

4.  Na karcie **Narzędzia główne** w grupie **Produkt** kliknij polecenie **Zażądaj aktualizacji katalogu**.  

5.  Zapoznaj się z komunikatem dotyczącym zachowania poufności informacji podczas przesyłania informacji do programu System Center Online w celu kategoryzacji. Kliknij pozycję **Szczegóły** , aby wyświetlić informacje, które zostaną przesłane do programu System Center Online.  

6.  Wybierz pozycję **Potwierdzam przeczytanie i zrozumienie tego komunikatu**, a następnie kliknij przycisk **OK** , aby zezwolić na przesłanie wybranych tytułów oprogramowania w celu kategoryzacji.  

7.  Sprawdź, czy stan nazw produktów spisanego oprogramowania przesłanych do programu System Center Online w celu kategoryzacji został zmieniony z **Bez kategorii** na **Oczekujące**.  

    > [!NOTE]  
    >  Oprogramowanie przesłane do programu System Center Online w celu kategoryzacji ma stan sprawdzania poprawności **Oczekujące** w centralnej lokacji administracyjnej, ale w podrzędnych lokacjach głównych jest nadal wyświetlany stan **Bez kategorii** .  

##  <a name="BKMK_ResolveSoftwareDetails"></a> Rozwiązywanie konfliktów dotyczących szczegółów oprogramowania  
 Po odebraniu z programu System Center Online zaktualizowanych szczegółów dotyczących kategoryzacji oprogramowania, które są sprzeczne z istniejącymi szczegółami oprogramowania, możesz wybrać sposób rozwiązania konfliktu. Oprogramowanie, w przypadku którego występuje konflikt, ma stan sprawdzania poprawności **Aktualizowalne**. Po rozwiązaniu konfliktu szczegółów oprogramowania w katalogu analizy zasobów są przechowywane informacje o kategoryzacji oprogramowania zgodne z określonym ustawieniem. Konflikt dotyczący szczegółów oprogramowania nie wystąpi ponownie dla tej samej wartości kategoryzacji oprogramowania, chyba że wartość w programie System Center Online ulegnie zmianie po rozwiązaniu konfliktu.  

 Poniższa procedura umożliwia rozwiązanie konfliktu szczegółów oprogramowania.  

#### <a name="to-resolve-a-software-details-conflict"></a>Aby rozwiązać konflikt szczegółów oprogramowania  

1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.  

2.  W obszarze roboczym **Zasoby i zgodność** kliknij pozycję **Analiza zasobów**, a następnie kliknij pozycję **Spisane oprogramowanie**.  

3.  Przejrzyj kolumnę **Stan** , aby znaleźć tytuły oprogramowania w stanie **Aktualizowalne** .  

4.  Wybierz tytuł oprogramowania, dla którego chcesz rozwiązać konflikt, a następnie na karcie **Narzędzia główne** w grupie **Produkt** kliknij polecenie **Rozwiąż konflikt**.  

5.  Przejrzyj następujące informacje:  

    -   **Wartości lokalnej**: Określa informacje o kategoryzacji oprogramowania w katalogu analizy zasobów powodujący konflikt z nowszej szczegółami kategoryzacji oprogramowania System Center Online.  

    -   **Pobrana wartość**: Określa nowy System Center Online informacje o kategoryzacji oprogramowania powodujące konflikt analizy zasobów katalogu informacje o kategoryzacji oprogramowania.  

6.  Wybierz jedno z następujących ustawień, aby rozwiązać konflikt szczegółów oprogramowania:  

    -   **Nie zmieniaj lokalnie edytowanej wartości informacji katalogu**: Rozwiązuje konflikt szczegółów oprogramowania przez zachowanie istniejące informacje o kategoryzacji oprogramowania katalogu analizy zasobów. Po wybraniu tego ustawienia stan tytułu oprogramowania zostanie zmieniony z **Aktualizowalne** na **Zdefiniowane przez użytkownika**.  

    -   **Zastąp lokalnie edytowaną wartość informacji katalogu pobrany System Center Online wartość**: Rozwiązuje konflikt szczegółów oprogramowania przez zastąpienie istniejącej informacje o kategoryzacji oprogramowania katalogu analizy zasobów z nowymi informacjami uzyskanymi z programu System Center Online. Po wybraniu tego ustawienia stan tytułu oprogramowania zostanie zmieniony z **Aktualizowalne** na **Zweryfikowane**.  

     Kliknij przycisk **OK** , aby zapisać rozwiązanie konfliktu.  
