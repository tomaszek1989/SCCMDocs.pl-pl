---
title: "Tworzenie sekwencji zadań w celu uaktualnienia systemu operacyjnego | Dokumentacja firmy Microsoft"
description: "Sekwencje zadań w programie System Center Configuration Manager automatycznie uaktualnić system operacyjny z systemu Windows 7 lub nowszej, aby system Windows 10."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7591e386-a9ab-4640-8643-332dce5aa006
caps.latest.revision: 12
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d7b13f3dea5a3ae413ca6b8150ec24e1632a4d4d
ms.openlocfilehash: e63b639836bc38a030a051e80db4b057ab75a0b0
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="create-a-task-sequence-to-upgrade-an-operating-system-in-system-center-configuration-manager"></a>Tworzenie sekwencji zadań w celu uaktualnienia systemu operacyjnego w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Za pomocą sekwencji zadań w programie System Center Configuration Manager automatycznie uaktualnić system operacyjny Windows 7 lub nowszej, aby 10 systemu Windows na komputerze docelowym. Tworzenie sekwencji zadań, która odwołuje się do obrazu systemu operacyjnego, który ma zostać zainstalowany na komputerze docelowym i innej dodatkowej zawartości, jak aplikacje i aktualizacje oprogramowania, które chcesz zainstalować. Sekwencja zadań, aby uaktualnić system operacyjny jest częścią [Windows uaktualnienia do najnowszej wersji](upgrade-windows-to-the-latest-version.md) scenariusza.  

##  <a name="BKMK_UpgradeOS"></a>Tworzenie sekwencji zadań w celu uaktualnienia systemu operacyjnego  
 Do uaktualnienia systemu operacyjnego na komputerach z systemem Windows 10, należy utworzyć sekwencję zadań i wybierz **uaktualnienie pakietu uaktualnienia systemu operacyjnego** w kreatorze tworzenia sekwencji zadań. Kreator doda kroki, aby uaktualnić system operacyjny, stosowanie aktualizacji oprogramowania i instalować aplikacje. Przed utworzeniem sekwencji zadań musi być następujące w miejscu:  

-   **Wymagane**  

     - System Windows 10 [pakiet uaktualnienia systemu operacyjnego](../get-started/manage-operating-system-upgrade-packages.md) muszą być dostępne w konsoli programu Configuration Manager.  

-   **Wymagane (jeśli są używane)**  

    -   [Aktualizacje oprogramowania](../../sum/get-started/synchronize-software-updates.md) musi być synchronizowane w konsoli programu Configuration Manager.  

    -   [Aplikacje](../../apps/deploy-use/create-applications.md) muszą zostać dodane do konsoli programu Configuration Manager.  

#### <a name="to-create-a-task-sequence-that-upgrades-an-operating-system"></a>Aby utworzyć sekwencję zadań, która uaktualnienia systemu operacyjnego  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij przycisk **Sekwencje zadań**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz sekwencję zadań** , aby uruchomić Kreatora tworzenia sekwencji zadań.  

4.  Na **Tworzenie nowej sekwencji zadań** kliknij **uaktualnienie pakietu uaktualnienia systemu operacyjnego**, a następnie kliknij przycisk **dalej**.  

5.  Na stronie **Informacje o sekwencji zadań** określ poniższe ustawienia, a następnie kliknij przycisk **Dalej**.  

    -   **Nazwa sekwencji zadań**: Określ nazwę identyfikującą sekwencję zadań.  

    -   **Opis**: Określ opis zadania wykonywanego przez sekwencję zadań.  

6.  Na **uaktualnienia systemu operacyjnego Windows** , określ następujące ustawienia, a następnie kliknij przycisk **dalej**.  

    -   **Pakiet uaktualnienia**: Określ pakiet uaktualniający, który zawiera pliki źródłowe uaktualnienia systemu operacyjnego. Można sprawdzić, czy wybrano poprawny pakiet uaktualniający, przeglądając informacje w **właściwości** okienka. Aby uzyskać więcej informacji, zobacz [Zarządzanie pakietami uaktualnienia systemu operacyjnego](../get-started/manage-operating-system-upgrade-packages.md).  

    -   **Indeks wersji**: Jeśli wiele indeksów wersji systemu operacyjnego są dostępne w pakiecie, wybierz indeks żądaną wersji. Pierwszy element jest domyślnie zaznaczone.  

    -   **Klucz produktu**: Określ klucz produktu dla systemu operacyjnego do zainstalowania. Możesz określić zakodowane klucze licencji zbiorczych oraz standardowe klucze produktów. W przypadku użycia niezakodowanego klucza produktu poszczególne grupy 5 znaków muszą być oddzielone kreskami (-). Na przykład: *XXXXX-XXXXX-XXXXX-XXXXX-XXXXX*. W przypadku uaktualniania Edition licencji woluminu, klucz produktu nie jest wymagane. Wystarczy tylko klucz produktu po uaktualnieniu do wersji handlowej systemu Windows.  

