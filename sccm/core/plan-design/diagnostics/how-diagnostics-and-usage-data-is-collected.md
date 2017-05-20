---
title: Zbieranie danych diagnostyki | Dokumentacja firmy Microsoft
description: "Dowiedz się, jak System Center Configuration Manager umożliwia zbieranie diagnostyki i danych użycia o sobie."
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: becfa825-b19f-448c-ab82-bb929255e4ae
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 24a233516058e645df2a43623855665b97b041b0
ms.openlocfilehash: 9c0165212fe34f460be2ce870d0542b616f3bc4d
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-diagnostics-and-usage-data-is-collected-by-system-center-configuration-manager"></a>Jak zbierane są dane diagnostyczne i dane użycia dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Zbieranie diagnostyki i dane dotyczące użycia programu System Center Configuration Manager, każdej lokacji głównej jest uruchomiony kwerend programu SQL Server w cyklu tygodniowym. W hierarchii wielu lokacji dane są replikowane do centralnej lokacji administracyjnej.  

W lokacji najwyższego poziomu w hierarchii rola systemu lokacji punktu połączenia z usługą przesyła te informacje podczas wyszukiwania aktualizacji. Tryb detemines punktu połączenia usługi sposób przekazywania danych:  

-   **W trybie online:** Danych diagnostycznych i użycia są automatycznie wysyłane po tygodniu od połączenia z usługą punktu do usługi w chmurze.  

-   **W trybie offline:** Diagnostyka i użycia dane są przenoszone ręcznie przy użyciu narzędzia połączenia usługi. Aby uzyskać więcej informacji, zobacz [Używanie narzędzia połączenia z usługą w programie System Center Configuration Manager](../../../core/servers/manage/use-the-service-connection-tool.md).  

Aby uzyskać więcej informacji, zobacz [Informacje o punkcie połączenia z usługą w programie System Center Configuration Manager](../../../core/servers/deploy/configure/about-the-service-connection-point.md).  

