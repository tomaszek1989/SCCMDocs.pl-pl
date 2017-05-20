---
title: Wybieranie metod odnajdywania programu Configuration Manager | Dokumentacja firmy Microsoft
description: "Przejrzyj zagadnienia dla metod do używania i lokacje, w których je uruchomić."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 127ce713-d085-430f-ac7b-2701637fe126
caps.latest.revision: 9
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f72317cefab5ce8cad13b3120c3c93c856fa40b7
ms.openlocfilehash: 4b6be888be2ad6c1f5e7c0be33d9830bb870114e
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="select-discovery-methods-to-use-for-system-center-configuration-manager"></a>Wybieranie metod odnajdywania do zastosowania dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Pomyślnie i efektywne korzystanie z odnajdywania dla programu System Center Configuration Manager, należy wziąć pod uwagę metod do używania i lokacje, w których je uruchomić.  

 Odnajdywanie może generować duże natężenie ruchu sieciowego i rekordów danych odnajdowania wynikowe (DDR) można użyć znaczących zasobów procesora CPU podczas przetwarzania, używanie tylko metod odnajdywania wymaganych do zrealizowania określonych celów. Może uruchomić za pomocą tylko jednego lub dwóch metod odnajdywania, a następnie później włączyć dodatkowe metody w kontrolowany sposób, aby rozszerzyć zakres odnajdywania w środowisku. Informacje przedstawione w tym temacie ułatwiają podejmowanie świadomych decyzji.  

 Informacje o metodach odnajdywania różnych, zobacz [o metodach odnajdywania dla programu System Center Configuration Manager](../../../../core/servers/deploy/configure/about-discovery-methods.md).  

## <a name="select-methods-to-discover-different-things"></a>Wybieranie metody wykrywania różne  
 Aby odnaleźć potencjalne komputery klienckie programu Configuration Manager lub zasoby użytkownika, należy włączyć odpowiednie metody odnajdywania. Można użyć różne kombinacje metod odnajdywania, pozwalające zlokalizować różne zasoby i odnaleźć dodatkowe informacje o tych zasobach. Używane metody odnajdywania określają typ zasobów, które zostały wykryte, oraz usług programu Configuration Manager i agenci są używane w procesie odnajdowania. Określają również typ informacji dotyczących zasobów, które można odnaleźć.  

### <a name="discover-computers"></a>Wykryj komputery   
Jeśli chcesz odnaleźć komputery, można użyć **odnajdywania systemu usługi Active Directory** lub **odnajdowania sieci**.  

 Na przykład jeśli chcesz odnaleźć zasobów, które można zainstalować klienta programu Configuration Manager przed użyciem instalacji wypychanej klienta, można uruchamiać odnajdywania systemu usługi Active Directory. Przy użyciu tej metody, można nie tylko zasób, ale również odnaleźć podstawowe informacje nawet rozszerzone informacje o nim z usług domenowych w usłudze Active Directory. Te informacje mogą być przydatne podczas konstruowania złożonych kwerend oraz kolekcji na potrzeby przypisanie ustawień klienta lub rozmieszczania zawartości.

Alternatywnie można uruchomić odnajdowanie sieci i użycia jej opcji do odnalezienia systemu operacyjnego zasobów (wymagane do późniejszego użycia instalacji wypychanej klienta). Odnajdywanie sieci zapewnia informacje dotyczące topologii sieci, których nie można uzyskać za pomocą innych metod odnajdywania. Ta metoda nie, jednak zapewnia żadnych informacji dotyczących środowiska usługi Active Directory.

 Jest również metodę o nazwie **odnajdywania pulsu**. Istnieje możliwość użycia tylko funkcji odnajdywania pulsu, aby wymusić odnajdywanie klientów zainstalowanych przy użyciu innych metod niż wypychana instalacja klienta. Jednak w przeciwieństwie do innych metod, odnajdywanie pulsu nie umożliwia odnajdywania komputerów bez aktywnego klienta programu Configuration Manager. Zwraca ograniczony zestaw informacji przeznaczonych do obsługi istniejącego rekordu bazy danych, a nie stanowić podstawy tego rekordu. Informacje przesyłane w ramach odnajdywania pulsu mogą nie być wystarczające do tworzenia złożonych kwerend lub kolekcji.  

 Jeśli używasz **odnajdywania grupy usługi Active Directory** odnajdywania członkostwa w określonej grupie, można odnaleźć ograniczone informacje system lub komputer. Nie zastępuje pełnego odnajdywania komputerów, ale może zapewnić podstawowe informacje. Te informacje są wystarczające do instalacji wypychanej klienta.  

