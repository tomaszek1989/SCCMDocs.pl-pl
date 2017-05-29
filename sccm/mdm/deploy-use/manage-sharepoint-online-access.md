---
title: "Zarządzanie dostępem do usługi SharePoint Online | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak używać zasad dostępu warunkowego programu System Center Configuration Manager SharePoint Online do zarządzania dostępem do usługi OneDrive."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 49cec466-1676-4fe2-a2fe-5004f01d735e
caps.latest.revision: 11
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: c564c1fc25c5156a2d9ddfa1b4123024c658bf61
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="manage-sharepoint-online-access-in-system-center-configuration-manager"></a>Zarządzanie dostępem do usługi SharePoint Online w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


Użyj programu System Center Configuration Manager **usługi SharePoint Online** zasady dostępu warunkowego w celu zarządzania dostępem do usługi OneDrive biznesowych plików znajdujących się w programie SharePoint online, na podstawie warunków określisz.
Dostęp do programu SharePoint Online można kontrolować z poniższych aplikacji dla wymienionych platform:  

-   Microsoft Office Mobile (Android)  

-   Microsoft OneDrive (Android i iOS)  

-   Microsoft Word (Android i iOS)  

-   Microsoft Excel (Android i iOS)  

-   Microsoft PowerPoint (Android i iOS)  

-   Microsoft OneNote (Android i iOS)

Aplikacji komputerowych pakietu Office można uzyskać dostęp do usługi SharePoint Online na komputerach z systemem:  

