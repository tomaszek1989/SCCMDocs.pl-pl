---
title: Wymagania wstępne dotyczące zdalnego sterowania
titleSuffix: Configuration Manager
description: Pobierz wymagania wstępne dotyczące zdalnego sterowania w programie System Center Configuration Manager.
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: c1b2057e-b74f-43fa-a293-763a8f866d3d
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 117ad9a087151db51c4cf33112ab662f53b9134e
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="prerequisites-for-remote-control-in-system-center-configuration-manager"></a>Wymagania wstępne dotyczące zdalnego sterowania w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Zdalnego sterowania w programie System Center Configuration Manager istnieją zależności zewnętrzne i zależności w ramach produktu.  

## <a name="dependencies-external-to-configuration-manager"></a>Zależności poza programem Configuration Manager  

|Zależność|Więcej informacji|  
|----------------|----------------------|  
|Sterownik karty wideo komputera|Aby zapewnić optymalną wydajność zdalnego sterowania, upewnij się, że na komputerach klienckich został zainstalowany najnowszy sterownik wideo.|  

 Urządzenia z systemem Windows Embedded, Windows Embedded dla punktu usługi oraz Windows Fundamentals dla starszych komputerów nie obsługują podglądu zdalnego sterowania, ale obsługują klienta zdalnego sterowania.  

 Zdalne sterowanie programu Configuration Manager nie może służyć do zdalnego zarządzania klientami, które są uruchamiane Systems Management Server 2003 lub programu Configuration Manager 2007.  

> [!NOTE]  
>  W przypadku zdalnego sterowania usługi systemu Windows nie są wymagane jako zależności zewnętrzne.  

### <a name="supported-operating-systems-for-the-remote-control-viewer"></a>Obsługiwane systemy operacyjne podglądu zdalnego sterowania  
Przeglądarka zdalnego sterowania jest obsługiwane we wszystkich systemach operacyjnych obsługiwanych przez konsolę programu Configuration Manager. Aby uzyskać informacje, zobacz [dla konsoli programu System Center Configuration Manager — obsługiwane konfiguracje](../../../../core/plan-design/configs/supported-operating-systems-consoles.md).   

## <a name="configuration-manager-dependencies"></a>Zależności programu Configuration Manager  

|Zależność|Więcej informacji|  
|----------------|----------------------|  
|Zdalne sterowanie musi zostać włączone dla klientów|Domyślnie zdalne sterowanie nie jest włączona podczas instalowania programu Configuration Manager. Aby uzyskać informacje dotyczące sposobu włączania i konfigurowania zdalnego sterowania, zobacz [Konfigurowanie zdalnego sterowania w programie System Center Configuration Manager](../../../../core/clients/manage/remote-control/configuring-remote-control.md).|  
|Punkt usług raportowania|Przed rozpoczęciem raportowania dotyczącego zdalnego sterowania należy skonfigurować rolę systemu lokacji punktu usług raportowania. Aby uzyskać więcej informacji, zobacz [Raportowanie w programie System Center Configuration Manager](../../../../core/servers/manage/reporting.md).|  
|Uprawnienia zabezpieczeń do zarządzania zdalnym sterowaniem|Dostęp do zasobów w kolekcji i zainicjować sesję zdalnego sterowania z konsoli programu Configuration Manager: **Odczyt**, **Odczytaj zasób**, i **zdalnego sterowania** uprawnienie **kolekcji** obiektu.<br /><br /> **Zdalny Operator narzędzi** roli zabezpieczeń obejmuje uprawnienia wymagane do zarządzania zdalnego sterowania w programie Configuration Manager.<br /><br /> Aby uzyskać więcej informacji, zobacz [Konfigurowanie administracji opartej na rolach dla programu System Center Configuration Manager](../../../../core/servers/deploy/configure/configure-role-based-administration.md).<br /><br /> Ponadto dopuszczone podglądy musi mieć uprawnienie do korzystać ze zdalnego sterowania przez dodanie tych użytkowników do **dopuszczone podglądy zdalnego sterowania i pomocy zdalnej** na liście **narzędzia zdalnej** ustawień klienta.
