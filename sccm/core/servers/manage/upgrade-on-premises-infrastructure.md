---
title: Uaktualnianie infrastruktury lokalnej | Dokumentacja firmy Microsoft
description: "Informacje o sposobie uaktualniania infrastruktury, takich jak SQL Server i systemu operacyjnego lokacji systemów lokacji."
ms.custom: na
ms.date: 06/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8ca970dd-e71c-404f-9435-d36e773a0db2
caps.latest.revision: 7
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0564cb678200d17d97c0f1d111c0b4b41d8ba40e
ms.openlocfilehash: 188b7f2537dd0e569a5c00995620124512cf311b
ms.contentlocale: pl-pl
ms.lasthandoff: 06/30/2017


---
# <a name="upgrade-on-premises-infrastructure-that-supports-system-center-configuration-manager"></a>Uaktualnianie infrastruktury lokalnej, która obsługuje program System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Skorzystaj z informacji w tym temacie, aby ułatwić uaktualnienie infrastruktury serwera, na którym działa System Center Configuration Manager.  

 - Jeśli chcesz uaktualnić ze starszej wersji programu Configuration Manager do programu System Center Configuration Manager, zobacz [uaktualnienia do programu System Center Configuration Manager](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager).

- Jeśli chcesz zaktualizować infrastruktury programu System Center Configuration Manager do nowej wersji, zobacz [aktualizacji dla programu System Center Configuration Manager](/sccm/core/servers/manage/updates).

##  <a name="BKMK_SupConfigUpgradeSiteSrv"></a>Uaktualnij system operacyjny systemów lokacji  
 Program Configuration Manager obsługuje uaktualnienie w miejscu systemu operacyjnego serwery obsługujące serwer lokacji i serwery zdalne, które host żadnych ról systemu lokacji w następujących sytuacjach:  

