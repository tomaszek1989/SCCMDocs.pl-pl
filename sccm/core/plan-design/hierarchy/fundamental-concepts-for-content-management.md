---
title: "Podstawowe informacje na temat zarządzania zawartością"
titleSuffix: Configuration Manager
description: "Użyj narzędzi i opcji w programie System Center Configuration Manager do zarządzania zawartością, którą można wdrożyć."
ms.custom: na
ms.date: 05/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c201be2a-692c-4d67-ac95-0a3afa5320fe
caps.latest.revision: "28"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: d550d18de93f5e11c7538de24473d36c788145e6
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="fundamental-concepts-for-content-management-in-system-center-configuration-manager"></a>Podstawowe pojęcia związane z zarządzaniem zawartością w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

System Center Configuration Manager obsługuje niezawodny system narzędzi i opcji do zarządzania zawartością wdrażaną jako aplikacje, pakiety, aktualizacje oprogramowania i wdrożeń systemu operacyjnego.  

Zawartość, którą można wdrożyć są przechowywane na serwerach lokacji i na serwerach systemu lokacji punktu dystrybucji. Zawartość ta może wymagać dużej ilości przepustowości sieci, gdy są przesyłane między lokacjami. Efektywne planowanie i wykorzystanie infrastruktury zarządzania zawartością, zalecamy opisano dostępne opcje i konfiguracje, a także rozważenia sposób ich użycia w celu optymalnego dopasowania środowisku sieciowemu i potrzebom związanym z wdrażaniem zawartości.  

