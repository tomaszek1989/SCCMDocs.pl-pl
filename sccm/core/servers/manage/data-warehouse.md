---
title: Magazyn danych | Dokumentacja firmy Microsoft
description: "Punkt usługi magazynu danych i bazy danych programu System Center Configuration Manager"
ms.custom: na
ms.date: 7/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aaf43e69-68b4-469a-ad58-9b66deb29057
caps.latest.revision: 
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: eedbf12d3bf628666efc90c85a8dfab37e4dc9ab
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
#  <a name="the-data-warehouse-service-point-for-system-center-configuration-manager"></a>Punkt usługi Magazyn danych programu System Center Configuration Manager
*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Począwszy od wersji 1702, punkt usługi Magazyn danych można użyć do przechowywania i raport dotyczący długoterminowe dane historyczne dla danego wdrożenia programu Configuration Manager.

> [!TIP]
> Punkt usługi Magazyn danych jest wprowadzonych w wersji 1702 funkcji wersji wstępnej. Aby ją włączyć, zobacz [korzystanie z funkcji wersji wstępnej](/sccm/core/servers/manage/pre-release-features).

> Począwszy od wersji 1706, ta funkcja nie jest już funkcji wersji wstępnej.

Magazyn danych obsługuje maksymalnie 2 TB danych z sygnaturami czasowymi, śledzenie zmian. Przechowywanie danych odbywa się przez automatyczne synchronizacje z bazy danych lokacji programu Configuration Manager do bazy danych magazynu danych. Te informacje są dostępne z punktu usług Reporting Services. Dane, które są synchronizowane z bazy danych magazynu danych jest zachowywana przez 3 lata. Okresowo wbudowanego zadania usuwa dane starsze niż trzy lata.

Dane, które są synchronizowane obejmuje następujące elementy z grup danych globalnych i danych lokacji:
- Kondycja infrastruktury
- Zabezpieczenia
- Zgodność
- Złośliwe oprogramowanie   
- Wdrożenia oprogramowania
- Szczegóły spisu (jednak historię spisu nie jest zsynchronizowany)

Podczas instalowania roli systemu lokacji, instaluje i konfiguruje bazę danych magazynu danych. Kilka raportów, można łatwo wyszukiwać i raportu także instalacji na tych danych.



## <a name="prerequisites-for-the-data-warehouse-service-point"></a>Wymagania wstępne dotyczące punktu usługi magazynu danych
- Rola systemu lokacji magazynu danych jest obsługiwana tylko w lokacji najwyższego poziomu w hierarchii. (Centralnej lokacji administracyjnej lub autonomicznej lokacji głównej).
- Komputer, na którym zainstalowano rolę systemu lokacji wymaga programu .NET Framework 4.5.2 lub nowszej.
- Aby zsynchronizować dane z bazy danych magazynu danych jest używane konto komputera komputera, na którym zainstalowano rolę systemu lokacji. To konto wymaga następujących uprawnień:  
  - **Administrator** na komputerze, który będzie hostem bazy danych magazynu danych.
  - **DB_owner** uprawnień w bazie danych magazynu danych.
  - **DB_reader** i **wykonania** baza danych lokacji uprawnienia do lokacji najwyższego poziomu.
- Baza danych magazynu danych wymaga użycia programu SQL Server 2012 lub nowszym. Wersja może być Standard, Enterprise lub Datacenter.
- Obsługiwane są następujące konfiguracje programu SQL Server do hostowania bazy danych magazynu:  
  - Domyślne wystąpienie
  - Nazwane wystąpienie
  - SQL Server zawsze włączone grupy dostępności
  - Klaster pracy awaryjnej programu SQL Server
