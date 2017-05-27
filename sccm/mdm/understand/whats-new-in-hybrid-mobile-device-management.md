---
title: "What&quot;s new in hybrydowego zarządzania urządzeniami Przenośnymi za pomocą programu Configuration Manager | Dokumentacja firmy Microsoft"
description: "Poznaj nowe funkcje zarządzania urządzeniami przenośnymi dostępne dla wdrożenia hybrydowego z programu Configuration Manager i usługi Intune."
ms.custom: na
ms.date: 04/21/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b127cee-61f1-4681-9760-caebed36ddf5
caps.latest.revision: 40
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: ae008c91a7387ba76f2bfac13f8feb489a0cc558
ms.openlocfilehash: 0af5ae68353fcf1db846e2e27f3391fe87dcfc42
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="whats-new-in-hybrid-mobile-device-management-with-system-center-configuration-manager-and-microsoft-intune"></a>What's new in hybrydowe zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i Microsoft Intune

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Ten artykuł zawiera szczegółowe informacje dotyczące nowych urządzeń przenośnych, dostępne dla wdrożenia hybrydowego za pomocą programu System Center Configuration Manager i Microsoft Intune funkcje zarządzania (MDM).  

##  <a name="compatibility-with-configuration-manager-versions"></a>Zgodność z wersjami programu Configuration Manager  

 Każda sekcja w tym artykule przedstawiono hybrydowe funkcji w ramach różnych kategorii 3. Można określić zgodność funkcji w każdej kategorii z różnymi wersjami programu Configuration Manager, użyj poniższych wskazówek:  

|Kategorie funkcji|Opis|
|-|-|
|**Nowość w usłudze Microsoft Intune** | Ogólnie rzecz biorąc wszystkie funkcje wymienione w tej kategorii powinien współpracować z wszystkie wersje programu Configuration Manager, w tym wersje programu System Center 2012 R2 Configuration Manager, ponieważ tylko te funkcje wymagają usługi Intune i nie wymagają dodatkowych funkcji w programie Configuration Manager.|
|**Nowość w programie Configuration Manager Technical Preview**| Wszystkie funkcje wymienione w tej kategorii pracować tylko z określonej wersji Technical Preview. Aby wypróbować te funkcje, należy zainstalować określony w opisie funkcji wersji Technical Preview. Aby uzyskać więcej informacji, zobacz [Technical Preview dla programu System Center Configuration Manager](../../core/get-started/technical-preview.md).|
|**Nowe w programie Configuration Manager (bieżącej gałęzi)**| Wszystkie funkcje wymienione w tej kategorii pracować tylko z określonej wersji programu Configuration Manager (bieżącej gałęzi), takich jak wersja 1511 lub 1602. Jeśli używasz starszej wersji programu Configuration Manager wdrożenie hybrydowe, należy uaktualnić do wersji Configuration Manager (bieżącej gałęzi) określona w opisie funkcji. Aby uzyskać więcej informacji, zobacz [uaktualnienia programu System Center Configuration Manager](../../core/servers/deploy/install/upgrade-to-configuration-manager.md).|

## <a name="april-2017"></a>2017 kwietnia

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune

- **MyApps dostępne dla Managed Browser**

  Microsoft MyApps już lepszą obsługę przeglądarki zarządzane. Użytkowników zarządzanych przeglądarki, którzy nie są przeznaczone do zarządzania zostanie przeniesiony bezpośrednio do usługi MyApps, gdzie mogą uzyskiwać dostęp do swoich aplikacji SaaS udostępnione przez administratora. Użytkownicy, którzy są przeznaczone do zarządzania Intune będzie mógł uzyskać dostęp do MyApps z wbudowanych zakładki Managed Browser.

