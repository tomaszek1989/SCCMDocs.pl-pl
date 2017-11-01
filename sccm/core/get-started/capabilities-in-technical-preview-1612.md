---
title: Funkcje w wersji zapoznawczej Technical Preview 1612
titleSuffix: Configuration Manager
description: "Dowiedz się więcej o funkcjach dostępnych w wersji zapoznawczej Technical Preview programu System Center Configuration Manager, wersja 1612."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bceab2e8-2f05-4a17-9ac8-a7a558670fb7
caps.latest.revision: "5"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 7eeaa0895445bab661a2dd11f12737e02d29f5c7
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="capabilities-in-technical-preview-1612-for-system-center-configuration-manager"></a>Funkcje w wersji Technical Preview 1612 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*



W tym artykule przedstawiono funkcje, które są dostępne w wersji Technical Preview programu System Center Configuration Manager, wersja 1612. Można zainstalować tę wersję, aby zaktualizować i dodać nowe funkcje do lokacji programu Configuration Manager technical preview. Przed zainstalowaniem tej wersji technical Preview, przejrzyj temat wprowadzający [Technical Preview programu System Center Configuration Manager](../../core/get-started/technical-preview.md), aby zapoznać się z ogólne wymagania i ograniczenia dotyczące używania wersji technical preview, jak zaktualizować między wersjami i sposobu wyrazić swoją opinię na temat funkcji w wersji technical preview.    


**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  

## <a name="the-data-warehouse-service-point"></a>Punkt usługi magazynu danych
Począwszy od wersji Technical Preview 1612 punktu usługi magazynu danych można przechowywać i raport dotyczący długoterminowe dane historyczne dla danego wdrożenia programu Configuration Manager. Jest to osiągane przez automatyczne synchronizacje z bazy danych lokacji programu Configuration Manager do bazy danych magazynu danych. Te informacje są dostępne z punktu usług raportowania.

Domyślnie po zainstalowaniu nowej roli systemu lokacji programu Configuration Manager utworzy bazę danych magazynu danych w wystąpieniu programu SQL Server, który określisz. Magazyn danych obsługuje maksymalnie 2 TB danych z sygnaturami czasowymi, śledzenie zmian.  Domyślnie dane, które są synchronizowane z bazy danych lokacji zawiera grupy danych dla danych globalnych, dane lokacji Global_Proxy, danych w chmurze i widoków bazy danych. Można również zmodyfikować, co jest synchronizowane uwzględnić dodatkowe tabele lub wykluczyć określonych tabel domyślne zestawy replikacji.
Wartości domyślne, który jest synchronizowany zawiera informacje dotyczące następujących:
- Kondycja infrastruktury
- Zabezpieczenia
- Zgodność
- Złośliwe oprogramowanie   
- Wdrożenia oprogramowania
- Szczegóły spisu (jednak historię spisu nie jest zsynchronizowany)

Oprócz instalowania i konfigurowania bazy danych magazynu danych, kilka nowych raportów są zainstalowane, aby można było łatwo wyszukać i raportu na tych danych.

### <a name="data-warehouse-dataflow"></a>Biblioteka przepływu danych magazynu danych   
![Datawarehouse_flow](./media/datawarehouse.png)

| Krok         | Szczegóły  |
|:------:|-----------|  
| **1**  |  Serwer lokacji przesyła i przechowuje dane w bazie danych lokacji.  |  
| **2** |   Punkt usługi magazynu danych na podstawie harmonogramu i konfiguracji, pobiera dane z bazy danych lokacji.  |  
| **3** |  Punkt usługi magazynu danych przesyła i przechowuje kopię zsynchronizowane dane w bazie danych magazynu danych. |  
| **A** |  Używając raportów wbudowanych, danych żądań która jest przekazywana do usług Reporting Services punktu, przy użyciu programu SQL Server Reporting Services. |  
| **B** |   Większość raporty są aktualne informacje, a te żądania są uruchamiane w bazie danych lokacji. |  
| **C** | Gdy raport żąda danych historycznych, za pomocą jednej z raporty z *kategorii* z **hurtowni danych**, żądanie jest wykonywane na bazie danych magazynu danych.   |  

### <a name="prerequisites-for-the-data-warehouse-service-point-and-database"></a>Wymagania wstępne dla punktu usługi magazynu danych i bazy danych
- Hierarchii musi mieć zainstalowaną rolę systemu lokacji punktu usług raportowania.
- Komputer, na którym zainstalowano rolę systemu lokacji wymaga programu .NET Framework 4.5.2 lub nowszej.
- Konto komputera, na którym zainstalowano rolę systemu lokacji musi mieć uprawnienia administratora lokalnego na komputerze, który będzie hostem bazy danych magazynu danych.
- Konto administracyjne, które należy zainstalować rolę systemu lokacji musi być użytkownikiem DBO w wystąpieniu programu SQL Server, który będzie hostem bazy danych magazynu danych.  
-  Baza danych jest obsługiwana:
  - Z programu SQL Server 2012 lub nowszym, Enterprise lub Datacenter edition.
  - Na domyślne lub nazwane wystąpienie
  - Na *klastra programu SQL Server*. Mimo że ta konfiguracja powinna działać, nie została przetestowana i obsługa to optymalne rozwiązanie.
  - Gdy wspólnie z jednej bazy danych lokacji lub baza danych punktu usług raportowania. Jednak zaleca się, można zainstalować na osobnym serwerze.  
