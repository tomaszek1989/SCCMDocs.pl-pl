---
title: Nowa wersja 1706
titleSuffix: Configuration Manager
description: "Uzyskiwanie szczegółowych informacji dotyczących zmian i nowych możliwości wprowadzonych w wersji 1706 programu System Center Configuration Manager."
ms.custom: na
ms.date: 08/11/2017
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ac034143-003e-4629-aac2-99eaffef4db1
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: fddb31279587df5306c07a9f23dfc4dace418ea7
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2017
---
# <a name="what39s-new-in-version-1706-of-system-center-configuration-manager"></a>Jaki &#39; s nowego w wersji 1706 programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Zaktualizuj 1706 dla bieżącej gałęzi programu System Center Configuration Manager jest dostępna jako aktualizacja w konsoli dla zainstalowanych wcześniej lokacji, w których jest uruchomiona wersja 1606, 1610 lub 1702.

> [!TIP]  
> Aby zainstalować nową lokację, należy użyć wersji bazowej programu Configuration Manager.  
>  Dowiedz się więcej o:    
>   - [Instalowanie nowej lokacji](https://technet.microsoft.com/library/mt590197.aspx)  
>   - [Instalowanie aktualizacji w lokacjach](https://technet.microsoft.com/library/mt607046.aspx)  
>   - [Wersje linii bazowej i aktualizacji](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions)  

Poniższe sekcje zawierają szczegółowe informacje dotyczące zmian i nowych możliwości wprowadzonych w wersji 1706 programu Configuration Manager.  

<!--
## Deprecated features and operating systems
Learn about support changes before they are implemented in [removed and deprecated features](/sccm/core/plan-design/changes/removed-and-deprecated-features).

Version 1706 drops support for the following products:
-->


## <a name="site-infrastructure"></a>Infrastruktura lokacji

### <a name="client-peer-cache-support-for-express-installation-files-for-windows-10-and-office-365"></a>Klient równorzędnej pamięci podręcznej obsługę plików instalacji ekspresowej dla systemu Windows 10 i usługi Office 365  
<!-- 1352486 -->
Począwszy od tej wersji, równorzędnej pamięci podręcznej obsługuje dystrybucji plików instalacji ekspresowej zawartości dla systemu Windows 10 i plików aktualizacji w usłudze Office 365. Żadne dodatkowe konfiguracje wymagane do obsługi tej zmiany.

### <a name="updates-for-the-data-warehouse"></a>Aktualizacje dla magazynu danych
<!-- 1277922 -->
Magazyn danych nie jest już funkcji wersji wstępnej. Zaktualizowano również wymagania wstępne dotyczące obejmują obsługę bazy danych na serwer SQL zawsze grupy dostępności i klastrów pracy awaryjnej. Aby uzyskać więcej informacji, zobacz [punktu usługi Magazyn danych](/sccm/core/servers/manage/data-warehouse).

### <a name="accessibility-improvements"></a>Ulepszenia ułatwień dostępu
<!-- 1253000 -->
Dodatkowe udoskonalenia dodano do ułatwienia dostępu dla konsoli programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [funkcje ułatwień dostępu](/sccm/core/understand/accessibility-features).

### <a name="improvements--for-sql-server-always-on-availability-groups"></a>Ulepszenia dla programu SQL Server, zawsze włączone grupy dostępności
<!-- 1352094 -->
W tej wersji można teraz używać zatwierdzania asynchronicznego replik w programu SQL Server zawsze włączone grupy dostępności używanych z programem Configuration Manager. Oznacza to, Dodaj do grup dostępności ma być używana jako poza nim (zdalnego) kopii zapasowych dodatkowych replik, a następnie używać ich w sytuacji odzyskiwania po awarii.  
  -   Program Configuration Manager obsługuje przy użyciu repliki zatwierdzania asynchronicznego replika synchroniczna odzyskać. Zobacz [opcje odzyskiwania bazy danych lokacji](/sccm/protect/understand/backup-and-recovery#BKMK_SiteDatabaseRecoveryOption) w temacie kopii zapasowych i odzyskiwania, aby uzyskać informacje o tym.
  -   Ta wersja nie obsługuje trybu failover do korzystania z repliki zatwierdzania asynchronicznego jako bazy danych lokacji.
Aby uzyskać więcej informacji, zobacz [przygotowanie do korzystania z zawsze włączonych grup dostępności](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database).

### <a name="update-reset-tool"></a>Narzędzie resetowania aktualizacji
<!-- 1324589 -->
Począwszy od wersji 1706, lokacji głównej programu Configuration Manager i centralne Lokacje administracyjne obejmują Configuration Manager Zresetuj narzędzie aktualizacji, **CMUpdateReset.exe**. To narzędzie z dowolnej wersji current branch, który pozostaje w pomocy technicznej, aby rozwiązać problemy, gdy problemy pobierania lub replikowanie aktualizacje w konsoli. Aby uzyskać więcej informacji, zobacz [aktualizacji zresetuj narzędzie](/sccm/core/servers/manage/update-reset-tool).

### <a name="high-dpi-console-support"></a>Obsługa konsoli usługi wysokiej rozdzielczości  
<!-- 1353476 -->
W tej wersji należy ustalić problemów z jak skaluje i wyświetla różne części interfejsu użytkownika podczas wyświetlania na wysokie DPI urządzeniach (na przykład powierzchni książki) w konsoli programu Configuration Manager.

### <a name="improved-boundary-groups-for-software-update-points"></a>Grupy granic ulepszone dla punktów aktualizacji oprogramowania
<!-- 1324591 -->
Ta wersja zawiera ulepszenia działania punktów aktualizacji oprogramowania z grupy granic. Poniżej przedstawiono podsumowanie nowe działanie rezerwowe:
-   Używane dla punktów aktualizacji oprogramowania używa teraz można skonfigurować czas powrotu do grup granic sąsiedniego.
-   Niezależne od konfiguracji rezerwowej, klient próbuje osiągnąć ostatniego punktu aktualizacji oprogramowania używanych przez 120 minut. Po nieudanym do tego serwera na 120 minut, klient sprawdzi puli punktów aktualizacji oprogramowania, aby umożliwić znalezienie nowy.
-   Po awarii do oryginalnego serwera przez 2 godziny, klient przełącza się do krótszej cykl w celu kontaktowania się nowego punktu aktualizacji oprogramowania. Oznacza to, jeśli klient nie może nawiązać połączenia z nowym serwerze, szybko wybiera kolejny serwer z puli serwerów dostępnych i próbuje skontaktować się z co.

Aby uzyskać więcej informacji, zobacz [punktów aktualizacji oprogramowania](/sccm/core/servers/deploy/configure/boundary-groups#software-update-points) w temacie grup granic dla bieżącej gałęzi.

### <a name="azure-ad-integration-with-configuration-manager"></a>Azure AD integracji z programem Configuration Manager
<!-- 1248187, 1290765, 1258052, 1298097, 1319334, 1319883, 1352135, 1353331 -->
W tej wersji firma Microsoft ulepszyła integracji programu Configuration Manager i usługi Azure Active Directory (Azure AD).  Te ulepszenia upraszcza sposób konfigurowania usług Azure, z których korzystasz z programu Configuration Manager i ułatwić zarządzanie klientów i użytkowników, którzy uwierzytelniają się jednak usługi Azure AD.

Ulepszona integracja umożliwia następujące:  
  -   Kreator usług Azure — Kreator zapewnia typowych konfiguracji zastępujący poszczególnych przepływów pracy do konfigurowania następujących usług platformy Azure, których korzystasz z programu Configuration Manager.
      - **Chmury zarządzania** umożliwić klientom z uwierzytelniania za pomocą usługi Azure Active Directory (Azure AD). Można również skonfigurować odnajdowanie użytkowników usługi AD platformy Azure.
      - **Łącznik OMS** nawiązywanie Operations Manager Suite (OMS) i synchronizacji danych, takich jak kolekcje w celu analizy dzienników OMS.
      - **Gotowość do uaktualnienia** nawiązywanie gotowości do uaktualnienia i Wyświetl dane zgodności uaktualnienia klienta.
      - **Sklep Windows dla firm** Connect w magazynie online dla Sklepu Windows dla aplikacji biznesowych i get dla organizacji, które można wdrożyć z programem Configuration Manager.


  Jest to zrobić za pomocą [aplikacji sieci web serwera Azure](/azure/azure/app-service/app-service-authentication-overview#service-to-service-authentication) zapewnienie Szczegóły subskrypcji i konfiguracji, które należy wprowadzić w przeciwnym razie zawsze należy skonfigurować nowego składnika programu Configuration Manager lub usługi platformy Azure. Aby uzyskać więcej informacji, zobacz [Kreator usług Azure](/sccm/core/servers/deploy/configure/azure-services-wizard).

-   Przy użyciu usługi Azure AD do uwierzytelniania klientów w Internecie, aby uzyskać dostęp z lokacji programu Configuration Manager. Usługi Azure AD zastępuje konieczność skonfigurowania i używają certyfikatów uwierzytelniania klienta. Wymaga to rola systemu lokacji chmury zarządzania bramy. Aby uzyskać więcej informacji, zobacz [instalacji i przypisywanie klientów programu Configuration Manager z Internetu przy użyciu usługi Azure AD do uwierzytelniania](/sccm/core/clients/deploy/deploy-clients-cmg-azure).

-   Zainstaluj i Zarządzaj klientem programu Configuration Manager na komputerach, które znajdują się w Internecie. Wymaga to użycie roli systemu lokacji bramy zarządzania chmury. Aby uzyskać więcej informacji, zobacz [instalacji i przypisywanie klientów programu Configuration Manager z Internetu przy użyciu usługi Azure AD do uwierzytelniania](/sccm/core/clients/deploy/deploy-clients-cmg-azure).

-   Skonfiguruj odnajdowanie użytkowników usługi Azure AD.  Użyj kreatora usług Azure, aby skonfigurować to nowa metoda odnajdywania. Ta nowa metoda wysyła zapytanie do usługi Azure AD danych przez użytkownika można następnie użyć danych odnajdywania tradycyjnych wzdłuż po stronie.  Obsługiwane są zarówno pełne i różnicowe synchronizacji.  Aby uzyskać więcej informacji, zobacz [odnajdowanie użytkowników usługi AD Azure](/sccm/core/servers/deploy/configure/about-discovery-methods#azureaddisc).

### <a name="peer-cache-improvements"></a>Ulepszenia pamięci podręcznej elementów równorzędnych
<!-- 1252345 -->
Równorzędnej pamięci podręcznej nie jest już używa konta dostępu do sieci do uwierzytelniania żądań pobierania od elementów równorzędnych. Istnieje jedno zastrzeżenie: to, gdy pozostaje konta wymagane przez klientów. Wymaganie to pozostaje dla klientów, których rozruch w środowisku WinPE i uzyskuje dostęp do zawartości ze źródła równorzędnej pamięci podręcznej. Aby uzyskać więcej informacji, zobacz [wymagań i zagadnień dotyczących równorzędnej pamięci podręcznej](/sccm/core/plan-design/hierarchy/client-peer-cache#requirements-and-considerations-for-peer-cache).


<!-- ## Migration  -->


<!-- ## Client management  -->


## <a name="compliance-settings"></a>Ustawienia zgodności

### <a name="new-configuration-settings-for-windows-10-devices-that-are-not-managed-with-the-configuration-manager-client"></a>Nowe ustawienia konfiguracji dla urządzeń z systemem Windows 10, które nie są zarządzane przy użyciu klienta programu Configuration Manager
<!-- 1354715 -->
W tej wersji dodano nowe ustawienia elementu konfiguracji dla urządzeń z systemem Windows 10, które są zarejestrowane w usłudze Intune lub zarządzane lokalnie przez program Configuration Manager. Dostępne są następujące ustawienia:

- **Hasło**
    - Szyfrowanie urządzenia
- **Urządzenie**
    - Modyfikacja ustawień regionie (tylko wersja desktop)
    - Modyfikacja ustawień zasilania i uśpienia
    - Modyfikacja ustawień języka
    - System czas modyfikacji
    - Zmiana nazwy urządzenia
- **Magazyn**
    - Automatyczna aktualizacja aplikacji ze sklepu
    - Użyj tylko prywatnego magazynu
    - Uruchamianie aplikacji zdalnych magazynu
- **Przeglądarka Microsoft Edge**
    - Blokowanie dostępu do informacji o: flagi
    - Filtr SmartScreen monitu o zastąpienie
    - Filtr SmartScreen monitu o zastąpienie plików
    - Adres IP hosta lokalnego WebRTC
    - Domyślny aparat wyszukiwania
    - Adres URL OpenSearch XML
    - Strony główne (tylko wersja desktop)

Aby uzyskać szczegółowe informacje o wszystkie ustawienia systemu Windows 10, zobacz [jak utworzyć elementy konfiguracji dla urządzeń Windows 8.1 i Windows 10 zarządzanych bez klienta programu System Center Configuration Manager](/sccm/mdm/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client).

### <a name="new-device-compliance-policy-rules"></a>Nowe reguły zasad zgodności urządzenia

* **Wymagany typ hasła**. Określ, czy użytkownik muszą utworzyć hasła alfanumerycznego i numeryczne hasła. Alfanumeryczne haseł również określić minimalną liczbę zestawów znaków, które muszą mieć hasłem. Są cztery zestawy znaków: Małe litery, wielkie litery, symbole i cyfry.

 **Obsługiwane na:**
 * Windows Phone 8+
 * Windows 8.1 +
 * iOS 6+
<br></br>
* **Debugowanie USB bloku na urządzeniu**. Nie masz ustawień jako debugowanie USB już jest wyłączona w systemie Android pracy urządzeń.

 **Obsługiwane na:**
 * Android 4.0+
 * Samsung Knox Standard 4.0+
<br></br>
* **Blokowanie aplikacji z nieznanych źródeł**. Wymagaj, aby urządzenia uniemożliwiały instalację aplikacji z nieznanych źródeł. Nie masz Skonfiguruj to ustawienie, jak Android pracy urządzeń zawsze ograniczyć instalacja z nieznanych źródeł.

  **Obsługiwane na:**
  * Android 4.0+
  * Samsung Knox Standard 4.0+
<br></br>
* **Wymagaj skanowania zagrożeń na aplikacje**. To ustawienie określa, że funkcja aplikacji Sprawdź, czy jest włączona na urządzeniu.

 **Obsługiwane na:**
 * System android 4.2 za pośrednictwem 4.4
 * Samsung Knox Standard 4.0+

Zobacz [tworzenie i wdrażanie zasad zgodności urządzenia](https://docs.microsoft.com/sccm/mdm/deploy-use/create-compliance-policy) próby nowe reguły zgodności urządzenia

## <a name="application-management"></a>Zarządzanie aplikacjami

### <a name="run-powershell-scripts-from-the-configuration-manager-console"></a>Uruchamiać skrypty programu PowerShell z poziomu konsoli programu Configuration Manager
<!-- 1236459 -->

W programie Configuration Manager można wdrożyć skryptów na urządzeniach klienckich przy użyciu pakietów i programów. W tej wersji dodano nowe funkcje, które można wykonać następujące czynności:

- Importuj skryptów programu PowerShell dla programu Configuration Manager
- Edytowanie skryptów z poziomu konsoli programu Configuration Manager (w przypadku niepodpisanych skryptów tylko)
- Skrypty Oznacz jako zatwierdzone lub zabroniona, zwiększające bezpieczeństwo
- Uruchamianie skryptów w kolekcji komputerom klienckim z systemem Windows oraz lokalnych zarządzanych komputerów z systemem Windows. Nie można wdrożyć skrypty, zamiast tego są uruchamiane w najbliższym czasie rzeczywistym na urządzeniach klienckich.
- Zbadanie wyników zwróconych przez skrypt w konsoli programu Configuration Manager.

Aby uzyskać więcej informacji, zobacz [tworzenia i uruchamiania skryptów programu PowerShell z poziomu konsoli programu Configuration Manager](/sccm/apps/deploy-use/create-deploy-scripts).

### <a name="new-mobile-application-management-policy-settings"></a>Nowe ustawienia zasad zarządzania aplikacjami mobilnymi    
<!--1324760-->
Począwszy od tej wersji, można użyć trzech nowe ustawienia zasad zarządzania aplikacjami mobilnymi:

- **Zablokuj Przechwytywanie ekranu (tylko urządzenia z systemem Android):** Określa, że możliwości przechwytywania ekranu urządzenia są blokowane podczas korzystania z tej aplikacji.

Zobacz [ochrona aplikacji przy użyciu zasad ochrony aplikacji w programie Configuration Manager](https://docs.microsoft.com/sccm/mdm/deploy-use/protect-apps-using-mam-policies) próby nowe ustawienia zasad ochrony aplikacji.


## <a name="operating-system-deployment"></a>Wdrożenie systemu operacyjnego

### <a name="hardware-inventory-collects-secure-boot-information"></a>Spisu sprzętu zbiera informacje Bezpieczny rozruch
Spis sprzętu teraz zbiera informacje o czy Bezpieczny rozruch jest włączony na komputerach klienckich. Te informacje są przechowywane w **SMS_Firmware** klasy (wprowadzonych w wersji 1702) i włączone w sprzętu, spisu domyślnie. Aby uzyskać więcej informacji dotyczących zapasów sprzętu, zobacz [jak skonfigurować spis sprzętu](/sccm/core/clients/manage/inventory/configure-hardware-inventory).

### <a name="collapsible-task-sequence-groups"></a>Grupy sekwencji zadań zwijanej
W tej wersji wprowadzono możliwość rozwijanie i zwijanie grupy sekwencji zadań. Można rozwinąć lub zwinąć poszczególnych grup lub rozwiń lub Zwiń wszystkie grupy w jednocześnie.

### <a name="reload-boot-images-with-current-windows-pe-version"></a>Załaduj ponownie obrazy rozruchowe z bieżącej wersji systemu Windows PE
Po uruchomieniu **Aktualizuj punkty dystrybucji** na wybranego obrazu rozruchowego, teraz możesz ponownie załadować najnowszą wersję środowiska Windows PE (w katalogu instalacyjnym zestawu Windows ADK) do obrazu rozruchowego. Aby uzyskać więcej informacji, zobacz [Aktualizuj punkty dystrybucji o obraz rozruchowy](/sccm/osd/get-started/manage-boot-images#update-distribution-points-with-the-boot-image).

## <a name="software-updates"></a>Aktualizacje oprogramowania

### <a name="improvements-to-express-update-download-time"></a>Czas pobierania ulepszenia Express aktualizacji
W tej wersji możemy znacznie ulepszono czas pobierania aktualizacji Express. Aby uzyskać więcej informacji, zobacz [instalacji zarządzania Express pliki aktualizacji systemu Windows 10](/sccm/sum/deploy-use/manage-express-installation-files-for-windows-10-updates).

### <a name="manage-microsoft-surface-driver-updates"></a>Zarządzanie aktualizacjami sterownik Microsoft Surface
<!-- 1098490 -->
Można teraz używać programu Configuration Manager do zarządzania aktualizacjami sterownik Microsoft Surface.    


#### <a name="prerequisites"></a>Wymagania wstępne
- Wszystkie punkty aktualizacji oprogramowania, należy uruchomić system Windows Server 2016.    
- Jest to funkcja wersji wstępnej, które należy włączyć dla niego mają być dostępne. Aby uzyskać więcej informacji, zobacz sekcję dotyczącą [używania funkcji w wersjach wstępnych z poziomu aktualizacji](https://docs.microsoft.com/sccm/core/servers/manage/install-in-console-updates#bkmk_prerelease).

#### <a name="to-manage-surface-driver-updates"></a>Do zarządzania aktualizacjami powierzchni sterownika

1. Włącz synchronizację dla Microsoft Surface sterowników. Użyj procedury [Konfigurowanie klasyfikacji i produktów](/sccm/sum/get-started/configure-classifications-and-products) i wybierz **obejmują Microsoft Surface sterowniki i aktualizacje oprogramowania układowego** wyboru na **klasyfikacje** kartę, aby włączyć sterowniki powierzchni.
2. [Synchronizuj sterowniki Microsoft Surface](/sccm/sum/get-started/synchronize-software-updates).
3. [Wdrażanie zsynchronizowane Microsoft Surface sterowniki](/sccm/sum/deploy-use/deploy-software-updates)

### <a name="configure-windows-update-for-business-deferral-policies"></a>Konfigurowanie usługi Windows Update dla zasad wykluczenia biznesowych
<!-- 1290890 -->
Można teraz skonfigurować zasady odroczenia urządzeń aktualizacje funkcji systemu Windows 10 lub jakości aktualizacji dla systemu Windows 10 zarządzane bezpośrednio przez usługę Windows Update dla firm. Zasadami odroczenia można zarządzać w nowym **Windows Update dla firm, zasady** węźle **Biblioteka oprogramowania** > **obsługi systemu Windows 10**.

Aby uzyskać więcej informacji, zobacz [integracji z usługą Windows Update dla firm w systemie Windows 10](/sccm/sum/deploy-use/integrate-windows-update-for-business-windows-10#configure-windows-update-for-business-deferral-policies).

### <a name="improved-user-notifications-for-office-365-updates"></a>Ulepszone powiadomienia użytkowników aktualizacji usługi Office 365
Wprowadzono ulepszenia wykorzystać środowisko użytkownika pakietu Office kliknij polecenie do uruchomienia po zainstalowaniu klienta aktualizacji usługi Office 365. W tym powiadomienia wyskakującego i w aplikacji i środowisko odliczania. Aby uzyskać więcej informacji, zobacz [ponownie powiadomienia klienta i zachowanie, aby aktualizacji usługi Office 365](/sccm/sum/deploy-use/manage-office-365-proplus-updates#restart-behavior-and-client-notifications-for-office-365-updates)

## <a name="reporting"></a>Raportowanie

### <a name="use-windows-analytics-with-configuration-manager"></a>Użyj module analiz systemu Windows z programem Configuration Manager
<!-- 1318608 -->
Module analiz systemu Windows to zestaw rozwiązań, które są uruchamiane na Operations Management Suite. Rozwiązania umożliwiają formularza wgląd w bieżący stan środowiska. Urządzenia w danym środowisku zgłaszać dane telemetryczne systemu Windows. Dane są dostępne za pośrednictwem portalu sieci web usługi Operations Management Suite. W przypadku uaktualniania gotowości dane są bezpośrednio dostępne w węźle monitorowanie konsoli programu Configuration Manager.

Aby uzyskać więcej informacji, zobacz [module analiz systemu Windows używana z programem Configuration Manager](/sccm/core/clients/manage/monitor-windows-analytics).


<!-- ## Inventory  -->

## <a name="mobile-device-management"></a>Zarządzanie urządzeniami przenośnymi

### <a name="updates-to-android-for-work-sharing-configuration"></a>Aktualizacje w systemie Android for Work Konfiguracja udostępniania
<!-- 1338403 -->
W tym wydaniu wartości **Zezwalaj na udostępnianie między pracą a profilu osobistego danych** w **profil służbowy** ustawienie grupy zostały zaktualizowane. Dodaliśmy również ustawienie Blokowanie kopiowania i wklejania między pracą a Profile osobiste niestandardowego.

Aby uzyskać więcej informacji, zobacz [elementy konfiguracji dla systemu Android dla urządzeń pracy](/sccm/mdm/deploy-use/create-configuration-items-for-android-for-work-devices-managed-without-the-client).

### <a name="android-and-ios-enrollment-restrictions"></a>Android i iOS ograniczenia rejestracji
<!-- 1290826 -->
W tej wersji można teraz określić, że użytkownicy nie można zarejestrować urządzeń osobistych Android lub iOS. Nowe ustawienia ograniczeń urządzeń umożliwiają ograniczanie rejestracji urządzeń z systemem Android do wcześniej zadeklarowanej urządzeń. Dla urządzeń z systemem iOS możesz zablokować rejestrację wszystkich urządzeń, z wyjątkiem tych zarejestrowane za pomocą programu Device Enrollment Program firmy Apple, konfiguratora firmy Apple lub konta Menedżera rejestracji urządzeń usługi Intune.
- Aby uzyskać więcej informacji na temat ograniczeń rejestracja systemu Android, zobacz [Konfigurowanie zarządzania urządzeniami z systemem Android](/sccm/mdm/deploy-use/enroll-hybrid-android).
- Aby uzyskać więcej informacji na temat ograniczeń rejestracji systemu iOS, zobacz [skonfigurować ograniczenia rejestracji systemu iOS](/sccm/mdm/deploy-use/enroll-hybrid-ios-mac#configure-enrollment-restrictions).

## <a name="protect-devices"></a>Ochrona urządzeń

### <a name="include-trust-for-specific-files-and-folders-in-a-device-guard-policy"></a>Obejmują zaufania dla określonych plików i folderów w zasadach ochrony urządzeń
<!--1324676-->
W tej wersji dodano dodatkowe funkcje do zarządzania zasadami ochrony urządzeń.

Teraz można opcjonalnie dodawać zaufania dla określonych plików, folderów w zasadach ochrony urządzeń. Dzięki temu można:

- Rozwiązać problemy za pomocą zachowań zarządzanych Instalatora
- Zaufanie aplikacji z biznesowych, których nie można wdrożyć z programu Configuration Manager
- Zaufanie aplikacji, które są objęte obrazu wdrożenia systemu operacyjnego

Aby uzyskać więcej informacji, zobacz [zarządzania ochrona urządzeń z programem Configuration Manager](/sccm/protect/deploy-use/use-device-guard-with-configuration-manager).
