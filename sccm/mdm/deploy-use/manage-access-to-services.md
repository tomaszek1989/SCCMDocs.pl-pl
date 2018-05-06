---
title: Dostęp warunkowy
titleSuffix: Configuration Manager
description: Dowiedz się, jak używać dostępu warunkowego w programie System Center Configuration Manager ułatwia zabezpieczanie poczty e-mail i innych usług.
ms.date: 12/22/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 7b04727b-d563-422f-8d59-4dd66215d0b3
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: f354647ba9376ff18db1a4b63944ef31272308e1
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="manage-access-to-services-in-system-center-configuration-manager"></a>Zarządzanie dostępem do usług w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


## <a name="conditional-access-in-system-center-configuration-manager"></a>Dostęp warunkowy w programie System Center Configuration Manager
Korzystaj z dostępu warunkowego do określenia warunków, aby ułatwić zabezpieczanie poczty e-mail i innych usług na urządzeniach zarejestrowanych w usłudze Microsoft Intune.  

 Aby uzyskać informacje dotyczące dostępu warunkowego na urządzeniach, które są zarządzane przy użyciu klienta programu Configuration Manager, zobacz [zarządzanie dostępem do usług O365 dla komputerów zarządzanych przez program System Center Configuration Manager](../../protect/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm.md).  


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

    -   Określa, czy wiadomości e-mail na urządzeniu jest zarządzany przez zasady programu Configuration Manager lub Microsoft Intune  

     Urządzenie zgłasza zgodne dla wszystkie zasady dostępu warunkowego, jeśli dowolne zasady zgodności nie są wdrażane do niego.

-   **Zasady dostępu warunkowego** są przeznaczone dla określonej usługi. Te zasady definiują reguły, takie jak które usługi Azure Active Directory grupy użytkowników zabezpieczeń lub kolekcje użytkowników programu Configuration Manager docelowe lub wykluczone.  

     Możesz skonfigurować zasady dostępu warunkowego lokalnego programu Exchange z poziomu konsoli programu Configuration Manager. Jednak podczas konfigurowania zasad usługi Exchange Online lub SharePoint Online Microsoft Intune zostanie otwarta konsola pozwala skonfigurować zasady.  

     W odróżnieniu od innych zasad Microsoft Intune lub programie Configuration Manager nie należy wdrażać zasad dostępu warunkowego. Zamiast tego po skonfigurowaniu tych zasad i mają one zastosowanie do wszystkich użytkowników docelowych.  

 Gdy urządzenia nie spełniają skonfigurowanych warunków, użytkownik jest jednak rejestracji urządzenia i rozwiązywania problemu zgodności urządzenia z przewodnikiem.  

Przed rozpoczęciem korzystania z dostępu warunkowego upewnij się, że zostały spełnione odpowiednie wymagania:  

## <a name="requirements-for-exchange-online-using-the-shared-multi-tenant-environment"></a>Wymagania dotyczące Usługa Exchange Online (korzystająca ze współużytkowanego środowiska z wieloma dzierżawami)
Dostęp warunkowy do usługi Exchange Online obsługuje urządzenia, na których są uruchomione:
-   Windows 8.1 lub nowszy (jeśli jest zarejestrowane w usłudze Intune)
-   System Windows 7.0 lub Windows 8.1 (jeśli jest częścią domeny)
-   System Windows Phone 8.1 lub nowszy
-   System iOS 7.1 lub nowszy
-   System android 4.0 i nowsze, Samsung KNOX Standard 4.0 lub nowszy

 **Ponadto**:
-   Urządzenia muszą być dołączone do miejsca pracy, który rejestruje urządzenie w usłudze Azure Active Directory usługi rejestracji urządzeń (AAD DRS).<br />     
- Komputery przyłączone do domeny muszą być automatycznie rejestrowane w usłudze Azure Active Directory za pomocą funkcji MSI lub zasad grupy.

  **Dostęp warunkowy dla komputerów** w tym artykule opisano wszystkie wymagania dotyczące włączania dostępu warunkowego na komputerze.<br />     
  Usługa AAD DRS automatycznie aktywuje dla klientów firmy Microsoft Intune i Office 365. Klienci, którzy już wdrożyli usługę rejestracji urządzeń usług AD FS nie ma zarejestrowanych urządzeń w usłudze Active Directory ich lokalnych.
