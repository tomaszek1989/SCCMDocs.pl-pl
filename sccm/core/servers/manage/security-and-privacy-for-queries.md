---
title: "Bezpieczeństwo i prywatność zapytań | Dokumentacja firmy Microsoft"
description: "Najlepsze rozwiązania dotyczące zabezpieczeń i prywatności należy zrozumieć, kiedy można wyszukiwać informacje z bazy danych lokacji."
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
ms.sourcegitcommit: 2087badc9dd1d216352dce232b145a786783ac89
ms.openlocfilehash: e42b13c68ecaeac94245838c2f42e2790799de2b
ms.contentlocale: pl-pl
ms.lasthandoff: 05/18/2017


---
# <a name="security-and-privacy-for-queries-in-system-center-configuration-manager"></a>Bezpieczeństwo i prywatność zapytań w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Zapytania w programie System Center Configuration Manager umożliwiają pobieranie informacji z bazy danych lokacji na podstawie określonych kryteriów. Menedżer konfiguracji zbiera informacje z bazy danych lokacji podczas normalnego działania. Na przykład za pomocą informacji, które zostały zebrane podczas odnajdywania lub spisu, zapytanie można skonfigurować w taki sposób, aby zidentyfikować urządzenia spełniające określone kryteria.  

 Aby uzyskać więcej informacji o zapytaniach znajduje się w temacie [wprowadzenie do zapytań w programie System Center Configuration Manager](../../../core/servers/manage/introduction-to-queries.md). Aby uzyskać więcej informacji na temat najlepszych rozwiązań dotyczących zabezpieczeń i informacje o ochronie prywatności dla operacji programu Configuration Manager, które zbierają informacje, które można pobrać za pomocą zapytań, zobacz [zabezpieczenia i prywatność programu System Center Configuration Manager](../../../core/plan-design/security/security-and-privacy.md).  

## <a name="security-best-practices-for-queries"></a>Najlepsze rozwiązania w zakresie zabezpieczeń dotyczące zapytań  
 Należy stosować następujące najlepsze rozwiązania w zakresie zabezpieczeń dotyczące zapytań.  

|Najlepsze rozwiązanie w zakresie zabezpieczeń|Więcej informacji|  
|----------------------------|----------------------|  
|Podczas każdego eksportu lub importu zapytania zapisywanego w lokalizacji sieciowej, należy zabezpieczyć lokalizację i kanał sieciowy.|Ogranicz dostęp użytkowników do danego folderu sieciowego.<br /><br /> Aby zapobiec modyfikowaniu danych zapytania przed ich zaimportowaniem, korzystaj z podpisywania protokołu SMB lub protokołu IPsec między lokalizacją sieciową a serwerem lokacji oraz między lokalizacją sieciową a serwerem lokacji.|  

## <a name="see-also"></a>Zobacz także  
 [Informacje techniczne dotyczące zapytań programu System Center Configuration Manager](../../../core/servers/manage/queries-technical-reference.md)

