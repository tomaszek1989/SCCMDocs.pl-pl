---
title: Dane diagnostyczne i dane użycia
titleSuffix: Configuration Manager
description: Więcej informacji na temat diagnostycznych i danych użycia programu System Center Configuration Manager umożliwia zbieranie informacji o sobie samym.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 88ac4e55-d47b-4c94-b9c3-704c6a48b845
caps.latest.revision: ''
caps.handback.revision: ''
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 5f783f11f6fbabda2fd1d6f98748e945affa878e
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="diagnostics-and-usage-data-for-system-center-configuration-manager"></a>Dane diagnostyczne i dane użycia dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Menedżer konfiguracji zbiera dane diagnostyczne i dane użycia o sobie, który jest używany przez firmę Microsoft do poprawy obsługi instalacji, jakości i bezpieczeństwa przyszłych wersji.  

 Dane diagnostyczne i użycia danych jest włączone dla każdej hierarchii programu Configuration Manager. Składa się z zapytań programu SQL Server, które są uruchamiane co tydzień w każdej lokacji głównej i centralnej lokacji administracyjnej. Jeśli hierarchia używa centralnej lokacji administracyjnej, dane z lokacji głównych są replikowane do tej lokacji. W lokacji najwyższego poziomu w hierarchii punkt połączenia usługi przesyła te informacje podczas sprawdzania aktualizacji. Jeśli punkt połączenia usługi jest w trybie offline, dane te są przenoszone przy użyciu narzędzia połączenia usługi.  

> [!NOTE]  
>  Menedżer konfiguracji zbiera dane tylko z bazy danych serwera SQL dla lokacji i nie zbiera danych bezpośrednio od klientów lub serwerów lokacji.  

 Aby uzyskać więcej informacji, zobacz [zasady zachowania poufności informacji firmy Microsoft](https://go.microsoft.com/fwlink/?LinkID=626527).  

## <a name="articles"></a>Artykuły
 Więcej informacji na temat danych diagnostycznych i użycia programu Configuration Manager w następujących artykułach:  

-   [Jak używane są dane diagnostyczne i dane użycia](../../../core/plan-design/diagnostics/how-diagnostics-and-usage-data-is-used.md)  

-   Poziomy zbierania diagnostycznych danych użycia:
    - [Dane diagnostyczne dla 1802](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1802)  
    - [Dane diagnostyczne dla wersji 1710](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1710)  
    - [Przesłanie danych diagnostycznych dla wersji 1706](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1706)    

<!--
    - [Diagnostic data for 1702](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1702)      
    - [Diagnostic data for 1610](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1610)  
    - [Diagnostic data for  1606](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1606)    
    - [Diagnostic data for 1602](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1602)
    - [Diagnostic data for  1511](/sccm/core/plan-design/diagnostics/levels-of-diagnostic-usage-data-collection-1511)
-->

-   [Jak zbierane są dane diagnostyczne i dane użycia](../../../core/plan-design/diagnostics/how-diagnostics-and-usage-data-is-collected.md)  

-   [Jak wyświetlać dane diagnostyczne i dane użycia](../../../core/plan-design/diagnostics/view-diagnostics-and-usage-data.md)  

-   [Program poprawy jakości obsługi klienta](../../../core/plan-design/diagnostics/customer-experience-improvement-program-ceip.md)  

     > [!Note]  
     > Począwszy od programu Configuration Manager w wersji 1802 funkcję programu CEIP zostanie usunięte z produktu.


-   [Często zadawane pytania dotyczące danych diagnostycznych i danych użycia](../../../core/understand/frequently-asked-questions-about-diagnostics-and-usage-data.md)  

## <a name="see-also"></a>Zobacz też  
 [Informacje o punkcie połączenia z usługą](../../../core/servers/deploy/configure/about-the-service-connection-point.md)
