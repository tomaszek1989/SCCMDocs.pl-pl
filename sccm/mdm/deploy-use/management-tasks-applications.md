---
title: Zarządzanie aplikacjami
titleSuffix: Configuration Manager
description: Zarządzanie aplikacjami w programie System Center Configuration Manager.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 8adbe2e2-de26-4a80-8bbd-a5f34b8bac79
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 26aff6a374da4c6822943083b24c1a7ac04ee91d
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="manage-applications-in-system-center-configuration-manager"></a>Zarządzanie aplikacjami w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Zarządzanie urządzeniami za pomocą programu Microsoft Intune lub programu Configuration Manager zarządzanie urządzeniami lokalnymi, można zarządzać tych typów aplikacji dodatkowe:
- Pakiet aplikacji systemu Windows Phone (plik *.xap)
- Pakiet aplikacji dla systemu iOS (plik *.ipa)
- Pakiet aplikacji dla systemu Android (plik *.apk)
- Pakiet aplikacji dla systemu Android w sklepie Google Play
- Pakiet aplikacji systemu Windows Phone (w sklepie Windows Phone Store)
- Instalator systemu Windows korzystający z funkcji zarządzania urządzeniami przenośnymi (MDM)
- Aplikacja sieci Web

Ta sekcja zawiera szczegółowe informacje na temat tworzenia aplikacji i zarządzanie nimi przy użyciu hybrydowego zarządzania urządzeniami Przenośnymi lub lokalnego zarządzania urządzeniami przenośnymi.

[Zadania zarządzania dla aplikacji programu System Center Configuration Manager](../../apps/deploy-use/management-tasks-applications.md) zawiera więcej ogólnych informacji na temat zarządzania programu System Center Configuration Manager aplikacji i typów wdrożeń.

## <a name="deploying-and-monitoring-apps"></a>Wdrażania i monitorowania aplikacji

Wdrażanie i monitorowanie aplikacji w programie System Center Configuration Manager są tego samego procesu dla urządzeń przenośnych, jak w przypadku urządzeń na miejscu, takich jak komputerów przenośnych i stacjonarnych. Można przeczytać z poniższymi tematami, aby uzyskać ogólne informacje na temat wdrażania i monitorowania aplikacji:

- [Wdrażanie aplikacji w programie System Center Configuration Manager](../../apps/deploy-use/deploy-applications.md)
- [Monitorowanie aplikacji w programie System Center Configuration Manager](../../apps/deploy-use/monitor-applications-from-the-console.md)

Poniżej przedstawiono pewne kwestie do uwzględnienia podczas wdrażania i monitorowania aplikacji, specyficzne dla zarządzania urządzeniami przenośnymi.

- Urządzenia zarejestrowane MDM nie obsługują wdrożenia symulowane, użytkowników lub ustawień planowania.

- Jeśli masz już congured, co można skojarzyć wdrożenia przy użyciu zasad konfiguracji aplikacji systemu iOS. Zobacz [Konfigurowanie aplikacji systemu iOS przy użyciu zasad konfiguracji aplikacji](configure-ios-apps-with-app-configuration-policies.md).

### <a name="next-steps"></a>Następne kroki

Po pewnym czasie można wprowadzać zmian w aplikacji, odinstalowanie aplikacji lub Zastąp już wdrożonej aplikacji przez nową aplikację. Zapoznaj się z artykułem [aktualizacji i wycofywania aplikacji w programie System Center Configuration Manager](../../apps/deploy-use/update-and-retire-applications.md) zrozumieć tych możliwości.
