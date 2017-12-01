---
title: "Repliki bazy danych punktu zarządzania"
titleSuffix: Configuration Manager
description: "Użyj repliki bazy danych, aby zmniejszyć obciążenie procesora CPU umieszczone na serwerze bazy danych lokacji przez punkty zarządzania."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: b06f781b-ab25-4d9a-b128-02cbd7cbcffe
caps.latest.revision: "9"
author: mstewart
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 06f03b77fd79cd7aaf02127220683bd4327ab809
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2017
---
# <a name="database-replicas-for-management-points-for-system-center-configuration-manager"></a>Repliki bazy danych dla punktów zarządzania programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Lokacje główne programu System Center Configuration Manager można użyć repliki bazy danych, aby zmniejszyć obciążenie procesora CPU umieszczone na serwerze bazy danych lokacji przez punkty zarządzania realizujące żądania od klientów usługi.  

-   Kiedy punkt zarządzania korzysta z repliki bazy danych, żąda danych od komputera z programem SQL Server hostującego replikę bazy danych zamiast od serwera bazy danych lokacji.  

-   Może to pomóc w zmniejszeniu zapotrzebowania na moc obliczeniową procesora CPU na serwerze bazy danych lokacji dzięki przeniesieniu częstych zadań przetwarzania związanych z klientami.  Przykładem częstych zadań przetwarzania dla klientów są lokacje, w których istnieje duża liczba klientów wysyłających częste żądania dotyczące zasad klienta.  


##  <a name="bkmk_Prepare"></a> Przygotowanie do korzystania z replik bazy danych  
**Informacje o replikach bazy danych dla punktów zarządzania:**  

-   Repliki to częściowe kopie bazy danych lokacji, które są replikowane do osobnego wystąpienia programu SQL Server:  

    -   Lokacje główne obsługują dedykowaną replikę bazy danych dla każdego punktu zarządzania w lokacji (lokacje dodatkowe nie obsługują replik bazy danych)  

    -   Jedna replika bazy danych może być używana przez więcej niż jeden punkt zarządzania w tej samej lokacji.  

    -   Serwer SQL może hostować wiele replik bazy danych do użycia przez różne punkty zarządzania, dopóki każda z nich jest uruchamiana w oddzielnym wystąpieniu programu SQL Server.  

-   Repliki synchronizują kopię bazy danych lokacji zgodnie z ustalonym harmonogramem z danymi opublikowanymi w tym celu przez serwer bazy danych lokacji.  

-   Punkty zarządzania można skonfigurować do korzystania z repliki podczas instalacji punktu zarządzania lub w późniejszym czasie, przez ponowne skonfigurowanie wcześniej zainstalowanego punktu zarządzania do korzystania z repliki bazy danych.  

-   Należy regularnie monitorować serwer bazy danych lokacji i każdy serwer repliki bazy danych, aby mieć pewność, że zachodzi replikacja między nimi i że wydajność serwera repliki bazy danych jest wystarczająca dla wymaganej wydajności lokacji i klientów.  

**Wymagania wstępne dotyczące replik bazy danych:**  