-   Korzystanie z subskrypcji usługi Office 365, obejmującej usługę Exchange Online (na przykład E3). Użytkownicy muszą mieć licencję dla usługi Exchange Online.
-   Łącznik programu Exchange Server jest opcjonalna i łączy program Configuration Manager do programu Microsoft Exchange Online. Ten łącznik pomaga w monitorowaniu informacji o urządzeniach za pośrednictwem konsoli programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [Zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md).
Nie trzeba łącznika do stosowania zasad zgodności lub dostępu warunkowego. Uruchamianie raportów na temat wpływu dostępu warunkowego wymaga łącznika.

## <a name="requirements-for-exchange-online-dedicated"></a>Wymagania dotyczące usługi Exchange Online w wersji dedykowanej
Dostęp warunkowy do usługi Exchange Online w wersji dedykowanej obsługuje urządzenia, na których są uruchomione:
-   System Windows 8 lub nowszy (jeśli jest zarejestrowane w usłudze Intune)
-   System Windows 7.0 lub Windows 8.1 (jeśli jest częścią domeny)

  Dostęp warunkowy do komputerów przyłączonych do domeny tylko do dzierżawców w nowym dedykowanym środowisku usługi Exchange Online.
-   System Windows Phone 8 lub nowszy
-   Dowolne urządzenie z systemem iOS, które używa klienta poczty e-mail programu Exchange ActiveSync (EAS)
-   System android 4 lub nowszy.
-   W przypadku dzierżawców korzystających ze starszej wersji środowiska usługi Exchange Online w wersji dedykowanej:    

  Użyj łącznika serwera Exchange, który łączy program Configuration Manager do programu Microsoft Exchange lokalnego. Łącznik umożliwia zarządzanie urządzeniami przenośnymi i umożliwia dostęp warunkowy. Aby uzyskać więcej informacji, zobacz [Zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md).
-   W przypadku dzierżaw w nowym środowisku usługi Exchange Online w wersji dedykowanej:     
  Łącznik serwera Exchange jest opcjonalny, który łączy program Configuration Manager do programu Microsoft Exchange Online i ułatwia zarządzanie informacjami o urządzeniu. Aby uzyskać więcej informacji, zobacz [Zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md). Nie trzeba łącznika do stosowania zasad zgodności lub dostępu warunkowego. Uruchamianie raportów na temat wpływu dostępu warunkowego wymaga łącznika.  

## <a name="requirements-for-exchange-on-premises"></a>Wymagania dla lokalnego programu Exchange
Warunkowy dostęp do programu Exchange lokalnie obsługuje:
-   System Windows 8 lub nowszy (jeśli jest zarejestrowane w usłudze Intune)
-   System Windows Phone 8 lub nowszy
-   Natywna aplikacja poczty e-mail w systemie iOS
-   Natywna aplikacja poczty e-mail w systemie Android 4 lub nowszy
-   Aplikacja Microsoft Outlook nie jest obsługiwane (Android i iOS)

**Ponadto**:

- Wersja programu Exchange musi być programu Exchange 2010 lub nowszej.
- Macierz serwerów dostępu klienta (CAS) serwera programu Exchange jest obsługiwana.

> [!TIP]
> Jeśli środowisko programu Exchange znajduje się w konfiguracji serwera CAS, musisz skonfigurować łącznik programu Exchange lokalnie, aby wskazywał jeden z serwerów CAS.
- Użyj łącznika serwera Exchange, który łączy program Configuration Manager do programu Microsoft Exchange lokalnego. Łącznik umożliwia zarządzanie urządzeniami przenośnymi i umożliwia dostęp warunkowy. Aby uzyskać więcej informacji, zobacz [Zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md).
  - Upewnij się, że używasz najnowszej wersji łącznika lokalnego programu Exchange. Skonfiguruj lokalny łącznik Exchange za pomocą konsoli programu Configuration Manager. Aby uzyskać szczegółowe wskazówki, zobacz [Zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i Exchange](../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md).
  - Łącznik należy skonfigurować tylko w lokacji głównej programu Configuration Manager

- Program Exchange ActiveSync można skonfigurować za pomocą uwierzytelniania opartego na certyfikatach lub wpisu poświadczeń użytkownika.


## <a name="requirements-for-skype-for-business-online"></a>Wymagania dotyczące usługi Skype dla firm Online
Dostęp warunkowy do usługi SharePoint Online obsługuje urządzenia, na których uruchomiono:
 -   System iOS 7.1 lub nowszy
 -   Android 4.0 i nowsze
 -   Samsung KNOX Standard 4.0 lub nowszy

