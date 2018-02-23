---
title: "Archiwum nowości nowe hybrydowego zarządzania urządzeniami Przenośnymi"
titleSuffix: Configuration Manager
description: "Archiwum ostatnich funkcje zarządzania urządzeniami przenośnymi dostępne dla hybrydowych wdrożeń z programu System Center Configuration Manager i usługi Intune."
ms.custom: na
ms.date: 02/21/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4c27b161-9eb7-4cdd-b469-d8eb27e71aea
author: aczechowski
ms.author: aaroncz
manager: dougeby
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: d6b67cd820a618d6a96424362ff282cbf232f092
ms.sourcegitcommit: 45ff3ffa040eada5656b17f47dcabd3c637bdb60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/23/2018
---
# <a name="past-hybrid-features-with-system-center-configuration-manager-and-microsoft-intune"></a>Hybrydowe ostatnich funkcji za pomocą programu System Center Configuration Manager i Microsoft Intune

Dotyczy: Program System Center Configuration Manager (Current Branch)*

Ten artykuł zawiera szczegółowe informacje na urządzeniu przenośnym, ostatnie funkcje zarządzania urządzeniami Przenośnymi jest dostępne dla hybrydowych wdrożeń z programu System Center Configuration Manager i Microsoft Intune.  

##  <a name="compatibility-with-configuration-manager-versions"></a>Zgodność z wersjami programu Configuration Manager  

 Każda sekcja w tym artykule wymieniono funkcje hybrydowych w 3 różnych kategorii. Aby sprawdzić zgodność funkcji w każdej kategorii z różnych wersji programu Configuration Manager, użyj poniższych wskazówek:  

|Funkcja kategorii|
|-|  
|**Nowa w programie Microsoft Intune** — ogólnie, wszystkie funkcje wymienione w tej kategorii powinny wymagać pracy z wszystkie wersje programu Configuration Manager, w tym wersje programu System Center 2012 R2 Configuration Manager, ponieważ tylko funkcji usługi Intune usługi i nie wymagają dodatkowych funkcji w programie Configuration Manager.<br /><br /> **Nowa w programie Configuration Manager Technical Preview** — wszystkie funkcje wymienione w tej kategorii tylko pracować z określonej wersji Technical Preview. Aby wypróbować te funkcje, należy zainstalować wersję Technical Preview określony w opisie funkcji. Aby uzyskać więcej informacji, zobacz [Technical Preview programu System Center Configuration Manager](../../core/get-started/technical-preview.md).<br /><br /> **Nowe w programie Configuration Manager (wersji current branch)** — wszystkie funkcje wymienione w tej kategorii działać tylko w przypadku określonej wersji programu Configuration Manager (wersji current branch), np. w wersji 1511 lub 1602. Jeśli używasz starszej wersji programu Configuration Manager dla danego wdrożenia hybrydowego, należy uaktualnić do wersji Configuration Manager (wersji current branch) określona w opisie funkcji. Aby uzyskać więcej informacji, zobacz [uaktualnienia do programu System Center Configuration Manager](../../core/servers/deploy/install/upgrade-to-configuration-manager.md).|  



## <a name="february-2017"></a>Lutego 2017

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune

