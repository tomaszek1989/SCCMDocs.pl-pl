---
title: Zarządzanie dostępem do usługi O365
titleSuffix: Configuration Manager
description: Informacje o sposobie konfigurowania warunkowego dostępu do usług Office 365 dla komputerów, które są zarządzane przez program System Center Configuration Manager.
ms.date: 04/10/2018
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 34024741-edfa-4088-8599-d6bafc331e62
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 7bf7114382c956dcac6302b3fc11617ad6b5eeec
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="manage-access-to-o365-services-for-pcs-managed-by-system-center-configuration-manager"></a>Zarządzanie dostępem do usług O365 dla komputerów zarządzanych przez program System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

<!--1191496-->
Konfigurowanie warunkowego dostępu do usług Office 365 dla komputerów zarządzanych przez program Configuration Manager.  

> [!Note]  
> Ta funkcja opcjonalna nie włączyć domyślne programu Configuration Manager. Należy włączyć tę funkcję, przed jego użyciem. Aby uzyskać więcej informacji, zobacz [Włącz funkcje opcjonalne aktualizacji](/sccm/core/servers/manage/install-in-console-updates#bkmk_options).<!--505213-->  


Aby uzyskać informacje na temat konfigurowania dostępu warunkowego dla urządzeń zarejestrowanych i zarządzanych przez program Microsoft Intune, zobacz [zarządzanie dostępem do usług w programie System Center Configuration Manager](../../protect/deploy-use/manage-access-to-services.md). Ten artykuł obejmuje także urządzenia, które są domeny przyłączone i nie ocenione pod kątem zgodności.

## <a name="supported-services"></a>Obsługiwane usługi  

-   Exchange Online
-   SharePoint Online

## <a name="supported-pcs"></a>Obsługiwane komputery  

-   Windows 7
-   Windows 8.1
-   Windows 10

## <a name="supported-windows-servers"></a>Obsługiwane w systemach Windows Server

-   Windows Server 2008 R2
-   Windows Server 2012
-   Windows Server 2012 R2
-   Windows Server 2016

    > [!IMPORTANT]
    > Dla serwerów systemu Windows, który może mieć wielu użytkowników jednocześnie zalogowany należy wdrożyć te same zasady dostępu warunkowego dla wszystkich użytkowników.

## <a name="configure-conditional-access"></a>Konfigurowanie dostępu warunkowego  
 Aby skonfigurować dostęp warunkowy, należy najpierw utworzyć zasady zgodności i skonfigurować zasady dostępu warunkowego. Po skonfigurowaniu zasad dostępu warunkowego dla komputerów można wymagać, aby komputery być zgodne, aby uzyskiwać dostęp do usług Exchange Online i SharePoint Online.  

### <a name="prerequisites"></a>Wymagania wstępne  

-   Usługa ADFS Sync i subskrypcja usługi O365. Subskrypcja usługi O365 służy do konfigurowania usług Exchange Online i SharePoint Online.  

-   Subskrypcja usługi Microsoft Intune. Subskrypcję usługi Microsoft Intune należy skonfigurować w konsoli programu Configuration Manager. Subskrypcję usługi Intune służy do przekazywania stan zgodności urządzenia do usługi Azure Active Directory i licencjonowania na użytkownika.  

 Komputery muszą spełniać następujące wymagania:  

-   [Wymagania wstępne](https://docs.microsoft.com/azure/active-directory/device-management-hybrid-azuread-joined-devices-setup) automatycznej rejestracji urządzeń w usłudze Azure Active Directory  

     Komputery można zarejestrować w usłudze Azure AD za pomocą zasad zgodności.  

    -   W przypadku komputerów z systemem Windows 8.1 i Windows 10 można użyć zasad grup usługi Active Directory do skonfigurowania urządzeń do automatycznej rejestracji w usłudze Azure AD.  

    -   W przypadku komputerów z systemem Windows 7 należy wdrożyć pakiet oprogramowania rejestracji urządzenia na komputerze z systemem Windows 7 za pomocą programu System Center Configuration Manager. [Automatycznej rejestracji urządzeń z urządzeniami Joined](https://docs.microsoft.com/azure/active-directory/device-management-hybrid-azuread-joined-devices-setup) artykuł zawiera więcej szczegółowych informacji.  

-   Należy użyć pakietu Office 2013 lub Office 2016 z [włączonym](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) uwierzytelnianiem nowoczesnym.  

 Poniższe kroki dotyczą zarówno usługi Exchange Online i SharePoint Online  

### <a name="step-1-configure-compliance-policy"></a>Krok 1. Konfigurowanie zasad zgodności  
 W konsoli programu Configuration Manager utwórz zasady zgodności z następującymi regułami:  

-   **Wymagaj rejestracji w usłudze Azure Active Directory:** Ta reguła sprawdza, czy urządzenie użytkownika jest miejscu pracy zostało dołączone do usługi Azure AD, a jeśli nie, urządzenie jest automatycznie rejestrowane w usłudze Azure AD. Automatyczna rejestracja jest obsługiwana tylko w systemie Windows 8.1. W przypadku komputerów z systemem Windows 7 należy wdrożyć instalatora MSI w celu przeprowadzenia rejestracji automatycznej. Aby uzyskać więcej informacji, zobacz [automatycznej rejestracji urządzeń z usługą Azure Active Directory](https://docs.microsoft.com/azure/active-directory/device-management-hybrid-azuread-joined-devices-setup)  

-   **Zainstalowano wszystkie wymagane aktualizacje z ostatecznym terminem przypadającym wcześniej niż określona liczba dni temu:** Określ wartość dla okresu prolongaty od ostatecznego terminu wdrożenia wymagane aktualizacje na urządzeniu użytkownika. Dodanie tę regułę również automatycznie instaluje wszystkie oczekujące wymagane aktualizacje. Określ wymagane aktualizacje w **wymagane aktualizacje automatyczne** reguły.   

-   **Wymagaj szyfrowania dysków funkcją BitLocker:** Ta reguła sprawdza, czy dysk podstawowy (na przykład C:\\) na urządzeniu jest funkcją BitLocker zaszyfrowany. Jeśli funkcja Bitlocker nie jest włączone szyfrowanie na urządzeniu podstawowym dostęp do poczty e-mail i usług SharePoint jest zablokowany.  

-   **Wymagaj ochrony przed złośliwym oprogramowaniem:** Ta reguła sprawdza, czy System Center Endpoint Protection lub usługa Windows Defender jest włączona i uruchomiona. Jeśli takie oprogramowanie nie jest włączone, dostęp do poczty e-mail i usług SharePoint jest zablokowany.  

-   **Zgłoszone w dobrej kondycji przez usługę zaświadczania o kondycji:** Ten warunek obejmuje cztery reguły podrzędne, aby sprawdzić zgodność urządzenia z usługą zaświadczania o kondycji urządzenia. Aby uzyskać więcej informacji, zobacz [zaświadczania o kondycji](/sccm/core/servers/manage/health-attestation). 

    - **Wymagaj funkcji BitLocker można włączyć w urządzeniu**
    - **Wymagaj Bezpieczny rozruch jest włączony na urządzeniu** 
    - **Wymagaj integralności kodu jest włączone na urządzeniu**
    - **Wymaga wcześniejszego uruchomienia przed złośliwym oprogramowaniem włączenia na urządzeniu**  

    >[!Tip]  
    > Kryteria dostępu warunkowego zaświadczania o kondycji została wprowadzona w wersji 1710 jako [funkcji wersji wstępnej](/sccm/core/servers/manage/pre-release-features). Począwszy od wersji 1802, ta funkcja nie jest już funkcji wersji wstępnej.<!--1235616-->  

    > [!Note]  
    > Ta funkcja opcjonalna nie włączyć domyślne programu Configuration Manager. Należy włączyć tę funkcję, przed jego użyciem. Aby uzyskać więcej informacji, zobacz [Włącz funkcje opcjonalne aktualizacji](/sccm/core/servers/manage/install-in-console-updates#bkmk_options).<!--505213-->  

### <a name="step-2-evaluate-the-effect-of-conditional-access"></a>Krok 2. Ocena wpływu dostępu warunkowego  
 Uruchom **raport zgodności z dostępem warunkowym**. Można je znaleźć w **monitorowanie** obszarze roboczym **raporty** > **Zarządzanie zgodnością i ustawieniami**. Ten raport wyświetla stan zgodności dla wszystkich urządzeń. Raportowania jako zgodne urządzenia będą miały dostępu do usługi Exchange Online i SharePoint Online.  

 ![Konsola programu Configuration Manager, obszar roboczy monitorowanie, raportowanie, raporty, Zarządzanie zgodnością i ustawieniami: Raport zgodności z dostępem warunkowym](media/CA_compliance_report.png)  

### <a name="configure-active-directory-security-groups"></a>Konfigurowanie grup zabezpieczeń usługi Active Directory  
 Zasady dostępu warunkowego są przeznaczone dla grup użytkowników w zależności od typów zasad. Grupy te zawierają użytkowników, które zasady elementy docelowe lub wykluczone z zasad. Jeśli zasady jest przeznaczony dla użytkownika, każde urządzenie, którego używają musi być zgodne w celu uzyskania dostępu do usługi.  

 Grupy użytkowników zabezpieczeń usługi Active Directory. Te grupy użytkowników powinny być zsynchronizowane z usługą Azure Active Directory. Możesz skonfigurować te grupy również w centrum administracyjnym usługi Office 365 lub w portalu konta usługi Intune.  

 Można określić dwa typy grup, w każdej z zasad. :  

-   **Grupy docelowe** — grupy użytkowników, dla których zasady są stosowane. Należy używać tej samej grupy, zgodności i zasad dostępu warunkowego.  

-   **Wykluczone grupy** — grupy użytkowników, którzy są wykluczeni z zasad (opcjonalnie).  
    Jeśli użytkownik należy zarówno, są wykluczone z zasad.  

     Tylko grupy objęte zasadami dostępu warunkowego są oceniane.  

### <a name="step-3-create-a-conditional-access-policy-for-exchange-online-and-sharepoint-online"></a>Krok 3. Tworzenie zasad dostępu warunkowego dla usług Exchange Online i SharePoint Online  

1.  W konsoli programu Configuration Manager kliknij pozycję **Zasoby i zgodność**.  

2.  Aby utworzyć zasady dla usługi Exchange Online, wybierz opcję **Włącz zasady dostępu warunkowego dla usługi Exchange Online**.  

     Aby utworzyć zasady dla usługi SharePoint Online, wybierz opcję **Włącz zasady dostępu warunkowego dla usługi Exchange Online**.  

3.  Na karcie **Narzędzia główne** w grupie **Linki** kliknij pozycję **Konfiguruj zasady dostępu warunkowego w konsoli usługi Intune**. Może być konieczne podanie nazwy użytkownika i hasła konta używanego do łączenia programu Configuration Manager z usługą Intune.  

     Zostanie otwarta konsola administracyjna usługi Intune.  

4.  Dla usługi Exchange Online w konsoli administracyjnej Microsoft Intune, kliknij przycisk **zasady > dostęp warunkowy > zasady usługi Exchange Online**.  

     Dla usługi SharePoint Online w konsoli administracyjnej Microsoft Intune, kliknij przycisk **zasady > dostęp warunkowy > zasady usługi SharePoint Online**.  

5.  Wybierz dla wymagań dla komputerów z systemem Windows opcję**Urządzenia muszą być zgodne**.  

6.  W obszarze **grupy docelowe**, kliknij przycisk **Modyfikuj** aby wybrać grupy zabezpieczeń usługi Azure Active Directory, do których ma zastosowanie zasad.  

    > [!NOTE]  
    >  Należy używać tej samej grupy użytkowników zabezpieczeń do wdrożenia zasad zgodności i Grupa docelowa dla zasad dostępu warunkowego.  

     W obszarze **Wykluczone grupy**możesz kliknąć pozycję **Modyfikuj** , aby wybrać grupy zabezpieczeń usługi Azure Active Directory wykluczone z tych zasad.  

7.  Kliknij przycisk **Zapisz** , aby utworzyć i zapisać zasady  

Użytkownicy wyświetlać informacje o zgodności w programie Software Center. Gdy zablokowany z powodu niezgodności, zainicjowana nowa ocena zasad po korygowania problemów ze zgodnością.  


## <a name="see-also"></a>Zobacz także

- [Ochrona danych i infrastruktury lokacji z System Center Configuration Manager](../../protect/understand/protect-data-and-site-infrastructure.md)
- [Rozwiązywanie problemów z dostępu warunkowego flow-chart programu Configuration Manager](https://gallery.technet.microsoft.com/Conditional-access-fd747c1a?redir=0)
