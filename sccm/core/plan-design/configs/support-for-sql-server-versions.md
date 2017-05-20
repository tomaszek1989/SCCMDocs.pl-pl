---
title: "Obsługiwane wersje programu SQL Server | Dokumentacja firmy Microsoft"
description: "Pobierz wersję i konfiguracji wymagania programu SQL Server do obsługi bazy danych lokacji programu System Center Configuration Manager."
ms.custom: na
ms.date: 05/10/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 35e237b6-9f7b-4189-90e7-8eca92ae7d3d
caps.latest.revision: 21
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f809c9327db9f298168674add2d09820fdecd1b8
ms.openlocfilehash: 4166560602edf6eb299511c8b59dc3903e3bfffc
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="supported-sql-server-versions-for-system-center-configuration-manager"></a>Obsługiwane wersje programu SQL Server dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Każda lokacja programu System Center Configuration Manager wymaga obsługiwanych wersji programu SQL Server i konfigurację do obsługi bazy danych lokacji.  

##  <a name="bkmk_Instances"></a> Wystąpienia i lokalizacje programu SQL Server  
 **Witryny administracji centralnej i lokacje główne:**  
Baza danych lokacji musi korzystać z pełnej instalacji programu SQL Server.  

 Program SQL Server może znajdować się na:  

-   Komputer serwera lokacji.  
-   Komputer, który jest zdalnie z serwera lokacji.  

Obsługiwane są następujące wystąpienia:  

-   Domyślne lub nazwane wystąpienie programu SQL Server.  
-   Wiele konfiguracji wystąpienia.  
-   Klaster programu SQL Server. Zobacz [używanie klastra programu SQL Server do obsługi bazy danych lokacji](../../../core/servers/deploy/configure/use-a-sql-server-cluster-for-the-site-database.md).
-   Grupy dostępności AlwaysOn programu SQL Server. Ta opcja wymaga programu Configuration Manager w wersji 1602 lub nowszej. Aby uzyskać szczegółowe informacje, zobacz [AlwaysOn programu SQL Server dla wysokiej dostępności bazy danych lokacji programu System Center Configuration Manager](../../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md).


 **Lokacje dodatkowe:**  
 Baza danych lokacji można użyć domyślnego wystąpienia pełnej instalacji programu SQL Server lub SQL Server Express.  

 Program SQL Server musi znajdować się na komputerze serwera lokacji.  

 **Ograniczenia dotyczące obsługi**   
 Nie są obsługiwane następujące konfiguracje:
 -   Klastra programu SQL Server w konfiguracji klastra równoważenia obciążenia sieciowego (NLB)
 -   Klastra programu SQL Server na udostępnionego woluminu klastra (CSV)
 -   Dublowanie technologii i peer-to-peer replikacji datbase programu SQL Server

