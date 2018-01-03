---
title: "Tworzenie sekwencji zadań w celu uaktualnienia systemu operacyjnego"
titleSuffix: Configuration Manager
description: "Sekwencje zadań w programie System Center Configuration Manager może automatycznie Uaktualnij system operacyjny z systemu Windows 7 lub nowszym do systemu Windows 10."
ms.custom: na
ms.date: 12/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7591e386-a9ab-4640-8643-332dce5aa006
caps.latest.revision: "12"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 058b0710484a0452ddf19655bf2cabbb43f624ad
ms.sourcegitcommit: 92c3f916e6bbd35b6208463ff406e0247664543a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2018
---
# <a name="create-a-task-sequence-to-upgrade-an-operating-system-in-system-center-configuration-manager"></a>Tworzenie sekwencji zadań w celu uaktualnienia systemu operacyjnego w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Użyj sekwencji zadań w programie Configuration Manager automatycznie uaktualnić system operacyjny na komputerze docelowym. To uaktualnienie może być z systemu Windows 7 lub nowszym do systemu Windows 10, lub z systemu Windows Server 2012 lub nowszym na systemu Windows Server 2016. Tworzenie sekwencji zadań, która odwołuje się do pakietu uaktualnienia systemu operacyjnego oraz wszelkie inne zawartości do aktualizacji, takich jak aplikacje lub oprogramowanie. Sekwencja zadań, aby uaktualnić system operacyjny jest częścią [uaktualnienia systemu Windows do najnowszej wersji](upgrade-windows-to-the-latest-version.md) scenariusza.  

##  <a name="BKMK_UpgradeOS"></a>Tworzenie sekwencji zadań w celu uaktualnienia systemu operacyjnego  
 Aby uaktualnić system operacyjny na komputerach, należy utworzyć sekwencję zadań i wybrać **uaktualnienia systemu operacyjnego za pomocą pakietu uaktualnienia** w kreatorze tworzenia sekwencji zadań. Kreator doda kroki w celu uaktualnienia systemu operacyjnego, zastosować aktualizacje oprogramowania i zainstalować aplikacje. Przed utworzeniem sekwencji zadań, następujące wymagania muszą być spełnione:    

-   **Wymagane**  

     - [Pakiet uaktualnienia systemu operacyjnego](../get-started/manage-operating-system-upgrade-packages.md) muszą być dostępne w konsoli programu Configuration Manager.
     - Podczas uaktualniania do systemu Windows Server 2016, wybierz **Ignoruj wszystkie komunikaty o zgodności dismissable** ustawienie w kroku sekwencji zadań uaktualniania systemu operacyjnego. W przeciwnym razie uaktualnienie zakończy się niepowodzeniem.

-   **Wymagane (jeśli są używane)**  

    -   [Aktualizacje oprogramowania](../../sum/get-started/synchronize-software-updates.md) muszą być zsynchronizowane w konsoli programu Configuration Manager.  

    -   [Aplikacje](../../apps/deploy-use/create-applications.md) muszą zostać dodane do konsoli programu Configuration Manager.  

#### <a name="to-create-a-task-sequence-that-upgrades-an-operating-system"></a>Aby utworzyć sekwencję zadań uaktualniającą system operacyjny  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Sekwencje zadań**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz sekwencję zadań** , aby uruchomić Kreatora tworzenia sekwencji zadań.  

4.  Na **Tworzenie nowej sekwencji zadań** kliknij przycisk **uaktualnienia systemu operacyjnego za pomocą pakietu uaktualnienia**, a następnie kliknij przycisk **dalej**.  

5.  Na stronie **Informacje o sekwencji zadań** określ poniższe ustawienia, a następnie kliknij przycisk **Dalej**.  

    -   **Nazwa sekwencji zadań**: Określ nazwę identyfikującą sekwencję zadań.  

    -   **Opis elementu**: Określ opis zadania wykonywanego przez sekwencję zadań.  

