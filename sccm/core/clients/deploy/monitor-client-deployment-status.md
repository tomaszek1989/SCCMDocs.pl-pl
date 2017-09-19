---
title: "Monitorowanie stanu wdrożenia klientów | Dokumentacja firmy Microsoft"
description: "Monitorować stan wdrażania klientów w programie System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 20a573b3-53cb-4ed5-bae1-7542f533ed20
caps.latest.revision: "11"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: bddc2cf4ae335a8b407035a90818d7fa01dcc398
ms.sourcegitcommit: f6a428a8db7145affa388f59e0ad880bdfcf17b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2017
---
# <a name="how-to-monitor-client-deployment-status-in-system-center-configuration-manager"></a>Jak monitorować stan wdrażania klientów w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Wdrażanie klientów w lokacji jest czasochłonne, a niektóre instalacje kończą się niepowodzeniem przy pierwszej próbie. Konsoli programu System Center Configuration Manager umożliwia śledzić wdrażania klientów w kolekcji dzięki raportowaniu stanu wdrożenia klientów w czasie rzeczywistym.  

> [!NOTE]  
>  Najlepszym i najbardziej niezawodnym sposobem monitorowania wdrażania klientów jest z konsoli programu Configuration Manager (zgodnie z opisem w tym artykule). W sekcji **Stan klienta** obszaru roboczego **Monitorowanie** w konsoli wyświetlane są w czasie rzeczywistym precyzyjne informacje dotyczące stanu wdrożenia klienta. Można monitorować wdrożenia klientów przy użyciu innych narzędzi, takich jak program Server Manager w systemie Windows Server lub program System Center Operations Manager, ale w takim przypadku mogą być zgłaszane alarmy dotyczące normalnej aktywności związanej z instalowaniem klientów. Ze względu na sposób wykonywania programu instalacyjnego klienta (CCMSetup.exe) w różnych środowiskach narzędzia te mogą generować fałszywe alarmy i ostrzeżenia, które nie odzwierciedlają dokładnie stanu wdrożeń klientów.  

 W obszarze roboczym **Monitorowanie** konsoli wyświetlane są następujące informacje dotyczące stanu wdrożeń dokonywanych w określonej kolekcji:  

-   Zgodny  

-   W toku  

-   Niezgodne  

-   Niepowodzenie  

-   Nieznane  

 Program Configuration Manager zgłasza wdrożenia dla klientów w środowisku produkcyjnym lub klientów przedprodukcyjnych. Konsola programu Configuration Manager udostępnia również wykres nieudanych wdrożeń klientów w określonym przedziale czasowym, aby ułatwić ustalenie, czy działania podejmowane w celu rozwiązania problemów z wdrożeniami umożliwiają zwiększenie częstotliwości sukcesów wdrażania po pewnym czasie.  

## <a name="to-monitor-client-deployments"></a>Aby monitorować wdrożenia klientów  

-   W konsoli programu Configuration Manager kliknij **monitorowanie** > **stanu klienta**.  

-   Kliknij pozycję **Produkcyjne wdrożenie klienta** lub **Przedprodukcyjne wdrożenie klienta** zależnie od wersji klienta, którego chcesz monitorować.  

-   Przejrzyj wykresy stanu wdrożenia klientów i niepowodzeń wdrażania klientów.  

-   Jeśli chcesz zmienić zakres raportu, kliknij przycisk **Przeglądaj... ** i wybierz inną kolekcję.  

 Aby dowiedzieć się więcej na temat wdrożeń klientów przedprodukcyjnych, zobacz [testowanie uaktualnień klienta w kolekcji przedprodukcyjnej w programie System Center Configuration Manager](../../../core/clients/manage/upgrade/test-client-upgrades.md).

 > [!NOTE]
 > Stan wdrożenia na komputerach hostujących role systemu lokacji w kolekcji środowiska przedprodukcyjnego mogą być zgłaszane jako **niezgodnych** nawet jeśli klient został pomyślnie wdrożony. W przypadku podwyższania poziomu klienta do produkcji stan wdrożenia jest zgłaszany prawidłowo.   

 Aby monitorować stan wdrażanych klientów, zobacz [Jak monitorować klientów w programie System Center Configuration Manager](../../../core/clients/manage/monitor-clients.md)  

 Aby uzyskać więcej informacji o stanie klientów w lokacji, można użyć raportów programu Configuration Manager. Więcej informacji o sposobie uruchamiania raportów znajduje się w temacie [Raportowanie w programie System Center Configuration Manager](../../../core/servers/manage/reporting.md).  
