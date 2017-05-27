---
title: "Zarządzanie klientami w Internecie — Configuration Manager | Dokumentacja firmy Microsoft"
description: "Informacje o zarządzaniu klientów z chmury zarządzania bramy i zarządzania klientami w programie Configuration Manager."
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-client
ms.assetid: c667d6af-80c4-485f-910c-896c0171fd00
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 1b6752be448e1062c97a3225db4fa8af9f4832a6
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---

# <a name="manage-clients-on-the-internet-with-configuration-manager"></a>Zarządzanie klientami w Internecie przy użyciu programu Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Zwykle w programie Configuration Manager większość komputerów i serwerów, które są zarządzane są fizycznie w tej samej wewnętrznej sieci prywatnej lub firmowych jako serwery systemu lokacji, które wykonują funkcje zarządzania. Jednak można zarządzać komputerami klienckimi spoza sieci firmowej, jeśli są one połączone z Internetem bez konieczności klientów do łączenia za pomocą wirtualnych sieci prywatnych dociera do lokacji serwery systemu.

Program Configuration Manager udostępnia dwa sposoby zarządzania klientami połączonych z Internetem:

-   Brama zarządzania chmury

-   Internetowe zarządzanie klientami

## <a name="cloud-management-gateway"></a>Brama zarządzania chmury

Począwszy od wersji 1610, Configuration Manager wprowadza chmury zarządzania bramą. To nowa metoda umożliwia zarządzanie klientami internetowymi, korzystając z usługi w chmurze wdrożona Microsoft Azure i nowa rola systemu lokacji, który komunikuje się z tą usługą. Następnie klienci korzystają z usługi do komunikacji z programem Configuration Manager.

Zalety:

-   Nie wymaganych inwestycji dodatkowej infrastruktury.

-   Nie ujawnia infrastruktury lokalnej z Internetem.

-   Chmury maszyn wirtualnych, które uruchomienia usługi są w pełni zarządzane przez Azure i wymagają żadnej konserwacji.

-   Łatwo i konfigurowana w konsoli programu Configuration Manager.

Wady:

-   Koszt subskrypcji w chmurze.

-   Zarządzanie danych wysłanych przez usługę w chmurze.

Aby uzyskać więcej informacji, zobacz [planowanie brama zarządzania chmury](plan-cloud-management-gateway.md).

## <a name="internet-based-client-management"></a>Internetowe zarządzanie klientami

Ta metoda polega na serwerach systemu lokacji z Internetu do których klienci komunikują się do celów zarządzania. Ta metoda wymaga klientów i serwerów systemu lokacji można skonfigurować do zarządzania internetowego.

Zalety:

-   Nie zależności usługi chmury.

-   Bez dodatkowych kosztów skojarzone z subskrypcją chmury.

-   Pełna kontrola nad serwery i role świadczenie usług.

Wady:

-   Wymagają dodatkowej infrastruktury inwestycji.

-   I koszty operacyjne infrastruktury dodatkowe obciążenie.

-   Infrastruktury muszą być widoczne w Internecie.

Aby uzyskać więcej informacji, zobacz [Planowanie zarządzania klientami](plan-internet-based-client-management.md).

