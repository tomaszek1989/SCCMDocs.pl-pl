---
title: "Brama zarządzania chmury Monitor — Configuration Manager | Dokumentacja firmy Microsoft"
description: 
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-client
ms.assetid: 15f72f80-9850-40ce-9c3a-443ba04b6a03
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: daa0790995dc13ec2c78ae2d98a9eb38c0bcf8ae
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---

# <a name="monitor-cloud-management-gateway-in-configuration-manager"></a>Monitor bramy zarządzania chmury w programie Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Począwszy od wersji 1610 po chmury zarządzania bramą jest uruchomiona i za jego pośrednictwem łączą klienci, można monitorować klientów i ruchu sieciowym upewnij się, że wiesz, jak działa usługa.

## <a name="monitor-clients"></a>Monitor klientów

Klienci połączone za pośrednictwem usługi bramy zarządzania w chmurze są wyświetlane w konsoli programu Configuration Manager w taki sam sposób lokalnego do klientów. Aby uzyskać więcej informacji, zobacz [jak monitorować klientów](monitor-clients.md).

## <a name="monitor-traffic-in-the-console"></a>Monitor ruchu w konsoli

Można monitorować ruch w chmurze brama zarządzania przy użyciu konsoli programu Configuration Manager:

1. Przejdź do **Administracja > usługi w chmurze > chmury brama zarządzania**.

2. Wybierz usługę chmury zarządzania bramy w okienku listy.

3. Wyświetl informacje o ruchu w okienku szczegółów dla roli połączenia chmury zarządzania bramą i role systemu lokacji, z którą jest połączona.

## <a name="set-up-outbound-traffic-alerts"></a>Ustawianie alertów ruchu wychodzącego

Alerty ruch wychodzący pomoże Ci wiedzieć, gdy zbliża się ruchu progu (2 tygodniu) 14 dni. Konfigurowanie alertów ruchu podczas tworzenia usługi bramy zarządzania w chmurze są możliwość. Jeżeli pominięto tę część nadal zdefiniowaniem alerty po usługa jest uruchomiona. A także można dostosować ustawienia alertów w dowolnym momencie.

1. Przejdź do **Administracja > usługi w chmurze > chmury brama zarządzania**.

2. Kliknij prawym przyciskiem myszy usługę bramy w chmurze zarządzania w okienku listy, a następnie wybierz **właściwości**.

3. Kliknij kartę alerty i chcesz włączyć (lub wyłączyć) progów i alertów. Następnie określ próg 14 dni (w GB) i wartości procentowe progu dla występowanie różnych poziomów alertów.

4. Kliknij przycisk **OK** po zakończeniu.

## <a name="monitor-logs"></a>Dzienniki monitora

Usługa bramy zarządzania chmury generuje wpisów w plikach dziennika. Aby uzyskać więcej informacji, zobacz [dzienników programu Configuration Manager](/sccm/core/plan-design/hierarchy/log-files).

