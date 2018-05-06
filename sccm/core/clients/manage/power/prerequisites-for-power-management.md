---
title: Wymagania wstępne dotyczące zarządzania energią
titleSuffix: Configuration Manager
description: Pobierz wymagania wstępne dotyczące zarządzania energią w programie System Center Configuration Manager.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 9c062f13-3c1f-4621-9cae-de0e322aa03f
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: c6630ef07c0b7947875ea2adac4e6612143aaee8
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="prerequisites-for-power-management-in-system-center-configuration-manager"></a>Wymagania wstępne dotyczące zarządzania energią w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Zarządzanie energią w programie System Center Configuration Manager istnieją zależności zewnętrzne i zależności w obrębie produktu.  

## <a name="dependencies-external-to-configuration-manager"></a>Zależności poza programem Configuration Manager  
 Poniższa tabela zawiera listę zależności zewnętrznych do programu Configuration Manager za pomocą zarządzania energią.  

|Zależność|Więcej informacji|  
|----------------|----------------------|  
|Komputery klienckie muszą mieć możliwość obsługi wymaganych stanów zasilania|Aby korzystać ze wszystkich funkcji zarządzania energią, komputery klienckie muszą mieć możliwość obsługi akcji uśpienia, hibernacji, wychodzenia z trybu uśpienia i przebudzenia z hibernacji. Możesz użyć raportu **Możliwości zasilania** w celu określenia, czy komputery mogą obsługiwać te akcje. Aby uzyskać więcej informacji, zobacz [raport możliwości zasilania](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md#BKMK_Capabilites) w temacie [jak monitorować i planować zarządzanie energią w programie System Center Configuration Manager](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md).|  

## <a name="configuration-manager-dependencies"></a>Zależności programu Configuration Manager  
 W poniższej tabeli przedstawiono zależności w programie Configuration Manager do zarządzania energią.  

|Zależność|Więcej informacji|  
|----------------|----------------------|  
|Zarządzanie energią musi zostać włączone, aby można było tworzyć i monitorować plany zasilania.|Aby uzyskać informacje dotyczące sposobu włączania i konfigurowania zarządzania energią, zobacz [Konfigurowanie zarządzania energią w programie System Center Configuration Manager](../../../../core/clients/manage/power/configuring-power-management.md).|  
|Punkt usług raportowania|Aby wyświetlać raporty zarządzania energią, musisz skonfigurować punkt usług raportowania. Aby uzyskać więcej informacji, zobacz [Raportowanie w programie System Center Configuration Manager](../../../../core/servers/manage/reporting.md).|  
