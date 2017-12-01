---
title: Wybieranie metod odnajdywania
titleSuffix: Configuration Manager
description: "Zapoznaj się z uwagami dla metod do zastosowania i lokacje, w których je uruchomić."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 127ce713-d085-430f-ac7b-2701637fe126
caps.latest.revision: "9"
author: mstewart
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: b932c4670521af366c5cb40adf5b1076263a9c8e
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2017
---
# <a name="select-discovery-methods-to-use-for-system-center-configuration-manager"></a>Wybieranie metod odnajdywania do zastosowania dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Pomyślnie i wydajne korzystanie z odnajdywania dla programu System Center Configuration Manager, należy wziąć pod uwagę metod do zastosowania i lokacje, w których je uruchomić.  

 Ponieważ odnajdywanie może generować dużą ilość ruchu sieciowego i rekordy dane wynikowe odnajdywania (DDR) można użyć znaczące ilości zasobów procesora CPU podczas przetwarzania, należy używać tylko metod odnajdywania wymaganych do zrealizowania określonych celów. Może uruchomić przy użyciu tylko jednego lub dwóch metod odnajdywania, a następnie włączyć dodatkowe metody w kontrolowany sposób, aby rozszerzyć zakres odnajdywania w środowisku. Informacje przedstawione w tym temacie ułatwiają podejmowanie świadomych decyzji.  

 Aby uzyskać informacje na temat różnych metod odnajdywania, zobacz [o metodach odnajdywania dla programu System Center Configuration Manager](../../../../core/servers/deploy/configure/about-discovery-methods.md).  

## <a name="select-methods-to-discover-different-things"></a>Wybierz metody do wykrywanie różnych rzeczy  
 Aby odnaleźć potencjalne komputery klienckie programu Configuration Manager lub zasoby użytkowników, należy włączyć odpowiednie metody odnajdywania. Można użyć różnych kombinacji metod odnajdywania, pozwalające zlokalizować różne zasoby i odnaleźć dodatkowe informacje o tych zasobach. Metod odnajdywania, których używasz określają rodzaj zasobów, które zostały odnalezione, oraz usług programu Configuration Manager i agenci są używane w procesie odnajdowania. Określają również typ informacji o zasobach, które można odnajdywać.  

### <a name="discover-computers"></a>Wykryj komputery   
Jeśli chcesz odnajdywać komputery, możesz użyć **odnajdywania systemu usługi Active Directory** lub **odnajdywania sieci**.  

 Na przykład jeśli chcesz odnajdywać zasoby, które mogą zainstalować klienta programu Configuration Manager przed użyciem instalacji wypychanej klienta, możesz uruchomić odnajdowanie systemu usługi Active Directory. Za pomocą tej metody, można nie tylko odnajdywanie zasobów, ale również odnaleźć podstawowe informacje nawet rozszerzone informacje o nim w usługach domenowych w usłudze Active Directory. Informacje te mogą być przydatne do tworzenia złożonych kwerend i kolekcji używanych w celu przypisania ustawień klienta lub wdrożenia zawartości.

Alternatywnie można uruchomić odnajdowanie sieci i użycia jej opcji do odnalezienia systemu operacyjnego zasobów (wymagane do późniejszego użycia instalacji wypychanej klienta). Odnajdywanie sieci zapewnia informacje o topologii sieci, które nie są można uzyskać za pomocą innych metod odnajdowania. Ta metoda, jednak daje użytkownikowi żadnych informacji o środowisku usługi Active Directory.

 Istnieje również metody o nazwie **odnajdywania pulsu**. Istnieje możliwość użycia tylko funkcji odnajdywania pulsu, aby wymusić odnajdywanie klientów zainstalowanych przy użyciu metod niż wypychana instalacja klienta. Jednak w przeciwieństwie do innych metod, odnajdywanie pulsu nie umożliwia odnajdywania komputerów bez aktywnego klienta programu Configuration Manager. Zwraca ograniczony zestaw informacji przeznaczonych do obsługi istniejącego rekordu bazy danych, a nie stanowić podstawy tego rekordu. Informacje przesyłane w ramach odnajdywania pulsu mogą nie być wystarczające do tworzenia złożonych kwerend lub kolekcji.  

 Jeśli używasz **odnajdowanie grup usługi Active Directory** do odnajdywania członkostwa w określonej grupie, można odnaleźć ograniczone informacje system lub komputer. Nie zastępuje pełnego odnajdywania komputerów, ale może zapewnić podstawowe informacje. Te informacje są niewystarczające dla instalacji wypychanej klienta.  

