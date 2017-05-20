---
title: "Menedżer konfiguracji Azure | Dokumentacja firmy Microsoft"
description: "Informacje dotyczące korzystania z programu Configuration Manager w środowisku platformy Azure."
ms.custom: na
ms.date: 03/27/2017
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.topic: article
ms.assetid: d24257d8-8136-47f4-8e0d-34021356dc37
caps.latest.revision: 2
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 5276ad999fc871496d79e6efff34d5edc6335380
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="configuration-manager-on-azure---frequently-asked-questions"></a>Program Configuration Manager na platformie Azure — często zadawane pytania
*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Następujące pytania i odpowiedzi można łatwiej zrozumieć, kiedy należy używać i konfigurowanie programu Configuration Manager w programie Microsoft Azure.

## <a name="general-questions"></a>Pytania ogólne
### <a name="my-company-is-trying-to-move-as-many-physical-servers-as-possible-to-microsoft-azure-can-i-move-configuration-manager-servers-to-azure"></a>Moja firma próbuje przenieść zgodnie z wielu serwerów fizycznych, jak to możliwe do systemu Microsoft Azure można przenieść serwerów programu Configuration Manager Azure?
Oczywiście jest to obsługiwany scenariusz.  Zobacz [obsługę w środowiskach wirtualizacji dla programu System Center Configuration Manager](/sccm/core/plan-design/configs/support-for-virtualization-environments).

### <a name="great-my-environment-requires-multiple-sites-should-all-child-primary-sites-be-in-azure-with-the-central-administration-site-or-on-premises-what-about-secondary-sites"></a>Wspaniałe! Moje środowisko wymaga wielu lokacji. Wszystkie podrzędne Lokacje główne należy w Azure z centralnej lokacji administracyjnej lub lokalnie? Informacje o lokacjach dodatkowych?
Komunikacja lokacja lokacja (oparte na plikach i replikacji bazy danych) korzysta z blisko jest obsługiwana w systemie Azure. Jednak ruch będzie zdalnie z serwerami lokacji a systemami lokacji związane z wszystkich klientów. Jeśli używasz sieci szybkie i niezawodne połączenie między Azure i z siecią intranet z planem danych bez ograniczeń, hosting infrastruktury w usłudze Azure jest opcją.

Jednak jeżeli używanie planów danych pomiarów i dostępną przepustowość lub koszt jest istotny lub połączenie sieciowe między Azure i sieci intranet nie jest szybka lub mogą być zawodne, należy rozważyć umieszczenie określonych witryn (i systemy lokacji) lokalnie, a następnie użyć kontroli przepustowości, utworzone w programie Configuration Manager.

### <a name="is-having-configuration-manager-in-azure-a-saas-scenario-software-as-a-service"></a>Musi istnieć programu Configuration Manager w usłudze Azure scenariusz SaaS (oprogramowanie jako usługa)?
Nie, jest IaaS (infrastruktura jako usługa), ponieważ hostów serwerów infrastruktury programu Configuration Manager w maszynach wirtualnych platformy Azure.

### <a name="what-areas-should-i-pay-attention-to-when-considering-a-move-of-my-configuration-manager-infrastructure-to-azure"></a>Obszary powinien I zwrócić uwagę podczas wybierania przeniesienia Moje infrastruktury programu Configuration Manager na platformie Azure?
Doskonałe pytanie, Oto obszary, które są najważniejsze podczas podejmowania decyzji tego, każdy jest omówione zostały w oddzielnej części tego tematu:
1.    Obsługa sieci
2.    Dostępność
3.    Wydajność
4.    Koszt
5.    Środowisko użytkownika

