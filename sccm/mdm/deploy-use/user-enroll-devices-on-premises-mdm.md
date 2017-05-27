---
title: "Jak użytkownicy rejestrują urządzenia z lokalnych MDM — Configuration Manager | Dokumentacja firmy Microsoft"
description: "Zrozumienie, jak użytkownicy rejestrują urządzenia z lokalnego zarządzania urządzeniami przenośnymi w programie System Center Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 59004b34-b64f-4d77-898c-07bf3dc75430
caps.latest.revision: 9
caps.handback.revision: 0
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 507bad02c6e028f09a8b0c8a566ac55f7c3942a5
ms.openlocfilehash: 8c7438c2cc0bc66654eb3e74de10553df53181d9
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-users-enroll-devices-with-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>Jak użytkownicy rejestrują urządzenia z lokalnego zarządzania urządzeniami przenośnymi w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Za pomocą zarządzania urządzeniami przenośnymi lokalnego Menedżera konfiguracji centrum systemu użytkownicy mogą rejestrować urządzenia, jeśli przyznano im uprawnienia rejestracji (przez ustawienia zaktualizowanego klienta), a ich urządzeń certyfikatu wymaganego głównego zainstalowana tak, aby mieć zaufanej komunikacji z serwerów obsługujących role systemu lokacji wymagane. Aby uzyskać więcej informacji dotyczących sposobu konfigurowania rejestracji, zobacz [Konfigurowanie rejestracji urządzeń do zarządzania urządzeniami przenośnymi lokalnie w programie System Center Configuration Manager](../../mdm/get-started/set-up-device-enrollment-on-premises-mdm.md).  

> [!NOTE]  
>  Bieżącej gałęzi programu Configuration Manager obsługuje rejestracji w zarządzanie urządzeniami przenośnymi lokalnie na urządzeniach z systemem w następujących systemach operacyjnych:  
>   
> -  Windows 10 Enterprise  
> -   Windows 10 Pro  
> -   Windows 10 Team \(począwszy od 1602 wersji programu Configuration Manager\)  
> -   Windows 10 Mobile  
> -   Windows 10 Mobile Enterprise
> -   System Windows 10 Enterprise IoT   

Następujące zadania wyjaśniają, jak zarejestrować i zweryfikować rejestracji komputerów i urządzeń, na\-lokalnych zarządzanie urządzeniami przenośnymi:  

-   [Rejestrowanie komputera z systemem Windows 10](#bkmk_enrollDesk)  

-   [Rejestrowanie urządzenia z systemem Windows 10 Mobile](#bkmk_enrollMob)  

-   [Weryfikuj rejestrację urządzenia](#bkmk_verify)  

##  <a name="bkmk_enrollDesk"></a> Rejestrowanie komputera z systemem Windows 10  

1.  Na komputerze z system Windows 10 przejdź do opcji **Ustawienia**.  

2.  Kliknij pozycję **Konta**, a następnie **Dostęp z miejsca pracy**.  

3.  W opcji Dostęp z miejsca pracy w sekcji **Połącz z pracą lub szkołą**kliknij pozycję **Połącz**, wprowadź służbowy adres e-mail i kliknij pozycję **Kontynuuj**.  

4.  Wprowadź nazwę FQDN serwera obsługującego rolę systemu lokacji punktu proxy rejestracji, a następnie kliknij przycisk **Kontynuuj**.  

5.  W sekcji Łączenie z usługą wprowadź hasło do służbowego konta e-mail i kliknij pozycję **Zaloguj**.  

6.  Kliknij przycisk **Pomiń** , aby zapamiętać dane logowania. Po chwili urządzenie zostanie połączone.  

##  <a name="bkmk_enrollMob"></a> Rejestrowanie urządzenia z systemem Windows 10 Mobile  

1.  Na urządzeniu z systemem Windows 10 Mobile przejdź do pozycji **Ustawienia**.  

2.  Kliknij pozycję **Konta**, a następnie **Dostęp z miejsca pracy**.  

3.  Kliknij przycisk **Połącz**.  

4.  Wprowadź służbowy adres e-mail i nazwę FQDN serwera hostującego rolę systemu lokacji punktu proxy rejestracji. Kliknij przycisk **Połącz**.  

5.  Na następnym ekranie wprowadź służbowy adres e-mail i hasło, a następnie kliknij przycisk **Zaloguj**. Po chwili urządzenie zostanie zarejestrowane. Kliknij przycisk **Gotowe**.  

##  <a name="bkmk_verify"></a> Weryfikuj rejestrację urządzenia  
 Można sprawdzić, czy urządzenia zostały pomyślnie zarejestrowane w konsoli programu Configuration Manager.  

1.  Uruchom konsolę programu Configuration Manager.  

2.  Kliknij przycisk **Zasoby i zgodność** > **Przegląd** > **Urządzenia**. Zarejestrowane urządzenie zostanie wyświetlone na liście.  

