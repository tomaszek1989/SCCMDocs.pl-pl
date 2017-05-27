---
title: "Zarządzanie aplikacjami programu System Center Configuration Manager | Dokumentacja firmy Microsoft"
description: "Zarządzanie aplikacjami programu System Center Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 8adbe2e2-de26-4a80-8bbd-a5f34b8bac79
caps.latest.revision: 18
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: bc7bb99bc526ed0bbaaad15fc9af39fa8b7c3893
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="manage-applications-in-system-center-configuration-manager"></a>Zarządzanie aplikacjami programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Zarządzanie urządzeniami za pomocą programu Microsoft Intune lub programu Configuration Manager lokalnego zarządzania urządzeniami można zarządzać tych typów aplikacji dodatkowe:
- Pakiet aplikacji systemu Windows Phone (plik *.xap)
- Pakiet aplikacji dla systemu iOS (plik *.ipa)
- Pakiet aplikacji dla systemu Android (plik *.apk)
- Pakiet aplikacji dla systemu Android w sklepie Google Play
- Pakiet aplikacji systemu Windows Phone (w sklepie Windows Phone Store)
- Instalator systemu Windows korzystający z funkcji zarządzania urządzeniami przenośnymi (MDM)
- Aplikacja sieci Web

Ta sekcja zawiera szczegółowe informacje dotyczące tworzenia aplikacji i zarządzania nimi przy użyciu hybrydowe MDM lub lokalnego zarządzania urządzeniami przenośnymi.

[Zadania zarządzania dla programu System Center Configuration Manager aplikacji](../../apps/deploy-use/management-tasks-applications.md) bardziej ogólne informacje o zarządzaniu aplikacji System Center Configuration Manager i typów wdrożeń.

## <a name="deploying-and-monitoring-apps"></a>Wdrażanie i monitorowanie aplikacji

Wdrażanie i monitorowanie aplikacji w programie System Center Configuration Manager są tego samego procesu dla urządzeń przenośnych, jak dla urządzenia na miejscu, na przykład komputerów przenośnych i stacjonarnych. Należy zapoznać się z poniższymi tematami ogólne informacje na temat wdrażania i monitorowania aplikacji:

- [Wdrażanie aplikacji w programie System Center Configuration Manager](../../apps/deploy-use/deploy-applications.md)
- [Monitorowanie aplikacji w programie System Center Configuration Manager](../../apps/deploy-use/monitor-applications-from-the-console.md)

Poniżej przedstawiono kilka dodatkowych kwestii, które należy uwzględnić podczas wdrażania i monitorowania aplikacji, specyficzne dla zarządzania urządzeniami przenośnymi.

- Urządzenia zarejestrowane MDM nie obsługują wdrożenia symulowane, czynności użytkownika lub ustawień planowania.

- Wdrożenie można skojarzyć z zasad konfiguracji systemu iOS aplikacji, jeśli już masz congured jeden. Zobacz [skonfigurowanie aplikacji systemu iOS z zasady konfiguracji aplikacji](configure-ios-apps-with-app-configuration-policies.md).

### <a name="next-steps"></a>Następne kroki

Ostatecznie można wprowadzać zmian w aplikacji, odinstalować aplikację lub wymiana już wdrożonych aplikacji z nowej aplikacji. Zapoznaj się z artykułem [aktualizacji i wycofywania aplikacji z System Center Configuration Manager](../../apps/deploy-use/update-and-retire-applications.md) zrozumienie tych funkcji.

