---
title: "Zarządzanie klientami w Internecie — programu Configuration Manager | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat zarządzania klientami z brama zarządzania w chmurze i zarządzania klientami internetowymi w programie Configuration Manager."
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.assetid: c667d6af-80c4-485f-910c-896c0171fd00
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 1b6752be448e1062c97a3225db4fa8af9f4832a6
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="manage-clients-on-the-internet-with-configuration-manager"></a>Zarządzanie klientami w Internecie z programu Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Zwykle w programie Configuration Manager większość komputerów i serwerów, które są zarządzane są fizycznie w tej samej wewnętrznej sieci prywatnej lub firmowych jako serwery systemu lokacji, które wykonują funkcje zarządzania. Można jednak zarządzać komputerami klienckimi spoza sieci firmowej, jeśli są one połączone z Internetem bez konieczności klientom na łączenie się za pośrednictwem wirtualnych sieci prywatnych dociera do lokacji serwery systemu.

Configuration Manager udostępnia dwa sposoby zarządzania klientami połączonych z Internetem:

-   Brama zarządzania w chmurze

-   Internetowe zarządzanie klientami

## <a name="cloud-management-gateway"></a>Brama zarządzania w chmurze

Począwszy od wersji 1610, programu Configuration Manager wprowadza brama zarządzania w chmurze. Ta nowa metoda umożliwia zarządzanie klientów internetowych przy użyciu kombinacji usługi w chmurze wdrażane na Microsoft Azure i nowa rola systemu lokacji, który komunikuje się z tą usługą. Klienci używają następnie usługę do komunikowania się z programem Configuration Manager.

Zalety:

-   Nie wymagane inwestycje dodatkowej infrastruktury.

-   Nie ujawnia infrastruktury lokalnej z Internetem.

-   Chmury maszyn wirtualnych, które uruchamiania usługi pełni są zarządzane przez usługę Azure i wymagają nie obsługi.

-   Łatwe i konfigurowana w konsoli programu Configuration Manager.

Wady:

-   W chmurze koszt subskrypcji.

-   Zarządzanie danych wysłanych przez usługę w chmurze.

Aby uzyskać więcej informacji, zobacz [planowanie brama zarządzania chmury](plan-cloud-management-gateway.md).

## <a name="internet-based-client-management"></a>Internetowe zarządzanie klientami

Ta metoda polega na serwerach systemu lokacji internetowy których klienci komunikują się w celu zarządzania nim. Ta metoda wymaga klienci i serwery systemu lokacji, można skonfigurować dla internetowego zarządzania.

Zalety:

-   Nie zależności usługi chmury.

-   Bez dodatkowych kosztów skojarzonych z subskrypcji usługi w chmurze.

-   Pełną kontrolę nad serwery i role świadczących usługę.

Wady:

-   Wymagają dodatkowej infrastruktury inwestycji.

-   Koszty i kosztów operacyjnych dodatkowe infrastruktury.

-   Infrastruktury musi mieć połączenie z Internetem.

Aby uzyskać więcej informacji, zobacz [Plan zarządzania klientami internetowymi](plan-internet-based-client-management.md).
