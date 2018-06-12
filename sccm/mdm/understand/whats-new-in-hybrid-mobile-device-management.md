---
title: What's new in hybrydowego zarządzania urządzeniami Przenośnymi
titleSuffix: Configuration Manager
description: Poznaj nowe funkcje zarządzania urządzeniami przenośnymi dostępne dla hybrydowych wdrożeń z programu Configuration Manager i usługi Intune.
ms.date: 06/04/2018
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 7b127cee-61f1-4681-9760-caebed36ddf5
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 62b86310b8a7eb183cc5e759e9c1087b80a72d6b
ms.sourcegitcommit: 032e6e19b819863e43e36b24b57761d0a173d0dc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2018
ms.locfileid: "34754577"
---
# <a name="whats-new-in-hybrid-mobile-device-management-with-configuration-manager-and-microsoft-intune"></a>What's new in hybrydowego zarządzania urządzeniami przenośnymi za pomocą programu Configuration Manager i Microsoft Intune

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



## <a name="may-2018"></a>2018 maja

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune

#### <a name="intune-app-protection-policies-and-microsoft-edge"></a>Zasady ochrony aplikacji usługi Intune i Microsoft Edge 
<!--1818968,1818969-->
Przeglądarka Microsoft Edge dla urządzeń przenośnych (iOS i Android) obsługuje teraz zasady ochrony aplikacji Microsoft Intune. Użytkownicy urządzeń iOS i Android logujących się ich firmowych kont usługi Azure Active Directory w aplikacji krawędzi są chronione przez usługę Intune. Na urządzeniach z systemem iOS, zasady **wymagają programu managed browser dla zawartości sieci web** umożliwia użytkownikom otwieranie łączy w programie Edge, gdy jest on zarządzany.

#### <a name="requesting-help-in-the-company-portal-for-windows-10"></a>Żądanie pomocy w portalu firmy dla systemu Windows 10 
<!--1874137-->
Portal firmy dla systemu Windows 10 teraz wysyła Dzienniki aplikacji bezpośrednio do firmy Microsoft, gdy użytkownik inicjuje przepływu pracy, aby uzyskać pomoc dotyczącą problemu. To zachowanie ułatwia do rozwiązywania oraz usuwania problemów, które zostały zgłoszone do firmy Microsoft.  


### <a name="new-in-configuration-manager-current-branch"></a>Nowe w programie Configuration Manager (wersji current branch)

#### <a name="android-for-work-and-lookout-onboarding-moved-to-intune-on-azure"></a>Android do dołączenia do pracy i Lookout przeniesione do usługi Intune na platformie Azure
<!--2355022,2357366-->
Przy użyciu najnowszych aktualizacji usługi Intune można włączyć i zarządzać Android integracji pracy i Lookout zagrożeń przenośnych obrony integracji na dzierżawcy zarządzania urządzeniami przenośnymi hybrydowych w usłudze Intune w portalu Azure. Przed aktualizacją tylko były można skonfigurować w portalu klasycznym usługi Intune (platformy Silverlight).
 
Uwaga: Lookout to zagrożenie tylko przenośnych dostawca obrony (MTD) obsługiwane hybrydowy. Jeśli wcześniej jest zintegrowana z innymi dostawcy MTD, nadal wydaje się w usłudze Intune w portalu Azure. Usunięcie łącznika dla niego, następnie nie można dodać go ponownie.
 
Te zmiany nie wpływają na istniejące funkcje. Nadal używać konsoli programu Configuration Manager do zarządzania powiązanych aplikacji, raportowanie i zasady.
 
Aby uzyskać więcej informacji zobacz następujące artykuły:
- [Konfigurowanie zarządzania urządzeniami hybrydowego systemu Android](/sccm/mdm/deploy-use/enroll-hybrid-android)
- [Zarządzanie dostępem do zasobów firmy na podstawie urządzeń, sieci i ryzyka aplikacji](/sccm/mdm/deploy-use/lookout-mobile-threat-defense-in-configuration-manager)


#### <a name="support-for-new-versions-of-cisco-anyconnect-client-for-ios"></a>Obsługa nowych wersji klienta Cisco AnyConnect dla systemu iOS
<!--1357393-->
Można włączyć obsługę Cisco AnyConnect dla systemu iOS w wersji 4.0.7 lub nowszej. Jeśli to zrobisz, są oznaczone istniejących profilów sieci VPN między Cisco AnyConnect **Cisco AnyConnect starszych**i w dalszym ciągu działać tak jak poprzednio. **Cisco AnyConnect** opcja jest dla profile nowej sieci VPN, które współpracują Cisco AnyConnect w wersji dla systemu iOS 4.0.7 lub nowszej.

Aby uzyskać więcej informacji na temat włączania tej funkcji, zobacz [funkcje wersji wstępnej](/sccm/core/servers/manage/pre-release-features).

> [!Note]  
> Nadal używać **Cisco AnyConnect starszych** opcji macOS profilów sieci VPN. 



## <a name="april-2018"></a>2018 kwietnia

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune

#### <a name="intune-adapts-to-fluent-design-system-in-the-company-portal-app-for-windows-10"></a>Usługa Intune dostosowuje się do Fluent System projektu w aplikacji Portal firmy dla systemu Windows 10 
<!--1195010-->
Aplikacja Portal firmy usługi Intune dla systemu Windows 10 zostały zaktualizowane o [widok nawigacji Fluent System projektu](/windows/uwp/design/basics/navigation-basics). Strony aplikacji zauważyć statycznych, pionowy listy wszystkich stron najwyższego poziomu. Kliknij dowolne łącze, aby szybko wyświetlić i przełączać się między stronami. Ta aktualizacja jest pierwszy z kilku zostanie wyświetlony w ramach dążenia trwającą, aby utworzyć środowisko adaptacyjną, empathetic i znanego w usłudze Intune. Aby wyświetlić zaktualizowaną wygląd, przejdź do [nowości w aplikacji interfejsu użytkownika](/intune/whats-new-app-ui).

#### <a name="improved-device-tiles-in-the-windows-10-company-portal"></a>Kafelki ulepszone urządzenia w portalu firmy systemu Windows 10
<!--2213364-->
Kafelki zostały zaktualizowane więcej dostępne dla użytkowników z niskim wzrokiem i lepiej dla narzędzi do odczytywania zawartości ekranu.


