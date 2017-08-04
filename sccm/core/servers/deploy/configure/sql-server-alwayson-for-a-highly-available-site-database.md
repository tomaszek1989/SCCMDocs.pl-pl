---
title: "Zawsze włączone w programie SQL Server | Dokumentacja firmy Microsoft"
description: "Zaplanuj użycie programu SQL Server zawsze w grupie dostępności wraz z programem SCCM."
ms.custom: na
ms.date: 7/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 58d52fdc-bd18-494d-9f3b-ccfc13ea3d35
caps.latest.revision: 16
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: MT
ms.sourcegitcommit: 3c75c1647954d6507f9e28495810ef8c55e42cda
ms.openlocfilehash: c746365238e1255d73387a9496521bb03a56b21b
ms.contentlocale: pl-pl
ms.lasthandoff: 07/29/2017

---
# <a name="prepare-to-use-sql-server-always-on-availability-groups-with-configuration-manager"></a>Przygotowanie do korzystania z programu SQL Server zawsze włączonych grup dostępności z programu Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Przygotuj System Center Configuration Manager do używania programu SQL Server zawsze włączonych grup dostępności jako rozwiązanie wysokiej dostępności i odzyskiwaniem po awarii odzyskiwania bazy danych lokacji.  
Program Configuration Manager obsługuje korzystanie z grup dostępności:
-     W lokacjach głównych i centralnej lokacji administracyjnej.
-     W infrastrukturze lokalnej, lub na platformie Microsoft Azure.

