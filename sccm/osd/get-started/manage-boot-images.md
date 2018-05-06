---
title: 'Zarządzanie obrazami rozruchowymi '
titleSuffix: Configuration Manager
description: Dowiedz się, że w programie Configuration Manager do zarządzania obrazy rozruchowe Windows PE, używane podczas wdrażania systemu operacyjnego.
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: 97f2d81a-2c58-442c-88bc-defd5a1cd48f
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 6a2fe20896a781d7c897bd5a827d25a7b70390b7
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="manage-boot-images-with-system-center-configuration-manager"></a>Zarządzanie obrazami rozruchowymi przy użyciu programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Obraz rozruchowy w programie Configuration Manager jest [środowiska Windows PE](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-intro) obrazu (WinPE), który jest używany podczas wdrażania systemu operacyjnego. Obrazy rozruchowe są używane do uruchomienia komputera w środowisku WinPE. Ta minimalna wersja systemu operacyjnego zawiera ograniczoną listą składników i usług. Program Configuration Manager używa środowiska WinPE, aby przygotować komputer docelowy do instalacji systemu Windows. Poniższe sekcje umożliwiają zarządzanie obrazami rozruchowymi.

## <a name="BKMK_BootImageDefault"></a> Domyślne obrazy rozruchowe
Configuration Manager udostępnia dwa domyślne obrazy rozruchowe: Do obsługi x86 platform i jeden do obsługi x64 platform. Te obrazy są przechowywane w: \\ \\ *servername*> \SMS_ <*kod_lokacji*> \osd\boot\\<*x64*> lub <*i386*>. Domyślne obrazy rozruchowe są zaktualizowane lub ponownie wygenerowany w zależności od działanie, które należy podjąć.

Należy wziąć pod uwagę następujące zachowania do wykonywania czynności opisanych dla domyślne obrazy rozruchowe:
- Obiekty źródłowe sterowników muszą być prawidłowe. Te obiekty obejmują pliki źródłowe sterownika. Jeśli obiekty nie są prawidłowe, lokacji nie dodać sterowniki do obrazów rozruchowych.
- Obrazy rozruchowe, które nie są oparte na domyślne obrazy rozruchowe, nawet jeśli używają tej samej wersji systemu Windows PE nie są modyfikowane.
- Ponowna dystrybucja obrazów rozruchowych zmodyfikowane do punktów dystrybucji.
- Ponownie utwórz wszelkie nośnika, który korzysta z obrazów rozruchowych zmodyfikowane.
- Jeśli nie chcesz, aby dostosowane domyślne obrazy rozruchowe automatycznie aktualizowane, nie należy przechowywać je w lokalizacji domyślnej.

> [!NOTE]
> Configuration Manager Trace Log Tool (CMTrace) jest dodawany do wszystkich obrazów rozruchowych w **Biblioteka oprogramowania**. Podczas pracy w środowisku Windows PE, uruchom narzędzie, wpisując **CMTrace** z wiersza polecenia. Począwszy od wersji 1802, podczas uruchamiania cmtrace.exe w środowisku Windows PE, nie jest już monit o wybranie, czy to program domyślnej przeglądarki dla plików dziennika.

### <a name="use-updates-and-servicing-to-install-the-latest-version-of-configuration-manager"></a>Użyj aktualizacji i obsługi, aby zainstalować najnowszą wersję programu Configuration Manager
Począwszy od wersji 1702, kiedy uaktualnienie wersji systemu Windows Assessment and Deployment Kit (ADK), a następnie użyj aktualizacje i obsługa do zainstalowania najnowszej wersji programu Configuration Manager, lokacji generuje domyślne obrazy rozruchowe. Ta aktualizacja obejmuje nową wersję środowiska WinPE z zaktualizowany zestaw Windows ADK, nowa wersja klienta programu Configuration Manager, sterowników i dostosowania. Witryny nie modyfikuje niestandardowych obrazów rozruchowych.

Przed wersją 1702 programu Configuration Manager aktualizuje istniejący obraz rozruchowy przy użyciu składników klienta, sterowników i dostosowania, ale nie korzysta z najnowszej wersji środowiska WinPE z zestawu Windows ADK. Ręcznie zmodyfikować obraz rozruchowy do nowej wersji zestawu Windows adk.

