---
title: "Konfigurowanie subskrypcji usługi Intune | Dokumentacja firmy Microsoft"
description: "Konfigurowanie subskrypcji usługi Intune w celu śledzenia licencji na potrzeby zarządzania urządzeniami przenośnymi lokalnymi w programie System Center Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 1e42b1c1-3d58-481f-8647-5c7ae640c5f5
caps.latest.revision: "8"
caps.handback.revision: "0"
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.openlocfilehash: 5a81ec06e16992ae1c41b0fc98ebcd07386c5381
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="set-up-a-microsoft-intune-subscription-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>Skonfiguruj subskrypcję Microsoft Intune do zarządzania urządzeniami przenośnymi lokalnymi w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

System Center Configuration Manager na\-lokalne zarządzanie urządzeniami przenośnymi wymaga subskrypcji Microsoft Intune do śledzenia licencji. Usługa Intune nie jest używana do zarządzania urządzeniami ani do przechowywania informacji o zarządzaniu. Aby uzyskać na\-lokalnego zarządzania urządzeniami przenośnymi, całe zarządzanie urządzeniami jest obsługiwane przez infrastrukturę programu Configuration Manager.  

> [!NOTE]  
> Począwszy od wersji 1610, Configuration Manager obsługuje korzystanie z obu Microsoft Intune i lokalnej infrastruktury programu Configuration Manager do zarządzania urządzeniami przenośnymi, w tym samym czasie.   

> [!TIP]  
>  Zalecane jest skonfigurowanie subskrypcji usługi Intune na\-lokalnych zarządzanie urządzeniami przenośnymi, przed zainstalowaniem ról systemu lokacji wymagane, aby zminimalizować czas wymagany do nowo zainstalowane role systemu lokacji stały się funkcjonalne.  

##  <a name="sign-up-for-microsoft-intune"></a>Zarejestruj się w usłudze Microsoft Intune  
 Usługa Intune jest wymagana do udostępnienia na\-lokalnych funkcjonalności zarządzanie urządzeniami przenośnymi. Po prostu [Zarejestruj](http://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/) subskrypcji próbnej lub płatnej i przejdź do następnego kroku, aby dodać subskrypcję do programu Configuration Manager.  

##  <a name="add-the-intune-subscription-to-configuration-manager"></a>Dodaj subskrypcję usługi Intune do programu Configuration Manager  
 Aby dodać subskrypcję do programu Configuration Manager, wykonaj te same czynności podstawowe jak podczas dodawania subskrypcji na potrzeby zarządzania urządzeniami przenośnymi w usłudze Intune. Przeczytaj uwagi poniżej, aby poznać konkretne różnice, a następnie postępuj zgodnie z instrukcjami w [skonfigurować subskrypcję usługi Intune](../deploy-use/configure-intune-subscription.md).  

> [!NOTE]  
>  Podczas dodawania subskrypcji usługi Intune należy pamiętać o następujących czynności:  
>   
>  -   Kolekcja określona w Kreatorze dodawania subskrypcji usługi Intune Microsoft nie jest używany na\-lokalnych zarządzanie urządzeniami przenośnymi delegowania praw użytkownika lokalnego. Służy tylko do zarządzania urządzeniami przenośnymi przy użyciu usługi Intune. Jednakże należy określić kolekcję, aby kreator mógł kontynuować działanie.  
> -   Ustawienie kodu lokacji określone w kreatorze jest ignorowane dla na\-lokalnych zarządzanie urządzeniami przenośnymi. Używany kod lokacji jest kodem określonym w profilu rejestracji, który nadaje użytkownikowi uprawnienie do rejestrowania urządzeń.  
> -   Nie należy włączać uwierzytelniania wieloskładnikowego. Nie jest obsługiwany w na\-lokalnych zarządzanie urządzeniami przenośnymi.  

##  <a name="configure-the-intune-subscription-for-on-premises-mobile-device-management"></a>Konfigurowanie subskrypcji usługi Intune do zarządzania urządzeniami przenośnymi lokalnej  

1.  W konsoli programu Configuration Manager, kliknij prawym przyciskiem myszy **subskrypcję usługi Microsoft Intune**i kliknij przycisk **właściwości**.  

2.  W polu na lokalnego zarządzania urządzeniami przenośnymi wybierz jedną z następujących czynności:

  - Jeśli planujesz mieć tylko urządzenia zarządzane lokalnie, kliknij pole wyboru obok pozycji **tylko zarządzanie urządzeniami lokalnymi**i kliknij przycisk **OK**.  

      > [!NOTE]  
      >  Po kliknięciu tego pola wyboru, możesz skonfigurować subskrypcję usługi Intune, aby zachować wszystkie informacje lokalnego zarządzania i dane nie są replikowane do chmury.  

    - Jeśli planujesz urządzeń zarządzanych przez usługi Intune i programu Configuration Manager lokalnymi, nie zaznaczaj pola wyboru.

3.  Jeśli planowane jest zarządzanie urządzeniami z systemem Windows 10 Mobile, kliknij prawym przyciskiem myszy pozycję **Subskrypcja usługi Microsoft Intune**, kliknij pozycję **Konfiguruj platformy**, a następnie kliknij pozycję  **Windows Phone**.  

4.  Kliknij pole wyboru obok pozycji **Windows Phone 8.1 i Windows 10 Mobile**, a następnie kliknij przycisk **OK**.  

5.  Jeśli planowane jest zarządzanie urządzeniami z systemem Windows 10 Desktop, kliknij prawym przyciskiem myszy pozycję **Subskrypcja usługi Microsoft Intune**, kliknij pozycję **Konfiguruj platformy**, a następnie kliknij pozycję **Włącz rejestrację systemu Windows**.  

6.  Kliknij pole wyboru obok pozycji **Włącz rejestrację systemu Windows**, a następnie kliknij przycisk **OK**.  
