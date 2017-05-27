---
title: "Zarządzanie dostępem do usługi O365 dla komputerów zarządzanych | Dokumentacja firmy Microsoft"
description: "Informacje o sposobie konfigurowania warunkowego dostępu do komputerów, które są zarządzane przez program System Center Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 34024741-edfa-4088-8599-d6bafc331e62
caps.latest.revision: 15
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 23b1d24e908d04b64c3bbfa518793a44e696d468
ms.openlocfilehash: e9028a54e538b4ec987dbaeb5ba1ee22ad091728
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="manage-access-to-o365-services-for-pcs-managed-by-system-center-configuration-manager"></a>Zarządzanie dostępem do usług O365 dla komputerów zarządzanych przez program System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*



 Począwszy od wersji 1602 programu Configuration Manager, można skonfigurować dostępu warunkowego dla komputerów zarządzanych przez program System Center Configuration Manager.  

> [!IMPORTANT]  
>  Jest to wersja wstępna funkcją dostępną w ramach aktualizacji 1602, aktualizować 1606 i zaktualizować 1610. Funkcje wersji wstępnej są zawarte w produkcie do wczesnego testowania w środowisku produkcyjnym, ale nie powinny być uznawane za gotowe do produkcji. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą [używania funkcji w wersjach wstępnych z poziomu aktualizacji](../../core/servers/manage/install-in-console-updates.md#bkmk_prerelease).
> - Po zainstalowaniu aktualizacji 1602 typu funkcji zostanie zwolniony, mimo że jest to wersja wstępna.
> - Następnie zaktualizuj się od 1602 do 1606, wyświetla typ funkcji zwolnione nawet za jego pośrednictwem nadal wersji wstępnej.
> - Jeśli aktualizacja z wersji 1511 bezpośrednio do 1606 typu funkcji jest wyświetlana jako wersji wstępnej.

 Jeśli szukasz informacji na temat konfigurowania dostępu warunkowego dla urządzeń zarejestrowanych w usłudze Intune i zarządzanych przez tę usługę lub komputerów przyłączonych do domeny, które nie są oceniane pod kątem zgodności, zobacz [Zarządzanie dostępem do usług w programie System Center Configuration Manager](../../protect/deploy-use/manage-access-to-services.md).  


## <a name="supported-services"></a>Obsługiwane usługi  

-   Exchange Online  

-   SharePoint Online  

## <a name="supported-pcs"></a>Obsługiwane komputery  

-   Windows 7  

-   Windows 8.1  

-   Windows 10 

## <a name="configure-conditional-access"></a>Konfigurowanie dostępu warunkowego  
 Aby skonfigurować dostęp warunkowy, musisz najpierw utworzyć zasady zgodności i skonfigurować zasady dostępu warunkowego. Po skonfigurowaniu zasad dostępu warunkowego dla komputerów możesz wymagać zgodności komputerów z zasadami zgodności w celu uzyskiwania dostępu do usług Exchange Online i SharePoint Online.  

### <a name="prerequisites"></a>Wymagania wstępne  

-   Usługa ADFS Sync i subskrypcja usługi O365. Subskrypcja usługi O365 służy do konfigurowania usług Exchange Online i SharePoint Online.  

-   Subskrypcja usługi Microsoft Intune. Subskrypcję usługi Microsoft Intune należy skonfigurować w konsoli programu Configuration Manager. Nadal wymaga to wdrożenia hybrydowego.  

 Komputery muszą spełniać następujące wymagania:  

-   [Wymagania wstępne](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/?rnd=1) automatycznej rejestracji urządzeń w usłudze Azure Active Directory  

     Komputery można zarejestrować w usłudze Azure AD za pomocą zasad zgodności.  

    -   W przypadku komputerów z systemem Windows 8.1 i Windows 10 można użyć zasad grup usługi Active Directory do skonfigurowania urządzeń do automatycznej rejestracji w usłudze Azure AD.  

    -   W przypadku komputerów z systemem Windows 7 należy wdrożyć pakiet oprogramowania rejestracji urządzenia na komputerze z systemem Windows 7 za pomocą programu System Center Configuration Manager. [Urządzenia automatycznego rejestracji z urządzeń Azure Active Directory for Windows Domain-Joined](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/?rnd=1) temat ma więcej szczegółów.  

-   Należy użyć pakietu Office 2013 lub Office 2016 z [włączonym](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a)uwierzytelnianiem nowoczesnym.  

 Kroki opisane poniżej dotyczą usług Exchange Online i SharePoint Online  

### <a name="step-1-configure-compliance-policy"></a>Krok 1. Konfigurowanie zasad zgodności  
 W konsoli programu Configuration Manager utwórz zasady zgodności z następującymi regułami:  

-   Wymagaj rejestracji w usłudze Azure Active Directory: Ta reguła sprawdza, jeśli urządzenie użytkownika miejscu pracy przyłączone do usługi Azure AD, a w przeciwnym razie urządzenia zostanie automatycznie zarejestrowany w usłudze Azure AD. Automatyczna rejestracja jest obsługiwana tylko w systemie Windows 8.1. W przypadku komputerów z systemem Windows 7 należy wdrożyć instalatora MSI w celu przeprowadzenia rejestracji automatycznej. Aby uzyskać więcej informacji, zobacz [Automatic device registration with Azure Active Directory](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/?rnd=1)(Automatyczna rejestracja urządzeń w usłudze Azure Active Directory).  

-   **Zainstalowano wszystkie wymagane aktualizacje z terminem starsze niż określoną liczbę dni:** Ta reguła sprawdza, czy urządzenie użytkownika zawiera wszystkie wymagane aktualizacje (określone w regule wymagane aktualizacje automatyczne) w ramach terminu i okres prolongaty określonej przez Ciebie i automatycznie zainstalować wszelkie oczekujące aktualizacje.  

-   **Wymagaj szyfrowania dysków funkcją BitLocker:** Jest to sprawdź, czy dysk podstawowy (np. C:\\) na urządzeniu jest funkcją BitLocker zaszyfrowane. Jeśli szyfrowanie funkcją BitLocker nie jest włączone na głównym urządzeniu, dostęp do poczty e-mail i usług SharePoint jest zablokowany.  

-   **Wymagaj ochrony przed złośliwym oprogramowaniem:** Jest to sprawdź, czy oprogramowanie ochrony przed złośliwym oprogramowaniem (System Center Endpoint Protection lub Windows Defender) jest włączona i uruchomiona. Jeśli takie oprogramowanie nie jest włączone, dostęp do poczty e-mail i usług SharePoint jest zablokowany.  

### <a name="step-2-evaluate-the-effect-of-conditional-access"></a>Krok 2. Ocena wpływu dostępu warunkowego  
 Uruchom raport zgodności z dostępem warunkowym. Można go znaleźć w ramach monitorowania raporty w sekcji > Zarządzanie zgodnością i ustawieniami. Spowoduje to wyświetlenie stanu zgodności wszystkich urządzeń.  Dostęp urządzeń zgłoszonych jako niezgodne do usług Exchange Online i SharePoint Online będzie blokowany.  

 ![CA&#95;compliance&#95;report](media/CA_compliance_report.png)  

### <a name="configure-active-directory-security-groups"></a>Konfigurowanie grup zabezpieczeń usługi Active Directory  
 Zasady dostępu warunkowego są przeznaczone dla grup użytkowników w zależności od typów zasad. Grupy te zawierają użytkowników, którzy będą objęci zasadami lub wykluczeni z nich. Jeśli zasady obejmują użytkownika, każde używane przez niego urządzenie musi być zgodne, aby mógł uzyskać dostęp do usługi.  

 Grupy użytkowników zabezpieczeń usługi Active Directory. Te grupy użytkowników powinny być zsynchronizowane z usługą Azure Active Directory. Możesz skonfigurować te grupy również w centrum administracyjnym usługi Office 365 lub w portalu konta usługi Intune.  

 Można określić dwa typy grup, w każdej z zasad. :  

-   **Grupy docelowe** — grupy użytkowników, dla których są stosowane zasady. Należy używać tej samej grupy, zarówno dla zgodności i zasad dostępu warunkowego.  

-   **Wykluczone grupy** — grupy użytkowników, którzy są wykluczeni z zasad (opcjonalnie)  
    Jeśli użytkownik należy do obu grup, zostanie wykluczony z zasad.  

     Tylko grupy objęte zasadami dostępu warunkowego są oceniane.  

### <a name="step-3--create-a-conditional-access-policy-for-exchange-online-and-sharepoint-online"></a>Krok 3.  Tworzenie zasad dostępu warunkowego dla usług Exchange Online i SharePoint Online  

1.  W konsoli programu Configuration Manager kliknij pozycję **Zasoby i zgodność**.  

2.  Aby utworzyć zasady dla usługi Exchange Online, wybierz opcję **Włącz zasady dostępu warunkowego dla usługi Exchange Online**.  

     Aby utworzyć zasady dla usługi SharePoint Online, wybierz opcję **Włącz zasady dostępu warunkowego dla usługi Exchange Online**.  

3.  Na karcie **Narzędzia główne** w grupie **Linki** kliknij pozycję **Konfiguruj zasady dostępu warunkowego w konsoli usługi Intune**. Może być konieczne podanie nazwy użytkownika i hasła konta używanego do łączenia programu Configuration Manager z usługą Intune.  

     Zostanie otwarta konsola administracyjna usługi Intune.  

4.  Dla usługi Exchange Online w konsoli administracyjnej Microsoft Intune, kliknij przycisk **zasad > dostępu warunkowego > zasady usługi Exchange Online**.  

     Dla usługi SharePoint Online w konsoli administracyjnej Microsoft Intune, kliknij przycisk **zasad > dostępu warunkowego > zasady usługi SharePoint Online**.  

5.  Wybierz dla wymagań dla komputerów z systemem Windows opcję**Urządzenia muszą być zgodne**.  

6.  W obszarze **Grupy docelowe**kliknij pozycję **Modyfikuj** , aby wybrać grupy zabezpieczeń usługi Azure Active Directory, których będą dotyczyć zasady.  

    > [!NOTE]  
    >  Należy używać tej samej grupy zabezpieczeń użytkowników do wdrażania zasad compliancy i Grupa docelowa dla zasad dostępu warunkowego.  

     W obszarze **Wykluczone grupy**możesz kliknąć pozycję **Modyfikuj** , aby wybrać grupy zabezpieczeń usługi Azure Active Directory wykluczone z tych zasad.  

7.  Kliknij przycisk **Zapisz** , aby utworzyć i zapisać zasady  

 Użytkowników końcowych, którzy są blokowane z powodu niezgodności będą wyświetlać informacje o zgodności w Centrum oprogramowania System Center Configuration Manager i będzie inicjował nowej oceny zasad, gdy są rozwiązywane problemy ze zgodnością.  

<!---
##  <a name="bkmk_KnownIssues"></a> Known issues  
 You may see the following issues when using this feature:  

-   In this 1602 update,  the 5 day compliance is not enforced. Even if compliance check on the end-user's device has happened more than 5 days ago, users still can access Office 365 and SharePoint online.  

-   When a device is not compliant with the compliance policy, the reason is not automatically displayed. The end- user must go to the new Software Center to find the reason for non-compliance. The reason is displayed in the Device compliance section of the Software Center.  

-   Windows 10 users may see multiple access failures when trying to reach O365 and/or SharePoint online resources. Note that conditional access is not fully supported for Windows 10.  
--->
### <a name="see-also"></a>Zobacz także  
 [Ochrona infrastruktury danych i witryny z System Center Configuration Manager](../../protect/understand/protect-data-and-site-infrastructure.md)