### <a name="discover-users"></a>Odnajdywanie użytkowników   
Aby odnaleźć informacje o użytkownikach, należy użyć **odnajdywania użytkownika usługi Active Directory**. Podobnie jak odnajdywanie systemu usługi Active Directory, ta metoda umożliwia odnajdywanie użytkowników usługi Active Directory. Zawiera podstawowe informacje oprócz rozszerzonych informacji usługi Active Directory. Te informacje służą do tworzenia złożonych kwerend i kolekcji podobnych do tych komputerów.  

### <a name="discover-group-information"></a>Odnajdywanie informacji o grupie   
Odnajdywanie informacji o grupach lub członkostwie grupy, należy użyć **odnajdywania grupy usługi Active Directory**. Ta metoda odnajdywania tworzy rekordy zasobów grup zabezpieczeń.  

 Ta metoda służy do wyszukiwania określoną grupę usługi Active Directory, aby ustalić członków tej grupy, oprócz wszystkich zagnieżdżonych grup w tej grupie. Ponadto ta metoda umożliwia wyszukiwanie grup w lokalizacji usługi Active Directory oraz cykliczne wyszukiwanie każdego kontenera podrzędnego tej lokalizacji w usługach Active Directory Domain Services.  

 Ta metoda umożliwia również wyszukiwanie członkostwa w grupach dystrybucyjnych. Pozwala to ustalić relacje w grupie między użytkownikami i komputerami.  

 Po odnalezieniu grupy można również odnaleźć ograniczone informacje o jej elementów członkowskich. To nie zastępuje usługi Active Directory system lub użytkownik metody odnajdywania, mimo że. Jest to zazwyczaj nie wystarcza do utworzenia złożonych kwerend oraz kolekcji ani służyć jako podstawa instalację wypychaną klienta.  

### <a name="discover-infrastructure"></a>Odnajdywanie infrastruktury   
Istnieją dwie metody można użyć do odnajdywania infrastruktury sieci **odnajdywania lasu usługi Active Directory** i **odnajdowania sieci**.  

 Odnajdowanie lasu usługi Active Directory umożliwia wyszukiwanie w lesie usługi Active Directory informacji dotyczących podsieci oraz konfiguracji lokacji usługi Active Directory. Te konfiguracje można następnie automatycznie wprowadzić do programu Configuration Manager jako lokalizacje granic.  

 Jeśli chcesz odnaleźć topologię sieci, użyj funkcji odnajdywania sieci. Inne metody odnajdywania zwracają informacje dotyczące usług domenowych w usłudze Active Directory i umożliwiają ustalenie bieżącej lokalizacji sieciowej klienta, ale nie zapewniają informacji o infrastrukturze na podstawie podsieci i routerów topologii sieci.  

##  <a name="bkmk_shared"></a>Dane odnajdywania są udostępniane między lokacjami  
 Po programu Configuration Manager doda danych odnajdywania do bazy danych, są one szybko udostępniane między wszystkimi lokacjami w hierarchii. Ponieważ nie zazwyczaj żadnych korzyści odnajdywanie tych samych informacji w kilku lokacjach w hierarchii, należy rozważyć skonfigurowanie jednego wystąpienia każdej metody odnajdywania, którego używasz do uruchamiania w jednej lokacji. Jest warto to zrobić, zamiast uruchamiać kilka wystąpień jednej metody w różnych lokacjach.  

 Jednak w niektórych środowiskach mogą być przydatne do przypisywania tej samej metody odnajdywania uruchamianych w wielu lokacjach, każdy z osobną konfiguracją i harmonogramem. Na przykład używając odnajdowania sieci, można skierować każdej lokacji, aby odnaleźć jego sieci lokalnej, zamiast próby odnalezienia wszystkie lokalizacje sieciowe w sieci WAN.

