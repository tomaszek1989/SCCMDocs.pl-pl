---
title: Uaktualnij infrastruktury lokalnej | Dokumentacja firmy Microsoft
description: "Informacje o sposobie uaktualniania infrastruktury, takich jak SQL Server i systemu operacyjnego lokacji systemów lokacji."
ms.custom: na
ms.date: 2/14/2017
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
ms.sourcegitcommit: 2e711cce2435957f3e85dad08f17260e1a224fc2
ms.openlocfilehash: c6448932e91a02984ca57cef0b75c10ea3f43fa1
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="upgrade-on-premises-infrastructure-that-supports-system-center-configuration-manager"></a>Uaktualnianie infrastruktury lokalnej, która obsługuje program System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Użyj informacje w tym temacie ułatwiają uaktualniania infrastruktury serwera, na którym działa System Center Configuration Manager.  

 - Jeśli chcesz uaktualnić z wcześniejszej wersji programu Configuration Manager programu System Center Configuration Manager, zobacz [uaktualnienia programu System Center Configuration Manager](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager).

- Jeśli chcesz zaktualizować infrastruktury programu System Center Configuration Manager do nowej wersji, zobacz [aktualizacji dla programu System Center Configuration Manager](/sccm/core/servers/manage/updates).

##  <a name="BKMK_SupConfigUpgradeSiteSrv"></a>Uaktualnij system operacyjny systemów lokacji  
 Program Configuration Manager obsługuje uaktualnienia w miejscu systemu operacyjnego serwery obsługujące serwer lokacji i serwerów zdalnych, które obsługują żadnych ról systemu lokacji w następujących sytuacjach:  

