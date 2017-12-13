---
title: "Tworzenie sekwencji zadań w celu przechwycenia systemu operacyjnego"
titleSuffix: Configuration Manager
description: "Sekwencji zadań kompilacji i przechwytywania tworzy komputera odniesienia, który może zawierać określone sterowniki i aktualizacje oprogramowania z systemem operacyjnym."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 25e4ac68-0e78-4bbe-b8fc-3898b372c4e8
caps.latest.revision: "19"
caps.handback.revision: "0"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: c376a6b600e775f532410ad467b99cda1fbfc575
ms.sourcegitcommit: 08f9854fb6c6d21e1e923b13e38a64d0bc2bc9a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2017
---
# <a name="create-a-task-sequence-to-capture-an-operating-system-in-system-center-configuration-manager"></a>Tworzenie sekwencji zadań w celu przechwycenia systemu operacyjnego w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Korzystając z sekwencji zadań do wdrażania systemu operacyjnego do komputera w programie System Center Configuration Manager, komputer instaluje obraz systemu operacyjnego, który określisz w sekwencji zadań. Aby dostosować obraz systemu operacyjnego, uwzględniając określone sterowniki, aplikacje, aktualizacje oprogramowania itd., należy użyć sekwencji zadań tworzenia i przechwytywania w celu utworzenia komputera odniesienia, a następnie przechwycić z niego obraz systemu operacyjnego. Jeśli istnieje już komputer odniesienia dostępny do przechwycenia, można utworzyć niestandardową sekwencję zadań, aby przechwycić system operacyjny. Poniższe sekcje zawierają informacje dotyczące przechwytywania niestandardowego systemu operacyjnego.  

##  <a name="BKMK_BuildCaptureTS"></a> Tworzenie i przechwytywanie komputera odniesienia przy użyciu sekwencji zadań  
 Sekwencja zadań kompilacji i przechwycenia partycje i formatuje komputera odniesienia, instaluje system operacyjny, a także aktualizacje klienta, aplikacji i oprogramowania programu Configuration Manager i następnie przechwytuje system operacyjny z komputera odniesienia. Pakiety skojarzone z tą sekwencją zadań, takie jak aplikacje, muszą być dostępne w punktach dystrybucji przed utworzeniem sekwencji zadań tworzenia i przechwytywania.  

###  <a name="BKMK_CreatePackages"></a> Przygotowywanie do wdrażania systemu operacyjnego  
 Istnieje wiele scenariuszy wdrażania systemu operacyjnego na komputerach w danym środowisku. W większości przypadków należy utworzyć sekwencję zadań i wybrać pozycję **Zainstaluj istniejący pakiet obrazów** w Kreatorze tworzenia sekwencji zadań, aby zainstalować system operacyjny, przeprowadzić migrację ustawień użytkowników, zastosować aktualizacje oprogramowania i zainstalować aplikacje. Przed utworzeniem sekwencji zadań do zainstalowania systemu operacyjnego muszą być spełnione następujące warunki:  

-   **Wymagane**  

    -   [Obrazu rozruchowego](../get-started/manage-boot-images.md) muszą być dostępne w konsoli programu Configuration Manager.  

    -   [Obrazu systemu operacyjnego](../get-started/manage-operating-system-images.md) muszą być dostępne w konsoli programu Configuration Manager.  

