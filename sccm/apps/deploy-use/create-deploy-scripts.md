---
title: "Tworzenie i uruchamianie skryptów"
titleSuffix: Configuration Manager
description: "Tworzenie i uruchamianie skryptów programu Powershell na urządzeniach klienckich."
ms.custom: na
ms.date: 11/20/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cc230ff4-7056-4339-a0a6-6a44cdbb2857
caps.latest.revision: "14"
caps.handback.revision: "0"
author: BrucePerlerMS
ms.author: bruceper
manager: angrobe
ms.openlocfilehash: 964f6d39c4c1afc82ff4336821740923d27cd569
ms.sourcegitcommit: 12d0d53e47bbf1a0bbd85015b8404a44589d1e14
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="create-and-run-powershell-scripts-from-the-configuration-manager-console"></a>Tworzenie i uruchamianie skryptów programu PowerShell z poziomu konsoli programu Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Mamy teraz lepiej zintegrowana możliwość uruchamiać skrypty programu Powershell w programie System Center Configuration Manager. PowerShell ma Zaletą tworzenia zaawansowanych, zautomatyzowanych skryptów, Rozumiem i udostępnione z branży. Skrypty uprościć tworzenie niestandardowego narzędzia do administrowania oprogramowania i pozwalają osiągnąć żmudnych zadań, umożliwiając szybkie wykonywania obowiązków big łatwiejsze i bardziej spójnie.

Dzięki tej integracji w programie System Center Configuration Manager, można użyć *uruchamianie skryptów* funkcje można wykonywać następujące czynności:

- Tworzenie i edytowanie skryptów do użytku z programem Configuration Manager.
- Zarządzanie użyciem skryptu za pomocą ról i zakresów zabezpieczeń  
- Uruchamianie skryptów w kolekcji lub poszczególnych lokalnymi zarządzanych komputerów z systemem Windows.
- Pobierz wyniki skryptu zagregowanej szybkiego z urządzeń klienckich.
- Monitorowanie wykonania skryptu i wyświetlić wyniki raportowania z danych wyjściowych skryptu.

>[!IMPORTANT]
>Podana moc skrypty, możemy przypominać zamierzone i zachować ostrożność przy ich użycia. Stworzyliśmy dodatkowe zabezpieczenia, aby ułatwić; rozdzielone ról i zakresów. Pamiętaj sprawdzić dokładność skryptów przed ich uruchomieniem i upewnij się, że pochodzą z zaufanego źródła, aby zapobiec wykonaniu script niezamierzone. Zachować ostrożność, znaki rozszerzone lub innych zaciemnienie i zapoznanie się z informacjami o zabezpieczaniu skryptów.

>[!TIP]
>Skrypty programu PowerShell wprowadzonym w wersji 1706, to funkcja wersji wstępnej. Aby włączyć skryptów, zobacz [w programie System Center Configuration Manager funkcje wersji wstępnej](/sccm/core/servers/manage/pre-release-features).

## <a name="prerequisites"></a>Wymagania wstępne

- Aby uruchamiać skrypty programu PowerShell, klient musi działać program PowerShell w wersji 3.0 lub nowszej. Jednak jeśli po uruchomieniu skryptu zawiera funkcje z nowszej wersji programu PowerShell, klienta, na którym uruchomiono skrypt musi działać tej wersji programu PowerShell.
- Klienci programu Configuration Manager musi być uruchomiona klienta z wersji 1706 lub nowszego w celu uruchamiania skryptów.
- Używać skryptów, użytkownik musi należeć do odpowiedniej roli zabezpieczeń programu Configuration Manager.
- Aby zaimportować i tworzenia skryptów — Twoje konto musi mieć **Utwórz** uprawnienia dla **skryptów programu SMS** w **administrator o pełnych uprawnieniach** roli zabezpieczeń.
- Do zatwierdzenia lub odrzucenia skryptów — Twoje konto musi mieć **Zatwierdź** uprawnienia dla **skryptów programu SMS** w **administrator o pełnych uprawnieniach** roli zabezpieczeń.
- Aby uruchamiać skrypty - Twoje konto musi mieć **Uruchom skrypt** uprawnienia dla **kolekcje** w **Menedżer ustawień zgodności** roli zabezpieczeń.

