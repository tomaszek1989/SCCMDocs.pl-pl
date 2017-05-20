---
title: "Konfigurowanie subskrypcji usługi Intune | Dokumentacja firmy Microsoft"
description: "Konfigurowanie subskrypcji usługi Intune do śledzenia licencji dla lokalnego zarządzania urządzeniami przenośnymi w programie System Center Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 1e42b1c1-3d58-481f-8647-5c7ae640c5f5
caps.latest.revision: 8
caps.handback.revision: 0
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: 5a81ec06e16992ae1c41b0fc98ebcd07386c5381
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="set-up-a-microsoft-intune-subscription-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>Konfigurowanie subskrypcji usługi Microsoft Intune dla lokalnego zarządzania urządzeniami przenośnymi w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

System Center Configuration Manager na\-lokalnego zarządzania urządzeniami przenośnymi wymaga subskrypcji Microsoft Intune śledzenia licencji. Usługa Intune nie jest używany do zarządzania urządzeniami lub do przechowywania informacji o zarządzaniu. Aby uzyskać na\-lokalnego zarządzania urządzeniami przenośnymi, całe zarządzanie urządzeniami jest obsługiwane przez infrastrukturę programu Configuration Manager.  

> [!NOTE]  
> Począwszy od wersji 1610, Configuration Manager przy użyciu obu Microsoft Intune i lokalną infrastrukturę programu Configuration Manager do zarządzania urządzeniami przenośnymi, w tym samym czasie.   

> [!TIP]  
>  Zalecane jest skonfigurowanie subskrypcji usługi Intune na\-lokalnych zarządzanie urządzeniami przenośnymi, przed zainstalowaniem ról systemu lokacji wymagane, aby zminimalizować czas wymagany do nowo zainstalowanych ról systemu lokacji stają się funkcjonalności.  

##  <a name="sign-up-for-microsoft-intune"></a>Zarejestruj się w usłudze Microsoft Intune  
 Usługa Intune jest wymagana na\-lokalnych funkcjonalności zarządzanie urządzeniami przenośnymi. Po prostu [Załóż](http://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/) dla wersji próbnej lub płatnej subskrypcji i przejdź do następnego kroku, aby dodać subskrypcję do programu Configuration Manager.  

##  <a name="add-the-intune-subscription-to-configuration-manager"></a>Dodaj subskrypcję usługi Intune do programu Configuration Manager  
 Aby dodać subskrypcję do programu Configuration Manager, wykonaj te same kroki podstawowe tak jak w przypadku dodawania subskrypcji do zarządzania urządzeniami przenośnymi za pomocą usługi Intune. Przeczytaj notatki poniżej określonego różnic, a następnie postępuj zgodnie z instrukcjami w [skonfigurować subskrypcję usługi Intune](../deploy-use/configure-intune-subscription.md).  

> [!NOTE]  
>  Podczas dodawania subskrypcji usługi Intune, należy uwzględnić następujące czynności:  
>   
>  -   Kolekcja określone w Kreatorze dodawania subskrypcji usługi Intune Microsoft nie jest używany na\-lokalnych delegowanie prawa użytkownika Zarządzanie urządzeniami przenośnymi. Jest ono używane wyłącznie do zarządzania urządzeniami przenośnymi za pomocą usługi Intune. Jednakże należy określić kolekcję, aby kreator mógł kontynuować działanie.  
> -   Ustawienie kodu lokacji, określonych w kreatorze są ignorowane dla na\-lokalnych zarządzanie urządzeniami przenośnymi. Używany kod lokacji jest kodem określonym w profilu rejestracji, który nadaje użytkownikowi uprawnienie do rejestrowania urządzeń.  
> -   Nie należy włączać uwierzytelniania wieloskładnikowego. Nie jest obsługiwane w sprawie\-lokalnych zarządzanie urządzeniami przenośnymi.  

##  <a name="configure-the-intune-subscription-for-on-premises-mobile-device-management"></a>Skonfiguruj subskrypcję usługi Intune dla lokalnego zarządzania urządzeniami przenośnymi  

1.  W konsoli programu Configuration Manager kliknij prawym przyciskiem myszy **subskrypcja usługi Microsoft Intune**i kliknij przycisk **właściwości**.  

2.  W polu na zarządzanie urządzeniami przenośnymi lokalnego wybierz jedną z następujących czynności:

  - Jeśli planujesz mieć tylko urządzenia zarządzane lokalnie, kliknij pole wyboru obok pozycji **tylko zarządzania urządzeniami lokalnymi**i kliknij przycisk **OK**.  

      > [!NOTE]  
      >  Klikając to pole wyboru, należy skonfigurować subskrypcję usługi Intune, aby zachować wszystkie zarządzania informacji lokalnych i replikuje dane w chmurze.  

    - Jeśli planujesz urządzeń zarządzanych przez zarówno Intune i program Configuration Manager lokalnie, nie zaznaczaj pola wyboru.

3.  Jeśli planowane jest zarządzanie urządzeniami z systemem Windows 10 Mobile, kliknij prawym przyciskiem myszy pozycję **Subskrypcja usługi Microsoft Intune**, kliknij pozycję **Konfiguruj platformy**, a następnie kliknij pozycję  **Windows Phone**.  

4.  Kliknij pole wyboru obok pozycji **Windows Phone 8.1 i Windows 10 Mobile**, a następnie kliknij przycisk **OK**.  

5.  Jeśli planowane jest zarządzanie urządzeniami z systemem Windows 10 Desktop, kliknij prawym przyciskiem myszy pozycję **Subskrypcja usługi Microsoft Intune**, kliknij pozycję **Konfiguruj platformy**, a następnie kliknij pozycję **Włącz rejestrację systemu Windows**.  

6.  Kliknij pole wyboru obok pozycji **Włącz rejestrację systemu Windows**, a następnie kliknij przycisk **OK**.  