-   Gdy baza danych magazynu danych jest zdalnie z serwera bazy danych lokacji, musi mieć oddzielnej licencji dla każdego serwera SQL hostującego bazę danych.
- Jeśli używasz [widoki rozproszone](/sccm/core/servers/manage/data-transfers-between-sites#bkmk_distviews), roli systemu lokacji punktu usług danych magazynu należy zainstalować na tym samym serwerze, który udostępnia bazę danych witryny Administracja centralna.



> [!IMPORTANT]  
> Magazyn danych nie jest obsługiwana, gdy komputer z uruchomioną punktu usługi Magazyn danych lub obsługującego bazę danych magazynu danych ma jeden z następujących języków:
> - JPN — japoński
> - KOR — koreański
> - CHS — chiński proste
> - (CHT) — Chiński tradycyjny, ten problem zostanie rozwiązany w przyszłej wersji.


## <a name="install-the-data-warehouse"></a>Zainstalować Magazyn danych
Każda hierarchia obsługuje jedno wystąpienie tej roli w każdym systemie lokacji w lokacji najwyższego poziomu. SQL Server, który jest hostem bazy danych dla magazynu może być lokalnym do roli systemu lokacji lub zdalnym. Chociaż w magazynie danych działa z zainstalowanym w tej samej lokacji punkt usług raportowania, dwie role systemu lokacji nie jest konieczne można zainstalować na tym samym serwerze.   

Aby zainstalować rolę, użyj **lokacji Kreator dodawania ról systemu** lub **lokacji Kreator tworzenia serwera systemu**. Zobacz [zainstalować role systemu lokacji](/sccm/core/servers/deploy/configure/install-site-system-roles) Aby uzyskać więcej informacji.  

Po zainstalowaniu roli programu Configuration Manager utworzy bazę danych magazynu danych w wystąpieniu programu SQL Server, który określisz. Jeśli określono nazwę istniejącej bazy danych (w sposób jak w przypadku należy [przenieść bazę danych magazynu danych na nowy serwer SQL](#move-the-data-warehouse-database)), programu Configuration Manager nie tworzy nową bazę danych, ale zamiast tego używa jednego użytkownika.

### <a name="configurations-used-during-installation"></a>Konfiguracje używane podczas instalacji
**Wybór roli systemu** strony:  

**Ogólne** strony:
-   **Ustawienia połączenia bazy danych magazynu danych programu Configuration Manager**:
 - **Program SQL Server w pełni kwalifikowana nazwa domeny**:  
 Określ w pełni kwalifikowanej nazwy domeny (FQDN) serwera, który hostuje bazę danych magazynu danych usługi punktu.
 - **Nazwa wystąpienia serwera SQL, jeśli ma to zastosowanie**:   
 Jeśli nie używasz domyślnego wystąpienia programu SQL Server, należy określić wystąpienie.
 - **Nazwa bazy danych**:   
 Określ nazwę bazy danych magazynu danych. Nazwa bazy danych nie może przekraczać 10 znaków. (Długość nazwy obsługiwanych zostanie zwiększony w przyszłej wersji).
 Configuration Manager tworzy bazę danych magazynu danych o tej nazwie. Jeśli określisz nazwy bazy danych, która już istnieje w wystąpieniu programu SQL server Configuration Manager korzysta z tej bazy danych.
 - **Port serwera SQL używane do łączenia**:   
 Określ numer portu TCP/IP, który jest skonfigurowany dla programu SQL Server, który jest hostem bazy danych magazynu danych. Port ten jest używany przez usługę synchronizacji magazynu danych do nawiązania połączenia bazy danych magazynu danych.  

**Harmonogram synchronizacji** strony:   
- **Harmonogram synchronizacji**:
 - **Godzina rozpoczęcia**:  
 Określ czas, który ma synchronizacji magazynu danych, aby uruchomić.
 - **Wzorzec cyklu**:
    - **Codzienne**: Określ, że synchronizacja jest uruchamiana codziennie.
    - **Co tydzień**: Określ jeden dzień w każdej tydzień i cyklu tygodniowego synchronizacji.

## <a name="reporting"></a>Raportowanie
Po zainstalowaniu punktu usługi Data Warehouse kilka raportów stają się dostępne w punkcie usług Reporting Services, w którym jest zainstalowany w tej samej lokacji. Po zainstalowaniu punktu usługi magazynu danych przed zainstalowaniem punktu usług raportowania raporty zostaną dodane automatycznie po zainstalowaniu punktu usług Reporting Services.

Rola systemu lokacji magazynu danych obejmuje następujące raporty, które mają kategorię z **hurtowni danych**:
 - **Wdrażanie aplikacji — historycznych**:   
 Przejrzyj szczegóły dotyczące wdrażania aplikacji dla określonej aplikacji i komputera.
 - **Program Endpoint Protection i aktualizacji oprogramowania zgodności - historycznych**: Wyświetl komputery, których brakuje aktualizacji oprogramowania.  
 - **Spis sprzętu ogólne — historycznych**:   
 Wyświetl wszystkie spisu sprzętu dla określonej maszyny.
 - **Spis oprogramowania ogólne — historycznych**:   
 Wyświetl wszystkie spisu oprogramowania dla określonej maszyny.
 - **Przegląd kondycji infrastruktury — historycznych**:  
 Wyświetla Przegląd kondycji infrastruktury programu Configuration Manager
 - **Lista złośliwego oprogramowania wykryto - historycznych**:    
 Widok złośliwego oprogramowania, która została wykryta w organizacji.
 - **Podsumowanie dystrybucji oprogramowania - historycznych**:   
 Podsumowanie dystrybucji oprogramowania dla określonych anonsów i komputera.


## <a name="expand-an-existing-stand-alone-primary-into-a-hierarchy"></a>Rozszerzyć istniejącą autonomiczną lokację główną do hierarchii
Przed zainstalowaniem centralnej lokacji administracyjnej można rozszerzyć istniejącą autonomiczną lokację główną, należy najpierw odinstalować rolę punktu usługi Magazyn danych. Po zainstalowaniu centralnej lokacji administracyjnej można następnie zainstalować rolę systemu lokacji w centralnej lokacji administracyjnej.  

Inaczej niż w przypadku przenoszenia bazy danych magazynu danych ta zmiana powoduje utratę danych historycznych, który zsynchronizowane w lokacji głównej. Nie jest obsługiwane kopii zapasowej bazy danych z lokacji głównej i przywrócenie go w witrynie Administracja centralna.




## <a name="move-the-data-warehouse-database"></a>Przenoszenie bazy danych magazynu danych
Aby przenieść bazę danych magazynu danych na nowy serwer SQL, wykonaj następujące kroki:

1.  Aby utworzyć kopię zapasową bazy danych magazynu danych, należy użyć programu SQL Server Management Studio. Następnie Przywróć tę bazę danych do programu SQL Server na nowym komputerze, który obsługuje magazyn danych.   
> [!NOTE]     
> Po przywróceniu bazy danych na nowy serwer, upewnij się, że uprawnienia dostępu do bazy danych są takie same na nową bazę danych magazynu danych, jakie były na oryginalnej bazy danych magazynu danych.  

2.  Użyj konsoli programu Configuration Manager, aby usunąć rolę systemu lokacji punktu usługi Magazyn danych z bieżącego serwera.
3.  Ponownie zainstaluj punkt usługi Magazyn danych i określ nazwę nowego serwera SQL i wystąpienia, który jest hostem bazy danych magazynu danych, możesz przywrócić.
4.  Po zainstalowaniu roli systemu lokacji, przeniesienie zostało ukończone.

## <a name="troubleshooting-data-warehouse-issues"></a>Rozwiązywanie problemów z magazynem danych
**Pliki dziennika**:  
Użyj następujących dzienników do badania problemów dotyczących instalacji punktu usługi Magazyn danych lub synchronizacji danych:
 - *DWSSMSI.log* i *DWSSSetup.log* -zbadaj błędy podczas instalowania punktu usługi Magazyn danych za pomocą tych dzienników.
 - *Microsoft.ConfigMgrDataWarehouse.log* — ten dziennik umożliwia badanie synchronizacji danych między programami bazy danych lokacji do bazy danych magazynu danych.

**Konfigurowanie awarii**  
 Instalacja punktu usługi Magazyn danych nie powiedzie się na zdalnym serwerze systemu lokacji w magazynie danych po pierwszym Rola systemu lokacji, która instaluje na tym komputerze.  
  - **Rozwiązanie**:   
    Upewnij się, że komputer, na którym instalujesz punktu usługi Magazyn danych na już znajduje się co najmniej jeden innych ról systemu lokacji.  


**Znane problemy z synchronizacją**:   
Synchronizacja nie powiedzie się następujący komunikat o błędzie w *Microsoft.ConfigMgrDataWarehouse.log*: **"nie powiodło się wypełnienie obiektów schematu"**  
 - **Rozwiązanie**:  
    Upewnij się, że konto komputera komputera hostującego rolę systemu lokacji jest **db_owner** na bazę danych magazynu danych.

Raporty magazynu danych nie można otworzyć bazy danych magazynu danych i punkt usług raportowania znajdują się na innych systemów lokacji.  

 - **Rozwiązanie**:  
    Udziel **konta punktu usług raportowania** **db_datareader** uprawnień w bazie danych magazynu danych.

Po otwarciu raportu magazynu danych, jest zwracany następujący błąd:

*Wystąpił błąd podczas przetwarzania raportu. (rsProcessingAborted) Nie można utworzyć połączenia ze źródłem danych "AutoGen__39B693BB_524B_47DF_9FDB_9000C3118E82_". (rsErrorOpeningConnection) Pomyślnie ustanowiono połączenie z serwerem, ale wystąpił błąd podczas uzgadniania przed logowaniem. (Dostawca: Dostawca protokołu SSL, błąd: 0 — łańcuch certyfikatów został wystawiony przez urząd certyfikacji, który nie jest zaufany.)*

- **Rozwiązanie**: Aby skonfigurować certyfikaty, wykonaj następujące kroki:

  1. Na komputerze, który jest hostem bazy danych magazynu danych:

    1. Otwórz usług IIS, kliknij przycisk **certyfikaty serwera**, kliknij prawym przyciskiem myszy **Tworzenie certyfikatu z podpisem własnym**, a następnie określ "przyjazną nazwę" w nazwie certyfikatu jako **danych magazynu SQL Server Identification Certificate**. Wybierz magazyn certyfikatów jako **osobistych**.
    2. Otwórz **SQL Server Configuration Manager**w obszarze **konfigurację sieci programu SQL Server**, kliknij prawym przyciskiem myszy, aby wybrać **właściwości** w obszarze **protokoły dla elementu MSSQLSERVER**. Następnie na **certyfikatu** wybierz opcję **danych magazynu SQL Server Identification Certificate** jako certyfikat, a następnie zapisz zmiany.  
    3. Otwórz **SQL Server Configuration Manager**w obszarze **usług SQL Server**, uruchom ponownie **usługi SQL Server** i **usługi raportowania**.
    4.  Otwórz program Microsoft Management Console (MMC) i Dodaj przystawkę dla **certyfikaty**, wybierz pozycję Zarządzanie certyfikatami dla **konto komputera** komputera lokalnego. Następnie, w konsoli MMC rozwiń węzeł **osobistych** folder > **certyfikaty**i eksportowanie **danych magazynu SQL Server Identification Certificate** jako **certyfikat x.509 szyfrowany binarnie algorytmem DER (. CER)** pliku.    
  2.    Na komputerze, który jest hostem usług SQL Server Reporting Services, Otwórz program MMC i dodać przystawkę dla **certyfikaty**. Następnie wybierz opcję, aby zarządzać certyfikatami dla **konto komputera**. W obszarze **zaufane główne urzędy certyfikacji** folder importu **danych magazynu SQL Server Identification Certificate**.


## <a name="data-warehouse-dataflow"></a>Biblioteka przepływu danych magazynu danych   
![Datawarehouse_flow](./media/datawarehouse.png)

**Magazyn danych i synchronizacji**

| Krok   | Szczegóły  |
|:------:|-----------|  
| **1**  |  Serwer lokacji przesyła i przechowuje dane w bazie danych lokacji.  |  
| **2**  |      Punkt usługi Magazyn danych na podstawie harmonogramu i konfiguracji, pobiera dane z bazy danych lokacji.  |  
| **3**  |  Punkt usługi Magazyn danych przesyła i przechowuje kopię zsynchronizowane dane w bazie danych magazynu danych. |  
**Raportowanie**

| Krok   | Szczegóły  |
|:------:|-----------|  
| **A**  |  Za pomocą wbudowanych raportów, użytkownik zażąda danych. To żądanie jest przekazywana do usług Reporting Services punktu, przy użyciu programu SQL Server Reporting Services. |  
| **B**  |      Większość raporty są aktualne informacje, a te żądania są uruchamiane w bazie danych lokacji. |  
| **C**  | Gdy raport żąda danych historycznych, za pomocą jednej z raporty z *kategorii* z **hurtowni danych**, żądanie jest uruchamiana dla bazy danych magazynu danych.   |  
