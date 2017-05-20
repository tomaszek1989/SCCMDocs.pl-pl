---
title: Monitorowanie migracji | Dokumentacja firmy Microsoft
description: "Dowiedz się, jak używać konsoli programu Configuration Manager można monitorować postęp i Powodzenie zadań migracji."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fc731d3f-edd7-4049-b17b-653d6693a564
caps.latest.revision: 4
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5e3d3f4194b06442e34c10988a20fe9ca40ac5d7
ms.openlocfilehash: 896807ec2c4be2835094a27add59d4cc09e93add
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="planning-to-monitor-migration-activity-in-system-center-configuration-manager"></a>Planowanie monitorowania działania migracji w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Za pomocą programu System Center Configuration Manager można monitorować migrację w konsoli programu Configuration Manager, który łączy do hierarchii docelowej. W konsoli programu Configuration Manager w **Administracja** obszaru roboczego, można użyć **migracji** węzeł, aby monitorować postęp i Powodzenie zadań migracji. Można wyświetlić informacje podsumowujące dotyczące poszczególnych zadań migracji, który identyfikuje obiekty, które zostały zmigrowane, te obiekty, które nie zostały jeszcze zmigrowane oraz liczba obiektów wykluczonych z zadania migracji. Można również wyświetlić szczegółowe informacje o wszystkich problemach migracji.  

## <a name="view-migration-progress"></a>Wyświetl postęp migracji  
 Aby wyświetlić postęp zadania migracji, należy użyć dowolnego z następujących czynności:  

-   W **Administracja** obszaru roboczego w konsoli programu Configuration Manager, rozwiń węzeł **zadań migracji** węzła, wybierz zadanie migracji, a następnie wybierz **obiekty w zadaniu** kartę.  

-   Aby sprawdzić postęp migracji albo zidentyfikować wszelkie problemy, należy użyć plików dziennika programu Configuration Manager. Migration Manager to proces programu Configuration Manager, który śledzi akcje migracji i zapisuje je w pliku migmctrl.log w  **\&lt; Ścieżkainstalacyjna\>\\DZIENNIKI** folder na serwerze lokacji.  

    > [!NOTE]  
    >  Jeśli zadanie migracji nie powiedzie się, jak najszybciej sprawdzić szczegóły w pliku migmctrl.log. Wpisy dziennika migracji są stale dodawane do pliku i zastępuję starsze dane. Jeśli wpisy zostaną zastąpione, nie można określić, czy wszelkich problemów, które mogą wystąpić z obiektami migracji są związane z migracją. Aktywności migracji są rejestrowane na górze\-poziomu lokacji w hierarchii, niezależnie od lokacji, konsola programu Configuration Manager łączy się z podczas konfigurowania migracji.  

-   Użyj raportowania w programie Configuration Manager. Program Configuration Manager udostępnia wiele wbudowanych\-w formie raportów dla migracji, lub można edytować zgodnie z własnymi wymaganiami. Aby uzyskać więcej informacji o raportach programu Configuration Manager, zobacz [raportowania w programie System Center Configuration Manager](../../core/servers/manage/reporting.md).  

