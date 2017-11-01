---
title: Kopii zapasowej lokacji
titleSuffix: Configuration Manager
description: "Dowiedz się utworzyć kopię zapasową lokacji przed zdarzeniem awarii lub utraty danych w programie System Center Configuration Manager."
ms.custom: na
ms.date: 6/5/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f7832d83-9ae2-4530-8a77-790e0845e12f
caps.latest.revision: "22"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 7dae5ada647146713b884b09d0eda1c7ec6531ef
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="back-up-a-configuration-manager-site"></a>Tworzenie kopii zapasowej lokacji programu Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Przygotuj podejścia kopii zapasowych i odzyskiwania, aby uniknąć utraty danych. Dla lokacji programu Configuration Manager podejście kopii zapasowych i odzyskiwania może ułatwić Ci odzyskać Lokacje i hierarchie szybciej i przy minimalnej utracie danych.  

Sekcje w tym temacie ułatwiają tworzenie kopii zapasowej lokacji. Aby odzyskać lokację, zobacz [odzyskiwania dla programu Configuration Manager](/sccm/protect/understand/recover-sites).  

## <a name="considerations-before-creating-a-backup"></a>Zagadnienia dotyczące przed utworzeniem kopii zapasowej  
-   **Jeśli używasz programu SQL Server zawsze włączone grupy dostępności programu do obsługi bazy danych lokacji:** Zmodyfikuj swoje plany tworzenia kopii zapasowych i odzyskiwania, zgodnie z opisem w [przygotowanie do korzystania z programu SQL Server AlwaysOn](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database#changes-for-site-backup).

-   Configuration Manager można odzyskać bazy danych lokacji z zadania obsługi kopii zapasowej programu Configuration Manager lub z kopii zapasowej bazy danych lokacji utworzonej za pomocą innego procesu.   

    Na przykład można przywrócić bazy danych lokacji z kopii zapasowej, która jest tworzona w ramach planu obsługi programu Microsoft SQL Server. Można również użyć kopii zapasowej, który jest tworzony przez za pomocą programu Data Protection Manager do tworzenia kopii zapasowych bazy danych lokacji (DPM).

####  <a name="using-data-protection-manager-to-back-up-your-site-database"></a>Używanie programu Data Protection Manager do tworzenia kopii zapasowych bazy danych lokacji
Program System Center 2012 Data Protection Manager (DPM) umożliwia tworzenie kopii zapasowych bazy danych lokacji.

W programie DPM należy utworzyć nową grupę ochrony dla komputera bazy danych lokacji. Na stronie **Wybierz członków grupy** Kreatora tworzenia nowej grupy ochrony należy z listy źródeł danych wybrać Usługę składnika zapisywania programu SMS, a następnie jako właściwego członka grupy wybrać bazę danych lokacji. Więcej informacji o tworzeniu kopii zapasowej bazy danych lokacji za pomocą programu DPM znajduje się w [Data Protection Manager Documentation Library (Bibliotece dokumentacji programu Data Protection Manager)](http://go.microsoft.com/fwlink/?LinkId=272772) w witrynie TechNet.  

> [!IMPORTANT]  
>  Powrót do klastra programu SQL Server używającego wystąpienia nazwanego, ale obsługuje tworzenie kopii zapasowej programu DPM w klastrze programu SQL Server, który korzysta z domyślnego wystąpienia programu SQL Server programu Configuration Manager nie obsługuje programu DPM.  

 Po przywróceniu bazy danych lokacji wykonaj w Instalatorze kroki zmierzające do odzyskania lokacji. Wybierz **Użyj ręcznie odzyskanej bazy danych lokacji** opcję odzyskiwania, aby użyć bazy danych lokacji została odzyskana z programu Data Protection Manager.  

## <a name="backup-maintenance-task"></a>Zadanie obsługi dotyczące tworzenia kopii zapasowej
Tworzenie kopii zapasowych dla lokacji programu Configuration Manager można zautomatyzować poprzez zaplanowanie wstępnie zdefiniowanego zadania obsługi Utwórz kopię zapasową serwera lokacji. To zadanie:

-   jest uruchamiane zgodnie z harmonogramem,
-   tworzy kopię zapasową bazy danych lokacji,
-   tworzy kopię zapasową określonych kluczy rejestru,
-   tworzy kopię zapasową określonych folderów i plików,
-   Tworzy kopię zapasową [dysku CD. Najnowszego folderu](/sccm/core/servers/manage/the-cd.latest-folder)   

Zaplanuj uruchamianie domyślnego zadania kopii zapasowej lokacji nie rzadziej niż co 5 dni. Jest to, ponieważ program Configuration Manager używa *okresu przechowywania śledzenia zmian programu SQL Server* 5 dni.  (Zobacz [okresu przechowywania śledzenia zmian programu SQL Server](/sccm/protect/understand/recover-sites#bkmk_SQLretention) w temacie lokacji odzyskiwania.)

Aby uprościć proces tworzenia kopii zapasowej, można utworzyć **AfterBackup.bat** aby umożliwić wykonywanie akcji po wykonaniu kopii zapasowej automatycznie po pomyślnym uruchomieniu zadania konserwacji kopii zapasowej. Plik AfterBackup.bat zwykle służy do archiwizowania migawki kopii zapasowej w bezpiecznej lokalizacji. Plik AfterBackup.bat służy także do kopiowania plików do folderu kopii zapasowej i uruchamiania innych, uzupełniające zadania tworzenia kopii zapasowych.  

Można utworzyć kopię zapasową centralnej lokacji administracyjnej i lokacji głównej, ale tworzenie kopii zapasowych lokacji dodatkowych lub serwerów systemu lokacji nie jest obsługiwane.

Po uruchomieniu usługi tworzenia kopii zapasowej programu Configuration Manager będzie wykonywać instrukcje zdefiniowane w pliku sterowania kopią zapasową (**&lt;Folder_instalacji_programu_configuration_manager\>\Inboxes\Smsbkup.box\Smsbkup.ctl**). Plik sterowania kopii zapasowej można zmodyfikować w celu zmiany zachowania usługi tworzenia kopii zapasowych.  

Informacje o stanie kopii zapasowej lokacji są zapisywane w pliku **Smsbkup.log** . Ten plik jest tworzony w folderze docelowym określonym we właściwościach zadania obsługi Utwórz kopię zapasową serwera lokacji.  

#### <a name="to-enable-the-site-backup-maintenance-task"></a>Aby włączyć zadanie obsługi dotyczące kopii zapasowej lokacji  

1.  W konsoli programu Configuration Manager, otwórz **administracji** > **konfiguracja lokacji** > **witryny**.  

2.  Wybierz lokację, w której chcesz włączyć zadanie obsługi dotyczące tworzenia kopii zapasowej.  

3.  Na **Home** karcie **ustawienia** grupy, wybierz **zadania konserwacji lokacji**.  

4.  Wybierz **tworzenie kopii zapasowej serwera lokacji**  >  **Edytuj**.  

5.  Wybierz **Włącz to zadanie** > **Ustaw ścieżki** określone miejsce docelowe kopii zapasowej. Do wyboru są następujące opcje:  

    > [!IMPORTANT]  
    >  Aby przeciwdziałać naruszeniu plików kopii zapasowych, przechowuj te pliki w bezpiecznej lokalizacji. Najlepiej zabezpieczoną ścieżką dla kopii zapasowej jest dysk lokalny, można ustawić uprawnienia systemu plików NTFS w folderze. Menedżer konfiguracji nie szyfruje danych kopii zapasowych składowanych w ścieżce kopii zapasowych.  

    -   **Dysk lokalny na serwerze lokacji dla danych lokacji i bazy danych**: Określa, że pliki kopii zapasowej lokacji i bazy danych lokacji są przechowywane w określonej ścieżce na dysku lokalnym serwera lokacji. Folder lokalny należy utworzyć przed uruchomieniem zadania tworzenia kopii zapasowej. Konto System lokalny na serwerze lokacji musi mieć uprawnienia systemu plików NTFS **Zapis** do folderu lokalnego przeznaczonego na kopie zapasowe serwera lokacji. Konto System lokalny na komputerze z uruchomionym programem SQL Server musi mieć uprawnienia systemu plików NTFS **Zapis** do folderu przeznaczonego na kopie zapasowe bazy danych lokacji.  

    -   **Ścieżka sieciowa (Nazwa UNC) dla danych lokacji i bazy danych**: Określa, że pliki kopii zapasowej lokacji i bazy danych lokacji są przechowywane w określonej ścieżce UNC. Udział ten należy utworzyć przed uruchomieniem zadania tworzenia kopii zapasowej. Konto komputera serwera lokacji i konto komputera programu SQL Server, jeśli program SQL Server jest zainstalowany na innym komputerze, muszą mieć uprawnienia NTFS i uprawnienia udziału **Zapis** do udostępnionego folderu sieciowego.  

    -   **Dyski lokalne na serwerze lokacji i serwerze SQL**: Określa, że pliki kopii zapasowej lokacji są przechowywane w określonej ścieżce na dysku lokalnym serwera lokacji, a pliki kopii zapasowej bazy danych lokacji są przechowywane w określonej ścieżce na dysku lokalnym serwera bazy danych lokacji. Foldery lokalne należy utworzyć przed uruchomieniem zadania tworzenia kopii zapasowej. Konto komputera serwera lokacji musi mieć uprawnienia systemu plików NTFS **Zapis** do folderu utworzonego na serwerze lokacji. Konto komputera serwera programu SQL Server musi mieć uprawnienia systemu plików NTFS **Zapis** do folderu utworzonego na serwerze bazy danych lokacji. Ta opcja jest dostępna tylko wtedy, gdy baza danych lokacji nie jest zainstalowana na serwerze lokacji.  

    > [!NOTE]  
    >   Opcja wyboru miejsca docelowego kopii zapasowych w trybie przeglądania jest dostępna tylko w przypadku określania miejsca docelowego kopii zapasowych za pomocą ścieżki UNC.

    > Nazwa folderu lub udziału używana jako miejsce docelowe kopii zapasowych nie obsługuje użycia znaków Unicode.  

6.  Skonfiguruj harmonogram dla zadania tworzenia kopii zapasowej lokacji. W ramach najlepszych praktyk weź pod uwagę taki harmonogram tworzenia kopii zapasowych, który obejmuje czas poza godzinami aktywnej pracy. W zarządzaniu hierarchią rozważ harmonogram uruchamiany co najmniej dwa razy w tygodniu, aby zapewnić maksymalne przechowywanie danych na wypadek awarii lokacji.  

    Po uruchomieniu konsoli programu Configuration Manager na tym samym serwerze lokacji, który jest konfigurowany pod kątem tworzenia kopii zapasowej, zadanie obsługi Utwórz kopię zapasową serwera lokacji posługuje się czasem lokalnym harmonogramu. Podczas uruchamiania konsoli programu Configuration Manager z komputera odległego od lokacji, która jest konfigurowana pod kątem tworzenia kopii zapasowej, zadanie obsługi Utwórz kopię zapasową serwera lokacji używa harmonogramu czasem UTC.  

7.  Określ, czy ma być tworzony alert, jeśli zadanie tworzenia kopii zapasowej lokacji nie powiedzie się, kliknij przycisk **OK**, a następnie kliknij przycisk **OK**. Po wybraniu programu Configuration Manager tworzy alert krytyczny dotyczący niepowodzenia tworzenia kopii zapasowej, który można przejrzeć w **alerty** w węźle **monitorowanie** obszaru roboczego.  

 Następnie sprawdź, czy zadanie obsługi Utwórz kopię zapasową serwera lokacji jest uruchomiona, aby upewnić się, że kopie zapasowe są tworzone.  

#### <a name="to-verify-that-the-backup-site-server-maintenance-task-is-running"></a>Aby sprawdzić, czy zadanie obsługi Utwórz kopię zapasową serwera lokacji jest uruchomiona  
Sprawdź, czy zadanie konserwacji kopii zapasowej lokacji jest uruchomiona, sprawdzając dowolny z następujących czynności:  

-   Sprawdź znacznik czasu plików w folderze docelowym kopii zapasowych utworzonym przez zadanie. Upewnij się, że znacznik czasu został zaktualizowany o czasie, który jest zgodny z godziną podczas ostatniego zaplanowanego zadania do uruchomienia.  

-   W węźle **Stan składnika** w obszarze roboczym **Monitorowanie** sprawdź komunikaty o stanie dla elementu SMS_SITE_BACKUP. Po pomyślnym ukończeniu tworzenia kopii zapasowej lokacji jest wyświetlany komunikat o identyfikatorze 5035, który wskazuje, że tworzenie kopii zapasowej lokacji zostało ukończone bez żadnych błędów.  

-   O ile zadanie obsługi Utwórz kopię zapasową serwera lokacji skonfigurowano do tworzenia alertu w wypadku niepowodzenia tworzenia kopii zapasowej, można sprawdzić węzeł **Alerty** w obszarze roboczym **Monitorowanie** pod kątem awarii procesu tworzenia kopii zapasowej.  

-   W &lt; *Folder_instalacji_programu_configuration_manager*> \Logs Przejrzyj plik dziennika smsbkup.log pod kątem ostrzeżeń i błędów. Po pomyślnym ukończeniu tworzenia kopii zapasowej lokacji pojawia się komunikat `Backup completed` opatrzony znacznikiem czasu i identyfikatorem komunikatu `STATMSG: ID=5035`.  

    > [!TIP]  
    >  Kiedy zadanie obsługi tworzenia kopii zapasowej nie powiedzie się, można uruchomić zadanie tworzenia kopii zapasowej ponownie, zatrzymując i uruchamiając ponownie usługę SMS_SITE_BACKUP.  

## <a name="archive-the-backup-snapshot"></a>Archiwizowanie migawki kopii zapasowej  
Przy pierwszym uruchomieniu zadanie obsługi Utwórz kopię zapasową serwera lokacji tworzy migawkę kopii zapasowej, której można użyć do odzyskania serwera lokacji w wypadku awarii. Kiedy zadanie tworzenia kopii zapasowej uruchamia się ponownie podczas kolejnych cykli, tworzy nową migawkę kopii zapasowej, która zastępuje poprzednią migawkę. W efekcie dla lokacji istnieje zawsze tylko jedna migawka kopii zapasowej i nie ma możliwości pobrania żadnej wcześniejszej migawki.  

Najlepszym rozwiązaniem jest przechowywanie wielu archiwów migawki kopii zapasowej z następujących przyczyn:  

-   Są często ulegają awarii, zagubieniu lub zawierają tylko częściową kopię zapasową nośniki kopii zapasowych. Odzyskanie autonomicznej lokacji głównej, która uległa awarii, ze starszej kopii zapasowej jest lepszym rozwiązaniem niż podjęcie próby odzyskania takiej lokacji bez jakiejkolwiek kopii zapasowej. Kopia zapasowa dla serwera lokacji w hierarchii musi obejmować okres przechowywania funkcji monitorowania zmian programu SQL Server. W przeciwnym razie kopia zapasowa nie jest wymagana.  

-   Uszkodzenie lokacji może nie zostać wykryte przez klika cykli kopii zapasowej. Użytkownik może być konieczne użycie migawki kopii zapasowej wykonanej zanim lokacja uległa uszkodzeniu. Dotyczy to autonomicznej lokacji głównej, a do lokacji w hierarchii, w przypadku tworzenia kopii zapasowej w programie SQL Server należy zmienić okres przechowywania funkcji monitorowania.  

-   Lokacja może nie mieć żadnej migawki kopii zapasowej, na przykład w razie awarii zadania obsługi Utwórz kopię zapasową serwera lokacji. Ponieważ przed wykonaniem kopii zapasowej bieżących danych zadanie tworzenia kopii zapasowej usuwa poprzednią migawkę kopii zapasowej, nie zostanie utworzona prawidłowa migawka kopii zapasowej.  

## <a name="using-the-afterbackupbat-file"></a>Korzystanie z pliku AfterBackup.bat  
Po pomyślnym wykonaniu kopii zapasowej lokacji zadanie Utwórz kopię zapasową serwera lokacji automatycznie podejmie próbę uruchomienia pliku o nazwie AfterBackup.bat. Należy ręcznie utworzyć plik AfterBackup.bat w &lt; *Folder_instalacji_programu_configuration_manager*> \Inboxes\Smsbkup. Jeśli plik AfterBackup.bat istnieje i znajduje się w prawidłowym folderze, automatycznie jest przeprowadzane po zakończeniu zadania tworzenia kopii zapasowej.

Plik AfterBackup.bat umożliwia archiwizowanie migawki kopii zapasowej po zakończeniu każdej operacji tworzenia kopii zapasowej i automatyczne wykonywanie innych zadań po wykonaniu kopii zapasowej, które nie są częścią zadania obsługi Utwórz kopię zapasową serwera lokacji. Plik AfterBackup.bat integruje archiwum i operacje tworzenia kopii zapasowej, zapewniając, że wszystkie nowe migawki kopii zapasowej zostaną zarchiwizowane.

Jeśli plik AfterBackup.bat nie istnieje, zadanie tworzenia kopii zapasowej pominie ten plik, co nie będzie miało wpływu na operację tworzenia kopii zapasowej. Aby sprawdzić, czy zadanie tworzenia kopii zapasowej lokacji pomyślnie uruchomiło plik AfterBackup.bat, w węźle **Stan składnika** w obszarze roboczym **Monitorowanie** należy sprawdzić komunikaty o stanie dla elementu SMS_SITE_BACKUP. Po pomyślnym uruchomieniu pliku polecenia AfterBackup.bat przez zadanie jest wyświetlany komunikat o identyfikatorze 5040.  

> [!TIP]  
>  Aby utworzyć plik AfterBackup.bat w celu zarchiwizowania plików kopii zapasowej serwera lokacji, należy użyć narzędzia poleceń kopiowania, jak [Robocopy](http://go.microsoft.com/fwlink/p/?LinkId=228408), w pliku wsadowym. Na przykład można utworzyć plik AfterBackup.bat i w pierwszym wierszu, można dodać wyglądać mniej więcej tak:`Robocopy E:\ConfigMgr_Backup \\ServerName\ShareName\ConfigMgr_Backup /MIR`  

 Zamierzonym użyciem pliku AfterBackup.bat jest archiwizowanie migawek kopii zapasowych. Plik AfterBackup.bat można jednak również utworzyć w celu wykonywania dodatkowych zadań po zakończeniu każdej operacji tworzenia kopii zapasowej.  

##  <a name="supplemental-backup-tasks"></a>Uzupełniające zadania tworzenia kopii zapasowych  
Zadanie obsługi Utwórz kopię zapasową serwera lokacji umożliwia wykonanie migawki kopii zapasowej plików serwera lokacji i bazy danych lokacji, nie tworzy jednak kopii zapasowej innych elementów, które należy uwzględnić przy opracowywaniu strategii tworzenia kopii zapasowych. Skorzystaj z następujących sekcji mogą ułatwić ukończenie strategii tworzenia kopii zapasowych programu Configuration Manager.  

### <a name="back-up-custom-reporting-services-reports"></a>Tworzenie kopii zapasowych niestandardowych raportów usług Reporting Services  
W przypadku zmodyfikowania wstępnie zdefiniowanych lub utworzenia niestandardowych raportów usług raportowania, tworzenie kopii zapasowej plików bazy danych serwera raportów stanowi ważną część strategii tworzenia kopii zapasowych. Kopia zapasowa serwera raportów musi zawierać kopię zapasową plików źródłowych raportów i modeli, klucze szyfrowania, niestandardowe zestawy lub rozszerzenia, pliki konfiguracji, niestandardowe widoki programu SQL Server używane w niestandardowych raportach, niestandardowe procedury składowane i tak dalej.  

> [!IMPORTANT]  
>  Podczas aktualizacji programu Configuration Manager do nowszej wersji, wstępnie zdefiniowane raporty mogą zostać zastąpione przez nowe raporty. Przypadku zmodyfikowania wstępnie zdefiniowanych raportów, wykonaj kopię zapasową raportu, a następnie przywróć ją w usługach Reporting Services.  

 Więcej informacji na temat tworzenia kopii zapasowych niestandardowych raportów w usługach Reporting Services znajduje się w temacie [Backup and Restore Operations for a Reporting Services Installation (Operacje tworzenia i przywracania kopii zapasowych dla instalacji usług Reporting Services)](https://technet.microsoft.com/library/ms155814\(v=sql.120\).aspx) w dokumentacji programu SQL Server 2014 — Books Online.  

### <a name="back-up-content-files"></a>Tworzenie kopii zapasowych plików zawartości  
Biblioteka zawartości w programie Configuration Manager jest lokalizacja, w której są przechowywane wszystkie pliki zawartości dla aktualizacji oprogramowania, aplikacje, wdrożenia systemu operacyjnego i tak dalej. Biblioteka zawartości znajduje się na serwerze lokacji i w każdym punkcie dystrybucji. Zadanie obsługi Utwórz kopię zapasową serwera lokacji nie obejmuje kopii zapasowej biblioteki zawartości lub plików źródłowych pakietu. W przypadku awarii serwera lokacji informacje o plikach biblioteki zawartości są odzyskiwane do bazy danych lokacji. Należy jednak w takiej sytuacji samodzielne przywrócić bibliotekę zawartości i pliki źródłowe pakietu na serwerze lokacji.  

-   **Biblioteka zawartości**: Biblioteka zawartości musi zostać przywrócona, aby można było ponownie dystrybuować zawartość do punktów dystrybucji. Po uruchomieniu ponownej dystrybucji zawartości programu Configuration Manager kopiuje pliki z biblioteki zawartości na serwerze lokacji do punktów dystrybucji. Biblioteka zawartości serwera lokacji znajduje się w folderze SCCMContentLib, który zazwyczaj znajduje się na dysku o największej ilości wolnego miejsca w czasie, gdy lokacji została zainstalowana.  

-   **Pliki źródłowe pakietu**: Pliki źródłowe pakietu muszą przywrócone, aby można było zaktualizować zawartość w punktach dystrybucji. Po uruchomieniu aktualizacji zawartości programu Configuration Manager kopiuje nowe lub zmodyfikowane pliki ze źródła pakietu do biblioteki zawartości, która w Włącz kopiuje pliki do dystrybucji skojarzone punkty. Aby znaleźć lokalizację źródłową wszystkich pakietów i aplikacji, można uruchomić następujące zapytanie w programie SQL Server: `SELECT * FROM v_Package`. Możesz określić lokację źródłową pakietu za pomocą trzech pierwszych znaków identyfikatora pakietu. Na przykład jeśli identyfikator pakietu to CEN00001, kod lokacji źródłowej to CEN. Przywróć pliki źródłowe pakietu, muszą być przywrócone do tej samej lokalizacji, w której znajdowały się przed awarią.  

 Należy sprawdzić, czy kopia zapasowa systemu plików serwera lokacji zawiera lokalizacje biblioteki zawartości i źródła pakietu.  

### <a name="back-up-custom-software-updates"></a>Tworzenie kopii zapasowych niestandardowych aktualizacji oprogramowania  
 Programu System Center Updates Publisher 2011 jest autonomicznym narzędziem, które umożliwia publikowanie niestandardowych aktualizacji oprogramowania do systemu Windows Server Update Services (WSUS), synchronizowanie aktualizacji oprogramowania programu Configuration Manager, ocenianie zgodności aktualizacji oprogramowania i wdrażanie niestandardowych aktualizacji oprogramowania na klientach. Aktualizacje Wydawca używa lokalnej bazy danych jako repozytorium aktualizacji oprogramowania. Korzystając z programu Updates Publisher w celu zarządzania niestandardowymi aktualizacjami oprogramowania, należy określić, czy można dołączyć bazy danych wydawcy aktualizacji planu tworzenia kopii zapasowej. Więcej informacje dotyczących programu Updates Publisher znajduje się w temacie [System Center Updates Publisher 2011](http://go.microsoft.com/fwlink/p/?LinkId=228726) w bibliotece TechCenter dla programu System Center.  

 Aby utworzyć kopię zapasową bazy danych programu Updates Publisher, należy użyć poniższej procedury.  

#### <a name="to-back-up-the-updates-publisher-2011-database"></a>Aby wykonać kopię zapasową bazy danych programu Updates Publisher 2011:  

1.  Na komputerze z uruchomionym programem Updates Publisher, przejdź do Updates Publisher pliku bazy danych (Scupdb.sdf) w %*USERPROFILE*%\AppData\Local\Microsoft\System Center Updates Publisher 2011\5.00.1727.0000\\. Istnieje inny plik bazy danych dla każdego użytkownika, z zainstalowanym programem Updates Publisher.  

2.  Skopiuj plik bazy danych do folderu docelowego kopii zapasowych. Na przykład jeśli folderem docelowym kopii zapasowych jest E:\ConfigMgr_Backup, plik bazy danych Updates Publisher można skopiować do E:\ConfigMgr_Backup\SCUP2011.  

    > [!TIP]  
    >  Jeśli istnieje więcej niż jeden plik bazy danych na komputerze, należy wziąć pod uwagę przechowywać plik w podfolderze określającym profil użytkownika, skojarzone z plikiem bazy danych. Na przykład, jeden plik bazy danych może się znajdować w folderze E:\ConfigMgr_Backup\SCUP2011\Użytkownik1, a inny w folderze E:\ConfigMgr_Backup\SCUP2011\Użytkownik2.  

## <a name="user-state-migration-data"></a>Dane migracji stanu użytkownika  
Aby przechwycić i przywrócić dane stanu użytkownika w środowiskach wdrożenia systemu operacyjnego, w którym ma zostać zachowany stan użytkownika bieżącego systemu operacyjnego, można użyć sekwencji zadań programu Configuration Manager. Foldery, w których są przechowywane dane stanu użytkownika, są wyświetlane we właściwościach punktu migracji stanu. W ramach zadania obsługi Utwórz kopię zapasową serwera lokacji nie jest wykonywana kopia zapasowa tych danych migracji stanu użytkownika. W ramach planu tworzenia kopii zapasowej należy ręcznie wykonać kopię zapasową folderów określonych do przechowywania danych migracji stanu użytkownika   

### <a name="to-determine-the-folders-used-to-store-user-state-migration-data"></a>Aby określić foldery używane do przechowywania danych migracji stanu użytkownika:  

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  W **administracji** obszaru roboczego, rozwiń węzeł **konfiguracja lokacji**i wybierz polecenie **serwery i role systemu lokacji**.  

3.  Wybierz system lokacji, na którym jest uruchomiona rola migracji stanu, a następnie wybierz pozycję **punkt migracji stanu** w **ról systemu lokacji**.  


4.  Na karcie **Rola lokacji** w grupie **Właściwości** kliknij polecenie **Właściwości**.  
5.  Foldery, w których są przechowywane dane migracji stanu użytkownika, są wyświetlane w sekcji **Szczegóły folderu** na karcie **Ogólne** .  



## <a name="about-the-sms-writer-service"></a>Usługa składnika zapisywania programu SMS — informacje  
Składnik zapisywania programu SMS to usługa, która w trakcie tworzenia kopii zapasowej wchodzi w interakcję z usługą kopiowania woluminów w tle (VSS). Składnika zapisywania programu SMS, który musi być uruchomiona usługa kopii lokacji programu Configuration Manager do pomyślnie ukończona.  

### <a name="purpose"></a>Cel  
Usługa składnika zapisywania programu SMS rejestruje się w usłudze VSS i wiąże z jej interfejsami i zdarzeniami. Kiedy usługa VSS rozgłasza zdarzenia lub jeśli wysyła określone powiadomienia do usługi składnika zapisywania programu SMS, ta ostatnia odpowiada na powiadomienie i podejmuje odpowiednie działanie. Składnika zapisywania programu SMS odczytuje plik sterowania kopii zapasowej (smsbkup.ctl) znajdujący się w &lt; *ścieżka instalacji programu ConfigMgr*> \inboxes\smsbkup.box i określa pliki oraz dane do wykonania kopii zapasowej. Na podstawie tych informacji, a także określonych danych z kluczy i podkluczy rejestru programu SMS, usługa składnika zapisywania programu SMS tworzy metadane, złożone z różnych składników. Metadane te przesyła następnie na żądanie usłudze VSS. VSS z kolei wysyła metadane do aplikacji żądającej Menedżer kopii zapasowej programu Configuration Manager. Menedżer kopii zapasowych wybiera dane przeznaczone do utworzenia kopii zapasowej i za pośrednictwem usługi VSS wysyła te dane do usługi składnika zapisywania programu SMS. Ta ostatnia podejmuje odpowiednie czynności przygotowawcze do tworzenia kopii zapasowej. Później kiedy Usługa VSS jest gotowa do sporządzenia migawki, wysyła odpowiednie zdarzenie, usługa składnika zapisywania programu SMS zatrzymuje wszystkie usługi programu Configuration Manager i zapewnia, że działania programu Configuration Manager są zablokowane na czas tworzenia migawki. Po ukończeniu tworzenia migawki usługa składnika zapisywania programu SMS uruchamia ponownie usługi i działania.  

Usługa składnika zapisywania programu SMS jest instalowana automatycznie. Musi ona być uruchomiona, kiedy aplikacja VSS żąda utworzenia lub przywrócenia kopii zapasowej.  

### <a name="writer-id"></a>Identyfikator modułu zapisującego  
Identyfikator modułu zapisującego dla składnika zapisywania programu SMS jest: 03ba67dd-dc6d-4729-a038-251f7018463b.  

### <a name="permissions"></a>Uprawnienia  
Usługa składnika zapisywania programu SMS musi być uruchomiona za pomocą konta System lokalny.  

### <a name="volume-shadow-copy-service"></a>Usługa kopiowania woluminów w tle  
Usługa VSS stanowi zestaw interfejsów API modelu COM z zaimplementowaną strukturą pozwalającą na tworzenie kopii zapasowych woluminów bez przerywania zapisu wykonywanego na tych woluminach przez aplikacje systemowe. Usługa VSS zapewnia spójny interfejs, umożliwiający koordynację między tymi aplikacjami użytkowników, które aktualizują dane na dysku (usługa składnika zapisywania programu SMS) i tymi, które wykonują kopie zapasowe aplikacji (usługa menedżera kopii zapasowych). Aby uzyskać więcej informacji, zobacz [usługi kopiowania woluminów w tle](http://go.microsoft.com/fwlink/p/?LinkId=241968) w witrynie Windows Server TechCenter.  

## <a name="next-steps"></a>Następne kroki
Po utworzeniu kopii zapasowej ćwiczenie [lokacji odzyskiwania](/sccm/protect/understand/recover-sites) z kopii zapasowej. Może to być przydatne zapoznanie się z procesu odzyskiwania, zanim zajdzie konieczność na niej się opierać i można potwierdzić przeznaczeniem kopii zapasowej zakończyła się pomyślnie.  
