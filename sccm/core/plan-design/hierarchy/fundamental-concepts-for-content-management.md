---
title: "Podstawy zarządzania zawartością | Dokumentacja firmy Microsoft"
description: "Użyj narzędzia i opcje w programie System Center Configuration Manager do zarządzania zawartością, który można wdrożyć."
ms.custom: na
ms.date: 05/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c201be2a-692c-4d67-ac95-0a3afa5320fe
caps.latest.revision: 28
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 212628639300e9c361f7cee61b3df6b1cb6874ce
ms.openlocfilehash: f73dde64e0e8a0fc49f45b3afb3b8f00c926a820
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="fundamental-concepts-for-content-management-in-system-center-configuration-manager"></a>Podstawowe pojęcia związane z zarządzaniem zawartością w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

System Center Configuration Manager obsługuje stabilny system narzędzia i opcje zarządzania zawartością, który wdrażania w aplikacji, pakietów, aktualizacji oprogramowania i wdrożeń systemu operacyjnego.  

Zawartość, którą można wdrożyć znajduje się na obu serwerach lokacji i na serwerach systemu lokacji punktu dystrybucji. Ta zawartość może zająć dużo przepustowości sieci jest przesyłana między lokalizacjami. Aby efektywnie planować i korzystanie z infrastruktury zarządzania zawartością, zalecamy poznać dostępne opcje i konfiguracji, a następnie wziąć pod uwagę sposób używania ich do optymalnego dopasowania środowisko sieciowe i wymaga wdrożenia zawartości.  

