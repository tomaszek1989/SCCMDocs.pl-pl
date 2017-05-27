---
title: "Możliwości w Technical Preview 1612 programu Configuration Manager"
description: "Informacje na temat funkcji dostępnych w Technical Preview programu System Center Configuration Manager, wersja 1612."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bceab2e8-2f05-4a17-9ac8-a7a558670fb7
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: bcb14a2be312d4d8a4a9c235652c7bf971a7a976
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1612-for-system-center-configuration-manager"></a>Możliwości w Technical Preview 1612 System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (Technical Preview)*



Ten artykuł wprowadza do funkcji, które są dostępne w Technical Preview programu System Center Configuration Manager, wersja 1612. Można zainstalować tę wersję, aby zaktualizować i dodawać nowe funkcje do lokacji programu Configuration Manager technical preview. Przed zainstalowaniem tej wersji technical preview, przejrzyj temat wprowadzające [Technical Preview dla programu System Center Configuration Manager](../../core/get-started/technical-preview.md), aby zapoznać się z ogólnym wymagania i ograniczenia dotyczące używania technical preview, jak zaktualizować między wersjami i jak Wyraź swoją opinię dotyczącą funkcji w technical preview.    


**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  

## <a name="the-data-warehouse-service-point"></a>Punkt usługi magazynu danych
Począwszy od wersji Technical Preview 1612 punktu usługi magazynu danych pozwala na przechowywanie i raport dotyczący długoterminowe dane historyczne dla danego wdrożenia programu Configuration Manager. Jest to realizowane przez automatyczne synchronizacji z bazy danych lokacji programu Configuration Manager do bazy danych magazynu danych. Te informacje są dostępne z punktu usług raportowania.

Domyślnie po zainstalowaniu nowa rola systemu lokacji programu Configuration Manager tworzy bazy danych magazynu danych dla Ciebie w wystąpieniu programu SQL Server, które określisz. Magazyn danych obsługuje maksymalnie 2 TB danych znacznikami śledzenia zmian.  Domyślnie dane, które są synchronizowane z bazy danych lokacji zawiera grupy danych dla danych globalnych, danych lokacji, Global_Proxy, danych w chmurze i widoki bazy danych. Można również zmodyfikować, co jest zsynchronizowany dołączyć dodatkowe tabele, czyli wykluczania określonych tabel z domyślne zestawy replikacji.
Wartości domyślne są synchronizowane zawiera informacje dotyczące:
- Kondycja infrastruktury
- Zabezpieczenia
- Zgodność
- Złośliwe oprogramowanie   
- Wdrożenia oprogramowania
- Szczegóły spisu (jednak historię spisu nie jest zsynchronizowana)

Oprócz instalowania i konfigurowania bazy danych magazynu danych, są instalowane kilka nowych raportów, aby łatwo można wyszukiwać i raportować na tych danych.

### <a name="data-warehouse-dataflow"></a>Przepływ danych magazynu danych   
![Datawarehouse_flow](./media/datawarehouse.png)

| Krok         | Szczegóły  |
|:------:|-----------|  
| **1**  |     Serwer lokacji przekazuje i dane są przechowywane w bazie danych lokacji.  |  
| **2** |      Punkt usługi magazynu danych na podstawie jego harmonogram i konfiguracji, pobiera dane z bazy danych lokacji.  |  
| **3** |  Punkt usługi magazynu danych przesyła i przechowuje kopię zsynchronizowane dane w bazie danych magazynu danych. |  
| **A** |  Za pomocą wbudowanych raportów, danych wniosek o który jest przekazywany do usług Reporting Services punkt przy użyciu programu SQL Server Reporting Services. |  
| **B** |      Większość raportów są aktualne informacje, a te żądania są uruchamiane w bazie danych lokacji. |  
| **C** | Gdy raport zażąda danych historycznych za pomocą jednego z raportów z *kategorii* z **magazyn danych**, żądanie jest uruchamiane w bazie danych magazynu danych.   |  

### <a name="prerequisites-for-the-data-warehouse-service-point-and-database"></a>Wymagania wstępne dla punktu usługi magazynu danych i bazy danych
- Hierarchia musi mieć zainstalowana rola systemu lokacji punktu usług raportowania.
- Komputer, gdzie należy zainstalować rolę systemu lokacji wymaga programu .NET Framework 4.5.2 lub nowszy.
- Konto komputera komputera, na którym zainstalowano rolę systemu lokacji musi mieć uprawnienia administratora lokalnego na komputerze, który będzie obsługiwać bazę danych magazynu danych.
- Konto administracyjne, które należy zainstalować rolę systemu lokacji musi być DBO w wystąpieniu programu SQL Server, który będzie obsługiwać bazę danych magazynu danych.  
-  Baza danych jest obsługiwana:
  - Przy użyciu programu SQL Server 2012 lub nowszym, Enterprise lub Datacenter edition.
  - Domyślne lub nazwane wystąpienie
  - Na *klastra programu SQL Server*. Mimo że powinny działać w tej konfiguracji, nie zostały przetestowane i pomocy technicznej to optymalne rozwiązanie.
  - Gdy zapisane razem z jednej bazy danych lokacji lub baza danych punktu usług raportowania. Jednak zaleca się, można zainstalować na osobnym serwerze.  
