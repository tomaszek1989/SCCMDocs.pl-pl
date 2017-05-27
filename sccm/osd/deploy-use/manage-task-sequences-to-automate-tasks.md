---
title: "Sekwencje zadań do automatyzacji zadań zarządzania | Dokumentacja firmy Microsoft"
description: "Można tworzyć, edytować, wdrażanie, importowania i eksportowania sekwencje zadań w celu zarządzania nimi w środowisku programu System Center Configuration Manager."
ms.custom: na
ms.date: 03/24/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a1f099f1-e9b5-4189-88b3-f53e3b4e4add
caps.latest.revision: 10
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 113fa73bf0bd1b3b8a4754eb1e96549c520d7995
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="manage-task-sequences-to-automate-tasks-in-system-center-configuration-manager"></a>Zarządzanie sekwencjami zadań w celu zautomatyzowania zadań w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Aby zautomatyzować kroki w środowisku programu System Center Configuration Manager za pomocą sekwencji zadań. Te czynności umożliwiają wdrażanie obrazu systemu operacyjnego na komputerze docelowym, tworzenie i przechwytywanie obrazu systemu operacyjnego z zestawu plików instalacyjnych, a także przechwytywanie i przywracanie informacji o stanie użytkownika. Sekwencje zadań znajdują się w konsoli programu Configuration Manager pod adresem **Biblioteka oprogramowania** > **systemów operacyjnych** > **sekwencji zadań**. **Sekwencji zadań** węzła, w tym podfolderów, które tworzysz, są replikowane w całej hierarchii programu Configuration Manager. Informacje dotyczące planowania, zobacz [uwagi dotyczące automatyzacji zadań planowania](../plan-design/planning-considerations-for-automating-tasks.md).  

 Poniższe sekcje służą do zarządzania sekwencjami zadań.

##  <a name="BKMK_CreateTaskSequence"></a> Tworzenie sekwencji zadań  
 Utwórz sekwencje zadań za pomocą Kreatora tworzenia sekwencji zadań. Ten kreator umożliwia tworzenie następujących typów sekwencji zadań:  

|Typ sekwencji zadań|Więcej informacji|  
|------------------------|----------------------|  
|[Sekwencji zadań w celu zainstalowania systemu operacyjnego](create-a-task-sequence-to-install-an-operating-system.md)|Ten typ sekwencji zadań umożliwia utworzenie czynności niezbędnych do zainstalowania systemu operacyjnego, a także zapewnia opcje migracji danych użytkownika, dołączenia aktualizacji oprogramowania i instalacji aplikacji.|  
|[Sekwencji zadań w celu uaktualnienia systemu operacyjnego](create-a-task-sequence-to-upgrade-an-operating-system.md)|Ten typ sekwencji zadań umożliwia utworzenie czynności niezbędnych do uaktualnienia systemu operacyjnego, a także zapewnia opcje dołączenia aktualizacji oprogramowania i instalacji aplikacji.|  
|[Sekwencji zadań w celu przechwycenia systemu operacyjnego](create-a-task-sequence-to-capture-an-operating-system.md)|Ten typ sekwencji umożliwia utworzenie czynności niezbędnych do utworzenia i przechwycenia systemu operacyjnego z komputera odniesienia. Możesz dołączyć aktualizacje oprogramowania i zainstalować aplikacje na komputerze odniesienia przed przechwyceniem obrazu.|  
|[Sekwencji zadań w celu przechwycenia i przywrócenia stanu użytkownika](create-a-task-sequence-to-capture-and-restore-user-state.md)|Ta sekwencja zadań zapewnia czynności, które można dodać do istniejącej sekwencji zadań w celu przechwycenia i przywrócenia danych stanu użytkownika.|  
|[Zarządzanie wirtualnymi dyskami twardymi sekwencji zadań](use-a-task-sequence-to-manage-virtual-hard-disks.md)|Ten typ sekwencji zadań zawiera kroki, aby utworzyć dysk VHD, w tym do zainstalowania systemu operacyjnego i aplikacji, które można publikować na System Center Virtual Machine Manager (VMM) z konsoli programu Configuration Manager.|  
|[Niestandardową sekwencję zadań](create-a-custom-task-sequence.md)|Ten typ sekwencji zadań nie dodaje żadnych kroków do sekwencji zadań. Sekwencję zadań należy edytować i dodawać do niej kroki po jej utworzeniu.|  

## <a name="return-to-previous-page-when-a-task-sequence-fails"></a>Powrócić do poprzedniej strony, gdy sekwencja zadań zakończy się niepowodzeniem.
Począwszy od programu Configuration Manager w wersji 1702, możesz powrócić do poprzedniej strony podczas uruchamiania sekwencji zadań i awarii. Przed tej wersji było konieczne ponowne uruchomienie sekwencji zadań, gdy wystąpił błąd. Na przykład można użyć **Wstecz** przycisku w następujących scenariuszach:

- Po uruchomieniu komputera w środowisku Windows PE, okno dialogowe ładowania sekwencji zadań może być wyświetlany, zanim sekwencja zadań będzie dostępna. Po kliknięciu przycisku Dalej w tym scenariuszu na ostatniej stronie sekwencji zadań wyświetla komunikat, że są sekwencji zadań. Teraz, można kliknąć przycisk **Wstecz** ponowić wyszukiwanie uzyskać dostępne sekwencje zadań. Ten proces można powtarzać momentu udostępnienia sekwencji zadań.
- Podczas uruchamiania sekwencji zadań, ale zależne pakiety zawartości nie są jeszcze dostępne w punktach dystrybucji, sekwencja zadań kończy się niepowodzeniem. Możesz teraz dystrybucji brakującą zawartość (jeśli go nie została jeszcze rozesłana) lub poczekaj, aż zawartość ma być dostępna w punktach dystrybucji, a następnie kliknij **Wstecz** mieć wyszukiwania sekwencji zadań ponownie dla zawartości.

