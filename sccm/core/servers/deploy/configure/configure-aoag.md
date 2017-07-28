---
title: "Konfigurowanie grup dostępności | Dokumentacja firmy Microsoft"
description: "Konfigurowanie i zarządzanie grupami dostępności serwera SQL Server zawsze na wraz z programem SCCM."
ms.custom: na
ms.date: 5/26/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 7e4ec207-bb49-401f-af1b-dd705ecb465d
caps.latest.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dc221ddf547c43ab1f25ff83c3c9bb603297ece6
ms.openlocfilehash: 138834b6cc64332202256961ad1d2f5ab6d176db
ms.contentlocale: pl-pl
ms.lasthandoff: 06/01/2017


---
# <a name="configure-sql-server-always-on-availability-groups-for-configuration-manager"></a>Konfigurowanie programu SQL Server zawsze włączonych grup dostępności dla programu Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Skorzystaj z informacji w tym temacie, aby skonfigurować i zarządzać nimi grup dostępności, z których korzystasz z programu Configuration Manager.

Przed rozpoczęciem:  
-   Należy zapoznać się z informacjami z [przygotowanie do korzystania z programu SQL Server zawsze włączonych grup dostępności z programem Configuration Manager](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database).
-   Należy zapoznać się z dokumentacją serwera SQL, który obejmuje korzystania z grup dostępności i powiązanych procedur, które są wymagane do przeprowadzenia w następujących scenariuszach.

> [!TIP]  
>  Łącza z tego tematu dla programu SQL Server, przejdź do zawartości dla programu SQL Server 2016. Jeśli nie należy używać tej wersji programu SQL Server, zajrzyj do dokumentacji dla używanej wersji.

## <a name="create-and-configure-an-availability-group"></a>Utwórz i skonfiguruj grupy dostępności
Poniższa procedura umożliwia utworzenie grupy dostępności, a następnie przenieść kopię bazy danych lokacji do tej grupy dostępności.

Aby wykonać tę procedurę, konto, którego używasz, musi być:
-   Członek **Administratorzy lokalni** na każdym komputerze, który będzie znajdować się w grupie dostępności.
-   A **sysadmin** na każde wystąpienie programu SQL Server, który będzie hostem bazy danych lokacji.

### <a name="to-create-and-configure-an-availability-group-for-configuration-manager"></a>Aby utworzyć i skonfigurować grupę dostępności programu Configuration Manager  
1.    Aby zatrzymać lokację programu Configuration Manager, użyj następującego polecenia: **Preinst.exe /stopsite**. Aby uzyskać więcej informacji na temat używania Preinst.exe, zobacz [narzędzia Obsługa hierarchii](/sccm/core/servers/manage/hierarchy-maintenance-tool-preinst.exe).

2.    Zmień model kopii zapasowej bazy danych lokacji z **PROSTY** na **PEŁNY**.
Zobacz [View or Change the Recovery Model of a Database](/sql/relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server) (Wyświetlanie lub zmiana modelu odzyskiwania bazy danych) w dokumentacji programu SQL Server. (Grupy dostępności obsługują tylko model PEŁNY).

3.    Użyj programu SQL Server, aby utworzyć pełną kopię zapasową bazy danych lokacji, a następnie wykonaj jedną z następujących czynności, w zależności od tego, czy serwer, który jest hostem bazy danych lokacji będzie replik grupy dostępności lub nie:
    -   **Będzie członkiem tej grupy dostępności:**  
        Jeśli ten serwer jest używany jako początkowa replika podstawowa członkiem grupy dostępności, nie trzeba przywrócić kopię bazy danych lokacji do tego lub innego serwera w grupie. Bazy danych będą się już na miejscu w replice podstawowej, a program SQL Server zostaną zreplikowane bazy danych do repliki pomocniczej w kolejnym kroku.  

      -    **Nie będzie członkiem grupy dostępności:**   
    Na serwerze, który będzie obsługiwał replikę podstawową grupy, należy przywrócić kopię bazy danych lokacji.

    Aby uzyskać informacje na temat sposobu ukończenia tego kroku, zobacz [tworzenie pełnej kopii zapasowej bazy danych](/sql/relational-databases/backup-restore/create-a-full-database-backup-sql-server) i [Przywróć kopię zapasową bazy danych przy użyciu narzędzia SSMS](/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms)w dokumentacji programu SQL Server.

