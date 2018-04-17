---
title: Zarządzanie dostępem do poczty e-mail
titleSuffix: Configuration Manager
description: Dowiedz się, jak używać dostępu warunkowego programu System Center Configuration Manager do zarządzania dostępem do poczty e-mail programu Exchange.
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: fa648e73-5fb8-4818-ab57-7466ffaf888e
caps.latest.revision: 24
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: e36674d27757daab9ced4e7e8b51942a4929b5ff
ms.sourcegitcommit: fb84bcb31d825f454785e3d9d8be669e00fe2b27
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="manage-email-access-in-system-center-configuration-manager"></a>Zarządzanie dostępem do poczty e-mail w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Używany System Center Configuration Manager warunkowego dostępu do zarządzania dostępem do poczty e-mail programu Exchange na podstawie warunków, które określisz.  

Możesz zarządzać dostępem do następujących programów i usług:  

-   Lokalny program Microsoft Exchange  

-   Microsoft Exchange Online  

-   Usługa Exchange Online w wersji dedykowanej

Dostęp do programu Exchange Online i lokalnego programu Exchange można kontrolować z wbudowanego klienta poczty e-mail na poniższych platformach:  

-   System android 4.0 i nowsze, Samsung KNOX Standard 4.0 lub nowszy  

-   System iOS 9.0 lub nowszy  

-   System Windows Phone 8.1 lub nowszy  

-   Aplikacja do obsługi poczty w systemie Windows 8.1 lub nowszym

Aplikacje komputerowe pakietu Office można uzyskać dostępu do usługi Exchange Online na komputerach z systemem:  

