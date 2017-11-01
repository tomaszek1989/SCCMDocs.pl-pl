---
title: "Dane diagnostyczne i dane użycia"
titleSuffix: Configuration Manager
description: "Więcej informacji na temat diagnostycznych i danych użycia programu System Center Configuration Manager umożliwia zbieranie informacji o sobie samym."
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 88ac4e55-d47b-4c94-b9c3-704c6a48b845
caps.latest.revision: "9"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 478951f274c48424a3da0b8803968c2a51c93b76
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="diagnostics-and-usage-data-for-system-center-configuration-manager"></a>Dane diagnostyczne i dane użycia dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

System Center Configuration Manager zbiera dane diagnostyczne i dane użycia o sobie, który jest używany przez firmę Microsoft do poprawy obsługi instalacji, jakości i bezpieczeństwa przyszłych wersji.  

 Dane diagnostyczne i dane użycia jest włączone dla każdej hierarchii programu System Center Configuration Manager. Składa się z zapytań programu SQL Server, które są uruchamiane co tydzień w każdej lokacji głównej i centralnej lokacji administracyjnej. Jeśli hierarchia używa centralnej lokacji administracyjnej, dane z lokacji głównych są replikowane do tej lokacji. W lokacji najwyższego poziomu w hierarchii punkt połączenia usługi przesyła te informacje podczas sprawdzania aktualizacji. Jeśli punkt połączenia usługi jest w trybie offline, dane te są przenoszone przy użyciu narzędzia połączenia usługi.  

> [!NOTE]  
>  Menedżer konfiguracji zbiera dane tylko z bazy danych serwera SQL dla lokacji i nie zbiera danych bezpośrednio od klientów lub serwerów lokacji.  

 Aby uzyskać więcej informacji, zobacz [poufności informacji programu System Center Configuration Manager](http://go.microsoft.com/fwlink/?LinkID=626527).  

 Więcej informacji o danych diagnostycznych i użycia programu System Center Configuration Manager w następujących artykułach:  

-   [Sposób użycia danych diagnostycznych i użycia programu System Center Configuration Manager](../../../core/plan-design/diagnostics/how-diagnostics-and-usage-data-is-used.md)  

-   Poziomy zbierania diagnostycznych danych użycia:
    - [Przesłanie danych diagnostycznych dla wersji 1702](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1702)      
    - [Przesłanie danych diagnostycznych dla wersji 1610](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1610)  
    - [Dane diagnostyczne dla 1606](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1606)    

<!--
    - [Diagnostic data for 1602](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1602)
    - [Diagnostic data for  1511](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1511)
-->

-   [Jak diagnostyczne i dane użycia są zbierane przez program System Center Configuration Manager](../../../core/plan-design/diagnostics/how-diagnostics-and-usage-data-is-collected.md)  

-   [Jak wyświetlać dane diagnostyczne i dane użycia dla programu System Center Configuration Manager](../../../core/plan-design/diagnostics/view-diagnostics-and-usage-data.md)  

-   [Program poprawy jakości obsługi klienta (CEIP) programu System Center Configuration Manager](../../../core/plan-design/diagnostics/customer-experience-improvement-program-ceip.md)  

-   [Często zadawane pytania dotyczące danych diagnostycznych i danych użycia programu System Center Configuration Manager](../../../core/understand/frequently-asked-questions-about-diagnostics-and-usage-data.md)  

## <a name="see-also"></a>Zobacz też  
 [Informacje o punkcie połączenia usługi w programie System Center Configuration Manager](../../../core/servers/deploy/configure/about-the-service-connection-point.md)