## <a name="networking"></a>Obsługa sieci
### <a name="what-about-networking-requirements-should-i-use-expressroute-or-an-azure-vpn-gateway"></a>Informacje o sieci wymagania, należy użyć ExpressRoute lub bramy sieci VPN Azure?
Sieć jest bardzo ważne. Szybkość sieci i czas oczekiwania może mieć wpływ na funkcjonalność między serwerem lokacji i zdalne systemy lokacji i wszelkich komunikacji klienta z systemami lokacji. Nasze zalecenie, jest użycie ExpressRoute. Ale nie bez ograniczeń programu Configuration Manager, aby uniemożliwić korzystanie z bramą VPN Azure. Powinien jest dokładne zapoznanie się z wymaganiami (wydajności, poprawki, dystrybucji oprogramowania, wdrażaniem systemu operacyjnego) z tej infrastruktury, a następnie wprowadź decyzji. Czynniki należy rozważyć dla każdego rozwiązania obejmują:

 - **ExpressRoute** (zalecane)
  - Naturalne rozszerzenie do centrum danych (może powiązać ze sobą wiele centrów danych)
  - Prywatne połączenia między centrach danych platformy Azure i infrastruktury
  - Nie działa za pośrednictwem publicznej sieci Internet
  - Oferuje niezawodności, szybkości, mniejsze opóźnienia, wysokiego poziomu zabezpieczeń
  - Oferty maksymalnie 10gbps szybkości i opcje planu danych bez ograniczeń
 - **Brama sieci VPN**
  - Witryny do lokacji/punkt lokacja sieci VPN
  - Ruch przechodzi za pośrednictwem publicznej sieci Internet
  - Używa zabezpieczeń protokołu internetowego (IPsec) i Internet Key Exchange (IKE)

### <a name="expressroute-has-many-different-options-like-unlimited-vs-metered-different-speed-options-and-premium-add-on-which-should-i-choose"></a>ExpressRoute ma wiele różne opcje, takie jak nieograniczoną liczbę i opcje taryfowe, różne prędkości oraz dodatek premium. Który należy wybrać?
Opcje zależą od scenariusza, który w przypadku wdrażania i ilość danych zamierzasz rozesłać. Można sterować transferu danych programu Configuration Manager między serwerami lokacji a punktami dystrybucji, ale nie może być kontrolowana komunikacji serwera do lokacji serwer lokacji.   Kiedy używasz planu danych pomiarów wprowadzania do określonych witryn (i systemy lokacji) lokalnie i za pomocą [programu Configuration Manager przepustowości wbudowane formanty](/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management) może ułatwić kontrolę kosztów Azure.

### <a name="what-about-installation-requirements-like-active-directory-domains-do-i-still-need-to-join-my-site-servers-to-an-active-directory-domain"></a>Informacje o wymagania dotyczące instalacji, takich jak domen usługi Active Directory? Nadal należy do przyłączenia do domeny usługi Active Directory serwerów lokacji?
Tak. Po przeniesieniu Azure, [obsługiwane konfiguracje](/sccm/core/plan-design/configs/supported-configurations) pozostają takie same, w tym wymagania dotyczące usługi Active Directory w przypadku instalowania programu Configuration Manager.

### <a name="i-understand-the-need-to-join-my-site-servers-to-an-active-directory-domain-but-can-i-use-azure-active-directory"></a>Rozumiem trzeba dołączyć do domeny usługi Active Directory serwerów lokacji, ale można użyć usługi Azure Active Directory?
Nie, Azure Active Directory nie jest obsługiwana w tej chwili. Serwery lokacji nadal muszą być członkami [domeny usługi Active Directory systemu Windows](/sccm/core/plan-design/configs/support-for-active-directory-domains).



## <a name="availability"></a>Dostępność
### <a name="one-of-the-reasons-i-am-moving-infrastructure-to-azure-is-the-promise-of-high-availability-can-i-take-advantage-of-high-availability-options-like-azure-vm-availability-sets-for-vms-that-i-will-use-for-configuration-manager"></a>Jednym z powodów am I przenoszenie infrastruktury Azure jest promise o wysokiej dostępności. Czy można było korzystać z opcje wysokiej dostępności, takie jak zestawy dostępności maszyny Wirtualnej platformy Azure dla maszyn wirtualnych, które będą używać programu Configuration Manager?
Tak! Zbiory dostępności maszyny Wirtualnej platformy Azure może służyć do ról systemu lokacji nadmiarowe, takich jak punkty dystrybucji lub punktów zarządzania.

