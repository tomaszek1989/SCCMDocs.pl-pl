---
title: Nienadzorowane odzyskiwanie | Dokumentacja firmy Microsoft
description: "Odzyskiwanie lokacji w programie System Center Configuration Manager za pomocą skryptu."
ms.custom: na
ms.date: 6/5/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 828c31d1-3d70-4412-b1a8-c92e7e504d39
caps.latest.revision: 
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: b5a1a1d165a6888bc26e809666d2331ff3c24d68
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="unattended-site-recovery-for-configuration-manager"></a>Nienadzorowane odzyskiwanie lokacji programu Configuration Manager   

*Dotyczy: System Center Configuration Manager (Current Branch)* przeprowadzić [nienadzorowane odzyskiwanie](/sccm/protect/understand/recover-sites#site-recovery-procedures) programu Configuration Manager centralnej lokacji administracyjnej lub lokacji głównej, można utworzyć skrypt instalacji nienadzorowanej, a następnie użyć Instalatora z **/script** — opcja polecenia. Skrypt zawiera ten sam typ informacji, o które monituje Kreator instalacji, różnica polega tylko na braku ustawień domyślnych. Należy określić wszystkie wartości kluczy instalacji mających zastosowanie do używanego typu odzyskiwania.

 Aby użyć opcji wiersza polecenia Instalatora /script, należy utworzyć plik inicjujący oraz podać jego nazwę po opcji wiersza polecenia Instalatora /script. Nazwa pliku jest bez znaczenia, jak długo ma **.ini** rozszerzenia nazwy pliku. Podając odniesienie do pliku inicjowania Instalatora w wierszu polecenia, należy wprowadzić pełną ścieżkę do pliku. Na przykład, jeśli plik inicjujący Instalatora nosi nazwę *setup.ini*, i jest on przechowywany w *folderze C:\setup*, będzie wierszu polecenia:

 **setup /script c:\setup\setup.ini**.

> [!IMPORTANT]  
>  Uruchomienie Instalatora wymaga praw administratora. Uruchamiając Instalatora ze skryptem instalacji nienadzorowanej, należy uruchomić wiersz polecenia z uprawnieniami administratora przy użyciu polecenia **Uruchom jako administrator**.

 Skrypt zawiera nazwy sekcji i kluczy oraz wartości. Wymagane nazwy kluczy sekcji różnią się w zależności od typu odzyskiwania, którego skrypt jest wykonywany. Kolejność kluczy w sekcjach oraz kolejność sekcji w pliku nie mają znaczenia. W kluczach nie jest uwzględniana wielkość liter. Podając wartości kluczy, należy pamiętać, że po nazwie klucza należy wprowadzić znak równości (=), a następnie jego wartość.

 Poniższe sekcje zawierają informacje pomocne w tworzeniu skryptu nienadzorowanego odzyskiwania lokacji. Tabele zawierają listę dostępnych kluczy skryptu instalacji, ich wartości, informację, czy dany klucz jest wymagany, typ instalacji, do której klucz skryptu jest używany, oraz krótki opis klucza.

## <a name="recover-a-central-administration-site-unattended"></a>Odzyskiwanie nienadzorowane centralnej lokacji administracyjnej
 Skorzystaj z poniższych informacji, aby skonfigurować plik skryptu instalacji nienadzorowanej do odzyskiwania centralnej lokacji administracyjnej.

 **Identyfikacja**

-   **Nazwa klucza:** Akcja

    -   **Wymagane:** Tak
    -   **Wartości:** RecoverCCAR
    -   **Szczegóły:** Odzyskuje centralną lokację administracyjną


-   **Nazwa klucza:** CDLatest

    -   **Wymagane:** Tak — tylko w przypadku używania nośnika z dysku CD. Najnowszy folder.
    -   **Wartości:** 1 wartości innej niż 1 jest uważana za nie można przy użyciu dysku CD. Najnowsze.
    -   **Szczegóły:** Skrypt musi zawierać ten klucz i wartość po uruchomieniu Instalatora z nośnika na dysku CD. Najnowszy folder na potrzeby instalowania lokacji głównej lub centralnej administracji lub lokacji głównej lub centralnej administracji odzyskiwania. Ta wartość informuje Instalatora czy multimediów tworzą dysku CD. Jest używana najnowsza.

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

    -   **Wymagane:** Być może
    -   **Wartości:** 10, 20, 40, 80  
         10 = przywracanie bazy danych lokacji z kopii zapasowej.  
         20 = korzystanie z bazy danych lokacji, która została ręcznie odzyskana przy użyciu innej metody.   
         40 = tworzenie nowej bazy danych lokacji. Użyj tej opcji, gdy nie ma dostępnej kopii zapasowej bazy danych lokacji. Odzyskiwanie danych globalnych i danych lokacji przebiega przy użyciu replikacji z innych lokacji.  
         80 = pomijanie odzyskiwania bazy danych.
    -   **Szczegóły:** Określa sposób odzyskiwania bazy danych lokacji w programie SQL Server przez Instalatora. Ten klucz jest wymagany, gdy ustawienie **ServerRecoveryOptions** ma wartość **1** lub **4**.


-   **Nazwa klucza:** ReferenceSite  

    -   **Wymagane:** Być może
    -   **Wartości:** &lt;Nazwa FQDN lokacji odniesienia\>
    -   **Szczegóły:** Określa lokację główną odniesienia używaną przez centralną lokację administracyjną do odzyskiwania danych globalnych, jeśli kopia zapasowa bazy danych jest starsza od okresu przechowywania śledzenia zmian lub w przypadku odzyskiwania lokacji bez kopii zapasowej.

         Jeśli nie określono lokacji odniesienia, a tworzenie kopii zapasowej jest starsza od okresu przechowywania śledzenia zmian, wszystkie lokacje główne zostaną zainicjowane ponownie przy użyciu danych przywróconych z centralnej lokacji administracyjnej.

         Jeśli nie określono lokacji odniesienia, a kopia zapasowa pochodzi okresu przechowywania śledzenia zmian, jedynie zmian wprowadzonych po wykonaniu kopii zapasowej są replikowane w lokacjach głównych. W przypadku wystąpienia konfliktu między zmianami z różnych lokacji głównych centralna lokacja administracyjna użyje danych otrzymanych w pierwszej kolejności.

         Ten klucz jest wymagany, gdy ustawienie **DatabaseRecoveryOptions** ma wartość **40**.

-   **Nazwa klucza:** SiteServerBackupLocation

    -   **Wymagane:** Nie
    -   **Wartości:** &lt;Ścieżka_do_zestawu_kopii_zapasowych_serwera_lokacji\>
    -   **Szczegóły:** Określa ścieżkę do zestawu kopii zapasowych serwera lokacji. Ten klucz jest opcjonalny, gdy ustawienie **ServerRecoveryOptions** ma wartość **1** lub **2**. Określ wartość dla klucza **SiteServerBackupLocation** , aby odzyskiwać lokację przy użyciu kopii zapasowej lokacji. Jeżeli nie określisz wartości, lokacja zostanie ponownie zainstalowana bez przywracania jej z zestawu kopii zapasowych.


-   **Nazwa klucza:** BackupLocation

    -   **Wymagane:** Być może
    -   **Wartości:** &lt;Ścieżka_do_zestawu_kopii_zapasowych_bazy_danych_lokacji\>
    -   **Szczegóły:** Określa ścieżkę do zestawu kopii zapasowych bazy danych lokacji. Klucz **BackupLocation** jest wymagany w przypadku skonfigurowania dla klucza **ServerRecoveryOptions** wartości **1** lub **4** , a dla klucza **DatabaseRecoveryOptions** wartości **10** .


**Opcje**

-   **Nazwa klucza:** Identyfikator produktu
    -   **Wymagane:** Tak
    -   **Wartości:**   
         xxxxx-xxxxx-xxxxx-xxxxx-xxxxx  
          Eval
    -   **Szczegóły:** Menedżer konfiguracji instalacji klucz produktu, wraz z kreskami. Wprowadź **Eval** można zainstalować wersję ewaluacyjną programu Configuration Manager.  


-   **Nazwa klucza:** Kod lokacji

    -   **Wymagane:** Tak
    -   **Wartości:** &lt;Kod lokacji\>
    -   **Szczegóły:** Trzy znaki alfanumeryczne, które jednoznacznie identyfikują lokację w hierarchii. Należy określić kod lokacji używany przez lokację przed awarią.


-   **Nazwa klucza:** Nazwa witryny

    -   **Wymagane:** Tak
    -   **Wartości:** Nazwa witryny
    -   **Szczegóły:** Opis dla tej lokacji.


-   **Nazwa klucza:** SMSInstallDir

    -   **Wymagane:** Tak
    -   **Wartości:** &lt;*Ścieżka_instalacji_programu_configmgr*>
    -   **Szczegóły:** Określa folder instalacji plików programu Configuration Manager.
        > [!NOTE]   
        >  Możesz określić oryginalną lub nową ścieżkę do użycia na potrzeby instalacji programu Configuration Manager.

-   **Nazwa klucza:** SDKServer

    -   **Wymagane:** Tak
    -   **Wartości:** &lt;*Nazwa FQDN dostawcy programu SMS*>
    -   **Szczegóły:** Określa nazwę FQDN serwera, który będzie hostował dostawcę programu SMS. Należy określić serwer, który hostował dostawcę programu SMS przed awarią.

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

    -   **Wymagane:** Być może
    -   **Wartości:** 0 lub 1 0 = nie instaluj   
         1 = zainstaluj
    -   **Szczegóły:** Określa, czy instalować konsolę programu Configuration Manager. Ten klucz jest wymagany, chyba że ustawienie **ServerRecoveryOptions** ma wartość **4**.


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
    -   **Szczegóły:** Nazwa serwera lub nazwa wystąpienia klastrowego z programem SQL Server, który będzie hostem bazy danych. Należy określić serwer, który hostował bazę danych lokacji przed awarią.


-   **Nazwa klucza:** DatabaseName

    -   **Wymagane:** Tak
    -   **Wartości:** *&lt;Nazwa_bazy_danych_lokacji\>*  lub  *&lt;InstanceName\>*\\*&lt;Nazwa_bazy_danych_lokacji\>*
    -   **Szczegóły:** Nazwa bazy danych programu SQL Server do utworzenia lub używania w celu zainstalowania bazy danych witryny Administracja centralna. Należy określić nazwę bazy danych, która była używana przed awarią.

        > [!IMPORTANT]  
        >  Jeżeli nie używasz domyślnego wystąpienia, należy określić nazwy wystąpienia i lokacji.

-   **Nazwa klucza:** SQLSSBPort

    -   **Wymagane:** Nie
    -   **Wartości:** &lt;*Numer_portu_usługi_ssb*>
    -   **Szczegóły:** Określ port usługi SQL Server Service Broker (SSB) używany przez program SQL Server. Zazwyczaj port SSB jest skonfigurowany tak, aby używał portu TCP 4022, ale są obsługiwane również inne porty. Należy określić ten sam port SBB, który był używany przed awarią.

## <a name="recover-a-primary-site-unattended"></a>Odzyskiwanie nienadzorowane lokacji głównej
 Skorzystaj z poniższych informacji, aby skonfigurować plik skryptu instalacji nienadzorowanej do odzyskiwania centralnej lokacji administracyjnej.

 **Identyfikacja**

-   **Nazwa klucza:** Akcja

    -   **Wymagane:** Tak
    -   **Wartości:** RecoverPrimarySite
    -   **Szczegóły:** Odzyskuje lokację główną


-   **Nazwa klucza:** CDLatest

    -   **Wymagane:** Tak — tylko w przypadku używania nośnika z dysku CD. Najnowszy folder.
    -   **Wartości:** 1 wartości innej niż 1 jest uważana za nie można przy użyciu dysku CD. Najnowsze.
    -   **Szczegóły:** Skrypt musi zawierać ten klucz i wartość po uruchomieniu Instalatora z nośnika na dysku CD. Najnowszy folder na potrzeby instalowania lokacji głównej lub centralnej administracji lub lokacji głównej lub centralnej administracji odzyskiwania. Ta wartość informuje Instalatora czy multimediów tworzą dysku CD. Jest używana najnowsza.

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

    -   **Wymagane:** Być może
    -   **Wartości:** 10, 20, 40, 80  
         10 = przywracanie bazy danych lokacji z kopii zapasowej.  
         20 = korzystanie z bazy danych lokacji, która została ręcznie odzyskana przy użyciu innej metody.     
         40 = tworzenie nowej bazy danych lokacji. Użyj tej opcji, gdy nie ma dostępnej kopii zapasowej bazy danych lokacji. Odzyskiwanie danych globalnych i danych lokacji przebiega przy użyciu replikacji z innych lokacji.  
         80 = pomijanie odzyskiwania bazy danych.
    -   **Szczegóły:** Określa sposób odzyskiwania bazy danych lokacji w programie SQL Server przez Instalatora. Ten klucz jest wymagany, gdy ustawienie **ServerRecoveryOptions** ma wartość **1** lub **4**.


-   **Nazwa klucza:** SiteServerBackupLocation

    -   **Wymagane:** Nie
    -   **Wartości:** &lt;Ścieżka_do_zestawu_kopii_zapasowych_serwera_lokacji\>
    -   **Szczegóły:** Określa ścieżkę do zestawu kopii zapasowych serwera lokacji. Ten klucz jest opcjonalny, gdy ustawienie **ServerRecoveryOptions** ma wartość **1** lub **2**. Określ wartość dla klucza **SiteServerBackupLocation** , aby odzyskiwać lokację przy użyciu kopii zapasowej lokacji. Jeżeli nie określisz wartości, lokacja zostanie ponownie zainstalowana bez przywracania jej z zestawu kopii zapasowych.     


-   **Nazwa klucza:** BackupLocation

    -   **Wymagane:** Być może
    -   **Wartości:** &lt;Ścieżka_do_zestawu_kopii_zapasowych_bazy_danych_lokacji\>
    -   **Szczegóły:** Określa ścieżkę do zestawu kopii zapasowych bazy danych lokacji. Klucz **BackupLocation** jest wymagany w przypadku skonfigurowania dla klucza **ServerRecoveryOptions** wartości **1** lub **4** , a dla klucza **DatabaseRecoveryOptions** wartości **10** .

**Opcje**

-   **Nazwa klucza:** Identyfikator produktu

    -   **Wymagane:** Tak
    -   **Wartości:**     
         xxxxx-xxxxx-xxxxx-xxxxx-xxxxx  
         Eval     
    -   **Szczegóły:** Menedżer konfiguracji instalacji klucz produktu, wraz z kreskami. Wprowadź **Eval** można zainstalować wersję ewaluacyjną programu Configuration Manager.  


-   **Nazwa klucza:** Kod lokacji

    -   **Wymagane:** Tak
    -   **Wartości:** &lt;Kod lokacji\>
    -   **Szczegóły:** Trzy znaki alfanumeryczne, które jednoznacznie identyfikują lokację w hierarchii. Należy określić kod lokacji używany przez lokację przed awarią.


-   **Nazwa klucza:** Nazwa witryny

    -   **Wymagane:** Tak
    -   **Wartości:** Nazwa witryny
    -   **Szczegóły:** Opis dla tej lokacji.


-   **Nazwa klucza:** SMSInstallDir

    -   **Wymagane:** Tak
    -   **Wartości:** &lt;*Ścieżka_instalacji_programu_configmgr*>
    -   **Szczegóły:** Określa folder instalacji plików programu Configuration Manager.

        > [!NOTE]   
        >  Możesz określić oryginalną lub nową ścieżkę do użycia na potrzeby instalacji programu Configuration Manager.

-   **Nazwa klucza:** SDKServer

    -   **Wymagane:** Tak
    -   **Wartości:** &lt;*Nazwa FQDN dostawcy programu SMS*>
    -   **Szczegóły:** Określa nazwę FQDN serwera, który będzie hostował dostawcę programu SMS. Należy określić serwer, który hostował dostawcę programu SMS przed awarią.

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

    -   **Wymagane:** Być może
    -   **Wartości:** 0 lub 1  
         0 = nie instaluj   
         1 = zainstaluj  
    -   **Szczegóły:** Określa, czy instalować konsolę programu Configuration Manager. Ten klucz jest wymagany, chyba że ustawienie **ServerRecoveryOptions** ma wartość **4**.

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
    -   **Szczegóły:** Nazwa serwera lub nazwa wystąpienia klastrowego z programem SQL Server, który będzie hostem bazy danych. Należy określić serwer, który hostował bazę danych lokacji przed awarią.


-   **Nazwa klucza:** DatabaseName

    -   **Wymagane:** Tak
    -   **Wartości:** *&lt;Nazwa_bazy_danych_lokacji\>*  lub  *&lt;InstanceName\>*\\*&lt;Nazwa_bazy_danych_lokacji\>*
    -   **Szczegóły:** Nazwa bazy danych programu SQL Server do utworzenia lub używania w celu zainstalowania bazy danych witryny Administracja centralna. Należy określić nazwę bazy danych, która była używana przed awarią.

        > [!IMPORTANT]    
        >  Jeżeli nie używasz domyślnego wystąpienia, należy określić nazwy wystąpienia i lokacji.

-   **Nazwa klucza:** SQLSSBPort

    -   **Wymagane:** Nie
    -   **Wartości:** &lt;*Numer_portu_usługi_ssb*>
    -   **Szczegóły:** Określ port usługi SQL Server Service Broker (SSB) używany przez program SQL Server. Zazwyczaj port SSB jest skonfigurowany tak, aby używał portu TCP 4022, ale są obsługiwane również inne porty. Należy określić ten sam port SBB, który był używany przed awarią.

**Opcja rozszerzenia hierarchii**

-   **Nazwa klucza:** CCARSiteServer

    -   **Wymagane:** Być może
    -   **Wartości:** &lt;*Kod centralnej lokacji administracyjnej*>
    -   **Szczegóły:** Określa lokację administracji centralnej, który będzie dołączać lokacja główna po dołączeniu do hierarchii programu Configuration Manager. To ustawienie jest wymagane, jeśli lokacja główna była połączona z centralną lokacją administracyjną przed awarią. Należy określić kod lokacji używany w odniesieniu do centralnej lokacji administracyjnej przed awarią.

-   **Nazwa klucza:** CASRetryInterval

    -   **Wymagane:** Nie
    -   **Wartości:** &lt;*Interwał*>
    -   **Szczegóły:** Określa interwał ponawiania prób (w minutach) prób połączenia z lokacją administracji centralnej po niepowodzeniu. Jeśli na przykład nie uda się nawiązać połączenia z centralną lokacją administracyjną, lokacja główna ponowi próbę nawiązania połączenia po upływie czasu określonego (w minutach) dla opcji CASRetryInterval.


-   **Nazwa klucza:** WaitForCASTimeout

    -   **Wymagane:** Nie
    -   **Wartości:** &lt;*Limit czasu*>
    -   **Szczegóły:** Określa maksymalną wartość limitu czasu (w minutach) dla lokacji głównej połączyć się z witryną Administracja centralna. Jeśli na przykład nie uda się nawiązać połączenia między lokacją główną a centralną lokacją administracyjną, lokacja główna ponowi próbę połączenia z centralną lokacją administracyjną na podstawie wartości CASRetryInterval przed upływem czasu określonego w opcji WaitForCASTimeout. Możesz określić wartość z zakresu od 0 do 100.
