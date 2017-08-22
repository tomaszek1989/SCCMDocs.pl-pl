---
title: "Usługi systemu Windows | Dokumentacja firmy Microsoft"
description: "Usługi systemu windows umożliwia sterowanie podczas instalacji aktualizacji w lokacji programu System Center Configuration Manager."
ms.custom: na
ms.date: 1/11/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ca4886d4-7173-46be-8dcd-1657d5b0deb9
caps.latest.revision: "4"
caps.handback.revision: "0"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: d06a2a955ff59fa84bb844033fe31874fc735087
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
#  <a name="service-windows-for-site-servers"></a>Okna usług dla serwerów lokacji

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Można skonfigurować okna usługi w centralnych lokacjach administracyjnych i lokacjach głównych do formantu, gdy można zainstalować aktualizacji w konsoli.  Okno z uprawnieniami do instalowania aktualizacji jest określany przez kombinację wszystkich okien usługi dla serwera lokacji można skonfigurować wiele okien.

Gdy przedział czasu usługi nie jest skonfigurowany:
- **W lokacji najwyższego poziomu** (centralnej lokacji administracyjnej lub autonomicznej lokacji głównej) można zdecydować, kiedy rozpocząć instalację aktualizacji.
- **W lokacji podrzędnej**, aktualizacja zostanie zainstalowana automatycznie po ukończeniu instalacji w witrynie Administracja centralna.
- **W lokacji dodatkowej**, aktualizacje nigdy uruchamiana automatycznie. Zamiast tego należy ręcznie uruchomić instalację aktualizacji z poziomu konsoli po nadrzędnej lokacji głównej ma zainstalowaną aktualizację.

Jeśli skonfigurowano okno usługi:
- **W lokacji najwyższego poziomu**, nie można uruchomić instalacji nowej aktualizacji z poziomu konsoli programu Configuration Manager. Nawet w przypadku przedział czasu usługi skonfigurowane lokacji automatycznie pobiera aktualizacje, dzięki czemu są one gotowe do zainstalowania.  
- **W lokacji podrzędnej**, aktualizacji, które zostały zainstalowane w witrynie Administracja centralna spowoduje pobranie do lokacji głównej, ale nie automatycznie rozpoczęcia. Nie można ręcznie uruchomić instalację aktualizacji w czasie, który jest zablokowany przez użycie okna usługi. W czasie, po zainstalowaniu aktualizacji usługi systemu windows nie jest już bloku aktualizacji instalowane automatycznie uruchamia.
- **Lokacje dodatkowe** nie obsługuje usługi systemu windows i nie są instalowane automatycznie aktualizacji. Po zainstalowaniu aktualizacji lokacji głównej nadrzędnej lokacji dodatkowej można uruchomić aktualizację lokacji dodatkowej z poziomu konsoli.

## <a name="to-configure-a-service-window"></a>Aby skonfigurować okno usługi

1.  W konsoli programu Configuration Manager Otwórz **administracji** > **konfiguracja lokacji** > **witryny**, a następnie wybierz serwer lokacji, w której chcesz skonfigurować okno usługi.  

2.  Następnie edytuj **Właściwości** serwera lokacji i wybierz kartę **Okno usługi** , na której możesz ustawić okno usługi lub kilka okien usługi dla tego serwera lokacji.  
