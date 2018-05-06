---
title: Zarządzanie dostępem do usługi SharePoint Online
titleSuffix: Configuration Manager
description: Dowiedz się, jak korzystać z programu System Center Configuration Manager SharePoint Online zasad dostępu warunkowego do zarządzania dostępem do usługi OneDrive.
ms.date: 12/09/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 49cec466-1676-4fe2-a2fe-5004f01d735e
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: f723110abdb94dd96fb2ed7f52af681d27fccf87
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="manage-sharepoint-online-access-in-system-center-configuration-manager"></a>Zarządzanie dostępem do usługi SharePoint Online w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


Zasady dostępu warunkowego programu Configuration Manager dla **usługi SharePoint Online** zarządza dostępem do usługi OneDrive dla firm pliki, które są przechowywane w usłudze SharePoint Online. Dostęp jest oparty na podanych warunków.
Dostęp do programu SharePoint Online można kontrolować z poniższych aplikacji dla wymienionych platform:  

-   Microsoft Office Mobile (Android)  

-   Microsoft OneDrive (Android i iOS)  

-   Microsoft Word (Android i iOS)  

-   Microsoft Excel (Android i iOS)  

-   Microsoft PowerPoint (Android i iOS)  

-   Microsoft OneNote (Android i iOS)

Aplikacje komputerowe pakietu Office można uzyskać dostępu do usługi SharePoint Online na komputerach z systemem:  

-   Pakietem Office 2013 lub nowszym z włączonym [nowoczesnym uwierzytelnianiem](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a).  

-   Systemem Windows 7.0 lub Windows 8.1  