-   **Wymagania dotyczące programu SQL Server:**  

    -   Wystąpienie programu SQL Server hostujące replikę bazy danych musi spełniać te same wymagania co serwer bazy danych lokacji. Na serwerze repliki może być jednak uruchomiona inna wersja lub edycja programu SQL Server niż na serwerze bazy danych lokacji, o ile tylko jest to obsługiwana wersja i wydanie programu SQL Server. Aby uzyskać więcej informacji, zobacz [Obsługiwane konfiguracje programu SQL Server dla programu System Center Configuration Manager](../../../../core/plan-design/configs/support-for-sql-server-versions.md).  

    -   Usługa programu SQL Server na komputerze hostującym replikę bazy danych musi być uruchomiona za pomocą konta **System** .  

    -   Zarówno w programie SQL Server hostującym bazę danych lokacji, jak i hostującym replikę bazy danych musi być zainstalowana funkcja **replikacji programu SQL Server** .  

    -   Baza danych lokacji musi **publikować** replikę bazy danych, a każdy serwer zdalnej repliki bazy danych musi **subskrybować** publikowane dane.  

    -   Zarówno program SQL Server hostujący bazę danych lokacji, jak i hostujący replikę bazy danych należy skonfigurować do obsługi parametru **Max Text Repl Size** o wartości 2 GB. Przykład sposobu konfigurowania tej opcji dla programu SQL Server 2012 znajduje się w temacie [Konfigurowanie opcji max text repl size konfiguracji serwera](http://go.microsoft.com/fwlink/p/?LinkId=273960).  

-   **Certyfikat z podpisem własnym:** Aby skonfigurować replikę bazy danych, należy utworzyć certyfikat z podpisem własnym na serwerze repliki bazy danych i udostępnić ten certyfikat każdemu punktowi zarządzania, który będzie korzystał z tego serwera repliki bazy danych.  

    -   Ten certyfikat jest automatycznie dostępny dla punktu zarządzania zainstalowanego na serwerze repliki bazy danych.  

    -   Aby jednak udostępnić ten certyfikat zdalnym punktom zarządzania, należy go wyeksportować, a potem dodać do magazynu certyfikatów **Osoby zaufane** w zdalnym punkcie zarządzania.  

-   **Powiadomienie klienta:** Aby zapewnić obsługę powiadomień klienta z repliką bazy danych dla punktu zarządzania, należy skonfigurować komunikację między serwerem bazy danych lokacji i serwerze repliki bazy danych dla **SQL Server Service Broker**. Wymaga to:  

    -   Skonfigurowania w każdej bazie danych informacji o drugiej bazie danych  

    -   Wymiany certyfikatów między dwiema bazami danych na potrzeby bezpiecznej komunikacji  

**Ograniczenia w przypadku używania replik bazy danych:**  

-   Gdy lokacja jest skonfigurowana do publikowania replik baz danych, należy użyć następującej procedury zamiast normalnych wskazówek:  

    -   [Odinstalowywanie serwera lokacji publikującego replikę bazy danych](#BKMK_DBReplicaOps_Uninstall)  

    -   [Przenoszenie bazy danych serwera lokacji publikującej replikę bazy danych](#BKMK_DBReplicaOps_Move)  

-   **Uaktualnienia do programu System Center Configuration Manager**: Przed uaktualnieniem lokacji programu System Center 2012 Configuration Manager do programu System Center Configuration Manager, należy wyłączyć repliki bazy danych dla punktów zarządzania.  Po uaktualnieniu lokacji możesz ponownie skonfigurować repliki bazy danych dla punktów zarządzania.  

-   **Wiele replik na jednym serwerze SQL:**  Jeśli skonfigurujesz serwer repliki bazy danych jako hosta wielu replik bazy danych dla punktów zarządzania (każda replika musi być w oddzielnym wystąpieniu) należy użyć zmodyfikowanego skryptu konfiguracji (z kroku 4 z sekcji poniżej) aby zapobiec zastąpieniu certyfikatu z podpisem własnym używany przez wcześniej skonfigurowane repliki bazy danych na tym serwerze.  

##  <a name="BKMK_DBReplica_Config"></a> Konfigurowanie replik bazy danych  
Aby korzystać z konfigurowania repliki bazy danych, wymagane są następujące kroki:  

-   [Krok 1 — Konfigurowanie serwera bazy danych lokacji do publikowania repliki bazy danych](#BKMK_DBReplica_ConfigSiteDB)  

-   [Krok 2 — Konfigurowanie serwera repliki bazy danych](#BKMK_DBReplica_ConfigSrv)  

-   [Krok 3 — Konfigurowanie punktów zarządzania do korzystania z repliki bazy danych](#BKMK_DBReplica_ConfigMP)  

-   [Krok 4 — Konfigurowanie certyfikatu z podpisem własnym dla serwera repliki bazy danych](#BKMK_DBReplica_Cert)  

-   [Krok 5 — Konfigurowanie brokera usług serwera SQL dla serwera repliki bazy danych](#BKMK_DBreplica_SSB)  

###  <a name="BKMK_DBReplica_ConfigSiteDB"></a> Krok 1 — Konfigurowanie serwera bazy danych lokacji do publikowania repliki bazy danych  
 Poniższa procedura przedstawia przykład sposobu konfigurowania serwera bazy danych lokacji na komputerze z systemem Windows Server 2008 R2 pod kątem publikowania repliki bazy danych. W przypadku innej wersji systemu operacyjnego należy zapoznać się z jego dokumentacją w celu odpowiedniego dostosowania kroków poniższej procedury w razie potrzeby.  

##### <a name="to-configure-the-site-database-server"></a>Aby skonfigurować serwer bazy danych lokacji  

1.  Na serwerze bazy danych lokacji ustaw automatyczne uruchamianie programu SQL Server Agent.  

2.  Na serwerze bazy danych lokacji Utwórz lokalną grupę użytkowników o nazwie **ConfigMgr_MPReplicaAccess**. Musisz dodać do tej grupy konto komputera każdego z serwerów repliki bazy danych używanych w tej lokacji, aby umożliwić tym serwerom repliki bazy danych synchronizację z opublikowaną repliką bazy danych.  

3.  Na serwerze bazy danych lokacji skonfiguruj udział plików o nazwie **ConfigMgr_MPReplica**.  

4.  Dodaj następujące uprawnienia do **ConfigMgr_MPReplica** udziału:  

    > [!NOTE]  
    >  Jeśli program SQL Server Agent używa innego konta niż konto systemu lokalnego, zastąp nazwą tego konta wyraz SYSTEM na poniższej liście.  

    -   **Uprawnienia udziału**:  

        -   SYSTEM: **Zapisu**  

        -   ConfigMgr_MPReplicaAccess: **Odczyt**  

    -   **Uprawnienia NTFS**:  

        -   SYSTEM: **Pełna kontrola**  

        -   ConfigMgr_MPReplicaAccess: **Odczyt**, **odczytu & wykonać**, **wyświetlanie zawartości folderu**  

5.  Za pomocą programu **SQL Server Management Studio** połącz się z bazą danych lokacji i uruchom następującą procedurę składowaną jako zapytanie: **spCreateMPReplicaPublication**  

Po ukończeniu działania procedury składowanej serwer bazy danych lokacji będzie skonfigurowany do publikowania repliki bazy danych.  

###  <a name="BKMK_DBReplica_ConfigSrv"></a> Krok 2 — Konfigurowanie serwera repliki bazy danych  
Serwer repliki bazy danych to komputer, na którym działa program SQL Server i który jest hostem repliki bazy danych lokacji przeznaczonej na użytek punktów zarządzania. Zgodnie z ustalonym harmonogramem serwer repliki bazy danych synchronizuje własną kopię bazy danych z repliką bazy danych opublikowaną przez serwer bazy danych lokacji.  

Serwer repliki bazy danych musi spełniać te same wymagania co serwer bazy danych lokacji. Na serwerze repliki bazy danych może jednak być uruchomiona inna edycja czy też wersja programu SQL Server niż ta, z której korzysta serwer bazy danych lokacji. Informacje o obsługiwanych wersjach programu SQL Server można znaleźć w temacie [Obsługiwane konfiguracje programu SQL Server dla programu System Center Configuration Manager](../../../../core/plan-design/configs/support-for-sql-server-versions.md).  

> [!IMPORTANT]  
>  Usługa SQL Server na komputerze hostującym replikę bazy danych musi być uruchomiona za pomocą konta System.  

Poniższa procedura przedstawia przykład sposobu konfigurowania serwera repliki bazy danych na komputerze z systemem Windows Server 2008 R2. W przypadku innej wersji systemu operacyjnego należy zapoznać się z jego dokumentacją w celu odpowiedniego dostosowania kroków poniższej procedury w razie potrzeby.  

##### <a name="to-configure-the-database-replica-server"></a>Aby skonfigurować serwer repliki bazy danych  

1.  Na serwerze repliki bazy danych ustaw automatyczne uruchamianie programu SQL Server Agent.  

2.  Na serwerze repliki bazy danych za pomocą programu **SQL Server Management Studio** połącz się z serwerem lokalnym, w trybie przeglądania przejdź do folderu **Replikacja** , kliknij pozycję Subskrypcje lokalne i wybierz opcję **Nowe subskrypcje** , aby uruchomić **Kreatora nowej subskrypcji**:  

    1.  Na stronie **Publikacja** w polu listy **Wydawca** wybierz opcję **Znajdź wydawcę programu SQL Server**, wprowadź nazwę serwera bazy danych lokacji, a następnie kliknij przycisk **Połącz**.  

    2.  Wybierz **ConfigMgr_MPReplica**, a następnie kliknij przycisk **dalej**.  

    3.  Na **lokalizacja agenta dystrybucji** wybierz pozycję **Uruchom każdego agenta jako jego subskrybent (subskrypcje wciągane)**i kliknij przycisk **dalej**.  

    4.  Na stronie **Subskrybenci** wykonaj jedną z następujących czynności:  

        -   Wybierz z serwera repliki bazy danych jedną z istniejących baz danych do użycia dla repliki bazy danych, a następnie kliknij przycisk **OK**.  

        -   Wybierz opcję **Nowa baza danych** , aby utworzyć nową bazę danych dla repliki bazy danych. Na stronie **Nowa baza danych** określ nazwę bazy danych, a następnie kliknij przycisk **OK**.  

    5.  Kliknij przycisk **Dalej**, aby kontynuować.  

    6.  Na **zabezpieczenia agenta dystrybucji** strony, kliknij przycisk Właściwości **(...)**  w wierszu połączenie z subskrybentem okna dialogowego polu, a następnie skonfiguruj ustawienia zabezpieczeń dla tego połączenia.  

        > [!TIP]  
        >  Przycisk Właściwości **(...)** , znajduje się w czwartej kolumnie wyświetlanego pola.  

        **Ustawienia zabezpieczeń:**  

        -   Skonfiguruj konto, na którym uruchomiono proces agenta dystrybucji (konto procesu):  

            -   Jeśli programu SQL Server Agent działa jako system lokalny, wybierz opcję **uruchamiana na koncie usługi SQL Server Agent (to nie jest najlepszą zalecaną praktyką zabezpieczeń.)**  

            -   Jeśli program SQL Server Agent działa na innym koncie, wybierz opcję **Uruchom na następującym koncie systemu Windows**, po czym skonfiguruj to konto. Możesz określić konto systemu Windows lub konto programu SQL Server.  

            > [!IMPORTANT]  
            >  Kontu służącemu do uruchamiania agenta dystrybucji należy przyznać na użytek wydawcy uprawnienia subskrypcji wciąganej. Informacje o konfigurowaniu tych uprawnień znajdują się w temacie [Zabezpieczenia agenta dystrybucji](http://go.microsoft.com/fwlink/p/?LinkId=238463) w bibliotece TechNet poświęconej programowi SQL Server.  

        -   Dla opcji **Połącz z dystrybutorem**wybierz ustawienie **Personifikując konto procesu**.  

        -   Dla opcji **Połącz z subskrybentem**wybierz ustawienie **Personifikując konto procesu**.  

         Po skonfigurowaniu ustawień zabezpieczeń połączenia kliknij przycisk **OK** , aby je zapisać, a następnie kliknij przycisk **Dalej**.  

    7.  Na stronie **Harmonogram synchronizacji** w polu listy **Harmonogram agenta** wybierz opcję **Zdefiniuj harmonogram**, a następnie skonfiguruj **Nowy harmonogram zadania**. Ustaw częstotliwość występowania **codzienne**, powtarzanie co **5 minut**, a czas trwania na **bez daty zakończenia**. Kliknij przycisk **Dalej** , aby zapisać harmonogram, a następnie ponownie kliknij przycisk **Dalej** .  

    8.  Na **akcje kreatora** strony, zaznacz pole wyboru dla **tworzyć subskrypcje (s)**, a następnie kliknij przycisk **dalej**.  

    9. Na stronie **Zakończ pracę kreatora** kliknij przycisk **Zakończ**, a następnie kliknij przycisk **Zamknij** , aby zakończyć działanie kreatora.  

3.  Natychmiast po zakończeniu pracy Kreatora nowej subskrypcji użyj programu **SQL Server Management Studio** w celu ustanowienia połączenia z bazą danych serwera repliki bazy danych i uruchom następujące zapytanie, aby włączyć właściwość TRUSTWORTHY bazy danych:  `ALTER DATABASE <MP Replica Database Name> SET TRUSTWORTHY ON;`  

4.  Sprawdź stan synchronizacji, aby potwierdzić, że subskrypcja zakończyła się powodzeniem:  

    -   Na komputerze subskrybenta:  

        -   W programie **SQL Server Management Studio**połącz się z serwerem repliki bazy danych i rozwiń węzeł **Replikacja**.  

        -   Rozwiń węzeł **subskrypcje lokalne**, kliknij prawym przyciskiem myszy subskrypcję publikacji bazy danych lokacji, a następnie wybierz **Wyświetl stan synchronizacji**.  

    -   Na komputerze wydawcy:  

        -   W **programu SQL Server Management Studio**, połącz się z komputerem bazy danych lokacji, kliknij prawym przyciskiem myszy **replikacji** folder, a następnie wybierz **Uruchom Monitor replikacji**.  

5.  Aby włączyć integrację środowiska uruchomieniowego (języka wspólnego CLR) repliki bazy danych, należy użyć **programu SQL Server Management Studio** Połącz się z repliką bazy danych na serwerze repliki bazy danych i uruchom następującą procedurę składowaną jako zapytanie: **exec sp_configure 'clr enabled', 1; SKONFIGURUJ PONOWNIE ZA ZASTĄPIENIA**  

6.  Dla każdego punktu zarządzania wykorzystującego serwer repliki bazy danych dodaj konto komputera punktu zarządzania do lokalnej grupy **Administratorzy** na serwerze repliki bazy danych.  

    > [!TIP]  
    >  Ten krok jest zbędny w punkcie zarządzania działającym na serwerze repliki bazy danych.  

 Replika bazy danych jest teraz gotowa do użycia przez punkt zarządzania.  

###  <a name="BKMK_DBReplica_ConfigMP"></a> Krok 3 — Konfigurowanie punktów zarządzania do korzystania z repliki bazy danych  
 Korzystanie z repliki bazy danych można skonfigurować w punkcie zarządzania lokacji głównej podczas instalowania roli punktu zarządzania albo poprzez ponowną konfigurację istniejącego punktu zarządzania pod kątem użycia repliki bazy danych.  

 Do skonfigurowania punktu zarządzania pod kątem korzystania z repliki bazy danych służą następujące informacje:  

-   **Aby skonfigurować nowy punkt zarządzania:** Na **baza danych punktu zarządzania** kreatora używanego do instalacji punktu zarządzania, wybierz **korzystania z repliki bazy danych**, i określ nazwę FQDN komputera hostującego replikę bazy danych. Następnie w polu **Nazwa bazy danych lokacji programu ConfigMgr**podaj nazwę bazy danych repliki bazy danych na tym komputerze.  

-   **Aby skonfigurować wcześniej zainstalowany punkt zarządzania**: Otwórz stronę właściwości punktu zarządzania, wybierz **baza danych punktu zarządzania** wybierz opcję **korzystania z repliki bazy danych**, a następnie określ nazwę FQDN komputera hostującego replikę bazy danych. Następnie w polu **Nazwa bazy danych lokacji programu ConfigMgr**podaj nazwę bazy danych repliki bazy danych na tym komputerze.  

-   **Dla każdego punktu zarządzania, który używa repliki bazy danych**, należy ręcznie dodać konto komputera serwera punktu zarządzania **db_datareader** roli repliki bazy danych.  

Oprócz skonfigurowania punktu zarządzania pod kątem użycia serwera repliki bazy danych należy włączyć opcję **Uwierzytelnianie systemu Windows** w usłudze **IIS** w punkcie zarządzania:  

1.  Otwórz **internetowych usług informacyjnych (IIS) Manager**.  

2.  Wybierz witrynę sieci Web używaną przez punkt zarządzania i otwórz element **Uwierzytelnianie**.  

3.  Ustaw **uwierzytelniania systemu Windows** do **włączone**, a następnie Zamknij **Internet Information Services (IIS) Manager**.  

###  <a name="BKMK_DBReplica_Cert"></a> Krok 4 — Konfigurowanie certyfikatu z podpisem własnym dla serwera repliki bazy danych  
 Należy utworzyć certyfikat z podpisem własnym na serwerze repliki bazy danych i udostępnić ten certyfikat każdemu punktowi zarządzania, który będzie korzystał z tego serwera repliki bazy danych.  

 Ten certyfikat jest automatycznie dostępny dla punktu zarządzania zainstalowanego na serwerze repliki bazy danych. Aby jednak udostępnić ten certyfikat zdalnym punktom zarządzania, należy go wyeksportować, a potem dodać do magazynu certyfikatów Osoby zaufane w zdalnym punkcie zarządzania.  

 Na przykład sposobu konfigurowania certyfikatu z podpisem własnym na serwerze repliki bazy danych dla komputera z systemem Windows Server 2008 R2, należy użyć poniższych procedur. W przypadku innej wersji systemu operacyjnego należy zapoznać się z jego dokumentacją w celu odpowiedniego dostosowania kroków poniższych procedur w razie potrzeby.  

##### <a name="to-configure-a-self-signed-certificate-for-the-database-replica-server"></a>Aby skonfigurować certyfikatu z podpisem własnym dla serwera repliki bazy danych  

1.  Na serwerze repliki bazy danych otwórz wiersz polecenia programu PowerShell z uprawnieniami administracyjnymi, a następnie uruchom następujące polecenie: **set-executionpolicy UnRestricted**  

2.  Skopiuj poniższy skrypt programu PowerShell i zapisz go jako plik o nazwie **CreateMPReplicaCert.ps1**. Umieść kopię tego pliku w folderze głównym na partycji systemowej serwera repliki bazy danych.  

    > [!IMPORTANT]  
    >  W przypadku konfigurowania więcej niż jednej repliki bazy danych w pojedynczym wystąpieniu programu SQL Server dla każdej kolejnej konfigurowanej repliki należy użyć zmodyfikowanej wersji tego skryptu do wykonania tej procedury. Zobacz  [Dodatkowy skrypt dla dodatkowych replik bazy danych w jednym wystąpieniu programu SQL Server](#bkmk_supscript)  

    ```  
    # Script for creating a self-signed certificate for the local machine and configuring SQL Server to use it.  

    Param($SQLInstance)  

    $ConfigMgrCertFriendlyName = "ConfigMgr SQL Server Identification Certificate"  

    # Get local computer name  
    $computerName = "$env:computername"  

    # Get the sql server name  
    #$key="HKLM:\SOFTWARE\Microsoft\SMS\MP"  
    #$value="SQL Server Name"  
    #$sqlServerName= (Get-ItemProperty $key).$value  
    #$dbValue="Database Name"  
    #$sqlInstance_DB_Name= (Get-ItemProperty $key).$dbValue  

    $sqlServerName = [System.Net.Dns]::GetHostByName("localhost").HostName   
    $sqlInstanceName = "MSSQLSERVER"  
    $SQLServiceName = "MSSQLSERVER"  

    if ($SQLInstance -ne $Null)  
    {  
        $sqlInstanceName = $SQLInstance  
        $SQLServiceName = "MSSQL$" + $SQLInstance  
    }  

    # Delete existing cert if one exists  
    function Get-Certificate($storename, $storelocation)  
    {   
        $store=new-object System.Security.Cryptography.X509Certificates.X509Store($storename,$storelocation)   
        $store.Open([Security.Cryptography.X509Certificates.OpenFlags]::ReadWrite)   
        $store.Certificates   
    }   

    $cert = Get-Certificate "My" "LocalMachine" | ?{$_.FriendlyName -eq $ConfigMgrCertFriendlyName}   
    if($cert -is [Object])  
    {  
        $store = new-object System.Security.Cryptography.X509Certificates.X509Store("My","LocalMachine")   
        $store.Open([Security.Cryptography.X509Certificates.OpenFlags]::ReadWrite)   
        $store.Remove($cert)  
        $store.Close()  

        # Remove this cert from Trusted People too...  
        $store = new-object System.Security.Cryptography.X509Certificates.X509Store("TrustedPeople","LocalMachine")   
        $store.Open([Security.Cryptography.X509Certificates.OpenFlags]::ReadWrite)   
        $store.Remove($cert)  
        $store.Close()      
    }  

    # Create the new cert  
    $name = new-object -com "X509Enrollment.CX500DistinguishedName.1"  
    $name.Encode("CN=" + $sqlServerName, 0)  

    $key = new-object -com "X509Enrollment.CX509PrivateKey.1"  
    $key.ProviderName = "Microsoft RSA SChannel Cryptographic Provider"  
    $key.KeySpec = 1  
    $key.Length = 1024  
    $key.SecurityDescriptor = "D:PAI(A;;0xd01f01ff;;;SY)(A;;0xd01f01ff;;;BA)(A;;0x80120089;;;NS)"  
    $key.MachineContext = 1  
    $key.Create()  

    $serverauthoid = new-object -com "X509Enrollment.CObjectId.1"  
    $serverauthoid.InitializeFromValue("1.3.6.1.5.5.7.3.1")  
    $ekuoids = new-object -com "X509Enrollment.CObjectIds.1"  
    $ekuoids.add($serverauthoid)  
    $ekuext = new-object -com "X509Enrollment.CX509ExtensionEnhancedKeyUsage.1"  
    $ekuext.InitializeEncode($ekuoids)  

    $cert = new-object -com "X509Enrollment.CX509CertificateRequestCertificate.1"  
    $cert.InitializeFromPrivateKey(2, $key, "")  
    $cert.Subject = $name  
    $cert.Issuer = $cert.Subject  
    $cert.NotBefore = get-date  
    $cert.NotAfter = $cert.NotBefore.AddDays(3650)  
    $cert.X509Extensions.Add($ekuext)  
    $cert.Encode()  

    $enrollment = new-object -com "X509Enrollment.CX509Enrollment.1"  
    $enrollment.InitializeFromRequest($cert)  
    $enrollment.CertificateFriendlyName = "ConfigMgr SQL Server Identification Certificate"  
    $certdata = $enrollment.CreateRequest(0x1)  
    $enrollment.InstallResponse(0x2, $certdata, 0x1, "")  

    # Add this cert to the trusted peoples store  
    [Byte[]]$bytes = [System.Convert]::FromBase64String($certdata)  

    $trustedPeople = new-object System.Security.Cryptography.X509certificates.X509Store "TrustedPeople", "LocalMachine"  
    $trustedPeople.Open([Security.Cryptography.X509Certificates.OpenFlags]::ReadWrite)  
    $trustedPeople.Add([Security.Cryptography.X509Certificates.X509Certificate2]$bytes)  
    $trustedPeople.Close()  

    # Get thumbprint from cert  
    $sha = new-object System.Security.Cryptography.SHA1CryptoServiceProvider  
    $certHash = $sha.ComputeHash($bytes)  
    $certHashCharArray = "";  
    $certThumbprint = "";  

    # Format the bytes into a hexadecimal string  
    foreach($byte in $certHash)  
    {  
        $temp = ($byte | % {"{0:x}" -f $_}) -join ""  
        $temp = ($temp | % {"{0,2}" -f $_})  
        $certHashCharArray = $certHashCharArray+ $temp;  
    }  
    $certHashCharArray = $certHashCharArray.Replace(' ', '0');  

    # SQL needs the thumbprint in lower case  
    foreach($char in $certHashCharArray)  
    {  
        [System.String]$myString = $char;  
        $certThumbprint = $certThumbprint + $myString.ToLower();  
    }  

    # Configure SQL to use this cert  
    $path = "HKLM:\SOFTWARE\Microsoft\Microsoft SQL Server\Instance Names\SQL"  
    $subKey = (Get-ItemProperty $path).$sqlInstanceName  
    $realPath = "HKLM:\SOFTWARE\Microsoft\Microsoft SQL Server\" + $subKey + "\MSSQLServer\SuperSocketNetLib"  
    $certKeyName = "Certificate"  
    Set-ItemProperty -path $realPath -name $certKeyName -Type string -Value $certThumbprint  

    # restart sql service  
    Restart-Service $SQLServiceName -Force  
    ```  

3.  Na serwerze repliki bazy danych uruchom następujące polecenie, które dotyczy konfiguracji programu SQL Server:  

    -   Aby użyć domyślnego wystąpienia programu SQL Server: Kliknij prawym przyciskiem myszy plik **CreateMPReplicaCert.ps1** i wybierz **Uruchom przy użyciu programu PowerShell**. Po uruchomieniu skryptu, tworzy certyfikat z podpisem własnym i konfiguruje program SQL Server do używania certyfikatu.  

    -   Dla wystąpienia nazwanego programu SQL Server: Przy użyciu programu PowerShell Uruchom polecenie **%path%\CreateMPReplicaCert.ps1 xxxxxx** gdzie **xxxxxx** to nazwa wystąpienia programu SQL Server.  

    -   Po zakończeniu wykonywania skryptu sprawdź, czy program SQL Server Agent jest uruchomiony. Jeśli nie, uruchom ponownie program SQL Server Agent.  

##### <a name="to-configure-remote-management-points-to-use-the-self-signed-certificate-of-the-database-replica-server"></a>Aby skonfigurować punkty zarządzania zdalnego do używania certyfikatu z podpisem własnym z serwera repliki bazy danych  

1.  Na serwerze repliki bazy danych, aby wyeksportować certyfikat z podpisem własnym serwera, wykonaj następujące czynności:  

    1.  Kliknij przycisk **Start**, kliknij **Uruchom**i wpisz **mmc.exe**. W pustej konsoli kliknij menu **Plik**, a następnie kliknij polecenie **Dodaj/Usuń przystawkę**.  

    2.  W oknie dialogowym **Dodawanie lub usuwanie przystawek** wybierz z listy **Dostępne przystawki** pozycję **Certyfikaty**, a następnie kliknij przycisk **Dodaj**.  

    3.  W oknie dialogowym **Przystawka certyfikatów** wybierz pozycję **Konto komputera**, a następnie kliknij przycisk **Dalej**.  

    4.  W oknie dialogowym **Wybieranie komputera** sprawdź, czy pozycja **Komputer lokalny: (komputer, na którym uruchomiona jest ta konsola)** jest wybrana, a następnie kliknij przycisk **Zakończ**.  

    5.  W oknie dialogowym **Dodawanie lub usuwanie przystawek** kliknij przycisk **OK**.  

    6.  W konsoli rozwiń węzeł **certyfikaty (komputer lokalny)**, rozwiń węzeł **osobistych**i wybierz **certyfikaty**.  

    7.  Kliknij prawym przyciskiem myszy certyfikat o przyjaznej nazwie **ConfigMgr SQL Server Identification Certificate**, kliknij przycisk **wszystkie zadania**, a następnie wybierz **wyeksportować**.  

    8.  Ukończ pracę **Kreatora eksportu certyfikatu** , używając domyślnych opcji, a następnie zapisz certyfikat z rozszerzeniem nazwy pliku **.cer** .  

2.  Na komputerze punktu zarządzania, aby dodać certyfikat z podpisem własnym dla serwera repliki bazy danych do magazynu certyfikatów Zaufane osoby w punkcie zarządzania, należy wykonać następujące czynności:  

    1.  Powtórz poprzednie kroki od 1.a do 1.e, Aby skonfigurować **certyfikatu** przystawki MMC na komputerze punktu zarządzania.  

    2.  W konsoli rozwiń listę **Certyfikaty (komputer lokalny)**, rozwiń opcję **Zaufane osoby**, kliknij prawym przyciskiem myszy polecenie **Certyfikaty**, wybierz opcję **Wszystkie zadania**i polecenie **Importuj** . Zostanie uruchomiony **Kreator importowania certyfikatów**.  

    3.  Na stronie **Pliki do importu** wybierz certyfikat zapisany w kroku 1.h i kliknij przycisk **Dalej**.  

    4.  Na stronie **Magazyn certyfikatów** wybierz opcję **Umieść wszystkie certyfikaty w następującym magazynie**, z opcją **Magazyn certyfikatów** ustawioną na **Osoby zaufane**. Następnie kliknij przycisk **Dalej**.  

    5.  Kliknij przycisk **Zakończ** , aby zamknąć kreatora i zakończyć konfigurację certyfikatu w punkcie zarządzania.  

###  <a name="BKMK_DBreplica_SSB"></a> Krok 5 — Konfigurowanie brokera usług serwera SQL dla serwera repliki bazy danych  
Aby włączyć obsługę powiadomień klienta z repliką bazy danych dla punktu zarządzania, należy skonfigurować komunikację między serwerem bazy danych lokacji i serwerem repliki bazy danych dla usługi SQL Server Service Broker. Wymaga to wprowadzenia w każdej bazie danych informacji o drugiej bazie oraz wymiany certyfikatów między dwiema bazami danych tak, co pozwoli na nawiązanie bezpiecznej komunikacji między nimi.  

> [!NOTE]  
>  Przed użyciem poniższej procedury serwer z repliką baz danych musi pomyślnie wykonać synchronizację początkową z serwerem baz danych lokacji.  

 Poniższa procedura nie modyfikuje portu usługi Service Broker skonfigurowanego w programie SQL Server dla serwera bazy danych lokacji lub serwera repliki bazy danych. Zamiast tego procedura ta konfiguruje poszczególne bazy danych pod kątem komunikacji z drugą bazą za pomocą poprawnego portu broker usługi.  

 Użyj poniższej procedury, aby skonfigurować usługę Service Broker dla serwera bazy danych lokacji i serwera repliki bazy danych.  

##### <a name="to-configure-the-service-broker-for-a-database-replica"></a>Aby skonfigurować brokera usługi dla repliki baz danych  

1.  Użyj **programu SQL Server Management Studio** można nawiązać połączenia z bazą danych serwera repliki bazy danych, a następnie uruchom następujące zapytanie, aby włączyć brokera usługi na serwerze repliki bazy danych: **ALTER DATABASE &lt;nazwa repliki bazy danych\> SET ENABLE_BROKER, HONOR_BROKER_PRIORITY na WITH ROLLBACK IMMEDIATE**  

2.  Następnie na serwerze z repliką baz danych skonfiguruj brokera usługi dla powiadomień klienta i wyeksportuj certyfikat brokera usługi. Aby to zrobić, uruchom procedurę składowaną programu SQL Server, która w ramach jednej akcji konfiguruje usługę Service Broker i eksportuje certyfikat. Po uruchomieniu procedury składowanej należy określić nazwę FQDN serwera z repliką baz danych, nazwę bazy danych z replik baz danych oraz określić lokalizację eksportu pliku certyfikatu.  

     Uruchom następującą kwerendę, aby skonfigurować wymagane szczegóły serwera repliki bazy danych i wyeksportować certyfikat serwera repliki bazy danych: **EXEC sp_BgbConfigSSBForReplicaDB '&lt;nazwa FQDN serwera SQL repliki\>","&lt;nazwa repliki bazy danych\>","&lt;ścieżka do pliku kopii zapasowej certyfikatu\>"**  

    > [!NOTE]  
    >  Jeśli serwer repliki bazy danych nie znajduje się w domyślnym wystąpieniu programu SQL Server, należy w tym kroku obok nawy bazy danych repliki podać nazwę wystąpienia. W tym celu zastąp wartość **&lt;nazwa bazy danych repliki\>** wartością **&lt;nazwa wystąpienia\\nazwa bazy danych repliki\>**.  

     Po wyeksportowaniu certyfikatu z serwera z repliką baz danych umieść kopię certyfikatu na serwerze baz danych w lokacjach głównych.  

3.  Użyj programu **SQL Server Management Studio** , aby połączyć się z bazą danych lokacji głównej. Po połączeniu się z bazą danych lokacji głównych, uruchom zapytanie, które pozwoli zaimportować certyfikat oraz określić port brokera usługi używany w serwerze z repliką bazy danych, nazwą FQDN serwera z repliką baz danych oraz nazwę bazy danych na serwerze z repliką baz danych. Pozwoli to na skonfigurowanie baz danych lokacji głównych pod kątem wykorzystania brokera usługi do komunikacji z bazami danych z serwera z repliką baz danych.  

     Uruchom następującą kwerendę, aby zaimportować certyfikat z serwera repliki bazy danych, podając wymagane szczegóły: **EXEC sp_BgbConfigSSBForRemoteService 'REPLICA', '&lt;Port brokera usługi SQL\>","&lt;ścieżka do pliku certyfikatu\>","&lt;nazwa FQDN serwera SQL repliki\>","&lt;nazwa repliki bazy danych\>"**  

    > [!NOTE]  
    >  Jeśli serwer repliki bazy danych nie znajduje się w domyślnym wystąpieniu programu SQL Server, należy w tym kroku obok nawy bazy danych repliki podać nazwę wystąpienia. Aby to zrobić, Zamień  **&lt;nazwa repliki bazy danych\>**  z **nazwa \Instance\\nazwa repliki bazy danych\>**.  

4.  Następnie na serwerze bazy danych lokacji, uruchom następujące polecenie, aby wyeksportować certyfikat serwera bazy danych lokacji: **EXEC sp_BgbCreateAndBackupSQLCert '&lt;ścieżka do pliku kopii zapasowej certyfikatu\>"**  

     Po wyeksportowaniu certyfikatu z serwera baz danych lokacji umieść kopię certyfikatu na serwerze z repliką baz danych.  

5.  Użyj programu **SQL Server Management Studio** , aby połączyć się z bazą danych serwera repliki bazy danych. Po połączeniu się z bazą danych na serwerze z repliką baz danych, uruchom zapytanie, które pozwoli zaimportować certyfikat oraz określić kod lokacji dla lokacji głównej i port brokera usługi używany przez serwer baz danych lokacji. Pozwoli to na skonfigurowanie serwera z repliką baz danych pod kątem wykorzystania brokera usługi do komunikacji z bazą danych w lokacji głównej.  

     Uruchom następującą kwerendę, aby zaimportować certyfikat z serwera bazy danych lokacji: **EXEC sp_BgbConfigSSBForRemoteService '&lt;kod lokacji\>","&lt;Port brokera usługi SQL\>","&lt;ścieżka do pliku certyfikatu\>"**  

 Kilka minut po skonfigurowaniu baz danych lokacji głównej oraz serwera z repliką baz danych menedżer powiadomień w lokacji głównej ustawia w brokerze usługi konwersację obejmującą przesyłanie powiadomień klienta z baz danych lokacji głównej do repliki baz danych.  

###  <a name="bkmk_supscript"></a> Dodatkowy skrypt dla dodatkowych replik bazy danych w jednym wystąpieniu programu SQL Server  
 Użycie skryptu z kroku 4 do konfigurowania certyfikatu z podpisem własnym dla serwera repliki bazy danych na serwerze SQL Server, który ma już zaplanować kontynuować korzystanie z repliki bazy danych, należy użyć zmodyfikowanej wersji oryginalnego skryptu. Poniższe modyfikacje uniemożliwiają skryptowi usunięcie istniejącego certyfikatu na serwerze i powodują utworzenie kolejnych certyfikatów z unikatowymi przyjaznymi nazwami.  Edytuj oryginalny skrypt w następujący sposób:  

-   Oznacz jako komentarz (uniemożliwiając wykonanie) każdy wiersz między wpisami skryptu **# usunąć istniejącego certyfikatu, jeśli istnieje** i **# utworzyć nowego certyfikatu**. Aby to zrobić, dodaj znak **#** na początku każdego wiersza, którego to dotyczy.  

-   Dla każdej kolejnej repliki bazy danych konfigurowanej przy użyciu tego skryptu zaktualizuj przyjazną nazwę certyfikatu.  Aby to zrobić, Edytuj wiersz **$enrollment. CertificateFriendlyName = "ConfigMgr SQL Server Identification Certificate"** i Zastąp **ConfigMgr SQL Server Identification Certificate** pod nową nazwą, takich jak **Certificate1 identyfikacji serwera SQL programu ConfigMgr**.  

##  <a name="BKMK_DBReplicaOps"></a> Zarządzanie konfiguracjami repliki bazy danych  
 W przypadku używania repliki bazy danych w lokacji, skorzystaj z informacji w poniższych sekcjach, aby uzupełnić proces odinstalowywania repliki bazy danych, odinstalowywania lokacji używającej repliki bazy danych lub przenoszenia bazy danych lokacji do nowej instalacji programu SQL Server. Wykorzystując informacje z poniższych sekcji do usunięcia publikacji, należy użyć wskazówek dotyczących usuwania replikacji transakcyjnej dla wersji programu SQL Server używanej w replice baz danych. Na przykład, jeśli używasz programu SQL Server 2008 R2, zobacz [jak: Usuwanie publikacji (Programowanie replikacji Transact-SQL)](http://go.microsoft.com/fwlink/p/?LinkId=273934).  

> [!NOTE]  
>  Po przywróceniu baz danych lokacji skonfigurowanych pod kątem replik baz danych przed użyciem tych replik należy ponownie skonfigurować każdą replikę baz danych, tworząc jeszcze raz zarówno publikacje, jak i subskrypcje.  

###  <a name="BKMK_UninstallDbReplica"></a> Odinstalowywanie repliki bazy danych  
 Podczas używania repliki baz danych z punktu zarządzania konieczne może być odinstalowanie repliki baz danych na pewien czas i ponowne jej skonfigurowanie. Na przykład należy usunąć repliki bazy danych przed uaktualnieniem lokacji programu Configuration Manager do nowego dodatku service pack. Po zakończeniu uaktualnienia lokacji możliwe jest przywrócenie repliki baz danych.  

 Aby odinstalować replikę baz danych, wykonaj następujące czynności.  

1.  W **administracji** obszaru roboczego w konsoli programu Configuration Manager, rozwiń węzeł **konfiguracja lokacji**, a następnie wybierz pozycję **serwery i role systemu lokacji**, a następnie w okienku szczegółów wybierz serwer systemu lokacji hostujący punkt zarządzania, który używa odinstalowywanej repliki bazy danych.  

2.  W okienku **Role systemu lokacji** kliknij prawym przyciskiem myszy pozycję **Punkt zarządzania** i wybierz polecenie **Właściwości**.  

3.  Na karcie **Baza danych punktu zarządzania** wybierz opcję **Użyj bazy danych lokacji** w celu skonfigurowania punktu zarządzania tak, aby używał bazy danych lokacji, a nie repliki bazy danych. Następnie kliknij przycisk **OK** , aby zapisać konfigurację.  

4.  Następnie wykonaj następujące zadania za pomocą programu **SQL Server Management Studio** :  

    -   Usuń publikację repliki baz danych z bazy danych serwera lokacji.  

    -   Usuń subskrypcję repliki baz danych z serwera z repliką baz danych.  

    -   Usuń replikę bazy danych z serwera z repliką baz danych.  

    -   Wyłącz publikowanie i dystrybucję na serwerze baz danych lokacji. Aby wyłączyć publikowanie i dystrybucję, kliknij prawym przyciskiem myszy folder Replikacja i kliknij przycisk **wyłącz publikowanie i dystrybucję**.  

5.  Po usunięciu publikacji, subskrypcji, baz danych repliki i wyłączeniu publikacji na serwerze baz danych lokacji replika baz danych jest odinstalowana.  

###  <a name="BKMK_DBReplicaOps_Uninstall"></a> Odinstalowywanie serwera lokacji publikującego replikę bazy danych  
 Przed odinstalowaniem lokacji publikującej replikę bazy danych wykonaj następujące czynności, aby usunąć publikację i wszystkie subskrypcje.  

1.  Za pomocą programu **SQL Server Management Studio** usuń publikację repliki bazy danych z bazy danych serwera lokacji.  

2.  Za pomocą programu **SQL Server Management Studio** usuń subskrypcję repliki bazy danych z każdego zdalnego programu SQL Server, który hostuje replikę bazy danych dla danej lokacji.  

3.  Odinstaluj lokację.  

###  <a name="BKMK_DBReplicaOps_Move"></a> Przenoszenie bazy danych serwera lokacji publikującej replikę bazy danych  
 W celu przeniesienia bazy danych lokacji na nowy komputer, wykonaj następujące czynności:  

1.  Za pomocą programu **SQL Server Management Studio** usuń publikację repliki bazy danych z bazy danych serwera lokacji.  

2.  Za pomocą programu **SQL Server Management Studio** usuń subskrypcję repliki bazy danych z każdego serwera z repliką bazy danych dla danej lokacji.  

3.  Przenieś bazę danych na nowy komputer z programem SQL Server. Aby uzyskać więcej informacji, zobacz sekcję [Modyfikowanie konfiguracji bazy danych lokacji](../../../../core/servers/manage/modify-your-infrastructure.md#bkmk_dbconfig) w temacie [Modyfikowanie infrastruktury programu System Center Configuration Manager](../../../../core/servers/manage/modify-your-infrastructure.md).  

4.  Utwórz ponownie publikację repliki bazy danych na serwerze z bazami danych lokacji. Aby uzyskać więcej informacji, zobacz [Krok 1 — Konfigurowanie serwera bazy danych lokacji do publikowania repliki bazy danych](#BKMK_DBReplica_ConfigSiteDB) w tym temacie.  

5.  Utwórz ponownie subskrypcje repliki baz danych na każdym serwerze z repliką baz danych. Aby uzyskać więcej informacji, zobacz [Krok 2 — Konfigurowanie serwera repliki bazy danych](#BKMK_DBReplica_ConfigSrv) w tym temacie.  
