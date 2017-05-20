---
title: Magazyn danych | Dokumentacja firmy Microsoft
description: "Punkt usługi magazynu danych i bazy danych programu System Center Configuration Manager"
ms.custom: na
ms.date: 3/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aaf43e69-68b4-469a-ad58-9b66deb29057
caps.latest.revision: 
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3c2a07f560e0aa3d2beb7cc50e71c98ac45c27e1
ms.openlocfilehash: 9239f6e749c368835e8594ca2d07378d8555b99e
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
#  <a name="the-data-warehouse-service-point-for-system-center-configuration-manager"></a>Punkt usługi magazynu danych programu System Center Configuration Manager
*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Począwszy od wersji 1702, punkt usługi Magazyn danych można użyć do przechowywania i raport dotyczący długoterminowe dane historyczne dla danego wdrożenia programu Configuration Manager.

> [!TIP]  
> Wprowadzona w wersji 1702, punkt usługi Magazyn danych jest funkcją wersji wstępnej. Aby ją włączyć, zobacz [korzystanie z funkcji wersji wstępnej](/sccm/core/servers/manage/pre-release-features).

Magazyn danych obsługuje maksymalnie 2 TB danych znacznikami śledzenia zmian. Przechowywanie danych odbywa się przy automatycznych synchronizacji z bazy danych lokacji programu Configuration Manager do bazy danych magazynu danych. Te informacje są dostępne z punktu usług Reporting Services.


Dane, które są synchronizowane obejmuje następujące z grup danych globalnych i danych lokacji:
- Kondycja infrastruktury
- Zabezpieczenia
- Zgodność
- Złośliwe oprogramowanie   
- Wdrożenia oprogramowania
- Szczegóły spisu (jednak historię spisu nie jest zsynchronizowana)

Podczas instalowania roli systemu lokacji instaluje i konfiguruje bazę danych magazynu danych. Instaluje też kilka raportów, można łatwo wyszukiwać i raportu na tych danych.



## <a name="prerequisites-for-the-data-warehouse-service-point"></a>Wymagania wstępne dotyczące punktu usługi magazynu danych
- Komputer, gdzie należy zainstalować rolę systemu lokacji wymaga programu .NET Framework 4.5.2 lub nowszy.
- Aby zsynchronizować dane z bazy danych magazynu danych jest używane konto komputera komputera, na którym zainstalowano rolę systemu lokacji. To konto wymaga następujących uprawnień:  
  - **Administrator** na komputerze, który będzie obsługiwać bazę danych magazynu danych.
  - **DB_owner** uprawnienia bazy danych magazynu danych.
-    Baza danych magazynu danych jest obsługiwana na domyślne lub nazwane wystąpienie programu SQL Server 2012 lub nowszym. Wersja musi być Enterprise lub Datacenter.
  - Grupy dostępności AlwaysOn programu SQL Server: Ta konfiguracja nie jest obsługiwana.
  - Klastra programu SQL Server: Klastry pracy awaryjnej programu SQL Server nie są obsługiwane. Jest to spowodowane bazy danych magazynu danych nie głęboko przetestowano na klastrów pracy awaryjnej programu SQL Server.
  - Gdy baza danych magazynu danych jest zdalnie z bazy danych serwera lokacji, musi mieć licencję oddzielnych dla programu SQL Server, który obsługuje bazę danych.

> [!IMPORTANT]  
> Magazynu danych nie jest obsługiwany na komputerze z uruchomionym punkt usługi magazynu danych lub który jest hostem bazy danych magazynu danych obsługuje jeden z następujących języków:
> - JPN — japoński
> - KOR — koreański
> - (— Proste chiński uproszczony)
> - CHT — chiński tradycyjny ten problem zostanie rozwiązany w przyszłej wersji.


## <a name="install-the-data-warehouse"></a>Zainstalować Magazyn danych
Można zainstalować rolę systemu lokacji magazynu danych tylko w lokacji najwyższego poziomu w hierarchii (centralnej lokacji administracyjnej lub autonomicznej lokacji głównej).

