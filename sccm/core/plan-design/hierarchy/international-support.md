---
title: Obsługa wymagań międzynarodowych
titleSuffix: Configuration Manager
description: Skonfiguruj System Center Configuration Manager w celu zachowania zgodności z konkretnymi wymogami międzynarodowymi.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 46dd9cb2-a812-4b6a-a747-b840f92fef8b
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: bce6abd57cd50ff19339c29b97bda165109b79b1
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="international-support-in-system-center-configuration-manager"></a>Obsługa wymagań międzynarodowych w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Poniższe sekcje zawierają szczegółowe informacje techniczne w celu zapewnienia zgodności z konkretnymi wymogami międzynarodowymi System Center Configuration Manager.  

## <a name="gb18030-requirements"></a>Wymogi normy GB18030  
 Menedżer konfiguracji spełnia wymogi zdefiniowane w GB18030 tak, aby można było używać programu Configuration Manager w Chinach. Wdrożenia programu Configuration Manager musi mieć następującą konfigurację, aby spełnić wymogi normy GB18030:  

-   Każdy komputer serwera lokacji i programu SQL Server używany komputer z programem Configuration Manager muszą używać system operacyjny w chińskiej wersji językowej.  

-   Każda baza danych lokacji i każde wystąpienie programu SQL Server w hierarchii musi używać takiego samego sortowania, jednego z dwóch poniższych:  

    -   Chinese_Simplified_Pinyin_100_CI_AI  

    -   Chinese_Simplified_Stroke_Order_100_CI_AI  

    > [!NOTE]  
    >  Te sortowania bazy danych są wyjątkiem od wymagań, które są wymienione wśród [pomocy technicznej dla wersji programu SQL Server dla programu System Center Configuration Manager](../../../core/plan-design/configs/support-for-sql-server-versions.md).  

-   W folderze głównym woluminu systemowego każdego komputera serwera lokacji w hierarchii należy umieścić plik o nazwie **GB18030.SMS** . Ten plik nie zawiera żadnych danych i może być pustym plikiem tekstowym o nazwie zgodnej z tym wymogiem.  
