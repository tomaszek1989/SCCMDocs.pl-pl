---
title: "Dostęp warunkowy | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak używać dostępu warunkowego w programie System Center Configuration Manager ułatwia zabezpieczanie poczty e-mail i innych usług."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b04727b-d563-422f-8d59-4dd66215d0b3
caps.latest.revision: 26
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: d6933a331bb229f7e378e8f0bfa511f6b0553ae9
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---

# <a name="manage-access-to-services-in-system-center-configuration-manager"></a>Zarządzanie dostępem do usług w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


## <a name="conditional-access-in-system-center-configuration-manager"></a>Dostęp warunkowy w programie System Center Configuration Manager
Użyj **dostępu warunkowego** ułatwia zabezpieczanie poczty e-mail i innych usług na urządzeniach, które są zarejestrowane w usłudze Microsoft Intune, w zależności od określonych kryteriów.  

 Informacje o **dostępu warunkowego na komputerach, które są zarządzane przy użyciu System Center Configuration Manager** i oceny zgodności, zobacz [zarządzanie dostępem do usługi O365 dla komputerów zarządzanych przez program System Center Configuration Manager](../../protect/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm.md).  


 Typowy przepływ dla dostępu warunkowego może wyglądać następująco:  

 ![ConditionalAccess4](media/ConditionalAccess4.png)  

 Dostęp warunkowy umożliwia zarządzanie dostępem do następujących usług:  

-   Lokalny program Microsoft Exchange  

-   Microsoft Exchange Online  

-   Usługa Exchange Online w wersji dedykowanej  

-   SharePoint Online  

-   Skype dla firm Online

-   Dynamics CRM Online

 Aby zaimplementować dostęp warunkowy, należy skonfigurować dwa typy zasad w programie Configuration Manager:  

-   **Zasady zgodności** są opcjonalnymi zasadami, które można wdrożyć dla kolekcji użytkowników, aby oceniać ustawienia, takie jak:  

    -   Kod dostępu  

    -   Szyfrowanie  

    -   Określanie, czy urządzenie ma złamane zabezpieczenia lub odblokowany dostęp  

    -   Czy wiadomości e-mail na urządzeniu jest zarządzane przez zasady usługi Intune lub programu Configuration Manager  

     **Jeśli to nie wdrożono żadnych zasad zgodności na urządzeniu, a następnie wszystkie zasady dostępu warunkowego zastosowanie, będą traktować to urządzenie jako zgodne**.  

-   **Zasady dostępu warunkowego** są skonfigurowane dla określonej usługi i definiują reguły, takich jak które Azure Active Directory grupy użytkowników zabezpieczeń lub kolekcje użytkowników programu Configuration Manager będą kierowane lub wyłączać.  

     Konfigurowanie zasad dostępu warunkowego lokalnego programu Exchange z konsoli programu Configuration Manager. Jednak podczas konfigurowania zasad usługi Exchange Online lub Online programu SharePoint zostanie otwarta konsola administracyjna Intune konfigurowania zasad.  

     W odróżnieniu od innych zasad usługi Intune lub programu Configuration Manager nie należy wdrażać zasad dostępu warunkowego. Zamiast tego użytkownik konfiguruje je jednorazowo, a następnie stosuje do wszystkich użytkowników docelowych.  

 Gdy urządzenia nie spełniają skonfigurowanych warunków, użytkownik jest przeprowadzany przez procedurę rejestracji urządzenia i rozwiązywania problemu, w związku z którym urządzenie nie może być zgodne.  

**Przed** rozpocząć korzystanie z dostępu warunkowego, upewnij się, że masz poprawne **wymagania** w miejscu:  

## <a name="requirements-for-exchange-online-using-the-shared-multi-tenant-environment"></a>Wymagania programu Exchange Online (korzystająca ze współużytkowanego środowiska z wieloma dzierżawami)
Dostęp warunkowy do usługi Exchange Online obsługuje urządzenia, na których są uruchomione:
-   Windows 8.1 lub nowszy (jeśli jest zarejestrowane w usłudze Intune)
-   System Windows w wersji 7.0 lub Windows 8.1 (gdy są przyłączone do domeny)
-   System Windows Phone 8.1 lub nowszy
-   System iOS 7.1 lub nowszy
-   Android 4.0 i nowsze, Samsung KNOX Standard 4.0 i nowsze

 **Ponadto**:
-   Urządzenia muszą być dołączone do obszaru roboczego, co spowoduje rejestrację urządzenia za pomocą usługi Azure Active Directory urządzenia rejestracji (AAD DRS).<br />     
- Komputery przyłączone do domeny muszą być automatycznie rejestrowane w usłudze Azure Active Directory za pomocą funkcji MSI lub zasad grupy.

  W sekcji **Dostęp warunkowy dla komputerów** tego tematu opisano wszystkie wymagania dotyczące włączania dostępu warunkowego na komputerze.<br />     
  Usługa AAD DRS zostanie automatycznie uaktywniona dla klientów usług Intune i Office 365. Klienci, którzy już wdrożyli usługę rejestrowania urządzeń usług AD FS, nie będą widzieć zarejestrowanych urządzeń w lokalnej usłudze Active Directory.
