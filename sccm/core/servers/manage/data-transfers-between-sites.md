---
title: Transfer danych | Dokumentacja firmy Microsoft
description: "Dowiedz się, jak program Configuration Manager przenosi dane między lokacjami oraz sposób zarządzania transferu danych w sieci."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dc526e8d-fac3-4bb5-b206-03ad29b0ae11
caps.latest.revision: 12
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: bfe77a45b5f781611c343e06d1289add7abd2dfb
ms.openlocfilehash: bf0fdc8d4b4a72760b2cfb91231378a17df01594
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="data-transfers-between-sites-in-system-center-configuration-manager"></a>Transfer danych między lokacjami w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

System Center Configuration Manager używa **replikacji** i **replikacji bazy danych** do transferowania różnych typów informacji między lokacjami. Więcej informacji na temat sposobu programu Configuration Manager przenosi dane między lokacjami oraz sposób zarządzania transferu danych w sieci.  


## <a name="bkmk_fileroute"></a> File-based replication  
Program Configuration Manager używa replikacji plikowej do transferu danych opartych na plikach między lokacjami w hierarchii. Te dane obejmują aplikacje i pakiety, które mają zostać wdrożone do punktów dystrybucji w lokacjach podrzędnych oraz nieprzetworzone rekordy danych odnajdywania, które są przekazywane do lokacji nadrzędnej, a następnie przetwarzany.  

Komunikacja plikowa między lokacjami używa **bloku komunikatów serwera** protokołu (SMB) w portu TCP/IP 445. Można określić tryb impulsu i ograniczanie przepustowości do kontrolowania ilości danych przesyłanych przez sieć i harmonogramów można użyć do kontrolowania, kiedy do przesyłania danych przez sieć.  

### <a name="bkmk_routes"></a> Marszruty replikacji plików  
Poniższe informacje ułatwiają konfigurowanie i używanie marszruty replikacji plików.  

#### <a name="file-replication-route"></a>Trasa replikacji plików

Każda marszruta replikacji plików określa lokację docelową, do której można przetransferować dane oparte na plikach. Każda lokacja obsługuje jedną marszrutę replikacji plików do określonej lokacji docelowej.  

Można zmienić następujące ustawienia dla marszruty replikacji plików:  

-  **Konto replikacji plików**. To konto łączy do lokacji docelowej i zapisuje dane w tej lokacji **SMS_Site** udziału. Dane zapisywane w tym udziale są przetwarzane przez lokację odbierającą. Domyślnie po dodaniu lokacji w hierarchii programu Configuration Manager przypisuje konto komputera serwera lokacji nowej lokacji jako tej lokacji konto replikacji plików. Następnie to konto jest dodawane do lokacji docelowej **SMS_SiteToSiteConnection_&lt;Kod_lokacji\>**  grupy, to grupa lokalna na komputerze przyznająca dostęp do udziału SMS_Site. Można zmienić to konto na konto użytkownika systemu Windows. Jeśli zmienisz konto, upewnij się, Dodaj nowe konto do lokacji docelowej **SMS_SiteToSiteConnection_&lt;Kod_lokacji\>**  grupy.  

    > [!NOTE]  
    >  Lokacje dodatkowe zawsze używają konta komputera serwera lokacji dodatkowej jako **konta replikacji plików**.  