-   Pakietem Office 2013 lub nowszym z włączonym [nowoczesnym uwierzytelnianiem](https://support.office.com/en-US/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a) .  

-   Systemem Windows 7.0 lub Windows 8.1  

> [!NOTE]  
>  Komputery powinny zostać przyłączone do domeny lub być zgodnych z zasadami ustawionymi w usłudze Intune.  



 Jeśli wybrany użytkownik próbuje połączyć się z plikiem za pomocą obsługiwanej aplikacji, takiej jak usługa OneDrive, na swoim urządzeniu, sprawdzane są następujące kwestie:  

 ![ConditionalAccess8&#45;6](media/ConditionalAccess8-6.png)  

 Aby nawiązać połączenie z wymaganymi plikami, urządzenie z uruchomioną usługą OneDrive musi:  

-   Być zarejestrowane w usłudze Microsoft Intune lub komputera przyłączonego do domeny.  

-   Zarejestruj urządzenia w usłudze Azure Active Directory (dzieje się to automatycznie podczas rejestrowania urządzenia z usługą Intune.  

     W przypadku komputerów przyłączonych do domeny należy skonfigurować urządzenie do [automatycznego rejestrowania](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/) w usłudze Azure Active Directory.  

-   Być zgodne z zasadami zgodności wdrożonego programu Configuration Manager  

 Stan urządzenia jest przechowywany w usłudze Azure Active Directory, która na podstawie wybranych warunków blokuje dostęp do plików lub go przydziela.  

 Jeśli warunek nie jest spełniony, użytkownik zobaczy podczas logowania jeden z następujących komunikatów:  

-   Jeśli urządzenie nie zostało zarejestrowane w usłudze Intune lub Azure Active Directory, zostanie wyświetlony komunikat z instrukcjami dotyczącymi sposobu instalowania aplikacji portalu firmy i rejestrowania.  

-   Jeśli urządzenie nie jest zgodne, zostanie wyświetlony komunikat kierujący użytkownika do portalu sieci web usługi Intune, gdzie można znaleźć informacje o problemie i sposobie jego rozwiązania.  

- Urządzenia przenośne:

  Istnieje możliwość ograniczenia dostępu do usługi SharePoint Online z przeglądarki na urządzeniach z systemem **iOS** i **Android**.  Dostęp będzie można uzyskiwać tylko z poziomu obsługiwanych przeglądarek na zgodnych urządzeniach:
* Safari (iOS)
* Chrome (Android)
* Managed Browser (iOS i Android)

  Nieobsługiwane przeglądarki zostanie zablokowane.
-   W przypadku komputera:  


    -   Jeśli zasady zostały ustawione tak, aby przyłączenie do domeny było wymagane, a komputer nie został przyłączony do domeny, zostanie wyświetlony komunikat o konieczności skontaktowania się z administratorem IT.  

    -   Jeśli zasady zostały ustawione tak, aby wymagane było przyłączenie do domeny lub zgodność, komputer nie spełnia żadnego z tych wymagań. W takiej sytuacji zostanie wyświetlony komunikat z instrukcjami dotyczącymi sposobu instalowania aplikacji portalu firmy i rejestrowania.  

 Dostęp do usługi SharePoint Online można blokować za pomocą następujących aplikacji:  

-   Microsoft Office Mobile (Android)  

-   Microsoft OneDrive (Android i iOS)  

-   Microsoft Word (Android i iOS)  

-   Microsoft Excel (Android i iOS)  

-   Microsoft PowerPoint (Android i iOS)  

-   Microsoft OneNote (Android i iOS)  

## <a name="configure-conditional-access-for-sharepoint-online"></a>Konfigurowanie dostępu warunkowego dla usługi SharePoint Online  

### <a name="step-1-configure-active-directory-security-groups"></a>Krok 1: Skonfiguruj grupy zabezpieczeń usługi Active Directory  
 Przed rozpoczęciem skonfiguruj grupy zabezpieczeń usługi Azure Active Directory dla zasad dostępu warunkowego. Możesz skonfigurować te grupy w **centrum administracyjnym usługi Office 365** lub w **portalu konta usługi Intune**. Grupy te zawierają użytkowników, którzy będą objęci zasadami lub wykluczeni z nich. Jeśli zasady obejmują użytkownika, każde używane przez niego urządzenie musi być zgodne, aby mógł uzyskać dostęp do zasobów.  

 Możesz określić dwa typy grup dla zasad usługi SharePoint Online:  

-   **Grupy docelowe** â €"grupy użytkowników, do których mają dotyczyć zasady  

-   **Wykluczone grupy** â €"grupy użytkowników, którzy są wykluczeni z zasad (opcjonalnie)  

 Jeśli użytkownik należy do obu grup, będzie wykluczony z zasad.  

### <a name="step-2-configure-and-deploy-a-compliance-policy"></a>Krok 2: Konfigurowanie i wdrażanie zasad zgodności  
 Upewnij się, że utworzono zasady zgodności i wdrożono je na wszystkich urządzeniach, które będą objęte zasadami dostępu usługi SharePoint Online.  

> [!NOTE]  
>  Gdy zasady zgodności są wdrażane dla grup w usłudze Intune lub kolekcji programu Configuration Manager, zasady dostępu warunkowego są przeznaczone do grupy zabezpieczeń usługi Azure Active Directory.  

 Aby uzyskać szczegółowe informacje o tym, jak skonfigurować zasady zgodności, zobacz [Zarządzanie zasadami zgodności urządzeń za pomocą programu System Center Configuration Manager](../../protect/deploy-use/device-compliance-policies.md).  

> [!IMPORTANT]  
>  Jeśli zasady zgodności nie zostaną wdrożone i włączysz zasady dostępu do usługi SharePoint Online, wszystkie objęte nimi urządzenia będą mieć dostęp.  

 Gdy wszystko będzie gotowe, przejdź do **kroku 3**.  

###  <a name="BKMK_OneDrive"></a>Krok 3: Skonfiguruj zasady usługi SharePoint Online  


 Skonfiguruj zasady wymagające, aby tylko urządzenia zarządzane i zgodne miały dostęp do usługi SharePoint Online. Te zasady będą przechowywane w usłudze Azure Active Directory.

 >[!NOTE]
 >Można też utworzyć zasady dostępu warunkowego w konsoli zarządzania programu Azure AD. Konsola zarządzania usługi Azure AD umożliwia tworzenie urządzenia Intune zasady dostępu warunkowego (nazywany zasad dostępu warunkowego opartych na urządzeniach w usłudze Azure AD) oprócz innych zasad dostępu warunkowego, takich jak uwierzytelnianie wieloskładnikowe. Można także ustawić zasady dostępu warunkowego dla aplikacji Enterprise innych firm, takich jak Salesforce i obsługuje okno tej usługi Azure AD. Aby uzyskać więcej informacji, zobacz [sposobu ustawiania zasad dostępu warunkowego opartych na urządzeniach Azure Active Directory do kontroli dostępu do usługi Azure Active Directory połączone aplikacje](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-policy-connected-applications/).  

1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.  

2.  Wybierz pozycję **Włącz zasady dostępu warunkowego dla usługi SharePoint Online**.  

     ![IntuneSASharePointOnlineCAPolicy](media/IntuneSASharePointOnlineCAPolicy.png)  

3.  W obszarze **Dostęp do aplikacji** dla programu Outlook i aplikacji korzystających z nowoczesnego uwierzytelniania możesz ograniczyć dostęp tylko do zgodnych urządzeń dla każdej z platform.  

    > [!TIP]  
    >  **Nowoczesne uwierzytelnianie** umożliwia klientom pakietu Office logowanie się przy użyciu biblioteki uwierzytelniania usługi Active Directory (ADAL).  
    >   
    >  -   Uwierzytelnianie oparte na bibliotece ADAL umożliwia klientom pakietu Office korzystanie z uwierzytelniania za pomocą przeglądarki (nazywanego też uwierzytelnianiem pasywnym).  W celu uwierzytelnienia użytkownik jest kierowany do strony logowania.  
    > -   Ta nowa metoda logowania umożliwia obsługę nowych scenariuszy, takich jak dostęp warunkowy, na podstawie **zgodności urządzeń** oraz tego, czy przeprowadzono **uwierzytelnianie wieloskładnikowe** .  
    >   
    >  W tym [artykule](https://support.office.com/en-US/article/How-modern-authentication-works-for-Office-2013-and-Office-2016-client-apps-e4c45989-4b1a-462e-a81b-2a13191cf517) przedstawiono bardziej szczegółowe informacje dotyczące sposobu działania nowoczesnego uwierzytelniania.  

     Dla systemu windows, komputery komputer musi być albo domeny przyłączony lub zarejestrowane za pomocą usługi Intune i są zgodne. Można ustawić następujące wymagania:  

    -   **Urządzenia muszą zostać przyłączone do domeny lub być zgodne.** Oznacza to, że komputery muszą zostać domeny dołączonym do lub być zgodne z zasadami ustawionymi w usłudze Intune. Jeśli komputer nie spełnia żadnego z tych wymagań, użytkownik jest monitowany o zarejestrowanie urządzenia w usłudze Intune.  

    -   **Urządzenia muszą zostać przyłączone do domeny.** Oznacza to, że komputery muszą zostać przyłączone do domeny, aby mogły uzyskiwać dostęp do usługi Exchange Online. Jeśli komputer nie został przyłączony do domeny, dostęp do poczty e-mail będzie zablokowany, a użytkownik zostanie poproszony o skontaktowanie się z administratorem IT.  

    -   **Urządzenia muszą być zgodne.** Oznacza to, że komputery muszą być zarejestrowane w usłudze Intune i są zgodne. Jeśli komputer nie został zarejestrowany, zostanie wyświetlony komunikat z instrukcjami dotyczącymi rejestrowania.  

4.  W obszarze **dostęp z przeglądarki** do usługi SharePoint Online i OneDrive dla firm, można zezwolić na dostęp do usługi Exchange Online tylko za pośrednictwem obsługiwanych przeglądarek: Safari (iOS), a Chrome (Android). Dostęp z innych przeglądarek zostanie zablokowany.  Ograniczenia platformy wybrane w przypadku dostępu do aplikacji usługi OneDrive mają zastosowanie również w tym miejscu.

    Na urządzeniach z systemem **Android** użytkownicy muszą włączyć dostęp do przeglądarki.  Użytkownik końcowy w tym celu należy włączyć Włącz model obiektów opcji przeglądarki Accessâ€ na zarejestrowanym urządzeniu w następujący sposób:
    1.  Otwórz aplikację **Portal firmy**.
    2.  Przejdź do **ustawienia** strony Potrójna kropki (â €¦) lub przycisk menu sprzętu.
    3.  Naciśnij przycisk **Włącz dostęp za pomocą przeglądarki** .
    4.  W przeglądarce Chrome wyloguj się z usługi Office 365 i uruchom przeglądarkę.

    Na platformach **iOS i Android** w celu zidentyfikowania urządzenia używanego do uzyskania dostępu do usługi usługa Azure Active Directory wystawi certyfikat TLS dla urządzenia.  Urządzenie wyświetla certyfikat z monitem dla użytkownika końcowego o wybranie certyfikatu, tak jak to pokazano na zrzutach ekranu poniżej. Użytkownik końcowy musi wybrać ten certyfikat przed kontynuowaniem pracy z przeglądarką.

     **iOS**

     ![zrzut ekranu przedstawiający monit certyfikatu na urządzeniu iPad](media/mdm-browser-ca-ios-cert-prompt_v2.png)

     **Android**

      ![zrzut ekranu przedstawiający monit certyfikatu na urządzeniu z systemem Android](media/mdm-browser-ca-android-cert-prompt.png)

4.  Na karcie **Narzędzia główne** w grupie **Linki** kliknij pozycję **Konfiguruj zasady dostępu warunkowego w konsoli usługi Intune**. Może być konieczne podanie nazwy użytkownika i hasła konta używanego do łączenia programu Configuration Manager z usługą Intune.  

     Zostanie otwarta konsola administracyjna usługi Intune.  

5.  W [konsoli administracyjnej usługi Microsoft Intune](https://manage.microsoft.com) kliknij kolejno pozycje **Zasady** > **Dostęp warunkowy** > **Zasady usługi SharePoint Online**.  

6.  Wybierz pozycję **Blokuj dostęp aplikacji do usługi SharePoint Online, jeśli urządzenie jest niezgodne**.  

7.  W obszarze **Grupy docelowe** kliknij pozycję **Modyfikuj**, aby wybrać grupy zabezpieczeń usługi Azure Active Directory, których będą dotyczyć zasady.  

8.  W obszarze **Wykluczone grupy** możesz kliknąć pozycję **Modyfikuj**, aby wybrać grupy zabezpieczeń usługi Azure Active Directory wykluczone z tych zasad.  

9. Gdy wszystko będzie gotowe, kliknij pozycję **Zapisz**.  

 Nie musisz wdrażać zasad dostępu warunkowego; są one aktywne natychmiast.  

 Zobacz [dostępu Zarządzanie usługą SharePoint Online w usłudze Microsoft Intune](https://technet.microsoft.com/library/dn705844.aspx) informacji o sposobie można monitorować zasady z poziomu konsoli usługi Intune.  

### <a name="see-also"></a>Zobacz także  

 [Zarządzanie dostępem do usług w programie System Center Configuration Manager](../../protect/deploy-use/manage-access-to-services.md)
