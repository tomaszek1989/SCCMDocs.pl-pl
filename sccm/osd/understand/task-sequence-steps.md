---
title: "Kroki sekwencji zadań"
titleSuffix: Configuration Manager
description: "Więcej informacji na temat kroków sekwencji zadań, które można dodać do sekwencji zadań programu Configuration Manager."
ms.custom: na
ms.date: 01/12/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7c888a6f-8e37-4be5-8edb-832b218f266d
caps.latest.revision: 
caps.handback.revision: 
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 158817547d40f09fb8bd30ebedd5aea6420a8571
ms.sourcegitcommit: aee9ac45c15f27d8cf827890edcae94c03f5fd5e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2018
---
# <a name="task-sequence-steps-in-system-center-configuration-manager"></a>Kroki sekwencji zadań w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Następujące kroki sekwencji zadań można dodać do sekwencji zadań programu Configuration Manager. Aby uzyskać informacje na temat edytowania sekwencji zadań, zobacz [Edytowanie sekwencji zadań](../deploy-use/manage-task-sequences-to-automate-tasks.md#BKMK_ModifyTaskSequence).  

Następujące ustawienia są wspólne dla wszystkich kroków sekwencji zadań:

Na **właściwości** karty:
 - **Nazwa**: Edytor sekwencji zadań wymaga określenia krótką nazwę opisującą ten krok. Po dodaniu nowego krok edytora sekwencji zadań ustawia nazwę typu domyślnie. **Nazwa** długość nie może przekraczać 50 znaków.
 - **Opis elementu**: Opcjonalnie określ bardziej szczegółowych informacji dotyczących tego kroku. **Opis** długość nie może przekraczać 256 znaków.
Dalszej części tego artykułu opisano inne ustawienia na **właściwości** kartę dla każdego kroku sekwencji zadań.

Na **opcje** karty:  
-   **Wyłącz ten krok**: Sekwencja zadań pominie ten krok, gdy jest uruchamiany na komputerze. Ikona ten krok jest nieaktywna w edytorze sekwencji zadań. 
-   **Kontynuuj przy błędzie**: Sekwencja zadań będzie nadal występować, jeśli wystąpi błąd podczas wykonywania kroku.  
-   **Dodaj warunek**: Sekwencja zadań ocenia te warunkowe instrukcje, aby określić, czy go uruchamia krok.   
W sekcjach poniżej kroków sekwencji zadań określone opisano inne ustawienia możliwe na **opcje** kartę.



##  <a name="BKMK_ApplyDataImage"></a>Zastosuj obraz danych   
 Ten krok umożliwia skopiowanie obrazu danych na określoną partycję docelową.  

 Ten krok działa tylko w środowisku Windows PE. Nie działa on w standardowym systemie operacyjnym. Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań, zobacz [zmienne akcji sekwencji zadań](task-sequence-action-variables.md).  

W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **obrazów**i wybierz **Zastosuj obraz danych** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości  
 Na **właściwości** karta dla tego kroku, skonfigurować ustawienia opisane w tej sekcji.  

 **Pakiet obrazów**  
 Kliknij przycisk **Przeglądaj** do określenia **Pakiet obrazów** używany przez tę sekwencję zadań. W oknie dialogowym **Wybieranie pakietu** wybierz pakiet, który chcesz zainstalować. Informacje dotyczące właściwości skojarzone z każdym istniejącym pakietem obrazów są wyświetlane w dolnej części okna dialogowego **Wybieranie pakietu**. Użyj listy rozwijanej, aby wybrać **obraz** do zainstalowania z wybranego **pakietu obrazów**.  

> [!NOTE]  
>  Tej akcji sekwencji zadań traktuje obraz jak plik danych. Ta akcja nie wykonywać żadnej konfiguracji do uruchamiania obrazu jako systemu operacyjnego.  

 **Miejsce docelowe**  
 Skonfiguruj jeden z następujących opcji:

-   **Następnej dostępnej partycji**: Użyj następnej partycji sekwencyjnych który **Zastosuj System operacyjny** lub **Zastosuj obraz danych** akcji w tej sekwencji zadań nie ma już docelowe.  

-   **Określony dysk i partycja**: Wybierz **dysku** (rozpoczynający się od cyfry 0) i **partycji** (rozpoczynający się od cyfry 1).  

-   **Określona litera dysku logicznego**: Określ **literę dysku** przypisaną do partycji przez środowisko Windows PE. Ta litera dysku może różnić się od litery dysku, który przypisze nowo wdrożony system operacyjny.  

-   **Litera dysku logicznego przechowywana w zmiennej**: Określ zmienną sekwencji zadań zawiera literę dysku przypisaną do partycji przez środowisko Windows PE. Ta zmienna jest zwykle ustawić w sekcji Zaawansowane **właściwości partycji** okno dialogowe **Format i partycji** akcji sekwencji zadań.  

**Usuń całą zawartość na partycji przed zastosowaniem obrazu**  
 Określa, że sekwencja zadań Usuwa wszystkie pliki na partycji docelowej przed zainstalowaniem obrazu. Jeśli nie usuniesz zawartości partycji, ten krok może służyć do zastosowania dodatkowej zawartości do wcześniej wybranej partycji.  