-  **Harmonogram**. Można ustawić harmonogram dla każdej trasy replikacji plików do ograniczenia typu transferowanych danych oraz godziny realizacji transferu do lokacji docelowej.  
-  **Limity szybkości**. Można określić limity szybkości Każda marszruta replikacji plików do kontroli przepustowości sieci, który służy do transferowania danych do lokacji docelowej:  

    -  Ustawienie **Tryb impulsu** pozwala określić rozmiar bloków danych wysyłanych do lokacji docelowej. Można również określić opóźnienie między wysłaniem kolejnych bloków danych. Tej opcji należy użyć przy wysyłaniu danych w połączeniu sieciowym bardzo niskiej przepustowości do lokacji docelowej. Można na przykład ustawić ograniczenie zezwalające na przesyłanie 1 KB danych co pięć sekund, lecz nie co trzy sekundy, niezależnie od szybkości łinku lub jego obciążenia w danym momencie.
    -  Za pomocą opcji **Ograniczone do podanych maksymalnych szybkości transferu wg godziny** można ustawić, aby dane były wysyłane do lokacji docelowej wyłącznie z wykorzystaniem skonfigurowanej wartości procentowej czasu. Tej opcji nie będzie rozpoznawał dostępnej przepustowości sieci programu Configuration Manager, ale podzieli dostępny czas przesyłania danych na okresy. Następnie dane będą wysyłane przez krótki czas, po której następuje przedziałów czasu, gdy dane nie są wysyłane. Na przykład maksymalna szybkość wynosi **50%**, Configuration Manager przesyła dane do ilość czasu, po którym następuje sam okres czasu, gdy żadne dane nie są wysyłane. Rzeczywistej ilości danych lub rozmiaru bloku danych, nie jest zarządzana. lecz jedynie czasu przesyłania danych.  

        > [!CAUTION]  
        > Domyślne jedna lokacja może realizować maksymalnie trzy **jednoczesne operacje wysyłania** w celu transferowania danych do lokacji docelowej. Po włączeniu limitów szybkości dla marszruty replikacji plików liczba **jednoczesnych operacji wysyłania** na potrzeby wysyłania danych do tej lokacji zostanie zredukowana do jednej. Ma to zastosowanie nawet przy opcji **Ogranicz dostępną przepustowość (%)** ustawionej na **100%**. Na przykład użycie domyślne ustawienia dla nadawcy szybkość transferu do lokacji docelowej do jednej trzeciej wydajności domyślnej.  

-  Istnieje możliwość skonfigurowania marszruty replikacji plików między dwiema lokacjami dodatkowymi tak, aby realizować między nimi przesyłanie zawartości opartej na plikach.  

Aby obsłużyć marszrutę replikacji plików, w **Administracja** obszaru roboczego, rozwiń węzeł **Konfiguracja hierarchii** węzeł, a następnie wybierz **replikacji plików**.  

#### <a name="sender"></a>Nadawca

Każda lokacja ma jednego nadawcę. Nadawca obsługuje połączenie sieciowe z lokacji źródłowej do lokacji docelowej i może nawiązywać jednoczesne połączenia z wieloma lokacjami. Aby nawiązać połączenie z lokacją, w celu identyfikacji konta używanego do ustanowienia połączenia sieciowego nadawca korzysta ze skierowanej do lokacji marszruty replikacji plików. Nadawca używa tego konta również do zapisu danych do udziału SMS_Site tej lokacji docelowej.  

Domyślnie nadawca zapisuje dane do lokacji docelowej za pomocą wielu **jednoczesnych operacji wysyłania**nazywanych zwyczajowo wątkami. Każdy jednoczesny proces (wątek) może transferować różne obiekty plikowe do lokacji docelowej. Domyślnie gdy nadawca zaczyna wysyłać obiekt, kolejne bloki danych będą zapisywane do momentu wysłania całego obiektu. Po wysłaniu wszystkich danych obiektu wątek może zostać wykorzystane do rozpoczęcia przesyłania nowego obiektu.  

Można zmienić następujące ustawienia dla nadawcy:  

-  **Maksymalna liczba jednoczesnych operacji wysyłania**. Domyślnie każda lokacja korzysta pięć jednoczesnych operacji wysyłania, z czego trzy są dostępne do użycia podczas wysyłania danych do jednej z lokacji docelowych. Wraz ze zwiększeniem tej liczby, może zwiększyć przepływność danych między lokacjami, ponieważ Menedżer konfiguracji może transfer większej liczby plików w tym samym czasie. Ponadto po zwiększeniu tej liczby jest wymagana większa przepustowość sieci między lokacjami.  

