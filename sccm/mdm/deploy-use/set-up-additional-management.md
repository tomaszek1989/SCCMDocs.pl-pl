---
title: Ustawienia dodatkowego zarządzania
titleSuffix: Configuration Manager
description: Skonfiguruj dodatkowe zarządzanie przy użyciu programu System Center Configuration Manager.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 4877d674-6bbc-4e16-810c-daad70c74daa
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 58a61dffbdd9b04d3e872e23f88ddc0ac864f99d
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="set-up-additional-management-with-system-center-configuration-manager"></a>Ustawienia dodatkowego zarządzania w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

(Opcjonalnie) Można skonfigurować dodatkowe zarządzania przed zarejestrowaniem urządzenia. Takie rozwiązania do zarządzania można tworzyć i wdrażane po zarejestrowaniu urządzenia, mimo że wiele organizacji woli wdrażać je jako urządzenia są wprowadzane do systemu zarządzania.

**Elementy konfiguracji** umożliwiają zarządzanie ustawienia, takie jak wymaganie numeru PIN lub wymaganie szyfrowania na zarejestrowanych urządzeniach, w oparciu o platformy urządzeń:
- [Urządzenia z systemem Windows 10 i Windows 8.1](create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md)
- [Urządzenia Windows Phone](create-configuration-items-for-windows-phone-devices-managed-without-the-client.md)
- [iOS i Mac urządzeń](create-configuration-items-for-ios-and-mac-os-x-devices-managed-without-the-client.md)
- [Android i Samsung KNOX Standard urządzeń](create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client.md)

**Aplikacje** można wdrożyć na zarządzanych urządzeniach:
- [aplikacje systemu iOS](creating-ios-applications.md)
- [Aplikacji dla komputerów Mac](../../apps/get-started/creating-mac-computer-applications.md)
- [Aplikacje na komputerze z systemem Windows](../../apps/get-started/creating-windows-applications.md)
- [Aplikacje Windows Phone](creating-windows-phone-applications.md)
- [Aplikacje systemu android](creating-android-applications.md)

**Dostęp warunkowy** umożliwia zarządzanie dostępem do zasobów firmy, w tym:  
- [Dostęp do poczty e-mail](manage-email-access.md)
- [Dostęp do programu SharePoint](manage-sharepoint-online-access.md)
- [Skype dla firm dostępu](manage-skype-for-business-online-access.md)
- [Dynamiczne CRM Online](manage-dynamics-crm-online-access.md)

**Uwierzytelnianie wieloskładnikowe (MFA)** umożliwia wymagają więcej niż jednej metody weryfikacji, który dodaje kluczową drugą warstwę zabezpieczeń do logowania użytkowników i transakcji.
Wcześniej przejdzie do konsoli usługi Intune lub konsoli programu Configuration Manager do ustawienia usługi MFA dla rejestracji w usłudze Intune. Teraz możesz zalogować się do [portalu Microsoft Azure](https://manage.windowsazure.com) przy użyciu poświadczeń konta usługi Intune i skonfigurować ustawienia usługi MFA za pośrednictwem usługi Azure AD. Aby dowiedzieć się więcej, zobacz [uwierzytelnianie wieloskładnikowe w usłudze Microsoft Intune](https://aka.ms/mfa_ad).

> [!div class="button"]
[< Wstecz krok](enable-platform-enrollment.md)[następny krok >  ](verify-mdm-configuration.md)
