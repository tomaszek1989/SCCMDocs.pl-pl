---
title: Zarządzanie klientami w Internecie
titleSuffix: Configuration Manager
description: Więcej informacji na temat zarządzania klientami z brama zarządzania w chmurze i zarządzania klientami internetowymi w programie Configuration Manager.
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.assetid: c667d6af-80c4-485f-910c-896c0171fd00
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 6296a171f2ef225dbbf647eb5e53103650d60c11
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="manage-clients-on-the-internet-with-configuration-manager"></a>Zarządzanie klientami w Internecie z programu Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Zwykle w programie Configuration Manager większość zarządzanych komputerach i serwerach znajduje się fizycznie w tej samej sieci wewnętrznej jako serwery systemu lokacji, które wykonują funkcje zarządzania. Jednak można zarządzać klientami spoza sieci wewnętrznej, gdy są połączeni z Internetem. Ta możliwość nie wymaga klientom na łączenie się za pośrednictwem sieci VPN do osiągnięcia serwery systemu lokacji.

Configuration Manager udostępnia dwa sposoby zarządzania klientami podłączonej do Internetu:

-   Brama zarządzania w chmurze

-   Internetowe zarządzanie klientami


## <a name="cloud-management-gateway"></a>Brama zarządzania w chmurze

Brama chmury zarządzania umożliwia zarządzanie klientów internetowych. Korzysta ona z kombinacji usługi w chmurze Microsoft Azure i nowa rola systemu lokacji, który komunikuje się z tą usługą. Klienci internetowi Użyj usługi w chmurze do komunikowania się z lokalnym programem Configuration Manager.

#### <a name="advantages"></a>Zalety  

-   Nie wymagane inwestycje dodatkowej infrastruktury.  

-   Nie ujawnia infrastruktury lokalnej z Internetem.  

-   Chmury maszyn wirtualnych, które uruchamiania usługi pełni są zarządzane przez usługę Azure i wymagają nie obsługi.  

-   Łatwe i konfigurowana w konsoli programu Configuration Manager.  

#### <a name="disadvantages"></a>Wady  

-   W chmurze koszt subskrypcji.  

-   Zarządzanie danych wysłanych przez usługę w chmurze.  

Aby uzyskać więcej informacji, zobacz [planowanie brama zarządzania chmury](plan-cloud-management-gateway.md).  



## <a name="internet-based-client-management"></a>Internetowe zarządzanie klientami

Ta metoda polega na serwerach systemu lokacji internetowy których klienci komunikują się w celu zarządzania nim. Wymaga to klienci i serwery systemu lokacji, można skonfigurować dla internetowego zarządzania.

#### <a name="advantages"></a>Zalety  

-   Nie zależności usługi chmury.  

-   Bez dodatkowych kosztów skojarzonych z subskrypcji usługi w chmurze.  

-   Pełną kontrolę nad serwery i role świadczących usługę.  

#### <a name="disadvantages"></a>Wady  

-   Wymagają dodatkowej infrastruktury inwestycji.  

-   Koszty i kosztów operacyjnych dodatkowe infrastruktury.  

-   Infrastruktury musi mieć połączenie z Internetem.  

Aby uzyskać więcej informacji, zobacz [Plan zarządzania klientami internetowymi](plan-internet-based-client-management.md).  