-  **Ustawienia ponawiania**. Domyślnie każda lokacja ponawia próbę nawiązania połączenia w dwa razy z opóźnieniem jednej minuty między próbami. Liczba prób połączenia lokacji sprawia, że, można modyfikować oraz czas między próbami.  

Aby zarządzać nadawcą w lokacji, w **Administracja** obszaru roboczego, rozwiń węzeł **konfiguracja lokacji** węzła, wybierz opcję **witryn** węzeł, a następnie wybierz **właściwości** dla lokacji, w którym chcesz zarządzać. Wybierz **nadawcy** kartę, aby zmienić ustawienia nadawcy.  

## <a name="bkmk_dbrep"></a> Database replication  
Replikacja bazy danych programu Configuration Manager wykorzystuje program SQL Server do przesyłania danych i scalania zmian wprowadzonych w bazie danych lokacji z informacjami przechowywanymi w bazie danych w innych lokacjach w hierarchii. Należy pamiętać o następujących dotyczących replikacji bazy danych:

-  Wszystkie lokacje udostępnianie tych samych informacji.  
-  Podczas instalowania lokacji w hierarchii replikacji bazy danych zostanie automatycznie nawiązane między nową lokacją a jej wyznaczoną lokacją nadrzędną.  
-  Po zakończeniu instalacji lokacji Replikacja bazy danych zostanie automatycznie uruchomiona.  

Po dodaniu nowej lokacji do hierarchii programu Configuration Manager tworzy ogólną bazę danych w nowej lokacji. Następnie lokacja nadrzędna tworzy w swojej bazie danych migawkę odpowiednich danych i następnie przesyła migawkę do nowej lokacji za pomocą replikacji plikowej. Następnie nowej lokacji używa programu SQL Server zbiorczego kopiowania Program (BCP) ładuje te informacje do swojej lokalnej kopii bazy danych programu Configuration Manager. Po załadowaniu migawki między lokacjami odbywa się replikacja bazy danych.  

Do replikacji danych między lokacjami, Configuration Manager korzysta z własnej usługi replikacji bazy danych. Usługi replikacji bazy danych śledzenia do monitorowania bazy danych lokacji lokalnej zmiany zmian programu SQL Server, a następnie replikuje zmiany do innych lokacji za pomocą programu SQL Server Service Broker (SSB). Domyślnie ten proces używany TCP/IP port 4022.  

Dane grupy programu Configuration Manager replikacji bazy danych do różnych grup replikacji. Należy pamiętać o następujących dotyczących grup replikacji:

-  Każda grupa replikacji ma oddzielny, stały harmonogram replikacji. Określa on częstotliwość replikacji zmian wprowadzonych w danych w grupie do pozostałych lokacji.  

     Na przykład zmian w konfiguracji administracji opartej na szybko replikowane do innych lokacji upewnij się, że te zmiany są wymuszane tak szybko, jak to możliwe. W tym samym czasie zmian w konfiguracji o niższym priorytecie, takich jak żądania zainstalowania nowej lokacji dodatkowej, jest mniej pilna. Może upłynąć żądanie nowej lokacji dociera do docelowej lokacji głównej w ciągu kilku minut.  

-   Można zmodyfikować następujące ustawienia dla replikacji bazy danych:  

    -  **Bazy danych łącza replikacji**. Kontroluj kiedy przechodzi ruchu sieciowego.  
    -  **Widoki rozproszone**. Zmień ustawienia dla łącza replikacji, za pomocą którego żądań, które zostały wprowadzone w witrynie Administracja centralna wybranych danych lokacji można do nich dostępu lokacji bezpośrednio z bazy danych w podrzędnej lokacji głównej.  
    -  **Harmonogramy**. Określ, gdy łącze replikacji jest używany, a kiedy dane różnych typów danych lokacji.  
    -  **Podsumowanie**. Zmień ustawienia podsumowania danych dotyczących ruchu sieciowego, który przechodzi łącza replikacji. Podsumowania jest wykonywane domyślnie co 15 minut, a jest używane w raportach dotyczących replikacji bazy danych.  
    -  **Bazy danych progów replikacji**. Definiowanie, kiedy łącza są zgłaszane wskazany stan nieprawidłowego działania lub nie powiodło się. Ponadto można skonfigurować podczas alertów dotyczących łącz replikacji, które mają stan lub uszkodzenie zgłasza programu Configuration Manager.  