Aby uzyskać więcej informacji na temat ról zabezpieczeń programu Configuration Manager, zobacz [podstawowe informacje dotyczące administrowania opartego na rolach](/sccm/core/understand/fundamentals-of-role-based-administration).

## <a name="limitations"></a>Ograniczenia

Uruchom skrypty obecnie obsługuje:

- Języki skryptów: PowerShell
- Typ parametru: liczba całkowita i ciąg

## <a name="run-script-authors-and-approvers"></a>Uruchom skrypt autorzy i osoby zatwierdzające

Uruchom skrypty używa pojęcie *skryptu autorów* i *skryptu osób zatwierdzających* jako poszczególne role do wdrożenia i wykonywanie skryptu. O role autora i osoby zatwierdzającej oddzielone umożliwia sprawdzanie ważne procesu zaawansowane narzędzia, który jest uruchamianie skryptów.

### <a name="scripts-roles-control"></a>Formant ról skryptów

Domyślnie użytkownicy nie można zatwierdzić skryptu, który one utworzone przez użytkownika. Ponieważ skrypty są wydajne, elastyczne i można wdrożyć na wielu urządzeniach, można rozdzielić role między osoby, która tworzy skrypt i osoby, które zatwierdza skryptu. Role te zapewniają dodatkowy poziom zabezpieczeń przed uruchomieniem skryptu bez nadzoru. Możesz wyłączyć ten dodatkowej zatwierdzenia, aby ułatwić testowanie.

### <a name="approve-or-deny-a-script"></a>Zatwierdzanie lub odrzucanie skryptu

Skrypty musi być zatwierdzony przez *skryptu osoba zatwierdzająca* roli, aby mogły być uruchamiane. Aby zatwierdzić skryptu:

1. W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.
2. W **Biblioteka oprogramowania** obszaru roboczego kliknij **skryptów**.
3. W **skryptu** wybierz skrypt, aby zaakceptować lub odrzucić, a następnie na **Home** karcie **skryptu** kliknij przycisk **Zatwierdź/Deny**.
4. W **Zatwierdź lub odmówić skryptu** okno dialogowe, wybierz opcję **Zatwierdź** lub **Odmów** skryptu i opcjonalnie wprowadź komentarz dotyczący decyzji.  Jeśli użytkownik zezwoli na skryptu, nie można uruchomić na urządzeniach klienckich. <br>
![Skrypt - zatwierdzenia](./media/run-scripts/RS-approval.png)
5. Ukończ pracę kreatora. W **skryptu** listy, zostanie wyświetlony **stan zatwierdzenia** zmiany kolumny w zależności od akcja została wykonana.

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
1. Ukończ pracę kreatora. Nowy skrypt jest wyświetlany w **skryptu** liście ze stanem **oczekiwanie na zatwierdzenie**. Zanim można było uruchomić ten skrypt na urządzeniach klienckich, należy ją zatwierdzić.

## <a name="script-parameters"></a>Parametry skryptu
*(Wprowadzonym w wersji 1710)*  
Dodawanie parametrów do skryptu zapewnia większą elastyczność do pracy. Poniżej opisano możliwości bieżącej funkcji uruchamianie skryptów z Parametry skryptu. *Ciąg*, *całkowitą* typów danych. Dostępne są również list wstępnie zdefiniowane wartości. Jeśli skrypt zawiera nieobsługiwane typy danych, zostanie wyświetlone ostrzeżenie.

W **Tworzenie skryptu** okna dialogowego, kliknij przycisk **Parametry skryptu** w obszarze **skryptu**.

Każdy z parametrów skryptu ma własne okno dialogowe dodawania dalszych szczegółów i sprawdzania poprawności.

### <a name="parameter-validation"></a>Sprawdzanie poprawności parametru

Każdy parametr w skrypcie ma **właściwości parametru skryptu** okno dialogowe umożliwiające dodawanie sprawdzania poprawności dla tego parametru. Po dodaniu weryfikacji, należy pobrać błędy podczas wprowadzania wartości dla parametru, który nie spełnia jego poprawności.

#### <a name="example-firstname"></a>Przykład: Imię

W tym przykładzie jest możliwość ustawiania właściwości parametru ciągu *imię*. Zwróć uwagę, pole opcjonalne dla **błąd niestandardowy**. To pole jest przydatne w przypadku dodawania użytkownika wskazówek dotyczących określonego pola i Twoje wskazówki dla użytkownika o ich interakcji z parametru ciągu *imię* w takim przypadku.

