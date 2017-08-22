---
title: "Brama zarządzania chmury Monitor — programu Configuration Manager | Dokumentacja firmy Microsoft"
description: 
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.assetid: 15f72f80-9850-40ce-9c3a-443ba04b6a03
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: daa0790995dc13ec2c78ae2d98a9eb38c0bcf8ae
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="monitor-cloud-management-gateway-in-configuration-manager"></a>Monitor bramy zarządzania w chmurze w programie Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Począwszy od wersji 1610, po działa Usługa bramy zarządzania w chmurze i łączenia klientów z przy jego użyciu, można monitorować klientów i ruchu sieciowego, aby upewnić się, że wiesz, jak działa usługa.

## <a name="monitor-clients"></a>Monitor klientów

Klienci połączeni za pośrednictwem usługi bramy zarządzania w chmurze są wyświetlane w taki sam sposób lokalnych klientów do konsoli programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [jak monitorować klientów](monitor-clients.md).

## <a name="monitor-traffic-in-the-console"></a>Monitorowanie ruchu w konsoli programu

Umożliwia monitorowanie ruchu w bramie zarządzania chmury przy użyciu konsoli programu Configuration Manager:

1. Przejdź do **Administracja > usługi w chmurze > brama zarządzania w chmurze**.

2. Wybierz usługę w chmurze zarządzania bramy w okienku listy.

3. Wyświetl informacje o ruchu w okienku szczegółów dla roli połączenia bramy zarządzania chmury i role systemu lokacji, z którą jest połączona.

## <a name="set-up-outbound-traffic-alerts"></a>Konfigurowanie alertów ruchu wychodzącego

Ruch wychodzący alerty ułatwiają wiedzieć, gdy zbliża się 14 dni (2 tygodniu) progu ruchu. Możesz skorzystać z opcji konfigurowania alertów ruchu podczas tworzenia usługi bramy zarządzania w chmurze. Jeśli ta część została pominięta, można nadal skonfigurować alerty po uruchomieniu usługi. A także można dostosować ustawienia alertów w dowolnym momencie.

1. Przejdź do **Administracja > usługi w chmurze > brama zarządzania w chmurze**.

2. Kliknij prawym przyciskiem myszy usługę bramy w chmurze zarządzania w okienku listy, a następnie wybierz pozycję **właściwości**.

3. Kliknij kartę alerty i chcesz włączyć (lub wyłączyć) progów i alertów. Następnie określ próg 14 dni (w GB) i wartości procentowe progu do podniesienia na różnych poziomach alertów.

4. Kliknij przycisk **OK** po zakończeniu.

## <a name="monitor-logs"></a>Dzienniki monitora

Usługi w chmurze zarządzania bramy generuje wpisy w plikach dziennika. Aby uzyskać więcej informacji, zobacz [dzienników programu Configuration Manager](/sccm/core/plan-design/hierarchy/log-files).