Menedżer konfiguracji klasyfikuje dane replikowane za pomocą replikacji bazy danych jako **danych globalnych** lub **danych lokacji**. W ramach replikacji bazy danych zmiany wprowadzone w danych globalnych i danych lokacji są transferowane za pośrednictwem łącza replikacji danych. Dane globalne można replikować do lokacji nadrzędnych i podrzędnych. Dane lokacji są replikowane tylko do lokacji nadrzędnej. Trzeci typ danych, dane lokalne nie są replikowane do innych lokacji. Dane lokalne są informacje, które nie jest wymagane w innych lokacjach. Należy pamiętać o następujących informacji o typach danych:  

-  **Dane globalne**. Dane globalne dotyczą obiektów utworzone przez administratora, które są replikowane do wszystkich lokacji w hierarchii, Lokacje dodatkowe odbierają tylko podzestaw danych globalnych w formie danych globalnych serwera proxy. Dane globalne obejmuje wdrożenia oprogramowania, aktualizacji oprogramowania, definicje kolekcji oraz zakresy zabezpieczeń administracji opartej na rolach. Administratorzy mogą tworzyć dane globalne w centralnych lokacjach administracyjnych i w lokacjach głównych.  
-  **Dane lokacji**. Dane lokacji odnosi się do informacje operacyjne tej lokacji głównej programu Configuration Manager i klientów, służące do tworzenia raportów w lokacjach głównych. Dane lokacji są replikowane do centralnej lokacji administracyjnej, ale nie do innych lokacji głównych. Dane lokacji zawiera dane spisu sprzętu, komunikaty o stanie, alerty i wyniki kolekcji na podstawie kwerendy. Dane lokacji są widoczne tylko w centralnej lokacji administracyjnej i w lokacji głównej, z której pochodzą dane. Dane lokacji można modyfikować tylko w lokacji głównej, w której zostały utworzone.  

     Wszystkie dane lokacji są replikowane do centralnej lokacji administracyjnej. Witryna Administracja centralna wykonuje administrowanie i raportowanie dla całej hierarchii witryny.  

W poniższych sekcjach opisano ustawienia, które można zmienić do zarządzania replikacją bazy danych.  

### <a name="bkmk_Dblinks"></a> Linki replikacji bazy danych  
Po zainstalowaniu nowej lokacji w hierarchii programu Configuration Manager automatycznie tworzy łącze replikacji bazy danych między lokacją nadrzędną i nowej lokacji. Jedno łącze służy do łączenia dwóch lokacji.  

Można zmienić ustawienia dla każdego łącza replikacji bazy danych, aby ułatwić kontrolę transferu danych za pośrednictwem łącza replikacji. Każde łącze replikacji obsługuje różne konfiguracje. Są dostępne następujące kontrolki łączy replikacji bazy danych:  

-  Zatrzymania replikacji wybranych danych lokacji z lokacji głównej do centralnej lokacji administracyjnej, więc witryny Administracja centralna można dostęp do tych danych bezpośrednio z bazy danych lokacji głównej.  
-  Planowanie wybranych danych lokacji na przesyłanie z podrzędnej lokacji głównej do centralnej lokacji administracyjnej.
-  Definiowanie ustawień umożliwiających określenie, gdy łącze replikacji bazy danych ma uszkodzenia lub nie powiodła się.
-  Określ, kiedy warunków zgłaszania alertów dotyczących uszkodzonego łącza replikacji.
-  Określ, jak często program Configuration Manager podsumowuje dane o ruchu związanego z replikacją, który korzysta z łącza replikacji. Te dane są używane w raportach.