![Parametry skryptu — ciąg](./media/run-scripts/RS-parameters-string.png)

## <a name="script-examples"></a>Przykłady skryptów

Oto kilka przykładów ilustrujące skrypty, które można korzystać z tej funkcji.

### <a name="create-a-folder"></a>Utwórz folder

``` powershell
New-Item "c:\scripts" -type folder name
```

### <a name="create-a-file"></a>Utwórz plik

```powershell
New-Item "c:\scripts\new_file.txt" -type file name
```

### <a name="ping-a-given-computer"></a>Polecenie ping danego komputera

Ten skrypt ciąg znaków i używa go jako parametru dla *ping* operacji.

``` powershell
Param
(
 [String][Parameter(Mandatory=$True, Position=1)] $Computername
)

Ping $Computername
```

### <a name="get-battery-status"></a>Pobierz stan baterii

Ten skrypt używa usługi WMI do badania komputera w celu jego stan baterii.

``` powershell
Write-Output (Get-WmiObject -Class Win32_Battery).BatteryStatus

```

## <a name="run-a-script"></a>Uruchom skrypt

Po zatwierdzeniu skryptu mogą być uruchamiane na kolekcję, którą wybierzesz. Po rozpoczęciu wykonywania skryptu, jest uruchamiana szybko systemach o wysokim priorytecie i jest wykonywane w ciągu godziny. Zwracane są wyniki skryptu przy użyciu wiadomości wolniej, stan systemu.

1. W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.
2. W zasoby i zgodność obszar roboczy, kliknij przycisk **kolekcje urządzeń**.
3. W **kolekcje urządzeń** kliknij kolekcję urządzeń, na których chcesz uruchomić skrypt.
4. Na **Home** karcie **wszystkie systemy** kliknij przycisk **Uruchom skrypt**.
5. Na **skryptu** strony **Uruchom skrypt** kreatora wybierz skrypt z listy. Wyświetlane są tylko zatwierdzone skrypty.
6. Kliknij przycisk **dalej**, a następnie Zakończ pracę kreatora.

>[!IMPORTANT]
>Jeśli skrypt nie działa, na przykład ponieważ klienta docelowego jest wyłączone, w ciągu jednej godziny przedziale czasu, należy uruchomić je ponownie.

### <a name="target-machine-execution"></a>Wykonanie komputera docelowego
Skrypt zostanie wykonany jako *systemu* lub *komputera* konta na docelowych klientów. To konto ma ograniczony dostęp do sieci. Dostęp do systemów zdalnych i lokalizacje przez skrypt muszą mieć odpowiednio przydzielone.

## <a name="work-flow-and-monitoring"></a>Monitorowanie i przepływu pracy

Oto, jak wygląda uruchamianie skryptów jako przepływ pracy; Tworzenie, zatwierdzenia, uruchom i monitorowania.

![Uruchom skrypty — przepływ pracy](./media/run-scripts/RS-run-scripts-work-flow.png)

### <a name="script-monitoring"></a>Skrypt monitorowania

Po zainicjowaniu uruchomienie skryptu w kolekcji urządzeń, użyj poniższej procedury do monitorowania operacji. Począwszy od wersji 1710 jest jednocześnie możliwość monitorowania skryptu w czasie rzeczywistym wykonywania, a można także wrócić do raportu dla danego wykonywania Uruchom skrypt.

1. W konsoli programu Configuration Manager kliknij **monitorowanie**.
2. W **monitorowanie** obszaru roboczego kliknij **stanu skryptu**. ![Monitor skryptu — stan uruchomienia skryptu](./media/run-scripts/RS-monitoring-three-bar.png)
3. W **stanu skryptu** listy, wyświetlania wyników dla każdego skryptu uruchomionego na urządzeniach klienckich. Kod zakończenia skryptu **0** ogół wskazuje, że skrypt został uruchomiony pomyślnie.

## <a name="see-also"></a>Zobacz też

- [Konfigurowanie administracji opartej na rolach dla programu System Center Configuration Manager](../../core/servers/deploy/configure/configure-role-based-administration.md)
- [Podstawy administracji opartej na rolach](/sccm/core/understand/fundamentals-of-role-based-administration)
