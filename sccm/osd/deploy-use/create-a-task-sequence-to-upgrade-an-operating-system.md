---
title: Tworzenie sekwencji zadań uaktualniania systemu operacyjnego
titleSuffix: Configuration Manager
description: Za pomocą sekwencji zadań do automatycznego uaktualniania z systemu Windows 7 lub nowszym do systemu Windows 10
ms.date: 04/10/2018
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: 7591e386-a9ab-4640-8643-332dce5aa006
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: d35a5ea3ebde6ce6ab0934832180223c2a634541
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="create-a-task-sequence-to-upgrade-an-operating-system-in-system-center-configuration-manager"></a>Tworzenie sekwencji zadań w celu uaktualnienia systemu operacyjnego w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Użyj sekwencji zadań w programie Configuration Manager automatycznie uaktualnić system operacyjny na komputerze docelowym. To uaktualnienie może być z systemu Windows 7 lub nowszym do systemu Windows 10, lub z systemu Windows Server 2012 lub nowszym na systemu Windows Server 2016. Tworzenie sekwencji zadań, która odwołuje się do pakietu uaktualnienia systemu operacyjnego oraz wszelkie inne zawartości do aktualizacji, takich jak aplikacje lub oprogramowanie. Sekwencja zadań, aby uaktualnić system operacyjny jest częścią [uaktualnienia systemu Windows do najnowszej wersji](upgrade-windows-to-the-latest-version.md) scenariusza.  



##  <a name="BKMK_UpgradeOS"></a> Tworzenie sekwencji zadań w celu uaktualnienia systemu operacyjnego  
 Aby uaktualnić system operacyjny na komputerach, należy utworzyć sekwencję zadań i wybrać **uaktualnienia systemu operacyjnego za pomocą pakietu uaktualnienia** w kreatorze tworzenia sekwencji zadań. Kreator doda kroki sekwencji zadań uaktualniania systemu operacyjnego, zastosować aktualizacje oprogramowania i instalowanie aplikacji. Przed utworzeniem sekwencji zadań, następujące wymagania muszą być spełnione:    

-   **Wymagane**  

     - [Pakiet uaktualnienia systemu operacyjnego](../get-started/manage-operating-system-upgrade-packages.md) muszą być dostępne w konsoli programu Configuration Manager.
     - Podczas uaktualniania do systemu Windows Server 2016, wybierz **Ignoruj wszystkie komunikaty o zgodności dismissable** ustawienie w kroku sekwencji zadań uaktualniania systemu operacyjnego. W przeciwnym razie nieudanego uaktualnienia.

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

7.  Na **obejmują aktualizacje** Określ, czy wymagane do zainstalowania aktualizacji oprogramowania wszystkie lub nie. Następnie kliknij przycisk **Dalej**. Po wybraniu opcji instalowania aktualizacji oprogramowania programu Configuration Manager zainstaluje tylko aktualizacje oprogramowania przeznaczone dla kolekcji, których członkiem jest komputer docelowy.  

8.  Na stronie **Instalowanie aplikacji** określ aplikacje do zainstalowania na komputerze docelowym, a następnie kliknij przycisk **Dalej**. Jeżeli określisz wiele aplikacji, możesz również wybrać, aby nie przerywać sekwencji zadań w przypadku niepowodzenia instalowania określonej aplikacji.  