- **Nowe ikony Managed Browser i portalu firmy**

  Managed Browser otrzymuje zaktualizowane ikon dla systemu Android i iOS wersji aplikacji. Nowa ikona będzie zawierać identyfikator Intune zaktualizowane, aby stał się bardziej spójne z innymi aplikacjami w przedsiębiorstwie mobilności + zabezpieczeń (EM + S). Nowa ikona programu Managed Browser można wyświetlić na [what's new in strony interfejsu użytkownika aplikacji Intune](/intune/whats-new/whats-new-in-intune-app-ui.md).

  Portal firmy otrzymuje również ikony zaktualizowane wersje aplikacji, aby zwiększyć zgodność z innymi aplikacjami w EM + S Android, iOS i Windows. Te ikony zostanie wydana stopniowo na platformach od kwietnia do maja opóźnione.

- **Wskaźnik postępu logowanie w portalu firmy Android**

  Aktualizacji aplikacji Portal firmy Android zawiera wskaźnik postępu logowanie, gdy użytkownik uruchamia lub wznowieniu działania aplikacji. Wskaźnik przechodzi nowych stanów, począwszy od "Łączenie...", "Podpisywanie cali..", a następnie "Sprawdzanie wymagań dotyczących zabezpieczeń..." przed zezwoleniem na użytkownika dostęp do tej aplikacji. Można wyświetlić nowe ekrany dla aplikacji Portal firmy dla systemu Android [what's new in strony interfejsu użytkownika aplikacji Intune](/intune/whats-new/whats-new-in-intune-app-ui.md).

- **Blokuj dostęp do usługi SharePoint Online aplikacji**

  Teraz można utworzyć zasady dostępu warunkowego na podstawie aplikacji, aby zablokować aplikacje, które nie zawierają stosowane zasady ochrony aplikacji do nich dostęp do [usługi SharePoint Online](/InTune/deploy-use/mam-ca-for-sharepoint-online). W tym scenariuszu aplikacje na podstawie dostępu warunkowego można określić aplikacje, które mają mieć dostęp do usługi SharePoint Online za pomocą portalu Azure.

### <a name="new-in-configuration-manager-technical-preview-1704"></a>Nowością w programie Configuration Manager Technical Preview 1704

- **Konfigurowanie aplikacji systemu Android za pomocą zasad konfiguracji aplikacji**

  Umożliwia aplikacji zasad konfiguracji w System Center Configuration Manager (Menedżer konfiguracji) dystrybuować wstępnie skonfigurowanych ustawień, gdy użytkownik uruchamia aplikację w systemie Android pracy urządzeń. Zasady konfiguracji systemu android aplikacji są dostępne tylko na urządzeniach z systemem Android do pracy i stosuje się do aplikacji zatwierdzone w grze dla sklepu pracy. Aby uzyskać informacje na temat sposobu wypróbować tę funkcję, zobacz [Android Konfigurowanie aplikacji za pomocą zasad konfiguracji aplikacji](/sccm/core/get-started/capabilities-in-technical-preview-1704#configure-android-apps-with-app-configuration-policies).

## <a name="march-2017"></a>2017 marca

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune

- **Nowe środowisko użytkownika dla aplikacji Portal firmy dla systemu Android**

  Interfejs użytkownika aplikacji Portal firmy dla systemu Android musi bardziej nowoczesny wygląd i działanie. Znaczące aktualizacje są:

  - Kolory: Nagłówki kartę Portal firmy mają kolor zdefiniowany IT marki.
  - Aplikacje: W **aplikacje** kartę, **funkcjonalne aplikacje** i **wszystkie aplikacje** przyciski zostały zaktualizowane.
  - Wyszukiwania: W **aplikacje** kartę, **wyszukiwania** przycisk jest ruchomy przycisk akcji.
  - Nawigacja aplikacji: **Wszystkie aplikacje** widok przedstawia widok z kartami **duży**, **wszystkie**, i **kategorii** ułatwiające nawigację.
  - Obsługa: **Moje urządzenia** i **kontakt z działem IT** karty są aktualizowane w celu poprawienia czytelności.

  Aby uzyskać więcej informacji o tych zmianach, zobacz [aktualizacje interfejsu użytkownika dla aplikacji użytkownika końcowego Intune](/intune/whats-new/whats-new-in-intune-app-ui).

- **Podpisywanie skryptu dla portalu firmy systemu Windows 10**

  W razie potrzeby pobrać i ładowanie bezpośrednie aplikacji Portal firmy dla systemu Windows 10 można teraz używać skryptu uprościć i uprościć proces podpisywania aplikacji w Twojej organizacji.  Aby pobrać skrypt i instrukcje dotyczące korzystania z niego, zobacz [podpisywania skryptów dla systemu Windows 10 Portal firmy Microsoft Intune](https://aka.ms/win10cpscript) w galerii TechNet. Więcej szczegółów dotyczących tego powiadomienia, zobacz [aktualizacji aplikacji Portal firmy dla systemu Windows 10](https://blogs.technet.microsoft.com/intunesupport/2017/03/13/updating-your-windows-10-company-portal-app/) na blogu zespołu pomocy technicznej usługi Intune.

- **Ulepszona obsługa systemu Android użytkowników na podstawie w Chinach**

  Z powodu braku sklepu Google Play w Chinach urządzeń z systemem Android musi uzyskać aplikacje z rynków chińskiego. Portal firmy będzie obsługiwać ten przepływ pracy dzięki przekierowaniu użytkowników systemu Android w Chinach pobierania aplikacji portalu firmy i Outlook z lokalnych sklepów z aplikacjami. Zwiększy interfejsu użytkownika po włączeniu zasady dostępu warunkowego zarówno dla zarządzania urządzeniami przenośnymi i zarządzania aplikacjami mobilnymi. Portal firmy i Outlook aplikacje dla systemu Android są dostępne w następujących chińskiego sklepów:

  - [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
  - [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)
  - [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
  - [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
  - [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)

- **Upewnij się, że aplikacji portalu firmy są aktualne**

  W 2016 grudnia opublikowano aktualizację włączone wymuszania dla uwierzytelnianie wieloskładnikowe (MFA) na grupę użytkowników ich rejestracji, iOS, Android, Windows 8.1 + lub urządzenia Windows Phone 8.1 +. Ta funkcja nie może pracować bez niektóre wersje podstawy aplikacji Portal firmy dla systemu Android (v5.0.3419.0 +) i iOS (v2.1.17 +).

  Możliwości zarządzania w usłudze Intune są stale poprawianie i wiele ulepszeń mają koordynowany aktualizacje aplikacji portalu firmy na wszystkich obsługiwanych platformach. W związku z tym firma Microsoft zaleca zachowywanie najnowsze wersje aplikacji Portal firmy zainstalowany na urządzeniach, aby wykorzystać ulepszenia w usłudze Intune i najlepsze środowisko użytkownika.

  >[!Tip]
  > Ma ustawić swoje urządzenia do automatycznego aktualizowania aplikacji ze sklepu z aplikacjami odpowiednich użytkowników. Jeśli udostępnione w aplikacji Portal firmy systemu Android w udziale sieciowym, możesz pobrać najnowszą wersję ze [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=49140).

- **Teams firmy Microsoft jest teraz włączone dla MAM iOS i Android**

  Aplikacje Teams firmy Microsoft dla systemów iOS i Android są włączone z funkcjami zarządzania (MAM) aplikacji mobilnej Intune, więc dają możliwość zespołom swobodnie pracy na urządzeniach, przy jednoczesnym zapewnieniu konwersacji i danych firmowych jest chroniony na każdy ruch. Aby uzyskać więcej informacji, zobacz [anons Teams firmy Microsoft](https://blogs.technet.microsoft.com/enterprisemobility/2017/03/14/microsoft-teams-is-now-generally-available-and-mam-enabled-on-ios-and-android/) na blogu mobilności przedsiębiorstwa i zabezpieczeń.

### <a name="new-in-configuration-manager-technical-preview-1703"></a>Nowością w programie Configuration Manager Technical Preview 1703

- **Dodatkowa obsługa scenariuszy programu zakupów firmy Apple woluminu**

   Począwszy od Technical Preview 1703, masz teraz obsługę w następujących scenariuszach Program zakupu woluminu (VPP):

   - Urządzenie licencjonowania — aplikacje, które obsługują licencjonowania urządzeń i zostaną wdrożone do kolekcji urządzeń będzie wymagać tylko jedną licencję na urządzenie.  Wcześniej konieczne było użycie licencji dla każdego użytkownika na urządzeniu. Aby uzyskać więcej informacji, zobacz [wdrażanie aplikacji iOS kupionymi woluminu do kolekcji urządzeń](/sccm/core/get-started/capabilities-in-technical-preview-1703#deploy-volume-purchased-ios-apps-to-device-collections).
   - Używanie wielu tokenów VPP dzierżawcy hybrydowe jednego z obu tokeny używanym do zarządzania aplikacji VPP.
   - Użycie tokenów VPP edukacji umożliwia rozróżnienie działalności biznesowej i edukacja tokenów.

### <a name="new-in-configuration-manager-current-branch"></a>Nowe w programie Configuration Manager (bieżącej gałęzi)

Następujące funkcje, które wcześniej były dostępne w wersji Technical Preview programu Configuration Manager są teraz dostępne we wdrożeniach hybrydowych za pomocą usługi Intune i program Configuration Manager (bieżącej gałęzi) wersja 1702.

- [Android obsługi pracy](/sccm/core/plan-design/changes/whats-new-in-version-1702##android-for-work-support)
- [Ustawienia zgodności niezgodnych aplikacji.](/sccm/core/plan-design/changes/whats-new-in-version-1702#conditional-access-device-compliance-policy-improvements)
- [Utworzenie certyfikatu PFX i dystrybucji oraz obsługa szyfrowania S/MIME](/sccm/core/plan-design/changes/whats-new-in-version-1702#improvements-to-certificate-profiles)
- [Android i iOS wersje nie są już targetable w kreatorze tworzenia hybrydowe MDM](/sccm/core/plan-design/changes/whats-new-in-version-1702#android-and-ios-versions-are-no-longer-targetable-in-creation-wizards-for-hybrid-mdm)

Następujące funkcje dodatkowe hybrydowe znajdują się również w wersji 1702 programu Configuration Manager (bieżącej gałęzi):

- **Ulepszona obsługa dla woluminu Program zakupu (VPP) firmy Apple**

  - Teraz można wdrożyć licencjonowane aplikacje na urządzeniach, jak i użytkowników. W zależności od funkcji aplikacji do obsługi urządzeń licencjonowania odpowiedniej licencji będzie wymagana podczas wdrażania, w następujący sposób:

    | Wersja programu Configuration Manager | Aplikacja obsługuje licencjonowania urządzenia? | Typ kolekcji wdrożenia | Oświadczeniem licencji |
    |-|-|-|-|
    |Starsze niż 1702|Tak|Użytkownik|Licencja użytkownika|
    |Starsze niż 1702|Nie|Użytkownik|Licencja użytkownika|
    |Starsze niż 1702|Tak|Urządzenie|Licencja użytkownika|
    |Starsze niż 1702|Nie|Urządzenie|Licencja użytkownika|
    |1702 i nowsze|Tak|Użytkownik|Licencja użytkownika|
    |1702 i nowsze|Nie|Użytkownik|Licencja użytkownika|
    |1702 i nowsze|Tak|Urządzenie|Licencję urządzenia|
    |1702 i nowsze|Nie|Urządzenie|Licencja użytkownika|

  - Teraz można również wdrażać i śledzić aplikacji uzyskany z iOS Program zakupu zbiorczej dla instytucji edukacyjnych.

  - Można teraz skojarzyć wiele tokenów program zakupu woluminu Apple z programu Configuration Manager.

  Aby uzyskać więcej informacji o aplikacjach iOS kupionymi woluminu, zobacz [zarządzania aplikacjami zakupione woluminu iOS](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps).

- **Obsługa aplikacji biznesowych w Sklepie Windows dla firm**

  Niestandardowe aplikacje biznesowe w Sklepie Windows dla firm mogą teraz synchronizować.

- **Przed zagrożeniami Mobile nowe narzędzia do monitorowania**

    Ma teraz mają nowe możliwości monitorowania stanu zgodności z dostawcą usług przed zagrożeniami Mobile.

    Aby uzyskać więcej informacji, zobacz [sposób monitorowania zgodności przed zagrożeniami Mobile](/sccm/mdm/deploy-use/monitor-mobile-threat-defense-compliance).

## <a name="february-2017"></a>2017 lutego

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune

- **Modernizacji witryny internetowej portalu firmy**

  Witryna sieci Web portalu firmy obsługuje aplikacje, które są przeznaczone dla użytkowników, którzy nie mają zarządzanych urządzeń. Witryny sieci Web jest wyrównywany z innych produktów firmy Microsoft i usług przy użyciu nowego schematu kolorów kontrastujące, ilustracje dynamiczne i "menu hamburger,", która zawiera szczegóły dotyczące kontaktu z pomocą techniczną oraz informacje o istniejących zarządzanych urządzeń. Strona docelowa jest grupowany podkreślenie aplikacje, które są dostępne dla użytkowników, którzy carousels dla aplikacji duży i niedawno zaktualizowany. Można znaleźć przed i po obrazów dostępnych na [aktualizacje interfejsu użytkownika](/intune/whats-new/whats-new-in-intune-app-ui) strony.

- **Nowy adres serwera MDM dla urządzeń z systemem Windows**

  Adres serwera MDM rejestrowania urządzeń z systemem Windows i Windows Phone zmienił się z manage.microsoft.com enrollment.manage.microsoft.com. Powiadom użytkownika do używania enrollment.manage.microsoft.com jako adres serwera MDM, jeśli zostanie wyświetlony monit o jej podczas rejestrowania systemu Windows lub i urządzeń Windows Phone. Ta aktualizacja wymaga również wszelkich CNAME w systemie DNS, który przekierowuje domenę EnterpriseEnrollment.contoso.com do manage.microsoft.com być zastąpiona rekord CNAME w systemie DNS, który przekierowuje domenę EnterpriseEnrollment.contoso.com do EnterpriseEnrollment-s.manage.microsoft.com. Aby uzyskać dodatkowe informacje o tej zmianie odwiedź stronę http://aka.ms/intuneenrollsvrchange.

### <a name="new-in-configuration-manager-technical-preview-1702"></a>Nowością w programie Configuration Manager Technical Preview 1702

- **Android obsługi pracy**

  Teraz można zarządzać za pomocą Android do pracy w środowiskach hybrydowych MDM, przy użyciu konfiguracji Menedżera Technical Preview 1702 urządzenia z systemem Android. Obsługiwane urządzenia z systemem Android można rejestrować teraz jako Android pracy urządzeń, które tworzy profil pracy na urządzeniu, do którego można wdrożyć aplikacje zatwierdzone Play pracy. Można również skonfigurować i wdrożyć elementy konfiguracji, zasady zgodności i profilów dostępu do zasobów dla tych urządzeń. Aby uzyskać więcej informacji, zobacz [Android obsługę pracy](/sccm/core/get-started/capabilities-in-technical-preview-1702#android-for-work-support).

- **Ustawienia zgodności niezgodnych aplikacji.**

  Obecnie można tworzyć reguły niezgodnych aplikacji dla aplikacji Android i iOS w ramach zasad zgodności. Jeśli urządzenia mają określone aplikacje zainstalowane, zostaną oznaczone jako "niezgodnych" i spowoduje utratę dostępu do zasobów firmy, zgodnie z zasadami dostępu warunkowego w miejscu. Aby uzyskać więcej informacji [ulepszenia zasady zgodności urządzeń dostępu warunkowego](/sccm/core/get-started/capabilities-in-technical-preview-1702#conditional-access-device-compliance-policy-improvements).

- **Utworzenie certyfikatu PFX i dystrybucji oraz obsługa szyfrowania S/MIME**

  Teraz można tworzyć i wdrażać certyfikaty PFX dla użytkowników w środowisku hybrydowym. Tych certyfikatów można następnie używane S/MIME e-mail szyfrowania i odszyfrowywania urządzeń zarejestrowanych przez użytkownika. Aby uzyskać więcej informacji, zobacz [obsługuje certyfikaty PFX utworzyć z S MIME](/sccm/core/get-started/capabilities-in-technical-preview-1702#create-pfx-certificates-with-s-mime-support).

- **Obsługa iOS dodatkowe ustawienia konfiguracji**
   
    Masz teraz 42 ustawienia dodatkowe systemu iOS, które można skonfigurować w ramach pozycji konfiguracji. Dla urządzeń z systemem iOS nadzorowanego zostały dodane większość ustawień (35 we wszystkich). Aby uzyskać więcej informacji, zobacz [nowe ustawienia zgodności dla urządzeń z systemem iOS](/sccm/core/get-started/capabilities-in-technical-preview-1702#new-compliance-settings-for-ios-devices).

## <a name="january-2017"></a>2017 stycznia

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune

- **Obsługuje 7.1.1 systemu android**

  Intune teraz w pełni obsługuje i zarządza Android 7.1.1.

- **Rozwiąż problem, gdzie urządzenia z systemem iOS nie są aktywne lub konsoli administracyjnej nie może komunikować się z nimi**

  Gdy urządzenia użytkowników traci kontaktu z usługą Intune, można przekazać nowy kroki rozwiązywania problemów, aby pomóc w odzyskaniu dostępu do zasobów firmy. Zobacz [urządzenia są aktywne, lub konsoli administracyjnej nie może komunikować się z nimi](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them).

### <a name="new-in-configuration-manager-technical-preview-1701"></a>Nowością w programie Configuration Manager Technical Preview 1701

- **Android i iOS wersje nie są już targetable w kreatorze tworzenia hybrydowe MDM**

  Począwszy od Technical Preview 1701 dla hybrydowego zarządzania urządzeniami przenośnymi (MDM), nie jest już konieczne docelowych określonych wersji Android i iOS przy tworzeniu nowych zasad i profile dla urządzeń zarządzanych przez usługę Intune. Z tą zmianą wdrożenia hybrydowego można zapewnić obsługę szybciej nowe wersje Android i iOS bez konieczności nowej wersji programu Configuration Manager lub rozszerzenia. Aby dowiedzieć się więcej, zobacz temat [Android i iOS wersje nie są już targetable w kreatorach tworzenia](/sccm/core/get-started/capabilities-in-technical-preview-1701#android-and-ios-versions-are-no-longer-targetable-in-creation-wizards-for-hybrid-mdm).


## <a name="december-2016"></a>2016 grudnia

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune

- **Uwierzytelnianie wieloskładnikowe (MFA) na rejestracji jest przenoszony do portalu Azure**

  Wcześniej czy przejdź do konsoli usługi Intune lub konsoli programu Configuration Manager do ustawiania MFA rejestracje Intune. Ta funkcja zaktualizowane, możesz teraz logowania [portalu Microsoft Azure] (https://manage.windowsazure.com) przy użyciu programu Intune poświadczenia i skonfiguruj ustawienia uwierzytelniania Wieloskładnikowego za pomocą usługi Azure AD. Aby dowiedzieć się więcej, zobacz [uwierzytelnianie wieloskładnikowe dla Microsoft Intune] (https://aka.ms/mfa_ad).

- **Aplikacja Portal firmy dla systemu Android jest teraz dostępny w Chinach**

  Aplikacja Portal firmy dla systemu Android jest teraz dostępny w Chinach. Z powodu braku sklepu Google Play w Chinach urządzeń z systemem Android należy uzyskać aplikacji z rynków chińskiego aplikacji. Aplikacja Portal firmy dla systemu Android jest dostępny do pobrania w następujących magazynów:

  -    [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
  -    [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
  -    [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
  -    [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)
  -    [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)

  Aplikacja Portal firmy dla systemu Android używa Google Play usług do komunikowania się z usługą Microsoft Intune. Ponieważ Google Play usług nie są jeszcze dostępne w Chinach, wykonywania następujących zadań może zająć do 8 godzin.

  | Konsola administracyjna programu Configuration Manager | Aplikacja portalu firmy w usłudze Intune dla systemu Android | Witryny sieci Web portalu firmy usługi Intune |
  |----|----|----|        
  | Wycofaj/Wyczyść (Usuń wszystkie dane)    | Usuń urządzenie zdalne | Usuwanie urządzenia (lokalne i zdalne) |
  | Wycofaj/Wyczyść (Usuń dane firmy)    | Resetowanie urządzenia | Resetowanie urządzenia|
  | Wdrażanie nowych lub zaktualizowanych aplikacji | Instalowanie aplikacji biznesowych — dostępne | Resetowanie kodu dostępu urządzenia|
  | Zdalne blokowanie    | | |
  | Resetowanie kodu dostępu | | |        


## <a name="november-2016"></a>Listopad 2016

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune

- **Portal nowe firmy Microsoft Intune dostępnych dla urządzeń z systemem Windows 10**

  Firma Microsoft wydała nowy [aplikacji Portal firmy dla urządzeń z systemem Windows 10](https://www.microsoft.com/store/apps/9wzdncrfj3pz). Tej aplikacji, która korzysta z nowego formatu Windows 10 uniwersalnych zapewnia środowisko użytkownika zaktualizowane identyczne na wszystkich urządzeniach z systemem Windows 10, PC i Mobile podobne jednoczesnym nadal te same funkcje zapewniane przez poprzednie aplikacji portalu firmy.

  Nową aplikację korzysta z funkcji platformy, takich jak logowania jednokrotnego (SSO) i uwierzytelniania opartego na certyfikatach na urządzeniach z systemem Windows 10. Aplikacja jest dostępna jako uaktualnienie istniejącego portalu firmy Windows 8.1 i instaluje Portal firmy systemu Windows Phone 8.1 w Sklepie Windows. Aby uzyskać więcej informacji, przejdź do [Blog zespołu pomocy technicznej usługi Intune](http://aka.ms/intunecp_universalapp).

  Nowa aplikacja Portal firmy jest również wyświetlana dowolnego magazynu systemu Windows dla aplikacji biznesowych oznaczone **dostępne** w konsoli programu Configuration Manager.


### <a name="new-in-configuration-manager-current-branch"></a>Nowe w programie Configuration Manager (bieżącej gałęzi)

Następujące funkcje, które wcześniej były dostępne w wersji Technical Preview programu Configuration Manager są teraz dostępne we wdrożeniach hybrydowych za pomocą usługi Intune i program Configuration Manager (bieżącej gałęzi) wersja 1610.

* [Dodatkowe ustawienia i udoskonalone środowisko dla elementów konfiguracji](/sccm/core/plan-design/changes/whats-new-in-version-1610#new-compliance-settings-for-configuration-items)
* [Dodatkowe ustawienia profilów DEP](whats-new-hybrid-archive.md#new-in-configuration-manager-technical-preview-1609)
* [Płatną aplikacji w Sklepie Windows dla firm](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)
* [Typy połączeń macierzystego dla profilów sieci VPN systemu Windows 10](whats-new-hybrid-archive.md#new-in-configuration-manager-technical-preview-1609)
* [Wykresy zgodności Intune](/sccm/protect/deploy-use/create-compliance-policy#monitor-the-compliance-policy)
* [Żądanie zasad synchronizacji z konsoli](/sccm/mdm/deploy-use/sync-intune-device)
* [Ustawienia konfiguracji usługi Windows Defender](/sccm/compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client#windows-defender)

Następujące funkcje dodatkowe hybrydowe znajdują się również w wersji 1610 programu Configuration Manager (bieżącej gałęzi):

- **Zwiększenie liczby zarejestrowanych urządzeń**

  Teraz można umożliwić użytkownikom rejestrowanie urządzeń do 15. Poprzednie limit został 5 urządzeń dla poszczególnych użytkowników.


- **Obsługa zabezpieczeń drukarkach**

  Oprócz pełny Administrator następujące wbudowanych ról zabezpieczeń teraz mają pełny dostęp do elementów w węźle wszystkich urządzeń firmowych, w tym urządzeń Predeclared, profile rejestracji systemu iOS i profilami rejestracji systemu Windows:

    - Menedżer zasobów
    - Menedżer dostępu do zasobów firmy

  Tylko do odczytu do tych obszarów konsoli programu Configuration Manager nadal dostęp do roli analityk z uprawnieniami tylko do odczytu.

- **Wyzwalacz automatycznego dostępu do sieci VPN z aplikacji systemu Windows o ochronie informacji**

  Domeny głównej ochrony informacji systemu Windows można dodać do profilów sieci VPN systemu Windows 10, które powoduje, że wszystkie aplikacje skojarzone automatycznie wyzwalać połączenia sieci VPN, gdy są uruchamiane na urządzeniu. Ta opcja jest dostępna tylko w przypadku wybierania typu macierzystego połączenia.

- **Funkcja dostępu warunkowego dla profilów sieci VPN systemu Windows 10**

    Możesz teraz wymagać systemu Windows 10 urządzeń zarejestrowanych w usłudze Azure Active Directory zgodności w celu dostępu do sieci VPN za pomocą profili sieci VPN systemu Windows 10 utworzone w konsoli programu Configuration Manager. Można to zrobić za pomocą nowej **Włącz dostęp warunkowy dla tego połączenia VPN** pole wyboru na stronie metodę uwierzytelniania w Kreatorze profilu sieci VPN i właściwości profilu sieci VPN dla profilów sieci VPN systemu Windows 10. Ta opcja jest dostępna tylko w przypadku wybierania typu macierzystego połączenia.

    Można również określić osobny certyfikatu dla uwierzytelniania rejestracji jednokrotnej po włączeniu dostępu warunkowego dla profilu.


## <a name="notices"></a>Uwagi

### <a name="system-center-2012-configuration-sp1-and-system-center-2012-r2-configuration-manager-rtm-support-for-hybrid-mobile-device-management-ending-on-april-10-2017"></a>Konfiguracja programu System Center 2012 SP1 i System Center 2012 R2 Configuration Manager (RTM): Pomocy technicznej do zarządzania urządzeniami przenośnymi hybrydowe kończy się dnia 10 kwietnia 2017

*11 stycznia 2017*

Obsługa programu System Center 2012 Configuration Manager SP1 i System Center 2012 R2 Configuration Manager RTM upłynął 12 lipca 2016. Następnie obsługę tych wersjach, łączenie z Microsoft Intune usługi dla hybrydowego MDM kończy się na 10 kwietnia 2017. Po tej dacie hybrydowe MDM przestanie działać z tych wersji. Zarządzanych urządzeń zasadniczo być zarządzana, ponieważ łącznik usługi Intune nie jest już będą się łączyć z usługą Intune. Do usługi Intune nie będzie przepływu danych programu Configuration Manager (takich jak zasady i aplikacje) i urządzenia zarządzanego zostanie nie przepływ danych do programu Configuration Manager do momentu uaktualnienia ma miejsce.

Jeśli wdrożenie hybrydowe korzystasz z programu Configuration Manager 2012 z dodatkiem SP1 lub R2 RTM, zaleca się przed 10 kwietnia 2017 uaktualnienie do programu Configuration Manager (bieżącej gałęzi) lub obsługiwaną poprawkę programu Configuration Manager 2012 (R2 z dodatkiem SP1 lub z dodatkiem SP2), aby uniknąć zakłóceń w działaniu usługi.

Dodatkowe zasoby:
-    [Uaktualnienie programu System Center Configuration Manager (bieżącej gałęzi)](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager)
-    [Planowanie uaktualnienia do System Center 2012 R2 Configuration Manager SP1](https://technet.microsoft.com/library/jj822981.aspx#BKMK_PlanningR2SP1Upgrade)
-    [Planowanie uaktualnienia do programu System Center 2012 Configuration Manager SP2](https://technet.microsoft.com/library/jj822981.aspx#BKMK_PlanningSP2Upgrade)

### <a name="windows-phone-8-company-portal-upload-deprecated"></a>Przestarzałe przekazywania Portal firmy systemu Windows Phone 8
*25 października 2016*

Przekazywanie podpisanej aplikacji portalu firmy została usunięta z konsoli programu Configuration Manager jako pomocy technicznej usługi Intune jest przestarzałe i zastępowane dla systemu Windows 8, Windows Phone 8 i Windows RT i pomoc techniczna dla portalu firmy systemu Windows Phone 8 dobiega końca w listopadzie.  Urządzenia systemu Windows 8, Windows Phone 8 i Windows RT, które są już zarejestrowane w dalszym ciągu być obsługiwane, ale zarejestrowanie dodatkowych urządzeń z tych platform nie będą obsługiwane.


### <a name="see-also"></a>Zobacz też

- [W przeszłości hybrydowe funkcje zarządzania urządzeniami Przenośnymi](whats-new-hybrid-archive.md)
- [Nowości dotyczące zarządzania urządzeniami Przenośnymi w programie System Center 2012 Configuration Manager](https://technet.microsoft.com/library/mt445560.aspx)