Aby skonfigurować łącze replikacji bazy danych, w konsoli programu Configuration Manager na **replikacji bazy danych** węzła, edytować właściwości odpowiedniego łącza. Ten węzeł jest dostępny zarówno w **monitorowanie** obszar roboczy i w **Administracja** obszaru roboczego na **Konfiguracja hierarchii** węzła. Łącze replikacji można edytować z poziomu lokacji nadrzędnej lub podrzędnej.  

> [!TIP]  
> Linki replikacji bazy danych można edytować w węźle **Replikacja bazy danych** w każdym obszarze roboczym. Jednakże, gdy używasz **replikacji bazy danych** w węźle **monitorowanie** obszaru roboczego, również można wyświetlić stan replikacji za pośrednictwem łączy replikacji bazy danych i narzędzia Analizator łącza replikacji badać problemy z replikacją baz danych.  

Informacje o sposobie konfigurowania linków replikacji znajdują się w sekcji [Kontrolki replikacji bazy danych lokacji](#BKMK_DBRepControls). Aby uzyskać więcej informacji o sposobie monitorowania replikacji, zobacz [jak monitorować stan replikacji i łącza replikacji bazy danych](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_MonitorRepLinksAndStatuss) w [monitorowanie hierarchii i replikacji infrastruktury w programie System Center Configuration Manager](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md) tematu.  

Użyj informacje w poniższych sekcjach ułatwiają planowanie łączy replikacji bazy danych.  

### <a name="bkmk_distviews"></a> Widoki rozproszone  
Za pomocą widoków rozproszonych żądań wysyłanych do lokacji centralnej administracji wybrane dostęp do danych lokacji danych lokacji bezpośrednio z bazy danych w podrzędnej lokacji głównej. Bezpośredniemu dostępowi nie jest wymagana replikacja danych lokacji z lokacji głównej do witryny Administracja centralna. Ponieważ każde łącze replikacji jest niezależna od siebie, można użyć widoków rozproszonych w łączach replikacji, które można wybrać. Nie można używać widoków rozproszonych między lokacją podstawową a lokacją dodatkową.  

Widoki rozproszone zapewniają następujące korzyści:  

-  Zmniejszenie obciążenia Procesora, aby przetworzyć zmiany bazy danych w centralnej lokacji administracyjnej oraz lokacjach głównych
-  Zmniejszenie ilości danych transferowanych przez sieć do witryny Administracja centralna
-  Lepsza wydajność programu SQL server, który obsługuje bazę danych witryny Administracja centralna
-  Zmniejszenie miejsca na dysku używanego przez bazę danych w witrynie Administracja centralna

Należy rozważyć użycie widoków rozproszonych, gdy lokacja główna znajduje się w pobliżu witryny Administracja centralna w sieci, a dwie lokacje są stale włączone i zawsze połączone. Jest to spowodowane widokom rozproszonym zamiast replikacji wybranych danych między lokacjami z bezpośrednich połączeń między serwerami SQL w każdej lokacji. Połączenie bezpośrednie jest nawiązywane każdym odebraniu żądania danych jest w witrynie Administracja centralna. Zazwyczaj żądania danych dostępnych w ramach widoków rozproszonych są wysyłane w przypadku uruchamiania raportów lub kwerend, podczas wyświetlania informacji w Eksploratorze zasobów oraz oceny kolekcji zawierających zasady oparte na danych lokacji.  

Widoki rozproszone są domyślnie wyłączone dla każdego łącza replikacji. Po włączeniu widoków rozproszonych w ramach łącza replikacji należy wybrać dane lokacji, które nie będą replikowane do centralnej lokacji administracyjnej za pośrednictwem tego łącza. Witryna Administracja centralna uzyskuje dostęp do tych danych bezpośrednio z bazy danych lokacji podrzędnej udostępniającej łącze. W widokach rozproszonych można skonfigurować następujące typy danych lokacji:  

-  Dane dotyczące zapasów sprzętu klientów
-  Dane dotyczące zapasów oprogramowania i pomiarów klienta
-  Komunikaty o stanie klientów, lokacji głównej i wszystkich lokacji dodatkowych

Pod względem operacyjnym widoki rozproszone są niewidoczne dla użytkowników administracyjnych wyświetlających dane w raportach lub w konsoli programu Configuration Manager. Po wysłaniu żądania danych uwzględnionych w widokach rozproszonych programu SQL server obsługującym bazę danych dla witryny administracji centralnej bezpośrednio uzyskuje dostęp do programu SQL server podrzędnej lokacji głównej pobiera odpowiednie informacje. Na przykład użyć konsoli programu Configuration Manager w witrynie Administracja centralna żądanie informacji dotyczących zapasów sprzętu z dwóch lokacji, a tylko jedna lokacja ma włączone w widoku rozproszonym spis sprzętu. Informacje o zapasach klientów z lokacji nieskonfigurowanej w ramach widoków rozproszonych są pobierane z bazy danych w centralnej lokacji administracyjnej. Informacje o zapasach klientów z lokacji, skonfigurowany w widokach rozproszonych jest dostępna w bazie danych w podrzędnej lokacji głównej. Te informacje są wyświetlane w konsoli programu Configuration Manager lub raport bez identyfikacji źródła.  

Tak długo, jak łącze replikacji zawiera typ danych uwzględnionych w widokach rozproszonych, podrzędna lokacja główna nie replikacji danych w witrynie Administracja centralna. Zaraz po wyłączeniu widoków rozproszonych określonego typu danych, podrzędnych głównej lokacji wznowi replikację tych danych do centralnej lokacji administracyjnej w ramach normalnego procesu replikacji danych. Jednak przed te dane są dostępne w witrynie Administracja centralna, te dane należy ponownie zainicjować grupy replikacji między lokacją podstawową a lokacją administracji centralnej. Podobnie po odinstalowaniu lokacji głównej, która ma włączone widoki rozproszone witryny Administracja centralna musi ponownie zainicjować jej dane, można uzyskać dostęp do danych, które zostały włączone dla widoków rozproszonych w witrynie Administracja centralna.  

> [!IMPORTANT]  
> Korzystając z widoków rozproszonych w dowolnym łączu replikacji w hierarchii lokacji, należy wyłączyć widoki rozproszone dla wszystkich łączy replikacji przed odinstalowaniem jakiejkolwiek lokacji głównej. Aby uzyskać więcej informacji, zobacz [Odinstalowywanie lokacji głównej skonfigurowanej z widokami rozproszonymi](../../../core/servers/deploy/install/uninstall-sites-and-hierarchies.md#BKMK_UninstallPrimaryDistViews).  

#### <a name="prerequisites-and-limitations-for-distributed-views"></a>Warunki wstępne i ograniczenia dotyczące widoków rozproszonych  

-  Można użyć widoków rozproszonych tylko w łączach replikacji między centralną lokacją administracyjną i lokacją główną.
- Centralnej lokacji administracyjnej należy użyć programu SQL Server w wersji Enterprise. Lokacja główna ma to wymaganie.
-  Centralna lokacja administracyjna może mieć zainstalowane tylko jedno wystąpienie dostawcy programu SMS, a to wystąpienie musi być zainstalowane na serwerze bazy danych lokacji. Jest to wymagane do obsługi uwierzytelniania Kerberos, wymagane, aby umożliwić dostęp SQL server w witrynie Administracja centralna programu SQL server w podrzędnej lokacji głównej. Nie istnieją ograniczenia dotyczące dostawcy programu SMS w podrzędnej lokacji głównej.
-  Centralna lokacja administracyjna może mieć zainstalowany tylko jeden punkt usług SQL Server Reporting Services, który musi znajdować się na serwerze bazy danych lokacji. Jest to wymagane do obsługi uwierzytelniania Kerberos, wymaganego do włączenia programu SQL server w witrynie Administracja centralna dostępu do serwera SQL w podrzędnej lokacji głównej.
-  Baza danych lokacji nie może być hostowana w klastrze programu SQL Server.
-  Baza danych lokacji nie może być umieszczona w grupie dostępności SQL Server Always On.
-  Konto komputera serwera bazy danych z centralnej lokacji administracyjnej wymaga uprawnień do odczytu bazy danych lokacji w lokacji głównej.

> [!IMPORTANT]  
>  Widoki rozproszone i harmonogramy replikacji danych to wzajemnie wykluczające ustawienia dla łącza replikacji bazy danych.  

### <a name="BKMK_schedules"></a> Harmonogramy transferów danych lokacji w linkach replikacji bazy danych  
W celu ułatwienia kontroli przepustowości sieci używanej w ramach replikacji danych z podrzędnej lokacji głównej do jej centralnej lokacji administracyjnej istnieje można zaplanować używanie łącza replikacji oraz określić moment replikacji poszczególnych typów danych lokacji. Istnieje możliwość skonfigurowania, kiedy lokacja główna ma replikować komunikaty o stanie, zapasy oraz dane pomiarów. Łącza replikacji bazy danych z lokacji dodatkowych nie obsługują harmonogramów dla danych lokacji. Zaplanowanie transferu danych globalnych nie jest możliwe.  

Podczas konfigurowania harmonogramu łącza replikacji bazy danych można ograniczyć transfer wybranych danych z lokacji głównej do centralnej lokacji administracyjnej oraz skonfigurować różne czasy replikacji poszczególnych typów danych lokacji.  

> [!IMPORTANT]  
> Widoki rozproszone i harmonogramy replikacji danych to wzajemnie wykluczające się konfiguracje w ramach łącza replikacji bazy danych.  

### <a name="BKMK_SummarizeDBReplication"></a> Podsumowanie ruchu związanego z replikacją bazy danych  
Każda lokacja okresowo tworzy podsumowanie danych dotyczących ruchu sieciowego, który przechodzi łącza replikacji bazy danych lokacji. Podsumowanie danych jest używane w raportach dotyczących replikacji bazy danych. Obie lokacje należące do łącza replikacji podsumowują obciążenie sieci występujące na tym łączu. Dane podsumowuje programu SQL Server hostujący bazę danych lokacji. Po podsumowywania danych informacje są replikowane do innych lokacji jako dane globalne.  

Podsumowanie odbywa się domyślnie co 15 minut. Aby zmienić częstotliwość podsumowania dla ruchu sieciowego, we właściwościach łącza replikacji bazy danych, należy edytować **interwał podsumowania**. Częstotliwość podsumowania wpływa na informacje, które można wyświetlić w raportach dotyczących replikacji bazy danych. Można wybrać interwał od 5 minut do 60 minut. Zwiększenie wartości częstotliwości podsumowania powoduje wzrost obciążenia przetwarzaniem na serwerze SQL w każdej lokacji w ramach łącza replikacji.  

### <a name="BKMK_DBRepThresholds"></a>Progi replikacji bazy danych  
Progi replikacji bazy danych pozwalają zdefiniować, kiedy ma być zgłaszane nieprawidłowe działanie lub uszkodzenie łącza replikacji bazy danych. Domyślnie łącze jest ustawiana na uszkodzenia, gdy replikacja nie może przeprowadzić replikacji w okresie 12 kolejnych prób. Łącze jest ustawiana niepowodzenie, stan, gdy wszystkie grupy replikacji nie są replikowane w 24 kolejnych prób.  

Można określić wartości niestandardowe w celu dostosowania, gdy raportów programu Configuration Manager lub uszkodzenie łącza replikacji. Dopasowywanie, kiedy program Configuration Manager zgłasza, że każdy stan łączy replikacji bazy danych ułatwia precyzyjne monitorowanie kondycji replikacji bazy danych za pośrednictwem łączy replikacji bazy danych.  

Ponieważ jest to możliwe w jednej lub kilku grupach replikacji niepowodzenie, a w innych grupach replikacji replikację pomyślnie, należy zaplanować sprawdzenie stanu łącza replikacji po raz pierwszy zgłosi uszkodzenia. Jeżeli w pewnych grupach replikacji cyklicznie występują opóźnienia, które nie powodują problemu, lub gdy przepustowość łącza sieciowego między lokacjami jest niska, zaleca się zmodyfikowanie wartości ponownych prób przed zgłoszeniem nieprawidłowego działania lub uszkodzenia łącza. Zwiększenie liczby ponownych prób przed łącze jest równa lub uszkodzenia, można wyeliminować fałszywe ostrzeżenia dotyczące znanych problemów i bardziej precyzyjnie monitorować stan łącza.  

Ponadto należy wziąć pod uwagę interwał synchronizacji replikacji dla każdej grupy replikacji poznać częstotliwość replikacji w danej grupie. Aby wyświetlić **interwał synchronizacji** dla grup replikacji w **monitorowanie** obszaru roboczego na **replikacji bazy danych** węzła, wybierz opcję **szczegóły replikacji** łącza replikacji.  

Aby uzyskać więcej informacji o sposobie monitorowania replikacji bazy danych, w tym wyświetlaniu stanu replikacji, zobacz [jak monitorować stan replikacji i łącza replikacji bazy danych](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_MonitorRepLinksAndStatuss) w [monitorowanie hierarchii i replikacji infrastruktury w programie System Center Configuration Manager](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md) tematu.  

Aby uzyskać informacje o konfigurowaniu progów replikacji bazy danych, zobacz [kontrolki replikacji bazy danych lokacji](#BKMK_DBRepControls).  

## <a name="BKMK_DBRepControls"></a> Kontrolki replikacji bazy danych lokacji  
Można zmienić ustawienia dla każdej bazy danych lokacji w celu ułatwienia kontroli przepustowości sieci używanej w ramach replikacji bazy danych. Ustawienia stosują się tylko do bazy danych lokacji, w którym można skonfigurować ustawienia. Ustawienia są zawsze stosowane podczas żadnych danych replikacji bazy danych do innych lokacji.  

Kontrolki replikacji, które można modyfikować dla każdej bazy danych lokacji są następujące:  

-  Zmiana portu SSB.  
-  Skonfiguruj okres oczekiwania zanim niepowodzenia replikacji wyzwalacza lokacji ponowną inicjalizację kopii bazy danych lokacji.  
-  Skonfiguruj bazę danych lokacji, aby dane były kompresowane w ramach replikacji bazy danych. Dane są kompresowane tylko w ramach transferu między lokacjami, a nie przechowywania w bazie danych lokacji po jednej stronie.  

Aby zmienić ustawienia dla kontrolki replikacji bazy danych lokacji, w konsoli programu Configuration Manager na **replikacji bazy danych** węzła, edytować właściwości bazy danych lokacji. Ten węzeł jest wyświetlany w węźle **Konfiguracja hierarchii** obszaru roboczego **Administracja** , a także w obszarze roboczym **Monitorowanie**. Aby edytować właściwości bazy danych lokacji, wybierz łącze replikacji między lokacjami, a następnie otwórz okno dialogowe **właściwości nadrzędnej bazy danych** lub **właściwości podrzędnej bazy danych**.  

> [!TIP]  
> Kontrolki replikacji bazy danych można skonfigurować w węźle **Replikacja bazy danych** w każdym obszarze roboczym. Jednakże, gdy używasz **replikacji bazy danych** w węźle **monitorowanie** obszaru roboczego, również można wyświetlić stan replikacji bazy danych dla łącza replikacji i narzędzia Analizator łącza replikacji badać problemy z replikacją.  

