---
title: Konfigurowanie odnajdywania | Dokumentacja firmy Microsoft
description: "Skonfiguruj metody odnajdywania w lokacji programu Configuration Manager można znaleźć zasoby, którymi można zarządzać z infrastruktury sieci i usługi Active Directory."
ms.custom: na
ms.date: 2/17/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 49505eb1-d44d-4121-8712-e0f3d8b15bf5
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 860815010068422f2d8854ed2d574c24cc386891
ms.openlocfilehash: 63a3c2ef66c80d1da9b50e67166a2196cf1b081b
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="configure-discovery-methods-for-system-center-configuration-manager"></a>Skonfiguruj metody odnajdywania dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


Skonfiguruj metody odnajdywania w lokacji programu System Center Configuration Manager można znaleźć zasoby, którymi można zarządzać z infrastruktury sieci i usługi Active Directory. Wymaga to włączenia, a następnie skonfiguruj każdej metody, które chcesz użyć, aby wyszukać w środowisku. (Można również wyłączyć metody za pomocą tej samej procedury, która umożliwia ją włączyć.)  Jedynym wyjątkiem są odnajdywania pulsu oraz serwera:  

-   Domyślnie odnajdywanie pulsu jest już włączona po zainstalowaniu lokacji głównej programu Configuration Manager i skonfigurowanych do działania na podstawowe harmonogramu. Jest dobrym pomysłem jest włączone, ponieważ zapewnia, że rekordów danych odnajdowania (DDR) urządzeń są aktualne odnajdywanie pulsu warto pozostawić. Aby uzyskać więcej informacji dotyczących odnajdywania pulsu, zobacz [informacje o odnajdywaniu pulsu](../../../../core/servers/deploy/configure/about-discovery-methods.md#bkmk_aboutHeartbeat).  

-   Odnajdowanie serwera to metoda automatycznego odnajdywania wyszukuje komputery używane jako systemy lokacji. Nie można skonfigurować lub wyłączyć.  

**Aby włączyć każdą metodę odnajdywania można skonfigurować:**  

1.  W konsoli programu Configuration Manager wybierz **Administracja** > **Konfiguracja hierarchii**, a następnie wybierz **metody odnajdywania**.  

2.  Wybierz metodę odnajdywania dla lokacji, w której chcesz włączyć odnajdywanie.  

3.  Na **Home** w karcie **właściwości** grupy, wybierz **właściwości**, a następnie na **ogólne** zaznacz **włączyć&lt;metody odnajdywania\>**  pole.  

     Jeśli to pole jest już zaznaczone, Metoda odnajdywania można wyłączyć przez usunięcie zaznaczenia tego pola.  

4.  Wybierz **OK** Aby zapisać konfigurację.  


##  <a name="BKMK_ConfigADForestDisc"></a>Konfigurowanie odnajdywania lasu usługi Active Directory  
Aby ukończyć konfigurację odnajdywania lasu usługi Active Directory, należy skonfigurować ustawienia w dwóch miejscach:  

-   W **metody odnajdywania** węzła, można wykonywać następujące czynności:

    - Włączyć tę metodę odnajdywania.
    - Ustaw harmonogram sondowania.
    - Wybierz, czy odnajdywanie ma automatycznie tworzyć granice dla lokacji usługi Active Directory i podsieci, które wykryje.  

-   W **lasy usługi Active Directory** węzła, można wykonywać następujące czynności:

    - Dodać lasy, które chcesz odnaleźć.
    - Włącz odnajdywanie lokacji usługi Active Directory i podsieci w tym lesie.
    - Skonfiguruj ustawienia, które umożliwiają lokacji programu Configuration Manager publikowanie informacji o ich lokacji do lasu.
    - Przypisywanie konta do użycia jako konto lasu usługi Active Directory w każdym lesie.  

Użyj poniższych procedur, aby włączyć odnajdywanie lasu usługi Active Directory, a do skonfigurowania poszczególnych lasów na użytek odnajdywania lasu usługi Active Directory.  

#### <a name="to-enable-active-directory-forest-discovery"></a>Aby włączyć odnajdywanie lasu usługi Active Directory  

1.  W konsoli programu Configuration Manager wybierz **Administracja** > **Konfiguracja hierarchii**, a następnie wybierz **metody odnajdywania**.  

2.  Wybierz metodę odnajdywania lasu usługi Active Directory dla lokacji, w której chcesz skonfigurować odnajdywanie.  

3.  Na **Home** w karcie **właściwości** grupy, wybierz **właściwości**.  

4.  Na **ogólne** karta, pole wyboru, aby włączyć odnajdywanie. Lub można skonfigurować odnajdywanie teraz, a następnie wróć do włączenia odnajdywania później.  

5.  Określ opcje dotyczące tworzenia granic lokacji dla odnajdywanych lokalizacji.  

6.  Określ harmonogram uruchamiania odnajdywania.  

7.  Po zakończeniu konfigurowania odnajdywania lasu usługi Active Directory dla tej lokacji, wybierz **OK** Aby zapisać konfigurację.  

#### <a name="to-configure-a-forest-for-active-directory-forest-discovery"></a>Aby skonfigurować las dla odnajdywania lasu usługi Active Directory  

1.  W **Administracja** obszaru roboczego, wybierz **lasy usługi Active Directory**. Jeśli odnajdywanie lasu za pomocą usługi Active Directory było wcześniej uruchamiane, wszystkie odnalezione lasy zostaną wyświetlone w okienku wyników. Uruchomienie odnajdywania lasu za pomocą usługi Active Directory powoduje odnalezienie lasu lokalnego oraz wszystkich lasów zaufanych. Ręcznie należy dodać tylko lasy niezaufane.  

    -   W celu skonfigurowania poprzednio odnalezionego lasu wybierz go w okienku wyników. Następnie na **Home** w karcie **właściwości** grupy, wybierz **właściwości** otworzyć właściwości lasu. Przejdź do kroku 3.  

    -   Do skonfigurowania nowego lasu, który nie ma na liście, na **Home** w karcie **Utwórz** grupy, wybierz **Dodaj las** otworzyć **Dodawanie lasów** okno dialogowe. Przejdź do kroku 3.  

2.  Na **ogólne** pozycję Zakończ konfigurację lasu, który chcesz odnaleźć i określ **konto lasu usługi Active Directory**.  

    > [!NOTE]  
    >  Aby odnajdywać lasy niezaufane i w nich publikować, odnajdywanie lasu usługi Active Directory wymaga konta globalnego. Jeśli nie używasz konta komputera serwera lokacji, można wybrać tylko konto globalne.  

3.  Aby umożliwić witryn publikowania danych lokacji w tym lesie na **publikowania** pozycję Zakończ konfigurację publikowania w tym lesie.  

    > [!NOTE]  
    >  Dopuszczenie do nieograniczonego lokacji publikowanie w lesie, należy rozszerzyć schemat usługi Active Directory tego lasu dla programu Configuration Manager. Konto lasu usługi Active Directory musi mieć uprawnienia Pełna kontrola do kontenera systemu w tym lesie.  

4.  Po zakończeniu konfiguracji tego lasu do stosowania z odnajdywaniem lasu usługi Active Directory, wybierz **OK** Aby zapisać konfigurację.  

##  <a name="BKMK_ConfigADDiscGeneral"></a>Konfigurowanie odnajdywania usługi Active Directory dla komputerów, użytkowników lub grup  
 Użyj informacje w poniższych sekcjach do skonfigurowania funkcji odnajdywania komputerów, użytkowników lub grup. Użyjesz tych metod odnajdywania:  

-   Odnajdywanie grupy usługi Active Directory  

-   Odnajdywanie systemu usługi Active Directory  

-   odnajdywanie użytkownika usługi Active Directory  

> [!NOTE]  
>  Informacje przedstawione w tej sekcji nie dotyczą odnajdywania lasu usługi Active Directory.  

 Mimo że każda z tych metod odnajdywania niezależnie od innych, to mają wspólne, podobne opcje. Aby uzyskać więcej informacji o tych opcjach konfiguracji, zobacz [udostępniane opcje odnajdywania grupy, System i użytkownik](../../../../core/servers/deploy/configure/about-discovery-methods.md#bkmk_shared).  

> [!WARNING]  
>  Sondowanie usługi Active Directory każdą z tych metod odnajdywania może powodować znaczne obciążenie sieci. Warto pomyśleć o zaplanowaniu każdej metody odnajdywania w czasie, kiedy obciążenie sieci nie wpływa na biznesowych korzystanie z sieci.  

#### <a name="to-configure-active-directory-group-discovery"></a>Aby skonfigurować odnajdywanie grupy usługi Active Directory  

1.  W konsoli programu Configuration Manager wybierz **Administracja** > **Konfiguracja hierarchii**, a następnie wybierz **metody odnajdywania**.  

2.  Wybierz **odnajdywania grupy usługi Active Directory** metodę dla lokacji, w której chcesz skonfigurować odnajdywanie.  

3.  Na **Home** w karcie **właściwości** grupy, wybierz **właściwości**.  

4.  Na **ogólne** karta, pole wyboru, aby włączyć odnajdywanie. Lub można skonfigurować odnajdywanie teraz, a następnie wróć do włączenia odnajdywania później.  

5.  Wybierz **Dodaj** do skonfigurowania zakresu odnajdywania, wybierz **grup** lub **lokalizacji**i Zakończ następujące konfiguracje w **Dodawanie grup** lub **Dodawanie lokalizacji usługi Active Directory** okno dialogowe:  

    1.  Określ **nazwa** dla tego zakresu odnajdywania.  

    2.  Określ **domeny usługi Active Directory** lub **lokalizacji** do wyszukania:  

        -   Jeśli została wybrana opcja **grup**, określ jedną lub więcej grup usługi Active Directory do odnalezienia.  

        -   Jeśli została wybrana opcja **lokalizacji**, określ kontener usługi Active Directory jako lokalizację do odnalezienia. Można również włączyć wyszukiwanie cykliczne we wszystkich kontenerach podrzędnych usługi Active Directory dla tej lokalizacji.  

    3.  Określ **konto odnajdywania grupy usługi Active Directory** używane do przeszukiwania tego zakresu odnajdywania.  

    4.  Wybierz **OK** Aby zapisać konfigurację zakresu odnajdywania.  

6.  Powtórz krok 6 dla każdego dodatkowego zakresu odnajdywania, który chcesz zdefiniować.  

7.  Na **harmonogram sondowania** skonfiguruj zarówno sondowania pełnego odnajdywania, harmonogram i odnajdywanie zmian.  

8.  Opcjonalnie na **opcja** karcie, można skonfigurować opcje odfiltrowywania, czyli wykluczania starych rekordów z procesu odnajdywania i odnajdywania członkostwa w grupach dystrybucyjnych.  

    > [!NOTE]  
    >  Domyślnie odnajdywanie grupy usługi Active Directory odnajduje tylko członkostwo w grupach zabezpieczeń.  

9. Po zakończeniu konfigurowania odnajdywania grupy usługi Active Directory dla tej lokacji wybrać **OK** Aby zapisać konfigurację.  

#### <a name="to-configure-active-directory-system-discovery"></a>Aby skonfigurować odnajdywanie systemu usługi Active Directory  

1.  W konsoli programu Configuration Manager wybierz **Administracja** > **Konfiguracja hierarchii**, a następnie wybierz **metody odnajdywania**.  

2.  Wybierz metodę dla lokacji, w której chcesz skonfigurować odnajdywanie.  

3.  Na **Home** w karcie **właściwości** grupy, wybierz **właściwości**.  

4.  Na **ogólne** karta, pole wyboru, aby włączyć odnajdywanie. Lub można skonfigurować odnajdywanie teraz, a następnie wróć do włączenia odnajdywania później.  

5.  Wybierz **nowy** ikona ![nowa ikona](media/Disc_new_Icon.gif) , aby określić nowy kontener usługi Active Directory. W **kontener usługi Active Directory** okna dialogowego pozycję Zakończ następujące konfiguracje:  

    1.  Określ jedną lub więcej lokalizacji do przeszukania.  

    2.  Dla każdej lokalizacji określ opcje, które zmieniają sposób wyszukiwania.  

    3.  Dla każdej lokalizacji określ konto do użycia jako **konto odnajdywania usługi Active Directory**.  

        > [!TIP]  
        >  Dla każdej lokalizacji określonej przez użytkownika można skonfigurować zestaw opcji odnajdywania i unikatowe konto odnajdywania Active Directory.  

    4.  Wybierz **OK** Aby zapisać konfigurację kontenera usługi Active Directory.  

6.  Na **harmonogram sondowania** skonfiguruj zarówno sondowania pełnego odnajdywania, harmonogram i odnajdywanie zmian.  

7.  Opcjonalnie na **atrybuty usługi Active Directory** karcie, można skonfigurować dodatkowe atrybuty usługi Active Directory dla komputerów, które chcesz odnaleźć. Wymienione także domyślne atrybuty obiektów.  

8.  Opcjonalnie na **opcja** karcie, można skonfigurować opcje odfiltrowywania, czyli wykluczania starych rekordów z procesu odnajdywania.  

9. Po zakończeniu konfigurowania odnajdywania systemu usługi Active Directory dla tej lokacji wybrać **OK** Aby zapisać konfigurację.  

#### <a name="to-configure-active-directory-user-discovery"></a>Aby skonfigurować odnajdywanie użytkowników usługi Active Directory  

1.  W konsoli programu Configuration Manager wybierz **Administracja** > **Konfiguracja hierarchii**, a następnie wybierz **metody odnajdywania**.  

2.  Wybierz **odnajdywania użytkownika usługi Active Directory** metodę dla lokacji, w której chcesz skonfigurować odnajdywanie.  

3.  Na **Home** w karcie **właściwości** grupy, wybierz **właściwości**.  

4.  Na **ogólne** karta, pole wyboru, aby włączyć odnajdywanie. Lub można skonfigurować odnajdywanie teraz, a następnie wróć do włączenia odnajdywania później.  

5.  Wybierz **nowy** ikona ![nowa ikona](media/Disc_new_Icon.gif) , aby określić nowy kontener usługi Active Directory. W **kontener usługi Active Directory** okna dialogowego pozycję Zakończ następujące konfiguracje:  

    1.  Określ jedną lub więcej lokalizacji do przeszukania.  

    2.  Dla każdej lokalizacji określ opcje, które zmieniają sposób wyszukiwania.  

    3.  Dla każdej lokalizacji określ konto do użycia jako **konto odnajdywania usługi Active Directory**.  

        > [!NOTE]  
        >  Dla każdej lokalizacji określonej przez użytkownika można skonfigurować unikatowy zestaw opcji odnajdywania i unikatowe konto odnajdywania Active Directory.  

    4.  Wybierz **OK** Aby zapisać konfigurację kontenera usługi Active Directory.  

6.  Na **harmonogram sondowania** skonfiguruj zarówno sondowania pełnego odnajdywania, harmonogram i odnajdywanie zmian.  

7.  Opcjonalnie na **atrybuty usługi Active Directory** karcie, można skonfigurować dodatkowe atrybuty usługi Active Directory dla komputerów, które chcesz odnaleźć. Wymienione także domyślne atrybuty obiektów.  

8.  Po zakończeniu konfigurowania odnajdywania użytkownika usługi Active Directory dla tej lokacji wybrać **OK** Aby zapisać konfigurację.  

##  <a name="BKMK_ConfigHBDisc"></a>Konfigurowanie odnajdywania pulsu  
 Domyślnie odnajdywanie pulsu jest włączane podczas instalowania lokacji głównej programu Configuration Manager. W związku z tym wystarczy tylko skonfigurować harmonogram, jak często wysłania klientów rekord danych odnajdywania pulsu do punktu zarządzania, jeśli nie chcesz używać domyślnie co siedem dni.  

> [!NOTE]  
>  Jeśli zarówno wypychana instalacja klienta, jak i obsługę lokacji zadanie **Wyczyść flagę instalacji** są włączone w tej samej lokacji, ustawić harmonogram odnajdywania pulsu mniejszej niż **okres ponownego odnajdywania klienta** z **Wyczyść flagę instalacji** zadanie obsługi lokacji. Aby uzyskać więcej informacji na temat zadań konserwacji lokacji, zobacz [zadania konserwacji programu System Center Configuration Manager](../../../../core/servers/manage/maintenance-tasks.md).  

#### <a name="to-configure-the-heartbeat-discovery-schedule"></a>Aby skonfigurować harmonogram odnajdywania pulsu  

1.  W konsoli programu Configuration Manager wybierz **Administracja** > **Konfiguracja hierarchii**, a następnie wybierz **metody odnajdywania**.  

2.  Wybierz **odnajdywania pulsu** dla lokacji, w której chcesz skonfigurować odnajdywanie pulsu.  

3.  Na **Home** w karcie **właściwości** grupy, wybierz **właściwości**.  

4.  Skonfiguruj częstotliwość, z którym klienci Prześlij rekord danych odnajdywania pulsu, a następnie wybierz **OK** Aby zapisać konfigurację.  

##  <a name="BKMK_ConfigNetworkDisc"></a>Skonfigurowanie funkcji odnajdowania sieci  
 Użyj informacje w poniższych sekcjach ułatwiają konfigurowanie odnajdywania sieci.  

###  <a name="BKMK_AboutConfigNetworkDisc"></a>Informacje o konfigurowaniu odnajdywania sieci  
 Przed konfigurowaniem odnajdywania sieci należy zrozumieć następujące kwestie:  

-   Dostępne poziomy odnajdywania sieci  

-   Dostępne opcje odnajdywania sieci  

-   Ograniczanie odnajdywania sieci w sieci  

Aby uzyskać więcej informacji, zobacz [informacje o odnajdywaniu sieci](../../../../core/servers/deploy/configure/about-discovery-methods.md#bkmk_aboutNetwork).  

 Poniższe sekcje zawierają informacje o popularnych konfiguracjach odnajdywania sieci. Można skonfigurować jeden lub więcej z tych konfiguracji do użycia podczas odnajdywania tego samego uruchomienia. W przypadku wykorzystania wielu konfiguracji należy odpowiednio zaplanować interakcje, które mogą mieć wpływ na wyniki odnajdywania.  

 Można na przykład odnajdywanie wszystkich urządzeń protokołu Simple Network Management Protocol (SNMP), które używają określonej nazwy wspólnoty SNMP. Ponadto w tym samym uruchomieniu odnajdywania można wyłączyć odnajdywanie w określonej podsieci. Po uruchomieniu odnajdywania, funkcja odnajdowania sieci nie odnajdzie urządzeń SNMP o określonej nazwie Wspólnoty w podsieci, które zostały wyłączone.  

####  <a name="BKMK_DetermineNetTopology"></a>Ustalenie topologii sieci  
 Odnajdowanie tylko topologii służy do mapowania sieci. Ten rodzaj odnajdywania nie odnajduje potencjalnych klientów. Odnajdowanie tylko topologii opiera się na SNMP.  

 W przypadku mapowania topologii sieci, należy skonfigurować **maksymalna liczba przeskoków** na **SNMP** karcie w **odnajdowanie sieci: właściwości** okno dialogowe. Wystarczy kilka przeskoków może pomóc w kontrolowaniu przepustowości sieci, który jest używany podczas uruchamiania odnajdywania. W miarę odnajdywania dalszych obszarów sieci można zwiększyć liczbę przeskoków w celu uzyskania lepszej orientacji w topologii sieci.  

 Po zidentyfikowaniu topologii sieci można skonfigurować dodatkowe właściwości odnajdywania sieci w celu odnajdywania potencjalnych klientów i ich systemów operacyjnych, a równocześnie używać dostępnych konfiguracji do ograniczania segmentów sieci, które odnajdywanie sieci może przeszukiwać.  

####  <a name="BKMK_LimitBySubnet"></a>Ogranicz wyszukiwania za pomocą podsieci  
 Można skonfigurować odnajdywanie sieci pod kątem przeszukiwania określonych podsieci podczas odnajdywania. Domyślnie funkcja odnajdowania sieci przeszukuje podsieć serwera, na którym działa odnajdywanie. Dodatkowe podsieci, które można skonfigurować i włączyć stosują się tylko do protokołu SNMP i protokół dynamicznej konfiguracji hosta (DHCP) opcji wyszukiwania. Kiedy funkcja odnajdowania sieci przeszukuje domeny, nie jest ograniczone konfiguracjami dotyczącymi podsieci.  

 W przypadku określenia jednej lub kilku podsieci na **podsieci** karcie w **odnajdowanie sieci: właściwości** okno dialogowe, tylko podsieci oznaczone jako **włączone** są przeszukiwane.  

 W momencie wyłączenia podsieci jest ona wykluczana z odnajdywania i mają zastosowanie następujące warunki:  

-   W podsieci nie są uruchamiane zapytania oparte na protokole SNMP.  

-   Serwery DHCP nie odpowiadają wyświetleniem listy zasobów znajdujących się w podsieci.  

-   Zapytania oparte na domenie mogą odnajdywać zasoby znajdujące się w podsieci.  

####  <a name="BKMK_SearchByDomain"></a>Przeszukiwanie określonej domeny  
 Można skonfigurować odnajdywania sieci w celu przeszukania określonej domeny lub zestawu domen podczas pracy odnajdywania. Domyślnie funkcja odnajdowania sieci przeszukuje lokalną domenę serwera, na którym działa odnajdywanie.  

 W przypadku określenia jednej lub kilku domen na **domen** karcie w **odnajdowanie sieci: właściwości** okno dialogowe, domen, które są oznaczone jako **włączone** są przeszukiwane.  

 Po wyłączeniu domeny jest ona wykluczana z odnajdywania i mają zastosowanie następujące warunki:  

-   Funkcja odnajdowania sieci nie odpytuje kontrolerów domeny w tej domenie.  

-   Nadal można uruchomić kwerendy oparte na protokole SNMP na podsieci w domenie.  

-   Serwery DHCP nadal mogą odpowiedzieć listę zasobów znajdujących się w domenie.  

####  <a name="BKMK_LimitBySNMPname"></a>Ogranicz wyszukiwania za pomocą nazw wspólnot SNMP  
 Konfigurowanie odnajdywania sieci w celu przeszukania określonej Wspólnoty SNMP lub zestawów Wspólnot podczas pracy odnajdywania. Domyślnie nazwa Wspólnoty **publicznych** jest skonfigurowana do użycia.  

 Funkcja odnajdowania sieci korzysta z nazw Wspólnot w celu uzyskania dostępu do routerów, które są urządzeniami SNMP. Router może udostępnić funkcji odnajdowania sieci informacje o innych routerach i podsieciach połączonych z pierwszym routerem.  

> [!NOTE]  
>  Nazwy wspólnot SNMP przypominają hasła. Odnajdowania sieci może pobrać informację tylko z urządzenia SNMP, dla którego określono nazwę Wspólnoty. Każde urządzenie SNMP może mieć własną nazwę Wspólnoty, ale często jest współużytkowany z tej samej nazwy Wspólnoty korzysta kilka urządzeń. Ponadto większość urządzeń SNMP ma domyślną nazwę Wspólnoty **publiczny**. Jednak usunięcie niektórych organizacjach **publicznych** nazwę Wspólnoty z ich urządzeń ze względów bezpieczeństwa.  

 Jeśli kilka Wspólnot SNMP są pokazywane na **SNMP** karcie w **odnajdowanie sieci: właściwości** okno dialogowe odnajdowania sieci przeszukuje je w kolejności, w której są wyświetlane. Aby zminimalizować ruch sieciowy, który jest generowany przez próby połączenia z urządzeniem przy użyciu różnych nazw, należy umieścić najczęściej używane nazwy na początku listy.  

> [!NOTE]  
>  Oprócz korzystania z nazwy wspólnoty SNMP można określić adres IP lub rozpoznawalną nazwę urządzenia SNMP. Można to zrobić na **urządzeń SNMP** karcie w **odnajdowanie sieci: właściwości** okno dialogowe.  

####  <a name="BKMK_SearchByDHCP"></a>Przeszukiwanie określonego serwera DHCP  
 Można skonfigurować odnajdywanie sieci do korzystania z określonego serwera DHCP lub kilku serwerów do odnajdywania klientów DHCP podczas pracy odnajdywania.  

 Funkcja odnajdowania sieci przeszukuje każdy serwer DHCP określony na **DHCP** karcie w **odnajdowanie sieci: właściwości** okno dialogowe. Jeśli na serwerze, na którym działa odnajdywanie wydzierżawi swój adres IP z serwera DHCP, można skonfigurować odnajdywanie do przeszukania tego serwera DHCP, zaznaczając **Dołącz serwer DHCP, który serwer lokacji jest skonfigurowany do używania** pole.  

> [!NOTE]  
>  Aby pomyślnie skonfigurować serwer DHCP w ramach odnajdywania sieci, środowisko musi obsługiwać protokół IPv4. Nie można skonfigurować odnajdywanie sieci do używania serwera DHCP w macierzystym środowisku IPv6.  

###  <a name="BKMK_HowToConfigNetDisc"></a>Jak skonfigurować odnajdywanie sieci  
 Poniższe procedury umożliwiają najpierw wykrycie tylko topologii sieci, a następnie skonfigurowanie funkcji odnajdowania sieci w celu odnalezienia potencjalnych klientów za pomocą jednej lub kilku dostępnych opcji odnajdowania sieci.  

##### <a name="to-determine-your-network-topology"></a>Aby określić topologię sieci  

1.  W konsoli programu Configuration Manager wybierz **Administracja** > **Konfiguracja hierarchii**, a następnie wybierz **metody odnajdywania**.  

2.  Wybierz **odnajdowania sieci** dla lokacji, w której chcesz uruchomić odnajdowanie sieci.  

3.  Na **Home** w karcie **właściwości** grupy, wybierz **właściwości**.  

    -   Na **ogólne** zaznacz **Włącz odnajdowanie sieci** polu, a następnie wybierz **topologii** z **typu odnajdywania** opcje.  

    -   Na **podsieci** zaznacz **lokalnej podsieci** pole.  

        > [!TIP]  
        >  Jeśli znasz podsieci tworzą używaną sieć, można usunąć zaznaczenie **przeszukiwania podsieci lokalnej** pole i używać **nowy** ikona ![ikonę Nowy](media/Disc_new_Icon.gif) do dodania określonych podsieci, które chcesz przeszukać. W przypadku dużych sieci jest często optymalnym tylko jednej lub dwóch podsieci naraz w celu zminimalizowania użycia przepustowości sieci.  

    -   Na **domen** zaznacz **Przeszukaj domenę lokalną** pole.  

    -   Na **SNMP** użyj **maksymalna liczba przeskoków** listy rozwijanej, aby określić liczbę przeskoków odnajdowania sieci może wykonać podczas mapowania topologii.  

        > [!TIP]  
        >  Przed pierwszym mapowaniem topologii sieci, należy skonfigurować tylko kilka przeskoków, aby zminimalizować użycie przepustowości sieci.  

4.  Na **harmonogram** , wybierz **nowy** ikona ![nowa ikona](media/Disc_new_Icon.gif) ustawić harmonogram uruchamiania funkcji odnajdowania sieci.  

    > [!NOTE]  
    >  Nie można przypisać różnych konfiguracji odnajdywania do oddzielnych harmonogramów funkcji odnajdowania sieci. Przy każdym uruchomieniu funkcja odnajdowania sieci korzysta z bieżącej konfiguracji odnajdywania.  

5.  Wybierz **OK** aby zaakceptować konfiguracje. Funkcja odnajdowania sieci działa w zaplanowanym terminie.  

##### <a name="to-configure-network-discovery"></a>Aby skonfigurować odnajdywanie sieci  

1.  W konsoli programu Configuration Manager wybierz **Administracja** > **Konfiguracja hierarchii**, a następnie wybierz **metody odnajdywania**.  

2.  Wybierz **odnajdowania sieci** dla lokacji, w której chcesz uruchomić odnajdowanie sieci.  

3.  Na **Home** w karcie **właściwości** grupy, wybierz **właściwości**.  

4.  Na **ogólne** zaznacz **Włącz odnajdowanie sieci** polu, a następnie wybierz typ odnajdywania, który chcesz uruchomić z **typu odnajdywania** opcje.  

5.  Aby skonfigurować odnajdywanie w celu przeszukiwania podsieci, wybierz **podsieci** , a następnie skonfiguruj co najmniej jedną z następujących opcji:  

    -   Aby uruchomić odnajdywanie w podsieciach lokalnych dla komputera, na którym działa odnajdywanie, sprawdź **lokalnej podsieci** pole.  

    -   Aby przeszukać określoną podsieć, upewnij się, że podsieci jest wymieniony w **podsieci do przeszukania** i ma **wyszukiwania** wartość **włączone**:  

        1.  Jeżeli podsieć nie jest widoczna na liście, wybierz **nowy** ikona ![nowa ikona](media/Disc_new_Icon.gif). W **nowe przypisanie podsieci** okna dialogowego wprowadź **podsieci** i **maski** informacji, a następnie wybierz **OK**. Domyślnie nowa podsieć jest włączona do przeszukiwania.  

        2.  Aby zmienić **wyszukiwania** wartość dla podsieci widocznej na liście, wybierz podsieć, a następnie wybierz **przełączania** ikonę, aby przełączyć między wartością **wyłączone** i **włączone**.  

6.  Aby skonfigurować odnajdywanie w celu przeszukiwania domen, wybierz **domen** , a następnie skonfiguruj co najmniej jedną z następujących opcji:  

    -   Aby uruchomić odnajdywanie w domenie komputera, który przeprowadza odnajdywanie, sprawdź **Przeszukaj domenę lokalną** pole.  

    -   Aby przeszukać określoną domenę, upewnij się, że domena jest wymieniony w **domen** i ma **wyszukiwania** wartość **włączone**:  

        1.  Jeśli domena nie jest widoczna na liście, wybierz opcję **nowy** ikona ![nowa ikona](media/Disc_new_Icon.gif). W **właściwości domeny** okna dialogowego wprowadź **domeny** informacji, a następnie wybierz **OK**. Domyślnie nowa domena jest włączona do przeszukiwania.  

        2.  Aby zmienić **wyszukiwania** wartość dla domeny widocznej na liście, wybierz domenę, a następnie wybierz **przełączania** ikonę, aby przełączyć między wartością **wyłączone** i **włączone**.  

7.  Aby skonfigurować odnajdywanie w celu przeszukiwania nazw wspólnot SNMP dla urządzeń SNMP, wybierz **SNMP** , a następnie skonfiguruj co najmniej jedną z następujących opcji:  

    -   Aby dodać nazwę wspólnoty SNMP do listy **nazw wspólnot SNMP**, wybierz **nowy** ikona ![nowa ikona](media/Disc_new_Icon.gif). W **Nowa nazwa wspólnoty SNMP** okna dialogowego określ **nazwa** Wspólnoty SNMP, a następnie wybierz **OK**.  

    -   Aby usunąć nazwę wspólnoty SNMP, wybierz nazwę Wspólnoty, a następnie wybierz **usunąć** ikona ![ikonę Usuń](media/Disc_delete_Icon.gif).  

    -   Aby dostosować kolejność przeszukiwania nazw wspólnot SNMP, wybierz nazwę Wspólnoty, a następnie wybierz **Przenieś element w górę** ikona ![przenieść ikonę](media/Disc_moveUp_Icon.gif) lub **Przenieś element w dół** ikona ![przenieść ikonę](media/Disc_moveDown_Icon.gif). Po uruchomieniu odnajdywania nazwy Wspólnot są przeszukiwane w kolejności od góry do dołu. Należy uwzględnić następujące kwestie.

        > [!NOTE]  
        >  Funkcja odnajdowania sieci korzysta z nazw wspólnot SNMP w celu uzyskania dostępu do routerów, które są urządzeniami SNMP. Router może przekazać funkcji odnajdowania sieci informacje o innych routerach i podsieciach połączonych z pierwszym routerem.  

        -   Nazwy wspólnot SNMP przypominają hasła.  

        -   Odnajdowania sieci może pobrać informację tylko z urządzenia SNMP, dla którego określono nazwę Wspólnoty.  

        -   Każde urządzenie SNMP może mieć własną nazwę Wspólnoty, ale często jest współużytkowany z tej samej nazwy Wspólnoty korzysta kilka urządzeń.  

        -   Większość urządzeń SNMP ma domyślną nazwę Wspólnoty **publiczny**. Można go używać, jeśli nie znasz inne nazwy Wspólnot. Jednak usunięcie niektórych organizacjach **publicznych** nazwę Wspólnoty z ich urządzeń ze względów bezpieczeństwa.  

8.  Aby skonfigurować maksymalną liczbę przeskoków do użytku przez wyszukiwania SNMP, wybierz **SNMP** , a następnie wybierz liczbę przeskoków z **maksymalna liczba przeskoków** listy rozwijanej.  

9. Aby skonfigurować urządzenia SNMP, wybierz **urządzeń SNMP** kartę. Jeśli urządzenie nie jest tam wymienione, wybierz **nowy** ikona ![nowa ikona](media/Disc_new_Icon.gif). W **nowe urządzenie SNMP** okno dialogowe, określ nazwę urządzenia lub adres IP urządzenia SNMP, a następnie wybierz **OK**.  

    > [!NOTE]  
    >  W przypadku określenia nazwy urządzenia, programu Configuration Manager musi być w stanie rozpoznać nazwę NetBIOS na adres IP.  

10. Aby skonfigurować odnajdywanie do badania określonych serwerów DHCP dla klientów DHCP, wybierz **DHCP** , a następnie skonfiguruj co najmniej jedną z następujących opcji:  

    -   Aby odpytać serwer DHCP na komputerze, na którym działa odnajdowanie, sprawdź **zawsze używaj serwer DHCP serwera lokacji** pole.  

        > [!NOTE]  
        >  Aby użyć tej opcji, serwer musi wydzierżawić swój adres IP z serwera DHCP i nie może używać statycznego adresu IP.  

    -   Aby odpytać określony serwer DHCP, wybierz **nowy** ikona ![nowa ikona](media/Disc_new_Icon.gif). W **nowy serwer DHCP** okno dialogowe, określ nazwę serwera lub adres IP serwera DHCP, a następnie wybierz **OK**.  

        > [!NOTE]  
        >  W przypadku określenia nazwy serwera, programu Configuration Manager musi być w stanie rozpoznać nazwę NetBIOS na adres IP.  

11. Skonfigurowania po uruchomieniu odnajdywania, wybierz opcję **harmonogram** karcie, a następnie wybierz **nowy** ikona ![nowa ikona](media/Disc_new_Icon.gif) ustawić harmonogram uruchamiania funkcji odnajdowania sieci.  

     Można skonfigurować kilka harmonogramów cyklicznych i kilka harmonogramów bez cyklu.  

    > [!NOTE]  
    >  Jeśli wiele harmonogramów są pokazywane na **harmonogram** kartę w tym samym czasie wszystkie harmonogramy spowodować odnajdowania sieci działa dla zgodnie z konfiguracją o godzinie określonej w harmonogramie. Dotyczy to również harmonogramów cyklicznych.  

12. Wybierz **OK** Aby zapisać konfiguracje.  

###  <a name="BKMK_HowToVerifyNetDisc"></a>Jak sprawdzić, czy funkcja odnajdowania sieci zakończyła działanie  
 Czas odnajdowania sieci wymaga, aby zakończyć może się różnić w zależności od różnych czynników. Te czynniki może zawierać jeden lub więcej z następujących czynności:  

-   Rozmiar sieci  

-   Topologia sieci  

-   Maksymalna liczba przeskoków skonfigurowanych do znalezienia routerów w sieci  

-   Typ uruchomionego odnajdowania zostanie uruchomione  

Ponieważ funkcja odnajdowania sieci nie tworzy komunikatów powiadamiających o zakończeniu odnajdowania, służy poniższej procedury, aby sprawdzić, czy odnajdowanie zostało zakończone.  

##### <a name="to-verify-that-network-discovery-has-finished"></a>Aby sprawdzić, czy funkcja odnajdowania sieci zakończyła działanie  

1.  W konsoli programu Configuration Manager wybierz **monitorowanie**.  

2.  W **monitorowanie** obszaru roboczego, rozwiń węzeł **stan systemu**, a następnie wybierz **kwerendy komunikatów o stanie**.  

3.  Wybierz **wszystkie komunikaty o stanie**.  

4.  Na **Home** w karcie **kwerendy komunikatów o stanie** grupy, wybierz **Pokaż komunikaty**.  

5.  W **wybierz datę i godzinę** listy rozwijanej, wybierz wartość zawierającą czas przed rozpoczęto odnajdowanie, a następnie wybierz **OK** otworzyć **Podgląd komunikatów o stanie Menedżera konfiguracji**.  

    > [!TIP]  
    >  Można również użyć **Określ datę i godzinę** opcję, aby wybrać daną datę i godzinę uruchomienia odnajdowania. Ta opcja jest przydatna, gdy uruchomiono funkcję odnajdowania sieci w danym dniu i konieczne jest pobranie komunikatów tylko z tego dnia.  

6.  Aby sprawdzić, czy funkcja odnajdowania sieci zakończyła działanie, wyszukaj komunikat o stanie zawierający następujące informacje:  

    -   Identyfikator komunikatu: **502**  

    -   Składnik: **SMS_NETWORK_DISCOVERY**  

    -   Opis: **Ten składnik został zatrzymany**  

    Jeśli ten komunikat o stanie nie jest obecny, funkcja odnajdowania sieci nie zostało zakończone.  

7.  Aby sprawdzić, kiedy uruchomienie funkcji odnajdowania sieci, wyszukaj komunikat o stanie zawierający następujące informacje:  

    -   Identyfikator komunikatu: **500**  

    -   Składnik: **SMS_NETWORK_DISCOVERY**  

    -   Opis: **Ten składnik został rozpoczęty**  

    Te informacje oznaczają uruchomienie funkcji odnajdowania sieci. Jeśli te informacje nie jest obecny, Zmień harmonogram odnajdywania sieci.  