> [!TIP]    
> Możesz dowiedzieć się więcej na temat procesu dystrybucji zawartości i znaleźć pomocy w diagnozowaniu i rozwiązywaniu problemów ogólne dystrybucji zawartości. Zobacz [zrozumienie i rozwiązywanie problemów z zawartością dystrybucji programu Microsoft Configuration Manager](https://support.microsoft.com/help/4000401/content-distribution-in-mcm) na support.microsoft.com.

Poniżej opisano kluczowe pojęcia związane z zarządzaniem zawartością. W przypadku pojęć wymagających dodatkowych lub złożonych informacji podano linki kierujące do szczegółów.

## <a name="accounts-used-for-content-management"></a>Konta używane do zarządzania zawartością  
 Do zarządzania zawartością można stosować następujące konta:  

-   **Konto dostępu do sieci**: Używane przez klientów, połącz się z punktem dystrybucji oraz uzyskiwania dostępu do zawartości. Domyślnie konto komputera zostanie wybrany jako pierwszy.  

     To konto jest również używane przez punkty dystrybucji uzyskanie zawartości ze źródłowego punktu dystrybucji w lesie zdalnym.  

-   **Konto dostępu do pakietu**: Domyślnie program Configuration Manager daje dostęp do zawartości w punkcie dystrybucji do ogólnych kont dostępu użytkownikom i administratorom. Można jednak skonfigurować dodatkowe uprawnienia, aby ograniczyć dostęp.   

-   **Konto połączenia multiemisji**: Używany do wdrażania systemu operacyjnego.  

Aby uzyskać więcej informacji o tych kont, zobacz [Zarządzanie kontami dostępu do zawartości](../../../core/plan-design/hierarchy/manage-accounts-to-access-content.md).

## <a name="bandwidth-throttling-and-scheduling"></a>Ograniczenie przepustowości i planowanie  
 Ograniczenie przepustowości i planowanie to opcje ułatwiające kontrolowanie momentu dystrybucji zawartości z serwera lokacji do punktów dystrybucji. Przypominają one elementy sterujące przepustowością w opartej na plikach replikacji między lokacjami, chociaż nie są z nią bezpośrednio powiązane.  

 Aby uzyskać więcej informacji, zobacz [zarządzanie przepustowością sieci](/sccm/core/plan-design/hierarchy/manage-network-bandwidth).

## <a name="binary-differential-replication"></a>Binarna replikacja różnicowa  
 Automatycznie służy do wymagań wstępnych dla punktów dystrybucji, binarnej replikacji różnicowej (Nagłówka), której jest czasami określany jako replikacja różnicowa, aby zmniejszyć wykorzystanie przepustowości, gdy jest Dystrybucja aktualizacji do zawartości, która wcześniej wdrożona w innych witrynach lub do zdalnych punktów dystrybucji.  

 Replikacja BDR minimalizuje użycie przepustowości sieci na wysyłanie aktualizacji treści, która już została poddana dystrybucji, wysyłając ponownie tylko nową lub zmienioną zawartość zamiast przesyłania całego zestawu plików źródłowych zawartości za każdym razem, kiedy są one zmieniane.  

 W przypadku zastosowania binarnej replikacji różnicowej przy użyciu programu Configuration Manager identyfikuje zmiany w plikach źródłowych dla każdego zestawu zawartości, która została wcześniej poddana dystrybucji.  

-   Po zmianie plików zawartości źródła programu Configuration Manager tworzy nową przyrostową wersję zestawu zawartości i replikuje tylko zmienione pliki, do lokacji docelowych i punktów dystrybucji. Plik jest uważany za zmieniony, jeśli została zmieniona lub przeniesione lub zmieniono zawartość pliku. Jeśli przykładowo użytkownik zastępuje pojedynczy plik sterownika w pakiecie wdrożeniowym systemu operacyjnego, który wcześniej został wysłany do kilku lokacji, w tych lokacjach docelowych jest replikowany tylko zmieniony plik sterownika.  

-   Program Configuration Manager obsługuje do pięciu przyrostowych wersji zawartości przed ponownym wysłaniem całego zestawu zawartości. Po piątej aktualizacji kolejna zmiana zestawu zawartości powoduje Configuration Manager, aby utworzyć nową wersję zestawu zawartości. Następnie Menedżer konfiguracji dystrybuuje nową wersję zestawu, zastępując poprzedni zestaw i wszystkie jego wersje przyrostowe zawartości. Po wysłaniu nowej zawartości kolejne zmiany przyrostowe plików źródłowych są replikowane ponownie w ramach binarnej replikacji różnicowej.  


Replikacja BDR jest obsługiwana między poszczególnymi lokacjami nadrzędnymi i podrzędnymi w hierarchii. W obrębie lokacji Nagłówka jest obsługiwana między serwerem lokacji a jego punktami dystrybucji regularne. Jednak ściągające punkty dystrybucji i punkty dystrybucji w chmurze nie obsługują binarnej replikacji różnicowej do transferu zawartości. Ściągające punkty dystrybucji obsługują zmianami poziomie plików, przesyłania nowych plików, ale nie blokuje w pliku.

Aplikacje zawsze korzystają z binarnej replikacji różnicowej. W przypadku pakietów binarna replikacja różnicowa jest opcjonalna i nie jest włączona domyślnie. Aby korzystać z binarnej replikacji różnicowej dla pakietów, należy włączyć tę funkcję dla każdego z nich. Aby to zrobić, wybierz opcję **Włącz binarną replikację różnicową** podczas tworzenia nowego pakietu lub edytowania zawartości na karcie **Źródło danych** właściwości pakietu.  

## <a name="branchcache"></a>Usługa BranchCache  
 Technologii systemu Windows, która umożliwia klientom, które usługa BranchCache i zostały pobrane wdrożenia, skonfigurowanym do pamięci podręcznej gałęzi, aby następnie służyć jako źródło zawartości do innych klientów korzystających z usługi BranchCache.  

 Przykładowo kiedy pierwszy komputer kliencki z usługą BranchCache zażąda zawartości z punktu dystrybucji z uruchomionym systemem Windows Server 2012, który został skonfigurowany jako serwer usługi BranchCache, komputer kliencki pobierze zawartość i umieści ją w pamięci podręcznej.  

-   Komputera klienta można następnie udostępnić zawartość dla dodatkowych obsługujących usługę BranchCache klientów w tej samej podsieci, które również zawartość z pamięci podręcznej.  

-   Dzięki temu kolejni klienci w tej samej podsieci nie będą musieli pobierać zawartości z punktu dystrybucji, a zawartość będzie rozmieszczona na wielu klientach na potrzeby przyszłych transferów.  

## <a name="peer-cache"></a>Buforowanie równorzędne
Począwszy od wersji 1610 klienta Buforowanie równorzędne ułatwia zarządzanie wdrażaniem zawartości do klientów w lokalizacjach zdalnych. Buforowanie równorzędne jest wbudowane rozwiązanie programu Configuration Manager, które umożliwia klientom na współużytkowanie zawartości z innymi klientami bezpośrednio z lokalnej pamięci podręcznej.

Po wdrożeniu ustawień klienta, które umożliwiają Buforowanie równorzędne w kolekcji członków tej kolekcji może działać jako źródła zawartości elementu równorzędnego dla innych klientów w tej samej grupie granic.

Aby uzyskać więcej informacji, zobacz [Buforowanie równorzędne dla klientów programu Configuration Manager](/sccm/core/plan-design/hierarchy/client-peer-cache).


## <a name="windows-pe-peer-cache"></a>Równorzędna pamięć podręczna systemu Windows PE
Podczas wdrażania nowego systemu operacyjnego w programie System Center Configuration Manager komputerów korzystających z sekwencji zadań umożliwia Buforowanie równorzędne systemu Windows PE pobierania zawartości z lokalnego równorzędnych (peer źródła pamięci podręcznej) zamiast pobierać zawartość z punktu dystrybucji. Minimalizuje to ruch w sieci rozległej w scenariuszach oddziału firmy bez lokalnego punktu dystrybucji.

Aby uzyskać więcej informacji, zobacz [Buforowanie równorzędne systemu Windows PE](../../../osd/get-started/prepare-windows-pe-peer-cache-to-reduce-wan-traffic.md).


## <a name="client-locations"></a>Lokalizacje klientów  
 Poniżej przedstawiono lokalizacje, z których klienci uzyskują dostęp do zawartości:  

-   **Intranet** (lokalnie):  

    -   Punkty dystrybucji można użyć protokołu HTTP lub HTTPs.  

    -   Używać tylko punkt dystrybucji w chmurze dla powrotu, gdy lokalne punkty dystrybucji nie są dostępne.  

-   **Internet**:  

    -   Wymaga punktów dystrybucji do akceptowania protokołu HTTPS.  

    -   Mogą używać punktu dystrybucji w chmurze dla powrotu.  

-   **Grupa robocza**:  

    -   Wymaga punktów dystrybucji do akceptowania protokołu HTTPS.  

    -   Mogą używać punktu dystrybucji w chmurze dla powrotu.  



## <a name="content-library"></a>Biblioteka zawartości  
 Biblioteka zawartości znajduje się SIS zawartość, która pozwala zmniejszyć ogólną połączonych treści zawartości, którą można dystrybuować korzysta z programu Configuration Manager.  

- Dowiedz się więcej o [biblioteki zawartości](../../../core/plan-design/hierarchy/the-content-library.md).
- Użyj [narzędzia Oczyszczanie biblioteki zawartości](/sccm/core/plan-design/hierarchy/content-library-cleanup-tool) usunąć zawartość, która nie jest już skojarzona z aplikacją.  


## <a name="distribution-points"></a>Punkty dystrybucji  
 Program Configuration Manager używa punktów dystrybucji do przechowywania plików, które są wymagane do uruchomienia oprogramowania na komputerach klienckich. Klienci muszą mieć dostęp do co najmniej jednego punktu dystrybucji z którego mogą pobierać pliki zawartości, która jest wdrażana.  

 Punkt dystrybucji (wyspecjalizowanych) podstawowego jest nazywane standardowego punktu dystrybucji. Istnieją dwie odmiany standardowego punktu dystrybucji, które wymagają specjalnej uwagi:  

-   **Ściągający punkt dystrybucji**: Zmiana punktu dystrybucji, gdy punkt dystrybucji uzyskuje zawartość z innego punktu dystrybucji (źródłowego punktu dystrybucji). Ten proces jest podobny do jak klienci pobierają zawartość z punktów dystrybucji. Ściągające punkty dystrybucji może pomóc uniknąć wąskich gardeł przepustowości sieci, występujących na serwerze lokacji musi bezpośrednio dystrybucji zawartości do poszczególnych punktów dystrybucji.  [Użyj ściągający punkt dystrybucji z System Center Configuration Manager](/sccm/core/plan-design/hierarchy/use-a-pull-distribution-point).

-   **Punkt dystrybucji w chmurze**: Zmiana punktu dystrybucji zainstalowanego na Microsoft Azure. [Dowiedz się, jak korzystać z punktu dystrybucji w chmurze z System Center Configuration Manager](../../../core/plan-design/hierarchy/use-a-cloud-based-distribution-point.md).  


Standardowe punkty dystrybucji obsługują szereg konfiguracje i funkcje, takie jak ograniczenia przepustowości i planowania, środowiska PXE i multiemisji, lub wstępnie przygotowanego zawartości.  

-   Można używać formantów, takich jak **harmonogramy** lub **przepustowości** ułatwiające kontrolę transfer.  

-   Można również użyć innych opcji, w tym **wstępnie zawartości**, i **ściągające punkty dystrybucji**. Ponadto można wykorzystać **usługi BranchCache** do zmniejszenia przepustowości sieci, który jest używany podczas wdrażania zawartości.  

-   Punkty dystrybucji obsługują różne konfiguracje  **[PXE](../../../osd/get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_PXEDistributionPoint)**  i  **[multiemisji](../../../osd/get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_DPMulticast)**  dla wdrożeń systemu operacyjnego lub konfiguracji **urządzeń przenośnych**.  

 Oparte na chmurze i ściągających punktów dystrybucji obsługuje wiele z tych tej samej konfiguracji, ale ma ograniczenia, które są specyficzne dla każdej odmiany punktu dystrybucji.  

## <a name="distribution-point-groups"></a>Grupy punktów dystrybucji  
 Grupy punktów dystrybucji są logiczne grupowanie punktów dystrybucji, które można uprościć dystrybucji zawartości.  

 Aby uzyskać więcej informacji, zobacz [umożliwia zarządzanie grupami punktów dystrybucji](../../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_manage).

## <a name="distribution-point-priority"></a>Priorytet punktu dystrybucji  
 Wartość priorytetu punktu dystrybucji jest zależna od czasu, który zajęło przesłanie wcześniejszych wdrożeń do tego punktu dystrybucji.  

-   Jest to wartość Dostraja przypisanej do punktu dystrybucji, który pomaga programu Configuration Manager transferu zawartości do wielu punktów dystrybucji w krótszym czasie.  

-   Podczas dystrybucji zawartości do wielu punktów dystrybucji, w tym samym czasie lub dystrybucji grupy punktów, Configuration Manager wysyła zawartość do punktu dystrybucji o najwyższym priorytecie przed wysłaniem tej samej zawartości do punktu dystrybucji z niższym priorytetem.  

-   Nie zastępuje priorytetu dystrybucji pakietów, które pozostaje decydującym czynnikiem w sekwencji po różne dystrybucje są przenoszone.  


Na przykład jeśli dystrybucji zawartości o wysokim priorytecie dystrybucji do punktu dystrybucji o niskim priorytecie, ten pakiet priorytet Wysoki dystrybucji zawsze zostanie przetransferowany przed pakietem o niższym priorytecie dystrybucji. Priorytet dystrybucji ma zastosowanie, nawet jeśli pakiety o niższym priorytecie dystrybucji są dystrybuowane do punktów dystrybucji o wyższych priorytetach punktu dystrybucji.

Wysoki priorytet dystrybucji pakietu zapewnia, że program Configuration Manager dystrybuuje zawartość do odpowiednich punktów dystrybucji przed wysłaniem jakichkolwiek pakietów o niższym priorytecie dystrybucji.  

> [!NOTE]  
>  Ściągające punkty dystrybucji korzystają również z priorytetów w celu ustalenia sekwencji źródłowych punktów dystrybucji.  
>   
>  -   Priorytet punktu dystrybucji do transferu zawartości do punktu dystrybucji różni się od priorytetu punktów dystrybucji ściągania używać podczas wyszukiwania zawartości ze źródłowego punktu dystrybucji.  
>  -   Aby uzyskać więcej informacji, zobacz [użycia punktu dystrybucji z System Center Configuration Manager](/sccm/core/plan-design/hierarchy/use-a-pull-distribution-point).  


## <a name="fallback"></a>Opcja rezerwowa  
 Począwszy od wersji 1610 kilka czynności zostały zmienione w taki sposób, że klienci znajdą punkt dystrybucji, który ma zawartość, w tym powrotu. Użyj poniższych informacji, które mają zastosowanie do używanej wersji:

**Wersja 1610 i nowsze**   
Klienci, którzy nie można odnaleźć zawartości z punktu dystrybucji, który jest skojarzony z grupą granic, ich bieżący przełączają się użyć lokalizacji źródła zawartości, które są powiązane z grupami granic sąsiada. Do użycia jako bazowy, grupy granic sąsiada musi mieć zdefiniowanej relacji z grupą granic bieżącego klienta. Ta relacja obejmuje skonfigurowanym czasie, który musi minąć, zanim klient, który nie może odnaleźć zawartość lokalnie może zawierać zawartości źródła z grupy granic sąsiada w ramach jego wyszukiwania.

Pojęcia dystrybucji punktów nie są już używane, ustawień i **Zezwalaj lokalizacje rezerwowego źródła zawartości** nie są już dostępne lub wymuszone.

Aby uzyskać więcej informacji, zobacz [grup granic](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups).


**Wersja 1511, 1602 i 1606**   
Awaryjne są powiązane z użyciem **preferowane punkty dystrybucji** i lokalizacji źródła zawartości, które są używane przez klientów.

-   Domyślnie klienci pobierają zawartość tylko z punktu dystrybucji (taki, który jest skojarzony z grupy granic klienta).  

-   Jednak jeśli dla punktu dystrybucji skonfigurowano opcję **Zezwalaj klientom na stosowanie tego systemu lokacji jako rezerwowej lokalizacji źródłowej dla zawartości**, ten punkt dystrybucji jest oferowany jako poprawne źródło zawartości tylko tym klientom, którzy nie mogą uzyskać wdrożenia z żadnego z preferowanych punktów dystrybucji.  


Aby uzyskać informacje o różnych lokalizacji zawartości i przełączania awaryjnego, zobacz [scenariusze lokalizacji źródła zawartości](../../../core/plan-design/hierarchy/content-source-location-scenarios.md). Informacje o grupach granic, zobacz [grup granic dla wersji 1511,1602 i 1606](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606).

## <a name="network-bandwidth"></a>Przepustowość sieci  
 Aby ułatwić zarządzanie wielkość przepustowości sieci używanej podczas dystrybucji zawartości, można użyć następujących opcji:  

-   **Wstępnie przygotowane zawartość**:  Proces przesyłania zawartości do punktu dystrybucji bez polegania na programu Configuration Manager do dystrybucji zawartości w sieci.  

-   **Planowanie i dławienie**: Konfiguracje, które pomagają kontrolować, kiedy i jak zawartość jest rozsyłana do punktów dystrybucji.  

Aby uzyskać więcej informacji, zobacz [zarządzanie przepustowością sieci](/sccm/core/plan-design/hierarchy/manage-network-bandwidth).

## <a name="network-connection-speed-to-content-source"></a>Szybkość połączenia sieciowego ze źródłem zawartości  
Począwszy od wersji 1610 kilka czynności zostały zmienione w taki sposób, że klienci znajdą punkt dystrybucji, który ma zawartość, w tym szybkość połączenia sieciowego do źródła zawartości. Użyj poniższych informacji, które mają zastosowanie do używanej wersji:

**Wersja 1610 i nowsze**   
Szybkość połączenia sieciowego definiujące dystrybucji jako punktu **Fast** lub **wolno** nie są już używane. Zamiast tego każdy system lokacji, który jest skojarzony z grupą granic jest traktowany takie same.

Aby uzyskać więcej informacji, zobacz [grup granic](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups).


**Wersja 1511, 1602 i 1606**   
 Istnieje możliwość skonfigurowania szybkości połączenia sieciowego każdego punktu dystrybucji w grupie granic:  

-   Klienci używają tej wartości, gdy łączą się z punktem dystrybucji.

-   Domyślnie szybkość połączenia sieciowego jest skonfigurowana jako **Fast**, ale można ją również ustawić jako **wolno**.  

-   **Szybkość połączenia sieciowego**, wraz z konfiguracji wdrożenia, należy określić, czy klient może pobierać zawartość z punktu dystrybucji, gdy klient jest skojarzona grupa granic  

Aby uzyskać informacje o różnych lokalizacji zawartości i przełączania awaryjnego, zobacz [scenariusze lokalizacji źródła zawartości](../../../core/plan-design/hierarchy/content-source-location-scenarios.md). Informacje o grupach granic, zobacz [grup granic dla wersji 1511,1602 i 1606](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606).

## <a name="on-demand-content-distribution"></a>Dystrybucja zawartości na żądanie  
 Dystrybucja zawartości na żądanie jest opcją można ustawić dla osoby, aplikacji i pakietów (bez), aby włączyć na żądanie zawartości dystrybucji do preferowanych punktów dystrybucji.  

-   Aby włączyć tę opcję wdrożenia, Włącz **Dystrybuuj zawartość tego pakietu do preferowanych punktów dystrybucji**.  

-   Gdy ta opcja jest włączona dla wdrożenia i klient próbuje żądania tej zawartości, ale zawartość nie jest dostępna w każdym z punktów dystrybucji klienta, programu Configuration Manager automatycznie dystrybuuje zawartość do punktów dystrybucji klienta.  

-   Mimo że to wyzwala programu Configuration Manager automatycznie dystrybucji zawartości, do którego klient preferowanych punktów dystrybucji, klient może uzyskać tej zawartości z innych punktów dystrybucji przed preferowanych punktów dystrybucji dla klienta otrzymania wdrożenia. W takim przypadku zawartość będzie obecny w tym punkcie dystrybucji do użytku przez klienta dalej, który ma tego wdrożenia.  

Jeśli używasz wersji 1610 lub nowszej, zobacz [grup granic](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups).
Jeśli używasz wersji 1511, 1602 lub 1606, zobacz [scenariusze lokalizacji źródła zawartości](../../../core/plan-design/hierarchy/content-source-location-scenarios.md) informacji o różnych lokalizacji zawartości i przełączania awaryjnego.  



## <a name="package-transfer-manager"></a>Menedżer transferu pakietów  
 Menedżer transferu pakietów jest składnika serwera lokacji, która przesyła zawartość do punktów dystrybucji na innych komputerach.  

 Dowiedz się więcej o [Menedżer transferu pakietów](../../../core/plan-design/hierarchy/package-transfer-manager.md).  

## <a name="preferred-distribution-point"></a>Preferowany punkt dystrybucji  
 Preferowany punkt dystrybucji zawiera punkty dystrybucji, które są skojarzone z bieżącej grupy granic do klienta.  

 Istnieje możliwość skojarzenia każdego punktu dystrybucji z jedną lub większą liczbą grup granic:  

-   To skojarzenie ułatwia programowi klienta zidentyfikować punkty dystrybucji, z których można pobrać zawartość.  
-   Domyślnie klienci mogą pobierać tylko zawartość z preferowanego punktu dystrybucji.  


Aby uzyskać więcej informacji:
 - Jeśli używasz wersji 1610 lub nowszej, zobacz [grup granic](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups).
 - Jeśli używasz wersji 1511, 1602 lub 1606, zobacz [scenariusze lokalizacji źródła zawartości](../../../core/plan-design/hierarchy/content-source-location-scenarios.md).

## <a name="prestage-content"></a>Wstępne przygotowanie zawartości  
 Wstępne przygotowanie zawartości jest proces przesyłania zawartości do punktu dystrybucji bez polegania na programu Configuration Manager do dystrybucji zawartości w sieci.  

 Aby uzyskać więcej informacji, zobacz [zarządzanie przepustowością sieci](/sccm/core/plan-design/hierarchy/manage-network-bandwidth).

