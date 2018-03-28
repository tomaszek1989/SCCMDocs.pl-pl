---
title: Instalacja na użytkownika
titleSuffix: Microsoft Deployment Toolkit
description: 'Przewodnik dla deweloperów dla użytkownika na instalację programu Microsoft Deployment Toolkit 2013. '
ms.date: 09/09/2016
ms.prod: configuration-manager
ms.technology:
- configmgr-osd
ms.topic: article
ms.assetid: a2b3a3a0-7b81-4191-b1f9-c618e59347c3
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 434178f100c32a4188ecf5283066f9332035f761
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2018
---
# <a name="user-driven-installation---developers-guide"></a>Instalacja — przewodnik dla deweloperów na użytkownika
Instalacja zmiennych użytkownika (UDI) ułatwia wdrożenie Windows® klienckie systemy operacyjne, takie jak Windows 8.1, na komputerach w Microsoft® System Center 2012 R2 Configuration Manager przy użyciu funkcji systemu operacyjnego (OSD) wdrożenia. UDI wchodzi w skład programu Microsoft Deployment Toolkit (MDT).  

## <a name="introduction"></a>Wprowadzenie  
 Zazwyczaj podczas wdrażania systemów operacyjnych za pomocą funkcji OSD, musisz podać wszystkie informacje niezbędne do wdrożenia systemu operacyjnego. Informacje jest skonfigurowany w plikach konfiguracji lub w bazach danych (na przykład plik CustomSettings.ini lub zestaw MDT bazy danych [MDT DB]). Należy podać wszystkie ustawienia konfiguracji przed rozpoczęciem wdrażania.  

 UDI zapewnia uruchamianej za pomocą Kreatora interfejsu, który umożliwia podanie informacji o konfiguracji bezpośrednio przed wykonaniem wdrożenia. To zachowanie umożliwia tworzenie rodzajowe sekwencje zadań wdrożenia systemu operacyjnego, a następnie podaj informacje dotyczące komputera w czasie wdrażania, co zapewnia większą elastyczność w procesie wdrażania.  

### <a name="target-audience"></a>Odbiorcy docelowi  
 Ten przewodnik jest przeznaczony dla deweloperów, którzy tworzenie stron kreatora niestandardowego kreatora UDI i edytory strony kreatora niestandardowego dla projektanta Kreatora instalacji UDI. W tym przewodniku założono, że czytelnik zna tworzenie aplikacji systemu Windows przy użyciu:  

-   C++, który jest używany do tworzenia stron kreatora niestandardowego  

-   Microsoft .NET Framework, który służy do tworzenia kreatora niestandardowych edytory  

-   Windows Presentation Foundation (WPF), który jest używany do tworzenia strony kreatora niestandardowego edytory  

-   Języki, które obsługuje WPF, takich jak C#, C++ i Microsoft Visual Basic .NET®, które są używane do tworzenia edytory strony kreatora niestandardowego  

### <a name="about-this-guide"></a>O tym przewodniku  
 Ten przewodnik zawiera informacje niezbędne do dostosowywania UTI dla Twojej organizacji. W tym przewodniku nie omówiono w nim tematy administracyjnych lub operacyjnych, takich jak instalowanie zestawu MDT (w tym UDI), konfigurowanie UDI do wdrażania systemów operacyjnych i aplikacji lub wykonywania wdrożeń za pomocą Kreatora UDI. Aby uzyskać więcej informacji o tych tematów, zobacz Tematy UDI w *przy użyciu programu Microsoft Deployment Toolkit*, która jest dostarczana z zestawu MDT.  

## <a name="udi-development-overview"></a>Omówienie tworzenia UDI  
 Programowanie UDI umożliwia rozszerzanie funkcji, które udostępnia UDI. Zazwyczaj programowanie UDI jest wymagana, aby zbierać dodatkowe informacje, który wykorzystuje UDI procesu wdrażania. Te informacje dodatkowe zwykle jest zapisywany jako zmienne sekwencji zadań, które kroki sekwencji zadań w UDI sekwencji zadań w programie Configuration Manager do odczytu.  

### <a name="udi-architecture"></a>Architektura UDI  
 Celem wysokiego poziomu rozwoju UDI jest do tworzenia kreatora niestandardowych stron, które mogą być wyświetlane w Kreatorze UDI. Tworząc stron kreatora niestandardowego i można rozszerzyć istniejące funkcje UDI w celu spełnienia tego wymagania techniczne firmy. Strona kreatora niestandardowego zbiera informacje oprócz lub zamiast stronach kreatora, które zapewnia UDI.  

 Rysunek 1 przedstawiono relację między kreatora UDI i projektanta Kreatora instalacji UDI.  

 ![UDIDevelopersGuide1](media/UDIDevelopersGuide1.jpg "UDIDevelopersGuide1")  
Rysunek 1. Relacja między UDI kreatora i projektanta Kreatora instalacji UDI  

 **Rysunek 1. Relacja między UDI kreatora i projektanta Kreatora instalacji UDI**  

 Na poziomie pojęciach programowanie UDI obejmuje tworzenie:  

-   **Strony kreatora niestandardowego**. Strony kreatora są wyświetlane w Kreatorze UDI i zbierać informacje wymagane do ukończenia procesu wdrażania. Możesz utworzyć za pomocą języka C++ w Microsoft Visual Studio® stron kreatora. Strony kreatora niestandardowego są zaimplementowane jako biblioteki dll, które odczytuje kreatora UDI. UDI zestaw software development kit (SDK) zawiera przykład sposobu tworzenia kreatora niestandardowych stron.  

