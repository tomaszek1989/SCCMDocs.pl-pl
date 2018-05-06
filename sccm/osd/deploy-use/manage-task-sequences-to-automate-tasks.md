---
title: Zarządzanie sekwencjami zadań
titleSuffix: Configuration Manager
description: Tworzenia, edytowania, wdrażanie, importowania i eksportowania sekwencji zadań w celu zarządzania nimi i automatyzowania zadań w środowisku.
ms.date: 04/10/2018
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: a1f099f1-e9b5-4189-88b3-f53e3b4e4add
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 26d43b1ee065f3ae0b1221ca81e69f6cb1da6f6c
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="manage-task-sequences-to-automate-tasks-in-system-center-configuration-manager"></a>Zarządzanie sekwencjami zadań w celu zautomatyzowania zadań w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Użyj sekwencji zadań, aby automatyzować czynności w środowisku programu Configuration Manager. Te kroki można wdrożyć obraz systemu operacyjnego na komputerze docelowym, kompilacji i przechwytywania obrazu systemu operacyjnego z zestawu plików instalacji systemu operacyjnego i przechwytywania i przywracania informacji o stanie użytkownika. Sekwencje zadań znajdują się w konsoli programu Configuration Manager. W **Biblioteka oprogramowania** obszaru roboczego, rozwiń węzeł **systemów operacyjnych** i wybierz **sekwencje zadań**. **Sekwencje zadań** węzła, w tym podfolderów, które tworzysz, są replikowane w całej hierarchii programu Configuration Manager. Informacje dotyczące planowania, zobacz [uwagi dotyczące planowania automatyzacji zadań](../plan-design/planning-considerations-for-automating-tasks.md).  

 Poniższe sekcje umożliwiają zarządzanie sekwencjami zadań.

##  <a name="BKMK_CreateTaskSequence"></a> Tworzenie sekwencji zadań  
 Utwórz sekwencje zadań za pomocą Kreatora tworzenia sekwencji zadań. Ten kreator umożliwia tworzenie następujących typów sekwencji zadań:  

|Typ sekwencji zadań|Więcej informacji|  
|------------------------|----------------------|  
|[Sekwencja zadań instalacji systemu operacyjnego](create-a-task-sequence-to-install-an-operating-system.md)|Ten typ sekwencji zadań tworzy kroki w celu zainstalowania systemu operacyjnego, a także opcję migracji danych użytkownika, dołączenia aktualizacji oprogramowania i zainstalować aplikacje.|  
|[Sekwencji zadań w celu uaktualnienia systemu operacyjnego](create-a-task-sequence-to-upgrade-an-operating-system.md)|Ten typ sekwencji zadań utworzenie czynności niezbędnych do uaktualnienia systemu operacyjnego, a także opcję dołączenia aktualizacji oprogramowania i instalowanie aplikacji.|  
|[Sekwencji zadań w celu przechwycenia systemu operacyjnego](create-a-task-sequence-to-capture-an-operating-system.md)|Ten typ sekwencji zadań utworzenie czynności niezbędnych do utworzenia i przechwycenia systemu operacyjnego z komputera odniesienia. Możesz dołączyć aktualizacje oprogramowania i zainstalować aplikacje na komputerze odniesienia przed przechwyceniem obrazu.|  
|[Sekwencji zadań w celu przechwycenia i przywrócenia stanu użytkownika](create-a-task-sequence-to-capture-and-restore-user-state.md)|Ta sekwencja zadań zapewnia czynności, które można dodać do istniejącej sekwencji zadań w celu przechwycenia i przywrócenia danych stanu użytkownika.|  
|[Niestandardową sekwencję zadań](create-a-custom-task-sequence.md)|Ten typ sekwencji zadań nie dodaje żadnych kroków do sekwencji zadań. Przeprowadź edycję sekwencji zadań i dodać kroki do sekwencji zadań, po jego utworzeniu.|  



## <a name="return-to-previous-page-when-a-task-sequence-fails"></a>Powrót do poprzedniej strony, gdy sekwencja zadań nie powiodło się.
Po uruchomieniu sekwencji zadań i awarii, można powrócić do poprzedniej strony. W poprzednich wersjach programu Configuration Manager trzeba było ponownego uruchomienia sekwencji zadań, jeśli wystąpił błąd. Użyj **Wstecz** przycisk w następujących scenariuszach:

- Gdy komputer jest uruchamiany w środowisku Windows PE, dialogowym bootstrap sekwencji zadań może być wyświetlany, zanim sekwencja zadań będzie dostępna. Po kliknięciu przycisku Dalej w tym scenariuszu sekwencja zadań na ostatniej stronie wyświetla komunikat, że nie dostępnych sekwencji zadań. Teraz, możesz kliknąć **Wstecz** ponowić wyszukiwanie uzyskać dostępne sekwencje zadań. Ten proces można powtarzać do czasu udostępnienia sekwencji zadań.
- Po uruchomieniu sekwencji zadań, ale zależnych pakietów zawartości nie są jeszcze dostępne w punktach dystrybucji, sekwencja zadań kończy się niepowodzeniem. Brak zawartości nie została jeszcze rozesłana, rozpowszechnienie go teraz. Lub zaczekaj na zawartość ma być dostępne w punktach dystrybucji. Następnie kliknij przycisk **Wstecz** mają wyszukiwania sekwencji zadań ponownie dla zawartości.

##  <a name="BKMK_ModifyTaskSequence"></a> Edytowanie sekwencji zadań  
 Sekwencję zadań można modyfikować, dodając lub usuwając kroki, dodawanie lub usuwanie grup, lub zmieniając kolejność kroków. Użyj poniższej procedury, aby zmodyfikować istniejącą sekwencję zadań:  

