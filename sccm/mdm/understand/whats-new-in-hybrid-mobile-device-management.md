---
title: "What's new in hybrydowego zarządzania urządzeniami Przenośnymi"
titleSuffix: Configuration Manager
description: "Poznaj nowe funkcje zarządzania urządzeniami przenośnymi dostępne dla hybrydowych wdrożeń z programu Configuration Manager i usługi Intune."
ms.custom: na
ms.date: 11/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7b127cee-61f1-4681-9760-caebed36ddf5
author: dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 189e737eca5dee5bca3f0748cd1b4d944f868565
ms.sourcegitcommit: 4af1da9c18f5bdff31426cf1d58c7d949372292d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2017
---
# <a name="whats-new-in-hybrid-mobile-device-management-with-system-center-configuration-manager-and-microsoft-intune"></a>What's new in hybrydowego zarządzania urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i Microsoft Intune

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Ten artykuł zawiera szczegółowe informacje na urządzeniu przenośnym, nowe funkcje zarządzania urządzeniami Przenośnymi jest dostępne dla hybrydowych wdrożeń z programu System Center Configuration Manager i Microsoft Intune.     

> [!Note]    
> Usługa Intune na platformie Azure jest zalecanym rozwiązaniem MDM firmy Microsoft.     
> - Aby uzyskać szczegółowe informacje o nowych funkcjach i aktualizacje w autonomicznej usługi Intune, zobacz [What's new in Intune](https://docs.microsoft.com/intune/whats-new).    
> - Aby uzyskać szczegółowe informacje o tym, jak przeprowadzić migrację do autonomicznej usługi Intune, zobacz [migracji hybrydowego zarządzania urządzeniami Przenośnymi użytkowników i urządzeń do autonomicznej usługi Intune](https://docs.microsoft.com/sccm/mdm/deploy-use/migrate-hybridmdm-to-intunesa).
> - Aby uzyskać szczegółowe informacje o aktualizacjach interfejsu użytkownika dla usługi Intune i hybrydowego zarządzania urządzeniami Przenośnymi, zobacz [aktualizacje interfejsu użytkownika dla aplikacji użytkownika końcowego Intune](https://docs.microsoft.com/intune/whats-new-app-ui). 

##  <a name="compatibility-with-configuration-manager-versions"></a>Zgodność z wersjami programu Configuration Manager  
Każda sekcja w tym artykule wymieniono funkcje hybrydowych w trzech różnych kategorii. Aby sprawdzić zgodność funkcji w każdej kategorii z różnych wersji programu Configuration Manager, użyj poniższych wskazówek:  

|Funkcja kategorii|Opis|
|-|-|
|**Nowość w usłudze Microsoft Intune** | Ogólnie rzecz biorąc wszystkie funkcje wymienione w tej kategorii powinny współpracować z wszystkie wersje programu Configuration Manager. Zwalnia to tym System Center 2012 R2 Configuration Manager, ponieważ te funkcje tylko wymagane przez usługę Intune i nie wymagają dodatkowych funkcji w programie Configuration Manager.|
|**Nowość w programie Configuration Manager Technical Preview**| Wszystkie funkcje wymienione w tej kategorii są prawidłowe tylko w określonej wersji Technical Preview. Aby wypróbować te funkcje, należy zainstalować wersję Technical Preview określony w opisie funkcji. Aby uzyskać więcej informacji, zobacz [Technical Preview programu System Center Configuration Manager](../../core/get-started/technical-preview.md).|
|**Nowe w programie Configuration Manager (wersji current branch)**| Wszystkie funkcje wymienione w tej kategorii pracować tylko z określonej wersji programu Configuration Manager (wersji current branch), np. w wersji 1511 lub 1602. Jeśli używasz starszej wersji programu Configuration Manager dla danego wdrożenia hybrydowego, należy uaktualnić do wersji Configuration Manager (wersji current branch) określona w opisie funkcji. Aby uzyskać więcej informacji, zobacz [uaktualnienia do programu System Center Configuration Manager](../../core/servers/deploy/install/upgrade-to-configuration-manager.md).|


## <a name="november-2017"></a>2017 listopada

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune

- **Aplikacje zarządzane przez protokół tekstu od**<!-- 1414050  -->    
  Aplikacje zarządzane przez zestaw SDK aplikacji usługi Intune mają możliwość wysyłania wiadomości SMS.

- **Aplikacja Portal firmy dla macOS jest dostępna**<!--1541700-->    
  Portal firmy usługi Intune na macOS ma zaktualizowany obsługi aplikacji, która została zoptymalizowana do prawidłowo wyświetlić wszystkie powiadomienia informacji i zgodności, które użytkownicy potrzebują dla wszystkich urządzeń, które mają one zarejestrowane. I po Portal firmy usługi Intune został wdrożony na urządzeniu, AutoUpdate firmy Microsoft dla macOS dostarczają aktualizacje, które do niego. Możesz pobrać nowego portalu firmy usługi Intune dla macOS, logując się do witryny sieci Web Portal firmy usługi Intune z urządzenia macOS.

- **Microsoft Planner jest obecnie częścią zarządzania (aplikacjami mobilnymi MAM) aplikacji mobilnej listę zatwierdzonych aplikacji**  <!-- 1248473 -->    
  Aplikacja Microsoft Planner dla systemów iOS i Android jest obecnie częścią zatwierdzonych aplikacji do zarządzania aplikacjami mobilnymi (MAM). Aplikację można skonfigurować za pomocą bloku ochrony aplikacji usługi Intune w portalu Azure do wszystkich dzierżawców. Aby uzyskać więcej informacji, zobacz [MAM listę zatwierdzonych aplikacji](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).

- **Rejestruje dostęp do zarządzanych aplikacji dla systemu iOS**<!-- 1469920 -->    
  Użytkownikom końcowym z zainstalowaną przeglądarkę zarządzane mogą teraz wyświetlanie stanu zarządzania Microsoft wszystkie opublikowane aplikacje i wyśle dzienniki do rozwiązywania problemów z ich zarządzane aplikacje systemu iOS.
  
  Dowiedz się, jak włączyć trybu rozwiązywania problemów w programie Managed Browser na urządzeniu z systemem iOS, zobacz [jak uzyskać dostęp do zarządzanych aplikacji dzienników przy użyciu programu Managed Browser w systemie iOS](https://docs.microsoft.com/intune/app-configuration-managed-browser#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios).

- **Ulepszenia urządzenia Konfiguracja przepływu pracy w portalu firmy dla systemu iOS w wersji 2.9.0**    
  Ulepszono przepływu pracy ustawień urządzenia w aplikacji Portal firmy dla systemu iOS. Język jest bardziej przyjazny dla użytkownika i ekrany już połączyć w miarę możliwości. Również wprowadzono język dokładniej do firmy przy użyciu nazwy firmy przez cały tekst Instalatora. Ten zaktualizowany przepływ pracy można wyświetlić na [nowości w aplikacji interfejsu użytkownika](https://docs.microsoft.com/intune/whats-new-app-ui#week-of-november-13-2017) strony.

- **Opinie wyświetla monit dotyczący aplikacji Portal firmy dla systemu Android**<!--1165249-->    
Aplikacja Portal firmy dla systemu Android teraz żądania opinii użytkowników końcowych. Tej opinii będą wysyłane bezpośrednio do firmy Microsoft i zapewnić użytkownikom końcowym możliwość Przegląd aplikacji w sklepie Google Play publicznego. Opinia nie jest wymagana i łatwo może być ukryty, dlatego użytkownicy mogą nadal używać aplikacji. 

- **Powiadamia użytkowników końcowych, jakie informacje o urządzeniu są widoczne dla urządzeń z systemem Windows 10**<!--1337920-->    
Dodaliśmy **typ własności** do ekranu szczegóły urządzenia w aplikacji Portal firmy dla systemu Windows 10. Dzięki temu użytkownicy dowiedzieć się więcej o ochronie prywatności bezpośrednio z tej strony z dokumentów użytkownika usługi Intune. Również będą w stanie zlokalizować tę informację na **o** ekranu.

- **Nowy "rozwiązać" Akcja jest dostępna dla urządzeń z systemem Android**<!--1583480-->    
  Aplikacja Portal firmy dla systemu Android wprowadzają akcję "Usuń" na _zaktualizować ustawienia urządzenia_ strony. Wybranie tej opcji spowoduje przejście użytkownika bezpośrednio do ustawienia powodującego swoje urządzenia jako niezgodne. Aplikacja Portal firmy dla systemu Android obsługuje obecnie tę akcję dla [kod dostępu urządzenia](https://docs.microsoft.com/intune-user-help/set-your-pin-or-password-android), [szyfrowania urządzenia](https://docs.microsoft.com/intune-user-help/encrypt-your-device-android), [debugowanie USB](https://docs.microsoft.com/intune-user-help/you-need-to-turn-off-usb-debugging-android), i [nieznany Źródła](https://docs.microsoft.com/intune-user-help/you-need-to-turn-off-unknown-sources-android) ustawienia. 


### <a name="new-in-configuration-manager-current-branch"></a>Nowe w programie Configuration Manager (wersji current branch)

- **Akcje dotyczące zgodności z systemem innym niż**<!--1321366 -->    
  Można teraz skonfigurować uporządkowane czasu sekwencję akcji, które są stosowane do urządzeń, które stwierdzona zostanie niezgodność. Na przykład można powiadamiać użytkowników o niezgodnych urządzeń za pośrednictwem poczty e-mail lub oznaczyć te urządzenia niezgodne. Aby uzyskać więcej informacji, zobacz [ustawiania akcji dla zgodności z systemem innym niż](/sccm/mdm/deploy-use/actions-for-noncompliance).

- **Nowe ustawienia zasad zarządzania aplikacjami mobilnymi**<!-- 1324760 -->    
  Następujące ustawienia zostały dodane do ustawienia zasad zarządzania aplikacjami mobilnymi:
  - **Wyłącz synchronizację kontaktów**: Aplikacja uniemożliwia zapisywania danych do aplikacji natywnej kontaktów na urządzeniu.
  - **Wyłącz drukowanie**: Zapobiega aplikacji z drukowaniem pracy lub szkoły danych.

  Zobacz [ochrona aplikacji przy użyciu zasad ochrony aplikacji w programie Configuration Manager](/sccm/mdm/deploy-use/protect-apps-using-mam-policies) próby nowe ustawienia zasad ochrony aplikacji.

- **Obsługa urządzeń z systemem Windows 10 ARM64**<!-- 1355000 -->    
  Scenariuszy zarządzania urządzeniami Przenośnymi urządzeniami przenośnymi hybrydowego będą obsługiwane na urządzeniach ARM64 z systemem Windows 10, jeśli te urządzenia nie są dostępne. Aby uzyskać więcej informacji, zobacz [Obsługa urządzeń z systemem Windows 10 ARM64](/sccm/core/plan-design/changes/whats-new-in-version-1710#windows-10-arm64-device-support).

- **Ulepszona obsługa profilu sieci VPN w konsoli programu Configuration Manager**<!-- 1318232 -->    
  W tej wersji Zaktualizowaliśmy VPN profilu Kreatora właściwości strony i aby wyświetlić ustawienia odpowiednie dla wybranej platformy. Ta funkcja była wcześniej dostępne w wersji Configuration Manager Technical Preview 1709 i są teraz dostępne w przypadku wdrożeń hybrydowych usługi Intune i programu Configuration Manager (Current Branch) 1710:
  - [Ulepszona obsługa profilu sieci VPN w konsoli programu Configuration Manager](/sccm/core/plan-design/changes/whats-new-in-version-1710#improved-vpn-profile-experience-in-configuration-manager-console).


### <a name="new-in-configuration-manger-technical-preview-1711"></a>Nowa w programie Configuration Manager Technical Preview 1711

- **Nowe opcje zasad zgodności dla systemu Windows 10** można teraz skonfigurować nowe opcje zasad zgodności dla urządzeń z systemem Windows 10. Nowe ustawienia wymuszania zasad zapory, Kontrola konta użytkownika systemu Windows Defender Antivirus i przechowywanie wersji kompilacji systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [nowe opcje zasad zgodności dla systemu Windows 10](/sccm/core/get-started/capabilities-in-technical-preview-1711#new-compliance-policy-options-for-windows-10).


## <a name="october-2017"></a>2017 października

### <a name="new-in-configuration-manager-technical-preview-1709"></a>Nowość w programie Configuration Manager Technical Preview 1709

- **Ulepszona obsługa profilu sieci VPN w konsoli programu Configuration Manager**<!-- 1313282 -->     
  Ustawienia profilu sieci VPN, teraz są filtrowane zgodnie z platform. Podczas tworzenia nowych profilów sieci VPN każdej z obsługiwanych platform zawiera tylko ustawienia odpowiednie dla platformy. Nie dotyczy istniejących profilów sieci VPN. Więcej o tej zmianie [tutaj](/sccm/core/get-started/capabilities-in-technical-preview-1709#improved-vpn-profile-experience-in-configuration-manager-console).


### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune  

- **Wskaźnik postępu instalacji urządzenia w portalu firmy Android**<!--1565657-->    
  Aplikacja Portal firmy dla systemu Android zawiera wskaźnik postępu instalacji urządzenia, gdy użytkownik jest rejestrowanie swojego urządzenia. Wskaźnik przedstawia nowe stany, począwszy od "Konfigurowanie urządzenia...", a następnie "... rejestrowanie urządzenia", "Zakończył rejestrowanie urządzenia...", a następnie "Kończenie konfigurowania urządzenia...".  

- **Obsługę uwierzytelniania opartego na certyfikatach w portalu firmy dla systemu iOS**<!--1029830-->    
  Dodaliśmy obsługę uwierzytelniania opartego na certyfikatach (CBA) w aplikacji Portal firmy dla systemu iOS. Użytkownicy z CBA wprowadzić swoją nazwę użytkownika, a następnie wybrać link "Zaloguj się przy użyciu certyfikatu". CBA jest już obsługiwana w aplikacji Portal firmy dla systemu Android i Windows. Aby dowiedzieć się więcej na [logowania do aplikacji Portal firmy](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) strony.

- **Ulepszenia urządzenia Konfiguracja przepływu pracy w portalu firmy**<!--1490692-->    
  Ulepszono przepływu pracy ustawień urządzenia w aplikacji Portal firmy dla systemu Android. Język jest bardziej przyjazny dla użytkownika i specyficzne dla firmy, a w miarę możliwości zostały połączyć ekranów. Można je wyświetlić na [nowości w aplikacji interfejsu użytkownika](https://docs.microsoft.com/intune/whats-new-app-ui#week-of-october-2-2017) strony.

- **Ulepszone wskazówki dotyczące żądania dostępu do kontaktów na urządzeniach z systemem Android**<!--1484985-->    
  Aplikacja Portal firmy dla systemu Android często wymaga od użytkownika końcowego zaakceptować uprawnień do kontaktów. Jeśli użytkownik odmówi dostęp, wyświetlane powiadomienie w aplikacji, które je, aby przyznać jej dostęp warunkowy do alertów. 

- **Zabezpieczanie korygowania uruchamiania dla systemu Android**<!--1490712-->    
  Użytkowników końcowych urządzeń z systemem Android będzie można wybierać z powodu niezgodności w aplikacji Portal firmy. Jeśli to możliwe, to może potrwać je bezpośrednio do poprawnej lokalizacji w aplikacji ustawień, aby rozwiązać ten problem. 

- **Powiadomienia wypychane dodatkowych dla użytkowników końcowych w aplikacji Portal firmy dla systemu Android Oreo**<!--1475932 -->    
  Dodatkowe powiadomienia do wskazania je, gdy aplikacja Portal firmy dla systemu Android Oreo wykonuje zadania w tle, takie jak pobieranie zasad z usługi Intune będzie widoczny dla użytkowników. Powiadomienia zwiększenia przejrzystości dla użytkowników końcowych, temat, do portalu firmy jest wykonywania zadań administracyjnych na urządzeniu. Jest to część ogólnych [optymalizacji interfejsu użytkownika portalu firmy](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune) aplikacji Portal firmy dla systemu Android Oreo. 

- **Nowe zachowania dla aplikacji Portal firmy dla systemu Android przy użyciu profilów pracy**<!--1485783-->    
  Po zarejestrowaniu Android pracy urządzenia z profilem pracy jest aplikacja Portal firmy w profilu pracy, który wykonuje zadania zarządzania na urządzeniu. 

  Jeśli korzystasz z aplikacji z obsługą funkcji MAM w ten profil, aplikacja Portal firmy dla systemu Android nie spełnia już użycia. Aby poprawić środowisko pracy profilu, Intune automatycznie spowoduje ukrycie osobistych aplikacji Portal firmy po rejestracji profilu pracy powiodło się.

  Aplikacja Portal firmy dla systemu Android można włączyć w dowolnym momencie w profilu osobistego przeglądając [Portal firmy ze sklepu Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) i naciskając **włączyć**.

- **Firmy, Portal dla Windows 8.1 i Windows Phone 8.1 przechodzenia do trybu utrzymywanie**<!--1428681-->    
 Zostanie wyświetlone powiadomienie został dodany do anonsowania, że przechodzenia do trybu utrzymywanie aplikacji Portal firmy dla Windows 8.1 i Windows Phone 8.1. Aby uzyskać więcej informacji, zobacz [powiadomienia](#notices).  

- **Blok nieobsługiwany rejestracji urządzenia Samsung Knox**<!-- 1490695 -->    
  Tylko aplikacja Portal firmy próbuje zarejestrować obsługiwane urządzenia Samsung Knox. Aby uniknąć błędów aktywacji KNOX, które uniemożliwiają rejestracji MDM, rejestracji urządzenia nastąpiła tylko jeśli urządzenie znajduje się w [listy urządzeń opublikowanych przez firmy Samsung](https://www.samsungknox.com/knox-supported-devices/knox-workspace). Urządzenia Samsung mogą mieć numery modelu, które obsługują KNOX, podczas gdy inne, które nie. Sprawdź zgodność Knox z odsprzedawcą urządzenia przed zakupu i wdrażania. Pełną listę zweryfikowanych urządzeń w można znaleźć [ustawienia zasad systemu Android i Samsung KNOX Standard](https://docs.microsoft.com/intune-classic/deploy-use/android-policy-settings-in-microsoft-intune#supported-samsung-knox-standard-devices).

- **Wsparcie dla systemu Android 4.3 i dolny**<!--1171126, 1326920 -->    
  Zostanie wyświetlone powiadomienie został dodany na końcu obsługę systemu Android 4.3 i niżej. Aby uzyskać więcej informacji, zobacz [powiadomienia](#notices).

- **Powiadamia użytkowników końcowych w informacjach urządzenia są widoczne na zarejestrowanych urządzeniach**<!--1165314-->    
  Dodajemy **typ własności** do ekranu szczegóły urządzenia na wszystkie aplikacje portalu firmy. Dzięki temu użytkownicy dowiedzieć się więcej o ochronie prywatności bezpośrednio z [informacjach można wyświetlić firmie?](https://docs.microsoft.com/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune) artykułu. To będzie można zetknie we wszystkich aplikacjach Portal firmy w najbliższej przyszłości. Wprowadziliśmy to dla systemu iOS w [września](https://docs.microsoft.com/intune/whats-new#week-of-september-11-2017). 


## <a name="september-2017"></a>2017 września

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune     

- **Akcja dodaje do aplikacji Portal firmy dla systemu Windows 10 odświeżania**<!-- 1132468 -->    
    Aplikacja Portal firmy dla systemu Windows 10 umożliwia odświeżanie danych w aplikacji, przenosząc albo odświeżyć lub na pulpitach, naciskając klawisz F5.

- **Powiadamia użytkowników końcowych, jakie informacje o urządzeniu są widoczne dla systemu iOS**<!--739894-->    
    Dodaliśmy **typ własności** do ekranu szczegóły urządzenia w aplikacji Portal firmy dla systemu iOS. Dzięki temu użytkownicy dowiedzieć się więcej o ochronie prywatności bezpośrednio z tej strony z dokumentów użytkownika usługi Intune. Również będą oni mogli zlokalizować te informacje na ekranie informacje. 

- **Łatwiejsze do zrozumienia właściwej dla aplikacji Portal firmy dla systemu Android**<!---1396349-->       
    Proces rejestracji w aplikacji Portal firmy dla systemu Android został uproszczony na nowy tekst w celu ułatwienia dla użytkowników końcowych zarejestrowania. Jeśli masz dokumentacji rejestrowania niestandardowego, należy zaktualizować je, aby uwzględnić nowe ekrany. Przykładowe obrazy można znaleźć w naszych [aktualizacje interfejsu użytkownika dla aplikacji użytkownika końcowego Intune](https://docs.microsoft.com/intune/whats-new-app-ui#week-of-september-11-2017) strony.

- **Zezwalaj na zasady w aplikacji Portal firmy dla systemu Windows 10 dodane do systemu Windows Information Protection**<!-- 677129 -->    
    Aplikacja Portal firmy dla systemu Windows 10 została zaktualizowana do obsługi systemu Windows informacji ochrony (pracy w toku). Aplikację można dodać do pracy w toku Zezwalaj na zasady. Dzięki tej zmianie aplikacji nie ma już ma zostać dodany do **wykluczone** listy. 

     Tylko jeden element konfiguracji pracy w toku mogą być dostarczane na urządzeniu.  Jeśli dwa elementy konfiguracji pracy w toku są przeznaczone do tego samego urządzenia, zastosowanie żadne zasady pracy w toku.

- **Powiadomienie o pomocy technicznej dodane dla systemu iOS 8.0 zakończeniu**    
    Zostanie wyświetlone powiadomienie została dodana do zakończenia wsparcia dla systemu iOS 8.0. Aby uzyskać więcej informacji, zobacz [powiadomienia](#notices).

## <a name="august-2017"></a>2017 sierpnia

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune     

- **Nowe zalogowany środowisko dla użytkowników portalu firmy Android i zasady ochrony aplikacji użytkownicy**<!-- 621669 -->    
Użytkownicy końcowi mogą teraz przeglądać aplikacje, zarządzać urządzeniami i wyświetlić kontakt z działem IT informacje przy użyciu aplikacji Portal firmy dla systemu Android bez rejestrowania swoich urządzeń z systemem Android. Ponadto jeśli użytkownik końcowy używa aplikacji są chronione przez zasady aplikacji usługi Intune, a uruchamia Portal firmy dla systemu Android, użytkownik końcowy nie jest już wyświetlony monit o zarejestrowanie urządzenia.


## <a name="july-2017"></a>2017 lipca

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune

- **Koniec Obsługa powiadomienia dodane dla systemów Android i Windows Phone**

    Nowe powiadomienia zostały dodane w celu obsługi wersji systemów Android i Windows Phone. Aby uzyskać więcej informacji, zobacz [powiadomienia](#notices).


### <a name="new-in-configuration-manager-current-branch"></a>Nowe w programie Configuration Manager (wersji current branch)

Następujące funkcje, które były wcześniej dostępne w wersjach Configuration Manager Technical Preview są teraz dostępne w przypadku hybrydowych wdrożeń z usługi Intune i program Configuration Manager (wersji current branch) wersja 1706.

- [Powierzyć obsługę Entrust urzędów certyfikacji](/sccm/core/get-started/capabilities-in-technical-preview-1706#support-for-entrust-certification-authorities)
- [Nowe ustawienia zasad zarządzania aplikacjami mobilnymi](/sccm/core/plan-design/changes/whats-new-in-version-1706#new-mobile-application-management-policy-settings)
- [Aktualizacje w systemie Android for Work Konfiguracja udostępniania](/sccm/core/plan-design/changes/whats-new-in-version-1706#updates-to-android-for-work-sharing-configuration)
- [Nowe reguły zasad zgodności urządzenia](/sccm/core/plan-design/changes/whats-new-in-version-1706#new-device-compliance-policy-rules)
- [Nowe ustawienia konfiguracji dla urządzeń z systemem Windows 10, które nie są zarządzane przy użyciu klienta programu Configuration Manager](/sccm/core/plan-design/changes/whats-new-in-version-1706#new-configuration-settings-for-windows-10-devices-that-are-not-managed-with-the-configuration-manager-client)
- [Obsługa Cisco (IPsec) macOS profilów sieci VPN](/sccm/core/get-started/capabilities-in-technical-preview-1706#cisco-ipsec-support-for-macos-vpn-profiles)
- [Android i iOS ograniczenia rejestracji](/sccm/core/plan-design/changes/whats-new-in-version-1706#android-and-ios-enrollment-restrictions) 

## <a name="june-2017"></a>2017 czerwca

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune

- **Change your MDM authority (Zmiana urzędu MDM)**

  Począwszy od programu Configuration Manager 1610 wersji, można zmienić urzędu zarządzania urządzeniami Przenośnymi bez konieczności kontaktowania się Microsoft Support i bez konieczności wyrejestrowywania i Zarejestruj ponownie istniejących zarządzanych urządzeń. Aby uzyskać więcej informacji, zobacz [zmienić urzędu zarządzania urządzeniami Przenośnymi](/sccm/mdm/deploy-use/change-mdm-authority).

- **Zarządzane przeglądarki i aplikacji integracji serwera proxy**

  Intune Managed Browser teraz można zintegrować z usługą serwera Proxy aplikacji usługi Azure AD, aby umożliwić użytkownikom dostęp do wewnętrznych witryn sieci web, nawet wtedy, gdy użytkownik pracuje zdalnie. Użytkownicy przeglądarki wprowadź adres URL witryny ulega zmianie, a w programie Managed Browser kieruje żądanie za pośrednictwem bramy sieci web serwera proxy aplikacji. Aby uzyskać więcej informacji, zobacz [dostępu do internetowego zarządzania przy użyciu zasad przeglądarki Managed](https://docs.microsoft.com/intune/app-configuration-managed-browser).

- **Aplikacja Portal firmy dla systemu Android ma teraz nowe środowisko użytkownika końcowego zasad ochrony aplikacji**

  Na podstawie opinii klientów, firma Microsoft został zmodyfikowany w aplikacji Portal firmy dla systemu Android wyświetlić **dostępu firmy zawartości** przycisku. Celem jest, aby uniemożliwić użytkownikom końcowym niepotrzebnie przechodzi przez proces rejestracji, gdy potrzebują dostępu do aplikacji, które obsługuje zasady ochrony aplikacji z funkcją zarządzania aplikacjami mobilnymi usługi Intune. Te zmiany można wyświetlić na [nowości w aplikacji interfejsu użytkownika](https://docs.microsoft.com/intune/whats-new-app-ui) strony.

- **Nowa akcja menu można łatwo usunąć Portal firmy**

  Na podstawie opinii użytkowników, aplikacja Portal firmy dla systemu Android została dodana nowa akcja menu zainicjować usuwanie Portal firmy z urządzenia. Ta akcja powoduje usunięcie urządzenia z zarządzania usługi Intune, aby aplikację można usunąć z urządzenia przez użytkownika. Te zmiany można wyświetlić na [nowości w aplikacji interfejsu użytkownika](https://docs.microsoft.com/intune/whats-new-app-ui) strony i w [dokumentacja użytkownika Android](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-android).

- **Ulepszenia aplikacji synchronizację z usługą Windows Update twórców 10**

  Aplikacja Portal firmy dla systemu Windows 10 teraz automatycznie inicjuje synchronizacji żądania instalacji aplikacji dla urządzeń z systemem Windows 10 twórców aktualizację (wersja 1703). Zmniejsza to problem Gaśnięcie silnika w stanie "Oczekiwanie synchronizacji" instaluje aplikację. Ponadto użytkownicy mogą ręcznie zainicjować synchronizację z poziomu aplikacji. Te zmiany można wyświetlić na [nowości w aplikacji interfejsu użytkownika](https://docs.microsoft.com/intune/whats-new-app-ui) strony.

- **Nowe środowisko z przewodnikiem dla Portal firmy dla systemu Windows 10**

  Aplikacja Portal firmy dla systemu Windows 10 zawiera przewodnik obsługi wskazówki usługi Intune dla urządzeń, które nie zostały zidentyfikowane lub zarejestrowane. Nowe środowisko zawiera instrukcje krok po kroku, które prowadzą użytkowników przez proces rejestracji w usłudze Azure Active Directory (wymagane dla funkcji dostępu warunkowego) i rejestrowanie MDM (wymagane dla funkcji zarządzania urządzeniami). Przewodnik obsługi będzie dostępna na stronie głównej portalu firmy. Użytkownicy mogą nadal używać aplikacji, jeśli nie zostanie wypełnione, rejestracji i rejestracji, ale może wystąpić ograniczenie funkcjonalności.

  Ta aktualizacja jest tylko widoczne na urządzeniach z systemem Windows 10 Anniversary Update (kompilacja 1607) lub nowszej. Te zmiany można wyświetlić na [nowości w aplikacji interfejsu użytkownika](https://docs.microsoft.com/intune/whats-new-app-ui) strony.

- **Ulepszenia kafelków aplikacji w aplikacji Portal firmy dla systemu iOS**

  Zaktualizowaliśmy projekt kafelków aplikacji na stronie głównej znakowania koloru, ustawione przez Portal firmy. Aby uzyskać więcej informacji, zobacz [nowości w aplikacji interfejsu użytkownika](https://docs.microsoft.com/intune/whats-new-app-ui).

- **Selektor konta teraz dostępne dla aplikacji Portal firmy dla systemu iOS**

  Naszego nowego konta selektora mogą zobaczyć użytkownicy urządzeń z systemem iOS, podczas logowania się do portalu firmy Jeżeli Użyj ich pracy lub szkołą konta do logowania się do innych aplikacji firmy Microsoft. Aby uzyskać więcej informacji, zobacz [nowości w aplikacji interfejsu użytkownika](https://docs.microsoft.com/intune/whats-new-app-ui).

### <a name="new-in-configuration-manager-technical-preview-1706"></a>Nowość w programie Configuration Manager Technical Preview 1706

- **Nowe ustawienia elementu konfiguracji systemu Windows**  <!-- 1354715 -->    

  Nowe elementy konfiguracji systemu Windows są dostępne w ramach kategorii ustawienia haseł, urządzenia, magazynu i Microsoft Edge. Aby uzyskać więcej informacji, zobacz [ustawienia elementu konfiguracji systemu Windows nowego](/sccm/core/get-started/capabilities-in-technical-preview-1706#new-windows-configuration-item-settings).

- **Nowe reguły zasad zgodności urządzenia**    

  Można teraz skonfigurować nowe opcje zasad zgodności, które były wcześniej dostępne tylko w autonomicznej usługi Intune. Aby uzyskać więcej informacji, zobacz [ulepszenia zasad zgodności urządzenia](/sccm/core/get-started/capabilities-in-technical-preview-1706#new-device-compliance-policy-rules).

- **Android i iOS ograniczenia rejestracji**<!-- 1290826 -->      

  Administratorzy można teraz określić, że użytkownicy nie można zarejestrować urządzeń osobistych Android lub iOS w środowisku hybrydowym. Dzięki temu możesz limit zarejestrowanych urządzeń do predeclared, urządzenia należące do firmy lub zarejestrowane w usłudze Device Enrollment Program tylko urządzeń z systemem iOS. Aby uzyskać więcej informacji, zobacz [Android i iOS ograniczenia rejestracji](/sccm/core/get-started/capabilities-in-technical-preview-1706#android-and-ios-enrollment-restrictions).

- **Obsługa urzędów certyfikacji Entrust**<!-- 1350740 -->     

  Program Configuration Manager obsługuje teraz Entrust urzędów certyfikacji; Dzięki temu dostarczania certyfikatów PFX na urządzeniach zarejestrowanych w programie Microsoft Intune.    

  Podczas dodawania roli punktu rejestracji certyfikatu w programie Configuration Manager, można skonfigurować Entrust jako urząd certyfikacji. Podczas dodawania nowego profilu certyfikatu, który wystawia certyfikaty PFX, możesz wybrać Microsoft lub Entrust urzędu certyfikacji.

  **Znany problem**: W 1706 technical preview certyfikaty PFX nie są wystawiane na potrzeby urzędów certyfikacji firmy Microsoft. Nie dotyczy to profilów SCEP lub importowanych certyfikatów PFX.

- **Obsługa Cisco (IPsec) macOS profilów sieci VPN**  <!-- 1321367 -->    

  Można utworzyć macOS profil sieci VPN z Cisco (IPsec) jako typ połączenia. Aby uzyskać więcej informacji, zobacz [tworzenie profilów sieci VPN](/sccm/mdm/deploy-use/create-vpn-profiles#create-vpn-profiles).


## <a name="april-2017"></a>Kwietnia 2017

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune

- **MyApps dostępne dla programu Managed Browser**

  Microsoft MyApps już lepszą obsługę w programie Managed Browser. Zarządzane przeglądarki użytkowników, którzy nie są przeznaczone dla zarządzania zostanie przeniesiony bezpośrednio z usługą MyApps, gdzie uzyskać dostęp do swoich aplikacji SaaS udostępniane przez administratora. Użytkownicy, którzy są przeznaczone do zarządzania usługi Intune w dalszym ciągu mieć możliwość dostępu MyApps z wbudowanych zakładki Managed Browser.

- **Nowe ikony programu Managed Browser i portalu firmy**

  W programie Managed Browser odbiera zaktualizowanym ikonom dla systemu Android i iOS wersji aplikacji. Nową ikonę będzie zawierał zaktualizowane wskaźnika usługi Intune, aby był bardziej spójny z innych aplikacji w Enterprise Mobility + Security (EM + S). Możesz wyświetlać ikonę Nowy w programie Managed Browser na [what's new in strony interfejsu użytkownika aplikacji usługi Intune](https://docs.microsoft.com/intune/whats-new-app-ui).

  Portal firmy jest również odbieranie zaktualizowanym ikonom dla systemu Android, iOS i Windows wersje aplikacji, aby zwiększyć zgodność z innymi aplikacjami w EM + S. Te ikony zostanie wydana stopniowo na platformach z kwietnia do maja opóźnione.

- **Zaloguj się wskaźnik postępu w portalu firmy dla systemu Android**

  Aktualizacja aplikacji Portal firmy dla systemu Android zawiera znak wskaźnik postępu, gdy użytkownik uruchamia lub wznowieniu działania aplikacji. Wskaźnik przechodzi nowe stany, począwszy od "Łączenie...", "Podpisywanie cali...", a następnie "Sprawdzanie wymagań dotyczących zabezpieczeń..." przed zezwoleniem mu dostęp do tej aplikacji. Można wyświetlić nowe ekrany dla aplikacji Portal firmy dla systemu Android na [what's new in strony interfejsu użytkownika aplikacji usługi Intune](https://docs.microsoft.com/intune/whats-new-app-ui).

- **Zablokuj aplikacjom uzyskiwanie dostępu do usługi SharePoint Online**

  Teraz można utworzyć zasad dostępu warunkowego opartego na aplikacji, aby zablokować aplikacje, których nie zastosowano zasady ochrony aplikacji do nich dostęp [usługi SharePoint Online](https://docs.microsoft.com/intune-classic/deploy-use/mam-ca-for-sharepoint-online). W tym scenariuszu dostępu warunkowego opartego na aplikacji można określić aplikacje, które mają dostęp do usługi SharePoint Online przy użyciu portalu Azure.

### <a name="new-in-configuration-manager-technical-preview-1704"></a>Nowość w programie Configuration Manager Technical Preview 1704

- **Konfigurowanie aplikacji systemu Android przy użyciu zasad konfiguracji aplikacji**

  Zasady konfiguracji aplikacji w programie System Center Configuration Manager (program Configuration Manager) można użyć do dystrybucji wstępnie skonfigurowanych ustawień, gdy użytkownik uruchamia aplikację w systemie Android pracy urządzeń. Zasady konfiguracji aplikacji systemu android są dostępne tylko na urządzeniach z systemem Android do pracy i dotyczą zatwierdzonych aplikacji w sklepie Play pracy magazynu. Aby uzyskać informacje na temat sposobu wypróbować tę funkcję, zobacz [Android Konfigurowanie aplikacji przy użyciu zasad konfiguracji aplikacji](/sccm/core/get-started/capabilities-in-technical-preview-1704#configure-android-apps-with-app-configuration-policies).

## <a name="march-2017"></a>2017 marca

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune

- **Nowe środowisko użytkownika dla aplikacji Portal firmy dla systemu Android**

  Aplikacja Portal firmy dla systemu Android ma bardziej nowoczesny wygląd i działanie jej interfejsu użytkownika. Ważne aktualizacje są:

  - Kolory: Nagłówków karty w portalu firmy mają kolor zdefiniowany IT marki.
  - Aplikacje: W **aplikacje** karcie **polecane aplikacje** i **wszystkie aplikacje** przyciski zostały zaktualizowane.
  - Wyszukiwania: W **aplikacje** karcie **wyszukiwania** przestawne przycisku akcji jest przycisk.
  - Nawigowanie po aplikacji: **Wszystkie aplikacje** widok przedstawia widok z kartami **proponowanym**, **wszystkie**, i **kategorii** ułatwiające nawigację.
  - Pomoc techniczna: **Moje urządzenia** i **kontakt z działem IT** karty są aktualizowane w celu zwiększenia czytelności.

  Aby uzyskać więcej informacji na temat tych zmian, zobacz [aktualizacje interfejsu użytkownika dla aplikacji przez użytkownika końcowego Intune](https://docs.microsoft.com/intune/whats-new-app-ui).

- **Podpisywanie skryptów dla aplikacji Portal firmy systemu Windows 10**

  Jeśli potrzebujesz do pobierania i ładować bezpośrednio aplikację Portal firmy dla systemu Windows 10, teraz umożliwia skrypt uprościć i usprawnić proces podpisywania aplikacji w Twojej organizacji.  Aby pobrać skrypt oraz instrukcje dotyczące korzystania z niego, zobacz [podpisywania skryptów dla systemu Windows 10 Portal firmy Microsoft Intune](https://aka.ms/win10cpscript) w galerii TechNet. Aby uzyskać więcej informacji na temat to zawiadomienie, zobacz [aktualizowanie aplikacji Portal firmy dla systemu Windows 10](https://blogs.technet.microsoft.com/intunesupport/2017/03/13/updating-your-windows-10-company-portal-app/) na blogu zespołu pomocy technicznej usługi Intune.

- **Ulepszona obsługa użytkowników systemu Android na podstawie w Chinach**

  Z powodu braku sklepu Google Play w Chinach urządzenia z systemem Android musi uzyskać aplikacje z języka chińskiego rynków. Portal firmy obsługuje ten przepływ pracy dzięki przekierowaniu użytkowników systemu Android w Chinach pobrania aplikacji Portal firmy i Outlook z magazynów lokalnych aplikacji. Zwiększa to środowisko użytkownika, gdy zasady dostępu warunkowego są włączone, zarówno w przypadku zarządzania urządzeniami przenośnymi, jak i zarządzania aplikacjami mobilnymi. Aplikacji portalu firmy i Outlook dla systemu Android są dostępne w następujących przechowywanych w chińskiej wersji językowej aplikacji:

  - [Usługi Baidu](https://go.microsoft.com/fwlink/?linkid=836946)
  - [Xiaomi](https://go.microsoft.com/fwlink/?linkid=836947)
  - [Tencent](https://go.microsoft.com/fwlink/?linkid=836949)
  - [Huawei](https://go.microsoft.com/fwlink/?linkid=836948)
  - [Wandoujia](https://go.microsoft.com/fwlink/?linkid=836950)

- **Upewnij się, że w aplikacji Portal firmy są aktualne**

  W grudnia 2016 r., firma Microsoft opublikowała aktualizacji, która umożliwiała wymuszania uwierzytelnianie wieloskładnikowe (MFA) w grupie użytkowników podczas rejestracji systemu iOS, Android, Windows 8.1 + lub urządzenia Windows Phone 8.1 +. Ta funkcja nie może działać bez określonych wersji linii bazowej w aplikacji Portal firmy dla systemu Android (v5.0.3419.0 +) i iOS (v2.1.17 +).

  Możliwości zarządzania usługi Intune są stale poprawy i wiele ulepszeń ma koordynowane aktualizacje aplikacji portalu firmy na wszystkich obsługiwanych platformach. W związku z tym zaleca się utrzymywanie najnowsze wersje aplikacji Portal firmy zainstalowanych na urządzeniach, aby korzystając z usprawnień w usłudze Intune i aby uzyskać najlepsze środowisko użytkownika.

  >[!Tip]
  > Ma ustawić swoje urządzenia do automatycznego aktualizowania aplikacji ze sklepu z aplikacjami odpowiednich użytkowników. Jeśli udostępnione w aplikacji Portal firmy dla systemu Android w udziale sieciowym, możesz pobrać najnowszą wersję ze [Microsoft Download Center](https://www.microsoft.com/download/details.aspx?id=49140).

- **Teams firmy Microsoft jest teraz włączony do zarządzania aplikacjami Mobilnymi w systemach iOS i Android**

  Aplikacje Teams firmy Microsoft dla systemu iOS i Android teraz są włączone dla funkcji zarządzania (aplikacjami mobilnymi MAM) aplikacji mobilnej usługi Intune, więc dają możliwość zespołów pracę za darmo na urządzeniach, przy jednoczesnym zapewnieniu konwersacje i danych firmowych jest chroniony w każdym Włącz. Aby uzyskać więcej informacji, zobacz [anons Teams Microsoft](https://blogs.technet.microsoft.com/enterprisemobility/2017/03/14/microsoft-teams-is-now-generally-available-and-mam-enabled-on-ios-and-android/) w blogu dotyczącym pakietu Enterprise Mobility i zabezpieczeń.

### <a name="new-in-configuration-manager-technical-preview-1703"></a>Nowość w programie Configuration Manager Technical Preview 1703

- **Dodatkowe wsparcie dla scenariuszy programu Apple Volume Purchase Program**

   Począwszy od Technical Preview 1703, masz teraz obsługę w następujących scenariuszach Volume Purchase Program (VPP):

   - Urządzenie licencjonowania — aplikacje, które obsługują Licencjonowanie urządzenia i wdrożonych do kolekcji urządzeń teraz wymagać tylko jedną licencję na urządzenie.  Wcześniej można było korzystać z licencji dla każdego użytkownika na urządzeniu. Aby uzyskać więcej informacji, zobacz [wdrażać aplikacje dla systemu iOS zakupionymi zbiorczo w kolekcjach urządzeń](/sccm/core/get-started/capabilities-in-technical-preview-1703#deploy-volume-purchased-ios-apps-to-device-collections).
   - Użycie wielu tokenów VPP do dzierżawy hybrydowego jednego z oba tokeny używane do zarządzania aplikacje programu VPP.
   - Użycie tokenów VPP education możliwość rozróżnienia tokeny działalności biznesowej i education.

### <a name="new-in-configuration-manager-current-branch"></a>Nowe w programie Configuration Manager (wersji current branch)

Następujące funkcje, które były wcześniej dostępne w wersjach Configuration Manager Technical Preview są teraz dostępne w przypadku hybrydowych wdrożeń z usługi Intune i program Configuration Manager (wersji current branch) wersja 1702.

- [Android obsługę pracy](/sccm/core/plan-design/changes/whats-new-in-version-1702##android-for-work-support)
- [Ustawienia zgodności niezgodnych aplikacji](/sccm/core/plan-design/changes/whats-new-in-version-1702#conditional-access-device-compliance-policy-improvements)
- [Utworzenie certyfikatu PFX i dystrybucji i obsługa szyfrowania S/MIME](/sccm/core/plan-design/changes/whats-new-in-version-1702#improvements-to-certificate-profiles)
- [Wersje systemów android i iOS nie są już targetable w kreatorach tworzenia dla hybrydowego zarządzania urządzeniami Przenośnymi](/sccm/core/plan-design/changes/whats-new-in-version-1702#android-and-ios-versions-are-no-longer-targetable-in-creation-wizards-for-hybrid-mdm)

Następujące funkcje dodatkowe hybrydowego znajdują się również w wersji 1702 programu Configuration Manager (wersji current branch):

- **Ulepszona obsługa dla Apple Volume Purchase Program (VPP)**

  - Teraz można wdrożyć licencjonowane aplikacje na urządzeniach, jak i użytkowników. W zależności od aplikacji możliwość obsługi urządzenia licencjonowania odpowiednią licencję jest określona, wdrażając go w następujący sposób:

    | Wersja programu Configuration Manager | Aplikacja obsługuje licencjonowania urządzeń? | Typ kolekcji wdrażania | Oświadczeniem licencji |
    |-|-|-|-|
    |Wcześniejsza niż 1702|Tak|Użytkownik|Licencja użytkownika|
    |Wcześniejsza niż 1702|Nie|Użytkownik|Licencja użytkownika|
    |Wcześniejsza niż 1702|Tak|Urządzenie|Licencja użytkownika|
    |Wcześniejsza niż 1702|Nie|Urządzenie|Licencja użytkownika|
    |1702 i nowsze|Tak|Użytkownik|Licencja użytkownika|
    |1702 i nowsze|Nie|Użytkownik|Licencja użytkownika|
    |1702 i nowsze|Tak|Urządzenie|Licencja urządzenia|
    |1702 i nowsze|Nie|Urządzenie|Licencja użytkownika|

  - Teraz można również wdrożyć i śledzenie aplikacji, które zostały zakupione od iOS Volume Purchase Program dla instytucji edukacyjnych.

  - Teraz można skojarzyć wiele tokenów program zakupów zbiorczych firmy Apple z programem Configuration Manager.

  Aby uzyskać więcej informacji o aplikacji dla systemu iOS zakupionymi zbiorczo, zobacz [Zarządzanie aplikacjami zakupionymi zbiorczo systemu iOS](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps).

- **Obsługa aplikacji biznesowych — w Sklepie Windows dla firm**

  Mogą teraz synchronizować niestandardowych aplikacji biznesowych — w Sklepie Windows dla firm.

- **Nowe przed zagrożeniami Mobile narzędzia do monitorowania**

    Masz teraz nowe sposoby monitorowania stanu zgodności z dostawcą usług Mobile przed zagrożeniami.

    Aby uzyskać więcej informacji, zobacz [sposobu monitorowania zgodności przed zagrożeniami Mobile](/sccm/mdm/deploy-use/monitor-mobile-threat-defense-compliance).

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


## <a name="notices"></a>Powiadomienia

### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode"></a>Firmy, Portal dla Windows 8.1 i Windows Phone 8.1 przechodzenia do trybu utrzymywanie 
<!--1428681-->
*6 października 2017 r.*   
 
Począwszy od października 2017 przeniesie do utrzymywanie tryb aplikacji Portal firmy dla Windows 8.1 i Windows Phone 8.1. Oznacza to, że aplikacje i istniejące scenariusze, takie jak rejestracji i zgodności, będą nadal obsługiwane dla tych platform. Te aplikacje będą nadal być dostępny do pobrania za pośrednictwem istniejącej wersji kanałów, takich jak Microsoft Store. 

Raz w utrzymywanie tryb, te aplikacje będą odbierać tylko krytyczne aktualizacje zabezpieczeń. Nie będzie żadnych dodatkowych aktualizacji lub funkcje wydane dla tych aplikacji. Nowe funkcje zaleca się, zaktualizuj urządzenia do systemu Windows 10 lub Windows 10 Mobile. 

### <a name="end-of-support-for-ios-80"></a>Wsparcie dla systemu iOS 8.0 
<!---1164477--->
Zarządzane aplikacje i aplikacji Portal firmy dla systemu iOS będą musieli iOS 9.0 lub nowszej, dostęp do zasobów firmy. Urządzenia, które nie są aktualizowane września nie będą już mogli uzyskać dostęp do portalu firmy lub aplikacji. 

### <a name="platform-support-reminder-windows-phone-81-mainstream-support-ended-july-11-2017"></a>Przypomnienie pomocy technicznej platformy: Windows Phone 8.1 dostępne podstawowe wsparcie zakończył 11 lipca 2017 r.
<!-- 1327781 -->
*11 lipca 2017 r.*

Platformy Windows Phone 8.1 osiągnął koniec dostępne podstawowe wsparcie. Obsługa komputerów Windows 8.1 nie jest w pełni funkcjonalne.

Nie ma żadnego wpływu natychmiastowego dla wszystkich urządzeń Windows Phone 8.1, który jest zarządzany przez usługę Intune, łącznie z tymi zarejestrowane w hybrydowego zarządzania urządzeniami przenośnymi. Urządzenia, które są zarejestrowane, będą nadal działać, a wszystkie zasady, konfiguracji i aplikacje będą nadal działać zgodnie z oczekiwaniami. Należy pamiętać, nie ma żadnych ulepszenia przeznaczone dla platformy Windows Phone 8.1 w usłudze Intune i dla aplikacji Portal firmy systemu Windows Phone 8.1.

Zaleca się uaktualnienie kwalifikujących się urządzeń Windows Phone 8.1 do systemu Windows 10 Mobile z najwcześniej.  

### <a name="end-of-support-for-android-43-and-lower"></a>Wsparcie dla systemu Android 4.3 i dolne
<!---1171127--->
*Lipiec, 6, 2017*

Zarządzane aplikacje i aplikacji Portal firmy dla systemu Android wymaga Android 4.4 lub wyższej dostępu do zasobów firmy. Urządzenia, które nie są aktualizowane na początku października nie będą już mogli uzyskać dostęp do portalu firmy lub aplikacji. Grudnia wszystkich zarejestrowanych urządzeń będzie życie wycofane grudnia, co spowoduje utratę dostępu do zasobów firmy. Jeśli używane są zasady ochrony aplikacji bez zarządzania urządzeniami Przenośnymi, aplikacje nie będą otrzymywać aktualizacje i jakości ich obsługi zmniejszą się wraz z upływem czasu.


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


### <a name="see-also"></a>Zobacz też

- [Poza hybrydowej funkcji MDM](whats-new-hybrid-archive.md)
- [Nowości w oprogramowaniu MDM w programie System Center 2012 Configuration Manager](https://technet.microsoft.com/library/mt445560.aspx)
