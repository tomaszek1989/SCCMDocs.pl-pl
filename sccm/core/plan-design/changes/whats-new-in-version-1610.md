---
title: Nowa wersja 1610 | Dokumentacja firmy Microsoft
description: "Uzyskiwanie szczegółowych informacji dotyczących zmian oraz nowe funkcje wprowadzone w wersji 1610 programu System Center Configuration Manager."
ms.custom: na
ms.date: 11/23/2016
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f7eb0803-3f8f-4ab6-825a-99ac11f5ba7d
caps.latest.revision: 40
author: Brenduns
ms.author: brenduns
manager: angrobe
ROBOTS: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 831d8a66c827d246069c7415cdce7a7c4bb95b33
ms.openlocfilehash: 19e3099773f887129374413482702de3f4b0a36f
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="what39s-new-in-version-1610-of-system-center-configuration-manager"></a>Co &#39; s nowe w wersji 1610 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Zaktualizuj 1610 dla bieżącej gałęzi System Center Configuration Manager jest dostępna jako aktualizacja w konsoli uprzednio zainstalowanej lokacji, w wersji 1511, 1602 lub 1606.


> [!TIP]  
> Aby zainstalować nową lokację, należy użyć wersji programu Configuration Manager linii bazowej.  
>  Więcej informacji na temat:    
>  -   [Instalowanie nowych witryn](https://technet.microsoft.com/library/mt590197.aspx)  
>  -   [Instalowanie aktualizacji w lokacjach](https://technet.microsoft.com/library/mt607046.aspx)  
>  -   [Wersje linii bazowej i aktualizacji](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions)  

Poniższe sekcje zawierają szczegółowe informacje dotyczące zmiany i nowe możliwości wprowadzona w wersji 1610 programu Configuration Manager.  


## <a name="in-console-monitoring-of-update-installation-status"></a>Monitorowanie stanu instalacji aktualizacji w konsoli  
Począwszy od wersji 1610 podczas instalowania pakietu aktualizacji i monitorowania instalacji w konsoli, istnieje nowej fazy: **Po instalacji**. Ta faza obejmuje stan zadania, takie jak ponowne uruchomienie usługi klucza i inicjowania monitorowania replikacji. (Ta faza nie jest dostępne w konsoli dopiero po aktualizacji lokacji do wersji 1610). Aby uzyskać więcej informacji o stanie instalacji aktualizacji, zobacz [zainstalować aktualizacji w konsoli](/sccm/core/servers/manage/install-in-console-updates#a-namebkmkinstalla-install-in-console-updates).


## <a name="exclude-clients-from-automatic-upgrade"></a>Wyklucz klientów z automatycznej aktualizacji
Klienci systemu Windows można wykluczyć z pobieranie uaktualniony do nowych wersji oprogramowania klienckiego. W tym celu należy obejmują komputerów klienckich w kolekcji określonej mają być wykluczone z uaktualnienia. Klienci w kolekcji wykluczonych zignorować żądań dotyczących aktualizacji oprogramowania klienckiego.  Aby uzyskać więcej informacji, zobacz [wykluczyć klientów systemu Windows z uaktualnień](../../clients/manage/upgrade/exclude-clients-windows.md).


## <a name="improvements-for-boundary-groups"></a>Udoskonalenia w zakresie grup granic
Wersja 1610 wprowadza ważne zmiany do grupy granic oraz ich współdziałaniu z punktami dystrybucji. Te zmiany można uprościć projektowania infrastruktury zawartości podczas co daje większą kontrolę nad kiedy i jak klienci powrotu do wyszukiwania dystrybucji dodatkowych punktów jako lokalizacji źródła zawartości. Obejmuje to zarówno lokalnie, jak i punkty dystrybucji w chmurze.
Te ulepszenia Zamień pojęcia i zachowania można zapoznać się z (np. Konfigurowanie punktów dystrybucji za dużą lub małą). Nowy model powinna być łatwiejsze do konfiguracji i utrzymania. Te zmiany przygotowawczych także przyszłe zmiany zwiększające inne role systemu lokacji, którą można skojarzyć do grup granic.

Po uaktualnieniu do wersji 1610 aktualizacji konwertuje bieżącej konfiguracji grupy granic do nowego modelu, aby te zmiany nie przeszkadzać istniejącej konfiguracji dystrybucji zawartości.

Aby uzyskać więcej informacji, zobacz [grup granic](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#a-namebkmkboundarygroupsa-boundary-groups).


## <a name="peer-cache-for-content-distribution-to-clients"></a>Buforowanie równorzędne dla dystrybucji zawartości do klientów
Począwszy od wersji 1610, klient **Buforowanie równorzędne** ułatwia zarządzanie wdrażaniem zawartości do klientów w lokalizacjach zdalnych. Buforowanie równorzędne to rozwiązanie programu Configuration Manager wbudowanych klientom na współużytkowanie zawartości z innymi klientami bezpośrednio z lokalnej pamięci podręcznej.

Po wdrożeniu ustawień klienta, które umożliwiają Buforowanie równorzędne w kolekcji członków tej kolekcji może działać jako źródła zawartości elementu równorzędnego dla innych klientów w tej samej grupie granic.

Można także użyć nowego **źródeł danych klientów** pulpit nawigacyjny, aby poznać wykorzystanie źródeł zawartości Buforowanie równorzędne w danym środowisku.

> [!TIP]  
> Z wersją 1610 Buforowanie równorzędne i pulpit nawigacyjny źródeł danych klientów są funkcje wersji wstępnej. Aby je włączyć, zobacz [używać funkcji wersji wstępnej z aktualizacji](/sccm/core/servers/manage/install-in-console-updates#bkmk_prerelease).

Aby uzyskać więcej informacji, zobacz [Buforowanie równorzędne dla klientów programu Configuration Manager](/sccm/core/plan-design/hierarchy/client-peer-cache), i [pulpitu nawigacyjnego źródeł danych klientów](/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed#client-data-sources-dashboard).


## <a name="migrate-multiple-shared-distribution-points-at-the-same-time"></a>Migracja wielu współużytkowanych punktów dystrybucji w tym samym czasie
Możesz teraz użyć opcję **ponowne przypisanie punktu dystrybucji** mieć proces programu Configuration Manager równolegle ponowne przypisanie maksymalnie 50 współużytkowanych punktów dystrybucji, w tym samym czasie. Przed tej wersji punktów dystrybucji przypisywać zostały przetworzone pojedynczo. Aby uzyskać więcej informacji, zobacz [migracji wiele współużytkowanych punktów dystrybucji, w tym samym czasie](/sccm/core/migration/planning-a-content-deployment-migration-strategy#migrate-multiple-shared-distribution-points-at-the-same-time).

## <a name="cloud-management-gateway-for-managing-internet-based-clients"></a>Brama zarządzania chmury do zarządzania klientami internetowymi

Brama zarządzania chmury udostępnia prosty sposób zarządzać klientami programu Configuration Manager w Internecie. Usługę bramy zarządzania chmury, która jest wdrażana Microsoft Azure i wymaga subskrypcji platformy Azure, łączy się z lokalnej infrastruktury programu Configuration Manager za pomocą nowej roli o nazwie punktu połączenia chmury zarządzania bramą. Gdy ma całkowicie wdrożone i skonfigurowane, klienci mogą komunikować się z rolami systemu lokacji programu Configuration Manager lokalnych i punktów dystrybucji w chmurze, niezależnie od tego, czy nawiązano połączenie z prywatną siecią wewnętrzną lub w Internecie. Aby uzyskać więcej informacji i zobacz, jak brama zarządzania chmury porównuje za pomocą funkcji zarządzania klientami, zobacz [zarządzać klientami w Internecie](/sccm/core/clients/manage/manage-clients-internet).

## <a name="improvements-to-the-windows-10-edition-upgrade-policy"></a>Ulepszenia zasad uaktualniania wersji systemu Windows 10
W tej wersji tego typu zasad wprowadzono następujące ulepszenia:

- Można teraz używać zasady uaktualniania wersji z komputery z systemem Windows 10 uruchomionymi klienta programu Configuration Manager, oprócz komputery z systemem Windows 10 zarejestrowanych w usłudze Microsoft Intune.
- Można uaktualnić z systemu Windows 10 Professional do dowolnej platformy w kreatorze, które są zgodne ze sprzętem.

## <a name="manage-hardware-identifiers"></a>Zarządzanie identyfikatory sprzętu
Teraz można podać listę sprzętu identyfikatory ignorować programu Configuration Manager na potrzeby rejestracji klienta i rozruchu środowiska PXE. Istnieją dwa typowych problemów, które pozwala to na adres:

1. Wiele urządzeń, takich jak Surface Pro 3, nie ma objąć portu Ethernet. Karta USB-Ethernet zazwyczaj jest używane do nawiązania połączenia sieci przewodowych na potrzeby wdrażania systemu operacyjnego. Jednakże z powodu kosztów i użyteczność ogólne są często udostępnionego kart. Ponieważ adres MAC karty jest używany do identyfikowania urządzenia, ponowne użycie karty staje się problematyczne bez administratora dodatkowe akcje między każdym wdrożeniu. Teraz w 1610 wersji programu Configuration Manager, można wykluczyć adres MAC karty, dzięki czemu można łatwo nastąpić w tym scenariuszu.
2. Identyfikator SMBIOS powinien być unikatowy identyfikator sprzętu, ale niektóre urządzenia specjalne są kompilowane mających zduplikowane identyfikatory. Ten problem może nie być jako wspólne jako scenariusz karty USB-Ethernet, po prostu opisano, ale można ją usunąć za pomocą listy identyfikatorów sprzętu wykluczone.

Aby uzyskać szczegółowe informacje, zobacz [Zarządzaj sprzętu zduplikowane identyfikatory](/sccm/core/clients/manage/manage-clients#manage-duplicate-hardware-identifiers).

## <a name="enhancements-to-windows-store-for-business-integration-with-configuration-manager"></a>Rozszerzenia do Sklepu Windows biznesowych integracji z programem Configuration Manager
Zmiany w tej wersji:
- Wcześniej można wdrożyć tylko bezpłatnej aplikacji ze Sklepu Windows dla firm. Program Configuration Manager teraz ponadto obsługuje wdrażanie płatności online licencjonowane aplikacje (tylko w przypadku zarejestrowanych w usłudze Intune urządzeń).
- Teraz można zainicjować natychmiastową synchronizację między Sklepu Windows dla firm i Configuration Manager.
- Teraz można zmodyfikować klucz tajny klienta został pobrany z usługi Azure Active Directory.
- Można usunąć subskrypcji do magazynu.

Aby uzyskać szczegółowe informacje, zobacz [zarządzania aplikacjami ze Sklepu Windows dla firm z System Center Configuration Manager](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business).


## <a name="policy-sync-for-intune-enrolled-devices"></a>Zasada synchronizacji dla urządzeń zarejestrowanych w usłudze Intune
Teraz można zażądać synchronizacji zasad dla urządzeń zarejestrowanych w usłudze Intune z konsoli programu Configuration Manager, bez konieczności wprowadzania żądania synchronizacji z aplikacji Portal firmy na urządzeniu. Informacje o stanie żądania synchronizacji jest dostępna jako nową kolumnę w widokach urządzenia, o nazwie **zdalnego stan synchronizacji**. Informacje są także dostępne w sekcji danych odnajdywania **właściwości** okna dialogowego dla każdego urządzenia.
Aby uzyskać szczegółowe informacje, zobacz [zdalnie synchronizować zasad na urządzeniach z konsoli programu Configuration Manager zarejestrowane Intune](/sccm/mdm/deploy-use/sync-intune-device).


## <a name="use-compliance-settings-to-configure-windows-defender-settings"></a>Aby skonfigurować ustawienia usługi Windows Defender za pomocą ustawień zgodności
Można teraz skonfigurować ustawienia klienta usługi Windows Defender na komputerach zarejestrowanych w usłudze Intune systemu Windows 10 za pomocą elementów konfiguracji w konsoli programu Configuration Manager.
Aby uzyskać szczegółowe informacje, zobacz **programu Windows Defender** w sekcji [tworzenie elementów konfiguracji dla urządzeń Windows 8.1 i Windows 10 zarządzane bez klienta programu System Center Configuration Manager](/sccm/compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client).



## <a name="general-improvements-to-software-center"></a>Ogólne ulepszenia Centrum oprogramowania
- Użytkownicy mogą teraz zażądać aplikacji z katalogu aplikacji, a także Centrum oprogramowania.
- Usprawnienia ułatwiające zrozumienie, jakie oprogramowanie jest nowe i odpowiednich użytkowników.

## <a name="new-columns-in-device-collection-views"></a>Nowe kolumny w widokach kolekcji urządzeń
Można teraz wyświetlić kolumny dla **IMEI** i **numer seryjny** (dla urządzeń z systemem iOS) w widokach kolekcji urządzeń.
Aby uzyskać więcej informacji, zobacz [Predeclare urządzeń o numerach seryjnych IMEI lub iOS](https://docs.microsoft.com/sccm/mdm/deploy-use/predeclare-devices-with-hardware-id).

## <a name="customizable-branding-for-software-center-dialogs"></a>Można dostosować, znakowania w oknach dialogowych programu Software Center
Niestandardowe znakowanie dla programu Software Center wprowadzono 1602 wersji programu Configuration Manager. W wersji 1610 tego znakowania jest rozszerzona do wszystkich skojarzonych okien dialogowych do zapewnienia bardziej spójne możliwości użytkownikom w Centrum oprogramowania.

Niestandardowe znakowanie dla programu Software Center zostanie zastosowane zgodnie z następującymi zasadami:

- Jeśli nie zainstalowano usługi roli serwera lokacji punktu witryny sieci Web katalogu aplikacji, a następnie Software Center wyświetla nazwę organizacji, określona w **Agent komputera** ustawienia klienta **nazwa organizacji wyświetlana w Centrum oprogramowania**. Aby uzyskać instrukcje, zobacz [sposób konfigurowania ustawień klienta](../../clients/deploy/configure-client-settings.md).

- Jeśli zainstalowano roli serwera lokacji punktu witryny sieci Web katalogu aplikacji, Centrum oprogramowania Wyświetla nazwę organizacji i kolor określony we właściwościach roli serwera lokacji punktu katalogu aplikacji witryny sieci Web. Aby uzyskać więcej informacji, zobacz [opcje konfiguracji dla punktu witryny sieci Web katalogu aplikacji](/sccm/core/servers/deploy/configure/configuration-options-for-site-system-roles#Application-Catalog-website-point).

- Jeśli subskrypcja Microsoft Intune jest skonfigurowany i podłączony do środowiska programu Configuration Manager, programu Software Center wyświetla nazwę organizacji, kolor i logo firmy określonej we właściwościach subskrypcji usługi Intune. Aby uzyskać więcej informacji, zobacz [Konfigurowanie subskrypcji usługi Microsoft Intune](/sccm/mdm/deploy-use/setup-hybrid-mdm#step-3-configure-intune-subscription).


## <a name="enforcement-grace-period-for-required-application-and-software-update-deployments"></a>Okres prolongaty wymuszania dla wdrożeń wymaganych aplikacji i aktualizacji oprogramowania
W niektórych przypadkach można umożliwić użytkownikom więcej czasu do instalacji wymagane wdrożenia aplikacji lub aktualizacji oprogramowania poza wszystkie terminy zdefiniowane. Na przykład może to być konieczne, gdy komputer została wyłączona przez dłuższy czas i należy go zainstalować dużej liczby wdrożeń aplikacji lub aktualizacji. Na przykład jeśli użytkownik końcowy zwrócił tylko z urlopie, konieczne może być oczekiwanie na długo jako aplikacja zaległe wdrożenia są instalowane. Aby rozwiązać ten problem, można zdefiniować okres prolongaty wymuszania przez wdrożenie ustawień klienta programu Configuration Manager do kolekcji. 

Aby skonfigurować okres prolongaty, należy wykonać następujące czynności:
1.      Na **Agent komputera** strony ustawień klienta, należy skonfigurować nową właściwość **okres prolongaty dla wymuszania po wdrożeniu termin ostateczny (w godzinach)** o wartości między **1** i **120** godzin.
2.      Nowe wdrożenie aplikacji lub właściwości istniejącego wdrożenia na **Planowanie** strony, zaznacz pole wyboru **opóźnienie wymuszania tego wdrożenia, zgodnie z preferencjami użytkownika do okresu prolongaty zdefiniowane w ustawieniach klienta**. Wszystkie wdrożenia, które zaznaczone to pole wyboru i są przeznaczone dla urządzeń, na których wdrożono również ustawienie klienta, zostanie użyty okres prolongaty wymuszania.

Skonfiguruj okres prolongaty wymuszania, zaznacz pole wyboru, po osiągnięciu ostatecznego terminu instalacji aplikacji zostanie zainstalowany w oknie-business pierwszy użytkownik skonfigurowany do tego okresu prolongaty. Jednak nadal użytkownika Otwórz Centrum oprogramowania i aplikacji w dowolnym momencie, które chcą zainstalować. Po wygaśnięciu okresu prolongaty wymuszania przywraca normalne zachowanie w przypadku wdrożeń zaległe. Podobne opcje zostały dodane do Kreatora wdrażania aktualizacji oprogramowania, Kreator reguł wdrażania automatycznego i stron właściwości.



## <a name="improved-functionality-in-dialog-boxes-about-required-software"></a>Udoskonalone funkcje w oknach dialogowych o wymaganego oprogramowania
WWhen użytkownik otrzymuje wymaganego oprogramowania z **Odłóż i Przypomnij mi:** ustawienia, można wybrać z listy rozwijanej następujące wartości: 
- **Później**. Określa zaplanowane powiadomienia na podstawie ustawień powiadomień skonfigurowanym w ustawieniach agenta klienta.
- **Stały czas**. Określa, że powiadomienia są planowane do wyświetlenia ponownie po wybrany czas (na przykład w 30 minut).

![Komputer agenta strony w ustawieniach agenta klienta](media/client-notification-settings.png)

Czas odłożenia maksymalna jest oparty na wartościach powiadomień skonfigurowanym w ustawieniach agenta klienta. Na przykład jeśli **wdrożenia termin ostateczny dłużej niż 24 godziny, przypominaj użytkowników co (godziny)** ustawienie agenta do komputera jest konfigurowane przez 10 godzin i jest więcej niż 24 godziny przed upływem ostatecznego terminu, wyświetlany zestaw opcji czuwania do, ale nigdy nie większa niż 10 godzin. Zbliża się termin mniej opcji są, zgodnie z odpowiednimi ustawieniami agenta klienta dla każdego składnika oś czasu wdrożenia.

Ponadto dla wdrożenia o wysokim ryzyku, takie jak sekwencji zadań, która wdraża system operacyjny, proces powiadamiania użytkownika jest teraz bardziej niepożądanego. Zamiast powiadomień paska zadań przejściowy, zawsze, gdy użytkownik zostanie powiadomiony, że konserwacji krytyczne oprogramowanie jest wymagane okno dialogowe takich jak następujące wyświetla na komputerze użytkownika:

![Wymagane oprogramowanie okna dialogowego](media/client-toast-notification.png)


Aby uzyskać więcej informacji:
- [Ustawienia zarządzania wdrożeniami o wysokim ryzyku](../../../protect/understand/settings-to-manage-high-risk-deployments.md)
- [Jak skonfigurować ustawienia klienta](../../clients/deploy/configure-client-settings.md)

## <a name="software-updates-dashboard"></a>Pulpit nawigacyjny aktualizacji oprogramowania
Użyj nowego pulpitu nawigacyjnego aktualizacje oprogramowania, aby wyświetlić bieżący stan zgodności urządzeń w Twojej organizacji i szybsze analizowanie danych, aby zobaczyć, które urządzenia są zagrożone. Aby wyświetlić pulpit nawigacyjny, przejdź do **monitorowanie** > **Przegląd** > **zabezpieczeń** > **pulpitu nawigacyjnego aktualizacji oprogramowania**.

Aby uzyskać szczegółowe informacje, zobacz [monitorowania aktualizacji oprogramowania](/sccm/sum/deploy-use/monitor-software-updates).


## <a name="improvements-to-the-application-request-process"></a>Ulepszenia proces żądania aplikacji
Po zatwierdzeniu aplikacji dla instalacji, później możesz odrzuciła żądanie, klikając **Odmów** w konsoli programu Configuration Manager. Ten przycisk wygaszone została wcześniej, po zatwierdzeniu.

Ta akcja nie powoduje aplikacji do odinstalowania z dowolnego urządzenia. Jednak go zatrzymać użytkownikom instalowanie nowej kopii aplikacji z Centrum oprogramowania.

## <a name="filter-by-content-size-in-automatic-deployment-rules"></a>Filtrowanie według rozmiaru zawartości w zasadach wdrażania automatycznego
Teraz można filtrować na rozmiar zawartości dla aktualizacji oprogramowania w zasadach wdrażania automatycznego. Na przykład, aby pobrać tylko aktualizacje oprogramowania, które są mniejsze niż 2 MB, należy ustawić **zawartości rozmiar (KB)** odfiltrować **< 2048**. Za pomocą tego filtra zapobiega aktualizacji oprogramowania dużych automatyczne pobieranie obsługujący lepsze uproszczony Windows niskiego poziomu obsługi, gdy przepustowość sieci jest ograniczona. Aby uzyskać szczegółowe informacje Zobacz:
- [Program Configuration Manager i obsługi uproszczonego systemu Windows na dół poziomu systemy operacyjne](https://blogs.technet.microsoft.com/enterprisemobility/2016/10/07/configuration-manager-and-simplified-windows-servicing-on-down-level-operating-systems/)
- [Automatyczne wdrażanie aktualizacji oprogramowania](/sccm/sum/deploy-use/automatically-deploy-software-updates)

Aby skonfigurować **zawartości rozmiar (KB)** pola, wykonaj jedną z następujących czynności:
- Podczas tworzenia reguły wdrażania automatycznego w kreatorze tworzenia reguły wdrażania automatycznego, przejdź do **aktualizacji oprogramowania** strony.
- W oknie właściwości do istniejącej reguły wdrażania automatycznego, przejdź do **aktualizacji oprogramowania** kartę.

## <a name="office-365-client-management-dashboard"></a>Pulpit nawigacyjny zarządzania klientami usługi Office 365
Pulpit nawigacyjny zarządzania klientami usługi Office 365 jest teraz dostępny w konsoli programu Configuration Manager. Aby wyświetlić pulpit nawigacyjny, przejdź do **Biblioteka oprogramowania** > **Przegląd** > **Zarządzanie klientem usługi Office 365**.

Na pulpicie nawigacyjnym wykresy dla następujących elementów:

- Liczba klientów usługi Office 365
- Wersje klienta usługi Office 365
- Języki klienta usługi Office 365
- Kanały klienta usługi Office 365     

Aby uzyskać szczegółowe informacje, zobacz [aktualizuje zarządzania Office 365 ProPlus](/sccm/sum/deploy-use/manage-office-365-proplus-updates).

## <a name="task-sequence-steps-to-manage-bios-to-uefi-conversion"></a>Kroki sekwencji zadań w celu zarządzania systemu BIOS z interfejsem UEFI konwersji
Teraz można dostosować sekwencję zadań wdrażania systemu operacyjnego za pomocą nowej zmiennej TSUEFIDrive, tak aby **Uruchom ponownie komputer** krok przygotuje FAT32 partycji na dysku twardym przejścia do UEFI. Poniższa procedura zawiera przykładowy sposób tworzenia kroki sekwencji zadań, aby przygotować dysk twardy do systemu BIOS z interfejsem UEFI konwersji. Aby uzyskać szczegółowe informacje, zobacz [czynności sekwencji do zarządzania systemu BIOS z interfejsem UEFI konwersji](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion).

##  <a name="improvements-to-the-task-sequence-step-prepare-configmgr-client-for-capture"></a>Ulepszenia kroku sekwencji zadań: Prepare ConfigMgr Client for Capture  
Krok przygotować klienta programu ConfigMgr teraz spowoduje całkowite usunięcie klienta programu Configuration Manager, a nie tylko usunięcie informacji o kluczu. Po wdrożeniu przechwyconego obrazu systemu operacyjnego sekwencję zadań, zainstalowania nowego klienta programu Configuration Manager zawsze. Aby uzyskać szczegółowe informacje, zobacz [czynności sekwencji zadań](/sccm/osd/understand/task-sequence-steps#BKMK_PrepareConfigMgrClientforCapture).



## <a name="intune-compliance-policy-charts"></a>Wykresy zasady zgodności Intune
Teraz można uzyskać szybki widok ogólnej zgodności dla urządzeń i górnej przyczyn braku zgodności, przy użyciu nowych wykresów w obszarze **monitorowanie** obszaru roboczego w konsoli programu Configuration Manager. Po kliknięciu części na wykresie w celu przejścia do listy urządzeń w tej kategorii. Aby uzyskać szczegółowe informacje, zobacz [monitorowanie zasad zgodności](/sccm/protect/deploy-use/create-compliance-policy#monitor-the-compliance-policy).


## <a name="lookout-integration-for-hybrid-implementations-to-protect-ios-and-android-devices"></a>Integracja szczególną implementacji hybrydowe chronić iOS i android
Microsoft jest zintegrowanie z jego szczególną przenośnych zagrożenia ochrony rozwiązania ochrony wykrycia złośliwego oprogramowania, aplikacje ryzykowne i nie tylko na urządzeniach iOS i Android urządzeń przenośnych. Rozwiązanie firmy ewentualnym ułatwia określenie poziomu zagrożenia, które można konfigurować. Można utworzyć reguły zgodności w System Center Configuration Manager do ustalenia oparte na ocenie ryzyka przez ewentualnym zgodności urządzenia. Za pomocą zasad dostępu warunkowego, można umożliwić lub zablokowanie dostępu do zasobów firmy, w oparciu o stan zgodności urządzenia. Aby dowiedzieć się więcej o integracji i jak działa, zobacz [zarządzanie dostępem na podstawie urządzeń, sieci i aplikacji ryzyko](/sccm/protect/deploy-use/manage-access-based-on-device-network-app-risk).

Aby zarejestrować użytkowników urządzeń z systemem iOS niezgodnych pojawi się monit. Będą one trzeba instalować szukać pracy aplikacji na urządzeniach, aktywacja aplikacji i rozwiązywania problemów zagrożenia zgłaszane w szukać pracy aplikacji w celu uzyskania dostępu do danych firmy. Dowiedz się jak [Konfigurowanie i wdrażanie ewentualnym dla aplikacji do pracy](/sccm/protect/deploy-use/configure-and-deploy-lookout-for-work-apps).



## <a name="new-compliance-settings-for-configuration-items"></a>Nowe ustawienia zgodności dla elementów konfiguracji
Istnieje wiele nowe ustawienia, które można użyć w swoich elementów konfiguracji dla różnych platform urządzeń. Są to ustawienia, które wcześniej były dostępne w programie Microsoft Intune w konfiguracji autonomicznej i są teraz dostępne przy użyciu usługi Intune z programem Configuration Manager.
Aby uzyskać szczegółowe informacje, zobacz [elementów konfiguracji dla urządzeń zarządzanych bez klienta programu System Center Configuration Manager](/sccm/compliance/deploy-use/configuration-items-for-devices-managed-without-the-client).

### <a name="new-settings-for-android-devices"></a>Nowe ustawienia dla urządzeń z systemem Android
#### <a name="password-settings"></a>Ustawienia hasła
- **Pamiętaj historię haseł**
- **Zezwalaj na podstawie linii papilarnych odblokowania**

#### <a name="security-settings"></a>Ustawienia zabezpieczeń
- **Wymagaj szyfrowania kart pamięci**
- **Zezwalaj na przechwytywanie ekranu**
- **Zezwalaj na przesłanie danych diagnostycznych**

#### <a name="browser-settings"></a>Ustawienia przeglądarki
- **Zezwalaj na używanie przeglądarki sieci web**
- **Zezwalaj na automatyczne uzupełnianie**
- **Zezwalaj na blokowanie wyskakujących okienek**
- **Zezwalaj na pliki cookie**
- **Zezwalaj na wykonywanie aktywnych skryptów**

#### <a name="app-settings"></a>Ustawienia aplikacji
- **Zezwalaj na sklep Google Play**

#### <a name="device-capability-settings"></a>Ustawienia możliwości urządzenia
- **Zezwalaj na używanie magazynu wymiennego**
- **Zezwalaj na tethering Wi-Fi**
- **Zezwalaj na używanie funkcji geolokalizacji**
- **Zezwalaj na komunikację NFC**
- **Zezwalaj na połączenia Bluetooth**
- **Zezwalaj na Roaming połączeń głosowych**
- **Zezwalaj na roaming danych**
- **Zezwalaj na obsługę wiadomości SMS/MMS**
- **Zezwalaj na Asystenta głosowego**
- **Zezwalaj na wybieranie głosowe**
- **Zezwalaj na kopiowanie i wklejanie**

### <a name="new-settings-for-ios-devices"></a>Nowe ustawienia dla urządzeń z systemem iOS
#### <a name="password-settings"></a>Ustawienia hasła
- **Złożone wymagana liczba znaków w haśle**
- **Zezwalaj na proste hasła**
- **Liczba minut braku aktywności, zanim będzie wymagane hasło**
- **Pamiętaj historię haseł**

### <a name="new-settings-for-mac-os-x-devices"></a>Nowe ustawienia dla urządzeń z systemem Mac OS X
#### <a name="password-settings"></a>Ustawienia hasła
- **Złożone wymagana liczba znaków w haśle**
- **Zezwalaj na proste hasła**
- **Pamiętaj historię haseł**
- **Liczba minut braku aktywności przed włączeniem wygaszacza**

### <a name="new-settings-for-windows-10-desktop-and-mobile-devices"></a>Nowe ustawienia dla urządzeń z systemem Windows 10 Desktop oraz Mobile
#### <a name="password-settings"></a>Ustawienia hasła
- **Minimalna liczba zestawów znaków**
- **Pamiętaj historię haseł**
- **Wymagaj hasła, gdy urządzenie powraca ze stanu bezczynności**

#### <a name="security-settings"></a>Ustawienia zabezpieczeń
- **Wymagaj szyfrowania na urządzeniu przenośnym**
- **Zezwalaj na ręczne unenrollment**

#### <a name="device-capability-settings"></a>Ustawienia możliwości urządzenia
- **Zezwalaj na sieć VPN przez sieć komórkową**
- **Zezwalaj na roaming sieci VPN przez sieć komórkową**
- **Zezwalaj na resetowanie telefonu**
- **Zezwalaj na połączenie USB**
- **Zezwalaj na Cortana**
- **Zezwalaj na powiadomienia Centrum akcji**

### <a name="new-settings-for-windows-10-team-devices"></a>Nowe ustawienia dla urządzeń z systemem Windows 10 Team
#### <a name="device-settings"></a>Ustawienia urządzeń
- **Włącz usługi Azure Operational Insights**
- **Włącz Miracast projekcji bezprzewodowej**
- **Wybierz spotkania informacje wyświetlane na ekranie powitalnym**
- **Adres URL obrazu tła Lockscreen**

### <a name="new-settings-for-windows-81-devices"></a>Nowe ustawienia dla urządzeń Windows 8.1
#### <a name="applicability-settings"></a>Stosowanie ustawień
- **Zastosuj wszystkie konfiguracje dla systemu Windows 10**

#### <a name="password-settings"></a>Ustawienia hasła
- **Wymagany typ hasła**
- **Minimalna liczba zestawów znaków**
- **Minimalna długość hasła**
- **Liczba dopuszczalnych nieudanych logowań przed wyczyszczeniem danych z urządzenia**
- **Liczba minut braku aktywności przed wyłączeniem ekranu**
- **Wygaśnięcie hasła (dni)**
- **Pamiętaj historię haseł**
- **Zapobiegaj ponownemu używaniu poprzednich haseł**
- **Zezwalaj na hasło obrazkowe i numer PIN**

#### <a name="browser-settings"></a>Ustawienia przeglądarki
- **Zezwalaj na automatyczne wykrywanie sieci intranet**

### <a name="new-settings-for-windows-phone-81-devices"></a>Nowe ustawienia dla urządzeń Windows Phone 8.1
#### <a name="applicability-settings"></a>Stosowanie ustawień
- **Zastosuj wszystkie konfiguracje dla systemu Windows 10**

#### <a name="password-settings"></a>Ustawienia hasła
- **Minimalna liczba zestawów znaków**
- **Zezwalaj na proste hasła**
- **Pamiętaj historię haseł**

#### <a name="device-capability-settings"></a>Ustawienia możliwości urządzenia
- **Zezwalaj na automatyczne łączenie z bezpłatnymi punktami HotSpot Wi-Fi**

