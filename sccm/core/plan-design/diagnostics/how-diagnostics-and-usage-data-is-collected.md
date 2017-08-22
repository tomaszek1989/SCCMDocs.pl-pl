---
title: Zbieranie danych diagnostycznych | Dokumentacja firmy Microsoft
description: "Więcej informacji na temat sposobu System Center Configuration Manager zbiera dane diagnostyczne i dane użycia o sobie samym."
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: becfa825-b19f-448c-ab82-bb929255e4ae
caps.latest.revision: "5"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 9c0165212fe34f460be2ce870d0542b616f3bc4d
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="how-diagnostics-and-usage-data-is-collected-by-system-center-configuration-manager"></a>Jak zbierane są dane diagnostyczne i dane użycia dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Aby zbierać dane diagnostyczne i dane użycia dla programu System Center Configuration Manager, każda lokacja główna działa zapytań programu SQL Server w cyklu tygodniowym. W hierarchii wielu lokacji dane są replikowane do centralnej lokacji administracyjnej.  

W lokacji najwyższego poziomu w hierarchii rola systemu lokacji punktu połączenia z usługą przesyła te informacje podczas wyszukiwania aktualizacji. Tryb Określa punkt połączenia usługi, jak dane są przesyłane:  

-   **W trybie online:** Diagnostyczne i dane użycia są wysyłane automatycznie, raz w tygodniu z połączenia z usługą punktu do usługi w chmurze.  

-   **W trybie offline:** Dane diagnostyczne i użycia są wysyłane ręcznie za pomocą narzędzia połączenia usługi. Aby uzyskać więcej informacji, zobacz [Używanie narzędzia połączenia z usługą w programie System Center Configuration Manager](../../../core/servers/manage/use-the-service-connection-tool.md).  

Aby uzyskać więcej informacji, zobacz [Informacje o punkcie połączenia z usługą w programie System Center Configuration Manager](../../../core/servers/deploy/configure/about-the-service-connection-point.md).  
