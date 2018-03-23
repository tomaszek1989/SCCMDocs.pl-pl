---
title: Plan chmury zarządzania bramy
titleSuffix: Configuration Manager
description: Planowanie i projektowanie brama zarządzania chmury (CMG), aby uprościć zarządzanie klientów internetowych.
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology:
- configmgr-client
ms.assetid: 2dc8c9f1-4176-4e35-9794-f44b15f4e55f
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 614c5ba3acb81f90a75726e8783125fb53a39a93
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="plan-for-the-cloud-management-gateway-in-configuration-manager"></a>Planowanie brama zarządzania chmury w programie Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Brama zarządzania chmury (CMG) zapewnia prosty sposób zarządzać klientami programu Configuration Manager w Internecie. Wdrażając CMG jako usługa w chmurze w systemie Microsoft Azure, możesz zarządzać tradycyjnych klientów, którzy są przekazywane w Internecie, bez dodatkowej infrastruktury. Nie należy uwidaczniać infrastruktury lokalnej z Internetem. 

> [!Tip]  
> Ta funkcja została wprowadzona w wersji 1610 jako [funkcji wersji wstępnej](/sccm/core/servers/manage/pre-release-features). Począwszy od wersji 1802, ta funkcja nie jest już funkcji wersji wstępnej.

Po ustaleniu wymagań wstępnych, tworzenie CMG składa się z trzech kroków w konsoli programu Configuration Manager:
1. Usługi w chmurze CMG wdrażanie na platformie Azure.
2. Dodaj rolę punktu połączenia CMG. 
3. Konfigurowanie lokacji i role lokacji dla usługi. Po wdrożeniu i skonfigurowaniu klientów uzyskiwanie dostępu do lokalnego role lokacji niezależnie od tego, czy są one w intranecie lub Internecie.

Ten artykuł zawiera podstawowych wiedzy poznać CMG, jego miejsce w środowisku projektowania i planowania wdrożenia. 



## <a name="scenarios"></a>Scenariusze 

Istnieje kilka scenariuszy, w których jest korzystne CMG. Poniższe scenariusze są niektóre popularnych:  

- Zarządzanie tradycyjnych klientami z systemem Windows przy użyciu tożsamości przyłączonych do domeny usługi Active Directory. Ci klienci obejmują systemu Windows 7, Windows 8.1 i Windows 10. Używa certyfikatów PKI do zabezpieczenia kanału komunikacyjnego. Działania związane z zarządzaniem obejmują:  
    - Aktualizacje oprogramowania i ochrony punktu końcowego
    - Stan zapasów i klienta
    - Ustawienia zgodności
    - Dystrybucja oprogramowania na urządzeniu
    - Sekwencja zadań uaktualnienia w miejscu systemu Windows 10 (począwszy od wersji 1802)

- Zarządzanie tradycyjnych klientów systemu Windows 10 z nowoczesnych tożsamości hybrydowej lub chmury czysty przyłączonych do domeny z usługą Azure Active Directory (Azure AD). Klienci używają usługi Azure AD do uwierzytelniania, a nie certyfikatów PKI. Używanie programu Azure AD jest łatwiejsze, konfigurowanie i utrzymania niż bardziej złożonych systemów infrastruktury kluczy publicznych. Działania związane z zarządzaniem są takie same jak pierwszego scenariusza, jak również:  
    - Dystrybucja oprogramowania do użytkownika  

- Zainstaluj klienta programu Configuration Manager na urządzeniach z systemem Windows 10 za pośrednictwem Internetu. Używanie programu Azure AD umożliwia urządzenia do uwierzytelniania CMG dla rejestracji i przypisywania klienta. Klienta można zainstalować ręcznie lub za pomocą innej metody dystrybucji oprogramowania, takich jak Microsoft Intune.  

- Inicjowanie obsługi administracyjnej z zarządzania wspólnej nowe urządzenie. CMG nie jest wymagane do zarządzania wspólnej. Pomaga ukończyć scenariusz end-to-end dla nowych urządzeń obejmujące AutoPilot systemu Windows, usługi Azure AD, Microsoft Intune i programu Configuration Manager.  

