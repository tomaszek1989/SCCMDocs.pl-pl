---
title: Najlepsze rozwiązania w zakresie raportowania
titleSuffix: Configuration Manager
description: Przeczytaj niektóre przydatne porady dotyczące korzystania z możliwości raportowania programu System Center Configuration Manager.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 64f9d931-33f1-456f-a4e4-0ec077465bd0
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 87ed3a0591107695a1f418b38f2e3f5cb9168c63
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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
