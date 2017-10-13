---
title: "Wprowadzenie analizy zasobów | Dokumentacja firmy Microsoft"
description: "Wprowadzenie do analizy zasobów w programie System Center Configuration Manager."
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 0bdfdef5-390f-4099-8bde-de51d9a89175
caps.latest.revision: "7"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 879dc3f04f361af955afbc4db180d097073e8d41
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="introduction-to-asset-intelligence-in-system-center-configuration-manager"></a>Wprowadzenie do analizy zasobów w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Analiza zasobów w programie System Center Configuration Manager umożliwia spisu i zarządzanie użyciem licencji oprogramowania w całym przedsiębiorstwie za pomocą katalogu analizy zasobów. Wiele klas spisu sprzętu usługi instrumentacji zarządzania Windows (WMI) poszerza zakres zbieranych informacji dotyczących używanego sprzętu i oprogramowania. Ponad 60 raportów umożliwia zaprezentowanie tych informacji w formacie łatwym w użyciu. Wiele z tych raportów łączy się z bardziej szczegółowymi raportami, w których możesz znaleźć ogólne informacje, a następnie przejść do informacji bardziej szczegółowych. Możesz dodawać niestandardowe informacje do katalogu analizy zasobów, takie jak niestandardowe kategorie oprogramowania, rodziny oprogramowania, etykiety oprogramowania i wymagania dotyczące sprzętu. Możesz również nawiązać połączenie z usługą System Center Online, aby dynamicznie aktualizować katalog analizy zasobów przy użyciu najbardziej aktualnych dostępnych informacji. Klienci firmy Microsoft mogą uzgodnić użycie licencji na oprogramowanie przedsiębiorstwie z zakupionymi licencjami na oprogramowanie używane przez zaimportowanie informacji o licencji oprogramowania do bazy danych lokacji programu Configuration Manager.  

##  <a name="BKMK_AssetIntelligenceCatalog"></a> Katalog analizy zasobów  

 Katalog inteligencji zasobów programu Configuration Manager jest zbiorem tabel bazy danych przechowywanych w bazie danych lokacji, które zawierają informacje o kategoryzacji i identyfikacji ponad 300 000 tytułów oprogramowania i wersji. Te tabele bazy danych służą również do zarządzania wymaganiami sprzętowymi poszczególnych tytułów oprogramowania.  

 Katalog analizy zasobów zawiera informacje o licencjach na używane tytuły oprogramowania firmy Microsoft i innych firm. W katalogu analizy zasobów dostępny jest wstępnie zdefiniowany zbiór wymagań sprzętowych tytułów oprogramowania, a użytkownik może utworzyć dodatkowe informacje o wymaganiach sprzętowych, aby spełnić wymagania niestandardowe. Ponadto można dostosować informacje w katalogu analizy zasobów i przekazać informacje o tytułach oprogramowania do usługi System Center Online w celu kategoryzacji.  

 Aktualizacje katalogu analizy zasobów zawierające nowo wydane oprogramowanie są co pewien czas dostępne do pobrania w celu wykonania zbiorczych aktualizacji katalogu. Katalog może być również dynamicznie aktualizowany przy użyciu punktu synchronizacji analizy zasobów roli systemu lokacji.  

###  <a name="BKMK_SoftwareCategories"></a> Kategorie oprogramowania  
 Kategorie oprogramowania analizy zasobów służą do ogólnego kategoryzowania spisanych tytułów oprogramowania i są również używane jako ogólne grupy dla bardziej konkretnych rodzin oprogramowania. Na przykład kategorią oprogramowania mogą być firmy z branży elektroenergetycznej, a rodziną oprogramowania w ramach tej kategorii oprogramowania — ropa naftowa i gaz lub elektrownie wodne. W katalogu analizy zasobów jest wstępnie zdefiniowanych wiele kategorii oprogramowania. Można również utworzyć kategorie zdefiniowane przez użytkownika, aby lepiej zdefiniować spisane oprogramowanie. Stan weryfikacji dla wszystkich wstępnie zdefiniowanych kategorii oprogramowania to zawsze **Zweryfikowane**, a informacje o niestandardowych kategoriach oprogramowania dodane do katalogu analizy zasobów mają stan **Zdefiniowane przez użytkownika**. Aby uzyskać więcej informacji o sposobie zarządzania kategoriami oprogramowania, zobacz [Konfigurowanie analizy zasobów w programie System Center Configuration Manager](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md).  