-   Należy użyć subskrypcji usługi Office 365 obejmującej usługę Exchange Online (na przykład E3), a użytkownicy muszą mieć licencję programu Exchange Online.
-   Opcjonalny **łącznika serwera Exchange** jest opcjonalny i łączy z programu Configuration Manager z usługą Microsoft Exchange Online i ułatwia monitorowanie informacji o urządzeniu za pośrednictwem konsoli programu Configuration Manager (zobacz [zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md)).
Łącznik nie musi być używany do stosowania zasad zgodności lub dostępu warunkowego, ale jest wymagany do uruchamiania raportów umożliwiających ocenę wpływu dostępu warunkowego.

## <a name="requirements-for-exchange-online-dedicated"></a>Wymagania dotyczące programu Exchange Online w wersji dedykowanej
Dostęp warunkowy do usługi Exchange Online w wersji dedykowanej obsługuje urządzenia, na których są uruchomione:
-   System Windows 8 lub nowszy (jeśli jest zarejestrowane w usłudze Intune)
-   System Windows w wersji 7.0 lub Windows 8.1 (gdy są przyłączone do domeny)

  Dostęp warunkowy do komputerów przyłączonych do domeny tylko do dzierżawców w nowym dedykowanym środowisku usługi Exchange Online.
-   System Windows Phone 8 lub nowszy
-   Dowolne urządzenie systemu iOS, które używa klienta poczty e-mail programu Exchange ActiveSync (EAS)
-   System android 4 lub nowszy.
-   W przypadku dzierżaw w **starszej wersji środowiska usługi Exchange Online w wersji dedykowanej**:    

  Należy użyć **łącznika serwera Exchange** którego programu Configuration Manager łączy się z lokalnego programu Microsoft Exchange. Pozwala to zarządzać urządzeniami przenośnymi i umożliwia dostęp warunkowy (zobacz [Zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md)).
-   W przypadku dzierżaw w **nowego środowiska usługi Exchange Online w wersji dedykowanej**:     
  Opcjonalny **łącznika serwera Exchange** łączy Menedżera konfiguracji programu Microsoft Exchange Online i ułatwia zarządzanie informacjami o urządzeniu (zobacz [zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md)). Łącznik nie musi być używany do stosowania zasad zgodności lub dostępu warunkowego, ale jest wymagany do uruchamiania raportów umożliwiających ocenę wpływu dostępu warunkowego.  

## <a name="requirements-for-exchange-on-premises"></a>Wymagania dla lokalnego programu Exchange
Dostęp warunkowy do lokalnego programu Exchange obsługuje:
-   System Windows 8 lub nowszy (jeśli jest zarejestrowane w usłudze Intune)
-   System Windows Phone 8 lub nowszy
-   Aplikacja Native poczty e-mail w systemie iOS
-   Aplikacja Native poczty e-mail na Android 4 lub nowszy
-   Aplikacja Microsoft Outlook nie jest obsługiwane (Android i iOS).

**Ponadto**:

-  Wersja programu Exchange musi być Exchange 2010 lub nowszej. Macierz serwerów dostępu klienta (CAS) serwera programu Exchange jest obsługiwana.

> [!TIP]
> Jeśli do konfiguracji serwera CAS środowiska serwera Exchange, należy skonfigurować łącznika programu Exchange lokalnie do wskazania jednego z serwerów urzędów certyfikacji.
- Należy użyć **łącznika serwera Exchange** którego programu Configuration Manager łączy się z lokalnego programu Microsoft Exchange. Pozwala to zarządzać urządzeniami przenośnymi i umożliwia dostęp warunkowy (zobacz [Zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md)).
  - Upewnij się, że używasz najnowszej wersji **łącznika lokalnego programu Exchange**. Łącznik lokalnego programu Exchange należy skonfigurować za pomocą konsoli programu Configuration Manager. Aby uzyskać szczegółowe wskazówki, zobacz [Zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md).
  - Łącznik może być skonfigurowany tylko w lokacji głównej programu System Center Configuration Manager.</li><li>Ten łącznik obsługuje środowisko serwera CAS programu Exchange. <br />        Podczas konfigurowania łącznika należy ustawić go tak, aby komunikował się z jednym z serwerów CAS programu Exchange.

- Program Exchange ActiveSync można skonfigurować przy użyciu uwierzytelniania opartego na certyfikatach lub wpisu poświadczeń użytkownika.


## <a name="requirements-for-skype-for-business-online"></a>Wymagania dotyczące programu Skype dla firm Online
Dostęp warunkowy do usługi SharePoint Online obsługuje urządzenia, na których uruchomiono:
 -   System iOS 7.1 lub nowszy
 -   Android 4.0 i nowsze
 -   KNOX Samsung Standard 4.0 lub nowszy