-   **Wymagane (jeśli są używane)**  

    -   [Pakiety sterowników](../get-started/manage-drivers.md) zawierających niezbędne sterowniki systemu Windows do obsługi sprzętu na komputerze odniesienia musi być dostępny w konsoli programu Configuration Manager. Aby uzyskać więcej informacji o krokach sekwencji zadań w zakresie zarządzania sterownikami, zobacz [sekwencje zadań, aby zainstalować sterowniki urządzeń](../get-started/manage-drivers.md#BKMK_TSDrivers).  

    -   [Aktualizacje oprogramowania](../../sum/get-started/synchronize-software-updates.md) muszą być zsynchronizowane w konsoli programu Configuration Manager.  

    -   [Aplikacje](../../apps/deploy-use/create-applications.md) muszą zostać dodane do konsoli programu Configuration Manager.  

###  <a name="BKMK_CreateBuildCaptureTS"></a> Tworzenie sekwencji zadań tworzenia i przechwytywania  
 Wykonaj następującą procedurę, aby za pomocą sekwencji zadań tworzenia i przechwytywania utworzyć komputer odniesienia i przechwycić system operacyjny.  

#### <a name="to-create-a-task-sequence-that-builds-and-captures-an-operating-system-image"></a>Aby utworzyć sekwencję zadań, która skompiluje i przechwyci obraz systemu operacyjnego  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Sekwencje zadań**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz sekwencję zadań** , aby uruchomić Kreatora tworzenia sekwencji zadań.  

4.  Na stronie **Utwórz nową sekwencję zadań** wybierz opcję **Utwórz i przechwyć referencyjny obraz systemu operacyjnego**.  

5.  Na stronie **Informacje o sekwencji zadań** określ poniższe ustawienia, a następnie kliknij przycisk **Dalej**.  

    -   **Nazwa sekwencji zadań**: Określ nazwę identyfikującą sekwencję zadań.  

    -   **Opis elementu**: Określ opis zadania wykonywanego przez sekwencję zadań, na przykład opis systemu operacyjnego, który jest tworzony przez sekwencję zadań.  

    -   **Obraz rozruchowy**: Określ obraz rozruchowy, który instaluje obraz systemu operacyjnego.  

        > [!IMPORTANT]  
        >  Architektura obrazu rozruchowego musi być zgodna z architekturą sprzętową komputera docelowego.  

6.  Na stronie **Instalowanie systemu Windows** określ poniższe ustawienia, a następnie kliknij przycisk **Dalej**.  

    -   **Pakiet obrazów**: Określ pakiet obrazu systemu operacyjnego, który zawiera pliki, które są wymagane do zainstalowania systemu operacyjnego.  

    -   **Indeks obrazu**: Określ system operacyjny do zainstalowania. Jeśli obraz systemu operacyjnego zawiera wiele wersji, wybierz wersję do zainstalowania.  

    -   **Klucz produktu**: Określ klucz produktu systemu operacyjnego do zainstalowania. Możesz określić zakodowane klucze licencji zbiorczych oraz standardowe klucze produktów. W przypadku użycia niezakodowanego klucza produktu poszczególne grupy 5 znaków muszą być oddzielone kreskami (-). Na przykład: *XXXXX-XXXXX-XXXXX-XXXXX-XXXXX*  

    -   **Tryb licencjonowania serwera**: Określ, czy serwer licencji jest **na stanowisko**, **na serwer**, lub które nie licencji. W przypadku wybrania licencji serwera **Na serwer**określ również maksymalną liczbę połączeń serwera.  

    -   Określ w jaki sposób ma być obsługiwane konto administratora używane po wdrożeniu systemu operacyjnego.  

        -   **Losowo Generuj hasło administratora lokalnego i Wyłącz konto na wszystkich obsługiwanych platformach**: Określ, czy program Configuration Manager ma losowo utworzyć hasło dla konta administratora lokalnego i wyłączył to konto po wdrożeniu systemu operacyjnego.  

        -   **Włącz konto i określ hasło administratora lokalnego**: Określ, czy jest używane to samo hasło dla konta administratora lokalnego na wszystkich komputerach, których jest wdrażany system operacyjny.  

7.  Na stronie **Konfigurowanie sieci** określ poniższe ustawienia, a następnie kliknij przycisk **Dalej**.  

    -   **Przyłącz do grupy roboczej**: Określ, czy dodać komputer docelowy do grupy roboczej po wdrożeniu systemu operacyjnego.  

    -   **Przyłącz do domeny**: Określ, czy dodać komputer docelowy do domeny po wdrożeniu systemu operacyjnego. W polu **Domena**określ nazwę domeny.  

        > [!IMPORTANT]  
        >  W lesie lokalnym możesz przeglądać w poszukiwaniu domen, lecz w przypadku lasu zdalnego musisz określić nazwę domeny.  

         Możesz również określić jednostkę organizacyjną (OU). To jest ustawienie opcjonalne określające nazwę wyróżniającą LDAP X.500 jednostki OU, w której ma zostać utworzone konto komputera, jeżeli jeszcze nie istnieje.  

    -   **Konto**: Określ nazwę użytkownika i hasło dla konta, które ma uprawnienia do dołączenia do określonej domeny. Przykład: *domena\użytkownik* lub *%zmienna%*.  

        > [!IMPORTANT]  
        >  Aby przeprowadzić migrację ustawień domeny lub ustawień grupy roboczej, wprowadź odpowiednie poświadczenia domeny.  

8.  Na **Instalowanie programu Configuration Manager** Określ pakiet klienta programu Configuration Manager, który zawiera pliki źródłowe instalacji klienta programu Configuration Manager, Dodaj wszelkie dodatkowe właściwości niezbędne do zainstalowania klienta, a następnie kliknij pozycję **dalej**.  

     Aby uzyskać więcej informacji o właściwościach, które mogą służyć do instalowania klienta, zobacz [o właściwościach instalacji klienta](../../core/clients/deploy/about-client-installation-properties.md).  

9. Na stronie **Dołączanie aktualizacji** określ, czy instalować wymagane aktualizacje oprogramowania lub wszystkie aktualizacje, bądź nie instalować żadnych aktualizacji, a następnie kliknij przycisk **Dalej**. Po wybraniu opcji instalowania aktualizacji oprogramowania programu Configuration Manager instaluje tylko aktualizacje oprogramowania, które są przeznaczone do kolekcji, których członkiem jest komputer docelowy.  

10. Na stronie **Instalowanie aplikacji** określ aplikacje do zainstalowania na komputerze docelowym, a następnie kliknij przycisk **Dalej**. Jeżeli określisz wiele aplikacji, możesz również wybrać, aby nie przerywać sekwencji zadań w przypadku niepowodzenia instalowania określonej aplikacji.  

11. Na stronie **Przygotowanie systemu** określ następujące ustawienia, a następnie kliknij przycisk **Dalej**.  

    -   **Pakiet**: Określ pakiet programu Configuration Manager, który zawiera odpowiednią wersję programu Sysprep do przechwycenia ustawień komputera odniesienia.  

         W przypadku korzystania z systemu Windows Vista lub nowszego program Sysprep jest automatycznie instalowany na komputerze i nie trzeba określać pakietu.  

12. Na stronie **Właściwości obrazu** określ następujące ustawienia obrazu systemu operacyjnego, a następnie kliknij przycisk **Dalej**.  

    -   **Utworzone przez**: Określ nazwę użytkownika, który utworzył obraz systemu operacyjnego.  

    -   **Wersja**: Określ numer wersji zdefiniowane przez użytkownika, który jest skojarzony z obrazem systemu operacyjnego.  

    -   **Opis elementu**: Określ zdefiniowany przez użytkownika opis obrazu komputera systemu operacyjnego.  

13. Na stronie **Przechwytywanie obrazu** określ następujące ustawienia, a następnie kliknij przycisk **Dalej**.  

    -   **Ścieżka**: Określ udostępniony folder sieciowy gdzie dane wyjściowe. Plik WIM jest przechowywany. Ten plik zawiera obraz systemu operacyjnego oparty na ustawieniach określonych za pomocą tego kreatora. W przypadku określenia folderu z istniejącym plikiem .WIM plik ten zostanie zastąpiony.  

    -   **Konto**: Określ konto systemu Windows, które ma uprawnienia do udziału sieciowego, w którym jest przechowywany obraz.  

14. Ukończ pracę kreatora.  

15. Aby dodać kolejne kroki do sekwencji zadań, wybierz utworzoną sekwencję zadań i kliknij przycisk **Edytuj**. Aby uzyskać informacje o sposobie edytowania sekwencji zadań, zobacz [edytowania sekwencji zadań](manage-task-sequences-to-automate-tasks.md#BKMK_ModifyTaskSequence).  

 Sekwencję zadań można wdrożyć na komputerze odniesienia w jeden z następujących sposobów:  

-   Jeśli komputer odniesienia jest klientem programu Configuration Manager, można wdrożyć kompilacji i przechwycenia sekwencji zadań do kolekcji, która zawiera komputer odniesienia. Aby uzyskać informacje o sposobie edycji wdrażania obrazu systemu operacyjnego, zobacz [tworzenia sekwencji zadań w celu zainstalowania systemu operacyjnego](create-a-task-sequence-to-install-an-operating-system.md).  

    > [!NOTE]  
    >  Jeśli sekwencja zadań zawiera krok dzielenia dysku na partycje, nie należy wybierać opcji **Pobierz program** podczas wdrażania sekwencji zadań.  

-   Jeśli komputer odniesienia nie jest klientem programu Configuration Manager lub jeśli chcesz ręcznie uruchomić sekwencję zadań na komputerze odniesienia, uruchom **zadania Kreatora tworzenia nośnika sekwencji** do tworzenia nośnika rozruchowego. Aby uzyskać informacje o sposobie tworzenia nośnika rozruchowego, zobacz [tworzenia nośnika rozruchowego](create-bootable-media.md).  

##  <a name="BKMK_CaptureExistingRefComputer"></a> Przechwytywanie obrazu systemu operacyjnego z istniejącego komputera odniesienia  
 Jeśli istnieje już komputer odniesienia gotowy do przechwycenia, możesz utworzyć sekwencję zadań służącą do przechwycenia systemu operacyjnego z komputera odniesienia. Krok sekwencji zadań **Przechwyć obraz systemu operacyjnego** umożliwia przechwycenie jednego lub więcej obrazów z komputera odniesienia i zapisanie ich w pliku obrazów (wim) w określonym udziale sieciowym. Komputer odniesienia jest uruchamiany w środowisku Windows PE przy użyciu obrazu rozruchowego, a każdy dysk twardy na komputerze odniesienia jest przechwytywany jako oddzielny obraz w pliku wim. Jeśli określony komputer ma wiele dysków, wynikowy plik wim będzie zawierał osobny obraz każdego woluminu. Przechwytywane są t ylko woluminy sformatowane przy użyciu systemu NTFS lub FAT32. Woluminy w innych formatach i woluminy USB są pomijane.  

 Aby przechwycić obraz systemu operacyjnego z istniejącego komputera odniesienia, wykonaj poniższą procedurę.  

#### <a name="to-capture-an-operating-system-from-an-existing-reference-computer"></a>Aby przechwycić system operacyjny z istniejącego komputera odniesienia  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Sekwencje zadań**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz sekwencję zadań** , aby uruchomić Kreatora tworzenia sekwencji zadań.  

4.  Na stronie **Tworzenie nowej sekwencji zadań** wybierz opcję **Utwórz nową niestandardową sekwencję zadań**.  

5.  Na stronie **Informacje o sekwencji zadań** określ nazwę i opis sekwencji zadań.  

6.  Określ obraz rozruchowy dla sekwencji zadań. Ten obraz rozruchowy jest używany do uruchomienia środowiska Windows PE na komputerze odniesienia.  Aby uzyskać więcej informacji, zobacz [zarządzanie obrazami rozruchowymi](../get-started/manage-boot-images.md).  

7.  Ukończ pracę kreatora.  

8.  Z listy **Sekwencje zadań**wybierz niestandardową sekwencję zadań, a następnie na karcie **Narzędzia główne** w grupie **Sekwencja zadań** kliknij pozycję **Edytuj** , aby otworzyć edytor sekwencji zadań.  

9. Ten krok należy używać tylko wtedy, gdy klient programu Configuration Manager jest zainstalowany na komputerze odniesienia.  

     Kliknij przycisk **Dodaj**, kliknij przycisk **obrazów**, a następnie kliknij przycisk [przygotować klienta programu ConfigMgr do przechwycenia](../understand/task-sequence-steps.md#BKMK_PrepareConfigMgrClientforCapture). Ten krok sekwencji zadań pobiera klienta programu Configuration Manager na komputerze odniesienia i przygotowuje go do przechwycenia w ramach procesu przetwarzania obrazów.  

    > [!Note]  
    >  Sekwencja zadań nie obsługuje odinstalowanie klienta programu Configuration Manager.

10. Kliknij przycisk **Dodaj**, kliknij przycisk **obrazów**, a następnie kliknij przycisk [Przygotuj system Windows do przechwycenia](../understand/task-sequence-steps.md#BKMK_PrepareWindowsforCapture). Ta akcja sekwencji zadań uruchamia narzędzie Sysprep, a następnie ponownie uruchamia komputer za pomocą obrazu rozruchowego środowiska Windows PE określonego dla sekwencji zadań. Jeśli k omputer odniesienia jest przyłączony do domeny, ta akcja nie zostanie ukończona pomyślnie.  

11. Kliknij przycisk **Dodaj**, kliknij przycisk **obrazów**, a następnie kliknij przycisk [Przechwyć obraz systemu operacyjnego](../understand/task-sequence-steps.md#BKMK_CaptureOperatingSystemImage).  Ta sekwencja zadań zostanie uruchomiona tylko w środowisku Windows PE w celu przechwycenia dysków twardych na komputerze odniesienia. Skonfiguruj następujące ustawienia kroku sekwencji zadań.  

    -   **Nazwa** i **opis**: Opcjonalnie można zmienić nazwę kroku sekwencji zadań i podać opis.  

    -   **Docelowy**: Określ udostępniony folder sieciowy gdzie dane wyjściowe. Plik WIM jest przechowywany. Ten plik zawiera obraz systemu operacyjnego oparty na ustawieniach określonych za pomocą tego kreatora. W przypadku określenia folderu z istniejącym plikiem .WIM plik ten zostanie zastąpiony.  

    -   **Opis elementu**, **wersji**, i **utworzone przez**: Opcjonalnie możesz podać szczegółowe informacje dotyczące obrazu, który zostanie przechwycony.  

    -   **Konto przechwytywania obrazu systemu operacyjnego**: Określ konto systemu Windows, które ma uprawnienia do sieci określonego udziału. Kliknij pozycję **Ustaw** , aby określić nazwę tego konta systemu Windows.  

     Aby zamknąć edytor sekwencji zadań, kliknij przycisk **OK** .  

 Sekwencję zadań można wdrożyć na komputerze odniesienia w jeden z następujących sposobów:  

-   Jeśli komputer odniesienia jest klientem programu Configuration Manager, sekwencja zadań można wdrożyć do kolekcji, która zawiera komputer odniesienia. Aby uzyskać informacje o sposobie edycji wdrażania obrazu systemu operacyjnego, zobacz [tworzenia sekwencji zadań w celu zainstalowania systemu operacyjnego](create-a-task-sequence-to-install-an-operating-system.md).  

-   Jeśli komputer odniesienia nie jest klientem programu Configuration Manager lub jeśli chcesz ręcznie uruchomić sekwencję zadań na komputerze odniesienia, uruchom **zadania Kreatora tworzenia nośnika sekwencji** do tworzenia nośnika rozruchowego. Aby uzyskać informacje o sposobie tworzenia nośnika rozruchowego, zobacz [tworzenia nośnika rozruchowego](create-bootable-media.md).  

##  <a name="BKMK_BuildandCaptureTSExample"></a> Przykład sekwencji zadań do tworzenia i przechwytywania obrazu systemu operacyjnego  
 W poniższej tabeli przedstawiono wskazówki pomocne podczas tworzenia sekwencji zadań w celu utworzenia i przechwycenia obrazu systemu operacyjnego. Tabela pomoże określić ogólną sekwencję kroków w sekwencji zadań oraz sposób organizowania tych kroków sekwencji zadań w grupach logicznych. Tworzona sekwencja zadań może się różnić od tego przykładu i może zawierać więcej lub mniej kroków sekwencji zadań i grup.  

> [!IMPORTANT]  
>  Ten typ sekwencji zadań należy zawsze tworzyć przy użyciu Kreatora tworzenia sekwencji zadań.  

 W przypadku utworzenia nowej sekwencji zadań przy użyciu polecenia **Nowa sekwencja zadań** niektóre nazwy kroków sekwencji zadań różnią się od nazw kroków sekwencji zadań dodawanych ręcznie do istniejącej sekwencji zadań. Różnice nazewnictwa przedstawiono w poniższej tabeli:  

|Nazwa kroku sekwencji zadań w Kreatorze nowej sekwencji zadań|Równoważna nazwa kroku w edytorze sekwencji zadań|  
|------------------------------------------------------|-----------------------------------------------|  
|Uruchom ponownie w systemie Windows PE|Wykonaj ponowny rozruch przy użyciu środowiska Windows PE lub dysku twardego|  
|Podziel dysk 0 na partycje|Formatuj dysk i podziel go na partycje|  
|Zastosuj sterowniki urządzeń|Automatycznie zastosuj sterowniki|  
|Zainstaluj aktualizacje|Instalowanie aktualizacji oprogramowania|  
|Przyłącz do grupy roboczej|Przyłącz do domeny lub grupy roboczej|  
|Przygotuj klienta programu ConfigMgr|Prepare ConfigMgr Client for Capture|  
|Przygotuj system operacyjny|Prepare Windows for Capture|  
|Przechwyć komputer odniesienia|Przechwyć obraz systemu operacyjnego|  

|Grupa/krok sekwencji zadań|Tematy pomocy|  
|-------------------------------|---------------|  
|Utwórz komputer odniesienia — **(nowa grupa sekwencji zadań)**|Umożliwia utworzenie grupy sekwencji zadań. Grupa sekwencji zadań przechowuje podobne kroki sekwencji zadań w celu zapewnienia lepszej organizacji i kontroli błędów.<br /><br /> Ta grupa zawiera akcje niezbędne do utworzenia komputera odniesienia.|  
|Uruchom ponownie w systemie Windows PE|Ten krok sekwencji zadań umożliwia określenie opcji ponownego uruchomienia komputera docelowego. Ten krok zapewnia wyświetlenie użytkownikowi komunikatu z informacją o ponownym uruchomieniu komputera, aby umożliwić kontynuowanie instalacji.<br /><br /> W tym kroku jest używana zmienna sekwencji zadań tylko do odczytu **_SMSTSInWinPE** . Jeśli skojarzona wartość jest równa **false** , ten krok sekwencji zadań będzie kontynuowany.|  
|Podziel dysk 0 na partycje|Ten krok sekwencji zadań umożliwia określenie akcji niezbędnych do sformatowania dysku twardego na komputerze docelowym. Domyślny numer dysku to **0**.<br /><br /> W tym kroku jest używana zmienna sekwencji zadań tylko do odczytu **_SMSTSClientCache** . Ten krok zostanie uruchomiony, jeśli pamięć podręczna klienta programu Configuration Manager nie istnieje.|  
|Zastosuj system operacyjny|Ten krok sekwencji zadań umożliwia zainstalowanie określonego obrazu systemu operacyjnego na komputerze docelowym. Ten krok należy wykonać wszystkie obrazy woluminów zawarte w pliku WIM do odpowiednich sekwencyjnych woluminów dysku na komputerze docelowym po wcześniejszym usunięciu wszystkich plików w danym woluminie (z wyjątkiem plików sterowania specyficzne dla programu Configuration Manager).|  
|Zastosuj ustawienia systemu Windows|Ten krok sekwencji zadań umożliwia skonfigurowanie informacji o konfiguracji ustawień systemu Windows dla komputera docelowego.|  
|Zastosuj ustawienia sieci|Ten krok sekwencji zadań pozwala określić informacje o konfiguracji sieci lub grupy roboczej dla komputera docelowego.|  
|Zastosuj sterowniki urządzeń|Ten krok sekwencji zadań umożliwia dopasowanie i zainstalowanie sterowników w ramach wdrażania systemu operacyjnego. Możesz zezwolić Instalatorowi systemu Windows na przeszukanie wszystkich istniejących kategorii sterowników, wybierając pozycję **Uwzględnij sterowniki z wszystkich kategorii** , lub ograniczyć kategorie sterowników przeszukiwane przez Instalatora systemu Windows, wybierając pozycję **Ogranicz dopasowywanie tylko do sterowników z wybranych kategorii**.<br /><br /> W tym kroku jest używana zmienna sekwencji zadań tylko do odczytu **_SMSTSMediaType** . Jeśli skojarzona wartość nie jest równa **FullMedia** , zostanie uruchomiony ten krok sekwencji zadań.|  
|Zainstaluj system Windows i program ConfigMgr|Ten krok sekwencji zadań należy zainstalować oprogramowanie klienta programu Configuration Manager. Configuration Manager instaluje i rejestruje identyfikator GUID klienta programu Configuration Manager. Niezbędne parametry instalacji można przypisać w oknie **Właściwości instalacji** .|  
|Zainstaluj aktualizacje|Ten krok sekwencji zadań umożliwia określenie sposobu instalacji aktualizacji oprogramowania na komputerze docelowym. Komputer docelowy nie jest sprawdzany pod kątem dostępności odpowiednich aktualizacji oprogramowania do czasu uruchomienia tego kroku sekwencji zadań. W tym momencie komputer docelowy sprawdzania pod kątem aktualizacji oprogramowania jak inny klient zarządzany przez Menedżera konfiguracji.<br /><br /> W tym kroku jest używana zmienna sekwencji zadań tylko do odczytu **_SMSTSMediaType** . Jeśli skojarzona wartość nie jest równa **FullMedia** , zostanie uruchomiony ten krok sekwencji zadań.|  
|Przechwyć komputer odniesienia — **(nowa grupa sekwencji zadań)**|Umożliwia utworzenie następnej grupy sekwencji zadań. Ta grupa zawiera kroki niezbędne do przygotowania i przechwycenia komputera odniesienia.|  
|Przyłącz do grupy roboczej|Ten krok sekwencji zadań umożliwia określenie informacji niezbędnych do przyłączenia komputera docelowego do grupy roboczej.|  
|Prepare ConfigMgr Client for Capture|Ten krok umożliwia wykonywanie klienta programu Configuration Manager na komputerze odniesienia i przygotowuje go do przechwycenia w ramach procesu przetwarzania obrazów|  
|Przygotuj system operacyjny|Ten krok sekwencji zadań umożliwia określenie opcji programu Sysprep, które mają zostać użyte podczas przechwytywania ustawień systemu Windows z komputera odniesienia. W tym kroku sekwencji zadań jest uruchamiany program Sysprep, a następnie jest wykonywany ponowny rozruch komputera za pomocą obrazu rozruchowego środowiska Windows PE określonego dla sekwencji zadań.|  
|Przechwyć obraz systemu operacyjnego|Ten krok sekwencji zadań umożliwia wprowadzenie określonego istniejącego udziału sieciowego i pliku WIM do użycia podczas zapisywania obrazu. Ta lokalizacja jest używana jako źródłowa lokalizacja pakietu podczas dodawania pakietu obrazów systemu operacyjnego przy użyciu **Kreatora dodawania pakietu obrazów systemu operacyjnego**.|  

 Po przechwyceniu obrazu z komputera odniesienia nie należy przechwytywać z niego kolejnego obrazu systemu operacyjnego, ponieważ podczas konfiguracji początkowej tworzone są wpisy rejestru. Nowy komputer odniesienia należy utworzyć przy każdym przechwytywaniu systemu operacyjnego. Jeśli planujesz używać tego samego komputera odniesienia do tworzenia obrazów systemu operacyjnego w przyszłości, należy najpierw odinstalować klienta programu Configuration Manager, a następnie ponownie zainstalować klienta programu Configuration Manager.  

## <a name="next-steps"></a>Następne kroki  
[Metody wdrażania systemów operacyjnych dla przedsiębiorstw](methods-to-deploy-enterprise-operating-systems.md)