-   Uaktualnienie w miejscu do nowszej dodatku service pack systemu Windows Server, gdy Wynikowy poziom dodatku service pack systemu Windows jest obsługiwany przez program Configuration Manager.  
-   Uaktualnienie w miejscu z:
    - Windows Server 2012 R2 do systemu Windows Server 2016 ([dodatkowe szczegóły](#bkmk_2016)).
    - Windows Server 2012 do systemu Windows Server 2016 ([dodatkowe szczegóły](#bkmk_2016)).
    - Windows Server 2012 do systemu Windows Server 2012 R2 ([dodatkowe szczegóły](#bkmk_2012r2)).
    - Jeśli używasz programu Configuration Manager w wersji 1602 lub później, jest też obsługiwana do uaktualnienia systemu Windows Server 2008 R2 do systemu Windows Server 2012 R2 ([dodatkowe szczegóły](#bkmk_from2008r2).

    > [!WARNING]  
    >  Przed uaktualnieniem do systemu Windows Server 2012 R2 *należy odinstalować usługi WSUS 3.2* z serwera.  
    >   
    >  Aby uzyskać informacje o tym krytycznym kroku, zobacz sekcję "Nowe i zmienione funkcje" w [Omówienie usług Windows Server Update Services](https://technet.microsoft.com/library/hh852345.aspx) w dokumentacji systemu Windows Server.  

Aby uaktualnić serwer, wykorzystywane procedury uaktualniania udostępnione przez system operacyjny, który jest uaktualniany do.  Zobacz następujące tematy:
  -  [Uaktualnij opcje dla systemu Windows Server 2012 R2](https://technet.microsoft.com/library/dn303416.aspx) w dokumentacji systemu Windows Server.  
  - [Opcje uaktualniania i konwersji dla systemu Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/supported-upgrade-paths) w dokumentacji systemu Windows Server.

### <a name="bkmk_2016"></a>Uaktualnienie systemu Windows Server 2012 lub Windows Server 2012 R2 i 2016
Podczas uaktualniania systemu Windows Server 2012 lub Windows Server 2012 R2 do systemu Windows Server 2016 następujących warunków:


**Przed uaktualnieniem:**  
-   Usuń klienta programu System Center Endpoint Protection (SCEP). Windows Server 2016 ma usługa Windows Defender wbudowane, która zastępuje SCEP klienta. Obecności klienta protokołu SCEP może uniemożliwić uaktualnienia do systemu Windows Server 2016.

**Po uaktualnieniu:**
-   Upewnij się, że usługa Windows Defender jest włączona, Ustaw automatyczne uruchamianie i uruchomiona.
-   Upewnij się, że są uruchomione następujące usługi programu Configuration Manager:
  -     SMS_EXECUTIVE
  -     SMS_SITE_COMPONENT_MANAGER


-   Upewnij się, **aktywacji procesów systemu Windows** i **WWW/W3svc** usługi są włączone, ustaw dla automatycznego uruchamiania i uruchomione dla następujących ról systemu lokacji (te usługi są wyłączone podczas uaktualniania):
  -     Serwer lokacji
  -     Punkt zarządzania
  -     Punkt usługi sieci Web Wykaz aplikacji
  -     Punkt witryny sieci Web wykazu aplikacji

-   Upewnij się, każdy serwer, który jest hostem roli systemu lokacji nadal spełniają wszystkie [wymagania wstępne dotyczące ról systemu lokacji](/sccm/core/plan-design/configs/site-and-site-system-prerequisites) uruchomionymi na tym serwerze. Na przykład może być konieczne ponowne zainstalowanie usługi BITS, usług WSUS, lub skonfigurować ustawienia specyficzne dla usług IIS.

-   Po przywróceniu wszystkie brakujące wymagania wstępne, uruchom ponownie serwer jeszcze raz, aby upewnić się, że usługi jest uruchomiony i działa.

**Znany problem dla zdalnej konsoli programu Configuration Manager:**  
Po uaktualnieniu serwera lokacji lub serwera hostującego wystąpienie SMS_Provider do systemu Windows Server 2016, użytkownicy z uprawnieniami administracyjnymi może nie móc połączyć konsolę programu Configuration Manager do lokacji. Aby obejść ten problem, należy ręcznie przywrócić uprawnienia dla grupy administratorów programu SMS w usłudze WMI. Uprawnienia należy ustawić na serwerze lokacji i na każdym serwerze zdalnym, który hostuje wystąpienie element SMS_Provider:

1. Na odpowiednich serwerach, Otwórz program Microsoft Management Console (MMC) i Dodaj przystawkę dla **Sterowanie usługą WMI**, a następnie wybierz **komputera lokalnego**.
2. W przystawce MMC, otwórz **właściwości** z **Sterowanie usługą WMI (lokalnie)** i wybierz **zabezpieczeń** kartę.
3. Rozwiń drzewo poniżej katalogu głównego, wybierz **SMS** węzeł, a następnie wybierz pozycję **zabezpieczeń**.  Upewnij się, **Administratorzy programu SMS** grupa ma następujące uprawnienia:
  -     Włącz konto
  -     Włączanie zdalne
4. Na **karta Zabezpieczenia** poniżej **SMS** węzła, wybierz opcję **site_&lt;kod_lokacji**> węzła, a następnie wybierz pozycję **zabezpieczeń**. Upewnij się, **Administratorzy programu SMS** grupa ma następujące uprawnienia:
  -   Wykonywanie metod
  -   Zapis dostawcy
  -   Włącz konto
  -   Włączanie zdalne
5. Zapisz te uprawnienia, aby przywrócić dostęp do konsoli programu Configuration Manager.

### <a name="bkmk_2012r2"></a>Windows Server 2012 do systemu Windows Server 2012 R2

**Przed uaktualnieniem:**
-  W przeciwieństwie do innych obsługiwanych scenariuszach ten scenariusz nie wymaga uwagi dodatkowe przed uaktualnieniem.

**Po uaktualnieniu:**
  - Sprawdź, czy usługi wdrażania systemu Windows jest uruchomiony i działa dla następujących ról systemu lokacji (ta usługa zostanie zatrzymana podczas uaktualniania):
    - Serwer lokacji
    - Punkt zarządzania
    - Punkt usługi sieci Web Wykaz aplikacji
    - Punkt witryny sieci Web wykazu aplikacji

  -     Upewnij się, **aktywacji procesów systemu Windows** i **WWW/W3svc** usługi są włączone, ustaw dla automatycznego uruchamiania i uruchomione dla następujących ról systemu lokacji (te usługi są wyłączone podczas uaktualniania):
    -   Serwer lokacji
    -   Punkt zarządzania
    -   Punkt usługi sieci Web Wykaz aplikacji
    -   Punkt witryny sieci Web wykazu aplikacji


  -     Upewnij się, każdy serwer, który jest hostem roli systemu lokacji nadal spełniają wszystkie [wymagania wstępne dotyczące ról systemu lokacji](/sccm/core/plan-design/configs/site-and-site-system-prerequisites) uruchomionymi na tym serwerze. Na przykład może być konieczne ponowne zainstalowanie usługi BITS, usług WSUS, lub skonfigurować ustawienia specyficzne dla usług IIS.

  Po przywróceniu wszystkie brakujące wymagania wstępne, uruchom ponownie serwer jeszcze raz, aby upewnić się, że usługi jest uruchomiony i działa.

### <a name="bkmk_from2008r2"></a>Uaktualnienie systemu Windows Server 2008 R2 do systemu Windows Server 2012 R2
Ten scenariusz uaktualniania systemu operacyjnego ma następujące warunki:  

**Przed uaktualnieniem:**
-   Odinstaluj program WSUS 3.2.  
    Przed rozpoczęciem uaktualniania systemu operacyjnego serwera do systemu Windows Server 2012 R2, należy odinstalować usługi WSUS 3.2 z serwera. Aby uzyskać informacje o tym krytycznym kroku zobacz sekcję nowe i zmienione funkcje w artykule Omówienie usług Windows Server Update Services w dokumentacji systemu Windows Server.

**Po uaktualnieniu:**
  - Sprawdź, czy usługi wdrażania systemu Windows jest uruchomiony i działa dla następujących ról systemu lokacji (ta usługa zostanie zatrzymana podczas uaktualniania):
    - Serwer lokacji
    - Punkt zarządzania
    - Punkt usługi sieci Web Wykaz aplikacji
    - Punkt witryny sieci Web wykazu aplikacji


  -     Upewnij się, **aktywacji procesów systemu Windows** i **WWW/W3svc** usługi są włączone, ustaw dla automatycznego uruchamiania i uruchomione dla następujących ról systemu lokacji (te usługi są wyłączone podczas uaktualniania):
    -   Serwer lokacji
    -   Punkt zarządzania
    -   Punkt usługi sieci Web Wykaz aplikacji
    -   Punkt witryny sieci Web wykazu aplikacji


  -     Upewnij się, każdy serwer, który jest hostem roli systemu lokacji nadal spełniają wszystkie [wymagania wstępne dotyczące ról systemu lokacji](/sccm/core/plan-design/configs/site-and-site-system-prerequisites) uruchomionymi na tym serwerze. Na przykład może być konieczne ponowne zainstalowanie usługi BITS, usług WSUS, lub skonfigurować ustawienia specyficzne dla usług IIS.

  Po przywróceniu wszystkie brakujące wymagania wstępne, uruchom ponownie serwer jeszcze raz, aby upewnić się, że usługi jest uruchomiony i działa.


### <a name="unsupported-upgrade-scenarios"></a>Nieobsługiwane scenariusze uaktualniania
W następujących scenariuszach uaktualniania systemu Windows Server są najczęściej zadawane, ale nie obsługiwane przez program Configuration Manager:  

-   Windows Server 2008 do systemu Windows Server 2012 lub nowszym  
-   Windows Server 2008 R2 do systemu Windows Server 2012



##  <a name="BKMK_SupConfigUpgradeClient"></a>Uaktualnij system operacyjny klientów programu Configuration Manager  
 Program Configuration Manager obsługuje uaktualnienie w miejscu systemu operacyjnego klientów programu Configuration Manager w następujących sytuacjach:  

-   Uaktualnienie w miejscu do nowszej dodatku service pack systemu Windows, gdy Wynikowy poziom dodatku service pack jest obsługiwany przez program Configuration Manager.  

-   Uaktualnienie w miejscu systemu Windows z obsługiwanej wersji systemu Windows 10. Aby uzyskać więcej informacji, zobacz [Uaktualnianie systemu Windows do najnowszej wersji przy użyciu programu System Center Configuration Manager](../../../osd/deploy-use/upgrade-windows-to-the-latest-version.md).  

-   Uaktualnienia obsługi do kompilacji systemu Windows 10.  Aby uzyskać więcej informacji, zobacz [Zarządzanie systemem Windows jako usługą za pomocą programu System Center Configuration Manager](../../../osd/deploy-use/manage-windows-as-a-service.md).  

##  <a name="BKMK_SupConfigUpgradeDBSrv"></a>Uaktualnij program SQL Server na serwerze bazy danych lokacji  
  Program Configuration Manager obsługuje uaktualnienie w miejscu programu SQL Server z obsługiwanej wersji programu SQL Server na serwerze bazy danych lokacji. Scenariuszach uaktualniania programu SQL Server w tej sekcji są obsługiwane przez program Configuration Manager i zawierają wymagania dotyczące każdego scenariusza.

 Aby uzyskać informacje o wersjach programu SQL Server, które są obsługiwane przez program Configuration Manager, zobacz [pomocy technicznej dla wersji programu SQL Server dla programu System Center Configuration Manager](../../../core/plan-design/configs/support-for-sql-server-versions.md).  

 **Uaktualnianie wersji dodatku service pack programu SQL Server:**    
 Program Configuration Manager obsługuje uaktualnianie w miejscu programu SQL Server do późniejszy dodatek service pack, jeśli gdy Wynikowy poziom pakietu usług SQL Server jest obsługiwane przez program Configuration Manager.

 Jeśli masz wiele lokacji programu Configuration Manager w hierarchii każdej lokacji może działać wersję pakietu innej usługi programu SQL Server,. nie ma ograniczeń dotyczących kolejności uaktualniania wersji dodatku service pack programu SQL Server dla bazy danych lokacji w lokacji.

 **Uaktualnienie do nowej wersji programu SQL Server:**   
 Program Configuration Manager obsługuje uaktualnianie w miejscu programu SQL Server do następujących wersji:

 - SQL Server 2012  
 - SQL Server 2014  
 - SQL Server 2016  

Podczas uaktualniania wersji programu SQL Server, który jest hostem bazy danych lokacji, należy uaktualnić wersji programu SQL Server, która jest używana w lokacjach w następującej kolejności:

 1. Najpierw uaktualnij program SQL Server w centralnej lokacji administracyjnej.
 2. Uaktualnij lokacje dodatkowe, przed uaktualnieniem lokacji dodatkowej nadrzędnej lokacji głównej.
 3. Na końcu uaktualnij nadrzędne lokacje główne. Dotyczy to zarówno podrzędnych lokacji głównych, którzy raportują do centralnej lokacji administracyjnej i autonomicznych lokacjach głównych, które są lokacja najwyższego poziomu w hierarchii.

**Poziom szacowania kardynalności serwera SQL i bazy danych lokacji:**   
Po uaktualnieniu bazy danych lokacji z wcześniejszej wersji programu SQL Server, baza danych zachowuje istniejące poziomu szacowania kardynalności SQL (CE), jeśli jest dozwolony dla tego wystąpienia programu SQL Server. Uaktualnianie programu SQL Server z bazą danych na poziom zgodności niższy niż poziom dozwolonych automatycznie ustawia bazy danych na najniższy poziom zgodności dozwolone przez program SQL Server.

W poniższej tabeli przedstawiono poziomy zgodności zalecane dla baz danych lokacji programu Configuration Manager:

|Wersja programu SQL | Poziomy zgodności obsługiwanych |Zalecany poziom|
|----------------|--------------------|--------|
| SQL Server 2016| 130, 120, 110, 100 | 130|
| SQL Server 2014| 120, 110, 100      | 110|

Aby zidentyfikować poziom zgodności programu SQL Server CE na użytek bazy danych lokacji, uruchom następujące zapytanie SQL na serwerze bazy danych lokacji:  **Wybierz nazwę, compatibility_level FROM sys.databases**

 Aby uzyskać więcej informacji o poziomy zgodności SQL CE i sposobu ich ustawiania, zobacz [zmienić poziom zgodności bazy danych (Transact-SQL)](https://msdn.microsoft.com/library/bb510680.aspx).


Aby uzyskać więcej informacji na temat programów SQL Server zobacz dokumentację SQL Server w witrynie TechNet:
-   [Uaktualnianie do programu SQL Server 2012](http://technet.microsoft.com/library/ms143393\(v=sql.110))
-   [Uaktualnianie do programu SQL Server 2014](http://technet.microsoft.com/library/ms143393\(v=sql.120))  
-   [Uaktualnianie do programu SQL Server 2016](https://technet.microsoft.com/library/bb677622(v=sql.130))



### <a name="to-upgrade-sql-server-on-the-site-database-server"></a>Aby uaktualnić program SQL Server na serwerze bazy danych lokacji  

1.  Zatrzymanie wszystkich usług programu Configuration Manager w lokacji.  
2.  Uaktualnij program SQL Server do jego obsługiwanej wersji.  
3.  Ponowne uruchomienie usług programu Configuration Manager.  

> [!NOTE]  
>  Po zmianie wersji programu SQL Server używanej w centralnej lokacji administracyjnej z wersji Standard na wersję Datacenter lub Enterprise partycja bazy danych ograniczająca liczbę klientów obsługiwanych przez hierarchię nie zostaje zmieniona.