6.  Na **uaktualnienia systemu operacyjnego Windows** , określ następujące ustawienia, a następnie kliknij przycisk **dalej**.  

    -   **Pakiet uaktualnienia**: Określ pakiet uaktualnienia, który zawiera pliki źródłowe uaktualnienia systemu operacyjnego. Można sprawdzić, czy wybrano prawidłowy pakiet uaktualnienia, sprawdzając informacje w **właściwości** okienka. Aby uzyskać więcej informacji, zobacz [Zarządzanie pakietami uaktualnień systemu operacyjnego](../get-started/manage-operating-system-upgrade-packages.md).  

    -   **Indeks wersji**: Jeśli wiele indeksów wersji systemu operacyjnego są dostępne w pakiecie, wybierz odpowiedni indeks wersji. Domyślnie jest zaznaczony pierwszy element.  

    -   **Klucz produktu**: Określ klucz produktu systemu operacyjnego do zainstalowania. Możesz określić zakodowane klucze licencji zbiorczych oraz standardowe klucze produktów. Jeśli używasz klucza produktu algorytmem Base64 każdej grupy 5 znaków muszą być oddzielone kreski (-). Na przykład: *XXXXX-XXXXX-XXXXX-XXXXX-XXXXX*. Jeśli uaktualnienie dotyczy wersji używającej licencji zbiorczej, klucz produktu nie jest wymagany. Wystarczy tylko klucz produktu po uaktualnieniu do wersji detalicznej systemu Windows.  

    -   **Ignoruj wszystkie komunikaty o zgodności dismissable**: Wybierz to ustawienie, jeśli w przypadku uaktualniania do systemu Windows Server 2016. Jeśli to ustawienie nie jest wybrane, sekwencja zadań nie powiedzie się, ponieważ Instalator systemu Windows oczekuje dla użytkownika kliknij **Potwierdź** na oknie dialogowym zgodności aplikacji systemu Windows.   

7.  Na stronie **Dołączanie aktualizacji** określ, czy instalować wymagane aktualizacje oprogramowania lub wszystkie aktualizacje, bądź nie instalować żadnych aktualizacji, a następnie kliknij przycisk **Dalej**. Po wybraniu opcji instalowania aktualizacji oprogramowania programu Configuration Manager zainstaluje tylko aktualizacje oprogramowania przeznaczone dla kolekcji, których członkiem jest komputer docelowy.  

8.  Na stronie **Instalowanie aplikacji** określ aplikacje do zainstalowania na komputerze docelowym, a następnie kliknij przycisk **Dalej**. Jeżeli określisz wiele aplikacji, możesz również wybrać, aby nie przerywać sekwencji zadań w przypadku niepowodzenia instalowania określonej aplikacji.  

9. Ukończ pracę kreatora.  



## <a name="configure-pre-cache-content"></a>Konfigurowanie wstępne wypełnienie pamięci podręcznej
Począwszy od wersji 1702, funkcję pamięci podręcznej przed dostępnych wdrożeń sekwencji zadań zezwala klientom na pobieranie tylko odpowiedniej zawartości, zanim użytkownik instaluje sekwencji zadań.
> [!TIP]  
> Ta funkcja została wprowadzona w wersji 1702 jako [funkcji wersji wstępnej](/sccm/core/servers/manage/pre-release-features). Począwszy od wersji 1706, ta funkcja nie jest już funkcji wersji wstępnej.

Załóżmy na przykład, że chcesz wdrożyć sekwencję zadań uaktualnienia w miejscu systemu Windows 10, tylko pojedynczej sekwencji zadań dla wszystkich użytkowników i mieć wiele architektur i języków. W poprzednich wersjach zawartość uruchamia pobierania, gdy użytkownik instaluje wdrożenie dostępnej sekwencji zadań w programie Software Center. To opóźnienie dodaje dodatkowy czas, zanim będzie gotowy do rozpoczęcia instalacji. Ponadto cała zawartość, do którego odwołuje się sekwencja zadań zostanie pobrana. Ta zawartość zawiera pakiet uaktualniający systemu operacyjnego dla wszystkich języków i architektury. W przypadku każdego pakietu uaktualnienia około trzech GB rozmiar, całkowita zawartość jest bardzo duża.