-   **Edytory strony kreatora niestandardowego**. Edytory strony kreatora umożliwia konfigurowanie zachowania strony kreatora niestandardowego. Edytory strony kreatora niestandardowego są zaimplementowane jako biblioteki dll, które odczytuje projektanta Kreatora instalacji UDI. Strona kreatora tworzenia edytory przy użyciu:  

    -   [WPF](http://msdn.microsoft.com/library/ms754130.aspx) w wersji 4.0  

    -   [Microsoft Prism](http://compositewpf.codeplex.com/) w wersji 4.0  

    -   [Blok aplikacji platformy Unity Microsoft](http://unity.codeplex.com/) (Unity) w wersji 2.1  

     Zestaw MDT obejmuje wszystkie zestawy niezbędnych do utworzenia strony kreatora niestandardowego edytora do użycia w projektanta Kreatora instalacji UDI. UDI zestaw SDK zawiera przykładowy sposób tworzenia edytory strony kreatora niestandardowego.  

 Ponadto projektanta Kreatora instalacji UDI zużywa obsługi plików konfiguracyjnych Edytor strony kreatora. Edytor stron kreatora można tworzyć pliki konfiguracji w ramach procesu tworzenia kreatora niestandardowych stron i edytory strony kreatora niestandardowego. Projektanta Kreatora instalacji UDI tworzy niezbędne informacje XML w pliku konfiguracji kreatora UDI i odpowiadający mu plik .app.  

### <a name="preparing-the-udi-development-environment"></a>Przygotowywanie środowiska projektowego UDI  
 Przed rozpoczęciem tworzenia własnych stron kreatora niestandardowego i strona kreatora edytory, wykonaj następujące kroki, aby przygotować środowisko projektowe UDI:  

1.  Przygotowanie programowanie UDI wymagania wstępne dotyczące środowiska zgodnie z opisem w [przygotowanie wymagania wstępne dotyczące środowiska programowania UDI](#PrepareUDIDevelopmentEnvironmentPrerequisites).  

2.  Konfigurowanie środowiska programowania UDI zgodnie z opisem w [skonfigurować środowisko projektowe UDI](#ConfigureUDIDevelopmentEnvironment).  

3.  Sprawdź, czy środowisko projektowe UDI jest skonfigurowane poprawnie, zgodnie z opisem w [Sprawdź środowisko projektowe UDI](#VerifyUDIDeploymentEnvironment).  

####  <a name="PrepareUDIDevelopmentEnvironmentPrerequisites"></a> Przygotuj środowisko rozwoju UDI wstępnie wymagane składniki  
 Aby przygotować programowanie UDI wymagania wstępne dotyczące środowiska, wykonaj następujące czynności:  

1.  Przygotowanie warunek wstępny sprzętu środowisko rozwoju UDI zgodnie z opisem w [przygotowanie wymagania wstępne dotyczące UDI programowanie środowiska sprzętu](#PrepareUDIDevelopmentEnvironmentHardwarePrerequisites).  

2.  Przygotuj środowisko projektowe UDI warunek wstępny oprogramowania zgodnie z opisem w [przygotować wstępnie wymagane oprogramowanie środowisko rozwoju UDI](#PrepareUDIDevelopmentEnvironmentSoftwarePrerequisites).  

#####  <a name="PrepareUDIDevelopmentEnvironmentHardwarePrerequisites"></a> Przygotowanie UDI programowanie sprzętu wymagania wstępne dotyczące środowiska  
 Wymagania wstępne dotyczące UDI programowanie środowiska sprzętu są te same wymagania sprzętowe dla wersji programu Microsoft Visual Studio 2010 musisz za pomocą. Aby uzyskać więcej informacji na temat tych wymagań, zobacz wymagania systemowe dla poszczególnych wersji na [programu Visual Studio 2010 Products](http://www.microsoft.com/visualstudio/products/2010-editions).  

#####  <a name="PrepareUDIDevelopmentEnvironmentSoftwarePrerequisites"></a> Przygotowanie UDI rozwoju oprogramowania wymagania wstępne dotyczące środowiska  
 Środowisko projektowe UDI ma następujące wstępnie wymagane oprogramowanie:  

-   Oknami systemu operacyjnego obsługiwane przez program Visual Studio 2010 (Windows 7 lub Windows Server® 2008 R2 jest zalecane.)  

     Konieczne będzie systemu operacyjnego, który obsługuje architektury procesora, dla której chcesz utworzyć. Można wykonywać 32-bitowe i 64-bitowe programowanie UDI przy użyciu 64-bitowym systemie operacyjnym. Czynność programowanie UDI 32-bitowego w 32-bitowych systemach operacyjnych. Z tego powodu należy używać 64-bitowym systemie operacyjnym.  

    > [!NOTE]
    >  Wersje IntelItanium (IA-64) systemu operacyjnego Windows nie są obsługiwane dla środowisk deweloperskich UDI.  

     Aby uzyskać więcej informacji o systemach operacyjnych obsługiwanych przez program Visual Studio 2010, zobacz wymagania systemowe dla poszczególnych wersji na [programu Visual Studio 2010 Products](http://www.microsoft.com/visualstudio/products/2010-editions).  

-   Microsoft .NET Framework w wersji 4.0 (wymaganego przez program Visual Studio 2010)  

-   Języka C++ (języka używanego w rozszerzanie stron kreatora UDI)  

-   Inne języki tego WPF obsługuje, takich jak C#, Visual Basic .NET lub C + +/ wspólną infrastrukturę języka, które służą do rozszerzania projektanta Kreatora instalacji UDI edytory strony kreatora  

    > [!NOTE]
    >  Przykładowy kod źródłowy dla edytory strony kreatora projektanta Kreatora instalacji UDI jest napisany w języku C#. Instalowanie języka C#, jeśli chcesz użyć przykładowego kodu źródłowego.  

####  <a name="ConfigureUDIDevelopmentEnvironment"></a> Konfigurowanie środowiska programowania UDI  
 Po UDI następnie są spełnione wymagania wstępne dotyczące środowiska programowania, wykonaj następujące kroki, aby skonfigurować środowisko projektowe UDI:  

1.  Zainstaluj program Visual Studio 2010.  

     Pamiętaj, aby zainstalować język C++ i dowolnego języka, który obsługuje WPF.  

    > [!NOTE]
    >  Przykładowy kod źródłowy stron Edytor projektanta Kreatora instalacji UDI jest napisany w języku C#. Instalowanie języka C#, jeśli chcesz użyć przykładowego kodu źródłowego.  

     Aby uzyskać więcej informacji na temat instalowania programu Visual Studio 2010, zobacz [Instalowanie programu Visual Studio](http://msdn.microsoft.com/library/e2h7fzkw.aspx).  

2.  Instalowanie zestawu MDT.  

     Aby uzyskać więcej informacji na temat instalacji zestawu MDT, zobacz sekcję "Instalowanie lub uaktualnianie do zestawu MDT", w zestawie MDT dokumentu *przy użyciu programu Microsoft Deployment Toolkit*.  

3.  W Eksploratorze Windows, Utwórz *local_folder* (gdzie *local_folder* jest dowolnego folderu znajdującego się na dysk lokalny na komputerze dewelopera).  

4.  Kopiuj *installation_folder*\SDK folder *local_folder* (gdzie *installation_folder* to folder, w którym jest zainstalowany zestaw MDT i *local_ folder* jest dowolnego folderu znajdującego się na dysk lokalny na komputerze dewelopera).  

     Możesz skopiować folderu zestawu SDK do innej lokalizacji, ponieważ zestaw MDT jest instalowana w folderze Program Files, którego nie można zapisać bez podniesionego poziomu uprawnień. Kopiowanie folderu zestawu SDK do innej lokalizacji umożliwia modyfikowanie plików w folderze SDK bez podniesionego poziomu uprawnień.  

5.  Kopiuj *installation_folder*\Templates\Distribution\Tools folder *local_folder* (gdzie *installation_folder* to folder, w którym jest zainstalowany zestaw MDT i *local_folder* jest folder utworzony wcześniej w procesie).  

6.  Zmień nazwę *local_folder*folderu \Tools *local_folder*\OSDSetupWizard (gdzie *local_folder* jest folder utworzony wcześniej w procesie).  

     Po zakończeniu tej struktury folderów poniżej *local_folder* powinna wyglądać struktury folderów przedstawiono na rysunku 2 (gdzie *local_folder* jest folder utworzony wcześniej w trakcie procesu i jest wyświetlane jako *UDIDevelopment* na rysunku).  

     ![UDIDevelopersGuide2](media/UDIDevelopersGuide2.jpg "UDIDevelopersGuide2")  
Rysunek 2. Struktura folderów dla rozwoju UDI  

     **Rysunek 2. Struktura folderów dla rozwoju UDI**  

####  <a name="VerifyUDIDeploymentEnvironment"></a> Sprawdź UDI Środowisko deweloperskie  
 Po skonfigurowaniu środowiska projektowego UDI, sprawdzić poprawność konfiguracji środowiska programowania UDI przez zapewnienie, że przykładowych projektach prawidłowej kompilacji programu Visual Studio 2010.  

 Sprawdzić poprawność konfiguracji środowiska programowania UDI przez określenie czy:  

-   Poprawnie zgodnie z opisem w temacie Tworzenie projektów SamplePage [upewnij się, że poprawnie tworzenie projektów SamplePage](#VerifySamplePageProjectBuildsCorrectly)  

-   Poprawnie zgodnie z opisem w temacie Tworzenie projektów SampleEditor [upewnij się, że poprawnie tworzenie projektów SampleEditor](#VerifySampleEditorProjectBuildsCorrectly)  

#####  <a name="VerifySamplePageProjectBuildsCorrectly"></a> Sprawdź poprawnie tworzenie projektów SamplePage  
 Projekt SamplePage przedstawiono przykład sposobu tworzenia strony kreatora niestandardowego kreatora UDI. Aby uzyskać więcej informacji o projekcie SamplePage, zobacz [Przejrzyj rozwiązania Visual Studio SamplePage](#ReviewSamplePageVisualStudioSolution).  

 **Aby sprawdzić poprawnie tworzenie projektów SamplePage**  

1.  Uruchom program Visual Studio 2010.  

2.  Otwórz projekt SamplePage.  

     Projekt SamplePage znajduje się w *local_folder*\SDK\UDI\SamplePage folder (gdzie *local_folder* jest folder utworzony wcześniej w procesie).  

3.  W programie Visual Studio 2010, w Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt SamplePage, a następnie kliknij przycisk **właściwości**.  

     **Strony właściwości SamplePage** zostanie wyświetlone okno dialogowe.  

4.  W **strony właściwości SamplePage** okno dialogowe, przejdź do Konfiguracja właściwości/debugowanie.  

5.  W oknie właściwości debugowania w obszarze **konfiguracji**, wybierz pozycję **wszystkie konfiguracje**.  

6.  W oknie właściwości debugowania w obszarze **polecenia**, typ **$(TargetDir)\OSDSetupWizard.exe.**  

7.  W oknie właściwości debugowania w obszarze **katalog roboczy**, typ **$(targetdir) —**.  

8.  W **strony właściwości SamplePage** okno dialogowe, przejdź do Konfiguracja właściwości/zdarzenia/po kompilacji — zdarzenie kompilacji.  

9. We właściwościach zdarzenia Postkompilacyjnego w obszarze **wiersza polecenia**, wpisz następujące polecenie:  

    ```  
    copy /y "$(ProjectDir)..\..\..\..\OSDSetupWizard\x86\*.*" "$(TargetDir)"  
    xcopy /y /i "$(ProjectDir)..\..\..\..\OSDSetupWizard\x86\en-us" "$(TargetDir)en-us"  
    copy /y "$(ProjectDir)..\..\..\..\OSDSetupWizard\OSDResults\Images\UDI_Wizard_Banner.bmp" "$(ProjectDir)header.bmp"  
    copy /y "$(ProjectDir)Config.xml" "$(TargetDir)”  
    copy /y "$(ProjectDir)header.bmp" "$(TargetDir)header.bmp"  
    ```  

10. W **strony właściwości SamplePage** okno dialogowe, kliknij przycisk **OK**.  

11. Zapisz projekt.  

12. Z **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie**.  

     **Programu Microsoft Visual Studio**wyświetlone okno dialogowe informujące, że jest nieaktualny i zapyta, czy chcesz skompilować projekt.  

13. W **programu Microsoft Visual Studio** okno dialogowe, kliknij przycisk **tak**.  

     **Informacji o debugowaniu nie** zostanie wyświetlone okno dialogowe informujące, że informacje debugowania są niedostępne dla OSDSetupWizard.exe.  

14. W **informacji o debugowaniu nie** okno dialogowe, kliknij przycisk **tak**.  

     Na stronie kreatora niestandardowego wyświetlane zostanie otwarty Kreator UDI.  

15. Sprawdź, czy należy wybrać wartość w **wybierz lokalizację**.  

16. W **kreatora z przykładową stronę** kliknij przycisk **anulować**.  

     **Anuluj kreatora** zostanie wyświetlone okno dialogowe.  

17. W **Anuluj kreatora** okno dialogowe, kliknij przycisk **tak**.  

18. Close Visual Studio 2010.  

#####  <a name="VerifySampleEditorProjectBuildsCorrectly"></a> Sprawdź poprawnie tworzenie projektów SampleEditor  
 Projekt SampleEditor przedstawiono przykład sposobu tworzenia edytorze strony kreatora niestandardowego dla projektanta Kreatora instalacji UDI. Aby uzyskać więcej informacji o projekcie SampleEditor, zobacz [Przejrzyj rozwiązania Visual Studio SamplePage](#ReviewSamplePageVisualStudioSolution).  

 **Aby sprawdzić poprawnie tworzenie projektów SampleEditor**  

1.  Uruchom program Visual Studio 2010.  

2.  Otwórz projekt SampleEditor.  

     Projekt SampleEditor znajduje się w *local_folder*\SDK\UDI\SampleEditor folder (gdzie *local_folder* jest folder utworzony wcześniej w procesie).  

3.  W programie Visual Studio 2010, w Eksploratorze rozwiązań wybierz projekt SampleEditor.  

4.  Z **projektu** menu, kliknij przycisk **Dodaj odwołanie**.  

     **Dodaj odwołanie** zostanie otwarte okno dialogowe.  

5.  W **Dodaj odwołanie** okno dialogowe, kliknij przycisk **Przeglądaj** kartę.  

6.  Na **Przeglądaj** kartę, przejdź do *installation_folder*\Bin (gdzie *installation_folder* to folder, w którym jest zainstalowany zestaw MDT). Wybierz następujące pliki, a następnie kliknij przycisk **OK**:  

    -   Microsoft.Enterprise.UDIDesigner.Common.dll  

    -   Microsoft.Enterprise.UDIDesigner.DataService.dll  

    -   Microsoft.Enterprise.UDIDesigner.Infrastructure.dll  

    -   Microsoft.Practices.Prism.dll  

    -   Microsoft.Practices.ServiceLocation.dll  

    -   Microsoft.Practices.Unity.dll  

    -   RibbonControlsLibrary.dll  

    > [!NOTE]
    >  Można wybrać wiele plików na **Przeglądaj** kartę, przytrzymując klawisz CTRL podczas klikania plików.  

7.  W Eksploratorze rozwiązań przejdź do SampleEditor/odwołania.  

8.  Sprawdź, czy żaden z odwołania nie ma żadnych ostrzeżeń ani błędów.  

9. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy projekt SampleEditor, a następnie kliknij przycisk **właściwości**.  

     **Strony właściwości SampleEditor** zostanie wyświetlone okno dialogowe.  

10. W **strony właściwości SampleEditor** okno dialogowe, kliknij przycisk **debugowania** kartę.  

11. Na **debugowania** , kliknij pozycję **uruchomienia programu zewnętrznego**.  

12. W **uruchomienia programu zewnętrznego**, typ ***installation_folder\Bin\UDIDesigner.exe*** (gdzie *installation_folder* to folder, w którym jest zainstalowany zestaw MDT), a następnie kliknij przycisk **OK**.  

    > [!TIP]
    >  Kliknięcie przycisku wielokropka (...), przejdź do folderu i wybierz UDIDesigner.exe.  

13. Z **pliku** menu, kliknij przycisk **Zapisz wszystko**.  

14. Kopiowania *local_folder*pliku \SDK\SamplePage\SamplePage.dll.config *installation_folder*\Bin\Config folderu (gdzie *local_folder* to folder, możesz utworzona na komputerze dewelopera wcześniej w trakcie procesu konfiguracji i*installation_folder* to folder, w którym jest zainstalowany zestaw MDT).  

15. W programie Visual Studio 2010 z **debugowania** menu, kliknij przycisk **Rozpocznij debugowanie**.  

     Uruchamia projektanta Kreatora instalacji UDI.  

16. W projektanta Kreatora instalacji UDI na wstążce kliknij **Otwórz**.  

     **Otwórz** zostanie wyświetlone okno dialogowe.  

17. W **Otwórz** okno dialogowe, otwórz *local_folder*\SDK\SamplePage\SamplePage\Config.xml pliku (gdzie *local_folder* jest folder utworzony w rozwoju komputer wcześniej w trakcie procesu konfiguracji).  

     Plik Config.xml, plik zostanie otwarty i niestandardowej [StageGroup](#StageGroup) jest wyświetlany w okienku szczegółów.  

18. W okienku szczegółów kliknij **Konfiguruj** kartę.  

19. Przejrzyj informacje o konfiguracji **lokalizacji** pola, w tym następujące:  

    -   **Odblokowany** przycisku, z którym można włączyć lub wyłączyć **lokalizacji** pole  

    -   **Wartość domyślna** pola, w którym należy wprowadzić wartość domyślną, który będzie wyświetlany w **lokalizacji** pole  

    -   **Przyjazną nazwę wyświetlaną widoczne na stronie podsumowania**, w którym możesz wprowadzić podpis dla informacji wyświetlanych na **podsumowania** strony  

    -   **Lokalizacja** polu listy, która zawiera listę możliwych lokalizacji  

20. Zamknij projektanta Kreatora instalacji UDI.  

21. Close Visual Studio 2010.  

## <a name="reviewing-the-udi-sdk-examples"></a>Przegląd przykładów UDI SDK  
 Przed rozpoczęciem tworzenia, przejrzyj przykłady podane w zestawie SDK UDI. Użyj informacji w tym przewodniku i kod źródłowy w przykładach ułatwiające tworzenie własnych stron kreatora niestandardowego UDI i strona kreatora edytory.  

 Przejdź przez przykłady UDI zestawu SDK, przeglądając:  

-   Zawartość folderu zestawu SDK skopiowanego wcześniej w procesie instalacji, zgodnie z opisem w [Przejrzyj zawartość folderu zestawu SDK](#ReviewContentsofSDKFolder)  

-   Przykład strony kreatora UDI niestandardowego zgodnie z opisem w [Przejrzyj SamplePage rozwiązania Visual Studio](#ReviewSamplePageVisualStudioSolution)  

-   Niestandardowe UDI Kreatora strony Edytor przykład zgodnie z opisem w [Przejrzyj SampleEditor rozwiązania Visual Studio](#ReviewSampleEditorVisualStudioSolution)  

###  <a name="ReviewContentsofSDKFolder"></a> Przejrzyj zawartość folderu zestawu SDK  
 Podczas konfigurowania środowiska deweloperskiego UDI folderu zestawu SDK jest skopiowany z folderu zainstalowano zestaw MDT do innego folderu, który został utworzony. Tabela 1 zawiera foldery natychmiast poniżej folderu zestawu SDK i zawiera krótki opis każdego z nich.  

### <a name="table-1-folders-in-the-udi-sdk"></a>Tabela 1. Foldery w zestawie SDK UDI  

|**Folder**|**Ten folder zawiera**|  
|-|-|  
|Zawiera|Pliki nagłówkowe C++ niezbędne do tworzenia kreatora niestandardowych stron kreatora UDI|  
|Biblioteki|Pliki biblioteki języka C++, połączone z niestandardowej strony; istnieje 32-bitowe i 64-bitowe wersje biblioteki dołączanej statycznie. **Uwaga:**  Itanium wersje bibliotek (IA-64) są niedostępne.|  
|SampleEditor|Projektu programu Visual Studio umożliwiające tworzenie niestandardowego edytora używane do edycji strony SamplePage w projektanta Kreatora instalacji UDI, który jest napisany w języku C#|  
|SamplePage|Projektu programu Visual Studio umożliwiające tworzenie niestandardowej strony kreatora UDI, który jest zapisany w programie Visual C++|  

###  <a name="ReviewSamplePageVisualStudioSolution"></a> Przejrzyj rozwiązania SamplePage Visual Studio  
 Przed rozpoczęciem tworzenia kreatora niestandardowych stron i strona kreatora edytory, wykonaj następujące zadania, aby przygotować środowisko projektowe UDI:  

-   Przejrzyj etapy cyklu życia strony kreatora UDI zgodnie z opisem w [Przegląd cyklu życia strony kreatora](#ReviewWizardPageLifeCycle).  

-   Przejrzyj rozwiązania Visual Studio, na przykład SamplePage w zestawie SDK UDI zgodnie z opisem w [Przejrzyj przykład SamplePage](#ReviewSamplePageExample).  

####  <a name="ReviewWizardPageLifeCycle"></a> Przegląd cyklu życia strony kreatora  
 Strona kreatora UDI ma metody, które odpowiadają każdego etapu (lub fazy) cyklu życia strony. W ramach tworzenia strony kreatora niestandardowego należy zastąpić te metody z kodu. Tabela 2 zawiera listę metod, należy zastąpić i zawiera krótki opis poszczególnych metod, w tym, kiedy należy użyć metody w cyklu życia strony kreatora.  

### <a name="table-2-methods-in-a-wizard-page-life-cycle"></a>Tabela 2. Metody w kreatorze strony cykl życia  

|**— Metoda**|**Opis**|  
|-|-|  
|**OnWindowCreated**|Ta metoda jest wywoływana raz, po utworzeniu strony okna.<br /><br /> W przypadku tej metody pisania kodu, który inicjuje stronę po raz pierwszy, a tylko musi zostać wykonana na raz. Na przykład użyć tej metody można zainicjować pól lub odczytać informacji z **metody ustawiającej** elementów w pliku konfiguracyjnym UDI kreatora.|  
|**OnWindowShown**|Ta metoda jest wywoływana za każdym razem, wyświetlania strony (widoczne), w Kreatorze UDI. Jest to strona jest wyświetlana po raz pierwszy i za każdym razem, przejdź do strony, klikając **dalej** lub **ponownie** w kreatorze.<br /><br /> Tę metodę należy napisać kod, który przygotowuje stronę do wyświetlenia — na przykład Odczyt zmienne pamięci, zmienne sekwencji zadań lub zmiennych środowiskowych, a następnie zaktualizować strony na podstawie wszelkich zmian do tych zmiennych.|  
|**OnCommonControlEvent**|Tę metodę można wywołać w dowolnym momencie strona kreatora jest wyświetlana i odbiera komunikat WM_NOTIFY z elementem podrzędnym (zazwyczaj typowe kontrolki).<br /><br /> W przypadku tej metody pisania kodu, który obsługuje na podstawie komunikatu powiadomienia WM_NOTIFY. Na przykład może być odpowiadanie na zdarzenia z formantu wspólnego, takich jak odpowiada kliknij lub kliknij dwukrotnie zdarzenia **TreeView** formantu.|  
|**OnUnhandledEvent**|Ta metoda jest wywoływana przy każdym okna nieobsługiwany komunikat jest wyświetlany na stronie kreatora. Ta metoda zapewnia możliwość przechwytywać i obsługiwać je w przeciwnym razie nieobsługiwany komunikaty okna.<br /><br /> W przypadku tej metody należy napisać kod, który obsługuje komunikaty okna, które są odpowiednie do strony kreatora. Zwykle nie należy przesłonić tę metodę.|  
|**OnNextClicked**|Ta metoda jest wywoływana po kliknięciu **dalej** w kreatorze.<br /><br /> W przypadku tej metody należy napisać kod, który wykonuje wszystkie akcje niezbędne przed przejściem do następnej strony kreatora — na przykład, wykonywanie weryfikacji, który może zająć dużo czasu. W przypadku niepowodzenia weryfikacji, możesz anulować **dalej** żądania i wyświetlić wiadomość.|  
|**OnWindowHidden**|Ta metoda jest wywoływana zawsze, gdy strona jest ukryty, gdy jest wyświetlana strona kreatora poprzedniego lub następnego.<br /><br /> Tę metodę należy napisać kod, który wykonuje wszystkie akcje przed strony jest ukryty przed innej strony jest pokazywany. Zwykle nie należy przesłonić tę metodę.|  

####  <a name="ReviewSamplePageExample"></a> Przejrzyj przykład SamplePage  
 Przejrzyj przykład SamplePage przy użyciu poniższej listy reprezentuje sekwencję zdarzeń cyklu życia strony kreatora przykładu SamplePage:  

1.  Kreator UDI, OSDSetupWizard.exe, odczytuje informacje o konfiguracji z pliku konfiguracji kreatora UDI w przykładzie (pliku Config.xml) zgodnie z opisem w [krok 1: Kreator UDI (OSDSetupWizard.exe) odczytuje plik Config.xml](#UDIWizardReadstheConfigFile).  

2.  Kreator UDI ładuje bibliotek DLL wymaganych dla każdej z wymienionych w pliku konfiguracji kreatora UDI zgodnie z opisem w stron kreatora [krok 2: Kreator UDI ładuje bibliotekę DLL na stronie kreatora niestandardowego](#UDIWizardLoadstheDLLforCustomWizardPage).  

3.  Kreator UDI zostanie wyświetlona strona kreatora niestandardowego i pozwala na współdziałanie żądanego formantu, zgodnie z opisem w [krok 3: Kreator UDI zostanie wyświetlona strona kreatora niestandardowego](#UDIWizardDisplaysCustomWizardPage).  

4.  Po stronie kreatora niestandardowego zebrał informacje, należy wykonać wszystkie zadania, które są niezbędne przed kliknięciem przycisku **dalej** do przejścia do następnej kreatora zgodnie z opisem w [krok 4: Kliknięciu przycisku Dalej na stronie kreatora niestandardowego](#TheNextButtonisClickedinCustomWizardPage).  

#####  <a name="UDIWizardReadstheConfigFile"></a> Krok 1. Kreator UDI (OSDSetupWizard.exe) odczytuje plik Config.xml  
 Po uruchomieniu kreatora UDI (OSDSetupWizard.exe), domyślnie jest odczytywana plik konfiguracyjny UDI kreatora, który jest plikiem UDIWizard_Config.xml — plik konfiguracji podstawowej dla Kreatora UDI.  

> [!NOTE]
>  W przykładzie użyto pliku Config.xml w pliku konfiguracji. W zestawie MDT domyślny plik konfiguracji jest plik UDIWizard_Config.xml, który znajduje się w folderze skryptów w pakiecie zestawu MDT plików konfiguracji.  

 Można zastąpić domyślny plik konfiguracji kreatora UDI używa modyfikując kroku sekwencji zadań w Kreatorze UDI do użycia **/definition** parametru. Aby uzyskać więcej informacji na temat zastępowania domyślny plik konfiguracji, który korzysta z Kreatora UDI zobacz "Override konfiguracji pliku UDI kreatora używającą".  

 Są elementów najwyższego poziomu w pliku Config.xml  

-   [Biblioteki dll](#DLLs) — element  

-   [Styl](#Style) — element  

-   [Strony](#Pages) — element  

-   [StageGroups](#StageGroups) — element  

 Aby uzyskać więcej informacji na temat schematu pliku konfiguracji kreatora UDI i każdy z tych elementów, zobacz [odwołania schematu pliku konfiguracji kreatora UDI](#UDIWizardConfigurationFileSchemaReference).  

 Kreator UDI skanuje **biblioteki dll** wyszukiwanie plików .dll, które można załadować elementu. W tym przykładzie są wyświetlane dwa pliki dll: SamplePage.dll i SharedPages.dll. Te pliki dll musi znajdować się w tym samym folderze co narzędzia OSDSetupWizard.exe—the\\*platformy* folder (gdzie *platformy* x86 w 32-bitowej wersji lub x64 dla 64-bitowej wersji).  

 Kreator UDI skanuje **stron** element wyszukiwania dla stron, które zostały zdefiniowane. W tym przykładzie zdefiniowano dwie strony: **Niestandardowe** i **SummaryPage**. **Typu** atrybutu **strony** element jest zdefiniowana w pliku PageClassIDs.h i unikatowo określa typ niestandardowej strony.  

 W tym przykładzie jest zdefiniowanym typem **Microsoft.SamplePage.LocationPage**. Niestandardowe strony Zastąp następujące polecenie, aby uniknąć potencjalne konflikty z innych stron, które mogą zostać utworzone w przyszłości:  

-   Nazwa organizacji zamiast z **Microsoft**.  

-   Nazwę projektu zamiast elementu **SamplePage**.  

-   Nazwę strony kreatora niestandardowego zamiast z **LocationPage**.  

#####  <a name="UDIWizardLoadstheDLLforCustomWizardPage"></a> Krok 2. Kreator UDI ładuje bibliotekę DLL na stronie kreatora niestandardowego  
 Podczas ładowania biblioteki DLL Kreatora UDI wywołuje **RegisterFactories** funkcji, która musi zostać wdrożone w pliku dll. W tym przykładzie tej funkcji jest zaimplementowana w pliku dllmain.ccp. Każdej stronie Kreatora tworzenia musi implementować **RegisterFactories** funkcji.  

 **RegisterFactories** funkcja jest używana do zarejestrowania fabryki klasy strony kreatora z rejestru fabryki klasy dla Kreatora UDI. *Fabryki klas* są klasy, które można utworzyć wystąpienia innej klasy. **RegisterFactories** funkcja tworzy nowe wystąpienie klasy fabryki i przekazuje tej klasy w rejestrze fabryki klasy dla Kreatora UDI, który udostępnia fabrykę klas do kreatora. Kreator UDI szuka klasę fabryki zarejestrowany identyfikator, który odpowiada **typu** atrybutu **strony** elementu na stronie kreatora niestandardowego.  

 W tym przykładzie identyfikator jest zdefiniowany jako **ID_Location** w pliku PageClassIds.h jako **Microsoft.SamplePage.LocationPage**, odpowiadający identyfikatorowi **typu** atrybutu  **Strona** elementu w pliku Config.xml. **ID_Location** jest przekazywana jako parametr w **RegisterFactories** funkcja zaimplementowana w pliku dllmain.ccp.  

 Można utworzyć funkcji za pomocą Register_*nazwa* szablonu funkcji, aby uprościć tworzenie nowego wystąpienia fabryki i zarejestrować nowo utworzone wystąpienie. **Nazwa** wartość przy użyciu szablonu funkcji rejestru musi implementować **iClassFactory** interfejsu. [Klasy ClassFactoryImpl](#ClassFactoryImplClass) obsługuje większość szczegóły dotyczące implementowania fabrykę klas.  

 Można również użyć **RegisterFactories** funkcji, aby zarejestrować typy zadań i modułu sprawdzania poprawności. Aby uzyskać więcej informacji, zobacz następujące tematy:  

-   [Tworzenie niestandardowych UDI zadań](#CreatingCustomUDITasks)  

-   [Tworzenie niestandardowych UDI modułów sprawdzania poprawności](#CreatingCustomUDIValidators)  

> [!NOTE]
>  W przykładzie zawiera i rejestruje tylko jedną stronę kreatora niestandardowego. W przykładzie nie ma niestandardowych zadań lub moduły weryfikacji i dlatego nie rejestruje żadnych niestandardowych zadań lub moduły weryfikacji.  

#####  <a name="UDIWizardDisplaysCustomWizardPage"></a> Krok 3. Kreator UDI zostanie wyświetlona strona kreatora niestandardowego  
 Strona kreatora niestandardowego, w tym przykładzie jest zdefiniowana w pliku LocationPage.cpp. Strony kreatora są uzyskiwane z szablonu klasy, które zapewniają ma wiele funkcji strony. Wszystkie strony kreatora powinien pochodzić od [WizardPageImpl szablonu klasy](#WizardPageImplTemplateClass), który implementuje [IWizardPage interfejsu](#IWizardPageInterface). Każdej stronie kreatora można zaimplementować inne opcjonalne szablonu klasy i odpowiednie interfejsy, w zależności od potrzeb strony.  

 [WizardPageImpl szablonu klasy](#WizardPageImplTemplateClass) ma kilka przydatne interfejsów, które mogą pomóc Ci zapisu stron kreatora niestandardowego. Implementowanie [WizardPageImpl szablonu klasy](#WizardPageImplTemplateClass) jako klasę podstawową dla strony kreatora niestandardowego.  

 Aby uzyskać listę dostępnych:  

-   Klasy szablonów dla stron kreatora, zobacz [klas pomocy strony kreatora](#WizardPageHelperClasses)  

-   Interfejsy dla klasy szablonów strony kreatora, zobacz [interfejsy strony kreatora](#WizardPageInterfaces)  

 Strona kreatora niestandardowego, w tym przykładzie jest pochodną [klasy szablonu WizardPageImpl](#WizardPageImplTemplateClass) i implementuje [IWizardPage interfejsu](#IWizardPageInterface). Dodatkowo implementuje strony kreatora niestandardowego **IFieldCallback** interfejsu. Oba te są implementowane w pliku LocationPage.cpp.  

 Przykładowa strona kreatora niestandardowego zastępuje następujące metody:  

-   **OnWindowCreated**. **OnWindowCreated** wywołania metod w przykładowa strona kreatora następujących metod:  

    -   [AddField](#AddField). Ta metoda odnosi się **IDC_COMBO_LOCATION** polu formantu **IDD_LOCATION_PAGE** zasobów z [danych](#Data) elementu o nazwie **lokalizacji**w pliku Config.xml.  

         Oprócz **AddField** metody, można użyć [AddRadioGroup](#AddRadioGroup) i [AddToGroup](#AddToGroup) metod do obsługi innych formantów i zachowań.  

        > [!NOTE]
        >  Upewnij się, że należy wywołać [AddField](#AddField), [AddRadioGroup](#AddRadioGroup), lub [AddToGroup](#AddToGroup) metoda przed wywołaniem [InitFields](#InitFields) metody.  

    -   [InitFields](#InitFields). Ta metoda umożliwia inicjowanie pola (formanty), które ma być dodany do formularza. Wskaźnik strony jest parametrem. W tym przykładzie **to** przekazany wskaźnika, które odwołuje się do bieżącej strony.  

        > [!NOTE]
        >  Do korzystania z **to** wskaźnika, musisz zaimplementować **IFieldCallback** interfejsu oprócz interfejsy który [WizardPageImpl szablonu klasy](#WizardPageImplTemplateClass) obsługuje.  

         **IFieldCallback** interfejs wywołania **SetFieldDefault** metodę, która jest używana do ustawiania wartości domyślne dla formantów innych niż tekst pola i formanty. W tym przykładzie **SetFieldDefault** metoda ustawia początkowy indeks kontrolki pola kombi na podstawie wartości domyślne, określona w **domyślne** elementu [pola](#Field) element w pliku Config.xml.  

     **OnWindowCreated** metody konfiguruje przy użyciu kontrolera formularza [IFormController interfejsu](#IFormController-Interface). Aby uzyskać więcej informacji na temat konfigurowania kontrolera formularza, zobacz [Konfigurowanie formularza](#SettingUptheForm).  

-   **InitLocations**. Ta metoda umożliwia wypełnienie pola kombi z listy lokalizacji w pliku Config.xml. [Danych](#Data) element i podrzędne [DataItem](#DataItem) elementów pliku Confg.xml zawierają listę możliwych wartości.  

-   **OnNextClicked**. Ta metoda wykonuje następujące zadania:  

    -   Aktualizacje **TSLocation** zmienną sekwencji zadań z wybranej w polu kombi przy użyciu wartości **SaveFields** — metoda  

    -   Dodaje informacje, które będą wyświetlane na **Podsumowanie** strony **SaveFields** — metoda  

#####  <a name="TheNextButtonisClickedinCustomWizardPage"></a> Krok 4. Kliknięciu przycisku Dalej na stronie kreatora niestandardowego  
 Po ukończeniu przez użytkownika pola na stronie kreatora niestandardowego użytkownik klika polecenie **dalej**, które wywołuje **OnNextClicked** metody. **OnNextClicked** metoda wykonuje wszelkie niezbędne zadania przed kontynuowaniem do następnej strony kreatora, takie jak rejestrowanie jakiekolwiek zmiany konfiguracji wprowadzone na stronie kreatora niestandardowego.  

 Na stronie kreatora niestandardowego przykład zastąpienia dla **OnNextClicked** metoda jest zaimplementowana w pliku LocationPage.ccp. W **OnNextClicked** metody w przykładowa strona kreatora niestandardowych, są nazywane następujących metod:  

1.  [InitSection](#InitSection). Ta metoda inicjuje nagłówek (podpis etykiety) dla podsumowania danych wyświetlanych na **podsumowania** strony. Zazwyczaj można ustawić tej wartości przy użyciu **DisplayName()** funkcji. Dane skojarzone z tą etykietą został zapisany przy użyciu [SaveFields](#SaveFields) metody.  

2.  [SaveFields](#SaveFields). Taka metoda ogranicza wartości pól do zmiennych sekwencji zadań i dane wyświetlane w **Podsumowanie** strony.  

###  <a name="ReviewSampleEditorVisualStudioSolution"></a> Przejrzyj rozwiązania SampleEditor Visual Studio  
 Przed rozpoczęciem tworzenia własnych stron kreatora niestandardowego i strona kreatora edytory, wykonaj następujące kroki, aby przygotować środowisko projektowe UDI:  

-   Przegląd architektury projektanta Kreatora instalacji UDI zgodnie z opisem w [Przejrzyj architektura projektanta kreatora UDI](#ReviewUDIWizardDesignerArchitecture).  

-   Przejrzyj składniki strony kreatora UDI, który można dostosować przy użyciu pliku konfiguracji kreatora UDI zgodnie z opisem w [przeglądu można skonfigurować składniki strony kreatora UDI](#ReviewConfigurableComponentsofUDIWizardPage).  

-   Przejrzyj podany w zestawie SDK UDI zgodnie z opisem w przykład EditorPage [Przejrzyj przykład EditorPage](#ReviewEditorPageExample).  

####  <a name="ReviewUDIWizardDesignerArchitecture"></a> Przegląd architektury projektanta kreatora UDI  
 Projektanta Kreatora instalacji UDI został opracowany przy użyciu WPF, biblioteki Prism i Unity. Projektant UDI jest używany do edytowania pliku konfiguracji kreatora UDI (UDIWizard_Config.xml), Kreator UDI (OSDSetupWizard.exe) odczytywany w czasie wykonywania. [Stron](#Pages) w pliku konfiguracji kreatora UDI zawiera listę stron, która ma oddzielnej [strony](#Page) elementu dla każdej strony kreatora.  

 Podczas edytowania ustawień konfiguracyjnych dla strony kreatora projektanta Kreatora instalacji UDI ładuje edytorze niestandardowej strony, który odpowiada typowi strony kreatora. Edytory strony kreatora niestandardowego są tworzone jako formanty użytkownika WPF. Użyj strony Edytor stron kreatora niestandardowego [modelu — widok — ViewModel](http://msdn.microsoft.com/magazine/dd419663.aspx) wzorca projektowego (MVVM) dla programu WPF.  

 Wzorzec projektowy MVVM pomaga oddzielić interfejsu użytkownika (UI; prezentacji) od dane są prezentowane. Dane są fasad za pośrednictwem [strony](#Page) w pliku konfiguracji kreatora UDI (pliku Config.xml w przykładzie), który jest dostępny za pomocą [CurrentPage](#CurrentPage) właściwość [ IDataService](#IDataService) interfejsu.  

 Używa projektanta Kreatora instalacji UDI **DependencyAttribute** uzyskać dostępu do **DataService** klasy oparte na framework iniekcji zależności w Unity. Aby uzyskać więcej informacji na temat framework interjection zależności w Unity, zobacz [wstrzyknąć niektóre życia do Twojej aplikacji — Poznaj bloku aplikacji platformy Unity](http://msdn.microsoft.com/library/ff650806.aspx).  

####  <a name="ReviewConfigurableComponentsofUDIWizardPage"></a> Przejrzyj składniki można skonfigurować UDI strony kreatora  
 Jak utworzyć stronę kreatora niestandardowego, niektóre ustawienia konfiguracji może być ustawiona w kodzie i nie można zmienić po stronie została wykonana. Jednak dla innych ustawień konfiguracyjnych, należy umożliwić te ustawienia konfiguracji można zmienić za pomocą projektanta Kreatora instalacji UDI.  

 Zazwyczaj ustawienia konfiguracji, które chcesz skonfigurować za pomocą projektanta Kreatora instalacji UDI są zapisywane w pliku konfiguracji kreatora UDI (pliku Config.xml w przykładzie). Również można jednak utworzyć własny plik osobną konfiguracją, w razie potrzeby. UDIWizard_Config.xml.app jest jednym z przykładów przy użyciu pliku konfiguracji oddzielnych plików, które **odnajdywania aplikacji** zadań i **ApplicationPage** użycie typu strony kreatora.  

 Poniżej przedstawiono listę typowych ustawień, którymi można zarządzać za pomocą projektanta Kreatora instalacji UDI:  

-   **Pole**. Użyj pola umożliwiają podawanie danych wejściowych. Pola są wyświetlane jako [pola](#Field) elementów w pliku konfiguracji kreatora UDI (UDIWizard_Config.xml), który zawiera ustawienia konfiguracji dla każdego pola. Odpowiedniego edytora strony kreatora należy podać metodę edycji ustawień konfiguracji pola dla pola za pomocą [FieldElementControl](#FieldElementControl).  

-   **Właściwości**. Metody ustawiające pomocy utworzyć właściwości dla jednostek na tej stronie, takich jak strony w [strony](#Page) elementu pola w [pola](#Field) elementu lub danych w [danych](#Data) lub [ DataItem](#DataItem) elementów. Skonfiguruj właściwości w [metody ustawiającej]() elementów. Dodać osobną [metody ustawiającej]() dla każdej właściwości, które chcesz zdefiniować. Edytuj właściwości, za pomocą [SetterControl](#SetterControl) i skonfigurować inne [metody ustawiającej]() elementów za pomocą innych kontrolek.  

-   **Dane**. Dane są używane do przechowywania informacji do użytku przez strony kreatora i innych składników. Można zdefiniować dane dotyczące strony lub za pomocą pola [danych](#Data) lub [DataItem](#DataItem) elementów. Dane można zdefiniować w płaskiej lub hierarchiczna struktura przy użyciu prawidłowego [danych](#Data) lub [DataItem](#DataItem) elementów. Pliku Config.xml w przykładzie w zestawie SDK przedstawia sposób tworzenia struktury danych w prostych.  

 Utworzony Edytor stron kreatora niestandardowego musi mieć możliwość zarządzania te ustawienia konfiguracji.  

####  <a name="ReviewEditorPageExample"></a> Przejrzyj przykład EditorPage  
 W przykładzie EditorPage służy do konfigurowania ustawień konfiguracyjnych dla **SamplePage** strona kreatora w pliku konfiguracyjnym UDI kreatora. Przykład EditorPage zawiera następujące składniki podstawowe:  

-   Interfejs użytkownika, aby skonfigurować **lokalizacji** ustawienia pola kombi  

-   Interfejs użytkownika, aby dodać lub edytować lokalizację na liście możliwych lokalizacji, które są wyświetlane w **lokalizacji** pola kombi  

-   Ustawienia konfiguracji odczytywane i zapisywane w pliku konfiguracji kreatora UDI  

-   Obsługa kodu dla innych składników  

 Przejrzyj przykład EditorPage w programie Visual Studio, wykonując następujące czynności:  

1.  Przejrzyj jak **SampleEditor** ładowany i zainicjowany w projektanta Kreatora instalacji UDI zgodnie z opisem w edytorze strony kreatora [ładowanie Edytor strony kreatora przejrzyj i inicjalizacji](#ReviewWizardPageEditorLoadingInitialization).  

2.  Przegląd interfejsu użytkownika używane do edycji **lokalizacji** pola kombi w plikach LocationPageEditor.xaml i LocationPageEditor.xaml.cs zgodnie z opisem w [Przejrzyj interfejs użytkownika używany do konfigurowania pola kombi lokalizacji](#ReviewUserInterfaceUsedtoConfigureLocationComboBox).  

3.  Przegląd interfejsu użytkownika używane do dodawania lub edytowania lokalizacji do listy w plikach AddEditLocationView.xaml i AddEditLocationView.xaml.cs zgodnie z opisem w [Przejrzyj interfejsu użytkownika używane do modyfikowania listy możliwych lokalizacji](#ReviewUserInterfaceUsedtoModifyListofPossibleLocations).  

4.  Przejrzyj kod używany do zarządzania informacjami o konfiguracji zapisane w pliku konfiguracji kreatora UDI zgodnie z opisem w [przejrzeć kod używany do zarządzania informacje o konfiguracji](#ReviewCodeUsedtoManageConfigurationInformation).  

#####  <a name="ReviewWizardPageEditorLoadingInitialization"></a> Przejrzyj ładowania Edytor stron kreatora i inicjalizacji  
 Edytory strony kreatora niestandardowego są załadowane, co jest wymagane przez projektanta Kreatora instalacji UDI. Pliki konfiguracji projektanta Kreatora instalacji UDI są ładowane podczas uruchamiania projektanta Kreatora instalacji UDI. Skanuje projektanta Kreatora instalacji UDI *install_folder*\Bin\Config folder (gdzie *install_folder* jest nazwą folderu, w którym jest zainstalowany zestaw MDT) dla plików z rozszerzeniem pliku .config.  

 Podczas konfigurowania środowiska deweloperskiego UDI skopiowany plik SamplePage.dll.confg *install_folder*\Bin\Config folderu. Po uruchomieniu projektanta Kreatora instalacji UDI plik SamplePage.dll.confg odnaleźć i załadować.  

 Projektanta Kreatora instalacji UDI używa następujących atrybutach [strony](#Page) elementu w pliku SamplePage.dll.confg do ładowania i zainicjować przykład EditorPage:  

-   **DesignerAssembly**. Ten atrybut określa nazwę biblioteki DLL do załadowania. Ta biblioteka DLL musi być umieszczona w tym samym folderze co plik UDIDesigner.exe, który jest *install_folder*\Bin folder (gdzie *install_folder* jest nazwą folderu, w którym jest zainstalowany zestaw MDT).  

-   **DesignerType**. Ten atrybut jest program Microsoft .NET Nazwa typu klasy, która zawiera formanty użytkownika WPF.  

-   **Typ**. Aby skonfigurować typ strony, strony kreatora niestandardowego, który jest ładowany przez kreatora UDI, należy użyć tego atrybutu. Projektanta Kreatora instalacji UDI używa tego atrybutu, aby zlokalizować odpowiedni [strony](#Page) w pliku konfiguracji kreatora UDI.  

-   **Biblioteki dll**. Ten atrybut umożliwia skonfigurowanie [DLL](#DLL) elementu w pliku konfiguracyjnym UDI Kreator tworzy projektanta Kreatora instalacji UDI.  

-   **Opis elementu**. Aby podać informacje o Edytorze stron kreatora, należy użyć tego atrybutu. Wartość tego atrybutu jest wyświetlany w **Dodaj nową stronę** okno dialogowe w projektanta Kreatora instalacji UDI, który służy do dodania do biblioteki"strony" strony kreatora.  

-   **Nazwa wyświetlana**. Aby podać nazwę strony kreatora niestandardowego, która jest wyświetlana w projektanta Kreatora instalacji UDI, należy użyć tego atrybutu. Wartość tego atrybutu jest wyświetlany w **Dodaj nową stronę** okno dialogowe w projektanta Kreatora instalacji UDI, który służy do dodania do biblioteki"strony" strony kreatora.  

     W tym przykładzie typ **SamplePage** strona kreatora niestandardowego jest **Microsoft.SamplePage.LocationPage**, które są zapisywane w pliku Config.xml. W pliku Config.xml znajduje się w *local_folder*\SDK\SamplePage\SamplePage folder (gdzie *local_folder* jest do folderu utworzonego na komputerze dewelopera wcześniej w konfiguracji proces).  

#####  <a name="ReviewUserInterfaceUsedtoConfigureLocationComboBox"></a> Przegląd interfejsu użytkownika, które umożliwiają skonfigurowanie lokalizacji pola kombi  
 Gdy ładowany i zainicjować Edytor stron kreatora, Edytor stron kreatora SampleEditor jest załadowany, gdy strony o typie **Microsoft.SamplePage.LocationPage** jest edytowany. Interfejs użytkownika dla edytora strony są przechowywane w pliku LocationPageEditor.xaml.  

 Jeśli należy zbadać interfejsu użytkownika na **projekt** kartę i kodu na **XAML** kartę, można zobaczyć relację pomiędzy graficznego interfejsu użytkownika oraz elementy i atrybuty (Extensible Application Markup Language XAML).  

 Na przykład, jeśli należy przejrzeć **kontrolki: FieldElementControl** elementu w pliku XAML widać, jak odnoszącej się do układu odpowiedniego interfejsu użytkownika. Użyj **kontrolki: FieldElementControl** element, aby zdefiniować [FieldElementControl](#FieldElementControl) formantu.  

 **Powiązanie** pola Edytor strony przykładowe z informacji w pliku konfiguracji kreatora UDI wiązania parametrów w pliku XAML. Na przykład poniższy kod ties **wartość domyślna** pole tekstowe z [domyślne](#Default) w pliku konfiguracji kreatora UDI (pliku Config.xml w przykładzie):  

```  
<TextBox Text="{Binding FieldData.DefaultValue,  
 UpdateSourceTrigger=PropertyChanged,  
 Mode=TwoWay}"/>  
```  

 Aby uzyskać więcej informacji, zobacz [jak: Przechowuj dane dostępne przez powiązanie w języku XAML](http://msdn.microsoft.com/library/ms748857.aspx).  

 Użyj **Views:CollectionTControl.ColumnCollectionView** elementu w języku XAML, aby edytować listę dostępnych lokalizacji, w widoku siatki. Możesz użyć [CollectionTControl](#CollectionTControl) formantu do wyświetlania widoku siatki i powiązać widoku siatki w [danych](#Data) elementu o nazwie **lokalizacji** w pliku konfiguracyjnym UDI.  

#####  <a name="ReviewUserInterfaceUsedtoModifyListofPossibleLocations"></a> Przegląd interfejsu użytkownika używane do modyfikowania listy możliwych lokalizacji  
 Interfejs użytkownika do modyfikowania listy możliwych lokalizacji obejmuje:  

-   Menu kontekstowe i przyciski wstążki, które umożliwiają dodawanie, edytowanie, usunąć lub zmienić kolejność elementów na liście lokalizacje, zgodnie z opisem w [przeglądu Context-sensitive Menu i przyciski wstążki do modyfikowania listy lokalizacji](#ReviewContextSensitiveMenuandRibbonButtons)  

-   Okno dialogowe, które jest inicjowana po wybraniu umożliwiają dodawanie lub edytowanie elementu na liście lokalizacje, zgodnie z opisem w [Sprawdź okno dialogowe Dodawanie lub edytowanie lokalizacji](#ReviewDialogBoxforAddingEditingLocations)  

######  <a name="ReviewContextSensitiveMenuandRibbonButtons"></a> Menu kontekstowe przeglądu i przyciski wstążki do modyfikowania listy lokalizacji  
 Po kliknięciu prawym przyciskiem myszy w polu listy, który zawiera listę lokalizacji jest wyświetlane menu kontekstowe. Wstążka ma odpowiadające mu przyciski, które umożliwiają wykonywanie zadań. **Widoków: CollectionsTControl** element formantu w pliku LocationPageEditor.xaml definiuje metody wywołane oparte na akcję wykonywaną i właściwości, które można ustawić w następujący sposób:  

-   **SelectedItem**. Ta właściwość powiązane z danymi jest aktywowany, gdy użytkownik wybiera element z listy. Ta właściwość jest związany z **CurrentLocation** właściwości w modelu widoku, który jest zlokalizowany w pliku LocationPageEditorViewModel.cs i używana przez [CollectionTControl](#CollectionTControl) formantu do przekazania elementu wybrany, gdy Edytuj lub usuń istniejący element.  

-   **AddItemAction**. Ta akcja jest wykonywana, gdy użytkownik kliknie **Dodaj element** opcji z menu kontekstowego lub odpowiadające mu przyciski na Wstążce. Brak powiązania danych właściwości w modelu widoku, który zwraca **AddLocationAction** obiektu. Ten obiekt jest **AddLocationCallback** metoda, znajduje się w pliku LocationPageEditorViewModel.cs i wyświetla okno dialogowe pliku AddEditLocationView.xaml.  

-   **EditItemAction**. Ta akcja jest wykonywana, gdy użytkownik kliknie **edycji elementu** opcji z menu kontekstowego. Brak powiązania danych właściwości w modelu widoku, który zwraca **EditLocationAction** obiektu. Ten obiekt jest **EditLocationCallback** metoda, znajduje się w pliku LocationPageEditorViewModel.cs i wyświetla okno dialogowe pliku AddEditLocationView.xaml.  

-   **RemoveAction**. Ta akcja jest wykonywana, gdy użytkownik kliknie **Usuń element** opcji z menu kontekstowego. Brak powiązania danych właściwości w modelu widoku, który zwraca **RemoveAction** obiektu. Ten obiekt jest **EditLocationCallback** metoda, znajduje się w pliku LocationPageEditorViewModel.cs i zawiera komunikat potwierdzający usunięcie lokalizacji.  

######  <a name="ReviewDialogBoxforAddingEditingLocations"></a> Sprawdź okno dialogowe dodawania i edytowania lokalizacji  
 Jeśli dodawanie nowych lokalizacji do listy lokalizacji lub Edytuj istniejącą lokalizację, zostanie wyświetlony komunikat, który znajduje się w pliku AddEditLocationView.xaml. Ten komunikat jest wyświetlany za pomocą [ShowDialogWindow](#ShowDialogWindow) metodę okna w pliku LocationPageEditorViewModel.cs.  

 Interfejs użytkownika w pliku AddEditLocationView.xaml obejmuje:  

-   Ramka okna dialogowego o nazwie **DialogFrame**, która obejmuje następujące elementy:  

    -   Tytuł, który można skonfigurować za pomocą **DialogTitle** atrybutu ramki okna dialogowego  

    -   **OK** przycisku, który ustawia stan zwrotu, jak w przypadku **zatwierdzone** właściwości **True** (stan zwracany jest sprawdzany **AddLocationCallback** metodę w celu ustalenia, czy użytkownik kliknął pliku LocationPageEditorViewModel.cs **OK**.)  

    -   A **anulować** przycisku, który ustawia stan zwrotu, jak w przypadku **zatwierdzone** właściwości **False** (stan zwracany jest sprawdzany **AddLocationCallback**  metodę w celu ustalenia, czy użytkownik kliknął pliku LocationPageEditorViewModel.cs **anulować**.)  

-   Element WPF, który zawiera:  

    -   Etykietę, którą można skonfigurować za pomocą **zawartości** atrybutu  

    -   Pole tekstowe, który jest powiązany z [danych](#Data) elementu o nazwie **lokalizacji** w pliku konfiguracyjnym UDI (pliku Config.xml w przykładzie)  

######  <a name="ReviewCodeUsedtoManageConfigurationInformation"></a> Przejrzyj kod używany do zarządzania informacjami o konfiguracji  
 Informacje o konfiguracji dla strony kreatora niestandardowego są przechowywane w pliku konfiguracyjnym UDI kreatora, który jest:  

-   Pliku Config.XML w przykładzie podana przy użyciu zestawu SDK UDI (ten plik zawiera tylko ustawienia konfiguracji dla przykładu).  

-   Podany zestaw mdt przechowywane w pliku UDIWizard_Config.xml *installation_folder*\Templates\Distribution\Scripts folder (gdzie *installation_folder* to folder, w którym jest zainstalowany zestaw MDT); Ten plik zawiera ustawienia konfiguracji dla wszystkich stron kreatora wbudowanych i etapach  

 W tym przykładzie SampleEditor **lokalizacje** procedura ułatwia zarządzanie informacjami o konfiguracji i znajduje się w pliku LocationPageEditorViewModel.cs. **Lokalizacje** procedury zwraca listę z lokalizacji z pliku konfiguracyjnego UDI kreatora. W szczególności, zwracana lista zawiera element dla każdego [DataItem](#DataItem) elementu w pliku konfiguracyjnym UDI kreatora.  

## <a name="creating-custom-udi-wizard-pages"></a>Tworzenie niestandardowych UDI strony kreatora  
 Tworzenie niestandardowych stron kreatora UDI ogólny proces wygląda następująco:  

1.  Utwórz kopię rozwiązania SamplePage jako punktu wyjścia.  

2.  Umieść formanty żądaną (pól) w formularzu.  

3.  Pisanie kodu do wykonywania odpowiednich zadań podczas ładowania strony kreatora (zastąpień dla **OnWindowCreated** metodę), w tym następujące etapy:  

    1.  Inicjowanie formularza.  

    2.  Zmienne, zmienne sekwencji zadań, zmienne środowiskowe lub XML informacje o plikach pamięci do odczytu (takich jak **metody ustawiającej** właściwości).  

4.  Pisania kodu do wykonywania odpowiednich zadań, gdy strona jest wyświetlana (zastąpień dla **OnWindowShown** metodę), w tym następujące etapy:  

    1.  Włącz lub wyłącz formantów na podstawie informacji, przeczytaj podczas ładowania strony w kroku 3.  

    2.  Aktualizacja formantów na podstawie informacji o odczytu, gdy następnie załadować strony w kroku 3, takich jak wypełnianie formantów na podstawie informacji do odczytu.  

5.  Pisania kodu do wykonywania odpowiednich zadań podczas wykonywania czynności na stronie kreatora.  

6.  Pisania kodu do wykonywania odpowiednich zadań, po kliknięciu przez użytkownika **dalej** w Kreatorze UDI (zastąpień dla **OnNextClicked** metodę), w tym następujące etapy:  

    1.  Zaktualizuj zmienne pamięci, zmienne sekwencji zadań, zmienne środowiskowe lub informacje o pliku XML.  

    2.  Zaktualizuj informacje ze strony podsumowania (Jeśli nie zostanie wykonany przez pola na stronie).  

7.  Skompiluj rozwiązanie.  

     Upewnij się, że wersja biblioteki DLL należy utworzyć jest tę samą platformę procesora jako instalacji zestawu MDT — w szczególności platformy procesora środowiska preinstalacji systemu Windows (Windows PE). UDI kreatora można uruchomić w:  

    -   **Istniejącego systemu operacyjnego na komputerze docelowym**. 32-bitowe wersje strony kreatora można uruchomić w 32-bitowy lub 64-bitowych systemach operacyjnych Windows. Wersje 64-bitowe strony kreatora można jednak uruchamiać tylko w 64-bitowych systemach operacyjnych Windows.  

    -   **Środowiska Preinstalacyjnego systemu Windows na komputerze docelowym**. Środowiska Preinstalacyjnego systemu Windows nie obsługuje uruchamiania aplikacji 32-bitowych na 64-bitowej wersji systemu Windows PE. Należy więc utworzone wersji strony kreatora dla każdej architektury procesora, środowiska Windows PE, która ma być używany.  

8.  Skopiuj biblioteki DLL dla strony kreatora niestandardowego *installation_folder*\Templates\Distribution\Tools\ platforma folder (gdzie *installation_folder* to folder, w którym zainstalowano zestaw MDT i *platformy* jest **x86** w 32-bitowej wersji lub **x64** jest przeznaczony dla 64-bitowej wersji).  

9. Wykonaj kroki tworzenia niestandardowej strony edytora.  

## <a name="creating-custom-wizard-page-editors"></a>Tworzenie edytory strony kreatora niestandardowego  
 Ogólny proces tworzenia niestandardowych UDI edytory strona kreatora jest następująca:  

1.  Utwórz kopię rozwiązania SampleEditor jako punktu wyjścia.  

2.  Utwórz Edytor interfejsu użytkownika strony głównej, w pliku .xaml.  

3.  Dodawanie wystąpień [FieldElementControl](#FieldElementControl) kontroli zgodnie z wymaganiami strony kreatora należy skonfigurować (jeśli jest to wymagane).  

4.  Dodawanie wystąpień [SetterControl](#SetterControl) kontroli zgodnie z wymaganiami strony kreatora należy skonfigurować (jeśli jest to wymagane).  

5.  Dodawanie wystąpień [CollectionTControl](#CollectionTControl) kontroli zgodnie z wymaganiami strony kreatora należy skonfigurować (jeśli jest to wymagane).  

6.  Dodaj [IDataService](#IDataService) interfejsu.  

7.  Pisanie kodu odpowiednich aktualizacji pliku konfiguracji kreatora UDI zgodnie z ustawieniami konfiguracji do można skonfigurować za pomocą edytora strony kreatora niestandardowego.  

8.  Tworzenie okien dialogowych obiektu podrzędnego w pliku .xaml i połączeń telefonicznych z nimi ze strony głównej przy użyciu edytora [IMessageBoxService](#IMessageBoxService) zgodnie z wymaganiami strony kreatora należy skonfigurować na interfejsie.  

9. Dodanie odpowiednich interfejsów do projektanta wstążki kreatora UDI na podstawie wymagań strony kreatora należy skonfigurować.  

10. Skompiluj rozwiązanie.  

    > [!NOTE]
    >  Upewnij się, że wersja biblioteki DLL należy utworzyć jest tę samą platformę procesora jako instalacji zestawu MDT. Na przykład po zainstalowaniu 64-bitowej wersji zestawu mdt, utworzyć wersję 64-bitowych edytora niestandardowej strony.  

11. Na stronie kreatora odpowiedniego (plik SamplePage.dll.config w przykładzie), należy utworzyć plik konfiguracji projektanta Kreatora instalacji UDI, można załadować biblioteki dll i mapowanie strony kreatora edytora.  

     Aby uzyskać więcej informacji na temat elementy wymagane do przeprowadzenia mapowanie między strony kreatora i Edytor stron kreatora, zobacz [DesignerMappings](#DesignerMappings) element elementów podrzędnych i odpowiednie atrybuty.  

12. Skopiuj utworzony w poprzednim kroku, aby plik konfiguracji projektanta Kreatora instalacji UDI *installation_folder*\Bin\Config folder (gdzie *installation_folder* to folder, w którym jest zainstalowany Wersja zestawu MDT).  

13. Skopiuj bibliotekę DLL tego kreatora niestandardowego edytora strony do *installation_folder*\Bin folder (gdzie *installation_folder* to folder, w którym jest zainstalowany zestaw MDT).  

##  <a name="CreatingCustomUDITasks"></a> Tworzenie niestandardowych UDI zadań  
 *Zadania UDI* są bibliotek DLL w języku C++, które implementują [interfejsu ITask](#ITaskinterface). Zarejestruj plik DLL z biblioteką zadań projektanta Kreatora instalacji UDI, tworząc plik konfiguracji projektanta Kreatora instalacji UDI (pliku .config) i umieszczenie go w *installation_folder*\Bin\Config folder (gdzie *installation_ folder* to folder, w którym jest zainstalowany zestaw MDT).  

> [!NOTE]
>  Można utworzyć biblioteki DLL, która zawiera stron kreatora, zadania i moduły weryfikacji w ramach tego samego pliku dll. Można również utworzyć pojedynczy projektanta Kreatora instalacji UDI plik konfiguracji (config) zawierający ustawienia konfiguracji dla stron kreatora, zadania i moduły weryfikacji w bibliotece DLL.  

 **Aby utworzyć niestandardowe UDI zadania**  

1.  Pisanie kodu, który implementuje [interfejsu ITask](#ITaskinterface) i następujących metod:  

    -   [Init](#Init). Ta metoda jest wywoływana w celu zainicjowania zadania.  

    -   [Wykonanie](#Execute). Ta metoda jest wywoływana w celu uruchomienia zadania.  

2.  Pisanie kodu, który rejestruje zadanie niestandardowe fabryki klasy z rejestru fabryki.  

3.  Skompiluj rozwiązanie niestandardowe zadania.  

    > [!NOTE]
    >  Upewnij się, że wersja biblioteki DLL należy utworzyć jest tę samą platformę procesora jako instalacji zestawu MDT. Na przykład jeśli musisz zainstalować 64-bitowej wersji zestawu mdt, kompilacji 64-bitowej wersji niestandardowego zadania UDI.  

4.  Utwórz [zadań](#Task) pod [TaskLibrary](#TaskLibrary) elementu w pliku konfiguracyjnym projektanta Kreatora instalacji UDI podobnie poniższy fragment:  

    ```  
    <Task DLL="OSDRefreshWizard.dll" Description="Discovers supported applications for install." Type="Microsoft.OSDRefresh.AppDiscoveryTask" Name="Application Discovery">  
       <TaskItem Type="Setter" Name="Status Bitmap">  
          <Param Name="BitmapFilename"/>  
       </TaskItem>  
       <TaskItem Type="Setter" Name="Log File">  
          <Param Name="log"/>  
       </TaskItem>  
       <TaskItem Type="Setter" Name="Write Configuration File">  
          <Param Name="writecfg"/>  
       </TaskItem>  
       <TaskItem Type="Setter" Name="Read Configuration File">  
          <Param Name="readcfg"/>  
       </TaskItem>  
    </Task>  
    ```  

    > [!NOTE]
    >  Wszystkie [zadań](#Task) powinna zawierać elementy **BitmapFilename** parametru. Określ inne parametry zadanie wymaga. Na przykład w poprzednim fragmencie kodu **dziennika** parametr jest używany do określenia parametru lokalizację pliku dziennika.  

5.  Skopiuj utworzony w poprzednim kroku, aby plik konfiguracji projektanta Kreatora instalacji UDI *installation_folder*\Bin\Config folder (gdzie *installation_folder* to folder, w którym jest zainstalowany zestaw MDT).  

6.  Skopiuj biblioteki DLL dla niestandardowego zadania *installation_folder*\Templates\Distribution\Tools\ platforma folder (gdzie *installation_folder* to folder, w którym zainstalowano zestaw MDT i *platformy* jest **x86** w 32-bitowej wersji lub **x64** jest przeznaczony dla 64-bitowej wersji).  

##  <a name="CreatingCustomUDIValidators"></a> Tworzenie niestandardowych UDI modułów sprawdzania poprawności  
 *Moduły weryfikacji UDI* są bibliotek DLL w języku C++, które implementują **IValidator** interfejsu. Zarejestruj plik DLL z biblioteką modułu sprawdzania poprawności projektanta Kreatora instalacji UDI, tworząc plik konfiguracji projektanta Kreatora instalacji UDI (pliku .config) i umieszczenie go w *installation_folder*\Bin\Config folder (gdzie  *installation_folder* to folder, w którym jest zainstalowany zestaw MDT).  

 **Aby utworzyć niestandardowe moduły UDI**  

1.  Pisanie kodu, który tworzy podklasy **BaseValidator** klasy i implementuje następujących metod:  

    -   **Init (IControl \*pControl, IWizardPageContainer \*pContainer, IStringProperties \*pProperties)**. Wywołuje kontrolera **Init** elementu członkowskiego można zainicjować modułu sprawdzania poprawności. Tej metody należy wywołać **Init** metodę **BaseValidator** klasy. Zwykle odczytuje właściwości dla modułu weryfikacji z Kreatora UDI pliku konfiguracji. Na przykład **InvalidCharactersValidator** modułu sprawdzania poprawności pobiera wartość **InvalidChars** właściwości przy użyciu tej metody.  

    -   **IsValid**. Kontroler formularza wywołuje tę metodę, aby zobaczyć, czy formant zawiera prawidłowy tekst. Poniżej przedstawiono przykład **IsValid** metody dla modułu weryfikacji, który sprawdza, czy pole nie jest pusta:  

        ```  
        BOOL IsValid(LPBSTR pMessage)  
        {  
            __super::IsValid(pMessage);  

            _bstr_t text;  
            m_pText->GetText(text.GetAddress());  
            return (text.length() > 0);  
        }  
        ```  

    -   **Init (IControl \*pControl, komunikat LPCTSTR)**. Kontroler formularza wywołuje ten element członkowski każdym naciśnięciu klawisza i inne zdarzenia, aby modułu sprawdzania poprawności można sprawdza, czy zawartość formantu i zaktualizowane wiadomości w dolnej części strony kreatora (lub usuń ich zaznaczenie).  

     Zazwyczaj są tylko metody, które należy zastąpić. Jednak w zależności od modułu sprawdzania poprawności, konieczne może być zastępować inne metody w podklasą klasy **BaseValidator** klasy tworzenia. Aby uzyskać więcej informacji o tych innych metod, zobacz **BaseValidator** klasy.  

2.  Pisanie kodu, który rejestruje zadanie niestandardowe klasy z fabryką rejestru.  

3.  Skompiluj rozwiązanie niestandardowe zadania.  

    > [!NOTE]
    >  Upewnij się, że wersja biblioteki DLL należy utworzyć jest tę samą platformę procesora jako instalacji zestawu MDT. Na przykład jeśli musisz zainstalować 64-bitowej wersji zestawu mdt, kompilacji 64-bitowej wersji niestandardowego zadania UDI.  

4.  Utwórz [modułu sprawdzania poprawności](#Validator) pod **ValidatorLibrary** elementu w pliku konfiguracyjnym projektanta Kreatora instalacji UDI podobnie poniższy fragment:  

    ```  
    <Validator   
    <Validator DLL="" Description="Must follow a pre-defined pattern" Type="Microsoft.Wizard.Validation.RegEx" Name="NamedPattern">  
       <Param Description="Enter the message you want displayed when the text in this field doesn't match the pattern:" Name="Message" DisplayName="Message"/>  
       <Param Description="The name of a pre-defined regular expression pattern. Must be Username, ComputerName, or Workgroup" Name="NamedPattern" DisplayName="Named Pattern"/>  
    </Validator>  
    ```  

    > [!WARNING]
    >  Wszystkie [modułu sprawdzania poprawności](#Validator) powinna zawierać elementy **komunikat** parametru. Określ inne parametry zgodnie z wymaganiami modułu sprawdzania poprawności. Na przykład w poprzednim fragmencie kodu **NamedPattern** parametr jest używany do określenia parametru nazwy wstępnie zdefiniowane wyrażenia regularnego.  

5.  Skopiuj utworzony w poprzednim kroku, aby plik konfiguracji projektanta Kreatora instalacji UDI *installation_folder*\Bin\Config folder (gdzie *installation_folder* to folder, w którym jest zainstalowany zestaw MDT).  

6.  Skopiuj biblioteki DLL dla niestandardowego zadania *installation_folder*\Templates\Distribution\Tools\ platforma folder (gdzie *installation_folder* to folder, w którym zainstalowano zestaw MDT i *platformy* jest **x86** w 32-bitowej wersji lub **x64** jest przeznaczony dla 64-bitowej wersji).  

## <a name="udi-wizard-reference"></a>Kreator UDI — informacje  

### <a name="wizard-page-components"></a>Kreator składników stron  
 Jedną z kilku składników wbudowane umożliwia tworzenie niestandardowych stronach.  

#### <a name="creating-component-instances"></a>Tworzenie wystąpień składników  
 Kreator UDI używa fabryki klas do utworzenia nowego wystąpienia obiektów. Te fabryki są zarejestrowane w usłudze rejestr fabryczny, za pomocą ciągu jako klucz w usłudze fabryka. Na przykład **WmiRepository** składnika jest określana przez ciąg "Microsoft.Wizard.WmiRepository", która jest dostępna w pliku nagłówka IWmiRepository jako **ID_WmiRepository**.  

 Przy założeniu, że strony zostały zapisane jako podklasa **WizardPageImpl**, można utworzyć nowe wystąpienie klasy **WmiRepoistory** podobnie do następującej:  

```  
PWmiRepository pWmi;  
CreateInstance(Container(), ID_WmiRepository, &pWmi);  
```  

 **CreateInstance** funkcja jest funkcją bezpieczne szablonu do tworzenia nowych wystąpień składników. **PWmiRepository** jest wskaźnika inteligentnego, więc obsługi Zliczanie dla Ciebie.  

#### <a name="creatable-components"></a>Możliwość utworzenia składników  
 Istnieje zestaw składników, które można zarejestrować za pomocą rejestru. Pierwszy zestaw składników zawsze jest zarejestrowana, ponieważ zapewnia głównego pliku wykonywalnego UDI kreatora. Dwa zestawy elementów są zawarte w "opcjonalne" biblioteki dll. Te składniki mają być dostępne biblioteki DLL musi być wymienione w **biblioteki dll** sekcji pliku .config w formacie XML. Kod nie musi wiedzieć, który pliku wykonywalnego zawiera określony składnik.  

 Lista identyfikatorów składników dla składników (nazwa składnika jest taka sama, jako identyfikator, ale bez początkowej *ID_*) zarejestrowany z fabryką rejestru (zdefiniowany w OSDSetupWizard) jest wyświetlany w tabeli 3.  

### <a name="table-3-component-ids"></a>Tabela 3. Identyfikatory składników  

|**ID**|**Opis**|  
|-|-|  
|ID_ACPowerTask|(ITask IWizardComponent) Zapewnia, że komputer nie jest uruchomiona na poziomie naładowania baterii tylko zadania wstępnego|  
|ID_AppDiscoveryTask|(ITask IWizardComponent) Specjalne zadanie odnajdywania, jakie oprogramowanie elementów, należy mieć zainstalowany na tym komputerze|  
|**ID_BackgroundTask**|(**IBackgroundTask**, **IWizardComponent**) może służyć do uruchamiania zadania w innym wątku|  
|**ID_CopyFilesTask**|(**ITask**, **IWizardComponent**) zadań, aby skopiować jeden lub więcej plików|  
|**ID_FormController**|(**IFormController**) będzie najbardziej tak, nie trzeba tworzyć wystąpienia samodzielnie, zgodnie ze strony odbiera własne wystąpienie|  
|**ID_InvalidCharactersValidator**|(**IValidator**) zapewnia, że żadne pole tekstowe zawiera znaki z listy, aby moduł weryfikacji|  
|**ID_Logger**|(**ILogger**) będzie najbardziej tak, nie trzeba tworzyć wystąpienia samodzielnie, zgodnie ze strony odbiera wskaźnikiem do współużytkowanego wystąpienia|  
|**ID_NonEmptyValidator**|(**IValidator**) moduł weryfikacji, który zapewnia, że żadne pole nie jest pusty|  
|**ID_PasswordValidator**|(**IValidator**) moduł weryfikacji, który zapewnia, że nie ma pól tekstowych mają taką samą zawartość|  
|**ID_Regex**|(**IRegEx**) ocenia wyrażeń regularnych, wyszukiwanie dopasowań|  
|**ID_RegExValidator**|(**IValidator**) sprawdzania poprawności weryfikuje względem wyrażenie regularne lub znanych wzorca|  
|**ID_SimpleStringProperties**|(**IStringProperties**, **ISimpleStringProperties**) zapewnia prosty sposób wysyłania właściwości do zadań bez użycia XML|  
|**ID_ShellExecuteTask**|(**ITask**, **IWizardComponent**) wykonanie programu zewnętrznego|  
|**ID_SummaryBag**|(**ISummaryBag**) dostępne pośrednio ze strony za pomocą metody formularza|  
|**ID_TaskManager**|(**ITaskManager**, **IBackgroundCallback**, **IWizardComponent**) służy do zarządzania systemem zestaw zadań i interfejsu użytkownika|  
|**ID_WmiRepository**|(**IWmiRepository**, **IWizardComponent**) służy do uruchamiania kwerendy Instrumentacji zarządzania Windows (WMI)|  
|**ID_IXmlDocument**|(**IXmlDocument**) zapewnia fasad odczytywanie i zapisywanie dokumentów XML|  

 W tabeli 4 i 5 tabeli przedstawiono zdefiniowanych OSDRefreshWizard.dll, udostępnionych stron i inne składniki formantu.  

### <a name="table-4-directory-controls"></a>Tabela 4. Formanty katalogu  

|**ID**|**Opis**|  
|-|-|  
|**ID_Directory**|(**IDirectory**) fasad uzyskiwania informacji katalogu z system plików|  

### <a name="table-5-defined-sharedpagesdll"></a>Tabela 5. Zdefiniowanych SharedPages.dll  

|**ID**|**Opis**|  
|-|-|  
|**ID_ADHelper**|(**IADHelper**) zapewnia fasad ograniczony zestaw funkcji w usługach domenowych Active Directory® (AD DS)|  
|**ID_CpuInfo**|(**ICpuInfo**) określa, czy ten Procesor, 32 lub 64-bitowa|  
|**ID_DomainJoinValidator**|(**IDomainJoinValidator**) zawiera niektóre metody sprawdzania, czy zestaw poświadczeń jest dozwolone w celu przyłączenia do domeny|  
|**ID_DriveList**|(**IDriveList**, **IBindableList**, **IWizardComponent**) używa usługi WMI, aby uzyskać listę dysków na komputerze|  
|**ID_WiredNetworkTask**|(**ITask**) zadania, które sprawdza, czy nawiązano połączenie z siecią zakodowane (a nie bezprzewodową) karty sieciowej|  

#### <a name="control-components"></a>Składniki formantu  
 Interakcji z kontrolki na stronie za pośrednictwem **GetControlWrapper** funkcji szablonu, który zapewnia dostęp do jednego z typów składników wymienione w tabeli 6.  

### <a name="table-6-components"></a>Tabela 6. Składniki  

|**Typy formantów okna dialogowego**|**Opis**|  
|-|-|  
|**CONTROL_CHECK_BOX**|(**ICheckBox**) fasad do pracy z formanty pól wyboru|  
|**CONTROL_COMBO_BOX**|(**IComboBox**) fasad dla formantów pola kombi|  
|**CONTROL_GENERIC**|(**IControl**) umożliwia pracę z większość typów kontroli w celu sterowania Włączanie i widoczności|  
|**CONTROL_LIST_VIEW**|(**IListView**) fasad, zapewniając dostęp do funkcji formantu widoku listy|  
|**CONTROL_PROGRESS_BAR**|(**IProgressBar**) fasad do pracy z pozycji formantu paska postępu|  
|**CONTROL_RADIO_BUTTON**|(**IRadioButton**) fasad do pracy z kontrolek przycisków radiowych|  
|**CONTROL_STATIC_TEXT**|(**IStaticText**) fasad, która zapewnia uprawnienia odczytu/zapisu do tekstu formantu, takie jak etykiety lub pola tekstowego|  
|**CONTROL_TREE_VIEW**|(**ItreeView**) fasad do pracy z formantem widoku drzewa|  

#### <a name="image-list-component"></a>Składnik listy obrazów  
 Ten składnik jest fasad dla **ImageList** na stronie. Tworzenie listy obrazów za pośrednictwem **IListView** lub **ITreeView** interfejsu.  

#### <a name="formcontroller-component"></a>Składnik FormController  
 Kreator utworzy ten składnik i przekazuje je do strony. Dostęp do niej z Twojej strony przy użyciu **formularza** metody, która **WizardPageImpl** implementuje klasy podstawowej.  

#### <a name="invalidcharactervalidator-component"></a>Składnik InvalidCharacterValidator  
 Jest to typ modułu sprawdzania poprawności, które mogą uwzględniać na stronie. Identyfikator jest **ID_InvalidCharactersValidator** (zdefiniowany w IValidator.h), która zawiera wartość tekstu "Microsoft.Wizard.Validation.InvalidChars."  

 Ten moduł weryfikacji sprawdza jednej właściwości ( **metody ustawiającej** elementu w pliku .config) o nazwie **InvalidChars**, który znajduje się lista znaków, które nie są dozwolone. Sprawdza znaków w polu tekstowym; Jeśli tekst zawiera wszystkie znaki z tej listy, składnik zgłasza błąd.  

#### <a name="nonemptyvalidator-component"></a>Składnik NonEmptyValidator  
 Jest to typ modułu sprawdzania poprawności, które mogą uwzględniać na stronie. Identyfikator jest **ID_NonEmptyValidator** (zdefiniowany w IValidator.h), która zawiera wartość tekstu "Microsoft.Wizard.Validation.NonEmpty."  

 Ten moduł weryfikacji zgłasza błąd, jeśli pole tekstowe (lub inny formant, który obsługuje **IStaticText**) ma wartość pustego ciągu.  

#### <a name="passwordvalidator-component"></a>Składnik PasswordValidator  
 Jest to typ modułu sprawdzania poprawności, które mogą uwzględniać na stronie. Identyfikator jest **ID_PasswordValidator** (zdefiniowany w IValidator.h), która zawiera wartość tekstu "Microsoft.Wizard.Validation.Password."  

 Ten moduł weryfikacji współpracuje z dwóch różnych formantów (określa, że wsparcie **IStaticText**) i zgłasza błąd, jeśli nie zawierają tych samych wartości. Innymi słowy, to niemożliwe, gdy **hasło** i **Potwierdź hasło** pola tekstowe nie są zgodne.  

 Ten moduł weryfikacji wymaga dwóch formantów, dlatego musi instalacji więcej niż inne moduły weryfikacji. Instalatora może wyglądać mniej więcej tak:  

```  
Form()->AddToGroup(IDC_EDIT_PASSWORD, IDC_EDIT_PASSWORD2);  
PValidator pValidator;  
Form()->AddValidator(IDC_EDIT_PASSWORD, ID_PasswordValidator, pMessage, &pValidator);  
PStaticText pPassword2;  
GetControlWrapper(View(), IDC_EDIT_PASSWORD2, CONTROL_STATIC_TEXT, &pPassword2);  
pValidator->SetProperty(0, pPassword2);  
```  

 Najpierw należy zdefiniować **Potwierdź hasło** formant jako element "podrzędny" **hasło** formantu. W ten sposób kontroler formularza wyłącza **hasło** kontroli, go spowoduje również wyłączenie **Potwierdź hasło** formantu. Następnie dodaj moduł weryfikacji hasła do formularza. Na koniec zapewniają interfejs do modułu sprawdzania poprawności hasła **Potwierdź hasło** formantu.  

 Ze względu na wymagania dla dwóch formantów należy użyć kodu do konfigurowania tego sprawdzania poprawności, a nie w pliku .config XML.  

#### <a name="regexvalidator-component"></a>Składnik RegExValidator  
 Jest to typ modułu sprawdzania poprawności, które mogą uwzględniać na stronie. Identyfikator jest **ID_RegExValidator** (zdefiniowany w IValidator.h), która zawiera wartość tekstu "Microsoft.Wizard.Validation.RegEx."  

 Ten moduł weryfikacji Porównuje zawartość kontrolki tekstu (obsługującą **IStaticText**) do wyrażenia regularnego i kończy się niepowodzeniem, jeśli tekst nie odpowiada wyrażeniu regularnemu.  

 Alternatywnie można użyć tego sprawdzania poprawności z wzorcem o nazwie wstępnie zdefiniowane. Aby użyć wyrażenia regularnego, XML musi zawierać metody ustawiającej właściwość o nazwie **wzorzec**. Jeśli chcesz zamiast tego użyj wzorca nazwanego, użyj metody ustawiającej o nazwie **NamedPattern** ustawić jedną z wartości w tabeli 7.  

### <a name="table-7-named-pattern-setters"></a>Tabela 7. Metody ustawiające wzorzec o nazwie  

|**Pattern**|**Opis**|  
|-|-|  
|Nazwa użytkownika|Sprawdza, czy tekst jest albo w postaci domena\użytkownik lub user@domain|  
|ComputerName|Nazwa musi należeć do zakresu od 1 do 15 znaków i nie może zawierać zestaw znaków (takich jak: a?)|  
|Workgroup|Nazwa musi należeć do zakresu od 1 do 15 znaków i nie może zawierać zestaw znaków (taki jak =, +, i?)|  

#### <a name="factoryregistry-component"></a>FactoryRegistry Component  
 Ten składnik przechowuje informacje o wszystkich fabryki klas i usług. Implementuje **IFactoryRegistry** interfejsu i jest dostępna pośrednio za pośrednictwem strony **kontenera** metody. Ponadto rejestru załadowanie biblioteki DLL rozszerzeń. Po ładuje bibliotekę DLL, rejestru szuka wyeksportowanej funkcji o nazwie **RegisterFactories**. Należy zaimplementować tę funkcję, a w nim zarejestrować fabryki klas dla stron, zadania i modułów sprawdzania poprawności (i innych fabryki klas, które chcesz zarejestrować). Oto przykład z przykładowy projekt:  

```  
extern "C" __declspec(dllexport) void RegisterFactories(IFactoryRegistry *factories)  
{  
Register<LocationPageFactory>(ID_LocationPage, factories);  
}  
```  

#### <a name="logger-component"></a>Składnik rejestratora  
 Ten składnik jest dostępny do strony za pomocą **rejestratora** — metoda (implementowane przez **WizardPageImpl**). Ta metoda umożliwia zapisywanie wpisów w pliku dziennika. Zawartość pliku dziennika są przydatne do diagnozowania problemów, które użytkownicy mogą mieć uruchomiony Kreator UDI.  

#### <a name="propertybag-component"></a>Składnik PropertyBag  
 *Zbioru właściwości* to kontener dla zmiennych pamięci. Jest dostępny za pomocą strony **Container() -> obiekcie Properties()**. Zmienne pamięci są przydatne podczas przekazywania danych tymczasowych spośród różnych stron.  

#### <a name="tsvariablebag-and-tsrepository-components"></a>TSVariableBag i składniki TSRepository  
 **TSVariableBag** składnik umożliwia odczytywanie i zapisywanie zmienne sekwencji zadań. Przechowuje wartości w pamięci dopóki użytkownik klika polecenie **Zakończ** (domyślnie). Dostęp można uzyskać **TSVariable** zbioru za pośrednictwem strony **TSVariables** — metoda (implementowane przez **WizardPageImpl** klasy podstawowej). Te składniki rejestrować wszystkie odczyty i zapisy zmiennych sekwencji zadań.  

#### <a name="wmirepository-component"></a>Składnik WmiRepository  
 Ten składnik zapewnia fasadowym przeznaczonym do pracy z kwerendy usługi WMI. Możesz wywołać **CreateInstance** funkcji pomocnika z **ID_WmiRepository** uzyskać wystąpienia tego składnika, który obsługuje **IWmiRepository** interfejsu. Ten składnik zwraca wynik rekordów za pomocą **IWmiIterator** interfejsu.  

###  <a name="WizardPageHelperClasses"></a> Klasy pomocy strony kreatora  
 Można tworzyć niestandardowe strony kreatora UDI przy użyciu klasy pomocy wbudowanych podana przy użyciu zestawu SDK UDI. Tabela 8 zawiera klasy pomocnicze, które służy do tworzenia kreatora niestandardowych stron.  

### <a name="table-8-helper-classes"></a>Tabela 8. Klasy pomocy  

|**Klasa pomocy**|**Opis**|  
|-|-|  
|[Klasa ClassFactoryImpl](#ClassFactoryImplClass)|Jest to przydatne klasa podstawowa dla tworzenia fabrykę klas, które następnie można zarejestrować za pomocą rejestru fabryki.|  
|[Interfejs szablonu klasy](#InterfaceTemplateClass)|Ta klasa szablonu należy używać do tworzenia składnika, który implementuje interfejs więcej niż jeden.|  
|[Klasa pomocnika ścieżki](#PathHelperClass)|Ta klasa udostępnia typowe operacje pliku/katalogu.|  
|[Wskaźnik szablonu klasy](#PointerTemplateClass)|Ta klasa udostępnia zliczanie okres istnienia zarządzania w programie COM — składniki. Należy zwolnić interfejsów po zakończeniu z nimi. Ta klasa szablon obsługuje okres istnienia automatycznie.|  
|[Klasa PUnknown](#PUnkownClass)|Ta klasa jest wskaźnika inteligentnego specjalnie z myślą o interfejsie IUnknown. Dla wszystkich innych interfejsów należy użyć klasy szablonu wskaźnika.|  
|[Klasa pomocy StringUtil](#StringUtilHelperClass)|Ta klasa zawiera metody pomocnicze, które ułatwiają pracy z ciągami.|  
|[Identyfikator szablonu klasy](#SubInterfaceTemplateClass)|Ta klasa podstawowa ułatwia wdrożenie składnik, który obsługuje interfejs tego samego dziedziczy inny interfejs.|  
|[UnknownImpl szablonu klasy](#UnknownImplTemplateClass)|Ta klasa obsługuje większość szczegółów tworzenia składnika modelu COM.|  
|[WizardComponent szablonu klasy](#WizardComponentTemplateClass)|Ta klasa podstawowa jest używany do tworzenia składników, które wymagają dostępu do usług kreatora, takich jak tworzenie składników i rejestrowania.|  
|[WizardPageImpl szablonu klasy](#WizardPageImplTemplateClass)|Ta klasa podstawowa powinien służyć jako klasa podstawowa dla wszystkich stron kreatora niestandardowego|  

####  <a name="ClassFactoryImplClass"></a> Klasa ClassFactoryImpl  
 Jest to przydatne klasa podstawowa dla tworzenia fabrykę klas, które następnie można zarejestrować za pomocą rejestru fabryki.  

 Poniżej przedstawiono fragment LocationPage.h plik przykładowy projekt do definiowania **ClassFactoryImpl** klasy.  

```  
#pragma once  

#include "ClassFactoryImpl.h"  

class LocationPageFactory :public ClassFactoryImpl  
{  
protected:  
    IUnknown *CreateNewInstance();  
};  
```  

 Poniżej przedstawiono fragment pliku LocationPage.cpp na stronie Kreatora przykładowych używane do definiowania fabryki klasy dla strony.  

```  
IUnknown *LocationPageFactory::CreateNewInstance()  
{  
    return static_cast<IWizardPage *>(new LocationPage);  
}  
```  

####  <a name="InterfaceTemplateClass"></a> Interfejs szablonu klasy  
 Ta klasa szablonu należy używać do tworzenia składnika, który implementuje interfejs więcej niż jeden — na przykład:  

```  
classLocationPage :public Interface<IFieldCallback, WizardPageImpl<IDD_LOCATION_PAGE>>  
```  

 Ten kod tworzy łańcuch klasy podstawowej, który obsługuje zarówno **IFieldCalback** i interfejsów który **WizardPageImpl** obsługuje (która stanie się być **IWizardPage**).  

####  <a name="PathHelperClass"></a> Klasa pomocnika ścieżki  
 Ta klasa udostępnia typowe operacje pliku/katalogu:  

```  
static inline std::wstring GetModulePath(HINSTANCE hModule)  
```  

 Zwraca także pełną ścieżkę do pliku .exe lub .dll dojście wystąpienia, które zapewniają do tej metody:  

```  
static inline std::wstring GetModuleFilename(HINSTANCE hModule)  
```  

 Klasa zwraca pełną ścieżkę i nazwę pliku .exe i .dll z podane dojście wystąpienia do tej metody:  

```  
static inline std::wstring GetDirecotryName(LPCWSTR fullName)  
```  

 . . . lub po prostu ścieżki podczas usuwanie nazwa pliku:  

```  
static inline std::wstring GetFileName(LPCWSTR fullName)  
```  

 Klasa pomocnika ścieżki podanej ścieżki pliku o nazwie, zwraca tylko nazwa pliku:  

```  
static inline std::wstring Combine(LPCWSTR path, LPCWSTR name)  
```  

 Ponadto klasa zwraca nowy ciąg, który jest nazwa połączone ścieżki i plik (lub inną ścieżkę).  

####  <a name="PointerTemplateClass"></a> Wskaźnik szablonu klasy  
 Ta klasa jest zdefiniowana w Pointer.h. Ponieważ składniki COM używają Zliczanie dla Zarządzanie okresem istnienia, ważne jest zawsze wersji interfejsów po zakończeniu z nimi. Firma Microsoft udostępnia szablonu klasy, która obsługuje okres istnienia automatycznie. Na przykład jeśli chcesz wskaźnika inteligentnego dla interfejsu XML można zapisać podobny do następującego:  

```  
Pointer<IXMLDOMNode> pNewChild  
pXmlDom->CreateNode(NODE_ELEMENT, L"MyElement", L"", &pNewChild);  
```  

 Pierwszy wiersz definiuje wskaźnika inteligentnego. Drugi wiersz zawiera pobierania wskaźnika inteligentnego przez inne połączenie. **&** Operator zawsze zwalnia istniejącego interfejsu, jeśli zawiera jeden i zwraca adres wewnętrzny wskaźnik. Po pobraniu wskaźnik takie, **wskaźnika** wystąpienie wywołania **wersji** automatycznie, gdy zmienna wykracza poza zakres. Firma Microsoft zaleca użycie wskaźniki inteligentne zamiast wywoływać metodę **AddRef** i **wersji** ręcznie.  

 Ponadto **wskaźnika** wywołania klasy wskaźnik inteligentny **QueryInterface** pobrać inne interfejsy. Na przykład gdy rejestr fabryczny tworzy nowe wystąpienie składnika, ma kod w następujący sposób:  

```  
PWizardComponent pComp = pUnknown;  
if (pComp != nullptr)  
    pComp->SetContainer(m_pContainer);  
```  

 Pierwsze wywołania wiersza **QueryInterface** w tle, aby zażądać **IWizardComponent** interfejsu. Wynikowa wskaźnik inteligentny będzie równa **nullptr** Jeśli składnik nie obsługuje ten interfejs.  

####  <a name="PUnkownClass"></a> Klasa PUnknown  
 Ta klasa jest wskaźnika inteligentnego specjalnie z myślą o **IUnknown** interfejsu. Dla wszystkich innych interfejsów, użyj **wskaźnika** klasy szablonu.  

####  <a name="StringUtilHelperClass"></a> Klasa pomocy StringUtil  
 Ta klasa jest zdefiniowana w Utilities.h i udostępnia metody pomocnicze, które ułatwiają pracy z ciągami:  

```  
static inline int CompareIgnore(LPCWSTR first, LPCWSTR second)  
```  

 Ta metoda porównuje dwa ciągi podczas ignoruje wielkość liter (patrz tabela 9).  

### <a name="table-9-stringutil-helper-class"></a>Tabela 9. Klasa pomocy StringUtil  

|**Zwraca**|**Opis**|  
|-|-|  
|**0**|Parametry są zgodne, bez uwzględnienia wielkości liter|  
|**<0**|Pierwszy < drugi|  
|**>0**|Pierwszy > drugi|  

 Oto przykład:  

```  
static inline std::wstring Format(LPCWSTR input, int index, LPCWSTR value)  
static inline std::wstring Format(LPCWSTR input, int index, DWORD value)  
```  

 Te metody są nieco takich jak Microsoft .NET **Format** metody w tym sensie, że parametry są w formie **{0}**. Jednak nie wykonują formatowania danych wejściowych — tylko podstawienia:  

```  
static inline std::wstring Printf(std::wstring format, I val)  
static inline std::wstring Printf(std::wstring format, I val1, J val2)  
static inline std::wstring Printf(std::wstring format, I val1, J val2, K val3)  
static inline std::wstring Printf(std::wstring format, I val1, J val2, K val3, L val4)  
```  

 Są to otoki wokół **StringCchPrintf** zwracające **wstring** dzięki czemu nie trzeba przydzielić pamięci dla ciągów lub buforów samodzielnie.  

####  <a name="SubInterfaceTemplateClass"></a> Identyfikator szablonu klasy  
 Ta klasa podstawowa ułatwia wdrożenie składnik, który obsługuje interfejs tego samego dziedziczy inny interfejs. Na przykład **ICheckBox** dziedziczy interfejs **IControl**. Oto, jak ta klasa służy do definiowania **CheckBoxWrapper**:  

```  
classCheckBoxWrapper :public SubInterface<IControl, UnknownImpl<ICheckBox> >  
```  

 Interfejs podstawowy jest pierwszym parametrem, gdy drugi parametr jest interfejsu pochodnego.  

####  <a name="UnknownImplTemplateClass"></a> UnknownImpl szablonu klasy  
 Ta klasa jest zdefiniowana w UnknownImpl.h i obsługuje większość szczegółów tworzenia składnika modelu COM. Poniżej przedstawiono przykład sposobu użyje tej klasy podstawowej:  

```  
classDirectory :public UnknownImpl<IDirectory>  
```  

 Ten kod definiuje klasę, która obsługuje **IDirectory** interfejsu.  

####  <a name="WizardComponentTemplateClass"></a> WizardComponent szablonu klasy  
 Ta klasa jest zdefiniowana w IWizardComponent.h i jest klasą podstawową przydatne do tworzenia składników, które wymagają dostępu do usług kreatora, takich jak tworzenie składników i rejestrowania.  

 Na przykład poniżej przedstawiono sposób **CopyFilesTask** określono składnika:  

```  
classCopyFilesTask :public WizardComponent<ITask>  
{  
    ...  
```  

 Parametr dla tej klasy szablonu jest interfejsem "main" ma być używany dla składnika, czyli w przypadku zadania **ITask**. Przy użyciu **WizardComponent** oznacza, że składnik obsługuje zarówno interfejs użytkownika Podaj (**ITask** w tym przykładzie) i **IWizardComponent**.  

 Zawsze, gdy używasz rejestr fabryczny klasa do tworzenia nowego składnika rejestru wywołuje składnik **IWizardComponent -> SetContainer** metodę w celu zapewnienia składnika dostęp do usług kreatora.  

####  <a name="WizardPageImplTemplateClass"></a> WizardPageImpl szablonu klasy  
 Klasa jest używana jako klasa podstawowa dla niestandardowych stron — na przykład:  

```  
class LocationPage :public WizardPageImpl<IDD_LOCATION_PAGE>  
```  

 Parametr jest identyfikator zasobu szablonu — okno dialogowe.  

###  <a name="WizardPageInterfaces"></a> Interfejsy strony kreatora  
 Kreator UDI używa interfejsów do dostęp inne formanty na stronie. Na stronie możesz użyć **GetControlWrapper** funkcji, aby pobrać otoki formantu. Oto przykład:  

```  
PStaticText pFormat;  
GetControlWrapper(View(), IDC_CHECK_PARTITION, CONTROL_STATIC_TEXT, &pFormat);  
```  

 W tym miejscu **PStaticText** jest wskaźnik inteligentny **IStaticText** interfejsu. Wskaźniki inteligentne automatycznie wywołania modelu COM **Release()** metodą podczas ich się znaleźć poza zakresem lub Przekaż adresu zmiennej (takich jak **& pFormat**) do metody.  

#### <a name="iadhelper-interface"></a>Interfejs IADHelper  

```  
__interfaceIADHelper : IUnknown  
{  
    HRESULT Init(ILogger *pLogger);  
    HRESULT ValidLogon(LPCTSTR userName, LPCTSTR password, LPCTSTR domain);  
    HRESULT HasAccess(LPCTSTR username, LPCTSTR password, LPCTSTR domain, LPCTSTR computerName, LPCTSTR accountDomain);  
};  

```  

##### <a name="hresult-initilogger-plogger"></a>HRESULT Init(ILogger \*pLogger)  
 Inicjowanie tego składnika, przekazywanie do rejestratora, dzięki czemu można rejestrować informacje.  

##### <a name="hresultvalidlogonlpctstr-username-lpctstr-password-lpctstr-domain"></a>HRESULTValidLogon (LPCTSTR nazwy użytkownika, hasło LPCTSTR LPCTSTR domeny)  
 Ta metoda sprawdza, czy zestaw poświadczeń jest prawidłowy, jak pokazano w tabeli 10.  

### <a name="table-10-hresultvalidlogon"></a>Tabela 10. HResultValidLogon  

|**HResult**|**Opis**|  
|-|-|  
|S_OK|Poświadczenia są prawidłowe|  
|S_FALSE|Poświadczenia są nieprawidłowe|  
|E_FAIL|Nie można zlokalizować kontrolera domeny; Sprawdź dzienniki, aby uzyskać więcej informacji|  

##### <a name="hresult-hasaccesslpctstr-username-lpctstr-password-lpctstr-domain-lpctstr-computername-lpctstr-accountdomain"></a>HRESULT HasAccess(LPCTSTR username, LPCTSTR password, LPCTSTR domain, LPCTSTR computerName, LPCTSTR accountDomain)  
 Ta metoda sprawdza, czy zestaw poświadczeń, ma dostęp do odczytu i zapisu do obiektu komputera w usługach AD DS, jak pokazano w tabeli 11.  

### <a name="table-11-hresult-hasaccess"></a>Tabela 11. HResult HasAccess  

|**HRESULT**|**Opis**|  
|-|-|  
|S_OK|Użytkownik ma dostęp|  
|E_FAIL|Użytkownik nie ma dostępu. Sprawdź plik dziennika, aby uzyskać dodatkowe informacje.|  

#### <a name="ibackgroundtask-interface"></a>Interfejs IBackgroundTask  

```  
__interface IBackgroundTask : IUnknown  
{  
    HRESULT Init(ITask *pTask, int id, IBackgroundCallback *pCallback);  
    void Start(void);  
    BOOL Running(void);  
    HRESULT Wait(DWORD waitMilliseconds);  
    HRESULT Terminate(DWORD exitCode);  
    HRESULT GetExitCode(LPDWORD pCode, HRESULT *pHresult);  
    HRESULT Close(void);  
};  
```  

##### <a name="overview"></a>Omówienie  
 **Postępu** strona korzysta z tej klasy do uruchamiania zadań w oddzielnym wątku. Umożliwia także ta klasa służy do wykonywania operacji na oddzielnym wątku. *Zadania* są wszystkie klasy, która obsługuje **ITask** interfejsu.  

 Ten interfejs jest implementowany przez **ID_BackgroundTask** zdefiniowanych w interfejsie IBackgroundTask.h składnika ("Microsoft.Wizard.BackgroundTask").  

##### <a name="hresult-inititask-ptask-int-id-ibackgroundcallback-pcallback"></a>HRESULT Init(ITask \*pTask, int id, IBackgroundCallback \*pCallback)  
 Ten interfejs inicjuje składnika, jak pokazano w tabeli 12.  

### <a name="table-12-hresult-init"></a>Tabela 12. HRESULT Init  

|**Parametr**|**Opis**|  
|-|-|  
|**pTask**|Wskaźnik do klasy, która zawiera kod, który chcesz uruchomić w innym wątku|  
|**Id**|Numer, można użyć w metodę wywołania zwrotnego **Zakończono** metodę, aby sprawdzić, które zadanie zakończone uruchomiony; przydatne w przypadku uruchamiania kilka zadań o tej samej metody wywołania zwrotnego|  
|**pCallback**|Klasa, która implementuje **Zakończono** metodę, która jest wywoływana, gdy zadanie zakończeniu; wywołanie **Zakończono** metoda będzie w wątku tła nie wątku interfejsu użytkownika|  

##### <a name="void-startvoid"></a>void Start(void)  
 Ta metoda uruchamia zadanie wątku w tle i zwraca elementy wyświetlane w tabeli 13.  

### <a name="table-13-return-background-thread"></a>Tabela 13. Zwraca wątku w tle  

|**Zwraca**|**Opis**|  
|-|-|  
|**E_INVALIDARG**|Zadanie jest już uruchomione, więc nie można uruchomić go teraz.|  
|**E_FAIL**|Wystąpił problem z uruchomieniem wątku.|  
|**S_OK**|Wątek został uruchomiony.|  

##### <a name="bool-running"></a>Wartość logiczna Running()  
 Ta metoda zwraca wartość TRUE, jeśli zadanie w tle jest uruchomiony i wartość FALSE, jeśli nie jest uruchomiona.  

##### <a name="hresult-waitdword-waitmilliseconds"></a>HRESULT Wait(DWORD waitMilliseconds)  
 Ta metoda oczekuje, aż wątek przestanie działać albo wyrażony w milisekundach czas upłynął.  

##### <a name="hresult-terminatedword-exitcode"></a>HRESULT Terminate(DWORD exitCode)  
 Ta metoda kasuje wątku, który jest uruchomiony (patrz tabela 14 i tabela 15). Ten proces może potrwać krótkim czasu po powrocie z tej metody.  

### <a name="table-14-hresult-terminate-exit-code"></a>Tabela 14. Kod zakończenia przerwanie HRESULT  

|**Parametr**|**Opis**|  
|-|-|  
|**exitCode**|Kod zakończenia, który zostanie wysłany do metody Zakończono wywołania zwrotnego, która będzie także dostępna z **GetExitCode** metody.|  

### <a name="table-15-termination-codes"></a>Tabela 15. Kody zakończenia  

|**Zwraca**|**Opis**|  
|-|-|  
|**E_FAIL**|Nie można wywołać, aby zakończyć.|  
|**S_OK**|Żądanie zakończenie wątku powiodło się.|  

##### <a name="hresult-getexitcodelpdword-pcode-hresult-phresult"></a>HRESULT GetExitCode(LPDWORD pCode, HRESULT \*pHresult)  
 Ta metoda umożliwia wyniki uruchomienia zadania dla wątku w tle (patrz tabela 16).  

### <a name="table-16-result-codes"></a>Tabela 16. Kody wyników  

|**Parametr**|**Opis**|  
|-|-|  
|**pCode**|Wskaźnik do **DWORD** który ustawi przy powrocie lub **nullptr** , jeśli nie są zwracane wartości. Po zakończeniu tego parametru jest równa **STILL_ACTIVE** Jeśli wątek jest uruchomiony, kod zwrócony przez zadania **Execute** metody lub wartość przekazana do **przerwania** — metoda Jeśli wywołana metoda.|  
|**pHresult**|Wskaźnik do **HRESULT** który ustawi przy powrocie lub **nullptr** Jeśli nie potrzebujesz **HRESULT** wartość.|  

##### <a name="hresult-closevoid"></a>HRESULT Close(void)  
 Ta metoda zwalnia wątku w tle. Zwraca **E_INVALIDARG** Jeśli wątek jest uruchomiony i **S_OK** inaczej.  

#### <a name="icheckbox-interface"></a>Interfejs ICheckBox  

```  
__interface ICheckBox : IControl  
{  
    void Check(BOOL check);  
    BOOL IsButtonChecked();  
};  
```  

##### <a name="void-checkbool-check"></a>Sprawdź void (Sprawdź wartość logiczna)  
 Ustaw stan zaznaczenia pola wyboru. Metoda ma wartość TRUE, pole wyboru jest zaznaczone; gdy metoda ma wartość FALSE, pole wyboru jest wyczyszczone.  

##### <a name="bool-isbuttonchecked"></a>Wartość logiczna IsButtonChecked()  
 Ta metoda zgłasza bieżącego wyboru stanu pola wyboru.  

#### <a name="icombobox-interface"></a>Interfejs IComboBox  

```  
__interface IComboBox : IControl  
{  
    HRESULT Bind([in] IBindableList *pList);  
    HRESULT Select(int index);  
    int Selected(void);  
    void Add([in] LPCTSTR caption);  
    HRESULT GetText([out, retval] LPBSTR pText);  
    void Clear();  
};  
```  

##### <a name="overview"></a>Omówienie  
 Ten interfejs jest implementowany przez **CheckBoxWrapper** składnika. Pobiera wystąpienie tego składnika przy użyciu **GetControlWrapper** funkcji Pomocnik z typem **CONTROL_COMBO_BOX**.  

##### <a name="hresult-bindin-ibindablelist-plist"></a>HRESULT Bind([in] IBindableList \*pList)  
 Użyj tej metody, jeśli masz źródło danych, który implementuje **IBindableList** interfejsu. Pole listy inicjuje zawartość z napisami z tej listy.  

##### <a name="hresult-selectint-index"></a>HRESULT Select(int index)  
 Wybierz element w polu kombi w indeksie.  

##### <a name="int-selectedvoid"></a>int Selected(void)  
 Ta metoda zwraca indeks wybranego elementu lub **-1** Jeśli nic nie jest zaznaczone.  

##### <a name="void-addin-lpctstr-caption"></a>Dodaj void ([in] LPCTSTR podpisu)  
 Ręcznie Dodaj element do pola kombi.  

##### <a name="hresult-gettextout-retval-lpbstr-ptext"></a>HRESULT GetText([out, retval] LPBSTR pText)  
 Pobierz ciąg aktualnie zaznaczonego elementu w polu kombi.  

##### <a name="void-clear"></a>metody Clear() void  
 Usuń wszystkie elementy w polu kombi.  

#### <a name="icontrol-interface"></a>Interfejs IControl  

```  
__interface IControl : IUnknown  
{  
    HRESULT SetEnable(BOOL enable);  
    BOOL IsEnabled(void);  
    HRESULT SetVisible(BOOL visible);  
};  
```  

##### <a name="overview"></a>Omówienie  
 Ten interfejs jest implementowany przez **ControlWrapper** składnika. Pobiera wystąpienie tego składnika przy użyciu **GetControlWrapper** funkcji Pomocnik z typem **CONTROL_GENERIC**.  

##### <a name="hresult-setenablebool-enable"></a>HRESULT SetEnable(BOOL enable)  
 Włącza lub wyłącza formant.  

##### <a name="bool-isenabledvoid"></a>Wartość logiczna IsEnabled(void)  
 Zwraca wartość PRAWDA, jeśli formant jest włączony, wartość FALSE, jeśli nie jest.  

##### <a name="hresult-setvisiblebool-visible"></a>HRESULT SetVisible(BOOL visible)  
 Pokaż lub Ukryj formantu.  

#### <a name="icpuinfo-interface"></a>Interfejs ICpuInfo  

```  
__interface ICpuInfo : IUnknown  
{  
    BOOL Is64Bit(void);  
};  
```  

##### <a name="overview"></a>Omówienie  
 Ten interfejs można uzyskać, tworząc nową **ID_CpuInfo** składnika. Pojedynczej metody informuje, czy Procesor jest 32 lub 64-bitowa. Należy pamiętać, że mając 32-bitowym systemie operacyjnym na komputerze 64-bitowym, ta metoda zwraca wartość TRUE, ponieważ jest on tylko raporty szerokość procesora CPU (nie systemu operacyjnego).  

##### <a name="idirectory-interface"></a>Interfejs IDirectory  

```  
__interface IDirectory : IUnknown  
{  
    BOOL FileExists(LPCWSTR name);  
    BOOL FindFirst([in] LPCWSTR name);  
    HRESULT FoundName([out, retval] LPBSTR name);  
    DWORD FoundAttributes(void);  
    BOOL FindNext(void);  
    void FinishFind(void);  
};  
```  

###### <a name="overview"></a>Omówienie  
 **Katalogu** składników, które można tworzyć przy użyciu **ID_Directory**, zapewnia fasadowym przeznaczonym do pracy z katalogów w systemie plików.  

###### <a name="bool-fileexistslpcwstr-name"></a>Wartość logiczna FileExists(LPCWSTR name)  
 Ta metoda zwraca wartość PRAWDA, jeśli istnieje plik o podanej nazwie.  

###### <a name="bool-findfirstin-lpcwstr-name"></a>Wartość logiczna FindFirst([in] LPCWSTR name)  
 Ta metoda umożliwia znalezienie pierwszego dopasowania dla nazwy podane przez użytkownika. Obsługuje znaki symboli wieloznacznych, a zwraca nazw zarówno plików i katalogów. Metoda zwraca wartość PRAWDA, jeśli znaleziono dopasowania, wartość FALSE w przeciwnym razie wartość.  

###### <a name="hresult-foundnameout-retval-lpbstr-name"></a>HRESULT FoundName([out, retval] LPBSTR name)  
 Ta metoda pobiera nazwę pliku, znaleziono wywołanie **FindFirst** lub **FindNext**.  

###### <a name="dword-foundattributesvoid"></a>DWORD FoundAttributes(void)  
 Ta metoda zwraca wartość atrybutu najnowszych znaleziono pliku lub katalogu. Aby sprawdzić, czy jest katalog można w następujący sposób użyć kodu:  

```  
pDirectory->FoundAttributes() & FILE_ATTRIBUTE_DIRECTORY  
```  

###### <a name="bool-findnextvoid"></a>Wartość logiczna FindNext(void)  
 Znajdź następny. Ta metoda zwraca wartość PRAWDA, jeśli inny dopasowania został znaleziony, wartość FALSE w przeciwnym razie wartość.  

###### <a name="void-finishfindvoid"></a>void FinishFind(void)  
 Ta metoda zwalnia zasoby używane dla operacji wyszukiwania.  

#### <a name="idomainjoinvalidator-interface"></a>Interfejs IDomainJoinValidator  

```  
__interface IDomainJoinValidator : IUnknown  
{  
    HRESULT Init(ILogger *pLogger, IWizardPageContainer *pContainer, IStaticText *pUsername, IStaticText *pPassword, IStaticText *pComputerName);  
    HRESULT IsUsernameValid(LPCWSTR domainName);  
    BOOL CanModifyComputerAdEntry(LPCWSTR domainName);  
};  
```  

##### <a name="overview"></a>Omówienie  
 Uzyskać wystąpienia przy użyciu tego interfejsu **ID_DomainJoinValidator** do wartości **CreateInstance** funkcji szablonu.  

##### <a name="hresult-initilogger-plogger-iwizardpagecontainer-pcontainer-istatictext-pusername-istatictext-ppassword-istatictext-pcomputername"></a>HRESULT Init (ILogger \*pLogger, IWizardPageContainer \*pContainer, IStaticText \*pUsername, IStaticText \*pPassword, IStaticText \*pComputerName)  
 Inicjowanie wystąpienia, jak pokazano w tabeli 17.  

### <a name="table-17-hresult-init---instance-initialization"></a>Tabela 17. HRESULT Init - inicjowania wystąpienia  

|**Parametr**|**Opis**|  
|-|-|  
|**pLogger**|Wystąpienia rejestratora, która jest dostępna na stronie za pośrednictwem strony **rejestratora** — metoda|  
|**pContainer**|Przekazuje wyniki ze strony użytkownika **kontenera** — metoda|  
|**pUsername**|Pole tekstowe, zawierające nazwę użytkownika, który ma zostać zweryfikowana|  
|**pPassword**|Pole tekstowe, które zawiera hasło do sprawdzenia poprawności|  
|**PComputerName**|Pole tekstowe, który zawiera nazwę komputera, który ostatecznie zostanie dołączona do domeny|  

##### <a name="hresult-isusernamevalidlpcwstr-domainname"></a>HRESULT IsUsernameValid(LPCWSTR domainName)  
 Ta metoda używa **IADHelper -> ValidLogon** metody w pracy. Zobacz tej metody, aby uzyskać szczegółowe informacje.  

##### <a name="bool-canmodifycomputeradentrylpcwstr-domainname"></a>Wartość logiczna CanModifyComputerAdEntry(LPCWSTR domainName)  
 Sprawdź, czy użytkownik ma uprawnienia do modyfikowania wpisu komputera. Większość pracy odbywa się **IADHelper -> HasAccess**. Jeśli ta metoda zwraca wartość FALSE, sprawdź plik dziennika, aby uzyskać szczegółowe informacje.  

#### <a name="idrivelist-interface"></a>Interfejs IDriveList  

```  
__interface IDriveList : IUnknown  
{  
    HRESULT Init(IWmiRepository *pWmi);  
    HRESULT SetWhereClause(LPCTSTR whereClause);  
    HRESULT SetMinimumDriveSize(__int64 size);  
    HRESULT Update(void);  
    HRESULT AddProperty(ENUM_DISK_QUERY_SECTION section, LPCTSTR propName, LPCTSTR propNameReturned);  

    size_t Count(void);  
    HRESULT GetProperty(size_t index, LPCTSTR propName,  LPVARIANT value);  
    HRESULT GetCaption(size_t index,  LPBSTR pCaption);  
}  
```  

##### <a name="hresult-initiwmirepository-pwmi"></a>HRESULT Init(IWmiRepository \*pWmi)  
 Tę metodę należy wywołać przed wywołaniem innych składników. Musisz utworzyć nowy **WmiRepository** przed wywołaniem tej metody.  

##### <a name="hresult-setwhereclauselpctstr-whereclause"></a>HRESULT SetWhereClause(LPCTSTR whereClause)  
 Ta metoda umożliwia dodanie tekstu, który będzie wyświetlany jako klauzula "where" w zapytaniu. Na przykład następujące polecenie zwraca tylko dyski USB:  

```  
pDrives->SetWhereClause(L"WHERE InterfaceType='USB'");  
```  

##### <a name="hresult-setminimumdrivesizeint64-size"></a>HRESULT SetMinimumDriveSize (\_rozmiar _int64)  
 Minimalizuj rozmiar dysku, należy ustawić w bajtach dyski, które będą zwracane z kwerendy.  

##### <a name="hresult-updatevoid"></a>HRESULT Update(void)  
 Wykonanie kwerendy. Lista dysków dostępne po wywołaniu tej metody jest sortowana przez literę dysku.  

##### <a name="hresult-addpropertyenumdiskquerysection-section-lpctstr-propname-lpctstr-propnamereturned"></a>HRESULT AddProperty(ENUM_DISK_QUERY_SECTION section, LPCTSTR propName, LPCTSTR propNameReturned)  
 Ta metoda dodaje nazwy dodatkowe właściwości, które mają być dostępne w wynikach zapytania. Wywołanie tej metody przed wywołaniem **aktualizacji**. Tabela 18 zawiera trzy przydatnych właściwości.  

### <a name="table-18-hresult-addproperty-useful-properties"></a>Tabela 18. HRESULT AddProperty: Przydatne właściwości  

|**Sekcja**|**Właściwość**|**Opis**|  
|-|-|-|  
|**DISKQUERY_LOGICALDISK**|**Rozmiar**|Rozmiar w bajtach reprezentowany jako ciąg|  
|**DISKQUERY_DISKPARTITION**|**DiskIndex**|Numer dysku jako liczbę całkowitą z zakresu od 0|  
|**DISKQUERY_LOGICALDISK**|**VolumeName**|Etykieta woluminu|  

##### <a name="sizet-countvoid"></a>size_t Count(void)  
 Liczba rekordów, które zwraca zapytanie. Wywołanie **aktualizacji** przed wywołaniem tej metody.  

##### <a name="hresult-getpropertysizet-index-lpctstr-propname--lpvariant-value"></a>HRESULT GetProperty(size_t index, LPCTSTR propName, LPVARIANT value)  
 Ta metoda pobiera wartość właściwości z wyników zapytania, jak pokazano w tabeli 19.  

### <a name="table-19-hresult-getproperty"></a>Tabela 19. HRESULT GetProperty  

|**Parametr**|**Opis**|  
|-|-|  
|**Indeks**|Liczony od zera indeks w rekordzie wyników|  
|**propName**|Nazwa właściwości, na przykład "Rozmiar"|  
|**Wartość**|Przy powrocie ten parametr zawiera wartość wariantu właściwości|  

##### <a name="hresult-getcaptionsizet-index--lpbstr-pcaption"></a>HRESULT GetCaption(size_t index, LPBSTR pCaption)  
 Ta metoda pobiera podpis, zmień rekordu jest taka sama jak **podpis** właściwości.  

#### <a name="iimagelist-interface"></a>Interfejs IImageList  

```  
__interface IImageList  
{  
    HRESULT CreateImageList(int width, int height, UINT flags);  
    HImageList GetImageList(void);  
    int AddImage(HInstance hInstance, int resourceId);  
};  
```  

##### <a name="overview"></a>Omówienie  
 Ten interfejs jest implementowany przez **ImageList** składnika. Pobiera wystąpienie tego składnika z **IListView** interfejsu.  

##### <a name="hresult-createimagelistint-width-int-height-uint-flags"></a>HRESULT CreateImageList(int width, int height, UINT flags)  
 Utwórz nową listę obrazu, który zarządza tego składnika. Tę metodę należy wywołać tylko raz.  

##### <a name="himagelist-getimagelistvoid"></a>HImageList GetImageList(void)  
 Ta metoda zwraca dojście do listy obrazów, w przypadku, gdy trzeba wykonać inne operacje dotyczące listy obrazów.  

##### <a name="int-addimagehinstance-hinstance-int-resourceid"></a>int AddImage (wystąpienie wystąpienie HInstance hInstance, int resourceId)  
 Dodaj nowy obraz do listy obrazów z zasobem, jak pokazano w tabeli 20.  

### <a name="table-20-hresult-iimagelist-interface"></a>Tabela 20. Interfejs IImageList HRESULT  

|**Parametr**|**Opis**|  
|-|-|  
|**hInstance**|Dojście wystąpienia modułu zawierającego zasobu mapy bitowej|  
|**resourceId**|Identyfikator zasobu, aby załadować do listy obrazów|  

#### <a name="ilistview-interface"></a>Interfejs IListView  

```  
__interface IListView : IControl  
{  
    int AddItem([in] LPCTSTR text);  
    int AddColumn(int width, [in] LPCTSTR text);  
    HRESULT SetSubItem(int index, int column, [in] LPCTSTR text);  
    int GetWidth(void);  
    void SetExtendedStyle(DWORD style);  
    int GetSelectedItem(void);  
    HRESULT SelectItem(int index);  
    BOOL IsItemChecked(int index);  
    int GetItemCount(void);  
    HRESULT CreateImageList(int width, int height, UINT flags);  
    int AddImage(HINSTANCE hInstance, int resourceId);  
    HRESULT SetImage(int index, int imageIndex);  
    HRESULT Clear(void);  
};  
```  

##### <a name="overview"></a>Omówienie  
 Ten interfejs jest implementowany przez **ControlWrapper** składnika. Pobiera wystąpienie tego składnika przy użyciu **GetControlWrapper** funkcji Pomocnik z typem **CONTROL_LIST_VIEW**.  

##### <a name="int-additemin-lpctstr-text"></a>int AddItem ([in] tekst LPCTSTR)  
 Dodaj nowy wiersz do pola listy. Zwraca indeks elementu dodaną.  

##### <a name="int-addcolumnint-width-in-lpctstr-text"></a>int AddColumn (szerokość int, tekst LPCTSTR [in])  
 Dodaj nową kolumnę do widoku listy.  

##### <a name="hresult-setsubitemint-index-int-column-in-lpctstr-text"></a>HRESULT SetSubItem(int index, int column, [in] LPCTSTR text)  
 Ustawianie tekstu w kolumnie inne niż pierwsza kolumna pola listy, jak pokazano w tabeli 21.  

### <a name="table-21-hresult-setsubitem"></a>Tabela 21. HRESULT SetSubItem  

|**Parametr**|**Opis**|  
|-|-|  
|**index**|Indeks elementu listy, który chcesz zmodyfikować|  
|**column**|Indeks kolumny, które chcesz zaktualizować; Pierwsza kolumna została skonfigurowana z **AddItem**, dwóch kolumn i następujących są konfigurowane przy użyciu tej metody|  
|**Tekst**|Ciąg wyświetlany w kolumnie|  

##### <a name="int-getwidthvoid"></a>int GetWidth(void)  
 Ta metoda zwraca szerokość pola cały tekst.  

##### <a name="void-setextendedstyledword-style"></a>void SetExtendedStyle(DWORD style)  
 Ta metoda umożliwia ustawienie rozszerzone style pola listy — na przykład:  

```  
m_pList->SetExtendedStyle(LVS_EX_FULLROWSELECT);  
```  

##### <a name="int-getselecteditemvoid"></a>int GetSelectedItem(void)  
 Ta metoda zwraca indeks aktualnie wybranego elementu widoku listy.  

##### <a name="hresult-selectitemint-index"></a>HRESULT SelectItem(int index)  
 Ustawienie wybranego elementu listy do tego indeksu.  

##### <a name="bool-isitemcheckedint-index"></a>Wartość logiczna IsItemChecked(int index)  
 Ta metoda zwraca wartość PRAWDA, jeśli wybrano element na liście. Ta metoda wymaga, aby wywołać **SetExtendedStyle** na ustawienie stylu pola wyboru.  

##### <a name="int-getitemcountvoid"></a>int GetItemCount(void)  
 Ta metoda zwraca liczbę elementów w widoku listy.  

##### <a name="hresult-createimagelistint-width-int-height-uint-flags"></a>HRESULT CreateImageList(int width, int height, UINT flags)  
 Utwórz nową listę obrazu i dołącz je do widoku listy.  

##### <a name="int-addimagehinstance-hinstance-int-resourceid"></a>int AddImage (wystąpienie wystąpienie HINSTANCE hInstance, int resourceId)  
 Dodawanie obrazu do widoku listy, listy obrazów. Należy wywołać **CreateImageList**, pierwszy.  

##### <a name="hresult-setimageint-index-int-imageindex"></a>HRESULT SetImage(int index, int imageIndex)  
 Ustawianie obrazu, która będzie wyświetlana po lewej stronie dla elementu widoku listy określonych.  

##### <a name="hresult-clearvoid"></a>HRESULT Clear(void)  
 Usuń wszystkie elementy z widoku listy.  

#### <a name="iprogressbar-interface"></a>Interfejs IProgressBar  

```  
__interface IProgressBar : IControl  
{  
    HRESULT SetPercentage(int position);  
    int GetPercentage(void);  
};  
```  

##### <a name="overview"></a>Omówienie  
 Ten interfejs jest implementowany przez **ProgressBarWrapper** składnika. Pobiera wystąpienie tego składnika przy użyciu **GetControlWrapper** funkcji Pomocnik z typem **CONTROL_PROGRESS_BAR**.  

##### <a name="hresult-setpercentageint-position"></a>HRESULT SetPercentage(int position)  
 Ustaw położenie postępu, korzystając z liczbą z zakresu od 0 do 100. Domyślnie nowe paski postępu Win32® mają maksymalną wielkość zakresu wynoszącą 100.  

##### <a name="int-getpercentagevoid"></a>int GetPercentage(void)  
 Ta metoda zwraca bieżącą pozycję pasek postępu.  

#### <a name="iradiobutton-interface"></a>Interfejs IRadioButton  

```  
__interface IRadioButton : IControl  
{  
public:  
    void SetGroup(int firstId, int lastId);  
    void CheckRadio(int id);  
    BOOL IsButtonChecked(int id);  
    void EnableRadio(int id, BOOL enable);  
};  
```  

##### <a name="overview"></a>Omówienie  
 Ten interfejs jest implementowany przez **RadioButtonWrapper** składnika. Pobiera wystąpienie tego składnika przy użyciu **GetControlWrapper** funkcji Pomocnik z typem **CONTROL_RADIO_BUTTON**.  

##### <a name="void-setgroupint-firstid-int-lastid"></a>void SetGroup (int firstId, int lastId)  
 Podaj otoka z zakresem przycisków radiowych, które powinny być traktowane jako grupa. Tę metodę należy wywołać przed wywołaniem **CheckRadio**.  

##### <a name="void-checkradioint-id"></a>void CheckRadio(int id)  
 Ustaw przycisk radiowy określonych jako pojedynczy przycisk w grupie przycisków radiowych wybrane. Wywołanie **SetGroup** przed wywołaniem tej metody.  

##### <a name="bool-isbuttoncheckedint-id"></a>Wartość logiczna IsButtonChecked(int id)  
 Ta metoda zwraca wartość PRAWDA, jeśli zaznaczona jest opcja obecnie, wartość FALSE w przeciwnym razie wartość.  

##### <a name="void-enableradioint-id-bool-enable"></a>void EnableRadio (identyfikator int, Włącz wartość logiczna)  
 Ta metoda włącza lub wyłącza przycisk radiowy.  

#### <a name="istatictext-interface"></a>Interfejs IStaticText  

```  
__interface IStaticText : IControl  
{  
    HRESULT SetText([in] LPCTSTR pText);  
    HRESULT GetText([out, retval] LPBSTR pText);  
};  
```  

##### <a name="overview"></a>Omówienie  
 Ten interfejs jest implementowany przez **StaticTextWrapper** składnika. Pobiera wystąpienie tego składnika przy użyciu **GetControlWrapper** funkcji Pomocnik z typem **CONTROL_STATIC_TEXT**.  

##### <a name="hresult-settextin-lpctstr-ptext"></a>HRESULT SetText([in] LPCTSTR pText)  
 Ustawianie tekstu formantu.  

##### <a name="hresult-gettextout-retval-lpbstr-ptext"></a>HRESULT GetText([out, retval] LPBSTR pText)  
 Ta metoda zwraca wartość bieżącą tekstu formantu.  

####  <a name="ITaskinterface"></a> Interfejsu ITask  

```  
__interface IControl : IUnknown  
{  
    HRESULT Init(IStringProperties *pProperties, ISettingsProperties *pTaskSettings);  
    HRESULT Execute(LPDWORD pReturnCode);  
};  
```  

 Implementuje ten interfejs składnika mają być dostępne jako zadania na stronie wstępnej lub jeśli chcesz użyć **BackgroundTask** składnik do wykonywania pracy na wątku w tle.  

 Poniżej przedstawiono składniki, które implementują **ITask** interfejsu:  

-   ID_ShellExecuteTask, L"Microsoft.Wizard.ShellExecuteTask"  

-   ID_CopyFilesTask, L"Microsoft.Wizard.CopyFilesTask"  

-   ID_ACPowerTask, L"Microsoft.OSDRefresh.ACPowerTask"  

-   ID_WiredNetworkTask, L"Microsoft.SharedPages.WiredNetworkTask"  

##### <a name="init"></a>init  

```  
HRESULT Init(IStringProperties *pProperties, ISettingsProperties *pTaskSettings)  
```  

 Jeśli piszesz zadania wstępnego strony wywołać tę metodę można zainicjować zadania. Plik .config zawiera kod XML, który może wyglądać mniej więcej tak:  

```  
<Task DisplayName="Check Windows Scripting Host" Type="Microsoft.Wizard.ShellExecuteTask">  
  <Setter Property="filename">%windir%\system32\cscript.exe</Setter>  
  <Setter Property="parameters">Preflight\OSDCheckWSH.vbs</Setter>  
  <Setter Property="BitmapFilename">images\WinScriptHost.bmp</Setter>  
  <ExitCodes>  
    <ExitCode State="Success" Type="0" Value="0" Text="" />  
    <ExitCode State="Error" Type="-1" Value="*" Text="Windows Scripting Host not installed." />  
  </ExitCodes>  
</Task>  
```  

 **PProperties** parametru zapewnia dostęp do wartości trzy metody ustawiającej, podczas gdy **pTaskSettings** parametru zapewnia dostęp do **zadań** element i elementy podrzędne. Większość zadań wymagane jest tylko do odczytu danych z **pProperties** parametru.  

#####  <a name="Execute"></a> Wykonanie  

```  
HRESULT Execute(LPDWORD pReturnCode)  
```  

 Oto, gdzie pisania kodu, który wykonuje zadanie. Ta metoda powinna zwrócić **S_OK** Jeśli nie było żadnych błędów i może on zwrócić inny **HRESULT** Jeśli wystąpił błąd, gdy zadanie było uruchomione. Wartości inne niż **S_OK** ta metoda zwraca są dopasowywane do < błąd\> elementów < ExitCodes\> sekcji, jeśli używasz wstępnej strony.  

 **PReturnCode** parametru muszą zostać zaktualizowane liczbą raportowanie stanu zadania. Te wartości są dopasowywane przez stronę preflights do < ExitCode\> elementów.  

#### <a name="itreeview-interface"></a>Interfejs ITreeView  

```  
__interface ITreeView : IControl  
{  
    void EnableCheckboxes(void);  
    HRESULT CreateImageList(int width, int height, UINT flags);  
    int AddImage(HINSTANCE hInstance, int resourceId);  

    HTREEITEM AddItem(LPCTSTR text, HTREEITEM hParent = NULL);  
    void SetImage(HTREEITEM item, int image, int expandImage);  

    void Clear(void);  
    BOOL SetFirstVisible(HTREEITEM item);  
    BOOL SelectItem(HTREEITEM item);  
    void CheckItem(HTREEITEM item, UINT checkState);  
    HTREEITEM SelectedItem(void);  
    int SetItemHeight(SHORT height);  
    HRESULT EnableItem(HTREEITEM item, BOOL enable);  
    void Expand(HTREEITEM hItem, BOOL expand);  

    HTREEITEM GetChild(HTREEITEM hParent);  
    HTREEITEM GetParent(HTREEITEM hNode);  
    HTREEITEM GetNextItem(HTREEITEM hPrevious);  

    UINT IsChecked(HTREEITEM item);  
    BOOL IsEnabled(HTREEITEM item);  

    INT_PTR CommonControlEvent(WORD controlId, void* pInfo, BOOL *pCancel);  
    HRESULT SetEventHandler(ITreeViewEvent *pEventHandler);  

    void SetSelectedBackColor(COLORREF color);  
};  
```  

##### <a name="overview"></a>Omówienie  
 Ten interfejs jest implementowany przez **TreeViewWrapper** składnika. Pobiera wystąpienie tego składnika przy użyciu **GetControlWrapper** funkcji Pomocnik z typem **CONTROL_TREE_VIEW**.  

##### <a name="void-enablecheckboxesvoid"></a>void EnableCheckboxes(void)  
 Ta metoda powoduje włączenie pola wyboru w widoku drzewa, ustawiając **TVS_CHECKBOXES** stylu.  

##### <a name="hresult-createimagelistint-width-int-height-uint-flags"></a>HRESULT CreateImageList(int width, int height, UINT flags)  
 Dodaj nowe listy obrazów z formantem widoku drzewa. **Flagi** parametr jest przekazywany w wywołaniu **ImageList_Create** funkcji Win32.  

##### <a name="int-addimagehinstance-hinstance-int-resourceid"></a>int AddImage (wystąpienie wystąpienie HINSTANCE hInstance, int resourceId)  
 Dodawanie obrazu do listy obrazów z zasobu (**resourceId**) w module z dojście wystąpienia **wystąpienie hInstance**.  

##### <a name="htreeitem-additemlpctstr-text-htreeitem-hparent--null"></a>HTREEITEM AddItem(LPCTSTR text, HTREEITEM hParent = NULL)  
 Dodaj węzeł do widoku drzewa. Jeśli nowy węzeł zostanie dodany na najwyższym poziomie **hParent** ma wartość NULL. W przeciwnym razie Podaj dojścia do nadrzędnego elementu miejscu nowy element dodany. Ta metoda zwraca dojście do nowego elementu.  

##### <a name="void-setimagehtreeitem-item-int-image-int-expandimage"></a>SetImage void (elementu HTREEITEM, obrazu int, int expandImage)  
 Ustaw obrazu do użycia dla elementu widoku drzewa. Można ustawić zarówno normalnych, jak i rozszerzonej obrazu.  

##### <a name="void-clearvoid"></a>void Clear(void)  
 Usuń wszystkie elementy z widoku drzewa.  

##### <a name="bool-setfirstvisiblehtreeitem-item"></a>Wartość logiczna SetFirstVisible(HTREEITEM item)  
 Upewnij się, że będzie widoczna pozycja widoku drzewa. Widok drzewa przewinie, jeśli jest to wymagane, aby wyświetlić ten element.  

##### <a name="bool-selectitemhtreeitem-item"></a>Wartość logiczna SelectItem(HTREEITEM item)  
 Ustaw zaznaczony element do elementu, który podasz. Możesz wywołać **SetFirstVisible** po to, aby upewnić się, że nowo wybrany element jest widoczny.  

##### <a name="void-checkitemhtreeitem-item-uint-checkstate"></a>void CheckItem (element HTREEITEM, UINT checkState)  
 Metoda zasadniczo Ustawia obraz, który ma być wyświetlany dla pola wyboru w widoku drzewa. Te obrazy są w oddzielnej **ImageList** formant, który zarządza widoku drzewa. Domyślnie ta lista obraz ma trzy obrazy w nim wyświetlane w tabeli 22.  

### <a name="table-22void-checkitem-image-list-default"></a>Ustawienia domyślne listy obrazów CheckItem void 22. tabeli  

|**CheckState**|**Opis**|  
|-|-|  
|**0**|Puste|  
|**1**|Wyczyszczone|  
|**2**|Wybrane|  

##### <a name="htreeitem-selecteditemvoid"></a>HTREEITEM SelectedItem(void)  
 Ta metoda zwraca dojście widok drzewa, w obecnie wybranego elementu.  

##### <a name="int-setitemheightshort-height"></a>int SetItemHeight (krótka wysokość)  
 Ta metoda określa wysokość wszystkich elementów w kontrolce widok drzewa w pikselach. Zwraca poprzedniej wysokość w pikselach.  

##### <a name="hresult-enableitemhtreeitem-item-bool-enable"></a>HRESULT EnableItem(HTREEITEM item, BOOL enable)  
 Ta metoda włącza lub wyłącza pojedynczego elementu w drzewie. Wyłączenie z elementami podrzędnymi elementu nie spowoduje wyłączenie elementów podrzędnych.  

##### <a name="void-expandhtreeitem-hitem-bool-expand"></a>Rozwiń void (HTREEITEM hItem, rozwiń wartość logiczna)  
 Ta metoda rozwija lub zwija węzeł w drzewie.  

##### <a name="htreeitem-getchildhtreeitem-hparent"></a>HTREEITEM GetChild(HTREEITEM hParent)  
 Ta metoda zwraca pierwszy element podrzędny elementu w widoku drzewa lub wartość NULL, jeśli istnieją bez żadnych elementów podrzędnych.  

##### <a name="htreeitem-getparenthtreeitem-hnode"></a>HTREEITEM GetParent(HTREEITEM hNode)  
 Ta metoda zwraca uchwyt elementu nadrzędnego węzła w widoku drzewa lub wartość NULL, jeśli węzeł jest na najwyższym poziomie.  

##### <a name="htreeitem-getnextitemhtreeitem-hprevious"></a>HTREEITEM GetNextItem(HTREEITEM hPrevious)  
 Można wywołać tej metody za pomocą dojścia **GetChild** zwraca do iteracji wszystkich elementów podrzędnych węzła. Ta metoda zwraca następny element równorzędny w drzewie, które współużytkują ten sam element nadrzędny.  

##### <a name="uint-ischeckedhtreeitem-item"></a>UINT IsChecked(HTREEITEM item)  
 Ta metoda zwraca **0** Jeśli węzeł drzewa widoku nie jest zaznaczone i **1** przypadku.  

##### <a name="bool-isenabledhtreeitem-item"></a>Wartość logiczna IsEnabled(HTREEITEM item)  
 Ta metoda zwraca wartość PRAWDA, jeśli węzeł drzewa widoku jest włączony, FALSE w przeciwnym razie wartość.  

##### <a name="intptr-commoncontroleventword-controlid-void-pinfo-bool-pcancel"></a>INT_PTR CommonControlEvent(WORD controlId, void* pInfo, BOOL \*pCancel)  
 Ta metoda jest tylko do użytku wewnętrznego.  

##### <a name="hresult-seteventhandleritreeviewevent-peventhandler"></a>HRESULT SetEventHandler(ITreeViewEvent \*pEventHandler)  
 Tę metodę można wywołać, jeśli chcesz otrzymywać powiadomienia, gdy zmiany wybranego elementu lub użytkownik zmieni stan wyboru elementu widoku drzewa. Musisz zaimplementować **ITreeViewEvent** w składniku do odbierania tych wywołań zwrotnych.  

##### <a name="void-setselectedbackcolorcolorref-color"></a>void SetSelectedBackColor(COLORREF color)  
 Kolor tła używany dla wybranego elementu.  

#### <a name="iwmiiteration-interface"></a>Interfejs IWmiIteration  

```  
__interface IWmiIterator : IUnknown  
{  
    HRESULT Next(void);  
    HRESULT GetProperty(LPCTSTR propertyName, [out] LPVARIANT pValue);  
};  
```  

##### <a name="overview"></a>Omówienie  
 Ten interfejs używane zwykle wraz z **IWmiRepository**, podczas pracy z wywołań usługi WMI. **IWmiIteration** interfejs umożliwia iterację wartości zwracanych przez zapytanie.  

##### <a name="hresult-nextvoid"></a>HRESULT Next(void)  
 Przenieś do następnego elementu w wynikach zapytania, jak pokazano w tabeli 23.  

### <a name="table-23-hresult-nextvoid-query-returns"></a>Tabela 23. Zwraca zapytanie Next(void) HRESULT  

|**HRRESULT**|**Opis**|  
|-|-|  
|**S_OK**|Przenoszone do następnego wyniku; można użyć **GetProperty** można pobrać właściwości tego wyniku.|  
|**S_FALSE**|Brak więcej elementów na liście.|  
|**E_NOT_SET**|Nie są wyniki zapytania|  

##### <a name="hresult-getpropertylpctstr-propertyname-out-lpvariant-pvalue"></a>HRESULT GetProperty(LPCTSTR propertyName, [out] LPVARIANT pValue)  
 Ta metoda pobiera wartość właściwości z bieżącego rekordu wyniku, jak pokazano w tabeli 24 i tabela 25.  

### <a name="table-24-hresult-getproperty"></a>Tabela 24. HRESULT GetProperty  

|**Parametr**|**Opis**|  
|-|-|  
|**propertyName**|Nazwa właściwości, który chcesz pobrać|  
|**pValue**|Wskazuje strukturę VARIANT, który przy powrocie zawiera wartość właściwości|  

### <a name="table-25-hresult-getproperty-result"></a>Tabela 25. Wynik GetProperty HRESULT  

|**HRESULT**|**Opis**|  
|-|-|  
|**S_OK**|Wartość właściwości została pobrana.|  
|**WBEM_E_NOT_FOUND**|Nie ma właściwości o tej nazwie.|  
|**E_NOT_VALID_STATE**|Brak bieżącego rekordu.|  

> [!NOTE]
>  **GetProperty** metoda może zwracać innych kodów błędów WMI wymienionych w tabeli 25. Wartości wyświetlane są ogólne wyniki, które są zwracane.  

#### <a name="iwmirepository-interface"></a>Interfejs IWmiRepository  

```  
__interface IWmiRepository : IUnknown  
{  
    HRESULT SetNamespace(LPCWSTR namespaceName);  
    HRESULT ExecQuery(LPCWSTR query, [out] IWmiIterator **ppIterator);  
};  
```  

##### <a name="overview"></a>Omówienie  
 Ten interfejs jest implementowany przez **WmiRepository** składnika (**ID_WmiRepository**).  

##### <a name="hresult-setnamespacelpcwstr-namespacename"></a>HRESULT SetNamespace(LPCWSTR namespaceName)  
 Ta metoda ustawia obszar nazw usługi WMI, który będzie używany dla zapytania. Tę metodę należy wywołać przed wywołaniem **metoda ExecQuery**. Jeśli nie wywołuj tej metody, przestrzeń nazw jest root\cimv2. Ta metoda zawsze zwraca **S_OK**.  

##### <a name="hresult-execquerylpcwstr-query-out-iwmiiterator-ppiterator"></a>HRESULT ExecQuery(LPCWSTR query, [out] IWmiIterator **ppIterator)  
 Wykonywanie zapytań względem przestrzeni nazw usługi WMI ustawiony za pomocą wywołania **SetNamespace**, jak pokazano w tabeli 26 i 27 tabeli.  

### <a name="table-26-hresult-execquery"></a>26 tabeli. Metoda ExecQuery HRESULT  

|**Parametr**|**Opis**|  
|-|-|  
|**Query**|Ciąg zapytania usługi WMI, którą chcesz wykonać|  
|**ppIterator**|Przekazać wskaźnika do wskaźnika interfejsu, który przy powrocie zostanie wprowadzona interfejs, zapewniając dostęp do wyników zapytania|  

### <a name="table-27-hresult-query-result"></a>27 tabeli. Wynik kwerendy HRESULT  

|**HRESULT**|**Opis**|  
|-|-|  
|**S_OK**|Zapytanie powiodło się.|  
|**Inne**|Jeśli zapytanie nie powiodła się, zwraca WMI **HRESULT**|  

#### <a name="iformcontroller-interface"></a>Interfejs IFormController  

```  
__interface IFormController : IUnknown  
{  
    Init(IWizardPageView *pView, IWizardPageContainer *pContainer);  
    SetPageInfo(ISettingsProperties *pPageInfo);  

    Validate(void);  

    AddToGroup(int groupControlId, int controlId);  
    UpdateCheckGroup(int groupControlId);  
    AddValidator(int controlId, IValidator *pValidator, IControl *pCOntrol = 0);  

    AddValidator(int controlId, LPCWSTR validatorId, LPCWSTR message, IValidator **ppValidator = nullptr);  
    DisableValidation(int controlId, BOOL disable);  

    AddField(LPCWSTR fieldName, int controlId, BOOL suppressLog, DialogControlTypes type);  
    AddRadioGroup(LPCWSTR groupName, int radioControlId);  
    EnableRadioGroup(LPCWSTR groupName, BOOL enable);  
    InitFields(IFieldCallback *pFieldCallback = nullptr);  
    SaveFields(IFieldCallback *pFieldCallback = nullptr);  
    BOOL IsFieldDisabled(int controlId);  

    InitSection(LPCWSTR key, LPCWSTR sectionCaption);  
    AddSummaryItem(LPCWSTR first, LPCWSTR second);  
    SuppressLogValue(LPCWSTR tsVariableName);  
    SaveText(int controlId, LPCWSTR tsVariableName, LPCWSTR summaryCaption);  
    LoadText(int controlId, LPCWSTR tsVariableName);  

    void ControlEvent(WORD eventId, WORD controlId);  
    BOOL IsValid(void);  
 };  
```  

##### <a name="overview"></a>Omówienie  
 Każdej stronie kreatora UDI ma swój własny kontroler formularz, który implementuje ten interfejs. Ten kontroler umożliwia połączenie danych pola w pliku .config XML do formantów na stronie. Formularz kontroler obsługuje wiele informacji dla Ciebie.  

#####  <a name="SettingUptheForm"></a> Konfigurowanie formularza  
 Ogólnie rzecz biorąc, skonfigurować kontroler formularz na stronie **OnWindowCreated** metody. Dlatego zazwyczaj ten obejmuje wywoływania metod wyświetlany w tabeli 28.  

### <a name="table-28-onwindowcreated-method"></a>28 tabeli. OnWindowCreated — metoda  

|**— Metoda**|**Opis**|  
|-|-|  
|**Init**|Inicjuje kontrolera formularza|  
|**AddField**|Zapewnia połączenie między polem w pliku XML .config, który jest nazwą ciągu i kontroli w okno dialogowe ze strony, który jest Identyfikatorem|  
|**AddRadioGroup**|Używane do łączenia z przycisku radiowego do grupy i kontroli w oknie dialogowym|  
|**AddToGroup**|Pozwala formantów "podrzędnych", które są włączone lub wyłączone wraz z ich nadrzędnym lub oparte na które przycisk radiowy zostanie wybrany|  
|**InitFields**|Wywołania po wywołaniu wszystkich **Dodaj** metody do ustawiania formularza|  
|**Sprawdzanie poprawności**|Sprawdza poprawność początkowej|  

##### <a name="processing-form-events"></a>Przetwarzanie zdarzeń formularza  
 Dodaj następujące wywołanie do Twojej **OnControlEvent** metody:  

```  
Form()->ControlEvent(eventId, controlId);  
```  

 To wywołanie przekazuje zdarzenia się na kontrolerze formularza, aby przetworzyć zdarzenia związane z formularza.  

##### <a name="save-form-data"></a>Zapisz dane formularza  
 W **OnNextClicked** metody, wywoływanie metod formularza wyświetlany w tabeli 29.  

### <a name="table-29-onnextclicked-method"></a>29 tabeli. OnNextClicked — metoda  

|**— Metoda**|**Opis**|  
|-|-|  
|**InitSection**|Zawiera nazwę sekcji, która będzie wyświetlana na **Podsumowanie** dla tej strony|  
|**SaveFields**|Zapisywanie wartości pól do zmiennych sekwencji zadań oraz na **Podsumowanie** strony|  

#####  <a name="Init"></a> init  

```  
HRESULT Init(IWizardPageView *pView, IWizardPageContainer *pContainer)  
```  

 Ta metoda jest wywoływana zwykle w pobliżu początku ze strony **OnWindowCreated** metody. Polecenie powinno wyglądać mniej więcej tak:  

```  
Form()->Init(View(), Container());  
```  

##### <a name="setpageinfo"></a>SetPageInfo  

```  
HRESULT SetPageInfo(ISettingsProperties *pPageInfo)  
```  

 Ta metoda jest wywoływana wewnętrznie, a użytkownik powinien nie wywołać ją samodzielnie. Zapewnia on strony XML do kontrolera formularza.  

##### <a name="validate"></a>Sprawdzanie poprawności  

```  
HRESULT Validate(void)  
```  

 Ta metoda wykonuje wszystkie moduły weryfikacji związanych z formantami. Jeśli moduł weryfikacji nie zostały spełnione, kontrolera formularza zostanie wyświetlony komunikat ostrzegawczy i wyłącza **dalej** przycisk, a następnie zatrzymuje przetwarzanie modułów weryfikacji. Zazwyczaj konieczne jest ta metoda jest wywoływana po zakończeniu Twojej **OnWindowCreated** ; metoda zawsze zwraca **S_OK**.  

##### <a name="addtogroup"></a>AddToGroup  

```  
AddToGroup(int groupControlId, int controlId)  
```  

 Ta metoda dodaje do formantu "podrzędnym" pola wyboru lub przycisku radiowego, jak pokazano w tabeli 30. Takie formantów podrzędnych zostanie wyłączone, gdy formant nadrzędny nie jest zaznaczona. Metoda zawsze zwraca **S_OK**.  

### <a name="table-30-addtogroup"></a>30 tabeli. AddToGroup  

|**Parametr**|**Opis**|  
|-|-|  
|**groupControlId**|Identyfikator pola wyboru lub przycisku radiowego, który będzie kontrolować stan aktywny formant podrzędny|  
|**Controlld**|Identyfikator formantu, który chcesz dodać jako element podrzędny|  

##### <a name="updatecheckgroup"></a>UpdateCheckGroup  

```  
HRESULT UpdateCheckGroup(int groupControlId)  
```  

 Ta metoda aktualizacji Włącz lub Wyłącz stan formantów podrzędnych grupy na podstawie stanu formantu nadrzędnego. Ogólnie rzecz biorąc nie trzeba wywołać tę metodę, samodzielnie, ponieważ kontroler formularza wywołuje go dla Ciebie.  

##### <a name="addvalidator"></a>AddValidator  

```  
HRESULT AddValidator(int controlId, IValidator *pValidator, IControl *pControl = 0)  
```  

 Tę metodę można wywołać tylko wtedy, gdy moduł sprawdzania poprawności, który ma zostać utworzony w kodzie zamiast z pliku XML. Ta metoda zawsze zwraca **S_OK**.  

##### <a name="addvalidator"></a>AddValidator  

```  
HRESULT AddValidator(int controlId, LPCWSTR validatorId, LPCWSTR message, IValidator **ppValidator = nullptr)  
```  

 Tę metodę można wywołać tylko wtedy, gdy moduł sprawdzania poprawności, który ma zostać utworzony w kodzie zamiast z pliku XML.  

##### <a name="disablevalidation"></a>DisableValidation  

```  
HRESULT DisableValidation(int controlId, BOOL disable)  
```  

 Wywołać tę metodę, aby jawnie Wyłącz moduł weryfikacji dla formantu lub przywrócić normalne sprawdzanie poprawności, jak pokazano w tabeli 31. Ta metoda jest przydatna, na przykład gdy Włączanie/wyłączanie reguły dla formantów, które nie są obsługiwane z weryfikacji formularza należy wyłączyć sprawdzanie poprawności dla formantu. Innymi słowy, czy nie zwykle ta metoda jest wywoływana. Ta metoda zawsze zwraca **S_OK**.  

### <a name="table-31-hresult-disablevalidation"></a>Tabela 31. HRESULT DisableValidation  

|**Parametr**|**Opis**|  
|-|-|  
|**właściwości controlId**|Formant, dla którego chcesz włączyć lub wyłączyć weryfikację|  
|**Wyłącz**|Ustawione na wartość TRUE powoduje wyłączenie sprawdzania poprawności i wartość false, aby przywrócić normalne sprawdzanie poprawności|  

#####  <a name="AddField"></a> AddField  

```  
HRESULT AddField(LPCWSTR fieldName, int controlId, BOOL suppressLog, DialogControlTypes type)  
```  

 Dodaj formant mapowanie nazwy w **pola** element .config pliku XML i identyfikator formantu w ze strony — okno dialogowe, jak pokazano w tabeli 32. Należy wywołać tę metodę przed wywołaniem do **InitFields**, ponieważ **InitFields** używa tych informacji. Ta metoda zawsze zwraca **S_OK**.  

### <a name="table-32-hresult-addfield"></a>Tabela 32. HRESULT AddField  

|**Parametr**|**Opis**|  
|-|-|  
|**Nazwa pola**|Nazwa pola w XML ze strony|  
|**właściwości controlId**|Identyfikator formantu w szablonie — okno dialogowe ze strony|  
|**suppressLog**|Wartość TRUE, jeśli nie ma wartości z tego pola zapisywane w pliku dziennika; Ten parametr zawsze ustawiony na wartość TRUE dla hasła lub numeru PIN pól|  
|**Typ**|Typ formantu, który jest jednym z następujących czynności:<br /><br /> -   **CONTROL_STATIC_TEXT**<br />-   **CONTROL_COMBO_BOX**<br />-   **CONTROL_LIST_VIEW**<br />-   **CONTROL_PROGRESS_BAR**<br />-   **CONTROL_GENERIC**<br />-   **CONTROL_RADIO_BUTTON**<br />-   **CONTROL_CHECK_BOX**<br />-   **CONTROL_TREE_VIEW**|  

#####  <a name="AddRadioGroup"></a> AddRadioGroup  

```  
HRESULT AddRadioGroup(LPCWSTR groupName, int radioControlId)  
```  

 Ta metoda dodaje formant do nazwanego Grupa przycisków radiowych, jak pokazano w tabeli 33. Należy wywołać to przed **InitFields** metody, ponieważ ta metoda używa atrybutów na **RadioGroup** element, aby kontrolować ustawienia dla wszystkich kontrolek przycisku radiowego w grupie. Grup przycisków opcji można zablokować, na przykład, tak aby przycisków radiowych są wyłączone, ale formantów podrzędnych są włączone lub wyłączone w oparciu jedynie przycisku radiowego, która jest zaznaczona. Ta metoda zawsze zwraca **S_OK**.  

### <a name="table-33-hresult-addradiogroup"></a>Tabela 33. HRESULT AddRadioGroup  

|**Parametr**|**Opis**|  
|-|-|  
|**groupName**|Ciąg, który definiuje grupę przycisków opcji na tej stronie|  
|**radioControlId**|Identyfikator przycisku radiowego jednego do dodania do tej grupy|  

##### <a name="enableradiogroup"></a>EnableRadioGroup  

```  
HRESULT EnableRadioGroup(LPCWSTR groupName, BOOL enable)  
```  

 Ta metoda umożliwia włączanie lub wyłączanie Grupa przycisków radiowych całego. Wyłączanie grupa opcji powoduje wyłączenie wszystkich przycisk radiowy formantów w grupie oraz wszelkie elementy podrzędne tych przycisków radiowych, które zostały dodane z **AddToGroup**. Zobacz tabelę 34 i 35 tabeli.  

### <a name="table-34-enableradiogroup"></a>34 tabeli. EnableRadioGroup  

|**Parametr**|**Opis**|  
|-|-|  
|**groupName**|Nazwa Grupa przycisków radiowych, już zdefiniowany w wyniku wywołania **AddRadioGroup**|  
|**Włączenie**|Wartość TRUE włącza Grupa przycisków radiowych i FALSE wyłączyć grupy|  

### <a name="table-35-hresult-enableradiogroup"></a>35 tabeli. HRESULT EnableRadioGroup  

|**HRESULT**|**Opis**|  
|-|-|  
|**S_OK**|Grupy włączone lub wyłączone|  
|**E_INVALIDARG**|Brak nie grupa przycisków radiowych o nazwie podane|  

#####  <a name="InitFields"></a> InitFields  

```  
HRESULT InitFields(IFieldCallback *pFieldCallback = nullptr)  
```  

 Przed wywołaniem tej metody, należy wywołać **AddField** dla każdego pola, które można kontrolować kod XML. Ta metoda zawsze zwraca **S_OK**.  

 **PFieldCallback** parametr jest opcjonalny. Jeśli zostaną podane, wywołuje metodę kontrolera formularza **SetFieldDefault** dla formantów, które nie są albo **CONTROL_STATIC_TEXT** lub **CONTROL_CHECK_BOX**. To zachowanie umożliwia pobieranie wartości domyślnej z pliku XML i ustaw go w formancie użytkownika.  

#####  <a name="SaveFields"></a> SaveFields  

```  
HRESULT SaveFields(IFieldCallback *pFieldCallback = nullptr)  
```  

 Taka metoda ogranicza wartości pól do zmiennych sekwencji zadań i danych podsumowania, który ma być wyświetlany na **podsumowania** strony. Udostępnia wskaźnik w **pFieldCallback** umożliwia obsługę zapisywanie wartości dla formantów, które nie obsługują **CONTROL_STATIC_TEXT**.  

##### <a name="isfielddisabled"></a>IsFieldDisabled  

```  
BOOL IsFieldDisabled(int controlId)  
```  

 Ta metoda pozwala określić, czy pole zostało wyłączone w pliku XML.  

#####  <a name="InitSection"></a> InitSection  

```  
HRESULT InitSection(LPCWSTR key, LPCWSTR sectionCaption)  
```  

 Ta metoda inicjuje dane podsumowania, który ma być wyświetlany na **podsumowania** strony, jak pokazano w tabeli 36. Wywołanie tej metody Twojej **OnNextClicked** metoda przed wywołaniem **SaveFields**. Ta metoda zawsze zwraca **S_OK**.  

### <a name="table-36-hresult-initsection"></a>36 tabeli. HRESULT InitSection  

|**Parametr**|**Opis**|  
|-|-|  
|**Key**|Ten parametr powinien być unikatowy do strony. Służy do zapewnienia, że każdej strony ma własną podsumowanie informacji.|  
|**sectionCaption**|Nagłówek, który ma być wyświetlana w **podsumowania** strony dla tej strony Podsumowanie informacji. Zazwyczaj **DisplayName()** jako wartość tego parametru.|  

##### <a name="addsummaryitem"></a>AddSummaryItem  

```  
HRESULT AddSummaryItem(LPCWSTR first, LPCWSTR second)  
```  

 Ta metoda umożliwia dodanie podsumowania elementów do **podsumowania** strony niż te elementy zestaw z pliku XML. Zobacz 37 tabeli.  

### <a name="table-37-hresult-addsummaryitem"></a>37 tabeli. HRESULT AddSummaryItem  

|**Parametr**|**Opis**|  
|-|-|  
|**pierwszy**|Podpis elementu podsumowania jest wyświetlany po lewej stronie|  
|**Drugie**|Wartość, która będzie wyświetlana po prawej stronie|  

##### <a name="suppresslogvalue"></a>SuppressLogValue  

```  
HRESULT SuppressLogValue(LPCWSTR tsVariableName)  
```  

 Tę metodę należy wywoływać dla zmiennych sekwencji zadań, dla których nie ma wartości, które mają być zapisywane w pliku dziennika. Wywołanie tej metody dla zadań zmienne sekwencji, których są przechowywane hasła, PIN lub inne poufne wartości, które użytkownik może wprowadzić.  

##### <a name="savetext"></a>SaveText  

```  
HRESULT SaveText(int controlId, LPCWSTR tsVariableName, LPCWSTR summaryCaption)  
```  

 Ta metoda zapisuje wartość kontrolki tekstu do zmiennej sekwencji zadań i sekcja podsumowania. Zazwyczaj nie należy wywołać tę metodę, samodzielnie, ponieważ kontrolera formularza robi to dla wszystkich pól. Zobacz tabeli 38.  

### <a name="table-38-hresult-savetext"></a>Tabela 38. HRESULT SaveText  

|**Parametr**|**Opis**|  
|-|-|  
|**właściwości controlId**|Identyfikator pola tekstowego, który zawiera wartość, którą chcesz zapisać (lub inny formant, która może zwrócić tekst)|  
|**tsVariableName**|Nazwa zmiennej sekwencji zadań, który chcesz zmodyfikować|  
|**summaryCaption**|Podpis na **Podsumowanie** strony dla tej wartości|  

##### <a name="loadtext"></a>LoadText  

```  
HRESULT LoadText(int controlId, LPCWSTR tsVariableName)  
```  

 Ta metoda odczytuje wartość zmiennej sekwencji zadań i ustawia pole tekstowe tej wartości.  

##### <a name="controlevent"></a>Controlevent zdarzenie  

```  
void ControlEvent(WORD eventId, WORD controlId)  
```  

 Wywołanie tej metody na Twojej **OnControlEvent** metody, aby upewnić się, że kontroler formularza może przetwarzać zdarzeń kontrolowania, które należy wykonać, aby działać poprawnie. Wartości są przekazywane do tej metody są takie same wartości przekazanych do **OnControlEvent** metody.  

##### <a name="isvalid"></a>IsValid  

```  
BOOL IsValid(void)  
```  

 Ta metoda zwraca stan ostatniej weryfikacji formularza. Jeśli moduły weryfikacji kontroli raportowane błąd, ta metoda zwraca wartość FALSE. Innymi słowy zwraca wartość TRUE tylko wtedy, gdy wszystkie kontrolki na stronie są prawidłowe.  

#### <a name="ivalidator-interface"></a>IValidator — interfejs  

```  
__interface IValidator : IUnknown  
{  
    HRESULT Init(IControl *pControl, LPCTSTR message);  
    HRESULT Init(IControl *pControl, IWizardPageContainer *pContainer, IStringProperties *pProperties);  
    BOOL, IsValid(LPBSTR pMessage);  
    HRESULT SetProperty(int propertyId, LPVARIANT pValue);  
    HRESULT SetProperty(int propertyId, IUnknown *pUnknown);  
    HRESULT SetProperty)(int propertyId, LPCTSTR pValue);  
};  
```  

##### <a name="overview"></a>Omówienie  
 *Moduły weryfikacji* są składnikami, które można zweryfikować jednego formantu na stronie. Najprostszym sposobem, aby zaimplementować moduł weryfikacji jest stał się podklasą **BaseValidator** klasy, która jest zdefiniowana w pliku nagłówka BaseValidator.h.  

##### <a name="hresult-initicontrol-pcontrol-lpctstr-message"></a>HRESULT Init(IControl \*pControl, LPCTSTR message)  
 Jeśli tworzysz moduł weryfikacji w kodzie można wywołać tej metody można zainicjować modułu sprawdzania poprawności. Zobacz 39 tabeli.  

### <a name="table-39-hresult-init"></a>39 tabeli. HRESULT Init  

|**Parametr**|**Opis**|  
|-|-|  
|**pControl**|Formant, który zweryfikować Twojego modułu sprawdzania poprawności|  
|**Komunikat**|Komunikat wyświetlany na stronie, jeśli formant jest nieprawidłowy|  

##### <a name="hresult-initicontrol-pcontrol-iwizardpagecontainer-pcontainer-istringproperties-pproperties"></a>HRESULT Init(IControl \*pControl, IWizardPageContainer \*pContainer, IStringProperties \*pProperties)  
 Kontroler formularza wywołuje tę metodę, aby zainicjować modułów weryfikacji, które tworzy oparte na języku XML strony. Zobacz 40 tabeli.  

### <a name="table-40-hresult-init-method"></a>Table 40. HRESULT Init — metoda  

|**Parametr**|**Opis**|  
|-|-|  
|**pControl**|Formant, który zweryfikować Twojego modułu sprawdzania poprawności|  
|**pContainer**|W przypadku Twojego modułu sprawdzania poprawności musi mieć dostęp do rejestratora lub musi utworzyć innych składników|  
|**pProperties**|Umożliwia dostęp do właściwości (elementy setter) dla użytkownika modułu sprawdzania poprawności|  

##### <a name="bool-isvalidlpbstr-pmessage"></a>Wartość logiczna, IsValid (LPBSTR pMessage)  
 Ta metoda zwraca wartość PRAWDA, jeśli formant jest nieprawidłowy, lub FAŁSZ, jeśli formant jest nieprawidłowy. Przy powrocie **pMessage** powinno być wypełnione nowy **BSTR** zawierający komunikat wyświetlany, gdy formant jest nieprawidłowy.  

##### <a name="hresult-setpropertyint-propertyid-lpvariant-pvalue"></a>HRESULT SetProperty(int propertyId, LPVARIANT pValue)  
 Można zaimplementować tę metodę, aby uzyskać dodatkowe wartości, które nie znajdują się w pliku XML.  

##### <a name="hresult-setpropertyint-propertyid-iunknown-punknown"></a>HRESULT SetProperty(int propertyId, IUnknown \*pUnknown)  
 Można zaimplementować tę metodę, aby uzyskać dodatkowe wartości, które nie znajdują się w pliku XML.  

##### <a name="hresult-setpropertyint-propertyid-lpctstr-pvalue"></a>HRESULT SetProperty) (int propertyId LPCTSTR pValue)  
 Można zaimplementować tę metodę, aby uzyskać dodatkowe wartości, które nie znajdują się w pliku XML.  

#### <a name="iregex-interface"></a>Interfejs IRegEx  

```  
__interface IRegEx : IUnknown  
{  
    BOOL MatchesRegex(LPCTSTR input, LPCTSTR regex);  
    HRESULT GetMatch(size_t index, LPBSTR pValue);  
};  
```  

 Ta metoda jest implementowany przez **ID_Regex** składnika (IRegex.h) i zapewnia obsługę przetwarzania wyrażenia regularnego.  

##### <a name="bool-matchesregexlpctstr-input-lpctstr-regex"></a>Wartość logiczna MatchesRegex(LPCTSTR input, LPCTSTR regex)  
 Ta metoda jest uruchamiana wyrażenia regularnego względem tekstu wejściowego. Ta biblioteka standard C++ **regex_match —** funkcji wykonują rzeczywistą pracę. Metoda zwraca wartość PRAWDA, jeśli było zgodne, FALSE w przeciwnym razie.  

##### <a name="hresult-getmatchsizet-index-lpbstr-pvalue"></a>HRESULT GetMatch(size_t index, LPBSTR pValue)  
 Ta metoda umożliwia pobieranie dopasowań z ostatniego **MatchesRegex** wywołania. Pamiętaj, że nie było błędu przetwarzania w tej metodzie i albo zwraca **S_OK** lub zgłasza wyjątek.  

#### <a name="isummaryinfo-interface"></a>Interfejs ISummaryInfo  

```  
__interface ISummaryInfo : IUnknown  
{  
    size_t Count(void);  
    HRESULT Clear(void);  
    HRESULT AddInfo(LPCTSTR pFirst, LPCTSTR pSecond);  
    HRESULT GetInfo(size_t index, LPBSTR pFirst, LPBSTR pSecond);  
    HRESULT GetCaption(LPBSTR pCaption);  
    HRESULT SetCaption(LPCTSTR caption);  
};  
```  

 Należy nie trzeba korzystać bezpośrednio tego interfejsu. Zamiast tego należy użyć **IFormController**.  

#### <a name="isummarybag"></a>ISummaryBag  

```  
__interface ISummaryBag : IUnknown  
{  
    size_t Count(void);  
    HRESULT GetInfoByIndex(size_t index, [out] ISummaryInfo **ppSummary);  
    HRESULT GetInfoByKey(LPCTSTR key, [out] ISummaryInfo **ppSummary);  
};  
```  

 Należy nie trzeba korzystać bezpośrednio tego interfejsu. Zamiast tego należy użyć **IFormController**.  

#### <a name="itsvariablebag-interface"></a>Interfejs ITSVariableBag  

```  
__interface ITSVariableBag : IUnknown  
{  
    void GetValue([in] LPCTSTR variableName, [out] LPBSTR pValue);  
    void SetValue([in] LPCTSTR variableName, [in] LPCTSTR pValue);  
    void Clear(void);  
    HRESULT Remove([in] LPCTSTR variableName);  
    HRESULT SuppressLogValue([in] LPCTSTR variableName);  
    void Save(void);  
};  
```  

 Ten interfejs umożliwia dostęp do zmiennych sekwencji zadań. Dostęp można uzyskać ten interfejs, za pomocą strony **TSVariables()** metody.  

##### <a name="void-getvaluein-lpctstr-variablename-out-lpbstr-pvalue"></a>GetValue void ([in] nazwa_zmiennej LPCTSTR LPBSTR pValue [out])  
 Ta metoda odczytuje wartość zmiennej sekwencji zadań.  

> [!NOTE]
>  Wartości są buforowane, po pierwszym odczytu.  

##### <a name="void-setvaluein-lpctstr-variablename-in-lpctstr-pvalue"></a>SetValue void ([in] nazwa_zmiennej LPCTSTR LPCTSTR pValue [in])  
 Ta metoda określa wartość zmiennej sekwencji zadań. Ta wartość jest zapisana w pamięci. Wartości sekwencji zadań są zapisywane po kliknięciu **Zakończ** w Kreatorze UDI.  

##### <a name="void-clearvoid"></a>void Clear(void)  
 Ta metoda usuwa wszystkie wartości sekwencji zadań, które zostały zapisane w pamięci.  

##### <a name="hresult-removein-lpctstr-variablename"></a>HRESULT Remove([in] LPCTSTR variableName)  
 Ta metoda usuwa wartość sekwencji zadania z pamięci. Przy następnym wywołaniu **GetValue** o takiej samej nazwie sekwencji zadań, metoda próbuje pobrać go z sekwencji zadań.  

##### <a name="hresult-suppresslogvaluein-lpctstr-variablename"></a>HRESULT SuppressLogValue([in] LPCTSTR variableName)  
 Zawsze, gdy są zapisywane zmienne sekwencji zadań, takich jak kliknięcie **Zakończ** w Kreatorze UDI nazwy i wartości są zapisywane w pliku dziennika. Wywołaj tę metodę, aby pominąć rejestrowanie poufnych wartości, takie jak hasła lub kody PIN, zmienną sekwencji zadań określone.  

##### <a name="void-savevoid"></a>void Save(void)  
 Taka metoda ogranicza wszystkie wartości sekwencji zadań, które zostały ustawione z wywołaniami **SetValue**.  

#### <a name="itsvariablerepository-interface"></a>Interfejs ITSVariableRepository  

```  
__interface ITSVariableRepository : IUnknown  
{  
    void GetValue([in] LPCTSTR variableName, BOOL logValue, [out] LPBSTR pValue);  
    void SetValue([in] LPCTSTR variableName, BOOL logValue, [in] LPCTSTR value);  
};  
```  

 Ten interfejs jest do użytku wewnętrznego przez **TSVariableBag** do odczytywania i zapisywania zmiennych sekwencji zadań.  

#### <a name="iwizardfinish-interface"></a>Interfejs IWizardFinish  

```  
__interface IWizardFinish : IUnknown  
{  
    HRESULT Canceled(void);  
    HRESULT Finished(void);  
};  
```  

 Ten interfejs jest przydatne w zaawansowanych scenariuszach, w której chcesz wykonać dodatkowego przetwarzania po kliknięciu **Zakończ** lub **anulować** w Kreatorze UDI. Zawiera Kreatora UDI **Zakończ** zadanie, które zapisuje zmienne sekwencji zadań, po kliknięciu **Zakończ**. Jeśli anulujesz Kreatora zadanie określa tylko **OSDSetupWizCancelled** zmiennych sekwencji zmienną sekwencji zadań na wartość TRUE i nie nie zapisać zmiany w innych zadań.  

 Jeśli utworzysz składnika Zakończ należy zarejestrowanie go za pomocą kodu w następujący sposób:  

```  
Register<MyFinishTaskFactory>(ID_MyFinishTask, pRegistry);  

PWizardFinish pFinish;  
CreateInstance(pRegistry, ID_MyFinishTask, &pFinish);  

PWizardFinishService pService;  
GetService<IWizardFinishService>(pRegistry, &pService);  

pService->Register(pFinish);  
```  

#### <a name="ibindablelist-interface"></a>Interfejs IBindableList  

```  
__interface IBindableList : IUnknown  
{  
    size_t Count(void);  
    HRESULT GetCaption(size_t index, LPBSTR pCaption);  
};  
```  

 Implementuje ten interfejs, jeśli składnik źródła danych, które chcesz powiązać pole kombi, wywołując jego **powiązać** metody.  

##### <a name="sizet-countvoid"></a>size_t Count(void)  
 Ta metoda zwraca liczbę elementów na liście.  

##### <a name="hresult-getcaptionsizet-index-lpbstr-pcaption"></a>HRESULT GetCaption(size_t index, LPBSTR pCaption)  
 Ta metoda zwraca podpis elementu pod określonym indeksem.  

#### <a name="idatanodes-interface"></a>Interfejs IDataNodes  

```  
__interface IDataNodes : IUnknown  
{  
    size_t Count();  
    HRESULT SetCaptionProperty(LPCTSTR captionProperty);  
    HRESULT GetProperty(size_t index, LPCTSTR propertyName, [out] LPBSTR propertyValue);  
    HRESULT GetNode(size_t index, [out] ISettingsProperties **ppNode);  
};  
```  

 Ten interfejs umożliwia dostęp do hierarchiczne dane, które mogą być zapisane w stronie. Uzyskać ten interfejs, za pomocą metod na **ISettingsProperties** interfejsu, który jest dostępny na stronie za pośrednictwem **ustawienia** metody.  

 Dane w formacie XML na stronie może wyglądać mniej więcej tak  

```  
      <Data Name="Network">  
        <DataItem>  
          <Setter Property="DisplayName">Public</Setter>  
          <Setter Property="Share">\\servername\Share</Setter>  
        </DataItem>  
        <DataItem>  
          <Setter Property="DisplayName">Dev Team</Setter>  
          <Setter Property="Share">\\servername\DevShare</Setter>  
        </DataItem>  
      </Data>  
```  

 Wywoływanie **GetDataNode (L "Sieć" & pData) -> Settings()** daje **IDataNodes** wystąpienia z dwoma elementami danych (które z kolei ma dwie właściwości).  

##### <a name="sizet-count"></a>size_t Count()  
 Ta metoda zwraca liczbę **DataItem** elementów.  

##### <a name="hresult-setcaptionpropertylpctstr-captionproperty"></a>HRESULT SetCaptionProperty(LPCTSTR captionProperty)  
 Składnik, który obsługuje ten interfejs obsługuje również **IBindableList**, która ułatwia wypełnić pole kombi z danymi ze strony XML. Ta metoda określa, które właściwości (settera) w każdym **DataItem** element zostanie użyty dla tego powiązania. Na przykład można wywołać tej metody za pomocą **DisplayName**, i użyje metody ustawiającej właściwości dla powiązania danych. Następnie będzie zawierał pole kombi **publicznego** i **zespół deweloperów** jako elementy.  

##### <a name="hresult-getpropertysizet-index-lpctstr-propertyname-out-lpbstr-propertyvalue"></a>HRESULT GetProperty(size_t index, LPCTSTR propertyName, [out] LPBSTR propertyValue)  
 Ta metoda pobiera właściwości z jednego z **DataItem** elementów. Zobacz tabelę 41 i 42 tabeli.  

### <a name="table-41-dataitem-getproperty"></a>41 tabeli. Funkcja GetProperty elementu danych  

|**Parametr**|**Opis**|  
|-|-|  
|**Indeks**|Wartość indeksu (począwszy od 0) **DataItem** dla których chcesz pobrać wartości właściwości|  
|**propertyName**|Nazwa właściwości metody ustawiającej, dla którego chcesz pobrać wartości|  
|**propertyValue**|Przy powrocie zawiera wartość ciągu właściwości|  

### <a name="table-42-hresult-getproperty"></a>42 tabeli. HRESULT GetProperty  

|||  
|-|-|  
|**HRESULT**|**Opis**|  
|**S_OK**|Właściwość została pobrana.|  
|**E_INVALIDARG**|Indeks jest poza koniec tablicy.|  

##### <a name="hresult-getnodesizet-index-out-isettingsproperties-ppnode"></a>HRESULT GetNode(size_t index, [out] ISettingsProperties **ppNode)  
 Ta metoda jest podobna do **GetProperty**, ale zamiast zwracać jedną wartość z **DataItem**, zwraca całą **DataItem** ujęte w  **ISettingsProperties** interfejsu. Zobacz tabelę 43 i 44 tabeli.  

### <a name="table-43-hresult-getnode"></a>43 tabeli. HRESULT GetNode  

|**Parametr**|**Opis**|  
|-|-|  
|Indeks|Wartość indeksu (począwszy od 0) **DataItem** dla których chcesz pobrać wartości właściwości|  
|**ppNode**|Po zakończeniu **ISettingsProperties** interfejs, który opakowuje **DataItem** węzła|  

### <a name="table-44-hresult-getnode-results"></a>44 tabeli. Wyniki GetNode HRESULT  

|**HRESULT**|**Opis**|  
|-|-|  
|**S_OK**|Węzeł został pobrany.|  
|**E_INVALIDARG**|Indeks jest poza koniec tablicy.|  

#### <a name="ifactoryregistry-interface"></a>IFactoryRegistry Interface  

```  
__interface IFactoryRegistry : IUnknown  
{  
    void Register(LPCTSTR type,  IClassFactory *pFactory);  
    HRESULT LoadAndRegister(LPCTSTR dllName, ILogger *pLogger);  
    BOOL Contains(LPCTSTR type);  
    HRESULT GetFactory(LPCTSTR type,  IClassFactory **ppFactory);  
    HRESULT CreateInstance(LPCTSTR type,  IUnknown **ppInstance);  
    HRESULT SetContainer(IWizardPageContainer *pContainer);  
    HRESULT RegisterService(REFGUID iid, IUnknown *pService);  
    HRESULT GetService(REFGUID iid,  IUnknown **ppService);  
};  
```  

##### <a name="overview"></a>Omówienie  
 Podczas tworzenia nowej niestandardowej strony co najmniej, musisz utworzyć *fabryki strony*— klasa implementująca **IClassFactory**. (Można użyć **ClassFactoryImpl** jako klasę podstawową fabrycznej.)  

##### <a name="void-registerlpctstr-type--iclassfactory-pfactory"></a>Unieważnij rejestru (LPCTSTR typu, elementu IClassFactory \*pFactory)  
 Ta metoda rejestruje fabrykę klas z rejestru. Zobacz 45 tabeli.  

### <a name="table-45-iclassfactory-void-register"></a>45 tabeli. Rejestr void IClassFactory  

|**Parametr**|**Opis**|  
|-|-|  
|**Typ**|Ciąg, który identyfikuje fabryka rejestrujesz; Ogólnie rzecz biorąc ten parametr powinien mieć nazwę swojej firmy w ciągu, aby upewnić się, że jest unikatowa|  
|**pFactory**|Wskaźnik do Twojego wystąpienia fabryki klas|  

##### <a name="hresult-loadandregisterlpctstr-dllname-ilogger-plogger"></a>HRESULT LoadAndRegister(LPCTSTR dllName, ILogger \*pLogger)  
 Ta metoda jest tylko do użytku wewnętrznego.  

##### <a name="bool-containslpctstr-type"></a>Wartość logiczna Contains(LPCTSTR type)  
 Ta metoda jest zwykle do użytku wewnętrznego. Sprawdza, czy fabryka klas została zarejestrowana dla typu.  

##### <a name="hresult-getfactorylpctstr-type--iclassfactory-ppfactory"></a>HRESULT GetFactory(LPCTSTR type, IClassFactory **ppFactory)  
 Ta metoda umożliwia pobranie fabryki klasy. Zazwyczaj spowodowałoby wywołanie **CreateInstance**. Jednak jeśli zamierzasz utworzyć wiele tego składnika, jest bardziej wydajne, aby pobrać fabrykę, a następnie poprosić go w celu utworzenia wystąpienia dla Ciebie.  

##### <a name="hresult-createinstancelpctstr-type--iunknown-ppinstance"></a>HRESULT CreateInstance(LPCTSTR type, IUnknown **ppInstance)  
 Ta metoda tworzy nowe wystąpienie składnika danego jego typu. Użyj **CreateInstance** metody szablonu zamiast tego, co pozwala Tworzenie obiektów bezpieczne.  

##### <a name="hresult-setcontaineriwizardpagecontainer-pcontainer"></a>HRESULT SetContainer(IWizardPageContainer \*pContainer)  
 Ta metoda jest tylko do użytku wewnętrznego.  

##### <a name="hresult-registerservicerefguid-iid-iunknown-pservice"></a>HRESULT RegisterService(REFGUID iid, IUnknown \*pService)  
 *Usługi* wystąpień jednego składnika, który może być używana w wielu miejscach. Można użyć tej metody do zarejestrowania usługi na jednej stronie, a następnie pobrać tego samego wystąpienia z innej strony.  

##### <a name="hresult-getservicerefguid-iid--iunknown-ppservice"></a>HRESULT GetService(REFGUID iid, IUnknown **ppService)  
 Ta metoda pobiera to usługa, która została wcześniej zarejestrowane w wyniku wywołania RegisterService.  

##### <a name="hresult-setlanguagelangid-languageid"></a>HRESULT SetLanguage(LANGID languageId)  
 Ta metoda określa język kreatora UDI identyfikator języka podany w **languageId** parametru.  

##### <a name="langid-getlanguage"></a>Identyfikator LANGID GetLanguage()  
 Ta metoda zwraca wartość identyfikatora języka dostarczona z **/Locale** parametru wiersza polecenia dla Kreatora UDI. Metoda zwraca jedną z następujących wartości:  

-   Wartość identyfikatora języka, pod warunkiem z **/Locale** parametru wiersza polecenia  

-   0, jeśli nie podano **/Locale** parametru wiersza polecenia  

#### <a name="ilogger-interface"></a>Interfejs ILogger  

```  
__interface ILogger : IUnknown  
{  
    HRESULT Init(LPCWSTR logFilename);  
    HRESULT MoveLog(LPCWSTR logFilename);  
    HRESULT LogBase(EMessageType messageType, LPCTSTR component, SYSTEMTIME eventTime, LPCTSTR message);  
    HRESULT Log(EMessageType messageType, LPCTSTR component, LPCTSTR message);  
    HRESULT Error(HRESULT error, LPCTSTR component, LPCTSTR message);  
    HRESULT Error2(HRESULT error, LPCTSTR component, LPCTSTR message, LPCTSTR message2);  
    HRESULT Normal(LPCTSTR component, LPCTSTR message);      
    HRESULT Normal2(LPCTSTR component, LPCTSTR message, LPCTSTR message2);  
    HRESULT Verbose(LPCTSTR component, LPCTSTR message);  
    HRESULT Verbose2(LPCTSTR component, LPCTSTR message, LPCTSTR message2);  
    HRESULT Debug(LPCWSTR component, LPCWSTR message);  
    HRESULT EnableDebug(BOOL debug);  
    HRESULT Close(void);  
    HRESULT GetLogFilename(LPBSTR pFilename);  
};  
```  

##### <a name="overview"></a>Omówienie  
 Kreator UDI rejestruje informacje w pliku dziennika, który ułatwia rozwiązywanie problemów znalezionej w polu. Należy dobrze stron do rejestrowania informacji. Wskaźnik do interfejsu z może być uzyskany w stronę za pomocą strony **Logger()** metody. Wiersze w pliku dziennika zawierać "poziomu" tego błędu reprezentuje, normalny, pełne lub komunikaty debugowania.  

> [!NOTE]
>  Komunikaty debugowania nie są zapisywane w pliku dziennika, dopóki nie zostanie włączona obsługa debugowania. Można włączyć obsługę debugowania, dodając następujący wiersz do **styl** elementu w pliku .config:  

```  
<Setter Property="debug">true</Setter>  
```  

##### <a name="init"></a>init  

```  
HRESULT Init(LPCWSTR logFilename)  
```  

 Ta metoda jest tylko do użytku wewnętrznego.  

##### <a name="movelog"></a>MoveLog  

```  
HRESULT MoveLog(LPCWSTR logFilename)  
```  

 Ta metoda jest tylko do użytku wewnętrznego.  

##### <a name="logbase"></a>LogBase  

```  
HRESULT LogBase(EMessageType messageType, LPCTSTR component, SYSTEMTIME eventTime, LPCTSTR message)  
```  

 Ta metoda jest tylko do użytku wewnętrznego.  

##### <a name="log"></a>Log  

```  
HRESULT Log(EMessageType messageType, LPCTSTR component, LPCTSTR message)  
```  

 Ta metoda jest tylko do użytku wewnętrznego.  

##### <a name="error"></a>Błąd  

```  
HRESULT Error(HRESULT error, LPCTSTR component, LPCTSTR message)  
```  

 Wywołanie tej metody do rejestrowania informacji o błędzie. Zobacz 46 tabeli.  

### <a name="table-46-hresult-error"></a>46 tabeli. Błąd HRESULT  

|**Parametr**|**Opis**|  
|-|-|  
|**Błąd**|Kod błędu zwrócony przez wywołanie (ten kod zostaną wyświetlone w pozycji dziennika jako liczbę).|  
|**Składnik**|Ciąg, który identyfikuje źródło błędu, który jest zazwyczaj ze strony lub składnik, który ma być zapisany|  
|**Komunikat**|Komunikat, który objaśnia, co powoduje błąd|  

#####  <a name="Error2"></a> error2  

```  
HRESULT Error2(HRESULT error, LPCTSTR component, LPCTSTR message, LPCTSTR message2)  
```  

 Ta metoda jest podobna **błąd** metoda umożliwia jednak komunikat dwóch części. Komunikatu końcowego ma "komunikat" i "Komunikat2" w pliku wyjściowym. Jest to po prostu metodę wygody.  

##### <a name="normal"></a>Normalne  

```  
HRESULT Normal(LPCTSTR component, LPCTSTR message)  
```  

 Ta metoda rejestruje normalnego komunikatu. Zobacz opis [błąd](#Error) metody dla parametrów.  

##### <a name="normal2"></a>Normal2  

```  
HRESULT Normal2(LPCTSTR component, LPCTSTR message, LPCTSTR message2)  
```  

 Ta metoda rejestruje normalnego komunikatu. Zobacz opis [Error2](#Error2) metody dla parametrów.  

##### <a name="verbose"></a>Pełny  

```  
HRESULT Verbose(LPCTSTR component, LPCTSTR message)  
```  

 Ta metoda rejestruje komunikat trybu informacji pełnej. Zobacz opis [błąd](#Error) metody dla parametrów.  

##### <a name="verbose2"></a>Verbose2  

```  
HRESULT Verbose2(LPCTSTR component, LPCTSTR message, LPCTSTR message2)  
```  

 Ta metoda rejestruje komunikat trybu informacji pełnej. Zobacz opis [Error2](#Error2) metody dla parametrów.  

##### <a name="debug"></a>Debugowania  

```  
HRESULT Debug(LPCWSTR component, LPCWSTR message)  
```  

 Ta metoda rejestruje komunikat debugowania. Zobacz opis [błąd](#Error) metody dla parametrów. Debugowanie komunikaty nie są zapisywane do pliku, chyba że jest włączona. W sekcji Przegląd szczegóły.  

##### <a name="enabledebug"></a>EnableDebug  

```  
HRESULT EnableDebug(BOOL debug)  
```  

 Ta metoda jest tylko do użytku wewnętrznego.  

##### <a name="close"></a>Zamknij  

```  
HRESULT Close(void)  
```  

 Ta metoda jest tylko do użytku wewnętrznego.  

##### <a name="getlogfilename"></a>GetLogFilename  

```  
HRESULT GetLogFilename(LPBSTR pFilename)  
```  

 Ta metoda pobiera nazwę pliku dziennika.  

#### <a name="iorientation-interface"></a>Interfejs IOrientation  

```  
__interface IOrientation : IUnknown  
{  
    void SetController(IWizardDialogController *pController);  
    int AddPage(LPCTSTR name);  
    void SelectPage(int index);  
};  
```  

 Ten interfejs jest tylko do użytku wewnętrznego.  

#### <a name="isettings-interface"></a>Interfejs ISettings  

```  
__interface ISettings : IUnknown  
{  
    int NumDlls();  
    int NumPages();  

    HRESULT SetStage(LPCWSTR stageName);  
    HRESULT GetDllName(long index, __out LPBSTR pDllName);  
    HRESULT GetPageInfo(long index, __out ISettingsProperties **ppPageInfo);  
    HRESULT GetStyle(__out ISettingsProperties **ppStyleInfo);  
};  
```  

 Ten interfejs jest tylko do użytku wewnętrznego.  

#### <a name="isettingsproperties-interface"></a>Interfejs ISettingsProperties  

```  
__interface ISettingsProperties : IUnknown  
{  
    HRESULT GetAttribute(LPCTSTR attributeName, __out LPBSTR attributeValue);  
    IStringProperties * Properties();  
   RESULT SelectNodes(LPCTSTR xPath, __out IXMLDOMNodeList **ppList);  
    HRESULT SelectSingleNode(LPCTSTR xPath, __out IXMLDOMNode **ppNode);  
    HRESULT GetDataNode(LPCTSTR name, __out ISettingsProperties **ppNode);  
    HRESULT GetDataNodes(__out IDataNodes **ppNodes);  
    HRESULT GetChildDataNodes(LPCTSTR childeName, __out IDataNodes **ppNodes);  
};  
```  

##### <a name="overview"></a>Omówienie  
 Ten interfejs umożliwia dostęp do danych strony. Aby uzyskać dostęp do danych strony najwyższego poziomu, użyj strony **Settings()** metody.  

##### <a name="hresult-getattributelpctstr-attributename--lpbstr-attributevalue"></a>HRESULT GetAttribute(LPCTSTR attributeName, LPBSTR attributeValue)  
 Ta metoda umożliwia pobieranie wartości atrybutów w węźle głównym jest **strony** węzła, gdy używasz **Settings()** metody strony.  

##### <a name="istringproperties--properties"></a>IStringProperties * obiekcie Properties()  
 Ta metoda zapewnia dostęp do wartości właściwości metody ustawiającej w węźle głównym. Na stronie są właściwości najwyższego poziomu.  

##### <a name="hresult-selectnodeslpctstr-xpath--ixmldomnodelist-pplist"></a>HRESULT SelectNodes(LPCTSTR xPath, IXMLDOMNodeList **ppList)  
 Tę metodę można wywołać, aby bezpośrednio pobrać listy węzłów XML za pomocą wyrażenia XPath. Warto użyć jednego z innych metod, jeśli to możliwe. Tej metody można użyć tylko wtedy, gdy do węzłów nie można pobrać inny sposób.  

##### <a name="hresult-selectsinglenodelpctstr-xpath--ixmldomnode-ppnode"></a>HRESULT SelectSingleNode(LPCTSTR xPath, IXMLDOMNode **ppNode)  
 Tę metodę można wywołać, aby bezpośrednio pobrać pojedynczego węzła XML za pomocą wyrażenia XPath. Warto użyć jednego z innych metod, jeśli to możliwe. Tej metody można użyć tylko wtedy, gdy do węzła nie można pobrać inny sposób.  

##### <a name="hresult-getdatanodelpctstr-name--isettingsproperties-ppnode"></a>HRESULT GetDataNode(LPCTSTR name, ISettingsProperties **ppNode)  
 Pobrać **danych** na ten element na podstawie elementu **nazwa** atrybutu.  

##### <a name="hresult-getdatanodesidatanodes-ppnodes"></a>HRESULT GetDataNodes(IDataNodes **ppNodes)  
 Ta metoda powoduje pobranie listy **DataItem** elementy w obszarze bieżącego węzła. Z poziomu strony należy wywołać **GetDataNode** można pobrać **ISettingsProperty** interfejs do danych. Następnie, w tym wystąpieniu wywołać **GetDataNodes** można pobrać listy rekordów. Na przykład podany plik XML:  

```  
    <Page …>  
      <Data Name="Network">  
        <DataItem>  
          <Setter Property="DisplayName">Public</Setter>  
          <Setter Property="Share">\\servername\Share</Setter>  
        </DataItem>  
        <DataItem>  
          <Setter Property="DisplayName">Dev Team</Setter>  
          <Setter Property="Share">\\servername\DevShare</Setter>  
        </DataItem>  
      </Data>  

PSettingsProperties pData;  
Settings()->GetDataNode(L"Network", &pData);  
PDataNodes pNodes;  
pData->GetDataNodes(&pNodes);  
```  

##### <a name="hresult-getchilddatanodeslpctstr-childename--idatanodes-ppnodes"></a>HRESULT GetChildDataNodes(LPCTSTR childeName, IDataNodes **ppNodes)  
 Ta metoda umożliwia szybkie uzyskanie do zestawu **DataItem** węzłów w obszarze określonej **danych** węzła. Za pomocą XML z **GetDataNodes** przykład następujący kod jest równoważne jako czterech wierszy kodu w przykładzie w obszarze **GetDataNodes** , ale sprawdzanie błędów:  

```  
ISimpleStringProperties Interface  
```  

#### <a name="isimplestringproperties-interface"></a>Interfejs ISimpleStringProperties  

```  
__interface ISimpleStringProperties : IStringProperties  
{  
void Add(LPCTSTR propertyName, LPCTSTR value);  
};  
```  

 Samodzielnie ten interfejs nie może być przydatne. Jednak jest implementowany przez **ID_SimpleStringProperties** składnik, który implementuje również **IStringProperties** interfejsu. Ten składnik można użyć w przypadku gdy musisz przekazać zbiór właściwości do innego składnika, takiego jak zadania, ale chcesz dodać wartości programowo, zamiast wartości z pliku XML. Poniżej przedstawiono przykład sposobu użyje tego interfejsu:  

```  
PSimpleStringProperties *pProperties;  
CreateInstance(Container(), ID_SimpleStringProperties, &pProperties);  
pProperties->Add(L"filename", L"%windir%\\system32\\cscript.exe");  
pTask->Init(pProperties, nullptr);  
IStringProperties  
__interface IStringProperties : IUnknown  
{  
    HRESULT Get(LPCTSTR propertyName, [out] LPBSTR pPropValue);  
};  
```  

 Ten interfejs umożliwia proste dostęp do zestawu elementów setter, które pochodzą z pliku XML. Ten interfejs jest dostępne dla właściwości, używając strony **Settings() -> obiekcie Properties()**.  

##### <a name="hresult-getlpctstr-propertyname-out-lpbstr-ppropvalue"></a>HRESULT Get(LPCTSTR propertyName, [out] LPBSTR pPropValue)  
 Ta metoda pobiera wartość jednej właściwości. Zobacz tabelę 47 i 48 tabeli.  

### <a name="table-47-ihresult-get-property-value"></a>47 tabeli. Wartość właściwości IHRESULT Get  

|**Parametr**|**Opis**|  
|-|-|  
|**propertyName**|Nazwa właściwości, która ma być do odczytu|  
|**pPropValue**|Po zakończeniu zawiera wartość właściwości w postaci ciągu (Ta wartość będzie **nullptr** , jeśli nie ma takich właściwości.)|  

### <a name="table-48-ihresult-get-property-value-results"></a>48 tabeli. IHRESULT uzyskiwać wyniki z wartości właściwości  

|||  
|-|-|  
|**HRESULT**|**Opis**|  
|**S_OK**|Pobrać wartości właściwości.|  
|**E_INVALIDARG**|Nie ma właściwości o nazwie podane.|  

#### <a name="itaskmanager-interface"></a>Interfejs ITaskManager  

```  
__interface ITaskManager : IUnknown  
{  
    HRESULT Init(IWizardPageView *pPageView, int idListView, int idMessage, int idRetryButton, ISettingsProperties *pPageInfo, ITaskManagerCallback *pCallback);  
    HRESULT SetFailMessage(LPCWSTR message);  

    HRESULT Start(void);  

    HRESULT GetTaskMessage(size_t index, LPBSTR message);  
    HRESULT GetResultType)(size_t index, LPBSTR type);  
    HRESULT GetProperty(size_t index, LPCTSTR propertyName, LPBSTR value);  
    int GetSelectedIndex(void);  
    HRESULT Wait(DWORD waitMilliseconds);  
    size_t FailedCount(void);  
    size_t WarningCount(void);  
    size_t SucceedCount(void);  
    size_t RunningCount(void);  

    void OnCommonControlEvent(WORD controlId, LPNMHDR pInfo);  
    void OnControlEvent(WORD eventId, WORD controlId);  
    void EnableButtons(BOOL enable);  
}  
```  

 Ten interfejs jest implementowany przez **Menedżer zadań** składnika (**ID_TaskManager** w ITaskManager.h), czyli składnik, który uruchamia zadania na stronie wstępnej. Można użyć wstępnej strony bezpośrednio, czyli co zrobić w większości przypadków, lub kompilacji własnej strony, dzięki czemu ten składnik, czy większość pracy.  

##### <a name="hresult-initiwizardpageview-ppageview-int-idlistview-int-idmessage-int-idretrybutton-isettingsproperties-ppageinfo-itaskmanagercallback-pcallback"></a>HRESULT Init(IWizardPageView \*pPageView, int idListView, int idMessage, int idRetryButton, ISettingsProperties \*pPageInfo, ITaskManagerCallback \*pCallback)  
 Tej metody należy wywołać przed wywołaniem innej metody. Inicjuje on **Menedżer zadań** składnika. Zobacz 49 tabeli.  

### <a name="table-49-hresult-init"></a>49 tabeli. HRESULT Init  

|**Parametr**|**Opis**|  
|-|-|  
|**pPageView**|Umożliwia dostęp do strony, które będą uruchomione zadania (Ta strona musi mieć określony zestaw formanty, które zostały opisane w następnej kilka parametrów).|  
|**idListView**|Identyfikator formantu **ListView** kontrolkę, która będzie wyświetlana na liście zadań i stanem tych zadań|  
|**idMessage**|Identyfikator formantu pola tekstowego, który będzie używany do wyświetlania komunikatu dla wybranego zadania|  
|**idRetryButton**|Identyfikator formantu przycisku można kliknąć, aby ponownie uruchomić zadania|  
|**pPageInfo**|Otokę strony XML (**Menedżer zadań** ładuje zestaw zadań do wykonania z tego pliku XML.)|  
|**pCallback**|Może mieć wartości null (Jeśli ten parametr nie jest zerowa, **Menedżer zadań** wywołania **uruchomiono** metody podczas uruchamiania zadania i **Zakończono** metodę dla każdego zadania, które zakończeniu.)|  

##### <a name="hresult-setfailmessagelpcwstr-message"></a>HRESULT SetFailMessage(LPCWSTR message)  
 Ta metoda określa komunikat, który będzie wyświetlany, jeśli jeden lub więcej zadań zakończy się niepowodzeniem.  

##### <a name="hresult-startvoid"></a>HRESULT Start(void)  
 Ta metoda uruchamiania wszystkich zadań. Każde zadanie jest uruchomiona na oddzielnym wątku.  

##### <a name="hresult-gettaskmessagesizet-index-lpbstr-message"></a>HRESULT GetTaskMessage(size_t index, LPBSTR message)  
 Ta metoda jest tylko do użytku wewnętrznego. Pobiera on bieżącego komunikatu dla zadania, w zależności od jej indeks w liście zadań.  

##### <a name="hresult-getresulttypesizet-index-lpbstr-type"></a>HRESULT GetResultType) (indeks size_t LPBSTR typu)  
 Ta metoda pobiera bieżącą "type" dla zadania. 50 tabeli przedstawiono dostępne typy.  

### <a name="table-50-hresult-getresulttype"></a>50 tabeli. HRESULT GetResultType  

|**Typ**|**Opis**|  
|-|-|  
|**0**|Reprezentuje zadanie, które zakończyło się pomyślnie|  
|**1**|Reprezentuje zadania, które zwróciło ostrzeżenie|  
|**-1**|Reprezentuje zadania nie powiodło się|  

 Typ jest pobierana przez patrzeć kod błędu lub zakończenia tego zadania w celu znalezienia dopasowania w zadaniu < ExitCodes\> — element XML.  

##### <a name="hresult-getpropertysizet-index-lpctstr-propertyname-lpbstr-value"></a>HRESULT GetProperty(size_t index, LPCTSTR propertyName, LPBSTR value)  
 Ta metoda służy do pobierania przez strony postępu i inspekcja **BitmapFilename** metody ustawiającej właściwości, można wyświetlić obraz obok komunikatu dla zadania, które można wyróżnić. Innymi słowy można dodać niestandardowe metody ustawiającej do pliku XML zadania i pobierz go z tą metodą.  

##### <a name="int-getselectedindexvoid"></a>int GetSelectedIndex(void)  
 Ta metoda pobiera Indeks aktualnie zaznaczonego zadania, które jest przydatne, jeśli chcesz pobrać dodatkowe informacje o zadaniu (zobacz **GetProperty** metody) do wyświetlenia dla wybranego zadania. Postęp i wstępnego stron Użyj tej metody do wyświetlania obrazu dla wybranego zadania.  

##### <a name="hresult-waitdword-waitmilliseconds"></a>HRESULT Wait(DWORD waitMilliseconds)  
 Ta metoda ułatwia głównie przy użyciu testów jednostkowych tak testu można zapewnić, że zadania zakończone przed wyjścia testu jednostkowego. Ta metoda nie będzie zwykle wywołana. Zwraca albo po zakończeniu wszystkich zadań, uruchomienia lub czas oczekiwania upłynął.  

##### <a name="sizet-failedcountvoid"></a>size_t FailedCount(void)  
 Ta metoda zwraca liczbę zadań obecnie oznaczony jako zakończony niepowodzeniem.  

##### <a name="sizet-warningcountvoid"></a>size_t WarningCount(void)  
 Ta metoda zwraca liczbę zadań obecnie oznaczone jako ostrzeżenie.  

##### <a name="sizet-succeedcountvoid"></a>size_t SucceedCount(void)  
 Ta metoda zwraca liczbę zadań obecnie oznaczone jako zakończyło się pomyślnie.  

##### <a name="sizet-runningcountvoid"></a>size_t RunningCount(void)  
 Ta metoda zwraca liczbę aktualnie uruchomione zadanie.  

##### <a name="void-oncommoncontroleventword-controlid-lpnmhdr-pinfo"></a>void OnCommonControlEvent (WORD controlId, LPNMHDR pInfo)  
 Ta metoda jest wywoływana ze strony użytkownika **OnCommonControlEvent** tak **Menedżer zadań** może przetwarzać zdarzenia należy.  

##### <a name="void-oncontroleventword-eventid-word-controlid"></a>void OnControlEvent (identyfikator zdarzenia programu WORD, controlId programu WORD)  
 Ta metoda jest wywoływana ze strony użytkownika **OnControlEvent** tak **Menedżer zadań** może przetwarzać zdarzenia należy.  

##### <a name="void-enablebuttonsbool-enable"></a>void EnableButtons(BOOL enable)  
 Ta metoda jest tylko do użytku wewnętrznego.  

#### <a name="iwizardcomponent-interface"></a>Interfejs IWizardComponent  

```  
__interface IWizardComponent : IUnknown  
{  
    HRESULT SetContainer(IWizardPageContainer *pContainer);  
};  
```  

##### <a name="overview"></a>Omówienie  
 Zazwyczaj można będzie implementuje ten interfejs bezpośrednio, ale zamiast tego za pośrednictwem **WizardComponent** klasy szablonu. Jeśli składnika implementuje ten interfejs fabryki klasy zostały zarejestrowane w rejestrze, składnika otrzymuje wskaźnik **IWizardPageContainer** wystąpienie podczas jego tworzenia. Dzięki temu można, na przykład, dostęp do rejestratora lub rejestru do tworzenia innych składników, które mogą wymagać składnika.  

#### <a name="iwizarddialogcontroller-interface"></a>Interfejs IWizardDialogController  

```  
__interface IWizardDialogController : IUnknown  
{  
    void Initialize(ISettings *pSettings);  
    void InitPages(void);  
    void Start();  
    void Next();  
    void Finish();  
    void Previous();  
    int NumPages();  
    void Cancel();  

    HRESULT Focus(WizardButtons button);  
    HRESULT SetEnable(WizardButtons button, BOOL enable);  
    void ShowWarningMessage(LPCTSTR message);  
    void HideWarningMessage();  

    void ChangePage(size_t newIndex);  
    IUnknown *CurrentPage(void);  
    HRESULT GetCurrentTitle([out, retval] LPBSTR pDisplayName);  
};  
```  

 Ten interfejs jest tylko do użytku wewnętrznego.  

#### <a name="iwizarddialogview-interface"></a>Interfejs IWizardDialogView  

```  
__interface IWizardDialogView : IUnknown  
{  
    HRESULT LoadBannerImage(LPCTSTR bannerFilename);  
    HRESULT LoadPage(LPCTSTR pageType, ISettingsProperties *pPageSettings, IWizardPageView **view);  
    HRESULT SetEnable(WizardButtons button, BOOL enable);  
    HRESULT Focus(WizardButtons button);  
    void EnableFinish(BOOL isFinish);  
    void Exit(int exitCode);  
    void ShowWarningMessage(LPCTSTR message);  
    void HideWarningMessage(void);  
    void SetTitle(LPCTSTR title);  
    void SetPageTitle(LPCTSTR title);  
    int ShowMessageBox(LPCTSTR message, LPCTSTR lpCaption, UINT uType);  
    HWND GetHwnd(void);  
    void UpdateFocus(void);  
};  
```  

 Ten interfejs jest tylko do użytku wewnętrznego.  

####  <a name="IWizardPageInterface"></a> Interfejs IWizardPage  

```  
__interface IWizardPage : IUnknown  
{  
    HRESULT SetPageSettings(ISettingsProperties *pPageSettings);  
    HINSTANCE GetInstanceHandle(void);  
    int GetDialogResourceId(void);  
    void WindowCreated(IWizardPageView *pView, IWizardPageContainer *pContainer);  
    void WindowShown(void);  
    void WindowHidden(void);  

    HRESULT NextClicked(void);  
    void ControlEvent(WORD eventId, WORD controlId);  
    void CommonControlEvent(WORD controlId, LPNMHDR pInfo, LPBOOL pCancel);  
    void UnhandledEvent(HWND hwnd, UINT message, WPARAM wParam, LPARAM lParam);  
};  
```  

##### <a name="overview"></a>Omówienie  
 Ten interfejs jest implementowany przez **WizardPageImpl**, dzięki czemu nie będą zazwyczaj musi implementacji tego użytkownika. Kreator wywołuje wszystkie te metody automatycznie, gdy interakcji z Twojej strony niestandardowe.  

#### <a name="iwizardpagecontainer-interface"></a>IWizardPageContainer Interface  

```  
__interface IWizardPageContainer : IUnknown  
{  
    ILogger * Logger(void);  
    IPropertyBag * Properties(void);  
    HRESULT CreateInstance(LPCTSTR type, [out] IUnknown **ppInstance);  
    HRESULT GetService(REFIID iid, [out] IUnknown **ppInstance);  
    HRESULT ReplaceVariables(LPCTSTR source, [out] LPBSTR pDest);  
    HRESULT GotoPage(LPCTSTR pageName);  
    int ShowMessageBox(LPCTSTR message, LPCTSTR lpCaption, UINT uType);  
    BOOL InPreview(void);  
    HWND GetHwnd(void);  
};  
```  

##### <a name="overview"></a>Omówienie  
 Ten interfejs jest dostępny do strony za pomocą **kontenera** — metoda (implementowane przez **WizardPageImpl**) i zapewnia dostęp do różnych usług kreatora.  

##### <a name="ilogger--loggervoid"></a>ILogger * Logger(void)  
 Ta metoda służy do zapisywania wiadomości do pliku dziennika — na przykład:  

```  
Logger()->Verbose(s_component, L"Message for log file");  
```  

##### <a name="ipropertybag--propertiesvoid"></a>IPropertyBag * Properties(void)  
 Ta metoda zapewnia dostęp do zmiennych "pamięci", które są właściwości, które znajdują się w pamięci tylko wtedy, gdy Kreator UDI jest uruchomiony. Te właściwości są dostępne dla innych stron w kodzie lub za pomocą XML **$memoryVarName$** składni.  

##### <a name="hresult-createinstancelpctstr-type-out-iunknown-ppinstance"></a>HRESULT CreateInstance(LPCTSTR type, [out] IUnknown **ppInstance)  
 Ta metoda służy do utworzenia nowego wystąpienia każdego składnika, który został zarejestrowany. Jednak zaleca się użycie funkcji szablonu **CreateInstance**, ponieważ jest silnie typizowane.  

##### <a name="hresult-getservicerefiid-iid-out-iunknown-ppinstance"></a>HRESULT GetService(REFIID iid, [out] IUnknown **ppInstance)  
 Ta metoda umożliwia pobieranie usługi, który został zarejestrowany. Jednak zaleca się wywołać **GetService** funkcji szablonu, który jest silnie typizowane (zamiast **IUnknown**).  

##### <a name="hresult-replacevariableslpctstr-source-out-lpbstr-pdest"></a>HRESULT ReplaceVariables(LPCTSTR source, [out] LPBSTR pDest)  
 Ta metoda obsługuje pracy ze zmiennymi wewnątrz wartości ciągu. Obsługuje ona formatów wyświetlany w tabeli 51 i 52 tabeli.  

### <a name="table-51-hresult-replacevariables"></a>51 tabeli. HRESULT ReplaceVariables  

|**Format**|**Opis**|  
|-|-|  
|**$Name$**|Zamienia wartości zmiennej pamięci o tej nazwie (Jeśli nie ma żadnych pamięci zmienna o nazwie, "token" zostaną usunięte).|  
|**Nazwa %**|Zmienną sekwencji zadań lub zmiennej środowiskowej. Kolejność jest następująca:<br /><br /> 1.  Wartość zmiennej sekwencji zadań, należy użyć, jeśli jest obecny.<br />2.  Użyj wartości zmiennej środowiskowej, jeśli jest obecny.<br />3.  W przeciwnym razie Usuń ten tekst z ciągu.|  

### <a name="table-52-hresult-parameter"></a>Tabela 52. Parametrem HRESULT  

|**Parametr**|**Opis**|  
|-|-|  
|**Obiekt źródłowy**|Ciąg wejściowy może zawierać dowolną kombinację **$** i **%** zmienne lub brak gwarancja|  
|**pDest**|Przy powrocie zawiera nowe ciąg, który zawiera wszystkie tokeny zastąpione zgodnie z tabeli 51|  

##### <a name="hresult-gotopagelpctstr-pagename"></a>HRESULT GotoPage(LPCTSTR pageName)  
 Ta metoda nie została w pełni przetestowany. Będzie można przełączyć bezpośrednio do określonej strony na podstawie nazwy strony zgodnie z definicją w pliku .config XML. Wywołanie tej metody pomija **OnNextClicked** na stronie. Ponadto jest zachowanie tej metody może ulec zmianie, więc Użyj na własne ryzyko.  

##### <a name="int-showmessageboxlpctstr-message-lpctstr-lpcaption-uint-utype"></a>int ShowMessageBox (komunikat LPCTSTR, LPCTSTR lpCaption, UINT uType)  
 Ta metoda wyświetla komunikat z tekstem i musisz podać podpis. **UType** parametr ma wartość wprowadzona do **MessageBox** funkcji Win32.  

##### <a name="bool-inpreviewvoid"></a>Wartość logiczna InPreview(void)  
 Ta metoda zwraca wartość PRAWDA, jeśli uruchomić kreatora w trybie "w wersji zapoznawczej" podając **/Podgląd** przełącznika. W wersji zapoznawczej **dalej** przycisk nigdy nie jest wyłączony. Ta metoda umożliwia obejście kodu w wersji zapoznawczej, na przykład, który może powodować problemy, gdy nie ma prawidłowych danych na stronie.  

##### <a name="hwnd-gethwndvoid"></a>HWND GetHwnd(void)  
 Ta metoda zwraca **HWND** głównego okna dialogowego. Użyj tej metody z rozwagą. Ogólnie rzecz biorąc Kreator UDI interfejsu programowania aplikacji zaprojektowano tak, aby nigdy nie pracować bezpośrednio za pomocą dojścia do okna.  

#### <a name="iwizardpageview-interface"></a>Interfejs IWizardPageView  

```  
__interface IWizardPageView : IUnknown  
{  
    HRESULT GetControlWrapper(int itemId, DialogControlTypes controlType, IUnknown **ppControl);  
    HWND GetHwnd(void);  
    HWND GetControl(int itemId);  
    HRESULT Show (void);  
    HRESULT Hide(void);  
    HRESULT Focus(int itemId);  
    IWizardPage * Page(void);  
    IFormController * Form(void);  

    HRESULT FocusWizardButton(WizardButtons button);  
    HRESULT SetEnable(WizardButtons button, BOOL enable);  
    void ShowWarningMessage(LPCTSTR message);  
    void HideWarningMessage(void);  
};  
```  

 Ten interfejs jest dostępna dla kodu na stronie za pośrednictwem **widoku** — metoda (implementowane przez **WizardPageImpl**).  

##### <a name="hresult-getcontrolwrapperint-itemid-dialogcontroltypes-controltype-iunknown-ppcontrol"></a>HRESULT GetControlWrapper(int itemId, DialogControlTypes controlType, IUnknown \*ppControl)  
 Używa Kreatora UDI *otoki*, które są elewacje interakcji z kontrolki na stronie. Za pomocą tych elewacje zamiast rzeczywistej formanty ułatwia napisać testy strony, ponieważ zapewniają zasymulować elewacje z testów.  

 Zamiast bezpośrednio za pomocą tej metody, warto użyć **GetControlWrapper** szablonu metodę, która jest silnie typizowane — na przykład:  

```  
PComboBox m_pLanguagePackCombo;  
GetControlWrapper(View(), IDC_MY_COMBO, CONTROL_COMBO_BOX, &m_pCombo);  
```  

##### <a name="hwnd-gethwndvoid"></a>HWND GetHwnd(void)  
 Ta metoda zwraca uchwytu okna dla strony. Ogólnie rzecz biorąc nie należy dostęp do tego uchwytu okna.  

##### <a name="hwnd-getcontrolint-itemid"></a>HWND GetControl(int itemId)  
 Jeśli konieczne, można wywołać tej metody można pobrać uchwytu okna dla formantu na stronie. (Zaleca się wywołać **GetControlWrapper** funkcji szablonu).  

##### <a name="hresult-show-void"></a>HRESULT Pokaż (void)  
 Ta metoda jest tylko do użytku wewnętrznego.  

##### <a name="hresult-hidevoid"></a>HRESULT Hide(void)  
 Ta metoda jest tylko do użytku wewnętrznego.  

##### <a name="hresult-focusint-itemid"></a>HRESULT Focus(int itemId)  
 Ustaw fokus wprowadzania do określonego formantu.  

##### <a name="iwizardpage--pagevoid"></a>IWizardPage * Page(void)  
 Ta metoda jest tylko do użytku wewnętrznego.  

##### <a name="iformcontroller--formvoid"></a>IFormController * Form(void)  
 Ta metoda jest tylko do użytku wewnętrznego.  

##### <a name="hresult-focuswizardbuttonwizardbuttons-button"></a>HRESULT FocusWizardButton(WizardButtons button)  
 Ustawia fokus na jeden z przycisków kreatora. **WizardButtons** ma dwie wartości: **BackButton** i **NextButton**.  

##### <a name="hresult-setenablewizardbuttons-button-bool-enable"></a>HRESULT SetEnable(WizardButtons button, BOOL enable)  
 Żądanie, że jeden z przycisków kreatora można włączać lub wyłączać. Przycisk może być niezgodny stan żądania. Na przykład po uruchomieniu kreatora UDI **/Podgląd** przełącznika, przyciski będzie zawsze włączony. **WizardButtons** ma dwie wartości: **BackButton** i **NextButton**.  

##### <a name="void-showwarningmessagelpctstr-message"></a>void ShowWarningMessage(LPCTSTR message)  
 Ta metoda wyświetla komunikat ostrzegawczy w dolnej części obszaru zawartości strony. Ten komunikat może być dowolny tekst, który ma.  

##### <a name="void-hidewarningmessagevoid"></a>void HideWarningMessage(void)  
 Ukryj ostrzeżenie informujące, że wyświetlony w wyniku wywołania **ShowWarningMessage**.  

#### <a name="ixmldocument-interface"></a>Interfejs IXmlDocument  

```  
__interface IXmlDocument : IUnknown  
    HRESULT Load(LPCTSTR filename);  
    HRESULT LoadXml(LPCTSTR xml);  
    HRESULT Save(LPCWSTR filename);  
    HRESULT GetParseErrorMessage(LPBSTR pMessage);  
    HRESULT SelectNodes(LPCTSTR xpath, IXMLDOMNodeList **ppNodes);  
    HRESULT SelectSingleNode(LPCTSTR xpath, IXMLDOMNode **ppNode);  
    HRESULT AddSchema(LPCTSTR filename, LPCTSTR ns);  
    HRESULT AddAttribute(IXMLDOMNode *pNode, LPCWSTR name, LPCWSTR value);  
    HRESULT CreateNode(DOMNodeType type, LPCWSTR name, LPCWSTR ns, IXMLDOMNode **ppNode);  
};  
```  

##### <a name="overview"></a>Omówienie  
 Ten interfejs jest implementowany przez **ID_IXmlDocument** składnika, który jest fasad zaprojektowane, aby ułatwić pracę z dokumentami XML w języku C++.  

##### <a name="hresult-loadlpctstr-filename"></a>HRESULT Load(LPCTSTR filename)  
 Ta metoda ładowania dokumentu XML z pliku zewnętrznego. Zwraca **S_OK** Jeśli plik został załadowany bez błędów lub **S_FALSE** Jeśli wystąpił błąd. Jeśli wystąpi błąd, można uzyskać komunikatu o błędzie przez wywołanie metody **GetParseErrorMessage**.  

##### <a name="hresult-loadxmllpctstr-xml"></a>HRESULT LoadXml(LPCTSTR xml)  
 Ta metoda ładowania dokumentu XML z ciągu zamiast pliku zewnętrznego. Inne niż źródła do odczytywania pliku XML, zachowanie jest taka sama jak **obciążenia** metody.  

##### <a name="hresult-savelpcwstr-filename"></a>HRESULT Save(LPCWSTR filename)  
 Ta metoda zapisuje dokument XML, który znajduje się w pamięci do pliku zewnętrznego.  

##### <a name="hresult-getparseerrormessagelpbstr-pmessage"></a>HRESULT GetParseErrorMessage(LPBSTR pMessage)  
 Ta metoda zwraca nowy ciąg z komunikatem o błędzie z ładowania dokumentu XML. Zawsze zwraca **S_OK**.  

##### <a name="hresult-selectnodeslpctstr-xpath-ixmldomnodelist-ppnodes"></a>HRESULT SelectNodes(LPCTSTR xpath, IXMLDOMNodeList \**ppNodes)  
 Ta metoda umożliwia przy użyciu wyrażenia XPath do pobierania kolekcję węzłów z dokumentu. Zawsze zwraca **S_OK**.  

##### <a name="hresult-selectsinglenodelpctstr-xpath-ixmldomnode-ppnode"></a>HRESULT SelectSingleNode(LPCTSTR xpath, IXMLDOMNode \**ppNode)  
 Ta metoda umożliwia Pobierz jeden węzeł z dokumentu za pomocą wyrażenia XPath. Zawsze zwraca **S_OK**.  

##### <a name="hresult-addschemalpctstr-filename-lpctstr-ns"></a>HRESULT AddSchema(LPCTSTR filename, LPCTSTR ns)  
 Ta metoda dodaje nazwę pliku schematu zewnętrznego, który będzie używany do sprawdzania poprawności schematu XML dokumentu po załadowaniu go. Przestrzeń nazw jest ciąg służy kwerendy XPath, mimo że ta nie została przetestowana.  

##### <a name="hresult-addattributeixmldomnode-pnode-lpcwstr-name-lpcwstr-value"></a>HRESULT AddAttribute(IXMLDOMNode \*pNode, LPCWSTR name, LPCWSTR value)  
 Ta metoda dodaje nowy atrybut do istniejący węzeł w dokumencie XML. Zobacz 53 tabeli.  

### <a name="table-53-hresult-addattribute"></a>53 tabeli. HRESULT AddAttribute  

|**Parametr**|**Opis**|  
|-|-|  
|**pNode**|Węzeł, do której chcesz dodać atrybut|  
|**Nazwa**|Nazwa nowego atrybutu|  
|**Wartość**|Wartość nowego atrybutu|  

##### <a name="hresult-createnodedomnodetype-type-lpcwstr-name-lpcwstr-ns-ixmldomnode-ppnode"></a>HRESULT CreateNode(DOMNodeType type, LPCWSTR name, LPCWSTR ns, IXMLDOMNode \**ppNode)  
 Wywołaj tę metodę, aby utworzyć nowy węzeł:  

```  
Pointer<IXMLDOMNode> pNewChild  
pXmlDom->CreateNode(NODE_ELEMENT, L"MyElement", L"", &pNewChild);  
```  

 Po utworzeniu nowego węzła, należy dodać go jako element podrzędny do innego węzła przez wywołanie elementu nadrzędnego **appendChild** metody.  

### <a name="helper-functions"></a>Funkcje pomocy  

#### <a name="createinstance-template-function"></a>Funkcja CreateInstance szablonu  

```  
HRESULT CreateInstance(IWizardPageContainer *pContainer, LPCTSTR type, I **ppObject)  
```  

 Ta funkcja jest zdefiniowany w IWizardPageContainer.h i udostępnia otokę bezpieczne za pośrednictwem **IWizardPageContainer -> CreateInstance** metoda — na przykład:  

```  
CreateInstance<IDirectory>(Container(), ID_Directory, &pDirectory);  
```  

 Ten kod tworzy nową **ID_Directory** składników do pobrania **IDirectory** interfejsu tego składnika.  

#### <a name="getservice-template-function"></a>Funkcja GetService szablonu  

```  
void GetService(IWizardPageContainer *pContainer, I **ppService)  
```  

 Ta funkcja jest zdefiniowany w IWizardPageContainer.h i udostępnia otokę bezpieczne za pośrednictwem **IWizardPageContainer -> GetService** metoda — na przykład:  

```  
GetService<ITSVariableBag>(Container(), &pTsBag);  
```  

 Ta funkcja pobiera składnika sekwencji zadań, który obsługuje **ITSVariableBag** interfejsu. (Dla **ITSVariableBag**, można użyć metody TSVariables **WizardPageImpl** klasy zamiast.)  

### <a name="udi-wizard-designer-configuration-file-schema-reference"></a>UDI — informacje schematu pliku konfiguracji projektanta Kreatora  
 Ten plik jest używany przez projektanta Kreatora instalacji UDI. Dla każdego pliku DLL niestandardowych, który może zawierać edytory strony kreatora niestandardowego, niestandardowych zadań lub niestandardowych modułów sprawdzania poprawności jest tworzony oddzielny plik. Plik musi się kończyć *.config* i znajdują się w *installation_folder*\Bin\Config folder (gdzie *installation_folder* to folder, w którym jest zainstalowany zestaw MDT).  

  54 tabela zawiera listę elementów w pliku konfiguracji projektanta Kreatora instalacji UDI i ich opisy. **DesignerConfig** element jest węzeł główny dla tego odwołania.  

### <a name="table-54-elements-in-the-udi-wizard-designer-configuration-file-and-their-descriptions"></a>54 tabeli. Elementy w pliku konfiguracji projektanta kreatora UDI i ich opisy  

|**Nazwa elementu**|**Opis**|  
|-|-|  
|[DesignerConfig](#DesignerConfig)|Określa katalog główny dla wszystkich pozostałych elementów|  
|[DesignerMappings](#DesignerMappings)|Zbiór grup [strony](#Page)elementów|  
|[Strona](#Page)|Określa edytor stron kreatora, aby można było załadować projektanta Kreatora instalacji UDI, który jest używany do edytowania ustawień konfiguracyjnych dla strony kreatora|  
|[Param](#Param)|Określa parametr, który jest przekazywany do elementu nadrzędnego [zadań](#Task) lub [modułu sprawdzania poprawności](#Validator) element i odpowiada [metody ustawiającej]() w pliku konfiguracji kreatora UDI **Uwaga:**  Atrybuty dla tego elementu są różne, jeśli element nadrzędny jest [zadań](#Task) lub [modułu sprawdzania poprawności](#Validator) elementu.|  
|[Zadanie](#Task)|Określa, czy zadanie w bibliotece zadań|  
|[TaskItem](#TaskItem)|Określa grupę parametry przekazywane do zadania|  
|[TaskLibrary](#TaskLibrary)|Zbiór grup [zadań](#Task) elementów|  
|[Validator](#Validator)|Określa moduł weryfikacji w bibliotece modułu sprawdzania poprawności|  
|[ValidatorLibrary](#ValidatorLibrary)|Zbiór grup [modułu sprawdzania poprawności](#Validator) elementów|  

####  <a name="DesignerConfig"></a> DesignerConfig  
 Ten element Określa katalog główny dla wszystkich innych elementów.  

##### <a name="element-information"></a>Informacje o elementach  
  55 tabela zawiera informacje na temat [DesignerConfig](#DesignerConfig) elementu.  

### <a name="table-55-designerconfig-element-information"></a>55 tabeli. Informacje o elementach DesignerConfig  

|**Atrybut**|**Wartość**|  
|-|-|  
|Liczba wystąpień|Jeden z nich: Ten element jest wymagany.|  
|Elementy nadrzędne|Brak|  
|Zawartość|**DesignerMappings**, **TaskLibrary**, **ValidatorLibrary**|  

##### <a name="element-attributes"></a>Atrybuty elementu  
 Ten element nie ma żadnych atrybutów.  

##### <a name="remarks"></a>Uwagi  
 Brak.  

##### <a name="example"></a>Przykład  

```  
<DesignerConfig>  
   + <TaskLibrary>  
   + <ValidatorLibrary>  
   + <DesignerMappings>  
</DesignerConfig>  
```  

####  <a name="DesignerMappings"></a> DesignerMappings  
 Ten element grupy zestaw [strony](#Page) elementów.  

##### <a name="element-information"></a>Informacje o elementach  
  56 tabela zawiera informacje na temat [DesignerMappings](#DesignerMappings) elementu.  

### <a name="table-56-designermappings-element-information"></a>56 tabeli. Informacje o elementach DesignerMappings  

|**Atrybut**|**Wartość**|  
|-|-|  
|Liczba wystąpień|Zero lub jeden w ramach [DesignerConfig](#DesignerConfig) elementu (ten element jest opcjonalny, gdy w DLL, która odpowiada ten plik konfiguracji projektanta Kreatora instalacji UDI nie żadnej strony kreatora niestandardowego).|  
|Elementy nadrzędne|**DesignerConfig**|  
|Zawartość|**Strona**|  

##### <a name="element-attributes"></a>Atrybuty elementu  
 Ten element nie ma żadnych atrybutów.  

##### <a name="remarks"></a>Uwagi  
 Brak.  

##### <a name="example"></a>Przykład  

```  
<DesignerConfig>  
   + <TaskLibrary>  
   + <ValidatorLibrary>  
   - <DesignerMappings>  
        <Page DLL="SharedPages.dll"  
           Description="Used to display text that describes the current stagegroup"  
           Type="Microsoft.SharedPages.WelcomePage"  
           DisplayName="Welcome"   
           Image="Welcome_188.png"  
           DesignerType="Microsoft.Enterprise.UDIDesigner.CoreModules.Views.WelcomePageView"  
           DesignerAssembly="Microsoft.Enterprise.UDIDesigner.CoreModules.dll"/>  
        <Page DLL="OSDRefreshWizard.dll"  
           Description="Captures or restores user state data"  
           Type="Microsoft.OSDRefresh.UserStatePage"  
           DisplayName="User Data"  
           Image="UserState_188.png"  
           DesignerType="Microsoft.Enterprise.UDIDesigner.CoreModules.Views.UserStatePageView"  
           DesignerAssembly="Microsoft.Enterprise.UDIDesigner.CoreModules.dll"/>  
        <Page DLL="OSDRefreshWizard.dll"  
           Description="Allows selecting the image to install, target drive, and whether to format"  
           Type="Microsoft.OSDRefresh.VolumePage"  
           DisplayName="Volume"  
           Image="Volume_188.png"  
           DesignerType="Microsoft.Enterprise.UDIDesigner.CoreModules.Views.VolumePageView"  
           DesignerAssembly="Microsoft.Enterprise.UDIDesigner.CoreModules.dll"/>  
     </DesignerMappings>  
</DesignerConfig>  
```  

####  <a name="Page"></a> Strona  
 Ten element Określa edytor stron kreatora, aby można było załadować projektanta Kreatora instalacji UDI, który z kolei jest używany do edytowania ustawień konfiguracyjnych dla strony kreatora.  

##### <a name="element-information"></a>Informacje o elementach  
57 tabela zawiera informacje na temat [strony](#Page) elementu.  

### <a name="table-57-page-element-information"></a>57 tabeli. Informacje o elementach strony  

|**Atrybut**|**Wartość**|  
|-|-|  
|Liczba wystąpień|Co najmniej jedna dla każdej strony kreatora zdefiniowane w [DesignerMappings](#DesignerMappings) — element|  
|Elementy nadrzędne|**DesignerMappings**|  
|Zawartość|Poprawnie sformułowany zawartości XML|  

##### <a name="element-attributes"></a>Atrybuty elementu  
58 tabela zawiera listę atrybutów [strony](#Page) element i opis dla każdego.  

### <a name="table-58-attributes-and-corresponding-values-for-the-page-element"></a>58 tabeli. Atrybuty i wartości dla elementu strony  

|**Atrybut**|**Opis**|  
|-|-|  
|**Opis**|Określa tekst, który zawiera informacje o parametr, który jest wyświetlany w projektanta Kreatora instalacji UDI|  
|**DesignerAssembly**|Określa nazwę pliku DLL skojarzonych z Edytor stron kreatora (plik dll musi istnieć w *installation_folder*\Bin folder (gdzie *installation_folder* to folder, w którym możesz zainstalowanego zestawu MDT.)|  
|**DesignerType**|Określa nazwę Edytor stron kreatora, w ramach określonego w pliku dll **DesignerAssembly** atrybutu (jest to typ platformy Microsoft .NET dla edytorze strony kreatora z przestrzenią nazw FQDN Microsoft .NET).|  
|**DisplayName**|Określa przyjazną dla użytkownika nazwę Edytor stron, która jest wyświetlana w projektanta Kreatora instalacji UDI|  
|**DLL**|Określa nazwę pliku DLL skojarzonych z strony kreatora (plik dll musi istnieć w *installation_folder*\Templates\Distribution\Tools\\*platformy* folder (gdzie *installation_folder* to folder, w którym jest zainstalowany zestaw MDT i *platformy* jest **x86** w 32-bitowej wersji lub **x64** jest w przypadku wersji 64-bit.) **Uwaga:**  Sprawdź, czy biblioteka DLL architektury procesora zgodny architektury procesora zestawu MDT zainstalowane. Na przykład jeśli zainstalowano 32-bitowej wersji zestawu mdt, następnie upewnij się, że używasz 32-bitowa biblioteka dla strony kreatora.|  
|**Obraz**|Określa nazwę obrazu strony, która jest w formacie Portable Network Graphics (PNG) (plik PNG musi istnieć w *installation_folder*\Bin\Images folder (gdzie *installation_folder* jest folder, w którym jest zainstalowany zestaw MDT.)|  
|**Typ**|Określa edytor stron kreatora i musi odpowiadać używany, gdy zarejestrowano niestandardową stronę o nazwie|  

##### <a name="remarks"></a>Uwagi  
 Używa projektanta Kreatora instalacji UDI [strony](#Page) element jako szablonu do utworzenia początkowej XML dla Kreatora nowej. Upewnij się, że sprawdzanie poprawności schematu wykonuje projektanta Kreatora instalacji UDI [strony](#Page) i elementy podrzędne mają prawidłowy format. Ten element zapewnia mapowanie między typ strony kreatora UDI i informacje, które należy edytować i tworzyć strony tego typu za pomocą edytora niestandardowej strony projektanta Kreatora instalacji UDI.  

##### <a name="example"></a>Przykład  
 Brak.  

####  <a name="Param"></a> Param  
 Ten element określa parametr, który jest przekazywany do elementu nadrzędnego [zadań](#Task) lub [modułu sprawdzania poprawności](#Validator) element i odpowiada [metody ustawiającej]() elementu w pliku konfiguracyjnym UDI kreatora.  

> [!NOTE]
>  Atrybuty dla tego elementu są różne, jeśli element nadrzędny jest [zadań](#Task) lub [modułu sprawdzania poprawności](#Validator) elementu.  

##### <a name="element-information"></a>Informacje o elementach  
 59 tabela zawiera informacje na temat [Param](#Param) elementu.  

### <a name="table-59-param-element-information"></a>Tabela 59. Informacje o elementach param  

|**Atrybut**|**Wartość**|  
|-|-|  
|Liczba wystąpień|Co najmniej jeden dla każdego [TaskItem](#TaskItem) lub [modułu sprawdzania poprawności](#Validator) elementu nadrzędnego|  
|Elementy nadrzędne|**TaskItem**, **modułu sprawdzania poprawności**|  
|Zawartość|Poprawnie sformułowany zawartości XML|  

##### <a name="element-attributes"></a>Atrybuty elementu  
  60 tabela zawiera listę atrybutów [Param](#Param) element i zawiera opis każdego z nich.  

### <a name="table-60-attributes-and-corresponding-values-for-the-param-element"></a>60 tabeli. Atrybuty i wartości dla elementu Param  

|**Atrybut**|**Opis**|  
|-|-|  
|**Opis**|Określa tekst, który zawiera informacje o parametr, który jest wyświetlany w projektanta Kreatora instalacji UDI **Uwaga:**  Ten atrybut jest prawidłowy tylko w przypadku [modułu sprawdzania poprawności](#Validator) elementu.|  
|**DisplayName**|Określa przyjazną dla użytkownika nazwę parametru modułu sprawdzania poprawności, która jest wyświetlana na stronie kreatora UDI odpowiednie w projektanta Kreatora instalacji UDI (Ta nazwa jest zazwyczaj bardziej opisowe niż **nazwa** atrybutu.) **Uwaga:**  Ten atrybut jest prawidłowy tylko w przypadku [modułu sprawdzania poprawności](#Validator) elementu.|  
|**Nazwa**|Określa nazwę parametru, który zostanie przekazany do zadania lub modułu sprawdzania poprawności, w zależności od elementu nadrzędnego (tego atrybutu będzie **właściwości** atrybutu w [metody ustawiającej]() elementu w Kreatorze UDI plik konfiguracji.) **Uwaga:**  Ten parametr jest używany zarówno [TaskItem](#TaskItem) i [modułu sprawdzania poprawności](#Validator) elementów nadrzędnych.|  

##### <a name="remarks"></a>Uwagi  
 Brak.  

##### <a name="example"></a>Przykład  
 Brak.  

####  <a name="Task"></a> Zadanie  
 Ten element określa, czy zadanie w bibliotece zadań.  

##### <a name="element-information"></a>Informacje o elementach  
 61 tabela zawiera informacje na temat [zadań](#Task) elementu.  

### <a name="table-61-task-element-information"></a>61 tabeli. Informacje o elementach zadań  

|**Atrybut**|**Wartość**|  
|-|-|  
|Liczba wystąpień|Co najmniej jeden w ramach [TaskLibrary](#TaskLibrary) elementu (ten element nie jest opcjonalny Jeśli **TaskLibrary** określony element.)|  
|Elementy nadrzędne|**TaskLibrary**|  
|Zawartość|**TaskItem**|  

##### <a name="element-attributes"></a>Atrybuty elementu  
  62 tabela zawiera listę atrybutów [zadań](#Task) element i zawiera opis każdego z nich.  

### <a name="table-62-attributes-and-corresponding-values-for-the-task-element"></a>62 tabeli. Atrybuty i wartości dla elementu zadania  

|**Atrybut**|**Opis**|  
|-|-|  
|**Opis**|Określa tekst, który zawiera informacje o zadaniu, która jest wyświetlana w projektanta Kreatora instalacji UDI|  
|**DLL**|Określa nazwę pliku DLL skojarzonych z zadaniem (plik dll musi istnieć w *installation_folder*\Templates\Distribution\Tools\\*platformy* folder (gdzie *installation_folder* to folder, w którym jest zainstalowany zestaw MDT i *platformy* jest **x86** w 32-bitowej wersji lub **x64** 64 -bitowej wersji.)|  
|**Nazwa**|Określa nazwę zadania, które jest wyświetlane w odpowiedniej strony kreatora UDI i projektanta Kreatora instalacji UDI|  
|**Typ**|Określa typ zadania, który jest zarejestrowana rejestr fabryczny, a następnie użyć do wywołania określonych zadań w pliku dll|  

##### <a name="remarks"></a>Uwagi  
 Brak.  

##### <a name="example"></a>Przykład  
 Brak.  

####  <a name="TaskItem"></a> TaskItem  
 Ten element określa grupę parametry przekazywane do zadania.  

##### <a name="element-information"></a>Informacje o elementach  
  63 tabela zawiera informacje na temat [TaskItem](#TaskItem) elementu.  

### <a name="table-63-taskitem-element-information"></a>Tabela 63. Informacje o elementach TaskItem  

|**Atrybut**|**Wartość**|  
|-|-|  
|Liczba wystąpień|Co najmniej jeden dla każdego **zadań** — element|  
|Elementy nadrzędne|**Zadanie**|  
|Zawartość|**Param**|  

##### <a name="element-attributes"></a>Atrybuty elementu  
 64 tabela zawiera listę atrybutów [TaskItem](#TaskItem) element i zawiera opis każdego z nich.  

### <a name="table-64-attribute-and-corresponding-values-for-the-taskitem-element"></a>64 tabeli. Atrybut i odpowiadające im wartości dla elementu TaskItem  

|**Atrybut**|**Opis**|  
|-|-|  
|**Typ**|Określa typu elementu, który zostanie utworzony w pliku konfiguracyjnym UDI kreatora. Zostanie utworzony XML element odpowiada wartości tego atrybutu. Na przykład, jeśli wartość tego atrybutu jest [pliku](#File), a następnie **pliku** będzie można utworzyć elementu w pliku konfiguracyjnym UDI kreatora.<br /><br /> Obecnie są obsługiwane tylko następujące wartości:<br /><br /> -   **Plik**, co wymaga dwóch [Param](#Param) elementy podrzędne (jeden **Param** elementu podrzędnego z **nazwa** ustawić atrybutu **źródła**i innym **Param** elementu podrzędnego z **nazwa** ustawić atrybutu **Dest**)<br />-   [Metoda ustawiająca](), co wymaga **Param** elementu podrzędnego|  

##### <a name="remarks"></a>Uwagi  
 Brak.  

##### <a name="example"></a>Przykład  
 Brak.  

####  <a name="TaskLibrary"></a> TaskLibrary  
 Ten element grupy zestaw [zadań](#Task) elementów.  

##### <a name="element-information"></a>Informacje o elementach  
 65 tabela zawiera informacje na temat [TaskLibrary](#TaskLibrary) elementu.  

### <a name="table-65-tasklibrary-element-information"></a>65 tabeli. Informacje o elementach TaskLibrary  

|**Atrybut**|**Wartość**|  
|-|-|  
|Liczba wystąpień|Zero lub jeden w ramach [DesignerConfig](#DesignerConfig) elementu (ten element jest opcjonalny, jeśli nie ma żadnych niestandardowych zadań w bibliotece DLL odpowiadające ten plik konfiguracji projektanta Kreatora instalacji UDI).|  
|Elementy nadrzędne|**DesignerConfig**|  
|Zawartość|**Zadanie**|  

##### <a name="element-attributes"></a>Atrybuty elementu  
 Ten element nie ma żadnych atrybutów.  

##### <a name="remarks"></a>Uwagi  
 Brak.  

##### <a name="example"></a>Przykład  

```  
<DesignerConfig>  
   - <TaskLibrary>  
        +<Task DLL="" Description="Executes a process with the given command line." Type="Microsoft.Wizard.ShellExecuteTask" Name="Shell Execute Task">  
        +<Task DLL="OSDRefreshWizard.dll" Description="Discovers supported applications for install." Type="Microsoft.OSDRefresh.AppDiscoveryTask" Name="Application Discovery">  
        +<Task DLL="SharedPages.dll" Description="Check to ensure a wired network connection is available." Type="Microsoft.SharedPages.WiredNetworkTask" Name="Wired Network Check">  
        +<Task DLL="OSDRefreshWizard.dll" Description="Check to ensure power source is AC (not battery)." Type="Microsoft.OSDRefresh.ACPowerTask" Name="AC Power Check">  
        +<Task DLL="" Description="Check to ensure power source is AC (not battery)." Type="Microsoft.Wizard.CopyFilesTask" Name="Copy Files Task">  
     </TaskLibrary>  
   + <ValidatorLibrary>  
   + <DesignerMappings>  
</DesignerConfig>  
```  

####  <a name="Validator"></a> Moduł sprawdzania poprawności  
 Ten element Określa moduł weryfikacji w bibliotece modułu sprawdzania poprawności.  

##### <a name="element-information"></a>Informacje o elementach  
 66 tabela zawiera informacje na temat [modułu sprawdzania poprawności](#Validator) elementu.  

### <a name="table-66-validator-element-information"></a>66 tabeli. Informacje o elementach modułu sprawdzania poprawności  

|**Atrybut**|**Wartość**|  
|-|-|  
|Liczba wystąpień|Zero lub więcej w [ValidatorLibrary](#ValidatorLibrary) elementu (ten element jest opcjonalny).|  
|Elementy nadrzędne|**ValidatorLibrary**|  
|Zawartość|**Param**|  

##### <a name="element-attributes"></a>Atrybuty elementu  
67 tabela zawiera listę atrybutów [modułu sprawdzania poprawności](#Validator) element i zawiera opis każdego z nich.  

### <a name="table-67-attributes-and-corresponding-values-for-the-validator-element"></a>Tabela 67. Atrybuty i wartości dla elementu modułu sprawdzania poprawności  

|**Atrybut**|**Opis**|  
|-|-|  
|**Opis**|Określa tekst, który zawiera informacje o modułu sprawdzania poprawności, która jest wyświetlana w projektanta Kreatora instalacji UDI|  
|**DisplayName**|Określa przyjazną dla użytkownika nazwę modułu sprawdzania poprawności wyświetlane w projektanta Kreatora instalacji UDI (Ta nazwa jest zazwyczaj bardziej opisowe niż **nazwa** atrybutu.)|  
|**DLL**|Określa nazwę pliku DLL skojarzonych z modułu sprawdzania poprawności (plik dll musi istnieć w *installation_folder*\Templates\Distribution\Tools\\*platformy* folder (gdzie *installation_folder* to folder, w którym jest zainstalowany zestaw MDT i *platformy* jest **x86** w 32-bitowej wersji lub **x64** w przypadku wersji 64-bit.)|  
|**Nazwa**|Określa nazwę modułu sprawdzania poprawności, która jest wyświetlana w odpowiedniej strony kreatora UDI i projektanta Kreatora instalacji UDI|  
|**Typ**|Określa typ modułu sprawdzania poprawności, która jest zarejestrowana w usłudze Multi-Factor rejestru i używane do wywoływania określonego modułu sprawdzania poprawności w pliku dll|  

##### <a name="remarks"></a>Uwagi  
 Brak.  

##### <a name="example"></a>Przykład  
 Brak.  

####  <a name="ValidatorLibrary"></a> ValidatorLibrary  
 Ten element grupy zestaw [modułu sprawdzania poprawności](#Validator) elementów.  

##### <a name="element-information"></a>Informacje o elementach  
 68 tabela zawiera informacje na temat [ValidatorLibrary](#ValidatorLibrary) elementu.  

### <a name="table-68-validatorlibrary-element-information"></a>68 tabeli. Informacje o elementach ValidatorLibrary  

|**Atrybut**|**Wartość**|  
|-|-|  
|Liczba wystąpień|Zero lub jeden w ramach [DesignerConfig](#DesignerConfig) elementu (ten element jest opcjonalny, jeśli nie ma żadnych niestandardowych modułów sprawdzania poprawności w bibliotece DLL odpowiadające ten plik konfiguracji projektanta Kreatora instalacji UDI).|  
|Elementy nadrzędne|**DesignerConfig**|  
|Zawartość|**Validator**|  

##### <a name="element-attributes"></a>Atrybuty elementu  
 Ten element nie ma żadnych atrybutów.  

##### <a name="remarks"></a>Uwagi  
 Brak.  

##### <a name="example"></a>Przykład  
 < DesignerConfig\> + < TaskLibrary\> -< ValidatorLibrary\> + < DLL modułu sprawdzania poprawności = "" opis "Wymaga tekst w polu" Type="Microsoft.Wizard.Validation.NonEmpty =" Nazwa = "NonEmpty"\> + < DLL modułu sprawdzania poprawności = "" opis = "Nie zezwala na niektórych znaków w polu" Type="Microsoft.Wizard.Validation.InvalidChars" Nazwa = "InvalidChars"\> + < DLL modułu sprawdzania poprawności = "" opis = "Musi występować po wstępnie zdefiniowane wzorzec" typ = " Microsoft.Wizard.Validation.RegEx"Nazwa ="NamedPattern"\> + < DLL modułu sprawdzania poprawności =" "opis"Wymagaj zawartość odpowiada wyrażeniu regularnemu"Type="Microsoft.Wizard.Validation.RegEx = "Nazwa ="Wyrażenie regularne"\> < / ValidatorLibrary\> + < DesignerMappings\>< / DesignerConfig\>  

## <a name="udi-wizard-designer-reference"></a>Kreator UDI — informacje projektanta  

### <a name="controls"></a>Formanty  
 Formanty używane do tworzenia kreatora niestandardowych edytory do użycia w projektanta Kreatora instalacji UDI są WPF **UserControl** wystąpień. 69 tabela zawiera listę formantów, które umożliwia tworzenie edytory strony kreatora niestandardowego.  

### <a name="table-69-controls-that-can-be-used-to-create-custom-wizard-page-editors"></a>69 tabeli. Formanty, które mogą służyć do tworzenia edytory strony kreatora niestandardowego  

|Formant|Opis|  
|-|-|  
|[CollectionTControl](#CollectionTControl)|Ten formant jest używany do edytowania danych przechowywanych w [danych](#Data) w elemencie [strony](#Page) elementu.|  
|[FieldElementControl](#FieldElementControl)|Ten formant jest używany do edytowania pola, które zwykle są połączone do formantu TextBox na stronie .xaml.|  
|[SetterControl](#SetterControl)|Ten formant służy do modyfikowania wartości [metody ustawiającej]() elementu w pliku konfiguracyjnym UDI kreatora.|  

####  <a name="CollectionTControl"></a> CollectionTControl  
 Ten formant zawiera wiele funkcji edytowanie danych. Najlepszy sposób, aby dowiedzieć się, jak użyć tej kontrolki jest spojrzeć na przykładzie pokazano, jak edytowanie danych w obszarze strony **danych** elementu. W szczególności przykładzie przedstawiono sposób dodawania, usuwania i edytowanie elementów w tym formancie.  

####  <a name="FieldElementControl"></a> FieldElementControl  
 Ten formant służy do edytowania pola, które zwykle jest połączone z **pole tekstowe** kontrolki na stronie .xaml.  

##### <a name="example"></a>Przykład  
 Poniższy fragment pliku .xaml ilustruje użycie **FieldElementControl** skonfigurować wartości domyślne dla pola na stronie kreatora, za pomocą elementu podrzędnego **pole tekstowe** sterowania:  

```  
<Controls:FieldElementControl  
Width="450"  
Margin="0,5"  
FieldData="{Binding DataContext.Location, ElementName=ControlRoot}"  
HeaderText="Location Combo Box"  
InstructionText="Here you can configure the behavior of the location combo box."  
HideValidationTab="True">  

<TextBox Text="{Binding FieldData.DefaultValue,  
 UpdateSourceTrigger=PropertyChanged,  
 Mode=TwoWay}"/>  
</Controls:FieldElementControl>  
```  

##### <a name="properties"></a>Właściwości  

###### <a name="fielddata"></a>FieldData  
 Ta właściwość zawiera informacje dotyczące łączenia **FieldElementControl** do źródłowego pliku XML dla pola. Połączenie jest nawiązywane z właściwością interfejs edytora strony. Poniższy fragment pliku .xaml ilustruje użycie **FieldData** właściwości:  

```  
FieldData="{Binding DataContext.Location, ElementName=ControlRoot}"  
```  

 W tym fragmencie wywoływany jest interfejs edytora strony **ControlRoot** i jest określony w **ElementName** parametru. Powiązanie odbywa się na **DataContext.Location** właściwość **ControlRoot** interfejs edytora strony. **Element DataContext** model widoku, który wskazuje [strony](#Page) elementu w pliku konfiguracyjnym UDI kreatora. **Lokalizacja** jest właściwością widoku, który zwraca listę możliwych lokalizacji i jest definiowana za pomocą [danych](#Data) elementu w pliku konfiguracyjnym UDI kreatora. Każda lokalizacja jest definiowana za pomocą [DataItem](#DataItem) elementu w pliku konfiguracyjnym UDI kreatora.  

###### <a name="headertext"></a>Właściwość HeaderText  
 Ta właściwość umożliwia określenie nagłówka [FieldElementControl](#FieldElementControl) formantu. Nagłówek działa jako tytuł dla formantu, jest formatowana jako tekst pogrubienie, pomarańczowy natychmiast wyświetlane nad formantem.  

###### <a name="instructiontext"></a>InstructionText  
 Ta właściwość umożliwia określenie tekst informacyjny dla [FieldElementControl](#FieldElementControl) formantu. Zazwyczaj ten tekst jest używany do można podać krótki opis pola oraz wyjaśniono, jak konfigurowanie pole wpływa na odpowiadające im strony kreatora.  

###### <a name="hideenablebutton"></a>HideEnableButton  
 Ta właściwość logiczna pozwala na kontrolowanie widoczność przycisku, który zmienia stan między **odblokowany** i **zablokowany** (włączona lub wyłączona). Jeśli ustawiono:  

-   **Wartość true,**, nie jest widoczny przycisk  

-   **FALSE**, jest widoczny przycisk (jest to wartość domyślna).  

###### <a name="hidedefaulttab"></a>HideDefaultTab  
 Ta właściwość logiczna pozwala na kontrolowanie widoczność sekcję zawierającą kontrolkę służącą do ustawiania wartości domyślnej. Mimo że właściwość odwołuje się do karty, to ma karty na [FieldElementControl](#FieldElementControl) , ale raczej sekcja, która może być ukryty. Jeśli ustawiono:  

-   **Wartość true,**, sekcji nie jest widoczny  

-   **FALSE**, sekcja jest widoczne (jest to wartość domyślna).  

###### <a name="hideborder"></a>HideBorder  
 Ta właściwość logiczna pozwala na kontrolowanie widoczności obramowania wokół formantu pola. Jeśli ustawiono:  

-   **Wartość true,**, obramowanie nie jest widoczny  

-   **FALSE**, obramowanie jest widoczne (jest to wartość domyślna).  

###### <a name="hideimage"></a>HideImage  
 Ta właściwość logiczna umożliwia kontrolowanie widoczność obrazu, który **FieldImageSource** konfiguruje właściwości. Jeśli ustawiono:  

-   **Wartość true,**, obraz nie jest widoczny  

-   **FALSE**, obraz jest widoczne (jest to wartość domyślna).  

###### <a name="hidevalidationtab"></a>HideValidationTab  
 Ta właściwość logiczna pozwala na kontrolowanie widoczność sekcji, w którym odbywa się na liście modułów weryfikacji. Mimo że właściwość odwołuje się do karty, to ma karty na [FieldElementControl](#FieldElementControl) , ale raczej sekcja, która może być ukryty. Jeśli ustawiono:  

-   **Wartość true,**, sekcji nie jest widoczny  

-   **FALSE**, sekcja jest widoczne (jest to wartość domyślna).  

###### <a name="hidesummarytab"></a>HideSummaryTab  
 Ta właściwość logiczna pozwala na kontrolowanie widoczność sekcji, w którym można skonfigurować nagłówek podsumowania. Podpis i odpowiednią wartość w polu są wyświetlane na **SummaryPage** typ strony kreatora w przepływie etapu. Mimo że właściwość odwołuje się do karty, to ma karty na [FieldElementControl](#FieldElementControl) , ale raczej sekcja, która może być ukryty. Jeśli ustawiono:  

-   **Wartość true,**, sekcji nie jest widoczny  

-   **FALSE**, sekcja jest widoczne (jest to wartość domyślna).  

###### <a name="hidetasksequencetab"></a>HideTaskSequenceTab  
 Ta właściwość logiczna pozwala na kontrolowanie widoczność sekcji, w którym można skonfigurować zmienną sekwencji zadań, która odnosi się do pola. Mimo że właściwość odwołuje się do karty, to ma karty na [FieldElementControl](#FieldElementControl) , ale raczej sekcja, która może być ukryty. Jeśli ustawiono:  

-   **Wartość true,**, sekcji nie jest widoczny  

-   **FALSE**, sekcja jest widoczne (jest to wartość domyślna).  


####  <a name="SetterControl"></a> SetterControl  
 Użyj tego formantu, aby zmodyfikować wartość [metody ustawiającej]() elementu w pliku konfiguracyjnym UDI kreatora. Ten formant zawiera kontrolki podrzędnej można modyfikować wartości **metody ustawiającej** elementu.  

##### <a name="example"></a>Przykład  
 Poniższy fragment pliku .xaml ilustruje użycie **SetterControl** do modyfikowania [metody ustawiającej]() elementu o nazwie **KeyLocationSetter** przy użyciu elementu podrzędnego **Pole tekstowe** formantu.  

```  
<Controls:SetterControl Margin="5"  
        Width="450"  
        HeaderText="Title text"  
        SetterData="{Binding KeyLocationSetter}"   
        InstructionText="What this means…"  
        HorizontalAlignment="Left">  

    <TextBox  
                   Margin="0,3"  
                   Text="{Binding SetterData.SetterValue, Mode=TwoWay, UpdateSourceTrigger=PropertyChanged}"  
    />  

</Controls:SetterControl>  
```  

##### <a name="properties"></a>Właściwości  

###### <a name="setterdata"></a>SetterData  
 Należy powiązać to właściwości widoku lub widok modelu, który łączy do metody ustawiającej. W ten sposób jest podobny do sposobu może powiązać z polem, zgodnie z opisem dla **FieldElementControl**.  

###### <a name="headertext"></a>Właściwość HeaderText  
 Ta właściwość umożliwia ustawienie tekst, który będzie wyświetlany w nagłówku formantu. Tej właściwości należy traktować jako tytuł kontroli. Domyślnie jest widoczny jako pogrubiony tekst pomarańczowy.  

###### <a name="instructiontext"></a>InstructionText  
 Ustaw tą właściwość na tekst, który ma być wyświetlany poniżej nagłówka — zwykle tekst instrukcji, który informuje użytkownika edytora niestandardowego, kiedy i dlaczego dany użytkownik zechce modyfikowanie pola.  

### <a name="interfaces"></a>Interfejsy  
70 tabela zawiera listę interfejsów, które umożliwia tworzenie edytory strony kreatora niestandardowego.  

### <a name="table-70-interfaces-that-can-be-used-to-create-custom-wizard-page-editors"></a>Table 70. Interfejsy, które mogą służyć do tworzenia edytory strony kreatora niestandardowego  

|**Interface**|**Opis**|  
|-|-|  
|[IDataService](#IDataService)|Ten interfejs umożliwia połączenie pól do **danych** elementów w pliku konfiguracyjnym UDI kreatora.|  
|[IMessageBoxService](#IMessageBoxService)|Ten interfejs umożliwia dostęp do metody, które służy do wyświetlenia pola wiadomości.|  

####  <a name="IDataService"></a> IDataService  
 Ten interfejs zawiera kilka właściwości i metody, ale istnieje tylko jedna właściwość, która przypominają będzie potrzebny. Ta właściwość jest tylko jeden opisanych tutaj.  

 Iniekcji zależności umożliwia uzyskiwanie wskaźnika do tego interfejsu przy użyciu kodu następująco w klasie:  

```  
[Dependency]  
public IDataService DataService { get; set; }  
```  

##### <a name="properties"></a>Właściwości  
 71 tabela zawiera listę właściwości **IDataService** interfejsu.  

### <a name="table-71-properties-for-the-idataservice-interface"></a>71 tabeli. Właściwości interfejsu IDataService  

|**Interface**|**Opis**|  
|-|-|  
|[CurrentPage](#CurrentPage)|Ta właściwość zapewnia dostęp do elementów XML, atrybuty i wartości poniżej kontekstu bieżącej strony edytowany w pliku konfiguracyjnym UDI Kreatora|  

######  <a name="CurrentPage"></a> CurrentPage  

```  
XElement CurrentPage { get; set; }  
```  

 Ta właściwość zapewnia dostęp do pliku XML dla bieżącej strony. Nigdy nie należy ustawić tę właściwość, ale można ją zmodyfikowany plik XML dla strony. Edytor stron przykładowych pokazano przykłady modyfikowanie kodu XML. Ta właściwość jest służy głównie w przypadku, gdy masz danych niestandardowych. Wbudowane formantów, zajmowała wszystkie szczegóły można używać pól i właściwości (ustawiające).  

####  <a name="IMessageBoxService"></a> IMessageBoxService  
 Ten interfejs umożliwia dostęp do metody, które służy do wyświetlenia pola wiadomości. Możesz się zastanawiać, czego potrzebujesz interfejsu, aby wyświetlić okno komunikatu. Istnienie jest, że nie chcesz: Firma Microsoft używa tego interfejsu w kodzie, ponieważ jego pomaga pisanie zautomatyzowanych testów dla strony projektanta.  

 Za pomocą następujących metod zapewnia jednak jeden przydatne korzyści: Okna dialogowe zawsze mieć ustawioną wartość kreatora UDI, który zapewnia, że okno dialogowe jest poprawnie zgrupowana za pomocą okna głównego "właściciela".  

 Iniekcji zależności umożliwia uzyskiwanie wskaźnika do tego interfejsu przy użyciu kodu następująco w klasie:  

```  
[Dependency]  
public IMessageBoxService MessageBoxes { get; set; }  
```  

##### <a name="methods"></a>Metody  
 72 tabeli wymieniono metody dla **IMessageBoxService** interfejsu.  

### <a name="table-72-methods-for-the-imessageboxservice-interface"></a>72 tabeli. Metody interfejsu IMessageBoxService  

|**— Metoda**|**Opis**|  
|-|-|  
|[ShowMessageBox](#ShowMessageBox)|Tej przeciążonej metody służy do wyświetlenia pola wiadomości z następujących członków:<br /><br /> -   [ShowMessageBox (ciąg komunikatu, podpis ciąg, ikonę MessageBoxImage)](#ShowMessageBox_Stringmessage_Stringcaption_MessageBoxImage_icon)<br />-   [ShowMessageBox (ciąg komunikatu, ciąg podpis, przycisk MessageBoxButton, ikona MessageBoxImage)](#ShowMessageBox_stringmessage_stringcaption_MessageBoxButtonbutton_MessageBoxImage_icon)<br />-   [ShowMessageBox (wyjątek wyjątek)](#ShowMessageBox_Exception_exception)|  
|[ShowDialogWindow](#ShowDialogWindow)|Ta metoda umożliwia utworzenie nowego okna dialogowego.|  
|[ShowWizardWindow](#ShowWizardWindow)|Ta metoda służy do wyświetlania niestandardowego edytora wewnątrz okno dialogowe, które zawiera **dalej** i **ponownie** przycisków nawigacji.|  

######  <a name="ShowMessageBox"></a> ShowMessageBox  
 Ta metoda wyświetla komunikat, który jest elementem podrzędnym Edytor stron kreatora niestandardowego. Ten element członkowski jest przeciążony: 73 tabela zawiera listę elementów członkowskich i krótki opis każdego z nich. Aby uzyskać pełne informacje dotyczące każdego elementu członkowskiego (wraz ze składnią, użycia i przykłady) zobacz sekcję umożliwiająca każdy element członkowski.  

### <a name="table-73-overloaded-members-for-the-showmessagbox-method"></a>73 tabeli. Przeciążone elementy członkowskie dla metody ShowMessagBox  

|Element członkowski|Opis|  
|-|-|  
|[ShowMessageBox (ciąg komunikatu, podpis ciąg, ikonę MessageBoxImage)](#ShowMessageBox_Stringmessage_Stringcaption_MessageBoxImage_icon)|Wyświetla komunikat z ikoną i **OK** przycisku|  
|[ShowMessageBox (ciąg komunikatu, ciąg podpis, przycisk MessageBoxButton, ikona MessageBoxImage)](#ShowMessageBox_stringmessage_stringcaption_MessageBoxButtonbutton_MessageBoxImage_icon)|Wyświetla okno z ikony, jak i różnych możliwych kombinacji przycisków|  
|[ShowMessageBox (wyjątek wyjątek)](#ShowMessageBox_Exception_exception)|Wyświetla komunikat zawiera informacje o wyjątku, który ma **OK** przycisku|  

######  <a name="ShowMessageBox_Stringmessage_Stringcaption_MessageBoxImage_icon"></a> ShowMessageBox (ciąg komunikatu, podpis ciąg, ikonę MessageBoxImage)  

```  
void ShowMessageBox(String message, String caption, MessageBoxImage icon);  
```  

 Ta metoda Wyświetla okno z **OK** przycisku. Zobacz 74 tabeli.  

### <a name="table-74-parameters-for-the-showmessageboxstring-message-string-caption-messageboximage-icon-method"></a>74 tabeli. Parametry dla metody ShowMessageBox(String message, String caption, MessageBoxImage icon)  

|**Parametr**|**Opis**|  
|-|-|  
|**Komunikat**|Komunikat wyświetlany w obszarze zawartości okna komunikatu|  
|**Podpis**|Tekst wyświetlany w pasku tytułu okna dialogowego|  
|**icon**|Typ ikonę do wyświetlenia w oknie komunikatu|  

######  <a name="ShowMessageBox_stringmessage_stringcaption_MessageBoxButtonbutton_MessageBoxImage_icon"></a> ShowMessageBox (ciąg komunikatu, ciąg podpis, przycisk MessageBoxButton, ikona MessageBoxImage)  

```  
MessageBoxResult ShowMessageBox(string message, string caption, MessageBoxButton button, MessageBoxImage icon);  
```  

 Ta metoda Wyświetla okno z zestaw przycisków, które mają być pokazywane i raportów, które zostanie kliknięty przycisk. Zobacz 75 tabeli.  

### <a name="table-75-parameters-for-the-showmessageboxstring-message-string-caption-messageboxbutton-button-messageboximage-icon-method"></a>75 tabeli. Parametry dla metody ShowMessageBox(string message, string caption, MessageBoxButton button, MessageBoxImage icon)  

|**Parametr**|**Opis**|  
|-|-|  
|**Komunikat**|Komunikat wyświetlany w obszarze zawartości okna komunikatu|  
|**Podpis**|Tekst wyświetlany w pasku tytułu okna dialogowego|  
|**button**|Wyświetlane przyciski|  
|**icon**|Typ ikonę do wyświetlenia w oknie komunikatu|  

######  <a name="ShowMessageBox_Exception_exception"></a> ShowMessageBox (wyjątek wyjątek)  

```  
void ShowMessageBox(Exception exception);  
```  

 Ta metoda wyświetla komunikat, który zgłasza informacje o wyjątku. Ten komunikat ma jeden **OK** przycisku. Zobacz 76 tabeli.  

### <a name="table-76-parameters-for-the-showmessageboxexception-exception-method"></a>76 tabeli. Parametry dla metody ShowMessageBox(Exception exception)  

|**Parametr**|**Opis**|  
|-|-|  
|**Wyjątek**|Wyjątek, który chcesz zgłosić (korzysta z okna dialogowego **wyjątku. Komunikat** jako zawartość.)|  

######  <a name="ShowDialogWindow"></a> ShowDialogWindow  

```  
void ShowDialogWindow(Type viewType, DialogInteraction dialogPayload);  
```  

 Ta metoda tworzy nowe okno dialogowe, zawartość, w których jest wyświetlany tekst podanych w **viewType** parametru. Projektant UDI tworzy nowe wystąpienie tego typu i koduje go w oknie dialogowym, które ma **OK** i **anulować** przycisków.  

 Przekazywanie danych do formantu przy użyciu parametru dialogPayload. **SampleEditor** rozwiązania w katalogu zestawu SDK zawiera przykładowy sposób używać tej funkcji.  

######  <a name="ShowWizardWindow"></a> ShowWizardWindow  

```  
void ShowWizardWindow(Type viewType, DialogInteraction dialogPayload);  
```  

 Ta metoda umożliwia wyświetlanie niestandardowego edytora wewnątrz okno dialogowe, które zawiera **dalej** i **ponownie** przycisków nawigacji. Firma Microsoft nie udostępnia przykład sposobu używania tej metody.  

###  <a name="UDIWizardConfigurationFileSchemaReference"></a> UDI — informacje schematu pliku konfiguracji kreatora  
 Ten plik jest używane przez kreatora UDI i konfigurowane za pomocą projektanta Kreatora instalacji UDI. Ten plik jest używany do konfigurowania:  

-   Wyświetlany w Kreatorze UDI strony kreatora  

-   Sekwencja na stronach kreatora, w Kreatorze UDI  

-   Ustawienia dla pól na każdej stronie kreatora  

-   Dostępne StageGroups w projektanta Kreatora instalacji UDI  

-   Etapach dostępny w ramach każdego Kreatora wdrażania w projektanta Kreatora instalacji UDI  

  77 zawiera listę elementów w pliku konfiguracji kreatora UDI i ich opisy. **Kreatora** element jest węzeł główny dla tego odwołania.  

### <a name="table-77-elements-in-the-udi-wizard-configuration-file-and-their-descriptions"></a>77 tabeli. Elementy w pliku konfiguracji kreatora UDI i ich opisy  

|**Nazwa elementu**|**Opis**|  
|-|-|  
|[Dane](#Data)|Grupuje poszczególne [DataItem](#DataItem) elementów w obrębie [strony](#Page) element i nosi nazwę przez **nazwa** atrybutu.|  
|[DataItem](#DataItem)|Grupuje poszczególne [metody ustawiającej]() elementów w obrębie [strony](#Page) elementu. Hierarchiczne dane można utworzyć, umieszczając w niej co najmniej jeden [danych](#Data) elementów w obrębie [DataItem](#DataItem) elementu. Każdy **DataItem** element reprezentuje pojedynczy element. Na przykład listę dostępnych dysków może być **DataItem** nazwę wyświetlaną i inny **DataItem** elementu dla odpowiedniego literę dysku.|  
|[Domyślny](#Default)|Określa wartość domyślną w polu określonym w obiekcie nadrzędnym [pola](#Field) lub [RadioGroup](#RadioGroup) elementu. Wartość domyślna ma ustawioną wartość oddzielona przez ten element.|  
|[DLL](#DLL)|Określa bibliotekę DLL, która ma być załadowany i odwołuje się Kreator UDI i projektanta Kreatora instalacji UDI.|  
|[Biblioteki dll](#DLLs)|Grupuje poszczególne [DLL](#DLL) elementów.|  
|[Błąd](#Error)|Określa, że może zwrócić kod może zawierać błąd, który można zadania. Wartość kodu błędu, jest zwracana w zadaniu **HRESULT** i jest to spowodowane ten element, aby zapewnić bardziej szczegółowe informacje o błędzie.|  
|[ExitCode](#ExitCode)|Określa kod możliwe zakończenia zadania. Kody zakończenia są kody powrotu, które zadania oczekuje. Utwórz **ExitCode** elementu każdy kod zakończenia to możliwe. W przeciwnym razie można określić znak gwiazdki (\*) w **wartość** atrybut do obsługi niewymienione w innych kodów powrotnych **ExitCode** elementów.|  
|[ExitCodes](#ExitCodes)|Zbiór grup [ExitCode](#ExitCode) i [błąd](#Error) elementy [zadań](#Task) element lub **błąd** elementu.|  
|[Pole](#Field)|Określa wystąpienie formantu w [strony](#Page) element, który służy do zapewnienia dostosowania XML. Nie wszystkie formanty można dostosowywać za pomocą XML — tylko formanty używające [pola](#Field) elementu.|  
|[Pola](#Fields)|Grupuje poszczególne [pola](#Field) elementów w obrębie [strony](#Page) elementu.|  
|[Plik](#File)|Określa źródło i miejsce docelowe using operacji kopiowania pliku **Microsoft.Wizard.CopyFilesTask** typ zadania. Mogą zawierać osobne **pliku** element, aby skopiować więcej niż jeden plik w jednym zadaniu.|  
|[Strona](#Page)|Określa wystąpienie strony i zawiera wszystkie ustawienia konfiguracji dla strony.|  
|[PageRef](#PageRef)|Określa odwołania do wystąpienia strony [etap](#Stage) w [StageGroup](#StageGroup).|  
|[Strony](#Pages)|Grupuje poszczególne [strony](#Page) elementów.|  
|[RadioGroup](#RadioGroup)|Grupa przycisków radiowych w [pola](#Field) elementu.|  
|[StageGroup](#StageGroup)|Określa grupę co najmniej jeden etapach.|  
|[StageGroups](#StageGroups)|Grupuje zestaw grup etap w pliku konfiguracji kreatora UDI.|  
|[Metody ustawiającej]()|Określa ustawienia właściwości wartości dla właściwości o nazwie w **właściwości** właściwości.|  
|[Etap](#Stage)|Określa etap w [StageGroup](#StageGroup) i zawiera co najmniej jeden [PageRef](#PageRef) elementów.|  
|[Styl](#Style)|Grupuje poszczególne [metody ustawiającej]() elementów, które skonfigurować kreatora UDI wyglądu i działania, łącznie z tytułu wyświetlaną u góry kreatora i transparent obraz wyświetlany w Kreatorze UDI.|  
|[Zadanie](#Task)|Określa zadanie, które ma być uruchamiane na stronie określony w obiekcie nadrzędnym [strony](#Page) elementu.|  
|[Zadania](#Tasks)|Grupy zadań dla [strony](#Page) elementu.|  
|[Validator](#Validator)|Określa moduł weryfikacji dla formantu pole, który jest określony w obiekcie nadrzędnym [pola](#Field) elementu.|  
|[Kreator](#Wizard)|Określa katalog główny dla wszystkich innych elementów.|  

####  <a name="Data"></a> Dane  
 Ten element grupuje poszczególne [DataItem](#DataItem) elementów w obrębie [strony](#Page) element i nosi nazwę przez **nazwa** atrybutu.  

##### <a name="element-information"></a>Informacje o elementach  
78 tabela zawiera informacje na temat [danych](#Data) elementu.  

### <a name="table-78-data-element-information"></a>78 tabeli. Element danych  

|**Atrybut**|**Wartość**|  
|-|-|  
|Liczba wystąpień|Zero lub więcej w ramach każdej [strony](#Page) elementu (ten element jest opcjonalny).|  
|Elementy nadrzędne|**Strona**, **DataItem**|  
|Zawartość|**DataItem**, **metody ustawiającej**|  

##### <a name="element-attributes"></a>Atrybuty elementu  
 79 tabela zawiera listę atrybutów [danych](#Data) element i zawiera opis każdego z nich.  

### <a name="table-79-attributes-and-corresponding-values-for-the-data-element"></a>79 tabeli. Atrybuty i wartości elementu danych  

|**Atrybut**|**Opis**|  
|-|-|  
|**Nazwa**|Określa nazwę [danych](#Data) — element|  

##### <a name="remarks"></a>Uwagi  
 **Nazwa** atrybutu umożliwia kod, aby pobrać określony zestaw danych.  

##### <a name="example"></a>Przykład  
 Brak.  

####  <a name="DataItem"></a> Element danych  
 Ten element grupuje poszczególne [metody ustawiającej]() elementów w obrębie [strony](#Page) elementu. Hierarchiczne dane można utworzyć, umieszczając w niej co najmniej jeden [danych](#Data) elementów w obrębie [DataItem](#DataItem) elementu. Każdy **DataItem** element reprezentuje pojedynczy element. Na przykład listę dostępnych dysków może być **DataItem** nazwę wyświetlaną i inny **DataItem** elementu dla odpowiedniego literę dysku.  

##### <a name="element-information"></a>Informacje o elementach  
 80 tabela zawiera informacje na temat [DataItem](#DataItem) elementu.  

### <a name="table-80-dataitem-element-information"></a>Table 80. Informacje o elementach DataItem  

|**Atrybut**|**Wartość**|  
|-|-|  
|Liczba wystąpień|Zero lub więcej w ramach każdej [danych](#Data) elementu (ten element jest opcjonalny).|  
|Elementy nadrzędne|**Dane**|  
|Zawartość|**Dane**, **metody ustawiającej**|  

##### <a name="element-attributes"></a>Atrybuty elementu  
 Ten element nie ma żadnych atrybutów.  

##### <a name="remarks"></a>Uwagi  
 Brak.  

##### <a name="example"></a>Przykład  
 Brak.  

#### <a name="default"></a>Domyślny  
 Ten element określa wartość domyślną w polu określonym w obiekcie nadrzędnym [pola](#Field) lub [RadioGroup](#RadioGroup) elementu. Wartość domyślna jest ustawiona na wartość tego elementu w nawiasach kwadratowych.  

##### <a name="element-information"></a>Informacje o elementach  
81 tabela zawiera informacje na temat [domyślne](#Default) elementu.  

### <a name="table-81-default-element-information"></a>81 tabeli. Informacje o elementach domyślne  

|**Atrybut**|**Wartość**|  
|-|-|  
|Liczba wystąpień |Zero lub więcej w [pola](#Field) lub [RadioGroup](#RadioGroup) elementu (ten element jest opcjonalny).|  
|Elementy nadrzędne|**Pole**, **RadioGroup**|  
|Zawartość|Może być dowolnym poprawnie sformułowany plik XML zawartości, ale jest zwykle standardowego tekstu|  

##### <a name="element-attributes"></a>Atrybuty elementu  
 Ten element nie ma żadnych atrybutów.  

##### <a name="remarks"></a>Uwagi  
 Brak.  

##### <a name="example"></a>Przykład  
 W poniższym przykładzie, wartością domyślną **strefy czasowej** pole jest ustawione na "Czas pacyficzny":  

```  
<Field Name="TimeZone" Enabled="true" VarName="OSDTimeZone" Summary="Time Zone:">  
  <Default>Pacific Standard Time</Default>  
```  

####  <a name="DLL"></a> DLL  
 Ten element Określa bibliotekę DLL UDI kreatora i projektanta Kreatora instalacji UDI do ładowania i odwołania.  

##### <a name="element-information"></a>Informacje o elementach  
82 tabela zawiera informacje na temat [DLL](#DLL) elementu.  

### <a name="table-82-dll-element-information"></a>82 tabeli. Informacje o elementach biblioteki DLL  

|**Atrybut**|**Wartość**|  
|-|-|  
|Liczba wystąpień|Co najmniej jeden w ramach [biblioteki dll](#DLLs) — element|  
|Element nadrzędny|**Biblioteki dll**|  
|Zawartość|Brak zawartości dozwolone dla tego elementu|  

##### <a name="element-attributes"></a>Atrybuty elementu  
 83 tabela zawiera listę atrybutów [DLL](#DLL) element i zawiera opis każdego z nich.  

### <a name="table-83-attributes-and-corresponding-values-for-the-dll-element"></a>83 tabeli. Atrybuty i wartości dla elementu biblioteki DLL  

|**Atrybut**|**Opis**|  
|-|-|  
|Nazwa|Określa nazwę UDI kreatora i projektanta Kreatora instalacji UDI odwołanie do biblioteki dll|  

##### <a name="remarks"></a>Uwagi  
 Brak.  

##### <a name="example"></a>Przykład  

```  
<DLLs>  
  <DLL Name="OSDRefreshWizard.dll" />   
  <DLL Name="SharedPages.dll" />  
</DLLs>  
```  

####  <a name="DLLs"></a> Biblioteki dll  
 Ten element grupuje poszczególne [DLL](#DLL) elementów.  

##### <a name="element-information"></a>Informacje o elementach  
84 tabela zawiera informacje na temat [biblioteki dll](#DLLs) elementu.  

### <a name="table-84-dlls-element-information"></a>84 tabeli. Informacje o elementach biblioteki dll  

|**Atrybut**|**Wartość**|  
|-|-|  
|Liczba wystąpień|jeden|  
|Elementy nadrzędne|**Kreator**|  
|Zawartość|**DLL**|  

##### <a name="element-attributes"></a>Atrybuty elementu  
 Ten element nie ma żadnych atrybutów.  

##### <a name="remarks"></a>Uwagi  
 Brak.  

##### <a name="example"></a>Przykład  

```  
<DLLs>  
   <DLL Name="OSDRefreshWizard.dll" />  
   <DLL Name="SharedPages.dll" />   
</DLLs>  
```  

####  <a name="Error"></a> Błąd  
 Ten element określa zadania mogą zwracać kod może zawierać błąd. Wartość kodu błędu został zwrócony, a to spowodowane zadania **HRESULT** zapewnienie bardziej szczegółowe informacje o błędzie.  

##### <a name="element-information"></a>Informacje o elementach  
 85 tabela zawiera informacje na temat [błąd](#Error) elementu.  

### <a name="table-85-error-element-information"></a>85 tabeli. Informacje o błędzie — Element  

|**Atrybut**|**Wartość**|  
|-|-|  
|Liczba wystąpień|Zero lub więcej w ramach każdej [ExitCode](#ExitCode) elementu (ten element jest opcjonalny).|  
|Elementy nadrzędne|**ExitCodes**|  
|Zawartość|Poprawnie sformułowany zawartości XML|  

##### <a name="element-attributes"></a>Atrybuty elementu  
 86 tabela zawiera listę atrybutów [błąd](#Error) element i zawiera opis każdego z nich.  

###  

|**Atrybut**|**Opis**|  
|-|-|  
|**Stan**|Określa zwracany stan zadań, który wystąpił błąd. Zwykle wartość tego atrybutu jest ustawiana na błąd. Ta wartość jest wyświetlana w **stanu** kolumn na stronie kreatora w Kreatorze UDI.|  
|**Text**|Określa tekst opisujący warunek błędu, który napotkano zadania.|  
|**Typ**|Określa, czy ten element reprezentuje błąd, ostrzeżenie lub Powodzenie. Wartość określona w**typu** muszą być unikatowe w obrębie [ExitCodes](#ExitCodes) elementu. Poniżej przedstawiono prawidłowe wartości dla tego elementu:<br /><br /> -   **0.**ten element reprezentuje sukcesu.<br />-   **1.** Ten element reprezentuje ostrzeżenie.<br />-   **-1.** Ten element reprezentuje wystąpił błąd.|  
|**Wartość**|Określa wartość kodu, który zwrócił zadania jako wartość liczbową. Określa wartość znak gwiazdki (*) wskazuje domyślny element dla kody powrotu, które nie są wymienione w innych [błąd](#Error) elementów.|  

##### <a name="remarks"></a>Uwagi  
 Brak.  

##### <a name="example"></a>Przykład  
 Brak.  

####  <a name="ExitCode"></a> ExitCode  
 Ten element określa kod możliwe zakończenia zadania. Kody zakończenia są kody powrotu, które zadania oczekuje. Utwórz **ExitCode** elementu każdy kod zakończenia to możliwe. W przeciwnym razie można określić znak gwiazdki (\*) w **wartość** atrybut do obsługi niewymienione w innych kodów powrotnych **ExitCode** elementów.  

##### <a name="element-information"></a>Informacje o elementach  
87 tabela zawiera informacje na temat [ExitCode](#ExitCode) elementu.  

### <a name="table-87-exitcode-element-information"></a>87 tabeli. Informacje o elementach ExitCode  

|**Atrybut**|**Wartość**|  
|-|-|  
|Liczba wystąpień|Zero lub więcej w ramach każdej [ExitCodes](#ExitCodes) elementu (ten element jest opcjonalny).|  
|Elementy nadrzędne|**ExitCodes**|  
|Zawartość|Co najmniej jeden [ExitCode](#ExitCode) element i zero lub więcej [błąd](#Error) elementów|  

##### <a name="element-attributes"></a>Atrybuty elementu  
88 tabela zawiera listę atrybutów [ExitCode](#ExitCode) element i zawiera opis każdego z nich.  

### <a name="table-88-attributes-and-corresponding-values-for-the-exitcode-element"></a>88 tabeli. Atrybuty i wartości dla elementu ExitCode  

|**Atrybut**|Opis|  
|-|-|  
|**Stan**|Określa zwracany stan zadania. Wartość tego atrybutu będzie wyświetlana w **stanu** kolumn na stronie kreatora w Kreatorze UDI. Można użyć wartości dla tego atrybutu zrozumiały dla zadania. Poniżej przedstawiono typowe wartości używane dla tego atrybutu:<br /><br /> — Powodzenie<br />— Ostrzeżenie<br />— Błąd|  
|**Text**|Określa tekst opisowy o kodzie istnieją zadania.|  
|**Typ**|Określa, czy ten element reprezentuje błąd, ostrzeżenie lub Powodzenie. Wartość określona w typie muszą być unikatowe w obrębie [ExitCodes](#ExitCodes) elementu. Poniżej przedstawiono prawidłowe wartości dla tego elementu:<br /><br /> -   **0.** Ten element reprezentuje sukcesu.<br />-   **1.** Ten element reprezentuje ostrzeżenie.<br />-   **-1.** Ten element reprezentuje wystąpił błąd.|  
|**Wartość**|Określa wartość kodu, który zwrócił zadania jako wartość liczbową. Określa wartość znak gwiazdki (*) wskazuje domyślny element dla kody powrotu, które nie są wymienione w innych [ExitCode](#ExitCode) elementów.|  

##### <a name="remarks"></a>Uwagi  
 Brak.  

##### <a name="example"></a>Przykład  
 Brak.  

####  <a name="ExitCodes"></a> ExitCodes  
 Ten element grupy zestaw [ExitCode](#ExitCode) i [błąd](#Error) elementy [zadań](#Task) lub **błąd** elementu.  

##### <a name="element-information"></a>Informacje o elementach  
89 tabela zawiera informacje na temat [ExitCodes](#ExitCodes) elementu.  

### <a name="table-89-exitcodes-element-information"></a>89 tabeli. Informacje o elementach ExitCodes  

|**Atrybut**|**Wartość**|  
|-|-|  
|Liczba wystąpień|W każdym [zadań](#Task) — element|  
|Elementy nadrzędne|**Zadanie**|  
|Zawartość|**Błąd**, **ExitCode**|  

##### <a name="element-attributes"></a>Atrybuty elementu  
 Ten element nie ma żadnych atrybutów.  

##### <a name="remarks"></a>Uwagi  
 Brak.  

##### <a name="example"></a>Przykład  
 Brak.  

####  <a name="Field"></a> Pole  
 Ten element określa wystąpienie formantu w [strony](#Page) element umożliwiające dostosowywanie XML. Nie wszystkie formanty można dostosowywać za pomocą XML — tylko formanty używające [pola](#Field) elementu.  

##### <a name="element-information"></a>Informacje o elementach  
 90 tabela zawiera informacje na temat [pola](#Field) elementu.  

### <a name="table-90-field-element-information"></a>Tabela 90. Informacje o elementach pola  

|**Atrybut**|**Wartość**|  
|-|-|  
|Liczba wystąpień|Zero lub więcej w ramach każdej [pola](#Field) elementu (ten element jest opcjonalny).|  
|Elementy nadrzędne|**Pola**|  
|Zawartość|**Domyślna**, **modułu sprawdzania poprawności**|  

##### <a name="element-attributes"></a>Atrybuty elementu  
91 tabela zawiera listę atrybutów [pola](#Field) element i zawiera opis każdego z nich.  

### <a name="table-91-attributes-and-corresponding-values-for-the-field-element"></a>91 tabeli. Atrybuty i wartości dla pola elementu  

|**Atrybut**|**Opis**|  
|-|-|  
|**włączone**|Określa, czy pole jest włączone dla użytkownika danych wejściowych (atrybut może zostać ustawiony na wartość True lub False.)|  
|**Nazwa**|Określa nazwę pola|  
|**Podsumowanie**|Określa opis wyświetlany na **Podsumowanie** strony kreatora o wartości, który ustawia tego pola|  
|**Nazwa_zmiennej**|Określa nazwy zmiennej sekwencji zadań do odczytu lub skonfigurowany za pomocą pola w obiekcie nadrzędnym [pola](#Field) — element|  

##### <a name="remarks"></a>Uwagi  
 Ten element może zawierać zero lub więcej [domyślne](#Default) elementów i zero lub więcej [modułu sprawdzania poprawności](#Validator) elementów.  

##### <a name="example"></a>Przykład  
 Brak.  

####  <a name="Fields"></a> Pola  
 Ten element grupuje poszczególne [pola](#Field) elementów w obrębie [strony](#Page) elementu.  

##### <a name="element-information"></a>Informacje o elementach  
92 tabela zawiera informacje na temat [pola](#Fields) elementu.  

### <a name="table-92-fields-element-information"></a>92 tabeli. Informacje o elementach pola  

|**Atrybut**|**Wartość**|  
|-|-|  
|Liczba wystąpień|Zero lub więcej w ramach każdej [strony](#Page) elementu (ten element jest opcjonalny).|  
|Elementy nadrzędne|**Strona**|  
|Zawartość|**Pole**, **RadioGroup**|  

##### <a name="element-attributes"></a>Atrybuty elementu  
 Ten element nie ma żadnych atrybutów.  

##### <a name="remarks"></a>Uwagi  
 Brak.  

##### <a name="example"></a>Przykład  
 Brak.  

####  <a name="File"></a> Plik  
 Ten element Określa źródło i miejsce docelowe using operacji kopiowania pliku **Microsoft.Wizard.CopyFilesTask** typ zadania. Mogą zawierać osobne [pliku](#File) element, aby skopiować więcej niż jeden plik w jednym zadaniu.  

##### <a name="element-information"></a>Informacje o elementach  
 93 tabela zawiera informacje na temat [pliku](#File) elementu.  

### <a name="table-93-file-element-information"></a>93 tabeli. Informacje o elementach pliku  

|**Atrybut**|**Wartość**|  
|-|-|  
|Liczba wystąpień|Co najmniej jeden dla każdego zadania, który ma typ zadania **Microsoft.Wizard.CopyFilesTask**|  
|Elementy nadrzędne|**Zadanie**|  
|Zawartość|Brak|  

##### <a name="element-attributes"></a>Atrybuty elementu  
 94 tabela zawiera listę atrybutów [pliku](#File) element i zawiera opis każdego z nich.  

### <a name="table-94-attributes-and-corresponding-values-for-the-file-element"></a>94 tabeli. Atrybuty i wartości dla elementu pliku  

|**Atrybut**|**Opis**|  
|-|-|  
|**Docelowy**|Określa w pełni kwalifikowaną lub względną ścieżkę do folderu docelowego dla określonego w pliku **źródła** atrybutu. Zmienne środowiskowe są dozwolone jako części ścieżki.|  
|**Obiekt źródłowy**|Określa w pełni kwalifikowaną lub względną ścieżkę do źródła plików, który **Microsoft.Wizard.CopyFilesTask** zadań kopii typu. Ten atrybut obsługuje znaki symboli wieloznacznych, dzięki czemu można skopiować wielu plików przy użyciu pojedynczej [pliku](#File) elementu. Zmienne środowiskowe są dozwolone jako części ścieżki.|  

##### <a name="remarks"></a>Uwagi  
 Brak.  

##### <a name="example"></a>Przykład  
 Brak.  

####  <a name="PageElement"></a> Strona  
 Ten element określa wystąpienie strony i zawiera wszystkie ustawienia konfiguracji dla strony.  

##### <a name="element-information"></a>Informacje o elementach  
95 tabela zawiera informacje na temat [strony](#Page) elementu.  

### <a name="table-95-page-element-information"></a>95 tabeli. Informacje o elementach strony  

|**Atrybut**|**Wartość**|  
|-|-|  
|Liczba wystąpień|Co najmniej jeden w każdym [stron](#Pages) — element|  
|Elementy nadrzędne|**Strony**|  
|Zawartość|**Dane**, **pola**, **metody ustawiającej**, **zadań**|  

##### <a name="element-attributes"></a>Atrybuty elementu  
96 tabela zawiera listę atrybutów [strony](#Page) element i zawiera opis każdego z nich.  

### <a name="table-96-attributes-and-corresponding-values-for-the-page-element"></a>96 tabeli. Atrybuty i wartości dla elementu strony  

|**Atrybut**|**Opis**|  
|-|-|  
|**DisplayName**|Określa przyjazną dla użytkownika nazwa wyświetlana w projektanta Kreatora instalacji UDI strony kreatora. Ta nazwa jest zazwyczaj bardziej opisowe niż **nazwa** atrybutu.|  
|**Nazwa**|Nazwa wyświetlana w projektanta Kreatora instalacji UDI strony kreatora.|  
|**Typ**|Określa typ strony kreatora, który bezpośrednio odnosi się do strony kreatora określonej biblioteki DLL.|  

##### <a name="remarks"></a>Uwagi  
 Brak.  

##### <a name="example"></a>Przykład  
 Brak.  

####  <a name="PageRef"></a> PageRef  
 Ten element określa odwołania do wystąpienia strony [etap](#Stage) w [StageGroup](#StageGroup).  

##### <a name="element-information"></a>Informacje o elementach  
97 tabela zawiera informacje na temat [PageRef](#PageRef) elementu.  

### <a name="table-97-pageref-element-information"></a>97 tabeli. Informacje o elementach PageRef  

|**Atrybut**|**Wartość**|  
|-|-|  
|Liczba wystąpień|Co najmniej jeden w ramach [etap](#Stage) — element|  
|Elementy nadrzędne|**Etap**|  
|Zawartość|Brak|  

##### <a name="element-attributes"></a>Atrybuty elementu  
98 tabeli wymieniono atrybut [PageRef](#PageRef) element i zawiera jego opis.  

### <a name="table-98-attributes-and-corresponding-values-for-the-pageref-element"></a>98 tabeli. Atrybuty i wartości dla elementu PageRef  

|**Atrybut**|**Opis**|  
|-|-|  
|**Strona**|Określa wystąpienie strony [etap](#Stage) w [StageGroup](#StageGroup). Ta wartość atrybutu Name [strony](#Page) elementu.|  

##### <a name="remarks"></a>Uwagi  
 Brak.  

##### <a name="example"></a>Przykład  
 Brak.  

####  <a name="Pages"></a> Strony  
 Ten element grupuje poszczególne [strony](#Page) elementów.  

##### <a name="element-information"></a>Informacje o elementach  
99 tabela zawiera informacje na temat [stron](#Pages) elementu.  

### <a name="table-99-pages-element-information"></a>Tabela 99. Informacje o elementach stron  

|**Atrybut**|**Wartość**|  
|-|-|  
|Liczba wystąpień|jeden|  
|Elementy nadrzędne|**Kreator**|  
|Zawartość|**Strona**|  

##### <a name="element-attributes"></a>Atrybuty elementu  
 Ten element nie ma żadnych atrybutów.  

##### <a name="remarks"></a>Uwagi  
 Brak.  

##### <a name="example"></a>Przykład  

```  
<Pages>  
   + <Page Name="WelcomePage" DisplayName="Welcome" Type="Microsoft.SharedPages.WelcomePage">  
   + <Page Name="ConfigScanPage" DisplayName="Deployment Readiness" Type="Microsoft.OSDRefresh.ConfigScanPage">  
   + <Page Name="ConfigScanBareMetal" DisplayName="Deployment Readiness" Type="Microsoft.OSDRefresh.ConfigScanPage">  
   + <Page Name="RebootPage" DisplayName="Reboot" Type="Microsoft.OSDRefresh.RebootPage">  
   + <Page Name="WelcomePageReplace" DisplayName="Welcome" Type="Microsoft.SharedPages.WelcomePage">  
   + <Page Name="VolumePage" DisplayName="Volume" Type="Microsoft.OSDRefresh.VolumePage">  
   + <Page Name="UserRestorePage" DisplayName="Select Target" Type="Microsoft.OSDRefresh.UserStatePage">  
   + <Page Name="ComputerPage" DisplayName="New Computer Details" Type="Microsoft.OSDRefresh.ComputerPage">  
   + <Page Name="AdminAccounts" DisplayName="Administrator Password" Type="Microsoft.SharedPages.AdminAccountsPage">  
   + <Page Name="UDAPage" DisplayName="User Device Affinity" Type="Microsoft.OSDRefresh.UDAPage">  
   + <Page Name="LanguagePage" DisplayName="Language" Type="Microsoft.OSDRefresh.LanguagePage">  
   + <Page Name="ApplicationPage" DisplayName="Install Programs" Type="Microsoft.OSDRefresh.ApplicationPage">  
     <Page Name="SummaryPage" DisplayName="Summary" Type="Microsoft.Shared.SummaryPage" />   
   + <Page Name="UserCapturePageOldPC" DisplayName="Select Target" Type="Microsoft.OSDRefresh.UserStatePage">  
   + <Page Name="ProgressPage" DisplayName="Capture Data" Type="Microsoft.OSDRefresh.ProgressPage">  
   + <Page Name="RebootAfterCapture" DisplayName="Reboot" Type="Microsoft.OSDRefresh.RebootPage">  
</Pages>  
```  

####  <a name="RadioGroup"></a> RadioGroup  
 Ten element określa grupę przyciski radiowe z w [pola](#Field) elementu.  

##### <a name="element-information"></a>Informacje o elementach  
100 tabela zawiera informacje na temat [RadioGroup](#RadioGroup) elementu.  

### <a name="table-100-radiogroup-element-information"></a>100 tabeli. Informacje o elementach RadioGroup  

|**Atrybut**|**Wartość**|  
|-|-|  
|Liczba wystąpień|Zero lub więcej w [pola](#Fields) elementu (ten element jest opcjonalny).|  
|Elementy nadrzędne|**Pola**|  
|Zawartość|**Domyślny**|  

##### <a name="element-attributes"></a>Atrybuty elementu  
 101 tabela zawiera listę atrybutów [RadioGroup](#RadioGroup) element i zawiera opis każdego z nich.  

### <a name="table-101-attributes-and-corresponding-values-for-the-radiogroup-element"></a>101 tabeli. Atrybuty i wartości dla elementu RadioGroup  

|**Atrybut**|**Opis**|  
|-|-|  
|**Zablokowane**|Określa, czy grupa przycisków radiowych jest włączone dla danych wejściowych użytkownika. Ten atrybut może należeć do:<br /><br /> -   **Wartość true,**. Określa, że przycisków radiowych są wyłączone, a użytkownicy nie można wybrać przycisk radiowy w grupie.<br />-   **FALSE**. Określa, że włączono przycisków radiowych i użytkownicy mogą wybrać przycisk radiowy w grupie.|  
|**Nazwa**|Określa nazwę grupy opcji opcji.|  

##### <a name="remarks"></a>Uwagi  
 Brak.  

##### <a name="example"></a>Przykład  
 Brak.  

####  <a name="StageGroup"></a> StageGroup  
 Ten element określa grupę etap wdrażania.  

##### <a name="element-information"></a>Informacje o elementach  
102 tabela zawiera informacje na temat [StageGroup](#StageGroup) elementu.  

### <a name="table-102-stagegroup-element-information"></a>102 tabeli. Informacje o elementach StageGroup  

|**Atrybut**|**Wartość**|  
|-|-|  
|Liczba wystąpień|Co najmniej jeden w ramach [StageGroups](#StageGroups) — element|  
|Elementy nadrzędne|**StageGroups**|  
|Zawartość|**Etap**|  

##### <a name="element-attributes"></a>Atrybuty elementu  
 103 tabela zawiera listę atrybutów [StageGroup](#StageGroup) element i opis atrybutu.  

### <a name="table-103-attributes-and-corresponding-values-for-the-stagegroup-element"></a>103 tabeli. Atrybuty i wartości dla elementu StageGroup  

|**Atrybut**|**Opis**|  
|-|-|  
|**DisplayName**|Określa przyjazną dla użytkownika nazwę grupy etapu wyświetlany w projektanta Kreatora instalacji UDI. Ta nazwa jest zazwyczaj bardziej opisowe niż **nazwa** atrybutu.|  

##### <a name="remarks"></a>Uwagi  
 Brak.  

##### <a name="example"></a>Przykład  
 Brak.  

####  <a name="StageGroups"></a> StageGroups  
 Ten element grupy grupy etap w pliku konfiguracji kreatora UDI.  

##### <a name="element-information"></a>Informacje o elementach  
104 tabela zawiera informacje na temat [StageGroups](#StageGroups) elementu.  

### <a name="table-104-stagegroups-element-information"></a>104 tabeli. Informacje o elementach StageGroups  

|**Atrybut**|**Wartość**|  
|-|-|  
|Liczba wystąpień|Zero lub jeden w ramach [kreatora](#Wizard) — element|  
|Elementy nadrzędne|**Kreator**|  
|Zawartość|**StageGroup**|  

##### <a name="element-attributes"></a>Atrybuty elementu  
 Ten element nie ma żadnych atrybutów.  

##### <a name="remarks"></a>Uwagi  
 Brak.  

##### <a name="example"></a>Przykład  
 Brak.  

####  <a name="Setter"></a> Metody ustawiającej  
 Ten element określa ustawienia właściwości dla wartości dla właściwości o nazwie w **właściwości** właściwości.  

##### <a name="element-information"></a>Informacje o elementach  
 105 tabela zawiera informacje na temat [metody ustawiającej]() elementu.  

### <a name="table-105-setter-element-information"></a>105 tabeli. Informacje o elementach metody ustawiającej  

|**Atrybut**|**Wartość**|  
|-|-|  
|Liczba wystąpień|Zero lub więcej w ramach każdego elementu nadrzędnego (ten element jest opcjonalny).|  
|Elementy nadrzędne|**Dane**, **DataItem**, **strony**, **styl**, **zadań**, **modułu sprawdzania poprawności**|  
|Zawartość|Zawiera wartość ciągu w **właściwość** atrybutu|  

##### <a name="element-attributes"></a>Atrybuty elementu  
106 tabeli wymieniono atrybut [metody ustawiającej]() element i zawiera jego opis.  

### <a name="table-106-attributes-and-corresponding-values-for-the-setter-element"></a>106 tabeli. Atrybuty i wartości dla elementu Setter  

|**Atrybut**|**Opis**|  
|-|-|  
|**Właściwość**|Określa nazwę właściwości ustawiania. Nazwa właściwości ma ustawioną wartość tego atrybutu w nawiasach kwadratowych.|  

##### <a name="remarks"></a>Uwagi  
 Brak.  

##### <a name="example"></a>Przykład  
 Brak.  

#### <a name="stage"></a>Etap  
 Ten element Określa [etap](#Stage) w [StageGroup](#StageGroup) i zawiera co najmniej jeden [PageRef](#PageRef) elementów.  

##### <a name="element-information"></a>Informacje o elementach  
107 tabela zawiera informacje na temat [etap](#Stage) elementu.  

### <a name="table-107-stage-element-information"></a>107 tabeli. Informacje o elementach etap  

|**Atrybut**|**Wartość**|  
|-|-|  
|Liczba wystąpień|Co najmniej jeden w ramach [StageGroup](#StageGroup) — element|  
|Elementy nadrzędne|**StageGroup**|  
|Zawartość|**PageRef**|  

##### <a name="element-attributes"></a>Atrybuty elementu  
108 tabela zawiera listę atrybutów [etap](#Stage) element i zawiera opis każdego z nich.  

### <a name="table-108-attributes-and-corresponding-values-for-the-stage-element"></a>108 tabeli. Atrybuty i wartości dla elementu etap  

|**Atrybut**|**Opis**|  
|-|-|  
|**DisplayName**|Określa przyjazną dla użytkownika nazwa wyświetlana w projektanta Kreatora instalacji UDI strony kreatora. Ta nazwa jest zazwyczaj bardziej opisowe niż **nazwa** atrybutu.|  
|**Nazwa**|Określa nazwę etapu. Wartość tego elementu jest używana podczas uruchamiania kreatora UDI z **/etap: nazwa** parametr wiersza polecenia.|  

##### <a name="remarks"></a>Uwagi  
 Brak.  

##### <a name="example"></a>Przykład  
 Brak.  

####  <a name="Style"></a> Styl  
 Ten element grupuje poszczególne [metody ustawiającej]() elementów, które skonfigurować kreatora UDI wyglądu i działania, łącznie z tytułu wyświetlaną u góry kreatora i transparent obraz wyświetlany w Kreatorze UDI.  

##### <a name="element-information"></a>Informacje o elementach  
109 tabela zawiera informacje dotyczące elementu stylu.  

### <a name="table-109-style-element-information"></a>109 tabeli. Informacje o elementach stylu  

|**Atrybut**|**Wartość**|  
|-|-|  
|Liczba wystąpień|jeden|  
|Elementy nadrzędne|**Kreator**|  
|Zawartość|**Metody ustawiającej**|  

##### <a name="element-attributes"></a>Atrybuty elementu  
 Ten element nie ma żadnych atrybutów.  

##### <a name="remarks"></a>Uwagi  
 Brak.  

##### <a name="example"></a>Przykład  

```  
<Style>  
  <Setter Property="bannerFilename">UDI_Wizard_Banner.bmp</Setter>   
  <Setter Property="title">Operating System Deployment (OSD) Refresh Wizard</Setter>   
</Style>  
```  

####  <a name="TaskElement"></a> Zadanie  
 Ten element Określa zadanie, które ma być uruchamiane na stronie określony w obiekcie nadrzędnym [strony](#Page) elementu.  

##### <a name="element-information"></a>Informacje o elementach  
110 tabela zawiera informacje na temat [zadań](#Task) elementu.  

### <a name="table-110-task-element-information"></a>110 tabeli. Informacje o elementach zadań  

|**Atrybut**|**Wartość**|  
|-|-|  
|Liczba wystąpień|Co najmniej jeden w ramach [zadania](#Tasks) — element|  
|Elementy nadrzędne|**Zadania**|  
|Zawartość|**ExitCodes**, **pliku**, **metody ustawiającej**|  

##### <a name="element-attributes"></a>Atrybuty elementu  
111 tabela zawiera listę atrybutów [zadań](#Task) element i zawiera opis każdego z nich.  

### <a name="table-111-attributes-and-corresponding-values-for-the-task-element"></a>111 tabeli. Atrybuty i wartości dla elementu zadania  

|**Atrybut**|**Opis**|  
|-|-|  
|**dependsOn**|Określa, czy zadanie jest zależne od innego zadania. Wartość tego atrybutu jest ustawiona na **nazwa** atrybutu innego [zadań](#Task) elementu. **Uwaga:**  Ten atrybut nie można skonfigurować za pomocą projektanta Kreatora instalacji UDI. Jednak można ręcznie dodać ten atrybut [zadań](#Task) elementu przez bezpośrednie zmodyfikowanie pliku .xml.|  
|**DisplayName**|Określa przyjazną dla użytkownika nazwę zadań wyświetlane w projektanta Kreatora instalacji UDI. Ta nazwa jest zazwyczaj bardziej opisowe niż **nazwa** atrybutu.|  
|**Nazwa**|Określa nazwę zadania. Ta nazwa musi być unikatowa.|  
|Typ|Określa typ zadań dla zadania do wykonania, która jest zdefiniowana w pliku DLL zawierającego zadanie.|  

##### <a name="remarks"></a>Uwagi  
 Brak.  

##### <a name="example"></a>Przykład  
 Brak.  

####  <a name="Tasks"></a> Zadania  
 Ten element grupy zestawu zadań dla [strony](#Page) elementu.  

##### <a name="element-information"></a>Informacje o elementach  
112 tabela zawiera informacje na temat [zadania](#Tasks) elementu.  

### <a name="table-112-tasks-element-information"></a>112 tabeli. Informacje o elementach zadań  

|**Atrybut**|**Wartość**|  
|-|-|  
|Liczba wystąpień|Zero lub jeden w każdym [strony](#Page) elementu (ten element jest opcjonalny).|  
|Elementy nadrzędne|**Strona**|  
|Zawartość|**Zadanie**|  

##### <a name="element-attributes"></a>Atrybuty elementu  
113 tabela zawiera listę atrybutów [zadania](#Tasks) element i zawiera opis każdego z nich.  

### <a name="table-113-attributes-and-corresponding-values-for-the-tasks-element"></a>113 tabeli. Atrybuty i wartości dla elementu zadania  

|**Atrybut**|**Opis**|  
|-|-|  
|**NameTitle**|Określa podpis wyświetlany w górnej części kolumny, która zawiera nazwę zadania w odpowiedniej strony w kreatorze.|  
|**StatusTitle**|Określa podpis wyświetlany w górnej części kolumny, która zawiera stan zadań w odpowiedniej strony w kreatorze.|  

##### <a name="remarks"></a>Uwagi  
 Brak.  

##### <a name="example"></a>Przykład  
 Brak.  

####  <a name="ValidatorElement"></a> Moduł sprawdzania poprawności  
 Ten element Określa moduł weryfikacji dla formantu pole, który jest określony w obiekcie nadrzędnym [pola](#Field) elementu.  

##### <a name="element-information"></a>Informacje o elementach  
114 tabela zawiera informacje na temat [modułu sprawdzania poprawności](#Validator) elementu.  

### <a name="table-114-validator-element-information"></a>114 tabeli. Informacje o elementach modułu sprawdzania poprawności  

|**Atrybut**|**Wartość**|  
|-|-|  
|Liczba wystąpień|Zero lub jeden w ramach [pola](#Field) — element|  
|Elementy nadrzędne|**Pole**|  
|Zawartość|**Metody ustawiającej**|  

##### <a name="element-attributes"></a>Atrybuty elementu  
115 tabeli wymieniono atrybut [modułu sprawdzania poprawności](#Validator) element i zawiera jego opis.  

### <a name="table-115-attributes-and-corresponding-values-for-the-validator-element"></a>115 tabeli. Atrybuty i wartości dla elementu modułu sprawdzania poprawności  

|**Atrybut**|**Opis**|  
|-|-|  
|Typ|Określa typ Walidatora, który został zdefiniowany w bibliotece DLL, które zawiera moduł weryfikacji|  

##### <a name="remarks"></a>Uwagi  
 Brak.  

##### <a name="example"></a>Przykład  
 Brak.  

####  <a name="Wizard"></a> Kreator  
 Ten element Określa katalog główny dla wszystkich innych elementów.  

##### <a name="element-information"></a>Informacje o elementach  
116 tabela zawiera informacje na temat [kreatora](#Wizard) elementu.  

### <a name="table-116-wizard-element-information"></a>116 tabeli. Informacje o elementach Kreatora  

|**Atrybut**|**Wartość**|  
|-|-|  
|Liczba wystąpień|jeden|  
|Elementy nadrzędne|Brak|  
|Zawartość|**Biblioteki dll**, **stron**, **StageGroups**, **stylu**|  

##### <a name="element-attributes"></a>Atrybuty elementu  
 Ten element nie ma żadnych atrybutów.  

##### <a name="remarks"></a>Uwagi  
 Brak.  

##### <a name="example"></a>Przykład  

```  
<Wizard>  
   + <DLLs>  
   + <Style>  
   + <Pages>  
   + <StageGroups>  
</Wizard>  
```