W przypadku skonfigurowania kilku wystąpień tej samej metody odnajdywania uruchamianych w różnych lokacjach, należy uważnie zaplanować konfigurację każdej lokacji. Aby uniknąć dwa lub więcej lokacji odnajdywania tych samych zasobów w sieci lub usługi Active Directory. To użycie dodatkowej przepustowości sieci i utworzenie zduplikowanych rekordów DDR.

W poniższej tabeli przedstawiono lokacje, w których można skonfigurować różne metody odnajdywania.  

|Metoda odnajdywania|Obsługiwane lokalizacje|  
|----------------------|-------------------------|  
|Odnajdywanie lasu usługi Active Directory|Centralna lokacja administracyjna<br /><br /> Lokacja główna|  
|Odnajdywanie grupy usługi Active Directory|Lokacja główna|  
|Odnajdywanie systemu usługi Active Directory|Lokacja główna|  
|odnajdywanie użytkownika usługi Active Directory|Lokacja główna|  
|Odnajdywanie pulsu<sup>1</sup>|Lokacja główna|  
|Odnajdywanie sieci|Lokacja główna<br /><br /> Lokacja dodatkowa|  

 <sup>1</sup> Lokacje dodatkowe nie mogą skonfigurować funkcji odnajdywania pulsu, ale mogą odbierać rekord DDR interwału czasowego od klienta.  

 Gdy lokacje dodatkowe uruchomią funkcję odnajdowania sieci lub odbiorą rekordy DDR odnajdywania pulsu, przesyłają rekord DDR za pomocą replikacji opartych na plikach do ich nadrzędnej lokacji głównej. Jest to spowodowane Lokacje tylko główne i centralne Lokacje administracyjne mogą przetwarzać rekordy DDR. Aby uzyskać więcej informacji o sposobie przetwarzania rekordów DDR, zobacz [informacje o rekordach danych odnajdywania](../../../../core/servers/deploy/configure/run-discovery.md#BKMK_DDRs).  

## <a name="considerations-for-different-discovery-methods"></a>Uwagi dotyczące różne metody odnajdywania  
 Ponieważ każdy lokacji serwera i środowisko sieciowe są różne, to warto Ogranicz konfiguracje początkowego odnajdywania. Następnie dokładnie Monitoruj każdy serwer lokacji dla możliwości przetwarzania generowanych danych odnajdywania.  

Kiedy używasz **usługi Active Directory** metodę odnajdywania dla systemów, użytkowników lub grup:  

-   Uruchom odnajdywanie w lokacji, która ma szybkie połączenie sieciowe z kontrolerami domeny.  

-   Uwzględnij topologię replikacji usługi Active Directory, aby zapewnić funkcji odnajdywania dostęp do najnowszych informacji.  

-   Uwzględnij zakres konfiguracji odnajdywania i Ogranicz odnajdywanie tylko do tych lokalizacji usługi Active Directory i grup, które zostaną odnalezione.  

Jeśli używasz **odnajdowania sieci**:  

-   Użyj ograniczonej konfiguracji początkowej, aby zidentyfikować topografię sieci.  

-   Po zidentyfikowaniu topografii sieci skonfiguruj odnajdowania sieci w określonych lokacjach centralnych względem obszarów sieci wymagających dokładniejszego odnajdywania.  

Ponieważ **odnajdywania pulsu** nie działa w określonej lokacji, nie trzeba uwzględniać jej w ogólnym planowaniu uruchamiania odnajdywania.  

##  <a name="bkmk_best"></a>Najlepsze praktyki dotyczące odnajdywania  
Aby uzyskać najlepsze wyniki przy użyciu funkcji odnajdywania są zalecane:

 - **Uruchom odnajdowanie systemu usługi Active Directory i odnajdowanie użytkowników usługi Active Directory przed uruchomieniem odnajdywania grupy usługi Active Directory.**  

 Podczas odnajdywania grupy usługi Active Directory zidentyfikuje nieodnalezionego wcześniej użytkownika lub komputera jako członka grupy, próbuje odnaleźć podstawowe szczegóły dotyczące użytkownika lub komputera. Ponieważ odnajdywania grupy usługi Active Directory nie jest zoptymalizowana dla tego typu odnajdywania, ten proces może spowodować jej działanie. Ponadto odnajdywania grupy usługi Active Directory identyfikuje tylko podstawowe informacje szczegółowe o użytkownikach i komputerach umożliwia odnalezienie i nie tworzy pełną użytkownika lub komputera rekordu odnajdywania. Po uruchomieniu odnajdywania systemu usługi Active Directory i odnajdowanie użytkowników usługi Active Directory, dostępne są dodatkowe atrybuty usługi Active Directory dla każdego typu obiektu. W związku z tym odnajdywania grupy usługi Active Directory działa bardziej efektywnie.  

- **Podczas konfigurowania odnajdywania grupy usługi Active Directory Określ tylko grupy, które korzystają z programu Configuration Manager.**  

 Aby kontrolować korzystania z zasobów przez odnajdowanie grup usługi Active Directory, określ tylko grupy, które korzystają z programu Configuration Manager. Jest to spowodowane odnajdywania grupy usługi Active Directory rekursywnie wyszukuje każdej odnalezionej grupie Użytkownicy, komputery i grupy zagnieżdżone. Przeszukiwanie każdej zagnieżdżonej grupy może rozszerzyć zakres odnajdywania grupy usługi Active Directory i zmniejszyć wydajność. Ponadto po skonfigurowaniu odnajdowania różnicowego dla odnajdywania grupy usługi Active Directory Metoda odnajdywania monitoruje zmiany w każdej grupie. Powoduje to dodatkowe zmniejszenie wydajności, gdy metoda musi przeszukać niepotrzebne grupy.  

- **Skonfiguruj metody odnajdywania z dłuższym interwałem pomiędzy pełnym odnajdywaniem i krótszym okresem odnajdywania różnicowego.**  

 Ponieważ odnajdywanie różnicowe zużywa mniej zasobów niż pełny cykl odnajdywania i może identyfikować nowe lub zmodyfikowane zasoby w usłudze Active Directory, można zmniejszyć częstotliwość cykli pełnego odnajdywania cotygodniowe (lub mniej). Odnajdywanie różnicowe dla funkcji odnajdywania systemu usługi Active Directory, odnajdowanie użytkowników usługi Active Directory i odnajdowanie grup usługi Active Directory identyfikuje niemal wszystkie zmiany obiektów usługi Active Directory i może zachować dokładne dane odnajdywania dla zasobów.  

- **Uruchom metody odnajdywania usługi Active Directory w lokacji głównej zawierającej lokalizację sieciową najbliższą kontrolerowi domeny usługi Active Directory.**  

 Aby poprawić wydajność odnajdywania usługi Active Directory, jego dobrym rozwiązaniem jest uruchamianie odnajdywania w lokacji głównej, która ma szybkie połączenie sieciowe z kontrolerami domeny. Po uruchomieniu tej samej metody odnajdywania usługi Active Directory w wielu lokacjach, należy skonfigurować każdej metody odnajdywania w celu uniknięcia nakładania. W przeciwieństwie do wcześniejszych wersji programu Configuration Manager dane odnajdywania są współużytkowane przez lokacje. W związku z tym nie jest konieczne odnajdywanie tych samych informacji w kilku lokacjach. Aby uzyskać więcej informacji, zobacz [danych odnajdywania jest udostępniana między lokacjami](../../../../core/servers/deploy/configure/select-discovery-methods-to-use.md#bkmk_shared).  

- **Uruchom odnajdowanie lasu usługi Active Directory w tylko jednej lokacji, jeżeli planowane jest automatyczne tworzenie granic z danych.**  

 Po uruchomieniu odnajdywania lasu usługi Active Directory w więcej niż jednej lokacji w hierarchii jest dobrym pomysłem jest włączenie tylko opcji automatycznego tworzenia granic w jednej lokacji. Jest to spowodowane podczas odnajdywania lasu usługi Active Directory działa w każdej lokacji i tworzy granice, program Configuration Manager nie może scalić tych granic w jeden obiekt granic. Podczas konfigurowania odnajdywania lasu usługi Active Directory do automatycznego tworzenia granic w kilku lokacjach, wynik może być zduplikowanych obiektów granic w konsoli programu Configuration Manager.  