Wstępne wypełnienie pamięci podręcznej udostępnia opcję, aby umożliwić klientom pobieranie tylko zawartość dotyczy zaraz po otrzymaniu wdrożenia. W związku z tym, kiedy użytkownik kliknie **zainstalować** w programie Software Center zawartości są gotowe, a instalacja uruchamia się szybko, ponieważ zawartość znajduje się na lokalnym dysku twardym.

### <a name="to-configure-the-pre-cache-feature"></a>Aby skonfigurować funkcję wstępne pamięci podręcznej

1. Utwórz pakiety uaktualnień dla określonych architektur i języków systemu operacyjnego. Określ architekturę i język na **źródła danych** pakietu. Dla języka, użyj konwersji dziesiętne (na przykład 1033 jest dziesiętnego dla języka angielskiego i 0x0409 jest odpowiednikiem szesnastkowym). Aby uzyskać więcej informacji, zobacz [tworzenia sekwencji zadań w celu uaktualnienia systemu operacyjnego](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system).

    Wartości architekturę i język zgodne warunki kroki sekwencji zadań w celu ustalenia, czy pakiet uaktualnienia systemu operacyjnego jest wstępnie pamięci podręcznej.
1. Tworzenie sekwencji zadań z warunkowego kroki dla innych języków i architektur. Na przykład następujący krok używa wersji angielskiej:

    ![właściwości przed pamięci podręcznej](../media/precacheproperties2.png)

    ![opcje wstępne pamięci podręcznej](../media/precacheoptions2.png)  

3. Wdróż sekwencję zadań. Dla funkcji wstępne pamięci podręcznej skonfiguruj następujące ustawienia:
    - Na **ogólne** wybierz opcję **wstępnie pobrać zawartość do tej sekwencji zadań**.
    - Na **ustawienia wdrażania** skonfiguruj sekwencji zadań z **dostępne** dla **celu**.
    - Na **Planowanie** karcie dla **Zaplanuj, kiedy to wdrożenie będzie dostępne** ustawienia, wybierz aktualnie zaznaczony czas. Klient uruchamia wstępnie buforowanie zawartości na czas dostępności wdrożenia. Kiedy docelowe klient otrzymuje tych zasad, jest dostępny czas w przeszłości, w związku z tym pobierania wstępnego pamięci podręcznej rozpoczyna się od razu. Jeśli klient odbierze tych zasad, ale czas dostępności jest w przyszłości, klient nie uruchamia wstępnie buforowanie zawartości, dopóki nie wystąpi dostępny czas. 
    - Na **punktów dystrybucji** skonfiguruj **opcje wdrażania** ustawienia. Jeśli zawartość nie jest wstępnie buforowane na kliencie, zanim użytkownik uruchamia proces instalacji, te ustawienia są używane.


### <a name="user-experience"></a>Środowisko użytkownika
- Gdy klient odbierze zasady wdrażania, zostanie ona rozpoczęta wstępnie buforowanie zawartości po czasu dostępności wdrożenia. Treść ta obejmuje wszystkie pakiety z którym związane są odwołania, a ustawiona tylko pakiet uaktualnienia systemu operacyjnego zgodny klienta na podstawie wybranych warunków w sekwencji zadań.
- Gdy wdrożenie jest udostępniane użytkownikom, wyświetlane jest powiadomienie informować użytkowników o nowe wdrożenie, a sekwencja zadań jest widoczna w Centrum oprogramowania. Użytkownik może przejść do Centrum oprogramowania i kliknij przycisk **zainstalować** do rozpoczęcia instalacji.
- Jeśli zawartość nie jest całkowicie wstępnie buforowana kiedy użytkownik instaluje sekwencji zadań, następnie klient korzysta z ustawień określonych na **opcji wdrażania** kartę wdrożenia. 



