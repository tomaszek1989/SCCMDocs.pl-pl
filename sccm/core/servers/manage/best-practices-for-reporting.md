---
title: "Najlepsze rozwiązania w zakresie raportowania | Dokumentacja firmy Microsoft"
description: "Przeczytaj wskazówek pomocnych przy użyciu funkcji raportowania programu System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 64f9d931-33f1-456f-a4e4-0ec077465bd0
caps.latest.revision: 4
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 10b1010ccbf3889c58c55b87e70b354559243c90
ms.openlocfilehash: 759258999f3eaa810803a6a7f856f00fe7771a9e
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="best-practices-for-reporting-in-system-center-configuration-manager"></a>Najlepsze rozwiązania w zakresie raportowania w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Użyj poniższych najlepszych rozwiązań do raportowania w programie System Center Configuration Manager:  

## <a name="for-best-performance-install-the-reporting-services-point-on-a-remote-site-system-server"></a>Aby uzyskać najlepszą wydajność, zainstaluj punkt usług raportowania na serwerze zdalnego systemu lokacji  
 Mimo że możesz zainstalować punkt usług raportowania na serwerze lokacji lub zdalnym systemie lokacji, w celu zwiększenia wydajności lepiej zainstalować go na serwerze zdalnego systemu lokacji.  

## <a name="optimize-sql-server-reporting-services-queries"></a>Zoptymalizuj kwerendy usług SQL Server Reporting Services  
 Zwykle wszelkie opóźnienia raportowania są związane z uruchamianiem kwerend i pobieraniem ich wyników. W przypadku programu Microsoft SQL Server kwerendy można zoptymalizować za pomocą takich narzędzi, jak Query Analyzer oraz Profiler.  

## <a name="schedule-report-subscription-processing-to-run-outside-standard-office-hours"></a>Planuj uruchamianie przetwarzania subskrypcji raportów poza standardowymi godzinami pracy  
 Jeśli to możliwe, należy zaplanować subskrypcji uruchamianie przetwarzania raportów poza standardowymi godzinami zminimalizować przetwarzania procesora CPU w Menedżerze konfiguracji serwera bazy danych lokacji. Takie rozwiązanie zwiększa również dostępność w przypadku odebrania nieoczekiwanych żądań raportów.  

## <a name="next-steps"></a>Następne kroki
[Konfigurowanie raportowania](configuring-reporting.md)

