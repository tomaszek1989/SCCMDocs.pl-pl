---
title: Brama zarządzania chmury monitora
titleSuffix: Configuration Manager
description: Monitorowanie klientów i ruchu sieciowego za pośrednictwem bramy zarządzania chmury (CMG).
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.assetid: 15f72f80-9850-40ce-9c3a-443ba04b6a03
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: a4ecbeb2484297160797b7b5632c86cee4ff1122
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="monitor-cloud-management-gateway-in-configuration-manager"></a>Monitor bramy zarządzania w chmurze w programie Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Po chmurze brama zarządzania jest uruchomiona i łączenia klientów z przy jego użyciu, można monitorować klientów i ruchu sieciowego, aby upewnić się, że wiesz, jak działa usługa.



## <a name="monitor-clients"></a>Monitor klientów

Klientów połączonych za pośrednictwem bramy zarządzania w chmurze są wyświetlane w konsoli programu Configuration Manager taki sam sposób lokalnie czy klientów. Aby uzyskać więcej informacji, zobacz [jak monitorować klientów](/sccm/core/clients/manage/monitor-clients).



## <a name="monitor-traffic-in-the-console"></a>Monitorowanie ruchu w konsoli programu

Monitorowanie ruchu w bramie zarządzania chmury, za pomocą konsoli programu Configuration Manager:

1. Przejdź do **Administracja > usługi w chmurze > brama zarządzania w chmurze**.

2. Wybierz bramę zarządzania chmury w okienku listy.

3. Wyświetl informacje o ruchu w okienku szczegółów na punkt połączenia z chmurą zarządzania bramy i role systemu lokacji, z którą jest połączona.



## <a name="set-up-outbound-traffic-alerts"></a>Konfigurowanie alertów ruchu wychodzącego

Ruch wychodzący alertów pomagają wiedzieć, kiedy zbliża się do 14 dni progu ruchu sieciowego. Podczas tworzenia chmury bramy zarządzania można skonfigurować alerty ruchu. Jeśli ta część została pominięta, można nadal skonfigurować alerty po uruchomieniu usługi. Ustawienia alertów w dowolnym momencie.

1. Przejdź do **Administracja > usługi w chmurze > brama zarządzania w chmurze**.

2. Kliknij prawym przyciskiem myszy brama zarządzania chmury w okienku listy, a następnie wybierz pozycję **właściwości**.

3. Kliknij przycisk **alerty** kartę. Włącz progów i alertów. Określ próg 14-dniowym danych (w gigabajtach). Ponadto określ procentowy próg podnieść na różnych poziomach alertów.

4. Kliknij przycisk **OK** po zakończeniu.



## <a name="monitor-logs"></a>Dzienniki monitora

Brama zarządzania chmury generuje wpisy w plikach dziennika. Aby uzyskać więcej informacji, zobacz [dzienników programu Configuration Manager](/sccm/core/plan-design/hierarchy/log-files#cloud-management-gateway).
