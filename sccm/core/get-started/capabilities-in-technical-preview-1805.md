---
title: Technical Preview 1805
titleSuffix: Configuration Manager
description: Więcej informacji na temat nowych funkcji dostępnych w wersji Configuration Manager Technical Preview 1805.
ms.date: 05/21/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 7996b3eb-5259-483b-af40-adae2943d123
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 24cb16ab17475bdd063949c7e3e2961b53341026
ms.sourcegitcommit: b113f184efafa166813c18fa1fa000b75a67e4eb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/22/2018
---
# <a name="capabilities-in-technical-preview-1805-for-system-center-configuration-manager"></a>Funkcje w wersji Technical Preview 1805 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*

W tym artykule przedstawiono funkcje, które są dostępne w wersji Technical Preview programu Configuration Manager, wersja 1805. Można zainstalować tę wersję, aby zaktualizować i dodać nowe funkcje do swojej witryny wersji zapoznawczej technical preview. 

Przegląd [Technical Preview](/sccm/core/get-started/technical-preview) artykuł przed zainstalowaniem tej aktualizacji. Ten artykuł zaznajomić z ogólne wymagania i ograniczenia dotyczące używania wersji technical preview, jak zaktualizować między wersjami i sposobu wyrazić swoją opinię.     


<!--  Known Issues Template
## Known Issues in this Technical Preview

### <a name="bkmk_ANCHOR"></a> Known issue title
<!--bugID--
Issue description and cause.

#### Workaround
Steps to workaround, if any.  
-->



</br>

**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  



## <a name="create-a-phased-deployment-with-manually-configured-phases-for-a-task-sequence"></a>Utwórz wdrożenie etapowe z fazy ręcznie skonfigurowanej dla sekwencji zadań
<!--1358148--> 
Możesz teraz [Utwórz wdrożenie etapowe](/sccm/osd/deploy-use/create-phased-deployment-for-task-sequence) faz ręcznie skonfigurowanej dla sekwencji zadań. Możesz dodać maksymalnie 10 dodatkowe fazy z **fazy** kartę Kreatora tworzenia wdrożenia stopniowo. 