7.  Na stronie **Dołączanie aktualizacji** określ, czy instalować wymagane aktualizacje oprogramowania lub wszystkie aktualizacje, bądź nie instalować żadnych aktualizacji, a następnie kliknij przycisk **Dalej**. Po wybraniu opcji instalowania aktualizacji oprogramowania programu Configuration Manager instaluje tylko aktualizacje oprogramowania przeznaczone do kolekcji, których członkiem jest komputer docelowy.  

8.  Na stronie **Instalowanie aplikacji** określ aplikacje do zainstalowania na komputerze docelowym, a następnie kliknij przycisk **Dalej**. Jeżeli określisz wiele aplikacji, możesz również wybrać, aby nie przerywać sekwencji zadań w przypadku niepowodzenia instalowania określonej aplikacji.  

9. Ukończ pracę kreatora.  



## <a name="configure-pre-cache-content"></a>Konfigurowanie wstępne buforowania zawartości
Począwszy od wersji 1702, w przypadku wdrożeń dostępnych sekwencji zadań, można użyć funkcji wstępne pamięci podręcznej klienci Pobierz tylko odpowiednich treści, zanim użytkownik instaluje zawartość.
> [!TIP]  
> Wprowadzona w wersji 1702, wstępne pamięci podręcznej jest funkcją wersji wstępnej. Aby ją włączyć, zobacz [używać funkcji wersji wstępnej z aktualizacji](/sccm/core/servers/manage/pre-release-features).

Na przykład załóżmy, że chcesz wdrożyć sekwencję zadań uaktualnienia w miejscu systemu Windows 10, tylko pojedynczą sekwencję zadań dla wszystkich użytkowników i mieć wiele architektury i języków. Przed wersją 1702, jeśli tworzysz dostępne wdrożenie, a użytkownik kliknie **zainstalować** w programie Software Center pobranie zawartości w tym czasie. Spowoduje to dodanie dodatkowych sprzed instalacji jest gotowy do uruchomienia. Ponadto cała zawartość, do którego odwołuje się sekwencja zadań zostanie pobrana. W tym pakiet uaktualnienia systemu operacyjnego dla wszystkich języków i architektury. W przypadku każdego około 3 GB rozmiar, może być dość duży pakiet do pobrania.

Wstępne buforowania zawartości zawiera opcję, aby umożliwić klientowi tylko pobierania zawartości odpowiednich zaraz po otrzymaniu wdrożenia. W związku z tym, kiedy użytkownik kliknie przycisk **zainstalować** w Centrum oprogramowania, zawartość jest gotowa i instalacji uruchamia się szybko, ponieważ zawartość znajduje się na lokalnym dysku twardym.

### <a name="to-configure-the-pre-cache-feature"></a>Aby skonfigurować funkcję wstępne pamięci podręcznej

1. Utwórz pakiety uaktualnienia języków i określonej architektury systemu operacyjnego. Określ architekturę i języka na **źródła danych** pakietu. Dla języka, użyj decimal konwersji (na przykład 1033 jest dziesiętnych dla języka angielskiego i 0x0409 jest odpowiednikiem szesnastkowej). Aby uzyskać szczegółowe informacje, zobacz [tworzenia sekwencji zadań w celu uaktualnienia systemu operacyjnego](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system).

    Architektura i języka wartości są używane do spełniają warunki kroku sekwencji zadań, tworzonych w następnym kroku w celu ustalenia, czy pakiet uaktualnienia systemu operacyjnego mają być buforowane wstępnie.
2. Tworzenie sekwencji zadań kroki warunkowego dla różnych języków i architektury. Na przykład dla angielskiej wersji można utworzyć krok zbliżoną do następującej:

    ![właściwości wstępne pamięci podręcznej](../media/precacheproperties2.png)

    ![Opcje pamięci podręcznej wstępnego](../media/precacheoptions2.png)  

3. Wdrożenie sekwencji zadań. Dla funkcji wstępne pamięci podręcznej skonfiguruj następujące ustawienia:
    - Na **ogólne** zaznacz **wstępnie pobierania zawartości dla tej sekwencji zadań**.
    - Na **ustawienia wdrażania** skonfiguruj sekwencję zadań z **dostępne** dla **celu**. W przypadku utworzenia **wymagane** wdrożenia, funkcje wstępne pamięci podręcznej nie będą działać.
    - Na **Planowanie** kartę, dla **Zaplanuj, kiedy to wdrożenie będą dostępne** ustawienie, wybierz odpowiedni czas w przyszłości zapewnia klientom wystarczająco dużo czasu na wstępnie buforowanie zawartości przed udostępnieniem wdrożenia dla użytkowników. Na przykład można ustawić czas dostępności do 3 godzin w przyszłości, aby umożliwić wystarczająco dużo czasu na wstępnie buforowaną zawartości.  
    - Na **punktów dystrybucji** skonfiguruj **opcje wdrażania** ustawienia. Jeśli zawartość nie jest wstępnie buforowana na komputerze klienckim, zanim użytkownik uruchamia proces instalacji, te ustawienia są używane.


