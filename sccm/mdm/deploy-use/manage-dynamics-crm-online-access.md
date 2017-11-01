---
title: "Zarządzanie dostępem do usługi Dynamics CRM Online"
titleSuffix: Configuration Manager
description: "Informacje o sposobie kontrolowania dostępu do programu Microsoft Dynamics CRM Online z urządzeń iOS i Android przy użyciu dostępu warunkowego Microsoft Intune."
ms.custom: na
ms.date: 03/05/2017
ms.reviewer: na
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2bfc4c51-b25c-4c70-b81e-8a3b6ddf02c8
caps.latest.revision: "5"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 556bb29918327499cc9262a44b9810269d84822a
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="manage-dynamics-crm-online-access-in-system-center-configuration-manager"></a>Zarządzanie dostępem do usługi Dynamics CRM Online w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Dostęp do programu Microsoft Dynamics CRM Online można kontrolować z systemem iOS i urządzeniach z systemem Android przy użyciu dostępu warunkowego Microsoft Intune.  Dostęp warunkowy usługi Intune ma dwa składniki:
* [Zasady zgodności urządzeń](../../protect/deploy-use/device-compliance-policies.md) czy urządzenie musi spełniać, aby zostać uznane za zgodne.
* [Zasady dostępu warunkowego](../../protect/deploy-use/manage-access-to-services.md) który których określane są warunki, które urządzenie musi spełniać w celu uzyskania dostępu do usługi.

Aby dowiedzieć się więcej o sposobie działania dostępu warunkowego, przeczytaj [zarządzanie dostępem do usług](../../protect/deploy-use/manage-access-to-services.md) artykułu.


Jeśli wybrany użytkownik próbuje użyć aplikacji Dynamics CRM na swoim urządzeniu, są następujące kwestie:

![Diagram przedstawiający punkty decyzyjne używane do określenia, czy urządzenie ma mieć dostęp do usługi lub jest zablokowany](media/mdm-ca-dynamics-crm-flow-diagram.png)

Urządzenia, które wymagają dostępu do usługi Dynamics CRM Online, musi:
* Można **Android** lub **iOS** urządzenia.
* Można **zarejestrowane** usłudze Microsoft Intune.
* Można **zgodne** ze wszystkimi wdrożone zasadami zgodności usługi Intune.

Stan urządzenia jest przechowywany w usłudze Azure Active Directory, która na podstawie określonych kryteriów blokuje dostęp lub go przydziela.

Jeśli warunek nie jest spełniony, użytkownik zobaczy podczas logowania jeden z następujących komunikatów:
* Jeśli urządzenie nie zostało zarejestrowane w usłudze Microsoft Intune lub nie jest zarejestrowany w usłudze Azure Active Directory, zostanie wyświetlony komunikat z instrukcjami dotyczącymi sposobu instalowania aplikacji portalu firmy i rejestrowania.
* Jeśli urządzenie nie jest zgodne, zostanie wyświetlony komunikat kierujący użytkownika do witryny sieci Web Portal firmy usługi Microsoft Intune lub aplikacji Portal firmy, gdzie można znaleźć informacje o problemie i sposobie jego rozwiązania.

## <a name="configure-conditional-access-for-dynamics-crm-online"></a>Konfigurowanie dostępu warunkowego dla usługi Dynamics CRM Online  
### <a name="step-1-configure-active-directory-security-groups"></a>Krok 1. Konfigurowanie grup zabezpieczeń usługi Active Directory

Przed rozpoczęciem skonfiguruj grupy zabezpieczeń usługi Azure Active Directory dla zasad dostępu warunkowego. Możesz skonfigurować te grupy w **Centrum administracyjnego usługi Office 365**. Te grupy będą służyć do docelowego lub wykluczenia użytkowników z zasad. Jeśli zasady obejmują użytkownika, każde używane przez niego urządzenie musi być zgodne, aby mógł uzyskać dostęp do zasobów.

