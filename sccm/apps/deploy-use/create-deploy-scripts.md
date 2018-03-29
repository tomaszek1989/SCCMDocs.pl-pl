---
title: Tworzenie i uruchamianie skryptów
titleSuffix: Configuration Manager
description: Tworzenie i uruchamianie skryptów programu Powershell na urządzeniach klienckich.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cc230ff4-7056-4339-a0a6-6a44cdbb2857
caps.latest.revision: ''
caps.handback.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 19bb8b2c4e47dcc8a75db568e7f93541544a4566
ms.sourcegitcommit: a19e12d5c3198764901d44f4df7c60eb542e765f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/28/2018
---
# <a name="create-and-run-powershell-scripts-from-the-configuration-manager-console"></a>Tworzenie i uruchamianie skryptów programu PowerShell z poziomu konsoli programu Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


System Center Configuration Manager ma zintegrowane możliwość uruchamiania skryptów programu Powershell. PowerShell ma Zaletą tworzenia zaawansowanych, zautomatyzowanych skryptów, Rozumiem i udostępnione z branży. Skrypty uprościć tworzenie niestandardowego narzędzia do administrowania pozwalają osiągnąć żmudnych zadań szybko, co umożliwia uzyskiwanie dużych zadań łatwiejsze i bardziej spójnego i oprogramowania.

> [!TIP]  
> Ta funkcja została wprowadzona w wersji 1706 jako [funkcji wersji wstępnej](/sccm/core/servers/manage/pre-release-features). Począwszy od wersji 1802, ta funkcja nie jest już funkcji wersji wstępnej.


Dzięki tej integracji w programie System Center Configuration Manager, można użyć *uruchamianie skryptów* funkcji, aby wykonać następujące czynności:

- Tworzenie i edytowanie skryptów do użytku w programie System Center Configuration Manager.
- Zarządzanie użyciem skryptu za pomocą ról i zakresów zabezpieczeń. 
- Uruchamianie skryptów w kolekcji lub poszczególnych lokalnymi zarządzanych komputerów z systemem Windows.
- Pobierz wyniki skryptu zagregowanej szybkiego z urządzeń klienckich.
- Monitorowanie wykonania skryptu i wyświetlić wyniki raportowania z danych wyjściowych skryptu.

>[!WARNING]
>Podana moc skrypty, możemy przypominać zamierzone i zachować ostrożność przy ich użycia. Stworzyliśmy dodatkowe zabezpieczenia, aby ułatwić; rozdzielone ról i zakresów. Pamiętaj sprawdzić dokładność skryptów przed ich uruchomieniem i upewnij się, że pochodzą z zaufanego źródła, aby zapobiec wykonaniu script niezamierzone. Zachować ostrożność, znaki rozszerzone lub innych zaciemnienie i zapoznanie się z informacjami o zabezpieczaniu skryptów. [Dowiedz się więcej o zabezpieczeniach skrypt programu PowerShell](/sccm/apps/deploy-use/learn-script-security)

## <a name="prerequisites"></a>Wymagania wstępne

- Aby uruchamiać skrypty programu PowerShell, klient musi działać program PowerShell w wersji 3.0 lub nowszej. Jednak jeśli po uruchomieniu skryptu zawiera funkcje z nowszej wersji programu PowerShell, klienta, na którym uruchomiono skrypt musi działać tej wersji programu PowerShell.
- Klienci programu Configuration Manager musi być uruchomiona klienta z wersji 1706 lub nowszego w celu uruchamiania skryptów.
- Używać skryptów, użytkownik musi należeć do odpowiedniej roli zabezpieczeń programu Configuration Manager.
- Aby zaimportować i tworzenia skryptów — Twoje konto musi mieć **Utwórz** uprawnienia dla **skryptów programu SMS**.
- Do zatwierdzenia lub odrzucenia skryptów — Twoje konto musi mieć **Zatwierdź** uprawnienia dla **skryptów programu SMS**.
- Aby uruchamiać skrypty - Twoje konto musi mieć **Uruchom skrypt** uprawnienia dla **kolekcji**.

