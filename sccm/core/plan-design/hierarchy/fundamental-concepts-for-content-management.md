---
title: Podstawowe informacje na temat zarządzania zawartością
titleSuffix: Configuration Manager
description: Użyj narzędzi i opcji w programie Configuration Manager do zarządzania zawartością, którą można wdrożyć.
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: c201be2a-692c-4d67-ac95-0a3afa5320fe
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 5dfe33e7182eae158c15afb848d3a9f1702678ba
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="fundamental-concepts-for-content-management-in-system-center-configuration-manager"></a>Podstawowe pojęcia związane z zarządzaniem zawartością w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Program Configuration Manager obsługuje niezawodny system narzędzi i opcji do zarządzania zawartością wdrażaną jako aplikacje, pakiety, aktualizacje oprogramowania i wdrożenia systemu operacyjnego. Program Configuration Manager przechowuje zawartości na serwerach lokacji i punktów dystrybucji. Ta zawartość wymaga dużą ilość przepustowości, gdy są przesyłane między lokalizacjami. Efektywne planowanie i wykorzystanie infrastruktury zarządzania zawartością, firma Microsoft zaleca, że rozumiesz, dostępne opcje oraz konfiguracje. Należy rozważyć sposób ich użycia w celu optymalnego dopasowania Twoich potrzeb dotyczących wdrażania zawartości i środowiska sieciowego.  