### <a name="try-it-out"></a>Wypróbuj
Postępuj zgodnie z instrukcjami, aby utworzyć wdrożenie etapowe ręcznie konfigurować wszystkich faz. Wyślij [opinii](capabilities-in-technical-preview-1804.md#bkmk_feedback) zawiadomienie nas o tym, jak Ci poszło. 

1. W **Biblioteka oprogramowania** obszaru roboczego, rozwiń węzeł **systemów operacyjnych**i wybierz **sekwencje zadań**.  

2. Kliknij prawym przyciskiem myszy na istniejącej sekwencji zadań i wybierz **tworzenia wdrożenia stopniowo**.  

3. Na **ogólne** karcie, określ etapowego wdrażania nazwę, opis (opcjonalnie) i wybierz **ręcznie skonfigurować wszystkich faz**.  

4. Na **fazy** kliknij **Dodaj**.  

5. Określ **nazwa** dla fazy, a następnie przejdź do elementu docelowego **kolekcji fazy**.  

6. Na **ustawienia fazy** , wybierz jedną z opcji dla każdego ustawienia planowania i wybierz **dalej** po zakończeniu.  

    - Kryteria sukcesu fazy poprzedniego (Ta opcja jest wyłączona dla pierwszego etapu).
        - **Procent powodzenia wdrożenia**: Określ procent urządzeń, które zakończyło się powodzeniem wdrożenia kryteria sukcesu fazy poprzedniej.  

    - Warunki od tej fazy wdrożenia po pomyślnym poprzedniej fazy  
        - **Automatycznie rozpocząć tej fazy po upływie opóźnienia (w dniach)**: Wybierz liczbę dni oczekiwania przed rozpoczęciem fazy dalej po pomyślnym poprzedniej fazy. 
        - **Ręcznie rozpocząć tej fazy wdrożenia**: Nie należy rozpocząć tej fazy automatycznie po pomyślnym poprzedniej fazy.  

    - Gdy urządzenie jest przeznaczona, należy zainstalować oprogramowanie
        - **Jak najszybciej**: Określa ostateczny termin instalacji na urządzeniu, jak docelowym jest urządzenie.
        - **Czas (względem czasu, urządzenie podlega) ostatecznego terminu**: Ustawia termin ostateczny instalacji określonej liczby dni, po docelowym jest urządzenie.  
     
7. Ukończ pracę Kreatora ustawień fazy.

8. Na **fazy** kartę Kreatora tworzenia wdrożenia stopniowo można teraz dodać, usunąć, zmienić kolejność lub edytować fazy dla tego wdrożenia.  

9. Ukończ pracę Kreatora tworzenia wdrożenia stopniowo.  



## <a name="cloud-distribution-point-support-for-azure-resource-manager"></a>Obsługa punktu dystrybucji chmury dla usługi Azure Resource Manager
<!--1322209-->
Podczas tworzenia wystąpienia [punktu dystrybucji w chmurze](/sccm/core/servers/deploy/configure/install-cloud-based-distribution-points-in-microsoft-azure), Kreator udostępnia teraz opcję, aby utworzyć **wdrożenia usługi Azure Resource Manager**. [Usługa Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview) nowoczesnych platforma do zarządzania wszystkimi zasobami rozwiązania jako pojedynczy element o nazwie [grupy zasobów](/azure/azure-resource-manager/resource-group-overview#resource-groups). W przypadku wdrażania punkt dystrybucji chmury za pomocą Menedżera zasobów Azure, lokacji używa usługi Azure Active Directory (Azure AD) do uwierzytelniania i Utwórz zasoby niezbędne chmury. To wdrożenie zmodernizowanej nie wymaga certyfikatu zarządzania platformy Azure w klasycznym.  

Kreatora punktu dystrybucji w chmurze nadal zawiera opcję **wdrożenia usługi klasycznego** używa certyfikatu zarządzania platformy Azure. Aby uprościć wdrażanie i zarządzanie zasobami, zaleca się przy użyciu modelu wdrażania usługi Azure Resource Manager dla wszystkich nowych punktów dystrybucji w chmurze. Jeśli to możliwe należy ponownie wdrożyć istniejących punktów dystrybucji w chmurze za pomocą Menedżera zasobów.

Configuration Manager nie może zmigrować istniejących punktów dystrybucji w chmurze klasycznego modelu wdrażania usługi Azure Resource Manager. Tworzenie chmury nowych punktów dystrybucji przy użyciu wdrożenia usługi Azure Resource Manager, a następnie usuń punkty dystrybucji w chmurze klasycznego. 

> [!IMPORTANT]  
> Ta funkcja nie obsługuje dla dostawców usług Azure chmurze (CSP). Wdrożenie punktu dystrybucji chmury z usługi Azure Resource Manager w dalszym ciągu używa usługi w chmurze klasycznego, który nie obsługuje dostawca usług Kryptograficznych. Aby uzyskać więcej informacji, zobacz [dostępnych usług Azure w dostawcy usług Kryptograficznych Azure](/azure/cloud-solution-provider/overview/azure-csp-available-services).  


### <a name="prerequisites"></a>Wymagania wstępne  
- Integracja z [usługi Azure AD](/sccm/core/clients/deploy/deploy-clients-cmg-azure). Odnajdowanie użytkowników usługi Azure AD nie jest wymagane.  

- Taki sam [wymagania dla punktu dystrybucji chmury](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point#BKMK_PrereqsCloudDP), z wyjątkiem certyfikat zarządzania platformy Azure.  


### <a name="try-it-out"></a>Wypróbuj  
 Spróbuj wykonać zadania. Wyślij [opinii](capabilities-in-technical-preview-1804.md#bkmk_feedback) zawiadomienie nas o tym, jak Ci poszło.

1. W konsoli programu Configuration Manager **administracji** obszaru roboczego, rozwiń węzeł **usługi w chmurze**i wybierz **punkty dystrybucji w chmurze**. Kliknij przycisk **Utwórz punkty dystrybucji w chmurze** na Wstążce.   

2. Na **ogólne** wybierz pozycję **wdrożenia usługi Azure Resource Manager**. Kliknij przycisk **Zaloguj** do uwierzytelniania przy użyciu konta administratora subskrypcji platformy Azure. Kreator automatycznego wypełniania pozostałe pola z informacji o subskrypcji usługi Azure AD, przechowywane podczas integracji wymagań wstępnych. Jeśli masz wiele subskrypcji wybierz odpowiednią subskrypcję. Kliknij przycisk **Dalej**.  

3. Na **ustawienia** Podaj serwera PKI **plik certyfikatu** w zwykły sposób. Ten certyfikat definiuje punkt dystrybucji w chmurze **nazwa FQDN usługi** używane przez platformę Azure. Wybierz **Region**, a następnie wybierz opcję grupy zasobów, albo **Utwórz nowy** lub **Użyj istniejącego**. Wprowadź nazwę nowej grupy zasobów lub wybierz istniejącą grupę zasobów z listy rozwijanej.  

4. Ukończ pracę kreatora.  

> [!NOTE]  
> Dla wybranej usługi Azure AD aplikacji serwera Azure przypisuje subskrypcji **współautora** uprawnienia.  

Monitorowanie postępu wdrożenia usługi za pomocą **cloudmgr.log** w punkcie połączenia usługi.



## <a name="take-actions-based-on-management-insights"></a>Podjąć działania w oparciu o informacje na temat technologii zarządzania
<!--1357930-->
Niektóre [insights zarządzania](/sccm/core/servers/manage/management-insights) teraz dostępna opcja podjęcia odpowiednich działań. W zależności od reguły, ta akcja spowoduje jedną z następujących zachowań:  

- Automatycznie przejdź w konsoli do węzła, której można wykonać dalszego działania. Na przykład jeśli wiedzę zarządzania zaleca się zmianę ustawienia klienta, podejmowania działań przechodzi do węzła Ustawienia klienta. Można wykonać dalszego działania przez zmodyfikowanie domyślnych lub obiekt ustawień klienta.  

- Przejdź do widoku filtrowanego, na podstawie zapytania. Na przykład podejmowania działań w regule puste kolekcje pokazuje tylko te kolekcje, na liście w kolekcji. W tym miejscu można wykonać dalszego akcji, np. usunięcie kolekcji lub modyfikowanie regułach jego członkostwa.  

Następujące reguły szczegółowe dane zarządzania są akcji w tej wersji:
- Zabezpieczenia
    - Wersje klientów nieobsługiwana ochrony przed złośliwym oprogramowaniem
- Centrum oprogramowania
    - Użycie nowej wersji Centrum oprogramowania
- Aplikacje
    - Aplikacje bez wdrożenia
- Uproszczone zarządzanie
    - Wersje klientów z systemem innym niż CB
- Kolekcje
    - Puste kolekcje 
- Usługi w chmurze
    - Aktualizacja klientów do najnowszej wersji systemu Windows 10



## <a name="transition-device-configuration-workload-to-intune-using-co-management"></a>Obciążenie konfiguracji urządzenia przejścia do usługi Intune przy użyciu wspólnej zarządzania
<!--1357903-->

Obciążenie konfiguracji urządzenia z programu Configuration Manager do usługi Intune mogą teraz przejście po włączeniu wspólnego zarządzania. Przejście to obciążenie umożliwia Użyj usługi Intune do wdrażania zarządzania urządzeniami Przenośnymi zasad, przy użyciu programu Configuration Manager do wdrażania aplikacji. 

Do przejścia to obciążenie, przejdź do strony właściwości wspólnego zarządzania i przesuń suwak z programu Configuration Manager do **pilotażu** lub **wszystkich**. Aby uzyskać więcej informacji, zobacz [urządzenia zarządzania wspólnej dla systemu Windows 10](/sccm/core/clients/manage/co-management-overview).

> [!Note]  
> Przesunięcie to obciążenie również przenosi **dostęp do zasobów** i **programu Endpoint Protection** obciążeń, które są podzbiorem obciążenia konfiguracji urządzenia.

Podczas przejścia to obciążenie, można nadal wdrażać ustawienia z programu Configuration Manager do tej samej zarządzanych urządzeń, nawet jeśli usługa Intune jest urzędem konfiguracji urządzenia. Ten wyjątek może służyć do konfigurowania ustawień, które są wymagane przez organizację, ale nie jest jeszcze dostępna w usłudze Intune. Określ ten wyjątek na linii bazowej konfiguracji programu Configuration Manager. Włącz opcję, aby **Zawsze stosuj tej linii bazowej, nawet w przypadku wspólnie zarządzanych klientów** podczas tworzenia planu bazowego, albo na **ogólne** karta właściwości istniejącej linii bazowej. 



## <a name="enable-distribution-points-to-use-network-congestion-control"></a>Włącz punkty dystrybucji do użycia kontroli przeciążenia sieci
<!--1358112-->

Dodatkowe opóźnienia tła transportu (LEDBAT) dla systemu Windows małej to funkcja systemu Windows Server, aby ułatwić zarządzanie transfery sieci w tle. W przypadku punktów dystrybucji działających w obsługiwanych wersjach systemu Windows Server można włączyć opcję, aby pomóc dostosować ruchu sieciowego. Klienci używają tylko przepustowość sieci, gdy jest ona dostępna. 

Aby uzyskać więcej informacji na LEDBAT systemu Windows, temacie [nowy transport korzyści](https://blogs.technet.microsoft.com/networking/2016/07/18/announcing-new-transport-advancements-in-the-anniversary-update-for-windows-10-and-windows-server-2016/) wpis w blogu.


### <a name="prerequisites"></a>Wymagania wstępne
- Punkt dystrybucji w systemie Windows Server w wersji 1709.  

- Urządzenia klienckiego, z systemem Windows 10 w wersji 1607.


### <a name="try-it-out"></a>Wypróbuj
 Spróbuj wykonać zadania. Wyślij [opinii](#bkmk_feedback) zawiadomienie nas o tym, jak Ci poszło.

1. W konsoli programu Configuration Manager, przejdź do **administracji** obszaru roboczego. Wybierz **punktów dystrybucji** węzła. Wybierz docelowy punkt dystrybucji, a następnie kliknij przycisk **właściwości** na Wstążce.  

2. Na **ogólne** karcie, należy włączyć opcję **dopasowywać prędkość pobierania do użycia przepustowości sieci nieużywane (LEDBAT systemu Windows)**.  



## <a name="cloud-management-dashboard"></a>Pulpit nawigacyjny zarządzania w chmurze
<!--1358461-->
Nowy **pulpit nawigacyjny zarządzania chmury** zapewnia scentralizowane widoku użycie bramy (CMG) zarządzania w chmurze. Jeśli witryna jest został załadowany z usługą Azure AD, wyświetla również dane dotyczące chmury użytkowników i urządzeń.  

Poniższy zrzut ekranu jest częścią pulpit nawigacyjny zarządzania chmury przedstawiający dwa dostępne Kafelki:  
![Pulpit nawigacyjny zarządzania chmury Kafelki CMG ruchu, a bieżąca liczba klientów online](media/1358461-cmg-dashboard.png)

Ta funkcja umożliwia także **CMG połączenia analizator** do weryfikacji w czasie rzeczywistym ułatwić rozwiązywanie problemów. W konsoli narzędzia sprawdza bieżący stan usługi, a kanał komunikacji za pośrednictwem połączenia CMG punktu do żadnych punktów zarządzania, które zezwalają na ruch CMG.


### <a name="prerequisites"></a>Wymagania wstępne
- Aktywny [brama zarządzania chmury](/sccm/core/clients/manage/cmg/plan-cloud-management-gateway) używany przez klientów internetowych.  

- Dołączać lokacji do [usług Azure](/sccm/core/servers/deploy/configure/azure-services-wizard) do zarządzania chmurą.  


### <a name="try-it-out"></a>Wypróbuj
Spróbuj wykonać zadania. Wyślij [opinii](capabilities-in-technical-preview-1804.md#bkmk_feedback) zawiadomienie nas o tym, jak Ci poszło.

#### <a name="cloud-management-dashboard"></a>Pulpit nawigacyjny zarządzania w chmurze

W konsoli programu Configuration Manager, przejdź do **monitorowanie** obszaru roboczego. Wybierz **zarządzania chmurą** Kafelki węzeł i widoku pulpitu nawigacyjnego.  

#### <a name="cmg-connection-analyzer"></a>Analizator połączenia CMG

1. W konsoli programu Configuration Manager, przejdź do **administracji** obszaru roboczego. Rozwiń węzeł **usługi w chmurze** i wybierz **brama zarządzania chmury**.  

2. Wybierz docelowy obiekt CMG, a następnie wybierz **analizator połączenia** na Wstążce.  

3. W oknie CMG połączenia analizatora wybierz jedną z następujących opcji do uwierzytelniania w usłudze:  

     1. **Użytkownik usługi Azure AD**: Użyj tej opcji, aby symulować komunikacji taka sama jak tożsamość użytkowników w chmurze zalogowany do usługi Azure AD — Windows 10 dołączone do urządzenia. Kliknij przycisk **logowania** do bezpiecznego wprowadź poświadczenia dla tego konta użytkownika usługi Azure AD.  

     2. **Certyfikat klienta**: Użyj tej opcji, aby symulować komunikacji taka sama jak klient programu Configuration Manager z [certyfikat uwierzytelniania klienta](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway#client-authentication-certificate).  

4. Kliknij przycisk **Start** można rozpocząć analizy. Wyniki są wyświetlane w oknie analizatora. Wybierz pozycję, aby wyświetlić więcej szczegółów, w polu Opis.  



## <a name="cmpivot"></a>CMPivot
<!--1358456-->
Menedżer konfiguracji zawsze udostępnił dużych centralny magazyn danych urządzenia, których klienci użyć na potrzeby raportowania. Jednak dane są tylko tak dobrze czasu ostatniej zostały zebrane od klientów. 

CMPivot to nowe narzędzie w konsoli, która zapewnia dostęp do stanu w czasie rzeczywistym urządzeń w środowisku. Natychmiast uruchamia zapytanie na wszystkich aktualnie podłączonych urządzeń w kolekcji docelowej i zwraca wyniki. Możesz filtrować i pogrupować te dane w narzędziu. Zapewniając dane w czasie rzeczywistym z klientów online, można szybciej odpowiedzi na pytania biznesowe, rozwiązywania problemów i reagowania na zagrożenia bezpieczeństwa.

Na przykład w [zmniejszenia luk kanału po stronie rozważana wykonywania](https://blogs.technet.microsoft.com/configurationmgr/2018/01/08/additional-guidance-to-mitigate-speculative-execution-side-channel-vulnerabilities/), jest jednym z wymagań można zaktualizować system BIOS. Użyj CMPivot, aby szybko przeszukiwać na informacje systemu BIOS i znaleźć klientów, którzy nie są zgodne. 

W tym zrzucie ekranu pokazano CMPivot wyświetla dwie różne wersje systemu BIOS wraz z liczbą urządzeń jednej. Skorzystaj z tej kwerendy przykład, gdy wypróbowanie CMPivot:  
`Registry('hklm:\\Hardware\\Description\\System\\BIOS') | where (Property == 'BIOSVersion') | summarize dcount( Device ) by Value`  

![Okno CMPivot przykładu z zapytania BIOSVersion](media/1358456-cmpivot-biosversion.png)

Możesz kliknąć liczba urządzenia, aby przejść do określonego urządzenia. Przy wyświetlaniu urządzeń w CMPivot, można kliknąć prawym przyciskiem myszy urządzenie i wykonaj następujące czynności [działań powiadomień klienta](/sccm/core/clients/manage/manage-clients#BKMK_ManagingClients_DevicesNode):
- Uruchom skrypt
- Zdalne sterowanie
- Eksplorator zasobów

Gdy prawym przyciskiem myszy na określonym urządzeniu, można także przestawiać widoku określonego urządzenia na jedną z następujących atrybutów:
- Automatyczne uruchamianie poleceń
- Zainstalowanych produktów
- Procesy
- Usługi
- Użytkownicy
- Aktywnych połączeń
- Brak aktualizacji

### <a name="prerequisites"></a>Wymagania wstępne
- Musisz zaktualizować klientów docelowych do najnowszej wersji.  

- Administrator programu Configuration Manager wymaga uprawnień do uruchamiania skryptów. Aby uzyskać więcej informacji, zobacz [role zabezpieczeń dla skryptów](/sccm/apps/deploy-use/create-deploy-scripts#bkmk_ScriptRoles).  

### <a name="try-it-out"></a>Wypróbuj
Spróbuj wykonać zadania. Wyślij [opinii](capabilities-in-technical-preview-1804.md#bkmk_feedback) zawiadomienie nas o tym, jak Ci poszło.

1. W konsoli programu Configuration Manager, przejdź do **zasoby i zgodność** obszaru roboczego, a następnie wybierz **kolekcje urządzeń**. Wybierz kolekcję docelową, a następnie kliknij przycisk **Start CMPivot** na Wstążce, aby uruchomić narzędzie.  

2. Interfejs zawiera dodatkowe informacje o za pomocą narzędzia. 
     - Można ręcznie wprowadź ciągi zapytań u góry lub po kliknięciu łączy w dokumentacji w wierszu.
     - Kliknij jeden z **jednostek** Aby dodać go do ciągu zapytania. 
     - Łącza do **operatory tabeli**, **funkcje agregacji**, i **funkcji skalarnych** Otwórz dokumentacji języka w przeglądarce sieci web. CMPivot używa tego samego języka zapytania jako [Azure Log Analytics](https://docs.loganalytics.io/docs/Language-Reference/Change-log).



## <a name="improved-secure-client-communications"></a>Ulepszono klienta bezpiecznej komunikacji
<!--1356889,1358228,1358460-->
Za pomocą komunikacji HTTPS jest zalecana dla wszystkich ścieżek komunikacji programu Configuration Manager, ale może być wyzwaniem dla niektórych klientów, ze względu na obciążenie związane z zarządzaniem certyfikatów PKI. Wprowadzenie usługi Azure Active Directory (Azure AD), integracja zmniejsza niektóre, ale nie wszystkie wymagania dotyczące certyfikatów. 

Ta wersja zawiera ulepszenia do komunikowania się klientów z systemami lokacji. Istnieją dwa podstawowe cele te ulepszenia:  

- Możesz zabezpieczyć komunikację z klientem bez konieczności certyfikatów uwierzytelniania serwera PKI.  

- Klienci mogą bezpiecznie uzyskiwać dostęp zawartości z punktów dystrybucji, bez konieczności konta dostępu do sieci.  

> [!Note]  
> Certyfikaty PKI są nadal prawidłową opcją dla użytkowników, którzy mają z niego korzystać.  


### <a name="bkmk_token"></a> Scenariusze
Następujące scenariusze korzystania z tych ulepszeń:  

#### <a name="bkmk_token1"></a> Scenariusz 1. Klient z punktem zarządzania
<!--1356889-->
[Urządzeniach przyłączonych do usługi Azure AD](/azure/active-directory/device-management-introduction#azure-ad-joined-devices) może komunikować się za pośrednictwem bramy zarządzania chmury (CMG) z punktem zarządzania skonfigurowany do obsługi protokołu HTTP. Serwer lokacji generuje certyfikat punktu zarządzania, dzięki któremu do komunikacji za pośrednictwem bezpiecznego kanału.   

> [!Note]  
> To zachowanie jest zmieniany z programu Configuration Manager bieżącą wersję gałęzi 1802, co wymaga punktu zarządzania z włączonym protokołem HTTPS dla tego scenariusza. Aby uzyskać więcej informacji, zobacz [Włącz punkt zarządzania dla protokołu HTTPS](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway#enable-management-point-for-https).  

#### <a name="bkmk_token2"></a> Scenariusz 2. Klient z punktem dystrybucji
<!--1358228-->
Grupy roboczej lub klienta usługi Azure AD przyłączone mogą pobierać zawartość przy użyciu bezpiecznego kanału z punktu dystrybucji skonfigurowanego do obsługi protokołu HTTP.   

#### <a name="bkmk_token3"></a> Scenariusz 3 tożsamości urządzenia w usłudze Azure AD 
<!--1358460-->
Przyłączonych do usługi Azure AD lub [urządzenia hybrydowej usługi Azure AD](/azure/active-directory/device-management-introduction#hybrid-azure-ad-joined-devices) bez usługi Azure AD zalogowany użytkownik może bezpiecznego komunikowania się z przypisanej do niego lokacji. Tożsamość oparta na chmurze urządzeniami teraz jest odpowiednia do uwierzytelniania za pomocą punktu zarządzania i CMG.  


### <a name="prerequisites"></a>Wymagania wstępne  

- Punkt zarządzania skonfigurowany dla połączeń klienta HTTP. Ustaw tę opcję na **ogólne** kartę Właściwości roli systemu lokacji.  

- Punkt dystrybucji skonfigurowany dla połączeń klienta HTTP. Ustaw tę opcję na **ogólne** kartę Właściwości roli systemu lokacji. Nie należy włączać opcji **Zezwalaj klientom na anonimowe połączenia**.  

- Brama zarządzania chmury.  

- Dodaj witrynę do usługi Azure AD do zarządzania chmurą.  

    - Jeśli te wymagania wstępne dla witryny już zostały spełnione, musisz zaktualizować aplikację usługi Azure AD. W konsoli programu Configuration Manager, przejdź do **administracji** obszaru roboczego, rozwiń węzeł **usługi w chmurze**i wybierz **Azure Active Directory dzierżaw**. Wybierz dzierżawę usługi Azure AD, wybierz aplikację sieci web w **aplikacji** okienka, a następnie kliknij przycisk **zaktualizować ustawienia aplikacji** na Wstążce.  

- Klient z systemem Windows 10 w wersji 1803 i połączone z usługą Azure AD. (To wymaganie dotyczy technicznie tylko [Scenariusz 3](#bkmk_token3).) 


### <a name="try-it-out"></a>Wypróbuj
Spróbuj wykonać zadania. Wyślij [opinii](capabilities-in-technical-preview-1804.md#bkmk_feedback) zawiadomienie nas o tym, jak Ci poszło.

1. W konsoli programu Configuration Manager, przejdź do **administracji** obszaru roboczego, rozwiń węzeł **konfiguracja lokacji**i wybierz **witryny**. Wybierz lokację, a następnie kliknij przycisk **właściwości** na Wstążce.  

2. Przełącz się do **komunikacja komputerów klienckich** kartę. Wybierz opcję dla **HTTP lub HTTPS** , a następnie włącz opcję Nowy **wygenerowane za pomocą konfiguracji Menedżera certyfikatów dla protokołu HTTP z systemami lokacji**.  

Zobacz wcześniej [listę scenariuszy](#bkmk_token) do sprawdzania poprawności.

> [!Tip]
> W tej wersji odczekanie 30 minut dla punktu zarządzania do pobierania i skonfiguruj nowy certyfikat z lokacji.

Te certyfikaty w konsoli programu Configuration Manager jest widoczny. Przejdź do **administracji** obszaru roboczego, rozwiń węzeł **zabezpieczeń**i wybierz **certyfikaty** węzła. Wyszukaj **wystawiania SMS** certyfikatu głównego, a także certyfikaty roli serwera lokacji, wystawiony przez urząd główny wystawiającego certyfikaty programu SMS.


### <a name="known-issues"></a>Znane problemy
- Użytkownik nie można wyświetlić w programie Software Center wszystkie aplikacje przeznaczone dla nich jako dostępne.  

- Scenariusze wdrażania systemu operacyjnego nadal wymaga konta dostępu do sieci.  

- Szybko i wielokrotnie Włączanie i wyłączanie opcji **wygenerowane za pomocą konfiguracji Menedżera certyfikatów dla protokołu HTTP z systemami lokacji** może spowodować, że certyfikat do powiązania nie zostało prawidłowo z rolami systemu lokacji. Nie certyfikatów wystawianych przez certyfikatu "SMS wystawiania" są powiązane z witryny sieci Web w systemu Windows Server Internet informacji usług (IIS). Aby obejść ten problem, należy usunąć wszystkie certyfikaty wydane przez "SMS wystawienie" z **SMS** certyfikatu magazynu w systemie Windows, a następnie ponownie uruchom usługę przez proces smsexec.



## <a name="improvements-for-enabling-third-party-software-update-support"></a>Ulepszenia włączania obsługi aktualizacji oprogramowania innych firm
<!--1357605-->
W wyniku UserVoice opinie na temat [Obsługa aktualizacji oprogramowania innych firm](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/8803711-3rd-party-patching-scup-integration-with-sccm-co), dalej w tej wersji, który iteruje po o integracji z System Center aktualizuje wydawcy (SCUP). Wersja zapoznawcza technical preview programu Configuration Manager [wersji 1803](/sccm/core/get-started/capabilities-in-technical-preview-1803#enable-third-party-software-update-support-on-clients) dodano możliwość odczytać certyfikatu z serwera WSUS aktualizacji innych firm, a następnie wdrożyć ten certyfikat do klientów. Jednak nadal potrzebne do używania narzędzia SCUP tworzenie i zarządzanie nimi certyfikat do podpisania aktualizacji oprogramowania innych firm.

W tej wersji aby umożliwić lokacji programu Configuration Manager automatycznie skonfigurować certyfikat. Lokacja komunikuje się z serwerem WSUS w celu wygenerowania certyfikatu w tym celu. Configuration Manager nadal wdrożenia tego certyfikatu do klientów. Tą iterację eliminuje potrzebę korzystania z narzędzia SCUP tworzenie i zarządzanie nimi certyfikatu. 

Aby uzyskać więcej informacji na ogólne użycie narzędzia SCUP, zobacz [System Center Updates Publisher](/sccm/sum/tools/updates-publisher).

### <a name="prerequisites"></a>Wymagania wstępne
- Włączyć i wdrożyć ustawienia klienta **Włącz aktualizacje oprogramowania innych firm** w **aktualizacji oprogramowania** grupy.
- Jeśli usługi WSUS znajduje się na innym serwerze niż punkt aktualizacji oprogramowania, wykonaj jedną z następujących opcji na zdalnym serwerze programu WSUS:
    - Włączanie usługi Rejestr zdalny w systemie Windows  
    lub
    - W kluczu rejestru `HKLM\Software\Microsoft\Update Services\Server\Setup`, Utwórz nową wartość typu DWORD o nazwie **EnableSelfSignedCertificates** o wartości `1`. 

### <a name="try-it-out"></a>Wypróbuj
Spróbuj wykonać zadania. Wyślij [opinii](capabilities-in-technical-preview-1804.md#bkmk_feedback) zawiadomienie nas o tym, jak Ci poszło.

1. W konsoli programu Configuration Manager, przejdź do **administracji** obszaru roboczego. Rozwiń węzeł **konfiguracja lokacji** i wybierz **witryny**. Wybierz lokację najwyższego poziomu, kliknij przycisk **Konfiguruj składniki lokacji** w wstążki, a następnie wybierz **punkt aktualizacji oprogramowania**.  

2. Przełącz się do **aktualizacji innych firm** kartę. Wybierz opcję **Włącz aktualizacje oprogramowania innych firm**, a następnie wybierz opcję **programu Configuration Manager automatycznie zarządza certyfikat**.

3. Kontynuuj reszty Typowy przepływ pracy SCUP importowania katalogu aktualizacji oprogramowania innych firm, a następnie wdrożyć aktualizacje na klientach.



## <a name="improvements-to-windows-10-in-place-upgrade-task-sequence"></a>Ulepszenia dotyczące sekwencji zadań uaktualniania w miejscu systemu Windows 10
<!--1358500-->

Domyślny szablon sekwencji zadań dla uaktualnienia w miejscu systemu Windows 10 zawiera teraz innej nowej grupy zalecanych czynności można dodać w przypadku, gdy proces uaktualniania zakończy się niepowodzeniem. Te akcje ułatwiają rozwiązywanie problemów.

### <a name="new-groups-under-run-actions-on-failure"></a>Nowe grupy w obszarze **wykonanie akcji po awarii**
- **Zbieranie dzienników**: Aby zebrać dzienniki od klienta, należy dodać kroki w tej grupie. 
    - Popularną praktyką służy do kopiowania plików dziennika w udziale sieciowym. Aby ustanowić połączenia, należy użyć [Połącz z folderem sieciowym](/sccm/osd/understand/task-sequence-steps#BKMK_ConnectToNetworkFolder) kroku. 
    - Aby wykonać operację kopiowania, użyj niestandardowego skryptu lub narzędzia przy użyciu jednej [Uruchom wiersz polecenia](/sccm/osd/understand/task-sequence-steps#BKMK_RunCommandLine) lub [Uruchom skrypt programu PowerShell](/sccm/osd/understand/task-sequence-steps#BKMK_RunPowerShellScript) kroku.
    - Zbierane pliki może obejmować następujące dzienniki:  
         `%_SMSTSLogPath%\*.log`   
         `%SystemDrive%\$Windows.~BT\Sources\Panther\setupact.log`  
    - Aby uzyskać więcej informacji o setupact.log, a inne dzienniki Instalatora systemu Windows, zobacz [plikach dziennika Instalatora Windows](/windows/deployment/upgrade/log-files).
    - Aby uzyskać więcej informacji o dzienniki klienta programu Configuration Manager, zobacz [dzienniki klienta programu Configuration Manager](/sccm/core/plan-design/hierarchy/log-files#BKMK_ClientLogs)
    - Aby uzyskać więcej informacji na _SMSTSLogPath i inne przydatne zmienne, zobacz [wbudowane zmienne sekwencji zadań](/sccm/osd/understand/task-sequence-built-in-variables)

- **Uruchamianie narzędzi diagnostycznych**: Aby uruchomić dodatkowe narzędzia diagnostyczne, należy dodać kroki w tej grupie. Powinno zostać zautomatyzowane tych narzędzi do gromadzenia dodatkowych informacji z systemu jak najszybciej po niepowodzeniu jak to możliwe.
    - Jest jednym z takich narzędzi Windows [SetupDiag](/windows/deployment/upgrade/setupdiag). Jest to samodzielne narzędzie diagnostyczne, używanego w celu uzyskania szczegółowych informacji na temat przyczyny niepowodzenia uaktualniania systemu Windows 10.
         - W programie Configuration Manager [Utwórz pakiet](/sccm/apps/deploy-use/packages-and-programs#create-a-package-and-program) narzędzia.
         - Dodaj [Uruchom wiersz polecenia](/sccm/osd/understand/task-sequence-steps#BKMK_RunCommandLine) krok do tej grupy sekwencji zadań. Użyj **pakietu** opcję, aby odwołać narzędzie. Przykładem jest następujący ciąg **wiersza polecenia**:  
             `SetupDiag.exe /Output:"%_SMSTSLogPath%\SetupDiagResults.log" /Mode:Online`



## <a name="cmtrace-installed-with-client"></a>CMTrace zainstalowane z klientem
<!--1357971-->

Narzędzia do przeglądania dziennika CMTrace teraz jest instalowany automatycznie wraz z klientem programu Configuration Manager. Jest ona dodawana do katalogu instalacyjnego klienta, która domyślnie jest `%WinDir%\ccm\cmtrace.exe`.

> [!Note]  
> CMTrace jest *nie* automatycznie zarejestrowane w usłudze Windows, aby otworzyć rozszerzenie log.



## <a name="improvement-to-the-configuration-manager-console"></a>Ulepszenia w konsoli programu Configuration Manager
<!--1358202-->
Wprowadziliśmy następujące ulepszenia w konsoli programu Configuration Manager:

- Listy urządzeń w obszarze zasoby i zgodność, urządzeń, teraz domyślnie wyświetla aktualnie zalogowanego użytkownika. Ta wartość jest jako bieżący jako [stanu klienta](/sccm/core/clients/manage/monitor-clients#bkmk_indStatus). Wartość zostanie wyczyszczona po wylogowaniu. Jeśli żaden użytkownik nie jest zalogowany, wartość jest pusta. 

### <a name="known-issues"></a>Znane problemy
Obecnie zalogowanego użytkownika wartość jest pusta, w węźle urządzenia lub podczas wyświetlania listy urządzeń w obszarze węzła kolekcje urządzeń. Aby obejść ten problem, Pobierz [skryptu SQL](https://gallery.technet.microsoft.com/ConfigMgr-1805-BgbUpdateLiv-306ff46c). Sp_BgbUpdateLiveData.sql na serwerze bazy danych lokacji i ponownego uruchamiania usług smsexec i sms_notification_server w punkcie zarządzania.<!--514471-->



## <a name="improvements-to-console-feedback"></a>Ulepszenia konsoli opinii
<!--1357542-->
W tej wersji dodano następujące ulepszenia do nowego [opinii](capabilities-in-technical-preview-1804.md#bkmk_feedback) mechanizm w konsoli programu Configuration Manager:  

- Okno dialogowe opinii pamięta teraz poprzednich ustawień, takich jak wybrane opcje i adres e-mail.  

- Obsługuje ona teraz w trybie offline opinii. Zapisz swoją opinię w konsoli, a następnie przekazać do firmy Microsoft z systemu podłączonej do Internetu. Użyj nowego narzędzia przesyłania opinii w trybie offline znajduje się w `cd.latest\SMSSETUP\Tools\UploadOfflineFeedback\UploadOfflineFeedback.exe`. Aby wyświetlić dostępne i wymagane opcje wiersza polecenia, należy uruchomić narzędzie z `--help` opcji. Połączony system musi mieć dostęp do **petrol.office.microsoft.com**.

### <a name="known-issues"></a>Znane problemy
Korzystając z **Wyślij uśmiech** lub **Wyślij niezadowolenie** z poziomu konsoli na komputerze z łącznością z Internetem, może zwrócić z następującym komunikatem: "Wystąpił błąd podczas wysyłania opinii." Po kliknięciu **szczegółowe**, widoczny jest następujący tekst: `{"Message":""}`. Przyczyną tego błędu jest to znany problem z odpowiedzią z wewnętrznej bazy danych systemu opinii. Można zignorować ten błąd. Microsoft nadal otrzymał Twoją opinię. (Jeśli zostanie wyświetlone szczegóły inny komunikat, użyć w trybie offline opinie aby ponowić próbę wysyłanie opinii w późniejszym czasie).



## <a name="improvements-to-pxe-enabled-distribution-points"></a>Ulepszenia do punktów dystrybucji z włączoną obsługą środowiska PXE
<!--1357580-->

Korzystając z opcji w tej wersji dodano następujące dodatkowe ulepszenia [ **włączyć obiekt odpowiadający środowiska PXE bez usług wdrażania systemu Windows** ](/sccm/core/get-started/capabilities-in-technical-preview-1802#improvements-to-pxe-enabled-distribution-points) punktu dystrybucji:  

- Zasady zapory systemu Windows są tworzone automatycznie w punkcie dystrybucji, po włączeniu tej opcji  
- Ulepszenia rejestrowanie składników



## <a name="improvement-to-hardware-inventory-for-large-integer-values"></a>Poprawa spis sprzętu dla dużej liczby całkowite
<!--1357880-->
Spis sprzętu aktualnie ma limit liczby całkowite większe niż 4 294 967 296 (2 ^ 32). Ten limit jest osiągalna dla atrybutów, takich jak dysk twardy rozmiar w bajtach. Punkt zarządzania nie przetwarza wartości będące liczbami całkowitymi przekracza ten limit, w związku z tym nie wartości są przechowywane w bazie danych. Obecnie w tej wersji limit zostaje zwiększona do 18,446,744,073,709,551,616 (2 ^ 64). 

Dla właściwości z wartością, która nie ulega zmianie, takich jak łącznego rozmiaru dysku nie od razu widać wartość po uaktualnieniu lokacji. Większość spis sprzętu jest raport delta. Klient wysyła tylko wartości, które spowodują zmianę. Aby obejść ten problem, należy dodać do tej samej klasy innej właściwości. Ta akcja powoduje, że klient modyfikowanie wszystkich właściwości w klasie zmienione. 



## <a name="improvement-to-wsus-maintenance"></a>Poprawy obsługi usług WSUS
<!--1357898-->

Kreatora oczyszczania usług WSUS odrzuci teraz aktualizacje, które wygasły lub zastąpione zgodnie z regułami zastępowania. Te reguły są definiowane na właściwości składnika punktu aktualizacji oprogramowania.

### <a name="try-it-out"></a>Wypróbuj
Spróbuj wykonać zadania. Wyślij [opinii](capabilities-in-technical-preview-1804.md#bkmk_feedback) zawiadomienie nas o tym, jak Ci poszło.

1. W konsoli programu Configuration Manager, przejdź do **administracji** obszaru roboczego. Rozwiń węzeł **konfiguracja lokacji** i wybierz **witryny**. Wybierz lokację najwyższego poziomu, kliknij przycisk **Konfiguruj składniki lokacji** w wstążki, a następnie wybierz **punkt aktualizacji oprogramowania**.  

2. Przełącz się do **reguły zastępowania** kartę. Włącz opcję, aby **WSUS Uruchom Kreatora oczyszczania**. Określ zachowanie żądaną zastępowania.  

3. Przejrzyj plik WSyncMgr.log file.



## <a name="improvement-to-support-for-cng-certificates"></a>Poprawy jakości obsługi w przypadku certyfikatów CNG
<!--1357314-->
W tej wersji, należy użyć [certyfikatów CNG](/sccm/core/plan-design/network/cng-certificates-overview) dla następujących ról dodatkowy serwer z włączoną obsługą HTTPS:  
- Punkt rejestracji certyfikatu, włącznie z serwera usługi NDES z modułem zasad programu Configuration Manager



## <a name="next-steps"></a>Następne kroki
Uzyskać informacji dotyczących instalowania lub aktualizowania gałęzi wersji zapoznawczej technical preview, zobacz [Technical Preview programu System Center Configuration Manager](/sccm/core/get-started/technical-preview).    
