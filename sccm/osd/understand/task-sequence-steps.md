---
title: "Zadania sekwencji kroki — programu Configuration Manager | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat kroków sekwencji zadań, które można dodać do sekwencji zadań programu Configuration Manager."
ms.custom: na
ms.date: 03/26/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7c888a6f-8e37-4be5-8edb-832b218f266d
caps.latest.revision: 26
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6f9e6e93fce95666503907010a5c253158c5de7c
ms.openlocfilehash: f648d7626af50d95fbaa5a7a2abd821a9c47f5d1
ms.contentlocale: pl-pl
ms.lasthandoff: 07/07/2017


---
# <a name="task-sequence-steps-in-system-center-configuration-manager"></a>Kroki sekwencji zadań w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Następujące kroki sekwencji zadań można dodać do sekwencji zadań programu Configuration Manager. Aby uzyskać informacje na temat edytowania sekwencji zadań, zobacz [Edytowanie sekwencji zadań](../deploy-use/manage-task-sequences-to-automate-tasks.md#BKMK_ModifyTaskSequence).  


##  <a name="BKMK_ApplyDataImage"></a>Zastosuj krok sekwencji zadań obraz danych  
 Krok sekwencji zadań **Zastosuj obraz danych** umożliwia skopiowanie obrazu danych na określoną partycję docelową.  

 Ten krok działa tylko w środowisku Windows PE. Nie działa on w standardowym systemie operacyjnym. Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań dotyczących tej akcji, zobacz [zmienne akcji sekwencji zadań](task-sequence-action-variables.md).  

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

 **Nazwa**  
 Zdefiniowana przez użytkownika krótka nazwa opisująca akcję wykonywaną w tym kroku.  

 **Opis**  
 Bardziej szczegółowe informacje dotyczące akcji wykonywanej w tym kroku.  

 **Pakiet obrazów**  
 Kliknij pozycję **Przeglądaj**, aby określić **pakiet obrazów**, który będzie używany przez ten krok sekwencji zadań. W oknie dialogowym **Wybieranie pakietu** wybierz pakiet, który chcesz zainstalować. Informacje dotyczące właściwości skojarzone z każdym istniejącym pakietem obrazów są wyświetlane w dolnej części okna dialogowego **Wybieranie pakietu**. Użyj listy rozwijanej, aby wybrać **obraz** do zainstalowania z wybranego **pakietu obrazów**.  

> [!NOTE]  
>  Ta akcja sekwencji zadań traktuje obraz jak plik danych i nie wykonuje konfiguracji wymaganej do uruchamiania obrazu jako systemu operacyjnego.  

 **Miejsce docelowe**  
 Określa istniejącą sformatowaną partycję i istniejący sformatowany dysk twardy, literę dysku logicznego lub nazwę zmiennej sekwencji zadań, która zawiera literę dysku logicznego.  

-   **Następnej dostępnej partycji** -Użyj dalej sekwencyjnych partycji, która ma nie zostały wcześniej celem akcji Zastosuj System operacyjny lub Zastosuj obraz danych w tej sekwencji zadań.  

-   **Określony dysk i partycja** — wybierz tę opcję **dysku** (rozpoczynający się od cyfry 0) i **partycji** (rozpoczynający się od cyfry 1).  

-   **Określona litera dysku logicznego** — określ **literę dysku** przypisaną do partycji przez środowisko Windows PE. Ta litera dysku może różnić się od litery dysku, którą przypisze nowo wdrożony system operacyjny.  

-   **Litera dysku logicznego przechowywana w zmiennej** — Określ zmienną sekwencji zadań zawiera literę dysku przypisaną do partycji przez środowisko Windows PE. Tę zmienną można zwykle ustawić w sekcji Zaawansowane w oknie dialogowym **Właściwości partycji** dla akcji sekwencji zadań **Formatuj dysk i podziel go na partycje**.  

 **Usuń całą zawartość na partycji przed zastosowaniem obrazu**  
 Określa, że wszystkie pliki na partycji docelowej zostaną usunięte przed zainstalowaniem obrazu. Jeśli nie usuniesz zawartości partycji, ten krok może służyć do zastosowania dodatkowej zawartości do wcześniej wybranej partycji.  

