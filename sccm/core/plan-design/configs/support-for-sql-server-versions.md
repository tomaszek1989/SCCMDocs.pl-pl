---
title: "Obsługiwane wersje programu SQL Server"
titleSuffix: Configuration Manager
description: Pobierz wymagania konfiguracji i wersji programu SQL Server do hostowania bazy danych lokacji programu System Center Configuration Manager.
ms.custom: na
ms.date: 12/18/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 35e237b6-9f7b-4189-90e7-8eca92ae7d3d
caps.latest.revision: 
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 82df06873449d538b7efbe414a451d746d48e11f
ms.sourcegitcommit: b13da5ad8ffd58e3b89fa6d7170e1dec3ff130a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2018
---
# <a name="supported-sql-server-versions-for-system-center-configuration-manager"></a>Obsługiwane wersje programu SQL Server dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Każda lokacja programu System Center Configuration Manager wymaga obsługiwana wersja programu SQL Server i konfigurację do obsługi bazy danych lokacji.  

##  <a name="bkmk_Instances"></a> Wystąpienia i lokalizacje programu SQL Server  
 **Centralna lokacja administracyjna i lokacje główne:**  
Bazy danych lokacji musi używać pełnej instalacji programu SQL Server.  

 SQL Server może znajdować się na:  

-   Komputer serwera lokacji.  
-   Komputer zdalnie z serwera lokacji.  

Obsługiwane są następujące wystąpienia:  

-   Domyślne lub nazwane wystąpienie programu SQL Server.  
-   Konfiguracje z wieloma wystąpieniami.  
-   Klaster programu SQL Server. Zobacz [używać klastra programu SQL Server do hostowania bazy danych lokacji](../../../core/servers/deploy/configure/use-a-sql-server-cluster-for-the-site-database.md).
-   Grupa dostępności AlwaysOn programu SQL Server. Ta opcja wymaga programu Configuration Manager w wersji 1602 lub nowszej. Aby uzyskać więcej informacji, zobacz [AlwaysOn programu SQL Server dla bazy danych lokacji o wysokiej dostępności programu System Center Configuration Manager](../../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md).


 **Lokacje dodatkowe:**  
 Bazy danych lokacji można użyć domyślnego wystąpienia pełnej instalacji programu SQL Server lub SQL Server Express.  

 Program SQL Server musi znajdować się na komputerze serwera lokacji.  

 **Ograniczenia dotyczące obsługi**   
 Nie są obsługiwane następujące konfiguracje:
 -   Klastra programu SQL Server w konfiguracji klastra równoważenia obciążenia sieciowego (NLB)
 -   Klastra programu SQL Server na udostępnionego woluminu klastra (CSV)
 -   Dublowanie technologii i peer-to-peer replikacji bazy danych SQL Server