> [!NOTE]  
>  Komputery powinny zostać przyłączone do domeny lub być zgodne z zasadami ustawionymi w usłudze Intune.  



 Wybrany użytkownik próbuje połączyć się z plikiem za pomocą obsługiwanej aplikacji, np. OneDrive na urządzeniu, następujące kwestie:  

 ![ConditionalAccess8&#45;6](media/ConditionalAccess8-6.png)  

 Aby nawiązać połączenie z wymaganymi plikami, urządzenie z uruchomioną usługą OneDrive musi:  

-   Zostać zarejestrowane w usłudze Microsoft Intune lub przyłączony do domeny.  

-   Rejestrowanie urządzenia w usłudze Azure Active Directory (Azure AD). Rejestracja odbywa się automatycznie podczas rejestrowania urządzenia w usłudze Intune.  

     W przypadku komputerów przyłączonych do domeny, należy skonfigurować go do [automatycznego rejestrowania](/azure/active-directory/device-management-hybrid-azuread-joined-devices-setup) z usługą Azure AD.  

-   Być zgodne z wdrożonymi zasadami zgodności programu Configuration Manager  

    Usługi Azure AD przechowuje stan urządzenia. Przyznaje lub blokuje dostęp do plików, na podstawie wybranych warunków, które określisz.  

    Jeśli warunek nie jest spełniony, użytkownik zobaczy jeden z następujących komunikatów podczas logowania:  

-   Jeśli urządzenie nie jest zarejestrowane w usłudze Intune lub nie jest zarejestrowany w usłudze Azure AD, zostanie wyświetlony komunikat z instrukcjami dotyczącymi sposobu instalowania aplikacji Portal firmy i rejestrowania.  

-   Jeśli urządzenie nie jest zgodne, zostanie wyświetlony komunikat kierujący użytkownika do portalu sieci web usługi Intune. Można znaleźć informacje o problemie i sposobie jego rozwiązania.  

- Urządzenia przenośne:

  Możesz ograniczyć dostęp do usługi SharePoint Online podczas uzyskiwania dostępu do w przeglądarce na **iOS** i **Android** urządzeń. Dostęp jest dozwolony tylko za pomocą obsługiwanych przeglądarek na zgodnych urządzeniach:  
    - Safari (iOS)
    - Chrome (Android)
    - Managed Browser (iOS i Android)  

    Nieobsługiwane przeglądarki są zablokowane.  

-   W przypadku komputera:  


    -   Jeśli zasady zostały ustawione tak, aby wymagane było przyłączenie do domeny, a komputer nie jest przyłączony do domeny, zostanie wyświetlony komunikat do kontaktowania się z administratorem IT.  

    -   Jeśli zasady zostały ustawione tak, aby wymagane było przyłączenie do domeny lub być zgodne, a komputer nie spełnia żadnego z tych wymagań, zostanie wyświetlony komunikat z instrukcjami dotyczącymi sposobu instalowania aplikacji Portal firmy i rejestrowania.  

Dostęp do usługi SharePoint Online można blokować za pomocą następujących aplikacji:  

-   Microsoft Office Mobile (Android)  

-   Microsoft OneDrive (Android i iOS)  

-   Microsoft Word (Android i iOS)  

-   Microsoft Excel (Android i iOS)  

-   Microsoft PowerPoint (Android i iOS)  

-   Microsoft OneNote (Android i iOS)  



## <a name="configure-conditional-access-for-sharepoint-online"></a>Konfigurowanie dostępu warunkowego dla usługi SharePoint Online  

### <a name="step-1-configure-active-directory-security-groups"></a>Krok 1. Konfigurowanie grup zabezpieczeń usługi Active Directory  
 Przed rozpoczęciem Skonfiguruj grupy zabezpieczeń usługi Azure AD dla zasad dostępu warunkowego. Możesz skonfigurować te grupy w **centrum administracyjnym usługi Office 365**lub w **portalu konta usługi Intune**. Grupy te zawierają użytkowników, którzy są objęci lub wykluczeni z zasad. Jeśli użytkownik podlega zasadom, każde urządzenie, którego używają musi być zgodne, dostęp do zasobów.  

 Możesz określić dwa typy grup dla zasad usługi SharePoint Online:  

-   **Grupy docelowe**: Grupy użytkowników, których dotyczą zasady  

-   **Wykluczone grupy**: Grupy użytkowników, którzy są wykluczeni z zasad (opcjonalnie)  

 Jeśli użytkownik należy do obu grup, są wykluczone z zasad.  

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>Krok 2. Konfigurowanie i wdrażanie zasad zgodności  
 Tworzenie i wdrażanie zasad zgodności na wszystkich urządzeniach, do których zostanie rozpoczęta dla zasad usługi SharePoint Online.  

> [!NOTE]   
>  Jeśli zasady zgodności są wdrażane do grup w usłudze Intune lub kolekcji programu Configuration Manager, zasady dostępu warunkowego są przeznaczone dla grup zabezpieczeń usługi Azure AD.  

 Aby uzyskać szczegółowe informacje o tym, jak skonfigurować zasady zgodności, zobacz [Zarządzanie zasadami zgodności urządzeń za pomocą programu System Center Configuration Manager](../../protect/deploy-use/device-compliance-policies.md).  

> [!IMPORTANT]  
>  Jeśli zasady zgodności nie zostały wdrożone i włączysz zasady usługi SharePoint Online, wszystkie objęte nimi urządzenia mają dostęp.  

   

###  <a name="BKMK_OneDrive"></a> Krok 3. Konfigurowanie zasad usługi SharePoint Online  

 Skonfiguruj zasady wymagające, aby tylko urządzenia zarządzane i zgodne miały dostęp do usługi SharePoint Online. Te zasady są przechowywane w usłudze Azure AD.

 >[!NOTE]
 >Można też utworzyć zasady dostępu warunkowego w konsoli zarządzania usługą Azure AD. Konsola zarządzania usługą Azure AD umożliwia tworzenie zasad dostępu warunkowego urządzeń usługi Intune. Usługi Azure AD odwołuje się do tych zasad jako zasady dostępu warunkowego opartego na urządzeniu. Można również utworzyć innych zasad dostępu warunkowego, takich jak uwierzytelnianie wieloskładnikowe. W portalu można ustawić zasady dostępu warunkowego dla aplikacji innych firm, które obsługuje usługę Azure AD, takie jak Salesforce i pola. Aby uzyskać więcej informacji, zobacz [sposobu ustawiania zasad dostępu warunkowego opartego na urządzenia usługi Azure AD do kontroli dostępu do usługi Azure AD połączone aplikacji](/azure/active-directory/active-directory-conditional-access-policy-connected-applications).  

1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.  

2.  Wybierz **Włącz zasady dostępu warunkowego dla usługi SharePoint Online**.  

     ![IntuneSASharePointOnlineCAPolicy](media/IntuneSASharePointOnlineCAPolicy.png)  

3.  W obszarze **Dostęp do aplikacji** dla programu Outlook i aplikacji korzystających z nowoczesnego uwierzytelniania możesz ograniczyć dostęp tylko do zgodnych urządzeń dla każdej z platform.  

    > [!TIP]  
    >  **Nowoczesne uwierzytelnianie** oferuje klientom pakietu Office na podstawie Active Directory Authentication Library ADAL logowania.  
    >   
    >  -   Uwierzytelniania opartego na bibliotece ADAL umożliwia klientom pakietu Office do prowadzenia uwierzytelnianie za pomocą przeglądarki (nazywanego też uwierzytelnianiem pasywnym). W celu uwierzytelnienia użytkownik jest kierowany do strony logowania.  
    > -   Ta nowa metoda logowania umożliwia obsługę nowych scenariuszy, takich jak dostęp warunkowy, na podstawie **zgodności urządzeń**oraz tego, czy **uwierzytelnianie wieloskładnikowe** została wykonana.  
    >   
    >  Aby uzyskać więcej informacji, zobacz [sposobu działania nowoczesnego uwierzytelniania dla aplikacji klienckich pakietu Office 2013 i Office 2016](https://support.office.com/article/How-modern-authentication-works-for-Office-2013-and-Office-2016-client-apps-e4c45989-4b1a-462e-a81b-2a13191cf517).  

     Dla komputerów z systemem windows komputer musi być domeny przyłączone lub zarejestrowane w usłudze Intune i zgodne. Można ustawić następujące wymagania:  

    -   **Urządzenia muszą być przyłączone do domeny lub zgodne**: Komputery muszą zostać przyłączone do domeny lub zgodne z zasadami ustawionymi w usłudze Intune. Jeśli komputer nie spełnia żadnego z tych wymagań, użytkownik jest monitowany o zarejestrowanie urządzenia w usłudze Intune.  

    -   **Urządzenia muszą być przyłączone do domeny**: Komputery muszą zostać przyłączone do dostępu do usługi Exchange Online do domeny. Jeśli komputer nie został przyłączony do domeny, dostęp do poczty e-mail będzie zablokowany, a użytkownik jest monitowany o kontakt z administratorem IT.  

    -   **Urządzenia muszą być zgodne**: Komputery muszą być zarejestrowane w usłudze Intune i zgodne. Jeśli komputer nie jest zarejestrowany, zostanie wyświetlony komunikat z instrukcjami dotyczącymi rejestrowania.  

4.  W obszarze **dostęp za pomocą przeglądarki** do usługi SharePoint Online i OneDrive dla firm można zezwolić na dostęp do usługi Exchange Online tylko za pośrednictwem obsługiwanych przeglądarek: Safari (iOS) i Chrome (Android). Dostęp z innych przeglądarek będzie zablokowany. Ograniczenia platformy wybrane w przypadku dostępu do aplikacji usługi OneDrive mają zastosowanie również w tym miejscu.

    Na **Android** urządzeń, użytkownicy muszą włączyć **włączyć dostęp za pomocą przeglądarki** opcji na zarejestrowanym urządzeniu w następujący sposób:
    1.  Otwórz aplikację **Portal firmy**.
    2.  Przejdź do **ustawienia** strony z przycisku wielokropka (...) lub przycisku menu sprzętu.
    3.  Naciśnij przycisk **Włącz dostęp za pomocą przeglądarki** .
    4.  W przeglądarce Chrome wyloguj się z usługi Office 365 i uruchom przeglądarkę.

    Na **z systemem iOS i Android** platformy, aby zidentyfikować urządzenia, które jest używane do uzyskania dostępu do usługi Azure AD wystawia certyfikat TLS na urządzeniu. Urządzenie Wyświetla certyfikatu monitu dla użytkownika końcowego, aby wybrać certyfikat, jak pokazano na poniższych zrzutach ekranu: Użytkownik końcowy musi wybrać ten certyfikat, aby kontynuować korzystanie z przeglądarki.

     **iOS**

     ![Zrzut ekranu przedstawiający monit certyfikatu na Ipadzie](media/mdm-browser-ca-ios-cert-prompt_v2.png)

     **Android**

      ![zrzut ekranu przedstawiający monit certyfikatu na urządzeniu z systemem Android](media/mdm-browser-ca-android-cert-prompt.png)

4.  Na karcie **Narzędzia główne** w grupie **Linki** kliknij pozycję **Konfiguruj zasady dostępu warunkowego w konsoli usługi Intune**. Może być konieczne podanie nazwy użytkownika i hasła konta używanego do łączenia programu Configuration Manager z usługą Intune.  

     Zostanie otwarta konsola administracyjna usługi Intune.  

5.  W [konsoli administracyjnej usługi Microsoft Intune](https://manage.microsoft.com) kliknij kolejno pozycje **Zasady** > **Dostęp warunkowy** > **Zasady usługi SharePoint Online**.  

6.  Wybierz pozycję **Blokuj dostęp aplikacji do usługi SharePoint Online, jeśli urządzenie jest niezgodne**.  

7.  W obszarze **grupy docelowe**, kliknij przycisk **Modyfikuj** aby wybrać grupy zabezpieczeń usługi Azure AD, do których ma zastosowanie zasad.  

8.  W obszarze **wykluczone grupy**, opcjonalnie kliknij **Modyfikuj** aby wybrać grupy zabezpieczeń usługi Azure AD, które są wykluczone z tych zasad.  

9. Gdy wszystko będzie gotowe, kliknij pozycję **Zapisz**.  

 Nie musisz wdrażać zasad dostępu warunkowego, one aktywne natychmiast.  

 Zobacz [dostępu Zarządzanie usługą SharePoint Online w usłudze Microsoft Intune](/intune-classic/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune) uzyskać informacji na temat sposobu monitorowania zasad za pomocą konsoli usługi Intune.  

### <a name="see-also"></a>Zobacz także  

 [Zarządzanie dostępem do usług w programie System Center Configuration Manager](../../protect/deploy-use/manage-access-to-services.md)