> [!TIP]    
> Możesz dowiedzieć się więcej na temat procesu dystrybucji zawartości i znaleźć pomoc w diagnozowania i rozwiązywania problemów ogólne dystrybucji zawartości. Zobacz [zrozumienie i rozwiązywanie problemów z dystrybucji w programie Microsoft Configuration Manager zawartości](https://support.microsoft.com/help/4000401/content-distribution-in-mcm) w witrynie support.microsoft.com.

Poniżej przedstawiono podstawowe pojęcia związane z zarządzaniem zawartością. W przypadku pojęć wymagających dodatkowych lub złożonych informacji podano linki kierujące do szczegółów.

## <a name="accounts-used-for-content-management"></a>Konta używane do zarządzania zawartością  
 Do zarządzania zawartością można stosować następujące konta:  

-   **Konto dostępu do sieci**: Używany przez klientów, aby podłączyć się do punktu dystrybucji i uzyskiwać dostęp do zawartości. Domyślnie konto komputera jest wybrany jako pierwszy.  

     To konto jest również używane przez punkty dystrybucji ściągania pobierać zawartość ze źródłowego punktu dystrybucji w lesie zdalnym.  

-   **Konto dostępu do pakietu**: Domyślnie program Configuration Manager udziela dostępu do zawartości w punkcie dystrybucji dla ogólnych kont dostępu użytkowników i administratorów. Można jednak skonfigurować dodatkowe uprawnienia, aby ograniczyć dostęp.   

-   **Konto połączenia multiemisji**: Użyć wdrożeń systemu operacyjnego.  

Aby uzyskać więcej informacji o tych kont, zobacz [Zarządzanie kontami dostępu do zawartości](../../../core/plan-design/hierarchy/manage-accounts-to-access-content.md).

## <a name="bandwidth-throttling-and-scheduling"></a>Ograniczenie przepustowości i planowanie  
 Ograniczenie przepustowości i planowanie to opcje ułatwiające kontrolowanie momentu dystrybucji zawartości z serwera lokacji do punktów dystrybucji. Przypominają one elementy sterujące przepustowością w opartej na plikach replikacji między lokacjami, chociaż nie są z nią bezpośrednio powiązane.  

 Aby uzyskać więcej informacji, zobacz [zarządzanie przepustowością sieci](/sccm/core/plan-design/hierarchy/manage-network-bandwidth).

## <a name="binary-differential-replication"></a>Binarna replikacja różnicowa  
 Wymaganiem wstępnym dla punktów dystrybucji, binarna replikacja różnicowa (BDR), która czasem jest nazywana replikacja różnicowa, jest automatycznie używany do ograniczania wykorzystania przepustowości podczas jest dystrybucji aktualizacji zawartości wdrożonej wcześniej do innych lokacji lub do zdalnych punktów dystrybucji.  

 Replikacja BDR minimalizuje użycie przepustowości sieci na wysyłanie aktualizacji treści, która już została poddana dystrybucji, wysyłając ponownie tylko nową lub zmienioną zawartość zamiast przesyłania całego zestawu plików źródłowych zawartości za każdym razem, kiedy są one zmieniane.  

 W przypadku zastosowania binarnej replikacji różnicowej program Configuration Manager identyfikuje zmiany w plikach źródłowych dla każdego zestawu zawartości, która została wcześniej poddana dystrybucji.  

-   Po zmianie plików zawartości źródła programu Configuration Manager tworzy nową przyrostową wersję zestawu zawartości i replikuje tylko zmienione pliki do lokacji docelowych i punktów dystrybucji. Plik jest uważany za zmieniony, jeśli została zmieniona lub przenieść lub zawartość pliku zostały zmienione. Jeśli przykładowo użytkownik zastępuje pojedynczy plik sterownika w pakiecie wdrożeniowym systemu operacyjnego, który wcześniej został wysłany do kilku lokacji, w tych lokacjach docelowych jest replikowany tylko zmieniony plik sterownika.  

-   Program Configuration Manager obsługuje do pięciu przyrostowych wersji zawartości przed jego przesłania całego zestawu zawartości. Po piątej aktualizacji kolejna zmiana zestawu zawartości powoduje, że Configuration Manager, aby utworzyć nową wersję zestawu zawartości. Menedżer konfiguracji następnie dystrybuuje nową wersję zestawu w celu zastąpienia poprzedniego zestawu i wszystkich jego przyrostowych wersji zawartości. Po wysłaniu nowej zawartości kolejne zmiany przyrostowe plików źródłowych są replikowane ponownie w ramach binarnej replikacji różnicowej.  


Replikacja BDR jest obsługiwana między poszczególnymi lokacjami nadrzędnymi i podrzędnymi w hierarchii. W ramach lokacji replikacja BDR jest obsługiwana między serwerem lokacji a jego punktami dystrybucji regularne. Jednak ściągające punkty dystrybucji i punkty dystrybucji w chmurze nie obsługują binarnej replikacji różnicowej do transferowania zawartości. Ściągające punkty dystrybucji obsługują delty poziomie plików, przesyłania nowych plików, ale nie bloków pliku.

Aplikacje zawsze korzystają z binarnej replikacji różnicowej. W przypadku pakietów binarna replikacja różnicowa jest opcjonalna i nie jest włączona domyślnie. Aby korzystać z binarnej replikacji różnicowej dla pakietów, należy włączyć tę funkcję dla każdego z nich. Aby to zrobić, wybierz opcję **Włącz binarną replikację różnicową** podczas tworzenia nowego pakietu lub edytowania zawartości na karcie **Źródło danych** właściwości pakietu.  

## <a name="branchcache"></a>Usługa BranchCache  
 Technologia systemu Windows, która umożliwia klientom obsługującym usługę BranchCache i dysponującym pobranym wdrożeniem skonfigurowanym do pamięci podręcznej gałęzi pełnienie roli źródła zawartości dla innych klientów obsługujących usługę BranchCache.  

 Przykładowo kiedy pierwszy komputer kliencki z usługą BranchCache zażąda zawartości z punktu dystrybucji z uruchomionym systemem Windows Server 2012, który został skonfigurowany jako serwer usługi BranchCache, komputer kliencki pobierze zawartość i umieści ją w pamięci podręcznej.  

-   Temu komputerowi klienckiemu można następnie udostępnić zawartość dla dodatkowych włączona usługa BranchCache klientów w tej samej podsieci, które również buforują zawartość.  

-   Dzięki temu kolejni klienci w tej samej podsieci nie będą musieli pobierać zawartości z punktu dystrybucji, a zawartość będzie rozmieszczona na wielu klientach na potrzeby przyszłych transferów.  

## <a name="peer-cache"></a>Równorzędna pamięć podręczna
Począwszy od wersji 1610 buforowania równorzędnego klientów ułatwia zarządzanie wdrażaniem zawartości dla klientów w lokalizacjach zdalnych. Równorzędna pamięć podręczna jest wbudowanego rozwiązania programu Configuration Manager, która umożliwia klientom na współużytkowanie zawartości z innymi klientami bezpośrednio z lokalnej pamięci podręcznej.

Po wdrożeniu ustawień klienta umożliwiających Buforowanie równorzędne kolekcji elementy członkowskie tej kolekcji może działać jako źródło zawartości elementu równorzędnego dla innych klientów w tej samej grupy granic.

Aby uzyskać więcej informacji, zobacz [buforowania równorzędnego klientów programu Configuration Manager](/sccm/core/plan-design/hierarchy/client-peer-cache).


## <a name="windows-pe-peer-cache"></a>Równorzędna pamięć podręczna systemu Windows PE
Podczas wdrażania nowego systemu operacyjnego w programie System Center Configuration Manager, komputery z systemem sekwencji zadań można użyć równorzędnej pamięci podręcznej systemu Windows PE pobierać zawartość z lokalnego elementu równorzędnego (źródła równorzędnej pamięci podręcznej) zamiast z punktu dystrybucji. Minimalizuje to ruch w sieci rozległej w scenariuszach oddziału firmy bez lokalnego punktu dystrybucji.

Aby uzyskać więcej informacji, zobacz [równorzędnej pamięci podręcznej systemu Windows PE](../../../osd/get-started/prepare-windows-pe-peer-cache-to-reduce-wan-traffic.md).


## <a name="client-locations"></a>Lokalizacje klientów  
 Poniżej przedstawiono lokalizacje, z których klienci uzyskują dostęp do zawartości:  

-   **Intranet** (lokalnie):  

    -   Punkty dystrybucji mogą używać protokołu HTTP lub HTTPs.  

    -   Używać tylko punkt dystrybucji w chmurze jako metody rezerwowej, gdy lokalne punkty dystrybucji nie są dostępne.  

-   **Internet**:  

    -   Wymaga od punktów dystrybucji akceptowania protokołu HTTPS.  

    -   Mogą używać punktu dystrybucji w chmurze jako metody rezerwowej.  

-   **Grupa robocza**:  

    -   Wymaga od punktów dystrybucji akceptowania protokołu HTTPS.  

    -   Mogą używać punktu dystrybucji w chmurze jako metody rezerwowej.  



## <a name="content-library"></a>Biblioteka zawartości  
 Biblioteka zawartości to Magazyn jednego wystąpienia zawartości, która korzysta z programu Configuration Manager do redukowania łącznego rozmiaru połączonej treści zawartości, którą można dystrybuować.  

- Dowiedz się więcej o [biblioteki zawartości](../../../core/plan-design/hierarchy/the-content-library.md).
- Użyj [narzędzia do oczyszczania biblioteki zawartości](/sccm/core/plan-design/hierarchy/content-library-cleanup-tool) usunąć zawartość, która nie jest już skojarzona z aplikacją.  


## <a name="distribution-points"></a>Punkty dystrybucji  
 Configuration Manager używa punktów dystrybucji do przechowywania plików, które są wymagane do działania oprogramowania na komputerach klienckich. Klienci muszą mieć dostęp do co najmniej jednego punktu dystrybucji z którego mogą pobierać pliki zawartości, którą można wdrożyć.  

 Punkt dystrybucji (niewyspecjalizowany) podstawowa jest często określana jako standardowego punktu dystrybucji. Istnieją dwie odmiany standardowego punktu dystrybucji, które wymagają specjalnej uwagi:  

-   **Ściągający punkt dystrybucji**: Odmiana punktu dystrybucji, w której punkt dystrybucji uzyskuje zawartość z innego punktu dystrybucji (źródłowego punktu dystrybucji). Ten proces jest podobny jak klienci pobierają zawartość z punktów dystrybucji. Ściągające punkty dystrybucji mogą pomóc uniknąć wąskich gardeł przepustowości sieci, które wystąpić, gdy serwer lokacji musi rozsyłać zawartość bezpośrednio do poszczególnych punktów dystrybucji.  [Użyj punktu dystrybucji ściągania w programie System Center Configuration Manager](/sccm/core/plan-design/hierarchy/use-a-pull-distribution-point).

-   **Punkt dystrybucji w chmurze**: Odmiana punktu dystrybucji zainstalowanego w systemie Microsoft Azure. [Używanie punktu dystrybucji w chmurze w programie System Center Configuration Manager](../../../core/plan-design/hierarchy/use-a-cloud-based-distribution-point.md).  


Standardowe punkty dystrybucji obsługują szereg konfiguracje i funkcje, takie jak ograniczania przepustowości i Planowanie środowiska PXE i multiemisji, lub wstępnie przygotowanej zawartości.  

-   Można używać formantów, takich jak **harmonogramy** lub **przepustowości** ułatwiające kontrolę to przeniesienie.  

-   Można również użyć innych opcji, w tym **wstępnie przygotowanej zawartości**, i **ściągające punkty dystrybucji**. Ponadto można wykorzystać **usługi BranchCache** do zmniejszenia przepustowości sieci, który jest używany podczas wdrażania zawartości.  

-   Punkty dystrybucji obsługują różne konfiguracje  **[PXE](../../../osd/get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_PXEDistributionPoint)**  i  **[multiemisji](../../../osd/get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_DPMulticast)**  dla wdrożeń systemów operacyjnych oraz konfiguracje obsługujące **urządzeń przenośnych**.  

 Oparte na chmurze i ściągające punkty dystrybucji obsługują wiele podobnych konfiguracji, ale mają ograniczenia, które są specyficzne dla poszczególnych odmian punktów dystrybucji.  

## <a name="distribution-point-groups"></a>Grupy punktów dystrybucji  
 Grupy punktów dystrybucji są logiczne grupowanie punktów dystrybucji, które może uprościć dystrybucję zawartości.  

 Aby uzyskać więcej informacji, zobacz [Zarządzanie grupami punktów dystrybucji](../../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_manage).

## <a name="distribution-point-priority"></a>Priorytet punktu dystrybucji  
 Wartość priorytetu punktu dystrybucji jest zależna od czasu, który zajęło przesłanie wcześniejszych wdrożeń do tego punktu dystrybucji.  

-   Jest to dostrajana automatycznie wartość przypisana do punktu dystrybucji, który pomaga programu Configuration Manager transferu zawartości do większej liczby punktów dystrybucji w krótszym czasie.  

-   Podczas dystrybucji zawartości do wielu punktów dystrybucji, w tym samym czasie lub dystrybucji grupy punktów, programu Configuration Manager wysyła zawartość do punktu dystrybucji o najwyższym priorytecie przed wysłaniem tej samej zawartości do punktu dystrybucji z niższym priorytetem.  

-   Nie zastępuje priorytetu dystrybucji dla pakietów, który pozostaje decydującym czynnikiem w sekwencji podczas transferu poszczególnych dystrybucji.  


Na przykład jeśli dystrybucji zawartości o wysokim priorytecie dystrybucji do punktu dystrybucji o niskim priorytecie, ten pakiet priorytet Wysoki dystrybucji zawsze zostanie przetransferowany przed pakietem o niższym priorytecie dystrybucji. Priorytet dystrybucji ma zastosowanie, nawet jeśli pakiety o niższym priorytecie dystrybucji są dystrybuowane do punktów dystrybucji o wyższych priorytetach punktu dystrybucji.

Wysoki priorytet dystrybucji pakietu gwarantuje, że Configuration Manager dystrybuuje zawartość do odpowiednich punktów dystrybucji przed wysłaniem jakichkolwiek pakietów o niższym priorytecie dystrybucji.  

> [!NOTE]  
>  Ściągające punkty dystrybucji korzystają również z priorytetów w celu ustalenia sekwencji źródłowych punktów dystrybucji.  
>   
>  -   Priorytet punktów dystrybucji dla transferów zawartości do punktu dystrybucji jest inny niż priorytet stosowany przez ściągające punkty dystrybucji podczas wyszukiwania zawartości ze źródłowego punktu dystrybucji.  
>  -   Aby uzyskać więcej informacji, zobacz [użyć punktu dystrybucji ściągania w programie System Center Configuration Manager](/sccm/core/plan-design/hierarchy/use-a-pull-distribution-point).  


## <a name="fallback"></a>Opcja rezerwowa  
 Począwszy od wersji 1610 kilka kwestii zostały zmienione w taki sposób, że klienci znaleźć punktu dystrybucji z zawartością, włączając powrotu. Skorzystaj z poniższych informacji, która ma zastosowanie do używanej wersji:

**Wersja 1610 i nowsze**   
Klienci, których nie można odnaleźć zawartości z punktu dystrybucji, który został skojarzony z grupą granic, ich bieżący mogą wrócić do używania lokalizacji źródła zawartości, które są skojarzone z grupami granic sąsiedniego. Mają być używane jako metody rezerwowej, grupą granic sąsiada musi mieć zdefiniowanych relacji z grupą granic bieżącego klienta. Ta relacja zawiera skonfigurowany czas, który musi upłynąć przed klienta, który nie może znaleźć zawartość lokalnie może zawierać źródła zawartości z grupą granic sąsiada jako część wyszukiwanie.

Pojęcia związane z dystrybucji punktów nie są już używane i ustawień **Zezwalaj lokalizacji rezerwowej dla zawartości** nie są już dostępne lub wymuszone.

Aby uzyskać więcej informacji, zobacz [grup granic](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups).


**Wersja 1511, 1602 i 1606**   
Ustawienia opcji rezerwowych są powiązane z wykorzystaniem **preferowanych punktów dystrybucji** oraz do lokalizacji źródła zawartości, które są używane przez klientów.

-   Domyślnie klienci pobierają zawartość tylko z preferowanego punktu dystrybucji (skojarzonego z grupami granicy klienta).  

-   Jednak jeśli dla punktu dystrybucji skonfigurowano opcję **Zezwalaj klientom na stosowanie tego systemu lokacji jako rezerwowej lokalizacji źródłowej dla zawartości**, ten punkt dystrybucji jest oferowany jako poprawne źródło zawartości tylko tym klientom, którzy nie mogą uzyskać wdrożenia z żadnego z preferowanych punktów dystrybucji.  


Aby uzyskać informacje o różnych lokalizacji zawartości i scenariuszy rezerwowych, zobacz [scenariusze lokalizacji źródła zawartości](../../../core/plan-design/hierarchy/content-source-location-scenarios.md). Aby uzyskać informacje o grupach granic, zobacz [grup granic dla wersji 1511,1602 i 1606](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606).

## <a name="network-bandwidth"></a>Przepustowość sieci  
 Aby ułatwić zarządzanie ilość przepustowości sieci, który jest używany podczas dystrybucji zawartości, można użyć następujących opcji:  

-   **Wstępnie przygotowanej zawartości**:  Proces przesyłania zawartości do punktu dystrybucji bez polegania na programu Configuration Manager do dystrybucji zawartości w sieci.  

-   **Planowania i ograniczania przepustowości**: Konfiguracje, które pomagają kontrolować czas i sposób dystrybucji zawartości do punktów dystrybucji.  

Aby uzyskać więcej informacji, zobacz [zarządzanie przepustowością sieci](/sccm/core/plan-design/hierarchy/manage-network-bandwidth).

## <a name="network-connection-speed-to-content-source"></a>Szybkość połączenia sieciowego ze źródłem zawartości  
Począwszy od wersji 1610 kilka kwestii zostały zmienione w taki sposób, że klienci znaleźć punktu dystrybucji, które ma zawartość, w tym szybkość połączenia sieciowego do źródła zawartości. Skorzystaj z poniższych informacji, która ma zastosowanie do używanej wersji:

**Wersja 1610 i nowsze**   
Szybkość połączenia sieciowego definiujące dystrybucji punktu jako **Fast** lub **wolno** nie są już używane. Zamiast tego jest traktowany każdego systemu lokacji, która jest skojarzona z grupą granic takie same.

Aby uzyskać więcej informacji, zobacz [grup granic](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups).


**Wersja 1511, 1602 i 1606**   
 Istnieje możliwość skonfigurowania szybkości połączenia sieciowego każdego punktu dystrybucji w grupie granic:  

-   Klienci używają tej wartości, gdy łączą się z punktem dystrybucji.

-   Domyślnie szybkość połączenia sieciowego jest skonfigurowana jako **Fast**, ale można ją również ustawić jako **wolno**.  

-   **Szybkość połączenia sieciowego**, wraz z konfiguracji wdrożenia, należy określić, jeśli klient może pobierać zawartość z punktu dystrybucji zostanie skojarzona grupa granic  

Aby uzyskać informacje o różnych lokalizacji zawartości i scenariuszy rezerwowych, zobacz [scenariusze lokalizacji źródła zawartości](../../../core/plan-design/hierarchy/content-source-location-scenarios.md). Aby uzyskać informacje o grupach granic, zobacz [grup granic dla wersji 1511,1602 i 1606](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606).

## <a name="on-demand-content-distribution"></a>Dystrybucja zawartości na żądanie  
 Dystrybucja zawartości na żądanie to opcja można ustawić dla poszczególnych aplikacji i pakietów (wdrożeń), aby włączyć na żądanie dystrybucję do preferowanych punktów dystrybucji zawartości.  

-   Aby włączyć tę opcję dla wdrożenia, Włącz **Dystrybuuj zawartość tego pakietu do preferowanych punktów dystrybucji**.  

-   Gdy ta opcja jest włączona dla wdrożenia i klient próbuje zażądać tej zawartości, ale zawartość nie jest dostępna w żadnym z punktów dystrybucji klienta, program Configuration Manager automatycznie dystrybuuje zawartość do punktów dystrybucji klienta.  

-   Mimo że powoduje automatyczną dystrybucję zawartości do tego klienta preferowanych punktów dystrybucji program Configuration Manager, klient może uzyskać tę zawartość z innych punktów dystrybucji przed preferowanych punktów dystrybucji klienta otrzymaniem wdrożenia. W takim przypadku zawartość będzie dostępny w tym punkcie dystrybucji do użytku przez następnego klienta poszukującego tego wdrożenia.  

Jeśli używasz wersji 1610 lub nowszej, zobacz [grup granic](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups).
Jeśli używasz wersji 1511, 1602 lub 1606 zobacz [scenariusze lokalizacji źródła zawartości](../../../core/plan-design/hierarchy/content-source-location-scenarios.md) informacji o różnych lokalizacji zawartości i scenariuszy rezerwowych.  



## <a name="package-transfer-manager"></a>Menedżer transferu pakietów  
 Menedżer transferu pakietów jest składnika serwera lokacji, który przesyła zawartość do punktów dystrybucji na innych komputerach.  

 Dowiedz się więcej o [Menedżer transferu pakietów](../../../core/plan-design/hierarchy/package-transfer-manager.md).  

## <a name="preferred-distribution-point"></a>Preferowany punkt dystrybucji  
 Preferowany punkt dystrybucji zawiera punkty dystrybucji, które są skojarzone z bieżącymi grupami granic klienta.  

 Istnieje możliwość skojarzenia każdego punktu dystrybucji z jedną lub większą liczbą grup granic:  

-   To skojarzenie ułatwia klientowi identyfikację punktów dystrybucji, z których mogą pobierać zawartość.  
-   Domyślnie klienci mogą pobierać zawartość tylko z preferowanego punktu dystrybucji.  


Aby uzyskać więcej informacji:
 - Jeśli używasz wersji 1610 lub nowszej, zobacz [grup granic](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups).
 - Jeśli używasz wersji 1511, 1602 lub 1606 zobacz [scenariusze lokalizacji źródła zawartości](../../../core/plan-design/hierarchy/content-source-location-scenarios.md).

## <a name="prestage-content"></a>Wstępne przygotowanie zawartości  
 Wstępne przygotowanie zawartości jest proces przesyłania zawartości do punktu dystrybucji bez polegania na programu Configuration Manager do dystrybucji zawartości w sieci.  

 Aby uzyskać więcej informacji, zobacz [zarządzanie przepustowością sieci](/sccm/core/plan-design/hierarchy/manage-network-bandwidth).