Replikacja transakcyjna programu SQL Server jest obsługiwana tylko na potrzeby replikacji obiektów do punktów zarządzania, które są skonfigurowane do używania [replik bazy danych](https://technet.microsoft.com/library/mt608546.aspx).  

##  <a name="bkmk_SQLVersions"></a> Obsługiwane wersje programu SQL Server  
 W hierarchii z wieloma lokacjami różnych lokacji możesz użyć innej wersji programu SQL Server do hostowania bazy danych lokacji, tak długo, jak zostały spełnione następujące warunki:
 -  Program Configuration Manager obsługuje wersje programu SQL Server, którego używasz.
 -  Wersje programu SQL Server, którego używasz pozostają w pomocy technicznej firmy Microsoft.
 -  SQL Server obsługuje replikację między dwoma wersjami programu SQL Server.  Na przykład [programu SQL Server nie obsługuje replikacji między programu SQL Server 2008 R2 i SQL Server 2016](https://docs.microsoft.com/sql/relational-databases/replication/deprecated-features-in-sql-server-replication).



 O ile nie określono inaczej, następujące wersje programu SQL Server są obsługiwane przez wszystkie aktywne wersje programu System Center Configuration Manager. Jeśli obsługa nowej wersji programu SQL Server lub z dodatkiem Service pack jest dodawany, wersji programu Configuration Manager, który dodaje obsługę zostanie zapisany. Podobnie jeśli obsługa jest przestarzała, znaleźć szczegółowe informacje o usterce wersje programu Configuration Manager.   

Obsługa określonego dodatku service pack programu SQL Server obejmuje aktualizacje zbiorcze, chyba że awarie zgodność ze starszymi wersjami usługi podstawowej wersji pakietu. Nie wersji dodatku service pack należy zauważyć, obsługa dotyczy wersji programu SQL Server bez dodatku service pack. W przyszłości Jeśli wydaniu dodatku service pack do wersji SQL Server instrukcji obsługi oddzielnych będą deklarowane przed nowej wersji dodatku service pack jest obsługiwany.


> [!IMPORTANT]  
>  Korzystając z programu SQL Server Standard dla bazy danych w centralnej lokacji administracyjnej, należy ograniczyć całkowitą liczbę klientów obsługiwanych w hierarchii. Zobacz [Wartości dotyczące rozmiarów i skalowania](../../../core/plan-design/configs/size-and-scale-numbers.md).

### <a name="sql-server-2017-standard-enterprise"></a>SQL Server 2017: Wersje Standard, Enterprise  
Ta wersja programu SQL Server, można użyć z co najmniej [wersji aktualizacji zbiorczej 2](https://support.microsoft.com/help/4052574), począwszy od [1710 wersji programu Configuration Manager](https://docs.microsoft.com/en-us/sccm/core/plan-design/changes/whats-new-in-version-1710) dla następujących witryn: 

-   Centralna lokacja administracyjna  
-   Lokacja główna  
-   Lokację dodatkową  
<!--SMS.498506-->

### <a name="sql-server-2016-sp1-standard-enterprise"></a>SQL Server 2016 SP1: Wersje Standard, Enterprise  
Za pomocą tej wersji programu SQL Server i nie ma wersji minimalnej wersji aktualizacji zbiorczej dla następujących witryn:  

-   Centralna lokacja administracyjna  
-   Lokacja główna  
-   Lokację dodatkową  

### <a name="sql-server-2016-standard-enterprise"></a>SQL Server 2016: Wersje Standard, Enterprise  
Za pomocą tej wersji programu SQL Server i nie ma wersji minimalnej wersji aktualizacji zbiorczej dla następujących witryn:  

-   Centralna lokacja administracyjna  
-   Lokacja główna  
-   Lokację dodatkową  


### <a name="sql-server-2014-sp2-standard-enterprise"></a>SQL Server 2014 SP2: Wersje Standard, Enterprise  
Za pomocą tej wersji programu SQL Server i nie ma wersji minimalnej wersji aktualizacji zbiorczej dla następujących witryn:  

-   Centralna lokacja administracyjna  
-   Lokacja główna  
-   Lokację dodatkową

### <a name="sql-server-2014-sp1-standard-enterprise"></a>SQL Server 2014 SP1: Wersje Standard, Enterprise  
 Za pomocą tej wersji programu SQL Server i nie ma wersji minimalnej wersji aktualizacji zbiorczej dla następujących witryn:  

-   Centralna lokacja administracyjna  
-   Lokacja główna  
-   Lokację dodatkową

### <a name="sql-server-2012-sp4-standard-enterprise"></a>SQL Server 2012 SP4: Wersje Standard, Enterprise  
 Za pomocą tej wersji programu SQL Server i nie ma wersji minimalnej wersji aktualizacji zbiorczej dla następujących witryn:  

-   Centralna lokacja administracyjna  
-   Lokacja główna  
-   Lokację dodatkową  

### <a name="sql-server-2012-sp3-standard-enterprise"></a>SQL Server 2012 SP3: Wersje Standard, Enterprise  
 Za pomocą tej wersji programu SQL Server i nie ma wersji minimalnej wersji aktualizacji zbiorczej dla następujących witryn:  

-   Centralna lokacja administracyjna  
-   Lokacja główna  
-   Lokację dodatkową  

<!-- Support for this service pack version has been dropped by Microsoft    
### SQL Server 2012 SP2: Standard, Enterprise   
 You can use this version of SQL Server with no minimum cumulative update version for the following sites:  

-   A central administration site  
-   A primary site  
-   A secondary site  
-->

### <a name="sql-server-2008-r2-sp3-standard-enterprise-datacenter"></a>SQL Server 2008 R2 SP3: Standard, Enterprise, Datacenter     
  Ta wersja programu SQL Server nie jest obsługiwana [począwszy od wersji 1702](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-server#deprecated-support-for-sql-server-versions-as-a-site-database).  
 Ta wersja programu SQL Server jest obsługiwany w przypadku korzystania z wersji programu Configuration Manager przed 1702.

Jeśli są obsługiwane przez wersję programu Configuration Manager, można tej wersji programu SQL Server bez wersji minimalnej wersji aktualizacji zbiorczej dla następujących witryn:  

-   Centralna lokacja administracyjna  
-   Lokacja główna
-   Lokację dodatkową

### <a name="sql-server-2017-express"></a>SQL Server 2017 Express   
Ta wersja programu SQL Server, można użyć z co najmniej [wersji aktualizacji zbiorczej 2](https://support.microsoft.com/help/4052574), począwszy od [1710 wersji programu Configuration Manager](https://docs.microsoft.com/en-us/sccm/core/plan-design/changes/whats-new-in-version-1710) dla następujących witryn:
-   Lokację dodatkową
<!--SMS.498506-->

### <a name="sql-server-2016-express-sp1"></a>SQL Server 2016 Express SP1  
Za pomocą tej wersji programu SQL Server i nie ma wersji minimalnej wersji aktualizacji zbiorczej dla następujących witryn:
-   Lokację dodatkową

### <a name="sql-server-2016-express"></a>SQL Server 2016 Express
Za pomocą tej wersji programu SQL Server i nie ma wersji minimalnej wersji aktualizacji zbiorczej dla następujących witryn:
-   Lokację dodatkową


### <a name="sql-server-2014-express-sp2"></a>SQL Server 2014 Express SP2   
Za pomocą tej wersji programu SQL Server i nie ma wersji minimalnej wersji aktualizacji zbiorczej dla następujących witryn:  

-   Lokację dodatkową  


### <a name="sql-server-2014-express-sp1"></a>SQL Server 2014 Express SP1   
 Za pomocą tej wersji programu SQL Server i nie ma wersji minimalnej wersji aktualizacji zbiorczej dla następujących witryn:  

-   Lokację dodatkową  

### <a name="sql-server-2012-express-sp3"></a>SQL Server 2012 Express SP3  
Za pomocą tej wersji programu SQL Server i nie ma wersji minimalnej wersji aktualizacji zbiorczej dla następujących witryn:  

-   Lokację dodatkową  

<!-- Support for this service pack version has been dropped by Microsoft   
### SQL Server 2012 Express SP2   
 You can use this version of SQL Server with no minimum cumulative update version for the following sites:  

-   A secondary site  
-->


##  <a name="bkmk_SQLConfig"></a> Konfiguracje wymagane dla programu SQL Server  
 Poniższe elementy są wymagane przez wszystkie instalacje programu SQL Server, której użyjesz dla bazy danych lokacji (w tym programu SQL Server Express). Program Configuration Manager instaluje program SQL Server Express w ramach instalacji lokacji dodatkowej, te konfiguracje są tworzone automatycznie dla Ciebie.  

 **Wersja architektury programu SQL Server:**  
 Configuration Manager wymaga 64-bitowej wersji programu SQL Server do obsługi bazy danych lokacji.  

 **Sortowanie bazy danych:**  
 W każdej lokacji zarówno wystąpienie programu SQL Server, który jest używany dla lokacji i bazy danych lokacji musi używać następującego sortowania: **SQL_Latin1_General_CP1_CI_AS**.  

 Program Configuration Manager obsługuje dwa wyjątki związane z tym sortowaniem, aby spełniać normy, które są zdefiniowane w GB18030 w Chinach. Aby uzyskać więcej informacji, zobacz [Obsługa wymagań międzynarodowych w programie System Center Configuration Manager](../../../core/plan-design/hierarchy/international-support.md).  

 **Poziom zgodności bazy danych:** </br>
 Program Configuration Manager wymaga, aby poziom zgodności bazy danych lokacji być nie mniejszy niż najniższa obsługiwana wersja programu SQL Server dla używanej wersji programu Configuration Manager. Na przykład, począwszy od wersji 1702, musisz mieć [bazy danych ma poziom zgodności](https://docs.microsoft.com/sql/relational-databases/databases/view-or-change-the-compatibility-level-of-a-database) wynosił co najmniej 110. <!-- SMS.506266--> 

 **Funkcje programu SQL Server:**  
 Każdy serwer lokacji wymaga tylko funkcji **Usługi aparatu bazy danych** .  

 Replikacja bazy danych programu Configuration Manager nie wymaga **replikacji programu SQL Server** funkcji. Jednak taka konfiguracja programu SQL Server jest wymagana, jeśli używasz [replik bazy danych dla punktów zarządzania programu System Center Configuration Manager](../../../core/servers/deploy/configure/database-replicas-for-management-points.md).  

 **Uwierzytelnianie systemu Windows:**  
 Program Configuration Manager wymaga **uwierzytelniania systemu Windows** do weryfikowania połączeń z bazą danych.  

 **Wystąpienie programu SQL Server:**  
 Musisz użyć dedykowanego wystąpienia programu SQL Server dla każdej lokacji. Wystąpienie może być **nazwane wystąpienie** lub **domyślnego wystąpienia**.  

 **Pamięć programu SQL Server:**  
 Zarezerwuj pamięć dla programu SQL Server przy użyciu programu SQL Server Management Studio i ustawienie **minimalna ilość pamięci serwera** w obszarze **opcje pamięci serwera**. Aby uzyskać więcej informacji na temat sposobu ustawiania stałej ilości pamięci, zobacz [jak: Ustawianie stałej ilości pamięci (SQL Server Management Studio)](http://go.microsoft.com/fwlink/p/?LinkId=233759).  

-   **Dla serwera bazy danych, który jest zainstalowany na tym samym komputerze co serwer lokacji:** Ogranicz pamięć programu SQL Server z 50 do 80 procent dostępnej adresowalnej pamięci systemu.  

-   **Serwer dedykowany bazy danych (poza komputerem serwera lokacji):** Ogranicz pamięć programu SQL Server z 80 do 90 procent dostępnej adresowalnej pamięci systemu.  

-   **Dla rezerwa pamięci dla puli buforów dla każdego wystąpienia programu SQL Server w użyciu:**  

    -   Dla centralnej lokacji administracyjnej: Ustaw co najmniej 8 gigabajtów (GB).  
    -   Dla lokacji głównej: Ustaw co najmniej 8 gigabajtów (GB).  
    -   Dla lokacji dodatkowej: Ustaw co najmniej 4 gigabajty (GB).  

**Zagnieżdżone wyzwalacze SQL:**  
 [Zagnieżdżone wyzwalacze SQL](http://go.microsoft.com/fwlink/?LinkId=528802) muszą być włączone.  

 **Integracja środowiska CLR programu SQL Server**  
  Baza danych lokacji wymaga włączenia środowiska uruchomieniowego języka wspólnego (CLR, common language runtime) programu SQL Server. Ta opcja jest włączona automatycznie po zainstalowaniu programu Configuration Manager. Aby uzyskać więcej informacji na temat środowiska CLR, zobacz [wprowadzenie do integracji środowiska CLR programu SQL Server](https://msdn.microsoft.com/library/ms254498\(v=vs.110\).aspx).  

##  <a name="bkmk_optional"></a> Konfiguracje opcjonalne dla programu SQL Server  
 Następujące konfiguracje są opcjonalne dla poszczególnych baz danych korzystających z pełnej instalacji programu SQL Server.  

 **Usługa SQL Server:**  
 Można skonfigurować usługę SQL Server, aby była uruchamiana przy użyciu:  

-   A *niskich prawach użytkownika domeny* konta:  

    -   Najlepszym rozwiązaniem jest i może wymagać ręcznej rejestracji główna nazwa usługi (SPN) dla konta.  

-   **Systemu lokalnego** konta komputera, na którym działa program SQL Server:  

    -   Użyj konta systemu lokalnego, aby uprościć proces konfigurowania.  
    -   Korzystając z konta system lokalny, programu Configuration Manager automatycznie rejestruje główną nazwę usługi programu SQL Server.  
    -   Pamiętaj, że korzystanie z lokalnego konta systemowego na potrzeby usługi SQL Server nie jest najlepszym rozwiązaniem dla programu SQL Server.  

W przypadku komputera z programem SQL Server nie używa swojego konta systemu lokalnego do uruchamiania usługi programu SQL Server, należy skonfigurować nazwę SPN konta, na którym jest uruchomiona usługa SQL Server w usługach domenowych w usłudze Active Directory. (W przypadku konta systemowego nazwy SPN jest rejestrowana automatycznie.)

Informacje o nazwach SPN dla bazy danych lokacji, zobacz [zarządzać nazwami SPN dla serwera bazy danych lokacji](../../../core/servers/manage/modify-your-infrastructure.md#bkmk_SPN) w [modyfikowanie infrastruktury programu System Center Configuration Manager](../../../core/servers/manage/modify-your-infrastructure.md) artykułu.  

Aby uzyskać informacje na temat zmieniania konta używanego przez usługi SQL Server, zobacz [jak: Zmienianie konta uruchamiania usługi programu SQL Server (SQL Server Configuration Manager)](http://go.microsoft.com/fwlink/p/?LinkId=237661).  

**Usługi Usługi SQL Server Reporting Services:**  
SQL Server Reporting Services jest wymagany do zainstalowania punktu usług raportowania, który umożliwia uruchamianie raportów.  

> [!IMPORTANT]  
> Po uaktualnieniu z poprzedniej wersji programu SQL Server, może zostać wyświetlony następujący błąd:  *Raport nie istnieje konstruktor*.    
> Aby rozwiązać ten problem, należy ponownie zainstalować rolę systemu lokacji punktu usług raportowania.

**Porty programu SQL Server:**  
Do komunikacji z aparatem bazy danych programu SQL Server oraz replikacji między lokacjami można użyć w domyślnej konfiguracji portów programu SQL Server lub określić porty niestandardowe:  

-   **Komunikacji między lokacjami** Użyj programu SQL Server Service Broker, która używa portu TCP 4022 domyślnie.  
-   **Komunikacja wewnątrzlokacyjna** między aparatem bazy danych programu SQL Server i systemu lokacji programu Configuration Manager różne role używają domyślnie z portu TCP 1433. Następujące role systemu lokacji komunikują się bezpośrednio z bazą danych program SQL Server:  

    -   Punkt zarządzania  
    -   Komputer dostawcy programu SMS  
    -   Punkt usług raportowania  
    -   Serwer lokacji  

Gdy komputer z uruchomionym programem SQL Server hostuje bazę danych z więcej niż jednej lokacji, każda baza danych musi używać osobnego wystąpienia programu SQL Server. Ponadto każde wystąpienie musi być skonfigurowana do używania unikatowego zestawu portów.  

> [!WARNING]  
>  Program Configuration Manager nie obsługuje portów dynamicznych. Nazwane wystąpienia (gdy są używane) programu SQL Server domyślnie używają portów dynamicznych do połączeń z aparatem bazy danych, dlatego należy ręcznie skonfigurować port statyczny, który będzie używany do komunikacji wewnątrzlokacyjnej.  

Jeśli na komputerze z programem SQL Server jest włączona zapora, upewnij się, że jest skonfigurowana, aby zezwalać na ruch na portach używanych przez wdrożenie oraz we wszystkich lokalizacjach sieciowych między komputerami komunikującymi się z programem SQL Server.  

Na przykład sposobu konfigurowania programu SQL Server do używania konkretnego portu zobacz [jak: Konfigurowanie serwera do nasłuchiwania na konkretnym porcie TCP (SQL Server Configuration Manager)](http://go.microsoft.com/fwlink/p/?LinkID=226349) w bibliotece TechNet programu SQL Server.  

## <a name="upgrade-options-for-sql-server"></a>Opcje uaktualniania dla programu SQL Server
Należy uaktualnić używanej wersji programu SQL Server, zalecamy następujących metod z ułatwia bardziej złożonych.
1. [Uaktualnienie programu SQL Server w miejscu](/sccm/core/servers/manage/upgrade-on-premises-infrastructure#a-namebkmksupconfigupgradedbsrva-upgrade-sql-server-on-the-site-database-server) (zalecane).
2. Instalowanie nowej wersji programu SQL Server na nowym komputerze, a następnie [opcja przenoszenia bazy danych](/sccm/core/servers/manage/modify-your-infrastructure#a-namebkmkdbconfiga-modify-the-site-database-configuration) Instalatora programu Configuration Manager, aby wskazywały nowy serwer SQL serwera lokacji.
3. Użyj [kopii zapasowych i odzyskiwania](/sccm/protect/understand/backup-and-recovery).