### <a name="user-experience"></a>Środowisko użytkownika
- Gdy klient odbierze zasady wdrażania, rozpocznie się wstępnie buforowania zawartości. Obejmuje całą zawartość odwołania (wszystkie inne typy pakietów) oraz tylko pakiet uaktualnienia systemu operacyjnego zgodnym klienta na podstawie warunków ustawienie w sekwencji zadań.
- Podczas wdrażania zostanie udostępniona użytkownikom (ustawienie na **Planowanie** kartę wdrożenia), wyświetla powiadomienia informują użytkowników o nowego wdrożenia i wdrożenie stanie się widoczna w Centrum oprogramowania. Użytkownik może przejść do Centrum oprogramowania i kliknij przycisk **zainstalować** aby rozpocząć instalację.
- Jeśli zawartość nie jest w pełni wstępnie pamięci podręcznej, a następnie go użyje ustawień określonych w **opcji wdrożenia** kartę wdrożenia. Zaleca się, że jest wystarczająco dużo czasu między po utworzeniu wdrożenia i czasu, w którym wdrożenie staje się dostępny dla użytkowników, aby umożliwić klientom wystarczająco dużo czasu na wstępnie buforowanie zawartości.



## <a name="download-package-content-task-sequence-step"></a>Pobierz pakiet zawartości sekwencji zadań  
 [Pobierz zawartość pakietu](../understand/task-sequence-steps.md#BKMK_DownloadPackageContent) krok może służyć przed **uaktualnienia systemu operacyjnego** krok w następujących scenariuszach:  

-   W przypadku użycia sekwencji pojedyncze zadanie uaktualniania współpracującym z platform zarówno x86, jak i x64. W tym celu dodaj dwa kroki zadania **Pobierz zawartość pakietu** w grupie **Przygotowanie do uaktualnienia** z warunkami wykrywania architektury klienta i pobrania tylko odpowiedniego pakietu uaktualnienia systemu operacyjnego. Skonfiguruj tę samą zmienną dla każdego kroku **Pobierz zawartość pakietu** i użyj zmiennej ścieżki nośnika w kroku **Uaktualnij system operacyjny**.  

-   Aby odpowiedni pakiet sterowników był pobierany dynamicznie, użyj dwóch kroków **Pobierz zawartość pakietu** z warunkami wykrywania odpowiedniego typu sprzętu dla każdego pakietu sterowników. Skonfiguruj tę samą zmienną dla każdego kroku **Pobierz zawartość pakietu** i użyj zmiennej wartości **Zawartość przejściowa** w sekcji sterowników w kroku **Uaktualnij system operacyjny**.  

   > [!NOTE]
   > Jeśli istnieje więcej niż jeden pakiet, Configuration Manager dodaje sufiksu liczbowego do nazwy zmiennej. Na przykład jeśli określisz zmienną % mycontent % jako zmienną niestandardową jest główną przechowywania przywoływanej zawartości (co może mieć wielu pakietów). W przypadku odwoływania się do zmiennej w kroku podsekwencji, takim jak Uaktualnij system operacyjny, jest ona używana z sufiksem numerycznym. W tym przykładzie, % mycontent01% lub % mycontent02%, gdy liczba odpowiada kolejności, w której pakiet zostanie wyświetlony w tym kroku.

## <a name="optional-post-processing-task-sequence-steps"></a>Opcjonalne kroki sekwencji zadań przetwarzania końcowego  
 Po utworzeniu sekwencji zadań, można dodać dodatkowe kroki w celu odinstalowania aplikacji za pomocą znanych problemów ze zgodnością lub Dodaj przetwarzania końcowego akcje do wykonania po ponownym uruchomieniu komputera i uaktualnienia do systemu Windows 10 zakończyło się powodzeniem. Dodaj następujące dodatkowe kroki w grupie przetwarzania końcowego sekwencji zadań.  

> [!NOTE]  
>  Ta sekwencja zadań nie jest liniowy, to warunki na czynności, które mogą mieć wpływ na wyniki sekwencji zadań, w zależności od tego, czy pomyślnie uaktualnia komputer kliencki lub jeśli przywracać wersje systemu operacyjnego komputera klienckiego jego uruchomienia z.  

## <a name="optional-rollback-task-sequence-steps"></a>Wycofywanie opcjonalne kroki sekwencji zadań  
 Jeśli wystąpią problemy z procesu uaktualniania, po ponownym uruchomieniu komputera, Instalator będzie wycofać uaktualnienie do poprzedniego systemu operacyjnego i sekwencja zadań będzie kontynuować żadnych czynności w grupie wycofywania. Po utworzeniu sekwencji zadań, można dodać opcjonalne czynności do grupy wycofywania.  

## <a name="folder-and-files-removed-after-computer-restart"></a>Foldery i pliki usunięte po utworzeniu komputera, należy ponownie uruchomić  
 Po zakończeniu sekwencji zadań w celu uaktualnienia systemu operacyjnego do systemu Windows 10 i innych kroków w sekwencji zadań skrypty przetwarzania końcowego i wycofywania nie są usuwane aż do ponownego uruchomienia komputera.  Te pliki skryptów nie zawierają poufne informacje.  