-   Pakietem Office 2013 lub nowszym z włączonym [nowoczesnym uwierzytelnianiem](https://support.office.com/article/Using-Office-365-modern-authentication-with-Office-clients-776c0036-66fd-41cb-8928-5495c0f9168a).  

-   Systemem Windows 7.0 lub Windows 8.1  

> [!NOTE]  
>  Komputery powinny zostać przyłączone do domeny lub być zgodne z zasadami ustawionymi w usłudze Intune.  


## <a name="device-requirements"></a>Wymagania dotyczące urządzeń
 Jeśli skonfigurujesz dostęp warunkowy, to aby użytkownik mógł połączyć się ze swoją pocztą e-mail, jego urządzenie musi:  

-   Zostać zarejestrowane w usłudze Intune lub przyłączony do domeny.  

-   Rejestrowanie urządzenia w usłudze Azure Active Directory (dzieje się automatycznie, gdy urządzenie jest zarejestrowane w usłudze Intune (tylko w przypadku usługi Exchange Online). ponadto identyfikator klienta programu Exchange ActiveSync musi być zarejestrowany w usłudze Azure Active Directory (nie dotyczy to urządzeń z systemem Windows i Windows Phone łączących się z lokalnym programem Exchange);  

     W przypadku komputera przyłączonego do domeny należy skonfigurować urządzenie do automatycznego rejestrowania w usłudze Azure Active Directory.  Sekcja **Dostęp warunkowy dla komputerów** w temacie [Zarządzanie dostępem do usług w programie System Center Configuration Manager](../../protect/deploy-use/manage-access-to-services.md) zawiera pełen zestaw wymagań dotyczących włączania dostępu warunkowego dla komputerów.  

-   Być zgodne z wdrożonymi na tym urządzeniu zasadami zgodności programu Configuration Manager  

 Jeśli warunki dostępu warunkowego nie zostaną spełnione, użytkownik zobaczy podczas logowania jeden z następujących komunikatów:  

-   Jeśli urządzenie nie jest zarejestrowane w usłudze Intune lub nie jest zarejestrowany w usłudze Azure Active Directory, zostanie wyświetlony komunikat z instrukcjami o sposobie instalowania aplikacji portalu firmy, rejestrowania urządzenia i (w przypadku urządzeń z systemami Android i iOS) i aktywowania poczty e-mail, co umożliwia skojarzenie Identyfikatora programu Exchange ActiveSync urządzenia z rekordem urządzenia w usłudze Azure Active Directory.  

-   Jeśli urządzenie nie jest zgodne, zostanie wyświetlony komunikat kierujący użytkownika do portalu sieci web usługi Intune, gdzie można znaleźć informacje o problemie i sposobie jego rozwiązania.  

**Urządzenia przenośne:**

Istnieje możliwość ograniczenia dostępu do usługi **Outlook Web Access (OWA)** w usłudze Exchange Online w przypadku uzyskiwania dostępu z przeglądarki na urządzeniach z systemem **iOS** i **Android** .  Dostęp będzie można uzyskiwać tylko z poziomu obsługiwanych przeglądarek na zgodnych urządzeniach:

* Safari (iOS)
* Chrome (Android)
* Managed Browser (iOS i Android)

Nieobsługiwane przeglądarki zostaną zablokowane. Aplikacje programu OWA dla systemów iOS i Android nie są obsługiwane.  Powinny one zablokowane za pomocą reguł oświadczeń usług AD FS:
* Aby zablokować nienowoczesne protokoły uwierzytelniania, należy skonfigurować reguły oświadczeń ADFS. Szczegółowe instrukcje zostały przedstawione w scenariuszu 3 — [całkowite blokowanie dostępu do usługi O365 z wyjątkiem aplikacji opartych na przeglądarce](https://technet.microsoft.com/library/dn592182.aspx).

 **W przypadku komputerów:**  

-   Jeśli zasady dostępu warunkowego wymagają zezwolenia na użycie komputerów **przyłączonych do domeny** lub **zgodnych**, zostanie wyświetlony komunikat z instrukcjami dotyczącymi sposobu rejestrowania urządzenia. Jeśli komputer nie spełnia żadnego z tych wymagań, użytkownik zostanie poproszony o zarejestrowanie urządzenia w usłudze Intune.  

-   Jeśli zasady dostępu warunkowego zostały ustawione tak, aby zezwalać tylko na użycie urządzeń z systemem Windows przyłączonych do domeny, urządzenie zostanie zablokowane oraz pojawi się komunikat o konieczności skontaktowania się z administratorem IT.  

 Możesz zablokować dostęp do poczty e-mail programu Exchange z poziomu klienta poczty e-mail programu Exchange ActiveSync dostarczonego z urządzeniem na następujących platformach:  

-   System android 4.0 i nowsze, Samsung KNOX Standard 4.0 lub nowszy  

-   System iOS 9.0 lub nowszy  

-   System Windows Phone 8.1 lub nowszy  

-   Aplikacja **Poczta** w systemie Windows 8.1 lub nowszym  

 Aplikacja Outlook dla systemów iOS i Android oraz aplikacja klasyczna Outlook 2013 lub nowszym są obsługiwane tylko usługi Exchange Online.  

 **Lokalnego programu Exchange connector** programu Configuration Manager i Exchange jest wymagana do działania dostępu warunkowego.  

 Można skonfigurować zasady dostępu warunkowego dla lokalnego programu Exchange z poziomu konsoli programu Configuration Manager. Po skonfigurowaniu zasad dostępu warunkowego dla usługi Exchange Online, możesz rozpocząć ten proces w konsoli programu Configuration Manager, co spowoduje uruchomienie konsoli usługi Intune, w którym można ukończyć proces.  

## <a name="configure-conditional-access"></a>Konfigurowanie dostępu warunkowego
### <a name="step-1-evaluate-the-effect-of-the-conditional-access-policy"></a>Krok 1. Ocena wpływu zasad dostępu warunkowego  
 Po skonfigurowaniu **lokalnego programu Exchange connector**, korzystając z programu Configuration Manager**lista urządzeń uporządkowana według stanu dostępu warunkowego** raport, aby zidentyfikować urządzenia, które będą miały zablokowany dostęp do programu Exchange po skonfigurowaniu zasad dostępu warunkowego. Ten raport wymaga również:  

-   Subskrypcja usługi Intune  

-   skonfigurowania i wdrożenia punktu połączenia usługi.  

 W parametrach raportu wybierz grupę usługi Intune, w której chcesz ocenić i, w razie potrzeby, platformy urządzeń, do których zasady będą stosowane.  

 Więcej informacji o sposobie uruchamiania raportów znajduje się w temacie [Raportowanie w programie System Center Configuration Manager](../../core/servers/manage/reporting.md).  

 Po uruchomieniu raportu sprawdź następujące cztery kolumny w celu określenia, czy użytkownik będzie zablokowany:  

-   **Kanał zarządzania** — wskazuje, czy urządzenie jest zarządzane przez usługę Intune i programu Exchange ActiveSync.  

-   **Zarejestrowane w usłudze AAD** — wskazuje, czy urządzenie jest zarejestrowane w usłudze Azure Active Directory (nazywane dołączanie do miejsca pracy).  

-   **Zgodne** — wskazuje, czy urządzenie jest zgodne ze wszystkimi wdrożonymi zasadami zgodności.  

-   **Aktywowano program EAS** -urządzeń iOS i Android muszą mieć identyfikator programu Exchange ActiveSync skojarzony z rekordem rejestracji urządzenia w usłudze Azure Active Directory. Kojarzenie jest wykonywane, gdy użytkownik kliknie link **Uaktywnij pocztę e-mail** w wiadomości e-mail z kwarantanny.  

    > [!NOTE]  
    >  Urządzenia z systemem Windows Phone zawsze wyświetlają wartość w tej kolumnie.  

 Urządzenia, które należą do grupy lub kolekcji docelowej, nie będą mieć dostępu do programu Exchange, jeśli wartości w kolumnach nie są zgodne z wartościami w poniższej tabeli:  

|Kanał zarządzania|Zarejestrowane w usłudze AAD|zgodnych|Aktywowano program EAS|Wynikowa akcja|  
|------------------------|--------------------|---------------|-------------------|----------------------|  
|**Zarządzane przez usługę Microsoft Intune i program Exchange ActiveSync**|Tak|Tak|Wyświetlana jest wartość**Tak** lub **Nie** |Dozwolony dostęp do poczty e-mail|  
|Dowolna inna wartość|Nie|Nie|Żadna wartość nie jest wyświetlana|Zablokowany dostęp do poczty e-mail|  

 Możesz wyeksportować zawartość raportu i użyć kolumny **Adres e-mail** , aby zawiadomić użytkowników o tym, że będą blokowani.  

### <a name="step-2-configure-user-groups-or-collections-for-the-conditional-access-policy"></a>Krok 2. Konfigurowanie grup użytkowników lub kolekcji dla zasad dostępu warunkowego  
 Zasady dostępu warunkowego są przeznaczone dla różnych grup lub kolekcji użytkowników w zależności od typów zasad. Grupy te zawierają użytkowników, którzy będą objęci zasadami lub wykluczeni z nich. Jeśli zasady obejmują użytkownika, każde używane przez niego urządzenie musi być zgodne, aby mógł uzyskać dostęp do poczty e-mail.  

-   **Zasady usługi Exchange Online** — grupy użytkowników zabezpieczeń usługi Azure Active Directory. Możesz skonfigurować te grupy w **centrum administracyjnym usługi Office 365**lub w **portalu konta usługi Intune**.  

-   **W przypadku zasad lokalnego programu Exchange** — do kolekcji użytkowników programu Configuration Manager. Możesz je konfigurować w obszarze roboczym **Zasoby i zgodność** .  

 Możesz określić dwa typy grup dla każdej zasady:  

-   **Grupy docelowe** — grupy użytkowników lub kolekcji, do których zastosowano zasady  

-   **Wykluczone grupy** — grupy lub użytkowników, kolekcje, które są wykluczone z zasad (opcjonalnie)  

 Jeśli użytkownik należy do obu grup, zostanie wykluczony z zasad.  

 Tylko grupy i kolekcje objęte zasadami dostępu warunkowego są oceniane pod kątem dostępu do programu Exchange.  

### <a name="step-3-configure-and-deploy-a-compliance-policy"></a>Krok 3. Konfigurowanie i wdrażanie zasad zgodności  
 Upewnij się, że utworzono zasady zgodności i wdrożono je na wszystkich urządzeniach, które będą objęte zasadami dostępu warunkowego do programu Exchange.  

 Aby uzyskać szczegółowe informacje o tym, jak skonfigurować zasady zgodności, zobacz [Zarządzanie zasadami zgodności urządzeń za pomocą programu System Center Configuration Manager](device-compliance-policies.md).  

> [!IMPORTANT]  
>  Jeśli zasady zgodności nie zostaną wdrożone i włączysz zasady dostępu warunkowego do programu Exchange, wszystkie objęte nimi urządzenia będą miały dostęp.  

 Gdy wszystko będzie gotowe, przejdź do **kroku 4**.  

### <a name="step-4-configure-the-conditional-access-policy"></a>Krok 4. Konfigurowanie zasad dostępu warunkowego  

#### <a name="for-exchange-online-and-tenants-in-the-new-exchange-online-dedicated-environment"></a>Usługa Exchange Online (i dzierżawy w nowym środowisku usługi Exchange Online w wersji dedykowanej)

>[!NOTE]
>Można też utworzyć zasady dostępu warunkowego w konsoli zarządzania usługą Azure AD. Konsola zarządzania w usłudze Azure AD umożliwia tworzenie urządzeń w usłudze Intune zasady dostępu warunkowego (nazywane zasad dostępu warunkowego opartego na urządzeniach w usłudze Azure AD) oprócz innych zasad dostępu warunkowego, takich jak uwierzytelnianie wieloskładnikowe. Można także ustawić zasady dostępu warunkowego dla aplikacji przedsiębiorstwa innych firm, takich jak Salesforce i obsługuje pole tej usługi Azure AD. Aby uzyskać więcej informacji, zobacz [sposobu ustawiania zasad dostępu warunkowego opartego na urządzenia usługi Azure Active Directory do kontroli dostępu do usługi Azure Active Directory połączone aplikacji](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-policy-connected-applications/).

 Następujący przepływ jest używany przez zasady dostępu warunkowego dla usługi Exchange Online na potrzeby oceniania, czy urządzenia mają mieć do niej dostęp.  

 ![ConditionalAccess8 & #45; 1](media/ConditionalAccess8-1.png)  

 Aby uzyskać dostęp do poczty e-mail, urządzenie musi:  

-   Być zarejestrowane w usłudze Intune  

-   Komputery muszą zostać przyłączone do domeny lub zostać zarejestrowane i zgodne z zasadami ustawionymi w usłudze Intune.  

-   Rejestrowanie urządzenia w usłudze Azure Active Directory (dzieje się automatycznie, gdy urządzenie jest zarejestrowane w usłudze Intune.  

     W przypadku komputerów przyłączonych do domeny musisz skonfigurować [automatyczne rejestrowanie urządzenia](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-automatic-device-registration/) w usłudze Azure Active Directory.  

-   Mieć aktywną pocztę e-mail, co powoduje skojarzenie Identyfikatora programu Exchange ActiveSync urządzenia z rekordem urządzenia w usłudze Azure Active Directory (dotyczy systemów iOS i tylko w przypadku urządzeń z systemem Android).  

-   być zgodne z wdrożonymi zasadami zgodności.  

 Stan urządzenia jest przechowywany w usłudze Azure Active Directory, która blokuje dostęp do poczty e-mail lub go przydziela na podstawie ocenionych warunków.  

 Jeśli warunek nie jest spełniony, użytkownik zobaczy podczas logowania jeden z następujących komunikatów:  

-   Jeśli urządzenie nie jest zarejestrowane w usłudze Azure Active Directory, zostanie wyświetlony komunikat z instrukcjami dotyczącymi sposobu instalowania aplikacji portalu firmy i rejestrowania.  

-   Jeśli urządzenie nie jest zgodne, zostanie wyświetlony komunikat kierujący użytkownika do witryny sieci Web Portal firmy usługi Intune lub aplikacji Portal firmy, gdzie można znaleźć informacje o problemie i sposobie jego rozwiązania.  

-   W przypadku komputera:  

    -   Jeśli zasady zostały ustawione tak, aby przyłączenie do domeny było wymagane, a komputer nie został przyłączony do domeny, zostanie wyświetlony komunikat o konieczności skontaktowania się z administratorem IT.  

    -   Jeśli zasady zostały ustawione tak, aby wymagane było przyłączenie do domeny lub zgodność, komputer nie spełnia żadnego z tych wymagań. W takiej sytuacji zostanie wyświetlony komunikat z instrukcjami dotyczącymi sposobu instalowania aplikacji portalu firmy i rejestrowania.  

 Komunikat jest wyświetlany na urządzeniu w przypadku użytkowników usługi Exchange Online i dzierżaw w nowym środowisku usługi Exchange Online w wersji dedykowanej. Jest także dostarczany do skrzynki odbiorczej poczty e-mail w przypadku lokalnego programu Exchange i starszych urządzeń usługi Exchange Online w wersji dedykowanej.  

> [!NOTE]  
>  Menedżer konfiguracji, które zastępują zasady dostępu warunkowego, zezwalania, blokowania i kwarantanny zdefiniowanych w konsoli administracyjnej usługi Exchange Online.  

> [!NOTE]  
>  Zasady dostępu warunkowego muszą zostać skonfigurowane w konsoli usługi Intune. Aby rozpocząć wykonywanie poniższych czynności, uzyskaj dostęp do konsoli usługi Intune za pośrednictwem programu Configuration Manager. W przypadku wyświetlenia monitu zaloguj się za pomocą poświadczeń użytych w celu skonfigurowania punktu połączenia programu Configuration Manager i usługi Intune.  

##### <a name="to-enable-the-exchange-online-policy"></a>Włączanie zasad usługi Exchange Online  

1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.  

2.  Rozwiń węzeł **Ustawienia zgodności**, rozwiń węzeł **Dostęp warunkowy**, a następnie kliknij pozycję **Exchange Online**.  

3.  Na karcie **Narzędzia główne** w grupie **Linki** kliknij pozycję **Konfiguruj zasady dostępu warunkowego w konsoli usługi Intune**. Należy podać nazwę użytkownika i hasło konta używanego do łączenia programu Configuration Manager z administratorami globalnymi usługi Intune.  

     Zostanie otwarta konsola administracyjna usługi Intune.  

4.  W [konsoli administracyjnej usługi Microsoft Intune](https://manage.microsoft.com)kliknij kolejno pozycje **Zasady** > **Dostęp warunkowy** > **Zasady usługi Exchange Online**.  

     ![HybridOnlineSetupIntune](media/HybridOnlineSetupIntune.png)  

5.  Na stronie **Zasady usługi Exchange Online** zaznacz opcję **Włącz zasady dostępu warunkowego dla usługi Exchange Online**. Jeśli wybierzesz tę opcję, urządzenie musi być zgodne. Jeśli nie wybierzesz tej opcji, dostęp warunkowy nie będzie mieć zastosowania.  

    > [!NOTE]  
    >  Jeśli zasady zgodności nie zostaną wdrożone i włączysz zasady usługi Exchange Online, wszystkie objęte nimi urządzenia będą raportowane jako zgodne.  
    >   
    >  Bez względu na stan zgodności wszyscy użytkownicy, którzy są objęci zasadami będą musieli zarejestrować używane urządzenia w usłudze Intune.  

6.  W obszarze **Dostęp do aplikacji**dla programu Outlook i innych aplikacji korzystających z nowoczesnych metod uwierzytelniania możesz ograniczyć dostęp tylko do zgodnych urządzeń dla każdej z platform.  Urządzenia z systemem Windows muszą zostać przyłączone do domeny lub zostać zarejestrowane w usłudze Intune i być zgodne.  

    > [!TIP]  
    >  **Nowoczesne uwierzytelnianie** umożliwia klientom pakietu Office logowanie się przy użyciu biblioteki uwierzytelniania usługi Active Directory (ADAL).  
    >   
    >  -   Uwierzytelnianie oparte na bibliotece ADAL umożliwia klientom pakietu Office korzystanie z uwierzytelniania za pomocą przeglądarki (nazywanego też uwierzytelnianiem pasywnym).  W celu uwierzytelnienia użytkownik jest kierowany do strony logowania.  
    > -   Ta nowa metoda logowania umożliwia obsługę nowych scenariuszy, takich jak dostęp warunkowy, na podstawie **zgodności urządzeń** oraz tego, czy przeprowadzono **uwierzytelnianie wieloskładnikowe** .  
    >   
    >  W tym [artykule](https://support.office.com/en-US/article/How-modern-authentication-works-for-Office-2013-and-Office-2016-client-apps-e4c45989-4b1a-462e-a81b-2a13191cf517) przedstawiono bardziej szczegółowe informacje dotyczące sposobu działania nowoczesnego uwierzytelniania.  

     Oprócz zarządzania urządzeniami przenośnymi przy użyciu dostępu warunkowego usługa Exchange Online razem z programem Configuration Manager i usługą Intune umożliwiają zarządzanie komputerami. Komputery muszą zostać przyłączone do domeny lub zostać zarejestrowane w usłudze Intune i być zgodne. Można ustawić następujące wymagania:  

    -   **Urządzenia muszą zostać przyłączone do domeny lub być zgodne.** Komputery muszą zostać przyłączone do domeny lub być zgodne z zasadami. Jeśli komputer nie spełnia żadnego z tych wymagań, użytkownik jest monitowany o zarejestrowanie urządzenia w usłudze Intune.  

    -   **Urządzenia muszą zostać przyłączone do domeny.** Komputery muszą zostać przyłączone do domeny, aby mogły uzyskiwać dostęp do usługi Exchange Online. Jeśli komputer nie został przyłączony do domeny, dostęp do poczty e-mail będzie zablokowany, a użytkownik zostanie poproszony o skontaktowanie się z administratorem IT.  

    -   **Urządzenia muszą być zgodne.** Komputery muszą być zarejestrowane w usłudze Intune i zgodne. Jeśli komputer nie został zarejestrowany, zostanie wyświetlony komunikat z instrukcjami dotyczącymi rejestrowania.  

7.  W obszarze **programu Outlook web access (OWA)**, można zezwolić na dostęp do usługi Exchange Online tylko za pośrednictwem obsługiwanych przeglądarek: Safari (iOS) i Chrome (Android). Dostęp z innych przeglądarek zostanie zablokowany. Ograniczenia platformy wybrane w przypadku dostępu do aplikacji dla programu Outlook mają zastosowanie również w tym miejscu.

    Na urządzeniach z systemem **Android** użytkownicy muszą włączyć dostęp do przeglądarki.  W tym celu użytkownik końcowy musi włączyć opcję "Włącz dostęp za pomocą przeglądarki" na zarejestrowanym urządzeniu w następujący sposób:
     1. Otwórz aplikację **Portal firmy**.
     2. Przejdź do **ustawienia** strony z przycisku wielokropka (...) lub przycisku menu sprzętu.
      3.    Naciśnij przycisk **Włącz dostęp za pomocą przeglądarki** .
      4.    W przeglądarce Chrome wyloguj się z usługi Office 365 i uruchom przeglądarkę.

     Na platformach **iOS i Android** w celu zidentyfikowania urządzenia używanego do uzyskania dostępu do usługi usługa Azure Active Directory wystawi certyfikat TLS dla urządzenia.  Urządzenie wyświetla certyfikat z monitem dla użytkownika końcowego o wybranie certyfikatu, tak jak to pokazano na zrzutach ekranu poniżej. Użytkownik końcowy musi wybrać ten certyfikat przed kontynuowaniem pracy z przeglądarką.

     **iOS**

     ![zrzut ekranu przedstawiający monit certyfikatu na urządzeniu iPad](media/mdm-browser-ca-ios-cert-prompt_v2.png)

    **Android**

    ![zrzut ekranu przedstawiający monit certyfikatu na urządzeniu z systemem Android](media/mdm-browser-ca-android-cert-prompt.png)

7.  W przypadku**aplikacji poczty programu Exchange ActiveSync**możesz zablokować dostęp do usługi Exchange Online z poziomu poczty e-mail, jeśli urządzenie jest niezgodne, a także zdecydować, czy zezwolić na dostęp do poczty e-mail bądź go zablokować, jeśli usługa Intune nie może zarządzać urządzeniem.  

8.  W obszarze **Grupy docelowe**wybierz grupy zabezpieczeń użytkowników usługi Active Directory obejmowane przez te zasady.  

    > [!NOTE]  
    >  W przypadku użytkowników należących do grup docelowych zasady usługi Intune spowodują zastąpienie reguł i zasad programu Exchange.  
    >   
    >  Program Exchange będzie tylko wymuszać reguły zezwalania, blokowania i kwarantanny programu Exchange oraz zasady programu Exchange w następujących sytuacjach:  
    >   
    >  -   Użytkownik nie ma licencji na usługę Intune.  
    > -   Użytkownik ma licencję na usługę Intune, ale nie należy do żadnej grupy zabezpieczeń użytej w zasadach dostępu warunkowego.  

9. W obszarze **Wykluczone grupy**wybierz grupy zabezpieczeń użytkowników usługi Active Directory wykluczane z tych zasad. Jeśli użytkownik należy zarówno do grupy objętej zasadami, jak i do grupy wykluczonej z zasad, zostanie wykluczony z zasad i będzie mieć dostęp do swojej poczty e-mail.  

10. Po zakończeniu kliknij pozycję **Zapisz**.  

-   Nie musisz wdrażać zasad dostępu warunkowego; są one aktywne natychmiast.  

-   Gdy użytkownik utworzy konto e-mail, urządzenie zostanie od razu zablokowane.  

-   Jeśli zablokowany użytkownik zarejestruje urządzenia w usłudze Intune (lub rozwiąże problemy z niezgodnością), dostęp do poczty e-mail zostanie odblokowany w ciągu 2 minut.  

-   Jeśli użytkownik wyrejestruje swoje urządzenie, poczta e-mail zostanie zablokowana po około 6 godzinach.  

### <a name="for-exchange-on-premises-and-tenants-in-the-legacy-exchange-online-dedicated-environment"></a>Lokalny program Exchange (i dzierżawy w starszym środowisku usługi Exchange Online w wersji dedykowanej)  
 Następujący przepływ jest używany przez zasady dostępu warunkowego dla lokalnego programu Exchange i dzierżaw w starszej usłudze Exchange Online w wersji dedykowanej na potrzeby oceniania, czy zezwolić na dostęp urządzeń, czy też zablokować urządzenia.  

 ![ConditionalAccess8&#45;2](media/ConditionalAccess8-2.png)  

##### <a name="to-enable-the-exchange-on-premises-policy"></a>Włączanie zasad lokalnego programu Exchange  

1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.  

2.  Rozwiń węzeł **Ustawienia zgodności**, rozwiń węzeł **Dostęp warunkowy**, a następnie kliknij pozycję **Lokalny program Exchange**.  

3.  Na karcie **Narzędzia główne** w grupie **Lokalny program Exchange** kliknij pozycję **Konfiguruj zasady dostępu warunkowego**.  

4.  **Począwszy od wersji 1602 programu Configuration Manager**, na stronie **Ogólne** **Kreatora konfiguracji zasad dostępu warunkowego**określ, czy chcesz zastąpić domyślną regułę programu Exchange Active Sync. Kliknij tę opcję, jeśli chcesz, aby zarejestrowane i zgodne urządzenia zawsze miały dostęp do poczty e-mail, nawet wtedy, gdy domyślna reguła określa kwarantannę lub blokowanie dostępu.  

    > [!NOTE]  
    >  Istnieje problem z zastępowaniem ustawień domyślnych w przypadku urządzeń z systemem Android. Jeśli dla domyślnej reguły dostępu serwera Exchange wybrano ustawienie **Zablokuj** , a zasady dostępu warunkowego programu Exchange są włączone z opcją zastępowania domyślnej reguły, urządzenia Android użytkowników docelowych mogą nie zostać odblokowane nawet wtedy, gdy urządzenia są zarejestrowane w usłudze Intune i zgodne.  Aby obejść ten problem, ustaw domyślną regułę dostępu programu Exchange na **Kwarantanna**. Urządzenie nie będzie domyślnie uzyskiwać dostępu do programu Exchange, a administrator może otrzymać z serwera Exchange raport zawierający listę urządzeń objętych kwarantanną.  

     Jeśli podczas konfigurowania łącznika programu Exchange nie zostało skonfigurowane konto powiadomień e-mail, na tej stronie zostanie wyświetlone ostrzeżenie, a przycisk **Dalej** zostanie wyłączony.  Zanim przejdziesz dalej, musisz najpierw skonfigurować ustawienia powiadomień e-mail w programie Exchange Connector, a następnie wrócić do **Kreatora konfiguracji zasad dostępu warunkowego** w celu ukończenia procesu.  

     ![HybridCondAccessWiz1](media/HybridCondAccessWiz1.PNG)  

     Kliknij przycisk **Dalej**.  

5.  Na stronie **Kolekcje docelowe** dodaj jedną lub więcej kolekcji użytkowników. Aby uzyskać dostęp do programu Exchange, użytkownicy w tych kolekcjach muszą zarejestrować swoje urządzenia w usłudze Intune i muszą być zgodni z zasadami zgodności wdrożone.  

     ![HybridCondAccessWiz2](media/HybridCondAccessWiz2.PNG)  

     Kliknij przycisk **Dalej**.  

6.  Na stronie **Wykluczone kolekcje** dodaj dowolne kolekcje użytkowników, które mają być wykluczone z zasad dostępu warunkowego. Użytkownicy w tych grupach, nie muszą rejestrować swoje urządzenia w usłudze Intune i nie muszą być zgodne z wdrożonymi zasadami zgodności, aby dostęp do programu Exchange.  

     ![HybridCondAccessWiz3](media/HybridCondAccessWiz3.png)  

     Jeśli użytkownik należy zarówno do listy objętej zasadami, jak i do listy wykluczonej z zasad, zostanie wykluczony z zasad dostępu warunkowego.  

     Kliknij przycisk **Dalej**.  

7.  Na **edytowanie powiadomienia użytkownika** skonfiguruj wiadomości e-mail wysyłanej przez usługę Intune z instrukcjami dotyczącymi odblokowywania urządzenia (jako uzupełnienie wiadomości e-mail wysyłanej przez program Exchange).  

     Możesz zmienić domyślną wiadomość i użyć tagów HTML do formatowania wyświetlania tekstu. Możesz też wysłać wcześniej do pracowników wiadomość e-mail z informacjami o nadchodzących zmianach i instrukcjami dotyczącymi rejestrowania urządzeń.  

     ![HybridCondAccessWiz4](media/HybridCondAccessWiz4.PNG)  

    > [!NOTE]  
    >  Ponieważ powiadomienie e-mail usługi Intune instrukcjami odblokowywania jest dostarczane do skrzynki pocztowej programu Exchange użytkownika, w przypadku, gdy urządzenie użytkownika zostanie zablokowane przed odebraniem wiadomości e-mail, ich użyć niezablokowanego urządzenia lub innej metody dostępu do programu Exchange i wyświetlić wiadomość.  

    > [!NOTE]  
    >  Aby program Exchange mógł wysłać powiadomienie e-mail, musisz skonfigurować konto, które będzie używane do wysyłania powiadomień e-mail. Czynność tę wykonujesz podczas konfigurowania właściwości łącznika serwera Exchange.  
    >   
    >  Aby uzyskać szczegółowe informacje, zobacz [Zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md).  

     Kliknij przycisk **Dalej**.  

8.  Na stronie  **Podsumowanie** przejrzyj ustawienia, a następnie zakończ działanie kreatora.  

-   Nie musisz wdrażać zasad dostępu warunkowego; są one aktywne natychmiast.  

-   Po skonfigurowaniu przez użytkownika profilu programu Exchange ActiveSync, może potrwać od 1 do 3 godzin urządzenia do zablokowania (Jeśli nie jest zarządzany przez usługę Intune).  

-   Jeśli zablokowany użytkownik następnie zarejestruje urządzenie w usłudze Intune (lub rozwiąże problemy z niezgodnością), dostęp do poczty e-mail zostanie odblokowany w ciągu 2 minut.  

-   Jeśli użytkownik wyrejestruje-urządzenie z usługi Intune może potrwać od 1 do 3 godzin zablokowanie urządzenia.  

### <a name="see-also"></a>Zobacz także  
 [Zarządzanie dostępem do usług w programie System Center Configuration Manager](../../protect/deploy-use/manage-access-to-services.md)
