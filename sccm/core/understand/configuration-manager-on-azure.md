---
title: Configuration Manager na platformie Azure
description: "Informacje o korzystaniu z programu Configuration Manager w środowisku platformy Azure."
ms.custom: na
ms.date: 03/27/2017
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: article
ms.assetid: d24257d8-8136-47f4-8e0d-34021356dc37
caps.latest.revision: "2"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: a1d4fb9c8a19565d6f49f3d3e1e70f698305e6a4
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="configuration-manager-on-azure---frequently-asked-questions"></a>Menedżer konfiguracji Azure — często zadawane pytania
*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Następujące pytania i odpowiedzi może ułatwić zrozumienie, kiedy należy używać i konfigurowanie programu Configuration Manager w systemie Microsoft Azure.

## <a name="general-questions"></a>Pytania ogólne
### <a name="my-company-is-trying-to-move-as-many-physical-servers-as-possible-to-microsoft-azure-can-i-move-configuration-manager-servers-to-azure"></a>Moja firma podejmuje próbę przeniesienia zgodnie z wielu serwerów fizycznych, jak to możliwe do systemu Microsoft Azure, można przenieść serwerów programu Configuration Manager na platformie Azure?
Oczywiście jest obsługiwany scenariusz.  Zobacz [Obsługa środowisk wirtualizacji dla programu System Center Configuration Manager](/sccm/core/plan-design/configs/support-for-virtualization-environments).

### <a name="great-my-environment-requires-multiple-sites-should-all-child-primary-sites-be-in-azure-with-the-central-administration-site-or-on-premises-what-about-secondary-sites"></a>Doskonałe! Moje środowisko wymaga wielu lokacji. Wszystkie podrzędne Lokacje główne należy na platformie Azure z centralnej lokacji administracyjnej lub lokalnymi? Informacje o lokacji dodatkowej?
Komunikacja lokacja lokacja (opartych na plikach i replikacji bazy danych) korzysta z blisko hostowana na platformie Azure. Jednak ruch będzie zdalnie z serwerami lokacji a systemami lokacji związanych z wszystkich klientów. Jeśli używasz szybkie i niezawodne połączenie sieciowe platformy Azure i intranetem z planem dane nieograniczone obsługi infrastruktury w usłudze Azure jest opcją.

Jednak używanie planów dane naliczane i dostępnej przepustowości lub koszt jest istotny, czy połączenie sieciowe między Azure i sieci intranet nie jest szybkie lub mogą być nieprawidłowe, należy rozważyć umieszczenie w określonych lokacjach (i systemy lokacji) lokalnie, a następnie użyj kontroli przepustowości wbudowane w oprogramowanie Configuration Manager.

### <a name="is-having-configuration-manager-in-azure-a-saas-scenario-software-as-a-service"></a>Występują programu Configuration Manager na platformie Azure scenariusza SaaS (oprogramowanie jako usługa)?
Nie, jest IaaS (infrastruktura jako usługa), ponieważ host serwery infrastruktury programu Configuration Manager w maszynach wirtualnych platformy Azure.

### <a name="what-areas-should-i-pay-attention-to-when-considering-a-move-of-my-configuration-manager-infrastructure-to-azure"></a>Obszary I zwrócić uwagę na Rozważając przenoszenia Moje infrastruktury programu Configuration Manager na platformie Azure?
Doskonałe pytanie, w tym miejscu są obszarów, które są najważniejsze podczas podejmowania decyzji tego, każdego jest przedstawione w osobnej sekcji tego tematu:
1.  Obsługa sieci
2.  Dostępność
3.  Wydajność
4.  Koszt
5.  Środowisko użytkownika