Aby uzyskać więcej informacji na temat ról zabezpieczeń programu Configuration Manager:</br>
[Zakresy zabezpieczeń dla wykonywania skryptów](#BKMK_Scopes)</br>
[Role zabezpieczeń dla wykonywania skryptów](#BKMK_ScriptRoles)</br>
[Podstawowe informacje dotyczące administrowania opartego na rolach](/sccm/core/understand/fundamentals-of-role-based-administration).

## <a name="limitations"></a>Ograniczenia

Uruchom skrypty obecnie obsługuje:

- Języki skryptów: PowerShell
- Typ parametru: liczba całkowita, ciąg i listy.


>[!WARNING]
>Należy pamiętać, że podczas korzystania z parametrów, otwiera powierzchni dla potencjalne ryzyko ataków iniekcji programu PowerShell. Istnieją różne sposoby ograniczenia i obejścia, takie jak za pomocą wyrażeń regularnych do sprawdzania poprawności danych wejściowych parametru lub przy użyciu wstępnie zdefiniowanych parametrów. Typowe najlepszym rozwiązaniem jest nie, aby dołączyć do kluczy tajnych w skryptach środowiska PowerShell (nie hasła itp.). [Dowiedz się więcej o zabezpieczeniach skrypt programu PowerShell](/sccm/apps/deploy-use/learn-script-security) <!--There are external tools available to validate your PowerShell scripts such as the [PowerShell Injection Hunter](https://www.powershellgallery.com/packages/InjectionHunter/1.0.0) tool. -->


## <a name="run-script-authors-and-approvers"></a>Uruchom skrypt autorzy i osoby zatwierdzające

Uruchom skrypty używa pojęcie *skryptu autorów* i *skryptu osób zatwierdzających* jako poszczególne role do wdrożenia i wykonywanie skryptu. O role autora i osoby zatwierdzającej oddzielone umożliwia sprawdzanie ważne procesu zaawansowane narzędzia, który jest uruchamianie skryptów. Brak dodatkowych *skryptów używanych modułów uruchamiających* roli, która zezwala na wykonywanie skryptów, ale nie tworzenia lub zatwierdzenia skryptów. Zobacz [tworzyć role zabezpieczeń dla skryptów](#BKMK_ScriptRoles).

### <a name="scripts-roles-control"></a>Formant ról skryptów

Domyślnie użytkownicy nie można zatwierdzić skryptu, który one utworzone przez użytkownika. Ponieważ skrypty są wydajne, elastyczne i potencjalnie wdrożonego na wielu urządzeniach, można rozdzielić role między osoby, która tworzy skrypt i osoby, które zatwierdza skryptu. Role te zapewniają dodatkowy poziom zabezpieczeń przed uruchomieniem skryptu bez nadzoru. Mogą wyłączyć dodatkowej zatwierdzenia, aby ułatwić testowanie.

### <a name="approve-or-deny-a-script"></a>Zatwierdzanie lub odrzucanie skryptu

Skrypty musi być zatwierdzony przez *skryptu osoba zatwierdzająca* roli, aby mogły być uruchamiane. Aby zatwierdzić skryptu:

1. W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.
2. W **Biblioteka oprogramowania** obszaru roboczego kliknij **skryptów**.
3. W **skryptu** wybierz skrypt, aby zaakceptować lub odrzucić, a następnie na **Home** karcie **skryptu** kliknij przycisk **Zatwierdź/Deny**.
4. W **zatwierdzanie lub odrzucanie skryptu** wybierz pozycję **Zatwierdź**, lub **Odmów** dla skryptu. Opcjonalnie wprowadź komentarz dotyczący decyzji.  Jeśli użytkownik zezwoli na skryptu, nie można uruchomić na urządzeniach klienckich. <br>
![Skrypt - zatwierdzenia](./media/run-scripts/RS-approval.png)
1. Ukończ pracę kreatora. W **skryptu** listy, zostanie wyświetlony **stan zatwierdzenia** zmiany kolumny w zależności od akcja została wykonana.

### <a name="allow-users-to-approve-their-own-scripts"></a>Użytkownicy mogą zatwierdzać własnych skryptów

To jest używany głównie do przeprowadzenia w fazie testowania skryptów tworzenia.

1. W konsoli programu Configuration Manager kliknij przycisk **Administracja**.
2. W obszarze roboczym **Administracja** rozwiń węzeł **Konfiguracja lokacji**, a następnie kliknij przycisk **Lokacje**.
3. Na liście witryn, wybierz witryny, a następnie na **Home** karcie **witryny** kliknij przycisk **ustawienia hierarchii**.
4. Na **ogólne** karcie **właściwości ustawień hierarchii** okna dialogowego polu, wyczyść pole wyboru **nie zezwalaj na skryptu autorzy mogą zatwierdzać własnych skryptów**.

>[!IMPORTANT]
>Najlepszym rozwiązaniem nie należy zezwalać na autorowi skryptu zatwierdzać własnych skryptów. Powinno być dozwolone tylko w środowisku laboratoryjnym. Należy rozważyć potencjalny wpływ zmiany tego ustawienia w środowisku produkcyjnym.

## <a name="security-scopes"></a>Zakresy zabezpieczeń
*(Wprowadzonym w wersji 1710)*  
Uruchom używa skryptów zakresy zabezpieczeń istniejących funkcji programu Configuration Manager do tworzenia skryptów kontroli i wykonywanie poprzez przypisywanie tagi, które reprezentują grup użytkowników. Aby uzyskać więcej informacji na temat używania zakresy zabezpieczeń, zobacz [Konfigurowanie administracji opartej na rolach dla programu System Center Configuration Manager](../../core/servers/deploy/configure/configure-role-based-administration.md).

## <a name="bkmk_ScriptRoles"></a> Tworzenie ról zabezpieczeń skryptów
Domyślnie w programie Configuration Manager nie są tworzone trzy role używane do uruchamiania skryptów. Aby utworzyć skrypt uczestników, autorów skryptów i role osób zatwierdzających skryptu, wykonaj kroki obramowane.

1. W konsoli programu Configuration Manager, przejdź do **administracji** >**zabezpieczeń** >**ról zabezpieczeń**
2. Kliknij prawym przyciskiem myszy rolę i kliknij przycisk **kopiowania**. Rola, którą należy skopiować ma już przypisane uprawnienia. Upewnij się, że należy wykonać tylko uprawnienia, które mają. 
3. Nadaj tworzona rola niestandardowa **nazwa** i **opis**. 
4. Przypisz uprawnienia przedstawione poniżej roli zabezpieczeń. 

    ### <a name="security-role-permissions"></a>**Uprawnienia roli zabezpieczeń**

     **Nazwa roli**: Używanych modułów uruchamiających skryptu
    - **Opis elementu**: Te uprawnienia włączyć tę rolę można uruchamiać tylko skrypty, które zostały wcześniej utworzona i zatwierdzona przez innych ról. 
    - **Uprawnienia:** Upewnij się, ustawiono następujące **tak**.
         |**Kategoria**|**Uprawnienia**|**Stan**|
         |---|---|---|
         |Kolekcja|Uruchom skrypt|Tak|
         |Skrypty programu SMS|Utwórz|Tak|
         |Skrypty programu SMS|Odczyt|Tak|

     **Nazwa roli**: Autorzy skryptu
    - **Opis elementu**: Te uprawnienia włączyć tę rolę można tworzyć skrypty, ale nie można zatwierdzić lub ich uruchamiać. 
    - **Uprawnienia**: Upewnij się, że następujące uprawnienia zostały ustawione.
    - 
         |**Kategoria**|**Uprawnienia**|**Stan**|
         |---|---|---|
         |Kolekcja|Uruchom skrypt|Nie|
         |Skrypty programu SMS|Utwórz|Tak|
         |Skrypty programu SMS|Odczyt|Tak|
         |Skrypty programu SMS|Usuwanie|Tak|
         |Skrypty programu SMS|Modyfikuj|Tak|

    **Nazwa roli**: Autorzy skryptu
    - **Opis elementu**: Te uprawnienia włączyć tę rolę zatwierdzić skryptów, ale ich nie można utworzyć ani uruchomić je. 
    - **Uprawnienia:** Upewnij się, że następujące uprawnienia zostały ustawione.

         |**Kategoria**|**Uprawnienia**|**Stan**|
         |---|---|---|
         |Kolekcja|Uruchom skrypt|Nie|
         |Skrypty programu SMS|Odczyt|Tak|
         |Skrypty programu SMS|Zatwierdzanie|Tak|
         |Skrypty programu SMS|Modyfikuj|Tak|
     
**Przykładowe skrypty SMS uprawnienia roli autorów skryptu**

 ![Przykładowe skrypty SMS uprawnienia roli autorów skryptu](./media/run-scripts/script_authors_permissions.png)

   

## <a name="create-a-script"></a>Utwórz skrypt

1. W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.
2. W **Biblioteka oprogramowania** obszaru roboczego kliknij **skryptów**.
3. Na **Home** karcie **Utwórz** kliknij przycisk **Tworzenie skryptu**.
4. Na **skryptu** tworzenia **skryptu** kreatora skonfiguruj następujące ustawienia:
    - **Nazwa skryptu** — wprowadź nazwę skryptu. Mimo że można tworzyć wiele skryptów o takiej samej nazwie, przy użyciu takich samych nazwach utrudnia odnajdywania skryptów, które są potrzebne w konsoli programu Configuration Manager.
    - **Język skryptów** — obecnie są obsługiwane tylko skrypty programu PowerShell.
    - **Importuj** — importowanie skrypt programu PowerShell do konsoli. Skrypt jest wyświetlany w **skryptu** pola.
    - **Wyczyść** — usuwa bieżący skrypt pola skryptu.
    - **Skrypt** -wyświetla skrypt aktualnie zaimportowany. Skrypt w tym polu, w razie potrzeby można edytować.
5. Ukończ pracę kreatora. Nowy skrypt jest wyświetlany w **skryptu** liście ze stanem **oczekiwanie na zatwierdzenie**. Zanim można było uruchomić ten skrypt na urządzeniach klienckich, należy ją zatwierdzić. 

> [!IMPORTANT]
    >Unikaj skryptów ponowne uruchomienie urządzenia lub ponownego uruchomienia agenta menedżera konfiguracji podczas korzystania z funkcji uruchamianie skryptów. To może prowadzić do ciągłego stanu rebooting. Jeśli to konieczne, istnieją ulepszenia funkcji powiadomienia klienta umożliwiające ponownie uruchomić urządzenia, począwszy od 1710 wersji programu Configuration Manager. [Do czasu ponownego uruchomienia kolumny](/sccm/core/clients/manage/manage-clients#Restart-clients) może ułatwić identyfikację urządzenia, które wymagają ponownego uruchomienia komputera. 
<!--SMS503978  -->

## <a name="script-parameters"></a>Parametry skryptu
*(Wprowadzonym w wersji 1710)*  
Dodawanie parametrów do skryptu zapewnia większą elastyczność do pracy. Poniżej opisano możliwości bieżącej funkcji uruchamianie skryptów z Parametry skryptu. *Ciąg*, *całkowitą* typów danych. Dostępne są również list wstępnie zdefiniowane wartości. Jeśli skrypt zawiera nieobsługiwane typy danych, zostanie wyświetlone ostrzeżenie.

W **Tworzenie skryptu** okna dialogowego, kliknij przycisk **Parametry skryptu** w obszarze **skryptu**.

Każdy z parametrów skryptu ma własne okno dialogowe dodawania dalszych szczegółów i sprawdzania poprawności.

>[!IMPORTANT]
> Wartości parametrów nie może zawierać apostrof. 


### <a name="parameter-validation"></a>Sprawdzanie poprawności parametru

Każdy parametr w skrypcie ma **właściwości parametru skryptu** okno dialogowe umożliwiające dodawanie sprawdzania poprawności dla tego parametru. Po dodaniu weryfikacji, należy pobrać błędy podczas wprowadzania wartości dla parametru, który nie spełnia jego poprawności.

#### <a name="example-firstname"></a>Przykład: *Imię*

W tym przykładzie jest możliwość ustawiania właściwości parametru ciągu *imię*.

![Parametry skryptu — ciąg](./media/run-scripts/RS-parameters-string.png)


Sprawdzanie poprawności części **właściwości parametru skryptu** okno dialogowe zawiera następujące pola do użycia:

- **Minimalna długość** — minimalna liczba znaków *imię* pola.
- **Maksymalna długość**— maksymalna liczba znaków *imię* pola
- **Wyrażenie regularne** — skrót *wyrażenie regularne*. Aby uzyskać więcej informacji o korzystaniu z wyrażeniem regularnym, zobacz następną sekcję, *weryfikacji przy użyciu wyrażenia regularnego*.
- **Błąd niestandardowy** — jest to przydatne w przypadku dodawania własny niestandardowy komunikat o błędzie zastępującym komunikaty o błędach weryfikacji systemu.

#### <a name="using-regular-expression-validation"></a>Przy użyciu weryfikacji wyrażenia regularnego

Wyrażenie regularne jest compact formularza programowania sprawdzania ciąg znaków względem zakodowanego sprawdzania poprawności. Na przykład można sprawdzić, czy brak kapitału litery w *imię* przez umieszczenie `[^A-Z]` w *RegEx* pola.

Wyrażenie regularne przetwarzania dla tego okna dialogowego jest obsługiwana przez program .NET Framework. Aby uzyskać wskazówki dotyczące za pomocą wyrażeń regularnych, zobacz [wyrażenie regularne .NET](https://docs.microsoft.com/dotnet/standard/base-types/regular-expressions). 


## <a name="script-examples"></a>Przykłady skryptów

Oto kilka przykładów ilustrujące skrypty, które można korzystać z tej funkcji.

### <a name="create-a-new-folder-and-file"></a>Utwórz nowy folder i plików

Ten skrypt tworzy nowy folder i plik w folderze podane dane wejściowe pod kątem nazw.

``` powershell
Param(
[Parameter(Mandatory=$True)]
[string]$FolderName,
[Parameter(Mandatory=$True)]
[string]$FileName,
)

New-Item $FolderName -type directory
New-Item $FileName -type file
```

### <a name="get-os-version"></a>Pobieranie wersji systemu operacyjnego

Ten skrypt używa usługi WMI do badania komputer, aby jego wersja systemu operacyjnego.

``` powershell
Write-Output (Get-WmiObject -Class Win32_operatingSystem).Caption
```

## <a name="run-a-script"></a>Uruchom skrypt

Po zatwierdzeniu skryptu mogą być uruchamiane na jednym urządzeniu lub kolekcji. Po rozpoczęciu wykonywania skryptu uruchomionego szybko za pośrednictwem systemu o wysokim priorytecie, w którym wychodzący razy w ciągu godziny. Zwracany są wyniki skryptu, za pomocą systemu komunikatów o stanie.

Aby wybrać kolekcję elementów docelowych dla skryptu:

1. W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.
2. W zasoby i zgodność obszar roboczy, kliknij przycisk **kolekcje urządzeń**.
3. W **kolekcje urządzeń** kliknij kolekcję urządzeń, na których chcesz uruchomić skrypt.
4. Wybierz kolekcję wybór, kliknij przycisk **Uruchom skrypt**.
5. Na **skryptu** strony **Uruchom skrypt** kreatora wybierz skrypt z listy. Wyświetlane są tylko zatwierdzone skrypty.
6. Kliknij przycisk **dalej**, a następnie Zakończ pracę kreatora.

>[!IMPORTANT]
>Jeśli skrypt nie działa, na przykład ponieważ urządzenia docelowego jest wyłączony w trakcie godzinę przedziale czasu, należy uruchomić je ponownie.

### <a name="target-machine-execution"></a>Wykonanie komputera docelowego

Skrypt zostanie wykonany jako *systemu* lub *komputera* konta na docelowych klientów. To konto ma ograniczony dostęp do sieci. Dostęp do systemów zdalnych i lokalizacje przez skrypt muszą mieć odpowiednio przydzielone.

## <a name="script-monitoring"></a>Skrypt monitorowania

Po zainicjowaniu uruchomienie skryptu w kolekcji urządzeń, użyj poniższej procedury do monitorowania operacji. Począwszy od wersji 1710, są, jednocześnie możliwość monitorowania skryptu w czasie rzeczywistym, wykonywania i można także wrócić do raportu dla danego wykonywania Uruchom skrypt. <br>

![Monitor skryptu — stan uruchomienia skryptu](./media/run-scripts/RS-monitoring-three-bar.png)

1. W konsoli programu Configuration Manager kliknij **monitorowanie**.
2. W **monitorowanie** obszaru roboczego kliknij **stanu skryptu**.
3. W **stanu skryptu** listy, wyświetlania wyników dla każdego skryptu uruchomionego na urządzeniach klienckich. Kod zakończenia skryptu **0** ogół wskazuje, że skrypt został uruchomiony pomyślnie.
    - Począwszy od programu Configuration Manager 1802, dane wyjściowe skryptu jest obcinana do 4 KB, aby umożliwić lepsze środowisko wyświetlania.  <!--510013-->
      ![Monitor skryptu — skrócona skryptu](./media/run-scripts/Script-monitoring-truncated.png) 

## <a name="script-output"></a>Dane wyjściowe skryptu

- Począwszy od programu Configuration Manager w wersji 1802 danych wyjściowych skryptu zwraca przy użyciu formatowania JSON. Ten format spójnie zwraca dane wyjściowe skryptu do odczytu. 
- Skrypty, które uzyskać nieznany wynik lub których klient był w trybie offline, nie zostanie wyświetlona w wykresach lub zestawu danych. <!--507179-->
- Unikaj przekazujących dane wyjściowe skryptu dużych, ponieważ jest obcinana do 4 KB. <!--508488-->
- Niektóre funkcje ze skryptem wyjściowe formatowanie nie jest dostępna podczas uruchamiania 1802 wersji programu Configuration Manager lub nowszego z niższej wersji klienta. <!--508487-->
    - Gdy klient programu Configuration Manager pre 1802, otrzymasz wyjściowego ciągu.
    -  Dla programu Configuration Manager wersja klienta 1802 i powyżej, możesz pobrać formatowania JSON.
        - Na przykład może uzyskiwać wyniki, które Wypowiedz tekst w jednej wersji klienta i "TEXT" (dane wyjściowe jest ujęta w cudzysłów podwójny) na innych wersji, która zostanie umieszczona na wykresie jako dwa różne kategorie.
        - Aby obejść ten problem, należy rozważyć uruchomienie skryptu przed dwa różne kolekcje. Jeden z wstępnie 1802 klienci i inny 1802 i wyższych. Lub obiektu wyliczenia można przekonwertować na wartość ciągu w skryptach, są wyświetlane poprawnie w formacie JSON formatowania. 
- Przekonwertować obiektu wyliczenia wartość ciągu w skryptach, są wyświetlane poprawnie w formacie JSON formatowania. <!--508377--> ![Przekonwertować na wartość ciągu obiektu wyliczenia](./media/run-scripts/enum-tostring-JSON.png)



## <a name="see-also"></a>Zobacz też

- [Konfigurowanie administracji opartej na rolach dla programu System Center Configuration Manager](../../core/servers/deploy/configure/configure-role-based-administration.md)
- [Podstawy administracji opartej na rolach](/sccm/core/understand/fundamentals-of-role-based-administration)