4.    Na serwerze, który będzie obsługiwał początkowej replikę podstawową grupy, użyj [Kreatora nowej grupy dostępności](/sql/database-engine/availability-groups/windows/use-the-availability-group-wizard-sql-server-management-studio) można utworzyć grupy dostępności. W kreatorze:
      -    Na **wybierz bazę danych** wybierz bazy danych lokacji programu Configuration Manager automatycznie.  

      -    Na stronie **Określanie replik** skonfiguruj:
          -    **Repliki:** Określ serwery, które będą obsługiwać repliki pomocniczej.

          -    **Odbiornik:** Określ **nazwy DNS odbiornika** pełnej nazwy DNS, takich jak  **&lt;Listener_Server >. fabrikam.com**. To jest używany podczas konfigurowania programu Configuration Manager do używania bazy danych w grupie dostępności.

      -    Na stronie **Wybieranie początkowej synchronizacji danych** wybierz opcję **Pełna**. Po utworzeniu grupy dostępności, Kreator kopii zapasowej głównej bazy danych i dziennika transakcji i następnie przywróci je na każdym serwerze, który obsługuje replikę pomocniczą. (Jeśli nie możesz użyć tego kroku, konieczne będzie przywrócenie kopii bazy danych lokacji na każdym serwerze, który obsługuje replikę pomocniczą, a następnie ręczne dołączenie tej bazy danych w grupie.)   