### <a name="upgrade-from-configuration-manager-2012-to-configuration-manager-current-branch-cb"></a>Uaktualnianie z programu Configuration Manager 2012 do programu Configuration Manager bieżącego Branch (CB)
Po uaktualnieniu programu Configuration Manager 2012 CB programu Configuration Manager przy użyciu procesu instalacji lokacji generuje domyślne obrazy rozruchowe. Ta aktualizacja obejmuje nową wersję środowiska WinPE z zaktualizowany zestaw Windows ADK i nowej wersji klienta programu Configuration Manager. Wszystkie dostosowania obrazów rozruchowych pozostają niezmienione. Witryny nie modyfikuje niestandardowych obrazów rozruchowych.

### <a name="update-distribution-points-with-the-boot-image"></a>Aktualizuj punkty dystrybucji o obraz rozruchowy
Jeśli używasz **Aktualizuj punkty dystrybucji** akcji z **obrazów rozruchowych** węzeł w konsoli lokacji aktualizacji obrazu rozruchowego docelowego z składników klienta, sterowników i dostosowania.    

Począwszy od programu Configuration Manager w wersji 1706 ponownego załadowania obrazu rozruchowego z najnowszą wersję środowiska WinPE z katalogu instalacyjnego zestawu Windows ADK. **Ogólne** Kreatora aktualizacji punktów dystrybucji zawiera następujące informacje: 
 - Wersja zestawu Windows ADK zainstalowane na serwerze lokacji
 - Wersja zestawu Windows ADK środowiska WinPE w obrazie rozruchowym
 - Wersja klienta programu Configuration Manager dzięki tym informacjom można pomóc zdecydować, czy ponowne załadowanie z obrazu rozruchowego. **Obrazów rozruchowych** węzła zawiera również nową kolumnę do (**wersji klienta**). Aby szybko wyświetlić wersji klienta programu Configuration Manager w każdego obrazu rozruchowego, należy użyć tej kolumny.    


