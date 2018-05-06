---
title: Rejestrowanie urządzeń należących do użytkowników dla wdrożeń hybrydowych
titleSuffix: Configuration Manager
description: Więcej informacji na temat różnych metod, aby rejestrować urządzenia należące do użytkownika dla hybrydowych wdrożeń z programem Configuration Manager.
ms.date: 09/08/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 2bdaa8a7-6a64-4b0e-b617-309dcd912c45
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 198e5b65b85e10a1aa64f06361f1ba425e156662
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="enroll-user-owned-devices-for-hybrid-deployments-with-configuration-manager"></a>Rejestrowanie urządzeń należących do użytkownika dla hybrydowych wdrożeń z programu Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Urządzenia należące do użytkownika mogą być wprowadzane do zarządzania przez zarejestrowanie ich, proces często nazywana "Przynieś własne urządzenia" lub po prostu "BYOD". Użytkownicy w tym przez zainstalowanie aplikacji Portal firmy i zalogować się na urządzeniu (iOS, system macOS i Android) lub przez dodanie konta służbowego na urządzeniu i przyłączanie do domeny (system Windows). Ten proces zarejestruje urządzenie w usłudze Intune, przyznawanie użytkownikowi dostęp do zasobów zarządzanych przez usługę Intune i umożliwienie zarządzania niektórymi ustawieniami urządzenia, np. wymaganie numeru PIN usługi Intune.

Aby wyświetlić urządzenia do zarządzania jako administrator, należy najpierw [Konfigurowanie zarządzania urządzeniami przenośnymi](setup-hybrid-mdm.md) i [włączyć rejestrowanie](enable-platform-enrollment.md). Po włączeniu rejestracji użytkownicy mogą rejestrować swoje urządzenia. Zobacz [sposób informować użytkowników końcowych o Microsoft Intune](https://docs.microsoft.com/intune/end-user-educate) zagadnienia i czynności, aby udostępnić użytkownikom.

Firmy lub szkoły, które zakupu urządzeń można korzystać z programów, które pozwalają [zarządzać urządzeniami należącymi do firmy](enroll-company-owned-devices.md).