-   Uaktualnienie w miejscu do nowszego dodatku service Pack systemu Windows Server, jeśli Wynikowy poziom dodatku service pack systemu Windows będzie obsługiwane przez program Configuration Manager.  
-   Uaktualnienie w miejscu z:
    - Windows Server 2012 R2 do systemu Windows Server 2016 ([wyświetlić dodatkowe szczegóły](#upgrade-windows-server-2012-r2-to-2016)).
    - Windows Server 2012 do systemu Windows Server 2012 R2 ([wyświetlić dodatkowe szczegóły](#upgrade-windows-server-2012-to-windows-server-2012-r2)).
    - Gdy używasz 1602 wersji programu Configuration Manager lub później, jest również obsługiwane uaktualnienia do systemu Windows Server 2012 R2 systemu Windows Server 2008 R2 ([wyświetlić dodatkowe szczegóły](#upgrade-windows-server-2008-r2-to-windows-server-2012-r2)).

    > [!WARNING]  
    >  Przed uaktualnieniem do systemu Windows Server 2012 R2 *należy odinstalować usługi WSUS 3.2* z serwera.  
    >   
    >  Informacji dotyczących tego kroku krytyczne, zobacz sekcję "Nowe i zmienione funkcje" w [Omówienie usług Windows Server Update](https://technet.microsoft.com/library/hh852345.aspx) w dokumentacji systemu Windows Server.  

Aby uaktualnić serwer, użyj procedury uaktualniania udostępnione przez system operacyjny, który jest uaktualniany do.  Zobacz następujące tematy:
  -  [Uaktualnij opcje dla systemu Windows Server 2012 R2](https://technet.microsoft.com/library/dn303416.aspx) w dokumentacji systemu Windows Server.  
  - [Opcje uaktualniania i konwersji dla systemu Windows Server 2016](https://technet.microsoft.com/windows-server-docs/get-started/supported-upgrade-paths) w dokumentacji systemu Windows Server.

### <a name="upgrade-windows-server-2012-r2-to-2016"></a>Uaktualnienie systemu Windows Server 2012 R2 lub 2016  
Ten scenariusz uaktualnienia systemu operacyjnego ma następujące warunki:

**Przed uaktualnieniem:**  
-     Usuń klienta programu System Center Endpoint Protection (SCEP). Windows Server 2016 ma usługi Windows Defender wbudowane, która zastępuje klienta SCEP. Obecność klienta SCEP można uniemożliwiają uaktualnienie do systemu Windows Server 2016.

**Po uaktualnieniu:**
-     Upewnij się, że usługa Windows Defender jest włączona, Ustaw automatyczne uruchamianie i uruchomiona.
-     Upewnij się, że są uruchomione następujące usługi programu Configuration Manager:
  -     SMS_EXECUTIVE
  -     SMS_SITE_COMPONENT_MANAGER


-     Upewnij się, **aktywacji procesów systemu Windows** i **WWW/W3svc** usługi są włączone, ustaw dla automatycznego uruchamiania i uruchomione dla następujących ról systemu lokacji (te usługi są wyłączone podczas uaktualniania):
  -     Serwer lokacji
  -     Punkt zarządzania
  -     Punkt usługi sieci Web Wykaz aplikacji
  -     Punkt witryny sieci Web wykazu aplikacji


-     Upewnij się, każdy serwer, który obsługuje rolę systemu lokacji nadal spełniają wszystkie [prequisites dla ról systemu lokacji](/sccm/core/plan-design/configs/site-and-site-system-prerequisites) uruchomiony na tym serwerze. Na przykład może być konieczne ponowne zainstalowanie usługi BITS, WSUS, lub skonfiguruj ustawienia określone dla usług IIS.

  Po przywróceniu brakujących wymagań wstępnych należy ponownie uruchomić serwer więcej czasu upewnij się, że usługi są uruchomione i operacyjnej.

**Znany problem dla zdalnej konsoli programu Configuration Manager:**  
Po uaktualnieniu serwera lokacji lub na serwerze obsługującym wystąpienie SMS_Provider do systemu Windows Server 2016 użytkownicy z uprawnieniami administracyjnymi może nie można połączyć konsolę programu Configuration Manager do lokacji. Aby obejść ten problem, należy ręcznie przywrócić uprawnienia grupy Administratorzy programu SMS w usłudze WMI. Należy określić uprawnienia na serwerze lokacji i na każdym serwerze zdalnym obsługujący wystąpienie SMS_Provider:

1. Odpowiednich serwerach, Otwórz program Microsoft Management Console (MMC) i Dodawanie przystawki dla **Sterowanie usługą WMI**, a następnie wybierz **komputera lokalnego**.
2. W przystawce programu MMC, otwórz **właściwości** z **Sterowanie usługą WMI (lokalnie)** i wybierz **zabezpieczeń** kartę.
3. Rozwiń drzewo poniżej katalogu głównego, wybierz **SMS** węzeł, a następnie wybierz **zabezpieczeń**.  Upewnij się, **Administratorzy programu SMS** grupa ma następujące uprawnienia:
  -     Włącz konto
  -     Włączanie zdalne
4. Na **karta Zabezpieczenia** poniżej **SMS** węzła, wybierz opcję **site_**&lt;*kod lokacji*> węzeł, a następnie wybierz **zabezpieczeń**. Upewnij się, **Administratorzy programu SMS** grupa ma następujące uprawnienia:
  -   Wykonywanie metod
  -   Zapis dostawcy
  -   Włącz konto
  -   Włączanie zdalne
5. Zapisz uprawnienia, aby przywrócić dostęp do konsoli programu Configuration Manager.

### <a name="windows-server-2012-to-windows-server-2012-r2"></a>Windows Server 2012 do systemu Windows Server 2012 R2

**Przed uaktualnieniem:**
-  W przeciwieństwie do innych obsługiwanych scenariuszach w tym scenariuszu nie wymaga dodatkowe uwagi przed uaktualnieniem.

**Po uaktualnieniu:**
  -    Sprawdź, czy usługi wdrażania systemu Windows jest uruchomione dla następujących ról systemu lokacji (ta usługa zostanie zatrzymana podczas uaktualniania):
    - Serwer lokacji
    - Punkt zarządzania
    - Punkt usługi sieci Web Wykaz aplikacji
    - Punkt witryny sieci Web wykazu aplikacji


  -     Upewnij się, **aktywacji procesów systemu Windows** i **WWW/W3svc** usługi są włączone, ustaw dla automatycznego uruchamiania i uruchomione dla następujących ról systemu lokacji (te usługi są wyłączone podczas uaktualniania):
    -     Serwer lokacji
    -     Punkt zarządzania
    -     Punkt usługi sieci Web Wykaz aplikacji
    -     Punkt witryny sieci Web wykazu aplikacji


  -     Upewnij się, każdy serwer, który obsługuje rolę systemu lokacji nadal spełniają wszystkie [prequisites dla ról systemu lokacji](/sccm/core/plan-design/configs/site-and-site-system-prerequisites) uruchomiony na tym serwerze. Na przykład może być konieczne ponowne zainstalowanie usługi BITS, WSUS, lub skonfiguruj ustawienia określone dla usług IIS.

  Po przywróceniu brakujących wymagań wstępnych należy ponownie uruchomić serwer więcej czasu upewnij się, że usługi są uruchomione i operacyjnej.

### <a name="upgrade-windows-server-2008-r2-to-windows-server-2012-r2"></a>Uaktualnienie systemu Windows Server 2008 R2 do systemu Windows Server 2012 R2
Ten scenariusz uaktualnienia systemu operacyjnego ma następujące warunki:  

**Przed uaktualnieniem:**
-     Odinstaluj program WSUS 3.2.  
    Przed uaktualnieniem systemu operacyjnego serwera do systemu Windows Server 2012 R2, należy odinstalować WSUS 3.2 z serwera. Informacji dotyczących tego kroku krytyczne można znaleźć w temacie nowe i zmienione funkcje części Omówienie usług aktualizacji serwera systemu Windows w dokumentacji systemu Windows Server.

**Po uaktualnieniu:**
  -    Sprawdź, czy usługi wdrażania systemu Windows jest uruchomione dla następujących ról systemu lokacji (ta usługa zostanie zatrzymana podczas uaktualniania):
    - Serwer lokacji
    - Punkt zarządzania
    - Punkt usługi sieci Web Wykaz aplikacji
    - Punkt witryny sieci Web wykazu aplikacji


  -     Upewnij się, **aktywacji procesów systemu Windows** i **WWW/W3svc** usługi są włączone, ustaw dla automatycznego uruchamiania i uruchomione dla następujących ról systemu lokacji (te usługi są wyłączone podczas uaktualniania):
    -     Serwer lokacji
    -     Punkt zarządzania
    -     Punkt usługi sieci Web Wykaz aplikacji
    -     Punkt witryny sieci Web wykazu aplikacji


  -     Upewnij się, każdy serwer, który obsługuje rolę systemu lokacji nadal spełniają wszystkie [wymagania wstępne dla ról systemu lokacji](/sccm/core/plan-design/configs/site-and-site-system-prerequisites) uruchomiony na tym serwerze. Na przykład może być konieczne ponowne zainstalowanie usługi BITS, WSUS, lub skonfiguruj ustawienia określone dla usług IIS.

  Po przywróceniu brakujących wymagań wstępnych należy ponownie uruchomić serwer więcej czasu upewnij się, że usługi są uruchomione i operacyjnej.


### <a name="unsupported-upgrade-scenarios"></a>Nieobsługiwane scenariusze uaktualniania
W następujących scenariuszach uaktualniania systemu Windows Server są najczęściej zadawane dotyczące, ale nie obsługiwane przez program Configuration Manager:  

-   Windows Server 2008, Windows Server 2012 lub nowszy  
-   Windows Server 2008 R2 do systemu Windows Server 2012



##  <a name="BKMK_SupConfigUpgradeClient"></a>Uaktualnij system operacyjny klientów programu Configuration Manager  
 Uaktualnienie w miejscu systemu operacyjnego programu Configuration Manager obsługuje klientów programu Configuration Manager w następujących sytuacjach:  

-   Uaktualnienie w miejscu do nowszego dodatku service Pack systemu Windows czy Wynikowy poziom dodatku service pack będzie obsługiwane przez program Configuration Manager.  

-   Uaktualnienie w miejscu systemu Windows z obsługiwanej wersji systemu Windows 10. Aby uzyskać więcej informacji, zobacz [Uaktualnianie systemu Windows do najnowszej wersji przy użyciu programu System Center Configuration Manager](../../../osd/deploy-use/upgrade-windows-to-the-latest-version.md).  

-   Z kompilacją obsługi uaktualnień systemu Windows 10.  Aby uzyskać więcej informacji, zobacz [Zarządzanie systemem Windows jako usługą za pomocą programu System Center Configuration Manager](../../../osd/deploy-use/manage-windows-as-a-service.md).  

##  <a name="BKMK_SupConfigUpgradeDBSrv"></a>Uaktualnij program SQL Server na serwerze bazy danych lokacji  
  Program Configuration Manager obsługuje uaktualnienie w miejscu programu SQL Server z obsługiwanej wersji programu SQL Server na serwerze bazy danych lokacji. Scenariuszach uaktualniania programu SQL Server w tej sekcji są obsługiwane przez program Configuration Manager i zawiera wymogi dla każdego scenariusza.

 Aby uzyskać informacje o wersji programu SQL Server, które są obsługiwane przez program Configuration Manager, zobacz [obsługę wersji programu SQL Server dla programu System Center Configuration Manager](../../../core/plan-design/configs/support-for-sql-server-versions.md).  

 **Uaktualnienie wersji dodatku service pack programu SQL Server:**    
 Program Configuration Manager obsługuje uaktualnienia w miejscu programu SQL Server do nowszego dodatku service pack, jeśli Wynikowy poziom pakietu usług SQL Server będzie obsługiwane przez program Configuration Manager.

 Jeśli masz wiele lokacji programu Configuration Manager w hierarchii każdej lokacji można uruchomić wersję pakietu innej usługi programu SQL Server, a istnieje bez ograniczeń, kolejność, w której wersji dodatku service pack programu SQL Server dla bazy danych lokacji uaktualnienia lokacji.

 **Uaktualnienie do nowej wersji programu SQL Server:**   
 Program Configuration Manager obsługuje uaktualniania w miejscu programu SQL Server do następujących wersji:

 - SQL Server 2012  
 - SQL Server 2014  
 - SQL Server 2016  

Podczas uaktualniania wersji programu SQL Server, który obsługuje bazę danych lokacji należy uaktualnić wersji programu SQL Server, która jest używana w lokacjach w następującej kolejności:

 1. Najpierw uaktualnij program SQL Server w centralnej lokacji administracyjnej.
 2. Przed uaktualnieniem lokacji dodatkowej nadrzędnej lokacji głównej, należy uaktualnić lokacje dodatkowe.
 3. Na końcu uaktualnij nadrzędne lokacje główne. Dotyczy to zarówno podrzędne Lokacje główne, którzy raportują do witryny administracji centralnej i autonomicznych lokacjach głównych, które są lokacji najwyższego poziomu w hierarchii.

**Poziom szacowania Kardynalność serwera SQL i bazy danych lokacji:**   
Po uaktualnieniu bazy danych lokacji z wcześniejszej wersji programu SQL Server, baza danych zachowuje jego poziom istniejących szacowania Kardynalność SQL (CE) Jeśli jest co najmniej dozwolone dla tego wystąpienia programu SQL Server. Uaktualnianie programu SQL Server z bazą danych na poziom zgodności niższy niż dozwolony poziom automatycznie ustawia bazy danych na najniższy poziom zgodności dozwolone przez program SQL Server.

W poniższej tabeli przedstawiono poziomy zgodności zalecane dla baz danych lokacji programu Configuration Manager:

|Wersja programu SQL | Poziomy zgodności obsługiwane |Zalecany poziom|
|----------------|--------------------|--------|
| SQL Server 2016| 130, 120, 110, 100 | 130|
| SQL Server 2014| 120, 110, 100      | 110|

Aby określić poziom zgodności programu SQL Server CE na użytek bazy danych lokacji, uruchom następujące zapytanie SQL na serwerze bazy danych lokacji:  **Wybierz nazwę, compatibility_level FROM sys.databases**

 Aby uzyskać więcej informacji na poziomy zgodności SQL CE i jak je ustawić, zobacz [zmienić poziom zgodności bazy danych (Transact-SQL)](https://msdn.microsoft.com/library/bb510680.aspx).


Więcej informacji na temat programu SQL Server zobacz dokumentację programu SQL Server w witrynie TechNet:
-   [Uaktualnianie do programu SQL Server 2012](http://technet.microsoft.com/library/ms143393\(v=sql.110))
-   [Uaktualnianie do programu SQL Server 2014](http://technet.microsoft.com/library/ms143393\(v=sql.120))  
-   [Uaktualnianie do programu SQL Server 2016](https://technet.microsoft.com/library/bb677622(v=sql.130))



### <a name="to-upgrade-sql-server-on-the-site-database-server"></a>Aby uaktualnić program SQL Server na serwerze bazy danych lokacji  

1.  Zatrzymanie wszystkich usług programu Configuration Manager w witrynie.  
2.  Uaktualnij program SQL Server do jego obsługiwanej wersji.  
3.  Ponowne uruchomienie usług programu Configuration Manager.  

> [!NOTE]  
>  Po zmianie wersji programu SQL Server używanej w centralnej lokacji administracyjnej z wersji Standard na wersję Datacenter lub Enterprise partycja bazy danych ograniczająca liczbę klientów obsługiwanych przez hierarchię nie zostaje zmieniona.

