---
title: Nowa wersja 1802
titleSuffix: Configuration Manager
description: Uzyskiwanie szczegółowych informacji dotyczących zmian i nowych możliwości wprowadzonych w wersji 1802 programu Configuration Manager.
ms.date: 04/11/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 5bd637b1-d7a1-411b-877a-c7aae9741173
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 776db45fe64cc54e6209ba3fc45737a053613c83
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="whats-new-in-version-1802-of-system-center-configuration-manager"></a>Nowości w wersji 1802 programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Zaktualizuj 1802 dla bieżącej gałęzi programu Configuration Manager jest dostępna jako aktualizacja w konsoli. W witrynach, w których jest uruchomiona wersja 1702, 1706 lub 1710, należy zastosować tę aktualizację. <!-- baseline only statement: -->Podczas instalowania nowej lokacji, jest również dostępny jako wersji linii bazowej.

Oprócz nowych funkcji ta wersja zawiera również dodatkowe zmiany, takie jak poprawki błędów. Aby uzyskać więcej informacji, zobacz [podsumowanie zmian w programie System Center Configuration Manager bieżącej gałęzi, wersja 1802](https://support.microsoft.com/help/4101375).

<!--
The following additional updates to this release are also now available:
- [Update rollup for System Center Configuration Manager current branch, version 1710](https://support.microsoft.com/help/4057517)
-->

> [!TIP]  
> Aby zainstalować nową lokację, należy użyć wersji bazowej programu Configuration Manager.  
>
>  Dowiedz się więcej o:    
>   - [Instalowanie nowej lokacji](/sccm/core/servers/deploy/install/installing-sites)  
>   - [Instalowanie aktualizacji w lokacjach](/sccm/core/servers/manage/updates)  
>   - [Wersje linii bazowej i aktualizacji](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions)  

Poniższe sekcje zawierają szczegółowe informacje dotyczące zmian i nowe funkcje w wersji 1802 programu Configuration Manager.  

<!--
## Deprecated features and operating systems
Learn about support changes before they are implemented in [removed and deprecated items](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated).

Version 1802 drops support for the following products:
-->


## <a name="site-infrastructure"></a>Infrastruktura lokacji

### <a name="reassign-distribution-point"></a>Ponowne przypisanie punktu dystrybucji
<!-- 1306937 -->
Wielu klientów mają duże infrastruktury programu Configuration Manager i ograniczają lokacjach głównych lub dodatkowych, aby uprościć ich środowiska. Nadal należy zachować punktów dystrybucji w oddziałach, aby obsługiwać zawartość dla klientów zarządzanych. Te punkty dystrybucji zawierają często wielu terabajtów lub więcej zawartości. Ta zawartość jest kosztowna pod względem przepustowości czasu i sieci do dystrybucji na tych serwerach zdalnych. Ta funkcja umożliwia ponowne przypisanie punktu dystrybucji do innej lokacji głównej bez dystrybucję zawartości. Aktualizuje przypisania systemu lokacji podczas utrwalanie całej zawartości na serwerze. Aby uzyskać więcej informacji, zobacz [ponownego przypisania punktu dystrybucji](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#bkmk_reassign).

### <a name="configure-windows-delivery-optimization-to-use-configuration-manager-boundary-groups"></a>Konfigurowanie optymalizacji dostarczania systemu Windows do użycia grup granic w programie Configuration Manager
<!-- 1324696 -->
Grupy granic w programie Configuration Manager służy do definiowania i uregulowanie dystrybucji zawartości w sieci firmowej i biurach zdalnych. [Optymalizacja dostarczania Windows](/windows/deployment/update/waas-delivery-optimization) jest oparta na chmurze, peer-to-peer technologii do udostępniania zawartości między urządzeniami z systemem Windows 10. Począwszy od tej wersji, skonfiguruj optymalizacji dostarczania do grup granic udostępniania zawartości między elementami równorzędnymi. Nowe ustawienie klienta stosuje identyfikator grupy granic, jako identyfikator grupy optymalizacji dostarczania na kliencie. Gdy klient komunikuje się z usługą w chmurze optymalizacji dostarczania, używa tego identyfikatora można zlokalizować elementów równorzędnych o żądanej zawartości. Aby uzyskać więcej informacji, zobacz [podstawowe pojęcia związane z zarządzaniem zawartością](/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management#delivery-optimization).

### <a name="support-for-windows-10-arm64-devices"></a>Obsługa urządzeń z systemem Windows 10 ARM64
<!-- 1353704 -->
Począwszy od tej wersji klienta programu Configuration Manager jest obsługiwana na urządzeniach z systemem Windows 10 ARM64. Istniejące funkcje zarządzania klient powinien współpracować z tych nowych urządzeń. Na przykład sprzętu i spisu oprogramowania, aktualizacji oprogramowania i zarządzania aplikacjami. Wdrożenie systemu operacyjnego nie jest obecnie obsługiwane. 

### <a name="improved-support-for-cng-certificates"></a>Ulepszona obsługa certyfikatów CNG
<!-- 1357314 -->
Wersja programu Configuration Manager (wersji current branch) 1710 obsługuje [kryptografii: Next Generation (CNG) certyfikaty](/sccm/core/plan-design/network/cng-certificates-overview). Obsługuje limity 1710 wersji do certyfikatów klienta w kilku scenariuszach. 

Począwszy od tej wersji, należy użyć certyfikatów CNG dla następujących ról serwera obsługującego protokół HTTPS:
- Punkt zarządzania
- Punkt dystrybucji
- Punkt aktualizacji oprogramowania
- punkt migracji stanu  


### <a name="boundary-group-fallback-for-management-points"></a>Grupy granic rezerwowy dla punktów zarządzania
<!-- 1324594 -->
Skonfiguruj rezerwowy relacje dla punktów zarządzania między [grup granic](/sccm/core/servers/deploy/configure/boundary-groups). To zachowanie zapewnia większą kontrolę dla punktów zarządzania używanych przez klientów. Aby uzyskać więcej informacji, zobacz [konfigurowania grup granic](/sccm/core/servers/deploy/configure/boundary-groups#management-points).


### <a name="cloud-distribution-point-site-affinity"></a>Koligacja lokacji punktu dystrybucji chmury
<!--503719-->
Ta funkcja korzysta z klientów z wieloma lokacjami, geograficznie hierarchii za pomocą punktów dystrybucji w chmurze. Podczas wyszukiwania zawartości klienta internetowego, wcześniej nie było żadnych zlecenia do listy punktów dystrybucji w chmurze odebranych przez klienta. To zachowanie może spowodować Klienci internetowi odbierania zawartości z punktów dystrybucji w chmurze odległymi geograficznie. Pobieranie zawartości z serwera odległości jest zwykle mniejsza niż bliżej serwera.
 
Koligacji lokacji punktu dystrybucji chmury internetowego klient otrzymuje listy uporządkowanej. Ta lista priorytetem punkty dystrybucji w chmurze z przypisanej lokacji klienta. To zachowanie umożliwia administratorowi Zachowaj opcje projektu ich pobierania zawartości z zasobów lokacji.
 

## <a name="management-insights"></a>Informacje na temat technologii zarządzania
<!-- 1353967 -->
Informacje na temat technologii zarządzania w programie System Center Configuration Manager zawierają informacje dotyczące bieżącego stanu środowiska. Informacje jest oparta na analizie danych z bazy danych lokacji. Szczegółowe informacje ułatwiają lepszego zrozumienia środowiska i podejmij działania oparte na wiedzę. Aby uzyskać więcej informacji, zobacz [Insights zarządzania](/sccm/core/servers/manage/management-insights)

W konfiguracji Menedżera 1802 dostępne są poniższe szczegółowe informacje:
- Aplikacje:
    - Aplikacje bez wdrożenia
- Usługi w chmurze: <!--1356412-->
    - Oceny gotowości zarządzania wspólnej 
    - Włącz urządzenia być hybrydowe przyłączonych do usługi Azure Active Directory
    - Modernizacji infrastruktury tożsamości i dostępu
    -  Uaktualnienie klientów systemu Windows 10 w wersji 1709 lub nowszy 
- Kolekcje:
    - Puste kolekcje
- Uproszczone zarządzanie:  <!--1355148-->
    - Wersje nieaktualnych klientów  
- Software Center: 
    - Bezpośrednie użytkownikom Centrum oprogramowania zamiast katalogu aplikacji  
    - Użycie nowej wersji Centrum oprogramowania 
- Windows 10: <!--1357421-->
    - Skonfiguruj telemetrii systemu Windows i komercyjnych klucza Identyfikatora 
    - Połącz gotowości do uaktualnienia program Configuration Manager 
   
<!-- ## Migration  -->



## <a name="client-management"></a>Zarządzanie klientami

### <a name="cloud-management-gateway-support-for-azure-resource-manager"></a>Obsługa brama zarządzania usługi Azure Resource Manager w chmurze
<!-- 1324735 -->
Podczas tworzenia wystąpienia [brama zarządzania chmury](/sccm/core/clients/manage/plan-cloud-management-gateway) (CMG), Kreator udostępnia teraz opcję, aby utworzyć **wdrożenia usługi Azure Resource Manager**. [Usługa Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview) nowoczesnych platforma do zarządzania wszystkimi zasobami rozwiązania jako pojedynczy element o nazwie [grupy zasobów](/azure/azure-resource-manager/resource-group-overview#resource-groups). W przypadku wdrażania CMG za pomocą Menedżera zasobów Azure, lokacji używa usługi Azure Active Directory (Azure AD) do uwierzytelniania i Utwórz zasoby niezbędne chmury. To wdrożenie zmodernizowanej nie wymaga certyfikatu zarządzania platformy Azure w klasycznym. Aby uzyskać więcej informacji, zobacz [projektowania topologii CMG](/sccm/core/clients/manage/plan-cloud-management-gateway#azure-resource-manager).

> [!IMPORTANT]
> Ta funkcja nie Włącz obsługę dla dostawców usług Azure chmurze (CSP). Wdrożenie CMG z usługi Azure Resource Manager w dalszym ciągu używa usługi w chmurze klasycznego, które nie obsługują dostawcy usług Kryptograficznych. Aby uzyskać więcej informacji, zobacz [usług Azure dostępne w dostawcy usług Kryptograficznych Azure](/azure/cloud-solution-provider/overview/azure-csp-available-services).  

### <a name="improvements-to-cloud-management-gateway"></a>Ulepszenia zarządzania bramy w chmurze  

- Począwszy od tej wersji **brama zarządzania chmury** nie jest już funkcji wersji wstępnej.  

- Dokumentacja funkcji jest zmian i rozszerzone. Aby uzyskać więcej informacji zobacz następujące artykuły:
    - [Planowanie brama zarządzania w chmurze](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway)
    - [Rozmiar bramy zarządzania w chmurze i skalowanie liczb](/sccm/core/plan-design/configs/size-and-scale-numbers#bkmk_cmg)
    - [Zabezpieczenia i prywatność bramy zarządzania chmurą](/sccm/core/clients/manage/cmg/security-and-privacy-for-cloud-management-gateway)
    - [Często zadawane pytania dotyczące zarządzania bramy chmury](/sccm/core/clients/manage/cmg/cloud-management-gateway-faq)
    - [Certyfikaty bramy zarządzania chmurą](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway)
    - [Konfigurowanie bramy zarządzania chmurą](/sccm/core/clients/manage/cmg/setup-cloud-management-gateway)  


### <a name="configure-hardware-inventory-to-collect-strings-larger-than-255-characters"></a>Konfigurowanie spisu sprzętu do zbierania ciągów więcej niż 255 znaków
<!-- 1357389 -->
Można skonfigurować długość ciągów, powinien być większy niż 255 znaków dla właściwości spisu sprzętu. Ta zmiana dotyczy tylko nowo dodane klasy i właściwości spisu sprzętu, które nie są klucze. Aby uzyskać więcej informacji, zobacz [rozszerzania spisu sprzętu](/sccm/core/clients/manage/inventory/extend-hardware-inventory#BKMK_GreaterThan255) artykułu. 

 ### <a name="deprecation-announcement-for-linux-and-unix-client-support"></a>Amortyzacja powiadomienia dla systemów Linux i Unix Obsługa klientów
 <!--510139-->
Firma Microsoft zamierza zastąpić Obsługa klientów systemu Linux i UNIX w programie System Center Configuration Manager mniej więcej co rok, taki, że klienci nie będą uwzględniane w SCCM 1902 wersji w kalendarzu wczesne 2019.  Wersja programu Configuration Manager 1810 w kalendarzu późne 2018, będzie ostatniej wersji, aby uwzględnić klienci systemu Linux i UNIX, i będą obsługiwane dla pełny cykl 1810 Menedżera konfiguracji.  Po 1810 Menedżera konfiguracji klienci powinni rozważyć firmy Microsoft Operations Management Suite do zarządzania serwerami z systemem Linux.  Ma OMS szeroką gamę Linux obsługują, które w większości przypadków przekroczenia funkcje programu Configuration Manager, w tym zarządzanie poprawkami end-to-end dla systemu Linux.

### <a name="surface-device-dashboard"></a>Pulpit nawigacyjny powierzchni urządzenia
<!--1355788-->
Pulpit nawigacyjny powierzchni urządzenia zawiera informacje o powierzchni urządzenia w danym środowisku. W konsoli przejdź do **monitorowanie** > **urządzeń Surface**. Aby wyświetlić elementy:
- procent powierzchni.
- procent powierzchni modeli
- Wersje oprogramowania układowego 5

Aby uzyskać więcej informacji, zobacz [powierzchni pulpitu nawigacyjnego](/sccm/core/clients/manage/surface-device-dashboard) artykułu.

### <a name="change-in-the-configuration-manager-client-install"></a>Zainstaluj zmiany w kliencie programu Configuration Manager
<!--1356195-->
Począwszy od tej wersji Silverlight nie jest już zainstalowane na urządzeniach klienckich automatycznie. Aby uzyskać więcej informacji, zobacz [wymagania wstępne dotyczące wdrażania klientów na komputerach z systemem Windows](/sccm/core/clients/deploy/prerequisites-for-deploying-clients-to-windows-computers#bkmk_ExternalDependencies)

## <a name="co-management"></a>Zarządzanie wspólnej

### <a name="transition-endpoint-protection-workload-to-intune-using-co-management"></a>Obciążenia programu Endpoint Protection przejścia do usługi Intune przy użyciu wspólnej zarządzania
<!-- 1357365 -->
 Obciążenia programu Endpoint Protection może zostać przeniesieni do usługi Intune po włączeniu wspólnego zarządzania. Do przejścia obciążenia programu Endpoint Protection, przejdź do strony właściwości wspólnego zarządzania i przesuń suwak z programu Configuration Manager do **pilotażu** lub **wszystkich**. Aby uzyskać szczegółowe informacje na temat obciążeń, zobacz [obciążenia mógł zostać przeniesieni do usługi Intune](/sccm/core/clients/manage/co-management-switch-workloads#Workloads-able-to-be-transitioned-to-Intune). Aby uzyskać więcej informacji na temat zarządzania wspólnej, zobacz [urządzenia zarządzania wspólnej dla systemu Windows 10](/sccm/core/clients/manage/co-management-overview).
 
### <a name="co-management-dashboard-in-system-center-configuration-manager"></a>Pulpit nawigacyjny wspólnej zarządzania w programie System Center Configuration Manager
<!--1356648-->
Począwszy od tej wersji, można wyświetlić pulpit nawigacyjny z informacjami o wspólnej zarządzania. Pulpit nawigacyjny pomaga Przejrzyj maszyny, które są zarządzane wspólnie w danym środowisku. Wykresy ułatwiają identyfikowanie urządzeń, które mogą wymagać uwagi. Aby uzyskać więcej informacji, zobacz [pulpit nawigacyjny zarządzania wspólnej](\sccm\core\clients\manage\client-management-dashboard) artykułu. 


## <a name="compliance-settings"></a>Ustawienia zgodności

### <a name="microsoft-edge-browser-policies"></a>Zasady przeglądarki Microsoft Edge
<!-- 1357310 -->
Dla klientów, którzy korzystają z [Microsoft Edge](https://technet.microsoft.com/microsoft-edge/bb265256) sieci web w przeglądarce na klientach systemu Windows 10, należy utworzyć zasady ustawień zgodności programu Configuration Manager, aby skonfigurować kilka ustawień Microsoft Edge. Aby uzyskać więcej informacji, zobacz [utworzyć Microsoft Edge przeglądarki profilu](/sccm/compliance/deploy-use/browser-profiles). 



## <a name="application-management"></a>Zarządzanie aplikacjami

### <a name="allow-user-interaction-when-installing-an-application"></a>Zezwala na interakcję użytkownika podczas instalowania aplikacji
<!-- 1356976 -->
Zezwalaj użytkownikowi na interakcji z instalacją aplikacji, podczas uruchamiania sekwencji zadań. Na przykład uruchomić proces instalacji, które monituje użytkownika końcowego dla różnych opcji. Niektóre programy instalacyjne nie wyłączeniu monity użytkownika lub proces instalacji może wymagać tylko znane użytkownikowi wartości określonej konfiguracji. Ta funkcja umożliwia obsługę tych scenariuszy instalacji. Aby uzyskać więcej informacji, zobacz [określenie opcji czynności użytkownika dotyczących typu wdrożenia](/sccm/apps/deploy-use/create-applications#specify-user-experience-options-for-the-deployment-type).

### <a name="do-not-automatically-upgrade-superseded-applications"></a>Nie uaktualniaj automatycznie zastąpionej aplikacji
<!-- 1351266 -->
Skonfiguruj wdrożenia aplikacji na automatycznie Uaktualnij wszystkie zastąpione wersje. Teraz podczas tworzenia wdrożenia, na **ustawienia wdrażania** strony **Kreatora wdrażania oprogramowania**, w obu **dostępne** lub **wymagane**zainstalować cel, można włączyć lub wyłączyć opcję **automatyczne uaktualnianie dowolnej wersji tej aplikacji zastąpione**. Aby uzyskać więcej informacji, zobacz [Określ ustawienia wdrożenia](/sccm/apps/deploy-use/deploy-applications#specify-deployment-settings).

### <a name="approve-application-requests-for-users-per-device"></a>Zatwierdzanie żądań aplikacji dla użytkowników na urządzenie
<!-- 1357015 -->
Uruchamianie w tej wersji, gdy użytkownik zażąda aplikację wymagającej zatwierdzenia, nazwę określonego urządzenia jest teraz częścią żądania. Administrator zatwierdza żądanie, użytkownik jest tylko możliwość instalowania aplikacji na tym urządzeniu. Użytkownik musi przesłać innego żądania, aby zainstalować aplikację na innym urządzeniu. Aby uzyskać więcej informacji, zobacz [Określ ustawienia wdrożenia](/sccm/apps/deploy-use/deploy-applications#specify-deployment-settings).

 > [!Note]  
 > Jest to opcjonalna funkcja. Aby uzyskać więcej informacji, zobacz [Włącz funkcje opcjonalne aktualizacji](/sccm/core/servers/manage/install-in-console-updates#bkmk_options).  


### <a name="run-scripts-improvements"></a>Uruchom skrypty ulepszenia 
<!-- 1236459 -->
 Począwszy od tej wersji **uruchamianie skryptów** nie jest już funkcji wersji wstępnej. Dane wyjściowe skryptu zwraca teraz przy użyciu formatowania JSON. Aby uzyskać więcej informacji, zobacz [tworzenia i uruchamiania skryptów programu PowerShell z poziomu konsoli programu Configuration Manager](/sccm/apps/deploy-use/create-deploy-scripts).


## <a name="operating-system-deployment"></a>Wdrożenie systemu operacyjnego

### <a name="windows-10-in-place-upgrade-task-sequence-via-cloud-management-gateway"></a>Sekwencji zadań uaktualniania w miejscu systemu Windows 10 za pośrednictwem bramy zarządzania w chmurze
<!-- 1357149 -->
Windows 10 [sekwencji zadań uaktualniania w miejscu](/sccm/osd/deploy-use/upgrade-windows-to-the-latest-version) teraz obsługuje wdrażanie na klientach internetowych zarządzanych za pomocą [brama zarządzania chmury](/sccm/core/clients/manage/plan-cloud-management-gateway). Dzięki tej możliwości użytkownicy zdalni łatwiej uaktualniania do systemu Windows 10, bez konieczności nawiązywania połączenia z siecią firmową. Aby uzyskać więcej informacji, zobacz [Wdrażanie sekwencji zadań](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#deploy-windows-10-in-place-upgrade-via-cmg).

### <a name="improvements-to-windows-10-in-place-upgrade-task-sequence"></a>Ulepszenia dotyczące sekwencji zadań uaktualniania w miejscu systemu Windows 10
<!-- 1357425 -->
Domyślny szablon sekwencji zadań dla uaktualnienia w miejscu systemu Windows 10 zawiera teraz dodatkowe grupy z zalecane działania, aby dodać przed i po zakończeniu uaktualniania. Te akcje są wspólne dla wielu klientów, którzy pomyślnie uaktualniania urządzeń do systemu Windows 10. Aby uzyskać więcej informacji, zobacz [Tworzenie sekwencji zadań w celu uaktualnienia systemu operacyjnego](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#recommended-task-sequence-steps-to-prepare-for-upgrade).

### <a name="improvements-to-operating-system-deployment"></a>Ulepszenia dotyczące wdrażania systemu operacyjnego
Ta wersja zawiera następujące ulepszenia dotyczące wdrażania systemu operacyjnego:
 - W systemie Windows PE, podczas uruchamiania cmtrace.exe już monit o wybranie, czy to program domyślnej przeglądarki dla plików dziennika. <!-- SMS 500897 -->
 - Dodawanie obrazów rozruchowych do [Pobierz zawartość pakietu](/sccm/osd/understand/task-sequence-steps#BKMK_DownloadPackageContent) krok sekwencji zadań.
 - Ulepszenia [uruchamiania sekwencji zadań](/sccm/osd/understand/task-sequence-steps#child-task-sequence) krok: <!-- 1261338 -->   
     - Obsługa wszystkich scenariuszy wdrożenia systemu operacyjnego z Centrum oprogramowania, środowiska PXE oraz nośnika.
     - Ulepszenia konsoli akcji, takich jak kopiowanie, importu, eksportu i ostrzeżenie podczas usuwania obiektu.
     - Obsługa [Utwórz wstępnie przygotowany plik zawartości](/sccm/core/plan-design/hierarchy/manage-network-bandwidth#BKMK_PrestagingContent) kreatora.
     - Integracja z weryfikację wdrożenia. Aby uzyskać więcej informacji, zobacz [wdrożeń sekwencji zadań o wysokim ryzyku](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#BKMK_DeployTS). 
     - Krok sekwencji zadań Uruchom można teraz używać na wielu poziomach sekwencji zadań, nie tylko relacje jeden nadrzędny podrzędny. Relacje wielopoziomowe zwiększenia złożoności, dlatego należy używać ostrożnie. Te relacje nadal są sprawdzane pod kątem odwołań cyklicznych.
    
### <a name="deployment-templates-for-task-sequences"></a>Szablony wdrażania dla sekwencji zadań
<!-- 1357391 -->
[Kreatora wdrażania dla sekwencji zadań](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#BKMK_DeployTS) można teraz utworzyć szablon wdrożenia. Szablon wdrożenia można zapisać i zastosowane do istniejącej lub nowej sekwencji zadań w celu utworzenia wdrożenia. 

### <a name="phased-deployments-for-task-sequences"></a>Etapowego wdrażania dla sekwencji zadań
<!--1356837-->
 Wdrożenia etapowego jest [funkcji wersji wstępnej](/sccm/core/servers/manage/pre-release-features). Wdrożenia etapowego zautomatyzować skoordynowane, Sekwencyjna wdrożenia sekwencji zadań w wielu kolekcjach. Możesz [tworzenie wdrożeń etapowe](/sccm/osd/deploy-use/create-phased-deployment-for-task-sequence) przy użyciu domyślnego dwóch faz, lub ręcznie skonfigurować faz. Etapowego wdrażania sekwencji zadań nie obsługuje instalacji środowiska PXE lub nośnika.




## <a name="software-center"></a>Centrum oprogramowania

### <a name="install-multiple-applications-in-software-center"></a>Zainstaluj wiele aplikacji w programie Software Center
<!-- 1357126 -->
Jeśli użytkownik końcowy lub pulpitu technika musi zainstalować wiele aplikacji na urządzeniu, Centrum oprogramowania obsługuje teraz instalowanie wielu wybranych aplikacji. Takie zachowanie umożliwia użytkownikowi efektywniejsze nie oczekując na zakończenie przed rozpoczęciem następnego jednej instalacji. Aby uzyskać więcej informacji, zobacz [zainstalować wiele aplikacji](/sccm/core/understand/software-center#install-multiple-applications) w podręczniku użytkownika Centrum oprogramowania.

### <a name="use-software-center-to-browse-and-install-user-available-applications-on-azure-ad-joined-devices"></a>Przeglądanie i instalowanie aplikacji dostępne dla użytkowników na urządzeniach przyłączonych do usługi AD platformy Azure przy użyciu programu Software Center
<!-- 1322613 -->
W przypadku wdrażania aplikacji jako dostępnych dla użytkowników mogą teraz Przeglądaj i zainstalować je za pomocą Centrum oprogramowania na urządzeniach w usłudze Azure Active Directory (Azure AD). Aby uzyskać więcej informacji, zobacz [wdrażać aplikacje dostępne dla użytkowników na urządzeniach przyłączonych do usługi AD platformy Azure](/sccm/apps/deploy-use/deploy-applications#deploy-user-available-applications-on-azure-ad-joined-devices).

### <a name="hide-installed-applications-in-software-center"></a>Ukryj zainstalowanych aplikacji w programie Software Center
<!--1357592-->
Teraz można ukryć zainstalowanych aplikacji w programie Software Center. Aplikacje, które są już zainstalowane nie będą już wyświetlane na karcie aplikacje po włączeniu tej opcji w obszarze Ustawienia klienta. Ta opcja jest ustawiona domyślnie podczas instalacji lub uaktualnienia do programu Configuration Manager 1802.  Zainstalowane aplikacje są nadal dostępne do przeglądu na karcie Stan instalacji. [Ukryj zainstalowane aplikacje w programie Software Center](/sccm/core/clients/deploy/about-client-settings#BKMK_HideInstalled) zawiera dodatkowe szczegóły.   

### <a name="hide-unapproved-applications-in-software-center"></a>Ukryj niezatwierdzonych aplikacji w programie Software Center
 <!--1355146-->
Po włączeniu tej opcji ustawienie klienta użytkownika dostępnych aplikacji, które wymagają zatwierdzenia są ukryte w programie Software Center.  [Ukryj niezatwierdzonych aplikacji w programie Software Center](/sccm/core/clients/deploy/about-client-settings#BKMK_HideUnapproved) zawiera dodatkowe szczegóły.  

### <a name="software-center-shows-user-additional-compliance-information"></a>Centrum oprogramowania zawiera informacje o zgodności dodatkowe użytkownika
<!-- 1235616 -->
 W przypadku używania stan zaświadczania o kondycji jako reguły zasad zgodności dla warunkowego dostępu do zasobów firmy, program Software Center zawiera obecnie użytkownika ustawienia zaświadczania o kondycji, który nie jest zgodny.


 ## <a name="software-updates"></a>Aktualizacje oprogramowania 

### <a name="schedule-automatic-deployment-rule-evaluation-to-be-offset-from-a-base-day"></a>Zaplanuj ocenę reguły automatycznego wdrażania do przesunięcia od dnia podstawowa. 
<!--1357133-->
Reguły wdrażania automatycznego można zaplanować do oceny przesunięcie od dnia podstawowa. To znaczy, jeśli poprawka wtorek faktycznie znajduje się w środę dla Ciebie, harmonogram oceny można ustawić dla drugi wtorek miesiąca przesunięcie przez jeden dzień. Aby uzyskać więcej informacji, zobacz [automatyczne wdrażanie aktualizacji oprogramowania](/sccm/sum/deploy-use/automatically-deploy-software-updates#BKMK_CreateAutomaticDeploymentRule). 



## <a name="reporting"></a>Raportowanie

### <a name="report-for-default-browser-counts"></a>Raport dotyczący liczby przeglądarka domyślna
<!-- 1357830 -->
Teraz jest nowy raport do wyświetlenia liczba klientów z przeglądarką internetową określonego jako domyślny systemu Windows. Zobacz **liczby domyślnej przeglądarki** raportu **oprogramowanie — firmy i produkty** grupy raporty. Aby uzyskać więcej informacji, zobacz [listę raportów](/sccm/core/servers/manage/list-of-reports#software---companies-and-products).

### <a name="report-on-windows-autopilot-device-information"></a>Raport dotyczący informacji o urządzeniu AutoPilot systemu Windows
<!-- 1351442 -->
AutoPilot systemu Windows to rozwiązanie dotyczące dołączania i konfigurowania nowych urządzeń z systemem Windows 10 w nowoczesnych sposób. Aby uzyskać więcej informacji, zobacz [AutoPilot omówienie Windows](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot). Jedną z metod rejestrowania istniejących urządzeń z systemem Windows AutoPilot jest przekazywanie informacji o urządzeniu do Store firmy Microsoft dla firm i Education. Informacje te obejmują numer seryjny urządzenia, identyfikator produktu systemu Windows i identyfikatora sprzętu. Użyj programu Configuration Manager do zbierania i raportowania tych informacji o urządzeniach nowy raport **informacje o urządzeniu AutoPilot Windows**w **sprzęt — ogólne** węzła Raporty. Aby uzyskać więcej informacji, zobacz [urządzeń nowego systemu Windows 10](/sccm/core/clients/manage/co-management-prepare#new-windows-10-devices) w celu przygotowania do wspólnego zarządzania.

### <a name="report-on-windows-10-servicing-details-for-a-specific-collection"></a>Raport dotyczący szczegółów obsługi systemu Windows 10 dla określonej kolekcji
<!--1357653-->
**Szczegóły obsługi systemu Windows 10 dla określonej kolekcji** raport wyświetla ogólne informacje na temat obsługi systemu Windows 10 dla określonej kolekcji. Ten raport przedstawia identyfikator zasobu, nazwy NetBIOS, nazwa systemu operacyjnego, Nazwa wersji systemu operacyjnego, kompilacji, gałąź systemu operacyjnego i obsługi stanu dla urządzeń z systemem Windows 10. Aby uzyskać więcej informacji, zobacz [listę raportów](/sccm/core/servers/manage/list-of-reports#operating-system)



<!-- ## Inventory  -->



<!-- ## Mobile device management -->



 ## <a name="protect-devices"></a>Ochrona urządzeń

### <a name="improvements-to-configuration-manager-policies-for-windows-defender-exploit-guard"></a>Ulepszenia zasad programu Configuration Manager dla usługi Windows Defender wykorzystać zabezpieczenia
<!-- 1356220 -->
Dodatkowe ustawienia zasad dla [służącym do zmniejszania możliwości ataków](/sccm/protect/deploy-use/create-deploy-exploit-guard-policy#BKMK_ASR) i [kontrolowany dostęp do folderu](/sccm/protect/deploy-use/create-deploy-exploit-guard-policy#BKMK_CFA) składniki zostały dodane w programie Configuration Manager dla [Guard wykorzystać programu Windows Defender ](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/windows-defender-exploit-guard).

### <a name="new-host-interaction-settings-for-windows-defender-application-guard"></a>Nowe ustawienia interakcji hosta dla programu Windows Defender aplikacji Guard
<!-- 1356256 -->
Dla wersji systemu Windows 10 1709 i urządzenia z nowszymi wersjami, istnieją dwa nowe ustawienia hosta interakcji dla [Windows Defender aplikacji Guard](/sccm/protect/deploy-use/create-deploy-application-guard-policy#BKMK_HIS): 
- Witryny sieci Web mogą mieć dostęp do procesora graficznego wirtualnego hosta. 
- Pliki pobierane wewnątrz kontenera może trwale znajdować się na hoście. 




## <a name="configuration-manager-console"></a>Konsola programu Configuration Manager

### <a name="improvements-to-the-configuration-manager-console"></a>Ulepszenia konsoli programu Configuration Manager 
Ta wersja zawiera następujące ulepszenia w konsoli programu Configuration Manager.
- Listy urządzeń w obszarze zasoby i zgodność, urządzeń, jest teraz wyświetlany głównego użytkownika domyślnie. W tej kolumnie są wyświetlane tylko w węźle urządzenia. Można również dodać ostatniego zalogowanego użytkownika jako opcjonalne kolumny.<!-- 1357280 --> Włącz [koligacji użytkownika i urządzenia](/sccm/core/clients/deploy/about-client-settings#user-and-device-affinity) ustawienia klienta dla witryny, aby skojarzyć głównego użytkownika z urządzeniem.
- Jeśli kolekcja jest członkiem innej kolekcji, a jego nazwa zostanie zmieniona, Nowa nazwa jest aktualizowana w ramach reguł członkostwa.<!--1357282--> 
- Przy użyciu zdalnego sterowania na komputerze klienckim z wieloma monitorami w różnych Skalowanie DPI, kursor myszy teraz prawidłowo mapuje między nimi. <!--433170-->
- [Pulpit nawigacyjny zarządzania klienta usługi Office 365](/sccm/sum/deploy-use/manage-office-365-proplus-updates#office-365-client-management-dashboard) Wyświetla listę odpowiednich urządzeń po wybraniu sekcje wykresu. <!--1357281 --> 



## <a name="next-steps"></a>Następne kroki
Jeśli wszystko jest gotowe do zainstalowania tej wersji, zobacz [aktualizacje programu Configuration Manager](/sccm/core/servers/manage/updates).
