---
title: Importowanie danych do firmy Microsoft Intune
titleSuffix: Configuration Manager
description: 
keywords: 
author: dougeby
manager: dougeby
ms.date: 12/05/2017
ms.topic: article
ms.prod: configmgr-hybrid
ms.service: 
ms.technology: 
ms.assetid: b552391d-abc0-48a2-a429-93605a13a66a
ms.openlocfilehash: d42a5fd64b5baead8ef87d8c08a99ec659f94633
ms.sourcegitcommit: 8c6e9355846ff6a73c534c079e3cdae09cf13c45
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/06/2017
---
# <a name="import-configuration-manager-data-to-microsoft-intune"></a>Importuj dane programu Configuration Manager w usłudze Microsoft Intune 

*Dotyczy: Program System Center Configuration Manager (Current Branch)*    

Zalecane pierwszego etapu w procesie [migracji hybrydowego zarządzania urządzeniami Przenośnymi użytkowników i urządzeń do autonomicznej usługi Intune](migrate-hybridmdm-to-intunesa.md) w konfiguracji opartej tylko na chmurze jest użycie narzędzia odbierający dane usługi Intune. Jeśli chcesz, możesz pominąć tej fazy i przenieść na [przygotować usługę Intune do migracji użytkownika](migrate-prepare-intune.md) fazy. Jednak to narzędzie wykonuje następujące funkcje, które mogą pomóc zaoszczędzić dużo czasu w następnej fazy: 
1.  Zbiera dane dotyczące obiekty, które należy wybrać z hierarchii programu Configuration Manager. 
2.  Zawiera szczegółowe informacje o obiektach, które można wybrać importowania i dowiedzieć się, dlaczego nie można zaimportować niektórych obiektów.
3.  Importuje wybrane obiekty w dzierżawcy usługi Microsoft Intune. 

Narzędzie odbierający dane nie zmienia środowiska programu Configuration Manager w jakikolwiek sposób i w związku z tym można importować obiekty w usłudze Intune i zweryfikować, czy wszystko działa zgodnie z oczekiwaniami bez ryzyko pozostawienia urządzenia hybrydowego zarządzania urządzeniami Przenośnymi w stanie niezarządzanym. 

## <a name="what-objects-can-this-tool-import"></a>Jakie obiekty można zaimportować tego narzędzia?
Narzędzia importu można zbierać informacje o następujących typach obiektów w programie Configuration Manager i zawiera informacje o można importować obiekty zbierane: 
- Elementy konfiguracji
- Profile certyfikatów
- Profile poczty e-mail
- Profile sieci VPN
- Profile sieci Wi-Fi
- Zasady zgodności
- Aplikacje
- Wdrożenia

> [!Note]    
> Importowanie wdrożeń przydaje się tylko do innych obiektów, które są importowane. Na przykład po zaimportowaniu profili sieci VPN i wdrożeń tylko można zaimportować wdrożenia profilów sieci VPN, które można wybrać. Wdrożeń w usłudze Intune są nazywane przypisania. Jeśli chcesz zaimportować wdrożenia dla obiekt wcześniej importowany, należy ponownie zaimportować ten obiekt lub ręcznie utworzyć przypisania w usłudze Intune na platformie Azure. Na przykład po zaimportowaniu profili sieci VPN i wdrożenia nie należy ponownie uruchomić narzędzie i wybierz profile sieci VPN i wdrożeń lub ręcznie utworzyć przypisania w usłudze Intune na platformie Azure.  Jeśli uruchomisz narzędzie zduplikowane obiekty może zostać utworzony, można usunąć później w usłudze Intune na platformie Azure.  

> [!Important]    
> Jeśli kolekcję dla wdrożenia jest oparta na grupy usługi Active Directory, który został zreplikowany do usługi Azure Active Directory (AAD), narzędzie automatycznie docelowe migrowanych obiektów do grup, w przypadku wybrania odpowiedniego wdrożenia podczas uruchamiania narzędzia. W przypadku bardziej złożonych kolekcji lub kolekcji członkostwa bezpośredniego, należy ręcznie utwórz je ponownie w usłudze AAD i ręcznie docelowego obiektu przypisania do nich w usłudze Intune na platformie Azure.