> [!NOTE]  
>  Informacje o wstępnie zdefiniowanych kategoriach oprogramowania przechowywane w katalogu analizy zasobów są tylko do odczytu i nie można ich zmienić ani usunąć. Użytkownicy administracyjni mogą dodawać, modyfikować i usuwać kategorie oprogramowania zdefiniowane przez użytkownika.  

###  <a name="BKMK_SoftwareFamilies"></a> Rodziny oprogramowania  
 Rodziny oprogramowania analizy zasobów są używane do definiowania spisanych tytułów oprogramowania w ramach kategorii oprogramowania. W katalogu analizy zasobów jest wstępnie zdefiniowanych wiele rodzin oprogramowania. Można również utworzyć kategorie zdefiniowane przez użytkownika, aby lepiej zdefiniować spisane oprogramowanie. Stan weryfikacji dla wszystkich wstępnie zdefiniowanych rodzin oprogramowania to zawsze **Zweryfikowane**, a informacje o niestandardowych rodzinach oprogramowania dodane do katalogu analizy zasobów mają stan **Zdefiniowane przez użytkownika**. Aby uzyskać więcej informacji o sposobie zarządzania rodzinami oprogramowania, zobacz [Konfigurowanie analizy zasobów w programie System Center Configuration Manager](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md).  

> [!NOTE]  
>  Informacje o wstępnie zdefiniowanych rodzinach oprogramowania są tylko do odczytu i nie można ich zmienić. Użytkownicy administracyjni mogą dodawać, modyfikować i usuwać rodziny oprogramowania zdefiniowane przez użytkownika.  

###  <a name="BKMK_CustomLabels"></a> Etykiety oprogramowania  
 Niestandardowe etykiety oprogramowania analizy zasobów pozwalają tworzyć filtry służące do grupowania tytułów oprogramowania i wyświetlania ich w raportach analizy zasobów. Za pomocą etykiet oprogramowania można tworzyć zdefiniowane przez użytkownika grupy tytułów oprogramowania mających wspólny atrybut. Możesz na przykład utworzyć etykietę oprogramowania o nazwie „Shareware”, skojarzyć ją z tytułami oprogramowania typu shareware występującymi w spisie, a następnie uruchomić raport pokazujący wszystkie tytuły z etykietą oprogramowania „Shareware”. Etykiety oprogramowania nie są wstępnie zdefiniowane. Stan weryfikacji dla etykiet oprogramowania ma zawsze wartość **Zdefiniowane przez użytkownika**. Aby uzyskać więcej informacji o sposobie zarządzania etykietami oprogramowania, zobacz [Konfigurowanie analizy zasobów w programie System Center Configuration Manager](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md).  

###  <a name="BKMK_HardwareRequirements"></a> Wymagania sprzętowe  
 Informacje o wymaganiach sprzętowych umożliwiają sprawdzenie, czy komputery spełniają wymagania sprzętowe tytułów oprogramowania zanim zostaną wyznaczone w celu wdrożenia oprogramowania. Wymaganiami sprzętowymi tytułów oprogramowania można zarządzać w obszarze roboczym **Zasoby i zgodność** w węźle **Wymagania sprzętowe** w węźle **Analiza zasobów** . Wiele wymagań sprzętowych jest wstępnie zdefiniowanych w katalogu analizy zasobów, a użytkownik może utworzyć dodatkowe informacje o wymaganiach sprzętowych, aby spełnić wymagania niestandardowe. Stan weryfikacji dla wszystkich wstępnie zdefiniowanych wymagań sprzętowych to zawsze **Zweryfikowane**, a zdefiniowane przez użytkownika informacje o wymaganiach sprzętowych dodane do katalogu analizy zasobów mają stan **Zdefiniowane przez użytkownika**. Aby uzyskać więcej informacji o sposobie zarządzania wymaganiami sprzętowymi, zobacz [Konfigurowanie analizy zasobów w programie System Center Configuration Manager](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md).  

