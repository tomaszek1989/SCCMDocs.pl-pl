---
title: "Metody rejestracji urządzeń w hybrydowym rozwiązaniu MDM"
titleSuffix: Configuration Manager
description: "Metody rejestracji urządzeń dla hybrydowego zarządzania urządzeniami przenośnymi."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: b81d06dc-3844-4117-9937-16732a227994
caps.latest.revision: "9"
caps.handback.revision: "0"
author: dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 180f7699f184779d98db5ccedb296b409a119a30
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="overview-of-device-enrollment-methods"></a>Przegląd metod rejestracji urządzeń

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Po rozszerzeniu programu Configuration Manager z usługą Intune można rejestrować i zarządzanie urządzeniami firmowymi lub zezwolić użytkownikom na rejestrowanie swoich urządzeń osobistych. Można również zarządzać urządzeniami należącymi do firmy przy użyciu usługi Intune przy użyciu programu Configuration Manager.

W poniższej tabeli przedstawiono metody rejestracji z ich obsługiwane możliwości. Te możliwości to m.in.:
- **Czyszczenie** -fabryki zresetowania urządzenia, usunięcie wszystkich danych. [Wycofywanie urządzeń](../deploy-use/wipe-lock-reset-devices.md)
- **Koligacja** -kojarzy urządzeń użytkowników. Wymagane do zarządzania aplikacjami mobilnymi (MAM) i warunkowego dostępu do danych firmowych. [Koligację użytkownika](../deploy-use/user-affinity-for-hybrid-managed-devices.md)
- **Zablokuj** uniemożliwia użytkownikom usunięcie urządzenia z zarządzania. urządzenia z systemem iOS wymaga nadzorowane tryb blokady. [Zdalne blokowanie](../deploy-use/wipe-lock-reset-devices.md#remote-lock)

**metody rejestracji systemu iOS**

| **— Metoda** |  **Czyszczenie danych** |  **Koligacji**    |   **Blokady** | **Szczegóły** |
|:---:|:---:|:---:|:---:|:---:|
|**[MODEL BYOD](#byod)** | Nie|    Tak |   Nie | [więcej](../deploy-use/enable-platform-enrollment.md)|
|**[MENEDŻER REJESTRACJI URZĄDZEŃ](#dem)**|   Nie |Nie |Nie  | [więcej](../deploy-use/enroll-devices-with-device-enrollment-manager.md)|
|**[DEP](#dep)**|   Tak |   Opcjonalne |  Opcjonalne|[więcej](../deploy-use/ios-device-enrollment-program-for-hybrid.md)|
|**[USB-SA](#usb-sa)**| Tak |   Opcjonalne |  Nie| [więcej](../deploy-use/ios-hybrid-enrollment-using-apple-configurator.md)|

**System Windows i metody rejestracji systemu Android**

| **— Metoda** |  **Czyszczenie danych** |  **Koligacji**    |   **Blokady** | **Szczegóły**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[MODEL BYOD](#byod)** | Nie|    Tak |   Nie | [więcej](../deploy-use/enroll-hybrid-windows.md)|
|**[MENEDŻER REJESTRACJI URZĄDZEŃ](#dem)**|   Nie |Nie |Nie  |[więcej](../deploy-use/enroll-devices-with-device-enrollment-manager.md)|

Na szereg pytań, które pomagają znaleźć właściwej metody, zobacz [Wybieranie metody rejestrowania urządzeń](/intune/get-started/choose-how-to-enroll-devices1).

## <a name="byod"></a>MODEL BYOD
"Przynieś własne urządzenie" (BYOD) użytkownicy instalować aplikację Portal firmy i zarejestrować swoje urządzenia. To pozwolić użytkownikom nawiązywanie połączeń z firmową siecią dołączania do domeny lub usługi Azure Active Directory. Włączanie BYOD rejestracji jest wymagane w różnych scenariuszach COD dla większości platform. Zobacz [Instalatora hybrydowego zarządzania urządzeniami Przenośnymi](../deploy-use/setup-hybrid-mdm.md). ([Powrót do tabeli](#overview-of-device-enrollment-methods))

## <a name="corporate-owned-devices"></a>Urządzenia należące do firmy
Urządzenia należące do firmy (COD) można zarządzać za pomocą konsoli programu Configuration Manager. urządzenia z systemem iOS można zarejestrować bezpośrednio za pomocą narzędzi dostarczanych przez firmę Apple. Wszystkie typy urządzeń mogą być rejestrowane przez administratora lub Menedżera za pomocą Menedżera rejestracji urządzeń. Urządzeń numerami IMEI można również zidentyfikować i oznaczone jako należące do firmy na potrzeby scenariuszy z COD.

[Rejestrowanie firmowych urządzeń](../deploy-use/enroll-company-owned-devices.md)

### <a name="dem"></a>MENEDŻER REJESTRACJI URZĄDZEŃ
Menedżer rejestracji urządzeń to specjalne konto użytkownika używane do rejestrowania i zarządzanie wieloma urządzeniami firmowymi. Menedżerowie mogą zainstalować aplikację Portal firmy i zarejestrować wiele urządzeń bez użytkowników. Dowiedz się więcej o [DEM](../deploy-use/enroll-devices-with-device-enrollment-manager.md). ([Powrót do tabeli](#overview-of-device-enrollment-methods))

### <a name="dep"></a>DEP
Zarządzania programu Apple Device Enrollment Program (DEP) umożliwia tworzenie i wdrażanie zasad "za pośrednictwem udziału użytkownika, na urządzeniach z systemem iOS zakupionych i zarządzanych w ramach programu DEP. Urządzenie jest zarejestrowane, gdy użytkownik zmieni się na urządzeniu po raz pierwszy i uruchamia Asystenta ustawień systemu iOS. Ta metoda obsługuje **nadzorcy systemu iOS** tryb, który z kolei umożliwia:
  - Rejestrację zablokowaną
  - Dostęp warunkowy
  - Wykrywanie zdjęcia zabezpieczeń systemu
  - Zarządzanie aplikacjami mobilnymi

Dowiedz się więcej o [DEP](../deploy-use/ios-device-enrollment-program-for-hybrid.md). ([Powrót do tabeli](#overview-of-device-enrollment-methods))

### <a name="usb-sa"></a>USB-SA
Połączenie USB, rejestracja Asystenta ustawień. Administrator tworzy zasady i eksportuje je do programu Apple Configurator. Urządzeń firmowych, połączenie USB są przygotowywane za pomocą zasad. Administrator musi ręcznie zarejestrować każde urządzenie. Użytkownicy odbierają swoje urządzenia i uruchamiają Asystenta ustawień, rejestrowanie swojego urządzenia. Ta metoda obsługuje **nadzorcy systemu iOS** tryb, który z kolei umożliwia:
  - Dostęp warunkowy
  - Wykrywanie zdjęcia zabezpieczeń systemu
  - Zarządzanie aplikacjami mobilnymi

Dowiedz się więcej o [rejestracja Asystenta ustawień przy użyciu narzędzia Apple Configurator](../deploy-use/ios-hybrid-enrollment-using-apple-configurator.md). ([Powrót do tabeli](#overview-of-device-enrollment-methods))

## <a name="mobile-device-management-with-exchange-activesync-and-configuration-manager"></a>Zarządzanie urządzeniami przenośnymi za pomocą programu Exchange ActiveSync i programu Configuration Manager
Urządzenia przenośne, które nie są zarejestrowane, ale który połączenia protokołu Exchange ActiveSync (EAS) mogą być zarządzane przez usługę Intune przy użyciu zasad zarządzania urządzeniami Przenośnymi EAS. Usługa Intune używa łącznika programu Exchange do komunikowania się z programem EAS lokalnie i hostowanych w chmurze.

[Zarządzanie urządzeniami przenośnymi za pomocą programu Exchange ActiveSync i usługi Intune](../deploy-use/manage-mobile-devices-with-exchange-activesync.md)
