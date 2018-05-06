---
title: Hybrydowe zarządzanie urządzeniami przenośnymi (MDM) w usłudze Microsoft Intune
titleSuffix: Configuration Manager
description: Więcej informacji na temat hybrydowego zarządzania urządzeniami przenośnymi (MDM) z programu System Center Configuration Manager i Microsoft Intune.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: bb95154b-f63e-4491-896e-41d732c802f8
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: c8651b5a82c4e3cb4e39fac53cc5bc3357df6e47
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="hybrid-mobile-device-management-mdm-with-system-center-configuration-manager-and-microsoft-intune"></a>Hybrydowe zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i usługi Microsoft Intune

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


Można zarządzać z systemem iOS, Windows i urządzeń z systemem Android z programu Configuration Manager i Microsoft Intune. Wszystkie zadania zarządzania są obsługiwane z poziomu konsoli programu Configuration Manager, gdzie wykonać reszty zadań zarządzania za pośrednictwem Internetu w pełni zintegrowana z usługi online Microsoft Intune.  Można użyć programu Configuration Manager, aby umożliwić użytkownikom dostęp do zasobów firmowych na swoich urządzeniach w sposób bezpiecznego, zarządzanego. Przy użyciu zarządzania urządzeniami, możesz chronić dane firmy, pozwalając użytkownikom rejestrowanie swoich urządzeń osobistych lub będących własnością firmy dostępu do danych firmowych. Możliwości zarządzania na urządzeniach:

-   Wycofywanie lub czyszczenie urządzeń.
-   Konfigurowanie ustawień zgodności, takich jak hasła, zabezpieczenia, roaming, szyfrowanie i komunikacja bezprzewodowa.
-   Wdrażanie aplikacji — biznesowych (LOB) na urządzeniach
-   Wdrażanie aplikacji na urządzeniach, które łączą się ze sklepami, takimi jak Sklep Windows, Sklep Windows Phone, App Store czy Google Play.
-   Zbieranie spisu sprzętu.
-   Zbieranie spisu oprogramowania za pomocą wbudowanych raportów.

Jakie nowe funkcje są dostępne w hybrydowym rozwiązaniu MDM zamieszczono w [What's new in hybrydowego zarządzania urządzeniami przenośnymi](../understand/whats-new-in-hybrid-mobile-device-management.md).

Tym dokumencie przyjęto założenie, że używasz programu Configuration Manager do zarządzania komputerami, i że planuje się rozszerzenie konsoli programu Configuration Manager przy użyciu usługi Intune do zarządzania urządzeniami przenośnymi. Aby poznać różnice między usługą Intune i hybrydowego wdrożenia zarządzania urządzeniami przenośnymi, zobacz [wybór między Microsoft Intune autonomiczne, jak i hybrydowe zarządzanie urządzeniami przenośnymi z System Center Configuration Manager](choose-between-standalone-intune-and-hybrid-mobile-device-management.md).

Po rozszerzeniu programu Configuration Manager z usługą Intune, możesz zarejestrować i zarządzania firmowymi urządzeniami lub zezwolić użytkownikom na rejestrowanie swoich urządzeń osobistych. Można również zarządzać urządzeniami należącymi do firmy przy użyciu usługi Intune przy użyciu programu Configuration Manager.

## <a name="hybrid-mdm-enrollment"></a>Hybrydowe zarządzanie urządzeniami Przenośnymi rejestracji
Do zapewnienia hybrydowego zarządzania urządzeniami, te urządzenia muszą być zarejestrowane w usłudze. Jak urządzenia rejestrowania urządzeń zależy od tego, typu urządzenia, własność i poziom zarządzania wymagane.
- "Przynieś własne urządzenie" (BYOD) rejestracji użytkownicy mogą rejestrować swoje osobiste telefonów, tabletów lub komputerów.
- Rejestracja urządzenia firmowe (COD) umożliwia scenariusze zarządzania, takie jak zdalne czyszczenie, urządzeń współużytkowanych lub koligacji użytkownika dla urządzenia.
- Jeśli używasz [programu Exchange ActiveSync](../plan-design/device-enrollment-methods.md#mobile-device-management-with-exchange-activesync-and-configuration-manager), lokalnie hostowanych w chmurze, można też włączyć proste zarządzanie bez rejestracji w usłudze Intune. Komputery z systemem Windows można także zarządzać za pomocą [oprogramowania klienckiego usługi Intune](/intune/deploy-use/manage-windows-pcs-with-microsoft-intune).
