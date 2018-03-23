---
title: Nienadzorowane odzyskiwanie
titleSuffix: Configuration Manager
description: Odzyskiwanie lokacji w programie System Center Configuration Manager za pomocą skryptu.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 828c31d1-3d70-4412-b1a8-c92e7e504d39
caps.latest.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: fc6325d00e048fbbf54d740a89f78070fac6b0cb
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="unattended-site-recovery-for-configuration-manager"></a>Nienadzorowane odzyskiwanie lokacji programu Configuration Manager   

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

 Aby wykonać [nienadzorowane odzyskiwanie](/sccm/protect/understand/recover-sites#site-recovery-procedures) programu Configuration Manager centralnej lokacji administracyjnej lub lokacji głównej, można utworzyć skrypt instalacji nienadzorowanej, a następnie użyć Instalatora z **/script** polecenia Opcja. Skrypt zawiera ten sam rodzaj informacji, które monituje Kreator instalacji, z tą różnicą, że nie ma żadnych ustawień domyślnej. Należy określić wszystkie wartości kluczy instalacji mających zastosowanie do używanego typu odzyskiwania.

 Aby użyć opcji wiersza polecenia Instalatora/Script, należy utworzyć plik inicjujący. Następnie należy określić nazwę pliku po opcji/Script. Nazwa pliku jest bez znaczenia, jak długo ma **.ini** rozszerzenia nazwy pliku. Podając odniesienie do pliku inicjowania Instalatora w wierszu polecenia, należy wprowadzić pełną ścieżkę do pliku. Na przykład, jeśli plik inicjujący Instalatora nosi nazwę *setup.ini*, i jest on przechowywany w *folderze C:\setup*, będzie wierszu polecenia:

 `setup /script c:\setup\setup.ini`

> [!IMPORTANT]  
>  Musi mieć prawa administratora, aby uruchomić Instalatora. Po uruchomieniu Instalatora ze skryptem instalacji nienadzorowanej Uruchom wiersz polecenia z uprawnieniami administratora przy użyciu **Uruchom jako administrator**.

 Skrypt zawiera nazwy sekcji i kluczy oraz wartości. Wymagane nazwy kluczy sekcji różnią się w zależności od typu odzyskiwania, którego skrypt jest wykonywany. Kolejność kluczy w sekcjach oraz kolejność sekcji w pliku nie mają znaczenia. W kluczach nie jest rozróżniana wielkość liter. Podając wartości kluczy, należy pamiętać, że po nazwie klucza należy wprowadzić znak równości (=), a następnie jego wartość.

 Poniższe sekcje zawierają informacje pomocne w tworzeniu skryptu nienadzorowanego odzyskiwania lokacji. Tabele zawierają listę dostępnych kluczy skryptu instalacji, ich wartości, informację, czy dany klucz jest wymagany, typ instalacji, do której klucz skryptu jest używany, oraz krótki opis klucza.

## <a name="recover-a-central-administration-site-unattended"></a>Odzyskiwanie nienadzorowane centralnej lokacji administracyjnej
 Skorzystaj z poniższych informacji, aby skonfigurować plik skryptu instalacji nienadzorowanej, aby odzyskać lokację administracji centralnej.

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
    -   **Szczegóły:** Określa, czy Instalator odzyskuje serwer lokacji i programu SQL Server. Skojarzone klucze są wymagane podczas ustawiania poniższej wartości dla ustawienia ServerRecoveryOptions:  
        -   **Wartość = 1** Możesz określić wartość dla klucza **SiteServerBackupLocation** , aby odzyskiwać lokację przy użyciu kopii zapasowej lokacji. Jeżeli nie określisz wartości, lokacja zostanie ponownie zainstalowana bez przywracania jej z zestawu kopii zapasowych.

             Klucz **BackupLocation** jest wymagany w przypadku skonfigurowania dla klucza **DatabaseRecoveryOptions** wartości **10** , która umożliwia przywracanie bazy danych lokacji z kopii zapasowej.

        -   **Wartość = 2** Możesz określić wartość dla klucza **SiteServerBackupLocation** , aby odzyskać lokację przy użyciu kopii zapasowej lokacji. Jeżeli nie określisz wartości, lokacja zostanie ponownie zainstalowana bez przywracania jej z zestawu kopii zapasowych.

        -   **Wartość = 4** Klucz **BackupLocation** jest wymagany w przypadku skonfigurowania wartości **10** dla klucza **DatabaseRecoveryOptions** , co oznacza przywrócenie bazy danych lokacji z kopii zapasowej.

-   **Nazwa klucza:** DatabaseRecoveryOptions

    -   **Wymagane:** Być może
    -   **Wartości:**   
         - **10** = Przywracanie bazy danych lokacji z kopii zapasowej.  
         - **20** = Użyj bazy danych lokacji, która została ręcznie odzyskana przy użyciu innej metody.   
         - **40** = Tworzenie nowej bazy danych lokacji. Użyj tej opcji, gdy nie ma dostępnej kopii zapasowej bazy danych lokacji. Odzyskiwanie danych globalnych i danych lokacji przebiega przy użyciu replikacji z innych lokacji.  
         - **80** = pomijanie odzyskiwania bazy danych.
    -   **Szczegóły:** Określa sposób odzyskiwania bazy danych lokacji w programie SQL Server. Ten klucz jest wymagany, gdy ustawienie **ServerRecoveryOptions** ma wartość **1** lub **4**.


-   **Nazwa klucza:** ReferenceSite  

    -   **Wymagane:** Być może
    -   **Wartości:** &lt;ReferenceSiteFQDN\>
    -   **Szczegóły:** Określa lokację główną odniesienia. Jeśli kopia zapasowa bazy danych jest starsza od okresu przechowywania śledzenia zmian lub odzyskiwania lokacji bez kopii zapasowej, centralna lokacja administracyjna użyje lokacji odniesienia do odzyskiwania danych globalnych.

         Jeśli nie określono lokacji odniesienia, a tworzenie kopii zapasowej jest starsza od okresu przechowywania śledzenia zmian, wszystkie lokacje główne zostaną zainicjowane ponownie przy użyciu danych przywróconych z centralnej lokacji administracyjnej.

         Jeśli nie określono lokacji odniesienia, a kopia zapasowa pochodzi okresu przechowywania śledzenia zmian, jedynie zmian wprowadzonych po wykonaniu kopii zapasowej są replikowane w lokacjach głównych. W przypadku wystąpienia konfliktu między zmianami z różnych lokacji głównych centralna lokacja administracyjna użyje danych otrzymanych w pierwszej kolejności.

         Ten klucz jest wymagany, gdy ustawienie **DatabaseRecoveryOptions** ma wartość **40**.

-   **Nazwa klucza:** SiteServerBackupLocation

    -   **Wymagane:** Nie
    -   **Wartości:** &lt;PathToSiteServerBackupSet\>
    -   **Szczegóły:** Określa ścieżkę do zestawu kopii zapasowych serwera lokacji. Ten klucz jest opcjonalny, gdy ustawienie **ServerRecoveryOptions** ma wartość **1** lub **2**. Określ wartość dla klucza **SiteServerBackupLocation** , aby odzyskiwać lokację przy użyciu kopii zapasowej lokacji. Jeżeli nie określisz wartości, lokacja zostanie ponownie zainstalowana bez przywracania jej z zestawu kopii zapasowych.


-   **Nazwa klucza:** BackupLocation

    -   **Wymagane:** Być może
    -   **Wartości:** &lt;PathToSiteDatabaseBackupSet\>
    -   **Szczegóły:** Określa ścieżkę do zestawu kopii zapasowych bazy danych lokacji. Klucz **BackupLocation** jest wymagany w przypadku skonfigurowania dla klucza **ServerRecoveryOptions** wartości **1** lub **4** , a dla klucza **DatabaseRecoveryOptions** wartości **10** .


**Opcje**

-   **Nazwa klucza:** Identyfikator produktu
    -   **Wymagane:** Tak
    -   **Wartości:**   
         - xxxxx-xxxxx-xxxxx-xxxxx-xxxxx  
         - Eval
    -   **Szczegóły:** Menedżer konfiguracji instalacji klucz produktu, wraz z kreskami. Wprowadź **Eval** można zainstalować wersję ewaluacyjną programu Configuration Manager.  


-   **Nazwa klucza:** SiteCode

    -   **Wymagane:** Tak
    -   **Wartości:** &lt;Kod lokacji\>
    -   **Szczegóły:** Trzy znaki alfanumeryczne, które jednoznacznie identyfikują lokację w hierarchii. Określ kod lokacji, który był używany przez lokację przed awarią.


-   **Nazwa klucza:** SiteName

    -   **Wymagane:** Tak
    -   **Wartości:** SiteName
    -   **Szczegóły:** Opis dla tej lokacji.


-   **Nazwa klucza:** SMSInstallDir

    -   **Wymagane:** Tak
    -   **Wartości:** &lt;*ConfigMgrInstallationPath*>
    -   **Szczegóły:** Określa folder instalacji plików programu Configuration Manager.
        > [!NOTE]   
        >  Możesz określić oryginalną lub nową ścieżkę do użycia na potrzeby instalacji programu Configuration Manager.

-   **Nazwa klucza:** SDKServer

    -   **Wymagane:** Tak
    -   **Wartości:** &lt;*Nazwa FQDN dostawcy programu SMS*>
    -   **Szczegóły:** Określa nazwę FQDN serwera obsługującego dostawcę programu SMS. Określ serwer, który hostował dostawcę programu SMS przed awarią.

         Po instalacji początkowej możesz skonfigurować dodatkowych dostawców programu SMS dla lokacji.

-   **Nazwa klucza:** PrerequisiteComp

    -   **Wymagane:** Tak
    -   **Wartości:** 0 lub 1  
         0 = pobieranie   
         1 = już pobrane
    -   **Szczegóły:** Określa, czy pliki wymagań wstępnych Instalatora zostały już pobrane. Na przykład wybierzesz wartość 0, Instalator pobierze pliki.  


-   **Nazwa klucza:** PrerequisitePath

    -   **Wymagane:** Tak
    -   **Wartości:** &lt;*PathToSetupPrerequisiteFiles*>
    -   **Szczegóły:** Określa ścieżkę do plików wymagań wstępnych Instalatora. W zależności od **PrerequisiteComp** Instalator używa tej ścieżki do przechowywania pobranych plików lub lokalizowania wcześniej pobranych plików.

-   **Nazwa klucza:** AdminConsole

    -   **Wymagane:** Być może
    -   **Wartości:** 0 lub 1 0 = nie instaluj   
         1 = zainstaluj
    -   **Szczegóły:** Określa, czy instalować konsolę programu Configuration Manager. Ten klucz jest wymagany, chyba że ustawienie **ServerRecoveryOptions** ma wartość **4**.


-   **Nazwa klucza:** JoinCEIP   
    > [!Note]  
    > Począwszy od programu Configuration Manager w wersji 1802 funkcję programu CEIP zostanie usunięte z produktu.

    -   **Wymagane:** Tak
    -   **Wartości:** 0 lub 1  
         0 = nie dołączaj  
         1 = dołącz
    -   **Szczegóły:** Określa, czy dołączyć do programu poprawy jakości obsługi klienta.

**SQLConfigOptions**

-   **Nazwa klucza:** SQLServerName

    -   **Wymagane:** Tak
    -   **Wartości:** *&lt;SQLServerName\>*
    -   **Szczegóły:** Nazwa serwera lub nazwa wystąpienia klastrowego z programem SQL Server, który udostępnia bazę danych. Określ serwer, który hostował bazę danych lokacji przed awarią.


-   **Nazwa klucza:** DatabaseName

    -   **Wymagane:** Tak
    -   **Wartości:** *&lt;Nazwa_bazy_danych_lokacji\>*  lub  *&lt;InstanceName\>*\\*&lt;Nazwa_bazy_danych_lokacji\>*
    -   **Szczegóły:** Nazwa bazy danych programu SQL Server do utworzenia lub używania w celu zainstalowania bazy danych witryny Administracja centralna. Określ nazwę bazy danych, który był używany przed awarią.

        > [!IMPORTANT]  
        >  Jeśli nie używasz domyślnego wystąpienia, należy określić nazwę wystąpienia i nazwę bazy danych lokacji.

-   **Nazwa klucza:** SQLSSBPort

    -   **Wymagane:** Nie
    -   **Wartości:** &lt;*Numer_portu_usługi_ssb*>
    -   **Szczegóły:** Określ port usługi SQL Server Service Broker (SSB) używany przez program SQL Server. Zazwyczaj port SSB jest skonfigurowany tak, aby używał portu TCP 4022, ale są obsługiwane również inne porty. Należy określić ten sam port SBB, który był używany przed awarią.

## <a name="recover-a-primary-site-unattended"></a>Odzyskiwanie nienadzorowane lokacji głównej
 Skorzystaj z poniższych informacji, aby skonfigurować plik skryptu instalacji nienadzorowanej, aby odzyskać lokację administracji centralnej.

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
    -   **Szczegóły:** Określa, czy Instalator odzyskuje serwer lokacji i programu SQL Server. Skojarzone klucze są wymagane podczas ustawiania poniższej wartości dla ustawienia ServerRecoveryOptions:

        -   **Wartość = 1** Możesz określić wartość dla klucza **SiteServerBackupLocation** , aby odzyskiwać lokację przy użyciu kopii zapasowej lokacji. Jeżeli nie określisz wartości, lokacja zostanie ponownie zainstalowana bez przywracania jej z zestawu kopii zapasowych.

             Klucz **BackupLocation** jest wymagany w przypadku skonfigurowania dla klucza **DatabaseRecoveryOptions** wartości **10** , która umożliwia przywracanie bazy danych lokacji z kopii zapasowej.

        -   **Wartość = 2** Możesz określić wartość dla klucza **SiteServerBackupLocation** , aby odzyskać lokację przy użyciu kopii zapasowej lokacji. Jeżeli nie określisz wartości, lokacja zostanie ponownie zainstalowana bez przywracania jej z zestawu kopii zapasowych.

        -   **Wartość = 4** Klucz **BackupLocation** jest wymagany w przypadku skonfigurowania wartości **10** dla klucza **DatabaseRecoveryOptions** , co oznacza przywrócenie bazy danych lokacji z kopii zapasowej.

-   **Nazwa klucza:** DatabaseRecoveryOptions

    -   **Wymagane:** Być może
    -   **Wartości:**   
         - **10** = Przywracanie bazy danych lokacji z kopii zapasowej.  
         - **20** = Użyj bazy danych lokacji, która została ręcznie odzyskana przy użyciu innej metody.     
         - **40** = Tworzenie nowej bazy danych lokacji. Użyj tej opcji, gdy nie ma dostępnej kopii zapasowej bazy danych lokacji. Odzyskiwanie danych globalnych i danych lokacji przebiega przy użyciu replikacji z innych lokacji.  
         - **80** = pomijanie odzyskiwania bazy danych.
    -   **Szczegóły:** Określa sposób odzyskiwania bazy danych lokacji w programie SQL Server. Ten klucz jest wymagany, gdy ustawienie **ServerRecoveryOptions** ma wartość **1** lub **4**.


-   **Nazwa klucza:** SiteServerBackupLocation

    -   **Wymagane:** Nie
    -   **Wartości:** &lt;PathToSiteServerBackupSet\>
    -   **Szczegóły:** Określa ścieżkę do zestawu kopii zapasowych serwera lokacji. Ten klucz jest opcjonalny, gdy ustawienie **ServerRecoveryOptions** ma wartość **1** lub **2**. Określ wartość dla klucza **SiteServerBackupLocation** , aby odzyskiwać lokację przy użyciu kopii zapasowej lokacji. Jeżeli nie określisz wartości, lokacja zostanie ponownie zainstalowana bez przywracania jej z zestawu kopii zapasowych.     


-   **Nazwa klucza:** BackupLocation

    -   **Wymagane:** Być może
    -   **Wartości:** &lt;PathToSiteDatabaseBackupSet\>
    -   **Szczegóły:** Określa ścieżkę do zestawu kopii zapasowych bazy danych lokacji. Klucz **BackupLocation** jest wymagany w przypadku skonfigurowania dla klucza **ServerRecoveryOptions** wartości **1** lub **4** , a dla klucza **DatabaseRecoveryOptions** wartości **10** .

**Opcje**

-   **Nazwa klucza:** Identyfikator produktu

    -   **Wymagane:** Tak
    -   **Wartości:**     
         - xxxxx-xxxxx-xxxxx-xxxxx-xxxxx  
         - Eval     
    -   **Szczegóły:** Menedżer konfiguracji instalacji klucz produktu, wraz z kreskami. Wprowadź **Eval** można zainstalować wersję ewaluacyjną programu Configuration Manager.  


-   **Nazwa klucza:** SiteCode

    -   **Wymagane:** Tak
    -   **Wartości:** &lt;Kod lokacji\>
    -   **Szczegóły:** Trzy znaki alfanumeryczne, które jednoznacznie identyfikują lokację w hierarchii. Określ kod lokacji, który był używany przez lokację przed awarią.


-   **Nazwa klucza:** SiteName

    -   **Wymagane:** Tak
    -   **Wartości:** SiteName
    -   **Szczegóły:** Opis dla tej lokacji.


-   **Nazwa klucza:** SMSInstallDir

    -   **Wymagane:** Tak
    -   **Wartości:** &lt;*ConfigMgrInstallationPath*>
    -   **Szczegóły:** Określa folder instalacji plików programu Configuration Manager.

        > [!NOTE]   
        >  Możesz określić oryginalną lub nową ścieżkę do użycia na potrzeby instalacji programu Configuration Manager.

-   **Nazwa klucza:** SDKServer

    -   **Wymagane:** Tak
    -   **Wartości:** &lt;*Nazwa FQDN dostawcy programu SMS*>
    -   **Szczegóły:** Określa nazwę FQDN serwera obsługującego dostawcę programu SMS. Określ serwer, który hostował dostawcę programu SMS przed awarią.

         Po instalacji początkowej możesz skonfigurować dodatkowych dostawców programu SMS dla lokacji.

-   **Nazwa klucza:** PrerequisiteComp

    -   **Wymagane:** Tak
    -   **Wartości:** 0 lub 1    
         0 = pobieranie   
         1 = już pobrane   
    -   **Szczegóły:** Określa, czy pliki wymagań wstępnych Instalatora zostały już pobrane. Na przykład wybierzesz wartość 0, Instalator pobierze pliki.


-   **Nazwa klucza:** PrerequisitePath

    -   **Wymagane:** Tak
    -   **Wartości:** &lt;*PathToSetupPrerequisiteFiles*>
    -   **Szczegóły:** Określa ścieżkę do plików wymagań wstępnych Instalatora. W zależności od **PrerequisiteComp** Instalator używa tej ścieżki do przechowywania pobranych plików lub lokalizowania wcześniej pobranych plików.


-   **Nazwa klucza:** AdminConsole

    -   **Wymagane:** Być może
    -   **Wartości:** 0 lub 1  
         0 = nie instaluj   
         1 = zainstaluj  
    -   **Szczegóły:** Określa, czy instalować konsolę programu Configuration Manager. Ten klucz jest wymagany, chyba że ustawienie **ServerRecoveryOptions** ma wartość **4**.

-   **Nazwa klucza:** JoinCEIP  
    > [!Note]  
    > Począwszy od programu Configuration Manager w wersji 1802 funkcję programu CEIP zostanie usunięte z produktu.

    -   **Wymagane:** Tak
    -   **Wartości:** 0 lub 1    
         0 = nie dołączaj  
         1 = dołącz
    -   **Szczegóły:** Określa, czy dołączyć do programu poprawy jakości obsługi klienta.


**SQLConfigOptions**

-   **Nazwa klucza:** SQLServerName

    -   **Wymagane:** Tak
    -   **Wartości:** *&lt;SQLServerName\>*
    -   **Szczegóły:** Nazwa serwera lub nazwa wystąpienia klastrowego z programem SQL Server, który udostępnia bazę danych. Określ serwer, który hostował bazę danych lokacji przed awarią.


-   **Nazwa klucza:** DatabaseName

    -   **Wymagane:** Tak
    -   **Wartości:** *&lt;Nazwa_bazy_danych_lokacji\>*  lub  *&lt;InstanceName\>*\\*&lt;Nazwa_bazy_danych_lokacji\>*
    -   **Szczegóły:** Nazwa bazy danych programu SQL Server do utworzenia lub używania w celu zainstalowania bazy danych witryny Administracja centralna. Określ nazwę bazy danych, który był używany przed awarią.

        > [!IMPORTANT]    
        >  Jeśli nie używasz domyślnego wystąpienia, należy określić nazwę wystąpienia i nazwę bazy danych lokacji.

-   **Nazwa klucza:** SQLSSBPort

    -   **Wymagane:** Nie
    -   **Wartości:** &lt;*Numer_portu_usługi_ssb*>
    -   **Szczegóły:** Określ port usługi SQL Server Service Broker (SSB) używany przez program SQL Server. Zazwyczaj port SSB jest skonfigurowany tak, aby używał portu TCP 4022, ale są obsługiwane również inne porty. Należy określić ten sam port SBB, który był używany przed awarią.

**Opcja rozszerzenia hierarchii**

-   **Nazwa klucza:** CCARSiteServer

    -   **Wymagane:** Być może
    -   **Wartości:** &lt;*SiteCodeForCentralAdministrationSite*>
    -   **Szczegóły:** Określa lokację administracji centralnej, z którą połączy się lokacja główna się po dołączeniu do hierarchii programu Configuration Manager. To ustawienie jest wymagane, jeśli lokacja główna była połączona z centralną lokacją administracyjną przed awarią. Określ kod lokacji, która była używana w centralnej lokacji administracyjnej przed awarią.

-   **Nazwa klucza:** CASRetryInterval

    -   **Wymagane:** Nie
    -   **Wartości:** &lt;*Interval*>
    -   **Szczegóły:** Określa interwał ponawiania prób (w minutach) prób połączenia z lokacją administracji centralnej po niepowodzeniu. Na przykład jeśli nie może nawiązać połączenia z lokacją administracji centralnej, lokacji głównej oczekuje liczbę minut, przez które dla opcji CASRetryInterval, a następnie reattempts połączenia.


-   **Nazwa klucza:** WaitForCASTimeout

    -   **Wymagane:** Nie
    -   **Wartości:** &lt;*Limit czasu*>
    -   **Szczegóły:** Określa maksymalną wartość limitu czasu (w minutach) dla lokacji głównej połączyć się z witryną Administracja centralna. Jeśli na przykład nie uda się nawiązać połączenia między lokacją główną a centralną lokacją administracyjną, lokacja główna ponowi próbę połączenia z centralną lokacją administracyjną na podstawie wartości CASRetryInterval przed upływem czasu określonego w opcji WaitForCASTimeout. Możesz określić wartość z zakresu od 0 do 100.
