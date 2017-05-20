---
title: "Hybrydowe zarządzanie urządzeniami przenośnymi (MDM) -, korzystając programu Configuration Manager i Microsoft Intune | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat zarządzania urządzeniami przenośnymi (MDM) hybrydowych za pomocą programu System Center Configuration Manager i Microsoft Intune."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: bb95154b-f63e-4491-896e-41d732c802f8
caps.latest.revision: 34
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: e54478a03807c939ffa64ff39a21ef6f9ea4ae2d
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="hybrid-mobile-device-management-mdm-with-system-center-configuration-manager-and-microsoft-intune"></a>Hybrydowe zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i usługi Microsoft Intune

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


Można zarządzać iOS, Windows i urządzeń z systemem Android za pomocą programu Configuration Manager i Microsoft Intune. Wszystkie zadania zarządzania są obsługiwane z poziomu konsoli programu Configuration Manager, gdzie wykonać pozostałe zadań zarządzania przez internet w pełni zintegrowana z usługi online Microsoft Intune.  Aby umożliwić użytkownikom dostęp do zasobów firmy na urządzeniach w sposób bezpieczny, zarządzanych, można użyć programu Configuration Manager. Dzięki zarządzaniu urządzeniami, pozwalając użytkownikom rejestrowanie swoich urządzeń osobistych lub firmowych, dostępu do danych firmy ochrony danych firmy. Możliwości zarządzania na urządzeniach:

-   Wycofywanie lub czyszczenie urządzeń.
-   Konfigurowanie ustawień zgodności, takich jak hasła, zabezpieczenia, roaming, szyfrowanie i komunikacja bezprzewodowa.
-   Wdrażanie aplikacji — biznesowych (LOB) na urządzeniach
-   Wdrażanie aplikacji na urządzeniach, które łączą się ze sklepami, takimi jak Sklep Windows, Sklep Windows Phone, App Store czy Google Play.
-   Zbieranie spisu sprzętu.
-   Zbieranie spisu oprogramowania za pomocą wbudowanych raportów.

Do odczytu, jakie nowe funkcje są dostępne dla hybrydowego zarządzania urządzeniami Przenośnymi, zobacz [What's new in zarządzania urządzeniami przenośnymi hybrydowe](../understand/whats-new-in-hybrid-mobile-device-management.md).

Tym dokumencie przyjęto założenie, że używasz programu Configuration Manager do zarządzania komputerami, i że planuje się rozszerzenie konsoli programu Configuration Manager za pomocą usługi Intune do zarządzania urządzeniami przenośnymi. Aby poznać różnice między Intune i hybrydowe zarządzanie urządzeniami przenośnymi, zobacz [wybierz między Microsoft Intune autonomiczne, jak i hybrydowe zarządzanie urządzeniami przenośnymi za pomocą System Center Configuration Manager](choose-between-standalone-intune-and-hybrid-mobile-device-management.md).

Po rozszerzeniu programu Configuration Manager za pomocą usługi Intune, możesz zarejestrować i zarządzanie firmowymi urządzeniami lub zezwolić użytkownikom na rejestrowanie swoich urządzeń osobistych. Można również zarządzać firmowych urządzeń za pomocą usługi Intune przy użyciu Menedżera konfiguracji.

## <a name="hybrid-mdm-enrollment"></a>Hybrydowe rejestracji MDM
Aby przywrócić hybrydowe zarządzanie urządzeniami, te wymaga zarejestrowania urządzeń z usługą. Jak urządzenia rejestrują urządzenia zależy od typu urządzenia, własność i poziom zarządzania potrzebne.
- "Strategię Przynieś własne urządzenie" (BYOD) rejestracji umożliwia użytkownikom rejestrowanie swoich osobistych telefonów, tabletów lub komputerami.
- Urządzenie należące (do firmy COD) rejestracji umożliwia scenariuszy zarządzania, takich jak wymazywania urządzenia udostępnione i koligacja urządzenia użytkownika.
- Jeśli używasz [programu Exchange ActiveSync](../plan-design/device-enrollment-methods.md#mobile-device-management-with-exchange-activesync-and-configuration-manager), albo lokalnie przechowywane w chmurze, można również włączyć prostego zarządzania usługi Intune bez rejestracji. Komputery z systemem Windows mogą być zarządzane przy użyciu [oprogramowania klienckiego usługi Intune](/intune/deploy-use/manage-windows-pcs-with-microsoft-intune).