### <a name="discover-users"></a>Odnajdywanie użytkowników   
Aby dowiedzieć się, informacje o użytkownikach, należy użyć **odnajdywania użytkownika usługi Active Directory**. Podobnie jak odnajdywanie systemu usługi Active Directory, ta metoda umożliwia odnajdywanie użytkowników usługi Active Directory. Zawiera podstawowe informacje oprócz rozszerzonych informacji usługi Active Directory. Te informacje można użyć do tworzenia złożonych kwerend i kolekcji podobnych do tych komputerów.  

### <a name="discover-group-information"></a>Odnajdywanie informacji o grupie   
Odnajdywanie informacji o grupach lub członkostwie grupy, należy użyć **odnajdowanie grup usługi Active Directory**. Ta metoda odnajdywania tworzy rekordy zasobów grup zabezpieczeń.  

 Ta metoda służy do wyszukiwania określonych grupy usługi Active Directory, aby zidentyfikować członków tej grupy, oprócz wszystkich zagnieżdżonych grup w tej grupie. Ponadto ta metoda umożliwia wyszukiwanie grup w lokalizacji usługi Active Directory oraz cykliczne wyszukiwanie każdego kontenera podrzędnego tej lokalizacji w usługach Active Directory Domain Services.  

 Ta metoda odnajdywania można także przeszukać członkostwo grup dystrybucyjnych. Pozwala to ustalić relacje grupy użytkowników i komputerów.  

 Po odnalezieniu grupy można również odnaleźć ograniczone informacje o jego elementów członkowskich. To rozwiązanie nie eliminuje usługi Active Directory system lub użytkownik metod odnajdywania, mimo że. Jest to zazwyczaj nie wystarcza do tworzenia złożonych kwerend i kolekcji lub służyć jako podstawa instalacji wypychanej klienta.  

### <a name="discover-infrastructure"></a>Odnajdywanie infrastruktury   
Istnieją dwie metody można użyć do odnajdywania infrastruktury sieci **odnajdywania lasu usługi Active Directory** i **odnajdywania sieci**.  

 Odnajdowanie lasu usługi Active Directory umożliwia wyszukiwanie w lesie usługi Active Directory, informacje o podsieci i konfiguracje lokacji usługi Active Directory. Te konfiguracje można następnie automatycznie wprowadzić do programu Configuration Manager jako lokalizacje granic.  

 Jeśli chcesz odnaleźć topologię sieci, użyj funkcji odnajdywania sieci. Podczas gdy inne metody odnajdywania zwracają informacje związane z usług domenowych w usłudze Active Directory i można zidentyfikować także bieżącą lokalizację sieciową klienta, nie zapewniają informacji o infrastrukturze na podstawie podsieci i routerów topologii sieci.  

##  <a name="bkmk_shared"></a>Dane odnajdywania są udostępniane między lokacjami  
 Po programu Configuration Manager doda danych odnajdywania do bazy danych, są one szybko udostępniane między wszystkimi lokacjami w hierarchii. Ponieważ nie istnieje zwykle żadnych korzyści odnajdywanie tych samych informacji w wielu lokacjach w hierarchii, warto rozważyć skonfigurowanie jednego wystąpienia każdej metody odnajdywania, którego używasz do uruchamiania w jednej lokacji. Należy dobrze w tym celu zamiast uruchamiać kilka wystąpień jednej metody w różnych lokacjach.  

 Jednak w niektórych środowiskach takie mogą być przydatne do tej samej metody odnajdywania do uruchamiania w wielu lokacjach, każda z osobną konfiguracją i harmonogramem przypisywania. Na przykład przy użyciu odnajdywania sieci, można kierować każdej lokacji w celu odnajdywania swoich sieciach lokalnych, a podjęciem próby odnajdywania wszystkich lokalizacje sieciowe w sieci WAN.