> [!NOTE]  
>  Wymagania sprzętowe wyświetlane w konsoli programu Configuration Manager są pobierane z katalogu analizy zasobów i nie są oparte na informacjach dotyczących tytułów oprogramowania spisanych z klientów programu System Center 2012 Configuration Manager. Informacje dotyczące wymagań sprzętowych nie są aktualizowane w ramach procesu synchronizacji z usługą System Center Online. Możesz utworzyć zdefiniowane przez użytkownika wymagania sprzętowe dla spisanego oprogramowania, które nie ma skojarzonych wymagań sprzętowych.  

 Domyślnie dla poszczególnych wymagań sprzętowych na liście są wyświetlane następujące informacje:  

-   **Tytuł oprogramowania**: Określa tytuł oprogramowania skojarzony z wymaganiami sprzętowymi.  

-   **Minimalna szybkość CPU (MHz)**: Określa minimalną szybkość procesora w megahercach (MHz) wymaganą przez tytuł oprogramowania.  

-   **Minimalna ilość pamięci RAM (KB)**: Określa minimalną ilość pamięci RAM w kilobajtach (KB) wymaganą przez tytuł oprogramowania.  

-   **Minimalna ilość miejsca (KB)**: Określa minimalną wolnego miejsca, w artykule bazy wiedzy wymaganą przez tytuł oprogramowania.  

-   **Minimalny rozmiar dysku (KB)**: Określa minimalny rozmiar dysku twardego, w artykule bazy wiedzy wymaganą przez tytuł oprogramowania.  

-   **Stan sprawdzania poprawności**: Określa stan weryfikacji wymagań sprzętowych.  

 Wstępnie zdefiniowane wymagania sprzętowe przechowywane w katalogu analizy zasobów są tylko do odczytu i nie można ich usunąć.  Użytkownicy administracyjni mogą dodawać, modyfikować lub usuwać wymagania sprzętowe zdefiniowane przez użytkownika dla tytułów oprogramowania, które nie są przechowywane w katalogu analizy zasobów.  

##  <a name="BKMK_InventoriedSoftwareTitles"></a> Spisane tytuły oprogramowania  
 Informacje o spisanych tytułach oprogramowania można wyświetlić w obszarze roboczym **Zasoby i zgodność** w węźle **Spisane oprogramowanie** w węźle **Analiza zasobów** . Agent klienta spisu sprzętu zbiera informacje spisanego oprogramowania z klientów programu Configuration Manager według tytułów oprogramowania, które są przechowywane w katalogu analizy zasobów.  

> [!WARNING]  
>  Agent klienta spisu sprzętu zbiera dane spisu w oparciu o klasy raportowania spisu sprzętu analizy zasobów włączone przez użytkownika. Aby uzyskać więcej informacji o sposobie włączania raportowania klas, zobacz [Konfigurowanie analizy zasobów w programie System Center Configuration Manager](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md).  

 Domyślnie dla poszczególnych spisanych tytułów oprogramowania są wyświetlane następujące informacje:  

-   **Nazwa**: Określa nazwę spisanego tytułu oprogramowania.  

-   **Dostawcy**: Określa nazwę dostawcy, który opracował spisany tytuł oprogramowania.  

-   **Wersja**: Określa wersję produktu spisanego tytułu oprogramowania.  

-   **Kategoria**: Określa kategorię oprogramowania, która jest aktualnie przypisana do spisanego tytułu oprogramowania.  

-   **Rodzina**: Określa rodziny oprogramowania, który jest aktualnie przypisana do spisanego tytułu oprogramowania.  

-   **Etykieta** [**1**, **2**, i **3**]: Określa etykiety niestandardowe, które są skojarzone z tytułu oprogramowania. Do spisanych tytułów oprogramowania można przypisać do trzech etykiet niestandardowych.  

-   **Liczba**: Określa liczbę klientów programu Configuration Manager, na których został spisany tytuł oprogramowania.  

-   **Stan**: Określa stan weryfikacji spisanego tytułu oprogramowania.  

> [!NOTE]  
>  Można zmienić informacje dotyczące kategoryzacji (nazwa produktu, dostawca, kategoria oprogramowania i rodzina oprogramowania) spisanego oprogramowania tylko w lokacji najwyższego poziomu w hierarchii. Po zmodyfikowaniu informacji o kategoryzacji wstępnie zdefiniowanego oprogramowania jego stan weryfikacji zmienia się ze **Zweryfikowane** na **Zdefiniowane przez użytkownika**.  

