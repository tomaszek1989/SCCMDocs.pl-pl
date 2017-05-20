---
title: Scenariusze instalacji | Dokumentacja firmy Microsoft
description: Poznaj techniki instalowania nowej hierarchii programu Configuration Manager podczas aktualizowania lub uaktualniania lokacji.
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 35586a85-4af9-4c8b-925a-0e32dc8b7346
caps.latest.revision: 6
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9dac6b3fa92c193e3c1a75dd804e0b72fb5394b9
ms.openlocfilehash: dbc303ea9df5a429cb2ef8bd89f372639a4ae2b2
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="scenarios-to-streamline-your-installation-of-system-center-configuration-manager"></a>Scenariusze umożliwiające usprawnienie instalowania programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Wraz z wydaniem wersji aktualizacji dla programu System Center Configuration Manager w bieżącej gałęzi są nowe scenariusze uprościć instalację nowej hierarchii do wersji update (tak jak zaktualizować 1610) i uaktualniania programu Microsoft System Center 2012 Configuration Manager. 

Obsługiwane scenariusze:  

**Zainstalować nową hierarchię gałęzi bieżący System Center Configuration Manager** z uruchomioną wersją aktualizacji.  

-   Zainstaluj tylko lokację najwyższego poziomu, a następnie natychmiast zainstalować aktualizacji do tej lokacji z wersji aktualizacji, która będzie używana. Następnie należy zainstalować dodatkowe Lokacje bezpośrednio do tej wersji aktualizacji.  
-   W tym scenariuszu możesz pominąć proces instalowania dodatkowych lokacji do poziomu linii bazowej, a następnie ich uaktualnienia do wersji aktualizacji, która ma być używana.  
-   W tym scenariuszu możesz pominąć proces instalacji klientów do wersji linii bazowej, a następnie instalując je ponownie podczas aktualizacji do nowszej wersji.  

**Uaktualnienie programu Microsoft System Center 2012 Configuration Manager** infrastruktury w celu aktualizacji w wersji programu System Center Configuration Manager.  

-   Ręcznie uaktualnienia centralnej lokacji administracyjnej i każdej lokacji głównej do linii bazowej wersji (takich jak wersja 1606) przed uruchomieniem instalacji aktualizacji wersji (takich jak wersja 1610).  
-   Nie uaktualnić lokacje dodatkowe z programu Microsoft System Center 2012 Configuration Manager, dopóki nie będzie działać z lokacją główną wersji aktualizacji, która będzie używana.  
-   Nie uaktualniaj klientów z programu Microsoft System Center 2012 Configuration Manager, dopóki nie będzie działać z lokacją główną wersji aktualizacji, która będzie używana.  

## <a name="scenario-install-a-new-hierarchy-to-an-update-version"></a>Scenariusz: Zainstalować nową hierarchię do wersji aktualizacji  
W tym przykładowym scenariuszu przy użyciu linii bazowej wersji programu System Center Configuration Manager, podobnie jak w wersji 1610 do instalacji pierwszej lokacji w hierarchii. Następnie należy zainstalować aktualizację 1610 przed wdrożeniem dodatkowe Lokacje lub klienci.  

-   Ponieważ planujesz użyć wersji aktualizacji (na przykład wersja 1610) i nie pozostaje w wersji linii bazowej (takie jak wersja 1606), nie trzeba instalować dodatkowych lokacji, a następnie je. Dotyczy to również klientów.  
-   Nie zainstalowanie lokacji dodatkowej z wersją 1606 i uaktualnić je do wersji 1610. Po uruchomieniu z lokacją główną wersję 1610, zamiast tego Zainstaluj Lokacje dodatkowe.  

Wykonaj tej sekwencji:  

1.  **Zainstaluj lokację najwyższego poziomu dla nowej hierarchii** przy użyciu nośnika linii bazowej.  

    -   Nośnik linii bazowej służy tylko do instalacji pierwszej lokacji nowej hierarchii.  
    -   Na przykład zainstalować lokacji najwyższego poziomu przy użyciu wersji linii bazowej 1606. Aby uzyskać więcej informacji, zobacz [Kreator instalacji umożliwia zainstalowanie lokacji](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites).  

    Po wykonaniu tego kroku że lokacja najwyższego poziomu uruchomiona wersja 1606.  

