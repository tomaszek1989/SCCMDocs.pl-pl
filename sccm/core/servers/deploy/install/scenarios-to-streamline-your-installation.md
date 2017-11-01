---
title: Scenariusze instalacji
titleSuffix: Configuration Manager
description: "Dowiedz się więcej metod dotyczących instalacji nowej hierarchii programu Configuration Manager podczas aktualizowania lub uaktualniania lokacji."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 35586a85-4af9-4c8b-925a-0e32dc8b7346
caps.latest.revision: "6"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 9e7cdd08ba7850f4cb3558c7474c0583e4411b98
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="scenarios-to-streamline-your-installation-of-system-center-configuration-manager"></a>Scenariusze umożliwiające usprawnienie instalowania programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Wraz z wydaniem zaktualizowanych wersji dla bieżącej gałęzi programu System Center Configuration Manager istnieją nowe scenariusze usprawniające instalowanie nowej hierarchii w zaktualizowanej wersji (np. aktualizacji 1610) i umożliwiające uaktualnienie z programu Microsoft System Center 2012 Configuration Manager.

Obsługiwane scenariusze:  

**Instalacja nowej hierarchii gałęzi bieżący System Center Configuration Manager** , na którym działają zaktualizowanej wersji.  

-   Zainstaluj tylko lokację najwyższego poziomu, a następnie natychmiast zainstalować aktualizację lokację bieżącej wersji aktualizacji, która będzie używana. Następnie można zainstalować dodatkowe Lokacje bezpośrednio w zaktualizowanej wersji.  
-   W tym scenariuszu możesz pominąć proces instalowania dodatkowych lokacji na poziomie linii bazowej, a następnie zaktualizować je do zaktualizowanej wersji, która ma być używany.  
-   W tym scenariuszu możesz pominąć proces instalacji klientów do wersji linii bazowej i ponownie zainstalować je po zaktualizowaniu do nowszej wersji.  

**Uaktualnij program Microsoft System Center 2012 Configuration Manager** infrastruktury do zaktualizowanej wersji programu System Center Configuration Manager.  

-   Ręcznie uaktualnienia centralnej lokacji administracyjnej i każdej lokacji głównej do wersji linii bazowej (np. wersja 1606) Aby zainstalować zaktualizowaną wersję (takie jak wersja 1610).  
-   Nie uaktualnić lokacje z programu Microsoft System Center 2012 Configuration Manager, zanim Lokacje podstawowe zaktualizowanej wersji, która będzie używana.  
-   Nie uaktualniaj klientów z programu Microsoft System Center 2012 Configuration Manager, zanim Lokacje podstawowe zaktualizowanej wersji, która będzie używana.  

## <a name="scenario-install-a-new-hierarchy-to-an-update-version"></a>Scenariusz: Instalacja nowej hierarchii w zaktualizowanej wersji  
W tym przykładowym scenariuszu należy zainstalować pierwszą lokację hierarchii za pomocą wersji bazowej programu System Center Configuration Manager, takie jak wersja 1610. Następnie należy zainstalować aktualizację 1610 przed wdrożeniem dodatkowych lokacji lub klientów.  

-   Ponieważ planujesz użycie zaktualizowanej wersji (takie jak wersja 1610), a nie pozostanie przy wersji linii bazowej (np. wersja 1606), nie trzeba instalować dodatkowych lokacji, a następnie je. Dotyczy to również klientów.  
-   Nie instalowanie lokacji dodatkowej z wersją 1606, przeprowadzając następnie uaktualnienie do wersji 1610. Po Lokacje główne wersją 1610, zamiast tego Zainstaluj Lokacje dodatkowe.  

Wykonaj tej sekwencji:  

1.  **Zainstaluj lokację najwyższego poziomu dla nowej hierarchii** za pomocą nośnika linii bazowej.  

    -   Nośnika linii bazowej można użyć tylko do instalowania pierwszej lokacji nowej hierarchii.  
    -   Na przykład zainstalować lokację najwyższego poziomu przy użyciu wersji linii bazowej 1606. Aby uzyskać więcej informacji, zobacz [instalowanie lokacji za pomocą Kreatora konfiguracji](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites).  

    Po wykonaniu tego kroku w lokacji najwyższego poziomu jest uruchomiona wersja 1606.  

