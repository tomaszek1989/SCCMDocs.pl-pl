---
title: "Znajdowania zasobów lokacji"
titleSuffix: Configuration Manager
description: "Dowiedz się, jak i kiedy klienci programu System Center Configuration Manager używają lokalizacji usług do znajdowania zasobów lokacji."
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ae72df4b-5f5d-4e19-9052-bda28edfbace
caps.latest.revision: "10"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: d0cbaf0b9f10926015cf203dbb28633976034162
ms.sourcegitcommit: ca9d15dfb1c9eb47ee27ea9b5b39c9f8cdcc0748
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2018
---
# <a name="learn-how-clients-find-site-resources-and-services-for-system-center-configuration-manager"></a>Dowiedz się, jak klienci znajdują zasoby i usługi programu System Center Configuration Manager lokacji

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

W procesie nazywanym Użyj klientów System Center Configuration Manager *usługi lokalizacji* do zlokalizowania systemu lokacji serwery, które mogą się komunikować i które zapewniają usługi, której klienci są kierowane do użycia. Zrozumienie, jak i kiedy klienci używają lokalizacji usług do znajdowania zasobów lokacji może pomóc Ci w skonfigurowaniu lokacji pod kątem pomyślnej obsługi zadań klienta. Te konfiguracje mogą wymagać interakcji lokacji z konfiguracjami domeny i sieci, takich jak usług domenowych w usłudze Active Directory (AD DS) i DNS. Lub może ich wymagają skonfigurowania bardziej złożonych alternatyw.  

 Przykłady ról systemu lokacji, które udostępniają usługi:

 - Podstawowy serwer systemu lokacji dla klientów.
 - Punkt zarządzania.
 - Dodatkowe serwery systemu lokacji, które klient może się komunikować, takie jak punkty dystrybucji i punkty aktualizacji oprogramowania.  



##  <a name="bkmk_fund"></a> Fundamentals of service location  
 Klient ocenia jego bieżącej lokalizacji sieciowej, preferencji protokołu komunikacji i przypisanej lokacji, gdy używa lokalizacji usługi można znaleźć punktu zarządzania, który może komunikować się z.  

 **Klient komunikuje się z punktem zarządzania w celu:**  
-   Pobieranie informacji o innych punktach zarządzania lokacji, może utworzyć listę punktów zarządzania znane (nazywane *lista*) dla przyszłych usługi lokalizacji cykli.  
-   Przekaż szczegółów konfiguracji, takich jak spisu i stanu.  
-   Pobierz zasadę, która ustawia konfiguracje na kliencie i może poinformować klienta oprogramowania, które można, lub należy zainstalować i inne zadania pokrewne.  
-   Żądanie informacji o dodatkowych lokacji role systemu, które udostępniają usługi, które klient został skonfigurowany do użycia. Przykłady obejmują punktów dystrybucji oprogramowania, które można zainstalować klienta lub punktu aktualizacji oprogramowania, z którego można pobrać aktualizacji.  

**Klient programu Configuration Manager wysyła żądanie lokalizacji usługi:**  
-   Co 25 godzin pracy w trybie ciągłym.  
-   Jeśli klient wykryje zmiany w konfiguracji sieci lub lokalizacji.  
-   Gdy **ccmexec.exe** uruchamia usługę na komputerze (usługi podstawowej klienta).  
-   Gdy klient musi zlokalizować Rola systemu lokacji, która dostarcza wymagane usługi.  

**Gdy klient próbuje odnaleźć serwery hostujące role systemu lokacji**, używa lokalizacji usługi można znaleźć roli systemu lokacji, który obsługuje protokół klienta (HTTP lub HTTPS). Domyślnie klienci używają najbezpieczniejszej dostępnej dla nich metody. Rozważ następujące opcje:  

-   Zastosowanie protokołu HTTPS wymaga skonfigurowania infrastruktury kluczy publicznych (PKI) i instalacji certyfikatów PKI na klientach i serwerach. Aby uzyskać informacje o używaniu certyfikatów, zobacz [Wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager](../../../core/plan-design/network/pki-certificate-requirements.md).  