Włącz [nowoczesnego uwierzytelniania](https://aka.ms/SkypeModernAuth) dla usługi Skype dla firm Online. 

Każdy użytkownik musi użyć usługi Skype dla firm Online. Jeśli masz wdrożenie z Skype dla firm Online i Skype dla firm lokalnymi, zasady dostępu warunkowego nie dotyczą użytkowników lokalnych.

## <a name="requirements-for-sharepoint-online"></a>Wymagania dotyczące programu SharePoint Online
Dostęp warunkowy do usługi SharePoint Online obsługuje urządzenia, na których uruchomiono:
 -   Windows 8.1 lub nowszy (jeśli jest zarejestrowane w usłudze Intune)
 -   System Windows 7.0 lub Windows 8.1 (jeśli jest częścią domeny)
 -   System Windows Phone 8.1 lub nowszy
 -   System iOS 7.1 lub nowszy
 -   System android 4.0 i nowsze, Samsung KNOX Standard 4.0 lub nowszy

 **Ponadto**:
 -   Urządzenia muszą być dołączone do miejsca pracy, który rejestruje urządzenie w usłudze Azure Active Directory usługi rejestracji urządzeń (AAD DRS).

 Komputery przyłączone do domeny muszą być automatycznie rejestrowane w usłudze Azure Active Directory za pomocą funkcji MSI lub zasad grupy. **Dostęp warunkowy dla komputerów** w tym artykule opisano wszystkie wymagania dotyczące włączania dostępu warunkowego na komputerze.

 Usługa AAD DRS automatycznie aktywuje dla klientów firmy Microsoft Intune i Office 365. Klienci, którzy już wdrożyli usługę rejestracji urządzeń usług AD FS nie ma zarejestrowanych urządzeń w usłudze Active Directory ich lokalnych.
 -   Wymagana jest subskrypcja usługi SharePoint Online, a użytkownicy muszą mieć licencję na usługę SharePoint Online.

 ### <a name="conditional-access-for-pcs"></a>Dostęp warunkowy dla komputerów

 Dostęp warunkowy można skonfigurować dla komputerów z aplikacjami klasycznymi pakietu Office i uzyskiwać dostęp do usługi Exchange Online lub SharePoint Online. Komputery muszą spełniać następujące wymagania:
 -   Na komputerze musi działać system Windows 7.0 lub Windows 8.1
 -   Komputer musi być albo przyłączone do domeny lub zgodne

 W celu zapewnienia zgodności komputer musi być zarejestrowane w programie Microsoft Intune i zgodne z zasadami.

 W przypadku komputerów przyłączonych do domeny musisz skonfigurować [automatyczne rejestrowanie urządzenia](https://azure.microsoft.com/documentation/articles/active-directory-conditional-access-automatic-device-registration/) w usłudze Azure Active Directory.
 -   [Należy włączyć nowoczesne uwierzytelnianie usługi Office 365](https://blogs.office.com/2015/03/23/office-2013-modern-authentication-public-preview-announced/) i zainstalować wszystkie najnowsze aktualizacje pakietu Office.<br />     Nowoczesnego uwierzytelniania umożliwia podstawie Active Directory Authentication Library ADAL logowanie do klientów systemu Windows z pakietu Office 2013 i zapewnia większe bezpieczeństwo dzięki zastosowaniu uwierzytelniania wieloskładnikowego oraz uwierzytelnianie oparte na certyfikatach.
 -   Aby zablokować nienowoczesne protokoły uwierzytelniania, należy skonfigurować reguły oświadczeń ADFS.  

## <a name="next-steps"></a>Następne kroki  
 Przeczytaj następujące tematy, aby dowiedzieć się, jak skonfigurować zasady zgodności i zasady dostępu warunkowego dla wymaganego scenariusza:  

-   [Zarządzanie zasadami zgodności urządzeń w programie System Center Configuration Manager](../../protect/deploy-use/device-compliance-policies.md)  

-   [Zarządzanie dostępem do poczty e-mail w programie System Center Configuration Manager](../../protect/deploy-use/manage-email-access.md)  

-   [Zarządzanie dostępem do usługi SharePoint Online w programie System Center Configuration Manager](../../protect/deploy-use/manage-sharepoint-online-access.md)  

-   [Zarządzanie dostępem do usługi Skype dla firm Online](../../protect/deploy-use/manage-skype-for-business-online-access.md)  

### <a name="see-also"></a>Zobacz także  

 [Rozpoczynanie pracy z ustawieniami zgodności w programie System Center Configuration Manager](../../compliance/get-started/get-started-with-compliance-settings.md)
