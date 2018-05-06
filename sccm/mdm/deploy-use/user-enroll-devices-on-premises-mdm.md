---
title: 'Jak użytkownicy rejestrują urządzenia z lokalnym zarządzaniem urządzeniami Przenośnymi '
titleSuffix: Configuration Manager
description: Dowiedz się, jak użytkownicy rejestrują urządzenia z zarządzania urządzeniami przenośnymi lokalnymi w programie System Center Configuration Manager.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 59004b34-b64f-4d77-898c-07bf3dc75430
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 15774704665b2b52daf1061db221ab0eb158eceb
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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
