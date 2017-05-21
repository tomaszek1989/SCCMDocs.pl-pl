---
title: "Monitorować stan wdrożenia klienta | Dokumentacja firmy Microsoft"
description: "Monitorować stan wdrożenia klienta w programie System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 20a573b3-53cb-4ed5-bae1-7542f533ed20
caps.latest.revision: 11
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 3d9d02d8c56aea17e563112f92173c2b56781da6
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-monitor-client-deployment-status-in-system-center-configuration-manager"></a>Jak monitorować stan wdrażania klientów w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Wdrażanie klientów w lokacji jest czasochłonne, a niektóre instalacje kończą się niepowodzeniem przy pierwszej próbie. Konsoli programu System Center Configuration Manager umożliwia śledzą wdrożeń klientów w kolekcji raportowanie stanu wdrożenia klienta w czasie rzeczywistym.  

> [!NOTE]  
>  Najlepsze i najbardziej niezawodnym sposobem monitorowania wdrażania klientów jest za pomocą konsoli programu Configuration Manager (zgodnie z opisem w tym artykule). W sekcji **Stan klienta** obszaru roboczego **Monitorowanie** w konsoli wyświetlane są w czasie rzeczywistym precyzyjne informacje dotyczące stanu wdrożenia klienta. Można monitorować wdrożenia klientów przy użyciu innych narzędzi, takich jak program Server Manager w systemie Windows Server lub program System Center Operations Manager, ale w takim przypadku mogą być zgłaszane alarmy dotyczące normalnej aktywności związanej z instalowaniem klientów. Ze względu na sposób wykonywania programu instalacyjnego klienta (CCMSetup.exe) w różnych środowiskach narzędzia te mogą generować fałszywe alarmy i ostrzeżenia, które nie odzwierciedlają dokładnie stanu wdrożeń klientów.  

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

-   Aby zmienić zakres raportu, kliknij przycisk **Przeglądaj...**  i wybierz polecenie innej kolekcji.  

 Aby dowiedzieć się więcej na temat wdrożenia klienta przedprodukcyjnego, zobacz [sposób testowania uaktualnienia klienta w kolekcji przedprodukcyjnej w programie System Center Configuration Manager](../../../core/clients/manage/upgrade/test-client-upgrades.md).

 > [!NOTE]
 > Stan wdrożenia na komputerach obsługujących ról systemu lokacji w kolekcji przedprodukcyjnej może być zgłaszany jako **niezgodnych** nawet jeśli klient został pomyślnie wdrożony. W przypadku podwyższania poziomu klienta do produkcji stan wdrożenia jest zgłaszany prawidłowo.   

 Aby monitorować stan wdrażanych klientów, zobacz [Jak monitorować klientów w programie System Center Configuration Manager](../../../core/clients/manage/monitor-clients.md)  

 Raporty programu Configuration Manager można użyć, aby dowiedzieć się więcej o stanie klientów w danej lokacji. Więcej informacji o sposobie uruchamiania raportów znajduje się w temacie [Raportowanie w programie System Center Configuration Manager](../../../core/servers/manage/reporting.md).  