## <a name="things-to-know-before-you-run-the-tool"></a>Co należy wiedzieć przed uruchomieniem narzędzia
- Uruchamianie narzędzia nie zmieni środowiska programu Configuration Manager w dowolny sposób.
- Zaleca się przetestowanie procesu importowania danych za pomocą dzierżawy w wersji próbnej. Następnie po upewnieniu się, że oczekiwane zostały zaimportowane dane, można przejść przez ten sam proces z dzierżawą usługi Intune w środowisku produkcyjnym.
- Dane mają na celu importować tylko dane programu Configuration Manager jeden raz. Go nie zachować informacje o obiektów w programie Configuration Manager lub usługi Intune. Jednak po uruchomieniu importera ponownie na tym samym komputerze jako przed, jego informuje o obiekty, które wcześniej zaimportowana. Narzędzie nie będzie wiedzieć, czy obiekt nadal istnieje w usłudze Intune, czy obiekt został zmieniony. Jeśli więcej niż raz importowanie danych do usługi Intune, może to spowodować z zduplikowane obiekty.
- Nie wszystkie ustawienia profilu można zaimportować. Na przykład nie można zaimportować tryb kiosku lub ustawienia PFX. 
- Jeśli zasady programu Configuration Manager przy użyciu ustawień, które nie mają zastosowania do wybranej platformy, narzędzie może ignorować te ustawienia podczas importowania. Ignorowanie pomoc ustawienia, aby upewnić się, że zasady można zaimportować i obsługiwane przez usługę Intune. 
- Narzędzie będzie podejmować próby zapewniają Przyczyna Dlaczego nie można zaimportować obiektu. W niektórych przypadkach przed zaimportowaniem obiektów do usługi Intune, możesz przejść do konsoli programu Configuration Manager, należy rozwiązać ten problem, uruchom Menedżera konfiguracji odnajdywania obiektów Skanuj ponownie, a następnie zaimportowanie obiektów. Czasami może być konieczne, lub może być, aby ponownie utworzyć te obiekty ręcznie w usłudze Intune.
- Brak niektórych profilów, które są zależne od innych obiektów. Jeśli chcesz zaimportować profil, który jest zależny od innego obiektu, takich jak profil poczty e-mail, która jest zależna od certyfikatu, należy zaimportować zarówno do obiektów w tym samym czasie, jeśli wcześniej zaimportowano innego obiektu z tego samego komputera z tego samego użytkownika.  
- Po uruchomieniu narzędzia może być konieczne wykonanie dodatkowych czynności ręcznie. Na przykład przeznaczonych dla aplikacji i zasad w grupach usługi AAD. 

## <a name="prerequisites"></a>Wymagania wstępne
- Configuration Manager w wersji 1610 lub nowszej.-zaleca się określenie lokacji najwyższego poziomu i uruchomić narzędzie z użytkownikiem, który ma dostęp do wszystkich obiektów w hierarchii lokacji. Narzędzie wykrywa tylko obiekty, które są dostępne przez użytkownika z uruchomionym narzędziem. 
- Administrator globalny musi uruchomić narzędzie odbierający dane z następującym po raz pierwszy ***intunedataimporter.exe - GlobalConsent*** parametru. Następnie narzędzie można uruchomić administratora globalnego lub administratora usługi Intune.  


<!-- ## Objects that cannot be imported
There are some Configuration Manager objects that the importer tool cannot import to Intune. You must manually create these objects in Intune. 
- Collections based on direct membership or that are based on a query. The only collections that are imported are based on a single AD group. For all other collections, you must create the assignment in Intune and add the assignment to the appropriate objects. 
- Profiles <list what we cannot import>
- Policies <??>
- Etc.
-->

## <a name="download-the-data-importer-tool"></a>Pobierz narzędzie odbierający dane
Narzędzie importera danych jest dostępne do pobrania z repozytorium ConfigMgrTools/Intune--odbierający dane w usłudze GitHub. Użyj poniższej procedury, aby pobrać to narzędzie.

