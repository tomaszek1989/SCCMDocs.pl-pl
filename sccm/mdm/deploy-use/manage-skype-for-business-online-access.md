---
title: Zarządzanie dostępem do usługi Skype dla firm Online
titleSuffix: Configuration Manager
description: Dowiedz się, jak zarządzać dostępem do usługi Skype dla firm Online za pomocą zasad dostępu warunkowego.
ms.date: 12/22/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 71c44250-626e-482c-8794-434c6aeb2fb1
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 4a88706233e85be6960585963c26bd740e9ff6ed
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="manage-skype-for-business-online-access"></a>Zarządzanie dostępem do usługi Skype dla firm Online

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


Użyj zasad dostępu warunkowego dla usługi Skype dla firm Online, aby zarządzać dostępem do usługi Skype dla firm Online, na podstawie warunków, które określisz.  


 Gdy wybrany użytkownik próbuje użyć usługi Skype dla firm Online na swoim urządzeniu, sprawdzane są następujące kwestie:![ConditionalAccess&#95;SFBFlow](media/ConditionalAccess_SFBFlow.png)  

## <a name="prerequisites"></a>Wymagania wstępne  

-   Włącz [nowoczesnego uwierzytelniania](https://aka.ms/SkypeModernAuth) dla usługi Skype dla firm Online.   

-   Każdy użytkownik musi użyć usługi Skype dla firm Online. Jeśli masz wdrożenie z Skype dla firm Online i Skype dla firm lokalnymi, zasady dostępu warunkowego nie dotyczą użytkowników lokalnych.  

-   Urządzenie, które wymaga dostępu do usługi Skype dla firm Online, musi:  

    -   Urządzenie Android lub iOS

    -   Zostać zarejestrowane w usłudze Microsoft Intune

    -   Być zgodne z wdrożonymi zasadami zgodności programu Microsoft Intune

 Usługa Azure Active Directory przechowuje stanu urządzenia, która blokuje dostęp na podstawie wybranych warunków, które określisz lub go przydziela.  
Jeśli warunek nie jest spełniony, użytkownik zobaczy jeden z następujących komunikatów podczas logowania:  

-   Jeśli urządzenie nie zostało zarejestrowane w usłudze Microsoft Intune lub nie jest zarejestrowany w usłudze Azure Active Directory, użytkownik widzi instrukcjami dotyczącymi sposobu instalowania aplikacji Portal firmy i rejestrowania.  

-   Jeśli urządzenie nie jest zgodne, użytkownik zobaczy następujący komunikat, który kieruje je do aplikacji Portal firmy lub witryny sieci Web Portal firmy. Portal firmy ma informacje o problemie i sposobie jego rozwiązania.  

## <a name="configure-conditional-access-for-skype-for-business-online"></a>Konfigurowanie dostępu warunkowego do usługi Skype dla firm Online  

### <a name="step-1-configure-active-directory-security-groups"></a>Krok 1. Konfigurowanie grup zabezpieczeń usługi Active Directory  
 Przed rozpoczęciem skonfiguruj grupy zabezpieczeń usługi Azure Active Directory dla zasad dostępu warunkowego. Skonfigurować te grupy w Centrum administracyjnym usługi Office 365. Grupy te zawierają użytkowników docelowych lub wykluczone z zasad. Jeśli zasady obejmują użytkownika, każde używane przez niego urządzenie musi być zgodne, aby mógł uzyskać dostęp do zasobów.  

 Możesz określić dwa typy grup, które mogą być używane w zasadach dotyczących programu Skype dla firm:  

-   **Grupy docelowe** zawierają użytkowników, których dotyczą zasady  

-   **Wykluczone grupy** zawierają użytkowników, które mają zostać wykluczone z zasad  
    Jeśli użytkownik należy do obu grup, są wyłączone.  

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>Krok 2. Konfigurowanie i wdrażanie zasad zgodności  
 Tworzenie i wdrażanie zasad zgodności na wszystkich urządzeniach, do których podlega zasady usługi Skype dla firm Online.  

 Aby uzyskać więcej informacji o sposobie konfigurowania zasad zgodności, zobacz [Zarządzanie zasadami zgodności urządzeń](../../protect/deploy-use/device-compliance-policies.md).  

> [!NOTE]  
>  Jeśli zasady zgodności nie zostaną wdrożone i włączysz zasady usługi Skype dla firm Online, wszystkie objęte nimi urządzenia mają dostęp, jeśli są one rejestrowane w Microsoft Intune.  


### <a name="step-3-configure-the-skype-for-business-online-policy"></a>Krok 3. Skonfiguruj zasady usługi Skype dla firm Online  
 Skonfiguruj zasady wymagające, który tylko zarządzane i zgodne urządzenia mają dostęp do usługi Skype dla firm Online. Te zasady są przechowywane w usłudze Azure Active Directory.  

1.  W [konsoli administracyjnej usługi Microsoft Intune](https://manage.microsoft.com)kliknij kolejno pozycje **Zasady** > **Dostęp warunkowy** > **Skype for Business Online Zasady**.  

     ![ConditionalAccess & #95; SFBPolicy](media/ConditionalAccess_SFBPolicy.png)  

2.  Wybierz pozycję **Włącz zasady dostępu warunkowego**.  

3.  W obszarze **Dostęp do aplikacji**możesz wybrać platformy, do których zostaną zastosowane zasady dostępu warunkowego:  

    -   iOS  

    -   Android  

4.  W obszarze **grupy docelowe**, kliknij przycisk **Modyfikuj** aby wybrać grupy zabezpieczeń usługi Azure Active Directory, do których ma zastosowanie zasad. Można wybrać wyeliminować te zasady do wszystkich użytkowników lub wybraną grupę użytkowników.  

5.  W obszarze **Wykluczone grupy**możesz kliknąć pozycję **Modyfikuj** , aby wybrać grupy zabezpieczeń usługi Azure Active Directory wykluczone z tych zasad.  

6.  Gdy wszystko będzie gotowe, kliknij pozycję **Zapisz**.  

 Dostęp warunkowy do usługi Skype dla firm Online jest teraz skonfigurowany. Nie musisz wdrażać zasad dostępu warunkowego; są one aktywne natychmiast.  

## <a name="monitor-the-compliance-and-conditional-access-policies"></a>Monitorowanie zgodności i zasad dostępu warunkowego  
 W obszarze roboczym Grupy możesz przeglądać informacje o stanie dostępu warunkowego urządzeń.  

 Wybierz dowolną grupę urządzeń przenośnych, a następnie na karcie **Urządzenia** wybierz jeden z następujących **filtrów**:  

-   **Urządzenia, które nie są zarejestrowane w usłudze AAD** usługi Skype dla firm Online jest zablokowany

-   **Urządzenia, które nie są zgodne** usługi Skype dla firm Online jest zablokowany  

-   **Urządzenia, które są zarejestrowane w usłudze AAD i są zgodne** można uzyskać dostęp do usługi Skype dla firm Online  

### <a name="see-also"></a>Zobacz także  

 [Zarządzanie zasadami zgodności urządzeń w programie System Center Configuration Manager](../../protect/deploy-use/device-compliance-policies.md)