-   Podczas wdrażania roli systemu lokacji, która korzysta z internetowych usług informacyjnych (IIS) i obsługuje komunikację od klientów, należy określić, czy klienci łączą się z systemem lokacji przy użyciu protokołu HTTP, czy HTTPS. W przypadku wybrania protokołu HTTP należy również skonfigurować opcje podpisywania i szyfrowania. Aby uzyskać więcej informacji, zobacz [planowanie podpisywania i szyfrowania](../../../core/plan-design/security/plan-for-security.md#BKMK_PlanningForSigningEncryption) w [Planowanie zabezpieczeń w programie System Center Configuration Manager](../../../core/plan-design/security/plan-for-security.md).  

##  <a name="BKMK_Plan_Service_Location"></a>Lokalizacja usługi i jak klienci określają przypisanego punktu zarządzania  
Gdy klient najpierw jest przypisany do lokacji głównej, wybiera domyślny punkt zarządzania dla tej lokacji. Lokacje główne obsługują wiele punktów zarządzania, a każdy klient niezależnie identyfikuje punkt zarządzania jako swój domyślny punkt zarządzania. Ten domyślny punkt zarządzania staje się tego klienta przypisanego punktu zarządzania. (Umożliwia także polecenia instalacji klienta można ustawić przypisanego punktu zarządzania dla klienta, gdy jest zainstalowany.)  

Klient wybiera punkt zarządzania do komunikacji z oparte na klienta bieżącej lokalizacji i granic grupy konfiguracji sieci. Nawet jeśli ma przypisany punkt zarządzania, to może być używany przez klienta punktu zarządzania.  

    > [!NOTE]  
    >  A client always uses the assigned management point for registration messages and certain policy messages, even when other communications are sent to a proxy or local management point.  

Możesz użyć preferowanych punktów zarządzania. Preferowane punkty zarządzania to punkty zarządzania z przypisanej lokacji klienta, które są skojarzone z grupą granic, co klient używa do wyszukiwania serwerów systemu lokacji. Preferowanego punktu zarządzania w połączeniu z granicy grupy jako serwer systemu lokacji jest podobny do sposobu punkty dystrybucji lub punkty migracji stanu są skojarzone z grupą granic. Gdy po włączeniu w hierarchii preferowanych punktów zarządzania klient będzie chciał użyć punktu zarządzania z przypisanej do niego lokacji, podejmie próbę użycia preferowanego punktu zarządzania przed użyciem innych punktów zarządzania z przypisanej do niego lokacji.  

Umożliwia również informacje zawarte w [koligacji punktu zarządzania](http://blogs.technet.com/b/jchalfant/archive/2014/09/22/management-point-affinity-added-in-configmgr-2012-r2-cu3.aspx) blogu w witrynie TechNet.com w celu skonfigurowania koligacji punktów zarządzania. Zastąpienia koligacja punktu zarządzania domyślne zachowanie dla przypisanych zarządzania punkty i umożliwia klienta Użyj co najmniej jeden punkt zarządzania określonymi.  

Zawsze, gdy klient musi skontaktować się z punktem zarządzania, sprawdza listy punktów zarządzania, którą przechowuje lokalnie w Instrumentacji zarządzania Windows (WMI). Klient tworzy wstępną listę po jej zainstalowaniu. Klient następnie okresowo aktualizuje listę przy użyciu szczegółów dotyczących poszczególnych punktów zarządzania w hierarchii.  

Gdy klient nie może znaleźć prawidłowego punktu zarządzania na swojej liście pakietu administracyjnego, przeszukuje następujące źródła lokalizacji usługi, w kolejności, aż do znalezienia punktu zarządzania, której można użyć:  

1.  Punkt zarządzania  
2.  USŁUGI AD DS  
3.  systemem DNS,  
4.  WINS  

Po klient pomyślnie zlokalizuje i skontaktuje się z punktem zarządzania, pobiera bieżącą listę punktów zarządzania, które są dostępne w hierarchii i aktualizuje lokalną listę punktów. Dotyczy to zarówno klientów przyłączonych do domeny, jak i nieprzyłączonych.  

Na przykład gdy klient programu Configuration Manager, który jest połączony z Internetem łączy się z punktem zarządzania internetowego, punkt zarządzania wysyła temu klientowi listę dostępnych internetowych punktów zarządzania w lokacji. Podobnie klienci przyłączeni do domeny lub znajdujący się w grupach roboczych również otrzymują listę punktów zarządzania, których mogą użyć.  

Nie podano punktów zarządzania dostępnych — tylko na internetowe klienta, który nie jest skonfigurowany do korzystania z Internetu. Klienci grup roboczych skonfigurowanych do korzystania z Internetu komunikują się tylko z punktami zarządzania skierowane do Internetu.  

##  <a name="BKMK_MPList"></a> Lista punktów zarządzania  
Lista punktów zarządzania jest preferowany usługi źródło lokalizacji dla klienta, ponieważ jest priorytetową listą punktów zarządzania zidentyfikowanych uprzednio przez klienta. Ta lista jest sortowana przez każdego klienta na podstawie jego lokalizacji w momencie aktualizacji listy przez klienta, a następnie zapisywana lokalnie na kliencie w usłudze WMI.  

### <a name="building-the-initial-mp-list"></a>Tworzenie początkowej listy punktów zarządzania  
Podczas instalacji klienta następujące zasady są używane do tworzenia początkowej listy punktów zarządzania klienta:  

-   Początkowa lista zawiera punkty zarządzania określone podczas instalacji klienta (Jeśli używasz **SMSMP**= lub **/MP** opcja).  
-   Klient wysyła zapytanie do usługi AD DS opublikowanych punktów zarządzania. Identyfikację z usług AD DS, punkt zarządzania musi być z przypisanej lokacji klienta, a musi być w tej samej wersji produktu co klient.  
-   Jeśli żaden punkt zarządzania został określony podczas instalacji klienta, a schemat usługi Active Directory nie zostanie rozszerzony, klient sprawdza serwery DNS i WINS o opublikowane punkty zarządzania.  
-   Gdy klient tworzy listę początkowej, informacje o niektórych punktach zarządzania w hierarchii nie mogą być znane.  

### <a name="organizing-the-mp-list"></a>Organizowanie listy punktów zarządzania  
Klienci organizują swoje listy punktów zarządzania przy użyciu następujących klasyfikacjach:  

-   **Serwer proxy**: Punkt zarządzania w lokacji dodatkowej.  
-   **Lokalne**: Dowolny punkt zarządzania, który jest skojarzony z bieżącą lokalizacją sieciową klienta zdefiniowaną przez granice lokacji. Należy uwzględnić następujące informacje dotyczące granic:
    -   Jeśli klient należy do więcej niż jednej grupy granic, lista lokalnych punktów zarządzania lokalnego jest określana na podstawie połączenia wszystkich granic obejmujących bieżącą lokalizację sieciową klienta.  
    -   Punkty zarządzania lokalnego są to zazwyczaj podzbiór klienta przypisanych punktów zarządzania, chyba że klient znajduje się w lokalizacji sieciowej, która jest skojarzona z inną lokalizacją z punktami zarządzania obsługującymi jego grupę granic.   


-   **Przypisane**: Dowolny punkt zarządzania będący systemem lokacji przypisanej lokacji klienta.  

Możesz użyć preferowanych punktów zarządzania. Punkty zarządzania w lokacji, które nie są skojarzone z grupą granic ani nie znajdują się w grupie granic skojarzonej z bieżącą lokalizacją sieciową klienta nie są uważane za preferowane. Będą one być używane, gdy klient nie może zidentyfikować dostępnego preferowanego punktu zarządzania.  

### <a name="selecting-a-management-point-to-use"></a>Wybieranie używanego punktu zarządzania  
W przypadku typowej komunikacji klient próbuje użyć punktu zarządzania z klasyfikacji w poniższej kolejności, bazując na lokalizacji sieciowej klienta:  

1.  Proxy  
2.  Lokalny  
3.  przypisanych  

Jednak klient zawsze używa przypisanego punktu zarządzania dla komunikatów rejestracji i niektórych komunikatów zasad, nawet jeśli pozostała komunikacja jest przesyłana do punktu zarządzania proxy lub lokalnego.  

W ramach każdej klasyfikacji (proxy, lokalne i przypisane) klient próbuje użyć punktu zarządzania na podstawie preferencji, w następującej kolejności:  

1.  Obsługa protokołu HTTPS w lesie zaufanym lub lokalnym (jeśli klient jest skonfigurowany do komunikacji HTTPS)  
2.  Obsługa protokołu HTTPS poza lasem zaufanym lub lokalnym (Jeśli klient jest skonfigurowany do komunikacji HTTPS)  
3.  Obsługa protokołu HTTP w lesie zaufanym lub lokalnym  
4.  Obsługa protokołu HTTP nie znajduje się w lesie zaufanym lub lokalnym  

Z tego zestawu punktów zarządzania posortowanego według preferencji klienci podejmują próbę użycia pierwszego punktu zarządzania na liście. Ta posortowana lista punktów zarządzania jest losowa i nie może zostać określona. Zawsze klient aktualizuje swoją listę MP, można zmienić kolejność listy.  

Gdy klient nie może nawiązać kontaktu z pierwszym punktem zarządzania, podejmuje kolejnych punktów zarządzania na swojej liście. Próbuje każdego preferowanego punktu zarządzania w klasyfikacji przed punktami niepreferowanymi. Jeśli klient nie może pomyślnie komunikować się z żadnym punktem zarządzania w klasyfikacji, próbuje skontaktować się z preferowanym punktem zarządzania z następnej klasyfikacji i tak dalej, aż do znalezienia punktu zarządzania do użycia.  

Po klient nawiąże komunikację z punktem zarządzania, nadal używać, że punkt zarządzania tej samej, aż do:  

-   upłynie 25 godzin.  
-   Klient nie może nawiązać połączenia z punktem zarządzania dla 5 próbach w okresie 10 minut.

Klient następnie losowo wybiera nowy punkt zarządzania do użycia.  

##  <a name="bkmk_ad"></a> Active Directory  
Klienci przyłączeni do domeny mogą używać usług AD DS na potrzeby lokalizacji usług. Wymaga to od lokacji [publikowania danych w usłudze Active Directory](http://technet.microsoft.com/library/hh696543.aspx).  

Klient może używać usług AD DS w celu lokalizacji usługi, gdy są spełnione wszystkie następujące warunki:  

-   Usługi Active Directory [schemat został rozszerzony](https://technet.microsoft.com/library/mt345589.aspx) lub przedłużony dla programu System Center 2012 Configuration Manager.  
-   [Lasu usługi Active Directory jest skonfigurowany do publikowania](http://technet.microsoft.com/library/hh696542.aspx), oraz Lokacje programu Configuration Manager są skonfigurowane do publikowania.  
-   Komputer kliencki jest członkiem domeny usługi Active Directory i może uzyskać dostęp do serwera wykazu globalnego.  

Jeśli klient nie może znaleźć punktu zarządzania na potrzeby lokalizacji usługi z usług AD DS, próbuje użyć DNS.  

##  <a name="bkmk_dns"></a> DNS  
Klienci w intranecie mogą używać serwera DNS do lokalizacji usług. Wymagane jest, by co najmniej jedna lokacja w hierarchii publikowała informacje na temat punktów zarządzania na serwerze DNS.  

Należy rozważyć zastosowanie serwera DNS na potrzeby lokalizacji usług, jeśli spełniono następujące warunki:
-   Schemat usług AD DS nie jest rozszerzony do obsługi programu Configuration Manager.
-   Klienci w sieci intranet znajdują się w lesie, który nie jest włączony do opublikowania programu Configuration Manager.  
-   Klienci znajdują się na komputerach grupy roboczej i nie są skonfigurowani do zarządzania klientami wyłącznie przez Internet. (Klient grupy roboczej skonfigurowany do korzystania z Internetu będą komunikować się tylko z punktami zarządzania połączonych z Internetem i nie zostanie użyty system DNS w celu lokalizacji usługi).  
-   Można [skonfigurować klientów do wyszukiwania punktów zarządzania przy użyciu serwera DNS](http://technet.microsoft.com/library/gg682055).  

Jeśli lokacja publikuje rekordy lokalizacji usług dla punktów zarządzania na serwerze DNS:  

-   Publikowanie ma zastosowanie tylko do punktów zarządzania, które akceptują połączenia klientów z intranetu.  
-   Publikowanie dodaje rekord zasobu lokalizacji usługi (SRV RR) w strefie DNS komputera punktu zarządzania. Na serwerze DNS musi występować wpis hosta odpowiadający danemu komputerowi.  

Domyślnie klientów przyłączonych do domeny wyszukiwanie DNS rekordów punktów zarządzania z domeny lokalnej klienta. Można skonfigurować właściwości klienta, która określa sufiks domeny dla domeny, która zawiera dane publikowane na serwerze DNS punktów zarządzania.  

Aby uzyskać więcej informacji o sposobie konfigurowania sufiksu DNS we właściwości klienta, zobacz [sposobu konfigurowania komputerów klienckich do wyszukiwania punktów zarządzania przy użyciu publikowania DNS w programie System Center Configuration Manager](../../../core/clients/deploy/configure-client-computers-to-find-management-points-by-using-dns-publishing.md).  

Jeśli klient nie może znaleźć punktu zarządzania na potrzeby lokalizacji usługi przy użyciu serwera DNS, próbuje korzystać z usługi WINS.  

### <a name="publish-management-points-to-dns"></a>Publikowanie punktów zarządzania w systemie DNS  
Aby publikować punkty zarządzania w systemie DNS, należy spełnić następujące dwa warunki:  

-   Serwery DNS obsługują rekordy zasobów lokalizacji usługi przy użyciu oprogramowania BIND w wersji 8.1.2 lub nowszej.  
-   Intranetowe nazwy FQDN określone dla punktów zarządzania w programie Configuration Manager mają wpisy hosta (na przykład rekordy) w systemie DNS.  

> [!IMPORTANT]  
>  Publikowanie DNS programu Configuration Manager nie obsługuje rozłącznego obszaru nazw. Jeśli masz rozłącznego obszaru nazw można ręcznie publikować punkty zarządzania w systemie DNS lub użyj jednej z innych metod lokalizacji usługi, które są udokumentowane w tej sekcji.  

**Jeżeli serwery DNS obsługują aktualizacje automatyczne**, można skonfigurować programu Configuration Manager do automatycznego publikowania punktów zarządzania w intranecie w systemie DNS lub można ręcznie opublikować te rekordy w systemie DNS. W przypadku publikowania punktów zarządzania w systemie DNS ich intranetowa nazwa FQDN i numer portu są publikowane w rekordzie lokalizacji usługi (SRV). Możesz skonfigurować publikowanie DNS w witrynie właściwości składnika punktu zarządzania lokacji. Aby uzyskać więcej informacji, zobacz [lokacji składników programu System Center Configuration Manager](../../../core/servers/deploy/configure/site-components.md).  

**Jeśli strefy DNS ma wartość "Secure tylko" dla aktualizacji dynamicznych**, aby pomyślnie wykonać tylko pierwszy punkt zarządzania do publikowania DNS przy użyciu domyślnych uprawnień.

Jeśli tylko jeden punkt zarządzania może pomyślnie publikowanie i zmianę jego rekordu DNS i serwerze punktu zarządzania jest w dobrej kondycji, klienci mogą korzystać z pełną listą pakietu administracyjnego z czy punkt zarządzania, a następnie znajdź ich preferowanego punktu zarządzania.


**Jeżeli serwery DNS nie obsługują aktualizacji automatycznych, ale obsługują rekordy lokalizacji usług**, punkty zarządzania można publikować w systemie DNS ręcznie. W tym celu należy ręcznie określić rekord zasobów lokalizacji usługi (SRV RR) w systemie DNS.  

Program Configuration Manager obsługuje RFC 2782 rekordy lokalizacji usługi. Te rekordy mają następujący format: *_usługa._proto.Nazwa TTL klasa SRV priorytet waga Port cel*  

Aby opublikować punkt zarządzania do programu Configuration Manager, określ następujące wartości:  

-   **_Usługa**: Wprowadź **_mssms_mp**_&lt;kod_lokacji\>, gdzie &lt;kod_lokacji\> oznacza kod lokacji punktu zarządzania.  
-   **._Proto**: Określ **._tcp**.  
-   **. Nazwa**: Wprowadź sufiks DNS punktu zarządzania, na przykład **contoso.com**.  
-   **CZAS WYGAŚNIĘCIA**: Wprowadź **14400**, która odpowiada czterem godzinom.  
-   **Klasa**: Określ **IN** (zgodnie ze standardem RFC 1035).  
-   **Priorytet**: Menedżer konfiguracji nie korzysta z tego pola.
-   **Waga**: Menedżer konfiguracji nie korzysta z tego pola.  
-   **Port**: Wprowadź numer portu, którego używa punkt zarządzania, na przykład **80** dla protokołu HTTP i **443** dla protokołu HTTPS.  

    > [!NOTE]  
    >  Port rekordu SRV powinien odpowiadać portowi komunikacyjnemu, używanego przez punkt zarządzania. Domyślnie jest to **80** dla komunikacji HTTP i **443** dla komunikacji HTTPS.  

-   **Docelowy**: Wprowadź intranetową nazwę FQDN określoną dla systemu lokacji skonfigurowanego przy użyciu roli lokacji punktu zarządzania.  

W przypadku używania systemu DNS w ramach systemu Windows Server można wprowadzić rekord DNS dla intranetowych punktów zarządzania, wykonując czynności opisane w poniższej procedurze. W przypadku stosowania innej implementacji systemu DNS, w celu zastosowania tej procedury należy skorzystać z informacji dotyczących wartości pól w tej sekcji oraz zapoznać się z dokumentacją systemu DNS.  

##### <a name="to-configure-automatic-publishing"></a>Aby skonfigurować publikowanie automatyczne:  

1.  W konsoli programu Configuration Manager, rozwiń węzeł **administracji** > **konfiguracja lokacji** > **witryny**.  

2.  Wybierz lokację, a następnie wybierz pozycję **Konfiguruj składniki lokacji**.  

3.  Wybierz **punkt zarządzania**.  

4.  Wybierz punkty zarządzania, które chcesz opublikować. (Wybór ten dotyczy publikowania w usługach AD DS i DNS).  

5.  Pole wyboru, aby publikować w systemie DNS. To pole:  

    -   Umożliwia wybór punktów zarządzania do publikowania DNS.  

    -   Do konfiguracji publikowania w usługach AD DS.  

##### <a name="to-manually-publish-management-points-to-dns-on-windows-server"></a>Aby ręcznie opublikować punkty zarządzania w systemie DNS w ramach systemu Windows Server  

1.  W konsoli programu Configuration Manager Określ intranetowe nazwy FQDN systemów lokacji.  

2.  W konsoli zarządzania systemem DNS wybierz strefę DNS dla komputera punktu zarządzania.  

3.  Sprawdź, czy występuje rekord hosta (A lub AAAA) dla intranetowej nazwy FQDN systemu lokacji. Jeżeli ten rekord nie istnieje, utwórz go.  

4.  Za pomocą **nowe inne rekordy** wybierz **lokalizacji usługi (SRV)** w **typ rekordu zasobów** oknie dialogowym wybierz **Utwórz rekord**, wprowadź następujące informacje, a następnie wybierz pozycję **gotowe**:  

    -   **Domeny**: W razie potrzeby wprowadź sufiks DNS punktu zarządzania, na przykład **contoso.com**.  
    -   **Usługa**: Typ **_mssms_mp**_&lt;kod_lokacji\>, gdzie &lt;kod_lokacji\> oznacza kod lokacji punktu zarządzania.  
    -   **Protokół**: Typ **_tcp**.  
    -   **Priorytet**: Menedżer konfiguracji nie korzysta z tego pola.  
    -   **Waga**: Menedżer konfiguracji nie korzysta z tego pola.  
    -   **Port**: Wprowadź numer portu, którego używa punkt zarządzania, na przykład **80** dla protokołu HTTP i **443** dla protokołu HTTPS.  

        > [!NOTE]  
        >  Port rekordu SRV powinien odpowiadać portowi komunikacyjnemu, używanego przez punkt zarządzania. Domyślnie jest to **80** dla komunikacji HTTP i **443** dla komunikacji HTTPS.  

    -   **Host oferujący tę usługę**: Wprowadź intranetową nazwę FQDN określoną dla systemu lokacji skonfigurowanego przy użyciu roli lokacji punktu zarządzania.  

Powtórz te czynności dla każdego punktu zarządzania w sieci intranet, który ma zostać opublikowany w systemie DNS.  

##  <a name="bkmk_wins"></a> WINS  
W przypadku niepowodzenia innych mechanizmów lokalizacji usługi klienci mogą znaleźć początkowy punkt zarządzania, sprawdzając usługę WINS.  

Domyślnie lokacja główna publikuje w usłudze WINS pierwszy punkt zarządzania w lokacji, który jest skonfigurowany dla protokołu HTTP i pierwszy punkt zarządzania, który jest skonfigurowany do obsługi protokołu HTTPS.  

Aby klienci nie mogli znaleźć w usłudze WINS punktu zarządzania HTTP, skonfiguruj klientów przy użyciu właściwości **SMSDIRECTORYLOOKUP=NOWINS**pliku Client.msi w programie CCMSetup.exe.  
