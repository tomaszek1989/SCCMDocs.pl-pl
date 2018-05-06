---
title: Zbieranie danych diagnostycznych
titleSuffix: Configuration Manager
description: Więcej informacji na temat sposobu System Center Configuration Manager zbiera dane diagnostyczne i dane użycia o sobie samym.
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: becfa825-b19f-448c-ab82-bb929255e4ae
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 7eb4becd24ac143ce17c476cda0535ac6bedd039
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-diagnostics-and-usage-data-is-collected-by-system-center-configuration-manager"></a>Jak zbierane są dane diagnostyczne i dane użycia dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Aby zbierać dane diagnostyczne i dane użycia dla programu System Center Configuration Manager, każda lokacja główna działa zapytań programu SQL Server w cyklu tygodniowym. W hierarchii wielu lokacji dane są replikowane do centralnej lokacji administracyjnej.  

W lokacji najwyższego poziomu w hierarchii rola systemu lokacji punktu połączenia z usługą przesyła te informacje podczas wyszukiwania aktualizacji. Tryb Określa punkt połączenia usługi, jak dane są przesyłane:  

-   **W trybie online:** Diagnostyczne i dane użycia są wysyłane automatycznie, raz w tygodniu z połączenia z usługą punktu do usługi w chmurze.  

-   **W trybie offline:** Dane diagnostyczne i użycia są wysyłane ręcznie za pomocą narzędzia połączenia usługi. Aby uzyskać więcej informacji, zobacz [Używanie narzędzia połączenia z usługą w programie System Center Configuration Manager](../../../core/servers/manage/use-the-service-connection-tool.md).  

Aby uzyskać więcej informacji, zobacz [Informacje o punkcie połączenia z usługą w programie System Center Configuration Manager](../../../core/servers/deploy/configure/about-the-service-connection-point.md).  