2.  **Użyj aktualizacji w konsoli, aby zaktualizować lokację najwyższego poziomu do nowszej wersji.**  

    -   Przed zainstalowaniem jakichkolwiek podrzędnych lokacji lub klientów zaktualizuj lokację najwyższego poziomu do zaktualizowanej wersji, która ma być używany.  
    -   Na przykład należy zaktualizować lokację najwyższego poziomu z wersją 1606 do wersji 1610. Aby uzyskać więcej informacji, zobacz [Aktualizacje programu System Center Configuration Manager](../../../../core/servers/manage/updates.md).  

    Po wykonaniu tego kroku w lokacji najwyższego poziomu jest uruchomiona wersja 1610.  

3.  **Zainstaluj nowe podrzędne lokacje główne poniżej centralnej lokacji administracyjnej.**  

    -   Użyj nośnika instalacyjnego z folderu CD.Latest na serwerze centralnej lokacji administracyjnej, aby zainstalować podrzędne lokacje główne. Aby uzyskać więcej informacji, zobacz [The CD.Latest folder for System Center Configuration Manager](../../../../core/servers/manage/the-cd.latest-folder.md) (Folder CD.Latest dla programu System Center Configuration Manager).  

      Ten nośnik źródłowy jest wymagany do zapewnienia, że wersja nowych podrzędnych lokacji głównych będzie zgodna z wersją centralnej lokacji administracyjnej.  

    Po wykonaniu tego kroku nowe podrzędne Lokacje główne wersją 1610.  

