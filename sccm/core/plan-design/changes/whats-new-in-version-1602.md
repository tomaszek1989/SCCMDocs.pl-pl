---
title: Nowe w programie System Center Configuration Manager wersji 1602 | Dokumentacja firmy Microsoft
description: "Uzyskiwanie szczegółowych informacji dotyczących zmian oraz nowe funkcje wprowadzone w wersji 1602 programu System Center Configuration Manager."
ms.custom: na
ms.date: 12/30/2016
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4021eca1-adfb-4e5a-adee-159263c29637
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 9a548f43625a907173e7b967d26356bd80f1c5d9
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="what39s-new-in-version-1602-of-system-center-configuration-manager"></a>Co &#39; s nowe w wersji 1602 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


Zaktualizuj 1602 dla programu System Center Configuration Manager jest dostępna jako aktualizacja w konsoli dla witryn zainstalowane wcześniej, których jest uruchomiona wersja 1511 tylko. Wersja 1511 jest początkowej, wersję linii bazowej, którą można użyć do zainstalowania nowej lokacji programu Configuration Manager.  


> [!TIP]  
>  Więcej informacji na temat:  
>   
>   -   [Instalowanie nowych witryn](/sccm/core/servers/deploy/install) (przy użyciu wersji linii bazowej, takich jak 1511)  
>   -   [Instalowanie aktualizacji w lokacjach](/sccm/core/servers/manage/updates) (takich jak zaktualizować 1602)  

 Poniższe sekcje zawierają szczegółowe informacje dotyczące zmiany i nowe możliwości wprowadzona w wersji 1602 programu Configuration Manager.  

## <a name="site-infrastructure"></a>Infrastruktura lokacji  

###  <a name="bkmk_UpgradeOS"></a>Uaktualnij system operacyjny serwerów lokacji, z systemem Windows Server 2008 R2, w miejscu  
 Lokacji programu Configuration Manager, na których jest uruchomiona wersja 1602 lub nowszej obsługuje uaktualnienia w miejscu lokacji serwery systemu operacyjnego z systemem Windows Server 2008 R2 do systemu Windows Server 2012 R2.  

