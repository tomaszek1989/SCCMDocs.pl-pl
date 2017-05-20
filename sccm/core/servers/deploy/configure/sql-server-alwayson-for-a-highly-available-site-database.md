---
title: SQL Server AlwaysOn | Dokumentacja firmy Microsoft
ms.custom: na
ms.date: 1/4/2017
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: aaaab003ddd22f18160d4be63cfeab3a7e7f6b03
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="sql-server-alwayson-for-a-highly-available-site-database-for-system-center-configuration-manager"></a>Zawsze włączony serwer programu SQL Server na potrzeby bazy danych lokacji o wysokiej dostępności programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


 Począwszy od z System Center Configuration Manager w wersji 1602, można użyć programu SQL Server [grup dostępności AlwaysOn](https://msdn.microsoft.com/library/hh510230\(v=sql.120\).aspx) do obsługi bazy danych lokacji w lokacji głównej i centralnej lokacji administracyjnej jako rozwiązań wysokiej dostępności i odzyskiwania po awarii. Grupa dostępności może być obsługiwana lokalnie lub na platformie Microsoft Azure.  

 Gdy w celu obsługiwania grupy dostępności używana jest platforma Microsoft Azure, można zwiększyć dostępność bazy danych lokacji przy użyciu zawsze włączonych grup dostępności programu SQL Server z zestawami dostępności Azure. Więcej informacji o zestawach dostępności Azure zawiera temat [Manage the availability of virtual machines](https://azure.microsoft.com/documentation/articles/virtual-machines-windows-manage-availability/)(Zarządzanie dostępnością maszyn wirtualnych).  

 Program Configuration Manager obsługuje baza danych lokacji w grupie dostępności SQL związanej wewnętrznych lub zewnętrznych usługi równoważenia obciążenia. Oprócz konfigurowania wyjątków zapory dla każdej repliki, należy dodać następujące porty zasady równoważenia obciążenia:
  - SQL przez TCP: TCP 1433
  - SQL Server Service Broker: TCP 4022
  - Blok komunikatów serwera (SMB): TCP 445
  - Program mapowania punktów końcowych wywołań RPC: TCP 135


Obsługiwane są następujące scenariusze dotyczące grup dostępności:  

-   Bazę danych lokacji można przenieść do wystąpienia domyślnego grupy dostępności.  

-   Elementy członkowskie będące replikami można dodawać lub usuwać z grupy dostępności, która obsługuje bazę danych lokacji.  

-   Bazę danych lokacji można przenieść z grupy dostępności do domyślnego lub nazwanego wystąpienia autonomicznego programu SQL Server.  

> [!Important]  
> Używając Microsoft Intune z programem Configuration Manager w konfiguracji hybrydowych, przeniesienie bazy danych lokacji z wyzwalaczy grupy dostępności lub ponownej synchronizacji danych z chmurą. Nie można uniknąć. 



> [!NOTE]  
>  Aby pomyślnie konfigurować grupy dostępności i ich używać, niezbędna jest dobra znajomość sposobu konfigurowania programu SQL Server i grup dostępności programu SQL Server. Procedury programu System Center Configuration Manager w tym temacie polegają na dodatkowej dokumentacji i procedur omówionych w bibliotece dokumentacji programu SQL Server.  

 **Znane problemy podczas używania zawsze włączonych grup dostępności z programem Configuration Manager:**  

-   **Wszystkie serwery replik wymagają identycznej ścieżki pliku podczas konfigurowania programu Configuration Manager na potrzeby używania grupy dostępności:**  

    -   W czasie uruchamiania Instalatora programu Configuration Manager do przekierowania lokacji do używania bazy danych w grupie dostępności każdy serwer repliki pomocniczej w grupie musi mieć ścieżkę pliku, która jest taka sama jak ścieżka plików używana do przechowywania plików bazy danych lokacji dla bieżącej repliki podstawowej. Jeśli identyczna ścieżka nie istnieje w replikach pomocniczych, Instalator nie doda wystąpienia grup dostępności jako nowej lokalizacji bazy danych lokacji.  

         Ponadto na każdym pomocniczym serwerze repliki lokalne konto usługi programu SQL Server musi posiadać uprawnienie **Pełna kontrola** do tego folderu.  

         Pomocnicze serwery repliki wymagają tej ścieżki pliku tylko podczas używania Instalatora, aby określić wystąpienie bazy danych w grupie dostępności.  Gdy Instalator zakończy zmianę w celu używania bazy danych lokacji w grupie dostępności, można usunąć nieużywaną ścieżkę z pomocniczych serwerów repliki.  

         Na przykład rozważmy następujący scenariusz:  

        -   Tworzysz grupę dostępności, która używa trzech serwerów SQL.  

        -   Twoim podstawowym serwerem repliki jest nowa instalacja programu SQL Server 2014.  Domyślnie pliki MDF i LDF bazy danych są przechowywane w ścieżce C:\Program Files\Microsoft SQL Server\MSSQL12.MSSQLSERVER\MSSQL\DATA  

        -   Oba serwery pomocnicze repliki zostały uaktualnione do programu SQL Server 2014 z poprzednich wersji i Zachowaj w oryginalnej ścieżce pliku do przechowywania plików bazy danych: C:\Program Files\Microsoft SQL Server\MSSQL10. MSSQLSERVER\MSSQL\DATA  

        -   Przed przystąpieniem do przenoszenia bazy danych lokacji do tej grupy dostępności, na każdym serwerze repliki pomocniczej należy utworzyć następującą ścieżkę pliku nawet wtedy, gdy replikach pomocniczych nie będzie używać tej lokalizacji pliku:  C:\Program Files\Microsoft SQL Server\MSSQL12. MSSQLSERVER\MSSQL\DATA (jest to duplikat ścieżki, która jest używana dla repliki podstawowej)  

        -   Następnie nadasz uprawnienie Pełna kontrola — dotyczące nowo utworzonej lokalizacji pliku na tym serwerze — kontu usługi programu SQL Server na każdej replice pomocniczej.  

        -   Teraz można pomyślnie uruchomić Instalatora programu Configuration Manager, aby skonfigurować, aby użyć bazy danych lokacji w grupie dostępności  

-   **Gdy Instalator zostanie uruchomiony, aby nakazać bazie danych lokacji używanie grupy dostępności, wówczas błędy podobne do następującego mogą być rejestrowane w dzienniku ConfigMgrSetup.log:**  

    -   BŁĄD: Błąd serwera SQL: [25000] [3906] [Microsoft] [SQL Server Native klienta 11.0] [SQL Server] nie można zaktualizować bazy danych "CM_AAA", ponieważ baza danych jest tylko do odczytu.   Instalator programu Configuration Manager 21/1/2016 16:54:59  7344 (0x1CB0)  

     Te błędy są rejestrowane, gdy Instalator podejmuje próbę przetwarzania ról bazy danych w replikach pomocniczych grupy dostępności. Te błędy można zignorować.
- **Serwery SQL, które obsługują grup dostępności dodatkowe:**

  Przed zainstalowaniem wersji 1610 podczas używania grupy dostępności i następnie uruchamiania Instalatora programu Configuration Manager lub zainstalowania aktualizacji dla programu Configuration Manager, każdej repliki w każdej grupie dostępności dodatkowych na serwerze SQL, który obsługuje grupy dostępności programu Configuration Manager musi mieć następującą konfigurację:
    - **ręcznej pracy awaryjnej**
    - **zezwalała na każde połączenie tylko do odczytu**


##  <a name="bkmk_BnR"></a> Zmiany dotyczące kopii zapasowych i odzyskiwania, gdy używana jest zawsze włączona grupa dostępności programu SQL Server  
 **Kopia zapasowa:**  

 Po uruchomieniu bazy danych lokacji w grupie dostępności, dlatego należy kontynuować wykonywanie Uruchom wbudowane **kopii zapasowej lokacji** zadanie obsługi serwera do wykonywania kopii zapasowej typowe ustawienia programu Configuration Manager i pliki, ale aby nie korzystać. MDF lub. Pliki LDF utworzone przez tej kopii zapasowej. Zamiast tego należy zaplanować tworzenie bezpośrednich kopii zapasowych bazy danych lokacji za pomocą programu SQL Server.  

 Ponadto ponieważ model odzyskiwania bazy danych jest ustawiony na odzyskiwanie pełne, należy zaplanować monitorowanie i utrzymywanie rozmiaru dziennika transakcji bazy danych lokacji.  W modelu odzyskiwania pełnego transakcje nie działają w trybie zaostrzonym aż do wykonania pełnej kopii zapasowej bazy danych lub dziennika transakcji. Model odzyskiwania pełnego jest wymagany przy użyciu bazy danych lokacji w grupie dostępności i podczas konfigurowania grupy do użytku z programem Configuration Manager. Więcej informacji na temat wykonywania kopii zapasowych serwera SQL i przywracania go zawiera temat [Back Up and Restore of SQL Server Databases](https://msdn.microsoft.com/library/ms187048\(v=sql.120\).aspx) (Tworzenie kopii zapasowych i przywracanie baz danych programu SQL Server) w dokumentacji programu SQL Server.  

 **Przywracanie:**  

 Podczas odzyskiwania lokacji, dopóki jeden węzeł grupy dostępności pozostaje funkcjonalny, można używać opcji odzyskiwania lokacji **Pomiń odzyskiwanie bazy danych (użyj tej opcji, jeśli baza danych jest nietknięta)**.  

 Jednak wszystkie węzły do grupy dostępności zostały utracone, zanim można odzyskać lokację, należy ponownie utworzyć grupy dostępności (System Center Configuration Manager nie można odbudować lub przywrócić węzeł dostępność.)  Po ponownym utworzeniu grupy poprzez przywrócenie i ponowne skonfigurowanie kopii zapasowej można użyć opcji odzyskiwania lokacji **Pomiń odzyskiwanie bazy danych (użyj tej opcji, jeśli baza danych jest nietknięta)**.  

 Aby uzyskać więcej informacji o tworzeniu kopii zapasowych i odzyskiwaniu danych, zobacz [Tworzenie i odzyskiwanie kopii zapasowych programu System Center Configuration Manager](../../../../protect/understand/backup-and-recovery.md).  

##  <a name="bkmk_create"></a> Konfigurowanie grupy dostępności przeznaczonej do użytku z programem Configuration Manager  
 Przed rozpoczęciem poniższej procedury, można zapoznać się z programu SQL Server procedury niezbędne do ukończenia tej konfiguracji i skonfiguruj następujące informacje, które są stosowane do grup dostępności do użytku z programem Configuration Manager.  

 **Wymagania dotyczące zawsze włączonych grup dostępności używanych z programem System Center Configuration Manager:**  

-  *Wersja*: Każdy węzeł (lub repliki) w grupie dostępności, należy uruchomić wersję programu SQL Server obsługiwane przez program System Center Configuration Manager. Różne węzły grupy dostępności obsługiwanych przez program SQL Server, można uruchomić różnych wersji programu SQL Server.   

- *Wersja*: Należy użyć programu SQL Server w wersji Enterprise.  Wersja programu SQL Server 2016 Standard wprowadza grup dostępności podstawowych, które nie są obsługiwane przez program Configuration Manager.


-   Grupy dostępności musi mieć jedną replikę podstawową i może mieć maksymalnie dwa synchroniczne replikach pomocniczych.  

-  Po dodaniu bazy danych do grupy dostępności, należy przełączyć w tryb pracy awaryjnej replikę podstawową i przełączyć się na replikę pomocniczą (tworząc z niej nową replikę podstawową), a następnie skonfigurować bazę danych z następującymi ustawieniami:
    - Włącz właściwość Trustworthy: True
    - Włącz brokera usług: True
    - Ustaw właściciela bazy danych: SA

    Aby skonfigurować te ustawienia, możesz uruchomić następujący skrypt, gdzie cm_ABC to nazwa bazy danych lokacji:  

    >     UŻYJ wzorca  
    >     Cm_ABC ALTER DATABASE SET NEW_BROKER   
    >     Cm_ABC ALTER DATABASE SET ENABLE_BROKER  
    >     ALTER DATABASE cm_ABC USTAWIĆ WIARYGODNEGO dalej.  
    >     UŻYJ cm_ABC  
    >     EXEC sp_changedbowner 'sa'  
    >     Skonfiguruj ponownie Exec sp_configure 'max text repl size (B)", 2147483647



-   Grupa dostępności musi mieć co najmniej jeden **odbiornik grupy dostępności**.  Nazwa wirtualnego tego odbiornika jest używana podczas konfigurowania programu Configuration Manager do używania bazy danych lokacji w grupie dostępności. Mimo że grupy dostępności może zawierać wiele odbiorników, Configuration Manager tworzyć tylko używać jednego  

-   Każda replika podstawowa i pomocnicza musi:  
    - być skonfigurowana w taki sposób, aby **zezwalała na każde połączenie tylko do odczytu**;
    - używać **wystąpienia domyślnego**;
    - być skonfigurowana na potrzeby **ręcznej pracy awaryjnej**.  

        > [!TIP]  
        >  System Center Configuration Manager umożliwia używanie repliki grupy dostępności, jeśli określono opcję automatycznej pracy awaryjnej. Jednak ręczne pracy awaryjnej musi być ustawiona, uruchom Instalatora, aby określić bazę danych lokacji w grupie dostępności, gdy w czasie zainstalować wszystkie aktualizacje programu Configuration Manager (nie tylko aktualizacje, które są stosowane do bazy danych lokacji).  

  **Ograniczenia dotyczące grup dostępności**
   - Grupy dostępności podstawowe (wprowadzone w programie SQL Server 2016 Standard edition) nie są obsługiwane. Jest to spowodowane grup dostępności podstawowe nie obsługują dostęp do odczytu replikach pomocniczych, wymagane do użytku z programem Configuration Manager. Aby uzyskać więcej informacji, zobacz [podstawowe grupy dostępności (zawsze na dostępność grupy)](https://msdn.microsoft.com/en-us/library/mt614935.aspx).

   - Grupy dostępności są obsługiwane tylko w przypadku bazy danych lokacji i nie aktualizacji oprogramowania lub bazy danych raportowania.   
   - W przypadku używania grupy dostępności należy ręcznie skonfigurować punkt raportowania tak, aby używał bieżącej repliki podstawowej, a nie odbiornika grupy dostępności. Jeśli replika podstawowa zostanie przełączona w tryb pracy awaryjnej przy użyciu innej repliki, należy ponownie skonfigurować punkt raportowania, aby używał nowej repliki podstawowej.  
   - Przed zainstalowaniem aktualizacji, podobnie jak w wersji 1606, upewnij się, że grupa dostępności jest ustawiona na ręczną pracę awaryjną. Po zaktualizowaniu lokacji można przywrócić ustawienie na automatyczną pracę awaryjną.



 **Uprawnienia wymagane do konfigurowania i korzystania z grup dostępności:**  

-   Konto komputera serwera lokacji musi być członkiem grupy **Administratorzy lokalni** na komputerze należącym do danej grupy dostępności.  

#### <a name="to-configure-an-availability-group-to-host-a-site-database"></a>Aby skonfigurować grupę dostępności do obsługi bazy danych lokacji  

1.  Użyj następującego polecenia zatrzymania lokacji programu Configuration Manager:  
     **Preinst.exe /stopsite**  

     Aby uzyskać informacje na temat korzystania z narzędzia Preinst.exe, zobacz [Narzędzie Obsługa hierarchii (Preinst.exe) dla programu System Center Configuration Manager](../../../../core/servers/manage/hierarchy-maintenance-tool-preinst.exe.md).  

2.  Zmień model kopii zapasowej bazy danych lokacji z **PROSTY** na **PEŁNY**.  

     Zobacz [View or Change the Recovery Model of a Database](https://msdn.microsoft.com/library/ms189272\(v=sql.120\).aspx) (Wyświetlanie lub zmiana modelu odzyskiwania bazy danych) w dokumentacji programu SQL Server. (Grupy dostępności obsługują tylko model PEŁNY).  

3.  Na serwerze, który będzie obsługiwał replikę podstawową grupy, użyj **Kreatora nowej grupy dostępności** , aby utworzyć grupę dostępności. W kreatorze:  

    -   Na **wybierz bazę danych** wybierz bazę danych dla Ciebie lokacji programu Configuration Manager  

    -   Na stronie **Określanie replik** skonfiguruj:  

        -   **Replik**: Określ serwery, które będą obsługiwać replikach pomocniczych  

        -   **Odbiornik**: Określ **odbiornika nazwa DNS** pełnej nazwy DNS, takich jak  **&lt;Listener_Server >. fabrikam.com**. To jest używane podczas konfigurowania programu Configuration Manager do używania bazy danych w grupie dostępności.

    -   Na stronie **Wybieranie początkowej synchronizacji danych** wybierz opcję **Pełna**. Po utworzeniu grupy dostępności kreator utworzy kopię zapasową głównej bazy danych i dziennika transakcji, a następnie przywróci je na każdym serwerze, który obsługuje replikę pomocniczą. Jeśli ten krok zostanie pominięty, konieczne będzie przywrócenie kopii bazy danych lokacji na każdym serwerze, który obsługuje replikę pomocniczą, a następnie ręczne dołączenie tej bazy danych do grupy.  

    Aby uzyskać więcej informacji, zobacz [Use the Availability Group Wizard](https://msdn.microsoft.com/library/hh403415\(v=sql.120\).aspx) (Korzystanie z kreatora grup dostępności) w dokumentacji programu SQL Server.  

4.  Po skonfigurowaniu grupy dostępności skonfiguruj bazę danych lokacji w replice podstawowej za pomocą właściwością **TRUSTWORTHY** , a następnie **włącz integrację środowiska CLR**. Aby uzyskać informacje dotyczące sposobu konfigurowania tych komponentów, zobacz [TRUSTWORTHY Database Property](https://msdn.microsoft.com/library/ms187861\(v=sql.120\).aspx) (Właściwość TRUSTWORTHY bazy danych) i  [Enabling CLR Integration](https://msdn.microsoft.com/library/ms131048\(v=sql.120\).aspx) (Włączanie integracji środowiska CLR) w dokumentacji programu SQL Server.  

5.  Wykonaj następujące czynności w celu skonfigurowania każdej repliki pomocniczej w grupie dostępności:  

    1.  Przełącz ręcznie w tryb pracy awaryjnej aktualną replikę podstawową, tworząc z niej replikę pomocniczą. Zobacz [Perform a Planned Manual Failover of an Availability Group](https://msdn.microsoft.com/library/hh231018\(v=sql.120\).aspx) (Wykonywanie zaplanowanego ręcznego przełączania awaryjnego grupy dostępności) w dokumentacji programu SQL Server.  

    2.  Skonfiguruj bazę danych w nowej replice podstawowej za pomocą właściwości **TRUSTWORTHY** , a następnie **włącz integrację środowiska CLR**.  

6.  Po wszystkie repliki są przenoszone do głównej replik i baz danych skonfigurowanych, grupa dostępności jest gotowa do użycia z programem Configuration Manager.  





##  <a name="bkmk_direct"></a> Przenoszenie bazy danych lokacji do grupy dostępności  
 Bazę danych lokacji dla uprzednio zainstalowanej lokacji można przenieść do grupy dostępności. Najpierw musisz utworzyć grupę dostępności, a następnie skonfigurować bazę danych na potrzeby działania w grupie dostępności.  

 Aby wykonać tę procedurę, konto użytkownika uruchamiającego instalację programu Configuration Manager musi być członkiem **Administratorzy lokalni** na każdym komputerze, który jest członkiem grupy dostępności.  

#### <a name="to-move-a-site-database-to-an-availability-group"></a>Aby przenieść bazę danych lokacji do grupy dostępności  

1.  Uruchom **Instalatora programu Configuration Manager** z  **&lt;folder instalacji lokacji programu Configuration Manager\>\BIN\X64\setup.exe**.  

2.  Na stronie **Pierwsze kroki** wybierz pozycję **Przeprowadź obsługę lokacji lub zresetuj tę lokację**, a następnie kliknij przycisk **Dalej**.  

3.  Wybierz opcję **Modyfikuj konfigurację serwera SQL** , a następnie kliknij przycisk **Dalej**.  

4.  Skonfiguruj ponownie następujące elementy dla bazy danych lokacji:  

    -   **Nazwa serwera SQL:** Wprowadź nazwę wirtualną dla odbiornika grupy dostępności, który został skonfigurowany podczas tworzenia grupy dostępności. Nazwa wirtualnej powinna być pełną nazwę DNS, jak  **&lt;endpointServer\>. fabrikam.com**  

    -   **Wystąpienie:** Ta wartość musi być pusty, aby określić wystąpienie domyślne dla odbiornika grupy dostępności grupy dostępności.  Jeśli bieżąca baza danych lokacji jest zainstalowana w nazwanym wystąpieniu, ta nazwa będzie widoczna i należy ją wyczyścić.  

    -   **Baza danych:** Pozostaw nazwę wyświetlaną. Jest to nazwa bieżącej bazy danych lokacji.  

5.  Po podaniu informacji dotyczących nowej lokalizacji bazy danych zamknij Instalator, wykonując normalne czynności procedury i konfiguracji.  

##  <a name="bkmk_change"></a> Dodawanie lub usuwanie elementów członkowskich aktywnej grupy dostępności  
 Po używa hostowanej w grupie dostępności bazy danych lokacji programu Configuration Manager można usunąć członka repliki lub dodać dodatkowe replik (not przekroczenie podstawowego i dwa węzły dodatkowej).  

#### <a name="to-add-a-new-replica-member"></a>Aby dodać nowy element członkowski repliki  

1.  Dodaj nowy serwer jako replikę pomocniczą do grupy dostępności. Zobacz  [Add a Secondary Replica to an Availability Group (SQL Server)](https://msdn.microsoft.com/library/hh213247\(v=sql.120\).aspx)(SQL Server — Dodawanie repliki pomocniczej do grupy dostępności) w bibliotece dokumentacji programu SQL Server.  

2.  Zatrzymaj witrynę programu Configuration Manager za pomocą **Preinst.exe/stopsite** zobacz [narzędzia Obsługa hierarchii (Preinst.exe) dla programu System Center Configuration Manager](../../../../core/servers/manage/hierarchy-maintenance-tool-preinst.exe.md).  

3.  Skonfiguruj każdą replikę pomocniczą. W celu skonfigurowania każdej repliki pomocniczej w grupie dostępności wykonaj następujące czynności:  

    1.  Przełącz ręcznie w tryb pracy awaryjnej replikę podstawową, tworząc z niej nową replikę pomocniczą. Zobacz [Perform a Planned Manual Failover of an Availability Group](https://msdn.microsoft.com/library/hh231018\(v=sql.120\).aspx) (Wykonywanie zaplanowanego ręcznego przełączania awaryjnego grupy dostępności) w dokumentacji programu SQL Server.  

    2.  Skonfiguruj bazę danych na nowym serwerze, nadając jej właściwość Trustworthy i włączając integrację środowiska CLR. Zobacz [TRUSTWORTHY Database Property](https://msdn.microsoft.com/library/ms187861\(v=sql.120\).aspx) (Właściwość TRUSTWORTHY bazy danych) i  [Enabling CLR Integration](https://msdn.microsoft.com/library/ms131048\(v=sql.120\).aspx)(Włączanie integracji środowiska CLR) w dokumentacji programu SQL Server.  

4.  Uruchom ponownie lokację, uruchamiając usługi Menedżer składników lokacji (**sitecomp**) i **SMS_Executive** .  

#### <a name="to-remove-a-replica-member-from-the-availability-group"></a>Aby usunąć element członkowski repliki z grupy dostępności  

-   Skorzystaj z informacji zawartych w temacie [Remove a Secondary Replica from an Availability Group](https://msdn.microsoft.com/library/hh213149\(v=sql.120\).aspx) (Usuwanie repliki pomocniczej z grupy dostępności) w dokumentacji programu SQL Server.  

##  <a name="bkmk_remove"></a> Przenoszenie bazy danych lokacji z grupy dostępności z powrotem do pojedynczego wystąpienia programu SQL Server  
 Gdy nie chcesz już obsługiwać bazy danych lokacji w grupie dostępności, użyj poniższej procedury.  

#### <a name="to-move-the-site-database-from-an-availability-group-back-to-a-single-instance-sql-server"></a>Aby przenieść bazę danych lokacji z grupy dostępności do pojedynczego wystąpienia programu SQL Server  

1.  Zatrzymaj witrynę programu Configuration Manager za pomocą następującego polecenia:  
     **Preinst.exe /stopsite**.  Aby uzyskać więcej informacji, zobacz [Narzędzie Obsługa hierarchii (Preinst.exe) dla programu System Center Configuration Manager](../../../../core/servers/manage/hierarchy-maintenance-tool-preinst.exe.md).  

2.  Użyj programu SQL Server, aby utworzyć pełną kopię zapasową bazy danych lokacji z repliki podstawowej. Informacje na temat sposobu ukończenia tego kroku zawiera temat [Create a Full Database Backup](https://msdn.microsoft.com/library/ms187510\(v=sql.120\).aspx) (Tworzenie pełnej kopii zapasowej bazy danych) w dokumentacji programu SQL Server.  

3.  Jeśli serwer, który obsługuje replikę podstawową dla grupy dostępności, będzie teraz obsługiwać pojedyncze wystąpienie bazy danych lokacji, możesz pominąć ten krok:  

    -   Użyj programu SQL Server do przywrócenia kopii zapasowej bazy danych lokacji do serwera, który będzie obsługiwał bazę danych lokacji.  Zobacz temat [Restore a Database Backup (SQL Server Management Studio)](https://msdn.microsoft.com/library/ms177429\(v=sql.120\).aspx) (SQL Server Management Studio — Przywracanie kopii zapasowej bazy danych) w bibliotece dokumentacji programu SQL Server.  

4.  W przywróconej bazie danych lokacji zmień model kopii zapasowej bazy danych lokacji z **PEŁNY** na **PROSTY**.  Zobacz [View or Change the Recovery Model of a Database](https://msdn.microsoft.com/library/ms189272\(v=sql.120\).aspx) (Wyświetlanie lub zmiana modelu odzyskiwania bazy danych) w dokumentacji programu SQL Server.  

5.  Uruchom **Instalatora programu Configuration Manager** z  **&lt;folder instalacji lokacji programu Configuration Manager\>\BIN\X64\setup.exe**.  

6.  Na stronie **Pierwsze kroki** wybierz pozycję **Przeprowadź obsługę lokacji lub zresetuj tę lokację**, a następnie kliknij przycisk **Dalej**.  

7.  Wybierz opcję **Modyfikuj konfigurację serwera SQL** , a następnie kliknij przycisk **Dalej**.  

8.  Skonfiguruj ponownie następujące elementy dla bazy danych lokacji:  

    -   **Nazwa serwera SQL:** Wprowadź nazwę serwera, na którym teraz znajduje się baza danych lokacji.  

    -   **Wystąpienie:** Określ nazwanego wystąpienia, które obsługuje bazę danych lokacji, lub pozostaw to pole puste, jeśli baza danych znajduje się w domyślnym wystąpieniu.  

    -   **Baza danych:** Pozostaw nazwę wyświetlaną. Jest to nazwa bieżącej bazy danych lokacji.  

9. Po podaniu informacji dotyczących nowej lokalizacji bazy danych zamknij Instalator, wykonując normalne czynności procedury i konfiguracji. Po zakończeniu instalacji lokacja zostanie ponownie uruchomiona i rozpocznie korzystanie z nowej lokalizacji bazy danych.  

10. Aby wyczyścić serwery, które były elementami członkowskimi grupy dostępności, postępuj zgodnie ze wskazówkami w temacie [Remove an Availability Group](https://msdn.microsoft.com/library/ff878113\(v=sql.120\).aspx) (Usuwanie grupy dostępności) w dokumentacji programu SQL Server.

