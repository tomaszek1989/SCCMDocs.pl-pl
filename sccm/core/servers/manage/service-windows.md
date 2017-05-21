---
title: "Usługi systemu Windows | Dokumentacja firmy Microsoft"
description: "Użyj usługi systemu windows do sterowania podczas instalacji aktualizacji w lokacji programu System Center Configuration Manager."
ms.custom: na
ms.date: 1/11/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ca4886d4-7173-46be-8dcd-1657d5b0deb9
caps.latest.revision: 4
caps.handback.revision: 0
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d0735c170820259ac8bb6706aac7cc5569a1628
ms.openlocfilehash: d06a2a955ff59fa84bb844033fe31874fc735087
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
#  <a name="service-windows-for-site-servers"></a>Usługi systemu windows dla serwerów lokacji

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Usługi systemu windows można skonfigurować w administracji centralnej i lokacje główne do kontroli, gdy można zainstalować aktualizacji w konsoli.  Można skonfigurować wiele okien, okien dozwolone w przypadku instalowania aktualizacji określane przez kombinację wszystkie usługi systemu windows dla tego serwera lokacji.

Gdy jest skonfigurowany żadnego okna usługi:
- **W witrynie najwyższego poziomu** (centralnej lokacji administracyjnej lub autonomicznej lokacji głównej) wybierz uruchamianiem instalacji aktualizacji.
- **W lokacji podstawowej podrzędnych**, aktualizacja zostanie zainstalowana automatycznie po ukończeniu instalacji w witrynie Administracja centralna.
- **W lokacji dodatkowej**, aktualizacje nigdy uruchamiana automatycznie. Zamiast tego należy ręcznie uruchomić instalację aktualizacji z poziomu konsoli, po zainstalowaniu aktualizacji nadrzędnej lokacji głównej.

Gdy okno usług jest skonfigurowany:
- **W witrynie najwyższego poziomu**, nie będzie można uruchomić instalacji nowych aktualizacji z konsoli programu Configuration Manager. Nawet w przypadku skonfigurowano okno usługi lokacji automatycznie pobiera aktualizacje tak, aby były gotowe do zainstalowania.  
- **W lokacji podstawowej podrzędnych**, aktualizacje, które zostały zainstalowane w witrynie Administracja centralna spowoduje pobranie do lokacji głównej, ale nie automatycznie rozpoczęcia. Nie można ręcznie uruchomić instalację aktualizacji w czasie, jest zablokowany przez użycie przedział czasu usługi. W czasie gdy usługa systemu windows nie jest już bloku instalacji aktualizacji aktualizacji instalacji automatycznie uruchamia.
- **Lokacje dodatkowe** nie obsługują usługi systemu windows, a aktualizacje nie są automatycznie instalowane. Po zainstalowaniu lokacji głównej nadrzędnej lokacji dodatkowej aktualizacji, można uruchomić aktualizację lokacji dodatkowej z konsoli.

## <a name="to-configure-a-service-window"></a>Aby skonfigurować okna usługi

1.  W konsoli programu Configuration Manager Otwórz **Administracja** > **konfiguracja lokacji** > **witryny**, a następnie wybierz serwer lokacji, w której chcesz skonfigurować okno usługi.  

2.  Następnie edytuj **Właściwości** serwera lokacji i wybierz kartę **Okno usługi** , na której możesz ustawić okno usługi lub kilka okien usługi dla tego serwera lokacji.  

