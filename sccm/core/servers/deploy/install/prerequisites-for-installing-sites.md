---
title: "Wymagania wstępne dotyczące witryn | Dokumentacja firmy Microsoft"
description: "Dowiedz się więcej o wymaganiach wstępnych dotyczących instalowania różnych typów witryn programu System Center Configuration Manager."
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 92b339ef-2723-4322-bec6-077b3e8846b0
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: ff89d4aea6be871e64e0a788f054ba4cadb3e51d
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="prerequisites-for-installing-system-center-configuration-manager-sites"></a>Wymagania wstępne dotyczące instalacji lokacji programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Przed rozpoczęciem instalacji lokacji jest dobrym rozwiązaniem, aby dowiedzieć się więcej o wymaganiach wstępnych dotyczących instalowania różnych typów witryn programu System Center Configuration Manager.

## <a name="primary-sites-and-the-central-administration-site"></a>Lokacje główne i centralna lokacja administracyjna
Następujące wymagania wstępne dotyczą instalowania centralnej lokacji administracyjnej jako pierwszą lokację w hierarchii, zainstalowaniu autonomicznej lokacji głównej lub podrzędnej lokacji głównej. Jeśli witryna Administracja centralna jest instalowany jako część rozszerzenia hierarchii, zobacz [rozszerzania autonomicznej lokacji głównej](../../../../core/servers/deploy/install/prerequisites-for-installing-sites.md#bkmk_expand) w tym temacie.

###  <a name="bkmk_PrereqPri"></a>Wymagania wstępne dotyczące instalacji lokacji głównej lub centralnej lokacji administracyjnej  

-   Konto użytkownika, który instaluje lokacji musi mieć następujące uprawnienia:  

    -   **Administrator** na komputerze serwera lokacji  
    -   **Administrator** na każdym komputerze, który będzie obsługiwać **bazy danych lokacji** lub wystąpienie **dostawcy programu SMS** dla witryny  
    -   **Sysadmin** w wystąpieniu programu SQL Server, który obsługuje bazę danych lokacji  

        > [!IMPORTANT]  
        >  Po zakończeniu instalacji zarówno konto użytkownika uruchamiającego instalację, jak i konto komputera serwera lokacji musi zachować uprawnienia administratora systemu do programu SQL Server. Nie usuwaj uprawnienia administratora systemu z tych kont.  

-   Jeśli instalujesz głównej witryny wymagane są następujące prawa dodatkowe:  
    -  **Administrator** na dodatkowych komputerach, na których zostanie zainstalowany początkowy punkt zarządzania i punkt dystrybucji, ile na serwerze lokacji  

-   Jeśli instalujesz nowej lokacji głównej podrzędnych poniżej witryny Administracja centralna, wymagane są następujące prawa dodatkowe:  

    -   **Administrator** na komputerze, na którym przechowywana jest witryna Administracja centralna  

    -   Prawa administracyjne oparte na rolach w programie Configuration Manager, odpowiadające roli zabezpieczeń **Administrator infrastruktury** lub **pełnego administratora.**  

-   Należy użyć nośnika instalacyjnego poprawne (plików źródłowych) i uruchom Instalatora z tej lokalizacji. Informacje o plikach prawidłowego źródła użyć do zainstalowania różnych typach witryn, zobacz [opcje instalowania różnych typach witryn](../../../../core/servers/deploy/install/prepare-to-install-sites.md#bkmk_options) w [przygotowanie do zainstalowania lokacji](../../../../core/servers/deploy/install/prepare-to-install-sites.md) tematu.

-   Komputer serwera lokacji musi mieć dostęp do zaktualizowane pliki Instalatora firmy Microsoft, w jeden z następujących sposobów:
    -  Przed rozpoczęciem instalacji można pobrać i przechowywanie kopii tych plików w sieci lokalnej za pomocą [Narzędzie pobierania Instalatora](../../../../core/servers/deploy/install/setup-downloader.md).
    -  Jeśli lokalną kopię tych plików nie jest dostępna, serwer lokacji musi mieć dostęp do Internetu, więc można go pobrać te pliki firmy Microsoft podczas instalacji.

- Aby rozszerzyć autonomicznej lokacji głównej, w którym jest zainstalowana rola systemu lokacji przez punkt usługi połączenia, należy odinstalować punkt połączenia usługi. Dozwolony jest tylko jedno wystąpienie tej roli w hierarchii i jest dozwolony tylko w lokacji najwyższego poziomu w hierarchii. Będziesz mieć możliwość ponownego zainstalowania roli podczas instalacji centralnej lokacji administracyjnej.
- Serwer lokacji i komputerach bazy danych lokacji musi spełniać wszystkie konfiguracje wymagań wstępnych. Przed uruchomieniem programu instalacyjnego, mogą [ręcznie uruchomić narzędzie sprawdzania wymagań wstępnych](../../../../core/servers/deploy/install/prerequisite-checker.md) do identyfikowania i rozwiązywania problemów.  


### <a name="bkmk_expand"></a>Wymagania wstępne dotyczące rozszerzania autonomicznej lokacji głównej
Aby rozszerzyć do hierarchii z centralną lokacją administracyjną, autonomicznej lokacji głównej musi spełniać następujące wymagania wstępne:

-   **Należy zainstalować nowych instalacji centralnej lokacji administracyjnej przy użyciu nośnika z dysku CD. Najnowsze folderu (która zawiera pliki źródłowe) odpowiadający wersji autonomicznej lokacji głównej**

 Upewnij się, dopasowanie wersji, należy użyć plików źródłowych znalezione w [dysku CD. Najnowszy folder](/sccm/core/servers/manage/the-cd.latest-folder) autonomicznej lokacji głównej.

 Aby uzyskać więcej informacji o plikach prawidłowego źródła użyć do zainstalowania różnych lokacji, zobacz [opcje instalowania różnych typach witryn](../../../../core/servers/deploy/install/prepare-to-install-sites.md#bkmk_options) w [przygotowanie do zainstalowania lokacji](../../../../core/servers/deploy/install/prepare-to-install-sites.md) tematu.


-   **Nie można skonfigurować autonomicznej lokacji głównej do migracji danych z innej hierarchii programu Configuration Manager**  

     Należy zatrzymać aktywną migrację danych do autonomicznej lokacji głównej z innych hierarchii programu Configuration Manager i usunąć wszystkie konfiguracje migracji. Obejmuje to zadania migracji, które nie zostały ukończone, zbierania danych i konfiguracji aktywnej hierarchii źródłowej.  

     Jest to konieczne, ponieważ operacje migracji odbywają się za pośrednictwem lokacji najwyższej warstwy w hierarchii, a po rozszerzeniu autonomicznej lokacji głównej konfiguracje migracji nie transferu witryny administracji centralnej.  

     Jeżeli po rozszerzeniu autonomicznej lokacji głównej, należy zmienić konfigurację migracji w lokacji głównej, centralna lokacja administracyjna wykonuje operacje związane z migracją. Aby uzyskać więcej informacji o sposobie konfigurowania migracji, zobacz [Konfigurowanie hierarchii źródłowych i lokacji źródłowych na potrzeby migracji programu System Center Configuration Manager](../../../../core/migration/configuring-source-hierarchies-and-source-sites-for-migration.md).  

-   **Konto komputera komputer, który będzie hostem nowej centralnej lokacji administracyjnej musi należeć do grupy użytkowników administratora na pojedynczy standa lokacji głównej**  

     Aby pomyślnie rozszerzyć autonomiczną lokację główną, musi mieć konto komputera nowej witryny Administracja centralna **administratora** prawa w autonomicznej lokacji głównej. Jest to wymagane tylko podczas rozszerzania lokacji. Konto można usunąć z grupy użytkowników w lokacji głównej, po zakończeniu rozszerzania lokacji.  

-   **Konto użytkownika, który uruchamia Instalatora w celu zainstalowania nowej centralnej lokacji administracyjnej musi mieć uprawnienia do administrowania opartego na rolach w autonomicznej lokacji głównej**  

     Aby zainstalować centralną lokację administracyjną w ramach rozszerzania lokacji, konto użytkownika, który uruchamia Instalatora w celu zainstalowania centralnej lokacji administracyjnej musi mieć zdefiniowane w administracji opartej na rolach w autonomicznej lokacji głównej jako **administrator o pełnych uprawnieniach** lub **Administrator infrastruktury**.  

-   **Aby rozszerzyć lokację, należy odinstalować następujące role systemu lokacji autonomicznej lokacji głównej:**  

    -   Punkt synchronizacji analizy zasobów  
    -   Punkt ochrony punktu końcowego  
    -   Punkt połączenia usługi  

   Te role systemu lokacji są obsługiwane tylko w lokacji najwyższego poziomu w hierarchii. W związku z tym należy odinstalować te role systemu lokacji, przed rozszerzeniem autonomicznej lokacji głównej. Po rozszerzeniu lokacji można ponownie zainstalować te role systemu lokacji w witrynie Administracja centralna.  

    Wszystkie inne role systemu lokacji można pozostają zainstalowane w lokacji głównej.  

-   **Musi być otwarty port dla SQL Server Service Broker (SSB) między autonomicznej lokacji głównej i komputera, na którym zostanie zainstalowany w witrynie Administracja centralna**  

     Do replikacji danych między centralną lokacją administracyjną i lokacją główną, Configuration Manager wymaga otwartego portu między dwiema lokacjami dla SSB do użycia. Podczas instalowania centralnej lokacji administracyjnej i rozszerzania autonomicznej lokacji głównej, sprawdzanie wymagań wstępnych nie sprawdza czy port określony dla SSB jest otwarty w lokacji podstawowej.  


## <a name="bkmk_secondary"></a>Lokacje dodatkowe
Wymagania wstępne dotyczące instalacji lokacji dodatkowej są następujące:
-   Administrator konfigurujący instalację lokacji dodatkowej w konsoli programu Configuration Manager musi mieć prawa administracyjne oparte na rolach odpowiadające roli zabezpieczeń **Administrator infrastruktury** lub **administrator o pełnych uprawnieniach**.  
-   Konto komputera nadrzędnej lokacji głównej musi być **administratora** na komputerze serwera lokacji dodatkowej.  
-   Jeśli lokacja dodatkowa używa uprzednio zainstalowanego wystąpienia programu SQL Server do obsługi bazy danych lokacji dodatkowej:  

    -   **Konto komputera** nadrzędnej lokacji głównej musi mieć **sysadmin** prawa do wystąpienia programu SQL Server na komputerze serwera lokacji dodatkowej.  

    -   **Systemu lokalnego** konto komputera serwera lokacji dodatkowej musi mieć **sysadmin** prawa do wystąpienia programu SQL Server na komputerze serwera lokacji dodatkowej.  

        > [!IMPORTANT]  
        >  Po zakończeniu instalacji oba konta muszą zachować uprawnienia administratora systemu do programu SQL Server. Nie usuwaj uprawnienia administratora systemu z tych kont.  

-   Komputer serwera lokacji dodatkowej musi spełniać wszystkie konfiguracje wymagań wstępnych, w tym program SQL Server i domyślne role systemu lokacji punktu zarządzania i punkt dystrybucji.  