- **Modernizacji witryny sieci Web Portal firmy**

  Witryny sieci Web Portal firmy obsługuje aplikacje, które są przeznaczone dla użytkowników, którzy nie mają zarządzanych urządzeń. Witryny sieci Web była zgodna z innymi usługami i produktami firmy Microsoft przy użyciu nowego kontrastujące schemat kolorów, dynamiczne ilustracje i "menu hamburger,", która zawiera szczegóły dotyczące kontaktu z pomocą techniczną oraz informacje o istniejących urządzeń zarządzanych. Strona docelowa jest grupowany do wyróżnienia aplikacje, które są dostępne dla użytkowników, którzy carousels dla aplikacji duży i niedawno aktualizowana. Można znaleźć przed i po dostępnych obrazów na [aktualizacje interfejsu użytkownika](https://docs.microsoft.com/intune/whats-new-app-ui) strony.

- **Nowy adres serwera zarządzania urządzeniami Przenośnymi dla urządzeń z systemem Windows**

  Adres serwera MDM związane z rejestrowaniem urządzeń z systemem Windows i Windows Phone zmienił się z manage.microsoft.com enrollment.manage.microsoft.com. Powiadom użytkownika do używania enrollment.manage.microsoft.com jako adres serwera MDM, jeśli wyświetlony monit o jej podczas rejestrowania systemu Windows lub i urządzeń Windows Phone. Ta aktualizacja wymaga również wszystkie CNAME w systemie DNS, który przekierowuje domenę EnterpriseEnrollment.contoso.com do domeny manage.microsoft.com być zastąpiona rekord CNAME w systemie DNS, który przekierowuje domenę EnterpriseEnrollment.contoso.com do domeny EnterpriseEnrollment-s.manage.microsoft.com. Aby uzyskać dodatkowe informacje o tej zmianie odwiedź stronę http://aka.ms/intuneenrollsvrchange.

### <a name="new-in-configuration-manager-technical-preview-1702"></a>Nowość w programie Configuration Manager Technical Preview 1702

- **Android obsługę pracy**

  Możesz teraz zarządzać urządzeniami z systemem Android przy użyciu systemu Android do pracy w środowiskach hybrydowych zarządzania urządzeniami Przenośnymi, za pomocą konfiguracji Manager Technical Preview 1702. Obsługiwane są urządzenia z systemem Android można teraz je zarejestrować jako Android pracy urządzeń, które tworzy profil pracy na urządzeniu, do którego można wdrożyć aplikacji zatwierdzone Play do pracy. Można również skonfigurować i wdrożyć elementy konfiguracji, zasady zgodności i profilów dostępu do zasobów dla tych urządzeń. Aby uzyskać więcej informacji, zobacz [Android obsługę pracy](/sccm/core/get-started/capabilities-in-technical-preview-1702#android-for-work-support).

- **Ustawienia zgodności niezgodnych aplikacji**

  Reguły niezgodnych aplikacji dla aplikacji systemu Android i iOS można teraz utworzyć w zasadach zgodności. Jeśli określonych aplikacji zainstalowane urządzenia, są oznaczone jako "niezgodnych" i utracić dostęp do zasobów firmy zgodnie z zasadami dostępu warunkowego. Aby uzyskać więcej informacji, zobacz [ulepszenia zasad zgodności urządzenia dostępu warunkowego](/sccm/core/get-started/capabilities-in-technical-preview-1702#conditional-access-device-compliance-policy-improvements).

- **Utworzenie certyfikatu PFX i dystrybucji i obsługa szyfrowania S/MIME**

  Teraz można tworzyć i wdrażać certyfikaty PFX dla użytkowników w środowisku hybrydowym. Tych certyfikatów można następnie używane do szyfrowania S/MIME poczty e-mail i odszyfrowywania przez urządzenia, które użytkownik zarejestrował. Aby uzyskać więcej informacji, zobacz [obsługuje tworzenie PFX certyfikatów przy użyciu S MIME](/sccm/core/get-started/capabilities-in-technical-preview-1702#create-pfx-certificates-with-s-mime-support).

- **Obsługa systemu iOS dodatkowe ustawienia konfiguracji**
   
    Masz teraz 42 ustawienia dodatkowe systemu iOS, które można skonfigurować w ramach elementu konfiguracji. W przypadku urządzeń nadzorowanych iOS zostały dodane większość ustawień (35 we wszystkich). Aby uzyskać więcej informacji, zobacz [nowe ustawienia zgodności dla urządzeń z systemem iOS](/sccm/core/get-started/capabilities-in-technical-preview-1702#new-compliance-settings-for-ios-devices).



## <a name="january-2017"></a>Stycznia 2017 r

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune

- **Obsługuje 7.1.1 systemu android**

  Usługa Intune teraz w pełni obsługuje i zarządza 7.1.1 systemu Android.

- **Rozwiąż problem, gdy urządzenia z systemem iOS są nieaktywne lub konsoli administracyjnej nie mogą komunikować się z nimi**

  Gdy urządzenia użytkowników utraci kontaktu z usługą Intune, można przekazać nowy kroki rozwiązywania problemów, aby pomóc w odzyskaniu dostępu do zasobów firmy. Zobacz [urządzenia są nieaktywne lub konsoli administracyjnej nie mogą komunikować się z nimi](https://docs.microsoft.com/intune/troubleshoot/troubleshoot-device-enrollment-in-intune#devices-are-inactive-or-the-admin-console-cannot-communicate-with-them).

### <a name="new-in-configuration-manager-technical-preview-1701"></a>Nowość w programie Configuration Manager Technical Preview 1701

- **Wersje systemów android i iOS nie są już targetable w kreatorach tworzenia dla hybrydowego zarządzania urządzeniami Przenośnymi**

  Począwszy od Technical Preview 1701 hybrydowego zarządzania urządzeniami przenośnymi (MDM), nie trzeba docelowych określonych wersji systemu Android i iOS, podczas tworzenia nowych zasad i profilów dla urządzeń zarządzanych przez usługę Intune. Dzięki tej zmianie hybrydowych wdrożeń można zapewnić obsługę szybciej nowe wersje systemów Android i iOS bez konieczności nową wersję programu Configuration Manager lub rozszerzenia. Aby dowiedzieć się więcej, zobacz [wersji systemów Android i iOS nie są już targetable w kreatorach tworzenia](/sccm/core/get-started/capabilities-in-technical-preview-1701#android-and-ios-versions-are-no-longer-targetable-in-creation-wizards-for-hybrid-mdm).



## <a name="december-2016"></a>Grudnia 2016

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune

- **Uwierzytelnianie wieloskładnikowe (MFA) na rejestracji jest przenoszona do portalu Azure**

  Wcześniej przejdzie do konsoli usługi Intune lub konsoli programu Configuration Manager do ustawienia usługi MFA dla rejestracji w usłudze Intune. Ta funkcja zaktualizowane, można teraz logowania [portalu Microsoft Azure] (https://manage.windowsazure.com) za pomocą programu Intune poświadczenia i skonfigurować ustawienia usługi MFA za pośrednictwem usługi Azure AD. Aby dowiedzieć się więcej, zobacz [uwierzytelnianie wieloskładnikowe w usłudze Microsoft Intune] (https://aka.ms/mfa_ad).

- **Aplikacja Portal firmy dla systemu Android teraz dostępny w Chinach**

  Aplikacja Portal firmy dla systemu Android jest teraz dostępna w Chinach. Z powodu braku sklepu Google Play w Chinach urządzenia z systemem Android musi uzyskać aplikacje z aplikacji języka chińskiego rynków. Aplikacja Portal firmy dla systemu Android jest dostępny do pobrania w sklepach następujące:

  - [Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
  - [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
  - [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
  - [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)
  - [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)

  Aplikacja Portal firmy dla systemu Android używa usług Google Play do komunikowania się z usługą Microsoft Intune. Ponieważ usług Google Play nie są jeszcze dostępne w Chinach, wykonasz następujące zadania może potrwać do 8 godzin.

  | Konsola administracyjna programu Configuration Manager | Aplikacja portalu firmy w usłudze Intune dla systemu Android | Witryny sieci Web Portal firmy usługi Intune |
  |----|----|----|      
  | Wycofaj/Wyczyść (Usuń wszystkie dane)   | Usuń urządzenie zdalne | Usunięcie urządzenia (lokalne i zdalne) |
  | Wycofaj/Wyczyść (Usuń dane firmy)   | Resetowanie urządzenia | Resetowanie urządzenia|
  | Wdrożenia aplikacji nowa czy zaktualizowana? | Instalowanie dostępnych aplikacji biznesowych z | Resetowanie kodu dostępu urządzenia|
  | Zdalne blokowanie | | |
  | Resetowanie kodu dostępu | | |        


## <a name="november-2016"></a>Listopada 2016

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune

- **Portal nowe firmy Microsoft Intune dostępnych dla urządzeń z systemem Windows 10**

  Firma Microsoft wydała nowy [aplikacji Portal firmy dla urządzeń z systemem Windows 10](https://www.microsoft.com/store/apps/9wzdncrfj3pz). Tej aplikacji, który korzysta z nowego formatu uniwersalnych systemu Windows 10 udostępnia środowisko zaktualizowanego użytkownika, które są identyczne dla wszystkich urządzeń z systemem Windows 10, komputera i Mobile podobne, ograniczając te same funkcje udostępniane przez poprzednie aplikacji Portal firmy.

  Nowa aplikacja korzysta z funkcji takich jak logowanie jednokrotne (SSO) i uwierzytelnianie oparte na urządzeniach z systemem Windows 10. Aplikacja jest dostępna jako uaktualnienie istniejącego portalu firmy Windows 8.1 i instaluje Portal firmy systemu Windows Phone 8.1 w Sklepie Windows. Aby uzyskać więcej informacji, przejdź do [Blog zespołu pomocy technicznej usługi Intune](http://aka.ms/intunecp_universalapp).

  Nowa aplikacja Portal firmy jest również wyświetlana żadnych Sklep Windows dla aplikacji biznesowych oznaczone **dostępne** w konsoli programu Configuration Manager.


### <a name="new-in-configuration-manager-current-branch"></a>Nowe w programie Configuration Manager (wersji current branch)

Następujące funkcje, które były wcześniej dostępne w wersjach Configuration Manager Technical Preview są teraz dostępne w przypadku hybrydowych wdrożeń z usługi Intune i program Configuration Manager (wersji current branch) wersja 1610.

* [Dodatkowe ustawienia i lepszą obsługę dla elementów konfiguracji](/sccm/core/plan-design/changes/whats-new-in-version-1610#new-compliance-settings-for-configuration-items)
* [Dodatkowe ustawienia profilów DEP](whats-new-hybrid-archive.md#new-in-configuration-manager-technical-preview-1609)
* [Płatnej aplikacji w Sklepie Windows dla firm](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business)
* [Typy połączeń macierzystego dla profilów sieci VPN systemu Windows 10](whats-new-hybrid-archive.md#new-in-configuration-manager-technical-preview-1609)
* [Wykresy zgodności usługi Intune](/sccm/protect/deploy-use/create-compliance-policy#monitor-the-compliance-policy)
* [Żądanie zasad synchronizacji z konsoli](/sccm/mdm/deploy-use/sync-intune-device)
* [Ustawienia konfiguracji usługi Windows Defender](/sccm/compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client#windows-defender)

Następujące funkcje dodatkowe hybrydowego znajdują się również w wersji 1610 programu Configuration Manager (wersji current branch):

- **Zwiększenie liczby zarejestrowanych urządzeń**

  Teraz można umożliwić użytkownikom rejestrowanie urządzeń do 15. Poprzednie limit został 5 urządzeń dla każdego użytkownika.


- **Obsługa zabezpieczeń drukarkach**

  Oprócz administrator o pełnych uprawnieniach następujące wbudowanych ról zabezpieczeń teraz mają pełny dostęp do elementów w węźle wszystkie urządzenia firmowe, w tym urządzeń wcześniej zadeklarowanej, profile rejestracji systemu iOS i profilami rejestracji systemu Windows:

    - Menedżer zasobów
    - Menedżer dostępu do zasobów firmy

  Tylko do odczytu do tych obszarów konsoli programu Configuration Manager nadal dostęp do roli analityk z uprawnieniami tylko do odczytu.

- **Wyzwalacz automatycznego dostępu do sieci VPN z aplikacji systemu Windows Information Protection**

  Domena podstawowa ochrony informacji w systemie Windows można dodać do profilów sieci VPN systemu Windows 10, które powoduje, że wszystkie skojarzone aplikacje automatycznie wyzwalać połączenia sieci VPN, gdy są uruchamiane na urządzeniu. Ta opcja jest dostępna tylko w przypadku wybrania typu natywnego połączenia.

- **Dostęp warunkowy dla profilów sieci VPN systemu Windows 10**

    Można teraz wymagają systemu Windows 10 urządzenia zarejestrowane w usłudze Azure Active Directory, aby było zgodne, aby mieć dostęp do sieci VPN za pomocą profilów VPN w systemie Windows 10 utworzone w konsoli programu Configuration Manager. Można to zrobić za pomocą nowej **włączania dostępu warunkowego dla tego połączenia VPN** pole wyboru na stronie metodę uwierzytelniania w Kreatorze profilu sieci VPN i właściwości profilu sieci VPN, profilów sieci VPN systemu Windows 10. Ta opcja jest dostępna tylko w przypadku wybrania typu natywnego połączenia.

    Można również określić oddzielny certyfikat dla pojedynczego uwierzytelniania logowania, po włączeniu dostępu warunkowego dla profilu.

## <a name="october-2016"></a>Października 2016

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune

Następujące funkcje usługi Intune, wprowadzone w października 2016 działa w przypadku wdrożeń hybrydowych.

- **Dostęp warunkowy do zarządzania aplikacjami mobilnymi**

  Można ograniczyć dostęp do usługi Exchange Online, tak aby dostępu pochodzi tylko z aplikacji, które obsługują zasad zarządzania aplikacjami mobilnymi usługi Intune, takich jak Outlook. [Ta nowa funkcja](/intune/deploy-use/allow-policy-managed-apps-access-to-o365) pary dokładnie z zasadami zarządzania (aplikacjami mobilnymi MAM) usługi Intune aplikacji mobilnej jako może zablokować dostęp do klientów poczty wbudowanych lub inne aplikacje, które nie zostały skonfigurowane przy użyciu zasad zarządzania aplikacjami Mobilnymi usługi Intune. Dzięki temu użytkownicy uzyskują dostęp do danych w organizacji z aplikacjami, które mogą być chronione przy użyciu funkcji MAM usługi Intune. Możesz rozpocząć pracę w zarządzania aplikacjami mobilnymi usługi Intune za pośrednictwem portalu Azure. Poszukaj nową sekcję dostępu warunkowego w bloku "Ustawienia".

-   **Narzędzia do zawijania aplikacji usługi Intune dla systemu Android**

  Można włączyć aplikacji do użycia zasad zarządzania (aplikacjami mobilnymi MAM) aplikacjami mobilnymi usługi Intune za pomocą narzędzia opakowującego aplikacje w usłudze Intune aplikacji.

- **Android Samsung KNOX Standard zgodności w usłudze Intune**

  Niektóre modele phone Samsung Galaxy Ace nie zarządzane przez usługę Intune jako urządzenia Samsung KNOX Standard. Podczas rejestrowania urządzeń w usłudze Intune, zamiast tego będą one zarządzane jako standardowa urządzeń z systemem Android.

  Numery modeli, których to dotyczy, są:

  - SM-G313HU
  - SM-G313HY
  - SM-G313M
  - SM-G313MY
  - SM-G313U

  Użytkownicy końcowi nie muszą podejmować żadnych dodatkowych czynności. Aby uzyskać więcej informacji odwiedź witrynę Samsung KNOX.

### <a name="new-in-configuration-manager-technical-preview-1610"></a>Nowość w programie Configuration Manager Technical Preview 1610

Wprowadzono następujące nowe funkcje hybrydowych w października 2016 dla konfiguracji Manager Technical Preview 1610.

- **Żądanie synchronizacji zasad z konsoli administracyjnej**

  Z poziomu konsoli programu Configuration Manager, bez konieczności żądania synchronizacji w aplikacji Portal firmy na urządzeniu może wysłać żądanie synchronizacji zasad na zarejestrowanym urządzeniu przenośnym. Jest to nowa akcja wywoływana **Wyślij żądanie synchronizacji** w menu Akcje urządzeń zdalnych, która jest wyświetlana na Wstążce po wybraniu urządzenia przenośnego w węźle urządzenia.

- **Ustawienia konfiguracji usługi Windows Defender**

  Można teraz skonfigurować ustawienia klienta usługi Windows Defender na komputerach zarejestrowanych w usłudze Intune systemu Windows 10 za pomocą elementów konfiguracji w konsoli programu Configuration Manager. Brak grupę ustawienie o nazwie **usługa Windows Defender** w Kreatorze elementu konfiguracji. Należy pamiętać, że jest to obsługiwane tylko w systemie Windows 10 w wersji 1511 lub nowszej.


### <a name="new-in-configuration-manager-current-branch"></a>Nowe w programie Configuration Manager (wersji current branch)

Nie nowych funkcji hybrydowych zostały wprowadzone w sierpniu 2016 programu Configuration Manager (wersji current branch).

## <a name="september-2016"></a>Wrześniu 2016 r.

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune

Następujące funkcje usługi Intune wprowadzone we wrześniu 2016 r działają w przypadku wdrożeń hybrydowych.

- **Dodanie obszaru "Powiadomienia" do portalu firmy dla systemu Android**

  Nową ikonę powiadomienia dodano do portalu firmy dla systemu Android na stronie głównej. Naciśnięcie tej ikony uzyskuje dostęp do strony powiadomienia zawiera wszystkie elementy, które wymagają uwagi w aplikacji Portal firmy, takich jak niezgodnych urządzeń, aktualizacja rejestracji i aktywacja rejestracji użytkowników końcowych. Aplikacja Portal firmy dla systemu iOS jest już to środowisko powiadomienia. Nowych oznacza strony powiadomienia o ten użytkownik nie będzie widoczna strona Konfigurowanie dostępu do zasobów firmy uruchomieniu lub wznowieniu pracy w portalu firmy, tak długo, jak długo urządzenie zostało już zarejestrowane. W przypadku utworzenia własnych wskazówki dla użytkowników końcowych, można zaktualizować dokumentacji w celu odzwierciedlenia tej zmiany. Znajdź zaktualizowane zrzuty ekranu [tutaj](https://aka.ms/androidcpupdate).

- **Zmiany w obsłudze aplikacji Portal firmy dla systemu iOS**

  Wszyscy użytkownicy aplikacji Portal firmy usługi Microsoft Intune dla systemu iOS są musieli używać jej najnowszej wersji. Nowi użytkownicy będą mogli pobrać tylko najnowszą wersję, a bieżący użytkownicy muszą przeprowadzić aktualizację do. Najnowszą wersję wymaga iOS 8.0 lub nowszego, dlatego urządzenia starszymi wersjami systemu iOS nie można korzystać z portalu firmy lub zarejestrować do czasu zaktualizowania do systemu iOS 8.0 lub nowszej, a następnie zaktualizuj do najnowszej wersji aplikacji Portal firmy. Zarejestrowane urządzenia z wersjami systemu iOS poniżej 8.0 będą nadal zarządzane i wyświetlane w konsoli administracyjnej usługi Intune.

- **Dodaje do aplikacji Portal firmy systemu Windows Phone 8.1 przycisku opinii**

  Aplikacja Portal firmy systemu Windows Phone 8.1 umożliwia użytkownikom wysyłanie informacji zwrotnych na temat aplikacji przy użyciu nowy przycisk "Wyślij opinię". Aby znaleźć przycisku, użytkowników wybierz menu "trzy kropki" w prawym dolnym rogu ekranu aplikacji Portal firmy, a następnie wybierz **wysłać opinię**. Zebrane, anonimowe opinie pomogą firmie Microsoft w ulepszaniu środowiska aplikacji Portal firmy dla użytkowników.

### <a name="new-in-configuration-manager-technical-preview-1609"></a>Nowość w programie Configuration Manager Technical Preview 1609

Dla konfiguracji Manager Technical Preview 1609 we wrześniu 2016 r zostały wprowadzone następujące nowe funkcje hybrydowego.

- **Dodatkowe ustawienia i lepszą obsługę dotyczące ustawień elementu konfiguracji**

  Dodano nowe ustawienia dla systemu Android, iOS i Windows, a tylko ustawienia mające zastosowanie do wybranych na stronie platformy obsługiwane platformy są wyświetlane w kreatorze. Aby uzyskać więcej informacji, zobacz [nowe ustawienia zgodności dla elementów konfiguracji w TP 1609](/sccm/core/get-started/capabilities-in-technical-preview-1609#new-compliance-settings-for-configuration-items).

- **Dodatkowe ustawienia profilów DEP**

  Czytnik TouchID, ApplePay i powiększenia zostały dodane jako można skonfigurować ustawienia w programie DEP profile dla urządzeń z systemem iOS.

- **Płatnej aplikacji w Sklepie Windows dla firm**

  Można teraz dodać zarówno płatną, jak i wolnego aplikacje do Sklepu Windows dla firm i wdrażać je dla użytkowników w organizacji. Aby uzyskać więcej informacji, zobacz [ulepszenia do Sklepu Windows dla firm w TP 1609](/sccm/core/get-started/capabilities-in-technical-preview-1609#enhancements-to-windows-store-for-business-integration-with-configuration-manager).

- **Typy połączeń macierzystego dla profilów sieci VPN systemu Windows 10**

  Można teraz utworzyć profile sieci VPN systemu Windows 10 do zarządzania urządzeniami Przenośnymi z typu połączenia Automatic firmy Microsoft, IKEv2 i PPTP w konsoli programu Configuration Manager bez przy użyciu identyfikatora OMA-URI.

- **Wykresy zgodności usługi Intune**

  Możesz uzyskać szybki przegląd urządzeń ogólnej zgodności i od góry przyczyn braku zgodności przy użyciu nowych wykresów w obszarze roboczym monitorowanie. Aby uzyskać więcej informacji, zobacz [wykresów zgodności usługi Intune w TP 1609](/sccm/core/get-started/capabilities-in-technical-preview-1609#intune-compliance-charts).

### <a name="new-in-configuration-manager-current-branch"></a>Nowe w programie Configuration Manager (wersji current branch)

Następujące nowa funkcja wprowadzona w we wrześniu 2016 r jest dostępna dla hybrydowych wdrożeń w usłudze Microsoft Intune i programu Configuration Manager w wersji 1606 (wersji current branch).

- **Obsługa systemu iOS 10**

  Jeśli profile lub elementy konfiguracji, przeznaczone dla wszystkich platform systemu iOS, te również zostanie przekazany do systemu iOS 10. Zostało również opublikowane aktualizacji 1606 wersji programu Configuration Manager, umożliwiający profile docelowy i elementy konfiguracji do poszczególnych iOS platform, w tym iOS 10. Można zainstalować aktualizacji z konsoli administratora programu Configuration Manager pod adresem **Administracja > Przegląd > usługi w chmurze > aktualizacje i obsługa**. Można znaleźć więcej informacji na temat aktualizacji w [http://support.microsoft.com/kb/3192616](http://support.microsoft.com/kb/3192616).

## <a name="august-2016"></a>Sierpnia 2016

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune

Następujące funkcje usługi Intune wprowadzono w sierpniu 2016 działają w przypadku wdrożeń hybrydowych.

- **Obsługa systemu android 7 w aplikacji Portal firmy**

  Aplikacja Portal firmy usługi Intune dla systemu Android zapewnia obsługę "od dnia 0" nadchodzącego systemu operacyjnego Android 7.0 dla urządzeń przenośnych.

- **Google usunięcie zdalnym resetowania kodu dostępu możliwości na urządzeniach z systemem Android 7.0**

  Google usuwa możliwość zdalnie zresetować kod dostępu urządzenia z systemem Android 7.0 administratorzy IT i użytkowników końcowych. Wcześniej Administratorzy IT mogli zdalnie zresetować kod dostępu użytkownika, a użytkownicy końcowi mogli resetować swoje kody dostępu z witryny portalu firmy.

- **Zasady dozwolonych i zablokowanych aplikacji dla urządzeń Samsung KNOX Standard**

  Można teraz skonfigurować niestandardowe zasady dla urządzenia Samsung KNOX Standard, które pozwala utworzyć jedną z następujących:

  - Lista aplikacji, które są blokowane uruchomionej na urządzeniu. Nawet po zainstalowaniu aplikacji zdefiniowanej na liście zablokowanych nie można uaktywnić na urządzeniu.
  - Lista aplikacji, które użytkownicy urządzenia mogą instalować ze sklepu Google Play. Można zainstalować żadnych innych aplikacji ze sklepu.

  Te ustawienia można używać tylko przez urządzenia z systemem Samsung KNOX Standard. Aby uzyskać więcej informacji, zobacz [użycie zasad niestandardowych, aby umożliwić lub zablokować aplikacje dla urządzeń Samsung KNOX Standard](/intune/deploy-use/custom-policy-to-allow-and-block-samsung-knox-apps).

- **Link opinii z portalu firmy do firmy Microsoft**

   Witryny sieci Web Portal firmy umożliwia użytkownikom końcowym wybierz nowy link "Opinia" u dołu strony, aby wysłać opinię do firmy Microsoft o ich obsługi w witrynie. Zebrane, anonimowe opinie pomogą firmie Microsoft w ulepszaniu środowiska witryny sieci Web Portal firmy dla użytkowników.

- **IOS minimalnej wersji Managed Browser zaktualizowana do 8.0**

  Aplikacja Microsoft Intune Managed Browser dla systemu iOS została zaktualizowana do obsługi urządzeń z systemem iOS 8.0 lub nowszej. Gdy urządzenia z systemem iOS 7.1 można nadal używać istniejącej aplikacji Managed Browser, należy zachęcać użytkowników do aktualizację do wersji iOS 8.0 lub nowszej, aby uzyskać dostęp do w pełni skorzystać z nowych funkcji w programie Managed Browser.

### <a name="new-in-configuration-manager-technical-preview"></a>Nowość w programie Configuration Manager Technical Preview

Nie nowych funkcji hybrydowych zostały wprowadzone w sierpniu 2016 Technical Preview programu Configuration Manager.

### <a name="new-in-configuration-manager-current-branch"></a>Nowe w programie Configuration Manager (wersji current branch)

Nie nowych funkcji hybrydowych zostały wprowadzone w sierpniu 2016 programu Configuration Manager (wersji current branch).

## <a name="july-2016"></a>Lipca 2016 r.

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune

Następujące funkcje usługi Intune, wprowadzone w lipca 2016 działa we wdrożeniach hybrydowych.

- **Zestaw SDK platformy Xamarin dla aplikacji usługi Intune jest dostępna**

  Składnik Xamarin zestawu SDK aplikacji usługi Intune umożliwia włączenie funkcje zarządzania aplikacjami mobilnymi usługi Intune w przenośnych z systemem iOS i Android aplikacji skompilowanej za pomocą platformy Xamarin. Można znaleźć składnika w [sklepie Xamarin](https://components.xamarin.com/view/Microsoft.Intune.MAM) lub na [stronie Microsoft Intune Github](https://github.com/msintuneappsdk).

- **Poprawione środowisko użytkownika końcowego podczas rejestrowania urządzeń z systemem Windows**

  Korzystając z dostępu warunkowego, kroki rejestracji dla Windows 8.1, Windows 10 Desktop i Windows 10 Mobile zostały uproszczone w witrynie internetowej portalu firmy. Użytkownicy zobaczą teraz osobne **rejestracji urządzeń** i **dołączania** kroków, co ułatwi sprawdzenie stanu urządzenia i ukończenie procesu po wystąpieniu awarii pracy Join (narzędzia WPJ). Oddzielne kroki powinny również uprościć proces rozwiązywania problemów dla administratorów IT. Wcześniej gdy użytkownik końcowy próbował zarejestrować, a wszystkie kroki rejestracji zakończyło się pomyślnie z wyjątkiem narzędzia WPJ, zarejestrowane urządzenie nie było wyświetlane na liście urządzeń użytkowników zidentyfikować, co było mylące dla użytkowników.

 - **Pełne czyszczenie danych, które są teraz dostępne dla urządzeń z systemem Windows 10**

    Komputery z systemem Windows 10 i laptopów zarejestrowane jako urządzenia przenośne można wyczyścić próbę zresetowania urządzenia do ustawień fabrycznych. Aby uzyskać więcej informacji, zobacz [ochrona urządzeń za pomocą funkcji zdalnego czyszczenia](/sccm/mdm/deploy-use/wipe-lock-reset).

- **Zmiany menedżerów rejestracji urządzenia konta w aplikacji Portal firmy dla systemu iOS**

  Aby zwiększyć wydajność i skalę, usługa Intune nie jest już wyświetlany wszystkich urządzeń menedżerów rejestracji urządzeń (DEM) w okienku Moje urządzenia aplikacji Portal firmy dla systemu iOS. Tylko urządzenie lokalne, na którym uruchomiono aplikację jest wyświetlane, a tylko wtedy, gdy jest ono zarejestrowane przez aplikację Portal firmy.

  Użytkownik Menedżera rejestracji urządzeń może wykonywać działania na urządzeniu lokalnym, ale zdalne zarządzanie innymi zarejestrowanymi urządzeniami można wykonać tylko z poziomu konsoli administracyjnej usługi Intune. Ponadto w usłudze Intune wycofano używanie kont menedżera rejestracji urządzeń z programem Device Enrollment Program lub narzędzia Apple Configurator. Obie te metody rejestracji obsługują już rejestrację bez użytkowników dla urządzeń udostępnionych z systemem iOS.

  Kont menedżera rejestracji urządzeń należy używać tylko w przypadku rejestracji bez użytkowników dla współużytkowanych urządzeń. Aby uzyskać więcej informacji, zobacz [rejestrowanie urządzeń należących do firmy przy użyciu Menedżera rejestracji urządzeń w programie Microsoft Intune](../deploy-use/enroll-devices-with-device-enrollment-manager.md).

- **Zmiany w aplikacji Portal firmy dla systemu Android**

  Jeśli użytkownicy końcowi systemu Android komunikat o błędzie informujący o urządzeniu nie ma wymaganego certyfikatu, mogą nacisnąć przycisk "Jak rozwiązać ten problem", aby pobrać kroki dotyczące instalowania brakującego certyfikatu. Jeżeli użytkownicy wykonaj kroki wyświetlone dodatkowe "Brak certyfikatu" komunikat o błędzie jest proszony o administratora IT i podaj ten link, który zawiera kroki, które umożliwiają administratorom IT usunięcie problemu z certyfikatem.

- **Ograniczenie instalacji aplikacji ładowana na zarejestrowanych urządzeniach z systemem Android**

  Urządzenia z systemem android nie mogą już instalować aplikacji za pośrednictwem witryny sieci Web portalu firmy, chyba że urządzenia zostały zarejestrowane w usłudze Intune przy użyciu aplikacji Portal firmy usługi Intune dla systemu Android.


### <a name="new-in-configuration-manager-technical-preview"></a>Nowość w programie Configuration Manager Technical Preview

Nie nowych funkcji hybrydowych zostały wprowadzone w lipca 2016 Technical Preview programu Configuration Manager.

### <a name="new-in-configuration-manager-current-branch"></a>Nowe w programie Configuration Manager (wersji current branch)

Następujące funkcje, które były wcześniej dostępne w wersjach Configuration Manager Technical Preview są teraz dostępne w przypadku hybrydowych wdrożeń z usługi Intune i program Configuration Manager (wersji current branch) wersja 1606.

* Znajdź, zarządzania i dystrybucji Sklepu Windows dla aplikacji biznesowych dla urządzeń z systemem Windows 10 z konsoli programu Configuration Manager ([1604](#new-in-1604-technical-preview))
*   Ustawienie SmartLock dla urządzeń z systemem Android ([1604](#new-in-1604-technical-preview))
*   Wyzwalane aplikacji urządzenia sieci VPN dla systemu Windows 10 ([1605](#new-in-1605-technical-preview))
*   Nowe środowisko dla akcji urządzenie zdalne ([1605](#new-in-1605-technical-preview))
*   Sklep Windows dla aplikacji biznesowych ([1605](#new-in-1605-technical-preview))
*   Ogólne poprawki dotyczące aplikacjami zakupionymi zbiorczo ([1605](#new-in-1605-technical-preview))
*   Rozwiązanie Windows Information Protection (pracy w toku) ([1605](#new-in-1605-technical-preview))
*   Wstępnie Zadeklaruj urządzenia należące do firmy z numerami IMEI lub iOS ([1605](#new-in-1605-technical-preview))
*   Automatycznie kategoryzowanie urządzeń do kolekcji ([1606](#new-in-1606-technical-preview))

Aby uzyskać informacje na temat nowych funkcji zobacz dokumentację dla określonej wersji Technical Preview.

## <a name="june-2016"></a>Czerwca 2016 r.

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune
Następujące funkcje usługi Intune, wprowadzone w czerwca 2016 działa we wdrożeniach hybrydowych.

- **Kondycja usługi Intune** informacje kondycji usługi dla usługi Intune zostały przeniesione do centralnej lokalizacji z innymi usługami firmy Microsoft. Teraz znajdziesz te informacje w portalu zarządzania usługi Office 365 w obszarze kondycja usługi. Aby uzyskać więcej informacji, zobacz [wpis w blogu](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).

- **Ulepszone systemu Windows 10 enterprise danych funkcje konfiguracji zasad**

  Usługa Intune ma teraz udoskonalone środowisko konfigurowania zasad ochrony informacji systemu Windows 10. Ulepszenia obejmują lepsze metody tworzenia reguł aplikacji, określ definicji granic sieci i inne ustawienia systemu Windows Information Protection. Aby dowiedzieć się więcej, zobacz [Tworzenie zasad systemu Windows informacji ochrony (pracy w toku) przy użyciu programu Microsoft Intune](https://technet.microsoft.com/itpro/windows/keep-secure/create-wip-policy-using-intune).

- **Cisco ISE sieci zasad kontroli dostępu dla usługi Intune**

  Klienci, którzy używać Cisco Identity usługi Engine (ISE) 2.1 a Microsoft Intune można ustawić zasady kontroli dostępu do sieci w ISE. Przy użyciu tych zasad, urządzeń, które muszą łączyć się z siecią przy użyciu sieci Wi-Fi lub VPN musi spełniać następujące warunki przed udzieleniem im dostępu:

  - Musi być zarządzane przez usługę Intune
  - Musi być zgodne z wdrożonymi zasadami zgodności usługi Intune

  Użytkownicy końcowi niezgodnych urządzeń zostaną poproszeni o zarejestrowanie i korygowania wszelkich problemach ze zgodnością w celu uzyskania dostępu.

- **Dostęp warunkowy dla przeglądarki**

  Zasady dostępu warunkowego dla usługi Exchange Online i SharePoint Online można ustawić tak, czy są dostępne tylko z obsługiwanych przeglądarek internetowych zarządzane i zgodne z systemami iOS i urządzeniach z systemem Android. Użytkownicy końcowi, którzy podejmą próbę zalogowania się do witryn usługi Outlook Web Access (OWA) i programu SharePoint przy użyciu urządzeń iOS i Android pojawi się monit o zarejestrowanie swoich urządzeń w usłudze Intune oraz rozwiązanie wszelkich problemów z niezgodnością przed zakończeniem logowania. Aby uzyskać więcej informacji, zobacz

  * [Ograniczanie dostępu poczty e-mail do usługi Exchange Online i nowej usługi Exchange Online w wersji dedykowanej przy użyciu usługi Intune](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)
  * [Ograniczanie dostępu do usługi SharePoint Online, usłudze Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune)

- **Dynamics CRM Online obsługuje dostęp warunkowy**

  Można ustawić zasady dostępu warunkowego dla usługi Dynamics CRM Online, aby go można uzyskać tylko przez zarządzane i zgodne z systemami iOS i urządzeniach z systemem Android. Użytkownicy końcowi, którzy podejmą próbę zalogowania się do aplikacji mobilnej Dynamics CRM w systemach iOS i Android zostaną poproszeni o rejestrację w usłudze Intune oraz Korygowanie problemów z niezgodnością przed logowanie może zakończyć. Aby uzyskać więcej informacji, zobacz [ograniczanie dostępu do programu Dynamics CRM Online, usłudze Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune).

- **Aktualizacje aplikacji portalu firmy dla systemu Android**

  Usługa Intune ma teraz następujące nowe zasady, które będzie miało wpływ na użytkowników Portal firmy dla systemu Android:   

  Zasady  |Wpływ na użytkowników  
  ---------|---------
  Wymagaj, aby urządzenia nie zezwalały na instalację aplikacji z nieznanych źródeł (Android 4.0 +)     |  Użytkownicy końcowi systemu Android 4.0 lub nowszym zostanie wyświetlony komunikat, "Instalacja z nieznanych źródeł musi zostać wyłączona." Użytkownicy będą musieli przejść do **Ustawienia > Zabezpieczenia** na ich urządzeniach i Wyłącz **nieznane źródła**. Link w komunikacie dotyczącym zgodności pozwala użytkownikom uzyskać więcej informacji na temat wiadomości i dlaczego ich wymagane jest wyłączenie tego ustawienia.
  Wymagaj, aby urządzenia nie zezwalały na instalację aplikacji z nieznanych źródeł (Android 4.0 +)  |    Użytkownicy końcowi systemu Android 4.0 lub nowszym zostanie wyświetlony komunikat "Skanuj urządzenie pod kątem zagrożeń zabezpieczeń". Użytkownicy będą musieli przejść do **Ustawienia > Google > zabezpieczeń** na ich urządzeniach i Włącz **Skanuj urządzenie pod kątem zagrożeń zabezpieczeń**. Link w komunikacie dotyczącym zgodności pozwala użytkownikom uzyskać więcej informacji na temat wiadomości i dlaczego ich wymagane jest włączenie tego ustawienia.     
  Wymagaj, aby debugowanie USB było wyłączone (Android 4.2 +)  | Użytkownicy końcowi z systemem Android 4.2 lub nowszym zostanie wyświetlony komunikat, "debugowanie USB musi zostać wyłączona." Użytkownicy będą musieli przejść do **Ustawienia > Opcje dewelopera** na ich urządzeniach i Wyłącz **debugowanie USB**. Link w komunikacie dotyczącym zgodności pozwala użytkownikom uzyskać więcej informacji na temat wiadomości i dlaczego ich wymagane jest wyłączenie tego ustawienia.
  Poziom poprawki zabezpieczeń systemu Android minimalną (Android 6.0 +)  | Użytkownikom końcowym urządzeń z systemem Android 6.0 lub nowszym zostanie wyświetlony komunikat, "to urządzenie nie spełnia poziomu poprawki zabezpieczeń systemu Android minimalne". Użytkownicy będą musieli zainstalować wymaganą poprawkę zabezpieczeń. Link w komunikacie dotyczącym zgodności pozwala użytkownikom uzyskać informacje o tym, jak zainstalować wymaganą poprawkę zabezpieczeń oraz poprawki zabezpieczeń, które aktualnie zainstalowana.

- **Aktualizacje aplikacji portalu firmy dla systemu iOS**

  * Podczas instalacji aplikacji biznesowych dla użytkowników końcowych, widzą będzie teraz usprawnione środowisko instalacyjne aplikacji. Jeśli instalacja aplikacji trwa zbyt długo, użytkownicy mogą ręcznie synchronizować swoje urządzenia, aby wymusić wznowienie procesu synchronizacji. Aby przejrzeć instrukcje dla użytkowników końcowych, zobacz ręcznie synchronizacji urządzenia z systemem iOS.
  * Aplikacja Portal firmy usługi Microsoft Intune dla systemu iOS został został zaktualizowany do obsługi systemu iOS w wersji 8.0 lub nowszym. Ta aktualizacja oznacza, że użytkowników końcowych można zainstalować aplikacji Portal firmy i zarejestrować w usłudze Intune nowe urządzenia tylko wtedy, gdy urządzenie ma zainstalowany system iOS w wersji 8.0 lub nowszej. Użytkownicy, którzy mają wcześniej zarejestrowane urządzenia, które są uruchomione na wystąpieniu nieobsługiwanej wersji systemu IOS można nadal używać aplikacji Portal firmy, która znajduje się na urządzeniu.


### <a name="new-in-1606-technical-preview"></a>Nowość w wersji zapoznawczej Technical Preview 1606
Następujące nowe funkcje wprowadzone w czerwca 2016 r są dostępne w przypadku hybrydowych wdrożeń z usługą Intune i Configuration Manager Technical Podgląd 1606.

- **Automatycznie kategoryzowanie urządzeń do kolekcji**

  Możesz utworzyć kategorie urządzeń, które mogą być używane do automatycznego umieszczania urządzeń w kolekcji urządzeń, gdy używasz programu Configuration Manager z usługą Intune. Następnie użytkownicy muszą wybrać kategorię urządzenia, gdy rejestrują urządzenia w usłudze Intune. Ponadto można zmienić kategorię urządzenia z konsoli programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [automatycznie kategoryzowanie urządzeń do kolekcji](/sccm/core/get-started/capabilities-in-technical-preview-1606#dmp_category) w [możliwości w Technical Preview 1606 programu System Center Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1606).

  > [!IMPORTANT]
  > Ta funkcja działa wraz z wydaniem czerwca 2016 Microsoft Intune. Upewnij się, że możesz zostały zaktualizowane do tej wersji przed wypróbowanie tych procedur.

### <a name="new-in-configuration-manager-current-branch"></a>Nowe w programie Configuration Manager (wersji current branch)
Nie nowych funkcji hybrydowych zostały wprowadzone w czerwca 2016 programu Configuration Manager (wersji current branch).

##  <a name="may-2016"></a>Maj 2016  

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune  
 Następujące funkcje usługi Intune, wprowadzone w maj 2016 działa w przypadku wdrożeń hybrydowych.

- **ZESTAW SDK ZARZĄDZANIA APLIKACJAMI MOBILNYMI: Konfiguracji długości numeru PIN pomocy technicznej**

  Teraz można określić długości numeru PIN dla aplikacji zarządzania aplikacjami Mobilnymi podobne do numeru PIN urządzenia. Wymaga to użytkownikom końcowym są zgodne z określonymi nowymi ograniczeniami, które można ustawić. Ekran numeru PIN jest nieco zmodyfikowany w celu konta dla danych wejściowych dłużej. Aby uzyskać więcej informacji, zobacz [ustawienia zasad MAM dla systemu Android](https://docs.microsoft.com/intune/deploy-use/android-mam-policy-settings), i [ustawienia zasad MAM dla systemu iOS](https://docs.microsoft.com/intune/deploy-use/ios-mam-policy-settings).  

- **Skype dla firm dla systemu iOS i Android**

  Można teraz kierować aplikacją Skype dla firm przy użyciu [zarządzania aplikacjami Mobilnymi bez zasad rejestracji](https://docs.microsoft.com/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune). Gdy użytkownicy zalogują się, zostaną zastosowane zasady zarządzania aplikacjami Mobilnymi.  

- **Nowe aplikacje dostępne do zarządzania za pomocą zasad zarządzania aplikacjami Mobilnymi**

  Aplikacje Microsoft Word, Excel i PowerPoint dla systemu Android teraz mogą być skojarzone z zasadami zarządzania aplikacjami Mobilnymi na urządzeniach, które nie są zarejestrowane w usłudze Intune. Aby uzyskać pełną listę obsługiwanych aplikacji, przejdź galerii aplikacji mobilnych Microsoft Intune w [partnerów aplikacji Microsoft Intune](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) strony.  

- **Aplikacja portal firmy dla systemu android: Wyskakujące powiadomienia dla użytkownika końcowego**

  Wyskakujące powiadomienia z aplikacji Portal firmy dla systemu Android są wyświetlane, gdy użytkownicy końcowi rejestrowania lub Usuń swoje urządzenia z portalu firmy.  

- **Witryna sieci Web portalu firmy: Baner identyfikacji urządzenia będzie zapewniać więcej informacji użytkownikom końcowym**

  Użytkownicy końcowi mogą teraz łatwiej identyfikować urządzenie, które wybrali, gdy korzystają z witryny Portal firmy. Jeśli wybrano niewłaściwe urządzenie, można wybrać poprawne urządzenie, naciskając pozycję **naciśnij tutaj** łącza na transparencie strony głównej.  


### <a name="new-in-1605-technical-preview"></a>Nowość w wersji zapoznawczej Technical Preview 1605  
 Następujące nowe funkcje wprowadzone w maj 2016 są dostępne w przypadku hybrydowych wdrożeń z usługą Intune i Configuration Manager Technical Podgląd 1605. Tych funkcji wymaga użycia konsoli programu Configuration Manager do konfigurowania i zarządzania nimi.  

- **Wyzwalane aplikacji urządzenia sieci VPN dla systemu Windows 10**

  Dla urządzeń z systemem Windows 10 zarządzane przy użyciu programu Configuration Manager z usługą Intune możesz dodać listę aplikacji, które automatycznie otwarte połączenie sieci VPN, który został skonfigurowany za pomocą konsoli administracyjnej programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [urządzeń wyzwalane przez aplikację sieci VPN dla systemu Windows 10](/sccm/core/get-started/capabilities-in-technical-preview-1605) w [możliwości w Technical Preview 1605 programu System Center Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1605)  

- **Nowe środowisko dla akcji urządzeniu zdalnym**

  Udoskonalono obsługę wykonywania akcji urządzenia zdalnego z konsoli programu Configuration Manager.

  Typowe akcje, takie jak **Wycofaj/wyczyść**, **resetowania kodu dostępu**, **zdalne blokowanie**, i **obejścia blokady aktywacji** można znaleźć w **akcje urządzeń zdalnych** menu użytkowcy **zasoby i zgodność** obszaru roboczego

  Aby uzyskać więcej informacji, zobacz [nowe środowisko dla akcji urządzenie zdalne](/sccm/core/get-started/capabilities-in-technical-preview-1605#new-experience-for-remote-device-actions) w [możliwości w Technical Preview 1605 programu System Center Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1605).  

- **Aplikacje ze Sklepu Windows dla firm**

  [Sklep Windows dla firm](https://www.microsoft.com/en-us/business-store) jest, gdzie można znaleźć i zakupić aplikacje dla Twojej organizacji, pojedynczo lub zbiorczo. Łącząc Sklep do programu Configuration Manager, można zarządzać aplikacjami zakupionymi zbiorczo z poziomu konsoli programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [Sklep Windows dla aplikacji biznesowych](/sccm/core/get-started/capabilities-in-technical-preview-1605.md#windows-store-for-business-apps) w [możliwości w Technical Preview 1605 programu System Center Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1605).  

- **Ogólne poprawki dotyczące aplikacje nabyte zbiorczo**

  Aplikacjami zakupionymi zbiorczo w Sklepie Windows dla firm i iOS app store zostały skonsolidowane do tego samego widoku **informacji o licencji dla aplikacji do przechowywania**. Ponadto udoskonalono sposób, w którym można utworzyć zbiorczo zakupionymi aplikacjami dla systemu iOS. Aby uzyskać więcej informacji, zobacz[ogólne poprawki dotyczące aplikacjami zakupionymi zbiorczo](/sccm/core/get-started/capabilities-in-technical-preview-1605.md#general-improvements-for-volume-purchased-apps) w [możliwości w Technical Preview 1605 programu System Center Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1605).  

- **Wstępnie Zadeklaruj urządzenia należące do firmy z numerami IMEI lub iOS**

  Teraz możesz zidentyfikować urządzenia należące do firmy przez zaimportowanie ich stacji międzynarodowe numery identyfikujące (IMEI) urządzenia przenośne. Możesz przekazać plik wartości rozdzielanych przecinkami (.csv) zawierający numery IMEI lub możesz ręcznie wprowadzić informacje o urządzeniu.  Można również zaimportować numerów seryjnych urządzeń z systemem iOS.  Aby uzyskać więcej informacji, zobacz [wstępnie Zadeklaruj urządzenia należące do firmy z numerami IMEI lub iOS](../../core/get-started/capabilities-in-technical-preview-1605.md#BKMK_IMEI) w [możliwości w Technical Preview 1605 programu System Center Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1605).  

- **Rozwiązanie Windows Information Protection (pracy w toku)**

  Możesz utworzyć elementy konfiguracji, które pozwalają na wdrożenie zasad systemu Windows informacji ochrony (pracy w toku), w tym pozwala wybrać chronionych aplikacji, poziom ochrony pracy w toku i jak znaleźć dane organizacji w sieci. Aby uzyskać więcej informacji na temat pracy w toku zobacz następujące tematy:  

  -   [Chroń dane przedsiębiorstwa przy użyciu systemu Windows informacji ochrony (pracy w toku)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip)  

  -   [Tworzenie i wdrażanie zasad systemu Windows informacji ochrony (pracy w toku), za pomocą programu System Center Configuration Manager](https://technet.microsoft.com/itpro/windows/keep-secure/create-wip-policy-using-sccm)  

### <a name="new-in-configuration-manager-current-branch"></a>Nowe w programie Configuration Manager (wersji current branch)  
 Nie nowych funkcji hybrydowych zostały wprowadzone w maj 2016 programu Configuration Manager (wersji current branch).  

##  <a name="april-2016"></a>Kwietnia 2016  

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune  
 Następujące funkcje usługi Intune, wprowadzone w kwietnia 2016 działa w przypadku wdrożeń hybrydowych.  

- **Zgodność użytkownika funkcji MAM**

  Można teraz wyświetlać stan zasad zarządzania aplikacjami dla użytkowników w dzierżawie usługi Azure Active Directory (AAD).  Aby uzyskać więcej informacji, zobacz [monitorowanie zasad zarządzania aplikacjami mobilnymi w usłudze Microsoft Intune](/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune) w bibliotece usługi Intune.  

- **Kontrolki zarządzania aplikacjami Mobilnymi zapobiegające synchronizacji kontaktów programu Outlook (Android)**

  Dostępne jest nowe ustawienie pozwala to zapobiec aplikacji synchronizowanie kontaktów z natywną książką adresową na urządzeniach z systemem Android. To nowe ustawienie jest obsługiwane początkowo przez aplikację Outlook na urządzeniach z systemem Android. Aby uzyskać więcej informacji, zobacz [tworzenie i wdrażanie zasad zarządzania aplikacjami mobilnymi w usłudze Microsoft Intune](/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune) w bibliotece usługi Intune.  

- **Ulepszenia do witryny sieci Web Portal firmy**

  Podczas instalacji aplikacji biznesowych dla użytkowników systemu Windows 10 Mobile i Windows Phone 8.1, teraz zobaczą są następujące nowe stany zapewniające więcej szczegółów na temat stanu instalacji:  

  -   **Oczekiwanie na zsynchronizowanie urządzenia** — użytkownik nacisnął pozycję "Instaluj" i urządzenie próbuje przeprowadzić synchronizację z infrastrukturą usługi Intune. Synchronizacja jest wymagana przed ukończeniem instalacji. Komunikat "Oczekiwanie na synchronizację urządzenia" również jest łącze, którego naciśnięcie powoduje wyświetlenie instrukcji na temat ręcznie zsynchronizować urządzenie w usłudze Intune, jeśli proces synchronizacji trwa zbyt długo lub zablokował.  

  -   **Pobieranie** — Trwa przetwarzanie żądania pobierania użytkownika i urządzenia jest pobranie i zainstalowanie aplikacji.  

- **Ulepszenia w aplikacji portal firmy dla systemu Android**

  Użytkownicy, którzy nie zarejestrowali swoich urządzeń w usłudze Intune i którzy nie mają zainstalowanych poprawnych certyfikatów nie będzie można logować się do aplikacji Portal firmy dla systemu Android i zobaczą komunikat, "Nie można zalogować się, ponieważ urządzenie nie ma wymaganego certyfikatu." Komunikat zawiera link "Rozwiązanie problemu", którego naciśnięcie powoduje wyświetlenie instrukcji instalacji certyfikatu. Aby wyświetlić czynności, które użytkownicy końcowi powinni wykonać w celu rozwiązania problemu, zobacz [Brak wymaganego certyfikatu urządzenia](/intune/enduser/using-your-android-device-with-intune) w bibliotece usługi Intune.  

- **Ulepszenia aplikacji Portal firmy dla systemu iOS**

  Dodano obsługę na odświeżenie zawartości ekranu głównego, który zawiera aplikacje z listy, urządzeń i kontakt z działem IT akcji pociągnij, aby odświeżyć informacje. Akcja pociągnij, aby odświeżyć nie sprawdza informacji zgodności i zasad, można to zrobić, wybierając Kafelek bieżącego urządzenia i naciskając **synchronizacji** przycisku.  

- **Ulepszenia systemu Windows 10 Mobile i Windows Phone 8.1 firmy aplikacji portalu**

  Podczas instalacji aplikacji biznesowych dla użytkowników końcowych, widzą będzie teraz usprawnione środowisko instalacyjne aplikacji. Jeśli instalacja aplikacji trwa zbyt długo, użytkownicy mogą ręcznie synchronizować swoje urządzenia, aby wymusić wznowienie procesu synchronizacji. Aby przejrzeć instrukcje dla użytkowników końcowych, zobacz [zsynchronizować urządzenie ręcznie w celu przyspieszenia instalacji aplikacji](/intune/enduser/using-your-windows-device-with-intune) w bibliotece usługi Intune.  

###  <a name="new-in-1604-technical-preview"></a>Nowość w wersji 1604 Technical Preview
 Następujące nowe funkcje wprowadzone w kwietnia 2016 r. są dostępne w przypadku wdrożeń hybrydowych usługi Intune i konfiguracji Manager Technical Preview 1604. Tych funkcji wymaga użycia konsoli programu Configuration Manager do konfigurowania i zarządzania nimi.  

- **Znajdź, zarządzania i dystrybucji Sklepu Windows dla aplikacji biznesowych dla urządzeń z systemem Windows 10 z konsoli programu Configuration Manager**


  Obsługuje Sklep Windows dla firm jest dostępna w Configuration Manager Technical Preview 1604 ułatwiają znajdowanie, zarządzania i dystrybucji aplikacji na urządzeniach Windows 10, który jest zarządzany. Aby uzyskać więcej informacji, zobacz [Zarządzanie aplikacjami zakupionymi zbiorczo w Sklepie Windows dla firm](/sccm/core/get-started/capabilities-in-technical-preview-1604#manage-volume-purchased-apps-from-the-windows-store-for-business) w [możliwości w Technical Preview 1604 programu System Center Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1604).  

- **Ustawienie SmartLock dla urządzeń z systemem Android**

  Nowe ustawienie dodano do elementu konfiguracji systemów Android i Samsung KNOX Standard, które umożliwia kontrolowanie funkcji SmartLock na zgodnych urządzeniach z systemem Android.  To ustawienie umożliwia uniemożliwić użytkownikom końcowym Konfigurowanie funkcji SmartLock. Zobacz [ustawienie SmartLock dla urządzeń z systemem Android](/sccm/get-started/capabilities-in-technical-preview-1604#smartlock-setting-for-android-devices) w [możliwości w Technical Preview 1604 programu System Center Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1604.md).  

### <a name="new-in-configuration-manager-current-branch"></a>Nowe w programie Configuration Manager (wersji current branch)  
 Nie nowych funkcji hybrydowych zostały wprowadzone w kwietnia 2016 programu Configuration Manager (wersji current branch).  

##  <a name="march-2016"></a>Marca 2016  

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune  
 Następujące funkcje usługi Intune, wprowadzone w marca 2016 działa we wdrożeniach hybrydowych.  

- **Kontrolki zarządzania aplikacjami Mobilnymi zapobiegające synchronizacji kontaktów programu Outlook (iOS)**

  Dostępne jest nowe ustawienie pozwala to zapobiec aplikacji synchronizowanie kontaktów z natywną książką adresową na urządzeniach z systemem iOS. To nowe ustawienie jest obsługiwane przez aplikację Outlook na urządzeniach z systemem iOS. Aby uzyskać więcej informacji dotyczących tego i innych ustawień, zobacz [tworzenie i wdrażanie zasad MAM](/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune) w bibliotece usługi Intune.  

- **Skype dla firm Online obsługuje dostęp warunkowy**

  Można ustawić zasady dostępu warunkowego dla usługi Skype dla firm Online, tak, aby go można uzyskać tylko przez zarządzane i zgodne z systemami iOS i urządzeniach z systemem Android.  Aby uzyskać więcej informacji, zobacz [zarządzanie dostępem do usługi Skype dla firm Online](/intune/deploy-use/restrict-access-to-skype-for-business-online-with-microsoft-intune) w bibliotece usługi Intune.  

- **Obsługa systemu iOS 9.3**

  W poniedziałek 21 marca firma Apple ogłosiła dostępność systemu iOS 9.3. Wszystkie istniejące funkcje usługi Intune aktualnie dostępnych do zarządzania urządzeniami z systemem iOS będą nadal działać bezproblemowo, jak użytkownicy uaktualnić swoje urządzenia do systemu iOS 9.3.  

- **Pakiety aplikacji systemu Windows dostępne bezpośrednio z witryny portalu firmy**

  Użytkownicy systemu Windows 8, Windows 8.1 i komputerów z systemem Windows RT mogą teraz zainstalować pakiety aplikacji systemu Windows (z rozszerzeniem appx) bezpośrednio z witryny portalu firmy. Poprzednio konieczne było wdrożenie lub użytkownicy musieli instalować aplikację Portal firmy na urządzeniach w celu instalowania aplikacji.  

- **Użytkownicy mogą zdalnie blokować swoje urządzenie z witryny sieci Web Portal firmy**

  Nową opcję blokady zdalnej dodano do witryny sieci Web portalu firmy, aby umożliwić użytkownikom zdalne blokowanie urządzenia z portalu w przypadku utraty lub kradzieży urządzenia.  

- **Warto korzystać z systemu iOS "Otwórz w" dla urządzeń zarejestrowanych w rozwiązaniu MDM innej firmy**

  Warto korzystać z systemu iOS "Otwórz w" umożliwia dostawcą zarządzania urządzeniami Przenośnymi urządzeniami przenośnymi innej firmy. Możesz konfigurować ograniczenia w konfiguracji ustawień profilu i wdrażania aplikacji za pomocą oprogramowania do zarządzania urządzeniami Przenośnymi. Ograniczenia są stosowane w przypadku instalowania aplikacji zarządzanej przez użytkownika. Przeczytaj szczegóły: [Zasady zarządzania aplikacjami mobilnymi Microsoft Intune i iOS Otwórz w](/intune/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune) w bibliotece usługi Intune.  

- **Aplikacje firmy Microsoft, które obsługują zarządzanie aplikacjami Mobilnymi**

  Lista aplikacji firmy Microsoft, których można używać z zasadami zarządzania aplikacjami mobilnymi usługi Intune ma została zaktualizowana do zawiera najnowsze aplikacje (w przypadku urządzeń, które są tylko zarejestrowane w usłudze Intune).  

- **Wdrażanie programu Adobe Reader dla Microsoft Intune na urządzeniach zarządzanych przez usługę Intune z systemem iOS w przedsiębiorstwie**

  Teraz można zarządzać aplikacją Adobe Reader dla systemu iOS na zarejestrowanych urządzeniach, stosując zasady zarządzania aplikacjami mobilnymi usługi Intune.  

- Aplikacja do udostępniania usługi Rights Management jest obsługiwane dla systemu Android

  Administratorzy IT mogą wdrażać zasad zarządzania aplikacjami mobilnymi, tak aby użytkownicy końcowi mogą wyświetlać obrazów, AV i PDF pliki bardziej bezpieczne, czy IT korzysta z usługi Intune do zarządzania urządzeniami.  

- **Ulepszenia systemów Android i iOS aplikacji Portal firmy**

  -   Gdy użytkownicy uruchomią aplikację, która jest zarządzana przez Zarządzanie aplikacjami mobilnymi (MAM), zobaczą komunikat z informacją, że aplikacja jest zarządzana przez ich firmę. Użytkownicy mogą nacisnąć link "Dowiedz się więcej", aby uzyskać więcej informacji, w tym miejscu o co oznacza określenie "aplikacje zarządzane". Mogą również nacisnąć "Nie pokazuj ponownie", aby komunikat nie jest już wyświetlany po uruchomieniu aplikacji.  

  -   Zostały dodane nowe ekrany które prowadzą użytkowników przez proces rejestracji i udostępniają więcej informacji na temat Dlaczego użytkownicy powinni się rejestrować i jakie Administratorzy IT może zobaczyć na zarejestrowanych urządzeniach.  

  -   Komunikaty o błędach rejestracji są teraz wyświetlane w aplikacji Portal firmy.  

### <a name="new-in-configuration-manager-technical-preview"></a>Nowość w programie Configuration Manager Technical Preview  
 Nie nowych funkcji hybrydowych zostały wprowadzone w marca 2016 Technical Preview programu Configuration Manager.  

### <a name="new-in-configuration-manager-current-branch"></a>Nowe w programie Configuration Manager (wersji current branch)  
 Następujące nowe funkcje wprowadzone w marca 2016 r są dostępne w przypadku hybrydowych wdrożeń z usługi Intune i program Configuration Manager (wersji current branch) w wersji 1602. Tych funkcji wymaga użycia konsoli programu Configuration Manager do konfigurowania i zarządzania nimi.  

- **Zasady konfiguracji aplikacji systemu iOS**

  W wersji 1602 programu Configuration Manager (wersji current branch), można użyć zasad konfiguracji aplikacji umożliwiają określanie wartości ustawień, które mogą być wymagane, jeśli użytkownik uruchamia aplikację systemu iOS. Aby uzyskać więcej informacji, zobacz [Konfigurowanie aplikacji systemu iOS przy użyciu zasad konfiguracji aplikacji w programie System Center Configuration Manager](/sccm/apps/deploy-use/configure-ios-apps-with-app-configuration-policies).  

- **Zarządzanie aplikacjami zakupionymi zbiorczo systemu iOS**

  W wersji 1602 programu Configuration Manager (wersji current branch) można wdrażać i zarządzać aplikacjami zakupionymi zbiorczo w od firmy Apple Volume Purchase Program (VPP) przez zaimportowanie informacji o licencji ze sklepu z aplikacjami i śledzenie, ile licencji jest używanych. Aby uzyskać więcej informacji, zobacz [Zarządzanie zbiorczo zakupionymi aplikacjami systemu iOS z System Center Configuration Manager](/sccm/apps/deploy-use/manage-volume-purchased-ios-apps).  

- **Automatyczne tworzenie aplikacji mobilnych pakietu Office**

  Począwszy od wersji 1602 programu Configuration Manager (wersji current branch), następujące aplikacje mobilne Microsoft Office dla systemów Android i iOS są tworzone po uaktualnieniu z wersji 1511:  

  -   Microsoft Word  
  -   Microsoft Excel  
  -   Microsoft PowerPoint  
  -   Microsoft OneDrive  
  -   Microsoft OneNote (tylko iOS)  
  -   Microsoft Outlook  

  Te aplikacje będą dostępne w węźle aplikacji w konsoli programu Configuration Manager. Aby uzyskać więcej informacji na temat wdrażania aplikacji, zobacz [sposobu wdrażania aplikacji w programie System Center Configuration Manager](../../apps/deploy-use/deploy-applications.md).  

- **Ustawienia trybu kiosku dla urządzeń z systemem Android Samsung KNOX Standard**

  Tryb kiosku umożliwia blokowanie urządzenia w celu zezwolenia na działanie tylko niektórych funkcji.  Począwszy od wersji 1602 programu Configuration Manager (wersji current branch), można teraz określić ustawienia trybu kiosku dla urządzenia Samsung KNOX Standard. Aby uzyskać więcej informacji, zobacz [jak utworzyć elementy konfiguracji dla urządzeń z systemami Android i Samsung KNOX Standard zarządzanych bez klienta programu System Center Configuration Manager](/sccm/compliance/deploy-use/create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client).  

- **Blokady aktywacji systemu iOS**

  Począwszy od wersji 1602 programu Configuration Manager (wersji current branch), można zarządzać blokadą aktywacji systemu iOS, funkcją aplikacji Znajdź mój iPhone dla systemu iOS 7.1 i nowszym. Blokada aktywacji jest włączana automatycznie w przypadku użycia aplikacji Znajdź mój iPhone na urządzeniu.  Aby uzyskać więcej informacji, zobacz [Zarządzanie blokadą aktywacji systemu iOS obejścia dla programu System Center Configuration Manager](/sccm/mdm/deploy-use/manage-ios-activation-lock#bypass-activation-lock).  



## <a name="notices"></a>Powiadomienia

### <a name="system-center-2012-configuration-sp1-and-system-center-2012-r2-configuration-manager-rtm-support-for-hybrid-mobile-device-management-ending-on-april-10-2017"></a>Konfiguracja programu System Center 2012 SP1 i System Center 2012 R2 Configuration Manager (RTM): Obsługa hybrydowego zarządzania urządzeniami przenośnymi kończą się 10 kwietnia 2017 r.
*11 stycznia 2017 r.*

Obsługa programu System Center 2012 Configuration Manager SP1 i System Center 2012 R2 Configuration Manager RTM zakończona w dniu 12 lipca 2016 r. Następnie obsługę tych wersji łączenie z Microsoft Intune usługi dla hybrydowego zarządzania urządzeniami Przenośnymi kończy się 10 kwietnia 2017 r. Po tej dacie hybrydowego zarządzania urządzeniami Przenośnymi przestanie działać z tych wersji. Zarządzane urządzenia zasadniczo staną się Niezarządzani zgodnie z łącznika usługi Intune połączy się już w usłudze Intune. Dane programu Configuration Manager (takich jak zasady i aplikacje) nie będą przepływać do usługi Intune i dane zarządzanych urządzeń nie będą przepływać do programu Configuration Manager do momentu uaktualnienia ma miejsce.

Jeśli korzystasz z wdrożenia hybrydowego programu Configuration Manager 2012 z dodatkiem SP1 lub R2 RTM, zaleca się przed 10 kwietnia 2017 uaktualnienie do programu Configuration Manager (wersji current branch) lub obsługiwanych poprawkę programu Configuration Manager 2012 (R2 z dodatkiem SP1 lub z dodatkiem SP2), aby uniknąć przerw w działaniu usługi.

Dodatkowe zasoby:
-   [Uaktualnij do System Center Configuration Manager (wersji current branch)](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager)
-   [Planowanie uaktualnienia do systemu System Center 2012 R2 Configuration Manager SP1](https://technet.microsoft.com/library/jj822981.aspx#BKMK_PlanningR2SP1Upgrade)
-   [Planowanie uaktualnienia do programu System Center 2012 Configuration Manager SP2](https://technet.microsoft.com/library/jj822981.aspx#BKMK_PlanningSP2Upgrade)

### <a name="windows-phone-8-company-portal-upload-deprecated"></a>Przestarzałe przekazywania Portal firmy systemu Windows Phone 8
*25 października 2016 r.*

Pomocy technicznej usługi Intune jest przestarzałe w systemie Windows 8, Windows Phone 8 i Windows RT i pomoc techniczna dla portalu firmy systemu Windows Phone 8 kończy się w listopadzie została usunięta możliwość Przekaż podpisaną aplikację Portal firmy z poziomu konsoli programu Configuration Manager.  Urządzenia z systemem Windows 8, Windows Phone 8 i Windows RT, które są już zarejestrowane będą w dalszym ciągu obsługiwany, ale rejestracji dodatkowych urządzeń z tych platform nie jest obsługiwana.
