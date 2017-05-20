---
title: Planowanie bazy danych lokacji | Dokumentacja firmy Microsoft
description: "Podczas planowania hierarchii programu System Center Configuration Manager, należy rozważyć bazy danych lokacji i roli serwera bazy danych lokacji."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 104fb4cc-6e83-40a3-8e6b-ac909fb9ec7d
caps.latest.revision: 5
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: cec63ed7781e236dbf5e8baa0a468193ea794339
ms.openlocfilehash: d4efe1f013dbb74efca79cd27f7248fc085c7424
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="plan-for-the-site-database-for-system-center-configuration-manager"></a>Publikowanie bazy danych lokacji dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Serwer bazy danych lokacji to komputer, który działa obsługiwana wersja programu Microsoft SQL Server. Program SQL Server jest używany do przechowywania informacji o lokacji programu Configuration Manager. Każda lokacja w hierarchii programu Configuration Manager zawiera bazę danych lokacji i serwera, który jest przypisany do roli serwera bazy danych lokacji.  

-   Dla witryny administracji centralnej i lokacje główne SQL Server można zainstalować na serwerze lokacji lub SQL Server można zainstalować na innym komputerze niż serwer lokacji.  

-   W przypadku lokacji dodatkowych można użyć programu SQL Server Express zamiast z pełnej instalacji programu SQL Server. Serwer bazy danych musi, jednak można uruchomić na serwerze lokacji dodatkowej.  

Następujące konfiguracje programu SQL Server może służyć do obsługi bazy danych lokacji:  

-   Domyślne wystąpienie programu SQL Server  

-   Nazwane wystąpienie na jednym komputerze z uruchomionym programem SQL Server  

-   Nazwane wystąpienie w ramach klastrowanego wystąpienia programu SQL Server  

-   Grupy dostępności AlwaysOn programu SQL Server (począwszy od wersji 1602 programu System Center Configuration Manager)


Do obsługi bazy danych lokacji, programu SQL Server musi spełniać wymagania wyszczególnione w [obsługę wersji programu SQL Server dla programu System Center Configuration Manager](../../../core/plan-design/configs/support-for-sql-server-versions.md).  



## <a name="remote-database-server-location-considerations"></a>Zagadnienia dotyczące lokalizacji serwera zdalnej bazy danych  

Jeśli używasz komputera serwera zdalnej bazy danych, upewnij się, że pośredniczące połączenie sieciowe jest połączenie sieciowe o wysokiej dostępności, wysokiej przepustowości. Serwer lokacji i niektóre role systemu lokacji stale komunikują się ze zdalnym serwerem, który jest hostem bazy danych lokacji.

-   Przepustowość wymagana do komunikacji z serwerem bazy danych zależy od kombinacji wiele różnych konfiguracji lokacji i klientów. W związku z tym rzeczywiste przepustowość wymagana odpowiednio nieprzewidywalny.  

-   Każdy komputer z uruchomionym dostawcą program SMS i nawiązujący połączenie z bazą danych lokacji zwiększa wymagania dotyczące przepustowości sieci.  

-   Komputerze, na którym działa program SQL Server musi znajdować się w domenie mającej dwukierunkową relację zaufania z serwerem lokacji a wszystkimi komputerami z uruchomionym dostawcą programu SMS.  

-   Na serwerze bazy danych lokacji nie można używać klastrowanego wystąpienia programu SQL Server, gdy baza danych lokacji jest kolokowana z serwerem lokacji.  


Zwykle serwer systemu lokacji obsługuje role systemu lokacji z tylko jednej lokacji programu Configuration Manager. Jednak służy innych wystąpień programu SQL Server na klastrowanych lub nieklastrowanych serwerach z programem SQL Server do obsługi bazy danych z różnych lokacji programu Configuration Manager. Aby obsługiwać bazy danych za pośrednictwem różnych lokacji, każde wystąpienie programu SQL Server należy skonfigurować, aby komunikowało się przy użyciu unikatowych portów.  

