---
title: Nowa wersja 1610
titleSuffix: Configuration Manager
description: "Uzyskiwanie szczegółowych informacji dotyczących zmian i nowych możliwości wprowadzonych w wersji 1610 programu System Center Configuration Manager."
ms.custom: na
ms.date: 11/23/2016
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f7eb0803-3f8f-4ab6-825a-99ac11f5ba7d
caps.latest.revision: "40"
author: mestew
ms.author: mstewart
manager: angrobe
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: e3dac4ceb08c15c1eaeef0a6006ebcc6eccff49c
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2017
---
# <a name="what39s-new-in-version-1610-of-system-center-configuration-manager"></a>Jaki &#39; s nowego w wersji 1610 programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Zaktualizuj 1610 dla bieżącej gałęzi programu System Center Configuration Manager jest dostępna jako aktualizacja w konsoli dla zainstalowanych wcześniej lokacji, które są uruchamiane w wersji 1511, 1602 lub 1606.


> [!TIP]  
> Aby zainstalować nową lokację, należy użyć wersji bazowej programu Configuration Manager.  
>  Dowiedz się więcej o:    
>  -   [Instalowanie nowej lokacji](https://technet.microsoft.com/library/mt590197.aspx)  
>  -   [Instalowanie aktualizacji w lokacjach](https://technet.microsoft.com/library/mt607046.aspx)  
>  -   [Wersje linii bazowej i aktualizacji](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions)  

Poniższe sekcje zawierają szczegółowe informacje dotyczące zmian i nowych możliwości wprowadzonych w wersji 1610 programu Configuration Manager.  


## <a name="in-console-monitoring-of-update-installation-status"></a>Monitorowanie stanu instalacji aktualizacji w konsoli  
Począwszy od wersji 1610, podczas instalacji pakietu aktualizacji i monitorowania instalacji w konsoli, brak nowej fazy: **Po zakończeniu instalacji**. Ta faza obejmuje stan zadania, takie jak ponowne uruchomienie najważniejszych usług i zainicjowanie monitorowania replikacji. (Ta faza nie jest dostępne w konsoli dopiero po aktualizacji lokacji do wersji 1610). Aby uzyskać więcej informacji na temat stanu instalacji aktualizacji, zobacz [instalacja aktualizacji w konsoli](/sccm/core/servers/manage/install-in-console-updates#a-namebkmkinstalla-install-in-console-updates).


## <a name="exclude-clients-from-automatic-upgrade"></a>Wyklucz z automatycznego uaktualnienia klientów
Klienci z systemem Windows można wykluczyć z pobierania uaktualniony przy użyciu nowej wersji oprogramowania klienckiego. Aby to zrobić, możesz obejmują komputery klienckie w kolekcji, który został określony do wykluczenia z uaktualnienia. Klienci w kolekcji wykluczonych zignorować żądań dotyczących aktualizacji oprogramowania klienckiego.  Aby uzyskać więcej informacji, zobacz [wykluczyć klientów systemu Windows z uaktualnień](../../clients/manage/upgrade/exclude-clients-windows.md).


## <a name="improvements-for-boundary-groups"></a>Ulepszenia grup granic
Wersji 1610 wprowadzono istotne zmiany do grupy granic oraz ich współdziałaniu z punktami dystrybucji. Te zmiany można uprościć projektowania infrastruktury zawartości podczas zapewniając większą kontrolę nad jak i kiedy klienci powrotu do wyszukiwania dystrybucji dodatkowe punkty jako lokalizacji źródła zawartości. W tym zarówno lokalnie, jak i punkty dystrybucji w chmurze.
Te ulepszenia zastąpienie pojęcia i zachowania, które może być znasz (np. Konfigurowanie punktów dystrybucji jako dużą lub małą). Nowy model powinien być łatwiejsze do konfiguracji i utrzymania. Te zmiany przygotowawczych także przyszłe zmiany, które poprawią inne role systemu lokacji, które można powiązać do grup granic.

Podczas aktualizacji do wersji 1610 aktualizacji konwertuje bieżącej konfiguracji grupy granic do nowego modelu tak, aby te zmiany nie przeszkadzać istniejącej konfiguracji dystrybucji zawartości.

Aby uzyskać więcej informacji, zobacz [grup granic](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#a-namebkmkboundarygroupsa-boundary-groups).


## <a name="peer-cache-for-content-distribution-to-clients"></a>Równorzędnej pamięci podręcznej w celu dystrybucji zawartości do klientów
Począwszy od wersji 1610, klient **równorzędnej pamięci podręcznej** pomaga w zarządzaniu wdrażaniem zawartości dla klientów w lokalizacjach zdalnych. Równorzędna pamięć podręczna jest wbudowane rozwiązanie klientom na współużytkowanie zawartości z innymi klientami bezpośrednio z lokalnej pamięci podręcznej programu Configuration Manager.

Po wdrożeniu ustawień klienta umożliwiających Buforowanie równorzędne kolekcji elementy członkowskie tej kolekcji może działać jako źródło zawartości elementu równorzędnego dla innych klientów w tej samej grupy granic.

Można również użyć nowej **źródła danych klienta** pulpit nawigacyjny, aby zrozumieć użycie źródeł zawartości równorzędnej pamięci podręcznej w danym środowisku.

> [!TIP]  
> Wersją 1610 równorzędnej pamięci podręcznej i pulpit nawigacyjny źródła danych klienta są funkcje wersji wstępnej. Aby je włączyć, zobacz [korzystanie z funkcji wersji wstępnej aktualizacje](/sccm/core/servers/manage/install-in-console-updates#bkmk_prerelease).

Aby uzyskać więcej informacji, zobacz [buforowania równorzędnego klientów programu Configuration Manager](/sccm/core/plan-design/hierarchy/client-peer-cache), i [źródła danych klienta pulpitu nawigacyjnego](/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed#client-data-sources-dashboard).


## <a name="migrate-multiple-shared-distribution-points-at-the-same-time"></a>Migrowanie wielu współużytkowanych punktów dystrybucji w tym samym czasie
Teraz można używać opcji **ponowne przypisanie punktu dystrybucji** mają proces programu Configuration Manager równolegle ponownego przypisania do 50 współużytkowanych punktów dystrybucji, w tym samym czasie. Przed tą wersją punktów dystrybucji ponownie przypisane zostały przetworzone pojedynczo. Aby uzyskać więcej informacji, zobacz [migracji wiele współużytkowanych punktów dystrybucji w tym samym czasie](/sccm/core/migration/planning-a-content-deployment-migration-strategy#migrate-multiple-shared-distribution-points-at-the-same-time).

## <a name="cloud-management-gateway-for-managing-internet-based-clients"></a>Brama zarządzania chmury do zarządzania klientami internetowymi

Brama zarządzania w chmurze zapewnia prosty sposób zarządzać klientami programu Configuration Manager w Internecie. Zarządzanie bramy usługi w chmurze, która została wdrożona do systemu Microsoft Azure i wymaga subskrypcji platformy Azure, nawiązuje połączenie z lokalnej infrastruktury programu Configuration Manager przy użyciu nowej roli wywołuje punkt połączenia z chmurą zarządzania bramy. Gdy ma ona całkowicie wdrożone i skonfigurowane, klienci mogą komunikować się z ról systemu lokacji programu Configuration Manager lokalnymi i punkty dystrybucji w chmurze, niezależnie od tego, czy są one połączone siecią wewnętrzną prywatnych lub w Internecie. Aby uzyskać więcej informacji i aby zobaczyć, jak brama zarządzania chmury porównuje z klienta internetowego zarządzania, zobacz [zarządzać klientami w Internecie](/sccm/core/clients/manage/manage-clients-internet).

## <a name="improvements-to-the-windows-10-edition-upgrade-policy"></a>Ulepszenia zasad uaktualniania wersji systemu Windows 10
W tej wersji wprowadzono następujące ulepszenia do tego typu zasad:

- Można teraz używać zasad uaktualniania wersji z 10 komputerów z systemem Windows uruchom klienta programu Configuration Manager, oprócz komputerów z systemem Windows 10 zarejestrowanych w usłudze Microsoft Intune.
- Windows 10 Professional można uaktualnić do żadnej platformy w kreatorze, które są zgodne ze sprzętem.

## <a name="manage-hardware-identifiers"></a>Zarządzanie identyfikatory sprzętu
Teraz można podać listę identyfikatorów, które ignorować programu Configuration Manager na potrzeby rejestracji rozruchu i klient PXE sprzętu. Istnieją dwie typowe problemy, które ułatwia to adres:

1. Wiele urządzeń, takich jak 3 Surface Pro, nie dołączaj wewnętrznego portu sieci Ethernet. Karta USB do Ethernet jest zazwyczaj używany do ustanawiania połączenia przewodowego na potrzeby wdrażania systemu operacyjnego. Jednak z powodu kosztów i użyteczność ogólne są często udostępnionego adaptera. Ponieważ adresu MAC ta karta służy do identyfikowania urządzenia, ponowne użycie karty staje się problemem bez administratora dodatkowe akcje między każdym wdrożeniu. Teraz w 1610 wersji programu Configuration Manager, można wykluczyć adres MAC tej karty, dzięki czemu można łatwo nastąpić w tym scenariuszu.
2. Identyfikator SMBIOS powinien być unikatowy identyfikator sprzętu, ale niektóre urządzenia specjalistyczne są tworzone za zduplikowane identyfikatory. Ten problem może nie być jako wspólne, jak w scenariuszu karty USB do Ethernet tylko opisane, ale można go rozwiązać przy użyciu listy wykluczeń identyfikatory sprzętu.

Aby uzyskać więcej informacji, zobacz [Zarządzaj sprzętu zduplikowane identyfikatory](/sccm/core/clients/manage/manage-clients#manage-duplicate-hardware-identifiers).

## <a name="enhancements-to-windows-store-for-business-integration-with-configuration-manager"></a>Rozszerzenia do Sklepu Windows dla firm integracji z programem Configuration Manager
Zmiany w tej wersji:
- Wcześniej można wdrażać tylko bezpłatnych aplikacji ze Sklepu Windows dla firm. Configuration Manager teraz również obsługują wdrażanie płatności online licencjonowane aplikacje (tylko urządzenia zarejestrowane w usłudze Intune).
- Teraz można zainicjować natychmiastową synchronizację między Sklep Windows dla firm i programie Configuration Manager.
- Teraz można zmodyfikować klucza tajnego klienta, które zostały uzyskane z usługi Azure Active Directory.
- Można usunąć subskrypcji w magazynie.

Aby uzyskać więcej informacji, zobacz [Zarządzanie aplikacjami ze Sklepu Windows dla firm z System Center Configuration Manager](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business).


## <a name="policy-sync-for-intune-enrolled-devices"></a>Zasada synchronizacji dla urządzenia zarejestrowane w usłudze Intune
Zasada synchronizacji urządzenia zarejestrowane w usłudze Intune można teraz żądanie z poziomu konsoli programu Configuration Manager, bez konieczności żądania synchronizacji z aplikacji Portal firmy na urządzeniu. Informacje o stanie żądanie synchronizacji jest dostępna jako nową kolumnę w widokach urządzenia o nazwie **stan synchronizacji zdalnej**. Informacje są także dostępne w sekcji danych odnajdywania **właściwości** okna dialogowego dla każdego urządzenia.
Aby uzyskać więcej informacji, zobacz [zdalnie synchronizować zasady na zarejestrowane w usłudze Intune urządzenia z konsoli programu Configuration Manager](/sccm/mdm/deploy-use/sync-intune-device).


## <a name="use-compliance-settings-to-configure-windows-defender-settings"></a>Ustawienia zgodności umożliwiają konfigurowanie ustawień usługi Windows Defender
Można teraz skonfigurować ustawienia klienta usługi Windows Defender na komputerach zarejestrowanych w usłudze Intune systemu Windows 10 przy użyciu elementów konfiguracji w konsoli programu Configuration Manager.
Aby uzyskać więcej informacji, zobacz **usługa Windows Defender** sekcji [tworzenie elementów konfiguracji dla urządzeń Windows 8.1 i Windows 10 zarządzanych bez klienta programu System Center Configuration Manager](/sccm/compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client).



## <a name="general-improvements-to-software-center"></a>Ogólne ulepszenia Centrum oprogramowania
- Użytkownicy mogą teraz zażądać aplikacji z Centrum oprogramowania, a także z katalogu aplikacji.
- Ulepszenia, aby ułatwić użytkownikom zrozumienie, jakie oprogramowanie jest nowy i odpowiednie.

## <a name="new-columns-in-device-collection-views"></a>Nowe kolumny w widokach kolekcji urządzeń
Można teraz wyświetlić kolumn dla **IMEI** i **numer seryjny** (dla systemu IOS) w widokach kolekcji urządzeń.
Aby uzyskać więcej informacji, zobacz [wstępna deklaracja urządzeń z numery IMEI lub iOS za](https://docs.microsoft.com/sccm/mdm/deploy-use/predeclare-devices-with-hardware-id).

## <a name="customizable-branding-for-software-center-dialogs"></a>Można dostosować, znakowania w oknach dialogowych programu Software Center
Znakowanie niestandardowych w programie Software Center wprowadzono w programie Configuration Manager w wersji 1602. W wersji 1610 tego znakowania jest rozszerzona na wszystkie skojarzone okna dialogowe zapewnia lepsze środowisko użytkownikom Centrum oprogramowania.

Znakowanie niestandardowych w programie Software Center jest stosowane zgodnie z następującymi zasadami:

- Jeśli nie zainstalowano roli serwera lokacji punktu witryny sieci Web katalogu aplikacji, a następnie Centrum oprogramowania wyświetlana nazwa organizacji określona w **Agent komputera** ustawienia klienta **nazwa organizacji wyświetlana w Centrum oprogramowania**. Aby uzyskać instrukcje, zobacz [sposób konfigurowania ustawień klienta](../../clients/deploy/configure-client-settings.md).

- Po zainstalowaniu roli serwera lokacji punktu witryny sieci Web katalogu aplikacji programu Software Center wyświetla nazwę organizacji i kolor określone we właściwościach roli serwera lokacji katalogu aplikacji witryny sieci Web punktu. Aby uzyskać więcej informacji, zobacz [opcji konfiguracji dla punktu witryny sieci Web katalogu aplikacji](/sccm/core/servers/deploy/configure/configuration-options-for-site-system-roles#Application-Catalog-website-point).

- Jeśli subskrypcję Microsoft Intune jest skonfigurowana i podłączone do środowiska programu Configuration Manager, programu Software Center wyświetla nazwę organizacji, kolor i logo firmy określone we właściwościach subskrypcji usługi Intune. Aby uzyskać więcej informacji, zobacz [Konfigurowanie subskrypcji usługi Microsoft Intune](/sccm/mdm/deploy-use/setup-hybrid-mdm#step-3-configure-intune-subscription).


## <a name="enforcement-grace-period-for-required-application-and-software-update-deployments"></a>Okres prolongaty wymuszania dla wdrożeń wymaganych aplikacji i aktualizacji oprogramowania
W niektórych przypadkach można umożliwić użytkownikom więcej czasu do instalacji wymagane wdrożenia aplikacji lub aktualizacji oprogramowania poza wszystkie terminy skonfigurowane. Na przykład może to być konieczne, gdy komputer została wyłączona przez dłuższy czas i należy go zainstalować dużą liczbę wdrożeń aplikacji lub aktualizacji. Na przykład jeśli użytkownik końcowy zwrócił się tylko z urlopu, ich może być konieczne Zaczekaj, aż do postaci długiej jako zaległe aplikacji są zainstalowane wdrożeń. Aby rozwiązać ten problem, można zdefiniować okres prolongaty wymuszania przez wdrożenie ustawienia klienta programu Configuration Manager do kolekcji. 

Aby skonfigurować okres prolongaty, należy wykonać następujące czynności:
1.      Na **Agent komputera** strony ustawień klienta, należy skonfigurować nową właściwość **okres prolongaty wymuszania po wdrożeniu terminu wdrożenia (godziny)** z wartością pomiędzy **1** i **120** godzin.
2.      W ramach nowego wdrożenia wymaganej aplikacji lub we właściwościach istniejącego wdrożenia na **Planowanie** strony, zaznacz pole wyboru **Opóźnij wymuszenie dotyczące tego wdrożenia zgodnie z preferencjami użytkownika do okresu prolongaty zdefiniowanego w ustawieniach klienta**. Wszystkie wdrożenia, to zaznaczone pole wyboru, które są przeznaczone dla urządzeń, na których wdrożono również ustawienie, klienta użyje okres prolongaty wymuszania.

Skonfiguruj okres prolongaty wymuszania, zaznacz pole wyboru, po osiągnięciu ostatecznego terminu instalacji aplikacji zostanie zainstalowany w pierwszym oknie-business skonfigurowanego przez użytkownika do tego okresu prolongaty. Jednak użytkownik może nadal otworzyć programu Software Center i zainstalować aplikację w dowolnym momencie, które mają. Po wygaśnięciu okresu prolongaty wymuszania wraca do normalnej zachowaniem wdrożeń zaległe. Podobne opcje zostały dodane do Kreatora wdrażania aktualizacji oprogramowania, Kreator reguł wdrażania automatycznego i strony właściwości.



## <a name="improved-functionality-in-dialog-boxes-about-required-software"></a>Udoskonalone funkcje w oknach dialogowych dotyczące wymaganego oprogramowania
Kiedy użytkownik odbiera wymaganego oprogramowania, z **Odłóż i Przypomnij:** ustawienie, można wybrać z listy rozwijanej następujące wartości: 
- **Później**. Określa, czy powiadomienia zostały zaplanowane na podstawie ustawień powiadomień skonfigurowanego w ustawieniach agenta klienta.
- **Stały czas**. Określa, że powiadomienie zostanie zaplanowane do wyświetlenia ponownie po zaznaczony czas (na przykład w 30 minut).

![Konfiguracja agenta w ustawieniach agenta klienta](media/client-notification-settings.png)

Czas włączenia trybu czuwania maksymalna jest oparty na wartości powiadomień skonfigurowanego w ustawieniach agenta klienta. Na przykład jeśli **wdrożenia termin ostateczny dłuższego niż 24 godziny, przypominaj użytkowników co (godziny)** ustawienie na komputerze agenta strona jest skonfigurowana do 10 godzin i jest dłuższy niż 24 godziny przed upływem ostatecznego terminu, zestaw opcji włączenia trybu czuwania do, ale nigdy nie większa niż 10 godzin będzie widoczny dla użytkownika. Mniej opcji zbliża się termin, są dostępne, zgodnie z odpowiednimi ustawieniami agenta klienta dla każdego składnika oś czasu wdrożenia.

Ponadto dla wysokiego ryzyka, takiego jak wdrożenie sekwencji zadań, która wdraża system operacyjny użytkowników powiadomień jest teraz bardziej natrętnych. Zamiast przejściowej zadań powiadomienie o każdym razem, gdy użytkownik jest powiadamiany, że konserwacji krytyczne oprogramowanie jest wymagane okno dialogowe takie jak następujące wyświetla na komputerze użytkownika:

![Wymagane oprogramowanie okna dialogowego](media/client-toast-notification.png)


Aby uzyskać więcej informacji:
- [Ustawienia zarządzania wdrożeniami o wysokim ryzyku](../../../protect/understand/settings-to-manage-high-risk-deployments.md)
- [Jak skonfigurować ustawienia klienta](../../clients/deploy/configure-client-settings.md)

## <a name="software-updates-dashboard"></a>Pulpit nawigacyjny aktualizacji oprogramowania
Użyj nowego pulpitu nawigacyjnego aktualizacje oprogramowania, aby wyświetlić bieżący stan zgodności urządzeń w Twojej organizacji i szybsze analizowanie danych, aby sprawdzić, które urządzenia są narażeni na ataki. Aby wyświetlić pulpit nawigacyjny, przejdź do **monitorowanie** > **omówienie** > **zabezpieczeń** > **pulpitu nawigacyjnego aktualizacje oprogramowania**.

Aby uzyskać więcej informacji, zobacz [monitorowanie aktualizacji oprogramowania](/sccm/sum/deploy-use/monitor-software-updates).


## <a name="improvements-to-the-application-request-process"></a>Ulepszenia procesu żądania aplikacji
Po zatwierdzeniu aplikacji do instalacji, później możesz odrzuciła żądanie, klikając **Odmów** w konsoli programu Configuration Manager. Ten przycisk, wygaszone została wcześniej, po zatwierdzeniu.

Ta akcja nie powoduje aplikacji ma zostać odinstalowany z dowolnego urządzenia. Jednak powoduje ono zaprzestanie użytkownikom instalowanie nowych kopii aplikacji z Centrum oprogramowania.

## <a name="filter-by-content-size-in-automatic-deployment-rules"></a>Filtruj według rozmiaru zawartości w regułach wdrażania automatycznego
Teraz można filtrować na rozmiar zawartości dla aktualizacji oprogramowania w zasadach wdrażania automatycznego. Na przykład, aby pobrać tylko aktualizacje oprogramowania, które są mniejsze niż 2 MB, należy ustawić **zawartości rozmiar (KB)** filtrowane w celu **< 2048**. Przy użyciu tego filtru uniemożliwia aktualizacje oprogramowania dużych automatyczne pobieranie, który lepiej obsługuje uproszczony Windows niższego poziomu obsługi, gdy przepustowość sieci jest ograniczona. Aby uzyskać więcej informacji zobacz:
- [Program Configuration Manager i obsługa uproszczonego systemu Windows na dół poziomu systemów operacyjnych](https://blogs.technet.microsoft.com/enterprisemobility/2016/10/07/configuration-manager-and-simplified-windows-servicing-on-down-level-operating-systems/)
- [Automatyczne wdrażanie aktualizacji oprogramowania](/sccm/sum/deploy-use/automatically-deploy-software-updates)

Aby skonfigurować **zawartości rozmiar (KB)** pola, wykonaj jedną z następujących czynności:
- Podczas tworzenia reguły wdrażania automatycznego, w kreatorze tworzenia reguły wdrażania automatycznego, przejdź do **aktualizacji oprogramowania** strony.
- We właściwościach istniejącej reguły wdrażania automatycznego, przejdź do **aktualizacji oprogramowania** kartę.

## <a name="office-365-client-management-dashboard"></a>Pulpit nawigacyjny zarządzania klienta usługi Office 365
Pulpit nawigacyjny zarządzania usługi Office 365 klienta jest teraz dostępna w konsoli programu Configuration Manager. Aby wyświetlić pulpit nawigacyjny, przejdź do **Biblioteka oprogramowania** > **omówienie** > **zarządzania klienta usługi Office 365**.

Pulpit nawigacyjny Wyświetla wykresy dla następujących elementów:

- Liczba klientów usługi Office 365
- Wersje klienta usługi Office 365
- Języki klienta usługi Office 365
- Kanały klienta usługi Office 365     

Aby uzyskać więcej informacji, zobacz [aktualizacji z zarządzania usługi Office 365 ProPlus](/sccm/sum/deploy-use/manage-office-365-proplus-updates).

## <a name="task-sequence-steps-to-manage-bios-to-uefi-conversion"></a>Kroki sekwencji zadań do zarządzania systemem BIOS do konwersji UEFI
Dostosuj sekwencję zadań wdrażania systemu operacyjnego z nową zmienną TSUEFIDrive, dzięki czemu **Uruchom ponownie komputer** krok przygotuje FAT32 partycji na dysku twardym przejścia do UEFI. Poniższa procedura zawiera przykładowy sposób tworzenia kroków sekwencji zadań, aby przygotować dysk twardy dla systemu BIOS z interfejsem UEFI konwersji. Aby uzyskać więcej informacji, zobacz [zadania sekwencji kroki, aby zarządzać systemu BIOS z interfejsem UEFI konwersji](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion).

##  <a name="improvements-to-the-task-sequence-step-prepare-configmgr-client-for-capture"></a>Ulepszenia kroku sekwencji zadań: Prepare ConfigMgr Client for Capture  
Przygotuj klienta programu ConfigMgr krok teraz spowoduje całkowite usunięcie klienta programu Configuration Manager, a nie tylko usunięcie informacji o kluczu. Jeśli sekwencja zadań wdrażania przechwyconego obrazu systemu operacyjnego, zainstaluje nowy klient programu Configuration Manager zawsze. Aby uzyskać więcej informacji, zobacz [czynności sekwencji zadań](/sccm/osd/understand/task-sequence-steps#BKMK_PrepareConfigMgrClientforCapture).



## <a name="intune-compliance-policy-charts"></a>Wykresy zasad zgodności usługi Intune
Teraz można uzyskać szybki przegląd ogólnej zgodności dla urządzeń, a górnej przyczyn braku zgodności, przy użyciu nowych wykresów w obszarze **monitorowanie** obszaru roboczego w konsoli programu Configuration Manager. Możesz kliknąć części na wykresie, aby następnie przejść do listy urządzeń w tej kategorii. Aby uzyskać więcej informacji, zobacz [monitorowanie zasad zgodności](/sccm/protect/deploy-use/create-compliance-policy#monitor-the-compliance-policy).


## <a name="lookout-integration-for-hybrid-implementations-to-protect-ios-and-android-devices"></a>Lookout integracji dla hybrydowych wdrożeń do ochrony urządzeń iOS i Android
Microsoft jest integracja z rozwiązaniem ochrony przenośnych zagrożeń Lookout firmy do ochrony został określony poprzez wykrycie złośliwego oprogramowania, ryzykowne aplikacje i inne, na urządzeniach z systemem iOS i Android urządzeń przenośnych. Lookout przez rozwiązanie pomaga ustalić poziom zagrożenia, które można skonfigurować. Można utworzyć reguły zgodności programu System Center Configuration Manager do ustalenia zgodności urządzenia oparte na ocenie ryzyka przez aplikację Lookout. Korzystając z zasad dostępu warunkowego, można akceptować lub blokowanie dostępu do zasobów firmy na podstawie stanu zgodności urządzenia. Informacje na temat integracji i jej działania, zobacz [zarządzanie dostępem na podstawie urządzeń, sieci i aplikacji ryzyka](/sccm/protect/deploy-use/manage-access-based-on-device-network-app-risk).

Użytkownicy urządzeń niezgodnych z systemem iOS będą się monit o zarejestrowanie. Będą one musieli instalować aplikację Lookout for Work aplikacji na urządzeniach, aktywować aplikację i eliminowanie zagrożeń w poszukaj pracy aplikacji do uzyskiwania dostępu do danych firmowych. Dowiedz się, jak [Konfigurowanie i wdrażanie Lookout dla aplikacji służbowych](/sccm/protect/deploy-use/configure-and-deploy-lookout-for-work-apps).



## <a name="new-compliance-settings-for-configuration-items"></a>Nowe ustawienia zgodności dla elementów konfiguracji
Istnieje wiele nowych ustawień, które można używać we wszystkich elementach konfiguracji dla różnych platform urządzeń. Są to ustawienia, które wcześniej były dostępne w programie Microsoft Intune w konfiguracji autonomicznej i są teraz dostępne podczas korzystania z usługi Intune z programem Configuration Manager.
Aby uzyskać więcej informacji, zobacz [elementy konfiguracji dla urządzeń zarządzanych bez klienta programu System Center Configuration Manager](/sccm/compliance/deploy-use/configuration-items-for-devices-managed-without-the-client).

### <a name="new-settings-for-android-devices"></a>Nowe ustawienia dla urządzeń z systemem Android
#### <a name="password-settings"></a>Ustawienia hasła
- **Pamiętaj historię haseł**
- **Zezwalaj na odcisk palca odblokowania**

#### <a name="security-settings"></a>Ustawienia zabezpieczeń
- **Wymagaj szyfrowania na kartach pamięci**
- **Zezwalaj na przechwytywanie ekranu**
- **Zezwalaj na przesyłanie danych diagnostycznych**

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
- **Liczba znaków złożonych w haśle**
- **Zezwalaj na proste hasła**
- **Liczba minut braku aktywności, zanim będzie wymagane hasło**
- **Pamiętaj historię haseł**

### <a name="new-settings-for-mac-os-x-devices"></a>Nowe ustawienia dla urządzeń z systemem Mac OS X
#### <a name="password-settings"></a>Ustawienia hasła
- **Liczba znaków złożonych w haśle**
- **Zezwalaj na proste hasła**
- **Pamiętaj historię haseł**
- **Liczba minut braku aktywności przed uaktywnieniem wygaszacza ekranu**

### <a name="new-settings-for-windows-10-desktop-and-mobile-devices"></a>Nowe ustawienia dla urządzeń z systemem Windows 10 Desktop i Mobile
#### <a name="password-settings"></a>Ustawienia hasła
- **Minimalna liczba zestawów znaków**
- **Pamiętaj historię haseł**
- **Wymagaj hasła, gdy urządzenie powraca ze stanu bezczynności**

#### <a name="security-settings"></a>Ustawienia zabezpieczeń
- **Wymagaj szyfrowania na urządzeniu przenośnym**
- **Zezwalaj na ręczne Wyrejestrowanie**

#### <a name="device-capability-settings"></a>Ustawienia możliwości urządzenia
- **Zezwalaj na połączenia VPN przez sieć komórkową**
- **Zezwalaj na roaming VPN przez sieć komórkową**
- **Zezwalaj na resetowanie telefonu**
- **Zezwalaj na połączenie USB**
- **Zezwalaj na funkcję Cortana**
- **Zezwalaj na powiadomienia Centrum akcji**

### <a name="new-settings-for-windows-10-team-devices"></a>Nowe ustawienia dla urządzeń z systemem Windows 10 Team
#### <a name="device-settings"></a>Ustawienia urządzenia
- **Włącz usługę Azure Operational Insights**
- **Włącz projekcję bezprzewodową Miracast**
- **Wybierz informacje o spotkaniu wyświetlane na ekranie powitalnym**
- **Adres URL obrazu tła ekranu blokady**

### <a name="new-settings-for-windows-81-devices"></a>Nowe ustawienia dla urządzeń Windows 8.1
#### <a name="applicability-settings"></a>Ustawienia zastosowania
- **Zastosuj wszystkie konfiguracje dla systemu Windows 10**

#### <a name="password-settings"></a>Ustawienia hasła
- **Wymagany typ hasła**
- **Minimalna liczba zestawów znaków**
- **Minimalna długość hasła**
- **Liczba dopuszczalnych nieudanych logowań przed usunięciem zawartości urządzenia**
- **Liczba minut braku aktywności przed wyłączeniem ekranu**
- **Wygaśnięcie hasła (dni)**
- **Pamiętaj historię haseł**
- **Zapobiegaj ponownemu używaniu poprzednich haseł**
- **Zezwalaj na hasło obrazkowe i numer PIN**

#### <a name="browser-settings"></a>Ustawienia przeglądarki
- **Zezwalaj na automatyczne wykrywanie sieci intranet**

### <a name="new-settings-for-windows-phone-81-devices"></a>Nowe ustawienia dla urządzeń Windows Phone 8.1
#### <a name="applicability-settings"></a>Ustawienia zastosowania
- **Zastosuj wszystkie konfiguracje dla systemu Windows 10**

#### <a name="password-settings"></a>Ustawienia hasła
- **Minimalna liczba zestawów znaków**
- **Zezwalaj na proste hasła**
- **Pamiętaj historię haseł**

#### <a name="device-capability-settings"></a>Ustawienia możliwości urządzenia
- **Zezwalaj na automatyczne łączenie z bezpłatnymi punktami HotSpot Wi-Fi**
