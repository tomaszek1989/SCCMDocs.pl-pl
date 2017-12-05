---
title: Transfer danych
titleSuffix: Configuration Manager
description: "Dowiedz się, jak programu Configuration Manager przenosi dane między lokacjami oraz sposobu zarządzania transferem danych w sieci."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: dc526e8d-fac3-4bb5-b206-03ad29b0ae11
caps.latest.revision: "12"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 185598e9f6b0678ca1fcbe9c19ed420f37805861
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2017
---
# <a name="data-transfers-between-sites-in-system-center-configuration-manager"></a>Transfer danych między lokacjami w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

System Center Configuration Manager używa **replikacji plikowej** i **replikacji bazy danych** do transferowania różnych typów informacji między lokacjami. Więcej informacji na temat sposobu programu Configuration Manager przenosi dane między lokacjami oraz sposobu zarządzania transferem danych w sieci.  


## <a name="bkmk_fileroute"></a> File-based replication  
Program Configuration Manager używa replikacji plikowej do transferu danych opartych na plikach między lokacjami w hierarchii. Te dane obejmują aplikacje i pakiety, które można wdrożyć w punktach dystrybucji w lokacjach podrzędnych oraz nieprzetworzone rekordy danych odnajdywania, które są przesyłane do lokacji nadrzędnej, a następnie przetwarzany.  

Komunikacja plikowa między lokacjami używa **bloku komunikatów serwera** protokołu (SMB) na portu TCP/IP 445. Można określić tryb ograniczania przepustowości i pulse przepustowości do kontroli ilości danych transferowanych przez sieć, a harmonogramów można użyć do kontrolowania, kiedy mają zostać wysłane dane przez sieć.  

### <a name="bkmk_routes"></a> Marszruty replikacji plików  
Poniższe informacje ułatwiają konfigurowanie i używanie marszrut replikacji plików.  

#### <a name="file-replication-route"></a>Trasa replikacji plików

Każda marszruta replikacji plików określa lokację docelową, do której można przetransferować dane oparte na pliku. Każda lokacja obsługuje jedną trasę replikacji plików do określonej lokacji docelowej.  

Można zmienić następujące ustawienia dla marszruty replikacji plików:  

-  **Konto replikacji plików**. To konto łączy do lokacji docelowej i zapisuje dane do tej lokacji **SMS_Site** udziału. Dane zapisywane w tym udziale są przetwarzane przez lokację odbierającą. Domyślnie po dodaniu lokacji do hierarchii program Configuration Manager przypisuje konto komputera serwera lokacji nowych lokacji tej lokacji konto replikacji plików. To konto jest dodawane do lokacji docelowej **SMS_SiteToSiteConnection_&lt;Kod_lokacji\>**  grupy, to grupa lokalna na komputerze przyznająca dostęp do udziału SMS_Site. Można zmienić to konto na konto użytkownika systemu Windows. Jeśli zmienisz konto, upewnij się, Dodaj nowe konto do lokacji docelowej **SMS_SiteToSiteConnection_&lt;Kod_lokacji\>**  grupy.  

    > [!NOTE]  
    >  Lokacje dodatkowe zawsze używają konta komputera serwera lokacji dodatkowej jako **konta replikacji plików**.  