Każda hierarchia obsługuje pojedyncze wystąpienie tej roli, a może znajdować się w każdym systemie lokacji w tej lokacji najwyższego poziomu. SQL Server, który obsługuje bazę danych dla magazynu może być lokalnym do roli systemu lokacji lub zdalnym. Chociaż w magazynie danych działa z punktem usług Reporting Services, w którym jest zainstalowany w tej samej lokacji, nie muszą być zainstalowane na tym samym serwerze dwie role systemu lokacji.   

Aby zainstalować rolę, użyj **lokacji Kreator dodawania ról systemu** lub **lokacji Kreator tworzenia serwera systemu**. Zobacz [zainstalować role systemu lokacji](/sccm/core/servers/deploy/configure/install-site-system-roles) uzyskać więcej informacji.  

Podczas instalowania roli programu Configuration Manager utworzy bazę danych magazynu danych w wystąpieniu programu SQL Server, który określisz. W przypadku określenia nazwy istniejącej bazy danych (tak jak w przypadku możesz [przenieść bazę danych magazynu danych na nowy serwer SQL](#move-the-data-warehouse-database)), programu Configuration Manager nie tworzy nową bazę danych, ale zamiast tego używa jednego użytkownika.

### <a name="configurations-used-during-installation"></a>Konfiguracje używane podczas instalacji
**Wybór roli systemu** strony:  

**Ogólne** strony:
-     **Ustawienia połączenia bazy danych magazynu danych programu Configuration Manager**:
 - **Program SQL Server w pełni kwalifikowana nazwa domeny**:  
 Określ pełną kwalifikowaną nazwę domeny (FQDN) serwera, który obsługuje bazę danych magazynu danych usługi punktu.
 - **Nazwa wystąpienia programu SQL Server, jeśli ma zastosowanie**:   
 Jeśli nie używasz domyślnego wystąpienia programu SQL Server, należy określić wystąpienie.
 - **Nazwa bazy danych**:   
 Określ nazwę bazy danych magazynu danych.  Program Configuration Manager utworzy bazę danych magazynu danych o tej nazwie. Jeśli określisz nazwę bazy danych, która już istnieje w wystąpieniu programu SQL server Configuration Manager będzie używać tej bazy danych.
 - **Port serwera SQL dla połączenia**:   
 Określ numer portu TCP/IP, który jest skonfigurowany dla programu SQL Server, który obsługuje datbase magazynu danych. Ten port jest używany przez usługi synchronizacji magazynu danych do połączenia z bazą danych magazynu danych.  

**Harmonogram synchronizacji** strony:   
- **Harmonogram synchronizacji**:
 - **Godzina rozpoczęcia**:  
 Określ czas, jaki ma synchronizacji magazynu danych, aby rozpocząć.
 - **Wzorzec cyklu**:
    - **Codzienne**: Określ, że synchronizacja jest uruchamiany codziennie.
    - **Co tydzień**: Określ jednego dnia każdego tygodnia i tygodniowego cyklu synchronizacji.

## <a name="reporting"></a>Raportowanie
Po zainstalowaniu punktu usługi magazynu danych, kilka raportów stają się dostępne w punkcie usług Reporting Services, w którym jest zainstalowany w tej samej lokacji. Po zainstalowaniu punktu usługi magazynu danych przed zainstalowaniem punktu usług Reporting Services, raporty zostaną automatycznie dodane po zainstalowaniu punktu usług Reporting Services.

Rola systemu lokacji magazynu danych obejmuje następujące raporty, które mają kategorię z **magazyn danych**:
 - **Wdrażanie aplikacji — historycznych**:   
 Wyświetlić szczegóły dotyczące wdrażania aplikacji dla określonej aplikacji i komputera.
 - **Endpoint Protection i aktualizacji oprogramowania zgodności - historycznych**: Wyświetl komputery, których brakuje aktualizacji oprogramowania.  
 - **Spis sprzętu ogólne — historycznych**:      
 Wyświetl wszystkie spis sprzętu dla określonego komputera.
 - **Spis oprogramowania ogólne — historycznych**:      
 Wyświetl wszystkie spisu oprogramowania dla określonego komputera.
 - **Przegląd kondycji infrastruktury — historycznych**:     
 Zawiera omówienie kondycję infrastruktury programu Configuration Manager
 - **Lista złośliwego oprogramowania wykrył - historycznych**:     
 Widok złośliwego oprogramowania, które zostały wykryte w organizacji.
 - **Podsumowanie dystrybucji oprogramowania - historycznych**:     
 Podsumowanie dystrybucji oprogramowania dla określonych anonsów i maszyny.


## <a name="expand-an-existing-stand-alone-primary-into-a-hierarchy"></a>Rozszerzenia istniejącej autonomicznej podstawowego do hierarchii
Przed zainstalowaniem witryny Administracja centralna, aby rozszerzyć istniejącą autonomiczną lokację główną, należy najpierw odinstalować roli punktu obsługi magazynu danych. Po zainstalowaniu centralnej lokacji administracyjnej można zainstalować następnie Rola systemu lokacji w witrynie Administracja centralna.  

W przeciwieństwie do przeniesienia bazy danych magazynu danych ta zmiana powoduje utratę danych historycznych, które wcześniej zsynchronizowane w lokacji głównej. Nie jest obsługiwane wykonywanie kopii zapasowych bazy danych z lokacji głównej i przywrócić go w witrynie Administracja centralna.




## <a name="move-the-data-warehouse-database"></a>Przenieś bazy danych magazynu danych
Aby przenieść bazę danych magazynu danych na nowy serwer SQL, wykonaj następujące kroki:

1.    Użyj SQL Server Management Studio, aby utworzyć kopię zapasową danych baza danych magazynu, a następnie Przywróć tę bazę danych do programu SQL Server na nowym komputerze, który będzie udostępniał magazyn danych.   
> [!NOTE]     
> Po przywróceniu bazy danych na nowy serwer, upewnij się, że uprawnień dostępu do bazy danych są takie same na nową bazę danych magazynu danych, jak znajdowały się one w oryginalnej bazy danych magazynu danych.  

2.    Aby usunąć rolę systemu lokacji punktu usługi magazynu danych z bieżącego serwera, należy użyć konsoli programu Configuration Manager.
3.    Ponownie zainstaluj punkt usługi magazynu danych i określ nazwę nowego serwera SQL i wystąpienie bazy danych magazynu danych, należy przywrócić.
4.    Po zainstalowaniu roli systemu lokacji przeniesienie zostało ukończone.

## <a name="troubleshooting-data-warehouse-issues"></a>Rozwiązywanie problemów z magazynem danych
**Pliki dziennika**:  
Użyj następujących dziennikach do badania problemów z instalacji punktu usług magazynu danych lub synchronizacji danych:
 - *DWSSMSI.log* i *DWSSSetup.log* -Użyj w tych dziennikach do badania błędy, podczas instalowania punktu usługi magazynu danych.
 - *Microsoft.ConfigMgrDataWarehouse.log* — Użyj tego dziennika do badania synchronizacji danych między bazą danych lokacji do bazy danych magazynu danych.

**Konfigurowanie awarii**  
 Punkt obsługi magazynu danych nie można zainstalować na serwerze systemu lokacji zdalnej gdy magazyn danych jest pierwszym Rola systemu lokacji zainstalowaną na tym komputerze.  
  - **Rozwiązanie**:   
    Upewnij się, czy punkt usługi Magazyn danych jest instalowany już na komputerze znajduje się co najmniej jeden innych ról systemu lokacji.  


**Znane problemy z synchronizacją**:   
Synchronizacja nie powiodła się z następującymi w *Microsoft.ConfigMgrDataWarehouse.log*: **"nie powiodło się wypełnienie obiekty schematu"**  
 - **Rozwiązanie**:  
    Upewnij się, że konto komputera z komputerem obsługującym Rola systemu lokacji **db_owner** na bazie danych magazynu danych.

Raporty magazynu danych nie można otwierać, gdy baza danych magazynu danych i punkt usług raportowania są na innych systemów lokacji.  

 - **Rozwiązanie**:  
    Udziel **konta punktu usług raportowania** **db_datareader** uprawnienia bazy danych magazynu danych.

Po otwarciu raportu magazynu danych, jest zwracany następujący błąd:

*Wystąpił błąd podczas przetwarzania raportu. (rsProcessingAborted) Nie można utworzyć połączenia ze źródłem danych "AutoGen__39B693BB_524B_47DF_9FDB_9000C3118E82_". (rsErrorOpeningConnection) Pomyślnie jest nawiązane połączenie z serwerem, ale wystąpił błąd podczas uzgadniania przed logowaniem. (Dostawca: Dostawca protokołu SSL, błąd: 0 - łańcuch certyfikatów został wystawiony przez urząd, który nie jest zaufany.)*

- **Rozwiązanie**: Aby skonfigurować certyfikaty, wykonaj następujące kroki:

  1. Na komputerze, który obsługuje bazę danych magazynu danych:

    1. Otwórz usług IIS, kliknij przycisk **certyfikaty serwera**, kliknij prawym przyciskiem myszy **Tworzenie certyfikatu z podpisem własnym**, a następnie określ "Przyjazna nazwa" nazwę certyfikatu jako **certyfikatu identyfikacji serwera SQL magazynu danych**. Wybierz magazyn certyfikatów jako **osobiste**.
    2. Otwórz **programu SQL Server Configuration Manager**w obszarze **konfigurację sieci programu SQL Server**, kliknij prawym przyciskiem myszy, aby wybrać **właściwości** pod **protokoły dla MSSQLSERVER**. Następnie na **certyfikatu** zaznacz **certyfikatu identyfikacji serwera SQL magazynu danych** jako certyfikat, a następnie zapisz zmiany.  
    3. Otwórz **programu SQL Server Configuration Manager**w obszarze **usług SQL Server**, uruchom ponownie **usługi SQL Server** i **usługi raportowania**.
    4.    Otwórz program Microsoft Management Console (MMC) i Dodawanie przystawki dla **certyfikaty**, wybierz opcję Zarządzanie certyfikatami dla **konto komputera** komputera lokalnego. Następnie w konsoli MMC rozwiń **osobiste** folder > **certyfikaty**i eksportowanie **certyfikat identyfikacji serwera SQL magazynu danych** jako **certyfikat x.509 szyfrowany binarnie algorytmem DER (. CER)** pliku.    
  2.    Na komputerze, który obsługuje program SQL Server Reporting Services, należy otworzyć konsolę MMC i dodać przystawkę dla **certyfikaty**, a następnie wybierz certyfikat dla zarządzania **konto komputera**. W obszarze **zaufane główne urzędy certyfikacji** folderu importu **certyfikat identyfikacji serwera SQL magazynu danych**.


## <a name="data-warehouse-dataflow"></a>Przepływ danych magazynu danych   
![Datawarehouse_flow](./media/datawarehouse.png)

**Magazyn danych i synchronizacji**

| Krok   | Szczegóły  |
|:------:|-----------|  
| **1**  |     Serwer lokacji przekazuje i dane są przechowywane w bazie danych lokacji.  |  
| **2**  |      Punkt usługi magazynu danych na podstawie jego harmonogram i konfiguracji, pobiera dane z bazy danych lokacji.  |  
| **3**  |  Punkt usługi Magazyn danych przesyła i przechowuje kopię zsynchronizowane dane w bazie danych magazynu danych. |  
**Raportowanie**

| Krok   | Szczegóły  |
|:------:|-----------|  
| **A**  |  Za pomocą wbudowanych raportów, użytkownik żąda danych. To żądanie jest przekazywany do usług Reporting Services punkt przy użyciu programu SQL Server Reporting Services. |  
| **B**  |      Większość raportów są aktualne informacje, a te żądania są uruchamiane w bazie danych lokacji. |  
| **C**  | Gdy raport zażąda danych historycznych za pomocą jednego z raportów z *kategorii* z **magazyn danych**, żądanie jest uruchamiane w bazie danych magazynu danych.   |  

