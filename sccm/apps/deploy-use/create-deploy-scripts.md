---
title: "Tworzenie i uruchamianie skryptów"
titleSuffix: Configuration Manager
description: "Tworzenie i uruchamianie skryptów programu Powershell na urządzeniach klienckich."
ms.custom: na
ms.date: 01/05/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cc230ff4-7056-4339-a0a6-6a44cdbb2857
caps.latest.revision: "14"
caps.handback.revision: "0"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: b00dfb875ca032032a9782e9950247eb3fceb124
ms.sourcegitcommit: 9de3d74030b7c3313c34b5cbe2dbe6e18a48c043
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/10/2018
---
# <a name="create-and-run-powershell-scripts-from-the-configuration-manager-console"></a>Tworzenie i uruchamianie skryptów programu PowerShell z poziomu konsoli programu Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

>[!TIP]
>Możliwość uruchamiania skryptów programu PowerShell wprowadzonym w wersji 1706, to funkcja wersji wstępnej. Aby włączyć skryptów, zobacz [w programie System Center Configuration Manager funkcje wersji wstępnej](/sccm/core/servers/manage/pre-release-features).

Mamy teraz lepiej zintegrowana możliwość uruchamiać skrypty programu Powershell w programie System Center Configuration Manager. PowerShell ma Zaletą tworzenia zaawansowanych, zautomatyzowanych skryptów, Rozumiem i udostępnione z branży. Skrypty uprościć tworzenie niestandardowego narzędzia do administrowania pozwalają osiągnąć żmudnych zadań szybkie, umożliwiając wykonywania obowiązków big łatwiejsze i bardziej spójnego i oprogramowania.

Dzięki tej integracji w programie System Center Configuration Manager, można użyć *uruchamianie skryptów* funkcje można wykonywać następujące czynności:

- Tworzenie i edytowanie skryptów do użytku w programie System Center Configuration Manager.
- Zarządzanie użyciem skryptu za pomocą ról i zakresów zabezpieczeń. 
- Uruchamianie skryptów w kolekcji lub poszczególnych lokalnymi zarządzanych komputerów z systemem Windows.
- Pobierz wyniki skryptu zagregowanej szybkiego z urządzeń klienckich.
- Monitorowanie wykonania skryptu i wyświetlić wyniki raportowania z danych wyjściowych skryptu.

>[!WARNING]
>Podana moc skrypty, możemy przypominać zamierzone i zachować ostrożność przy ich użycia. Stworzyliśmy dodatkowe zabezpieczenia, aby ułatwić; rozdzielone ról i zakresów. Pamiętaj sprawdzić dokładność skryptów przed ich uruchomieniem i upewnij się, że pochodzą z zaufanego źródła, aby zapobiec wykonaniu script niezamierzone. Zachować ostrożność, znaki rozszerzone lub innych zaciemnienie i zapoznanie się z informacjami o zabezpieczaniu skryptów.

## <a name="prerequisites"></a>Wymagania wstępne

- Aby uruchamiać skrypty programu PowerShell, klient musi działać program PowerShell w wersji 3.0 lub nowszej. Jednak jeśli po uruchomieniu skryptu zawiera funkcje z nowszej wersji programu PowerShell, klienta, na którym uruchomiono skrypt musi działać tej wersji programu PowerShell.
- Klienci programu Configuration Manager musi być uruchomiona klienta z wersji 1706 lub nowszego w celu uruchamiania skryptów.
- Używać skryptów, użytkownik musi należeć do odpowiedniej roli zabezpieczeń programu Configuration Manager.
- Aby zaimportować i tworzenia skryptów — Twoje konto musi mieć **Utwórz** uprawnienia dla **skryptów programu SMS** w **administrator o pełnych uprawnieniach** roli zabezpieczeń.
- Do zatwierdzenia lub odrzucenia skryptów — Twoje konto musi mieć **Zatwierdź** uprawnienia dla **skryptów programu SMS** w **administrator o pełnych uprawnieniach** roli zabezpieczeń.
- Aby uruchamiać skrypty - Twoje konto musi mieć **Uruchom skrypt** uprawnienia dla **kolekcje** w **administrator o pełnych uprawnieniach** roli zabezpieczeń.

Aby uzyskać więcej informacji na temat ról zabezpieczeń programu Configuration Manager, zobacz [podstawowe informacje dotyczące administrowania opartego na rolach](/sccm/core/understand/fundamentals-of-role-based-administration).

## <a name="limitations"></a>Ograniczenia

Uruchom skrypty obecnie obsługuje:

- Języki skryptów: PowerShell
- Typ parametru: liczba całkowita, ciąg i listy

## <a name="run-script-authors-and-approvers"></a>Uruchom skrypt autorzy i osoby zatwierdzające

Uruchom skrypty używa pojęcie *skryptu autorów* i *skryptu osób zatwierdzających* jako poszczególne role do wdrożenia i wykonywanie skryptu. O role autora i osoby zatwierdzającej oddzielone umożliwia sprawdzanie ważne procesu zaawansowane narzędzia, który jest uruchamianie skryptów.

### <a name="scripts-roles-control"></a>Formant ról skryptów