##  <a name="AssetIntelligenceSycnronizationPoint"></a> Punkt synchronizacji analizy zasobów  
 Punkt synchronizacji analizy zasobów jest rolą systemu lokacji programu Configuration Manager używane do łączenia się z programem System Center Online (przy użyciu portu TCP 443) aby zarządzać informacji o katalogu analizy zasobów dynamicznych aktualizacji. Tę rolę lokacji można zainstalować tylko w lokacji najwyższego poziomu w hierarchii. Wszystkie niestandardowe w katalogu analizy zasobów należy skonfigurować przy użyciu konsoli programu Configuration Manager połączonej z lokacją najwyższego poziomu. Mimo że wszystkie aktualizacje należy skonfigurować w lokacji najwyższego poziomu, informacje w katalogu analizy zasobów są replikowane do innych lokacji w hierarchii. Rola lokacji punktu synchronizacji analizy zasobów umożliwia zażądanie synchronizacji katalogu na żądanie z usługą System Center Online lub zaplanowanie automatycznej synchronizacji katalogu. Oprócz pobierania nowych informacji z katalogu analizy zasobów punkt synchronizacji analizy zasobów umożliwia przekazywanie niestandardowych informacji o tytułach oprogramowania do usługi System Center Online w celu kategoryzacji. Wszystkie tytuły oprogramowania przekazane do usługi System Center Online w celu kategoryzacji są traktowane przez firmę Microsoft jako informacje publiczne. Dlatego należy się upewnić, że niestandardowe tytuły nie zawierają informacji poufnych lub zastrzeżonych.  

> [!NOTE]  
>  Po przesłaniu tytułu oprogramowania bez kategorii, gdy istnieją co najmniej 4 żądania kategoryzacji tego samego tytułu oprogramowania pochodzące od klientów, pracownicy naukowo-badawczy usługi System Center Online zidentyfikują i skategoryzują tytuł oprogramowania, a następnie udostępnią informacje o kategoryzacji tego tytułu dla wszystkich klientów korzystających z usługi online. Tytuły oprogramowania, dla których istnieje najwięcej żądań kategoryzacji, otrzymują najwyższy priorytet kategoryzacji. Oprogramowanie niestandardowe i aplikacje biznesowe najprawdopodobniej nie zostaną skategoryzowane, dlatego najlepiej nie przesyłać tych tytułów oprogramowania do firmy Microsoft w celu kategoryzacji.  

> [!NOTE]  
>  Rola systemu punktu synchronizacji analizy zasobów jest wymagana do nawiązania połączenia z usługą System Center Online. Aby uzyskać informacje o sposobie instalowania punktu synchronizacji analizy zasobów, zobacz [Konfigurowanie analizy zasobów w programie System Center Configuration Manager](../../../../core/clients/manage/asset-intelligence/configuring-asset-intelligence.md).  

##  <a name="BKMK_AssetIntelligenceHomePage"></a> Strona główna Analiza zasobów  
 **Analizy zasobów** w węźle **zasoby i zgodność** obszaru roboczego jest stroną główną analizy zasobów w programie Configuration Manager. Na stronie głównej **Analiza zasobów** jest wyświetlany widok pulpitu nawigacyjnego podsumowania zawierający informacje o katalogu analizy zasobów.  

> [!NOTE]  
>  Strona główna **Analiza zasobów** nie jest aktualizowana automatycznie, gdy jest wyświetlana.  

 Strona główna **Analiza zasobów** zawiera następujące sekcje:  

-   **Synchronizacja katalogu**: Zawiera informacje dotyczące tego, czy analiza zasobów jest włączona i bieżący stan punktu synchronizacji analizy zasobów. Ta sekcja zawiera również informacje o harmonogramie synchronizacji, zaimportowaniu zestawienia licencji klienta, czasie następnej zaplanowanej aktualizacji oraz liczbie zmian, które wystąpiły po zainstalowaniu systemu lokacji punktu synchronizacji analizy zasobów.  

    > [!NOTE]  
    >  Sekcja synchronizacji katalogu analizy zasobów jest wyświetlana na stronie **Analiza zasobów** tylko wtedy, gdy zainstalowano rolę systemu lokacji punktu synchronizacji analizy zasobów.  

