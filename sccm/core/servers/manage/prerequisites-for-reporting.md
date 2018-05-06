---
title: Wymagania wstępne dotyczące raportowania
titleSuffix: Configuration Manager
description: Zrozumienie różnych zależności, które mają wpływ na korzystanie z raportowania w programie System Center Configuration Manager.
ms.date: 01/29/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 9cc508a5-5023-4833-b776-ae9a6971138f
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: c9e20321a794f093dbb494034fe256c26be31480
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="prerequisites-for-reporting-in-system-center-configuration-manager"></a>Wymagania wstępne dotyczące raportowania w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Raportowanie w programie System Center Configuration Manager istnieją zależności zewnętrzne i zależności w obrębie produktu.  

## <a name="dependencies-external-to-configuration-manager"></a>Zależności poza programem Configuration Manager  
 Poniższa tabela zawiera listę zależności zewnętrznych dla raportowania.  

|Wymaganie wstępne|Więcej informacji|  
|------------------|----------------------|  
|SQL Server Reporting Services|Przed użyciem funkcji raportowania w programie Configuration Manager, należy zainstalować i skonfigurować program SQL Server Reporting Services.<br /><br /> Informacje i planowaniu i wdrażaniu usług Reporting Services w używanym środowisku znajdują się w sekcji [Reporting Services (Usługi Reporting Services)](http://go.microsoft.com/fwlink/p/?LinkId=212032) w podręczniku programu SQL Server 2008 dostępnym w trybie online.|  
|Zależności ról systemu lokacji dla komputerów, na których działa punkt usług raportowania.|[Obsługiwane konfiguracje programu System Center Configuration Manager](../../../core/plan-design/configs/supported-configurations.md)|  

## <a name="dependencies-internal-to-configuration-manager"></a>Zależności wewnętrzne w programie Configuration Manager  
 Poniższa tabela zawiera listę zależności dla raportowania w programie Configuration Manager.  

|Wymaganie wstępne|Więcej informacji|  
|------------------|----------------------|  
|Punkt usług raportowania|Przed użyciem funkcji raportowania w programie Configuration Manager, należy skonfigurować rolę systemu lokacji punktu usług raportowania. Aby uzyskać więcej informacji o sposobie instalowania i konfigurowania punktu usług raportowania, zobacz [konfigurowanie raportowania w programie System Center Configuration Manager](../../../core/servers/manage/configuring-reporting.md).|  

## <a name="supported-sql-server-versions-for-the-reporting-services-point"></a>Wersje programu SQL Server obsługiwane przez punkt usług raportowania  
 Bazę danych usług Reporting Services można zainstalować na domyślnym lub nazwanym wystąpieniu 64-bitowej instalacji programu SQL Server. Wystąpienie programu SQL Server może być kolokowane z serwerem systemu lokacji lub na komputerze zdalnym.  

 Poniższa tabela zawiera listę wersji programu SQL Server obsługiwanych przez punkt usług raportowania.  

|Wersja programu SQL|Punkt usług raportowania|  
|------------------------|------------------------------|
|SQL Server 2017 z co najmniej aktualizacją zbiorczą 2<br /><br /> -Standard<br />-Enterprise|Tak, począwszy od 1710 wersji programu Configuration Manager|  
|SQL Server 2016 z dodatkiem SP1<br /><br /> -Standard<br />-Enterprise|Tak| 
|SQL Server 2016<br /><br /> -Standard<br />-Enterprise|Tak|
|SQL Server 2014 z dodatkiem SP2<br /><br /> -Standard<br />-Enterprise|Tak|
|SQL Server 2014 z dodatkiem SP1<br /><br /> -Standard<br />-Enterprise|Tak|
|SQL Server 2012 z dodatkiem SP4 <br /><br /> -Standard<br />-Enterprise|Tak|  
|SQL Server 2012 z dodatkiem SP3 <br /><br /> -Standard<br />-Enterprise|Tak|  
|SQL Server 2008 R2 z dodatkiem SP3<br /><br /> -Standard<br />-Enterprise<br />-Centrum danych|Tak, obsługiwane wersje programu Configuration Manager przed 1702.|  
|Program SQL Server Express 2008 R2 z dodatkiem SP3|Nieobsługiwane| 




## <a name="next-steps"></a>Następne kroki
[Operacje i obsługa raportowania](operations-and-maintenance-for-reporting.md)
