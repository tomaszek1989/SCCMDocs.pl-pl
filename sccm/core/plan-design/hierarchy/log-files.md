---
title: Pliki dziennika programu Configuration Manager | Dokumentacja firmy Microsoft
description: "Pliki dziennika umożliwia rozwiązywanie problemów w hierarchii programu System Center Configuration Manager."
ms.custom: na
ms.date: 3/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c1ff371e-b0ad-4048-aeda-02a9ff08889e
caps.latest.revision: 9
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: b991b4ea27e66c233b04f8e65a412404521d89a6
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="log-files-in-system-center-configuration-manager"></a>Pliki dziennika w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

W System Center Configuration Manager składniki serwera klienta i lokacji rejestrują informacje o procesach w osobnych plikach dziennika. Aby rozwiązać problemy, które mogą wystąpić w hierarchii programu Configuration Manager służy informacji w plikach dziennika. Domyślnie rejestrowanie przez składnik klienta i serwera jest włączone w programie Configuration Manager.   

 Poniższe sekcje zawierają szczegółowe informacje o różnych plikach dziennika dostępny dla użytkownika. Aby zidentyfikować błąd informacje, które mogą ułatwić rozwiązywanie problemów i szczegółów działania służą te informacje umożliwiają wyświetlenie i monitorowanie klienta programu Configuration Manager i dzienniki serwera.  

