---
title: "Zdalnie synchronizować zasad na urządzeniach zarejestrowane w usłudze Intune | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak zsynchronizować zasad na urządzeniach zarejestrowanych Intune z konsoli programu Configuration Manager"
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b3731ad0-2a24-4042-994e-5e4c1230e3fe
caps.latest.revision: 18
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 337814fd5ba49ed17fc97aba49f79f02df817f4e
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="remotely-synchronize-policy-on-intune-enrolled-devices-from-the-configuration-manager-console"></a>Zdalnie synchronizować zasad na urządzeniach zarejestrowanych Intune z konsoli programu Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


Możesz poprosić o zasady synchronizacji urządzenia, które są zarejestrowane w usłudze Intune z konsoli programu Configuration Manager zamiast żądanie synchronizacji z aplikacji Portal firmy na urządzeniu. 

Wykonaj następujące czynności:

1.    Wybierz urządzenie pod adresem **zasoby i zgodność** > **Przegląd** > **urządzeń**.
2.    Kliknij przycisk **Wyślij żądanie synchronizacji** w **zdalnego akcji urządzenia** menu.


Po upływie pięciu do dziesięciu minut wszelkie zmiany w zasadach będą synchronizowane z urządzeniem. Można wyświetlić informacje o stanie żądania synchronizacji w nowej kolumnie w widokach urządzenia, o nazwie **stan synchronizacji zdalnego**, jak również w sekcji danych odnajdywania **właściwości** okno dialogowe dla każdego urządzenia.

