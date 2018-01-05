---
title: Planowanie migracji
titleSuffix: Configuration Manager
description: "Więcej informacji o lokacjach i hierarchiach przed migracją danych do hierarchii docelowej programu System Center Configuration Manager."
ms.custom: na
ms.date: 1/12/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b2bf493e-1e10-496f-a139-2646522703ed
caps.latest.revision: "7"
caps.handback.revision: "0"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 390211f13fb6bac6dab5b133744ec01ec589bc77
ms.sourcegitcommit: ca9d15dfb1c9eb47ee27ea9b5b39c9f8cdcc0748
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2018
---
# <a name="plan-for-migration-to-system-center-configuration-manager"></a>Planowanie migracji do programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Przed migracją danych do hierarchii docelowej programu System Center Configuration Manager, upewnij się, że czytelnik zna lokacji i hierarchii w programie Configuration Manager. Aby uzyskać więcej informacji o lokacjach i hierarchiach, zobacz [podstawowe informacje na temat programu System Center Configuration Manager](../../core/understand/fundamentals.md).  

 Należy zainstalować hierarchię programu System Center Configuration Manager, aby być hierarchii docelowej przed migracją danych z obsługiwanej hierarchii źródłowej.  

 Po zainstalowaniu hierarchii docelowej należy skonfigurować funkcje zarządzania i funkcje, które ma być używany w hierarchii docelowej przed przystąpieniem do migracji danych.  

 Ponadto może być konieczne planach pokrywanie hierarchią źródłową i hierarchię docelową. Na przykład można skonfigurować hierarchii źródłowej do używania tej samej lokalizacji lub granic sieciowych jako hierarchii docelowej, a następnie zainstalować nowych klientów do hierarchii docelowej i używać automatycznego przypisania lokacji. W tym scenariuszu ponieważ nowo zainstalowany klient programu Configuration Manager można wybrać lokację do przyłączenia z jednej hierarchii, klient może zostać nieprawidłowo przypisany do hierarchii źródłowej. W związku z tym należy zaplanować przypisanie każdego nowego klienta w hierarchii docelowej do określonej lokacji w tej hierarchii, zamiast używać automatycznego przypisania lokacji.  

 Aby uzyskać więcej informacji o przypisywaniu do lokacji, zobacz [uwagi dotyczące przypisywania klientów do lokacji](../../core/plan-design/hierarchy/interoperability-between-different-versions.md#BKMK_SupConfigSiteAssignment) w [współdziałanie różnych wersji programu System Center Configuration Manager](../../core/plan-design/hierarchy/interoperability-between-different-versions.md).  

## <a name="plan-topics"></a>Planowanie — tematy  
 Użyj poniższych tematach ułatwią planowanie sposobu migracji obsługiwanej hierarchii źródłowej do hierarchii docelowej programu System Center Configuration Manager:

-   [Wymagania wstępne dotyczące migracji w programie System Center Configuration Manager](../../core/migration/prerequisites-for-migration.md)  

-   [Listy kontrolne administratora dotyczące planowania programu System Center Configuration Manager migracji](../../core/migration/administrator-checklists-for-migration-planning.md)  

-   [Określanie, czy migrować dane do programu System Center Configuration Manager](../../core/migration/determine-whether-to-migrate-data.md)  

-   [Planowanie strategii hierarchii źródłowej w programie System Center Configuration Manager](../../core/migration/planning-a-source-hierarchy-strategy.md)  

-   [Listy kontrolne administratora dotyczące planowania programu System Center Configuration Manager migracji](../../core/migration/administrator-checklists-for-migration-planning.md)  

-   [Planowanie strategii migracji klientów w programie System Center Configuration Manager](../../core/migration/planning-a-client-migration-strategy.md)  

-   [Planowanie strategii migracji wdrożenia zawartości w programie System Center Configuration Manager](../../core/migration/planning-a-content-deployment-migration-strategy.md)  

-   [Planowanie migracji obiektów programu Configuration Manager do programu System Center Configuration Manager](../../core/migration/planning-for-the-migration-of-objects.md)  

-   [Planowanie monitorowania działania migracji w programie System Center Configuration Manager](../../core/migration/planning-to-monitor-migration-activity.md)  

-   [Planowanie kończenia migracji w programie System Center Configuration Manager](../../core/migration/planning-to-complete-migration.md)  
