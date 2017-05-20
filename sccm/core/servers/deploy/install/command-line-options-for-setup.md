---
title: Opcje wiersza polecenia Instalatora | Dokumentacja firmy Microsoft
description: "Użyj informacje w tym artykule skonfigurować skrypty lub do zainstalowania programu System Center Configuration Manager z wiersza polecenia."
ms.custom: na
ms.date: 03/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0da167f1-52cf-4dfd-8f73-833ca3eb8478
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 04fe7b3e674287c4255563ab4a308e54d0b6c3aa
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="command-line-options-for-setup-in-system-center-configuration-manager"></a>Opcje wiersza polecenia instalacji w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


 Użyj poniższych informacji, aby skonfigurować skrypty lub do zainstalowania programu System Center Configuration Manager z wiersza polecenia.  

##  <a name="bkmk_setup"></a>Opcje wiersza polecenia Instalatora  
 **/ DEINSTALL**  
 Odinstalowanie lokacji. Należy uruchomić Instalatora z komputera serwera lokacji.  

 **/ DONTSTARTSITECOMP**  
 Instaluje lokację, lecz zapobiega uruchomieniu usługi Menedżer składników lokacji. Do momentu uruchomienia usługi Menedżera składników lokacji lokacja będzie nieaktywna. Menedżer składników lokacji jest odpowiedzialny za instalację i uruchomienie usługi SMS_Executive oraz dodatkowych procesów w lokacji. Po zakończeniu instalacji lokacji, po uruchomieniu usługi Menedżer składników lokacji, instaluje usługi SMS_Executive oraz dodatkowych procesów, które są niezbędne do funkcjonowania lokacji.  

 **/ UKRYTE**  
 Służy do ukrycia interfejsu użytkownika podczas instalacji. Użyj tej opcji tylko w połączeniu z **/SCRIPT** opcji. Plik skryptu instalacji nienadzorowanej musi zawierać wszystkie wymagane opcje lub instalacja nie powiedzie się.  

 **/ NOUSERINPUT**  
 Wyłącza dane wejściowe użytkownika podczas instalacji, ale wyświetla Kreatora instalacji. Użyj tej opcji tylko w połączeniu z **/SCRIPT** opcji. Plik skryptu instalacji nienadzorowanej musi zawierać wszystkie wymagane opcje lub instalacja nie powiedzie się.  

 **/ RESETSITE**  
 Wykonuje lokacji resetowania powodującego zresetowanie bazy danych oraz kont usług lokacji. Należy uruchomić Instalatora z  **<* ścieżkę instalacji programu Configuration Manager*> \BIN\X64** na serwerze lokacji. Aby uzyskać więcej informacji na temat resetowania lokacji, zobacz [Uruchom reset lokacji](../../../../core/servers/manage/modify-your-infrastructure.md#bkmk_reset) w sekcji [zmodyfikować infrastruktury programu System Center Configuration Manager](../../../../core/servers/manage/modify-your-infrastructure.md).  

 **/ TESTDBUPGRADE <*nazwa wystąpienia*>\\<*Nazwa bazy danych*>**  
 Służy do wykonania testu na kopii zapasowej bazy danych lokacji w celu zapewnienia można przeprowadzić uaktualnienie bazy danych. Należy podać nazwę wystąpienia i nazwę bazy danych dla bazy danych lokacji. Jeśli określisz nazwę bazy danych Instalator użyje domyślnej nazwy wystąpienia.  

> [!IMPORTANT]  
>  Nie wolno uruchamiać tej opcji wiersza polecenia w produkcyjnej bazy danych lokacji. Uruchamianie tej opcji wiersza polecenia w produkcyjnej bazy danych lokacji uaktualnienie bazy danych lokacji i może przestać witryny.  

 **/ UPGRADE**  
 Uruchamia do przeprowadzenia nienadzorowanego uaktualnienia lokacji. Kiedy używasz **/UPGRADE**, należy określić klucz produktu, łącznie z myślnikami (-). Ponadto należy określić ścieżkę do uprzednio pobranych wstępnie wymaganych plików instalacji.  

 Przykład: `setupwpf.exe /UPGRADE xxxxx-xxxxx-xxxxx-xxxxx-xxxxx <path to external component files>`  

 Aby uzyskać więcej informacji na temat plików wymagań wstępnych instalacji, zobacz [Narzędzie pobierania Instalatora](setup-downloader.md).  

 **/ SCRIPT <*ścieżka skryptu Instalatora*>**  
 Służy do przeprowadzenia instalacji nienadzorowanej. Plik inicjujący Instalatora jest wymagany w przypadku używania **/SCRIPT** opcji. Aby uzyskać więcej informacji na temat uruchamiania instalacji nienadzorowanej, zobacz [pobranych przy użyciu wiersza polecenia](../../../../core/servers/deploy/install/use-a-command-line-to-install-sites.md).  

 **/ SDKINST <*dostawcy programu SMS w pełni kwalifikowaną nazwę domeny*>**  
 Instaluje dostawcę programu SMS na określonym komputerze. Należy podać w pełni kwalifikowaną nazwę domeny (FQDN) komputera dostawcy programu SMS. Aby uzyskać więcej informacji na temat dostawcy programu SMS, zobacz [planowanie dostawcy programu SMS dla programu System Center Configuration Manager](../../../../core/plan-design/hierarchy/plan-for-the-sms-provider.md).  

 **/ SDKDEINST <*dostawcy programu SMS w pełni kwalifikowaną nazwę domeny*>**  
 Służy do odinstalowania dostawcy programu SMS na określonym komputerze. Należy podać nazwę FQDN komputera dostawcy programu SMS.  

 **/ MANAGELANGS <*ścieżka skryptu języka*>**  
 Służy do zarządzania językami zainstalowanymi w uprzednio zainstalowanej lokacji. Aby użyć tej opcji, należy uruchomić Instalatora z  **<* ścieżkę instalacji programu Configuration Manager*> \BIN\X64** na serwerze lokacji i podać lokalizację pliku skryptu języka zawierającego ustawienia języka. Aby uzyskać więcej informacji na temat dostępnych opcji języka w pliku skryptu Instalatora języka, zobacz [opcji wiersza polecenia do zarządzania językami](#bkmk_Lang) w tym temacie.  

##  <a name="bkmk_Lang"></a>Opcje wiersza polecenia do zarządzania językami  
 **Identyfikacja**  

-   **Nazwa klucza:** Akcja  

    -   **Wymagane:** Tak  

    -   **Wartości:** ManageLanguages  

    -   **Szczegóły:** Zarządza serwer, klient i obsługa języków klientów urządzeń przenośnych w lokacji.  

**Opcje**  

-   **Nazwa klucza:** AddServerLanguages  

    -   **Wymagane:** Nie  

    -   **Wartości:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK lub ZHH  

    -   **Szczegóły:** Określa języki serwera, które będą dostępne dla konsoli programu Configuration Manager, raporty i obiektów programu Configuration Manager. Język angielski jest dostępny domyślnie.  

-   **Nazwa klucza:** AddClientLanguages  

    -   **Wymagane:** Nie  

    -   **Wartości:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK lub ZHH  

    -   **Szczegóły:** Określa języki, które będą dostępne na komputerach klienckich. Język angielski jest dostępny domyślnie.  

-   **Nazwa klucza:** DeleteServerLanguages  

    -   **Wymagane:** Nie  

    -   **Wartości:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK lub ZHH  

    -   **Szczegóły:** Określa języki do usunięcia, a które nie będzie już dostępny dla konsoli programu Configuration Manager, raporty i obiektów programu Configuration Manager. Język angielski jest dostępny domyślnie i nie można go usunąć.  

-   **Nazwa klucza:** DeleteClientLanguages  

    -   **Wymagane:** Nie  

    -   **Wartości:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK lub ZHH  

    -   **Szczegóły:** Określa języki do usunięcia, a które nie będzie już dostępne na komputerach klienckich. Język angielski jest dostępny domyślnie i nie można go usunąć.  

-   **Nazwa klucza:** MobileDeviceLanguage  

    -   **Wymagane:** Tak  

    -   **Wartości:** 0 lub 1  

         0 = nie instaluj  

         1 = instalacji  

    -   **Szczegóły:** Określa, czy mają zostać zainstalowane języki klienta urządzenia przenośnego.  

-   **Nazwa klucza:** PrerequisiteComp  

    -   **Wymagane:** Tak  

    -   **Wartości:** 0 lub 1  

         0 = pobierania  

         1 = już pobrane  

    -   **Szczegóły:** Określa, czy pliki wymagań wstępnych Instalatora zostały już pobrane. Na przykład, jeśli używasz wartość **0**, Instalator pobierze pliki.  

-   **Nazwa klucza:** PrerequisitePath  

    -   **Wymagane:** Tak  

    -   **Wartości:** <*ścieżkę do plików wymagań wstępnych instalacji*>  

    -   **Szczegóły:** Określa ścieżkę do plików wymagań wstępnych Instalatora. W zależności od wartości **PrerequisiteComp** Instalator używa tej ścieżki do przechowywania pobranych plików lub lokalizowania wcześniej pobranych plików.  

##  <a name="bkmk_Unattended"></a>Klucze plików skryptu instalacji nienadzorowanej  
 Użyj następujące sekcje zawierają informacje pomocne w tworzeniu skryptu instalacji nienadzorowanej. Listy Pokaż dostępnych kluczy skryptu instalacji, odpowiadające im wartości, czy są one wymagane, jakiego typu instalację służą one do realizacji i krótki opis klucza.  

### <a name="unattended-install-for-a-central-administration-site"></a>Instalacji nienadzorowanej dla witryny administracji centralnej  
 Następujące informacje należy zainstalować centralnej lokacji administracyjnej przy użyciu pliku instalacji nienadzorowanej.  

**Identyfikacja**  

-   **Nazwa klucza:** Akcja  

    -   **Wymagane:** Tak  

    -   **Wartości:** InstallCAS  

    -   **Szczegóły:** Instaluje lokację administracji centralnej.  

-   **Nazwa klucza:** CDLatest  

    -   **Wymagane:** Tak — tylko w przypadku używania nośnika z dysku CD. Najnowszy folder.    

    -   **Wartości:** 1 wartości innej niż 1 jest uważany za nie można przy użyciu dysku CD. Najnowsze.

    -   **Szczegóły:** Skrypt musi zawierać ten klucz i wartość po uruchomieniu Instalatora z nośnika na dysku CD. Najnowsze folderu na potrzeby instalowania lokacji głównej lub centralnej administracji lub odzyskiwania lokacji głównej lub centralnej administracji. Ta wartość informuje Instalatora że nośnik tworzą dysku CD. R jest używany.

**Opcje**  

-   **Nazwa klucza:** Identyfikator produktu  

    -   **Wymagane:** Tak  

    -   **Wartości:** <*xxxxx-xxxxx-xxxxx-xxxxx-xxxxx*> *lub* Eval  

    -   **Szczegóły:** Określa klucz produktu instalacji programu Configuration Manager, wraz z kreskami. Wprowadź **Eval** zainstalować wersję ewaluacyjną programu Configuration Manager.  

-   **Nazwa klucza:** Kod lokacji  

    -   **Wymagane:** Tak  

    -   **Wartości:** <*kod lokacji*>  

    -   **Szczegóły:** Określa trzy znaki alfanumeryczne, które jednoznacznie identyfikują lokację w hierarchii.  

-   **Nazwa klucza:** Nazwa witryny  

    -   **Wymagane:** Tak  

    -   **Wartości:** <*Nazwa lokacji*>  

    -   **Szczegóły:** Określa nazwę dla tej lokacji.  

-   **Nazwa klucza:** SMSInstallDir  

    -   **Wymagane:** Tak  

    -   **Wartości:** <*ścieżkę instalacji programu Configuration Manager*>  

    -   **Szczegóły:** Określa folder instalacji plików programu Configuration Manager.  

-   **Nazwa klucza:** SDKServer  

    -   **Wymagane:** Tak  

    -   **Wartości:** <*dostawcy programu SMS w pełni kwalifikowaną nazwę domeny*>  

    -   **Szczegóły:** Określa nazwę FQDN serwera, który będzie hostem dostawcy programu SMS. Po instalacji początkowej możesz skonfigurować dodatkowych dostawców programu SMS dla lokacji.  

-   **Nazwa klucza:** PrerequisiteComp  

    -   **Wymagane:** Tak  

    -   **Wartości:** 0 lub 1  

         0 = pobierania  

         1 = już pobrane  

    -   **Szczegóły:** Określa, czy pliki wymagań wstępnych Instalatora zostały już pobrane. Na przykład, jeśli używasz wartość **0**, Instalator pobierze pliki.  

-   **Nazwa klucza:** PrerequisitePath  

    -   **Wymagane:** Tak  

    -   **Wartości:** <*ścieżkę do plików wymagań wstępnych instalacji*>  

    -   **Szczegóły:** Określa ścieżkę do plików wymagań wstępnych Instalatora. W zależności od wartości **PrerequisiteComp** Instalator używa tej ścieżki do przechowywania pobranych plików lub lokalizowania wcześniej pobranych plików.  

-   **Nazwa klucza:** AdminConsole  

    -   **Wymagane:** Tak  

    -   **Wartości:** 0 lub 1  

         0 = nie instaluj  

         1 = instalacji  

    -   **Szczegóły:** Określa, czy należy zainstalować konsolę programu Configuration Manager.  

-   **Nazwa klucza:** JoinCEIP  

    -   **Wymagane:** Tak  

    -   **Wartości:** 0 lub 1  

         0 = nie dołączaj  

         1 = sprzężenia  

    -   **Szczegóły:** Określa, czy dołączyć do programu poprawy jakości obsługi klienta (CEIP).  

-   **Nazwa klucza:** AddServerLanguages  

    -   **Wymagane:** Nie  

    -   **Wartości:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK lub ZHH  

    -   **Szczegóły:** Określa języki serwera, które będą dostępne dla konsoli programu Configuration Manager, raporty i obiektów programu Configuration Manager. Język angielski jest dostępny domyślnie.  

-   **Nazwa klucza:** AddClientLanguages  

    -   **Wymagane:** Nie  

    -   **Wartości:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK lub ZHH  

    -   **Szczegóły:** Określa języki, które będą dostępne na komputerach klienckich. Język angielski jest dostępny domyślnie.  

-   **Nazwa klucza:** DeleteServerLanguages  

    -   **Wymagane:** Nie  

    -   **Wartości:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK lub ZHH  

    -   **Szczegóły:** Modyfikuje lokację po jej zainstalowaniu. Określa języki do usunięcia, a które nie będzie już dostępny dla konsoli programu Configuration Manager, raporty i obiektów programu Configuration Manager. Język angielski jest dostępny domyślnie i nie można go usunąć.  

-   **Nazwa klucza:** DeleteClientLanguages  

    -   **Wymagane:** Nie  

    -   **Wartości:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK lub ZHH  

    -   **Szczegóły:** Modyfikuje lokację po jej zainstalowaniu. Określa języki do usunięcia, a które nie będzie już dostępne na komputerach klienckich. Język angielski jest dostępny domyślnie i nie można go usunąć.  

-   **Nazwa klucza:** MobileDeviceLanguage  

    -   **Wymagane:** Tak  

    -   **Wartości:** 0 lub 1  

         0 = nie instaluj  

         1 = instalacji  

    -   **Szczegóły:** Określa, czy mają zostać zainstalowane języki klienta urządzenia przenośnego.  

**SQLConfigOptions**  

-   **Nazwa klucza:** SQLServerName  

    -   **Wymagane:** Tak  

    -   **Wartości:** <*nazwa serwera SQL*>  

    -   **Szczegóły:** Określa nazwę serwera lub klastrowanego wystąpienia, w którym jest uruchomiony program SQL Server i który będzie hostem bazy danych lokacji.  

-   **Nazwa klucza:** DatabaseName  

    -   **Wymagane:** Tak  

    -   **Wartości:** <*Nazwa bazy danych lokacji*> lub <*nazwa wystąpienia*>\\<*Nazwa bazy danych lokacji*>  

    -   **Szczegóły:** Określa nazwę bazy danych programu SQL Server do utworzenia lub bazy danych programu SQL Server do użycia podczas instalowania bazy danych witryny Administracja centralna.  

        > [!IMPORTANT]  
        >  Jeżeli nie używasz domyślnego wystąpienia, należy określić nazwy wystąpienia i lokacji.  

-   **Nazwa klucza:** SQLSSBPort  

    -   **Wymagane:** Nie  

    -   **Wartości:** <*numer portu SSB*>  

    -   **Szczegóły:** Określa port usługi SQL Server Service Broker (SSB) używany przez program SQL Server. SSB zazwyczaj jest skonfigurowany do używania portu TCP 4022, ale można użyć innego portu.  

-   **Nazwa klucza:** SQLDataFilePath  

    -   **Wymagane:** Nie  

    -   **Wartości:** <*ścieżkę do pliku MDB bazy danych*>  

    -   **Szczegóły:** Określa alternatywną lokalizację do utworzenia pliku MDB bazy danych.  

-   **Nazwa klucza:** SQLLogFilePath  

    -   **Wymagane:** Nie  

    -   **Wartości:** <*ścieżkę do pliku .ldf bazy danych*>  

    -   **Szczegóły:** Określa alternatywną lokalizację do utworzenia pliku .ldf bazy danych.  

**CloudConnectorOptions**  

-   **Nazwa klucza:** CloudConnector  

    -   **Wymagane:** Tak  

    -   **Wartości:** 0 lub 1  

         0 = nie instaluj  

         1 = instalacji  

    -   **Szczegóły:** Określa, czy zainstalować punktu połączenia usługi w tej lokacji. Ponieważ punktu połączenia usługi można zainstalować tylko w lokacji najwyższego poziomu w hierarchii, ta wartość musi być **0** dla podrzędnej lokacji głównej.  

-   **Nazwa klucza:** CloudConnectorServer  

    -   **Wymagane:** Wymagany, gdy **CloudConnector** jest równe 1  

    -   **Wartości:** <*nazwa FQDN serwera punktu połączenia usługi*>  

    -   **Szczegóły:** Określa nazwę FQDN serwera obsługującego rolę systemu lokacji punktu połączenia usługi.  

-   **Nazwa klucza:** UseProxy  

    -   **Wymagane:** Wymagany, gdy **CloudConnector** jest równe 1  

    -   **Wartości:** 0 lub 1  

         0 = nie instaluj  

         1 = instalacji  

    -   **Szczegóły:** Określa, czy punkt połączenia usługi będzie używać serwera proxy.  

-   **Nazwa klucza:** ProxyName  

    -   **Wymagane:** Wymagany, gdy **UseProxy** jest równe 1  

    -   **Wartości:** <*nazwa FQDN serwera Proxy*>  

    -   **Szczegóły:** Określa nazwę FQDN serwera proxy, który będzie używany przez rolę systemu lokacji punktu połączenia usługi.  

-   **Nazwa klucza:** ProxyPort  

    -   **Wymagane:** Wymagany, gdy **UseProxy** jest równe 1  

    -   **Wartości:** <*numer portu*>  

    -   **Szczegóły:** Określa numer portu używany do portu serwera proxy.  

### <a name="unattended-install-for-a-primary-site"></a>Instalacji nienadzorowanej dla lokacji głównej  
Następujące informacje należy zainstalować lokacji głównej przy użyciu pliku instalacji nienadzorowanej.  

**Identyfikacja**  

-   **Nazwa klucza:** Akcja  

    -   **Wymagane:** Tak  

    -   **Wartości:** InstallPrimarySite  

    -   **Szczegóły:** Instaluje lokację główną.  

-   **Nazwa klucza:** CDLatest  

    -   **Wymagane:** Tak — tylko w przypadku używania nośnika z dysku CD. Najnowszy folder.    

    -   **Wartości:** 1 wartości innej niż 1 jest uważany za nie można przy użyciu dysku CD. Najnowsze.

    -   **Szczegóły:** Skrypt musi zawierać ten klucz i wartość po uruchomieniu Instalatora z nośnika na dysku CD. Najnowsze folderu na potrzeby instalowania lokacji głównej lub centralnej administracji lub odzyskiwania lokacji głównej lub centralnej administracji. Ta wartość informuje Instalatora że nośnik tworzą dysku CD. R jest używany.

**Opcje**  

-   **Nazwa klucza:** Identyfikator produktu  

    -   **Wymagane:** Tak  

    -   **Wartości:** <*xxxxx-xxxxx-xxxxx-xxxxx-xxxxx*> *lub* Eval  

    -   **Szczegóły:** Określa klucz produktu instalacji programu Configuration Manager, wraz z kreskami. Wprowadź **Eval** zainstalować wersję ewaluacyjną programu Configuration Manager.  

-   **Nazwa klucza:** Kod lokacji  

    -   **Wymagane:** Tak  

    -   **Wartości:** <*kod lokacji*>  

    -   **Szczegóły:** Określa trzy znaki alfanumeryczne, które jednoznacznie identyfikują lokację w hierarchii.  

-   **Nazwa klucza:** Nazwa witryny  

    -   **Wymagane:** Tak  

    -   **Wartości:** <*Nazwa lokacji*>  

    -   **Szczegóły:** Określa nazwę dla tej lokacji.  

-   **Nazwa klucza:** SMSInstallDir  

    -   **Wymagane:** Tak  

    -   **Wartości:** <*ścieżkę instalacji programu Configuration Manager*>

    -   **Szczegóły:** Określa folder instalacji plików programu Configuration Manager.  

-   **Nazwa klucza:** SDKServer  

    -   **Wymagane:** Tak  

    -   **Wartości:** <*dostawcy programu SMS w pełni kwalifikowaną nazwę domeny*>  

    -   **Szczegóły:** Określa nazwę FQDN serwera, który będzie hostem dostawcy programu SMS. Po instalacji początkowej możesz skonfigurować dodatkowych dostawców programu SMS dla lokacji.  

-   **Nazwa klucza:** PrerequisiteComp  

    -   **Wymagane:** Tak  

    -   **Wartości:** 0 lub 1  

         0 = pobierania  

         1 = już pobrane  

    -   **Szczegóły:** Określa, czy pliki wymagań wstępnych Instalatora zostały już pobrane. Na przykład, jeśli używasz wartość **0**, Instalator pobierze pliki.  

-   **Nazwa klucza:** PrerequisitePath  

    -   **Wymagane:** Tak  

    -   **Wartości:** <*ścieżkę do plików wymagań wstępnych instalacji*>  

    -   **Szczegóły:** Określa ścieżkę do plików wymagań wstępnych Instalatora. W zależności od wartości **PrerequisiteComp** Instalator używa tej ścieżki do przechowywania pobranych plików lub lokalizowania wcześniej pobranych plików.  

-   **Nazwa klucza:** AdminConsole  

    -   **Wymagane:** Tak  

    -   **Wartości:** 0 lub 1  

         0 = nie instaluj  

         1 = instalacji  

    -   **Szczegóły:** Określa, czy należy zainstalować konsolę programu Configuration Manager.  

-   **Nazwa klucza:** JoinCEIP  

    -   **Wymagane:** Tak  

    -   **Wartości:** 0 lub 1  

         0 = nie dołączaj  

         1 = sprzężenia  

    -   **Szczegóły:** Określa, czy dołączyć do programu CEIP.  

-   **Nazwa klucza:** ManagementPoint  

    -   **Wymagane:** Nie  

    -   **Wartości:** <*nazwa FQDN serwera lokacji punktu zarządzania*>  

    -   **Szczegóły:** Określa nazwę FQDN serwera obsługującego rolę systemu lokacji punktu zarządzania.  

-   **Nazwa klucza:** ManagementPointProtocol  

    -   **Wymagane:** Nie  

    -   **Wartości:** HTTPS *lub* HTTP  

    -   **Szczegóły:** Określa protokół używany do punktu zarządzania.  

-   **Nazwa klucza:** W Krakowie  

    -   **Wymagane:** Nie  

    -   **Wartości:** <*nazwa FQDN serwera lokacji punktu dystrybucji*>  

    -   **Szczegóły:** Określa protokół używany do punktu dystrybucji.  

-   **Nazwa klucza:** DistributionPointProtocol  

    -   **Wymagane:** Nie  

    -   **Wartości:** HTTPS *lub* HTTP  

    -   **Szczegóły:** Określa protokół używany do punktu dystrybucji.  

-   **Nazwa klucza:** RoleCommunicationProtocol  

    -   **Wymagane:** Tak  

    -   **Wartości:** EnforceHTTPS *lub* HTTPorHTTPS  

    -   **Szczegóły:** Określa, czy skonfigurować wszystkie systemy lokacji, aby akceptowały wyłącznie komunikację HTTPS od klientów lub metoda komunikacji ma być skonfigurowana dla poszczególnych ról systemu lokacji. Po wybraniu do **EnforceHTTPS**, komputer kliencki musi mieć prawidłowy infrastruktury kluczy publicznych (PKI) certyfikatu uwierzytelniania klienta.  

-   **Nazwa klucza:** ClientsUsePKICertificate  

    -   **Wymagane:** Tak  

    -   **Wartości:** 0 lub 1  

         0 = nie używaj  

         1 = użyj  

    -   **Szczegóły:** Określa, czy klienci będą używać certyfikatu PKI klienta do komunikacji z rolami systemu lokacji.  

-   **Nazwa klucza:** AddServerLanguages  

    -   **Wymagane:** Nie  

    -   **Wartości:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK lub ZHH  

    -   **Szczegóły:** Określa języki serwera, które będą dostępne dla konsoli programu Configuration Manager, raporty i obiektów programu Configuration Manager. Język angielski jest dostępny domyślnie.  

-   **Nazwa klucza:** AddClientLanguages  

    -   **Wymagane:** Nie  

    -   **Wartości:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK lub ZHH  

    -   **Szczegóły:** Określa języki, które będą dostępne na komputerach klienckich. Język angielski jest dostępny domyślnie.  

-   **Nazwa klucza:** DeleteServerLanguages  

    -   **Wymagane:** Nie  

    -   **Wartości:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK lub ZHH  

    -   **Szczegóły:** Modyfikuje lokację po jej zainstalowaniu. Określa języki do usunięcia, a które nie będzie już dostępny dla konsoli programu Configuration Manager, raporty i obiektów programu Configuration Manager. Język angielski jest dostępny domyślnie i nie można go usunąć.  

-   **Nazwa klucza:** DeleteClientLanguages  

    -   **Wymagane:** Nie  

    -   **Wartości:** DEU, FRA, RUS, CHS, JPN, CHT, CSY, ESN, HUN, ITA, KOR, NLD, PLK, PTB, PTG, SVE, TRK lub ZHH  

    -   **Szczegóły:** Modyfikuje lokację po jej zainstalowaniu. Określa języki do usunięcia, a które nie będzie już dostępne na komputerach klienckich. Język angielski jest dostępny domyślnie i nie można go usunąć.  

-   **Nazwa klucza:** MobileDeviceLanguage  

    -   **Wymagane:** Tak  

    -   **Wartości:** 0 lub 1  

         0 = nie instaluj  

         1 = instalacji  

    -   **Szczegóły:** Określa, czy mają zostać zainstalowane języki klienta urządzenia przenośnego.  

**SQLConfigOptions**  

-   **Nazwa klucza:** SQLServerName  

    -   **Wymagane:** Tak  

    -   **Wartości:** <*nazwa serwera SQL*>  

    -   **Szczegóły:** Określa nazwę serwera lub klastrowanego wystąpienia, w którym jest uruchomiony program SQL Server i który będzie hostem bazy danych lokacji.  

-   **Nazwa klucza:** DatabaseName  

    -   **Wymagane:** Tak  

    -   **Wartości:** <*Nazwa bazy danych lokacji*> lub <*nazwa wystąpienia*>\\<*Nazwa bazy danych lokacji*>  

    -   **Szczegóły:** Określa nazwę bazy danych programu SQL Server do utworzenia lub bazy danych programu SQL Server do użycia podczas instalowania bazy danych lokacji głównej.  

        > [!IMPORTANT]  
        >  Jeżeli nie używasz domyślnego wystąpienia, należy określić nazwy wystąpienia i lokacji.  

-   **Nazwa klucza:** SQLSSBPort  

    -   **Wymagane:** Nie  

    -   **Wartości:** <*numer portu SSB*>  

    -   **Szczegóły:** Określa port SSB, który używa programu SQL Server. SSB zazwyczaj jest skonfigurowany do używania portu TCP 4022, ale można użyć innego portu.  

-   **Nazwa klucza:** SQLDataFilePath  

    -   **Wymagane:** Nie  

    -   **Wartości:** <*ścieżkę do pliku MDB bazy danych*>  

    -   **Szczegóły:** Określa alternatywną lokalizację do utworzenia pliku MDB bazy danych.  

-   **Nazwa klucza:** SQLLogFilePath  

    -   **Wymagane:** Nie  

    -   **Wartości:** <*ścieżkę do pliku .ldf bazy danych*>  

    -   **Szczegóły:** Określa alternatywną lokalizację do utworzenia pliku .ldf bazy danych.  

**HierarchyExpansionOption**  

-   **Nazwa klucza:** CCARSiteServer  

    -   **Wymagane:** Nie  

    -   **Wartości:** <*witryny Administracja centralna w pełni kwalifikowaną nazwę domeny*>  

    -   **Szczegóły:** Określa, który po dołączeniu hierarchii programu Configuration Manager wstawi do lokacji głównej witryny administracji centralnej. Podczas instalacji, należy określić witryny administracji centralnej.  

-   **Nazwa klucza:** CASRetryInterval  

    -   **Wymagane:** Nie  

    -   **Wartości:** <*Interval*>  

    -   **Szczegóły:** Określa interwał ponawiania prób (w minutach) prób połączenia z witryną Administracja centralna, po niepowodzeniu. Na przykład, jeśli połączenie z centralnej lokacji administracyjnej nie powiedzie się, lokacji głównej czeka liczbę minut, które określisz dla **CASRetryInterval** wartości, a następnie ponowne próby nawiązania połączenia.  

-   **Nazwa klucza:** WaitForCASTimeout  

    -   **Wymagane:** Nie  

    -   **Wartości:** <*Timeout*>  

         Wartość **0** do **100**  

    -   **Szczegóły:** Określa maksymalną wartość limitu czasu (w minutach) dla lokacji głównej połączyć się z witryną Administracja centralna. Na przykład, jeśli lokacji głównej nie może połączyć się z witryną Administracja centralna, lokacja główna ponowi próbę połączenia witryny administracji centralnej, na podstawie **CASRetryInterval** wartości do **WaitForCASTimeout** czasu. Można określić wartość **0** do **100**.  

**CloudConnectorOptions**  

-   **Nazwa klucza:** CloudConnector  

    -   **Wymagane:** Tak  

    -   **Wartości:** 0 lub 1  

         0 = nie instaluj  

         1 = instalacji  

    -   **Szczegóły:** Określa, czy zainstalować punktu połączenia usługi w tej lokacji. Ponieważ punktu połączenia usługi można zainstalować tylko w lokacji najwyższego poziomu w hierarchii, ta wartość musi być **0** dla podrzędnej lokacji głównej.  

-   **Nazwa klucza:** CloudConnectorServer  

    -   **Wymagane:** Wymagany, gdy **CloudConnector** jest równe 1  

    -   **Wartości:** <*nazwa FQDN serwera punktu połączenia usługi*\>  

    -   **Szczegóły:** Określa nazwę FQDN serwera obsługującego rolę systemu lokacji punktu połączenia usługi.  

-   **Nazwa klucza:** UseProxy  

    -   **Wymagane:** Wymagany, gdy **CloudConnector** jest równe 1  

    -   **Wartości:** 0 lub 1  

         0 = nie instaluj  

         1 = instalacji  

    -   **Szczegóły:** Określa, czy punkt połączenia usługi będzie używać serwera proxy.  

-   **Nazwa klucza:** ProxyName  

    -   **Wymagane:** Wymagany, gdy **UseProxy** jest równe 1  

    -   **Wartości:** <*nazwa FQDN serwera Proxy*>  

    -   **Szczegóły:** Określa nazwę FQDN serwera proxy, który będzie używany przez rolę systemu lokacji punktu połączenia usługi.  

-   **Nazwa klucza:** ProxyPort  

    -   **Wymagane:** Wymagany, gdy **UseProxy** jest równe 1  

    -   **Wartości:** <*numer portu*>  

    -   **Szczegóły:** Określa numer portu używany do portu serwera proxy.  

### <a name="unattended-recovery-for-a-central-administration-site"></a>Nienadzorowane Odzyskiwanie witryny Administracja centralna  
 Użyj następujące szczegóły do odzyskiwania centralnej lokacji administracyjnej przy użyciu pliku instalacji nienadzorowanej.  

**Identyfikacja**  

-   **Nazwa klucza:** Akcja  

    -   **Wymagane:** Tak  

    -   **Wartości:** RecoverCCAR  

    -   **Szczegóły:** Odzyskuje lokację administracji centralnej.  

-   **Nazwa klucza:** CDLatest  

    -   **Wymagane:** Tak — tylko w przypadku używania nośnika z dysku CD. Najnowszy folder.    

    -   **Wartości:** 1 wartości innej niż 1 jest uważany za nie można przy użyciu dysku CD. Najnowsze.

    -   **Szczegóły:** Skrypt musi zawierać ten klucz i wartość po uruchomieniu Instalatora z nośnika na dysku CD. Najnowsze folderu na potrzeby instalowania lokacji głównej lub centralnej administracji lub odzyskiwania lokacji głównej lub centralnej administracji. Ta wartość informuje Instalatora że nośnik tworzą dysku CD. R jest używany.

**RecoveryOptions**  

-   **Nazwa klucza:** ServerRecoveryOptions  

    -   **Wymagane:** Tak  

    -   **Wartości:** 1, 2 lub 4  

         1 = odzyskiwanie serwera lokacji i programu SQL Server.  

         2 = odzyskiwanie tylko serwera lokacji.  

         4 = odzyskiwanie tylko programu SQL Server.  

    -   **Szczegóły:** Określa, czy Instalator będzie przeprowadzał odzyskiwanie serwera lokacji i programu SQL Server. Skojarzone klucze są wymagane podczas ustawiania poniższej wartości dla **ServerRecoveryOptions** ustawienie:  

        -   Wartość = 1: Istnieje możliwość określenia wartości **SiteServerBackupLocation** klawisz, aby odzyskiwać lokację przy użyciu kopii zapasowej lokacji. Jeżeli nie określisz wartości, lokacja zostanie ponownie zainstalowana bez przywracania jej z zestawu kopii zapasowych.  

        -   Wartość = 2: Istnieje możliwość określenia wartości **SiteServerBackupLocation** klawisz, aby odzyskiwać lokację przy użyciu kopii zapasowej lokacji. Jeżeli nie określisz wartości, lokacja zostanie ponownie zainstalowana bez przywracania jej z zestawu kopii zapasowych.  

        -   Wartość = 4: Klucz **BackupLocation** jest wymagany w przypadku skonfigurowania dla klucza **DatabaseRecoveryOptions** wartości **10** , która umożliwia przywracanie bazy danych lokacji z kopii zapasowej.  

-   **Nazwa klucza:** DatabaseRecoveryOptions  

    -   **Wymagane:** Ten klucz jest wymagany, gdy ustawienie **ServerRecoveryOptions** ma wartość **1** lub **4**.  

    -   **Wartości:** 10, 20, 40 lub 80  

         10 = przywracanie bazy danych lokacji z kopii zapasowej.  

         20 = korzystanie z bazy danych lokacji, która została ręcznie odzyskana przy użyciu innej metody.  

         40 = tworzenie nowej bazy danych lokacji. Użyj tej opcji, gdy nie ma dostępnej kopii zapasowej bazy danych lokacji. Odzyskiwanie danych globalnych i danych lokacji przebiega przy użyciu replikacji z innych lokacji.  

         80 = pomijanie odzyskiwania bazy danych.  

    -   **Szczegóły:** Określa sposób odzyskiwania bazy danych lokacji w programie SQL Server.  

-   **Nazwa klucza:** ReferenceSite  

    -   **Wymagane:** Ten klucz jest wymagany, gdy ustawienie **DatabaseRecoveryOptions** ma wartość **40**.  

    -   **Wartości:** <*nazwa FQDN lokacji odniesienia*>  

    -   **Szczegóły:** Określa lokację główną odniesienia do odzyskiwania danych globalnych, jeśli kopia zapasowa bazy danych jest starsza od okresu przechowywania śledzenia zmian lub w przypadku odzyskiwania lokacji bez kopii zapasowej używany w witrynie Administracja centralna.  

         Jeśli nie określisz lokacji odniesienia, a kopia zapasowa jest starsza od okresu przechowywania śledzenia zmian, wszystkie lokacje główne zostaną zainicjowane ponownie przy użyciu danych przywróconych z centralnej lokacji administracyjnej.  

         Gdy nie zostanie określona lokacja odniesienia i kopia zapasowa będzie okresu przechowywania śledzenia zmian, tylko zmiany wprowadzone po kopii zapasowej są replikowane z lokacji głównych. W przypadku wystąpienia konfliktu między zmianami z różnych lokacji głównych centralna lokacja administracyjna użyje danych otrzymanych w pierwszej kolejności.  

-   **Nazwa klucza:** SiteServerBackupLocation  

    -   **Wymagane:** Nie  

    -   **Wartości:** <*ścieżkę do zestawu kopii zapasowych serwera lokacji*>  

    -   **Szczegóły:** Określa ścieżkę do zestawu kopii zapasowych serwera lokacji. Ten klucz jest opcjonalny, gdy ustawienie **ServerRecoveryOptions** ma wartość **1** lub **2**. Określ wartość dla klucza **SiteServerBackupLocation** , aby odzyskiwać lokację przy użyciu kopii zapasowej lokacji. Jeżeli nie określisz wartości, lokacja zostanie ponownie zainstalowana bez przywracania jej z zestawu kopii zapasowych.  

-   **Nazwa klucza:** BackupLocation  

    -   **Wymagane:** Ten klucz jest wymagany podczas konfigurowania wartość **1** lub **4** dla **ServerRecoveryOptions** klucz i skonfiguruj wartość **10** dla **DatabaseRecoveryOptions** klucza.  

    -   **Wartości:** <*ścieżkę do zestawu kopii zapasowych bazy danych lokacji*>  

    -   **Szczegóły:** Określa ścieżkę do zestawu kopii zapasowych bazy danych lokacji.  

**Opcje**  

-   **Nazwa klucza:** Identyfikator produktu  

    -   **Wymagane:** Tak  

    -   **Wartości:** <*xxxxx-xxxxx-xxxxx-xxxxx-xxxxx*> *lub* Eval  

    -   **Szczegóły:** Określa klucz produktu instalacji programu Configuration Manager, wraz z kreskami. Wprowadź **Eval** zainstalować wersję ewaluacyjną programu Configuration Manager.  

-   **Nazwa klucza:** Kod lokacji  

    -   **Wymagane:** Tak  

    -   **Wartości:** <*kod lokacji*>  

    -   **Szczegóły:** Określa trzy znaki alfanumeryczne, które jednoznacznie identyfikują lokację w hierarchii. Należy określić kod lokacji używany przed awarią.

-   **Nazwa klucza:** Nazwa witryny  

    -   **Wymagane:** Nie  

    -   **Wartości:** <*Nazwa lokacji*>  

    -   **Szczegóły:** Określa nazwę dla tej lokacji.  

-   **Nazwa klucza:** SMSInstallDir  

    -   **Wymagane:** Tak  

    -   **Wartości:** <*ścieżkę instalacji programu Configuration Manager*>  

    -   **Szczegóły:** Określa folder instalacji plików programu Configuration Manager.  

-   **Nazwa klucza:** SDKServer  

    -   **Wymagane:** Tak  

    -   **Wartości:** <*dostawcy programu SMS w pełni kwalifikowaną nazwę domeny*>  

    -   **Szczegóły:** Określa nazwę FQDN serwera, który będzie hostem dostawcy programu SMS. Należy określić serwer, który hostował dostawcę programu SMS przed awarią.  

         Po instalacji początkowej możesz skonfigurować dodatkowych dostawców programu SMS dla lokacji. Aby uzyskać więcej informacji na temat dostawcy programu SMS, zobacz [planowanie dostawcy programu SMS dla programu System Center Configuration Manager](../../../../core/plan-design/hierarchy/plan-for-the-sms-provider.md).  

-   **Nazwa klucza:** PrerequisiteComp  

    -   **Wymagane:** Tak  

    -   **Wartości:** 0 lub 1  

         0 = pobierania  

         1 = już pobrane  

    -   **Szczegóły:** Określa, czy pliki wymagań wstępnych Instalatora zostały już pobrane. Na przykład, jeśli używasz wartość **0**, Instalator pobierze pliki.  

-   **Nazwa klucza:** PrerequisitePath  

    -   **Wymagane:** Tak  

    -   **Wartości:** <*ścieżkę do plików wymagań wstępnych instalacji*>  

    -   **Szczegóły:** Określa ścieżkę do plików wymagań wstępnych Instalatora. W zależności od wartości **PrerequisiteComp** Instalator używa tej ścieżki do przechowywania pobranych plików lub lokalizowania wcześniej pobranych plików.  

-   **Nazwa klucza:** AdminConsole  

    -   **Wymagane:** Ten klucz jest wymagany, chyba że ustawienie **ServerRecoveryOptions** ma wartość **4**.  

    -   **Wartości:** 0 lub 1  

         0 = nie instaluj  

         1 = instalacji  

    -   **Szczegóły:** Określa, czy należy zainstalować konsolę programu Configuration Manager.  

-   **Nazwa klucza:** JoinCEIP  

    -   **Wymagane:** Tak  

    -   **Wartości:** 0 lub 1  

         0 = nie dołączaj  

         1 = sprzężenia  

    -   **Szczegóły:** Określa, czy dołączyć do programu CEIP.  

**SQLConfigOptions**  

-   **Nazwa klucza:** SQLServerName  

    -   **Wymagane:** Tak  

    -   **Wartości:** <*nazwa serwera SQL*>  

    -   **Szczegóły:** Określa nazwę serwera lub klastrowanego wystąpienia, w którym jest uruchomiony program SQL Server i który będzie hostem bazy danych lokacji. Należy określić serwer, który hostował bazę danych lokacji przed awarią.  

-   **Nazwa klucza:** DatabaseName  

    -   **Wymagane:** Tak  

    -   **Wartości:** <*Nazwa bazy danych lokacji*> lub <*nazwa wystąpienia*>\\<*Nazwa bazy danych lokacji*>  

    -   **Szczegóły:** Określa nazwę bazy danych programu SQL Server do utworzenia lub bazy danych programu SQL Server do użycia podczas instalowania bazy danych witryny Administracja centralna. Należy określić nazwę bazy danych, która była używana przed awarią.  

        > [!IMPORTANT]  
        >  Jeżeli nie używasz domyślnego wystąpienia, należy określić nazwy wystąpienia i lokacji.  

-   **Nazwa klucza:** SQLSSBPort  

    -   **Wymagane:** Tak  

    -   **Wartości:** <*numer portu SSB*>  

    -   **Szczegóły:** Określa port SSB, który używa programu SQL Server. SSB zazwyczaj jest skonfigurowany do używania portu TCP 4022. Należy określić ten sam port SBB, który był używany przed awarią.  

-   **Nazwa klucza:** SQLDataFilePath  

    -   **Wymagane:** Nie  

    -   **Wartości:** <*ścieżkę do pliku MDB bazy danych*>  

    -   **Szczegóły:** Określa alternatywną lokalizację do utworzenia pliku MDB bazy danych.  

-   **Nazwa klucza:** SQLLogFilePath  

    -   **Wymagane:** Nie  

    -   **Wartości:** <*ścieżkę do pliku .ldf bazy danych*>  

    -   **Szczegóły:** Określa alternatywną lokalizację do utworzenia pliku .ldf bazy danych.  

**CloudConnectorOptions**  

-   **Nazwa klucza:** CloudConnector  

    -   **Wymagane:** Tak  

    -   **Wartości:** 0 lub 1  

         0 = nie instaluj  

         1 = instalacji  

    -   **Szczegóły:** Określa, czy zainstalować punktu połączenia usługi w tej lokacji. Ponieważ punktu połączenia usługi można zainstalować tylko w lokacji najwyższego poziomu w hierarchii, ta wartość musi być **0** dla podrzędnej lokacji głównej.  

-   **Nazwa klucza:** CloudConnectorServer  

    -   **Wymagane:** Wymagany, gdy **CloudConnector** jest równe 1  

    -   **Wartości:** <*nazwa FQDN serwera punktu połączenia usługi*>  

    -   **Szczegóły:** Określa nazwę FQDN serwera obsługującego rolę systemu lokacji punktu połączenia usługi.  

-   **Nazwa klucza:** UseProxy  

    -   **Wymagane:** Wymagany, gdy **CloudConnector** jest równe 1  

    -   **Wartości:** 0 lub 1  

         0 = nie instaluj  

         1 = instalacji  

    -   **Szczegóły:** Określa, czy punkt połączenia usługi będzie używać serwera proxy.  

-   **Nazwa klucza:** ProxyName  

    -   **Wymagane:** Wymagany, gdy **CloudConnector** jest równe 1  

    -   **Wartości:** <*nazwa FQDN serwera Proxy*>  

    -   **Szczegóły:** Określa nazwę FQDN serwera proxy, który będzie używany przez rolę systemu lokacji punktu połączenia usługi.  

-   **Nazwa klucza:** ProxyPort  

    -   **Wymagane:** Wymagany, gdy **CloudConnector** jest równe 1  

    -   **Wartości:** <*numer portu*>  

    -   **Szczegóły:** Określa numer portu używany do portu serwera proxy.  

### <a name="unattended-recovery-for-a-primary-site"></a>Nienadzorowane odzyskiwanie lokacji głównej  
 Następujące szczegóły umożliwia odzyskiwanie lokacji głównej przy użyciu pliku instalacji nienadzorowanej.  

**Identyfikacja**  

-   **Nazwa klucza:** Akcja  

    -   **Wymagane:** Tak  

    -   **Wartości:** <*RecoverPrimarySite*>  

    -   **Szczegóły:** Odzyskuje lokację główną.  

-   **Nazwa klucza:** CDLatest  

    -   **Wymagane:** Tak — tylko w przypadku używania nośnika z dysku CD. Najnowszy folder.    

    -   **Wartości:** 1 wartości innej niż 1 jest uważany za nie można przy użyciu dysku CD. Najnowsze.

    -   **Szczegóły:** Skrypt musi zawierać ten klucz i wartość po uruchomieniu Instalatora z nośnika na dysku CD. Najnowsze folderu na potrzeby instalowania lokacji głównej lub centralnej administracji lub odzyskiwania lokacji głównej lub centralnej administracji. Ta wartość informuje Instalatora że nośnik tworzą dysku CD. R jest używany.    

**RecoveryOptions**  

-   **Nazwa klucza:** ServerRecoveryOptions  

    -   **Wymagane:** Tak  

    -   **Wartości:** 1, 2 lub 4  

         1 = odzyskiwanie serwera lokacji i programu SQL Server.  

         2 = odzyskiwanie tylko serwera lokacji.  

         4 = odzyskiwanie tylko programu SQL Server.  

    -   **Szczegóły:** Określa, czy Instalator będzie przeprowadzał odzyskiwanie serwera lokacji i programu SQL Server. Skojarzone klucze są wymagane podczas ustawiania poniższej wartości dla **ServerRecoveryOptions** ustawienie:  

        -   Wartość = 1: Istnieje możliwość określenia wartości **SiteServerBackupLocation** klawisz, aby odzyskiwać lokację przy użyciu kopii zapasowej lokacji. Jeżeli nie określisz wartości, lokacja zostanie ponownie zainstalowana bez przywracania jej z zestawu kopii zapasowych.  

        -   Wartość = 2: Istnieje możliwość określenia wartości **SiteServerBackupLocation** klawisz, aby odzyskiwać lokację przy użyciu kopii zapasowej lokacji. Jeżeli nie określisz wartości, lokacja zostanie ponownie zainstalowana bez przywracania jej z zestawu kopii zapasowych.  

        -   Wartość = 4: Klucz **BackupLocation** jest wymagany w przypadku skonfigurowania dla klucza **DatabaseRecoveryOptions** wartości **10** , która umożliwia przywracanie bazy danych lokacji z kopii zapasowej.  

-   **Nazwa klucza:** DatabaseRecoveryOptions  

    -   **Wymagane:** Ten klucz jest wymagany, gdy ustawienie **ServerRecoveryOptions** ma wartość **1** lub **4**.  

    -   **Wartości:** 10, 20, 40 lub 80  

         10 = przywracanie bazy danych lokacji z kopii zapasowej.  

         20 = korzystanie z bazy danych lokacji, która została ręcznie odzyskana przy użyciu innej metody.  

         40 = tworzenie nowej bazy danych lokacji. Użyj tej opcji, gdy nie ma dostępnej kopii zapasowej bazy danych lokacji. Odzyskiwanie danych globalnych i danych lokacji przebiega przy użyciu replikacji z innych lokacji.  

         80 = pomijanie odzyskiwania bazy danych.  

    -   **Szczegóły:** Określa sposób odzyskiwania bazy danych lokacji w programie SQL Server.  

-   **Nazwa klucza:** SiteServerBackupLocation  

    -   **Wymagane:** Nie  

    -   **Wartości:** <*ścieżkę do zestawu kopii zapasowych serwera lokacji*>  

    -   **Szczegóły:**  

         Określa ścieżkę do zestawu kopii zapasowych serwera lokacji. Ten klucz jest opcjonalny, gdy ustawienie **ServerRecoveryOptions** ma wartość **1** lub **2**. Określ wartość dla klucza **SiteServerBackupLocation** , aby odzyskiwać lokację przy użyciu kopii zapasowej lokacji. Jeżeli nie określisz wartości, lokacja zostanie ponownie zainstalowana bez przywracania jej z zestawu kopii zapasowych.  

-   **Nazwa klucza:** BackupLocation  

    -   **Wymagane:** Ten klucz jest wymagany podczas konfigurowania wartość **1** lub **4** dla **ServerRecoveryOptions** , a wartość **10** dla **DatabaseRecoveryOptions** klucza.  

    -   **Wartości:** <*ścieżkę do zestawu kopii zapasowych bazy danych lokacji*>  

    -   **Szczegóły:** Określa ścieżkę do zestawu kopii zapasowych bazy danych lokacji.  

**Opcje**  

-   **Nazwa klucza:** Identyfikator produktu  

    -   **Wymagane:** Tak  

    -   **Wartości:** *xxxxx-xxxxx-xxxxx-xxxxx-xxxxx* lub *Eval*  

    -   **Szczegóły:** Określa klucz produktu instalacji programu Configuration Manager, wraz z kreskami. Wprowadź **Eval** zainstalować wersję ewaluacyjną programu Configuration Manager.  

-   **Nazwa klucza:** Kod lokacji  

    -   **Wymagane:** Tak  

    -   **Wartości:** <*kod lokacji*>  

    -   **Szczegóły:** Określa trzy znaki alfanumeryczne, które jednoznacznie identyfikują lokację w hierarchii. Należy określić kod lokacji używany przed awarią.

-   **Nazwa klucza:** Nazwa witryny  

    -   **Wymagane:** Nie  

    -   **Wartości:** <*Nazwa lokacji*>  

    -   **Szczegóły:** Określa nazwę dla tej lokacji.  

-   **Nazwa klucza:** SMSInstallDir  

    -   **Wymagane:** Tak  

    -   **Wartości:** <*ścieżkę instalacji programu Configuration Manager*>  

    -   **Szczegóły:** Określa folder instalacji plików programu Configuration Manager.  

-   **Nazwa klucza:** SDKServer  

    -   **Wymagane:** Tak  

    -   **Wartości:** <*dostawcy programu SMS w pełni kwalifikowaną nazwę domeny*>  

    -   **Szczegóły:** Określa nazwę FQDN serwera, który będzie hostem dostawcy programu SMS. Należy określić serwer, który hostował dostawcę programu SMS przed awarią. Po instalacji początkowej możesz skonfigurować dodatkowych dostawców programu SMS dla lokacji. Aby uzyskać więcej informacji na temat dostawcy programu SMS, zobacz [planowanie dostawcy programu SMS dla programu System Center Configuration Manager](../../../../core/plan-design/hierarchy/plan-for-the-sms-provider.md).  

-   **Nazwa klucza:** PrerequisiteComp  

    -   **Wymagane:** Tak  

    -   **Wartości:** 0 lub 1  

         0 = pobierania  

         1 = już pobrane  

    -   **Szczegóły:** Określa, czy pliki wymagań wstępnych Instalatora zostały już pobrane. Na przykład, jeśli używasz wartość **0**, Instalator pobierze pliki.  

-   **Nazwa klucza:** PrerequisitePath  

    -   **Wymagane:** Tak  

    -   **Wartości:** <*ścieżkę do plików wymagań wstępnych instalacji*>  

    -   **Szczegóły:** Określa ścieżkę do plików wymagań wstępnych Instalatora. W zależności od wartości **PrerequisiteComp** Instalator używa tej ścieżki do przechowywania pobranych plików lub lokalizowania wcześniej pobranych plików.  

-   **Nazwa klucza:** AdminConsole  

    -   **Wymagane:** Ten klucz jest wymagany, chyba że ustawienie **ServerRecoveryOptions** ma wartość **4**.  

    -   **Wartości:** 0 lub 1  

         0 = nie instaluj  

         1 = instalacji  

    -   **Szczegóły:** Określa, czy należy zainstalować konsolę programu Configuration Manager.  

-   **Nazwa klucza:** JoinCEIP  

    -   **Wymagane:** Tak  

    -   **Wartości:** 0 lub 1  

         0 = nie dołączaj  

         1 = sprzężenia  

    -   **Szczegóły:** Określa, czy dołączyć do programu CEIP.  

**SQLConfigOptions**  

-   **Nazwa klucza:** SQLServerName  

    -   **Wymagane:** Tak  

    -   **Wartości:** <*nazwa serwera SQL*>  

    -   **Szczegóły:** Określa nazwę serwera lub klastrowanego wystąpienia, w którym jest uruchomiony program SQL Server i który będzie hostem bazy danych lokacji. Należy określić serwer, który hostował bazę danych lokacji przed awarią.  

-   **Nazwa klucza:** DatabaseName  

    -   **Wymagane:** Tak  

    -   **Wartości:**  <*Nazwa bazy danych lokacji*> lub <*nazwa wystąpienia*>\\<*Nazwa bazy danych lokacji*>

    -   **Szczegóły:**  

         Określa nazwę bazy danych programu SQL Server do utworzenia lub bazy danych programu SQL Server do użycia podczas instalowania bazy danych witryny Administracja centralna. Należy określić nazwę bazy danych, która była używana przed awarią.  

        > [!IMPORTANT]  
        >  Jeżeli nie używasz domyślnego wystąpienia, należy określić nazwy wystąpienia i lokacji.  

-   **Nazwa klucza:** SQLSSBPort  

    -   **Wymagane:** Tak  

    -   **Wartości:** <*numer portu SSB*>  

    -   **Szczegóły:** Określa port SSB, który używa programu SQL Server. Zazwyczaj port SSB jest skonfigurowany do używania portu TCP 4022. Należy określić ten sam port SBB, który był używany przed awarią.  

-   **Nazwa klucza:** SQLDataFilePath  

    -   **Wymagane:** Nie  

    -   **Wartości:** <*ścieżkę do pliku MDB bazy danych*>  

    -   **Szczegóły:** Określa alternatywną lokalizację do utworzenia pliku MDB bazy danych.  

-   **Nazwa klucza:** SQLLogFilePath  

    -   **Wymagane:** Nie  

    -   **Wartości:** <*ścieżkę do pliku .ldf bazy danych*>  

    -   **Szczegóły:** Określa alternatywną lokalizację do utworzenia pliku .ldf bazy danych.  

**HierarchyExpansionOptions**  

-   **Nazwa klucza:** CCARSiteServer  

    -   **Wymagane:** Zobacz szczegóły.  

    -   **Wartości:** <*kod dla witryny administracji centralnej lokacji*>  

    -   **Szczegóły:** Określa lokację administracji centralnej, z którym połączy się lokacja główna po dołączeniu hierarchii programu Configuration Manager. To ustawienie jest wymagane, jeśli lokacja główna była połączona z centralną lokacją administracyjną przed awarią. Należy określić kod lokacji używany w odniesieniu do centralnej lokacji administracyjnej przed awarią.  

-   **Nazwa klucza:** CASRetryInterval  

    -   **Wymagane:** Nie  

    -   **Wartości:** <*Interval*>  

    -   **Szczegóły:** Określa interwał ponawiania prób (w minutach) prób połączenia z witryną Administracja centralna, po niepowodzeniu. Na przykład, jeśli połączenie z centralnej lokacji administracyjnej nie powiedzie się, lokacji głównej czeka liczbę minut, które określisz dla **CASRetryInterval** wartości i podejmuje próbę połączenia.  

-   **Nazwa klucza:** WaitForCASTimeout  

    -   **Wymagane:** Nie  

    -   **Wartości:** <*Timeout*>  

    -   **Szczegóły:** Określa maksymalną wartość limitu czasu (w minutach) dla lokacji głównej połączyć się z witryną Administracja centralna. Na przykład, jeśli lokacji głównej nie może połączyć się z witryną Administracja centralna, lokacja główna ponowi próbę połączenia witryny administracji centralnej, na podstawie **CASRetryInterval** wartości do **WaitForCASTimeout** czasu. Można określić wartość **0** do **100**.  

**CloudConnectorOptions**  

-   **Nazwa klucza:** CloudConnector  

    -   **Wymagane:** Tak  

    -   **Wartości:** 0 lub 1  

         0 = nie instaluj  

         1 = instalacji  

    -   **Szczegóły:** Określa, czy zainstalować punktu połączenia usługi w tej lokacji. Ponieważ punktu połączenia usługi można zainstalować tylko w lokacji najwyższego poziomu w hierarchii, ta wartość musi być **0** dla podrzędnej lokacji głównej.  

-   **Nazwa klucza:** CloudConnectorServer  

    -   **Wymagane:** Wymagany, gdy **CloudConnector** jest równe 1  

    -   **Wartości:** <*nazwa FQDN serwera punktu połączenia usługi*>  

    -   **Szczegóły:** Określa nazwę FQDN serwera obsługującego rolę systemu lokacji punktu połączenia usługi.  

-   **Nazwa klucza:** UseProxy  

    -   **Wymagane:** Wymagany, gdy **CloudConnector** jest równe 1  

    -   **Wartości:** 0 lub 1  

         0 = nie instaluj  

         1 = instalacji  

    -   **Szczegóły:** Określa, czy punkt połączenia usługi będzie używać serwera proxy.  

-   **Nazwa klucza:** ProxyName  

    -   **Wymagane:** Wymagany, gdy **CloudConnector** jest równe 1  

    -   **Wartości:** <*nazwa FQDN serwera Proxy*>  

    -   **Szczegóły:** Określa nazwę FQDN serwera proxy, który będzie używany przez rolę systemu lokacji punktu połączenia usługi.  

-   **Nazwa klucza:** ProxyPort  

    -   **Wymagane:** Wymagany, gdy **CloudConnector** jest równe 1  

    -   **Wartości:** <*numer portu*>  

    -   **Szczegóły:** Określa numer portu używany do portu serwera proxy.  

