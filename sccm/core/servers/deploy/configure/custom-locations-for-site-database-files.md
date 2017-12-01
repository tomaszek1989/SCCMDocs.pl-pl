---
title: Lokalizacje pliku bazy danych niestandardowych
titleSuffix: Configuration Manager
description: "Dowiedz się, jak określić niestandardowych lokalizacji plików bazy danych programu SQL Server."
ms.custom: na
ms.date: 10/06/2016
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 500a9aa6-68aa-44eb-bf49-350c1314a697
caps.latest.revision: "3"
author: mstewart
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 9eeb083f8602562941cd52abfbaa327c8bcbcdc2
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2017
---
# <a name="custom-locations-for-system-center-configuration-manager-site-database-files"></a>Pliki bazy danych lokacji lokalizacji niestandardowych dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

 System Center Configuration Manager obsługuje niestandardowe lokalizacje plików bazy danych programu SQL Server.  

> [!NOTE]  
>  Można określić innych niż domyślne lokalizacje plików nie jest dostępne podczas używania klastra programu SQL Server.  

 **Podczas instalacji** nowej lokacji głównej lub centralnej lokacji administracyjnej, możesz:  

-   **Określ z systemem innym niż domyślne lokalizacje plików bazy danych lokacji**: Instalator programu Configuration Manager utworzy bazę danych lokacji przy użyciu tych lokalizacji.  

-   **Określenie użycia wstępnie utworzonej bazy danych programu SQL Server, która używa niestandardowych lokalizacji plików**:  Instalator programu Configuration Manager, a następnie użyje wstępnie utworzonej bazy danych oraz jej wstępnie skonfigurowanych lokalizacji plików.  

**Po zakończeniu instalacji**, możesz zmienić lokalizację plików bazy danych lokacji. Wymaga to zatrzymania lokacji i edytować lokalizację plików w programie SQL Server:  

-   Na serwerze lokacji programu Configuration Manager, należy zatrzymać **SMS_Executive** usługi.  

-   Użyj dokumentację dla używanej wersji programu SQL Server dotyczącą jak przenieść bazę danych użytkownika. Na przykład, jeśli używasz programu SQL Server 2014, zobacz [przenoszenia baz danych użytkowników](https://technet.microsoft.com/library/ms345483\(v=sql.120\).aspx) w witrynie TechNet.  

-   Po zakończeniu przenoszenia pliku bazy danych należy ponownie uruchomić **SMS_Executive** usługi na serwerze lokacji programu Configuration Manager.  