## <a name="networking"></a>Obsługa sieci
### <a name="what-about-networking-requirements-should-i-use-expressroute-or-an-azure-vpn-gateway"></a>Informacje o sieci wymagania, należy użyć programu ExpressRoute lub brama sieci VPN platformy Azure?
Sieć jest bardzo ważne. Szybkości sieci i czas oczekiwania może mieć wpływ na funkcjonalność między serwerem lokacji i systemów lokacji zdalnych, a wszelkie komunikacji klienta z systemami lokacji. Nasze zalecenie ma używać usługi ExpressRoute. Ale nie ma ograniczeń programu Configuration Manager, aby uniemożliwić korzystanie z bramy sieci VPN platformy Azure. Należy uważnie przejrzeć wymagań (wydajność, poprawki, dystrybucji oprogramowania, wdrażania systemu operacyjnego) z tej infrastruktury, a następnie wprowadź decyzji. Należy wziąć pod uwagę dla każdego z rozwiązań w kilku kwestiach obejmują:

 - **ExpressRoute** (zalecane)
  - Naturalne rozszerzenie centrum danych (można powiązać razem wiele centrów danych)
  - Prywatne połączeń między centrach danych platformy Azure i infrastruktury
  - Nie działa za pośrednictwem publicznej sieci Internet
  - Zapewnia niezawodność, szybkości, mniejsze opóźnienia, wysokiego poziomu zabezpieczeń
  - Oferty do szybkości 10 GB/s i opcje planu nieograniczone danych
 - **Brama sieci VPN**
  - Sieci VPN lokacji do lokacji/punkt lokacja
  - Ruch przechodzi przez publiczny Internet
  - Używa zabezpieczeń protokołu internetowego (IPsec) i Internet Key Exchange (IKE)

### <a name="expressroute-has-many-different-options-like-unlimited-vs-metered-different-speed-options-and-premium-add-on-which-should-i-choose"></a>ExpressRoute ma wiele różnych opcji, takich jak nieograniczone a szybkość naliczane, różne opcje, a dodatek w warstwie premium. Który należy wybrać?
Wybrane opcje zależą od scenariusza, który w przypadku wdrażania i ilości danych zamierzasz rozesłać. Transfer danych programu Configuration Manager mogą być kontrolowane między serwerami lokacji a punktami dystrybucji, ale nie mogą być kontrolowane komunikacji z serwerem lokacji serwera lokacji.   Jeśli używasz planu dane naliczane wprowadzania do określonych witryn (i systemy lokacji) lokalnie i za pomocą [kontroli przepustowości wbudowanych programu Configuration Manager](/sccm/core/plan-design/hierarchy/fundamental-concepts-for-content-management) można ułatwić kontrolę kosztów Azure.

### <a name="what-about-installation-requirements-like-active-directory-domains-do-i-still-need-to-join-my-site-servers-to-an-active-directory-domain"></a>O wymaganiach dotyczących instalacji jak domen usługi Active Directory? Nadal należy do przyłączenia do domeny usługi Active Directory Moje serwery lokacji?
Tak. W przypadku przenoszenia do platformy Azure, [obsługiwane konfiguracje](/sccm/core/plan-design/configs/supported-configurations) pozostają takie same, w tym wymagania dotyczące usługi Active Directory w przypadku instalowania programu Configuration Manager.

### <a name="i-understand-the-need-to-join-my-site-servers-to-an-active-directory-domain-but-can-i-use-azure-active-directory"></a>Rozumiem potrzeba przyłączania serwerów lokacji do domeny usługi Active Directory, ale można użyć usługi Azure Active Directory?
Nie, Azure Active Directory nie jest obsługiwana w tej chwili. Serwery lokacji nadal muszą być elementami członkowskimi [domeny usługi Active Directory systemu Windows](/sccm/core/plan-design/configs/support-for-active-directory-domains).



## <a name="availability"></a>Dostępność
### <a name="one-of-the-reasons-i-am-moving-infrastructure-to-azure-is-the-promise-of-high-availability-can-i-take-advantage-of-high-availability-options-like-azure-vm-availability-sets-for-vms-that-i-will-use-for-configuration-manager"></a>Jedną z przyczyn przeprowadzam infrastruktury na platformie Azure jest gwarantuje wysoką dostępność. Czy można wykonać opcje wysokiej dostępności, takich jak zestawy dostępności maszyny Wirtualnej platformy Azure dla maszyn wirtualnych, które będą używać programu Configuration Manager?
Tak! Zestawy dostępności maszyny Wirtualnej platformy Azure może służyć do ról systemu lokacji nadmiarowego, takich jak punkty dystrybucji lub punkty zarządzania.