-  **Harmonogram**. Można ustawić harmonogram każdej trasy replikacji plików w celu ograniczenia typu danych oraz czasu przesyłania danych do lokacji docelowej.  
-  **Limity szybkości**. Można określić limity szybkości dla każdej trasy replikacji plików do kontroli przepustowości sieci, który służy do przesyłania danych do lokacji docelowej:  

    -  Ustawienie **Tryb impulsu** pozwala określić rozmiar bloków danych wysyłanych do lokacji docelowej. Można również określić opóźnienie między wysłaniem kolejnych bloków danych. Użyj tej opcji, po wysłaniu danych przez połączenie sieciowe o bardzo niskiej przepustowości do lokacji docelowej. Można na przykład ustawić ograniczenie zezwalające na przesyłanie 1 KB danych co pięć sekund, lecz nie co trzy sekundy, niezależnie od szybkości łinku lub jego obciążenia w danym momencie.
    -  Za pomocą opcji **Ograniczone do podanych maksymalnych szybkości transferu wg godziny** można ustawić, aby dane były wysyłane do lokacji docelowej wyłącznie z wykorzystaniem skonfigurowanej wartości procentowej czasu. Tej opcji programu Configuration Manager nie będzie rozpoznawał dostępnej przepustowości sieci, ale podzieli dostępny czas przesyłania danych na okresy. Następnie danych jest wysyłane przez krótki czas, po której następuje przedziałów czasu, gdy dane nie są wysyłane. Na przykład maksymalna szybkość wynosi **50%**, programu Configuration Manager nieprzesyłania danych przez sam okres czasu, gdy żadne dane nie są wysyłane. Rzeczywistej ilości danych lub rozmiaru bloku danych nie jest obsługiwany. lecz jedynie czasu przesyłania danych.  

        > [!CAUTION]  
        > Domyślne jedna lokacja może realizować maksymalnie trzy **jednoczesne operacje wysyłania** w celu transferowania danych do lokacji docelowej. Po włączeniu limitów szybkości dla marszruty replikacji plików liczba **jednoczesnych operacji wysyłania** na potrzeby wysyłania danych do tej lokacji zostanie zredukowana do jednej. Ma to zastosowanie nawet przy opcji **Ogranicz dostępną przepustowość (%)** ustawionej na **100%**. Na przykład jeśli używasz domyślne ustawienia dla nadawcy, zmniejsza szybkość transferu do lokacji docelowej jako jedna trzecia wydajności domyślnej.  

-  Istnieje możliwość skonfigurowania marszruty replikacji plików między dwiema lokacjami dodatkowymi tak, aby realizować między nimi przesyłanie zawartości opartej na plikach.  

Aby obsłużyć marszrutę replikacji plików w **administracji** obszaru roboczego, rozwiń węzeł **Konfiguracja hierarchii** węzeł, a następnie wybierz **replikacji plików**.  

#### <a name="sender"></a>Nadawca

Każda lokacja ma jednego nadawcę. Nadawca obsługuje połączenie sieciowe z lokacji źródłowej do lokacji docelowej i może nawiązywać jednoczesne połączenia z wieloma lokacjami. Aby nawiązać połączenie z lokacją, w celu identyfikacji konta używanego do ustanowienia połączenia sieciowego nadawca korzysta ze skierowanej do lokacji marszruty replikacji plików. Nadawca używa tego konta również do zapisu danych do udziału SMS_Site lokacji docelowej.  

Domyślnie nadawca zapisuje dane do lokacji docelowej za pomocą wielu **jednoczesnych operacji wysyłania**nazywanych zwyczajowo wątkami. Każdy jednoczesny proces (wątek) może transferować różne obiekty plikowe do lokacji docelowej. Domyślnie gdy nadawca zaczyna wysyłać obiekt, kolejne bloki danych będą zapisywane do momentu wysłania całego obiektu. Po wysłaniu wszystkich danych obiektu wątek może zostać wykorzystane do rozpoczęcia przesyłania nowego obiektu.  

Można zmienić następujące ustawienia dla nadawcy:  

-  **Maksymalna liczba jednoczesnych operacji wysyłania**. Domyślnie każda lokacja korzysta z pięciu jednoczesnych operacji wysyłania, z których trzy są dostępne do użycia podczas wysyłania danych do jednej z lokacji docelowych. Wraz ze zwiększeniem tej liczby, ponieważ Menedżer konfiguracji może transfer większej liczby plików w tym samym czasie można zwiększyć przepływność danych między lokacjami. Ponadto po zwiększeniu tej liczby jest wymagana większa przepustowość sieci między lokacjami.  

