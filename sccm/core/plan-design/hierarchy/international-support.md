---
title: "Obsługa międzynarodowych | Dokumentacja firmy Microsoft"
description: "Skonfiguruj System Center Configuration Manager do zapewnienia zgodności z konkretnymi wymogami międzynarodowymi."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 46dd9cb2-a812-4b6a-a747-b840f92fef8b
caps.latest.revision: 6
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 40e018084dd2703327ff653f962f488432b1ec98
ms.openlocfilehash: 3bab51be96445f766e8f5bbf54eee854e5d09cee
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="international-support-in-system-center-configuration-manager"></a>Obsługa wymagań międzynarodowych w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Poniższe sekcje zawierają szczegółowe informacje techniczne ułatwiające zapewnienia zgodności z konkretnymi wymogami międzynarodowymi programu System Center Configuration Manager.  

## <a name="gb18030-requirements"></a>Wymogi normy GB18030  
 Menedżer konfiguracji spełnia normy, które są zdefiniowane w GB18030, tak aby można było używać programu Configuration Manager w Chinach. Wdrożenie programu Configuration Manager wymagane są następujące konfiguracje, aby spełnić wymogi normy GB18030:  

-   Każdy komputer serwera lokacji i komputer serwera SQL jest używany z programem Configuration Manager muszą używać system operacyjny w Chińskiej.  

-   Każda baza danych lokacji i każde wystąpienie programu SQL Server w hierarchii musi używać takiego samego sortowania, jednego z dwóch poniższych:  

    -   Chinese_Simplified_Pinyin_100_CI_AI  

    -   Chinese_Simplified_Stroke_Order_100_CI_AI  

    > [!NOTE]  
    >  Te sortowania bazy danych są wyjątkiem wymagania, które zostały wymienione w [obsługę wersji programu SQL Server dla programu System Center Configuration Manager](../../../core/plan-design/configs/support-for-sql-server-versions.md).  

-   W folderze głównym woluminu systemowego każdego komputera serwera lokacji w hierarchii należy umieścić plik o nazwie **GB18030.SMS** . Ten plik nie zawiera żadnych danych i może być pustym plikiem tekstowym o nazwie zgodnej z tym wymogiem.  