Można także używać ich na serwerach lokacji programu Configuration Manager. Na przykład centralne Lokacje administracyjne i lokacje główne wszystkich można w tym samym zestawie dostępności, która może pomóc upewnić się, że ich są nie ponownie uruchamiane w tym samym czasie.

### <a name="how-can-i-make-my-database-highly-available-can-i-use-azure-sql-database-or-do-i-have-to-use-microsoft-sql-server-in-a-vm"></a>Jak utworzyć bazy danych wysokiej dostępności? Czy można używać bazy danych SQL Azure? Czy trzeba użyć programu Microsoft SQL Server na maszynie wirtualnej?
Należy użyć programu Microsoft SQL Server na maszynie wirtualnej. Menedżer konfiguracji nie obsługuje Azure SQL Server w tej chwili. Jednak można użyć funkcji, takich jak zawsze włączonych grup dostępności dla programu SQL server. [Zawsze włączone grupy dostępności](/sccm/core/servers/deploy/configure/sql-server-alwayson-for-a-highly-available-site-database) zaleca się i oficjalnie są obsługiwane począwszy od wersji 1602 programu Configuration Manager.

### <a name="can-i-use-azure-load-balancers-with-site-system-roles-like-management-points--or-software-update-points"></a>Moduły równoważenia obciążenia Azure można używać z rolami systemu lokacji, takich jak punkty zarządzania lub punktów aktualizacji oprogramowania?
Gdy Menedżer konfiguracji nie jest testowana równoważenia obciążenia Azure, jeśli dana funkcja jest niewidoczne dla aplikacji, nie powinna mieć żadnych niekorzystny wpływ na normalne operacje.


## <a name="performance"></a>Wydajność
### <a name="what-factors-affect-performance-in-this-scenario"></a>Jakie czynniki wpływają na wydajność w tym scenariuszu?
[Azure rozmiar maszyny Wirtualnej i typ](https://azure.microsoft.com/documentation/articles/virtual-machines-size-specs), maszyny Wirtualnej platformy Azure (magazyn w warstwie premium jest zalecane, szczególnie dla programu SQL Server) dysków, sieci opóźnienia i szybkość są najważniejsze obszary.

### <a name="so-tell-me-more-about-azure-virtual-machines-what-size-vms-should-i-use"></a>Tak więcej informacji o maszynach wirtualnych platformy Azure; jakie rozmiar maszyn wirtualnych należy użyć?
Ogólnie rzecz biorąc, Twoje moc obliczeniową, (Procesora i pamięci) muszą spełniać [zalecany sprzęt dla programu System Center Configuration Manager](/sccm/core/plan-design/configs/recommended-hardware). Istnieją pewne różnice między komputerem regularne i maszyn wirtualnych platformy Azure, zwłaszcza, jeśli chodzi o dyski te maszyny wirtualne korzystają.  Jaki rozmiar maszyn wirtualnych, możesz użyć zależy od rozmiaru środowiska, ale poniżej przedstawiono kilka zaleceń:
- Wdrożeń produkcyjnych o dowolnym rozmiarze znaczących zalecamy "**S**" klasy maszynach wirtualnych platformy Azure. Jest to spowodowane mogą korzystać z dysków Premium Storage.  Klasa z systemem innym niż "S" maszyn wirtualnych Użyj magazynu obiektów blob i zazwyczaj nie będzie spełniać wymagania wydajności wymaganych przez środowisko produkcji dopuszczalne.
- Wiele dysków magazyn w warstwie Premium należy użyć w celu zwiększenia skali i rozłożone w konsoli Zarządzanie dyskami systemu Windows dla opcji Maksymalna liczba IOPS.  
- Firma Microsoft zaleca używanie lepiej lub premium wielu dysków podczas wdrożenia początkowej lokacji (na przykład P30 zamiast P20 i 2xP30 w woluminy rozłożone zamiast 1xP30). Następnie Jeśli witryny później musi zwiększać rozmiar maszyny Wirtualnej ze względu na dodatkowe obciążenie, można skorzystać dodatkowych zasobów Procesora i pamięci, która zapewnia większy rozmiar maszyny Wirtualnej. Dyski będą także mieć już w miejscu, które można wykorzystać dodatkowej przepływności IOPS, który umożliwia większy rozmiar maszyny Wirtualnej.



W poniższych tabelach przedstawiono liczby dysku sugerowane początkowej mogą korzystać z różnych instalacjach w lokacjach głównych i centralnej administracji:

**Baza danych lokacji wspólnie** -głównej lub centralnej lokacji administracyjnej z bazy danych lokacji na serwerze lokacji:

| Klienci Stacjonarni    |Zalecany rozmiar maszyny Wirtualnej|Zalecane dysków|
|--------------------|-------------------|-----------------|
|**25k**       |   DS4_V2          |2xP30 (rozkładane)  |
|**25k do 50k**      |   DS13_V2         |2xP30 (rozkładane)  |
|**50k-100k**     |   DS14_V2         |3xP30 (rozkładane)  |


**Baza danych lokacji zdalnej** -głównej lub centralnej lokacji administracyjnej z bazy danych lokacji na serwerze zdalnym:

| Klienci Stacjonarni    |Zalecany rozmiar maszyny Wirtualnej|Zalecane dysków |
|--------------------|-------------------|------------------|
|**25k**       | Serwer lokacji: F4S </br>Serwer bazy danych: DS12_V2 | Serwer lokacji: 1xP30 </br>Serwer bazy danych: 2xP30 (rozkładane)  |
|**25k do 50k**      | Serwer lokacji: F4S </br>Serwer bazy danych: DS13_V2 | Serwer lokacji: 1xP30 </br>Serwer bazy danych: 2xP30 (rozkładane)   |
|**50k-100k**     | Serwer lokacji: F8S </br>Serwer bazy danych: DS14_V2 | Serwer lokacji: 2xP30 (rozkładane)   </br>Serwer bazy danych: 3xP30 (rozkładane)   |

Poniżej przedstawiono przykładową konfigurację klientów 50k-100k na DS14_V2 z dyskami 3xP30 na woluminie rozłożonym z oddzielnym logicznej woluminów programu Configuration Manager Zainstaluj i pliki bazy danych: ![Dyski maszyny Wirtualnej)](media/vm_disks.png)  



