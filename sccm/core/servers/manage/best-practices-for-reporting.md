---
title: "Najlepsze rozwiązania w zakresie raportowania | Dokumentacja firmy Microsoft"
description: "Przeczytaj niektóre przydatne porady dotyczące korzystania z możliwości raportowania programu System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 64f9d931-33f1-456f-a4e4-0ec077465bd0
caps.latest.revision: "4"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 759258999f3eaa810803a6a7f856f00fe7771a9e
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="best-practices-for-reporting-in-system-center-configuration-manager"></a>Najlepsze rozwiązania w zakresie raportowania w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Do raportowania w programie System Center Configuration Manager, należy użyć następujących rozwiązań:  

## <a name="for-best-performance-install-the-reporting-services-point-on-a-remote-site-system-server"></a>Aby uzyskać najlepszą wydajność, zainstaluj punkt usług raportowania na serwerze zdalnego systemu lokacji  
 Mimo że możesz zainstalować punkt usług raportowania na serwerze lokacji lub zdalnym systemie lokacji, w celu zwiększenia wydajności lepiej zainstalować go na serwerze zdalnego systemu lokacji.  

## <a name="optimize-sql-server-reporting-services-queries"></a>Zoptymalizuj kwerendy usług SQL Server Reporting Services  
 Zwykle wszelkie opóźnienia raportowania są związane z uruchamianiem kwerend i pobieraniem ich wyników. W przypadku programu Microsoft SQL Server kwerendy można zoptymalizować za pomocą takich narzędzi, jak Query Analyzer oraz Profiler.  

## <a name="schedule-report-subscription-processing-to-run-outside-standard-office-hours"></a>Planuj uruchamianie przetwarzania subskrypcji raportów poza standardowymi godzinami pracy  
 Jeśli to możliwe, należy zaplanować przetwarzania subskrypcji raportów do uruchamiania poza standardowymi godzinami pracy, aby zminimalizować obciążenie Procesora w programie Configuration Manager z serwera bazy danych lokacji. Takie rozwiązanie zwiększa również dostępność w przypadku odebrania nieoczekiwanych żądań raportów.  

## <a name="next-steps"></a>Następne kroki
[Konfigurowanie raportowania](configuring-reporting.md)
