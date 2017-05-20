---
title: Planowanie migracji | Dokumentacja firmy Microsoft
description: "Dowiedz się więcej o lokacjach i hierarchiach przed migracją danych do hierarchii docelowej programu System Center Configuration Manager."
ms.custom: na
ms.date: 1/12/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b2bf493e-1e10-496f-a139-2646522703ed
caps.latest.revision: 7
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: a2405bc04889bd6ae46069fe447228149bbaf468
ms.openlocfilehash: fffef1e95e1dfa03971f140a6e5a7fff9bfe5e27
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="plan-for-migration-to-system-center-configuration-manager"></a>Planowanie migracji programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Przed migracją danych do hierarchii docelowej programu System Center Configuration Manager, upewnij się, że znasz lokacji i hierarchii w programie Configuration Manager. Aby uzyskać więcej informacji o lokacjach i hierarchiach, zobacz [podstawy programu System Center Configuration Manager](../../core/understand/fundamentals.md).  

 Należy zainstalować hierarchii programu System Center Configuration Manager do hierarchii docelowej przed migracją danych z obsługiwanej hierarchii źródłowej.  

 Po zainstalowaniu hierarchii docelowej należy skonfigurować funkcje zarządzania i funkcje, które chcesz użyć w hierarchii docelowej przed rozpoczęciem migracji danych.  

 Ponadto należy uwzględnić w planach pokrywanie się hierarchii źródłowej i hierarchię docelową. Na przykład można skonfigurować hierarchii źródłowej do użycia tej samej lokalizacji lub granic sieciowych co w hierarchii docelowej, a następnie zainstalować nowych klientów do hierarchii docelowej i używać automatycznego przypisania lokacji. W tym scenariuszu ponieważ nowo zainstalowany klient programu Configuration Manager można wybrać lokację do przyłączenia z drugiej hierarchii, klient może zostać nieprawidłowo przypisany do hierarchii źródłowej. Dlatego też należy zaplanować przypisanie każdego nowego klienta w hierarchii docelowej do określonej lokacji w tej hierarchii, zamiast używać automatycznego przypisania lokacji.  

 Aby uzyskać więcej informacji o przypisywaniu do lokacji, zobacz [uwagi dotyczące przypisywania klientów do lokacji](../../core/plan-design/hierarchy/interoperability-between-different-versions.md#BKMK_SupConfigSiteAssignment) w [współdziałanie różnych wersji programu System Center Configuration Manager](../../core/plan-design/hierarchy/interoperability-between-different-versions.md).  

## <a name="plan-topics"></a>Tematy dotyczące planowania  
 Użyj poniższych tematach ułatwiają planowanie sposobu migracji obsługiwanej hierarchii źródłowej do hierarchii docelowej programu System Center Configuration Manager:

-   [Wymagania wstępne dotyczące migracji w programie System Center Configuration Manager](../../core/migration/prerequisites-for-migration.md)  

-   [Listy kontrolne administratora dotyczące planowania w programie System Center Configuration Manager migracji](../../core/migration/administrator-checklists-for-migration-planning.md)  

-   [Określanie, czy migracja danych programu System Center Configuration Manager](../../core/migration/determine-whether-to-migrate-data.md)  

-   [Planowanie strategii hierarchii źródłowej w programie System Center Configuration Manager](../../core/migration/planning-a-source-hierarchy-strategy.md)  

-   [Listy kontrolne administratora dotyczące planowania w programie System Center Configuration Manager migracji](../../core/migration/administrator-checklists-for-migration-planning.md)  

-   [Planowanie strategii migracji klienta w programie System Center Configuration Manager](../../core/migration/planning-a-client-migration-strategy.md)  

-   [Planowanie strategii migracji wdrożenia zawartości w programie System Center Configuration Manager](../../core/migration/planning-a-content-deployment-migration-strategy.md)  

-   [Planowanie migracji obiektów programu Configuration Manager programu System Center Configuration Manager](../../core/migration/planning-for-the-migration-of-objects.md)  

-   [Planowanie monitorowania działania migracji w programie System Center Configuration Manager](../../core/migration/planning-to-monitor-migration-activity.md)  

-   [Planowanie ukończenia migracji w programie System Center Configuration Manager](../../core/migration/planning-to-complete-migration.md)  