-  **Ustawienia ponawiania**. Domyślnie każda lokacja ponowi próbę połączenia dwa razy z opóźnieniem jednej minuty między próbami. Liczba prób nawiązania połączenia realizowanych lokacji, można modyfikować i jak długo czekać między próbami.  

Aby zarządzać nadawcą w ramach lokacji, w **administracji** obszaru roboczego, rozwiń węzeł **konfiguracja lokacji** węzła, wybierz opcję **witryny** węzeł, a następnie wybierz **właściwości** dla witryny, którymi chcesz zarządzać. Wybierz **nadawcy** kartę, aby zmienić ustawienia nadawcy.  

## <a name="bkmk_dbrep"></a> Database replication  
Replikacja bazy danych programu Configuration Manager używa programu SQL Server do przesyłania danych i scalania zmian wprowadzonych w bazie danych lokacji z informacjami przechowywanymi w bazie danych innych lokacji w hierarchii. Należy pamiętać, że dotyczących replikacji bazy danych:

-  We wszystkich lokacjach udostępnianie tych samych informacji.  
-  Podczas instalowania lokacji w hierarchii jest automatycznie ustanowić replikacji bazy danych między nową lokacją a jej wyznaczoną lokacją nadrzędną.  
-  Po zakończeniu instalacji lokacji Replikacja bazy danych zostanie automatycznie uruchomiona.  

Po dodaniu nowej lokacji do hierarchii programu Configuration Manager tworzy ogólną bazę danych w nowej lokacji. Następnie lokacja nadrzędna tworzy w swojej bazie danych migawkę odpowiednich danych i następnie przesyła migawkę do nowej lokacji za pomocą replikacji opartej na plikach. Następnie nowej lokacji używa programu SQL Server zbiorczego kopii programu (BCP) ładuje te informacje do swojej lokalnej kopii bazy danych programu Configuration Manager. Po załadowaniu migawki między lokacjami odbywa się replikacja bazy danych.  

Do replikacji danych między lokacjami, programu Configuration Manager korzysta z własnej usługi replikacji bazy danych. Usługa replikacji bazy danych śledzenia do bazy danych lokacji lokalnych zmian monitorowania zmian programu SQL Server, a następnie replikuje dane zmian do innych lokacji za pomocą programu SQL Server Service Broker (SSB). Domyślnie ten proces wykorzystuje TCP/IP port 4022.  

Configuration Manager grupuje dane objęte replikacją bazy danych do różnych grup replikacji. Należy pamiętać, że dotyczących grup replikacji:

-  Każda grupa replikacji ma oddzielny, stały harmonogram replikacji. Określa on częstotliwość replikacji zmian wprowadzonych w danych w grupie do pozostałych lokacji.  

     Na przykład zmian w konfiguracji administracji opartej na rolach na szybkie replikuje do innych witryn, aby upewnić się, że te zmiany są wymuszane tak szybko, jak to możliwe. W tym samym czasie zmiany konfiguracji o niższym priorytecie, na przykład żądania zainstalowania nowej lokacji dodatkowej, jest mniej pilna. Może upłynąć kilka minut, żądanie nowej lokacji dociera do docelowej lokacji głównej.  

-   Można zmodyfikować następujące ustawienia replikacji bazy danych:  

    -  **Łącza replikacji bazy danych**. Formant, gdy określony ruch jest przesyłany w sieci.  
    -  **Widoki rozproszone**. Zmień ustawienia łączy replikacji za pomocą którego żądań, które zostały wprowadzone w witrynie Administracja centralna danych wybranej lokacji mają dostęp do danych tej lokacji bezpośrednio z bazy danych w podrzędnej lokacji głównej.  
    -  **Harmonogramy**. Określ stosowania łącza replikacji i moment replikacji poszczególnych typów danych lokacji.  
    -  **Podsumowanie**. Zmień ustawienia podsumowania danych dotyczących ruchu sieciowego, który przechodzi przez łącza replikacji. Podsumowanie występuje domyślnie co 15 minut, a jest używane w raportach dotyczących replikacji bazy danych.  
    -  **Progi replikacji bazy danych**. Definiowanie, kiedy łączy ma być zgłaszane nieprawidłowe działanie lub nie powiodło się. Można także skonfigurować w przypadku programu Configuration Manager alertów dotyczących łącz replikacji, które będą miały stan nieprawidłowe działanie lub uszkodzenie.  