4.  **W każdej lokacji głównej użyj opcji konsoli do zainstalowania nowych lokacji dodatkowych.**  

    -   Ponieważ Lokacje dodatkowe nie został zainstalowany, gdy lokacje główne były w wersji 1606, nie trzeba uaktualnić lokacje dodatkowe.  
    -   Zamiast tego należy zainstalować nowe Lokacje dodatkowe używające wersji 1610. Aby uzyskać więcej informacji, zobacz sekcję [Install a secondary site](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites#bkmk_secondary)(Instalacja lokacji dodatkowej) w temacie [Use the SetupWizard to install sites](/sccm/core/servers/deploy/install/use-the-setup-wizard-to-install-sites) (Instalowanie lokacji za pomocą Kreatora instalacji).  

    Po wykonaniu tego kroku nowe Lokacje dodatkowe są zainstalowane i wersją 1610.  

5.  **Zainstaluj nowych klientów w lokacji głównej.**  

    -   Ponieważ klienci nie byli instalowani, gdy lokacje główne były w wersji 1606, jest konieczne uaktualnienie do wersji 1610 wersji 1606 klientów.  
    -   Zamiast tego należy zainstalować nowych klientów, których jest uruchomiona wersja 1610. Aby uzyskać więcej informacji, zobacz [wdrażanie klientów w programie System Center Configuration Manager](../../../clients/deploy/deploy-clients-to-windows-computers.md).  

    Po wykonaniu tego kroku nowi klienci są zainstalowane z wersją 1610.  

## <a name="scenario-upgrade-system-center-2012-configuration-manager-to-an-update-version-of-system-center-configuration-manager-current-branch"></a>Scenariusz: Uaktualnienie System Center 2012 Configuration Manager do zaktualizowanej wersji programu System Center Configuration Manager, bieżącej gałęzi  
W tym przykładowym scenariuszu uaktualnienie infrastruktury programu Microsoft System Center 2012 Configuration Manager do zaktualizowanej wersji programu System Center Configuration Manager, takie jak wersja 1610.  

-   Centralnej lokacji administracyjnej i każdej lokacji głównej należy uaktualnić do wersji linii bazowej 1606 przed zainstalowaniem aktualizacji do wersji 1610.  
-   Lokacje dodatkowe i klienci nie uaktualnienia lub zainstaluj wersję 1606. Zamiast tego przechodzą bezpośrednio z programu Microsoft System Center 2012 Configuration Manager do System Center Configuration Manager w wersji 1610.  

Wykonaj tej sekwencji:  

1.  **Uaktualnij lokację najwyższego poziomu programu Microsoft System Center 2012 Configuration Manager** do wersji linii bazowej bieżącej gałęzi przy użyciu nośnika źródłowego programu System Center Configuration Manager (takie jak wersja 1606). Aby uzyskać więcej informacji, zobacz [uaktualnienia do programu System Center Configuration Manager](../../../../core/servers/deploy/install/upgrade-to-configuration-manager.md).  

    -   Podobnie jak tradycyjnych scenariuszy uaktualniania zawsze najpierw uaktualniania lokacji najwyższego poziomu w hierarchii, a następnie Uaktualnij lokacje podrzędne.  

    Po wykonaniu tego kroku w lokacji najwyższego poziomu jest uruchomiona wersja 1606.  

2.  **Uaktualnij wszystkie podrzędne lokacje główne w hierarchii** do tej samej wersji linii bazowej.  

    -   Po uaktualnieniu z programu Microsoft System Center 2012 Configuration Manager, należy ręcznie uaktualnić każdej lokacji głównej do wersji linii bazowej bieżącej gałęzi.  
    -   Nie uaktualni w tym momencie Lokacje dodatkowe.  

    Po wykonaniu tego kroku w każdej lokacji głównej jest uruchomiona wersja 1606.  

3.  **Ustaw okna obsługi w podrzędnych lokacjach głównych.** Po uaktualnieniu wszystkich lokacji głównych do wersji linii bazowej Zaplanuj skonfigurowanie okien obsługi w celu kontrolowania, podczas instalacji aktualizacji infrastruktury przez te lokacje. Aby uzyskać więcej informacji, zobacz [używanie okien obsługi w programie System Center Configuration Manager](../../../../core/clients/manage/collections/use-maintenance-windows.md).  (Okna obsługi były nazywane *usługi systemu windows* w wersji 1606.)  

    -   Podrzędna lokacja główna automatycznie zainstaluje te same aktualizacje, które zostały zainstalowane w centralnej lokacji administracyjnej.  
    -   Lokacje dodatkowe nie instalują automatycznie nowych wersji. Należy uaktualnić je ręcznie z poziomu konsoli.  

  Po wykonaniu tego kroku i po zainstalowaniu aktualizacji w centralnej lokacji administracyjnej podrzędne lokacje główne zainstalują tę aktualizację tylko wtedy, gdy zezwolą na to ich okna obsługi.  

4.  **Zainstaluj zaktualizowaną wersję w lokacji najwyższego poziomu.** Spowoduje to zaktualizowanie lokacji najwyższego poziomu. Po zainstalowaniu zaktualizowanej wersji centralnej lokacji administracyjnej wszystkie podrzędne Lokacje główne automatycznie zainstalują aktualizację, chyba, że instalacja jest zablokowana przez okno obsługi.  

    -   Na przykład należy zaktualizować lokację najwyższego poziomu z wersji 1606 do wersji 1610. Aby uzyskać więcej informacji, zobacz [Aktualizacje programu System Center Configuration Manager](../../../../core/servers/manage/updates.md).  

    Po wykonaniu tego kroku w centralnej lokacji administracyjnej i każdej lokacji głównej wersją 1610.  

5.  **Uaktualnij lokacje dodatkowe.** Po lokacji głównej aktualizacja zostanie zainstalowana i uruchomiona wersja 1610, użyj opcji w konsoli, aby uaktualnić lokacje dodatkowe.  

    -   To spowoduje uaktualnienie lokacji dodatkowych bezpośrednio z programu Microsoft System Center 2012 Configuration Manager do zaktualizowanej wersji zainstalowanej w lokacji głównej.  
    -   Aby uzyskać informacje dotyczące uaktualniania lokacji dodatkowej, zobacz [uaktualnienia lokacji](../../../../core/servers/deploy/install/upgrade-to-configuration-manager.md#bkmk_upgrade) w [uaktualnienia do programu System Center Configuration Manager](../../../../core/servers/deploy/install/upgrade-to-configuration-manager.md) tematu.  

6.  **Uaktualnij klientów.** Aby uaktualnić klientów, skorzystaj z informacji w [uaktualnianie klientów komputerów z systemem Windows w programie System Center Configuration Manager](../../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md).  

    -   To spowoduje uaktualnienie klientów bezpośrednio z programu Microsoft System Center 2012 Configuration Manager do zaktualizowanej wersji zainstalowanej w lokacji głównej.  

    Po wykonaniu tego kroku klienci zostaną uaktualnieni do wersji 1610 bez wcześniejszego uaktualnienia do wersji 1606.