> [!WARNING]  
>  Przed uaktualnieniem do systemu Windows Server 2012 R2, należy odinstalować WSUS 3.2 z serwera.  
>   
>  Informacji dotyczących tego kroku krytyczne, zobacz sekcję "Nowe i zmienione funkcje" w [Omówienie usług Windows Server Update](https://technet.microsoft.com/library/hh852345.aspx), w dokumentacji systemu Windows Server.  

 Aby uaktualnić serwer, użyj procedury uaktualniania systemu Windows Server 2012 R2. Nie trzeba uruchomić przywracanie serwera lokacji po uaktualnieniu programu Configuration Manager. Informacje dotyczące procedur uaktualniania można znaleźć w temacie [Opcje uaktualniania do systemu Windows Server 2012 R2](https://technet.microsoft.com/library/dn303416.aspx) w dokumentacji systemu Windows Server.  

###  <a name="bkmk_AOAG"></a>Grupy dostępności AlwaysOn programu SQL Server  
 Użyj grupy dostępności AlwaysOn programu SQL Server do obsługi bazy danych lokacji w lokacji głównej i centralnej lokacji administracyjnej jako rozwiązań wysokiej dostępności i odzyskiwania po awarii.  

 Aby uzyskać szczegółowe informacje, zobacz [AlwaysOn programu SQL Server dla bazy danych lokacji wysokiej dostępności dla programu System Center Configuration Manager](../../../core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database.md).  

## <a name="operating-system-deployment"></a>Wdrożenie systemu operacyjnego  

### <a name="windows-10-servicing"></a>Obsługa systemu Windows 10  
 Dodano następujące ulepszenia obsługi systemu Windows 10 w 1602 wersji programu Configuration Manager:  

-   Nowe opcje filtrowania są dostępne do obsługi planów, które umożliwiają filtrowanie **języka**, **wymagane**, i **tytuł**. Tylko uaktualnienia zgodne z określonymi kryteriami zostaną dodane do skojarzonego wdrożenia.  

-   Po wybraniu **uaktualnień** klasyfikacji dla oprogramowania aktualizuje synchronizacji, zostanie wyświetlone ostrzeżenie. To ostrzeżenie informuje, że [poprawkę 3095113](https://support.microsoft.com/kb/3095113) dla systemu Windows Server Update Services (WSUS) 4.0 jest wymagany, zanim będzie można pomyślnie synchronizować aktualizacje oprogramowania, a także obsługi systemu Windows 10 do poprawnego działania. Z z komunikatem ostrzegawczym, można przejść do artykułu bazy wiedzy skojarzone.  

-   Dostępne systemu Windows 10 teraz uaktualnia tylko do wyświetlania w **obsługi systemu Windows 10** \ **wszystkie aktualizacje składników systemu Windows 10** węzeł konsoli programu Configuration Manager. Aktualizacje te nie są już wyświetlane w **aktualizacji oprogramowania** \ **wszystkie aktualizacje oprogramowania** węzeł konsoli.  

-   Planowanie obsługi jest uznawany za wdrożenie o wysokim ryzyku i **Wybieranie kolekcji** tylko kolekcji niestandardowych, które spełniają ustawienia weryfikacji wdrażania, które są skonfigurowane we właściwościach lokacji jest wyświetlana w oknie. Aby uzyskać więcej informacji, zobacz [Ustawienia zarządzania wdrożeniami o wysokim ryzyku dla programu System Center Configuration Manager](../../../protect/understand/settings-to-manage-high-risk-deployments.md).  

-   Użytkownicy, którzy teraz uruchomić pakiet uaktualnienia systemu Windows 10 komunikat czy one zaktualizuje ich systemu operacyjnego.  

## <a name="application-management"></a>Zarządzanie aplikacjami  

### <a name="ios-app-configuration-policies"></a>Zasady konfiguracji aplikacji systemu iOS  
 Użycie zasad konfiguracji aplikacji programu Configuration Manager do dostarczenia ustawień, które mogą być wymagane, gdy użytkownik uruchomi aplikację iOS. Na przykład aplikacja może wymagać użytkownikowi na określenie numeru portu niestandardowego języka, ustawienia zabezpieczeń i ustawienia znakowania (np. logo firmy). Te ustawienia są niepoprawnie wprowadzone, to zwiększenia obciążeń do pomocy technicznej, a także spowolnić przyjęcia nowych aplikacji.  

 Zasady konfiguracji aplikacji może pomóc wyeliminować te problemy, umożliwiając wdrożenia tych ustawień dla użytkowników w zasadach, zanim uruchomienia aplikacji. Ustawienia są następnie udostępniane automatycznie, a użytkownik nie trzeba podejmować żadnych działań. Aby uzyskać szczegółowe informacje, zobacz [skonfigurowanie aplikacji systemu iOS z zasady konfiguracji aplikacji w programie System Center Configuration Manager](../../../apps/deploy-use/configure-ios-apps-with-app-configuration-policies.md).  

### <a name="manage-volume-purchased-ios-apps"></a>Zarządzanie aplikacjami systemu iOS nabytymi w ramach zakupów zbiorczych  
 Menedżer konfiguracji ułatwiają wdrażanie i zarządzanie aplikacjami, zakupionym w woluminie z VPP firmy Apple woluminu zakupu programu (). Program Configuration Manager importuje informacje o licencji ze sklepu z aplikacjami i śledzi, ile licencji jest używany.  

 Aby uzyskać szczegółowe informacje, zobacz [zarządzania aplikacjami iOS kupionymi woluminu z System Center Configuration Manager](../../../apps/deploy-use/manage-volume-purchased-ios-apps.md).  

### <a name="automatic-creation-of-office-mobile-apps"></a>Automatyczne tworzenie aplikacji mobilnych pakietu Office  
 Po uaktualnieniu do wersji 1602 z 1511 programu Configuration Manager automatycznie tworzy następujące aplikacje mobilne Microsoft Office dla systemów Android i iOS:  

-   Program Microsoft Word  

-   Program Microsoft Excel  

-   Program Microsoft PowerPoint  

-   Microsoft OneDrive  

-   Program Microsoft OneNote (tylko iOS)  

-   Program Microsoft Outlook  

Można znaleźć tych aplikacji w **aplikacji** węzeł konsoli programu Configuration Manager.  

 Aby uzyskać więcej informacji dotyczących wdrażania aplikacji, zobacz [jak wdrażać aplikacje z System Center Configuration Manager](../../../apps/deploy-use/deploy-applications.md).  

## <a name="software-updates"></a>Aktualizacje oprogramowania  

### <a name="manage-office-365-client-updates"></a>Zarządzanie aktualizacjami klienta usługi Office 365  
 System Center Configuration Manager ma możliwość zarządzania aktualizacji klienta usługi Office 365 za pomocą przepływu pracy zarządzania aktualizacji oprogramowania. Aby uzyskać więcej informacji, zobacz [zarządzania Office 365 ProPlus aktualizacji z System Center Configuration Manager](/sccm/sum/deploy-use/manage-office-365-proplus-updates).  

## <a name="compliance-settings"></a>Ustawienia zgodności  

### <a name="compliance-settings-for-devices-running-windows-10-team"></a>Ustawienia zgodności dla urządzeń z systemem Windows 10 Team  
 Dodano nowe ustawienia **Windows 8.1 i Windows 10** elementu konfiguracji. Te ustawienia ułatwiają kontroli urządzeń z systemem Windows 10 Team, takich jak urządzenia Surface Hub.  

 Aby uzyskać szczegółowe informacje, zobacz [tworzenie elementów konfiguracji dla urządzeń Windows 8.1 i Windows 10 zarządzane bez klienta programu System Center Configuration Manager](../../../compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md).  

### <a name="kiosk-mode-settings-for-android-samsung-knox-standard-devices"></a>Ustawienia trybu kiosku dla urządzeń z systemem Android Samsung KNOX Standard  
 Tryb kiosku służy do blokowania urządzenia tak, aby pracować tylko niektórych funkcji. Na przykład można zezwolić na urządzeniu do uruchamiania tylko jednej aplikacji zarządzanych, który określisz lub można wyłączyć przyciski regulacji głośności na urządzeniu. Można użyć tych ustawień dla modeli pokazowych urządzenia lub dla urządzeń przeznaczonych do wykonywania tylko jednej funkcji, takich jak urządzenia w punktach sprzedaży. W programie Configuration Manager można teraz określić ustawienia trybu kiosku dla urządzeń Samsung KNOX Standard.  

 Aby uzyskać szczegółowe informacje, zobacz [tworzenie elementów konfiguracji dla urządzeń Android i Samsung KNOX Standard zarządzane bez klienta programu System Center Configuration Manager](../../../compliance/deploy-use/create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client.md).  

## <a name="conditional-access"></a>Dostęp warunkowy  

### <a name="conditional-access-for-pcs-managed-by-system-center-configuration-manager"></a>Dostęp warunkowy dla komputerów zarządzanych przez program System Center Configuration Manager  
 Wstecz, aby tej wersji do ustawiania dostępu warunkowego dla komputera, komputer musiała zostać zarejestrowane w usłudze Intune albo muszą być w przypadku komputera przyłączonego do domeny. Począwszy od aktualizacji 1602 dostępu warunkowego dla komputerów zarządzanych przez program System Center Configuration manager jest obsługiwana. Na komputerach, które są zarządzane przez program System Center Configuration Manager można ograniczyć dostęp do usługi Exchange Online i usługi SharePoint Online tylko do urządzeń, które są zgodne z zasadami zgodności, które można ustawić.  

 Aby uzyskać szczegółowe informacje, zobacz [zarządzanie dostępem do usługi O365 dla komputerów zarządzanych przez program System Center Configuration Manager](../../../protect/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm.md).  

### <a name="restricting-access-based-on-the-health-of-devices"></a>Ograniczanie dostępu oparte na kondycji urządzeń  
 Teraz można ograniczyć dostęp do poczty e-mail i 0ffice usług 365 oparte na kondycji urządzeń, podawaną przez usługę kondycji zaświadczania. Ponadto urządzenia zarządzane przez usługę Intune zostaną uwzględnione w raportach kondycji urządzenia.  

 Konsoli programu Configuration Manager oferuje nowe zasady zgodności, która pozwala określić, czy urządzenia powinno być dozwolone lub zablokowane dostępu na podstawie ich stanu kondycji. Aby uzyskać szczegółowe informacje o kondycji usługi zaświadczania i jak kondycji urządzeń jest zgłaszany w usłudze Intune, zobacz [zaświadczania kondycji programu System Center Configuration Manager](../../../core/servers/manage/health-attestation.md).  

### <a name="new-compliance-policy-rules"></a>Nowe reguły zasad zgodności  
 Nowe reguły zasad zgodności, takie jak aktualizacje automatyczne i wymagający hasła do odblokowania urządzeń, zostały dodane do obsługi lepsze wymagania dotyczące zabezpieczeń.

 Aby uzyskać więcej informacji, zobacz [zasadami zgodności urządzeń w programie System Center Configuration Manager](../../../protect/deploy-use/device-compliance-policies.md).  

### <a name="make-sure-enrolled-and-compliant-devices-always-have-access-to-exchange-on-premises"></a>Upewnij się, że urządzenia zarejestrowane i być zgodne zawsze mają dostęp do lokalnego programu Exchange  
 Podczas sprawdzania następującą opcję urządzeń, które są zarejestrowane w usłudze Intune i być zgodne z zasadami zgodności mogą uzyskiwać dostęp do lokalnego programu Exchange: **Domyślne reguły zastąpienie — zawsze Zezwalaj Intune zarejestrowane i zgodne urządzenia w celu dostępu do lokalnego programu Exchange:**. Ta zasada jest dostępna w **strony Ogólne** z **skonfigurować kreatora zasady dostępu warunkowego** dla lokalnego programu Exchange.

 Ta zasada ma pierwszeństwo przed regułą domyślne, co oznacza, że nawet jeśli ustawić domyślną regułę do kwarantanny lub blok dostępu zarejestrowane i urządzeń zgodnych nadal będą mogli uzyskać dostęp do lokalnego programu Exchange. Użyj tego ustawienia, należy zarejestrować i urządzeń zgodnych zawsze ma dostęp do poczty e-mail za pośrednictwem lokalnego programu Exchange.   

 Aby uzyskać szczegółowe wskazówki, zobacz [zarządzanie dostępem do poczty e-mail w programie System Center Configuration Manager](../../../protect/deploy-use/manage-email-access.md).  

## <a name="client-management"></a>Zarządzanie klientami  

### <a name="client-online-status"></a>Stan online klienta  
 Nowy stan dla klientów jest dostępne dla monitorowania, jeśli komputer jest w trybie online lub nie. Komputer jest uznawany za online, jeśli jest ona połączona z przypisanego punktu zarządzania. Aby wskazać, że komputer jest w trybie online, klient wysyła komunikaty ping podobny do punktu zarządzania. Jeśli punkt zarządzania nie pojawi się komunikat po 5 minut, klient jest określana jako trybu offline.  

 Aby uzyskać szczegółowe informacje, zobacz [jak monitorować klientów w programie System Center Configuration Manager](../../../core/clients/manage/monitor-clients.md).  

### <a name="refresh-pc-machine-and-user-policy-from-software-center"></a>Odświeżanie zasad komputera i użytkownika komputera z Centrum oprogramowania  
 Nowa opcja **zasady synchronizacji**, został dodany do **opcje** > **Konserwacja komputera** strony Centrum oprogramowania, które powoduje, że komputer, aby odświeżyć jego programu Configuration Manager zasad komputera i użytkownika.  

### <a name="software-center-branding-changes"></a>Zmiany znakowania Centrum oprogramowania  
 Można zmienić kolor, nazwę organizacji i ikony, które są wyświetlane w Centrum oprogramowania. Te ustawienia są stosowane zgodnie z następującymi zasadami:  

- Jeśli nie zainstalowano usługi roli serwera lokacji punktu witryny sieci Web katalogu aplikacji, a następnie Software Center wyświetla nazwę organizacji, określona w **Agent komputera** klienta nosi nazwę **nazwa organizacji wyświetlana w Centrum oprogramowania**.  

- Jeśli zainstalowano roli serwera lokacji punktu witryny sieci Web katalogu aplikacji, Centrum oprogramowania Wyświetla nazwę organizacji i kolor określony we właściwościach roli serwera lokacji punktu witryny sieci Web katalogu aplikacji.  

- Jeśli subskrypcja Microsoft Intune jest skonfigurowany i podłączony do środowiska programu Configuration Manager, programu Software Center wyświetla nazwę organizacji, kolor i logo firmy określonej we właściwościach subskrypcji usługi Intune.  

### <a name="health-attestation"></a>Poświadczenie zdrowia  
 Administratorzy mogą wyświetlać stan systemu Windows 10 urządzenia kondycji zaświadczania w konsoli programu Configuration Manager. Jest on dostępny dla programu Configuration Manager, a także programu Configuration Manager w usłudze Microsoft Intune. Zaświadczanie o kondycji urządzenia umożliwia administratorowi upewnienie się, że komputery klienckie mają włączone następujące godne zaufania konfiguracje systemu BIOS, modułu TPM i oprogramowania rozruchowego:  

-   Wczesne uruchamiania ochrony przed złośliwym oprogramowaniem  

-   Funkcja BitLocker  

-   Bezpieczny rozruch  

-   Integralności kodu  

Aby uzyskać szczegółowe informacje, zobacz [zaświadczania kondycji programu System Center Configuration Manager](../../../core/servers/manage/health-attestation.md).  

### <a name="improvements-to-endpoint-protection-antimalware-settings"></a>Ulepszenia ustawień ochrony przed złośliwym oprogramowaniem Endpoint Protection  
 1602 dodaje następujące nowe ustawienia w zasadach ochrony przed złośliwym oprogramowaniem Endpoint Protection dla usługi Windows Defender:  

-   Ochrona w czasie rzeczywistym: Blokowanie aplikacji potencjalnie niechciane pobierania przed instalacji.  

-   Ustawienia skanowania: Skanuj zamapowane dyski sieciowe podczas pełnego skanowania.  

-   Automatyczne przykładowe ustawienia przesyłania plików:  

     Aparat ochrony przed złośliwym oprogramowaniem może zażądać próbki plików, które zostanie wysłane do firmy Microsoft do dalszej analizy. Domyślnie przed wysłaniem takich próbek zawsze wyświetlany jest monit. Administratorzy mogą teraz zarządzać następującymi ustawieniami w celu skonfigurowania tego zachowania:  

    -   Zaawansowane: Włącz automatyczne próbką pliku pomagające ustalić, czy niektóre elementy wykrytego złośliwego firmy Microsoft.  

    -   Zaawansowane: Zezwalaj użytkownikom na modyfikowanie automatycznego przykładowe ustawienia przesyłania plików.  

    Ponadto w sekcji "Ustawienia wykluczania" zasady ochrony przed złośliwym oprogramowaniem ochrony punktu końcowego istniejące **wykluczyć pliki i foldery** teraz umożliwia urządzenie wyłączenia.  

Aby uzyskać szczegółowe informacje, zobacz [sposobu tworzenia i wdrażania zasad ochrony przed złośliwym oprogramowaniem programu Endpoint Protection w programie System Center Configuration Manager](../../../protect/deploy-use/endpoint-antimalware-policies.md).  

## <a name="mobile-device-management"></a>Zarządzanie urządzeniami przenośnymi  

### <a name="ios-activation-lock"></a>iOS blokadę aktywacji  
 Configuration Manager może ułatwić zarządzanie iOS blokadę aktywacji, funkcja Znajdź mój iPhone i aplikacji dla systemu iOS 7.1 urządzenia z nowszymi wersjami. Blokada aktywacji jest włączana automatycznie w przypadku użycia aplikacji Znajdź mój iPhone na urządzeniu. Jeśli ta funkcja została włączona, należy podać identyfikator Apple ID i hasło użytkownika, aby można było wykonać następujące czynności:  

-   Wyłącz Znajdź mój iPhone.  

-   Wymazanie urządzenia.  

-   Uaktywnij ponownie urządzenie.  

Program Configuration Manager mogą poprosić o stan blokady aktywacji zarówno nadzorowanego i bez kontroli urządzeń z systemem iOS 7.1 i nowsze. Dla urządzeń z nadzorowanego programu Configuration Manager można pobrać kodu obejścia blokady aktywacji i wydać go bezpośrednio do urządzenia.  

 Aby uzyskać szczegółowe informacje, zobacz [chronić iOS urządzeniami przy użyciu blokady aktywacji obejścia w programie System Center Configuration Manager](/sccm/mdm/deploy-use/manage-ios-activation-lock).  

### <a name="monitor-terms-and-conditions-deployments"></a>Monitorowanie wdrożenia warunki i postanowienia  
 Można monitorować wdrożeń, warunki i postanowienia w konsoli programu Configuration Manager.  

 Wybierz warunki i postanowienia wdrożenie z listy wdrożeń. Obszar Podsumowanie zawiera następujące statystyki:  

-   **Zgodny z**: Użytkowników, którzy zaakceptowali najnowszą wersję warunków i postanowień.  

-   **Błąd**  

-   **Niezgodne**: Użytkowników, którzy zaakceptowali wersji warunków i postanowień, ale nie najnowszej wersji.  

-   **Nieznany**: Użytkownicy nigdy nie zaakceptował warunki i postanowienia, łącznie z tymi bez zarejestrowane urządzenia.  