##  <a name="BKMK_ModifyTaskSequence"></a> Edytowanie sekwencji zadań  
 Sekwencję zadań można modyfikować, dodając lub usuwając kroki i grupy sekwencji zadań albo zmieniając kolejność kroków. Aby zmodyfikować istniejącą sekwencję zadań, wykonaj czynności opisane w poniższej procedurze.  

> [!IMPORTANT]  
>  W przypadku edytowania sekwencji zadań utworzonej za pomocą Kreatora tworzenia sekwencji zadań, jako nazwę korku można określić akcję lub typ tego kroku. Na przykład, można napotkać krok o nazwie "Podziel dysk 0" oznacza akcję kroku typu [Formatuj dysk partycji i](../understand/task-sequence-steps.md#BKMK_FormatandPartitionDisk). Wszystkie kroki sekwencji zadań najczęściej określa się na podstawie ich typu, a nie nazw wyświetlanych w Edytorze.  

#### <a name="to-edit-a-task-sequence"></a>Aby edytować sekwencję zadań  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Sekwencje zadań**.  

3.  Z listy **Sekwencja zadań** wybierz sekwencję do edytowania.  

4.  Na karcie **Narzędzia główne** w grupie **Sekwencja zadań** kliknij przycisk **Edytuj**, a następnie wykonaj jedną z następujących czynności:  

    -   Aby dodać krok sekwencji zadań, kliknij przycisk **Dodaj**, wybierz typ kroku, a następnie kliknij krok sekwencji zadań, który chcesz dodać. Aby na przykład dodać krok Uruchom wiersz polecenia, kliknij przycisk **Dodaj**, wybierz pozycję **Ogólny**, a następnie kliknij pozycję **Uruchom wiersz polecenia**.  

         Lista wszystkich kroków sekwencji zadań oraz ich typów znajduje się w tabeli pod tą procedurą.  

    -   Aby dodać grupę do sekwencji zadań, kliknij przycisk **Dodaj**, a następnie kliknij przycisk **Nowa grupa**. Po dodaniu grupy można do niej dodać kroki.  

    -   Aby zmienić kolejność kroków i grup w sekwencji zadań, wybierz odpowiedni krok lub grupę, których kolejność chcesz zmienić, a następnie użyj ikon **Przenieś element w górę** lub **Przenieś element w dół** . Jednocześnie można przenosić tylko jeden krok lub grupę.  

    -   Aby usunąć krok lub grupę, wybierz odpowiednie elementy i kliknij przycisk **Usuń**.  

5.  Kliknij przycisk **OK** , aby zapisać zmiany.  

 Lista kroków sekwencji zadań dostępnych w temacie [czynności sekwencji zadań](../understand/task-sequence-steps.md).  

## <a name="configure-high-impact-task-sequence-settings"></a>Konfigurowanie ustawień sekwencji zadań wysoki wpływ
Począwszy od programu Configuration Manager w wersji 1702, możesz ustawić sekwencji zadań jako wysoki wpływ i dostosować wiadomości, które użytkownicy będą otrzymywali po uruchomieniu sekwencji zadań.

### <a name="set-a-task-sequence-as-a-high-impact-task-sequence"></a>Ustawianie sekwencji zadań za pomocą sekwencji zadań wysoki wpływ
Użyj poniższej procedury do ustawienia sekwencji zadań jako wysoki wpływ.
> [!NOTE]
> Wszystkie sekwencje zadań, która spełnia określone warunki automatycznie jest zdefiniowany jako wysoki wpływ. Aby uzyskać szczegółowe informacje, zobacz [Zarządzanie wdrożeniami o wysokim ryzyku](http://docs.microsoft.com/sccm/protect/understand/settings-to-manage-high-risk-deployments).

1. W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** > **systemów operacyjnych** > **sekwencji zadań**.
2. Wybierz sekwencję zadań do edycji, a następnie kliknij przycisk **właściwości**.
3. Na **powiadomienie użytkownika** zaznacz **jest sekwencji zadań wysoki wpływ**.

### <a name="create-a-custom-notification-for-high-risk-deployments"></a>Utwórz niestandardowe powiadomienia dla wdrożenia o wysokim ryzyku
Poniższa procedura umożliwia utworzenie niestandardowego powiadomień w przypadku wdrożeń wysoki wpływ.
1. W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** > **systemów operacyjnych** > **sekwencji zadań**.
2. Wybierz sekwencję zadań do edycji, a następnie kliknij przycisk **właściwości**.
3. Na **powiadomienie użytkownika** zaznacz **użyć niestandardowego tekstu**.
>  [!NOTE]
>  Tekst powiadomienia użytkownika można ustawić tylko podczas **jest sekwencji zadań wysoki wpływ** jest zaznaczone.

4. Skonfiguruj następujące ustawienia (maksymalnie 255 znaków dla każdego pola tekstowego):

  **Tekst nagłówka powiadomienia użytkownika**: Określa niebieski tekst wyświetlany na powiadomienie użytkownika Centrum oprogramowania. Na przykład domyślny powiadomienie użytkowników, ta sekcja zawiera którąś "Potwierdź chcesz uaktualnić system operacyjny na tym komputerze".

  **Tekst komunikatu powiadomienia użytkownika**: Istnieją trzy pola tekstowe, które zawierają treści niestandardowe powiadomienia. Wszystkie pola tekstowe wymagają, aby dodać tekst.
  - 1. pole tekstowe: Określa główną część tekstu, zazwyczaj zawierającej instrukcje dla użytkownika. Na przykład domyślny powiadomienie użytkowników, ta sekcja zawiera coś jak "Uaktualnianie systemu operacyjnego potrwa i komputer może być kilka razy ponownie."
  - pole tekstowe 2: Określa tekst czcionką pogrubioną w głównej części tekstu. Na przykład domyślny powiadomienie użytkowników, ta sekcja zawiera coś jak "to uaktualnienie w miejscu instalacji nowego systemu operacyjnego i automatycznie migruje aplikacje, dane i ustawienia".
  - pole tekstowe 3: Określa ostatni wiersz tekstu pogrubienie tekstu. Na przykład domyślny powiadomienie użytkowników, ta sekcja zawiera którąś "kliknij przycisk Zainstaluj, aby rozpocząć. W przeciwnym razie kliknij przycisk Anuluj."   

  Załóżmy, że skonfigurować następujące powiadomienie niestandardowych właściwości.

    ![Niestandardowe powiadomienia dla sekwencji zadań](..\media\user-notification.png)

    Następujący komunikat powiadomienia będą wyświetlane podczas instalacji zostanie otwarty przez użytkownika z Centrum oprogramowania.

    ![Niestandardowe powiadomienia dla sekwencji zadań](..\media\user-notification-enduser.png)

### <a name="configure-software-center-properties"></a>Konfigurowanie właściwości Centrum oprogramowania
Poniższa procedura służy do konfigurowania szczegółowe informacje dotyczące sekwencji zadań wyświetlana w Centrum oprogramowania. Te informacje są wyłącznie w celach informacyjnych.  
1. W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** > **systemów operacyjnych** > **sekwencji zadań**.
2. Wybierz sekwencję zadań do edycji, a następnie kliknij przycisk **właściwości**.
3. Na **ogólne** kartę, dostępne są następujące ustawienia dla programu Software Center:
  - **Wymagane jest ponowne uruchomienie**: Powiadomi użytkownika, czy ponowne uruchomienie jest wymagane podczas instalacji.
  - **Pobierz rozmiar (MB)**: Określa, ile megabajtów jest wyświetlana w Centrum oprogramowania dla sekwencji zadań.  
  - **Szacowany czas wykonywania (minuty)**: Określa, że szacowany czas wykonywania w minutach, które jest wyświetlane w Centrum oprogramowania dla sekwencji zadań.

##  <a name="BKMK_DistributeTS"></a> Dystrybucja zawartości, do której odwołuje się sekwencja zadań  
 Przed uruchomieniem na klientach sekwencji zadań odwołującej się do zawartości należy rozesłać ową zawartość do punktów dystrybucji. W dowolnym momencie można wybrać sekwencję zadań i rozesłać jej zawartość w celu utworzenia nowej listy pakietów odniesienia do dystrybucji. Po wprowadzeniu zmian w sekwencji zadań obejmujących zaktualizowaną zawartość należy ponownie rozesłać zawartość, zanim sekwencja zadań zostanie udostępniona klientom. Aby rozesłać zawartość, do której odwołuje się sekwencja zadań, należy wykonać następującą procedurę.  

#### <a name="to-distribute-referenced-content-to-distribution-points"></a>Aby rozesłać zawartość z odwołaniem do punktów dystrybucji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Sekwencje zadań**.  

3.  Z listy **Sekwencja zadań** wybierz sekwencję, którą chcesz rozesłać.  

4.  Na karcie **Narzędzia główne** w grupie **Wdrażanie** kliknij przycisk **Dystrybuuj zawartość** , aby uruchomić Kreatora dystrybucji zawartości.  

5.  Na stronie **Ogólne** sprawdź, czy wybrano właściwą sekwencję zadań do dystrybucji, a następnie kliknij przycisk **Dalej**.  

6.  Na stronie **Zawartość** sprawdź zawartość do rozesłania, na przykład obraz rozruchowy, do którego odwołuje się sekwencja zadań, a następnie kliknij przycisk **Dalej**.  

7.  Na stronie **Miejsce docelowe zawartości** określ kolekcje, punkty dystrybucji lub grupę punktów docelowych, do których chcesz rozesłać zawartość sekwencji zadań, a następnie kliknij przycisk **Dalej**.  

    > [!IMPORTANT]  
    >  Jeśli wybrana sekwencja zadań odwołuje się do zawartości, która została już wysłana do określonego punktu dystrybucji, ten punkt dystrybucji nie będzie wymieniony na liście w kreatorze.  

8.  Ukończ pracę kreatora.  

 Można wstępnie przygotować zawartość, do której odwołuje się sekwencja zadań. Program Configuration Manager tworzy skompresowany, wstępnie przygotowany plik zawartości zawierający pliki, skojarzone zależności i skojarzone metadane dla wybranej zawartości. Następnie możesz ręcznie zaimportować zawartość na serwer lokacji, do lokacji dodatkowej albo punktu dystrybucji. Aby uzyskać więcej informacji o przygotowywaniu plików zawartości, zobacz [wstępnie przygotować zawartość](../../core/servers/deploy/configure/deploy-and-manage-content.md#a-namebkmkprestagea-use-prestaged-content).  

##  <a name="BKMK_DeployTS"></a> Wdrażanie sekwencji zadań  
 Aby wdrożyć sekwencję zadań na komputerach w kolekcji, należy wykonać następującą procedurę.  

> [!WARNING]  
>  Można zarządzać zachowaniem wdrożeń sekwencji zadań wysokiego ryzyka. Wdrożenie wysokiego ryzyka to wdrożenie, które jest instalowane automatycznie i może mieć niepożądane wyniki. Na przykład sekwencja zadań, której cel to **Wymagane** i która wdraża system operacyjny, jest uznawana za wdrożenie wysokiego ryzyka. Aby uzyskać więcej informacji, zobacz [ustawienia do zarządzania wdrożeniami o wysokim ryzyku](../../protect/understand/settings-to-manage-high-risk-deployments.md).  

> [!NOTE]  
>  Komunikaty o stanie wdrożenia sekwencji zadań będą wyświetlane w oknie Komunikat w lokacji głównej, jednak nie będą wyświetlane w centralnej lokacji administracyjnej.  

#### <a name="to-deploy-a-task-sequence"></a>Aby wdrożyć sekwencję zadań  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Sekwencje zadań**.  

3.  Z listy **Sekwencja zadań** wybierz sekwencję, którą chcesz wdrożyć.  

4.  Na karcie **Narzędzia główne** w grupie **Wdrażanie** kliknij przycisk **Wdróż**.  

    > [!NOTE]  
    >  Jeśli przycisk **Wdróż** będzie niedostępny, oznacza to, że sekwencja zawiera nieprawidłowe odwołanie.  Popraw odwołanie, a następnie ponów próbę wdrożenia sekwencji zadań.  

5.  Na stronie **Ogólne** określ poniższe informacje, a następnie kliknij przycisk **Dalej**.  

    -   **Sekwencja zadań**: Określ sekwencję, którą chcesz wdrożyć. Domyślnie w tym polu będzie wyświetlana wybrana sekwencja zadań.  

    -   **Kolekcja**: Określ kolekcję zawierającą komputery, których będzie uruchamiany sekwencji zadań.  

         Nie należy wdrażać sekwencji zadań instalujących systemy operacyjne w nieodpowiednich kolekcjach, na przykład w kolekcji **Wszystkie systemy** . Należy sprawdzić, czy wybrana kolekcja zawiera jedynie te komputery, na których ma zostać uruchomiona sekwencja zadań.  

        > [!NOTE]  
        >  Podczas wdrażania wdrożenie o wysokim ryzyku, takich jak system operacyjny **Wybieranie kolekcji** tylko kolekcji niestandardowych, które spełniają ustawienia weryfikacji wdrażania, które są skonfigurowane we właściwościach lokacji jest wyświetlana w oknie. Wdrożenia wysokiego ryzyka są zawsze ograniczone do kolekcji niestandardowych, kolekcji tworzonych przez Ciebie i wbudowanej kolekcji **Nieznane komputery** . Podczas tworzeniu wdrożenia wysokiego ryzyka nie można wybrać wbudowanej kolekcji, takiej jak **Wszystkie systemy**. Usuń zaznaczenie pola wyboru **Ukryj kolekcje z elementem członkowskim liczba większa niż minimalny rozmiar skonfigurowany dla lokacji** wyświetlić wszystkich kolekcji niestandardowych, zawierających klientów mniej niż skonfigurowany maksymalny rozmiar. Aby uzyskać więcej informacji, zobacz [ustawienia do zarządzania wdrożeniami o wysokim ryzyku](../../protect/understand/settings-to-manage-high-risk-deployments.md).  
        >   
        >  Ustawienia weryfikacji wdrożenia zależą od bieżącego członkostwa w kolekcji. Po wdrożeniu sekwencji zadań członkostwo w kolekcji nie jest ponownie szacowane na potrzeby ustawień wdrożenia wysokiego ryzyka.  
        >   
        >  Na przykład załóżmy, że należy ustawić **domyślny rozmiar** do 100 i **maksymalny rozmiar** do 1000. Podczas tworzenia wdrożenia wysokiego ryzyka w oknie **Wybieranie kolekcji** będą wyświetlane tylko kolekcje zawierające mniej niż 100 klientów. W przypadku usunięcia zaznaczenia **Ukryj kolekcje z elementem członkowskim liczba większa niż minimalny rozmiar skonfigurowany dla lokacji** ustawienie, w oknie zostaną wyświetlone kolekcji zawierających więcej niż 1000 klientów.  
        >   
        >  W przypadku wybrania kolekcji zawierającej rolę lokacji należy wziąć pod uwagę następujące kwestie:  
        >   
        >  -   Jeśli kolekcja zawiera serwer systemu lokacji i skonfigurowano ustawienia weryfikacji wdrożenia w celu blokowania kolekcji z serwerami systemu lokacji, wystąpi błąd i nie będzie można kontynuować.  
        > -   Jeśli kolekcja zawiera serwer systemu lokacji i skonfigurowano ustawienia weryfikacji wdrożenia w celu ostrzegania o kolekcjach zawierających serwery systemu lokacji, to w przypadku przekroczenia domyślnej wartości rozmiaru lub w przypadku kolekcji zawierające serwer w Kreatorze wdrażania oprogramowania zostanie wyświetlone ostrzeżenie o wysokim ryzyku. Musisz zaakceptować utworzenie wdrożenia wysokiego ryzyka. Zostanie utworzony komunikat o stanie inspekcji.  

    -   **Komentarze (opcjonalne)**: Podaj dodatkowe informacje opisujące to wdrożenie sekwencji zadań.  

6.  Na stronie **Ustawienia wdrażania** określ poniższe informacje, a następnie kliknij przycisk **Dalej**.  

    -   **Cel**: Z listy rozwijanej wybierz jedną z następujących opcji:  

        -   **Dostępne**: Jeśli sekwencja zadań jest wdrażana dla użytkownika, użytkownik będzie widział opublikowaną sekwencję zadań w katalogu aplikacji i może ją na żądanie. Jeśli sekwencja zadań jest wdrażana na urządzeniu, użytkownik będzie ją widział w programie Software Center i może zainstalować ją na żądanie.  

        -   **Wymagane**: Sekwencja zadań zostanie wdrożona automatycznie zgodnie ze skonfigurowanym harmonogramem. Użytkownik może jednak obserwować stan wdrożenia sekwencji zadań (jeśli nie jest ukryty) i zainstalować sekwencję zadań przed upływem ostatecznego terminu przy użyciu programu Software Center.  

    -   **Wdróż automatycznie zgodnie z harmonogramem, czy użytkownik jest zalogowany**: Ta opcja nie jest dostępna podczas wdrażania sekwencji zadań.  

    -   **Wyślij pakiety wzbudzania**: Jeśli w celu wdrożenia wybrano opcję **wymagane** i ta opcja jest zaznaczona, otrzyma pakiet wznawiania do komputerów przed zainstalowaniem wdrożenia do wznowienia w ostatecznym terminie instalacji. Aby użyć tej opcji, należy skonfigurować komputery i sieci do używania funkcji Wake On LAN.  

    -   **Zezwalaj klientom mierzonego połączenia internetowego na pobieranie zawartości po upływie ostatecznego terminu instalacji, co może pociągnąć za sobą dodatkowe koszty**: Jeśli masz sekwencji zadań, która jest instalowana aplikacja, ale nie wdrażania systemu operacyjnego, można określić, czy zezwolić klientom na pobranie zawartości po termin instalacji przy korzystaniu z taryfowego połączenia z Internetem. Dostawcy Internetu czasami naliczają opłaty według ilości wysyłanych i odbieranych danych podczas taryfowego połączenia z Internetem.  

        > [!NOTE]  
        >  Używanie taryfowego połączenia z Internetem może sprawdzić się w przypadku sekwencji zadań niewdrażających systemu operacyjnego, nie jest jednak obsługiwane.  

    -   **Wymagaj zgody administratora, jeśli użytkownicy zażądają tej aplikacji**: Ta opcja nie jest dostępna podczas wdrażania sekwencji zadań.  

    -   **Udostępnij następujących**: Określ, czy sekwencja zadań jest dostępna dla klientów programu Configuration Manager, nośników lub środowiska PXE.  

        > [!IMPORTANT]  
        >  W przypadku zautomatyzowanych wdrożeń sekwencji zadań należy użyć ustawienia **Tylko nośniki i PXE (ukryte)** . Wybierz opcję **Zezwól na nienadzorowane wdrożenie systemu operacyjnego** i ustaw zmienną SMSTSPreferredAdvertID jako część tego nośnika, aby komputer automatycznie przeprowadził rozruch do wdrożenia bez interakcji ze strony użytkownika. Aby uzyskać więcej informacji na temat zmiennych sekwencji zadań, zobacz [wbudowane zmienne sekwencji zadań](../understand/task-sequence-built-in-variables.md)  

7.  Na stronie **Planowanie** określ poniższe informacje, a następnie kliknij przycisk **Dalej**.  

    > [!IMPORTANT]  
    >  Przy uruchamianiu klienta środowiska Windows PE za pomocą środowiska PXE lub nośnika rozruchowego klient nie rozpoznaje harmonogramów wdrażania (godziny uruchomienia, wygaśnięcia lub ostatecznego terminu). Harmonogramy można konfigurować tylko w przypadku wdrożeń na klientach uruchamianych za pomocą pełnego systemu operacyjnego Windows. Należy rozważyć zastosowanie innych metod, takich jak okna obsługi, do kontrolowania aktywnych sekwencji zadań wdrożonych na klientach uruchamianych ze środowiska Windows PE.  

    -   **Zaplanuj, kiedy to wdrożenie stanie się dostępne**: Określ datę i godzinę, kiedy sekwencja zadań będzie dostępna do uruchamiania na komputerze docelowym. W przypadku zaznaczenia pola wyboru **UTC** to ustawienie zapewni, że sekwencja zadań będzie dostępna dla wielu komputerów docelowych jednocześnie zamiast w różnych godzinach uzależnionych od lokalnego czasu na komputerach docelowych.  

         Jeśli czas rozpoczęcia będzie wcześniejszy niż wymagany czas, klient pobierze sekwencję zadań zgodnie z określonym czasem rozpoczęcia.  

    -   **Zaplanuj, kiedy to wdrożenie wygaśnie**: Określ datę i godzinę wygaśnięcia sekwencji zadań na komputerze docelowym. W przypadku zaznaczenia pola wyboru **UTC** to ustawienie zapewni, że sekwencja zadań wygaśnie dla wielu komputerów docelowych jednocześnie zamiast w różnych godzinach uzależnionych od lokalnego czasu na komputerach docelowych.  

    -   **Harmonogram przypisania**: Określ, kiedy wymagana sekwencja zadań jest uruchomiona na komputerze docelowym. Można dodawać wiele harmonogramów.  

         Można określić datę i godzinę rozpoczęcia harmonogramu, jego częstotliwość: tygodniową, miesięczną lub niestandardową, a także czy sekwencja zadań ma być wykonywana po zdarzeniach takich jak zalogowanie się do komputera lub wylogowanie z niego.  

        > [!NOTE]  
        >  Jeśli zaplanowany czas rozpoczęcia wymaganej sekwencji zadań będzie wcześniejszy niż data i godzina, gdy sekwencja zadań jest dostępna, klienta programu Configuration Manager pobierze sekwencję zadań w zaplanowanym terminie, nawet jeśli sekwencja zadań będzie dostępna wcześniej.  

    -   **Zachowanie ponownego uruchamiania**: Określ czas ponownego uruchomienia sekwencji zadań. Można wybrać jedną z następujących opcji.  

        -   **Nigdy nie uruchamiaj ponownie wdrożonego programu**: Sekwencja zadań nie zostanie uruchomiona ponownie na kliencie, jeśli sekwencja zadań została wcześniej uruchomiona na kliencie. Sekwencja zadań nie zostanie uruchomiona ponownie, nawet jeśli poprzednie uruchomienie zakończyło się niepowodzeniem lub pliki sekwencji zadań uległy zmianie.  

        -   **Zawsze uruchamiaj ponownie program**: Sekwencja zadań będzie zawsze uruchamiana ponownie na kliencie podczas planowania wdrożenia, nawet jeśli sekwencja zadań została poprzednio uruchomiona pomyślnie. To ustawienie jest przydatne zwłaszcza w przypadku używania wdrożeń cyklicznych, wiążących się z regularnymi aktualizacjami sekwencji zadań.  

            > [!IMPORTANT]  
            >  Ta opcja jest zaznaczona domyślnie, jednak nie będzie stosowana do momentu przypisania wymaganego wdrożenia. Użytkownik może zawsze uruchomić ponownie dostępne wdrożenia.  

        -   **Uruchom ponownie, jeśli nie powiodło się poprzednia próba**: Sekwencja zadań zostanie uruchomiona ponownie, podczas planowania wdrożenia tylko wtedy, gdy sekwencja zadań nie może uruchomić wcześniej. To ustawienie jest przydatne zwłaszcza w przypadku wymaganych wdrożeń, umożliwiając ich automatyczne uruchomienie ponowne zgodnie z harmonogramem przypisania, jeśli ostatnia próba uruchomienia zakończyła się niepowodzeniem.  

        -   Uruchom ponownie, jeśli poprzednia próba powiodła się: Sekwencja zadań zostanie uruchomiona ponownie tylko wtedy, gdy zostało wcześniej uruchomione pomyślnie na kliencie. To ustawienie jest przydatne w przypadku używania cyklicznych wdrożeń z regularnie aktualizowaną sekwencją zadań, gdy każda aktualizacja wymaga pomyślnego zainstalowania poprzedniej aktualizacji.  

        > [!NOTE]  
        >  Ponieważ użytkownik może ponownie uruchomić wdrożenie dostępnej sekwencji zadań, przed wdrożeniem dostępnej sekwencji zadań w środowisku produkcyjnym należy starannie oszacować i sprawdzić, co się stanie w przypadku wielokrotnego uruchomienia sekwencji zadań.  

8.  Na stronie **Czynności użytkownika** określ następujące informacje, a następnie kliknij przycisk **Dalej**.  

    -   **Zezwalaj użytkownikowi na uruchamianie programu niezależnie od przypisań**: Określ, czy użytkownik może uruchomić wymaganą sekwencję zadań niezależnie od wdrożonych przypisań.  

    -   **Pokaż postęp sekwencji zadań**: Określ, czy klient programu Configuration Manager Wyświetla postęp sekwencji zadań.  

    -   **Instalacja oprogramowania**: Określ, czy użytkownik może instalować oprogramowanie poza skonfigurowanymi oknami obsługi po zaplanowanym terminie.  

    -   **Ponowne uruchomienie systemu (jeśli jest to wymagane do ukończenia instalacji)**: Określ, czy użytkownik może ponownie uruchomić komputer po zainstalowaniu oprogramowania poza skonfigurowanym oknem obsługi po upływie czasu przypisania.  

    -   **Zezwalaj na uruchamianie dla klienta w Internecie przy użyciu sekwencji zadań**: Określ, czy sekwencja zadań może uruchamiać na klientach internetowych programu Configuration Manager wykryje się w Internecie. To ustawienie nie obsługuje operacji mających na celu zainstalowanie oprogramowania, na przykład systemu operacyjnego. Tej opcji należy używać wyłącznie w połączeniu z ogólnymi sekwencjami zadań na podstawie skryptów, wykonujących operacje w standardowym systemie operacyjnym.  

9. Na stronie **Alerty** określ ustawienia alertów dla tego wdrożenia sekwencji zadań, a następnie kliknij przycisk **Dalej**.  

10. Na stronie **Punkty dystrybucji** określ poniższe informacje, a następnie kliknij przycisk **Dalej**.  

    -   **Opcje wdrażania**: Określ jedną z następujących opcji:  

        > [!NOTE]  
        >  Używając funkcji multiemisji w celu wdrożenia systemu operacyjnego, zawartość należy pobrać na komputery docelowe w momencie, gdy będzie potrzebna, lub przed uruchomieniem sekwencji danych.  

        -   Określ, że klienci mają pobierać zawartość z punktu dystrybucji na komputer docelowy zgodnie z zapotrzebowaniem sekwencji zadań.  

        -   Określ, że klienci mają pobierać całą zawartość z punktu dystrybucji na komputer docelowy przed uruchomieniem sekwencji zadań. Ta opcja nie będzie wyświetlana, jeśli określono, że sekwencja zadań ma być dostępna dla środowiska PXE oraz nośnika rozruchowego (patrz strona **Ustawienia wdrożenia** ).  

        -   Określ, że klienci mają uruchamiać zawartość z punktów dystrybucji. Ta opcja jest dostępna, pod warunkiem że wszystkie pakiety skojarzone z sekwencją zadań będą mogły używać udziału pakietu w punkcie dystrybucji. Aby umożliwić używanie udziału pakietu przez zawartość, wyświetl kartę **Dostęp do danych** w oknie **Właściwości** każdego z pakietów.  

    -   **Gdy żaden lokalny punkt dystrybucji nie jest dostępna, Użyj zdalnego punktu dystrybucji**: Określ, czy klienci mogą używać punktów dystrybucji w powolnych i zawodnych sieciach do pobierania zawartości wymaganej przez sekwencję zadań.  

11. Ukończ pracę kreatora.  

##  <a name="BKMK_ExportImport"></a> Eksportowanie i importowanie sekwencji zadań  
 Sekwencje zadań można eksportować i importować wraz z powiązanymi obiektami, takimi jak obraz systemu operacyjnego, obraz rozruchowy, pakiet agenta klienta, pakiet sterownika oraz aplikacje z zależnościami, lub bez nich.  

 Eksportując i importując sekwencje zadań, uwzględnij następujące kwestie.  

-   Hasła zapisane w sekwencji zadań nie zostaną wyeksportowane. Eksportując i importując sekwencję zadań zawierającą hasła, należy wyedytować importowaną sekwencję zadań i ponownie określić hasła. Upewnij się, że wprowadzono hasła dla [Przyłącz do domeny lub grupy roboczej](../understand/task-sequence-steps.md#BKMK_JoinDomainorWorkgroup), [połączenia do folderu sieciowego](../understand/task-sequence-steps.md#BKMK_ConnectToNetworkFolder), i [Uruchom wiersz polecenia](../understand/task-sequence-steps.md#BKMK_RunCommandLine) akcje.  

- Podczas eksportowania sekwencji zadań z **Ustaw zmienne Dynanmic** kroku wartości nie są eksportowane zmiennych, które zostały skonfigurowane z **wartość tajna** ustawienie. Po zaimportowaniu sekwencji zadań należy ponownie wprowadzić wartości tych zmiennych.

-   W przypadku wielu lokacji głównych zgodnie z najlepszymi praktykami sekwencje zadań należy importować w centralnej lokacji administracyjnej.  

 Aby wyeksportować i zaimportować sekwencję zadań, należy wykonać następującą procedurę.  

#### <a name="to-export-task-sequences"></a>Aby wyeksportować sekwencje zadań  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Sekwencje zadań**.  

3.  Z listy **Sekwencja zadań** wybierz sekwencję, którą chcesz wyeksportować. W przypadku wybrania więcej niż jednej sekwencji zostaną one zapisane w jednym pliku eksportu.  

4.  Na karcie **Narzędzia główne** w grupie **Sekwencja zadań** kliknij przycisk **Eksport** , aby uruchomić Kreatora sekwencji zadań eksportu.  

5.  Na stronie **Ogólne** określ następujące informacje, a następnie kliknij przycisk **Dalej**.  

    -   W polu **Plik** określ lokalizację i nazwę pliku eksportu. Jeśli bezpośrednio wprowadzasz nazwę pliku, pamiętaj o dodaniu rozszerzenia .zip do nazwy. Jeśli wprowadzasz nazwę pliku eksportu przy użyciu funkcji przeglądania, kreator automatycznie doda to rozszerzenie do nazwy pliku.  

    -   Usuń zaznaczenie **Eksportuj wszystkie zależności sekwencji zadań** , jeśli nie chcesz eksportować tych zależności. Domyślnie kreator wykona skanowanie w poszukiwaniu powiązanych obiektów i wyeksportuje je wraz z sekwencją zadań. Dotyczy to również wszelkich zależności aplikacji.  

    -   Usuń zaznaczenie pola wyboru **Eksportuj całą zawartość dla wybranych sekwencji zadań i zależności** , jeśli nie chcesz kopiować zawartości ze źródła pakietu do lokalizacji plików eksportu. Zaznaczenie tego pola wyboru spowoduje, że Kreator sekwencji zadań importu użyje ścieżki importu jako nowej lokalizacji źródła pakietu.  

    -   W polu **Komentarze administratora** dodaj opis sekwencji zadań do wyeksportowania.  

6.  Ukończ pracę kreatora.  

 Kreator utworzy następujące pliki wyjściowe:  

-   Bez eksportu zawartości: plik zip.  

-   Z eksportem zawartości: plik zip oraz folder o nazwie *export*_files, gdzie *export* to nazwa pliku zip zawierającego wyeksportowaną zawartość.  

 W przypadku uwzględnienia zawartości podczas eksportowania sekwencji zadań pamiętaj o skopiowaniu pliku .zip i folderu *export*_files, ponieważ w przeciwnym razie import zakończy się niepowodzeniem.  

#### <a name="to-import-task-sequences"></a>Aby zaimportować sekwencje zadań  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Sekwencje zadań**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Importuj sekwencję zadań** , aby uruchomić Kreatora sekwencji importu zadań.  

4.  Na stronie **Ogólne** określ eksportowany plik *.zip, a następnie kliknij przycisk **Dalej**.  

5.  Na stronie **Zawartość pliku** wybierz akcję, która jest wymagana w przypadku każdego importowanego obiektu. Ta strona zawiera wszystkie obiekty, które zostaną zaimportowane programu Configuration Manager.  

    -   Jeśli obiekt nie był nigdy importowany, wybierz polecenie **Utwórz nowy**.  

    -   Jeśli obiekt był wcześniej importowany, wybierz jedną z następujących akcji:  

        -   **Ignoruj duplikat** (domyślnie): Ta akcja nie importuje obiektu. Zamiast importowania, kreator łączy istniejący obiekt z sekwencją zadań.  

        -   **Zastąp**: Ta akcja zastępuje istniejący obiekt importowanym obiektem. W przypadku aplikacji można dodać wersję aktualizującą istniejącą aplikację lub utworzyć nową aplikację.  

6.  Ukończ pracę kreatora.  

 Po zaimportowaniu sekwencji zadań edytuj sekwencję zadań, aby określić hasła z oryginalnej sekwencji zadań. Ze względu na bezpieczeństwo hasła nie są eksportowane.  

##  <a name="BKMK_CreateTSVariables"></a> Tworzenie zmiennych sekwencji zadań dla komputerów i kolekcji  
 Można definiować niestandardowe zmienne sekwencji zadań dla komputerów i kolekcji. Zmienne definiowane dla komputera są określane zmiennymi sekwencji zadań dla komputera. Zmienne definiowane dla kolekcji są określane zmiennymi sekwencji zadań dla kolekcji. W przypadku konfliktu zmienne dla komputera mają pierwszeństwo przed zmiennymi dla kolekcji. Oznacza to, że zmienne sekwencji zadań przypisane do konkretnego komputera automatycznie mają wyższy priorytet niż zmienne przypisane do kolekcji zawierającej komputer.  

 Jeśli na przykład do kolekcji ABC jest przypisana zmienna, a komputer XYZ, który jest członkiem kolekcji ABC, ma przypisaną zmienną o takiej samej nazwie, zmienna przypisana do komputera XYZ ma wyższy priorytet niż zmienna przypisana do kolekcji ABC.  

 Zmienne dla komputera i dla kolekcji można ukryć, tak aby nie były widoczne w konsoli programu Configuration Manager. Aby zmienne nie były ukryte, należy usunąć je i ponownie zdefiniować bez wybierania opcji ukrycia. Po wybraniu opcji **Nie wyświetlaj tej wartości w konsoli Configuration Manager**wartość zmiennej nie będzie wyświetlana, ale uruchomiona sekwencja zadań może jej użyć.  

 Zmiennymi dla komputera można zarządzać w lokacji głównej lub w centralnej lokacji administracyjnej. Programu Configuration Manager nie obsługuje więcej niż 1000 przypisanej zmienne dla komputera.  

> [!WARNING]  
>  W przypadku używania zmiennych dla kolekcji z sekwencjami zadań należy wziąć pod uwagę następujące kwestie:  
>   
>  -   Ponieważ zmiany wprowadzane do kolekcji są zawsze replikowane w całej hierarchii, wszelkie zmiany zmiennych kolekcji mają zastosowanie nie tylko do członków bieżącej lokacji, lecz do wszystkich członków kolekcji w całej hierarchii.  
> -   Usunięcie kolekcji powoduje usunięcie zmiennych sekwencji zadań, które są skonfigurowane dla tej kolekcji.  

 Aby utworzyć zmienne sekwencji zadań dla komputera lub kolekcji, wykonaj czynności opisane w poniższych procedurach.  

#### <a name="to-create-task-sequence-variables-for-a-computer"></a>Aby utworzyć zmienne sekwencji zadań dla komputera  

1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.  

2.  W obszarze roboczym **Zasoby i zgodność** rozwiń kolekcję zawierającą komputer, do którego chcesz dodać zmienną.  

3.  Wybierz komputer i kliknij pozycję **Właściwości**.  

4.  W oknie dialogowym **Właściwości** kliknij kartę **Zmienne** .  

5.  Dla każdej zmiennej, którą chcesz utworzyć, kliknij przycisk **nowy** ikonę w **< nowy\> zmiennej** okna dialogowego i określ nazwę oraz wartość zmiennej sekwencji zadań. Wyczyść **nie wyświetlaj tej wartości w konsoli programu Configuration Manager** pole wyboru, jeśli chcesz ukryć zmienne, tak aby nie były widoczne w konsoli programu Configuration Manager.  

6.  Po dodaniu wszystkich zmiennych do komputera kliknij przycisk **OK**.  

#### <a name="to-create-task-sequence-variables-for-a-collection"></a>Aby utworzyć zmienne sekwencji zadań dla kolekcji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.  

2.  W obszarze roboczym **Zasoby i zgodność** wybierz kolekcję, do której chcesz dodać zmienną, i kliknij pozycję **Właściwości**.  

3.  W oknie dialogowym **Właściwości** kliknij kartę **Zmienne kolekcji** .  

4.  Dla każdej zmiennej, którą chcesz utworzyć, kliknij przycisk **nowy** ikonę w **< nowy\> zmiennej** okna dialogowego i określ nazwę oraz wartość zmiennej sekwencji zadań. Wyczyść **nie wyświetlaj tej wartości w konsoli programu Configuration Manager** pole wyboru, jeśli chcesz ukryć zmienne, tak aby nie były widoczne w konsoli programu Configuration Manager.  

5.  Opcjonalnie określ priorytet dla programu Configuration Manager do użycia podczas oceny zmiennych sekwencji zadań.  

6.  Po dodaniu wszystkich zmiennych do kolekcji kliknij przycisk **OK**.  

##  <a name="BKMK_AdditionalActionsTS"></a> Dodatkowe akcje zarządzania sekwencjami zadań  
 Wybieranymi sekwencjami zadań można zarządzać za pomocą dodatkowych akcji, wykonując czynności opisane w poniższej procedurze.  

#### <a name="to-select-a-task-sequence-to-manage"></a>Aby wybrać sekwencję zadań do zarządzania  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne** , a następnie kliknij przycisk **Sekwencje zadań**.  

3.  Z listy **Sekwencja zadań** wybierz sekwencję, którą chcesz zarządzać, a następnie wybierz jedną z dostępnych opcji.  

 Więcej informacji o niektórych dodatkowych akcjach zarządzania sekwencjami zadań znajduje się w poniższej tabeli.  

|Akcja|Opis|  
|------------|-----------------|  
|**Kopiuj**|Wykonuje kopię wybranej sekwencji zadań. Ta akcja może się przydać, gdy chcesz utworzyć nową sekwencję zadań na podstawie istniejącej sekwencji.<br /><br /> W przypadku kopiowania sekwencji zadań w folderze kopia będzie widoczna w tym folderze, aż do chwili odświeżenia węzła sekwencji zadań.  Po odświeżeniu kopia stanie się widoczna w folderze głównym.|  
|**Wyłącz**|Wyłącza sekwencję zadań, tak aby nie można jej było uruchomić na komputerach. Wyłączone sekwencje zadań można wdrażać na komputerach, jednak komputery nie mogą jej uruchamiać, aż do jej włączenia.|  
|**Włączenie**|Włącza sekwencję zadań, tak aby można ją było uruchamiać. Po włączeniu wdrożonej sekwencji zadań jej ponowne wdrożenie nie jest konieczne.|  
|**Tworzenie wstępnie przygotowanego pliku zawartości**|Uruchamia Kreatora tworzenia przygotowanego pliku zawartości w celu wstępnego przygotowania zawartości sekwencji zadań. Aby uzyskać informacje o sposobie tworzenia wstępnie przygotowanego pliku zawartości, zobacz [wstępnie przygotować zawartość](../../core/servers/deploy/configure/deploy-and-manage-content.md#a-namebkmkprestagea-use-prestaged-content).|  
|**Przenieś**|Przenosi wybraną sekwencję zadań do innego folderu.|  
|**Właściwości**|Otwiera okno dialogowe **Właściwości** dla wybranej sekwencji zadań. To okno dialogowe umożliwia zmianę zachowania obiektu sekwencji zadań. Za jego pomocą nie można jednak zmieniać kolejności kroków w sekwencji zadań.|  

## <a name="next-steps"></a>Następne kroki
[Scenariusze wdrażania systemów operacyjnych enterprise](scenarios-to-deploy-enterprise-operating-systems.md)

