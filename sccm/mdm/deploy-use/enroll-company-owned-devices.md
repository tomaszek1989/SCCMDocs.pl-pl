---
title: 'Rejestrowanie urządzeń należących do firmy '
titleSuffix: Configuration Manager
description: Więcej informacji na temat różnych metod na rejestrowanie urządzeń należących do firmy w przypadku hybrydowych wdrożeń z programem Configuration Manager.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: e2754ce6-1460-4ddd-9050-2cc87e7964f4
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 36b4169f3bed1957f8ea14159902f408ba642944
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="enroll-company-owned-devices-for-hybrid-deployments-with-configuration-manager"></a>Rejestrowanie urządzeń należących do firmy w przypadku hybrydowych wdrożeń z programu Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Organizację lub urządzenia należące do firmy (COD) mogą być wprowadzane do systemu zarządzania na wiele sposobów, w zależności od urządzenia i sposobu jego zakupu.  

## <a name="enroll-device-enrollment-program-ios-devices"></a>Rejestrowanie urządzeń z systemem iOS Device Enrollment Program  
 Wdraża profil rejestracji "bez udziału użytkownika" urządzenia zakupione w ramach programu Device Enrollment Program firmy Apple. Gdy użytkownik uruchomi Asystenta ustawień na urządzeniu, urządzenie jest zarejestrowane w usłudze Intune.  Urządzenia zarejestrowane przy użyciu DEP nie może być wyrejestrowane przez użytkowników. Zobacz [rejestrowanie dla systemu iOS Device Enrollment Program (DEP) dla hybrydowych wdrożeń z programem Configuration Manager](../../mdm/deploy-use/ios-device-enrollment-program-for-hybrid.md).  

## <a name="enroll-ios-devices-with-apple-configurator"></a>Rejestrowanie urządzeń z systemem iOS przy użyciu narzędzia Apple Configurator  
 Ta metoda wymaga od administratora USB podłączenia urządzenia z systemem iOS do komputera Mac z programem Apple Configurator w celu wstępnego skonfigurowania rejestracji. Urządzenia są następnie dostarczany do swoich użytkowników, którzy korzystają proces Asystenta ustawień, konfigurowanie urządzenia przy użyciu swoich poświadczeń konta służbowego i wykonując procedurę rejestracji. Zobacz [rejestrowanie hybrydowego systemu iOS przy użyciu programu Apple Configurator z programem Configuration Manager](../../mdm/deploy-use/ios-hybrid-enrollment-using-apple-configurator.md).  

## <a name="device-enrollment-manager"></a>Menedżer rejestracji urządzeń  
 Organizacje mogą zarządzać dużą liczbą urządzeń przenośnych z jednego konta użytkownika o nazwie konta Menedżera rejestracji urządzeń przy użyciu usługi Intune. Po utworzeniu konta Menedżera rejestracji urządzeń, to konto można przez Menedżera więcej niż pięciu urządzeń domyślnie normalni użytkownicy mogą zarejestrować. Rejestrowanie urządzeń za pomocą Menedżera rejestracji urządzeń działa tylko w przypadku urządzeń, które nie są używane przez określonego użytkownika. Te urządzenia są dobrym do punktów sprzedaży lub narzędziu aplikacji, na przykład, ale złym rozwiązaniem dla użytkowników, którzy potrzebują dostępu do poczty e-mail lub zasobów firmowych. Zobacz [rejestrować urządzenia za pomocą Menedżera rejestracji urządzeń z programem Configuration Manager](../../mdm/deploy-use/enroll-devices-with-device-enrollment-manager.md).  

## <a name="user-affinity-for-managed-devices"></a>Koligacja użytkownika dla zarządzanych urządzeń  
 Podczas konfigurowania profilów dla urządzeń należących do firmy, administrator może określić, czy zarządzane urządzenia obsługują *koligacji użytkownika* identyfikujący określonego użytkownika z urządzeniem. Na urządzeniach, na których skonfigurowano **user affinity** , można instalować i uruchamiać aplikację Portal firmy w celu pobierania aplikacji i zarządzania urządzeniami. Zobacz [koligacji użytkownika dla hybrydowych zarządzanych urządzeń w programie Configuration Manager](../../mdm/deploy-use/user-affinity-for-hybrid-managed-devices.md).  

## <a name="manage-devices-with-activation-lock"></a>Zarządzanie urządzeniami przy użyciu blokady aktywacji  
 Microsoft Intune ułatwia zarządzanie blokadą aktywacji, funkcja Znajdź systemu iOS aplikacja Mój iPhone dla systemu iOS 7.1 i nowszym. Blokada aktywacji jest włączana automatycznie w przypadku użycia aplikacji Znajdź mój iPhone na urządzeniu. Zobacz [Zarządzanie blokadą aktywacji w programie System Center Configuration Manager systemu iOS](../../mdm/deploy-use/manage-ios-activation-lock.md).

 ## <a name="predeclare-devices-with-imei-or-ios-serial-numbers"></a>Wstępna deklaracja urządzeń z numery IMEI lub iOS za

Można zidentyfikować urządzenia należące do firmy przez zaimportowanie ich numerów identyfikujących (IMEI) urządzeń przenośnych międzynarodowe stacji lub numery seryjne systemu iOS. Możesz przekazać plik wartości rozdzielanych przecinkami (.csv) zawierający numery IMEI lub możesz ręcznie wprowadzić informacje o urządzeniu.  Zobacz [wstępna deklaracja urządzeń za numerami identyfikator sprzętem](../../mdm/deploy-use/predeclare-devices-with-hardware-id.md).