## <a name="download-package-content-task-sequence-step"></a>Pobierz zawartość pakietu sekwencji zadań  
 [Pobierz zawartość pakietu](../understand/task-sequence-steps.md#BKMK_DownloadPackageContent) krok może służyć przed **Uaktualnij System operacyjny** krok w następujących scenariuszach:  

-   Używasz pojedynczej sekwencji zadań uaktualniania dla zarówno x86 i x64 64. Dodaj dwa **Pobierz zawartość pakietu** czynnościach w ramach **przygotować do uaktualnienia** grupy. Ustaw warunki na każdym kroku w celu wykrywania architektury klienta. Z tego powodu krok w celu pobrania tylko odpowiedniego pakietu uaktualnienia systemu operacyjnego. Skonfiguruj tę samą zmienną dla każdego kroku **Pobierz zawartość pakietu** i użyj zmiennej ścieżki nośnika w kroku **Uaktualnij system operacyjny**.  

-   Aby odpowiedni pakiet sterowników był pobierany dynamicznie, użyj dwóch kroków **Pobierz zawartość pakietu** z warunkami wykrywania odpowiedniego typu sprzętu dla każdego pakietu sterowników. Skonfiguruj każdy **Pobierz zawartość pakietu** krok, aby użyć tej samej zmiennej. Następnie użyć tej zmiennej do **zawartość przejściowa** wartości w sekcji sterowników na **Uaktualnij System operacyjny** kroku.  

   > [!NOTE]
   > W przypadku więcej niż jeden pakiet programu Configuration Manager dodaje sufiks numeryczny do nazwy zmiennej. Na przykład jeśli określisz zmienną % mojazawartosc % jako zmienną niestandardową, ta lokalizacja jest, gdzie klient przechowuje wszystkie przywoływanej zawartości. Odwołań do zmiennych w kolejnym kroku, takie jak **Uaktualnij System operacyjny**, użyj zmiennej z sufiksem numerycznym. W tym przykładzie, mojazawartosc01% lub % mojazawartosc02%, gdzie numer odpowiada w kolejności **Pobierz zawartość pakietu** kroku przedstawiono tej określonej zawartości.

## <a name="optional-post-processing-task-sequence-steps"></a>Opcjonalne kroki przetwarzania końcowego sekwencji zadań  
 Po utworzeniu sekwencji zadań, należy dodać kolejne kroki w razie potrzeby. Na przykład do odinstalowania aplikacji ze znanymi problemami dotyczącymi zgodności lub dodać akcje przetwarzania końcowego uruchamiane po ponownym uruchomieniu komputera i uaktualnienia do systemu Windows 10 zakończy się pomyślnie. Dodaj te dodatkowe kroki w grupy przetwarzanie końcowe sekwencji zadań.  

> [!NOTE]  
>  Ponieważ ta sekwencja zadań nie jest liniowa, istnieją warunki dotyczące kroków, które mogą wpłynąć na wyniki sekwencji zadań, w zależności od tego, czy pomyślnie uaktualni ona komputer kliencki, czy też będzie konieczne przywrócenie komputera klienta do wersji systemu operacyjnego z.  

## <a name="optional-rollback-task-sequence-steps"></a>Kroki opcjonalne wycofywania sekwencji zadań  
 W przypadku wystąpienia problemów z procesem uaktualnienia po ponownym uruchomieniu komputera, Instalator systemu Windows będzie wycofać uaktualnienie do poprzedniego systemu operacyjnego. Sekwencja zadań zostanie następnie kontynuować wykonywanie kolejnych kroków, w grupie wycofywanie. Po utworzeniu sekwencji zadań, można dodać opcjonalne kroki do grupy wycofywanie.  

## <a name="folder-and-files-removed-after-computer-restart"></a>Uruchom ponownie folder i pliki zostały usunięte po komputera  
 Po zakończeniu sekwencji zadań klienta nie powoduje usunięcia skryptów wycofywania i przetwarzania po ponownym uruchomieniu komputera. Te pliki skryptów nie zawierają informacji poufnych.  
