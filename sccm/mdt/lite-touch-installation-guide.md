---
title: Szybki Start - instalacji Lite Touch Installation
titleSuffix: Microsoft Deployment Toolkit
description: 'Przewodnik Szybki Start dla Microsoft Deployment Toolkit lite touch instalacji. '
ms.date: 09/09/2016
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: article
ms.assetid: 21bedd68-e925-46e0-a540-df8c0aba2d6c
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 63ddb0c95fe08051dee8e9d003d542307d21b28c
ms.sourcegitcommit: 645cd5a324bdd299906efa27eaca5885eafc9e9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2018
---
# <a name="quick-start-guide-for-lite-touch-installation"></a>Przewodnik Szybki Start dotyczący instalacji Lite Touch  
 Microsoft Deployment Toolkit (MDT) 2013 udostępnia technologii wdrażania systemów operacyjnych Windows i program Microsoft Office. Ten przewodnik pomaga szybko ocenić zestawu MDT 2013 zapewniając skrócone instrukcji krok po kroku dotyczących korzystania z niego do zainstalowania systemu operacyjnego Windows 8.1 za pomocą Lite Touch Installation (LTI) przy użyciu nośnika rozruchowego (DVD lub dysk flash USB). W tym przewodniku pokazano, jak wykonać scenariusz wdrażania nowego komputera przy użyciu udziału wdrożenia zestawu MDT 2013. Scenariusz wdrażania nowego komputera obejmuje wdrażania systemu Windows 8.1 do nowego komputera. W tym scenariuszu przyjęto założenie, że nie istnieje lub profilu, aby zachować dane użytkownika.  

> [!NOTE]     
>  W tym dokumencie *Windows* ma zastosowanie do systemów operacyjnych Windows 8.1, Windows 8, Windows 7, Windows Server® 2012 R2, Windows Server 2012 i Windows Server 2008 R2, chyba że określono inaczej. Zestaw MDT nie obsługuje wersji na podstawie procesora ARM systemu Windows. Podobnie *MDT* odwołuje się do zestawu MDT 2013, chyba że określono inaczej.  

 Po użyciu tego przewodnika, można obliczyć zestawu MDT, przejrzyj pozostałe wskazówki zestawu MDT, aby dowiedzieć się więcej o funkcjach zaawansowanych technologii.  

## <a name="prerequisites"></a>Wymagania wstępne  
 Aby wdrożyć systemy operacyjne i aplikacje przy użyciu zestawu MDT, środowisko musi spełniać następujące wymagania konfiguracji oprogramowania i komputera.  

### <a name="required-software"></a>Wymagane oprogramowanie  
 Aby ukończyć ten przewodnik, wymagane jest następujące oprogramowanie:  

-   Windows 8.1  

     Jeśli zdecydujesz ukończyć ten przewodnik po systemie operacyjnym niż Windows 8.1, zestawu MDT wymaga następujących elementów:  

    -   Microsoft .NET Framework w wersji 3.5 z dodatkiem Service Pack 1  

    -   Windows PowerShell™ w wersji 2.0  

     Windows 8.1 zawiera następujące funkcje.  

-   Windows Assessment and Deployment Kit (Windows ADK) dla Windows 8.1  

-   Usługi sieciowe, w tym System nazw domen i Dynamic Host Configuration Protocol  

> [!NOTE]   
>  Sekwencjonowania zadań używać we wdrożeniach MDT wymaga przypisania Tworzenie obiektu globalnego prawo do poświadczenia używane do uzyskania dostępu i uruchamiania konsoli Deployment Workbench i procesu wdrażania. To prawo jest dostępne dla kont z uprawnieniami administratora na poziomie (chyba że jawnie usunięte). Ponadto specjalizowany zabezpieczeń — profil zabezpieczeń ograniczoną funkcjonalność (SSLF) usuwa uprawnienie do tworzenia obiektów globalnych i nie powinny być stosowane do komputerów wdrażany przy użyciu zestawu MDT, aż do ukończenia procesu zestawu MDT.  

### <a name="computer-configuration"></a>Konfiguracja komputera  
 Aby ukończyć w tym przewodniku, należy skonfigurować komputery wymienione w poniższej tabeli. Te komputery mogą być komputerów fizycznych lub maszynach wirtualnych (VM) z wymienionych zasobów systemowych.  


|**Nazwa komputera**|**Opis**|  
|-|-|  
|WDG-MDT-01|Ten komputer uruchamia zestaw MDT i Windows 8.1 i jest zainstalowany w domenie o nazwie *mdt2013.corp.woodgrovebank.com* o nazwie system podstawowych operacji wejścia/wyjścia (NetBIOS) sieci *MDT2013*. Zasoby systemu komputera są:<br /><br /> -Uruchomiony na 1,4 GHz (GHz) lub szybszy procesor.<br />-1 gigabajt (GB) lub większa ilość pamięci fizycznej.<br />— Partycji jeden dysk, który ma 16 GB lub więcej dostępnego miejsca na dysku, który ma zostać partycji dysku C.<br />-CD-ROM lub DVD-ROM dysk, który zostanie przypisany literą dysku D. dysku|  
|WDG-REF-01|To jest komputer odniesienia i uruchamia bez bieżącego systemu operacyjnego. Zasoby systemu komputera są:<br /><br /> -Systemem 1,4 GHz lub szybszy procesor.<br />— 1 GB lub więcej pamięci fizycznej.<br />– 16 GB lub więcej dostępnego miejsca na dysku.|  
|WDG-CLI-01|To jest komputer docelowy i jest uruchamiany bez bieżącego systemu operacyjnego. Zasoby systemu komputera są:<br /><br /> -Systemem 1,4 GHz lub szybszy procesor.<br />— 1 GB lub więcej pamięci fizycznej.<br />– 16 GB lub więcej dostępnego miejsca na dysku.|  

> [!NOTE]   
>  W tym przewodniku założono, w przypadku oceny MDT na komputerach fizycznych lub wirtualnych 64-bitowej (x 64). Jeśli ocena MDT na różnych platformach 32-bitowej (x 86), Pobierz i zainstaluj x86 wersji zestawu MDT i składników, które opisano w tym przewodniku.  

## <a name="step-1-obtain-the-required-software"></a>Krok 1. Uzyskanie wymaganego oprogramowania  
 W tym przewodniku założono, że 64-bitowej wersji systemu Windows 8.1 jest zainstalowany na komputerze o nazwie *WDG-MDT-01*. Jeśli używasz komputera ma inną nazwę, nazwę komputera w celu zastąpienia *WDG-MDT-01*.  

> [!NOTE]   
>  W tej sekcji założono, że w przypadku tworzenia nowej infrastruktury zestawu MDT.  

 Następujące oprogramowanie jest wymagane do przeprowadzenia wdrożenia LTI:  

