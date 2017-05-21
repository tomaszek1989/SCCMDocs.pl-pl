---
title: Konfigurowanie raportowania | Dokumentacja firmy Microsoft
description: "Więcej informacji o sposobie konfigurowania raportowania w hierarchii programu Configuration Manager, w tym informacje na temat programu SQL Server Reporting Services."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 55ae86a7-f0ab-4c09-b4da-89cd0e7fa0e0
caps.latest.revision: 6
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 10b1010ccbf3889c58c55b87e70b354559243c90
ms.openlocfilehash: aed95333b6509b0aa7061f23969381f1ce8aff7f
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="configuring-reporting-in-system-center-configuration-manager"></a>Konfigurowanie raportowania w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Przed tworzyć, modyfikować i uruchamiać raporty w konsoli programu System Center Configuration Manager, należy wykonać kilka zadań konfiguracyjnych. Użyj poniższe sekcje w tym temacie ułatwiają konfigurowanie raportowania w hierarchii programu Configuration Manager:  

 Przed przystąpieniem do instalacji i konfiguracji usług Reporting Services w hierarchii, przejrzyj następujące tematy dotyczące raportowania Menedżera konfiguracji:  

-   [Wprowadzenie do raportowania w programie System Center Configuration Manager](../../../core/servers/manage/introduction-to-reporting.md)  

-   [Planowanie raportowania w programie System Center Configuration Manager](../../../core/servers/manage/planning-for-reporting.md)  

