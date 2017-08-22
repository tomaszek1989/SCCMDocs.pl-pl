---
title: Nowe w programie System Center Configuration Manager wersji 1602 | Dokumentacja firmy Microsoft
description: "Uzyskiwanie szczegółowych informacji dotyczących zmian i nowych możliwości wprowadzonych w wersji 1602 programu System Center Configuration Manager."
ms.custom: na
ms.date: 12/30/2016
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4021eca1-adfb-4e5a-adee-159263c29637
caps.latest.revision: "3"
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
ms.openlocfilehash: 9a548f43625a907173e7b967d26356bd80f1c5d9
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="what39s-new-in-version-1602-of-system-center-configuration-manager"></a>Jaki &#39; s nowego w wersji 1602 programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


Aktualizacji 1602 dla programu System Center Configuration Manager jest tylko dostępna jako aktualizacja w konsoli dla zainstalowanych wcześniej lokacji w wersji 1511. Wersja 1511 to początkowa, wersji linii bazowej, używaną do zainstalowania nowych lokacji programu Configuration Manager.  


> [!TIP]  
>  Dowiedz się więcej o:  
>   
>   -   [Instalowanie nowej lokacji](/sccm/core/servers/deploy/install) (przy użyciu wersji linii bazowej, np. 1511)  
>   -   [Instalowanie aktualizacji w lokacjach](/sccm/core/servers/manage/updates) (np. aktualizacji 1602)  

 Poniższe sekcje zawierają szczegółowe informacje dotyczące zmian i nowych możliwości wprowadzonych w wersji 1602 programu Configuration Manager.  

## <a name="site-infrastructure"></a>Infrastruktura lokacji  

###  <a name="bkmk_UpgradeOS"></a>Uaktualnienie w miejscu systemu operacyjnego serwerów lokacji, z systemem Windows Server 2008 R2  
 Lokacje programu Configuration Manager, na których jest uruchomiona wersja 1602 lub nowszej obsługują uaktualnienie w miejscu lokacji serwery systemu operacyjnego z systemu Windows Server 2008 R2 do systemu Windows Server 2012 R2.  