##  <a name="BKMK_ApplyDriverPackage"></a>Zastosuj pakiet sterowników  
 Krok sekwencji zadań **Zastosuj pakiet sterowników** umożliwia pobranie wszystkich sterowników w pakiecie sterowników i zainstalowanie ich w systemie operacyjnym Windows.

 Krok sekwencji zadań **Zastosuj pakiet sterowników** udostępnia wszystkie sterowniki urządzeń w pakiecie sterowników do użycia przez system Windows. Ten krok można dodać do sekwencji zadań między krokami **Zastosuj system operacyjny** oraz **Zainstaluj system Windows i program ConfigMgr**, aby udostępnić sterowniki urządzeń w pakiecie sterowników na potrzeby systemu Windows. Zazwyczaj krok **Zastosuj pakiet sterowników** jest umieszczany po kroku sekwencji zadań **Automatycznie zastosuj sterowniki**. Krok sekwencji zadań **Zastosuj pakiet sterowników** może być też używany w scenariuszach wdrażania nośników autonomicznych.  

 Upewnij się, że w pakiecie sterowników umieszczono podobne sterowniki urządzeń, i rozpowszechnij je w odpowiednich punktach dystrybucji. Rozpowszechnienie klientów programu Configuration Manager można zainstalować je. Można na przykład umieścić w pakiecie sterowników wszystkie sterowniki urządzeń od danego producenta, a następnie rozpowszechnić ten pakiet w punktach dystrybucji, z których skojarzone komputery mogą uzyskiwać do nich dostęp.

 Ten krok może być używany w przypadku nośników autonomicznych i przez administratorów, którzy chcą zainstalować określony zestaw sterowników — dotyczy to też sterowników urządzeń, których nie można wykryć w ramach skanowania urządzeń Plug and Play (na przykład drukarek sieciowych).  

 Ten krok sekwencji zadań działa tylko w środowisku Windows PE. Nie działa on w standardowym systemie operacyjnym. Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań dla tej akcji, zobacz [Zmienne akcji sekwencji zadań Zastosuj pakiet sterowników](task-sequence-action-variables.md#BKMK_ApplyDriverPackage).  

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

 **Nazwa**  
 Zdefiniowana przez użytkownika krótka nazwa opisująca akcję wykonywaną w tym kroku.  

 **Opis**  
 Bardziej szczegółowe informacje dotyczące akcji wykonywanej w tym kroku.  

 **Pakiet sterowników**  
 Określ pakiet sterowników zawierający wymagane sterowniki urządzeń, klikając przycisk **Przeglądaj** i uruchamiając okno dialogowe **Wybieranie pakietu**. Określ istniejący pakiet, który ma zostać udostępniony. Właściwości skojarzonego pakietu są wyświetlane u dołu okna dialogowego.  

 **Wybierz sterownik pamięci masowej w pakiecie, który musi być zainstalowany przed instalacją w systemach operacyjnych starszych niż Windows Vista**  
 Określ sterowniki urządzeń pamięci masowej niezbędne w przypadku instalacji systemów operacyjnych starszych niż Windows Vista.  

 **Sterownik**  
 Wybierz plik sterownika urządzenia pamięci masowej do zainstalowania przed instalacją we wdrożeniach systemów operacyjnych starszych niż Windows Vista. Pozycje na liście rozwijanej pochodzą z określonego pakietu.  

 **Model**  
 Określ urządzenie wymagane do rozruchu, które jest potrzebne w przypadku wdrożeń systemów operacyjnych starszych niż Windows Vista.  

 **Wykonaj instalację nienadzorowaną niepodpisanych sterowników w wersjach systemu Windows, gdy jest to dozwolone**  
 Wybierz tę opcję, aby umożliwić w systemie Windows instalację sterowników, które nie są podpisane na komputerze odniesienia.  

##  <a name="BKMK_ApplyNetworkSettings"></a>Krok Zastosuj ustawienia sieci  
 Krok sekwencji zadań **Zastosuj ustawienia sieci** pozwala określić informacje o konfiguracji sieci lub grupy roboczej na komputerze docelowym. Określone wartości są przechowywane w odpowiednim formacie pliku odpowiedzi na potrzeby Instalatora systemu Windows po uruchomieniu kroku sekwencji zadań **Zainstaluj system Windows i program ConfigMgr**.  

 Ten krok sekwencji zadań działa w standardowym systemie operacyjnym lub w środowisku Windows PE. Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań dla tej akcji, zobacz [Zmienne akcji sekwencji zadań Zastosuj ustawienia sieci](task-sequence-action-variables.md#BKMK_ApplyNetworkSettings).  

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

 **Nazwa**  
 Zdefiniowana przez użytkownika krótka nazwa opisująca akcję wykonywaną w tym kroku.  

 **Opis**  
 Bardziej szczegółowe informacje dotyczące akcji wykonywanej w tym kroku.  

 **Przyłącz do grupy roboczej**  
 Wybierz tę opcję, aby przyłączyć komputer docelowy do określonej grupy roboczej. Wprowadź nazwę grupy roboczej w wierszu **Grupa robocza**. Ta wartość może zostać przesłonięta przez wartość przechwyconą przez krok sekwencji zadań **Przechwyć ustawienia sieci**.  

 **Przyłącz do domeny**  
 Wybierz tę opcję, aby przyłączyć komputer docelowy do określonej domeny. Określ lub wyszukaj domenę, taką jak *fabricam.com*. Określ lub wyszukaj ścieżkę protokołu LDAP (Lightweight Directory Access Protocol) dla jednostki organizacyjnej (tj. LDAP//OU=computers, DC=Fabricam.com, C=com).  

 **Konta**  
 Kliknij pozycję **Ustaw**, aby określić konto z uprawnieniami przyłączania komputera do domeny. W **konta użytkownika systemu Windows** okno dialogowe, które można wprowadzić nazwę użytkownika w następującym formacie: **DOMENA\UŻYTKOWNIK** .  

 **Ustawienia karty sieciowej**  
 Określ konfigurację sieci dla każdej karty sieciowej w komputerze. Kliknij pozycję **Nowy**, aby otworzyć okno dialogowe **Ustawienia sieciowe**, a następnie określ ustawienia sieciowe. Jeśli ustawienia sieciowe zostały przechwycone w ramach poprzedniego kroku sekwencji zadań **Przechwyć ustawienia sieci**, do karty sieciowej zostaną zastosowane poprzednie ustawienia, a nie ustawienia określone w tym kroku. Jeśli ustawienia sieciowe nie zostały wcześniej przechwycone, do kart sieciowych zostaną zastosowane ustawienia określone w kroku **Zastosuj ustawienia sieci** w kolejności wyliczenia urządzeń systemu Windows.  

##  <a name="BKMK_ApplyOperatingSystemImage"></a>Zastosuj obraz systemu operacyjnego  
 Krok sekwencji zadań **Zastosuj obraz systemu operacyjnego** umożliwia zainstalowanie systemu operacyjnego na komputerze docelowym. W ramach tego kroku sekwencji zadań jest wykonywany zestaw akcji zależny od tego, czy system operacyjny jest instalowany za pomocą obrazu systemu operacyjnego czy pakietu instalacji systemu operacyjnego.  

 Gdy jest używany obraz systemu operacyjnego, w ramach kroku **Zastosuj obraz systemu operacyjnego** są wykonywane następujące akcje:  

1.  Usunięcie całej zawartości na wybranym woluminie oprócz plików znajdujących się w folderze określonym przez &#95; SMSTSUserStatePath zmienną sekwencji zadań.  

2.  Wyodrębnienie zawartości określonego pliku wim na określonej partycji docelowej.  

3.  Przygotowanie pliku odpowiedzi:  

    1.  Utworzenie nowego domyślnego pliku odpowiedzi Instalatora systemu Windows (sysprep.inf lub unattend.xml) dla wdrażanego systemu operacyjnego.  

    2.  Scalenie wszystkich wartości z pliku odpowiedzi podanego przez użytkownika.  

4.  Skopiowanie modułów ładowania rozruchu systemu Windows na aktywną partycję.  

5.  Skonfigurowanie pliku boot.ini lub bazy danych konfiguracji rozruchu (BCD) w celu utworzenia odwołania do nowo zainstalowanego systemu operacyjnego.  

 Gdy jest używany pakiet instalacji systemu operacyjnego, w ramach kroku **Zastosuj obraz systemu operacyjnego** są wykonywane następujące akcje:  

1.  Usunięcie całej zawartości na wybranym woluminie oprócz plików znajdujących się w folderze określonym przez &#95; SMSTSUserStatePath zmienną sekwencji zadań.  

2.  Przygotowanie pliku odpowiedzi:  

    1.  Tworzy nowego pliku odpowiedzi ze standardowymi wartościami utworzonymi przez program Configuration Manager.  

    2.  Scalenie wszystkich wartości z pliku odpowiedzi podanego przez użytkownika.  

> [!NOTE]  
>  Rzeczywista instalacja systemu Windows jest uruchamiana przez krok sekwencji zadań **Zainstaluj system Windows i program ConfigMgr**. Po uruchomieniu akcji sekwencji zadań **Zastosuj system operacyjny** dla zmiennej sekwencji zadań OSDTargetSystemDrive jest ustawiana litera dysku partycji zawierającej pliki systemu operacyjnego.  

 Ten krok sekwencji zadań działa tylko w środowisku Windows PE. Nie działa on w standardowym systemie operacyjnym. Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań dla tej akcji, zobacz [Zmienne akcji sekwencji zadań Zastosuj obraz systemu operacyjnego](task-sequence-action-variables.md#BKMK_ApplyOperatingSystem).  

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   **Uzyskaj dostęp do zawartości bezpośrednio z punktu dystrybucji**:  

     Ta opcja pozwala określić, czy sekwencja zadań ma uzyskiwać dostęp do obrazu systemu operacyjnego bezpośrednio z punktu dystrybucji. Można jej na przykład użyć podczas wdrażania systemów operacyjnych na urządzeniach osadzonych z ograniczoną ilością miejsca. Po wybraniu tej opcji należy również skonfigurować ustawienia udziału pakietu na karcie **Dostęp do danych** właściwości pakietu.  

    > [!NOTE]  
    >  To ustawienie przesłania opcję wdrożenia skonfigurowaną na stronie **Punkty dystrybucji** w **Kreatorze wdrażania oprogramowania** tylko w przypadku obrazu systemu operacyjnego określonego w tym kroku sekwencji zadań, a nie całej zawartości w całej sekwencji zadań.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

 **Nazwa**  
 Zdefiniowana przez użytkownika krótka nazwa opisująca akcję wykonywaną w tym kroku.  

 **Opis**  
 Bardziej szczegółowe informacje dotyczące akcji wykonywanej w tym kroku.  

 **Zastosuj system operacyjny z przechwyconego obrazu**  
 Instaluje obraz systemu operacyjnego, który został wcześniej przechwycony. Kliknij przycisk **Przeglądaj**, aby otworzyć okno dialogowe **Wybieranie pakietu**, a następnie wybierz istniejący pakiet obrazów, który chcesz zainstalować. Jeśli z danym **pakietem obrazów** skojarzono wiele obrazów, określ za pomocą listy rozwijanej skojarzony obraz, który zostanie użyty dla tego wdrożenia. Aby wyświetlić podstawowe informacje o istniejącym obrazie, kliknij ten obraz.  

 **Zastosuj obraz systemu operacyjnego z oryginalnego źródła instalacji**  
 Instaluje system operacyjny przy użyciu oryginalnego źródła instalacji. Kliknij przycisk **Przeglądaj**, aby otworzyć okno dialogowe **Wybieranie pakietu instalacji systemu operacyjnego**, a następnie wybierz istniejący pakiet instalacji systemu operacyjnego, którego chcesz użyć. Aby wyświetlić podstawowe informacje o istniejącym źródle obrazu, kliknij to źródło obrazu. Właściwości skojarzonego źródła obrazu są wyświetlane w okienku wyników u dołu okna dialogowego. Jeśli z danym pakietem skojarzono wiele wydań, określ za pomocą listy rozwijanej skojarzone **wydanie**, którego używasz.  

 **Użyj pliku odpowiedzi unattended lub sysprep do instalacji niestandardowej**  
 Ta opcja pozwala udostępnić plik odpowiedzi Instalatora systemu Windows (**unattend.xml**, **unattend.txt** lub **sysprep.inf**) w zależności od wersji i metody instalacji systemu operacyjnego. Określony plik może zawierać dowolne standardowe opcje konfiguracji obsługiwane przez pliki odpowiedzi systemu Windows. Można na przykład określić za jego pomocą domyślną stronę główną programu Internet Explorer. Musisz określić pakiet zawierający plik odpowiedzi i skojarzoną ścieżkę do pliku w pakiecie.  

> [!NOTE]  
>  Wybrany plik odpowiedzi Instalatora systemu Windows może zawierać osadzone zmienne sekwencji zadań w postaci %*nazwa_zmiennej*%, gdzie nazwa_zmiennej to nazwa zmiennej. Ciąg %*nazwa_zmiennej*% zostanie zamieniony na rzeczywiste wartości zmiennej w ramach akcji sekwencji zadań **Zainstaluj system Windows i program ConfigMgr**. Jednak takie osadzone zmienne sekwencji zadań nie mogą być używane w polach zawierających tylko liczby w pliku odpowiedzi unattend.xml.  

 Jeśli nie podasz pliku odpowiedzi Instalatora systemu Windows, ta akcja sekwencji zadań automatycznie wygeneruje plik odpowiedzi.  

 **Miejsce docelowe**  
 Określa istniejącą sformatowaną partycję i istniejący sformatowany dysk twardy, literę dysku logicznego lub nazwę zmiennej sekwencji zadań, która zawiera literę dysku logicznego.  

-   **Następnej dostępnej partycji** -Użyj dalej sekwencyjnych partycji, która ma nie zostały wcześniej celem akcji Zastosuj System operacyjny lub Zastosuj obraz danych w tej sekwencji zadań.  

-   **Określony dysk i partycja** — wybierz tę opcję **dysku** (rozpoczynający się od cyfry 0) i **partycji** (rozpoczynający się od cyfry 1).  

-   **Określona litera dysku logicznego** — określ **literę dysku** przypisaną do partycji przez środowisko Windows PE. Ta litera dysku może różnić się od litery dysku, którą przypisze nowo wdrożony system operacyjny.  

-   **Litera dysku logicznego przechowywana w zmiennej** — Określ zmienną sekwencji zadań zawiera literę dysku przypisaną do partycji przez środowisko Windows PE. Tę zmienną można zwykle ustawić w sekcji Zaawansowane w oknie dialogowym **Właściwości partycji** dla akcji sekwencji zadań **Formatuj dysk i podziel go na partycje**.  

##  <a name="BKMK_ApplyWindowsSettings"></a>Zastosuj ustawienia systemu Windows  
 Krok sekwencji zadań **Zastosuj ustawienia systemu Windows** umożliwia skonfigurowanie ustawień systemu Windows na komputerze docelowym. Określone wartości są przechowywane w odpowiednim formacie pliku odpowiedzi na potrzeby Instalatora systemu Windows po uruchomieniu kroku sekwencji zadań **Zainstaluj system Windows i program ConfigMgr**.  

 Ten krok sekwencji zadań działa tylko w środowisku Windows PE. Nie działa on w standardowym systemie operacyjnym. Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań dla tej akcji, zobacz [Zmienne akcji sekwencji zadań Zastosuj ustawienia systemu Windows](task-sequence-action-variables.md#BKMK_ApplyWindowsSettings).  

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

 **Nazwa**  
 Zdefiniowana przez użytkownika krótka nazwa opisująca akcję wykonywaną w tym kroku.  

 **Opis**  
 Bardziej szczegółowe informacje dotyczące akcji wykonywanej w tym kroku.  

 **Nazwa użytkownika**  
 Podaj nazwę zarejestrowanego użytkownika skojarzoną z komputerem docelowym. Ta wartość może zostać przesłonięta przez wartość przechwyconą przez akcję sekwencji zadań **Przechwyć ustawienia systemu Windows**.  

 **Nazwa organizacji**  
 Podaj nazwę zarejestrowanej organizacji skojarzoną z komputerem docelowym. Ta wartość może zostać przesłonięta przez wartość przechwyconą przez akcję sekwencji zadań **Przechwyć ustawienia systemu Windows**.  

 **Klucz produktu**  
 Określ klucz produktu używany na potrzeby instalacji systemu Windows na komputerze docelowym.  

 **Licencjonowanie serwera**  
 Określ tryb licencjonowania serwera. Możesz wybrać tryb licencjonowania **Na serwer** lub **Na użytkownika**. W przypadku wybrania trybu licencjonowania na serwer musisz też określić maksymalną liczbę połączeń dozwolonych dla umowy licencyjnej. Wybierz pozycję **Nie określaj**, jeśli komputer docelowy nie jest serwerem lub jeśli nie chcesz określać trybu licencjonowania.  

 **Maksymalna liczba połączeń**  
 Określ maksymalną liczbę połączeń dostępnych dla tego komputera zgodnie z zapisem w umowie licencyjnej.  

 **Losowo Generuj hasło administratora lokalnego i Wyłącz konto na wszystkich obsługiwanych platformach (zalecane)**  
 Wybierz tę opcję, aby losowo wygenerować hasło administratora lokalnego. Spowoduje to utworzenie hasła administratora lokalnego i wyłączenie konta na obsługiwanych platformach.  

 **Włącz konto i określ hasło administratora lokalnego**  
 Wybierz tę opcję, aby włączyć konto administratora lokalnego i utworzyć hasło administratora lokalnego. Wprowadź hasło w wierszu **Hasło** i potwierdź hasło w wierszu **Potwierdź hasło**.  

 **Strefa czasowa**  
 Określ strefę czasową na komputerze docelowym. Ta wartość może zostać przesłonięta przez wartość przechwyconą przez krok sekwencji zadań **Przechwyć ustawienia systemu Windows**.  

##  <a name="BKMK_AutoApplyDrivers"></a>Automatycznie Zastosuj sterowniki  
 Krok sekwencji zadań **Automatycznie zastosuj sterowniki** umożliwia dopasowanie i zainstalowanie sterowników w ramach wdrażania systemu operacyjnego.  

 W ramach kroku sekwencji zadań **Automatycznie zastosuj sterowniki** są wykonywane następujące akcje:  

1.  Zeskanowanie sprzętu i znalezienie identyfikatorów Plug and Play wszystkich urządzeń istniejących w systemie.  

2.  Wysłanie listy urządzeń i ich identyfikatorów Plug and Play do punktu zarządzania. Punkt zarządzania zwraca listę zgodnych sterowników z katalogu sterowników dla poszczególnych urządzeń. Punkt zarządzania uwzględnia wszystkie sterowniki bez względu na pakiet sterowników, w którym się znajdują. Uwzględniane są tylko sterowniki oznaczone za pomocą określonej kategorii sterowników i nie oznaczone jako wyłączone.  

3.  W przypadku każdego urządzenia klient wybiera najlepszy sterownik odpowiedni dla systemu operacyjnego, na którym jest wdrażany, i znajdujący się w dostępnym punkcie dystrybucji.  

4.  Wybrane sterowniki są pobierane z punktu dystrybucji i umieszczane w docelowym systemie operacyjnym.  

    1.  W przypadku instalacji opartych na obrazach sterowniki są umieszczane w magazynie sterowników systemu operacyjnego.  

    2.  W przypadku instalacji korzystających z instalatora w Instalatorze systemu Windows jest konfigurowana lokalizacja, w której można znaleźć sterowniki.  

5.  Po uruchomieniu akcji sekwencji zadań **Zainstaluj system Windows i program ConfigMgr** i wykonaniu pierwszego rozruchu systemu Windows zostaną znalezione sterowniki wdrożone przejściowo w ramach tej akcji.  

> [!IMPORTANT]
>  **Automatycznie Zastosuj sterowniki** krok sekwencji zadań nie może być używany z nośnikami autonomicznymi, ponieważ Instalator systemu Windows nie będzie mieć połączenia z lokacją programu Configuration Manager.

Ten krok sekwencji zadań działa tylko w środowisku Windows PE. Nie działa on w standardowym systemie operacyjnym. Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań dla tej akcji, zobacz [Zmienne akcji sekwencji zadań Automatycznie zastosuj sterowniki](task-sequence-action-variables.md#BKMK_AutoApplyDrivers).  

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

 **Nazwa**  
 Zdefiniowana przez użytkownika krótka nazwa opisująca akcję wykonywaną w tym kroku.  

 **Opis**  
 Bardziej szczegółowe informacje dotyczące akcji wykonywanej w tym kroku.  

 **Zainstaluj tylko najlepiej pasujące zgodne sterowniki**  
 Określa, że w ramach kroku sekwencji zadań jest instalowany tylko najlepiej dopasowany sterownik dla każdego wykrytego urządzenia sprzętowego.  

 **Zainstaluj wszystkie zgodne sterowniki**  
 Określa, że w ramach kroku sekwencji zadań są instalowane wszystkie zgodne sterowniki dla każdego wykrytego urządzenia sprzętowego, i umożliwia Instalatorowi systemu Windows wybranie najlepszego sterownika. Ta opcja używa więcej przepustowości sieci i miejsca na dysku, ponieważ jest pobieranych więcej sterowników, ale dzięki temu może zostać wybrany lepszy sterownik.  

 **Uwzględnij sterowniki z wszystkich kategorii**  
 Określa, że w ramach akcji sekwencji zadań odpowiednie sterowniki urządzeń są wyszukiwane we wszystkich dostępnych kategoriach sterowników.  

 **Ogranicz dopasowywanie tylko do sterowników z wybranych kategorii**  
 Określa, że w ramach akcji sekwencji zadań odpowiednie sterowniki urządzeń są wyszukiwane w określonych kategoriach sterowników.  

 **Wykonaj instalację nienadzorowaną niepodpisanych sterowników w wersjach systemu Windows, gdy jest to dozwolone**  
 Umożliwia zainstalowanie niepodpisanych sterowników urządzeń systemu Windows w ramach tej akcji sekwencji zadań.  

> [!IMPORTANT]  
>  Ta opcja nie dotyczy systemów operacyjnych, w których nie można skonfigurować zasad podpisywania sterowników.  

##  <a name="BKMK_CaptureNetworkSettings"></a>Przechwyć ustawienia sieci  
 Krok sekwencji zadań **Przechwyć ustawienia sieci** umożliwia przechwycenie ustawień sieci firmy Microsoft z komputera, na którym uruchomiono sekwencję zadań. Ustawienia są zapisywane w zmiennych sekwencji zadań, które przesłonią ustawienia domyślne skonfigurowane w kroku sekwencji zadań **Zastosuj ustawienia sieci**.  

 Ten krok sekwencji zadań działa tylko w standardowym systemie operacyjnym. Nie działa on w środowisku Windows PE. Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań dla tej akcji, zobacz [Zmienne akcji sekwencji zadań Przechwyć ustawienia sieci](task-sequence-action-variables.md#BKMK_CaptureNetworkSettings).  

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

 **Nazwa**  
 Określa zdefiniowaną przez użytkownika krótką nazwę, która opisuje akcję wykonywaną w tym kroku.  

 **Opis**  
 Zawiera bardziej szczegółowe informacje dotyczące akcji wykonywanej w tym kroku.  

 **Migruj członkostwo w domenie i grupie roboczej**  
 Przechwytuje informacje dotyczące członkostwa w domenie i grupie roboczej na komputerze docelowym.  

 **Migruj konfigurację karty sieciowej**  
 Przechwytuje konfigurację karty sieciowej komputera docelowego. Przechwycone informacje obejmują ustawienia globalne sieci, liczbę kart i ustawienia sieci skojarzone z każdą kartą. Należą do nich ustawienia związane z usługami DNS i WINS, adresami IP oraz filtrami portów.  

##  <a name="BKMK_CaptureOperatingSystemImage"></a>Przechwyć obraz systemu operacyjnego  
 Krok sekwencji zadań **Przechwyć obraz systemu operacyjnego** umożliwia przechwycenie obrazów z komputera odniesienia i zapisanie ich w pliku WIM w określonym udziale sieciowym. Aby zaimportować ten można następnie Kreatora dodawania pakietu obrazów systemu operacyjnego. Plik WIM do programu Configuration Manager, którego nie może służyć do wdrożenia na podstawie obrazu systemu operacyjnego.  

 Każdy wolumin (dysk) na komputerze odniesienia jest przechwytywany jako osobny obraz w pliku wim. Jeśli przywoływany komputer ma wiele woluminów, wynikowy plik WIM będzie zawierał osobny obraz każdego woluminu. Przechwytywane są tylko woluminy sformatowane przy użyciu systemu NTFS lub FAT32. Woluminy w innych formatach i woluminy USB są pomijane.  

 System operacyjny zainstalowany na komputerze odniesienia musi być z wersją systemu Windows, który jest obsługiwany przez program Configuration Manager i muszą zostać przygotowane za pomocą narzędzia SysPrep. Wolumin z zainstalowanym systemem operacyjnym i wolumin rozruchowy muszą być tym samym woluminem.  

 Musisz też wprowadzić konto systemu Windows, które ma uprawnienia zapisu w wybranym udziale sieciowym.  

 Ten krok sekwencji zadań działa tylko w środowisku Windows PE. Nie działa on w standardowym systemie operacyjnym. Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań dla tej akcji, zobacz [Zmienne akcji sekwencji zadań Przechwyć obraz systemu operacyjnego](task-sequence-action-variables.md#BKMK_CaptureOperatingSystemImage).  

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

 **Nazwa**  
 Zdefiniowana przez użytkownika krótka nazwa opisująca akcję wykonywaną w tym kroku.  

 **Opis**  
 Bardziej szczegółowe informacje dotyczące akcji wykonywanej w tym kroku.  

 **Docelowy**  
 Nazwa ścieżki systemu plików do lokalizacji programu Configuration Manager używa do przechowywania przechwyconego obrazu systemu operacyjnego.  

 **Opis**  
 Opcjonalny opis zdefiniowany przez użytkownika dotyczący przechwyconego obrazu systemu operacyjnego, który jest przechowywany w pliku WIM.  

 **Wersja**  
 Opcjonalny numer wersji zdefiniowany przez użytkownika, który ma zostać przypisany do przechwyconego obrazu systemu operacyjnego. Może to być dowolna kombinacja liter i cyfr. Ta wartość jest przechowywana w pliku WIM.  

 **Utworzone przez**  
 Opcjonalna nazwa użytkownika, który utworzył obraz systemu operacyjnego. Ta nazwa jest przechowywana w pliku WIM.  

 **Konto przechwytywania obrazu systemu operacyjnego**  
 Musisz wprowadzić konto systemu Windows z uprawnieniami do określonego udziału sieciowego. Kliknij pozycję **Ustaw** , aby określić nazwę tego konta systemu Windows.  

##  <a name="BKMK_CaptureUserState"></a>Przechwyć stan użytkownika  
 Krok sekwencji zadań **Przechwyć stan użytkownika** umożliwia przechwycenie za pomocą narzędzia do migracji stanu użytkowników (USMT) stanu i ustawień użytkownika z komputera, na którym uruchomiono sekwencję zadań. Ten krok sekwencji zadań jest używany razem z krokiem sekwencji zadań **Przywróć stan użytkownika**. Przy użyciu narzędzia USMT 3.0.1 i później, ta opcja zawsze szyfruje Magazyn stanów narzędzia USMT za pomocą klucza szyfrowania wygenerowanego i zarządzanego przez program Configuration Manager.  

 Aby uzyskać więcej informacji o zarządzaniu stanem użytkownika podczas wdrażania systemów operacyjnych, zobacz [Zarządzanie stanem użytkownika](../get-started/manage-user-state.md).  

 Można również użyć **Przechwyć stan użytkownika** krok sekwencji zadań z **Zażądaj magazynu stanów** i **Zwolnij Magazyn stanów** punktu kroków sekwencji zadań, aby zapisać ustawienia stanu lub przywrócenia ustawień z migracji stanu w lokacji programu Configuration Manager.  

 Krok sekwencji zadań **Przechwyć stan użytkownika** zapewnia kontrolę nad ograniczonym podzbiorem najczęściej używanych opcji narzędzia USMT. Dodatkowe opcje wiersza polecenia można określić za pomocą zmiennej sekwencji zadań OSDMigrateAdditionalCaptureOptions.  

 Ten krok sekwencji zadań działa tylko w środowisku Windows PE. Nie działa on w standardowym systemie operacyjnym. Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań dla tej akcji, zobacz [Zmienne akcji sekwencji zadań Przechwyć stan użytkownika](task-sequence-action-variables.md#BKMK_CaptureUserState).  

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

 **Nazwa**  
 Zdefiniowana przez użytkownika krótka nazwa opisująca akcję wykonywaną w tym kroku.  

 **Opis**  
 Bardziej szczegółowe informacje dotyczące akcji wykonywanej w tym kroku.  

 **Pakiet narzędzia migracji stanu użytkownika**  
 Wprowadź pakiet programu Configuration Manager, która zawiera wersję narzędzia USMT dla tego kroku sekwencji zadań do użycia podczas przechwytywania stanu i ustawień użytkownika. Ten pakiet nie wymaga programu. Gdy krok sekwencji zadań zostanie uruchomiony, sekwencja zadań użyje wersji narzędzia USMT z określonego pakietu. Określ pakiet zawierający wersję 32-bitową lub wersję x64 narzędzia USMT w zależności od architektury systemu operacyjnego, z którego jest przechwytywany stan.  

 **Przechwyć wszystkie profile użytkowników z opcjami standardowymi**  
 Wybierz tę opcję, aby przeprowadzić migrację wszystkich informacji o profilach użytkowników. Ta opcja jest domyślnie wybrana.  

 Wybierz tę opcję, ale nie zaznaczaj opcji Przywróć profile użytkowników komputera lokalnego w kroku sekwencji zadań Przywróć stan użytkownika, sekwencja zadań zakończy się niepowodzeniem, ponieważ Menedżer konfiguracji nie może migrować nowych kont bez przypisywania do nich haseł. Jeśli użyjesz kreatora **Nowa sekwencja zadań** i utworzysz sekwencję zadań **Zainstaluj istniejący pakiet obrazów**, wynikowa sekwencja zadań domyślnie użyje opcji Przechwyć wszystkie profile z użyciem opcji standardowych, ale nie wybierze opcji Przywróć profile użytkowników komputera lokalnego (konta spoza domeny).  

 Wybierz pozycję **Przywróć profile użytkowników komputera lokalnego** i podaj hasło dla konta, które chcesz migrować. W przypadku ręcznie utworzonej sekwencji zadań to ustawienie znajduje się w kroku Przywróć stan użytkownika. W przypadku sekwencji zadań utworzonej przez kreatora **Nowa sekwencja zadań** to ustawienie znajduje się na stronie kreatora dotyczącej kroku **Przywróć pliki i ustawienia użytkownika**.  

 Jeśli nie masz kont użytkowników lokalnych, to rozwiązanie nie ma zastosowania.  

 **Dostosuj sposób przechwytywania profili użytkowników**  
 Wybierz tę opcję, aby określić niestandardową migrację pliku profilu. Kliknij pozycję **Pliki**, aby wybrać pliki konfiguracji do użycia przez narzędzie USMT w ramach tego kroku. Musisz określić niestandardowy plik xml, który zawiera reguły definiujące pliki stanu użytkownika do migrowania.  

 **Kliknij tutaj, aby wybrać pliki konfiguracji:**  
 Wybierz tę opcję, aby wybrać pliki konfiguracji w pakiecie narzędzia USMT, za pomocą których chcesz przechwytywać profile użytkowników. Kliknij przycisk **Pliki**, aby otworzyć okno dialogowe **Pliki konfiguracji**. Aby określić plik konfiguracji, wprowadź nazwę pliku w wierszu **Nazwa pliku**, a następnie kliknij przycisk **Dodaj**.  

 **Włącz pełne rejestrowanie**  
 Włącz tę opcję, aby wygenerować bardziej szczegółowe informacje pliku dziennika. W przypadku przechwytywania stanu jest generowany plik Scanstate.log, który jest domyślnie przechowywany w folderze dziennika sekwencji zadań w folderze \windows\system32\ccm\logs.  

 **Pomiń pliki korzystające z systemu szyfrowania plików**  
 Włącz tę opcję, aby pominąć przechwytywanie plików zaszyfrowanych za pomocą systemu szyfrowania plików (EFS), łącznie z plikami profili. W zależności od systemu operacyjnego i wersji narzędzia USMT odczyt zaszyfrowanych plików może nie być możliwy po przywróceniu. Więcej informacji można znaleźć w dokumentacji narzędzia USMT.  

 **Kopiuj, używając dostępu do systemu plików**  
 Włącz tę opcję, aby określić dowolne z następujących ustawień:  

-   **Kontynuuj, jeśli nie można przechwycić niektórych plików**: Włącz to ustawienie, aby kontynuować proces migracji, nawet jeśli nie można przechwycić niektórych plików. Jeśli wyłączysz tę opcję i nie będzie można przechwycić pliku, krok sekwencji zadań zakończy się niepowodzeniem. Ta opcja jest domyślnie włączona.  

-   **Przechwyć lokalnie, używając łączy zamiast kopiować pliki**: Włącz to ustawienie umożliwia przechwytywanie plików, twardych linków NTFS.  

     Aby uzyskać więcej informacji na temat migrowania danych przy użyciu twardych linków, zobacz [Magazyn migracji za pomocą twardych linków](http://go.microsoft.com/fwlink/p/?LinkId=240222)  

-   **Przechwyć w trybie offline (tylko Windows PE)**: Włącz to ustawienie, aby przechwycić stan użytkownika w środowisku Windows PE zamiast pełnej wersji systemu operacyjnego.  

 **Przechwyć, używając tle usługi kopiowania woluminów (VSS)**  
 Ta opcja umożliwia przechwytywanie plików, nawet jeśli zostały one zablokowane do edycji przez inną aplikację.  

##  <a name="BKMK_CaptureWindowsSettings"></a>Przechwyć ustawienia systemu Windows  
 Krok sekwencji zadań **Przechwyć ustawienia systemu Windows** umożliwia przechwycenie ustawień systemu Windows z komputera z uruchomioną sekwencją zadań. Ustawienia są zapisywane w zmiennych sekwencji zadań, które przesłaniają ustawienia domyślne skonfigurowane w ramach kroku sekwencji zadań **Zastosuj ustawienia systemu Windows**.  

 Ten krok sekwencji zadań działa w środowisku Windows PE lub w standardowym systemie operacyjnym. Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań dla tej akcji, zobacz [Zmienne akcji sekwencji zadań Przechwyć ustawienia systemu Windows](task-sequence-action-variables.md#BKMK_CaptureWindowsSettings).  

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

 **Nazwa**  
 Zdefiniowana przez użytkownika krótka nazwa opisująca akcję wykonywaną w tym kroku.  

 **Opis**  
 Bardziej szczegółowe informacje dotyczące akcji wykonywanej w tym kroku.  

 **Migruj nazwę komputera**  
 Wybierz tę opcję, aby przechwycić nazwą komputera NetBIOS.  

 **Migrowanie zarejestrowane nazwy użytkownika i organizacji**  
 Wybierz tę opcję, aby przechwycić z komputera zarejestrowane nazwy użytkowników i organizacji.  

 **Migruj strefę czasową**  
 Wybierz tę opcję, aby przechwycić ustawienie strefy czasowej na komputerze.  

##  <a name="BKMK_CheckReadiness"></a>Sprawdź gotowość  
 Krok sekwencji zadań **Sprawdź gotowość** pozwala sprawdzić, czy komputer docelowy spełnia warunki wstępne określonego wdrożenia.  

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku. W przypadku tego kroku nie należy wybierać tego ustawienia, ponieważ w ramach kroku będą rejestrowane tylko sprawdzenia gotowości i sekwencja zadań nie zostanie zatrzymana w przypadku niepowodzenia sprawdzania.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

 **Nazwa**  
 Zdefiniowana przez użytkownika krótka nazwa opisująca akcję wykonywaną w tym kroku.  

 **Opis**  
 Bardziej szczegółowe informacje dotyczące akcji wykonywanej w tym kroku.  

 **Zapewnij minimalną ilość pamięci (MB)**  
 Wybierz to ustawienie, aby sprawdzić, czy ilość pamięci (w megabajtach) zainstalowanej w komputerze docelowym jest większa lub równa określonej wartości. Domyślnie to ustawienie jest włączone.  

 **Zapewnij minimalną szybkość procesora (MHz)**  
 Wybierz to ustawienie, aby sprawdzić, czy szybkość procesora (w MHz) zainstalowanego w komputerze docelowym jest większa lub równa określonej wartości. Domyślnie to ustawienie jest włączone.  

 **Upewnij się, minimalna ilość wolnego miejsca (MB)**  
 Wybierz to ustawienie, aby sprawdzić, czy ilość wolnego miejsca na dysku (w megabajtach) na komputerze docelowym jest większa lub równa określonej wartości.  

 **Upewnij się, że bieżący system operacyjny do odświeżenia**  
 Wybierz to ustawienie, aby sprawdzić, czy system operacyjny zainstalowany na komputerze docelowym spełnia określone wymagania. Domyślnie to ustawienie jest wybrane i ma ustawioną wartość **KLIENT**.  

##  <a name="BKMK_ConnectToNetworkFolder"></a>Połącz z folderem sieciowym  
 Akcja sekwencji zadań **Połącz z folderem sieciowym** umożliwia utworzenie połączenia z udostępnionym folderem sieciowym.  

 Ten krok sekwencji zadań działa w standardowym systemie operacyjnym lub w środowisku Windows PE. Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań dla tej akcji, zobacz [Zmienne akcji sekwencji zadań Połącz z folderem sieciowym](task-sequence-action-variables.md#BKMK_ConnecttoNetworkFolder).  

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

##  <a name="BKMK_ConvertDisktoDynamic"></a>Konwertuj dysk na dynamiczny  
 Krok sekwencji zadań **Konwertuj dysk na dynamiczny** umożliwia przekonwertowanie dysku fizycznego z dysku podstawowego na dysk dynamiczny.  

 Ten krok działa w standardowym systemie operacyjnym lub w środowisku Windows PE. Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań dla tej akcji, zobacz [Zmienne akcji sekwencji zadań Przekonwertuj dysk na dynamiczny](task-sequence-action-variables.md#BKMK_ConvertDisk).  

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

 **Nazwa**  
 Zdefiniowana przez użytkownika krótka nazwa opisująca akcję wykonywaną w tym kroku.  

 **Opis**  
 Bardziej szczegółowe informacje dotyczące akcji wykonywanej w tym kroku.  

 **Numer dysku**  
 Numer dysku fizycznego, który zostanie przekonwertowany.  

##  <a name="BKMK_DisableBitLocker"></a>Wyłącz funkcję BitLocker  
 Krok sekwencji zadań **Wyłącz funkcję BitLocker** umożliwia wyłączenie szyfrowania za pomocą funkcji BitLocker na bieżącym dysku systemu operacyjnego albo na określonym dysku. Po wykonaniu tej akcji funkcje ochrony kluczy są widoczne w postaci zwykłego tekstu na dysku twardym, ale zawartość dysku nie jest odszyfrowywana. W związku z tym ta akcja jest wykonywana niemal natychmiast.  

> [!NOTE]  
>  Szyfrowanie dysków za pomocą funkcji BitLocker umożliwia szyfrowanie zawartości woluminu dysku na niskim poziomie.  

 Jeśli masz wiele zaszyfrowanych dysków, musisz wyłączyć funkcję BitLocker na wszystkich dyskach danych przed wyłączeniem funkcji BitLocker na dysku systemu operacyjnego.  

 Ten krok działa tylko w standardowym systemie operacyjnym. Nie działa on w środowisku Windows PE.  

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

 **Nazwa**  
 Określa zdefiniowaną przez użytkownika krótką nazwę, która opisuje akcję wykonywaną w tym kroku.  

 **Opis**  
 Zawiera bardziej szczegółowe informacje dotyczące akcji wykonywanej w tym kroku.  

 **Bieżący dysk systemu operacyjnego**  
 Wyłącza funkcję BitLocker na bieżącym dysku systemu operacyjnego.  

 **Określony dysk**  
 Wyłącza funkcję BitLocker na określonym dysku. Użyj listy rozwijanej, aby określić dysk, na którym chcesz wyłączyć funkcję BitLocker.  

##  <a name="BKMK_DownloadPackageContent"></a>Pobierz zawartość pakietu  
 Użyj kroku sekwencji zadań **Pobierz zawartość pakietu**, aby pobrać dowolny z następujących typów pakietów:  

-   Obrazy systemu operacyjnego  

-   Pakiety uaktualnień systemu operacyjnego  

-   Pakiety sterowników  

-   Pakiety  

 Ten krok działa dobrze w sekwencji zadań w celu uaktualnienia systemu operacyjnego w następujących scenariuszach:  

-   Użycie pojedynczej sekwencji zadań uaktualniania działającej na platformach x86 i x64. W tym celu dodaj dwa kroki zadania **Pobierz zawartość pakietu** w grupie **Przygotowanie do uaktualnienia** z warunkami wykrywania architektury klienta i pobrania tylko odpowiedniego pakietu uaktualnienia systemu operacyjnego. Skonfiguruj tę samą zmienną dla każdego kroku **Pobierz zawartość pakietu** i użyj zmiennej ścieżki nośnika w kroku **Uaktualnij system operacyjny**.  

-   Aby odpowiedni pakiet sterowników był pobierany dynamicznie, użyj dwóch kroków **Pobierz zawartość pakietu** z warunkami wykrywania odpowiedniego typu sprzętu dla każdego pakietu sterowników. Skonfiguruj tę samą zmienną dla każdego kroku **Pobierz zawartość pakietu** i użyj zmiennej wartości **Zawartość przejściowa** w sekcji sterowników w kroku **Uaktualnij system operacyjny**.  

> [!NOTE]    
> Podczas wdrażania sekwencji zadań zawiera krok Pobierz zawartość pakietu nie zaznaczaj **Pobierz całą zawartość lokalnie przed uruchomieniem sekwencji zadań** dla **opcje wdrażania** na **punktów dystrybucji** strony Kreatora wdrażania oprogramowania.  

Ten krok działa w standardowym systemie operacyjnym lub w środowisku Windows PE. Jednak opcję, aby zapisać pakiet w pamięci podręcznej klienta programu Configuration Manager nie jest obsługiwane w środowisku WinPE.

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

 **Nazwa**  
 Określa zdefiniowaną przez użytkownika krótką nazwę, która opisuje akcję wykonywaną w tym kroku.  

 **Opis**  
 Zawiera bardziej szczegółowe informacje dotyczące akcji wykonywanej w tym kroku.  

 Ikona **Wybierz pakiet**  
 Kliknij ikonę, aby wybrać pakiet do pobrania. Po wybraniu pakietu możesz kliknąć ikonę ponownie, aby wybrać inny pakiet.  

 **Umieść w następującej lokalizacji**  
 Wybierz opcję, aby zapisać pakiet w jednej z następujących lokalizacji:  

 -   **Katalog roboczy sekwencji zadań**  

 -   **Pamięć podręczna klienta programu Configuration Manager**: Ta opcja umożliwia przechowywanie zawartości w pamięci podręcznej klientów. Dzięki temu klient może działać jako źródło pamięci podręcznej elementów równorzędnych dla innych klientów pamięci podręcznej elementów równorzędnych. Aby uzyskać więcej informacji, zobacz [przygotowanie środowiska Windows PE równorzędnej pamięci podręcznej, aby zmniejszyć ruch w sieci WAN](../get-started/prepare-windows-pe-peer-cache-to-reduce-wan-traffic.md).  

 -   **Ścieżka niestandardowa**  

 **Zapisz ścieżkę jako zmienną**  
 Ścieżkę można zapisać jako zmienną do użycia w innym kroku sekwencji zadań. Menedżer konfiguracji dodaje sufiks numeryczny do nazwy zmiennej. Na przykład jeśli określisz zmienną %*mojazawartosc*% jako zmienną niestandardową, jest to główny katalog do przechowywania przywoływanej zawartości, (która może być wiele pakietów). W przypadku odwoływania się do zmiennej, zostaną dodane do zmiennej sufiksem numerycznym. Na przykład dla pierwszego pakietu zostanie odwołujesz się do %*mojazawartosc01*zmienną %. W przypadku odwoływania się do zmiennej w kolejnych kroków, takich jak Uaktualnij System operacyjny, należy użyć %*mojazawartosc02*% lub %*mycontent03*%, gdzie numer odpowiada kolejności, w której pakiet zostanie wyświetlony w kroku.  

 **Jeśli pobieranie pakietu nie powiedzie się, kontynuuj pobieranie pozostałych pakietów na liście**  
 Wskazuje, że jeśli pobieranie pakietu nie powiedzie się, nastąpi przejście do następnego pakietu na liście i rozpoczęcie pobierania.  

##  <a name="BKMK_EnableBitLocker"></a>Włącz funkcję BitLocker  
 Krok sekwencji zadań **Włącz funkcję BitLocker** umożliwia włączenie szyfrowania za pomocą funkcji BitLocker na co najmniej dwóch partycjach dysku twardego. Pierwsza aktywna partycja zawiera kod ładowania początkowego systemu Windows. Kolejna partycja zawiera system operacyjny. Partycja ładowania początkowego musi pozostać niezaszyfrowana.  

 Krok sekwencji zadań **Wstępne inicjowanie obsługi funkcji BitLocker** umożliwia włączenie funkcji BitLocker na dysku w środowisku Windows PE. Więcej informacji znajduje się w sekcji [Wstępne aprowizowanie funkcji BitLocker](#BKMK_PreProvisionBitLocker) w tym temacie.  

> [!NOTE]  
>  Szyfrowanie dysków za pomocą funkcji BitLocker umożliwia szyfrowanie zawartości woluminu dysku na niskim poziomie.  

 Krok **Włącz funkcję BitLocker** działa tylko w standardowym systemie operacyjnym. Nie działa on w środowisku Windows PE. Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań dla tej akcji, zobacz [Zmienne akcji sekwencji zadań Włącz funkcję BitLocker](task-sequence-action-variables.md#BKMK_EnableBitLocker).  

 Aby można było uruchomić krok **Włącz funkcję BitLocker**, moduł TPM (Trusted Platform Module) musi być w następującym stanie po określeniu ustawienia **Tylko TPM**, **TPM i klucz uruchomienia na USB** lub **Moduł TPM i numer PIN**:  

-   Włączono  

-   Uaktywniony  

-   Własność dozwolona  

 Krok sekwencji zadań może ukończyć każde pozostałe inicjowanie modułu TPM, ponieważ pozostałe kroki nie wymagają obecności fizycznej ani ponownego uruchomienia. Do pozostałych kroków inicjowania modułu TPM, które w razie potrzeby można ukończyć niewidocznie w ramach kroku **Włącz funkcję BitLocker**, należą:  

-   Utworzenie pary kluczy poręczenia  

-   Utworzenie wartości autoryzacji właściciela i utworzenie depozytu w usłudze Active Directory, która musi zostać rozszerzona w celu obsługi tej wartości  

-   Przejęcie na własność  

-   Utworzenie klucza głównego magazynowania lub zresetowanie, jeśli klucz już istnieje, ale jest niezgodny  

 Jeśli krok **Włącz funkcję BitLocker** ma zaczekać na ukończenie procesu szyfrowania dysku przed przejściem do następnego kroku w sekwencji zadań, zaznacz pole wyboru **Czekaj**. Jeśli nie zaznaczysz pola wyboru **Czekaj**, proces szyfrowania dysku zostanie wykonany w tle, a sekwencja zadań przejdzie natychmiast do następnego kroku.  

 Funkcja BitLocker umożliwia szyfrowanie wielu dysków w systemie komputerowym (dysków systemu operacyjnego i dysków danych). Aby można było zaszyfrować dysk danych, system operacyjny musi być już zaszyfrowany i proces szyfrowania musi być zakończony, ponieważ funkcje ochrony kluczy dysków danych są przechowywane na dysku systemu operacyjnego. Jeśli szyfrujesz dysk systemu operacyjnego i dysk danych w ramach tego samego procesu, opcja oczekiwania musi być wybrana dla kroku, w ramach którego włączono funkcję BitLocker dla dysku systemu operacyjnego.  

 Jeśli dysk twardy jest już zaszyfrowany, ale funkcja BitLocker jest wyłączona, funkcja BitLocker ponownie włączy funkcje ochrony kluczy i zostanie ukończona niemal natychmiast. W takiej sytuacji nie musisz ponownie szyfrować dysku twardego.  

 Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań dla tej akcji, zobacz [Zmienne akcji sekwencji zadań Włącz funkcję BitLocker](task-sequence-action-variables.md#BKMK_EnableBitLocker).  

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

 **Nazwa**  
 Określa nazwę opisową tego kroku sekwencji zadań.  

 **Opis**  
 Umożliwia opcjonalnie wprowadzić opis tego kroku sekwencji zadań.  

 **Wybierz dysk do zaszyfrowania**  
 Określa dysk do zaszyfrowania. Aby zaszyfrować bieżący dysk systemu operacyjnego, wybierz pozycję **Bieżący dysk systemu operacyjnego**, a następnie skonfiguruj jedną z następujących opcji zarządzania kluczami:  

-   **Tylko TPM**: Wybierz tę opcję, aby użyć tylko modułu (TPM).  

-   **Klucz uruchomienia tylko na USB**: Wybierz tę opcję, aby użyć klucza uruchomienia przechowywanego na dysku flash USB. Jeśli wybierzesz tę opcję, funkcja BitLocker zablokuje normalny proces rozruchu do czasu podłączenia do komputera urządzenia USB zawierającego klucz uruchomienia funkcji BitLocker.  

-   **Moduł TPM i klucz uruchomienia na USB**: Wybierz tę opcję, aby użyć modułu TPM i klucza uruchomienia przechowywanego na dysku flash USB. Jeśli wybierzesz tę opcję, funkcja BitLocker zablokuje normalny proces rozruchu do czasu podłączenia do komputera urządzenia USB zawierającego klucz uruchomienia funkcji BitLocker.  

-   **Moduł TPM i numer PIN**:  Wybierz tę opcję, aby użyć modułu TPM i osobistego numeru identyfikacyjnego (PIN). Jeśli wybierzesz tę opcję, funkcja BitLocker zablokuje normalny proces rozruchu do czasu podania numeru PIN przez użytkownika.  

 Aby zaszyfrować określony dysk danych, na którym nie ma systemu operacyjnego, wybierz pozycję **Określony dysk**, a następnie wybierz dysk z listy.  

 **Wybierz miejsce utworzenia klucza odzyskiwania**  
 Aby określić miejsce tworzenia hasła odzyskiwania, wybierz pozycję **W usłudze Active Directory** w celu zdeponowania hasła w usłudze Active Directory. Jeśli wybierzesz tę opcję, będzie konieczne rozszerzenie usługi Active Directory dla tej lokacji, aby można było zapisać skojarzone informacje odzyskiwania funkcji BitLocker. Jeśli nie chcesz tworzyć hasła, wybierz pozycję **Nie twórz klucza odzyskiwania**. Jednak najlepszym rozwiązaniem jest utworzenie hasła.  

 **Poczekaj na ukończenie procesu szyfrowania dysku na wszystkich dyskach przed kontynuowanie wykonania sekwencji zadań przez funkcję BitLocker**  
 Wybierz tę opcję, aby umożliwić ukończenie szyfrowania dysków za pomocą funkcji BitLocker przed uruchomieniem następnego kroku w sekwencji zadań. W przypadku wybrania tej opcji cały wolumin dysku będzie zaszyfrowany zanim użytkownik będzie mógł zalogować się do komputera.  

 Szyfrowanie może potrwać kilka godzin w przypadku dużego dysku twardego. Jeśli nie wybierzesz tej opcji, sekwencja zadań będzie natychmiast kontynuowana.  

##  <a name="BKMK_FormatandPartitionDisk"></a>Format i partycji  
 Krok sekwencji zadań **Formatuj dysk i podziel go na partycje** umożliwia sformatowanie określonego dysku na komputerze docelowym i podzielenie go na partycje.  

> [!IMPORTANT]  
>  Każde ustawienie określone dla tego kroku sekwencji zadań dotyczy jednego określonego dysku. Jeśli chcesz sformatować inny dysk na komputerze docelowym i podzielić go na partycje, musisz dodać kolejny krok sekwencji zadań **Formatuj dysk i podziel go na partycje** do sekwencji zadań.  

 Ten krok sekwencji zadań działa tylko w środowisku Windows PE. Nie działa on w standardowym systemie operacyjnym. Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań dla tej akcji, zobacz [Zmienne akcji sekwencji zadań Formatuj dysk i podziel go na partycje](task-sequence-action-variables.md#BKMK_FormatPartitionDisk).  

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

 **Nazwa**  
 Zdefiniowana przez użytkownika krótka nazwa opisująca akcję wykonywaną w tym kroku.  

 **Opis**  
 Bardziej szczegółowe informacje dotyczące akcji wykonywanej w tym kroku.  

 **Numer dysku**  
 Numer dysku fizycznego, który zostanie sformatowany. Jest on wyznaczany w kolejności wyliczania dysków systemu Windows.  

 **Typ dysku**  
 Typ formatowanego dysku. Na liście rozwijanej są dostępne dwie opcje do wyboru:  

-   Standardowa (MBR) — główny rekord rozruchowy.  

-   GPT — tabela partycji GUID  

> [!NOTE]  
>  Jeśli zmienisz typ dysku **Standardowa (MBR)** na **GPT**, a układ partycji zawiera partycję rozszerzoną, wszystkie partycje rozszerzone i logiczne zostaną usunięte z układu. Przed zmianą typu dysku zostanie wyświetlony monit o potwierdzenie tego działania.  

 **Wolumin**  
 Szczegółowe informacji o partycji lub woluminie, które zostaną utworzone, w tym:  

-   Nazwa  

-   Pozostałe miejsce na dysku  

 Aby utworzyć nową partycję, kliknij pozycję **Nowy** w celu otwarcia okna dialogowego **Właściwości partycji**. Możesz określić typ i rozmiar partycji oraz określić, czy ma ona być partycją rozruchową. Aby zmodyfikować istniejącą partycję, kliknij partycję, którą chcesz zmodyfikować, a następnie kliknij przycisk właściwości. Więcej informacji o konfigurowaniu partycji dysków twardych można znaleźć w jednym z następujących artykułów:  

-   [Jak skonfigurować partycje dysków twardych z systemem UEFI/GPT](http://go.microsoft.com/fwlink/?LinkID=272104)  

-   [Jak skonfigurować partycje dysków twardych z systemem BIOS/MBR](http://go.microsoft.com/fwlink/?LinkId=272105)  

 Aby usunąć partycję, zaznacz partycję do usunięcia, a następnie kliknij pozycję **Usuń**.  

##  <a name="BKMK_InstallApplication"></a>Instalowanie aplikacji  
 Krok sekwencji zadań **Zainstaluj aplikację** umożliwia instalowanie aplikacji w ramach sekwencji zadań. Ten krok umożliwia zainstalowanie zestawu aplikacji określonych w kroku sekwencji zadań lub zestawu aplikacji określonych przez dynamiczną listę zmiennych sekwencji zadań. Gdy ten krok zostanie uruchomiony, instalacja aplikacji rozpocznie się natychmiast bez oczekiwania na interwał sondowania zasad.  

 Instalowane oprogramowanie musi spełniać następujące kryteria:  

-   Aplikacja musi mieć typ wdrożenia Instalator Windows lub Instalator skryptowy. Typy wdrożeń Pakiet aplikacji systemu Windows (pliki appx) nie są obsługiwane.  

-   Oprogramowanie musi być uruchamiane na lokalnym koncie systemowym, a nie na koncie użytkownika.  

-   Oprogramowanie nie może mieć interakcji z pulpitem. Oprogramowanie musi być uruchamiane w trybie dyskretnym lub nienadzorowanym.  

-   Oprogramowanie nie może samodzielnie inicjować ponownego uruchomienia. Aplikacja musi żądać ponownego uruchomienia przy użyciu standardowego kodu ponownego uruchomienia (kodu zakończenia 3010). Dzięki temu krok sekwencji zadań poprawnie obsłuży ponowne uruchomienie. Jeśli aplikacja zwróci kod zakończenia 3010, aparat sekwencji zadań wykona ponowne uruchomienie. Sekwencja zadań będzie automatycznie kontynuować działanie po ponownym uruchomieniu komputera.  

 W przypadku uruchomienia kroku **Zainstaluj aplikację** aplikacja sprawdza możliwość zastosowania reguł wymagań oraz metody wykrywania do typów wdrożeń aplikacji. Na podstawie wyników tej kontroli aplikacja instaluje odpowiedni typ wdrożenia. Jeśli typ wdrożenia zawiera zależności, zostanie obliczony zależny typ wdrożenia, który zostanie zainstalowany w ramach kroku Zainstaluj aplikację. Zależności aplikacji nie są obsługiwane w przypadku nośników autonomicznych.  

> [!NOTE]  
>  Aby można było zainstalować aplikację, która zastępuje inną aplikację, pliki zawartości zastępowanej aplikacji muszą być dostępne. W przeciwnym razie krok sekwencji zadań zakończy się niepowodzeniem. Przykład: program Microsoft Visio 2010 jest zainstalowany na kliencie lub w przechwyconym obrazie. Po uruchomieniu kroku sekwencji zadań Zainstaluj aplikację w celu zainstalowania programu Microsoft Visio 2013 pliki zawartości programu Microsoft Visio 2010 (zastępowanej aplikacji) muszą być dostępne w punkcie dystrybucji. W przeciwnym razie sekwencja zadań zakończy się niepowodzeniem. Klient lub przechwycony obraz bez zainstalowanego programu Microsoft Visio ukończy instalację programu Microsoft Visio 2013 bez sprawdzania dostępności plików zawartości programu Microsoft Visio 2010.  

> [!NOTE]
> Można użyć SMSTSMPListRequestTimeoutEnabled i listy punktów SMSTSMPListRequestTimeout wbudowane zmienne, aby włączyć i określ liczbę milisekund oczekiwania przez sekwencję zadań przed ponowną próbą zainstalowania aplikacji lub oprogramowania zaktualizować po niepowodzeniu pobrania zarządzania z usług lokalizacji. Aby uzyskać więcej informacji, zobacz [varliables wbudowanej sekwencji zadań](task-sequence-built-in-variables.md).

 Ten krok sekwencji zadań działa tylko w standardowym systemie operacyjnym. Nie działa on w środowisku Windows PE.  

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Określenie, że ten krok ma zostać ponowiony, jeśli komputer zostanie nieoczekiwanie uruchomiony ponownie. Możesz także określić liczbę ponownych prób po ponownym uruchomieniu.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

 **Nazwa**  
 Zdefiniowana przez użytkownika krótka nazwa opisująca akcję wykonywaną w tym kroku.  

 **Opis**  
 Bardziej szczegółowe informacje dotyczące akcji wykonywanej w tym kroku.  

 **Zainstaluj następujące aplikacje**  
 To ustawienie określa aplikacje, które zostaną zainstalowane w kolejności, w jakiej zostały określone.  

 Menedżer konfiguracji odfiltruje wyłączone aplikacje lub wszystkie aplikacje z poniższymi ustawieniami. Te aplikacje nie będą wyświetlane w oknie dialogowym **Wybierz aplikację do zainstalowania**.  

-   Tylko, gdy użytkownik jest zalogowany  

-   Uruchom z prawami użytkownika  

 **Zainstaluj aplikacje zgodnie z listą zmiennych dynamicznych**  
 To ustawienie określa podstawową nazwę zestawu zmiennych sekwencji zadań zdefiniowanych dla kolekcji lub komputera. Te zmienne określają aplikacje, które zostaną zainstalowane dla tej kolekcji lub tego komputera. Każda nazwa zmiennej składa się z podstawowej nazwy pospolitej i liczbowego sufiksu (zaczynając od 01). Wartość każdej zmiennej musi zawierać wyłącznie nazwę aplikacji.  

 W przypadku aplikacji do zainstalowania przy użyciu listy zmiennych dynamicznych należy włączyć następujące ustawienie na **ogólne** kartę aplikacji **właściwości** okno dialogowe: **Zezwalaj na tę aplikację do zainstalowania z akcji sekwencji zadań zainstaluj aplikację zamiast wdrażania ręcznego**  

> [!NOTE]  
>  W przypadku wdrożeń nośników autonomicznych nie można instalować aplikacji za pomocą listy zmiennych dynamicznych.  

 Na przykład w celu zainstalowania jednej aplikacji za pomocą zmiennej sekwencji zadań o nazwie AA01 określ następującą zmienną:  

|Nazwa zmiennej|Wartość zmiennej|  
|-------------------|--------------------|  
|AA01|Microsoft Office|  

 Aby zainstalować dwie aplikacje, określ następujące zmienne:  

|Nazwa zmiennej|Wartość zmiennej|  
|-------------------|--------------------|  
|AA01|Microsoft Lync|  
|AA02|Microsoft Office|  

 Na instalowaną zawartość mają wpływ następujące warunki:  

-   Jeśli wartość zmiennej zawiera informacje inne niż nazwa aplikacji, ta aplikacja nie zostanie zainstalowana i sekwencja zadań będzie kontynuować działanie.  

-   Jeśli nie zostanie znaleziona zmienna o określonej nazwie podstawowej i sufiksie „01”, aplikacje nie zostaną zainstalowane. Po wybraniu **Kontynuuj przy błędzie** na karcie Opcje kroku sekwencji zadań, sekwencja zadań ma być kontynuowana po niepowodzeniu instalacji aplikacji. Gdy to ustawienie nie zostanie wybrane, sekwencja zadań zakończy się niepowodzeniem i pozostałe aplikacje nie zostaną zainstalowane.  

 **Jeśli aplikacja nie powiedzie się, kontynuuj instalowanie pozostałych aplikacji z listy**  
 To ustawienie określa, że krok ma kontynuować działanie w przypadku niepowodzenia instalacji aplikacji. Jeśli to ustawienie zostanie określone, sekwencja zadań będzie kontynuować działanie niezależnie od zwracanych błędów instalacji. Jeśli to ustawienie nie zostanie określone i instalacja zakończy się niepowodzeniem, krok sekwencji zadań zakończy się natychmiast.  

##  <a name="BKMK_InstallDeploymentTools"></a>Instalowanie narzędzi wdrażania  
 Użyj **Zainstaluj narzędzia wdrażania** krok sekwencji zadań umożliwia zainstalowanie pakietu programu Configuration Manager zawierający narzędzia wdrażania Sysprep.  

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

 **Nazwa**  
 Zdefiniowana przez użytkownika krótka nazwa opisująca akcję wykonywaną w tym kroku.  

 **Opis**  
 Bardziej szczegółowe informacje dotyczące akcji wykonywanej w tym kroku.  

 **Pakiet programu Sysprep**  
 To ustawienie określa pakiet programu Configuration Manager zawierający narzędzia wdrażania Sysprep dla następujących systemów operacyjnych:  

-   Windows XP z dodatkiem SP3  

-   Windows XP X64 z dodatkiem SP2  

-   Windows Server 2003 SP2  

##  <a name="BKMK_InstallPackage"></a>Zainstaluj pakiet

 Krok sekwencji zadań **Zainstaluj pakiet** umożliwia zainstalowanie oprogramowania w ramach sekwencji zadań. Gdy ten krok zostanie uruchomiony, instalacja rozpocznie się natychmiast bez oczekiwania na interwał sondowania zasad.  

 Instalowane oprogramowanie musi spełniać następujące kryteria:  

-   Oprogramowanie musi być uruchamiane na lokalnym koncie systemowym, a nie na koncie użytkownika.  

-   Oprogramowanie nie może mieć interakcji z pulpitem. Oprogramowanie musi być uruchamiane w trybie dyskretnym lub nienadzorowanym.  

-   Oprogramowanie nie może samodzielnie inicjować ponownego uruchomienia. Oprogramowanie musi żądać ponownego uruchomienia przy użyciu standardowego kodu ponownego uruchomienia (kodu zakończenia 3010). Dzięki temu krok sekwencji zadań poprawnie obsłuży ponowne uruchomienie. Jeśli oprogramowanie zwróci kod zakończenia 3010, aparat sekwencji zadań wykona ponowne uruchomienie. Sekwencja zadań będzie automatycznie kontynuować działanie po ponownym uruchomieniu komputera.  

 Programy używające opcji **Uruchom najpierw inny program** w celu zainstalowania programu zależnego nie są obsługiwane w przypadku wdrażania systemu operacyjnego. Jeśli opcja **Uruchom najpierw inny program** jest włączona dla oprogramowania i program zależny został już uruchomiony na komputerze docelowym, zostanie uruchomiony program zależny i sekwencja zadań będzie kontynuować działanie. Jeśli jednak program zależny nie został jeszcze uruchomiony na komputerze docelowym, krok sekwencji zadań zakończy się niepowodzeniem.  

> [!NOTE]  
>  W centralnej lokacji administracyjnej nie ma odpowiednich zasad konfiguracji klienta, które są wymagane do włączenia agenta dystrybucji oprogramowania w trakcie wykonywania sekwencji zadań. Podczas tworzenia nośnika samodzielnego dla sekwencji zadań w centralnej lokacji administracyjnej, gdy sekwencja zadań zawiera krok **Zainstaluj pakiet**, w pliku CreateTsMedia.log może się pojawić następujący błąd:  
>   
>  `"WMI method SMS_TaskSequencePackage.GetClientConfigPolicies failed (0x80041001)"`  
>   
>  W przypadku nośnika samodzielnego zawierającego krok Zainstaluj pakiet nośnik ten należy utworzyć w lokacji głównej, na której jest włączony agent dystrybucji oprogramowania, albo dodać krok **Uruchom wiersz polecenia** przed krokiem **Zainstaluj system Windows i program ConfigMgr** oraz przed pierwszym krokiem **Zainstaluj pakiet**. Krok **Uruchom wiersz polecenia** uruchamia polecenie WMIC włączające agenta dystrybucji oprogramowania przed uruchomieniem pierwszego kroku Zainstaluj pakiet. W kroku **Uruchom wiersz polecenia** sekwencji zadań można użyć następującej składni:  
>   
>  **Wiersz polecenia**: **WMIC/Namespace:\\ccm_SoftwareDistributionClientConfig ścieżki \root\ccm\policy\machine\requestedconfig NazwaSkładnika utworzyć = "Włącz SWDist" Enabled = "true", LockSettings = "TRUE", PolicySource = "local", PolicyVersion = "1.0" SiteSettingsKey = "1" /NOINTERACTIVE**  
>   
>  Aby uzyskać więcej informacji o tworzeniu nośników autonomicznych, zobacz [tworzenia nośnika samodzielnego](../deploy-use/create-stand-alone-media.md).  

 Ten krok sekwencji zadań działa tylko w standardowym systemie operacyjnym. Nie działa on w środowisku Windows PE.  

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

 **Nazwa**  
 Zdefiniowana przez użytkownika krótka nazwa opisująca akcję wykonywaną w tym kroku.  

 **Opis**  
 Bardziej szczegółowe informacje dotyczące akcji wykonywanej w tym kroku.  

 **Zainstaluj pojedynczy pakiet oprogramowania**  
 To ustawienie określa pakiet oprogramowania programu Configuration Manager. Krok zaczeka na ukończenie instalacji.  

 **Zainstaluj pakiety oprogramowania zgodnie z listą zmiennych dynamicznych**  
 To ustawienie określa podstawową nazwę zestawu zmiennych sekwencji zadań zdefiniowanych dla kolekcji lub komputera. Te zmienne określają pakiety, które zostaną zainstalowane dla tej kolekcji lub tego komputera. Każda nazwa zmiennej składa się z podstawowej nazwy pospolitej i liczbowego sufiksu (zaczynając od 001). Wartość każdej zmiennej musi zawierać identyfikator pakietu i nazwę oprogramowania rozdzielone dwukropkiem.  

 W przypadku oprogramowania instalowanego przy użyciu listy zmiennych dynamicznych należy włączyć następujące ustawienie na **zaawansowane** kartę pakietu **właściwości** okno dialogowe: **Zezwalaj na ten program można zainstalować z sekwencji zadań pakietu instalacyjnego bez wdrożenia**  

> [!NOTE]  
>  W przypadku wdrożeń nośników autonomicznych nie można instalować pakietów oprogramowania za pomocą listy zmiennych dynamicznych.  

 Na przykład w celu zainstalowania jednego pakietu oprogramowania za pomocą zmiennej sekwencji zadań o nazwie AA001 określ następującą zmienną:  

|Nazwa zmiennej|Wartość zmiennej|  
|-------------------|--------------------|  
|AA001|CEN00054:Install|  

 Aby zainstalować trzy pakiety oprogramowania, określ następujące zmienne:  

|Nazwa zmiennej|Wartość zmiennej|  
|-------------------|--------------------|  
|AA001|CEN00054:Install|  
|AA002|CEN00107:Install Silent|  
|AA003|CEN00031:Install|  

 Na instalowaną zawartość mają wpływ następujące warunki:  

-   Jeśli wartość zmiennej nie została utworzona w poprawnym formacie lub nie określa prawidłowego identyfikatora aplikacji i prawidłowej nazwy aplikacji, instalacja oprogramowania zakończy się niepowodzeniem.  

-   Jeśli identyfikator pakietu zawiera małe litery, instalacja oprogramowania zakończy się niepowodzeniem.  

-   Jeśli nie zostanie znaleziona zmienna o określonej nazwie podstawowej i sufiksie „001”, pakiety nie zostaną zainstalowane i sekwencja zadań będzie kontynuować działanie.  

 **Jeśli instalacja pakietu oprogramowania nie powiedzie się, kontynuuj instalowanie pozostałych pakietów na liście**  
 To ustawienie określa, że krok ma kontynuować działanie w przypadku niepowodzenia instalacji pakietu oprogramowania. Jeśli to ustawienie zostanie określone, sekwencja zadań będzie kontynuować działanie niezależnie od zwracanych błędów instalacji. Jeśli to ustawienie nie zostanie określone i instalacja zakończy się niepowodzeniem, krok sekwencji zadań zakończy się natychmiast.  

##  <a name="BKMK_InstallSoftwareUpdates"></a>Instalacja aktualizacji oprogramowania  
 Krok sekwencji zadań **Zainstaluj aktualizacje oprogramowania** umożliwia zainstalowanie aktualizacji oprogramowania na komputerze docelowym. Komputer docelowy nie jest sprawdzany pod kątem dostępności odpowiednich aktualizacji oprogramowania do czasu uruchomienia tego kroku sekwencji zadań. Po uruchomieniu komputera docelowego jest oceniane pod kątem aktualizacji oprogramowania, takich jak inny klient zarządzany przez Menedżera konfiguracji. W szczególności w ramach tego kroku są instalowane tylko aktualizacje oprogramowania przeznaczone dla kolekcji, do których obecnie należy komputer.  
>  [!IMPORTANT]
>Zdecydowanie zaleca się zainstalowanie najnowszej wersji usługi Windows Update Agent dla znacznie lepszą wydajność przy użyciu kroku sekwencji zadań Zainstaluj aktualizacje oprogramowania.
>* System Windows 7 — zobacz [artykuł 3161647 bazy wiedzy](https://support.microsoft.com/kb/3161647).
>* System Windows 8 — zobacz [artykuł 3163023 bazy wiedzy](https://support.microsoft.com/kb/3163023).

 Ten krok sekwencji zadań działa tylko w standardowym systemie operacyjnym. Nie działa on w środowisku Windows PE. Aby uzyskać informacje o zmiennych sekwencji zadań dotyczących tej akcji sekwencji zadań, zobacz [Zmienne akcji sekwencji zadań Zainstaluj aktualizacje oprogramowania](task-sequence-action-variables.md#BKMK_InstallSoftwareUpdates).

 > [!NOTE]
 > Można użyć SMSTSMPListRequestTimeoutEnabled i listy punktów SMSTSMPListRequestTimeout wbudowane zmienne, aby włączyć i określ liczbę milisekund oczekiwania przez sekwencję zadań przed ponowną próbą zainstalowania aplikacji lub oprogramowania zaktualizować po niepowodzeniu pobrania zarządzania z usług lokalizacji. Aby uzyskać więcej informacji, zobacz [wbudowane zmienne sekwencji zadań](task-sequence-built-in-variables.md).

> [!NOTE]
>Na karcie opcji możesz skonfigurować tę sekwencję zadań, aby ponowić próbę, jeśli komputer zostanie nieoczekiwanie uruchomiony ponownie. Na przykład instalację aktualizacji oprogramowania, która powoduje ponowne uruchomienie komputera. Począwszy od wersji 1602 programu Configuration Manager, można skonfigurować zmienną SMSTSWaitForSecondReboot, aby określić czas (w sekundach) wstrzymania sekwencji zadań, po ponownym uruchomieniu komputera po zainstalowaniu aktualizacji oprogramowania. Aby uzyskać więcej informacji, zobacz [wbudowane zmienne sekwencji zadań](task-sequence-built-in-variables.md).

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Określenie, że ten krok ma zostać ponowiony, jeśli komputer zostanie nieoczekiwanie uruchomiony ponownie. Możesz także określić liczbę ponownych prób po ponownym uruchomieniu.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

 **Nazwa**  
 Zdefiniowana przez użytkownika krótka nazwa opisująca akcję wykonywaną w tym kroku.  

 **Opis**  
 Bardziej szczegółowe informacje dotyczące akcji wykonywanej w tym kroku.  

 **Wymagane do instalacji — obowiązkowe aktualizacje oprogramowania tylko**  
 Wybierz tę opcję, aby zainstalować wszystkie aktualizacje oprogramowania oflagowane w programie Configuration Manager jako obowiązkowe dla komputerów docelowych, które odbierają sekwencję zadań. Obowiązkowe aktualizacje oprogramowania mają zdefiniowane przez administratora terminy instalacji.  

 **Dostępne do instalacji — wszystkie aktualizacje oprogramowania**  
 Wybierz tę opcję, aby zainstalować wszystkie dostępne aktualizacje oprogramowania przeznaczonych dla kolekcji programu Configuration Manager, która odbierze sekwencję zadań. Na komputerach docelowych zostaną zainstalowane wszystkie dostępne aktualizacje oprogramowania.  

 **Oceń aktualizacje oprogramowania z wyników skanowania w pamięci podręcznej**  
Począwszy od wersji Configuration Manager 1606, można wykonać pełne skanowanie w poszukiwaniu aktualizacji oprogramowania (zamiast korzystać z buforowanych wyników skanowania). Domyślnie sekwencja zadań używa wyników buforowanych. Jeśli chcesz, aby klient łączył się z punktem aktualizacji oprogramowania w celu przetwarzania i pobierania wykazu najnowszych aktualizacji oprogramowania, możesz wyczyścić pole wyboru opcji. Tę opcję można wybrać w przypadku używania sekwencji zadań w celu [przechwytywania i kompilowania obrazu systemu operacyjnego](../deploy-use/create-a-task-sequence-to-capture-an-operating-system.md), gdy wiadomo, że oczekiwana jest duża liczba aktualizacji oprogramowania i wiele z nich ma zależności (jeśli ma to zastosowanie, pojawi się komunikat o konieczności zainstalowania produktu X przed produktem Y). Gdy wyczyścić to ustawienie i wdrożyć sekwencję zadań do dużej liczby klientów, one będzie łączyć się punkt aktualizacji oprogramowania w tym samym czasie. Może to spowodować problemy z wydajnością podczas przetwarzania i pobierania wykazu. W większości przypadków zalecamy użycie ustawienia domyślnego.

W programie Configuration Manager w wersji 1606 wprowadzono nową zmienną sekwencji zadań SMSTSSoftwareUpdateScanTimeout. Umożliwia ona kontrolę limitu czasu skanowania w celu wyszukania aktualizacji oprogramowania podczas kroku sekwencji zadań Zainstaluj aktualizacje oprogramowania. Wartość domyślna to 30 minut. Aby uzyskać więcej informacji, zobacz [wbudowane zmienne sekwencji zadań](task-sequence-built-in-variables.md).


##  <a name="BKMK_JoinDomainorWorkgroup"></a>Przyłącz do domeny lub grupy roboczej  
 Krok sekwencji zadań **Przyłącz do domeny lub grupy roboczej** umożliwia dodanie komputera docelowego do grupy roboczej lub domeny.  

 Ten krok sekwencji zadań działa tylko w standardowym systemie operacyjnym. Nie działa on w środowisku Windows PE. Aby uzyskać informacje o zmiennych sekwencji zadań dotyczących tej akcji sekwencji zadań, zobacz [Zmienne akcji sekwencji zadań Przyłącz do domeny lub grupy roboczej](task-sequence-action-variables.md#BKMK_JoinDomainWorkgroup).  

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

 **Nazwa**  
 Zdefiniowana przez użytkownika krótka nazwa opisująca akcję wykonywaną w tym kroku.  

 **Opis**  
 Bardziej szczegółowe informacje dotyczące akcji wykonywanej w tym kroku.  

 **Przyłącz do grupy roboczej**  
 Wybierz tę opcję, aby przyłączyć komputer docelowy do określonej grupy roboczej. Jeśli komputer należy obecnie do domeny, wybranie tej opcji spowoduje ponowne uruchomienie komputera.  

 **Przyłącz do domeny**  
 Wybierz tę opcję, aby przyłączyć komputer docelowy do określonej domeny.  

 Opcjonalnie można wprowadzić lub wyszukać jednostkę organizacyjną w określonej domenie, do której ma zostać przyłączony komputer. Jeśli komputer należy obecnie do innej domeny lub grupy roboczej, spowoduje to ponowne uruchomienie komputera. Jeśli komputer należy już do innej jednostki organizacyjnej, usługi Active Directory Domain Services nie zezwolą na zmianę jednostki organizacyjnej i to ustawienie zostanie zignorowane.  

 **Wprowadź konto z uprawnieniem do przyłączenia do domeny**  
 Kliknij pozycję **Ustaw**, aby wprowadzić konto i hasło z uprawnieniami do przyłączenia do domeny. Konto należy wprowadzić w następującym formacie:  

 *Domena\konto*  

## <a name="BKMK_PrepareConfigMgrClientforCapture"></a>Przygotuj klienta programu ConfigMgr do przechwycenia  
Użyj **przygotować klienta programu ConfigMgr do przechwycenia** krok, aby usunąć klienta programu Configuration Manager lub konfigurowania klienta na komputerze odniesienia, aby przygotować go do przechwycenia w ramach procesu przetwarzania obrazów.

Począwszy od programu Configuration Manager w wersji 1610 krok przygotować klienta programu ConfigMgr powoduje całkowite usunięcie klienta programu Configuration Manager, a nie tylko usunięcie informacji o kluczu. Jeśli sekwencja zadań wdrażania przechwyconego obrazu systemu operacyjnego zainstaluje nowy klient programu Configuration Manager zawsze.  

Przed 1610 wersji programu Configuration Manager w tym kroku wykonuje następujące zadania:  

-   Usunięcie sekcji właściwości konfiguracji klienta z pliku smscfg.ini w katalogu systemu Windows. Tych właściwości należą informacje specyficzne dla klienta, w tym identyfikator GUID programu Configuration Manager i inne identyfikatory klienta.  

-   Usuwa wszystkie certyfikaty komputera programu SMS lub programu Configuration Manager.  

-   Usuwa pamięci podręcznej klienta programu Configuration Manager.  

-   Wyczyszczenie przypisanej zmiennej lokacji klienta programu Configuration Manager.  

-   Usuwa wszystkie lokalne zasady programu Configuration Manager.  

-   Usuwa zaufany klucz główny dla klienta programu Configuration Manager.  

 Ten krok sekwencji zadań działa tylko w standardowym systemie operacyjnym. Nie działa on w środowisku Windows PE.  

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

 **Nazwa**  
 Zdefiniowana przez użytkownika krótka nazwa opisująca akcję wykonywaną w tym kroku.  

 **Opis**  
 Bardziej szczegółowe informacje dotyczące akcji wykonywanej w tym kroku.  

##  <a name="BKMK_PrepareWindowsforCapture"></a>Przygotuj system Windows do przechwycenia  
 Krok sekwencji zadań **Przygotuj system Windows do przechwycenia** umożliwia określenie opcji narzędzia Sysprep do użycia podczas przechwytywania obrazu systemu operacyjnego na komputerze odniesienia. Ta akcja sekwencji zadań uruchamia narzędzie Sysprep, a następnie ponownie uruchamia komputer za pomocą obrazu rozruchowego środowiska Windows PE określonego dla sekwencji zadań. Jeśli komputer odniesienia jest przyłączony do domeny, ta akcja nie zostanie ukończona pomyślnie.  

 Ten krok sekwencji zadań działa tylko w standardowym systemie operacyjnym. Nie działa on w środowisku Windows PE. Aby uzyskać informacje o zmiennych sekwencji zadań dotyczących tej akcji sekwencji zadań, zobacz [Zmienne akcji sekwencji zadań Przygotuj system Windows do przechwycenia](task-sequence-action-variables.md#BKMK_PrepareWindowsCapture).  

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

 **Nazwa**  
 Zdefiniowana przez użytkownika krótka nazwa opisująca akcję wykonywaną w tym kroku.  

 **Opis**  
 Bardziej szczegółowe informacje dotyczące akcji wykonywanej w tym kroku.  

 **Automatycznie twórz listę sterowników pamięci masowej**  
 Wybierz tę opcję, aby umożliwić narzędziu Sysprep automatyczne utworzenie listy sterowników pamięci masowej z komputera odniesienia. Ta opcja włącza opcję tworzenia sterowników pamięci masowej w pliku sysprep.inf na komputerze odniesienia. Więcej informacji na temat tego ustawienia można znaleźć w dokumentacji narzędzia Sysprep.  

 **Nie Resetuj flagi aktywacji**  
 Wybierz tę opcję, aby uniemożliwić narzędziu Sysprep resetowanie flagi aktywacji produktu.  

##  <a name="BKMK_PreProvisionBitLocker"></a>Funkcja BitLocker przed udostępnieniem  
 Krok sekwencji zadań **Wstępne inicjowanie obsługi funkcji BitLocker** umożliwia włączenie funkcji BitLocker na dysku w środowisku Windows PE. Szyfrowany jest tylko zajęty obszar dysku, dzięki czemu szyfrowanie jest znacznie szybsze. Aby zastosować opcje zarządzania kluczami, użyj kroku sekwencji zadań [Wstępne inicjowanie obsługi funkcji BitLocker](#BKMK_EnableBitLocker) po zainstalowaniu systemu operacyjnego. Ten krok działa tylko w środowisku Windows PE. Nie działa on w standardowym systemie operacyjnym.  

> [!IMPORTANT]  
>  Aby móc wstępnie zainicjować obsługę funkcji BitLocker, musisz wdrożyć system operacyjny Windows 7 lub nowszy, a na komputerze musi być obsługiwany i włączony moduł TPM.  

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

 **Nazwa**  
 Określa zdefiniowaną przez użytkownika krótką nazwę, która opisuje akcję wykonywaną w tym kroku.  

 **Opis**  
 Określa szczegółowe informacje dotyczące akcji wykonywanej w tym kroku.  

 **Zastosuj funkcję BitLocker do określonego dysku**  
 Określ dysk, dla którego chcesz włączyć funkcję BitLocker. Szyfrowany jest tylko zajęty obszar dysku.  

 **Pomiń ten krok w przypadku komputerów, które nie ma modułu TPM lub gdy moduł TPM nie jest włączona**  
 Wybierz tę opcję, aby pominąć szyfrowanie dysku, gdy sprzęt komputerowy nie obsługuje modułu TPM lub gdy moduł TPM nie jest włączony. Można jej na przykład użyć w przypadku wdrażania systemu operacyjnego na maszynie wirtualnej.  

##  <a name="BKMK_ReleaseStateStore"></a>Zwolnij Magazyn stanów  
 Krok sekwencji zadań **Zwolnij magazyn stanów** umożliwia powiadomienie punktu migracji stanu o ukończeniu akcji przechwytywania lub przywracania. Ten krok jest używany razem z krokami sekwencji zadań **Zażądaj magazynu stanów**, **Przechwyć stan użytkownika** i **Przywróć stan użytkownika** w celu przeprowadzenia migracji danych stanu użytkownika przy użyciu punktu migracji stanu i narzędzia do migracji stanu użytkowników (USMT).  

 Aby uzyskać więcej informacji o zarządzaniu stanem użytkownika podczas wdrażania systemów operacyjnych, zobacz [Zarządzanie stanem użytkownika](../get-started/manage-user-state.md).  

 Jeśli zażądano dostępu do punktu migracji stanu w celu przechwycenia stanu użytkownika w ramach kroku sekwencji zadań **Zażądaj magazynu stanów**, ten krok powiadomi punkt migracji stanu o ukończeniu procesu przechwytywania oraz o tym, że dane stanu użytkownika są dostępne do przywrócenia. Punkt migracji stanu ustawi uprawnienia kontroli dostępu dla przechwyconego stanu tak, aby dostęp do niego (tylko do odczytu) miał tylko komputer, na którym jest wykonywane przywracanie.  

 Jeśli zażądano dostępu do punktu migracji stanu w celu przechwycenia stanu użytkownika w ramach kroku sekwencji zadań **Zażądaj magazynu stanów**, ten krok powiadomi punkt migracji stanu o ukończeniu procesu przywracania. Zostaną uaktywnione wszystkie ustawienia przechowywania skonfigurowane dla punktu migracji stanu.  

> [!IMPORTANT]  
>  Najlepszym rozwiązaniem jest ustawienie pozycji **Kontynuuj przy błędzie** dla dowolnych kroków sekwencji zadań między krokami **Zażądaj magazynu stanów** i **Zwolnij magazyn stanów**, tak aby każda akcja sekwencji zadań **Zażądaj magazynu stanów** miała zgodną akcję sekwencji zadań **Zwolnij magazyn stanów**.  

 Ten krok sekwencji zadań działa tylko w standardowym systemie operacyjnym. Nie działa on w środowisku Windows PE. Aby uzyskać informacje o zmiennych sekwencji zadań dotyczących tej akcji sekwencji zadań, zobacz [Zmienne akcji sekwencji zadań Zwolnij magazyn stanów](task-sequence-action-variables.md#BKMK_ReleaseStateStore).  

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

 **Nazwa**  
 Zdefiniowana przez użytkownika krótka nazwa opisująca akcję wykonywaną w tym kroku.  

 **Opis**  
 Bardziej szczegółowe informacje dotyczące akcji wykonywanej w tym kroku.  

##  <a name="BKMK_RequestStateStore"></a>Zażądaj magazynu stanów  
 Krok sekwencji zadań **Zażądaj magazynu stanów** umożliwia zażądanie dostępu do punktu migracji stanu podczas przechwytywania stanu z komputera lub przywracania stanu na komputerze.  

 Aby uzyskać więcej informacji o zarządzaniu stanem użytkownika podczas wdrażania systemów operacyjnych, zobacz [Zarządzanie stanem użytkownika](../get-started/manage-user-state.md).  

 Krok sekwencji zadań **Zażądaj magazynu stanów** może być używany razem z krokami **Zwolnij magazyn stanów**, **Przechwyć stan użytkownika** i **Przywróć stan użytkownika** w celu przeprowadzenia migracji stanu komputera przy użyciu punktu migracji stanu i narzędzia do migracji stanu użytkowników (USMT).  

> [!NOTE]  
>  Jeśli utworzono nową rolę lokacji punktu migracji stanu (SMP), udostępnienie jej w magazynie stanów użytkowników może potrwać do godziny. Aby przyspieszyć udostępnianie tej roli, można dostosować dowolne ustawienie właściwości punktu migracji stanu w celu wyzwolenia aktualizacji pliku kontroli lokacji.  

 Ten krok sekwencji zadań działa w standardowym systemie operacyjnym i w środowisku Windows PE w przypadku narzędzia USMT w trybie offline. Aby uzyskać informacje o zmiennych sekwencji zadań dla tej akcji sekwencji zadań, zobacz [Zmienne akcji sekwencji zadań Zażądaj magazynu stanów](task-sequence-action-variables.md#BKMK_RequestState).  

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

 **Nazwa**  
 Zdefiniowana przez użytkownika krótka nazwa opisująca akcję wykonywaną w tym kroku.  

 **Opis**  
 Bardziej szczegółowe informacje dotyczące akcji wykonywanej w tym kroku.  

 **Przechwyć stan z komputera**  
 Ten krok znajduje punkt migracji stanu, który spełnia wymagania minimalne zgodnie z konfiguracją w ustawieniach punktu migracji stanu (maksymalna liczba klientów i minimalna ilość wolnego miejsca na dysku), ale nie gwarantuje, że podczas migracji stanu na dysku będzie dostępna wystarczająca ilość wolnego miejsca. Wybranie tej opcji spowoduje zażądanie dostępu do punktu migracji stanu na potrzeby przechwycenia stanu i ustawień użytkownika z komputera.  

 Jeśli lokacja programu Configuration Manager ma włączonych wiele punktów migracji stanu, ten krok sekwencji zadań znajduje punkt migracji stanu, który ma dostępnego miejsca na dysku przez wysłanie zapytania punktu zarządzania lokacji, aby uzyskać listę punktów migracji stanu i ocenę każdego z nich do czasu znalezienia punktu, który spełnia minimalne wymagania.  

 **Przywróć stan z innego komputera**  
 Wybierz tę opcję, aby zażądać dostępu do punktu migracji stanu na potrzeby przywrócenia przechwyconych wcześniej stanu i ustawień użytkownika na komputerze docelowym.  

 Jeśli witryna programu Configuration Manager zawiera wiele punktów migracji stanu, ten krok sekwencji zadań znajduje punkt migracji stanu ze stanem komputera przechowywanym na komputerze docelowym.  

 **Liczba ponownych prób**  
 Liczba prób znalezienia odpowiedniego punktu migracji stanu przez ten krok sekwencji zadań, po której krok zakończy się niepowodzeniem.  

 **Opóźnienie ponowienia próby (w sekundach)**  
 Czas oczekiwania (w sekundach) kroku sekwencji zadań między ponownymi próbami.  

 **Jeśli konto komputera nie może nawiązać połączenia z magazynem stanów, użyj konta dostępu do sieci.**  
 Określa, że poświadczenia konta dostępu do sieci programu Configuration Manager będzie służyć do połączenia z punktem migracji stanu, jeśli klient programu Configuration Manager nie może uzyskać dostępu do magazynu stanu przy użyciu konta komputera. Ta opcja jest mniej bezpieczna, ponieważ inne komputery mogą uzyskać dostęp do przechowywanego stanu za pomocą konta dostępu do sieci, ale może być wymagana, jeśli komputer docelowy nie jest przyłączony do domeny.  

##  <a name="BKMK_RestartComputer"></a>Uruchom ponownie komputer  
 Krok sekwencji zadań **Uruchom ponownie komputer** umożliwia ponowne uruchomienie komputera, na którym działa sekwencja zadań. Po ponownym uruchomieniu komputer automatycznie przejdzie do następnego kroku w sekwencji zadań.  

 Ten krok działa w standardowym systemie operacyjnym lub w środowisku Windows PE. Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań dotyczących tej akcji sekwencji zadań, zobacz [ponowne uruchomienie zmienne akcji sekwencji zadań komputera](task-sequence-action-variables.md#BKMK_RestartComputer).  

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

 **Nazwa**  
 Zdefiniowana przez użytkownika krótka nazwa opisująca akcję wykonywaną w tym kroku.  

 **Opis**  
 Bardziej szczegółowe informacje dotyczące akcji wykonywanej w tym kroku.  

 **Obraz rozruchowy przypisany do tej sekwencji zadań**  
 Wybierz tę opcję na komputerze docelowym, aby użyć obrazu rozruchowego przypisanego do sekwencji zadań. Obraz rozruchowy zostanie użyty do uruchomienia kolejnych kroków sekwencji zadań działających w środowisku Windows PE.  

 **Aktualnie zainstalowany domyślny system operacyjny**  
 Wybierz tę opcję na komputerze docelowym, aby uruchomić ponownie komputer za pomocą zainstalowanego systemu operacyjnego.  

 **Powiadom użytkownika przed ponownym uruchomieniem**  
 Wybierz tę opcję, aby wyświetlić powiadomienie dla użytkownika o tym, że komputer zostanie ponownie uruchomiony. Ta opcja jest domyślnie wybrana.  

 **Komunikat z powiadomieniem**  
 Wprowadź komunikat z powiadomieniem, który będzie wyświetlany u użytkownika przed ponownym uruchomieniem komputera docelowego.  

 **Limit czasu wyświetlania komunikatu**  
 Określ ilość czasu w sekundach, po upływie którego komputer docelowy użytkownika zostanie ponownie uruchomiony. Domyślna ilość czasu to sześćdziesiąt (60) sekund.  

##  <a name="BKMK_RestoreUserState"></a>Przywróć stan użytkownika  
 Krok sekwencji zadań **Przywróć stan użytkownika** umożliwia zainicjowanie narzędzia do migracji stanu użytkowników (USMT) w celu przywrócenia stanu i ustawień użytkownika na komputerze docelowym. Ten krok sekwencji zadań jest używany razem z krokiem sekwencji zadań **Przechwyć stan użytkownika**.  

 Aby uzyskać więcej informacji o zarządzaniu stanem użytkownika podczas wdrażania systemów operacyjnych, zobacz [Zarządzanie stanem użytkownika](../get-started/manage-user-state.md).  

 Można również użyć **Przywróć stan użytkownika** krok sekwencji zadań z **Zażądaj magazynu stanów** i **Zwolnij Magazyn stanów** punktu kroków sekwencji zadań, aby zapisać ustawienia stanu lub przywrócenia ustawień z migracji stanu w lokacji programu Configuration Manager. Z narzędzia USMT 3.0 lub nowszego ta opcja zawsze odszyfrowuje Magazyn stanów narzędzia USMT za pomocą klucza szyfrowania wygenerowanego i zarządzanego przez program Configuration Manager.  

 Krok sekwencji zadań **Przywróć stan użytkownika** zapewnia kontrolę nad ograniczonym podzbiorem najczęściej używanych opcji narzędzia USMT. Dodatkowe opcje wiersza polecenia można określić za pomocą zmiennej sekwencji zadań OSDMigrateAdditionalRestoreOptions.  

> [!IMPORTANT]  
>  Jeśli używasz kroku sekwencji zadań **Przywróć stan użytkownika** w celu niezwiązanym ze scenariuszem wdrażania systemu operacyjnego, dodaj krok sekwencji zadań [Uruchom ponownie komputer](#BKMK_RestartComputer) bezpośrednio po kroku sekwencji zadań **Przywróć stan użytkownika**.  

 Ten krok sekwencji zadań działa tylko w standardowym systemie operacyjnym. Nie działa on w środowisku Windows PE. Aby uzyskać informacje o zmiennych sekwencji zadań dla tej akcji sekwencji zadań, zobacz [Zmienne akcji sekwencji zadań Przywróć stan użytkownika](task-sequence-action-variables.md#BKMK_RestoreUserState).  

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

 **Nazwa**  
 Określa zdefiniowaną przez użytkownika krótką nazwę, która opisuje akcję wykonywaną w tym kroku.  

 **Opis**  
 Określa bardziej szczegółowe informacje dotyczące akcji wykonywanej w tym kroku.  

 **Pakiet narzędzia migracji stanu użytkownika**  
 Wprowadź pakiet programu Configuration Manager, która zawiera wersję narzędzia USMT dla tego kroku do użycia podczas przywracania stanu i ustawień użytkownika. Ten pakiet nie wymaga programu. Gdy krok sekwencji zadań zostanie uruchomiony, sekwencja zadań użyje wersji narzędzia USMT z określonego pakietu. Określ pakiet zawierający wersję 32-bitową lub wersję x64 narzędzia USMT w zależności od architektury systemu operacyjnego, w którym jest przywracany stan.  

 **Przywróć wszystkie przechwycone profile użytkowników z opcjami standardowymi**  
 Przywraca przechwycone profile użytkowników z opcjami standardowymi. Aby dostosować opcje, które zostaną przywrócone, wybierz pozycję **Dostosuj przechwytywanie profili użytkowników**.  

 **Dostosuj sposób przywracania profili użytkowników**  
 Umożliwia dostosowanie plików, które mają zostać przywrócone na komputerze docelowym. Kliknij pozycję **Pliki**, aby określić pliki konfiguracji w pakiecie narzędzia USMT, za pomocą których zostaną przywrócone profile użytkowników. Aby dodać plik konfiguracji, wprowadź nazwę pliku w polu **Nazwa pliku**, a następnie kliknij przycisk **Dodaj**. Pliki konfiguracji, które będą używane na potrzeby operacji, zostaną wyświetlone w okienku Pliki. Określony plik xml definiuje plik użytkownika, który zostanie przywrócony.  

 **Przywróć profile użytkowników komputera lokalnego**  
 Przywraca profile użytkowników komputera lokalnego (nie użytkowników domeny). Musisz przypisać nowe hasła do przywróconych kont użytkowników lokalnych, ponieważ nie można migrować oryginalnych haseł kont użytkowników lokalnych. Wprowadź nowe hasło w polu **Hasło** i potwierdź hasło w polu **Potwierdź hasło**.  

 **Kontynuuj, jeśli nie można przywrócić niektórych plików**  
 Kontynuuje przywracanie stanu i ustawień użytkownika, nawet jeśli nie można przywrócić niektórych plików. Ta opcja jest domyślnie włączona. Jeśli wyłączysz tę opcję i podczas przywracania plików zostaną napotkane błędy, krok sekwencji zadań zakończy się natychmiast z powodu błędu i nie wszystkie pliki zostaną przywrócone.  

 **Włącz pełne rejestrowanie**  
 Włącz tę opcję, aby wygenerować bardziej szczegółowe informacje pliku dziennika. W przypadku przywracania stanu jest generowany plik Loadstate.log, który jest domyślnie przechowywany w folderze dziennika sekwencji zadań w folderze \windows\system32\ccm\logs.  

##  <a name="BKMK_RunCommandLine"></a>Uruchom wiersz polecenia  
 Krok sekwencji zadań **Uruchom wiersz polecenia** umożliwia uruchomienie określonego wiersza polecenia.  

 Ten krok działa w standardowym systemie operacyjnym lub w środowisku Windows PE. Aby uzyskać informacje o zmiennych sekwencji zadań dotyczących tej akcji sekwencji zadań, zobacz [Zmienne akcji sekwencji zadań Uruchom wiersz polecenia](task-sequence-action-variables.md#BKMK_RunCommand).  

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

 **Nazwa**  
 Określa zdefiniowaną przez użytkownika krótką nazwę opisującą uruchamiany wiersz polecenia.  

 **Opis**  
 Określa bardziej szczegółowe informacje dotyczące uruchamianego wiersza polecenia.  

 **Wiersz polecenia**  
 Określa uruchamiany wiersz polecenia. To pole jest wymagane. Najlepszym rozwiązaniem, na przykład vbs i .exe jest tym rozszerzeń nazw plików. Uwzględnij wszystkie wymagane pliki ustawień, opcje wiersza polecenia i przełączniki.  

 Jeśli nazwa pliku nie ma określone rozszerzenie nazwy pliku, programu Configuration Manager prób .com, .exe i. bat. Jeśli nazwa pliku ma rozszerzenie, które nie jest plikiem wykonywalnym, programu Configuration Manager spróbuje zastosować skojarzenie lokalne. Na przykład jeśli wiersz polecenia to plik readme.gif, programu Configuration Manager uruchomi aplikację określoną na komputerze docelowym w celu otwierania plików GIF.  

 Przykłady:  

 **Setup.exe /a**  

 **cmd.exe /c copy sty98.dat c:\sales\Jan98.dat**  

> [!NOTE]  
>  Akcje wiersza polecenia, takie jak przekierowywanie danych wyjściowych, przesyłanie potokowe lub kopiowanie, tak jak w poprzednim przykładzie, musi być poprzedzona **cmd.exe /c** polecenie do uruchomienia pomyślnie.  

 **Wyłączyć przekierowania systemu plików 64-bitowych**  
 Domyślnie w przypadku uruchomienia w 64-bitowym systemie operacyjnym plik wykonywalny podany w wierszu polecenia jest wyszukiwany i uruchamiany za pomocą przekierowania systemu plików WOW64, dzięki czemu można znaleźć 32-bitowe wersje plików wykonywanych i bibliotek DLL systemu operacyjnego.  Wybranie tej opcji wyłącza użycie przekierowania systemu plików WOW64, dzięki czemu można znaleźć 64-bitowe wersje plików wykonywanych i bibliotek DLL systemu operacyjnego.  Wybranie tej opcji nie ma znaczenia w przypadku uruchamiania w systemie 32-bitowym.  

 **Rozpocznij w**  
 Określa folder z plikiem wykonywalnym programu (do 127 znaków). Ten folder może być ścieżką bezwzględną na komputerze docelowym lub ścieżką względną do folderu punktu dystrybucji, który zawiera pakiet. To pole jest opcjonalne.  

 Przykłady:  

 **c:\OfficeXP**  

 **I386**  

> [!NOTE]  
>  Przycisk **Przeglądaj** umożliwia wyszukanie plików i folderów na komputerze lokalnym, dlatego każdy wybrany w ten sposób element musi również istnieć na komputerze docelowym w tej samej lokalizacji oraz pod tą samą nazwą pliku i folderu.  

 **Pakiet**  
 Po określeniu plików lub programów w wierszu polecenia, który nie ma jeszcze na komputerze docelowym, wybierz tę opcję, aby określić pakiet programu Configuration Manager, który zawiera odpowiednie pliki. Ten pakiet nie wymaga programu. Ta opcja nie jest wymagana, jeśli określone pliki znajdują się na komputerze docelowym.  

 **Limit czasu**  
 Określa, że wartość, która reprezentuje czas programu Configuration Manager zezwala wiersza polecenia do uruchomienia. Ta wartość może być od 1 do 999 minut. Wartość domyślna to 15 minut.  

 Ta opcja jest domyślnie wyłączona.  

> [!IMPORTANT]  
>  Jeśli wprowadzisz wartość, która nie umożliwia pomyślnego ukończenia kroku sekwencji zadań Uruchom wiersz polecenia, krok sekwencji zadań zakończy się niepowodzeniem i cała sekwencja zadań może się nie powieść w zależności od innych ustawień kontroli. Po przekroczeniu limitu czasu program Configuration Manager zakończy proces wiersza polecenia.  

 **Uruchom ten krok jako następujące konto**  
 Określa, że wiersz polecenia ma być uruchamiany przy użyciu konta użytkownika systemu Windows innego niż lokalne konto systemowe.  

> [!NOTE]  
>  Jeśli określisz inne konto dla tego kroku i nastąpi to po kroku instalacji systemu operacyjnego, musisz dodać to konto na komputerze, aby można było uruchomić proste skrypty lub polecenia, a w przypadku uruchamiania bardziej złożonych programów, takich jak instalator MSI, musisz przywrócić konto użytkownika systemu Windows.  

 **Konta**  
 Określa konto Uruchom jako użytkownika systemu Windows na potrzeby zadania wiersza polecenia w sekwencji zadań, która ma zostać uruchomiona przez tę akcję. Wiersz polecenia zostanie uruchomiony z uprawnieniami określonego konta. Kliknij pozycję **Ustaw**, aby określić konto użytkownika lokalnego lub domeny.  

> [!IMPORTANT]  
>  Jeśli akcja sekwencji zadań **Uruchom wiersz polecenia** określająca konto użytkownika jest wykonywana w środowisku Windows PE, zakończy się niepowodzeniem, ponieważ nie można przyłączyć środowiska Windows PE do domeny. Błąd zostanie zarejestrowany w pliku smsts.log.  

##  <a name="BKMK_RunPowerShellScript"></a>Uruchom skrypt programu PowerShell  
 Krok sekwencji zadań **Uruchom skrypt programu PowerShell** umożliwia uruchomienie określonego skryptu programu PowerShell.  

 Ten krok działa w standardowym systemie operacyjnym lub w środowisku Windows PE. Aby można było uruchomić t en krok w środowisku Windows PE, program Power Shell musi być włączony w obrazie rozruchowym. Program Windows PowerShell (WinPE-PowerShell) można włączyć na karcie **Składniki opcjonalne** we właściwościach obrazu rozruchowego. Aby uzyskać więcej informacji o modyfikowaniu obrazu rozruchowego, zobacz [zarządzanie obrazami rozruchowymi](../get-started/manage-boot-images.md).  

> [!NOTE]  
>  Program PowerShell nie jest domyślnie włączony w systemach operacyjnych Windows Embedded.  

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

 **Nazwa**  
 Określa zdefiniowaną przez użytkownika krótką nazwę opisującą uruchamiany wiersz polecenia.  

 **Opis**  
 Określa bardziej szczegółowe informacje dotyczące uruchamianego wiersza polecenia.  

 **Pakiet**  
 Określ pakiet programu Configuration Manager, który zawiera skrypt programu PowerShell. Jeden pakiet może zawierać wiele skryptów programu PowerShell.  

 **Nazwa skryptu**  
 Określa nazwę skryptu programu PowerShell, który ma zostać uruchomiony. To pole jest wymagane.  

 **Parametry**  
 Określa parametry do przekazania do skryptu programu Windows PowerShell. Skonfiguruj parametry tak, jakby były dodawane do skryptu programu Windows PowerShell z wiersza polecenia.  

> [!IMPORTANT]  
>  Podaj parametry używane przez skrypt, a nie parametry wiersza polecenia programu Windows PowerShell.  
>   
>  Poniżej przedstawiono przykład zawierający prawidłowe parametry:  
>   
>  **-Mój_parametr_1 Moja_wartość_1-Mój_parametr_2 Moja_wartość_2**  
>   
>  Poniżej przedstawiono przykład zawierający nieprawidłowe parametry. Elementy pogrubione to parametry wiersza polecenia programu Windows PowerShell (-nologo i - executionpolicy unrestricted) i nie są używane przez skrypt.  
>   
>  **-nologo-executionpolicy unrestricted plik Mój_skrypt.ps1-Mój_parametr_1 Moja_wartość_1-Mój_parametr_2 Moja_wartość_2**  

 **Zasady wykonywania programu PowerShell**  
 Wybranie zasad wykonywania programu PowerShell pozwala określić, które skrypty programu Windows PowerShell (jeśli takie istnieją) mogą być uruchamiane na komputerze. Wybierz jedną z następujących zasad wykonywania:  

-   **Wszystkie podpisane**: Można uruchamiać tylko skrypty podpisane przez zaufanego wydawcę.  

-   **Niezdefiniowany**: Zdefiniowano zasad wykonywania. .  

-   **Obejście**: Ładuje wszystkie pliki konfiguracji i uruchamia wszystkie skrypty. Jeśli uruchomisz niepodpisany skrypt pobrany z Internetu, przed jego uruchomieniem nie zostanie wyświetlony monit dotyczący uprawnienia.  

> [!IMPORTANT]  
>  Program PowerShell 1.0 nie obsługuje zasad wykonywania Niezdefiniowane i Obejście.  

##  <a name="BKMK_SetDynamicVariables"></a>Ustaw zmienne dynamiczne  
 Krok sekwencji zadań **Ustaw zmienne dynamiczne** umożliwia wykonywanie następujących czynności:  

1.  Zebranie informacji z komputera i środowiska, w którym się znajduje, a następnie ustawienie tych informacji w określonych zmiennych sekwencji zadań.  

2.  Obliczenie zdefiniowanych reguł i ustawienie zmiennych sekwencji zadań na podstawie zmiennych i wartości skonfigurowanych dla reguł, które zwrócą wartość true.  

 Sekwencja zadań automatycznie ustawia następujące zmienne sekwencji zadań tylko do odczytu:  

 -   &#95; SMSTSMake  

 -   &#95; SMSTSModel  

 -   &#95; SMSTSMacAddresses  

 -   &#95; SMSTSIPAddresses  

 -   &#95; SMSTSSerialNumber  

 -   &#95; SMSTSAssetTag  

 -   &#95; SMSTSUUID  

 Ten krok działa w standardowym systemie operacyjnym lub w środowisku Windows PE. Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań, zobacz [zmienne akcji sekwencji zadań](task-sequence-action-variables.md).  

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

**Nazwa**  
 Zdefiniowana przez użytkownika krótka nazwa tego kroku sekwencji zadań.  

**Opis**  
 Bardziej szczegółowe informacje dotyczące akcji wykonywanej w tym kroku.  

**Dynamiczne reguły i zmienne**  
 Aby ustawić zmienną dynamiczną do użycia w sekwencji zadań, możesz dodać regułę, a następnie ustawić wartość dla każdej zmiennej określonej dla reguły albo dodać co najmniej jedną zmienną do ustawienia bez dodawania reguły. Możesz dodać regułę z jednej z następujących kategorii:  

 -   **Komputer**: Użyj ta kategoria reguł pozwala obliczyć wartości tagu zasobu, identyfikatora UUID, numer seryjny lub adres mac. Możesz ustawić wiele wartości, a jeśli którakolwiek z nich będzie mieć wartość true, reguła zwróci wartość true. Na przykład poniższa reguła zwraca wartość true, jeśli numer seryjny to 5892087, niezależnie od tego, czy adres MAC to 26-78-13-5A-A4-22.  

     `IF Serial Number = 5892087 OR MAC address = 26-78-13-5A-A4-22 THEN`  

-   **Lokalizacja**: Ta kategoria reguł pozwala obliczyć wartości bramy domyślnej.  

-   **Producent i Model**: Użyj ta kategoria reguł pozwala obliczyć wartości producenta i modelu komputera. Aby reguła mogła zwrócić wartość true, producent i model muszą zwrócić wartość true.   

    Począwszy od programu Configuration Manager 1610 wersji, można określić znak gwiazdki (*) i znak zapytania (**?**) jako symbole wieloznaczne, gdzie *** odpowiada wielu znaków i **?** reprezentuje pojedynczy znak. Na przykład ciąg "DELL * 900?" będzie odpowiadała DELL-ABC-9001 i DELL9009.

-   **Zmienna sekwencji zadań**: Ta kategoria reguł umożliwia dodawanie zmiennej sekwencji zadań, warunek i wartość do obliczenia. Reguła zwraca wartość true, gdy ustawiona wartość zmiennej spełnia określony warunek.  

Możesz określić co najmniej jedną zmienną do ustawienia dla reguły, która zwróci wartość true, lub ustawić zmienne bez używania reguły. Możesz użyć istniejących zmiennych lub utworzyć zmienną niestandardową.  

 -   **Istniejące zmienne sekwencji zadań**: Użyj tego ustawienia, aby wybrać co najmniej jedną zmienną z listy istniejących zmiennych sekwencji zadań. Nie można wybierać zmiennych tablicy.  

 -   **Niestandardowe zmienne sekwencji zadań**: To ustawienie umożliwia zdefiniowanie niestandardowej zmiennej sekwencji zadań. Można również określić istniejącą zmienną sekwencji zadań. Dzięki temu można określić istniejącą tablicę zmiennych, taką jak OSDAdapter, ponieważ tablic zmiennych nie ma na liście istniejących zmiennych sekwencji zadań.  

Po wybraniu zmiennych reguły musisz podać wartość każdej zmiennej. Dla zmiennej jest ustawiana określona wartość, gdy reguła zwraca wartość true. Dla każdej zmiennej można wybrać ustawienie **Wartość tajna**, aby ukryć wartość zmiennej. Domyślnie niektóre istniejące zmienne, takie jak zmienna sekwencji zadań OSDCaptureAccountPassword, ukrywają wartości.  

> [!IMPORTANT]  
>  W przypadku importowania sekwencji zadań z krokiem Ustaw zmienne dynamiczne i wybrania pozycji **Wartość tajna** dla wartości zmiennej wartość zostanie usunięta po zaimportowaniu sekwencji zadań. Dlatego musisz ponownie wprowadzić wartość zmiennej dynamicznej po zaimportowaniu sekwencji zadań.  

##  <a name="BKMK_SetTaskSequenceVariable"></a>Ustaw zmienną sekwencji zadań  
 Krok sekwencji zadań **Ustaw zmienną sekwencji zadań** umożliwia ustawienie wartości zmiennej używanej w sekwencji zadań.  

 Ten krok działa w standardowym systemie operacyjnym lub w środowisku Windows PE. Zmienne sekwencji zadań są odczytywane przez akcje sekwencji zadań i określają działanie tych akcji. Aby uzyskać więcej informacji na temat określonych zmiennych sekwencji zadań, zobacz [zmienne akcji sekwencji zadań](task-sequence-action-variables.md).  

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

 **Nazwa**  
 Zdefiniowana przez użytkownika krótka nazwa tego kroku sekwencji zadań.  

 **Opis**  
 Bardziej szczegółowe informacje dotyczące akcji wykonywanej w tym kroku.  

 **Zmienną sekwencji zadań**  
 Zdefiniowana przez użytkownika nazwa zmiennej sekwencji zadań.  

 **Wartość**  
 Wartość skojarzona ze zmienną sekwencji zadań. Może to być inna zmienna sekwencji zadań określona za pomocą składni %<nazwa zmiennej\>%.  

##  <a name="BKMK_SetupWindowsandConfigMgr"></a>Zainstaluj system Windows i program ConfigMgr  
 Krok sekwencji zadań **Zainstaluj system Windows i program ConfigMgr** umożliwia przejście ze środowiska Windows PE do nowego systemu operacyjnego. Ten krok sekwencji zadań stanowi wymaganą część każdego wdrożenia systemu operacyjnego. Go instaluje klienta programu Configuration Manager w nowym systemie operacyjnym i przygotowuje sekwencję zadań kontynuować wykonywanie w nowym systemie operacyjnym.  

 Ten krok działa tylko w środowisku Windows PE. Nie działa on w standardowym systemie operacyjnym. Aby uzyskać więcej informacji o zmiennych sekwencji zadań dotyczących tej akcji sekwencji zadań, zobacz [zmienne akcji sekwencji zadań Zainstaluj system Windows i program ConfigMgr](task-sequence-action-variables.md#BKMK_SetupWindows).  

 **Zainstaluj system Windows i program ConfigMgr** akcji sekwencji zadań zamienia zmienne katalogów pliku sysprep.inf lub unattend.xml, takie jak % WINDIR % i % ProgramFiles %, na katalog instalacyjny środowiska Windows PE X:\Windows. Zmienne sekwencji zadań określone przy użyciu tych zmiennych środowiskowych zostaną zignorowane.  

 Ten krok sekwencji zadań umożliwia wykonywanie następujących czynności:  

1.  Czynności wstępne: Windows PE  

    1.  Wykonuje podstawienie zmiennej sekwencji zadań w pliku unattend.xml.  

    2.  Pobranie pakietu zawierającego klienta programu Configuration Manager i umieszczenie go we wdrożonym obrazie.  

2.  Instalowanie systemu Windows  

    1.  Instalacja wykonywana przy użyciu obrazu.  

        1.  Wyłączenie klienta programu Configuration Manager w obrazie (czyli wyłącza automatyczne uruchamianie usługi klienta Configuration Manager).  

        2.  Zaktualizowanie rejestru wdrożonego obrazu, aby wdrożony system operacyjny był uruchamiany przy użyciu tej samej litery dysku, która jest używana na komputerze odniesienia.  

        3.  Ponowne uruchomienie wdrożonego systemu operacyjnego.  

        4.  Miniinstalacja systemu Windows jest uruchamiana za pomocą wcześniej określonego pliku sysprep.inf lub unattend.xml, który zawiera wszystkie pominięte interakcje użytkownika końcowego. Uwaga: Jeśli **Zastosuj ustawienia sieci** określony w celu przyłączenia do domeny, te informacje są w pliku sysprep.inf lub unattend.xml, a miniinstalacji systemu Windows jest wykonywane przyłączanie do domeny.  

    2.  Instalacja wykonywana przy użyciu pliku Setup.exe.  Uruchamia plik Setup.exe, który wykonuje typowy proces instalacji systemu Windows:  

        1.  Skopiowanie pakietu instalacyjnego systemu operacyjnego określonego we wcześniejszej sekwencji zadań **Zastosuj system operacyjny** na dysku twardym.  

        2.  Ponowne uruchomienie nowo wdrożonego systemu operacyjnego.  

        3.  Miniinstalacja systemu Windows jest uruchamiana za pomocą wcześniej określonego pliku sysprep.inf lub unattend.xml, który zawiera wszystkie pominięte ustawienia interfejsu użytkownika. Uwaga: Jeśli **Zastosuj ustawienia sieci** określony w celu przyłączenia do domeny, te informacje są w pliku sysprep.inf lub unattend.xml, a miniinstalacji systemu Windows jest wykonywane przyłączanie do domeny.  

3.  Konfigurowanie klienta programu Configuration Manager  

    1.  Po zakończeniu miniinstalacji systemu Windows sekwencja zadań zostaje wznowiona przy użyciu polecenia setupcomplete.cmd.  

    2.  Włączenie lub wyłączenie konta administratora lokalnego w zależności od opcji wybranej w ramach kroku **Zastosuj ustawienia systemu Windows**.  

    3.  Instaluje klienta programu Configuration Manager przy użyciu pobranego wcześniej pakietu (1.b) i właściwości instalacji określonych w edytorze sekwencji zadań. Klient zostanie zainstalowany w trybie obsługi, aby uniemożliwić przetwarzanie nowych żądań zasad do czasu ukończenia sekwencji zadań.  

    4.  Oczekiwanie na uzyskanie pełnej funkcjonalności klienta.  

    5.  Jeśli komputer działa w środowisku z włączoną ochroną dostępu do sieci, klient wyszukuje i instaluje wszystkie wymagane aktualizacje, dzięki czemu wszystkie wymagane aktualizacje są obecne przed kontynuowaniem działania sekwencji zadań.  

4.  Sekwencja zadań przechodzi do następnego kroku.  

> [!NOTE]  
>  Akcja sekwencji zadań **Zainstaluj systemu Windows i program ConfigMgr** odpowiada za uruchamianie zasad grupy na nowo zainstalowanym komputerze. Zasady grupy są stosowane po zakończeniu sekwencji zadań.  

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Jeśli ustawienie jest niewybrane, sekwencja zadań będzie kontynuowana w przypadku wystąpienia błędu podczas wykonywania kroku. Jeśli wystąpi błąd, sekwencja zadań zakończy się niepowodzeniem niezależnie od tego, czy to ustawienie jest wybrane.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

 **Nazwa**  
 Określa zdefiniowaną przez użytkownika krótką nazwę, która opisuje akcję wykonywaną w tym kroku.  

 **Opis**  
 Określa dodatkowe informacje dotyczące akcji wykonywanej w tym kroku.  

 **Pakiet klienta**  
 Określa pakiet instalacyjny klienta programu Configuration Manager, który będzie używany przez ten krok sekwencji zadań. Kliknij przycisk **Przeglądaj** i wybierz pakiet instalacyjny klienta, którego chcesz użyć do zainstalowania klienta programu Configuration Manager.  

 **Użyj pakietu przedprodukcyjnego klienta, jeśli jest dostępny**  
 Określa, że jeśli pakiet przedprodukcyjny klienta jest dostępny, podczas wykonywania kroku sekwencji zadań zostanie użyty ten pakiet, a nie pakiet produkcyjny klienta. Zazwyczaj klient przedprodukcyjny to nowsza wersja testowana w środowisku produkcyjnym. Kliknij przycisk **Przeglądaj** i wybierz pakiet instalacyjny klienta przedprodukcyjnego, którego chcesz użyć do zainstalowania klienta programu Configuration Manager.  

 **Właściwości instalacji**  
 Przypisanie lokacji i konfiguracja domyślna są automatycznie określane przez akcję sekwencji zadań. W tym polu można określić dodatkowe właściwości instalacji, które mają być używane podczas instalacji klienta. Aby wprowadzić wiele właściwości instalacji, oddziel je spacjami.  

 Możesz określić opcje wiersza polecenia, których chcesz użyć podczas instalacji klienta. Na przykład można wprowadzić polecenie **/skipprereq: silverlight.exe** w celu nakazania programowi CCMSetup.exe, aby nie instalował wstępnie wymaganego programu Microsoft Silverlight. Aby uzyskać więcej informacji o dostępnych opcjach wiersza polecenia programu CCMSetup.exe, zobacz [o właściwościach instalacji klienta](../../core/clients/deploy/about-client-installation-properties.md).  

##  <a name="BKMK_UpgradeOS"></a>Uaktualnij System operacyjny  
 Użyj kroku sekwencji zadań **Uaktualnij system operacyjny**, aby uaktualnić istniejący system operacyjny Windows 7, Windows 8, Windows 8.1 i Windows 10 do wersji Windows 10.  

 Ten krok sekwencji zadań działa tylko w standardowym systemie operacyjnym. Nie działa on w środowisku Windows PE.  

### <a name="details"></a>Szczegóły  
 Na karcie **Właściwości** tego kroku można skonfigurować ustawienia opisane w tej sekcji.  

 Jest też dostępna karta **Opcje**, która umożliwia wykonywanie następujących czynności:  

-   Wyłączenie kroku.  

-   Określenie, czy sekwencja zadań ma kontynuować działanie w przypadku wystąpienia błędu podczas wykonywania kroku.  

-   Określenie warunków, które muszą zostać spełnione, aby można było wykonać krok.  

 **Nazwa**  
 Zdefiniowana przez użytkownika krótka nazwa opisująca akcję wykonywaną w tym kroku.  

 **Opis**  
 Bardziej szczegółowe informacje dotyczące akcji wykonywanej w tym kroku.  

 **Pakiet uaktualnienia**  
 Wybierz tę opcję, aby określić pakiet uaktualniający systemu operacyjnego Windows 10 do użycia podczas uaktualniania.  

 **Ścieżka źródłowa**  
 Określa lokalną lub sieciową ścieżkę do nośnika systemu Windows 10, który ma zostać użyty (odpowiada opcji wiersza polecenia/installFrom). Można również określić zmienną, taką jak %moja_ścieżka_zawartości% lub %DPC01%. Aby używać zmiennej w ścieżce źródłowej, należy wcześniej określić tę zmienną w sekwencji zadań. Jeśli na przykład używasz kroku [Pobierz zawartość pakietu](#BKMK_DownloadPackageContent) w sekwencji zadań, możesz określić zmienną lokalizacji pakietu uaktualniającego systemu operacyjnego. Następnie można użyć tej zmiennej dla ścieżki źródłowej danego kroku.  

 **Edition**  
 Określ wersję w ramach nośnika systemu operacyjnego do użycia podczas uaktualniania.  

 **Klucz produktu**  
 Określ klucz produktu do zastosowania podczas procesu uaktualniania  

 **Podaj poniższą zawartość sterowników w Instalatorze systemu Windows podczas uaktualniania**  
 Wybierz to ustawienie, aby dodać sterowniki do komputera docelowego podczas procesu uaktualniania (odpowiada opcji wiersza polecenia /InstallDriver). Sterowniki muszą być zgodne z systemem Windows 10. Określ jedną z następujących opcji:  

-   **Pakiet sterowników**: Kliknij przycisk **Przeglądaj** i wybierz istniejący pakiet sterowników z listy.  

-   **Zawartość przejściowa**:  Wybierz tę opcję, aby określić lokalizację pakietu sterowników. Możesz wybrać folder lokalny, ścieżkę sieciową lub zmienną sekwencji zadań. Aby używać zmiennej w ścieżce źródłowej, należy wcześniej określić tę zmienną w sekwencji zadań. Na przykład za pomocą kroku [Pobierz zawartość pakietu](task-sequence-steps.md#BKMK_DownloadPackageContent).  

 **Limit czasu (w minutach)**  
 Określa liczbę minut, przez które Instalator ma uruchomić, zanim programu Configuration Manager zakończy się niepowodzeniem, krok sekwencji zadań.  

 **Skanowanie zgodności Instalatora systemu Windows bez rozpoczynania uaktualnienia**  
 Określa, że skanowanie zgodności Instalatora systemu Windows ma się odbyć bez uruchamiania procesu uaktualniania (odpowiada opcji wiersza polecenia /Compat ScanOnly). Po wybraniu tej opcji nadal należy wdrożyć całe źródło instalacji. Instalator zwraca kod zakończenia w wyniku skanowania. Poniższa tabela zawiera niektóre z najczęściej używanych kodów zakończenia.  

|Kod zakończenia|Szczegóły|  
|-|-|  
|MOSETUP_E_COMPAT_SCANONLY (0xC1900210)|Brak problemów ze zgodnością („powodzenie”).|  
|MOSETUP_E_COMPAT_INSTALLREQ_BLOCK (0xC1900208)|Problemy ze zgodnością możliwości podejmowania działań.|  
|MOSETUP_E_COMPAT_MIGCHOICE_BLOCK (0xC1900204)|Wybrana opcja migracji jest niedostępna, na przykład uaktualnienie wersji Enterprise do Professional.|  
|MOSETUP_E_COMPAT_SYSREQ_BLOCK (0xC1900200)|Brak uprawnień w przypadku systemu Windows 10.|  
|MOSETUP_E_COMPAT_INSTALLDISKSPACE_BLOCK (0xC190020E)|Brak wystarczającej ilości wolnego miejsca na dysku.|  

 Aby uzyskać więcej informacji o tym parametrze, zobacz [Windows Setup Command-Line Options](https://msdn.microsoft.com/library/windows/hardware/dn938368\(v=vs.85\).aspx) (Opcje wiersza polecenia Instalatora systemu Windows)  

 **Ignoruj wszystkie komunikaty o zgodności możliwe do odrzucenia**  
 Określa, że Instalator ukończy instalację, ignorując wszystkie możliwe do odrzucenia komunikaty o zgodności (odpowiada opcji wiersza polecenia /Compat IgnoreWarning).  

 **Dynamicznie Aktualizuj Instalatora systemu Windows z usługi Windows Update**  
 Określa, czy Instalator będzie wykonywać operacje aktualizacji dynamicznych, takie jak wyszukiwanie, pobieranie i instalowanie aktualizacji (odpowiada opcji wiersza polecenia /DynamicUpdate). To ustawienie nie jest zgodny z aktualizacji oprogramowania programu Configuration Manager, ale można ją włączyć w przypadku obsługi aktualizacji za pomocą usługi WSUS (autonomicznie) lub usługi Windows Update.  

 **Zastąpienia zasad i użyj domyślnej usługi Microsoft Update**: Wybierz to ustawienie, aby tymczasowo zastąpić zasady lokalne w czasie rzeczywistym w celu uruchomienia aktualizacji dynamicznych i pobrania aktualizacji z witryny Windows Update na komputerze.  

