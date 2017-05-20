---
title: "Wymagania wstępne zdalnego sterowania | Dokumentacja firmy Microsoft"
description: "Pobierz wstępnie wymagane składniki do zdalnego sterowania w programie System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c1b2057e-b74f-43fa-a293-763a8f866d3d
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: e08bca886dfc0730ab45ab899754394ae61335e3
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="prerequisites-for-remote-control-in-system-center-configuration-manager"></a>Wymagania wstępne dotyczące zdalnego sterowania w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Zdalne sterowanie w programie System Center Configuration Manager ma zależności zewnętrzne i zależności w produkcie.  

## <a name="dependencies-external-to-configuration-manager"></a>Zależności poza programem Configuration Manager  

|Zależność|Więcej informacji|  
|----------------|----------------------|  
|Sterownik karty wideo komputera|Aby zapewnić optymalną wydajność zdalnego sterowania, upewnij się, że na komputerach klienckich został zainstalowany najnowszy sterownik wideo.|  

 Urządzenia z systemem Windows Embedded, Windows Embedded dla punktu usługi oraz Windows Fundamentals dla starszych komputerów nie obsługują podglądu zdalnego sterowania, ale obsługują klienta zdalnego sterowania.  

 Zdalne sterowanie programu Configuration Manager nie można użyć do zdalnego administrowania komputerów klienckich z systemem Systems Management Server 2003 lub Configuration Manager 2007.  

> [!NOTE]  
>  W przypadku zdalnego sterowania usługi systemu Windows nie są wymagane jako zależności zewnętrzne.  

### <a name="supported-operating-systems-for-the-remote-control-viewer"></a>Obsługiwane systemy operacyjne podglądu zdalnego sterowania  
 W poniższej tabeli znajdują się informacje dotyczące systemów operacyjnych obsługiwanych w przypadku podglądu zdalnego sterowania. Informacje o klienckich obsługiwanych systemów operacyjnych, zobacz [obsługiwanych konfiguracji programu System Center Configuration Manager](../../../../core/plan-design/configs/supported-configurations.md).  

|System operacyjny|Obsługa poglądu|Więcej informacji|  
|----------------------|--------------------|----------------------|  
|Windows XP (wersja 32-bitowa)|Tak|Aby uruchomić podglądu zdalnego sterowania w tym systemie operacyjnym, należy najpierw pobrać i zainstalować [Aktualizacja klienta połączenia pulpitu zdalnego (RDC) 7.0 (KB969084)](https://www.microsoft.com/en-us/download/details.aspx?id=12767) z Microsoft Download Center.|  
|Windows XP (wersja 64-bitowa)|Nie|Brak dodatkowych informacji.|  
|Windows Vista (wersja 32-bitowa)|Tak|Aby uruchomić podglądu zdalnego sterowania w tym systemie operacyjnym, należy najpierw pobrać i zainstalować [Aktualizacja klienta połączenia pulpitu zdalnego (RDC) 7.0 (KB969084)](https://www.microsoft.com/en-us/download/details.aspx?id=12767) z Microsoft Download Center.|  
|Windows Vista (wersja 64-bitowa)|Tak|Aby uruchomić podglądu zdalnego sterowania w tym systemie operacyjnym, należy najpierw pobrać i zainstalować [Aktualizacja klienta połączenia pulpitu zdalnego (RDC) 7.0 (KB969084)](https://www.microsoft.com/en-us/download/details.aspx?id=12767) z Microsoft Download Center.|  
|Windows 7 (wersja 32-bitowa)|Tak|Brak dodatkowych informacji.|  
|Windows 7 (wersja 64-bitowa)|Tak|Brak dodatkowych informacji.|  
|Windows Server 2003 (wersja 32-bitowa)|Nie|Brak dodatkowych informacji.|  
|Windows Server 2003 (wersja 64-bitowa)|Nie|Brak dodatkowych informacji.|  
|Windows Server 2008 (wersja 32-bitowa)|Nie|Brak dodatkowych informacji.|  
|Windows Server 2008 (wersja 64-bitowa)|Nie|Brak dodatkowych informacji.|  
|Windows Server 2008 R2 (wersja 64-bitowa)|Tak|Brak dodatkowych informacji.|  

## <a name="configuration-manager-dependencies"></a>Zależności programu Configuration Manager  

|Zależność|Więcej informacji|  
|----------------|----------------------|  
|Zdalne sterowanie musi zostać włączone dla klientów|Domyślnie zdalnego sterowania nie jest włączane podczas instalowania programu Configuration Manager. Aby dowiedzieć się, jak włączyć i skonfigurować zdalne sterowanie, zobacz [Konfigurowanie zdalnego sterowania w programie System Center Configuration Manager](../../../../core/clients/manage/remote-control/configuring-remote-control.md).|  
|Punkt usług raportowania|Przed rozpoczęciem raportowania dotyczącego zdalnego sterowania należy skonfigurować rolę systemu lokacji punktu usług raportowania. Aby uzyskać więcej informacji, zobacz [Raportowanie w programie System Center Configuration Manager](../../../../core/servers/manage/reporting.md).|  
|Uprawnienia zabezpieczeń do zarządzania zdalnym sterowaniem|Dostęp do zasobów w kolekcji i zainicjować sesji zdalnego sterowania z konsoli programu Configuration Manager: **Kontrolować AMT**, **odczytu**, **Odczytaj zasób**, i **zdalnego sterowania** uprawnienia dla **kolekcji** obiektu.<br /><br /> **Zdalny Operator narzędzi** te uprawnienia, które są wymagane do zarządzania zdalnego sterowania w programie Configuration Manager obejmuje rola zabezpieczeń.<br /><br /> Aby uzyskać więcej informacji, zobacz [skonfigurowanie administracji opartej na rolach dla programu System Center Configuration Manager](../../../../core/servers/deploy/configure/configure-role-based-administration.md).<br /><br /> Ponadto musisz dodać użytkowników, którym chcesz nadać uprawnienia do korzystania z listy dozwolonych podglądów zdalnego sterowania i zdalnej pomocy dotyczącej zdalnego sterowania przy użyciu opcji **Dopuszczone podglądy zdalnego sterowania i pomocy zdalnej** w ustawieniach klienta **Narzędzia zdalne** .|  