Ponadto można użyć dla serwerów lokacji programu Configuration Manager. Na przykład administracji centralnej i lokacje główne mogą należeć do tego samego zestawu dostępności, co pomaga zapewnić, że ich są jeszcze ponownie uruchomiony w tym samym czasie.

### <a name="how-can-i-make-my-database-highly-available-can-i-use-azure-sql-database-or-do-i-have-to-use-microsoft-sql-server-in-a-vm"></a>Jak utworzyć bazy danych wysokiej dostępności? Można używać bazy danych SQL Azure? Czy trzeba używać programu Microsoft SQL Server na maszynie Wirtualnej?
Należy użyć programu Microsoft SQL Server na maszynie Wirtualnej. Menedżer konfiguracji nie obsługuje serwera SQL Azure w tej chwili. Jednak można użyć funkcji, takich jak grupy dostępności AlwaysOn dla programu SQL server. [Zawsze włączone grupy dostępności](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database) oficjalnie są obsługiwane począwszy od wersji 1602 programu Configuration Manager i są zalecane.

### <a name="can-i-use-azure-load-balancers-with-site-system-roles-like-management-points--or-software-update-points"></a>Można użyć usługi równoważenia obciążenia Azure z rolami systemu lokacji, takich jak punkty zarządzania lub punktów aktualizacji oprogramowania?
Menedżer konfiguracji nie jest testowana usługi równoważenia obciążenia Azure, jeśli funkcje są niewidoczne dla aplikacji, jej nie powinna mieć żadnych niekorzystny wpływ na normalną pracę.


## <a name="performance"></a>Wydajność
### <a name="what-factors-affect-performance-in-this-scenario"></a>Jakie czynniki wpływają na wydajność w tym scenariuszu?
[Azure rozmiar maszyny Wirtualnej i typ](https://azure.microsoft.com/documentation/articles/virtual-machines-size-specs), maszyny Wirtualnej Azure dysków (magazynu premium jest zalecane, szczególnie w przypadku programu SQL Server), sieci opóźnienia i szybkość są najważniejszych obszarów.

### <a name="so-tell-me-more-about-azure-virtual-machines-what-size-vms-should-i-use"></a>Tak więc Powiedz mi więcej o maszyny wirtualne platformy Azure; jakie maszyny wirtualne rozmiar należy użyć?
Ogólnie rzecz biorąc, muszą spełniać swoje mocy obliczeniowej (Procesora i pamięci) [zalecane sprzętu dla programu System Center Configuration Manager](/sccm/core/plan-design/configs/recommended-hardware). Jednak istnieją pewne różnice między sprzęt komputerowy regularnych i maszyny wirtualne platformy Azure, zwłaszcza, jeśli chodzi o dyski użycia tych maszyn wirtualnych.  Jaki rozmiar maszyny wirtualne można użyć zależy od wielkości środowiska, ale poniżej przedstawiono kilka zaleceń:
- W przypadku wdrożeń produkcyjnych o dowolnym rozmiarze znaczące zaleca się "**S**" klasy maszynach wirtualnych platformy Azure. Jest to spowodowane wykorzystują dyski magazynu Premium.  Klasa innych niż "S" Użyj maszyny wirtualne obiektu blob magazynu i ogólnie rzecz biorąc nie będzie spełnić wymagania dotyczące wydajności niezbędne do obsługi dopuszczalne produkcji.
- Wielu dysków w magazynie Premium należy używać na wyższym poziomie i rozłożone w konsoli Zarządzanie dyskami systemu Windows dla maksymalna liczba IOPS.  
- Zaleca się używanie lepiej lub premium wielu dysków podczas wdrożenia początkowej lokacji (na przykład P30 zamiast P20 i 2xP30 na woluminie rozłożonym zamiast 1xP30). Następnie Jeśli później witryny musi zwiększać rozmiar maszyny Wirtualnej ze względu na dodatkowe obciążenie, możesz korzystać dodatkowych zasobów Procesora i pamięci, która zapewnia większy rozmiar maszyny Wirtualnej. Ponadto mają dysków już w miejscu, które można wykorzystać dodatkowe przepływności operacje We/Wy, który pozwala na większy rozmiar maszyny Wirtualnej.



W poniższej tabeli wymieniono liczby początkowej dysku sugerowane korzystanie z lokacji głównej i centralnej administracji różnych instalacjach:

**Baza danych lokacji wspólnie** -lokacji głównej lub centralnej administracji baza danych lokacji na serwerze lokacji:

| Klienci pulpitu    |Zalecany rozmiar maszyny Wirtualnej|Zalecane dysków|
|--------------------|-------------------|-----------------|
|**Maksymalnie 25 tys.**       |   DS4_V2          |2xP30 (rozłożone)  |
|**25 do 50 tys**      |   DS13_V2         |2xP30 (rozłożone)  |
|**50k-100k**     |   DS14_V2         |3xP30 (rozłożone)  |


**Baza danych lokacji zdalnej** -lokacji głównej lub centralnej administracji baza danych lokacji na serwerze zdalnym:

| Klienci pulpitu    |Zalecany rozmiar maszyny Wirtualnej|Zalecane dysków |
|--------------------|-------------------|------------------|
|**Maksymalnie 25 tys.**       | Serwer lokacji: F4S </br>Serwer bazy danych: DS12_V2 | Serwer lokacji: 1xP30 </br>Serwer bazy danych: 2xP30 (rozłożone)  |
|**25 do 50 tys**      | Serwer lokacji: F4S </br>Serwer bazy danych: DS13_V2 | Serwer lokacji: 1xP30 </br>Serwer bazy danych: 2xP30 (rozłożone)   |
|**50k-100k**     | Serwer lokacji: F8S </br>Serwer bazy danych: DS14_V2 | Serwer lokacji: 2xP30 (rozłożone)   </br>Serwer bazy danych: 3xP30 (rozłożone)   |

Poniżej przedstawiono przykładową konfigurację dla klientów 50k-100k na DS14_V2 z dyskami 3xP30 na woluminie rozłożonym z oddzielnym logicznej woluminów programu Configuration Manager Zainstaluj i pliki bazy danych:  ![Dyski maszyny Wirtualnej)](media/vm_disks.png)  



