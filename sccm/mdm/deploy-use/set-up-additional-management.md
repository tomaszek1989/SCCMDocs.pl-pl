---
title: "Konfigurowanie dodatkowych zarządzania za pomocą programu System Center Configuration Manager | Dokumentacja firmy Microsoft"
description: "Skonfiguruj dodatkowe zarządzanie przy użyciu programu System Center Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4877d674-6bbc-4e16-810c-daad70c74daa
caps.latest.revision: 18
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 947d2a85f2ac68c7ccaf9a1237fd60e89e7d1d10
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="set-up-additional-management-with-system-center-configuration-manager"></a>Konfigurowanie dodatkowych zarządzania z programem System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

(Opcjonalnie) Można skonfigurować dodatkowe Zarządzanie przed rejestracji urządzeń. Można tworzyć i wdrożone po zarejestrowaniu urządzeń, chociaż wiele organizacji woli wdrażać je jako urządzenia są włączane do zarządzania rozwiązaniach do zarządzania.

**Elementy konfiguracji** umożliwiają zarządzanie ustawienia, takie jak wymagających numeru PIN lub wymagających szyfrowania na zarejestrowanych urządzeniach z platformą urządzenia:
- [Urządzenia z systemem Windows 10 i Windows 8.1](create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md)
- [Urządzenia Windows Phone](create-configuration-items-for-windows-phone-devices-managed-without-the-client.md)
- [iOS i Mac urządzeń](create-configuration-items-for-ios-and-mac-os-x-devices-managed-without-the-client.md)
- [Android i Samsung KNOX Standard urządzeń](create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client.md)

**Aplikacje** można wdrożyć do zarządzanych urządzeń:
- [aplikacje systemu iOS](creating-ios-applications.md)
- [Aplikacji dla komputerów Mac](../../apps/get-started/creating-mac-computer-applications.md)
- [Aplikacje na komputerze z systemem Windows](../../apps/get-started/creating-windows-applications.md)
- [Aplikacje Windows Phone](creating-windows-phone-applications.md)
- [Aplikacje systemu android](creating-android-applications.md)

**Dostęp warunkowy** umożliwia zarządzanie dostępem do zasobów firmy, w tym:  
- [Dostęp do poczty e-mail](manage-email-access.md)
- [Dostęp do programu SharePoint](manage-sharepoint-online-access.md)
- [Skype dostępu biznesowe](manage-skype-for-business-online-access.md)
- [Dynamiczne CRM Online](manage-dynamics-crm-online-access.md)

**Uwierzytelnianie wieloskładnikowe (MFA)** umożliwia wymagają więcej niż jedną metodę weryfikacji, który dodaje kluczową drugą warstwę zabezpieczeń użytkownika logowania i transakcji.
Wcześniej czy przejdź do konsoli usługi Intune lub konsoli programu Configuration Manager do ustawiania MFA rejestracje Intune. Teraz możesz zalogować się do [portalu Microsoft Azure](https://manage.windowsazure.com) przy użyciu poświadczeń usługi Intune i skonfigurować ustawienia uwierzytelniania Wieloskładnikowego za pośrednictwem usługi Azure AD. Aby dowiedzieć się więcej, zobacz [uwierzytelnianie wieloskładnikowe dla Microsoft Intune](https://aka.ms/mfa_ad).

> [!div class="button"]
[< Wstecz kroku](enable-platform-enrollment.md)[następny krok >  ](verify-mdm-configuration.md)