5.    Sprawdź konfigurację w każdej repliki:   
  1.    Upewnij się, konto komputera serwera lokacji jest elementem członkowskim **Administratorzy lokalni** na każdym komputerze, który jest członkiem grupy dostępności.  

  2.  Uruchom [skrypt weryfikacji](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database#prerequisites) z wymagań wstępnych, aby upewnić się, że dla każdej repliki bazy danych lokacji jest poprawnie skonfigurowana.

  3.    Jeśli jest ustawiona konfiguracje w replikach pomocniczych, należy ręcznie pracy awaryjnej replikę podstawową do repliki pomocniczej przed kontynuowaniem, ponieważ można skonfigurować tylko bazy danych z repliki podstawowej. Aby uzyskać więcej informacji, zobacz [wykonać planowanego ręcznego trybu Failover grupy dostępności](/sql/database-engine/availability-groups/windows/perform-a-planned-manual-failover-of-an-availability-group-sql-server) w dokumentacji programu SQL Server.

6.    Po wszystkich replik spełnić te wymagania, grupa dostępności jest gotowa do użycia z programem Configuration Manager.

## <a name="configure-a-site-to-use-the-database-in-the-availability-group"></a>Konfigurowanie lokacji do używania bazy danych w grupie dostępności
Po [utworzyć i skonfigurować grupę dostępności](#create-and-configure-an-availability-group), obsługę lokacji programu Configuration Manager umożliwia skonfigurowanie lokacji do używania bazy danych, która jest hostowana przez grupy dostępności.

Instalowanie nowej lokacji z jej bazą danych w grupie dostępności nie jest obsługiwane. Na przykład jeśli używasz nośnika linii bazowej 1702 zainstalowanie lokacji przy użyciu jednego wystąpienia programu SQL Server. Po zainstalowaniu lokacji, można następnie przenieść bazę danych lokacji do grupy dostępności.

Aby wykonać tę procedurę, musi być konto, którego używasz do uruchamiania Instalatora programu Configuration Manager:
-   Członek **Administratorzy lokalni** na każdym komputerze, który jest członkiem grupy dostępności.
-   A **sysadmin** na każde wystąpienie programu SQL Server, który jest hostem bazy danych lokacji.

> [!IMPORTANT]
> Korzystając z programu Microsoft Intune z programem Configuration Manager w konfiguracji hybrydowych, przenoszenie bazy danych lokacji z grupy dostępności lub wyzwala ponowne synchronizowanie danych z chmurą. Nie można uniknąć.

### <a name="to-configure-a-site-to-use-the-availability-group"></a>Aby skonfigurować lokację do używania grupy dostępności
1.    Uruchom **Instalatora programu Configuration Manager** z  **&lt;* folder instalacji lokacji programu Configuration Manager*> \BIN\X64\setup.exe**.

2.    Na stronie **Pierwsze kroki** wybierz pozycję **Przeprowadź obsługę lokacji lub zresetuj tę lokację**, a następnie kliknij przycisk **Dalej**.

3.    Wybierz opcję **Modyfikuj konfigurację serwera SQL** , a następnie kliknij przycisk **Dalej**.

4.    Skonfiguruj ponownie następujące elementy dla bazy danych lokacji:
    -   **Nazwa programu SQL Server:** Wprowadź nazwę wirtualną dla grupy dostępności **odbiornika** można skonfigurować podczas tworzenia grupy dostępności. Nazwa wirtualna powinna być pełną nazwą DNS, takie jak  **&lt;* Serwer_punktu_końcowego*>. fabrikam.com**.  

    -   **Wystąpienie:** Ta wartość musi być pusta, aby określić wystąpienie domyślne *odbiornika* grupy dostępności. Jeśli bieżąca baza danych lokacji jest zainstalowana w nazwanym wystąpieniu, nazwane wystąpienie będzie widoczna i muszą zostać wyczyszczone.

    -   **Baza danych:** Pozostaw nazwę wyświetlaną. Jest to nazwa bieżącej bazy danych lokacji.

5.    Po podaniu informacji dotyczących nowej lokalizacji bazy danych zamknij Instalator, wykonując normalne czynności procedury i konfiguracji.



## <a name="add-and-remove-replica-members"></a>Dodawanie i usuwanie replik  
Kiedy bazy danych lokacji znajduje się w grupie dostępności, aby dodać lub usunąć członków repliki należy użyć poniższych procedur. Program Configuration Manager obsługuje jeden podstawowe i dwa węzły dodatkowej.

Aby wykonać poniższe procedury, konto, którego używasz, musi być:
-   Członek **Administratorzy lokalni** na każdym komputerze, który jest członkiem grupy dostępności.
-   A **sysadmin** na każdym serwerze SQL, który jest hostem lub będzie hostem bazy danych lokacji.


### <a name="to-add-a-new-replica-member"></a>Aby dodać nowy element członkowski repliki
1.    Dodaj nowy serwer jako replikę pomocniczą do grupy dostępności. Zobacz [Dodawanie repliki pomocniczej do grupy dostępności (SQL Server)](/sql/database-engine/availability-groups/windows/add-a-secondary-replica-to-an-availability-group-sql-server) w bibliotece dokumentacji programu SQL Server.

2.    Zatrzymaj lokację programu Configuration Manager, uruchamiając **Preinst.exe/stopsite**. Zobacz [narzędzia Obsługa hierarchii](/sccm/core/servers/manage/hierarchy-maintenance-tool-preinst.exe).

3.    Użyj programu SQL Server, aby utworzyć kopię zapasową bazy danych lokacji z repliki podstawowej, a następnie przywrócić dane z tej kopii zapasowej do nowego serwera repliki pomocniczej. Zobacz [tworzenie pełnej kopii zapasowej bazy danych](/sql/relational-databases/backup-restore/create-a-full-database-backup-sql-server) i [Przywróć kopię zapasową bazy danych przy użyciu narzędzia SSMS](/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms) w dokumentacji programu SQL Server.

4.    Skonfiguruj każdą replikę pomocniczą. W celu skonfigurowania każdej repliki pomocniczej w grupie dostępności wykonaj następujące czynności:

    1.    Upewnij się, konto komputera serwera lokacji jest elementem członkowskim **Administratorzy lokalni** na każdym komputerze, który jest członkiem grupy dostępności.

    2.    Uruchom [skrypt weryfikacji](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database#prerequisites) z wymagań wstępnych, aby upewnić się, że dla każdej repliki bazy danych lokacji jest poprawnie skonfigurowana.

    3.    Jeśli jest to niezbędne do skonfigurowania nowej repliki ręcznie pracy awaryjnej replikę podstawową do niej nową replikę pomocniczą, a następnie wprowadź wymagane ustawienia. Zobacz [Perform a Planned Manual Failover of an Availability Group](/sql/database-engine/availability-groups/windows/perform-a-planned-manual-failover-of-an-availability-group-sql-server) (Wykonywanie zaplanowanego ręcznego przełączania awaryjnego grupy dostępności) w dokumentacji programu SQL Server.

5.    Uruchom ponownie lokację, uruchamiając usługi Menedżer składników lokacji (**sitecomp**) i **SMS_Executive** .

### <a name="to-remove-a-replica-member"></a>Aby usunąć element członkowski repliki
Do wykonania tej procedury, skorzystaj z informacji w [usunąć repliki pomocniczej z grupy dostępności](/sql/database-engine/availability-groups/windows/remove-a-secondary-replica-from-an-availability-group-sql-server) z dokumentacji programu SQL Server.

## <a name="stop-using-an-availability-group"></a>Zatrzymaj przy użyciu grupy dostępności
Gdy nie chcesz już obsługiwać bazy danych lokacji w grupie dostępności, użyj poniższej procedury. Obejmuje to przeniesienie bazy danych lokacji z powrotem do pojedynczego wystąpienia programu SQL Server.

Aby wykonać tę procedurę, konto, którego używasz, musi być:
-   Członek **Administratorzy lokalni** na każdym komputerze, który jest członkiem grupy dostępności
-   A **sysadmin** na każde wystąpienie programu SQL Server, który jest hostem bazy danych lokacji.

> [!IMPORTANT]  
> Korzystając z programu Microsoft Intune z programem Configuration Manager w konfiguracji hybrydowych, przenoszenie bazy danych lokacji z grupy dostępności lub wyzwala ponowne synchronizowanie danych z chmurą. Nie można uniknąć.

### <a name="to-move-the-site-database-from-an-availability-group-back-to-a-single-instance-sql-server"></a>Aby przenieść bazę danych lokacji z grupy dostępności do pojedynczego wystąpienia programu SQL Server
1.    Zatrzymaj lokację programu Configuration Manager za pomocą następującego polecenia: **Preinst.exe /stopsite**. Aby uzyskać więcej informacji, zobacz [narzędzia Obsługa hierarchii](/sccm/core/servers/manage/hierarchy-maintenance-tool-preinst.exe).

2.    Użyj programu SQL Server, aby utworzyć pełną kopię zapasową bazy danych lokacji z repliki podstawowej. Informacje na temat sposobu ukończenia tego kroku zawiera temat [Create a Full Database Backup](/sql/relational-databases/backup-restore/create-a-full-database-backup-sql-server) (Tworzenie pełnej kopii zapasowej bazy danych) w dokumentacji programu SQL Server.

3.    Jeśli serwer, który jest repliką podstawową dla grupy dostępności będzie obsługiwać pojedyncze wystąpienie bazy danych lokacji, możesz pominąć ten krok:  

    -   Użyj programu SQL Server do przywrócenia kopii zapasowej bazy danych lokacji do serwera, który będzie obsługiwał bazę danych lokacji. Zobacz [Przywróć kopię zapasową bazy danych przy użyciu narzędzia SSMS](/sql/relational-databases/backup-restore/restore-a-database-backup-using-ssms) w dokumentacji programu SQL Server.   <br />  <br />

4.    Na serwerze, który będzie hostem bazy danych lokacji (repliką podstawową lub serwerze, gdzie przywróconej bazy danych lokacji), należy zmienić model kopii zapasowej bazy danych lokacji z **pełne** do **proste**. Zobacz [View or Change the Recovery Model of a Database](/sql/relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server) (Wyświetlanie lub zmiana modelu odzyskiwania bazy danych) w dokumentacji programu SQL Server.  

5.    Uruchom **Instalatora programu Configuration Manager** z  **&lt;* folder instalacji lokacji programu Configuration Manager >*\BIN\X64\setup.exe**.

6.    Na stronie **Pierwsze kroki** wybierz pozycję **Przeprowadź obsługę lokacji lub zresetuj tę lokację**, a następnie kliknij przycisk **Dalej**.  

7.    Wybierz opcję **Modyfikuj konfigurację serwera SQL** , a następnie kliknij przycisk **Dalej**.  

8.    Skonfiguruj ponownie następujące elementy dla bazy danych lokacji:
    -   **Nazwa programu SQL Server:** Wprowadź nazwę serwera, który teraz udostępnia bazę danych lokacji.

    -   **Wystąpienie:** Określ nazwanego wystąpienia, który jest hostem bazy danych lokacji, lub pozostaw to pole puste, jeśli baza danych znajduje się w domyślnym wystąpieniu.

    -   **Baza danych:** Pozostaw nazwę wyświetlaną. Jest to nazwa bieżącej bazy danych lokacji.    

9.    Po podaniu informacji dotyczących nowej lokalizacji bazy danych zamknij Instalator, wykonując normalne czynności procedury i konfiguracji. Po zakończeniu instalacji lokacja zostanie ponownie uruchomiona i rozpocznie korzystanie z nowej lokalizacji bazy danych.    

10.    Aby wyczyścić serwery, które były elementami członkowskimi grupy dostępności, postępuj zgodnie ze wskazówkami w temacie [Remove an Availability Group](/sql/database-engine/availability-groups/windows/remove-an-availability-group-sql-server) (Usuwanie grupy dostępności) w dokumentacji programu SQL Server.
