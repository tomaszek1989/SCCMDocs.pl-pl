---
title: "Wymagania wstępne dotyczące lokacji"
titleSuffix: Configuration Manager
description: "Więcej informacji na temat wymagań wstępnych dotyczących instalowania różnych typów lokacji programu System Center Configuration Manager."
ms.custom: na
ms.date: 7/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 92b339ef-2723-4322-bec6-077b3e8846b0
caps.latest.revision: "5"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 2875a90b1f2ae853563d7716fcfe634efd551fe5
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2017
---
# <a name="prerequisites-for-installing-system-center-configuration-manager-sites"></a>Wymagania wstępne dotyczące instalowania lokacji programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Przed rozpoczęciem instalacji lokacji jest dobrym rozwiązaniem, aby dowiedzieć się więcej o wymaganiach wstępnych dotyczących instalacji różnych typów lokacji programu System Center Configuration Manager.

## <a name="primary-sites-and-the-central-administration-site"></a>Lokacje główne i centralna lokacja administracyjna
Następujące wymagania wstępne dotyczą instalowania centralną lokację administracyjną jako pierwszą lokację w hierarchii, zainstalowaniu autonomicznej lokacji głównej lub podrzędnej lokacji głównej. Jeśli instalujesz centralną lokację administracyjną w ramach rozszerzania hierarchii, zobacz [rozszerzania autonomicznej lokacji głównej](../../../../core/servers/deploy/install/prerequisites-for-installing-sites.md#bkmk_expand) w tym temacie.

###  <a name="bkmk_PrereqPri"></a>Wymagania wstępne dotyczące instalowania lokacji głównej lub centralnej lokacji administracyjnej  

-   Konto użytkownika, który powoduje zainstalowanie lokacji musi mieć następujące uprawnienia:  

    -   **Administrator** na komputerze serwera lokacji  
    -   **Administrator** na każdym komputerze, który będzie obsługiwał **bazy danych lokacji** lub wystąpienie **dostawcy programu SMS** dla lokacji  
    -   **Sysadmin** w wystąpieniu programu SQL Server, który jest hostem bazy danych lokacji  

        > [!IMPORTANT]  
        >  Po zakończeniu instalacji zarówno konto użytkownika uruchamiającego instalację, jak i konto komputera serwera lokacji musi zachować prawa sysadmin do programu SQL Server. Nie usuwaj praw sysadmin z tych kont.  

-   Jeśli instalujesz lokacji głównej, wymagane są następujące prawa dodatkowe:  
    -  **Administrator** na dodatkowych komputerach, na którym będzie instalowany początkowy punkt zarządzania i punkt dystrybucji, w przeciwnym razie na serwerze lokacji  

-   Jeśli instalujesz nową podrzędną lokację główną poniżej centralnej lokacji administracyjnej, wymagane są następujące prawa dodatkowe:  

    -   **Administrator** na komputerze, który jest hostem witryny Administracja centralna  

    -   Prawa administracyjne opartej na rolach w programie Configuration Manager, które są równoważne roli zabezpieczeń **Administrator infrastruktury** lub **administrator o pełnych uprawnieniach**  

-   Należy użyć nośnika instalacyjnego poprawne (plików źródłowych) i uruchom Instalatora z tej lokalizacji. Aby uzyskać informacje o poprawnych plików źródłowych na potrzeby instalacji różnych typów lokacji, zobacz [opcje instalacji różnych typów lokacji](../../../../core/servers/deploy/install/prepare-to-install-sites.md#bkmk_options) w [przygotowaniu się do zainstalowania lokacji](../../../../core/servers/deploy/install/prepare-to-install-sites.md) tematu.

-   Komputer serwera lokacji musi mieć dostęp do zaktualizowanych plików Instalatora firmy Microsoft, w jednym z następujących sposobów:
    -  Przed rozpoczęciem instalacji, możesz pobrać i przechowywać kopię tych plików w sieci lokalnej za pomocą [Narzędzie pobierania Instalatora](../../../../core/servers/deploy/install/setup-downloader.md).
    -  Jeśli lokalną kopię tych plików nie jest dostępny, serwer lokacji musi mieć dostęp do Internetu, aby mógł pobrać tych plików przez firmę Microsoft podczas instalacji.

- Aby rozszerzyć autonomicznej lokacji głównej, który ma zainstalowaną rolę systemu lokacji przez punkt usługi połączenia, należy odinstalować punkt połączenia usługi. W hierarchii jest dozwolone tylko jedno wystąpienie tej roli, a jest dozwolona tylko w lokacji najwyższego poziomu w hierarchii. Będziesz mieć możliwość ponownego zainstalowania roli podczas instalacji centralnej lokacji administracyjnej.
- Serwer lokacji i komputery bazy danych lokacji muszą spełniać wszystkie wymagania wstępne konfiguracji. Przed rozpoczęciem instalacji możesz [ręcznie uruchomić narzędzie sprawdzania wymagań wstępnych](../../../../core/servers/deploy/install/prerequisite-checker.md) do identyfikowania i rozwiązywania problemów.  


### <a name="bkmk_expand"></a>Wymagania wstępne dotyczące rozszerzania autonomicznej lokacji głównej
Autonomicznej lokacji głównej musi spełniać następujące wymagania wstępne, aby rozszerzyć do hierarchii z centralną lokacją administracyjną:

-   **Zainstalowanie nowych instalacji centralnej lokacji administracyjnej przy użyciu nośnika z dysku CD. Najnowszy folder (zawierający pliki źródłowe) odpowiadający wersji autonomicznej lokacji głównej**

 Aby zapewnić Dopasowanie wersji, użyj plików źródłowych w znaleziono [dysku CD. Najnowszy folder](/sccm/core/servers/manage/the-cd.latest-folder) autonomicznej lokacji głównej.

 Aby uzyskać więcej informacji o plikach poprawnego źródła użyć do zainstalowania w różnych lokacjach, zobacz [opcje instalacji różnych typów lokacji](../../../../core/servers/deploy/install/prepare-to-install-sites.md#bkmk_options) w [przygotowaniu się do zainstalowania lokacji](../../../../core/servers/deploy/install/prepare-to-install-sites.md) tematu.


-   **Autonomicznej lokacji głównej nie można skonfigurować do migracji danych z innej hierarchii programu Configuration Manager**  

     Należy zatrzymać aktywną migrację autonomicznej lokacji głównej z innych hierarchii programu Configuration Manager i usunąć wszystkie konfiguracje migracji. Dotyczy to również zadania migracji, które nie zostały wykonane, zbierania danych oraz konfiguracji aktywnej hierarchii źródłowej.  

     Jest to konieczne, ponieważ operacje migracji odbywają się w lokacji najwyższego poziomu w hierarchii, a po rozszerzeniu autonomicznej lokacji głównej konfiguracje migracji nie są przenoszone do centralnej lokacji administracyjnej.  

     Po rozszerzeniu autonomicznej lokacji głównej, jeśli skonfigurujesz migracji w lokacji głównej, centralna lokacja administracyjna wykonuje operacje związane z migracją. Aby uzyskać więcej informacji o sposobie konfigurowania migracji, zobacz [Konfigurowanie hierarchii źródłowych i lokacji źródłowych na potrzeby migracji do programu System Center Configuration Manager](../../../../core/migration/configuring-source-hierarchies-and-source-sites-for-migration.md).  

-   **Konto komputera komputer, który będzie hostem nowej centralnej lokacji administracyjnej musi być członkiem grupy użytkownika administratora w pojedynczy standa lokacji głównej**  

     Aby pomyślnie rozszerzyć autonomiczną lokację główną, konto komputera nowej centralnej lokacji administracyjnej musi mieć **administratora** prawa w autonomicznej lokacji głównej. Jest to wymagane tylko podczas rozszerzania lokacji. Konto można usunąć z grupy użytkowników w lokacji głównej po zakończeniu rozszerzania lokacji.  

-   **Konto użytkownika, który uruchamia Instalatora w celu zainstalowania nowej centralnej lokacji administracyjnej musi mieć prawa administracyjne oparte na rolach w autonomicznej lokacji głównej**  

     Aby zainstalować centralną lokację administracyjną w ramach rozszerzania lokacji, konto użytkownika, który uruchamia Instalatora w celu zainstalowania centralnej lokacji administracyjnej musi mieć zdefiniowane w administracji opartej na rolach w autonomicznej lokacji głównej jako **administrator o pełnych uprawnieniach** lub **Administrator infrastruktury**.  

-   **Aby rozszerzyć lokację, należy odinstalować następujące role systemu lokacji z autonomicznej lokacji głównej:**  

    -   Punkt synchronizacji analizy zasobów  
    -   Punkt ochrony punktu końcowego  
    -   Punkt połączenia usługi  

   Te role systemu lokacji są obsługiwane tylko w lokacji najwyższego poziomu w hierarchii. W związku z tym należy odinstalować te role systemu lokacji, przed rozszerzeniem autonomicznej lokacji głównej. Po rozszerzeniu lokacji można ponownie zainstalować te role systemu lokacji w centralnej lokacji administracyjnej.  

    Wszystkie inne role systemu lokacji można pozostają zainstalowane w lokacji głównej.  

-   **Musi być otwarty port dla programu SQL Server Service Broker (SSB) między autonomiczną lokację główną a komputerem instalującym centralną lokację administracyjną**  

     Do replikacji danych między centralną lokacją administracyjną a lokacją główną, program Configuration Manager wymaga otwartego portu między dwiema lokacjami dla SSB do użycia. Po zainstalowaniu centralnej lokacji administracyjnej i rozszerzenia autonomicznej lokacji głównej, sprawdzanie wymagań wstępnych sprawdza, czy port SSB wybrane jest otwarty w lokacji głównej.  

**Znane problemy podczas konfigurowania usług Azure:**  
Gdy użyj jednej z następujących usług platformy Azure z programem Configuration Manager i planowanie rozszerzania lokacji, po rozwinięciu lokacji należy usunąć, a następnie utwórz ponownie połączenie z usługą.

Usługi:  
-       [Program Operations Manager Suite](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite) (OMS)
-       [Gotowości do uaktualnienia](/sccm/core/clients/manage/upgrade/upgrade-analytics)
-       [Sklep Windows dla firm](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)

Aby rozwiązać ten problem, wykonaj następujące kroki:
 1.    W konsoli programu Configuration Manager należy usunąć usługę Azure z węzła usług Azure.
 2.    W portalu Azure należy usunąć dzierżawy, która jest skojarzona z usługą w węźle usługi Azure Active Directory dzierżaw.  Spowoduje to również usunięcie aplikacji sieci web usługi Azure AD, który jest skojarzony z usługą.  
 3.   Ponownie skonfiguruj połączenie z usługą Azure do użytku z programem Configuration Manager.


## <a name="bkmk_secondary"></a>Lokacje dodatkowe
Poniżej przedstawiono wymagania wstępne dotyczące instalowania lokacji dodatkowej:
-   Administrator konfigurujący instalację lokacji dodatkowej w konsoli programu Configuration Manager musi mieć prawa administracyjne oparte na rolach, które są równoważne roli zabezpieczeń **Administrator infrastruktury** lub **administrator o pełnych uprawnieniach**.  
-   Konto komputera nadrzędnej lokacji głównej musi być **administratora** na komputerze serwera lokacji dodatkowej.  
-   Kiedy lokacja dodatkowa używa uprzednio zainstalowanego wystąpienia programu SQL Server do hostowania bazy danych lokacji dodatkowej:  

    -   **Konto komputera** nadrzędnej lokacji głównej musi mieć **sysadmin** prawa do wystąpienia programu SQL Server na komputerze serwera lokacji dodatkowej.  

    -   **Systemu lokalnego** konto komputera serwera lokacji dodatkowej musi mieć **sysadmin** prawa do wystąpienia programu SQL Server na komputerze serwera lokacji dodatkowej.  

        > [!IMPORTANT]  
        >  Po zakończeniu instalacji oba konta muszą zachować prawa sysadmin do programu SQL Server. Nie usuwaj praw sysadmin z tych kont.  

-   Komputer serwera lokacji dodatkowej musi spełniać wszystkie wymagania wstępne konfiguracji, w tym programu SQL Server i domyślne role systemu lokacji punktu zarządzania i punkt dystrybucji.  
