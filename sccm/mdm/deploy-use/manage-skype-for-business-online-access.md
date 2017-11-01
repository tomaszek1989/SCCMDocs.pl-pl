---
title: "Zarządzanie dostępem do usługi Skype dla firm Online"
titleSuffix: Configuration Manager
description: "Dowiedz się, jak zarządzać dostępem do usługi Skype dla firm Online za pomocą zasad dostępu warunkowego."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 71c44250-626e-482c-8794-434c6aeb2fb1
caps.latest.revision: "6"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: b7886d3e8f181d6d9316c5438dd948b21a658648
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="manage-skype-for-business-online-access"></a>Zarządzanie dostępem do usługi Skype dla firm Online

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


Użyj zasad dostępu warunkowego dla usługi  **Skype dla firm Online** , aby zarządzać dostępem do usługi Skype dla firm Online na podstawie określonych kryteriów.  


 Gdy wybrany użytkownik próbuje użyć usługi Skype dla firm Online na swoim urządzeniu, sprawdzane są następujące kwestie:![ConditionalAccess&#95;SFBFlow](media/ConditionalAccess_SFBFlow.png)  

## <a name="prerequisites"></a>Wymagania wstępne  

-   Włącz nowoczesne uwierzytelnianie dla usługi Skype dla firm Online. Wypełnij ten [formularz Connect](https://connect.microsoft.com/office/Survey/NominationSurvey.aspx?SurveyID=17299&ProgramID=8715) , aby zarejestrować się w programie nowoczesnego uwierzytelniania.  

-   Wszyscy użytkownicy końcowi muszą używać programu Skype dla firm Online. Jeśli masz wdrożenie z Skype dla firm Online i Skype dla firm lokalnymi, zasady dostępu warunkowego nie będą stosowane do użytkowników końcowych.  

-   Urządzenie, które wymaga dostępu do usługi Skype dla firm Online, musi:  

    -   być urządzeniem z systemem Android lub iOS,  

    -   być zarejestrowane w usłudze Intune,  

    -   być zgodne z wdrożonymi zasadami zgodności usługi Intune.  

 Stan urządzenia jest przechowywany w usłudze Azure Active Directory, która na podstawie określonych kryteriów blokuje dostęp lub go przydziela.  
Jeśli warunek nie jest spełniony, użytkownik zobaczy podczas logowania jeden z następujących komunikatów:  

-   Jeśli urządzenie nie zostało zarejestrowane w usłudze Intune lub Azure Active Directory, zostanie wyświetlony komunikat z instrukcjami dotyczącymi sposobu instalowania aplikacji portalu firmy i rejestrowania.  

-   Jeśli urządzenie nie jest zgodne, zostanie wyświetlony komunikat kierujący użytkownika do witryny sieci Web portalu firmy usługi Intune lub aplikacji portalu firmy, gdzie można znaleźć informacje o problemie i sposobie jego rozwiązania.  

## <a name="configure-conditional-access-for-skype-for-business-online"></a>Konfigurowanie dostępu warunkowego do usługi Skype dla firm Online  

### <a name="step-1-configure-active-directory-security-groups"></a>Krok 1. Konfigurowanie grup zabezpieczeń usługi Active Directory  
 Przed rozpoczęciem skonfiguruj grupy zabezpieczeń usługi Azure Active Directory dla zasad dostępu warunkowego. Możesz skonfigurować te grupy w centrum administracyjnym usługi Office 365. Grupy te zawierają użytkowników, którzy będą objęci zasadami lub wykluczeni z nich. Jeśli zasady obejmują użytkownika, każde używane przez niego urządzenie musi być zgodne, aby mógł uzyskać dostęp do zasobów.  

 Możesz określić dwa typy grup, które mogą być używane w zasadach dotyczących programu Skype dla firm:  

-   Docelowe grupy â €"grupy użytkowników, do których zasady będą stosowane  

-   Wykluczone grupy â €"grupy użytkowników, którzy są wykluczeni z zasad (opcjonalnie)  
    Jeśli użytkownik należy do obu grup, będzie wykluczony z zasad.  

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>Krok 2. Konfigurowanie i wdrażanie zasad zgodności  
 Upewnij się, że utworzono zasady zgodności i wdrożono je na wszystkich urządzeniach, które będą objęte zasadami usługi Skype dla firm Online.  

 Aby uzyskać szczegółowe informacje o tym, jak skonfigurować zasady zgodności, zobacz [Zarządzanie zasadami zgodności urządzeń za pomocą programu System Center Configuration Manager](../../protect/deploy-use/device-compliance-policies.md).  

> [!NOTE]  
>  Jeśli zasady zgodności nie zostaną wdrożone i włączysz zasady usługi Skype dla firm Online, wszystkie objęte nimi urządzenia będą mieć dostęp, jeśli zostaną zarejestrowane w usłudze Intune.  

 Gdy wszystko będzie gotowe, przejdź do kroku 3.  

### <a name="step-3-configure-the-skype-for-business-online-policy"></a>Krok 3. Skonfiguruj zasady usługi Skype dla firm Online  
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

-   **Urządzenia, które nie są zarejestrowane w usłudze AAD** â €"usługi Skype dla firm Online jest zablokowany tych urządzeń.  

-   **Urządzenia, które nie są zgodne** â €"usługi Skype dla firm Online jest zablokowany tych urządzeń.  

-   **Urządzenia, które są zarejestrowane w usłudze AAD i są zgodne** â €"te urządzenia mogą uzyskiwać dostęp do programu Skype dla firm Online.  

### <a name="see-also"></a>Zobacz także  

 [Zarządzanie zasadami zgodności urządzeń w programie System Center Configuration Manager](../../protect/deploy-use/device-compliance-policies.md)
