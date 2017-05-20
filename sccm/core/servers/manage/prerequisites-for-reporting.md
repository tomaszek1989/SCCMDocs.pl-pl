---
title: "Wymagania wstępne dotyczące raportowania | Dokumentacja firmy Microsoft"
description: "Zrozumienie różnych zależności, które wpłynąć na korzystanie z raportowania w programie System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 9cc508a5-5023-4833-b776-ae9a6971138f
caps.latest.revision: 5
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 70034213442f4c3d5a28ab65c2ceb51aa64320ad
ms.openlocfilehash: 2e624eb2ea061a4eb7d92365410fada335640224
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="prerequisites-for-reporting-in-system-center-configuration-manager"></a>Wymagania wstępne dotyczące raportowania w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Raportowanie w programie System Center Configuration Manager ma zależności zewnętrzne i zależności w obrębie produktu.  

## <a name="dependencies-external-to-configuration-manager"></a>Zależności poza programem Configuration Manager  
 Poniższa tabela zawiera listę zależności zewnętrznych dla raportowania.  

|Wymaganie wstępne|Więcej informacji|  
|------------------|----------------------|  
|SQL Server Reporting Services|Przed użyciem funkcji raportowania w programie Configuration Manager, należy zainstalować i skonfigurować program SQL Server Reporting Services.<br /><br /> Informacje i planowaniu i wdrażaniu usług Reporting Services w używanym środowisku znajdują się w sekcji [Reporting Services (Usługi Reporting Services)](http://go.microsoft.com/fwlink/p/?LinkId=212032) w podręczniku programu SQL Server 2008 dostępnym w trybie online.|  
|Zależności ról systemu lokacji dla komputerów, na których działa punkt usług raportowania.|[Obsługiwane konfiguracje dla programu System Center Configuration Manager](../../../core/plan-design/configs/supported-configurations.md)|  

## <a name="dependencies-internal-to-configuration-manager"></a>Zależności wewnętrzne w programie Configuration Manager  
 Poniższa tabela zawiera listę zależności raportowania w programie Configuration Manager.  

|Wymaganie wstępne|Więcej informacji|  
|------------------|----------------------|  
|Punkt usług raportowania|Przed użyciem funkcji raportowania w programie Configuration Manager należy skonfigurować rolę systemu lokacji punktu usług raportowania. Aby uzyskać więcej informacji o sposobie instalowania i konfigurowania punktu usług raportowania, zobacz [konfigurowanie raportowania w programie System Center Configuration Manager](../../../core/servers/manage/configuring-reporting.md).|  

## <a name="supported-sql-server-versions-for-the-reporting-services-point"></a>Wersje programu SQL Server obsługiwane przez punkt usług raportowania  
 Bazę danych usług Reporting Services można zainstalować na domyślnym lub nazwanym wystąpieniu 64-bitowej instalacji programu SQL Server. Wystąpienie programu SQL Server może być kolokowane z serwerem systemu lokacji lub na komputerze zdalnym.  

 Poniższa tabela zawiera listę wersji programu SQL Server obsługiwanych przez punkt usług raportowania.  

|Wersja programu SQL|Punkt usług raportowania|  
|------------------------|------------------------------|  
|SQL Server 2008 z dodatkiem SP2 i co najmniej aktualizacją zbiorczą 9<br /><br /> — Standardowe<br />-Enterprise<br />-Centrum danych|Tak|  
|SQL Server 2008 z dodatkiem SP3 i co najmniej aktualizacją zbiorczą 4<br /><br /> — Standardowe<br />-Enterprise<br />-Centrum danych|Tak|  
|SQL Server 2008 R2 z dodatkiem SP1 i co najmniej aktualizacją zbiorczą 6<br /><br /> — Standardowe<br />-Enterprise<br />-Centrum danych|Tak|  
|SQL Server 2008 R2 z dodatkiem SP2<br /><br /> — Standardowe<br />-Enterprise<br />-Centrum danych|Tak|  
|SQL Server Express 2008 R2 z dodatkiem SP1 i co najmniej aktualizacją zbiorczą 4|Nieobsługiwane|  
|SQL Server Express 2008 R2 z dodatkiem SP2|Nieobsługiwane|  
|SQL Server 2012 z co najmniej aktualizacją zbiorczą 2<br /><br /> — Standardowe<br />-Enterprise|Tak|  
|SQL Server 2012 z dodatkiem SP1 bez minimalnej wersji aktualizacji zbiorczej<br /><br /> — Standardowe<br />-Enterprise|Tak|  
|SQL Server 2014<br /><br /> — Standardowe<br />-Enterprise|Tak|
|SQL Server 2016<br /><br /> — Standardowe<br />-Enterprise|Tak|
|SQL Server 2016 z dodatkiem SP1<br /><br /> — Standardowe<br />-Enterprise|Tak|
## <a name="next-steps"></a>Następne kroki
[Operacje i Obsługa raportowania](operations-and-maintenance-for-reporting.md)