- Konto, które jest używane jako *konta punktu usług raportowania* musi mieć **db_datareader** uprawnień do bazy danych magazynu danych.  
- Bazy danych nie jest obsługiwana na *grupy dostępności AlwaysOn programu SQL Server*.

### <a name="install-the-data-warehouse"></a>Zainstalować Magazyn danych
Zainstaluj rolę systemu lokacji magazynu danych w centralnej lokacji administracyjnej lub lokacji głównej przy użyciu **lokacji Kreator dodawania ról systemu** lub **lokacji Kreator tworzenia serwera systemu**. Zobacz [zainstalować role systemu lokacji](/sccm/core/servers/deploy/configure/install-site-system-roles) uzyskać więcej informacji. Hierarchia obsługuje wiele wystąpień tej roli, ale tylko jedno wystąpienie jest obsługiwana w każdej lokacji.  

Podczas instalowania roli programu Configuration Manager utworzy bazę danych magazynu danych w wystąpieniu programu SQL Server, który określisz. W przypadku określenia nazwy istniejącej bazy danych (tak jak w przypadku możesz [przenieść bazę danych magazynu danych na nowy serwer SQL](#move-the-data-warehouse-database)), programu Configuration Manager nie tworzy nową bazę danych, ale zamiast tego używa jednego użytkownika.

#### <a name="configurations-used-during-installation"></a>Konfiguracje używane podczas instalacji
Użyj poniższych informacji do ukończenia instalacji roli systemu lokacji:

**Wybór roli systemu** strony:  
Zanim Kreator wyświetla opcję Wybierz i zainstaluj punkt usługi magazynu danych, należy zainstalować punkt usług raportowania.

**Ogólne** strony: Wymagane są następujące informacje ogólne:
- **Ustawienia bazy danych programu Configuration Manager:**   
  - **Nazwa serwera** — Określ nazwę FQDN serwera obsługującego bazę danych lokacji. Jeśli nie używasz domyślnego wystąpienia programu SQL Server, należy określić wystąpienie po nazwy FQDN w następującym formacie: ***&lt;Sqlserver_FQDN >\&< nazwa_wystąpienia >***
  - **Nazwa bazy danych** — Określ nazwę bazy danych lokacji.
  -    **Sprawdź, czy** -kliknij **Sprawdź** aby upewnić się, że połączenie z bazą danych lokacji zakończyła się powodzeniem.
</br></br>
- **Ustawienia bazy danych magazynu danych:**
  -    **Nazwa serwera** — Podaj nazwę FQDN serwera, który obsługuje punkt usługi magazynu danych i bazy danych. Jeśli nie używasz domyślnego wystąpienia programu SQL Server, należy określić wystąpienie po nazwy FQDN w następującym formacie: ***&lt;Sqlserver_FQDN >\&< nazwa_wystąpienia >***
  -    **Nazwa bazy danych** — Określ nazwę FQDN dla bazy danych magazynu danych.  Program Configuration Manager utworzy bazy danych o tej nazwie. Jeśli określisz nazwę bazy danych, która już istnieje w wystąpieniu programu SQL server Configuration Manager będzie używać tej bazy danych.
  -    **Sprawdź, czy** -kliknij **Sprawdź** aby upewnić się, że połączenie z bazą danych lokacji zakończyła się powodzeniem.

**Ustawienia synchronizacji** strony:   
- **Ustawienia danych:**
  - **Grupy replikacji, aby zsynchronizować** — wybierz grupy danych mają być synchronizowane. Informacje o różnych typach danych grup, zobacz [replikacji bazy danych](/sccm/core/servers/manage/data-transfers-between-sites#a-namebkmkdbrepa-database-replication) i **widoki rozproszone** w [transferu danych między lokacjami](/sccm/core/servers/manage/data-transfers-between-sites).
  - **Tabel dołączonych do synchronizowania** — Określ nazwę każdego dodatkowego tabeli mają być synchronizowane. Wiele tabel należy oddzielić przecinkami. Tych tabel zostaną zsynchronizowane z bazy danych lokacji oprócz wybranych grup replikacji.
  - **Tabele wykluczane w celu synchronizowania** — Określ nazwę dla poszczególnych tabel z synchronizacji grupy replikacji. Tabele, które określisz zostaną wykluczone z. Wiele tabel należy oddzielić przecinkami.
- **Ustawienia synchronizacji:**
  - **Interwał synchronizacji (w minutach)** — Określ wartość w minutach. Po upływie interwału uruchamia nowy synchronizacji. Obejmuje to obsługę zakres od 60 do 1440 minut (24 godziny).
  - **Harmonogram** -określ dni, które mają uruchamianie synchronizacji.

**Dostęp do punktu raportowania**:   
Po zainstalowaniu roli magazynu danych, upewnij się, konto, które jest używane jako *konta punktu usług raportowania* ma **db_datareader** uprawnień do bazy danych magazynu danych.

#### <a name="troubleshoot-installation-and-data-synchronization"></a>Rozwiązywanie problemów z synchronizacją instalacji i danych
Użyj następujących dziennikach do badania problemów z instalacji punktu usługi magazynu danych lub synchronizacji danych:
- **DWSSMSI.log** i **DWSSSetup.log** -Użyj w tych dziennikach do badania błędy, podczas instalowania punktu usług magazynu danych.
-     **Microsoft.ConfigMgrDataWarehouse.log** — Użyj tego dziennika do badania synchronizacji danych między bazą danych lokacji do bazy danych magazynu danych.

### <a name="reporting"></a>Raportowanie
Po zainstalowaniu roli systemu lokacji magazynu danych, następujące raporty są dostępne na punktu usług raportowania z *kategorii* z **magazynu danych:**

|Raport                   | Szczegóły                                  |
|-------------------------|------------------------------------------|
| **Raport wdrażania aplikacji** | Wyświetlić szczegóły dotyczące wdrażania aplikacji dla określonej aplikacji i komputera.|
| **Raport zgodności aktualizacji oprogramowania i ochrony punktu końcowego**   | Wyświetl komputery, których brakuje aktualizacji oprogramowania.|
| **Raport o spisie sprzętu ogólne**  | Wyświetl wszystkie spisu sprzętu dla określonego komputera.|
| **Raport ze spisu oprogramowania ogólne**  | Wyświetl wszystkie spisu oprogramowania dla określonego komputera.|
| **Przegląd kondycji infrastruktury**  |Zawiera omówienie kondycję infrastruktury programu Configuration Manager.|
| **Lista wykryto złośliwe oprogramowanie**  |Widok złośliwego oprogramowania, które zostały wykryte w organizacji.|
|** Oprogramowania dystrybucji podsumowania raportu ** | Podsumowanie dystrybucji oprogramowania dla określonych anonsów i maszyny.|

### <a name="move-the-data-warehouse-database"></a>Przenieś bazy danych magazynu danych
Aby przenieść bazę danych magazynu danych na nowy serwer SQL, wykonaj następujące kroki:

  1. Sprawdź bieżącą konfigurację bazy danych, a następnie Zapisz szczegóły konfiguracji, w tym:  
   - Grupy danych, które można synchronizować
   - Tabele można dołączać lub wykluczać z synchronizacji       

   Po Przywróć bazę danych do nowego serwera i ponownie zainstalować rolę systemu lokacji będzie ponownie skonfigurować te grupy danych i tabele.  

  2. Użyj programu SQL Server Management Studio do wykonania kopii zapasowej bazy danych magazynu danych, a następnie ponownie, aby przywrócić tę bazę danych do programu SQL server na nowym komputerze, który będzie udostępniał magazyn danych.

  Po przywróceniu bazy danych na nowy serwer, upewnij się, że uprawnień dostępu do bazy danych są takie same na nową bazę danych magazynu danych, jak znajdowały się one w oryginalnej bazy danych magazynu danych.

  3. Aby usunąć rolę systemu lokacji punktu usługi magazynu danych z bieżącego serwera, należy użyć konsoli programu Configuration Manager.

  4. Zainstaluj nowy punkt usługi magazynu danych i określ nazwę nowego serwera SQL i wystąpienie bazy danych magazynu danych, należy przywrócić.

  5. Po zainstalowaniu roli systemu lokacji przeniesienie zostało ukończone.

Możesz przejrzeć następujące dzienników programu Configuration Manager, aby potwierdzić, że pomyślnie ponownie zainstalował Rola systemu lokacji:  
- **DWSSMSI.log** i **DWSSSetup.log** -Użyj w tych dziennikach do badania błędy, podczas instalowania punktu usług magazynu danych.
-     **Microsoft.ConfigMgrDataWarehouse.log** — Użyj tego dziennika do badania synchronizacji danych między bazą danych lokacji do bazy danych magazynu danych.


## <a name="content-library-cleanup-tool"></a>Narzędzie do oczyszczania biblioteki zawartości
Począwszy od wersji Technical Preview 1612, można użyć nowego narzędzia wiersza polecenia (**ContentLibraryCleanup.exe**) aby usunąć zawartość, która jest już skojarzony z dowolnego pakietu lub aplikacji z punktu dystrybucji (oddzielony zawartości). To narzędzie jest nazywany narzędzia Oczyszczanie biblioteki zawartości.

To narzędzie dotyczy wyłącznie zawartość w punkcie dystrybucji, które określisz po uruchomieniu narzędzia i nie można usunąć zawartość z biblioteki zawartości na serwerze lokacji.

Po zainstalowaniu Technical Preview 1612 można znaleźć **ContentLibraryCleanup.exe** w *%CM_Installation_Path%\cd.latest\SMSSETUP\TOOLS\ContentLibraryCleanup\* folder na serwerze lokacji Technical Preview.

Narzędzie wydanej z tym Technical Preview ma zastąpić starsze wersje podobne narzędzia opublikowany dla wcześniejszej produktów Configuration Manager. Mimo że ta wersja narzędzia przestanie działać po 1 marca 2017 nowe wersje spowoduje zwolnienie z przyszłych wersji zapoznawczych techniczne, dopóki to narzędzie jest wydane jako część bieżącej gałęzi lub produkcyjnym gotowy wydania poza pasmem.

### <a name="requirements"></a>Wymagania  
 - Narzędzie można uruchomić bezpośrednio na komputerze, który obsługuje punkt dystrybucji lub zdalnie z innego serwera. Narzędzie można uruchomić tylko z pojedynczego punktu dystrybucji w czasie.
 - Konto użytkownika, który uruchomił narzędzie bezpośrednio musi mieć uprawnienia administracji opartej na rolach, które są równe pełny Administrator w hierarchii programu Configuration Manager.  Narzędzie nie działa, gdy konto użytkownika ma udzielone uprawnienia jako członek grupy zabezpieczeń systemu Windows z uprawnieniami pełnego dostępu administratora.

### <a name="modes-of-operation"></a>Tryby operacyjne
Narzędzie można uruchomić w dwóch trybach:
  1.    **Tryb symulacji**:   
      Jeśli nie określisz **/delete** przełącznika, narzędzie działa w trybie symulacji i identyfikuje zawartość, do której zostaną usunięte z punktu dystrybucji, ale nie faktycznie usunięcia żadnych danych.

      - Po uruchomieniu narzędzia w tym trybie, informacje o zawartości, które zostałyby usunięte automatycznie są zapisywane w pliku dziennika narzędzia. Użytkownik nie jest monitowany o potwierdzenie każdej operacji usunięcia potencjalne.
      - Domyślnie plik dziennika są zapisywane do folderu tymczasowego użytkowników na komputerze, na którym uruchomiono narzędzie, jednak można użyć przełącznika/log przekierowanie pliku dziennika do innej lokalizacji.  
      </br>

    Firma Microsoft zaleca, uruchom narzędzie w tym trybie i przejrzeć wynikowy plik dziennika przed uruchomieniem narzędzia z opcją/DELETE.  

  2. **Usuń tryb**: Po uruchomieniu narzędzia z **/delete** przełącznika, narzędzie działa w trybie delete.

     - Po uruchomieniu narzędzia w tym trybie, oddzielone zawartość, która znajduje się w punkcie dystrybucji określonego mogą zostać usunięte z biblioteki zawartości w punkcie dystrybucji.
     -     Przed usunięciem każdego pliku, użytkownik jest monitowany o potwierdzenie, że należy usunąć plik.  Możesz wybrać **Y** tak, **N** nie, lub **tak na wszystkie** Aby pominąć dalsze monity i usuń zawartość wszystkich oddzielone.  
     </br>

     Firma Microsoft zaleca, uruchom narzędzie w trybie symulacji i przejrzeć wynikowy plik dziennika przed uruchomieniem narzędzia z opcją/DELETE.  

Po uruchomieniu narzędzia Oczyszczanie biblioteki zawartości w trybie, automatycznie tworzy plik dziennika o nazwę, która zawiera narzędzie działa w trybie, nazwę punktu dystrybucji, daty i godziny operacji. Plik dziennika nawiązywane automatycznie po zakończeniu działania narzędzia. Domyślnie ten dziennik jest zapisywany do użytkowników **temp** folderu na komputerze, na którym jest uruchomione narzędzie., jednak umożliwia przełącznik w wierszu polecenia przekierowania pliku dziennika do innej lokalizacji, w tym udziale sieciowym.   


### <a name="run-the-tool"></a>Uruchom narzędzie
Aby uruchomić narzędzie:
1. Otwórz wiersz polecenia administracyjne z folderu, który zawiera **ContentLibraryCleanup.exe**.  
2. Następnie wprowadź wiersz polecenia, który zawiera przełączników wiersza polecenia wymagane i opcjonalne przełączniki, którego chcesz użyć.

**Znany problem** po uruchomieniu narzędzia wdrażanie lub pakietu nie powiodło się lub jest w toku może być zwracany błąd podobnie do poniższego:
-  *System.InvalidOperationException: Ta biblioteka zawartości nie można oczyścić teraz ponieważ pakiet <packageID> nie jest w pełni zainstalowany.*

**Obejście problemu:** Brak. Narzędzie nie niezawodne identyfikować oddzielone pliki, gdy zawartość jest w toku lub nie udało się wdrożyć. W związku z tym narzędzie nie pozwoli do czyszczenia zawartości do momentu rozwiązania problemu.



### <a name="command-line-switches"></a>Przełączniki wiersza polecenia  
Następujące przełączniki wiersza polecenia można użyć w dowolnej kolejności.   

|Przełącznik|Szczegóły|
|---------|-------|
|**/ DELETE**  |**Opcjonalne** </br> Użyj tego przełącznika, jeśli chcesz usunąć zawartość z punktu dystrybucji. Zostanie wyświetlony monit, przed usunięciem zawartości. </br></br> Jeśli ten przełącznik nie jest używany, narzędzie rejestruje wyniki o tym, jaka zawartość zostaną usunięte, ale nie powoduje usunięcia zawartości z punktu dystrybucji. </br></br> Przykład: ***/ Delete server1.contoso.com /dp ContentLibraryCleanup.exe*** |
| **/q**       |**Opcjonalne** </br> Uruchom narzędzie w trybie cichym, który powoduje pominięcie wszystkich monitów (na przykład monity podczas usuwania zawartości), a nie automatycznie otworzyć plik dziennika. </br></br> Przykład: ***ContentLibraryCleanup.exe /q /dp serwer1.contoso.com*** |
| **/dp &lt;FQDN punktu dystrybucji >**  | **Wymagane** </br> Podaj pełną nazwę domeny (FQDN) punktu dystrybucji, które chcesz wyczyścić. </br></br> Przykład:  ***ContentLibraryCleanup.exe /dp serwer1.contoso.com***|
| **/PS &lt;lokacji głównej nazwy FQDN >**       | **Opcjonalny** podczas czyszczenia zawartości z punktu dystrybucji w lokacji głównej.</br>**Wymagane** podczas czyszczenia zawartości z punktu dystrybucji w lokacji dodatkowej. </br></br> Określ, czy nazwa FQDN lokacji głównej punktu dystrybucji należy do lub elementu nadrzędnego głównej nadrzędnej, gdy punkt dystrybucji znajduje się w lokacji dodatkowej. </br></br> Przykład: ***ContentLibraryCleanup.exe /dp server1.contoso.com /ps siteserver1.contoso.com*** |
| **/sc &lt;kod lokacji głównej >**  | **Opcjonalny** podczas czyszczenia zawartości z punktu dystrybucji w lokacji głównej.</br>**Wymagane** podczas czyszczenia zawartości z punktu dystrybucji w lokacji dodatkowej. </br></br> Określ kod lokacji punktu dystrybucji należy do lokacji głównej lub z nadrzędnej lokacji głównej, gdy punkt dystrybucji znajduje się w lokacji dodatkowej.</br></br> Przykład: ***ContentLibraryCleanup.exe /dp server1.contoso.com /sc ABC*** |
| **/ log<log file directory>**       |**Opcjonalne** </br> Określ katalog, aby umieścić pliki dziennika w. To być lokalny lub Udostępnij na sieć.</br></br> Jeśli ten przełącznik nie jest używany, pliki dziennika są automatycznie umieszczane w folderze tymczasowym użytkowników.</br></br> Przykład dysku lokalnego: ***/ ContentLibraryCleanup.exe /dp server1.contoso.com log C:\Users\Administrator\Desktop*** </br></br>Przykład udziału sieciowego: ***/ Log server1.contoso.com /dp ContentLibraryCleanup.exe \\ &lt;udostępnić >\&< folder >***|


## <a name="improvements-for-in-console-search"></a>Udoskonalenia w zakresie wyszukiwania w konsoli
Na podstawie User Voice opinii, dodaliśmy następujące ulepszenia dotyczące wyszukiwania w konsoli:
 - **Ścieżka obiektu:**  
  Wiele obiektów obsługuje teraz nową kolumnę o nazwie **ścieżki obiektu**.  Podczas wyszukiwania i zawierało tej kolumny w wynikach wyświetlania, można wyświetlić ścieżkę do każdego obiektu. Na przykład, jeśli podczas wykonywania wyszukiwania dla aplikacji w węźle aplikacje wyszukiwania węzły podrzędne *ścieżki obiektu* kolumny w okienku wyników zostanie wyświetlona ścieżka do każdego obiektu zwróconego.   

- **Zachowania wyszukiwany tekst:**  
  Gdy wprowadź tekst w polu tekstowym wyszukiwania, a następnie przełączać się między wyszukiwanie węzła podrzędnego i bieżącego węzła, wpisany tekst teraz utrwalić i pozostaną dostępne dla nowego wyszukiwania bez konieczności wpisz je ponownie.

- **Zachowania zdecydować, aby wyszukać węzły podrzędne:**  
 Opcja Wybierz albo wyszukiwania *bieżącego węzła* lub *wszystkie węzły podrzędne* teraz będzie nadal występować po zmianie pracy w węźle.   To nowe zachowanie oznacza, że nie trzeba stale ustawiony decyzji, jak przenosić konsoli.  Domyślnie po otwarciu konsoli opcją jest wyszukiwanie tylko bieżącego węzła.

## <a name="prevent-installation-of-an-application-if-a-specified-program-is-running"></a>Zapobieganie instalacji aplikacji, uruchomienie określonego programu.
Lista plików wykonywalnych (z rozszerzeniem .exe) można teraz skonfigurować we właściwościach typu wdrożenia, które uruchomiona, spowoduje zablokowania instalacji aplikacji. Po próbie instalacji użytkownicy będą widzieć okno dialogowe z pytaniem je, aby zamknąć procesy, które blokują instalacji.

### <a name="try-it-out"></a>Wypróbuj to
Aby skonfigurować listę plików wykonywalnych
1.    Na stronie właściwości każdego typu wdrożenia wybierz **Obsługa Instalator** kartę.
2.    Kliknij przycisk **Dodaj**, aby dodać jeden z plików wykonywalnych więcej do listy (na przykład **Edge.exe**)
3.    Kliknij przycisk **OK** aby zamknąć okno dialogowe właściwości typu wdrożenia.

Teraz podczas wdrażania tej aplikacji dla użytkownika lub urządzenia i jeden z plików wykonywalnych dodawane jest uruchomiona, użytkownicy otrzymają Centrum oprogramowania okno dialogowe z informacją, których instalacja nie powiodła się, ponieważ aplikacja jest uruchomiona.

## <a name="new-windows-hello-for-business-notification-for-end-users"></a>Nowy Windows Hello Powiadomienia biznesowe dla użytkowników końcowych

Nowe powiadomienie systemu Windows 10 informuje użytkownicy końcowi muszą zabrać dodatkowe akcje do wykonania Windows Hello Instalatora biznesowych (na przykład ustawienie kodu PIN).

## <a name="windows-store-for-business-support-in-configuration-manager"></a>Sklep Windows dla wsparcia biznesowego w programie Configuration Manager

Teraz można wdrażać licencjonowane aplikacje online z celem wdrożenia **dostępne** ze Sklepu Windows dla firm do komputerów z systemem klienta programu Configuration Manager.
Aby uzyskać więcej informacji, zobacz [zarządzania aplikacjami ze Sklepu Windows dla firm z System Center Configuration Manager](https://docs.microsoft.com/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business).

Obsługa ta funkcja jest obecnie dostępna tylko do komputerów z systemem Windows 10 RS2 kompilacji (wersja zapoznawcza).

## <a name="return-to-previous-page-when-a-task-sequence-fails"></a>Powrócić do poprzedniej strony, gdy sekwencja zadań zakończy się niepowodzeniem.
Możesz teraz powrócić do poprzedniej strony podczas uruchamiania sekwencji zadań i awarii. Przed tej wersji było konieczne ponowne uruchomienie sekwencji zadań po wystąpił błąd. Na przykład można użyć **Wstecz** przycisku w następujących scenariuszach:

- Po uruchomieniu komputera w środowisku Windows PE, okno dialogowe ładowania sekwencji zadań może być wyświetlany, zanim sekwencja zadań będzie dostępna. Po kliknięciu przycisku Dalej w tym scenariuszu na ostatniej stronie sekwencji zadań wyświetla komunikat, że są sekwencji zadań. Teraz, można kliknąć przycisk **Wstecz** ponowić wyszukiwanie uzyskać dostępne sekwencje zadań. Ten proces można powtarzać momentu udostępnienia sekwencji zadań.
- Podczas uruchamiania sekwencji zadań, ale zależne pakiety zawartości nie są jeszcze dostępne w punktach dystrybucji, sekwencja zadań kończy się niepowodzeniem. Możesz teraz dystrybucji brakującą zawartość (jeśli go nie została jeszcze rozesłana) lub poczekaj, aż zawartość ma być dostępna w punktach dystrybucji, a następnie kliknij **Wstecz** mieć wyszukiwania sekwencji zadań ponownie dla zawartości.

## <a name="express-installation-files-support-for-windows-10-updates"></a>Pliki instalacji ekspresowej obsługę aktualizacji systemu Windows 10
Dodaliśmy pliki instalacji ekspresowej obsługę aktualizacji systemu Windows 10 w programie Configuration Manager. Używając obsługiwanej wersji systemu Windows 10 teraz służy ustawień programu Configuration Manager do pobierania różnicy między bieżącym miesiącu systemu Windows 10 zbiorczej aktualizacji i aktualizacji w poprzednim miesiącu. Obecnie w programie Configuration Manager bieżącej gałęzi, pełnego systemu Windows 10 aktualizacji zbiorczej (w tym wszystkie aktualizacje z poprzednich miesięcy) są pobierane co miesiąc. Przy użyciu plików instalacji ekspresowej zapewnia mniejsze pliki do pobrania i skrócenie czasu instalacji na komputerach klienckich.

> [!IMPORTANT]
> Podczas ustawienia do obsługi plików instalacji ekspresowej plików jest dostępna w programie Configuration Manager, ta funkcja jest obsługiwana tylko w systemie Windows 10 wersji 1607 z aktualizacją Windows Update Agent dołączonej do aktualizacji wydanych 10 stycznia 2017 (wtorek poprawek). Aby uzyskać więcej informacji na temat tych aktualizacji, zobacz [obsługuje artykułu 3213986](https://support.microsoft.com/help/4009938/january-10-2017-kb3213986-os-build-14393-693). Możesz korzystać z plików instalacji ekspresowej podczas następnego zestawu aktualizacji są wydawane na 14 lutego 2017. System Windows 10 wersji 1607 bez aktualizacji i wcześniejsze wersje nie obsługują pliki instalacji ekspresowej.


### <a name="to-enable-the-download-of-express-installation-files-for-windows-10-updates-on-the-server"></a>Aby umożliwić pobieranie plików instalacji ekspresowej aktualizacji systemu Windows 10 na serwerze
Aby rozpocząć synchronizowanie metadanych dla systemu Windows 10 pliki instalacji ekspresowej, można włączyć je w oknie Właściwości punktu aktualizacji oprogramowania.
1.    W konsoli programu Configuration Manager, przejdź do **Administracja** > **konfiguracja lokacji** > **witryny**.
2.    Wybierz centralnej lokacji administracyjnej lub autonomicznej lokacji głównej.
3.    Na karcie **Narzędzia główne** w grupie **Ustawienia** kliknij przycisk **Konfiguruj składniki lokacji**, a następnie kliknij pozycję **Punkt aktualizacji oprogramowania**. Na **pliki aktualizacji** zaznacz **pobierania plików pełnego wszystkie aktualizacje zatwierdzone i express pliki instalacyjne dla systemu Windows 10**.

### <a name="to-enable-support-for-clients-to-download-and-install-express-installation-files"></a>Aby włączyć obsługę klientów pobrać i zainstalować pliki instalacji ekspresowej
Aby włączyć obsługę plików instalacji ekspresowej na klientach, należy włączyć pliki instalacji ekspresowej na komputerach klienckich w sekcji Ustawienia klienta aktualizacji oprogramowania. Spowoduje to utworzenie nowego odbiornik HTTP, który nasłuchuje żądań pobrać pliki instalacji ekspresowej na porcie, który określisz. Gdy wdrożyć ustawienia klienta, aby włączyć tę funkcję na komputerze klienckim, podejmuje próbę pobrania różnica między bieżącym miesiącu systemu Windows 10 zbiorczej aktualizacji i aktualizacji w poprzednim miesiącu (klienci muszą uruchomić wersji systemu Windows 10, że obsługuje express pliki instalacyjne).
1.    Włącz obsługę plików instalacji ekspresowej we właściwościach składnika punktu aktualizacji oprogramowania (poprzedniej procedury).
2.    W konsoli programu Configuration Manager, przejdź do **Administracja** > **ustawień klienta**.
3.    Wybierz ustawienia odpowiedniego klienta, a następnie na **Home** , kliknij pozycję **właściwości**.
4.    Wybierz **aktualizacji oprogramowania** skonfiguruj **tak** dla **Włącz instalację Express aktualizacji na klientach** i konfiguracji port używany przez odbiornik HTTP na kliencie **Port używany do pobierania zawartości dla aktualizacji Express** ustawienie.


## <a name="odata-endpoint-data-access"></a>Dostęp do danych punktu końcowego OData

 Program Configuration Manager udostępnia teraz punktu końcowego RESTful OData do uzyskiwania dostępu do danych programu Configuration Manager. Punkt końcowy jest zgodny z Odata w wersji 4, co umożliwia narzędzi, takich jak program Excel i Power BI łatwy dostęp do danych programu Configuration Manager za pośrednictwem pojedynczego punktu końcowego. Technical Preview 1612 obsługuje tylko do odczytu obiektów w programie Configuration Manager.  

Dane, które są aktualnie dostępne w [dostawcy WMI programu Configuration Manager](/sccm/develop/reference/configuration-manager-reference) również jest teraz dostępny za pomocą nowego punktu końcowego OData RESTful. Zestawów jednostek udostępnianych przez punkt końcowy OData umożliwiają Wylicz dane, które można tworzyć zapytania przy użyciu dostawcy WMI.

### <a name="try-it-out"></a>Wypróbuj to

Przed użyciem punktu końcowego OData, należy włączyć ją dla tej lokacji.

1.  Przejdź do **Administracja** > **lokacji konfiguracji** > **witryny**.
2.  Wybierz lokację główną, a następnie kliknij przycisk **właściwości**.
3.  Na karcie Ogólne arkusza właściwości lokacji głównej, kliknij przycisk **REST włączyć punkt końcowy dla wszystkich dostawców w tej witrynie**, a następnie kliknij przycisk **OK**.

W ulubionej przeglądarce zapytania OData spróbuj zapytania podobne do następujących zwrócić różnych obiektów w programie Configuration Manager:

| Cel | Zapytania OData |
|---|---|
| Pobierz wszystkie kolekcje | `http://localhost/CMRestProvider/Collection` |
| Pobierz kolekcję | `http://localhost/CMRestProvider/Collection('SMS00001')`
| Pobierz pierwsze 100 urządzeń w kolekcji | `http://localhost/CMRestProvider/Collection('SMS00001')/Device?$top=100` |
| Pobierz urządzeń o identyfikatorze zasobu w kolekcji | `http://localhost/CMRestProvider/Collection('SMS00001')/Device(16777573)` |
| Pobierz system operacyjny urządzenia w kolekcji | `http://localhost/CMRestProvider/Collection('SMS00001')/Device(16777573)/OPERATING_SYSTEM` |
| Pobierz użytkowników w kolekcji | `http://localhost/CMRestProvider/Collection('SMS00001')/User` |

> [!NOTE]
> Zapytania przykładzie pokazano użycie tabeli *localhost* jako host nazw w adresie URL i może być używana na komputerze z uruchomionym dostawcą programu SMS. Jeśli używasz zapytań z innego komputera, zastąp nazwę FQDN serwera z zainstalowanym dostawcą programu SMS localhost.

## <a name="azure-active-directory-onboarding"></a>Dołączanie do usługi Azure Active Directory

Dołączanie do usługi Azure Active Directory (AD) tworzy połączenie między programu Configuration Manager i usługi Azure Active Directory do użycia przez inne usługi w chmurze. Obecnie służy ona do utworzenia połączenia potrzebnych do zarządzania bramy chmury.

Potrzebne będą poświadczenia administratora Azure wykonywać zadania z administrator systemu Azure.

#### <a name="to-create-the-connection"></a>Aby utworzyć połączenie:

2. W **Administracja** obszaru roboczego, wybierz **usług w chmurze** > **Azure Active Directory** > **dodać Azure Active Directory**.
2. Wybierz **Zaloguj** do utworzenia połączenia z usługą Azure AD.

#### <a name="configuration-manager-client-requirements"></a>Wymagania dotyczące klienta programu Configuration Manager

Istnieje kilka wymagań umożliwiających tworzenie zasad użytkownika w chmurze brama zarządzania.

- Musi zostać ukończony proces dołączania Azure AD, a klient ma być początkowo podłączony do sieci firmowej, aby uzyskać informacje o połączeniu.
- Klienci muszą być zarówno przyłączonych do domeny (zarejestrowanych w usłudze Active Directory) i chmury przyłączone do domeny (zarejestrowana w usłudze Azure AD).
- Należy uruchomić [odnajdywania użytkownika usługi Active Directory](/sccm/core/servers/deploy/configure/about-discovery-methods#active-directory-user-discovery#active-directory-user-discovery).
- Należy zmodyfikować klienta programu Configuration Manager, aby umożliwić żądania dotyczące zasad użytkownika w Internecie i wdrożenia zmiany do klienta. Ponieważ ta zmiana klient ma miejsce *na urządzeniu klienckim*, jego można wdrożyć za pośrednictwem bramy zarządzania chmury, mimo że nie zostały wykonane zmiany konfiguracji niezbędne dla zasad użytkownika.
- Ten punkt zarządzania musi być skonfigurowany do używania protokołu HTTPS do zabezpieczania token w sieci, a musi mieć .net 4.5 zainstalowane.

Po wprowadzeniu tych zmian konfiguracji, można utworzyć zasady użytkownika i przenieść klientów internetowych do testowania zasad. Żądania dotyczące zasad użytkownika za pośrednictwem bramy zarządzania chmury są uwierzytelniane przy użyciu uwierzytelniania opartego na tokenach Azure AD.

## <a name="change-to-configuring-multi-factor-authentication-for-device-enrollment"></a>Zmień na konfigurowanie uwierzytelnianie wieloskładnikowe dla rejestracji urządzeń

Teraz, możesz skonfigurować uwierzytelnianie wieloskładnikowe (MFA) do rejestracji urządzenia w portalu Azure, usunięto opcję MFA w konsoli programu Configuration Manager. Można znaleźć więcej informacji na temat konfigurowania MFA do rejestracji [w tym temacie Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/multi-factor-authentication-azure-active-directory).