- Konto, które jest używane jako *konta punktu usług raportowania* musi mieć **db_datareader** uprawnień do bazy danych magazynu danych.  
- Bazy danych nie jest obsługiwana w *grupy dostępności AlwaysOn programu SQL Server*.

### <a name="install-the-data-warehouse"></a>Zainstalować Magazyn danych
Zainstaluj rolę systemu lokacji magazynu danych w centralnej lokacji administracyjnej lub lokacji głównej przy użyciu **lokacji Kreator dodawania ról systemu** lub **lokacji Kreator tworzenia serwera systemu**. Zobacz [zainstalować role systemu lokacji](/sccm/core/servers/deploy/configure/install-site-system-roles) Aby uzyskać więcej informacji. Hierarchia obsługuje wiele wystąpień tej roli, ale w każdej lokacji jest obsługiwane tylko jedno wystąpienie.  

Po zainstalowaniu roli programu Configuration Manager utworzy bazę danych magazynu danych w wystąpieniu programu SQL Server, który określisz. Jeśli określono nazwę istniejącej bazy danych (w sposób jak w przypadku należy [przenieść bazę danych magazynu danych na nowy serwer SQL](#move-the-data-warehouse-database)), programu Configuration Manager nie tworzy nową bazę danych, ale zamiast tego używa jednego użytkownika.

#### <a name="configurations-used-during-installation"></a>Konfiguracje używane podczas instalacji
Skorzystaj z poniższych informacji w celu ukończenia instalacji roli systemu lokacji:

**Wybór roli systemu** strony:  
Zanim kreator wyświetli opcję Wybierz i zainstaluj punkt usługi magazynu danych, należy zainstalować punkt usług raportowania.

**Ogólne** strony: Wymagane są następujące informacje ogólne:
- **Ustawienia bazy danych programu Configuration Manager:**   
  - **Nazwa serwera** — Określ nazwę FQDN serwera obsługującego bazę danych lokacji. Jeśli nie używasz domyślnego wystąpienia programu SQL Server, należy określić wystąpienie po nazwy FQDN w następującym formacie: ***&lt;Sqlserver_FQDN >\&< nazwa_wystąpienia >***
  - **Nazwa bazy danych** — Określ nazwę bazy danych lokacji.
  - **Sprawdź, czy** — kliknij przycisk **Sprawdź** aby upewnić się, że połączenie z bazą danych lokacji zostanie nawiązane.
</br></br>
- **Ustawienia bazy danych magazynu danych:**
  - **Nazwa serwera** — Określ nazwę FQDN serwera, który jest hostem punktu usługi magazynu danych i bazy danych. Jeśli nie używasz domyślnego wystąpienia programu SQL Server, należy określić wystąpienie po nazwy FQDN w następującym formacie: ***&lt;Sqlserver_FQDN >\&< nazwa_wystąpienia >***
  - **Nazwa bazy danych** — Określ nazwę FQDN dla bazy danych magazynu danych.  Configuration Manager utworzy bazę danych o tej nazwie. Jeśli określisz nazwy bazy danych, która już istnieje w wystąpieniu programu SQL server Configuration Manager będzie używać tej bazy danych.
  - **Sprawdź, czy** — kliknij przycisk **Sprawdź** aby upewnić się, że połączenie z bazą danych lokacji zostanie nawiązane.

**Ustawienia synchronizacji** strony:   
- **Ustawienia danych:**
  - **Grupy replikacji, aby zsynchronizować** — wybierz grupę danych mają być synchronizowane. Aby uzyskać informacje o różnych typach danych grup, zobacz [replikacji bazy danych](/sccm/core/servers/manage/data-transfers-between-sites#a-namebkmkdbrepa-database-replication) i **widoki rozproszone** w [transfer danych między lokacjami](/sccm/core/servers/manage/data-transfers-between-sites).
  - **Tabel dołączonych do synchronizowania** — Określ nazwę każdej kolejnej tabeli mają być synchronizowane. Oddziel wiele tabel za pomocą przecinka. Te tabele zostaną zsynchronizowane z bazy danych lokacji oprócz grupy replikacji, którą wybierzesz.
  - **Tabele wyłączone do synchronizowania** — Określ nazwę dla poszczególnych tabel z synchronizacji grupy replikacji. Tabele, które określisz, zostanie wykluczony z. Oddziel wiele tabel za pomocą przecinka.
- **Ustawienia synchronizacji:**
  - **Interwał synchronizacji (w minutach)** — Określ wartość w minutach. Po upływie interwału uruchamia nowe synchronizacji. W ten sposób realizowany zakresu od 60 do 1440 minut (24 godziny).
  - **Harmonogram** — określ dni, które mają uruchamianie synchronizacji.

**Dostęp do punktu raportowania**:   
Po zainstalowaniu roli magazynu danych, upewnij się, konto, które jest używane jako *konta punktu usług raportowania* ma **db_datareader** uprawnień do bazy danych magazynu danych.

#### <a name="troubleshoot-installation-and-data-synchronization"></a>Rozwiązywanie problemów z synchronizacją instalacji i danych
Użyj następujących dzienników do badania problemów dotyczących instalacji punktu usługi magazynu danych lub synchronizacji danych:
- **DWSSMSI.log** i **DWSSSetup.log** — za pomocą tych dzienników do sprawdzania, czy błędy podczas instalowania punktu usług magazynu danych.
-   **Microsoft.ConfigMgrDataWarehouse.log** — ten dziennik umożliwia badanie synchronizacji danych między programami bazy danych lokacji do bazy danych magazynu danych.

### <a name="reporting"></a>Raportowanie
Po zainstalowaniu roli systemu lokacji hurtowni danych, następujące raporty są dostępne na ten punkt usług raportowania z *kategorii* z **magazynu danych:**

|Raport                   | Szczegóły                                  |
|-------------------------|------------------------------------------|
| **Raport wdrażania aplikacji** | Przejrzyj szczegóły dotyczące wdrażania aplikacji dla określonej aplikacji i komputera.|
| **Program Endpoint Protection, a raport zgodności aktualizacji oprogramowania**   | Wyświetl komputery, których brakuje aktualizacji oprogramowania.|
| **Raport o spisie sprzętu ogólne**  | Wyświetl wszystkie spisu sprzętu dla określonej maszyny.|
| **Raport ze spisu oprogramowania ogólne**  | Wyświetl wszystkie spisu oprogramowania dla określonej maszyny.|
| **Przegląd kondycji infrastruktury**  |Wyświetla Przegląd kondycji infrastruktury programu Configuration Manager.|
| **Lista wykrytym złośliwym oprogramowaniem**  |Widok złośliwego oprogramowania, która została wykryta w organizacji.|
|** Oprogramowania dystrybucji podsumowania raportu ** | Podsumowanie dystrybucji oprogramowania dla określonych anonsów i komputera.|

### <a name="move-the-data-warehouse-database"></a>Przenoszenie bazy danych magazynu danych
Aby przenieść bazę danych magazynu danych na nowy serwer SQL, wykonaj następujące kroki:

  1. Przejrzyj bieżącej konfiguracji bazy danych i rekordów szczegółów konfiguracji, takich jak:  
   - Grupy danych, które można synchronizować
   - Tabele, możesz dołączyć lub wykluczyć z synchronizacji       

   Po przywrócić bazę danych na nowy serwer i ponownie zainstalować rolę systemu lokacji zostanie ponownie skonfigurować te grupy danych i tabele.  

  2. Użyj programu SQL Server Management Studio kopii zapasowej bazy danych magazynu danych, a następnie ponownie, aby przywrócić tę bazę danych do programu SQL server na nowym komputerze, który będzie obsługiwał hurtowni danych.

  Po przywróceniu bazy danych na nowy serwer, upewnij się, że uprawnienia dostępu do bazy danych są takie same na nową bazę danych magazynu danych, jakie były na oryginalnej bazy danych magazynu danych.

  3. Użyj konsoli programu Configuration Manager, aby usunąć rolę systemu lokacji punktu usługi magazynu danych z bieżącego serwera.

  4. Instalowania nowego punktu usługi magazynu danych i określ nazwę nowego serwera SQL i wystąpienia, który jest hostem bazy danych magazynu danych, możesz przywrócić.

  5. Po zainstalowaniu roli systemu lokacji, przeniesienie zostało ukończone.

Możesz przejrzeć następujące dzienniki programu Configuration Manager, aby potwierdzić, że pomyślnie ponownie zainstalował rolę systemu lokacji:  
- **DWSSMSI.log** i **DWSSSetup.log** — za pomocą tych dzienników do sprawdzania, czy błędy podczas instalowania punktu usług magazynu danych.
-   **Microsoft.ConfigMgrDataWarehouse.log** — ten dziennik umożliwia badanie synchronizacji danych między programami bazy danych lokacji do bazy danych magazynu danych.


## <a name="content-library-cleanup-tool"></a>Narzędzia do oczyszczania biblioteki zawartości
Począwszy od wersji Technical Preview 1612, można użyć nowego narzędzia wiersza polecenia (**ContentLibraryCleanup.exe**) można usunąć zawartość, która jest już skojarzony z dowolnego pakietu lub aplikacji z punktu dystrybucji (oddzielony zawartości). To narzędzie jest wywoływana narzędzia Oczyszczanie biblioteki zawartości.

To narzędzie ma wpływ tylko na zawartość w punkcie dystrybucji, które określisz po uruchomieniu narzędzia i nie można usunąć zawartość z biblioteki zawartości na serwerze lokacji.

Po zainstalowaniu Technical Preview 1612 można znaleźć **ContentLibraryCleanup.exe** w *%CM_Installation_Path%\cd.latest\SMSSETUP\TOOLS\ContentLibraryCleanup\* folderu na serwerze lokacji Technical Preview.

Narzędzia dostępne w tej wersji Technical Preview ma zastąpić starsze wersje narzędzi podobne wydane w ciągu ostatnich produktów Configuration Manager. Mimo że ta wersja narzędzia przestanie działać po 1 marca 2017 nowe wersje opublikuje z przyszłych wersji zapoznawczych Technical Preview, dopóki to narzędzie jest wydane jako część Current Branch lub wersja produkcyjna gotowy poza pasmem.

### <a name="requirements"></a>Wymagania  
 - Narzędzie można uruchomić bezpośrednio na komputerze, który hostuje punkt dystrybucji lub zdalnie z innego serwera. Narzędzie można uruchomić tylko z pojedynczego punktu dystrybucji w czasie.
 - Konto użytkownika, który uruchomił narzędzie bezpośrednio musi mieć uprawnienia administracji opartej na rolach, które są równe z pełnymi uprawnieniami administratora w hierarchii programu Configuration Manager.  Narzędzie nie działa, gdy konto użytkownika jest uprawnienia jako członek grupy zabezpieczeń systemu Windows z uprawnieniami administratora pełnego.

### <a name="modes-of-operation"></a>Tryby operacyjne
Narzędzie można uruchomić w dwóch trybach:
  1.    **Co jeśli tryb**:   
      Jeśli nie określisz **/delete** przełącznika, narzędzie działa w trybie co jeśli i identyfikuje zawartości, które zostaną usunięte z punktu dystrybucji, ale nie faktycznego usunięcia żadnych danych.

      - Narzędzie jest uruchamiane w tym trybie, informacje o zawartości, które zostałyby usunięte są automatycznie zapisywane w pliku dziennika narzędzia. Użytkownik nie jest monit o potwierdzenie każdego potencjalnych usunięcia.
      - Domyślnie plik dziennika są zapisywane do folderu tymczasowego użytkowników na komputerze, na którym należy uruchomić narzędzie, ale przełącznik/log może zostać użyty do przekierowania do innej lokalizacji pliku dziennika.  
      </br>

    Firma Microsoft zaleca, uruchom narzędzie w tym trybie i przejrzeć wynikowy plik dziennika, przed uruchomieniem narzędzia z przełącznikiem/DELETE.  

  2. **Usuń tryb**: Po uruchomieniu narzędzia z **/delete** przełącznika, narzędzie jest uruchamiane w trybie delete.

     - Po uruchomieniu narzędzia w tym trybie oddzielone zawartości, która znajduje się w określonym punkcie dystrybucji można usunąć z biblioteki zawartości w punkcie dystrybucji.
     -  Przed usunięciem każdego pliku, użytkownik jest monitowany o potwierdzenie, że plik powinien zostać usunięty.  Można wybrać **Y** tak, **N** na nie, lub **tak na wszystkie** pominąć dalsze monity i Usuń wszystkie oddzielone zawartość.  
     </br>

     Firma Microsoft zaleca, uruchom narzędzie w trybie warunkowej i przejrzeć wynikowy plik dziennika, przed uruchomieniem narzędzia z przełącznikiem/DELETE.  

Po uruchomieniu narzędzia do oczyszczania biblioteki zawartości w trybie automatycznie tworzy dziennika o nazwę, która zawiera tryb, w którym narzędzie jest uruchamiane w, nazwę punktu dystrybucji, Data i czas operacji. W pliku dziennika było nawiązywane automatycznie po zakończeniu działania narzędzia. Domyślnie ten dziennik jest zapisywany do użytkowników **temp** folderu na komputerze, na którym uruchamiasz narzędzia., jednak można przełącznik wiersza polecenia przekierowania w pliku dziennika do innej lokalizacji, w tym udziale sieciowym.   


### <a name="run-the-tool"></a>Uruchom narzędzie
Aby uruchomić narzędzie:
1. Otwórz administracyjny wiersz polecenia w folderze, który zawiera **ContentLibraryCleanup.exe**.  
2. Następnie wprowadź wiersz polecenia, który zawiera przełączniki wiersza polecenia wymagane i opcjonalne przełączniki, którego chcesz użyć.

**Znany problem** po uruchomieniu narzędzia dowolnego pakietu lub wdrożenia nie powiodło się lub jest w toku może być zwracany błąd podobnie do następującej:
-  *System.InvalidOperationException: Ta biblioteka zawartości nie można oczyścić teraz ponieważ pakietu <packageID> nie jest w pełni zainstalowany.*

**Obejście problemu:** Brak. Narzędzie nie niezawodnej zidentyfikować osieroconych plików, gdy zawartość jest w toku lub nie powiodła się do wdrożenia. W związku z tym narzędzie nie pozwoli do czyszczenia zawartości do momentu rozwiązania problemu.



### <a name="command-line-switches"></a>Przełączniki wiersza polecenia  
Następujące przełączniki wiersza polecenia mogą być używane w dowolnej kolejności.   

|Przełącznik|Szczegóły|
|---------|-------|
|**/ DELETE**  |**Opcjonalne** </br> Użyj tego przełącznika, jeśli chcesz usunąć zawartość z punktu dystrybucji. Zostanie wyświetlony monit, przed usunięciem zawartości. </br></br> Gdy ta opcja nie jest używany, narzędzie rejestruje wyniki dotyczące zawartości zostaną usunięte, ale nie powoduje usunięcia zawartości z punktu dystrybucji. </br></br> Przykład: ***/ Delete server1.contoso.com /dp ContentLibraryCleanup.exe*** |
| **/q**       |**Opcjonalne** </br> Uruchom narzędzie w trybie cichym, które pomijają wszystkie monity (na przykład monity podczas usuwania zawartości), a nie automatycznie otworzyć plik dziennika. </br></br> Przykład: ***ContentLibraryCleanup.exe /q /dp serwer1.contoso.com*** |
| **/dp &lt;FQDN punktów dystrybucji >**  | **Wymagane** </br> Określ w pełni kwalifikowaną nazwę (FQDN) punktu dystrybucji, które chcesz wyczyścić. </br></br> Przykład:  ***ContentLibraryCleanup.exe /dp serwer1.contoso.com***|
| **/PS &lt;lokacji głównej nazwy FQDN >**       | **Opcjonalne** podczas czyszczenia zawartości z punktu dystrybucji w lokacji głównej.</br>**Wymagane** podczas czyszczenia zawartości z punktu dystrybucji w lokacji dodatkowej. </br></br> Określ nazwę FQDN punktu dystrybucji w lokacji głównej należy do lub z głównej nadrzędnej, gdy punkt dystrybucji znajduje się w lokacji dodatkowej. </br></br> Przykład: ***ContentLibraryCleanup.exe /dp server1.contoso.com /ps siteserver1.contoso.com*** |
| **/sc &lt;kod lokacji głównej >**  | **Opcjonalne** podczas czyszczenia zawartości z punktu dystrybucji w lokacji głównej.</br>**Wymagane** podczas czyszczenia zawartości z punktu dystrybucji w lokacji dodatkowej. </br></br> Określ kod lokacji w lokacji głównej, należącego do punktu dystrybucji lub nadrzędnej lokacji głównej, gdy punkt dystrybucji znajduje się w lokacji dodatkowej.</br></br> Przykład: ***ContentLibraryCleanup.exe /dp server1.contoso.com /sc ABC*** |
| **/ log<log file directory>**       |**Opcjonalne** </br> Określ katalog, aby umieścić pliki dziennika w. Może to być lokalny lub w sieci, należy udostępnić.</br></br> Gdy ta opcja nie jest używana, pliki dziennika są automatycznie umieszczane w folderze tymczasowym użytkowników.</br></br> Przykład dysku lokalnym: ***/ ContentLibraryCleanup.exe /dp server1.contoso.com log C:\Users\Administrator\Desktop*** </br></br>Przykład z udziału sieciowego: ***/ Log server1.contoso.com /dp ContentLibraryCleanup.exe \\ &lt;udostępnianie >\&< folder >***|


## <a name="improvements-for-in-console-search"></a>Ulepszenia wyszukiwania w konsoli
Na podstawie User Voice opinii, dodano następujące ulepszenia dotyczące wyszukiwania w konsoli:
 - **Ścieżka obiektu:**  
  Wiele obiektów obsługuje teraz nową kolumnę o nazwie **ścieżki obiektu**.  Podczas wyszukiwania i zawierało tej kolumny w wynikach wyświetlania, można wyświetlić ścieżkę do każdego obiektu. Na przykład, jeśli podczas wykonywania wyszukiwania dla aplikacji w węźle aplikacje są również wyszukiwanie węzły podrzędne *ścieżki obiektu* kolumny w okienku wyników zostanie wyświetlona ścieżka do każdego obiektu zwróconego.   

- **Zachowanie szukany tekst:**  
  Gdy wprowadź tekst w polu tekstowym wyszukiwania, a następnie przełączać się między wyszukiwanie węzła podrzędnego i bieżącego węzła wpisany tekst teraz utrwalić i pozostają dostępne dla nowego wyszukiwania bez konieczności wpisz je ponownie.

- **Zachowanie zdecydować, czy wyszukiwanie węzły podrzędne:**  
 Opcja Wybierz albo wyszukiwania *bieżącego węzła* lub *wszystkie węzły podrzędne* teraz będzie nadal występować po zmianie pracujesz w węźle.   To nowe zachowanie oznacza, że nie trzeba stale ustawiony decyzję, jak poruszanie konsoli.  Domyślnie po otwarciu konsoli opcją jest wyszukiwanie tylko bieżącego węzła.

## <a name="prevent-installation-of-an-application-if-a-specified-program-is-running"></a>Zapobiega instalacji aplikacji, jeśli określony program jest uruchomiony.
Lista plików wykonywalnych (z rozszerzeniem .exe) można teraz skonfigurować we właściwościach typu wdrożenia, które, jeśli działa, zablokuje instalacji aplikacji. Po próbie instalacji, użytkownicy będą widzieć okno dialogowe z pytaniem, aby zamknąć procesów, które blokują instalacji.

### <a name="try-it-out"></a>Podczas próby
Aby skonfigurować listę plików wykonywalnych
1.  Na stronie właściwości każdego typu wdrożenia wybierz **obsługi Instalatora** kartę.
2.  Kliknij przycisk **Dodaj**, dodać więcej plików wykonywalnych do listy (na przykład **Edge.exe**)
3.  Kliknij przycisk **OK** aby zamknąć okno dialogowe właściwości typu wdrożenia.

Teraz podczas wdrażania tej aplikacji, użytkownika lub urządzenia, a jeden z plików wykonywalnych, dodane jest uruchomiona, użytkownicy zobaczą okno dialogowe Centrum oprogramowania informacją, których instalacja nie powiodła się, ponieważ aplikacja jest uruchomiona.

## <a name="new-windows-hello-for-business-notification-for-end-users"></a>Nowe usługi Windows Hello dla firm powiadomienia dla użytkowników końcowych

Nowe powiadomienie systemu Windows 10 informuje o użytkowników końcowych, że ich należy wykonać dodatkowe akcje do wykonania Windows Hello dla firm Instalatora (na przykład konfigurowania numeru PIN).

## <a name="windows-store-for-business-support-in-configuration-manager"></a>Sklep Windows dla firm pomocy technicznej w programie Configuration Manager

Teraz można wdrożyć licencjonowane aplikacje z celem wdrożenia **dostępne** ze Sklepu Windows dla firm na komputerach z uruchomionym klientem programu Configuration Manager.
Aby uzyskać więcej informacji, zobacz [Zarządzanie aplikacjami ze Sklepu Windows dla firm z System Center Configuration Manager](https://docs.microsoft.com/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business).

Obsługa ta funkcja jest obecnie dostępna tylko dla komputerów z systemem Windows 10 RS2 kompilacji wersji zapoznawczej.

## <a name="return-to-previous-page-when-a-task-sequence-fails"></a>Powrót do poprzedniej strony, gdy sekwencja zadań nie powiodło się.
Można teraz wróć do poprzedniej strony po uruchomieniu sekwencji zadań i awarii. Przed tą wersją trzeba było ponownego uruchomienia sekwencji zadań, jeśli wystąpił błąd. Na przykład można użyć **Wstecz** przycisk w następujących scenariuszach:

- Gdy komputer jest uruchamiany w środowisku Windows PE, dialogowym bootstrap sekwencji zadań może być wyświetlany, zanim sekwencja zadań będzie dostępna. Po kliknięciu przycisku Dalej w tym scenariuszu sekwencja zadań na ostatniej stronie wyświetla komunikat, że nie dostępnych sekwencji zadań. Teraz, możesz kliknąć **Wstecz** ponowić wyszukiwanie uzyskać dostępne sekwencje zadań. Ten proces można powtarzać do czasu udostępnienia sekwencji zadań.
- Po uruchomieniu sekwencji zadań, ale zależnych pakietów zawartości nie są jeszcze dostępne w punktach dystrybucji, sekwencja zadań kończy się niepowodzeniem. Możesz teraz dystrybuować brakującą zawartość (jeśli go nie została jeszcze rozesłana) lub poczekaj, aż zawartości, które mają być dostępne w punktach dystrybucji, a następnie kliknij **Wstecz** mają wyszukiwania sekwencji zadań ponownie dla zawartości.

## <a name="express-installation-files-support-for-windows-10-updates"></a>Obsługa aktualizacji systemu Windows 10 pliki instalacji ekspresowej
Dodaliśmy obsługę plików instalacji ekspresowej w programie Configuration Manager dla aktualizacje systemu Windows 10. Korzystając z obsługiwanej wersji systemu Windows 10, teraz służy ustawień programu Configuration Manager można pobrać tylko różnice między bieżącego miesiąca systemu Windows 10 aktualizacji zbiorczej i aktualizacją poprzedniego miesiąca. Obecnie w programie Configuration Manager bieżącej gałęzi, pełnej systemu Windows 10 aktualizacji zbiorczej (w tym wszystkie aktualizacje z ostatnich miesięcy) są pobierane każdego miesiąca. Przy użyciu plików instalacji ekspresowej zapewnia mniejsze pliki do pobrania i instalacji szybsze na klientach.

> [!IMPORTANT]
> Podczas ustawienia, aby obsługiwać użycie plików instalacji ekspresowej jest dostępna w programie Configuration Manager, ta funkcja jest obsługiwana tylko w systemie Windows 10 w wersji 1607 z aktualizacją usługi Windows Update Agent dołączone do aktualizacji wydanej w dniu 10 stycznia 2017 (wtorek poprawek). Aby uzyskać więcej informacji na temat tych aktualizacji, zobacz [obsługuje artykułu 3213986](https://support.microsoft.com/help/4009938/january-10-2017-kb3213986-os-build-14393-693). Możliwość korzystania z plików instalacji ekspresowej, po udostępnieniu dalej zestaw aktualizacji na 14 lutego 2017 r. Windows 10 w wersji 1607 bez aktualizacji i wcześniejsze wersje nie obsługują plików instalacji ekspresowej.


### <a name="to-enable-the-download-of-express-installation-files-for-windows-10-updates-on-the-server"></a>Aby włączyć pobieranie plików instalacji ekspresowej aktualizacji systemu Windows 10 na serwerze
Aby rozpocząć, synchronizacja metadanych dla plików instalacji ekspresowej systemu Windows 10, należy włączyć ją we właściwościach punktu aktualizacji oprogramowania.
1.  W konsoli programu Configuration Manager, przejdź do **administracji** > **konfiguracja lokacji** > **witryny**.
2.  Wybierz centralnej lokacji administracyjnej lub autonomicznej lokacji głównej.
3.  Na karcie **Narzędzia główne** w grupie **Ustawienia** kliknij przycisk **Konfiguruj składniki lokacji**, a następnie kliknij pozycję **Punkt aktualizacji oprogramowania**. Na **pliki aktualizacji** wybierz opcję **pobrać pełną pliki dla wszystkich aktualizacji zatwierdzonych i pliki instalacji ekspresowej dla systemu Windows 10**.

### <a name="to-enable-support-for-clients-to-download-and-install-express-installation-files"></a>Aby włączyć obsługę klientów pobrać i zainstalować pliki instalacji ekspresowej
Aby włączyć obsługę plików instalacji ekspresowej na klientach, należy włączyć plików instalacji ekspresowej na klientach w sekcji Ustawienia klienta aktualizacji oprogramowania. Spowoduje to utworzenie nowego odbiornik HTTP, która nasłuchuje żądań pobrać pliki instalacji ekspresowej na porcie, który określisz. Po wdrożeniu ustawień klienta, aby włączyć tę funkcję na komputerze klienckim, spróbuje pobrać różnica między bieżącego miesiąca systemu Windows 10 aktualizacji zbiorczej i poprzedniego miesiąca aktualizacji (klientów musi działać wersja systemu Windows 10 obsługuje pliki instalacji ekspresowej).
1.  Umożliwia obsługę plików instalacji ekspresowej we właściwościach składnika punktu aktualizacji oprogramowania (poprzedniej procedury).
2.  W konsoli programu Configuration Manager, przejdź do **administracji** > **ustawień klienta**.
3.  Wybierz ustawienia odpowiedniego klienta, a następnie na **Home** , kliknij pozycję **właściwości**.
4.  Wybierz **aktualizacji oprogramowania** skonfiguruj **tak** dla **Włącz instalację Express aktualizacji na klientach** ustawienia i skonfigurować port używany przez odbiornik HTTP na kliencie **Port używany na pobieranie zawartości dla aktualizacji Express** ustawienie.


## <a name="odata-endpoint-data-access"></a>Dostęp do danych punktu końcowego OData

 Configuration Manager udostępnia teraz punktu końcowego RESTful OData do uzyskiwania dostępu do danych programu Configuration Manager. Punkt końcowy jest zgodny z Odata w wersji 4, dzięki czemu narzędzi, takich jak Excel i Power BI, aby łatwo uzyskiwać dostęp do danych programu Configuration Manager za pośrednictwem jednego punktu końcowego. Technical Preview 1612 obsługuje tylko do odczytu obiektów w programie Configuration Manager.  

Dane, które jest obecnie dostępny w [dostawca WMI programu Configuration Manager](/sccm/develop/reference/configuration-manager-reference) również jest teraz dostępne przy użyciu nowego punktu końcowego OData RESTful. Zestawy jednostek udostępnianych przez punkt końcowy OData umożliwiają Wylicz tych samych danych, które można zbadać za pomocą dostawcy WMI.

### <a name="try-it-out"></a>Podczas próby

Przed użyciem punktu końcowego OData, należy włączyć ją dla tej lokacji.

1.  Przejdź do **administracji** > **lokacji konfiguracji** > **witryny**.
2.  Wybierz lokację główną, a następnie kliknij przycisk **właściwości**.
3.  W arkuszu właściwości lokacji głównej na karcie Ogólne kliknij **punkt końcowy REST włączyć dla wszystkich dostawców w tej witrynie**, a następnie kliknij przycisk **OK**.

W ulubionych podglądu zapytania OData, spróbuj zapytania podobne do następujących zwracać różne obiekty w programie Configuration Manager:

| Cel | Zapytanie OData |
|---|---|
| Pobierz wszystkie kolekcje | `http://localhost/CMRestProvider/Collection` |
| Pobierz kolekcję | `http://localhost/CMRestProvider/Collection('SMS00001')`
| Pobierz top 100 urządzeń w kolekcji | `http://localhost/CMRestProvider/Collection('SMS00001')/Device?$top=100` |
| Pobierz urządzeń o identyfikatorze zasobu w kolekcji | `http://localhost/CMRestProvider/Collection('SMS00001')/Device(16777573)` |
| Pobierz system operacyjny urządzenia w kolekcji | `http://localhost/CMRestProvider/Collection('SMS00001')/Device(16777573)/OPERATING_SYSTEM` |
| Pobierz użytkowników w kolekcji | `http://localhost/CMRestProvider/Collection('SMS00001')/User` |

> [!NOTE]
> Przykładowe zapytania wyświetlany w przypadku użycia tabeli *localhost* jako host name w adresie URL i mogą być używane na komputerze z uruchomionym dostawcą programu SMS. Jeśli korzystasz z zapytań na innym komputerze, zastąpić nazwę FQDN serwera z zainstalowanym dostawcą programu SMS localhost.

## <a name="azure-active-directory-onboarding"></a>Azure Active Directory dołączania

Azure Active Directory (AD) dołączania tworzy połączenie programu Configuration Manager i usługi Azure Active Directory, który będzie używany przez inne usługi w chmurze. Obecnie można to do utworzenia połączenia potrzebne do zarządzania bramy chmury.

To zadanie z administratora platformy Azure, należy wykonać, potrzebne będą poświadczenia administratora usługi Azure.

#### <a name="to-create-the-connection"></a>Aby utworzyć połączenie:

2. W **administracji** obszaru roboczego wybierz **usługi w chmurze** > **usługi Azure Active Directory** > **Dodaj usługi Azure Active Directory**.
2. Wybierz **logowania** do utworzenia połączenia z usługą Azure AD.

#### <a name="configuration-manager-client-requirements"></a>Wymagania dotyczące klienta programu Configuration Manager

Istnieje kilka wymagań dotyczących włączania tworzenia zasad użytkowników w chmurze brama zarządzania.

- Musi zostać ukończony proces przechodzenia do usługi Azure AD, a klient ma początkowo będą podłączone do sieci firmowej, aby uzyskać informacje o połączeniu.
- Klienci muszą mieć jednocześnie przyłączonych do domeny (zarejestrowane w usługi Active Directory) i przyłączone do domeny chmury (zarejestrowane w usłudze Azure AD).
- Należy uruchomić [odnajdywania użytkownika usługi Active Directory](/sccm/core/servers/deploy/configure/about-discovery-methods#active-directory-user-discovery#active-directory-user-discovery).
- Modyfikowanie klienta programu Configuration Manager, aby umożliwić żądania dotyczące zasad użytkownika za pośrednictwem Internetu, a wdrożenia zmiany do klienta. Ponieważ ta zmiana klienta odbywa się *na urządzeniu klienckim*, mimo że nie ukończono zmiany konfiguracji niezbędne dla zasad użytkownika można ją wdrożyć za pośrednictwem bramy zarządzania w chmurze.
- Punkt zarządzania musi być skonfigurowana do używania protokołu HTTPS do zabezpieczania token w sieci, a musi mieć .net 4.5 zainstalowane.

Po wprowadzeniu tych zmian konfiguracji, można utworzyć zasad użytkownika i przenieść klientów do Internetu, aby przetestować zasady. Żądania dotyczące zasad użytkownika przez bramę zarządzania chmury będą uwierzytelniane przy użyciu uwierzytelniania opartego na tokenach usługi Azure AD.

## <a name="change-to-configuring-multi-factor-authentication-for-device-enrollment"></a>Zmień na konfigurowanie uwierzytelniania wieloskładnikowego dla rejestracji urządzeń

Teraz, możesz skonfigurować uwierzytelnianie wieloskładnikowe (MFA) do zarejestrowania urządzenia w portalu Azure, opcja MFA została usunięta w konsoli programu Configuration Manager. Więcej informacji na temat konfigurowania uwierzytelniania Wieloskładnikowego dla rejestracji można znaleźć [w tym temacie Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/multi-factor-authentication-azure-active-directory).