Menedżer konfiguracji klasyfikuje dane replikowane w ramach replikacji bazy danych jako **danych globalnych** lub **dane lokacji**. W ramach replikacji bazy danych zmiany wprowadzone w danych globalnych i danych lokacji są transferowane za pośrednictwem łącza replikacji danych. Dane globalne można replikować do lokacji nadrzędnych i podrzędnych. Dane lokacji są replikowane tylko do lokacji nadrzędnej. Trzeci typ danych, dane lokalne nie jest replikowany do innych lokacji. Dane lokalne są informacje, które nie jest wymagane przez innych lokacji. Należy pamiętać, że o typach danych:  

-  **Dane globalne**. Dane globalne dotyczą obiektów utworzonych przez administratora, które są replikowane do wszystkich lokacji w całej hierarchii, jednak Lokacje dodatkowe odbierają tylko podzestaw danych globalnych w formie danych globalnych serwera proxy. Dane globalne obejmuje wdrożenia oprogramowania, aktualizacje oprogramowania, definicje kolekcji i zakresy zabezpieczeń administracji opartej na rolach. Administratorzy mogą tworzyć dane globalne w centralnych lokacjach administracyjnych i w lokacjach głównych.  
-  **Dane lokacji**. Dane lokacji odwołuje się do informacji operacyjnych tej lokacji podstawowej programu Configuration Manager i klienci, którzy utworzyć raport do lokacji głównych. Dane lokacji są replikowane do centralnej lokacji administracyjnej, ale nie do innych lokacji głównych. Dane lokacji obejmują dane dotyczące zapasów sprzętu, komunikaty o stanie, alerty i wyniki kolekcji opartych na zapytaniach. Dane lokacji są widoczne tylko w centralnej lokacji administracyjnej i w lokacji głównej, z których pochodzą dane. Dane lokacji można modyfikować tylko w lokacji głównej, w której zostały utworzone.  

     Wszystkie dane lokacji są replikowane do centralnej lokacji administracyjnej. Centralna lokacja administracyjna wykonuje administrowanie i raportowanie na całą hierarchię lokacji.  

W poniższych sekcjach opisano ustawienia, które można zmienić do zarządzania replikacją bazy danych.  

### <a name="bkmk_Dblinks"></a> Linki replikacji bazy danych  
Po zainstalowaniu nowej lokacji w hierarchii programu Configuration Manager automatycznie tworzy łącze replikacji bazy danych między lokacją nadrzędną i nowej lokacji. Jedno łącze służy do połączenia dwóch lokacji.  

Możesz zmienić ustawienia w ramach poszczególnych łączy replikacji bazy danych ułatwiające kontrolę transferu danych za pośrednictwem łącza replikacji. Każde łącze replikacji obsługuje różne konfiguracje. Są dostępne następujące kontrolki łączy replikacji bazy danych:  

-  Zatrzymania replikacji danych wybranej lokacji z lokacji głównej do centralnej lokacji administracyjnej, w centralnej lokacji administracyjnej wymaga dostępu do tych danych bezpośrednio z bazy danych lokacji głównej.  
-  Planowanie wybranych danych na przesyłanie z podrzędnej lokacji głównej do centralnej lokacji administracyjnej.
-  Definiowanie ustawień umożliwiających określenie, gdy łącze replikacji bazy danych znajduje się w stanie obniżeniem lub nie powiodła się.
-  Określ, kiedy warunków zgłaszania alertów dotyczących uszkodzonego łącza replikacji.
-  Określ, jak często programu Configuration Manager znajduje się podsumowanie danych dotyczących obciążenia związanego z łącza replikacji. Te dane są używane w raportach.