## <a name="user-experience"></a>Środowisko użytkownika
### <a name="you-mention-that-user-experience-is-one-of-the-main-areas-of-importance-why-is-that"></a>Wymieniają się, że środowisko użytkownika jest jednym z głównych obszarów znaczenie, dlaczego?
Decyzje podejmowane w sieci, dostępności, wydajności i gdzie należy umieścić serwery lokacji programu Configuration Manager może mieć wpływ na użytkowników bezpośrednio. Mamy nadzieję, że przenoszenie na platformę Azure powinna być niewidoczny dla użytkowników, aby nie wystąpieniu zmianę ich codzienną interakcję z programem Configuration Manager.

### <a name="ok-i-get-it-i-plan-to-install-a-single-stand-alone-primary-site-on-an-azure-virtual-machine-and-i-want-to-make-sure-my-costs-are-low-should-i-place-remote-site-systems-like-management-points-distribution-points-and-software-update-points-on-azure-virtual-machines-as-well-or-on-premises"></a>OK I Pobierz go. Należy zaplanować, zainstalować jednej autonomicznej lokacji podstawowej na maszynę wirtualną platformy Azure i chcę upewnij się, że brakuje Moje kosztów. (Zdalnych) systemów lokacji (np. punkty zarządzania, punktów dystrybucji i punkty aktualizacji oprogramowania) należy umieścić na również maszyn wirtualnych platformy Azure lub lokalnie?
Z wyjątkiem komunikacji między serwerem lokacji do punktu dystrybucji komunikacja do serwera w lokacji może występować w dowolnym momencie i nie używa mechanizmów kontroli użycia przepustowości sieci. Ponieważ nie można kontrolować komunikacji między systemami lokacji, należy rozważyć kosztów związanych z otrzymywania tych wiadomości.