9. Ukończ pracę kreatora.  


 > [!Important] 
 > Po zakończeniu sekwencji zadań klienta nie powoduje usunięcia skryptów wycofywania i przetwarzania po ponownym uruchomieniu komputera. Te pliki skryptów nie zawierają informacji poufnych.  


 > [!Note]
 > Począwszy od wersji 1802 domyślny szablon sekwencji zadań dla uaktualnienia w miejscu systemu Windows 10 obejmują dodatkowe grupy zalecanych czynności można dodać przed i po proces uaktualniania. Te akcje są wspólne dla wielu klientów, którzy pomyślnie uaktualniania urządzeń do systemu Windows 10. Aby uzyskać więcej informacji, zobacz kroki sekwencji zadań zalecane [przygotować do uaktualnienia](#recommended-task-sequence-steps-to-prepare-for-upgrade) i [dla przetwarzania końcowego](#recommended-task-sequence-steps-for-post-processing).



## <a name="configure-pre-cache-content"></a>Konfigurowanie wstępne wypełnienie pamięci podręcznej
<!--1021244-->
Funkcja wstępne pamięci podręcznej dla wdrożeń dostępnych sekwencji zadań umożliwia klientom pobieranie odpowiedniej zawartości pakietu uaktualnienia systemu operacyjnego, zanim użytkownik instaluje sekwencji zadań.  

> [!TIP]  
> Ta funkcja została wprowadzona w wersji 1702 jako [funkcji wersji wstępnej](/sccm/core/servers/manage/pre-release-features). Począwszy od wersji 1706, ta funkcja nie jest już funkcji wersji wstępnej.  


> [!Note]  
> Ta funkcja opcjonalna nie włączyć domyślne programu Configuration Manager. Należy włączyć tę funkcję, przed jego użyciem. Aby uzyskać więcej informacji, zobacz [Włącz funkcje opcjonalne aktualizacji](/sccm/core/servers/manage/install-in-console-updates#bkmk_options).<!--505213-->  


Na przykład można tylko sekwencja pojedyncze zadanie uaktualniania w miejscu dla wszystkich użytkowników i wielu architektur i języków. W poprzednich wersjach zawartość uruchamia pobierania, gdy użytkownik instaluje wdrożenie dostępnej sekwencji zadań w programie Software Center. To opóźnienie dodaje dodatkowy czas, zanim będzie gotowy do rozpoczęcia instalacji. Cała zawartość, do którego odwołuje się sekwencja zadań zostanie pobrana. Ta zawartość zawiera pakiet uaktualniający systemu operacyjnego dla wszystkich języków i architektury. W przypadku każdego pakietu uaktualnienia około trzech GB rozmiar, całkowita zawartość jest bardzo duża.

Zapewnia zawartości pamięci podręcznej przed opcję, aby umożliwić klientom pobieranie tylko odpowiednie systemu operacyjnego uaktualniania pakietu, a także wszystkie inne przywoływanej zawartości zaraz po otrzymaniu wdrożenia. Po kliknięciu przez użytkownika **zainstalować** w programie Software Center zawartości są gotowe, a instalacja uruchamia się szybko, ponieważ zawartość znajduje się na lokalnym dysku twardym.

 > [!NOTE]
 > To zachowanie aktualnie ma zastosowanie tylko do pakietu uaktualnienia systemu operacyjnego. Ten pakiet jest tylko zawartość, na której można określić zgodnej architektury ani języka. Na przykład jeśli sekwencja zadań odwołuje się również wiele pakietów sterowników, klient aktualnie pobiera je wszystkie. Aparat sekwencji zadań oblicza warunki dotyczące kroków, po uruchomieniu sekwencji zadań, a nie w wyprzedzeniem. Klient używa znaczniki we właściwościach pakietu można ustalić, które zawartości do wstępnie pamięci podręcznej.

### <a name="to-configure-the-pre-cache-feature"></a>Aby skonfigurować funkcję wstępne pamięci podręcznej

1. Utwórz pakiety uaktualnienia systemu operacyjnego dla określonych architektur i języków. Określ architekturę i język na **źródła danych** pakietu. Dla języka Użyj dziesiętną konwersji. Na przykład 1033 jest wartość dziesiętna w języku angielskim i 0x0409 jest odpowiednikiem szesnastkową.

    Klient oceni wartości architekturę i język, aby ustalić, które pakiet, który pobiera podczas wstępnego buforowanie uaktualnienia systemu operacyjnego.

1. Tworzenie sekwencji zadań z warunkowego kroki dla innych języków i architektur. Na przykład następujący krok używa wersji angielskiej:

    ![Wyświetlanie wielu kroków uaktualnienia systemu operacyjnego ENU, DEU i JPN edytora sekwencji zadań](../media/precacheproperties2.png)

    ![Edytor sekwencji zadań, karta Opcje wyświetlania kwerend WQL usługi WMI dla ustawień regionalnych i OSArchitecture](../media/precacheoptions2.png)  

3. Wdróż sekwencję zadań. Dla funkcji wstępne pamięci podręcznej skonfiguruj następujące ustawienia:
    - Na **ogólne** wybierz opcję **wstępnie pobrać zawartość do tej sekwencji zadań**.
    - Na **ustawienia wdrażania** skonfiguruj sekwencji zadań z **dostępne** dla **celu**.
    - Na **Planowanie** karcie dla **Zaplanuj, kiedy to wdrożenie będzie dostępne** ustawienia, wybierz aktualnie zaznaczony czas. Klient uruchamia wstępnie buforowanie zawartości na czas dostępności wdrożenia. Kiedy docelowe klient otrzymuje tych zasad, jest dostępny czas w przeszłości, w związku z tym pobierania wstępnego pamięci podręcznej rozpoczyna się od razu. Jeśli klient odbierze tych zasad, ale czas dostępności jest w przyszłości, klient nie uruchamia wstępnie buforowanie zawartości, dopóki nie wystąpi dostępny czas. 
    - Na **punktów dystrybucji** skonfiguruj **opcje wdrażania** ustawienia. Jeśli zawartość nie jest buforowana wstępnie zanim użytkownik uruchamia proces instalacji, klient korzysta z tych ustawień.
  

### <a name="user-experience"></a>Środowisko użytkownika
- Gdy klient odbierze zasady wdrażania, rozpoczyna się wstępnie buforowanie zawartości po czasu dostępności wdrożenia. Ta zawartość obejmuje pakiety wszystkich przywoływanych, ale tylko odpowiadający architekturę i język atrybutów w pakiecie uaktualniania pakietu systemu operacyjnego.
- Gdy klient wysyła wdrażania dostępne dla użytkowników, informować użytkowników o nowe wdrożenie wyświetlane jest powiadomienie. Teraz sekwencja zadań jest widoczna w Centrum oprogramowania. Użytkownik może przejść do Centrum oprogramowania i kliknij przycisk **zainstalować** do rozpoczęcia instalacji.
- Jeśli zawartość nie jest całkowicie wstępnie buforowana kiedy użytkownik instaluje sekwencji zadań, następnie klient korzysta z ustawień określonych na **opcji wdrażania** kartę wdrożenia. 



## <a name="recommended-task-sequence-steps-to-prepare-for-upgrade"></a>Kroki sekwencji zadań zalecane, aby przygotować do uaktualnienia

Począwszy od wersji 1802 domyślny szablon sekwencji zadań dla uaktualnienia w miejscu systemu Windows 10 obejmują dodatkowe grupy zalecanych czynności można dodać przed procesu uaktualniania. Te akcje w **przygotować do uaktualnienia** grupy są wspólne dla wielu klientów, którzy pomyślnie uaktualniania urządzeń do systemu Windows 10. W przypadku lokacji w wersjach wcześniejszych niż 1802 ręcznie dodać tych działań do sekwencji zadań w **przygotować do uaktualnienia** grupy.
- **Sprawdza baterii**: Dodaj kroki do tej grupy, aby sprawdzić, czy komputer używa baterii lub przewodowej zasilania. Ta akcja wymaga niestandardowego skryptu lub narzędzia do wykonania tego sprawdzenia.
- **Sieci/przewodowe połączenie kontroli**: Dodaj kroki do tej grupy, aby sprawdzić, czy komputer jest połączony z siecią, a nie korzysta z połączenia bezprzewodowego. Ta akcja wymaga niestandardowego skryptu lub narzędzia do wykonania tego sprawdzenia.
- **Usunięcia niezgodnych aplikacji**: Dodaj kroki do tej grupy, aby usunąć wszystkie aplikacje, które są niezgodne z tą wersją systemu Windows 10. Metoda do odinstalowania aplikacji może być różna. Jeśli aplikacja używa Instalatora Windows, skopiuj **program dezinstalacyjny** wiersz polecenia z **programy** karcie we właściwościach typu wdrażania aplikacji Instalatora Windows. Następnie dodaj **Uruchom wiersz polecenia** krok w tej grupie przy użyciu wiersza polecenia Odinstaluj program. Na przykład: </br>`msiexec /x {150031D8-1234-4BA8-9F52-D6E5190D1CBA} /q`</br> 
- **Usuń niezgodnych sterowników**: Dodaj kroki do tej grupy, aby usunąć wszystkie sterowniki, które nie są zgodne z tą wersją systemu Windows 10.
- **Usuń/zawiesić zabezpieczeń innych firm**: Dodaj kroki do tej grupy, usunięcia lub zawiesić programów zabezpieczeń innych firm, takich jak oprogramowanie antywirusowe.
   - Jeśli używasz programu szyfrowania dysku innych firm, podaj jej szyfrowania sterownika w Instalatorze systemu Windows z **/ReflectDrivers** [opcji wiersza polecenia](/windows-hardware/manufacture/desktop/windows-setup-command-line-options). Dodaj [Ustaw zmienną sekwencji zadań](/sccm/osd/understand/task-sequence-steps#BKMK_SetTaskSequenceVariable) krok do sekwencji zadań w tej grupie. Ustaw zmienną sekwencji zadań **OSDSetupAdditionalUpgradeOptions**. Ustaw wartość na **/ReflectDriver** ze ścieżką do sterownika. To [zmiennej akcji sekwencji zadań](/sccm/osd/understand/task-sequence-action-variables#upgrade-operating-system) dołącza wiersza polecenia Instalatora systemu Windows używane przez sekwencję zadań. Wszelkie dodatkowe wskazówki dotyczące tego procesu, skontaktuj się z dostawcą oprogramowania.

### <a name="download-package-content-task-sequence-step"></a>Pobierz zawartość pakietu sekwencji zadań  
 [Pobierz zawartość pakietu](../understand/task-sequence-steps.md#BKMK_DownloadPackageContent) krok może służyć przed **Uaktualnij System operacyjny** krok w następujących scenariuszach:  

-   Używasz pojedynczej sekwencji zadań uaktualniania dla zarówno x86 i x64 64. Dodaj dwa **Pobierz zawartość pakietu** czynnościach w ramach **przygotować do uaktualnienia** grupy. Ustaw warunki na każdym kroku w celu wykrywania architektury klienta. Z tego powodu krok w celu pobrania tylko odpowiedniego pakietu uaktualnienia systemu operacyjnego. Skonfiguruj tę samą zmienną dla każdego kroku **Pobierz zawartość pakietu** i użyj zmiennej ścieżki nośnika w kroku **Uaktualnij system operacyjny**.  

-   Aby odpowiedni pakiet sterowników był pobierany dynamicznie, użyj dwóch kroków **Pobierz zawartość pakietu** z warunkami wykrywania odpowiedniego typu sprzętu dla każdego pakietu sterowników. Skonfiguruj każdy **Pobierz zawartość pakietu** krok, aby użyć tej samej zmiennej. Następnie użyć tej zmiennej do **zawartość przejściowa** wartości w sekcji sterowników na **Uaktualnij System operacyjny** kroku.  

   > [!NOTE]
   > W przypadku więcej niż jeden pakiet programu Configuration Manager dodaje sufiks numeryczny do nazwy zmiennej. Na przykład jeśli określisz zmienną % mojazawartosc % jako zmienną niestandardową, ta lokalizacja jest, gdzie klient przechowuje wszystkie przywoływanej zawartości. Odwołań do zmiennych w kolejnym kroku, takie jak **Uaktualnij System operacyjny**, użyj zmiennej z sufiksem numerycznym. W tym przykładzie, mojazawartosc01% lub % mojazawartosc02%, gdzie numer odpowiada w kolejności **Pobierz zawartość pakietu** kroku przedstawiono tej określonej zawartości.



## <a name="recommended-task-sequence-steps-for-post-processing"></a>Kroki sekwencji zadań zalecane dla przetwarzania końcowego   
 Po utworzeniu sekwencji zadań, należy dodać kolejne kroki w **przetwarzania końcowego** grupy sekwencji zadań.  

> [!NOTE]  
>  Ta sekwencja zadań nie jest liniowa. Istnieją warunki dotyczące kroków, które mogą wpłynąć na wyniki sekwencji zadań. To zachowanie zależy, czy pomyślnie uaktualni ona komputer kliencki, czy będzie konieczne przywrócenie komputera klienta oryginalnym systemie operacyjnym.  

Począwszy od wersji 1802 domyślny szablon sekwencji zadań dla uaktualnienia w miejscu systemu Windows 10 obejmują dodatkowe grupy zalecanych czynności można dodać po zakończeniu uaktualniania. Te akcje w **przetwarzania końcowego** grupy są wspólne dla wielu klientów, którzy pomyślnie uaktualniania urządzeń do systemu Windows 10. W przypadku lokacji w wersjach wcześniejszych niż 1802 ręcznie dodać tych działań do sekwencji zadań w **przetwarzania końcowego** grupy.
- **Zastosuj sterowniki instalacją**: Dodaj kroki do tej grupy, aby zainstalować sterowniki oparte na Instalatora (.exe) z pakietów.
- **Instalacja/enable zabezpieczeń innych firm**: Dodaj kroki do tej grupy, aby zainstalować lub włączyć programów zabezpieczeń innych firm, takich jak oprogramowanie antywirusowe. 
- **Ustaw aplikacji domyślne systemu Windows i skojarzenia**: Dodaj kroki opisane w tej grupie można ustawić aplikacji domyślne systemu Windows i skojarzeń plików. Najpierw przygotować komputer odniesienia z sieci skojarzenia żądanej aplikacji. Następnie uruchom następujące polecenie, aby wyeksportować: </br>`dism /online /Export-DefaultAppAssociations:"%UserProfile%\Desktop\DefaultAppAssociations.xml"`</br>Dodaj plik XML do pakietu. Następnie dodaj [Uruchom wiersz polecenia](/sccm/osd/understand/task-sequence-steps#BKMK_RunCommandLine) krok w tej grupie. Określ pakiet, który zawiera plik XML, a następnie wprowadzić następujący wiersz polecenia: </br>`dism /online /Import-DefaultAppAssociations:DefaultAppAssocations.xml`</br> Aby uzyskać więcej informacji, zobacz [eksportu lub importu domyślna skojarzenia aplikacji](/windows-hardware/manufacture/desktop/export-or-import-default-application-associations).
- **Zastosowanie dostosowań i personalizacji**: Dodaj kroki do tej grupy do stosowania dostosowania menu Start, takie jak organizowanie grup programu. Aby uzyskać więcej informacji, zobacz [dostosowywanie ekranu startowego](/windows-hardware/manufacture/desktop/customize-the-start-screen).



## <a name="optional-task-sequence-steps-for-rollback"></a>Kroki sekwencji zadań opcjonalne na potrzeby wycofywania  
 W przypadku wystąpienia problemów z procesem uaktualnienia po ponownym uruchomieniu komputera, Instalator systemu Windows będzie wycofać uaktualnienie do poprzedniego systemu operacyjnego. Kontynuuje wykonywanie kolejnych kroków w sekwencji zadań **wycofywania** grupy. Po utworzeniu sekwencji zadań, można dodać opcjonalne kroki w grupie wycofywanie. Na przykład wycofać zmiany wprowadzone do systemu w ramach sekcji przygotowanie do uaktualnienia grupy, na przykład odinstalowanie oprogramowania niezgodne.



## <a name="additional-recommendations"></a>Zalecenia dodatkowe
- Przejrzyj dokumentację systemu Windows [błędy uaktualniania rozwiązać systemu Windows 10](/windows/deployment/upgrade/resolve-windows-10-upgrade-errors). Ten artykuł zawiera także szczegółowe informacje na temat procesu uaktualniania.
- Domyślny **Sprawdź gotowość** kroku, należy włączyć funkcję **zapewnić minimalną ilość wolnego miejsca (MB)**. Ustaw wartość na co najmniej **16384** (16 GB) dla 32-bitowego systemu operacyjnego pakietu, uaktualnienia lub **20480** (20 GB) dla wersji 64-bitowych. 
- Użyj **SMSTSDownloadRetryCount** [wbudowanej zmiennej sekwencji zadań](/sccm/osd/understand/task-sequence-built-in-variables) do pobierania zasady ponawiania. Obecnie domyślnie klient ponawia próbę dwukrotnie; Ta zmienna jest ustawiona dwóch (2). Jeśli klienci nie są na połączenie z firmową siecią przewodową, dodatkowych ponownych prób pomocy Uzyskaj zasady klienta. Za pomocą tej zmiennej powoduje, że nie negatywny wpływ po stronie niż błąd opóźnionego Jeśli nie można pobrać zasad.<!-- 501016 --> Również zwiększyć **SMSTSDownloadRetryDelay** zmiennej z domyślnej 15 sekund.
- Przeprowadzenie oceny zgodności wbudowanego. 
   - Dodaj drugi **Uaktualnij System operacyjny** krok wczesne **przygotować do uaktualnienia** grupy. Nadaj mu nazwę *oceny uaktualnienia*. Określ tego samego pakietu uaktualnienia, a następnie włącz opcję **skanowanie zgodności wykonywania Instalatora Windows bez rozpoczynania uaktualniania**. Włącz **Kontynuuj przy błędzie** na karcie Opcje. 
   - Natychmiast po tym *oceny uaktualnienia* kroku, należy dodać **Uruchom wiersz polecenia** kroku. Określ następujący wiersz polecenia:</br> `cmd /c exit %_SMSTSOSUpgradeActionReturnCode%`</br>Na **opcje** , Dodaj następujący warunek: </br>`Task Sequence Variable _SMSTSOSUpgradeActionReturnCode not equals 3247440400` </br>Tego kodu powrotnego jest wartość dziesiętną MOSETUP_E_COMPAT_SCANONLY (0xC1900210), czyli skanowania zgodności pomyślnie bez żadnych problemów. Jeśli *ocena uaktualnienia* krok zakończy się pomyślnie i zwraca ten kod, ten krok zostanie pominięty. W przeciwnym razie jeśli etap oceny zwraca innych kod powrotny, ten krok zakończy się niepowodzeniem sekwencji zadań z kodem powrotu z skanowanie zgodności Instalatora systemu Windows.
   - Aby uzyskać więcej informacji, zobacz [Uaktualnij system operacyjny](/sccm/osd/understand/task-sequence-steps#BKMK_UpgradeOS).
- Jeśli chcesz zmienić urządzenia z systemem BIOS do UEFI podczas tej sekwencji zadań, zobacz [Konwertowanie systemu BIOS na UEFI podczas uaktualniania w miejscu](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#convert-from-bios-to-uefi-during-an-in-place-upgrade).
