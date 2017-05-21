---
title: "Rejestrowanie firmowych urządzeń - programu Configuration Manager | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat różnych metod rejestrowanie firmowych urządzeń do wdrożenia hybrydowego z programu Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e2754ce6-1460-4ddd-9050-2cc87e7964f4
caps.latest.revision: 13
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: f0b503d8c9eba2dd1b6eb4c41ec40c001b727326
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="enroll-company-owned-devices-for-hybrid-deployments-with-configuration-manager"></a>Rejestrowanie firmowych urządzeń do wdrożenia hybrydowego z programu Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Organizacja lub urządzenia należące (do firmy COD) może być wprowadzana do zarządzania w różny sposób w zależności od urządzenia, a także jak zostało zakupione.  

## <a name="enroll-device-enrollment-program-ios-devices"></a>Rejestrowanie urządzeń iOS Device Enrollment Program  
 Wdraża profil rejestracji "bezprzewodowo" urządzenia zakupione w ramach programu Device Enrollment Program firmy Apple. Gdy użytkownik uruchomi Asystenta ustawień urządzenia, urządzenie jest zarejestrowane w usłudze Intune.  Urządzenia zarejestrowane w programie DEP nie mogą zostać wyrejestrowane przez użytkowników. Zobacz [iOS Device Enrollment Program (DEP) rejestracji dla wdrożenia hybrydowego z programu Configuration Manager](../../mdm/deploy-use/ios-device-enrollment-program-for-hybrid.md).  

## <a name="enroll-ios-devices-with-apple-configurator"></a>Rejestrowanie urządzeń z systemem iOS przy użyciu narzędzia Apple Configurator  
 Ta metoda wymaga administratorowi USB nawiązać komputer Mac z systemem Apple Configurator, aby wstępnie skonfigurować rejestrowanie na urządzeniu. Urządzenia są następnie dostarczane do swoich użytkowników, którzy uruchamiają proces Asystenta, konfigurowanie urządzenia przy użyciu swoich poświadczeń służbowego i ukończenie procesu rejestracji. Zobacz [rejestracji hybrydowe iOS przy użyciu programu Apple Configurator z programu Configuration Manager](../../mdm/deploy-use/ios-hybrid-enrollment-using-apple-configurator.md).  

## <a name="device-enrollment-manager"></a>Menedżer rejestracji urządzeń  
 Organizacje mogą używać usługi Intune do zarządzania dużą liczbą urządzeń przenośnych za pomocą jednego konta użytkownika o nazwie konto menedżera rejestracji urządzeń. Po utworzeniu konta Menedżera rejestracji urządzeń, tego konta można przez Menedżera zarejestrować więcej niż standardowa pięciu urządzeń domyślnie użytkownikom normalne dozwolone. Rejestrowanie urządzeń przy użyciu Menedżera rejestracji urządzeń działa tylko w przypadku urządzeń, które nie są używane przez określonego użytkownika. Te urządzenia są dobre do punktów sprzedaży lub narzędzia aplikacji, na przykład, ale zły dla użytkowników wymagających dostępu do zasobów firmy lub adres e-mail. Zobacz [zarejestrować urządzenia za pomocą Menedżera rejestracji urządzeń z programu Configuration Manager](../../mdm/deploy-use/enroll-devices-with-device-enrollment-manager.md).  

## <a name="user-affinity-for-managed-devices"></a>Koligacji użytkownika dla zarządzanych urządzeń  
 Podczas konfigurowania profilów dla firmowych urządzeń, administrator może określić, czy zarządzane urządzenia obsługują *koligacji użytkownika* identyfikujący określonego użytkownika z urządzeniem. Na urządzeniach, na których skonfigurowano **user affinity** , można instalować i uruchamiać aplikację Portal firmy w celu pobierania aplikacji i zarządzania urządzeniami. Zobacz [koligacji użytkownika dla hybrydowego zarządzanych urządzeń w programie Configuration Manager](../../mdm/deploy-use/user-affinity-for-hybrid-managed-devices.md).  

## <a name="manage-devices-with-activation-lock"></a>Zarządzanie urządzeniami przy użyciu blokady aktywacji  
 Microsoft Intune może ułatwić zarządzanie iOS blokadę aktywacji, funkcja Znajdź mój iPhone i aplikacji dla systemu iOS 7.1 urządzenia z nowszymi wersjami. Blokada aktywacji jest włączana automatycznie w przypadku użycia aplikacji Znajdź mój iPhone na urządzeniu. Zobacz [Zarządzanie iOS blokady aktywacji z System Center Configuration Manager](../../mdm/deploy-use/manage-ios-activation-lock.md).

 ## <a name="predeclare-devices-with-imei-or-ios-serial-numbers"></a>Predeclare urządzenia z IMEI lub iOS numerów seryjnych

Importowanie ich liczby tożsamości (IMEI) urządzeń przenośnych stacji międzynarodowe lub numery seryjne iOS można zidentyfikować firmowych urządzeń. Możesz przekazać plik wartości rozdzielanych przecinkami (.csv) zawierający numery IMEI urządzenia lub można ręcznie wprowadzić informacje o urządzeniu.  Zobacz [Predeclare urządzeń przy użyciu identyfikatorów sprzętu](../../mdm/deploy-use/predeclare-devices-with-hardware-id.md).