2.  **Aby zaktualizować witryny najwyższego poziomu do nowszej wersji, należy użyć aktualizacji w konsoli.**  

    -   Przed zainstalowaniem wszystkie podrzędne Lokacje lub klienci zaktualizować witryny najwyższego poziomu do wersji aktualizacji, który ma być używany.  
    -   Na przykład można zaktualizować uruchomioną wersją 1606 do wersji 1610 witryny najwyższego poziomu. Aby uzyskać więcej informacji, zobacz [Aktualizacje programu System Center Configuration Manager](../../../../core/servers/manage/updates.md).  

    Po wykonaniu tego kroku że lokacja najwyższego poziomu uruchomiona wersja 1610.  

3.  **Zainstaluj nowe podrzędne lokacje główne poniżej centralnej lokacji administracyjnej.**  

    -   Użyj nośnika instalacyjnego z folderu CD.Latest na serwerze centralnej lokacji administracyjnej, aby zainstalować podrzędne lokacje główne. Aby uzyskać więcej informacji, zobacz [The CD.Latest folder for System Center Configuration Manager](../../../../core/servers/manage/the-cd.latest-folder.md) (Folder CD.Latest dla programu System Center Configuration Manager).  

      Ten nośnik źródłowy jest wymagany do zapewnienia, że wersja nowych podrzędnych lokacji głównych będzie zgodna z wersją centralnej lokacji administracyjnej.  

    Po wykonaniu tego kroku nowych lokacji głównych podrzędnych uruchomić wersję 1610.  

