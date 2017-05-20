---
title: "Bezpieczeństwo i prywatność zapytania | Dokumentacja firmy Microsoft"
description: "Najlepsze rozwiązania dotyczące bezpieczeństwa i ochrony prywatności należy zrozumieć, kiedy kwerendy informacji z bazy danych lokacji."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 30080620-20d3-4c38-b8dd-db5516e1acae
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 10b1010ccbf3889c58c55b87e70b354559243c90
ms.openlocfilehash: 09f7bdaa29a01fb2a38aa223db56b5bce3bc5205
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="security-and-privacy-for-queries-in-system-center-configuration-manager"></a>Bezpieczeństwo i prywatność zapytań w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Kwerendy w programie System Center Configuration Manager umożliwiają pobieranie informacji z bazy danych lokacji na podstawie określonych kryteriów. Menedżer konfiguracji zbiera bazy danych lokacji w trakcie normalnej pracy. Na przykład za pomocą informacji, które zostały zebrane podczas odnajdywania lub spisu, zapytanie można skonfigurować w taki sposób, aby zidentyfikować urządzenia spełniające określone kryteria.  

 Aby uzyskać więcej informacji dotyczących kwerend, zobacz [wprowadzenie do kwerend w programie System Center Configuration Manager](../../../core/servers/manage/introduction-to-queries.md). Więcej informacji na temat wszelkie najlepsze rozwiązania i informacje o ochronie prywatności dla operacji programu Configuration Manager, które zbierają informacje, które można pobrać za pomocą kwerend, zobacz [zabezpieczenia i prywatność programu System Center Configuration Manager](../../../core/plan-design/security/security-and-privacy.md).  

## <a name="security-best-practices-for-queries"></a>Najlepsze rozwiązania w zakresie zabezpieczeń dotyczące zapytań  
 Należy stosować następujące najlepsze rozwiązania w zakresie zabezpieczeń dotyczące zapytań.  

|Najlepsze rozwiązanie w zakresie zabezpieczeń|Więcej informacji|  
|----------------------------|----------------------|  
|Podczas każdego eksportu lub importu zapytania zapisywanego w lokalizacji sieciowej zabezpieczaj zarówno samą lokalizację, jak i kanał sieciowy.|Ogranicz dostęp użytkowników do danego folderu sieciowego.<br /><br /> Aby zapobiec modyfikowaniu danych zapytania przed ich zaimportowaniem, korzystaj z podpisywania protokołu SMB lub protokołu IPsec między lokalizacją sieciową a serwerem lokacji oraz między lokalizacją sieciową a serwerem lokacji.|  

## <a name="see-also"></a>Zobacz też  
 [Dokumentacja techniczna zapytania dla programu System Center Configuration Manager](../../../core/servers/manage/queries-technical-reference.md)