Domyślnie użytkownicy nie można zatwierdzić skryptu, który one utworzone przez użytkownika. Ponieważ skrypty są wydajne, elastyczne i można wdrożyć na wielu urządzeniach, można rozdzielić role między osoby, która tworzy skrypt i osoby, które zatwierdza skryptu. Role te zapewniają dodatkowy poziom zabezpieczeń przed uruchomieniem skryptu bez nadzoru. Możesz wyłączyć ten dodatkowej zatwierdzenia, aby ułatwić testowanie.

### <a name="approve-or-deny-a-script"></a>Zatwierdzanie lub odrzucanie skryptu

Skrypty musi być zatwierdzony przez *skryptu osoba zatwierdzająca* roli, aby mogły być uruchamiane. Aby zatwierdzić skryptu:

1. W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.
2. W **Biblioteka oprogramowania** obszaru roboczego kliknij **skryptów**.
3. W **skryptu** wybierz skrypt, aby zaakceptować lub odrzucić, a następnie na **Home** karcie **skryptu** kliknij przycisk **Zatwierdź/Deny**.
4. W **zatwierdzanie lub odrzucanie skryptu** wybierz pozycję **Zatwierdź** lub **Odmów** dla skryptu. Opcjonalnie wprowadź komentarz dotyczący decyzji.  Jeśli użytkownik zezwoli na skryptu, nie można uruchomić na urządzeniach klienckich. <br>
![Skrypt - zatwierdzenia](./media/run-scripts/RS-approval.png)
1. Ukończ pracę kreatora. W **skryptu** listy, zostanie wyświetlony **stan zatwierdzenia** zmiany kolumny w zależności od akcja została wykonana.

### <a name="allow-users-to-approve-their-own-scripts"></a>Użytkownicy mogą zatwierdzać własnych skryptów

To jest używany głównie do przeprowadzenia w fazie testowania skryptów tworzenia.

1. W konsoli programu Configuration Manager kliknij przycisk **Administracja**.
2. W obszarze roboczym **Administracja** rozwiń węzeł **Konfiguracja lokacji**, a następnie kliknij przycisk **Lokacje**.
3. Na liście witryn, wybierz witryny, a następnie na **Home** karcie **witryny** kliknij przycisk **ustawienia hierarchii**.
4. Na **ogólne** karcie **właściwości ustawień hierarchii** okna dialogowego polu, wyczyść pole wyboru **nie zezwalaj na skryptu autorzy mogą zatwierdzać własnych skryptów**.

>[!IMPORTANT]
>Najlepszym rozwiązaniem nie należy zezwalać na autorowi skryptu zatwierdzać własnych skryptów. To powinno być dozwolone tylko w środowisku laboratoryjnym. Należy rozważyć potencjalny wpływ zmiany tego ustawienia w środowisku produkcyjnym.

## <a name="security-scopes"></a>Zakresy zabezpieczeń
*(Wprowadzonym w wersji 1710)*  
Uruchom używa skryptów zakresy zabezpieczeń istniejących funkcji programu Configuration Manager do tworzenia skryptów kontroli i wykonywanie poprzez przypisywanie tagi, które reprezentują grup użytkowników. Aby uzyskać więcej informacji na temat używania zakresy zabezpieczeń, zobacz [Konfigurowanie administracji opartej na rolach dla programu System Center Configuration Manager](../../core/servers/deploy/configure/configure-role-based-administration.md).

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
    >  Unikaj skryptów ponowne uruchomienie urządzenia lub ponownego uruchomienia agenta menedżera konfiguracji podczas korzystania z funkcji uruchamianie skryptów. To może prowadzić do ciągłego stanu rebooting. Jeśli to konieczne, istnieją ulepszenia funkcji powiadomienia klienta umożliwiające ponownie uruchomić urządzenia, począwszy od 1710 wersji programu Configuration Manager. [Do czasu ponownego uruchomienia kolumny](/sccm/core/clients/manage/manage-clients#Restart-clients) może ułatwić identyfikację urządzenia, które wymagają ponownego uruchomienia komputera. 
<!--SMS503978--Script reboot warning-->

## <a name="script-parameters"></a>Parametry skryptu
*(Wprowadzonym w wersji 1710)*  
Dodawanie parametrów do skryptu zapewnia większą elastyczność do pracy. Poniżej opisano możliwości bieżącej funkcji uruchamianie skryptów z Parametry skryptu. *Ciąg*, *całkowitą* typów danych. Dostępne są również list wstępnie zdefiniowane wartości. Jeśli skrypt zawiera nieobsługiwane typy danych, zostanie wyświetlone ostrzeżenie.

W **Tworzenie skryptu** okna dialogowego, kliknij przycisk **Parametry skryptu** w obszarze **skryptu**.

Każdy z parametrów skryptu ma własne okno dialogowe dodawania dalszych szczegółów i sprawdzania poprawności.

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

Ten skrypt tworzy nowy folder i plik w jego podane dane wejściowe pod kątem nazw.

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

## <a name="see-also"></a>Zobacz też

- [Konfigurowanie administracji opartej na rolach dla programu System Center Configuration Manager](../../core/servers/deploy/configure/configure-role-based-administration.md)
- [Podstawy administracji opartej na rolach](/sccm/core/understand/fundamentals-of-role-based-administration)
