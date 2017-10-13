---
title: Odzyskiwanie lokacji | Dokumentacja firmy Microsoft
description: "Dowiedz się odzyskać witryn w programie System Center Configuration Manager."
ms.custom: na
ms.date: 6/5/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 19539f4d-1667-4b4c-99a1-9995f12cf5f7
caps.latest.revision: 
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: f5aff56e9948536944140fbadb0539c7a4e20f26
ms.sourcegitcommit: 5ca89204716750eaaceb01bba40b35b85c7122ba
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2017
---
#  <a name="recover-a-configuration-manager-site"></a>Odzyskiwanie lokacji programu Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Uruchom odzyskiwanie lokacji programu Configuration Manager po awarii lokacji programu Configuration Manager lub w bazie danych lokacji dojdzie do utraty danych. Do podstawowych zadań funkcji odzyskiwania lokacji należy naprawianie i ponowne synchronizowanie danych, aby zapobiegać przerwom w wykonywaniu operacji.

Sekcje w tym temacie ułatwiają odzyskiwanie lokacji programu Configuration Manager. Aby utworzyć kopię zapasową, zobacz [kopii zapasowej programu Configuration Manager](/sccm/protect/understand/backup-and-recovery).

## <a name="considerations-before-recovering-a-site"></a>Zagadnienia dotyczące przed odzyskaniem lokacji
**Należy użyć tej samej wersji i wydania programu SQL Server:** Na przykład przywracanie bazy danych uruchamianej w programie SQL Server 2014 do programu SQL Server 2016 nie jest obsługiwane. Podobnie Przywracanie bazy danych lokacji uruchamianej w wersji Standard programu SQL Server 2016 do wersji Enterprise programu SQL Server 2016 nie jest obsługiwane.
-   Program SQL Server nie może działać w **trybie jednego użytkownika**.
-   Upewnij się, że pliki MDF i LDF są prawidłowe. W przypadku odzyskiwania lokacji nie ma żadnych sprawdzenia stanu przywracanych plików.

