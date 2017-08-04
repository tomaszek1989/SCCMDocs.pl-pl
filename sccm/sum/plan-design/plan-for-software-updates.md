---
title: Planowanie aktualizacji oprogramowania | Dokumentacja firmy Microsoft
description: "Planowanie infrastruktury punktu aktualizacji oprogramowania jest niezbędne, aby używać aktualizacji oprogramowania w środowisku produkcyjnym programu System Center Configuration Manager."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 06/27/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: d071b0ec-e070-40a9-b7d4-564b92a5465f
ms.translationtype: MT
ms.sourcegitcommit: 3c75c1647954d6507f9e28495810ef8c55e42cda
ms.openlocfilehash: bc7e702a4277ac1dc358aa9a2795cddbf42e475f
ms.contentlocale: pl-pl
ms.lasthandoff: 07/29/2017

---

# <a name="plan-for-software-updates-in-system-center-configuration-manager"></a>Planowanie aktualizacji oprogramowania w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Przed użyciem aktualizacji oprogramowania w środowisku produkcyjnym programu System Center Configuration Manager, należy przeprowadzić proces planowania. Dobry plan infrastruktury punktu aktualizacji oprogramowania o ma kluczowe znaczenie dla wdrożenia aktualizacji oprogramowania pomyślnie.

## <a name="capacity-planning-recommendations-for-software-updates"></a>Zalecenia dotyczące planowania wydajności pod kątem aktualizacji oprogramowania  
 Poniższe zalecenia można potraktować jako bazę pomocną w ustaleniu właściwych dla danej organizacji informacji dotyczących planowania wydajności pod kątem aktualizacji oprogramowania. Rzeczywiste wymagania dotyczące wydajności mogą się różnić od zaleceń w tym temacie zależnie od tych kryteriów: konkretne środowisko sieciowe, sprzęt używany do hostowania systemu lokacji punktu aktualizacji oprogramowania, liczba zainstalowanych klientów, a także role systemu lokacji zainstalowane na serwerze.  

###  <a name="BKMK_SUMCapacity"></a> Planowanie wydajności dla punktu aktualizacji oprogramowania  
 Liczba obsługiwanych klientów zależy od wersji usług Windows Server Update Services (WSUS) uruchamianej w punkcie aktualizacji oprogramowania, a także od tego, czy rola systemu lokacji punktu aktualizacji oprogramowania współistnieje z inną rolą systemu lokacji:  

-   Punkt aktualizacji oprogramowania może obsłużyć do 25 000 klientów, jeśli usługi WSUS działają na komputerze punktu aktualizacji oprogramowania, a punkt aktualizacji oprogramowania współistnieje z inną rolą systemu lokacji.  