## <a name="user-experience"></a>Środowisko użytkownika
### <a name="you-mention-that-user-experience-is-one-of-the-main-areas-of-importance-why-is-that"></a>Wspomnieć, że środowisko użytkownika jest jednym z głównych obszarów znaczenie, dlaczego?
Decyzje podejmowane w sieci, dostępność, wydajność, a w przypadku, gdy umieścisz serwerów lokacji programu Configuration Manager można bezpośrednio wpływa na użytkowników. Uważamy, Przenieś Azure powinien być niewidoczne dla użytkowników, aby ich nie występują zmiany w ich codziennych interakcji z programem Configuration Manager.

### <a name="ok-i-get-it-i-plan-to-install-a-single-stand-alone-primary-site-on-an-azure-virtual-machine-and-i-want-to-make-sure-my-costs-are-low-should-i-place-remote-site-systems-like-management-points-distribution-points-and-software-update-points-on-azure-virtual-machines-as-well-or-on-premises"></a>Dobrze chcę ją. Należy zaplanować zainstalować jednej autonomicznej lokacji głównej na maszynie wirtualnej platformy Azure i chcę upewnij się, że brakuje Moje kosztów. Systemy lokacji (zdalnego), (takie jak punkty zarządzania, punkty dystrybucji i aktualizacji oprogramowania punktów) należy umieścić na również maszyny wirtualne platformy Azure lub lokalnie?
Z wyjątkiem komunikacji między serwerem lokacji do punktu dystrybucji komunikacja do serwera w lokacji może występować w dowolnym momencie i nie używa mechanizmów kontroli użycia przepustowości sieci. Ponieważ nie można kontrolować komunikacji między systemami lokacji, należy rozważyć kosztów związanych z tych informacji.