**Jeśli używasz programu SQL Server zawsze włączone grupy dostępności programu do obsługi bazy danych lokacji:** Zmodyfikuj swoje plany odzyskiwania, zgodnie z opisem w [przygotowanie do korzystania z programu SQL Server AlwaysOn](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database#changes-for-site-recovery).

**Jeśli w przypadku używania replik bazy danych:** Po przywróceniu baz danych lokacji skonfigurowanych pod kątem replik baz danych przed użyciem tych replik należy ponownie skonfigurować każdą replikę baz danych, tworząc jeszcze raz zarówno publikacje, jak i subskrypcje.

## <a name="determine-your-recovery-options"></a>Ustalanie dostępnych opcji odzyskiwania
Istnieją dwa główne obszary wziąć pod uwagę dla serwera lokacji głównej programu Configuration Manager i odzyskiwanie centralnej lokacji administracyjnej; **serwera lokacji** i **bazy danych lokacji**.
Poniższe sekcje ułatwiają wybrać najlepsze ustawienia dla scenariusza odzyskiwania.

> [!NOTE]   
> Gdy Instalator wykryje istniejącą lokację programu Configuration Manager na serwerze, można rozpocząć odzyskiwanie lokacji, ale opcje odzyskiwania serwera lokacji są ograniczone. Na przykład, jeśli Instalator zostanie uruchomiony na istniejącym serwerze lokacji, po wybraniu opcji odzyskiwania będzie można odzyskać serwer bazy danych lokacji, opcja odzyskiwania serwera lokacji będzie jednak wyłączona.

### <a name="site-server-recovery-options"></a>Opcje odzyskiwania serwera lokacji
Uruchom Instalatora z kopii **dysku CD. Najnowsze** folder utworzony poza folder instalacji programu Configuration Manager.
-   Po uruchomieniu Instalatora programu Configuration Manager z **Start** menu na serwerze lokacji **odzyskać lokację** opcja jest niedostępna.
-   Jeśli żadnych aktualizacji z poziomu konsoli programu Configuration Manager jest zainstalowany, przed wprowadzeniem kopii zapasowej, możesz nie może pomyślnie zainstalować ponownie lokacji za pomocą Instalatora z nośnika instalacyjnego lub ścieżka instalacji programu Configuration Manager.

Następnie wybierz **odzyskać lokację** opcji. Masz następujące opcje odzyskiwania serwera lokacji nie powiodło się:

-   **Odzyskaj serwer lokacji przy użyciu istniejącej kopii zapasowej:** Użyj tej opcji, jeśli masz kopię zapasową serwera lokacji programu Configuration Manager, który został utworzony na serwerze lokacji w ramach **Utwórz kopię zapasową serwera lokacji** zadanie konserwacji przed awarią lokacji. Lokacja zostanie zainstalowana ponownie, a ustawienia lokacji zostaną skonfigurowane na podstawie lokacji, której kopię zapasową utworzono.
-   **Zainstaluj ponownie serwer lokacji:** Użyj tej opcji, jeśli nie masz kopii zapasowej serwera lokacji. Serwer lokacji zostanie zainstalowany ponownie, a użytkownik będzie musiał określić ustawienia lokacji w taki sam sposób jak podczas instalacji początkowej.
  -   Należy użyć tego samego kodu lokacji i nazwa bazy danych lokacji, który został użyty podczas pierwszej instalacji lokacji nie powiodło się.
  -   Można ponownie zainstalować lokacji na nowym komputerze z systemem nowego systemu operacyjnego.
  -   Na komputerze musi być tą samą nazwą FQDN pierwotnego serwera lokacji.   

### <a name="site-database-recovery-options"></a>Opcje odzyskiwania bazy danych lokacji
Po uruchomieniu Instalatora będą dostępne następujące opcje odzyskiwania bazy danych lokacji:
-   **Odzyskiwanie bazy danych lokacji przy użyciu zestawu kopii zapasowych:** Użyj tej opcji, jeśli użytkownik dysponuje kopią zapasową bazy danych lokacji programu Configuration Manager, który został utworzony jako część **Utwórz kopię zapasową serwera lokacji** zadania obsługi lokacji przed awarią bazy danych lokacji. Jeśli użytkownik ma hierarchię, zmiany dokonane w bazie danych lokacji po utworzeniu ostatniej kopii zapasowej bazy danych lokacji zostaną pobrane z centralnej lokacji administracyjnej dla lokacji głównej lub z lokacji głównej odniesienia dla centralnej lokacji administracyjnej. Po odzyskaniu bazy danych lokacji autonomicznej lokacji głównej zmiany lokacji po utworzeniu ostatniej kopii zapasowej zostaną utracone.

   W przypadku odzyskiwania bazy danych lokacji w hierarchii proces odzyskiwania jest różny dla centralnej lokacji administracyjnej i lokacji głównej oraz zależy również od tego, czy ostatnia kopia zapasowa została utworzona w okresie przechowywania funkcji monitorowania zmian programu SQL Server, czy poza tym okresem. Więcej informacji znajduje się w sekcji [Scenariusze odzyskiwania bazy danych lokacji](##site-database-recovery-scenarios) w tym temacie.
  > [!NOTE]   
  > Odzyskiwanie nie powiedzie się, jeśli użytkownik wybierze opcję przywracania bazy danych lokacji przy użyciu zestawu kopii zapasowych, a baza danych lokacji już istnieje.  

-   **Utwórz nową bazę danych dla tej witryny:** Użyj tej opcji, jeśli nie masz kopii zapasowej bazy danych lokacji programu Configuration Manager. Jeśli użytkownik ma hierarchię, zostanie utworzona nowa baza danych, a dane zostaną odzyskane przy użyciu zreplikowanych danych z centralnej lokacji administracyjnej dla lokacji głównej lub z lokacji głównej odniesienia dla centralnej lokacji administracyjnej. Ta opcja jest niedostępna, jeśli użytkownik odzyskuje autonomiczną lokację główną lub centralną lokację administracyjną nie mającą lokacji głównych.

-   **Użyj ręcznie odzyskanej bazy danych lokacji:** Użyj tej opcji, gdy zostało już wykonane przywrócenie bazy danych lokacji programu Configuration Manager, ale musi zakończyć proces odzyskiwania.
    -   Configuration Manager można odzyskać bazy danych lokacji z zadania obsługi kopii zapasowej programu Configuration Manager lub z kopii zapasowej bazy danych lokacji utworzonej za pomocą programu DPM lub inny proces. Po przywróceniu bazy danych lokacji przy użyciu metody poza programem Configuration Manager należy uruchomić Instalatora i wybrać tę opcję, aby ukończyć odzyskiwanie bazy danych lokacji.

    > [!NOTE]   
    > Jeśli używasz programu DPM, aby utworzyć kopię zapasową bazy danych lokacji, należy użyć procedur programu DPM do przywrócenia bazy danych lokacji w określonej lokalizacji przed kontynuowaniem procesu przywracania w programie Configuration Manager. Więcej informacji na temat programu DPM zawiera [Data Protection Manager Documentation Library (Biblioteka dokumentacji programu Data Protection Manager)]() w witrynie TechNet.    

    -   Jeśli użytkownik ma hierarchię, zmiany dokonane w bazie danych lokacji po utworzeniu ostatniej kopii zapasowej bazy danych lokacji zostaną pobrane z centralnej lokacji administracyjnej dla lokacji głównej lub z lokacji głównej odniesienia dla centralnej lokacji administracyjnej. Po odzyskaniu bazy danych lokacji autonomicznej lokacji głównej zmiany lokacji po utworzeniu ostatniej kopii zapasowej zostaną utracone.     


-   **Pomiń odzyskiwanie bazy danych:** Ta opcja nie danych nastąpiła utrata na serwerze bazy danych lokacji programu Configuration Manager. Ta opcja jest prawidłowa tylko wtedy, gdy baza danych lokacji znajduje się na innym komputerze niż odzyskiwany serwer lokacji.

### <a name="sql-server-change-tracking-retention-period"></a>Okres przechowywania funkcji śledzenia zmian programu SQL Server
Funkcja monitorowania zmian jest włączona dla bazy danych lokacji w programie SQL Server. Śledzenie zmian umożliwia programowi Configuration Manager zapytania, aby uzyskać informacje o zmianach dokonanych w tabelach bazy danych po stanie z określonego momentu w czasie. Okres przechowywania określa, jak długo są przechowywane informacje o monitorowaniu zmian. Domyślny okres przechowywania dla bazy danych lokacji wynosi 5 dni. Przebieg procesu odzyskiwania bazy danych lokacji zależy od tego, czy kopia zapasowa została utworzona w okresie przechowywania danych czy poza tym okresem. Na przykład, jeśli serwer bazy danych lokacji ulegnie awarii, a ostatnia kopia zapasowa została wykonana 7 dni temu, kopia zapasowa została utworzona poza okresem przechowywania.

Aby uzyskać więcej informacji na temat wewnętrzne śledzenia zmian programu SQL Server zobacz następujące blogi zespołu programu SQL Server: [Oczyszczanie — część 1 śledzenia zmian](https://blogs.msdn.microsoft.com/sql_server_team/change-tracking-cleanup-part-1/) i [oczyszczania śledzenia zmian — część 2](https://blogs.msdn.microsoft.com/sql_server_team/change-tracking-cleanup-part-2).

### <a name="reinitialization-of-site-or-global-data"></a>Ponowne inicjowanie lokacji lub danych globalnych
Proces ponownego inicjowania danych lokacji lub danych globalnych zastępuje istniejące dane w bazie danych lokacji danymi z innej bazy danych lokacji. Na przykład, gdy lokacja ABC ponownie zainicjuje dane z lokacji XYZ, zostaną wykonane następujące kroki:
-   Dane zostaną skopiowane z lokacji XYZ do lokacji ABC.
-   Istniejące dane dla lokacji XYZ zostaną usunięte z bazy danych lokacji w lokacji ABC.
-   Dane skopiowane z lokacji XYZ zostaną wstawione do bazy danych lokacji w lokacji ABC.

#### <a name="example-scenario-1"></a>Przykładowy scenariusz 1
**Lokacja główna ponownie inicjuje dane globalne z centralnej lokacji administracyjnej:** Proces odzyskiwania usuwa istniejące dane globalne lokacji głównej w bazie danych lokacji głównej i zastępuje je danymi globalne dane skopiowane z centralnej lokacji administracyjnej.

#### <a name="example-scenario-2"></a>Przykładowy scenariusz 2
**Centralna lokacja administracyjna ponownie inicjuje dane lokacji z lokacji głównej:** Proces odzyskiwania usuwa istniejące dane tej lokacji głównej w bazie danych lokacji administracji centralnej i zastępuje je danymi z danymi lokacji skopiowanymi z lokacji głównej. Proces nie wpływa na dane lokacji innych lokacji głównych.

### <a name="site-database-recovery-scenarios"></a>Scenariusze odzyskiwania bazy danych lokacji
Po przywróceniu bazy danych lokacji z kopii zapasowej programu Configuration Manager podejmie próbę przywrócenia zmian w lokacji i danych globalnych po utworzeniu ostatniej kopii zapasowej bazy danych. Poniżej opisano akcje inicjowane uruchomieniu tego programu Configuration Manager po przywróceniu bazy danych lokacji z kopii zapasowej.

**Odzyskana lokacja jest centralną lokacją administracyjną:**
-   **Kopia zapasowa bazy danych w okresie przechowywania funkcji monitorowania zmian**
    -   **Dane globalne:** Zmiany danych globalnych po wykonaniu kopii zapasowej są replikowane ze wszystkich lokacji głównych.
    -   **Dane lokacji:** Zmiany danych lokacji po wykonaniu kopii zapasowej są replikowane ze wszystkich lokacji głównych.


-   **Kopia zapasowa bazy danych poza okresem przechowywania funkcji monitorowania zmian**
    -   **Dane globalne:** Centralna lokacja administracyjna ponownie inicjuje dane globalne z lokacji głównej odniesienia, jeśli została ona określona. Następnie wszystkie inne lokacje główne ponownie inicjują dane globalne z centralnej lokacji administracyjnej. Jeśli nie określono lokacji odniesienia, wszystkie lokacje główne ponownie inicjują dane globalne (przywrócone z kopii zapasowej) z centralnej lokacji administracyjnej.
    -   **Dane lokacji:** Centralna lokacja administracyjna ponownie inicjuje dane lokacji ze wszystkich lokacji głównych.


**Odzyskana lokacja to lokacja główna:**
-   **Kopia zapasowa bazy danych w okresie przechowywania funkcji monitorowania zmian**
    -   **Dane globalne:** Zmiany danych globalnych po wykonaniu kopii zapasowej są replikowane z centralnej lokacji administracyjnej.
    -   **Dane lokacji:** Centralna lokacja administracyjna ponownie inicjuje dane lokacji z lokacji głównej. Zmiany dokonane po wykonaniu kopii zapasowej zostaną utracone, ale większość danych są generowane przez klientów wysyłających informacje do lokacji głównej.


-   **Kopia zapasowa bazy danych poza okresem przechowywania funkcji monitorowania zmian**
    -   **Dane globalne:** Lokacja główna ponownie inicjuje dane globalne z centralnej lokacji administracyjnej.
    -   **Dane lokacji:** Centralna lokacja administracyjna ponownie inicjuje dane lokacji z lokacji głównej. Zmiany dokonane po wykonaniu kopii zapasowej zostaną utracone, ale większość danych są generowane przez klientów wysyłających informacje do lokacji głównej.

## <a name="site-recovery-procedures"></a>Procedury odzyskiwania lokacji
Aby odzyskać serwer lokacji i bazę danych lokacji, należy użyć jednej z poniższych procedur.

### <a name="to-start-a-site-recovery-in-the-setup-wizard"></a>Aby rozpocząć odzyskiwanie lokacji w Kreatorze instalacji:
1.  Kopiuj [dysku CD. Najnowszy folder](/sccm/core/servers/manage/the-cd.latest-folde) do lokalizacji poza folderem instalacji programu Configuration Manager.
Z kopii dysku CD. Najnowszy folder, uruchom Kreatora instalacji programu Configuration Manager.

2.  Na stronie **Wprowadzenie** wybierz opcję **Odzyskaj lokację**, a następnie kliknij przycisk **Dalej**.

3.  Ukończ kreatora, używając opcji odpowiednich dla danego odzyskiwania lokacji.

  -   W trakcie odzyskiwania Instalator określi port usługi SQL Server Service Broker (SSB) używany przez program SQL Server. Nie należy zmieniać tego ustawienia portu podczas odzyskiwania, w przeciwnym razie po jego ukończeniu replikacja danych nie będzie działać prawidłowo.

  -   Możesz określić oryginalną lub nową ścieżkę do użycia podczas instalacji programu Configuration Manager w Kreatorze instalacji.

### <a name="to-start-an-unattended-site-recovery"></a>Aby rozpocząć nienadzorowane odzyskiwanie lokacji:
  1.    Przygotuj skrypt instalacji nienadzorowanej pod kątem opcji wymaganych do odzyskania lokacji.  Zobacz [klucze plików skryptu instalacji nienadzorowanej lokacji odzyskiwania](/sccm/protect/understand/unattended-site-recovery-script-file-keys).

  2.    Uruchom Instalatora programu Configuration Manager za pomocą polecenia **/script** opcji. Na przykład jeśli plik inicjowania Instalatora ma nazwę ConfigMgrUnattend.ini i jest zapisany w katalogu C:\Temp komputera, na którym jest uruchomiony Instalator, polecenie będzie następujące: **Setup/Script C:\temp\ConfigMgrUnattend.ini**.

  > [!NOTE]   
  >  Po odzyskaniu centralnej lokacji administracyjnej replikacja niektórych danych lokacji z lokacji podrzędnych może się nie powieść. Może to obejmować spis sprzętu, spis oprogramowania i komunikaty o stanie.
  >
  >  W takiej sytuacji należy ponownie zainicjować element **ConfigMgrDRSSiteQueue** w celu uruchomienia replikacji bazy danych.  Aby to zrobić, użyj **programu SQL Server Manager** do Uruchom następującą kwerendę programu Configuration Manager bazy danych lokacji w centralnej lokacji administracyjnej:
  >
  >  **IF EXISTS (SELECT \* FROM sys.service_queues WHERE name = 'ConfigMgrDRSSiteQueue' AND is_receive_enabled = 0)**
  >
  >  **ALTER QUEUE [dbo].[ConfigMgrDRSSiteQueue] WITH STATUS = ON**


## <a name="post-recovery-tasks"></a>Zadania po odzyskiwaniu
Po odzyskaniu lokacji należy wykonać szereg zadań umożliwiających ukończenie procesu odzyskiwania lokacji. Informacje w poniższych sekcjach mogą ułatwić ukończenie procesu odzyskiwania lokacji.

### <a name="re-enter-user-account-passwords"></a>Ponowne wprowadzanie haseł kont użytkowników
Po odzyskaniu serwera lokacji należy ponownie wprowadzić hasła kont użytkowników określonych dla lokacji, ponieważ są one resetowane podczas odzyskiwania lokacji. Konta są wyświetlane na stronie **Zakończ** Kreatora instalacji po ukończeniu odzyskiwania lokacji i zapisywane w pliku C:\ConfigMgrPostRecoveryActions.html na odzyskanym serwerze lokacji.

#### <a name="to-re-enter-user-account-passwords-after-site-recovery"></a>Aby ponownie wprowadzić hasła kont użytkowników po odzyskaniu lokacji:

1.  Otwórz konsolę programu Configuration Manager i połącz się z odzyskaną lokacją.

2.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.

3.  W obszarze roboczym **Administracja** rozwiń węzeł **Zabezpieczenia**, a następnie kliknij przycisk **Konta**.

4.  Dla każdego konta, w którym należy ponownie wprowadzić hasło wykonaj następujące czynności:

    1.  Wybierz konto z listy kont zidentyfikowanych po odzyskaniu lokacji. Listę kont zawiera plik C:\ConfigMgrPostRecoveryActions.html na odzyskanym serwerze lokacji.

    2.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości** , aby otworzyć właściwości konta.

    3.  Na karcie **Ogólne** kliknij przycisk **Ustaw**, a następnie wprowadź ponownie hasła konta.

    4.  Kliknij przycisk **Weryfikuj**, wybierz odpowiednie źródło danych dla wybranego konta użytkownika, a następnie kliknij opcję **Testuj połączenie** , aby sprawdzić, czy można połączyć konto użytkownika ze źródłem danych.

    5.  Kliknij przycisk **OK** , aby zapisać zmiany haseł, a następnie kliknij przycisk **OK**.

### <a name="re-enter-sideloading-keys"></a>Ponowne wprowadzanie kluczy ładowania bezpośredniego
Po odzyskaniu serwera lokacji należy ponownie wprowadzić klucze pobierania lokalnego systemu Windows wprowadzone dla tej lokacji. Jest to konieczne, gdyż podczas odzyskiwania dochodzi do zresetowania tych kluczy. Po ich ponownym wprowadzeniu klucze pobierania lokalnego, liczba **użyte aktywacje** kolumny kluczy ładowania bezpośredniego systemu Windows zostanie zresetowana w konsoli programu Configuration Manager. Na przykład, załóżmy, że przed awarią lokacji **łączna liczba aktywacji** miał wartość **100** i **użyte aktywacje** w **90** liczbę kluczy wykorzystanych przez urządzenia. Po odzyskaniu lokacji w kolumnie **Łączna liczba aktywacji** jest nadal wyświetlana liczba **100**, lecz w kolumnie **Użyte aktywacje** znajduje się nieprawidłowa wartość **0**. Jednak wprowadzenie 10 nowych urządzeń do kluczy pobierania lokalnego wyczerpie zapas kluczy i uniemożliwi zastosowanie nowego klucza do kolejnego urządzenia.

### <a name="recreate-the-microsoft-intune-subscription"></a>Ponowne tworzenie subskrypcji usługi Microsoft Intune
 W przypadku odzyskiwania serwera lokacji programu Configuration Manager po komputera serwera lokacji ponownie obraz zostanie utworzony, nie jest przywracany subskrypcję Microsoft Intune. Po odzyskaniu lokacji należy nawiązać ponownie połączenie Twojej subskrypcji.  Nie należy tworzyć nowe żądanie APN, ale zamiast tego przekazać bieżącego prawidłową — plik PEM przekazany podczas ostatniego zarządzania w systemie iOS został skonfigurowany lub odnowienia. Aby uzyskać więcej informacji, zobacz [Konfigurowanie subskrypcji usługi Microsoft Intune](/sccm/mdm/deploy-use/configure-intune-subscription).

### <a name="configure-ssl-for-site-system-roles-that-use-iis"></a>Konfiguracja protokołu SSL w rolach systemu lokacji używających usług IIS
Po odzyskaniu systemu lokacji z serwerem IIS i skonfigurowanym przed awarią protokołem HTTPS, należy zrekonfigurować serwer IIS tak, aby używany w nim był certyfikat serwera sieci Web.

### <a name="reinstall-hotfixes-in-the-recovered-site-server"></a>Ponowna instalacja poprawek w odzyskanym serwerze lokacji
Po odzyskaniu serwera lokacji należy ponownie zainstalować wszystkie poprawki zastosowane do serwera lokacji. Wyświetl listę uprzednio zainstalowanych poprawek na **Zakończono** strony Kreatora instalacji po odzyskaniu lokacji. Ta lista jest także zapisywane w **C:\ConfigMgrPostRecoveryActions.html** na odzyskanym serwerze lokacji.

### <a name="recover-custom-reports-on-the-computer-running-reporting-services"></a>Odzyskiwanie niestandardowych raportów na komputerze z uruchomioną usługą Reporting Services
Przy wcześniejszym utworzeniu kopii zapasowej serwera raportów, istnieje możliwość odzyskania niestandardowych raportów usług Reporting Services utraconych po jego awarii. Więcej informacji o przywracaniu niestandardowych raportów w programie Reporting Services znajduje się w sekcji [Tworzenie i przywracanie kopii zapasowych w instalacji programu Reporting Services](http://go.microsoft.com/fwlink/p/?LinkId=228724) w dokumentacji programu SQL Server 2008 — Books Online.

### <a name="recover-content-files"></a>Odzyskiwanie plików zawartości
 Chociaż baza danych lokacji zawiera informacje o miejscu przechowywania zawartości na serwerze lokacji, to pliki zawartości nie są ujęte w procesach tworzenia i odzyskiwania kopii zapasowej. Aby całkowicie odzyskać pliki zawartości, należy przywrócić bibliotekę zawartości oraz pliki źródłowe pakietu do początkowej lokacji. Istnieje kilka metod odzyskiwania plików zawartości. Najprostszą jest przywrócenie plików z kopii zapasowej systemu plików na serwerze lokacji.

 Jeśli nie masz kopii zapasowej systemu plików dla plików źródłowych pakietu, należy ręcznie skopiować lub pobrać tak samo jak pierwotnym tworzeniu pakietu. Aby znaleźć lokalizację źródłową wszystkich pakietów i aplikacji, można uruchomić następujące zapytanie w programie SQL Server: `SELECT * FROM v_Package`. Możesz określić lokację źródłową pakietu za pomocą trzech pierwszych znaków identyfikatora pakietu. Na przykład jeśli identyfikator pakietu to CEN00001, kod lokacji źródłowej to CEN. Pliki źródłowe pakietu muszą być przywrócone do tej samej lokacji, w której znajdowały się przed awarią.

 Jeśli kopia zapasowa systemu plików z biblioteką zawartości nie jest dostępna, masz następujące opcje przywracania:

-   **Zaimportowanie wstępnie przygotowanego pliku zawartości**: W przypadku hierarchii programu Configuration Manager można utworzyć wstępnie przygotowany plik zawartości ze wszystkimi pakietami i aplikacjami w innej lokacji, a następnie zaimportować wstępnie przygotowanego pliku zawartości, aby odzyskać bibliotekę zawartości na serwerze lokacji.

-   **Aktualizacja zawartości**: Po uruchomieniu akcji aktualizacji zawartości dla typu wdrożenia pakietu lub aplikacji zawartość jest kopiowana ze źródła pakietu do biblioteki zawartości. Aby to działanie zakończyło się pomyślnie, pliki źródłowe pakietu muszą być dostępne w początkowej lokacji. Działanie to należy wykonać we wszystkich pakietach i aplikacjach.

### <a name="recover-custom-software-updates-on-the-computer-running-updates-publisher"></a>Odzyskiwanie niestandardowych aktualizacji oprogramowania na komputerze z uruchomionym programem Updates Publisher
Gdy Updates Publisher pliki bazy danych zostały uwzględnione w planu tworzenia kopii zapasowej, można odzyskać bazy danych w przypadku awarii na komputerze, na którym jest uruchomiony Updates Publisher. Więcej informacje dotyczących programu Updates Publisher znajduje się w temacie [System Center Updates Publisher 2011](http://go.microsoft.com/fwlink/p/?LinkId=228726) w bibliotece TechCenter dla programu System Center.

Przywracanie bazy danych programu Updates Publisher, należy użyć następującej procedury.

#### <a name="to-restore-the-updates-publisher-2011-database"></a>Aby przywrócić bazę danych programu Updates Publisher 2011
1.  Zainstaluj ponownie Updates Publisher na odzyskanym komputerze.

2.  Skopiuj plik bazy danych (Scupdb.sdf) z folderu docelowego kopii zapasowych %*USERPROFILE*%\AppData\Local\Microsoft\System Center Updates Publisher 2011\5.00.1727.0000\ na komputerze z uruchomionym programem Updates Publisher.

3.  Gdy więcej niż jednego użytkownika programem Updates Publisher na komputerze, należy skopiować wszystkich plików bazy danych do lokacji w profilach użytkowników.

### <a name="user-state-migration-data"></a>Dane migracji stanu użytkownika
Częścią właściwości systemu lokacji punktu migracji stanu jest określenie folderów, w których znajdują się dane migracji stanu użytkownika. Po odzyskaniu serwera z folderem, w którym znajdują się dane migracji stanu użytkownika należy ręcznie przywrócić te dane migracji na serwer z takimi samymi folderami, w których znajdowały się dane przed awarią.

### <a name="regenerate-the-certificates-for-distribution-points"></a>Ponowne generowanie certyfikatów dla punktów dystrybucji
Po odzyskaniu lokacji plik distmgr.log może zawierać następujący wpis dotyczący co najmniej jeden punkt dystrybucji: **Nie można odszyfrować danych PFX certyfikatu**. Ten wpis informuje, że lokacja nie może odszyfrować danych certyfikatu punktu dystrybucji. Aby rozwiązać ten problem, należy ponownie wygenerować lub ponownie zaimportować certyfikat dla punktów dystrybucji dotyczy. W tym celu możesz użyć polecenia cmdlet programu PowerShell [Set-CMDistributionPoint](https://technet.microsoft.com/library/jj821872\(v=sc.20\).aspx).

### <a name="update-certificates-used-for-cloud-based-distribution-points"></a>Aktualizacja certyfikatów używanych w chmurowych punktach dystrybucji
 Program Configuration Manager wymaga certyfikatu zarządzania używa serwer lokacji do komunikacji między punktem dystrybucji w chmurze. Po odzyskaniu lokacji należy ręcznie zaktualizować certyfikaty dla chmurowych punktów dystrybucji.

## <a name="recover-a-secondary-site"></a>Odzyskiwanie lokacji dodatkowej
 Menedżer konfiguracji nie obsługuje tworzenia kopii zapasowej bazy danych w lokacji dodatkowej, ale obsługuje odzyskiwanie przez ponowne zainstalowanie lokacji dodatkowej. Odzyskiwania lokacji dodatkowej jest wymagany, gdy lokacji dodatkowej programu Configuration Manager nie powiodło się.

### <a name="requirements-for-reinstalling-a-secondary-site"></a>Wymagania dotyczące ponowne zainstalowanie lokacji dodatkowej
-   Komputer musi spełniać wszystkie wymagania wstępne dotyczące lokacji i miały właściwe zabezpieczenia prawa.
-   Należy używać tej samej ścieżki instalacji, którego użyto w uszkodzonej lokacji.
-   Aby pomyślnie odzyskać lokację dodatkową, należy użyć komputera z taką samą konfiguracją, co w komputerze, który uległ awarii, w tym nazwę FQDN.
-   Komputer musi mieć taką samą konfigurację programu SQL Server jako lokacji nie powiodło się.
  -   Podczas odzyskiwania lokacji dodatkowej programu Configuration Manager instaluje program SQL Server Express nie jest już zainstalowany na komputerze.
  -   Wersja i wystąpienie programu SQL Server do bazy danych lokacji dodatkowej muszą być takie same, co przed awarią.

### <a name="to-recover-a-secondary-site"></a>Aby odzyskać lokację dodatkową:
Aby odzyskać lokację dodatkową, należy użyć **odzyskiwanie lokacji dodatkowej** akcji z **witryny** węzeł w konsoli programu Configuration Manager. W przeciwieństwie do odzyskiwania centralnej lokacji administracyjnej lub lokacji głównej podczas odzyskiwania lokacji dodatkowej nie jest używany plik kopii zapasowej. Zamiast tego pliki lokacji dodatkowej są ponownie instalowane na komputerze w lokacji dodatkowej, na którym wystąpiła awaria. Po ponownie instaluje witrynę, dane w lokacji dodatkowej są ponownie inicjowane danymi z nadrzędnej lokacji głównej.

Podczas procesu odzyskiwania programu Configuration Manager sprawdza, czy na komputerze lokacji dodatkowej istnieje biblioteka zawartości oraz czy odpowiednia zawartość jest dostępna. Lokacja dodatkowa użyje istniejącej biblioteki zawartości, o ile zawiera ona odpowiednią zawartość. W przeciwnym razie odzyskanie biblioteki zawartości w odzyskanej lokacji dodatkowej wymaga ponownej dystrybucji lub wstępnego przygotowania zawartości dla odzyskanej lokacji.

Punkt dystrybucji poza lokacją dodatkową nie musi być instalowany ponownie podczas odzyskiwania tej lokacji. Odzyskana lokacja dodatkowa zostanie automatycznie zsynchronizowana ponownie z punktem dystrybucji.

Status odzyskiwania lokacji dodatkowej można sprawdzić za pomocą **Pokaż stan instalacji** akcji z **witryny** węzeł w konsoli programu Configuration Manager.
