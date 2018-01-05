---
title: "Migracja monitorów"
titleSuffix: Configuration Manager
description: "Dowiedz się, jak za pomocą konsoli programu Configuration Manager monitoruje postęp i Powodzenie zadań migracji."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fc731d3f-edd7-4049-b17b-653d6693a564
caps.latest.revision: "4"
caps.handback.revision: "0"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: ee5c65b41678bd5c86170f2d7a20b1d2fc569226
ms.sourcegitcommit: ca9d15dfb1c9eb47ee27ea9b5b39c9f8cdcc0748
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2018
---
# <a name="planning-to-monitor-migration-activity-in-system-center-configuration-manager"></a>Planowanie monitorowania działania migracji w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Z programem System Center Configuration Manager można monitorować migrację w konsoli programu Configuration Manager, który łączy do hierarchii docelowej. W konsoli programu Configuration Manager w **administracji** obszaru roboczego, można użyć **migracji** węzeł, aby monitorować postęp i Powodzenie zadań migracji. Można wyświetlić informacje podsumowujące dotyczące poszczególnych zadań migracji, który określa obiekty, które zostały zmigrowane, te obiekty, które nie zostały jeszcze zmigrowane, a liczba obiektów wykluczonych z zadania migracji. Widoczne będzie także szczegółowe informacje o wszystkich problemach migracji.  

## <a name="view-migration-progress"></a>Wyświetl postęp migracji  
 Aby wyświetlić postęp zadania migracji, należy użyć dowolnego z następujących czynności:  

-   W **administracji** obszaru roboczego w konsoli programu Configuration Manager, rozwiń węzeł **zadań migracji** węzła, wybierz zadanie migracji, a następnie wybierz **obiekty w zadaniu** kartę.  

-   Użyj plików dziennika programu Configuration Manager, aby sprawdzić postęp migracji albo zidentyfikować wszelkie problemy. Migration Manager to proces programu Configuration Manager, który śledzi akcje migracji i zapisuje je w pliku migmctrl.log w  **\&lt; Ścieżka_instalacji\>\\DZIENNIKI** folderu na serwerze lokacji.  

    > [!NOTE]  
    >  Jeśli zadanie migracji nie powiedzie się, sprawdź szczegóły w pliku migmctrl.log tak szybko, jak to możliwe. Wpisy dziennika migracji są stale dodawane do pliku i zastępuję starsze dane. Jeśli wpisy zostaną zastąpione, nie można ustalić, czy wszelkie problemy, które mogą wystąpić z migrowanych obiektów dotyczą problemy przy migracji. Aktywności migracji są rejestrowane w górnej\-poziomu lokacji w hierarchii, niezależnie od lokacji konsoli programu Configuration Manager łączy się z podczas konfigurowania migracji.  

-   Użyj raportowania w programie Configuration Manager. Configuration Manager udostępnia wiele wbudowanych\-raporty dotyczące migracji, lub można edytować tych raportów zgodnie z własnymi wymaganiami. Aby uzyskać więcej informacji o raportach programu Configuration Manager, zobacz [raportowania w programie System Center Configuration Manager](../../core/servers/manage/reporting.md).  
