---
title: Metody odnajdywania
titleSuffix: Configuration Manager
description: Więcej informacji na temat metody odnajdowania dostępne na znalezienie urządzeń w sieci, z usługi Active Directory lub Azure Active Directory.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ed931751-18f2-4230-a09e-a0a329fbfa1c
caps.latest.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: e53eb90b55034479ba3d278b4b19879f2ee1e4b7
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="about-discovery-methods-for-system-center-configuration-manager"></a>Informacje o metodach odnajdywania dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Metody odnajdywania programu Configuration Manager Znajdź różnych urządzeń w sieci, urządzeń i użytkowników usługi Active Directory lub użytkowników z usługi Azure Active Directory (Azure AD). Aby wydajnie korzysta z metody odnajdywania, zapoznaj się jego dostępnych konfiguracji i ograniczenia.  



##  <a name="bkmk_aboutForest"></a> Odnajdywanie lasu usługi Active Directory  
 **Można skonfigurować:** Tak  

 **Domyślnie:** Nie  

 **Konta** służy do uruchamiania tej metody:  

-   **Konto odnajdywania lasu usługi Active Directory** (zdefiniowane przez użytkownika)  

-   **Konto komputera** serwera lokacji  

W odróżnieniu od innych metod odnajdywania usługi Active Directory odnajdowanie lasu usługi Active Directory nie wykryje zasobów, którymi można zarządzać. Zamiast tego ta metoda umożliwia odnajdywanie lokalizacji sieciowych, które są skonfigurowane w usłudze Active Directory. Umożliwia on konwertowanie tych lokalizacjach pełniły funkcję granic używanych w całej hierarchii.  

Po uruchomieniu tej metody wyszukiwania w lokalnym lesie usługi Active Directory, w każdym zaufanym lesie oraz w każdym dodatkowym lesie skonfigurowanym w **lasy usługi Active Directory** węzła konsoli programu Configuration Manager.  

Odnajdywanie lasu usługi Active Directory używany w celu:  

-   Odnajdywanie lokacji usługi Active Directory i podsieci, a następnie tworzyć granice programu Configuration Manager na podstawie tych lokalizacji sieciowych.  

-   Zidentyfikuj supernets, które są przypisane do lokacji usługi Active Directory. Przekonwertuj każdego supersieć na granicy zakresu adresów IP.  

-   Po włączeniu opcji publikowania w tym lesie i publikowania do usług domenowych Active Directory (AD DS) w lesie. Określone konto lasu Active Directory musi mieć uprawnienia do tego lasu.  

Odnajdowanie lasu usługi Active Directory można zarządzać w konsoli programu Configuration Manager. Przejdź do **administracji** obszaru roboczego i rozwiń **Konfiguracja hierarchii**.   

-   **Metody odnajdywania**: Włącz odnajdowanie lasu usługi Active Directory w lokacji najwyższego poziomu w hierarchii. Można również określić prosty harmonogram odnajdywania. Skonfiguruj, aby automatycznie utworzyć granice z podsieci IP i lokacji usługi Active Directory, które wykryje. Odnajdywanie lasu usługi Active Directory nie można uruchomić w podrzędnej lokacji głównej lub lokacji dodatkowej.  

-   **Lasy usługi Active Directory**: Skonfigurowanie dodatkowych lasów, aby sprawdzić, określ każdy konto lasu usługi Active Directory oraz skonfigurowanie publikowania w każdym lesie. Monitorowanie procesu odnajdywania. Dodawanie podsieci IP i lokacji usługi Active Directory jako granic programu Configuration Manager i członków grup granic.  

Aby skonfigurować publikowanie w lasach usługi Active Directory dla każdej lokacji w hierarchii, należy połączyć z konsoli programu Configuration Manager do lokacji najwyższego poziomu w hierarchii. **Publikowania** kartę w lokacji usługi Active Directory **właściwości** okno dialogowe można wyświetlić tylko bieżąca lokacja i jej Lokacje podrzędne. Po włączeniu opcji publikowania w lasach, schemat tego lasu zostanie rozszerzony dla programu Configuration Manager, dla każdej lokacji, które mogą publikować informacje w tym lesie usługi Active Directory są publikowane następujące informacje:  

-    **SMS-Site -&lt;kod lokacji >**

-   **SMS-MP -&lt;kod lokacji >-&lt;nazwy serwera systemu lokacji >**  

-   **SMS-SLP -&lt;kod lokacji >-&lt;nazwy serwera systemu lokacji >**  

-   **SMS -&lt;kod lokacji >-&lt;Nazwa lokacji usługi Active Directory lub podsieć >**  

> [!NOTE]  
>  Lokacje dodatkowe zawsze publikują dane w usłudze Active Directory przy użyciu konta komputera serwera lokacji dodatkowej. Jeśli chcesz, aby Lokacje dodatkowe do publikowania w usłudze Active Directory, upewnij się, że konto komputera serwera lokacji dodatkowej ma uprawnienia do publikowania w usłudze Active Directory. Lokacja dodatkowa nie może publikować danych w niezaufanym lesie.  

> [!CAUTION]  
>  Możesz usunąć zaznaczenie pola wyboru opcji publikowania lokacji w lesie usługi Active Directory, wszystkie wcześniej publikowane informacje dla tej witryny, łącznie z dostępnych ról systemu lokacji, usunięcie z usługi Active Directory.  

Akcje dla odnajdywania lasu usługi Active Directory są rejestrowane w następujących dziennikach:  

-   Wszystkie akcje, z wyjątkiem działań związanych z publikowaniem są rejestrowane w **ADForestDisc.Log** w pliku  **&lt;Ścieżka_instalacji > \Logs** folderu na serwerze lokacji.  

-   Akcje związane z publikowaniem są rejestrowane w odnajdywania lasu usługi Active Directory **hman.log** i **sitecomp.log** plików  **&lt;Ścieżka_instalacji > \Logs** folderu na serwerze lokacji.  