> [!WARNING]  
>  Przed uaktualnieniem do systemu Windows Server 2012 R2, należy odinstalować usługi WSUS 3.2 z serwera.  
>   
>  Aby uzyskać informacje o tym krytycznym kroku, zobacz sekcję "Nowe i zmienione funkcje" w [Omówienie usług Windows Server Update Services](https://technet.microsoft.com/library/hh852345.aspx), w dokumentacji systemu Windows Server.  

 Aby uaktualnić serwer, wykorzystywane procedury uaktualniania systemu Windows Server 2012 R2. Nie trzeba uruchomić przywracania serwera lokacji po uaktualnieniu programu Configuration Manager. Informacje dotyczące procedur uaktualniania można znaleźć w temacie [Opcje uaktualniania do systemu Windows Server 2012 R2](https://technet.microsoft.com/library/dn303416.aspx) w dokumentacji systemu Windows Server.  

###  <a name="bkmk_AOAG"></a>Grupy dostępności AlwaysOn programu SQL Server  
 Użyj grup dostępności AlwaysOn programu SQL Server do hostowania bazy danych lokacji w lokacjach głównych i centralnej lokacji administracyjnej jako rozwiązania wysokiej dostępności i odzyskiwania po awarii.  

 Aby uzyskać więcej informacji, zobacz [AlwaysOn programu SQL Server dla bazy danych lokacji o wysokiej dostępności programu System Center Configuration Manager](../../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md).  

## <a name="operating-system-deployment"></a>Wdrożenie systemu operacyjnego  

### <a name="windows-10-servicing"></a>Obsługa systemu Windows 10  
 Następujące ulepszenia obsługi systemu Windows 10 zostały dodane w programie Configuration Manager w wersji 1602:  

-   Nowe opcje filtrowania są dostępne dla planów, które umożliwiają filtrowanie dla obsługi **języka**, **wymagane**, i **tytuł**. Tylko uaktualnienia zgodne z określonymi kryteriami zostaną dodane do skojarzonego wdrożenia.  

-   Po wybraniu **uaktualnień** synchronizacji aktualizacji oprogramowania klasyfikacji, wyświetlane jest ostrzeżenie. To ostrzeżenie informujące, że [poprawkę 3095113](https://support.microsoft.com/kb/3095113) dla systemu Windows Server Update Services (WSUS) 4.0 jest wymagany, zanim można pomyślnie zsynchronizować aktualizacje oprogramowania i obsługi systemu Windows 10 działała poprawnie. W komunikacie ostrzegawczym można przejść do skojarzonego artykułu bazy wiedzy.  

-   10 systemu Windows dostępne uaktualnienia są teraz wyświetlane tylko w **obsługi systemu Windows 10** \ **wszystkie aktualizacje systemu Windows 10** węzła konsoli programu Configuration Manager. Te aktualizacje nie są już wyświetlane w **aktualizacji oprogramowania** \ **wszystkie aktualizacje oprogramowania** węzła konsoli.  

-   Plan obsługi jest uznawana za wdrożenie wysokiego ryzyka oraz **Wybieranie kolekcji** wyświetlane tylko kolekcje niestandardowe zgodne z ustawieniami weryfikacji wdrożenia skonfigurowanymi we właściwościach lokacji. Aby uzyskać więcej informacji, zobacz [Ustawienia zarządzania wdrożeniami o wysokim ryzyku dla programu System Center Configuration Manager](../../../protect/understand/settings-to-manage-high-risk-deployments.md).  

-   Użytkownicy, którzy teraz uruchomić pakiet uaktualnienia systemu Windows 10 komunikat że będą uaktualniać ich systemu operacyjnego.  

## <a name="application-management"></a>Zarządzanie aplikacjami  

### <a name="ios-app-configuration-policies"></a>Zasady konfiguracji aplikacji systemu iOS  
 Użyj zasad konfiguracji aplikacji programu Configuration Manager umożliwiają określanie wartości ustawień, które mogą być wymagane, jeśli użytkownik uruchamia aplikację systemu iOS. Na przykład aplikacja może wymagać użytkownikowi określić niestandardowy numer portu, języka, ustawień zabezpieczeń i ustawień oznaczania marką (takich jak logo firmy). Jeśli te ustawienia są niepoprawnie wprowadzona, to zwiększyć obciążenie działu pomocy technicznej i zwolnić rozpowszechnianie nowych aplikacji.  

 Zasady konfiguracji aplikacji mogą pomóc wyeliminować te problemy, umożliwiając wdrażanie tych ustawień do użytkowników w zasadach, zanim uruchomią oni aplikację. Ustawienia są następnie określane automatycznie, a użytkownik nie musi wykonywać żadnych czynności. Aby uzyskać więcej informacji, zobacz [Konfigurowanie aplikacji systemu iOS przy użyciu zasad konfiguracji aplikacji w programie System Center Configuration Manager](../../../apps/deploy-use/configure-ios-apps-with-app-configuration-policies.md).  

### <a name="manage-volume-purchased-ios-apps"></a>Zarządzanie aplikacjami systemu iOS nabytymi w ramach zakupów zbiorczych  
 Menedżer konfiguracji ułatwiają wdrażanie i zarządzanie aplikacjami zakupionymi zbiorczo w od firmy Apple Volume Purchase Program (VPP). Configuration Manager importuje informacje o licencji ze sklepu z aplikacjami i śledzenie, ile licencji jest używanych.  

 Aby uzyskać więcej informacji, zobacz [Zarządzanie zbiorczo zakupionymi aplikacjami systemu iOS z System Center Configuration Manager](../../../apps/deploy-use/manage-volume-purchased-ios-apps.md).  

### <a name="automatic-creation-of-office-mobile-apps"></a>Automatyczne tworzenie aplikacji mobilnych pakietu Office  
 Podczas aktualizacji do wersji 1602 z 1511 programu Configuration Manager automatycznie tworzy następujące aplikacje mobilne Microsoft Office dla systemów Android i iOS:  

-   Program Microsoft Word  

-   Program Microsoft Excel  

-   Program Microsoft PowerPoint  

-   Microsoft OneDrive  

-   Microsoft OneNote (tylko iOS)  

-   Program Microsoft Outlook  

Dostępne są te aplikacje w **aplikacji** węzła konsoli programu Configuration Manager.  

 Aby uzyskać więcej informacji na temat wdrażania aplikacji, zobacz [sposobu wdrażania aplikacji w programie System Center Configuration Manager](../../../apps/deploy-use/deploy-applications.md).  

## <a name="software-updates"></a>Aktualizacje oprogramowania  

### <a name="manage-office-365-client-updates"></a>Zarządzanie aktualizacjami klienta usługi Office 365  
 System Center Configuration Manager ma możliwość zarządzania aktualizacjami klienta usługi Office 365 za pomocą przepływu pracy zarządzania aktualizacjami oprogramowania. Aby uzyskać więcej informacji, zobacz [zarządzania usługi Office 365 ProPlus aktualizacji w programie System Center Configuration Manager](/sccm/sum/deploy-use/manage-office-365-proplus-updates).  

## <a name="compliance-settings"></a>Ustawienia zgodności  

### <a name="compliance-settings-for-devices-running-windows-10-team"></a>Ustawienia zgodności dla urządzeń z systemem Windows 10 Team  
 Nowe ustawienia zostały dodane do **Windows 8.1 i Windows 10** elementu konfiguracji. Te ustawienia ułatwiają kontrolowanie urządzeń z systemem Windows 10 Team, takich jak urządzenia Surface Hub.  

 Aby uzyskać więcej informacji, zobacz [jak utworzyć elementy konfiguracji dla urządzeń Windows 8.1 i Windows 10 zarządzanych bez klienta programu System Center Configuration Manager](../../../compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md).  

### <a name="kiosk-mode-settings-for-android-samsung-knox-standard-devices"></a>Ustawienia trybu kiosku dla urządzeń z systemem Android Samsung KNOX Standard  
 Tryb kiosku umożliwia blokowanie urządzenia, tak aby tylko niektóre funkcje działają. Na przykład można zezwolić na uruchamianie tylko określonej zarządzanej aplikacji przez użytkownika na urządzeniu, lub można wyłączyć przyciski regulacji głośności na urządzeniu. Można użyć tych ustawień dla modeli pokazowych urządzenia lub urządzenia służącego do wykonywania tylko jednej funkcji, takich jak urządzeń w punkcie sprzedaży. W programie Configuration Manager można teraz określić ustawienia trybu kiosku dla urządzenia Samsung KNOX Standard.  

 Aby uzyskać więcej informacji, zobacz [jak utworzyć elementy konfiguracji dla urządzeń z systemami Android i Samsung KNOX Standard zarządzanych bez klienta programu System Center Configuration Manager](../../../compliance/deploy-use/create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client.md).  

## <a name="conditional-access"></a>Dostęp warunkowy  

### <a name="conditional-access-for-pcs-managed-by-system-center-configuration-manager"></a>Dostęp warunkowy dla komputerów zarządzanych przez program System Center Configuration Manager  
 Przed tą wersją Konfigurowanie dostępu warunkowego na komputerze, do komputera musiały być zarejestrowane w usłudze Intune albo muszą być przyłączone do domeny komputera. Począwszy od aktualizacji 1602, dostęp warunkowy dla komputerów zarządzanych przez program System Center Configuration manager jest obsługiwana. W przypadku komputerów zarządzanych przez program System Center Configuration Manager można ograniczyć dostęp do usługi Exchange Online i SharePoint Online tylko do urządzeń, które są zgodne z ustawionymi zasadami zgodności.  

 Aby uzyskać więcej informacji, zobacz [zarządzanie dostępem do usług O365 dla komputerów zarządzanych przez program System Center Configuration Manager](../../../protect/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm.md).  

### <a name="restricting-access-based-on-the-health-of-devices"></a>Ograniczanie dostępu na podstawie kondycji urządzeń  
 Można teraz ograniczyć dostęp do poczty e-mail i 0ffice 365 usługi na podstawie kondycji urządzeń zgłoszonej przez usługę zaświadczania o kondycji. Ponadto urządzenia zarządzane przez usługę Intune są ujęte w raportach o kondycji urządzeń.  

 Nowa reguła zgodności, który służy do określenia, czy urządzeniu powinno być dozwolone, czy zablokowała dostęp na podstawie stanu kondycji funkcjami, konsoli programu Configuration Manager. Aby uzyskać szczegółowe informacje o usłudze zaświadczania o kondycji i sposobie zgłaszania kondycji urządzeń w usłudze Intune, zobacz [zaświadczania o kondycji programu System Center Configuration Manager](../../../core/servers/manage/health-attestation.md).  

### <a name="new-compliance-policy-rules"></a>Nowe reguły zasad zgodności  
 Nowe reguły zasad zgodności, takie jak aktualizacje automatyczne i wymaganie hasła do odblokowania urządzeń, zostały dodane do obsługi lepsze wymagań w zakresie zabezpieczeń.

 Aby uzyskać więcej informacji, zobacz [zasady zgodności urządzeń w programie System Center Configuration Manager](../../../protect/deploy-use/device-compliance-policies.md).  

### <a name="make-sure-enrolled-and-compliant-devices-always-have-access-to-exchange-on-premises"></a>Upewnij się, że zarejestrowane i zgodne urządzenia zawsze miały dostęp do lokalnego programu Exchange  
 Jeśli zaznaczysz poniższą opcję, urządzenia zarejestrowane w usłudze Intune i zgodne z zasadami zgodności, mogą uzyskiwać dostęp do lokalnego programu Exchange: **Przesłonięcie reguły domyślnej — zawsze Zezwalaj zarejestrowanym w usłudze Intune i zgodnym urządzeniom na dostęp do lokalnego programu Exchange:**. Ta reguła jest dostępna na **strony Ogólne** z **warunkowego Kreatora konfiguracji zasad dostępu** dla lokalnego programu Exchange.

 Ta reguła zastępuje regułę domyślną, co oznacza, że nawet jeśli domyślna reguła jest ustawiona na kwarantannę lub blokowanie dostępu, zarejestrowane i zgodne urządzenia nadal będzie można uzyskać dostęp do lokalnego programu Exchange. Użyj tego ustawienia, aby zarejestrowane i zgodne urządzenia zawsze miały dostęp do poczty e-mail za pośrednictwem lokalnego programu Exchange.   

 Aby uzyskać szczegółowe wskazówki, zobacz [zarządzanie dostępem do poczty e-mail w programie System Center Configuration Manager](../../../protect/deploy-use/manage-email-access.md).  

## <a name="client-management"></a>Zarządzanie klientami  

### <a name="client-online-status"></a>Stan online klienta  
 Nowy stan dla klientów jest dostępna do monitorowania, jeśli komputer jest w trybie online lub nie. Komputer jest uznawany za online, jeśli jest ona połączona z przypisanym punkcie zarządzania. Aby wskazać, że komputer jest w trybie online, klient wysyła komunikaty typu ping do punktu zarządzania. Jeśli punkt zarządzania nie odbierze komunikatu po 5 minutach, klient jest traktowany jako w trybie offline.  

 Aby uzyskać więcej informacji, zobacz [jak monitorować klientów w programie System Center Configuration Manager](../../../core/clients/manage/monitor-clients.md).  

### <a name="refresh-pc-machine-and-user-policy-from-software-center"></a>Odświeżanie zasad użytkownika i komputera PC z Centrum oprogramowania  
 Nowa opcja **zasady synchronizacji**, został dodany do **opcje** > **Konserwacja komputera** w Centrum oprogramowania, który powoduje odświeżenie jej programu Configuration Manager na komputerze zasad użytkownika i komputera.  

### <a name="software-center-branding-changes"></a>Zmiany znakowania programu Centrum oprogramowania  
 Można zmienić kolor, nazwę organizacji i ikony wyświetlane w programie Software Center. Te ustawienia są stosowane zgodnie z następującymi zasadami:  

- Jeśli nie zainstalowano roli serwera lokacji punktu witryny sieci Web katalogu aplikacji, a następnie Centrum oprogramowania wyświetlana nazwa organizacji określona w **Agent komputera** klienta nosi nazwę **nazwa organizacji wyświetlana w Centrum oprogramowania**.  

- Po zainstalowaniu roli serwera lokacji punktu witryny sieci Web katalogu aplikacji programu Software Center wyświetla nazwę organizacji i kolor określone we właściwościach roli serwera lokacji punktu witryny sieci Web katalogu aplikacji.  

- Jeśli subskrypcję Microsoft Intune jest skonfigurowana i podłączone do środowiska programu Configuration Manager, programu Software Center wyświetla nazwę organizacji, kolor i logo firmy określone we właściwościach subskrypcji usługi Intune.  

### <a name="health-attestation"></a>Zaświadczanie o kondycji  
 Administratorzy mogą wyświetlać stan zaświadczania o kondycji urządzenia systemu Windows 10 w konsoli programu Configuration Manager. To jest dostępna dla programu Configuration Manager, a także programu Configuration Manager w usłudze Microsoft Intune. Zaświadczanie o kondycji urządzenia umożliwia administratorowi upewnienie się, że komputery klienckie mają włączone następujące godne zaufania konfiguracje systemu BIOS, modułu TPM i oprogramowania rozruchowego:  

-   Usługa wczesnej ochrony przed złośliwym oprogramowaniem  

-   Funkcja BitLocker  

-   Bezpieczny rozruch  

-   Integralność kodu  

Aby uzyskać więcej informacji, zobacz [zaświadczania o kondycji programu System Center Configuration Manager](../../../core/servers/manage/health-attestation.md).  

### <a name="improvements-to-endpoint-protection-antimalware-settings"></a>Udoskonalenia ustawień ochrony przed złośliwym kodem programu Endpoint Protection  
 1602 dodano następujące nowe ustawienia w zasadach ochrony przed złośliwym kodem Endpoint Protection dla usługi Windows Defender:  

-   Ochrona w czasie rzeczywistym: Blokuj potencjalnie niechciane aplikacje podczas pobierania przed instalacją.  

-   Ustawienia skanowania: Skanuj zamapowane dyski sieciowe podczas pełnego skanowania.  

-   Przykładowy automatycznej ustawień przesyłania plików:  

     Aparat ochrony przed złośliwym kodem może prosić o przesyłanie plików próbek do firmy Microsoft w celu dalszej analizy. Domyślnie przed wysłaniem takich próbek zawsze wyświetlany jest monit. Administratorzy mogą teraz zarządzać następującymi ustawieniami w celu skonfigurowania tego zachowania:  

    -   Zaawansowane: Włącz przesyłanie plików próbek automatycznego pomóc firmie Microsoft w określeniu, czy konkretne wykryte elementy są złośliwe.  

    -   Zaawansowane: Zezwalaj użytkownikom na modyfikowanie ustawień przesyłania automatyczne przykładowych plików.  

    Ponadto w sekcji "Ustawienia wykluczania" zasad ochrony przed złośliwym kodem ochrony punktu końcowego, istniejące **wykluczyć pliki i foldery** ustawienie teraz umożliwia teraz wykluczanie urządzeń.  

Aby uzyskać więcej informacji, zobacz [tworzenie i wdrażanie zasad ochrony przed złośliwym kodem programu Endpoint Protection w programie System Center Configuration Manager](../../../protect/deploy-use/endpoint-antimalware-policies.md).  

## <a name="mobile-device-management"></a>Zarządzanie urządzeniami przenośnymi  

### <a name="ios-activation-lock"></a>Blokady aktywacji systemu iOS  
 Configuration Manager ułatwia zarządzanie blokadą aktywacji, funkcja Znajdź systemu iOS aplikacja Mój iPhone dla systemu iOS 7.1 i nowszym. Blokada aktywacji jest włączana automatycznie w przypadku użycia aplikacji Znajdź mój iPhone na urządzeniu. Jeśli ta funkcja została włączona, należy podać identyfikator Apple ID i hasło użytkownika, aby można było wykonać następujące czynności:  

-   Wyłączenie aplikacji Znajdź mój iPhone.  

-   Usunięcie z urządzenia.  

-   Ponownego uaktywnienia urządzenia.  

Menedżer konfiguracji może wysłać żądanie stanu blokady aktywacji na nadzorowanych i nienadzorowanych urządzeniach z systemem iOS 7.1 lub nowszy. W przypadku urządzeń nadzorowanych programu Configuration Manager może pobrać kod obejścia blokady aktywacji i wystawić go bezpośrednio na urządzeniu.  

 Aby uzyskać więcej informacji, zobacz [Łatwiejsza ochrona urządzeń z blokady aktywacji obejścia w programie System Center Configuration Manager dla systemu iOS](/sccm/mdm/deploy-use/manage-ios-activation-lock).  

### <a name="monitor-terms-and-conditions-deployments"></a>Monitorować wdrożenia warunków i postanowień  
 Możesz monitorować wdrożenia warunków i postanowień w konsoli programu Configuration Manager.  

 Wybierz wdrożenie warunków i postanowień, z listy wdrożeń. Obszar podsumowania przedstawia następujące statystyki:  

-   **Zgodne**: Użytkownicy zaakceptowali najnowszą wersję warunków i postanowień.  

-   **Błąd**  

-   **Niezgodne**: Użytkownicy zaakceptowali wersję warunków i postanowień, ale nie najnowszą wersję.  

-   **Nieznany**: Użytkownicy nigdy nie zaakceptowali warunków i postanowień, w tym użytkownicy bez zarejestrowanego urządzenia.  