Replikacji transakcyjnej programu SQL Server jest obsługiwana tylko w przypadku replikacji obiektów do punktów zarządzania, które są skonfigurowane do używania [bazy danych repliki](https://technet.microsoft.com/library/mt608546.aspx).  

##  <a name="bkmk_SQLVersions"></a> Obsługiwane wersje programu SQL Server  
 W hierarchii z wieloma lokacjami różnymi lokacjami można używać różnych wersji programu SQL Server do obsługi bazy danych lokacji, tak długo, jak zostały spełnione następujące warunki:
 -  Program Configuration Manager obsługuje wersje programu SQL Server, którego używasz.
 -  Wersje programu SQL Server, którego używasz pozostają w pomocy technicznej firmy Microsoft.
 -  Program SQL Server obsługuje replikację między dwoma wersjami programu SQL Server.  Na przykład [programu SQL Server nie obsługuje replikacji między programu SQL Server 2008 R2 i SQL Server 2016](https://docs.microsoft.com/sql/relational-databases/replication/deprecated-features-in-sql-server-replication).



 O ile nie określono inaczej, następujące wersje programu SQL Server są obsługiwane z wszystkich aktywnych wersji programu System Center Configuration Manager. Jeśli obsługa nowej wersji programu SQL Server lub z dodatkiem Service pack jest dodawany, będą wyświetlane informacje dotyczące wersji programu Configuration Manager, który dodaje obsługę. Podobnie jeśli jest przestarzały pomocy technicznej, poszukaj szczegółowych informacji o usterce wersji programu Configuration Manager.   

Obsługa dla określonego dodatku service pack programu SQL Server obejmuje aktualizacje zbiorcze tego dodatku service pack, chyba że aktualizacji zbiorczej przerywa wstecz do nowszej wersji pakietu usługi podstawowej. Gdy nie wersji dodatku service pack należy zauważyć, pomoc techniczna jest dla tej wersji programu SQL Server bez dodatku service pack. W przyszłości Jeśli wydaniu dodatku service pack dla danej wersji instrukcji obsługi oddzielnych będą deklarowane przed tej nowej wersji dodatku service pack jest obsługiwany.


> [!IMPORTANT]  
>  Korzystając z programu SQL Server Standard dla bazy danych w witrynie Administracja centralna, można Ogranicz całkowitą liczbę klientów, którzy obsługują hierarchii. Zobacz [Wartości dotyczące rozmiarów i skalowania](../../../core/plan-design/configs/size-and-scale-numbers.md).

### <a name="sql-server-2016-sp1-standard-enterprise"></a>SQL Server 2016 z dodatkiem SP1: Standard, Enterprise  
Tej wersji programu SQL Server możesz używać bez ograniczeń minimalnej wersji aktualizacji zbiorczej dla następujących elementów:  

-   Witryny Administracja centralna  
-   Lokacja główna  
-   Lokację dodatkową  

### <a name="sql-server-2016-standard-enterprise"></a>Program SQL Server 2016: Standard, Enterprise  
Tej wersji programu SQL Server możesz używać bez ograniczeń minimalnej wersji aktualizacji zbiorczej dla następujących elementów:  

-   Witryny Administracja centralna  
-   Lokacja główna  
-   Lokację dodatkową  


### <a name="sql-server-2014-sp2-standard-enterprise"></a>SQL Server 2014 z dodatkiem SP2: Standard, Enterprise  
Tej wersji programu SQL Server możesz używać bez ograniczeń minimalnej wersji aktualizacji zbiorczej dla następujących elementów:  

-   Witryny Administracja centralna  
-   Lokacja główna  
-   Lokację dodatkową



### <a name="sql-server-2014-sp1-standard-enterprise"></a>SQL Server 2014 SP1: Standard, Enterprise  
 Tej wersji programu SQL Server możesz używać bez ograniczeń minimalnej wersji aktualizacji zbiorczej dla następujących elementów:  

-   Witryny Administracja centralna  
-   Lokacja główna  
-   Lokację dodatkową


### <a name="sql-server-2012-sp3-standard-enterprise"></a>SQL Server 2012 z dodatkiem SP3: Standard, Enterprise  
 Tej wersji programu SQL Server możesz używać bez ograniczeń minimalnej wersji aktualizacji zbiorczej dla następujących elementów:  

-   Witryny Administracja centralna  
-   Lokacja główna  
-   Lokację dodatkową  

<!-- Support for this service pack version has been dropped by Microsoft    
### SQL Server 2012 SP2: Standard, Enterprise   
 You can use this version of SQL Server with no minimum cumulative update version for the following:  

-   A central administration site  
-   A primary site  
-   A secondary site  
-->

### <a name="sql-server-2008-r2-sp3-standard-enterprise-datacenter"></a>SQL Server 2008 R2 z dodatkiem SP3: Standard, Enterprise i Datacenter     
  Ta wersja programu SQL Server nie jest obsługiwana [począwszy od wersji 1702](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-support-for-sql-server-versions-as-a-site-database).  
 Ta wersja programu SQL Server będzie obsługiwane przy użyciu wersji programu Configuration Manager przed 1702.

Jeśli są obsługiwane przez używaną wersję programu Configuration Manager, program tej wersji programu SQL Server z wersją bez minimalnej wersji aktualizacji zbiorczej dla następujących elementów:  

-   Witryny Administracja centralna  
-   Lokacja główna
-   Lokację dodatkową



### <a name="sql-server-2016-express-sp1"></a>SQL Server 2016 Express z dodatkiem SP1  
Tej wersji programu SQL Server możesz używać bez ograniczeń minimalnej wersji aktualizacji zbiorczej dla następujących elementów:
-   Lokację dodatkową

### <a name="sql-server-2016-express"></a>Program SQL Server 2016 Express
Tej wersji programu SQL Server możesz używać bez ograniczeń minimalnej wersji aktualizacji zbiorczej dla następujących elementów:
-   Lokację dodatkową


### <a name="sql-server-2014-express-sp2"></a>SQL Server 2014 Express z dodatkiem SP2   
Tej wersji programu SQL Server możesz używać bez ograniczeń minimalnej wersji aktualizacji zbiorczej dla następujących elementów:  

-   Lokację dodatkową  


### <a name="sql-server-2014-express-sp1"></a>SQL Server 2014 Express SP1   
 Tej wersji programu SQL Server możesz używać bez ograniczeń minimalnej wersji aktualizacji zbiorczej dla następujących elementów:  

-   Lokację dodatkową  

### <a name="sql-server-2012-express-sp3"></a>SQL Server 2012 Express SP3  
Tej wersji programu SQL Server możesz używać bez ograniczeń minimalnej wersji aktualizacji zbiorczej dla następujących elementów:  

-   Lokację dodatkową  

<!-- Support for this service pack version has been dropped by Microsoft   
### SQL Server 2012 Express SP2   
 You can use this version of SQL Server with no minimum cumulative update version for the following:  

-   A secondary site  
-->


##  <a name="bkmk_SQLConfig"></a> Konfiguracje wymagane dla programu SQL Server  
 Następujące czynności są wymagane przez wszystkie instalacje programu SQL Server używanego do bazy danych lokacji (w tym programu SQL Server Express). Gdy program Configuration Manager instaluje programu SQL Server Express w ramach instalacji lokacji dodatkowej, te konfiguracje są tworzone automatycznie dla Ciebie.  

 **Wersja architektury programu SQL Server:**  
 Program Configuration Manager wymaga 64-bitowej wersji programu SQL Server do obsługi bazy danych lokacji.  

 **Sortowanie bazy danych:**  
 W każdej lokacji wystąpienie programu SQL Server dla lokacji i bazy danych lokacji muszą używać następujących sortowania: **SQL_Latin1_General_CP1_CI_AS**.  

 Program Configuration Manager obsługuje dwa wyjątki to sortowanie do spełnienia standardów, które są zdefiniowane w GB18030 do użytku w Chinach. Aby uzyskać więcej informacji, zobacz [Obsługa wymagań międzynarodowych w programie System Center Configuration Manager](../../../core/plan-design/hierarchy/international-support.md).  

 **Funkcje programu SQL Server:**  
 Każdy serwer lokacji wymaga tylko funkcji **Usługi aparatu bazy danych** .  

 Replikacja bazy danych programu Configuration Manager nie wymagają **replikacji programu SQL Server** funkcji. Jednak ta konfiguracja programu SQL Server jest wymagany, jeśli używasz [bazy danych repliki dla punktów zarządzania programu System Center Configuration Manager](../../../core/servers/deploy/configure/database-replicas-for-management-points.md).  

 **Uwierzytelnianie systemu Windows:**  
 Program Configuration Manager wymaga **uwierzytelniania systemu Windows** do sprawdzania poprawności połączenia z bazą danych.  

 **Wystąpienie programu SQL Server:**  
 Musisz użyć dedykowanego wystąpienia programu SQL Server dla każdej lokacji. Może to być **nazwane wystąpienie** lub **wystąpienie domyślne**.  

 **Pamięć programu SQL Server:**  
 Rezerwa pamięci dla programu SQL Server przy użyciu programu SQL Server Management Studio i ustawienie **minimalna ilość pamięci serwera** ustawienia w obszarze **opcje pamięci serwera**. Aby uzyskać więcej informacji dotyczących sposobu ustawiania stałej ilości pamięci, zobacz [How to: Ustawianie stałej ilości pamięci (SQL Server Management Studio)](http://go.microsoft.com/fwlink/p/?LinkId=233759).  

-   **Dla serwera bazy danych, który jest zainstalowany na tym samym komputerze co serwer lokacji:** Ograniczenie pamięci dla programu SQL Server do 50 do 80 procent dostępnej pamięci adresowanego.  

-   **Dla serwera bazy danych dedykowanego (zdalnie z serwera lokacji):** Ograniczenie pamięci dla programu SQL Server do 80 90 procent dostępnej pamięci adresowanego.  

-   **Dla rezerwę pamięci puli buforów każdego wystąpienia programu SQL Server w użyciu:**  

    -   W witrynie Administracja centralna: Ustaw co najmniej 8 gigabajtów (GB).  
    -   Dla lokacji głównej: Ustaw co najmniej 8 gigabajtów (GB).  
    -   Dla lokacji dodatkowej: Ustaw co najmniej 4 gigabajty (GB).  

**Zagnieżdżone wyzwalacze SQL:**  
 [Zagnieżdżone wyzwalacze SQL](http://go.microsoft.com/fwlink/?LinkId=528802) muszą być włączone.  

 **Integracja środowiska CLR programu SQL Server**  
  Baza danych lokacji wymaga włączenia środowiska uruchomieniowego języka wspólnego (CLR, common language runtime) programu SQL Server. Ta funkcja jest włączana automatycznie podczas instalowania programu Configuration Manager. Aby uzyskać więcej informacji na temat środowiska CLR, zobacz [wprowadzenie do integracji CLR programu SQL Server](https://msdn.microsoft.com/library/ms254498\(v=vs.110\).aspx).  

##  <a name="bkmk_optional"></a> Konfiguracje opcjonalne dla programu SQL Server  
 Następujące konfiguracje są opcjonalne dla poszczególnych baz danych korzystających z pełnej instalacji programu SQL Server.  

 **Usługa SQL Server:**  
 Można skonfigurować usługę SQL Server, aby była uruchamiana przy użyciu:  

-   **Lokalnego użytkownika domeny** konta:  

    -   Najlepszym rozwiązaniem jest i konieczne będzie ręczne zarejestrowanie głównej nazwy usługi (SPN) dla konta.  

-   **Systemu lokalnego** konta komputera z uruchomionym programem SQL Server:  

    -   Użyj konta systemu lokalnego, aby uprościć proces konfigurowania.  
    -   Jeśli używasz konta systemu lokalnego, programu Configuration Manager automatycznie rejestruje SPN dla usługi programu SQL Server.  
    -   Pamiętaj, że korzystanie z lokalnego konta systemowego na potrzeby usługi SQL Server nie jest najlepszym rozwiązaniem dla programu SQL Server.  

Gdy na komputerze z uruchomionym programem SQL Server nie używa jej konto systemu lokalnego do uruchamiania usługi SQL Server, należy skonfigurować nazwę SPN konta, na którym jest uruchomiona usługa SQL Server w usługach domenowych w usłudze Active Directory. (W przypadku przy użyciu konta systemu nazwy SPN jest automatycznie rejestrowany automatycznie.)

Informacje o nazwy SPN dla bazy danych lokacji, można znaleźć w temacie [zarządzać nazwami SPN dla serwera bazy danych lokacji](../../../core/servers/manage/modify-your-infrastructure.md#bkmk_SPN) w [zmodyfikować infrastruktury programu System Center Configuration Manager](../../../core/servers/manage/modify-your-infrastructure.md) tematu.  

Aby uzyskać informacje dotyczące zmiany konta używanego przez usługi SQL Server, zobacz [How to: Zmień konto uruchamiania usługi programu SQL Server (SQL Server Configuration Manager)](http://go.microsoft.com/fwlink/p/?LinkId=237661).  

**Usługi Usługi SQL Server Reporting Services:**  
SQL Server Reporting Services jest wymagany do zainstalowania punktu usług raportowania, która umożliwia uruchamianie raportów.  

> [!IMPORTANT]  
> Po zakończeniu uaktualnienia z poprzedniej wersji programu SQL Server może zostać wyświetlony następujący błąd:  *Raport nie ma konstruktora*.    
> Aby rozwiązać ten problem, należy ponownie zainstalować rolę systemu lokacji punktu usług raportowania.

**Porty programu SQL Server:**  
Do komunikacji z aparatem bazy danych programu SQL Server oraz replikacji międzylokacyjnej można użyć w domyślnej konfiguracji portu programu SQL Server lub określić porty niestandardowe:  

-   **Komunikacja międzylokacyjna** używać programu SQL Server Service Broker, która używa portu TCP 4022 domyślnie.  
-   **Komunikacja międzylokacyjna** między aparatem bazy danych programu SQL Server i systemu lokacji programu Configuration Manager różnych ról domyślnie używają portu TCP 1433. Następujące role systemu lokacji komunikują się bezpośrednio z bazą danych program SQL Server:  

    -   Punkt zarządzania  
    -   Komputer dostawcy programu SMS  
    -   Punkt usług raportowania  
    -   Serwer lokacji  

Gdy na komputerze z programem SQL Server obsługuje bazę danych z więcej niż jednej lokacji, każda baza danych musi używać osobnego wystąpienia programu SQL Server. Również każde wystąpienie musi być skonfigurowane do używania unikatowego zestawu portów.  

> [!WARNING]  
>  Menedżer konfiguracji nie obsługuje portów dynamicznych. Nazwane wystąpienia (gdy są używane) programu SQL Server domyślnie używają portów dynamicznych do połączeń z aparatem bazy danych, dlatego należy ręcznie skonfigurować port statyczny, który będzie używany do komunikacji wewnątrzlokacyjnej.  

Jeśli na komputerze z programem SQL Server jest włączona zapora, upewnij się, że jest skonfigurowana, aby zezwalać na ruch na portach używanych przez wdrożenie oraz we wszystkich lokalizacjach sieciowych między komputerami komunikującymi się z programem SQL Server.  

Na przykład sposobu konfigurowania programu SQL Server do używania konkretnego portu zobacz [How to: Konfigurowanie serwera do nasłuchiwania na porcie TCP (SQL Server Configuration Manager) określonego](http://go.microsoft.com/fwlink/p/?LinkID=226349) w bibliotece TechNet serwera SQL.  

## <a name="upgrade-options-for-sql-server"></a>Opcje uaktualniania dla programu SQL Server
Jeśli musisz uaktualnić używanej wersji programu SQL Server, zaleca się następujących metod z łatwe do bardziej złożonych.
1. [Uaktualnij program SQL Server w miejscu](/sccm/core/servers/manage/upgrade-on-premises-infrastructure#a-namebkmksupconfigupgradedbsrva-upgrade-sql-server-on-the-site-database-server) (zalecane).
2. Zainstalować nową wersję programu SQL Server na nowym komputerze, a następnie [opcja move datbase](/sccm/core/servers/manage/modify-your-infrastructure#a-namebkmkdbconfiga-modify-the-site-database-configuration) instalacji programu Configuration Manager, aby wskazywały nowy serwer SQL serwera lokacji.
3. Użyj [kopii zapasowych i odzyskiwania](/sccm/protect/understand/backup-and-recovery).

