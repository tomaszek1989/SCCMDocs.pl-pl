---
title: "Diagnostyka i dane dotyczące użycia | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat diagnostyki i danych użycia programu System Center Configuration Manager umożliwia zbieranie informacji o sobie."
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 88ac4e55-d47b-4c94-b9c3-704c6a48b845
caps.latest.revision: 9
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 4a4b7c9c0d40b6bd3ea2f318e37d744f1a0cc084
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="diagnostics-and-usage-data-for-system-center-configuration-manager"></a>Dane diagnostyczne i dane użycia dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

System Center Configuration Manager umożliwia zbieranie diagnostyki i danych użycia o, który jest używany przez firmę Microsoft do poprawy obsługi instalacji, jakość i bezpieczeństwo w przyszłych wersjach.  

 Diagnostyka i danych użycia jest włączona dla każdej hierarchii programu System Center Configuration Manager. Składa się on z kwerend programu SQL Server, uruchamiane co tydzień w każdej lokacji głównej i centralnej lokacji administracyjnej. Jeśli hierarchia używa centralnej lokacji administracyjnej, dane z lokacji głównych są replikowane do tej lokacji. W lokacji najwyższego poziomu w hierarchii punkt połączenia usługi przesyła te informacje podczas sprawdzania aktualizacji. Jeśli punkt połączenia usługi jest w trybie offline, dane te są przenoszone przy użyciu narzędzia połączenia usługi.  

> [!NOTE]  
>  Menedżer konfiguracji zbiera dane tylko z bazy danych lokacji programu SQL server, a nie zbiera danych bezpośrednio od klientów lub serwerów lokacji.  

 Aby uzyskać więcej informacji, zobacz [zachowania poufności informacji dla programu System Center Configuration Manager](http://go.microsoft.com/fwlink/?LinkID=626527).  

 Więcej informacji o danych diagnostycznych i użycia programu System Center Configuration Manager w następujących artykułach:  

-   [Sposób użycia danych diagnostycznych i użycia programu System Center Configuration Manager](../../../core/plan-design/diagnostics/how-diagnostics-and-usage-data-is-used.md)  

-   Poziomy zbierania danych diagnostycznych użycia:
    - [Dane diagnostyczne dla 1702](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1702)      
    - [Dane diagnostyczne dla 1610](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1610)  
    - [Dane diagnostyczne dla 1606](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1606)    

<!--
    - [Diagnostic data for 1602](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1602)
    - [Diagnostic data for  1511](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1511)
-->

-   [Jak danych diagnostycznych i użycia są zbierane przez program System Center Configuration Manager](../../../core/plan-design/diagnostics/how-diagnostics-and-usage-data-is-collected.md)  

-   [Jak wyświetlić diagnostyki i dane dotyczące użycia programu System Center Configuration Manager](../../../core/plan-design/diagnostics/view-diagnostics-and-usage-data.md)  

-   [Program poprawy jakości obsługi klienta (CEIP) programu System Center Configuration Manager](../../../core/plan-design/diagnostics/customer-experience-improvement-program-ceip.md)  

-   [Często zadawane pytania dotyczące diagnostyki i dane dotyczące użycia programu System Center Configuration Manager](../../../core/understand/frequently-asked-questions-about-diagnostics-and-usage-data.md)  

## <a name="see-also"></a>Zobacz też  
 [O punktu połączenia usługi w programie System Center Configuration Manager](../../../core/servers/deploy/configure/about-the-service-connection-point.md)

