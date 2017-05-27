---
title: "Zarządzanie dostępem do programu Dynamics CRM Online | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak kontrolować dostęp do programu Microsoft Dynamics CRM Online z systemem iOS i android przy użyciu dostępu warunkowego Microsoft Intune."
ms.custom: na
ms.date: 03/05/2017
ms.reviewer: na
ms.prod: configuration-manager
ms.technology:
- configmgr-hybrid
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2bfc4c51-b25c-4c70-b81e-8a3b6ddf02c8
caps.latest.revision: 5
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: bd00f12ae3bc14a34d24c22c3d5277d275d51e85
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="manage-dynamics-crm-online-access-in-system-center-configuration-manager"></a>Zarządzanie dostępem do programu Dynamics CRM Online w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Dostęp do programu Microsoft Dynamics CRM Online można kontrolować z systemem iOS i android przy użyciu dostępu warunkowego Microsoft Intune.  Dostęp warunkowy Intune zawiera dwa składniki:
* [Zasady zgodności urządzeń](../../protect/deploy-use/device-compliance-policies.md) czy urządzenia muszą być zgodne, aby zostać uznane za zgodne.
* [Zasady dostępu warunkowego](../../protect/deploy-use/manage-access-to-services.md) który podania warunki, które urządzenie musi spełniać w celu uzyskania dostępu do usługi.

Aby dowiedzieć się więcej o jak warunkowego dostępu do działania, przeczytaj [zarządzanie dostępem do usług](../../protect/deploy-use/manage-access-to-services.md) artykułu.


Wybrany użytkownik próbuje korzystać z aplikacji programu Dynamics CRM na urządzeniu, następujące kwestie:

![Diagram Pokaż punkty decyzji, używane do ustalenia, czy urządzenie jest dozwolony dostęp do usługi lub jest zablokowany](media/mdm-ca-dynamics-crm-flow-diagram.png)

Urządzenia, które wymagają dostępu do programu Dynamics CRM Online musi:
* Można **Android** lub **iOS** urządzenia.
* Można **zarejestrowane** usłudze Microsoft Intune.
* Można **zgodne** ze wszystkimi wdrożone zasady zgodności Microsoft Intune.

Stan urządzenia jest przechowywany w usłudze Azure Active Directory, która na podstawie określonych kryteriów blokuje dostęp lub go przydziela.

Jeśli warunek nie jest spełniony, użytkownik zobaczy podczas logowania jeden z następujących komunikatów:
* Jeśli urządzenie nie jest zarejestrowane w usłudze Microsoft Intune lub nie jest zarejestrowany w usłudze Azure Active Directory, zostanie wyświetlony komunikat z instrukcjami dotyczącymi sposobu instalowania aplikacji portalu firmy i rejestrowania.
* Jeśli urządzenie nie jest zgodne, zostanie wyświetlony komunikat kierujący użytkownika do witryny sieci Web Portal firmy Microsoft Intune lub aplikacji Portal firmy, gdzie można znaleźć informacje o problemie i sposobie jego rozwiązania.

## <a name="configure-conditional-access-for-dynamics-crm-online"></a>Konfigurowania warunkowego dostępu do programu Dynamics CRM Online  
### <a name="step-1-configure-active-directory-security-groups"></a>Krok 1: Skonfiguruj grupy zabezpieczeń usługi Active Directory

Przed rozpoczęciem skonfiguruj grupy zabezpieczeń usługi Azure Active Directory dla zasad dostępu warunkowego. Można skonfigurować te grupy w **Centrum administracyjnym usługi Office 365**. Te grupy będzie służyć do docelowego lub Wykluczeni użytkownicy z zasad. Jeśli zasady obejmują użytkownika, każde używane przez niego urządzenie musi być zgodne, aby mógł uzyskać dostęp do zasobów.

Można określić dwa typy grup dla zasad programu Dynamics CRM:
* **Grupy docelowe** — grupy użytkowników, do których mają dotyczyć zasady.
* **Wykluczone grupy** — grupy użytkowników, którzy są wykluczeni z zasad.

Jeśli użytkownik należy do obu grup, będzie wykluczony z zasad.

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>Krok 2: Konfigurowanie i wdrażanie zasad zgodności
[Tworzenie i wdrażanie](../../protect/deploy-use/device-compliance-policies.md) zasady zgodności dla wszystkich urządzeń, które zostaną zmienione przez zasady. Będą one wszystkich urządzeń, które są używane przez użytkowników w grupach docelowa.

> [!NOTE]
> Gdy zasady zgodności są wdrażane do grupy Microsoft Intune, zasady dostępu warunkowego są przeznaczone do grupy zabezpieczeń usługi Azure Active Directory.

> [!IMPORTANT]
> Jeśli zasady zgodności nie zostaną wdrożone, urządzenia będą traktowane jako zgodne.

Gdy wszystko będzie gotowe, przejdź do kroku 3.
### <a name="step-3-configure-the-dynamics-crm-policy"></a>Krok 3: Konfigurowanie zasad programu Dynamics CRM
Skonfiguruj zasady wymagające, że tylko zarządzane i zgodne urządzenia mają dostęp do programu Dynamics CRM. Te zasady będą przechowywane w usłudze Azure Active Directory.

1.  W konsoli administracyjnej Microsoft Intune, wybierz **zasad > dostępu warunkowego > Dynamics CRM Online zasad**.

     ![Zrzut ekranu strony zasad dostępu warunkowego programu Dynamics CRM Online](media/mdm-ca-dynamics-crm-policy-configuration.png)

2.  Wybierz **Włącz dostęp warunkowy** zasad.
3.  W obszarze **Dostęp do aplikacji**możesz wybrać platformy, do których zostaną zastosowane zasady dostępu warunkowego:
  * **iOS**
  * **Android**
4.  W obszarze **grupy docelowe**, wybierz **Modyfikuj** aby wybrać grupy zabezpieczeń usługi Azure Active Directory, do których mają dotyczyć zasady. Możesz objąć zasadami wszystkich użytkowników lub wybraną grupę.
5.  W obszarze **grupy docelowe**, opcjonalnie wybierz **Modyfikuj** aby wybrać grupy zabezpieczeń usługi Azure Active Directory, które są wykluczone z tej zasady.
6.  Gdy skończysz, wybierz **zapisać**.

Teraz skonfigurowano dostępu warunkowego programu Dynamics CRM. Nie musisz wdrażać zasad dostępu warunkowego; są one aktywne natychmiast.
##  <a name="monitor-the-compliance-and-conditional-access-policies"></a>Monitorowanie zgodności i zasad dostępu warunkowego

W **grup** obszaru roboczego, można wyświetlić stan dostępu warunkowego urządzeń.

Wybierz dowolną grupę urządzeń przenośnych, a następnie na karcie **Urządzenia** wybierz jeden z następujących **filtrów**:
* **Urządzenia, które nie są zarejestrowane w usłudze AAD** — te urządzenia są blokowane Dynamics CRM.
* **Urządzenia, które nie są zgodne z** — te urządzenia są blokowane Dynamics CRM.
* **Urządzenia, które są zarejestrowane w usłudze AAD i są zgodne** — te urządzenia mogą uzyskać dostęp do programu Dynamics CRM.

###  <a name="see-also"></a>Zobacz także
[Zarządzanie dostępem do poczty e-mail](../../protect/deploy-use/manage-email-access.md)

[Zarządzanie dostępem do usługi SharePoint Online](../../protect/deploy-use/manage-sharepoint-online-access.md)

[Zarządzanie dostępem do programu Skype dla usługi Online firmy](../../protect/deploy-use/manage-skype-for-business-online-access.md)

