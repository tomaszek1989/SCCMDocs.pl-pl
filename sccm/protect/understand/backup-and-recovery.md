---
title: Kopia zapasowa i odzyskiwanie | Dokumentacja firmy Microsoft
description: "Informacje dotyczące sposobu tworzenia kopii zapasowych i odzyskiwanie lokacji w przypadku awarii lub utraty danych w programie System Center Configuration Manager."
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f7832d83-9ae2-4530-8a77-790e0845e12f
caps.latest.revision: 22
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: ea6668ee7ee6b209b659426a0dc2c0be605ceaf1
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---

# <a name="backup-and-recovery"></a>Tworzenie kopii zapasowej i odzyskiwanie

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Przygotuj podejścia kopii zapasowych i odzyskiwania, aby uniknąć utraty danych. Lokacji programu Configuration Manager w sposób tworzenia kopii zapasowych i odzyskiwania można odzyskać Lokacje i hierarchie szybciej i przy minimalnej utracie danych. Sekcje w tym temacie można ułatwia tworzenie kopii zapasowej lokacji i odzyskiwaniu lokacji w przypadku awarii lub utraty danych.  



- [Tworzenie kopii zapasowej lokacji programu Configuration Manager](#BKMK_SiteBackup)   

  - [Zadanie obsługi dotyczące tworzenia kopii zapasowej](#BKMK_BackupMaintenanceTask)   

  - [Używanie programu Data Protection Manager do tworzenia kopii zapasowych bazy danych lokacji](#BKMK_DPMBackup)   

  -  [Archiwizowanie migawki kopii zapasowej](#BKMK_ArchivingBackupSnapshot)   

  -  [Korzystanie z pliku AfterBackup.bat](#BKMK_UsingAfterBackup)   

  -  [Uzupełniające zadania tworzenia kopii zapasowych](#BKMK_SupplementalBackup)   

-  [Odzyskiwanie lokacji programu Configuration Manager](#BKMK_RecoverSite)   

  -   [Ustalanie dostępnych opcji odzyskiwania](#BKMK_DetermineRecoveryOptions)   

         -   [Opcje odzyskiwania serwera lokacji](#BKMK_SiteServerRecoveryOptions)   

         -   [Opcje odzyskiwania bazy danych lokacji](#BKMK_SiteDatabaseRecoveryOption)   

         -   [Okres przechowywania funkcji śledzenia zmian programu SQL Server](#bkmk_SQLretention)   

         -   [Proces ponownego inicjowania danych lokacji lub danych globalnych](#bkmk_reinit)   

         -   [Scenariusze odzyskiwania bazy danych lokacji](#BKMK_SiteDBRecoveryScenarios)  

  -   [Klucze plików skryptu nienadzorowanego odzyskiwania lokacji](#BKMK_UnattendedSiteRecoveryKeys)  

  -   [Zadania po odzyskiwaniu](#BKMK_PostRecovery)  

  -   [Odzyskiwanie lokacji dodatkowej](#BKMK_RecoverSecondarySite)  

-   [Usługa składnika zapisywania programu SMS](#BKMK_SMSWriterService)  

> [!NOTE]  
>  Jeśli używasz grup dostępności AlwaysOn programu SQL Server do obsługi bazy danych lokacji, zmodyfikować planów i odzyskiwania kopii zapasowej zgodnie z opisem w [zmiany kopii zapasowych i odzyskiwania w przypadku używania grupy dostępności AlwaysOn programu SQL Server](../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md#bkmk_BnR) części [AlwaysOn programu SQL Server dla bazy danych lokacji wysokiej dostępności dla programu System Center Configuration Manager](../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md) tematu.  

##  <a name="BKMK_SiteBackup"></a> Tworzenie kopii zapasowej lokacji programu Configuration Manager  
 Program Configuration Manager ma obsługi tworzenia kopii zapasowej, który zadań:  

-   jest uruchamiane zgodnie z harmonogramem,  

-   tworzy kopię zapasową bazy danych lokacji,  

-   tworzy kopię zapasową określonych kluczy rejestru,  

-   tworzy kopię zapasową określonych folderów i plików,  

-   tworzy kopię zapasową folderu **CD.Latest** (zobacz [Folder CD.Latest programu System Center Configuration Manager](../../core/servers/manage/the-cd.latest-folder.md))  

 Zaplanuj uruchamianie domyślnego zadania kopii zapasowej lokacji nie rzadziej niż co 5 dni. Jest to spowodowane Configuration Manager używa [okresu przechowywania śledzenia zmian programu SQL Server](#bkmk_SQLretention) okresu 5 dni.  

 Aby uprościć proces tworzenia kopii zapasowej, należy utworzyć **AfterBackup.bat** plik w celu automatycznego wykonywania akcji po wykonaniu kopii zapasowej, po pomyślnym uruchomieniu zadania obsługi tworzenia kopii zapasowej. Plik AfterBackup.bat jest zwykle używane do archiwizowania migawki kopii zapasowej w bezpiecznej lokalizacji. Plik AfterBackup.bat służy także do kopiowania plików do folderu kopii zapasowej i uruchamiania innych, uzupełniające zadania tworzenia kopii zapasowych.

Następujące sekcje służą do utworzenia strategii tworzenia kopii zapasowych programu Configuration Manager.  

> [!NOTE]  
>  Program Configuration Manager można odzyskać bazy danych lokacji z zadania obsługi tworzenia kopii zapasowej programu Configuration Manager lub z kopii zapasowej bazy danych lokacji, utworzony za pomocą innego procesu. Na przykład możesz przywrócić bazy danych lokacji z kopii zapasowej utworzonej w ramach planu obsługi programu Microsoft SQL Server. Baza danych lokacji można przywrócić z kopii zapasowej, który jest tworzony za pomocą 2012 System Center Data Protection Manager (DPM). Więcej informacji znajduje się w temacie [Używanie programu Data Protection Manager do tworzenia kopii zapasowych bazy danych lokacji](#BKMK_DPMBackup).  

###  <a name="BKMK_BackupMaintenanceTask"></a> Zadanie obsługi dotyczące tworzenia kopii zapasowej  
 Kopia zapasowa lokacji programu Configuration Manager można zautomatyzować poprzez zaplanowanie wstępnie zdefiniowanego zadania obsługi Utwórz kopię zapasową serwera lokacji. Można utworzyć kopię zapasową centralnej lokacji administracyjnej i lokacji głównej, ale tworzenie kopii zapasowych lokacji dodatkowych lub serwerów systemu lokacji nie jest obsługiwane. Po uruchomieniu usługi tworzenia kopii zapasowej programu Configuration Manager wynika instrukcje zdefiniowane w pliku sterowania kopii zapasowej (**&lt;Folderinstalacjiprogramuconfigmgr\>\Inboxes\Smsbkup.box\Smsbkup.ctl**). Plik sterowania kopii zapasowej można zmodyfikować w celu zmiany zachowania usługi tworzenia kopii zapasowych. Informacje o stanie kopii zapasowej lokacji są zapisywane w pliku **Smsbkup.log** . Ten plik jest tworzony w folderze docelowym określonym we właściwościach zadania obsługi Utwórz kopię zapasową serwera lokacji.  


##### <a name="to-enable-the-site-backup-maintenance-task"></a>Aby włączyć zadanie obsługi dotyczące kopii zapasowej lokacji  

1.  W konsoli programu Configuration Manager, otwórz **Administracja** > **konfiguracji lokacji**  

     \> **Lokacje**.  

2.  Wybierz lokację, w której chcesz włączyć zadanie obsługi dotyczące tworzenia kopii zapasowej.  

3.  Na **Home** w karcie **ustawienia** grupy, wybierz **zadania obsługi lokacji**.  

4.  Wybierz **kopii zapasowej serwera lokacji**  >  **edytować**.  

5.  Wybierz **Włącz to zadanie** > **Ustaw ścieżki** do określenia miejsca docelowego kopii zapasowej. Do wyboru są następujące opcje:  

    > [!IMPORTANT]  
    >  Aby przeciwdziałać naruszeniu plików kopii zapasowych, przechowuj te pliki w bezpiecznej lokalizacji. Najlepiej zabezpieczoną ścieżką dla kopii zapasowych jest folder na dysku lokalnym, dla którego można ustawić uprawnienia systemu plików NTFS. Menedżer konfiguracji nie szyfruje danych kopii zapasowej znajduje się w ścieżce kopii zapasowych.  

    -   **Dysk lokalny na serwerze lokacji dla danych lokacji i bazy danych**: Określa, że pliki kopii zapasowych dla lokacji i bazy danych lokacji są składowane w określonej ścieżce na dysku lokalnym serwera lokacji. Folder lokalny należy utworzyć przed uruchomieniem zadania tworzenia kopii zapasowej. Konto System lokalny na serwerze lokacji musi mieć uprawnienia systemu plików NTFS **Zapis** do folderu lokalnego przeznaczonego na kopie zapasowe serwera lokacji. Konto System lokalny na komputerze z uruchomionym programem SQL Server musi mieć uprawnienia systemu plików NTFS **Zapis** do folderu przeznaczonego na kopie zapasowe bazy danych lokacji.  

    -   **Ścieżka sieciowa (Nazwa UNC) dla danych lokacji i bazy danych**: Określa, że pliki kopii zapasowych dla lokacji i bazy danych lokacji są składowane w określonej ścieżce UNC. Udział ten należy utworzyć przed uruchomieniem zadania tworzenia kopii zapasowej. Konto komputera serwera lokacji i konto komputera programu SQL Server, jeśli program SQL Server jest zainstalowany na innym komputerze, muszą mieć uprawnienia NTFS i uprawnienia udziału **Zapis** do udostępnionego folderu sieciowego.  

    -   **Dyski lokalne na serwerze lokacji i programu SQL Server**: Określa, że pliki kopii zapasowych dla lokacji są przechowywane w określonej ścieżce na dysku lokalnym serwera lokacji i pliki kopii zapasowej bazy danych lokacji są przechowywane w określonej ścieżce na dysku lokalnym serwera bazy danych lokacji. Foldery lokalne należy utworzyć przed uruchomieniem zadania tworzenia kopii zapasowej. Konto komputera serwera lokacji musi mieć uprawnienia systemu plików NTFS **Zapis** do folderu utworzonego na serwerze lokacji. Konto komputera serwera programu SQL Server musi mieć uprawnienia systemu plików NTFS **Zapis** do folderu utworzonego na serwerze bazy danych lokacji. Ta opcja jest dostępna tylko wtedy, gdy baza danych lokacji nie jest zainstalowana na serwerze lokacji.  

    > [!NOTE]  
    >    - Opcja wyboru miejsca docelowego kopii zapasowych w trybie przeglądania jest dostępna tylko w przypadku określania miejsca docelowego kopii zapasowych za pomocą ścieżki UNC.

    > - Nazwa folderu lub udziału używana jako miejsce docelowe kopii zapasowych nie obsługuje użycia znaków Unicode.  


6.  Skonfiguruj harmonogram dla zadania tworzenia kopii zapasowej lokacji. W ramach najlepszych praktyk weź pod uwagę taki harmonogram tworzenia kopii zapasowych, który obejmuje czas poza godzinami aktywnej pracy. W zarządzaniu hierarchią rozważ harmonogram uruchamiany co najmniej dwa razy w tygodniu, aby zapewnić maksymalne przechowywanie danych na wypadek awarii lokacji.  

    Po uruchomieniu konsoli programu Configuration Manager na tym samym serwerze lokacji, który jest konfigurowany pod kątem tworzenia kopii zapasowej, zadanie obsługi Utwórz kopię zapasową serwera lokacji używa czasu lokalnego harmonogramu. Po uruchomieniu konsoli programu Configuration Manager z komputera odległego od lokacji, w której są konfigurowane do tworzenia kopii zapasowych, zadanie obsługi Utwórz kopię zapasową serwera lokacji używa UTC harmonogramu.  

7.  Określ, czy ma być tworzony alert, jeśli zadanie tworzenia kopii zapasowej lokacji nie powiedzie się, kliknij przycisk **OK**, a następnie kliknij przycisk **OK**. Po wybraniu programu Configuration Manager tworzy alert krytyczny dotyczący niepowodzenia wykonywania kopii zapasowej, który można sprawdzić w **alerty** w węźle **monitorowanie** obszaru roboczego.  

 Następnie sprawdź, czy zadanie obsługi Utwórz kopię zapasową serwera lokacji jest uruchomiona, aby upewnić się, że kopie zapasowe są tworzone.  

##### <a name="to-verify-that-the-backup-site-server-maintenance-task-is-running"></a>Aby sprawdzić, czy zadanie obsługi Utwórz kopię zapasową serwera lokacji jest uruchomiona  

-   Sprawdź, czy zadanie obsługi tworzenia kopii zapasowej lokacji jest uruchomiona, sprawdzając dowolny z następujących czynności:  

    -   Sprawdź znacznik czasu plików w folderze docelowym kopii zapasowych utworzonym przez zadanie. Sprawdź, że znacznik czasu został zaktualizowany o czasie, który pasuje do raz podczas ostatniego zaplanowanego zadania do uruchomienia.  

    -   W węźle **Stan składnika** w obszarze roboczym **Monitorowanie** sprawdź komunikaty o stanie dla elementu SMS_SITE_BACKUP. Po pomyślnym ukończeniu tworzenia kopii zapasowej lokacji jest wyświetlany komunikat o identyfikatorze 5035, który wskazuje, że tworzenie kopii zapasowej lokacji zostało ukończone bez żadnych błędów.  

    -   O ile zadanie obsługi Utwórz kopię zapasową serwera lokacji skonfigurowano do tworzenia alertu w wypadku niepowodzenia tworzenia kopii zapasowej, można sprawdzić węzeł **Alerty** w obszarze roboczym **Monitorowanie** pod kątem awarii procesu tworzenia kopii zapasowej.  

    -   W &lt; *Folderinstalacjiprogramuconfigmgr*> \Logs Przejrzyj plik dziennika smsbkup.log pod kątem ostrzeżeń i błędów. Po pomyślnym ukończeniu tworzenia kopii zapasowej lokacji pojawia się komunikat `Backup completed` opatrzony znacznikiem czasu i identyfikatorem komunikatu `STATMSG: ID=5035`.  

    > [!TIP]  
    >  Kiedy zadanie obsługi tworzenia kopii zapasowej nie powiedzie się, można uruchomić zadanie tworzenia kopii zapasowej ponownie, zatrzymując i uruchamiając ponownie usługę SMS_SITE_BACKUP.  

###  <a name="BKMK_DPMBackup"></a> Używanie programu Data Protection Manager do tworzenia kopii zapasowych bazy danych lokacji  
 Program System Center 2012 Data Protection Manager (DPM) umożliwia tworzenie kopii zapasowych bazy danych lokacji. W programie DPM należy utworzyć nową grupę ochrony dla komputera bazy danych lokacji. Na stronie **Wybierz członków grupy** Kreatora tworzenia nowej grupy ochrony należy z listy źródeł danych wybrać Usługę składnika zapisywania programu SMS, a następnie jako właściwego członka grupy wybrać bazę danych lokacji. Więcej informacji o tworzeniu kopii zapasowej bazy danych lokacji za pomocą programu DPM znajduje się w [Data Protection Manager Documentation Library (Bibliotece dokumentacji programu Data Protection Manager)](http://go.microsoft.com/fwlink/?LinkId=272772) w witrynie TechNet.  

> [!IMPORTANT]  
>  Menedżer konfiguracji nie obsługuje kopii zapasowych programu DPM dla klastra programu SQL Server używającego wystąpienia nazwanego, ale obsługuje kopii zapasowych programu DPM na klastrze programu SQL Server, który używa domyślnego wystąpienia programu SQL Server.  

 Po przywróceniu bazy danych lokacji wykonaj w Instalatorze kroki zmierzające do odzyskania lokacji. Wybierz **Użyj ręcznie odzyskanej bazy danych lokacji** opcję odzyskiwania, aby użyć bazy danych lokacji, które można odzyskać za pomocą programu Data Protection Manager.  

###  <a name="BKMK_ArchivingBackupSnapshot"></a> Archiwizowanie migawki kopii zapasowej  
 Przy pierwszym uruchomieniu zadanie obsługi Utwórz kopię zapasową serwera lokacji tworzy migawkę kopii zapasowej, której można użyć do odzyskania serwera lokacji w wypadku awarii. Kiedy zadanie tworzenia kopii zapasowej uruchamia się ponownie podczas kolejnych cykli, tworzy nową migawkę kopii zapasowej, która zastępuje poprzednią migawkę. W efekcie dla lokacji istnieje zawsze tylko jedna migawka kopii zapasowej i nie ma możliwości pobrania żadnej wcześniejszej migawki.  

 Najlepszym rozwiązaniem jest przechowywanie wielu archiwów migawki kopii zapasowej z następujących przyczyn:  

-   Bardzo często nośnik kopii zapasowej do awarii, zagubieniu lub zawierają tylko częściową kopię zapasową. Odzyskanie autonomicznej lokacji głównej, która uległa awarii, ze starszej kopii zapasowej jest lepszym rozwiązaniem niż podjęcie próby odzyskania takiej lokacji bez jakiejkolwiek kopii zapasowej. Kopia zapasowa dla serwera lokacji w hierarchii musi obejmować okres przechowywania funkcji monitorowania zmian programu SQL Server. W przeciwnym razie kopia zapasowa nie jest wymagana.  

-   Uszkodzenie lokacji może nie zostać wykryte przez klika cykli kopii zapasowej. Użytkownik może być konieczne użycie kopii zapasowej migawki z przed stały się uszkodzony lokacji. Dotyczy autonomicznej lokacji głównej, a do lokacji w hierarchii, w której jest tworzenie kopii zapasowej w programie SQL Server śledzenia zmian okresu przechowywania.  

-   Lokacja może nie mieć żadnej migawki kopii zapasowej, na przykład w razie awarii zadania obsługi Utwórz kopię zapasową serwera lokacji. Ponieważ przed wykonaniem kopii zapasowej bieżących danych zadanie tworzenia kopii zapasowej usuwa poprzednią migawkę kopii zapasowej, nie zostanie utworzona prawidłowa migawka kopii zapasowej.  

###  <a name="BKMK_UsingAfterBackup"></a> Korzystanie z pliku AfterBackup.bat  
 Po pomyślnym wykonaniu kopii zapasowej lokacji zadanie Utwórz kopię zapasową serwera lokacji automatycznie podejmie próbę uruchomienia pliku o nazwie AfterBackup.bat. Należy ręcznie utworzyć plik AfterBackup.bat w &lt; *Folderinstalacjiprogramuconfigmgr*> \Inboxes\Smsbkup. Jeśli plik AfterBackup.bat istnieje i jest przechowywany w prawidłowym folderze, go automatycznie uruchomiony po zakończeniu zadania tworzenia kopii zapasowej. Plik AfterBackup.bat umożliwia archiwizowanie migawki kopii zapasowej po zakończeniu każdej operacji tworzenia kopii zapasowej i automatyczne wykonywanie innych zadań po wykonaniu kopii zapasowej, które nie są częścią zadania obsługi Utwórz kopię zapasową serwera lokacji. Plik AfterBackup.bat integruje archiwum i operacje tworzenia kopii zapasowej, zapewniając, że wszystkie nowe migawki kopii zapasowej zostaną zarchiwizowane. Jeśli plik AfterBackup.bat nie istnieje, zadanie tworzenia kopii zapasowej pominie ten plik, co nie będzie miało wpływu na operację tworzenia kopii zapasowej. Aby sprawdzić, czy zadanie tworzenia kopii zapasowej lokacji pomyślnie uruchomiło plik AfterBackup.bat, w węźle **Stan składnika** w obszarze roboczym **Monitorowanie** należy sprawdzić komunikaty o stanie dla elementu SMS_SITE_BACKUP. Po pomyślnym uruchomieniu pliku polecenia AfterBackup.bat przez zadanie jest wyświetlany komunikat o identyfikatorze 5040.  

> [!TIP]  
>  Aby utworzyć plik AfterBackup.bat w celu zarchiwizowania plików kopii zapasowej serwera lokacji, należy użyć narzędzia poleceń kopiowania, jak Robocopy, w pliku wsadowym. Można na przykład utworzyć plik AfterBackup.bat i w pierwszym wierszu dodać polecenie podobne do następującego: `Robocopy E:\ConfigMgr_Backup \\ServerName\ShareName\ConfigMgr_Backup /MIR`. Więcej informacji o narzędziu Robocopy znajduje się na stronie sieci Web z dokumentacją wiersza polecenia narzędzia [Robocopy](http://go.microsoft.com/fwlink/p/?LinkId=228408) .  

 Zamierzonym użyciem pliku AfterBackup.bat jest archiwizowanie migawek kopii zapasowych. Plik AfterBackup.bat można jednak również utworzyć w celu wykonywania dodatkowych zadań po zakończeniu każdej operacji tworzenia kopii zapasowej.  

###  <a name="BKMK_SupplementalBackup"></a> Uzupełniające zadania tworzenia kopii zapasowych  
 Zadanie obsługi Utwórz kopię zapasową serwera lokacji umożliwia wykonanie migawki kopii zapasowej plików serwera lokacji i bazy danych lokacji, nie tworzy jednak kopii zapasowej innych elementów, które należy uwzględnić przy opracowywaniu strategii tworzenia kopii zapasowych. Użyj poniższych sekcjach mogą ułatwić ukończenie strategii tworzenia kopii zapasowych programu Configuration Manager.  

#### <a name="back-up-custom-reporting-services-reports"></a>Tworzenie kopii zapasowych niestandardowych raportów usług Reporting Services  
 W przypadku zmodyfikowania wstępnie zdefiniowanych lub utworzenia niestandardowych raportów usług raportowania, tworzenie kopii zapasowej plików bazy danych serwera raportów stanowi ważną część strategii tworzenia kopii zapasowych. Kopia zapasowa serwera raportów musi zawierać kopię zapasową plików źródłowych raportów i modeli, klucze szyfrowania, niestandardowe zestawy lub rozszerzenia, pliki konfiguracji, niestandardowe widoki programu SQL Server używane w niestandardowych raportach, niestandardowe procedury składowane i tak dalej.  

> [!IMPORTANT]  
>  Podczas aktualizacji programu Configuration Manager do nowszej wersji, wstępnie zdefiniowanych raportów mogą zostać zastąpione przez nowe raporty. W przypadku zmodyfikowania wstępnie zdefiniowanych raportów, tworzenie kopii zapasowej raportu, a następnie przywróć ją w usługach Reporting Services.  

 Więcej informacji na temat tworzenia kopii zapasowych niestandardowych raportów w usługach Reporting Services znajduje się w temacie [Backup and Restore Operations for a Reporting Services Installation (Operacje tworzenia i przywracania kopii zapasowych dla instalacji usług Reporting Services)](https://technet.microsoft.com/library/ms155814\(v=sql.120\).aspx) w dokumentacji programu SQL Server 2014 — Books Online.  

#### <a name="backup-content-files"></a>Tworzenie kopii zapasowych plików zawartości  
 Biblioteki zawartości w programie Configuration Manager to miejsce, gdzie są przechowywane wszystkie pliki zawartości dla aktualizacji oprogramowania, aplikacje, wdrożenia systemu operacyjnego i tak dalej. Biblioteka zawartości znajduje się na serwerze lokacji oraz w każdym punkcie dystrybucji. Zadanie obsługi Utwórz kopię zapasową serwera lokacji nie obejmuje kopii zapasowej biblioteki zawartości lub plików źródłowych pakietu. W przypadku awarii serwera lokacji informacje o plikach biblioteki zawartości są odzyskiwane do bazy danych lokacji. Należy jednak w takiej sytuacji samodzielne przywrócić bibliotekę zawartości i pliki źródłowe pakietu na serwerze lokacji.  

-   **Biblioteka zawartości**: Przed ponowną dystrybucją zawartości do punktów dystrybucji, jest przywrócenie biblioteki zawartości. Po uruchomieniu ponownej dystrybucji zawartości programu Configuration Manager kopiuje pliki z biblioteki zawartości na serwerze lokacji do punktów dystrybucji. Biblioteka zawartości serwera lokacji znajduje się w folderze SCCMContentLib, który zazwyczaj znajduje się na dysku o największej ilości wolnego miejsca w czasie, gdy do instalacji lokacji.  

-   **Pliki źródłowe pakietu**: Musi być przywrócenie plików źródłowych pakietu, przed zaktualizowaniem zawartości w punktach dystrybucji. Po uruchomieniu aktualizacji zawartości programu Configuration Manager kopiuje nowe lub zmodyfikowane pliki ze źródła pakietu do biblioteki zawartości, której Włącz kopiuje pliki do dystrybucji skojarzone punkty. Aby znaleźć lokalizację źródłową wszystkich pakietów i aplikacji, można uruchomić następujące zapytanie w programie SQL Server: `SELECT * FROM v_Package`. Możesz określić lokację źródłową pakietu za pomocą trzech pierwszych znaków identyfikatora pakietu. Na przykład jeśli identyfikator pakietu to CEN00001, kod lokacji źródłowej to CEN. Podczas przywracania plików źródłowych pakietu muszą być przywrócone do tej samej lokalizacji, w której znajdowały się przed awarią.  

 Należy sprawdzić, czy kopia zapasowa systemu plików serwera lokacji zawiera lokalizacje biblioteki zawartości i źródła pakietu.  

#### <a name="back-up-custom-software-updates"></a>Tworzenie kopii zapasowych niestandardowych aktualizacji oprogramowania  
 System Center Updates Publisher 2011 jest autonomicznym narzędziem umożliwia publikowanie niestandardowych aktualizacji oprogramowania do systemu Windows Server Update Services (WSUS), synchronizowanie aktualizacji oprogramowania programu Configuration Manager, oceny zgodności aktualizacji oprogramowania i wdrażanie niestandardowych aktualizacji oprogramowania do klientów. Updates Publisher korzysta z lokalnej bazy danych jako repozytorium aktualizacji oprogramowania. Podczas Updates Publisher umożliwiają zarządzania niestandardowymi aktualizacjami oprogramowania, należy ustalić, czy należy dołączyć bazy danych wydawcy aktualizacji planu tworzenia kopii zapasowej. Więcej informacje dotyczących programu Updates Publisher znajduje się w temacie [System Center Updates Publisher 2011](http://go.microsoft.com/fwlink/p/?LinkId=228726) w bibliotece TechCenter dla programu System Center.  

 Użyj poniższej procedury do utworzenia kopii zapasowej bazy danych programu Updates Publisher.  

###### <a name="to-back-up-the-updates-publisher-2011-database"></a>Aby wykonać kopię zapasową bazy danych programu Updates Publisher 2011:  

1.  Na komputerze, na którym działa Updates Publisher, przejdź do pliku bazy danych wydawcy aktualizacji (Scupdb.sdf) w lokalizacji %*USERPROFILE*%\AppData\Local\Microsoft\System Center Updates Publisher 2011\5.00.1727.0000\\. Istnieje inny plik bazy danych dla każdego użytkownika, z zainstalowanym programem Updates Publisher.  

2.  Skopiuj plik bazy danych do folderu docelowego kopii zapasowych. Na przykład jeśli miejsce docelowe kopii zapasowej jest E:\ConfigMgr_Backup, można skopiować pliku bazy danych programu Updates Publisher do E:\ConfigMgr_Backup\SCUP2011.  

    > [!TIP]  
    >  Jeśli istnieje więcej niż jeden plik bazy danych na komputerze, należy wziąć pod uwagę przechowywać plik w podfolderze określającym profil użytkownika, skojarzone z plikiem bazy danych. Na przykład, jeden plik bazy danych może się znajdować w folderze E:\ConfigMgr_Backup\SCUP2011\Użytkownik1, a inny w folderze E:\ConfigMgr_Backup\SCUP2011\Użytkownik2.  

### <a name="user-state-migration-data"></a>Dane migracji stanu użytkownika  
 Użyj sekwencji zadań programu Configuration Manager przechwycić i przywrócić dane stanu użytkownika w scenariuszach wdrażania systemu operacyjnego którym chcesz przechowywać stan użytkownika bieżącego systemu operacyjnego. Foldery, w których są przechowywane dane stanu użytkownika, są wyświetlane we właściwościach punktu migracji stanu. W ramach zadania obsługi Utwórz kopię zapasową serwera lokacji nie jest wykonywana kopia zapasowa tych danych migracji stanu użytkownika. W ramach planu tworzenia kopii zapasowej należy ręcznie wykonać kopię zapasową folderów określonych do przechowywania danych migracji stanu użytkownika   

#### <a name="to-determine-the-folders-used-to-store-user-state-migration-data"></a>Aby określić foldery używane do przechowywania danych migracji stanu użytkownika:  

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  W **Administracja** obszaru roboczego, rozwiń węzeł **konfiguracja lokacji**i wybierz polecenie **serwery i role systemu lokacji**.  

3.  Wybierz system lokacji, na którym jest uruchomiona rola migracji stanu, a następnie wybierz **punkt migracji stanu** w **ról systemu lokacji**.  


4.  Na karcie **Rola lokacji** w grupie **Właściwości** kliknij polecenie **Właściwości**.  
5.  Foldery, w których są przechowywane dane migracji stanu użytkownika, są wyświetlane w sekcji **Szczegóły folderu** na karcie **Ogólne**.  

## <a name="recover-a-configuration-manager-site"></a>Odzyskiwanie lokacji programu Configuration Manager
 Odzyskiwanie lokacji programu Configuration Manager jest wymagany przy każdym awarii lokacji programu Configuration Manager lub utraty danych w bazie danych lokacji. Do podstawowych zadań funkcji odzyskiwania lokacji należy naprawianie i ponowne synchronizowanie danych, aby zapobiegać przerwom w wykonywaniu operacji.  

> [!IMPORTANT]  
>  W przypadku odzyskiwania bazy danych lokacji:  

>  -   Musisz użyć takiej samej wersji i wydania programu SQL Server. Na przykład przywracanie bazy danych, który uruchomił programu SQL Server 2012 do programu SQL Server 2014 nie jest obsługiwane. Podobnie Przywracanie bazy danych lokacji, który został uruchomiony w wersji Standard programu SQL Server 2014 do wersji Enterprise programu SQL Server 2014 nie jest obsługiwane.  
> -   Program SQL Server nie może działać w **trybie jednego użytkownika**.  
> -   Upewnij się, że pliki MDF i LDF są prawidłowe. W przypadku odzyskiwania lokacji nie ma możliwości sprawdzenia stanu przywracanych plików.  


 Odzyskiwanie lokacji można rozpocząć, uruchamiając Kreatora instalacji programu Configuration Manager z dysku CD. Najnowszy folder.  Można również skonfigurować w skrypcie instalacji nienadzorowanej, a następnie użyć polecenia Instalatora **/script** opcję, aby uruchomić Instalatora z tego samego dysku CD. Najnowszy folder. Opcje odzyskiwania są różne w zależności od tego, czy użytkownik dysponuje kopią zapasową bazy danych lokacji programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [The CD.Latest folder for System Center Configuration Manager](../../core/servers/manage/the-cd.latest-folder.md) (Folder CD.Latest dla programu System Center Configuration Manager).  

> [!IMPORTANT]  
>  Po uruchomieniu Instalatora programu Configuration Manager z **Start** menu na serwerze lokacji **odzyskiwanie lokacji** opcja jest niedostępna.  

>  Jeśli zainstalowano żadnych aktualizacji z poziomu konsoli programu Configuration Manager przed wykonaniem kopii zapasowej, można pomyślnie ponownie lokacji za pomocą Instalatora z nośnika instalacyjnego lub ścieżka instalacji programu Configuration Manager.  

> [!NOTE]  
>  Po przywróceniu baz danych lokacji skonfigurowanych pod kątem replik baz danych przed użyciem tych replik należy ponownie skonfigurować każdą replikę baz danych, tworząc jeszcze raz zarówno publikacje, jak i subskrypcje.  

###  <a name="BKMK_DetermineRecoveryOptions"></a> Ustalanie dostępnych opcji odzyskiwania  
 Istnieją dwa główne obszary, które należy wziąć pod uwagę dla serwera lokacji głównej programu Configuration Manager i odzyskiwanie centralnej lokacji administracyjnej; serwer lokacji i bazy danych lokacji. Poniższe sekcje zawierają informacje pomocne w określeniu opcji wyboru scenariusza odzyskiwania.  

> [!NOTE]  

####  <a name="BKMK_SiteServerRecoveryOptions"></a> Opcje odzyskiwania serwera lokacji  
 Należy uruchomić Instalatora z kopię dysku CD. Najnowsze utworzony folder poza folder instalacji programu Configuration Manager. Następnie wybierz opcję **Odzyskaj lokację** . Po uruchomieniu Instalatora będą dostępne następujące opcje odzyskiwania serwera lokacji, który uległ awarii:  

-   **Odzyskaj serwer lokacji przy użyciu istniejącej kopii zapasowej**: Użyj tej opcji, jeśli użytkownik dysponuje kopią zapasową serwera lokacji programu Configuration Manager, który został utworzony na serwerze lokacji w ramach **kopię zapasową serwera lokacji** zadań konserwacji przed awarią lokacji. Lokacja zostanie zainstalowana ponownie, a ustawienia lokacji zostaną skonfigurowane na podstawie lokacji, której kopię zapasową utworzono.  

-   **Ponowna instalacja serwera lokacji**: Użyj tej opcji, jeśli nie masz kopii zapasowej na serwerze lokacji. Serwer lokacji zostanie zainstalowany ponownie, a użytkownik będzie musiał określić ustawienia lokacji w taki sam sposób jak podczas instalacji początkowej. Aby pomyślnie odzyskać lokację, należy użyć tego samego kodu lokacji i nazwy bazy danych lokacji jak podczas pierwszej instalacji lokacji, która uległa awarii.  

> [!NOTE]  
>  Jeśli Instalator wykryje istniejącą lokację programu Configuration Manager na serwerze, można rozpocząć odzyskiwanie lokacji, ale są ograniczone opcje odzyskiwania na serwerze lokacji. Na przykład, jeśli Instalator zostanie uruchomiony na istniejącym serwerze lokacji, po wybraniu opcji odzyskiwania będzie można odzyskać serwer bazy danych lokacji, opcja odzyskiwania serwera lokacji będzie jednak wyłączona.  

####  <a name="BKMK_SiteDatabaseRecoveryOption"></a> Opcje odzyskiwania bazy danych lokacji  
 Po uruchomieniu Instalatora będą dostępne następujące opcje odzyskiwania bazy danych lokacji:  

-   **Odzyskiwanie bazy danych lokacji przy użyciu zestawu kopii zapasowych**: Użyj tej opcji, jeśli użytkownik dysponuje kopią zapasową bazy danych lokacji programu Configuration Manager, który został utworzony w ramach **kopię zapasową serwera lokacji** zadania obsługi na lokację przed awarią bazy danych lokacji. Jeśli użytkownik ma hierarchię, zmiany dokonane w bazie danych lokacji po utworzeniu ostatniej kopii zapasowej bazy danych lokacji zostaną pobrane z centralnej lokacji administracyjnej dla lokacji głównej lub z lokacji głównej odniesienia dla centralnej lokacji administracyjnej. Po odzyskaniu bazy danych lokacji autonomicznej lokacji głównej zmiany lokacji po utworzeniu ostatniej kopii zapasowej zostaną utracone.  

     W przypadku odzyskiwania bazy danych lokacji w hierarchii proces odzyskiwania jest różny dla centralnej lokacji administracyjnej i lokacji głównej oraz zależy również od tego, czy ostatnia kopia zapasowa została utworzona w okresie przechowywania funkcji monitorowania zmian programu SQL Server, czy poza tym okresem. Więcej informacji znajduje się w sekcji [Scenariusze odzyskiwania bazy danych lokacji](#BKMK_SiteDBRecoveryScenarios) w tym temacie.  

    > [!NOTE]  
    >  Odzyskiwanie nie powiedzie się, jeśli użytkownik wybierze opcję przywracania bazy danych lokacji przy użyciu zestawu kopii zapasowych, a baza danych lokacji już istnieje.  

-   **Utwórz nową bazę danych dla tej witryny**: Użyj tej opcji, jeśli nie masz kopii zapasowej bazy danych lokacji programu Configuration Manager. Jeśli użytkownik ma hierarchię, zostanie utworzona nowa baza danych, a dane zostaną odzyskane przy użyciu zreplikowanych danych z centralnej lokacji administracyjnej dla lokacji głównej lub z lokacji głównej odniesienia dla centralnej lokacji administracyjnej. Ta opcja jest niedostępna, jeśli użytkownik odzyskuje autonomiczną lokację główną lub centralną lokację administracyjną nie mającą lokacji głównych.  

-   **Użyj bazy danych lokacji, która została ręcznie odzyskana**: Tej opcji należy użyć, gdy odzyskał już bazę danych lokacji programu Configuration Manager, ale musi zakończyć proces odzyskiwania. Program Configuration Manager można odzyskać bazy danych lokacji z zadania obsługi tworzenia kopii zapasowej programu Configuration Manager lub z kopii zapasowej bazy danych lokacji utworzonej przy użyciu programu DPM lub inny proces. Po przywróceniu bazy danych lokacji przy użyciu metody poza programem Configuration Manager należy uruchomić Instalatora i wybrać tę opcję, aby ukończyć odzyskiwanie bazy danych lokacji. Jeśli użytkownik ma hierarchię, zmiany dokonane w bazie danych lokacji po utworzeniu ostatniej kopii zapasowej bazy danych lokacji zostaną pobrane z centralnej lokacji administracyjnej dla lokacji głównej lub z lokacji głównej odniesienia dla centralnej lokacji administracyjnej. Po odzyskaniu bazy danych lokacji autonomicznej lokacji głównej zmiany lokacji po utworzeniu ostatniej kopii zapasowej zostaną utracone.  

    > [!NOTE]  
    >  Po wykonać kopię zapasową bazy danych lokacji przy użyciu programu DPM, należy skorzystać z procedur programu DPM, aby przywrócić bazę danych lokacji w określonej lokalizacji przed kontynuowaniem procesu przywracania w programie Configuration Manager. Więcej informacji na temat programu DPM zawiera [Data Protection Manager Documentation Library (Biblioteka dokumentacji programu Data Protection Manager)](http://go.microsoft.com/fwlink/?LinkId=272772) w witrynie TechNet.  

-   **Pominięcie odzyskiwania bazy danych**: Tej opcji należy użyć, gdy doszło do utraty nie danych na serwerze bazy danych lokacji programu Configuration Manager. Ta opcja jest prawidłowa tylko wtedy, gdy baza danych lokacji znajduje się na innym komputerze niż odzyskiwany serwer lokacji.  

####  <a name="bkmk_SQLretention"></a> Okres przechowywania funkcji śledzenia zmian programu SQL Server  
 Funkcja monitorowania zmian jest włączona dla bazy danych lokacji w programie SQL Server. Menedżer konfiguracji umożliwia śledzenie zmian kwerendy informacji o zmianach dokonanych w tabelach bazy danych po poprzednim punkcie w czasie. Okres przechowywania określa, jak długo są przechowywane informacje o monitorowaniu zmian. Domyślny okres przechowywania dla bazy danych lokacji wynosi 5 dni. Przebieg procesu odzyskiwania bazy danych lokacji zależy od tego, czy kopia zapasowa została utworzona w okresie przechowywania danych czy poza tym okresem. Na przykład, jeśli serwer bazy danych lokacji ulegnie awarii, a ostatnia kopia zapasowa została wykonana 7 dni temu, kopia zapasowa została utworzona poza okresem przechowywania.

 Aby uzyskać więcej informacji na temat wewnętrzne śledzenia zmian programu SQL Server zobacz następujące blogów zespołu programu SQL Server: [Oczyszczanie — część 1 śledzenia zmian](https://blogs.msdn.microsoft.com/sql_server_team/change-tracking-cleanup-part-1) i [oczyszczania śledzenia zmian — część 2](https://blogs.msdn.microsoft.com/sql_server_team/change-tracking-cleanup-part-2).



####  <a name="bkmk_reinit"></a> Proces ponownego inicjowania danych lokacji lub danych globalnych  
 Proces ponownego inicjowania danych lokacji lub danych globalnych zastępuje istniejące dane w bazie danych lokacji danymi z innej bazy danych lokacji. Na przykład, gdy lokacja ABC ponownie zainicjuje dane z lokacji XYZ, zostaną wykonane następujące kroki:  

-   Dane zostaną skopiowane z lokacji XYZ do lokacji ABC.  

-   Istniejące dane dla lokacji XYZ zostaną usunięte z bazy danych lokacji w lokacji ABC.  

-   Dane skopiowane z lokacji XYZ zostaną wstawione do bazy danych lokacji w lokacji ABC.  

##### <a name="example-scenario-1"></a>Przykładowy scenariusz 1  
 **Lokacja główna ponownie inicjuje dane globalne z centralnej lokacji administracyjnej**: Proces odzyskiwania usuwa istniejące dane globalne lokacji głównej w bazie danych lokacji głównej i zastępuje je danymi danych globalnych skopiowane z witryny administracji centralnej.  

##### <a name="example-scenario-2"></a>Przykładowy scenariusz 2  
 **Centralna lokacja administracyjna ponownie inicjuje dane lokacji z lokacji głównej**: Proces odzyskiwania usuwa istniejące dane lokacji tej lokacji głównej w bazie danych witryny administracji centralnej i zastępuje je danymi z danymi lokacji skopiowanymi z lokacji głównej. Proces nie wpływa na dane lokacji innych lokacji głównych.  

####  <a name="BKMK_SiteDBRecoveryScenarios"></a> Scenariusze odzyskiwania bazy danych lokacji  
 Po przywróceniu bazy danych lokacji z kopii zapasowej programu Configuration Manager podejmie próbę przywrócenia zmian w lokacji oraz danych globalnych po utworzeniu ostatniej kopii zapasowej bazy danych. Poniżej wymieniono akcje tego programu Configuration Manager rozpoczyna się po przywróceniu bazy danych lokacji z kopii zapasowej.  

 **Odzyskana lokacja jest centralną lokacją administracyjną:**  

-   **Kopia zapasowa bazy danych w okresie przechowywania funkcji monitorowania zmian**  

    -   **Dane globalne:** Zmiany danych globalnych po wykonaniu kopii zapasowej są replikowane ze wszystkich lokacji głównych.  

    -   **Dane lokacji:** Zmiany danych lokacji po wykonaniu kopii zapasowej są replikowane ze wszystkich lokacji głównych.  

-   **Kopia zapasowa bazy danych poza okresem przechowywania funkcji monitorowania zmian**  

    -   **Dane globalne:** Centralna lokacja administracyjna ponownie inicjuje dane globalne z lokacji głównej odniesienia, w przypadku określenia. Następnie wszystkie inne lokacje główne ponownie inicjują dane globalne z centralnej lokacji administracyjnej. Jeśli nie określono lokacji odniesienia, wszystkie lokacje główne ponownie inicjują dane globalne (przywrócone z kopii zapasowej) z centralnej lokacji administracyjnej.  

    -   **Dane lokacji:** Witryna Administracja centralna ponownie inicjuje dane lokacji z każdej lokacji głównej.  

 **Odzyskana lokacja to lokacja główna:**  

-   **Kopia zapasowa bazy danych w okresie przechowywania funkcji monitorowania zmian**  

    -   **Dane globalne:** Zmiany danych globalnych po wykonaniu kopii zapasowej są replikowane z centralnej lokacji administracyjnej.  

    -   **Dane lokacji:** Centralna lokacja administracyjna ponownie inicjuje dane lokacji z lokacji podstawowej. Zmiany dokonane po wykonaniu kopii zapasowej zostaną utracone, większość danych zostanie jednak wygenerowana ponownie przez klientów wysyłających informacje do lokacji głównej.  

-   **Kopia zapasowa bazy danych poza okresem przechowywania funkcji monitorowania zmian**  

    -   **Dane globalne:** Lokacja główna ponownie inicjuje dane globalne z centralnej lokacji administracyjnej.  

    -   **Dane lokacji:** Centralna lokacja administracyjna ponownie inicjuje dane lokacji z lokacji podstawowej. Zmiany dokonane po wykonaniu kopii zapasowej zostaną utracone, większość danych zostanie jednak wygenerowana ponownie przez klientów wysyłających informacje do lokacji głównej.  

### <a name="site-recovery-procedures"></a>Procedury odzyskiwania lokacji  
 Aby odzyskać serwer lokacji i bazę danych lokacji, należy użyć jednej z poniższych procedur.  

##### <a name="to-start-a-site-recovery-in-the-setup-wizard"></a>Aby rozpocząć odzyskiwanie lokacji w Kreatorze instalacji:  

1.  Kopiowanie dysku CD. Najnowszy folder do lokalizacji poza folder instalacji programu Configuration Manager. (Zobacz [Folder CD.Latest programu System Center Configuration Manager](../../core/servers/manage/the-cd.latest-folder.md))  

     Z kopii dysku CD. Najnowszy folder, uruchom Kreatora instalacji programu Configuration Manager.  

2.  Na stronie **Wprowadzenie** wybierz opcję **Odzyskaj lokację**, a następnie kliknij przycisk **Dalej**.  

3.  Ukończ kreatora, używając opcji odpowiednich dla danego odzyskiwania lokacji.  

    > [!IMPORTANT]  
    >  W trakcie odzyskiwania Instalator określi port usługi SQL Server Service Broker (SSB) używany przez program SQL Server. Nie należy zmieniać tego ustawienia portu podczas odzyskiwania, w przeciwnym razie po jego ukończeniu replikacja danych nie będzie działać prawidłowo.  

    > [!NOTE]  
    >  Można określić oryginalne lub nową ścieżkę, aby użyć podczas instalacji programu Configuration Manager w Kreatorze instalacji.  

##### <a name="to-start-an-unattended-site-recovery"></a>Aby rozpocząć nienadzorowane odzyskiwanie lokacji:  

1.  Przygotuj skrypt instalacji nienadzorowanej pod kątem opcji wymaganych do odzyskania lokacji.  

2.  Uruchom Instalatora programu Configuration Manager za pomocą polecenia **/script** opcji. Na przykład jeśli plik inicjowania Instalatora ConfigMgrUnattend.ini i jest zapisany w katalogu C:\Temp komputera, na którym jest uruchomiony Instalator, polecenie będzie następujący: **Instalatora/Script C:\temp\ConfigMgrUnattend.ini**.  

> [!NOTE]  
>  Po odzyskaniu centralnej lokacji administracyjnej replikacja niektórych danych lokacji z lokacji podrzędnych może się nie powieść. Może to obejmować spis sprzętu, spis oprogramowania i komunikaty o stanie.  
>   
>  W takiej sytuacji należy ponownie zainicjować element **ConfigMgrDRSSiteQueue** w celu uruchomienia replikacji bazy danych.  Aby to zrobić, użyj **programu SQL Server Manager** uruchomić następujące kwerendy w Menedżerze konfiguracji bazy danych lokacji w witrynie Administracja centralna:  
>   
>  **IF EXISTS (SELECT \* FROM sys.service_queues WHERE name = 'ConfigMgrDRSSiteQueue' AND is_receive_enabled = 0)**  
>   
>  **ALTER QUEUE [dbo].[ConfigMgrDRSSiteQueue] WITH STATUS = ON**  

###  <a name="BKMK_UnattendedSiteRecoveryKeys"></a> Klucze plików skryptu nienadzorowanego odzyskiwania lokacji  
 Aby przeprowadzić nienadzorowane odzyskiwanie lokacji administracji centralnej programu Configuration Manager lub lokacji głównej, można utworzyć skrypt instalacji nienadzorowanej i użyć opcji polecenia/Script. Skrypt zawiera ten sam typ informacji, o które monituje Kreator instalacji, różnica polega tylko na braku ustawień domyślnych. Należy określić wszystkie wartości kluczy instalacji mających zastosowanie do używanego typu odzyskiwania.  

 Można uruchomić nienadzorowaną instalację programu Configuration Manager za pomocą pliku inicjującego z opcją wiersza polecenia Instalatora/Script. Instalacja nienadzorowana jest obsługiwana przy odzyskiwaniu witryny administracji centralnej programu Configuration Manager i lokacji głównej. Aby użyć opcji wiersza polecenia Instalatora /script, należy utworzyć plik inicjujący oraz podać jego nazwę po opcji wiersza polecenia Instalatora /script. Nazwa pliku jest bez znaczenia, musi mieć jedynie rozszerzenie .ini. Podając odniesienie do pliku inicjowania Instalatora w wierszu polecenia, należy wprowadzić pełną ścieżkę do pliku. Na przykład, jeśli plik inicjowania Instalatora ma nazwę setup.ini i znajduje się w folderze C:\setup, należy wpisać następujący tekst w wierszu polecenia:  

 **setup /script c:\setup\setup.ini**.  

> [!IMPORTANT]  
>  Uruchomienie Instalatora wymaga praw administratora. Uruchamiając Instalatora ze skryptem instalacji nienadzorowanej, należy uruchomić wiersz polecenia z uprawnieniami administratora przy użyciu polecenia **Uruchom jako administrator**.  

 Skrypt zawiera nazwy sekcji i kluczy oraz wartości. Wymagane nazwy kluczy sekcji różnią się w zależności od typu odzyskiwania, którego skrypt jest wykonywany. Kolejność kluczy w sekcjach oraz kolejność sekcji w pliku nie mają znaczenia. W kluczach nie jest uwzględniana wielkość liter. Podając wartości kluczy, należy pamiętać, że po nazwie klucza należy wprowadzić znak równości (=), a następnie jego wartość.  

 Poniższe sekcje zawierają informacje pomocne w tworzeniu skryptu nienadzorowanego odzyskiwania lokacji. Tabele zawierają listę dostępnych kluczy skryptu instalacji, ich wartości, informację, czy dany klucz jest wymagany, typ instalacji, do której klucz skryptu jest używany, oraz krótki opis klucza.  

#### <a name="recover-a-central-administration-site-unattended"></a>Odzyskiwanie nienadzorowane centralnej lokacji administracyjnej  
 Skorzystaj z poniższych informacji, aby skonfigurować plik skryptu instalacji nienadzorowanej odzyskać witryny administracji centralnej.  

 **Identyfikacja**  

-   **Nazwa klucza:** Akcja  

    -   **Wymagane:** Tak  

    -   **Wartości:** RecoverCCAR  

    -   **Szczegóły:** Odzyskuje centralną lokację administracyjną  

-   **Nazwa klucza:** CDLatest  

    -   **Wymagane:** Tak — tylko w przypadku używania nośnika z dysku CD. Najnowszy folder.    

    -   **Wartości:** 1 wartości innej niż 1 jest uważany za nie można przy użyciu dysku CD. Najnowsze.

    -   **Szczegóły:** Skrypt musi zawierać ten klucz i wartość po uruchomieniu Instalatora z nośnika na dysku CD. Najnowszy folder na potrzeby instalowania lokacji głównej lub centralnej administracji lub odzyskiwania lokacji głównej lub centralnej administracji. Ta wartość informuje Instalatora że nośnik tworzą dysku CD. R jest używany.  

**RecoveryOptions**  

-   **Nazwa klucza:** ServerRecoveryOptions  

    -   **Wymagane:** Tak  

    -   **Wartości:** 1, 2 lub 4  

         1 = odzyskiwanie serwera lokacji i programu SQL Server.  

         2 = odzyskiwanie tylko serwera lokacji.  

         4 = odzyskiwanie tylko programu SQL Server.  

    -   **Szczegóły:** Określa, czy Instalator będzie przeprowadzał odzyskiwanie serwera lokacji i programu SQL Server. Skojarzone klucze są wymagane podczas ustawiania poniższej wartości dla ustawienia ServerRecoveryOptions:  

        -   **Wartość = 1** Możesz określić wartość dla klucza **SiteServerBackupLocation** , aby odzyskiwać lokację przy użyciu kopii zapasowej lokacji. Jeżeli nie określisz wartości, lokacja zostanie ponownie zainstalowana bez przywracania jej z zestawu kopii zapasowych.  

             Klucz **BackupLocation** jest wymagany w przypadku skonfigurowania dla klucza **DatabaseRecoveryOptions** wartości **10** , która umożliwia przywracanie bazy danych lokacji z kopii zapasowej.  

        -   **Wartość = 2** Możesz określić wartość dla klucza **SiteServerBackupLocation** , aby odzyskać lokację przy użyciu kopii zapasowej lokacji. Jeżeli nie określisz wartości, lokacja zostanie ponownie zainstalowana bez przywracania jej z zestawu kopii zapasowych.  

        -   **Wartość = 4** Klucz **BackupLocation** jest wymagany w przypadku skonfigurowania wartości **10** dla klucza **DatabaseRecoveryOptions** , co oznacza przywrócenie bazy danych lokacji z kopii zapasowej.  

-   **Nazwa klucza:** DatabaseRecoveryOptions  

    -   **Wymagane:** Może być  

    -   **Wartości:** 10, 20, 40, 80  

         10 = przywracanie bazy danych lokacji z kopii zapasowej.  

         20 = korzystanie z bazy danych lokacji, która została ręcznie odzyskana przy użyciu innej metody.  

         40 = tworzenie nowej bazy danych lokacji. Użyj tej opcji, gdy nie ma dostępnej kopii zapasowej bazy danych lokacji. Odzyskiwanie danych globalnych i danych lokacji przebiega przy użyciu replikacji z innych lokacji.  

         80 = pomijanie odzyskiwania bazy danych.  

    -   **Szczegóły:** Określa sposób odzyskiwania bazy danych lokacji w programie SQL Server przez Instalatora. Ten klucz jest wymagany, gdy ustawienie **ServerRecoveryOptions** ma wartość **1** lub **4**.  

-   **Nazwa klucza:** ReferenceSite  

    -   **Wymagane:** Może być  

    -   **Wartości:** &lt;ReferenceSiteFQDN\>  

    -   **Szczegóły:** Określa lokację główną odniesienia do odzyskiwania danych globalnych, jeśli kopia zapasowa bazy danych jest starsza od okresu przechowywania śledzenia zmian lub po odzyskaniu lokacji bez kopii zapasowej używany w witrynie Administracja centralna.  

         Jeśli nie zostanie określona lokacja odniesienia lub kopia zapasowa będzie starsza od okresu przechowywania śledzenia zmian, wszystkie lokacje główne zostaną zainicjowane ponownie przy użyciu danych przywróconych z centralnej lokacji administracyjnej.  

         Jeśli nie określono lokacji odniesienia, a kopia zapasowa pochodzi z okresu przechowywania funkcji monitorowania zmian, replikacja z lokacji głównych będzie dotyczyła jedynie zmian wprowadzonych po wykonaniu kopii zapasowej. W przypadku wystąpienia konfliktu między zmianami z różnych lokacji głównych centralna lokacja administracyjna użyje danych otrzymanych w pierwszej kolejności.  

         Ten klucz jest wymagany, gdy ustawienie **DatabaseRecoveryOptions** ma wartość **40**.  

-   **Nazwa klucza:** SiteServerBackupLocation  

    -   **Wymagane:** Nie  

    -   **Wartości:** &lt;PathToSiteServerBackupSet\>  

    -   **Szczegóły:** Określa ścieżkę do zestawu kopii zapasowych serwera lokacji. Ten klucz jest opcjonalny, gdy ustawienie **ServerRecoveryOptions** ma wartość **1** lub **2**. Określ wartość dla klucza **SiteServerBackupLocation** , aby odzyskiwać lokację przy użyciu kopii zapasowej lokacji. Jeżeli nie określisz wartości, lokacja zostanie ponownie zainstalowana bez przywracania jej z zestawu kopii zapasowych.  

-   **Nazwa klucza:** BackupLocation  

    -   **Wymagane:** Może być  

    -   **Wartości:** &lt;PathToSiteDatabaseBackupSet\>  

    -   **Szczegóły:** Określa ścieżkę do zestawu kopii zapasowych bazy danych lokacji. Klucz **BackupLocation** jest wymagany w przypadku skonfigurowania dla klucza **ServerRecoveryOptions** wartości **1** lub **4** , a dla klucza **DatabaseRecoveryOptions** wartości **10** .  

**Opcje**  

-   **Nazwa klucza:** Identyfikator produktu  

    -   **Wymagane:** Tak  

    -   **Wartości:**  

         xxxxx-xxxxx-xxxxx-xxxxx-xxxxx  

         Eval  

    -   **Szczegóły:** Menedżer konfiguracji instalacji klucz produktu, łącznie z myślnikami. Wprowadź **Eval** można zainstalować wersję ewaluacyjną programu Configuration Manager.  

-   **Nazwa klucza:** Kod lokacji  

    -   **Wymagane:** Tak  

    -   **Wartości:** &lt;Kod lokacji\>  

    -   **Szczegóły:** Trzy znaki alfanumeryczne, które jednoznacznie identyfikuje lokacji w hierarchii. Należy określić kod lokacji używany przez lokację przed awarią.  

-   **Nazwa klucza:** Nazwa witryny  

    -   **Wymagane:** Tak  

    -   **Wartości:** Nazwa witryny  

    -   **Szczegóły:** Opis tej lokacji.  

-   **Nazwa klucza:** SMSInstallDir  

    -   **Wymagane:** Tak  

    -   **Wartości:** &lt;*Ścieżkainstalacjiprogramuconfigmgr*>  

    -   **Szczegóły:** Określa folder instalacji plików programu Configuration Manager.  

        > [!NOTE]  
        >  Można określić nową ścieżkę, aby użyć podczas instalacji programu Configuration Manager lub oryginalnej ścieżce.  

-   **Nazwa klucza:** SDKServer  

    -   **Wymagane:** Tak  

    -   **Wartości:** &lt;*Nazwa FQDN dostawcy programu SMS*>  

    -   **Szczegóły:** Określa nazwę FQDN serwera, który będzie hostem dostawcy programu SMS. Należy określić serwer, który hostował dostawcę programu SMS przed awarią.  

         Po instalacji początkowej możesz skonfigurować dodatkowych dostawców programu SMS dla lokacji.  

-   **Nazwa klucza:** PrerequisiteComp  

    -   **Wymagane:** Tak  

    -   **Wartości:** 0 lub 1  

         0 = pobieranie  

         1 = już pobrane  

    -   **Szczegóły:** Określa, czy pliki wymagań wstępnych Instalatora zostały już pobrane. Jeśli na przykład wybierzesz wartość 0, Instalator pobierze pliki.  

-   **Nazwa klucza:** PrerequisitePath  

    -   **Wymagane:** Tak  

    -   **Wartości:** &lt;*PathToSetupPrerequisiteFiles*>  

    -   **Szczegóły:** Określa ścieżkę do plików wymagań wstępnych Instalatora. W zależności od wartości **PrerequisiteComp** Instalator używa tej ścieżki do przechowywania pobranych plików lub lokalizowania wcześniej pobranych plików.  

-   **Nazwa klucza:** AdminConsole  

    -   **Wymagane:** Może być  

    -   **Wartości:** 0 lub 1  

         0 = nie instaluj  

         1 = zainstaluj  

    -   **Szczegóły:** Określa, czy należy zainstalować konsolę programu Configuration Manager. Ten klucz jest wymagany, chyba że ustawienie **ServerRecoveryOptions** ma wartość **4**.  

-   **Nazwa klucza:** JoinCEIP  

    -   **Wymagane:** Tak  

    -   **Wartości:** 0 lub 1  

         0 = nie dołączaj  

         1 = dołącz  

    -   **Szczegóły:** Określa, czy dołączyć do programu poprawy jakości obsługi klienta.  

**SQLConfigOptions**  

-   **Nazwa klucza:** SQLServerName  

    -   **Wymagane:** Tak  

    -   **Wartości:** *&lt;SQLServerName\>*  

    -   **Szczegóły:** Nazwa serwera lub nazwa wystąpienia klastrowego, programem SQL Server, który będzie obsługiwał bazy danych lokacji. Należy określić serwer, który hostował bazę danych lokacji przed awarią.  

-   **Nazwa klucza:** DatabaseName  

    -   **Wymagane:** Tak  

    -   **Wartości:**  

         *&lt;SiteDatabaseName\>*  

         lub  

         *&lt;InstanceName\>*\\*&lt;SiteDatabaseName\>*  

    -   **Szczegóły:** Nazwa bazy danych programu SQL Server do utworzenia lub używania w celu zainstalowania bazy danych witryny administracji centralnej. Należy określić nazwę bazy danych, która była używana przed awarią.  

        > [!IMPORTANT]  
        >  Jeżeli nie używasz domyślnego wystąpienia, należy określić nazwy wystąpienia i lokacji.  

-   **Nazwa klucza:** SQLSSBPort  

    -   **Wymagane:** Nie  

    -   **Wartości:** &lt;*SSBPortNumber*>  

    -   **Szczegóły:** Określ port usługi SQL Server Service Broker (SSB) używany przez program SQL Server. Zazwyczaj port SSB jest skonfigurowany tak, aby używał portu TCP 4022, ale są obsługiwane również inne porty. Należy określić ten sam port SBB, który był używany przed awarią.  

#### <a name="recover-a-primary-site-unattended"></a>Odzyskiwanie nienadzorowane lokacji głównej  
 Skorzystaj z poniższych informacji, aby skonfigurować plik skryptu instalacji nienadzorowanej odzyskać witryny administracji centralnej.  

 **Identyfikacja**  

-   **Nazwa klucza:** Akcja  

    -   **Wymagane:** Tak  

    -   **Wartości:** RecoverPrimarySite  

    -   **Szczegóły:** Odzyskuje lokację główną  

-   **Nazwa klucza:** CDLatest  

    -   **Wymagane:** Tak — tylko w przypadku używania nośnika z dysku CD. Najnowszy folder.    

    -   **Wartości:** 1 wartości innej niż 1 jest uważany za nie można przy użyciu dysku CD. Najnowsze.

    -   **Szczegóły:** Skrypt musi zawierać ten klucz i wartość po uruchomieniu Instalatora z nośnika na dysku CD. Najnowszy folder na potrzeby instalowania lokacji głównej lub centralnej administracji lub odzyskiwania lokacji głównej lub centralnej administracji. Ta wartość informuje Instalatora że nośnik tworzą dysku CD. R jest używany.

**RecoveryOptions**  

-   **Nazwa klucza:** ServerRecoveryOptions  

    -   **Wymagane:** Tak  

    -   **Wartości:** 1, 2 lub 4  

         1 = odzyskiwanie serwera lokacji i programu SQL Server.  

         2 = odzyskiwanie tylko serwera lokacji.  

         4 = odzyskiwanie tylko programu SQL Server.  

    -   **Szczegóły:** Określa, czy Instalator będzie przeprowadzał odzyskiwanie serwera lokacji i programu SQL Server. Skojarzone klucze są wymagane podczas ustawiania poniższej wartości dla ustawienia ServerRecoveryOptions:  

        -   **Wartość = 1** Możesz określić wartość dla klucza **SiteServerBackupLocation** , aby odzyskiwać lokację przy użyciu kopii zapasowej lokacji. Jeżeli nie określisz wartości, lokacja zostanie ponownie zainstalowana bez przywracania jej z zestawu kopii zapasowych.  

             Klucz **BackupLocation** jest wymagany w przypadku skonfigurowania dla klucza **DatabaseRecoveryOptions** wartości **10** , która umożliwia przywracanie bazy danych lokacji z kopii zapasowej.  

        -   **Wartość = 2** Możesz określić wartość dla klucza **SiteServerBackupLocation** , aby odzyskać lokację przy użyciu kopii zapasowej lokacji. Jeżeli nie określisz wartości, lokacja zostanie ponownie zainstalowana bez przywracania jej z zestawu kopii zapasowych.  

        -   **Wartość = 4** Klucz **BackupLocation** jest wymagany w przypadku skonfigurowania wartości **10** dla klucza **DatabaseRecoveryOptions** , co oznacza przywrócenie bazy danych lokacji z kopii zapasowej.  

-   **Nazwa klucza:** DatabaseRecoveryOptions  

    -   **Wymagane:** Może być  

    -   **Wartości:** 10, 20, 40, 80  

         10 = przywracanie bazy danych lokacji z kopii zapasowej.  

         20 = korzystanie z bazy danych lokacji, która została ręcznie odzyskana przy użyciu innej metody.  

         40 = tworzenie nowej bazy danych lokacji. Użyj tej opcji, gdy nie ma dostępnej kopii zapasowej bazy danych lokacji. Odzyskiwanie danych globalnych i danych lokacji przebiega przy użyciu replikacji z innych lokacji.  

         80 = pomijanie odzyskiwania bazy danych.  

    -   **Szczegóły:** Określa sposób odzyskiwania bazy danych lokacji w programie SQL Server przez Instalatora. Ten klucz jest wymagany, gdy ustawienie **ServerRecoveryOptions** ma wartość **1** lub **4**.  

-   **Nazwa klucza:** SiteServerBackupLocation  

    -   **Wymagane:** Nie  

    -   **Wartości:** &lt;PathToSiteServerBackupSet\>  

    -   **Szczegóły:** Określa ścieżkę do zestawu kopii zapasowych serwera lokacji. Ten klucz jest opcjonalny, gdy ustawienie **ServerRecoveryOptions** ma wartość **1** lub **2**. Określ wartość dla klucza **SiteServerBackupLocation** , aby odzyskiwać lokację przy użyciu kopii zapasowej lokacji. Jeżeli nie określisz wartości, lokacja zostanie ponownie zainstalowana bez przywracania jej z zestawu kopii zapasowych.  

-   **Nazwa klucza:** BackupLocation  

    -   **Wymagane:** Może być  

    -   **Wartości:** &lt;PathToSiteDatabaseBackupSet\>  

    -   **Szczegóły:** Określa ścieżkę do zestawu kopii zapasowych bazy danych lokacji. Klucz **BackupLocation** jest wymagany w przypadku skonfigurowania dla klucza **ServerRecoveryOptions** wartości **1** lub **4** , a dla klucza **DatabaseRecoveryOptions** wartości **10** .  

**Opcje**  

-   **Nazwa klucza:** Identyfikator produktu  

    -   **Wymagane:** Tak  

    -   **Wartości:**  

         xxxxx-xxxxx-xxxxx-xxxxx-xxxxx  

         Eval  

    -   **Szczegóły:** Menedżer konfiguracji instalacji klucz produktu, łącznie z myślnikami. Wprowadź **Eval** można zainstalować wersję ewaluacyjną programu Configuration Manager.  

-   **Nazwa klucza:** Kod lokacji  

    -   **Wymagane:** Tak  

    -   **Wartości:** &lt;Kod lokacji\>  

    -   **Szczegóły:** Trzy znaki alfanumeryczne, które jednoznacznie identyfikuje lokacji w hierarchii. Należy określić kod lokacji używany przez lokację przed awarią.  

-   **Nazwa klucza:** Nazwa witryny  

    -   **Wymagane:** Tak  

    -   **Wartości:** Nazwa witryny  

    -   **Szczegóły:** Opis tej lokacji.  

-   **Nazwa klucza:** SMSInstallDir  

    -   **Wymagane:** Tak  

    -   **Wartości:** &lt;*Ścieżkainstalacjiprogramuconfigmgr*>  

    -   **Szczegóły:** Określa folder instalacji plików programu Configuration Manager.  

        > [!NOTE]  
        >  Można określić nową ścieżkę, aby użyć podczas instalacji programu Configuration Manager lub oryginalnej ścieżce.  

-   **Nazwa klucza:** SDKServer  

    -   **Wymagane:** Tak  

    -   **Wartości:** &lt;*Nazwa FQDN dostawcy programu SMS*>  

    -   **Szczegóły:** Określa nazwę FQDN serwera, który będzie hostem dostawcy programu SMS. Należy określić serwer, który hostował dostawcę programu SMS przed awarią.  

         Po instalacji początkowej możesz skonfigurować dodatkowych dostawców programu SMS dla lokacji.  

-   **Nazwa klucza:** PrerequisiteComp  

    -   **Wymagane:** Tak  

    -   **Wartości:** 0 lub 1  

         0 = pobieranie  

         1 = już pobrane  

    -   **Szczegóły:** Określa, czy pliki wymagań wstępnych Instalatora zostały już pobrane. Jeśli na przykład wybierzesz wartość 0, Instalator pobierze pliki.  

-   **Nazwa klucza:** PrerequisitePath  

    -   **Wymagane:** Tak  

    -   **Wartości:** &lt;*PathToSetupPrerequisiteFiles*>  

    -   **Szczegóły:** Określa ścieżkę do plików wymagań wstępnych Instalatora. W zależności od wartości **PrerequisiteComp** Instalator używa tej ścieżki do przechowywania pobranych plików lub lokalizowania wcześniej pobranych plików.  

-   **Nazwa klucza:** AdminConsole  

    -   **Wymagane:** Może być  

    -   **Wartości:** 0 lub 1  

         0 = nie instaluj  

         1 = zainstaluj  

    -   **Szczegóły:** Określa, czy należy zainstalować konsolę programu Configuration Manager. Ten klucz jest wymagany, chyba że ustawienie **ServerRecoveryOptions** ma wartość **4**.  

-   **Nazwa klucza:** JoinCEIP  

    -   **Wymagane:** Tak  

    -   **Wartości:** 0 lub 1  

         0 = nie dołączaj  

         1 = dołącz  

    -   **Szczegóły:** Określa, czy dołączyć do programu poprawy jakości obsługi klienta.  

**SQLConfigOptions**  

-   **Nazwa klucza:** SQLServerName  

    -   **Wymagane:** Tak  

    -   **Wartości:** *&lt;SQLServerName\>*  

    -   **Szczegóły:** Nazwa serwera lub nazwa wystąpienia klastrowego, programem SQL Server, który będzie obsługiwał bazy danych lokacji. Należy określić serwer, który hostował bazę danych lokacji przed awarią.  

-   **Nazwa klucza:** DatabaseName  

    -   **Wymagane:** Tak  

    -   **Wartości:**  

         *&lt;SiteDatabaseName\>*  

         lub  

         *&lt;InstanceName\>*\\*&lt;SiteDatabaseName\>*  

    -   **Szczegóły:** Nazwa bazy danych programu SQL Server do utworzenia lub używania w celu zainstalowania bazy danych witryny administracji centralnej. Należy określić nazwę bazy danych, która była używana przed awarią.  

        > [!IMPORTANT]  
        >  Jeżeli nie używasz domyślnego wystąpienia, należy określić nazwy wystąpienia i lokacji.  

-   **Nazwa klucza:** SQLSSBPort  

    -   **Wymagane:** Nie  

    -   **Wartości:** &lt;*SSBPortNumber*>  

    -   **Szczegóły:** Określ port usługi SQL Server Service Broker (SSB) używany przez program SQL Server. Zazwyczaj port SSB jest skonfigurowany tak, aby używał portu TCP 4022, ale są obsługiwane również inne porty. Należy określić ten sam port SBB, który był używany przed awarią.  

**Opcja rozszerzenia hierarchii**  

-   **Nazwa klucza:** CCARSiteServer  

    -   **Wymagane:** Może być  

    -   **Wartości:** &lt;*SiteCodeForCentralAdministrationSite*>  

    -   **Szczegóły:** Określa, który po dołączeniu hierarchii programu Configuration Manager wstawi do lokacji głównej witryny administracji centralnej. To ustawienie jest wymagane, jeśli lokacja główna była połączona z centralną lokacją administracyjną przed awarią. Należy określić kod lokacji używany w odniesieniu do centralnej lokacji administracyjnej przed awarią.  

-   **Nazwa klucza:** CASRetryInterval  

    -   **Wymagane:** Nie  

    -   **Wartości:** &lt;*Interwał*>  

    -   **Szczegóły:** Określa interwał ponawiania prób (w minutach) prób połączenia z witryną Administracja centralna, po niepowodzeniu. Jeśli na przykład nie uda się nawiązać połączenia z centralną lokacją administracyjną, lokacja główna ponowi próbę nawiązania połączenia po upływie czasu określonego (w minutach) dla opcji CASRetryInterval.  

-   **Nazwa klucza:** WaitForCASTimeout  

    -   **Wymagane:** Nie  

    -   **Wartości:** &lt;*Limit czasu*>  

    -   **Szczegóły:** Określa maksymalną wartość limitu czasu (w minutach) dla lokacji głównej połączyć się z witryną Administracja centralna. Jeśli na przykład nie uda się nawiązać połączenia między lokacją główną a centralną lokacją administracyjną, lokacja główna ponowi próbę połączenia z centralną lokacją administracyjną na podstawie wartości CASRetryInterval przed upływem czasu określonego w opcji WaitForCASTimeout. Możesz określić wartość z zakresu od 0 do 100.  

###  <a name="BKMK_PostRecovery"></a> Zadania po odzyskiwaniu  
 Po odzyskaniu lokacji należy wykonać szereg zadań umożliwiających ukończenie procesu odzyskiwania lokacji. Informacje w poniższych sekcjach mogą ułatwić ukończenie procesu odzyskiwania lokacji.  

#### <a name="re-enter-user-account-passwords"></a>Ponowne wprowadzanie haseł kont użytkowników  
 Po odzyskaniu serwera lokacji należy ponownie wprowadzić hasła kont użytkowników określonych dla lokacji, ponieważ są one resetowane podczas odzyskiwania lokacji. Konta są wyświetlane na stronie **Zakończ** Kreatora instalacji po ukończeniu odzyskiwania lokacji i zapisywane w pliku C:\ConfigMgrPostRecoveryActions.html na odzyskanym serwerze lokacji.  

###### <a name="to-re-enter-user-account-passwords-after-site-recovery"></a>Aby ponownie wprowadzić hasła kont użytkowników po odzyskaniu lokacji:  

1.  Otwórz konsolę programu Configuration Manager i połącz się z odzyskaną lokacją.  

2.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

3.  W obszarze roboczym **Administracja** rozwiń węzeł **Zabezpieczenia**, a następnie kliknij przycisk **Konta**.  

4.  Wykonaj następujące czynności w odniesieniu do wszystkich kont, dla których konieczne jest ponowne wprowadzenie hasła:  

    1.  Wybierz konto z listy kont zidentyfikowanych po odzyskaniu lokacji. Listę kont zawiera plik C:\ConfigMgrPostRecoveryActions.html na odzyskanym serwerze lokacji.  

    2.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości** , aby otworzyć właściwości konta.  

    3.  Na karcie **Ogólne** kliknij przycisk **Ustaw**, a następnie wprowadź ponownie hasła konta.  

    4.  Kliknij przycisk **Weryfikuj**, wybierz odpowiednie źródło danych dla wybranego konta użytkownika, a następnie kliknij opcję **Testuj połączenie** , aby sprawdzić, czy można połączyć konto użytkownika ze źródłem danych.  

    5.  Kliknij przycisk **OK** , aby zapisać zmiany haseł, a następnie kliknij przycisk **OK**.  

#### <a name="re-enter-sideloading-keys"></a>Ponowne wprowadzanie kluczy ładowania bezpośredniego  
 Po odzyskaniu serwera lokacji należy ponownie wprowadzić klucze pobierania lokalnego systemu Windows wprowadzone dla tej lokacji. Jest to konieczne, gdyż podczas odzyskiwania dochodzi do zresetowania tych kluczy. Po ich ponownym wprowadzeniu klucze pobierania lokalnego, liczba w **użyte aktywacje** kluczy ładowania bezpośredniego systemu Windows zostanie zresetowana w konsoli programu Configuration Manager. Na przykład załóżmy, że przed awarią lokacji **łączna liczba aktywacji** miał wartość **100** i **użyte aktywacje** w **90** liczbę kluczy wykorzystanych przez urządzenia. Po odzyskaniu lokacji w kolumnie **Łączna liczba aktywacji** jest nadal wyświetlana liczba **100**, lecz w kolumnie **Użyte aktywacje** znajduje się nieprawidłowa wartość **0**. Jednak wprowadzenie 10 nowych urządzeń do kluczy pobierania lokalnego wyczerpie zapas kluczy i uniemożliwi zastosowanie nowego klucza do kolejnego urządzenia.  

#### <a name="recreate-the-microsoft-intune-subscription"></a>Ponowne tworzenie subskrypcji usługi Microsoft Intune  
 W przypadku odzyskiwania serwera lokacji programu Configuration Manager po komputera serwera lokacji jest ponownie obrazami, subskrypcji usługi Microsoft Intune nie została przywrócona. Po odzyskaniu lokacji należy ponownie podłączyć subskrypcji.  Nie należy tworzyć nowe żądanie APN, ale zamiast tego przekazać bieżący prawidłowy — plik PEM przekazanemu podczas ostatniego iOS zarządzania został skonfigurowany lub odnowienia. Aby uzyskać więcej informacji, zobacz [Konfigurowanie subskrypcji usługi Microsoft Intune](/sccm/mdm/deploy-use/configure-intune-subscription).  

#### <a name="configure-ssl-for-site-system-roles-that-use-iis"></a>Konfiguracja protokołu SSL w rolach systemu lokacji używających usług IIS  
 Po odzyskaniu systemu lokacji z serwerem IIS i skonfigurowanym przed awarią protokołem HTTPS, należy zrekonfigurować serwer IIS tak, aby używany w nim był certyfikat serwera sieci Web.  

#### <a name="reinstall-hotfixes-in-the-recovered-site-server"></a>Ponowna instalacja poprawek w odzyskanym serwerze lokacji  
 Po odzyskaniu serwera lokacji należy ponownie zainstalować wszystkie poprawki zastosowane do serwera lokacji. Po odzyskaniu lokacji lista uprzednio zainstalowanych poprawek znajduje się na stronie **Zakończono** Kreatora instalacji i jest zapisywana w pliku **C:\ConfigMgrPostRecoveryActions.html** na odzyskanym serwerze lokacji.  

#### <a name="recover-custom-reports-on-the-computer-running-reporting-services"></a>Odzyskiwanie niestandardowych raportów na komputerze z uruchomioną usługą Reporting Services  
 Przy wcześniejszym utworzeniu kopii zapasowej serwera raportów, istnieje możliwość odzyskania niestandardowych raportów usług Reporting Services utraconych po jego awarii. Więcej informacji o przywracaniu niestandardowych raportów w programie Reporting Services znajduje się w sekcji [Tworzenie i przywracanie kopii zapasowych w instalacji programu Reporting Services](http://go.microsoft.com/fwlink/p/?LinkId=228724) w dokumentacji programu SQL Server 2008 — Books Online.  

#### <a name="recover-content-files"></a>Odzyskiwanie plików zawartości  
 Chociaż baza danych lokacji zawiera informacje o miejscu przechowywania zawartości na serwerze lokacji, to pliki zawartości nie są ujęte w procesach tworzenia i odzyskiwania kopii zapasowej. Aby całkowicie odzyskać pliki zawartości, należy przywrócić bibliotekę zawartości oraz pliki źródłowe pakietu do początkowej lokacji. Istnieje kilka metod odzyskiwania plików zawartości. Najprostszą jest przywrócenie plików z kopii zapasowej systemu plików na serwerze lokacji.  

 Jeśli nie jest dostępna kopia zapasowa systemu plików dla plików źródłowych pakietu, należy je ręcznie skopiować lub pobrać tak samo, jak przy pierwotnym tworzeniu pakietu. Aby znaleźć lokalizację źródłową wszystkich pakietów i aplikacji, można uruchomić następujące zapytanie w programie SQL Server: `SELECT * FROM v_Package`. Możesz określić lokację źródłową pakietu za pomocą trzech pierwszych znaków identyfikatora pakietu. Na przykład jeśli identyfikator pakietu to CEN00001, kod lokacji źródłowej to CEN. Pliki źródłowe pakietu muszą być przywrócone do tej samej lokacji, w której znajdowały się przed awarią.  

 Jeśli kopia zapasowa systemu plików z biblioteką zawartości nie jest dostępna, masz następujące opcje przywracania:  

-   **Zaimportowanie wstępnie przygotowanego pliku zawartości**: Masz hierarchii programu Configuration Manager, można utworzyć wstępnie przygotowany plik zawartości ze wszystkimi pakietami i aplikacjami z innej lokalizacji, a następnie zaimportować wstępnie przygotowanego pliku zawartości do odzyskania biblioteki zawartości na serwerze lokacji.  

-   **Aktualizowanie zawartości**: Po uruchomieniu działania aktualizacji zawartości odpowiedniego dla typu wdrożenia pakietu lub aplikacji zawartość zostanie skopiowana ze źródła pakietu do biblioteki zawartości. Aby to działanie zakończyło się pomyślnie, pliki źródłowe pakietu muszą być dostępne w początkowej lokacji. Działanie to należy wykonać we wszystkich pakietach i aplikacjach.  

#### <a name="recover-custom-software-updates-on-the-computer-running-updates-publisher"></a>Odzyskiwanie niestandardowych aktualizacji oprogramowania na komputerze z uruchomionym programem Updates Publisher  
 Gdy dołączenie plików bazy danych wydawcy aktualizacji planu tworzenia kopii zapasowej, można odzyskać bazy danych w razie awarii na komputerze, na którym jest uruchomiony program Updates Publisher. Więcej informacje dotyczących programu Updates Publisher znajduje się w temacie [System Center Updates Publisher 2011](http://go.microsoft.com/fwlink/p/?LinkId=228726) w bibliotece TechCenter dla programu System Center.  

 Przywracanie bazy danych programu Updates Publisher, należy użyć następującej procedury.  

###### <a name="to-restore-the-updates-publisher-2011-database"></a>Aby przywrócić bazę danych programu Updates Publisher 2011  

1.  Zainstaluj ponownie Updates Publisher na odzyskanym komputerze.  

2.  Skopiuj plik bazy danych (Scupdb.sdf) z miejsce docelowe kopii zapasowej %*USERPROFILE*%\AppData\Local\Microsoft\System Center Updates Publisher 2011\5.00.1727.0000\ na komputerze z programem Updates Publisher.  

3.  Po uruchomieniu Updates Publisher na komputerze więcej niż jednego użytkownika każdego pliku bazy danych należy skopiować do odpowiedniej lokalizacji profilu.  

#### <a name="user-state-migration-data"></a>Dane migracji stanu użytkownika  
 Częścią właściwości systemu lokacji punktu migracji stanu jest określenie folderów, w których znajdują się dane migracji stanu użytkownika. Po odzyskaniu serwera z folderem, w którym znajdują się dane migracji stanu użytkownika należy ręcznie przywrócić te dane migracji na serwer z takimi samymi folderami, w których znajdowały się dane przed awarią.  

#### <a name="regenerate-the-certificates-for-distribution-points"></a>Ponowne generowanie certyfikatów dla punktów dystrybucji  
 Po przywróceniu witryny distmgr.log może zawierać następujący wpis dla jednego lub więcej punktów dystrybucji: **Nie można odszyfrować certyfikatu PFX danych**. Ten wpis informuje, że lokacja nie może odszyfrować danych certyfikatu punktu dystrybucji. Aby rozwiązać ten problem, należy ponownie wygenerować lub ponownie zaimportować certyfikat dla punktów dystrybucji, których dotyczy ten problem. W tym celu możesz użyć polecenia cmdlet programu PowerShell [Set-CMDistributionPoint](https://technet.microsoft.com/library/jj821872\(v=sc.20\).aspx).  

#### <a name="update-certificates-used-for-cloud-based-distribution-points"></a>Aktualizacja certyfikatów używanych w chmurowych punktach dystrybucji  
 Program Configuration Manager wymaga certyfikat zarządzania, który używa serwer lokacji do komunikacji między punktem dystrybucji w chmurze. Po odzyskaniu lokacji należy ręcznie zaktualizować certyfikaty dla chmurowych punktów dystrybucji.  

####  <a name="BKMK_RecoverSecondarySite"></a> Odzyskiwanie lokacji dodatkowej  
 Menedżer konfiguracji nie obsługuje wykonywania kopii zapasowych bazy danych w lokacji dodatkowej, ale obsługuje odzyskiwanie przez ponowne zainstalowanie lokacji dodatkowej. Odzyskiwanie lokacji dodatkowej jest wymagany, gdy dodatkowej lokacji programu Configuration Manager nie powiedzie się. Lokację dodatkową można odzyskać za pomocą **odzyskiwanie lokacji dodatkowej** akcji z **witryny** węzła w konsoli programu Configuration Manager. W przeciwieństwie do odzyskiwania centralnej lokacji administracyjnej lub lokacji głównej podczas odzyskiwania lokacji dodatkowej nie jest używany plik kopii zapasowej. Zamiast tego pliki lokacji dodatkowej są ponownie instalowane na komputerze w lokacji dodatkowej, na którym wystąpiła awaria. Następnie dane w lokacji dodatkowej są ponownie inicjowane danymi z nadrzędnej lokacji głównej. Podczas procesu odzyskiwania programu Configuration Manager sprawdza, czy Biblioteka zawartości istnieje na komputerze lokacji dodatkowej i czy jest dostępna odpowiednia zawartość. Lokacja dodatkowa użyje istniejącej biblioteki zawartości, o ile zawiera ona odpowiednią zawartość. W przeciwnym razie odzyskanie biblioteki zawartości w odzyskanej lokacji dodatkowej wymaga ponownej dystrybucji lub wstępnego przygotowania zawartości dla odzyskanej lokacji. Punkt dystrybucji poza lokacją dodatkową nie musi być instalowany ponownie podczas odzyskiwania tej lokacji. Odzyskana lokacja dodatkowa zostanie automatycznie zsynchronizowana ponownie z punktem dystrybucji.  

 Status odzyskiwania lokacji dodatkowej można sprawdzić za pomocą **Pokaż stan instalacji** akcji z **witryny** węzła w konsoli programu Configuration Manager.  

> [!IMPORTANT]  
>  Aby pomyślnie odzyskać lokację dodatkową, należy użyć komputera z taką samą konfiguracją, co w komputerze, który uległ awarii, w tym nazwę FQDN. W komputerze muszą zostać także spełnione wszystkie wymagania wstępne dotyczące lokacji, w tym odpowiednie prawa zabezpieczeń. Należy także użyć tej samej ścieżki instalacji, co w uszkodzonej lokacji.  

> [!IMPORTANT]  
>  Podczas odzyskiwania lokacji dodatkowej programu Configuration Manager nie instaluje programu SQL Server Express nie jest zainstalowany na komputerze. Dlatego należy wcześniej zainstalować ręcznie program SQL Server Express lub SQL Server w lokacji dodatkowej. Wersja i wystąpienie programu SQL Server do bazy danych lokacji dodatkowej muszą być takie same, co przed awarią.  

##  <a name="BKMK_SMSWriterService"></a> Usługa składnika zapisywania programu SMS  
 Składnik zapisywania programu SMS to usługa, która w trakcie tworzenia kopii zapasowej wchodzi w interakcję z usługą kopiowania woluminów w tle (VSS). Składnik zapisywania programu SMS, który musi być uruchomiona usługa Kopia lokacji programu Configuration Manager do pomyślnie ukończona.  

### <a name="purpose"></a>Cel  
 Usługa składnika zapisywania programu SMS rejestruje się w usłudze VSS i wiąże z jej interfejsami i zdarzeniami. Kiedy usługa VSS rozgłasza zdarzenia lub jeśli wysyła określone powiadomienia do usługi składnika zapisywania programu SMS, ta ostatnia odpowiada na powiadomienie i podejmuje odpowiednie działanie. Składnik zapisywania programu SMS odczytuje plik sterowania kopii zapasowej (smsbkup.ctl), znajdujący się w &lt; *ścieżkę instalacji programu ConfigMgr*> \inboxes\smsbkup.box i ustala pliki oraz dane, które są do wykonania kopii zapasowej. Na podstawie tych informacji, a także określonych danych z kluczy i podkluczy rejestru programu SMS, usługa składnika zapisywania programu SMS tworzy metadane, złożone z różnych składników. Metadane te przesyła następnie na żądanie usłudze VSS. VSS z kolei wysyła metadane do aplikacji żądającej Menedżer kopii zapasowej programu Configuration Manager. Menedżer kopii zapasowych wybiera dane przeznaczone do utworzenia kopii zapasowej i za pośrednictwem usługi VSS wysyła te dane do usługi składnika zapisywania programu SMS. Ta ostatnia podejmuje odpowiednie czynności przygotowawcze do tworzenia kopii zapasowej. Później kiedy Usługa VSS jest gotowa do sporządzenia migawki, wysyła odpowiednie zdarzenie, składnik zapisywania programu SMS zatrzymuje wszystkie usługi programu Configuration Manager i zapewnia, że działania programu Configuration Manager są zablokowane na czas tworzenia migawki. Po ukończeniu tworzenia migawki usługa składnika zapisywania programu SMS uruchamia ponownie usługi i działania.  

 Usługa składnika zapisywania programu SMS jest instalowana automatycznie. Musi ona być uruchomiona, kiedy aplikacja VSS żąda utworzenia lub przywrócenia kopii zapasowej.  

### <a name="writer-id"></a>Identyfikator modułu zapisującego  
 Identyfikator modułu zapisującego składnika zapisywania programu SMS jest: 03ba67dd-dc6d-4729-a038-251f7018463b.  

### <a name="permissions"></a>Uprawnienia  
 Usługa składnika zapisywania programu SMS musi być uruchomiona za pomocą konta System lokalny.  

### <a name="volume-shadow-copy-service"></a>Usługa kopiowania woluminów w tle  
 Usługa VSS stanowi zestaw interfejsów API modelu COM z zaimplementowaną strukturą pozwalającą na tworzenie kopii zapasowych woluminów bez przerywania zapisu wykonywanego na tych woluminach przez aplikacje systemowe. Usługa VSS zapewnia spójny interfejs, umożliwiający koordynację między tymi aplikacjami użytkowników, które aktualizują dane na dysku (usługa składnika zapisywania programu SMS) i tymi, które wykonują kopie zapasowe aplikacji (usługa menedżera kopii zapasowych). Więcej informacji o usłudze VSS znajduje się w artykule [Usługa kopiowania woluminów w tle](http://go.microsoft.com/fwlink/p/?LinkId=241968) w witrynie Windows Server TechCenter.  

