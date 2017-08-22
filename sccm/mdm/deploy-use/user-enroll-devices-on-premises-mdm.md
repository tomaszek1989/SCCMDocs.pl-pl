---
title: "Jak użytkownicy rejestrują urządzenia z lokalnym zarządzaniem urządzeniami Przenośnymi — programu Configuration Manager | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak użytkownicy rejestrują urządzenia z zarządzania urządzeniami przenośnymi lokalnymi w programie System Center Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 59004b34-b64f-4d77-898c-07bf3dc75430
caps.latest.revision: "9"
caps.handback.revision: "0"
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.openlocfilehash: 8c7438c2cc0bc66654eb3e74de10553df53181d9
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="how-users-enroll-devices-with-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>Jak użytkownicy rejestrują urządzenia z zarządzania urządzeniami przenośnymi lokalnymi w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Z System Center Configuration Manager na — lokalne zarządzanie urządzeniami przenośnymi użytkownicy mogą rejestrować urządzenia, jeśli przyznano im uprawnienia rejestracji (przez uaktualnione ustawienia klienta), a ich urządzeniach zainstalowano certyfikat główny wymagany do nawiązania zaufanej komunikacji z serwerami hostującymi wymagane role systemu lokacji. Aby uzyskać więcej informacji na temat sposobu konfigurowania rejestracji, zobacz [Konfigurowanie rejestracji urządzeń do zarządzania urządzeniami przenośnymi lokalnymi w programie System Center Configuration Manager](../../mdm/get-started/set-up-device-enrollment-on-premises-mdm.md).  

> [!NOTE]  
>  Bieżąca gałąź programu Configuration Manager obsługuje rejestrację w lokalnego zarządzania urządzeniami przenośnymi dla urządzeń z systemem następujących systemach operacyjnych:  
>   
> -  Windows 10 Enterprise  
> -   Windows 10 Pro  
> -   Windows 10 Team \(w programie Configuration Manager w wersji 1602\)  
> -   Windows 10 Mobile  
> -   Windows 10 Mobile Enterprise
> -   Windows 10 Enterprise IoT   

Następujące zadania wyjaśniają, jak zarejestrować oraz zweryfikować rejestrację komputerów i urządzeń dla na\-lokalnych zarządzanie urządzeniami przenośnymi:  

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
 Aby sprawdzić, czy urządzenia zostały zarejestrowane pomyślnie w konsoli programu Configuration Manager.  

1.  Uruchom konsolę programu Configuration Manager.  

2.  Kliknij przycisk **Zasoby i zgodność** > **Przegląd** > **Urządzenia**. Zarejestrowane urządzenie zostanie wyświetlone na liście.  
