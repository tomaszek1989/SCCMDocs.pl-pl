---
title: Metody odnajdywania | Dokumentacja firmy Microsoft
ms.custom: na
ms.date: 2/3/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ed931751-18f2-4230-a09e-a0a329fbfa1c
caps.latest.revision: 8
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 81d7516b814d2db74d4d857871071c8911755754
ms.openlocfilehash: 6e53f501281e31f2b7df54b9740eac970f108257
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="about-discovery-methods-for-system-center-configuration-manager"></a>Informacje o metodach odnajdywania dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Metody odnajdywania programu System Center Configuration Manager można znaleźć różnych urządzeń w sieci lub urządzeń i użytkowników z usługi Active Directory. Aby wydajnie korzystać z metody odnajdywania, należy zapoznać się jej dostępnych konfiguracji i ograniczenia.  

##  <a name="bkmk_aboutForest"></a>Odnajdywanie lasu usługi Active Directory  
 **Można skonfigurować:** Tak  

 **Domyślnie włączone:** Nie  

 **Konta** służy do uruchamiania tej metody:  

-   **Konto odnajdywania lasu usługi Active Directory** (zdefiniowane przez użytkownika)  

-   **Konto komputera** serwera lokacji  

W odróżnieniu od innych metod odnajdywania usługi Active Directory odnajdowanie lasu usługi Active Directory nie odnajduje zasobów, którymi można zarządzać. Zamiast tego metoda ta umożliwia odnalezienie lokalizacje sieciowe, które są skonfigurowane w usłudze Active Directory i konwertowanie tych lokalizacjach funkcję granic używanych w całej hierarchii.  

Po uruchomieniu tej metody wyszukiwania w lokalnym lesie usługi Active Directory, w każdym zaufanym lesie oraz w każdym dodatkowym lesie skonfigurowanym w **lasy usługi Active Directory** węzeł konsoli programu Configuration Manager.  

Odnajdywanie lasu usługi Active Directory użyj:  

-   Odnajdywanie lokacji usługi Active Directory i podsieci, a następnie utwórz granice programu Configuration Manager oparte na tych lokalizacjach sieciowych.  

-   Zidentyfikuj supernets, które są przypisane do lokacji usługi Active Directory i konwertowanie każdego supersieć na granicę zakres adresów IP.  

-   Po włączeniu opcji publikowania w tym lesie a określone konto lasu usługi Active Directory ma odpowiednie uprawnienia tego lasu i publikować w usługach domenowych Active Directory (AD DS) w lesie.  

Odnajdowanie lasu usługi Active Directory można zarządzać w konsoli programu Configuration Manager w następujących węzłach w obszarze **Konfiguracja hierarchii** w **administracji** obszaru roboczego:  

-   **Metody odnajdywania**: W tym miejscu można włączyć odnajdowanie lasu usługi Active Directory w lokacji najwyższego poziomu hierarchii. Można również określić prosty harmonogram odnajdywania i skonfigurować go, aby automatycznie utworzyć granice z podsieci IP i lokacji usługi Active Directory, które wykryje. Odnajdywanie lasu usługi Active Directory nie można uruchomić w podrzędnej lokacji głównej lub w lokacji dodatkowej.  

-   **Lasy usługi Active Directory**: Umożliwia skonfigurowanie dodatkowych lasów usługi Active Directory, przeznaczonych do odnalezienia, określenie konta używanego jako konto lasu usługi Active Directory w każdym lesie oraz skonfigurowanie publikowania w każdym lesie. Ponadto można monitorować proces odnajdywania i dodawać podsieci IP i lokacji usługi Active Directory do programu Configuration Manager jako granic i członków grup granic.  

Aby skonfigurować publikowanie w lasach usługi Active Directory dla każdej lokacji w hierarchii, należy połączyć konsola programu Configuration Manager do lokacji najwyższego poziomu w hierarchii. **Publikowania** kartę w lokacji usługi Active Directory **właściwości** okno dialogowe można wyświetlić tylko bieżąca lokacja i jej lokacji podrzędnych. Po włączeniu opcji publikowania w lasach i rozszerzeniu schematu tego lasu dla programu Configuration Manager, dla każdej lokacji, które mogą publikować informacje w tym lesie usługi Active Directory są publikowane następujące informacje:  

-    **SMS-witryny -&lt;kod lokacji >**

-   **SMS-MP -&lt;kod lokacji >-&lt;nazwy serwera systemu lokacji >**  

-   **SMS-SLP -&lt;kod lokacji >-&lt;nazwy serwera systemu lokacji >**  

-   **SMS -&lt;kod lokacji >-&lt;Nazwa lokacji usługi Active Directory lub podsieci >**  

> [!NOTE]  
>  Lokacje dodatkowe zawsze publikują dane w usłudze Active Directory przy użyciu konta komputera serwera lokacji dodatkowej. Lokacje dodatkowe do publikowania w usłudze Active Directory, upewnij się, że konto komputera serwera lokacji dodatkowej ma uprawnienia do publikowania w usłudze Active Directory. Lokacja dodatkowa nie może publikować danych w niezaufanym lesie.  

> [!CAUTION]  
>  Wyczyść pole wyboru opcji publikowania lokacji w lesie usługi Active Directory, wszystkie wcześniej publikowane informacje dotyczące tej lokacji z uwzględnieniem ról systemu lokacji, usunięcie z usługi Active Directory.  

Akcje dla odnajdywania lasu usługi Active Directory są rejestrowane w następujących dziennikach:  

-   Wszystkie działania, z wyjątkiem działań związanych z publikowaniem są rejestrowane w **ADForestDisc.Log** pliku w  **&lt;Ścieżkainstalacyjna > \Logs** folder na serwerze lokacji.  

