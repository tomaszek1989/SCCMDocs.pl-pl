---
title: Instalator hybrydowego zarządzania urządzeniami Przenośnymi
titleSuffix: Configuration Manager
description: Skonfiguruj hybrydowych rejestracji urządzeń z programu Configuration Manager i usługi Intune.
ms.date: 03/08/2018
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: bb95154b-f63e-4491-896e-41d732c802f8
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: fbc5b9abf63d95185795716cfcb9ebfaf3e2ec3d
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="setup-hybrid-mobile-device-management-mdm-with-system-center-configuration-manager-and-microsoft-intune"></a>Konfiguracja hybrydowego zarządzania urządzeniami przenośnymi (MDM) z programu System Center Configuration Manager i Microsoft Intune

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


Aby można było zarządzać systemu iOS, Windows i urządzeń z systemem Android z programem Configuration Manager, muszą być zarejestrowane przy użyciu usługi Intune. Wykonaj następujące kroki do skonfigurowania hybrydowego urządzenia rejestracji z programem Configuration Manager przy użyciu usługi Intune. Przez wykonanie następujących kroków spowoduje włączenie "Przynieś własne urządzenie" (BYOD) rejestracji dla użytkowników. Te kroki są również wymagania wstępne dotyczące [rejestracja urządzeń BYOD](enroll-hybrid-ios-mac.md) i [rejestrowanie urządzeń należących do firmy](enroll-company-owned-devices.md).

 |Kroki|Szczegóły|  
 |-----------|-------------|  
 |**Krok 1.** [Tworzenie kolekcji funkcji MDM](create-mdm-collection.md)|Utwórz kolekcję użytkownika programu Configuration Manager z użytkownikami, których urządzenia mogą być rejestrowane.|  
 |**Krok 2.** [Wymagania dotyczące nazw domen](confirm-dns.md)|Potwierdź usługi organizacji domain name service (DNS) i zarządzania usługą Active Directory użytkownika spełnia wymagania dotyczące zarządzania urządzeniami Przenośnymi|
 |**Krok 3.** [Konfigurowanie subskrypcji usługi Intune](configure-intune-subscription.md)|Usługa Intune umożliwia zarządzanie urządzeniami za pośrednictwem Internetu.|  
 |**Krok 4.** [Dodawanie warunków i postanowień](terms-and-conditions.md)| Tworzenie warunków i postanowień, do których użytkownicy muszą wyrazić zgodę przed użyciem aplikacji Portal firmy|
 |**Krok 5.** [Tworzenie punktu połączenia z usługą](create-service-connection-point.md)|Punkt połączenia z usługą wysyła ustawienia i informacje o wdrożeniu oprogramowania do programu Configuration Manager i pobiera komunikaty o stanie i spisie z urządzeń przenośnych. |  
 |**Krok 6.** [Włączanie rejestrowania platformy](enable-platform-enrollment.md)|Rejestrowanie MDM dla systemu iOS i urządzeniach z systemem Windows wymagają dodatkowych czynności do komunikacji między usługą i urządzeń. Android nie wymaga dodatkowej konfiguracji.|  
 |**Krok 7.** [Konfigurowanie dodatkowego zarządzania](set-up-additional-management.md)|(Opcjonalnie) Konfigurowanie elementów konfiguracji i dostępu warunkowego dla zarejestrowanych urządzeń|
 |**Krok 8.** [Weryfikowanie konfiguracji funkcji MDM](verify-mdm-configuration.md)|Wyświetl pliki dziennika, aby upewnić się, że pomyślnie utworzono punkt połączenia usługi i konta użytkowników są synchronizacji.|

Szukasz Intune bez programu Configuration Manager?
> [!div class="button"]
[Wyświetlanie dokumentów w usłudze Intune >](https://docs.microsoft.com/intune/deploy-use/enroll-devices-in-microsoft-intune)


## <a name="enroll-devices"></a>Rejestruj urządzenia
Po zakończeniu instalacji hybrydowego urządzenia mogą być rejestrowane w programie Configuration Manager na kilka sposobów:
- **Urządzenia należące do firmy (COD):** [Rejestrowanie urządzeń należących do firmy](enroll-company-owned-devices.md) znajdują się wskazówki dotyczące różnych sposobów specyficzne dla platformy rejestrować urządzenia należące do firmy.
- **Urządzenia należące do użytkowników (BYOD):** [Rejestrowanie urządzeń należących do użytkowników (BYOD)](enroll-hybrid-ios-mac.md) znajdują się wskazówki dotyczące sposobów, aby rejestrować urządzenia należące do użytkownika.