**Ponadto** należy włączyć nowoczesnego uwierzytelniania dla programu Skype dla firmy Online. Wypełnij ten [formularz Connect](https://connect.microsoft.com/office/Survey/NominationSurvey.aspx?SurveyID=17299&ProgramID=8715) , aby zarejestrować się w programie nowoczesnego uwierzytelniania.

Wszyscy użytkownicy końcowi muszą używać programu Skype dla firm Online. Jeśli masz wdrożenie z programem Skype dla firm Online oraz lokalną instalacją programu Skype dla firm, zasady dostępu warunkowego nie będą stosowane wobec użytkowników, którzy korzystają z lokalnego wdrożenia programu.

## <a name="requirements-for-sharepoint-online"></a>Wymagania dotyczące programu SharePoint Online
Dostęp warunkowy do usługi SharePoint Online obsługuje urządzenia, na których uruchomiono:
 -   Windows 8.1 lub nowszy (jeśli jest zarejestrowane w usłudze Intune)
 -   System Windows w wersji 7.0 lub Windows 8.1 (gdy są przyłączone do domeny)
 -   System Windows Phone 8.1 lub nowszy
 -   System iOS 7.1 lub nowszy
 -   Android 4.0 i nowsze, Samsung KNOX Standard 4.0 i nowsze

 **Ponadto**:
 -   Urządzenia muszą być dołączone do obszaru roboczego, co spowoduje rejestrację urządzenia za pomocą usługi Azure Active Directory urządzenia rejestracji (AAD DRS).

 Komputery przyłączone do domeny muszą być automatycznie rejestrowane w usłudze Azure Active Directory za pomocą funkcji MSI lub zasad grupy. W sekcji **Dostęp warunkowy dla komputerów** tego tematu opisano wszystkie wymagania dotyczące włączania dostępu warunkowego na komputerze.

 Usługa AAD DRS zostanie automatycznie uaktywniona dla klientów usług Intune i Office 365. Klienci, którzy już wdrożyli usługę rejestrowania urządzeń usług AD FS, nie będą widzieć zarejestrowanych urządzeń w lokalnej usłudze Active Directory.
 -   Wymagana jest subskrypcja usługi SharePoint Online, a użytkownicy muszą mieć licencję programu SharePoint Online.

 ### <a name="conditional-access-for-pcs"></a>Dostęp warunkowy dla komputerów

 Dostęp warunkowy można skonfigurować dla komputerów z aplikacjami klasycznymi pakietu Office, aby uzyskiwać dostęp do usług **Exchange Online** i **SharePoint Online** na komputerach spełniających następujące wymagania:
 -   Komputer musi działać system Windows w wersji 7.0 lub Windows 8.1.
 -   Komputer musi być przyłączone do domeny lub zgodne.

 Aby być zgodne, komputer musi być zarejestrowany w usłudze Intune i zgodne z zasadami.

 W przypadku komputerów przyłączonych do domeny musisz skonfigurować [automatyczne rejestrowanie urządzenia](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/) w usłudze Azure Active Directory.
 -   [Należy włączyć nowoczesne uwierzytelnianie usługi Office 365](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/) i zainstalować wszystkie najnowsze aktualizacje pakietu Office.<br />     Nowoczesne uwierzytelniane umożliwia logowanie do klientów systemu Windows z pakietem Office 2013 oparte na bibliotece Active Directory Authentication Library (ADAL), a także udostępnia lepsze zabezpieczenia, takie jak **uwierzytelnianie wieloskładnikowe**i **uwierzytelnianie oparte na certyfikatach**.
 -   Aby zablokować nienowoczesne protokoły uwierzytelniania, należy skonfigurować reguły oświadczeń ADFS.  

## <a name="next-steps"></a>Następne kroki  
 Przeczytaj następujące tematy, aby dowiedzieć się, jak skonfigurować zasady zgodności i zasady dostępu warunkowego dla wymaganego scenariusza:  

-   [Zarządzanie zasadami zgodności urządzeń w programie System Center Configuration Manager](../../protect/deploy-use/device-compliance-policies.md)  

-   [Zarządzanie dostępem do poczty e-mail w programie System Center Configuration Manager](../../protect/deploy-use/manage-email-access.md)  

-   [Zarządzanie dostępem do usługi SharePoint Online w programie System Center Configuration Manager](../../protect/deploy-use/manage-sharepoint-online-access.md)  

-   [Zarządzanie Skype dostępu dla biznesowych Online](../../protect/deploy-use/manage-skype-for-business-online-access.md)  

### <a name="see-also"></a>Zobacz także  

 [Rozpocznij pracę z ustawieniami zgodności w programie System Center Configuration Manager](../../compliance/get-started/get-started-with-compliance-settings.md)

