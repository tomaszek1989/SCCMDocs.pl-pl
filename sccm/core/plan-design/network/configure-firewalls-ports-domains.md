---
title: Zapór i domen
titleSuffix: Configuration Manager
description: Konfigurowanie zapór, portów i domen do przygotowania do komunikacji programu System Center Configuration Manager.
ms.date: 2/6/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: d6993bba-f6bd-4639-adbf-efc1c638b2f3
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: ee7494b582828014114d41eb6bb721a7e1fd5c16
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="set-up-firewalls-ports-and-domains-for-system-center-configuration-manager"></a>Konfigurowanie zapór, portów i domen dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Aby przygotować sieć do obsługi programu System Center Configuration Manager, Planowanie konfigurowania infrastruktury, takiej jak zapory w celu przekazywania informacji używanych przez program Configuration Manager.  

|Kwestia|Szczegóły|  
|-------------------|-------------|  
|**Porty i protokoły** czy użyć różnych funkcji programu Configuration Manager. Niektóre porty są wymagane, a inne można dostosować **domen i usług**.|Większość komunikacji programu Configuration Manager używane typowe porty, takie jak port 80 dla protokołu HTTP i 443 dla protokołu HTTPS. Jednak [niektóre role systemu lokacji obsługują korzystanie z niestandardowych witryn sieci Web](/sccm/core/plan-design/network/websites-for-site-system-servers) i niestandardowych portów.<br /><br /> **Przed wdrożeniem programu Configuration Manager**, identyfikowania portów, które planujesz używać i odpowiednio skonfigurowane zapory.<br /><br /> **Jeśli musisz zmienić port** po zainstalowaniu programu Configuration Manager, nie zapomnij zaktualizować zapór na urządzeniach i sieci oraz zmienić konfigurację portu od w programie Configuration Manager.<br /><br /> Aby uzyskać więcej informacji, zobacz: </br>- [Jak skonfigurować porty komunikacyjne klienta](../../../core/clients/deploy/configure-client-communication-ports.md) </br>- [Porty używane w programie Configuration Manager](../../../core/plan-design/hierarchy/ports.md) </br>- [Wymagania dotyczące dostępu internetowego punktu połączenia usługi](/sccm/core/servers/deploy/configure/about-the-service-connection-point#bkmk_urls)|  
|**Domeny i usługi** serwerów lokacji i klientów może być konieczne do użycia.|Funkcje programu Configuration Manager mogą wymagać serwerów lokacji i klientów dostępu do określonych usług i domen w Internecie, takich jak Windowsudpate.microsoft.com lub usługa Microsoft Intune.<br /><br /> Jeśli korzystasz z programu Microsoft Intune do zarządzania urządzeniami przenośnymi, należy również skonfigurować dostęp do [portów i domen wymaganych przez usługę Intune.](https://docs.microsoft.com/en-us/intune/get-started/network-infrastructure-requirements-for-microsoft-intune)|  
|**Serwery proxy** dla serwerów systemu lokacji i komunikacji z klientem. Możesz określić odrębne serwery proxy dla różnymi serwerami systemu lokacji i klientów.|Ponieważ te konfiguracje zostaną zastosowane w czasie instalowania roli systemu lokacji lub klienta, wystarczy należy pamiętać o konfiguracji serwera proxy podczas późniejszego konfigurowania ról systemu lokacji i klientów.<br /><br /> Jeśli nie masz pewności, wdrożenie będzie potrzebować do korzystania z serwerów proxy, przejrzyj [Obsługa serwerów Proxy w programie System Center Configuration Manager](../../../core/plan-design/network/proxy-server-support.md) informacje na temat ról systemu lokacji i akcji klienta, które można użyć serwera proxy.|   
|  
