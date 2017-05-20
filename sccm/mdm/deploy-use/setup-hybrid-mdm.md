---
title: Instalator hybrydowe MDM | Dokumentacja firmy Microsoft
description: "Konfigurowanie rejestracji urządzeń hybrydowych przy użyciu programu Configuration Manager i usługi Intune."
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
ms.openlocfilehash: c494fcc38955571c06507278a1ae88e5777b5708
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---

# <a name="setup-hybrid-mobile-device-management-mdm-with-system-center-configuration-manager-and-microsoft-intune"></a>Konfiguracja zarządzania urządzeniami przenośnymi (MDM) hybrydowych za pomocą programu System Center Configuration Manager i Microsoft Intune

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


Aby można było zarządzać iOS, Windows i urządzeń z systemem Android za pomocą programu Configuration Manager, musi być zarejestrowany za pomocą usługi Intune. Wykonaj następujące kroki do rejestracji urządzeń hybrydowe Instalatora za pomocą programu Configuration Manager za pomocą usługi Intune. Wykonując poniższe czynności spowoduje włączenie "strategię Przynieś własne urządzenie" (BYOD) rejestracji dla użytkowników. Następujące kroki są również wymagania wstępne dotyczące [rejestrowanie urządzeń PRZYNIEŚ](enroll-hybrid-ios-mac.md) i [rejestrowanie firmowych urządzeń](enroll-company-owned-devices.md).

 |Kroki|Szczegóły|  
 |-----------|-------------|  
 |**Krok 1:** [Tworzenie kolekcji MDM](create-mdm-collection.md)|Tworzenie kolekcji użytkowników programu Configuration Manager z użytkowników, których urządzenia mogą być zarejestrowane|  
 |**Krok 2:** [Wymagania dotyczące nazw domen](confirm-dns.md)|Potwierdź organizacji usługi nazw domen (DNS) i usługi Active Directory użytkownika zarządzania spełnia wymagania dotyczące oprogramowania MDM|
 |**Krok 3:** [Skonfiguruj subskrypcję usługi Intune](configure-intune-subscription.md)|Usługa Intune umożliwia zarządzanie urządzeniami przez Internet.|  
 |**Krok 4:** [Dodaj warunki i postanowienia](terms-and-conditions.md)| Tworzenie warunków i postanowień, do których użytkownicy muszą wyrazić zgodę przed użyciem aplikacji Portal firmy|
 |**Krok 5.** [Utwórz punkt połączenia usługi](create-service-connection-point.md)|Punkt połączenia usługi wysyła ustawienia i informacje o wdrożeniu oprogramowania Configuration Manager i pobiera komunikaty o stanie i spisie z urządzeń przenośnych. |  
 |**Krok 6:** [Włącz rejestrowanie dla platformy](enable-platform-enrollment.md)|Rejestrowanie MDM dla urządzeń z systemem Windows i iOS wymagają dodatkowych kroków do komunikacji między usługą i urządzeń. Android nie wymaga dodatkowej konfiguracji.|  
 |**Krok 7:** [Konfigurowanie zarządzania dodatkowe](set-up-additional-management.md)|(Opcjonalnie) Ustawianie pozycji konfiguracji i dostępu warunkowego dla zarejestrowanych urządzeń|
 |**Krok 8.** [Weryfikowanie konfiguracji oprogramowania MDM](verify-mdm-configuration.md)|Wyświetl pliki dziennika o potwierdzenie, że pomyślnie utworzono punkt połączenia usługi i konta użytkowników synchronizacji.|

Szukasz Intune bez programu Configuration Manager?
> [!div class="button"]
[Wyświetlanie dokumentów Intune >](https://docs.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune)


## <a name="enroll-devices"></a>Rejestruj urządzenia
Po zakończeniu instalacji hybrydowe będzie można zarejestrować urządzeń w programie Configuration Manager na kilka sposobów:
- **Urządzenia należące do firmy (COD):** [Rejestrowanie urządzeń należących do firmy](enroll-company-owned-devices.md) znajdują się wskazówki dotyczące sposobów platformy do rejestrowania urządzeń należących do firmy.
- **Urządzenia należące do użytkownika (BYOD):** [Rejestrowanie urządzeń należących do użytkownika (BYOD)](enroll-hybrid-ios-mac.md) znajdują się wskazówki dotyczące sposobów, aby zarejestrować urządzenia należące do użytkownika.