#### <a name="test-the-company-portal-for-macos-on-virtual-machines"></a>Testowanie portalu firmy, aby system macOS na maszynach wirtualnych
<!--2216679-->
Firma Microsoft opublikowaniu wskazówki ułatwiające Administratorzy IT testowanie aplikacji Portal firmy dla macOS na maszynach wirtualnych w pulpitu równoleżników i VMware Fusion. Aby uzyskać więcej informacji, zobacz [rejestrowanie maszyn wirtualnych macOS testowania](/intune/macos-enroll#enroll-virtual-macos-machines-for-testing).


#### <a name="send-diagnostic-reports-in-company-portal-app-for-macos"></a>Wyślij raporty diagnostyczne w aplikacji Portal firmy dla macOS
<!--2216677-->
Aplikacja Portal firmy dla urządzeń macOS została zaktualizowana do poprawy, jak użytkownicy raportować błędy związane z usługi Intune. W aplikacji Portal firmy można pracowników:

- Ładowanie raportów diagnostycznych bezpośrednio do zespołu deweloperów Microsoft.
- Identyfikator zdarzenia w Twojej firmie poczty e-mail IT obsługuje zespołu.


#### <a name="updated-help-experience-on-company-portal-app-for-android"></a>Zaktualizowano środowiska Pomoc w aplikacji Portal firmy dla systemu Android 
<!--1631531-->
Zaktualizowaliśmy środowiska Pomoc w aplikacji Portal firmy dla systemu Android w celu zapewnienia zgodności z najlepszymi rozwiązaniami platformy systemu Android. Teraz, gdy użytkownicy wystąpi problem w aplikacji, można wybrać **Menu** > **pomocy** oraz:
- Przekazywanie dzienników diagnostycznych do firmy Microsoft.
- Wyślij wiadomość e-mail, który opisuje identyfikator problemu i zdarzenia do działu pomocy technicznej firmy.


#### <a name="update-where-to-configure-your-app-protection-policies"></a>Zaktualizuj where do skonfigurowania zasad ochrony aplikacji 
<!--2144597-->
W portalu Azure w ramach usługi Microsoft Intune zamierzamy tymczasowo przekierowanie z **ochrony aplikacji usługi Intune** bloku usługi do **aplikacji mobilnej** bloku. Należy pamiętać, że wszystkie zasad ochrony aplikacji znajdują się już na **aplikacji mobilnej** bloku w usłudze Intune w obszarze Konfiguracja aplikacji. Zamiast przechodząc do ochrony aplikacji usługi Intune, tak aby przejść do usługi Intune. W kwietniu 2018, możemy zatrzyma przekierowywanie i całkowitego usunięcia **ochrony aplikacji usługi Intune** usługi bloku, w taki sposób, aby tylko jedną lokalizację dla zasad ochrony aplikacji w ramach usługi Intune. 

**Jak to wpływa mnie?** Ta zmiana będzie miało wpływ na klientów autonomicznej usługi Intune i klientów hybrydowych (usługę Intune z programem Configuration Manager). Integracja ta pomoże uprościć administrowanie zarządzania z chmury.

**Co należy zrobić, aby przygotować się do tej zmiany?** Sprawdź znacznik **Intune** jako ulubiony zamiast **ochrony aplikacji usługi Intune** usługi bloku i upewnij się, możesz zapoznać się z przepływem pracy zasad ochrony aplikacji w **Mobile** bloku aplikacji w ramach usługi Intune. Firma Microsoft będzie przekierowywać krótki okres czasu, a następnie usuń **ochrony aplikacji** bloku. Pamiętaj, że wszystkie zasady ochrony aplikacji znajdują się już w usłudze Intune i można zmodyfikować jego dowolne zasad dostępu warunkowego. Aby uzyskać więcej informacji na temat modyfikowania zasad dostępu warunkowego, zobacz [dostępu warunkowego w usłudze Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-conditional-access-azure-portal). Aby uzyskać dodatkowe informacje, zobacz [co to są zasady ochrony aplikacji?](/intune/app-protection-policy) 




#### <a name="user-experience-update-for-the-company-portal-app-for-ios"></a>Aktualizacja środowiska użytkownika dla aplikacji Portal firmy dla systemu iOS 
<!--1412866-->
Firma Microsoft opublikowała zostały aktualizacją środowisko głównych użytkownika do aplikacji Portal firmy dla systemu iOS. Aktualizacja funkcji pełną one visual zawierającą zmodernizowanej wyglądu i działania. Firma Microsoft już utrzymywane funkcjonalności aplikacji, ale zwiększenie jego użyteczność i dostępności.  

Zostanie również wyświetlony:
- Obsługa iPhone X.
- Szybsze uruchamianie aplikacji i ładowania odpowiedzi, aby zaoszczędzić czas użytkowników.
- Paski postępu dodatkowe użytkownikom najbardziej aktualne informacje o stanie.
- Ulepszenia użytkownikom sposób przekazywania dzienników, więc jeśli jakaś nieprawidłowość, jest łatwiejsze do raportu.  

Aby wyświetlić zaktualizowaną wygląd, przejdź do [nowości w aplikacji interfejsu użytkownika](/intune/whats-new-app-ui).



## <a name="march-2018"></a>2018 marca

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune

#### <a name="windows-company-portal-send-feedback-option-may-no-longer-work"></a>Systemu Windows firmy portalu wysyłania opinie mogą przestać działać.
<!--2070166-->
Aplikacja Portal firmy dla systemu Windows ma opcję Prześlij opinię zezwolenie użytkownikom wysyłanie informacji zwrotnych na temat aplikacji do firmy Microsoft. Od 30 kwietnia 2018 tej opcji nadal jest obsługiwany tylko w aplikacji Portal firmy dla systemu Windows 10, uruchomionej w systemie Windows 10 w wersji 1607 i nowszych.   

**Jak to wpływa mnie?**

Jeśli nie ma aplikacji Portal firmy dla systemu Windows zainstalowane dla użytkowników końcowych, możesz zignorować ten komunikat.

Jeśli którykolwiek z użytkowników końcowych w aplikacji Portal firmy, należy pamiętać, że począwszy od 30 kwietnia, przycisk Prześlij opinię przestaje działać dla aplikacji w następujących scenariuszach:  

 - Aplikacja Portal firmy dla systemu Windows 10 w systemie Windows 10 w wersji 1507 i wersji 1511  

 - Windows Phone 8.1 aplikacji Portal firmy  

W przypadku urządzeń wpływ na opcji Prześlij opinię kończy się niepowodzeniem i nie powiedzie się, nawet w przypadku ponawianie próby. Wysyłanie opinii do firmy Microsoft dotyczące środowiska na tych platformach, istnieją alternatywne opinii kanały wymienionych poniżej.

**Co należy zrobić, aby przygotować się do tej zmiany?**

Powiadamia użytkowników końcowych tej zmiany i zaktualizować wskazówki żadnych użytkowników, jeśli to konieczne. 

Poinformuj użytkowników końcowych za pomocą portalu firmy na Windows Phone 8.1, Windows 10 w wersji 1507 i Windows 10 w wersji 1511 mają dwa kanały alternatywny opinii. Mogą one:  

- Użyj informacji zwrotnych Centrum aplikacji w systemie Windows 10  
- Wyślij wiadomość e-mail do WinCPfeedback@microsoft.com  

Poproś użytkowników końcowych w systemie Windows 10 w wersji 1607 lub później aktualizację do najnowszej wersji systemu Windows w portalu firmy dostępnej w Microsoft Store.



#### <a name="azure-active-directory-web-sites-can-require-the-intune-managed-browser-app-and-support-single-sign-on-for-the-managed-browser-public-preview"></a>Witryn sieci web w usłudze Azure Active Directory może wymagać aplikacji przeglądarki zarządzanej Intune i obsługę rejestracji jednokrotnej w programie Managed Browser (publicznej wersji zapoznawczej)
<!-- 710595 --> 
Za pomocą usługi Azure Active Directory (Azure AD), można teraz ograniczyć dostęp do witryn sieci web na urządzeniach przenośnych z aplikacji Intune Managed Browser. W programie managed browser danych witryny sieci web pozostanie bezpieczne i oddzielnie od danych osobowych użytkownika końcowego. Ponadto w programie Managed Browser będzie obsługiwać możliwości logowania jednokrotnego dla witryn chronione przez usługę Azure AD. Rejestrowanie w programie Managed Browser lub przy użyciu programu Managed Browser na urządzeniu z innej aplikacji zarządzanych przez usługę Intune, umożliwia Managed Browser na dostęp do firmowych stron chronione przez usługę Azure AD bez konieczności wprowadzania poświadczeń użytkownika. Ta funkcja ma zastosowanie do witryny, takich jak program Outlook Web Access (OWA) i usługi SharePoint Online, a także innych witryn firmowych, takich jak zasoby intranetowe dostępne za pośrednictwem serwera Proxy aplikacji Azure.



## <a name="february-2018"></a>2018 lutego

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune

- **System macOS Portal firmy obsługę rejestracji, które używają Menedżera rejestracji urządzeń**  
    Użytkownicy mogą teraz używać Menedżera rejestracji urządzeń podczas rejestrowania z macOS portalu firmy.
    <!-- 1352411 -->


## <a name="january-2018"></a>2018 stycznia

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune

- **Zatwierdzenie aplikacji Portal firmy dla systemu Android for Work**  
  Jeśli Twoja organizacja korzysta z systemu Android do pracy, należy ręcznie zatwierdzić aplikacji Portal firmy dla systemu Android. Następnie nadal otrzymywać aktualizacje automatyczne zarządzanych sklepu Google Play.
  <!--1797090 -->  

- **Zasady dostępu warunkowego dla usługi Intune są dostępne wyłącznie z portalu Azure**   
  Począwszy od tej wersji, należy skonfigurować i zarządzać zasad dostępu warunkowego w [portalu Azure](https://portal.azure.com) z **usługi Azure Active Directory** > **dostępu warunkowego** . Dla wygody można także przejść tego bloku z usługi Intune w portalu Azure pod adresem **Intune** > **dostępu warunkowego**.
  <!-- 1737088 1634311 --> 

- **Aktualizacje zgodności wiadomości e-mail**    
  Po wysłaniu wiadomości e-mail na zgłaszanie niezgodnych urządzeń szczegółowe informacje o niezgodności urządzenia są uwzględniane. 
  <!--1637547 -->

- **Nowa funkcja akcję "Usuń" dla urządzeń z systemem Android**    
  Rozwija akcję "Usuń" dla aplikacji Portal firmy dla systemu Android **zaktualizować ustawienia urządzenia** rozwiązywać [problemy dotyczące szyfrowania urządzenia](https://docs.microsoft.com/intune-user-help/encrypt-your-device-android).
  <!--1583480-->

- **Zdalne blokowanie dostępne w aplikacji Portal firmy dla systemu Windows 10**    
  Użytkownicy końcowi teraz mogą zdalnie blokować swoje urządzenia w aplikacji Portal firmy dla systemu Windows 10. Ta akcja nie jest wyświetlana dla lokalnej urządzenia, które aktywnie używanych.
  <!--676506-->

- **Łatwiejsze Rozwiązywanie problemów zgodności aplikacji Portal firmy dla systemu Windows 10**   
  Użytkownicy końcowi z urządzeniami z systemem Windows można wybrać przyczynę braku zgodności aplikacji Portal firmy. Jeśli to możliwe, ta czynność przynosi je bezpośrednio do poprawnej lokalizacji w aplikacji ustawień, aby rozwiązać ten problem.
  <!--676546-->    



## <a name="december-2017"></a>2017 grudnia

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune

- **Wdrożenia aplikacji dostępna teraz obsługiwane dla systemu Android przedsiębiorstwa**    
  Teraz można wdrażać aplikacje dla systemu Android przedsiębiorstwa (dawniej Android for Work) jako **dostępne**, oprócz **wymagane**. Aby uzyskać więcej informacji, zobacz [utworzyć Android aplikacje z System Center Configuration Manager](/sccm/mdm/deploy-use/creating-android-applications).



## <a name="november-2017"></a>2017 listopada

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune

- **Protokół tekst dozwolone z zarządzanych aplikacji**  
  Aplikacje zarządzane przez zestaw SDK aplikacji usługi Intune mają możliwość wysyłania wiadomości SMS.
  <!-- 1414050  -->   

- **Aplikacja Portal firmy dla macOS jest dostępna**   
  Portal firmy usługi Intune na macOS ma środowisko zaktualizowane. Jest zoptymalizowany do prawidłowo wyświetlić wszystkie powiadomienia informacji i zgodności, które użytkownicy potrzebują dla wszystkich urządzeń, które mają one zarejestrowane. I po Portal firmy usługi Intune został wdrożony na urządzeniu, AutoUpdate firmy Microsoft dla macOS zawiera aktualizacje do niego. Pobierz nowy Portal firmy usługi Intune dla macOS, logując się do witryny sieci Web Portal firmy usługi Intune z urządzenia macOS.
  <!--1541700-->   

- **Microsoft Planner jest obecnie częścią zarządzania (aplikacjami mobilnymi MAM) aplikacji mobilnej listę zatwierdzonych aplikacji**    
  Aplikacja Microsoft Planner dla systemów iOS i Android jest obecnie częścią zatwierdzonych aplikacji do zarządzania aplikacjami mobilnymi (MAM). Konfigurowanie aplikacji za pomocą bloku ochrony aplikacji usługi Intune w portalu Azure do wszystkich dzierżawców. Aby uzyskać więcej informacji, zobacz [MAM listę zatwierdzonych aplikacji](https://www.microsoft.com/cloud-platform/microsoft-intune-apps).
  <!-- 1248473 -->    

- **Rejestruje dostęp do zarządzanych aplikacji dla systemu iOS**    
  Użytkownikom końcowym z zainstalowaną przeglądarkę zarządzane mogą teraz wyświetlanie stanu zarządzania Microsoft wszystkie opublikowane aplikacje i wyśle dzienniki do rozwiązywania problemów z ich zarządzane aplikacje systemu iOS.
  <!-- 1469920 -->    

  Dowiedz się, jak włączyć trybu rozwiązywania problemów w programie Managed Browser na urządzeniu z systemem iOS, zobacz [jak uzyskać dostęp do zarządzanych aplikacji dzienników przy użyciu programu Managed Browser w systemie iOS](https://docs.microsoft.com/intune/app-configuration-managed-browser#how-to-access-to-managed-app-logs-using-the-managed-browser-on-ios).

- **Ulepszenia urządzenia Konfiguracja przepływu pracy w portalu firmy dla systemu iOS w wersji 2.9.0**    
  Ulepszono przepływu pracy ustawień urządzenia w aplikacji Portal firmy dla systemu iOS. Język jest bardziej przyjazny dla użytkownika i ekrany już połączyć w miarę możliwości. Również wprowadzono język dokładniej do firmy przy użyciu nazwy firmy przez cały tekst Instalatora. Ten zaktualizowany przepływ pracy można wyświetlić na [nowości w aplikacji interfejsu użytkownika](https://docs.microsoft.com/intune/whats-new-app-ui#week-of-november-13-2017) strony.

- **Opinie wyświetla monit dotyczący aplikacji Portal firmy dla systemu Android**    
  Aplikacja Portal firmy dla systemu Android teraz żądania opinii użytkowników końcowych. Tej opinii jest wysyłany bezpośrednio do firmy Microsoft i oferuje użytkownikom końcowym możliwość Przegląd aplikacji w sklepie Google Play publicznego. Opinia nie jest wymagana i łatwo może być ukryty, dlatego użytkownicy mogą nadal używać aplikacji. 
  <!--1165249-->    

- **Powiadamia użytkowników końcowych, jakie informacje o urządzeniu są widoczne dla urządzeń z systemem Windows 10**    
  Dodaliśmy **typ własności** do ekranu szczegóły urządzenia w aplikacji Portal firmy dla systemu Windows 10. Tych informacji umożliwia użytkownikom dowiedzieć się więcej o ochronie prywatności bezpośrednio z usługi Intune dokumentów użytkownika końcowego. One również informacje można znaleźć na **o** ekranu.
  <!--1337920-->    

- **Nowa akcja "Rozwiązać" dostępne dla urządzeń z systemem Android**    
  Aplikacja Portal firmy dla systemu Android wprowadzają akcję "Usuń" na _zaktualizować ustawienia urządzenia_ strony. Wybranie tej opcji powoduje użytkownika bezpośrednio do ustawienie, które powoduje ich urządzenia niezgodne. Aplikacja Portal firmy dla systemu Android obsługuje obecnie tę akcję dla [kod dostępu urządzenia](https://docs.microsoft.com/intune-user-help/set-your-pin-or-password-android), [szyfrowania urządzenia](https://docs.microsoft.com/intune-user-help/encrypt-your-device-android), [debugowanie USB](https://docs.microsoft.com/intune-user-help/you-need-to-turn-off-usb-debugging-android), i [nieznany Źródła](https://docs.microsoft.com/intune-user-help/you-need-to-turn-off-unknown-sources-android) ustawienia. 
  <!--1583480-->    


### <a name="new-in-configuration-manager-current-branch"></a>Nowe w programie Configuration Manager (wersji current branch)

- **Akcje dla braku zgodności**    
  Można teraz skonfigurować uporządkowane czasu sekwencję akcji, które są stosowane do urządzeń, które stwierdzona zostanie niezgodność. Na przykład można powiadamiać użytkowników o niezgodnych urządzeń za pośrednictwem poczty e-mail lub oznaczyć te urządzenia niezgodne. Aby uzyskać więcej informacji, zobacz [ustawiania akcji dla zgodności z systemem innym niż](/sccm/mdm/deploy-use/actions-for-noncompliance).
  <!--1321366 -->

- **Nowe ustawienia zasad zarządzania aplikacjami mobilnymi**     
  Następujące ustawienia zostały dodane do ustawienia zasad zarządzania aplikacjami mobilnymi:
  - **Wyłącz synchronizację kontaktów**: Aplikacja uniemożliwia zapisywania danych do aplikacji natywnej kontaktów na urządzeniu.
  - **Wyłącz drukowanie**: Zapobiega aplikacji z drukowaniem pracy lub szkoły danych.
  <!-- 1324760 -->    

  Zobacz [ochrona aplikacji przy użyciu zasad ochrony aplikacji w programie Configuration Manager](/sccm/mdm/deploy-use/protect-apps-using-mam-policies) próby nowe ustawienia zasad ochrony aplikacji.

- **Obsługa urządzeń z systemem Windows 10 ARM64**     
  Scenariuszy zarządzania urządzeniami Przenośnymi urządzeniami przenośnymi hybrydowego są obsługiwane na urządzeniach ARM64 z systemem Windows 10, jeśli te urządzenia nie są dostępne. Aby uzyskać więcej informacji, zobacz [Obsługa urządzeń z systemem Windows 10 ARM64](/sccm/core/plan-design/changes/whats-new-in-version-1710#windows-10-arm64-device-support).
  <!-- 1355000 -->    

- **Udoskonalone środowisko profilu sieci VPN w konsoli programu Configuration Manager**     
  W tej wersji Zaktualizowaliśmy VPN profilu Kreatora właściwości strony i aby wyświetlić ustawienia odpowiednie dla wybranej platformy. Ta funkcja była wcześniej dostępne w konfiguracji Manager Technical Preview 1709. Teraz jest ona dostępna w przypadku wdrożeń hybrydowych usługi Intune i programu Configuration Manager (Current Branch) wersja 1710. Aby uzyskać więcej informacji, zobacz [środowisko profilu ulepszone sieci VPN w konsoli programu Configuration Manager](/sccm/core/plan-design/changes/whats-new-in-version-1710#improved-vpn-profile-experience-in-configuration-manager-console).
  <!-- 1318232 -->


### <a name="new-in-configuration-manger-technical-preview-1711"></a>Nowa w programie Configuration Manager Technical Preview 1711

- **Nowe opcje zasad zgodności dla systemu Windows 10**   
  Można teraz skonfigurować nowe opcje zasad zgodności dla urządzeń z systemem Windows 10. Nowe ustawienia wymuszania zasad zapory, Kontrola konta użytkownika systemu Windows Defender Antivirus i przechowywanie wersji kompilacji systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [nowe opcje zasad zgodności dla systemu Windows 10](/sccm/core/get-started/capabilities-in-technical-preview-1711#new-compliance-policy-options-for-windows-10).



## <a name="october-2017"></a>2017 października

### <a name="new-in-configuration-manager-technical-preview-1709"></a>Nowość w programie Configuration Manager Technical Preview 1709

- **Udoskonalone środowisko profil sieci VPN w konsoli programu Configuration Manager**      
  Ustawienia profilu sieci VPN, teraz są filtrowane zgodnie z platform. Podczas tworzenia nowych profilów sieci VPN każdej z obsługiwanych platform zawiera tylko ustawienia odpowiednie dla platformy. Nie dotyczy istniejących profilów sieci VPN. Więcej o tej zmianie [tutaj](/sccm/core/get-started/capabilities-in-technical-preview-1709#improved-vpn-profile-experience-in-configuration-manager-console).
  <!-- 1313282 -->


### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune  

- **Pomoc programu użytkowników samodzielne rozwiązywanie problemów z aplikacją Portal firmy dla systemu Android**     
  Aplikacja Portal firmy dla systemu Android został dodany instrukcji dla użytkowników końcowych pomóc zrozumieć i prawdopodobnie własnym rozwiązania na nowe przypadki użycia.
    - Jeśli użytkownicy końcowi osiągnięto maksymalną liczbę urządzeń, które mogą dodawać, są one wskazówki [portalu usługi Azure Active Directory](https://account.activedirectory.windowsazure.com/r/#/profile) do usunięcia urządzenia.
    - Użytkownicy końcowi są podane kroki, aby wykonać, aby ułatwić im [błędy aktywacji na Samsung Knox urządzenia](https://go.microsoft.com/fwlink/?linkid=859718) lub [wyłączyć tryb oszczędzania energii](https://docs.microsoft.com/intune-user-help/power-saving-mode-android). Jeśli żadna z tych rozwiązań ich rozwiązać udostępniamy wyjaśnienie sposobu [dzienniki przesłać do firmy Microsoft](https://docs.microsoft.com/intune-user-help/send-logs-to-microsoft-android).
  <!-- 1573324, 1573150, 1558616, 1564878 -->      

- **Wskaźnik postępu instalacji urządzenia w portalu firmy dla systemu Android**    
  Aplikacja Portal firmy dla systemu Android zawiera wskaźnik postępu instalacji urządzenia, gdy użytkownik jest rejestrowanie swojego urządzenia. Wskaźnik przedstawia nowe stany, począwszy od "Konfigurowanie urządzenia...", a następnie "... rejestrowanie urządzenia", "Zakończył rejestrowanie urządzenia...", a następnie "Kończenie konfigurowania urządzenia...".  
  <!--1565657-->    

- **Obsługę uwierzytelniania opartego na certyfikatach w portalu firmy dla systemu iOS**    
  Dodaliśmy obsługę uwierzytelniania opartego na certyfikatach (CBA) w aplikacji Portal firmy dla systemu iOS. Użytkownicy z CBA wprowadzić swoją nazwę użytkownika, a następnie wybrać link "Zaloguj się przy użyciu certyfikatu". CBA jest już obsługiwana w aplikacji Portal firmy dla systemu Android i Windows. Aby dowiedzieć się więcej na [logowania do aplikacji Portal firmy](https://docs.microsoft.com/intune-user-help/sign-in-to-the-company-portal) strony.
  <!--1029830-->   

- **Ulepszenia przepływu pracy ustawień urządzenia w portalu firmy**     
  Ulepszono przepływu pracy ustawień urządzenia w aplikacji Portal firmy dla systemu Android. Język jest bardziej przyjazny dla użytkownika i specyficzne dla firmy, a w miarę możliwości zostały połączyć ekranów. Te ulepszenia można wyświetlić na [nowości w aplikacji interfejsu użytkownika](https://docs.microsoft.com/intune/whats-new-app-ui#week-of-october-2-2017) strony.
  <!--1490692-->     

- **Ulepszone wskazówki dotyczące żądania dostępu do kontaktów na urządzeniach z systemem Android**     
  Aplikacja Portal firmy dla systemu Android często wymaga od użytkownika końcowego zaakceptować uprawnień do kontaktów. Konto użytkownika końcowego odrzuci tego dostępu, zobacz temat powiadomienie w aplikacji, które je, aby przyznać jej dostęp warunkowy do alertów. 
  <!--1484985-->     

- **Korygowanie bezpiecznego uruchamiania dla systemu Android**     
  Użytkownicy końcowi z urządzeniami z systemem Android można wybrać przyczynę braku zgodności aplikacji Portal firmy. Jeśli to możliwe, ta czynność przynosi je bezpośrednio do poprawnej lokalizacji w aplikacji ustawień, aby rozwiązać ten problem. 
  <!--1490712-->    

- **Powiadomienia wypychane dodatkowych dla użytkowników końcowych w aplikacji Portal firmy dla systemu Android Oreo**    
  Użytkownicy widzą dodatkowe powiadomienia do wskazania je, gdy aplikacja Portal firmy dla systemu Android Oreo wykonuje zadania w tle, takie jak pobieranie zasad z usługi Intune. Powiadomienia zwiększenia przejrzystości dla użytkowników końcowych, temat, do portalu firmy jest wykonywania zadań administracyjnych na urządzeniu. To ulepszenie jest częścią ogólnych [optymalizacji interfejsu użytkownika portalu firmy](https://blogs.technet.microsoft.com/intunesupport/2017/08/21/android-8-0-o-behaviour-changes-and-microsoft-intune) aplikacji Portal firmy dla systemu Android Oreo. 
  <!--1475932 -->     

- **Nowe zachowania dla aplikacji Portal firmy dla systemu Android przy użyciu profilów pracy**     
  Po zarejestrowaniu Android pracy urządzenia z profilem pracy jest aplikacja Portal firmy w profilu pracy, który wykonuje zadania zarządzania na urządzeniu. 

  Jeśli nie używasz aplikacji z obsługą funkcji MAM w ten profil, aplikacja Portal firmy dla systemu Android nie spełnia już użycia. Aby poprawić środowisko pracy profilu, Intune automatycznie ukrywa osobistych aplikacji Portal firmy po rejestracji profilu pracy powiodło się.

  Aplikacja Portal firmy dla systemu Android można włączyć w dowolnym momencie w profilu osobistego przeglądając [Portal firmy ze sklepu Play](https://play.google.com/store/apps/details?id=com.microsoft.windowsintune.companyportal) i naciskając **włączyć**.
  <!--1485783-->    

- **Firmy, Portal dla Windows 8.1 i Windows Phone 8.1 przechodzenia do trybu utrzymywanie**    
  Zostanie wyświetlone powiadomienie został dodany do anonsowania, że przechodzenia do trybu utrzymywanie aplikacji Portal firmy dla Windows 8.1 i Windows Phone 8.1. Aby uzyskać więcej informacji, zobacz [powiadomienia](#notices).  
  <!--1428681-->    

- **Blok nieobsługiwany rejestracji urządzenia Samsung Knox**   
  Tylko aplikacja Portal firmy próbuje zarejestrować obsługiwane urządzenia Samsung Knox. Aby uniknąć błędów aktywacji KNOX, które uniemożliwiają rejestracji MDM, rejestracji urządzenia nastąpiła tylko jeśli urządzenie znajduje się w [listy urządzeń opublikowanych przez firmy Samsung](https://www.samsungknox.com/knox-supported-devices/knox-workspace). Urządzenia Samsung mogą mieć numery modelu, które obsługują KNOX, podczas gdy inne, które nie. Sprawdź zgodność Knox z odsprzedawcą urządzenia przed zakupu i wdrażania. Pełną listę zweryfikowanych urządzeń w można znaleźć [ustawienia zasad systemu Android i Samsung KNOX Standard](https://docs.microsoft.com/intune-classic/deploy-use/android-policy-settings-in-microsoft-intune#supported-samsung-knox-standard-devices).
  <!-- 1490695 -->     

- **Wsparcie dla systemu Android 4.3 i dolne**     
  Zostanie wyświetlone powiadomienie został dodany na końcu obsługę systemu Android 4.3 i niżej. Aby uzyskać więcej informacji, zobacz [powiadomienia](#notices).
  <!--1171126, 1326920 -->     

- **Powiadamia użytkowników końcowych w informacjach urządzenia są widoczne na zarejestrowanych urządzeniach**     
  Dodajemy **typ własności** do ekranu szczegóły urządzenia na wszystkie aplikacje portalu firmy. Informacje te pozwalają użytkownikom dowiedzieć się więcej o ochronie prywatności bezpośrednio z [informacjach można wyświetlić firmie?](https://docs.microsoft.com/intune-user-help/what-info-can-your-company-see-when-you-enroll-your-device-in-intune) artykułu. To ulepszenie wprowadza we wszystkich aplikacjach Portal firmy w najbliższej przyszłości. Wprowadziliśmy tę funkcję dla systemu iOS w [września](https://docs.microsoft.com/intune/whats-new#week-of-september-11-2017). 
  <!--1165314-->     



## <a name="september-2017"></a>2017 września

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune     

- **Odśwież akcja dodaje do aplikacji Portal firmy dla systemu Windows 10**    
    Aplikacja Portal firmy dla systemu Windows 10 umożliwia odświeżanie danych w aplikacji, przenosząc albo odświeżyć lub na pulpitach, naciskając klawisz F5.
    <!-- 1132468 -->     

- **Powiadamia użytkowników końcowych, jakie informacje o urządzeniu są widoczne dla systemu iOS**   
    Dodaliśmy **typ własności** do ekranu szczegóły urządzenia w aplikacji Portal firmy dla systemu iOS. Tych informacji umożliwia użytkownikom dowiedzieć się więcej o ochronie prywatności bezpośrednio z usługi Intune dokumentów użytkownika końcowego. Mogą one również znaleźć te informacje na ekranie informacje. 
    <!--739894-->    

- **Łatwiejsze do zrozumienia właściwej dla aplikacji Portal firmy dla systemu Android**   
    Proces rejestracji w aplikacji Portal firmy dla systemu Android został uproszczony na nowy tekst w celu ułatwienia dla użytkowników końcowych zarejestrowania. Jeśli masz dokumentacji rejestrowania niestandardowego, należy zaktualizować go, aby uwzględnić nowe ekrany. Przykładowe obrazy można znaleźć w naszych [aktualizacje interfejsu użytkownika dla aplikacji użytkownika końcowego Intune](https://docs.microsoft.com/intune/whats-new-app-ui#week-of-september-11-2017) strony.
    <!---1396349-->    

- **Zezwalaj na zasady dodane do systemu Windows Information Protection aplikacji Portal firmy dla systemu Windows 10**    
    Aplikacja Portal firmy dla systemu Windows 10 została zaktualizowana do obsługi systemu Windows informacji ochrony (pracy w toku). Aplikację można dodać do pracy w toku Zezwalaj na zasady. Dzięki tej zmianie aplikacji nie ma już ma zostać dodany do **wykluczone** listy. 

    Tylko jeden element konfiguracji pracy w toku mogą być dostarczane na urządzeniu. Jeśli dwa elementy konfiguracji pracy w toku są przeznaczone do tego samego urządzenia, zastosowanie żadne zasady pracy w toku.
    <!-- 677129 -->    

- **Powiadomienie o pomocy technicznej dodane dla systemu iOS 8.0 zakończeniu**    
    Zostanie wyświetlone powiadomienie została dodana do zakończenia wsparcia dla systemu iOS 8.0. Aby uzyskać więcej informacji, zobacz [powiadomienia](#notices).



## <a name="august-2017"></a>2017 sierpnia

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune     

- **Nowe zalogowany środowisko dla użytkowników portalu firmy Android i użytkownikom zasady ochrony aplikacji**    
  Użytkownicy końcowi mogą teraz przeglądać aplikacje, zarządzać urządzeniami i wyświetlić kontakt z działem IT informacje przy użyciu aplikacji Portal firmy dla systemu Android bez rejestrowania swoich urządzeń z systemem Android. Ponadto jeśli już użytkownik końcowy używa aplikacji są chronione przez zasady aplikacji usługi Intune i uruchamia Portal firmy dla systemu Android, użytkownik końcowy nie będzie już otrzymywać monit o zarejestrowanie urządzenia.
  <!-- 621669 -->



## <a name="july-2017"></a>2017 lipca

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune

- **Koniec Obsługa powiadomienia dodane dla systemów Android i Windows Phone**    
    Nowe powiadomienia zostały dodane w celu obsługi wersji systemów Android i Windows Phone. Aby uzyskać więcej informacji, zobacz [powiadomienia](#notices).


### <a name="new-in-configuration-manager-current-branch"></a>Nowe w programie Configuration Manager (wersji current branch)

Następujące funkcje były wcześniej dostępne w wersjach Configuration Manager Technical Preview. Te funkcje są teraz dostępne w przypadku hybrydowych wdrożeń z usługi Intune i program Configuration Manager (wersji current branch) wersja 1706.

- [Powierzyć obsługę Entrust urzędów certyfikacji](/sccm/core/get-started/capabilities-in-technical-preview-1706#support-for-entrust-certification-authorities)
- [Nowe ustawienia zasad zarządzania aplikacjami mobilnymi](/sccm/core/plan-design/changes/whats-new-in-version-1706#new-mobile-application-management-policy-settings)
- [Aktualizacje w systemie Android for Work Konfiguracja udostępniania](/sccm/core/plan-design/changes/whats-new-in-version-1706#updates-to-android-for-work-sharing-configuration)
- [Nowe reguły zasad zgodności urządzenia](/sccm/core/plan-design/changes/whats-new-in-version-1706#new-device-compliance-policy-rules)
- [Nowe ustawienia konfiguracji dla urządzeń z systemem Windows 10, które nie są zarządzane przy użyciu klienta programu Configuration Manager](/sccm/core/plan-design/changes/whats-new-in-version-1706#new-configuration-settings-for-windows-10-devices-that-are-not-managed-with-the-configuration-manager-client)
- [Obsługa Cisco (IPsec) macOS profilów sieci VPN](/sccm/core/get-started/capabilities-in-technical-preview-1706#cisco-ipsec-support-for-macos-vpn-profiles)
- [Android i iOS ograniczenia rejestracji](/sccm/core/plan-design/changes/whats-new-in-version-1706#android-and-ios-enrollment-restrictions) 



## <a name="june-2017"></a>2017 czerwca

### <a name="new-in-microsoft-intune"></a>Nowość w usłudze Microsoft Intune

- **Zmienić urzędu zarządzania urządzeniami Przenośnymi**    
  Począwszy od programu Configuration Manager 1610 wersji, można zmienić urzędu zarządzania urządzeniami Przenośnymi bez konieczności kontaktowania się Support firmy Microsoft. Również nie trzeba wyrejestrować i Zarejestruj ponownie istniejących zarządzanych urządzeń. Aby uzyskać więcej informacji, zobacz [zmienić urzędu zarządzania urządzeniami Przenośnymi](/sccm/mdm/deploy-use/change-mdm-authority).

- **Zarządzane przeglądarki i aplikacji integracji serwera proxy**    
  Intune Managed Browser teraz można zintegrować z usługą serwera Proxy aplikacji usługi Azure AD, aby umożliwić użytkownikom dostęp do wewnętrznych witryn sieci web, nawet wtedy, gdy użytkownik pracuje zdalnie. Użytkownicy przeglądarki wprowadź adres URL witryny ulega zmianie, a w programie Managed Browser kieruje żądanie za pośrednictwem bramy sieci web serwera proxy aplikacji. Aby uzyskać więcej informacji, zobacz [dostępu do internetowego zarządzania przy użyciu zasad przeglądarki Managed](https://docs.microsoft.com/intune/app-configuration-managed-browser).

- **Aplikacja Portal firmy dla systemu Android ma teraz nowe środowisko użytkownika końcowego zasad ochrony aplikacji**  
  Na podstawie opinii klientów, firma Microsoft został zmodyfikowany w aplikacji Portal firmy dla systemu Android wyświetlić **dostępu firmy zawartości** przycisku. Celem jest, aby uniemożliwić użytkownikom końcowym niepotrzebnie przechodzi przez proces rejestracji, gdy potrzebują dostępu do aplikacji, które obsługuje zasady ochrony aplikacji z funkcją zarządzania aplikacjami mobilnymi usługi Intune. Te zmiany można wyświetlić na [nowości w aplikacji interfejsu użytkownika](https://docs.microsoft.com/intune/whats-new-app-ui) strony.

- **Nowa akcja menu można łatwo usunąć Portal firmy**  
  Na podstawie opinii użytkowników, aplikacja Portal firmy dla systemu Android została dodana nowa akcja menu zainicjować usuwanie Portal firmy z urządzenia. Ta akcja powoduje usunięcie urządzenia z zarządzania usługi Intune, aby aplikację można usunąć z urządzenia przez użytkownika. Te zmiany można wyświetlić na [nowości w aplikacji interfejsu użytkownika](https://docs.microsoft.com/intune/whats-new-app-ui) strony i w [dokumentacja użytkownika Android](https://docs.microsoft.com/intune-user-help/unenroll-your-device-from-intune-android).

- **Ulepszenia aplikacji synchronizację z usługą Windows Update twórców 10**  
  Aplikacja Portal firmy dla systemu Windows 10 teraz automatycznie inicjuje synchronizacji żądania instalacji aplikacji dla urządzeń z systemem Windows 10 twórców aktualizację (wersja 1703). To zachowanie zmniejsza problem Gaśnięcie silnika w stanie "Oczekiwanie synchronizacji" instaluje aplikację. Ponadto użytkownicy mogą ręcznie zainicjować synchronizację z poziomu aplikacji. Te zmiany można wyświetlić na [nowości w aplikacji interfejsu użytkownika](https://docs.microsoft.com/intune/whats-new-app-ui) strony.

- **Nowe środowisko z przewodnikiem dla Portal firmy dla systemu Windows 10**  
  Aplikacja Portal firmy dla systemu Windows 10 zawiera przewodnik obsługi wskazówki usługi Intune dla urządzeń, które nie zostały zidentyfikowane lub zarejestrowane. Nowe środowisko zawiera instrukcje krok po kroku prowadzi użytkownika przez proces rejestracji w usłudze Azure Active Directory (wymagane dla funkcji dostępu warunkowego) i rejestrowanie MDM (wymagane dla funkcji zarządzania urządzeniami). Przewodnik obsługi jest dostępna na stronie głównej portalu firmy. Jeśli użytkownicy nie wykonuj rejestracji i rejestracji, może nadal korzystać z aplikacji, ale występuje ograniczona funkcjonalność.

  Ta aktualizacja jest tylko widoczne na urządzeniach z systemem Windows 10 Anniversary Update (kompilacja 1607) lub nowszej. Te zmiany można wyświetlić na [nowości w aplikacji interfejsu użytkownika](https://docs.microsoft.com/intune/whats-new-app-ui) strony.

- **Ulepszenia kafelków aplikacji w aplikacji Portal firmy dla systemu iOS**  
  Zaktualizowaliśmy projekt kafelków aplikacji na stronie głównej znakowania koloru, ustawione przez Portal firmy. Aby uzyskać więcej informacji, zobacz [nowości w aplikacji interfejsu użytkownika](https://docs.microsoft.com/intune/whats-new-app-ui).

- **Selektor konta teraz dostępne dla aplikacji Portal firmy dla systemu iOS**  
  Jeśli użytkownicy urządzeń z systemem iOS Użyj pracy konto służbowe do logowania się do innych aplikacji firmy Microsoft, mogą widzieć naszego nowego konta selektora podczas logowania się do portalu firmy. Aby uzyskać więcej informacji, zobacz [nowości w aplikacji interfejsu użytkownika](https://docs.microsoft.com/intune/whats-new-app-ui).

### <a name="new-in-configuration-manager-technical-preview-1706"></a>Nowość w programie Configuration Manager Technical Preview 1706

- **Nowe ustawienia elementu konfiguracji systemu Windows**      
  Nowe elementy konfiguracji systemu Windows są dostępne w ramach kategorii ustawienia haseł, urządzenia, magazynu i Microsoft Edge. Aby uzyskać więcej informacji, zobacz [ustawienia elementu konfiguracji systemu Windows nowego](/sccm/core/get-started/capabilities-in-technical-preview-1706#new-windows-configuration-item-settings).
  <!-- 1354715 -->

- **Nowe reguły zasad zgodności urządzenia**   
  Można teraz skonfigurować nowe opcje zasad zgodności, które były wcześniej dostępne tylko w autonomicznej usługi Intune. Aby uzyskać więcej informacji, zobacz [ulepszenia zasad zgodności urządzenia](/sccm/core/get-started/capabilities-in-technical-preview-1706#new-device-compliance-policy-rules).

- **Android i iOS ograniczenia rejestracji**       
  Administratorzy można teraz określić, że użytkownicy nie można zarejestrować urządzeń osobistych Android lub iOS w środowisku hybrydowym. Ta akcja umożliwia limit zarejestrowanych urządzeń do predeclared, urządzenia należące do firmy lub zarejestrowane w usłudze Device Enrollment Program tylko urządzeń z systemem iOS. Aby uzyskać więcej informacji, zobacz [Android i iOS ograniczenia rejestracji](/sccm/core/get-started/capabilities-in-technical-preview-1706#android-and-ios-enrollment-restrictions).
  <!-- 1290826 -->

- **Obsługa Entrust urzędów certyfikacji**      
  Program Configuration Manager obsługuje teraz Entrust urzędów certyfikacji. Ta obsługa umożliwia dostarczania certyfikatów PFX na urządzeniach zarejestrowanych w programie Microsoft Intune.    
  <!-- 1350740 -->

  Podczas dodawania roli punktu rejestracji certyfikatu w programie Configuration Manager, można skonfigurować Entrust jako urząd certyfikacji. Podczas dodawania nowego profilu certyfikatu, który wystawia certyfikaty PFX, możesz wybrać Microsoft lub Entrust urzędu certyfikacji.

  **Znany problem**: W 1706 technical preview certyfikaty PFX nie są wystawiane na potrzeby urzędów certyfikacji firmy Microsoft. Ten problem nie ma wpływu na profilów SCEP lub importowanych certyfikatów PFX.

- **Obsługa Cisco (IPsec) macOS profilów sieci VPN**      
  Można utworzyć macOS profil sieci VPN z Cisco (IPsec) jako typ połączenia. Aby uzyskać więcej informacji, zobacz [tworzenie profilów sieci VPN](/sccm/mdm/deploy-use/create-vpn-profiles#create-vpn-profiles).
  <!-- 1321367 -->


## <a name="notices"></a>Powiadomienia

### <a name="company-portal-for-windows-81-and-windows-phone-81-moving-to-sustaining-mode"></a>Firmy, Portal dla Windows 8.1 i Windows Phone 8.1 przechodzenia do trybu utrzymywanie 
<!--1428681-->
*6 października 2017 r.*   
 
Począwszy od października 2017 aplikacji Portal firmy dla Windows 8.1 i Windows Phone 8.1 Przenieś utrzymywanie tryb. W tym trybie oznacza, że aplikacje i istniejące scenariusze, takie jak rejestracji i zgodności, nadal jest obsługiwana dla tych platform. Te aplikacje mogą nadal być dostępny do pobrania za pośrednictwem istniejącej wersji kanałów, takich jak Microsoft Store. 

Raz w utrzymywanie tryb, te aplikacje odbierać krytyczne aktualizacje zabezpieczeń. Nie dodatkowe aktualizacje i funkcje zostaną wydane dla tych aplikacji. Nowe funkcje zaleca się, zaktualizuj urządzenia do systemu Windows 10 lub Windows 10 Mobile. 

### <a name="end-of-support-for-ios-80"></a>Wsparcie dla systemu iOS 8.0 
<!---1164477--->
Zarządzane aplikacje i aplikacji Portal firmy dla systemu iOS wymagają iOS 9.0 lub nowszej, dostęp do zasobów firmy. Urządzenia, które nie są zaktualizowane przed września nie będą mogli uzyskać dostęp do portalu firmy lub aplikacji. 

### <a name="platform-support-reminder-windows-phone-81-mainstream-support-ended-july-11-2017"></a>Przypomnienie pomocy technicznej platformy: Windows Phone 8.1 dostępne podstawowe wsparcie zakończył 11 lipca 2017 r.
<!-- 1327781 -->
*11 lipca 2017 r.*

Platformy Windows Phone 8.1 osiągnął koniec dostępne podstawowe wsparcie. Obsługa komputerów Windows 8.1 nie jest w pełni funkcjonalne.

Nie ma żadnego wpływu natychmiastowego dla wszystkich urządzeń Windows Phone 8.1, który jest zarządzany przez usługę Intune, w tym tych urządzeń zarejestrowanych w hybrydowego zarządzania urządzeniami przenośnymi. Urządzenia zarejestrowane kontynuować pracę. Wszystkie zasady, konfiguracji i aplikacje nadal działać zgodnie z oczekiwaniami. Należy pamiętać, że nie ma żadnych ulepszenia przeznaczone dla platformy Windows Phone 8.1 w usłudze Intune i dla aplikacji Portal firmy systemu Windows Phone 8.1.

Zaleca się uaktualnienie kwalifikujących się urządzeń Windows Phone 8.1 do systemu Windows 10 Mobile z najwcześniej.  

### <a name="end-of-support-for-android-43-and-lower"></a>Wsparcie dla systemu Android 4.3 i dolne
<!---1171127--->
*6 lipca 2017 r.*

Zarządzane aplikacje i aplikacji Portal firmy dla systemu Android wymagają Android 4.4 lub wyższej dostęp do zasobów firmy. Urządzenia, które nie są zaktualizowane przed rozpoczęciem października nie będą mogli uzyskać dostęp do portalu firmy lub aplikacji. Grudnia wszystkie zarejestrowane urządzenia są życie wycofane grudnia, co spowoduje utratę dostępu do zasobów firmy. Jeśli używane są zasady ochrony aplikacji bez zarządzania urządzeniami Przenośnymi, aplikacje nie będą otrzymywać aktualizacje i jakości ich obsługi zmniejsza się wraz z upływem czasu.



## <a name="see-also"></a>Zobacz też

- [Hybrydowe zarządzanie urządzeniami Przenośnymi funkcje i powiadomienia](whats-new-hybrid-archive.md)
- [Nowości w oprogramowaniu MDM w programie System Center 2012 Configuration Manager](https://technet.microsoft.com/library/mt445560.aspx)
