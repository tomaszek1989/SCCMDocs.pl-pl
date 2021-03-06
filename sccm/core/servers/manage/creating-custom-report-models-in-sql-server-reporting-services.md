---
title: Tworzenie niestandardowych raportów
titleSuffix: Configuration Manager
description: Zdefiniować modele, aby spełnić wymagania biznesowe, a następnie wdrożyć modeli raportów do programu Configuration Manager.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: f2df88b4-c348-4dcf-854a-54fd6eedf485
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: fd606ff7068b7c14047e445d16ea78d20a5c12ea
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="creating-custom-report-models-for-system-center-configuration-manager-in-sql-server-reporting-services"></a>Tworzenie niestandardowych modeli raportów programu System Center Configuration Manager w SQL Server Reporting Services

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

W programie System Center Configuration Manager są dostępne przykładowe modele raportów, ale można również zdefiniować modele, aby spełnić wymagania biznesowe, a następnie Wdróż model raportu do programu Configuration Manager do użycia podczas tworzenia nowych raportów na podstawie modelu. W poniższej tabeli przedstawiono opis kroków składających się na tworzenie i wdrożenie podstawowego modelu raportu.  

> [!NOTE]  
>  Opis kroków służących do utworzenia bardziej zaawansowanego modelu raportu znajduje się w sekcji [kroki tworzenia zaawansowanego modelu raportu w usługach SQL Server Reporting Services](#AdvancedReportModel) w tym temacie.  

|Krok|Opis|Więcej informacji|  
|----------|-----------------|----------------------|  
|Sprawdź, że jest zainstalowany program SQL Server Business Intelligence Development Studio|Modele raportów projektuje się i konstruuje w programie SQL Server Business Intelligence Development Studio. Sprawdź, że program SQL Server Business Intelligence Development Studio jest zainstalowany na komputerze, na którym tworzysz niestandardowy model raportu.|Więcej informacji o programie SQL Server Business Intelligence Development Studio znajduje się w dokumentacji programu SQL Server 2008.|  
|Utwórz projekt modelu raportu|Projekt modelu raportu obejmuje definicję źródła danych (plik .ds), definicję widoku źródła danych (plik .dsv) oraz model raportu (plik .smdl).|Więcej informacji można znaleźć w sekcji [To create the report model project](#BKMK_CreateReportModelProject) w tym temacie.|  
|Zdefiniuj źródło danych dla modelu raportu|Po utworzeniu projektu modelu raportu należy zdefiniować jedno źródło danych, z którego będą wyodrębniane dane biznesowe. Zazwyczaj jest to bazy danych lokacji programu Configuration Manager.|Więcej informacji można znaleźć w sekcji [Aby zdefiniować źródło danych dla modelu raportu](#BKMK_DefineReportModelDataSource) w tym temacie.|  
|Zdefiniuj widok źródła danych dla modelu raportu|Po zdefiniowaniu źródeł danych do wykorzystania w projekcie modelu raportu następnym krokiem jest zdefiniowanie widoku źródła danych dla projektu. Widok źródła danych to model danych logicznych oparty na jednym lub większej liczbie źródeł danych. Widoki źródeł danych reprezentują dostęp do obiektów fizycznych, takich jak tabele i widoki, zawartych w odnośnych źródłach danych. Z widoku źródła danych usługi SQL Server Reporting Services generują model raportu.<br /><br /> Widoki źródła danych umożliwiają proces projektowania modelu, zapewniając praktyczne odwzorowanie określonych danych. Nie zmieniając odnośnych źródeł danych, w widoku źródła danych można zmieniać nazwy tabel i pól oraz dodawać pola zbiorcze i tabele pochodne. Aby tworzony model działał sprawnie, do widoku źródła danych warto dodawać tylko te tabele, z których planuje się korzystać.|Więcej informacji można znaleźć w sekcji [Aby zdefiniować widok źródła danych dla modelu raportu](#BKMK_DefineReportModelDataSourceView) w tym temacie.|  
|Utwórz model raportu|Model raportu to wierzchnia warstwa bazy danych, która identyfikuje jednostki biznesowe, pola i role. Posługując się tymi modelami po ich opublikowaniu, użytkownicy programu Report Builder mogą opracowywać raporty bez potrzeby zaznajamiania się ze strukturami baz danych i bez potrzeby rozumienia kwerend czy umiejętności ich pisania. Modele składają się z zestawów powiązanych ze sobą elementów raportów, które zgrupowano pod przyjazną nazwą, ze wstępnie zdefiniowanymi relacjami między tymi elementami biznesowymi i ze wstępnie zdefiniowanymi obliczeniami. Modele definiuje się w odmianie języka XML zwanej językiem definiowania modeli semantycznych (ang. Semantic Model Definition Language, SMDL). Rozszerzenie nazwy pliku modelu raportu to .smdl.|Więcej informacji można znaleźć w sekcji [To create the report model](#BKMK_CreateReportModel) w tym temacie.|  
|Opublikuj model raportu|Aby utworzyć raport na podstawie właśnie utworzonego modelu, należy opublikować ten model na serwerze raportów. Źródło danych i widok źródła danych są dołączane do modelu w czasie jego publikacji.|Więcej informacji można znaleźć w sekcji [Aby opublikować model raportu w programie SQL Server Reporting Services](#BKMK_PublishReportModel) w tym temacie.|  
|Wdróż model raportu do programu Configuration Manager|Przed użyciem niestandardowego modelu raportu w **Kreatora tworzenia raportu** do utworzenia raportu na podstawie modelu, należy wdrożyć model raportu do programu Configuration Manager.|Więcej informacji można znaleźć w sekcji [Aby wdrożyć niestandardowy model raportu do programu Configuration Manager](#BKMK_DeployReportModel) w tym temacie.|  

## <a name="steps-for-creating-a-basic-report-model-in-sql-server-reporting-services"></a>Procedury tworzenia podstawowego modelu raportu w usługach SQL Server Reporting Services  
 Poniższe procedury służą do utworzenia podstawowego modelu raportu, który użytkownicy danej lokacji mogą wykorzystać do tworzenia konkretnych raportów na podstawie modelu, opartych na danych pojedynczego widoku bazy danych programu Configuration Manager. Utworzony model raportu prezentuje autorowi raportu informacje o komputerach klienckich w danej lokacji. Informacje te są brane z **v_R_System** widoku w bazie danych programu Configuration Manager.  

 Sprawdź, czy na komputerze, na którym wykonujesz tę procedurę, jest zainstalowany program SQL Server Business Intelligence Development Studio i czy komputer ma łączność sieciową z serwerem punktu usług raportowania. Szczegółowe informacje o programie SQL Server Business Intelligence Development Studio znajdują się w dokumentacji programu SQL Server 2008.  

###  <a name="BKMK_CreateReportModelProject"></a> To create the report model project  

1.  Na pulpicie komputera kliknij przycisk **Start**, **Microsoft SQL Server 2008**i **SQL Server Business Intelligence Development Studio**.  

2.  Gdy program **SQL Server Business Intelligence Development Studio** zostanie otwarty w programie Microsoft Visual Studio, kliknij polecenie **Plik**, **Nowy**i **Projekt**.  

3.  W oknie dialogowym **Nowy projekt** , na liście **Szablony** zaznacz opcję **Projekt z modelem raportu** .  

4.  W polu **Nazwa** wpisz nazwę danego modelu raportu. W ramach tego przykładu wpisz **Simple_Model**.  

5.  Aby utworzyć projekt z modelem raportu, kliknij przycisk **OK**.  

6.  W **Eksploratorze rozwiązań** jest wyświetlone rozwiązanie **Simple_Model**.  

    > [!NOTE]  
    >  Jeśli okienko **Eksploratora rozwiązań** nie jest widoczne, kliknij polecenia **Widok**i **Eksplorator rozwiązań**.  

###  <a name="BKMK_DefineReportModelDataSource"></a>Aby zdefiniować źródło danych dla modelu raportu  

1.  W okienku **Eksploratora rozwiązań** programu **SQL Server Business Intelligence Development Studio**kliknij prawym przyciskiem myszy polecenie **Źródła danych** i wybierz polecenie **Dodaj nowe źródło danych**.  

2.  Na stronie **Witamy w Kreatorze źródła danych** kliknij przycisk **Dalej**.  

3.  Na stronie **Wybierz sposób definiowania połączenia** sprawdź, czy została wybrana opcja **Utwórz źródło danych na podstawie istniejącego lub nowego połączenia** i kliknij przycisk **Nowe**.  

4.  W oknie dialogowym **Menedżer połączeń** wprowadź następujące właściwości źródła danych:  

    -   **Nazwa serwera**: Wpisz nazwę serwera bazy danych lokacji programu Configuration Manager lub wybierz ją z listy. Jeśli pracujesz przy użyciu nazwanego wystąpienia, a nie wystąpieniem domyślnym, wpisz &lt; *serwera bazy danych*>\\&lt;*nazwa wystąpienia*>.  

    -   Wybierz opcję **Uwierzytelnianie systemu Windows**.  

    -   W **wybierz lub wprowadź nazwę bazy danych** listy, wybierz nazwę bazy danych lokacji programu Configuration Manager.  

5.  Aby sprawdzić połączenie z bazą danych, kliknij przycisk **Testuj połączenie**.  

6.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Menedżer połączeń** . Jeśli połączenie nie powiedzie się, sprawdź, czy wprowadzone zostały poprawne informacje i kliknij jeszcze raz przycisk **Testuj połączenie** .  

7.  Na stronie **Wybierz, jak zdefiniować połączenie** sprawdź, że jest wybrana opcja **Utwórz źródło danych na podstawie istniejącego lub nowego połączenia** , sprawdź, że określone właśnie źródło danych jest wybrane w polu **Połączenia danych**, a następnie kliknij przycisk **Dalej**.  

8.  W polu **Nazwa źródła danych**określ nazwę dla źródła danych, a następnie kliknij przycisk **Zakończ**. W ramach tego przykładu wpisz **Simple_Model**.  

9. W **Eksploratorze rozwiązań** w węźle **Źródła danych** jest teraz wyświetlone źródło danych **Simple_Model.ds** .  

    > [!NOTE]  
    >  Aby zmienić właściwości istniejącego źródła danych, kliknij dwukrotnie źródło danych w folderze **Źródła danych** okienka **Eksplorator rozwiązań** . Właściwości źródła danych zostaną wyświetlone w Projektancie źródła danych.  

###  <a name="BKMK_DefineReportModelDataSourceView"></a>Aby zdefiniować widok źródła danych dla modelu raportu  

1.  W okienku **Eksploratora rozwiązań**kliknij prawym przyciskiem myszy polecenie **Widoki źródła danych** i wybierz polecenie **Dodaj nowy widok źródła danych**.  

2.  Na stronie **Witamy w Kreatorze widoku źródła danych** kliknij przycisk **Dalej**. Zostanie wyświetlona strona **Wybierz źródło danych** .  

3.  W oknie **Relacyjne źródła danych** sprawdź, że jest wybrane źródło danych **Simple_Model** , a następnie kliknij przycisk **Dalej**.  

4.  Na stronie **Wybieranie tabel i widoków** zaznacz na liście **Dostępne obiekty** następujący widok do użycia w modelu raportu: **v_R_System (dbo)**.  

    > [!TIP]  
    >  Aby łatwiej zlokalizować widoki na liście **Dostępne obiekty** , kliknij nagłówek **Nazwa** na górze listy. Obiekty zostaną posortowane w kolejności alfabetycznej.  

5.  Po zaznaczeniu widoku kliknij przycisk **>** , aby przenieść obiekt na listę **Uwzględnione obiekty** .  

6.  Jeśli zostanie wyświetlona strona **Dopasowywanie nazw** , zaakceptuj ustawienia domyślne, a następnie kliknij przycisk **Dalej**.  

7.  Po zakończeniu wybierania potrzebnych obiektów kliknij przycisk **Dalej**, a następnie określ nazwę dla widoku źródła danych. W ramach tego przykładu wpisz **Simple_Model**.  

8.  Kliknij przycisk **Zakończ**. Widok źródła danych **Simple_Model.dsv** zostanie wyświetlony w folderze **Widoki źródła danych** **Eksploratora rozwiązań**.  

###  <a name="BKMK_CreateReportModel"></a> To create the report model  

1.  W okienku **Eksploratora rozwiązań**kliknij prawym przyciskiem myszy polecenie **Modele raportu** i wybierz polecenie **Dodaj nowy model raportu**.  

2.  Na stronie **Witamy w Kreatorze modelu raportu** kliknij przycisk **Dalej**.  

3.  Na stronie **Wybieranie widoków źródła danych** wybierz widok źródła danych z listy **Dostępne widoki źródła danych** , a następnie kliknij przycisk **Dalej**. Na potrzeby tego przykładu wybierz plik **Simple_Model.dsv**.  

4.  Na stronie **Wybieranie zasad generowania modelu raportu** zaakceptuj ustawienia domyślne, a następnie kliknij przycisk **Dalej**.  

5.  Na stronie **Statystyki modelu kolekcji** sprawdź, czy została wybrana opcja **Aktualizuj statystyki modelu przed tworzeniem** i kliknij przycisk **Dalej**.  

6.  Na stronie **Kończenie pracy kreatora** wpisz nazwę modelu raportu. W ramach tego przykładu sprawdź, że jest wyświetlona nazwa **Simple_Model** .  

7.  Aby zakończyć pracę kreatora i utworzyć model raportu, kliknij przycisk **Uruchom**.  

8.  Aby wyjść z kreatora, kliknij przycisk **Zakończ**. Model raportu pojawi się w oknie projektowania.  

###  <a name="BKMK_PublishReportModel"></a>Aby opublikować model raportu w programie SQL Server Reporting Services  

1.  W **Eksploratorze rozwiązań**kliknij prawym przyciskiem myszy model raportu i wybierz polecenie **Wdróż**. W ramach tego przykładu modelem raportu jest **Simple_Model.smdl**.  

2.  Sprawdź status wdrożenia w lewym dolnym rogu okna programu **SQL Server Business Intelligence Development Studio** . Po zakończeniu wdrażania zostanie wyświetlony komunikat **Wdrożenie powiodło się** . Jeśli wdrożenie nie powiodło się, powód awarii zostanie wyświetlony w oknie **Wyjście** . Nowy model raportu zostanie udostępniony w witrynie sieci Web usług SQL Server Reporting Services.  

3.  Kliknij przycisk **Plik**, polecenie **Zapisz wszystko**i zamknij okno programu **SQL Server Business Intelligence Development Studio**.  

###  <a name="BKMK_DeployReportModel"></a> Aby wdrożyć niestandardowy model raportu do programu Configuration Manager  

1.  Zlokalizuj folder, w którym został utworzony projekt z modelem raportu. Na przykład %*USERPROFILE*%\Documents\Visual Studio 2008\Projects\\*&lt;Nazwa projektu\>.*  

2.  Skopiuj następujące pliki z folderu projektu modelu raportu do folderu tymczasowego na komputerze:  

    -   *&lt;Nazwa modelu\>*  **.dsv**  

    -   *&lt;Nazwa modelu\>*  **.smdl**  

3.  Otwórz poprzednie pliki w edytorze tekstów, np. Notatniku.  

4.  W pliku *&lt;Nazwa modelu\>***.dsv**, zlokalizuj pierwszy wiersz pliku o następującej treści:  

     **&lt;DataSourceView xmlns = "http://schemas.microsoft.com/analysisservices/2003/engine"\>**  

     Zmień go na następujący wiersz:  

     **&lt;DataSourceView xmlns = "http://schemas.microsoft.com/analysisservices/2003/engine" xmlns:xsi = "RelationalDataSourceView"\>**  

5.  Skopiuj cała zawartość pliku do schowka systemu Windows.  

6.  Zamknij plik *&lt;Nazwa modelu\>***.dsv**.  

7.  W pliku *&lt;Nazwa modelu\>***.smdl**, zlokalizuj trzy ostatnie wiersze pliku, które znajdują się w następujący sposób:  

     `</Entity>`  

     `</Entities>`  

     `</SemanticModel>`  

8.  Wklej zawartość pliku  *&lt;Nazwa modelu\>** *.dsv** bezpośrednio przed ostatnim wierszem pliku (**&lt;SemanticModel\>**).  

9. Zapisz i zamknij plik *&lt;Nazwa modelu\>***.smdl**.  

10. Skopiuj plik  *&lt;Nazwa modelu\>** *.smdl** do folderu *% programfiles %* \Microsoft Configuration Manager \AdminConsole\XmlStorage\Other na konfiguracji Menedżer serwera lokacji.  

    > [!IMPORTANT]  
    >  Po skopiowaniu pliku modelu raportu na serwerze lokacji programu Configuration Manager, należy zamknąć i ponownie uruchomić konsolę programu Configuration Manager zanim można użyć danego modelu raportu w **Kreatora tworzenia raportu**.  

##  <a name="AdvancedReportModel"></a>Procedura tworzenia zaawansowanego modelu raportu w programie SQL Server Reporting Services  
 Poniższe procedury służą do utworzenia zaawansowanego modelu raportu, który użytkownicy danej lokacji mogą wykorzystać do tworzenia konkretnych raportów na podstawie modelu, opartych na danych wielu widoków bazy danych programu Configuration Manager. Utworzony model raportu prezentuje autorowi raportu informacje o komputerach klienckich i zainstalowanym na nich systemie operacyjnym. Informacje te są brane z następujących widoków bazy danych programu Configuration Manager:  

-   **V_R_System**: Zawiera informacje o wykrytych komputerach i kliencie programu Configuration Manager.  

-   **V_GS_OPERATING_SYSTEM**: Zawiera informacje o systemie operacyjnym zainstalowanym na komputerze klienckim.  

 Pozycje wybrane w poprzednich widokach są łączone na jednej liście, mają nadawane przyjazne nazwy i przedstawiane autorowi raportu w programie Report Builder do uwzględnienia w poszczególnych raportach.  

 Sprawdź, czy na komputerze, na którym wykonujesz tę procedurę, jest zainstalowany program SQL Server Business Intelligence Development Studio i czy komputer ma łączność sieciową z serwerem punktu usług raportowania. Szczegółowe informacje o programie SQL Server Business Intelligence Development Studio znajdują się w dokumentacji programu SQL Server.  

#### <a name="to-create-the-report-model-project"></a>To create the report model project  

1.  Na pulpicie komputera kliknij przycisk **Start**, **Microsoft SQL Server 2008**i **SQL Server Business Intelligence Development Studio**.  

2.  Gdy program **SQL Server Business Intelligence Development Studio** zostanie otwarty w programie Microsoft Visual Studio, kliknij polecenie **Plik**, **Nowy**i **Projekt**.  

3.  W oknie dialogowym **Nowy projekt** , na liście **Szablony** zaznacz opcję **Projekt z modelem raportu** .  

4.  W polu **Nazwa** wpisz nazwę danego modelu raportu. W ramach tego przykładu wpisz **Advanced_Model**.  

5.  Aby utworzyć projekt z modelem raportu, kliknij przycisk **OK**.  

6.  W okienku **Eksploratora rozwiązań** zostanie wyświetlone rozwiązanie **Advanced_Model**.  

    > [!NOTE]  
    >  Jeśli okienko **Eksploratora rozwiązań** nie jest widoczne, kliknij polecenia **Widok**i **Eksplorator rozwiązań**.  

#### <a name="to-define-the-data-source-for-the-report-model"></a>Aby zdefiniować źródło danych dla modelu raportu  

1.  W okienku **Eksploratora rozwiązań** programu **SQL Server Business Intelligence Development Studio**kliknij prawym przyciskiem myszy polecenie **Źródła danych** i wybierz polecenie **Dodaj nowe źródło danych**.  

2.  Na stronie **Witamy w Kreatorze źródła danych** kliknij przycisk **Dalej**.  

3.  Na stronie **Wybierz sposób definiowania połączenia** sprawdź, czy została wybrana opcja **Utwórz źródło danych na podstawie istniejącego lub nowego połączenia** i kliknij przycisk **Nowe**.  

4.  W oknie dialogowym **Menedżer połączeń** wprowadź następujące właściwości źródła danych:  

    -   **Nazwa serwera**: Wpisz nazwę serwera bazy danych lokacji programu Configuration Manager lub wybierz ją z listy. Jeśli pracujesz przy użyciu nazwanego wystąpienia, a nie wystąpieniem domyślnym, wpisz &lt; *serwera bazy danych*>\\&lt;*nazwa wystąpienia*>.  

    -   Wybierz opcję **Uwierzytelnianie systemu Windows**.  

    -   W **wybierz lub wprowadź nazwę bazy danych** listy, wybierz nazwę bazy danych lokacji programu Configuration Manager.  

5.  Aby sprawdzić połączenie z bazą danych, kliknij przycisk **Testuj połączenie**.  

6.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Menedżer połączeń** . Jeśli połączenie nie powiedzie się, sprawdź, czy wprowadzone zostały poprawne informacje i kliknij jeszcze raz przycisk **Testuj połączenie** .  

7.  Na stronie **Wybierz sposób definiowania połączenia** sprawdź, czy została wybrana opcja **Utwórz źródło danych na podstawie istniejącego lub nowego połączenia** , sprawdź, czy określone źródło danych zostało wybrane w polu listy **Połączenia danych** i kliknij przycisk **Dalej**.  

8.  W polu **Nazwa źródła danych**wpisz nazwę źródła danych i kliknij przycisk **Zakończ**. W ramach tego przykładu wpisz **Advanced_Model**.  

9. W **Eksploratorze rozwiązań** , w węźle **Źródła danych** zostanie wyświetlone źródło danych **Advanced_Model.ds** .  

    > [!NOTE]  
    >  Aby zmienić właściwości istniejącego źródła danych, kliknij dwukrotnie źródło danych w folderze **Źródła danych** okienka **Eksplorator rozwiązań** . Właściwości źródła danych zostaną wyświetlone w Projektancie źródła danych.  

#### <a name="to-define-the-data-source-view-for-the-report-model"></a>Aby zdefiniować widok źródła danych dla modelu raportu  

1.  W okienku **Eksploratora rozwiązań**kliknij prawym przyciskiem myszy polecenie **Widoki źródła danych** i wybierz polecenie **Dodaj nowy widok źródła danych**.  

2.  Na stronie **Witamy w Kreatorze widoku źródła danych** kliknij przycisk **Dalej**. Zostanie wyświetlona strona **Wybierz źródło danych** .  

3.  W oknie **Relacyjne źródła danych** sprawdź, czy zostało wybrane źródło danych **Advanced_Model** i kliknij przycisk **Dalej**.  

4.  Na stronie **Wybierz tabele i widoki** wybierz następujące widoki z listy **Dostępne obiekty** , które zostaną użyte w modelu raportu:  

    -   **v_R_System (dbo)**  

    -   **v_GS_OPERATING_SYSTEM (dbo)**  

     Po wybraniu każdego widoku kliknij przycisk **>** , aby przenieść obiekt na listę **Uwzględnione obiekty** .  

    > [!TIP]  
    >  Aby łatwiej zlokalizować widoki na liście **Dostępne obiekty** , kliknij nagłówek **Nazwa** na górze listy. Obiekty zostaną posortowane w kolejności alfabetycznej.  

5.  Gdy pojawi się okno dialogowe **Dopasowywanie nazw** , zatwierdź wybór domyślny i kliknij przycisk **Dalej**.  

6.  Po wybraniu wymaganych obiektów kliknij przycisk **Dalej**i określ nazwę widoku źródła danych. W ramach tego przykładu wpisz **Advanced_Model**.  

7.  Kliknij przycisk **Zakończ**. W folderze **Widoki źródła danych** w **Eksploratorze rozwiązań** zostanie wyświetlony widok źródła danych **Advanced_Model.dsv**.  

#### <a name="to-define-relationships-in-the-data-source-view"></a>Aby zdefiniować relacje w widoku źródła danych  

1.  W **Eksploratorze rozwiązań**kliknij dwukrotnie opcję **Advanced_Model.dsv** . Zostanie otwarte okno projektowania.  

2.  Kliknij prawym przyciskiem myszy pasek tytułu okna **v_R_System** , wybierz opcję **Zamień tabelę**i kliknij opcję **Za pomocą nowego nazwanego zapytania**.  

3.  W oknie dialogowym **Tworzenie nazwanego zapytania** kliknij ikonę **Dodaj tabelę** (przeważnie jest to ostatnia ikona na wstążce).  

4.  W oknie dialogowym **Dodawanie tabeli** kliknij kartę **Widoki** , wybierz z listy opcję **V_GS_OPERATING_SYSTEM** i kliknij przycisk **Dodaj**.  

5.  Zamknij okno dialogowe **Dodawanie tabeli** , klikając przycisk **Zamknij** .  

6.  W oknie dialogowym **Tworzenie nazwanego zapytania** wprowadź następujące informacje:  

    -   **Nazwa:** Określ nazwę zapytania. W ramach tego przykładu wpisz **Advanced_Model**.  

    -   **Opis:** Określ opis zapytania. Przykładowo wpisz **Przykładowy model raportu usług Reporting Services**.  

7.  W oknie **v_R_System** wybierz następujące pozycje z listy obiektów do wyświetlenia w modelu raportu:  

    -   **ResourceID**  

    -   **ResourceType**  

    -   **Active0**  

    -   **AD_Domain_Name0**  

    -   **AD_SiteName0**  

    -   **Client0**  

    -   **Client_Type0**  

    -   **Client_Version0**  

    -   **CPUType0**  

    -   **Hardware_ID0**  

    -   **User_Domain0**  

    -   **User_Name0**  

    -   **Netbios_Name0**  

    -   **Operating_System_Name_and0**  

8.  W oknie **v_GS_OPERATING_SYSTEM** wybierz następujące pozycje z listy obiektów przeznaczonych do wyświetlenia w modelu raportu:  

    -   **ResourceID**  

    -   **Caption0**  

    -   **CountryCode0**  

    -   **CSDVersion0**  

    -   **Description0**  

    -   **InstallDate0**  

    -   **LastBootUpTime0**  

    -   **Locale0**  

    -   **Manufacturer0**  

    -   **Version0**  

    -   **WindowsDirectory0**  

9. Aby obiekty z tych widoków przedstawić autorowi raportów jako jedną listę, określ relację między dwiema tabelami lub dwoma widokami za pomocą funkcji łączenia. Dwa widoki można połączyć, używając parametru **ResourceID**obiektu widocznego w obu widokach.  

10. W oknie **v_R_System** kliknij i przytrzymaj obiekt **ResourceID** , a następnie przeciągnij go na obiekt **ResourceID** w oknie **v_GS_OPERATING_SYSTEM** .  

11. Kliknij przycisk **OK**.  

12. Okno **Advanced_Model** , które zamieni okno **v_R_System** , będzie zawierało wszystkie niezbędne obiekty wymagane przez model raportu do widoków **v_R_System** i **v_GS_OPERATING_SYSTEM** . Następnie można usunąć okno **v_GS_OPERATING_SYSTEM** z Projektanta widoków źródła danych. Kliknij prawym przyciskiem myszy pasek tytułu okna **v_GS_OPERATING_SYSTEM** i wybierz opcję **Usuń tabelę z DSV**. W oknie dialogowym **Usuń obiekty** kliknij przycisk **OK** , aby potwierdzić decyzję.  

13. Kliknij przycisk **Plik**i polecenie **Zapisz wszystko**.  

#### <a name="to-create-the-report-model"></a>To create the report model  

1.  W okienku **Eksploratora rozwiązań**kliknij prawym przyciskiem myszy polecenie **Modele raportu** i wybierz polecenie **Dodaj nowy model raportu**.  

2.  Na stronie **Witamy w Kreatorze modelu raportu** kliknij przycisk **Dalej**.  

3.  Na stronie **Wybierz widok źródła danych** wybierz widok źródła danych z listy **Dostępne widoku źródła danych** i kliknij przycisk **Dalej**. Na potrzeby tego przykładu wybierz plik **Simple_Model.dsv**.  

4.  Na stronie **Wybierz reguły tworzenia modelu raportu** nie zmieniaj wartości domyślnych i kliknij przycisk **Dalej**.  

5.  Na stronie **Statystyki modelu kolekcji** sprawdź, czy została wybrana opcja **Aktualizuj statystyki modelu przed tworzeniem** i kliknij przycisk **Dalej**.  

6.  Na stronie **Kończenie pracy kreatora** wpisz nazwę modelu raportu. W ramach tego przykładu zostanie wyświetlony model **Advanced_Model** .  

7.  Aby zakończyć pracę kreatora i utworzyć model raportu, kliknij przycisk **Uruchom**.  

8.  Aby wyjść z kreatora, kliknij przycisk **Zakończ**.  

9. Model raportu pojawi się w oknie projektowania.  

#### <a name="to-modify-object-names-in-the-report-model"></a>Aby zmodyfikować nazwy obiektów w modelu raportu  

1.  W okienku **Eksploratora rozwiązań**kliknij prawym przyciskiem myszy model raportu i wybierz polecenie **Projektant widoków**. Na potrzeby tego przykładu wybierz plik **Advanced_Model.smdl**.  

2.  W widoku projektu modelu raportu kliknij prawym przyciskiem myszy dowolną nazwę obiektu i wybierz polecenie **Zmień nazwę**.  

3.  Wpisz nową nazwę wybranego obiektu, a następnie naciśnij klawisz Enter. Przykładowo możesz zmienić nazwę obiektu **CSD_Version_0** na **Wersja dodatku Service Pack dla systemu Windows**.  

4.  Po zakończeniu zmiany nazw obiektów kliknij przycisk **Plik**i polecenie **Zapisz wszystko**.  

#### <a name="to-publish-the-report-model-for-use-in-sql-server-reporting-services"></a>Aby opublikować model raportu w programie SQL Server Reporting Services  

1.  W okienku **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Advanced_Model.smdl** i wybierz polecenie **Wdróż**.  

2.  Sprawdź status wdrożenia w lewym dolnym rogu okna programu **SQL Server Business Intelligence Development Studio** . Po zakończeniu wdrażania zostanie wyświetlony komunikat **Wdrożenie powiodło się** . Jeśli wdrożenie nie powiodło się, powód awarii zostanie wyświetlony w oknie **Wyjście** . Nowy model raportu zostanie udostępniony w witrynie sieci Web usług SQL Server Reporting Services.  

3.  Kliknij przycisk **Plik**, polecenie **Zapisz wszystko**i zamknij okno programu **SQL Server Business Intelligence Development Studio**.  

#### <a name="to-deploy-the-custom-report-model-to-configuration-manager"></a>Aby wdrożyć niestandardowy model raportu do programu Configuration Manager  

1.  Zlokalizuj folder, w którym został utworzony projekt z modelem raportu. Na przykład %*USERPROFILE*%\Documents\Visual Studio 2008\Projects\\*&lt;Nazwa projektu\>.*  

2.  Skopiuj następujące pliki z folderu projektu modelu raportu do folderu tymczasowego na komputerze:  

    -   *&lt;Nazwa modelu\>*  **.dsv**  

    -   *&lt;Nazwa modelu\>*  **.smdl**  

3.  Otwórz poprzednie pliki w edytorze tekstów, np. Notatniku.  

4.  W pliku *&lt;Nazwa modelu\>***.dsv**, zlokalizuj pierwszy wiersz pliku o następującej treści:  

     **&lt;DataSourceView xmlns = "http://schemas.microsoft.com/analysisservices/2003/engine"\>**  

     Zmień go na następujący wiersz:  

     **&lt;DataSourceView xmlns = "http://schemas.microsoft.com/analysisservices/2003/engine" xmlns:xsi = "RelationalDataSourceView"\>**  

5.  Skopiuj cała zawartość pliku do schowka systemu Windows.  

6.  Zamknij plik *&lt;Nazwa modelu\>***.dsv**.  

7.  W pliku *&lt;Nazwa modelu\>***.smdl**, zlokalizuj trzy ostatnie wiersze pliku, które znajdują się w następujący sposób:  

     `</Entity>`  

     `</Entities>`  

     `</SemanticModel>`  

8.  Wklej zawartość pliku  *&lt;Nazwa modelu\>** *.dsv** bezpośrednio przed ostatnim wierszem pliku (**&lt;SemanticModel\>**).  

9. Zapisz i zamknij plik *&lt;Nazwa modelu\>***.smdl**.  

10. Skopiuj plik  *&lt;Nazwa modelu\>** *.smdl** do folderu *% programfiles %* \Microsoft Configuration Manager\AdminConsole\XmlStorage\Other na konfiguracji Menedżer serwera lokacji.  

    > [!IMPORTANT]  
    >  Po skopiowaniu pliku modelu raportu na serwerze lokacji programu Configuration Manager, należy zamknąć i ponownie uruchomić konsolę programu Configuration Manager zanim można użyć danego modelu raportu w **Kreatora tworzenia raportu**.  