-   [Informacje o plikach dziennika programu Configuration Manager](#BKMK_AboutLogs)  

    -   [Konfigurowanie opcji rejestrowania przy użyciu Menedżera usług programu Configuration Manager](#BKMK_LogOptions)  

    -   [Lokalizowanie dzienników programu Configuration Manager](#BKMK_LogLocation)  

-   [Dzienniki klienta programu Configuration Manager](#BKMK_ClientLogs)  

    -   [Operacje klienta](#BKMK_ClientOpLogs)  

    -   [Pliki dziennika instalacji klienta](#BKMK_ClientInstallLog)  

    -   [Klient dla systemu Linux i UNIX](#BKMK_LogFilesforLnU)  

    -   [Klient dla komputerów Mac](#BKMK_LogfilesforMac)  

-   [Pliki dziennika serwera lokacji programu Configuration Manager](#BKMK_ServerLogs)  

    -   [Serwera i witryny dzienniki systemu lokacji serwera](#BKMK_SiteSiteServerLog)  

    -   [Pliki dziennika instalacji serwera lokacji](#BKMK_SiteInstallLog)  

    -   [Pliki dziennika punktu stanu powrotu](#BKMK_FSPLog)  

    -   [Pliki dziennika punktu zarządzania](#BKMK_MPLog)  

    -   [Pliki dziennika punktu aktualizacji oprogramowania](#BKMK_SUPLog)  

-   [Pliki dziennika dotyczące funkcji programu Configuration Manager](#BKMK_FunctionLogs)  

    -   [Zarządzanie aplikacjami](#BKMK_AppManageLog)  

    -   [Analiza zasobów](#BKMK_AILog)  

    -   [Kopia zapasowa i odzyskiwanie](#BKMK_BnRLog)  

    -   [Rejestracja certyfikatów](#BKMK_CertificateEnrollment)

    -   [Powiadomienie klienta](#BKMK_BGB)

    -   [Brama zarządzania chmury](#cloud-management-gateway)

    -   [Ustawienia zgodności i dostęp do zasobów firmy](#BKMK_CompSettingsLog)  

    -   [Konsola programu Configuration Manager](#BKMK_ConsoleLog)  

    -   [Zarządzanie zawartością](#BKMK_ContentLog)  

    -   [Odnajdywanie](#BKMK_DiscoveryLog)  

    -   [Endpoint Protection](#BKMK_EPLog)  

    -   [Rozszerzenia](#BKMK_Extensions)  

    -   [Spis](#BKMK_InventoryLog)  

    -   [Pomiaru](#BKMK_MeteringLog)  

    -   [Migracja](#BKMK_MigrationLog)  

    -   [Urządzenia przenośne](#BKMK_MDMLog)  

    -   [Wdrożenie systemu operacyjnego](#BKMK_OSDLog)  

    -   [Zarządzanie energią](#BKMK_PowerMgmtLog)  

    -   [Zdalne sterowanie](#BKMK_RCLog)  

    -   [Raportowanie](#BKMK_ReportLog)  

    -   [Administracja oparta na rolach](#BKMK_RBALog)  

    -   [Punkt połączenia usługi](#BKMK_WITLog)  

    -   [Aktualizacje oprogramowania](#BKMK_SU_NAPLog)  

    -   [Funkcji Wake On LAN](#BKMK_WOLLog)  

    -   [Obsługa systemu Windows 10](#BKMK_WindowsServicingLog)

    -   [Usługa Windows Update Agent](#BKMK_WULog)  

    -   [Serwer WSUS](#BKMK_WSUSLog)  

##  <a name="BKMK_AboutLogs"></a>Informacje o plikach dziennika programu Configuration Manager  
 Większość procesów w programie Configuration Manager zapisuje informacje o działaniu do pliku dziennika dedykowanego dla tego procesu. Pliki dziennika są identyfikowane przez **log** lub **Lo_** pliku rozszerzenia. Configuration Manager zapisuje do pliku log, dopóki nie osiągnie maksymalny rozmiar. Po zapełnieniu dziennika zawartość pliku log jest kopiowana do pliku o tej samej nazwie, ale z rozszerzeniem Lo_, a proces lub składnik kontynuuje zapis do pliku log. Gdy plik log ponownie osiągnie maksymalny rozmiar, plik Lo_ jest zastępowany i proces powtarza się. Niektóre składniki tworzą historię pliku dziennika, dodając datę i sygnaturę czasową do nazwy pliku dziennika i zachowując rozszerzenie log. Wyjątek maksymalnego rozmiaru i korzystania z pliku Lo_ jest klient dla systemu Linux i UNIX. Informacje o używaniu plików dziennika klienta dla systemu Linux i UNIX znajdują się w temacie [zarządzanie plikami dziennika klienta dla systemu Linux i UNIX](#BKMK_ManageLinuxLogs) w tym temacie.  

 Aby wyświetlić dzienniki, użyj narzędzie podglądu dziennika programu Configuration Manager CMTrace, znajduje się w \\SMSSetup\\folder Narzędzia z nośnika źródłowego programu Configuration Manager. Narzędzie CMTrace jest dodawane do wszystkich obrazów rozruchowych, które są dodawane do biblioteki oprogramowania.  

###  <a name="BKMK_LogOptions"></a>Konfigurowanie opcji rejestrowania przy użyciu Menedżera usług programu Configuration Manager  
 W programie Configuration Manager można zmienić gdzie są przechowywane pliki dziennika i można zmienić rozmiar pliku dziennika.  

 Aby zmodyfikować rozmiaru plików dziennika, Zmień nazwę i lokalizację pliku dziennika lub wymusić wielu składników do zapisu w jednym pliku dziennika, wykonaj następujące kroki.  

#### <a name="to-modify-logging-for-a-component"></a>Aby zmienić sposób rejestrowania składnika  

1.  W konsoli programu Configuration Manager wybierz **monitorowanie**, wybierz opcję **stan systemu**, a następnie wybierz opcję **stan lokacji** lub **stan składnika**.  
2.  Na **Home** w karcie **składnika** grupy wybierz **Start**, a następnie wybierz **usług programu Configuration Manager**.  
3.  Po otwarciu Menedżera usług programu Configuration Manager, należy nawiązać lokację, którą chcesz zarządzać. Jeśli lokację, którą chcesz zarządzać, nie jest wyświetlane, wybierz pozycję **witryny**, wybierz opcję **Connect**, a następnie wprowadź nazwę serwera lokacji dla odpowiedniej lokacji.  
4.  Rozwiń lokację i przejdź do **składniki** lub **serwerów**, w zależności od lokalizacji składników, którymi chcesz zarządzać.  
5.  W prawym okienku wybierz jeden lub więcej składników.  
6.  Na **składnika** menu, wybierz opcję **rejestrowanie**.  
7.  W oknie dialogowym **Rejestrowanie składników programu Configuration Manager** uzupełnij dostępne opcje konfiguracji dla wybranego elementu.  
8.  Wybierz **OK** Aby zapisać konfigurację.  

###  <a name="BKMK_LogLocation"></a>Znajdź dzienników programu Configuration Manager  
Pliki dziennika programu Configuration Manager są przechowywane w różnych lokalizacjach, które zależą od procesu tworzącego plik dziennika i konfiguracji systemów lokacji. Lokalizacja dziennika na komputerze może się różnić, użyj funkcji wyszukiwania, aby znaleźć odpowiednich plików dziennika na komputerach programu Configuration Manager, w razie potrzeby rozwiązywać danego scenariusza.  

##  <a name="BKMK_ClientLogs"></a>Dzienniki klienta programu Configuration Manager  
Poniższe sekcje listę plików dziennika związanych z operacjami i instalacją klienta.  

###  <a name="BKMK_ClientOpLogs"></a>Operacje klienta  
Poniższa tabela zawiera listę plików dziennika, znajdującego się na kliencie programu Configuration Manager.  

|Nazwa dziennika|Opis|  
|--------------|-----------------|  
|CAS.log|Usługa dostępu do zawartości. Obsługuje lokalną pamięć podręczną pakietów na kliencie.|  
|Ccm32BitLauncher.log|Rejestruje akcje uruchamiania aplikacji na kliencie oznaczone jako "Uruchom jako 32-bitowe".|  
|CcmEval.log|Rejestruje działania oceny stanu klienta programu Configuration Manager i szczegóły dla składników wymaganych przez klienta programu Configuration Manager.|  
|CcmEvalTask.log|Rejestruje działania oceny stanu klienta programu Configuration Manager, które są inicjowane przez zaplanowane zadanie oceny.|  
|CcmExec.log|Rejestruje działania klienta i usługi Host agenta programu SMS. Ten plik dziennika zawiera także informacje o włączaniu i wyłączaniu serwera proxy wznawiania.|  
|CcmMessaging.log|Rejestruje działania dotyczące komunikacji między klientem i zarządzania punktów.|  
|CCMNotificationAgent.log|Rejestruje działania związane z operacjami powiadamiania klienta.|  
|Ccmperf.log|Rejestruje działania powiązane z obsługą i przechwytywaniem danych dotyczących liczników wydajności klienta.|  
|CcmRestart.log|Rejestruje działanie ponownego uruchomienia usługi klienta.|  
|CCMSDKProvider.log|Rejestruje działania dla interfejsów zestawu SDK klienta.|  
|CertificateMaintenance.log|Obsługuje certyfikaty dla usług domenowych w usłudze Active Directory i punktach zarządzania.|  
|CIDownloader.log|Rejestruje szczegółowe informacje o pobraniach definicji elementu konfiguracji.|  
|CITaskMgr.log|Rejestruje zadania, które są inicjowane dla każdej aplikacji i typu wdrożenia, takich jak zawartość pobrać i zainstalować lub odinstalować akcje.|  
|ClientAuth.log|Rejestruje podpisywania i działania uwierzytelniania dla klienta.|  
|ClientIDManagerStartup.log|Tworzy i obsługuje identyfikator GUID klienta oraz identyfikuje zadania wykonywane podczas rejestracji i przypisywania klienta.|  
|ClientLocation.log|Rejestruje zadania związane z przypisaniem lokacji klienta.|  
|CMHttpsReadiness.log|Rejestruje wyniki działania narzędzie oceny gotowości protokołu HTTPS Menedżera konfiguracji. To narzędzie sprawdza, czy komputery mają certyfikat uwierzytelniania klienta infrastruktury kluczy publicznych (PKI), który może służyć za pomocą programu Configuration Manager.|  
|CmRcService.log|Rejestruje informacje dla usługi zdalnego sterowania.|  
|ContentTransferManager.log|Określa harmonogram usługi inteligentnego transferu w tle (BITS) lub blok komunikatów serwera (SMB) do pobrania lub dostępu do pakietów.|  
|DataTransferService.log|Rejestruje całą komunikację usługi BITS dotyczącą zasad lub dostępu do pakietów.|  
|EndpointProtectionAgent|Rejestruje informacje o instalacji klienta programu System Center Endpoint Protection i zastosowania zasad ochrony przed złośliwym kodem na tym kliencie.|  
|execmgr.log|Rejestruje szczegółowe informacje o pakietach i sekwencjach zadań uruchamianych na kliencie.|  
|ExpressionSolver.log|Rejestruje szczegółowe informacje o ulepszonych metodach wykrywania używanych po włączeniu pełnego rejestrowania lub rejestrowania związanego z debugowaniem jest włączona.|  
|ExternalEventAgent.log|Rejestruje historię wykrywania złośliwego oprogramowania przez program Endpoint Protection i zdarzenia związane ze stanem klienta.|  
|FileBITS.log|Rejestruje wszystkie zadania dostępu do pakietu SMB.|  
|FileSystemFile.log|Rejestruje działania dostawcy Instrumentacji zarządzania Windows (WMI) dla spisu oprogramowania i zbierania plików.|  
|FSPStateMessage.log|Rejestruje działania dotyczące komunikatów o stanie wysyłane przez klienta do rezerwowego punkt stanu.|  
|InternetProxy.log|Rejestruje działania konfiguracji i używania serwera proxy sieci dla klienta.|  
|InventoryAgent.log|Rejestruje działania ewidencji zapasów sprzętu, ewidencji zapasów oprogramowania i akcje odnajdywania pulsu na kliencie.|  
|LocationCache.log|Rejestruje działania dotyczące użycia pamięci podręcznej lokalizacji i obsługi klienta.|  
|LocationServices.log|Rejestruje działania klienta dotyczące lokalizowania punktów zarządzania, punktów aktualizacji oprogramowania i punktów dystrybucji.|  
|MaintenanceCoordinator.log|Rejestruje działania zadań obsługi ogólne dla klienta.|  
|Mifprovider.log|Rejestruje działania dostawcy WMI dla plików formatu MIF (Management Information).|  
|mtrmgr.log|Monitoruje wszystkie procesy pomiarów użytkowania oprogramowania.|  
|PolicyAgent.log|Rejestruje żądania zasad wysłane za pomocą usługi transferu danych.|  
|PolicyAgentProvider.log|Rejestruje zmiany zasad.|  
|PolicyEvaluator.log|Rejestruje szczegółowe informacje o ocenie zasad na komputerach klienckich, w tym zasad z aktualizacji oprogramowania.|  
|PolicyPlatformClient.log|Rejestruje proces korygowania i zgodności dla wszystkich dostawców znajdujących się w \Program Files\Microsoft Policy Platform z wyjątkiem dostawcy plików.|  
|PolicySdk.log|Rejestruje działania dla interfejsów zestawu SDK systemu zasad.|  
|Pwrmgmt.log|Rejestruje informacje o włączeniu lub wyłączeniu ustawień klienta serwera proxy wznawiania.|  
|PwrProvider.log|Rejestruje działania dostawcy zarządzania energią (PWRInvProvider) hostowanego w usłudze WMI. We wszystkich obsługiwanych wersjach systemu Windows dostawca wylicza bieżące ustawienia na komputerach podczas tworzenia spisu sprzętu i stosuje ustawienia planu zasilania.|  
|SCClient_&lt;*domain*\>@&lt;*username*\>_1.log|Rejestruje działanie w Centrum oprogramowania dla określonego użytkownika na komputerze klienckim.|  
|SCClient_&lt;*domain*\>@&lt;*username*\>_2.log|Rejestruje historyczne działanie w Centrum oprogramowania dla określonego użytkownika na komputerze klienckim.|  
|Scheduler.log|Rejestruje działania zaplanowanych zadań dla wszystkich operacji klienta.|  
|SCNotify_&lt;*domain*\>@&lt;*username*\>_1.log|Rejestruje działanie powiadamiania użytkowników dla określonego użytkownika.|  
|SCNotify_&lt;*domain*\>@&lt;*username*\>_1-&lt;*date_time*>.log|Rejestruje informacje historyczne dotyczące powiadamiania użytkowników dla określonego użytkownika.|  
|setuppolicyevaluator.log|Rejestruje konfigurację i tworzenie zasad magazynu w usłudze WMI.|  
|SleepAgent_&lt;*domeny*\>@SYSTEM_0.log|Główny plik dziennika dla serwera proxy wznawiania.|  
|smscliui.log|Rejestruje użycie klienta programu Configuration Manager w Panelu sterowania.|  
|SrcUpdateMgr.log|Rejestruje działanie zainstalowanych aplikacji Instalator Windows, w których zaktualizowano lokalizacje źródłowe bieżącego punktu dystrybucji.|  
|StatusAgent.log|Rejestruje komunikaty o stanie tworzone przez komponenty klienta.|  
|SWMTRReportGen.log|Generuje raport danych użycia zbieranych przez agenta zliczania. Te dane są rejestrowane w pliku Mtrmgr.log.|  
|UserAffinity.log|Rejestruje szczegółowe informacje o koligacji urządzenia użytkownika.|  
|VirtualApp.log|Rejestruje informacje specyficzne dla oceny typów wdrożeń Application Virtualization (App-V).|  
|Wedmtrace.log|Rejestruje operacje dotyczące filtrów zapisu na klientach z systemem Windows Embedded.|  
|wakeprxy-install.log|Rejestruje informacje o instalacji, gdy klienci odbierają opcję Ustawienia klienta, aby włączyć serwer proxy wznawiania.|  
|wakeprxy-uninstall.log|Rejestruje informacje o odinstalowaniu serwera proxy wzbudzania, gdy klienci odbierają opcję Ustawienia klienta na wyłączenie serwera proxy wzbudzania, jeżeli serwera proxy wznawiania był wcześniej włączony.|  

###  <a name="BKMK_ClientInstallLog"></a>Pliki dziennika instalacji klienta  
 W poniższej tabeli wymieniono pliki dziennika zawierające informacje dotyczące instalacji klienta programu Configuration Manager.  

|Nazwa dziennika|Opis|  
|--------------|-----------------|  
|ccmsetup.log|Rejestruje zadania ccmsetup.exe dla Instalatora klienta, uaktualniania i usuwania klientów. Może służyć do rozwiązywania problemów z instalacją klienta.|  
|ccmsetup-ccmeval.log|Rejestruje zadania ccmsetup.exe dla stanu i korygowania klienta.|  
|CcmRepair.log|Rejestruje działania naprawy agenta klienta.|  
|client.msi.log|Rejestruje zadania instalacji wykonywane przez program client.msi. Może służyć do rozwiązywania problemów z instalacją lub usuwaniem klienta.|  

###  <a name="BKMK_LogFilesforLnU"></a>Klient dla systemu Linux i UNIX  
 Klient programu Configuration Manager dla systemu Linux i UNIX rejestruje informacje w poniższych plikach dziennika.  

> [!TIP]  
>  Począwszy od klientów dla systemu Linux i UNIX od aktualizacji zbiorczej 1, można użyć programu CMTrace do wyświetlania plików dziennika na kliencie dla systemu Linux i UNIX.  

> [!NOTE]  
>  Jeżeli używana jest początkowa wersja klienta dla systemu Linux i UNIX oraz dokumentacja w tej sekcji, dla każdego pliku lub procesu należy zastąpić poniższe odwołania:  
>   
>  -   Zamień **omiserver.bin** na **nwserver.bin**  
> -   Zamień **omi** na **nanowbem**  

|Nazwa dziennika|Szczegóły|  
|--------------|-------------|  
|Scxcm.log|Plik dziennika usługi podstawowej klienta programu Configuration Manager dla systemu Linux i UNIX (ccmexec.bin). Ten plik dziennika zawiera informacje o instalacji i przeprowadzanych operacjach programu ccmexec.bin.<br /><br /> Domyślnie ten plik dziennika znajduje się w **/var/opt/microsoft/scxcm.log**<br /><br /> Aby zmienić lokalizację pliku dziennika, należy otworzyć do edycji plik **/opt/microsoft/configmgr/etc/scxcm.conf** i zmienić wartość pola **PATH**. Aby zmiana została uwzględniona, nie trzeba ponownie uruchamiać komputera klienckiego ani usługi.<br /><br /> Można ustawić poziom rejestrowania do jednej z czterech ustawień.|  
|Scxcmprovider.log|Plik dziennika usługi CIM klienta programu Configuration Manager dla systemu Linux i UNIX (omiserver.bin). Ten plik dziennika zawiera informacje o przeprowadzanych operacjach programu nwserver.bin.<br /><br /> Ten dziennik znajduje się w folderze**/var/opt/microsoft/configmgr/scxcmprovider.log**<br /><br /> Aby zmienić lokalizację pliku dziennika, należy otworzyć do edycji plik **/opt/microsoft/omi/etc/scxcmprovider.conf** i zmienić wartość pola **PATH**. Aby zmiana została uwzględniona, nie trzeba ponownie uruchamiać komputera klienckiego ani usługi.<br /><br /> Jedno z trzech ustawień można ustawić poziom rejestrowania.|  

 Oba pliki dziennika obsługują kilka poziomów rejestrowania:  

-   **scxcm.log**. Aby zmienić poziom dziennika, należy edytować **/opt/microsoft/configmgr/etc/scxcm.conf** i zmienić każde wystąpienie **modułu** tag poziom dziennika ma:  

    -   BŁĄD: Informuje o problemach wymagających uwagi  

    -   OSTRZEŻENIE: Informuje o możliwych problemach z operacjami klienta  

    -   INFORMACJE: Bardziej szczegółowe rejestrowanie, które wskazuje stan różnych zdarzeń na kliencie  

    -   TRACE: Pełne rejestrowanie to zazwyczaj służy do diagnozowania problemów  

-   **scxcmprovider.log**. Aby zmienić poziom dziennika, należy edytować **/opt/microsoft/omi/etc/scxcmprovider.conf** i zmienić każde wystąpienie **modułu** tag poziom dziennika ma:  

    -   BŁĄD: Informuje o problemach wymagających uwagi  

    -   OSTRZEŻENIE: Informuje o możliwych problemach z operacjami klienta

    -   INFORMACJE: Bardziej szczegółowe rejestrowanie, które wskazuje stan różnych zdarzeń na kliencie  

W normalnych warunkach pracy należy używać poziomu ERROR dziennika. Ten poziom dziennika tworzy najmniejszy plik dziennika. Zwiększenie poziomu dziennika z ERROR WARNING, Info, a następnie do śledzenia, rozmiar pliku dziennika jest tworzony podczas zapisywania do pliku więcej danych.  

####  <a name="BKMK_ManageLinuxLogs"></a>Zarządzanie plikami dziennika na kliencie systemu Linux i UNIX  
Klienta dla systemu Linux i UNIX nie istnieje limit maksymalny rozmiar plików dziennika klienta, a nie klienta kopiuje automatycznie zawartości jego plików log do innego pliku, takich jak plik Lo_. Jeśli chcesz kontrolować maksymalny rozmiar plików dziennika, należy wdrożyć proces zarządzania plikami dziennika niezależny od klienta programu Configuration Manager dla systemu Linux i UNIX.  

Na przykład można użyć standardowego polecenia systemu Linux i UNIX **logrotate** zarządzać rozmiarem i rotacją plików dziennika klienta. Klient programu Configuration Manager dla systemu Linux i UNIX zawiera interfejs umożliwiający **logrotate** sygnalizują klienta po ukończeniu rotacji dziennika, więc klienta można wznowić rejestrowanie w pliku dziennika.  

Informacje o poleceniu **logrotate** zawiera dokumentacja używanych dystrybucji systemu Linux i UNIX.  

###  <a name="BKMK_LogfilesforMac"></a>Klient dla komputerów Mac  
Klient programu Configuration Manager dla komputerów Mac rejestruje informacje w poniższych plikach dziennika.  

|Nazwa dziennika|Szczegóły|  
|--------------|-------------|  
|CCMClient -&lt;*start_time*> .log|Rejestruje działania związane z operacjami klienta Mac, w tym zarządzania aplikacjami, spisu i rejestrowania błędów.<br /><br /> Ten plik dziennika znajduje się w folderze/Library/Application Support/Microsoft/CCM/Logs na komputerze Mac.|  
|CCMAgent -&lt;*start_time*> .log|Rejestruje informacje dotyczące operacji klienta, w tym logowania użytkownika i operacje wylogowania oraz działań komputera Mac.<br /><br /> Ten plik dziennika znajduje się w folderze ~/Library/Logs na komputerze Mac.|  
|CCMNotifications -&lt;*start_time*> .log|Rejestruje działania związane z wyświetlanych na komputerze Mac powiadomienia programu Configuration Manager.<br /><br /> Ten plik dziennika znajduje się w folderze ~/Library/Logs na komputerze Mac.|  
|CCMPrefPane -&lt;*start_time*> .log|Rejestruje działania dotyczące do okna dialogowego preferencji programu Configuration Manager na komputerze Mac, w tym stanu ogólnego i rejestrowania błędów.<br /><br /> Ten plik dziennika znajduje się w folderze ~/Library/Logs na komputerze Mac.|  

M komunikację między komputerami Mac i punktem zarządzania, ustawionej dla urządzeń przenośnych i komputerów Mac rejestruje także plik dziennika SMS_DM.log na serwerze systemu lokacji.  

##  <a name="BKMK_ServerLogs"></a>Pliki dziennika serwera lokacji programu Configuration Manager  
 W poniższych sekcjach wymieniono pliki dziennika, które znajdują się na serwerze lokacji lub które są związane z określonych ról systemu lokacji.  

###  <a name="BKMK_SiteSiteServerLog"></a>Serwera i witryny dzienniki systemu lokacji serwera  
 Poniższa tabela zawiera listę plików dziennika, znajdujących się na serwerze lokacji programu Configuration Manager i serwery systemu lokacji.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|adctrl.log|Rejestruje działanie przetwarzania rejestracji.|Serwer lokacji|  
|ADForestDisc.log|Rejestruje akcje odnajdowania lasu usługi Active Directory.|Serwer lokacji|  
|ADService.log|Rejestruje szczegółowe informacje o tworzeniu konta i grupie zabezpieczeń w usłudze Active Directory.|Serwer lokacji|  
|adsgdis.log|Rejestruje akcje odnajdowania grupy usługi Active Directory.|Serwer lokacji|  
|adsysdis.log|Rejestruje akcje odnajdowania systemu usługi Active Directory.|Serwer lokacji|  
|adusrdis.log|Rejestruje akcje odnajdowania użytkownika usługi Active Directory.|Serwer lokacji|  
|ccm.log|Rejestruje działania instalacji wypychanej klienta.|Serwer lokacji|  
|CertMgr.log|Rejestruje certyfikat działań do komunikacji wewnątrzlokacyjnej.|Serwer systemu lokacji|  
|chmgr.log|Rejestruje działania menedżera kondycji klienta.|Serwer lokacji|  
|Cidm.log|Rejestruje zmiany w ustawieniach klienta wprowadzone przez program Client Install Data Manager (CIDM).|Serwer lokacji|  
|colleval.log|Rejestruje szczegóły dotyczące utworzenia, zmiany i usunięcia kolekcji przez Ewaluatora kolekcji.|Serwer lokacji|  
|compmon.log|Rejestruje stan wątków składnika monitorowanych dla serwera lokacji.|Serwer systemu lokacji|  
|compsumm.log|Rejestruje zadania składnika podsumowania stanu składnika.|Serwer lokacji|  
|ComRegSetup.log|Rejestruje instalację początkową wyników rejestracji COM dla serwera lokacji.|Serwer systemu lokacji|  
|dataldr.log|Rejestruje informacje o przetwarzaniu plików MIF i spisu sprzętu w bazie danych programu Configuration Manager.|Serwer lokacji|  
|ddm.log|Rejestruje czynności menedżera danych odnajdywania.|Serwer lokacji|  
|despool.log|Rejestruje komunikację przychodzącą między lokacjami.|Serwer lokacji|  
|distmgr.log|Rejestruje szczegółowe informacje o tworzeniu pakietu, kompresji, replikacji różnicowej i aktualizacjach informacji.|Serwer lokacji|  
|EPCtrlMgr.log|Rejestruje informacje o synchronizacji informacji zagrożenia złośliwym oprogramowaniem z serwera roli systemu lokacji programu Endpoint Protection z bazą danych programu Configuration Manager.|Serwer lokacji|  
|EPMgr.log|Rejestruje stan roli systemu lokacji programu Endpoint Protection.|Serwer systemu lokacji|  
|EPSetup.log|Udostępnia informacje o instalacji roli systemu lokacji programu Endpoint Protection.|Serwer systemu lokacji|  
|EnrollSrv.log|Rejestruje działania procesu usługi rejestracji.|Serwer systemu lokacji|  
|EnrollWeb.log|Rejestruje działania procesu witryny sieci Web rejestracji.|Serwer systemu lokacji|  
|fspmgr.log|Rejestruje działania roli systemu lokacji rezerwowego punkt stanu.|Serwer systemu lokacji|  
|hman.log|Rejestruje informacje o zmianach konfiguracji lokacji i o publikowaniu informacji o lokacji w usługach domenowych w usłudze Active Directory.|Serwer lokacji|  
|Inboxast.log|Rejestruje pliki przenoszone z punktu zarządzania do odpowiedniego folderu INBOXES na serwerze lokacji.|Serwer lokacji|  
|inboxmgr.log|Rejestruje działania transferu plików między folderami skrzynki odbiorczej.|Serwer lokacji|  
|inboxmon.log|Rejestruje przetwarzanie plików skrzynki odbiorczej i aktualizacje licznika wydajności.|Serwer lokacji|  
|invproc.log|Rejestruje przekazywanie plików MIF z lokacji dodatkowej do jej lokacji nadrzędnej.|Serwer lokacji|  
|migmctrl.log|Rejestruje informacje o akcjach migracji zadań migracji, współużytkowanych punktów dystrybucji i uaktualnień punktu dystrybucji.|Lokacja najwyższego poziomu w hierarchii programu Configuration Manager i każda podrzędna lokacja główna.<br /><br /> W hierarchii wielu lokacji głównych należy użyć pliku dziennika jest tworzony w witrynie Administracja centralna.|  
|mpcontrol.log|Rejestruje rejestrację punktu zarządzania z usługi nazw internetowych systemu Windows (WINS). Rejestruje dostępność punktu zarządzania co 10 minut.|Serwer systemu lokacji|  
|mpfdm.log|Rejestruje akcje składnika punktu zarządzania, który przenosi pliki klienta do odpowiedniego folderu INBOXES na serwerze lokacji.|Serwer systemu lokacji|  
|mpMSI.log|Rejestruje szczegółowe informacje o zarządzaniu punktu instalacji.|Serwer lokacji|  
|MPSetup.log|Rejestruje proces otoki instalacji punktu zarządzania.|Serwer lokacji|  
|netdisc.log|Rejestruje akcje funkcji Odnajdywanie sieci.|Serwer lokacji|  
|ntsvrdis.log|Rejestruje działanie odnajdowania serwerów systemu lokacji.|Serwer lokacji|  
|Objreplmgr|Rejestruje przetwarzania powiadomień o zmianie obiektu na potrzeby replikacji.|Serwer lokacji|  
|offermgr.log|Rejestruje aktualizacje anonsu.|Serwer lokacji|  
|offersum.log|Rejestruje podsumowanie komunikatów o stanie wdrożenia.|Serwer lokacji|  
|OfflineServicingMgr.log|Rejestruje działania zastosowania aktualizacji w plikach obrazu systemu operacyjnego.|Serwer lokacji|  
|outboxmon.log|Rejestruje przetwarzanie plików skrzynki nadawczej i aktualizacje licznika wydajności.|Serwer lokacji|  
|PerfSetup.log|Rejestruje wyniki instalacji liczników wydajności.|Serwer systemu lokacji|  
|PkgXferMgr.log|Rejestruje akcje składnika SMS_Executive, który jest odpowiedzialny za wysyłanie zawartości z lokacji głównej do zdalnego punktu dystrybucji.|Serwer lokacji|  
|policypv.log|Rejestruje aktualizacje zasad klienta, aby uwzględnić zmiany w ustawieniach lub wdrożeniach klienta.|Serwer lokacji głównej|  
|rcmctrl.log|Rejestruje działania replikacji bazy danych między lokacjami w hierarchii.|Serwer lokacji|  
|replmgr.log|Rejestruje replikację plików między składnikami serwera lokacji a składnikiem Harmonogram.|Serwer lokacji|  
|ResourceExplorer.log|Rejestruje błędy, ostrzeżenia i informacje o uruchamianiu Eksploratora zasobów.|Komputera, na którym jest uruchomiona konsola programu Configuration Manager|  
|ruleengine.log|Rejestruje szczegółowe informacje o zasadach automatycznego wdrażania dla celów identyfikacji, pobierania zawartości oraz tworzenia grupy aktualizacji oprogramowania i wdrożenia.|Serwer lokacji|  
|schedule.log|Rejestruje szczegółowe informacje o replikacji zadań i plików między lokacjami.|Serwer lokacji|  
|sender.log|Rejestruje pliki przesyłane między lokacjami za pomocą replikacji opartej na plikach.|Serwer lokacji|  
|sinvproc.log|Rejestruje informacje o przetwarzaniu danych stanu zapasów oprogramowania w bazie danych lokacji.|Serwer lokacji|  
|sitecomp.log|Rejestruje szczegółowe informacje o obsłudze zainstalowanych komponentów lokacji na wszystkich serwerach systemu lokacji.|Serwer lokacji|  
|sitectrl.log|Rejestruje zmiany w ustawieniach lokacji wprowadzone w obiektach kontroli lokacji w bazie danych.|Serwer lokacji|  
|sitestat.log|Rejestruje dostępność i proces monitorowania miejsca na dysku we wszystkich systemach lokacji.|Serwer lokacji|  
|SmsAdminUI.log|Rejestruje działanie konsoli programu Configuration Manager.|Komputera, na którym jest uruchomiona konsola programu Configuration Manager|  
|SMSAWEBSVCSetup.log|Rejestruje działania instalacji usługi sieci Web Katalog aplikacji.|Serwer systemu lokacji|  
|smsbkup.log|Rejestruje dane wyjściowe z procesu tworzenia kopii zapasowej aplikacji.|Serwer lokacji|  
|smsdbmon.log|Rejestruje zmiany bazy danych.|Serwer lokacji|  
|SMSENROLLSRVSetup.log|Rejestruje działania instalacji usługi sieci Web rejestracji.|Serwer systemu lokacji|  
|SMSENROLLWEBSetup.log|Rejestruje działania instalacji witryny sieci Web rejestracji.|Serwer systemu lokacji|  
|smsexec.log|Rejestruje przetwarzanie wszystkich wątków składnika serwera lokacji.|Serwer lokacji lub serwer systemu lokacji|  
|SMSFSPSetup.log|Rejestruje komunikaty generowane przez instalację rezerwowego punkt stanu.|Serwer systemu lokacji|  
|SMSPORTALWEBSetup.log|Rejestruje działania instalacji witryny sieci Web Katalog aplikacji.|Serwer systemu lokacji|  
|SMSProv.log|Rejestruje dostęp dostawcy WMI do bazy danych lokacji.|Komputer z dostawcą programu SMS|  
|srsrpMSI.log|Rejestruje szczegółowe wyniki procesu instalacji punktu raportowania z danych wyjściowych MSI.|Serwer systemu lokacji|  
|srsrpsetup.log|Rejestruje wyniki procesu instalacji punktu raportowania.|Serwer systemu lokacji|  
|statesys.log|Rejestruje przetwarzanie komunikatów o stanie systemu.|Serwer lokacji|  
|statmgr.log|Rejestruje zapisywanie wszystkich komunikatów o stanie w bazie danych.|Serwer lokacji|  
|swmproc.log|Rejestruje przetwarzanie plików i ustawień zliczania.|Serwer lokacji|  

###  <a name="BKMK_SiteInstallLog"></a>Pliki dziennika instalacji serwera lokacji  
 W poniższej tabeli wymieniono pliki dziennika zawierające informacje dotyczące instalacji lokacji.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|ConfigMgrPrereq.log|Rejestruje składników wymaganych wstępnie działania oceny i instalacji.|Serwer lokacji|  
|ConfigMgrSetup.log|Rejestruje szczegółowe dane wyjściowe instalacji serwera lokacji.|Serwer lokacji|  
|ConfigMgrSetupWizard.log|Rejestruje informacje dotyczące działań w Kreatorze instalacji.|Serwer lokacji|  
|SMS_BOOTSTRAP.log|Rejestruje informacje postępie uruchamiania procesu instalacji lokacji dodatkowej. Szczegółowe informacje o procesie instalacji znajdują się w pliku ConfigMgrSetup.log.|Serwer lokacji|  
|smstsvc.log|Rejestruje informacje o instalacji, użyciu i usunięciu usługi systemu Windows, który służy do testowania połączenia sieciowego i uprawnień między serwerami przy użyciu konta komputera serwera, który inicjuje połączenie.|Serwer lokacji i serwera systemu lokacji|  

###  <a name="BKMK_FSPLog"></a>Pliki dziennika punktu stanu powrotu  
 W poniższej tabeli wymieniono pliki dziennika zawierające informacje dotyczące rezerwowego punkt stanu.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|FspIsapi|Rejestruje szczegółowe informacje o komunikacji z rezerwowym punktem stanu ze starszych klientów urządzeń przenośnych i komputerów klienckich.|Serwer systemu lokacji|  
|fspMSI.log|Rejestruje komunikaty generowane przez instalację rezerwowego punkt stanu.|Serwer systemu lokacji|  
|fspmgr.log|Rejestruje działania roli systemu lokacji rezerwowego punkt stanu.|Serwer systemu lokacji|  

###  <a name="BKMK_MPLog"></a>Pliki dziennika punktu zarządzania  
 W poniższej tabeli wymieniono pliki dziennika zawierające informacje dotyczące punktu zarządzania.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|CcmIsapi.log|Rejestruje działanie wysyłania wiadomości przez klienta w punkcie końcowym.|Serwer systemu lokacji|  
|MP_CliReg.log|Rejestruje działanie rejestracji klienta przetworzone przez punkt zarządzania.|Serwer systemu lokacji|  
|MP_Ddr.log|Rejestruje konwersji XML.ddr rejestruje od klientów i kopiuje je na serwerze lokacji.|Serwer systemu lokacji|  
|MP_Framework.log|Rejestruje działania podstawowego punktu zarządzania i komponentów środowiska klienta.|Serwer systemu lokacji|  
|MP_GetAuth.log|Rejestruje działanie autoryzacji klienta.|Serwer systemu lokacji|  
|MP_GetPolicy.log|Rejestruje działanie żądania zasad z komputerów klienckich.|Serwer systemu lokacji|  
|MP_Hinv.log|Rejestruje szczegółowe informacje o konwersji rekordów XML spisu sprzętu od klientów i kopii tych plików na serwerze lokacji.|Serwer systemu lokacji|  
|MP_Location.log|Rejestruje żądanie lokalizacji i odpowiedzi klientów.|Serwer systemu lokacji|  
|MP_OOBMgr.log|Rejestruje działania punktu zarządzania dotyczące odbierania OTP od klienta.|Serwer systemu lokacji|  
|MP_Policy.log|Rejestruje przesyłanie zasad.|Serwer systemu lokacji|  
|MP_Relay.log|Rejestruje transfer plików zebranych od klienta.|Serwer systemu lokacji|  
|MP_Retry.log|Rejestruje procesy ponawiania prób spisu sprzętu.|Serwer systemu lokacji|  
|MP_Sinv.log|Rejestruje szczegółowe informacje o konwersji rekordów XML spisu oprogramowania od klientów i kopii tych plików na serwerze lokacji.|Serwer systemu lokacji|  
|MP_SinvCollFile.log|Rejestruje szczegółowe informacje o zbieraniu plików.|Serwer systemu lokacji|  
|MP_Status.log|Rejestruje szczegółowe informacje o konwersji plików komunikatów o stanie XML.svf od klientów i kopii tych plików na serwerze lokacji.|Serwer systemu lokacji|  
|mpcontrol.log|Rejestruje rejestrację punktu zarządzania w usłudze WINS. Rejestruje dostępność punktu zarządzania co 10 minut.|Serwer lokacji|  
|mpfdm.log|Rejestruje akcje składnika punktu zarządzania, który przenosi pliki klienta do odpowiedniego folderu INBOXES na serwerze lokacji.|Serwer systemu lokacji|  
|mpMSI.log|Rejestruje szczegółowe informacje o zarządzaniu punktu instalacji.|Serwer lokacji|  
|MPSetup.log|Rejestruje proces otoki instalacji punktu zarządzania.|Serwer lokacji|  

###  <a name="BKMK_SUPLog"></a>Pliki dziennika punktu aktualizacji oprogramowania  
 W poniższej tabeli wymieniono pliki dziennika zawierające informacje powiązane z punktem aktualizacji oprogramowania.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|objreplmgr.log|Rejestruje szczegółowe informacje o replikacji oprogramowania plików powiadomień aktualizacji z witryny nadrzędnej do lokacji podrzędnych.|Serwer lokacji|  
|PatchDownloader.log|Rejestruje szczegółowe informacje o procesie pobierania aktualizacji oprogramowania ze źródła aktualizacji do miejsca docelowego pobierania na serwerze lokacji.|Komputer, który jest hostem konsoli programu Configuration Manager, z której inicjowane jest pobieranie|  
|ruleengine.log|Rejestruje szczegółowe informacje o zasadach automatycznego wdrażania dla celów identyfikacji, pobierania zawartości oraz tworzenia grupy aktualizacji oprogramowania i wdrożenia.|Serwer lokacji|  
|SUPSetup.log|Rejestruje szczegółowe informacje o instalacji punktu aktualizacji oprogramowania. Po ukończeniu instalacji punktu aktualizacji oprogramowania w tym pliku dziennika zapisywany jest komunikat **Instalacja powiodła się**.|Serwer systemu lokacji|  
|WCM.log|Rejestruje szczegółowe informacje o aktualizacjach oprogramowania punktu konfiguracji i połączeń z serwerem WSUS dotyczące zasubskrybowanych kategorii aktualizacji, klasyfikacji i języków.|Serwer lokacji, który łączy się z serwerem WSUS|  
|WSUSCtrl.log|Rejestruje szczegółowe informacje o konfiguracji, połączeniu z bazą danych i kondycji serwera programu WSUS dla lokacji.|Serwer systemu lokacji|  
|wsyncmgr.log|Rejestruje szczegółowe informacje na temat procesu synchronizacji aktualizacji oprogramowania.|Serwer systemu lokacji|  
|WUSSyncXML.log|Rejestruje szczegółowe informacje dotyczące narzędzia stanu zapasów usługi Microsoft Updates synchronizacji procesu.|Komputer kliencki skonfigurowany jako host synchronizacji narzędzia stanu zapasów usługi Microsoft Updates|  

##  <a name="BKMK_FunctionLogs"></a>Pliki dziennika dotyczące funkcji programu Configuration Manager  
 Na poniższej liście sekcje pliki dziennika związane z funkcjami programu Configuration Manager.  

###  <a name="BKMK_AppManageLog"></a>Zarządzanie aplikacjami  
 W poniższej tabeli wymieniono pliki dziennika zawierające informacje powiązane z zarządzaniem aplikacjami.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|AppIntentEval.log|Rejestruje szczegółowe informacje o bieżącym i planowanym stanie aplikacji, możliwości ich zastosowania, spełnieniu lub niespełnieniu wymagań, typach wdrożeń i zależnościach.|Klient|  
|AppDiscovery.log|Rejestruje szczegółowe informacje o odnajdywaniu (wykrywaniu) aplikacji na komputerach klienckich.|Klient|  
|AppEnforce.log|Rejestruje szczegółowe informacje o akcjach wymuszania (instalacji i dezinstalacji) podejmowanych przez aplikacje na kliencie.|Klient|  
|awebsctl.log|Rejestruje działania usługi sieci web katalogu aplikacji monitorowania punktu Rola systemu lokacji.|Serwer systemu lokacji|  
|awebsvcMSI.log|Rejestruje szczegółowe informacje o instalacji roli systemu lokacji punktu usługi sieci Web Katalog aplikacji.|Serwer systemu lokacji|  
|Ccmsdkprovider.log|Rejestruje działania zestawu SDK do zarządzania aplikacjami.|Klient|  
|colleval.log|Rejestruje szczegóły dotyczące utworzenia, zmiany i usunięcia kolekcji przez Ewaluatora kolekcji.|Serwer systemu lokacji|  
|ConfigMgrSoftwareCatalog.log|Rejestruje działania Katalogu aplikacji, w tym wykorzystanie przez niego programu Silverlight.|Klient|  
|portlctl.log|Rejestruje działania monitorujące roli systemu lokacji punktu witryny sieci Web Katalog aplikacji.|Serwer systemu lokacji|  
|portlwebMSI.log|Rejestruje działania instalacji MSI roli witryny sieci Web Katalog aplikacji.|Serwer systemu lokacji|  
|PrestageContent.log|Rejestruje szczegółowe informacje dotyczące korzystania z narzędzia ExtractContent.exe w punkcie dystrybucji zdalnego, wstępnie przygotowany. To narzędzie wyodrębnia zawartość, którą wcześniej wyeksportowano do pliku.|Serwer systemu lokacji|  
|ServicePortalWebService.log|Rejestruje działania usługi sieci Web Katalog aplikacji.|Serwer systemu lokacji|  
|ServicePortalWebSite.log|Rejestruje działania witryny sieci Web Katalog aplikacji.|Serwer systemu lokacji|  
|SMSdpmon.log|Rejestruje szczegółowe informacje o zaplanowanym zadaniu monitorowania kondycji punktu dystrybucji skonfigurowanym w punkcie dystrybucji.|Serwer lokacji|  
|SoftwareCatalogUpdateEndpoint.log|Rejestruje działania dotyczące zarządzania adres URL katalogu aplikacji widocznym w Centrum oprogramowania.|Klient|  
|SoftwareCenterSystemTasks.log|Rejestruje działania dotyczące weryfikacji składnika wymagań wstępnych Centrum oprogramowania.|Klient|  

 W poniższej tabeli wymieniono pliki dziennika zawierające informacje powiązane z wdrażaniem pakietów i programów.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|colleval.log|Rejestruje szczegóły dotyczące utworzenia, zmiany i usunięcia kolekcji przez Ewaluatora kolekcji.|Serwer lokacji|  
|execmgr.log|Rejestruje szczegółowe informacje o uruchamianych pakietach i sekwencjach zadań.|Klient|  

###  <a name="BKMK_AILog"></a>Analiza zasobów  
 W poniższej tabeli wymieniono pliki dziennika zawierające informacje powiązane z Analizą zasobów.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|AssetAdvisor.log|Rejestruje działania akcji ewidencjonowania Analizy zasobów.|Klient|  
|aikbmgr.log|Rejestruje szczegółowe informacje o przetwarzaniu plików XML ze skrzynki odbiorczej w celu aktualizacji katalogu Analizy zasobów.|Serwer lokacji|  
|AIUpdateSvc.log|Rejestruje interakcję synchronizacji analizy zasobów punktu z System Center Online (SCO), usługi sieci web trybu online.|Serwer systemu lokacji|  
|AIUSMSI.log|Rejestruje szczegółowe informacje o instalacji synchronizacji analizy zasobów punktu Rola systemu lokacji.|Serwer systemu lokacji|  
|AIUSSetup.log|Rejestruje szczegółowe informacje o instalacji synchronizacji analizy zasobów punktu Rola systemu lokacji.|Serwer systemu lokacji|  
|ManagedProvider.log|Rejestruje szczegółowe informacje o odnajdywaniu oprogramowania na podstawie skojarzonego znacznika identyfikacji oprogramowania. Rejestruje także działania powiązane z spisu sprzętu.|Serwer systemu lokacji|  
|MVLSImport.log|Rejestruje szczegółowe informacje o przetwarzaniu zaimportowanych plików licencjonowania.|Serwer systemu lokacji|  

###  <a name="BKMK_BnRLog"></a>Kopia zapasowa i odzyskiwanie  
 W poniższej tabeli wymieniono pliki dziennika zawierające informacje powiązane z akcjami tworzenia kopii zapasowych i odzyskiwania, w tym także resetowaniem lokacji, i zmianami dostawcy programu SMS.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|ConfigMgrSetup.log|Rejestruje informacje o zadaniach instalacji i odzyskiwania, gdy Menedżer konfiguracji odzyskiwania lokacji z kopii zapasowej.|Serwer lokacji|  
|Smsbkup.log|Rejestruje szczegółowe informacje o działaniach związanych z tworzeniem kopii zapasowej lokacji.|Serwer lokacji|  
|smssqlbkup.log|Rejestruje dane wyjściowe z procesu tworzenia kopii zapasowej bazy danych lokacji programu SQL Server jest zainstalowany na serwerze, który nie jest serwerem lokacji.|Serwer bazy danych lokacji|  
|Smswriter.log|Rejestruje informacje o stanie składnik zapisywania usługi VSS programu Configuration Manager, który jest używany przez proces tworzenia kopii zapasowej.|Serwer lokacji|  

###  <a name="BKMK_CertificateEnrollment"></a>Rejestracja certyfikatów  
 Poniższa tabela zawiera listę plików dziennika programu Configuration Manager, zawierające informacje powiązane z rejestracją certyfikatów. Rejestracji certyfikatów używa punkt rejestracji certyfikatu i moduł zasad programu Configuration Manager na serwerze, na którym jest uruchomiony usługi rejestracji urządzeń sieciowych.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|Crp.log|Rejestruje działania rejestracji.|Punkt rejestracji certyfikatu|  
|Crpctrl.log|Rejestruje kondycję operacyjną punktu rejestracji certyfikatu.|Punkt rejestracji certyfikatu|  
|Crpsetup.log|Rejestruje szczegółowe informacje o instalacji i konfiguracji punktu rejestracji certyfikatu.|Punkt rejestracji certyfikatu|  
|Crpmsi.log|Rejestruje szczegółowe informacje o instalacji i konfiguracji punktu rejestracji certyfikatu.|Punkt rejestracji certyfikatu|  
|NDESPlugin.log|Rejestruje challenge weryfikacji i działania rejestracji certyfikatu.|Moduł zasad programu Configuration Manager i usługi rejestracji urządzeń sieciowych|  

 Oprócz plików dziennika programu Configuration Manager należy przejrzeć dzienniki aplikacji systemu Windows w Podglądzie zdarzeń na serwerze z uruchomioną usługą rejestracji urządzeń sieciowych i serwerze hoście punktu rejestracji certyfikatu. Można na przykład poszukać komunikatów ze źródła **NetworkDeviceEnrollmentService**. Można także użyć następujących plików dziennika:  

-   Pliki dziennika usług IIS dla usługi rejestracji urządzeń sieciowych:  **&lt;ścieżki\>\inetpub\logs\LogFiles\W3SVC1**  

-   Usługi IIS plików dziennika dla punktu rejestracji certyfikatu:  **&lt;ścieżki\>\inetpub\logs\LogFiles\W3SVC1**  

-   Plik dziennika zasad rejestracji urządzeń sieciowych: **mscep.log**  

    > [!NOTE]  
    >  Ten plik znajduje się w folderze profilu konta usługi rejestracji urządzeń sieciowych, na przykład w folderze C:\Users\SCEPSvc. Więcej informacji o sposobach włączania rejestrowania zdarzeń dla usługi rejestracji urządzeń sieciowych znajduje się w sekcji [Enable Logging (Włączanie rejestrowania)](http://go.microsoft.com/fwlink/?LinkId=320576) w artykule Network Device Enrollment Service (NDES) in Active Directory Certificate Services (AD CS) (Usługa rejestracji urządzeń sieciowych w usługach certyfikatów Active Directory) w witrynie wiki biblioteki TechNet.  

###  <a name="BKMK_BGB"></a>Powiadomienie klienta  
 W poniższej tabeli wymieniono pliki dziennika zawierające informacje powiązane z powiadamianiem klientów.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|bgbmgr.log|Rejestruje szczegółowe informacje o działaniach serwera lokacji powiązane z zadaniami powiadamiania klientów oraz przetwarzanie w trybie online i plików stanu zadań.|Serwer lokacji|  
|BGBServer.log|Rejestruje działania serwera powiadamiania, takie jak komunikacja klient serwer i wypychanie zadań do klientów. Rejestruje także informacje o Generowanie online i plików stanu zadań, które zostanie wysłane do serwera lokacji.|Punkt zarządzania|  
|BgbSetup.log|Rejestruje działania procesu otoki instalacji serwera powiadamiania podczas instalacji i dezinstalacji.|Punkt zarządzania|  
|bgbisapiMSI.log|Rejestruje szczegółowe informacje dotyczące instalacji serwera powiadamiania i dezinstalacji.|Punkt zarządzania|  
|BgbHttpProxy.log|Rejestruje działania serwera proxy HTTP powiadamiania w trakcie przekazywania przez niego komunikatów klientów wykorzystujących protokół HTTP do i od serwera powiadamiania.|Klient|  
|CcmNotificationAgent.log|Rejestruje działania agenta powiadamiania, takie jak komunikacja klient serwer oraz informacje o zadaniach odebranych i wysłanych do innych agentów klienta.|Klient|  

### <a name="cloud-management-gateway"></a>Brama zarządzania chmury

Poniższej tabeli wymieniono pliki dziennika zawierające informacje powiązane z bramą zarządzania chmury.

||||
|-|-|-|
|Nazwa dziennika|Opis|Komputer z plikiem dziennika|
|CloudMgr.log|Rejestruje szczegółowe informacje dotyczące wdrażania usługi w chmurze zarządzania bramą, stan trwającej usługi i Użyj danych skojarzonych z usługą.<br>Można skonfigurować poziom rejestrowania Edycja rejestru **poziom HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\SMS\COMPONENTS\SMS_CLOUD_SERVICES_MANAGER\Logging**|**SMS/dzienniki** folder na serwerze systemu lokacji|
|CMGSetup.log lub CMG -*RoleInstanceID*-CMGSetup.log<sup>1</sup>|Rejestruje szczegółowe informacje dotyczące etapu 2, wdrożenie bramy zarządzania chmury (lokalnego wdrożenia Azure)<br>Można skonfigurować przy użyciu ustawienia poziomu rejestrowania **poziom śledzenia** (**informacji** (opcja domyślna), **pełne**, **błąd**) na **Konfiguracja usług Azure portal\Cloud** kartę.|**%Approot%\logs** na serwerze Azure lub folderze SMS/dzienniki na serwerze systemu lokacji|
|CMGHttpHandler.log lub CMG -*RoleInstanceID*-CMGHttpHandler.log<sup>1</sup>|Rejestruje szczegółowe informacje o chmurze zarządzania bramy http obsługi powiązania z Internetowymi usługami informacyjnymi w systemie Azure<br>Można skonfigurować przy użyciu ustawienia poziomu rejestrowania **poziom śledzenia** (**informacji** (opcja domyślna), **pełne**, **błąd**) na **Konfiguracja usług Azure portal\Cloud** kartę.|**%Approot%\logs** na serwerze Azure lub folderze SMS/dzienniki na serwerze systemu lokacji|
|CMGService.log lub CMG -*RoleInstanceID*-CMGService.log<sup>1</sup>|Rejestruje szczegółowe informacje o chmurze składnik bramy zarządzania usługi core w systemie Azure<br>Można skonfigurować przy użyciu ustawienia poziomu rejestrowania **poziom śledzenia** (**informacji** (opcja domyślna), **pełne**, **błąd**) na **Konfiguracja usług Azure portal\Cloud** kartę.|**%Approot%\logs** na serwerze Azure lub folderze SMS/dzienniki na serwerze systemu lokacji|
|SMS_Cloud_ProxyConnector.log|Rejestruje szczegółowe informacje o konfigurowaniu połączeń między usługą bramy zarządzania w chmurze i połączenie bramy zarządzania chmury punktu.|Serwer systemu lokacji|

<sup>1</sup> są lokalne pliki dziennika programu Configuration Manager w chmurze usługi Menedżera synchronizacji z magazynu systemu Azure co 5 minut. Brama zarządzania chmury przeprowadzi wypychanie dzienniki do magazynu systemu Azure co 5 minut. Maksymalne opóźnienie będzie to 10 minut. Przełączniki pełne wpływają na dzienniki lokalnymi i zdalnymi.

- Rozwiązywanie problemów z wdrożeniami, użyj **CloudMgr.log** i **CMGSetup.log**
- Rozwiązywanie problemów z kondycji usługi, użyj **CMGService.log** i **SMS_Cloud_ProxyConnector.log**.
- Rozwiązywanie problemów z ruch sieciowy klienta, użyj **CMGHttpHandler.log**, **CMGService.log**, i **SMS_Cloud_ProxyConnector.log**.

###  <a name="BKMK_CompSettingsLog"></a>Ustawienia zgodności i dostęp do zasobów firmy  
 W poniższej tabeli wymieniono pliki dziennika zawierające informacje powiązane z ustawieniami zgodności i dostępem do zasobów firmy.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|CIAgent.log|Rejestruje szczegółowe informacje o procesie korygowania i zapewniania zgodności dotyczącym ustawień zgodności, aktualizacji oprogramowania i zarządzania aplikacjami.|Klient|  
|CITaskManager.log|Rejestruje informacje o planowaniu zadań elementu konfiguracji.|Klient|  
|DCMAgent.log|Rejestruje informacje wysokiego poziomu o ocenie, raportowaniu konfliktów i korygowaniu elementów konfiguracji oraz aplikacji.|Klient|  
|DCMReporting.log|Rejestruje informacje o raportowaniu wyników platformy zasad w komunikatach o stanie elementów konfiguracji.|Klient|  
|DcmWmiProvider.log|Rejestruje informacje o odczytywaniu synclets elementów konfiguracji z usługi WMI.|Klient|  

###  <a name="BKMK_ConsoleLog"></a>Konsola programu Configuration Manager  
 W poniższej tabeli wymieniono pliki dziennika zawierające informacje powiązane z konsoli programu Configuration Manager.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|ConfigMgrAdminUISetup.log|Rejestruje instalację konsoli programu Configuration Manager.|Komputera, na którym jest uruchomiona konsola programu Configuration Manager|  
|SmsAdminUI.log|Rejestruje informacje o działaniu konsoli programu Configuration Manager.|Komputera, na którym jest uruchomiona konsola programu Configuration Manager|  
|Smsprov.log|Rejestruje działania wykonywane przez dostawcę programu SMS. Dostawca programu SMS korzystają działania konsoli programu Configuration Manager.|Serwer lokacji lub serwer systemu lokacji|  

###  <a name="BKMK_ContentLog"></a>Zarządzanie zawartością  
 W poniższej tabeli wymieniono pliki dziennika zawierające informacje powiązane z zarządzaniem zawartością.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|Pliku CloudDP -&lt;identyfikatora guid\>log|Rejestruje szczegółowe informacje o określonym chmurowym punkcie dystrybucji, w tym informacje o magazynie i dostępie do zawartości.|Serwer systemu lokacji|  
|CloudMgr.log|Rejestruje szczegółowe informacje o udostępnianiu zawartości, zbieraniu magazynu i statystyki przepustowości oraz inicjowanych przez administratora akcjach zatrzymywania lub uruchamiania usługi w chmurze z punktem dystrybucji w chmurze.|Serwer systemu lokacji|  
|DataTransferService.log|Rejestruje całą komunikację usługi BITS dotyczącą zasad lub dostępu do pakietów. Ten dziennik również służy do zarządzania zawartością ściągających punktów dystrybucji.|Komputer skonfigurowany jako punkt dystrybucji|  
|PullDP.log|Rejestruje szczegółowe informacje o zawartości, jaką ściągający punkt dystrybucji transferuje od źródłowych punktów dystrybucji.|Komputer skonfigurowany jako punkt dystrybucji|  
|PrestageContent.log|Rejestruje szczegółowe informacje dotyczące korzystania z ExtractContent.exe narzędzia w punkcie dystrybucji zdalnego, wstępnie przygotowany. To narzędzie wyodrębnia zawartość, którą wcześniej wyeksportowano do pliku.|Rola systemu lokacji|  
|SMSdpmon.log|Rejestruje szczegółowe informacje o kondycji punktu dystrybucji monitorowania zaplanowanych zadań, które są konfigurowane w punkcie dystrybucji.|Rola systemu lokacji|  
|smsdpprov.log|Rejestruje szczegółowe informacje o wyodrębnianiu plików skompresowanych odebranych z lokacji głównej. Ten dziennik jest generowany przez dostawcę WMI zdalnego punktu dystrybucji.|Komputer punktu dystrybucji, który nie jest przechowywane razem na jednej z serwerem lokacji|  


###  <a name="BKMK_DiscoveryLog"></a>Odnajdywanie  
W poniższej tabeli wymieniono pliki dziennika zawierające informacje powiązane z odnajdywaniem.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|adsgdis.log|Rejestruje akcje odnajdowania grupy zabezpieczeń usługi Active Directory.|Serwer lokacji|  
|adsysdis.log|Rejestruje akcje odnajdowania systemu usługi Active Directory.|Serwer lokacji|  
|adusrdis.log|Rejestruje akcje odnajdowania użytkownika usługi Active Directory.|Serwer lokacji|  
|ADForestDisc.log|Rejestruje akcje odnajdowania lasu usługi Active Directory.|Serwer lokacji|  
|ddm.log|Rejestruje czynności menedżera danych odnajdywania.|Serwer lokacji|  
|InventoryAgent.log|Rejestruje działania ewidencji zapasów sprzętu, ewidencji zapasów oprogramowania i akcje odnajdywania pulsu na kliencie.|Klient|  
|netdisc.log|Rejestruje akcje funkcji Odnajdywanie sieci.|Serwer lokacji|  

###  <a name="BKMK_EPLog"></a>Endpoint Protection  
 W poniższej tabeli wymieniono pliki dziennika zawierające informacje powiązane z ochroną punktu końcowego.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|EndpointProtectionAgent.log|Rejestruje szczegółowe informacje o instalacji klienta programu Endpoint Protection i zastosowaniu zasad ochrony przed złośliwym kodem na tym kliencie.|Klient|  
|EPCtrlMgr.log|Rejestruje szczegółowe informacje dotyczące synchronizowania informacji zagrożenia złośliwym oprogramowaniem z serwera roli programu Endpoint Protection z bazą danych programu Configuration Manager.|Serwer systemu lokacji|  
|EPMgr.log|Monitoruje stan roli systemu lokacji programu Endpoint Protection.|Serwer systemu lokacji|  
|EPSetup.log|Udostępnia informacje o instalacji roli systemu lokacji programu Endpoint Protection.|Serwer systemu lokacji|  

###  <a name="BKMK_Extensions"></a>Rozszerzenia  
 W poniższej tabeli wymieniono pliki dziennika zawierające informacje dotyczące rozszerzeń.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|AdminUI.ExtensionInstaller.log|Rejestruje informacje o pobieraniu rozszerzeń firmy Microsoft oraz instalowaniu i dezinstalowaniu wszystkich rozszerzeń.|Komputera, na którym jest uruchomiona konsola programu Configuration Manager|  
|FeatureExtensionInstaller.log|Rejestruje informacje o instalowaniu i usuwaniu poszczególnych rozszerzeń, gdy są one włączone lub wyłączone w konsoli programu Configuration Manager.|Komputera, na którym jest uruchomiona konsola programu Configuration Manager|  
|SmsAdminUI.log|Rejestruje działanie konsoli programu Configuration Manager.|Komputera, na którym jest uruchomiona konsola programu Configuration Manager|  

###  <a name="BKMK_InventoryLog"></a>Spis  
 W poniższej tabeli wymieniono pliki dziennika zawierające informacje powiązane z przetwarzaniem danych o stanie zapasów.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|dataldr.log|Rejestruje informacje o przetwarzaniu plików MIF i spisu sprzętu w bazie danych programu Configuration Manager.|Serwer lokacji|  
|invproc.log|Rejestruje przekazywanie plików MIF z lokacji dodatkowej do jej lokacji nadrzędnej.|Serwer lokacji dodatkowej|  
|sinvproc.log|Rejestruje informacje o przetwarzaniu danych stanu zapasów oprogramowania w bazie danych lokacji.|Serwer lokacji|  

###  <a name="BKMK_MeteringLog"></a>Pomiaru  
 W poniższej tabeli wymieniono pliki dziennika zawierające informacje powiązane z pomiarami użytkowania.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|mtrmgr.log|Monitoruje wszystkie procesy pomiarów użytkowania oprogramowania.|Serwer lokacji|  

###  <a name="BKMK_MigrationLog"></a>Migracja  
 W poniższej tabeli wymieniono pliki dziennika zawierające informacje powiązane z migracją.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|migmctrl.log|Rejestruje informacje o akcjach migracji dotyczące zadań migracji, współużytkowanych punktów dystrybucji i uaktualnień punktów dystrybucji.|Lokacja najwyższego poziomu w hierarchii programu Configuration Manager i każda podrzędna lokacja główna.<br /><br /> W hierarchii z kilkoma lokacjami głównymi należy użyć pliku dziennika utworzonego w centralnej lokacji administracyjnej.|  

###  <a name="BKMK_MDMLog"></a>Urządzenia przenośne  
 W poniższych sekcjach wymieniono pliki dziennika zawierające informacje powiązane z zarządzaniem urządzeniami przenośnymi.  

####  <a name="BKMK_EnrollmentLog"></a>Rejestracji  
 W poniższej tabeli wymieniono pliki dziennika zawierające informacje powiązane z rejestrowaniem urządzeń przenośnych.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|DMPRP.log|Rejestruje komunikację między punktami zarządzania, w których włączono obsługę urządzeń przenośnych, a punktami końcowymi punktów zarządzania.|Serwer systemu lokacji|  
|dmpmsi.log|Rejestruje dane Instalatora Windows dotyczące konfiguracji punktu zarządzania, w którym włączono obsługę urządzeń przenośnych.|Serwer systemu lokacji|  
|DMPSetup.log|Rejestruje konfigurację punktu zarządzania, w którym włączono obsługę urządzeń przenośnych.|Serwer systemu lokacji|  
|enrollsrvMSI.log|Rejestruje dane Instalatora Windows dotyczące konfiguracji punktu rejestracyjnego.|Serwer systemu lokacji|  
|enrollmentweb.log|Rejestruje komunikację między urządzeniami przenośnymi i punktem proxy rejestracji.|Serwer systemu lokacji|  
|enrollwebMSI.log|Rejestruje dane Instalatora Windows dotyczące konfiguracji punktu proxy rejestracji.|Serwer systemu lokacji|  
|enrollmentservice.log|Rejestruje komunikację między punktem proxy rejestracji i punktem rejestracyjnym.|Serwer systemu lokacji|  
|SMS_DM.log|Rejestruje komunikację między urządzeniami przenośnymi, komputerami Mac i punktem zarządzania, w którym włączono obsługę urządzeń przenośnych i komputerów Mac.|Serwer systemu lokacji|  

####  <a name="BKMK_ExchSrvLog"></a>Łącznik serwera Exchange  
 Następujące dzienniki zawierają informacje dotyczące łącznika serwera Exchange.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|easdisc.log|Rejestruje działania i stan łącznika serwera Exchange.|Serwer lokacji|  

####  <a name="BKMK_MDLegLog"></a>Starsze urządzenia przenośne  
 W poniższej tabeli wymieniono pliki dziennika zawierające informacje powiązane ze starszymi klientami urządzeń przenośnych.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|DmCertEnroll.log|Rejestruje szczegółowe informacje o danych rejestrowania certyfikatów na starszych klientach urządzeń przenośnych.|Klient|  
|DMCertResp.htm|Rejestruje odpowiedź HTML od serwera certyfikatu, kiedy program rejestrowania starszych klientów urządzeń przenośnych żąda certyfikatu PKI.|Klient|  
|DmClientHealth.log|Rejestruje identyfikatory GUID wszystkich starszych klientów urządzeń przenośnych komunikujących się z punktem zarządzania, w którym włączono obsługę urządzeń przenośnych.|Serwer systemu lokacji|  
|DmClientRegistration.log|Rejestruje żądania rejestracji i odpowiedzi na nie wysyłane do i przez starszych klientów urządzeń przenośnych.|Serwer systemu lokacji|  
|DmClientSetup.log|Rejestruje dane instalacji klienta dla starszych klientów urządzeń przenośnych.|Klient|  
|DmClientXfer.log|Rejestruje dane transferu klienta dla starszych klientów urządzeń przenośnych i dla wdrożeń usługi ActiveSync.|Klient|  
|DmCommonInstaller.log|Rejestruje instalację pliku transferu klienta dla konfigurowania plików transferu starszych klientów urządzeń przenośnych.|Klient|  
|DmInstaller.log|Rejestruje, czy funkcja DMInstaller prawidłowo wywołuje funkcję DmClientSetup i czy funkcja DmClientSetup w przypadku starszych klientów urządzeń przenośnych kończy się powodzeniem, czy niepowodzeniem.|Klient|  
|DmpDatastore.log|Rejestruje wszystkie połączenia bazy danych i zapytania punktu zarządzania, w którym włączono obsługę urządzeń przenośnych.|Serwer systemu lokacji|  
|DmpDiscovery.log|Rejestruje wszystkie dane odnajdywania starszych klientów urządzeń przenośnych w punkcie zarządzania, w którym włączono obsługę urządzeń przenośnych.|Serwer systemu lokacji|  
|DmpHardware.log|Rejestruje dane stanu zapasów starszych klientów urządzeń przenośnych w punkcie zarządzania, w którym włączono obsługę urządzeń przenośnych.|Serwer systemu lokacji|  
|DmpIsapi.log|Rejestruje komunikację starszych klientów urządzeń przenośnych z punktem zarządzania, w którym włączono obsługę urządzeń przenośnych.|Serwer systemu lokacji|  
|dmpmsi.log|Rejestruje dane Instalatora Windows dotyczące konfiguracji punktu zarządzania, w którym włączono obsługę urządzeń przenośnych.|Serwer systemu lokacji|  
|DMPSetup.log|Rejestruje konfigurację punktu zarządzania, w którym włączono obsługę urządzeń przenośnych.|Serwer systemu lokacji|  
|DmpSoftware.log|Rejestruje dane dystrybucji oprogramowania starszych klientów urządzeń przenośnych w punkcie zarządzania, w którym włączono obsługę urządzeń przenośnych.|Serwer systemu lokacji|  
|DmpStatus.log|Rejestruje dane komunikatów o stanie klientów urządzeń przenośnych w punkcie zarządzania, w którym włączono obsługę urządzeń przenośnych.|Serwer systemu lokacji|  
|DmSvc.log|Rejestruje komunikację kliencką starszych klientów urządzeń przenośnych z punktem zarządzania, w którym włączono obsługę urządzeń przenośnych.|Klient|  
|FspIsapi.log|Rejestruje szczegółowe informacje o komunikacji z rezerwowym punktem stanu ze starszych klientów urządzeń przenośnych i komputerów klienckich.|Serwer systemu lokacji|  

###  <a name="BKMK_OSDLog"></a>Wdrożenie systemu operacyjnego  
 W poniższej tabeli wymieniono pliki dziennika zawierające informacje powiązane z wdrażaniem systemu operacyjnego.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|CAS.log|Rejestruje szczegółowe informacje o znajdowaniu punktów dystrybucji dla zawartości występującej w odwołaniach.|Klient|  
|ccmsetup.log|Rejestruje zadania programu ccmsetup dla Instalatora klienta, uaktualniania i usuwania klientów. Może służyć do rozwiązywania problemów z instalacją klienta.|Klient|  
|CreateTSMedia.log|Rejestruje szczegółowe informacje o tworzeniu nośnika sekwencji zadań.|Komputera, na którym jest uruchomiona konsola programu Configuration Manager|  
|DeployToVhd.log|Rejestruje szczegółowe informacje o procesie tworzenia i modyfikacji wirtualnych dysków twardych (VHD).|Komputera, na którym jest uruchomiona konsola programu Configuration Manager|  
|Dism.log|Rejestruje akcje instalacji sterowników lub działania aktualizacji aplikacji do obsługi w trybie offline.|Serwer systemu lokacji|  
|Distmgr.log|Rejestruje szczegółowe informacje o konfiguracji włączania obsługi punktu dystrybucji dla środowiska wykonawczego przed uruchomieniem systemu (PXE).|Serwer systemu lokacji|  
|DriverCatalog.log|Rejestruje szczegółowe informacje o sterownikach urządzeń, które zostały zaimportowane do katalogu sterowników.|Serwer systemu lokacji|  
|mcsisapi.log|Rejestruje informacje o transferze pakietów multiemisji i odpowiedziach na żądania klientów.|Serwer systemu lokacji|  
|mcsexec.log|Sprawdzenie kondycji rekordów, przestrzeń nazw, tworzenia sesji i certyfikatów, sprawdź akcje.|Serwer systemu lokacji|  
|mcsmgr.log|Rejestruje zmiany w konfiguracji, trybu zabezpieczeń i dostępności.|Serwer systemu lokacji|  
|mcsprv.log|Rejestruje interakcję dostawcy multiemisji z Usługami wdrażania systemu Windows (WDS).|Serwer systemu lokacji|  
|MCSSetup.log|Rejestruje szczegółowe informacje o instalacji roli serwera multiemisji.|Serwer systemu lokacji|  
|MCSMSI.log|Rejestruje szczegółowe informacje o instalacji roli serwera multiemisji.|Serwer systemu lokacji|  
|Mcsperf.log|Rejestruje szczegółowe informacje o aktualizacjach liczników wydajności multiemisji.|Serwer systemu lokacji|  
|MP_ClientIDManager.log|Rejestruje odpowiedzi punktu zarządzania na sekwencje zadań z żądaniami identyfikacji klienta inicjowane ze środowiska PXE lub nośnika rozruchowego.|Serwer systemu lokacji|  
|MP_DriverManager.log|Rejestruje odpowiedzi punktu zarządzania na żądania akcji sekwencji zadań Automatycznie zastosuj sterowniki.|Serwer systemu lokacji|  
|OfflineServicingMgr.log|Rejestruje szczegółowe informacje o harmonogramach obsługi w trybie offline i aktualizacji stosuje określone akcje na pliki systemu operacyjnego Windows Imaging Format (WIM).|Serwer systemu lokacji|  
|Setupact.log|Rejestruje szczegóły dotyczące programu Sysprep systemu Windows i dzienników instalatora.|Klient|  
|Setupapi.log|Rejestruje szczegóły dotyczące programu Sysprep systemu Windows i dzienników instalatora.|Klient|  
|Setuperr.log|Rejestruje szczegóły dotyczące programu Sysprep systemu Windows i dzienników instalatora.|Klient|  
|smpisapi.log|Rejestruje szczegółowe informacje o akcjach przechwytywania i przywracania stanu klienta oraz informacje o wartościach progowych.|Klient|  
|Smpmgr.log|Rejestruje szczegółowe informacje o wynikach kontroli kondycji punktu migracji stanu i zmianach konfiguracji.|Serwer systemu lokacji|  
|smpmsi.log|Rejestruje szczegółowe informacje o instalacji i konfiguracji punktu migracji stanu.|Serwer systemu lokacji|  
|smpperf.log|Rejestruje aktualizacje liczników wydajności punktu migracji stanu.|Serwer systemu lokacji|  
|smspxe.log|Rejestruje szczegółowe informacje o odpowiedziach wysyłanych do klientów, którzy używają rozruchu PXE oraz szczegółowe informacje o rozwijaniu obrazów rozruchowych i plików rozruchowych.|Serwer systemu lokacji|  
|smssmpsetup.log|Rejestruje szczegółowe informacje o instalacji i konfiguracji punktu migracji stanu.|Serwer systemu lokacji|  
|Smsts.log|Rejestruje działania sekwencji zadań.|Klient|  
|TSAgent.log|Rejestruje wyniki zależności sekwencji zadań przed jej uruchomieniem.|Klient|  
|TaskSequenceProvider.log|Rejestruje szczegółowe informacje o sekwencjach zadań podczas ich importu, eksportu lub edycji.|Serwer systemu lokacji|  
|loadstate.log|Rejestruje szczegółowe informacje o narzędziu do migracji stanu użytkowników (USMT) i przywracaniu danych o stanie użytkowników.|Klient|  
|scanstate.log|Rejestruje szczegółowe informacje o narzędziu do migracji stanu użytkowników (USMT) i przechwytywaniu danych o stanie użytkowników.|Klient|  

###  <a name="BKMK_PowerMgmtLog"></a>Zarządzanie energią  
 W poniższej tabeli wymieniono pliki dziennika zawierające informacje powiązane z zarządzaniem energią.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|pwrmgmt.log|Rejestruje szczegółowe informacje o działaniach zarządzania energią na komputerze klienckim, w tym monitorowaniu i egzekwowaniu ustawień przez agenta klienta zarządzania energią.|Klient|  

###  <a name="BKMK_RCLog"></a>Zdalne sterowanie  
 W poniższej tabeli wymieniono pliki dziennika zawierające informacje powiązane ze zdalnym sterowaniem.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|CMRcViewer.log|Rejestruje szczegółowe informacje o działaniach podglądu zdalnego sterowania.|W folderze % temp % na komputerze z uruchomionym podglądem zdalnego sterowania|  

###  <a name="BKMK_ReportLog"></a>Raportowanie  
 Poniższa tabela zawiera listę plików dziennika programu Configuration Manager, zawierające informacje powiązane z raportowaniem.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|srsrp.log|Rejestruje informacje o działaniu i stanie punktu usług raportowania.|Serwer systemu lokacji|  
|srsrpMSI.log|Rejestruje szczegółowe wyniki procesu instalacji punktu usług raportowania z danych wyjściowych MSI.|Serwer systemu lokacji|  
|srsrpsetup.log|Rejestruje wyniki procesu instalacji punktu usług raportowania.|Serwer systemu lokacji|  

###  <a name="BKMK_RBALog"></a>Administracja oparta na rolach  
 W poniższej tabeli wymieniono pliki dziennika zawierające informacje powiązane z zarządzaniem administracją opartą na rolach.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|hman.log|Rejestruje informacje o zmianach konfiguracji lokacji i publikowaniu informacji o lokacji w usługach domenowych w usłudze Active Directory.|Serwer lokacji|  
|SMSProv.log|Rejestruje dostęp dostawcy WMI do bazy danych lokacji.|Komputer z dostawcą programu SMS|  

###  <a name="BKMK_WITLog"></a>Punkt połączenia usługi  
 W poniższej tabeli wymieniono pliki dziennika zawierające informacje powiązane z punktem połączenia z usługą.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|CertMgr.log|Rejestruje informacje o certyfikacie i koncie serwera proxy.|Serwer lokacji|  
|CollEval.log|Rejestruje szczegóły dotyczące utworzenia, zmiany i usunięcia kolekcji przez Ewaluatora kolekcji.|Lokacja główna i centralna lokacja administracyjna|  
|Cloudusersync.log|Rejestruje uaktywnianie licencji dla użytkowników.|Komputer z punktem połączenia z usługą|  
|Dataldr.log|Rejestruje informacje o przetwarzaniu plików MIF.|Serwer lokacji|  
|ddm.log|Rejestruje czynności menedżera danych odnajdywania.|Serwer lokacji|  
|Distmgr.log|Rejestruje szczegółowe informacje o żądaniach dystrybucji zawartości.|Sewer lokacji najwyższego poziomu|  
|Dmpdownloader.log|Rejestruje szczegółowe informacje o pobraniach z Microsoft Intune.|Komputer z punktem połączenia z usługą|  
|Dmpuploader.log|Rejestruje szczegółowe informacje dotyczące przekazywania zmian w bazie danych w usłudze Microsoft Intune.|Komputer z punktem połączenia z usługą|  
|hman.log|Rejestruje informacje o przesyłaniu komunikatów dalej.|Serwer lokacji|  
|objreplmgr.log|Rejestruje przetwarzanie zasad i przypisań.|Serwer lokacji głównej|  
|PolicyPV.log|Rejestruje generowanie wszystkich zasad.|Serwer lokacji|  
|outgoingcontentmanager.log|Rejestruje zawartość przekazywaną usłudze Microsoft Intune.|Komputer z punktem połączenia z usługą|  
|Sitecomp.log|Rejestruje szczegółowe informacje o instalacji punktu połączenia z usługą.|Serwer lokacji|  
|SmsAdminUI.log|Rejestruje działanie konsoli programu Configuration Manager.|Komputera, na którym jest uruchomiona konsola programu Configuration Manager|  
|Smsprov.log|Rejestruje działania wykonywane przez dostawcę programu SMS. Dostawca programu SMS korzystają działania konsoli programu Configuration Manager.|Komputer z dostawcą programu SMS|  
|SrvBoot.log|Rejestruje szczegółowe informacje o usłudze instalacji punktu połączenia z usługą.|Komputer z punktem połączenia z usługą|  
|Statesys.log|Rejestruje przetwarzanie komunikatów zarządzania urządzeniami przenośnymi.|Lokacja główna i centralna lokacja administracyjna|  

###  <a name="BKMK_SU_NAPLog"></a>Aktualizacje oprogramowania  
 W poniższej tabeli wymieniono pliki dziennika zawierające informacje dotyczące aktualizacji oprogramowania.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|ccmperf.log|Rejestruje działania powiązane z obsługą i przechwytywaniem danych dotyczących liczników wydajności klienta.|Klient|  
|PatchDownloader.log|Rejestruje szczegółowe informacje o procesie pobierania aktualizacji oprogramowania ze źródła aktualizacji do miejsca docelowego pobierania na serwerze lokacji.|Komputer, który jest hostem konsoli programu Configuration Manager, z której inicjowane jest pobieranie|  
|PolicyEvaluator.log|Rejestruje szczegółowe informacje o ocenie zasad na komputerach klienckich, w tym zasad z aktualizacji oprogramowania.|Klient|  
|RebootCoordinator.log|Rejestruje szczegółowe informacje o koordynacji ponownych uruchomień systemu na komputerach klienckich po instalacjach aktualizacji oprogramowania.|Klient|  
|ScanAgent.log|Rejestruje szczegółowe informacje o żądaniach skanowania pod kątem aktualizacji oprogramowania, lokalizacji WSUS i akcjach powiązanych.|Klient|  
|SdmAgent.log|Rejestruje szczegółowe informacje o śledzeniu korygowania i zgodności. Niemniej jednak plik dziennika aktualizacji oprogramowania, Updateshandler.log, zawiera więcej szczegółowych informacji o instalowaniu aktualizacji oprogramowania, które są wymagane dla zgodności.<br /><br /> Ten plik dziennika jest współużytkowany z ustawieniami zgodności.|Klient|  
|ServiceWindowManager.log|Rejestruje szczegółowe informacje o ocenie okien obsługi.|Klient|  
|SmsWusHandler.log|Rejestruje szczegółowe informacje o procesie skanowania dotyczącym narzędzia stanu zapasów usługi Microsoft Updates.|Klient|  
|StateMessage.log|Rejestruje szczegółowe informacje o oprogramowaniu aktualizacji komunikatów o stanie tworzonych i wysyłanych do punktu zarządzania.|Klient|  
|SUPSetup.log|Rejestruje szczegółowe informacje o instalacji punktu aktualizacji oprogramowania. Po ukończeniu instalacji punktu aktualizacji oprogramowania w tym pliku dziennika zapisywany jest komunikat **Instalacja powiodła się**.|Serwer systemu lokacji|  
|UpdatesDeployment.log|Rejestruje szczegółowe informacje o wdrożeniach na kliencie, w tym o aktywacji, ocenie i wymuszaniu aktualizacji oprogramowania. Pełne rejestrowanie udostępnia dodatkowe informacje o interakcji z interfejsem użytkownika klienta.|Klient|  
|UpdatesHandler.log|Rejestruje szczegółowe informacje o skanowaniu pod kątem zgodności aktualizacji oprogramowania oraz o pobieraniu i instalowaniu aktualizacji oprogramowania na kliencie.|Klient|  
|UpdatesStore.log|Rejestruje szczegółowe informacje o stanie zgodności dla aktualizacji oprogramowania, które zostały ocenione podczas cyklu skanowania pod kątem zgodności.|Klient|  
|WCM.log|Rejestruje szczegółowe informacje o oprogramowaniu aktualizacji konfiguracji i punktu połączenia z serwerem WSUS dotyczące zasubskrybowanych kategorii aktualizacji, klasyfikacji i języków.|Serwer lokacji|  
|WSUSCtrl.log|Rejestruje szczegółowe informacje o konfiguracji, połączeniu z bazą danych i kondycji serwera programu WSUS dla lokacji.|Serwer systemu lokacji|  
|wsyncmgr.log|Rejestruje szczegółowe informacje dotyczące oprogramowania, aktualizacji procesu synchronizacji.|Serwer lokacji|  
|WUAHandler.log|Rejestruje szczegółowe informacje o usłudze Windows Update Agent na kliencie podczas wyszukiwania przez nią aktualizacji oprogramowania.|Klient|  

###  <a name="BKMK_WOLLog"></a>Funkcji Wake On LAN  
 W poniższej tabeli wymieniono pliki dziennika zawierające informacje powiązane z użyciem funkcji Wake On LAN.  

> [!NOTE]  
>  Gdy Wake On LAN można uzupełnić przy użyciu serwera proxy wznawiania, to działanie jest rejestrowane na kliencie. Na przykład Zobacz pliki CcmExec.log i SleepAgent_ <*domeny* \> @SYSTEM_0.log w [operacji klienta](#BKMK_ClientOpLogs) sekcji tego tematu.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|wolcmgr.log|Rejestruje szczegółowe informacje o tym, do których klientów należy wysłać pakiety wznawiania, liczbę wysłanych pakietów wznawiania i liczbę pakietów wznawiania, których próbę wysyłania ponawiano.|Serwer lokacji|  
|wolmgr.log|Rejestruje szczegółowe informacje o procedurach wznawiania, takie jak kiedy wznawiać wdrożenia skonfigurowane pod kątem funkcji Wake On LAN.|Serwer lokacji|  

###  <a name="BKMK_WindowsServicingLog"></a>Obsługa systemu Windows 10  
 W poniższej tabeli wymieniono pliki dziennika zawierające informacje dotyczące obsługi systemu Windows 10.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|ccmperf.log|Rejestruje działania powiązane z obsługą i przechwytywaniem danych dotyczących liczników wydajności klienta.|Klient|  
|CcmRepair.log|Rejestruje działania naprawy agenta klienta.|Klient|
|PatchDownloader.log|Rejestruje szczegółowe informacje o procesie pobierania aktualizacji oprogramowania ze źródła aktualizacji do miejsca docelowego pobierania na serwerze lokacji.|Komputer, który jest hostem konsoli programu Configuration Manager, z której inicjowane jest pobieranie|  
|PolicyEvaluator.log|Rejestruje szczegółowe informacje o ocenie zasad na komputerach klienckich, w tym zasad z aktualizacji oprogramowania.|Klient|  
|RebootCoordinator.log|Rejestruje szczegółowe informacje o koordynacji ponownych uruchomień systemu na komputerach klienckich po instalacjach aktualizacji oprogramowania.|Klient|  
|ScanAgent.log|Rejestruje szczegółowe informacje o żądaniach skanowania pod kątem aktualizacji oprogramowania, lokalizacji WSUS i akcjach powiązanych.|Klient|  
|SdmAgent.log|Rejestruje szczegółowe informacje o śledzeniu korygowania i zgodności. Niemniej jednak plik dziennika aktualizacji oprogramowania, UpdatesHandler.log, zawiera więcej szczegółowych informacji o instalowaniu aktualizacji oprogramowania, które są wymagane dla zgodności.<br /><br /> Ten plik dziennika jest współużytkowany z ustawieniami zgodności.|Klient|  
|ServiceWindowManager.log|Rejestruje szczegółowe informacje o ocenie okien obsługi.|Klient|  
|Setupact.log|Podstawowego pliku dziennika większość błędów występujących podczas instalacji systemu Windows. Plik dziennika znajduje się w folderze % windir %\$Windows.~BT\sources\panther folder.|Klient|
|SmsWusHandler.log|Rejestruje szczegółowe informacje o procesie skanowania dotyczącym narzędzia stanu zapasów usługi Microsoft Updates.|Klient|  
|StateMessage.log|Rejestruje szczegółowe informacje o komunikatach o stanie aktualizacji oprogramowania tworzonych i wysyłanych do punktu zarządzania.|Klient|  
|SUPSetup.log|Rejestruje szczegółowe informacje o instalacji punktu aktualizacji oprogramowania. Po ukończeniu instalacji punktu aktualizacji oprogramowania w tym pliku dziennika zapisywany jest komunikat **Instalacja powiodła się**.|Serwer systemu lokacji|  
|UpdatesDeployment.log|Rejestruje szczegółowe informacje o wdrożeniach na kliencie, w tym o aktywacji, ocenie i wymuszaniu aktualizacji oprogramowania. Pełne rejestrowanie udostępnia dodatkowe informacje o interakcji z interfejsem użytkownika klienta.|Klient|  
|Updateshandler.log|Rejestruje szczegółowe informacje o skanowaniu pod kątem zgodności aktualizacji oprogramowania oraz o pobieraniu i instalowaniu aktualizacji oprogramowania na kliencie.|Klient|  
|UpdatesStore.log|Rejestruje szczegółowe informacje o stanie zgodności dla aktualizacji oprogramowania, które zostały ocenione podczas cyklu skanowania pod kątem zgodności.|Klient|  
|WCM.log|Rejestruje szczegółowe informacje o oprogramowaniu aktualizacji konfiguracji i punktu połączenia z serwerem WSUS dotyczące zasubskrybowanych kategorii aktualizacji, klasyfikacji i języków.|Serwer lokacji|  
|WSUSCtrl.log|Rejestruje szczegółowe informacje o konfiguracji, połączeniu z bazą danych i kondycji serwera programu WSUS dla lokacji.|Serwer systemu lokacji|  
|wsyncmgr.log|Rejestruje szczegółowe informacje dotyczące oprogramowania, aktualizacji procesu synchronizacji.|Serwer lokacji|  
|WUAHandler.log|Rejestruje szczegółowe informacje o usłudze Windows Update Agent na kliencie podczas wyszukiwania przez nią aktualizacji oprogramowania.|Klient|  

###  <a name="BKMK_WULog"></a>Usługa Windows Update Agent  
 W poniższej tabeli wymieniono pliki dziennika zawierające informacje powiązane z programem Windows Update Agent.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|WindowsUpdate.log|Rejestruje szczegółowe informacje o Kiedy Windows Update Agent łączy się z serwerem WSUS i pobiera aktualizacje oprogramowania w celu oceny zgodności i czy są dostępne aktualizacje składników agenta.|Klient|  

###  <a name="BKMK_WSUSLog"></a>Serwer WSUS  
 W poniższej tabeli wymieniono pliki dziennika zawierające informacje powiązane z serwerem WSUS.  

|Nazwa dziennika|Opis|Komputer z plikiem dziennika|  
|--------------|-----------------|----------------------------|  
|Change.log|Rejestruje szczegółowe informacje o serwerze programu WSUS bazy danych informacje, które uległy zmianie.|Serwer WSUS|  
|SoftwareDistribution.log|Rejestruje szczegółowe informacje o aktualizacjach oprogramowania, które są zsynchronizowane ze skonfigurowanego źródła aktualizacji do bazy danych serwera WSUS.|Serwer WSUS|  

