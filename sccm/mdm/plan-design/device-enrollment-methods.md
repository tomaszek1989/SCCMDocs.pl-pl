---
title: "Metody rejestracji urządzeń dla hybrydowego MDM | Dokumentacja firmy Microsoft"
description: "Metody rejestracji urządzeń dla hybrydowego zarządzania urządzeniami przenośnymi."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: b81d06dc-3844-4117-9937-16732a227994
caps.latest.revision: 9
caps.handback.revision: 0
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: e09e639e939b846cdc162681f9d7bd4c39cd6fbf
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="overview-of-device-enrollment-methods"></a>Przegląd metod rejestracji urządzenia

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Po rozszerzeniu programu Configuration Manager za pomocą usługi Intune można zarejestrować i zarządzanie firmowymi urządzeniami lub zezwolić użytkownikom na rejestrowanie swoich urządzeń osobistych. Można również zarządzać firmowych urządzeń za pomocą usługi Intune przy użyciu Menedżera konfiguracji.

W poniższej tabeli przedstawiono metody rejestracji z ich możliwości obsługiwane. Te funkcje obejmują:
- **Czyszczenie** -fabryki zresetowania urządzenia, usunięcie wszystkich danych. [Wycofywać urządzeń](../deploy-use/wipe-lock-reset-devices.md)
- **Koligacja** -kojarzy urządzeń użytkowników. Wymagane w celu zarządzania aplikacjami mobilnymi (MAM) i warunkowego dostępu do danych firmowych. [Koligację użytkownika](../deploy-use/user-affinity-for-hybrid-managed-devices.md)
- **Zablokuj** uniemożliwia użytkownikom usunięcie urządzenia z zarządzania. urządzenia z systemem iOS wymaga trybu Supervised do blokady. [Zdalne blokowanie](../deploy-use/wipe-lock-reset-devices.md#remote-lock)

**metody rejestracji systemu iOS**

| **Metoda** |    **Czyszczenie danych** |    **Koligacja**    |    **Blokady** | **Szczegóły** |
|:---:|:---:|:---:|:---:|:---:|
|**[PRZYNIEŚ](#byod)** | Nie|    Tak |    Nie | [więcej](../deploy-use/enable-platform-enrollment.md)|
|**[DEM](#dem)**|    Nie |Nie |Nie    | [więcej](../deploy-use/enroll-devices-with-device-enrollment-manager.md)|
|**[DEP](#dep)**|    Tak |    Opcjonalne |    Opcjonalne|[więcej](../deploy-use/ios-device-enrollment-program-for-hybrid.md)|
|**[USB SA](#usb-sa)**|    Tak |    Opcjonalne |    Nie| [więcej](../deploy-use/ios-hybrid-enrollment-using-apple-configurator.md)|

**System Windows i metody rejestracji systemu Android**

| **Metoda** |    **Czyszczenie danych** |    **Koligacja**    |    **Blokady** | **Szczegóły**|
|:---:|:---:|:---:|:---:|:---:|:---:|
|**[PRZYNIEŚ](#byod)** | Nie|    Tak |    Nie | [więcej](../deploy-use/enroll-hybrid-windows.md)|
|**[DEM](#dem)**|    Nie |Nie |Nie    |[więcej](../deploy-use/enroll-devices-with-device-enrollment-manager.md)|

Na szereg pytań, które pomagają znaleźć właściwej metody, zobacz [wybierz jak zarejestrować urządzenia](/intune/get-started/choose-how-to-enroll-devices1).

## <a name="byod"></a>PRZYNIEŚ
"Strategię Przynieś własne urządzenie" (BYOD) użytkownicy zainstaluj aplikację Portal firmy i zarejestrować swoje urządzenie. To pozwolić użytkownikom nawiązywanie połączeń z siecią firmową, dołączania do domeny lub Azure Active Directory. Włączanie PRZYNIEŚ rejestracji jest wymagane w wielu scenariuszach COD dla większości platform. Zobacz [Instalatora hybrydowe MDM](../deploy-use/setup-hybrid-mdm.md). ([Do tabeli](#overview-of-device-enrollment-methods))

## <a name="corporate-owned-devices"></a>Urządzenia należące do firmy
Urządzenia należące (do firmy COD) można zarządzać za pomocą konsoli programu Configuration Manager. urządzenia z systemem iOS można rejestrować bezpośrednio za pomocą narzędzi dostarczanych przez firmę Apple. Wszystkich typów urządzeń mogą być rejestrowane przez administratora lub Menedżera przy użyciu Menedżera rejestracji urządzeń. Urządzenia z liczbą IMEI można również zidentyfikować i oznaczonymi jako należące do firmy do włączenia COD scenariuszy.

[Rejestrowanie firmowych urządzeń](../deploy-use/enroll-company-owned-devices.md)

### <a name="dem"></a>DEM
Menedżer rejestracji urządzeń to specjalne konto użytkownika używane do rejestrowania i zarządzanie wieloma urządzeniami firmowych. Menedżerowie mogą zainstalować aplikację Portal firmy i zarejestrować wiele urządzenia bez użytkowników. Dowiedz się więcej o [DEM](../deploy-use/enroll-devices-with-device-enrollment-manager.md). ([Do tabeli](#overview-of-device-enrollment-methods))

### <a name="dep"></a>DEP
Zarządzania Apple Device Enrollment Program (DEP) umożliwia tworzenie i wdrażanie zasad "bezprzewodowo" urządzeniach z systemem iOS kupionymi i zarządzane przy użyciu usługi DEP. Urządzenie jest zarejestrowane, gdy użytkownik przechodzi na urządzeniu po raz pierwszy i nie uruchomi Asystenta ustawień systemu iOS. Ta metoda obsługuje **iOS Supervised** tryb, który z kolei umożliwia:
  -    Zablokowane rejestracji
  -    Dostęp warunkowy
  -    Wykrywanie zdjęcia
  -    Zarządzanie aplikacjami mobilnymi

Dowiedz się więcej o [DEP](../deploy-use/ios-device-enrollment-program-for-hybrid.md). ([Do tabeli](#overview-of-device-enrollment-methods))

### <a name="usb-sa"></a>USB SA
Połączenie USB, Asystenta rejestracji. Administrator tworzy zasadę i eksportuje do programu Apple Configurator. Należy przygotować połączenie USB, firmowe urządzenia z zasadami. Administrator musi ręcznie zarejestrować każdego urządzenia. Użytkownicy otrzymywać swoje urządzenia i uruchomić Asystenta, rejestrowanie swoich urządzeń. Ta metoda obsługuje **iOS Supervised** tryb, który z kolei umożliwia:
  -    Dostęp warunkowy
  -    Wykrywanie zdjęcia
  -    Zarządzanie aplikacjami mobilnymi

Dowiedz się więcej o [Asystenta rejestracji przy użyciu programu Apple Configurator](../deploy-use/ios-hybrid-enrollment-using-apple-configurator.md). ([Do tabeli](#overview-of-device-enrollment-methods))

## <a name="mobile-device-management-with-exchange-activesync-and-configuration-manager"></a>Zarządzanie urządzeniami przenośnymi za pomocą programu Exchange ActiveSync i programu Configuration Manager
Urządzenia przenośne, które nie są zarejestrowane, ale który połączenia protokołu Exchange ActiveSync (EAS) można zarządzać przez usługę Intune za pomocą zasad EAS MDM. Intune używa łącznika programu Exchange do komunikacji z EAS, albo lokalnych i hostowanych w chmurze.

[Zarządzanie urządzeniami przenośnymi za pomocą programu Exchange ActiveSync i Intune](../deploy-use/manage-mobile-devices-with-exchange-activesync.md)