Można określić dwa typy grup dla zasad usługi Dynamics CRM:
* **Grupy docelowe** — grupy użytkowników, do których zasady będą stosowane.
* **Wykluczone grupy** — grupy użytkowników, którzy są wykluczeni z zasad.

Jeśli użytkownik należy do obu grup, będzie wykluczony z zasad.

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>Krok 2. Konfigurowanie i wdrażanie zasad zgodności
[Tworzenie i wdrażanie](../../protect/deploy-use/device-compliance-policies.md) zasady zgodności dla wszystkich urządzeń, które będą objęte zasadami. Będą to wszystkie urządzenia, które są używane przez użytkowników do grup docelowych.

> [!NOTE]
> Jeśli zasady zgodności są wdrażane do grup usługi Microsoft Intune, zasady dostępu warunkowego są przeznaczone dla grup zabezpieczeń usługi Azure Active Directory.

> [!IMPORTANT]
> Jeśli zasady zgodności nie zostały wdrożone, urządzenia będą traktowane jako zgodne.

Gdy wszystko będzie gotowe, przejdź do kroku 3.
### <a name="step-3-configure-the-dynamics-crm-policy"></a>Krok 3. Konfigurowanie zasad usługi Dynamics CRM
Skonfiguruj zasady wymagające, aby tylko urządzenia zarządzane i zgodne mogą uzyskiwać dostęp do usługi Dynamics CRM. Te zasady będą przechowywane w usłudze Azure Active Directory.

1.  W konsoli administracyjnej Microsoft Intune, wybierz **zasady > dostęp warunkowy > zasady usługi Dynamics CRM Online**.

     ![Zrzut ekranu przedstawiający stronę zasad dostępu warunkowego usługi Dynamics CRM Online](media/mdm-ca-dynamics-crm-policy-configuration.png)

2.  Wybierz **włączania dostępu warunkowego** zasad.
3.  W obszarze **Dostęp do aplikacji**możesz wybrać platformy, do których zostaną zastosowane zasady dostępu warunkowego:
  * **iOS**
  * **Android**
4.  W obszarze **grupy docelowe**, wybierz **Modyfikuj** aby wybrać grupy zabezpieczeń usługi Azure Active Directory, do których zasady będą stosowane. Możesz objąć zasadami wszystkich użytkowników lub wybraną grupę.
5.  W obszarze **wykluczone grupy**, opcjonalnie wybierz **Modyfikuj** aby wybrać grupy zabezpieczeń usługi Azure Active Directory, które są wykluczone z tych zasad.
6.  Gdy wszystko będzie gotowe, wybierz pozycję **zapisać**.

Warunkowy dostęp został skonfigurowany dla usługi Dynamics CRM. Nie musisz wdrażać zasad dostępu warunkowego; są one aktywne natychmiast.
##  <a name="monitor-the-compliance-and-conditional-access-policies"></a>Monitorowanie zgodności i zasad dostępu warunkowego

W **grup** obszaru roboczego można wyświetlić stan dostępu warunkowego urządzeń.

Wybierz dowolną grupę urządzeń przenośnych, a następnie na karcie **Urządzenia** wybierz jeden z następujących **filtrów**:
* **Urządzenia, które nie są zarejestrowane w usłudze AAD** — te urządzenia są blokowane usługi Dynamics CRM.
* **Urządzenia, które nie są zgodne** — te urządzenia są blokowane usługi Dynamics CRM.
* **Urządzenia, które są zarejestrowane w usłudze AAD i są zgodne** — te urządzenia mogą uzyskiwać dostęp do usługi Dynamics CRM.

###  <a name="see-also"></a>Zobacz także
[Zarządzanie dostępem do poczty e-mail](../../protect/deploy-use/manage-email-access.md)

[Zarządzanie dostępem do usługi SharePoint Online](../../protect/deploy-use/manage-sharepoint-online-access.md)

[Zarządzanie dostępem do usługi Skype dla firm Online](../../protect/deploy-use/manage-skype-for-business-online-access.md)