Aby uzyskać więcej informacji o sposobie konfiguracji metody odnajdywania, zobacz [skonfiguruj metody odnajdywania](/sccm/core/servers/deploy/configure/configure-discovery-methods#BKMK_ConfigADForestDisc).  



##  <a name="bkmk_aboutGroup"></a> Odnajdywanie grupy usługi Active Directory  
**Można skonfigurować:** Tak  

**Domyślnie:** Nie  

**Konta** służy do uruchamiania tej metody:  

-   **Konto odnajdowania grup usługi Active Directory** (zdefiniowane przez użytkownika)  

-   **Konto komputera** serwera lokacji  

> [!TIP]  
>  Oprócz informacji w tej sekcji, zobacz [wspólne funkcje grupy usługi Active Directory, systemu i odnajdowanie użytkowników](#bkmk_shared).  

Ta metoda służy do wyszukiwania usług domenowych Active Directory do identyfikowania:  

-   Grupy zabezpieczeń lokalnych, globalnych i uniwersalnych.  

-   Członkostwa w grupach.  

-   Ograniczone informacje dotyczące komputerów należących do grupy i użytkowników, nawet wtedy, gdy innej metody odnajdywania nie został wcześniej odnaleźć tych komputerów i użytkowników.  

Ta metoda odnajdywania służy do identyfikowania grup oraz relacji członków grup. Domyślnie są odnajdywane tylko grupy zabezpieczeń. Jeśli chcesz również znaleźć członkostwo grup dystrybucyjnych, należy zaznaczyć pole obok opcji **odnajdź członkostwo grup dystrybucyjnych** na **opcji** karcie **właściwości odnajdywania grupy usługi Active Directory** okno dialogowe.  

Odnajdywanie grupy usługi Active Directory nie obsługuje rozszerzonych atrybutów usługi Active Directory, które mogą zostać zidentyfikowane przy użyciu odnajdywania systemu usługi Active Directory lub odnajdywania użytkownika usługi Active Directory. Ponieważ ta metoda nie jest przeznaczona do odnajdywania zasobów komputerów i użytkowników, rozważ użycie polecenia ta metoda odnajdywania, po uruchomieniu odnajdywania systemu usługi Active Directory i odnajdowanie użytkowników usługi Active Directory. Sugestia ta jest, ponieważ ta metoda tworzy rekord danych pełnego odnajdywania (DDR) dla grupy, ale tylko ograniczone DDR dla komputerów i użytkowników, którzy są członkami grup.  

Można skonfigurować następujących zakresów odnajdywania kontrolujących sposób tej metody wyszukiwania informacji w ramach:  

-   **Lokalizacja**: Użycie lokalizacji, jeśli chcesz wyszukać co najmniej jeden kontenerach usługi Active Directory. Ta opcja zakresu umożliwia cykliczne wyszukiwanie określonych kontenerach usługi Active Directory. Ten proces wyszukiwanie każdego kontenera podrzędnego w kontenerze, który określisz. Nadal go, dopóki nie zostaną znalezione kontenerów podrzędnych.  

-   **Grupy**: Użyj grup, jeśli chcesz wyszukać jeden lub więcej określonych grup usługi Active Directory. Można skonfigurować **domeny usługi Active Directory** do używania domyślnej domeny i lasu lub ograniczyć wyszukiwanie do poszczególnych kontrolerów domeny. Ponadto można określić co najmniej jedną grupę do wyszukiwania. Jeśli nie określisz przynajmniej jedną grupę, wszystkie grupy znalezione w określonym **domeny usługi Active Directory** lokalizacji są przeszukiwane.  

> [!CAUTION]  
>  Podczas konfigurowania zakresu odnajdywania, wybierz tylko do grup, które muszą zostać odnalezione. To zalecenie wynika odnajdowanie grup usługi Active Directory próbuje odnaleźć wszystkich członków poszczególnych grup objętych zakresem odnajdywania. Odnajdywanie dużych grup może powodować zwiększone użycie przepustowości i zasobów usługi Active Directory.  

> [!NOTE]  
>  Zanim można tworzyć kolekcje, które są oparte na rozszerzonych atrybutów usługi Active Directory i aby dokładne wyniki odnajdywania komputerów i użytkowników, uruchom odnajdowanie systemu usługi Active Directory lub odnajdywania użytkownika usługi Active Directory, w zależności od tego, co chcesz Odnajdywanie.  

Akcje dotyczące odnajdywania grupy usługi Active Directory są rejestrowane w pliku **adsgdis.log** w  **&lt;Ścieżka_instalacji\>\LOGS** folderu na serwerze lokacji.  

Aby uzyskać więcej informacji o sposobie konfiguracji metody odnajdywania, zobacz [skonfiguruj metody odnajdywania](/sccm/core/servers/deploy/configure/configure-discovery-methods#BKMK_ConfigADDiscGeneral).  



##  <a name="bkmk_aboutSystem"></a> Odnajdowanie systemu usługi Active Directory  
**Można skonfigurować:** Tak  

**Domyślnie:** Nie  

**Konta** służy do uruchamiania tej metody:  

-   **Konto odnajdywania systemu usługi Active Directory** (zdefiniowane przez użytkownika)  

-   **Konto komputera** serwera lokacji  

> [!TIP]  
>  Oprócz informacji w tej sekcji, zobacz [wspólne funkcje grupy usługi Active Directory, systemu i odnajdowanie użytkowników](#bkmk_shared).  

Ta metoda umożliwia wyszukiwanie w określonych lokalizacjach usług domenowych w usłudze Active Directory zasobów komputera, które można tworzyć kolekcje i kwerendy. Można także zainstalować klienta programu Configuration Manager w odnalezionych urządzeń przy użyciu instalacji wypychanej klienta.  

Domyślnie ta metoda odnajduje podstawowe informacje o komputerze, włącznie z następującymi atrybutami:  

-   Nazwa komputera  

-   Wersja systemu operacyjnego i  

-   Nazwa kontenera usługi Active Directory  

-   Adres IP  

-   Lokacja usługi Active Directory  

-   Sygnatura czasowa ostatniego logowania  

Aby pomyślnie utworzyć DDR dla komputera, odnajdowanie systemu usługi Active Directory musi być mógł zidentyfikować konta komputera, a następnie rozpoznać nazwę komputera na adres IP.  

W **właściwości odnajdywania systemu usługi Active Directory** na okna dialogowego **atrybuty usługi Active Directory** kartę, można wyświetlić pełną listę domyślne atrybuty obiektów, które wykryje. Można również skonfigurować metodę odnajdywanie dodatkowych atrybutów (extended).  

Akcje dotyczące odnajdywania systemu usługi Active Directory są rejestrowane w pliku **adsysdis.log** w  **&lt;Ścieżka_instalacji\>\LOGS** folderu na serwerze lokacji.  

Aby uzyskać więcej informacji o sposobie konfiguracji metody odnajdywania, zobacz [skonfiguruj metody odnajdywania](/sccm/core/servers/deploy/configure/configure-discovery-methods#BKMK_ConfigADDiscGeneral).  



##  <a name="bkmk_aboutUser"></a> Odnajdowanie użytkowników usługi Active Directory  
**Można skonfigurować:** Tak  

**Domyślnie:** Nie  

**Konta** służy do uruchamiania tej metody:  

-   **Konto odnajdywania użytkownika usługi Active Directory** (zdefiniowane przez użytkownika)  

-   **Konto komputera** serwera lokacji  

> [!TIP]  
>  Oprócz informacji w tej sekcji, zobacz [wspólne funkcje grupy usługi Active Directory, systemu i odnajdowanie użytkowników](#bkmk_shared).  

Ta metoda umożliwia wyszukiwanie w usługach domenowych Active Directory w celu zidentyfikowania kont użytkowników i skojarzonych z nimi atrybutów. Domyślnie ta metoda odnajduje podstawowe informacje o koncie użytkownika, łącznie z następującymi atrybutami:  

-   Nazwa użytkownika  

-   Unikatowej nazwy użytkownika (w tym nazwa domeny)  

-   Domain  

-   Nazwy kontenerów usługi Active Directory  

W **właściwości odnajdywania użytkownika usługi Active Directory** na okna dialogowego **atrybuty usługi Active Directory** kartę, można wyświetlić domyślną pełną listę atrybutów obiektu, które wykryje. Można również skonfigurować metodę odnajdywanie dodatkowych atrybutów (extended).

Akcje dotyczące odnajdywania użytkownika usługi Active Directory są rejestrowane w pliku **adusrdis.log** w  **&lt;Ścieżka_instalacji\>\LOGS** folderu na serwerze lokacji.  

Aby uzyskać więcej informacji o sposobie konfiguracji metody odnajdywania, zobacz [skonfiguruj metody odnajdywania](/sccm/core/servers/deploy/configure/configure-discovery-methods#BKMK_ConfigADDiscGeneral).  



## <a name="azureaddisc"></a> Odnajdowanie użytkowników usługi Azure Active Directory
Umożliwia wyszukiwanie subskrypcję usługi Azure AD dla użytkowników z tożsamości chmury nowoczesnych odnajdowanie użytkowników usługi Azure Active Directory (Azure AD). Odnajdowanie użytkowników usługi Azure AD można znaleźć w następujących atrybutów:  
-   Identyfikator obiektu
-   Nazwa wyświetlana
-   Poczty
-   mailNickname
-   onPremisesSecurityIdentifier
-   userPrincipalName
-   Identyfikator AAD tenantID

Ta metoda obsługuje pełne i różnicowe synchronizacji atrybutów użytkownika z usługi Azure AD. Te informacje mogą być następnie używane odnajdywania wzdłuż po stronie danych, zbieranych z innych metod odnajdowania.

Akcje dotyczące odnajdywania użytkownika usługi Azure AD są rejestrowane w **SMS_AZUREAD_DISCOVERY_AGENT.log** pliku na serwerze lokacji najwyższego poziomu w hierarchii.

Aby skonfigurować odnajdowanie użytkowników usługi Azure AD, zobacz [Konfigurowanie usług Azure](/sccm/core/servers/deploy/configure/Azure-services-wizard) do zarządzania chmurą. Aby uzyskać informacje o sposobie konfiguracji metody odnajdywania, zobacz [odnajdywania Skonfiguruj użytkownika programu Azure AD](/sccm/core/servers/deploy/configure/configure-discovery-methods#azureaadisc).



##  <a name="bkmk_aboutHeartbeat"></a> Odnajdywanie pulsu  
**Można skonfigurować:** Tak  

**Domyślnie:** Tak  

**Konta** służy do uruchamiania tej metody:  

-   **Konto komputera** serwera lokacji  

Odnajdywanie pulsu różni się od innych metod odnajdywania programu Configuration Manager. Jest domyślnie włączona i działa na każdym komputerze klienckim (a nie na serwerze lokacji) do utworzenia rekordu DDR. Dla klientów urządzeń przenośnych ten rekord DDR jest tworzony przez punkt zarządzania, które używa klienta urządzenia przenośnego. Aby ułatwić obsługę rekordów bazy danych klientów programu Configuration Manager, nie należy wyłączać odnajdywania pulsu. Oprócz obsługi rekordów bazy danych, ta metoda może wymusić odnajdywanie komputera jako nowego rekordu zasobu. Można również ponownie wypełnić rekord bazy danych z komputera, który został usunięty z bazy danych.  

Odnajdywanie pulsu jest przeprowadzane zgodnie z harmonogramem skonfigurowanym na wszystkich klientach w hierarchii. Domyślny harmonogram odnajdywania pulsu jest równa co siedem dni. W przypadku zmiany interwału odnajdywania pulsu, upewnij się, że będzie ono przeprowadzane częściej niż zadanie obsługi lokacji **Usuń przestarzałe dane wykrywania**. To zadanie usuwa rekordów nieaktywnych klientów z bazy danych lokacji. Można skonfigurować **Usuń przestarzałe dane wykrywania** zadania tylko w lokacjach głównych. 

Można też ręcznie wywołania odnajdywania pulsu na określonym kliencie. Uruchom **cykl zbierania danych odnajdowania** na **akcji** kartę klienta programu Configuration Manager w Panelu sterowania.  

Podczas odnajdywania pulsu, tworzy rekordu DDR zawierający aktualne informacje klienta. Klient następnie kopiuje to mały plik (o rozmiarze 1 KB) do punktu zarządzania, aby można go przetworzyć lokacji głównej. Plik zawiera następujące informacje:  

-   Lokalizacja sieciowa  

-   Nazwa NetBIOS  

-   Wersja agenta klienta  

-   Szczegóły dotyczące stanu operacyjnego  

Odnajdywanie pulsu to jedyna metoda zapewniająca szczegóły dotyczące stanu instalacji klienta. Robi to przez aktualizuje atrybut klienta zasobu systemu, aby ustawić wartość równą **tak**.  

> [!NOTE]  
>  Nawet po wyłączeniu odnajdywania pulsu, liczba rekordów DDR nadal są tworzone i przesyłane do aktywnych klientów urządzeń przenośnych. Takie zachowanie gwarantuje, że zadanie **Usuń przestarzałe dane wykrywania** nie ma wpływu na aktywne urządzenia przenośne. Gdy **Usuń przestarzałe dane wykrywania** zadań usunięcie rekordu bazy danych dla urządzenia przenośnego, jego powoduje także odwołanie certyfikatu tego urządzenia. Ta akcja umożliwia blokowanie urządzenia przenośnego z łączenia się z punktami zarządzania.  

Akcje odnajdywania pulsu są rejestrowane w następujących lokalizacjach:  

-   Dla komputerów klienckich akcje w ramach odnajdywania pulsu są rejestrowane na kliencie w **InventoryAgent.log** w pliku *%Windir%\CCM\Logs* folderu.  

-   Dla klientów urządzeń przenośnych akcje w ramach odnajdywania pulsu są rejestrowane w **DMPRP.log** w pliku *% Program Files%\CCM\Logs* folderu punktu zarządzania używanego przez klienta urządzenia przenośnego.  

Aby uzyskać więcej informacji o sposobie konfiguracji metody odnajdywania, zobacz [skonfiguruj metody odnajdywania](/sccm/core/servers/deploy/configure/configure-discovery-methods#BKMK_ConfigHBDisc).  



##  <a name="bkmk_aboutNetwork"></a> Funkcja odnajdowania sieci  
**Można skonfigurować:** Tak  

**Domyślnie:** Nie  

**Konta** służy do uruchamiania tej metody:  

-   **Konto komputera** serwera lokacji  

Ta metoda umożliwia odnalezienie topologii sieci oraz w celu odnalezienia urządzeń, które mają adres IP w sieci. Odnajdywanie sieci przeszukuje sieci dla zasobów adres IP włączony badając następujących obiektów: 
- Serwery z implementacją DHCP firmy Microsoft
- Buforuje protokołu ARP (Address Resolution Protocol) w routery sieciowe
- Urządzenia z włączoną obsługą protokołu SNMP
- Domeny usługi Active Directory  

Przed użyciem odnajdywania sieci, należy określić *poziom* odnajdywania. Możesz również skonfigurować co najmniej jednego mechanizmu odnajdywania włączenia funkcji wykrywania sieci w zapytaniu dla urządzeń lub segmentów sieci. Można również skonfigurować ustawienia, które ułatwiają kontrolę akcji odnajdywania w sieci. Na koniec należy zdefiniować co najmniej jeden harmonogram uruchamiania odnajdywania sieci.  

Tę metodę w celu pomyślnego odnajdywania zasobów odnajdywania sieci musi rozpoznać adres IP i maski podsieci zasobu. Następujące metody są używane do identyfikacji maski podsieci obiektu:  

-   **Pamięć podręczna ARP routera:** Funkcja odnajdowania sieci odpytuje pamięć podręczną ARP routera, aby znaleźć informacje o podsieci. Zwykle dane w pamięci podręcznej ARP routera mają krótki czas wygaśnięcia. W związku z tym gdy funkcja odnajdowania sieci odpytuje pamięć podręczną ARP, pamięć podręczną ARP może już informacji na temat żądanego obiektu.  

-   **DHCP:** Funkcja odnajdowania sieci odpytuje każdy serwer DHCP, który określisz w celu odnalezienia urządzeń, dla których serwer DHCP udostępnił dzierżawę. Funkcja odnajdywania sieci obsługuje tylko serwery DHCP, które są uruchamiane przez firmę Microsoft implementacją protokołu DHCP.  

-   **Urządzenie SNMP:** Funkcja odnajdowania sieci może bezpośrednio odpytywać urządzenie SNMP. Aby funkcja odnajdowania sieci odpytała urządzenie urządzenie musi mieć zainstalowanego lokalnego agenta SNMP. Również skonfigurować odnajdywanie sieci do używania nazwy społeczności używanej przez agenta SNMP.  

Podczas odnajdywania identyfikuje obiekt adresem IP i może określić maski podsieci obiektu, tworzy rekordu DDR dla tego obiektu. Różne typy urządzeń łączyć się z siecią, dlatego odnajdywanie sieci umożliwia odnalezienie zasobów, które nie obsługują klienta programu Configuration Manager. Urządzenia, które mogą być wykryte, ale nie zarządza zawierają na przykład drukarki i routery.  

Funkcja odnajdowania sieci może zwrócić kilka atrybutów jako część rekordu odnajdywania, która tworzy. Te atrybuty obejmują:  

-   Nazwa NetBIOS  

-   Adresy IP  

-   Domeny zasobów  

-   Role systemu  

-   Nazwa wspólnoty SNMP  

-   Adresy MAC  

Działanie funkcji odnajdywania sieci jest rejestrowane w **Netdisc.log** w pliku  *&lt;Ścieżka_instalacji\>\Logs* na serwerze lokacji, na którym działa odnajdywanie.  

 Aby uzyskać więcej informacji o sposobie konfiguracji metody odnajdywania, zobacz [skonfiguruj metody odnajdywania](/sccm/core/servers/deploy/configure/configure-discovery-methods#BKMK_ConfigNetworkDisc).  

> [!NOTE]  
>  Złożone sieci i połączenia o niskiej przepustowości może spowodować odnajdywania sieci działać wolniej i powodować znaczne obciążenie sieci. Najlepszym rozwiązaniem należy uruchomić odnajdowanie sieci tylko wtedy, gdy pozostałe metody odnajdywania nie można znaleźć zasoby, które wymagają odnalezienia. Na przykład użyj funkcji odnajdywania sieci, jeśli muszą zostać odnalezione komputery grupy roboczej. Inne metody odnajdywania nie wykrywa komputerów grupy roboczej.  

###  <a name="BKMK_NetDiscLevels"></a> Poziomy odnajdywania sieci  
Podczas odnajdowania sieci można skonfigurować, należy określić jedną z trzech następujących zakresów:  

|Zakres odnajdywania|Szczegóły|  
|------------------------|-------------|  
|Topologia|Ten poziom umożliwia odnalezienie routerów i podsieci, ale nie określa maski podsieci obiektów.|  
|Topologia i klient|Oprócz topologii ten poziom odnajduje potencjalnych klientów, takich jak komputery i zasobów, takich jak drukarki i routery. Ten zakres odnajdywania próbuje określić maskę podsieci znalezionych obiektów.|  
|Topologia, klient i klient systemu operacyjnego|Oprócz topologii i potencjalnych klientów na tym poziomie próbuje wykryć nazwa komputera systemu operacyjnego i wersji. Ten poziom używa przeglądarki systemu Windows i wymaga obsługi sieci systemu Windows.|  

 Każdy kolejny zakres odnajdywania sieci jego działania i zwiększa wykorzystanie przepustowości sieci. Należy wziąć pod uwagę ruch sieciowy, który może zostać wygenerowany przed włączeniem wszystkich aspektów odnajdywania sieci.  

 Na przykład przy pierwszym użyciu odnajdywania sieci, może uruchomić tylko na poziomie topologii do określenia infrastruktury sieci. Następnie należy ponownie skonfigurować odnajdywanie sieci umożliwia odnalezienie obiektów i ich systemy operacyjne. Istnieje również możliwość skonfigurowania ustawień ograniczających odnajdywania sieci do określonego zakresu segmentów sieci. W ten sposób odnajdywania obiektów w lokalizacjach sieciowych wymagają i uniknąć niepotrzebnego obciążenia sieci. Ten proces umożliwia również odnajdywanie obiektów w routerach granicznych lub z spoza sieci.  

###  <a name="BKMK_NetDiscOptions"></a> Opcje odnajdywania sieci  
Aby włączyć odnajdywanie sieci wyszukiwać urządzenia z adresem IP, należy skonfigurować co najmniej jeden z tych opcji.  

> [!NOTE]  
>  Funkcja odnajdowania sieci działa w kontekście konta komputera serwera lokacji, na którym działa odnajdywanie. Jeśli konto komputera nie ma uprawnień do niezaufanej domenie, domena i konfiguracji serwera DHCP może zakończyć się niepowodzeniem do odnajdowania zasobów.  

#### <a name="dhcp"></a>DHCP  

Określ każdy serwer DHCP ma odnajdywania sieci do zapytania. (Funkcja odnajdywania sieci obsługuje tylko serwery DHCP, które są uruchamiane przez firmę Microsoft implementacją protokołu DHCP).  

-   Funkcja odnajdywania sieci pobiera informacje przy użyciu zdalnych wywołań procedury do bazy danych na serwerze DHCP.  

-   Odnajdowania sieci odpytuje zarówno 32-bitowe i 64-bitowych serwerów DHCP w celu listę urządzeń, które są zarejestrowane na każdym serwerze.  

-   Aby funkcja odnajdowania sieci pomyślnie odpytać serwer DHCP konto komputera serwera, na którym działa odnajdywanie musi być członkiem grupy Użytkownicy DHCP na serwerze DHCP. Na przykład ten poziom dostępu występuje, gdy spełniony jest jeden z następujących instrukcji:  

    -   Określony serwer DHCP jest serwer DHCP serwera, na którym działa odnajdywanie.  

    -   Komputer z uruchomioną odnajdywania i serwer DHCP znajdują się w tej samej domenie.  

    -   Między komputera, na którym działa odnajdywanie i serwerem DHCP istnieje zaufanie dwukierunkowe.  

    -   Serwer lokacji jest członkiem grupy Użytkownicy DHCP.  

-   Podczas wyliczania serwer DHCP, go nie zawsze odnajduje statyczne adresy IP. Funkcja odnajdywania sieci nie odnajdzie adresów IP, które są częścią wykluczonego zakresu adresów IP na serwerze DHCP. On także nie odnajduje adresy IP, które są zarezerwowane do ręcznego przypisania.  

#### <a name="domains"></a>Domeny  

Określ poszczególne domeny mają odnajdywania sieci do zapytania.  

-   Konto komputera serwera lokacji, na którym działa odnajdywanie musi mieć uprawnienia do odczytu kontrolerów domeny w każdej określonej domenie.  

-   Aby odnaleźć komputery z domeny lokalnej, należy włączyć usługę Przeglądarka komputera na co najmniej jednym komputerze. Ten komputer musi być w tej samej podsieci co serwer lokacji przeprowadzający odnajdywanie sieci.  

-   Odnajdywanie sieci umożliwia odnalezienie dowolny komputer, który można wyświetlić z poziomu serwera lokacji podczas przeglądania sieci.  

-   Funkcja odnajdywania sieci pobiera adres IP. Następnie używa żądanie echa protokołu komunikatu sterowania Internetem (ICMP) na polecenie ping każdego znalezionego urządzenia. **Ping** polecenia można ustalić, które komputery są obecnie aktywne.  

#### <a name="snmp-devices"></a>Urządzenia SNMP  

Określ poszczególne urządzenia SNMP, które mają odnajdywania sieci do zapytania.  

-   Funkcja odnajdywania sieci pobiera wartość ipNetToMediaTable z urządzenia SNMP, które odpowiada na kwerendę. Ta wartość zwraca tablice adresów IP, które są komputery klienckie lub innych zasobów, takich jak drukarki, routery albo inne urządzenia z adresem IP.  

-   Aby wysłać do urządzenia kwerendę, należy określić adres IP lub nazwę NetBIOS tego urządzenia.  

-   Konfigurowanie odnajdywania sieci do używania nazwy społeczności urządzenia, lub urządzenie odrzuci kwerendę opartą na protokole SNMP.  


###  <a name="BKMK_LimitNetDisc"></a> Ograniczanie odnajdywania sieci  
Gdy funkcja odnajdowania sieci odpytuje urządzenia SNMP na granicy sieci, może zidentyfikować informacje o podsieci i urządzeń SNMP spoza bezpośredniej sieci. Użyj następujące informacje, aby ograniczyć odnajdywanie sieci, konfigurując urządzenia SNMP wykrywania mogą się komunikować oraz określając segmenty sieci, do zapytania.  

#### <a name="subnets"></a>Podsieci  

Skonfiguruj podsieci tego zapytania odnajdywania sieci, podczas używania opcji SNMP i DHCP. Te dwie opcje wyszukiwania tylko włączone podsieci.  

Na przykład żądania DHCP mogą być zwrócone urządzenia z lokalizacji w całej sieci. Jeśli chcesz odnaleźć tylko urządzenia w określonej podsieci, wybierz i Włącz odpowiednią podsieć na **podsieci** karcie **odnajdowanie sieci: właściwości** okno dialogowe. Po określeniu i włączeniu podsieci ograniczenie przyszłych zadania odnajdywania DHCP oraz SNMP do tych podsieci.  

> [!NOTE]  
>  Konfiguracje podsieci nie ograniczają zakresu obiektów które **domen** opcji odnajdywania.  

#### <a name="snmp-community-names"></a>Nazwy wspólnot SNMP  

Aby włączyć odnajdywanie sieci pomyślnie wykonać zapytania urządzenia SNMP, odnajdowania sieci można skonfigurować przy użyciu nazwy społeczności urządzenia. Jeśli funkcja odnajdowania sieci nie jest skonfigurowany przy użyciu nazwy społeczności urządzenia SNMP, urządzenie odrzuci kwerendę.  

#### <a name="maximum-hops"></a>Maksymalna liczba przeskoków  

Po skonfigurowaniu maksymalną liczbę przeskoków między routerami, można ograniczyć liczbę segmentów sieci i routerów, jaką funkcja odnajdowania sieci można badać przy użyciu protokołu SNMP.  

Liczba przeskoków ogranicza liczbę dodatkowych urządzeń i segmentów sieci, które funkcja odnajdowania sieci może wysyłać zapytania.  

Przykładowo odnajdowanie tylko topologii z **0** (zero) przeskoków między routerami odnajduje podsieć, w którym znajduje się serwer źródłowy. Zawiera wszystkie routery w tej podsieci.  

Na poniższym diagramie przedstawiono określony tylko topologii sieci zapytania znalezione przez funkcję odnajdowania po uruchomieniu na serwerze 1 z 0 przeskoków między routerami: podsieć D i Router 1.  

 ![Obraz odnajdywania o zerowej przeskoku routera](media/Disc-0.gif)  

 Na poniższym diagramie przedstawiono jakie topologia i klient znalezione przez funkcję odnajdowania sieci zapytania po uruchomieniu na serwerze 1 z 0 przeskoków między routerami określony: podsieć D i Router 1 oraz wszyscy potencjalni klienci w podsieci D.  

 ![Obraz odnajdowania z jednym routerem szybkiego dostępu](media/Disc-1.gif)  

 Aby uzyskać zorientować się router jak dodatkowe przeskoki może zwiększyć ilość odnalezionych zasobów sieciowych, należy wziąć pod uwagę następujące sieci:  

 ![Obraz odnajdowania z dwóch przeskoki routera](media/Disc-2.gif)  

 Uruchamiania funkcji odnajdowania sieci tylko topologii na serwerze 1 z jednym przeskokiem między routerami spowoduje umożliwia odnalezienie następujących obiektów:  

-   Router 1 i podsieć 10.1.10.0 (znalezione przy zerowej przeskoków)  

-   Podsieci 10.1.20.0 i 10.1.30.0, podsieć A i Router 2 (znalezione po pierwszym przeskoku)  

> [!WARNING]  
>  Każde zwiększenie liczby przeskoków między routerami może znacznie zwiększyć liczbę odnalezionych zasobów i zwiększyć odnajdowania sieci korzysta z przepustowości sieci.  



##  <a name="bkmk_aboutServer"></a> Odnajdowanie serwera  
**Można skonfigurować:** Nie  

Oprócz metod odnajdywania użytkownika można skonfigurować program Configuration Manager używa procesu o nazwie **odnajdowania serwerów** (SMS_WINNT_SERVER_DISCOVERY_AGENT). Ta metoda odnajdywania tworzy rekordy zasobów dla komputerów, które systemy lokacji, takich jak komputer, który jest skonfigurowany jako punkt zarządzania.  



##  <a name="bkmk_shared"></a> Wspólne funkcje odnajdywania grupy usługi Active Directory, odnajdowanie systemu i odnajdowanie użytkowników usługi  
Ta sekcja zawiera informacje o funkcjach, które są wspólne dla następujących metod odnajdywania:  

-   Odnajdywanie grupy usługi Active Directory  

-   Odnajdywanie systemu usługi Active Directory  

-   odnajdywanie użytkownika usługi Active Directory  

> [!NOTE]  
>  Informacje przedstawione w tej sekcji nie dotyczą odnajdywania lasu usługi Active Directory.  

Tych trzech metod odnajdywania są podobne w konfiguracji i obsłudze. Mogą one odnajdywanie komputerów, użytkowników i informacji o członkostwie w grupie zasobów, które są przechowywane w usługach domenowych w usłudze Active Directory. Proces odnajdywania zarządza agent odnajdywania. Agent działa na serwerze lokacji w każdej lokacji, w której skonfigurowano odnajdywanie do uruchomienia. Istnieje możliwość skonfigurowania każdego z tych metod odnajdywania do wyszukania co najmniej jedna lokalizacja usługi Active Directory jako wystąpienia lokalizacji w lasach lokalnych lub zdalnych lasach.  

Gdy odnajdywanie obejmuje zasoby w niezaufanym lesie, agent odnajdywania musi mieć możliwość rozpoznania następujących powiódł się:  

-   Aby odnaleźć zasób komputera przy użyciu odnajdywania systemu usługi Active Directory, agent odnajdywania musi być w stanie rozpoznać nazwę FQDN zasobu. Jeśli nie można rozpoznać nazwę FQDN, próbuje rozpoznania zasobu wg jego nazwy NetBIOS.  

-   Aby odnaleźć użytkownika lub grupy zasobów za pomocą odnajdywania użytkownika usługi Active Directory lub odnajdywania grupy usługi Active Directory, agent odnajdywania musi być w stanie rozpoznać nazwę FQDN, nazwy kontrolera domeny, określony dla lokalizacji usługi Active Directory.  

Dla każdej lokalizacji można skonfigurować indywidualne opcje wyszukiwania, takie jak włączenie cyklicznego wyszukiwania kontenerów podrzędnych usługi Active Directory lokalizacji. Można także skonfigurować unikatowe konto używane podczas wyszukiwania tej lokalizacji. To konto zapewnia elastyczność podczas konfigurowania metody odnajdywania w jednej lokacji umożliwia wyszukiwanie w wielu lokalizacjach usługi Active Directory w wielu lasach. Nie trzeba konfigurować pojedyncze konto, które ma uprawnienia do wszystkich lokalizacji.  

Po uruchomieniu każdego z tych trzech metod odnajdywania w określonej lokacji, serwerze lokacji programu Configuration Manager w danej lokacji kontaktuje się z najbliższym kontrolerem domeny w określonym lesie usługi Active Directory do lokalizowania zasobów usługi Active Directory. Domena i las mogą mieć ustawiony dowolny obsługiwany tryb usługi Active Directory. Konto przypisane do każdego wystąpienia lokalizacji musi mieć **odczytu** uprawnienia w określonych lokalizacjach usługi Active Directory dostępu.

Odnajdywania wyszukuje określone lokalizacje obiektów, a następnie próbuje zebrać informacje o tych obiektach. DDR jest tworzony podczas wystarczającej ilości informacji o zasobie, które mogą zostać zidentyfikowane. Wymagane informacje zależą od używanej metody odnajdywania.  

Jeśli konfigurujesz tej samej metody odnajdywania uruchamianych w różnych lokacjach programu Configuration Manager przeprowadzać kwerendy lokalnych serwerów usługi Active Directory, każdej lokacji można skonfigurować unikatowy zestaw opcji odnajdywania. Ponieważ dane odnajdywania są udostępniane każdej lokacji w hierarchii, należy unikać nakładania się tych konfiguracji w celu wydajnego odnajdywania zasobów jeden raz.

W mniejszych środowiskach należy wziąć pod uwagę uruchomienia każdej metody odnajdywania w tylko jednej lokacji w hierarchii. Ta konfiguracja ogranicza koszty administracyjne i potencjalnych wielu akcji odnajdywania ponowne odnajdywanie tych samych zasobów. Gdy zminimalizować liczbę witryn, aby uruchomić odnajdywanie, można zmniejszyć ogólną przepustowość sieci wykrywania używa. Można także zmniejszyć ogólną liczba rekordów DDR, które są tworzone i muszą zostać przetworzone przez serwery lokacji.  

Wiele konfiguracji metod odnajdywania wyjaśnień. Użyj poniższych sekcji, aby uzyskać więcej informacji na temat opcji odnajdywania, które mogą wymagać dodatkowe informacje, aby je skonfigurować.  

Poniższe opcje są dostępne do użycia z wielu metod odnajdywania usługi Active Directory:  

-   [Odnajdowanie różnicowe](#bkmk_delta)  

-   [Filtrowanie starych rekordów komputera na podstawie logowania do domeny](#bkmk_stalelogon)  

-   [Filtrowanie starych rekordów na podstawie hasła komputera](#bkmk_stalepassword)  

-   [Wyszukiwanie niestandardowych atrybutów usługi Active Directory](#bkmk_customAD)  


###  <a name="bkmk_delta"></a> Odnajdowanie różnicowe  
Dostępne dla:  

-   Odnajdywanie grupy usługi Active Directory  

-   Odnajdywanie systemu usługi Active Directory  

-   odnajdywanie użytkownika usługi Active Directory  

Odnajdywanie zmian nie jest to metoda odnajdywania niezależne, lecz opcją dostępną metod odnajdywania dotyczy. Odnajdywanie zmian wyszukuje określone atrybuty usługi Active Directory do zmiany wprowadzone od czasu ostatniego pełnego cyklu odnajdywania metody odnajdywania zastosowania. Zmiany atrybutów są przesyłane do bazy danych programu Configuration Manager w celu zaktualizowania rekordu odnajdywania zasobów.  

Domyślnie odnajdywanie zmian odbywa się w cyklu 5 minut. Ten harmonogram jest znacznie częściej niż typowe harmonogram pełny cykl odnajdywania. Ten cykl częste jest możliwa, ponieważ odnajdywanie zmian wykorzystuje mniej serwera lokacji i zasobów sieciowych niż pełny cykl odnajdywania jest. Podczas stosowania metody odnajdywania zmian można zmniejszyć częstotliwość pełnego cyklu odnajdywania w ramach tej metody.  

Odnajdywanie zmian umożliwia wykrywanie najczęstszych zmian są następujące:  

-   Nowe komputery lub użytkownicy dodani do usługi Active Directory  

-   Zmiany do podstawowych informacji, komputera i użytkownika  

-   Nowe komputery lub użytkownicy dodani do grupy  

-   Komputery lub użytkownicy usunięci z grupy  

-   Zmiany w obiektach grupy systemu  

Chociaż odnajdywanie zmian umożliwia wykrywanie nowych zasobów oraz zmian w członkostwie grupy, nie może wykryć, gdy zasób został usunięty z usługi Active Directory. Rekordy DDR utworzone przez odnajdywania zmian są przetwarzane w podobny sposób rekordów DDR, które są tworzone przez pełny cykl odnajdywania.  

Odnajdywanie zmian konfiguruje się na **harmonogram sondowania** we właściwościach poszczególnych metod odnajdywania.  


###  <a name="bkmk_stalelogon"></a> Filtrowanie starych rekordów komputera na podstawie logowania do domeny  
Dostępne dla:  

-   Odnajdywanie grupy usługi Active Directory  

-   Odnajdywanie systemu usługi Active Directory  

Można skonfigurować odnajdywanie w celu wykluczenia komputerów z rekordem starych. To wykluczenie zależy od ostatniego logowania domeny tego komputera. Gdy ta opcja jest włączona, odnajdowanie systemu usługi Active Directory ocenia każdy komputer, który identyfikuje. Odnajdywanie grupy usługi Active Directory ocenia każdy komputer, który jest członkiem grupy, który został odnaleziony.  

Aby użyć tej opcji:  

-   Komputery muszą być skonfigurowane tak, aby zaktualizować **lastLogonTimeStamp** atrybutów w usługach domenowych w usłudze Active Directory.  

-   Poziom funkcjonalności domeny usługi Active Directory przeznaczona do systemu Windows Server 2003 lub nowszego.  

Podczas konfigurowania czasu od ostatniego logowania, który ma zostać użyty dla tego ustawienia należy wziąć pod uwagę interwał replikacji między kontrolerami domeny.  

Aby skonfigurować filtrowanie **opcji** karcie **właściwości odnajdywania systemu usługi Active Directory** i **właściwości odnajdywania grupy usługi Active Directory** okien dialogowych. Wybierz **odnajdź tylko komputery zalogowane w domenie w danym okresie czasu**.  

> [!WARNING]  
>  Po skonfigurowaniu filtru i **filtrowanie starych rekordów na podstawie hasła komputera**, odnajdywanie nie obejmuje komputerów, które spełniają kryteria albo filtr.  


###  <a name="bkmk_stalepassword"></a> Filtrowanie starych rekordów na podstawie hasła komputera  
Dostępne dla:  

-   Odnajdywanie grupy usługi Active Directory  

-   Odnajdywanie systemu usługi Active Directory  

Można skonfigurować odnajdywanie w celu wykluczenia komputerów z rekordem starych. To wykluczenie opiera się na ostatniej aktualizacji hasła konta komputera przez komputer. Gdy ta opcja jest włączona, odnajdowanie systemu usługi Active Directory ocenia każdy komputer, który identyfikuje. Odnajdywanie grupy usługi Active Directory ocenia każdy komputer, który jest członkiem grupy, który został odnaleziony.  

Aby użyć tej opcji:  

-   Komputery muszą być skonfigurowane tak, aby zaktualizować **pwdLastSet** atrybutów w usługach domenowych w usłudze Active Directory.  

Podczas konfiguracji tej opcji, należy uwzględnić również interwał aktualizacji tego atrybutu. Należy również rozważyć interwał replikacji między kontrolerami domeny.  

Aby skonfigurować filtrowanie **opcji** karcie **właściwości odnajdywania systemu usługi Active Directory** i **właściwości odnajdywania grupy usługi Active Directory** okien dialogowych. Wybierz **odnajdź tylko komputery, które zaktualizowały swoje hasło konta komputera w danym okresie czasu**.  

> [!WARNING]  
>  Po skonfigurowaniu filtru i **filtrowanie starych rekordów na podstawie logowania do domeny**, odnajdywanie nie obejmuje komputerów, które spełniają kryteria albo filtr.  


###  <a name="bkmk_customAD"></a> Wyszukiwanie niestandardowych atrybutów usługi Active Directory  
 Dostępne dla:  

-   Odnajdywanie systemu usługi Active Directory  

-   odnajdywanie użytkownika usługi Active Directory  

Każda metoda odnajdywania obsługuje zawiera unikatową listę atrybutów usługi Active Directory, które mogą być wykrywane.  

Można wyświetlić i skonfigurować listę atrybutów niestandardowych na **atrybuty usługi Active Directory** karcie **właściwości odnajdywania systemu usługi Active Directory** i **właściwości odnajdywania użytkownika usługi Active Directory** okien dialogowych.  