Szybkość sieci i czas oczekiwania są inne czynniki do rozważenia również. Powolnych lub zawodnych sieci może mieć wpływ na funkcjonalność między serwerem lokacji a systemami lokacji zdalnej, jak również wszelkich komunikacji klienta z systemami lokacji. Należy również uwzględnić liczbę zarządzanych klientów, którzy używają systemu lokacji, a także aktywnie używanych funkcji.
Ogólnie rzecz biorąc można wykorzystać normalne wskazówek w powiązaniu z łączami i systemy lokacji jako punkt początkowy. Najlepiej, jeśli przepływność sieci, zaznacz i odbieranych platformy Azure i z siecią intranet będą zgodne z sieci WAN, który jest dobrze połączony z szybkiej sieci.

### <a name="what-about-content-distribution-and-content-management-should-standard-distribution-points-be-in-azure-or-on-premises-and-should-i-use-branchcache-or-pull-distribution-points-on-premises-or-should-i-make-exclusive-use-of-cloud-distribution-points"></a>Informacje o dystrybucji zawartości i zarządzanie zawartością? Powinna być standardowe punkty dystrybucji w Azure lub lokalnie i należy używać usługi BranchCache lub punktów dystrybucji ściągania lokalnie? Czy trzeba utworzyć wyłącznego użytku punkty dystrybucji w chmurze?
Podejście do zarządzania zawartością jest prawie tak samo jak w przypadku serwerów lokacji a systemami lokacji.
- Użycie sieci szybkie i niezawodne połączenie między Azure i sieć intranet z planem danych bez ograniczeń, hosting standardowe punkty dystrybucji w usłudze Azure można opcję.
-  Jeśli używasz koszt planowania i przepustowości danych pomiarów jest istotny lub połączenie sieciowe między Azure i sieci intranet nie jest szybka lub mogą być zawodne, a następnie rozważyć innych metod. Należą do nich lokalizowanie standard lub punktów dystrybucji ściągania lokalnych, jak również za pomocą usługi BranchCache. Korzystanie z punktów dystrybucji w chmurze jest również opcja, ale istnieją pewne ograniczenia na typy zawartości, obsługiwane (na przykład, nie są obsługiwane pakiety aktualizacji oprogramowania).

