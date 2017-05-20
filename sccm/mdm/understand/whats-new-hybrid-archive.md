---
title: Co to jest nowe hybrydowe MDM archiwum | Dokumentacja firmy Microsoft
description: "Archiwum poprzednich funkcje zarządzania urządzeniami przenośnymi dostępne dla wdrożenia hybrydowego z programu System Center Configuration Manager i usługi Intune."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4c27b161-9eb7-4cdd-b469-d8eb27e71aea
author: Mtillman
ms.author: mtillman
manager: angrobe
ROBOTS: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 623a30eddebcae196ff345ef5debc8183ecd6ae6
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="past-hybrid-features-with-system-center-configuration-manager-and-microsoft-intune"></a>Hybrydowe wcześniejszej funkcji za pomocą programu System Center Configuration Manager i Microsoft Intune

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Ten artykuł zawiera szczegółowe informacje dotyczące ostatnich urządzenia przenośnego, funkcji zarządzania (MDM) dostępnych dla wdrożenia hybrydowego za pomocą programu System Center Configuration Manager i Microsoft Intune.  

##  <a name="compatibility-with-configuration-manager-versions"></a>Zgodność z wersjami programu Configuration Manager  

 Każda sekcja w tym artykule przedstawiono hybrydowe funkcji w ramach różnych kategorii 3. Można określić zgodność funkcji w każdej kategorii z różnymi wersjami programu Configuration Manager, użyj poniższych wskazówek:  

|Kategorie funkcji|
|-|  
|**Nowością w programie Microsoft Intune** -ogólnie rzecz biorąc, wszystkie funkcje wymienione w tej kategorii powinien współpracować z wszystkie wersje programu Configuration Manager, łącznie z wersjami programu System Center 2012 R2 Configuration Manager, ponieważ tylko te funkcje wymagają usługi Intune i nie wymagają dodatkowych funkcji w programie Configuration Manager.<br /><br /> **Nowością w programie Configuration Manager Technical Preview** — wszystkie funkcje wymienione w tej kategorii, działają tylko w określonej wersji Technical Preview. Aby wypróbować te funkcje, należy zainstalować określony w opisie funkcji wersji Technical Preview. Aby uzyskać więcej informacji, zobacz [Technical Preview dla programu System Center Configuration Manager](../../core/get-started/technical-preview.md).<br /><br /> **Nowe w programie Configuration Manager (bieżącej gałęzi)** — wszystkie funkcje wymienione w tej kategorii działa tylko z określonej wersji programu Configuration Manager (bieżącej gałęzi), takich jak wersja 1511 lub 1602. Jeśli używasz starszej wersji programu Configuration Manager wdrożenie hybrydowe, należy uaktualnić do wersji Configuration Manager (bieżącej gałęzi) określona w opisie funkcji. Aby uzyskać więcej informacji, zobacz [uaktualnienia programu System Center Configuration Manager](../../core/servers/deploy/install/upgrade-to-configuration-manager.md).|  

## <a name="new-hybrid-features-in-october-2016"></a>Nowe funkcje hybrydowe października 2016

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune

Następujące funkcje Intune wprowadzone w programie 2016 października działają we wdrożeniach hybrydowego.

- **Dostęp warunkowy do zarządzania aplikacjami mobilnymi**

  Można ograniczyć dostęp do usługi Exchange Online, dzięki czemu dostęp pochodzą tylko z aplikacji, które obsługują zasad zarządzania aplikacjami mobilnymi usługi Intune, takie jak program Outlook. [Ta nowa funkcja](/intune/deploy-use/allow-policy-managed-apps-access-to-o365) pary dokładnie z zasadami zarządzania (MAM) aplikacji mobilnej Intune jako możesz zablokować dostęp do klientów poczty wbudowanych lub inne aplikacje, które nie zostały skonfigurowane przy użyciu zasad zarządzania aplikacjami Mobilnymi usługi Intune. Dzięki temu użytkownicy uzyskują dostęp do danych w organizacji za pomocą aplikacji, które mogą być chronione przy użyciu usługi Intune MAM. Można rozpocząć w zarządzania aplikacjami mobilnymi usługi Intune w portalu Azure. Poszukaj przez dodanie nowej sekcji dostępu warunkowego w bloku "Ustawienia".

-    **Narzędzia opakowującego aplikacji usługi Intune dla systemu Android**

  Można włączyć swoje aplikacje do użycia zasad zarządzania (MAM) aplikacjami mobilnymi usługi Intune za pomocą narzędzia opakowującego aplikacje usługi Intune.

- **Android Samsung KNOX Standard zgodność z usługą Intune**

  Niektóre modele phone Samsung Galaxy Ace nie zarządzane przez usługę Intune jako urządzenia Samsung KNOX Standard. Podczas rejestrowania urządzeń w usłudze Intune, zamiast tego będą one zarządzane jako standardowa urządzenia z systemem Android.

  Numery modeli, których to dotyczy, są:

  - SM G313HU
  -    SM G313HY
  -    SM G313M
  -    SM G313MY
  -    SM G313U

  Użytkownicy końcowi muszą podejmować żadnych dodatkowych czynności. Aby uzyskać więcej informacji odwiedź witrynę Samsung KNOX.

### <a name="new-in-configuration-manager-technical-preview-1610"></a>Nowością w programie Configuration Manager Technical Preview 1610

Wprowadzono następujące nowe funkcje hybrydowe w 2016 października dla konfiguracji Menedżera Technical Preview 1610.

- **Żądanie synchronizacji zasad z konsoli administracyjnej**

  W przypadku żądania synchronizacji zasad na zarejestrowanych urządzeń przenośnych z konsoli programu Configuration Manager, bez konieczności wprowadzania żądania synchronizacji w aplikacji Portal firmy na urządzeniu. Jest to nowa akcja o nazwie **Wyślij żądanie synchronizacji** w menu Akcje urządzenia zdalnego, który pojawia się na Wstążce po wybraniu urządzenia przenośnego w węźle urządzenia.

- **Ustawienia konfiguracji usługi Windows Defender**

  Na komputerach zarejestrowanych w usłudze Intune systemu Windows 10 za pomocą elementów konfiguracji w konsoli programu Configuration Manager można teraz skonfigurować ustawienia klienta usługi Windows Defender. Istnieje nowe ustawienie grupę o nazwie **programu Windows Defender** w Kreatorze elementu konfiguracji. Należy zauważyć, że jest to obsługiwane tylko w Windows 10 w wersji 1511 i powyżej.


### <a name="new-in-configuration-manager-current-branch"></a>Nowe w programie Configuration Manager (bieżącej gałęzi)

Żadne nowe funkcje hybrydowe zostały wprowadzone w sierpniu 2016 dla programu Configuration Manager (bieżącej gałęzi).

## <a name="new-hybrid-features-in-september-2016"></a>Nowe funkcje hybrydowe września 2016

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune

Następujące funkcje Intune wprowadzone w programie 2016 września działają we wdrożeniach hybrydowego.