Jeśli konfigurujesz wiele wystąpień tej samej metody odnajdywania uruchamianych w różnych lokacjach, należy starannie zaplanować konfigurację każdej lokacji. Aby uniknąć dwa lub więcej witryn odnajdywanie tych samych zasobów z usługi Active Directory lub sieci. To może wykorzystywać dodatkowej przepustowości sieci i utworzenie zduplikowanych rekordów DDR.

Poniższa tabela zawiera lokacje, w których można skonfigurować różne metody odnajdywania.  

|Metoda odnajdywania|Obsługiwane lokalizacje|  
|----------------------|-------------------------|  
|Odnajdywanie lasu usługi Active Directory|Centralna lokacja administracyjna<br /><br /> Lokacja główna|  
|Odnajdywanie grupy usługi Active Directory|Lokacja główna|  
|Odnajdywanie systemu usługi Active Directory|Lokacja główna|  
|odnajdywanie użytkownika usługi Active Directory|Lokacja główna|  
|Odnajdywanie pulsu<sup>1</sup>|Lokacja główna|  
|Odnajdywanie sieci|Lokacja główna<br /><br /> Lokacja dodatkowa|  

 <sup>1</sup> Lokacje dodatkowe nie może skonfigurować funkcji odnajdywania pulsu, ale mogą odbierać rekord DDR interwału czasowego od klienta.  

 Gdy lokacje dodatkowe uruchomić odnajdowanie sieci lub odebrać rekordy DDR odnajdywania pulsu, przesyłają rekord DDR za pomocą replikacji opartej na plikach do ich nadrzędnej lokacji głównej. Jest to spowodowane Lokacje tylko główne i centralne Lokacje administracyjne mogą przetwarzać DDR. Aby uzyskać więcej informacji o sposobie przetwarzania rekordów DDR, zobacz [informacje o rekordach danych odnajdywania](../../../../core/servers/deploy/configure/run-discovery.md#BKMK_DDRs).  

## <a name="considerations-for-different-discovery-methods"></a>Zagadnienia dotyczące różnych metod odnajdywania  
 Różni każdej lokacji serwera i środowisko sieciowe jest dobrym pomysłem jest Ogranicz konfiguracje początkowego odnajdywania. Następnie dokładnie Monitoruj każdy serwer lokacji dla możliwości przetwarzania generowanych danych odnajdywania.  

Jeśli używasz **usługi Active Directory** metodę odnajdywania dla systemów, użytkowników lub grup:  

-   Uruchom odnajdywanie w lokacji, która ma szybkie połączenie sieciowe z kontrolerami domeny.  

-   Należy rozważyć topologię replikacji usługi Active Directory, aby upewnić się, że odnajdywania mogą uzyskiwać dostęp do najnowszych informacji.  

-   Uwzględnij zakres konfiguracji odnajdywania i Ogranicz odnajdywanie tylko lokalizacji usługi Active Directory i grupy, które wymagają odnalezienia.  

Jeśli używasz **odnajdywania sieci**:  

-   Użyj ograniczonej konfiguracji początkowej, aby zidentyfikować topografię sieci.  

-   Po zidentyfikowaniu topografii sieci, należy skonfigurować odnajdywanie sieci z usługami w określonych lokacjach centralnych względem obszarów sieci, które mają być dokładniejszego odnajdywania.  

Ponieważ **odnajdywania pulsu** nie działa w określonej lokacji, nie trzeba uważają, że w ogólnym planowaniu uruchamiania odnajdywania.  

##  <a name="bkmk_best"></a>Najlepsze rozwiązania dotyczące odnajdywania  
Aby uzyskać najlepsze wyniki z odnajdywaniem zaleca się następujące:

 - **Uruchom odnajdowanie systemu usługi Active Directory i odnajdowanie użytkowników usługi Active Directory przed uruchomieniem odnajdowanie grup usługi Active Directory.**  

 Gdy odnajdowanie grup usługi Active Directory zidentyfikuje nieodnalezionego wcześniej użytkownika lub komputera jako członek grupy, próbuje odnaleźć podstawowe szczegóły dotyczące użytkownika lub komputera. Ponieważ odnajdowanie grup usługi Active Directory nie jest zoptymalizowana dla tego typu odnajdywania, ten proces może spowodować jej działanie. Ponadto odnajdowanie grup usługi Active Directory identyfikuje tylko podstawowe szczegóły dotyczące użytkowników i komputerów, które umożliwia odnalezienie i nie tworzy pełną użytkownika lub komputera rekordu odnajdywania. Po uruchomieniu odnajdywania systemu usługi Active Directory i odnajdowanie użytkowników usługi Active Directory, dostępne są dodatkowe atrybuty usługi Active Directory dla każdego typu obiektu. W związku z tym odnajdowanie grup usługi Active Directory działa bardziej efektywnie.  

- **Podczas konfigurowania odnajdywania grupy usługi Active Directory Określ tylko grupy używane z programem Configuration Manager.**  

 Aby kontrolować używanie zasobów przez odnajdowanie grup usługi Active Directory, określić tylko te grupy, korzystających z programu Configuration Manager. Jest to spowodowane odnajdowanie grup usługi Active Directory rekursywnie wyszukuje każdej odnalezionej dla użytkowników, komputerów i grup zagnieżdżonych grupie. Przeszukiwanie każdej zagnieżdżonej grupy może rozszerzyć zakres działania funkcji odnajdowanie grup usługi Active Directory i zmniejszyć wydajność. Ponadto po skonfigurowaniu odnajdowania różnicowego dla odnajdywania grupy usługi Active Directory Metoda odnajdywania monitoruje zmiany w każdej grupie. To dodatkowe zmniejszenie wydajności, gdy metoda musi przeszukać niepotrzebne grupy.  

- **Skonfiguruj metody odnajdywania z dłuższym interwałem pomiędzy pełnym odnajdywaniem i krótszym okresem odnajdywania różnicowego.**  

 Ponieważ odnajdywanie różnicowe zużywa mniej zasobów niż pełny cykl odnajdywania i można zidentyfikować nowych lub zmodyfikowanych zasobów w usłudze Active Directory, można zmniejszyć częstotliwość cykli pełnego odnajdywania do uruchamiania co tydzień (lub mniej). Odnajdywanie różnicowe dla funkcji odnajdywania systemu usługi Active Directory, odnajdowanie użytkowników usługi Active Directory i odnajdowanie grup usługi Active Directory identyfikuje niemal wszystkie zmiany obiektów usługi Active Directory i może zachować dokładne dane odnajdywania dla zasobów.  

- **Uruchom metody odnajdywania usługi Active Directory w lokacji głównej zawierającej lokalizację sieciową najbliższą kontrolerowi domeny usługi Active Directory.**  

 Aby poprawić wydajność odnajdowania usługi Active Directory, jego dobrym rozwiązaniem jest uruchamianie odnajdywania w lokacji głównej, która ma szybkie połączenie sieciowe z kontrolerami domeny. Po uruchomieniu tej samej metody odnajdywania usługi Active Directory w wielu lokacjach, należy skonfigurować każdej metody odnajdywania w celu uniknięcia nakładania się. W przeciwieństwie do poprzednich wersji programu Configuration Manager danych odnajdywania jest współużytkowane przez lokacje. W związku z tym nie jest konieczne odnajdywanie tych samych informacji w wielu lokacjach. Aby uzyskać więcej informacji, zobacz [danych odnajdywania jest udostępniana między lokacjami](../../../../core/servers/deploy/configure/select-discovery-methods-to-use.md#bkmk_shared).  

- **Uruchom odnajdowanie lasu usługi Active Directory tylko w jednej lokacji, jeżeli planowane jest automatyczne tworzenie granic na podstawie danych odnajdywania.**  

 Po uruchomieniu odnajdywania lasu usługi Active Directory w więcej niż jednej lokacji w hierarchii jest dobrym pomysłem jest włączenie tylko opcji automatycznego tworzenia granic w jednej lokacji. Jest to spowodowane podczas odnajdywania lasu usługi Active Directory działa w każdej lokacji i tworzy granice, programu Configuration Manager nie może scalić tych granic w jeden obiekt granic. Podczas konfigurowania odnajdywania lasu usługi Active Directory do automatycznego tworzenia granic w kilku lokacjach może to spowodować powstanie zduplikowanych obiektów granic w konsoli programu Configuration Manager.  