Szybkości sieci i opóźnienia są inne czynniki, które należy również wziąć pod uwagę. Wolnej lub zawodnej sieci może mieć wpływ na funkcjonalność między serwerem lokacji a systemami lokacji zdalnej, jak również wszystkie komunikacji klienta z systemami lokacji. Należy również uwzględnić liczbę zarządzanych klientów korzystających z systemu lokacji, a także funkcje, które aktywnie używane.
Ogólnie rzecz biorąc można wykorzystać normalnych wskazówek, ponieważ odnosi się do łącza sieci WAN i systemów lokacji jako punktu wyjścia. Najlepiej, jeśli przepustowość sieci, wybierz i odbierać platformy Azure i intranetem są zgodne z będący dobrze połączone z szybkiej sieci WAN.

### <a name="what-about-content-distribution-and-content-management-should-standard-distribution-points-be-in-azure-or-on-premises-and-should-i-use-branchcache-or-pull-distribution-points-on-premises-or-should-i-make-exclusive-use-of-cloud-distribution-points"></a>Informacje o dystrybucji zawartości i zarządzanie zawartością? Należy standardowe punkty dystrybucji w usłudze Azure lub lokalnie i używać usługi BranchCache lub lokalne punkty dystrybucji ściągających? Czy należy wykonać wyłącznego użytku punkty dystrybucji w chmurze?
Podejście związane z zarządzaniem zawartością są znacznie takie same, jak serwerami lokacji a systemami lokacji.
- Jeśli używasz szybkie i niezawodne połączenie sieciowe platformy Azure i intranetem z planem dane nieograniczone hosting standardowych punktów dystrybucji na platformie Azure można opcję.
-  Jeśli używasz jest istotny, dane naliczane koszt planowania i przepustowości lub połączenie sieciowe między Azure i sieci intranet nie jest szybkie lub może być zawodne, a następnie należy rozważyć inne podejścia. Obejmują one lokalizowanie standard lub punktów dystrybucji ściągania lokalnych, jak również za pomocą usługi BranchCache. Korzystanie z punktów dystrybucji w chmurze jest również opcję, ale istnieją pewne ograniczenia dla typów zawartości, obsługiwane (na przykład nie obsługuje pakietów aktualizacji oprogramowania).