-   Akcje związane z publikowaniem są rejestrowane w odnajdywania lasu usługi Active Directory **hman.log** i **sitecomp.log** pliki w  **&lt;Ścieżkainstalacyjna > \Logs** folder na serwerze lokacji.  

Aby uzyskać więcej informacji o sposobie konfiguracji metody odnajdywania, zobacz [skonfiguruj metody odnajdywania dla programu System Center Configuration Manager](../../../../core/servers/deploy/configure/configure-discovery-methods.md).  

##  <a name="bkmk_aboutGroup"></a>Odnajdywanie grupy usługi Active Directory  
**Można skonfigurować:** Tak  

**Domyślnie włączone:** Nie  

**Konta** służy do uruchamiania tej metody:  

-   **Konto odnajdywania grupy usługi Active Directory** (zdefiniowane przez użytkownika)  

-   **Konto komputera** serwera lokacji  

> [!TIP]  
>  Oprócz informacji w tej sekcji znajduje się w temacie [typowych funkcji grupy usługi Active Directory, System i odnajdowanie użytkowników](#bkmk_shared).  

Ta metoda umożliwia wyszukiwanie w usługach domenowych Active Directory do identyfikowania:  

-   Grupy zabezpieczeń lokalnych, globalnych i uniwersalnych.  

-   Członkostwo w grupach.  

-   Ograniczone informacje o grupy komputerów i użytkowników, nawet jeśli innej metody odnajdywania nie został wcześniej odnaleziono tych komputerów i użytkowników.  

Ta metoda służy do identyfikowania grup oraz relacji członków grup. Domyślnie są odnajdywane tylko grupy zabezpieczeń. Jeśli chcesz również znaleźć członkostwo grup dystrybucyjnych, należy sprawdzić pole opcji **odnajdywania członkostwa w grupach dystrybucyjnych** na **opcja** karcie w **właściwości odnajdywania grupy usługi Active Directory** okno dialogowe.  

Odnajdywanie grupy usługi Active Directory nie obsługuje rozszerzonych atrybutów usługi Active Directory można zidentyfikować za pomocą odnajdywania systemu usługi Active Directory lub odnajdywania użytkownika usługi Active Directory. Ta metoda nie jest przeznaczona do odnajdywania zasobów komputerów i użytkowników, dlatego należy uruchomić po metodach odnajdywania systemu usługi Active Directory i odnajdowanie użytkowników usługi Active Directory. Jest tak, ponieważ ta metoda tworzy rekord danych pełnego odnajdywania (DDR) dla grupy, ale tylko ograniczony DDR dla komputerów i użytkowników, którzy są członkami grupy.  

Można skonfigurować następujących zakresów odnajdywania kontrolujących sposób wyszukiwania tej metody informacji:  

-   **Lokalizacja**: Jeśli chcesz wyszukać przynajmniej jednej kontenerach usługi Active Directory, należy użyć lokalizacji. Ta opcja zakresu umożliwia cykliczne wyszukiwanie w określonych kontenerach usługi Active Directory wyszukująca każdego kontenera podrzędnego w kontenerze, który określisz. Ten proces jest kontynuowany, dopóki nie zostaną znalezione nie więcej kontenerów podrzędnych.  

-   **Grupy**: Jeśli chcesz wyszukać jeden lub więcej określonych grup usługi Active Directory za pomocą grup. Można skonfigurować **domeny usługi Active Directory** do używania domyślnej domeny i lasu lub ograniczyć wyszukiwanie do poszczególnych kontrolerów domeny. Ponadto można określić jedną lub więcej grup do wyszukiwania. Jeśli nie określisz przynajmniej jednej grupy, wszystkie grupy znalezione w określonym **domeny usługi Active Directory** lokalizacji są przeszukiwane.  

> [!CAUTION]  
>  Podczas konfigurowania zakresu odnajdywania należy wybrać tylko grupy, które muszą zostać odnalezione. Jest to spowodowane odnajdywania grupy usługi Active Directory próbuje odnaleźć wszystkich członków poszczególnych grup objętych zakresem odnajdywania. Odnajdywanie dużych grup może powodować zwiększone użycie przepustowości i zasobów usługi Active Directory.  

> [!NOTE]  
>  Przed mogą tworzyć kolekcje, które są oparte na rozszerzonych atrybutów usługi Active Directory (i zapewnienie odnajdywania dokładne wyniki dla komputerów i użytkowników), należy uruchomić odnajdywania systemu usługi Active Directory lub odnajdywania użytkownika usługi Active Directory, w zależności od tego, co chcesz odnaleźć.  

Akcje dla odnajdywania grupy usługi Active Directory są rejestrowane w pliku **adsgdis.log** w  **&lt;Ścieżkainstalacyjna\>\LOGS** folder na serwerze lokacji.  

Aby uzyskać więcej informacji o sposobie konfiguracji metody odnajdywania, zobacz [skonfiguruj metody odnajdywania dla programu System Center Configuration Manager](../../../../core/servers/deploy/configure/configure-discovery-methods.md).  

##  <a name="bkmk_aboutSystem"></a>Odnajdywanie systemu usługi Active Directory  
**Można skonfigurować:** Tak  

**Domyślnie włączone:** Nie  

**Konta** służy do uruchamiania tej metody:  

-   **Konto odnajdywania systemu usługi Active Directory** (zdefiniowane przez użytkownika)  

-   **Konto komputera** serwera lokacji  

> [!TIP]  
>  Oprócz informacji w tej sekcji znajduje się w temacie [typowych funkcji grupy usługi Active Directory, System i odnajdowanie użytkowników](#bkmk_shared).  

Ta metoda umożliwia wyszukiwanie w określonych lokalizacjach usług domenowych w usłudze Active Directory zasobów komputera, które można tworzyć kolekcje i kwerendy. Można również zainstalować klienta programu Configuration Manager odnalezione urządzenia przy użyciu instalacji wypychanej klienta.  

Domyślnie ta metoda odnajduje podstawowe informacje o komputerze, takie jak następujące:  

-   Nazwa komputera  

-   Wersja systemu operacyjnego i  

-   Nazwa kontenera usługi Active Directory  

-   Adres IP  

-   Lokacja usługi Active Directory  

-   Sygnatura czasowa ostatniego logowania  

Aby pomyślnie utworzyć rekord DDR dla komputera, odnajdywania systemu usługi Active Directory musi być rozpoznać konto komputera, a następnie pomyślnie skojarzyć nazwę komputera z adresem IP.  

W **właściwości odnajdywania systemu usługi Active Directory** okna dialogowego na **atrybuty usługi Active Directory** karcie, można wyświetlić pełną listę domyślne atrybuty obiektów, które zwróciło odnajdywania systemu usługi Active Directory. Istnieje również możliwość skonfigurowania metodę odnaleźć dodatkowe atrybuty (rozszerzone).  

Akcje dla odnajdywania systemu usługi Active Directory są rejestrowane w pliku **adsysdis.log** w  **&lt;Ścieżkainstalacyjna\>\LOGS** folder na serwerze lokacji.  

Aby uzyskać więcej informacji o sposobie konfiguracji metody odnajdywania, zobacz [skonfiguruj metody odnajdywania dla programu System Center Configuration Manager](../../../../core/servers/deploy/configure/configure-discovery-methods.md).  

##  <a name="bkmk_aboutUser"></a>Odnajdywanie użytkownika usługi Active Directory  
**Można skonfigurować:** Tak  

**Domyślnie włączone:** Nie  

**Konta** służy do uruchamiania tej metody:  

-   **Konto odnajdywania użytkownika usługi Active Directory** (zdefiniowane przez użytkownika)  

-   **Konto komputera** serwera lokacji  

> [!TIP]  
>  Oprócz informacji w tej sekcji znajduje się w temacie [typowych funkcji grupy usługi Active Directory, System i odnajdowanie użytkowników](#bkmk_shared).  

Ta metoda umożliwia wyszukiwanie w usługach domenowych Active Directory w celu zidentyfikowania kont użytkowników i skojarzonych z nimi atrybutów. Domyślnie ta metoda odnajduje podstawowe informacje o koncie użytkownika, takie jak następujące:  

-   Nazwa użytkownika  

-   Unikatowa nazwa użytkownika (w tym nazwa domeny)  

-   Domain  

-   Nazwy kontenerów usługi Active Directory  

W **właściwości odnajdywania użytkownika usługi Active Directory** okna dialogowego na **atrybuty usługi Active Directory** karcie, można wyświetlić pełną domyślną listę atrybutów obiektów, które zwróciło odnajdywania użytkownika usługi Active Directory. Istnieje również możliwość skonfigurowania metodę odnaleźć dodatkowe atrybuty (rozszerzone).

Akcje dla odnajdywania użytkownika usługi Active Directory są rejestrowane w pliku **adusrdis.log** w  **&lt;Ścieżkainstalacyjna\>\LOGS** folder na serwerze lokacji.  

Aby uzyskać więcej informacji o sposobie konfiguracji metody odnajdywania, zobacz [skonfiguruj metody odnajdywania dla programu System Center Configuration Manager](../../../../core/servers/deploy/configure/configure-discovery-methods.md).  

##  <a name="bkmk_aboutHeartbeat"></a>Odnajdywanie pulsu  
**Można skonfigurować:** Tak  

**Domyślnie włączone:** Tak  

**Konta** służy do uruchamiania tej metody:  

-   **Konto komputera** serwera lokacji  

Odnajdywanie pulsu różni się od innych metod odnajdywania programu Configuration Manager. Jest włączone domyślnie i działa na każdym komputerze klienckim (a nie na serwerze lokacji) do utworzenia rekordu DDR. Dla klientów urządzeń przenośnych ten rekord DDR tworzy punkt zarządzania używany przez klienta urządzenia przenośnego. Aby ułatwić obsługę rekordów bazy danych klientów programu Configuration Manager, nie należy wyłączać odnajdywania pulsu. Oprócz obsługi rekordu bazy danych, ta metoda może wymusić odnajdywanie komputera jako nowego rekordu zasobu lub ponownie wypełnić rekord bazy danych z komputera, który został usunięty z bazy danych.  

Odnajdywanie pulsu jest przeprowadzane zgodnie z harmonogramem skonfigurowanym na wszystkich klientach w hierarchii, lub jeśli ręcznie wywołać na określonym kliencie przez uruchomienie **cykl zbierania danych odnajdowania** na **akcji** kartę w programie Configuration Manager do klienta. Domyślny harmonogram odnajdywania pulsu, jest równa co 7 dni. W przypadku zmiany interwału odnajdywania pulsu, upewnij się, że będzie ono przeprowadzane częściej niż zadanie obsługi lokacji **Usuń przestarzałe dane wykrywania**, która usuwa z bazy danych lokacji rekordów nieaktywnych klientów. Można skonfigurować **Usuń przestarzałe dane wykrywania** zadania tylko w lokacjach głównych.  

Po uruchomieniu odnajdywania pulsu tworzy rekordu DDR, który ma aktualne informacje klienta. Klient następnie skopiowanie to mały plik (o rozmiarze 1 KB) do punktu zarządzania lokacji głównej można go przetworzyć. Plik zawiera następujące informacje:  

-   Lokalizacja sieciowa  

-   Nazwa NetBIOS  

-   Wersja agenta klienta  

-   Szczegóły stanu działania  

Odnajdywanie pulsu to jedyna metoda zapewniająca szczegóły dotyczące stanu instalacji klienta. Robi to za aktualizuje atrybut klienta zasobu systemu, aby ustawić wartość równą **tak**.  

> [!NOTE]  
>  Nawet po wyłączeniu odnajdywania pulsu DDR nadal są tworzone i przesyłane do aktywnych klientów urządzeń przenośnych. Gwarantuje to, że **Usuń przestarzałe dane wykrywania** zadań nie wpływa na aktywne urządzenia przenośne. Powodem jest to, że gdy **Usuń przestarzałe dane wykrywania** zadań usunięcie rekordu bazy danych dla urządzeń przenośnych, również odwołanie certyfikatu tego urządzenia i uniemożliwienie mu łączenia się z punktami zarządzania.  

Akcje odnajdywania pulsu są rejestrowane w następujących lokalizacjach:  

-   Dla komputerów klienckich akcje odnajdywania pulsu są rejestrowane na kliencie w **InventoryAgent.log** pliku w *%Windir%\CCM\Logs* folder.  

-   W przypadku klientów urządzeń przenośnych akcje odnajdywania pulsu są rejestrowane w **DMPRP.log** pliku w *% Program Files%\CCM\Logs* folderu punktu zarządzania używanego przez klienta urządzenia przenośnego.  

Aby uzyskać więcej informacji o sposobie konfiguracji metody odnajdywania, zobacz [skonfiguruj metody odnajdywania dla programu System Center Configuration Manager](../../../../core/servers/deploy/configure/configure-discovery-methods.md).  

##  <a name="bkmk_aboutNetwork"></a>Funkcja odnajdowania sieci  
**Można skonfigurować:** Tak  

**Domyślnie włączone:** Nie  

**Konta** służy do uruchamiania tej metody:  

-   **Konto komputera** serwera lokacji  

Ta metoda umożliwia odnalezienie topologii sieci oraz w celu odnalezienia urządzeń w sieci, które mają adres IP. Funkcja odnajdowania sieci przeszukuje sieci adresu IP zasobów serwerów, które implementacją protokołu DHCP firmy Microsoft, buforuje protokołu rozpoznawania adresów (ARP) w routerach, urządzeń z włączoną obsługą protokołu SNMP oraz domen usługi Active Directory.  

Przed użyciem odnajdowania sieci, należy określić *poziom* odnajdywania. Można również skonfigurować mechanizmów odnajdywania, które Włącz odnajdowanie sieci do kwerendy dla urządzeń lub segmentów sieci. Można również skonfigurować ustawienia ułatwiające kontrolę akcji odnajdywania w sieci. Użytkownik ma możliwość zdefiniowania co najmniej jednego harmonogramu odnajdywania sieci.  

Tę metodę pomyślnie odnaleźć zasób funkcja odnajdowania sieci musi rozpoznać adres IP i maskę podsieci zasobu. Następujące metody są używane do identyfikacji maski podsieci obiektu:  

-   **Pamięć podręczna ARP routera:** Funkcja odnajdowania sieci odpytuje pamięć podręczną ARP routera, aby znaleźć informacje o. Zwykle dane w pamięci podręcznej ARP routera mają krótki czas wygaśnięcia. W związku z tym gdy funkcja odnajdowania sieci odpytuje pamięć podręczną ARP, pamięć podręczną ARP może już informacji o wymaganym obiekcie.  

-   **DHCP:** Funkcja odnajdowania sieci odpytuje każdy serwer DHCP, który określisz w celu odnalezienia urządzeń, dla których serwer DHCP udostępnił dzierżawę. Funkcja odnajdywania sieci obsługuje tylko serwery DHCP firmy Microsoft implementacją protokołu DHCP.  

-   **Urządzenia SNMP:** Funkcja odnajdowania sieci może bezpośrednio odpytywać urządzenie SNMP. Aby funkcja odnajdowania sieci odpytała urządzenie musi ono mieć zainstalowanego lokalnego agenta SNMP. Należy również skonfigurować odnajdywania sieci do używania nazwy społeczności, który używa agenta SNMP.  

Podczas odnajdywania obiekt z adresem IP i może ustalić maskę podsieci obiektów, tworzy DDR dla tego obiektu. Dlatego różne typy urządzeń mogą łączyć się z siecią, funkcja odnajdowania sieci umożliwia odnalezienie zasobów, które nie obsługują oprogramowania klienta programu Configuration Manager. Na przykład urządzenia, które można odnaleźć, ale nie zarządza to drukarki i routery.  

Funkcja odnajdowania sieci może zwrócić kilka atrybutów w ramach odnajdywania tworzy rekord. Należą do nich następujące elementy:  

-   Nazwa NetBIOS  

-   Adresy IP  

-   Domena zasobów  

-   Role systemu  

-   Nazwa wspólnoty SNMP  

-   Adresy MAC  

Działanie funkcji odnajdywania sieci jest rejestrowane w **Netdisc.log** pliku w  *&lt;Ścieżkainstalacyjna\>\Logs* na serwerze lokacji, na którym działa odnajdywanie.  

 Aby uzyskać więcej informacji o sposobie konfiguracji metody odnajdywania, zobacz [skonfiguruj metody odnajdywania dla programu System Center Configuration Manager](../../../../core/servers/deploy/configure/configure-discovery-methods.md).  

> [!NOTE]  
>  Złożone sieci i połączenia o niskiej przepustowości mogą powodować odnajdywania sieci spowolnienie działania oraz generować bardzo duże obciążenie sieci. Najlepszym rozwiązaniem jest uruchamianie odnajdywania sieci tylko wtedy, gdy pozostałe metody odnajdywania nie może znaleźć zasoby, które zostaną odnalezione. Na przykład użyć odnajdowania sieci w przypadku konieczności odnalezienia komputerów grupy roboczej. Inne metody odnajdywania nie wykrywa komputerów grupy roboczej.  

###  <a name="BKMK_NetDiscLevels"></a>Zakresy odnajdywania sieci  
Podczas konfigurowania odnajdywania sieci można określić jeden z trzech następujących zakresów:  

|Zakres odnajdywania|Szczegóły|  
|------------------------|-------------|  
|Topologia|Ten zakres umożliwia odnalezienie routerów i podsieci, ale nie określa maski podsieci obiektów.|  
|Topologia i klient|Oprócz topologii ten poziom odnajduje potencjalnych klientów, takich jak komputery i zasobów, takich jak drukarki i routery. Ten zakres odnajdywania próbuje określić maskę podsieci obiektów, które znajdzie.|  
|Topologia, klient oraz system operacyjny klienta|Ten poziom oprócz topologii i potencjalnych klientów próbuje wykryć nazwa komputera systemu operacyjnego i wersji. Ten poziom używane Windows wywołania przeglądarki oraz obsługi sieci systemu Windows.|  

 Każdy kolejny zakres odnajdowania sieci zwiększa jego działania i przepustowości sieci. Należy wziąć pod uwagę ruch sieciowy, który może zostać wygenerowany przed włączeniem wszystkich aspektów odnajdywania sieci.  

 Na przykład przy pierwszym użyciu odnajdowania sieci, może uruchomić tylko zakres obejmujący topologię do określenia infrastruktury sieci. Następnie można ponownie skonfigurować odnajdywanie sieci umożliwia odnalezienie obiektów i ich systemy operacyjne. Można również konfigurować ustawienia, ograniczających odnajdywania sieci do określonego zakresu segmentów sieci. W ten sposób można odnaleźć obiekty w lokalizacji sieciowych, unikając niepotrzebnego obciążenia sieci i można odnaleźć obiektów w routerach granicznych lub spoza sieci.  

###  <a name="BKMK_NetDiscOptions"></a>Opcje odnajdywania sieci  
Aby włączyć odnajdywanie sieci wyszukać urządzenia z adresem IP, należy skonfigurować co najmniej jedną z następujących opcji, które określają sposób zapytania dla urządzeń.  

> [!NOTE]  
>  Funkcja odnajdowania sieci działa w ramach konta komputera serwera lokacji, który przeprowadza odnajdywanie. Jeśli konto komputera nie ma uprawnień w niezaufanej domenie, domena i konfiguracje serwerów DHCP może zakończyć się niepowodzeniem do odnajdowania zasobów.  

**DHCP:**  

Określ poszczególne serwery DHCP mają odnajdywania sieci do zapytania. (Odnajdywania sieci obsługuje tylko serwery DHCP firmy Microsoft implementacją protokołu DHCP).  

-   Funkcja odnajdywania sieci pobiera informacje przy użyciu zdalnych wywołań procedury do bazy danych na serwerze DHCP.  

-   Funkcja odnajdowania sieci można zbadać zarówno 32-bitowych i 64-bitowych serwerów DHCP w celu uzyskania listy urządzeń zarejestrowanych na każdym serwerze.  

-   Aby funkcja odnajdowania sieci pomyślnie wysłała do serwera DHCP kwerendę konto komputera serwera, na którym działa odnajdywanie musi być członkiem grupy Użytkownicy DHCP na serwerze DHCP. Ten poziom dostępu występuje na przykład po spełnieniu jednego z następujących warunków:  

    -   Określono serwer DHCP jest serwerem DHCP z serwera, na którym działa odnajdywanie.  

    -   Komputer z uruchomioną odnajdywania oraz serwer DHCP znajdują się w tej samej domenie.  

    -   Między komputerze, na którym działa odnajdywanie a serwerem DHCP istnieje zaufanie dwukierunkowe.  

    -   Serwer lokacji jest członkiem grupy Użytkownicy DHCP.  

-   Podczas wyliczania serwera DHCP, go nie zawsze odnajduje statyczne adresy IP. Funkcja odnajdowania sieci nie odnajdzie adresów IP, które są częścią wykluczonych zakres adresów IP na serwerze DHCP. Ponadto nie odnajduje adresów IP zastrzeżonych do ręcznego przypisania.  

**Domeny:**  

Określ poszczególne domeny mają odnajdywania sieci do zapytania.  

-   Konto komputera serwera lokacji przeprowadzający odnajdywanie musi mieć uprawnienia do odczytu kontrolerów domeny w każdej określonej domenie.  

-   Do odnajdywania komputerów z domeny lokalnej, należy włączyć usługę Przeglądarka komputera na co najmniej jeden komputer, który znajduje się w tej samej podsieci co serwer lokacji przeprowadzający odnajdywanie sieci.  

-   Funkcja odnajdowania sieci można odnaleźć wszystkie komputery, które można wyświetlić z poziomu serwera lokacji podczas przeglądania sieci.  

-   Funkcja odnajdowania sieci pobiera adres IP, a następnie żądanie echa protokołu komunikacyjnego sterowania Internetem do każdego znalezionego urządzenia polecenie ping. **Ping** polecenia można ustalić, które komputery są obecnie aktywne.  

**Urządzenia SNMP:**  

Określ poszczególne urządzenia SNMP ma odnajdywania sieci do zapytania.  

-   Funkcja odnajdywania sieci pobiera wartość ipNetToMediaTable z urządzenia SNMP, które odpowiada na kwerendę. Ta wartość zwraca tablice adresów IP komputerów klienckich lub innych zasobów, takich jak drukarki, routery albo inne urządzenia z adresem IP.  

-   Aby wysłać do urządzenia kwerendę, należy określić adres IP lub nazwę NetBIOS tego urządzenia.  

-   Należy skonfigurować funkcję odnajdowania sieci do używania nazwy społeczności urządzenia lub urządzenie odrzuci kwerendę opartą na protokole SNMP.  

###  <a name="BKMK_LimitNetDisc"></a>Ograniczanie odnajdywania sieci  
Gdy funkcja odnajdowania sieci odpytuje urządzenia SNMP na granicy sieci, może zidentyfikować informacje dotyczące podsieci i urządzeń SNMP spoza bezpośredniej sieci. Użyj następujące informacje, aby ograniczyć odnajdowania sieci, konfigurując urządzenia SNMP odnajdywania może się komunikować oraz określając segmenty sieci, do kwerendy.  

**Podsieci:**  

Skonfiguruj podsieci, do których kwerendy odnajdowania sieci podczas używania opcji SNMP i DHCP. Te dwie opcje wyszukiwania tylko włączone podsieci.  

Na przykład w ramach żądania DHCP mogą być zwrócone urządzenia z lokalizacji w całej sieci. Jeśli chcesz odnaleźć tylko urządzenia w określonej podsieci, wybierz i Włącz odpowiednią podsieć na **podsieci** karcie w **odnajdowanie sieci: właściwości** okno dialogowe. Po określeniu i włączeniu podsieci, można ograniczyć przyszłych zadania odnajdywania DHCP oraz SNMP do tych podsieci.  

> [!NOTE]  
>  Konfiguracje podsieci nie ograniczyć obiekty, które **domen** opcja odnajdywania umożliwia odnalezienie.  

**Nazwy wspólnot SNMP:**  

Aby włączyć odnajdywanie sieci i wysłać do urządzenia SNMP kwerendę, odnajdowania sieci można skonfigurować przy użyciu nazwy społeczności urządzenia. Jeśli funkcja odnajdowania sieci nie jest skonfigurowany przy użyciu nazwy społeczności urządzenia SNMP, urządzenie odrzuci kwerendę.  

**Maksymalna liczba przeskoków:**  

Skonfiguruj maksymalną liczbę przeskoków między routerami, ograniczenie liczby segmentów sieci i routerów, jaką funkcja odnajdowania sieci odpytuje za pomocą protokołu SNMP.  

Liczba przeskoków ogranicza liczbę dodatkowych urządzeń i segmentów sieci, jaką funkcja odnajdowania sieci odpytuje.  

Przykładowo odnajdowanie tylko topologii z **0** (zero) przeskoków między routerami odnajduje podsieć, w której znajduje się serwer źródłowy. Zawiera wszystkie routery w tej podsieci.  

Na poniższym diagramie przedstawiono określona funkcja odnajdowania sieci zapytania po przeszukaniu tylko topologii po uruchomieniu na serwerze 1 po określeniu 0 przeskoków: podsieć D i Router 1.  

 ![Obraz odnajdowania z obejściem zero router](media/Disc-0.gif)  

 Na poniższym diagramie przedstawiono jakie topologii i klientów odnajdowania sieci po przeszukaniu zapytania po uruchomieniu na serwerze 1 po określeniu 0 przeskoków między routerami: podsieć D i Router 1 oraz wszyscy potencjalni klienci w podsieci D.  

 ![Obraz odnajdowania z jednym routerem skoku](media/Disc-1.gif)  

 Aby lepiej zrozumieć, jak dodatkowe przeskoki między routerami mogą zwiększyć ilość odnalezionych zasobów sieciowych, należy uwzględnić następującą sieć:  

 ![Obraz odnajdowania z dwóch przeskoków routera](media/Disc-2.gif)  

 Uruchomienie odnajdywania sieci tylko topologii na serwerze 1 z jednego routera przeskoku odnalezienie następujących elementów:  

-   Router 1 i podsieć 10.1.10.0 (znalezione przy zerowej przeskoków) liczbie  

-   Podsieci 10.1.20.0 i 10.1.30.0, podsieć A i Router 2 (znalezione po pierwszym przeskoku)  

> [!WARNING]  
>  Każde zwiększenie liczby przeskoków między routerami może znacznie zwiększyć liczbę odnalezionych zasobów i przepustowości sieci używanej przez funkcję odnajdowania sieci.  

##  <a name="bkmk_aboutServer"></a>Odnajdowanie serwera  
**Można skonfigurować:** Nie  

Oprócz metod odnajdywania użytkownika można skonfigurować program Configuration Manager używa procesu o nazwie **odnajdywania serwera** (SMS_WINNT_SERVER_DISCOVERY_AGENT). Ta metoda odnajdywania tworzy rekordy zasobów komputerów pełniących funkcję systemów lokacji, podobnie jak komputer, który jest skonfigurowany jako punkt zarządzania.  

##  <a name="bkmk_shared"></a>Typowych funkcji odnajdywania grupy usługi Active Directory, odnajdowanie systemu i odnajdowanie użytkowników  
Ta sekcja zawiera informacje o funkcjach, które są wspólne dla następujących metod odnajdywania:  

-   Odnajdywanie grupy usługi Active Directory  

-   Odnajdywanie systemu usługi Active Directory  

-   odnajdywanie użytkownika usługi Active Directory  

> [!NOTE]  
>  Informacje przedstawione w tej sekcji nie dotyczą odnajdywania lasu usługi Active Directory.  

Tych trzech metod odnajdywania są podobne pod względem konfiguracji i operacji. Mogą one odnajdywanie komputerów, użytkowników i informacji o członkostwie w grupie zasobów przechowywanych w usługach domenowych w usłudze Active Directory. Procesem odnajdywania zarządza agent odnajdywania uruchomiony na serwerze lokacji w każdej lokacji, w której skonfigurowano odnajdywanie do uruchomienia. Można skonfigurować każdą z tych metod odnajdywania do wyszukiwania lokalizacji usługi Active Directory jedną lub więcej wystąpień w lasach lokalnych lub zdalnych.  

Gdy odnajdywanie obejmuje zasoby w niezaufanym lesie, agent odnajdywania musi mieć możliwość rozpoznania następujących elementów:  

-   Aby odnaleźć zasób komputera za pomocą odnajdywania systemu usługi Active Directory, agent odnajdywania musi mieć możliwość rozpoznania nazwy FQDN zasobu. Jeśli nie można rozpoznać nazwy FQDN, następnie będzie próby rozpoznania zasobu wg jego nazwy NetBIOS.  

-   Aby odnaleźć zasób użytkownika lub grupy za pomocą odnajdywania użytkownika usługi Active Directory lub odnajdowanie grup usługi Active Directory, agent odnajdywania musi mieć możliwość rozpoznania nazwy FQDN nazwy kontrolera domeny określonej dla danej lokalizacji usługi Active Directory.  

Dla każdej lokalizacji określonej przez użytkownika można skonfigurować indywidualne opcje wyszukiwania, takich jak włączenie cyklicznego wyszukiwania lokalizacji kontenerów podrzędnych usługi Active Directory. Można również skonfigurować unikatowe konto używane podczas wyszukiwania tej lokalizacji. Dzięki temu można swobodnie konfigurować metodę odnajdywania w jednej lokacji, aby wyszukiwać wiele lokalizacji usługi Active Directory w wielu lasach bez konieczności konfigurowania jednego konta z uprawnieniami we wszystkich lokalizacjach.  

Podczas każdej z tych trzech metod odnajdywania działa w określonej lokacji, serwerze lokacji programu Configuration Manager w tej lokacji kontaktuje się z najbliższym kontrolerem domeny w określonym lesie usługi Active Directory do lokalizowania zasobów usługi Active Directory. Domena i las mogą mieć ustawiony dowolny obsługiwany tryb usługi Active Directory. Konto, które można przypisać do każdego wystąpienia lokalizacji musi mieć **odczytu** uprawnienia w określonych lokalizacjach usługi Active Directory dostępu.

Odnajdywania wyszukuje określone lokalizacje obiektów, a następnie próbuje zebrać informacje o tych obiektach. Po zidentyfikowaniu wystarczającej ilości informacji o zasobie jest utworzony rekord DDR. Wymagane informacje zależą od używanej metody odnajdywania.  

Jeśli skonfigurujesz tej samej metody odnajdywania uruchamianych w różnych lokacjach programu Configuration Manager, aby przeprowadzać kwerendy lokalnych serwerów usługi Active Directory, można skonfigurować poszczególnych lokacji unikatowy zestaw opcji odnajdywania. Dane odnajdywania są udostępniane każdej lokacji w hierarchii, dlatego należy unikać nakładania się tych konfiguracji w celu wydajnego odnajdywania zasobów jeden raz. 

W mniejszych środowiskach istnieje możliwość uruchomienia każdej metody odnajdywania w tylko jednej lokacji w hierarchii, aby zmniejszyć obciążenie czynnościami administracyjnymi oraz ryzyko w ramach wielu akcji odnajdywania ponownego odnalezienia tych samych zasobów. Kiedy zminimalizować liczbę lokacji, aby uruchomić odnajdywanie, można zmniejszyć ogólną przepustowość sieci odnajdywania używa. Można również zmniejszyć ogólną liczbę rekordów DDR, które są tworzone i muszą zostać przetworzone przez serwery lokacji.  

Wiele konfiguracji metod odnajdywania nie wymaga wyjaśnień. Więcej informacji o opcjach odnajdywania, które mogą wymagać dodatkowych informacji, przed rozpoczęciem konfigurowania, należy użyć następujących sekcji.  

Poniższe opcje są dostępne w wielu metodach odnajdywania usługi Active Directory:  

-   [Odnajdywanie zmian](#bkmk_delta)  

-   [Filtrowanie starych rekordów na podstawie logowania do domeny](#bkmk_stalelogon)  

-   [Filtrowanie starych rekordów na podstawie hasła komputera](#bkmk_stalepassword)  

-   [Wyszukiwanie niestandardowych atrybutów usługi Active Directory](#bkmk_customAD)  

###  <a name="bkmk_delta"></a>Odnajdywanie zmian  
Dostępne dla:  

-   Odnajdywanie grupy usługi Active Directory  

-   Odnajdywanie systemu usługi Active Directory  

-   odnajdywanie użytkownika usługi Active Directory  

Odnajdywanie zmian nie jest metoda odnajdywania niezależne, lecz opcją dostępną dla metody odnajdywania odpowiednich. Odnajdywanie zmian wyszukuje określone atrybuty usługi Active Directory dla zmiany wprowadzone od czasu ostatniego pełnego cyklu odnajdywania metody odnajdywania zastosowania. Zmiany atrybutów są przesyłane do bazy danych programu Configuration Manager w celu zaktualizowania rekordu odnajdywania zasobów.  

Domyślnie odnajdywanie zmian odbywa się w cyklu 5 minut. Jest to znacznie częściej niż typowe Harmonogram pełnego cyklu odnajdowania.  Częste cyklu jest możliwe, ponieważ odnajdywanie różnicowe używa mniej serwera lokacji i wykonuje zasobów sieciowych niż pełny cykl odnajdywania. W przypadku stosowania metody odnajdywania zmian można zmniejszyć częstotliwość pełnego cyklu odnajdywania w ramach tej metody.  

Odnajdywanie zmian umożliwia wykrywanie najczęstszych zmian są następujące:  

-   Nowe komputery lub użytkownicy dodani do usługi Active Directory  

-   Zmiany w podstawowych informacji dotyczących użytkowników i komputerów  

-   Nowe komputery lub użytkownicy dodani do grupy  

-   Komputery lub użytkownicy usunięci z grupy  

-   Zmiany w obiektach grupy systemu  

Odnajdywanie zmian umożliwia wykrywanie nowych zasobów oraz zmian w członkostwie grupy, ale nie wykrywa usunięcia zasobu z usługi Active Directory. Rekordy DDR utworzone przez odnajdywania zmian są przetwarzane w podobny sposób DDR, które są tworzone przez pełny cykl odnajdywania.  

Odnajdywanie zmian konfiguruje się na **harmonogram sondowania** we właściwościach poszczególnych metod odnajdywania.  

###  <a name="bkmk_stalelogon"></a>Filtrowanie starych rekordów na podstawie logowania do domeny  
Dostępne dla:  

-   Odnajdywanie grupy usługi Active Directory  

-   Odnajdywanie systemu usługi Active Directory  

Można skonfigurować odnajdywanie w celu wykluczenia komputerów przy użyciu rekordu starych na podstawie ostatniego logowania domeny komputera. Gdy ta opcja jest włączona, odnajdywania systemu usługi Active Directory ocenia każdy komputer, który identyfikuje. Odnajdywanie grupy usługi Active Directory ocenia każdy komputer, który jest członkiem grupy, która zostanie wykryta.  

Aby użyć tej opcji:  

-   Komputery muszą być skonfigurowane tak, aby zaktualizować **lastLogonTimeStamp** atrybutu w usługach domenowych w usłudze Active Directory.  

-   Poziom funkcjonalności domeny usługi Active Directory należy wprowadzić do systemu Windows Server 2003 lub nowszy.  

Podczas konfiguracji czas od ostatniego logowania, którego chcesz używać dla tego ustawienia, należy uwzględnić interwał replikacji między kontrolerami domeny.  

Aby skonfigurować filtrowanie **opcja** karcie w **właściwości odnajdywania systemu usługi Active Directory** i **właściwości odnajdywania grupy usługi Active Directory** oknach dialogowych. Wybierz opcję **odnajdź tylko komputery zalogowane w domenie w danym okresie czasu**.  

> [!WARNING]  
>  Podczas konfigurowania tego filtru i **filtrowanie starych rekordów na podstawie hasła komputera**, komputery, które spełniają kryteria filtru albo są wyłączone z odnajdywania.  

###  <a name="bkmk_stalepassword"></a>Filtrowanie starych rekordów na podstawie hasła komputera  
Dostępne dla:  

-   Odnajdywanie grupy usługi Active Directory  

-   Odnajdywanie systemu usługi Active Directory  

Można skonfigurować odnajdywanie w celu wykluczenia komputerów przy użyciu rekordu starych oparte na ostatniej aktualizacji hasła do konta komputera przez komputer. Gdy ta opcja jest włączona, odnajdywania systemu usługi Active Directory ocenia każdy komputer, który identyfikuje. Odnajdywanie grupy usługi Active Directory ocenia każdy komputer, który jest członkiem grupy, która zostanie wykryta.  

Aby użyć tej opcji:  

-   Komputery muszą być skonfigurowane tak, aby zaktualizować **pwdLastSet** atrybutu w usługach domenowych w usłudze Active Directory.  

Podczas konfiguracji tej opcji, należy uwzględnić również interwał aktualizacji tego atrybutu, oprócz interwału replikacji między kontrolerami domeny.  

Aby skonfigurować filtrowanie **opcja** karcie w **właściwości odnajdywania systemu usługi Active Directory** i **właściwości odnajdywania grupy usługi Active Directory** oknach dialogowych. Wybierz opcję **odnajdź tylko komputery, które zaktualizowały swoje hasło konta komputera w danym okresie czasu**.  

> [!WARNING]  
>  Podczas konfigurowania tego filtru i **filtrowanie starych rekordów na podstawie logowania do domeny**, komputery, które spełniają kryteria filtru albo są wyłączone z odnajdywania.  

###  <a name="bkmk_customAD"></a>Wyszukiwanie niestandardowych atrybutów usługi Active Directory  
 Dostępne dla:  

-   Odnajdywanie systemu usługi Active Directory  

-   odnajdywanie użytkownika usługi Active Directory  

Każda metoda odnajdywania obsługuje unikatową listę atrybutów usługi Active Directory, które można odnaleźć.  

Można wyświetlić i skonfigurować listę atrybutów niestandardowych na **atrybuty usługi Active Directory** karcie w **właściwości odnajdywania systemu usługi Active Directory** i **właściwości odnajdywania użytkownika usługi Active Directory** oknach dialogowych.  