-   Punkt aktualizacji oprogramowania może obsługiwać do 150 000 klientów, gdy komputer zdalny spełnia wymagania usług WSUS, usługi WSUS jest używany z programem Configuration Manager i należy skonfigurować następujące ustawienia:

    Pule aplikacji usług IIS:
    - Zwiększ długość kolejki WsusPool do 2000
    - Zwiększ limit pamięci prywatnej WsusPool x4 czterokrotnie lub ustaw wartość na 0 (brak ograniczenia)      

    Aby uzyskać szczegółowe informacje na temat wymagań sprzętowych dla punktu aktualizacji oprogramowania, zobacz [zalecane sprzętu dla systemów lokacji](/sccm/core/plan-design/configs/recommended-hardware#a-namebkmkscalesiesystemsa-site-systems).

-   Domyślnie program Configuration Manager nie obsługuje konfigurowania punktów aktualizacji oprogramowania jako klastrów równoważenia obciążenia Sieciowego. Przed 1702 wersji programu Configuration Manager możesz użyć zestawu SDK programu Configuration Manager można skonfigurować maksymalnie czterech punktów aktualizacji oprogramowania w klastrze równoważenia obciążenia Sieciowego. Jednak począwszy od programu Configuration Manager w wersji 1702 punktów aktualizacji oprogramowania nie są obsługiwane jako klastrów równoważenia obciążenia Sieciowego i uaktualnienia do programu Configuration Manager w wersji 1702 zostanie zablokowane, jeśli zostanie wykryty w tej konfiguracji.

### <a name="capacity-planning-for-software-updates-objects"></a>Planowanie wydajności pod kątem obiektów aktualizacji oprogramowania  
 Podczas planowania obiektów aktualizacji oprogramowania należy uwzględnić następujące informacje dotyczące wydajności.  

-   **Limit 1000 aktualizacji oprogramowania w jednym wdrożeniu**  

     Liczbę aktualizacji oprogramowania w każdym wdrożeniu aktualizacji oprogramowania należy ograniczyć do 1000. Podczas tworzenia zasady wdrażania automatycznego należy określić kryteria, które ograniczą liczbę zwracanych aktualizacji oprogramowania. Jeśli określone kryteria zwrócą więcej niż 1000 aktualizacji oprogramowania, zasada wdrażania automatycznego zakończy się niepowodzeniem. Można sprawdzić stan zasady wdrażania automatycznego z **reguły wdrażania automatycznego** węzeł w konsoli programu Configuration Manager. W przypadku ręcznego wdrażania aktualizacji oprogramowania nie należy wybierać więcej niż 1000 aktualizacji.  

     Należy także ograniczać liczbę aktualizacji oprogramowania do 1000 w linii bazowej konfiguracji. Aby uzyskać więcej informacji, zobacz [Tworzenie linii bazowych konfiguracji](../../compliance/deploy-use/create-configuration-baselines.md).

##  <a name="BKMK_SUPInfrastructure"></a> Ustalanie infrastruktury punktu aktualizacji oprogramowania  
 Centralna lokacja administracyjna i wszystkie podrzędne lokacje główne muszą dysponować punktem aktualizacji oprogramowania, w którym aktualizacje oprogramowania będą wdrażane. Planując infrastrukturę punktu aktualizacji oprogramowania, należy ustalić następujące zależności:
 - gdzie zainstalować punkt aktualizacji oprogramowania dla lokacji
 - które lokacje wymagają punktu aktualizacji oprogramowania akceptującego komunikację z klientami internetowymi
 - Określa, czy należy oprogramowania punktu aktualizacji w lokacji dodatkowej.

W ustaleniu infrastruktury punktu aktualizacji oprogramowania będą pomocne poniższe części.  

> [!IMPORTANT]  
>  Aby uzyskać informacje o wewnętrznych i zewnętrznych zależnościach wymaganych do aktualizacji oprogramowania, zobacz [wymagania wstępne dotyczące aktualizacji oprogramowania](prerequisites-for-software-updates.md).  

 Można dodać wiele punktów aktualizacji oprogramowania w lokacji głównej programu Configuration Manager. Możliwość dysponowania wieloma punktami aktualizacji oprogramowania w jednej lokacji zapewnia odporność na uszkodzenia, a nie stawia tylu wymagań, co złożone równoważenie obciążenia sieciowego. Niemniej jednak tryb failover uzyskiwany dzięki wielu punktom aktualizacji oprogramowania nie jest równie niezawodny, co równoważenie obciążenia sieciowego, gdy chodzi o czyste równoważenie obciążenia; z założenia ma on zapewniać raczej odporność na uszkodzenia. Ponadto model trybu failover punktu aktualizacji oprogramowania jest inny niż model oparty na czystym generowaniu losowym, który wykorzystano w konstrukcji punktów zarządzania. Inaczej niż w konstrukcji punktów zarządzania, w przypadku punktów aktualizacji oprogramowania istnieją pewne koszty wydajności klientów i sieci związane z przełączaniem się do nowego punktu aktualizacji oprogramowania. Kiedy klient przełącza się do nowego serwera usług WSUS, aby przeprowadzić skanowanie w poszukiwaniu aktualizacji oprogramowania, w efekcie zwiększa się rozmiar katalogu i następuje wzrost związanych z tym potrzeb dotyczących wydajności sieci i wydajności po stronie klienta. Dlatego też klient zachowuje koligacje z ostatnim punktem aktualizacji oprogramowania, który z powodzeniem odnalazł w wyniku skanowania.  

 Pierwszy punkt aktualizacji oprogramowania zainstalowany w lokacji głównej stanowi źródło synchronizacji dla wszystkich dodatkowych punktów aktualizacji oprogramowania dodawanych w lokacji głównej. Po dodaniu potrzebnych punktów aktualizacji oprogramowania i zainicjowaniu synchronizacji aktualizacji oprogramowania można wyświetlić stan punktów aktualizacji oprogramowania i źródła synchronizacji w węźle **Stan synchronizacji punktu aktualizacji oprogramowania** w obszarze roboczym **Monitorowanie** .  

 Kiedy jakiś punkt aktualizacji oprogramowania ulegnie awarii, a jest skonfigurowany jako źródło synchronizacji dla innych punktów aktualizacji oprogramowania w danej lokacji, należy ręcznie usunąć niedziałający punkt aktualizacji oprogramowania i wybrać nowy punkt aktualizacji oprogramowania, który będzie używany jako źródło synchronizacji. Aby uzyskać więcej informacji o sposobie usuwania aktualizacji oprogramowania punktu, zobacz [Usuń rolę systemu lokacji punktu aktualizacji oprogramowania](../get-started/remove-a-software-update-point.md).  

###  <a name="BKMK_SUPList"></a> Lista punktów aktualizacji oprogramowania  
 Configuration Manager udostępnia klientowi listę punktów aktualizacji oprogramowania w następujących scenariuszach: kiedy nowy klient otrzymuje zasadę włączającą aktualizacje oprogramowania lub kiedy klient nie może skontaktować się z jego punktu aktualizacji oprogramowania i musi przełączyć się do innego punktu aktualizacji oprogramowania. Klient losowo wybiera punkt aktualizacji oprogramowania z listy, dając pierwszeństwo tym punktom aktualizacji oprogramowania, które znajdują się w tym samym lesie. Menedżer konfiguracji zapewnia klientom różne listy, w zależności od typu klienta.  

-   **Klienci intranetowi**: Otrzymują listę punktów aktualizacji oprogramowania, które można skonfigurować tak, aby zezwolić na połączenia tylko z intranetu, albo listę punktów aktualizacji oprogramowania zezwalających na połączenia klientów internetowych i intranetowych.  

-   **Klienci internetowi**: Otrzymują listę punktów aktualizacji oprogramowania skonfigurowanych Aby zezwolić na połączenia tylko z Internetu, albo listę punktów aktualizacji oprogramowania zezwalających na połączenia klientów internetowych i intranetowych.  

###  <a name="BKMK_SUPSwitching"></a> Przełączanie punktów aktualizacji oprogramowania  
> [!NOTE]
> Począwszy od wersji 1702, klienci używają grup granic w celu znalezienia punktu aktualizacji oprogramowania, a powrotu i Znajdź nowej aktualizacji oprogramowania punktu, jeśli ich aktualny plan nie jest już dostępny. Punkty aktualizacji oprogramowania można dodać do różnych grup granic do serwerów, które klient można znaleźć formantu. Aby uzyskać więcej informacji, zobacz [punktów aktualizacji oprogramowania](/sccm/core/servers/deploy/configure/boundary-groups#software-update-points) w [konfigurowania grup granic](/sccm/core/servers/deploy/configure/boundary-groups) tematu.

Jeśli w lokacji istnieje wiele punktów aktualizacji oprogramowania, a jeden z nich ulegnie awarii lub przestanie być dostępny, klienci połączą się z innym punktem aktualizacji oprogramowania, kontynuując skanowanie w poszukiwaniu najnowszych aktualizacji oprogramowania. Kiedy do klienta zostaje po raz pierwszy przypisany punkt aktualizacji oprogramowania, klient pozostaje do niego przypisany, dopóki udaje mu się skanować ten punkt w poszukiwaniu aktualizacji oprogramowania.  

Skanowanie w poszukiwaniu aktualizacji oprogramowania może zakończyć się niepowodzeniem, zwracając rozmaite kody błędów ponownej próby i innych błędów. Kiedy skanowanie kończy się niepowodzeniem, zwracając kod błędu ponownej próby, klient uruchamia proces ponownej próby skanowania w poszukiwaniu aktualizacji oprogramowania w punkcie aktualizacji oprogramowania. Warunki wysokiego poziomu, w wyniku których jest zwracany kod błędu ponownej próby, to najczęściej niedostępność serwera usług WSUS lub jego czasowe przeciążenie. Kiedy nie udaje się przeprowadzić skanowania w poszukiwaniu aktualizacji oprogramowania, klient przystępuje do następującej procedury:  

1.  Klient przeprowadza skanowanie w poszukiwaniu aktualizacji oprogramowania o czasie zaplanowanym w harmonogramie lub po zainicjowaniu skanowania za pośrednictwem panelu sterowania na kliencie albo za pomocą zestawu SDK. Jeśli skanowanie się nie powiedzie, klient odczekuje 30 minut i ponawia próbę skanowania w tym samym punkcie aktualizacji oprogramowania.  

2.  Klient ponawia próbę co najmniej czterokrotnie w odstępach 30-minutowych. Po czwartym niepowodzeniu i po odczekaniu kolejnych dwóch minut klient przechodzi do następnego punktu aktualizacji oprogramowania z listy punktów aktualizacji oprogramowania.  

3.  Klient przechodzi przez te same czynności na nowy punkt aktualizacji oprogramowania. Po udanym skanowaniu klient będzie kontynuował nawiązać połączenia z punktem aktualizacji oprogramowania.

 Na poniższej liście wymieniono dodatkowe informacje, które warto uwzględnić w scenariuszach ponawiania próby połączenia z punktem aktualizacji oprogramowania i przełączania go:  

-   Jeśli klient zostanie odłączony od firmowego intranetu i nie uda mu się przeprowadzić skanowania w poszukiwaniu aktualizacji oprogramowania, nie przełączy się do innego punktu aktualizacji oprogramowania. Jest to oczekiwany błąd, ponieważ nie mając dostępu do sieci firmowej, klient nie ma dostępu do punktu aktualizacji oprogramowania, który umożliwia połączenie z sieci firmowej. Klient programu Configuration Manager określa dostępność intranetowego punktu aktualizacji oprogramowania.  

-   Jeśli jest włączona funkcja internetowego zarządzania klientami i istnieje wiele punktów aktualizacji oprogramowania skonfigurowanych do akceptowania komunikacji od klientów z Internetu, proces przełączania będzie przebiegać tak samo jak standardowy proces ponawiania prób opisany w poprzednim scenariuszu.  

-   Jeśli proces skanowania rozpoczął się, ale przed jego ukończeniem nastąpiło wyłączenie zasilania klienta, nie jest to traktowane jako błąd skanowania ani nie liczy się jako jedna z czterech ponownych prób.  

Gdy programu Configuration Manager odbierze żadnego z następujących kodów błędów systemu Windows Update Agent, będzie mieć ponawiania klienta połączenia:  

2149842970, 2147954429, 2149859352, 2149859362, 2149859338, 2149859344, 2147954430, 2147747475, 2149842974, 2149859342, 2149859372, 2149859341, 2149904388, 2149859371, 2149859367, 2149859366, 2149859364, 2149859363, 2149859361, 2149859360, 2149859359, 2149859358, 2149859357, 2149859356, 2149859354, 2149859353, 2149859350, 2149859349, 2149859340, 2149859339, 2149859332, 2149859333, 2149859334, 2149859337, 2149859336, 2149859335

Aby wyszukać znaczenie kodu błędu, możesz przekonwertować kod dziesiętny błędu w postaci szesnastkowej, a następnie wyszukać wartości szesnastkowej w witrynie takich jak [usługi Windows Update Agent — kody błędów stron typu Wiki](https://social.technet.microsoft.com/wiki/contents/articles/15260.windows-update-agent-error-codes.aspx).


###  <a name="BKMK_ManuallySwitchSUPs"></a>Ręcznie przełączać klientów do nowego punktu aktualizacji oprogramowania
Począwszy od programu Configuration Manager w wersji 1606, możesz włączyć opcję dla klientów programu Configuration Manager, która umożliwia przełączanie do nowego punktu aktualizacji oprogramowania w przypadku wystąpienia problemów z aktywnym punktem aktualizacji oprogramowania. Ta opcja powoduje zmiany tylko wtedy, gdy klient odbierze wiele punktów aktualizacji oprogramowania z punktu zarządzania.

> [!IMPORTANT]    
> Po przełączeniu urządzenia do używania nowego serwera urządzenia używają rezerwowego do znajdowania ten nowy serwer. W związku z tym Przejrzyj konfiguracji grupy granic i upewnij się, że punkty aktualizacji oprogramowania znajdują się w grupach granic poprawne przed rozpoczęciem tej zmiany. Aby uzyskać więcej informacji, zobacz [punktów aktualizacji oprogramowania](/sccm/core/servers/deploy/configure/boundary-groups#software-update-points).
>
> Przełącz do nowego punktu aktualizacji oprogramowania wygeneruje dodatkowy ruch sieciowy. Ilość ruchu zależy od ustawień konfiguracji programu WSUS (klasyfikacje aktualizacji, produkty, czy punkty aktualizacji oprogramowania współdzielą bazę danych usług WSUS, itp.). Jeśli planujesz przełącznika wielu urządzeń, należy wziąć pod uwagę podczas okna obsługi, aby zmniejszyć wpływ do sieci podczas synchronizacji do nowego serwera punktu aktualizacji oprogramowania w ten sposób.

#### <a name="to-enable-the-option-to-switch-software-update-points"></a>Aby włączyć opcję przełączania punktów aktualizacji oprogramowania  
Włącz tę opcję dla kolekcji urządzeń lub zestawu wybranych urządzeń. Po włączeniu tej opcji klienci będą szukać innego punktu aktualizacji oprogramowania podczas kolejnego skanowania.

1.  W konsoli programu Configuration Manager kliknij pozycję **Zasoby i zgodność > Przegląd > Kolekcje urządzeń**.  

2.  Na karcie **Narzędzia główne** w grupie **Kolekcja** kliknij opcję **Powiadomienie klienta**, a następnie kliknij opcję **Przełącz na następny punkt aktualizacji oprogramowania**.  


###  <a name="BKMK_SUP_CrossForest"></a> Punkty aktualizacji oprogramowania w lesie niezaufanym  
 W danej lokacji można utworzyć jeden lub więcej punktów aktualizacji oprogramowania w celu obsługi klientów w lesie niezaufanym. Aby dodać punkt aktualizacji oprogramowania w innym lesie, należy najpierw zainstalować i skonfigurować w tym lesie serwer usług WSUS. Następnie uruchom kreatora w celu dodania serwera lokacji programu Configuration Manager z rolą systemu lokacji punktu aktualizacji oprogramowania. Aby pomyślnie łączyć się z usługami WSUS w lesie niezaufanym, należy skonfigurować w kreatorze następujące ustawienia:  

-   Określić konto instalacji systemu lokacji z dostępem do serwera usług WSUS w lesie.  

-   Określić konto połączenia serwera WSUS, które ma być używane do łączenia się z serwerem usług WSUS.  

 Załóżmy na przykład, że istnieje lokacja główna w lesie A z dwoma punktami aktualizacji oprogramowania (SUP01 i SUP02). Dla tej samej lokacji głównej istnieją też dwa punkty aktualizacji oprogramowania (SUP03 i SUP04) w lesie B. Kiedy w tym przykładzie dojdzie do przełączenia, w pierwszej kolejności zostaną użyte punkty aktualizacji oprogramowania z tego samego lasu co klient.  

###  <a name="BKMK_WSUSSyncSource"></a> Używanie istniejącego serwera usług WSUS jako źródła synchronizacji w lokacji najwyższego poziomu  
 Najczęściej lokację najwyższego poziomu w danej hierarchii konfiguruje się do synchronizowania metadanych aktualizacji oprogramowania z usługą Microsoft Update. Gdy zasady zabezpieczeń firmy nie zezwala na dostęp do Internetu z lokacji najwyższego poziomu, można skonfigurować źródło synchronizacji dla lokacji najwyższego poziomu do użycia istniejący serwer WSUS, który nie znajduje się w hierarchii programu Configuration Manager. Na przykład serwer usług WSUS może być zainstalowany w sieci obwodowej, która ma dostęp do Internetu, mimo że lokacja najwyższego poziomu tego dostępu nie ma. Serwer WSUS w sieci obwodowej można wówczas skonfigurować jako źródło synchronizacji dla metadanych aktualizacji oprogramowania. Pamiętaj, że serwer WSUS w strefie DMZ synchronizuje te aktualizacje oprogramowania, które spełniają kryteria wymagane w hierarchii programu Configuration Manager. W przeciwnym razie lokacja najwyższego poziomu może synchronizować nie te aktualizacje oprogramowania, których się oczekuje. Podczas instalacji punktu aktualizacji oprogramowania należy skonfigurować konto połączenia WSUS mające dostęp do serwera WSUS w sieci obwodowej i potwierdzić, że zapora pozwala na ruch danych przez odpowiednie porty. Aby uzyskać więcej informacji, przejrzyj [porty używane przez punkt aktualizacji oprogramowania ze źródłem synchronizacji](../../core/plan-design/hierarchy/ports.md#BKMK_PortsSUP-WSUS).  

###  <a name="BKMK_NLBSUPSP1"></a> Punkt aktualizacji oprogramowania skonfigurowany do korzystania z równoważenia obciążenia sieciowego  
 Przełączenie punktu aktualizacji oprogramowania zazwyczaj pozwala ustalić potrzebną odporność na uszkodzenia. Domyślnie program Configuration Manager nie obsługuje konfigurowania punktów aktualizacji oprogramowania jako klastrów równoważenia obciążenia Sieciowego. Przed 1702 wersji programu Configuration Manager możesz użyć zestawu SDK programu Configuration Manager można skonfigurować maksymalnie czterech punktów aktualizacji oprogramowania w klastrze równoważenia obciążenia Sieciowego. Jednak począwszy od programu Configuration Manager w wersji 1702 punktów aktualizacji oprogramowania nie są obsługiwane jako klastrów równoważenia obciążenia Sieciowego i uaktualnienia do programu Configuration Manager w wersji 1702 zostanie zablokowane, jeśli zostanie wykryty w tej konfiguracji. Aby uzyskać więcej informacji na temat polecenia cmdlet Set-CMSoftwareUpdatePoint środowiska PowerShell, zobacz [Set-CMSoftwareUpdatePoint](http://go.microsoft.com/fwlink/?LinkId=276834).

###  <a name="BKMK_SUPSecSite"></a> Punkt aktualizacji oprogramowania w lokacji dodatkowej  
 Punkt aktualizacji oprogramowania jest opcjonalny w lokacji dodatkowej. Podczas instalowania punktu aktualizacji oprogramowania w lokacji dodatkowej baza danych programu WSUS jest konfigurowana jako replika domyślnego punktu aktualizacji w nadrzędnej lokacji głównej. W lokacji dodatkowej można zainstalować tylko jeden punkt aktualizacji oprogramowania. Urządzenia przypisane do lokacji dodatkowej są skonfigurowane do używania punktu aktualizacji oprogramowania w lokacji nadrzędnej, gdy ten punkt nie jest zainstalowany w lokacji dodatkowej. Punkt aktualizacji oprogramowania zazwyczaj instaluje się w lokacji dodatkowej, gdy między przypisanymi do niej urządzeniami a punktami aktualizacji oprogramowania w nadrzędnej lokacji głównej występuje ograniczona przepustowość sieci, lub gdy wydajność punktu aktualizacji oprogramowania zbliża się do limitu. Po pomyślnym zainstalowaniu i skonfigurowaniu punktu aktualizacji oprogramowania w lokacji dodatkowej zasady obejmujące całą lokację zostaną zaktualizowane na komputerach klienckich przypisanych do tej lokacji i zaczną używać nowego punktu aktualizacji oprogramowania.  

##  <a name="BKMK_SUPInstallation"></a>Planowanie instalacji punktu aktualizacji oprogramowania  
 Przed utworzeniem roli systemu lokacji punktu aktualizacji oprogramowania w programie Configuration Manager, istnieje kilka wymagań, które należy wziąć pod uwagę w zależności od infrastruktury programu Configuration Manager. Z informacjami w tej sekcji należy się zapoznać w szczególności, gdy punkt aktualizacji oprogramowania został skonfigurowany do komunikacji przy użyciu protokołu SSL. W takim przypadku w celu prawidłowego działania punktów aktualizacji oprogramowania w hierarchii należy wykonać dodatkowe czynności. W tej sekcji opisano czynności, jakie należy wykonać w celu pomyślnego zaplanowania i przygotowania instalacji punktu aktualizacji oprogramowania.  

###  <a name="BKMK_SUPSystemRequirements"></a> Wymagania dotyczące punktu aktualizacji oprogramowania  
 Rolę systemu lokacji punktu aktualizacji oprogramowania musi być zainstalowany w systemie lokacji spełniającym minimalne wymagania dotyczące programu WSUS i obsługiwanych konfiguracji systemów lokacji programu Configuration Manager.  

-   Aby uzyskać więcej informacji o minimalnych wymaganiach dotyczących roli serwera WSUS w systemie Windows Server 2012, zobacz [przejrzyj zagadnienia i wymagania systemowe](https://technet.microsoft.com/library/hh852344.aspx#BKMK_1.1) w bibliotece dokumentacji systemu Windows Server 2012.  

-   Aby uzyskać więcej informacji o obsługiwanych konfiguracjach systemów lokacji programu Configuration Manager, zobacz [lokacji i wymagania wstępne systemu lokacji](../../core/plan-design/configs/site-and-site-system-prerequisites.md).  

###  <a name="BKMK_PlanningForWSUS"></a> Planowanie instalacji programu WSUS  

Aktualizacje oprogramowania wymagają zainstalowania obsługiwanej wersji programu WSUS na wszystkich serwerach systemu lokacji skonfigurowanych w ramach roli systemu lokacji punktu aktualizacji oprogramowania. Jeżeli punkt aktualizacji oprogramowania nie zostanie zainstalowany na serwerze lokacji, należy również zainstalować na komputerze serwera lokacji konsolę administracyjną programu WSUS (jeśli nie jest zainstalowana). Umożliwi to serwerowi lokacji komunikowanie się z programem WSUS uruchomionym w punkcie aktualizacji oprogramowania.  

 Jeśli używasz programu WSUS w systemie Windows Server 2012, należy skonfigurować dodatkowe uprawnienia, aby umożliwić **program WSUS Configuration Manager** sprawdza w programie Configuration Manager mógł łączyć się z programem WSUS w celu okresowego. Aby skonfigurować uprawnienia, wykonaj jedną z następujących czynności:  

-   Dodaj konto **SYSTEM** do grupy **Administratorzy WSUS**  

-   Dodaj konto **ZARZĄDZANIE NT\SYSTEM** jako użytkownika bazy danych programu WSUS (SUSDB) i skonfiguruj co najmniej członkostwo roli bazy danych usługi sieci Web  

 Więcej informacji o sposobie instalowania programu WSUS w systemie Windows Server 2012 znajduje się w temacie [Install the WSUS Server Role](http://go.microsoft.com/fwlink/p/?LinkId=272355) (Instalowanie roli serwera WSUS) w bibliotece dokumentacji dotyczącej programu Windows Server 2012.  

 W przypadku instalowania w lokacji głównej więcej niż jednego punktu aktualizacji oprogramowania należy użyć tej samej bazy danych programu WSUS dla każdego punktu aktualizacji oprogramowania w tym samym lesie usługi Active Directory. Współużytkowanie tej samej bazy danych może znacząco zniwelować wpływ na wydajność klientów i sieci w przypadku, gdy klienci przełączają się na nowy punkt aktualizacji oprogramowania. Kiedy klient przełącza się na nowy punkt aktualizacji oprogramowania, który współużytkuje tę samą bazę danych co stary punkt aktualizacji oprogramowania, skanowanie różnicowe jest nadal wykonywane, ale w znacznie mniejszym zakresie niż w przypadku, gdyby serwer programu WSUS miał własną bazę danych.  

####  <a name="BKMK_CustomWebSite"></a> Konfigurowanie programu WSUS do używania niestandardowej witryny sieci Web  
 Podczas instalowania programu WSUS można użyć istniejącej domyślnej witryny sieci web usług IIS lub utworzyć niestandardową witrynę sieci web programu WSUS. Utwórz niestandardową witrynę sieci Web programu WSUS, tak aby usługi IIS obsługiwały usługi programu WSUS w dedykowanej wirtualnej witrynie sieci, i nie udostępniały tej samej witryny sieci web, który jest używany przez inne systemy lokacji programu Configuration Manager lub inne aplikacje. Jest to szczególnie zalecane w przypadku instalowania roli systemu lokacji punktu aktualizacji oprogramowania na serwerze lokacji. Po uruchomieniu programu WSUS w systemie Windows Server 2012 lub Windows Server 2016, usługi WSUS są skonfigurowane, aby domyślnie używać portu 8530 do połączeń HTTP oraz portu 8531 dla protokołu HTTPS. Te ustawienia portów należy określić podczas tworzenia punktu aktualizacji oprogramowania w lokacji.  

####  <a name="BKMK_WSUSInfrastructure"></a> Używanie istniejącej infrastruktury programu WSUS  
 Można wybrać serwer WSUS, który był aktywny w środowisku przed zainstalowaniem programu Configuration Manager jako punkt aktualizacji oprogramowania. Po skonfigurowaniu punktu aktualizacji oprogramowania należy określić ustawienia synchronizacji. Configuration Manager łączy się z serwerem WSUS, który działa na serwerze punktu aktualizacji oprogramowania i konfiguruje serwer z tymi samymi ustawieniami. Jeśli usługi WSUS są synchronizowane przed został skonfigurowany jako punkt aktualizacji oprogramowania z produktami lub klasyfikacjami nie zostanie skonfigurowana jako część ustawień synchronizacji punktu aktualizacji oprogramowania, aktualizacji oprogramowania w metadanych dla produktów i klasyfikacji zostaną zsynchronizowane ze wszystkich metadanych aktualizacji oprogramowania w bazie danych usług WSUS niezależnie od ustawień synchronizacji skonfigurowanych dla punktu aktualizacji oprogramowania. Z tego powodu w bazie danych mogą znajdować się nieoczekiwane metadane aktualizacji oprogramowania. Takie samo zachowanie wystąpi podczas dodawania produktów i klasyfikacji bezpośrednio w konsoli administracyjnej programu WSUS, a następnie natychmiast zainicjować synchronizację. Co godzinę, domyślnie program Configuration Manager łączy się z usługami WSUS w punkcie aktualizacji oprogramowania i resetuje wszystkie ustawienia, które zostały zmodyfikowane poza programu Configuration Manager. Aktualizacje oprogramowania niezgodne z produktami i klasyfikacjami określonymi w ustawieniach synchronizacji wygasną, a następnie zostaną usunięte z bazy danych lokacji.

 Gdy serwer programu WSUS jest skonfigurowany jako punkt aktualizacji oprogramowania, nie jesteś już można używać go jako autonomiczny serwer programu WSUS. Jeśli potrzebujesz oddzielnych autonomicznego serwera WSUS, który nie jest zarządzany przez program Configuration Manager, musi skonfigurować go na innym serwerze.

####  <a name="BKMK_WSUSAsReplica"></a> Konfigurowanie programu WSUS jako serwera repliki  
 W przypadku utworzenia roli systemu lokacji punktu aktualizacji oprogramowania na serwerze lokacji głównej nie można korzystać z serwera programu WSUS skonfigurowanego jako replika. Gdy serwer WSUS został skonfigurowany jako replika, programu Configuration Manager nie może skonfigurować serwer WSUS i synchronizacji programu WSUS również nie powiedzie się. Po utworzeniu punktu aktualizacji oprogramowania w lokacji dodatkowej programu Configuration Manager konfiguruje serwer tak, aby pełnił funkcję serwera repliki programu WSUS uruchomionego w punkcie aktualizacji oprogramowania w nadrzędnej lokacji głównej. Pierwszy punkt aktualizacji oprogramowania zainstalowany w lokacji głównej jest domyślnym punktem aktualizacji oprogramowania. Dodatkowe punkty aktualizacji oprogramowania w danej lokacji są konfigurowane jako repliki domyślnego punktu aktualizacji oprogramowania.  

####  <a name="BKMK_WSUSandSSL"></a> Czy skonfigurować program WSUS do używania protokołu SSL  
 Użycie protokołu SSL może pomóc w zabezpieczeniu programu WSUS uruchomionego w punkcie aktualizacji oprogramowania. Program WSUS używa protokołu SSL do uwierzytelniania komputerów klienckich oraz podrzędnych serwerów programu WSUS. Program WSUS używa protokołu SSL również do szyfrowania metadanych aktualizacji oprogramowania. W przypadku zabezpieczenia programu WSUS przy użyciu protokołu SSL należy przygotować serwer programu WSUS przed zainstalowaniem punktu aktualizacji oprogramowania.  

 Podczas instalowania i konfigurowania punktu aktualizacji oprogramowania należy wybrać ustawienie **Włącz komunikację SSL z serwerem WSUS** . W przeciwnym razie programu Configuration Manager skonfiguruje usługi WSUS nie należy używać protokołu SSL. W przypadku włączenia protokołu SSL dla usług WSUS uruchamianych w punkcie aktualizacji oprogramowania, usługi WSUS uruchamiane w punkcie aktualizacji oprogramowania dowolnej lokacji podrzędnej muszą również zostać skonfigurowane do używania protokołu SSL.  

###  <a name="BKMK_ConfigureFirewalls"></a> Konfigurowanie zapór  
 Aktualizacje oprogramowania w witrynie administracji centralnej programu Configuration Manager komunikować się z usługami WSUS uruchamianymi w punkcie aktualizacji oprogramowania, które z kolei komunikują się ze źródłem synchronizacji celu synchronizowania aktualizacji oprogramowania metadanych. Punkty aktualizacji oprogramowania w lokacji podrzędnej komunikują się z punktem aktualizacji oprogramowania w lokacji nadrzędnej. Jeśli w lokacji głównej jest więcej niż jeden punkt aktualizacji oprogramowania, dodatkowe punkty aktualizacji oprogramowania muszą komunikować się z pierwszym punktem aktualizacji oprogramowania zainstalowanym w danej lokacji, który jest domyślnym punktem aktualizacji oprogramowania.  

 Zapora może być konieczne jest skonfigurowany do akceptowania portów HTTP lub HTTPS, które są używane przez usługi WSUS w następujących scenariuszach: gdy istnieje firmowa zapora między punktem aktualizacji oprogramowania programu Configuration Manager i Internet; Jeśli masz punkt aktualizacji oprogramowania i jego nadrzędnego źródła synchronizacji; lub jeśli użytkownik ma dodatkowe punkty aktualizacji oprogramowania. Połączenie z usługą Microsoft Update jest zawsze konfigurowane do korzystania z portu 80 w przypadku protokołu HTTP i portu 443 w przypadku protokołu HTTPS. Dla połączenia usług WSUS uruchomionych w punkcie aktualizacji oprogramowania lokacji podrzędnej z usługami WSUS uruchomionymi w punkcie aktualizacji oprogramowania lokacji nadrzędnej można użyć portu niestandardowego. Jeśli stosowane zasady zabezpieczeń nie zezwalają na połączenie, należy użyć metody synchronizacji polegającej na eksporcie i imporcie. Więcej informacji znajduje się w sekcji [Źródło synchronizacji](#BKMK_SyncSource) w tym temacie. Aby uzyskać więcej informacji o portach używanych przez usługi WSUS, zobacz [Jak określić ustawienia portów używane przez program WSUS w programie System Center Configuration Manager](../get-started/install-a-software-update-point.md#wsus-settings).  

#### <a name="restrict-access-to-specific-domains"></a>Ograniczanie dostępu do określonych domen  
 Jeśli w danej organizacji nie zezwala się na otwieranie portów i protokołów dla wszystkich adresów w zaporze oddzielającej punkt aktualizacji oprogramowania aktywnego od Internetu, można ograniczyć (zawęzić) dostęp do następujących domen, tak by usługi WSUS i Aktualizacje automatyczne mogły komunikować się z usługą Microsoft Update:  

-   http://windowsupdate.microsoft.com

-   http://*.windowsupdate.microsoft.com  

-   https://*.windowsupdate.microsoft.com  

-   http://*.update.microsoft.com  

-   https://*.update.microsoft.com  

-   http://*.windowsupdate.com  

-   http://download.windowsupdate.com  

-   http://download.microsoft.com  

-   http://*.download.windowsupdate.com  

-   http://test.stats.update.microsoft.com  

-   http://ntservicepack.microsoft.com  

 Może być konieczne dodanie poniższych adresów do zapory rozdzielającej dwa systemy lokacji w następujących przypadkach: jeśli lokacje podrzędne mają punkt aktualizacji oprogramowania lub jeśli w lokacji istnieje zdalny aktywny internetowy punkt aktualizacji oprogramowania:  

 **Punkt aktualizacji oprogramowania w lokacji podrzędnej**  

-   http://<*nazwy FQDN dla oprogramowania zaktualizować punkt w lokacji podrzędnej*>  

-   https://<*nazwy FQDN dla oprogramowania zaktualizować punkt w lokacji podrzędnej*>  

-   http://<*nazwy FQDN dla oprogramowania zaktualizować punkt w lokacji nadrzędnej*>  

-   https://<*nazwy FQDN dla oprogramowania zaktualizować punkt w lokacji nadrzędnej*>  

##  <a name="BKMK_SyncSettings"></a> Planowanie ustawień synchronizacji  
 Synchronizacja aktualizacji oprogramowania w programie Configuration Manager to proces pobierania metadanych aktualizacji oprogramowania, na podstawie kryteriów, które można skonfigurować. Lokacja najwyższego poziomu w danej hierarchii, centralna lokacja administracyjna lub autonomiczna lokacja główna synchronizuje aktualizacje oprogramowania z usługi Microsoft Update. Istnieje możliwość konfigurowania punktu aktualizacji oprogramowania w lokacji najwyższego poziomu do synchronizowania z istniejącym serwerem usług WSUS spoza hierarchii programu Configuration Manager. Podrzędne lokacje główne synchronizują metadane aktualizacji oprogramowania z punktu aktualizacji oprogramowania w centralnej lokacji administracyjnej. Przed zainstalowaniem i skonfigurowaniem punktu aktualizacji oprogramowania należy posłużyć się tą częścią do zaplanowania ustawień synchronizacji.  

###  <a name="BKMK_SyncSource"></a> Źródło synchronizacji  
 Ustawienia źródła synchronizacji dla punktu aktualizacji oprogramowania określają lokalizację, z której punkt aktualizacji oprogramowania pobiera metadane aktualizacji oprogramowania, a także to, czy podczas procesu synchronizacji są tworzone zdarzenia raportowania usług WSUS.  

-   **Źródło synchronizacji:** Punkt aktualizacji oprogramowania w lokacji najwyższego poziomu domyślnie konfiguruje źródło synchronizacji dla usługi Microsoft Update. Możesz synchronizować lokację najwyższego poziomu z istniejącym serwerem usług WSUS. Punkt aktualizacji oprogramowania w podrzędnej lokacji głównej domyślnie konfiguruje jako źródło synchronizacji punkt aktualizacji oprogramowania w centralnej lokacji administracyjnej.  

    > [!NOTE]  
    >  Pierwszy punkt aktualizacji oprogramowania zainstalowany w lokacji głównej, który jest domyślnym punktem aktualizacji oprogramowania, synchronizuje się z centralną lokacją administracyjną. Dodatkowe punkty aktualizacji oprogramowania w lokacji głównej synchronizują się z domyślnym punktem aktualizacji oprogramowania w lokacji głównej.  

     Kiedy punkt aktualizacji oprogramowania zostanie odłączony od usługi Microsoft Update lub od nadrzędnego serwera aktualizacji, można skonfigurować źródło synchronizacji tak, aby — zamiast synchronizacji ze skonfigurowanym źródłem synchronizacji — do synchronizacji aktualizacji oprogramowania była wykorzystywana funkcja eksportu i importu narzędzia WSUSUtil. Aby uzyskać więcej informacji, zobacz [Synchronizowanie aktualizacji oprogramowania z odłączonego punktu aktualizacji oprogramowania](../get-started/synchronize-software-updates-disconnected.md).  

-   **Zdarzenia raportowania usług WSUS:** Windows Update Agent na komputerach klienckich może tworzyć komunikaty o zdarzeniach, które są używane do raportowania usług WSUS. Te zdarzenia nie są używane przez aktualizację oprogramowania w programie Configuration Manager i w związku z tym **nie twórz zdarzeń do raportowania WSUS** opcja jest domyślnie zaznaczona. Kiedy te zdarzenia nie są tworzone, komputer kliencki powinien łączyć się z serwerem usług WSUS wyłącznie podczas skanowania pod kątem oceny zgodności z aktualizacjami oprogramowania. Jeśli te zdarzenia są potrzebne funkcjom raportowania poza aktualizacjami oprogramowania w programie Configuration Manager, należy zmodyfikować to ustawienie, aby utworzyć zdarzenia raportowania usług WSUS.  

###  <a name="BKMK_SyncSchedule"></a> Harmonogram synchronizacji  
 Harmonogram synchronizacji można skonfigurować tylko w punkcie aktualizacji oprogramowania w lokacji najwyższego poziomu w hierarchii programu Configuration Manager. Po skonfigurowaniu harmonogramu synchronizacji punkt aktualizacji oprogramowania synchronizuje się ze źródłem synchronizacji określonego dnia, o określonym czasie. Harmonogram niestandardowy pozwala na synchronizowanie aktualizacji oprogramowania tego dnia i o tej godzinie, gdy zapotrzebowanie ze strony serwera usług WSUS, serwera lokacji oraz sieci jest niskie, na przykład raz w tygodniu o godzinie 2.00 nad ranem. Można również zainicjować synchronizację w lokacji najwyższego poziomu, wybierając **synchronizacja aktualizacji oprogramowania** akcji z **wszystkie aktualizacje oprogramowania** lub **grup aktualizacji oprogramowania** węzeł w konsoli programu Configuration Manager.  

> [!TIP]  
>  Uruchamianie synchronizacji aktualizacji oprogramowania należy planować w ramach czasowych właściwych dla danego środowiska. Według jednego z typowych scenariuszy harmonogram synchronizowania aktualizacji oprogramowania uruchamia się wkrótce po regularnym wydaniu aktualizacji zabezpieczeń przez firmę Microsoft, co następuje w drugi wtorek każdego miesiąca, popularnie nazywany „wtorkiem poprawek”. Inny typowy scenariusz polega na tym, by ustawić codzienne uruchamianie harmonogramu synchronizowania aktualizacji oprogramowania podczas użycia aktualizacji oprogramowania do dostarczenia aktualizacji aparatu i definicji programu Endpoint Protection.  

 Po tym, gdy punkt aktualizacji oprogramowania pomyślnie ukończy synchronizację, żądanie synchronizacji zostaje wysłane do lokacji podrzędnych. Jeśli w lokacji głównej występują dodatkowe punkty aktualizacji oprogramowania, żądanie synchronizacji jest wysyłane do każdego z nich. Powyższy proces jest powtarzany w każdej lokacji z danej hierarchii.  

###  <a name="BKMK_UpdateClassifications"></a> Klasyfikacje aktualizacji  
 Każdą aktualizację oprogramowania definiuje klasyfikacja aktualizacji, która pomaga organizować aktualizacje w różne typy. Podczas procesu synchronizacji są synchronizowane metadane aktualizacji oprogramowania dla określonych klasyfikacji. Menedżer konfiguracji umożliwia synchronizowanie aktualizacji oprogramowania o następujących klasyfikacjach aktualizacji:  

-   **Aktualizacje krytyczne:** Określa szeroko rozpowszechnianej aktualizacji dotyczącej konkretnego problemu, którego dotyczy krytyczną usterkę niepowiązaną z zabezpieczeń.  

-   **Aktualizacje definicji:** Określenie aktualizacji plików definicji wirusów lub innych plików definicji.  

-   **Pakiety Feature Pack:** Określa nowych funkcji produktów, rozpowszechnianych poza wydaniami oraz funkcji najczęściej uwzględnianych w następnym pełnym wydaniu produktu.  

-   **Aktualizacje zabezpieczeń:** Określa szeroko rozpowszechnianej aktualizacji dotyczącej problemu z konkretnym produktem, związanych z zabezpieczeniami.  

-   **Dodatki Service Pack:** Określenie zbiorczego zestawu poprawek przeznaczonych do aplikacji. Poprawki tego typu mogą obejmować aktualizacje zabezpieczeń, aktualizacje krytyczne, aktualizacje oprogramowania i tak dalej.  

-   **Narzędzia:** Określenie narzędzia lub funkcji pomagających wykonać jedno lub więcej zadań.  

-   **Pakiety zbiorcze aktualizacji:** Określenie zbiorczego zestawu poprawek zebranych w jednym pakiecie w celu łatwiejszego wdrażania. Poprawki tego typu mogą obejmować aktualizacje zabezpieczeń, aktualizacje krytyczne, aktualizacje zwykłe i tak dalej. Pakiet zbiorczy aktualizacji na ogół dotyczy konkretnego obszaru, takiego jak zabezpieczenia czy składnik produktu.  

-   **Aktualizacje:** Określenie aktualizacji aplikacji lub pliku, który jest obecnie zainstalowany.  

 Ustawienia klasyfikacji aktualizacji konfiguruje się tylko w lokacji najwyższego poziomu. Ustawień klasyfikacji aktualizacji nie konfiguruje się w punkcie aktualizacji oprogramowania lokacji podrzędnych, bo metadane aktualizacji oprogramowania ulegają replikacji z lokacji najwyższego poziomu to podrzędnych lokacji głównych. Podczas wybierania klasyfikacji aktualizacji należy pamiętać, że im więcej klasyfikacji zostanie wybranych, tym dłużej będzie przebiegać synchronizowanie metadanych aktualizacji oprogramowania.  

> [!WARNING]  
>  W ramach najlepszych praktyk warto wyczyścić wszystkie klasyfikacje przed synchronizowaniem aktualizacji oprogramowania po raz pierwszy. Po początkowej synchronizacji można wybrać klasyfikacje z właściwości składnika punktu aktualizacji oprogramowania, a następnie ponownie zainicjować synchronizację.  

###  <a name="BKMK_UpdateProducts"></a> Produkty  
 Metadane każdej aktualizacji oprogramowania definiują jeden lub więcej produktów, których dotyczy dana aktualizacja. Produkt to konkretne wydanie systemu operacyjnego lub aplikacji. Przykładem produktu jest system Microsoft Windows Server 2008. Rodzina produktów to podstawowy system operacyjny lub podstawowa aplikacja, od których pochodzą produkty indywidualne. Przykładem rodziny produktów jest Microsoft Windows — rodzina, do której należy system Microsoft Windows Server 2008. Można określać rodziny produktów lub należące do nich produkty indywidualne.  

 Gdy aktualizacje oprogramowania dotyczą wielu produktów, a co najmniej jeden z nich zostanie wybrany do synchronizacji, wszystkie produkty będą wyświetlane w konsoli programu Configuration Manager, nawet jeśli część z nich nie zostały wybrane. Jeśli na przykład jedynym systemem operacyjnym objętym subskrypcją jest system Windows Server 2012, a aktualizacja oprogramowania dotyczy systemów Windows Server 2012 i Windows Server 2012 Datacenter Edition, obydwa te produkty pojawią się w bazie danych lokacji.  

 Ustawienia produktów konfiguruje się tylko w lokacji najwyższego poziomu. Ustawień produktów nie konfiguruje się w punkcie aktualizacji oprogramowania lokacji podrzędnych, bo metadane aktualizacji oprogramowania ulegają replikacji z lokacji najwyższego poziomu to podrzędnych lokacji głównych. Podczas wybierania produktów należy pamiętać, że im więcej produktów zostanie wybranych, tym dłużej będzie przebiegać synchronizowanie metadanych aktualizacji oprogramowania.  

> [!IMPORTANT]  
>  Program Configuration Manager przechowuje listę produktów i rodzin produktów, które można wybrać podczas pierwszej instalacji punktu aktualizacji oprogramowania. Produkty i rodziny produktów wydane po wydaniu programu Configuration Manager mogą nie być dostępne do wybrania, dopóki nie zostanie ukończona synchronizacja aktualizacji oprogramowania, które aktualizuje listę dostępnych produktów i rodzin produktów, spośród których można dokonać wyboru. W ramach najlepszych praktyk warto wyczyścić wszystkie produkty przed synchronizowaniem aktualizacji oprogramowania po raz pierwszy. Po początkowej synchronizacji można wybrać produkty z właściwości składnika punktu aktualizacji oprogramowania, a następnie ponownie zainicjować synchronizację.  

###  <a name="BKMK_SupersedenceRules"></a>Zasady zastępowania  
 Najczęściej aktualizacja oprogramowania zastępująca inną aktualizację oprogramowania wykonuje jedno lub więcej z następujących działań:  

-   Wzbogaca, usprawnia lub aktualizuje poprawkę udostępnioną przez jedną lub więcej wcześniej wydanych aktualizacji.  

-   Jeśli aktualizacja zostanie zatwierdzona do instalacji, zostanie zwiększona wydajność zastąpionego pakietu aktualizacji plików, który jest zainstalowany na komputerach klienckich. Przykładowo zastąpiona aktualizacja może zawierać pliki, które nie mają już zastosowania do poprawki lub systemów operacyjnych obsługiwanych przez nową aktualizację. Dlatego pliki te zostały usunięte z pakietu, który został zastąpiony.  

-   Aktualizuje nowe wersje produktu. Innymi słowy aktualizuje wersje, które nie mają już zastosowania do starszych wersji lub konfiguracji produktu. Jeśli zostały wprowadzone zmiany rozszerzające zakres obsługiwanych języków, aktualizacje mogą także zastąpić inne aktualizacje. Przykładowo starsza wersja aktualizacji pakietu Microsoft Office może usuwać obsługę starszych systemów operacyjnych, lecz i dodawać obsługę języków, których nie było w pierwotnej wersji.  

 We właściwościach punktu aktualizacji oprogramowania można określić, że zastępowane aktualizacje oprogramowania mają być natychmiast uznawane za wygasłe, co zapobiega włączaniu ich w nowe wdrożenia oraz flaguje istniejące wdrożenia i wskazuje, że zawierają one przynajmniej jedną wygasłą aktualizację oprogramowania. Alternatywnie można też wskazać okres czasu, jaki ma upłynąć przed uznaniem zastąpionych aktualizacji oprogramowania za wygasłe, co pozwala nadal je wdrażać. Warto rozważyć następujące scenariusze, w których konieczne może być wdrożenie zastąpionej aktualizacji oprogramowania:  

-   Jeśli nowsza aktualizacja oprogramowania obsługuje tylko nowsze wersje systemu operacyjnego, a niektórzy klienci działają pod kontrolą starszej wersji systemu.  

-   Jeśli nowsza aktualizacja oprogramowania ma ograniczoną funkcjonalność w porównaniu do zastępowanej. Może to być nieodpowiednie u niektórych klientów.  

-   Jeśli zastępowana aktualizacja oprogramowania nie została zatwierdzona do wdrożenia w środowisku produkcyjnym.  

    > [!NOTE]  
    >  Gdy ustawia zastąpionej aktualizacji oprogramowania programu Configuration Manager **ważność**, nie ustawia aktualizacji **ważność** w usługach WSUS. Jednakże, gdy zostanie uruchomione zadanie oczyszczania usług WSUS, aktualizacje ustawioną **ważność** w programie Configuration Manager są ustawione na stan **odrzucone** w programie WSUS server i Windows Update Agent na komputerach nie będzie więcej wyszukiwać tych aktualizacji. Oznacza to, że klienci będą nadal skanowania pod kątem wygasłych aktualizacji do momentu uruchamia zadanie oczyszczania. Aby uzyskać informacje na temat zadanie oczyszczania usług WSUS, zobacz [obsługi aktualizacji oprogramowania](/sccm/sum/deploy-use/software-updates-maintenance).

###  <a name="BKMK_UpdateLanguages"></a> Języki  
 Ustawienia języka w punkcie aktualizacji oprogramowania pozwala na skonfigurowanie języków, dla których szczegóły podsumowania (metadane aktualizacji oprogramowania) są synchronizowane z aktualizacjami oprogramowania, oraz wersji językowych aktualizacji oprogramowania, które zostaną pobrane.  

#### <a name="software-update-file"></a>Plik z aktualizacją oprogramowania  
 Języki skonfigurowane w opcji **Plik z aktualizacją oprogramowania** we właściwościach punktu aktualizacji oprogramowania pozwalają na wybranie domyślnego zestawu wersji językowych dostępnych przy pobieraniu aktualizacji oprogramowania w lokacji. Istnieje możliwość zmiany języków wybieranych domyślnie za każdym razem, gdy są pobierane lub wdrażane aktualizacje oprogramowania. Jeśli pliki z aktualizacją oprogramowania są dostępne w wybranym języku, to podczas pobierania odpowiednie pliki we właściwych skonfigurowanych językach zostaną pobrane do lokacji źródłowej pakietu wdrożeniowego. Następnie pliki te są kopiowane do biblioteki zawartości na serwerze lokacji i do punktów dystrybucji skonfigurowanych dla danego pakietu.  

 Ustawienia języka pliku z aktualizacją oprogramowania należy skonfigurować pod kątem języków najczęściej używanych w danym środowisku. Przykładowo jeśli klienci przypisani do lokacji mają systemy operacyjne i aplikacje w większości w języku angielskim i japońskim, a inne języki prawie nie są używane w danej lokacji, w kolumnie **Plik z aktualizacją oprogramowania** wybierz języki angielski i japoński przy pobieraniu lub aktualizacji oprogramowania i usuń zaznaczenie innych języków. Pozwoli to na wybranie domyślnych ustawień na stronie **Wybór języka** w Kreatorach wdrażania i pobierania. Dzięki temu można także uniknąć pobierania niepotrzebnych plików. To ustawienie jest konfigurowane w każdym punkcie aktualizacji oprogramowania w hierarchii programu Configuration Manager.  

#### <a name="summary-details"></a>Szczegóły podsumowania  
 W trakcie procesu synchronizacji informacje ze szczegółami podsumowania (metadane aktualizacji oprogramowania) zostaną zaktualizowane dla aktualizacji oprogramowania w wybranych językach. Metadane zapewniają informacje o aktualizacjach oprogramowania, takich jak nazwa, opis, produkty obsługiwane przez aktualizacje, klasyfikacje aktualizacji, identyfikator artykułu, adres URL pobierania, reguły stosowania itd.  

 Ustawienie ze szczegółami podsumowania jest konfigurowane tylko w lokacji najwyższego poziomu. Szczegóły podsumowania nie są konfigurowane w punkcie aktualizacji oprogramowania w lokacjach podrzędnych, ponieważ metadane aktualizacji oprogramowania są replikowane z centralnej lokacji administracyjnej do tych lokacji za pomocą replikacji plikowej. Przy wybieraniu języków ze szczegółami podsumowania należy wybrać tylko te języki, które są potrzebne w danym środowisku. Podczas wybierania języków należy pamiętać, że im więcej języków zostanie wybranych, tym dłużej będzie przebiegać synchronizowanie metadanych aktualizacji oprogramowania. Menedżer konfiguracji Wyświetla metadane aktualizacji oprogramowania w ustawieniach regionalnych systemu operacyjnego, w którym jest uruchomiona konsola programu Configuration Manager. Jeśli zlokalizowane właściwości aktualizacji oprogramowania nie są dostępne w ustawieniach regionalnych systemu operacyjnego, informacje te zostaną wyświetlone po angielsku.  

> [!IMPORTANT]  
>  Należy wybrać wszystkie języki szczegółów podsumowania, które będą potrzebne w hierarchii programu Configuration Manager. Jeśli punkt aktualizacji oprogramowania w lokacji najwyższego poziomu jest synchronizowany ze źródłem synchronizacji, wybrane języki szczegółów podsumowania określą pobierane metadane aktualizacji oprogramowania. Modyfikacja języków ze szczegółami podsumowania po realizacji przynajmniej jednej synchronizacji oznacza, że metadane aktualizacji oprogramowania będą pobierane dla zmodyfikowanych języków wyłącznie w zakresie nowych lub uaktualnionych aktualizacji oprogramowania. Aktualizacje oprogramowania, które zostały już zsynchronizowane, nie zostaną zaktualizowane o nowe metadane dla zmodyfikowanych języków, chyba że wystąpi zmiana w aktualizacjach oprogramowania w źródle synchronizacji.  

##  <a name="BKMK_MaintenanceWindow"></a> Planowanie okna obsługi aktualizacji oprogramowania  
 Istnieje możliwość dodania okna obsługi przeznaczonego do instalacji aktualizacji oprogramowania. Pozwala to na konfigurowanie ogólnego okna obsługi oraz innych okien obsługi na potrzeby aktualizacji oprogramowania. W przypadku skonfigurowania zarówno ogólnego okna obsługi, jak i okna obsługi aktualizacji oprogramowania, klienci instalują aktualizacje oprogramowania tylko przy otwartym oknie obsługi aktualizacji oprogramowania. Aby uzyskać więcej informacji dotyczących okien obsługi, zobacz [używanie okien obsługi](../../core/clients/manage/collections/use-maintenance-windows.md).  

##  <a name="BKMK_RestartOptions"></a> Ponowne uruchamianie dla klientów z systemem Windows 10 po instalacji aktualizacji oprogramowania
Gdy aktualizacja oprogramowania wymaga ponowne uruchomienie jest wdrażany przy użyciu programu Configuration Manager i zainstalowany na komputerze, oczekuje na ponowne uruchomienie zostało zaplanowane i zostanie wyświetlone okno dialogowe ponownego uruchomienia.

Począwszy od programu Configuration Manager w wersji 1606, opcje **Zaktualizuj i uruchom ponownie**i **Zaktualizuj i zamknij** są dostępne na komputerach z systemem Windows 10 w opcjach zasilania systemu Windows zawsze wtedy, gdy istnieje oczekujące ponowne uruchomienie dla aktualizacji oprogramowania programu Configuration Manager. W przypadku skorzystania z dowolnej z tych opcji okno dialogowe ponownego uruchamiania nie zostanie wyświetlone po ponownym uruchomieniu komputera.

W poprzednich wersjach programu Configuration Manager, gdy oczekuje na ponowne uruchomienie systemu Windows 8 i nowszych komputerów i gdy zamknięcie lub ponowne uruchomienie komputera przy użyciu opcji zasilania systemu Windows (zamiast z okna dialogowego ponownego uruchomienia), pozostaje okno dialogowe ponownego uruchomienia po ponownym uruchomieniu komputera i komputera nadal będzie konieczne ponowne uruchomienie po osiągnięciu terminu.

## <a name="next-steps"></a>Następne kroki
Po planowania aktualizacji oprogramowania, zapoznaj się z [przygotowanie do oprogramowania aktualizuje zarządzania](../get-started/prepare-for-software-updates-management.md).