Aby skonfigurować łącze replikacji bazy danych, w konsoli programu Configuration Manager na **replikacji bazy danych** węzła, edytować właściwości odpowiedniego łącza. Ten węzeł jest dostępny zarówno w **monitorowanie** obszaru roboczego i **administracji** obszaru roboczego na **Konfiguracja hierarchii** węzła. Łącze replikacji można edytować z poziomu lokacji nadrzędnej lub podrzędnej.  

> [!TIP]  
> Linki replikacji bazy danych można edytować w węźle **Replikacja bazy danych** w każdym obszarze roboczym. Jednak jeśli używasz **replikacji bazy danych** w węźle **monitorowanie** obszaru roboczego, również można wyświetlić stan replikacji za pośrednictwem łączy replikacji bazy danych i narzędzia Analizator łącza replikacji, aby badać problemy z replikacją baz danych.  

Informacje o sposobie konfigurowania linków replikacji znajdują się w sekcji [Kontrolki replikacji bazy danych lokacji](#BKMK_DBRepControls). Aby uzyskać więcej informacji o sposobie monitorowania replikacji, zobacz [jak monitorować stan łącza i replikacji replikacji bazy danych](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_MonitorRepLinksAndStatuss) w [Monitorowanie infrastruktury hierarchii i replikacji w programie System Center Configuration Manager](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md) tematu.  

Skorzystaj z informacji w poniższych sekcjach ułatwią zaplanowanie łączy replikacji bazy danych.  

### <a name="bkmk_distviews"></a> Widoki rozproszone  
Za pośrednictwem widoków rozproszonych żądań wysyłanych do lokacji centralnej administracji wybrane dostęp do danych lokacji danych lokacji bezpośrednio z bazy danych w podrzędnej lokacji głównej. Bezpośredniemu dostępowi konieczność replikacji danych lokacji z lokacji głównej do centralnej lokacji administracyjnej. Każde łącze replikacji są niezależne od siebie, można użyć widoków rozproszonych w łączach replikacji, która zostanie wybrana. Nie można używać widoków rozproszonych między lokacją główną a lokacją dodatkową.  

Widoki rozproszone zapewniają następujące korzyści:  

-  Zmniejszenie obciążenia procesora CPU związanego z przetwarzaniem zmian w bazie danych w centralnej lokacji administracyjnej i lokacjach głównych
-  Zmniejsz ilość danych transferowanych przez sieć do centralnej lokacji administracyjnej
-  Lepsza wydajność programu SQL server, który obsługuje bazę danych witryny Administracja centralna
-  Zmniejszenie miejsca na dysku używanego przez bazę danych w centralnej lokacji administracyjnej

Należy rozważyć użycie widoków rozproszonych, gdy lokacja główna znajduje się w sąsiedztwie centralnej lokacji administracyjnej w sieci, a dwie lokacje są stale włączone i zawsze połączone. Jest to spowodowane Dzięki widokom rozproszonym zamiast replikacji wybranych danych między lokacjami można używać bezpośrednich połączeń między serwerami SQL w każdej lokacji. Połączenie bezpośrednie jest nawiązywane każdym wysłaniu żądania danych w centralnej lokacji administracyjnej. Zazwyczaj żądania danych dostępnych w ramach widoków rozproszonych są wysyłane w przypadku uruchamiania raportów lub kwerend, wyświetlania informacji w Eksploratorze zasobów oraz oceny kolekcji zawierających zasady oparte na danych lokacji.  

Domyślnie widoki rozproszone są wyłączone dla każdego łącza replikacji. Po włączeniu widoków rozproszonych w ramach łącza replikacji należy wybrać dane lokacji, które nie będą replikowane do centralnej lokacji administracyjnej za pośrednictwem tego łącza. Centralna lokacja administracyjna uzyskuje dostęp do tych danych bezpośrednio z bazy danych lokacji podrzędnej udostępniającej łącze. W widokach rozproszonych można skonfigurować następujące typy danych lokacji:  

-  Dane dotyczące zapasów sprzętu klientów
-  Dane dotyczące zapasów oprogramowania i pomiarów klienta
-  Komunikaty o stanie klientów, lokacji głównej i wszystkich lokacji dodatkowych

Pod względem operacyjnym widoki rozproszone nie są widoczne dla użytkowników administracyjnych wyświetlających dane w raportach lub w konsoli programu Configuration Manager. Po wysłaniu żądania danych uwzględnionych w widokach rozproszonych, SQL server, który obsługuje bazę danych do centralnej lokacji administracyjnej bezpośrednio uzyskuje dostęp do programu SQL server podrzędnej lokacji głównej można pobrać informacji. Na przykład użyć konsoli programu Configuration Manager w centralnej lokacji administracyjnej żądanie informacji dotyczących zapasów sprzętu z dwóch lokacji, a tylko jedna lokacja ma włączone w widoku rozproszonym spisu sprzętu. Informacje o zapasach klientów z lokacji nieskonfigurowanej w ramach widoków rozproszonych są pobierane z bazy danych w centralnej lokacji administracyjnej. Informacje o zapasach klientów z lokacji, który jest skonfigurowany w widokach rozproszonych jest dostępny w bazie danych w podrzędnej lokacji głównej. Te informacje są wyświetlane w konsoli programu Configuration Manager lub w raporcie bez identyfikowania źródła.  

Tak długo, jak łącze replikacji zawiera typ danych uwzględnionych w widokach rozproszonych, podrzędna lokacja główna nie replikuje danych do centralnej lokacji administracyjnej. Zaraz po wyłączeniu widoków rozproszonych określonego typu danych, obiekt podrzędny głównej witryny wznawia replikacji danych do centralnej lokacji administracyjnej w ramach normalnego procesu replikacji danych. Jednak przed te dane są dostępne w witrynie Administracja centralna, grupy replikacji, które mają te dane należy ponownie zainicjować między lokacją główną a centralną lokacją administracyjną. Podobnie po odinstalowaniu lokacji głównej, która ma włączone widoki rozproszone centralnej lokacji administracyjnej należy wykonać ponowne inicjowanie swoich danych, aby dostęp do danych, które zostały włączone dla widoków rozproszonych w centralnej lokacji administracyjnej.  

> [!IMPORTANT]  
> Korzystając z widoków rozproszonych w dowolnym łączu replikacji w hierarchii lokacji, należy wyłączyć widoki rozproszone dla wszystkich łączy replikacji, przed odinstalowaniem lokacji głównej. Aby uzyskać więcej informacji, zobacz [Odinstalowywanie lokacji głównej skonfigurowanej z widokami rozproszonymi](../../../core/servers/deploy/install/uninstall-sites-and-hierarchies.md#BKMK_UninstallPrimaryDistViews).  

#### <a name="prerequisites-and-limitations-for-distributed-views"></a>Wymagania wstępne i ograniczenia dotyczące widoków rozproszonych  

-  Korzystając z widoków rozproszonych tylko w łączach replikacji między centralną lokacją administracyjną a lokacją główną.
- Centralna lokacja administracyjna musi używać wersji Enterprise programu SQL Server. Lokacja główna nie ma tego wymogu.
-  Centralna lokacja administracyjna może mieć zainstalowane tylko jedno wystąpienie dostawcy programu SMS, a to wystąpienie musi być zainstalowane na serwerze bazy danych lokacji. Jest to wymagane do obsługi uwierzytelniania Kerberos, dzięki którym SQL server w centralnej lokacji administracyjnej mają dostęp do serwera SQL w podrzędnej lokacji głównej. Nie istnieją ograniczenia dotyczące dostawcy programu SMS w podrzędnej lokacji głównej.
-  Centralna lokacja administracyjna może mieć zainstalowany tylko jeden punkt usług SQL Server Reporting Services, który musi znajdować się na serwerze bazy danych lokacji. Jest to wymagane do obsługi uwierzytelniania Kerberos, wymaganego do włączenia usługi SQL server w centralnej lokacji administracyjnej na dostęp do serwera SQL w podrzędnej lokacji głównej.
-  Baza danych lokacji nie może być hostowana w klastrze programu SQL Server.
-  Bazy danych lokacji nie może być umieszczona w grupie dostępności programu SQL Server AlwaysOn.
-  Konto komputera serwera bazy danych z centralnej lokacji administracyjnej wymaga uprawnień odczytu do bazy danych lokacji w lokacji głównej.

> [!IMPORTANT]  
>  Widoki rozproszone i harmonogramy replikacji danych to wzajemnie wykluczające ustawienia dla łącza replikacji bazy danych.  

### <a name="BKMK_schedules"></a> Harmonogramy transferów danych lokacji w linkach replikacji bazy danych  
W celu ułatwienia kontroli przepustowości sieci używanej w ramach replikacji danych z podrzędnej lokacji głównej do jej centralnej lokacji administracyjnej istnieje można zaplanować używanie łącza replikacji oraz określić moment replikacji poszczególnych typów danych lokacji. Istnieje możliwość skonfigurowania, kiedy lokacja główna ma replikować komunikaty o stanie, zapasy oraz dane pomiarów. Łącza replikacji bazy danych z lokacji dodatkowych nie obsługują harmonogramów dla danych lokacji. Zaplanowanie transferu danych globalnych nie jest możliwe.  

Podczas konfigurowania harmonogramu łącza replikacji bazy danych można ograniczyć transfer wybranych danych z lokacji głównej do centralnej lokacji administracyjnej oraz skonfigurować różne czasy replikacji poszczególnych typów danych lokacji.  

> [!IMPORTANT]  
> Widoki rozproszone i harmonogramy replikacji danych to wzajemnie wykluczające się konfiguracje w ramach łącza replikacji bazy danych.  

### <a name="BKMK_SummarizeDBReplication"></a> Podsumowanie ruchu związanego z replikacją bazy danych  
Każda lokacja okresowo tworzy podsumowanie danych dotyczących obciążenia sieci w ramach łączy replikacji bazy danych lokacji. Podsumowanie danych jest używane w raportach dotyczących replikacji bazy danych. Obie lokacje należące do łącza replikacji podsumowują obciążenie sieci występujące na tym łączu. Dane podsumowuje programu SQL Server hostujący bazę danych lokacji. Po podsumowywania danych do innych lokacji są replikowane informacje jako dane globalne.  

Podsumowanie odbywa się domyślnie co 15 minut. Aby zmienić częstotliwość podsumowania ruchu sieciowego, we właściwościach łącza replikacji bazy danych, należy edytować **interwał podsumowania**. Częstotliwość podsumowania wpływa na informacje, które można wyświetlić w raportach dotyczących replikacji bazy danych. Można wybrać między 5 minut do 60 minut. Zwiększenie częstotliwości podsumowania, możesz zwiększyć obciążenie związane z przetwarzaniem na serwerze SQL server w każdej lokacji objętej łączem replikacji.  

### <a name="BKMK_DBRepThresholds"></a>Progi replikacji bazy danych  
Progi replikacji bazy danych pozwalają zdefiniować, kiedy ma być zgłaszane nieprawidłowe działanie lub uszkodzenie łącza replikacji bazy danych. Domyślnie łącze ustawiono obniżeniem statusu gdy wszystkie grupy replikacji nie może przeprowadzić replikacji w okresie 12 kolejnych prób. Łącze ma ustawioną stanu nie powiodło się, gdy wszystkie grupy replikacji nie powiedzie się do replikacji w 24 kolejnych prób.  

Można określić wartości niestandardowe w celu dopasowania, gdy program Configuration Manager zaraportuje działanie lub uszkodzenie łącza replikacji. Dopasowywanie, gdy program Configuration Manager zaraportuje się, że każdy stan łączy replikacji bazy danych ułatwia precyzyjne monitorowanie kondycji replikacji bazy danych za pośrednictwem łączy replikacji bazy danych.  

Ponieważ jest możliwe w dla jednej lub kilku grupach replikacji, aby zakończyć się niepowodzeniem, a w innych grupach replikacji w dalszym ciągu powodzeniem, należy zaplanować sprawdzenie stanu łącza replikacji po raz pierwszy zgłosi obniżeniem stanu. Jeżeli w pewnych grupach replikacji cyklicznie występują opóźnienia, które nie powodują problemu, lub gdy przepustowość łącza sieciowego między lokacjami jest niska, zaleca się zmodyfikowanie wartości ponownych prób przed zgłoszeniem nieprawidłowego działania lub uszkodzenia łącza. Zwiększenie liczby ponownych prób przed określeniem łącze nieprawidłowego działania lub uszkodzenia można wyeliminować fałszywe ostrzeżenia dotyczące znanych problemów i bardziej precyzyjnie monitorować stan łącza.  

Ponadto należy wziąć pod uwagę interwał synchronizacji replikacji dla każdej grupy replikacji zrozumieć, jak często z tej grupy replikacji. Aby wyświetlić **interwał synchronizacji** dla grup replikacji w **monitorowanie** obszaru roboczego na **replikacji bazy danych** węzła, wybierz opcję **szczegóły replikacji** łącza replikacji.  

Aby uzyskać więcej informacji o sposobie monitorowania replikacji bazy danych, w tym wyświetlaniu stanu replikacji, zobacz [jak monitorować stan łącza i replikacji replikacji bazy danych](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_MonitorRepLinksAndStatuss) w [Monitorowanie infrastruktury hierarchii i replikacji w programie System Center Configuration Manager](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md) tematu.  

Aby uzyskać informacje o konfigurowaniu progów replikacji bazy danych, zobacz [kontrolki replikacji bazy danych lokacji](#BKMK_DBRepControls).  

## <a name="BKMK_DBRepControls"></a> Kontrolki replikacji bazy danych lokacji  
Możesz zmienić ustawienia dla każdej bazy danych lokacji w celu ułatwienia kontroli przepustowości sieci używanej w ramach replikacji bazy danych. Ustawienia dotyczą tylko bazy danych lokacji, w którym można skonfigurować ustawienia. Ustawienia są zawsze stosowane podczas żadnych danych replikacji bazy danych do innych lokacji.  

Kontrolki replikacji, które można modyfikować dla każdej bazy danych lokacji są następujące:  

-  Zmień SSB port.  
-  Skonfiguruj okres oczekiwania zanim niepowodzenia replikacji wyzwolenia lokacji ponowną inicjalizację kopii bazy danych lokacji.  
-  Skonfiguruj bazę danych lokacji, aby dane były kompresowane w ramach replikacji bazy danych. Dane są kompresowane tylko w ramach transferu między lokacjami, a nie przechowywania w bazie danych lokacji po jednej stronie.  

Aby zmienić ustawienia dla kontrolki replikacji bazy danych lokacji, w konsoli programu Configuration Manager na **replikacji bazy danych** węzła, edytować właściwości bazy danych lokacji. Ten węzeł jest wyświetlany w węźle **Konfiguracja hierarchii** obszaru roboczego **Administracja** , a także w obszarze roboczym **Monitorowanie**. Aby edytować właściwości bazy danych lokacji, wybierz łącze replikacji między lokacjami, a następnie otwórz opcję **właściwości nadrzędnej bazy danych** lub **właściwości podrzędnej bazy danych**.  

> [!TIP]  
> Kontrolki replikacji bazy danych można skonfigurować w węźle **Replikacja bazy danych** w każdym obszarze roboczym. Jednak jeśli używasz **replikacji bazy danych** w węźle **monitorowanie** obszaru roboczego, również można wyświetlić stan replikacji bazy danych w ramach łącza replikacji i narzędzia Analizator łącza replikacji, aby badać problemy z replikacją.  