- **Dodanie "Powiadomień" do portalu firmy dla systemu Android**

  Nowa ikona powiadomienia dodano do portalu firmy dla systemu Android na stronie głównej. Naciskając ikonę dostęp do strony powiadomienia, który pokazuje wszystkie elementy, które wymagają uwagi w aplikacji Portal firmy, takich jak urządzenia niezgodności, aktualizacja rejestracji i aktywacja rejestracji użytkownikom końcowym. Aplikacja Portal firmy dla systemu iOS ma już to zgłaszać powiadomienia. Nowe środki strony powiadomienia o tego użytkownika nie będą widoczne strony Konfigurowanie dostępu do zasobów firmy każdorazowo uruchomić lub wznowić portalu firmy, tak długo, jak długo urządzenie zostało już zarejestrowane. W przypadku utworzenia własnego wskazówki przez użytkownika końcowego, można zaktualizować dokumentacji w celu odzwierciedlenia tej zmiany. Znajdowanie zaktualizowanej zrzuty ekranu [tutaj](https://aka.ms/androidcpupdate).

- **Zmiany w obsługę aplikacji Portal firmy systemu iOS**

  Wszyscy użytkownicy aplikacji Portal firmy Microsoft Intune dla systemu iOS teraz są wymagane do jego najnowszej wersji. Nowi użytkownicy będą mogli pobrać najnowszą wersję, a bieżąca liczba użytkowników wymagane przez aktualizację do niego. Najnowsza wersja wymaga iOS 8,0 lub nowszy, dlatego urządzeń starszymi wersjami systemu iOS nie można korzystać z portalu firmy lub zarejestrować aż zaktualizować swoje urządzenie do iOS 8,0 lub nowszy, a następnie zaktualizuj aplikacji Portal firmy do najnowszej wersji. Zarejestrowane urządzenia z wersjami poniżej iOS 8.0 będzie zarządzania i wyświetlane w konsoli administracyjnej usługi Intune.

- **Przycisk opinię dodany do aplikacji Portal firmy systemu Windows Phone 8.1**

  Aplikacja Portal firmy systemu Windows Phone 8.1 umożliwia użytkownikom końcowym Prześlij opinię o aplikacji przy użyciu nowy przycisk "Wyślij opinię". Aby znaleźć przycisku, wybierz menu "trzy kropki" w prawej dolnej części ekranu aplikacji Portal firmy użytkowników, a następnie wybierz **wysłać opinię**. Zbierane, anonimowe opinie pomogą firmie Microsoft w ulepszaniu obsługi aplikacji Portal firmy dla użytkowników.

### <a name="new-in-configuration-manager-technical-preview-1609"></a>Nowością w programie Configuration Manager Technical Preview 1609

Wprowadzono następujące nowe funkcje hybrydowe w 2016 września dla konfiguracji Menedżera Technical Preview 1609.

- **Dodatkowe ustawienia i udoskonalone środowisko dla ustawienia elementu konfiguracji**

  Dodano nowe ustawienia dla systemu Android, iOS i Windows, a tylko ustawienia, które są stosowane do wybranych na stronie platformy obsługiwane platformy są wyświetlane w kreatorze. Aby uzyskać więcej informacji, zobacz [nowe ustawienia zgodności dla elementów konfiguracji w programie TP 1609](/sccm/core/get-started/capabilities-in-technical-preview-1609#new-compliance-settings-for-configuration-items).

- **Dodatkowe ustawienia profilów DEP**

  TouchID, ApplePay i powiększenie zostały dodane jako ustawienia można skonfigurować w programie DEP profile dla urządzeń z systemem iOS.

- **Płatnej aplikacji w Sklepie Windows dla firm**

  Teraz można dodać zarówno płatnych i bezpłatne aplikacje do Sklepu Windows dla firm i wdrożyć je dla użytkowników w organizacji. Aby uzyskać więcej informacji, zobacz [rozszerzeń do Sklepu Windows dla firm w TP 1609](/sccm/core/get-started/capabilities-in-technical-preview-1609#enhancements-to-windows-store-for-business-integration-with-configuration-manager).

- **Typy połączeń macierzystego dla profilów sieci VPN systemu Windows 10**

  Można teraz utworzyć profile sieci VPN systemu Windows 10 dla zarządzania urządzeniami Przenośnymi z Automatic firmy Microsoft, IKEv2 i PPTP typy połączeń w konsoli programu Configuration Manager bez użycia OMA-URI.

- **Wykresy zgodności Intune**

  Można uzyskać szybki widok urządzenia ogólnej zgodności i pierwszych przyczyny braku zgodności przy użyciu nowych wykresów w obszarze roboczym monitorowanie. Aby uzyskać więcej informacji, zobacz [wykresów zgodności Intune w TP 1609](/sccm/core/get-started/capabilities-in-technical-preview-1609#intune-compliance-charts).

### <a name="new-in-configuration-manager-current-branch"></a>Nowe w programie Configuration Manager (bieżącej gałęzi)

Następujące nowa funkcja wprowadzona w 2016 września dostępnej dla wdrożenia hybrydowego z Microsoft Intune i 1606 wersji programu Configuration Manager (bieżącej gałęzi).

- **Obsługa iOS 10**

  Jeśli profile lub elementy konfiguracji przeznaczone do wszystkich platform iOS, będą one również przypisany do iOS 10. Opublikowano zostały także aktualizacji 1606 wersji programu Configuration Manager pozwalająca na profile docelowy i elementy konfiguracji do poszczególnych iOS platformy, takie jak iOS 10. Można zainstalować aktualizację z konsoli administratora programu Configuration Manager pod adresem **Administracja > Przegląd > usług w chmurze > aktualizacji i obsługi**. Można znaleźć więcej informacji na temat aktualizacji w [http://support.microsoft.com/kb/3192616](http://support.microsoft.com/kb/3192616).

## <a name="new-hybrid-features-in-august-2016"></a>Nowe funkcje hybrydowe w sierpniu 2016

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune

Następujące funkcje Intune wprowadzono w sierpniu 2016 działają we wdrożeniach hybrydowego.

- **Obsługa systemu android 7 w aplikacji Portal firmy**

  Aplikacja Portal firmy usługi Intune dla systemu Android zapewnia obsługę "day 0" najbliższego Android 7.0 system operacyjny dla urządzeń przenośnych.

- **Usunięcie kodu dostępu zdalnego Google zresetować możliwości na urządzeniach z systemem Android 7.0**

  Google usuwa możliwość zdalnie zresetować kod dostępu urządzenia Android 7.0 administratorzy IT i użytkowników końcowych. Wcześniej Administratorzy IT mogą zdalnie zresetować kod dostępu użytkownika, a użytkownicy końcowi mogą resetować ich kody dostępu z witryny sieci Web portalu firmy.

- **Zasady dozwolonych i zablokowanych aplikacji dla urządzeń Samsung KNOX Standard**

  Można teraz skonfigurować zasady niestandardowe dla urządzeń Samsung KNOX Standard umożliwiający tworzenie jedną z następujących czynności:

  - Lista aplikacji, które są zablokowane na uruchamianie na urządzeniu. Nawet po zainstalowaniu aplikacji zdefiniowane na liście zablokowanych nie można uaktywnić na urządzeniu.
  - Lista aplikacji, które mogą użytkownicy urządzeń do zainstalowania ze sklepu Google Play. Żadnych innych aplikacji można zainstalować ze sklepu.

  Te ustawienia można używać tylko przez urządzenia z systemem Samsung KNOX Standard. Aby uzyskać szczegółowe informacje, zobacz [użycie zasad niestandardowych do dozwolonych i zablokowanych aplikacji dla urządzeń Samsung KNOX Standard](/intune/deploy-use/custom-policy-to-allow-and-block-samsung-knox-apps).

- **Link opinii z portalu firmy do firmy Microsoft**

   Witryna sieci Web portalu firmy umożliwia użytkownikom końcowym wybierz nowe łącze "Opinii" na dole strony, aby wysłać opinię do firmy Microsoft o ich obsługi w witrynie. Opinii zebranych, anonimowy może pomóc firmie Microsoft w ulepszaniu środowiska witryny sieci Web portalu firmy dla użytkowników.

- **Wersja przeglądarki zarządzane minimalne iOS dodano 8.0**

  Aplikacja Microsoft Intune Managed Browser dla systemu iOS ma została zaktualizowana do obsługi urządzeń z systemem iOS 8,0 lub nowszy. Gdy urządzenia z systemem iOS 7.1 nadal mogą korzystać z istniejących aplikacji Managed Browser, zachęca użytkowników do aktualizacji do iOS 8,0 lub nowszy, aby uzyskać dostęp do i w pełni korzystać z nowych funkcji Managed Browser.

### <a name="new-in-configuration-manager-technical-preview"></a>Nowość w programie Configuration Manager Technical Preview

Żadne nowe funkcje hybrydowe wprowadzono w sierpniu 2016 Configuration Manager Technical Preview.

### <a name="new-in-configuration-manager-current-branch"></a>Nowe w programie Configuration Manager (bieżącej gałęzi)

Żadne nowe funkcje hybrydowe zostały wprowadzone w sierpniu 2016 dla programu Configuration Manager (bieżącej gałęzi).

## <a name="new-hybrid-features-in-july-2016"></a>Nowe funkcje hybrydowe w lipcu 2016

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune

Następujące funkcje Intune wprowadzone w programie 2016 lipca działają we wdrożeniach hybrydowego.

- **Zestaw SDK platformy Xamarin dla aplikacji usługi Intune jest dostępna**

  Składnik Xamarin zestawu SDK aplikacji Intune umożliwia włączenie funkcji zarządzania aplikacji mobilnej Intune przenośnych iOS i Android aplikacji skompilowanej za pomocą platformy Xamarin. Można znaleźć składnika w [magazyn Xamarin](https://components.xamarin.com/view/Microsoft.Intune.MAM) lub na [strony Microsoft Intune Github](https://github.com/msintuneappsdk).

- **Ulepszone przez użytkownika końcowego podczas rejestrowania urządzenia z systemem Windows**

  Korzystając z dostępu warunkowego, kroki rejestracji dla Windows 8.1, Windows 10 Desktop i Windows 10 Mobile mają wyjaśnienia w witrynie sieci Web portalu firmy. Użytkownicy będą widzieć teraz oddzielnych **rejestracji urządzeń** i **Dołącz do miejsca pracy** kroki, co ułatwi ich zobaczyć stan swoich urządzeń i ukończyć proces w przypadku wystąpienia awarii Dołącz do miejsca pracy (WPJ). Oddzielne kroki oczekuje się, aby uprościć proces rozwiązywania dla administratorów IT. Wcześniej gdy użytkownicy końcowi próbował zarejestrować i wszystkie kroki rejestracji zakończyło się pomyślnie, z wyjątkiem WPJ, zarejestrowane urządzenie nie pojawiały się na liście urządzeń dla użytkowników zidentyfikować, powodując pomyłek dla użytkowników.

 - **Pełne czyszczenie danych, które są teraz dostępne dla urządzeń z systemem Windows 10**

    Komputery z systemem Windows 10 i komputery przenośne zarejestrowane jako urządzenia przenośne można wyczyszczone zresetowanie urządzenia do ustawień fabrycznych. Aby uzyskać więcej informacji, zobacz [jak chronić swoje urządzenia w wymazywania](/sccm/mdm/deploy-use/wipe-lock-reset).

- **Zmiany w menedżerów rejestracji urządzeń kont w aplikacji Portal firmy systemu iOS**

  Aby zwiększyć wydajność i skalowanie, Intune Wyświetla wszystkie urządzenia menedżerów rejestracji urządzeń (DEM) nie jest już w okienku Moje urządzenia w aplikacji Portal firmy systemu iOS. Tylko urządzenia lokalnego uruchomiona aplikacja zostanie wyświetlony, tylko wtedy, gdy jest zarejestrowany za pomocą aplikacji Portal firmy.

  Użytkownik DEM może wykonywać działania na urządzeniu lokalnym, ale zdalnego zarządzania inne zarejestrowane urządzenia można wykonać tylko z konsoli administracyjnej usługi Intune. Ponadto usługa Intune jest zaniechanie korzystania korzystania z kont DEM z programu rejestracji urządzeń firmy Apple lub narzędzia Apple Configurator. Obie metody rejestracji już obsługę rejestracji bez użytkowników urządzeń z systemem iOS udostępnionego.

  DEM konta należy używać tylko, gdy użytkownik bez rejestracji dla urządzenia udostępnione są niedostępne. Aby uzyskać więcej informacji, zobacz [rejestrowanie firmowych urządzeń za pomocą Menedżera rejestracji urządzeń w programie Microsoft Intune](../deploy-use/enroll-devices-with-device-enrollment-manager.md).

- **Zmiany w aplikacji portalu firmy Android**

  Jeśli użytkownicy końcowi Android komunikat o błędzie stwierdzający urządzeniu brakuje wymaganego certyfikatu, ich naciśnij przycisk "Jak rozwiązać ten problem" w celu poznania procedury dotyczące instalowania certyfikatu Brak. Jeżeli użytkownicy, wykonaj kroki wyświetlone dodatkowe "brakuje certyfikatu" komunikat o błędzie zostanie wyświetlony monit o ich administratora IT i dostarczenie tego łącza, która zawiera kroki, które Administratorzy IT mogą używać, aby rozwiązać problem z certyfikatem.

- **Ograniczenia instalacji aplikacji ładowana do zarejestrowanych urządzeń z systemem Android**

  Urządzenia z systemem android nie mogą już instalować aplikacji za pośrednictwem witryny internetowej portalu firmy, chyba że urządzenia zostały zarejestrowane w usłudze Intune przy użyciu aplikacji Portal firmy usługi Intune dla systemu Android.


### <a name="new-in-configuration-manager-technical-preview"></a>Nowość w programie Configuration Manager Technical Preview

Żadne nowe funkcje hybrydowe wprowadzono w lipcu 2016 Configuration Manager Technical Preview.

### <a name="new-in-configuration-manager-current-branch"></a>Nowe w programie Configuration Manager (bieżącej gałęzi)

Następujące funkcje, które wcześniej były dostępne w wersji Technical Preview programu Configuration Manager są teraz dostępne we wdrożeniach hybrydowych za pomocą usługi Intune i program Configuration Manager (bieżącej gałęzi) wersja 1606.

* Wyszukiwanie, zarządzania i dystrybucji Sklepu Windows dla aplikacji biznesowych dla urządzeń z systemem Windows 10 z konsoli programu Configuration Manager ([1604](#new-in-1604-technical-preview))
*     Ustawienie SmartLock dla urządzeń z systemem Android ([1604](#new-in-1604-technical-preview))
*    Urządzenia sieci VPN w systemie Windows 10 wyzwalane aplikacji ([1605](#new-in-1605-technical-preview))
*    Nowe środowisko na urządzeniu zdalnym działania ([1605](#new-in-1605-technical-preview))
*    Sklep Windows dla aplikacji biznesowych ([1605](#new-in-1605-technical-preview))
*    Ulepszenia ogólne zakupione woluminu aplikacji ([1605](#new-in-1605-technical-preview))
*    Ochrona informacji systemu Windows (PWT) ([1605](#new-in-1605-technical-preview))
*    Wstępnie zadeklarować firmowych urządzeń za pomocą numeru seryjnego systemu iOS lub IMEI ([1605](#new-in-1605-technical-preview))
*    Automatycznie kategoryzowanie urządzenia do kolekcji ([1606](#new-in-1606-technical-preview))

Informacje o nowych funkcjach zobacz dokumentację dla określonej wersji Technical Preview.

## <a name="new-hybrid-features-in-june-2016"></a>Nowe funkcje hybrydowe czerwca 2016

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune
Następujące funkcje Intune wprowadzone w programie czerwca 2016 działają we wdrożeniach hybrydowego.

- **Kondycja usługi Intune** informacje o kondycji usługi dla usługi Intune został przeniesiony do lokalizacji centralnej z innymi usługami firmy Microsoft. Teraz znajdziesz tych informacji w portalu zarządzania usługi Office 365 w ramach usługi kondycji. Aby uzyskać więcej informacji, zobacz [wpis w blogu](https://blogs.technet.microsoft.com/enterprisemobility/2016/04/28/intune-service-health-is-now-available-in-the-office-365-portal/).

- **Wystąpić rozszerzone konfiguracji zasad danych systemu Windows 10 enterprise**

  Intune ma teraz udoskonalone środowisko do konfigurowania zasad ochrony informacji systemu Windows 10. Ulepszenia obejmują lepsze sposoby tworzenia reguł aplikacji, określ definicji granic sieci i inne ustawienia ochrony informacji systemu Windows. Aby dowiedzieć się więcej, zobacz [utworzyć zasady ochrony informacji systemu Windows (PWT) przy użyciu programu Microsoft Intune](https://technet.microsoft.com/itpro/windows/keep-secure/create-wip-policy-using-intune).

- **Zasady kontroli dostępu do sieci ISE Cisco dla usługi Intune**

  Klienci, którzy używać Cisco tożsamość usługi aparatu (ISE) 2.1, a także Microsoft Intune można ustawić ISE zasady kontroli dostępu do sieci. Za pomocą tych zasad, urządzenia, które należy połączyć się z siecią przy użyciu sieci Wi-Fi lub VPN musi spełniać następujące warunki przed uzyskaniem dostępu do:

  - Musi być zarządzane przez usługę Intune
  - Musi być zgodne z zasadami zgodności wdrożonej usługi Intune

  Użytkownicy końcowi z niezgodnymi urządzeniami i zostanie wyświetlony monit o zapisanie i rozwiązać wszystkie problemy zgodności w celu uzyskania dostępu.

- **Funkcja dostępu warunkowego dla przeglądarki**

  Można ustawić zasad dostępu warunkowego dla usługi Exchange Online i SharePoint Online, dzięki czemu są one dostępne tylko z obsługiwanych przeglądarek na zarządzane i zgodne iOS i android. Aby zarejestrować urządzenie w usłudze Intune również odnośnie Rozwiąż wszelkie problemy niezgodności one aby można było zakończyć logowanie użytkowników końcowych, którzy spróbuj zalogować się do programu Outlook Web Access (OWA) oraz witryn programu SharePoint z systemem iOS i android pojawi się monit. Aby uzyskać więcej informacji, zobacz artykuł

  * [Ogranicz dostęp do poczty e-mail do usługi Exchange Online i nowego programu Exchange Online w wersji dedykowanej za pomocą usługi Intune](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-exchange-online-with-microsoft-intune)
  * [Ograniczanie dostępu do usługi SharePoint Online usłudze Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-sharepoint-online-with-microsoft-intune)

- **Dynamics CRM Online obsługuje dostępu warunkowego**

  Można ustawić zasad dostępu warunkowego dla programu Dynamics CRM Online, dzięki czemu mają dostęp tylko przez urządzenia Android i iOS zarządzane i zgodne. Aby zarejestrować w usłudze Intune, a także rozwiązać wszystkie problemy niezgodności logowanie aby można było zakończyć użytkowników końcowych, którzy spróbuj zalogować się do aplikacji mobilnej Dynamics CRM na iOS i Android pojawi się monit. Aby uzyskać więcej informacji, zobacz [ograniczyć dostęp do programu Dynamics CRM Online usłudze Microsoft Intune](https://docs.microsoft.com/intune/deploy-use/restrict-access-to-dynamics-crm-online-with-microsoft-intune).

- **Aktualizacje aplikacji portalu firmy Android**

  Intune ma teraz następujące nowych zasad dotyczących użytkowników portalu firmy Android:   

  Zasady  |Wpływa na użytkowników  
  ---------|---------
  Wymagaj, aby urządzenia nie zezwalaj na instalację aplikacji z nieznanego źródła (Android 4.0 +)     |  Użytkownicy końcowi Android 4.0 lub nowszym urządzeniom zostanie wyświetlony komunikat, "Instalacji z nieznanego źródła musi być wyłączony." Użytkownicy będą musieli przejdź do **Ustawienia > Zabezpieczenia** na ich urządzeniach i Wyłącz **nieznane źródła**. Łącze w wiadomości zgodności umożliwia użytkownikom uzyskać więcej informacji na temat wiadomość i dlaczego są są wymagane, aby wyłączyć ustawienie.
  Wymagaj, aby urządzenia nie zezwalaj na instalację aplikacji z nieznanego źródła (Android 4.0 +)  |    Użytkownicy końcowi Android 4.0 lub nowszym urządzeniom zostanie wyświetlony komunikat, "Skanowania urządzeń na zagrożenia bezpieczeństwa." Użytkownicy będą musieli przejdź do **Ustawienia > Google > zabezpieczeń** na ich urządzeniach i Włącz **skanowania urządzeń na zagrożenia bezpieczeństwa**. Łącze w wiadomości zgodności umożliwia użytkownikom uzyskać więcej informacji na temat wiadomości i dlaczego są są wymagane do Włącz to ustawienie.     
  Wymagają, że debugowanie USB jest wyłączona (Android 4.2 +)  | Użytkownikom końcowym z systemu Android 4.2 lub nowszy urządzenia zostanie wyświetlony komunikat, "debugowanie USB musi być wyłączony." Użytkownicy będą musieli przejdź do **Ustawienia > Opcje dla deweloperów** na ich urządzeniach i Wyłącz **debugowanie USB**. Łącze w wiadomości zgodności umożliwia użytkownikom uzyskać więcej informacji na temat wiadomość i dlaczego są są wymagane, aby wyłączyć ustawienie.
  Poziom poprawki minimalnych zabezpieczeń systemu Android (Android w wersji 6.0 +)  | Użytkownicy końcowi z systemem Android w wersji 6.0 lub urządzenia z nowszymi wersjami zostanie wyświetlony komunikat, "to urządzenie nie spełnia poziom poprawki minimalne Android zabezpieczeń". Użytkownicy będą musieli zainstalować poprawkę zabezpieczeń jest wymagana. Łącze w wiadomości zgodności pozwala uzyskać informacje o sposobach instalowania poprawki zabezpieczeń i poprawki zabezpieczeń, które są aktualnie zainstalowany.

- **Aktualizacje aplikacji portalu firmy iOS**

  * Podczas instalowania aplikacji biznesowych o użytkowników końcowych, teraz zobaczą wystąpić instalacja aplikacji została poprawiona. Jeśli instalacja aplikacji jest zbyt długo, użytkownicy ręcznie zsynchronizować swoje urządzenie, aby wymusić procesu synchronizacji, aby wznowić. Aby zapoznać się z instrukcjami przez użytkownika końcowego, zobacz ręcznie synchronizacji urządzenia z systemem iOS.
  * Zaktualizowano aplikacji Portal firmy Microsoft Intune dla systemu iOS do obsługi systemu iOS w wersji 8.0 i nowszych. Ta aktualizacja oznacza, że użytkownicy końcowi mogą zainstalować aplikację Portal firmy i rejestrować w usłudze Intune nowe urządzenia tylko wtedy, gdy urządzenie ma zainstalowany system iOS w wersji 8.0 lub nowszy. Użytkownicy, którzy mają już zarejestrowane urządzenia z nieobsługiwaną wersją systemu IOS można nadal używać aplikacji Portal firmy, która znajduje się na urządzeniu.


### <a name="new-in-1606-technical-preview"></a>Nowość w wersji 1606 Technical Preview
Następujące nowe funkcje wprowadzone w programie czerwca 2016 są dostępne we wdrożeniach hybrydowych z usługą Intune i techniczne 1606 Podgląd Configuration Manager.

- **Automatycznie kategoryzowanie urządzenia do kolekcji**

  Możesz utworzyć kategorie urządzeń, które mogą być używane do automatycznego umieszczania urządzeń w kolekcji urządzeń, podczas korzystania z programu Configuration Manager za pomocą usługi Intune. Następnie użytkownicy muszą wybrać kategorię urządzenia podczas ich zarejestrować urządzenia w usłudze Intune. Ponadto można zmienić kategorię urządzenie z konsoli programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [automatycznie kategoryzowanie urządzenia do kolekcji](/sccm/core/get-started/capabilities-in-technical-preview-1606#dmp_category) w [możliwości 1606 Technical Preview dla programu System Center Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1606).

  > [!IMPORTANT]
  > Ta funkcja działa z wersji czerwca 2016 programu Microsoft Intune. Upewnij się, że masz zostały zaktualizowane do tej wersji przed podjęciem próby wykonania tych procedur.

### <a name="new-in-configuration-manager-current-branch"></a>Nowe w programie Configuration Manager (bieżącej gałęzi)
Żadne nowe funkcje hybrydowe zostały wprowadzone w czerwca 2016 dla programu Configuration Manager (bieżącej gałęzi).

##  <a name="new-hybrid-features-in-may-2016"></a>Nowe funkcje hybrydowe w maju 2016  

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune  
 Następujące funkcje Intune wprowadzone w programie 2016 może pracować w wdrożenia hybrydowego.

- **MAM SDK: Konfiguracja długość numeru PIN pomocy technicznej**

  Obecnie można określić długość numeru PIN dla aplikacji MAM podobnie jak numer PIN urządzenia. Wymaga to użytkowników końcowych do wykonania nowego ograniczenia ustawione. Ekran numeru PIN jest modyfikowany nieco konto dłużej danych wejściowych. Aby uzyskać szczegółowe informacje, zobacz [MAM ustawienia zasad dla systemu Android](https://docs.microsoft.com/intune/deploy-use/android-mam-policy-settings), i [MAM ustawienia zasad dla systemu iOS](https://docs.microsoft.com/intune/deploy-use/ios-mam-policy-settings).  

- **Skype dla firmy dla systemu iOS i Android**

  Teraz można wskazać Skype dla firm z [MAM bez zasad rejestracji](https://docs.microsoft.com/intune/deploy-use/get-ready-to-configure-mobile-app-management-policies-with-microsoft-intune). Gdy użytkownicy logują się, zostaną zastosowane zasady zarządzania aplikacjami Mobilnymi.  

- **Nowe aplikacje można zarządzać za pomocą zasad zarządzania aplikacjami Mobilnymi**

  Aplikacje programu Microsoft Word, Excel i PowerPoint dla systemu Android teraz mogą być skojarzone z zasadami zarządzania aplikacjami Mobilnymi na urządzeniach, które nie są zarejestrowane w usłudze Intune. Aby uzyskać pełną listę obsługiwanych aplikacji, przejdź Galeria aplikacji mobilnej Microsoft Intune w [partnerów usługi Microsoft Intune aplikacji](https://www.microsoft.com/en-us/server-cloud/products/microsoft-intune/partners.aspx) strony.  

- **Aplikacja portalu firmy android: Powiadomienia toast użytkownika końcowego**

  Alert powiadomienia z aplikacji Portal firmy Android są wyświetlane, gdy użytkownicy końcowi rejestrowania lub Usuń swoje urządzenia z portalu firmy.  

- **Witryna sieci Web portalu firmy: Transparent identyfikacji urządzenia zapewni więcej informacji dla użytkowników końcowych**

  Użytkownicy końcowi mogą teraz łatwiej zidentyfikować urządzenia, dla którego wybranych podczas korzystania z witryny sieci Web portalu firmy. Jeśli wybrano nieprawidłowe urządzenie, mogą wybrać właściwe urządzenie naciskając **naciśnij tutaj** łącze na transparencie strony głównej.  


### <a name="new-in-1605-technical-preview"></a>Nowość w wersji 1605 Technical Preview  
 Następujące nowe funkcje wprowadzone w maju 2016 są dostępne we wdrożeniach hybrydowych z usługą Intune i techniczne 1605 Podgląd Configuration Manager. Te funkcje wymagają użycia konsoli programu Configuration Manager do konfigurowania i zarządzania nimi.  

- **Wyzwalane aplikacji urządzenia sieci VPN w systemie Windows 10**

  W przypadku urządzeń Windows 10 zarządzane przy użyciu programu Configuration Manager za pomocą usługi Intune można dodać listę aplikacji, które automatycznego otwierania połączenia VPN, który został skonfigurowany za pomocą konsoli administracyjnej programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [wyzwalane przez aplikację sieci VPN w systemie Windows 10 urządzeń](/sccm/core/get-started/capabilities-in-technical-preview-1605) w [możliwości 1605 Technical Preview dla programu System Center Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1605)  

- **Nowe środowisko dla akcji urządzenie zdalne**

  Udoskonalono obsługę wykonanie akcji urządzenia zdalnego z konsoli programu Configuration Manager.

  Typowe akcje, takie jak **wycofywania i czyszczenia**, **resetowania kodu dostępu**, **zdalnego blokowania**, i **obejścia blokady aktywacji** można znaleźć w **zdalnego akcji urządzenia** dostępne z menu **zasoby i zgodność** obszaru roboczego

  Aby uzyskać więcej informacji, zobacz [nowe środowisko na urządzeniu zdalnym działania](/sccm/core/get-started/capabilities-in-technical-preview-1605#new-experience-for-remote-device-actions) w [możliwości 1605 Technical Preview dla programu System Center Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1605).  

- **Sklep Windows dla aplikacji biznesowych**

  [Sklepu Windows dla firm](https://www.microsoft.com/en-us/business-store) pozwala znaleźć i zakupić aplikacji dla danej organizacji, pojedynczo lub w woluminie. Łącząc sklepu do programu Configuration Manager, zakupione woluminu aplikacji można zarządzać z konsoli programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [Sklep Windows dla aplikacji biznesowych](/sccm/core/get-started/capabilities-in-technical-preview-1605.md#windows-store-for-business-apps) w [możliwości 1605 Technical Preview dla programu System Center Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1605).  

- **Ulepszenia ogólne zakupione woluminu aplikacji**

  Zakupione woluminu aplikacji ze Sklepu Windows dla firm i iOS app store zostały skonsolidowane w jednym widoku **dla aplikacji do przechowywania informacji o licencji**. Ponadto udoskonalono taki sposób, w którym aplikacje dla systemu iOS kupionymi woluminu. Aby uzyskać więcej informacji, zobacz[ogólne ulepszenia dla aplikacji zakupione woluminu](/sccm/core/get-started/capabilities-in-technical-preview-1605.md#general-improvements-for-volume-purchased-apps) w [możliwości 1605 Technical Preview dla programu System Center Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1605).  

- **Wstępnie zadeklarować firmowych urządzeń o numerze seryjnym IMEI lub iOS**

  Można zidentyfikować firmowych urządzeń przez zaimportowanie numerów międzynarodowych stacji urządzeń przenośnych tożsamości (IMEI). Możesz przekazać plik wartości rozdzielanych przecinkami (.csv) zawierający numery IMEI urządzenia lub można ręcznie wprowadzić informacje o urządzeniu.  Można także zaimportować numerów seryjnych urządzeń z systemem iOS.  Aby uzyskać więcej informacji, zobacz [wstępnie zadeklarować firmowych urządzeń o numerze seryjnym IMEI lub iOS](../../core/get-started/capabilities-in-technical-preview-1605.md#BKMK_IMEI) w [możliwości 1605 Technical Preview dla programu System Center Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1605).  

- **Ochrona informacji systemu Windows (PWT)**

  Można utworzyć elementy konfiguracji, które umożliwiają wdrażanie z zasadami ochrony informacji systemu Windows (PWT), w tym pozwala wybrać chronionego aplikacji, poziom ochrony PWT i jak znaleźć dane przedsiębiorstwa w sieci. Aby uzyskać więcej informacji na temat PWT zobacz następujące tematy:  

  -   [Ochrona danych przedsiębiorstwa przy użyciu ochrony informacji systemu Windows (PWT)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-wip)  

  -   [Tworzenie i wdrażanie zasad ochrony informacji systemu Windows (PWT) przy użyciu programu System Center Configuration Manager](https://technet.microsoft.com/itpro/windows/keep-secure/create-wip-policy-using-sccm)  

### <a name="new-in-configuration-manager-current-branch"></a>Nowe w programie Configuration Manager (bieżącej gałęzi)  
 Żadne nowe funkcje hybrydowe zostały wprowadzone w 2016 maja dla programu Configuration Manager (bieżącej gałęzi).  

##  <a name="new-hybrid-features-in-april-2016"></a>Nowe funkcje hybrydowe w 2016 kwietnia  

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune  
 Następujące funkcje Intune wprowadzone w 2016 kwietnia działają we wdrożeniach hybrydowego.  

- **MAM użytkownika zgodności**

  Można wyświetlać stan z zasadami zarządzania aplikacjami dla każdego użytkownika w Twojej dzierżawy usługi Azure Active Directory (AAD).  Aby uzyskać więcej informacji, zobacz [monitorowania zasad zarządzania aplikacjami mobilnymi w usłudze Microsoft Intune](/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune) w bibliotece Intune.  

- **MAM formantów, aby zapobiec synchronizacji kontaktów programu Outlook (Android)**

  Dostępne jest nowe ustawienie umożliwiająca uniemożliwić aplikacji synchronizowania kontakty do książki adresowej natywnych na urządzeniach. To nowe ustawienie jest początkowo obsługiwane przez aplikację Outlook na urządzeniach. Aby uzyskać więcej informacji, zobacz [tworzenie i wdrażanie zasad zarządzania aplikacjami mobilnymi w usłudze Microsoft Intune](/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune) w bibliotece Intune.  

- **Ulepszenia witryny internetowej portalu firmy**

  Gdy Windows 10 Mobile i Windows Phone 8.1 użytkownicy będą instalować aplikacje z biznesowych, widzą będzie teraz następujące nowe stany, które dostarczają szczegółowe informacje o stanie ich instalacji:  

  -   **Oczekiwanie na urządzenia do synchronizowania** — użytkownik ma obszar "Instaluj" i urządzenie teraz próbuje przeprowadzić synchronizację z infrastruktury usługi Intune. Synchronizacja jest wymagane, aby dokończyć instalację. Komunikat "Oczekujące na urządzenia do synchronizowania" jest również łącze, które użytkownicy mogą naciśnij, aby wyświetlone instrukcje ręcznego synchronizacji urządzenie w usłudze Intune, jeśli proces synchronizacji jest zbyt długo lub pobiera zablokowany.  

  -   **Pobieranie** — Trwa przetwarzanie żądania pobierania użytkownika i urządzenia jest pobranie i zainstalowanie aplikacji.  

- **Ulepszenia aplikacji portalu firmy Android**

  Użytkownicy, którzy nie zarejestrowali swoje urządzenia w usłudze Intune i którzy nie mają prawidłowy certyfikat zainstalowany nie będzie mógł zalogować się do aplikacji portalu firmy Android i zostanie wyświetlony komunikat, "Nie można zalogować się, ponieważ urządzenie brakuje wymaganego certyfikatu." Komunikat zawiera łącze "Jak rozwiązać ten problem", który użytkownicy mogą naciśnij, aby wyświetlić instrukcje dotyczące instalowania certyfikatu. Aby zobaczyć czynności, które użytkownicy końcowi wykonać, aby rozwiązać ten problem, zobacz [urządzeniu brakuje wymaganego certyfikatu](/intune/enduser/using-your-android-device-with-intune) w bibliotece Intune.  

- **Ulepszenia aplikacji Portal firmy systemu iOS**

  Dodano obsługę dla akcji ściągania do odświeżania odświeżyć zawartość w domu ekranu, który zawiera aplikacje z listy, listy urządzeń i działu IT informacji. Akcja ściągania do odświeżania nie sprawdza zgodności lub zasad informacje, które można wykonać, zaznaczając kafelków dla bieżącego urządzenia i naciskając **synchronizacji** przycisku.  

- **Ulepszenia Windows 10 Mobile i Windows Phone 8.1 firmy aplikacji portalu**

  Podczas instalowania aplikacji biznesowych o użytkowników końcowych, teraz zobaczą wystąpić instalacja aplikacji została poprawiona. Jeśli instalacja aplikacji jest zbyt długo, użytkownicy ręcznie zsynchronizować swoje urządzenie, aby wymusić procesu synchronizacji, aby wznowić. Aby zapoznać się z instrukcjami przez użytkownika końcowego, zobacz [synchronizacji urządzenia ręcznie, aby przyspieszyć proces instalacji aplikacji](/intune/enduser/using-your-windows-device-with-intune) w bibliotece Intune.  

###  <a name="new-in-1604-technical-preview"></a>Nowość w wersji 1604 Technical Preview
 Następujące nowe funkcje wprowadzone w programie 2016 kwietnia są dostępne we wdrożeniach hybrydowych z usługą Intune i techniczne 1604 Podgląd Configuration Manager. Te funkcje wymagają użycia konsoli programu Configuration Manager do konfigurowania i zarządzania nimi.  

- **Wyszukiwanie, zarządzania i dystrybucji Sklepu Windows dla aplikacji biznesowych dla urządzeń z systemem Windows 10 z konsoli programu Configuration Manager**


  Pomoc dla Sklepu Windows dla firm jest dostępna w konfiguracji Menedżera Technical Preview 1604 ułatwiają znajdowanie, zarządzanie i przeprowadzić dystrybucję aplikacji na urządzeniach Windows 10, który jest zarządzany. Aby uzyskać szczegółowe informacje, zobacz [Zarządzanie zakupione woluminu aplikacji ze Sklepu Windows dla firm](/sccm/core/get-started/capabilities-in-technical-preview-1604#manage-volume-purchased-apps-from-the-windows-store-for-business) w [możliwości 1604 Technical Preview dla programu System Center Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1604).  

- **Ustawienie SmartLock dla urządzeń z systemem Android**

  Nowe ustawienie został dodany do Android i Samsung KNOX Standard element konfiguracji, który umożliwia sterowanie funkcji SmartLock na urządzeniach zgodnych.  To ustawienie umożliwia uniemożliwić użytkownikom końcowym Konfigurowanie SmartLock. Zobacz [SmartLock ustawienia dla urządzeń z systemem Android](/sccm/get-started/capabilities-in-technical-preview-1604#smartlock-setting-for-android-devices) w [możliwości 1604 Technical Preview dla programu System Center Configuration Manager](/sccm/core/get-started/capabilities-in-technical-preview-1604.md).  

### <a name="new-in-configuration-manager-current-branch"></a>Nowe w programie Configuration Manager (bieżącej gałęzi)  
 Żadne nowe funkcje hybrydowe zostały wprowadzone w 2016 kwietnia dla programu Configuration Manager (bieżącej gałęzi).  

##  <a name="new-hybrid-features-in-march-2016"></a>Nowe funkcje hybrydowe marca 2016  

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune  
 Następujące funkcje Intune wprowadzone w programie 2016 marca działają we wdrożeniach hybrydowego.  

- **MAM formantów, aby zapobiec synchronizacji kontaktów programu Outlook (iOS)**

  Dostępne jest nowe ustawienie umożliwiająca uniemożliwić aplikacji synchronizowania kontakty do książki adresowej natywnych na urządzenia z systemem iOS. To nowe ustawienie jest obsługiwane przez aplikację Outlook na urządzeniach. Aby uzyskać więcej szczegółów na temat tego, jak i inne ustawienia, zobacz [tworzenia i wdrażania zasad zarządzania aplikacjami Mobilnymi](/intune/deploy-use/monitor-mobile-app-management-policies-with-microsoft-intune) w bibliotece Intune.  

- **Skype biznesowych online dostęp warunkowy**

  Można ustawić zasad dostępu warunkowego dla Skype dla usługi Online firmy, dzięki czemu mają dostęp tylko przez urządzenia Android i iOS zarządzane i zgodne.  Aby uzyskać szczegółowe informacje, zobacz [zarządzanie dostępem do programu Skype dla usługi Online firmy](/intune/deploy-use/restrict-access-to-skype-for-business-online-with-microsoft-intune) w bibliotece Intune.  

- **Obsługa iOS 9,3**

  Poniedziałek marca 21 Apple poinformowała dostępność iOS 9.3. Wszystkie istniejące funkcje Intune aktualnie dostępnych do zarządzania urządzeniami z systemem iOS będą nadal działać bezproblemowo jako użytkownicy uaktualnić swoje urządzenia do iOS 9.3.  

- **Pakiety aplikacji systemu Windows dostępne bezpośrednio z witryny sieci Web portalu firmy**

  Użytkownicy systemu Windows 8, Windows 8.1 i komputery z systemem Windows RT bezpośrednio z witryny sieci Web portalu firmy można zainstalować pakiety aplikacji systemu Windows (z rozszerzeniem .appx). Wcześniej należy wdrożyć lub użytkownicy mieli do instalowania aplikacji Portal firmy na swoich urządzeniach do zainstalowania aplikacji.  

- **Użytkownicy mogą zdalnie zablokować urządzenie z witryny sieci Web portalu firmy**

  Nowa opcja zdalne blokowanie dodano do witryny internetowej portalu firmy, aby umożliwić użytkownikom zdalnie zablokować urządzenie z portalu w przypadku utracenia lub kradzieży urządzenia.  

- **Korzystaj z iOS "Otwórz w" zarządzania dla urządzeń, które są zarejestrowane w rozwiązaniu MDM innych firm**

  Z dostawcą zarządzania (MDM) urządzenia przenośnego innych firm umożliwia wykorzystać iOS zarządzania "Otwórz w". Można ustawić ograniczenia określone w konfiguracji ustawień profilu i wdrożyć aplikację za pomocą oprogramowania MDM. Podczas instalowania aplikacji zarządzanej przez użytkownika, są stosowane ograniczenia. Szczegółowe informacje, zobacz: [Zasady zarządzania aplikacjami mobilnymi Microsoft Intune i iOS Otwórz w](/intune/deploy-use/introduction-to-device-compliance-policies-in-microsoft-intune) w bibliotece Intune.  

- **Aplikacje firmy Microsoft, które obsługują MAM**

  Listę aplikacji firmy Microsoft, którego można używać z zasadami zarządzania aplikacjami mobilnymi usługi Intune została zaktualizowana w celu uwzględnienia najnowszych aplikacji (w przypadku urządzeń zarejestrowanych w usłudze Intune tylko).  

- **Wdrażanie programu Adobe Reader usługi Microsoft Intune na urządzeniach zarządzanych przez usługę Intune iOS w przedsiębiorstwie**

  Teraz można zarządzać aplikacji Adobe Reader dla systemu iOS na zarejestrowane urządzenia z zasadami zarządzania aplikacjami mobilnymi usługi Intune.  

- Zarządzanie prawami udostępnianie aplikacji jest obsługiwana dla systemu Android

  Administratorzy IT można wdrożyć zasady zarządzania aplikacjami mobilnymi, więc użytkownicy końcowi mogą wyświetlać obrazy, AV i PDF plików bardziej bezpieczne, czy IT używa usługi Intune do zarządzania urządzeniami.  

- **Ulepszenia Android i iOS aplikacji Portal firmy**

  -   Użytkownicy uruchomić aplikację, która jest zarządzana przez Zarządzanie aplikacjami mobilnymi (MAM), zobaczy komunikat z informacją, że aplikacja jest zarządzana przez ich firmę. Użytkownicy mogą teraz wybierz łącze "Dowiedz się więcej", aby uzyskać więcej informacji, w tym miejscu o znaczenie "aplikacje zarządzane". One także wybrać "Nie pokazuj ponownie", aby wiadomości nie jest już wyświetlany, gdy uruchamiają one aplikację.  

  -   Nowe ekrany zostały dodane do przewodnika użytkowników przez proces rejestracji i podaj więcej informacji na temat Dlaczego należy zarejestrować użytkowników i co Administratorzy IT mogą i nie są wyświetlane na zarejestrowanych urządzeniach.  

  -   Komunikaty o błędach rejestracji są teraz wyświetlane w aplikacji Portal firmy.  

### <a name="new-in-configuration-manager-technical-preview"></a>Nowość w programie Configuration Manager Technical Preview  
 Żadne nowe funkcje hybrydowe zostały wprowadzone w 2016 marca dla Configuration Manager Technical Preview.  

### <a name="new-in-configuration-manager-current-branch"></a>Nowe w programie Configuration Manager (bieżącej gałęzi)  
 Następujące nowe funkcje wprowadzone w programie 2016 marca są dostępne we wdrożeniach hybrydowych za pomocą usługi Intune i program Configuration Manager (bieżącej gałęzi) wersja 1602. Te funkcje wymagają użycia konsoli programu Configuration Manager do konfigurowania i zarządzania nimi.  

- **zasady konfiguracji systemu iOS aplikacji**

  W wersji 1602 programu Configuration Manager (bieżącej gałęzi) zasady konfiguracji aplikacji służy do dostarczenia ustawień, które mogą być wymagane, gdy użytkownik uruchomi aplikację iOS. Aby uzyskać szczegółowe informacje, zobacz [skonfigurowanie aplikacji systemu iOS z zasady konfiguracji aplikacji w programie System Center Configuration Manager](/sccm/apps/deploy-use/configure-ios-apps-with-app-configuration-policies).  

- **Zarządzanie aplikacjami iOS kupionymi woluminu**

  W wersji 1602 programu Configuration Manager (bieżącej gałęzi) można wdrożyć i zarządzać aplikacjami, zakupionym w woluminie z VPP firmy Apple woluminu zakupu programu () przez importowanie informacji o licencji ze sklepu z aplikacjami i śledzenia, ile licencji jest używany. Aby uzyskać szczegółowe informacje, zobacz [zarządzania aplikacjami iOS kupionymi woluminu z System Center Configuration Manager](/sccm/apps/deploy-use/manage-volume-purchased-ios-apps).  

- **Automatyczne tworzenie aplikacji mobilnych pakietu Office**

  Następujące aplikacje mobilne Microsoft Office dla systemów Android i iOS począwszy od wersji 1602 programu Configuration Manager (bieżącej gałęzi), są tworzone podczas uaktualnienia z wersji 1511:  

  -   Program Microsoft Word  
  -   Program Microsoft Excel  
  -   Program Microsoft PowerPoint  
  -   Microsoft OneDrive  
  -   Program Microsoft OneNote (tylko iOS)  
  -   Program Microsoft Outlook  

  Te aplikacje można znaleźć w węźle aplikacji konsoli programu Configuration Manager. Aby uzyskać więcej informacji dotyczących wdrażania aplikacji, zobacz [jak wdrażać aplikacje z System Center Configuration Manager](../../apps/deploy-use/deploy-applications.md).  

- **Ustawienia trybu kiosku dla urządzeń z systemem Android Samsung KNOX Standard**

  Tryb kiosku umożliwia blokowanie urządzenia w celu zezwolenia na działanie tylko niektórych funkcji.  Począwszy od wersji 1602 programu Configuration Manager (bieżącej gałęzi), można teraz określić ustawienia trybu kiosku dla urządzeń Samsung KNOX Standard. Aby uzyskać szczegółowe informacje, zobacz [tworzenie elementów konfiguracji dla urządzeń Android i Samsung KNOX Standard zarządzane bez klienta programu System Center Configuration Manager](/sccm/compliance/deploy-use/create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client).  

- **iOS blokadę aktywacji**

  Począwszy od wersji 1602 programu Configuration Manager (bieżącej gałęzi), można zarządzać iOS blokadę aktywacji, funkcja aplikacja Znajdź mój iPhone dla systemu iOS 7.1 i nowsze urządzeń. Blokada aktywacji jest włączana automatycznie w przypadku użycia aplikacji Znajdź mój iPhone na urządzeniu.  Aby uzyskać szczegółowe informacje, zobacz [iOS Zarządzaj blokadę aktywacji obejścia dla programu System Center Configuration Manager](/sccm/mdm/deploy-use/manage-ios-activation-lock#bypass-activation-lock).  