-   **Stan spisanego oprogramowania**: Zawiera ilość i odsetek spisanego oprogramowania, kategorie oprogramowania i rodziny oprogramowania, które są identyfikowane przez firmę Microsoft, zidentyfikowane przez administratora, będące w toku identyfikacji online lub niezidentyfikowane i nieoczekujące. Informacje wyświetlane w formacie tabeli zawierają liczbę elementów w każdej kategorii, natomiast informacje wyświetlane na wykresie przedstawiają odsetek dla każdej z nich.  

##  <a name="BKMK_AssetIntelligenceReports"></a> Raporty analizy zasobów  
 Raporty analizy zasobów znajdują się w konsoli programu Configuration Manager w **monitorowanie** w folderze analiza zasobów w obszarze roboczym **raportowania** węzła. Raporty zapewniają informacje dotyczące sprzętu, zarządzania licencjami oraz oprogramowania. Aby uzyskać więcej informacji o raportach w programie Configuration Manager, zobacz [raportowania w programie System Center Configuration Manager](../../../../core/servers/manage/reporting.md).  

> [!NOTE]  
>  Informacje o liczbie zainstalowanych tytułów oprogramowania i licencji wyświetlanych w raportach analizy zasobów mogą różnić się od rzeczywistej liczby zainstalowanych tytułów oprogramowania i licencji używanych w środowisku. Ta różnica wynika ze złożonych zależności i ograniczeń dotyczących tworzenia spisu informacji o licencjach na oprogramowanie dla tytułów oprogramowania zainstalowanych w środowiskach przedsiębiorstw. Raportów analizy zasobów nie należy używać jako jedynego źródła informacji podczas określania zgodności zakupionych licencji na oprogramowanie.  

###  <a name="BKMK_HardwareReports"></a> Raporty analizy zasobów dotyczące sprzętu  
 Raporty analizy zasobów dotyczące sprzętu zawierają informacje o zasobach sprzętowych w organizacji. Dzięki użyciu informacji dotyczących spisu sprzętu, takich jak m.in. szybkość, pamięć, urządzenia peryferyjne, raporty analizy zasobów dotyczące sprzętu umożliwiają prezentowanie informacji dotyczących urządzeń USB, sprzętu, który musi zostać uaktualniony, a nawet komputerów, które nie są gotowe do zastosowania określonego uaktualnienia oprogramowania.  

> [!NOTE]  
>  Niektóre dane użytkowników w raportach analizy zasobów dotyczących sprzętu są zbierane z dziennika zdarzeń zabezpieczeń systemu. W celu uzyskania większej dokładności raportów zaleca się czyszczenie tego dziennika po ponownym przypisaniu komputera do nowego użytkownika.  

###  <a name="BKMK_LicenseManagementReports"></a> Raporty analizy zasobów dotyczące zarządzania licencjami  
 Raporty analizy zasobów dotyczące zarządzania licencjami zawierają dane dotyczące licencji, które są używane. Raport Księga licencji zawiera listę zainstalowanych aplikacji firmy Microsoft w formacie zgodnym z zestawieniem licencji firmy Microsoft (MLS). Jest to wygodny sposób uzgadniania zakupionych licencji z używanymi licencjami. Inne raporty zarządzania licencjami zawierają informacje o komputerach działających jako serwery z uruchomioną usługą zarządzania kluczami (KMS) dla statystyk aktywacji systemu operacyjnego.  