> [!NOTE]
>  Jeśli wymagana jest obsługa środowiska PXE, musi być odpowiadać na żądania rozruchu lokalnych punktów dystrybucji (standard lub pull). [Usługi wdrażania systemu Windows nie jest obecnie obsługiwana na maszynach wirtualnych platformy Azure](https://technet.microsoft.com/library/hh831764(v=ws.11).aspx).


### <a name="while-i-am-ok-with-the-limitations-of-cloud-based-distribution-points-i-dont-want-to-put-my-management-point-into-a-dmz-even-though-that-is-needed-to-support-my-internet-based-clients-do-i-have-any-other-options"></a>Podczas rozmowy OK z ograniczeniami punktów dystrybucji w chmurze, nie chcę umieścić Moje punktu zarządzania w DMZ, mimo że jest potrzebny do obsługi klientów internetowych. Inne opcje są dostępne?
Tak! Z 1610 wersji programu Configuration Manager, firma Microsoft wprowadzone [brama zarządzania chmury](/sccm/core/clients/manage/manage-clients-internet#cloud-management-gateway) jako funkcję wersji wstępnej. (Ta funkcja pojawiły się najpierw w wersji Technical Preview 1606 jako [usługi serwera Proxy w chmurze](/sccm/core/get-started/capabilities-in-technical-preview-1606#a-namecloudproxyacloud-proxy-service-for-managing-clients-on-the-internet)).

**Brama zarządzania chmury** udostępnia prosty sposób zarządzać klientami programu Configuration Manager w Internecie. Usługa, która jest wdrażana Microsoft Azure i wymaga subskrypcji platformy Azure, łączy się z lokalnej infrastruktury programu Configuration Manager za pomocą nowej roli o nazwie punkt łącznik chmury zarządzania bramy. Po zostało wdrożone i skonfigurowane, klienci mogą uzyskiwać dostęp do lokalnego ról systemu lokacji programu Configuration Manager bez względu na to czy są połączone z prywatną siecią wewnętrzną lub w Internecie.

Można uruchomić przy użyciu bramy zarządzania chmury w danym środowisku i Prześlij nam opinię, aby to lepsze. Informacje o funkcjach wersji wstępnej, zobacz [używać funkcji wersji wstępnej z aktualizacji](/sccm/core/servers/manage/install-in-console-updates#a-namebkmkprereleasea-use-pre-release-features-from-updates).

### <a name="i-also-heard-that-you-have-another-new-feature-called-peer-cache-introduced-as-a-pre-release-feature-in-version-1610-is-that-different-than-branchcache-which-one-should-i-choose"></a>Heard I również, że masz innej nowej funkcji o nazwie wprowadzone jako funkcja wersji wstępnej wersji 1610 Buforowanie równorzędne. Jest to, że inne niż Usługa BranchCache? Co mam wybrać?
Tak, zupełnie różne. [Peer pamięci podręcznej](/sccm/core/plan-design/hierarchy/client-peer-cache) jest technologia programu Configuration Manager z macierzystego 100%, gdzie usługa BranchCache jest to funkcja systemu Windows. Jednocześnie może być przydatne dla Ciebie; Usługa BranchCache używa emisji, aby znaleźć wymaganą zawartość, podczas gdy Buforowanie równorzędne używa Menedżera konfiguracji regularnego przepływu pracy i granicy grupy ustawień dystrybucji.

Można skonfigurować dowolny klient jest źródłem Buforowanie równorzędne. Następnie, gdy punktów zarządzania zapewniają klientom informacją o lokalizacji źródła zawartości, ich zawierają szczegółowe informacje o zarówno punkty dystrybucji, jak i wszelkich źródeł Buforowanie równorzędne z zawartością ten klient wymaga.


## <a name="cost"></a>Koszt
### <a name="ok-tell-me-a-bit-about-the-cost-will-this-be-a-cost-effective-solution-for-me"></a>OK Powiedz mi coś o koszty. Spowoduje to ekonomiczne rozwiązanie dla mnie
Różni się trudno powiedzieć od każdego środowiska. Najlepiej, aby zrobić jest kosztów środowisku za pomocą Microsoft Azure Kalkulator cen: https://azure.microsoft.com/pricing/calculator/

## <a name="additional-resources"></a>Dodatkowe zasoby
**Podstawy:** http://azure.microsoft.com/documentation/articles/fundamentals-introduction-to-azure/

**Typy maszyny maszyny Wirtualnej platformy Azure:**
 - Azure rozmiarów maszyn: https://azure.microsoft.com/documentation/articles/virtual-machines-size-specs/  
 - Cennik maszyn wirtualnych: http://azure.microsoft.com/pricing/details/virtual-machines/  
 - Ceny usługi Magazyn: http://azure.microsoft.com/pricing/details/storage/

**Zagadnienia dotyczące wydajności dysku:**    
 - Wprowadzenie do dysku Premium: http://azure.microsoft.com/blog/2014/12/11/introducing-premium-storage-high-performance-storage-for-azure-virtual-machine-workloads/  
 - Więcej informacji o dysku Premium: http://azure.microsoft.com/documentation/articles/storage-premium-storage-preview-portal/   
 - Celem jest przydatny zestaw wykresy max rozmiary i informacji o wydajności magazynu: https://azure.microsoft.com/documentation/articles/storage-scalability-targets/  
 - Wprowadzenie do innego + niektórych schłodzić maniaków uber danych na jak magazynu Premium działa pod maską: http://azure.microsoft.com/blog/2015/04/16/azure-premium-storage-now-generally-available-2/

**Dostępność:**
 - Azure IaaS czas działania SLA firmy: https://azure.microsoft.com/support/legal/sla/virtual-machines/v1_0/  
 - Zbiory dostępności wyjaśniono: https://azure.microsoft.com/documentation/articles/virtual-machines-manage-availability/

**Połączenie:**
 - Express vs trasy. Azure VPN: http://azure.microsoft.com/blog/2014/06/10/expressroute-or-virtual-network-vpn-whats-right-for-me/
 - Express ceny trasy: http://azure.microsoft.com/pricing/details/expressroute/
 - Więcej informacji na temat Express trasy: http://azure.microsoft.com/documentation/articles/expressroute-introduction/

 