##  <a name="BKMK_ApplyDriverPackage"></a>Zastosuj pakiet sterowników  
 Ten krok umożliwia pobranie wszystkich sterowników w pakiecie sterowników i zainstalowanie ich w systemie operacyjnym.

 Krok sekwencji zadań **Zastosuj pakiet sterowników** udostępnia wszystkie sterowniki urządzeń w pakiecie sterowników do użycia przez system Windows. Dodaj ten krok między **Zastosuj System operacyjny** i **Zainstaluj system Windows i program ConfigMgr** kroki, aby udostępnić sterowniki w pakiecie do systemu Windows. Zazwyczaj krok **Zastosuj pakiet sterowników** jest umieszczany po kroku sekwencji zadań **Automatycznie zastosuj sterowniki**. Krok sekwencji zadań **Zastosuj pakiet sterowników** może być też używany w scenariuszach wdrażania nośników autonomicznych.  

 Upewnij się, że w pakiecie sterowników umieszczono podobne sterowniki urządzeń, i rozpowszechnij je w odpowiednich punktach dystrybucji. Po ich dystrybucji klientów programu Configuration Manager można zainstalować je. Na przykład umieścić w pakiecie sterowników wszystkie sterowniki z jednego producenta. Następnie rozpowszechnić ten pakiet do punktów dystrybucji, których skojarzone komputery mogą uzyskiwać do nich dostęp.

 **Zastosuj pakiet sterowników** kroku jest przydatne w przypadku nośników autonomicznych. W tym kroku jest również przydatne, jeśli chcesz zainstalować określony zestaw sterowników. Te sterowniki typy urządzeń, które nie są wykrywane podczas skanowania typu plug and play, na przykład drukarek sieciowych.  

 Ten krok sekwencji zadań działa tylko w środowisku Windows PE. Nie działa on w standardowym systemie operacyjnym. Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań dla tej akcji, zobacz [Zmienne akcji sekwencji zadań Zastosuj pakiet sterowników](task-sequence-action-variables.md#BKMK_ApplyDriverPackage).  

W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **sterowniki**i wybierz **zastosuj pakiet sterowników** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości  
 Na **właściwości** karta dla tego kroku, skonfigurować ustawienia opisane w tej sekcji.  

 **Pakiet sterowników**  
 Określ pakiet sterowników zawierający wymagane sterowniki urządzeń, klikając przycisk **Przeglądaj** i uruchamiając okno dialogowe **Wybieranie pakietu**. Określ istniejący pakiet, który ma zostać udostępniony. Właściwości skojarzonego pakietu są wyświetlane u dołu okna dialogowego.  

 **Wybierz sterownik pamięci masowej w pakiecie, który musi być zainstalowany przed instalacją w systemach operacyjnych starszych niż Windows Vista**  
 Określ sterowniki pamięci masowej niezbędne do zainstalowania klasycznego systemu operacyjnego.  

 **Sterownik**  
 Wybierz plik sterownika pamięci masowej do zainstalowania przed instalacją systemu operacyjnego klasycznego. Wypełnia listy rozwijanej z określonego pakietu.  

 **Model**  
 Określ urządzenie wymagane do rozruchu, które jest potrzebne w przypadku wdrożeń systemów operacyjnych starszych niż Windows Vista.  

 **Wykonaj instalację nienadzorowaną niepodpisanych sterowników w wersjach systemu Windows, gdy jest to dozwolone**  
 Ta opcja umożliwia systemu Windows zainstalować sterowniki bez podpisu cyfrowego.  



##  <a name="BKMK_ApplyNetworkSettings"></a>Zastosuj ustawienia sieci   
 Ten krok umożliwia określenie informacji o konfiguracji sieci lub grupy roboczej na komputerze docelowym. Sekwencja zadań przechowuje te wartości w pliku odpowiedzi odpowiednie. Instalator systemu Windows używa tego pliku odpowiedzi podczas **Zainstaluj system Windows i program ConfigMgr** akcji.  

 Ten krok sekwencji zadań działa w standardowym systemie operacyjnym lub w środowisku Windows PE. Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań dla tej akcji, zobacz [Zmienne akcji sekwencji zadań Zastosuj ustawienia sieci](task-sequence-action-variables.md#BKMK_ApplyNetworkSettings).  

 W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **ustawienia**i wybierz **Zastosuj ustawienia sieci** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości  
 Na **właściwości** karta dla tego kroku, skonfigurować ustawienia opisane w tej sekcji.  

 **Przyłącz do grupy roboczej**  
 Wybierz tę opcję, aby przyłączyć komputer docelowy do określonej grupy roboczej. Wprowadź nazwę grupy roboczej w wierszu **Grupa robocza**. Ta wartość może zostać przesłonięta przez wartość przechwyconą przez krok sekwencji zadań **Przechwyć ustawienia sieci**.  

 **Przyłącz do domeny**  
 Wybierz tę opcję, aby przyłączyć komputer docelowy do określonej domeny. Określ lub wyszukaj domenę, taką jak *fabricam.com*. Określ lub wyszukaj ścieżkę dostępu protokołu LDAP (Lightweight Directory) dla jednostki organizacyjnej. Na przykład: *LDAP / / OU = computers, DC=Fabricam.com, C = com*  

 **Konta**  
 Kliknij pozycję **Ustaw**, aby określić konto z uprawnieniami przyłączania komputera do domeny. W **konta użytkownika systemu Windows** okno dialogowe, które można wprowadzić nazwę użytkownika w następującym formacie: **DOMENA\UŻYTKOWNIK**.  

 **Ustawienia karty sieciowej**  
 Określ konfigurację sieci dla każdej karty sieciowej w komputerze. Kliknij pozycję **Nowy**, aby otworzyć okno dialogowe **Ustawienia sieciowe**, a następnie określ ustawienia sieciowe. Jeśli używasz również **Przechwyć ustawienia sieci** kroku sekwencji zadań dotyczy przechwyconych wcześniej ustawienia karty sieciowej. Sekwencja zadań nie ma zastosowania ustawień, które określisz w tym kroku. Jeśli sekwencja zadań wcześniej nie przechwytuje ustawienia sieci, stosuje się ustawienia określone w **Zastosuj ustawienia sieci** kroku. Sekwencja zadań stosuje następujące ustawienia dla kart sieciowych w kolejności wyliczenia urządzeń systemu Windows.  



##  <a name="BKMK_ApplyOperatingSystemImage"></a>Zastosuj obraz systemu operacyjnego  

> [!TIP]  
> Począwszy od systemu Windows 10 w wersji 1709, nośnikami wiele wersji. Podczas konfigurowania sekwencji zadań w celu za pomocą pakietu uaktualnienia systemu operacyjnego lub obrazu systemu operacyjnego, należy wybrać [obsługiwana wersja](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-as-a-client).

 Ten krok należy zainstalować system operacyjny na komputerze docelowym. Ten krok wykonuje czynności w zależności od tego, czy używa obrazu systemu operacyjnego lub pakietu uaktualnienia systemu operacyjnego.  

 **Zastosuj obraz systemu operacyjnego** krok wykonuje następujące czynności, korzystając z obrazu systemu operacyjnego:  

1.  Usuń całą zawartość na docelowym woluminie, z wyjątkiem plików w folderze &#95; Określa SMSTSUserStatePath zmiennej.

2.  Wyodrębnij zawartość określonego pliku wim do na określoną partycję docelową.  

3.  Przygotowanie pliku odpowiedzi:  

    1.  Utwórz nowy domyślny Instalatora systemu Windows plik odpowiedzi (sysprep.inf lub unattend.xml) dla systemu operacyjnego, który jest wdrażany.  

    2.  Scal wszystkie wartości z pliku odpowiedzi podanego przez użytkownika.  

4.  Skopiuj ładowarki rozruchu systemu Windows na aktywną partycję.  

5.  Ustaw pliku boot.ini lub bazy danych konfiguracji rozruchu (BCD) do odwołania nowo zainstalowanego systemu operacyjnego.  

 **Zastosuj obraz systemu operacyjnego** krok wykonuje następujące czynności w przypadku korzystania z pakietu uaktualnienia systemu operacyjnego:  

1.  Usuń całą zawartość na docelowym woluminie, z wyjątkiem plików w folderze &#95; Określa SMSTSUserStatePath zmiennej.  

2.  Przygotowanie pliku odpowiedzi:  

    1.  Tworzenie nowego pliku odpowiedzi ze standardowymi wartościami utworzonymi przez program Configuration Manager.  

    2.  Scal wszystkie wartości z pliku odpowiedzi podanego przez użytkownika.  

> [!NOTE]  
>  **Zainstaluj system Windows i program ConfigMgr** krok uruchamia proces instalacji systemu Windows. 

 Po **Zastosuj System operacyjny** uruchomieniu akcji OSDTargetSystemDrive zmienna jest ustawiona na literę dysku partycji zawierającej pliki systemu operacyjnego.  

 Ten krok sekwencji zadań działa tylko w środowisku Windows PE. Nie działa on w standardowym systemie operacyjnym. Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań dla tej akcji, zobacz [Zmienne akcji sekwencji zadań Zastosuj obraz systemu operacyjnego](task-sequence-action-variables.md#BKMK_ApplyOperatingSystem).  

 W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **obrazów**i wybierz **Zastosuj obraz systemu operacyjnego** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości  
 Na **właściwości** karta dla tego kroku, skonfigurować ustawienia opisane w tej sekcji.  

 **Zastosuj system operacyjny z przechwyconego obrazu**  
 Instaluje obraz systemu operacyjnego, który został wcześniej przechwycony. Kliknij przycisk **Przeglądaj**, aby otworzyć okno dialogowe **Wybieranie pakietu**, a następnie wybierz istniejący pakiet obrazów, który chcesz zainstalować. Jeśli wiele obrazów są skojarzone z określonym **Pakiet obrazów**, użyj listy rozwijanej, aby określić skojarzonego obrazu do użycia dla tego wdrożenia. Aby wyświetlić podstawowe informacje o istniejącym obrazie, kliknij ten obraz.  

 **Zastosuj obraz systemu operacyjnego z oryginalnego źródła instalacji**  
 Instaluje system operacyjny przy użyciu oryginalnego źródła instalacji. Kliknij przycisk **Przeglądaj** otworzyć **Select i pakietu instalacji systemu operacyjnego** okno dialogowe. Następnie wybierz istniejący pakiet uaktualnienia systemu operacyjnego, który ma być używany. Aby wyświetlić podstawowe informacje o istniejącym źródle obrazu, kliknij to źródło obrazu. Właściwości skojarzonego źródła obrazu są wyświetlane w okienku wyników u dołu okna dialogowego. Jeśli z danym pakietem skojarzono wiele wydań, określ za pomocą listy rozwijanej skojarzone **wydanie**, którego używasz.  

 **Użyj pliku odpowiedzi unattended lub sysprep do instalacji niestandardowej**  
 Ta opcja pozwala udostępnić plik odpowiedzi Instalatora systemu Windows (**unattend.xml**, **unattend.txt** lub **sysprep.inf**) w zależności od wersji i metody instalacji systemu operacyjnego. Określony plik może zawierać dowolne standardowe opcje konfiguracji obsługiwane przez pliki odpowiedzi systemu Windows. Można na przykład określić za jego pomocą domyślną stronę główną programu Internet Explorer. Określ pakiet, który zawiera plik odpowiedzi i skojarzoną ścieżkę do pliku w pakiecie.  

> [!NOTE]  
>  Systemu Windows, należy podać plik odpowiedzi Instalatora może zawierać osadzone zmienne sekwencji zadań w formie %*nazwa_zmiennej*%, gdzie *nazwa_zmiennej* to nazwa zmiennej. **Zainstaluj system Windows i program ConfigMgr** krok zastępuje %*nazwa_zmiennej*% ciągów na rzeczywiste wartości zmiennej. Nie można używać tych osadzone zmienne sekwencji zadań w polach zawierających tylko w pliku odpowiedzi unattend.xml.  

 Jeśli nie podasz pliku odpowiedzi Instalatora systemu Windows, ta akcja sekwencji zadań automatycznie generuje plik odpowiedzi.  

 **Miejsce docelowe**  
 Skonfiguruj jeden z następujących opcji:  

-   **Następnej dostępnej partycji**: Użyj następnej partycji sekwencyjnych który **Zastosuj System operacyjny** lub **Zastosuj obraz danych** akcji w tej sekwencji zadań nie ma już docelowe. 

-   **Określony dysk i partycja**: Wybierz **dysku** (rozpoczynający się od cyfry 0) i **partycji** (rozpoczynający się od cyfry 1).  

-   **Określona litera dysku logicznego**: Określ **literę dysku** przypisaną do partycji przez środowisko Windows PE. Ta litera dysku może różnić się od litery dysku, który przypisze nowo wdrożony system operacyjny.  

-   **Litera dysku logicznego przechowywana w zmiennej**: Określ zmienną sekwencji zadań zawiera literę dysku przypisaną do partycji przez środowisko Windows PE. Ta zmienna jest zwykle ustawić w sekcji Zaawansowane **właściwości partycji** okno dialogowe **Format i partycji** akcji sekwencji zadań.  

### <a name="options"></a>Opcje  
 Oprócz domyślnych opcji, należy skonfigurować następujące dodatkowe ustawienia na **opcje** kartę ten krok sekwencji zadań:  

-   **Dostęp do zawartości bezpośrednio z punktu dystrybucji**  
     Konfigurowanie sekwencji zadań w celu uzyskania dostępu do obrazu systemu operacyjnego bezpośrednio z punktu dystrybucji. Na przykład można użyć tej opcji, podczas wdrażania systemów operacyjnych na urządzeniach osadzonych z ograniczoną pojemność magazynu. Po wybraniu tej opcji należy również skonfigurować ustawienia udziału pakietu na **dostęp do danych** na karcie właściwości pakietu.  

    > [!NOTE]  
    >  To ustawienie przesłania opcję wdrożenia, który został skonfigurowany na **punktów dystrybucji** strony **Kreatora wdrażania oprogramowania**. Jest to zastąpienie tylko dla obrazu systemu operacyjnego, który określa ten krok, nie dla całej zawartości sekwencji zadań.  



##  <a name="BKMK_ApplyWindowsSettings"></a>Zastosuj ustawienia systemu Windows  
 Ten krok umożliwia skonfigurowanie ustawień systemu Windows na komputerze docelowym. Sekwencja zadań przechowuje te wartości w pliku odpowiedzi odpowiednie. Instalator systemu Windows używa tego pliku odpowiedzi podczas **Zainstaluj system Windows i program ConfigMgr** akcji.  

 Ten krok sekwencji zadań działa tylko w środowisku Windows PE. Nie działa on w standardowym systemie operacyjnym. Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań dla tej akcji, zobacz [Zmienne akcji sekwencji zadań Zastosuj ustawienia systemu Windows](task-sequence-action-variables.md#BKMK_ApplyWindowsSettings).  

 W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **ustawienia**i wybierz **Zastosuj ustawienia systemu Windows** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości  
 Na **właściwości** karta dla tego kroku, skonfigurować ustawienia opisane w tej sekcji.  

 **Nazwa użytkownika**  
 Podaj nazwę zarejestrowanego użytkownika skojarzoną z komputerem docelowym. Ta wartość może zostać przesłonięta przez wartość przechwyconą przez akcję sekwencji zadań **Przechwyć ustawienia systemu Windows**.  

 **Nazwa organizacji**  
 Podaj nazwę zarejestrowanej organizacji skojarzoną z komputerem docelowym. Ta wartość może zostać przesłonięta przez wartość przechwyconą przez akcję sekwencji zadań **Przechwyć ustawienia systemu Windows**.  

 **Klucz produktu**  
 Określ klucz produktu używany na potrzeby instalacji systemu Windows na komputerze docelowym.  

 **Licencjonowanie serwera**  
 Określ tryb licencjonowania serwera. Możesz wybrać tryb licencjonowania **Na serwer** lub **Na użytkownika**. W przypadku wybrania **na serwer**, określ również maksymalną liczbę połączeń dozwolonych dla umowy licencyjnej. Wybierz pozycję **Nie określaj**, jeśli komputer docelowy nie jest serwerem lub jeśli nie chcesz określać trybu licencjonowania.  

 **Maksymalna liczba połączeń**  
 Określ maksymalną liczbę połączeń dostępnych dla tego komputera zgodnie z zapisem w umowie licencyjnej.  

 **Losowo Generuj hasło administratora lokalnego i Wyłącz konto na wszystkich obsługiwanych platformach (zalecane)**  
 Wybierz tę opcję, aby ustawić wartość ciągu losowo wygenerowane hasło administratora lokalnego. Ta opcja powoduje również wyłączenie konta administratora lokalnego na platformach, które obsługują tę możliwość.  

 **Włącz konto i określ hasło administratora lokalnego**  
 Wybierz tę opcję, aby włączyć za pomocą określonego hasła konta administratora lokalnego. Wprowadź hasło w wierszu **Hasło** i potwierdź hasło w wierszu **Potwierdź hasło**.  

 **Strefa czasowa**  
 Określ strefę czasową na komputerze docelowym. Ta wartość może zostać przesłonięta przez wartość przechwyconą przez krok sekwencji zadań **Przechwyć ustawienia systemu Windows**.  



##  <a name="BKMK_AutoApplyDrivers"></a>Automatycznie Zastosuj sterowniki  
 Ten krok umożliwia dopasowanie i zainstalowanie sterowników w ramach wdrożenia systemu operacyjnego.  

 W ramach kroku sekwencji zadań **Automatycznie zastosuj sterowniki** są wykonywane następujące akcje:  

1.  Skanowanie sprzętu i znaleźć identyfikatorów plug and play wszystkich urządzeń istniejących w systemie.  

2.  Wysyłanie listy urządzeń i ich identyfikatorów plug and play do punktu zarządzania. Punkt zarządzania zwraca listę zgodnych sterowników z katalogu sterowników dla każdego urządzenia sprzętowego. Lista zawiera wszystkie sterowniki bez względu na pakiet sterowników, które znajdują się w, sterowniki z określonej kategorii sterowników i sterowniki nie zostały wyłączone.  

3.  Dla każdego urządzenia sprzętowego sekwencja zadań wybiera najlepszy sterownik. Ten sterownik jest, aby wdrożony system operacyjny i znajduje się w dostępnym punkcie dystrybucji.  

4.  Sekwencji zadań pobiera wybrane sterowniki z punktu dystrybucji i przygotowuje sterowników na docelowy system operacyjny.  

    1.  W przypadku instalacji opartej na obrazie sekwencja zadań umieszcza sterowników w magazynie sterowników systemu operacyjnego.  

    2.  W przypadku instalacji korzystających z instalacji sekwencja zadań konfiguruje Instalatora systemu Windows przy użyciu lokalizacji sterowników.  

5.  Podczas **Zainstaluj system Windows i program ConfigMgr** kroku w sekwencji zadań instalacji systemu Windows wyszukuje sterowniki umieszczone w ramach tej akcji.  

> [!IMPORTANT]
>  Nie można użyć nośnika autonomicznego **automatycznie Zastosuj sterowniki** kroku. Instalator systemu Windows nie jest żadne połączenie z lokacją programu Configuration Manager w tym scenariuszu.

Ten krok sekwencji zadań działa tylko w środowisku Windows PE. Nie działa on w standardowym systemie operacyjnym. Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań dla tej akcji, zobacz [Zmienne akcji sekwencji zadań Automatycznie zastosuj sterowniki](task-sequence-action-variables.md#BKMK_AutoApplyDrivers).  

 W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **sterowniki**i wybierz **automatycznie Zastosuj sterowniki** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości  
 Na **właściwości** karta dla tego kroku, skonfigurować ustawienia opisane w tej sekcji.  

 **Zainstaluj tylko najlepiej pasujące zgodne sterowniki**  
 Określa, że w ramach kroku sekwencji zadań jest instalowany tylko najlepiej dopasowany sterownik dla każdego wykrytego urządzenia sprzętowego.  

 **Zainstaluj wszystkie zgodne sterowniki**  
 Sekwencja zadań instaluje wszystkie sterowniki niezgodne dla każdego wykrytego urządzenia sprzętowego. Instalator systemu Windows następnie wybiera najlepszy sterownik. Ta opcja używa więcej sieci przepustowości i miejsca na dysku. Sekwencja zadań pobieranych więcej sterowników, ale systemu Windows można wybrać lepszy sterownik.  

 **Uwzględnij sterowniki z wszystkich kategorii**  
 Sekwencja zadań wyszukuje wszystkich dostępnych kategoriach sterowników odpowiednie sterowniki urządzeń.  

 **Ogranicz dopasowywanie tylko do sterowników z wybranych kategorii**  
 Sekwencja zadań wyszukuje w określonych kategoriach sterowników odpowiednie sterowniki urządzeń.  

 **Wykonaj instalację nienadzorowaną niepodpisanych sterowników w wersjach systemu Windows, gdy jest to dozwolone**  
 Ta opcja umożliwia systemu Windows zainstalować sterowniki bez podpisu cyfrowego.   

  > [!IMPORTANT]  
  >  Ta opcja nie ma zastosowania do systemów operacyjnych, których nie można skonfigurować zasad podpisywania sterowników.  



##  <a name="BKMK_CaptureNetworkSettings"></a>Przechwyć ustawienia sieci  
 Ten krok umożliwia przechwycenie ustawień sieci firmy Microsoft z komputera z uruchomioną sekwencją zadań. Sekwencja zadań te ustawienia są zapisywane w zmiennych sekwencji zadań. Ustawienia te zastępują ustawienia domyślne skonfigurowane w **Zastosuj ustawienia sieci** kroku.  

 Ten krok sekwencji zadań działa tylko w standardowym systemie operacyjnym. Nie działa on w środowisku Windows PE. Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań dla tej akcji, zobacz [Zmienne akcji sekwencji zadań Przechwyć ustawienia sieci](task-sequence-action-variables.md#BKMK_CaptureNetworkSettings).  

W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **ustawienia**i wybierz **Przechwyć ustawienia sieci** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości  
 Na **właściwości** karta dla tego kroku, skonfigurować ustawienia opisane w tej sekcji.  

 **Migruj członkostwo w domenie i grupie roboczej**  
 Przechwytuje informacje dotyczące członkostwa w domenie i grupie roboczej na komputerze docelowym.  

 **Migruj konfigurację karty sieciowej**  
 Przechwytuje konfigurację karty sieciowej komputera docelowego. Przechwycone informacje obejmują ustawienia globalne sieci, liczbę kart i ustawienia sieci skojarzone z każdą kartą. Należą do nich ustawienia związane z usługami DNS i WINS, adresami IP oraz filtrami portów.  



##  <a name="BKMK_CaptureOperatingSystemImage"></a>Przechwyć obraz systemu operacyjnego  
 Ten krok powoduje przechwycenie jednego lub więcej obrazów z komputera odniesienia. Sekwencja zadań tworzy plik obrazu systemu Windows (wim) w określonym udziale sieciowym. Następnie użyj **dodać pakiet obrazu systemu operacyjnego** kreatora można zaimportować tego obrazu do programu Configuration Manager w przypadku wdrożeń na podstawie obrazu systemu operacyjnego.  

 Menedżer konfiguracji przechwytuje każdy wolumin (dysk) z komputera odniesienia na osobny obraz w pliku wim. Jeśli przywoływany komputer ma wiele woluminów, wynikowy plik wim zawiera osobny obraz każdego woluminu. Przechwytywane są t ylko woluminy sformatowane przy użyciu systemu NTFS lub FAT32. Woluminy w innych formatach i woluminy USB są pomijane.  

 System operacyjny zainstalowany na komputerze odniesienia musi być wersji systemu Windows, która obsługuje programu Configuration Manager. Aby przygotować system operacyjny komputera odniesienia, należy użyć narzędzia SysPrep. Wolumin z zainstalowanym systemem operacyjnym i wolumin rozruchowy muszą być tym samym woluminem.  

 Określ konto z uprawnieniami do zapisu do udziału sieciowego wybrane.  

 Ten krok sekwencji zadań działa tylko w środowisku Windows PE. Nie działa on w standardowym systemie operacyjnym. Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań dla tej akcji, zobacz [Zmienne akcji sekwencji zadań Przechwyć obraz systemu operacyjnego](task-sequence-action-variables.md#BKMK_CaptureOperatingSystemImage).  

 W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **obrazów**i wybierz **Przechwyć obraz systemu operacyjnego** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości  
 Na **właściwości** karta dla tego kroku, skonfigurować ustawienia opisane w tej sekcji.  

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
 Aby użyć narzędzia migracji stanu użytkowników (USMT) do przechwytywania stanu użytkownika i ustawień z komputera z uruchomioną sekwencją zadań, należy użyć tego kroku. Ten krok sekwencji zadań jest używany razem z krokiem sekwencji zadań **Przywróć stan użytkownika**. Przy użyciu narzędzia USMT 3.0.1 i później, ta opcja zawsze szyfruje Magazyn stanów narzędzia USMT za pomocą klucza szyfrowania wygenerowanego i zarządzanego przez program Configuration Manager.  

 Aby uzyskać więcej informacji o zarządzaniu stanem użytkownika podczas wdrażania systemów operacyjnych, zobacz [Zarządzanie stanem użytkownika](../get-started/manage-user-state.md).  

 Jeśli chcesz zapisać i przywracania stanu użytkownika z punktu migracji stanu, użyj **Przechwyć stan użytkownika** krok z **Zażądaj magazynu stanów** i **Zwolnij Magazyn stanów** kroki.  

 Krok sekwencji zadań **Przechwyć stan użytkownika** zapewnia kontrolę nad ograniczonym podzbiorem najczęściej używanych opcji narzędzia USMT. Dodatkowe opcje wiersza polecenia można określić za pomocą zmiennej sekwencji zadań OSDMigrateAdditionalCaptureOptions.  

 Ten krok sekwencji zadań działa tylko w środowisku Windows PE. Nie działa on w standardowym systemie operacyjnym. Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań dla tej akcji, zobacz [Zmienne akcji sekwencji zadań Przechwyć stan użytkownika](task-sequence-action-variables.md#BKMK_CaptureUserState).  

 W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **stanu użytkownika**i wybierz **Przechwyć stan użytkownika** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości  
 Na **właściwości** karta dla tego kroku, skonfigurować ustawienia opisane w tej sekcji.  

 **Pakiet narzędzia migracji stanu użytkownika**  
 Określ pakiet, który zawiera narzędzie migracji stanu użytkowników (USMT). Sekwencja zadań używa tej wersji narzędzia USMT do przechwycenia stanu i ustawień użytkownika. Ten pakiet nie wymaga programu. Określ pakiet zawierający wersję 32-bitowy lub 64-bitowego narzędzia USMT. Architektura narzędzia USMT zależy od architektury systemu operacyjnego, w którym sekwencja zadań jest przechwytywania stanu.  

 **Przechwyć wszystkie profile użytkowników z opcjami standardowymi**  
 Przeprowadź migrację wszystkich informacji o profilu użytkownika. Jest to opcja domyślna.  

 Jeśli ta opcja, ale nie zaznaczaj **Przywróć profile użytkowników komputera lokalnego** w **Przywróć stan użytkownika** kroku sekwencji zadań zakończy się niepowodzeniem. Menedżer konfiguracji nie może migrować nowych kont bez przypisywania do nich haseł. 

 Jeśli używasz **Zainstaluj istniejący pakiet obrazów** opcji **nowej sekwencji zadań** kreatora, wynikowa sekwencja zadań jest równa **Przechwyć wszystkie profile użytkowników z opcjami standardowymi**. Ta domyślna sekwencja zadań nie opcję, aby **Przywróć profile użytkowników komputera lokalnego**, innymi słowy, konta użytkowników domeny.  

 Wybierz pozycję **Przywróć profile użytkowników komputera lokalnego** i podaj hasło dla konta, które chcesz migrować. W przypadku ręcznie utworzonej sekwencji zadań to ustawienie znajduje się w kroku Przywróć stan użytkownika. W przypadku sekwencji zadań utworzonej przez kreatora **Nowa sekwencja zadań** to ustawienie znajduje się na stronie kreatora dotyczącej kroku **Przywróć pliki i ustawienia użytkownika**.  

 Jeśli nie masz żadnych kont użytkowników lokalnych, to ustawienie nie ma zastosowania.  

 **Dostosuj sposób przechwytywania profili użytkowników**  
 Wybierz tę opcję, aby określić niestandardową migrację pliku profilu. Kliknij pozycję **Pliki**, aby wybrać pliki konfiguracji do użycia przez narzędzie USMT w ramach tego kroku. Określ plik XML niestandardowego, który zawiera reguły definiujące pliki stanu użytkownika, aby przeprowadzić migrację.  

 **Kliknij tutaj, aby wybrać pliki konfiguracji:**  
 Wybierz tę opcję, aby wybrać pliki konfiguracji w pakiecie narzędzia USMT, za pomocą których chcesz przechwytywać profile użytkowników. Kliknij przycisk **Pliki**, aby otworzyć okno dialogowe **Pliki konfiguracji**. Aby określić plik konfiguracji, wprowadź nazwę pliku w wierszu **Nazwa pliku**, a następnie kliknij przycisk **Dodaj**.  

 **Włącz pełne rejestrowanie**  
 Włącz tę opcję, aby wygenerować bardziej szczegółowe informacje pliku dziennika. Podczas przechwytywania stanu, sekwencja zadań domyślnie generuje ScanState.log w folderze dziennika sekwencji zadań \windows\system32\ccm\logs.   

 **Pomiń pliki korzystające z systemu szyfrowania plików**  
 Włącz tę opcję pominąć Przechwytywanie plików zaszyfrowanych z systemu szyfrowania plików (EFS). Te pliki zawierają pliki profilu użytkownika. W zależności od systemu operacyjnego i wersji narzędzia USMT odczyt zaszyfrowanych plików może nie być możliwy po przywróceniu. Więcej informacji można znaleźć w dokumentacji narzędzia USMT.  

 **Kopiuj, używając dostępu do systemu plików**  
 Włącz tę opcję, aby określić dowolne z następujących ustawień:  

-   **Kontynuuj, jeśli nie można przechwycić niektórych plików**: Włącz to ustawienie, aby kontynuować proces migracji, nawet jeśli nie można przechwycić niektórych plików. Jeśli wyłączysz tę opcję, jeśli nie można przechwycić pliku, ten krok zakończy się niepowodzeniem. Ta opcja jest domyślnie włączona.  

-   **Przechwyć lokalnie, używając łączy zamiast kopiować pliki**: Włącz to ustawienie umożliwia przechwytywanie plików, twardych linków NTFS.  

     Aby uzyskać więcej informacji na temat migrowania danych przy użyciu twardych linków, zobacz [Magazyn migracji za pomocą twardych linków](http://go.microsoft.com/fwlink/p/?LinkId=240222)  

-   **Przechwyć w trybie offline (tylko Windows PE)**: Włącz to ustawienie, aby przechwycić stan użytkownika w środowisku Windows PE zamiast pełnej wersji systemu operacyjnego.  
    
**Przechwyć, używając tle usługi kopiowania woluminów (VSS)**  
 Ta opcja umożliwia przechwytywanie plików, nawet jeśli zostały one zablokowane do edycji przez inną aplikację.  



##  <a name="BKMK_CaptureWindowsSettings"></a>Przechwyć ustawienia systemu Windows  
 Ten krok umożliwia przechwycenie ustawień systemu Windows z komputera z uruchomioną sekwencją zadań. Sekwencja zadań te ustawienia są zapisywane w zmiennych sekwencji zadań. Ustawienia te przechwycone zastępują ustawienia domyślne, które można skonfigurować na **Zastosuj ustawienia systemu Windows** kroku.  

 Ten krok sekwencji zadań działa w środowisku Windows PE lub w standardowym systemie operacyjnym. Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań dla tej akcji, zobacz [Zmienne akcji sekwencji zadań Przechwyć ustawienia systemu Windows](task-sequence-action-variables.md#BKMK_CaptureWindowsSettings).  

 W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **ustawienia**i wybierz **Przechwyć ustawienia systemu Windows** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości  
 Na **właściwości** karta dla tego kroku, skonfigurować ustawienia opisane w tej sekcji.  

 **Migruj nazwę komputera**  
 Przechwycić nazwą komputera NetBIOS komputera.  

 **Migrowanie zarejestrowane nazwy użytkownika i organizacji**  
 Przechwyć zarejestrowane nazwy użytkownika i organizacji z komputera.  

 **Migruj strefę czasową**  
 Przechwyć ustawienia strefy czasowej na komputerze.  



##  <a name="BKMK_CheckReadiness"></a>Sprawdź gotowość  
 Aby sprawdzić, czy komputer docelowy spełnia warunki wstępne określonego wdrożenia, należy użyć tego kroku.  

W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **ogólne**i wybierz **Sprawdź gotowość** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości  
 Na **właściwości** karta dla tego kroku, skonfigurować ustawienia opisane w tej sekcji.  

 **Zapewnij minimalną ilość pamięci (MB)**  
 Sprawdź, czy ilość pamięci w megabajtach (MB), spełnia lub przekracza podanej wartości. Krok powoduje włączenie tego ustawienia domyślne.  

 **Zapewnij minimalną szybkość procesora (MHz)**  
 Sprawdź, czy szybkość procesora w megahercach (MHz), spełnia lub przekracza podanej wartości. Krok powoduje włączenie tego ustawienia domyślne.  

 **Upewnij się, minimalna ilość wolnego miejsca (MB)**  
 Sprawdź, czy ilość wolnego miejsca na dysku wyrażony w megabajtach (MB), spełnia lub przekracza podanej wartości.  

 **Upewnij się, że bieżący system operacyjny do odświeżenia**  
 Sprawdź, czy system operacyjny zainstalowany na komputerze docelowym spełnia określonych wymagań. Krok ustawia to **klienta** domyślnie.  

### <a name="options"></a>Opcje
 > [!NOTE]  
 > Po włączeniu **Kontynuuj przy błędzie** ustawienie **opcje** kartę tego kroku tylko rejestruje ono wyniki sprawdzania gotowości. Jeśli sprawdzenie zakończy się niepowodzeniem, sekwencja zadań nie zatrzymuje się.



##  <a name="BKMK_ConnectToNetworkFolder"></a>Połącz z folderem sieciowym  
 Ten krok umożliwia utworzenie połączenia z udostępnionym folderem sieciowym.  

 Ten krok sekwencji zadań działa w standardowym systemie operacyjnym lub w środowisku Windows PE. Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań dla tej akcji, zobacz [Zmienne akcji sekwencji zadań Połącz z folderem sieciowym](task-sequence-action-variables.md#BKMK_ConnecttoNetworkFolder).  

 W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **ogólne**i wybierz **połączenia do folderu sieciowego** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości  
 Na **właściwości** karta dla tego kroku, skonfigurować ustawienia opisane w tej sekcji.  

 **Ścieżka**  
 Kliknij przycisk **Przeglądaj** Aby określić ścieżkę do folderu sieciowego. Użyj formatu  *\\\server\share*.

 **Dysk**  
 Wybierz literę dysku lokalnego, aby przypisać dla tego połączenia. 

 **Konta**  
 Kliknij przycisk **ustawić** do określenia konta użytkownika z uprawnieniami do nawiązania połączenia tego folderu sieciowego.



##  <a name="BKMK_DisableBitLocker"></a>Wyłącz funkcję BitLocker  
 Ten krok umożliwia wyłączenie szyfrowania BitLocker na bieżącym dysku systemu operacyjnego lub na określonym dysku. Po wykonaniu tej akcji funkcje ochrony kluczy są widoczne w postaci zwykłego tekstu na dysku twardym, ale zawartość dysku nie jest odszyfrowywana. W związku z tym ta akcja jest wykonywana niemal natychmiast.  

> [!NOTE]  
>  Szyfrowanie dysków za pomocą funkcji BitLocker umożliwia szyfrowanie zawartości woluminu dysku na niskim poziomie.  

 Jeśli masz wiele zaszyfrowanych dysków, musisz wyłączyć funkcję BitLocker na wszystkich dyskach danych przed wyłączeniem funkcji BitLocker na dysku systemu operacyjnego.  

 Ten krok działa tylko w standardowym systemie operacyjnym. Nie działa on w środowisku Windows PE.  

 W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **dysków**i wybierz **Wyłącz funkcję BitLocker** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości  
 Na **właściwości** karta dla tego kroku, skonfigurować ustawienia opisane w tej sekcji.  

 **Bieżący dysk systemu operacyjnego**  
 Wyłącza funkcję BitLocker na bieżącym dysku systemu operacyjnego.  

 **Określony dysk**  
 Wyłącza funkcję BitLocker na określonym dysku. Użyj listy rozwijanej, aby określić dysk, na którym chcesz wyłączyć funkcję BitLocker.  



##  <a name="BKMK_DownloadPackageContent"></a>Pobierz zawartość pakietu  
 Aby pobrać dowolny z następujących typów pakietów, należy użyć tego kroku:  

-   Obrazy systemu operacyjnego  

-   Pakiety uaktualnień systemu operacyjnego  

-   Pakiety sterowników  

-   Pakiety  
    
Ten krok działa dobrze w sekwencji zadań w celu uaktualnienia systemu operacyjnego w następujących scenariuszach:  

-   Użycie pojedynczej sekwencji zadań uaktualniania działającej na platformach x86 i x64. Dodaj dwa **Pobierz zawartość pakietu** czynnościach w ramach **przygotować do uaktualnienia** grupy. Określ warunki na **opcje** kartę wykrywania architektury klienta i pobrania tylko odpowiedniego systemu operacyjnego uaktualniania pakietu. Skonfiguruj każdy **Pobierz zawartość pakietu** krok, aby użyć tej samej zmiennej. Użyj zmiennej ścieżki nośnika w **Uaktualnij System operacyjny** kroku.  

-   Aby odpowiedni pakiet sterowników był pobierany dynamicznie, użyj dwóch kroków **Pobierz zawartość pakietu** z warunkami wykrywania odpowiedniego typu sprzętu dla każdego pakietu sterowników. Skonfiguruj każdy **Pobierz zawartość pakietu** krok, aby użyć tej samej zmiennej. Użyj zmiennej **zawartość przejściowa** wartości w sekcji sterowników **Uaktualnij System operacyjny** kroku.  

> [!NOTE]    
> Podczas wdrażania sekwencji zadań zawiera krok Pobierz zawartość pakietu nie zaznaczaj **Pobierz całą zawartość lokalnie przed uruchomieniem sekwencji zadań** lub **uzyskują dostęp do zawartości bezpośrednio z punktu dystrybucji** dla **opcje wdrażania** na **punktów dystrybucji** strony Kreatora wdrażania oprogramowania.  

Ten krok działa w standardowym systemie operacyjnym lub w środowisku Windows PE. Jednak opcję, aby zapisać pakiet w pamięci podręcznej klienta programu Configuration Manager nie jest obsługiwane w środowisku WinPE.

 W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **oprogramowania**i wybierz **Pobierz zawartość pakietu** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości  
 Na **właściwości** karta dla tego kroku, skonfigurować ustawienia opisane w tej sekcji.  

 Ikona **Wybierz pakiet**  
 Kliknij ikonę, aby wybrać pakiet do pobrania. Po wybraniu pakietu możesz kliknąć ikonę ponownie, aby wybrać inny pakiet.  

 **Umieść w następującej lokalizacji**  
 Wybierz opcję, aby zapisać pakiet w jednej z następujących lokalizacji:  

 -   **Katalog roboczy sekwencji zadań**  

 -   **Pamięć podręczna klienta programu Configuration Manager**: Ta opcja służy do przechowywania zawartości w pamięci podręcznej klienta. Klient działa jako źródło równorzędnej pamięci podręcznej dla innych klientów równorzędnej pamięci podręcznej. Aby uzyskać więcej informacji, zobacz [przygotowanie środowiska Windows PE równorzędnej pamięci podręcznej, aby zmniejszyć ruch w sieci WAN](../get-started/prepare-windows-pe-peer-cache-to-reduce-wan-traffic.md).  

 -    **Niestandardowa ścieżka**: Po wybraniu tej opcji aparat sekwencji zadań najpierw pobiera pakiet katalog roboczy sekwencji zadań, a następnie przenosi je do tej ścieżki, które określisz. Aparat sekwencji zadań dołącza ścieżki z identyfikatora pakietu. 
   
**Zapisz ścieżkę jako zmienną**  
 Ścieżkę można zapisać jako zmienną do użycia w innym kroku sekwencji zadań. Menedżer konfiguracji dodaje sufiks numeryczny do nazwy zmiennej. Na przykład jeśli określisz zmienną %*mojazawartosc*% jako zmienną niestandardową, jest głównego, dla której przechowuje wszystkie przywoływanej zawartości w sekwencji zadań. Zawartość ta może zawierać wielu pakietów. Następnie w przypadku odwoływania się do zmiennej, należy dodać sufiksem numerycznym. Na przykład pierwszego pakietu, można znaleźć w temacie %*mojazawartosc01*%. Odwołań do zmiennych w kolejnych krokach, takich jak **Uaktualnij System operacyjny**, użyj %*mojazawartosc02*% lub %*mycontent03*%, gdzie numer odpowiada Aby **Pobierz zawartość pakietu** krok zawiera listę pakietów.  

**Jeśli pobieranie pakietu nie powiedzie się, kontynuuj pobieranie pozostałych pakietów na liście**  
 Jeśli sekwencja zadań nie powiedzie się pobrać pakiet, rozpoczyna się pobrać następnego pakietu na liście.  



##  <a name="BKMK_EnableBitLocker"></a>Włącz funkcję BitLocker  
Aby włączyć szyfrowanie funkcji BitLocker na co najmniej dwóch partycjach dysku twardego, należy użyć tego kroku. Pierwsza aktywna partycja zawiera kod ładowania początkowego systemu Windows. Kolejna partycja zawiera system operacyjny. Partycja ładowania początkowego musi pozostać niezaszyfrowana.  

Krok sekwencji zadań **Wstępne inicjowanie obsługi funkcji BitLocker** umożliwia włączenie funkcji BitLocker na dysku w środowisku Windows PE. Aby uzyskać więcej informacji, zobacz [funkcja BitLocker przed udostępnieniem](#BKMK_PreProvisionBitLocker) sekcji.  

> [!NOTE]  
>  Szyfrowanie dysków za pomocą funkcji BitLocker umożliwia szyfrowanie zawartości woluminu dysku na niskim poziomie.  

Krok **Włącz funkcję BitLocker** działa tylko w standardowym systemie operacyjnym. Nie działa on w środowisku Windows PE. Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań dla tej akcji, zobacz [Zmienne akcji sekwencji zadań Włącz funkcję BitLocker](task-sequence-action-variables.md#BKMK_EnableBitLocker).  

Po określeniu **tylko TPM**, **modułu TPM i klucz uruchomienia na USB**, lub **modułu TPM i numer PIN**, przed uruchomieniem należywnastępującymstaniemodułu(TPM) **Włącz funkcję BitLocker** krok:  

-   Włączono  
-   Uaktywniony  
-   Własność dozwolona  
   
Ten krok jest wykonywany wszelkie pozostałe Inicjowanie modułu TPM. Pozostałe kroki nie wymagają obecności fizycznej ani ponownego uruchamiania. **Włącz funkcję BitLocker** krok przezroczysty wykonuje do pozostałych kroków inicjowania modułu TPM, w razie potrzeby:  

-   Utworzenie pary kluczy poręczenia  
-   Utworzenie wartości autoryzacji właściciela i utworzenie depozytu w usłudze Active Directory, która musi zostać rozszerzona w celu obsługi tej wartości  
-   Przejęcie na własność  
-   Utworzenie klucza głównego magazynowania lub zresetowanie, jeśli klucz już istnieje, ale jest niezgodny  
   
Jeśli sekwencja zadań oczekiwania **Włącz funkcję BitLocker** krok, aby ukończyć proces szyfrowania dysku, a następnie wybierz **oczekiwania** opcji. Jeśli nie zaznaczysz **oczekiwania** opcji, proces szyfrowania dysku przebiega w tle. Sekwencja zadań będzie kontynuowana natychmiast do następnego kroku.  

Funkcja BitLocker umożliwia szyfrowanie wielu dysków w systemie komputerowym (dysków systemu operacyjnego i dysków danych). Aby zaszyfrować dysk danych, szyfrowania dysku systemu operacyjnego i ukończenie procesu szyfrowania. To wymaganie dotyczy, ponieważ dysk systemu operacyjnego są przechowywane funkcje ochrony kluczy dysków danych. Jeśli szyfrowanie systemu operacyjnego i dysków danych w tej samej sekwencji zadań, zaznacz **oczekiwania** opcja **Włącz funkcję BitLocker** kroku dla dysku systemu operacyjnego.  

Jeśli dysk twardy jest już zaszyfrowany, ale funkcja BitLocker jest wyłączona, a następnie **Włącz funkcję BitLocker** krok ponownie włącza funkcje ochrony kluczy i zakończeniu szybko. W takiej sytuacji nie musisz ponownie szyfrować dysku twardego.  

Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań dla tej akcji, zobacz [Zmienne akcji sekwencji zadań Włącz funkcję BitLocker](task-sequence-action-variables.md#BKMK_EnableBitLocker).  

W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **dysków**i wybierz **Włącz funkcję BitLocker** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości  
 Na **właściwości** karta dla tego kroku, skonfigurować ustawienia opisane w tej sekcji.  

 **Wybierz dysk do zaszyfrowania**  
 Określa dysk do zaszyfrowania. Aby zaszyfrować bieżący dysk systemu operacyjnego, wybierz pozycję **Bieżący dysk systemu operacyjnego**, a następnie skonfiguruj jedną z następujących opcji zarządzania kluczami:  

-   **Tylko TPM**: Wybierz tę opcję, aby użyć tylko modułu (TPM).  

-   **Klucz uruchomienia tylko na USB**: Wybierz tę opcję, aby użyć klucza uruchomienia przechowywanego na dysku flash USB. Jeśli wybierzesz tę opcję, funkcja BitLocker zablokuje normalny proces rozruchu do czasu podłączenia do komputera urządzenia USB zawierającego klucz uruchomienia funkcji BitLocker.  

-   **Moduł TPM i klucz uruchomienia na USB**: Wybierz tę opcję, aby użyć modułu TPM i klucza uruchomienia przechowywanego na dysku flash USB. Jeśli wybierzesz tę opcję, funkcja BitLocker zablokuje normalny proces rozruchu do czasu podłączenia do komputera urządzenia USB zawierającego klucz uruchomienia funkcji BitLocker.  

-   **Moduł TPM i numer PIN**:  Wybierz tę opcję, aby użyć modułu TPM i osobistego numeru identyfikacyjnego (PIN). Jeśli wybierzesz tę opcję, funkcja BitLocker zablokuje normalny proces rozruchu do czasu podania numeru PIN przez użytkownika.  
   
Aby zaszyfrować określony dysk danych, na którym nie ma systemu operacyjnego, wybierz pozycję **Określony dysk**, a następnie wybierz dysk z listy.  

**Wybierz miejsce utworzenia klucza odzyskiwania**  
 Aby określić, gdzie funkcji BitLocker tworzy hasło odzyskiwania i zdeponowania go w usłudze Active Directory, zaznacz **w usłudze Active Directory**. Jeśli wybierzesz tę opcję, będzie konieczne rozszerzenie usługi Active Directory dla lokacji. Funkcji BitLocker można zapisać informacji o odzyskiwaniu skojarzony w usłudze Active Directory. Wybierz **nie twórz klucza odzyskiwania** aby nie utworzyć hasło. Najlepszym rozwiązaniem jest utworzenie hasła.  

**Poczekaj na ukończenie procesu szyfrowania dysku na wszystkich dyskach przed kontynuowanie wykonania sekwencji zadań przez funkcję BitLocker**  
 Wybierz tę opcję, aby umożliwić szyfrowania dysków funkcją BitLocker do wykonania przed uruchomieniem następnego kroku w sekwencji zadań. Jeśli wybierzesz tę opcję, funkcja BitLocker szyfruje cały wolumin dysku, zanim użytkownik będzie mógł zalogować się do komputera.  

Proces szyfrowania może zająć godziny podczas szyfrowania dużego dysku twardego. Nie wybierzesz tej opcji umożliwia sekwencji zadań bezzwłocznie ją kontynuować.  



##  <a name="BKMK_FormatandPartitionDisk"></a>Format i partycji  
 Umożliwia sformatowanie określonego dysku na komputerze docelowym, należy użyć tego kroku.  

> [!IMPORTANT]  
>  Każde ustawienie określone dla tego kroku sekwencji zadań dotyczy jednego określonego dysku. Aby sformatować i inny dysk na komputerze docelowym, dodać kolejny **Format i partycji** krok do sekwencji zadań.  

 Ten krok sekwencji zadań działa tylko w środowisku Windows PE. Nie działa on w standardowym systemie operacyjnym. Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań dla tej akcji, zobacz [Zmienne akcji sekwencji zadań Formatuj dysk i podziel go na partycje](task-sequence-action-variables.md#BKMK_FormatPartitionDisk).  

 W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **dysków**i wybierz **Format i partycji** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości  
 Na **właściwości** karta dla tego kroku, skonfigurować ustawienia opisane w tej sekcji.  

 **Numer dysku**  
 Numer dysku fizycznego do sformatowania dysku. Jest on wyznaczany w kolejności wyliczania dysków systemu Windows.  

 **Typ dysku**  
 Typ formatowanego dysku. Na liście rozwijanej są dostępne dwie opcje do wyboru: 

-   Standardowa — główny rekord rozruchowy (MBR)
-   GPT — tabela partycji GUID  

> [!NOTE]  
>  Jeśli zmienisz typ dysku **standardowa (MBR)** do **GPT**, a układ partycji zawiera partycję rozszerzoną, sekwencja zadań spowoduje usunięcie wszystkich partycji rozszerzonych i logicznych z układu. Edytor sekwencji zadań wyświetli monit o potwierdzenie tej akcji przed zmianą typu dysku.  
   
**Wolumin**  
 Określone informacje na temat partycji lub woluminie, który tworzy sekwencję zadań, łącznie z następującymi atrybutami:  

-   Nazwa  
-   Pozostałe miejsce na dysku  
   
Aby utworzyć nową partycję, kliknij pozycję **Nowy** w celu otwarcia okna dialogowego **Właściwości partycji**. Określ typ i rozmiar partycji, i czy jest partycją rozruchową. Aby zmodyfikować istniejącą partycję, kliknij partycję, którą chcesz zmodyfikować, a następnie kliknij przycisk właściwości. Aby uzyskać więcej informacji o tym, jak skonfigurować partycje dysków twardych zobacz następujące artykuły:  

-   [Jak skonfigurować partycje dysków twardych z systemem UEFI/GPT](http://go.microsoft.com/fwlink/?LinkID=272104)  
-   [Jak skonfigurować partycje dysków twardych z systemem BIOS/MBR](http://go.microsoft.com/fwlink/?LinkId=272105)  

Aby usunąć partycję, zaznacz partycję do usunięcia, a następnie kliknij pozycję **Usuń**.  



##  <a name="BKMK_InstallApplication"></a>Instalowanie aplikacji  
Ta czynność powoduje zainstalowanie określonej aplikacji lub zestawu aplikacji zdefiniowane przez dynamiczną listę zmiennych sekwencji zadań. Gdy ten krok zostanie uruchomiony, instalacja aplikacji rozpocznie się natychmiast bez oczekiwania na interwał sondowania zasad.  

Instalowane oprogramowanie musi spełniać następujące kryteria:  

-   Aplikacja musi mieć typ wdrożenia Instalator Windows lub Instalator skryptowy. Typy wdrożeń Pakiet aplikacji systemu Windows (pliki appx) nie są obsługiwane.  

-   Oprogramowanie musi być uruchamiane na lokalnym koncie systemowym, a nie na koncie użytkownika.  

-   Oprogramowanie nie może mieć interakcji z pulpitem. Oprogramowanie musi być uruchamiane w trybie dyskretnym lub nienadzorowanym.  

-   Oprogramowanie nie może samodzielnie inicjować ponownego uruchomienia. Aplikacja musi żądać ponownego uruchomienia przy użyciu standardowego kodu ponownego uruchomienia (kodu zakończenia 3010). Takie zachowanie gwarantuje, że krok sekwencji zadań poprawnie obsługuje ponowne uruchomienie. Jeśli aplikacja zwróci kod zakończenia 3010, aparat sekwencji zadań wykona ponowne uruchomienie. Sekwencja zadań będzie automatycznie kontynuować działanie po ponownym uruchomieniu komputera.  

Gdy **zainstaluj aplikację** kroku jest uruchamiane, aplikacja sprawdza możliwość zastosowania reguł wymagań oraz metody wykrywania jej typy wdrożeń. Na podstawie wyników tej kontroli aplikacja instaluje odpowiedni typ wdrożenia. Jeśli typ wdrożenia zawiera zależności, zostanie obliczony zależny typ wdrożenia, który zostanie zainstalowany w ramach kroku Zainstaluj aplikację. Zależności aplikacji nie są obsługiwane w przypadku nośników autonomicznych.  

> [!NOTE]  
>  Aby zainstalować aplikację, która zastępuje inną aplikację, pliki zawartości zastępowanej aplikacji musi być dostępna. W przeciwnym razie ten krok sekwencji zadań zakończy się niepowodzeniem. Przykład: program Microsoft Visio 2010 jest zainstalowany na kliencie lub w przechwyconym obrazie. Gdy **zainstaluj aplikację** krok instaluje program Microsoft Visio 2013, pliki zawartości dla programu Microsoft Visio 2010 (zastępowanej aplikacji) muszą być dostępne w punkcie dystrybucji. Jeśli program Microsoft Visio nie jest zainstalowany na wszystkich na kliencie lub przechwycony obraz, sekwencja zadań instaluje programu Microsoft Visio 2013 bez sprawdzania, czy pliki zawartości programu Microsoft Visio 2010.  

> [!NOTE]
> Jeśli klient nie może pobrać listy punktów zarządzania z usług lokalizacji, umożliwia określenie, ile milisekund zadanie sekwencji czeka przed ponowną instalowanie SMSTSMPListRequestTimeoutEnabled i SMSTSMPListRequestTimeout wbudowanych zmiennych aktualizacji oprogramowania lub aplikacji. Aby uzyskać więcej informacji, zobacz [wbudowane zmienne sekwencji zadań](task-sequence-built-in-variables.md).

 Ten krok sekwencji zadań działa tylko w standardowym systemie operacyjnym. Nie działa on w środowisku Windows PE.  

 W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **oprogramowania**i wybierz **zainstaluj aplikację** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości  
 Na **właściwości** karta dla tego kroku, skonfigurować ustawienia, które zostały opisane w tej sekcji.  

 **Zainstaluj następujące aplikacje**  
 Sekwencja zadań instaluje te aplikacje w określonej kolejności.  

 Filtry programu Configuration Manager jakąkolwiek wyłączone aplikacje lub wszystkie aplikacje, z następującymi ustawieniami:  

-   Tylko, gdy użytkownik jest zalogowany  
-   Uruchom z prawami użytkownika  

Te aplikacje nie są wyświetlane w **wybierz aplikację do zainstalowania** okno dialogowe.
  
**Zainstaluj aplikacje zgodnie z listą zmiennych dynamicznych**  
Sekwencja zadań instaluje aplikacji przy użyciu tego podstawową nazwę zmiennej. Podstawową nazwę zmiennej jest zestaw zmiennych sekwencji zadań zdefiniowanych dla kolekcji lub komputera. Te zmienne określają aplikacje, które sekwencja zadań instaluje dla tej kolekcji lub komputera. Każda nazwa zmiennej składa się z podstawowej nazwy pospolitej i liczbowego sufiksu (zaczynając od 01). Wartość każdej zmiennej musi zawierać wyłącznie nazwę aplikacji.  

W sekwencji zadań umożliwia instalowanie aplikacji za pomocą listy zmiennych dynamicznych należy włączyć następujące ustawienie na **ogólne** aplikacji **właściwości**: **Zezwalaj na tę aplikację do zainstalowania z akcji sekwencji zadań zainstaluj aplikację zamiast wdrażania ręcznego**  

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

Poniższe warunki mają wpływ na aplikacje zainstalowane przez sekwencję zadań:  

-   Jeśli wartość zmiennej zawiera informacje inne niż nazwa aplikacji, Sekwencja zadań nie instaluje aplikację, a sekwencja zadań będzie kontynuować działanie.  

-   Jeśli sekwencja zadań nie zostanie znaleziona zmienna o określonej nazwie podstawowej i sufiksie "01", sekwencja zadań nie instaluj żadnych aplikacji. 
   
**Jeśli aplikacja nie powiedzie się, kontynuuj instalowanie pozostałych aplikacji z listy**  
 To ustawienie określa, że krok ma kontynuować działanie w przypadku niepowodzenia instalacji aplikacji. Jeśli to ustawienie nie przerywać sekwencji zadań niezależnie od błędów instalacji. Jeśli to ustawienie nie zostanie określony, a instalacja zakończy się niepowodzeniem, krok natychmiast kończy się.  

### <a name="options"></a>Opcje
 > [!NOTE] 
 > Po wybraniu **Kontynuuj przy błędzie** na **opcje** kartę tego kroku sekwencji zadań będzie kontynuowane po niepowodzeniu instalacji aplikacji. Jeśli ta opcja nie jest włączone, sekwencja zadań zakończy się niepowodzeniem i nie można zainstalować pozostałe aplikacje.  
 
Oprócz domyślnych opcji, należy skonfigurować następujące dodatkowe ustawienia na **opcje** kartę ten krok sekwencji zadań:  

-   **Ponów ten krok, jeśli komputer zostanie nieoczekiwanie uruchomiony ponownie**  
    Jeśli jedna z instalacji aplikacji zostanie nieoczekiwanie uruchomiony ponownie komputer, ponów próbę wykonania tego kroku. Krok powoduje włączenie tego ustawienia domyślnie z dwóch ponownych prób. Można określić od jednej do pięciu ponownych prób.  



##  <a name="BKMK_InstallPackage"></a>Zainstaluj pakiet
Ten krok umożliwia zainstalowanie pakietu oprogramowania w ramach sekwencji zadań. Gdy ten krok zostanie uruchomiony, instalacja rozpocznie się natychmiast bez oczekiwania na interwał sondowania zasad.  

Pakiet musi spełniać następujące kryteria:  

-   Musi ona działać w ramach lokalnego konta systemowego, a nie konta użytkownika.  

-   Oprogramowanie nie może mieć interakcji z pulpitem. Oprogramowanie musi być uruchamiane w trybie dyskretnym lub nienadzorowanym.  

-   Oprogramowanie nie może samodzielnie inicjować ponownego uruchomienia. Oprogramowanie musi żądać ponownego uruchomienia przy użyciu standardowego kodu ponownego uruchomienia (kodu zakończenia 3010). Takie zachowanie gwarantuje, że krok sekwencji zadań poprawnie obsługuje ponowne uruchomienie. Jeśli oprogramowanie zwróci kod zakończenia 3010, aparat sekwencji zadań uruchamia ponownie komputer. Sekwencja zadań będzie automatycznie kontynuować działanie po ponownym uruchomieniu komputera.  

Programy używające opcji **Uruchom najpierw inny program** w celu zainstalowania programu zależnego nie są obsługiwane w przypadku wdrażania systemu operacyjnego. Po włączeniu opcji pakietu **Uruchom najpierw inny program**i program zależny był już uruchamiany na komputerze docelowym, uruchamia program zależny i sekwencja zadań będzie kontynuować działanie. Jednak jeśli program zależny nie został już uruchomiony na komputerze docelowym, krok sekwencji zadań zakończy się niepowodzeniem.  

> [!NOTE]  
>  Centralna lokacja administracyjna nie ma odpowiednich zasad konfiguracji klienta wymagane do włączenia agenta dystrybucji oprogramowania podczas sekwencji zadań. Podczas tworzenia nośnika samodzielnego dla sekwencji zadań w centralnej lokacji administracyjnej, gdy sekwencja zadań zawiera krok **Zainstaluj pakiet**, w pliku CreateTsMedia.log może się pojawić następujący błąd:  
>   
>  `"WMI method SMS_TaskSequencePackage.GetClientConfigPolicies failed (0x80041001)"`  
>   
>  W przypadku nośnika samodzielnego zawierającego **zainstaluj pakiet** krok, Utwórz nośnik autonomiczny w lokacji głównej, w której jest włączony agent dystrybucji oprogramowania. Możesz też dodać **Uruchom wiersz polecenia** krokiem **Zainstaluj system Windows i program ConfigMgr** kroku i przed pierwszym **zainstaluj pakiet** kroku. **Uruchom wiersz polecenia** polecenie WMIC włączające agenta dystrybucji oprogramowania przed pierwszym uruchomieniem kroku **zainstaluj pakiet** kroku. Użyj następującego polecenia w **Uruchom wiersz polecenia** krok:  
>   
>  **Wiersz polecenia**:`WMIC /namespace:\\\root\ccm\policy\machine\requestedconfig path ccm_SoftwareDistributionClientConfig CREATE ComponentName="Enable SWDist", Enabled="true", LockSettings="TRUE", PolicySource="local", PolicyVersion="1.0", SiteSettingsKey="1" /NOINTERACTIVE`  
>   
>  Aby uzyskać więcej informacji o tworzeniu nośników autonomicznych, zobacz [tworzenia nośnika samodzielnego](../deploy-use/create-stand-alone-media.md).  

Ten krok sekwencji zadań działa tylko w standardowym systemie operacyjnym. Nie działa on w środowisku Windows PE.  

W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **oprogramowania**i wybierz **zainstaluj pakiet** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości  
 Na **właściwości** karta dla tego kroku, skonfigurować ustawienia opisane w tej sekcji.  

 **Zainstaluj pojedynczy pakiet oprogramowania**  
 To ustawienie określa pakiet oprogramowania programu Configuration Manager. Krok czeka, aż do ukończenia instalacji.  

 **Zainstaluj pakiety oprogramowania zgodnie z listą zmiennych dynamicznych**  
 Sekwencja zadań instaluje pakiety przy użyciu tego podstawową nazwę zmiennej. Podstawową nazwę zmiennej jest zestaw zmiennych sekwencji zadań zdefiniowanych dla kolekcji lub komputera. Te zmienne określają pakiety, które sekwencja zadań instaluje dla tej kolekcji lub komputera. Każda nazwa zmiennej składa się z podstawowej nazwy pospolitej i liczbowego sufiksu (zaczynając od 001). Wartość każdej zmiennej musi zawierać identyfikator pakietu i nazwę oprogramowania rozdzielone dwukropkiem.  

 W sekwencji zadań do instalowania oprogramowania przy użyciu listy zmiennych dynamicznych należy włączyć następujące ustawienie na **zaawansowane** pakietu **właściwości**: **Zezwalaj na ten program można zainstalować z sekwencji zadań pakietu instalacyjnego bez wdrożenia**  

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

 Poniższe warunki mają wpływ na pakiety zainstalowane przez sekwencję zadań:  

-   Jeśli wartość zmiennej nie należy tworzyć w poprawnym formacie lub nie określa jest prawidłowy pakiet identyfikator i nazwa, instalacja oprogramowania kończy się niepowodzeniem.  

-   Jeśli identyfikator pakietu zawiera małe litery, instalacja oprogramowania kończy się niepowodzeniem.  

-   Jeśli sekwencja zadań nie zostanie znaleziona zmienna o określonej nazwie podstawowej i sufiksie "001", sekwencja zadań nie można zainstalować wszystkie pakiety. Sekwencja zadań będzie kontynuować działanie.  
   
**Jeśli instalacja pakietu oprogramowania nie powiedzie się, kontynuuj instalowanie pozostałych pakietów na liście**  
 To ustawienie określa, że krok ma kontynuować działanie w przypadku niepowodzenia instalacji pakietu oprogramowania. Jeśli to ustawienie nie przerywać sekwencji zadań niezależnie od błędów instalacji. Jeśli to ustawienie nie zostanie określony, a instalacja zakończy się niepowodzeniem, krok natychmiast kończy się.  



##  <a name="BKMK_InstallSoftwareUpdates"></a>Instalacja aktualizacji oprogramowania  
Ten krok umożliwia zainstalowanie aktualizacji oprogramowania na komputerze docelowym. Komputer docelowy nie jest sprawdzany pod kątem dostępności odpowiednich aktualizacji oprogramowania do czasu uruchomienia tego kroku sekwencji zadań. Po uruchomieniu komputera docelowego jest oceniane pod kątem aktualizacji oprogramowania, takich jak dowolnego klienta programu Configuration Manager. W tym kroku instalacji aktualizacji oprogramowania należy wdrożyć aktualizacje na kolekcję, której członkiem jest komputer docelowy.  
>  [!IMPORTANT]
> Zainstaluj najnowszą wersję programu Windows Update Agent jest najlepszym rozwiązaniem dla uzyskania optymalnej wydajności. 
>* System Windows 7 — zobacz [artykuł 3161647 bazy wiedzy](https://support.microsoft.com/kb/3161647).
>* System Windows 8 — zobacz [artykuł 3163023 bazy wiedzy](https://support.microsoft.com/kb/3163023).

 Ten krok sekwencji zadań działa tylko w standardowym systemie operacyjnym. Nie działa on w środowisku Windows PE. Aby uzyskać informacje o zmiennych sekwencji zadań dotyczących tej akcji sekwencji zadań, zobacz [Zmienne akcji sekwencji zadań Zainstaluj aktualizacje oprogramowania](task-sequence-action-variables.md#BKMK_InstallSoftwareUpdates).

 > [!NOTE]
 > Jeśli klient nie może pobrać listy punktów zarządzania z usług lokalizacji, umożliwia określenie, ile milisekund zadanie sekwencji czeka przed ponowną instalowanie SMSTSMPListRequestTimeoutEnabled i SMSTSMPListRequestTimeout wbudowanych zmiennych aktualizacji oprogramowania lub aplikacji. Aby uzyskać więcej informacji, zobacz [wbudowane zmienne sekwencji zadań](task-sequence-built-in-variables.md).

 W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **oprogramowania**i wybierz **Zainstaluj aktualizacje oprogramowania** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości  
 Na **właściwości** karta dla tego kroku, skonfigurować ustawienia opisane w tej sekcji.  

 **Wymagane do instalacji — obowiązkowe aktualizacje oprogramowania tylko**  
 Wybierz tę opcję, aby zainstalować wszystkie obowiązkowe aktualizacje oprogramowania z terminami instalacji zdefiniowane przez administratora.  

 **Dostępne do instalacji — wszystkie aktualizacje oprogramowania**  
 Wybierz tę opcję, aby zainstalować wszystkie dostępne aktualizacje oprogramowania. Najpierw należy wdrożyć te aktualizacje do kolekcji, której członkiem jest komputer. Sekwencja zadań instaluje wszystkie dostępne aktualizacje oprogramowania na komputerach docelowych.  

 **Oceń aktualizacje oprogramowania z wyników skanowania w pamięci podręcznej**  
 Domyślnie sekwencja zadań używa wyniki skanowania w pamięci podręcznej z usługi Windows Update Agent. Wyczyść pole wyboru, aby poinstruować usługi Windows Update Agent, aby pobrać najnowszy katalog z aktualizacji oprogramowania punktu. Wybierz tę opcję, korzystając z sekwencji zadań w celu [przechwytywania i utworzyć obraz systemu operacyjnego](../deploy-use/create-a-task-sequence-to-capture-an-operating-system.md). W tym scenariuszu prawdopodobnie dużą liczbę aktualizacji oprogramowania. Wiele z tych aktualizacji będzie zależnościami, na przykład, należy zainstalować X, Y pojawia się odpowiednio. Gdy wyczyścić to ustawienie i wdrożyć sekwencję zadań do wielu klientów, wszystkie łączą się z punktem aktualizacji oprogramowania w tym samym czasie. Ten problem powoduje problemy z wydajnością podczas procesu i pobierania katalogu. Najlepszym rozwiązaniem jest ustawienie domyślne, aby użyć wyniki skanowania w pamięci podręcznej. 

Zmienną sekwencji zadań SMSTSSoftwareUpdateScanTimeout określa limit czasu skanowania aktualizacji oprogramowania w tym kroku. Wartość domyślna to 30 minut. Aby uzyskać więcej informacji, zobacz [wbudowane zmienne sekwencji zadań](task-sequence-built-in-variables.md).

### <a name="options"></a>Opcje   
 Oprócz domyślnych opcji, należy skonfigurować następujące dodatkowe ustawienia na **opcje** kartę ten krok sekwencji zadań:  

-   **Ponów ten krok, jeśli komputer zostanie nieoczekiwanie uruchomiony ponownie**  
    Jeśli jedna z aktualizacji zostanie nieoczekiwanie uruchomiony ponownie komputer, ponów próbę wykonania tego kroku. Krok powoduje włączenie tego ustawienia domyślnie z dwóch ponownych prób. Można określić od jednej do pięciu ponownych prób.  

    > [!NOTE]
    > Skonfigurować zmienną SMSTSWaitForSecondReboot, aby określić, jak długo sekwencja zadań jest wstrzymywana po ponownym uruchomieniu komputera w tym scenariuszu. Aby uzyskać więcej informacji, zobacz [wbudowane zmienne sekwencji zadań](task-sequence-built-in-variables.md).



##  <a name="BKMK_JoinDomainorWorkgroup"></a>Przyłącz do domeny lub grupy roboczej  
 Aby dodać komputer docelowy do domeny lub grupy roboczej, należy użyć tego kroku.  

 Ten krok sekwencji zadań działa tylko w standardowym systemie operacyjnym. Nie działa on w środowisku Windows PE. Aby uzyskać informacje o zmiennych sekwencji zadań dotyczących tej akcji sekwencji zadań, zobacz [Zmienne akcji sekwencji zadań Przyłącz do domeny lub grupy roboczej](task-sequence-action-variables.md#BKMK_JoinDomainWorkgroup).  

 W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **ogólne**i wybierz **Przyłącz do domeny lub grupy roboczej** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości  
 Na **właściwości** karta dla tego kroku, skonfigurować ustawienia opisane w tej sekcji.  

 **Przyłącz do grupy roboczej**  
 Wybierz tę opcję, aby przyłączyć komputer docelowy do określonej grupy roboczej. Jeśli komputer jest obecnie jest członkiem domeny, wybranie tej opcji powoduje ponowne uruchomienie komputera.  

 **Przyłącz do domeny**  
 Wybierz tę opcję, aby przyłączyć komputer docelowy do określonej domeny.  

 Opcjonalnie można wprowadzić lub wyszukać jednostkę organizacyjną w określonej domenie, do której ma zostać przyłączony komputer. Jeśli komputer jest aktualnie członkiem innej domeny lub grupy roboczej, ta opcja powoduje ponowne uruchomienie komputera. Jeśli komputer jest już członkiem innej jednostki Organizacyjnej, ponieważ usługi domenowe Active Directory nie zezwala na zmianę jednostki Organizacyjnej, za pomocą tej metody, Instalator systemu Windows ignoruje to ustawienie.  

 **Wprowadź konto z uprawnieniem do przyłączenia do domeny**  
 Kliknij przycisk **ustawić** wprowadzić nazwę użytkownika i hasło dla konta z uprawnieniami do przyłączania do domeny. Wprowadź konto w formacie:  *Domena\konto*  



## <a name="BKMK_PrepareConfigMgrClientforCapture"></a>Przygotuj klienta programu ConfigMgr do przechwycenia  
Aby usunąć lub skonfigurować klienta programu Configuration Manager na komputerze odniesienia, należy użyć tego kroku. Ta akcja przygotowuje komputer do przechwycenia w ramach procesu przetwarzania obrazów.

Począwszy od programu Configuration Manager w wersji 1610, **przygotować klienta programu ConfigMgr** kroku powoduje całkowite usunięcie klienta programu Configuration Manager, a nie tylko usunięcie informacji o kluczu. Gdy sekwencja zadań wdrażania przechwyconego obrazu systemu operacyjnego, instaluje nowy klient programu Configuration Manager zawsze.  

> [!Note]  
>  Aparat sekwencji zadań umożliwia tylko usunięcie klienta w trakcie **Utwórz i Przechwyć referencyjny obraz systemu operacyjnego** sekwencji zadań. Aparat sekwencji zadań nie powoduje usunięcia klienta podczas innych metod przechwytywania, takich jak nośniki przechwytywania lub niestandardową sekwencję zadań.

Przed 1610 wersji programu Configuration Manager w tym kroku wykonuje następujące zadania:  

-   Usunięcie sekcji właściwości konfiguracji klienta z pliku smscfg.ini w katalogu systemu Windows. Tych właściwości należą informacje specyficzne dla klienta, w tym identyfikator GUID programu Configuration Manager i inne identyfikatory klienta.  

-   Usuwa wszystkie certyfikaty komputera programu SMS lub programu Configuration Manager.  

-   Usuwa pamięci podręcznej klienta programu Configuration Manager.  

-   Wyczyszczenie przypisanej zmiennej lokacji klienta programu Configuration Manager.  

-   Usuwa wszystkie lokalne zasady programu Configuration Manager.  

-   Usuwa zaufany klucz główny dla klienta programu Configuration Manager.  

Ten krok sekwencji zadań działa tylko w standardowym systemie operacyjnym. Nie działa on w środowisku Windows PE.  

W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **obrazów**i wybierz **przygotować klienta programu ConfigMgr do przechwycenia** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości  
 Ten krok nie wymaga żadnych ustawień na **właściwości** kartę.



##  <a name="BKMK_PrepareWindowsforCapture"></a>Przygotuj system Windows do przechwycenia  
 Ten krok umożliwia określenie opcji narzędzia Sysprep, podczas przechwytywania obrazu systemu operacyjnego na komputerze odniesienia. Tej akcji sekwencji zadań uruchamia narzędzie Sysprep, a następnie ponowne uruchomienie komputera z obrazu rozruchowego środowiska Windows PE określonego dla sekwencji zadań. Ta akcja zakończy się niepowodzeniem, jeśli komputer odniesienia jest przyłączony do domeny.  

 Ten krok sekwencji zadań działa tylko w standardowym systemie operacyjnym. Nie działa on w środowisku Windows PE. Aby uzyskać informacje o zmiennych sekwencji zadań dotyczących tej akcji sekwencji zadań, zobacz [Zmienne akcji sekwencji zadań Przygotuj system Windows do przechwycenia](task-sequence-action-variables.md#BKMK_PrepareWindowsCapture).  

 W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **obrazów**i wybierz **Przygotuj system Windows do przechwycenia** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości  
 Na **właściwości** karta dla tego kroku, skonfigurować ustawienia opisane w tej sekcji.  

 **Automatycznie twórz listę sterowników pamięci masowej**  
 Wybierz tę opcję, aby umożliwić narzędziu Sysprep automatyczne utworzenie listy sterowników pamięci masowej z komputera odniesienia. Ta opcja włącza opcję tworzenia sterowników pamięci masowej w pliku sysprep.inf na komputerze odniesienia. Aby uzyskać więcej informacji o tym ustawieniu zobacz dokumentację programu Sysprep.  

 **Nie Resetuj flagi aktywacji**  
 Wybierz tę opcję, aby uniemożliwić narzędziu Sysprep resetowanie flagi aktywacji produktu.  



##  <a name="BKMK_PreProvisionBitLocker"></a>Funkcja BitLocker przed udostępnieniem  
 Ten krok umożliwia włączenie funkcji BitLocker na dysku w środowisku Windows PE. Szyfrowany jest tylko zajęty obszar dysku, dzięki czemu szyfrowanie jest znacznie szybsze. Aby zastosować opcje zarządzania kluczami, użyj kroku sekwencji zadań [Wstępne inicjowanie obsługi funkcji BitLocker](#BKMK_EnableBitLocker) po zainstalowaniu systemu operacyjnego. Ten krok działa tylko w środowisku Windows PE. Nie działa on w standardowym systemie operacyjnym.  

> [!IMPORTANT]  
>  Wstępne inicjowanie obsługi funkcji BitLocker wymaga co najmniej Windows 7. Komputer musi zawierać obsługiwanej i włączone modułu Trusted Platform Module (TPM).  

 W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **dysków**i wybierz **funkcja BitLocker przed udostępnieniem** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości  
 Na **właściwości** karta dla tego kroku, skonfigurować ustawienia opisane w tej sekcji.  

 **Zastosuj funkcję BitLocker do określonego dysku**  
 Określ dysk, dla którego chcesz włączyć funkcję BitLocker. Szyfrowany jest tylko zajęty obszar dysku.  

 **Pomiń ten krok w przypadku komputerów, które nie ma modułu TPM lub gdy moduł TPM nie jest włączona**  
 Wybierz tę opcję, aby pominąć szyfrowanie dysku na komputerze, który nie zawiera modułu TPM obsługiwana lub włączone zgodnie z potrzebami. Na przykład można użyć tej opcji, podczas wdrażania systemu operacyjnego na maszynie wirtualnej.  



##  <a name="BKMK_ReleaseStateStore"></a>Zwolnij Magazyn stanów  
 Ten krok jest używany do powiadamiania stanu o ukończeniu akcji przechwytywania lub przywracania punktu migracji. Użyj tego kroku w połączeniu z **Zażądaj magazynu stanów**, **Przechwyć stan użytkownika**, i **Przywróć stan użytkownika** czynności. Korzystania z tych kroków do przeprowadzenia migracji danych stanu użytkownika przy użyciu punktu migracji stanu i narzędzia migracji stanu użytkowników (USMT).  

 Aby uzyskać więcej informacji o zarządzaniu stanem użytkownika podczas wdrażania systemów operacyjnych, zobacz [Zarządzanie stanem użytkownika](../get-started/manage-user-state.md).  

 Jeśli używasz **Zażądaj magazynu stanów** krok, aby zażądać dostępu do punktu migracji stanu do *przechwytywania* stanu użytkownika, ten krok powiadomi punkt migracji stanu, który przetworzył przechwytywania jest pełny. Punkt migracji stanu oznaczy wtedy dane stanu użytkownika jako dostępne do przywrócenia. Punkt migracji stanu ustawia dostępu formantu uprawnienia dostępu do danych o stanie użytkownika tak, aby tylko przywracanie komputer ma dostęp tylko do odczytu.  

 Jeśli używasz **Zażądaj magazynu stanów** krok, aby zażądać dostępu do punktu migracji stanu do *przywrócić* stanu użytkownika, ten krok powiadomi punkt migracji stanu procesu przywracania jest pełny. Migracja stanu punktu, a następnie aktywuje jej ustawień przechowywania skonfigurowanych danych.  

> [!IMPORTANT]  
>  Najlepszym rozwiązaniem jest skonfigurowanie **Kontynuuj przy błędzie** opcji w kontekście jakichkolwiek kroków między **Zażądaj magazynu stanów** i **Zwolnij Magazyn stanów** czynności. Każdy **Zażądaj magazynu stanów** kroku musi mieć zgodną **Zwolnij Magazyn stanów** kroku.  

 Ten krok sekwencji zadań działa tylko w standardowym systemie operacyjnym. Nie działa on w środowisku Windows PE. Aby uzyskać informacje o zmiennych sekwencji zadań dotyczących tej akcji sekwencji zadań, zobacz [Zmienne akcji sekwencji zadań Zwolnij magazyn stanów](task-sequence-action-variables.md#BKMK_ReleaseStateStore).  

 W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **stanu użytkownika**i wybierz **Zwolnij Magazyn stanów** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości  
 Ten krok nie wymaga żadnych ustawień na **właściwości** kartę.



##  <a name="BKMK_RequestStateStore"></a>Zażądaj magazynu stanów  
 Ten krok umożliwia zażądanie dostępu do punktu migracji stanu podczas przechwytywania lub przywracania stanu.  

 Aby uzyskać więcej informacji o zarządzaniu stanem użytkownika podczas wdrażania systemów operacyjnych, zobacz [Zarządzanie stanem użytkownika](../get-started/manage-user-state.md).  

 Użyj tego kroku w połączeniu z **Zwolnij Magazyn stanów**, **Przechwyć stan użytkownika**, i **Przywróć stan użytkownika** czynności. Korzystania z tych kroków do przeprowadzenia migracji stanu komputera przy użyciu punktu migracji stanu i narzędzia migracji stanu użytkowników (USMT).  

> [!NOTE]  
>  Podczas tworzenia nowego punktu migracji stanu, magazynu stanu użytkownika są niedostępne z maksymalnie jedną godzinę. Aby przyspieszyć dostępność, należy dostosować ustawienia właściwości w punkcie migracji stanu w celu wyzwolenia aktualizacji pliku kontroli lokacji.  

 Ten krok sekwencji zadań działa w standardowym systemie operacyjnym i w środowisku Windows PE w przypadku narzędzia USMT w trybie offline. Aby uzyskać informacje o zmiennych sekwencji zadań dla tej akcji sekwencji zadań, zobacz [Zmienne akcji sekwencji zadań Zażądaj magazynu stanów](task-sequence-action-variables.md#BKMK_RequestState).  

W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **stanu użytkownika**i wybierz **Zażądaj magazynu stanów** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości  
 Na **właściwości** karta dla tego kroku, skonfigurować ustawienia opisane w tej sekcji.  

 **Przechwyć stan z komputera**  
 Znalezienia punktu migracji stanu, który spełnia wymagania minimalne zgodnie z konfiguracją w ustawieniach punktu migracji stanu. Na przykład **maksymalna liczba klientów** i **minimalna ilość wolnego miejsca na dysku**. Ta opcja nie gwarantuje, że wystarczającą ilość miejsca jest dostępne w czasie migracji stanu. Ta opcja żąda dostępu do punktu migracji stanu na potrzeby przechwytywania stanu użytkownika i ustawienia z komputera.  

 Jeśli w lokacji programu Configuration Manager ma wiele punktów migracji stanu aktywnego, ten krok znajduje punkt migracji stanu z dostępnego miejsca na dysku. Sekwencja zadań wysyła zapytanie do punktu zarządzania, aby uzyskać listę punktów migracji stanu i ocenia każdy aż do znalezienia, który spełnia wymagania minimalne.  

 **Przywróć stan z innego komputera**  
 Żądanie dostępu do punktu migracji stanu w celu przywrócenia stanu użytkownika przechwyconych wcześniej i ustawienia na komputerze docelowym.  

 Jeśli istnieje wiele punktów migracji stanu, ten krok znajduje punkt migracji stanu ma stan dla komputera docelowego.  

 **Liczba ponownych prób**  
 Ile razy ten krok próbuje znaleźć punkt migracji stanu odpowiednie przed niepowodzeniem.  

 **Opóźnienie ponowienia próby (w sekundach)**  
 Czas oczekiwania (w sekundach) kroku sekwencji zadań między ponownymi próbami.  

 **Jeśli konto komputera nie może nawiązać połączenia z magazynem stanów, użyj konta dostępu do sieci.**  
 Jeśli sekwencja zadań nie może uzyskać dostęp do punktu migracji stanu, używając konta komputera, używa do łączenia poświadczenia konta dostępu do sieci. Ta opcja jest mniej bezpieczne, ponieważ inne komputery można używać konta dostępu do sieci przechowywany stan dostępu do. Ta opcja może być konieczne, jeśli komputer docelowy nie jest przyłączony do domeny.  



##  <a name="BKMK_RestartComputer"></a>Uruchom ponownie komputer  
 Ten krok umożliwia ponowne uruchomienie komputera z uruchomioną sekwencją zadań. Po ponownym uruchomieniu komputer będzie automatycznie kontynuować działanie do następnego kroku w sekwencji zadań.  

 Ten krok działa w standardowym systemie operacyjnym lub w środowisku Windows PE. Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań dotyczących tej akcji sekwencji zadań, zobacz [ponowne uruchomienie zmienne akcji sekwencji zadań komputera](task-sequence-action-variables.md#BKMK_RestartComputer).  

 W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **ogólne**i wybierz **Uruchom ponownie komputer** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości  
 Na **właściwości** karta dla tego kroku, skonfigurować ustawienia opisane w tej sekcji.  

 **Obraz rozruchowy przypisany do tej sekwencji zadań**  
 Wybierz tę opcję na komputerze docelowym użyć obrazu rozruchowego przypisanego do sekwencji zadań. Sekwencja zadań używa obraz rozruchowy do uruchomienia kolejnych kroków w środowisku Windows PE.  

 **Aktualnie zainstalowany domyślny system operacyjny**  
 Wybierz tę opcję na komputerze docelowym, aby uruchomić ponownie komputer za pomocą zainstalowanego systemu operacyjnego.  

 **Powiadom użytkownika przed ponownym uruchomieniem**  
 Wybierz tę opcję, aby wyświetlić powiadomienie dla użytkownika przed ponownym uruchomieniem komputera docelowego. Domyślnie kroku wybiera tej opcji.  

 **Komunikat z powiadomieniem**  
 Wprowadź komunikat powiadomienia, aby wyświetlić dla użytkownika przed ponownym uruchomieniem komputera docelowego.  

 **Limit czasu wyświetlania komunikatu**  
 Określ ilość czasu w sekundach przed ponownym uruchomieniem komputera docelowego. Wartość domyślna to 60 sekund.  



##  <a name="BKMK_RestoreUserState"></a>Przywróć stan użytkownika  
 Ten krok umożliwia zainicjowanie narzędzia do migracji stanu (USMT) użytkownika, do przywrócenia stanu i ustawień użytkownika na komputerze docelowym. Ten krok można używać w połączeniu z **Przechwyć stan użytkownika** kroku.  

 Aby uzyskać więcej informacji o zarządzaniu stanem użytkownika podczas wdrażania systemów operacyjnych, zobacz [Zarządzanie stanem użytkownika](../get-started/manage-user-state.md).  

 Ten krok z **Zażądaj magazynu stanów** i **Zwolnij Magazyn stanów** kroki, aby zapisać lub przywrócić ustawienia stanu z punktu migracji stanu. Z narzędzia USMT 3.0 lub nowszego ta opcja zawsze odszyfrowuje Magazyn stanów narzędzia USMT za pomocą klucza szyfrowania wygenerowanego i zarządzanego przez program Configuration Manager.  

 **Przywróć stan użytkownika** krok zapewnia kontrolę nad ograniczonym podzbiorem najczęściej używanych opcji narzędzia USMT. Określ dodatkowe opcje wiersza polecenia z OSDMigrateAdditionalRestoreOptions zmienną sekwencji zadań.  

> [!IMPORTANT]  
>  Jeśli w tym kroku jest używana do celu niezwiązanym ze scenariuszem wdrażania systemu operacyjnego, Dodaj [Uruchom ponownie komputer](#BKMK_RestartComputer) kroku bezpośrednio po **Przywróć stan użytkownika** kroku.  

 Ten krok działa tylko w standardowym systemie operacyjnym. Nie działa on w środowisku Windows PE. Aby uzyskać informacje o zmiennych sekwencji zadań dla tej akcji sekwencji zadań, zobacz [Zmienne akcji sekwencji zadań Przywróć stan użytkownika](task-sequence-action-variables.md#BKMK_RestoreUserState).  

 W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **stanu użytkownika**i wybierz **Przywróć stan użytkownika** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości  
 Na **właściwości** karta dla tego kroku, skonfigurować ustawienia opisane w tej sekcji.  

 **Pakiet narzędzia migracji stanu użytkownika**  
 Określ pakiet zawierający wersję narzędzia USMT dla tego kroku do użycia. Ten pakiet nie wymaga programu. Po uruchomieniu kroku sekwencji zadań używa wersji narzędzia USMT z określonego pakietu. Określ pakiet zawierający wersję 32-bitowy lub 64-bitowego narzędzia USMT. Architektura narzędzia USMT zależy od architektury systemu operacyjnego, do którego sekwencja zadań jest przywracania stanu. 

 **Przywróć wszystkie przechwycone profile użytkowników z opcjami standardowymi**  
 Przywraca przechwycone profile użytkowników z opcjami standardowymi. Aby dostosować opcje, które przywraca narzędzia USMT, wybierz **dostosować Przechwytywanie profili użytkowników**.  

 **Dostosuj sposób przywracania profili użytkowników**  
 Umożliwia dostosowanie plików, które mają zostać przywrócone na komputerze docelowym. Kliknij pozycję **Pliki**, aby określić pliki konfiguracji w pakiecie narzędzia USMT, za pomocą których zostaną przywrócone profile użytkowników. Aby dodać plik konfiguracji, wprowadź nazwę pliku w polu **Nazwa pliku**, a następnie kliknij przycisk **Dodaj**. W okienku plików zawiera pliki konfiguracyjne, które korzysta z narzędzia USMT. Należy określić plik XML definiuje plik użytkownika, który przywraca narzędzia USMT.  

 **Przywróć profile użytkowników komputera lokalnego**  
 Przywraca profile użytkowników komputera lokalnego. Te profile nie są użytkownicy domeny. Należy przypisać nowe hasła do przywróconych kont użytkowników lokalnych. Narzędzie USMT nie można migrować oryginalnych haseł. Wprowadź nowe hasło w polu **Hasło** i potwierdź hasło w polu **Potwierdź hasło**.  

 **Kontynuuj, jeśli nie można przywrócić niektórych plików**  
 Kontynuuje Przywracanie stanu i ustawień użytkownika, nawet w przypadku narzędzia USMT nie można przywrócić niektórych plików. Krok powoduje włączenie tej opcji domyślnie. Jeśli wyłączysz tę opcję i narzędzia USMT napotkał błędy podczas przywracania plików, w tym kroku nie powiedzie się natychmiast. Narzędzie USMT nie przywraca wszystkie pliki.   

 **Włącz pełne rejestrowanie**  
 Włącz tę opcję, aby wygenerować bardziej szczegółowe informacje pliku dziennika. Podczas przywracania stanu, sekwencja zadań domyślnie generuje plik Loadstate.log, który w folderze dziennika sekwencji zadań \windows\system32\ccm\logs.  



##  <a name="BKMK_RunCommandLine"></a>Uruchom wiersz polecenia  
 Ten krok umożliwia uruchomienie określonego wiersza polecenia.  

 Ten krok działa w standardowym systemie operacyjnym lub w środowisku Windows PE. Aby uzyskać informacje o zmiennych sekwencji zadań dotyczących tej akcji sekwencji zadań, zobacz [Zmienne akcji sekwencji zadań Uruchom wiersz polecenia](task-sequence-action-variables.md#BKMK_RunCommand).  

 W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **ogólne**i wybierz **Uruchom wiersz polecenia** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości  
 Na **właściwości** karta dla tego kroku, skonfigurować ustawienia opisane w tej sekcji.  

 **Wiersz polecenia**  
 Określa uruchamiany wiersz polecenia. To pole jest wymagane. Najlepszym rozwiązaniem, na przykład vbs i .exe jest tym rozszerzeń nazw plików. Uwzględnij wszystkie wymagane pliki ustawień, opcje wiersza polecenia i przełączniki.  

 Jeśli nazwa pliku nie ma określone rozszerzenie nazwy pliku, programu Configuration Manager prób .com, .exe i. bat. Jeśli nazwa pliku ma rozszerzenie, które nie jest plikiem wykonywalnym, programu Configuration Manager spróbuje zastosować skojarzenie lokalne. Na przykład jeśli wiersz polecenia to plik readme.gif, programu Configuration Manager uruchomi aplikację określoną na komputerze docelowym w celu otwierania plików GIF.  

 Przykłady:  

 `setup.exe /a`  

 `cmd.exe /c copy Jan98.dat c:\sales\Jan98.dat`  

> [!NOTE]  
>  Aby pomyślnie uruchomić, należy poprzedzić akcje wiersza polecenia z **cmd.exe /c** polecenia. Przykład działania te obejmują przekierowywanie danych wyjściowych, przekazanie w potoku i skopiuj poleceń.  

 **Wyłączyć przekierowania systemu plików 64-bitowych**  
 64-bitowe systemy operacyjne umożliwia przekierowania systemu plików WOW64 domyślnie uruchamiających wiersze polecenia. To zachowanie jest prawidłowo znaleźć 32-bitowe wersje systemu operacyjnego, plików wykonywalnych i bibliotek. Wybierz tę opcję, aby zablokować używanie przekierowania systemu plików WOW64. System Windows uruchamia polecenia przy użyciu natywnych 64-bitowych wersjach systemu operacyjnego, plików wykonywalnych i bibliotek. Ta opcja nie ma znaczenia, gdy uruchomione w 32-bitowym systemie operacyjnym.  

 **Rozpocznij w**  
 Określa folder z plikiem wykonywalnym programu (do 127 znaków). Ten folder może być ścieżką bezwzględną na komputerze docelowym lub ścieżką względną do folderu punktu dystrybucji, który zawiera pakiet. To pole jest opcjonalne.  

 Przykłady:  

 **c:\OfficeXP**  

 **I386**  

> [!NOTE]  
>  **Przeglądaj** przycisk umożliwia wyszukanie na komputerze lokalnym dla plików i folderów. Coś po wybraniu muszą także istnieć na komputerze docelowym w tej samej lokalizacji i z tego samego pliku i nazwy folderów.  

 **Pakiet**  
 Po określeniu plików lub programów w wierszu polecenia, który nie ma jeszcze na komputerze docelowym, wybierz tę opcję, aby określić pakiet programu Configuration Manager, który zawiera odpowiednie pliki. Ten pakiet nie wymaga programu. Ta opcja nie jest wymagana, jeśli określone pliki znajdują się na komputerze docelowym.  

 **Limit czasu**  
 Określa wartość, która reprezentuje, jak długo programu Configuration Manager umożliwia wiersza polecenia do uruchomienia. Ta wartość może być od 1 do 999 minut. Wartość domyślna to 15 minut.  

 Ta opcja jest domyślnie wyłączona.  

> [!IMPORTANT]  
>  Wprowadź wartość, która nie zezwala na wystarczająco dużo czasu dla określonego polecenia pomyślnie, w tym kroku nie powiedzie się. W całej sekwencji zadań może zakończyć się niepowodzeniem w zależności od innych ustawień kontroli. Po przekroczeniu limitu czasu program Configuration Manager zakończy proces wiersza polecenia.  

 **Uruchom ten krok jako następujące konto**  
 Określa, że wiersz polecenia ma być uruchamiany przy użyciu konta użytkownika systemu Windows innego niż lokalne konto systemowe.  

> [!NOTE]  
>  Aby uruchomić proste skrypty lub polecenia z innego konta, po zainstalowaniu systemu operacyjnego, musisz dodać konto na komputerze. Ponadto należy przywrócić profilu konta użytkownika systemu Windows do uruchamiania bardziej złożonych programów, takich jak Instalator Windows.  

 **Konta**  
 Określa konto użytkownika systemu Windows, które tego kroku jest używana do uruchamiania wiersza polecenia. W wierszu polecenia jest uruchamiany z uprawnieniami określonego konta. Kliknij pozycję **Ustaw**, aby określić konto użytkownika lokalnego lub domeny.  

> [!IMPORTANT]  
>  Jeśli ten krok Określa konto użytkownika i działa w środowisku Windows PE, akcja nie powiedzie się. Nie można przyłączyć środowiska Windows PE do domeny. Plik smsts.log rejestruje tego błędu.  



##  <a name="BKMK_RunPowerShellScript"></a>Uruchom skrypt programu PowerShell  
 Ten krok umożliwia uruchomienie określonego skryptu programu PowerShell.  

 Ten krok działa w standardowym systemie operacyjnym lub w środowisku Windows PE. Aby można było uruchomić t en krok w środowisku Windows PE, program Power Shell musi być włączony w obrazie rozruchowym. Program Windows PowerShell (WinPE-PowerShell) można włączyć na karcie **Składniki opcjonalne** we właściwościach obrazu rozruchowego. Aby uzyskać więcej informacji o modyfikowaniu obrazu rozruchowego, zobacz [zarządzanie obrazami rozruchowymi](../get-started/manage-boot-images.md).  

> [!NOTE]  
>  Program PowerShell nie jest domyślnie włączony w systemach operacyjnych Windows Embedded.  

W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **ogólne**i wybierz **Uruchom skrypt programu PowerShell** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości  
 Na **właściwości** karta dla tego kroku, skonfigurować ustawienia opisane w tej sekcji.  

 **Pakiet**  
 Określ pakiet programu Configuration Manager, który zawiera skrypt programu PowerShell. Jeden pakiet może zawierać wiele skryptów programu PowerShell.  

 **Nazwa skryptu**  
 Określa nazwę skryptu programu PowerShell, który ma zostać uruchomiony. To pole jest wymagane.  

 **Parametry**  
 Określa parametry przekazywane do skryptu programu Windows PowerShell. Te parametry są takie same jak parametry skryptu programu Windows PowerShell w wierszu polecenia.  

> [!IMPORTANT]  
>  Podaj parametry używane przez skrypt, a nie parametry wiersza polecenia programu Windows PowerShell.  
>   
>  Poniżej przedstawiono przykład zawierający prawidłowe parametry:  
>   
>  `-MyParameter1 MyValue1 -MyParameter2 MyValue2`  
>   
>  Poniżej przedstawiono przykład zawierający nieprawidłowe parametry. Pierwsze dwa elementy są parametry wiersza polecenia programu Windows PowerShell (**- NoLogo** i **- ExecutionPolicy Unrestricted**). Skrypt nie korzystać z tych parametrów.  
>   
>  `-NoLogo -ExecutionPolicy Unrestricted -File MyScript.ps1 -MyParameter1 MyValue1 -MyParameter2 MyValue2`  

 **Zasady wykonywania programu PowerShell**  
 Określić, które skrypty programu Windows PowerShell (jeśli istnieje), musisz zezwolić na komputerze. Wybierz jedną z następujących zasad wykonywania:  

-   **Wszystkie podpisane**: Uruchamiać tylko skrypty podpisane przez zaufanego wydawcę  

-   **Niezdefiniowany**: Nie definiują żadnych zasad wykonywania  

-   **Obejście**: Załaduj wszystkie pliki konfiguracji i uruchamianie wszystkich skryptów. Jeśli niepodpisany skrypt można pobrać z Internetu, programu Windows PowerShell nie jest wyświetlany monit o zgodę przed uruchomieniem skryptu.  

> [!IMPORTANT]  
>  Program PowerShell 1.0 nie obsługuje zasad wykonywania Niezdefiniowane i Obejście.  



##  <a name="child-task-sequence"></a>Uruchomienie sekwencji zadań

Począwszy od programu Configuration Manager w wersji 1710, możesz dodać nowy krok, który zostanie wykonany innej sekwencji zadań. Spowoduje to utworzenie relacji nadrzędny podrzędny między sekwencji zadań. Sekwencja zadań podrzędnych można utworzyć jedną sekwencją zadań moduły, wielokrotnego użytku.

Po dodaniu sekwencji zadań podrzędnych do sekwencji zadań należy wziąć pod uwagę następujące instrukcje:
 - Sekwencje zadań nadrzędnych i podrzędnych skutecznie są połączone w jedną zasadę, która działa na kliencie.
 - Środowisko jest globalnego. Jeśli nadrzędny sekwencja zadań ustawia zmienną, a następnie sekwencja zadań podrzędnych zmiany tej zmiennej, zachowuje najpóźniejszą wartość. Jeśli sekwencja zadań podrzędnych tworzy nową zmienną, jest ona dostępna w pozostałej części sekwencji zadań nadrzędnej.
 - Komunikaty o stanie są wysyłane na normalny dla operacji sekwencji pojedyncze zadanie.
 - Sekwencje zadań tworzyć wpisy w pliku smsts.log w nowy dziennik wpisów, dzięki któremu można wyczyścić podczas sekwencji zadań podrzędnych rozpoczyna się.

W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **ogólne**i wybierz **uruchamiania sekwencji zadań** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości
 Na **właściwości** karta dla tego kroku, skonfigurować ustawienia opisane w tej sekcji.  

**Wybierz sekwencję zadań do wykonania**  
 Kliknij przycisk **Przeglądaj** do wybierania sekwencji zadań podrzędnych. **Wybierz sekwencję zadań** okno dialogowe nie wyświetla nadrzędnego sekwencji zadań.



##  <a name="BKMK_SetDynamicVariables"></a>Ustaw zmienne dynamiczne  
 Ten krok umożliwia wykonaj następujące czynności:  

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

W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **ogólne**i wybierz **Ustaw zmienne dynamiczne** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości  
 Na **właściwości** karta dla tego kroku, skonfigurować ustawienia opisane w tej sekcji.  

**Dynamiczne reguły i zmienne**  
 Aby ustawić zmienną dynamiczną do użycia w sekwencji zadań, należy dodać regułę. Następnie ustaw wartość każdej zmiennej określonej w regule. Ponadto należy dodać co najmniej jedną zmienną bez dodawania reguły. Po dodaniu regułę, wybierz jedną z następujących kategorii:  

 -   **Komputer**: Obliczyć wartości tagu zasobu sprzętu, identyfikator UUID, numer seryjny lub adres MAC. W razie potrzeby, należy ustawić wiele wartości. Jeśli dowolna wartość ma wartość PRAWDA, reguła oblicza jako true. Na przykład Poniższa reguła ma jako wartość true, jeśli numer seryjny urządzenia to 5892087, i adres MAC jest 22-A4-5A-13-78-26.  

     `IF Serial Number = 5892087 OR MAC address = 26-78-13-5A-A4-22 THEN`  

-   **Lokalizacja**: Obliczyć wartości bramy domyślnej sieci  

-   **Producent i Model**: Obliczyć wartości producenta i modelu komputera. Aby reguła mogła zwrócić wartość true, producent i model muszą zwrócić wartość true.   

    <!-- for future edits: an escape code must be used for the bolded asterisk character, but may be removed somewhere along the way. Instead of five asterisk, should be bold tags with &#42; in-between -->

    Począwszy od programu Configuration Manager 1610 wersji, można określić znak gwiazdki (**&#42;**) i znak zapytania (**?**) jako symbole wieloznaczne, gdzie **&#42;** odpowiada wielu znaki i **?** reprezentuje pojedynczy znak. Na przykład ciąg "DELL * 900?" będzie odpowiadała DELL-ABC-9001 i DELL9009. 

    Określ znak gwiazdki (**&#42;**) i znak zapytania (**?**) jako symbole wieloznaczne, gdzie **&#42;** odpowiada wielu znaków i **?** reprezentuje pojedynczy znak. Na przykład ciąg "DELL * 900?" odpowiada DELL-ABC-9001 DELL9009.

-   **Zmienna sekwencji zadań**: Dodawanie zmiennej sekwencji zadań, warunek i wartość do obliczenia. Reguła zwraca wartość true, gdy ustawiona wartość zmiennej spełnia określony warunek.  

    Określ co najmniej jedną zmienną do ustawienia dla regułę, która zwraca wartość true, lub ustawić zmienne bez używania reguły. Wybierz istniejącą zmienną, lub utworzyć zmienną niestandardową.  

     -   **Istniejące zmienne sekwencji zadań**: Wybierz co najmniej jedną zmienną z listy istniejących zmiennych sekwencji zadań. Nie można wybierać zmiennych tablicy.  

     -   **Niestandardowe zmienne sekwencji zadań**: Zdefiniowanie niestandardowej zmiennej sekwencji zadań. Można również określić istniejącą zmienną sekwencji zadań. To ustawienie jest przydatne określić istniejącą tablicę zmiennych, taką jak OSDAdapter, ponieważ tablic zmiennych nie ma na liście istniejących zmiennych sekwencji zadań.  

Po wybraniu zmiennych reguły musisz podać wartość każdej zmiennej. Dla zmiennej jest ustawiana określona wartość, gdy reguła zwraca wartość true. Dla każdej zmiennej można wybrać ustawienie **Wartość tajna**, aby ukryć wartość zmiennej. Domyślnie niektóre istniejące zmienne, takie jak zmienna sekwencji zadań OSDCaptureAccountPassword, ukrywają wartości.  

> [!IMPORTANT]  
>  Programu Configuration Manager usunie wszystkie zmiennej wartości oznaczone jako **wartość tajna** podczas importowania sekwencji zadań z **Ustaw zmienne dynamiczne** kroku. Ponownie wprowadzić wartość zmiennej dynamicznej po zaimportowaniu sekwencji zadań.  



##  <a name="BKMK_SetTaskSequenceVariable"></a>Ustaw zmienną sekwencji zadań  
Aby ustawić wartość zmiennej używanej w sekwencji zadań, należy użyć tego kroku.  

Ten krok działa w standardowym systemie operacyjnym lub w środowisku Windows PE. Zmienne sekwencji zadań są odczytywane przez akcje sekwencji zadań i określają działanie tych akcji. Aby uzyskać więcej informacji na temat określonych zmiennych sekwencji zadań akcji, zobacz [zmienne akcji sekwencji zadań](task-sequence-action-variables.md). Aby uzyskać więcej informacji na temat określonych zmiennych sekwencji zadań wbudowanych, zobacz [wbudowane zmienne sekwencji zadań](/sccm/osd/understand/task-sequence-built-in-variables).

W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **ogólne**i wybierz **Ustaw zmienną sekwencji zadań** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości  
 Na **właściwości** karta dla tego kroku, skonfigurować ustawienia opisane w tej sekcji.  

 **Zmienną sekwencji zadań**  
 Określ nazwę wbudowanej sekwencji zadań lub zmiennej akcji, lub określ z własnej nazwy zmiennych zdefiniowanych przez użytkownika.  

 **Wartość**  
 Sekwencja zadań ustawia zmienną tej wartości. Ta zmienna sekwencji zadań należy ustawić wartość inna zmienna sekwencji zadań z nazwa_zmiennej % składni.  



##  <a name="BKMK_SetupWindowsandConfigMgr"></a>Zainstaluj system Windows i program ConfigMgr  
 Aby wykonać przejście ze środowiska Windows PE do nowego systemu operacyjnego, należy użyć tego kroku. Ten krok sekwencji zadań stanowi wymaganą część każdego wdrożenia systemu operacyjnego. Go instaluje klienta programu Configuration Manager w nowym systemie operacyjnym i przygotowuje sekwencję zadań kontynuować wykonywanie w nowym systemie operacyjnym.  

 Ten krok działa tylko w środowisku Windows PE. Nie działa on w standardowym systemie operacyjnym. Aby uzyskać więcej informacji o zmiennych sekwencji zadań dotyczących tej akcji sekwencji zadań, zobacz [zmienne akcji sekwencji zadań Zainstaluj system Windows i program ConfigMgr](task-sequence-action-variables.md#BKMK_SetupWindows).  

 Ten krok zamienia zmienne katalogów pliku sysprep.inf lub unattend.xml, takie jak % WINDIR % i % ProgramFiles % katalogu instalacyjnego środowiska Windows PE X:\Windows. Sekwencja zadań ignoruje zmienne określone przy użyciu tych zmiennych środowiskowych.  

 Ten krok sekwencji zadań umożliwia wykonywanie następujących czynności:  

1.  Czynności wstępne: Windows PE  

    1.  Zastąp zmienne sekwencji zadań w pliku unattend.xml.  

    2.  Pobierz pakiet, który zawiera klienta programu Configuration Manager. Dodaj pakiet do wdrożonym obrazie.  

2.  Instalowanie systemu Windows  

    1.  Instalacja oparta na obrazie  

        1.  Wyłączenie klienta programu Configuration Manager na ilustracji, jeśli istnieje. Innymi słowy Wyłącz automatyczne uruchamianie usługi klienta Configuration Manager.  

        2.  Aktualizowanie rejestru wdrożonego obrazu, aby uruchomić wdrożony system operacyjny z tej samej litery dysku jako komputer referencyjny.  

        3.  Uruchom ponownie, aby wdrożony system operacyjny.  

        4.  Miniinstalacja systemu Windows jest uruchamiana za pomocą wcześniej określonego pliku sysprep.inf lub Unattend.XML odpowiedzi, który zawiera wszystkie pominięte interakcje użytkownika końcowego. Jeśli używasz **Zastosuj ustawienia sieci** krok, aby dołączyć do domeny, a następnie te informacje są w pliku odpowiedzi. Miniinstalacja systemu Windows przyłączeniu komputera do domeny.  

    2.  Instalacja wykonywana przy użyciu pliku Setup.exe.  Uruchamia plik Setup.exe, który wykonuje typowy proces instalacji systemu Windows:  

        1.  Pakiet uaktualnienia kopii systemu operacyjnego, określona w **Zastosuj System operacyjny** krok na dysku twardym.  

        2.  Uruchom ponownie, aby nowo wdrożonym systemie operacyjnym.  

        3.  Miniinstalacja systemu Windows jest uruchamiana za pomocą wcześniej określonego pliku sysprep.inf lub unattend.xml plik odpowiedzi, który zawiera wszystkie ustawienia interfejsu użytkownika pomijane. Jeśli używasz **Zastosuj ustawienia sieci** krok, aby dołączyć do domeny, a następnie te informacje są w pliku odpowiedzi. Miniinstalacja systemu Windows przyłączeniu komputera do domeny.  

3.  Konfigurowanie klienta programu Configuration Manager  

    1.  Po zakończeniu miniinstalacji systemu Windows sekwencja zadań zostaje wznowiona przy użyciu polecenia setupcomplete.cmd.  

    2.  Włącz lub Wyłącz konta administratora lokalnego w zależności od opcji wybranej w **Zastosuj ustawienia systemu Windows** kroku.  

    3.  Zainstaluj klienta programu Configuration Manager przy użyciu pobranego wcześniej pakietu i właściwości instalacji określonych w tym kroku. Klient jest instalowany w "trybie obsługi" Aby uniemożliwić przetwarzanie nowych żądań zasad do momentu ukończenia sekwencji zadań.  

    4.  Oczekiwanie na uzyskanie pełnej funkcjonalności klienta.  

4.  Sekwencja zadań będzie nadal występować, uruchomieniem następnego kroku.  

<!-- Engineering confirmed that the task sequence does nothing with respect to group policy processing.
> [!NOTE]  
>  The **Setup Windows and ConfigMgr** task sequence action is responsible for running Group Policy on the newly installed computer. The Group Policy is applied after the task sequence is finished.  
-->

W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **obrazów**i wybierz **Zainstaluj system Windows i program ConfigMgr** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości  
 Na **właściwości** karta dla tego kroku, skonfigurować ustawienia opisane w tej sekcji.  

 **Pakiet klienta**  
 Kliknij przycisk **Przeglądaj**, następnie wybierz pakiet instalacyjny klienta programu Configuration Manager do użycia w ramach tego kroku.  

 **Użyj pakietu przedprodukcyjnego klienta, jeśli jest dostępny**  
 Jeśli pakiet klienta środowiska przedprodukcyjnego jest dostępny, sekwencja zadań używa tego pakietu, a nie pakiet produkcyjny klienta. Klient przedprodukcyjny to nowsza wersja do testowania w środowisku produkcyjnym. Kliknij przycisk **Przeglądaj**, następnie wybierz pakiet instalacyjny klienta przedprodukcyjnego do użycia w ramach tego kroku.  

 **Właściwości instalacji**  
 Przypisanie lokacji i konfiguracja domyślna są automatycznie określane przez akcję sekwencji zadań. W tym polu można określić dodatkowe właściwości instalacji, które mają być używane podczas instalacji klienta. Aby wprowadzić wiele właściwości instalacji, oddziel je spacjami.  

 Możesz określić opcje wiersza polecenia, których chcesz użyć podczas instalacji klienta. Na przykład można wprowadzić polecenie **/skipprereq: silverlight.exe** w celu nakazania programowi CCMSetup.exe, aby nie instalował wstępnie wymaganego programu Microsoft Silverlight. Aby uzyskać więcej informacji o dostępnych opcjach wiersza polecenia programu CCMSetup.exe, zobacz [o właściwościach instalacji klienta](../../core/clients/deploy/about-client-installation-properties.md).  

### <a name="options"></a>Opcje
> [!NOTE]
> Nie należy włączać **Kontynuuj przy błędzie** na **opcje** kartę. Jeśli w tym kroku jest błąd, sekwencja zadań nie powiedzie się, czy to ustawienie jest włączone.



##  <a name="BKMK_UpgradeOS"></a>Uaktualnij System operacyjny  
 > [!TIP]  
 > Począwszy od systemu Windows 10 w wersji 1709, nośnikami wiele wersji. Podczas konfigurowania sekwencji zadań w celu za pomocą pakietu uaktualnienia systemu operacyjnego lub obrazu systemu operacyjnego, należy wybrać [obsługiwana wersja](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-as-a-client).

 Ten krok umożliwia uaktualnienie starszej wersji systemu Windows do nowszej wersji systemu Windows 10.  

 Ten krok sekwencji zadań działa tylko w standardowym systemie operacyjnym. Nie działa on w środowisku Windows PE.  

W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **obrazów**i wybierz **Uaktualnij System operacyjny** Aby dodać ten krok. 

### <a name="properties"></a>Właściwości  
Na **właściwości** karta dla tego kroku, skonfigurować ustawienia opisane w tej sekcji.  

**Pakiet uaktualnienia**  
 Wybierz tę opcję, aby określić pakiet uaktualniający systemu operacyjnego Windows 10 do użycia podczas uaktualniania.  

**Ścieżka źródłowa**  
 Określa lokalną lub sieciową ścieżkę do nośnika systemu Windows 10 używa tego Instalatora systemu Windows. To ustawienie odpowiada opcji wiersza polecenia Instalatora systemu Windows **/InstallFrom**. Można również określić zmienną, taką jak %moja_ścieżka_zawartości% lub %DPC01%. Aby używać zmiennej w ścieżce źródłowej, należy wcześniej określić tę zmienną w sekwencji zadań. Jeśli na przykład używasz kroku [Pobierz zawartość pakietu](#BKMK_DownloadPackageContent) w sekwencji zadań, możesz określić zmienną lokalizacji pakietu uaktualniającego systemu operacyjnego. Następnie można użyć tej zmiennej dla ścieżki źródłowej danego kroku.  

**Edition**  
 Określ wersję w ramach nośnika systemu operacyjnego do użycia podczas uaktualniania.  

**Klucz produktu**  
 Określ klucz produktu do zastosowania podczas procesu uaktualniania  

**Podaj poniższą zawartość sterowników w Instalatorze systemu Windows podczas uaktualniania**  
 Dodaj sterowniki do komputera docelowego podczas procesu uaktualniania. To ustawienie odpowiada opcji wiersza polecenia Instalatora systemu Windows **/InstallDriver**. Sterowniki muszą być zgodne z systemem Windows 10. Określ jedną z następujących opcji:  

-   **Pakiet sterowników**: Kliknij przycisk **Przeglądaj** i wybierz istniejący pakiet sterowników z listy.  

-   **Zawartość przejściowa**:  Wybierz tę opcję, aby określić lokalizację pakietu sterowników. Możesz wybrać folder lokalny, ścieżkę sieciową lub zmienną sekwencji zadań. Aby używać zmiennej w ścieżce źródłowej, należy wcześniej określić tę zmienną w sekwencji zadań. Na przykład za pomocą kroku [Pobierz zawartość pakietu](task-sequence-steps.md#BKMK_DownloadPackageContent).  

**Limit czasu (w minutach)**  
 Określa liczbę minut, zanim Menedżera konfiguracji nie powiodło się w tym kroku. Ta opcja jest przydatna, jeśli zatrzymuje przetwarzanie Instalatora systemu Windows, ale nie zakończyć.  

**Skanowanie zgodności Instalatora systemu Windows bez rozpoczynania uaktualnienia**  
 Wykonaj skanowanie zgodności Instalatora systemu Windows bez rozpoczynania procesu uaktualniania. To ustawienie odpowiada opcji wiersza polecenia Instalatora systemu Windows **/Compat ScanOnly**. Po wybraniu tej opcji, należy wdrożyć całe źródło instalacji. Instalator zwraca kod zakończenia w wyniku skanowania. Poniższa tabela zawiera niektóre z najczęściej używanych kodów zakończenia.  

|Kod zakończenia|Szczegóły|  
|-|-|  
|MOSETUP_E_COMPAT_SCANONLY (0xC1900210)|Brak problemów ze zgodnością („powodzenie”).|  
|MOSETUP_E_COMPAT_INSTALLREQ_BLOCK (0xC1900208)|Problemy ze zgodnością możliwości podejmowania działań.|  
|MOSETUP_E_COMPAT_MIGCHOICE_BLOCK (0xC1900204)|Wybrana opcja migracji jest niedostępna, na przykład uaktualnienie wersji Enterprise do Professional.|  
|MOSETUP_E_COMPAT_SYSREQ_BLOCK (0xC1900200)|Brak uprawnień w przypadku systemu Windows 10.|  
|MOSETUP_E_COMPAT_INSTALLDISKSPACE_BLOCK (0xC190020E)|Brak wystarczającej ilości wolnego miejsca na dysku.|  

Aby uzyskać więcej informacji o tym parametrze, zobacz [Windows Setup Command-Line Options](https://msdn.microsoft.com/library/windows/hardware/dn938368\(v=vs.85\).aspx) (Opcje wiersza polecenia Instalatora systemu Windows)  

**Ignoruj wszystkie komunikaty o zgodności możliwe do odrzucenia**  
 Określa, że Instalator ukończy instalację, ignorując wszystkie komunikaty o zgodności możliwe do odrzucenia. To ustawienie odpowiada opcji wiersza polecenia Instalatora systemu Windows **/Compat IgnoreWarning**.  

**Dynamicznie Aktualizuj Instalatora systemu Windows z usługi Windows Update**  
 Włącz Instalatora, aby wykonać operacje aktualizacji dynamicznych, takie jak wyszukiwanie, Pobierz i zainstaluj aktualizacje. To ustawienie odpowiada opcji wiersza polecenia Instalatora systemu Windows **/DynamicUpdate**. To ustawienie nie jest zgodny z aktualizacji oprogramowania programu Configuration Manager. Włącz tę opcję, jeśli zarządzasz aktualizacji z autonomicznego systemu Windows Server Update Services (WSUS) lub usługi Windows Update dla firm.  

**Zastąpienia zasad i użyj domyślnej usługi Microsoft Update** tymczasowo zastąpić zasady lokalne w czasie rzeczywistym do uruchomienia aktualizacji dynamicznych i pobrania aktualizacji z witryny Windows Update na komputerze.
