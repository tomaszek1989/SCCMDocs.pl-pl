---
title: "Wymagania wstępne dotyczące zarządzania energią | Dokumentacja firmy Microsoft"
description: "Pobierz wymagania wstępne dotyczące zarządzania zużyciem energii w programie System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9c062f13-3c1f-4621-9cae-de0e322aa03f
caps.latest.revision: 4
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: fc392e4440e84614f92218e9c7a09ec1c2c64f53
ms.openlocfilehash: 711ef491899846b86bfed0355ac7fd0f9d509c4f
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="prerequisites-for-power-management-in-system-center-configuration-manager"></a>Wymagania wstępne dotyczące zarządzania zużyciem energii w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Zarządzanie energią w programie System Center Configuration Manager ma zależności zewnętrzne i zależności w obrębie produktu.  

## <a name="dependencies-external-to-configuration-manager"></a>Zależności poza programem Configuration Manager  
 Poniższa tabela zawiera listę zależności zewnętrznych do programu Configuration Manager za pomocą zarządzania energią.  

|Zależność|Więcej informacji|  
|----------------|----------------------|  
|Komputery klienckie muszą mieć możliwość obsługi wymaganych stanów zasilania|Aby korzystać ze wszystkich funkcji zarządzania energią, komputery klienckie muszą mieć możliwość obsługi akcji uśpienia, hibernacji, wychodzenia z trybu uśpienia i przebudzenia z hibernacji. Możesz użyć raportu **Możliwości zasilania** w celu określenia, czy komputery mogą obsługiwać te akcje. Aby uzyskać więcej informacji, zobacz [raportu możliwości](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md#BKMK_Capabilites) w temacie [monitora i planu na potrzeby zarządzania zużyciem energii w programie System Center Configuration Manager](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md).|  

## <a name="configuration-manager-dependencies"></a>Zależności programu Configuration Manager  
 Poniższa tabela zawiera listę zależności w programie Configuration Manager za pomocą zarządzania energią.  

|Zależność|Więcej informacji|  
|----------------|----------------------|  
|Zarządzanie energią musi zostać włączone, aby można było tworzyć i monitorować plany zasilania.|Informacje dotyczące sposobu włączania i konfigurowania zarządzania zasilaniem, zobacz [Konfigurowanie zarządzania zużyciem energii w programie System Center Configuration Manager](../../../../core/clients/manage/power/configuring-power-management.md).|  
|Punkt usług raportowania|Aby wyświetlać raporty zarządzania energią, musisz skonfigurować punkt usług raportowania. Aby uzyskać więcej informacji, zobacz [Raportowanie w programie System Center Configuration Manager](../../../../core/servers/manage/reporting.md).|  