-   MDT 2013  

-   Windows ADK dla Windows 8.1  

-   Windows 8.1, pliki dystrybucyjne  

-   Sterowniki urządzeń wymagane dla komputera docelowego, WDG-CLI-01  

-   Sterowniki urządzeń wymagane do komputera odniesienia, WDG-REF-01  

## <a name="step-2-prepare-the-mdt-environment"></a>Krok 2. Przygotowanie środowiska zestawu MDT  
 W tym kroku należy przygotować środowisko MDT przed tworzenia komputera odniesienia i wdrażania przechwyconego obrazu komputera odniesienia do komputera docelowego (WDG-CLI-01).  

 Przygotowanie środowiska MDT przez:  

-   Instalowanie zestawu MDT, zgodnie z opisem w [krok 2-1: Instalowanie zestawu MDT](#InstallMDT)  

-   Instalowanie zestawu Windows ADK, zgodnie z opisem w [krok 2-2: Zainstaluj zestaw Windows ADK](#InstallWindowsADK)  

###  <a name="InstallMDT"></a>Krok 2-1. Instalowanie zestawu MDT  
 Aby zainstalować zestaw MDT, wykonaj następujące czynności:  

1.  Kliknij dwukrotnie **MicrosoftDeploymentToolkit2013_x64.msi** (dla 64-bitowych systemach operacyjnych) lub **MicrosoftDeploymentToolkit2013_x86.msi** (dla 32-bitowych systemach operacyjnych), a następnie kliknij przycisk **Zainstalować**.  

     Uruchamia Kreatora instalacji programu Microsoft Deployment Toolkit 2013.  

2.  Ukończ Microsoft Deployment Toolkit 2013 Kreatora instalacji korzystając z poniższych informacji. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    |**Na tej stronie kreatora**|**W tym**|  
    |-|-|  
    |**Kreator instalacji 2013 Microsoft Deployment Toolkit — Zapraszamy!**|Kliknij przycisk **Dalej**.|  
    |**Umowa licencyjna użytkownika oprogramowania**|Kliknij przycisk **akceptuję warunki umowy licencyjnej**, a następnie kliknij przycisk **dalej**.|  
    |**Instalacja niestandardowa**|Kliknij przycisk **Dalej**.|  
    |**Gotowy do zainstalowania programu Microsoft Deployment Toolkit 2013**|Kliknij pozycję **Zainstaluj**.|  
    |**Instalowanie zestawu narzędzi firmy Microsoft do wdrażania 2013**|Zostanie wyświetlony pasek postępu instalacji zestawu MDT.|  
    |**Kończenie pracy Kreatora instalacji programu Microsoft Deployment Toolkit 2013**|Kliknij przycisk **Zakończ**.|  

 Ukończeniu działania Kreatora instalacji programu Microsoft Deployment Toolkit 2013 i zestaw MDT jest zainstalowany na WDG-MDT-01.  

###  <a name="InstallWindowsADK"></a>Krok 2-2. Zainstaluj zestaw Windows ADK  
 Aby zainstalować zestaw Windows ADK, wykonaj następujące czynności:  

1.  Instalowanie plików dystrybucji zestawu Windows ADK na dysku CD fizycznych lub wirtualnych.  

2.  W Eksploratorze Windows przejdź do katalogu głównego dysku CD, a następnie kliknij dwukrotnie **adksetup.exe**.  

     Uruchamia Kreatora instalacji zestawu wdrożenia i oceny.  

3.  Ukończenie oceny i instalacji Kreatora zestawu wdrażania, korzystając z poniższych informacji.

    |**Na tej stronie kreatora**|**W tym**|  
    |-|-|  
    |**Określ lokalizację**|Kliknij przycisk **Dalej**.|  
    |**Dołącz do programu poprawy jakości obsługi klienta (CEIP)**|Kliknij przycisk **tak** Jeśli chcesz uczestniczyć lub **nr** , jeśli nie. Następnie kliknij przycisk **dalej**.|  
    |**Umowa licencyjna**|Kliknij przycisk **zaakceptować**.|  
    |**Wybierz funkcje, które chcesz zainstalować**|Upewnij się, aby tylko pola wyboru dla następujące funkcje są zaznaczone, a następnie kliknij przycisk **dalej**:<br /><br /> -Narzędzia wdrażania<br />— Środowisko preinstalacyjne systemu Windows (Windows PE)<br />-Narzędzie migracji stanu użytkownika systemu Windows **Uwaga:**  Zestaw MDT nie wymaga innych funkcji, ale mogą zostać zainstalowane, w razie potrzeby.|  
    |**Instalowanie funkcji**|Zostanie wyświetlony pasek postępu instalacji funkcji.|  
    |**Witamy w Assessment and Deployment Kit**|Kliknij przycisk **Zamknij**.|  

4.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

5.  Zamknij wszystkie otwarte okna.  

> [!NOTE]   
>  Po zainstalowaniu zestawu Windows ADK, wyloguj się, a następnie zaloguj ponownie do komputera, aby zmienna środowiskowa PATH została zaktualizowana do folderu % Program Files%\Windows Imaging.  

## <a name="step-3-configure-mdt-to-create-the-reference-computer"></a>Krok 3. Konfigurowanie zestawu MDT, aby utworzyć komputer odniesienia  
 Po przygotowaniu środowiska zestawu MDT, należy utworzyć komputer odniesienia. Komputer odniesienia jest szablon do wdrażania nowych obrazów na komputerach docelowych. Skonfiguruj ten komputer dokładnie tak, jak na komputerach docelowych zostanie skonfigurowany. Zostanie wdrażanie Windows 8.1 na komputerze odniesienia (WDG-REF-01), przechwytywania obrazu komputera odniesienia, a następnie wdrażania przechwyconego obrazu na komputerze docelowym (WDG-CLI-01).  

 Skonfiguruj zestawu MDT, aby utworzyć komputer odniesienia przez:  

-   Tworzenie udziału wdrożenia zestawu MDT, zgodnie z opisem w [krok 3-1: Utwórz udział wdrożenia zestawu MDT](#CreateMDTDeployShare)  

-   Dodawanie plików systemu operacyjnego do udziału wdrożenia, zgodnie z opisem w [krok 3-2: Dodaj pliki systemu operacyjnego do udziału wdrożenia](#AddOSFilestoDeployShare)  

-   Dodawanie sterowników urządzeń do udziału wdrożenia, zgodnie z opisem w [kroku nr 3, 3: Dodawanie sterowników urządzeń do udziału wdrożenia](#AddDriverstoDeployShare)  

-   Tworzenie sekwencji zadań dla komputera odniesienia, zgodnie z opisem w [krok 3 — 4: Tworzenie sekwencji zadań dla komputera odniesienia](#CreateTaskSequence)  

-   Włączanie monitorowania procesu wdrożenia LTI, zgodnie z opisem w [krok 3 – 5: Włącz wdrożenia LTI monitorowania procesu](#EnableLTIDeployMonitor)  

-   Aktualizacja udziału wdrożenia, zgodnie z opisem w [krok 3 – 6: Zaktualizuj udział wdrożenia](#UpdateDeployShare)  

###  <a name="CreateMDTDeployShare"></a>Krok 3-1. Utwórz udział wdrożenia zestawu MDT  
 Przed rozpoczęciem wdrożenia, należy utworzyć udział wdrożenia zestawu MDT w konsoli Deployment Workbench. Ten udział wdrożenia to repozytorium obrazów systemu operacyjnego, pakietów językowych, aplikacji, sterowników urządzeń i innego oprogramowania wdrożone na komputerach docelowych.  

 **Aby utworzyć udział wdrożenia w konsoli Deployment Workbench**  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench przejdź do wdrożenia środowiska roboczego/wdrożenia udziałów.  

3.  W okienku Akcje kliknij polecenie **nowe udziały wdrożenia**.  

     Uruchamia Kreatora nowego udziału wdrożenia.  

4.  Ukończ Kreatora nowego udziału wdrożenia korzystając z poniższych informacji.

    |**Na tej stronie kreatora**|**W tym**|  
    |-|-|  
    |**Path**|W **ścieżka udziału wdrożenia**, typ **C:\DeploymentShare$**, a następnie kliknij przycisk **dalej**.|  
    |**Udostępnij**|Kliknij przycisk **Dalej**.|  
    |**Opisowa nazwa**|Kliknij przycisk **Dalej**.|  
    |**Opcje**|Kliknij przycisk **Dalej**.|  
    |**Podsumowanie**|Kliknij przycisk **Dalej**.|  
    |**Postęp**|Zostanie wyświetlony pasek postępu tworzenia udziału wdrożenia.|  
    |**Potwierdzenie**|Kliknij przycisk **Zakończ**.|  

 Zakończenie Kreatora nowego udziału wdrożenia, a nowy udział wdrożenia — udział wdrożenia zestawu MDT (C:\DeploymentShare$)—appears w okienku szczegółów.  

###  <a name="AddOSFilestoDeployShare"></a>Krok 3-2. Dodaj pliki systemu operacyjnego do udziału wdrożenia  
 Zestaw MDT działa jako repozytorium plików systemu operacyjnego wdrożona na komputerze odniesienia (WDG-REF-01) oraz komputera docelowego (WDG-CLI-01). Dodaj system operacyjny w węźle systemy operacyjne w konsoli Deployment Workbench przy użyciu Kreatora importu systemu operacyjnego.  

 **Aby dodać pliki systemu operacyjnego Windows 8.1 do udziału wdrożenia**  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench przejdź do wdrożenia środowiska roboczego/wdrożenia udziałów/udział wdrożenia zestawu MDT (C:\DeploymentShare$)/Operating systemów.  

3.  W okienku Akcje kliknij polecenie **importu systemu operacyjnego**.  

     Uruchamia Kreatora importu systemu operacyjnego.  

4.  Ukończ Kreatora importu systemu operacyjnego, korzystając z poniższych informacji.    

    |**Na tej stronie kreatora**|**W tym**|  
    |-|-|  
    |**Na tej stronie kreatora**|**W tym**|  
    |**Typ systemu operacyjnego**|Kliknij przycisk **pełny zestaw plików źródłowych**, a następnie kliknij przycisk **dalej**.|  
    |**Obiekt źródłowy**|W **katalog źródłowy**, typ ***source_path*** (gdzie *source_path* jest w pełni kwalifikowana ścieżka do plików dystrybucyjnych Windows 8.1), a następnie kliknij przycisk  **Następny**.|  
    |**Miejsce docelowe**|Kliknij przycisk **Dalej**.|  
    |**Podsumowanie**|Kliknij przycisk **Dalej**.|  
    |**Postęp**|Zostanie wyświetlony pasek postępu do importowania systemu operacyjnego.|  
    |**Potwierdzenie**|Kliknij przycisk **Zakończ**.|  

 Zakończeniu pracy Kreatora importu systemu operacyjnego. Windows 8.1 zostanie dodany do listy systemów operacyjnych w okienku szczegółów i skopiowane do *udział_wdrożenia*\Operating systemów\\*operating_system* folder (gdzie  *udział_wdrożenia* jest udostępnionego folderu sieciowego utworzonego wcześniej w procesie i *operating_system* jest nazwą dodane do udziału wdrożenia systemu operacyjnego).  

###  <a name="AddDriverstoDeployShare"></a>Krok 3-3. Dodawanie sterowników urządzeń do udziału wdrożenia  
 Po dodaniu Windows 8.1 do konsoli Deployment Workbench, należy dodać sterowniki urządzeń wymagane przez komputer odniesienia (WDG-REF-01), a na komputerze docelowym (WDG-CLI-01). Te sterowniki urządzeń zostaną dodane do systemu Windows PE i wdrażane z Windows 8.1. Dodaj sterowniki urządzeń w węźle sterowniki Out-of-box w konsoli Deployment Workbench przy użyciu Kreatora nowego sterownika, który kopiuje pliki sterowników urządzeń do wdrożenia udostępnionej w programie sterowniki Out-of-Box\\*device_driver* () gdzie *device_driver* to nazwa sterownika urządzenia, należy dodać do udziału wdrożenia).  

> [!NOTE]   
>  Jeśli sterowniki urządzenia komputera odniesienia (WDG-REF-01) i na komputerze docelowym (WDG-CLI-01) są dołączone Windows 8.1, Pomiń ten krok i przejdź do następujących czynności.  

 **Aby dodać sterowniki urządzeń dla komputerów referencyjnych i docelowych do udziału dystrybucyjnego**  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench przejdź do wdrożenia środowiska roboczego/wdrożenia udziałów/udział wdrożenia zestawu MDT (C:\DeploymentShare$)/Out-of-Box sterowniki.  

3.  W okienku Akcje kliknij polecenie **importowania sterowników**.  

     Uruchamia Kreatora importowania sterownika.  

4.  Ukończ Kreatora importowania sterownika, korzystając z poniższych informacji.

    |**Na tej stronie kreatora**|**W tym**|
    |-|-|  
    |**Określ katalog**|W **katalog źródłowy sterownika**, typ ***driver_path*** (gdzie *driver_path* jest w pełni kwalifikowana ścieżka do folderu zawierającego sterowniki urządzeń), a następnie kliknij przycisk  **Następny**.|  
    |**Podsumowanie**|Kliknij przycisk **Dalej**.|  
    |Postęp|Zostanie wyświetlony pasek postępu do importowania sterowników urządzeń.|  
    |**Potwierdzenie**|Kliknij przycisk **Zakończ**.|  

 Zakończeniu pracy Kreatora importu sterowników. Sterowniki urządzeń są dodawane do listy systemów operacyjnych w okienku szczegółów i są kopiowane do *udział_wdrożenia*folderu sterowników \Out-of-box (gdzie *udział_wdrożenia* jest udziału wdrożenia utworzone wcześniej w procesie).  

###  <a name="CreateTaskSequence"></a>Krok 3 — 4: Tworzenie sekwencji zadań dla komputera odniesienia  
 Tworzenie sekwencji zadań zestawu MDT w węźle sekwencje zadań w konsoli Deployment Workbench za pomocą Kreatora nowej sekwencji zadań. Zestaw MDT obejmuje szablonu standardowe sekwencję zadań klienta, który można użyć do wdrożenia docelowego systemu operacyjnego na komputerze odniesienia (WDG-REF-01).  

 **Aby utworzyć sekwencję zadań do wdrażania na komputerze odniesienia**  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench przejdź do wdrożenia środowiska roboczego/wdrożenia udziałów/udział wdrożenia zestawu MDT (C:\DeploymentShare$)/Task sekwencji  

3.  W okienku Akcje kliknij polecenie **nowej sekwencji zadań**.  

     Uruchamia Kreatora nowej sekwencji zadań.  

4.  Ukończ Kreatora nowej sekwencji zadań korzystając z poniższych informacji. Zaakceptuj wartości domyślne, chyba że określono inaczej.

    |**Na tej stronie kreatora**|**W tym**|  
    |-|-|  
    |**Ustawienia ogólne**|1.  W **identyfikator sekwencji zadań**, typ **WIN8_REFERENCE**.<br />2.  W **nazwę sekwencji zadań**, typ **wdrażanie Windows 8.1 na komputerze odniesienia**.<br />3.  W **komentarze sekwencji zadań**, typ **sekwencję zadań pod kątem wdrażania na komputerze odniesienia (WDG-REF-01) Windows 8.1**.<br />4.  Kliknij przycisk **Dalej**.|  
    |**Wybierz szablon**|W **dostępne są następujące szablony sekwencji zadań. Wybierz ten, który chcesz użyć jako punktu wyjścia**, wybierz pozycję **standardowe sekwencję zadań klienta**, a następnie kliknij przycisk **dalej**.|  
    |**Wybierz system operacyjny**|W **zawiera następujące obrazy systemu operacyjnego są dostępne do wdrożenia z tą sekwencją zadań**. **Wybierz jeden z nich do używania**, wybierz pozycję **Windows 8.1 *wersji***  (gdzie *wersji* jest w wersji Windows 8.1 dodana do węzła systemy operacyjne w Konsoli Deployment Workbench), a następnie kliknij przycisk **dalej**.|  
    |**Określ klucz produktu**|Kliknij przycisk **nie zostanie określony klucz produktu w tej chwili**, a następnie kliknij przycisk **dalej**.|  
    |**Ustawienia systemu operacyjnego**|1.  W **imię i nazwisko**, typ **pracownika banku Woodgrove**.<br /><br /> 2.  W **organizacji**, typ **banku Woodgrove**.<br /><br /> 3.  W **strona główna programu Internet Explorer**, typ **http://www.woodgrovebank.com**.<br /><br /> 4.  Kliknij przycisk **Dalej**.|  
    |**Hasło administratora**|W **hasło administratora** i **Potwierdź hasło administratora**, typ  **P@ssw0rd** , a następnie kliknij przycisk **dalej**.|  
    |**Podsumowanie**|Kliknij przycisk **Dalej**.|  
    |**Postęp**|Zostanie wyświetlony pasek postępu tworzenia sekwencji zadań.|  
    |**Potwierdzenie**|Kliknij przycisk **Zakończ**.|  

 Zakończeniu pracy Kreatora sekwencji importu zadań i **wdrażanie Windows 8.1 na komputerze odniesienia** sekwencja zadań zostanie dodany do listy sekwencji zadań.  

###  <a name="EnableLTIDeployMonitor"></a>Krok 3 – 5. Włącz wdrożenia LTI monitorowania procesu  
 Przed wdrożeniem komputer odniesienia (WDG-REF-01) z nośnika rozruchowego LTI utworzonego wcześniej w procesie, aby włączyć monitorowanie procesu wdrożenia LTI. Można monitorować proces wdrożenia LTI w węźle Monitorowanie w udziału wdrożenia. Monitorowanie na **monitorowanie** kartę na arkuszu właściwości udziału wdrożenia. W dalszej części procesu będziesz monitorować proces wdrożenia LTI.  

 **Aby włączyć monitorowanie procesu wdrażania LTI**  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench przejdź do wdrożenia środowiska roboczego/wdrożenia udziałów.  

3.  W okienku szczegółów kliknij **udział wdrożenia zestawu MDT (C:\DeploymentShare$)**.  

4.  W okienku Akcje kliknij polecenie **właściwości**  

     **Właściwości udziału wdrożenia zestawu MDT (C:\DeploymentShare$)** zostanie otwarte okno dialogowe.  

5.  W **właściwości udział wdrożenia zestawu MDT (C:\DeploymentShare$)** na okna dialogowego **monitorowanie** wybierz opcję **Włącz monitorowanie dla tego udziału wdrożenia** pole wyboru , a następnie kliknij przycisk **Zastosuj**.  

6.  W **właściwości udziału wdrożenia zestawu MDT (C:\DeploymentShare$)** na okna dialogowego **reguły** karcie, zwróć uwagę, że **EventService** właściwość została dodana do Plik CustomSettings.ini, a następnie kliknij przycisk **OK**.  

7.  Zamknij wszystkie otwarte okna i oknach dialogowych.  

###  <a name="UpdateDeployShare"></a>Krok 3 – 6. Zaktualizuj udział wdrożenia  
 Po skonfigurowaniu udziału wdrożenia, należy zaktualizować je. Aktualizacja udziału wdrożenia aktualizuje wszystkie pliki konfiguracyjne zestawu MDT i generuje dostosowaną wersję środowiska Windows PE. Używasz dostosowaną wersję środowiska Windows PE do uruchomienia komputera odniesienia i inicjowania wdrożenia LTI.  

 **Aby zaktualizować udział wdrożenia w konsoli Deployment Workbench**  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench przejdź do wdrożenia środowiska roboczego/wdrożenia udziałów.  

3.  W okienku szczegółów kliknij **udział wdrożenia zestawu MDT (C:\DeploymentShare$)**.  

4.  W okienku Akcje kliknij polecenie **udziału wdrożenia aktualizacji**.  

     Zostanie uruchomiony Kreator udziału wdrożenia aktualizacji.  

5.  Ukończ Kreatora udziału wdrożenia aktualizacji, korzystając z poniższych informacji. Zaakceptuj wartości domyślne, chyba że określono inaczej.

    |**Na tej stronie kreatora**|**W tym**|  
    |-|-|  
    |**Opcje**|Kliknij przycisk **Dalej**.|  
    |**Podsumowanie**|Kliknij przycisk **Dalej**.|  
    |**Postęp**|Zostanie wyświetlony pasek postępu aktualizacji udziału wdrożenia.|  
    |**Potwierdzenie**|Kliknij przycisk **Zakończ**.|  

 Konsoli Deployment Workbench uruchamia aktualizacja udziału wdrożenia zestawu MDT udział wdrożenia (C:\DeploymentShare$). Konsoli Deployment Workbench tworzy pliki pliki LiteTouchPE_x64.iso i LiteTouchPE_x64.wim (dla 64-bitowych komputerów docelowych) lub pliki LiteTouchPE_x86.iso i LiteTouchPE_x86.wim (dla 32-bitowych komputerów docelowych) w *udział_wdrożenia*Folderu \Boot (gdzie *udział_wdrożenia* jest udostępnianym folderem sieciowym używanym jako udziału wdrożenia).  

## <a name="step-4-deploy-windows-81-and-capture-an-image-of-the-reference-computer"></a>Krok 4. Windows 8.1, wdrażania i przechwytywania obrazu komputera odniesienia  
 Po utworzeniu sekwencji zadań, aby wdrożyć Windows 8.1 na komputerze odniesienia, inicjowania wdrożenia systemu operacyjnego i obraz przechwytywania, należy uruchomić na komputerze odniesienia z nośnika rozruchowego LTI.  

 Windows 8.1, wdrażania i przechwytywania obrazu komputera odniesienia przy:  

-   Tworzenie nośnika rozruchowego LTI, zgodnie z opisem w [krok 4-1: Tworzenie nośnika rozruchowego LTI](#CreateLTIBootable)  

-   Uruchamianie na komputerze odniesienia z nośnika rozruchowego LTI i monitorowanie procesu wdrażania LTI, zgodnie z opisem w [krok 4-2: Uruchom komputer odniesienia przy użyciu nośnika rozruchowego LTI](#StartRefCompwithLTIBootable)  

###  <a name="CreateLTIBootable"></a>Krok 4-1. Tworzenie nośnika rozruchowego LTI  
 Musisz podać metodę uruchamiania komputera z dostosowaną wersję środowiska Windows PE utworzonej po zaktualizowaniu udziału wdrożenia. Konsoli Deployment Workbench tworzy pliki pliki LiteTouchPE_x64.iso i LiteTouchPE_x64.wim (dla 64-bitowych komputerów docelowych) lub pliki LiteTouchPE_x86.iso i LiteTouchPE_x86.wim (dla 32-bitowych komputerów docelowych) w *udział_wdrożenia*Folderu \Boot (gdzie *udział_wdrożenia* jest udostępnianym folderem sieciowym używanym jako udziału wdrożenia). Utwórz odpowiedni nośnik rozruchowy LTI z jednego z tych obrazów.  

 **Aby utworzyć nośnik rozruchowy LTI**  

1.  W Eksploratorze Windows przejdź do C:\DeploymentShare$\Boot.  

2.  Na podstawie typu komputera używana dla komputera odniesienia (WDG-REF-01), wykonaj jedną z następujących czynności:  

    -   Jeśli komputer odniesienia jest komputera fizycznego, Utwórz fizycznego dysku CD lub DVD pliki LiteTouchPE_x64.iso lub LiteTouchPE_x86.iso pliku.  

    -   Jeśli komputer odniesienia jest maszyny Wirtualnej, należy uruchomić maszyny Wirtualnej bezpośrednio z pliku pliki LiteTouchPE_x64.iso lub LiteTouchPE_x86.iso lub z dysku CD lub DVD plików międzynarodowej organizacji standardowe (ISO).  

###  <a name="StartRefCompwithLTIBootable"></a>Krok 4-2. Uruchom komputer odniesienia przy użyciu nośnika rozruchowego LTI  
 Uruchom komputer odniesienia (WDG-REF-01) z nośnika rozruchowego LTI utworzonego wcześniej w procesie. Nośnik rozruchowy LTI uruchamia środowisko Windows PE na komputerze odniesienia i inicjuje wdrożenia. Po zakończeniu procesu wdrożenia zestawu MDT Windows 8.1 jest wdrażany na komputerze odniesienia.  

> [!NOTE]   
>  Można użyć 32-bitowego obrazu rozruchowego do wdrożenia zarówno 32-bitowe i 64-bitowe systemy operacyjne: Jednak 64-bitowego obrazu rozruchowego można używać tylko do wdrażania 64-bitowych systemach operacyjnych.  

 Można również zainicjować proces przez uruchomienie komputera docelowego z usług wdrażania systemu Windows. Aby uzyskać więcej informacji, zobacz sekcję "Przygotowanie usług wdrażania systemu Windows", w dokumentacji zestawu MDT *przy użyciu programu Microsoft Deployment Toolkit*.  

 **Aby uruchomić komputer odniesienia z nośnika rozruchowego LTI**  

1.  Uruchom WDG-REF-01 z nośnika rozruchowego LTI utworzonego wcześniej w procesie.  

     Uruchamia środowisko Windows PE, a następnie uruchamia Kreatora wdrażania systemu Windows.  

2.  Ukończ pracę Kreatora wdrażania systemu Windows, korzystając z poniższych informacji. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    |**Na tej stronie kreatora**|**W tym**|  
    |-|-|  
    |**Welcome**|Kliknij przycisk **Uruchom Kreatora wdrażania, aby zainstalować nowy System operacyjny**.|  
    |**Poświadczenia**|1.  W **nazwy użytkownika**, typ **administratora**.<br />2.  W **hasło**, typ  **P@ssw0rd** .<br />3.  W **domeny**, typ **MDT2013**.<br />4.  Kliknij przycisk **OK**.|  
    |**Sekwencja zadań**|Kliknij przycisk **wdrażanie Windows 8.1 na komputerze odniesienia**, a następnie kliknij przycisk **dalej**.|  
    |**Szczegóły komputera**|W **nazwy komputera**, **WDG-REF-01 wpisz**, a następnie kliknij przycisk **dalej**.|  
    |**Przenoszenia danych i ustawień**|Kliknij przycisk **Dalej**.|  
    |**Dane użytkownika (przywracanie)**|Kliknij przycisk **Dalej**.|  
    |**Ustawienia regionalne i czas**|Kliknij przycisk **Dalej**.|  
    |**Przechwycenie obrazu**|Kliknij przycisk **przechwytywania obrazu komputera odniesienia**, a następnie kliknij przycisk **dalej**.|  
    |**Gotowe**|1.  Kliknij przycisk **szczegóły** do wyświetlania informacji podanych w kreatorze.<br />2.  Kliknij przycisk **rozpocząć**.|  

 **Aby monitorować proces wdrażania komputera odniesienia, wykonaj następujące czynności na WDG-MDT-01**  

1.  Na WDG-MDT-01, kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench przejdź do wdrożenia środowiska roboczego/wdrożenia udziałów/udział wdrożenia zestawu MDT (C:\DeploymentShare$)/Monitoring.  

3.  W okienku szczegółów wyświetlić proces wdrażania **WDG-REF-01**.  

4.  W okienku Akcje kliknij okresowo **Odśwież**.  

     Stan procesu wdrażania jest aktualizowana w okienku szczegółów.  

     Nadal monitorować proces wdrażania, aż do ukończenia procesu.  

5.  W okienku szczegółów kliknij **WDG-REF-01**.  

6.  W okienku Akcje kliknij polecenie **właściwości**.  

     **Właściwości WDG-REF-01** zostanie wyświetlone okno dialogowe.  

7.  W **właściwości WDG-REF-01** na okna dialogowego **tożsamości** pozycję Wyświetl monitorowania dostarczone informacje na temat procesu wdrażania zgodnie z opisem w poniższej tabeli.

    |**Informacje**|**Opis**|  
    |-|-|  
    |**ID**|Unikatowy identyfikator dla komputera wdrażany.|  
    |**Nazwa komputera**|Nazwa komputera jest wdrożony.|  
    |**Stan wdrożenia**|Bieżący stan komputera wdrożony; Stan może być jedną z następujących czynności:<br /><br /> -   **Uruchomiona**. Sekwencja zadań jest dobra i uruchomiona.<br />-   **Nie powiodło się**. Sekwencja zadań nie powiodło się, a proces wdrażania nie powiodło się.<br />-   **Ukończono**. Sekwencja zadań została ukończona.<br />-   **Odpowiadać**. Sekwencja zadań jego stan nie został zaktualizowany w ciągu ostatnich czterech godzin i zostanie uznany za nieodpowiadający.|  
    |**Krok**|Bieżącego kroku sekwencji zadań uruchamiana.|  
    |**Postęp**|Ogólny postęp sekwencji zadań. Pasek postępu wskazuje, ile kroków sekwencji zadań zostały uruchomione poza całkowita liczba kroków sekwencji zadań.|  
    |**Początek**|Czas rozpoczęcia procesu wdrażania.|  
    |**Koniec**|Czas zakończenia procesu wdrażania.|  
    |**Który upłynął**|Czas procesu wdrażania była uruchomiona lub trwało do uruchomienia, jeśli zakończenie procesu wdrażania.|  
    |**Błędy**|Liczba błędów napotkanych podczas procesu wdrażania.|  
    |**Ostrzeżenia**|Liczba ostrzeżeń podczas procesu wdrażania.|  
    |**Pulpit zdalny**|Ten przycisk służy do ustanawiania połączenia pulpitu zdalnego z komputerem wdrażany przy użyciu funkcji pulpitu zdalnego systemu Windows. Ta metoda zakłada się, że:<br /><br /> -Docelowy system operacyjny jest uruchomiony i ma włączoną obsługę usług pulpitu zdalnego<br />-   **mstsc.exe** znajduje się w ścieżce **Uwaga:**  Ten przycisk jest zawsze widoczne, ale nie można ustanowić sesji usług pulpitu zdalnego Jeśli monitorowanym komputerze środowiska Preinstalacyjnego systemu Windows, instalacja docelowego systemu operacyjnego nie zostało zakończone lub nie ma włączenie tej funkcji pulpitu zdalnego.|  
    |**Połączenie maszyn wirtualnych**|Ten przycisk służy do ustanowienia połączenia pulpitu zdalnego z maszyną wirtualną w HyperV®. Ta metoda zakłada się, że:<br /><br /> -Wdrożenie jest wykonywane do maszyny Wirtualnej z systemem w funkcji Hyper-V<br />-   **vmconnect.exe** znajduje się w folderze %ProgramFiles%\Hyper-V **Uwaga:**  Ten przycisk jest wyświetlany, gdy ZTIGather.wsf wykryje, że składniki integracji funkcji Hyper-V są uruchomione na monitorowanym komputerze. W przeciwnym razie ten przycisk, nie będą widoczne.|  
    |**DaRT zdalnego sterowania**|Ten przycisk pozwala ustanowić sesję zdalnego sterowania należy użyć funkcji Podgląd zdalnego w Diagnostics and Recovery Toolkit (DaRT).<br /><br /> Ta metoda zakłada się, że:<br /><br /> -DaRT został wdrożony na komputerze docelowym i jest aktualnie uruchomiona<br />-   **DartRemoteViewer.exe** znajduje się w folderze %ProgramFiles%\Microsoft DaRT 7\v7 **Uwaga:**  Ten przycisk jest wyświetlany, gdy ZTIGather.wsf wykryje, że DaRT jest uruchomiony na monitorowanym komputerze. W przeciwnym razie ten przycisk, nie będą widoczne.|  
    |**Automatyczne odświeżanie te informacje co 10 sekund**|Pole wyboru, która kontroluje, czy informacje w oknie dialogowym są odświeżane automatycznie. Jeśli pole wyboru jest:<br /><br /> -Zaznaczone, dane są odświeżane co 10 sekund<br />-Wyczyszczone, nie jest automatycznie odświeżany informacje i musi być odświeżane ręcznie przy użyciu **Odśwież teraz** przycisku|  
    |**Odśwież teraz**|Ten przycisk natychmiast odświeża informacje wyświetlane w oknie dialogowym.|  

8.  W **właściwości WDG-REF-01** okno dialogowe, kliknij przycisk **OK**.  

9. Zamknięcie konsoli Deployment Workbench.  

 Aby ukończyć proces wdrażania komputera odniesienia, wykonaj następujące czynności na WDG-REF-01:  

1.  Na WDG-REF-01 w **Wdrożęnia** okno dialogowe, kliknij przycisk **szczegóły**.  

     Jeśli występują jakiekolwiek błędy i ostrzeżenia, przejrzyj błędy lub ostrzeżenia i Zarejestruj wszystkie informacje diagnostyczne.  

2.  W **Wdrożęnia** okno dialogowe, kliknij przycisk **Zakończ**.  

 Windows 8.1 jest zainstalowany na komputerze odniesienia, a przechwycony plik Windows Imaging Format (WIM) z komputera odniesienia (WIN7_REFERENCE.wim) są przechowywane w *udział_wdrożenia*\Captures folder (gdzie  *udział_wdrożenia* jest folder udostępniony służący jako udziału wdrożenia). Jeśli wystąpią błędy lub ostrzeżenia, należy skontaktować się dokumentu MDT *Rozwiązywanie problemów z odwołania*.  

## <a name="step-5-configure-mdt-to-deploy-windows-81-to-the-target-computer"></a>Krok 5. Skonfiguruj zestaw MDT do wdrożenia Windows 8.1 na komputerze docelowym  
 Po przechwyceniu obrazu komputera odniesienia (MDT-REF-01), należy go wdrożyć na komputerze docelowym (MDT-CLI-01). Przechwycony obraz należy zaimportować do konsoli Deployment Workbench przy użyciu Kreatora importu systemu operacyjnego. Następnie należy utworzyć sekwencję zadań do wdrażania przechwyconego obrazu na komputerze docelowym.  

 Skonfiguruj zestaw MDT do wdrożenia Windows 8.1 na komputerze docelowym przez:  

-   Dodawanie przechwycony obraz komputera odniesienia do konsoli Deployment Workbench, zgodnie z opisem w [krok 5-1: Dodaj przechwycony obraz komputera odniesienia do konsoli Deployment Workbench](#AddCapturedImagetoDeployWB)  

-   Tworzenie sekwencji zadań dla komputera docelowego, zgodnie z opisem w [krok 5-2: Tworzenie sekwencji zadań dla komputera docelowego](#CreateTaskSequenceforTarget)  

###  <a name="AddCapturedImagetoDeployWB"></a>Krok 5-1. Dodaj przechwycony obraz komputera odniesienia do konsoli Deployment Workbench  
 Do wdrażania przechwyconego obrazu komputera odniesienia do komputera docelowego, należy dodać do listy systemów operacyjnych w węźle systemy operacyjne w konsoli Deployment Workbench przechwyconego obrazu. Działanie Kreatora importu systemu operacyjnego kopiuje pliki systemu operacyjnego do *udział_wdrożenia*\Operating systemów\\*operating_system* folder (gdzie *deployment_ udostępnianie* jest folder udziału wdrożenia utworzony wcześniej w procesie i *operating_system* jest nazwą dodane do udziału wdrożenia systemu operacyjnego).  

 **Aby dodać przechwycony obraz komputera odniesienia do konsoli Deployment Workbench**  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench przejdź do wdrożenia środowiska roboczego/wdrożenia udziałów/udział wdrożenia zestawu MDT (C:\DeploymentShare$)/Operating systemów.  

3.  W okienku Akcje kliknij polecenie **system operacyjny importu**.  

     Uruchamia Kreatora importu systemu operacyjnego.  

4.  Ukończ Kreatora importu systemu operacyjnego, korzystając z informacji w poniższej tabeli.

    |**Na tej stronie kreatora**|**W tym**|  
    |-|-|  
    |**Typ systemu operacyjnego**|Kliknij przycisk **niestandardowy plik obrazu**, a następnie kliknij przycisk **dalej**.|  
    |**Obraz**|W **plik źródłowy**, typ **C:\DeploymentShare$\Captures\WIN8_REFERENCE.wim**, a następnie kliknij przycisk **dalej**.|  
    |**Instalator**|Kliknij przycisk **Dalej**.|  
    |**Miejsce docelowe**|Kliknij przycisk **Dalej**.|  
    |**Podsumowanie**|Kliknij przycisk **Dalej**.|  
    |**Postęp**|Zostanie wyświetlony pasek postępu do importowania systemu operacyjnego.|  
    |**Potwierdzenie**|Kliknij przycisk **Zakończ**.|  

     Zakończeniu pracy Kreatora importu systemu operacyjnego. Przechwycony obraz odniesienia systemu operacyjnego komputera (WDG-REF-01) zostanie dodany do listy systemów operacyjnych w okienku szczegółów i jest kopiowany do *udział_wdrożenia*\Operating systemów\\  *operating_system* folder (gdzie *udział_wdrożenia* jest folder udziału wdrożenia utworzony wcześniej w procesie i *operating_system* to nazwa systemu operacyjnego System dodane do udziału wdrożenia).  

5.  Zamknij wszystkie otwarte okna i oknach dialogowych.  

###  <a name="CreateTaskSequenceforTarget"></a>Krok 5-2. Tworzenie sekwencji zadań dla komputera docelowego  
 W węźle sekwencje zadań w konsoli Deployment Workbench za pomocą Kreatora nowej sekwencji zadań, należy utworzyć sekwencję zadań zestawu MDT dla komputera docelowego. Ta sekwencja zadań jest używany do wdrażania przechwyconego obrazu komputera odniesienia do komputera docelowego.  

 **Aby utworzyć sekwencję zadań do wdrażania przechwyconego obrazu na komputerze docelowym**  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Punkt **do programu Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench, przejdź do wdrożenia środowiska roboczego/wdrożenia udziałów/udział wdrożenia zestawu MDT (C:DeploymentShare$) / sekwencje zadań.  

3.  W okienku Akcje kliknij polecenie **nowej sekwencji zadań**.  

     Uruchamia Kreatora nowej sekwencji zadań.  

4.  Ukończ Kreatora nowej sekwencji zadań korzystając z poniższych informacji. Zaakceptuj wartości domyślne, chyba że określono inaczej.

    |**Na tej stronie kreatora**|**W tym**|  
    |-|-|  
    |**Ustawienia ogólne**|1.  W **identyfikator sekwencji zadań**, typ **WIN8_TARGET**.<br />2.  W **nazwę sekwencji zadań**, typ **wdrażania przechwyconych obrazów do komputera docelowego**.<br />3.  W **komentarze sekwencji zadań**, typ **sekwencję zadań pod kątem przechwycony obraz Windows 8.1 z komputera odniesienia (WDG-REF-01) do komputera docelowego (WDG-CLI-01)**.<br />4.  Kliknij przycisk **Dalej**.|  
    |**Wybierz szablon**|W **dostępne są następujące szablony sekwencji zadań**. **Wybierz ten, który chcesz użyć jako punktu wyjścia**, wybierz opcję standardowe **sekwencję zadań klienta**, a następnie kliknij przycisk **dalej**.|  
    |**Wybierz system operacyjny**|W **zawiera następujące obrazy systemu operacyjnego są dostępne do wdrożenia z tą sekwencją zadań**. **Wybierz jeden z nich do używania**, wybierz pozycję **WIN8_RERENCEDrive w "WIN8_REFERENCE\WIN8_REFERENCE.wim"**, a następnie kliknij przycisk **dalej**.|  
    |**Określ klucz produktu**|Kliknij przycisk **nie zostanie określony klucz produktu w tej chwili**, a następnie kliknij przycisk **dalej**.|  
    |**Ustawienia systemu operacyjnego**|1.  W **imię i nazwisko**, typ **pracownika banku Woodgrove**.<br />2.  W **organizacji**, typ **banku Woodgrove**.<br />3.  W **strona główna programu Internet Explorer**, typ **http://www.woodgrovebank.com**.<br />4.  Kliknij przycisk **Dalej**.|  
    |**Hasło administratora**|W **hasło administratora** i **Potwierdź hasło administratora**, typ  **P@ssw0rd** , a następnie kliknij przycisk **dalej**.|  
    |**Podsumowanie**|Kliknij przycisk **Dalej**.|  
    |**Postęp**|Zostanie wyświetlony pasek postępu tworzenia sekwencji zadań.|  
    |**Potwierdzenie**|Kliknij przycisk **Zakończ**.|  

     Po zakończeniu Kreatora sekwencji importu zadań i **WIN8_TARGET** sekwencja zadań zostanie dodany do listy sekwencji zadań.  

5.  Zamknij wszystkie otwarte okna i oknach dialogowych.  

## <a name="step-6-deploy-the-captured-image-of-the-reference-computer-to-the-target-computer"></a>Krok 6. Wdrażanie przechwycony obraz komputera odniesienia do komputera docelowego  
 Po przechwyceniu obrazu komputera odniesienia i utworzone i skonfigurowane sekwencji zadań odpowiednie wdrażania przechwyconego obrazu. Skonfiguruj zestawu MDT, aby podać wszystkie ustawienia konfiguracji niezbędne do wdrożenia na komputerze docelowym. Po zainicjowaniu procesu wdrażania, obraz komputera odniesienia z systemem Windows 8.1 jest wdrażany na komputerze docelowym i automatycznie skonfigurowane ustawienia zdefiniowane.  

 Przechwycony obraz komputera odniesienia należy wdrożyć na komputerze docelowym przez:  

-   Począwszy od LTI nośnika rozruchowego na komputerze docelowym i monitorować proces wdrożenia LTI, zgodnie z opisem w [krok 6-1: Uruchom komputer docelowy przy użyciu nośnika rozruchowego LTI](#StartTargetwithLTIBootable)  

###  <a name="StartTargetwithLTIBootable"></a>Krok 6-1. Uruchom komputer docelowy przy użyciu nośnika rozruchowego LTI  
 Uruchom komputer docelowy (WDG-CLI-01) z nośnika rozruchowego LTI utworzonego wcześniej w procesie. Ten dysk CD uruchamia środowisko Windows PE na komputerze docelowym i inicjuje wdrożenia. Po zakończeniu procesu Windows 8.1 jest wdrażany na komputerze docelowym.  

> [!NOTE]
>  Wdrożenia można także zainicjować przez uruchomienie komputera docelowego z usług wdrażania systemu Windows. Aby uzyskać więcej informacji, zobacz dokument MDT *przy użyciu programu Microsoft Deployment Toolkit*.  

 **Do uruchomienia komputera docelowego z nośnika rozruchowego LTI**  

1.  Uruchom WDG-CLI-01 z nośnika rozruchowego LTI utworzonego wcześniej w procesie.  

     Uruchamia środowisko Windows PE, a następnie uruchamia Kreatora wdrażania systemu Windows.  

2.  Ukończ pracę Kreatora wdrażania systemu Windows, korzystając z poniższych informacji. Zaakceptuj wartości domyślne, chyba że określono inaczej.   

    |**Na tej stronie kreatora**|**W tym**|  
    |-|-|  
    |**Welcome**|Kliknij przycisk **Uruchom Kreatora wdrażania, aby zainstalować nowy System operacyjny**.|  
    |**Poświadczenia**|1.  W **nazwy użytkownika**, typ **administratora**.<br />2.  W **hasło**, typ  **P@ssw0rd** .<br />3.  W **domeny**, typ **MDT2013**.<br />4.  Kliknij przycisk **OK**.|  
    |**Sekwencja zadań**|Kliknij przycisk **wdrażania przechwyconych obrazów do komputera docelowego**, a następnie kliknij przycisk **dalej**.|  
    |**Szczegóły komputera**|W **nazwy komputera**, typ **WDG-CLI-01**, a następnie kliknij przycisk **dalej**.|  
    |**Przenoszenia danych i ustawień**|Kliknij przycisk **Dalej**.|  
    |**Dane użytkownika (przywracanie)**|Kliknij przycisk **Dalej**.|  
    |**Ustawienia regionalne i czas**|**Kliknij przycisk Dalej**.|  
    |**Przechwycenie obrazu**|Kliknij przycisk **Dalej**.|  
    |**BitLocker**|Kliknij przycisk **Dalej**.|  
    |**Gotowe**|1.  Kliknij przycisk **szczegóły** do wyświetlania informacji podanych w kreatorze.<br />2.  Kliknij przycisk **rozpocząć**.|  

 Uruchamia kreatora, a następnie uruchamia wdrożenie systemu operacyjnego.  

 **Aby monitorować proces wdrażania komputera docelowego, wykonaj następujące czynności na WDG-MDT-01**  

1.  Na WDG-MDT-01, kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench przejdź do wdrożenia środowiska roboczego/wdrożenia udziałów/udział wdrożenia zestawu MDT (C:\DeploymentShare$)/Monitoring  

3.  W okienku Akcje kliknij okresowo **Odśwież**.  

4.  W okienku szczegółów wyświetlić proces wdrażania **WDG-CLI-01**.  

5.  W okienku Akcje kliknij okresowo **Odśwież**.  

     Stan procesu wdrażania jest aktualizowana w okienku szczegółów. Nadal monitorować proces wdrażania, aż do ukończenia procesu.  

6.  Zamknięcie konsoli Deployment Workbench.  

 **Aby ukończyć proces wdrażania komputera docelowego, wykonaj następujące czynności na WDG-CLI-01**  

1.  Na WDG-CLI-01 w **Wdrożęnia** okno dialogowe, kliknij przycisk **szczegóły**.  

     Jeśli występują jakiekolwiek błędy i ostrzeżenia, przejrzyj błędy lub ostrzeżenia i Zarejestruj wszystkie informacje diagnostyczne.  

2.  W **Wdrożęnia** okno dialogowe, kliknij przycisk **Zakończ**.  

 Po zakończeniu procesu wdrożenia zestawu MDT **podsumowanie wdrożenia** zostanie wyświetlone okno dialogowe. Obraz przechwycić z komputera odniesienia Windows 8.1 jest zainstalowany na komputerze docelowym. Jeśli występują jakiekolwiek błędy i ostrzeżenia, należy skontaktować się dokumentu MDT *Rozwiązywanie problemów z odwołania*.
