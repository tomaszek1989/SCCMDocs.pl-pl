---
title: "Lokalizacje plików bazy danych niestandardowych | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak określić niestandardowe lokalizacje plików bazy danych programu SQL Server."
ms.custom: na
ms.date: 10/06/2016
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 500a9aa6-68aa-44eb-bf49-350c1314a697
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5e5155aa8c03b7e0c200d083024c8fa386f97aa7
ms.openlocfilehash: cfac2c03c1b71b40c68d8acd5fbd96c5e98caaa9
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="custom-locations-for-system-center-configuration-manager-site-database-files"></a>Pliki bazy danych lokacji lokalizacji niestandardowych dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

 System Center Configuration Manager obsługuje niestandardowe lokalizacje plików bazy danych programu SQL Server.  

> [!NOTE]  
>  Można określić innych niż domyślne lokalizacje plików nie jest dostępne podczas używania klastra programu SQL Server.  

 **Podczas instalacji** nowej lokacji głównej lub centralnej lokacji administracyjnej, można wykonywać następujące czynności:  

-   **Określ inny niż domyślne lokalizacje plików bazy danych lokacji**: Instalator programu Configuration Manager tworzy następnie bazy danych lokacji przy użyciu tych lokalizacjach.  

-   **Określenie użycia wstępnie utworzonej bazy danych programu SQL Server, który używa niestandardowych lokalizacji plików**:  Następnie Instalator programu Configuration Manager używa tej wstępnie utworzonej bazy danych i jego lokalizacji plików wstępnie skonfigurowane.  

**Po zakończeniu instalacji**, można zmienić lokalizację plików bazy danych lokacji. Wymaga to Zatrzymaj witrynę i edytować lokalizację plików w programie SQL Server:  

-   Na serwerze lokacji programu Configuration Manager, należy zatrzymać **SMS_Executive** usługi.  

-   Korzystając z dokumentacji dla używanej wersji programu SQL Server do przeprowadzenia Cię o tym, jak przenieść bazę danych użytkownika. Na przykład, jeśli używasz programu SQL Server 2014, zobacz [przenoszenia baz danych użytkowników](https://technet.microsoft.com/library/ms345483\(v=sql.120\).aspx) w witrynie TechNet.  

-   Po przeniesieniu bazy danych plików, uruchom ponownie **SMS_Executive** usługi na serwerze lokacji programu Configuration Manager.  