##  <a name="BKMK_BootImageCustom"></a> Dostosowanie obrazu rozruchowego  
 Jeśli obraz rozruchowy jest oparty na wersji środowiska WinPE z obsługiwanej wersji zestawu Windows adk, można dostosować lub [zmodyfikować obraz rozruchowy](#BKMK_ModifyBootImages) z konsoli. Po uaktualnieniu lokacji do nowej wersji i zainstalowaniu nowej wersji zestawu Windows adk, niestandardowe obrazy rozruchowe (nie w domyślnej lokalizacji obrazu rozruchowego) nie są zaktualizowane o nową wersję zestawu Windows adk. W takim przypadku nie można dostosować obrazy rozruchowe w konsoli programu Configuration Manager. Jednak nadal działają tak samo jak przed uaktualnieniem.  

 Jeśli obraz rozruchowy jest oparty na innej wersji zestawu Windows adk zainstalowany w lokacji, należy dostosować obrazy rozruchowe. Aby dostosować te obrazy rozruchowe, takie jak narzędzie wiersza polecenia Deployment Image Servicing and Management (DISM), należy użyć innej metody. Narzędzie DISM jest częścią zestawu Windows ADK. Aby uzyskać więcej informacji, zobacz [dostosowywanie obrazów rozruchowych](customize-boot-images.md).  

##  <a name="BKMK_AddBootImages"></a> Dodawanie obrazu rozruchowego  

 Podczas instalacji lokacji programu Configuration Manager automatycznie dodaje obrazy rozruchowe, które są oparte na wersji środowiska WinPE z obsługiwanej wersji zestawu Windows adk. W zależności od wersji programu Configuration Manager może być możliwe dodanie obrazów rozruchowych opartych na różnych wersjach środowiska WinPE z obsługiwanej wersji zestawu Windows ADK. Przy próbie dodania obrazu rozruchowego, który zawiera nieobsługiwaną wersję środowiska WinPE, wystąpi błąd. Poniżej znajduje się aktualnie obsługiwanych wersji zestawu Windows ADK i środowiska WinPE: 

-   **Wersja zestawu Windows ADK**  

     Windows ADK dla systemu Windows 10  

-   **Wersje systemu Windows PE dla obrazów rozruchowych modyfikowalnych z konsoli programu Configuration Manager**  

     Windows PE 10  

-   **Obsługiwane wersje systemu Windows PE dla obrazów rozruchowych modyfikowalnych z konsoli programu Configuration Manager**  

     Windows PE 3.1<sup>1</sup> i Windows PE 5  

     <sup>1</sup> można dodawać tylko obraz rozruchowy do programu Configuration Manager bazujące na środowisku Windows PE 3.1. Uaktualnij Windows AIK dla systemu Windows 7 (oparty na systemie Windows PE 3.0) z systemu Windows AIK dodatku dla systemu Windows 7 z dodatkiem SP1 (oparte na środowisku Windows PE 3.1). Pobierz uzupełnienie Windows AIK dla systemu Windows 7 z dodatkiem SP1 z [Centrum pobierania Microsoft](https://www.microsoft.com/download/details.aspx?id=5188).  

     Na przykład użyć konsoli programu Configuration Manager, aby dostosować obrazy rozruchowe oparte na systemie Windows PE 10 ADK systemu Windows dla systemu Windows 10. Obraz rozruchowy oparty na środowisku Windows PE 5 dostosowanie go z innego komputera przy użyciu wersji narzędzia DISM z zestawu ADK systemu Windows dla systemu Windows 8. Następnie dodaj niestandardowy obraz rozruchowy do konsoli programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [dostosowywanie obrazów rozruchowych](customize-boot-images.md).

 Użyj następującej procedury, aby dodać ręcznie obraz rozruchowy.  

#### <a name="to-add-a-boot-image"></a>Aby dodać obraz rozruchowy  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij pozycję **Obrazy rozruchowe**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Dodaj obraz rozruchowy**, aby uruchomić Kreatora dodawania obrazu rozruchowego.  

4.  Na stronie **Źródło danych** określ poniższe opcje, a następnie kliknij przycisk **Dalej**.  

    -   W polu **Ścieżka** wskaż ścieżkę do pliku WIM obrazu rozruchowego.  

         Określona ścieżka musi być prawidłową ścieżką sieciową w formacie UNC. For example: \\\\<*servername*\\<*sharename*>\\<*bootimagename*>.wim.  

    -   Wybierz obraz rozruchowy z listy rozwijanej **Obraz rozruchowy**. Jeśli plik WIM zawiera wiele obrazów rozruchowych, wybierz odpowiedni obraz.  

5.  Na stronie **Ogólne** określ poniższe opcje, a następnie kliknij przycisk **Dalej**.  

    -   W polu **Nazwa** określ unikatową nazwę obrazu rozruchowego.  

    -   W polu **Wersja** określ numer wersji obrazu rozruchowego.  

    -   W polu **Komentarz** podaj krótki opis sposobu używania obrazu rozruchowego.  

6.  Ukończ pracę kreatora.  

 Obraz rozruchowy zostanie wyświetlony w **obrazu rozruchowego** węzła konsoli programu Configuration Manager. Przed użyciem obrazu rozruchowego do wdrożenia systemu operacyjnego, należy przeprowadzić dystrybucję obrazu rozruchowego do punktów dystrybucji. 

> [!NOTE]  
>  W **obrazu rozruchowego** węzła konsoli, **rozmiar (KB)** kolumny Wyświetla zdekompresowanych rozmiar każdego obrazu rozruchowego. Gdy lokacji wysyła obraz rozruchowy przez sieć, wysyła skompresowanej kopii. Ta kopia jest zwykle mniejsze niż podany w **rozmiar (KB)** kolumny.  

##  <a name="BKMK_DistributeBootImages"></a> Dystrybuowanie obrazów rozruchowych do punktu dystrybucji  
 Dystrybucja obrazów rozruchowych do punktów dystrybucji przebiega tak samo, jak w przypadku zawartości innego typu. W większości przypadków musisz przeprowadzić dystrybucję obrazu rozruchowego do co najmniej jednego punktu dystrybucji przed wdrożeniem systemu operacyjnego i przed utworzeniem nośnika.   

> [!NOTE]  
> Aby użyć środowiska PXE do wdrażania systemu operacyjnego, należy wziąć pod uwagę następujące kwestie przed rozpoczęciem dystrybucji obrazu rozruchowego:  
> - Skonfiguruj punkt dystrybucji do akceptowania żądań PXE.  
> - Dystrybuuj x x86, jak i x64 obraz rozruchowy z włączoną funkcją PXE do punktu dystrybucji z włączoną funkcją PXE co najmniej jeden.  
> - Configuration Manager dystrybuuje obrazy rozruchowe do **RemoteInstall** folderu w punkcie dystrybucji z włączoną obsługą środowiska PXE.  
>   
> Aby uzyskać więcej informacji o używaniu środowiska PXE do wdrażania systemów operacyjnych, zobacz [przy użyciu środowiska PXE do wdrażania systemu Windows za pośrednictwem sieci](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  

 Aby zapoznać się z procedurą dystrybucji obrazu rozruchowego, zobacz [Dystrybucja zawartości](/sccm/core/servers/deploy/configure/deploy-and-manage-content#bkmk_distribute).  

##  <a name="BKMK_ModifyBootImages"></a> Modyfikowanie obrazu rozruchowego  
 Możesz dodać sterowniki urządzeń do obrazu, usunąć je z obrazu lub edytować właściwości skojarzone z obrazem rozruchowym. Dodawane lub usuwane sterowniki urządzeń mogą obejmować sterowniki kart sieciowych albo urządzeń pamięci masowych. Podczas modyfikowania obrazów rozruchowych należy uwzględnić następujące czynniki:  

-   Importowanie i włączyć sterowniki urządzeń w katalogu sterowników urządzeń przed dodaniem ich do obrazu rozruchowego.  

-   Podczas modyfikowania obraz rozruchowy nie zmienia żadnych skojarzonych pakietów, do których się odwołuje.  

-   Po wprowadzeniu zmian w obrazie rozruchowym, **aktualizacji** obraz rozruchowy w dystrybucji punktowi już go. Ten proces udostępnia najnowszej wersji obrazu rozruchowego do klientów. Aby uzyskać więcej informacji, zobacz [Zarządzanie dystrybuowaną zawartością](/sccm/core/servers/deploy/configure/deploy-and-manage-content#bkmk_manage).  

 Aby zmodyfikować obraz rozruchowy, wykonaj czynności opisane w poniższej procedurze.  

#### <a name="to-modify-the-properties-of-a-boot-image"></a>Aby zmodyfikować właściwości obrazu rozruchowego  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij pozycję **Obrazy rozruchowe**.  

3.  Wybierz obraz rozruchowy, który chcesz zmodyfikować.  

4.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**, aby otworzyć okno dialogowe **Właściwości** obrazu rozruchowego.  

5.  Dostosuj następujące ustawienia, aby zmienić zachowanie obrazu rozruchowego:  

    -   Na karcie **Obrazy**, jeśli zmieniono właściwości obrazu rozruchowego za pomocą zewnętrznego narzędzia, kliknij przycisk **Załaduj ponownie**.  

    -   Na karcie **Sterowniki** dodaj sterowniki urządzeń systemu Windows wymagane do rozruchu środowiska WinPE. Podczas dodawania sterowników urządzeń, należy wziąć pod uwagę następujące kwestie:  

        -   Wybierz **Ukryj sterowniki, które nie są zgodne z architekturą obrazu rozruchowego** można wyświetlić tylko sterowniki dla architektury obrazu rozruchowego. Architektura jest oparta na architekturze zgłoszonej w pliku INF od producenta.  

        -   Wybierz **Ukryj sterowniki, które nie należą do klasy sieci lub magazynu (na potrzeby obrazów rozruchowych)** Aby wyświetlić tylko sterowniki magazynów i sieci. Ta opcja powoduje ukrycie również inne sterowniki, które nie są zwykle wymagane przez obrazy rozruchowe, takie jak sterowniki wideo lub modemu.  

        -   Wybierz **Ukryj sterowniki, które nie są podpisane cyfrowo** Aby ukryć sterowniki, które nie mają prawidłowy podpis cyfrowy.  

        -   Najlepszym rozwiązaniem dodawać tylko sterowniki pamięci masowej i sieci do obrazu rozruchowego, chyba że nie jest wymagany w przypadku innych sterowników w środowisku WinPE.  

        -   Ponieważ środowisko WinPE zawiera już dużą liczbę sterowników, Dodaj tylko sieci i masowej sterowników magazynu, które nie są dostarczane przez środowisko WinPE.  

        -   Upewnij się, że sterowniki dodawane do obrazu rozruchowego są zgodne z architekturą obrazu rozruchowego.  

        > [!NOTE]  
        >  Przed dodaniem sterowników urządzeń do obrazu rozruchowego należy zaimportować je do katalogu sterowników. Aby uzyskać informacje o sposobie importowania sterowników urządzeń, zobacz [zarządzania sterownikami](manage-drivers.md).  

    -   Na karcie **Dostosowanie** wybierz jedno z poniższych ustawień:  

        -   Zaznacz pole wyboru **Włącz polecenia przeduruchomieniowe**, aby określić polecenie do uruchomienia przed uruchomieniem sekwencji zadań. Po włączeniu tej opcji, również określić wiersza polecenia do uruchomienia i obsługi plików wymaganych przez polecenie.  

            > [!WARNING]  
            >  Dodaj **cmd /c** do początku wiersza polecenia. Jeśli nie określisz **cmd /c**, polecenie nie będzie zamknięte po uruchomieniu. Wdrożenie nadal oczekuje na zakończenie polecenia i nie można uruchomić innych skonfigurowanych poleceń ani akcji.  

            > [!TIP]  
            >  Podczas tworzenia nośnika sekwencji zadań kreator zapisuje identyfikator pakietu i wiersz polecenia przeduruchomieniowego, z uwzględnieniem wartości wszelkich zmiennych sekwencji zadań, w pliku dziennika CreateTSMedia.log. Ten dziennik znajduje się na komputerze, na którym jest uruchomiona konsola programu Configuration Manager. Przejrzyj ten plik dziennika, aby sprawdzić wartości zmiennych sekwencji zadań.  

        -   Wybierz ustawienia pozycji **Tło Windows PE**, aby określić, czy ma być używane domyślne tło środowiska WinPE, czy tło niestandardowe.  

        -   Wybierz pozycję **Włącz obsługę poleceń (tylko testowanie)**, aby umożliwić otwieranie wiersza polecenia za pomocą klawisza **F8** podczas wdrażania obrazu rozruchowego. Ta opcja jest przydatna do rozwiązywania problemów podczas testowania wdrożenia. Korzystanie z tego ustawienia w środowisku produkcyjnym nie jest zalecane.  

        -   Skonfiguruj miejsce na pliki tymczasowe środowiska WinPE, stanowiące magazyn tymczasowy (dysk w pamięci RAM) używany przez środowisko WinPE. Jeśli na przykład aplikacja jest uruchamiana w środowisku WinPE i musi zapisać pliki tymczasowe, środowisko WinPE przekierowuje pliki do miejsca na pliki tymczasowe w pamięci, aby symulować obecność dysku twardego. Domyślnie środowisko WinPE przydziela 32 megabajty (MB) pamięci zapisywalnej.  

    -   Na karcie **Źródło danych** zaktualizuj dowolne z następujących ustawień:  

        -   Aby zmienić plik źródłowy obrazu rozruchowego, należy ustawić **ścieżka obrazu** i **indeks obrazu**.  

        -   Aby utworzyć harmonogram kiedy lokacja aktualizuje obrazu rozruchowego, wybierz **Aktualizuj punkty dystrybucji według harmonogramu**.  

        -   Jeśli nie chcesz, aby zawartość tego pakietu przedawniła się pamięci podręcznej klienta, aby zwolnić miejsce dla innej zawartości, wybierz **Utrwal zawartość w pamięci podręcznej klienta**.  

        -   Aby określić, że lokacji dystrybuuje tylko zmienionych plików po aktualizuje pakiet obrazu rozruchowego w punkcie dystrybucji, wybierz **Włącz binarną replikację różnicową** (BDR). To ustawienie minimalizuje ruch sieciowy między lokacjami. Replikacja BDR jest szczególnie przydatne, gdy pakiet obrazu rozruchowego jest duży, a zmiany względnie małe.  

        -   Jeśli używasz obrazu rozruchowego we wdrożeniu obsługującym środowisko PXE, zaznacz **Wdróż ten obraz rozruchowy z punktu dystrybucji obsługującego PXE**.  

            > [!NOTE]  
            >  Aby uzyskać więcej informacji, zobacz [przy użyciu środowiska PXE do wdrażania systemu Windows za pośrednictwem sieci](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  

    -   Na karcie **Dostęp do danych** wybierz dowolne z poniższych ustawień:  

        -   Ustaw **Ustawienia udziału pakietu**, jeżeli klienci mają instalować zawartość tego pakietu z sieci.  

        -   Ustaw **ustawienia aktualizacji pakietu** można określić, jak program Configuration Manager do odłączania użytkowników od punktu dystrybucji. Menedżer konfiguracji może być nie można zaktualizować obrazu rozruchowego, gdy użytkownicy są podłączeni do punktu dystrybucji.  

    -   Na karcie **Ustawienia dystrybucji** wybierz dowolne z poniższych ustawień:  

        -   W **priorytetu dystrybucji** Określ poziom priorytetu. Configuration Manager korzysta z tej listy Priorytet podczas lokacji dystrybuuje wiele pakietów do tego samego punktu dystrybucji.  

        -   Jeśli chcesz włączyć dystrybucję zawartości na żądanie do preferowanych punktów dystrybucji, wybierz opcję **Dystrybuuj zawartość tego pakietu do preferowanych punktów dystrybucji**. Po włączeniu tego ustawienia, jeśli klient zażąda zawartości pakietu, a zawartość nie jest dostępna w żadnych preferowanych punktach dystrybucji, a następnie punkt zarządzania dystrybuuje zawartość do wszystkich preferowanych punktów dystrybucji.  

        -   Aby określić, jak witryny, aby dystrybuować obraz rozruchowy do punktów dystrybucji, które są włączone dla wstępnie przygotowanej zawartości, należy ustawić **wstępnie przygotowane ustawienia punktu dystrybucji**.  

            > [!NOTE]  
            >  Aby uzyskać więcej informacji na temat wstępnie przygotowanej zawartości, zobacz [Wstępne przygotowanie zawartości](/sccm/core/servers/deploy/configure/deploy-and-manage-content#bkmk_prestage).  

    -   Na karcie **Lokalizacje zawartości** wybierz punkt dystrybucji lub grupę punktów dystrybucji i wykonaj jedną z następujących akcji:  

        -   Kliknij przycisk **Ponowna dystrybucja**, aby ponownie dystrybuować obraz rozruchowy do wybranego punktu dystrybucji lub grupy punktów dystrybucji.  

        -   Kliknij przycisk **Sprawdź poprawność**, aby sprawność integralność pakietu obrazu rozruchowego w wybranym punkcie dystrybucji lub grupie punktów dystrybucji.  

    -   Na **opcjonalnych składników** karcie, określ składniki dodane do systemu Windows PE do użytku z programem Configuration Manager. Aby uzyskać więcej informacji o dostępnych składnikach opcjonalnych, zobacz [WinPE: Dodawanie pakietów (opcjonalnych składnikach)](https://docs.microsoft.com/windows-hardware/manufacture/desktop/winpe-add-packages--optional-components-reference).  

    -   Na karcie **Zabezpieczenia** wybierz użytkownika administracyjnego i zmień operacje, jakie może wykonywać.  

6.  Po skonfigurowaniu właściwości kliknij przycisk **OK**.  

##  <a name="BKMK_BootImagePXE"></a> Konfigurowanie obrazu rozruchowego do wdrożenia z punktu dystrybucji obsługującego PXE  
 Przed użyciem obrazu rozruchowego środowiska PXE do wdrożenia systemu operacyjnego należy skonfigurować obraz rozruchowy do wdrożenia z punktu dystrybucji obsługującego środowisko PXE.  

#### <a name="to-configure-a-boot-image-to-deploy-from-a-pxe-enabled-distribution-point"></a>Aby skonfigurować obraz rozruchowy do wdrożenia z punktu dystrybucji obsługującego środowisko PXE  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym **Biblioteka oprogramowania** rozwiń węzeł **Systemy operacyjne**, a następnie kliknij pozycję **Obrazy rozruchowe**.  

3.  Wybierz obraz rozruchowy, który chcesz zmodyfikować.  

4.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**, aby otworzyć okno dialogowe **Właściwości** obrazu rozruchowego.  

5.  Na karcie **Źródło danych** wybierz pozycję **Wdróż ten obraz rozruchowy z punktu dystrybucji obsługującego środowisko PXE**.  

    > [!NOTE]  
    >  Aby uzyskać więcej informacji, zobacz [przy użyciu środowiska PXE do wdrażania systemu Windows za pośrednictwem sieci](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  

6.  Po skonfigurowaniu właściwości kliknij przycisk **OK**.  

##  <a name="BKMK_BootImageLanguage"></a> Konfigurowanie wielu języków dla wdrażania obrazu rozruchowego  
 Obrazy rozruchowe są niezależne od języka. Ta funkcja pozwala na użycie jednego obrazu rozruchowego, aby wyświetlić tekst sekwencji zadań w wielu językach znajduje się w środowisku WinPE. Obejmują obsługę odpowiedniego języka za pomocą obrazu rozruchowego **opcjonalnych składników** kartę. Następnie ustaw zmienną sekwencji zadań odpowiednie, aby wskazać, który język do wyświetlenia. Język wdrożony system operacyjny jest niezależny od języka w środowisku WinPE. Język środowiska WinPE wyświetla użytkownikowi jest określany w następujący sposób:  

-   Gdy użytkownik uruchamia sekwencję zadań z istniejącego systemu operacyjnego, programu Configuration Manager automatycznie używa języka skonfigurowanego dla użytkownika. Jeśli sekwencja zadań jest uruchamiana automatycznie w wyniku obowiązującego ostatecznego terminu wdrożenia, program Configuration Manager używa języka systemu operacyjnego.  

-   Dla wdrożeń systemu operacyjnego, które używają środowiska PXE lub nośnika, należy ustawić wartość Identyfikatora języka **SMSTSLanguageFolder** zmiennej jako część polecenia przeduruchomieniowego. Gdy komputer jest uruchamiany w środowisku WinPE, komunikaty są wyświetlane w języku określonym za pomocą zmiennej. Jeśli wystąpił błąd podczas uzyskiwania dostępu do pliku zasobów języka we wskazanym folderze lub nie ustawisz zmiennej, WinPE wyświetla komunikaty w języku domyślnym.  

    > [!NOTE]  
    >  Jeśli nośnik jest chroniony hasłem, tekst monitu o hasło jest zawsze wyświetlany w języku środowiska WinPE.  

 Aby ustawić język środowiska WinPE używany z wdrożeniami systemu operacyjnego za pomocą środowiska PXE lub inicjowanymi z nośników, wykonaj poniższą procedurę.  

#### <a name="to-set-the-windows-pe-language-for-a-pxe-or-media-initiated-operating-system-deployment"></a>Aby ustawić język systemu Windows PE używany z wdrożeniami systemu operacyjnego typu PXE lub inicjowanymi z nośników  

1.  Sprawdź, czy plik zasobów sekwencji odpowiednich zadań (tsres.dll) jest w folderze danego języka na serwerze lokacji, aby zaktualizować obrazu rozruchowego. Na przykład plik zasobów dla języka angielskiego znajduje się w następującej lokalizacji: <*Folder_instalacji_programu_configuration_manager*> \OSD\bin\x64\00000409\tsres.dll.  

2.  W ramach polecenia przeduruchomieniowego ustaw dla zmiennej środowiskowej SMSTSLanguageFolder identyfikator wybranego języka. Identyfikator języka musi być liczbą dziesiętną, a nie szesnastkową. Na przykład ustawić identyfikator języka na język angielski, należy określić wartość dziesiętną 1033, a nie wartość szesnastkową 00000409 nazwy folderu.  