1. Przejdź do [zwalnia Intune GitHub importera danych](https://github.com/ConfigMgrTools/Intune-Data-Importer/releases) strony.
2. W najnowszej wersji, kliknij przycisk **Microsoft.Intune.Data.Importer.exe**.
3. Zapisz i (lub po prostu uruchamiane) .exe, a następnie wybierz folder docelowy wyodrębnić narzędzie odbierający dane usługi Intune.

## <a name="run-the-data-importer-tool"></a>Uruchom narzędzie odbierający dane
Kreator narzędzia odbierający dane można podzielić w trzech głównych kroków. Ta sekcja zawiera informacje ułatwiające ukończenia każdej sekcji kreatora i pomyślnie zaimportować dane programu Configuration Manager do usługi Intune. Każdy krok będzie nadal występować, gdy upłynął poprzedniego kroku.

### <a name="provide-permission-for-the-data-importer-tool-to-access-resources"></a>Podać uprawnienia dla narzędzia odbierający dane dostęp do zasobów
Przed uruchomieniem narzędzia odbierający dane, należy użyć konta administratora globalnego udzielić zezwolenia narzędzia odbierający dane na platformie Azure na dostęp do zasobów. Następnie można Uruchom narzędzie przy użyciu konta administratora globalnego lub administratora usługi Intune.   

1.  Administrator globalny musi uruchomienia po raz pierwszy narzędzia przy użyciu następującego parametru: ***intunedataimporter.exe - GlobalConsent*** 
2. Podczas uruchamiania narzędzia, wyświetla ekran logowania, gdzie należy zalogować się przy użyciu konta z rolą administratora globalnego w usłudze Azure. 
3. Kliknij przycisk **Akceptuj** do tworzenia aplikacji na platformie Azure z odpowiednie uprawnienia w programie Microsoft Graph. Narzędzie odbierający dane musi te prawa można importować obiekty do Microsoft Intune.   

   > [!Important]
   > Po kliknięciu **Akceptuj**, zezwolić narzędzia wykonać następujące czynności:
   > - Odczytanie wszystkich grup
   > - Zaloguj się i odczytuj profil użytkownika
   > - Odczytywanie i zapisywanie konfiguracji urządzeń usługi Intune i zasady
   > - Odczyt i zapis aplikacji usługi Intune
   > - Odczyt i zapis zasad kontroli administracji opartej na rolach usługi Intune
   > - Odczyt i zapis urządzeń usługi Intune
   > - Odczytywanie i zapisywanie konfiguracji usługi Intune
1. Po wykonaniu zaakceptować zgody, inne administratora globalnego lub administratora usługi Intune, można uruchomić narzędzie do importowania danych z programu Configuration Manager do usługi Intune na platformie Azure.    
        
    > [!Note]
    > Jeśli zgody nie najpierw została zaakceptowana przez administratora globalnego, narzędzie może wyświetlić **nie masz dostępu do tej aplikacji** po przez administratora usługi Intune uruchamia narzędzie odbierający dane i loguje się do subskrypcji usługi Intune.

### <a name="manually-map-collections-to-azure-ad-groups"></a>Ręcznie zmapuj kolekcje do grup usługi Azure AD
Po uruchomieniu narzędzia odbierający dane wyodrębnia nazwę grupy AD z kolekcji przy użyciu jednej reguły, przeznaczonego dla pojedynczej grupy AD. Przydziały są tworzone w usłudze Intune, dane szuka grupy usługi Azure AD z taką samą nazwę jak grupy usługi Active Directory i jeśli istnieje, obiekt importowany przypisuje do tej grupy usługi Azure AD. Można zastąpić nazwę grupy AD wyszukującą odbierający dane dla kolekcji i podaj jedną lub więcej grup usługi Azure AD do użycia dla tej kolekcji. Plik mapowania kolekcji zapewnia sposób mapowania kolekcje, które nie są zwykle importowane z importera danych do grup usługi Azure AD.
#### <a name="find-the-collections-that-cannot-be-imported"></a>Znajdź kolekcji, których nie można zaimportować
Można uzyskać listę wszystkich kolekcji, które nie są importowane, dzięki czemu można dodać je do pliku CSV mapowania kolekcji. 
1. Uruchom narzędzie odbierający dane i wybierz obiekty do zaimportowania. Użyj procedur w programie [fazy 1: Odnajdywanie obiektów programu Configuration Manager i zbieranie danych](#phase-1:-discover-configuration-manager-objects-and-collect-data) i [Faza 2: Rozwiązywanie problemów i wybierz obiekty do zaimportowania](#phase-2:-resolve-issues-and-select-the-objects-to-import) na potrzeby odnajdywania i wybrać obiekty. Następnie na **Podsumowanie** wybierz pozycję **wyeksportować szczegóły** można utworzyć pliku CSV ze szczegółami dotyczącymi wszystkie elementy wybrane do importu, łącznie z obiektów, które nie mogą być importowane i wdrożeń. 
2. Otwórz plik CSV w programie Microsoft Excel i filtrowanie danych na podstawie **wdrożenia** dla **typu** kolumny i **nr** dla **Importable** kolumna. Kolumna nazw kolekcji zawiera wszystkie kolekcje, które mają zostać dodane do pliku mapowania kolekcji w kolejności tych wdrożeń być importowane.

#### <a name="create-the-collection-mapping-file"></a>Utwórz plik mapowania kolekcji
Plik mapowania kolekcji to plik wartości rozdzielanych przecinkami (CSV), gdzie pierwsza kolumna zawiera nazwę kolekcji programu Configuration Manager, a druga kolumna jest nazwa grupy usługi Azure AD do użycia dla tej kolekcji. Aby określić więcej niż jednej grupy usługi Azure AD dla jednej kolekcji programu Configuration Manager, należy utworzyć wiele wierszy w pliku CSV przy użyciu tej nazwy kolekcji. Poniższy przykład to plik CSV, który zawiera dwie kolekcje. Pierwsza kolekcja jest zamapowana do jednej usługi Azure AD grupę, a druga kolekcja jest mapowany na dwie grupy usługi Azure AD.

![Przykładowy plik csv mapowanie kolekcji](..\media\migrate-collectionmapping.png)

#### <a name="start-the-data-importer-tool-using-collection-mapping"></a>Uruchom narzędzie odbierający dane przy użyciu mapowania kolekcji
Aby użyć pliku mapowania kolekcji, należy uruchomić przy użyciu narzędzia odbierający dane *- CollectionMappingFile* parametru wiersza polecenia i Pełna ścieżka do pliku CSV mapowania kolekcji tworzenia. Na przykład:

```IntuneDataImporter.exe -CollectionMappingFile c:\Users\myuser\Documents\collectionmapping.csv```

> [!Note]
> Dane nie wyświetla żadnych czynności na każdej stronie kreatora, aby wskazać, że załadowano plik mapowania kolekcji. Jednak narzędzie wyświetla wszelkie błędy podczas odczytu pliku CSV. Ponadto na **Podsumowanie** kreatora możesz przejrzeć **wdrożenia** typów. Narzędzie wyświetla **tak** w kolumnie importowane i listy grup usługi Azure AD, które zostanie przypisana do obiektów w **uwagi** kolumny.

### <a name="phase-1-discover-configuration-manager-objects-and-collect-data"></a>Faza 1: Odnajdywanie obiektów programu Configuration Manager i zbieranie danych
W faza 1 można wybrać obiekty do odnajdywania i narzędzie zbierać informacje o wybranych obiektów. 
1. Otwórz narzędzie, a następnie kliknij przycisk **Start**.  
2. Przeczytaj informacje, a następnie kliknij przycisk **dalej**. 
3. Określ, czy do importowania wyeksportowanego wcześniej zestaw danych lub wybór wszystkich typów obiektów do zaimportowania:
   - **Importowanie wcześniej wyeksportowany zestawu danych**: Wybierz **zestawu danych importu wyeksportowane z poprzedniego uruchomienia odbierający dane Intune**i kliknij przycisk **Przeglądaj** dla **eksportować dane folderze** można wybrać dane, które wcześniej ustawione wyeksportowane za pomocą narzędzia importera danych. Użytkownik, który importuje zestawu danych musi być tego samego użytkownika, które wyeksportowane dane. Po zaimportowaniu danych podsumowanie obiektu są wyświetlane na **podsumowania** stronie kreatora. Jeśli poprawne podsumowania, przejdź do [fazy 3: Importuj wybrany obiekt do usługi Intune](phase-3:-import-selected-object-to-intune).
 
      > [!Note]
      > Po wykryć i wybierz obiekty w lokacji do zaimportowania, można wyeksportować obiekty do zestawu danych na **logowania do usługi Intune** stronie kreatora. Następnie można zaimportować zestawu danych na tej stronie. Zestaw danych jest zaszyfrowany przy użyciu poświadczeń użytkownika systemu Windows zalogowanego użytkownika, więc tylko użytkownik, który wyeksportowane zestaw danych można zaimportować zestawu danych za pomocą narzędzia. 
   - **Wybierz typy obiektów, aby zaimportować**: Wybierz **wybierz typy obiektów, aby zaimportować** wybierz typy obiektów, aby zaimportować i odnajdywanie obiektów w danym środowisku. Podaj następujące informacje dotyczące lokacji i obiektów, które chcesz zaimportować.
      - **Nazwa serwera lokacji**: Podaj w pełni kwalifikowaną nazwę serwera lokacji do importowania obiektów. Narzędzie wykrywa tylko obiekty, które są dostępne przez użytkownika z uruchomionym narzędziem. Zazwyczaj będzie określić lokację najwyższego poziomu i uruchom narzędzie z użytkownikiem, który ma dostęp do wszystkich obiektów w hierarchii lokacji.
      - **Kod lokacji**: Podaj kod lokacji dla serwera lokacji. Można znaleźć trzyliterowy kod w górnej części konsoli programu Configuration Manager.
      - **Typy do importowania obiektów**: Wybierz obiekty, które chcesz użyć narzędzia do zbierania. Możesz wybrać **Zaznacz wszystko** wszystkich obiektów lub wybierz typy pojedynczego obiektu. 
4.  Kliknij przycisk **dalej** uruchomić odnajdywania obiektów w lokacji. Narzędzie wyświetla postęp dla każdego typu obiektu. 
    - Gdy narzędzie wykrywa żadne dane dla typu wybranego obiektu, pasek natychmiast wyświetla zakończone dla tego typu obiektu postępu.
    - Obiekty, które nie zostały wybrane nie będą wyświetlane na **zbieranie** strony danych. 
    - Możesz uruchomić narzędzie ponownie dla obiektów, które nie zostały zebrane lub anulowania podczas procesu kolekcji.

### <a name="phase-2-resolve-issues-and-select-the-objects-to-import"></a>Faza 2: Rozwiązywanie problemów i wybierz obiekty do zaimportowania  
W kroku 2 Przejrzyj znalezionych przez narzędzie, rozwiąż problemy, które uniemożliwiają obiekt importowany do usługi Intune, a następnie wybierz obiekty do zaimportowania. Jeśli Rozwiązywanie problemów, wróć do **środowiska odnajdowania** w Kreatorze ponowne odnalezienie obiektów. 
5.  Kliknij przycisk **dalej** Aby przejrzeć zebranych obiektów. Strona wybierania elementów jest dostępna dla każdego typu obiektu zebrane. 
 <!--   > [!Tip]     
    > On each item selection page, you can create a filter to help you find the objects that you want to import. However, take note of the following:
    > - When you are on an item selection page and the view is filtered, the Select all checkboxes only apply to the displayed items. Any hidden objects because of a filter are not included when using the checkboxes.
    > - Objects are always grouped under their parent item even when you sort or filter the objects.
-->
6.  Na każdej stronie Wybór elementu obiekty zostaną posortowane według kolumny importowane i przejrzyj obiekty, które nie są importowane. Informacje w kolumnie o szczegółowe informacje na temat przyczyny narzędzia nie można zaimportować obiektu. 
7.  Teraz należy zdecydować, czy chcesz naprawić dowolne problemy z systemem innym niż importowane obiektów. Jeśli co najmniej jeden problem można rozwiązać, kliknij przycisk Wstecz, aż do uzyskania dostępu do danych wybierz ze strony programu Configuration Manager i zbieranie danych, aby zobaczyć, czy rozwiązać problem, ponownie. Można rozwiązać problemy, aż do uzyskania z obiektami, które są importowane. 
8.  Na każdej stronie wyboru Zaznacz obiekty, które chcesz zaimportować. Są wyświetlane następujące kolumny:
    - **Nazwa**: Nazwa obiektu programu Configuration Manager. 
    - **Importowane**: Określa, czy można zaimportować obiektu. Obiektów, które można wybrać tylko tak w kolumnie importowane. 
    - **Platforma**: Określa platformę obsługiwaną przez obiekt.
    - **Zaimportowano już**: Określa, czy obiekt został już zaimportowany za pomocą narzędzia na tym komputerze. 
    - **Są zastępowane** (dla aplikacji): Określa, czy aplikacja zostało zastąpione przez inną aplikację. Należy sprawdzić **Pokaż zastąpione aplikacji** pole wyboru w górnej części strony zastępowanej aplikacji do wyświetlenia.
    - **Uwagi dotyczące**: Zawiera informacje o Dlaczego nie można zaimportować obiektu. **Uwagi** kolumny zawiera również informacje o ustawieniach, które zostały zignorowane (dla niektórych typów obiektów), ale obiekt jest nadal importowane bez tych ustawień.
    - **Linie bazowe konfiguracji** (dla elementów konfiguracji): Określa linie bazowe konfiguracji, które są skojarzone z elementem konfiguracji.
    - **Wymagany certyfikat** (dla zasad i profilów): Określa, czy certyfikat jest skojarzony z obiektem. Gdy certyfikat jest skojarzony z obiektem, należy zaimportować certyfikat za.
9.  Po wybraniu obiekty do zaimportowania, są one wyświetlane na stronie Podsumowanie. Są dostępne następujące akcje: 
    - **Szczegóły eksportu**: Tworzy plik CSV zawierający informacje wyświetlane na ekranie. Zawiera także obiekty, które nie są importowane i przyczynę Dlaczego nie można go zaimportować. Ten plik można przechowywać na przyszłość. 
    - **Eksportuj dane błąd**: Eksportuje skompresowany plik, który zawiera informacje o danych, że narzędzia nie można przekonwertować lub importu. 

### <a name="phase-3-import-selected-objects-to-intune"></a>Faza 3: Importuj wybrane obiekty do usługi Intune
W kroku 3 możesz zalogować się do usługi Intune i importowanie wybranych obiektów. 
10. Kliknij przycisk **dalej**, a następnie kliknij przycisk **logowania w usłudze Intune** do logowania się do dzierżawy usługi Intune dla danych, zaimportować lub wyeksportować dane.

    - **Eksportuj**: Po wykryć i wybierz obiekty w lokacji do zaimportowania, można wyeksportować obiekty do zestawu danych. Umożliwia to odnajdywanie obiektów z komputera, który nie ma dostępu do Internetu, eksportować dane, a następnie zaimportuj dane z komputera, który ma dostęp do Internetu. Zestaw danych jest zaszyfrowany przy użyciu poświadczeń użytkownika systemu Windows zalogowanego użytkownika, więc tylko użytkownik, który wyeksportowane zestaw danych można zaimportować zestawu danych za pomocą narzędzia. Po wybraniu tej opcji wybierz ścieżkę do wyeksportowane dane. 
      1. Kliknij przycisk **wyeksportować** na **logowania w usłudze Intune** strony. 
      2. Kliknij przycisk **Przeglądaj** do folderu docelowego eksportu. Folder może być pusta. 
      3. Kliknij przycisk **Start** do wyeksportowania danych, a po zakończeniu eksportu kliknij przycisk **zamknąć** aby zakończyć pracę kreatora i zamknij odbierający dane.
      4. Uruchomić importera danych z innego komputera z dostępem do Internetu za pomocą tego samego poświadczenia i wybierz **importu wcześniej wyeksportowany zestawu danych** na drugiej stronie kreatora. Po zaimportowaniu danych, Kreator prowadzi do **logowania w usłudze Intune** strony. 
    - **Zaloguj się do usługi Intune**: Użytkownik musi zalogować się przy użyciu konta administratora globalnego lub administratora usługi Intune. Po zalogowaniu, rozpocznie się proces importowania.
    
      > [!Important]
      > Zaleca się przetestowanie procesu importowania danych za pomocą dzierżawy w wersji próbnej. Następnie po upewnieniu się, że oczekiwane zostały zaimportowane dane, można przejść przez ten sam proces z dzierżawą usługi Intune w środowisku produkcyjnym.
12. Strona postępu zapewnia postęp obiekty są importowane. Kliknij przycisk **dalej** po zakończeniu importowania. 
13. Na stronie ukończenie importowanych obiektów są wyświetlane. Sprawdź stan dla obiektów które napotkał błąd podczas procesu importowania. Są dostępne następujące akcje: 
    - **Szczegóły eksportu**: Tworzy plik CSV zawierający informacje wyświetlane na ekranie. Ten plik można przechowywać na przyszłość. 
    - **Eksportuj dane błąd**: Eksportuje skompresowany plik, który zawiera informacje o danych, że narzędzia nie można przekonwertować lub importu.

## <a name="next-steps"></a>Następne kroki
Po zaimportowaniu danych do usługi Intune, należy wykonać kroki, aby [przygotować usługę Intune do migracji użytkownika](migrate-prepare-intune.md). 