Jeśli używasz grup dostępności w systemie Microsoft Azure, możesz zwiększyć dostępność bazy danych lokacji przy użyciu *zestawami dostępności Azure*. Więcej informacji o zestawach dostępności Azure zawiera temat [Manage the availability of virtual machines](https://azure.microsoft.com/documentation/articles/virtual-machines-windows-manage-availability/)(Zarządzanie dostępnością maszyn wirtualnych).

>  [!Important]   
>  Przed kontynuowaniem należy doświadczenia z konfiguracji programu SQL Server i grup dostępności programu SQL Server. Informacje poniżej odwołuje się do biblioteki dokumentacji programu SQL Server i procedur.

## <a name="supported-scenarios"></a>Scenariusze obsługiwane
Poniżej przedstawiono obsługiwane scenariusze użycia grup dostępności z programu Configuration Manager. Szczegóły i procedury dla każdego znajdują się w [Konfigurowanie grup dostępności dla programu Configuration Manager](/sccm/core/servers/deploy/configure/configure-aoag).


-      [Utwórz grupę dostępności do użytku z programem Configuration Manager](/sccm/core/servers/deploy/configure/configure-aoag#create-and-configure-an-availability-group).
-     [Konfigurowanie lokacji do używania grupy dostępności](/sccm/core/servers/deploy/configure/configure-aoag#configure-a-site-to-use-the-database-in-the-availability-group).
-     [Dodawanie lub usuwanie repliki synchroniczne członków z grupy dostępności, który jest hostem bazy danych lokacji](/sccm/core/servers/deploy/configure/configure-aoag#add-and-remove-synchronous-replica-members).
-     [Konfigurowanie replik zatwierdzania asynchronicznego](/sccm/core/servers/deploy/configure/configure-aoag#configure-an-asynchronous-commit-repilca) (wymaga programu Configuration Manager w wersji 1706 lub nowszej.)
-     [Odzyskiwanie lokacji z repliki zatwierdzania asynchronicznego](/sccm/core/servers/deploy/configure/configure-aoag#use-the-asynchronous-replica-to-recover-your-site) (wymaga programu Configuration Manager w wersji 1706 lub nowszej.)
-     [Przenieś bazy danych lokacji z grupy dostępności domyślne lub nazwane wystąpienie autonomiczny serwer SQL](/sccm/core/servers/deploy/configure/configure-aoag#stop-using-an-availability-group).


## <a name="prerequisites"></a>Wymagania wstępne
Następujące wymagania wstępne dotyczą wszystkich scenariuszy. Jeśli dodatkowe wymagania wstępne dotyczą scenariusza, te szczegóły z tym scenariuszem.   

### <a name="configuration-manager-accounts-and-permissions"></a>Konta programu Configuration Manager i uprawnień
**Serwer lokacji do dostępu do elementu członkowskiego repliki:**   
Konto komputera serwera lokacji musi być członkiem grupy **Administratorzy lokalni** na komputerze należącym do danej grupy dostępności.

### <a name="sql-server"></a>Serwer SQL
**Wersja:**  
Każdej repliki w grupie dostępności musi działać wersja programu SQL Server, która jest obsługiwana przez używaną wersję programu Configuration Manager. Jeśli są obsługiwane przez program SQL Server, różne węzły grupy dostępności, można uruchomić różnych wersji programu SQL Server.

**Wersja:**  
Należy użyć *Enterprise* wersji programu SQL Server.

**Konto:**  
Każde wystąpienie programu SQL Server można uruchomić przy użyciu konta użytkownika domeny (**konto usługi**) lub konta domeny. Każdej repliki w grupie może mieć inną konfigurację. Na [najlepsze rozwiązania programu SQL Server](/sql/sql-server/install/security-considerations-for-a-sql-server-installation#before-installing-includessnoversionincludesssnoversion-mdmd), użyj konta z najniższą możliwe uprawnienia.

-   Aby skonfigurować uprawnienia dla programu SQL Server 2016 i kont usług, zobacz [Konfigurowanie kont usług systemu Windows i uprawnienia](/sql/database-engine/configure-windows/configure-windows-service-accounts-and-permissions) w witrynie MSDN.
-   Aby użyć konta domeny, należy użyć certyfikatów. Aby uzyskać więcej informacji, zobacz [Użyj certyfikatów dla bazy danych dublowania punktu końcowego (Transact-SQL)](https://docs.microsoft.com/sql/database-engine/database-mirroring/use-certificates-for-a-database-mirroring-endpoint-transact-sql).


Aby uzyskać więcej informacji, zobacz [Tworzenie punktu końcowego dublowania bazy danych dla zawsze włączonych grup dostępności](/sql/database-engine/availability-groups/windows/database-mirroring-always-on-availability-groups-powershell).

### <a name="availability-group-configurations"></a>Konfiguracje grupy dostępności
**Elementy członkowskie repliki:**  
-   Grupa dostępności musi mieć jedną replikę podstawową.
-   Przed wersją 1706 może mieć maksymalnie dwóch synchronicznych replik pomocniczych.
-   Począwszy od wersji 1706, używając samą liczbę i rodzaj replik w grupie dostępności jako obsługiwany przez wersję programu SQL Server, którego używasz.

    Możesz użyć repliki zatwierdzania asynchronicznego, aby odzyskać repliki synchroniczne. Zobacz [opcje odzyskiwania bazy danych lokacji]( /sccm/protect/understand/backup-and-recovery#BKMK_SiteDatabaseRecoveryOption) w temacie kopii zapasowych i odzyskiwania, aby uzyskać informacje o tym.
    > [!CAUTION]  
    > Menedżer konfiguracji nie obsługuje trybu failover do korzystania z repliki zatwierdzania asynchronicznego jako bazy danych lokacji.
Ponieważ programu Configuration Manager nie można zweryfikować stanu repliki zatwierdzania asynchronicznego, aby upewnić się, że jest aktualny, i [zgodnie z założeniami takie repliki może być zsynchronizowane]( https://msdn.microsoft.com/library/ff877884(SQL.120).aspx(d=robot)#Availability%20Modes), użycie zatwierdzania asynchronicznego replika jako bazy danych lokacji można umieścić integralność danych lokacji i na ryzyko.

Każdy element członkowski repliki musi:
-   używać **wystąpienia domyślnego**;  
    *Począwszy od wersji 1702, można użyć* ***nazwane wystąpienie***.

-     Ma **połączenia w podstawową rolą** ustawioną **tak**
-     Ma **czytelny dodatkowej** ustawioną **tak**  
-     być skonfigurowana na potrzeby **ręcznej pracy awaryjnej**.      

    >  [!TIP]
    >  Obsługa programu Configuration Manager za pomocą dostępności grupy repliki synchroniczne, gdy wartość **automatycznej pracy awaryjnej**. Jednak **ręczną pracę awaryjną** musi być ustawiona podczas:
    >  -  Możesz uruchomić Instalatora, aby określić używanie bazy danych lokacji w grupie dostępności.
    >  -  Podczas instalowania wszelkich aktualizacji programu Configuration Manager (nie tylko aktualizacje, które są stosowane do bazy danych lokacji).  

**Lokalizacja elementu członkowskiego repliki:**  
Wszystkie repliki w grupie dostępności musi być obsługiwana lokalnie lub hostowanych w systemie Microsoft Azure. Grupy, która zawiera elementy członkowskie lokalnie i na platformie Azure nie jest obsługiwane.     

Po skonfigurowaniu grupy dostępności na platformie Azure i grupa jest za usługą równoważenia obciążenia wewnętrzne lub zewnętrzne, są następujące porty domyślne, należy otworzyć umożliwiające instalacji dostęp do każdej repliki:   

-     Program mapowania punktów końcowych RCP - **TCP 135**   
-     Blok komunikatów serwera — **TCP 445**  
    *Po zakończeniu przenoszenia bazy danych można usunąć tego portu. Począwszy od wersji 1702, ten port nie jest już wymagane.*
-     SQL Server Service Broker - **TCP 4022**
-     SQL przez TCP — **TCP 1433**   

Po zakończeniu instalacji następujące porty muszą pozostać dostępne:
-     SQL Server Service Broker - **TCP 4022**
-     SQL przez TCP — **TCP 1433**

Począwszy od wersji 1702, można użyć innych portów dla tych konfiguracji. Należy użyć tych samych portów, przez punkt końcowy, a na wszystkich replik w grupie dostępności.


**Odbiornik:**   
Grupa dostępności musi mieć co najmniej jeden **odbiornik grupy dostępności**. Nazwa wirtualnego tego odbiornika jest używany podczas konfigurowania programu Configuration Manager do używania bazy danych lokacji w grupie dostępności. Chociaż grupa dostępności może zawierać wiele odbiorników, Configuration Manager można tylko dokonać Użyj jednego. Zobacz [tworzenia lub konfigurowania odbiornika grupy dostępności (SQL Server)](/sql/database-engine/availability-groups/windows/create-or-configure-an-availability-group-listener-sql-server) Aby uzyskać więcej informacji.

**Ścieżki plików:**   
W przypadku należy uruchomić Instalatora programu Configuration Manager do skonfigurowania lokacji do używania bazy danych w grupie dostępności, każdy serwer repliki pomocniczej musi mieć ścieżkę pliku programu SQL Server, które jest taka sama jak ścieżka pliku dla plików bazy danych lokacji jako znajduje się w bieżącej podstawowej repliki.
-   Jeśli identyczna ścieżka nie istnieje, Instalator nie doda wystąpienia dla grupy dostępności jako nowej lokalizacji bazy danych lokacji.
-   Ponadto lokalne konto usługi programu SQL Server musi mieć **Pełna kontrola** uprawnienia do tego folderu.

Pomocnicze serwery repliki wymagają tej ścieżki pliku tylko podczas używania Instalatora, aby określić wystąpienie bazy danych w grupie dostępności. Po zakończeniu konfiguracji bazy danych lokacji w grupie dostępności, można usunąć nieużywaną ścieżkę z pomocnicze serwery repliki.

Na przykład rozważmy następujący scenariusz:
-   Można utworzyć grupy dostępności, która używa trzech serwerów SQL.

-   Twoim podstawowym serwerem repliki jest nowa instalacja programu SQL Server 2014. Domyślnie bazy danych. MDF i. Pliki LDF są przechowywane w C:\Program Files\Microsoft SQL Server\MSSQL12. MSSQLSERVER\MSSQL\DATA.

-   Oba serwery repliki pomocniczej zostały uaktualnione do programu SQL Server 2014 z poprzednich wersji i Zachowaj Oryginalna ścieżka pliku do przechowywania plików bazy danych: C:\Program Files\Microsoft SQL Server\MSSQL10. MSSQLSERVER\MSSQL\DATA.

-   Przed przystąpieniem do przenoszenia bazy danych lokacji do tej grupy dostępności, na każdym serwerze repliki pomocniczej należy utworzyć następujące ścieżki plików nawet w przypadku replik pomocniczych nie będzie używać tej lokalizacji pliku: C:\Program Files\Microsoft SQL Server\MSSQL12. MSSQLSERVER\MSSQL\DATA (jest to duplikat ścieżki, która jest używana w replice podstawowej).

-   Następnie przydziel konta usługi programu SQL Server w każdej repliki pomocniczej pełnego dostępu do lokalizacji pliku nowo utworzony na tym serwerze.

-   Teraz można pomyślnie uruchomić Instalatora programu Configuration Manager, aby skonfigurować lokację do użycia w grupie dostępności bazy danych lokacji.

**Skonfiguruj bazę danych na nowej repliki:**   
 Dla każdej repliki bazy danych musi być ustawione z następujących czynności:
-   **Integrację środowiska CLR** musi być *włączone*
-     **Maksymalny rozmiar repl** musi być *2147483647*
-     Właściciel bazy danych musi być *konta administratora systemu*
-     **TRUSTWORTY** musi być **ON**
-     **Usługa Service Broker** musi być *włączone*

Te konfiguracje mogą być wykonywane na tylko replikę podstawową. Aby skonfigurować replikę pomocniczą, należy pierwszy trybu failover serwera podstawowego na serwerze pomocniczym, aby pomocniczej, co sprawia, że pomocniczy nowej repliki podstawowej.   

Użyj dokumentacji programu SQL Server, gdy jest to konieczne skonfigurować ustawienia. Na przykład, zobacz [TRUSTWORTHY](/sql/relational-databases/security/trustworthy-database-property) lub [integrację środowiska CLR](/sql/relational-databases/clr-integration/clr-integration-enabling) w dokumentacji programu SQL Server.

### <a name="verification-script"></a>Skrypt weryfikacji
Można uruchomić następujący skrypt, aby zweryfikować konfiguracji bazy danych podstawowych i pomocniczych replik. Przed w replice pomocniczej można rozwiązać problem, należy zmienić tej repliki pomocniczej się repliką podstawową.

    SET NOCOUNT ON

    DECLARE @dbname NVARCHAR(128)

    SELECT @dbname = sd.name FROM sys.sysdatabases sd WHERE sd.dbid = DB_ID()

    IF (@dbname = N'master' OR @dbname = N'model' OR @dbname = N'msdb' OR @dbname = N'tempdb' OR @dbname = N'distribution' ) BEGIN
    RAISERROR(N'ERROR: Script is targetting a system database.  It should be targeting the DB you created instead.', 0, 1)
    GOTO Branch_Exit;
    END ELSE
    PRINT N'INFO: Targetted database is ' + @dbname + N'.'

    PRINT N'INFO: Running verifications....'

    IF NOT EXISTS (SELECT * FROM sys.configurations c WHERE c.name = 'clr enabled' AND c.value_in_use = 1)
    PRINT N'ERROR: CLR is not enabled!'
    ELSE
    PRINT N'PASS: CLR is enabled.'

    DECLARE @repltable TABLE (
    name nvarchar(max),
    minimum int,
    maximum int,
    config_value int,
    run_value int )

    INSERT INTO @repltable
    EXEC sp_configure 'max text repl size (B)'

    IF NOT EXISTS(SELECT * from @repltable where config_value = 2147483647 and run_value = 2147483647 )
    PRINT N'ERROR: Max text repl size is not correct!'
    ELSE
    PRINT N'PASS: Max text repl size is correct.'

    IF NOT EXISTS (SELECT db.owner_sid FROM sys.databases db WHERE db.database_id = DB_ID() AND db.owner_sid = 0x01)
    PRINT N'ERROR: Database owner is not sa account!'
    ELSE
    PRINT N'PASS: Database owner is sa account.'

    IF NOT EXISTS( SELECT * FROM sys.databases db WHERE db.database_id = DB_ID() AND db.is_trustworthy_on = 1 )
    PRINT N'ERROR: Trustworthy bit is not on!'
    ELSE
    PRINT N'PASS: Trustworthy bit is on.'

    IF NOT EXISTS( SELECT * FROM sys.databases db WHERE db.database_id = DB_ID() AND db.is_broker_enabled = 1 )
    PRINT N'ERROR: Service broker is not enabled!'
    ELSE
    PRINT N'PASS: Service broker is enabled.'

    IF NOT EXISTS( SELECT * FROM sys.databases db WHERE db.database_id = DB_ID() AND db.is_honor_broker_priority_on = 1 )
    PRINT N'ERROR: Service broker priority is not set!'
    ELSE
    PRINT N'PASS: Service broker priority is set.'

    PRINT N'Done!'

    Branch_Exit:

## <a name="limitations-and-known-issues"></a>Ograniczenia i znane problemy
Następujące ograniczenia mają zastosowanie do wszystkich scenariuszy.   

**Grupy dostępności podstawowych nie są obsługiwane:**  
Programu Microsoft SQL Server 2016 Standard edition [grup dostępności podstawowe](https://msdn.microsoft.com/library/mt614935.aspx) nie obsługuje dostęp do odczytu replikach pomocniczych, wymagane do użytku z programem Configuration Manager.

**Serwerami SQL, które zawierają grupy dostępności dodatkowe:**   
Przed 1610 wersji programu Configuration Manager gdy grupy dostępności na hostach programu SQL Server, co najmniej jedną grupę dostępności, oprócz używanego programu Configuration Manager, każdej repliki w każdej z tych grup dostępności dodatkowe grupy musi mieć następującą konfigurację ustawione w czasie uruchamiania Instalatora programu Configuration Manager lub instalowania aktualizacji programu Configuration Manager:
-   **ręcznej pracy awaryjnej**
-   **zezwalała na każde połączenie tylko do odczytu**

**Użyj nieobsługiwany bazy danych:**
-   **Program Configuration Manager obsługuje tylko bazy danych lokacji w grupie dostępności:** Następujące nie są obsługiwane:
    -   Baza danych raportowania
    -   Baza danych usług WSUS
-   **Istniejące bazy danych:** Nie można użyć nowej bazy danych utworzonej w replice. Zamiast tego należy przywrócić kopię istniejącej bazy danych programu Configuration Manager do repliki podstawowej, podczas konfigurowania grupy dostępności.

**Błędy instalacji w pliku ConfigMgrSetup.log:**  
Po uruchomieniu Instalatora w celu przeniesienia bazy danych lokacji do grupy dostępności, Instalator podejmuje próbę przetwarzania ról bazy danych na replikach pomocniczych grupy dostępności i rejestruje błędy podobne do następujących:
-   BŁĄD: Błąd serwera SQL: [25000] [3906] [Microsoft] [SQL Server Native klienta 11.0] [SQL Server] nie można zaktualizować bazy danych "CM_AAA", ponieważ baza danych jest tylko do odczytu. 2016-1-21 Instalatora programu Configuration Manager 4:54:59 PM 7344 (0x1CB0)  

Te błędy są bezpiecznie zignorować.

## <a name="changes-for-site-backup"></a>Zmiany dotyczące kopii zapasowej lokacji
**Pliki kopii zapasowej bazy danych:**  
Po uruchomieniu bazy danych lokacji w grupie dostępności, uruchom wbudowane **serwera kopii zapasowej lokacji** zadanie konserwacji, aby utworzyć kopię zapasową typowych ustawień programu Configuration Manager i plików. Jednak nie należy używać. MDF lub. Pliki LDF utworzonych przez tej kopii zapasowej. Zamiast tego należy wprowadzić bezpośrednich kopii zapasowych tych plików bazy danych przy użyciu programu SQL Server.

**Dziennik transakcji:**  
Model odzyskiwania bazy danych lokacji musi mieć ustawioną **pełne** (wymaganie do użytku w grupie dostępności). W tej konfiguracji należy zaplanować monitorowanie i utrzymywanie rozmiaru dziennika transakcji bazy danych lokacji. W modelu odzyskiwania pełnego transakcje nie działają w trybie zaostrzonym aż do wykonania pełnej kopii zapasowej bazy danych lub dziennika transakcji. Zobacz [kopii zapasowych i przywracanie z serwera bazy danych SQL](/sql/relational-databases/backup-restore/back-up-and-restore-of-sql-server-databases) w dokumentacji programu SQL Server w taki sposób, aby uzyskać więcej informacji.

## <a name="changes-for-site-recovery"></a>Zmiany dotyczące usługi site recovery
Można użyć opcji odzyskiwania lokacji **Pomiń odzyskiwanie bazy danych (Użyj tej opcji, jeśli baza danych jest nietknięta)** Jeśli co najmniej jeden węzeł grupy dostępności pozostaje funkcjonalny.

 Aby możliwe było odzyskanie lokacji, gdy wszystkie węzły grupy dostępności zostały utracone, należy ponownie utworzyć grupy dostępności. Menedżer konfiguracji nie może odbudować ani przywrócić węzła dostępności. Po grupie zostaje odtworzone, a kopia zapasowa przywrócenie i ponowne skonfigurowanie, można następnie użyć opcji odzyskiwania lokacji **Pomiń odzyskiwanie bazy danych (Użyj tej opcji, jeśli baza danych jest nietknięta)**.

Aby uzyskać więcej informacji, zobacz [kopii zapasowych i odzyskiwania dla programu System Center Configuration Manager](/sccm/protect/understand/backup-and-recovery).

## <a name="changes-for-reporting"></a>Zmiany dotyczące raportowania
**Zainstaluj punkt usług raportowania:**  
Punkt usług raportowania nie obsługuje używania wirtualnej nazwę odbiornika grupy dostępności lub obsługującego bazę danych usług raportowania w grupie dostępności programu SQL Server zawsze włączone:
-   Domyślnie usług raportowania punktu instalacji zestawy **nazwę serwera bazy danych lokacji** do nazwy wirtualnego, który jest określony jako odbiornik. Zmiany, aby określić nazwę komputera i wystąpienie replikę w grupie dostępności.
-   Do odciążenia raportowania obciążenia i zwiększenia dostępności, gdy węzeł repliki jest w trybie offline, należy wziąć pod uwagę instalowanie dodatkowych punkty usług raportowania w każdym węźle repliki i konfigurowania poszczególnych usług raportowania punkt-punkt do nazwy komputera.

Po zainstalowaniu punktu usług raportowania w każdej replice grupy dostępności raportowania można zawsze połączyć się z aktywnego serwera punktu raportowania.

**Przełącz punkt usług raportowania, używany przez konsolę programu:**  
Aby uruchamiać raporty, w konsoli przejdź do **monitorowanie** > **omówienie** > **raportowania** > **raporty**, a następnie wybierz pozycję **opcje raportu**. W oknie dialogowym Opcje raportu wybierz żądany punkt usług raportowania.

## <a name="next-steps"></a>Następne kroki
Po zidentyfikowaniu wymagań wstępnych, ograniczenia i zmiany do typowych zadań, które są wymagane w przypadku korzystania z grup dostępności, zobacz [Konfigurowanie grup dostępności dla programu Configuration Manager](/sccm/core/servers/deploy/configure/configure-aoag), procedury umożliwiające instalowanie i konfigurowanie lokacji do korzystania z grup dostępności.