> [!IMPORTANT]  
>  Kilka raportów analizy zasobów dotyczących zarządzania licencjami zawiera informacje na temat funkcji usługi zarządzania kluczami — metody administrowania licencjonowaniem zbiorowym. Jeśli serwer usługi KMS nie został zaimplementowany, niektóre raporty mogą nie zwracać żadnych danych. Aby uzyskać więcej informacji o usłudze KMS, wyszukaj termin KMS w witrynie [Microsoft TechNet](http://go.microsoft.com/fwlink/?linkid=3225).  

###  <a name="BKMK_SoftwareReports"></a> Raporty analizy zasobów dotyczące oprogramowania  
 Raporty analizy zasobów dotyczące oprogramowania zawierają informacje dotyczące rodziny oprogramowania, kategorii i określonych tytułów oprogramowania, które są zainstalowane na komputerach w organizacji. Raporty dotyczące oprogramowania zawierają m.in. informacje o obiektach pomocniczych przeglądarki oraz oprogramowaniu, które jest uruchamiane automatycznie. Te raporty mogą służyć do identyfikowania programów z reklamami, programów szpiegujących lub innego złośliwego oprogramowania oraz identyfikacji nadmiarowego oprogramowania w celu usprawnienia zakupów oprogramowania i pomocy technicznej.  

###  <a name="BKMK_SoftwareIdTagReports"></a> Raporty analizy zasobów dotyczące tagów identyfikacji oprogramowania  
 Raporty analizy zasobów dotyczące tagów identyfikacji oprogramowania zapewniają informacje o oprogramowaniu zawierającym tagi identyfikacji oprogramowania zgodne z normą ISO/IEC 19770-2. Tagi identyfikacji oprogramowania zapewniają autorytatywne informacje, które służą do identyfikowania zainstalowanego oprogramowania. Po włączeniu klasy raportowania spisu sprzętu analizy zasobów SMS_SoftwareTag programu Configuration Manager gromadzi informacje o oprogramowaniu z tagami identyfikacji oprogramowania. Następujące raporty zawierają informacje o oprogramowaniu:  

-   **Oprogramowanie 14A - Search for tagiem identyfikacji oprogramowania z włączonym**: Ten raport przedstawia liczbę zainstalowanych programów z włączonym tagiem identyfikacji oprogramowania.  

-   **Oprogramowanie 14B - komputery z określonym znacznikiem identyfikacji zainstalowanymi włączonym**: Ten raport zawiera listę wszystkich komputerów, na których zainstalowano oprogramowanie z włączonym tagiem identyfikacji oprogramowania określonych.  

-   **Oprogramowanie 14C - identyfikator tagu włączone oprogramowanie zainstalowane na określonym komputerze**: Ten raport zawiera listę całego oprogramowania z określonym znacznikiem identyfikacji włączone na określonym komputerze.  

###  <a name="BKMK_ReportingLImitations"></a> Ograniczenia dotyczące raportowania analizy zasobów  
 Raporty analizy zasobów zapewniają dużą ilość informacji o zainstalowanych tytułach oprogramowania i zakupionych licencjach na oprogramowanie, które są używane. Jednak nie należy używać tych informacji jako jedynego źródła służącego do określania zgodności zakupionych licencji na oprogramowanie.  

####  <a name="BKMK_ExampleDependencies"></a> Przykładowe zależności  
 Liczba zainstalowanych tytułów oprogramowania i licencji wyświetlana w raportach analizy zasobów może różnić się od rzeczywistej liczby będącej obecnie w użyciu. Ta różnica wynika ze złożonych zależności dotyczących tworzenia spisu informacji o licencjach na oprogramowanie dla tytułów oprogramowania będących w użyciu w środowiskach przedsiębiorstw. Poniższe przykłady pokazują zależności występujące podczas tworzenia spisu oprogramowania zainstalowanego w przedsiębiorstwie za pomocą analizy zasobów, które mogą mieć wpływ na dokładność raportów analizy zasobów:  

 **Zależności spisu sprzętu klienta**  
 Raporty dotyczące oprogramowania zainstalowane analizy zasobów są oparte na danych zbieranych z klientów programu Configuration Manager przez rozszerzenie spisu sprzętu, aby włączyć raportowanie analizy zasobów. Ze względu na tę zależność od raportowania spisu sprzętu raporty analizy zasobów uwzględniają dane tylko z klientów programu Configuration Manager, którzy pomyślnie zakończyli procesy spisu sprzętu z wymagane klasy raportowania WMI analizy zasobów włączone. Ponadto ponieważ klienci programu Configuration Manager wykonują procesy spisu sprzętu zgodnie z harmonogramem zdefiniowanym przez użytkownika administracyjnego, dane raportów, które ma wpływ na dokładność raportów analizy zasobów może wystąpić opóźnienie. Na przykład spisany tytuł licencjonowanego oprogramowania może zostać odinstalowany po pomyślnym zakończeniu cyklu spisu sprzętu przez klienta. Jednak tytuł oprogramowania jest wyświetlany jako zainstalowany w raportach analizy zasobów do klienta następnego zaplanowanego spisu sprzętu cyklu raportowania.  

 **Zależności pakietów oprogramowania**  
 Ponieważ raporty analizy zasobów są oparte na danych tytuł zainstalowanego oprogramowania, które są zbierane za pomocą standardowe procesy spisu sprzętu klienta programu Configuration Manager, niektóre dane tytuł oprogramowania mogą nie być poprawnie zbierane. Na przykład instalacje oprogramowania, które nie są zgodne ze standardowymi procesami instalacji, lub instalacje oprogramowania, które zostały zmienione przed instalacją, mogą powodować niedokładne raportowanie analizy zasobów.  

####  <a name="BKMK_LegalLimitations"></a> Ograniczenia prawne  
 Informacje wyświetlane w raportach analizy zasobów podlegają wielu ograniczeniom i nie stanowią porady prawnej, księgowej lub innej porady specjalistycznej. Informacje dostarczane przez raporty analizy zasobów mają charakter wyłącznie informacyjny i nie mogą być używane jako jedyne źródło informacji do określania zgodności użycia licencji na oprogramowanie.  

 Poniżej przedstawiono przykłady ograniczeń występujących podczas tworzenia spisu zainstalowanego oprogramowania i użycia licencji w przedsiębiorstwie za pomocą analizy zasobów, które mogą mieć wpływ na dokładność raportów analizy zasobów:  

 **Ograniczenia dotyczące liczby użyć licencji firmy Microsoft**  
 -   Liczba zakupionych licencji na oprogramowanie firmy Microsoft jest określana na podstawie informacji podanych przez administratorów i powinna być dokładnie sprawdzona w celu upewnienia się, że podano prawidłową liczbę licencji na oprogramowanie.  

-   Zgłoszona liczba licencji na oprogramowanie firmy Microsoft uwzględnia tylko informacje dotyczące licencji na oprogramowanie firmy Microsoft zakupionych za pośrednictwem programów licencjonowania zbiorowego i nie obejmuje informacji o licencjach na oprogramowanie zakupione w ramach sprzedaży detalicznej, OEM lub innych kanałów sprzedaży licencji na oprogramowanie.  

-   Licencje na oprogramowanie zakupione w ciągu ostatnich 45 dni mogą nie zostać uwzględnione w ilości zgłoszonych licencji na oprogramowanie firmy Microsoft ze względu na wymagania i harmonogramy raportowania przez sprzedawców.  

-   Transfery licencji na oprogramowanie wynikające z fuzji lub przejęć firm mogą nie zostać odzwierciedlone w liczbie licencji na oprogramowanie firmy Microsoft.  

-   Niestandardowe warunki i postanowienia w umowie licencjonowania zbiorowego firmy Microsoft (MVLS) mogą wpłynąć na liczbę zgłaszanych licencji na oprogramowanie i dlatego mogą wymagać dodatkowego sprawdzenia przez przedstawiciela firmy Microsoft.  

 **Ograniczenia dotyczące liczby zainstalowanych tytułów oprogramowania**  
 Klienci programu Configuration Manager muszą pomyślnie ukończyć cykle raportów analizy zasobów precyzyjnie liczby zainstalowanych tytułów oprogramowania i raportowania spisu sprzętu. Ponadto mogą wystąpić opóźnienia między instalacją a dezinstalacją tytułu licencjonowanego oprogramowania po pomyślnym zakończeniu cyklu raportowania spisu sprzętu, który nie zostanie uwzględniony w raportach analizy zasobów do czasu zgłoszenia następnego zaplanowanego spisu sprzętu przez klienta.  

 **Ograniczenia dotyczące uzgadniania licencji**  
 Uzgadnianie liczby zainstalowanych tytułów oprogramowania i liczby zakupionych licencji na oprogramowanie jest obliczane przez porównanie liczby licencji określonej przez administratora i liczby zainstalowanych tytułów oprogramowania zebrane z spisy sprzętu klientów programu Configuration Manager na podstawie harmonogramu ustawionych przez administratora. To porównanie nie reprezentuje ostatecznego określenia stanu licencji przez firmę Microsoft. Rzeczywisty stan licencji zależy od licencji na konkretny tytuł oprogramowania i praw użycia przyznanych przez postanowienia licencyjne.  

##  <a name="BKMK_ValidationStates"></a> Stany weryfikacji analizy zasobów  
 Stan weryfikacji analizy zasobów reprezentuje stan weryfikacji źródła i bieżący stan weryfikacji informacji z katalogu analizy zasobów. W poniższej tabeli przedstawiono możliwe stany weryfikacji analizy zasobów oraz czynności wykonywane przez administratorów, które mogą być ich przyczyną.  

|**Stan**|**Definicja**|**Czynności wykonywane przez administratora**|**Komentarz**|  
|---------------|--------------------|------------------------------|-----------------|  
|**Zweryfikowane**|Element katalogu został zdefiniowany przez pracowników naukowo-badawczych usługi System Center Online.|Brak.|Najlepszy stan.|  
|**Zdefiniowane przez użytkownika**|Element katalogu nie został zdefiniowany przez pracowników naukowo-badawczych usługi System Center Online.|Niestandardowe informacje w katalogu lokalnym.|Ten stan jest wyświetlany w raportach analizy zasobów.|  
|**Oczekiwanie**|Element katalogu nie został zdefiniowany przez pracowników naukowo-badawczych usługi System Center Online, ale element został przesłany do usługi System Center Online w celu kategoryzacji.|Zażądano kategoryzacji w usłudze System Center Online.|Element katalogu pozostaje w tym stanie do momentu skategoryzowania elementu przez pracowników naukowo-badawczych usługi System Center Online i synchronizacji katalogu analizy zasobów.|  
|**Można aktualizować**|Obiekty zdefiniowane przez użytkownika katalogu zostały skategoryzowane inaczej przez usługę System Center Online podczas kolejnej synchronizacji katalogu.|Dostosowano lokalny katalog analizy zasobów w celu skategoryzowania elementu jako zdefiniowany przez użytkownika.|Akcja Rozwiąż konflikt umożliwia określenie, czy mają zostać użyte nowe informacje o kategoryzacji czy poprzednia wartość zdefiniowana przez użytkownika. Aby uzyskać więcej informacji o sposobach rozwiązywania konfliktów, zobacz [operacje związane z analizą zasobów w programie System Center Configuration Manager](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md).|  
|**Bez kategorii**|Element katalogu nie został zdefiniowany przez pracowników naukowo-badawczych usługi System Center Online, element nie został przesłany do usługi System Center Online w celu kategoryzacji, a administrator nie przypisał wartości kategorii zdefiniowanej przez użytkownika.|Brak.|Zażądaj kategoryzacji lub dostosuj informacje w katalogu lokalnym.<br /><br /> Aby uzyskać więcej informacji dotyczących żądania kategoryzacji, zobacz [operacje związane z analizą zasobów w programie System Center Configuration Manager](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md).<br /><br /> Aby uzyskać więcej informacji na temat sposobów zmieniania kategorii tytułu oprogramowania, zobacz [operacje związane z analizą zasobów w programie System Center Configuration Manager](../../../../core/clients/manage/asset-intelligence/operations-for-asset-intelligence.md).|  

> [!NOTE]  
>  Elementy katalogu przesłane do programu System Center Online w celu kategoryzacji mają stan weryfikacji **Oczekujące** w centralnej lokacji administracyjnej, ale w podrzędnych lokacjach głównych jest nadal wyświetlany stan **Bez kategorii** .  

> [!NOTE]  
>  Po rozwiązaniu konfliktu kategoryzacji element nie jest weryfikowany ponownie jako powodujący konflikt, jeśli w późniejszych aktualizacjach nie zostaną wprowadzone nowe informacje o elemencie.  

 Przykłady tego, kiedy stan sprawdzania poprawności może przejście ze stanu jednego do drugiego, zobacz [przykład przejść stanu weryfikacji dla analizy zasobów w programie System Center Configuration Manager](../../../../core/clients/manage/asset-intelligence/example-validation-state-transitions-for-asset-intelligence.md).  