> [!TIP]    
> Aby uzyskać więcej informacji na temat procesu dystrybucji zawartości, a także znalezienia pomocy diagnozowanie i rozwiązywanie problemów z ogólne dystrybucji zawartości, zobacz [zrozumienie i rozwiązywanie problemów z dystrybucji zawartości programu Microsoft Configuration Manager ](https://support.microsoft.com/help/4000401/content-distribution-in-mcm).

Podstawowe pojęcia związane z zarządzaniem zawartością są następujące tematy. W przypadku pojęć wymagających dodatkowych lub złożonych informacji podano linki kierujące do szczegółów.



## <a name="accounts-used-for-content-management"></a>Konta używane do zarządzania zawartością  
 Do zarządzania zawartością można stosować następujące konta:  

-   **Konto dostępu do sieci**: Używany przez klientów, aby podłączyć się do punktu dystrybucji i uzyskiwać dostęp do zawartości. Domyślnie konto komputera jest wybrany jako pierwszy.  

     To konto jest również używane przez ściągające punkty dystrybucji do pobrania zawartości ze źródłowego punktu dystrybucji w lesie zdalnym.  

-   **Konto dostępu do pakietu**: Domyślnie program Configuration Manager udziela dostępu do zawartości w punkcie dystrybucji dla ogólnych kont dostępu użytkowników i administratorów. Można jednak skonfigurować dodatkowe uprawnienia, aby ograniczyć dostęp.   

-   **Konto połączenia multiemisji**: Używany we wdrożeniach systemu operacyjnego.  

Aby uzyskać więcej informacji o tych kont, zobacz [Zarządzanie kontami dostępu do zawartości](../../../core/plan-design/hierarchy/manage-accounts-to-access-content.md).



## <a name="bandwidth-throttling-and-scheduling"></a>Ograniczenie przepustowości i planowanie  
 Ograniczenie przepustowości i planowanie to opcje ułatwiające kontrolowanie momentu dystrybucji zawartości z serwera lokacji do punktów dystrybucji. Te możliwości są podobne do, ale nie są bezpośrednio powiązane do kontroli przepustowości replikacji plikowej lokacja lokacja.  

 Aby uzyskać więcej informacji, zobacz [zarządzanie przepustowością sieci](/sccm/core/plan-design/hierarchy/manage-network-bandwidth).



## <a name="binary-differential-replication"></a>Binarna replikacja różnicowa  
 Binarna replikacja różnicowa (BDR) jest wymagane w przypadku punktów dystrybucji. Czasami jest znana jako funkcja replikacji różnicowej. Gdy w przypadku dystrybucji aktualizacji zawartości wdrożonej wcześniej do innych lokacji lub do zdalnych punktów dystrybucji, replikacja BDR jest automatycznie używany do zmniejszenia przepustowości.  

 Replikacja BDR minimalizuje użycie przepustowości sieci używanej na wysyłanie aktualizacji treści. Wysyła go ponownie tylko nową lub zmienioną zawartość zamiast przesyłania całego zestawu plików źródłowych zawartości za każdym razem zmiany tych plików.  

 Gdy replikacja BDR jest używany, program Configuration Manager identyfikuje zmiany w plikach źródłowych dla każdego zestawu zawartości, który wcześniej został wysłany.  

-   Po zmianie plików zawartości źródła lokacji tworzy nową przyrostową wersję zestawu zawartości. Następnie replikuje tylko zmienione pliki do lokacji docelowych i punktów dystrybucji. Plik jest uważany za zmieniony, jeśli zmieniono jego nazwę lub go przenieść lub zmienić zawartość pliku. Na przykład jeśli zamienisz pojedynczy plik sterownika dla pakietu sterowników, który wcześniej został wysłany do wielu lokacji są replikowane tylko zmieniony plik sterownika.  

-   Program Configuration Manager obsługuje do pięciu przyrostowych wersji zawartości przed jego przesłania całego zestawu zawartości. Po piątej aktualizacji kolejna zmiana zestawu zawartości powoduje, że witryny utworzyć nową wersję zestawu zawartości. Menedżer konfiguracji następnie dystrybuuje nową wersję zestawu w celu zastąpienia poprzedniego zestawu i wszystkich jego przyrostowych wersji zawartości. Po wysłaniu nowego zestawu zawartości kolejne zmiany przyrostowe plików źródłowych są ponownie replikowane replikacja BDR.  

Replikacja BDR jest obsługiwana między poszczególnymi lokacjami nadrzędnymi i podrzędnymi w hierarchii. Replikacja BDR jest obsługiwana w ramach lokacji między serwerem lokacji a jego punktami dystrybucji regularne. Ściągające punkty dystrybucji i punkty dystrybucji w chmurze nie obsługuje jednak replikacja BDR do transferu zawartości. Ściągające punkty dystrybucji obsługują delty poziomie plików, przesyłania nowych plików, ale nie bloków pliku.

Aplikacje zawsze korzystają z binarnej replikacji różnicowej. Replikacja BDR jest opcjonalny dla pakietów i nie jest domyślnie włączona. Aby użyć replikacja BDR pakietów, należy włączyć tę funkcję dla każdego pakietu. Wybierz opcję **Włącz binarną replikację różnicową** podczas tworzenia lub edytowania pakietu.   



## <a name="branchcache"></a>Usługa BranchCache  
 [Usługa BranchCache](/windows-server/networking/branchcache/branchcache) to technologia systemu Windows. Klienci, którzy obsługują usługę BranchCache i dysponującym pobranym wdrożeniem skonfigurowanym dla pamięci podręcznej gałęzi, pełnienie roli źródła zawartości dla innych klientów obsługujących usługę BranchCache.  

 Na przykład masz punktu dystrybucji z systemem Windows Server 2012 lub nowszym, a jest skonfigurowana jako serwer usługi BranchCache. Gdy pierwszy klient z włączoną usługą BranchCache zażąda zawartości z tego serwera, klient pobierze zawartość i buforuje ją.  

- Klient następnie udostępnia zawartość dla dodatkowych włączona usługa BranchCache klientów w tej samej podsieci, które również buforują zawartość.  
- Innym klientom w tej samej podsieci, nie trzeba pobierać zawartość z punktu dystrybucji.  
- Zawartość będzie rozmieszczona na wielu klientach na potrzeby przyszłych transferów.  



## <a name="delivery-optimization"></a>Optymalizacja dostarczania
<!-- 1324696 -->
Grupy granic w programie Configuration Manager służy do definiowania i uregulowanie dystrybucji zawartości w sieci firmowej i biurach zdalnych. [Optymalizacja dostarczania Windows](/windows/deployment/update/waas-delivery-optimization) jest oparta na chmurze, peer-to-peer technologii do udostępniania zawartości między urządzeniami z systemem Windows 10. Począwszy od wersji 1802 Konfigurowanie optymalizacji dostarczania do grup granic udostępniania zawartości między elementami równorzędnymi. Ustawienia klienta stosowane identyfikator grupy granic jako identyfikator grupy optymalizacji dostarczania na kliencie. Gdy klient komunikuje się z usługą w chmurze optymalizacji dostarczania, używa tego identyfikatora można zlokalizować elementów równorzędnych o żądanej zawartości. Aby uzyskać więcej informacji, zobacz [optymalizacji dostarczania](/sccm/core/clients/deploy/about-client-settings#delivery-optimization) ustawień klienta.



## <a name="peer-cache"></a>Równorzędna pamięć podręczna
Klient równorzędnej pamięci podręcznej pomaga w zarządzaniu wdrażaniem zawartości dla klientów w lokalizacjach zdalnych. Równorzędna pamięć podręczna jest wbudowanego rozwiązania programu Configuration Manager, która umożliwia klientom na współużytkowanie zawartości z innymi klientami bezpośrednio z lokalnej pamięci podręcznej.

Po wdrożeniu ustawień klienta, umożliwiających Buforowanie równorzędne kolekcji elementy członkowskie tej kolekcji może działać jako źródło zawartości równorzędnej dla innych klientów w tej samej grupy granic.

Aby uzyskać więcej informacji, zobacz [buforowania równorzędnego klientów programu Configuration Manager](/sccm/core/plan-design/hierarchy/client-peer-cache).



## <a name="windows-pe-peer-cache"></a>Równorzędna pamięć podręczna systemu Windows PE
Podczas wdrażania nowego systemu operacyjnego z programem Configuration Manager, komputerach sekwencji zadań można użyć buforowania równorzędnego środowiska Windows PE. Będą oni mogli pobrać zawartość ze źródła równorzędnej pamięci podręcznej zamiast z punktu dystrybucji. To zachowanie minimalizuje WAN ruchu w scenariuszach oddziału firmy w przypadku braku lokalnego punktu dystrybucji.

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
 Biblioteka zawartości to Magazyn jednego wystąpienia zawartości w programie Configuration Manager. Ta biblioteka zmniejsza całkowity rozmiar zawartości, którą można dystrybuować.  

- Dowiedz się więcej o [biblioteki zawartości](../../../core/plan-design/hierarchy/the-content-library.md).
- Użyj [narzędzia do oczyszczania biblioteki zawartości](/sccm/core/plan-design/hierarchy/content-library-cleanup-tool) usunąć zawartość, która nie jest już skojarzona z aplikacją.  



## <a name="distribution-points"></a>Punkty dystrybucji  
 Configuration Manager używa punktów dystrybucji do przechowywania plików, które są wymagane do działania oprogramowania na komputerach klienckich. Klienci muszą mieć dostęp do co najmniej jednego punktu dystrybucji z którego mogą pobierać pliki zawartości, którą można wdrożyć.  

 Punkt dystrybucji (niewyspecjalizowany) podstawowa jest często określana jako standardowego punktu dystrybucji. Istnieją dwie odmiany standardowego punktu dystrybucji, które wymagają specjalnej uwagi:  

-   **Ściągający punkt dystrybucji**: Odmiana punktu dystrybucji, w której punkt dystrybucji uzyskuje zawartość z innego punktu dystrybucji (źródłowego punktu dystrybucji). Ten proces jest podobny jak klienci pobierają zawartość z punktów dystrybucji. Ściągające punkty dystrybucji mogą pomóc uniknąć wąskich gardeł przepustowości sieci, które wystąpić, gdy serwer lokacji musi rozsyłać zawartość bezpośrednio do poszczególnych punktów dystrybucji. [Używanie punktu dystrybucji ściągania](/sccm/core/plan-design/hierarchy/use-a-pull-distribution-point).

-   **Punkt dystrybucji w chmurze**: Odmiana punktu dystrybucji zainstalowanego w systemie Microsoft Azure. [Dowiedz się, jak używać punktu dystrybucji w chmurze](../../../core/plan-design/hierarchy/use-a-cloud-based-distribution-point.md).  


Standardowe punkty dystrybucji obsługują szereg konfiguracje i funkcje:  

- Używanie formantów, takiej jak **harmonogramy** lub **przepustowości** ułatwiające kontrolę to przeniesienie.  
- Użyj innych opcji, w tym **wstępnie przygotowanej zawartości**, i **ściągające punkty dystrybucji** zminimalizowanie i kontrolowania użycia sieci. 
- **Usługa BranchCache**, **elementu równorzędnego pamięci podręcznej**, i **optymalizacji dostarczania** przedstawiono technologie peer-to-peer do zmniejszenia przepustowości sieci, który jest używany podczas wdrażania zawartości.  
- Istnieją różne konfiguracje wdrożeń systemu operacyjnego, takie jak **[PXE](../../../osd/get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_PXEDistributionPoint)** i  **[multiemisji](../../../osd/get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_DPMulticast)**
- Opcje dla **urządzeń przenośnych**   
  
  
Oparte na chmurze i ściągające punkty dystrybucji obsługują wiele podobnych konfiguracji, ale mają ograniczenia, które są specyficzne dla poszczególnych odmian punktów dystrybucji.  



## <a name="distribution-point-groups"></a>Grupy punktów dystrybucji  
 Grupy punktów dystrybucji są logiczne grupowanie punktów dystrybucji, które może uprościć dystrybucję zawartości.  

 Aby uzyskać więcej informacji, zobacz [Zarządzanie grupami punktów dystrybucji](../../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_manage).



## <a name="distribution-point-priority"></a>Priorytet punktu dystrybucji  
 Wartość priorytetu punktu dystrybucji jest zależna od czasu, który zajęło przesłanie wcześniejszych wdrożeń do tego punktu dystrybucji.  

-   Ta wartość jest automatycznie. Aby ułatwić programu Configuration Manager więcej szybko transferu zawartości do większej liczby punktów dystrybucji jest ustawiona w każdym punkcie dystrybucji.  

-   Podczas dystrybucji zawartości do wielu punktów dystrybucji, w tym samym czasie lub do grupy punktów dystrybucji lokacji najpierw wysyła zawartość do serwera o najwyższym priorytecie. Następnie wysyła tę samą zawartość do punktu dystrybucji z niższym priorytetem.  

-   Priorytet punktu dystrybucji nie zastępuje priorytetu dystrybucji dla pakietów. Priorytet pakietu pozostaje decydującym czynnikiem programu, gdy lokacji wysyła innej zawartości.  

Na przykład masz pakiet, który ma pakiet wysoki priorytet. Rozpowszechnienie go do serwera o niskim priorytecie. Ten pakiet wysoki priorytet zawsze zostanie przetransferowany przed pakietem o niższym priorytecie. Priorytet pakietu ma zastosowanie, nawet jeśli lokacji dystrybuuje niższy priorytet pakietów na serwerach o wyższych priorytetach punktu dystrybucji.

Wysoki priorytet pakietu zapewnia Configuration Manager dystrybuuje zawartość do punktów dystrybucji przed wysłaniem jakichkolwiek pakietów o niższym priorytecie.  

> [!NOTE]  
>  Ściągające punkty dystrybucji korzystają również z priorytetów w celu ustalenia sekwencji źródłowych punktów dystrybucji.  
>   
>  -   Priorytet punktów dystrybucji dla transferów zawartości na serwerze jest inny niż priorytet stosowany przez ściągające punkty dystrybucji. Ściągające punkty dystrybucji przy użyciu ich priorytetu podczas wyszukiwania zawartości ze źródłowego punktu dystrybucji.  
>  -   Aby uzyskać więcej informacji, zobacz [użycia punktu dystrybucji ściągania](/sccm/core/plan-design/hierarchy/use-a-pull-distribution-point).  



## <a name="fallback"></a>Opcja rezerwowa  
 Kilka kwestii zostały zmienione z programu Configuration Manager bieżącej gałęzi w taki sposób, że klienci znaleźć punktu dystrybucji z zawartością, włączając powrotu. 

Klienci, których nie można odnaleźć zawartości z punktu dystrybucji, który został skojarzony z grupą granic, ich bieżący wrócić do używania lokalizacji źródła zawartości skojarzone z grupami granic sąsiedniego. Mają być używane jako metody rezerwowej, grupą granic sąsiada musi mieć zdefiniowanych relacji z grupą granic bieżącego klienta. Ta relacja zawiera skonfigurowany czas, jaki musi minąć, zanim klient, który nie może odnaleźć zawartość lokalnie uwzględnia źródła zawartości z grupą granic sąsiada jako część wyszukiwanie.

Pojęcia związane z dystrybucji punktów nie są już używane i ustawień **Zezwalaj lokalizacji rezerwowej dla zawartości** nie są już dostępne lub wymuszone.

Aby uzyskać więcej informacji, zobacz [grup granic](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups).

<!--
**Version 1511, 1602, and 1606**   
Fallback settings are related to the use of **preferred distribution points** and to content source locations that are used by clients.

-   By default, clients only download content from a preferred distribution point (one that is associated with the client's boundary groups).  

-   However, when a distribution point is configured with **Allow clients to use this site system as a fallback source location for content**, that distribution point is only offered as a valid content source to any client that can't get a deployment from one of its preferred distribution points.  

For information about the different content location and fallback scenarios, see [Content source location scenarios](../../../core/plan-design/hierarchy/content-source-location-scenarios.md). For information about boundary groups, see [Boundary groups for versions 1511,1602, and 1606](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606).
-->



## <a name="network-bandwidth"></a>Przepustowość sieci  
 Aby ułatwić zarządzanie ilość przepustowości sieci, który jest używany podczas dystrybucji zawartości, można użyć następujących opcji:  

-   **Wstępnie przygotowanej zawartości**: Przesyłania zawartości do punktu dystrybucji bez dystrybucji zawartości w sieci.  

-   **Planowania i ograniczania przepustowości**: Konfiguracje, które pomagają kontrolować czas i sposób dystrybucji zawartości do punktów dystrybucji.  

Aby uzyskać więcej informacji, zobacz [zarządzanie przepustowością sieci](/sccm/core/plan-design/hierarchy/manage-network-bandwidth).



## <a name="network-connection-speed-to-content-source"></a>Szybkość połączenia sieciowego ze źródłem zawartości  
 Kilka kwestii zostały zmienione z programu Configuration Manager bieżącej gałęzi w taki sposób, że klienci znaleźć punktu dystrybucji z zawartością. Te zmiany to między innymi szybkość sieci do źródła zawartości. 

Szybkość połączenia sieciowego definiujące dystrybucji punktu jako **Fast** lub **wolno** nie są już używane. Zamiast tego jest traktowany każdego systemu lokacji, która jest skojarzona z grupą granic takie same.

Aby uzyskać więcej informacji, zobacz [grup granic](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups).

<!--
**Version 1511, 1602, and 1606**   
 You can configure the network connection speed of each distribution point in a boundary group:  

-   Clients use this value when they connect to the distribution point.

-   By default, the network connection speed is configured as **Fast**, but it can also be set as **Slow**.  

-   The **network connection speed**, along with the configuration of a deployment, determine if a client can download content from a distribution point when the client is in an associated boundary group  

For information about the different content location and fallback scenarios, see [Content source location scenarios](../../../core/plan-design/hierarchy/content-source-location-scenarios.md). For information about boundary groups, see [Boundary groups for versions 1511,1602, and 1606](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606).
-->



## <a name="on-demand-content-distribution"></a>Dystrybucja zawartości na żądanie  
 Dystrybucja zawartości na żądanie jest opcją w przypadku poszczególnych wdrożeń aplikacji i pakietów. Ta opcja umożliwia dystrybucję zawartości na żądanie do preferowanych serwerów.  

-   Aby włączyć to ustawienie wdrożenia, należy włączyć: **Dystrybuuj zawartość tego pakietu do preferowanych punktów dystrybucji**.  

-   Gdy ta opcja jest włączona dla wdrożenia i klient próbuje zażądać tej zawartości, ale zawartość nie jest dostępna w żadnym z punktów dystrybucji klienta, program Configuration Manager automatycznie dystrybuuje zawartość do punktów dystrybucji klienta.  

-   Mimo że powoduje automatyczną dystrybucję zawartości do tego klienta preferowanych punktów dystrybucji program Configuration Manager, klient może uzyskać tę zawartość z innych punktów dystrybucji przed preferowanych punktów dystrybucji klienta otrzymaniem wdrożenia. W takiej sytuacji zawartości będzie dostępny w tym punkcie dystrybucji do użytku przez następnego klienta poszukującego tego wdrożenia.  

Aby uzyskać więcej informacji, zobacz [grup granic](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups).

<!--
If you use version 1511, 1602, or 1606, see  [Content source location scenarios](../../../core/plan-design/hierarchy/content-source-location-scenarios.md) for information about the different content location and fallback scenarios.
-->



## <a name="package-transfer-manager"></a>Menedżer transferu pakietów  
 Menedżer transferu pakietów jest składnika serwera lokacji, który przesyła zawartość do punktów dystrybucji na innych komputerach.  

 Aby uzyskać więcej informacji, zobacz [Menedżer transferu pakietów](../../../core/plan-design/hierarchy/package-transfer-manager.md).  



<!--
## Preferred distribution point  
 A preferred distribution point includes any distribution points that are associated with a client's current boundary groups.  

 You have the option to associate each distribution point with one or more boundary groups:  

-   This association helps the client identify distribution points from which it can download content.  
-   By default, clients can only download content from a preferred distribution point.  


For more information:
 - If you use version 1610 or later, see [Boundary groups](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups).
 - If you use version 1511, 1602, or 1606, see [Content source location scenarios](../../../core/plan-design/hierarchy/content-source-location-scenarios.md).
-->



## <a name="prestage-content"></a>Wstępne przygotowanie zawartości  
 Wstępne przygotowanie zawartości jest proces przesyłania zawartości do punktu dystrybucji bez dystrybucji zawartości w sieci.  

 Aby uzyskać więcej informacji, zobacz [zarządzanie przepustowością sieci](/sccm/core/plan-design/hierarchy/manage-network-bandwidth).