> [!NOTE]
>  Jeśli wymagana jest obsługa środowiska PXE, należy użyć lokalnych punktów dystrybucji (standardowy lub ściągania) do odpowiadania na żądania rozruchu. [Usługi wdrażania systemu Windows nie jest obecnie obsługiwany do uruchamiania na maszynach wirtualnych Azure](https://technet.microsoft.com/library/hh831764(v=ws.11).aspx).


### <a name="while-i-am-ok-with-the-limitations-of-cloud-based-distribution-points-i-dont-want-to-put-my-management-point-into-a-dmz-even-though-that-is-needed-to-support-my-internet-based-clients-do-i-have-any-other-options"></a>Podczas OK z ograniczeniami punkty dystrybucji w chmurze, nie chcę umieścić Moje punktu zarządzania w strefą DMZ, nawet jeśli są one wymagane do obsługi klientów internetowych. Inne opcje są dostępne?
Tak! Z 1610 wersji programu Configuration Manager, wprowadzono [brama zarządzania chmury](/sccm/core/clients/manage/manage-clients-internet#cloud-management-gateway) jako funkcja wersji wstępnej. (Ta funkcja znajdowała się najpierw w wersji zapoznawczej Technical Preview 1606 jako [usługa serwera Proxy w chmurze](/sccm/core/get-started/capabilities-in-technical-preview-1606#a-namecloudproxyacloud-proxy-service-for-managing-clients-on-the-internet)).

**Brama zarządzania chmury** zapewnia prosty sposób zarządzać klientami programu Configuration Manager w Internecie. Usługi, która została wdrożona do systemu Microsoft Azure i wymaga subskrypcji platformy Azure, łączy się przy użyciu nowej roli wywołuje punkt łącznika bramy zarządzania chmury infrastruktury programu Configuration Manager lokalnie. Po ma na nim wdrożone i skonfigurowane, klienci mogą uzyskiwać dostęp lokalnie ról systemu lokacji programu Configuration Manager bez względu na to czy są one połączone siecią wewnętrzną prywatnych lub w Internecie.

Można uruchomić przy użyciu bramy zarządzania chmury w danym środowisku i przekaż nam swoją opinię, aby osiągnąć lepszą. Informacje o funkcji wersji wstępnej, zobacz [korzystanie z funkcji wersji wstępnej aktualizacje](/sccm/core/servers/manage/install-in-console-updates#a-namebkmkprereleasea-use-pre-release-features-from-updates).

### <a name="i-also-heard-that-you-have-another-new-feature-called-peer-cache-introduced-as-a-pre-release-feature-in-version-1610-is-that-different-than-branchcache-which-one-should-i-choose"></a>Podobno się również, czy masz inną nową funkcję o nazwie wprowadzono jako funkcja wersji wstępnej wersji 1610 buforowania równorzędnego. Jest to, że inny niż Usługa BranchCache? Które z nich należy wybrać?
Tak, całkiem. [Elementu równorzędnego pamięci podręcznej](/sccm/core/plan-design/hierarchy/client-peer-cache) to technologia programu Configuration Manager natywnego 100%, gdzie usługa BranchCache jest funkcją systemu Windows. Jednocześnie może być przydatne w przypadku Usługa BranchCache używa emisji można znaleźć wymaganej zawartości, natomiast równorzędnej pamięci podręcznej używa Menedżera konfiguracji regularne dystrybucji przepływu pracy i granicy grupy ustawień.

Można skonfigurować dowolnego klienta jest źródłem równorzędnej pamięci podręcznej. Następnie, gdy punkty zarządzania zapewniają klientom informacji o lokalizacji źródła zawartości, zapewniają szczegółowe informacje o punktów dystrybucji i dowolnego źródła równorzędnej pamięci podręcznej z zawartością tego klienta wymaga.


## <a name="cost"></a>Koszt
### <a name="ok-tell-me-a-bit-about-the-cost-will-this-be-a-cost-effective-solution-for-me"></a>OK Powiedz mi coś o koszty. Spowoduje to ekonomiczne rozwiązanie służące do mnie
Trudno powiedzieć, ponieważ każde środowisko jest inna. Najlepiej, aby zrobić ma koszt środowiska przy użyciu Microsoft Azure Kalkulator cen: https://azure.microsoft.com/pricing/calculator/

## <a name="additional-resources"></a>Dodatkowe zasoby
**Podstawowe założenia:** http://azure.microsoft.com/documentation/articles/fundamentals-introduction-to-azure/

**Typy maszyna wirtualna Azure:**
 - Azure rozmiary: https://azure.microsoft.com/documentation/articles/virtual-machines-size-specs/  
 - Cennik maszyn wirtualnych: http://azure.microsoft.com/pricing/details/virtual-machines/  
 - Cennik Storage: http://azure.microsoft.com/pricing/details/storage/

**Zagadnienia dotyczące wydajności dysku:**    
 - Wprowadzenie do dysku Premium: http://azure.microsoft.com/blog/2014/12/11/introducing-premium-storage-high-performance-storage-for-azure-virtual-machine-workloads/  
 - Lepszy wyświetlania informacji o dysku Premium: http://azure.microsoft.com/documentation/articles/storage-premium-storage-preview-portal/   
 - Celem przydatny zestaw wykresy maksymalny rozmiar i wydajności dla magazynu: https://azure.microsoft.com/documentation/articles/storage-scalability-targets/  
 - Wprowadzenie do innego + niektóre cool pełny geek dane dotyczące sposobu działania magazyn w warstwie Premium za obejmuje: http://azure.microsoft.com/blog/2015/04/16/azure-premium-storage-now-generally-available-2/

**Dostępność:**
 - Azure IaaS przestojów SLA w: https://azure.microsoft.com/support/legal/sla/virtual-machines/v1_0/  
 - Zestawy dostępności wyjaśniono: https://azure.microsoft.com/documentation/articles/virtual-machines-manage-availability/

**Łączność:**
 - Express vs trasy. Sieci VPN platformy Azure: http://azure.microsoft.com/blog/2014/06/10/expressroute-or-virtual-network-vpn-whats-right-for-me/
 - Express trasy cennik: http://azure.microsoft.com/pricing/details/expressroute/
 - Więcej informacji na temat Express Route: http://azure.microsoft.com/documentation/articles/expressroute-introduction/

 