4.  **W każdej lokacji głównej użyj opcji w konsoli do zainstalowania nowych lokacji dodatkowej.**  

    -   Ponieważ Lokacje dodatkowe nie został zainstalowany, podczas gdy lokacje główne zostały w wersji 1606, nie należy uaktualnić lokacje dodatkowe.  
    -   Zamiast tego należy zainstalować nowe Lokacje dodatkowe, których jest uruchomiona wersja 1610. Aby uzyskać więcej informacji, zobacz sekcję [Install a secondary site](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites#bkmk_secondary)(Instalacja lokacji dodatkowej) w temacie [Use the SetupWizard to install sites](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites) (Instalowanie lokacji za pomocą Kreatora instalacji).  

    Po wykonaniu tego kroku nowych lokacji dodatkowej są zainstalowane i uruchomić wersję 1610.  

5.  **Zainstalowanie nowych klientów w lokacji głównej.**  

    -   Ponieważ klienci nie został zainstalowany, gdy lokacje główne zostały w wersji 1606, nie trzeba uaktualniać klientów z wersją 1606 do wersji 1610.  
    -   Zamiast tego należy zainstalować nowych klientów, na których jest uruchomiona wersja 1610. Aby uzyskać więcej informacji, zobacz [wdrażania klientów w programie System Center Configuration Manager](../../../clients/deploy/deploy-clients-to-windows-computers.md).  

    Po wykonaniu tego kroku nowych klientów są instalowane w wersji 1610.  

## <a name="scenario-upgrade-system-center-2012-configuration-manager-to-an-update-version-of-system-center-configuration-manager-current-branch"></a>Scenariusz: Uaktualnienie System Center 2012 Configuration Manager do wersji aktualizacji programu System Center Configuration Manager, bieżącej gałęzi  
W tym przykładowym scenariuszu uaktualnienia infrastruktury programu Microsoft System Center 2012 Configuration Manager do wersji aktualizacji programu System Center Configuration Manager, podobnie jak w wersji 1610.  

-   Centralnej lokacji administracyjnej i każdej lokacji głównej należy uaktualnić do wersji linii bazowej 1606 przed zainstalowaniem aktualizacji dla wersji 1610.  
-   Lokacje dodatkowe i klientów nie uaktualnić lub zainstalować wersję 1606. Zamiast tego przechodzące bezpośrednio z programu Microsoft System Center 2012 Configuration Manager programu System Center Configuration Manager 1610 wersji.  

Wykonaj tej sekwencji:  

1.  **Uaktualnienie lokacji programu Microsoft System Center 2012 Configuration Manager najwyższego poziomu** linii bazowej do wersji bieżącej gałęzi przy użyciu nośnika źródłowego programu System Center Configuration Manager (na przykład wersja 1606). Aby uzyskać więcej informacji, zobacz [uaktualnienia programu System Center Configuration Manager](../../../../core/servers/deploy/install/upgrade-to-configuration-manager.md).  

    -   Podobnie jak tradycyjny scenariuszach uaktualniania zawsze najpierw uaktualnić lokację najwyższego poziomu w hierarchii, a następnie Uaktualnij lokacji podrzędnych.  

    Po wykonaniu tego kroku że lokacja najwyższego poziomu uruchomiona wersja 1606.  

2.  **Uaktualnij wszystkie podrzędne lokacje główne w hierarchii** do tej samej wersji linii bazowej.  

    -   Podczas uaktualniania programu Microsoft System Center 2012 Configuration Manager, każdej lokacji głównej należy ręcznie uaktualnić do wersji bieżącej gałęzi linii bazowej.  
    -   W tym momencie spowoduje uaktualnienie nie Lokacje dodatkowe.  

    Po wykonaniu tego kroku w każdej lokacji głównej jest uruchamiana wersja 1606.  

3.  **Ustaw okna obsługi w lokacjach podrzędnych podstawowej.** Po uaktualnieniu wszystkich lokacji głównych do wersji linii bazowej zaplanować konfigurowanie okien obsługi do sterowania podczas instalacji aktualizacji infrastruktury w tych witrynach. Aby uzyskać więcej informacji, zobacz [sposobu używania okien obsługi w programie System Center Configuration Manager](../../../../core/clients/manage/collections/use-maintenance-windows.md).  (Konserwacji systemu windows są nazywane *usługi systemu windows* w wersji 1606.)  

    -   Podrzędna lokacja główna automatycznie zainstaluje te same aktualizacje, które zostały zainstalowane w centralnej lokacji administracyjnej.  
    -   Dodatkowej sties nie są instalowane automatycznie nowe wersje. Należy uaktualnić je ręcznie z konsoli.  

   

    Po wykonaniu tego kroku i po zainstalowaniu aktualizacji w centralnej lokacji administracyjnej podrzędne lokacje główne zainstalują tę aktualizację tylko wtedy, gdy zezwolą na to ich okna obsługi.  

4.  **Zainstaluj wersję aktualizacji w lokacji najwyższego poziomu.** To uaktualnienie lokacji najwyższego poziomu. Po zainstalowaniu wersji aktualizacji witryny administracji centralnej każda podrzędna lokacja główna automatycznie instaluje aktualizacji, chyba że instalacja jest zablokowana z powodu okna obsługi.  

    -   Na przykład można zaktualizować witryny najwyższego poziomu z wersji 1606 1610 wersji. Aby uzyskać więcej informacji, zobacz [Aktualizacje programu System Center Configuration Manager](../../../../core/servers/manage/updates.md).  

    Po wykonaniu tego kroku centralnej lokacji administracyjnej i każdej lokacji głównej uruchomiona wersja 1610.  

5.  **Uaktualnij lokacje dodatkowe.** Po lokacji głównej aktualizacja zostanie zainstalowana i uruchomiona wersja 1610, użyj opcji w konsoli uaktualnić lokacje dodatkowe.  

    -   To uaktualnienie lokacji dodatkowych bezpośrednio z programu Microsoft System Center 2012 Configuration Manager do wersji aktualizacji, który został zainstalowany w lokacji głównej.  
    -   Informacje dotyczące uaktualniania lokacji dodatkowej, zobacz [uaktualnić Lokacje](../../../../core/servers/deploy/install/upgrade-to-configuration-manager.md#bkmk_upgrade) w [uaktualnienia programu System Center Configuration Manager](../../../../core/servers/deploy/install/upgrade-to-configuration-manager.md) tematu.  

6.  **Uaktualnij klientów.** Aby uaktualnić klientów, skorzystaj z informacji w [sposobu uaktualniania klientów na komputerach z systemem Windows w programie System Center Configuration Manager](../../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md).  

    -   To uaktualnienie klientów bezpośrednio z programu Microsoft System Center 2012 Configuration Manager do wersji aktualizacji, który został zainstalowany w lokacji głównej.  

    Po wykonaniu tego kroku klienci uaktualnienia do wersji 1610 bez pierwszego uaktualniania do wersji 1606.