### <a name="specific-use-cases"></a>Przypadki użycia określonego
W tych scenariuszach może stosować następujących przypadków użycia określonego urządzenia:

- Roamingu urządzeń przenośnych  

- Zdalne/branch office urządzenia, które są mniej kosztowne i bardziej wydajnych do zarządzania za pośrednictwem Internetu niż w sieci WAN lub za pośrednictwem sieci VPN.  

- Fuzje i przejęcia, których może być łatwiej dołączenie urządzenia do usługi Azure AD i zarządzać nimi za pośrednictwem CMG.  

> [!Important]
> Domyślnie wszyscy klienci otrzymują zasady dla CMG i zacznij z niej korzystać, gdy stanie się internetowego. W zależności od scenariusza i użyj przypadku, gdy ma zastosowanie do organizacji, może być konieczne użycie zakresu CMG. Aby uzyskać więcej informacji, zobacz [umożliwić klientom używanie brama zarządzania chmury](/sccm/core/clients/deploy/about-client-settings#enable-clients-to-use-a-cloud-management-gateway) ustawienia klienta.


## <a name="topology-design"></a>Projekt topologii

### <a name="cmg-components"></a>Składniki CMG
Wdrażania i działania CMG obejmuje następujące składniki:  

- **Usługi w chmurze CMG** na platformie Azure uwierzytelnianie i przekazuje żądania klientów programu Configuration Manager do CMG punktu połączenia.  
 
- **Punktu połączenia CMG** Rola systemu lokacji umożliwia spójne i wysokiej wydajności połączenie z siecią lokalną usługą CMG na platformie Azure. Publikuje również ustawienia do CMG, w tym połączenia informacji i ustawień zabezpieczeń. Punkt połączenia CMG przekazuje żądania klientów z CMG do ról lokalnie zgodnie z mapowania adresów URL.

- [ **Punkt połączenia z usługą** ](/sccm/core/servers/deploy/configure/about-the-service-connection-point) składnika menedżera usługi chmury, która obsługuje wszystkie zadania wdrażania CMG działa rola systemu lokacji. Ponadto monitoruje i raportuje usługi kondycji i rejestrowanie informacji z usługi Azure AD. Upewnij się, że punkt połączenia usługi jest w [trybu online](/sccm/core/servers/deploy/configure/about-the-service-connection-point#bkmk_modes).  

- **Punkt zarządzania** Rola systemu lokacji usług żądań klientów na normalny.  

- **Punkt aktualizacji oprogramowania** Rola systemu lokacji usług żądań klientów na normalny.  

- **Klienci internetowi** nawiązać CMG uzyskiwanie dostępu do lokalnego programu Configuration Manager składników.

- Używa CMG **opartego na certyfikatach HTTPS** usługi do zabezpieczania komunikacji sieciowej z klientami sieci web.  

- Klienci internetowi użyj **infrastruktury kluczy publicznych certyfikatów lub usługi Azure AD** dla uwierzytelnianie i tożsamość.  

- A [ **punktu dystrybucji w chmurze** ](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point) zapewnia zawartości do klientów internetowych zgodnie z potrzebami.  


### <a name="azure-resource-manager"></a>Azure Resource Manager
<!-- 1324735 -->
Począwszy od wersji 1802, można utworzyć przy użyciu CMG **wdrożenia usługi Azure Resource Manager**. [Usługa Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview) nowoczesnych platforma do zarządzania wszystkimi zasobami rozwiązania jako pojedynczy element o nazwie [grupy zasobów](/azure/azure-resource-manager/resource-group-overview#resource-groups). W przypadku wdrażania CMG za pomocą Menedżera zasobów Azure, lokacji używa usługi Azure Active Directory (Azure AD) do uwierzytelniania i Utwórz zasoby niezbędne chmury. To wdrożenie zmodernizowanej nie wymaga certyfikatu zarządzania platformy Azure w klasycznym.  

Kreator CMG nadal udostępnia opcję **wdrożenia usługi klasycznego** używa certyfikatu zarządzania platformy Azure. Aby uprościć wdrażanie i zarządzanie zasobami, przy użyciu modelu wdrażania usługi Azure Resource Manager zaleca się dla wszystkich nowych wystąpień CMG. Jeśli to możliwe należy ponownie wdrożyć istniejących wystąpień CMG za pomocą Menedżera zasobów. Aby uzyskać więcej informacji, zobacz [zmodyfikować CMG](/sccm/core/clients/manage/cmg/setup-cloud-management-gateway#modify-a-cmg).

> [!IMPORTANT]  
> Ta funkcja nie obsługuje dla dostawców usług Azure chmurze (CSP). Wdrożenie CMG z usługi Azure Resource Manager w dalszym ciągu używa usługi w chmurze klasycznego, który nie obsługuje dostawca usług Kryptograficznych. Aby uzyskać więcej informacji, zobacz [dostępnych usług Azure w dostawcy usług Kryptograficznych Azure](/azure/cloud-solution-provider/overview/azure-csp-available-services). 


### <a name="hierarchy-design"></a>Projekt hierarchii

Utwórz CMG w lokacji najwyższego poziomu w hierarchii. Oznacza to centralna lokacja administracyjna, utworzenie punktów połączenia CMG w podrzędnych lokacjach głównych. Składnik menedżera usługi chmury znajduje się na punkt połączenia usługi, która jest również w witrynie Administracja centralna. W tym projekcie mogą udostępniać usługi między różnych lokacji głównych, w razie potrzeby.

Można utworzyć wiele usług CMG na platformie Azure, a następnie można utworzyć wiele punktów połączenia CMG. Wiele punktów połączenia CMG Podaj ruchu klienta z CMG do ról lokalnymi równoważenia obciążenia. W celu zmniejszenia opóźnienia sieci, należy przypisać skojarzone CMG do tego samego regionu geograficznego co lokacji głównej.

 > [!Note]  
 > Klienci internetowi i CMG nie należą do żadnej grupy granic.

Inne czynniki, takie jak liczba klientów do zarządzania, również wpływ CMG projektu. Aby uzyskać więcej informacji, zobacz [wydajności i skalowania](#performance-and-scale).

#### <a name="example-1-standalone-primary-site"></a>Przykład 1: autonomiczną lokacją główną

Firma Contoso ma autonomiczną lokacją główną w centrum danych lokalnych w swojej centrali w Nowym Jorku. 
- Tworzą CMG w regionie wschodnie nam Azure do zmniejszenia opóźnienia sieci. 
- Tworzenia dwoma punktami połączenia CMG, połączone z jednym usługi CMG.  

Ponieważ klienci są przekazywane do Internetu komunikują się z CMG w regionie wschodnie nam Azure. CMG przekazuje tej komunikacji w ramach zarówno CMG punkty połączenia.

#### <a name="example-2-hierarchy-with-site-specific-cmg"></a>Przykład 2: hierarchii z CMG specyficzne dla lokacji

Fourth Coffee ma centralnej lokacji administracyjnej w centrum danych lokalnych w swojej centrali w Seattle. Jedna lokacja główna znajduje się w tym samym centrum danych i innych lokacji głównej znajduje się w ich siedziba Europejskiego w Paryża. 
- W witrynie Administracja centralna tworzą dwie usługi CMG:
     - Jeden CMG regionu zachodnie nam Azure.
     - Jeden CMG w regionie Azure Europa Zachodnia.
- Na podstawie Seattle lokacji głównej tworzenia punktu połączenia CMG powiązany zachodnie nam CMG.
- Na podstawie Paryża lokacji głównej punkt połączenia CMG powiązany CMG Europa Zachodnia ich utworzyć.

Jak klienci z systemem Seattle są przekazywane do Internetu komunikują się z CMG regionu zachodnie nam Azure. CMG przekazuje komunikacji z punktem połączenia na podstawie Seattle CMG.

Podobnie jak klienci z systemem Paryża są przekazywane do Internetu, komunikują się z CMG w regionie Azure Europa Zachodnia. CMG przekazuje komunikacji z punktem połączenia na podstawie Paryża CMG. Gdy użytkownicy Paryża są przesyłane do siedziby firmy w Seattle, komputerach przejdź do komunikowania się z CMG w regionie Azure Europa Zachodnia. 

 > [!Note]  
 > Fourth Coffee uznawane za utworzenie innego punktu połączenia CMG na podstawie Paryża lokacji głównej powiązany zachodnie nam CMG. Klienci z systemem Paryża następnie użyje zarówno CMGs, niezależnie od ich lokalizacji. Gdy taka konfiguracja pozwala równoważenia obciążenia ruchu i zapewnić nadmiarowość usługi, może być przyczyną opóźnienia podczas komunikacji klientów z systemem Paryża z amerykańskiej CMG. Klienci programu Configuration Manager nie są obecnie znane ich regionu geograficznego, więc nie preferowane CMG, który znajduje się fizycznie bliżej. Klienci używają losowo CMG dostępne.



## <a name="requirements"></a>Wymagania

- **Subskrypcji platformy Azure** do hostowania CMG.  

    - **Administrator usługi Azure** musi brać udziału w pierwszym utworzeniu niektórych składników, w zależności od projektu. Ta osoba nie wymaga uprawnień w programie Configuration Manager.  

- Co najmniej jednego lokalnego systemu Windows server do hosta **punktu połączenia CMG**. Można kolokuj tę rolę z innych ról systemu lokacji programu Configuration Manager.  

- **Punkt połączenia z usługą** musi znajdować się w [trybu online](/sccm/core/servers/deploy/configure/about-the-service-connection-point#bkmk_modes).   

- A [ **certyfikatu uwierzytelniania serwera** ](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway#cmg-server-authentication-certificate) dla CMG.  

- Jeśli przy użyciu metody wdrożenia usługi Azure klasycznego, należy użyć [ **certyfikat zarządzania platformy Azure**](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway#azure-management-certificate).  

    > [!TIP]  
    > Począwszy od programu Configuration Manager w wersji 1802, za pomocą **usługi Azure Resource Manager** model wdrażania jest zalecane. Nie wymaga tego certyfikatu zarządzania.  

- **Inne certyfikaty** mogą być wymagane, w zależności od modelu wersji i uwierzytelnianie klienta systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [certyfikaty CMG](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway).  

    - Począwszy od wersji 1802, należy skonfigurować wszystkie [ **punktów zarządzania do używania protokołu HTTPS**](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway#enable-management-point-for-https).  

- Integracja z **usługi Azure AD** mogą być wymagane dla klientów systemu Windows 10. Aby uzyskać więcej informacji, zobacz [usług Azure skonfigurować](/sccm/core/servers/deploy/configure/azure-services-wizard).  

- Klienci muszą używać **IPv4**.  



## <a name="specifications"></a>Specyfikacje

- Wszystkie wersje systemu Windows wymienionych w [obsługiwane systemy operacyjne dla klientów i urządzeń](/sccm/core/plan-design/configs/supported-operating-systems-for-clients-and-devices) są obsługiwane w przypadku CMG.  

- CMG obsługuje tylko punkt i oprogramowania aktualizacji roli zarządzania punktu.  

- CMG nie obsługuje klientów komunikujących się tylko przy użyciu adresów IPv6.<!--495606-->  

- Punkty aktualizacji oprogramowania przy użyciu usługi równoważenia obciążenia sieciowego nie współpracujesz z CMG. <!--505311-->  

- Począwszy od wersji 1802 CMG wdrożenia przy użyciu modelu zasobów Azure nie należy włączać obsługi dla dostawców usług Azure chmurze (CSP). Wdrożenie CMG z usługi Azure Resource Manager w dalszym ciągu używa usługi w chmurze klasycznego, który nie obsługuje dostawca usług Kryptograficznych. Aby uzyskać więcej informacji, zobacz [dostępnych usług Azure w dostawcy usług w Chmurze Azure](/azure/cloud-solution-provider/overview/azure-csp-available-services)  


### <a name="support-for-configuration-manager-features"></a>Obsługa funkcji programu Configuration Manager
W poniższej tabeli wymieniono CMG obsługę funkcji programu Configuration Manager:


|Funkcja  |Obsługa  |
|---------|---------|
| Aktualizacje oprogramowania     | ![Obsługiwane](media/green_check.png) |
| Program Endpoint protection     | ![Obsługiwane](media/green_check.png) |
| Spis sprzętu i oprogramowania     | ![Obsługiwane](media/green_check.png) |
| Stan klienta i powiadomienia     | ![Obsługiwane](media/green_check.png) |
| Ustawienia zgodności     | ![Obsługiwane](media/green_check.png) |
| Instalacja klienta</br>(dzięki integracji usługi Azure AD)     | ![Obsługiwane](media/green_check.png)  (1706) |
| Dystrybucja oprogramowania (docelowe urządzenia)     | ![Obsługiwane](media/green_check.png) |
| Dystrybucja oprogramowania (ukierunkowane na użytkownika, wymagane)</br>(dzięki integracji usługi Azure AD)     | ![Obsługiwane](media/green_check.png)  (1710) |
| Dystrybucja oprogramowania (ukierunkowane na użytkownika, dostępne)</br>([wszystkie wymagania](/sccm/apps/deploy-use/deploy-applications#deploy-user-available-applications-on-azure-ad-joined-devices)) | ![Obsługiwane](media/green_check.png)  (1802) |
| Sekwencja zadań uaktualnienia w miejscu systemu Windows 10     | ![Obsługiwane](media/green_check.png)  (1802) |
| Każdej innej sytuacji sekwencji zadań     | ![Nieobsługiwane](media/Red_X.png) |
| Instalacji wypychanej klienta     | ![Nieobsługiwane](media/Red_X.png) |
| Automatycznego przypisywania lokacji     | ![Nieobsługiwane](media/Red_X.png) |
| Katalog aplikacji     | ![Nieobsługiwane](media/Red_X.png) |
| Żądania zatwierdzenia oprogramowania     | ![Nieobsługiwane](media/Red_X.png) |
| Konsola programu Configuration Manager     | ![Nieobsługiwane](media/Red_X.png) |
| Zdalne narzędzia     | ![Nieobsługiwane](media/Red_X.png) |
| Witryny sieci Web raportowania     | ![Nieobsługiwane](media/Red_X.png) |
| Wake on LAN     | ![Nieobsługiwane](media/Red_X.png) |
| Mac, Linux i UNIX     | ![Nieobsługiwane](media/Red_X.png) |
| Równorzędna pamięć podręczna     | ![Nieobsługiwane](media/Red_X.png) |
| Lokalne zarządzanie urządzeniami Przenośnymi     | ![Nieobsługiwane](media/Red_X.png) |


|Klucz|
|--|
|![Obsługiwane](media/green_check.png) = Ta funkcja jest obsługiwana z CMG przez wszystkie obsługiwane wersje programu Configuration Manager  |
|![Obsługiwane](media/green_check.png) (*RRMM*) = ta funkcja jest obsługiwana z CMG począwszy od wersji *RRMM* programu Configuration Manager  |
|![Nieobsługiwane](media/Red_X.png) = Ta funkcja nie jest obsługiwana z CMG |



## <a name="cost"></a>Koszt

>[!IMPORTANT]  
>Następujące informacje o koszcie jest tylko do celów szacowania. Środowiska mogą mieć inne zmienne, które mają wpływ na całkowity koszt przy użyciu CMG.

CMG wykorzystuje następujące składniki platformy Azure, które naliczenie opłat do konta subskrypcji platformy Azure:

#### <a name="virtual-machine"></a>Maszyna wirtualna

- CMG używa usług Azure Cloud Services jako platforma jako usługa (PaaS). Ta usługa korzysta z maszyn wirtualnych (VM), które pociągnąć za sobą koszty obliczeń.  

- W 1706 wersji programu Configuration Manager CMG używa standardowych maszyna wirtualna A2.  

- Począwszy od programu Configuration Manager w wersji 1710 CMG używa standardowych wirtualna V2 A2.  

- Wybierz liczbę wystąpień maszyny Wirtualnej obsługuje CMG. Co jest ustawieniem domyślnym i 16 to maksymalna. Ta liczba jest ustawiana podczas tworzenia CMG i można zmienić później można skalować usługi zgodnie z potrzebami.

- Aby uzyskać więcej informacji na liczbę maszyn wirtualnych wymagana jest obsługa klientów, zobacz [wydajności i skalowania](#performance-and-scale).

- Zobacz [Azure Kalkulator cen](https://azure.microsoft.com/pricing/calculator/) w celu określenia potencjalne koszty.

    > [!NOTE]  
    > Koszty maszyny wirtualnej zależy od regionu.

#### <a name="outbound-data-transfer"></a>Transfer danych wychodzących

- Opłaty są oparte na dane przepływające z platformy Azure (wyjściowych lub Pobierz). Wszystkie przepływy danych na platformie Azure są wolne (ruch przychodzący lub przekazywania). CMG przepływów danych z platformy Azure obejmują zasady klienta, powiadomienia klienta i odpowiedzi klienta przekazanych przez CMG do lokacji. Odpowiedzi na te obejmują raporty ze spisu, komunikaty o stanie i stanu zgodności.  

- Nawet bez żadnych klientów podczas komunikacji z CMG komunikacja tła powoduje, że ruch sieciowy między CMG i lokacji lokalnej.  

- Widok **transfer danych wychodzących (GB)** w konsoli programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [monitorowania klientów na CMG](/sccm/core/clients/manage/cmg/monitor-clients-cloud-management-gateway).  

- Zobacz [Azure przepustowości szczegóły cennika](https://azure.microsoft.com/pricing/details/bandwidth/) w celu określenia potencjalne koszty. Cennik danych jest warstwowa transferu. Im bardziej używanego, tym mniej płacisz za gigabajt.  

- *Podczas szacowania tylko do celów*, oczekiwano około 100 – 300 MB na klienta miesięcznie dla klientów internetowych. Niższe szacuje się, że w domyślnej konfiguracji klienta. Górny szacuje się, że dla bardziej agresywną konfiguracji klienta. Rzeczywiste użycie może się różnić w zależności od sposobu konfigurowania ustawień klienta.  

   > [!NOTE]  
   > Wykonywanie innych działań, takich jak wdrażanie aktualizacji oprogramowania lub aplikacji, zwiększa liczbę transfer danych wychodzących z platformy Azure.

#### <a name="content-storage"></a>Magazyn zawartości

- Klienci internetowi pobrać zawartość aktualizacji oprogramowania firmy Microsoft z witryny Windows Update bez dodatkowych opłat. Pakiety aktualizacji z firmy Microsoft aktualizacji zawartości do punktu dystrybucji chmury nie przeprowadzaj dystrybucji, w przeciwnym razie mogą ponieść koszty wyjście magazynu i danych.  

- Inne niezbędne zawartości, takich jak aplikacje lub aktualizacje oprogramowania innych firm musisz przeprowadzić dystrybucję do punktu dystrybucji w chmurze. Obecnie CMG obsługuje tylko punkt dystrybucji w chmurze wysyłanie zawartości do klientów.  

- Aby uzyskać więcej informacji, zobacz kosztów [chmurowych punktów dystrybucji](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point#cost-of-using-cloud-based-distribution).  

#### <a name="other-costs"></a>Inne koszty

- Każda usługa chmury ma dynamicznego adresu IP. Każdy różne CMG używa nowego dynamicznego adresu IP. Dodawanie dodatkowych maszyn wirtualnych na CMG nie rosną z tych adresów.  



## <a name="performance-and-scale"></a>Wydajność i skalę

Aby uzyskać więcej informacji na skali CMG, zobacz [rozmiaru i skali liczby](/sccm/core/plan-design/configs/size-and-scale-numbers#bkmk_cmg).

Poniższe zalecenia w celu poprawy wydajności CMG:

- Jeśli to możliwe, skonfiguruj CMG, CMG punktu połączenia, a serwerem lokacji programu Configuration Manager w tym samym regionie sieci, aby zmniejszyć opóźnienia.  

- Połączenie między klientem programu Configuration Manager i CMG nie jest obecnie obsługujący regionu.  

- Wysoką dostępność usługi należy utworzyć co najmniej dwie usługi CMG i dwoma punktami połączenia CMG dla każdej witryny.  

- Skala CMG w celu obsługi większej liczby klientów, dodając więcej wystąpień maszyny Wirtualnej. Moduł równoważenia obciążenia Azure określa połączenia klienta z usługą.  

- Utwórz więcej punktów połączenia CMG rozłożenie obciążenia między nimi. CMG dystrybuuje ruch do łączenia punktów połączenia CMG w działaniu okrężnym.  

- Gdy CMG jest mocno obciążony ze względu na więcej niż liczba obsługiwanych klientów, nadal obsługuje żądania, ale mogą występować opóźnienia.  


> [!Note]  
> Menedżer konfiguracji nie ma twardych limitu liczby klientów punktu połączenia CMG, Windows Server nie ma domyślny maksymalny dynamicznego zakresu portów TCP od 16384. Jeśli w lokacji programu Configuration Manager zarządza więcej niż 16 384 klientów z jednym punktem połączenia CMG, należy zwiększyć limit systemu Windows Server. Wszyscy klienci zachowują kanał powiadomień klienta, którego utrzymujących otwarte w punkcie połączenia CMG portu. Aby uzyskać więcej informacji na temat sposobu użyj polecenia netsh, aby zwiększyć ten limit, zobacz [Microsoft Support artykułu 929851](https://support.microsoft.com/help/929851).



## <a name="ports-and-data-flow"></a>Porty i przepływ danych

Nie trzeba otworzyć żadnych portów przychodzących do sieci lokalnej. Punkt połączenia usługi i punkt połączenia CMG zainicjować cała komunikacja z platformy Azure i CMG. Te dwie role systemu lokacji musi mieć możliwość tworzenia połączeń wychodzących do firmy Microsoft w chmurze. Punkt połączenia usługi wdraża i monitoruje usługi na platformie Azure, musi być tym samym trybie online. Punkt połączenia CMG łączy CMG do zarządzania komunikacją między CMG i lokalnymi role systemu lokacji.

Poniższy diagram jest przepływ danych podstawowych, koncepcyjnego dla CMG: ![Przepływ danych CMG](media/cmg-data-flow.png)
   1. Punkt połączenia usługi łączy na platformie Azure za pośrednictwem portu HTTPS 443. Używanie programu Azure AD uwierzytelnia lub certyfikat zarządzania platformy Azure. Punkt połączenia usługi wdraża CMG na platformie Azure. CMG tworzy usługę w chmurze HTTPS za pomocą certyfikatu uwierzytelniania serwera.  

   2. Punkt połączenia CMG łączy CMG na platformie Azure za pośrednictwem protokołu TLS TCP lub HTTPS. Utrzymujących otwarte połączenia, a kompilacje kanału dla przyszłych dwukierunkowej komunikacji.   

   3. Klient łączy się CMG za pośrednictwem portu HTTPS 443. Używanie programu Azure AD uwierzytelnia lub certyfikat uwierzytelniania klienta.  

   4. CMG przekazuje komunikacji z klientem za pośrednictwem istniejące połączenie z punktem połączenia CMG lokalnymi. Nie trzeba otwierać żadnych portów zapory dla ruchu przychodzącego.  

   5. Punkt połączenia CMG przekazuje komunikacji klienta do lokalnego punktu zarządzania i punkt aktualizacji oprogramowania.  

### <a name="required-ports"></a>Wymagane porty
Poniższa tabela zawiera wymagane porty i protokoły. *Klienta* urządzenie inicjowania połączenia, wymagających portu wychodzącego. *Serwera* urządzenie akceptować połączenia wymagające portu wejściowego. 

| Klient  | Protokół | Port  | Serwer  | Opis  |
|---------|---------|---------|---------|---------|
| Punkt połączenia usługi     | HTTPS | 443        | Azure        | CMG wdrożenia |
| Punkt połączenia CMG     |  TCP-TLS | 10140-10155        | Usługa CMG        | Preferowanym protokołem do tworzenia kanału CMG <sup>1</sup> |
| Punkt połączenia CMG     | HTTPS | 443        | Usługa CMG       | Powrót do tworzenia kanału CMG tylko jedno wystąpienie maszyny Wirtualnej<sup>2</sup> |
| Punkt połączenia CMG     |  HTTPS   | 10124-10139     | Usługa CMG       | Powrót do tworzenia kanału CMG do dwóch lub więcej wystąpień maszyny Wirtualnej<sup>3</sup> |
| Klient     |  HTTPS | 443         | CMG        | Komunikacja z klientem ogólne |
| Punkt połączenia CMG      | HTTP lub HTTPS | 443 lub 80         | Punkt zarządzania</br>(wersja 1706 lub 1710) | Ruch lokalnymi portu zależy od konfiguracji punktu zarządzania |
| Punkt połączenia CMG      | HTTPS | 443      | Punkt zarządzania</br>(wersja 1802) | Ruch lokalnej musi być typu HTTPS |
| Punkt połączenia CMG      | HTTP lub HTTPS | 443 lub 80         | Punkt aktualizacji oprogramowania | Ruch lokalnymi portu zależy od konfiguracji punktu aktualizacji oprogramowania |

<sup>1</sup> punktu połączenia CMG po raz pierwszy próbuje nawiązać połączenia TCP TLS długotrwałe z każdym wystąpieniem CMG maszyny Wirtualnej. Łączy się w pierwszym wystąpieniu maszyny Wirtualnej na porcie 10140. Drugie wystąpienie maszyny Wirtualnej korzysta z portu 10141, maksymalnie szesnastej na porcie 10155. Połączenia TCP TLS działa najlepiej, ale nie obsługuje internetowy serwer proxy. Jeśli punkt połączenia CMG nie może połączyć się za pośrednictwem protokołu TLS TCP, a następnie nastąpi powrót do HTTPS<sup>2</sup>.  

<sup>2</sup> Jeśli punkt połączenia CMG nie może połączyć się CMG za pośrednictwem protokołu TLS TCP<sup>1</sup>, ustanawiania połączenia z usługą równoważenia obciążenia sieci platformy Azure za pośrednictwem protokołu HTTPS 443 tylko dla jednego wystąpienia maszyny Wirtualnej.  

<sup>3</sup> w przypadku dwóch lub więcej wystąpień maszyny Wirtualnej, punkt połączenia CMG używa protokołu HTTPS 10124 do pierwszego wystąpienia maszyny Wirtualnej nie protokołu HTTPS 443. Łączy się drugie wystąpienie maszyny Wirtualnej na HTTPS 10125, maksymalnie szesnastej na HTTPS port 10139.


### <a name="internet-access-requirements"></a>Wymagania dotyczące dostępu do Internetu

Systemu lokacji punktu połączenia CMG obsługuje przy użyciu serwera proxy sieci web. Aby uzyskać więcej informacji na temat konfigurowania tej roli dla serwera proxy, zobacz [Obsługa serwerów Proxy](/sccm/core/plan-design/network/proxy-server-support#to-set-up-the-proxy-server-for-a-site-system-server). Punkt połączenia CMG wymaga połączenia z następujących punktów końcowych:  

- Określone punkty końcowe systemu Azure są różne w zależności od konfiguracji środowiska. Program Configuration Manager przechowuje te punkty końcowe w bazie danych lokacji. Zapytanie **AzureEnvironments** tabeli w programie SQL Server dla listy punkty końcowe systemu Azure.  

- ServiceManagementEndpoint (https://management.core.windows.net/)  

- StorageEndpoint (core.windows.net)  

- Token pobieranie z konsoli programu Configuration Manager i klienta dla usługi Azure AD: ActiveDirectoryEndpoint (https://login.microsoftonline.com/)  

- Do odnajdywania użytkownika usługi Azure AD: (Punkt końcowy usługi AAD wykresuhttps://graph.windows.net/)  



## <a name="next-steps"></a>Następne kroki

- [Certyfikaty bramy zarządzania w chmurze](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway)
- [Bezpieczeństwo i prywatność brama zarządzania w chmurze](/sccm/core/clients/manage/cmg/security-and-privacy-for-cloud-management-gateway)
- [Rozmiar bramy zarządzania w chmurze i skalowanie liczb](/sccm/core/plan-design/configs/size-and-scale-numbers#bkmk_cmg)
- [Często zadawane pytania dotyczące zarządzania bramy chmury](/sccm/core/clients/manage/cmg/cloud-management-gateway-faq)
- [Konfigurowanie bramy zarządzania chmurą](/sccm/core/clients/manage/cmg/setup-cloud-management-gateway)
