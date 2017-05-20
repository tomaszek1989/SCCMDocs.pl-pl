---
title: Zapory i domen | Dokumentacja firmy Microsoft
description: "Konfigurowanie zapór, portów i domen do przygotowania do komunikacji programu System Center Configuration Manager."
ms.custom: na
ms.date: 2/6/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: d6993bba-f6bd-4639-adbf-efc1c638b2f3
caps.latest.revision: 15
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: bd20983eeca47bdd63e0385440e6c8d64901b902
ms.openlocfilehash: 4a2a8f96a900a2c4959ae3ff59232771ece95991
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="set-up-firewalls-ports-and-domains-for-system-center-configuration-manager"></a>Konfigurowanie zapór, portów i domen programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Przygotowywanie sieci do obsługi programu System Center Configuration Manager, należy zaplanować konfigurowanie infrastruktury, takich jak zapory umożliwiała komunikację używane przez program Configuration Manager.  

|Kwestia|Szczegóły|  
|-------------------|-------------|  
|**Porty i protokoły** czy użyć różnych funkcji programu Configuration Manager. Niektóre porty są wymagane, a inne można dostosować **domen i usług**.|Większości komunikacji programu Configuration Manager używać najczęściej używane porty port 80 dla protokołu HTTP i 443 do komunikacji HTTPS. Jednak [niektóre role systemu lokacji obsługuje korzystania z niestandardowych witryn sieci Web](/sccm/core/plan-design/network/websites-for-site-system-servers) i porty niestandardowe.<br /><br /> **Przed wdrożeniem programu Configuration Manager**, identyfikowania portów, które planujesz używać i odpowiednio skonfigurowane zapory.<br /><br /> **Jeśli zachodzi potrzeba zmiany portu** po zainstalowaniu programu Configuration Manager, nie zapomnij zaktualizować zapory w sieci i urządzeń oraz zmienić konfigurację portu z w ramach programu Configuration Manager.<br /><br /> Aby uzyskać więcej informacji, zobacz: </br>- [Jak skonfigurować porty komunikacyjne klienta](../../../core/clients/deploy/configure-client-communication-ports.md) </br>- [Porty używane w programie Configuration Manager](../../../core/plan-design/hierarchy/ports.md) </br>- [Internet access wymagania dotyczące punktu połączenia usługi](/sccm/core/servers/deploy/configure/about-the-service-connection-point#bkmk_urls)|  
|**Domen i usług** serwerów lokacji i klientów może być konieczne do użycia.|Możliwości programu Configuration Manager może wymagać lokacji serwery i klienci dostępu do określonych usług i domeny w Internecie, takich jak Windowsudpate.microsoft.com lub usługi Microsoft Intune.<br /><br /> Jeśli używasz Microsoft Intune do zarządzania urządzeniami przenośnymi, należy również skonfigurować dostęp do [portów i domen, które wymaga usługi Intune.](https://docs.microsoft.com/en-us/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)|  
|**Serwery proxy** dla serwerów systemu lokacji i komunikacji z klientem. Można określić odrębnych serwerów proxy dla różnymi serwerami systemu lokacji i klientów.|Ponieważ te konfiguracje są dokonywane w czasie instalowania roli systemu lokacji lub klienta, wystarczy należy pamiętać o konfiguracji serwera proxy do wykorzystania w późniejszym czasie podczas konfigurowania ról systemu lokacji i klientów.<br /><br /> Jeżeli nie masz pewności, wdrożenie będą musieli korzystać z serwerów proxy, sprawdź, czy [obsługi serwera Proxy w programie System Center Configuration Manager](../../../core/plan-design/network/proxy-server-support.md) Aby dowiedzieć się więcej o role systemu lokacji i akcje klienta, które można używać serwera proxy.|   
|  