##  <a name="BKMK_SQLReportingServices"></a> SQL Server Reporting Services  
 SQL Server Reporting Services to platforma raportowania oparta na serwerze obejmująca kompleksowe funkcje raportowania w zakresie różnych źródeł danych. Punkt usług raportowania w programie Configuration Manager komunikuje się z programu SQL Server Reporting Services do kopiowania raportów programu Configuration Manager do określonego folderu raportów, aby skonfigurować ustawienia usług Reporting Services i skonfigurować ustawień zabezpieczeń usług Reporting Services. Usługi Reporting Services nawiązuje połączenie z bazą danych lokacji programu Configuration Manager do pobierania danych zwracanych podczas uruchamiania raportów.  

 Przed zainstalowaniem punktu usług raportowania w lokacji programu Configuration Manager, należy zainstalować i skonfigurować w systemie lokacji, który jest hostem roli systemu lokacji punktu usług raportowania SQL Server Reporting Services. Informacje o instalowaniu usług Reporting Services znajdują się w [SQL Server TechNet Library (Bibliotece TechNet poświęconej programowi SQL Server)](http://go.microsoft.com/fwlink/p/?LinkId=266389).  

 Poniższa procedura służy do weryfikacji, czy usługi SQL Server Reporting Services są zainstalowane i działają prawidłowo.  

#### <a name="to-verify-that-sql-server-reporting-services-is-installed-and-running"></a>Aby zweryfikować, czy usługi SQL Server Reporting Services są zainstalowane i działają  

1.  Na pulpicie kliknij przycisk **Start**, a następnie kliknij kolejno pozycje **Wszystkie programy**, **Microsoft SQL Server 2008 R2**, **Narzędzia konfiguracji**i **Reporting Services Configuration Manager**.  

2.  W oknie dialogowym **Połączenia konfiguracji usług Reporting Services** określ nazwę serwera-hosta usług SQL Server Reporting Services, wybierz z menu wystąpienie programu SQL Server z zainstalowanymi usługami SQL Reporting Services, a następnie kliknij przycisk **Połącz**. Otworzy się Menedżer konfiguracji usług Reporting Services.  

3.  Na stronie **Stan serwera raportów** sprawdź, że opcja **Stan usługi raportów** ma ustawioną wartość **Uruchomiono**. Jeśli nie, kliknij przycisk **Uruchom**.  

4.  Na stronie **Adres URL usługi sieci Web** kliknij adres URL w grupie **Adresy URL usługi sieci Web Usługi raportów** , aby przetestować połączenie z folderem raportów. Może otworzyć się okno dialogowe **Zabezpieczenia systemu Windows** z monitem o poświadczenia zabezpieczeń. Domyślnie wyświetlane jest w nim konto użytkownika. Wprowadź hasło i kliknij przycisk **OK**. Sprawdź, czy strona sieci Web otwiera się pomyślnie. Zamknij okno przeglądarki.  

5.  Na stronie **Baza danych** sprawdź, że opcja **Tryb serwera raportów** ma ustawioną wartość **Macierzysty**.  

6.  Na stronie **Adres URL Menedżera raportów** kliknij adres URL w grupie **Identyfikacja lokacji menedżera raportów** , aby przetestować połączenie z katalogiem wirtualnym menedżera raportów. Może otworzyć się okno dialogowe **Zabezpieczenia systemu Windows** z monitem o poświadczenia zabezpieczeń. Domyślnie wyświetlane jest w nim konto użytkownika. Wprowadź hasło i kliknij przycisk **OK**. Sprawdź, czy strona sieci Web otwiera się pomyślnie. Zamknij okno przeglądarki.  

    > [!NOTE]  
    >  Menedżer raportów usług Reporting Services nie jest wymagany do raportowania w programie Configuration Manager, ale jest wymagany, jeśli chcesz uruchamiać raporty w przeglądarce internetowej lub zarządzać raportami za pomocą Menedżera raportów.  

7.  Kliknij przycisk **zakończenia** zamknąć Reporting Services Configuration Manager.  

##  <a name="BKMK_ReportBuilder3"></a> Konfigurowanie raportowania do korzystania z programu Report Builder 3.0  

#### <a name="to-change-the-report-builder-manifest-name-to-report-builder-30"></a>Aby zmienić nazwę manifestu programu Report Builder na Report Builder 3.0  

1.  Na komputerze z konsolą programu Configuration Manager Otwórz Edytor rejestru systemu Windows.  

2.  Przejdź do gałęzi **HKEY_LOCAL_MACHINE/SOFTWARE/Wow6432Node/Microsoft/ConfigMgr10/AdminUI/Reporting**.  

3.  Dwukrotnie kliknij klucz **ReportBuilderApplicationManifestName** w celu edycji danych jego wartości.  

4.  Zmień **ReportBuilder_2_0_0_0.application** na **ReportBuilder_3_0_0_0.application**, a następnie kliknij przycisk **OK**.  

5.  Zamknij Edytor rejestru systemu Windows.  

##  <a name="BKMK_InstallReportingServicesPoint"></a> Instalowanie punktu usług raportowania  
 W celu zarządzania raportami w lokacji musi być w niej zainstalowany punkt usług raportowania. Punkt usług raportowania kopiuje foldery raportów i raporty do usług SQL Server Reporting Services, stosuje zasady zabezpieczeń do raportów i folderów oraz ustawia opcje konfiguracji w usługach Reporting Services. Punkt usług raportowania należy skonfigurować przed raporty są wyświetlane w konsoli programu Configuration Manager, aby można było zarządzać raportami w programie Configuration Manager. Punkt usług raportowania to rola systemu lokacji, która musi być skonfigurowana na serwerze z zainstalowanymi i uruchomionymi usługami Microsoft SQL Server Reporting Services. Aby uzyskać więcej informacji dotyczących wymagań wstępnych, zobacz [warunki wstępne dotyczące raportowania](prerequisites-for-reporting.md).  

> [!IMPORTANT]  
>  Wybierając lokację do zainstalowania punktu usług raportowania, należy pamiętać, że użytkownicy uzyskujący dostęp do raportów muszą być objęci tym samym zakresem zabezpieczeń, co lokacja, w której został zainstalowany punkt usług raportowania.  

> [!IMPORTANT]  
>  Po zainstalowaniu punktu usług raportowania w systemie lokacji nie należy zmieniać adresu URL serwera raportów. Na przykład jeśli utworzyć punkt usług raportowania, a następnie w Reporting Services Configuration Manager zmodyfikujesz adres URL serwera raportów, konsoli programu Configuration Manager będzie nadal używać starego adresu URL i będzie mógł uruchamiania, edytowania lub tworzenia raportów z poziomu konsoli. Jeżeli musisz zmienić adres URL serwera raportów, to usuń punkt usług raportowania, zmień adres URL, a potem ponownie zainstaluj punkt usług raportowania.  

 Aby zainstalować punkt usług raportowania, należy wykonać poniższe czynności.  

#### <a name="to-install-the-reporting-services-point-on-a-site-system"></a>Aby zainstalować punkt usług raportowania w systemie lokacji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  W obszarze roboczym **Administracja** rozwiń węzeł **Konfiguracja lokacji**, a następnie kliknij przycisk **Serwery i role systemu lokacji**.  

    > [!TIP]  
    >  Aby wyświetlić listę z wyłącznie tymi systemami lokacji, które hostują rolę lokacji punktu usług raportowania, kliknij prawym przyciskiem myszy polecenie **Serwery i role systemu lokacji** i wybierz polecenie **Punkt usług raportowania**.  

3.  Dodaj rolę systemu lokacji punktu usług raportowania do nowego lub istniejącego serwera systemu lokacji, wykonując odpowiednie czynności:  

    > [!NOTE]  
    >  Aby uzyskać więcej informacji o konfigurowaniu systemów lokacji, zobacz [Dodaj role systemu lokacji programu System Center Configuration Manager](../deploy/configure/add-site-system-roles.md).  

    -   **Nowy system lokacji**: Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz serwer systemu lokacji**. Otworzy się **Kreator tworzenia serwera systemu lokacji** .  

    -   **Istniejący system lokacji**: Kliknij serwer, na którym chcesz zainstalować rolę systemu lokacji punktu usług raportowania. Po kliknięciu serwera w okienku wyników wyświetli się lista ról systemu lokacji zainstalowanych już na serwerze.  

         Na karcie **Narzędzia główne** w grupie **Serwer** kliknij przycisk **Dodaj rolę systemu lokacji**. Otworzy się **Kreator dodawania ról systemu lokacji** .  

4.  Na stronie **Ogólne** określ ustawienia ogólne serwera systemu lokacji. Dodając punkt usług raportowania do istniejącego serwera systemu lokacji, sprawdź skonfigurowane na nim wcześniej wartości.  

5.  Na stronie **Wybór roli systemu** wybierz z listy dostępnych ról element **Punkt usług raportowania** , a następnie kliknij przycisk **Dalej**.  

6.  Na stronie **Punkt usług raportowania** skonfiguruj następujące ustawienia:  

    -   **Nazwa serwera bazy danych lokacji**: Określ nazwę serwera, który obsługuje bazę danych lokacji programu Configuration Manager. Przeważnie kreator automatycznie pobiera w pełni kwalifikowaną nazwę domeny (FQDN) dla serwera. Aby określić wystąpienie bazy danych, użyj formatu &lt; *nazwa serwera*>\&lt; *Nazwa wystąpienia*>.  

    -   **Nazwa bazy danych**: Określ nazwę bazy danych lokacji programu Configuration Manager, a następnie kliknij przycisk **Sprawdź** o potwierdzenie, że kreator ma dostęp do bazy danych lokacji.  

        > [!IMPORTANT]  
        >  Konto użytkownika tworzące punkt usług raportowania musi mieć dostęp do bazy danych lokacji z uprawnieniami **Odczyt** . Jeśli test połączenia nie powiedzie się, pojawi się czerwona ikona ostrzeżenia. Aby przeczytać szczegółowe informacje o tej awarii, przesuń kursor nad ikonę. Skoryguj awarię i kliknij ponownie przycisk **Testuj** .  

    -   **Nazwa folderu**: Określ nazwę folderu, który jest tworzony i używany do obsługi raporty programu Configuration Manager w usługach Reporting Services.  

    -   **Wystąpienie serwera usług Reporting Services**: Zaznacz na liście wystąpienia programu SQL Server dla usług Reporting Services. Jeśli zostanie znalezione tylko jedno wystąpienie, to zostanie ono domyślnie wymienione na liście i wybrane. Jeśli nie zostaną znalezione żadne wystąpienia, upewnij się, że usługi SQL Server Reporting Services są zainstalowane i skonfigurowane oraz że usługa SQL Server Reporting Services jest uruchomiona w systemie lokacji.  

        > [!IMPORTANT]  
        >  Menedżer konfiguracji nawiązuje połączenie w kontekście bieżącego użytkownika do Instrumentacji zarządzania Windows (WMI) do pobrania wystąpienia programu SQL Server dla usług Reporting Services w systemie wybranej lokacji. Bieżący użytkownik musi mieć uprawnienia dostępu **Odczyt** do Instrumentacji zarządzania Windows w systemie lokacji, inaczej wystąpień usług Reporting Services nie uda się pobrać.  

    -   **Konto punktu usług raportowania**: Kliknij przycisk **ustawić**, i wybierz konto do użycia, gdy punkt usług SQL Server Reporting Services na raportowania nawiążą połączenie z bazą danych lokacji programu Configuration Manager w celu pobrania danych wyświetlanych w raporcie. Wybierz **istniejące konto** do określenia konta użytkownika systemu Windows, który wcześniej został skonfigurowany jako konto programu Configuration Manager lub wybierz **nowe konto** do określenia konta użytkownika systemu Windows, który nie jest obecnie skonfigurowany jako konto programu Configuration Manager. Menedżer konfiguracji automatycznie udziela określonemu użytkownikowi dostępu do bazy danych lokacji. Użytkownik zostanie wyświetlony w podfolderze **Konta** węzła **Zabezpieczenia** w obszarze roboczym **Administracja** z nazwą konta **Punkt usług raportowania programu ConfigMgr** .  

         Konto, z którego są uruchamiane usługi Reporting Services, musi należeć do lokalnej grupy zabezpieczeń domeny **Grupa dostępu autoryzacji systemu Windows**i mieć uprawnienie **Odczyt tokenGroupsGlobalAndUniversal** ustawione na **Zezwalaj**.  

         Konto użytkownika systemu Windows i hasło do niego są szyfrowane i przechowywane w bazie danych usługi Reporting Services. Za pomocą tego konta i hasła usługa Reporting Services pobiera dane do raportów z bazy danych lokacji.  

        > [!IMPORTANT]  
        >  Określone tutaj konto musi mieć uprawnienia **Logowanie lokalne** do komputera-hosta bazy danych usług Reporting Services.  

7.  Na stronie **Punkt usług raportowania** kliknij przycisk **Dalej**.  

8.  Na stronie **Podsumowanie** zweryfikuj ustawienia, a następnie kliknij przycisk **Dalej** , aby zainstalować punkt usług raportowania.  

     Po ukończeniu pracy kreatora są tworzone foldery raportów i raporty programu Configuration Manager są kopiowane do folderów określonego raportu.  

    > [!NOTE]  
    >  Gdy są tworzone foldery raportów i raporty są kopiowane do serwera raportów, Configuration Manager ustala odpowiedni język dla obiektów. Jeśli powiązany pakiet języka jest zainstalowany w lokacji, programu Configuration Manager tworzy obiekty w języku systemu operacyjnego uruchomionego na serwerze raportów w witrynie. Jeśli ten język jest niedostępny, raporty są tworzone i wyświetlane w języku angielskim. W przypadku instalowania punktu usług raportowania w lokacji bez pakietów językowych raporty są także instalowane w języku angielskim. Jeśli pakiet językowy zostanie zainstalowany po instalacji punktu usług raportowania, to aby raporty stały się dostępne w odpowiednim języku z pakietu językowego, należy odinstalować punkt usług raportowania i zainstalować go ponownie. Aby uzyskać więcej informacji o pakietach językowych, zobacz [pakietów językowych w programie System Center Configuration Manager](../deploy/install/language-packs.md).  

###  <a name="BKMK_FileInstallationAndSecurity"></a> Instalacja plików i uprawnienia zabezpieczeń do folderu raportów  
 Menedżer konfiguracji wykonuje następujące czynności, aby zainstalować punkt usług raportowania i konfiguracji usług Reporting Services:  

> [!IMPORTANT]  
>  Akcje z poniższej listy są wykonywane z wykorzystaniem poświadczeń konta skonfigurowanego pod kątem usługi SMS_Executive, które jest zazwyczaj kontem systemu lokalnego serwera lokacji.  

-   Instalacja roli lokacji punktu usług raportowania.  

-   Tworzenie źródła danych w usługach Reporting Services za pomocą składowanych poświadczeń, które zostały określone w kreatorze. To z tego konta użytkownika i hasła systemu Windows korzystają usługi Reporting Services do łączenia się z bazą danych lokacji podczas uruchamiania raportów przez użytkownika.  

-   Tworzy folder główny Menedżera konfiguracji w usługach Reporting Services.  

-   Dodanie ról zabezpieczeń **Użytkownicy raportów programu ConfigMgr** i **Administratorzy raportów programu ConfigMgr** w usługach Reporting Services.  

-   Tworzenie podfolderów i wdrożenie raportów programu Configuration Manager z %ProgramFiles%\SMS_SRSRP do usług Reporting Services.  

-   Dodaje **Użytkownicy raportów programu ConfigMgr** roli w usługach Reporting Services do folderów głównych we wszystkich kontach użytkownika w programie Configuration Manager, które mają **odczyt lokacji** prawa.  

-   Dodaje **Administratorzy raportów programu ConfigMgr** roli w usługach Reporting Services do folderów głównych we wszystkich kontach użytkownika w programie Configuration Manager, które mają **modyfikacja lokacji** prawa.  

-   Pobiera mapowanie między folderami raportów i zabezpieczonymi typami obiektu (prowadzonymi w bazie danych lokacji programu Configuration Manager) programu Configuration Manager.  

-   Konfiguruje następujące prawa u użytkowników administracyjnych w programie Configuration Manager do konkretnych folderów raportów w usługach Reporting Services:  

    -   Dodaje użytkowników i przypisuje **Użytkownicy raportów programu ConfigMgr** roli do skojarzonego folderu raportów u użytkowników administracyjnych, którzy mają **Uruchom raport** uprawnienia dla obiektów programu Configuration Manager.  

    -   Dodaje użytkowników i przypisuje **Administratorzy raportów programu ConfigMgr** roli do skojarzonego folderu raportów u użytkowników administracyjnych, którzy mają **modyfikowanie raportu** uprawnienia dla obiektów programu Configuration Manager.  

     Program Configuration Manager łączy się z usługami raportowania i ustawia uprawnienia użytkowników w folderach głównych programu Configuration Manager i usługi Reporting Services i określonych folderach raportów. Po początkowej instalacji punktu usług raportowania programu Configuration Manager łączy się z usług Reporting Services w 10 minut, aby sprawdzić, czy prawa użytkownika skonfigurowane w folderach raportów są skojarzonymi prawami, które są ustawione dla użytkowników programu Configuration Manager. Po dodaniu użytkowników lub modyfikacji praw użytkownika w folderze raportów za pomocą Menedżera raportów usług Reporting Services, programu Configuration Manager zastąpi te zmiany za pomocą przypisań opartej na rolach, przechowywany w bazie danych lokacji. Program Configuration Manager usunie także użytkowników pozbawionych uprawnień raportowania w programie Configuration Manager.  

##  <a name="BKMK_SecurityRoles"></a> Role zabezpieczeń usług Reporting Services w programie Configuration Manager  
 Podczas instalowania punktu usług raportowania programu Configuration Manager dodanie następujących ról zabezpieczeń w usługach Reporting Services:  

-   **Użytkownicy raportów programu ConfigMgr**: Użytkownicy z przypisaną tą rolą zabezpieczeń mogą uruchamiać wyłącznie raporty programu Configuration Manager.  

-   **Administratorzy raportów programu ConfigMgr**: Użytkownicy z przypisaną tą rolą zabezpieczeń mogą wykonywać wszystkie zadania związane z raportowaniem w programie Configuration Manager.  

##  <a name="BKMK_VerifyReportingServicesPointInstallation"></a> Weryfikowanie instalacji punktu usług raportowania  
 Po dodaniu roli lokacji punktu usług raportowania można sprawdzić instalację, analizując określone komunikaty o stanie i pozycje w pliku dziennika. Za pomocą poniższej procedury można sprawdzić, czy instalacji punktu usług raportowania zakończyła się pomyślnie.  

> [!WARNING]  
>  Procedurę tę można pominąć, jeśli raporty są wyświetlane w **raporty** podfolderu **raportowania** w węźle **monitorowanie** obszaru roboczego w konsoli programu Configuration Manager.  

#### <a name="to-verify-the-reporting-services-point-installation"></a>Aby zweryfikować instalację punktu usług raportowania  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W obszarze roboczym **Monitorowanie** rozwiń węzeł **Stan systemu**i kliknij polecenie **Stan składnika**.  

3.  Na liście składników kliknij polecenie **SMS_SRS_REPORTING_POINT** .  

4.  Na karcie **Narzędzia główne** w grupie **Składnik** kliknij polecenie **Pokaż komunikaty**, a następnie kliknij przycisk **Wszystkie**.  

5.  Określ datę i godzinę okresu przed instalacją punktu usług raportowania i kliknij przycisk **OK**.  

6.  Sprawdź, czy na liście występuje identyfikator komunikatu o stanie 1015. Oznacza on, że punkt usług raportowania został pomyślnie zainstalowany. Alternatywnie, można otworzyć plik Srsrp.log, znajduje się w &lt; *ścieżkę instalacji programu ConfigMgr*> \Logs i wyszukać **instalacja zakończyła się pomyślnie**.  

     W Eksploratorze Windows przejdź do &lt; *ścieżkę instalacji programu ConfigMgr*> \Logs.  

7.  Otwórz plik dziennika Srsrp.log i przeczytaj go, rozpoczynając od godziny pomyślnej instalacji punktu usług raportowania. Sprawdź, czy foldery raportów zostały utworzone, raporty zostały wdrożone i zasady zabezpieczeń we wszystkich folderach zostały potwierdzone. Znajdź wiersz **Sprawdzono kondycję usługi sieci Web SRS na serwerze** znajdujący się po ostatnim wierszu potwierdzeń zasad zabezpieczeń.  

##  <a name="BKMK_Certificate"></a> Konfigurowanie certyfikatu z podpisem własnym dla komputerów z konsolą programu Configuration Manager  
 Istnieje wiele możliwości utworzenia raportów usług SQL Server Reporting Services. Podczas tworzenia lub edytowania raportów w konsoli programu Configuration Manager, programu Configuration Manager otworzy program Report Builder do użycia jako środowisko tworzenia. Niezależnie od sposobu tworzenia raportów programu Configuration Manager certyfikatu z podpisem własnym jest wymagany do uwierzytelnienia serwera na serwerze bazy danych lokacji. Menedżer konfiguracji automatycznie instaluje certyfikat na serwerze lokacji i komputerach z zainstalowanym dostawcą programu SMS. W związku z tym można utworzyć lub edytować raporty z konsoli programu Configuration Manager uruchomionej na jednym z tych komputerów. Jednak podczas tworzenia lub modyfikowania raportów z poziomu konsoli programu Configuration Manager, który jest zainstalowany na innym komputerze, należy wyeksportować certyfikat z serwera lokacji i dodać go do **zaufane osoby** magazynu certyfikatów na komputerze, na którym jest uruchomiona konsola programu Configuration Manager.  

> [!NOTE]  
>  Więcej informacji dotyczących innych środowisk tworzenia raportów dla usług SQL Server Reporting Services znajduje się w sekcji [Porównywanie środowisk do tworzenia raportów](http://go.microsoft.com/fwlink/p/?LinkId=242805) w podręczniku programu SQL Server 2008 dostępnym w trybie online.  

 Na przykład można przetransferować kopię certyfikatu z podpisem własnym z serwera lokacji na innym komputerze, na którym jest uruchomiona konsola programu Configuration Manager, gdy oba komputery pracują w systemie Windows Server 2008 R2, należy użyć następującej procedury. Jeżeli nie można wykonać tej procedury z powodu innej wersję systemu operacyjnego, należy zapoznać się z dokumentacją systemu operacyjnego w celu uzyskania odpowiedniej procedury.  

#### <a name="to-transfer-a-copy-of-self-signed-certificate-from-the-site-server-to-another-computer"></a>Aby przetransferować kopię certyfikatu z podpisem własnym z serwera lokacji na inny komputer  

1.  Aby wyeksportować certyfikat z podpisem własnym serwera, wykonaj następujące czynności na serwerze lokacji:  

    1.  Kliknij przycisk **Start**, kliknij polecenie **Uruchom**i wpisz **mmc.exe**. W pustej konsoli kliknij menu **Plik**, a następnie kliknij polecenie **Dodaj/Usuń przystawkę**.  

    2.  W oknie dialogowym **Dodawanie lub usuwanie przystawek** wybierz z listy **Dostępne przystawki** pozycję **Certyfikaty**, a następnie kliknij przycisk **Dodaj**.  

    3.  W oknie dialogowym **Przystawka certyfikatów** wybierz pozycję **Konto komputera**, a następnie kliknij przycisk **Dalej**.  

    4.  W oknie dialogowym **Wybieranie komputera** sprawdź, czy pozycja **Komputer lokalny: (komputer, na którym uruchomiona jest ta konsola)** jest wybrana, a następnie kliknij przycisk **Zakończ**.  

    5.  W oknie dialogowym **Dodawanie lub usuwanie przystawek** kliknij przycisk **OK**.  

    6.  W konsoli rozwiń listę **Certyfikaty (komputer lokalny)**, rozwiń opcję **Zaufane osoby**i wybierz pozycję **Certyfikaty**.  

    7.  Kliknij prawym przyciskiem myszy certyfikat o przyjaznej nazwie &lt; *nazwę FQDN serwera lokacji*>, kliknij przycisk **wszystkie zadania**, a następnie wybierz **wyeksportować**.  

    8.  Ukończ pracę **Kreatora eksportu certyfikatu** , używając domyślnych opcji, a następnie zapisz certyfikat z rozszerzeniem nazwy pliku **.cer** .  

2.  Na komputerze, na którym jest uruchomiona konsola programu Configuration Manager, aby dodać certyfikat z podpisem własnym do magazynu certyfikatów Zaufane osoby, wykonaj następujące czynności:  

    1.  Powtórz poprzednie kroki od 1.a do 1.e, Aby skonfigurować **certyfikatu** w przystawce MMC na komputerze punktu zarządzania.  

    2.  W konsoli rozwiń listę **Certyfikaty (komputer lokalny)**, rozwiń opcję **Zaufane osoby**, kliknij prawym przyciskiem myszy polecenie **Certyfikaty**, wybierz opcję **Wszystkie zadania**i polecenie **Importuj** . Zostanie uruchomiony **Kreator importowania certyfikatów**.  

    3.  Na stronie **Pliki do importu** wybierz certyfikat zapisany w kroku 1.h i kliknij przycisk **Dalej**.  

    4.  Na stronie **Magazyn certyfikatów** wybierz opcję **Umieść wszystkie certyfikaty w następującym magazynie**, przy opcji **Magazyn certyfikatów** ustawionej na **Osoby zaufane**. Następnie kliknij przycisk **Dalej**.  

    5.  Kliknij przycisk **Zakończ** , aby zamknąć kreatora i zakończyć konfigurację certyfikatu na komputerze.  

##  <a name="BKMK_ModifyReportingServicesPoint"></a> Modyfikowanie ustawień punktu usług raportowania  
 Po instalacji punktu usług raportowania we właściwościach punktu usług raportowania można zmodyfikować połączenie z bazą danych lokacji i ustawienia uwierzytelniania. Aby zmodyfikować ustawienia punktu usług raportowania, wykonaj poniższą procedurę.  

#### <a name="to-modify-reporting-services-point-settings"></a>Aby zmodyfikować ustawienia punktu usług raportowania  

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  W obszarze roboczym **Administracja** rozwiń węzeł **Konfiguracja lokacji**, a następnie kliknij przycisk **Serwery i role systemu lokacji** . Pojawi się lista systemów lokacji.  

    > [!TIP]  
    >  Aby wyświetlić listę z wyłącznie tymi systemami lokacji, które hostują rolę lokacji punktu usług raportowania, kliknij prawym przyciskiem myszy polecenie **Serwery i role systemu lokacji** i wybierz polecenie **Punkt usług raportowania**.  

3.  Wybierz system lokacji hostujący punkt usług raportowania, którego ustawienia chcesz zmodyfikować, i w ustawieniu **Role systemu lokacji** wybierz polecenie **Punkt usług raportowania**.  

4.  Na karcie **Rola lokacji** w grupie **Właściwości** kliknij polecenie **Właściwości**.  

5.  W oknie dialogowym **Właściwości punktu usług raportowania** można zmodyfikować następujące ustawienia:  

    -   **Nazwa serwera bazy danych lokacji**: Określ nazwę serwera, który obsługuje bazę danych lokacji programu Configuration Manager. Przeważnie kreator automatycznie pobiera w pełni kwalifikowaną nazwę domeny (FQDN) dla serwera. Aby określić wystąpienie bazy danych, użyj formatu &lt; *nazwa serwera*>\&lt; *Nazwa wystąpienia*>.  

    -   **Nazwa bazy danych**: Określ nazwę bazy danych lokacji programu System Center 2012 Configuration Manager, a następnie kliknij przycisk **Sprawdź** o potwierdzenie, że kreator ma dostęp do bazy danych lokacji.  

        > [!IMPORTANT]  
        >  Konto użytkownika, które posłużyło do utworzenia punktu usług raportowania, musi mieć dostęp do odczytu bazy danych lokacji. Jeśli test połączenia nie powiedzie się, pojawi się czerwona ikona ostrzeżenia. Aby przeczytać szczegółowe informacje o tej awarii, przesuń kursor nad ikonę. Skoryguj awarię i kliknij ponownie przycisk **Testuj** .  

    -   **Konto użytkownika**: Kliknij przycisk **ustawić**, a następnie wybierz konto, które jest używana, gdy punkt usług SQL Server Reporting Services na raportowania łączy się z bazy danych lokacji programu Configuration Manager w celu pobrania danych wyświetlanych w raporcie. Wybierz **istniejące konto** do określenia konta użytkownika systemu Windows, uprawnieniami istniejącego programu Configuration Manager lub wybierz **nowe konto** do określenia konta użytkownika systemu Windows, który obecnie nie ma uprawnień w programie Configuration Manager. Menedżer konfiguracji automatycznie udziela określonemu użytkownikowi konta dostępu do bazy danych lokacji. Konto zostanie wyświetlone w podfolderze **Konta** , w węźle **Zabezpieczenia** obszaru roboczego **Administracja** jako **Punkt raportowania SRS programu ConfigMgr** .  

         Konto użytkownika systemu Windows i hasło do niego są szyfrowane i przechowywane w bazie danych usługi Reporting Services. Za pomocą tego konta i hasła usługa Reporting Services pobiera dane do raportów z bazy danych lokacji.  

        > [!IMPORTANT]  
        >  Gdy baza danych lokacji znajduje się w zdalnym systemie lokacji, określone konto musi mieć uprawnienie **Logowanie lokalne** w danym komputerze.  

6.  Kliknij przycisk **OK** , aby zapisać zmiany i zamknąć okno dialogowe.  

## <a name="upgrading-sql-server"></a>Uaktualnienie programu SQL Server  
 Po uaktualnieniu programu SQL Server i SQL Server Reporting Services używanej jako źródło danych dla usług raportowania, mogą występować błędy przy próbie uruchomienia lub edycji raportu z konsoli programu Configuration Manager. Aby raporty prawidłowo działały w konsoli programu Configuration Manager, musi usunąć raportowania usług punktu rolą systemu lokacji dla lokacji i zainstalować go ponownie. Po uaktualnieniu można nadal uruchamiać i edytować raporty z przeglądarki internetowej.  

##  <a name="BKMK_ConfigureReportOptions"></a> Konfigurowanie opcji raportu  
 Umożliwia wybranie domyślnego punktu usług, który jest używany do zarządzania raportami raportowania opcje raportów w lokacji programu Configuration Manager. Chociaż w jednej lokacji może istnieć więcej niż jeden punkt usług raportowania, to zarządzanie raportami może być realizowane wyłącznie przez domyślny serwer raportów wybrany w opcjach raportów. Aby skonfigurować opcje raportów w danej lokacji, użyj poniższej procedury.  

#### <a name="to-configure-report-options"></a>Aby skonfigurować opcje raportu  

1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W obszarze roboczym **Monitorowanie** rozwiń węzeł **Raportowanie**, a następnie kliknij przycisk **Raporty**.  

3.  Na karcie **Narzędzia główne** w grupie **Ustawienia** kliknij polecenie **Opcje raportu**.  

4.  Wybierz z listy domyślny serwer raportów, a następnie kliknij przycisk **OK**. Jeśli na liście nie ma żadnych punktów usług raportowania, sprawdź czy punkt usług raportowania został pomyślnie zainstalowany i skonfigurowany w danej lokacji.  

## <a name="next-steps"></a>Następne kroki
[Operacje i Obsługa raportowania](operations-and-maintenance-for-reporting.md)