> [!IMPORTANT]  
>  Podczas edytowania sekwencji zadań, która została utworzona za pomocą Kreatora tworzenia sekwencji zadań, akcji lub typ tego kroku może być nazwa kroku. Na przykład można napotkać krok o nazwie "Podziel dysk 0" oznacza akcję kroku o typie [Format i partycji](../understand/task-sequence-steps.md#BKMK_FormatandPartitionDisk). Wszystkie kroki sekwencji zadań są udokumentowane według typu, nie musi to być nazwa kroku, który jest wyświetlany w edytorze.  

#### <a name="to-edit-a-task-sequence"></a>Aby edytować sekwencję zadań  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Sekwencje zadań**.  

3.  Z listy **Sekwencja zadań** wybierz sekwencję do edytowania.  

4.  Na karcie **Narzędzia główne** w grupie **Sekwencja zadań** kliknij przycisk **Edytuj**, a następnie wykonaj jedną z następujących czynności:  

    -   Aby dodać krok sekwencji zadań, kliknij przycisk **Dodaj**, wybierz typ kroku, a następnie kliknij krok, aby dodać. Aby na przykład dodać krok Uruchom wiersz polecenia, kliknij przycisk **Dodaj**, wybierz pozycję **Ogólny**, a następnie kliknij pozycję **Uruchom wiersz polecenia**.  

         Lista wszystkich kroków sekwencji zadań oraz ich typów znajduje się w tabeli pod tą procedurą.  

    -   Aby dodać grupę do sekwencji zadań, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **Nowa grupa**. Po dodaniu grupy można następnie dodać kroki do grupy.  

    -   Aby zmienić kolejność kroków i grup w sekwencji zadań, wybierz odpowiedni krok lub grupę, którą chcesz zmienić kolejność, a następnie użyj **Przenieś element w górę** lub **Przenieś element w dół** ikon. Jednocześnie można przenosić tylko jeden krok lub grupę.  

    -   Aby usunąć krok lub grupę, wybierz odpowiednie elementy i kliknij przycisk **Usuń**.  

5.  Kliknij przycisk **OK** , aby zapisać zmiany.  

 Aby uzyskać listę dostępnych kroków sekwencji zadań, zobacz [czynności sekwencji zadań](../understand/task-sequence-steps.md).  

## <a name="configure-software-center-properties"></a>Skonfiguruj właściwości Centrum oprogramowania
Poniższa procedura umożliwia skonfigurowanie szczegóły sekwencji zadań wyświetlana w Centrum oprogramowania. Te informacje są wyłącznie w celach informacyjnych.  
1. W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** obszaru roboczego, rozwiń węzeł **systemów operacyjnych**i wybierz **sekwencje zadań**.
2. Wybierz sekwencję zadań do edycji, a następnie kliknij przycisk **właściwości**.
3. Na **ogólne** kartę, dostępne są następujące ustawienia w programie Software Center:
  - **Wymagane jest ponowne uruchomienie**: Umożliwia użytkownikowi wiedzieć, czy ponowne uruchomienie jest wymagane podczas instalacji.
  - **Pobierz rozmiar (MB)**: Określa, ile megabajtów są wyświetlane w programie Software Center dla sekwencji zadań.  
  - **Szacowany czas wykonywania (minuty)**: Określa szacowany czas wykonywania w minutach, które jest wyświetlane w Centrum oprogramowania dla sekwencji zadań.

## <a name="configure-advanced-task-sequence-settings"></a>Konfigurowanie ustawień sekwencji zadań zaawansowane
Poniższa procedura umożliwia skonfigurowanie szczegóły sekwencji zadań wyświetlana w Centrum oprogramowania. Te informacje są wyłącznie w celach informacyjnych.  
1. W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** obszaru roboczego, rozwiń węzeł **systemów operacyjnych**i wybierz **sekwencje zadań**.
2. Wybierz sekwencję zadań do edycji, a następnie kliknij przycisk **właściwości**.
3. Na **zaawansowane** kartę, dostępne są następujące ustawienia:

    - **Uruchom najpierw inny program**    
    Zaznacz to pole wyboru, aby uruchomić inny program (w inny pakiet), przed uruchomieniem sekwencji zadań. To pole wyboru jest domyślnie wyczyszczone. Program, który będzie wybierany do uruchamiania najpierw nie musi być anonsowana oddzielnie.

        > [!IMPORTANT]     
        To ustawienie ma zastosowanie tylko do sekwencji zadań, które są uruchamiane w pełnej wersji systemu operacyjnego. Menedżera konfiguracji ignoruje to ustawienie, jeśli sekwencja zadań została uruchomiona przy użyciu środowiska PXE lub nośnika rozruchowego.

    - **Pakiet**     
        Po wybraniu **Uruchom najpierw inny program**, wyszukaj pakiet, który zawiera program, który musi zostać uruchomiony przed tej sekwencji zadań.

    - **Program**     
    Po wybraniu **Uruchom najpierw inny program**, wybierz program, który musi zostać uruchomiony przed tę sekwencję zadań z **Program** listy rozwijanej.

        > [!NOTE]    
        > Jeśli nie wybrany program do uruchomienia na komputerze klienckim, sekwencja zadań nie działa. Jeśli wybrany program jest uruchomiony pomyślnie, go nie Uruchom ponownie, nawet jeśli sekwencja zadań zostanie uruchomiona ponownie na tym samym kliencie.
 
    - **Wyłącz tę sekwencję zadań na komputerach, na których jest wdrożona**    
    Jeśli wybierzesz tę opcję, wszystkich wdrożeniach zawierających tę sekwencję zadań, są tymczasowo wyłączone. Sekwencja zadań zostanie usunięty z listy wdrożeń dostępna do uruchamiania. Aplikacja nie działać do czasu ponownego włączenia. Ta opcja jest domyślnie wyczyszczone.

    - **Maksymalny dozwolony czas wykonywania**    
    Określa maksymalny czas (w minutach), który oczekuje na uruchomienie sekwencji zadań na komputerze docelowym. Użyj liczbę całkowitą równą lub większą niż zero. Wartością domyślną jest 120 minut.

        > [!IMPORTANT]    
        > Jeśli używasz okna obsługi dla kolekcji, na którym działa ta sekwencja zadań, może wystąpić konflikt, jeśli **maksymalny dozwolony czas wykonywania** jest większa od czasu zaplanowanego okna obsługi. Jeśli maksymalny czas wykonywania jest równa **0**, sekwencja zadań zaczyna się w oknie konserwacji. Będzie działać do czasu jego ukończenia lub niepowodzenia po zamknięciu okna obsługi. W związku z tym sekwencje zadań z maksymalnie wykonawczego ustawioną **0** mogą zostać uruchomione poza koniec ich okna obsługi. Jeśli ustawisz maksymalny czas wykonywania do określonego okresu (nie **0**) przekraczający długość dowolnej z dostępnych okien obsługi, a następnie sekwencja zadań nie działa. Aby uzyskać więcej informacji, zobacz [używanie okien obsługi](/sccm/core/clients/manage/collections/use-maintenance-windows).
 
        Jeśli wartość jest ustawiana jako **0**, program Configuration Manager ocenia maksymalny dozwolony czas uruchomienia jako **12** godzin (720 minut) w celu monitorowania postępu. Jednak sekwencja zadań zaczyna tak długo, jak czas trwania odliczania nie może przekraczać wartości okna konserwacji.

    > [!NOTE]    
    > Po osiągnięciu maksymalnego dozwolonego czasu wykonywania programu Configuration Manager zatrzymuje sekwencja zadań jest ustawiona do uruchamiania z uprawnieniami administracyjnymi i Zezwól użytkownikom na interakcję z tym ustawieniem program nie jest zaznaczone. Sama sekwencja zadań nie został on zatrzymany, osiągnięto programu Configuration Manager Zatrzymuje monitorowanie sekwencji zadań po maksymalny dozwolony czas wykonywania. 

    - **Użyć obrazu rozruchowego**   
        Włącz tę opcję, aby użyć wybranego obrazu rozruchowego po uruchomieniu sekwencji zadań. 

        Kliknij przycisk **Przeglądaj** wybierz obraz rozruchowy inny. Usuń zaznaczenie tej opcji, aby uniemożliwić korzystanie z wybranego obrazu rozruchowego po uruchomieniu sekwencji zadań.

    - **Ta sekwencja zadań można uruchomić na dowolnej platformie**     
        Jeśli wybierzesz tę opcję, Menedżer konfiguracji nie sprawdza typ platformy komputera docelowego po wdrożeniu sekwencji zadań. Ta opcja jest domyślnie wybrana.

    - **Ta sekwencja zadań można uruchomić tylko na określonych platformach klienckich**    
        Ta opcja określa procesory, wersji systemu operacyjnego i dodatków service pack, na których można uruchomić tej sekwencji zadań. Po wybraniu tej opcji, również należy wybrać co najmniej jedną platformę z listy. Domyślnie nie zaznaczono żadnych platform. Program Configuration Manager używa tych informacji podczas jest obliczane, które komputerów docelowych w kolekcji odbierania wdrożona sekwencja zadań.

        > [!NOTE]    
        > Sekwencji zadań jest uruchamiany z nośnika rozruchowego lub przy rozruchu w środowisku PXE, ta opcja jest ignorowana po uruchomieniu sekwencji zadań jako opcję **ten program można uruchomić na dowolnej platformie** jest zaznaczone.



## <a name="configure-high-impact-task-sequence-settings"></a>Konfigurowanie ustawień sekwencji zadań o dużym wpływie na działanie
Można ustawić sekwencji zadań jako poważnych i dostosowywać komunikaty, które użytkownicy otrzymują po uruchomieniu sekwencji zadań.

### <a name="set-a-task-sequence-as-a-high-impact-task-sequence"></a>Ustawianie sekwencji zadań za pomocą sekwencji zadań o dużym wpływie na działanie
Użyj poniższej procedury, aby ustawić sekwencji zadań jako dużym znaczeniu.
> [!NOTE]    
> Wszystkie sekwencje zadań, która spełnia określone warunki automatycznie jest zdefiniowany jako dużym znaczeniu. Aby uzyskać więcej informacji, zobacz [zarządzania wdrożeniami o wysokim ryzyku](/sccm/protect/understand/settings-to-manage-high-risk-deployments).

1. W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** obszaru roboczego, rozwiń węzeł **systemów operacyjnych**i wybierz **sekwencje zadań**.
2. Wybierz sekwencję zadań do edycji, a następnie kliknij przycisk **właściwości**.
3. Na **powiadomienie użytkownika** wybierz opcję **to sekwencję zadań poważnych**.

### <a name="create-a-custom-notification-for-high-risk-deployments"></a>Utwórz niestandardowe powiadomienie w przypadku wdrożeń o wysokim ryzyku
Poniższa procedura umożliwia utworzenie niestandardowe powiadomienie w przypadku wdrożeń o dużym znaczeniu.
1. W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** obszaru roboczego, rozwiń węzeł **systemów operacyjnych**i wybierz **sekwencje zadań**.
2. Wybierz sekwencję zadań do edycji, a następnie kliknij przycisk **właściwości**.
3. Na **powiadomienie użytkownika** wybierz opcję **używać tekstu niestandardowego**.
>  [!NOTE]    
>  Tekst powiadomienia użytkownika można ustawić tylko podczas **to sekwencję zadań poważnych** jest zaznaczone.

4. Skonfiguruj następujące ustawienia (maksymalnie 255 znaków dla każdego pola tekstowego):

  **Tekst nagłówka powiadomienia użytkownika**: Określa niebieski tekst wyświetlany na powiadomienie użytkownika Centrum oprogramowania. Na przykład w domyślnie powiadomienie użytkownika, ta sekcja zawiera "Potwierdź do uaktualnienia systemu operacyjnego na tym komputerze."

  **Tekst komunikatu powiadomienia użytkownika**: Istnieją trzy pola tekstowe zawierających treść niestandardowe powiadomienie. Wszystkie pola tekstowe wymagają, aby dodać tekstu.
  - Pierwsze pole tekstowe: Określa główną część tekstu, zwykle zawierającego instrukcje dla użytkownika. Na przykład w domyślnie powiadomienie użytkownika, ta sekcja zawiera "Uaktualnianie systemu operacyjnego jest czasochłonne i komputer może być kilka razy ponownie."
  - Drugie pole tekstowe: Określa pogrubioną w głównej części tekstu. Na przykład w domyślnie powiadomienie użytkownika, ta sekcja zawiera "to uaktualnienie w miejscu instaluje nowy system operacyjny i automatycznie przeprowadzanie migracji aplikacji, danych i ustawień".
  - Trzecie pole tekstowe: Określa ostatni wiersz tekstu w polu pogrubiony tekst. Na przykład w domyślnie powiadomienie użytkownika, ta sekcja zawiera "kliknij przycisk Instaluj, aby rozpocząć. W przeciwnym razie kliknij przycisk Anuluj."   
    
Załóżmy, że możesz skonfigurować następujące powiadomienie niestandardowych we właściwościach.

![Niestandardowe powiadomienie użytkownika na karcie właściwości sekwencji zadań](..\media\user-notification.png)

Następujący komunikat powiadomienia wyświetlany, gdy użytkownik końcowy otworzy instalacji w programie Software Center.

![Dostosowane zadanie sekwencji powiadamianie użytkownika końcowego w programie Software Center](..\media\user-notification-enduser.png)


##  <a name="BKMK_DistributeTS"></a> Dystrybucja zawartości, do której odwołuje się sekwencja zadań  
 Przed uruchomieniem na klientach sekwencji zadań odwołującej się do zawartości należy rozesłać ową zawartość do punktów dystrybucji. W dowolnym momencie można wybrać sekwencję zadań i rozesłać jej zawartość w celu utworzenia nowej listy pakietów odniesienia do dystrybucji. Po wprowadzeniu zmian w sekwencji zadań obejmujących zaktualizowaną zawartość należy ponownie rozesłać zawartość, zanim sekwencja zadań zostanie udostępniona klientom. Aby rozesłać zawartość, do której odwołuje się sekwencja zadań, należy wykonać następującą procedurę.  

#### <a name="to-distribute-referenced-content-to-distribution-points"></a>Aby rozesłać zawartość z odwołaniem do punktów dystrybucji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Sekwencje zadań**.  

3.  Z listy **Sekwencja zadań** wybierz sekwencję, którą chcesz rozesłać.  

4.  Na karcie **Narzędzia główne** w grupie **Wdrażanie** kliknij przycisk **Dystrybuuj zawartość** , aby uruchomić Kreatora dystrybucji zawartości.  

5.  Na **ogólne** Sprawdź, czy wybrano właściwą sekwencję zadań, do dystrybucji. Następnie kliknij przycisk **Dalej**.  

6.  Na stronie **Zawartość** sprawdź zawartość do rozesłania, na przykład obraz rozruchowy, do którego odwołuje się sekwencja zadań, a następnie kliknij przycisk **Dalej**.  

7.  Na **miejsce docelowe zawartości** Określ kolekcje, punkt dystrybucji lub grupę punktów dystrybucji, które chcesz rozesłać zawartość sekwencji zadań. Następnie kliknij przycisk **Dalej**.  

    > [!IMPORTANT]  
    >  Jeśli wybrana sekwencja zadań odwołuje się do zawartości, która została już wysłana do określonego punktu dystrybucji, ten punkt dystrybucji nie będzie wymieniony na liście w kreatorze.  

8.  Ukończ pracę kreatora.  

 Można wstępnie przygotować zawartość, do której odwołuje się sekwencja zadań. Configuration Manager tworzy skompresowany, wstępnie przygotowany plik zawartości zawierający pliki, skojarzone zależności i skojarzone metadane wybranej zawartości. Następnie możesz ręcznie zaimportować zawartość na serwer lokacji, do lokacji dodatkowej albo punktu dystrybucji. Aby uzyskać więcej informacji na temat wstępnego przygotowania plików zawartości, zobacz [wstępnie przygotować zawartość](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_prestage).  



##  <a name="BKMK_DeployTS"></a> Wdrażanie sekwencji zadań  
 Aby wdrożyć sekwencję zadań na komputerach w kolekcji, należy wykonać następującą procedurę.  

> [!WARNING]  
>  Można zarządzać zachowaniem wdrożeń sekwencji zadań wysokiego ryzyka. Wdrożenie wysokiego ryzyka to wdrożenie, które jest instalowane automatycznie i może mieć niepożądane wyniki. Na przykład sekwencji zadań, która ma cel **wymagane** która wdraża system operacyjny jest uznawana za wdrożenie wysokiego ryzyka. Aby uzyskać więcej informacji, zobacz [ustawienia zarządzania wdrożeniami o wysokim ryzyku](../../protect/understand/settings-to-manage-high-risk-deployments.md).  

> [!NOTE]  
>  Komunikaty o stanie wdrożenia sekwencji zadań będą wyświetlane w oknie Komunikat w lokacji głównej, jednak nie będą wyświetlane w centralnej lokacji administracyjnej.  

#### <a name="to-deploy-a-task-sequence"></a>Aby wdrożyć sekwencję zadań    

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Sekwencje zadań**.  

3.  Z listy **Sekwencja zadań** wybierz sekwencję, którą chcesz wdrożyć.  

4.  Na karcie **Narzędzia główne** w grupie **Wdrażanie** kliknij przycisk **Wdróż**.  

    > [!NOTE]  
    >  Jeśli przycisk **Wdróż** będzie niedostępny, oznacza to, że sekwencja zawiera nieprawidłowe odwołanie. Popraw odwołanie, a następnie ponów próbę wdrożenia sekwencji zadań.  

5.  Na stronie **Ogólne** określ poniższe informacje, a następnie kliknij przycisk **Dalej**.  

    -   **Sekwencja zadań**: Określ sekwencję zadań, które mają zostać wdrożone. Domyślnie w tym polu będzie wyświetlana wybrana sekwencja zadań.  

    -   **Kolekcja**: Określ kolekcję zawierającą komputery, aby uruchomić sekwencję zadań.  

         Nie należy wdrażać sekwencji zadań, która instaluje system operacyjny w nieodpowiednich kolekcjach, takich jak **wszystkie systemy** kolekcji. Należy sprawdzić, czy wybrana kolekcja zawiera jedynie te komputery, na których ma zostać uruchomiona sekwencja zadań.  

        > [!NOTE]  
        >  W przypadku wdrożenia wysokiego ryzyka, takiego jak wdrożenie systemu operacyjnego, **Wybieranie kolekcji** wyświetlane tylko kolekcje niestandardowe zgodne z ustawieniami weryfikacji wdrożenia skonfigurowanymi we właściwościach lokacji. Wdrożenia wysokiego ryzyka są zawsze ograniczone do kolekcji niestandardowych, kolekcji tworzonych przez Ciebie i wbudowanej kolekcji **Nieznane komputery** . Podczas tworzeniu wdrożenia wysokiego ryzyka nie można wybrać wbudowanej kolekcji, takiej jak **Wszystkie systemy**. Usuń zaznaczenie pola wyboru **Ukryj kolekcje z elementem członkowskim liczbą większą niż minimalny rozmiar skonfigurowany dla lokacji** Aby wyświetlić wszystkie kolekcje niestandardowe zawierające liczbę klientów niż skonfigurowany maksymalny rozmiar. Aby uzyskać więcej informacji, zobacz [ustawienia zarządzania wdrożeniami o wysokim ryzyku](../../protect/understand/settings-to-manage-high-risk-deployments.md).  
        >   
        >  Ustawienia weryfikacji wdrożenia zależą od bieżącego członkostwa w kolekcji. Po wdrożeniu sekwencji zadań członkostwo w kolekcji nie jest ponownie szacowane na potrzeby ustawień wdrożenia wysokiego ryzyka.  
        >   
        >  Na przykład, załóżmy, że ustawisz **domyślny rozmiar** do 100 i **maksymalny rozmiar** do 1000. Podczas tworzenia wdrożenia wysokiego ryzyka, **Wybieranie kolekcji** okna są wyświetlane tylko kolekcje zawierające mniej niż 100 klientów. Jeśli wyczyścisz **Ukryj kolekcje z elementem członkowskim liczbą większą niż minimalny rozmiar skonfigurowany dla lokacji** ustawienie, jest wyświetlany w oknie kolekcje zawierające mniej niż 1000 klientów.  
        >   
        >  W przypadku wybrania kolekcji zawierającej rolę lokacji stosuje się następujące działania:  
        >   
        >  -   Jeśli kolekcja zawiera serwer systemu lokacji i skonfigurowano ustawienia weryfikacji wdrożenia w celu blokowania kolekcji z serwerami systemu lokacji, to występuje błąd. Nie można kontynuować, tworzenie wdrożenia.  
        > -   Jeśli jeden z następujących kryteriów ma zastosowanie, Kreatora wdrażania oprogramowania wyświetla ostrzeżenie o wysokim ryzyku. Aby kontynuować, musisz zaakceptować utworzenie wdrożenia wysokiego ryzyka. Lokacji generuje komunikat o stanie inspekcji.
        >     - Jeśli kolekcja zawiera serwer systemu lokacji i skonfigurowano ustawienia weryfikacji wdrożenia w celu ostrzegania o kolekcje z serwerami systemu lokacji
        >     - W przypadku przekroczenia domyślnej wartości rozmiaru
        >     - Jeśli kolekcja zawiera serwer  

    -   **Komentarze (opcjonalne)**: Określ dodatkowe informacje opisujące to wdrożenie sekwencji zadań.  
    - **Wybierz szablon wdrażania**: Począwszy od programu Configuration Manager w wersji 1802,<!--1357391--> można zapisywać i określ Szablon wdrożenia sekwencji zadań.     

         > [!IMPORTANT]
         > W 1802 wersji programu Configuration Manager niektóre elementy nie są zapisywane w szablonie.  <!--510610--> Upewnij się, że po uruchomieniu Kreatora wdrażania należy zastosować następujące elementy:
         > - Instalacja oprogramowania 
         > - Planowanie 
         > - Przed pobraniem zawartości
 
6.  Na stronie **Ustawienia wdrażania** określ poniższe informacje, a następnie kliknij przycisk **Dalej**.  

    -   **Cel**: Z listy rozwijanej wybierz jedną z następujących opcji:  

        -   **Dostępne**: Jeśli sekwencja zadań jest wdrażana dla użytkownika, użytkownik będzie widział opublikowaną sekwencję zadań w katalogu aplikacji i może zainstalować ją na żądanie. Jeśli sekwencja zadań jest wdrażana na urządzeniu, użytkownik będzie ją widział w Centrum oprogramowania i zainstalować ją na żądanie.  

        -   **Wymagane**: Sekwencja zadań zostanie wdrożona automatycznie, zgodnie ze skonfigurowanym harmonogramem. Jeśli sekwencja zadań nie jest ukryty, użytkownik nadal można śledzić stan wdrożenia. Mogą również zainstalować sekwencję zadań przed upływem ostatecznego terminu przy użyciu programu Software Center.  

    -   **Wdróż automatycznie zgodnie z harmonogramem, czy użytkownik jest zalogowany**: Ta opcja nie jest dostępna podczas wdrażania sekwencji zadań.  

    -   **Wyślij pakiety wznawiania**: Jeśli dla celu wdrożenia wybrano opcję **wymagane** i ta opcja jest zaznaczona, lokacji wyśle pakiet wznawiania do komputerów przed uruchomieniem wdrożenia. Ten pakiet wznawia działanie komputera ze stanu uśpienia w ostatecznym terminie instalacji. Aby użyć tej opcji, należy skonfigurować komputery i sieci do używania funkcji Wake On LAN.  

    -   **Zezwalaj klientom mierzonego połączenia internetowego na pobieranie zawartości po upływie ostatecznego terminu instalacji, co może pociągnąć za sobą dodatkowe koszty**: Jeśli sekwencja zadań, który instaluje aplikację, ale niewdrażającej systemu operacyjnego, można określić, czy zezwalać klientom na pobieranie zawartości po ostateczny termin instalacji, jeśli korzystają z mierzonych połączeń internetowych. Dostawcy Internetu czasami naliczają opłaty według ilości wysyłanych i odbieranych danych podczas taryfowego połączenia z Internetem.  

        > [!NOTE]  
        >  Gdy przy użyciu mierzonego połączenia internetowego może działać w przypadku sekwencji zadań, które nie są wdrażane przez system operacyjny, nie jest obsługiwane.  

    -   **Wymagaj zgody administratora, jeśli użytkownicy zażądają tej aplikacji**: Ta opcja nie jest dostępna podczas wdrażania sekwencji zadań.  

    -   **Udostępnij dla następujących**: Określ, czy sekwencja zadań będzie dostępna do klientów programu Configuration Manager, nośników lub środowiska PXE.  

        > [!IMPORTANT]  
        >  W przypadku zautomatyzowanych wdrożeń sekwencji zadań należy użyć ustawienia **Tylko nośniki i PXE (ukryte)** . Aby komputer automatycznie rozruch do wdrożenia bez interakcji użytkownika, wybierz **Zezwalaj na nienadzorowane wdrożenie systemu operacyjnego** i ustaw zmienną SMSTSPreferredAdvertID jako część tego nośnika. Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań, zobacz [wbudowane zmienne sekwencji zadań](../understand/task-sequence-built-in-variables.md)  

7.  Na stronie **Planowanie** określ poniższe informacje, a następnie kliknij przycisk **Dalej**.  

    > [!IMPORTANT]  
    >  Przy uruchamianiu klienta środowiska Windows PE za pomocą środowiska PXE lub nośnika rozruchowego klient nie rozpoznaje harmonogramów wdrażania (godziny uruchomienia, wygaśnięcia lub ostatecznego terminu). Harmonogramy można konfigurować tylko w przypadku wdrożeń na klientach uruchamianych za pomocą pełnego systemu operacyjnego Windows. Należy rozważyć zastosowanie innych metod, takich jak okna obsługi, do kontrolowania aktywnych sekwencji zadań wdrożonych na klientach uruchamianych ze środowiska Windows PE.  

    -   **Zaplanuj, kiedy to wdrożenie stanie się dostępne**: Określ datę i godzinę, kiedy sekwencja zadań będzie dostępna do uruchamiania na komputerze docelowym. W przypadku zaznaczenia pola wyboru **UTC** to ustawienie zapewni, że sekwencja zadań będzie dostępna dla wielu komputerów docelowych jednocześnie zamiast w różnych godzinach uzależnionych od lokalnego czasu na komputerach docelowych.  

         Jeśli czas rozpoczęcia będzie wcześniejszy niż wymagany czas, klient pobierze sekwencję zadań zgodnie z określonym czasem rozpoczęcia.  

    -   **Zaplanuj, kiedy to wdrożenie wygaśnie**: Określ datę i godzinę wygaśnięcia sekwencji zadań na komputerze docelowym. W przypadku zaznaczenia pola wyboru **UTC** to ustawienie zapewni, że sekwencja zadań wygaśnie dla wielu komputerów docelowych jednocześnie zamiast w różnych godzinach uzależnionych od lokalnego czasu na komputerach docelowych.  

    -   **Harmonogram przypisania**: Określ, kiedy wymagana sekwencja zadań jest uruchomiona na komputerze docelowym. Można dodawać wiele harmonogramów.  

         Można określić datę i godzinę rozpoczęcia harmonogramu, jego częstotliwość: tygodniową, miesięczną lub niestandardową, a także czy sekwencja zadań ma być wykonywana po zdarzeniach takich jak zalogowanie się do komputera lub wylogowanie z niego.  

        > [!NOTE]  
        >  Jeśli zaplanowany czas rozpoczęcia wymaganej sekwencji zadań będzie wcześniejszy niż data i godzina, jeśli sekwencja zadań nie jest dostępny, klient programu Configuration Manager pobierze sekwencję zadań w zaplanowanym terminie, nawet jeśli sekwencja zadań będzie dostępna wcześniej.  

    -   **Zachowanie ponownego uruchamiania**: Określ czas ponownego uruchomienia sekwencji zadań. Można określić jedną z następujących opcji:  

        -   **Nigdy nie uruchamiaj ponownie wdrożonego programu**: Jeśli klient Poprzednia próba uruchomienia sekwencji zadań, nie ponownie. Sekwencja zadań nie uruchomiona ponownie, nawet jeśli zakończyło się niepowodzeniem lub pliki sekwencji zadań uległy zmianie.  

        -   **Zawsze uruchamiaj ponownie program**: Sekwencja zadań będzie zawsze uruchamiana ponownie na kliencie, gdy wdrożenie jest zaplanowane, nawet jeśli sekwencja zadań została poprzednio uruchomiona pomyślnie. To ustawienie jest przydatne w przypadku używania wdrożeń cyklicznych, w których regularnie aktualizowaną sekwencją zadań.  

            > [!IMPORTANT]  
            >  Mimo że ta opcja jest domyślnie, nie ma wpływu, do momentu przypisania wymaganego wdrożenia. Użytkownik może zawsze uruchomić ponownie dostępne wdrożenia.  

        -   **Uruchom ponownie, jeśli poprzednia próba nie**: Sekwencja zadań zostanie uruchomiona ponownie, gdy wdrożenie jest zaplanowane tylko wtedy, gdy sekwencja zadań nie można uruchomić wcześniej. To ustawienie jest przydatne w celu dokonania wymaganych wdrożeń. Jeśli poprzednia próba uruchomienia zakończyła się niepowodzeniem, są automatycznie spróbuje ponownie uruchomić zgodnie z harmonogramem przypisania.  

        -   Uruchom ponownie, jeśli poprzednia próba powiodła się: Sekwencja zadań zostanie uruchomiona ponownie, tylko jeśli został wcześniej uruchomiony pomyślnie na kliencie. To ustawienie jest przydatne w przypadku używania cyklicznych wdrożeń z regularnie aktualizowaną sekwencją zadań, gdy każda aktualizacja wymaga pomyślnego zainstalowania poprzedniej aktualizacji.  

        > [!NOTE]  
        >  Ponieważ użytkownik może ponownie uruchomić wdrożenie dostępnej sekwencji zadań, upewnij się, że przed wdrożeniem dostępnej sekwencji zadań w środowisku produkcyjnym należy starannie oceny i testowania co się stanie, jeśli użytkownik ponownie uruchomi sekwencję zadań wiele razy.  

8.  Na stronie **Czynności użytkownika** określ następujące informacje, a następnie kliknij przycisk **Dalej**.  

    -   **Zezwalaj użytkownikowi na uruchamianie programu niezależnie od przypisań**: Określ, czy użytkownik może uruchomić wymaganą sekwencję zadań niezależnie od przypisań wdrożenia.  

    -   **Pokaż postęp sekwencji zadań**: Określ, czy klient programu Configuration Manager jest wyświetlany postęp sekwencji zadań.  

    -   **Instalacja oprogramowania**: Określ, czy użytkownik może instalować oprogramowanie poza skonfigurowanym oknem obsługi po upływie zaplanowanego czasu.  

    -   **Ponowne uruchomienie systemu (Jeśli wymagane w celu ukończenia instalacji)**: Określ, czy użytkownik może ponownie uruchomić komputer po zainstalowaniu oprogramowania poza skonfigurowanym oknem obsługi po upływie czasu przypisania.  

    -   **Zezwalaj na sekwencję zadań do wykonania dla klienta w Internecie**: Określ, czy sekwencja zadań może uruchamiać na klientach internetowych. Operacje, których zainstalowanie oprogramowania, takie jak system operacyjny, nie są obsługiwane z tym ustawieniem. Użyj tej opcji tylko dla sekwencji zadań opartych na skryptach ogólnych, które wykonują operacje w standardowy system operacyjny.  

         - Począwszy od wersji 1802, to ustawienie jest obsługiwane dla wdrożeń sekwencji zadań uaktualnienia w miejscu systemu Windows 10 do klientów internetowych za pośrednictwem bramy zarządzania w chmurze. Aby uzyskać więcej informacji, zobacz [uaktualnienia w miejscu wdrożenia systemu Windows 10 za pomocą CMG](#deploy-windows-10-in-place-upgrade-via-cmg).    

9. Na stronie **Alerty** określ ustawienia alertów dla tego wdrożenia sekwencji zadań, a następnie kliknij przycisk **Dalej**.  

10. Na stronie **Punkty dystrybucji** określ poniższe informacje, a następnie kliknij przycisk **Dalej**.  

    -   **Opcje wdrażania**: Określ jedną z następujących opcji:  

        > [!NOTE]  
        >  Podczas korzystania z multiemisji do wdrażania systemu operacyjnego, zawartość należy pobrać na komputery docelowe jest wymagana lub przed uruchomieniem sekwencji zadań.  

        -   Określ, że klienci mają pobierać zawartość z punktu dystrybucji na komputer docelowy zgodnie z zapotrzebowaniem sekwencji zadań.  

        -   Określ, że klienci mają pobierać całą zawartość z punktu dystrybucji na komputer docelowy przed uruchomieniem sekwencji zadań. Ta opcja nie jest wyświetlana, jeśli określono, że sekwencja zadań będzie dostępna dla środowiska PXE oraz rozruchowego nośnika na **ustawienia wdrażania** strony.  

        -   Określ, że klienci mają uruchamiać zawartość z punktów dystrybucji. Ta opcja jest dostępna tylko wtedy, gdy są włączone wszystkie pakiety skojarzone z sekwencją zadań, aby używać udziału pakietu w punkcie dystrybucji. Aby umożliwić używanie udziału pakietu przez zawartość, wyświetl kartę **Dostęp do danych** w oknie **Właściwości** każdego z pakietów.  

    -   **Gdy żaden lokalny punkt dystrybucji nie jest dostępna, Użyj zdalnego punktu dystrybucji**: Określ, czy klienci mogą używać punktów dystrybucji znajdujących się w powolnych i zawodnych sieciach do pobierania zawartości wymaganej przez sekwencję zadań.  
11. W programie Configuration Manager 1802, na **Podsumowanie** kliknij **Zapisz jako szablon** Jeśli chcesz zapisać ustawienia do ponownego użycia. Podaj nazwę dla szablonu i wybierz ustawienia do zapisania. 

 
12. Ukończ pracę kreatora.  


### <a name="deploy-windows-10-in-place-upgrade-via-cmg"></a>Wdrażanie uaktualnienia w miejscu systemu Windows 10 za pomocą CMG
<!-- 1357149 -->

Począwszy od wersji 1802 sekwencji zadań uaktualniania w miejscu systemu Windows 10 obsługuje wdrażanie na klientach internetowych zarządzanych za pomocą [brama zarządzania chmury](/sccm/core/clients/manage/plan-cloud-management-gateway) (CMG). Dzięki tej możliwości użytkownicy zdalni łatwiej uaktualniania do systemu Windows 10, bez konieczności łączenia się z intranetem. 

Upewnij się, cała zawartość odwołuje się sekwencja zadań uaktualniania w miejscu jest dystrybuowana do [punktu dystrybucji w chmurze](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point). W przeciwnym razie urządzenia nie można uruchomić sekwencji zadań.

Podczas wdrażania sekwencji zadań uaktualniania, należy użyć następujących ustawień:
- **Zezwalaj na sekwencję zadań do wykonania dla klienta w Internecie**, na karcie środowiska użytkownika wdrożenia.
- **Pobierz całą zawartość lokalnie przed uruchomieniem sekwencji zadań**, na karcie punktów dystrybucji wdrożenia. Inne opcje, takie jak **Pobierz zawartość lokalnie przez uruchomienie sekwencji zadań** nie działają w tym scenariuszu. Aparat sekwencji zadań nie może obecnie pobierać zawartość z punktu dystrybucji chmury. Klient programu Configuration Manager musi pobrać zawartość z punktu dystrybucji chmury przed uruchomieniem sekwencji zadań.
- (*Opcjonalnie*) **wstępnie pobrać zawartość do tej sekwencji zadań**, na karcie Ogólne we wdrożeniu. Aby uzyskać więcej informacji, zobacz [skonfigurować wstępne wypełnienie pamięci podręcznej](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#configure-pre-cache-content).



##  <a name="BKMK_ExportImport"></a> Eksportowanie i importowanie sekwencji zadań  
 Można eksportować i importować sekwencje zadań z lub bez nich powiązane obiekty. Ta przywoływanej zawartości zawiera obraz systemu operacyjnego, obraz rozruchowy, pakiet agenta klienta, pakiet sterownika i aplikacje z zależnościami.  

 Eksportując i importując sekwencje zadań, uwzględnij następujące kwestie.  

-   Hasła zapisane w sekwencji zadań nie zostaną wyeksportowane. Eksportując i importując sekwencję zadań zawierającą hasła, należy edytować importowaną sekwencję zadań, wprowadź ponownie hasła. Upewnij się, że wprowadzono hasła dla [Przyłącz do domeny lub grupy roboczej](../understand/task-sequence-steps.md#BKMK_JoinDomainorWorkgroup), [połączenia do folderu sieciowego](../understand/task-sequence-steps.md#BKMK_ConnectToNetworkFolder), i [Uruchom wiersz polecenia](../understand/task-sequence-steps.md#BKMK_RunCommandLine) akcje.  

- Podczas eksportowania sekwencji zadań z **Ustaw zmienne dynamiczne** kroku wartości nie są eksportowane zmiennych, które są skonfigurowane przy użyciu **wartość tajna** ustawienie. Po zaimportowaniu sekwencji zadań, należy ponownie wprowadzić wartości tych zmiennych.

-   W przypadku wielu lokacji głównych zgodnie z najlepszymi praktykami sekwencje zadań należy importować w centralnej lokacji administracyjnej.  

 Aby wyeksportować i zaimportować sekwencję zadań, należy wykonać następującą procedurę.  

#### <a name="to-export-task-sequences"></a>Aby wyeksportować sekwencje zadań  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Sekwencje zadań**.  

3.  Z listy **Sekwencja zadań** wybierz sekwencję, którą chcesz wyeksportować. W przypadku wybrania więcej niż jednej sekwencji zostaną one zapisane w jednym pliku eksportu.  

4.  Na karcie **Narzędzia główne** w grupie **Sekwencja zadań** kliknij przycisk **Eksport** , aby uruchomić Kreatora sekwencji zadań eksportu.  

5.  Na stronie **Ogólne** określ następujące informacje, a następnie kliknij przycisk **Dalej**.  

    -   W polu **Plik** określ lokalizację i nazwę pliku eksportu. Jeśli bezpośrednio wprowadzasz nazwę pliku, pamiętaj o dodaniu rozszerzenia .zip do nazwy. Jeśli wprowadzasz nazwę pliku eksportu przy użyciu funkcji przeglądania, kreator automatycznie doda to rozszerzenie do nazwy pliku.  

    -   Usuń zaznaczenie **Eksportuj wszystkie zależności sekwencji zadań** , jeśli nie chcesz eksportować tych zależności. Domyślnie kreator wykona skanowanie w poszukiwaniu powiązanych obiektów i wyeksportuje je wraz z sekwencją zadań. Te zależności zawierać dla aplikacji.  

    -   Usuń zaznaczenie pola wyboru **Eksportuj całą zawartość dla wybranych sekwencji zadań i zależności** , jeśli nie chcesz kopiować zawartości ze źródła pakietu do lokalizacji plików eksportu. Zaznaczenie tego pola wyboru spowoduje, że Kreator sekwencji zadań importu użyje ścieżki importu jako nowej lokalizacji źródła pakietu.  

    -   W polu **Komentarze administratora** dodaj opis sekwencji zadań do wyeksportowania.  

6.  Ukończ pracę kreatora.  

 Kreator utworzy następujące pliki wyjściowe:  

-   Bez eksportu zawartości: plik zip.  

-   Z eksportem zawartości: plik zip oraz folder o nazwie *export*_files, gdzie *export* to nazwa pliku zip zawierającego wyeksportowaną zawartość.  

 Jeśli w przypadku uwzględnienia zawartości podczas eksportowania sekwencji zadań, upewnij się, że skopiowaniu pliku .zip i *wyeksportować*_files folderu lub importowania kończy się niepowodzeniem.  

#### <a name="to-import-task-sequences"></a>Aby zaimportować sekwencje zadań  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Sekwencje zadań**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Importuj sekwencję zadań** , aby uruchomić Kreatora sekwencji importu zadań.  

4.  Na stronie **Ogólne** określ eksportowany plik *.zip, a następnie kliknij przycisk **Dalej**.  

5.  Na stronie **Zawartość pliku** wybierz akcję, która jest wymagana w przypadku każdego importowanego obiektu. Ta strona przedstawia wszystkie obiekty, które program Configuration Manager znalazł do zaimportowania.  

    -   Jeśli obiekt nie był nigdy importowany, wybierz polecenie **Utwórz nowy**.  

    -   Jeśli obiekt był wcześniej importowany, wybierz jedną z następujących akcji:  

        -   **Ignoruj duplikat** (domyślnie): Ta akcja nie importuje obiektu. Zamiast importowania, kreator łączy istniejący obiekt z sekwencją zadań.  

        -   **Zastąp**: Ta akcja zastępuje istniejący obiekt importowanym obiektem. W przypadku aplikacji można dodać wersję aktualizującą istniejącą aplikację lub utworzyć nową aplikację.  

6.  Ukończ pracę kreatora.  

 Po zaimportowaniu sekwencji zadań edytuj sekwencję zadań, aby określić hasła z oryginalnej sekwencji zadań. Ze względu na bezpieczeństwo hasła nie są eksportowane.  

##  <a name="BKMK_CreateTSVariables"></a> Tworzenie zmiennych sekwencji zadań dla komputerów i kolekcji  
Można definiować niestandardowe zmienne sekwencji zadań dla komputerów i kolekcji. Zmienne definiowane dla komputera są określane zmiennymi sekwencji zadań dla komputera. Zmienne definiowane dla kolekcji są określane zmiennymi sekwencji zadań dla kolekcji. W przypadku konfliktu zmienne dla komputera mają pierwszeństwo przed zmiennymi dla kolekcji. To zachowanie oznacza, że zmienne sekwencji zadań, które są przypisane do konkretnego komputera automatycznie mają wyższy priorytet niż zmienne, które są przypisane do kolekcji, która zawiera komputer.  

Jeśli na przykład do kolekcji ABC jest przypisana zmienna, a komputer XYZ, który jest członkiem kolekcji ABC, ma przypisaną zmienną o takiej samej nazwie, zmienna przypisana do komputera XYZ ma wyższy priorytet niż zmienna przypisana do kolekcji ABC.  

Zmienne dla komputera i dla kolekcji można ukryć, tak aby nie były widoczne w konsoli programu Configuration Manager. Aby zmienne nie były ukryte, należy usunąć je i ponownie zdefiniować bez wybierania opcji ukrycia. Jeśli używasz opcji **nie wyświetlaj tej wartości w konsoli programu Configuration Manager**, wartość zmiennej nie będzie wyświetlana w konsoli. Zmienna może nadal używane przez sekwencję zadań, po uruchomieniu.  

> [!WARNING]    
> **Nie wyświetlaj tej wartości w konsoli programu Configuration Manager** ustawienie ma zastosowanie tylko do konsoli programu Configuration Manager. Wartości zmiennych są wyświetlane w formacie pliku dziennika sekwencji zadań (SMSTS. DZIENNIK). 

Zmiennymi dla komputera można zarządzać w lokacji głównej lub w centralnej lokacji administracyjnej. Menedżer konfiguracji nie obsługuje więcej niż 1000 przypisanych zmiennych dla komputera.  

> [!IMPORTANT]  
>  W przypadku używania zmiennych dla kolekcji dla sekwencji zadań, należy uwzględnić następujące zachowania:  
>   
> - Zmiany w kolekcji są zawsze replikowane w całej hierarchii. Wszelkie zmiany zmiennych kolekcji mają zastosowanie nie tylko do członków bieżącej lokacji, ale do wszystkich elementów członkowskich kolekcji w całej hierarchii.  
> - Usunięcie kolekcji powoduje usunięcie zmiennych sekwencji zadań, które są skonfigurowane dla tej kolekcji.  

 Aby utworzyć zmienne sekwencji zadań dla komputera lub kolekcji, wykonaj czynności opisane w poniższych procedurach.  

#### <a name="to-create-task-sequence-variables-for-a-computer"></a>Aby utworzyć zmienne sekwencji zadań dla komputera  

1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.  

2.  W obszarze roboczym **Zasoby i zgodność** rozwiń kolekcję zawierającą komputer, do którego chcesz dodać zmienną.  

3.  Wybierz komputer i kliknij pozycję **Właściwości**.  

4.  W oknie dialogowym **Właściwości** kliknij kartę **Zmienne** .  

5.  Dla każdej zmiennej, którą chcesz utworzyć, kliknij przycisk **nowy** ikonę w **< nowy\> zmiennej** okno dialogowe. Określ nazwę oraz wartość zmiennej sekwencji zadań. Wyczyść **nie wyświetlaj tej wartości w konsoli programu Configuration Manager** pole wyboru, jeśli chcesz ukryć zmienne, tak aby nie były widoczne w konsoli programu Configuration Manager.  

6.  Po dodaniu wszystkich zmiennych do komputera kliknij przycisk **OK**.  

#### <a name="to-create-task-sequence-variables-for-a-collection"></a>Aby utworzyć zmienne sekwencji zadań dla kolekcji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.  

2.  W obszarze roboczym **Zasoby i zgodność** wybierz kolekcję, do której chcesz dodać zmienną, i kliknij pozycję **Właściwości**.  

3.  W oknie dialogowym **Właściwości** kliknij kartę **Zmienne kolekcji** .  

4.  Dla każdej zmiennej, którą chcesz utworzyć, kliknij przycisk **nowy** ikonę w **< nowy\> zmiennej** okno dialogowe. Określ nazwę oraz wartość zmiennej sekwencji zadań. Wyczyść **nie wyświetlaj tej wartości w konsoli programu Configuration Manager** pole wyboru, jeśli chcesz ukryć zmienne, tak aby nie były widoczne w konsoli programu Configuration Manager.  

5.  Opcjonalnie określ priorytet dla programu Configuration Manager można używać w czasie oceny zmiennych sekwencji zadań.  

6.  Po dodaniu wszystkich zmiennych do kolekcji kliknij przycisk **OK**.  

## <a name="add-child-task-sequences-to-a-task-sequence"></a>Dodaj do sekwencji zadań sekwencje zadań podrzędnych
<!--1261338-->
Począwszy od programu Configuration Manager w wersji 1710, możesz dodać nowy krok sekwencji zadań uruchamiana innej sekwencji zadań. Spowoduje to utworzenie relacji nadrzędny podrzędny między sekwencji zadań. Przy użyciu ten krok umożliwia tworzenie jedną sekwencją zadań moduły, które można użyć ponownie.  

> [!Note]  
> Ta funkcja opcjonalna nie włączyć domyślne programu Configuration Manager. Należy włączyć tę funkcję, przed jego użyciem. Aby uzyskać więcej informacji, zobacz [Włącz funkcje opcjonalne aktualizacji](/sccm/core/servers/manage/install-in-console-updates#bkmk_options).<!--505213-->  


Należy rozważyć dodanie sekwencji zadań podrzędnych do sekwencji zadań:

 - Sekwencje zadań nadrzędnych i podrzędnych skutecznie są połączone w jedną zasadę, która działa na kliencie.
 - Środowisko jest globalnego. Na przykład w przypadku zmiennej jest ustawiany przez sekwencję zadań nadrzędny i następnie zmienić przez sekwencję zadań podrzędnych, pozostaje zmienione. Podobnie jeśli sekwencja zadań podrzędnych tworzy nową zmienną, jest dostępny do pozostałych kroków w sekwencji zadań nadrzędnej.
 - Komunikaty o stanie są wysyłane na normalny dla operacji sekwencji pojedyncze zadanie.
 - Sekwencje zadań tworzyć wpisy w pliku smsts.log w nowy dziennik wpisów, dzięki któremu można wyczyścić podczas sekwencji zadań podrzędnych rozpoczyna się.

### <a name="to-add-a-child-task-sequence-to-a-task-sequence"></a>Możesz dodać sekwencję zadań podrzędnych do sekwencji zadań

1. W edytorze sekwencji zadań, kliknij przycisk **Dodaj**, wybierz pozycję **ogólne**i kliknij przycisk **uruchamiania sekwencji zadań**.
2. Kliknij przycisk **Przeglądaj** do wybierania sekwencji zadań podrzędnych.  

##  <a name="BKMK_AdditionalActionsTS"></a> Dodatkowe akcje zarządzania sekwencjami zadań  
 Sekwencje zadań można zarządzać za pomocą dodatkowych akcji po wybraniu sekwencji zadań.  

#### <a name="to-select-a-task-sequence-to-manage"></a>Aby wybrać sekwencję zadań do zarządzania  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne** , a następnie kliknij przycisk **Sekwencje zadań**.  

3.  Z listy **Sekwencja zadań** wybierz sekwencję, którą chcesz zarządzać, a następnie wybierz jedną z dostępnych opcji.  

 Więcej informacji o niektórych dodatkowych akcjach zarządzania sekwencjami zadań znajduje się w poniższej tabeli.  

|Akcja|Opis|  
|------------|-----------------|  
|**Kopiuj**|Wykonuje kopię wybranej sekwencji zadań. Ta akcja jest przydatne do utworzenia nowej sekwencji zadań, która jest oparta na istniejącej sekwencji zadań.<br /><br /> W przypadku kopiowania sekwencji zadań w folderze kopia będzie widoczna w tym folderze, aż do chwili odświeżenia węzła sekwencji zadań. Po odświeżeniu kopia stanie się widoczna w folderze głównym.|  
|**Wyłącz**|Wyłącza sekwencję zadań, tak aby nie można jej było uruchomić na komputerach. Można wdrożyć sekwencję zadań wyłączone, ale komputery nie pozwalają uruchamiać sekwencję zadań, dopóki nie zostanie włączona.|  
|**Włączenie**|Włącza sekwencję zadań, tak aby można ją było uruchamiać. Po włączeniu wdrożonej sekwencji zadań jej ponowne wdrożenie nie jest konieczne.|  
|**Tworzenie wstępnie przygotowanego pliku zawartości**|Uruchamia Kreatora tworzenia przygotowanego pliku zawartości w celu wstępnego przygotowania zawartości sekwencji zadań. Aby uzyskać informacje o sposobie tworzenia wstępnie przygotowanego pliku zawartości, zobacz [wstępnie przygotować zawartość](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_prestage).|  
|**Przenieś**|Przenosi wybraną sekwencję zadań do innego folderu.|  

## <a name="next-steps"></a>Następne kroki
[Scenariusze wdrażania systemów operacyjnych dla przedsiębiorstw](scenarios-to-deploy-enterprise-operating-systems.md)
