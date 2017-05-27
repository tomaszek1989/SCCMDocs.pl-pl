---
title: "Zarządzanie Skype dostępu dla biznesowych Online | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak używać zasad dostępu warunkowego do zarządzania dostępem do programu Skype dla usługi Online firmy."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 71c44250-626e-482c-8794-434c6aeb2fb1
caps.latest.revision: 6
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: cacb22a85e74a7d9cae75ad907d0206487cd4dc7
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="manage-skype-for-business-online-access"></a>Zarządzanie dostępem do usługi Skype dla firm Online

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


Użyj zasad dostępu warunkowego dla usługi  **Skype dla firm Online** , aby zarządzać dostępem do usługi Skype dla firm Online na podstawie określonych kryteriów.  


 Gdy wybrany użytkownik próbuje użyć usługi Skype dla firm Online na swoim urządzeniu, sprawdzane są następujące kwestie:![ConditionalAccess&#95;SFBFlow](media/ConditionalAccess_SFBFlow.png)  

## <a name="prerequisites"></a>Wymagania wstępne  

-   Włącz nowoczesne uwierzytelnianie dla usługi Skype dla firm Online. Wypełnij ten [formularz Connect](https://connect.microsoft.com/office/Survey/NominationSurvey.aspx?SurveyID=17299&ProgramID=8715) , aby zarejestrować się w programie nowoczesnego uwierzytelniania.  

-   Wszystkim użytkownikom końcowym musi być za pomocą programu Skype dla usługi Online firmy. Jeśli masz wdrożenie programu Skype dla usługi Online firmy i Skype dla firmy lokalnie zasad dostępu warunkowego nie będą stosowane do użytkowników końcowych.  

-   Urządzenie, które wymaga dostępu do usługi Skype dla firm Online, musi:  

    -   być urządzeniem z systemem Android lub iOS,  

    -   być zarejestrowane w usłudze Intune,  

    -   być zgodne z wdrożonymi zasadami zgodności usługi Intune.  

 Stan urządzenia jest przechowywany w usłudze Azure Active Directory, która na podstawie określonych kryteriów blokuje dostęp lub go przydziela.  
Jeśli warunek nie jest spełniony, użytkownik zobaczy podczas logowania jeden z następujących komunikatów:  

-   Jeśli urządzenie nie zostało zarejestrowane w usłudze Intune lub Azure Active Directory, zostanie wyświetlony komunikat z instrukcjami dotyczącymi sposobu instalowania aplikacji portalu firmy i rejestrowania.  

-   Jeśli urządzenie nie jest zgodne, zostanie wyświetlony komunikat kierujący użytkownika do witryny sieci Web portalu firmy usługi Intune lub aplikacji portalu firmy, gdzie można znaleźć informacje o problemie i sposobie jego rozwiązania.  

## <a name="configure-conditional-access-for-skype-for-business-online"></a>Konfigurowanie dostępu warunkowego do usługi Skype dla firm Online  

### <a name="step-1-configure-active-directory-security-groups"></a>Krok 1: Skonfiguruj grupy zabezpieczeń usługi Active Directory  
 Przed rozpoczęciem skonfiguruj grupy zabezpieczeń usługi Azure Active Directory dla zasad dostępu warunkowego. Możesz skonfigurować te grupy w centrum administracyjnym usługi Office 365. Grupy te zawierają użytkowników, którzy będą objęci zasadami lub wykluczeni z nich. Jeśli zasady obejmują użytkownika, każde używane przez niego urządzenie musi być zgodne, aby mógł uzyskać dostęp do zasobów.  

 Możesz określić dwa typy grup, które mogą być używane w zasadach dotyczących programu Skype dla firm:  

-   Celem grup â €"grupy użytkowników, do których mają dotyczyć zasady  

-   Wykluczone grupy â €"grupy użytkowników, którzy są wykluczeni z zasad (opcjonalnie)  
    Jeśli użytkownik należy do obu grup, będzie wykluczony z zasad.  

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>Krok 2: Konfigurowanie i wdrażanie zasad zgodności  
 Upewnij się, że utworzono zasady zgodności i wdrożono je na wszystkich urządzeniach, które będą objęte zasadami usługi Skype dla firm Online.  

 Aby uzyskać szczegółowe informacje o tym, jak skonfigurować zasady zgodności, zobacz [Zarządzanie zasadami zgodności urządzeń za pomocą programu System Center Configuration Manager](../../protect/deploy-use/device-compliance-policies.md).  

> [!NOTE]  
>  Jeśli zasady zgodności nie zostaną wdrożone i włączysz zasady usługi Skype dla firm Online, wszystkie objęte nimi urządzenia będą mieć dostęp, jeśli zostaną zarejestrowane w usłudze Intune.  

 Gdy wszystko będzie gotowe, przejdź do kroku 3.  

### <a name="step-3-configure-the-skype-for-business-online-policy"></a>Krok 3: Konfigurowanie programu Skype dla zasady biznesowe Online  
 Skonfiguruj zasady wymagające, aby tylko urządzenia zarządzane i zgodne miały dostęp do usługi Skype dla firm Online. Te zasady będą przechowywane w usłudze Azure Active Directory.  

1.  W [konsoli administracyjnej usługi Microsoft Intune](https://manage.microsoft.com)kliknij kolejno pozycje **Zasady** > **Dostęp warunkowy** > **Skype for Business Online Zasady**.  

     ![ConditionalAccess &#95; SFBPolicy](media/ConditionalAccess_SFBPolicy.png)  

2.  Wybierz pozycję **Włącz zasady dostępu warunkowego**.  

3.  W obszarze **Dostęp do aplikacji**możesz wybrać platformy, do których zostaną zastosowane zasady dostępu warunkowego:  

    -   iOS  

    -   Android  

4.  W obszarze **Grupy docelowe**kliknij pozycję **Modyfikuj** , aby wybrać grupy zabezpieczeń usługi Azure Active Directory, których będą dotyczyć zasady. Możesz objąć zasadami wszystkich użytkowników lub wybraną grupę.  

5.  W obszarze **Wykluczone grupy**możesz kliknąć pozycję **Modyfikuj** , aby wybrać grupy zabezpieczeń usługi Azure Active Directory wykluczone z tych zasad.  

6.  Gdy wszystko będzie gotowe, kliknij pozycję **Zapisz**.  

 Dostęp warunkowy do usługi Skype dla firm Online jest teraz skonfigurowany. Nie musisz wdrażać zasad dostępu warunkowego; są one aktywne natychmiast.  

## <a name="monitor-the-compliance-and-conditional-access-policies"></a>Monitorowanie zgodności i zasad dostępu warunkowego  
 W obszarze roboczym Grupy możesz przeglądać informacje o stanie dostępu warunkowego urządzeń.  

 Wybierz dowolną grupę urządzeń przenośnych, a następnie na karcie **Urządzenia** wybierz jeden z następujących **filtrów**:  

-   **Urządzenia, które nie są zarejestrowane w usłudze AAD** â €"te urządzenia są blokowane dla usługi Online firmy Skype.  

-   **Urządzenia, które nie są zgodne z** â €"te urządzenia są blokowane dla usługi Online firmy Skype.  

-   **Urządzenia, które są zarejestrowane w usłudze AAD i są zgodne** â €"te urządzenia mogą uzyskać dostęp do Skype dla usługi Online firmy.  

### <a name="see-also"></a>Zobacz także  

 [Zarządzanie zasadami zgodności urządzeń w programie System Center Configuration Manager](../../protect/deploy-use/device-compliance-policies.md)

