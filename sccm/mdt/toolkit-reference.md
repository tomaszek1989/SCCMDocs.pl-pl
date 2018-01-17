---
title: "Odwołanie do zestawu narzędzi"
titleSuffix: Microsoft Deployment Toolkit
description: "Szczegóły odwołania dla programu Microsoft Deployment Toolkit 2013. "
ms.date: 09/09/2016
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: article
ms.assetid: ac670143-b7cd-47d0-86ed-14cb2554dfc7
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: f9bd3e2d61ca8b1eddb83fd75de62ba4a123bb7a
ms.sourcegitcommit: 645cd5a324bdd299906efa27eaca5885eafc9e9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2018
---
# <a name="toolkit-reference-for-the-microsoft-deployment-toolkit"></a>Odwołanie do zestawu narzędzi dla programu Microsoft Deployment Toolkit
 To odwołanie jest częścią programu Microsoft® Deployment Toolkit (MDT) 2013 i zawiera ustawienia konfiguracji, które można użyć w ramach procesu wdrażania. Przejrzyj dokumenty zestawu MDT 2013 *Microsoft Deployment Toolkit przykłady Guide* i *przy użyciu programu Microsoft Deployment Toolkit* pomoc w Dostosowywanie ustawień konfiguracji środowiska wdrażania.  

> [!NOTE]
>  W tym dokumencie *Windows* ma zastosowanie do systemów operacyjnych Windows 8.1, Windows 8, Windows 7, Windows Server® 2012 R2, Windows Server 2012 i Windows Server 2008 R2, chyba że określono inaczej. Zestaw MDT nie obsługuje wersji na podstawie procesora ARM systemu Windows. Podobnie *MDT* odwołuje się do zestawu MDT 2013, chyba że określono inaczej.  

## <a name="task-sequence-steps"></a>Kroki sekwencji zadań  
 *Sekwencje zadań* są tworzone przez Edytor sekwencji zadań i składać się z szeregu połączonych kroków, które są przeznaczone do ukończenia działania. Sekwencji zadań może działać przez ponowne uruchomienie komputera i można skonfigurować w celu zautomatyzowania zadań na komputerze bez interwencji użytkownika. Ponadto można dodać kroki sekwencji zadań do grupy sekwencji zadań, która ułatwia dbanie o podobne kroki sekwencji zadań w celu zapewnienia lepszej organizacji i kontroli błędów.  

 Każdy krok sekwencji zadań wykonuje określone zadanie, takich jak sprawdzanie poprawności, który komputer docelowy jest w stanie odbieranie obrazu wdrożenia przechowywania danych użytkownika w bezpiecznej lokalizacji, wdrażania obrazu na komputerze docelowym i podczas przywracania zapisanego danych użytkownika. Te kroki sekwencji zadań wykonywania swoich zadań za pomocą narzędzia i skrypty podany zestaw mdt lub zespołu wdrażania. To odwołanie należy użyć w celu określenia grupy sekwencji zadań poprawne i kroki sekwencji zadań do skonfigurowania procesu wdrażania i prawidłowe właściwości i opcje używane.  

 Następujące informacje są udostępniane dla każdej grupy sekwencji zadań i krok:  

-   **Nazwa**. Nazwa kroku lub grupy sekwencji zadań  

-   **Opis elementu**. Opis przeznaczenia Grupa sekwencji zadań lub kroku oraz wszelkie stosowne informacje dotyczące jego dostosowania  

-   **Właściwości**. Wskazuje właściwości prawidłowej konfiguracji, które można określić dla grupy sekwencji zadań lub krok, definiujące, jak jest wykonywane zadanie  

-   **Opcje**. Wskazuje opcje prawidłowej konfiguracji określonych dla grupy sekwencji zadań lub krok definiujące wtedy, gdy jest wykonywane zadanie i co to jest uznawany za kod pomyślnego zakończenia zadania  

 Aby uzyskać więcej informacji na temat edytora sekwencji zadań, zobacz [wdrożenia systemu operacyjnego: Edytor sekwencji zadań](http://technet.microsoft.com/library/bb680396.aspx).  

###  <a name="CommonPropertiesandOptionsforTaskSequenceStepTypes"></a>Wspólne właściwości i opcje dotyczące typów krok sekwencji zadań  
 Każda Grupa sekwencji zadań i krok ma można skonfigurować ustawienia **właściwości** i **opcje** kart, które są wspólne dla wszystkich grup sekwencji zadań i kroków. Następujące typowe ustawienia krótko opisane w poniższych sekcjach.  

#### <a name="common-properties"></a>Wspólne właściwości
 Tabela 1 zawiera ustawienia, które są dostępne na **właściwości** kartę każdego kroku sekwencji zadań. Aby uzyskać więcej informacji na temat **właściwości** karcie dla określonej sekwencji zadań, zobacz temat, który odpowiada krok w dalszej części tego odwołania.  

> [!NOTE]
>  Typy krok sekwencji zadań przedstawione w tym miejscu są tymi, które są dostępne w konsoli Deployment Workbench. Typy krok sekwencji zadań dodatkowe mogą być dostępne podczas konfigurowania sekwencji zadań przy użyciu programu Microsoft System Center 2012 R2 Configuration Manager.  

##### <a name="table-1-settings-available-on-the-properties-tab"></a>Tabela 1. Ustawienia dostępne na karcie właściwości  

|**Nazwa**|**Opis**|**Grupy**|**Krok**|  
|-|-|-|-|  
|**Typ**|Wartość tylko do odczytu, która wskazuje typ grupa lub krok sekwencji zadań. Typ zostanie ustawiona do jednej z następujących wartości:<br /><br /> -Zastosuj ustawienia sieci<br /><br /> -Autoryzacji DHCP<br /><br /> -Przechwycenie ustawień sieci<br /><br /> -Konfigurowanie DODAJE<br /><br /> — Konfigurowanie serwera DHCP<br /><br /> -Konfigurowanie systemu DNS<br /><br /> -Włącz funkcję BitLocker<br /><br /> -Formatowania i partycjonowania dysku<br /><br /> -Zbierz<br /><br /> -Grupy<br /><br /> -Wstaw sterowniki<br /><br /> — Zainstaluj aplikację<br /><br /> — Zainstaluj System operacyjny<br /><br /> -Zainstaluj role i funkcje<br /><br /> -Instalację aktualizacji w trybie Offline<br /><br /> -Odzyskiwania po awarii Dołącz do domeny<br /><br /> — Ponowne uruchomienie komputera<br /><br /> -Uruchom wiersz polecenia<br /><br /> -Sprawdzanie poprawności|-|-|  
|**Nazwa**|Nazwa użytkownika powinna zezwalać łatwo zidentyfikować i różnicowania od innych zadań kroków sekwencji.|-|-|  
|**Opis**|Opis zdefiniowane przez użytkownika, który należy się upewnić, wymagania dotyczące krok sekwencji zadań i zadań, łatwe do zrozumienia.|-|-|  

#### <a name="common-options"></a>Typowe opcje  
 Tabela 2 zawiera ustawienia, które są dostępne na karcie Opcje kroku sekwencji zadań. Aby uzyskać więcej informacji o karcie opcji, zobacz [kartę Opcje sekwencji zadań](http://technet.microsoft.com/library/bb693661.aspx).  

##### <a name="table-2-settings-available-on-the-options-tab"></a>Tabela 2. Ustawienia dostępne na karcie Opcje  

|**Nazwa**|**Opis**|**Grupy**|**Krok**|  
|-|-|-|-|
|**Wyłącz ten krok**|Wybierz tę opcję, aby wyłączyć ten krok sekwencji zadań.|-|-|  
|**Kody operacji zakończonych powodzeniem**|Zamknij kody narzędzie skojarzony z tym krokiem sekwencji zadań, które wskazują, że krok zakończyło się pomyślnie.||-|  
|**Kontynuuj przy błędzie** |Wybierz tę opcję, aby umożliwić sekwencjonowania zadań przetwarzać dodatkowych kroków sekwencji zadań, jeśli wystąpi błąd.|-|-|  
|**Warunkowe instrukcje**|Co najmniej jeden warunki ograniczające uruchomiona sekwencja zadań — grupa lub krok. Warunkowe te są oparte na następujących czynności:<br /><br /> — Właściwości plik<br /><br /> — Właściwości folderu<br /><br /> Wersja systemu operacyjnego:<br /><br /> — To architektura niektórych<br /><br /> -Jest określonej wersji<br /><br /> -Instrumentacja zarządzania Windows query (WMI)<br /><br /> Ustawienie rejestru:<br /><br /> -Istnieje<br /><br /> -Nie istnieje<br /><br /> — Jest równe<br /><br /> -Nie równa się<br /><br /> — Większa niż<br /><br /> — Większa niż lub równe<br /><br /> — Mniejsza niż<br /><br /> — Mniejsza niż lub równe<br /><br /> -Zainstalowanego oprogramowania<br /><br /> Zmienną sekwencji zadań:<br /><br /> -Istnieje<br /><br /> — Jest równe<br /><br /> -Nie równa się<br /><br /> — Większa niż<br /><br /> — Większa niż lub równe<br /><br /> — Mniejsza niż<br /><br /> — Mniejsza niż lub równe<br /><br /> Te warunki mogą być grupowane przy użyciu **IF** instrukcji, które sprawdzenie wszystkie warunki, warunki i żadnego warunku, który ma wartość True.|-|-|  

> [!NOTE]
>  Dodatkowe instrukcje warunkowe mogą być dostępne, gdy Konfigurowanie kroków sekwencji zadań za pomocą programu Configuration Manager.  

###  <a name="SpecificPropertiesandSettingsforTaskSequenceStepTypes"></a>Właściwości i ustawień dla typów krok sekwencji zadań  
 Niektóre właściwości i parametry każdy typ kroku sekwencji zadań są unikatowe dla tego typu. Każdy typ właściwości unikatowy i ustawieniami jest wyświetlany w poniższych sekcjach z właściwości krok sekwencji zadań unikatowy i ustawienia.  

#### <a name="apply-network-settings"></a>Zastosuj ustawienia sieci  
 Ten krok sekwencji zadań umożliwia skonfigurowanie karty sieciowej na komputerze docelowym. Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które są używane, zobacz [ZTINICConfig.wsf](#ZTINICConfig.wsf).  

 Unikatowe właściwości i ustawienia **Zastosuj ustawienia sieci** typ kroku sekwencji zadań są:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Zastosuj ustawienia sieci|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Nazwa**|Nazwa ma zostać przypisany do połączenie sieciowe.|  
|**Uzyskaj adres IP automatycznie**|Po wybraniu protokołu dynamicznej konfiguracji hosta (DHCP) służy do uzyskiwania wymagane ustawienia konfiguracji protokołu internetowego (IP) dla połączeń sieciowych. To ustawienie domyślne.|  
|**Użyj następującego adresu IP**|W przypadku wybrania, musisz podać co najmniej jednego adresu IP adres podsieci maski kombinacji i oprócz bram, które zostaną przypisane do połączenia sieciowego.|  
|**Uzyskaj automatycznie serwera systemu nazw domen (DNS, Domain Name System)**|W przypadku wybrania, używany jest protokół DHCP uzyskanie wymaganego ustawienia konfiguracji protokołu IP dla połączeń sieciowych. To ustawienie domyślne.|  
|**Użyj następujących serwerów DNS**|W przypadku wybrania, musisz podać co najmniej jeden adres IP serwera DNS, przypisane do połączenia sieciowego.|  
|**Sufiks DNS**|Sufiks DNS, które zostaną zastosowane do wszystkich połączeń sieciowych, które używają protokołu TCP/IP.|  
|**Rejestruj adresy tego połączenia w usłudze DNS**|Określa, czy komputer podejmie próbę rejestracji dynamicznych adresów IP (przy użyciu systemu DNS) tego połączenia z pełną nazwą tego komputera.|  
|**Użyj sufiksu DNS tego połączenia w rejestracji DNS**|Określa, czy dynamicznej aktualizacji DNS jest używana do rejestracji adresów IP i nazwy domeny tego połączenia.|  
|**Adresy serwerów WINS**|Musisz podać co najmniej jednego serwera usługi nazw internetowych systemu Windows (WINS) adresów IP, które zostaną przypisane do połączenia sieciowego.|  
|**Włącz wyszukiwanie LMHOSTS**|Określa, czy plik menedżera hostów (LMHOSTS) sieci lokalnej (LAN) do rozpoznawania nazw systemu NetBIOS sieci podstawowych operacji wejścia/wyjścia jest używane.|  
|**Domyślny**|Określa, czy to połączenie sieciowe uzyskuje ustawienie Włącz lub Wyłącz system NetBIOS przez TCP/IP (NetBT) z serwera DHCP. To ustawienie domyślne.|  
|**Włącz system NetBIOS przez TCP/IP**|Określa, czy to połączenie sieciowe używa NetBT i WINS.|  
|**Wyłącz system NetBIOS przez TCP/IP**|Określa, czy to połączenie sieciowe nie używa NetBT i usługa WINS.|  

#### <a name="authorize-dhcp"></a>Autoryzacji DHCP  
 Ten krok sekwencji zadań autoryzuje komputer docelowy jako serwer DHCP. Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które używania, zobacz [ZTIAuthorizeDHCP.wsf](#ZTIAuthorizeDHCP.wsf).  

 Unikatowe właściwości i ustawienia **autoryzacji DHCP** typ kroku sekwencji zadań są:  

##### <a name="properties"></a>Właściwości  

|**Nazwa**|**Opis**|  
|-|-|  
|**Typ**|Ustaw ten typ tylko do odczytu **autoryzowania serwera DHCP**.|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Opis**|  
|-|-|  
|**Nazwa**|**Opis**|  
|**Konta**|Konto użytkownika, który jest członkiem grupy Administratorzy przedsiębiorstwa, który będzie używany podczas autoryzowania DHCP dla komputera docelowego.|  

#### <a name="capture-network-settings"></a>Przechwyć ustawienia sieci  
 Ten krok sekwencji zadań gromadzi ustawienia karty sieciowej z komputera docelowego. Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które używania, zobacz [ZTINICConfig.wsf](#ZTINICConfig.wsf).  

 Unikatowe właściwości i ustawienia **Przechwyć ustawienia sieci** typ kroku sekwencji zadań są:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Opis**|
|-|-|  
|**Nazwa**|**Opis**|  
|**Typ**|Ustaw ten typ tylko do odczytu **Przechwyć ustawienia sieci**.|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Opis**|  
|-|-|  
|Brak|Brak|  

#### <a name="configure-adds"></a>Skonfiguruj DODAJE  
 Ten krok sekwencji zadań umożliwia skonfigurowanie komputera docelowego jako kontroler domeny usług domenowych Active Directory® (AD DS). Aby uzyskać więcej informacji o ustawieniach wymienione w poniższych tabelach, które można skonfigurować ten krok sekwencji zadań, zobacz artykuł Microsoft Help i pomocy technicznej, [nienadzorowanej podwyższeniem i obniżeniem poziomu domeny systemu Windows 2000 i Windows Server 2003 kontrolery](http://support.microsoft.com/kb/223757).  

 Unikatowe właściwości i ustawienia **skonfigurować DODAJE** typ kroku sekwencji zadań są:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Opis**|  
|-|-|  
|**Typ**|Ustaw ten typ tylko do odczytu **skonfigurować DODAJE**.|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Opis**|  
|-|-|  
|Utwórz|Określa zestaw konfiguracji, która będzie służyć do konfigurowania komputera docelowego. Zestawy konfiguracyjne są:<br /><br /> - **Nowej repliki kontrolera domeny**. Tworzy dodatkowy kontroler domeny w istniejącej domenie usług AD DS<br /><br /> - **Nowej domeny tylko do odczytu (RODC) kontrolera repliki**. Tworzy kontrolera RODC<br /><br /> - **Nowej domeny w istniejącym lesie**. Tworzy domenę w istniejącym lesie usługi AD DS<br /><br /> - **Nowe drzewo domen w istniejącym lesie**. Tworzy nowe drzewo w istniejącym lesie usługi AD DS<br /><br /> - **Nowy las**. Tworzy nowy las usług AD DS|  
|**Nazwy DNS domeny**|Nazwa DNS nowej lub istniejącej domeny.|  
|**Nazwa domeny NetBIOS**|Nazwa NetBIOS nową domenę podrzędną, drzewa domen podrzędnych lub lesie, który wstępnie — AD DS klienci używają do uzyskiwania dostępu do domeny. Ta nazwa musi być unikatowa w sieci.|  
|**Nazwa DNS**|Nazwa DNS domeny podrzędnej lub drzewa domen.|  
|**Kontrolerem domeny źródła replikacji**|Nazwa kontrolera domeny lub kontroler domeny, z którego źródłem usług AD DS w nowej repliki uaktualnienie instalacji. Jeśli wartość nie zostanie podany, będzie domyślnie wybierany najbliższego kontrolera domeny z domeny replikowana.|  
|**Konta**|Konto, które ma być używane do wykonywania konfiguracji.|  
|**Hasło odzyskiwania (tryb awaryjny)**|Hasło dla konta administratora w trybie offline, który jest używany w trybie naprawy usług AD.|  
|**Instalacji usługi DNS, jeśli nie znajduje się już**|Po wybraniu DNS zostanie zainstalowany, jeśli nie został już zainstalowany.|  
|**Ustaw ten kontroler domeny serwera wykazu globalnego (GC)**|Określa, czy replika również będzie serwerem wykazu Globalnego. Po wybraniu komputer docelowy zostanie skonfigurowany jako serwer wykazu Globalnego, jeśli kontrolerem domeny źródła replikacji jest serwerem wykazu Globalnego.|  
|**Poczekaj, aż tylko replikacji krytycznej**|W przypadku wybrania, to ustawienie określa, czy tylko krytyczne replikacji są uzyskiwane podczas fazy replikacji Dcpromo. Replikacja niekrytyczna jest wykonywana wznawia działanie po ponownym uruchomieniu jako kontrolera domeny.|  
|**Poziom funkcjonalności lasu**|Określa poziom funkcjonalności nowego lasu. Dostępne są następujące opcje:<br /><br /> -Windows Server 2003<br /><br /> — Windows Server 2008<br /><br /> — Windows Server 2008 R2|  
|**Poziom funkcjonalności domeny**|Określa poziom funkcjonalności dla nowej domeny. Dostępne są następujące opcje:<br /><br /> -Windows Server 2003<br /><br /> — Windows Server 2008<br /><br /> — Windows Server 2008 R2|  
|**Bazy danych**|W pełni kwalifikowana, z systemem innym niż — UNC Universal Naming Convention katalogu na dysku twardym komputera lokalnego, który będzie hostem bazy danych usług AD DS (NTDS.dit). Jeśli katalog istnieje, może być pusta. Jeśli nie istnieje, zostanie utworzona. Zwolnij miejsce na dysku logicznego wybrane musi być 200 megabajtów (MB) i obszerniejszy, gdy wystąpią błędy zaokrąglania i do wszystkich obiektów w domenie. Aby uzyskać najlepszą wydajność katalogu powinien znajdować się na dysku twardym dedykowanych.|  
|**Pliki dziennika**|W pełni kwalifikowana, innym niż UNC katalogu na dysku twardym komputera lokalnego do hostowania usług AD DS pliki dziennika. Jeśli katalog istnieje, może być pusta. Jeśli nie istnieje, zostanie utworzona.|  
|**FOLDERU SYSVOL**|W pełni kwalifikowana, innym niż UNC katalogu na dysku twardym komputera lokalnego, który będzie hostować pliki usług AD DS systemu woluminu (SYSVOL). Jeśli katalog istnieje, może być pusta. Jeśli nie istnieje, zostanie utworzona. Katalog musi znajdować się na partycji, która jest sformatowany w systemie plików 5.0 wersji systemu plików NTFS. Aby uzyskać najlepszą wydajność katalogu powinien znajdować się na innym dysku twardym fizycznych niż system operacyjny.|  
|**Nazwa witryny**|Wartość istniejącej lokacji usług AD DS, w którym można zlokalizować nowego kontrolera domeny. Jeśli nie zostanie określony, zostanie wybrana odpowiedniej lokacji. Ta opcja ma zastosowanie tylko do nowego drzewa w scenariuszu z nowego lasu. Inne scenariusze lokacji zostanie wybrany przy użyciu bieżącej konfiguracji lokacji i podsieci lasu.|  

#### <a name="configure-dhcp"></a>Konfigurowanie serwera DHCP  
 Ten krok sekwencji zadań konfiguruje usługę serwera DHCP na komputerze docelowym. Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które używania, zobacz [ZTIConfigureDHCP.wsf](#ZTIConfigureDHCP.wsf).  

 Unikatowe właściwości i ustawienia **Konfigurowanie protokołu DHCP** typ kroku sekwencji zadań są:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Opis**|  
|-|-|  
|**Typ**|Ustaw ten typ tylko do odczytu **skonfigurować serwer DHCP**.|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Opis**|  
|-|-|  
|**Nazwa**|Konfigurowanie serwera DHCP|  
|Szczegóły zakresu|Opcje te dotyczą wszystkie komputery klienckie, które uzyskania dzierżawy w ramach określonego zakresu. Skonfigurowana opcja zakresu, wartości zawsze mają zastosowanie do wszystkich komputerów uzyskiwania dzierżawy w danym zakresie, chyba że są zastępowane Opcje przypisane do rezerwacji klasy lub klienta.<br /><br /> W ramach **szczegóły zakresu** ustawienie podrzędne są następujące ustawienia można skonfigurować:<br /><br /> - **Nazwa zakresu**. Nazwa definiowane przez użytkownika<br /><br /> - **Początkowy adres IP**. Początkowy adres IP zakresu<br /><br /> - **Końcowy adres IP**. Końcowy adres IP zakresu<br /><br /> - **Maska podsieci**. Maska podsieci klienta<br /><br /> - **Czas trwania dzierżawy dla klientów DHCP**. Czas trwania dzierżawy DHCP jest prawidłowy dla klienta<br /><br /> - **Opis elementu**. Opis zakresu<br /><br /> - **Wyklucz zakres adresów IP, początkowy adres IP**. Początkowy adres IP dla zakresu adresów IP, które mają być wykluczone z zakresu<br /><br /> -                                 **Wyklucz zakres adresów IP, końcowy adres IP**. Końcowy adres IP dla zakresu adresów IP, które mają być wykluczone z zakresu<br /><br /> - **003 router**. Lista adresów IP routerów w podsieci klienta<br /><br /> - **006 serwerów DNS**. Listę adresów IP dla serwera DNS, nazwy serwerów dostępnych dla klienta<br /><br /> - **Nazwa domeny 015 DNS**. Nazwa domeny, którego powinien skorzystać klient DHCP podczas rozpoznawania nazw niekwalifikowanych domeny z serwerem DNS<br /><br /> -                                 **Serwery WINS/NBNS%0 044**. Wyświetla listę adresów IP serwerów nazw NetBIOS (NBNSes) w sieci<br /><br /> - **Typ węzła WINS/NBT 046**. Określa typ węzła klienta dla klientów NetBT<br /><br /> - **Klient PXE 060**. Adres używany dla kodu inicjowania klienta środowiska wykonawczego przed uruchomieniem (PXE)|  
|Opcje serwera|Te opcje są stosowane globalnie do wszystkich zakresów i klas zdefiniowanych na każdym serwerze DHCP i dla wszystkich klientów że usługi serwera DHCP. Wartości opcji skonfigurowanego serwera zawsze stosuj, chyba że są zastępowane Opcje przypisane do innych rezerwacji zakresu, klasy lub klienta.<br /><br /> W ramach **opcje serwera** ustawienie podrzędne są następujące ustawienia można skonfigurować:<br /><br /> - **003 router**. Lista adresów IP routerów w podsieci klienta<br /><br /> - **006 serwerów DNS**. Listę adresów IP dla serwera DNS, nazwy serwerów dostępnych dla klienta<br /><br /> - **Nazwa domeny 015 DNS**. Nazwa domeny, która powinna być używana przez klientów DHCP podczas rozpoznawania nazw niekwalifikowanych domeny z serwera DNS<br /><br /> - **Serwery WINS/NBNS%0 044**. Wyświetla listę adresów IP dla NBNSes w sieci<br /><br /> -                                 **Typ węzła WINS/NBT 046**. Określa typ węzła klienta dla klientów NetBT<br /><br /> - **Klient PXE 060**. Adres używany dla kodu inicjowania klienta środowiska PXE|  

#### <a name="configure-dns"></a>Konfigurowanie systemu DNS  
 Ten krok sekwencji zadań umożliwia skonfigurowanie DNS na komputerze docelowym. Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które używania, zobacz [ZTIConfigureDNS.wsf](#ZTIConfigureDNS.wsf).  

 Unikatowe właściwości i ustawienia **Konfigurowanie usługi DNS** typ kroku sekwencji zadań są:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Opis**|  
|-|-|  
|**Typ**|Ustaw ten typ tylko do odczytu **konfiguracji serwera DNS**.|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Opis**|  
|-|-|  
|**Nazwa**|Konfigurowanie systemu DNS|  
|Strefy|W ramach **szczegóły zakresu** ustawienie podrzędne są następujące ustawienia można skonfigurować:<br /><br /> -                                 **Nazwa strefy DNS**. Nazwa definiowane przez użytkownika<br /><br /> -Type. Typ strefy DNS należy utworzyć<br /><br /> - **Replikacja**. Określa, schematu replikacji, używany do udostępniania informacji między serwerami DNS<br /><br /> - **Nazwa pliku strefy**. Plik bazy danych strefy DNS<br /><br /> -                                 **Aktualizacje dynamiczne**. Umożliwia komputerom klienckim DNS rejestrowanie i dynamiczne aktualizowanie ich rekordów zasobów przy użyciu serwera DNS po wystąpieniu każdej zmiany<br /><br /> -                                 **Oczyść stare rekordy zasobów**. Usuwa starych rekordów zasobów|  
|Właściwości serwera|Ustawienie właściwości serwera są można skonfigurować następujące ustawienia podrzędne:<br /><br /> -                                 **Wyłącz rekursję**. Określa, że serwer DNS nie będzie wykonywać rekursji dla żadnego zapytania<br /><br /> - **POWIĄŻ pomocnicze**. Określa, czy używany format szybkiego transferu do transferu strefy do serwerów DNS uruchomionych starsze implementacje Berkeley Internet nazwy domeny (BIND)<br /><br /> - **Nie ładuj, jeśli złe dane**. Określa, że serwer DNS powinien ściśle analizy plików<br /><br /> -                                 **Włącz działanie okrężne**. Określa, że serwer DNS należy używać mechanizmu okrężnego obracania i zmiany kolejności lista rekordów zasobów, jeśli istnieje wiele rekordów zasobów tego samego typu istnieje odpowiedzi kwerendy<br /><br /> - **Włącz porządkowanie**. Określa, czy serwer DNS powinien zmienić kolejność rekordy zasobów w ramach tego samego zasobu zestawu rekordów w odpowiedzi na kwerendę na podstawie adresu IP źródła zapytania<br /><br /> - **Zabezpieczenia pamięci podręcznej zanieczyszczeniu**. Określa, czy serwer DNS będzie podejmować próby czyścić odpowiedzi, aby uniknąć zanieczyszczenie pamięci podręcznej<br /><br /> - **Sprawdzanie nazw**. Konfiguruje sprawdzanie nazw metody do użycia|  

> [!NOTE]
>  **Konfigurowanie usługi DNS** sekwencja zadań używa narzędzia Dnscmd, który jest dołączony do narzędzi obsługi systemu Windows, aby skonfigurować usługę DNS. Pamiętaj, że zainstalowano narzędzia obsługi systemu Windows, przed uruchomieniem **Konfigurowanie usługi DNS** krok sekwencji zadań.  

> [!NOTE]
>  Aby uzyskać więcej informacji o tych właściwościach serwera, zobacz [Dnscmd](http://technet.microsoft.com/library/cc772069.aspx).  

#### <a name="enable-bitlocker"></a>Włącz funkcję BitLocker  
 Ten krok sekwencji zadań konfiguruje szyfrowanie dysków® BitLocker na komputerze docelowym. Aby uzyskać więcej informacji o tym typie kroku, zobacz [Włącz funkcję BitLocker](http://technet.microsoft.com/library/bb632526.aspx).  

 Unikatowe właściwości i ustawienia **Włącz funkcję BitLocker** typ kroku sekwencji zadań są:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Opis**|  
|-|-|  
|**Typ**|Ustaw ten typ tylko do odczytu **Włącz funkcję BitLocker**.|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Opis**|  
|-|-|  
|**Bieżący dysk systemu operacyjnego**|Po wybraniu dysku systemu operacyjnego zostanie skonfigurowany. To ustawienie domyślne.|  
|**Określony dysk**|Po wybraniu określonego dysku zostanie skonfigurowany.|  
|**Tylko TPM**|Po wybraniu modułu (TPM) jest wymagana. To ustawienie domyślne.|  
|**Tylko klucz uruchomienia na USB**|Po wybraniu na określony dysk USB wymagany jest klucz uruchomienia.|  
|**Klucza modułu TPM i uruchomienia na USB**|Po wybraniu moduł TPM jest wymagany dodatkowo klucza uruchomienia na określonym dysku USB.|  
|**W usłudze Active Directory**|Po wybraniu klucza odzyskiwania są przechowywane w usługach AD DS. To ustawienie domyślne.|  
|**Nie twórz klucza odzyskiwania**|Po wybraniu klucza odzyskiwania nie zostanie utworzony. Użycie tej opcji nie jest zalecane.|  
|**Poczekaj na zakończenie przez funkcję BitLocker**|Po wybraniu tego kroku nie zostaną zakończone do po zakończeniu funkcji BitLocker podczas przetwarzania wszystkich dysków.|  

####  <a name="ExecuteRunbook"></a>Wykonanie elementu Runbook  
 Ten krok sekwencji zadań uruchamia elementy runbook programu Microsoft System Center 2012 Orchestrator na komputerze docelowym. Orchestrator *runbook* sekwencja działań określająca sposób organizacji działań na komputerach i sieci. Elementy runbook programu Orchestrator mogą inicjować w zestawie MDT przy użyciu tego typu krok sekwencji zadań.  

> [!NOTE]
>  Ten krok sekwencji zadań nie jest uwzględnione wszystkie szablony sekwencji zadań zestawu MDT. Ten krok sekwencji zadań należy dodać do sekwencji zadań utworzone.  

 Unikatowe właściwości i ustawienia **wykonania elementu Runbook** typ kroku sekwencji zadań są:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Opis**|  
|-|-|  
|**Typ**|Ustaw ten typ tylko do odczytu **wykonania elementu Runbook**.|  
|**Nazwa**|Nazwa kroku sekwencji zadań, aby odzwierciedlały nazwa elementu runbook uruchomione.|  
|**Opis**|Tekst informacyjny, który udostępnia dodatkowe informacje o kroku sekwencji zadań|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Opis**|  
|-|-|   
|**Serwer programu orchestrator**|Wpisz adres URL usługi sieci web programu Orchestrator, która zawiera nazwę serwera. Usługa sieci web Orchestrator można użyć protokołu HTTP (Hypertext Transfer) lub HTTP za pośrednictwem warstwy Secure Sockets (HTTPS). Domyślnie usługa sieci web programu Orchestrator na porcie 81.<br /><br /> Usługa sieci web Orchestrator obsługuje wiele serwerów elementów runbook. Domyślnie element runbook może działać na dowolnym serwerze runbook. Aby określić serwerów runbook, które mają być używane do uruchamiania elementu runbook można skonfigurować elementu runbook.<br /><br /> Uwaga:<br /><br /> Usługa sieci web Orchestrator obsługuje możliwość uruchamiania elementu runbook na określonego serwera runbook. Ta funkcja nie jest obsługiwana w zestawie MDT.<br /><br /> Podaj adres URL w jednym z następujących formatów:<br /><br /> - ***ServerName***. Korzystając z tego formatu, adres URL domyślnie:<br /><br /> `http://<servername>:81/Orchestrator2012/Orchestrator.svc`<br /><br /> - ***nazwa_serwera: port***. Korzystając z tego formatu, adres URL domyślnie:<br /><br /> `http://<servername:port>/Orchestrator2012/Orchestrator.svc.`<br /><br /> -**http://*servername:port***. Korzystając z tego formatu, adres URL domyślnie:<br /><br /> `http://<servername:port>/Orchestrator2012/Orchestrator.svc.`<br /><br /> -**http://*servername:port***. Korzystając z tego formatu, adres URL domyślnie:<br /><br /> `https://<servername:port>/Orchestrator2012/Orchestrator.svc.`<br /><br /> - **http://*nazwa_serwera: port*/Orchestrator2012/Orchestrator.svc**. Podczas korzystania z tego formatu, zestawu MDT przyjęto założenie, że udostępniasz pełni kwalifikowany adres URL, ponieważ wartość kończy .svc.<br /><br /> -                                 **https://*nazwa_serwera: port*/Orchestrator2012/Orchestrator.svc**. Podczas korzystania z tego formatu, zestawu MDT przyjęto założenie, że udostępniasz pełni kwalifikowany adres URL, ponieważ wartość kończy .svc.|  
|**Element Runbook**|Kliknij przycisk **Przeglądaj**, a następnie wybierz nazwę elementu runbook programu Orchestrator, które należy uruchomić tej sekwencji zadań.<br /><br /> Uwaga:<br /><br /> Aby pomyślnie Przeglądaj w poszukiwaniu elementy runbook programu Orchestrator, należy zainstalować [aktualizacja ADO.NET Data Services dla programu .NET Framework 3.5 SP1 dla systemu Windows 7 i Windows Server 2008 R2](http://www.microsoft.com/download/details.aspx?displaylang=en&id=2343).|  
|**Automatycznie udostępnić parametrów elementu runbook**|Wybierz tę opcję, aby automatycznie udostępnić Orchestrator runbook wartości parametru wejściowego (który przy założeniu, że wartości parametrów elementu runbook są zmienne sekwencji zadań). Na przykład, jeśli element runbook ma parametr wejściowy o nazwie **OSDComputerName**, a następnie **OSDComputerName** wartość zmiennej sekwencji zadań jest przekazywany do elementu runbook.<br /><br /> Uwaga:<br /><br /> Ta opcja działa tylko dla parametrów wejściowych, które są nazwy zmiennych sekwencji zadań nieprawidłowy i nie zawiera spacji ani innych znaków specjalnych. Spacje i znaki specjalne są obsługiwane jako nazwy parametrów programu Orchestrator, ale nie są one nazwy zmiennych sekwencji zadań prawidłowe. Aby przekazać wartości do parametrów mających spacji ani innych znaków specjalnych, należy użyć **runbook jawne parametry** opcji.<br /><br /> Druga opcja to **runbook jawne parametry**.<br /><br /> Uwaga:<br /><br /> Podane parametry wejściowe elementu runbook z usługą sieci web programu Orchestrator wartości są w formacie XML. Przekazywanie wartości, które zawierają dane, które jest lub podobny dane w formacie XML może powodować błędy.|  
|**Określ parametry jawne elementu runbook**|Wybierz tę opcję, aby jawnie Podaj Orchestrator parametry wejściowe elementu runbook.<br /><br /> Należy skonfigurować następujące ustawienia dla każdego elementu runbook programu Orchestrator wymaga parametru wejściowego:<br /><br /> -                                 **Nazwa**. Jest to nazwa parametru wejściowego elementu runbook.<br /><br /> Uwaga:<br /><br /> W przypadku zmiany parametrów dla istniejącego elementu runbook programu Orchestrator, należy ponownie, przejdź (ponownie) dla elementu runbook ponieważ MDT pobiera tylko z listą parametrów podczas dodawania początkowo runbook programu Orchestrator.<br /><br /> - **Wartość**. Może to być stałą lub zmienną, takie jak zmienna sekwencji zadań lub zmiennej środowiskowej. Na przykład można określić wartość **OSDComputerName %**, który przekazuje wartość **OSDComputerName** zmienną sekwencji zadań do parametr wejściowy elementu runbook.|  
|**Poczekaj na zakończenie przed kontynuowaniem działania elementu runbook**|To pole wyboru określa, czy krok sekwencji zadań będzie czekać na zakończenie przed przejściem do następnego kroku sekwencji zadań dla elementu runbook.<br /><br /> Jeśli to pole wyboru jest:<br /><br /> - **Wybrane**, a następnie sekwencja zadań będzie czekać na element runbook, aby zakończyć działanie przed przejściem do kolejnego kroku sekwencji zadań.<br /><br /> Gdy to pole wyboru jest zaznaczone, krok sekwencji zadań wykona sondowanie usługi sieci web Orchestrator dla elementu runbook zakończyć. Ilość czasu między sond rozpoczyna się od 1 sekundy, a następnie wzrasta do 2, 4, 8, 16, 32 i 64 sekund między każdym sondowania. Gdy czas osiągnie 64 sekund, krok sekwencji zadań w dalszym ciągu sondowania co 64 sekund.<br /><br /> - **Wyczyszczone**, a następnie kroku sekwencji zadań nie będzie czekać na element runbook, aby zakończyć działanie przed przejściem do następnego kroku sekwencji zadań.<br /><br /> Uwaga:<br /><br /> To pole wyboru musi zostać wybrany, gdy element runbook zwraca parametrów wyjściowych.|  

#### <a name="format-and-partition-disk"></a>Formatuj dysk i podziel go na partycje  
 To zadanie sekwencji krok na partycje i sformatowany dysków na komputerze docelowym. Aby uzyskać więcej informacji o tym typie kroku, zobacz [Format i partycji](http://technet.microsoft.com/library/bb680345.aspx).  

 Unikatowe właściwości i ustawienia **Format i partycji** typ kroku sekwencji zadań są:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Opis**|  
|-|-|  
|**Typ**|Ustaw ten typ tylko do odczytu **Format i partycji**.|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Opis**|  
|-|-|  
|**Numer dysku**|Numer fizycznego dysku, który ma być skonfigurowany.|  
|**Typ dysku**|Typ dysku do utworzenia. Dostępne są następujące wartości:<br /><br /> -                                 **Standardowa (MBR)** (główny rekord rozruchowy)<br /><br /> - **GPT** (tabela partycji GUID [Unikatowy identyfikator globalny]).<br /><br /> Ustawieniem domyślnym jest **standardowa (MBR)**.|  
|**Wolumin**|W ramach **woluminu** ustawienie podrzędne są następujące ustawienia można skonfigurować:<br /><br /> -Partycji **nazwa**. Nazwa definiowane przez użytkownika.<br /><br /> - **Typ partycji.** Wartości zależy od typu dysku:<br /><br /> -MBR: **Podstawowy** tylko<br /><br /> -GPT: **Podstawowy**, **EFI**, lub **MSR**<br /><br /> - **Użyj centu pozostałego miejsca.**<br /><br /> -                                 **Użyj rozmiaru dysku.** Wartości są w krokach 1 MB lub 1 gigabajt (GB).<br /><br /> -                                 **Uczyń tę partycję rozruchową.**<br /><br /> -                                 **System plików.** Wartości są **NTFS** lub **FAT32**.<br /><br /> - **Szybkie formatowanie.** Po wybraniu jest wykonywane szybkie formatowanie.<br /><br /> - **Zmienna.** Litera dysku przypisana do tej partycji nowo skonfigurowana.|  

> [!NOTE]
>  Określ dysk twardy i konfiguracje partycji za pomocą pliku CustomSettings.ini, zostaną skonfigurowane tylko na pierwszym dysku twardym i pierwszych dwóch partycji. Edytuj ZTIGather.xml, aby skonfigurować dodatkowe dyski twarde i partycje.  

#### <a name="gather"></a>Zbierz  
 Ten krok sekwencji zadań zbieraniu danych i przetwarzania reguł dla komputera docelowego. Unikatowe właściwości i ustawienia **zebrać** typ kroku sekwencji zadań są:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Opis**|  
|-|-|  
|**Typ**|Ustaw ten odczytu\-tylko typ **zebrać**.|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Opis**|  
|-|-|  
|**Zbierz tylko dane lokalne**|Po wybraniu tego kroku przetwarza tylko właściwości znajdujące się w pliku ZTIGather.xml.|  
|**Zbieranie danych lokalnych i Przetwarzaj reguł**|Po wybraniu tego kroku przetwarza właściwości zawarte w pliku ZTIGather.xml i właściwości zawarte w pliku, który określa pliku reguł. To ustawienie domyślne.|  
|**Plik reguł**|Nazwa pliku reguł do przetworzenia. Jeśli pole pozostanie puste, krok sekwencji zadań próbuje zlokalizować i przetworzyć pliku CustomSettings.ini.|  

> [!NOTE]
>  Ten krok sekwencji zadań jest dostępna natywnie w System Center 2012 R2 Configuration Manager jako **Ustaw zmienne dynamiczne**w grupie ogólne.  

####  <a name="InjectDrivers"></a>Wstaw sterowniki  
 Ten krok sekwencji zadań injects sterowniki, które zostały skonfigurowane do wdrożenia na komputerze docelowym. Unikatowe właściwości i ustawienia **wstrzyknąć sterowniki** typ kroku sekwencji zadań są:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Opis**|  
|-|-|  
|**Typ**|Ustaw ten odczytu\-tylko typ **wstrzyknąć sterowniki**.|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Opis**|  
|-|-|   
|**Zainstaluj tylko zgodne sterowniki**|Injects tylko sterowniki wymagane przez komputer docelowy i co jest dostępne w wychodzących zgodnych\-z\-sterowniki|  
|**Zainstaluj wszystkie sterowniki**|Instaluje wszystkie sterowniki|  
|**Wybór profilu**|Instaluje wszystkie sterowniki w wybranym profilu|  

#### <a name="install-application"></a>Instalowanie aplikacji  
 Ten krok sekwencji zadań instalacji aplikacji na komputerze docelowym. Aby uzyskać więcej informacji o tym typie kroku, zobacz [Zainstaluj oprogramowanie](http://technet.microsoft.com/library/bb680842.aspx).  

 Unikatowe właściwości i ustawienia **zainstaluj aplikację** typ kroku sekwencji zadań są:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Opis**|  
|-|-|   
|**Typ**|Ustaw ten odczytu\-tylko typ **zainstaluj aplikację**.|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Opis**|  
|-|-|  
|**Zainstaluj wiele aplikacji**|Zainstaluj wymagane aplikacje który **MandatoryApplications** została określona właściwość i opcjonalnie aplikacji który **aplikacji** została określona właściwość. Te właściwości są skonfigurowane przez zasady lub zostały określone w trakcie rozmowy Kreatora wdrażania. To ustawienie domyślne.|  
|**Zainstalowania jednej aplikacji**|Określonej aplikacji do zainstalowania. Wybierz aplikację z listy\-w dół listy, która składa się z aplikacji, które zostały skonfigurowane w węźle aplikacji konsoli Deployment Workbench.|  
|**Kody operacji zakończonych powodzeniem**|Odstęp\-rozdzielaną listę kodów zakończenia instalacji aplikacji, które powinny być używane podczas określania pomyślnej instalacji aplikacji.|  

#### <a name="install-operating-system"></a>Instalowanie systemu operacyjnego  
 Ta sekwencja zadań instaluje system operacyjny na komputerze docelowym. Zestaw MDT można wdrożyć, Windows 8.1, Windows 8, Windows 7, Windows Server 2012 R2, Windows Server 2012 i przy użyciu systemu Windows Server 2008 R2:  

-   **Setup.exe**. Ta metoda jest tradycyjnych metodę, zainicjować przez uruchomienie setup.exe z nośnika instalacyjnego. Domyślnie zestaw MDT używa setup.exe.  

-   **ImageX.exe**. Ta metoda instaluje obraz systemu operacyjnego przy użyciu imagex.exe z  **\/zastosować** opcji. Zestaw MDT używa tej metody, gdy nie można użyć metody setup.exe \(tj., jego przełączy się imagex.exe\).  

 Można kontrolować, które z tych metod jest używany przy użyciu **ForceApplyFallback** właściwość, która także ma wpływ na które sekwencji zadań systemu operacyjnego są wyświetlane w Kreatorze wdrażania dla architektury obrazu rozruchowego konkretny procesor. Aby uzyskać więcej informacji, zobacz [ForceApplyFallback](#ForceApplyFallback) właściwości.  

 Unikatowe właściwości i ustawienia **Zainstaluj System operacyjny** typ kroku sekwencji zadań są:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Opis**|  
|-|-|   
|**Typ**|Ustaw ten odczytu\-tylko typ **Zainstaluj System operacyjny**.|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Opis**|  
|-|-|   
|**System operacyjny do zainstalowania**|Nazwa systemu operacyjnego do zainstalowania na komputerze docelowym. Wybierz system operacyjny z spadek\-pozycji listy skompilowana z systemów operacyjnych, które zostały skonfigurowane w węźle systemy operacyjne w konsoli Deployment Workbench.|  
|**Dysk**|Dysk, na którym jest instalowany system operacyjny.|  
|**Partycji**|Partycja, na którym jest instalowany system operacyjny.|  

####  <a name="InstallRolesandFeatures"></a>Instalowanie ról i funkcji  
 Ta sekwencja zadań instaluje wybranych ról i funkcji na komputerze docelowym. Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie oraz właściwości używanych, zobacz [ZTIOSRole.wsf](#ZTIOSRole.wsf).  

 Unikatowe właściwości i ustawienia **zainstalować role i funkcje** typ kroku sekwencji zadań są:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Opis**|  
|-|-|  
|**Typ**|Ustaw ten odczytu\-tylko typ **zainstalować role i funkcje**.|  
|**Opis**|Tekst informacyjny opisującą jego cel kroku sekwencji zadań.|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Opis**|  
|-|-|    
|**Wybierz system operacyjny, dla którego mają zostać zainstalowane role**|Wybierz system operacyjny do wdrażania na komputerze docelowym.|  
|**Wybierz role i funkcje, które powinny być instalowane**|Wybierz jeden lub więcej ról i funkcji do zainstalowania na komputerze docelowym.|  

#### <a name="install-language-packs-offline"></a>Zainstaluj pakiety językowe w trybie Offline  
 Ta sekwencja zadań instaluje aktualizacje do obrazu na komputerze docelowym po wdrożeniu systemu operacyjnego, ale przed elementem docelowym komputerze został uruchomiony ponownie. Należą do nich pakietów językowych. Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które używania, zobacz [ZTIPatches.wsf](#ZTIPatches.wsf).  

 Unikatowe właściwości i ustawienia **zainstalować język pakietów w trybie Offline** typ kroku sekwencji zadań są:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Opis**|  
|-|-|  
|**Typ**|Ustaw ten odczytu\-tylko typ **zainstalować aktualizacji w trybie Offline**.|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Opis**|  
|-|-|  
|**Nazwa pakietu**|Nazwa pakietu pakiet języka, który ma zostać zastosowany do komputera docelowego|  

> [!NOTE]
>  Ten krok sekwencji zadań jest prawidłowa tylko wtedy, gdy przy użyciu zestawu MDT z programem Configuration Manager.  

#### <a name="install-language-packs-online"></a>Zainstaluj pakiety językowe w trybie Online  
 Ta sekwencja zadań instaluje pakiety językowe obrazu na komputerze docelowym po wdrożeniu systemu operacyjnego i po ponownym uruchomieniu komputera docelowego. Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które używania, zobacz [ZTILangPacksOnline.wsf](#ZTILangPacksOnline.wsf).  

 Unikatowe właściwości i ustawienia **zainstalować Online pakietów językowych** typ kroku sekwencji zadań są:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Opis**|  
|-|-|  
|**Typ**|Ustaw ten odczytu\-tylko typ **zainstalować Online pakietów językowych**.|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Opis**|  
|-|-|  
|**Nazwa pakietu**|Nazwa pakietu pakiet języka, który ma zostać zastosowany do komputera docelowego|  

> [!NOTE]
>  Ten krok sekwencji zadań jest prawidłowa tylko wtedy, gdy przy użyciu zestawu MDT z programem Configuration Manager.  

#### <a name="install-updates-offline"></a>Instalowanie aktualizacji w trybie Offline  
 Ta sekwencja zadań instaluje aktualizacje do obrazu na komputerze docelowym po wdrożeniu systemu operacyjnego, ale przed elementem docelowym komputerze został uruchomiony ponownie. Należą do nich pakietów językowych. Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które używania, zobacz [ZTIPatches.wsf](#ZTIPatches.wsf).  

 Unikatowe właściwości i ustawienia **zainstalować aktualizacji w trybie Offline** typ kroku sekwencji zadań są:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Opis**|  
|-|-|  
|**Typ**|Ustaw ten odczytu\-tylko typ **zainstalować aktualizacji w trybie Offline**.|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Opis**|  
|-|-|  
|**Wybór profilu**|Nazwa profilu zaznaczenia, który ma zostać zastosowany do komputera docelowego<br /><br /> Uwaga:<br /><br /> Korzystając z zestawu MDT z programem Configuration Manager, określ nazwę pakietu aktualizacji, który ma zostać zastosowany.|  

#### <a name="recover-from-domain-join-failure"></a>Odzyskiwania po awarii Dołącz do domeny  
 Ten krok sekwencji zadań sprawdza, czy komputer docelowy została przyłączona do domeny. Unikatowe właściwości i ustawienia **odzyskiwania po awarii Dołącz do domeny** typ kroku sekwencji zadań są:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Opis**|  
|-|-|  
|**Typ**|Ustaw ten odczytu\-tylko typ do odzyskania z **niepowodzenie dołączenia domeny**.|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Opis**|  
|-|-|  
|**Automatyczne odzyskiwanie**|Krok sekwencji zadań próbuje dołączyć komputer docelowy do domeny.|  
|**Odzyskaj ręczne**|Jeśli komputer docelowy nie może przyłączyć się do domeny, krok sekwencji zadań powoduje, że sekwencjonowania zadań wstrzymać, co umożliwia próby przyłączenia komputera docelowego do domeny.|  
|**Nie odzyskiwanie**|Jeśli komputer docelowy nie będzie mógł dołączyć do domeny, sekwencja zadań zakończy się niepowodzeniem, zatrzymanie sekwencji zadań.|  

#### <a name="restart-computer"></a>Uruchom ponownie komputer  
 Ten krok sekwencji zadań ponownie uruchomi komputer docelowy. Unikatowe właściwości i ustawienia **ponownego uruchomienia komputera** typ kroku sekwencji zadań są:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Opis**|  
|-|-|  
|**Typ**|Ustaw ten odczytu\-tylko typ **ponownego uruchomienia komputera**.|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Opis**|  
|-|-|  
|**Brak**|Brak|  

#### <a name="run-command-line"></a>Uruchom wiersz polecenia  
 Ten krok sekwencji zadań uruchamia określonych poleceń na komputerze docelowym. Aby uzyskać więcej informacji o tym typie kroku, zobacz [Uruchom wiersz polecenia](http://technet.microsoft.com/library/bb632992.aspx).  

 Unikatowe właściwości i ustawienia **Uruchom wiersz polecenia** typ kroku sekwencji zadań są:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Opis**|  
|-|-|  
|**Typ**|Ustaw ten odczytu\-tylko typ **Uruchom wiersz polecenia**.|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Opis**|  
|-|-|  
|**Wiersz polecenia**|Polecenia do uruchomienia podczas przetwarzania tego kroku sekwencji zadań|  
|**Rozpocznij w**|Folder początkowy dla aplikacji \(ścieżka musi być prawidłową ścieżką na komputerze docelowym.\)|  
|**Uruchom ten krok jako następujące konto**|Umożliwia określenie poświadczeń użytkownika, które będą używane do uruchamiania tego polecenia|  
|**Konta**|Poświadczenia użytkownika, które będą używane do uruchamiania tego polecenia|  
|**Załaduj profil użytkownika**|Po wybraniu ładują profil użytkownika dla określonego konta|  

#### <a name="run-powershell-script"></a>Uruchom skrypt programu PowerShell  
 Ten krok sekwencji zadań uruchamia określony skrypt Windows PowerShell™ na komputerze docelowym. Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które są używane, zobacz [ZTIPowerShell.wsf](#ZTIPowerShell.wsf).  

 Unikatowe właściwości i ustawienia **Uruchom skrypt programu PowerShell** typ kroku sekwencji zadań są:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Opis**|  
|-|-|  
|**Typ**|Ustaw ten odczytu\-tylko typ **Uruchom skrypt programu PowerShell**.|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Opis**|  
|-|-|  
|**Skrypt programu PowerShell**|Skrypt programu Windows PowerShell do uruchomienia podczas przetwarzania tego kroku sekwencji zadań|  
|Parametry|Parametry do przekazania do skryptu programu Windows PowerShell. Parametry te powinny być takie same określony tak, jakby były dodawane do skryptu programu Windows PowerShell z wiersza polecenia.<br /><br /> Parametry podane powinny być tylko tych parametrów, który wykorzystuje skrypt, nie dla wiersza polecenia programu Windows PowerShell.<br /><br /> Poniższy przykład będzie prawidłową wartością dla tego ustawienia:<br /><br /> `-MyParameter1 MyValue1 -MyParameter2 MyValue2`<br /><br /> Poniższy przykład jest nieprawidłową wartością dla tego ustawienia \(elementy pogrubione są niepoprawne\):<br /><br /> `-nologo -executionpolicy unrestricted -File MyScript.ps1 -MyParameter1 MyValue1 -MyParameter2 MyValue2`<br /><br /> Poprzedni przykład jest nieprawidłowy, ponieważ wartość obejmuje polecenia programu Windows PowerShell\-wiersz parametry \(  **\-nologo** i **-executionpolicy unrestricted**\).|  

> [!NOTE]
>  Ten krok sekwencji zadań jest dostępna natywnie w System Center 2012 R2 Configuration Manager jako **Uruchom skrypt programu PowerShell** w grupie ogólne.  

#### <a name="set-task-sequence-variable"></a>Ustaw zmienną sekwencji zadań  
 Ten krok sekwencji zadań ustawia zmienną sekwencji zadań z podaną wartością. Aby uzyskać więcej informacji o tym typie kroku, zobacz [Ustaw zmienną sekwencji zadań](http://technet.microsoft.com/library/bb694306.aspx).  

 Unikatowe właściwości i ustawienia **Ustaw zmienną sekwencji zadań** typ kroku sekwencji zadań są:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Opis**|  
|-|-|  
|**Typ**|Ustaw ten odczytu\-tylko typ **Ustaw zmienną sekwencji zadań**.|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Opis**|  
|-|-|  
|**Zmienną sekwencji zadań**|Nazwa zmiennej, aby zmodyfikować|  
|**Wartość**|Wartość do przypisania do określonej zmiennej|  

####  <a name="UninstallRolesandFeatures"></a>Odinstalowywania ról i funkcji  
 Ten krok sekwencji zadań odinstalowuje wybranych ról i funkcji z komputera docelowego. Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie oraz właściwości używanych, zobacz [ZTIOSRole.wsf](#ZTIOSRole.wsf).  

 Unikatowe właściwości i ustawienia **odinstalowywanie ról i funkcji** typ kroku sekwencji zadań są:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Opis**|  
|-|-|  
|**Typ**|Ustaw ten odczytu\-tylko typ **odinstalowywanie ról i funkcji**.|  
|**Opis**|Tekst informacyjny opisującą jego cel kroku sekwencji zadań.|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Opis**|  
|-|-|  
|**Wybierz system operacyjny, dla którego mają zostać zainstalowane role**|Wybierz system operacyjny do wdrażania na komputerze docelowym.|  
|**Wybierz role i funkcje, które powinny być instalowane**|Wybierz jeden lub więcej ról i funkcji do unstallation z komputera docelowego.|  

#### <a name="validate"></a>Sprawdzanie poprawności  
 Ten krok sekwencji zadań sprawdza, czy komputer docelowy spełnia warunki wstępne określonego wdrożenia. Unikatowe właściwości i ustawienia **weryfikacji** typ kroku sekwencji zadań są:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Opis**|  
|-|-|  
|**Typ**|Ustaw ten odczytu\-tylko typ **weryfikacji**.|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Opis**|  
|-|-|  
|**Zapewnij minimalną ilość pamięci**|W przypadku wybrania, ten krok umożliwia zweryfikowanie, czy ilość pamięci w megabajtach, zainstalowane na komputer docelowy spełnia lub przekracza wartość określoną. Jest to domyślny wybór.|  
|**Zapewnij minimalną szybkość procesora**|Po wybraniu tego kroku sprawdza, czy szybkość procesora w megahercach \(MHz\), zainstalowane w komputer docelowy spełnia lub przekracza wartość określoną. Jest to domyślny wybór.|  
|**Zapewnienia zmieści się rozmiar określonego obrazu**|W przypadku wybrania, ten krok umożliwia zweryfikowanie, czy ilość wolnego miejsca na dysku wyrażony w megabajtach, na komputerze docelowym jest większa lub równa określonej.|  
|**Sprawdź bieżący system operacyjny do odświeżenia**|W przypadku wybrania, ten krok umożliwia zweryfikowanie, że system operacyjny zainstalowany na komputerze docelowym spełnia określone wymagania. Jest to domyślny wybór.|  

> [!NOTE]
>  Ten krok sekwencji zadań jest dostępna natywnie w System Center 2012 R2 Configuration Manager jako **Sprawdź gotowość** w grupie ogólne.  

### <a name="out-of-box-task-sequence-steps"></a>Limit\-z\-polu kroków sekwencji zadań  
 Następujące kroki sekwencji zadań odwołuje się co najmniej jednego z szablonów sekwencji zadań dostępne dołączone do zestawu MDT. Każdy z poniższych przykładach zawiera listę właściwości wstępnie skonfigurowane parametry i opcje i może służyć jako podstawy do tworzenia niestandardowych sekwencji zadań.  

 Tylko właściwości krok sekwencji zadań, parametry i opcje i ich wartości są wyświetlane w przykładach.  

> [!NOTE]
>  Aby uzyskać więcej informacji o każdym kroku sekwencji zadań, zobacz odpowiednich tematów w [wspólne właściwości i opcje dla typów krok sekwencji zadań](#CommonPropertiesandOptionsforTaskSequenceStepTypes) i [właściwości i ustawień dla typów krok sekwencji zadań](#SpecificPropertiesandSettingsforTaskSequenceStepTypes).  

#### <a name="apply-network-settings"></a>Zastosuj ustawienia sieci  
 Ten krok sekwencji zadań umożliwia skonfigurowanie karty sieciowej na komputerze docelowym. Poniżej znajduje się krótki listę ustawień, które pokazują, jak ten krok był oryginalnie skonfigurowany w jednym z szablonów sekwencji zadań zestawu MDT. Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które są używane, zobacz [ZTINICConfig.wsf](#ZTINICConfig.wsf).  

 Domyślna konfiguracja **Zastosuj ustawienia sieci** krok sekwencji zadań jest:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Zastosuj ustawienia sieci|  
|**Nazwa**|Zastosuj ustawienia sieci|  
|**Opis**|Nie określono|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
||Brak parametrów są wstępnie skonfigurowane dla tego kroku. Ten krok powoduje domyślnie, aby skonfigurować kartę sieciową do użycia protokołu DHCP.|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0 3010|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|**Kwalifikator warunkowe**|Nie określono|  

> [!NOTE]
>  Określ konfiguracje kart sieciowych za pomocą pliku CustomSettings.ini, będzie można skonfigurować tylko pierwsza karta sieciowa. Edytuj ZTIGather.xml, aby skonfigurować dodatkowe karty sieciowe.  

#### <a name="apply-patches"></a>Stosowania poprawek  
 Ta sekwencja zadań instaluje aktualizacje do obrazu na komputerze docelowym po wdrożeniu systemu operacyjnego, ale przed elementem docelowym komputerze został uruchomiony ponownie. Poniżej znajduje się krótki listę ustawień, które pokazują, jak ten krok był oryginalnie skonfigurowany w jednym z szablonów sekwencji zadań zestawu MDT. Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które używania, zobacz [ZTIPatches.wsf](#ZTIPatches.wsf).  

 Domyślna konfiguracja **zainstalować aktualizacji w trybie Offline** krok sekwencji zadań jest:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Instalowanie aktualizacji w trybie Offline|  
|**Nazwa**|Stosowania poprawek|  
|**Opis**|Nie określono|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wybór profilu**|Nazwa profilu używany w przypadku wybrania poprawki do zainstalowania na komputerze docelowym|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0 3010|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|**Kwalifikator warunkowe**|Nie określono|  

#### <a name="apply-windows-pe"></a>Zastosuj środowiska Preinstalacyjnego systemu Windows  
 Ten krok sekwencji zadań przygotowuje komputer docelowy może zostać uruchomiony w środowisku preinstalacji systemu Windows \(środowiska Windows PE\). Poniżej znajduje się krótki listę ustawień, które pokazują, jak ten krok był oryginalnie skonfigurowany w jednym z szablonów sekwencji zadań zestawu MDT. Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które używania, zobacz [LTIApply.wsf](#LTIApply.wsf).  

 Domyślna konfiguracja **zastosować środowiska Windows PE** krok sekwencji zadań jest:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Uruchom wiersz polecenia|  
|**Nazwa**|Zastosuj środowiska Preinstalacyjnego systemu Windows|  
|**Opis**|Nie określono|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wiersz polecenia**|`cscript.exe "%SCRIPTROOT%\LTIApply.wsf" /PE`|  
|**Rozpocznij w**|Nie określono|  
|**Uruchom ten krok jako następujące konto**|Nie określono|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0 3010|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|**Kwalifikator warunkowe**|Nie określono|  

#### <a name="backup"></a>Kopia zapasowa  
 Ten krok sekwencji zadań wykonuje kopię zapasową komputera docelowego przed rozpoczęciem wdrażania systemu operacyjnego. Poniżej znajduje się krótki listę ustawień, które pokazują, jak ten krok był oryginalnie skonfigurowany w jednym z szablonów sekwencji zadań zestawu MDT. Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które używania, zobacz [ZTIBackup.wsf](#ZTIBackup.wsf).  

 Domyślna konfiguracja **kopii zapasowej** krok sekwencji zadań jest:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Uruchom wiersz polecenia|  
|**Nazwa**|Kopia zapasowa|  
|**Opis**|Nie określono|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wiersz polecenia**|`cscript.exe "%SCRIPTROOT%\ZTIBackup.wsf"`|  
|**Rozpocznij w**|Nie określono|  
|**Uruchom ten krok jako następujące konto**|Nie określono|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0 3010|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|**Kwalifikator warunkowe**|Nie określono|  

#### <a name="capture-groups"></a>Przechwyć grup  
 Ten krok sekwencji zadań umożliwia przechwytywanie członkostwo grup lokalnych, które istnieją na komputerze docelowym. Poniżej znajduje się krótki listę ustawień, które pokazują, jak ten krok był oryginalnie skonfigurowany w jednym z szablonów sekwencji zadań zestawu MDT. Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które używania, zobacz [ZTIGroups.wsf](#ZTIGroups.wsf).  

 Domyślna konfiguracja **grup przechwytywania** krok sekwencji zadań jest:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Uruchom wiersz polecenia|  
|**Nazwa**|Przechwyć grup|  
|**Opis**|Nie określono|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wiersz polecenia**|`cscript.exe "%SCRIPTROOT%\ZTIGroups.wsf" /capture`|  
|**Rozpocznij w**|Nie został określony.|  
|**Uruchom ten krok jako następujące konto**|Nie określono|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0 3010|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|**Kwalifikator warunkowe**|Nie określono|  

#### <a name="capture-user-state"></a>Przechwyć stan użytkownika  
 Ta sekwencja zadań ma przechwytywać stan użytkownika dla profilów użytkowników, które istnieją na komputerze docelowym. Poniżej znajduje się krótki listę ustawień, które pokazują, jak ten krok był oryginalnie skonfigurowany w jednym z szablonów sekwencji zadań zestawu MDT. Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które są używane, zobacz [ZTIUserState.wsf](#ZTIUserState.wsf). Aby uzyskać więcej informacji o tym typie kroku, zobacz [Przechwyć stan użytkownika](http://technet.microsoft.com/library/bb680924.aspx).  

 Domyślna konfiguracja **Przechwyć stan użytkownika** krok sekwencji zadań jest:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Uruchom wiersz polecenia|  
|**Nazwa**|Przechwyć stan użytkownika|  
|**Opis**|Nie określono|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wiersz polecenia**|`cscript.exe "%SCRIPTROOT%\ZTIUserState.wsf" /capture`|  
|**Rozpocznij w**|Nie określono|  
|**Uruchom ten krok jako następujące konto**|Nie określono|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0 3010|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|**Kwalifikator warunkowe**|Nie określono|  

#### <a name="check-bios"></a>Sprawdzanie systemu BIOS  
 Ten krok sekwencji zadań sprawdza podstawowe dane wejściowe\/output system \(systemu BIOS\) na komputerze docelowym, aby upewnić się, że jest zgodny z systemem operacyjnym wdrażana. Poniżej znajduje się krótki listę ustawień, które pokazują, jak ten krok był oryginalnie skonfigurowany w jednym z szablonów sekwencji zadań zestawu MDT. Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które są używane, zobacz [ZTIBIOSCheck.wsf](#ZTIBIOSCheck.wsf).  

 Domyślna konfiguracja **Sprawdź BIOS** krok sekwencji zadań jest:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Uruchom wiersz polecenia|  
|**Nazwa**|Sprawdzanie systemu BIOS|  
|**Opis**|Nie określono|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wiersz polecenia**|`cscript.exe "%SCRIPTROOT%\ZTIBIOSCheck.wsf"`|  
|**Rozpocznij w**|Nie określono|  
|**Uruchom ten krok jako następujące konto**|Nie określono|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0 3010|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|**Kwalifikator warunkowe**|Nie określono|  

#### <a name="configure"></a>Konfiguruj  
 Ten krok sekwencji zadań umożliwia skonfigurowanie pliku Unattend.xml wartości właściwości wymaganych, które mają zastosowanie do systemu operacyjnego, który jest wdrażany na komputerze docelowym. Poniżej znajduje się krótki listę ustawień, które pokazują, jak ten krok był oryginalnie skonfigurowany w jednym z szablonów sekwencji zadań zestawu MDT. Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które używania, zobacz [ZTIConfigure.wsf](#ZTIConfigure.wsf).  

 Domyślna konfiguracja **Konfiguruj** krok sekwencji zadań jest:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Uruchom wiersz polecenia|  
|**Nazwa**|Konfiguruj|  
|**Opis**|Nie określono|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wiersz polecenia**|`cscript.exe "%SCRIPTROOT%\ZTIConfigure.wsf"`|  
|**Rozpocznij w**|Nie określono|  
|**Uruchom ten krok jako następujące konto**|Nie określono|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0 3010|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|**Kwalifikator warunkowe**|Nie określono|  

#### <a name="copy-scripts"></a>Skopiuj skryptów  
 Tej kopii krok sekwencji zadań skryptów wdrażania używane podczas procesów wdrażania na lokalnym dysku twardym, na komputerze docelowym. Poniżej znajduje się krótki listę ustawień, które pokazują, jak ten krok był oryginalnie skonfigurowany w jednym z szablonów sekwencji zadań zestawu MDT. Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które używania, zobacz [LTICopyScripts.wsf](#LTICopyScripts.wsf).  

 Domyślna konfiguracja **skrypty kopii** krok sekwencji zadań jest:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Uruchom wiersz polecenia|  
|**Nazwa**|Skopiuj skryptów|  
|**Opis**|Nie określono|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wiersz polecenia**|`cscript.exe "%SCRIPTROOT%\LTICopyScripts.wsf"`|  
|**Rozpocznij w**|Nie określono|  
|**Uruchom ten krok jako następujące konto**|Nie określono|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0 3010|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|**Kwalifikator warunkowe**|Nie określono|  

#### <a name="copy-sysprep-files"></a>Skopiuj pliki programu Sysprep  
 Ten krok sekwencji zadań kopiuje pliki programu Sysprep do komputera docelowego. Poniżej znajduje się krótki listę ustawień, które pokazują, jak ten krok był oryginalnie skonfigurowany w jednym z szablonów sekwencji zadań zestawu MDT. Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które używania, zobacz [LTISysprep.wsf](#LTISysprep.wsf).  

 Domyślna konfiguracja **kopiowania plików programu Sysprep** krok sekwencji zadań jest:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Uruchom wiersz polecenia|  
|**Nazwa**|Skopiuj pliki programu Sysprep|  
|**Opis**|Nie określono|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wiersz polecenia**|`cscript.exe "%SCRIPTROOT%\LTISysprep.wsf"`|  
|**Rozpocznij w**|Nie określono|  
|**Uruchom ten krok jako następujące konto**|Nie określono|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0 3010|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|**Kwalifikator warunkowe**|Nie określono|  

#### <a name="create-bitlocker-partition"></a>Tworzenie partycji funkcji BitLocker  
 Ten krok sekwencji zadań ustawia **BDEInstall** właściwości na wartość True, wskazując, że funkcja BitLocker zostanie zainstalowany na komputerze docelowym. Unikatowe właściwości i ustawienia **tworzenie partycji funkcji BitLocker** typ kroku sekwencji zadań są:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|   
|**Typ**|Ustaw zmienną sekwencji zadań|  
|**Nazwa**|Tworzenie partycji funkcji BitLocker|  
|**Opis**|Brak|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Zmienną sekwencji zadań**|Zainstaluj BDE|  
|**Wartość**|Prawda|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0 3010|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|**Kwalifikator warunkowe**|Nie określono|  

#### <a name="create-wim"></a>Utwórz WIM  
 Ta sekwencja zadań tworzy kopię zapasową komputera docelowego. Unikatowe właściwości i ustawienia **utworzyć WIM** typ kroku sekwencji zadań są:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Uruchom wiersz polecenia|  
|**Nazwa**|Utwórz WIM|  
|**Opis**|Brak|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wiersz polecenia**|`cscript.exe "%SCRIPTROOT%\ZTIBackup.wsf"`|  
|**Rozpocznij w**|Nie określono|  
|**Uruchom ten krok jako następujące konto**|Nie określono|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0 3010|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|**Kwalifikator warunkowe**|Nie określono|  

#### <a name="disable-bde-protectors"></a>Wyłącz BDE-Protectors  
 Jeśli funkcja BitLocker jest zainstalowany na komputerze docelowym, ten krok sekwencji zadań wyłącza funkcje ochrony funkcji BitLocker.  

 Unikatowe właściwości i ustawienia **wyłączyć funkcje ochrony BDE** typ kroku sekwencji zadań są:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Uruchom wiersz polecenia|  
|**Nazwa**|Wyłącz BDE-Protectors|  
|**Opis**|Brak|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wiersz polecenia**|`cscript.exe "%SCRIPTROOT%\ZTIDisableBDEProtectors.wsf"`|  
|**Rozpocznij w**|Nie określono|  
|**Uruchom ten krok jako następujące konto**|Nie określono|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0 3010|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|**Kwalifikator warunkowe**|Nie określono|  

#### <a name="enable-bitlocker"></a>Włącz funkcję BitLocker  
 Ten krok sekwencji zadań powoduje włączenie funkcji BitLocker na komputerze docelowym. Poniżej znajduje się krótki listę ustawień, które pokazują, jak ten krok był oryginalnie skonfigurowany w jednym z szablonów sekwencji zadań zestawu MDT. Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które są używane, zobacz [ZTIBde.wsf](#ZTIBde.wsf).  

 Domyślna konfiguracja **Włącz funkcję BitLocker** krok sekwencji zadań jest:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Włącz funkcję BitLocker|  
|**Nazwa**|Włącz funkcję BitLocker|  
|**Opis**|Brak|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Bieżący dysk systemu operacyjnego**|Wybrane|  
|**Tylko TPM**|Wybrane|  
|**Tylko klucz uruchomienia na USB**|Nie wybrano|  
|**Klucza modułu TPM i uruchomienia na USB**|Nie wybrano|  
|**Określony dysk**|Nie wybrano|  
|**W usłudze Active Directory**|Wybrane|  
|**Nie twórz klucza odzyskiwania**|Nie wybrano|  
|**Poczekaj na zakończenie przez funkcję BitLocker**|Nie wybrano|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0 3010|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|**Kwalifikator warunkowe**|**BdeInstallSuppress** tak nie jest równy|  

#### <a name="enable-oem-disk-configuration"></a>Włącz konfigurację dysku przez producenta OEM  
 Ten krok sekwencji zadań ustawia **DeploymentType**właściwości **NEWCOMPUTER**, co pozwala na komputerze docelowym dysku na partycje i sformatowany.  

 Unikatowe właściwości i ustawienia **Włącz konfigurację dysku OEM** typ kroku sekwencji zadań są:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Ustaw zmienną sekwencji zadań |  
|**Nazwa**|Włącz konfigurację dysku przez producenta OEM|  
|**Opis**|Brak|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Zmienną sekwencji zadań**|deploymentType|  
|**Wartość**|NEWCOMPUTER|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0 3010|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|**Kwalifikator warunkowe**|Nie określono|  

#### <a name="end-phase"></a>Faza celu  
 Ten krok sekwencji zadań kończy się bieżąca faza wdrożenia i ponownego uruchomienia komputera docelowego. Poniżej znajduje się krótki listę ustawień, które pokazują, jak ten krok był oryginalnie skonfigurowany w jednym z szablonów sekwencji zadań zestawu MDT.  

 Domyślna konfiguracja **faza celu** krok sekwencji zadań jest:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Uruchom ponownie komputer|  
|**Nazwa**|Faza celu|  
|**Opis**|Nie określono|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|Brak|Brak|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0 3010|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|**Kwalifikator warunkowe**|Nie określono|  

#### <a name="execute-sysprep"></a>Wykonanie programu Sysprep  
 Ten krok sekwencji zadań uruchamia narzędzie Sysprep na komputerze docelowym. Poniżej znajduje się krótki listę ustawień, które pokazują, jak ten krok był oryginalnie skonfigurowany w jednym z szablonów sekwencji zadań zestawu MDT. Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które są używane, zobacz [LTISysprep.wsf](#LTISysprep.wsf).  

 Domyślna konfiguracja **wykonanie programu Sysprep** krok sekwencji zadań jest:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Uruchom wiersz polecenia|  
|**Nazwa**|Wykonanie programu Sysprep|  
|**Opis**|Brak|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wiersz polecenia**|`cscript.exe "%SCRIPTROOT%\LTISysprep.wsf"`|  
|**Rozpocznij w**|Nie określono|  
|**Uruchom ten krok jako następujące konto**|Nie określono|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0 3010|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|**Kwalifikator warunkowe**|Nie określono|  

#### <a name="force-diskpart-action"></a>Wymuszenie akcji Diskpart  
 Jeśli dysku C:\\oem.wsf plik istnieje, ten krok sekwencji zadań Usuwa dysku C:\\oem.wsf pliku, który umożliwi **Format i partycji** krok sekwencji zadań do uruchomienia. Poniżej znajduje się krótki listę ustawień, które pokazują, jak ten krok był oryginalnie skonfigurowany w jednym z szablonów sekwencji zadań zestawu MDT.  

 Domyślna konfiguracja **życie Diskpart akcji** krok sekwencji zadań jest:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Uruchom wiersz polecenia|  
|**Nazwa**|Wymuszenie akcji Diskpart|  
|**Opis**|Nie określono|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wiersz polecenia**|`cmd.exe /c if exist c:\oem.wsf del /q c:\oem.wsf`|  
|**Rozpocznij w**|Nie określono|  
|**Uruchom ten krok jako następujące konto**|Nie określono|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0,1|  
|**Kontynuuj przy błędzie**|Wybrane|  
|**Kwalifikator warunkowe**|Brak|  

#### <a name="format-and-partition-disk"></a>Formatuj dysk i podziel go na partycje  
 Konfiguruje ten krok sekwencji zadań i formaty dysku partycji na komputerze docelowym. Poniżej znajduje się krótki listę ustawień, które pokazują, jak ten krok był oryginalnie skonfigurowany w jednym z szablonów sekwencji zadań zestawu MDT.  

 Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które są używane, zobacz [ZTIDiskpart.wsf](#ZTIDiskpart.wsf).  

 Domyślna konfiguracja **Format i partycji** krok sekwencji zadań jest:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Formatuj dysk i podziel go na partycje|  
|**Nazwa**|Formatuj dysk i podziel go na partycje|  
|**Opis**|Nie określono|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Numer dysku**|0|  
|**Typ dysku**|Standardowe \(MBR\)|  
|**Wolumin**|Ustawienie woluminu sub następujące\-ustawienia:<br /><br /> \-                                 **Nazwa partycji**. Parametr OSDisk<br /><br /> \-**Partycji typu**. Główna<br /><br /> \-                                 **Użyj centu pozostałego miejsca**. Wybrane<br /><br /> \-                                 **Rozmiar\(%\)**. 100<br /><br /> \-**Rozmiar dysku**. Nie wybrano<br /><br /> \-                                 **Uczyń tę partycję rozruchową**. Wybrane<br /><br /> \-**System plików**. SYSTEMU PLIKÓW NTFS<br /><br /> \-**Szybkie formatowanie**. Wybrane<br /><br /> \-**Zmiennej**. Nie określono|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0 3010|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|**Kwalifikator warunkowe**|Nie określono|  

> [!NOTE]
>  Określ dysk twardy i konfiguracje partycji za pomocą pliku CustomSettings.ini, zostaną skonfigurowane tylko na pierwszym dysku twardym i pierwszych dwóch partycji. Edytuj ZTIGather.xml, aby skonfigurować dodatkowe dyski twarde i partycje.  

#### <a name="gather-local-only"></a>Zbierz tylko lokalne  
 Ten krok sekwencji zadań zbiera ustawienia konfiguracji wdrażania z lokalnych źródeł, które są stosowane do komputera docelowego. Poniżej znajduje się krótki listę ustawień, które pokazują, jak ten krok był oryginalnie skonfigurowany w jednym z szablonów sekwencji zadań zestawu MDT.  

 Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które są używane, zobacz [ZTIGather.wsf](#ZTIGather.wsf).  

 Domyślna konfiguracja **Zbierz tylko lokalne** krok sekwencji zadań jest:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Zbierz|  
|**Nazwa**|Zbierz tylko lokalne|  
|**Opis**|Nie określono|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Zbierz tylko dane lokalne**|Wybrane|  
|**Zbieranie danych lokalnych i Przetwarzaj reguł**|Nie wybrano|  
|**Plik reguł**|Nie określono|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0 3010|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|**Kwalifikator warunkowe**|Brak|  

#### <a name="generate-application-migration-file"></a>Generowanie pliku migracji aplikacji  
 Ten krok sekwencji zadań generuje plik ZTIAppXmlGen.xml, który zawiera listę skojarzeń plików, które są zainstalowane na komputerze docelowym. Poniżej znajduje się krótki listę ustawień, które pokazują, jak ten krok był oryginalnie skonfigurowany w jednym z szablonów sekwencji zadań zestawu MDT.  

 Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które są używane, zobacz [ZTIAppXmlGen.wsf](#ZTIAppXmlGen.wsf).  

 Domyślna konfiguracja **Generowanie migracji aplikacji** krok sekwencji zadań w pliku jest:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Uruchom wiersz polecenia|  
|**Nazwa**|Generowanie pliku migracji aplikacji|  
|**Opis**|Nie określono|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wiersz polecenia**|`cscript.exe "%SCRIPTROOT%\ZTIAppXmlGen.wsf" /capture`|  
|**Rozpocznij w**|Nie określono|  
|**Uruchom ten krok jako następujące konto**|Nie określono|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0 3010|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|**Kwalifikator warunkowe**|Brak|  

#### <a name="inject-drivers"></a>Wstaw sterowniki  
 Ten krok sekwencji zadań injects sterowniki, które zostały skonfigurowane do wdrożenia na komputerze docelowym. Poniżej znajduje się krótki listę ustawień, które pokazują, jak ten krok był oryginalnie skonfigurowany w jednym z szablonów sekwencji zadań zestawu MDT.  

 Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które są używane, zobacz [ZTIDrivers.wsf](#ZTIDrivers.wsf).  

 Domyślna konfiguracja **wstrzyknąć sterowniki** krok sekwencji zadań jest:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Wstaw sterowniki|  
|**Nazwa**|Wstaw sterowniki|  
|**Opis**|Nie określono|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Zainstaluj tylko zgodne sterowniki**|Injects tylko te sterowniki, które są wymagane przez komputer docelowy i zgodne z co jest dostępne w wychodzących\-z\-sterowniki|  
|**Zainstaluj wszystkie sterowniki**|Injects wszystkie sterowniki|  
|**Wybór profilu**|Injects sterowniki, które są skojarzone z wybranym profilem|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0 3010|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|**Kwalifikator warunkowe**|Nie określono|  

#### <a name="install-applications"></a>Instalowanie aplikacji  
 Ten krok sekwencji zadań instalacji aplikacji na komputerze docelowym. Poniżej znajduje się krótki listę ustawień, które pokazują, jak ten krok był oryginalnie skonfigurowany w jednym z szablonów sekwencji zadań zestawu MDT.  

 Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które są używane, zobacz [ZTIApplications.wsf](#ZTIApplications.wsf).  

 Domyślna konfiguracja **instalowanie aplikacji** krok sekwencji zadań jest:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Instalowanie aplikacji|  
|**Nazwa**|Instalowanie aplikacji|  
|**Opis**|Nie określono|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Zainstaluj wiele aplikacji**|Wybrane|  
|**Zainstalowania jednej aplikacji**|Nie wybrano|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0 3010|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|**Kwalifikator warunkowe**|Nie określono|  

#### <a name="install-operating-system"></a>Instalowanie systemu operacyjnego  
 Ta sekwencja zadań instaluje system operacyjny na komputerze docelowym. Poniżej znajduje się krótki listę ustawień, które pokazują, jak ten krok był oryginalnie skonfigurowany w jednym z szablonów sekwencji zadań zestawu MDT.  

 Domyślna konfiguracja **Zainstaluj System operacyjny** krok sekwencji zadań jest:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Instalowanie systemu operacyjnego|  
|**Nazwa**|Instalowanie systemu operacyjnego|  
|**Opis**|Nie określono|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|**System operacyjny do zainstalowania**|Ta wartość odpowiada systemu operacyjnego, które zostały wybrane podczas tworzenia sekwencji zadań.|  
|**Dysk**|Dysk, na którym ma zostać zainstalowany system operacyjny.|  
|**Partycji**|Partycja, w którym ma zostać zainstalowany system operacyjny.|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0 3010|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|**Kwalifikator warunkowe**|Nie określono|  

#### <a name="next-phase"></a>Kolejną fazą  
 Ten krok sekwencji zadań aktualizacji **fazy** właściwości do następnej fazy w procesie wdrażania. Poniżej znajduje się krótki listę ustawień, które pokazują, jak ten krok był oryginalnie skonfigurowany w jednym z szablonów sekwencji zadań zestawu MDT.  

 Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które są używane, zobacz [ZTINextPhase.wsf](#ZTINextPhase.wsf).  

 Domyślna konfiguracja **kolejną fazą** krok sekwencji zadań jest:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Uruchom wiersz polecenia|  
|**Nazwa**|Kolejną fazą|  
|**Opis**|Nie określono|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wiersz polecenia**|`cscript.exe "%SCRIPTROOT%\ZTINextPhase.wsf"`|  
|**Rozpocznij w**|Nie określono|  
|**Uruchom ten krok jako następujące konto**|Nie określono|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0 3010|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|**Kwalifikator warunkowe**|Nie określono|  

#### <a name="post-apply-cleanup"></a>Post\-zastosować oczyszczania  
 Ten krok sekwencji zadań, które utraciły niepotrzebnych plików po zainstalowaniu obrazu na komputerze docelowym. Poniżej znajduje się krótki listę ustawień, które pokazują, jak ten krok był oryginalnie skonfigurowany w jednym z szablonów sekwencji zadań zestawu MDT.  

 Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które są używane, zobacz [LTIApply.wsf](#LTIApply.wsf).  

 Domyślna konfiguracja **Post\-zastosować oczyszczania** krok sekwencji zadań jest:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Uruchom wiersz polecenia|  
|**Nazwa**|Post\-zastosować oczyszczania|  
|**Opis**|Nie określono|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wiersz polecenia**|`cscript.exe "%SCRIPTROOT%\LTIApply.wsf" /post`|  
|**Rozpocznij w**|Nie określono|  
|**Uruchom ten krok jako następujące konto**|Nie określono|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0 3010|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|**Kwalifikator warunkowe**|Nie określono|  

#### <a name="recover-from-domain"></a>Odzyskiwanie z domeny  
 Ten krok sekwencji zadań będzie Sprawdź, czy komputer docelowy został przyłączony do domeny. Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które są używane, zobacz [ZTIDomainJoin.wsf](#ZTIDomainJoin.wsf).  

 Unikatowe właściwości i ustawienia odzyskiwanie z typ kroku sekwencji zadań domeny są:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Opis**|  
|-|-|  
|**Typ**|Ta odczytu\-tylko typ ma ustawioną wartość odzyskiwanie po awarii Dołącz do domeny.|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Opis**|  
|-|-|  
|**Automatyczne odzyskiwanie**|Krok sekwencji zadań będzie podejmować próby przyłączenia komputera docelowego do domeny.|  
|**Odzyskaj ręczne**|Jeśli komputer docelowy nie może przyłączyć się do domeny, krok sekwencji zadań spowoduje, że sekwencjonowania zadań wstrzymać, dzięki czemu się, że użytkownik próbuje dołączyć komputer docelowy do domeny.|  
|**Nie odzyskiwanie**|Jeśli komputer docelowy nie będzie mógł dołączyć do domeny, sekwencja zadań zakończy się niepowodzeniem, zatrzymanie sekwencji zadań.|  

#### <a name="restart-computer"></a>Uruchom ponownie komputer  
 Ten krok sekwencji zadań ponownie uruchomi komputer docelowy. Poniżej znajduje się krótki listę ustawień, które pokazują, jak ten krok był oryginalnie skonfigurowany w jednym z szablonów sekwencji zadań zestawu MDT.  

 Domyślna konfiguracja **ponownego uruchomienia komputera** krok sekwencji zadań jest:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Uruchom ponownie komputer|  
|**Nazwa**|Uruchom ponownie komputer|  
|**Opis**|Nie określono|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|Brak|Brak|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0 3010|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|**Kwalifikator warunkowe**|Nie określono|  

#### <a name="restore-groups"></a>Przywróć grup  
 Ten krok sekwencji zadań przywraca uprzednio przechwycony członkostwo grup lokalnych na komputerze docelowym. Poniżej znajduje się krótki listę ustawień, które pokazują, jak ten krok był oryginalnie skonfigurowany w jednym z szablonów sekwencji zadań zestawu MDT.  

 Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które są używane, zobacz [ZTIGroups.wsf](#ZTIGroups.wsf).  

 Domyślna konfiguracja **przywrócić grup** krok sekwencji zadań jest:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Uruchom wiersz polecenia|  
|**Nazwa**|Przywróć grup|  
|**Opis**|Nie określono|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wiersz polecenia**|`cscript.exe "%SCRIPTROOT%\ZTIGroups.wsf" /restore`|  
|**Rozpocznij w**|Nie określono|  
|**Uruchom ten krok jako następujące konto**|Nie określono|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0 3010|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|**Kwalifikator warunkowe**|Jeśli wszystkie warunki są spełnione:<br /><br /> \-**DoCapture** tak nie jest równy<br /><br /> \-                                 **DoCapture** przygotowywanie nie jest równy|  

####  <a name="RestoreUserState"></a>Przywróć stan użytkownika  
 Ten krok sekwencji zadań przywraca wcześniej przechwyconego stanu użytkownika z komputerem docelowym. Poniżej znajduje się krótki listę ustawień, które pokazują, jak ten krok był oryginalnie skonfigurowany w jednym z szablonów sekwencji zadań zestawu MDT.  

 Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które są używane, zobacz [ZTIUserState.wsf](#ZTIUserState.wsf).  

 Aby uzyskać więcej informacji o tym typie kroku, zobacz [Przywróć stan użytkownika](http://technet.microsoft.com/library/bb632881.aspx).  

 Domyślna konfiguracja **Przywróć stan użytkownika** krok sekwencji zadań jest:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Uruchom wiersz polecenia|  
|**Nazwa**|Przywróć stan użytkownika|  
|**Opis**|Nie określono|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wiersz polecenia**|`cscript.exe "%SCRIPTROOT%\ZTIUserState.wsf" /restore`|  
|**Rozpocznij w**|Nie określono|  
|**Uruchom ten krok jako następujące konto**|Nie określono|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0 3010|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|**Kwalifikator warunkowe**|Jeśli wszystkie warunki są spełnione:<br /><br /> \-Jeśli **DoCapture** tak nie jest równy<br /><br /> \-Jeśli **DoCapture** przygotowywanie nie jest równy|  

#### <a name="set-image-build"></a>Tworzenie obrazu zestawu  
 Ten krok sekwencji zadań ustawia **ImageBuild** właściwości do wartości zawartych w **OSCurrentVersion**. Poniżej znajduje się krótki listę ustawień, które pokazują, jak ten krok był oryginalnie skonfigurowany w jednym z szablonów sekwencji zadań zestawu MDT.  

 Domyślna konfiguracja **ustawić kompilacji obrazu** krok sekwencji zadań jest:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Ustaw zmienną sekwencji zadań|  
|**Nazwa**|Tworzenie obrazu zestawu|  
|**Opis**|Nie określono|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Zmienną sekwencji zadań**|**ImageBuild**|  
|**Wartość**|**% OSCurrentVersion %**|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|**0 3010**|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|**Kwalifikator warunkowe**|Nie określono|  

#### <a name="set-image-flags"></a>Ustaw flagi obrazu  
 Ten krok sekwencji zadań ustawia **ImageFlags** właściwości do wartości zawartych w **OSSKU**. Poniżej znajduje się krótki listę ustawień, które pokazują, jak ten krok był oryginalnie skonfigurowany w jednym z szablonów sekwencji zadań zestawu MDT.  

 Domyślna konfiguracja **Ustaw flagi obrazu** krok sekwencji zadań jest:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Ustaw zmienną sekwencji zadań|  
|**Nazwa**|Ustaw flagi obrazu|  
|**Opis**|Nie określono|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Zmienną sekwencji zadań**|ImageFlags|  
|**Wartość**|% OSSKU %|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0 3010|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|**Kwalifikator warunkowe**|Nie określono|  

#### <a name="tattoo"></a>Tatuaż  
 Ten krok sekwencji zadań tattoos do komputera docelowego z identyfikacji i informacje o wersji. Poniżej znajduje się krótki listę ustawień, które pokazują, jak ten krok był oryginalnie skonfigurowany w jednym z szablonów sekwencji zadań zestawu MDT.  

 Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które są używane, zobacz [ZTITatoo.wsf](#ZTITatoo.wsf).  

 Domyślna konfiguracja **tatuaż** krok sekwencji zadań jest:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Uruchom wiersz polecenia|  
|**Nazwa**|Tatuaż|  
|**Opis**|Nie określono|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wiersz polecenia**|`cscript.exe "%SCRIPTROOT%\ZTITatoo.wsf"`|  
|**Rozpocznij w**|Nie określono|  
|**Uruchom ten krok jako następujące konto**|Nie określono|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0 3010|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|Kwalifikator warunkowe|Nie określono|  

#### <a name="validate"></a>Sprawdzanie poprawności  
 Ten krok sekwencji zadań sprawdza, czy komputer docelowy spełnia warunki wstępne określonego wdrożenia. Poniżej znajduje się krótki listę ustawień, które pokazują, jak ten krok był oryginalnie skonfigurowany w jednym z szablonów sekwencji zadań zestawu MDT.  

 Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które są używane, zobacz [ZTIValidate.wsf](#ZTIValidate.wsf).  

 Domyślna konfiguracja **weryfikacji** krok sekwencji zadań jest:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Sprawdzanie poprawności|  
|**Nazwa**|Sprawdzanie poprawności|  
|**Opis**|Nie określono|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Zapewnij minimalną ilość pamięci \(MB\)**|Wybrany. Selektor wartość jest równa **768**.|  
|**Zapewnij minimalną szybkość procesora \(MHz\)**|Wybrany. Selektor wartość jest równa **800**.|  
|**Zapewnienia zmieści się rozmiar określonego obrazu \(MB\)**|Nie wybrano.|  
|**Sprawdź bieżący system operacyjny do odświeżenia**|Wybrany. Selektor wartość jest równa **serwera** lub **klienta**w zależności od szablonu używany do tworzenia sekwencji zadań.|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0 3010|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|**Kwalifikator warunkowe**|Nie określono|  

#### <a name="windows-update-pre-application-installation"></a>Usługi Windows Update \(sprzed\-instalacji aplikacji)  
 Ta sekwencja zadań instaluje aktualizacje do komputera docelowego przed zainstalowaniem aplikacji. Poniżej znajduje się krótki listę ustawień, które pokazują, jak ten krok był oryginalnie skonfigurowany w jednym z szablonów sekwencji zadań zestawu MDT.  

 Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które są używane, zobacz [ZTIWindowsUpdate.wsf](#ZTIWindowsUpdate.wsf).  

 Domyślna konfiguracja **usługi Windows Update \(sprzed\-instalacji aplikacji\)**  krok sekwencji zadań jest:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|   
|**Typ**|Uruchom wiersz polecenia|  
|**Nazwa**|Usługi Windows Update \(sprzed\-instalacji aplikacji\)|  
|**Opis**|Nie określono|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wiersz polecenia**|`cscript.exe "%SCRIPTROOT%\ZTIWindowsUpdate.wsf"`|  
|**Rozpocznij w**|Nie określono|  
|**Uruchom ten krok jako następujące konto**|Nie określono|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|   
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0 3010|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|**Kwalifikator warunkowe**|Nie określono|  

#### <a name="windows-update-post-application-installation"></a>Usługi Windows Update (aplikacji po instalacji)  
 Ten krok sekwencji zadań jest taka sama jak **usługi Windows Update (Instalacja aplikacji przed)** krok sekwencji zadań.  

#### <a name="wipe-disk"></a>Wyczyść dysk  
 Ten krok sekwencji zadań czyści wszystkie informacje z dysku przy użyciu **Format** polecenia.  

 Aby uzyskać więcej informacji na temat skryptu, które wykonuje to zadanie i właściwości, które są używane, zobacz [ZTIWipeDisk.wsf](#ZTIWipeDisk.wsf).  

 Domyślna konfiguracja **czyszczenia dysku** krok sekwencji zadań jest:  

##### <a name="properties"></a>Właściwości  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Typ**|Uruchom wiersz polecenia|  
|**Nazwa**|Wyczyść dysk|  
|**Opis**|To spowoduje tylko jeśli wykonywania **narzędzia WipeDisk**= TRUE w CustomSettings.ini|  

##### <a name="settings"></a>Ustawienia  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wiersz polecenia**|`cscript.exe "%SCRIPTROOT%\ZTIWipeDisk.wsf"`|  
|**Rozpocznij w**|Nie określono|  
|**Uruchom ten krok jako następujące konto**|Nie określono|  

##### <a name="options"></a>Opcje  
|**Nazwa**|**Wartość**|  
|-|-|  
|**Wyłącz ten krok**|Nie wybrano|  
|**Kody operacji zakończonych powodzeniem**|0 3010|  
|**Kontynuuj przy błędzie**|Nie wybrano|  
|**Kwalifikator warunkowe**|Nie określono|  

## <a name="properties"></a>Właściwości  
 Skrypty używane w Lite Touch Installation (LTI) i ZTI właściwości odwołania do określenia kroki tej procedury i ustawienia konfiguracji używane podczas procesu wdrażania. Skrypty niektóre z tych właściwości automatyczne tworzenie. Inne właściwości musi być skonfigurowany w pliku CustomSettings.ini. Niektóre z tych właściwości są:  

-   Dotyczą tylko ZTI  

-   Właściwe tylko LTI.  

-   Do użytku w ZTI i LTI  

 Użyj tego odwołania w celu określenia prawidłowe właściwości do skonfigurowania i prawidłowe wartości, które obejmują dla każdej właściwości.  

 Dla każdej właściwości podano następujące informacje:  

-   **Opis elementu**. Zawiera opis przeznaczenia właściwość i wszelkie stosowne informacje dotyczące dostosowywania właściwości.  

    > [!NOTE]
    >  Chyba że jawnie określone dla ZTI lub LTI tylko właściwość jest ważne dla ZTI i LTI.  

-   **Wartość i opis**. Wskazuje prawidłowe wartości, które można określić dla właściwości i krótki opis oznacza każdej wartości. (Wartości kursywą wskazują, że wartość zostanie zastąpiony — na przykład wartość *Użytkownik1*, *Użytkownik2* oznacza to, że *Użytkownik1* i *Użytkownik2* może być zastąpiony rzeczywistą nazwą konta użytkowników.)  

-   **Przykład**. Przykład użycia właściwości jako może pojawiać się pliki .ini.  

 Aby uzyskać więcej informacji na temat tych i innych właściwości sekwencji zadań, które mogą odwoływać się podczas wykonywania wdrożenia ZTI, zobacz [zmienne sekwencji zadań wdrożenia systemu operacyjnego](http://technet.microsoft.com/library/bb632442.aspx).  

 Skrypty wdrażania wymagają wartości należy określić wielkimi literami, dzięki czemu są one prawidłowo odczytać. Dlatego podczas określania wartości właściwości, należy używać wielkich liter.  

### <a name="property-definition"></a>Definicja właściwości  
 W poniższych sekcjach opisano właściwości, które są dostępne we wdrożeniach LTI oraz ZTI w zestawie MDT.  

> [!TIP]
>  Właściwości są sortowane w kolejności alfabetycznej.  

####  <a name="\_SMSTSOrgName"></a>\_SMSTSOrgName  
 Dostosowuje aparat sekwencjonowania zadań wyświetl transparent  
|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|  
|*Nazwa*|Nazwę, która będzie używana w aparat sekwencjonowania zadań wyświetl transparent|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] _SMSTSOrgName=Woodgrove Bank`|  

####  <a name="ADDSLogPath"></a>ADDSLogPath  
 W pełni kwalifikowana, innym niż UNC katalogu na dysku twardym komputera lokalnego do hostowania usług AD DS pliki dziennika. Jeśli istnieje katalog może być pusta. Jeśli nie istnieje, zostanie utworzona.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|  
|*log_path*|W pełni kwalifikowana, pliki dziennika z systemem innym niż UNC katalogu na dysku twardym komputera lokalnego do hostowania usług AD DS|  

|**Przykład**|
|-|   
|`[Settings] Priority=Default  [Default] ADDSLogPath=%DestinationLogicalDrive%\Windows\NTDS`|  

####  <a name="ADDSPassword"></a>ADDSPassword  
 Poświadczenia konta, które mogą być używane podczas podwyższania poziomu serwera do poziomu kontrolera domeny.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|  
|*hasło*|Poświadczenia konta, które mogą być używane dla operacji podwyższenia poziomu|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] ADDSUserName=Administrator ADDSUserDomain=WoodGroveBank ADDSPassword=<complex_password>`|  

####  <a name="ADDSUserDomain"></a>ADDSUserDomain  
 Jest to domena konta wskazanego przez **ADDSUserName** ma zostać pobrany. W przypadku operacji do tworzenia nowego lasu lub jako serwer członkowski z uaktualniania kontrolera domeny nie jest domyślnie. W przypadku operacji tworzenia nowego drzewa, domyślnie jest nazwa DNS lasu komputer jest obecnie przyłączona do. Jeśli operacja jest utworzenie nowej domeny podrzędnej lub replikę następnie domyślny jest nazwą DNS, komputer jest przyłączony do domeny. Jeśli komputer jest kontrolerem domeny w domenie podrzędnej jest operacja obniżenia poziomu komputera, wartość domyślna to nazwę DNS domeny nadrzędnej. Jeśli operacja jest obniżenia poziomu komputera, a komputer jest kontrolerem domeny w domenie katalogu głównego drzewa, wartość domyślna to nazwa DNS lasu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|  
|*domeny*|Nazwa użytkownika konta domeny, należy go pobrać z|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] ADDSUserName=Administrator ADDSUserDomain=WoodGroveBank ADDSPassword=<complex_password>`|  

####  <a name="ADDSUserName"></a>ADDSUserName  
 Poświadczenia konta, które będą używane podczas podwyższania poziomu serwera do poziomu kontrolera domeny.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|  
|*nazwa_użytkownika*|Poświadczenia konta, które będą używane dla operacji podwyższenia poziomu|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] ADDSUserName=Administrator ADDSUserDomain=WoodGroveBank ADDSPassword=complex_password`|  

####  <a name="Administrators"></a>Administratorzy  
 Lista kont użytkowników i grup domeny, które zostaną dodane do lokalnej grupy administratorów na komputerze docelowym. **Administratorzy** właściwości znajduje się lista wartości tekstowych, które mogą być dowolnego niepustą wartość. **Administratorzy** właściwość ma sufiks numeryczny (na przykład **Administrators001** lub **Administrators002**).  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|  
|*Nazwa*|Nazwa użytkownika lub grupę, która ma zostać dodany do lokalnej grupy administratorów|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] Administrators001=WOODGROVEBANK\NYC Help Desk Staff Administrators002=WOODGROVEBANK\North America East Help Desk Staff PowerUsers001=WOODGROVEBANK\User01 PowerUsers002=WOODGROVEBANK\User02`|  

####  <a name="AdminPassword"></a>AdminPassword  
 Określa hasło, które zostaną przypisane do konta użytkownika administratora lokalnego na komputerze docelowym. Jeśli nie zostanie określony, będzie służyć przed wdrożeniem hasło konta administratora.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*admin_password*|Hasło, które ma być przypisana do konta administratora na komputerze docelowym|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] Administrators001=WOODGROVEBANK\NYC Help Desk Staff AdminPassword=<admin_password>`|  

####  <a name="Applications"></a>Aplikacje  
 Lista identyfikatorów GUID aplikacji, które należy zainstalować na komputerze docelowym. Te aplikacje są określone w węźle aplikacji w konsoli Deployment Workbench. Te identyfikatory GUID są przechowywane w pliku Applications.xml. **Aplikacji** właściwości znajduje się lista wartości tekstowych, które mogą być dowolnego niepustą wartość. **Aplikacji** właściwość ma sufiks numeryczny (na przykład **Applications001** lub **Applications002**).  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*application_guid*|Identyfikator GUID jest określany przez konsoli Deployment Workbench dla aplikacji do wdrażania na komputerze docelowym. Identyfikator GUID odpowiada aplikacji, w której przechowywane w pliku Applications.xml identyfikatora GUID.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] Applications001={1D7DF331-47B7-472C-87B3-442597EC2F7D} Applications002={9d2b8999-5e4d-4f3d-bb05-edaaf4fe5628}`|  

####  <a name="ApplicationSuccessCodes"></a>ApplicationSuccessCodes  
 Rozdzieloną spacjami listę używane przez skrypt ZTIApplications kody błędów, które określają pomyślnej instalacji aplikacji.  

> [!NOTE]
>  Ta właściwość ma zastosowanie tylko do **zainstaluj aplikację** typ kroku sekwencji zadań i kiedy **zainstalować wiele aplikacji** jest zaznaczone.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*error_codes*|Kody błędów, które określają, kiedy aplikacji zostały pomyślnie zainstalowane. Wartości domyślne są **0** i **3010**.|  

|**Przykład**|  
|-|    
|`[Settings] Priority=Default  [Default] ApplicationSuccessCodes=0 3010`|  

####  <a name="ApplyGPOPack"></a>ApplyGPOPack  
 Ta właściwość jest używana do określenia czy **zastosuj pakiet lokalny obiekt zasad grupy** jest wykonywane w kroku sekwencji zadań.  

> [!NOTE]
>  Wartość domyślna dla tej właściwości jest zawsze przeprowadza **zastosuj pakiet lokalny obiekt zasad grupy** krok sekwencji zadań. Należy jawnie Podaj wartość "Nie", aby zmienić to zachowanie.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|  
|**TAK**|**Zastosuj pakiet lokalny obiekt zasad grupy** jest wykonywane w kroku sekwencji zadań. Jest to wartość domyślna.|  
|**BRAK**|**Zastosuj pakiet lokalny obiekt zasad grupy** krok sekwencji zadań nie jest wykonywana.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] ApplyGPOPack=NO`|  

####  <a name="Architecture"></a>Architektura  
 Architektura procesora procesora, które jest aktualnie uruchomione, i nie jest obsługiwane przez komputer docelowy architektury procesora. Na przykład, gdy uruchomiona systemu operacyjnego zgodnym z 32-bitowych na 64-bitowy procesor, **architektura** oznacza, że architektura procesora 32-bitowych.  

 Użyj **CapableArchitecture** właściwość do identyfikacji architektura procesora rzeczywistych, która obsługuje komputera docelowego.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez zestaw MDT skrypty i nie jest skonfigurowany w CustomSettings.ini. Traktować tę właściwość jako tylko do odczytu. Jednak służy tej właściwości w CustomSettings.ini, jak pokazano w poniższych przykładach ułatwiających definiując konfigurację komputera docelowego.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|**x86**|Architektura procesora jest 32-bitowych.|  
|**x64**|Architektura procesora jest 64-bitowym.|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="AreaCode"></a>Numer kierunkowy  
 Numer kierunkowy do skonfigurowania systemu operacyjnego na komputerze docelowym. Ta właściwość umożliwia tylko cyfry. Ta wartość jest wstawiany odpowiednie ustawienia konfiguracji w pliku Unattend.xml.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*numer_kierunkowy*|Numer kierunkowy, w którym ma zostać wdrożona na komputerze docelowym|  

|**Przykład**|  
|-|    
|`[Settings] Priority=Default  [Default] AreaCode=206 CountryCode=001 Dialing=TONE LongDistanceAccess=9`|  

####  <a name="AssetTag"></a>AssetTag  
 Liczba tagów zasobów skojarzonych z komputerem docelowym. Format liczb tag zasobu jest niezdefiniowana. Ta właściwość służy do tworzenia podsekcji, zawierający ustawienia przeznaczone dla określonego komputera.  

> [!NOTE]
>  Tej właściwości ustawiono dynamicznie przez zestaw MDT skrypty i nie może mieć jego wartość ustawiona w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu. Jednak służy tej właściwości w CustomSettings.ini lub zestaw MDT bazy danych, jak pokazano w poniższych przykładach ułatwiających definiując konfigurację komputera docelowego.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*asset_tag*|Format tagu zasobu nie jest zdefiniowana i zależy od standardowego tagu zasobów każdej organizacji.|  

|**Przykład 1**|  
|-|   
|`[Settings] Priority=Default  [Default] OSDComputerName=HP-%AssetTag%`|  

|**Przykład 2**|  
|-|    
|`[Settings] Priority=AssetTag, Default  [Default] OSInstall=YES  [0034034931] OSDComputerName=HPD530-1  [0034003233] OSDNEWMACHINENAME=BVMXP`|  

####  <a name="AutoConfigDNS"></a>AutoConfigDNS  
 Określa, czy Kreator instalacji usługi Active Directory konfiguruje DNS dla nowej domeny, jeśli wykryje, że protokół dynamicznej aktualizacji DNS nie jest dostępna.  

> [!CAUTION]
>  Wartość tej właściwości należy określić pisane wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|**TAK**|Konfiguruje usługę DNS dla nowej domeny, jeśli protokół dynamicznej aktualizacji DNS nie jest dostępna|  
|**BRAK**|Nie Konfiguruj DNS dla domeny|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] AutoConfigDNS=YES`|  

####  <a name="BackupDir"></a>BackupDir  
 Folder, w którym są przechowywane kopie zapasowe na komputerze docelowym. Ten folder istnieje pod ścieżki UNC określonej w **BackupShare** właściwości. Jeśli folder nie istnieje, zostanie automatycznie utworzony.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*Folder*|Nazwa folderu, który istnieje pod folderu udostępnionego, określona w **BackupShare** właściwości|  

|**Przykład**|  
|-|    
|`[Settings] Priority=Default  [Default] DoCapture=YES BackupShare=\\NYC-AM-FIL-01\Backup$ BackupDir=%OSDComputerName% BackupDrive=C:`|  

####  <a name="BackupDrive"></a>BackupDrive  
 Dysk do uwzględnienia w kopii zapasowej na komputerze docelowym. Ta właściwość jest domyślnie dysk, który zawiera partycję dysku 0, 1. Można również wybrać opcję **wszystkich**.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*backup_drive*|Litera dysku, aby utworzyć kopię zapasową|  
|**WSZYSTKIE**|Utworzyć kopię zapasową wszystkich dyskach na komputerze docelowym|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] DoCapture=YES BackupShare=\\NYC-AM-FIL-01\Backup$ BackupDir=%OSDComputerName% BackupDrive=C:`|  

####  <a name="BackupFile"></a>Plik  
 Określa plik WIM, który będzie używany przez skrypt ZTIBackup.wsf. Aby uzyskać więcej informacji o jakie skrypt używa tej właściwości, zobacz [ZTIBackup.wsf](#ZTIBackup.wsf).  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|  
|*BackupDir*|Nazwa pliku Windows Imaging Format (WIM), które mają być użyte podczas kopii.|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] DoCapture=YES BackupShare=\\NYC-AM-FIL-01\Backup$ BackupDir=%OSDComputerName% BackupFile=%OSDComputerName%.wim`|  

####  <a name="BackupShare"></a>BackupShare  
 Folder udostępniony, w którym są przechowywane kopie zapasowe na komputerze docelowym.  

 Poświadczenia używane do dostępu do folderu udostępnionego dla:  

-   LTI są podane w Kreatorze wdrażania poświadczenia.  

-   ZTI są poświadczenia używane przez kont dostępu sieci klienta zaawansowane Menedżera konfiguracji.  

 Uprawnienia wymagane w tym udziale są następujące:  

-   **Komputery domeny**. Zezwalaj na uprawnienie Tworzenie folderów/Dołączanie danych.  

-   **Użytkownicy domeny**. Zezwalaj na uprawnienie Tworzenie folderów/Dołączanie danych.  

-   **Twórca-właściciel**. Zezwalaj na uprawnienia Pełna kontrola.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*UNC_path*|Ścieżka UNC folderu udostępnionego<br /><br /> Uwaga:<br /><br /> Ścieżki UNC określonej w tej właściwości musi istnieć przed wdrożeniem docelowego systemu operacyjnego.|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] DoCapture=YES BackupShare=\\NYC-AM-FIL-01\Backup$ BackupDir=%OSDComputerName% BackupDrive=C:`|  

####  <a name="BDEAllowAlphaNumericPin"></a>BDEAllowAlphaNumericPin  
 Ta właściwość określa, czy numery PIN funkcji BitLocker zawiera wartości alfanumeryczne.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|**TAK**|Znaki alfanumeryczne są dozwolone w numerze PIN.<br /><br /> Uwaga:<br /><br /> Oprócz ustawienie dla tej właściwości **tak**, **Zezwalaj na używanie rozszerzonych numerów PIN przy uruchamianiu** należy włączyć ustawienie zasad grupy.|  
|**BRAK**|Tylko cyfry są dozwolone w numerze PIN.|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] BDEInstallSuppress=NO BDEAllowAlphaNumericPin=YES BDEDriveLetter=S: BDEDriveSize=2000 BDEInstall=TPMKey BDERecoveryKey=AD BDEKeyLocation=C:`|  

####  <a name="BDEDriveLetter"></a>BDEDriveLetter  
 Litera dysku partycji nie zaszyfrowane przez funkcję BitLocker, znanej także jako *wolumin systemowy*. Folderu SYSVOL jest katalog zawierający pliki specyficzne dla sprzętu potrzebne do załadowania komputerów z systemem Windows po systemie BIOS uruchomi się platformy.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|  
|*litera_dysku*|Przypisanie litery dysku logicznego do woluminu systemu (na przykład S lub T). Wartość domyślna to **S**.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] BDEInstallSuppress=NO BDEDriveLetter=S: BDEDriveSize=2000 BDEInstall=TPMKey BDERecoveryKey=AD BDEKeyLocation=C:`|  

####  <a name="BDEDriveSize"></a>BDEDriveSize  
 Rozmiar partycji systemowej funkcji BitLocker. Wartość jest wyrażona w megabajtach. W tym przykładzie rozmiar partycji funkcji BitLocker, aby utworzyć jest prawie 2 GB (2000 MB).  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*drive_size*|Rozmiar partycji w megabajtach; rozmiary domyślne są:<br /><br /> — Windows 7 i Windows Server 2008 R2: 300 MB|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] BDEInstallSuppress=NO BDEDriveLetter=S: BDEDriveSize=2000 BDEInstall=TPMKey BDERecoveryKey=AD BDEKeyLocation=C:`|  

####  <a name="BDEInstall"></a>BDEInstall  
 Typ instalacji funkcji BitLocker do wykonania. Ochrona komputera docelowego przy użyciu jednej z następujących metod:  

-   Mikroukłady modułu TPM  

-   Moduł TPM i klucz uruchomienia zewnętrzne (przy użyciu klucza, który zazwyczaj znajduje się na dysku flash USB [UFD])  

-   Moduł TPM i numer PIN  

-   Klucz uruchomienia zewnętrznych  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|  
|**MODUŁ TPM**|Chroń tylko komputer z modułem TPM. Moduł TPM jest mikroukłady, na którym są przechowywane klucze, hasła i certyfikatów cyfrowych. Mikroukłady zwykle jest integralną częścią płyty głównej.|  
|**TPMKey**|Ochrona komputerów z modułem TPM i klucz uruchomienia. Użyj tej opcji, aby utworzyć klucz uruchomienia i zapisać go na dysku flash USB. Klucz uruchomienia musi być obecny w porcie każdym uruchomieniu komputera.|  
|**TPMPin**|Ochrona komputerów z modułem TPM i numeru pin. Użyj tej opcji w połączeniu z **BDEPin** właściwości.|  
|**Klucz**|Chroń komputer przy użyciu klucza zewnętrzne (klucz odzyskiwania), które mogą być przechowywane w folderze, w usługach AD DS lub wydrukować.|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] BDEInstallSuppress=NO BDEDriveLetter=S: BDEDriveSize=2000 BDEInstall=TPMKey BDERecoveryKey=AD BDEKeyLocation=C:`|  

####  <a name="BDEInstallSuppress"></a>BDEInstallSuppress  
 Wskazuje, czy Proces wdrażania ma pomijać instalacji funkcji BitLocker.  

> [!CAUTION]
>  Wartość tej właściwości należy określić pisane wielkimi literami, aby skrypty wdrażania może go prawidłowo odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|  
|**TAK**|Nie należy próbować zainstalować funkcję BitLocker.|  
|**BRAK**|Próba zainstalowania funkcji BitLocker.|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] BDEInstallSuppress=YES`|  

####  <a name="BDEKeyLocation"></a>BDEKeyLocation  
 Lokalizacja do przechowywania klucza odzyskiwania funkcji BitLocker i klucz uruchomienia.  

> [!NOTE]
>  Jeśli ta właściwość jest skonfigurowana przy użyciu Kreatora wdrażania, właściwość musi być litera dysku wymiennym. Jeśli **SkipBitLocker** właściwość jest ustawiona na **TRUE** , aby **będzie określić konfigurację funkcji BitLocker** stronie kreatora zostanie pominięty, tej właściwości można ustawić na ścieżkę UNC w CustomSettings.ini lub w bazie danych zestawu MDT (MDT bazy danych).  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*Lokalizacja*|Określa, gdzie będzie przechowywany klucz odzyskiwania; musi być ścieżką UNC lub literę dysku wymiennym. Jeśli nie jest ustawiona, pierwszy dostępny dysk wymienny zostanie użyty.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] BDEInstallSuppress=NO BDEDriveLetter=S: BDEDriveSize=2000 BDEInstall=TPMKey BDERecoveryKey=AD BDEKeyLocation=C:`|  

####  <a name="BDEPin"></a>BDEPin  
 Numer PIN, aby podczas konfigurowania funkcji BitLocker można przypisać do komputera docelowego i **BDEInstall** lub **OSDBitLockerMode** właściwości są ustawione na **TPMPin**.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*Numer PIN*|Numer PIN, aby można używać funkcji BitLocker. Numer PIN może mieć wartość od 4 do 20 cyfr.|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] BDEInstallSuppress=NO BDEDriveLetter=S: BDEDriveSize=2000 BDEInstall=TPMPin BDEPin=123456789`|  

####  <a name="BDERecoveryKey"></a>BDERecoveryKey  
 Wartość logiczna wskazująca, czy proces tworzy klucz odzyskiwania funkcji BitLocker. Klucz jest używany do odzyskiwania danych zaszyfrowanych woluminu funkcji BitLocker. Ten klucz jest kryptograficznie odpowiednikiem klucza uruchomienia. Jeśli jest dostępna, klucz odzyskiwania odszyfrowuje klucz główny woluminu (VMK), który z kolei odszyfruje klucz szyfrowania całych woluminów (FVEK).  

> [!NOTE]
>  Klucz odzyskiwania są przechowywane w lokalizacji określonej w **BDEKeyLocation** właściwości.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|**USŁUGI AD**|Klucz odzyskiwania jest tworzony.|  
|Nie określono|Nie utworzono klucz odzyskiwania.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] BDEInstallSuppress=NO BDEDriveLetter=S: BDEDriveSize=2000 BDEInstall=TPMKey BDERecoveryKey=AD BDEKeyLocation=C:`|  

####  <a name="BDEWaitForEncryption"></a>BDEWaitForEncryption  
 Określa, że proces wdrażania nie powinien kontynuować, aż do zakończenia procesu szyfrowania wszystkich dysków w określonej funkcji BitLocker. Określenie wartości TRUE może znacznie zwiększyć czas wymagany do ukończenia procesu wdrażania.  

> [!CAUTION]
>  Wartość tej właściwości należy określić pisane wielkimi literami, aby skrypty wdrażania może go prawidłowo odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|**WARTOŚĆ TRUE**|Określa, że proces wdrażania powinno czekać na ukończenie szyfrowania dysków.|  
|**WARTOŚĆ FALSE**|Określa, że proces wdrażania nie powinno czekać na ukończenie szyfrowania dysków.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] BDEInstallSuppress=NO BDEDriveLetter=S: BDEDriveSize=2000 OSDBitLockerMode=TPMKey OSDBitLockerStartupKeyDrive=C: OSDBitLockerCreateRecoveryPassword=AD BDEWaitForEncryption=TRUE`|  

####  <a name="BitsPerPel"></a>BitsPerPel  
 Ustawienia wyświetlania kolorów na komputerze docelowym. Właściwość może zawierać cyfry i odpowiada ustawieniu jakości koloru. W tym przykładzie **32** wskazuje 32 bity na piksel jakości koloru. Ta wartość jest wstawiany odpowiednie ustawienia konfiguracji w pliku Unattend.xml.  

> [!NOTE]
>  Wartości domyślne (w pliku szablonu Unattend.xml) czy rozdzielczość pozioma 1024 pikseli, rozdzielczość pionowa 768 pikseli, 32-bitowej głębi kolorów i częstotliwość odświeżania pionowego 60 Hz (Hz).  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|  
|*bits_per_pixel*|Liczba bitów na piksel do użycia na potrzeby kolorów. Wartość domyślna to wartość domyślna dla wdrażanego systemu operacyjnego.|  

|**Przykład**|  
|-|    
|`[Settings] Priority=Default  [Default] BitsPerPel=32 VRefresh=60 XResolution=1024 YResolution=768`|  

####  <a name="BuildID"></a>Identyfikatora BuildID  
 Określa sekwencję zadań systemu operacyjnego w celu wdrażania na komputerze docelowym. Identyfikator sekwencji zadań możesz utworzyć w węźle sekwencje zadań w konsoli Deployment Workbench. **Identyfikatora BuildID** właściwość umożliwia znaki alfanumeryczne, łączniki (-) i znaki podkreślenia (\_). **Identyfikatora BuildID** właściwości nie może być pusta ani zawierać spacji.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|  
|*build_id*|Identyfikator sekwencji zadań systemu operacyjnego, zgodnie z definicją w konsoli Deployment Workbench dla docelowego systemu operacyjnego wdrażany<br /><br /> Uwaga:<br /><br /> Należy upewnić się użyć **TaskSequenceID** określony w interfejsie użytkownika (UI) konsoli Deployment Workbench, a nie identyfikator GUID **TaskSequenceID**.|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] BuildID=BareMetal`|  

####  <a name="CapableArchitecture"></a>CapableArchitecture  
 Architektura procesora procesora obsługiwane przez komputer docelowy, a nie bieżący architektury procesora, który jest uruchomiony. Na przykład, gdy uruchomiony system operacyjny 32-bitowych compatible na 64-bitowy procesor, **CapableArchitecture** oznacza, że architektura procesora 64-bitowym.  

 Użyj **architektura** właściwości, aby wyświetlić architektura procesora, które jest aktualnie uruchomione.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|   
|**x86**|Architektura procesora jest 32-bitowych.|  
|**x64**|Architektura procesora jest 64-bitowym.|  

|**Przykład**|  
|-|   
|Brak|  

####  <a name="CaptureGroups"></a>CaptureGroups  
 Określa, czy członkostwo grup lokalnych na komputerze docelowym są przechwytywane. Członkostwo w grupie są przechwytywane w fazie przechwytywania stanu i przywróceniu w fazie przywracania stanu.  

> [!NOTE]
>  Wartość tej właściwości należy określić pisane wielkimi literami, aby skrypty wdrażania może go prawidłowo odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|**BRAK**|Przechwytuje nie informacje o członkostwie w grupie.|  
|**WSZYSTKIE**|Przechwytuje członkostwo wszystkich grup lokalnych na komputerze docelowym.|  
|**TAK**|Przechwytuje członkostwo grup wbudowanych administratora i użytkownicy zaawansowani i grupy na liście właściwości wybranych grup. Jest to wartość domyślna, jeśli wartość jest określona. (**Tak** jest typowe wartości.)|  

|**Przykład**|  
|-|    
|`[Settings] Priority=Default  [Default] DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ CaptureGroups=YES Groups1=NYC Application Management Groups2=NYC Help Desk Users`|  

####  <a name="ChildName"></a>Nazwa ChildName  
 Określa, czy dołączyć Etykieta DNS na początku nazwy istniejącej domeny usługi directory podczas instalowania domeny podrzędnej.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*Nazwa*|Nazwa domeny podrzędnej|  

|**Przykład**|  
|-|    
|`[Settings] Priority=Default  [Default] ChildName=childdom.parentdom.WoodGroveBank.com`|  

####  <a name="ComputerBackupLocation"></a>ComputerBackupLocation  
 Sieciowy folder udostępniony przechowywania kopii zapasowych komputerów. Jeśli folder docelowy nie istnieje, została ona utworzona automatycznie.  

> [!CAUTION]
>  Wartość tej właściwości należy określić pisane wielkimi literami, aby skrypty wdrażania może go prawidłowo odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|  
|*puste*|Taki sam jak **AUTOMATYCZNIE**.|  
|*UNC_path*|Ścieżka UNC do udostępnionego folderu sieciowego przechowywania kopii zapasowej.|  
|**AUTOMATYCZNIE**|Tworzy kopię zapasową na lokalnym dysku twardym, jeśli jest wystarczająca ilość miejsca. W przeciwnym razie kopia zapasowa jest zapisywany do lokalizacji sieciowej, określona w **BackupShare** i **BackupDir** właściwości.|  
|**SIECI**|Tworzy kopię zapasową w lokalizacji sieciowej, określona w **BackupShare** i **BackupDir**.|  
|**BRAK**|Kopia zapasowa nie zostanie wykonane.|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ ComputerBackupLocation=NETWORK BackupShare=\\NYC-AM-FIL-01\Backup$ BackupDir=%OSDComputerName% UDDir=%OSDComputerName% SLShare=\\NYC-AM-FIL-01\Logs$ UDProfiles=Administrator, User-01, ExtranetUser UserDataLocation=NONE`|  

####  <a name="ComputerName"></a>Nazwa_komputera  
 Ta właściwość jest przestarzała. Użyj **OSDComputerName** zamiast tego.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI||  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|Brak|Brak|  

|**Przykład**|  
|-|   
|Brak|  

####  <a name="ConfigFileName"></a>Nazwa_pliku_konfiguracji  
 Określa nazwę pliku konfiguracji, używanego podczas wdrażania przez producenta OEM.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*nazwa_pliku*|Określa nazwę pliku konfiguracji, używanego podczas wdrażania przez producenta OEM|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="ConfigFilePackage"></a>ConfigFilePackage  
 Określa identyfikator pakietu dla pakietu konfiguracji używane podczas wdrażania przez producenta OEM.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|  
|*pakiet*|Określa identyfikator pakietu dla pakietu konfiguracji używane podczas wdrażania przez producenta OEM|  

|**Przykład**|  
|-|   
|Brak|  

####  <a name="ConfirmGC"></a>ConfirmGC  
 Określa, czy replika jest również wykazu globalnego.  

> [!CAUTION]
>  Wartość tej właściwości należy określić pisane wielkimi literami, aby skrypty wdrażania może go prawidłowo odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|**TAK**|Udostępnia repliki wykazu globalnego, jeśli kopia zapasowa została wykazu globalnego.|  
|**BRAK**|Nie powoduje repliki wykazu globalnego.|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] ConfirmGC=YES`|  

####  <a name="CountryCode"></a>CountryCode  
 Kod kraju do skonfigurowania systemu operacyjnego na komputerze docelowym. Ta właściwość umożliwia tylko cyfry. Ta wartość jest wstawiany odpowiednie ustawienia konfiguracji w pliku Unattend.xml.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*country_code*|Kod kraju, w którym ma zostać wdrożona na komputerze docelowym|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] AreaCode=206 CountryCode=001 Dialing=TONE LongDistanceAccess=9`|  

####  <a name="CriticalReplicationOnly"></a>CriticalReplicationOnly  
 Określa, czy operacja podwyższania poziomu powoduje wykonanie tylko replikacji krytycznej, a następnie jest kontynuowana, pomijanie niekrytyczne (i potencjalnie długie) część replikacji.  

> [!CAUTION]
>  Wartość tej właściwości należy określić pisane wielkimi literami, aby skrypty wdrażania może go prawidłowo odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|**TAK**|Replikacja niekrytyczna jest wykonywana pomija|  
|**BRAK**|Replikacja niekrytyczna jest wykonywana nie pominąć|  

|**Przykład**|  
|-|    
|`[Settings] Priority=Default  [Default] CriticalReplicationOnly=YES`|  

####  <a name="CustomDriverSelectionProfile"></a>CustomDriverSelectionProfile  
 Niestandardowy wybór określa profil używany podczas instalacji sterownika.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|  
|*Profil*|Profil niestandardowy wybór używany podczas instalacji sterownika|  

|**Przykład**|  
|-|    
|`[Settings] Priority=Default  [Default] CustomDriverSelectionProfile=CustomDrivers`|  

####  <a name="CustomPackageSelectionProfile"></a>CustomPackageSelectionProfile  
 Niestandardowy wybór określa profil używany podczas instalowania pakietu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*Profil*|Profil niestandardowy wybór używany podczas instalacji pakietu aktualizacji|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] CustomPackageSelectionProfile=CustomPackages`|  

####  <a name="CustomWizardSelectionProfile"></a>CustomWizardSelectionProfile  
 Określa profil niestandardowy wybór wykorzystywane przez kreatora w celu filtrowania wyświetlanie różne elementy.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|  
|*Profil*|Profil niestandardowy wybór przez kreatora w celu filtrowania wyświetlania różnych elementów|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] CustomWizardSelectionProfile=CustomWizard`|  

####  <a name="Database"></a>Bazy danych  
 Właściwość, która określa bazę danych do użycia na potrzeby zapytań o wartości właściwości z kolumn w tabeli określonej w **tabeli** właściwości. Baza danych znajduje się na komputerze określonym w **SQLServer** właściwości. Wystąpienie Microsoft SQL Server® na komputerze jest określona w **wystąpienia** właściwości.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|\-||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*bazy danych*|Nazwa bazy danych do użycia na potrzeby zapytań o wartości właściwości|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Computers, Default  [Default] OSInstall=YES  [Computers] SQLServer=NYC-SQL-01 SQLShare=SQL$ Database=MDTDB Instance=SQLEnterprise2005 Table=Computers Parameters=SerialNumber, AssetTag ParameterCondition=OR`|  

####  <a name="DatabasePath"></a>DatabasePath  
 Określa w pełni kwalifikowanej z systemem innym niż\-ścieżkę UNC do katalogu na dysku stałym komputera docelowego, który zawiera bazę danych domeny.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*Ścieżka*|Określa w pełni kwalifikowanej z systemem innym niż\-ścieżkę UNC do katalogu na dysku stałym komputera lokalnego, który zawiera bazę danych domeny|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] DatabasePath=%DestinationLogicalDrive%\Windows\NTSD`|  

####  <a name="DBID"></a>DBID  
 Określa konto użytkownika używane do łączenia się z komputerem z uruchomionym programem SQL Server \(określonego przez **SQLServer** właściwości\) przy użyciu uwierzytelniania programu SQL Server. **DBPwd** właściwość udostępnia hasło dla konta użytkownika w **DBID** właściwości.  

> [!NOTE]
>  Uwierzytelnianie programu SQL Server nie jest należycie zabezpieczone zintegrowanego uwierzytelniania systemu Windows. Zintegrowane uwierzytelnianie systemu Windows jest zalecaną metodą uwierzytelniania. Przy użyciu **DBID** i **DBPwd** właściwości przechowuje poświadczenia w postaci zwykłego tekstu w pliku CustomSettings.ini i dlatego nie jest bezpieczna. Aby uzyskać więcej informacji na temat używania zintegrowanego uwierzytelniania systemu Windows, zobacz [SQLShare](#SQLShare) właściwości.  

> [!NOTE]
>  Ta właściwość jest można skonfigurować tylko przez ręcznego edytowania plików CustomSettings.ini i BootStrap.ini.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|\-||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*Użytkownik\_id*|Nazwa poświadczenia konta użytkownika, które są używane do dostępu do komputera z uruchomionym programem SQL Server przy użyciu uwierzytelniania programu SQL Server|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Computers, Default  [Default] OSInstall=YES  [Computers] SQLServer=NYC-SQL-01 DBID=SQL_User-01 DBPwd=<complex_password> NetLib=DBNMPNTW Database=MDTDB Instance=SQLEnterprise2005 Table=Computers Parameters=SerialNumber, AssetTag ParameterCondition=OR`|  

####  <a name="DBPwd"></a>DBPwd  
 Określa hasło dla konta użytkownika określonego w **DBID** właściwości. **DBID** i **DBPwd** właściwości Podaj poświadczenia dla uwierzytelniania programu SQL Server do komputera z programem SQL Server \(określonego przez **SQLServer**  właściwości\).  

> [!NOTE]
>  Uwierzytelnianie programu SQL Server nie jest należycie zabezpieczone zintegrowanego uwierzytelniania systemu Windows. Zintegrowane uwierzytelnianie systemu Windows jest zalecaną metodą uwierzytelniania. Przy użyciu **DBID** i **DBPwd** właściwości przechowuje poświadczenia w postaci zwykłego tekstu w pliku CustomSettings.ini i dlatego nie jest bezpieczna. Aby uzyskać więcej informacji na temat używania zintegrowanego uwierzytelniania systemu Windows, zobacz [SQLShare](#SQLShare) właściwości.  

> [!NOTE]
>  Ta właściwość jest można skonfigurować tylko przez ręcznego edytowania plików CustomSettings.ini i BootStrap.ini.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|\-||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*Użytkownik\_hasła*|Hasło dla poświadczeń konta użytkownika określonego w **DBID** właściwość przy użyciu uwierzytelniania programu SQL Server|  

|**Przykład**|  
|-|    
|`[Settings] Priority=Computers, Default  [Default] OSInstall=YES  [Computers] SQLServer=NYC-SQL-01 DBID=SQL_User-01 DBPwd=<complex_password> NetLib=DBNMPNTW Database=MDTDB Instance=SQLEnterprise2005 Table=Computers Parameters=SerialNumber, AssetTag ParameterCondition=OR`|  

####  <a name="Debug"></a>Debugowania  
 Określa poziom szczegółowości komunikatów zapisanych w plikach dziennika zestawu MDT. Tej właściwości można skonfigurować w celu pomocy przy rozwiązywaniu problemów z wdrożeniami zapewniając rozszerzonych informacji na temat procesu wdrażania zestawu MDT.  

 Tę właściwość można ustawić przez uruchomienie skryptu LiteTouch.vbs  **\/debug: true** polecenia\-wiersz parametru w następujący sposób:  

```  
cscript.exe LiteTouch.vbs /debug:true  
```  

 Po uruchomieniu skryptu LiteTouch.vbs **debugowania** ma ustawioną wartość właściwości **TRUE**, oraz inne skrypty są automatycznie odczytywać wartości tej właściwości i pełne informacje.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub w bazie danych zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|**WARTOŚĆ TRUE**|Debugowanie rejestrowanie jest włączone, która obejmuje następujące elementy:<br /><br /> \-Pełne komunikaty są rejestrowane.<br /><br /> \-Przestarzałe komunikaty są rejestrowane jako błędy.|  
|**WARTOŚĆ FALSE**|Debugowanie nie włączono rejestrowania. Jest to wartość domyślna.|  

|**Przykład**|  
|-|   
|Brak|  

####  <a name="DefaultGateway"></a>Brama_domyślna  
 Adres IP bramy domyślne używane przez komputer docelowy. Format adresu IP zwrócona przez właściwość jest standardowy kropkami\-notacji dziesiętnej, na przykład 192.168.1.1. Umożliwia utworzenie podsekcji, który zawiera ustawienia przeznaczone dla grupy komputerów, na podstawie podsieci IP, na których znajdują się w tej właściwości.  

> [!NOTE]
>  Tej właściwości ustawiono dynamicznie przez zestaw MDT skrypty i nie może mieć jego wartość ustawiona w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu. Jednak służy tej właściwości w CustomSettings.ini lub zestaw MDT bazy danych, jak pokazano w poniższych przykładach ułatwiających definiując konfigurację komputera docelowego.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*domyślne\_bramy*|Adres IP bramy domyślnej w standardowy kropkami\-notacji dziesiętnej|  

|**Przykład**|  
|-|   
|`[Settings] Priority=DefaultGateway, Default  [Default] OSInstall=YES  [DefaultGateway] 192.168.0.1=HOUSTON 11.1.1.11=REDMOND 172.28.20.1=REDMOND  [REDMOND] Packages001=XXX00004:Program4 Packages002=XXX00005:Program5  [HOUSTON] Packages001=XXX00006:Program6 Packages002=XXX00007:Program7 Packages003=XXX00008:Program8`|  

####  <a name="DeployDrive"></a>DeployDrive  
 Tworzy wartość używana przez skrypty do dostępu do plików i uruchamianie programów udziału wdrożenia w konsoli Deployment Workbench. Właściwość zwraca zamapowane na literę dysku **DeployRoot** właściwości. Używa ZTIApplications.wsf **DeployDrive** właściwości podczas uruchamiania polecenia\-wiersz programy z rozszerzeniem cmd i bat.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*dysk\_list*|Przypisanie litery dysku logicznego, gdzie docelowy system operacyjny ma zostać zainstalowany \(takich jak C lub D\)|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="DeploymentMethod"></a>DeploymentMethod  
 Metoda używana do wdrażania (UNC, nośników lub programu Configuration Manager).  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

> [!CAUTION]
>  Wartość tej właściwości należy określić pisane wielkimi literami, aby skrypty wdrażania może go prawidłowo odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|  
|**UNC**|Wdrożenie się z komputerem docelowym za pośrednictwem sieci.|  
|**Nośnik**|Wdrożenie jest nawiązywane z nośnika lokalnego (np. dysku DVD lub dysku twardego) na komputerze docelowym.|  
|**SCCM**|ZTI używa tej metody dla programu Configuration Manager.|  

|**Przykład**|  
|-|   
|Brak|  

####  <a name="DeploymentType"></a>DeploymentType  
 Typ wdrożenia, wykonywane są oparte na scenariusz wdrażania. ZTI ta właściwość jest ustawiania dynamicznie przez zestaw MDT skrypty i nie jest skonfigurowany w CustomSettings.ini. Dla LTI można pominąć strony w Kreatorze wdrażania, na którym zostanie wybrany typ wdrożenia. Ponadto można określić typu wdrożenia przez przekazanie wartości wymienione poniżej do skryptu LiteTouch.wsf jako opcji wiersza polecenia.  

> [!CAUTION]
>  Wartość tej właściwości należy określić pisane wielkimi literami, aby skrypty wdrażania może go prawidłowo odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|**NEWCOMPUTER**|Komputer docelowy jest nowy komputer, który nigdy nie było członkiem sieci.|  
|**ODŚWIEŻ**|Komputer docelowy jest istniejącym komputerem w sieci, który wymaga ponownego wdrożenia standardowego środowiska pulpitu.|  
|**ZAMIEŃ**|Istniejący komputer w sieci jest zastępowany na nowym komputerze. Dane migracji stanu użytkownika jest przenoszona z istniejącego komputera na nowy komputer.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] DeploymentType=NEWCOMPUTER`|  

####  <a name="DeployRoot"></a>DeployRoot  
 Określa UNC lub ścieżka lokalna do folderu, który jest elementem głównym struktury folderów, która używa zestawu MDT. Ta struktura folder zawiera pliki konfiguracji, skryptów i innych folderów i plików, które korzysta z zestawu MDT. Wartość tej właściwości ustawiono na podstawie następujących technologii wdrożenia zestawu MDT:  

-   **LTI**. Ta właściwość jest ścieżką UNC do udziału wdrożenia, która tworzy konsoli Deployment Workbench. Ta właściwość służy do Wybierz udział w określonym wdrożeniu. Najczęściej tej właściwości jest w pliku BootStrap.ini, aby zidentyfikować udziału wdrożenia, zanim zostanie nawiązane połączenie, udziałem wdrożenia. Wszystkie inne foldery udziału wdrożenia są względem tej właściwości (takie jak sterowniki urządzeń, pakiety językowe lub systemów operacyjnych).  

-   **ZTI**. Ta właściwość jest ścieżka lokalna do folderu, do którego jest kopiowany pakietu plików zestawu MDT. **Użyj pakietu Toolkit** krok sekwencji zadań kopiuje pakiet plików zestawu MDT do folderu lokalnego na komputerze docelowym, a następnie automatycznie ustawia tę właściwość do folderu lokalnego.  

    > [!NOTE]
    >  ZTI ta właściwość jest dynamicznie ustawiania przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub w bazie danych zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*Ścieżka*|Nazwa UNC lub ścieżka lokalna do.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] DeployRoot=\\NYC-AM-FIL-01\Distribution$ UserDataLocation=NONE`|  

####  <a name="DestinationDisk"></a>DestinationDisk  
 Numer dysku, który zostanie wdrożony obraz.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI||  

|**Wartość**|**Opis**|  
|-|-|  
|*disk_number*|Liczba dysków, do której zostanie wdrożony obrazu|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] DestinationDisk=0`|  

####  <a name="DestinationLogicalDrive"></a>DestinationLogicalDrive  
 Dysk logiczny, do której zostanie wdrożony obrazu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI||  

|**Wartość**|**Opis**|  
|-|-|   
|*logical_drive_number*|Dysk logiczny, do której zostanie wdrożony obrazu|  

|**Przykład 1**|  
|-|   
|`[Settings] Priority=Default  [Default] DestinationLogicalDrive=0`|  

|**Przykład 2**|  
|-|  
|`[Settings] Priority=Default  [Default] DestinationLogicalDrive=0`<br /><br /> `[Settings] Priority=Default  [Default] InstallDNS=YES DomainNetBIOSName=WoodGroveBank NewDomain=Child DomainLevel=3 ForestLevel=3 NewDomainDNSName=newdom.WoodGroveBank.com ParentDomainDNSName=WoodGroveBank.com AutoConfigDNS=YES ConfirmGC=YES CriticalReplicationOnly=NO ADDSUserName=Administrator ADDSUserDomain=WoodGroveBank ADDSPassword=<complex_password> DatabasePath=%DestinationLogicalDrive%\Windows\NTDS ADDSLogPath=%DestinationLogicalDrive%\Windows\NTDS SysVolPath=%DestinationLogicalDrive%\Windows\SYSVOL SafeModeAdminPassword=<complex_password>`|  

####  <a name="DestinationPartition"></a>DestinationPartition  
 Partycja dysku, do której zostanie wdrożony obrazu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI||  

|**Wartość**|**Opis**|  
|-|-|  
|*partition_number*|Liczba partycji, do której zostanie wdrożony obrazu|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] DestinationPartition=1`|  

####  <a name="DHCPScopes"></a>DHCPScopes  
 Określa liczbę zakresów DHCP, aby skonfigurować.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|   
|*zakresy*|Określa liczbę zakresów DHCP, aby skonfigurować|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] DHCPScopes=1`|  

####  <a name="DHCPScopesxDescription"></a>DHCPScopesxDescription  
 Opis zakresu DHCP.  

> [!NOTE]
>  *x* w tej właściwości name jest symbolem zastępczym tablicę wartości nieujemnych zawierającą konfiguracji DHCP.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|  
|*Opis elementu*|Opis zakresu DHCP|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] DHCPScopes0Description=DHCPScope0`|  

####  <a name="DHCPScopesxEndIP"></a>DHCPScopesxEndIP  
 Określa końcowy adres IP zakresu DHCP.  

 *x* w tej właściwości name jest symbolem zastępczym tablicę wartości nieujemnych zawierającą konfiguracji DHCP.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*end_IP*|Określa końcowy adres IP zakresu DHCP|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] DHCPScopes0EndIP=192.168.0.30`|  

####  <a name="DHCPScopesxExcludeEndIP"></a>DHCPScopesxExcludeEndIP  
 Określa końcowy adres IP do wykluczenia zakresu DHCP. Adresy IP, które są wykluczone z zakresu nie są oferowane przez serwer DHCP klientom uzyskanie dzierżawy z tego zakresu.  

> [!NOTE]
>  *x* w tej właściwości name jest symbolem zastępczym tablicę wartości nieujemnych zawierającą konfiguracji DHCP.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|   
|*exclude_end_IP*|Określa końcowy adres IP do wykluczenia zakresu DHCP|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] DHCPScopes0ExcludeEndIP=192.168.0.15`|  

####  <a name="DHCPScopesxExcludeStartIP"></a>DHCPScopesxExcludeStartIP  
 Określa początkowy adres IP do wykluczenia zakresu DHCP. Adresy IP, które są wykluczone z zakresu nie są oferowane przez serwer DHCP klientom uzyskanie dzierżawy z tego zakresu.  

> [!NOTE]
>  *x* w tej właściwości name jest symbolem zastępczym tablicę wartości nieujemnych zawierającą konfiguracji DHCP.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*exclude_start_IP*|Określa początkowy adres IP do wykluczenia zakresu DHCP|  

|**Przykład**|  
|-|    
|`[Settings] Priority=Default  [Default] DHCPScopes0ExcludeStartIP=192.168.0.10`|  

####  <a name="DHCPScopesxIP"></a>DHCPScopesxIP  
 Określa podsieci IP, zakresu.  

 *x* w tej właściwości name jest symbolem zastępczym tablicę wartości nieujemnych zawierającą konfiguracji DHCP.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*IP*|Określa podsieci IP, zakresu|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] DHCPScopes0IP=192.168.0.0`|  

####  <a name="DHCPScopesxName"></a>DHCPScopesxName  
 Definiowane przez użytkownika nazwa ma zostać przypisany do zakresu.  

 *x* w tej właściwości name jest symbolem zastępczym tablicę wartości nieujemnych zawierającą konfiguracji DHCP.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|  
|*Nazwa*|Definiowane przez użytkownika nazwa ma zostać przypisany do zakresu|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] DHCPScopes0Name=DHCPScope0`|  

####  <a name="DHCPScopesxOptionDNSDomainName"></a>DHCPScopesxOptionDNSDomainName  
 Określa nazwę domeny, która powinna być używana przez klientów DHCP podczas rozpoznawania nazw niekwalifikowanych domeny z serwera DNS.  

> [!NOTE]
>  *x* w tej właściwości name jest symbolem zastępczym tablicę wartości nieujemnych zawierającą konfiguracji DHCP.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|  
|*DNS_domain_name*|Określa nazwę domeny, która powinna być używana przez klientów DHCP podczas rozpoznawania nazw niekwalifikowanych domeny z serwera DNS|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] DHCPScopes0OptionDNSDomainName=WoodGroveBank.com`|  

####  <a name="DHCPScopesxOptionDNSServer"></a>DHCPScopesxOptionDNSServer  
 Określa listę adresów IP serwerów nazw DNS dostępnych dla klienta. Jeśli przypisany jest więcej niż jeden serwer, klient interpretuje i używa adresów w określonej kolejności.  

> [!NOTE]
>  *x* w tej właściwości name jest symbolem zastępczym tablicę wartości nieujemnych zawierającą konfiguracji DHCP.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*DNS_server*|Określa listę adresów IP serwerów nazw DNS dostępnych dla klienta|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] DHCPScopes0OptionDNSServer=192.168.0.2`|  

####  <a name="DHCPScopesxOptionLease"></a>DHCPScopesxOptionLease  
 Czas trwania dzierżawy DHCP jest prawidłowy dla klienta.  

> [!NOTE]
>  *x* w tej właściwości name jest symbolem zastępczym tablicę wartości nieujemnych zawierającą konfiguracji DHCP.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|  
|*dzierżawy*|Czas trwania dzierżawy DHCP jest prawidłowy dla klienta|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] DHCPScopes0OptionLease=7`|  

####  <a name="DHCPScopesxOptionNBTNodeType"></a>DHCPScopesxOptionNBTNodeType  
 Określa typ węzła klienta dla klientów NetBT.  

> [!NOTE]
>  *x* w tej właściwości name jest symbolem zastępczym tablicę wartości nieujemnych zawierającą konfiguracji DHCP.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|**1**|Konfiguruje typu węzeł jako węzeł b|  
|**2**|Konfiguruje typu węzeł jako węzeł p|  
|**4**|Konfiguruje typu węzeł jako węzeł m|  
|**8**|Konfiguruje typu węzeł jako węzeł h|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] DHCPScopes0OptionNBTNodeType=4`|  

####  <a name="DHCPScopesxOptionPXEClient"></a>DHCPScopesxOptionPXEClient  
 Określa adres IP używany dla kodu inicjowania klienta środowiska PXE.  

> [!NOTE]
>  *x* w tej właściwości name jest symbolem zastępczym tablicę wartości nieujemnych zawierającą konfiguracji DHCP.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|   
|*PXE_client*|Określa adres IP używany dla kodu inicjowania klienta środowiska PXE|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] DHCPScopes0OptionPXEClient=192.168.0.252`|  

####  <a name="DHCPScopesxOptionRouter"></a>DHCPScopesxOptionRouter  
 Określa listę adresów IP routerów w podsieci klienta. Gdy router więcej niż jeden jest przypisany, klient interpretuje i używa adresów w określonej kolejności. Ta opcja jest zwykle używana do przypisywania klientów DHCP w podsieci bramy domyślnej.  

> [!NOTE]
>  *x* w tej właściwości name jest symbolem zastępczym tablicę wartości nieujemnych zawierającą konfiguracji DHCP.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*router*|Określa listę adresów IP routerów w podsieci klienta|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] DHCPScopes0OptionRouter=192.168.0.253`|  

####  <a name="DHCPScopesxOptionWINSServer"></a>DHCPScopesxOptionWINSServer  
 Określa adresy IP do użycia dla NBNSes w sieci.  

> [!NOTE]
>  *x* w tej właściwości name jest symbolem zastępczym tablicę wartości nieujemnych zawierającą konfiguracji DHCP  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|  
|*WINS_server*|Określa adresy IP do użycia dla NBNSes w sieci|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] DHCPScopes0OptionWINSServer=192.168.0.2`|  

####  <a name="DHCPScopesxStartIP"></a>DHCPScopesxStartIP  
 Początkowy adres IP zakresu adresów IP, które mają być uwzględniane w zakresie.  

> [!NOTE]
>  *x* w tej właściwości name jest symbolem zastępczym tablicę wartości nieujemnych zawierającą konfiguracji DHCP.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|  
|*start_IP*|Początkowy adres IP dla zakresu adresów IP, które mają być wykluczone z zakresu|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] DHCPScopes0StartIP=192.168.0.20`|  

####  <a name="DHCPScopesxSubnetMask"></a>DHCPScopesxSubnetMask  
 Określa maskę podsieci klienta.  

> [!NOTE]
>  *x* w tej właściwości name jest symbolem zastępczym tablicę wartości nieujemnych zawierającą konfiguracji DHCP.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|  
|*subnet_mask*|Określa maskę podsieci podsieci IP klienta|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] DHCPScopes0SubnetMask=255.255.255.0`|  

####  <a name="DHCPServerOptionDNSDomainName"></a>DHCPServerOptionDNSDomainName  
 Określa sufiks domeny DNS konkretnego połączenia komputerów klienckich.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|    
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|   
|*DNS_domain_name*|Określa sufiks domeny DNS konkretnego połączenia klientów|  

|**Przykład**|  
|-|    
|`[Settings] Priority=Default  [Default] DHCPServerOptionDNSDomainName=Fabrikam.com`|  

####  <a name="DHCPServerOptionDNSServer"></a>DHCPServerOptionDNSServer  
 Określa listę adresów IP, które mają być używane jako serwery nazw DNS, które są dostępne dla klienta.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*DNS_server*|Określa listę adresów IP, które mają być używane jako serwery nazw DNS, które są dostępne dla klienta|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] DHCPServerOptionDNSServer=192.168.0.1,192.168.0.2`|  

####  <a name="DHCPServerOptionNBTNodeType"></a>DHCPServerOptionNBTNodeType  
 Określa typ węzła klienta dla klientów NetBT.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|   
|**1**|Konfiguruje typu węzeł jako węzeł b|  
|**2**|Konfiguruje typu węzeł jako węzeł p|  
|**4**|Konfiguruje typu węzeł jako węzeł m|  
|**8**|Konfiguruje typu węzeł jako węzeł h|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] DHCPServerOptionNBTNodeType=4`|  

####  <a name="DHCPServerOptionPXEClient"></a>DHCPServerOptionPXEClient  
 Określa adres IP używany dla kodu inicjowania klienta środowiska PXE.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*PXE_client*|Określa adres IP używany dla kodu inicjowania klienta środowiska PXE|  

|**Przykład**|  
|-|    
|`[Settings] Priority=Default  [Default] DHCPServerOptionPXEClient=192.168.0.252`|  

####  <a name="DHCPServerOptionRouter"></a>DHCPServerOptionRouter  
 Określa listę adresów IP routerów w podsieci klienta. Gdy router więcej niż jeden jest przypisany, klient interpretuje i używa adresów w określonej kolejności. Ta opcja jest zwykle używana do przypisywania klientów DHCP w podsieci bramy domyślnej.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|  
|*router*|Określa listę adresów IP routerów w podsieci klienta|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] DHCPServerOptionRouter=192.168.0.253`|  

####  <a name="DHCPServerOptionWINSServer"></a>DHCPServerOptionWINSServer  
 Określa adresy IP do użycia dla NBNSes w sieci.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|    
|*WINS_server*|Określa adresy IP do użycia dla NBNSes w sieci|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] DHCPServerOptionWINSServer=192.168.0.2`|  

####  <a name="Dialing"></a>Wybieranie numeru  
 Typ wybierania obsługiwane przez infrastrukturę sieci telefonicznej, w którym znajduje się na komputerze docelowym. Ta wartość jest wstawiany odpowiednie ustawienia konfiguracji w pliku Unattend.xml.  

> [!CAUTION]
>  Wartość tej właściwości należy określić pisane wielkimi literami, aby skrypty wdrażania może go prawidłowo odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|  
|**PULS**|Infrastruktura telefonii obsługuje impulsowe wybieranie numeru.|  
|**TON KOMUNIKATU**|Infrastruktura telefonii obsługuje impulsowe wybieranie numerów.|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] AreaCode=206 CountryCode=001 Dialing=TONE LongDistanceAccess=9`|  

####  <a name="DisableTaskMgr"></a>DisableTaskMgr  
 Ta właściwość kontroluje zdolność użytkownika, aby uruchomić Menedżera zadań, naciskając klawisze CTRL + ALT + DEL. Po uruchomieniu Menedżera zadań użytkownik może przerwać LTI sekwencji zadań podczas uruchamiania w nowym systemie operacyjnym na komputerze docelowym. Ta właściwość jest używana w połączeniu z **HideShell** właściwości i jest prawidłowa tylko gdy **HideShell** właściwość jest ustawiona na **tak**.  

> [!NOTE]
>  Ta właściwość i **HideShell** właściwości musi być ustawione na **tak** aby uniemożliwić użytkownikowi naciśnięcie klawisza CTRL + ALT + DEL i przerywania LTI sekwencji zadań.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|   
|**TAK**|Uniemożliwić użytkownika można uruchomić Menedżera zadań, naciskając klawisze CTRL + ALT + DEL, a następnie przerywania LTI sekwencji zadań.|  
|**BRAK**|Zezwalaj użytkownikowi na uruchamianie Menedżera zadań, naciskając klawisze CTRL + ALT + DEL, a następnie przerwań LTI sekwencji zadań. Jest to wartość domyślna.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] DisableTaskMgr=YES HideShell=YES`|  

####  <a name="DNSServerOptionBINDSecondaries"></a>DNSServerOptionBINDSecondaries  
 Określa, czy ma być używany format szybkiego transferu transferu strefy do serwerów DNS uruchomionych starsze implementacje wiązania.  

 Domyślnie wszystkie serwery DNS z systemem Windows używają formatu szybkiego transferu stref. Ten format używa kompresji i może zawierać wiele rekordów w wiadomości TCP podczas operacji transferu. Ten format jest także zgodny z nowszą serwerów DNS na podstawie powiązania, które wersją 4.9.4 lub nowszy.  

> [!CAUTION]
>  Wartość tej właściwości należy określić pisane wielkimi literami, aby skrypty wdrażania może go prawidłowo odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|   
|**WARTOŚĆ TRUE**|Umożliwia POWIĄŻ pomocnicze|  
|**WARTOŚĆ FALSE**|Nie zezwala na POWIĄŻ pomocnicze|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] DNSServerOptionBINDSecondaries=TRUE`|  

####  <a name="DNSServerOptionDisableRecursion"></a>DNSServerOptionDisableRecursion  
 Określa, czy serwer DNS używa rekursji. Domyślnie usługa serwera DNS jest włączona rekursję.  

> [!CAUTION]
>  Wartość tej właściwości należy określić pisane wielkimi literami, aby skrypty wdrażania może go prawidłowo odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|    
|**WARTOŚĆ TRUE**|Wyłącza rekursję na serwerze DNS|  
|**WARTOŚĆ FALSE**|Włącza rekursji na serwerze DNS|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] DNSServerOptionDisableRecursion=TRUE`|  

####  <a name="DNSServerOptionEnableNetmaskOrdering"></a>DNSServerOptionEnableNetmaskOrdering  
 Określa, czy serwer DNS zmienia kolejność rekordów zasobów adresu (A) w ramach tego samego rekordu zasobu, który jest ustawiony w odpowiedzi serwera na kwerendy na podstawie adresu IP źródła zapytania.  

 Domyślnie usługa serwera DNS używa priorytetu podsieci lokalnej zmiany kolejności z rekordów zasobów.  

> [!CAUTION]
>  Wartość tej właściwości należy określić pisane wielkimi literami, aby skrypty wdrażania może go prawidłowo odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|  
|**WARTOŚĆ TRUE**|Umożliwia porządkowanie|  
|**WARTOŚĆ FALSE**|Wyłącza porządkowanie|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] DNSServerOptionEnableNetmaskOrdering=TRUE`|  

####  <a name="DNSServerOptionEnableRoundRobin"></a>DNSServerOptionEnableRoundRobin  
 Określa, czy serwer DNS używa mechanizmu okrężnego obracanie i zmienić kolejność listy rekordów zasobów, jeśli istnieje wiele rekordów zasobów tego samego typu, który istnieje dla odpowiedzi na kwerendę.  

 Domyślnie usługa serwera DNS używa okrężnego.  

> [!CAUTION]
>  Wartość tej właściwości należy określić pisane wielkimi literami, aby skrypty wdrażania może go prawidłowo odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|  
|**WARTOŚĆ TRUE**|Włącza działanie okrężne|  
|**WARTOŚĆ FALSE**|Wyłącza okrężnego|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] DNSServerOptionEnableRoundRobin=TRUE`|  

####  <a name="DNSServerOptionEnableSecureCache"></a>DNSServerOptionEnableSecureCache  
 Określa, czy serwer DNS próbuje wyczyścić odpowiedzi, aby uniknąć zanieczyszczenie pamięci podręcznej. To ustawienie jest domyślnie włączone. Domyślnie serwery DNS, użyj opcji bezpiecznej odpowiedzi, która eliminuje dodawanie niepowiązanych rekordów zasobów zawartych w odpowiedź z odwołaniem do pamięci podręcznej. W większości przypadków wszystkie nazwy, które są dodawane do odpowiedzi są buforowane i pomagają przyspieszyć rozpoznawanie kolejne zapytania DNS.  

 Jednak za pomocą tej funkcji, serwer może ustalić, że określonej nazwy są zbędne lub niezabezpieczone, a następnie je odrzucić. Serwer określa, czy w pamięci podręcznej nazwę, która jest oferowany odwołań na podstawie tego, czy jest ona częścią dokładne, powiązane, domeny drzewa nazw DNS dla którego utworzono oryginalną nazwę, którego dotyczy kwerenda.  

> [!CAUTION]
>  Wartość tej właściwości należy określić pisane wielkimi literami, aby skrypty wdrażania może go prawidłowo odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|   
|**WARTOŚĆ TRUE**|Włącza buforowanie zabezpieczeń|  
|**WARTOŚĆ FALSE**|Wyłącza buforowanie zabezpieczeń|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] DNSServerOptionEnableSecureCache=TRUE`|  

####  <a name="DNSServerOptionFailOnLoad"></a>DNSServerOptionFailOnLoad  
 Określa, czy ładowanie strefy powinna zakończyć się niepowodzeniem, jeśli znaleziono nieprawidłowe dane.  

> [!CAUTION]
>  Wartość tej właściwości należy określić pisane wielkimi literami, aby skrypty wdrażania może go prawidłowo odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|    
|**WARTOŚĆ TRUE**|Włącz błąd przy ładowaniu|  
|**WARTOŚĆ FALSE**|Wyłącz błąd przy ładowaniu|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] DNSServerOptionFailOnLoad=TRUE`|  

####  <a name="DNSServerOptionNameCheckFlag"></a>DNSServerOptionNameCheckFlag  
 Określa standard znaków, które są używane podczas sprawdzania dostępności nazwy DNS.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|  
|**0**|Używa znaków ANSI, które są zgodne z żądaniem Internet Engineering Task Force (IETF) for Comments (RFC). Ta wartość odpowiada **ścisłe RFC (ANSI)** zaznaczenia w przypadku konfigurowania DNS w konsoli Deployment Workbench.|  
|**1**|Używa znaków ANSI, które nie są zawsze zgodne z RFC organizacji IETF. Ta wartość odpowiada **nie RFC (ANSI)** zaznaczenia w przypadku konfigurowania DNS w konsoli Deployment Workbench.|  
|**2**|Używa znaków wielobajtowych UCS Transformation Format 8 (UTF-8). To jest ustawienie domyślne. Ta wartość odpowiada **Wielobajtowe (UTF-8)** zaznaczenia w przypadku konfigurowania DNS w konsoli Deployment Workbench.|  
|**3**|Używa wszystkich znaków. Ta wartość odpowiada **wszystkie nazwy** zaznaczenia w przypadku konfigurowania DNS w konsoli Deployment Workbench.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] DNSServerOptionNameCheckFlag=2`|  

####  <a name="DNSZones"></a>DNSZones  
 Określa liczbę stref DNS, aby skonfigurować.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|  
|*strefy*|Określa liczbę stref DNS, aby skonfigurować|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] DNSZones=1 DNSZones0Name=MyNewZone DNSZones0DirectoryPartition=Forest DNSZones0FileName=MyNewZone.dns DNSZones0MasterIP=192.168.0.1,192.168.0.2 DNSZones0Type=Secondary`|  

####  <a name="DNSZonesxDirectoryPartition"></a>DNSZonesxDirectoryPartition  
 Określa partycji katalogu do przechowywania strefy podczas konfigurowania dodatkowej lub stref skrótowych.  

> [!NOTE]
>  *x* w tej właściwości name jest symbolem zastępczym tablicę wartości nieujemnych zawierającą konfiguracji DNS.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|**Domeny**|Dane strefy są replikowane do wszystkich serwerów DNS w domenie usług AD DS|  
|**Lasu**|Dane strefy są replikowane do wszystkich serwerów DNS w lesie usługi AD DS|  
|**Starsza wersja**|Dane strefy są replikowane do wszystkich kontrolerów domeny w domenie usług AD DS|  

|**Przykład**|  
|-|
|`[Settings] Priority=Default  [Default] DNSZones0DirectoryPartition=Forest`|  

####  <a name="DNSZonesxFileName"></a>DNSZonesxFileName  
 Określa nazwę pliku, w którym będą przechowywane informacje o strefie.  

> [!NOTE]
>  *x* w tej właściwości name jest symbolem zastępczym tablicę wartości nieujemnych zawierającą konfiguracji DNS.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*nazwa_pliku*|Określa nazwę pliku, w którym będą przechowywane informacje o strefie|  

|**Przykład**|  
|-|
|`[Settings] Priority=Default  [Default] DNSZones0FileName=MyNewZone.dns`|  

####  <a name="DNSZonesxMasterIP"></a>DNSZonesxMasterIP  
 Rozdzielana przecinkami lista adresów IP serwerów głównych, który będzie używany przez serwer DNS, podczas aktualizowania określonej strefy pomocnicze. Ta właściwość musi być określone podczas konfigurowania dodatkowej lub skrótową strefy DNS.  

> [!NOTE]
>  *x* w tej właściwości name jest symbolem zastępczym tablicę wartości nieujemnych zawierającą konfiguracji DNS.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*IP1, IP2*|Rozdzielana przecinkami lista adresów IP serwerów głównych|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] DNSZones0MasterIP=192.168.0.1,192.168.0.2`|  

####  <a name="DNSZonesxName"></a>DNSZonesxName  
 Określa nazwę strefy.  

> [!NOTE]
>  *x* w tej właściwości name jest symbolem zastępczym tablicę wartości nieujemnych zawierającą konfiguracji DNS.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*Nazwa*|Określa nazwę strefy|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] DNSZones0Name=MyNewZone`|  

####  <a name="DNSZonesxScavenge"></a>DNSZonesxScavenge  
 Konfiguruje serwer podstawowy serwer DNS, aby "oczyścić" starych rekordów — to znaczy do wyszukiwania bazy danych dla rekordów, które uległy i usuń je.  

> [!NOTE]
>  *x* w tej właściwości name jest symbolem zastępczym tablicę wartości nieujemnych zawierającą konfiguracji DNS.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|**WARTOŚĆ TRUE**|Zezwalaj na oczyszczanie starych rekordów DNS.|  
|**WARTOŚĆ FALSE**|Nie zezwalaj oczyszczanie starych rekordów DNS.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] DNSZones0Scavenge=TRUE`|  

#### <a name="dnszonesxtype"></a>DNSZonesxType  
 Określa typ strefy, aby utworzyć.  

> [!NOTE]
>  *x* w tej właściwości name jest symbolem zastępczym tablicę wartości nieujemnych zawierającą konfiguracji DNS.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|**DSPrimary**|Tworzy strefa podstawowa i określanie, czy powinny być przechowywane w usługach AD DS na serwerze DNS, skonfigurowany jako kontroler domeny|  
|**DSStub**|Tworzy strefa skrótowa i określanie, czy powinny być przechowywane w usługach AD DS na serwerze DNS, skonfigurowany jako kontroler domeny|  
|**Podstawowy**|Tworzy strefa podstawowa|  
|**Pomocniczy**|Tworzy strefa dodatkowa|  
|**Stub**|Tworzy strefa skrótowa|  

|**Przykład**|  
|-|
|`[Settings] Priority=Default  [Default] DNSZones0Type=Secondary`|  

####  <a name="DNSZonesxUpdate"></a>DNSZonesxUpdate  
 Konfiguruje serwer podstawowy serwer DNS do przeprowadzania aktualizacji dynamicznej.  

> [!NOTE]
>  *x* w tej właściwości name jest symbolem zastępczym tablicę wartości nieujemnych zawierającą konfiguracji DNS.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|  
|**0**|Zezwalaj na aktualizacje dynamiczne|  
|**1**|Zezwala na aktualizacje dynamiczne|  
|**2**|Zezwala na zabezpieczone aktualizacje dynamiczne|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] DNSZones0Update=1`|  

####  <a name="DoCapture"></a>DoCapture  
 Wskazuje, czy ma być przechwytywane obrazu komputera docelowego. Jeśli tak jest, zostanie uruchomiony na komputerze docelowym, aby przygotować się do tworzenia obrazów. Po uruchomieniu programu Sysprep, nowy obraz WIM jest tworzony i zapisywany w folderze w folderze udostępnionym wyznaczone do kopii zapasowych komputera docelowego (**BackupDir** i **BackupShare**odpowiednio).  

> [!CAUTION]
>  Wartość tej właściwości należy określić pisane wielkimi literami, aby skrypty wdrażania może go prawidłowo odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|**TAK**|Skopiuj pliki niezbędne do uruchomienia programu Sysprep na komputerze docelowym, uruchom program Sysprep na komputerze docelowym i przechwytywanie obrazu WIM.|  
|**BRAK**|Narzędzie Sysprep nie jest uruchomione na komputerze docelowym, a nie Przechwytywanie obrazu WIM.|  
|**PRZYGOTOWANIE**|Skopiuj pliki niezbędne do uruchomienia programu Sysprep na komputerze docelowym, ale nie uruchamiaj programu Sysprep lub inne procesy przechwytywania obrazu.|  
|**NARZĘDZIE SYSPREP**|Skopiuj pliki niezbędne do uruchomienia programu Sysprep na komputerze docelowym, uruchom program Sysprep na komputerze docelowym, ale nie Przechwytywanie obrazu WIM.<br /><br /> Uwaga:<br /><br /> Głównym celem tej wartości jest umożliwienie tworzenia dysku VHD zawierającego system operacyjny, po uruchomieniu narzędzia Sysprep i niezbędne jest nie przechwytywania obrazu.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] DoCapture=YES DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ UDDir=%OSDComputerName%`|  

####  <a name="DomainAdmin"></a>Administrator domeny  
 Poświadczenia konta użytkownika, które są używane do przyłączenia komputera docelowego do domeny określonej w **przyłączania**. Określ jako *UserName*.  

> [!NOTE]
>  Dla ZTI używane są poświadczenia, które programu Configuration Manager, określa zazwyczaj. Jeśli **administrator domeny** określono właściwości poświadczenia w **administrator domeny** właściwości zastąpienia poświadczenia, które określa programu Configuration Manager.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*domain_admin*|Nazwa poświadczenia konta użytkownika|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] DomainAdmin=NYCAdmin DomainAdminDomain=WOODGROVEBANK DomainAdminPassword=<complex_password>`|  

####  <a name="DomainAdminDomain"></a>DomainAdminDomain  
 Domeny, w którym poświadczenia użytkownika określonego w **administrator domeny** znajdują się.  

> [!NOTE]
>  Dla ZTI używane są poświadczenia, które programu Configuration Manager, określa zazwyczaj. Jeśli **administrator domeny** określono właściwości poświadczenia w **administrator domeny** właściwości zastąpienia poświadczenia, które określa programu Configuration Manager.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*domain_admin_domain*|Nazwa domeny, na którym są przechowywane poświadczenia konta użytkownika|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] DomainAdmin=NYCAdmin DomainAdminDomain=WOODGROVEBANK DomainAdminPassword=<complex_password>`|  

####  <a name="DomainAdminPassword"></a>DomainAdminPassword  
 Hasło używane do domeny, konto administratora określone w **administrator domeny** właściwość, aby przyłączyć komputer do domeny.  

> [!NOTE]
>  Dla ZTI używane są poświadczenia, które programu Configuration Manager, określa zazwyczaj. Jeśli **administrator domeny** określono właściwości poświadczenia w **administrator domeny** właściwości zastąpienia poświadczenia, które określa programu Configuration Manager.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*domain_admin_password*|Hasło dla domeny konta administratora na komputerze docelowym|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] DomainAdmin=NYCAdmin DomainAdminDomain=WOODGROVEBANK DomainAdminPassword=<complex_password>`|  

####  <a name="DomainLevel"></a>DomainLevel  
 Ten wpis określa poziom funkcjonalności domeny. Ten wpis jest oparta na poziomach, które istnieją w lesie, podczas tworzenia nowej domeny w istniejącym lesie.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|  
|*Poziom*|Ustawia poziom funkcjonalności domeny do jednej z następujących czynności:<br /><br /> -2, Windows Server 2003<br /><br /> -3, Windows Server 2008<br /><br /> -4, Windows Server 2008 R2<br /><br /> -5, Windows Server 2012|  

|**Przykład**|  
|-|
|`[Settings] Priority=Default  [Default] DomainLevel=3`|  

####  <a name="DomainNetBiosName"></a>DomainNetBiosName  
 Przypisuje nazwę NetBIOS do nowej domeny.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*Nazwa*|Przypisuje nazwę NetBIOS do nowej domeny|  

|**Przykład**|  
|-|
|`[Settings] Priority=Default  [Default] DomainNetBiosName=NewDom`|  

####  <a name="DomainOUs"></a>DomainOUs  
 Lista usług AD DS także Podaj jednostki organizacyjne (OU) gdzie można utworzyć konta komputera docelowego. **DomainOUs** właściwość listę wartości tekstowych, które mogą być dowolnego niepustą wartość. **DomainOUs** właściwość ma sufiks numeryczny (na przykład **DomainOUs1** lub **DomainOUs2**). Wartości określonych przez DomainOUs zostanie wyświetlony w Kreatorze wdrażania wybieranych przez użytkownika. **MachineObjectOU** właściwość następnie zostanie ustawiona do jednostki Organizacyjnej wybrane.  

 Ponadto konfigurując pliku DomainOUList.xml można podać te same funkcje. Format pliku DomainOUList.xml jest następujący:  

```  
<?xml version="1.0" encoding="utf-8"?>  
<DomainOUs>  
<DomainOU>  
  OU=Computers,OU=Tellers,OU=NYC,DC=WOODGROVEBANK,DC=Com  
</DomainOU>  
<DomainOU>  
  OU=Computers,OU=Managers,OU=NYC,DC=WOODGROVEBANK,DC=Com  
</DomainOU>  
</DomainOUs>  
```  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*JEDNOSTKI ORGANIZACYJNEJ*|Jednostki Organizacyjnej, w którym można utworzyć konta komputera docelowego|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSInstall=Y DomainOUs1=OU=Computers, OU=Tellers, OU=NYC, DC=WOODGROVEBANK, DC=Com DomainOUs2=OU=Computers, OU=Managers, OU=NYC, DC=WOODGROVEBANK, DC=Com`|  

####  <a name="DoNotCreateExtraPartition"></a>DoNotCreateExtraPartition  
 Określa wdrożeń systemu Windows 7 i Windows Server 2008 R2 nie utworzy partycję systemową 300 MB.  

> [!CAUTION]
>  Wartość tej właściwości należy określić pisane wielkimi literami, aby skrypty wdrażania może go prawidłowo odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|  
|**TAK**|Na partycji systemowej dodatkowe nie zostanie utworzony.|  
|**BRAK**|Na partycji systemowej dodatkowe zostanie utworzony.|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] OSInstall=Y DoNotCreateExtraPartition=YES`|  

> [!NOTE]
>  Nie należy używać tej właściwości w połączeniu z właściwościami Aby skonfigurować ustawienia funkcji BitLocker.  

####  <a name="DoNotFormatAndPartition"></a>DoNotFormatAndPartition  
 Ta właściwość jest używana do konfigurowania, czy zestaw MDT wykonuje tych kroków sekwencji zadań podziału na partycje i formatowania w sekwencjach zadań utworzonych przy użyciu szablonów sekwencji zadań zestawu MDT.  

> [!CAUTION]
>  Wartość tej właściwości należy określić pisane wielkimi literami, aby skrypty wdrażania może go prawidłowo odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|  
|**TAK**|Podział na partycje i formatowania kroków sekwencji zadań w sekwencji zadań zestawu MDT zostaną wykonane.|  
|*Dowolna inna wartość*|Podział na partycje i formatowania kroków sekwencji zadań w sekwencji zadań zestawu MDT nie zostaną wykonane. Jest to wartość domyślna.|  

|**Przykład**|  
|-|
|`[Settings] Priority=Default  [Default] OSInstall=YES SkipUserData=YES USMTOfflineMigration=TRUE DoNotFormatAndPartition=YES OSDStateStorePath=\\WDG-MDT-01\StateStore$`|  

####  <a name="DriverGroup"></a>DriverGroup  
 Lista wartości tekstowych kojarzy sterowniki out-of-box utworzone w konsoli Deployment Workbench ze sobą (zazwyczaj na podstawie marka i model komputera). Sterownik może być skojarzony z co najmniej jednej grupy sterowników. **DriverGroup** właściwość umożliwia sterowniki w co najmniej jedną grupę w celu wdrażania na komputerze docelowym.  

 Wartości tekstowe na liście może być dowolnym niepustą wartość. **DriverGroup** sufiks numeryczny ma wartość właściwości (na przykład **DriverGroup001** lub **DriverGroup002**). Po jego zdefiniowaniu grupy sterowników jest skojarzony z komputerem. Komputer może być skojarzony z więcej niż jednej grupy sterowników.  

 Na przykład istnieją dwie sekcje dla każdego producenta komputera [Mfgr01] i [Mfgr02]. Dwie grupy sterowników są definiowane dla producenta Mfgr01: Sterowniki karty graficznej Mfgr01 i sterowniki sieciowe Mfgr01. Producent Mfgr02 zdefiniowano jednej grupy sterowników, sterowniki Mfgr02. Jednej grupy sterowników, udostępnionych sterowników jest stosowany do wszystkich komputerów w sekcji [domyślnie].  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*driver_group_name*|Nazwa grupy sterowników zdefiniowanych w konsoli Deployment Workbench|  

|**Przykład**|  
|-|
|`[Settings] Priority=Make, Default  [Default] DriverGroup001=Shared Drivers :: [Mfgr01] DriverGroup001=Mfgr01 Video Drivers DriverGroup002=Mfgr01 Network Drivers  [Mfgr02] DriverGroup001=Mfgr02 Drivers`|  

####  <a name="DriverInjectionMode"></a>DriverInjectionMode  
 Ta właściwość jest używana do sterowania sterowniki urządzeń, które są wstrzykiwane przez [wstrzyknąć sterowniki](#InjectDrivers) krok sekwencji zadań.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|Automatycznie|Wstaw tylko sterowniki zgodne z profilu zaznaczenie lub folderu.  To samo jako 2008 MDT injects wszystkie sterowniki, które pasują do jednego typu plug and play (PnP) identyfikatory (ID na komputerze docelowym).|  
|Wszystkie|Wstaw wszystkie sterowniki w profilu zaznaczenie lub folderu.|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] DriverInjectionMode=ALL DriverSelectionProfile=Nothing DriverPaths001=\\NYC-AM-FIL-01\Drivers$ DriverPaths002=\\NYC-AM-FIL-03\WinDrvs`|  

####  <a name="DriverPaths"></a>DriverPaths  
 Lista ścieżek UNC do folderów udostępnionych, w którym znajdują się dodatkowe sterowniki urządzeń. Te sterowniki urządzeń są instalowane z docelowego systemu operacyjnego na komputerze docelowym. Skrypty MDT skopiuj zawartość tych folderów do folderu C:\Drivers na komputerze docelowym. **DriverPaths** właściwości znajduje się lista wartości tekstowych, które mogą być dowolnego niepustą wartość. **DriverPaths** właściwość ma sufiks numeryczny (na przykład **DriverPaths001** lub **DriverPaths002**).  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*UNC_path*|Ścieżka UNC do folderu udostępnionego, w którym znajdują się dodatkowe sterowniki|  

|**Przykład**|  
|-|
|`[Settings] Priority=Default  [Default] DriverPaths001=\\NYC-AM-FIL-01\Drivers$ DriverPaths002=\\NYC-AM-FIL-03\Win8Drvs`|  

####  <a name="DriverSelectionProfile"></a>DriverSelectionProfile  
 Nazwa profilu jest używane podczas instalacji sterownika.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*nazwa_profilu*|Brak|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] DriverSelectionProfile=MonitorDrivers`|  

####  <a name="EventService"></a>EventService  
 **EventService** właściwość określa adres URL, którym jest uruchomiona MDT usługi monitorowania. Domyślnie usługa używa portu TCP 9800 do komunikacji. Zestaw MDT usługi monitorowania zbiera informacje na temat wdrażania na proces wdrażania, które mogą być wyświetlane w konsoli Deployment Workbench i użycie [Get-MDTMonitorData](#Get-MDTMonitorData) polecenia cmdlet.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*url_path*|Adres URL zestawu MDT, monitorowanie usługi.|  

|**Przykład**|  
|-|   
|`[Settings] Priority=Default  [Default] EventService=http://WDG-MDT-01:9800 DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$`|  

####  <a name="EventShare"></a>EventShare  
 **EventShare** właściwość wskazuje na folder udostępniony, w którym zestaw MDT skrypty rekordów zdarzeń.  

 Domyślnie udostępniony folder jest tworzony w C:\Events.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|  
|*UNC_path*|Ścieżka UNC do folderu udostępnionego, w którym zestaw MDT skrypty rekordów zdarzeń. Domyślna nazwa udziału jest zdarzenia.|  

|**Przykład**|  
|-|
|`[Settings] Priority=Default  [Default] EventShare=\\NYC-AM-FIL-01\Events DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$`|  

####  <a name="FinishAction"></a>FinishAction  
 Określa działanie podejmowane po zakończeniu sekwencji zadań LTI, czyli po **Podsumowanie** strona kreatora w Kreatorze wdrażania.  

> [!TIP]
>  Tej właściwości należy użyć w połączeniu z **SkipFinalSummary** właściwości, aby pominąć **Podsumowanie** strona kreatora w Kreatorze wdrażania i automatycznie wykonuje akcję.  

> [!CAUTION]
>  Wartość tej właściwości należy określić pisane wielkimi literami, aby skrypty wdrażania może go prawidłowo odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|  
|*Akcja*|Gdzie *akcji* jest jednym z następujących czynności:<br /><br /> - **ZAMKNIĘCIE**. Zamyka połączenie z komputerem docelowym.<br /><br /> - **PONOWNY ROZRUCH**. Ponowne uruchomienie komputera docelowego.<br /><br /> - **URUCHOM PONOWNIE**. Taki sam jak **ponowny ROZRUCH**.<br /><br /> - **WYLOGOWYWANIE**. Wyloguj bieżącego użytkownika. Jeśli komputer docelowy działa obecnie środowiska Windows PE, następnie komputer docelowy zostanie uruchomiona ponownie.<br /><br /> - **puste**. Zamknij Kreatora wdrażania bez wykonywania żadnych dodatkowych czynności. To jest ustawienie domyślne.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] FinishAction=REBOOT`|  

####  <a name="ForceApplyFallback"></a>ForceApplyFallback  
 Określa metodę używaną dla zainstalowanego systemu Windows:  

-   **Setup.exe**. Ta metoda jest metod tradycyjnych, zainicjować przez uruchomienie setup.exe z nośnika instalacyjnego. Domyślnie zestaw MDT używa tej metody.  

-   ImageX.exe. Ta metoda instaluje obraz systemu operacyjnego przy użyciu imagex.exe z **/ apply** opcji. Zestaw MDT używa tej metody, gdy nie można użyć metody setup.exe (tj. zestawu MDT przełączy się imagex.exe).  

 Oprócz kontrolowanie metody używane do instalowania tych systemów operacyjnych, ta właściwość ma wpływ na które sekwencji zadań systemu operacyjnego są wyświetlane w Kreatorze wdrażania dla architektury obrazu rozruchowego konkretny procesor. Jeśli wartość tej właściwości jest równa **nigdy**, tylko sekwencje pasuje do architektury procesora obrazu rozruchowego są wyświetlane zadania systemu operacyjnego. Jeśli wartość tej właściwości jest ustawiony na inną wartość lub jest pusty, wszystkie sekwencje zadań, które można użyć metody instalacji imagex.exe są wyświetlane, niezależnie od architektury procesora.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|  
|**NIGDY NIE**|Zestaw MDT zawsze używa metody imagex.exe, jeśli to konieczne. Tylko te sekwencje zadań, które wdrożyć system operacyjny zgodny z obrazu rozruchowego są wyświetlane w Kreatorze wdrażania.|  
|Wszelkie inne wartości, w tym puste| Wszelkie sekwencji zadań, która obsługuje metodę imagex.exe jest wyświetlana w Kreatorze wdrażania.|  


|**Przykład**|
 |-|
|`[Settings] Priority=Default  [Default] OSInstall=YES ForceApplyFallback=NEVER`|  

####  <a name="ForestLevel"></a>ForestLevel  
 Ten wpis określa poziom funkcjonalności lasu podczas tworzenia nowej domeny w nowym lesie.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|  
|*poziom*|Ustawia poziom funkcjonalności domeny do jednej z następujących czynności:<br /><br /> -2, Windows Server 2003<br /><br /> -3, Windows Server 2008<br /><br /> -4, Windows Server 2008 R2<br /><br /> -5, Windows Server 2012|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] ForestLevel=3`|  

####  <a name="FullName"></a>Imię i nazwisko  
 Pełna nazwa użytkownika podana podczas instalacji systemu operacyjnego komputera docelowego. Ta wartość jest wstawiany odpowiednie ustawienia konfiguracji w pliku Unattend.xml.  

> [!NOTE]
>  Ta wartość jest inna niż poświadczenia użytkownika utworzone po wdrożeniu systemu operacyjnego. **Imię i nazwisko** właściwość jest udostępniana jako informacje dla administratorów systemów o użytkowniku uruchamiania aplikacji na komputerze docelowym.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|  
|*full_name*|Pełna nazwa użytkownika, komputera docelowego|  

|**Przykład**|  
|-|  
|`[Settings] Priority=MACAddress, Default Properties=CustomProperty, ApplicationInstall  [Default] CustomProperty=TRUE OrgName=Woodgrove Bank  [00:0F:20:35:DE:AC] OSDNEWMACHINENAME=HPD530-1 ApplicationInstall=Custom FullName=Woodgrove Bank User  [00:03:FF:FE:FF:FF] OSDNEWMACHINENAME=BVMXP  ApplicationInstall=Minimum FullName=Woodgrove Bank Manager`|  

####  <a name="GPOPackPath"></a>GPOPackPath  
 Ta właściwość służy do zastępowania domyślna ścieżka do folderu, w którym znajdują się pakiety obiektu zasad grupy. Ścieżka określona w tej właściwości jest względne wobec folderu Templates\GPOPacks w udziału dystrybucyjnego. Zestaw MDT automatycznie skanuje określony podfolder tego folderu, systemem operacyjnym wdrażana na komputerze docelowym, na przykład Templates\GPOPacks\\*operating_system* (gdzie *operating_ System* jest wdrażany system operacyjny). Tabela 3 listę obsługiwanych systemów operacyjnych oraz podfolderów, które odpowiadają każdego systemu operacyjnego.  

##### <a name="table-3-windows-operating-systems-and-corresponding-gpo-pack-subfolder"></a>Tabela 3. Systemy operacyjne Windows i odpowiedniego podfolderu pakiet obiektu zasad grupy  

|**System operacyjny**|**Podfolder pakiet obiektu zasad grupy**|  
|-|-|  
|Windows 7 z dodatkiem SP1|Win7SP1 MDTGPOPack|  
|Windows Server 2008 R2|WS2008R2SP1 MDTGPOPack|  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|  
|*Ścieżka*|Ścieżka względem *distribution_share*\Templates\GPOPacks folder (gdzie *distribution_share* jest folder główny udziału dystrybucyjnego. Wartość domyślna to *distribution_share*\Templates\GPOPacks\\*operating_system* folder (gdzie *operating_system* na podstawie jest podfolderem wersja systemu operacyjnego).<br /><br /> W poniższym przykładzie ustawienie właściwości GPOPackPath na wartość "Win7 HighSecurity" umożliwia skonfigurowanie zestawu MDT, aby użyć *distribution_share*\Templates\GPOPacks\Win7-HighSecurity folder jako folder do przechowywania pakietów obiektu zasad grupy.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] GPOPackPath=Win7-HighSecurity`|  

####  <a name="Groups"></a>Grupy  
 Lista grup lokalnych na komputerze docelowym, którego członkostwo zostanie przechwycony. Członkostwo w grupie są przechwytywane w fazie przechwytywania stanu i przywróceniu w fazie przywracania stanu. (Są domyślne grupy Administratorzy i użytkownicy zaawansowani.) **Grup** właściwości znajduje się lista wartości tekstowych, które mogą być dowolnego niepustą wartość. **Grup** właściwość ma sufiks numeryczny (na przykład **Groups001** lub **Groups002**).  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|  
|*nazwa_grupy*|Nazwa komputera docelowego do grupy, do której będzie można przechwycić członkostwo w lokalnej grupie|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ CaptureGroups=YES Groups001=NYC Application Management Groups002=NYC Help Desk Users`|  

####  <a name="HideShell"></a>HideShell  
 Ta właściwość określa wyświetlanie Eksploratora Windows LTI sekwencji zadań jest uruchomiona w nowym systemie operacyjnym na komputerze docelowym. Ta właściwość może być używana w połączeniu z **DisableTaskMgr** właściwości.  

> [!NOTE]
>  Ta właściwość może być używana z **DisableTaskMgr** właściwość, aby uniemożliwić użytkownikom przerywania LTI sekwencji zadań. Aby uzyskać więcej informacji, zobacz [DisableTaskMgr](#DisableTaskMgr) właściwości.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|  
|**TAK**|Eksplorator Windows jest ukryty przed zakończeniem sekwencji zadań.|  
|**BRAK**|Eksplorator Windows jest widoczny, sekwencja zadań jest uruchomiona. Jest to wartość domyślna.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] DisableTaskMgr=YES HideShell=YES`|  

####  <a name="OSHome_Page"></a>OSHome_Page  
 Adres URL służący jako Windows Internet Explorer® strony głównej po wdrożeniu docelowego systemu operacyjnego.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|  
|*ADRES URL*|Adres URL strony sieci web do użycia jako strona główna programu Internet Explorer na komputerze docelowym|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] Home_Page=http://portal.woodgrovebank.com`|  

####  <a name="HostName"></a>Nazwa hosta  
 Nazwa hosta adresu IP komputera docelowego (nazwa przypisana do komputera docelowego).  

> [!NOTE]
>  Jest to nazwa komputera, na komputerze docelowym, a nie nazwa komputera NetBIOS komputera docelowego. Nazwa NetBIOS komputera może być krótszy niż nazwa komputera. Ponadto tej właściwości dynamicznie jest ustawiana przez zestaw MDT skryptów i nie może mieć jego wartość ustawiona w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu. Jednak służy tej właściwości w CustomSettings.ini lub zestaw MDT bazy danych, jak pokazano w poniższych przykładach ułatwiających definiując konfigurację komputera docelowego.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*host_name*|Nazwa hosta IP przypisane do komputera docelowego|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="ImagePackageID"></a>ImagePackageID  
 Identyfikator pakietu używane dla systemu operacyjnego do zainstalowania podczas wdrażania przez producenta OEM.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|
|-|-|  
|Brak|Identyfikator pakietu używane dla systemu operacyjnego do zainstalowania podczas wdrażania przez producenta OEM|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="InputLocale"></a>InputLocale  
 Listę ustawień regionalnych, które ma być używany z docelowego systemu operacyjnego. Można określić więcej niż jeden ustawień regionalnych dla docelowego systemu operacyjnego. Każdego ustawienia regionalne muszą być oddzielone średnikami (;). Jeśli nie zostanie określony, Kreatora wdrażania korzysta z ustawień regionalnych skonfigurowanych w wdrażany obraz.  

 Wyłączyć to ustawienie w Windows stanu użytkowników migracji narzędzia (USMT) podczas tworzenia kopii zapasowej i przywracanie informacji o stanie użytkownika. W przeciwnym razie wartość ustawienia w informacji o stanie użytkownika spowoduje zastąpienie wartości określonej w *InputLocale* właściwości.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|  
|*input_locale1; input_locale2*|Ustawienia regionalne klawiatury dołączony do komputera docelowego|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] UserLocale=en-us InputLocale=0409:00000409;0413:00020409;0413:00000409;0409:00020409`|  

####  <a name="InstallPackageID"></a>InstallPackageID  
 Identyfikator pakietu używane dla systemu operacyjnego do zainstalowania podczas wdrażania przez producenta OEM.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|Brak|Identyfikator pakietu używane dla systemu operacyjnego do zainstalowania podczas wdrażania przez producenta OEM|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="Instance"></a>Wystąpienie  
 Wystąpienie programu SQL Server używanego na potrzeby zapytań wartości właściwości z kolumn w tabeli określonej w **tabeli** właściwości. Baza danych znajduje się na komputerze określonym w **SQLServer** właściwości. Wystąpienie programu SQL Server na komputerze jest określona w **wystąpienia** właściwości.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
||*wystąpienie*|Nazwa wystąpienia programu SQL Server do użycia na potrzeby zapytań o wartości właściwości|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Computers, Default  [Default] OSInstall=YES  [Computers] SQLServer=NYC-SQL-01 Database=MDTDB Instance=SQLEnterprise2005 Table=Computers Parameters=SerialNumber, AssetTag ParameterCondition=OR`|  

####  <a name="IPAddress"></a>Adres IP  
 Adres IP komputera docelowego. Format adresu IP zwrócona przez właściwość jest standardowe kropkowo-cyfrowym; na przykład 192.168.1.1. Ta właściwość służy do tworzenia podsekcji, który zawiera ustawienia przeznaczone do komputera docelowego z określonego na podstawie adresu IP.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*IP\_adresu*|Adres IP komputera docelowego w standardowy kropkami\-notacji dziesiętnej|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="IsDesktop"></a>IsDesktop  
 Wskazuje, czy komputer jest pulpitu, ponieważ **Win32\_SystemEnclosure ChassisType** wartość właściwości jest **3**, **4**, **5** , **6**, **7**, lub **15**.  

> [!NOTE]
>  Tylko jeden z następujących właściwości będzie mieć wartość true w czasie: **IsDesktop**, **IsLaptop**, **IsServer**.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|**WARTOŚĆ TRUE**|Komputer docelowy jest komputerem stacjonarnym.|  
|**WARTOŚĆ FALSE**|Komputer docelowy nie jest komputerem stacjonarnym.|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="IsHypervisorRunning"></a>IsHypervisorRunning  
 Określa, czy funkcja hypervisor jest obecny na komputerze docelowym. Ta właściwość jest ustawiona, korzystając z informacji **CPUID** interfejsu.  

 Aby uzyskać dalsze informacje zebrane o maszyn wirtualnych i informacje zwrócone z **CPUID** interfejsu, zobacz następujące właściwości:  

-   **IsVM**  

-   **SupportsHyperVRole**  

-   **SupportsNX**  

-   **SupportsVT**  

-   **Supports64Bit**  

-   **VMPlatform**  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

> [!NOTE]
>  Właściwość IsVM należy ustalić, czy komputer docelowy jest maszyny wirtualnych lub fizycznych.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|**WARTOŚĆ TRUE**|Wykryto funkcji hypervisor.|  
|**WARTOŚĆ FALSE**|Funkcja hypervisor nie została wykryta.|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="IsLaptop"></a>IsLaptop  
 Wskazuje, czy komputer jest komputer przenośny, ponieważ **Win32\_SystemEnclosure ChassisType** wartość właściwości jest **8**, **10**, **12**, **14**, **18**, lub **21**.  

> [!NOTE]
>  Tylko jeden z następujących właściwości będzie mieć wartość true w czasie: **IsDesktop**, **IsLaptop**, **IsServer**.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|**WARTOŚĆ TRUE**|Komputer docelowy jest komputer przenośny.|  
|**WARTOŚĆ FALSE**|Komputer docelowy nie jest komputer przenośny.|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="IsServer"></a>IsServer  
 Wskazuje, czy komputer jest serwerem, ponieważ **Win32\_SystemEnclosure ChassisType** wartość właściwości jest **23**.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|**WARTOŚĆ TRUE**|Komputer docelowy jest serwerem.|  
|**WARTOŚĆ FALSE**|Komputer docelowy nie jest serwerem.|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="IsServerCoreOS"></a>IsServerCoreOS  
 Wskazuje, czy bieżący system operacyjny uruchomiony na komputerze docelowym jest opcją instalacji Server Core systemu operacyjnego Windows Server.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|**WARTOŚĆ TRUE**|System operacyjny na komputerze docelowym jest opcją instalacji Server Core systemu Windows Server.|  
|**WARTOŚĆ FALSE**|System operacyjny na komputerze docelowym nie jest opcją instalacji Server Core systemu Windows Server.|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="IsServerOS"></a>IsServerOS  
 Wskazuje, czy bieżący system operacyjny uruchomiony na komputerze docelowym jest system operacyjny serwera.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|**WARTOŚĆ TRUE**|System operacyjny na komputerze docelowym jest system operacyjny serwera.|  
|**WARTOŚĆ FALSE**|System operacyjny na komputerze docelowym nie jest system operacyjny serwera.|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="IsUEFI"></a>IsUEFI  
 Określa, czy komputer docelowy działa z Unified Extensible Firmware Interface \(UEFI\). To UEFI to specyfikacja interfejsu oprogramowania między systemu operacyjnego i oprogramowania układowego platformy. Z interfejsem UEFI jest bardziej bezpieczne zastępuje starszy interfejs oprogramowania sprzętowego BIOS w niektórych komputerów osobistych. Aby uzyskać więcej informacji dotyczących interfejsu UEFI, przejdź do [http:\/\/www.uefi.org](http://www.uefi.org).  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|**WARTOŚĆ TRUE**|Komputer docelowy działa z interfejsem UEFI.|  
|**WARTOŚĆ FALSE**|Komputer docelowy nie jest obecnie uruchomiona z interfejsem UEFI.<br /><br /> Uwaga:<br /><br /> Istnieje możliwość, że komputer docelowy może obsługują interfejs UEFI, ale działa w trybie zgodności, które emuluje starszy interfejs oprogramowania sprzętowego BIOS. W takiej sytuacji ustawi tę wartość tej właściwości na **FALSE** nawet jeśli komputer docelowy obsługuje UEFI.|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="IsVM"></a>IsVM  
 Określa, czy komputer docelowy jest maszyny Wirtualnej na podstawie informacji zebranych od **CPUID** interfejsu. Można określić w określonej maszyny Wirtualnej środowiska przy użyciu **VMPlatform** właściwości.  

 Aby uzyskać dalsze informacje zebrane o maszyn wirtualnych i informacje zwrócone z **CPUID** interfejsu, zobacz następujące właściwości:  

-   **IsHypervisorRunning**  

-   **SupportsHyperVRole**  

-   **SupportsNX**  

-   **SupportsVT**  

-   **Supports64Bit**  

-   **VMPlatform**  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|**WARTOŚĆ TRUE**|Komputer docelowy jest maszyny Wirtualnej.|  
|**WARTOŚĆ FALSE**|Komputer docelowy nie jest maszyny Wirtualnej.|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="JoinDomain"></a>Przyłączania  
 Domena, do której jest przyłączany komputer docelowy po docelowego systemu operacyjnego jest wdrażany. Jest to domena, gdzie jest tworzone konto komputera dla komputera docelowego. **Przyłączania** właściwości może zawierać znaki alfanumeryczne, łączniki \( \- \)i znaki podkreślenia \( \_ \). **Przyłączania** właściwości nie może być pusta ani zawierać spacji.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*domeny\_nazwy*|Nazwa domeny, do której jest przyłączany komputer docelowy|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] JoinDomain=WOODGROVEBANK MachineObjectOU=OU=Reception,OU=NYC,DC=Woodgrovebank,DC=com`|  

####  <a name="JoinWorkgroup"></a>JoinWorkgroup  
 Grupy roboczej, do której jest przyłączany komputer docelowy po docelowego systemu operacyjnego jest wdrażany. **JoinWorkgroup** właściwości może zawierać znaki alfanumeryczne, łączniki \( \- \)i znaki podkreślenia \( \_ \). **JoinWorkgroup** właściwości nie może być pusta ani zawierać spacji.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*Grupa robocza\_nazwy*|Nazwa grupy roboczej, do której jest przyłączany komputer docelowy|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] JoinWorkgroup=WDGV_WORKGROUP`|  

####  <a name="KeyboardLocale"></a>KeyboardLocale  
 Lista ustawień regionalnych klawiatury do użycia z docelowego systemu operacyjnego. Można określić więcej niż jeden klawiatury ustawień regionalnych dla docelowego systemu operacyjnego. Każdego ustawienia regionalne muszą być oddzielone średnikami \(;\). Jeśli nie zostanie określony, Kreatora wdrażania korzysta z ustawień regionalnych klawiatury skonfigurowany w obrazie wdrażany.  

 Wyklucz tego ustawienia w narzędzia USMT, podczas tworzenia kopii zapasowej i przywracanie informacji o stanie użytkownika. W przeciwnym razie wartość ustawienia w informacji o stanie użytkownika spowoduje zastąpienie wartości określonej w **KeyboardLocale** właściwości.  

> [!NOTE]
>  Dla tej właściwości, aby działać poprawnie musi być skonfigurowany zarówno CustomSettings.ini, jak i BootStrap.ini. BootStrap.ini są przetwarzane przed wybrano udział wdrożenia (zawierający CustomSettings.ini).  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*keyboard_locale1; keyboard_locale2*|Ustawienia regionalne klawiatury dołączony do komputera docelowego.<br /><br /> Wartość można określić w następujących formatach:<br /><br /> -Tekst (en-us)<br /><br /> -Liczba szesnastkowa: 0409: (00000409)|  

|**Przykład 1**|  
|-|  
|`[Settings] Priority=Default  [Default] UserLocale=en-us KeyboardLocale=en-us`|  

|**Przykład 2**|  
|-|  
|`[Settings] Priority=Default  [Default] UserLocale=en-us KeyboardLocale=0409:00000409;1809:00001809;041A:0000041A;083b:0001083b`|  

####  <a name="KeyboardLocalePE"></a>KeyboardLocalePE  
 Nazwa ustawień regionalnych klawiatury do użycia w środowisku Windows PE tylko.  

> [!NOTE]
>  Dla tej właściwości, aby działać poprawnie musi być skonfigurowany zarówno CustomSettings.ini, jak i BootStrap.ini. BootStrap.ini są przetwarzane przed wybrano udział wdrożenia (zawierający CustomSettings.ini).  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*keyboard_locale*|Ustawienia regionalne klawiatury dołączony do komputera docelowego.<br /><br /> Wartość można określić w następujących formatach:<br /><br /> -Tekst (en-us)<br /><br /> -Liczba szesnastkowa: 0409: (00000409)|  

|**Przykład 1**|  
|-|  
|`[Settings] Priority=Default  [Default] KeyboardLocalePE=en-us`|  

|**Przykład 2**|  
|-|  
|`[Settings] Priority=Default  [Default] KeyboardLocalePE=0409:00000409`|  

####  <a name="LanguagePacks"></a>LanguagePacks  
 Lista identyfikatorów GUID pakietów językowych można wdrożyć na komputerze docelowym. Konsoli Deployment Workbench określa tych pakietów językowych w węźle pakietów systemu operacyjnego. Te identyfikatory GUID są przechowywane w pliku Packages.xml. **LanguagePacks** właściwość ma sufiks numeryczny (na przykład **LanguagePacks001** lub **LanguagePacks002**).  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*language_pack_guid*|Identyfikator GUID, który określa konsoli Deployment Workbench pakietów językowych do zainstalowania na komputerze docelowym. Identyfikator GUID odpowiada GUID przechowywane w Packages.xml pakietu językowego.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] LanguagePacks001={a1923f8d-b07b-44c7-ac1e-353b7cc4c1ad}`|  

####  <a name="LoadStateArgs"></a>LoadStateArgs  
 Argumenty przekazywane do procesu Loadstate narzędzia USMT. Skrypt ZTI wstawia odpowiednie rejestrowania, postęp i stan parametry magazynu. Jeśli ta wartość nie jest uwzględniony w pliku ustawień, proces przywracania stanu użytkownika zostało pominięte.  

 W przypadku procesu Loadstate zakończy działanie pomyślnie, informacje o stanie użytkownika zostaną usunięte. W przypadku awarii Loadstate (lub niezerowy kod powrotny) magazynu stanu lokalnego została przeniesiona do %WINDIR%\StateStore, aby zapobiec usunięciu i upewnij się, że dane stanu użytkownika, nie zostaną utracone.  

> [!NOTE]
>  Nie dodawaj żadnego z następujących argumentów wiersza polecenia podczas konfigurowania tej właściwości: **/hardlink**, **/nocompress**, **/odszyfrowywania**, **następujący/key**, lub **/KeyFile**. Skrypty zestawu MDT zostaną dodane następujące argumenty wiersza polecenia, gdy mają zastosowanie do bieżącego scenariusza wdrażania.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|Argumenty|Argumenty wiersza polecenia przekazywane do Loadstate.exe.<br /><br /> Argumenty domyślne określone przez konsoli Deployment Workbench są następujące:<br /><br /> - **/v**. Włącza pełne dane wyjściowe w dzienniku Loadstate. Wartość domyślna to **0**. Określić dowolną liczbę z zakresu od 0 do 15. Wartość **5** umożliwia pełne i dane wyjściowe stanu.<br /><br /> - **/c**. W przypadku Loadstate będzie nadal działać, nawet jeśli istnieją błędy niekrytyczne. Bez **/c** opcji Loadstate opuszcza pierwszego błędu.<br /><br /> - **/LAC**. Określa, że jeśli migrowane konto jest kontem lokalnym (z systemem innym niż domena) i nie istnieje na komputerze docelowym, a następnie USMT utworzy konto, ale zostanie ona wyłączona.<br /><br /> Aby uzyskać więcej informacji na temat tych i innych argumentów Zobacz pliki pomocy narzędzia USMT.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSInstall=YES ScanStateArgs=/v:5 /o /c LoadStateArgs=/v:5 /c /lac DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ UDDir=%OSDComputerName%`|  

####  <a name="Location"></a>Lokalizacja  
 Lokalizację geograficzną na komputerach docelowych. Definiuje listę adresów IP, które odpowiadają bramy domyślne zdefiniowane dla komputerów w tej lokalizacji **lokalizacji** właściwości. Adres IP bramy domyślnej może być skojarzony z więcej niż jednej lokalizacji.  

 Zazwyczaj wartość **lokalizacji** właściwość jest ustawiona, wykonując zapytanie bazy danych w bazie danych zarządzania przy użyciu konsoli Deployment Workbench. Konsoli Deployment Workbench może pomóc w tworzeniu lokalizacjach, definiowanie ustawień właściwości skojarzone z lokalizacji, a następnie w konfigurowaniu CustomSettings.ini do przeprowadzenia kwerendy bazy danych dla lokalizacji właściwości i ustawienia właściwości skojarzone z lokalizacje.  

 Na przykład `LocationSettings` części CustomSettings.ini można zbadać widok LocationSettings w bazie danych dla listy lokalizacje, które zawierają wartości określonej w **brama_domyślna** na liście właściwości  **Parametry** właściwości. Zapytanie zwraca wszystkie ustawienia skojarzone z każdym bramy domyślnej.  

 Następnie skrypty przeanalizować każdej sekcji, która odpowiada lokalizacji zwracane w zapytaniu. Na przykład wartość `[Springfield]`i sekcji `[Springfield-123 Oak Street-4th Floor]` CustomSettings.ini może reprezentować odpowiedniej lokalizacji. To jest przykład z komputera, jak mogą należeć do dwóch lokalizacjach. `[Springfield]`Sekcja jest dla wszystkich komputerów w obszarze geograficznym większych (całego miejscowości) i `[Springfield-123 Oak Street-4th Floor]` sekcja dotyczy wszystkich komputerów w czwartym floor przy ulicy dębu 123, w województwach.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*location1,*location2|Listy lokalizacje, które mają zostać przypisane do konkretnego komputera lub grupy komputerów|  

|**Przykład**|  
|-|  
|`[Settings] Priority=LSettings, Default  [Default] UserDataLocation=AUTO DeployRoot=\\W2K3-SP1\Distribution$ OSInstall=YES ScanStateArgs=/v:15 /o /c LoadStateArgs=/v:7 /c  [LSettings] SQLServer=w2k3-sp1 Instance=MDT2010 Database=MDTDB Netlib=DBNMPNTW SQLShare=SQL$ Table=LocationSettings Parameters=DefaultGateway  [Springfield] UDDir=%OSDComputerName% UDShare=\\Springfield-FIL-01\UserData  [Springfield-123 Oak Street-4th Floor] DeployRoot=\\Springfield-BDD-01\Distribution1$`|  

####  <a name="LongDistanceAccess"></a>LongDistanceAccess  
 Cyfr numeru uzyskać dostęp z linią zewnętrzną do nawiązywania połączenia czas połączeń. Właściwość może zawierać tylko cyfry. Ta wartość jest wstawiany odpowiednie ustawienia konfiguracji w pliku Unattend.xml.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*language_pack_guid*|Identyfikator GUID, który określa konsoli Deployment Workbench pakietów językowych do zainstalowania na komputerze docelowym. Identyfikator GUID odpowiada GUID przechowywane w Packages.xml pakietu językowego.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] AreaCode=206 CountryCode=001 Dialing=TONE LongDistanceAccess=9`|  

####  <a name="MACAddress"></a>MACAddress  
 Adres media access control (MAC) warstwy karty sieciowej podstawowego komputera docelowego. **MACAddress** właściwości znajduje się na **priorytet** wiersz, dzięki czemu można podać wartości właściwości specyficzne dla komputera docelowego. Utwórz sekcję dla każdego adresu MAC dla wszystkich komputerów docelowych (takich jak `[00:0F:20:35:DE:AC]`lub `[00:03:FF:FE:FF:FF]`) zawierających ustawienia specyficzne dla komputera docelowego.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*Adres_MAC*|Adres MAC komputera docelowego|  

|**Przykład**|  
|-|  
|`[Settings] Priority=MACAddress, Default  [Default] CaptureGroups=YES Groups1=NYC Application Management Groups2=NYC Help Desk Users  [00:0F:20:35:DE:AC] OSDNEWMACHINENAME=HPD530-1  [00:03:FF:FE:FF:FF] OSDNEWMACHINENAME=BVMXP`|  

####  <a name="MachineObjectOU"></a>MachineObjectOU  
 Utworzono jednostkę Organizacyjną DS AD w domenie docelowej, gdy konto komputera dla komputera docelowego.  

> [!NOTE]
>  Jednostka Organizacyjna określone w tej właściwości musi istnieć przed wdrożeniem docelowego systemu operacyjnego.  

> [!NOTE]
>  Jeśli obiekt komputera istnieje już w usługach AD DS, określając **MachineObjectOU** nie spowoduje, że obiekt komputera zostanie przeniesiony na określonej jednostce Organizacyjnej.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*Jednostki Organizacyjnej\_nazwy*|Nazwa jednostki organizacyjnej, w której zostanie utworzone konto komputera dla komputera docelowego|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] JoinDomain=WOODGROVEBANK MachineObjectOU=OU=Reception,OU=NYC,DC=Woodgrovebank,DC=com`|  

####  <a name="Make"></a>Wprowadź  
 Producent komputera docelowego. Format **upewnij** jest niezdefiniowana. Ta właściwość służy do tworzenia podsekcji, zawierający ustawienia producenta komputera w określonym celem \(najczęściej w połączeniu z **modelu** i **produktu** właściwości\).  

> [!NOTE]
>  Tej właściwości ustawiono dynamicznie przez zestaw MDT skrypty i nie może mieć jego wartość ustawiona w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu. Jednak służy tej właściwości w CustomSettings.ini lub zestaw MDT bazy danych, jak pokazano w poniższych przykładach ułatwiających definiując konfigurację komputera docelowego.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*Wprowadź*|Producent komputera docelowego|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Make, Default  [Default]  [Dell Computer Corporation] Subsection=Dell-%Model%  [Dell-Latitude D600] Packages001=XXX00009:Program9 Packages002=XXX0000A:Program10`|  

####  <a name="MandatoryApplications"></a>MandatoryApplications  
 Lista identyfikatorów GUID aplikacji, które zostaną zainstalowane na komputerze docelowym. Te aplikacje są określone w węźle aplikacji w konsoli Deployment Workbench. Identyfikatory GUID są przechowywane w pliku Applications.xml. **MandatoryApplications** właściwości znajduje się lista wartości tekstowych, które mogą być dowolny z systemem innym niż\-puste wartości. **MandatoryApplications** właściwość ma sufiks numeryczny \(na przykład **MandatoryApplications001** lub **MandatoryApplications002** \).  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*Aplikacja\_identyfikator guid*|Identyfikator GUID określony przez konsoli Deployment Workbench dla aplikacji do wdrażania na komputerze docelowym. Identyfikator GUID odpowiada aplikacji, w której przechowywane w pliku Applications.xml identyfikatora GUID.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] MandatoryApplications001={1D7DF331-47B7-472C-87B3-442597EC2F7D} MandatoryApplications002={9d2b8999-5e4d-4f3d-bb05-edaaf4fe5628} Administrators001=WOODGROVEBANK\NYC Help Desk Staff`|  

####  <a name="Memory"></a>Pamięci  
 Ilość pamięci zainstalowanej na komputerze docelowym w megabajtach. Na przykład wartość **2038** wskazuje 2,038 MB \(lub 2 GB\) pamięci jest zainstalowany na komputerze docelowym.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*pamięci*|Ilość pamięci zainstalowanej na komputerze docelowym w megabajtach|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="Model"></a>Model  
 Model komputera docelowego. Format **modelu** jest niezdefiniowana. Ta właściwość służy do tworzenia podsekcji, zawierający ustawienia przeznaczone do określonego komputera liczby modelu dla określonego komputera producenta \(najczęściej w połączeniu z **upewnij** i  **Produkt** właściwości\).  

> [!NOTE]
>  Tej właściwości ustawiono dynamicznie przez zestaw MDT skrypty i nie może mieć jego wartość ustawiona w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu. Jednak służy tej właściwości w CustomSettings.ini lub zestaw MDT bazy danych, jak pokazano w poniższych przykładach ułatwiających definiując konfigurację komputera docelowego.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*Model*|Model komputera docelowego|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Make, Default  [Default]  [Dell Computer Corporation] Subsection=Dell-%Model%  [Dell-Latitude D600] Packages001=XXX00009:Program9 Packages002=XXX0000A:Program10`|  

####  <a name="NetLib"></a>NetLib  
 Protokół, który ma być używany do komunikowania się z komputera z uruchomionym serwerem SQL określony w **SQLServer** właściwości.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|\-||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|**DBNMPNTW**|Używanie protokołu potoków nazwanych do komunikacji.|  
|**DBMSSOCN**|Użyj protokołu TCP\/gniazda IP do komunikacji.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Computers, Default  [Default] ScanStateArgs=/v:5 /o /c LoadStateArgs=/v:5 /c /lac  [Computers] SQLServer=NYC-SQL-01 SQLShare=SQL$ NetLib=DBNMPNTW Database=MDTDB Instance=SQLEnterprise2005 Table=Computers Parameters=SerialNumber, AssetTag ParameterCondition=OR`|  

####  <a name="NewDomain"></a>NewDomain  
 Wskazuje typ nowej domeny: czy nową domenę w nowym lesie, katalog główny nowego drzewa w istniejącym lesie lub element podrzędny istniejącej domeny.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|Podrzędne|Nowa domena jest elementem podrzędnym istniejącej domeny.|  
|Lasu|Nowa domena jest pierwsza domena w lesie nowego drzew domen.|  
|drzewa|Nowej domeny jest głównym nowego drzewa w istniejącym lesie.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] NewDomain=Tree`|  

####  <a name="NewDomainDNSName"></a>NewDomainDNSName  
 Nazwa wymaganego nowego drzewa w istniejącej domenie lub instalacja nowego lasu domen.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*Nazwa*|Określa nazwę wymagane nowe drzewo w istniejącej domenie lub instalacja nowego lasu domen|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] NewDomainDNSName=newdom.WoodGroveBank.com`|  

####  <a name="Order"></a>Kolejność  
 Kolejność sortowania dla zestawu wyników, na zapytanie bazy danych. Zestaw wyników jest oparty na ustawienia konfiguracji **bazy danych**, **tabeli**, **SQLServer**, **parametry**i **ParameterCondition** właściwości. Sortowanie wyników można podać więcej niż jedną właściwość przez więcej niż jedną właściwość.  

 Na przykład jeśli **kolejności\=sekwencji** została określona w pliku CustomSettings.ini, a następnie **ORDER BY** klauzuli sekwencji zostanie dodany do kwerendy. **Określanie kolejności\=upewnij**, **modelu** dodaje **kolejności przez upewnij, Model** klauzuli do zapytania.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|\-||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*właściwości property1 property2...*|Właściwości, aby zdefiniować kolejność sortowania dla zestawu wyników \(gdzie *właściwośćN* reprezentuje właściwości w kryterium sortowania\)|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Computers, Default  [Default] OSInstall=YES ScanStateArgs=/v:5 /o /c LoadStateArgs=/v:5 /c /lac  [Computers] SQLServer=NYC-SQL-01 SQLShare=SQL$ NetLib=DBNMPNTW Database=MDTDB Instance=SQLEnterprise2005 Table=MakeModelSettings Parameters=SerialNumber, AssetTag ParameterCondition=OR Order=Make, Model`|  

####  <a name="OrgName"></a>Nazwa_org  
 Nazwa organizacji, która jest właścicielem komputera docelowego. Ta wartość jest wstawiany odpowiednie ustawienia konfiguracji w pliku Unattend.xml.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*org\_nazwy*|Nazwa organizacji, która jest właścicielem komputera docelowego|  

|**Przykład**|  
|-|  
|`[Settings] Priority=MACAddress, Default Properties=CustomProperty, ApplicationInstall  [Default] OSInstall=YES ScanStateArgs=/v:5 /o /c LoadStateArgs=/v:5 /c /lac UserDataLocation=NONE CustomProperty=TRUE OrgName=Woodgrove Bank  [00:0F:20:35:DE:AC] OSDNEWMACHINENAME=HPD530-1 ApplicationInstall=Custom FullName=Woodgrove Bank User  [00:03:FF:FE:FF:FF] OSDNEWMACHINENAME=BVMXP  ApplicationInstall=Minimum FullName=Woodgrove Bank Manager`|  

####  <a name="OSArchitecture"></a>OSArchitecture  
 Typ architektury procesora dla docelowego systemu operacyjnego. Ta właściwość jest wywoływany podczas wdrażania przez producenta OEM. Prawidłowe wartości to **x86** i **x64**.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|**x86**|Typ architektury procesora dla systemu operacyjnego jest 32-bitowych.|  
|**x64**|Typ architektury procesora przez system operacyjny jest 64-bitowym.|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="OSCurrentBuild"></a>OSCurrentBuild  
 Numer kompilacji systemu operacyjnego aktualnie uruchomione.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|**7600**|Windows 7|  
|**9600**|Windows 8.1|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="OSCurrentVersion"></a>OSCurrentVersion  
 Numer wersji aktualnie używanego systemu operacyjnego.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*numer_wersji*|Wersja główna systemu operacyjnego, podrzędny numer wersji i numery (major.minor.build) kompilacji. Na przykład 6.3.9600 będzie reprezentować Windows 8.1.|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="OSDAdapterxDescription"></a>OSDAdapterxDescription  
 Określa nazwę połączenia sieciowego, pojawiającą się w elemencie połączenia sieciowe w Panelu sterowania. Nazwa może być pomiędzy 0 a 255 znaków długości.  

 Ta właściwość jest tylko do LTI. Dla właściwości równoważne ZTI, zobacz [OSDAdapterxName](#OSDAdapterxName).  

> [!NOTE]
>  *x*w tej właściwości name jest symbolem zastępczym dla tablicy liczony od zera, który zawiera informacje dotyczące karty sieciowej, takich jak **OSDAdapter0Description** lub **OSDAdapter1Description**.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|Opis|Nazwa połączenia sieciowego w postaci, w jakiej jest wyświetlana w elementu połączenia sieciowe w Panelu sterowania|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="OSDAdapterxDNSDomain"></a>OSDAdapterxDNSDomain  
 Określa nazwę domeny DNS (sufiksu DNS), zostanie przypisana do połączenia sieciowego. Ta właściwość jest tylko do ZTI. Aby uzyskać LTI, zobacz [OSDAdapterxDNSSuffix](#OSDAdapterxDNSSuffix) właściwości.  

> [!NOTE]
>  *x*w tej właściwości name jest symbolem zastępczym dla tablicy liczony od zera, który zawiera informacje dotyczące karty sieciowej, takich jak **OSDAdapter0DNSDomain** lub **OSDAdapter1DNSDomain**.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI||  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*DNS_domain_name*|Nazwa domeny DNS (sufiksu DNS), zostanie przypisana do połączenia sieciowego|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0DNSDomain=WoodGroveBank.com`|  

####  <a name="OSDAdapterxDNSServerList"></a>OSDAdapterxDNSServerList  
 Jest to rozdzielana przecinkami lista adresów IP serwerów DNS, które zostanie przypisane do połączenia sieciowego.  

> [!NOTE]
>  *x*w tej właściwości name jest symbolem zastępczym dla tablicy liczony od zera, który zawiera informacje dotyczące karty sieciowej, takich jak **OSDAdapter0DNSServerList** lub **OSDAdapter1DNSServerList** .  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*DNS_servers*|Rozdzielana przecinkami lista adresów IP serwerów DNS, które zostanie przypisane do połączenia sieciowego|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0DNSServerList=192.168.0.254,192.168.100.254`|  

####  <a name="OSDAdapterxDNSSuffix"></a>OSDAdapterxDNSSuffix  
 Sufiks DNS zostanie przypisana do połączenia sieciowego. Ta właściwość jest tylko do LTI. Aby uzyskać ZTI, zobacz [OSDAdapterxDNSDomain](#OSDAdapterxDNSDomain) właściwości.  

> [!NOTE]
>  *x*w tej właściwości name jest symbolem zastępczym dla tablicy liczony od zera, który zawiera informacje dotyczące karty sieciowej, takich jak **OSDAdapter0DNSSuffix** lub **OSDAdapter1DNSSuffix**.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*Sufiks_dns*|Sufiks DNS zostanie przypisana do połączenia sieciowego|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0DNSSuffix= WoodGroveBank.com`|  

####  <a name="OSDAdapterxEnableDHCP"></a>OSDAdapterxEnableDHCP  
 Określa, czy połączenie sieciowe będzie można skonfigurować za pośrednictwem protokołu DHCP.  

> [!NOTE]
>  *x*w tej właściwości name jest symbolem zastępczym dla tablicy liczony od zera, który zawiera informacje dotyczące karty sieciowej, takich jak **OSDAdapter0EnableDHCP** lub **OSDAdapter1EnableDHCP**.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|**WARTOŚĆ TRUE**|Połączenie sieciowe zostaną skonfigurowane za pośrednictwem protokołu DHCP.|  
|**WARTOŚĆ FALSE**|Połączenie sieciowe będzie skonfigurowany z konfiguracją statycznego.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0EnableDHCP=TRUE`|  

####  <a name="OSDAdapterxEnableDNSRegistration"></a>OSDAdapterxEnableDNSRegistration  
 Określa, czy połączenie sieciowe jest włączone rejestrację DNS.  

> [!NOTE]
>  *x*w tej właściwości name jest symbolem zastępczym dla tablicy liczony od zera, który zawiera informacje dotyczące karty sieciowej, takich jak **OSDAdapter0EnableDNSRegistration** lub  **OSDAdapter1EnableDNSRegistration**.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|**WARTOŚĆ TRUE**|Umożliwia rejestrację DNS|  
|**WARTOŚĆ FALSE**|Wyłącza rejestrację DNS|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0EnableDNSRegistration=TRUE`|  

####  <a name="OSDAdapterxEnableFullDNSRegistration"></a>OSDAdapterxEnableFullDNSRegistration  
 Określa, czy pełną rejestrację DNS jest włączone dla połączenia sieciowego.  

> [!NOTE]
>  *x*w tej właściwości name jest symbolem zastępczym dla tablicy liczony od zera, który zawiera informacje dotyczące karty sieciowej, takich jak **OSDAdapter0EnableFullDNSRegistration** lub  **OSDAdapter1EnableFullDNSRegistration**.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|**WARTOŚĆ TRUE**|Włącza pełne rejestracji DNS|  
|**WARTOŚĆ FALSE**|Wyłącza pełne rejestracji DNS|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0EnableFullDNSRegistration=TRUE`|  

####  <a name="OSDAdapterxEnableLMHosts"></a>OSDAdapterxEnableLMHosts  
 Określa, czy wyszukiwanie LMHOSTS jest włączone dla połączenia sieciowego.  

> [!NOTE]
>  *x*w tej właściwości name jest symbolem zastępczym dla tablicy liczony od zera, który zawiera informacje dotyczące karty sieciowej, takich jak **OSDAdapter0EnableLMHosts** lub **OSDAdapter1EnableLMHosts** .  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|**WARTOŚĆ TRUE**|Umożliwia wyszukiwanie LMHOSTS|  
|**WARTOŚĆ FALSE**|Wyłącza wyszukiwanie LMHOSTS|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0EnableLMHosts=TRUE`|  

####  <a name="OSDAdapterxEnableIPProtocolFiltering"></a>OSDAdapterxEnableIPProtocolFiltering  
 Ta właściwość określa, czy filtrowanie protokołu IP powinno być włączone dla połączenia sieciowego.  

 *x*w nazwie tej właściwości jest symbolem zastępczym dla tablicę wartości nieujemnych zawierającą informacje o sieci karty, takie jak *OSDAdapter0EnableIPProtocolFiltering* lub  **OSDAdapter1EnableIPProtocolFiltering**.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|**WARTOŚĆ TRUE**|Umożliwia filtrowanie protokołu IP|  
|**WARTOŚĆ FALSE**|Wyłącza filtrowanie protokołu IP|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0EnableIPProtocolFiltering =TRUE`|  

####  <a name="OSDAdapterxEnableTCPFiltering"></a>OSDAdapterxEnableTCPFiltering  
 Określa, czy TCP\/filtrowanie IP powinno być włączone dla połączenia sieciowego. Ta właściwość jest tylko do ZTI. Aby uzyskać LTI, zobacz [OSDAdapterxEnableTCPIPFiltering](#OSDAdapterxEnableTCPIPFiltering) właściwości.  

> [!NOTE]
>  *x*w tym nazwy właściwości to symbol zastępczy zera\-na podstawie tablicy, która zawiera informacje dotyczące karty sieciowej, takie jak **OSDAdapter0EnableTCPFiltering** lub  **OSDAdapter1EnableTFiltering**.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|**WARTOŚĆ TRUE**|Włącza TCP\/filtrowanie IP|  
|**WARTOŚĆ FALSE**|Wyłącza TCP\/filtrowanie IP|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0EnableTCPFiltering=TRUE`|  

####  <a name="OSDAdapterxEnableTCPIPFiltering"></a>OSDAdapterxEnableTCPIPFiltering  
 Określa, czy TCP\/filtrowanie IP powinno być włączone dla połączenia sieciowego. Ta właściwość jest tylko do LTI. Aby uzyskać ZTI, zobacz [OSDAdapterxEnableTCPFiltering](#OSDAdapterxEnableTCPFiltering) właściwości.  

> [!NOTE]
>  *x*w tej właściwości name jest symbolem zastępczym zero\-na podstawie tablicy, która zawiera informacje dotyczące karty sieciowej, takie jak **OSDAdapter0EnableTCPIPFiltering** lub  **OSDAdapter1EnableTCPIPFiltering**.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|**WARTOŚĆ TRUE**|Włącza TCP\/filtrowanie IP|  
|**WARTOŚĆ FALSE**|Wyłącza TCP\/filtrowanie IP|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0EnableTCPIPFiltering=TRUE`|  

####  <a name="OSDAdapterxEnableWINS"></a>OSDAdapterxEnableWINS  
 Określa, czy usługa WINS zostanie włączone połączenie sieciowe.  

> [!NOTE]
>  *x*w tej właściwości name jest symbolem zastępczym zero\-na podstawie tablicy, która zawiera informacje dotyczące karty sieciowej, takie jak **OSDAdapter0EnableWINS** lub  **OSDAdapter1EnableWINS**.  

> [!CAUTION]
>  Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|**WARTOŚĆ TRUE**|Umożliwia usłudze WINS|  
|**WARTOŚĆ FALSE**|Wyłącza WINS|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0EnableWINS=TRUE OSDAdapter0WINSServerList=192.168.0.1,192.168.100.1`|  

####  <a name="OSDAdapterxGatewayCostMetric"></a>OSDAdapterxGatewayCostMetric  
 Przecinek\-lista ograniczanych znakami metryki koszt bramy określony jako liczby całkowite lub ciąg "Automatyczny" \(w przypadku braku używa "Automatyczny"\) która zostanie skonfigurowana w połączeniu.  

> [!NOTE]
>  *x*w tej właściwości name jest symbolem zastępczym zero\-na podstawie tablicy, która zawiera informacje dotyczące karty sieciowej, takie jak **OSDAdapter0GatewayCostMetric** lub  **OSDAdapter1GatewayCostMetric**.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*koszt\_metryk*|Przecinek\-lista ograniczanych znakami metryki koszt bramy|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0GatewayCostMetrics=Automatic`|  

####  <a name="OSDAdapterxGateways"></a>OSDAdapterxGateways  
 Przecinek\-lista ograniczanych znakami bramy do przypisania do połączenia sieciowego.  

> [!NOTE]
>  *x*w tej właściwości name jest symbolem zastępczym zero\-na podstawie tablicy, która zawiera informacje dotyczące karty sieciowej, takie jak **OSDAdapter0Gateways** lub  **OSDAdapter1Gateways**.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*bramy*|Przecinek\-przecinkami lista bram|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0Gateways=192.168.0.1,192.168.100.1`|  

####  <a name="OSDAdapterxIPAddressList"></a>OSDAdapterxIPAddressList  
 Przecinek\-rozdzielanej lista adresów IP ma być przypisany do połączenia sieciowego.  

> [!NOTE]
>  *x*w tej właściwości name jest symbolem zastępczym zero\-na podstawie tablicy, która zawiera informacje dotyczące karty sieciowej, takie jak **OSDAdapter0IPAddressList** lub  **OSDAdapter1IPAddressList**.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*IP\_adresów*|Rozdzielaną przecinkami listę adresów IP|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0IPAddressList=192.168.0.40,192.168.100.40 OSDAdapter0SubnetMask=255.255.255.0,255.255.255.0`|  

####  <a name="OSDAdapterxIPProtocolFilterList"></a>OSDAdapterxIPProtocolFilterList  
 Przecinek\-przecinkami lista filtrów protokołu IP ma być przypisany do połączenia sieciowego. Tej właściwości można skonfigurować przy użyciu pliku CustomSettings.ini lub zestaw MDT bazę danych, ale nie konsoli Deployment Workbench. W przypadku używania programu Configuration Manager jest także można skonfigurować za pomocą **Zastosuj ustawienia sieci** krok sekwencji zadań.  

> [!NOTE]
>  *x*w tej właściwości name jest symbolem zastępczym zero\-na podstawie tablicy, która zawiera informacje dotyczące karty sieciowej, takie jak **OSDAdapter0IPProtocolFilterList** lub  **OSDAdapter1IPProtocolFilterList**.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*Protokół\_filtru\_listy*|Przecinek\-przecinkami lista filtrów protokołu IP|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0IPProtocolFilterList=a list of approved IP protocols`|  

####  <a name="OSDAdapterxMacAddress"></a>OSDAdapterxMacAddress  
 Ustawienia konfiguracji należy przypisać do karty interfejsu sieciowego, który pasuje do określonego adresu MAC.  

> [!NOTE]
>  *x*w tej właściwości name jest symbolem zastępczym zero\-na podstawie tablicy, która zawiera informacje dotyczące karty sieciowej, takie jak **OSDAdapter0MacAddress** lub  **OSDAdapter1MacAddress**.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*MAC\_adresu*|Karta sieciowa adres MAC|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0MacAddress=00:0C:29:67:A3:6B`|  

####  <a name="OSDAdapterxName"></a>OSDAdapterxName  
 Ustawienia konfiguracji należy przypisać do karty sieciowej, która odpowiada podanej nazwie. Ta właściwość jest tylko do ZTI. Dla właściwości równoważne LTI, zobacz [OSDAdapterxDescription](#OSDAdapterxDescription).  

> [!NOTE]
>  *x*w tej właściwości name jest symbolem zastępczym zero\-na podstawie tablicy, która zawiera informacje dotyczące karty sieciowej, takie jak **OSDAdapter0Name** lub **OSDAdapter1Name**.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI||  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*Nazwa*|Nazwa karty sieciowej|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0Name=3Com 3C920 Integrated Fast Ethernet Controller`|  

####  <a name="OSDAdapterxSubnetMask"></a>OSDAdapterxSubnetMask  
 Przecinek\-przecinkami lista masek podsieci IP ma być przypisany do połączenia sieciowego.  

> [!NOTE]
>  *x*w tej właściwości name jest symbolem zastępczym zero\-na podstawie tablicy, która zawiera informacje dotyczące karty sieciowej, takie jak **OSDAdapter0SubnetMask** lub  **OSDAdapter1SubnetMask**.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*podsieci\_masek*|Przecinek\-przecinkami lista masek podsieci IP|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0IPAddressList=192.168.0.40,192.168.100.40 OSDAdapter0SubnetMask=255.255.255.0,255.255.255.0`|  

#### <a name="osdadapterxtcpfilterportlist"></a>OSDAdapterxTCPFilterPortList  
 Przecinek\-przecinkami lista portów TCP filtr do przypisania do połączenia sieciowego. Tej właściwości można skonfigurować przy użyciu pliku CustomSettings.ini lub zestaw MDT bazę danych, ale nie konsoli Deployment Workbench. W przypadku używania programu Configuration Manager jest także można skonfigurować za pomocą **Zastosuj ustawienia sieci** krok sekwencji zadań.  

> [!NOTE]
>  *x*w tej właściwości name jest symbolem zastępczym zero\-na podstawie tablicy, która zawiera informacje dotyczące karty sieciowej, takie jak **OSDAdapter0TCPFilterPortList** lub  **OSDAdapter1TCPFilterPortList**.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*port\_listy*|Przecinek\-lista ograniczanych znakami TCP\/portów filtru IP|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0TCPFilterPortList=a list of approved TCP ports`|  

####  <a name="OSDAdapterxTCPIPNetBiosOptions"></a>OSDAdapterxTCPIPNetBiosOptions  
 Określa protokół TCP\/opcje IP NetBIOS ma być przypisany do połączenia sieciowego.  

> [!NOTE]
>  *x*w tej właściwości name jest symbolem zastępczym zero\-na podstawie tablicy, która zawiera informacje dotyczące karty sieciowej, takie jak **OSDAdapter0TCPIPNetBiosOptions** lub  **OSDAdapter1TCPIPNetBiosOptions**.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|**0**|Wyłącz przesyłanie dalej IP.|  
|**1**|Włącz przesyłanie dalej IP.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0TCPIPNetBiosOptions=0`|  

####  <a name="OSDAdapterxUDPFilterPortList"></a>OSDAdapterxUDPFilterPortList  
 Przecinek\-lista ograniczanych znakami User Datagram Protocol \(UDP\) filtrowania portów do przypisania do połączenia sieciowego. Tej właściwości można skonfigurować przy użyciu pliku CustomSettings.ini i DB zestawu MDT, ale nie konsoli Deployment Workbench. W przypadku używania programu Configuration Manager jest także można skonfigurować za pomocą **Zastosuj ustawienia sieci** krok sekwencji zadań.  

> [!NOTE]
>  *x*w tej właściwości name jest symbolem zastępczym zero\-na podstawie tablicy, która zawiera informacje dotyczące karty sieciowej, takie jak **OSDAdapter0UDPFilterPortList** lub  **OSDAdapter1UDPFilterPortList**.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*port\_listy*|Przecinek\-przecinkami lista portów UDP filtru|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0UDPFilterPortList=a list of approved UDP ports`|  

####  <a name="OSDAdapterxWINSServerList"></a>OSDAdapterxWINSServerList  
 Dwa\-elementu, przecinek\-lista ograniczanych znakami adres IP serwera WINS adresów do przypisania do połączenia sieciowego.  

> [!NOTE]
>  *x*w tej właściwości name jest symbolem zastępczym zero\-na podstawie tablicy, która zawiera informacje dotyczące karty sieciowej, takie jak **OSDAdapter0WINSServerList** lub  **OSDAdapter1WINSServerList**.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*WINS\_serwera\_listy*|Przecinek\-przecinkami lista adresów IP serwerów WINS|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapter0EnableWINS=TRUE OSDAdapter0WINSServerList=192.168.0.1,192.168.100.1`|  

####  <a name="OSDAdapterCount"></a>OSDAdapterCount  
 Określa liczbę połączeń sieciowych, które mogą być konfigurowane.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|Liczba|Liczba kart sieciowych|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDAdapterCount=1 OSDAdapter0EnableDHCP=FALSE OSDAdapter0IPAddressList=192.168.0.40,192.168.100.40 OSDAdapter0SubnetMask=255.255.255.0,255.255.255.0 OSDAdapter0Gateways=192.168.0.1,192.168.100.1 OSDAdapter0EnableWINS=TRUE OSDAdapter0WINSServerList=192.168.0.1,192.168.100.1 OSDAdapter0TCPIPNetBiosOptions=0 OSDAdapter0MacAddress=00:0C:29:67:A3:6B OSDAdapter0GatewayCostMetrics=Automatic OSDAdapter0EnableTCPIPFiltering=TRUE OSDAdapter0EnableLMHosts=TRUE OSDAdapter0EnableFullDNSRegistration=TRUE OSDAdapter0EnableDNSRegistration=TRUE OSDAdapter0DNSSuffix=WoodGroveBank.com`|  

#### <a name="osdanswerfilepath"></a>OSDAnswerFilePath  
 Określa ścieżkę do pliku odpowiedzi, które mają być użyte podczas wdrożenia przez producenta OEM.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*plik\_ścieżki*|Określa ścieżkę do pliku odpowiedzi, które mają być użyte podczas wdrożenia przez producenta OEM|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="OSDBitLockerCreateRecoveryPassword"></a>OSDBitLockerCreateRecoveryPassword  
 Wartość logiczna wskazująca, czy proces tworzy klucz odzyskiwania funkcji BitLocker. Klucz jest używany do odzyskiwania danych zaszyfrowanych woluminu funkcji BitLocker. Ten klucz jest kryptograficznie odpowiednikiem klucza uruchomienia. Jeśli jest dostępna, klucz odzyskiwania odszyfrowuje VMK, który z kolei odszyfrowuje FVEK.  

> [!NOTE]
>  Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|**USŁUGI AD**|Klucz odzyskiwania jest tworzony.|  
|Nie określono|Nie utworzono klucz odzyskiwania.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] BDEInstallSuppress=NO BDEDriveLetter=S: BDEDriveSize=2000 OSDBitLockerMode=TPMKey OSDBitLockerCreateRecoveryPassword=AD OSDBitLockerStartupKeyDrive=C:`|  

####  <a name="OSDBitLockerMode"></a>OSDBitLockerMode  
 Typ instalacji funkcji BitLocker do wykonania. Ochrona komputera docelowego przy użyciu jednej z następujących metod:  

-   Mikroukłady modułu TPM  

-   Moduł TPM i klucz uruchomienia zewnętrznych \(przy użyciu klucza, który zazwyczaj znajduje się na dysku flash USB\)  

-   Moduł TPM i numer PIN  

-   Klucz uruchomienia zewnętrznych  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|**MODUŁ TPM**|Chroń tylko komputer z modułem TPM. Moduł TPM jest mikroukłady, na którym są przechowywane klucze, hasła i certyfikatów cyfrowych. Mikroukłady zwykle jest integralną częścią płyty głównej.|  
|**TPMKey**|Ochrona komputerów z modułem TPM i klucz uruchomienia. Użyj tej opcji, aby utworzyć klucz uruchomienia i zapisać go na dysku flash USB. Klucz uruchomienia musi być obecny w porcie każdym uruchomieniu komputera.|  
|**TPMPin**|Ochrona komputerów z modułem TPM i numeru pin. Użyj tej opcji w połączeniu z **BDEPin** właściwości.<br /><br /> Uwaga:<br /><br /> Ta wartość jest nieprawidłowa, korzystając z ZTI.|  
|**Klucz**|Chronić komputer z kluczem zewnętrznym \(klucza odzyskiwania\) którego przechowywane w folderze, w usługach AD DS lub wydrukować.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] BDEInstallSuppress=NO BDEDriveLetter=S: BDEDriveSize=2000 OSDBitLockerMode=TPM OSDBitLockerCreateRecoveryPassword=AD`|  

####  <a name="OSDBitLockerRecoveryPassword"></a>OSDBitLockerRecoveryPassword  
 Zamiast generowania losowego hasła odzyskiwania akcja sekwencji zadań **Włącz funkcję BitLocker** używa określonej wartości jako hasła odzyskiwania. Wartość musi być prawidłowym liczbowym hasłem odzyskiwania funkcji BitLocker.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*hasło*|Nieprawidłowa 48\-cyfrowe hasło|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] BDEInstallSuppress=NO BDEDriveLetter=S: BDEDriveSize=2000 OSDBitLockerMode=TPMKey OSDBitLockerCreateRecoveryPassword=AD OSDBitLockerRecoveryPassword=621280128854709621167486709731081433315062587367 OSDBitLockerStartupKeyDrive=C:`|  

####  <a name="OSDBitLockerStartupKey"></a>OSDBitLockerStartupKey  
 Zamiast generowania losowego klucza uruchomienia dla opcji zarządzania kluczami **klucz uruchomienia tylko na USB**, **Włącz funkcję BitLocker** akcji sekwencji zadań wartość jest używana jako klucz uruchomienia. Wartość musi być prawidłową, Base64\-zakodowany klucz uruchomienia funkcji BitLocker.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*klucz uruchomienia*|Base64\-zakodowany klucz uruchomienia funkcji BitLocker|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] BDEInstallSuppress=NO BDEDriveLetter=S: BDEDriveSize=2000 BDEInstall=KEY OSDBitLockerCreateRecoveryPassword=AD OSDBitLockerStartupKey=8F4922B8-2D8D-479E-B776-12629A361049`|  

####  <a name="OSDBitLockerStartupKeyDrive"></a>OSDBitLockerStartupKeyDrive  
 Lokalizacja do przechowywania klucza odzyskiwania funkcji BitLocker i klucz uruchomienia.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*Lokalizacja*|Lokalizacja magazynu dla klucza odzyskiwania i klucz uruchomienia \(albo lokalnego na komputerze docelowym lub ścieżką UNC, który wskazuje z udostępnionym folderem sieciowym\)|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] BDEInstallSuppress=NO BDEDriveLetter=S: BDEDriveSize=2000 OSDBitLockerMode=TPMKey OSDBitLocker CreateRecoveryPassword=AD OSDBitLockerStartupKeyDrive=C:`|  

####  <a name="OSDBitLockerTargetDrive"></a>OSDBitLockerTargetDrive  
 Określa dysk do zaszyfrowania. Domyślnym dysku to dysk, który zawiera system operacyjny.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*dysk*|Dysk, który ma być szyfrowane|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] BDEInstallSuppress=NO BDEDriveLetter=S: BDEDriveSize=2000 BDERecoveryPassword=TRUE OSDBitLockerMode=TPMKey OSDBitLockerCreateRecoveryPassword=AD OSDBitLockerTargetDrive=C:`|  

####  <a name="OSDBitLockerWaitForEncryption"></a>OSDBitLockerWaitForEncryption  
 Określa, że proces wdrażania nie powinien kontynuować, aż do zakończenia procesu szyfrowania wszystkich dysków w określonej funkcji BitLocker. Określenie wartości TRUE może znacznie zwiększyć czas wymagany do ukończenia procesu wdrażania.  

> [!CAUTION]
>  Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|**WARTOŚĆ TRUE**|Określa, że proces wdrażania powinna czekać na zakończenie szyfrowania dysku|  
|**WARTOŚĆ FALSE**|Określa, że proces wdrożenia nie należy czekać do szyfrowania dysku na zakończenie|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] BDEInstallSuppress=NO BDEDriveLetter=S: BDEDriveSize=2000 OSDBitLockerMode=TPMKey OSDBitLockerStartupKeyDrive=C: OSDBitLockerCreateRecoveryPassword=AD OSDBitLockerWaitForEncryption=TRUE`|  

####  <a name="OSDComputerName"></a>OSDComputerName  
 Nowa nazwa komputera można przypisać do komputera docelowego.  

> [!NOTE]
>  Można również ustawić tę właściwość w ramach sekwencji zadań za pomocą dostosowanego **Ustaw zmienną sekwencji zadań** krok sekwencji zadań.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*komputer\_nazwy*|Nowa nazwa komputera można przypisać do komputera docelowego|  

|**Przykład**|  
|-|  
|`[Default] OSDComputerName=%_SMSTSMachineName%`|  

####  <a name="OSDDiskAlign"></a>OSDDiskAlign  
 Ta właściwość jest używana do przekazania wartości do **Dopasuj** parametr **tworzenie partycji podstawowej** w **DiskPart** polecenia. **Dopasuj** parametr jest zwykle używany ze sprzętem numer jednostki logicznej RAID \(LUN\) tablic w celu zwiększenia wydajności podczas jednostki logiczne \(lu\) nie są wyrównane cylinder. **Dopasuj** parametr wyrównuje partycji podstawowej, która nie jest wyrównany na początku dysku cylinder i powoduje zaokrąglenie do najbliższej granicy wyrównania przesunięcie. Aby uzyskać więcej informacji na temat **Dopasuj** parametrów, zobacz [tworzenie partycji podstawowej](http://technet.microsoft.com/library/cc771243\(WS.10\).aspx).  

> [!NOTE]
>  Ta właściwość może być używana w połączeniu z **OSDDiskOffset** właściwości można ustawić **przesunięcie** parametr **tworzenie partycji podstawowej** w **DiskPart** polecenia. Aby uzyskać więcej informacji, zobacz [OSDDiskOffset](#OSDDiskOffset) właściwości.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*Wyrównanie\_wartość*|Określa liczbę kilobajtów \(KB\) od początku dysku do najbliższej granicy wyrównania.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDDiskAlign=1024 OSDDiskOffset=2048`|  

####  <a name="OSDDiskIndex"></a>OSDDiskIndex  
 Określa indeks dysku, który zostanie skonfigurowany.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*dysk\_indeksu*|Określa indeks dysku, który zostanie skonfigurowany \(wartość domyślna to **0**.\)|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDDiskIndex=0`|  

####  <a name="OSDDiskOffset"></a>OSDDiskOffset  
 Ta właściwość jest używana do przekazania wartości do **przesunięcie** parametr **tworzenie partycji podstawowej** w **DiskPart** polecenia. Aby uzyskać więcej informacji na temat **przesunięcie** parametrów, zobacz [tworzenie partycji podstawowej](http://technet.microsoft.com/library/cc771243\(WS.10\).aspx).  

 Ta właściwość może być używana w połączeniu z **OSDDiskAlign** właściwości można ustawić **Dopasuj** parametr **tworzenie partycji podstawowej** w **DiskPart** polecenia. Aby uzyskać więcej informacji, zobacz [OSDDiskAlign](#OSDDiskAlign) właściwości.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*Przesunięcie\_wartość*|Określa przesunięcie bajtów podczas tworzenia partycji. Dla głównego rekordu rozruchowego \(MBR\) dysków, Przesunięcie powoduje zaokrąglenie do najbliższej granicy cylinder.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDDiskAlign=1024 OSDDiskOffset=2048`|  

####  <a name="OSDDiskPartBiosCompatibilityMode"></a>OSDDiskPartBiosCompatibilityMode  
 Ta właściwość określa, czy wyłączyć optymalizacje wyrównania pamięci podręcznej podczas partycjonowania dysku twardego w celu zapewnienia zgodności z pewnymi typami systemu BIOS.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|**WARTOŚĆ TRUE**|Włącza buforowanie optymalizacje wyrównania podczas partycjonowania dysku twardego w celu zapewnienia zgodności z pewnymi typami systemu BIOS|  
|**WARTOŚĆ FALSE**|Wyłącza buforowanie optymalizacje wyrównania podczas partycjonowania dysku twardego w celu zapewnienia zgodności z pewnymi typami systemu BIOS \(jest to wartość domyślna.\)|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDDiskPartBiosCompatibilityMode=TRUE`|  

####  <a name="OSDImageCreator"></a>OSDImageCreator  
 Określa nazwę konta instalacji, który będzie używany podczas wdrażania przez producenta OEM.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*obraz\_creator*|Określa nazwę konta instalacji, który będzie używany podczas wdrażania przez producenta OEM|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="OSDImageIndex"></a>OSDImageIndex  
 Określa indeks obrazu w pliku wim. Ta właściwość jest wywoływany podczas wdrażania przez producenta OEM.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*Indeks*|Określa indeks obrazu w pliku WIM|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="OSDImagePackageID"></a>OSDImagePackageID  
 Określa identyfikator pakietu obrazu do zainstalowania podczas wdrażania przez producenta OEM.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*pakiet\_ID*|Określa identyfikator pakietu obrazu do zainstalowania podczas wdrażania przez producenta OEM|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="OSDInstallEditionIndex"></a>OSDInstallEditionIndex  
 Określa indeks obrazu w pliku WIM. Ta właściwość jest wywoływany podczas wdrażania przez producenta OEM.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*Indeks*|Określa indeks obrazu w pliku WIM|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="OSDInstallType"></a>OSDInstallType  
 Określa typ instalacji, używany we wdrożeniach OEM. Wartość domyślna to **Sysprep**.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*Zainstaluj\_typu*|Określa typ instalacji, używany we wdrożeniach przez producenta OEM|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="OSDisk"></a>Parametr OSDisk  
 Określa dysk, używane do instalowania systemu operacyjnego podczas wdrażania przez producenta OEM. Wartość domyślna to **C:**.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*dysku*|Określa dysk, używane do instalowania systemu operacyjnego podczas wdrażania przez producenta OEM|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="OSDPartitions"></a>OSDPartitions  
 Określa liczbę konfiguracje zdefiniowanych partycji. Maksymalna liczba partycji, które można skonfigurować wynosi dwa. Wartość domyślna to **Brak**.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*partycje*|Określa liczbę zdefiniowanych partycji konfiguracji|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDPartitions=1 OSDPartitions0Bootable=TRUE OSDPartitions0FileSystem=NTFS OSDPartitions0QuickFormat=TRUE OSDPartitions0Size=60 OSDPartitions0SizeUnits=GB OSDPartitions0Type=Primary OSDPartitions0VolumeName=OSDisk OSDPartitions0VolumeLetterVariable=NewDrive1`|  

####  <a name="OSDPartitionsxBootable"></a>OSDPartitionsxBootable  
 Partycja o określonym indeksie powinien być ustawiony rozruchowego. Domyślne pierwszej partycji ustawiono rozruchowego.  

> [!NOTE]
>  *x* w tej właściwości name jest symbolem zastępczym tablicę wartości nieujemnych zawierającą konfiguracje partycji.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|**WARTOŚĆ TRUE**|Partycja powinna być równa rozruchowego.|  
|**WARTOŚĆ FALSE**|Nie ustawiaj partycji rozruchowego.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDPartitions0Bootable=TRUE`|  

####  <a name="OSDPartitionsxFileSystem"></a>OSDPartitionsxFileSystem  
 Typ systemu plików dla partycji o określonym indeksie. Prawidłowe wartości to **NTFS** lub **FAT32**.  

> [!NOTE]
>  *x* w tej właściwości name jest symbolem zastępczym tablicę wartości nieujemnych zawierającą konfiguracje partycji.  

> [!CAUTION]
>  Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*file_system*|Typ systemu plików dla partycji|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDPartitions0FileSystem=NTFS`|  

####  <a name="OSDPartitionsxQuickFormat"></a>OSDPartitionsxQuickFormat  
 Można szybkie formatowanie partycji w określonym indeksie. Wartość domyślna to **TRUE**.  

> [!NOTE]
>  *x* w tej właściwości name jest symbolem zastępczym tablicę wartości nieujemnych zawierającą konfiguracje partycji.  

> [!CAUTION]
>  Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|**WARTOŚĆ TRUE**|Szybkie formatowanie partycji.|  
|**WARTOŚĆ FALSE**|Czy nie szybkie formatowanie partycji.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDPartitions0QuickFormat=TRUE`|  

####  <a name="OSDPartitionsxSize"></a>OSDPartitionsxSize  
 Rozmiar partycji w określonym indeksie.  

> [!NOTE]
>  *x* w tej właściwości name jest symbolem zastępczym tablicę wartości nieujemnych zawierającą konfiguracje partycji.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*Rozmiar*|Rozmiar partycji|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDPartitions0Size=60 OSDPartitions0SizeUnits=GB`|  

####  <a name="OSDPartitionsxSizeUnits"></a>OSDPartitionsxSizeUnits  
 Jednostki miary używana podczas określania rozmiar partycji. Prawidłowe wartości to **MB**, **GB**, lub  **%** . Wartość domyślna to **MB**.  

> [!NOTE]
>  *x* w tej właściwości name jest symbolem zastępczym tablicę wartości nieujemnych zawierającą konfiguracje partycji.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*size_units*|Jednostki miary używana podczas określania rozmiar partycji|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDPartitions0Size=60 OSDPartitions0SizeUnits=GB`|  

####  <a name="OSDPartitionsxType"></a>OSDPartitionsxType  
 Rodzaj partycji, które ma zostać utworzony w określonym indeksie.  

> [!NOTE]
>  *x* w tej właściwości name jest symbolem zastępczym tablicę wartości nieujemnych zawierającą konfiguracje partycji.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|**Podstawowy**|Tworzenie partycji podstawowej. Jest to wartość domyślna.|  
|**Logiczne**|Tworzenie partycji logicznej.|  
|**Rozszerzone**|Utwórz partycję rozszerzoną.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDPartitions0Type=Primary`|  

####  <a name="OSDPartitionsxVolumeLetterVariable"></a>OSDPartitionsxVolumeLetterVariable  
 Właściwość, która odbiera literę dysku przypisaną do partycji zarządzany.  

> [!NOTE]
>  *x* w tej właściwości name jest symbolem zastępczym tablicę wartości nieujemnych zawierającą konfiguracje partycji.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*volume_letter_variable*|Nazwa zmiennej, który zostanie przypisany literą dysku partycji zarządzany|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDPartitions0VolumeLetterVariable=NewDrive1`|  

####  <a name="OSDPartitionsxVolumeName"></a>OSDPartitionsxVolumeName  
 Nazwa woluminu zostanie przypisana do partycji w określonym indeksie.  

> [!NOTE]
>  *x* w tej właściwości name jest symbolem zastępczym tablicę wartości nieujemnych zawierającą konfiguracje partycji.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*volume_name*|Nazwa woluminu, który zostanie przypisany do partycji|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSDPartitions0VolumeName=OSDisk`|  

####  <a name="OSDPreserveDriveLetter"></a>OSDPreserveDriveLetter  
 Ta właściwość jest używana do określenia czy **Zastosuj system operacyjny** krok sekwencji zadań należy zachować litery dysku w pliku obrazu systemu operacyjnego (plik wim) wdrażane na komputerze docelowym.  

> [!NOTE]
>  Tej właściwości należy ustawić, tylko w kroku sekwencji zadań, nie znajduje się w pliku CustomSettings.ini lub w bazie danych zestawu MDT.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI||  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|**WARTOŚĆ TRUE**|Litery dysku w pliku obrazu systemu operacyjnego (plik wim) i systemu operacyjnego dysków litery, po wdrożenia są takie same jak litery dysku w pliku wim.|  
|**WARTOŚĆ FALSE**|Litery dysku w pliku obrazu systemu operacyjnego (plik wim) są ignorowane, co pozwala w sekwencji zadań w celu zastąpienia litery sterownik w pliku wim.<br /><br /> Uwaga:<br /><br /> Dla zestawu MDT zawsze należy wybrać tę wartość.|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="OSDStateStorePath"></a>OSDStateStorePath  
 LTI i ZTI używają tej właściwości można ustawić ścieżki, gdzie będą przechowywane dane migracji stanu użytkownika, może być ścieżką UNC, ścieżkę lokalną lub ścieżkę względną.  

> [!NOTE]
>  **OSDStateStorePath** właściwość ma wyższy priorytet niż [StatePath](#StatePath) lub [UserDataLocation](#UserDataLocation) właściwości, gdy określono też tych właściwości.  

 W scenariuszu wdrażania komputera Zamień w ZTI [Przywróć stan użytkownika](#RestoreUserState) krok sekwencji zadań jest pomijane, jeśli **OSDStateStorePath** właściwości ustawiono prawidłową lokalną lub ścieżkę UNC. Należy ustawić [USMTLocal](#USMTLocal) właściwości na wartość TRUE. Dzięki temu wymusza UserState.wsf ZTI rozpoznać ścieżki [OSDStateStorePath](#OSDStateStorePath) właściwości. Jest to spowodowane **Zażądaj magazynu stanów** zadań sekwencji krok zostanie pominięty i poprzednie wartości w **OSDStateStorePath** właściwości są zachowywane.  

 W scenariuszu wdrażania komputera Zamień w ZTI, w którym dane migracji stanu użytkownika i całego komputera tworzona jest kopia zapasowa, pliku Backup.wim znajduje się w folderze określonym w **OSDStateStorePath** właściwości. Może to być spowodowane przez określenie Nieprawidłowa wartość [ComputerBackupLocation](#ComputerBackupLocation) właściwości.  

 Na przykład następujący plik CustomSettings.ini spowoduje, że plik Backup.wim mają być przechowywane w tym samym folderze, określona w **OSDStateStorePath** właściwości:  

```  
USMTLocal=True  
OSDStateStorePath=\\fs1\Share\Replace  

ComputerBackupLocation=NETWORK  
BackupShare=\\fs1\Share\ComputerBackup  
BackupDir=Client01  
```  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*Ścieżka*|Ścieżka, w którym dane migracji stanu użytkownika będą przechowywane, który może być ścieżką UNC, ścieżkę lokalną lub ścieżkę względną|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] USMTLocal=True OSDStateStorePath=\\fs1\Share\Replace ComputerBackupLocation=\\fs1\Share\ComputerBackup\Client01`|  

####  <a name="OSDTargetSystemDrive"></a>OSDTargetSystemDrive  
 Określa dysk, na którym zainstalowany system operacyjny podczas wdrażania przez producenta OEM.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*dysk_systemowy*|Określa dysk, na którym zainstalowany system operacyjny podczas wdrażania przez producenta OEM|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="OSDTargetSystemRoot"></a>OSDTargetSystemRoot  
 Określa ścieżki instalacji, w której zainstalowany system operacyjny podczas wdrażania przez producenta OEM.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*główny_katalog_systemowy*|Określa ścieżki instalacji, w której zainstalowany system operacyjny podczas wdrażania przez producenta OEM|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="OSFeatures"></a>OSFeatures  
 Rozdzielana przecinkami lista funkcji serwera identyfikatorów, które zostaną zainstalowane na komputerze docelowym.  

> [!NOTE]
>  Nie wszystkie funkcje wymienione w pliku ServerManager.xml są zgodne z wszystkich systemów operacyjnych serwera.  

> [!CAUTION]
>  Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*ID1, ID2*|Funkcje serwera, które mają zostać zainstalowane na komputerze docelowym. Prawidłowe wartości znajdują się w *program_files*\Microsoft Deployment Toolkit\Bin\ServerManager.xml pliku na serwerze zestawu MDT.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSFeatures=CMAK,MSMQ-Multicasting,RSAT`|  

####  <a name="OSInstall"></a>OSInstall  
 Wskazuje, czy komputer docelowy jest autoryzowany do zainstalowanego systemu operacyjnego docelowych. Jeśli **OSInstall** właściwość nie ma na liście, wartość domyślna to, aby umożliwić wdrożenie systemów operacyjnych na dowolny komputer docelowy.  

> [!CAUTION]
>  Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|**TAK**|Wdrożenie systemu operacyjnego do komputera docelowego jest autoryzowany. Jest to wartość domyślna.|  
|**BRAK**|Wdrożenia systemu operacyjnego na komputerze docelowym nie ma uprawnień.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSInstall=YES`|  

####  <a name="OSRoles"></a>OSRoles  
 Rozdzielana przecinkami lista roli serwera identyfikatorów, które zostaną zainstalowane na komputerze docelowym.  

> [!NOTE]
>  Nie wszystkie role są zgodne z wszystkich systemów operacyjnych serwera.  

> [!CAUTION]
>  Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*ID1, ID2*|Rola serwera, który ma zostać zainstalowany na komputerze docelowym.|  

 Nieprawidłowy identyfikator wartości można znaleźć w temacie "C:\Program Files\Microsoft wdrożenia Toolkit\Bin\ServerManager.xml".  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSRoles=ADDS`|  

####  <a name="OSRoleServices"></a>OSRoleServices  
 Rozdzielana przecinkami lista usługi roli Serwer identyfikatorów, które zostaną zainstalowane na komputerze docelowym.  

> [!NOTE]
>  Nie wszystkie roli serwera usługi identyfikatory są zgodne z wszystkich systemów operacyjnych serwera.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*IDENTYFIKATOR*|Usługi roli Serwer, który zostanie zainstalowany na komputerze docelowym. Prawidłowa wartość to:<br /><br /> - **DODAJE Domain-Controller**|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSRoleServices=ADDS-Domain-Controller`|  

####  <a name="OSSKU"></a>OSSKU  
 Wersja aktualnie używanego systemu operacyjnego. Wersja systemu operacyjnego jest określany za pomocą **OperatingSystemSKU** właściwość **Win32_OperatingSystem WMI** klasy. Aby uzyskać listę wersji **OperatingSystemSKU** zwraca właściwości, zobacz sekcję "OperatingSystemSKU," na [klasy Win32_OperatingSystem](http://msdn.microsoft.com/library/windows/desktop/aa394239\(v=vs.85\).aspx).  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*Edition*|Wersja systemu operacyjnego. Na przykład "BUSINESS" Business Edition systemu operacyjnego lub "Przedsiębiorstwa" dla wersji Enterprise systemu operacyjnego.|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="OSVersion"></a>OSVersion  
 Wersja aktualnie używanego systemu operacyjnego. Ta właściwość powinna tylko służyć do wykrywania, jeśli obecnie systemem operacyjnym jest Windows PE. Użyj [OSVersionNumber](#OSVersionNumber) właściwość, aby wykryć innych systemów operacyjnych.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|**Środowiska WinPE**|Windows PE|  
|**2008R2**|Windows Server 2008 R2|  
|**Win7Client**|Windows 7|  
|**Inne**|Systemach operacyjnych innych niż wymienione, łącznie z systemem Windows 8 i Windows Server 2012|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="OSVersionNumber"></a>OSVersionNumber  
 Numer wersji głównej i pomocniczej systemu operacyjnego. Ta właściwość jest wywoływany podczas wdrażania przez producenta OEM.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*numer_wersji*|Numer wersji głównej i pomocniczej systemu operacyjnego|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="OverrideProductKey"></a>OverrideProductKey  
 Ciąg klucza aktywacji wielokrotnej (MAK) do zastosowania po operacyjnego docelowy jest wdrażany na komputerze docelowym. Wartość określona w tej właściwości jest używany przez skrypt ZTILicensing.wsf w fazie przywracania stanu do stosowania klucza MAK do docelowego systemu operacyjnego. Skrypt konfiguruje również obraz licencji woluminu na potrzeby używania aktywacji MAK zamiast usługi zarządzania kluczami (KMS). System operacyjny musi aktywować firmie Microsoft, po zastosowaniu Klucz MAK. Służy to, gdy komputer docelowy nie może uzyskać dostęp do serwera z systemem usługi KMS.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*KLUCZ MAK*|Ciąg klucza MAK do docelowego systemu operacyjnego|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] ProductKey=AAAAA-BBBBB-CCCCC-DDDDD-EEEEE-FFFFF OverrideProductKey=AAAAA-BBBBB-CCCCC-DDDDD-EEEEE-FFFFF`|  

####  <a name="PackageGroup"></a>PackageGroup  
 Listę wartości tekstowych, które kojarzy pracy pakiety systemu ze sobą (zazwyczaj na podstawie typu pakietu systemu operacyjnego). Pakiet systemu operacyjnego można skojarzyć z co najmniej jedną grupę pakietu. **PackageGroup** właściwość umożliwia pakietów systemu operacyjnego w co najmniej jedną grupę w celu wdrażania na komputerze docelowym.  

 Wartości tekstowe na liście może być dowolnym niepustą wartość. **PackageGroup** sufiks numeryczny ma wartość właściwości (na przykład **PackageGroup001** lub **PackageGroup002**). Po jego zdefiniowaniu grupa pakiet jest skojarzony z komputerem. Komputer może być skojarzony z więcej niż jednej grupy pakietu.  

> [!NOTE]
>  Pakiety systemu operacyjnego są tworzone w węźle pakietów systemu operacyjnego w konsoli Deployment Workbench.  

> [!NOTE]
>  **PackageGroup** właściwość może zostać określona w formacie *PackageGroup1 = aktualizacje* lub *PackageGroup001 = aktualizacje*.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*package_group_name*|Nazwa grupy pakietu do wdrażania na komputerze docelowym|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] PackageGroup001=Updates`|  

####  <a name="Packages"></a>Pakiety  
 Lista pakietów programu Configuration Manager do wdrażania na komputerze docelowym. **Pakiety** właściwość ma sufiks numeryczny (na przykład Packages001 lub Packages002).  

> [!NOTE]
>  **PackageGroup** właściwość może zostać określona w formacie *PackageGroup1 = aktualizacje* lub *PackageGroup001 = aktualizacje*.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI||  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*package_id:program_name*|Nazwa pakietu, który ma zostać wdrożone na komputerze docelowym|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] Packages001=NYC00010:Install Packages002=NYC00011:Install`|  

####  <a name="PackageSelectionProfile"></a>PackageSelectionProfile  
 Nazwa profilu jest używane podczas instalowania pakietu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*nazwa_profilu*|Nazwa profilu używane podczas instalacji pakietu aktualizacji|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] PackageSelectionProfile=CoreApplications`|  

####  <a name="Parameters"></a>Parametry  
 Parametry do przekazania do zapytanie bazy danych, które zwraca kolumn w tabeli określonej w wartości właściwości **tabeli** właściwości. Tabela znajduje się w bazie danych określona w **bazy danych** właściwości na komputerze określonym w **SQLServer** właściwości. Wystąpienie programu SQL Server na komputerze jest określona w **wystąpienia** właściwości.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*Parameter1, parameter2*|Lista parametry do przekazania do zapytania bazy danych|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Computers, Default  [Default] OSInstall=YES  [Computers] SQLServer=NYC-SQL-01 SQLShare=SQL$ Database=MDTDB Instance=SQLEnterprise2005 Table=Computers Parameters=SerialNumber, AssetTag ParameterCondition=OR`|  

####  <a name="ParameterCondition"></a>ParameterCondition  
 Wskazuje, czy wartość logiczną i lub lub operacja jest wykonywana na liście właściwości **parametry** właściwości.  

> [!CAUTION]
>  Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|**I**|Operacji logicznych i odbywa się na liście właściwości **parametry** właściwości. Tylko wyniki pasujące wszystkie właściwości określone w **parametry** właściwości są zwracane. Jest to wartość domyślna.|  
|**LUB**|Operacja logiczna lub odbywa się na liście właściwości **parametry** właściwości. Wyniki, które pasuje do żadnej właściwości określony w **parametry** właściwości są zwracane.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Computers, Default  [Default] OSInstall=YES  [Computers] SQLServer=NYC-SQL-01 SQLShare=SQL$ Database=MDTDB Instance=SQLEnterprise2005 Table=Computers Parameters=SerialNumber, AssetTag ParameterCondition=OR`|  

####  <a name="ParentDomainDNSName"></a>ParentDomainDNSName  
 Określa nazwę domeny DNS w istniejącej domeny usługi directory podczas instalowania domeny podrzędnej.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*Nazwa*|Określa nazwę domeny DNS w istniejącej domeny usługi directory podczas instalowania domeny podrzędnej|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] ParentDomainDNSName=WoodGroveBank.com`|  

####  <a name="Password"></a>Hasło  
 Określa hasło dla nazwy użytkownika (poświadczenia konta) do użycia podczas podwyższania poziomu serwera członkowskiego do kontrolera domeny.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*hasło*|Określa hasło dla nazwy użytkownika (poświadczenia konta) do użycia podczas podwyższania poziomu serwera członkowskiego do kontrolera domeny|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] Password=<complex_password>`|  

####  <a name="Phase"></a>Faza  
 Bieżący etap procesu wdrażania. Zadania program Sequencer używa tych fazach, aby określić, zadania, które należy wykonać.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

> [!CAUTION]
>  Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|**SPRAWDZANIE POPRAWNOŚCI**|Określa, czy komputer docelowy ma możliwość uruchamiania skryptów niezbędne do ukończenia procesu wdrażania.|  
|**STATECAPTURE**|Zapisuje wszystkie dane migracji stanu użytkownika przed wdrożeniem nowego docelowego systemu operacyjnego.|  
|**PREINSTALACJI**|Wykonuje wszelkie zadania, które muszą być przeprowadzone (takich jak tworzenie nowych partycji), przed wdrożeniem docelowego systemu operacyjnego.|  
|**ZAINSTALUJ**|Instaluje docelowy system operacyjny na komputerze docelowym.|  
|**WYKONYWANE**|Wykonuje wszelkie zadania, które należy wykonać przed przywróceniem danych migracji stanu użytkownika. Te zadania dostosować docelowego systemu operacyjnego, przed rozpoczęciem docelowy czas pierwszego komputera (na przykład instalowanie aktualizacji lub dodawanie sterowników).|  
|**STATERESTORE**|Przywraca dane migracji stanu użytkownika zapisane w fazie przechwytywania stanu.|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="Port"></a>Port  
 Numer portu, który ma być używany podczas nawiązywania połączenia z wystąpienie bazy danych programu SQL Server, które jest używane dla zapytania dotyczącego właściwości wartości z kolumn w tabeli określonej w **tabeli** właściwości. Baza danych znajduje się na komputerze określonym w **SQLServer** właściwości. Wystąpienie programu SQL Server na komputerze jest określona w **wystąpienia** właściwości. Port używany podczas połączenia jest określona w **portu** właściwości.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*Port*|Numer portu używany podczas nawiązywania połączenia z programem SQL Server|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Computers, Default  [Default] OSInstall=YES  [Computers] SQLServer=NYC-SQL-01 Database=MDTDB Instance=MDT2010 Port=1433 Table=Computers Parameters=SerialNumber, AssetTag ParameterCondition=OR`|  

####  <a name="PowerUsers"></a>Użytkownicy zaawansowani  
 Listę kont użytkowników i grup domeny, które mają zostać dodane do lokalnej grupy Użytkownicy zaawansowani na komputerze docelowym. **Użytkownicy zaawansowani** właściwości znajduje się lista wartości tekstowych, które mogą być dowolnego niepustą wartość. **Użytkownicy zaawansowani** właściwość ma sufiks numeryczny (na przykład **PowerUsers1** lub **PowerUsers2**).  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*Nazwa*|Nazwa użytkownika lub grupy, które mają zostać dodane do lokalnej grupy Użytkownicy zaawansowani|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] Administrators001=WOODGROVEBANK\NYC Help Desk Staff PowerUsers001=WOODGROVEBANK\User01 PowerUsers002=WOODGROVEBANK\User02`|  

####  <a name="PrepareWinRE"></a>PrepareWinRE  
 Ta właściwość określa, czy plik LiteTouchPE.wim, który zawiera środowiska Windows RE, opcjonalnie DaRT, została zastosowana na dysk systemowy jako partycja odzyskiwania. Dzięki temu komputer docelowy, aby użyć obrazu LiteTouchPE.wim do wykonywania zadań odzyskiwania. DaRT może opcjonalnie obejmować obrazu, który udostępnia funkcje odzyskiwania DaRT na komputerze docelowym.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|TAK|Plik LiteTouchPE.wim, który zawiera środowiska Windows RE, opcjonalnie DaRT, jest stosowany do dysku systemowego jako partycja odzyskiwania.|  
|*Dowolna inna wartość*|Plik LiteTouchPE.wim, który zawiera środowiska Windows RE, opcjonalnie DaRT, nie ma zastosowania do dysku systemowego jako partycja odzyskiwania. Jest to wartość domyślna.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] PrepareWinRE=YES`|  

####  <a name="Priority"></a>Priorytet  
 Właściwości zastrzeżone określa kolejność wyszukiwania wartości konfiguracji. **Priorytet** zarezerwowanej właściwości wymieniono każdej sekcji do wyszukania i kolejność, w którym są przeszukiwane sekcji. Po znalezieniu wartość właściwości skryptu ZTIGather.wsf kończy wyszukiwanie właściwości, a pozostałe sekcje nie są skanowane pod kątem tej właściwości.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*sekcja 1 Sekcja2*|Sekcje, które mają być wyszukiwane w kolejności, które mają być wyszukiwane|  

|**Przykład**|  
|-|  
|`[Settings] Priority=MACAddress, Default  [Default] UserDataLocation=NONE CustomProperty=TRUE  [00:0F:20:35:DE:AC] OSDNEWMACHINENAME=HPD530-1  [00:03:FF:FE:FF:FF] OSDNEWMACHINENAME=BVMXP`|  

####  <a name="ProcessorSpeed"></a>ProcessorSpeed  
 Szybkość procesora zainstalowanego na komputerze docelowym w MHz. Na przykład wartość **1995 r.** wskazuje procesora na komputerze docelowym jest uruchomiona na 1,995 MHz lub 2 GHz.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*processor_speed*|Szybkość procesora na komputerze docelowym w megahercach|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="Product"></a>Produktu  
 Nazwa produktu z komputerem docelowym. Z niektórych dostawców komputera marka i model może nie być wystarczająco unikatowy do identyfikowania właściwości określoną konfigurację (na przykład hyperthreaded lub z systemem innym niż hyperthreaded mikroukłady). **Produktu** właściwości ułatwiają odróżnienie.  

 Format **produktu** jest niezdefiniowana. Ta właściwość służy do tworzenia podsekcji, zawierający ustawienia nazwę określonego produktu numeru modelu określonego komputera od producenta komputerów w określonym celem (najczęściej w połączeniu z **upewnij** i **Modelu** właściwości).  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*produktu*|Nazwa produktu, komputera docelowego|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="ProductKey"></a>Klucz produktu  
 Ciąg klucza produktu można skonfigurować dla komputera docelowego. Przed wdrożeniem docelowy system operacyjny podany klucz produktu jest automatycznie wstawiana do odpowiednich lokacji w pliku Unattend.xml.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*klucz_produktu*|Klucz produktu, który ma być przypisany do komputera docelowego|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] ProductKey=AAAAA-BBBBB-CCCCC-DDDDD-EEEEE-FFFFF`|  

####  <a name="Properties"></a>Właściwości  
 Właściwości zastrzeżone, która definiuje żadnych właściwości niestandardowych, definiowanych przez użytkownika. Te właściwości zdefiniowane przez użytkownika znajdują się za pomocą skryptu ZTIGather.wsf w pliku CustomSettings.ini, pliku BootStrap.ini lub DB zestawu MDT. Te właściwości są dodatki do wstępnie zdefiniowanych właściwości w zestawie MDT.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*custom_property1,*custom_property2|Właściwości niestandardowych, definiowanych przez użytkownika można rozpoznać|  

|**Przykład**|  
|-|  
|`[Settings] Priority=MACAddress, Default Properties=CustomProperty, ApplicationInstall  [Default] OSInstall=YES ScanStateArgs=/v:5 /o /c LoadStateArgs=/v:5 /c /lac UserDataLocation=NONE CustomProperty=TRUE  [00:0F:20:35:DE:AC] OSDNEWMACHINENAME=HPD530-1 ApplicationInstall=Custom  [00:03:FF:FE:FF:FF] OSDNEWMACHINENAME=BVMXP ApplicationInstall=Minimum`|  

####  <a name="ReplicaDomainDNSName"></a>ReplicaDomainDNSName  
 Określa nazwę domeny DNS domeny do replikacji.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*Nazwa*|Określa nazwę domeny DNS domeny do replikacji|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] ReplicaDomainDNSName=WoodGroveBank.com`|  

####  <a name="ReplicaOrNewDomain"></a>ReplicaOrNewDomain  
 Określa, czy do zainstalowania nowego kontrolera domeny jako pierwszego kontrolera domeny w nowej domenie usługi katalogowej lub zainstalować ją jako repliki kontrolera domeny usługi katalogu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|**Repliki**|Nowy kontroler domeny jest instalowany jako repliki kontrolera domeny usługi katalogu.|  
|**Domeny**|Nowy kontroler domeny jest instalowany jako pierwszego kontrolera domeny w nowej domenie usługi katalogowej. Należy określić **TreeOrChild** wpis o prawidłowej wartości.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] ReplicaOrNewDomain=Domain`|  

####  <a name="ReplicationSourceDC"></a>ReplicationSourceDC  
 Określa pełną nazwę DNS kontrolera domeny, z którego są replikowane informacje o domenie.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*Nazwa*|Określa pełną nazwę DNS kontrolera domeny, z którego są replikowane informacje o domenie|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] ReplicationSourceDC=dc01.WoodGroveBank.com`|  

####  <a name="ResourceDrive"></a>ResourceDrive  
 Litera dysku mapowana na **ResourceRoot** właściwości ZTIDrivers.wsf i ZTIPatches.wsf skryptów na potrzeby instalowania sterowników i poprawek do komputera docelowego.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*litera_dysku*|Przypisanie litery dysku logicznego, który zawiera zasoby|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="ResourceRoot"></a>ResourceRoot  
 Wartość tej właściwości jest używany przez skrypty ZTIDrivers.wsf i ZTIPatches.wsf do instalowania sterowników i poprawek do komputera docelowego.  

> [!NOTE]
>  Dla LTI, automatyczne ustawienie skrypty **ResourceRoot** właściwość, aby być taka sama jak **DeployRoot** właściwości. Dla ZTI, wartości w **DeployRoot** i **ResourceRoot** właściwości mogą być unikatowe.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*UNC_path*|Ścieżka UNC do folderu udostępnionego, który zawiera zasoby|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceDrive=R: ResourceRoot=\\NYC-AM-FIL-01\Resource$ UserDataLocation=NONE`|  

####  <a name="Role"></a>Rola  
 Cel komputera, na podstawie zadań wykonywanych przez użytkownika na komputerze docelowym. **Roli** właściwość listę wartości tekstowych, które mogą być dowolnego niepustą wartość. **Roli** sufiks numeryczny ma wartość właściwości (na przykład **Role1** lub **Role2**). Po zdefiniowaniu roli jest skojarzony z komputerem. Komputer może działać więcej niż jednej roli.  

 Zazwyczaj wartość **roli** właściwość jest ustawiona, wykonując zapytanie bazy danych w bazie danych zestawu MDT. Konsoli Deployment Workbench może pomóc w tworzeniu ustawienia roli i właściwości skojarzone z rolą, a następnie skonfiguruj CustomSettings.ini do przeprowadzenia kwerendy bazy danych dla konsoli Deployment Workbench **roli** właściwość i ustawienia właściwości skojarzone z rolą.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*Rola*|Role do przypisania do pojedynczego komputera lub grupy komputerów|  

|**Przykład 1**|  
|-|  
|`[Settings] Priority=RoleSettings, Default  [Default] SkipCapture=NO UserDataLocation=AUTO DeployRoot=\\W2K3-SP1\Distribution$ OSInstall=YES ScanStateArgs=/v:15 /o /c LoadStateArgs=/v:7 /c  [RoleSettings] SQLServer=w2k3-sp1 Instance=MDT2010 Database=MDTDB Netlib=DBNMPNTW SQLShare=SQL_Share Table=RoleSettings Parameters=Role`|  

|**Przykład 2**|  
|-|  
|`[Settings] Priority=RoleSettings, Default  [Default] SkipCapture=NO UserDataLocation=AUTO DeployRoot=\\W2K3-SP1\Distribution$ OSInstall=YES Role1=Teller Role2=Woodgrove User  [RoleSettings] SQLServer=w2k3-sp1 Instance=MDT2010 Database=MDTDB Netlib=DBNMPNTW SQLShare=SQL_Share Table=RoleSettings Parameters=Role`|  

####  <a name="SafeModeAdminPassword"></a>SafeModeAdminPassword  
 Określa hasło dla konta administratora podczas uruchamiania komputera w trybie awaryjnym lub w wariancie trybu awaryjnego, takim jak tryb przywracania usług katalogowych.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*hasło*|Określa hasło dla konta administratora podczas uruchamiania komputera w trybie awaryjnym lub w wariancie trybu awaryjnego, takim jak tryb przywracania usług katalogowych|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] SafeModeAdminPassword=<complex_password>`|  

####  <a name="ScanStateArgs"></a>ScanStateArgs  
 Argumenty przekazywane do **USMT Scanstate** procesu. Skrypty wywołania Scanstate.exe, a następnie Włóż odpowiedni rejestrowania postępu i parametry magazynu stanu. Jeśli ta wartość nie jest uwzględniony w pliku ustawień, proces tworzenia kopii zapasowej stanu użytkownika zostało pominięte.  

> [!NOTE]
>  Użyj **USMTMigFiles** właściwości w celu określenia plików XML, który ma być używany przez Scanstate.exe zamiast za pomocą parametru /I w **ScanStateArgs** właściwości. Uniemożliwia to skrypt ZTIUserState.wsf potencjalnie duplikowania tę samą listę plików XML.  

> [!NOTE]
>  Nie dodawaj żadnego z następujących argumentów wiersza polecenia podczas konfigurowania tej właściwości: **/hardlink**, **/nocompress**, **/ encrypt**, **następujący/key**, lub **/KeyFile**. Skrypty zestawu MDT zostaną dodane następujące argumenty wiersza polecenia, gdy mają zastosowanie do bieżącego scenariusza wdrażania.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*argumenty*|Argumenty wiersza polecenia przekazywane do Scanstate.exe.<br /><br /> Argumenty domyślne określone przez konsoli Deployment Workbench są następujące:<br /><br /> - **/v**. Włącza pełne dane wyjściowe w dzienniku Scanstate. Wartość domyślna to **0**. Określić dowolną liczbę z zakresu od 0 do 15. Wartość **5** umożliwia pełne i dane wyjściowe stanu.<br /><br /> - **/o**. Zastępuje wszystkie istniejące dane w magazynie. Jeśli nie zostanie określony, Scanstate zakończy się niepowodzeniem, jeśli magazyn zawiera już dane. Ta opcja nie można określić więcej niż raz w oknie wiersza polecenia.<br /><br /> -                             **/c**. W przypadku Scanstate będzie nadal działać, nawet jeśli istnieją błędy niekrytyczne. Bez **/c** opcji Scanstate opuszcza pierwszego błędu.<br /><br /> Aby uzyskać więcej informacji na temat tych i innych argumentów Zobacz pliki pomocy narzędzia USMT.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] ScanStateArgs=/v:5 /o /c LoadStateArgs=/v:5 /c /lac DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ UDDir=%OSDComputerName%`|  

####  <a name="SerialNumber"></a>Numer seryjny  
 Numer seryjny komputera docelowego. Format numery seryjne jest niezdefiniowana. Ta właściwość służy do tworzenia podsekcji, zawierający ustawienia przeznaczone dla określonego komputera.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*numer_seryjny*|Format numer seryjny nie jest zdefiniowana i jest określane przez numer seryjny standardów każdego producenta komputerów.|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="SiteName"></a>Nazwa witryny  
 Określa nazwę istniejącej witryny lokalizację nowego kontrolera domeny.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*Nazwa*|Określa nazwę istniejącej witryny lokalizację nowego kontrolera domeny|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] SiteName=FirstSite`|  

####  <a name="SkipAdminAccounts"></a>SkipAdminAccounts  
 Wskazuje, czy **Administratorzy lokalni** stronie kreatora zostanie pominięty.  

> [!NOTE]
>  Jest to wartość domyślna dla tej właściwości **tak**, co oznacza, że **Administratorzy lokalni** stronie kreatora zostanie pominięta domyślnie. Do wyświetlania tej strony kreatora, w szczególności musi ustawić wartość tej właściwości, aby **nr** CustomSettings.ini lub w bazie danych zestawu MDT.  

 Dla innych właściwości, które można skonfigurować, ta właściwość jest ustawiona na **tak**, zobacz [dostarczanie właściwości pominięte stron Kreatora wdrażania](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!CAUTION]
>  Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|**TAK**|Strona kreatora nie jest wyświetlana, i nie są zbierane informacje na tej stronie. Jest to wartość domyślna.|  
|**BRAK**|Zostanie wyświetlona strona kreatora i zbieranych informacjach na tej stronie.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipAdminAccounts=NO SkipAdminPassword=NO SkipApplications=NO SkipComputerBackup=NO SkipDomainMembership=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO SkipProductKey=YES`|  

####  <a name="SkipAdminPassword"></a>SkipAdminPassword  
 Wskazuje, czy **hasło administratora** stronie kreatora zostanie pominięty.  

 Dla innych właściwości, które można skonfigurować, ta właściwość jest ustawiona na **tak**, zobacz [dostarczanie właściwości pominięte stron Kreatora wdrażania](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!CAUTION]
>  Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|**TAK**|Strona kreatora nie jest wyświetlana, i nie są zbierane informacje na tej stronie.|  
|**BRAK**|Zostanie wyświetlona strona kreatora i zbieranych informacjach na tej stronie. Jest to wartość domyślna.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipAdminPassword=YES SkipApplications=NO SkipComputerBackup=NO SkipDomainMembership=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO SkipProductKey=YES`|  

####  <a name="SkipApplications"></a>SkipApplications  
 Wskazuje, czy **zaznacz jedną lub więcej aplikacji, aby zainstalować** stronie kreatora zostanie pominięty.  

 Dla innych właściwości, które można skonfigurować, ta właściwość jest ustawiona na **tak**, zobacz [dostarczanie właściwości pominięte stron Kreatora wdrażania](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!CAUTION]
>  Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|**TAK**|Strona kreatora nie jest wyświetlana, i nie są zbierane informacje na tej stronie.|  
|**BRAK**|Zostanie wyświetlona strona kreatora i zbieranych informacjach na tej stronie. Jest to wartość domyślna.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipAdminPassword=NO SkipApplications=YES SkipComputerBackup=NO SkipDomainMembership=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO SkipProductKey=YES`|  

####  <a name="SkipBDDWelcome"></a>SkipBDDWelcome  
 Wskazuje, czy **wdrażania systemu Windows — Zapraszamy** stronie kreatora zostanie pominięty.  

 Dla innych właściwości, które można skonfigurować, ta właściwość jest ustawiona na **tak**, zobacz [dostarczanie właściwości pominięte stron Kreatora wdrażania](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!NOTE]
>  Dla tej właściwości funkcji prawidłowo należy go skonfigurować zarówno CustomSettings.ini, jak i BootStrap.ini. BootStrap.ini są przetwarzane przed wybrano udział wdrożenia (zawierający CustomSettings.ini).  

> [!CAUTION]
>  Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|**TAK**|Strona kreatora nie jest wyświetlana, i nie są zbierane informacje na tej stronie.|  
|**BRAK**|Zostanie wyświetlona strona kreatora i zbieranych informacjach na tej stronie. Jest to wartość domyślna.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipAdminPassword=YES SkipApplications=NO SkipBDDWelcome=YES SkipComputerBackup=NO SkipDomainMembership=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO SkipProductKey=YES`|  

####  <a name="SkipBitLocker"></a>SkipBitLocker  
 Wskazuje, czy **będzie określić konfigurację funkcji BitLocker** stronie kreatora zostanie pominięty.  

 Dla innych właściwości, które można skonfigurować, ta właściwość jest ustawiona na **tak**, zobacz [dostarczanie właściwości pominięte stron Kreatora wdrażania](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!CAUTION]
>  Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|**TAK**|Strona kreatora nie jest wyświetlana, i nie są zbierane informacje na tej stronie.|  
|**BRAK**|Zostanie wyświetlona strona kreatora i zbieranych informacjach na tej stronie. Jest to wartość domyślna.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipApplications=NO SkipBDDWelcome=YES SkipBitLocker=YES SkipComputerBackup=NO SkipDomainMembership=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO`|  

####  <a name="SkipBuild"></a>SkipBuild  
 Wskazuje, czy **wybierz sekwencję zadań do wykonania na tym komputerze** stronie kreatora zostanie pominięty.  

 Dla innych właściwości, które można skonfigurować, ta właściwość jest ustawiona na **tak**, zobacz [dostarczanie właściwości pominięte stron Kreatora wdrażania](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

 Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|**TAK**|Strona kreatora nie jest wyświetlana, i nie są zbierane informacje na tej stronie.|  
|**BRAK**|Zostanie wyświetlona strona kreatora i zbieranych informacjach na tej stronie. Jest to wartość domyślna.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipAdminPassword=YES SkipApplications=NO SkipBDDWelcome=YES SkipBuild=YES SkipComputerBackup=NO SkipComputerName=NO SkipDomainMembership=NO SkipFinalSummary=NO SkipSummary=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO`|  

####  <a name="SkipCapture"></a>SkipCapture  
 Wskazuje, czy **Określ, czy do przechwycenia obrazu** stronie kreatora zostanie pominięty.  

 Dla innych właściwości, które można skonfigurować, ta właściwość jest ustawiona na **tak**, zobacz [dostarczanie właściwości pominięte stron Kreatora wdrażania](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!CAUTION]
>  Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|**TAK**|Ta strona kreatora nie jest wyświetlana, a nie są zbierane informacje na tej stronie.|  
|**BRAK**|Ta strona kreatora jest wyświetlana, a zbierane są informacje na tej stronie. Jest to wartość domyślna.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=YES SkipApplications=NO SkipComputerBackup=NO SkipDomainMembership=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO`|  

####  <a name="SkipComputerBackup"></a>SkipComputerBackup  
 Wskazuje, czy **Określ, gdzie chcesz zapisać kopię zapasową komputera pełną** stronie kreatora zostanie pominięty.  

 Dla innych właściwości, które można skonfigurować, ta właściwość jest ustawiona na **tak**, zobacz [dostarczanie właściwości pominięte stron Kreatora wdrażania](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!CAUTION]
>  Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|**TAK**|Ta strona kreatora nie jest wyświetlana, a nie są zbierane informacje na tej stronie.|  
|**BRAK**|Ta strona kreatora jest wyświetlana, a zbierane są informacje na tej stronie. Jest to wartość domyślna.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipAdminPassword=NO SkipApplications=NO SkipComputerBackup=YES SkipDomainMembership=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO`|  

####  <a name="SkipComputerName"></a>SkipComputerName  
 Wskazuje, czy **skonfiguruj nazwę komputera** stronie kreatora zostanie pominięty.  

 Dla innych właściwości, które można skonfigurować, ta właściwość jest ustawiona na **tak**, zobacz [dostarczanie właściwości pominięte stron Kreatora wdrażania](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!CAUTION]
>  Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|**TAK**|Strona kreatora nie jest wyświetlana, i nie są zbierane informacje na tej stronie.|  
|**BRAK**|Zostanie wyświetlona strona kreatora i zbieranych informacjach na tej stronie. Jest to wartość domyślna.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipAdminPassword=NO SkipApplications=NO SkipComputerBackup=NO SkipComputerName=YES SkipDomainMembership=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO`|  

####  <a name="SkipDomainMembership"></a>SkipDomainMembership  
 Wskazuje, czy **przyłączyć komputer do domeny lub grupy roboczej** stronie kreatora zostanie pominięty.  

 Dla innych właściwości, które można skonfigurować, ta właściwość jest ustawiona na **tak**, zobacz [dostarczanie właściwości pominięte stron Kreatora wdrażania](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!CAUTION]
>  Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|**TAK**|Ta strona kreatora nie jest wyświetlana, a nie są zbierane informacje na tej stronie.|  
|**BRAK**|Ta strona kreatora jest wyświetlana, a zbierane są informacje na tej stronie. Jest to wartość domyślna.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipAdminPassword=NO SkipApplications=NO SkipComputerBackup=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO SkipDomainMembership=NO`|  

####  <a name="SkipFinalSummary"></a>SkipFinalSummary  
 Wskazuje, czy **wdrożenia systemu operacyjnego została ukończona pomyślnie** stronie kreatora zostanie pominięty.  

 Dla innych właściwości, które można skonfigurować, ta właściwość jest ustawiona na **tak**, zobacz [dostarczanie właściwości pominięte stron Kreatora wdrażania](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!NOTE]
>  Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|**TAK**|Ta strona kreatora nie jest wyświetlana, a nie są zbierane informacje na tej stronie.|  
|**BRAK**|Ta strona kreatora jest wyświetlana, a zbierane są informacje na tej stronie. Jest to wartość domyślna.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipApplications=NO SkipBDDWelcome=YES SkipComputerBackup=NO SkipComputerName=NO SkipDomainMembership=NO SkipFinalSummary=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO SkipProductKey=YES`|  

####  <a name="SkipGroupSubFolders"></a>SkipGroupSubFolders  
 Domyślnie podczas określania foldery do uwzględnienia podczas wstrzyknięcie sterowniki, poprawki \(pakiety\)i tak dalej wartości są określane coś, takich jak:  

```  
DriverGroup001=TopFolder\SecondFolder  
PackageGroup001=TopFolder\SecondFolder  
```  

 To domyślnie obejmuje również wszystkie sub\-folderów znajdujących się w obszarze "SecondFolder." Jeśli **SkipGroupSubFolders** ustawiono **tak** w CustomSettings.ini, zmień będzie to zachowanie, tak aby podfoldery zostaną wykluczone, i tylko zawartość "SecondFolder" zostanie dodany.  

 Aby wykluczyć podfoldery podczas dopasowywania dla grup, takich jak DriverGroup001, PackageGroup001 i tak dalej, ustaw **SkipGroupSubFolders** do **tak**.  

> [!CAUTION]
>  Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|**TAK**|Nie dołączaj podfoldery podczas dopasowywania względem grupy.|  
|**BRAK**|Uwzględnij podfoldery podczas dopasowywania względem grupy. Jest to zachowanie domyślne.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipGroupSubFolders=NO`|  

####  <a name="SkipLocaleSelection"></a>SkipLocaleSelection  
 Wskazuje, czy **ustawienia regionalne zaznaczenia** stronie kreatora zostanie pominięty.  

 Dla innych właściwości, które można skonfigurować, ta właściwość jest ustawiona na **tak**, zobacz [dostarczanie właściwości pominięte stron Kreatora wdrażania](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!CAUTION]
>  Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|**TAK**|Ta strona kreatora nie jest wyświetlana, a nie są zbierane informacje na tej stronie.|  
|**BRAK**|Ta strona kreatora jest wyświetlana, a zbierane są informacje na tej stronie. Jest to wartość domyślna.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipApplications=NO SkipComputerBackup=NO SkipDomainMembership=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO`|  

####  <a name="SkipPackageDisplay"></a>SkipPackageDisplay  
 Wskazuje, czy **pakiety** stronie kreatora zostanie pominięty.  

 Dla innych właściwości, które można skonfigurować, ta właściwość jest ustawiona na **tak**, zobacz [dostarczanie właściwości pominięte stron Kreatora wdrażania](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!CAUTION]
>  Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|**TAK**|Ta strona kreatora nie jest wyświetlana, a nie są zbierane informacje na tej stronie.|  
|**BRAK**|Ta strona kreatora jest wyświetlana, a zbierane są informacje na tej stronie. Jest to wartość domyślna.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipApplications=NO SkipComputerBackup=NO SkipDomainMembership=NO SkipUserData=NO SkipPackageDisplay=YES SkipLocaleSelection=NO`|  

####  <a name="SkipProductKey"></a>SkipProductKey  
 Wskazuje, czy **Określ potrzebnych do zainstalowania tego systemu operacyjnego klucz produktu** stronie kreatora zostanie pominięty.  

 Dla innych właściwości, które można skonfigurować, ta właściwość jest ustawiona na **tak**, zobacz [dostarczanie właściwości pominięte stron Kreatora wdrażania](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!CAUTION]
>  Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|**TAK**|Ta strona kreatora nie jest wyświetlana, a nie są zbierane informacje na tej stronie.|  
|**BRAK**|Ta strona kreatora jest wyświetlana, a zbierane są informacje na tej stronie. Jest to wartość domyślna.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipAdminPassword=YES SkipApplications=NO SkipComputerBackup=NO SkipDomainMembership=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO SkipProductKey=YES`|  

####  <a name="SkipRearm"></a>SkipRearm  
 Ta właściwość jest używana, aby określić, czy zestaw MDT rearms Microsoft Office 2010 25\-dniowy okres prolongaty aktywacji. Jeśli w niestandardowego obrazu przechwytywania pakietu Microsoft Office 2010, zostanie wyświetlona okno dialogowe powiadomień aktywacji natychmiast po wdrożeniu obrazu zamiast 25\-dni po wdrożeniu.  

 Domyślnie zestaw MDT rearms Microsoft Office 2010 25\-czasu podczas uruchamiania skryptu LTISysprep.wsf prolongaty aktywacji dnia. Można ustawić wartość tej właściwości, aby **tak** tak, aby zestaw MDT pomija rearming Microsoft Office 2010 25\-dniowy okres prolongaty aktywacji.  

> [!CAUTION]
>  Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|**TAK**|Zestaw MDT nie rearm Microsoft Office 2010 25\-dniowy okres prolongaty aktywacji.|  
|**BRAK**|Zestaw MDT rearms Microsoft Office 2010 25\-dniowy okres prolongaty aktywacji. Jest to wartość domyślna.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSInstall=Y SkipCapture=YES SkipAdminPassword=NO SkipProductKey=YES SkipRearm=YES DoCapture=YES`|  

####  <a name="SkipRoles"></a>SkipRoles  
 Wskazuje, czy **role i funkcje** stronie kreatora zostanie pominięty.  

 Dla innych właściwości, które można skonfigurować, ta właściwość jest ustawiona na **tak**, zobacz [dostarczanie właściwości pominięte stron Kreatora wdrażania](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!CAUTION]
>  Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|**TAK**|Ta strona kreatora nie jest wyświetlana, a nie są zbierane informacje na tej stronie.|  
|**BRAK**|Ta strona kreatora jest wyświetlana, a zbierane są informacje na tej stronie. Jest to wartość domyślna.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipAdminPassword=YES SkipApplications=NO SkipBDDWelcome=YES SkipTaskSequence=Yes SkipComputerBackup=NO SkipComputerName=NO SkipDomainMembership=NO SkipFinalSummary=NO SkipRoles=YES SkipSummary=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO`|  

####  <a name="SkipSummary"></a>SkipSummary  
 Wskazuje, czy **gotowy do rozpoczęcia** stronie kreatora zostanie pominięty.  

 Dla innych właściwości, które można skonfigurować, ta właściwość jest ustawiona na **tak**, zobacz [dostarczanie właściwości pominięte stron Kreatora wdrażania](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!CAUTION]
>  Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|**TAK**|Ta strona kreatora nie jest wyświetlana, a nie są zbierane informacje na tej stronie.|  
|**BRAK**|Ta strona kreatora jest wyświetlana, a zbierane są informacje na tej stronie. Jest to wartość domyślna.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipAdminPassword=YES SkipApplications=NO SkipBDDWelcome=YES SkipTaskSequence=Yes SkipComputerBackup=NO SkipComputerName=NO SkipDomainMembership=NO SkipFinalSummary=NO SkipSummary=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO`|  

####  <a name="SkipTaskSequence"></a>SkipTaskSequence  
 Wskazuje, czy **wybierz sekwencję zadań do wykonania na tym komputerze** stronie kreatora zostanie pominięty.  

 Dla innych właściwości, które można skonfigurować, ta właściwość jest ustawiona na **tak**, zobacz [dostarczanie właściwości pominięte stron Kreatora wdrażania](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!NOTE]
>  Określ **SkipBuild** właściwości, korzystając z konsoli Deployment Workbench można skonfigurować Kreatora wdrażania, aby pominąć **wybierz sekwencję zadań do wykonania na tym komputerze** strony kreatora.  

> [!CAUTION]
>  Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|**TAK**|Ta strona kreatora nie jest wyświetlana, a nie są zbierane informacje na tej stronie.|  
|**BRAK**|Ta strona kreatora jest wyświetlana, a zbierane są informacje na tej stronie. Jest to wartość domyślna.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipApplications=NO SkipBDDWelcome=YES SkipTaskSequence=NO SkipComputerBackup=NO SkipComputerName=NO SkipDomainMembership=NO SkipFinalSummary=NO SkipSummary=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO`|  

####  <a name="SkipTimeZone"></a>SkipTimeZone  
 Wskazuje, czy **Ustaw strefę czasową** stronie kreatora zostanie pominięty.  

 Dla innych właściwości, które można skonfigurować, ta właściwość jest ustawiona na **tak**, zobacz [dostarczanie właściwości pominięte stron Kreatora wdrażania](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!CAUTION]
>  Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|**TAK**|Ta strona kreatora nie jest wyświetlana, a nie są zbierane informacje na tej stronie.|  
|**BRAK**|Ta strona kreatora jest wyświetlana, a zbierane są informacje na tej stronie. Jest to wartość domyślna.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipAdminPassword=YES SkipApplications=NO SkipBDDWelcome=YES SkipTaskSequence=YES SkipComputerBackup=NO SkipComputerName=NO SkipDomainMembership=NO SkipFinalSummary=NO SkipSummary=NO SkipTimeZone=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO`|  

####  <a name="SkipUserData"></a>SkipUserData  
 Wskazuje, czy **Określ, czy przywrócenia danych użytkownika** i **Określanie lokalizacji zapisu danych i ustawień** stronie kreatora zostanie pominięty.  

 Dla innych właściwości, które można skonfigurować, ta właściwość jest ustawiona na **tak**, zobacz [dostarczanie właściwości pominięte stron Kreatora wdrażania](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!CAUTION]
>  Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|**TAK**|Ta strona kreatora nie jest wyświetlana, a nie są zbierane informacje na tej stronie.|  
|**BRAK**|Ta strona kreatora jest wyświetlana, a zbierane są informacje na tej stronie. Jest to wartość domyślna.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=NO SkipCapture=NO SkipAdminPassword=YES SkipApplications=NO SkipComputerBackup=NO SkipDomainMembership=NO SkipUserData=NO SkipPackageDisplay=NO SkipLocaleSelection=NO SkipProductKey=YES`|  

####  <a name="SkipWizard"></a>SkipWizard  
 Wskazuje, czy cały **Kreatora wdrażania** zostanie pominięta.  

 Dla innych właściwości, które można skonfigurować, ta właściwość jest ustawiona na **tak**, zobacz [dostarczanie właściwości pominięte stron Kreatora wdrażania](#ProvidingPropertiesforSkippedDeploymentWizardPages).  

> [!CAUTION]
>  Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|**TAK**|Cały kreatora nie jest wyświetlana, i nie są zbierane żadne informacje na kolejnych stronach kreatora.|  
|**BRAK**|Zostanie wyświetlony Kreator, a zbierane są informacje na kolejnych stronach kreatora włączone. Jest to wartość domyślna.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] SkipWizard=YES`|  

####  <a name="SLShare"></a>SLShare  
 Udostępnionego folderu sieciowego w którym przechowywane są dzienniki wdrożenia pod koniec procesu wdrażania.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|\-||ZTI|\-|  

|**Wartość**|**Opis**|  
|-|-|
|*shared_folder*|Nazwa udostępnionego folderu sieciowego w skrypcie, które są przechowywane dzienniki|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ UDDir=%OSDComputerName% SLShare=\\NYC-AM-FIL-01\Logs$ UDProfiles=Administrator, User-01, ExtranetUser UserDataLocation=NONE SkipCapture=NO SkipAdminPassword=YES SkipProductKey=YES`|  

####  <a name="SLShareDynamicLogging"></a>SLShareDynamicLogging  
 Sieciowy folder udostępniony w których wszystkie MDT zapisywane są dzienniki podczas wdrażania. Służy to zaawansowane w czasie rzeczywistym tylko do debugowania.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*shared_folder*|Nazwa udostępnionego folderu sieciowego w skrypcie, które są przechowywane dzienniki|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ UDDir=%OSDComputerName% SLShare=\\NYC-AM-FIL-01\Logs$ SLShareDynamicLogging=\\NYC-AM-FIL-01\Logs$ UDProfiles=Administrator, User-01, ExtranetUser UserDataLocation=NONE SkipCapture=NO SkipAdminPassword=YES SkipProductKey=YES`|  

####  <a name="SMSTSAssignUserMode"></a>SMSTSAssignUserMode  
 Określa, czy koligacji urządzenia użytkownika (UDA) powinno być włączone i czy zatwierdzenia jest wymagana. Ta właściwość działa tylko z funkcją UDA w programie Configuration Manager.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI||  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|**Automatycznie**|Koligację między użytkownikiem a urządzeniem docelowym zostanie nawiązane, a zatwierdzenia jest wykonywane automatycznie.|  
|**Oczekiwanie**|Koligację między użytkownikiem a urządzeniem docelowym zostanie nawiązane, a zatwierdzenia jest przesyłany w celu zatwierdzenia przez administratora programu Configuration Manager.|  
|**Wyłącz**|Koligację między użytkownikiem a urządzeniem docelowym nie zostanie nawiązane.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] SMSTSAssignUserMode=Auto SMSTSUdaUsers=Fabrikam\Ken, Fabrikam\Pilar`|  

####  <a name="SMSTSRunCommandLineUserName"></a>Zmienną SMSTSRunCommandLineUserName  
 Określa nazwę użytkownika w *domena\nazwa_użytkownika* formatu, który powinien być używany z **Uruchom wiersz polecenia** krok, który jest skonfigurowany do uruchamiania jako użytkownik.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*nazwa_użytkownika*|Określa nazwę użytkownika, który ma być używany z **Uruchom wiersz polecenia** kroku|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] SMSTSRunCommandLineUserName=Fabrikam\Ken SMSTSRunCommandLineUserPassword=<complex_password>`|  

####  <a name="SMSTSRunCommandLineUserPassword"></a>SMSTSRunCommandLineUserPassword  
 Określa hasło, które mają być używane z **Uruchom wiersz polecenia** krok, który jest skonfigurowany do uruchamiania jako użytkownik.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*user_password*|Określa hasło, które mają być używane z **Uruchom wiersz polecenia** kroku|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] SMSTSRunCommandLineUserName=Fabrikam\Ken SMSTSRunCommandLineUserPassword=<complex_password>`|  

####  <a name="SMSTSUdaUsers"></a>Zmienna SMSTSUdaUsers  
 Określa użytkowników, którzy zostaną przypisane koligacji z określonym urządzeniem przy użyciu funkcji UDA, która jest dostępna tylko w programie Configuration Manager.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI||  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*Użytkownik1 i Użytkownik2...*|Rozdzielana przecinkami lista użytkowników w *domena\nazwa_użytkownika* formatu, który zostanie przypisany koligacji z urządzenia.<br /><br /> Uwaga:<br /><br /> Można używać tylko nazwę NetBIOS domeny w tej wartości, takich jak *Fabrikam\Ken*. Nie można użyć w pełni kwalifikowaną nazwę domeny (fabrikam.com\Ken) lub notacji UPN (ken@fabrikam.com).|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] SMSTSAssignUserMode=Auto SMSTSUdaUsers=Fabrikam\Ken, Fabrikam\Pilar`|  

####  <a name="SQLServer"></a>SQLServer  
 Tożsamość komputera programem SQL Server, który wykonuje zapytanie bazy danych, które zwraca kolumn w tabeli określonej w wartości właściwości **tabeli** właściwości. Zapytanie jest na podstawie parametrów określonych w **parametry** i **ParameterCondition** właściwości. Wystąpienie programu SQL Server na komputerze jest określona w **wystąpienia** właściwości.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*SQL_server*|Nazwa komputera z programem SQL Server|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Computers, Default  [Default] OSInstall=YES ScanStateArgs=/v:5 /o /c LoadStateArgs=/v:5 /c /lac  [Computers] SQLServer=NYC-SQL-01 SQLShare=SQL$ Database=MDTDB Instance=SQLEnterprise2005 Table=Computers Parameters=SerialNumber, AssetTag ParameterCondition=OR`|  

####  <a name="SQLShare"></a>SQLShare  
 Nazwa folderu udostępnionego na komputerze z uruchomionym programem SQL Server (określonego przez **SQLServer** właściwości). Poświadczenia używane do uwierzytelniania są dostarczane przez **UserDomain**, **UserID**, i **UserPassword** właściwości (LTI i ZTI) lub przez program Configuration Manager Zaawansowanych poświadczenia konta klienta (tylko ZTI).  

> [!NOTE]
>  Ta właściwość jest wymagane do wykonania zintegrowanego uwierzytelniania systemu Windows. To jest zalecaną metodą uwierzytelniania, zamiast używania **DBID** i **DBPwd** właściwości (które obsługują metodę uwierzytelniania programu SQL Server).  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*shared_folder*|Nazwa folderu udostępnionego na komputerze z uruchomionym programem SQL Server|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Computers, Default Properties=MyCustomProperty  [Default] OSInstall=YES ScanStateArgs=/v:5 /o /c LoadStateArgs=/v:5 /c /lac  [Computers] SQLServer=NYC-SQL-01 SQLShare=SQL$ Database=MDTDB Instance=MDT2010 Table=Computers Parameters=SerialNumber, AssetTag ParameterCondition=OR`|  

####  <a name="StatePath"></a>StatePath  
 Ta właściwość jest używana w celu ustawienia ścieżki, gdzie będą przechowywane dane migracji stanu użytkownika, może być ścieżką UNC, ścieżkę lokalną lub ścieżkę względną. [OSDStateStorePath](#OSDStateStorePath) właściwość ma wyższy priorytet niż **StatePath** lub [UserDataLocation](#UserDataLocation) właściwości, gdy określono też tych właściwości.  

> [!NOTE]
>  Ta właściwość jest dostępne w celu zgodności z poprzednimi wersjami w poprzednich wersjach zestawu MDT. Użyj [OSDStateStorePath](#UserDataLocation) właściwości zamiast tego.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*Ścieżka*|Ścieżka, w którym dane migracji stanu użytkownika będą przechowywane, który może być ścieżką UNC, ścieżkę lokalną lub ścieżkę względną|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] SitePath=\\fs1\Share\Replace ComputerBackupLocation=\\fs1\Share\ComputerBackup\Client01`|  

####  <a name="StoredProcedure"></a>Procedura składowana  
 Nazwa procedury składowanej używane podczas wykonywania kwerendy bazy danych, która zwraca wartości właściwości z kolumn w tabeli lub widoku. Procedura składowana znajduje się w bazie danych określona w **bazy danych** właściwości. Komputera z programem SQL Server jest określona w **SQLServer** właściwości. Wystąpienie programu SQL Server na komputerze jest określona w **wystąpienia** właściwości. Nazwa procedury składowanej jest określona w **StoredProcedure** właściwości.  

 Aby uzyskać więcej informacji na temat za pomocą procedury składowanej zapytanie dotyczące bazy danych programu SQL Server, zobacz sekcję "Wdrażanie aplikacji oparta na starszej wersji aplikacji", w zestawie MDT dokumentu *Microsoft Deployment Toolkit przykłady Guide*.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*stored_procedure*|Nazwa procedury składowanej wykorzystywane do badania bazy danych programu SQL Server|  

|**Przykład**|  
|-|  
|`[Settings] Priority=DynamicPackages, Default  [Default] OSInstall=YES  [DynamicPackages] SQLDefault=DB_DynamicPackages  [DB_DynamicPackages] SQLServer=SERVER1 Database=MDTDB StoredProcedure=RetrievePackages Parameters=MacAddress SQLShare=Logs Instance=MDT2013 Port=1433 Netlib=DBNMPNTW`|  

####  <a name="SupportsHyperVRole"></a>SupportsHyperVRole  
 Określa, czy zasoby procesora na komputerze docelowym może obsługiwać rolę serwera funkcji Hyper-V w systemie Windows Server. Ta właściwość ma wartość PRAWDA, jeśli ustawiono wartość dla następujących właściwości **TRUE**:  

-   **SupportsNX**  

-   **SupportsVT**  

-   **Supports64Bit**  

 Ustawiono każdej poprzedniej właściwości, korzystając z informacji **CPUID** interfejsu. Aby uzyskać dalsze informacje zebrane o maszyn wirtualnych i informacje zwrócone z **CPUID** interfejsu, zobacz następujące właściwości:  

-   **IsHypervisorRunning**  

-   **IsVM**  

-   **SupportsNX**  

-   **SupportsVT**  

-   **Supports64Bit**  

-   **VMPlatform**  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|**WARTOŚĆ TRUE**|Zasoby procesora komputera docelowego może obsługiwać rolę serwera funkcji Hyper-V w systemie Windows Server.|  
|**WARTOŚĆ FALSE**|Zasoby procesora komputera docelowego nie może obsługiwać rolę serwera funkcji Hyper-V w systemie Windows Server.|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="SupportsNX"></a>SupportsNX  
 Określa, czy zasoby procesora na komputerze docelowym obsługują technologię nie wykonać (NX). Technologia NX jest używana w procesorach może też oddzielić obszary pamięci na potrzeby używania przez albo Magazyn instrukcji procesora (kod) lub do przechowywania danych. Ta właściwość jest ustawiona, korzystając z informacji **CPUID** interfejsu.  

 Aby uzyskać dalsze informacje zebrane o maszyn wirtualnych i informacje zwrócone z **CPUID** interfejsu, zobacz następujące właściwości:  

-   **IsHypervisorRunning**  

-   **IsVM**  

-   **SupportsHyperVRole**  

-   **SupportsVT**  

-   **Supports64Bit**  

-   **VMPlatform**  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|**WARTOŚĆ TRUE**|Zasoby procesora komputera docelowego obsługują technologię NX.|  
|**WARTOŚĆ FALSE**|Zasoby procesora komputera docelowego nie obsługują technologię NX.|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="SupportsVT"></a>SupportsVT  
 Określa, czy zasoby procesora na komputerze docelowym obsługuje funkcję technologii wirtualizacji (VT). VT jest używana do obsługi bieżącego zwirtualizowanych środowiskach, takich jak funkcja Hyper-V. Ta właściwość jest ustawiona, korzystając z informacji w interfejsie CPUID.  

 Dodatkowe informacje zebrane o maszyn wirtualnych i informacje zwrócone z interfejsu CPUID zobacz następujące właściwości:  

-   **IsHypervisorRunning**  

-   **IsVM**  

-   **SupportsHyperVRole**  

-   **SupportsNX**  

-   **Supports64Bit**  

-   **VMPlatform**  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|**WARTOŚĆ TRUE**|Zasoby procesora komputera docelowego obsługują technologię VT.|  
|**WARTOŚĆ FALSE**|Nie obsługują technologii VT zasobów procesora komputera docelowego.|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="Supports64Bit"></a>Supports64Bit  
 Określa, czy zasoby procesora na komputerze docelowym obsługują Windows 64-bitowych systemach operacyjnych. Większość nowoczesnych środowiskach wirtualizacji wymaga 64-bitowy procesor. Ta właściwość jest ustawiona, korzystając z informacji **CPUID** interfejsu.  

 Aby uzyskać dalsze informacje zebrane o maszyn wirtualnych i informacje zwrócone z **CPUID** interfejsu, zobacz następujące właściwości:  

-   **IsHypervisorRunning**  

-   **IsVM**  

-   **SupportsHyperVRole**  

-   **SupportsNX**  

-   **SupportsVT**  

-   **VMPlatform**  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|**WARTOŚĆ TRUE**|Zasoby procesora komputera docelowego obsługuje Windows 64-bitowym systemie operacyjnym.|  
|**WARTOŚĆ FALSE**|Windows 64-bitowym systemie operacyjnym nie obsługują zasobów procesora komputera docelowego.|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="SysVolPath"></a>SysVolPath  
 Określa ścieżkę pełną, innym niż UNC do katalogu na dysku stałym komputera lokalnego.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*Ścieżka*|Określa ścieżkę pełną, innym niż UNC do katalogu na dysku stałym komputera lokalnego|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] SysVolPath=%DestinationLogicalDrive%\Windows\Sysvol`|  

####  <a name="Table"></a>Tabela  
 Nazwa tabeli lub widoku ma być używana podczas wykonywania kwerendy bazy danych, która zwraca wartości właściwości z kolumn w tabeli lub widoku. Zapytanie jest na podstawie parametrów określonych w **parametry** i **ParameterCondition** właściwości. Tabela lub Widok znajduje się w bazie danych określona w **bazy danych** właściwości. Komputera z programem SQL Server jest określona w **SQLServer** właściwości. Wystąpienie programu SQL Server na komputerze jest określona w **wystąpienia** właściwości.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*nazwa_tabeli*|Nazwa tabeli lub widoku można zbadać wartości właściwości|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Computers, Default  [Default] OSInstall=YES ScanStateArgs=/v:5 /o /c LoadStateArgs=/v:5 /c /lac  [Computers] SQLServer=NYC-SQL-01 SQLShare=SQL$ Database=MDTDB Instance=MDT2010 Table=Computers Parameters=SerialNumber, AssetTag ParameterCondition=OR`|  

####  <a name="TaskSequenceID"></a>TaskSequenceID  
 Określa sekwencję zadań systemu operacyjnego w celu wdrażania na komputerze docelowym. Identyfikator sekwencji zadań jest tworzony w węźle sekwencje zadań w konsoli Deployment Workbench. **TaskSequenceID** właściwość umożliwia znaki alfanumeryczne, łączniki (-) i znaki podkreślenia (\_). **TaskSequenceID** właściwości nie może być pusta ani zawierać spacji.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*task_sequence_id*|Identyfikator sekwencji zadań systemu operacyjnego, które są zdefiniowane w konsoli Deployment Workbench dla docelowego systemu operacyjnego wdrażany<br /><br /> Uwaga:<br /><br /> Należy użyć **TaskSequenceID** określony w Interfejsie Deployment Workbench nie identyfikator GUID **TaskSequenceID**.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] TaskSequenceID=BareMetal`|  

####  <a name="TaskSequenceName"></a>TaskSequenceName  
 Określa nazwę sekwencji zadań uruchamiana.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*task_sequence_name*|Nazwa sekwencji zadań uruchamiana, takie jak wdrażanie *Windows 8.1 na komputerze odniesienia*|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="TaskSequenceVersion"></a>TaskSequenceVersion  
 Określa wersję uruchamiania sekwencji zadań.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*task_sequence_version*|Wersja sekwencji zadań uruchamiana, takich jak *1,00*|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="TimeZoneName"></a>TimeZoneName  
 Strefa czasowa, w którym znajduje się na komputerze docelowym. Ta wartość jest wstawiany odpowiednie ustawienia konfiguracji w pliku Unattend.xml.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*time_zone_name*|Wartość tekstu, która wskazuje strefy czasowej, w którym znajduje się na komputerze docelowym|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] TimeZoneName=Pacific Standard Time DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ UDDir=%OSDComputerName% SLShare=\\NYC-AM-FIL-01\Logs$ UDProfiles=Administrator, User-01, ExtranetUser UserDataLocation=NONE`|  

####  <a name="ToolRoot"></a>ToolRoot  
 Określa ścieżkę UNC do narzędzi\\*proc_arch* folder (gdzie *proc_arch* jest uruchomiony system operacyjny architektury procesora i może mieć wartości **x86** lub **x64**), która jest bezpośrednio poniżej poziomu głównego struktury folderów określone w **DeployRoot** właściwości. Narzędzia\\*proc_arch* folder zawiera narzędzia zestaw MDT jest używany podczas procesu wdrażania.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*Ścieżka*|Ścieżka UNC lub lokalnej ścieżki do narzędzi\\*proc_arch* folder (gdzie *proc_arch* jest uruchomiony system operacyjny architektury procesora i może mieć wartość  **x86** lub **x64**) znajdujący się bezpośrednio pod głównym struktury folderów określone przez **DeployRoot** właściwości|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="TPMOwnerPassword"></a>TPMOwnerPassword  
 Hasło modułu TPM (znanej także jako *hasła administracji modułu TPM*) dla właściciela na komputerze docelowym. Hasła można zapisać do pliku lub przechowywane w usługach AD DS.  

> [!NOTE]
>  Jeśli ustawiono już prawa własności modułu TPM lub własność modułu TPM nie jest dozwolona, a następnie **TPMOwnerPassword** właściwość jest ignorowana. Jeśli wymagane jest hasło modułu TPM i **TPMOwnerPassword** nie podano właściwości, hasła modułu TPM ustawiono hasło administratora lokalnego.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*hasło*|Hasło modułu TPM z właścicielem komputera docelowego|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] BDEDriveLetter=S: BDEDriveSize=2000 BDEInstall=TPMKey BDERecoveryKey=TRUE BDEKeyLocation=C: TPMOwnerPassword=<complex_password> BackupShare=\\NYC-AM-FIL-01\Backup$ BackupDir=%OSDComputerName% DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ UDDir=%OSDComputerName%`|  

####  <a name="UDDir"></a>UDDir  
 Folder, w którym są przechowywane dane migracji stanu użytkownika. Ten folder istnieje pod udostępnionego folderu sieciowego określone w **UDShare**.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*folder*|Nazwa folderu, który istnieje pod udostępnionego folderu sieciowego|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ UDDir=%OSDComputerName% SLShare=\\NYC-AM-FIL-01\Logs$ UDProfiles=Administrator, User-01, ExtranetUser UserDataLocation=NONE SkipCapture=NO`|  

####  <a name="UDProfiles"></a>UDProfiles  
 Rozdzielana przecinkami lista profilów użytkowników, które trzeba zapisać przez Scanstate.exe podczas fazę Przechwytywanie stanu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*user_profiles*|Na liście profilów użytkownika można zapisać, oddzielonych przecinkami|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ UDDir=%OSDComputerName% SLShare=\\NYC-AM-FIL-01\Logs$ UDProfiles=Administrator, User-01, ExtranetUser UserDataLocation=NONE SkipCapture=NO`|  

####  <a name="UDShare"></a>UDShare  
 Udziału sieciowego, w którym są przechowywane dane migracji stanu użytkownika.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*UNC_path*|Ścieżka UNC do udziału sieciowego, w którym są przechowywane dane migracji stanu użytkownika|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ UDDir=%OSDComputerName% SLShare=\\NYC-AM-FIL-01\Logs$ UDProfiles=Administrator, User-01, ExtranetUser UserDataLocation=NONE SkipCapture=NO`|  

####  <a name="UILanguage"></a>UILanguage  
 Domyślny język, który ma być używany z docelowego systemu operacyjnego. Jeśli nie zostanie określony, **Kreatora wdrażania** używa języka skonfigurowanego w obrazie wdrażany.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*UI_language*|Domyślny język systemu operacyjnego na komputerze docelowym|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] UserLocale=en-us UILanguage=en-us KeyboardLocale=0409:00000409`|  

####  <a name="UserDataLocation"></a>UserDataLocation  
 Lokalizacja, w którym są przechowywane dane migracji stanu użytkownika narzędzia USMT.  

> [!CAUTION]
>  Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|Puste|Jeśli **UserDataLocation**nie została określona lub jest pole pozostanie puste, Kreatora wdrażania domyślnie zostanie ustawiona przy użyciu zachowanie AUTO.|  
|*UNC_path*|Ścieżka UNC do udostępnionego folderu sieciowego przechowywania danych migracji stanu użytkownika.|  
|**AUTOMATYCZNIE**|Skrypty wdrażania przechowywania danych migracji stanu użytkownika na lokalnym dysku twardym, jeśli jest wystarczająca ilość miejsca. W przeciwnym razie dane migracji stanu użytkownika są zapisywane w lokalizacji sieciowej, która została określona w **UDShare** i **UDDir** właściwości.|  
|**SIECI**|Dane migracji stanu użytkownika są przechowywane w lokalizacji wskazywany przez **UDShare** i **UDDir** właściwości.|  
|**BRAK**|Dane migracji stanu użytkownika nie są zapisywane.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSInstall=YES ScanStateArgs=/v:5 /o /c LoadStateArgs=/v:5 /c /lac DoCapture=YES BackupShare=\\NYC-AM-FIL-01\Backup$ BackupDir=%OSDComputerName% UserDataLocation=NETWORK DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ UDDir=%OSDComputerName%`|  

####  <a name="UserDomain"></a>UserDomain  
 Domeną, w której poświadczeń użytkownika (określony w **UserID** właściwości) znajdują się.  

> [!NOTE]
>  Całkowicie zautomatyzowanego wdrażania LTI Podaj tę właściwość w CustomSettings.ini i BootStrap.ini. Pamiętaj jednak, że przechowywanie poświadczeń użytkownika w tych plikach przechowuje poświadczenia w postaci zwykłego tekstu i w związku z tym nie jest bezpieczna.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*domeny*|Nazwa domeny, na którym są przechowywane poświadczenia konta użytkownika|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSInstall=YES ScanStateArgs=/v:5 /o /c LoadStateArgs=/v:5 /c /lac DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UserDataLocation=NONE UserDomain=WOODGROVEBANK UserID=NYC Help Desk Staff UserPassword=<complex_password>`|  

####  <a name="UserID"></a>Nazwa użytkownika  
 Poświadczenia użytkownika do uzyskiwania dostępu do zasobów sieciowych.  

> [!NOTE]
>  Całkowicie zautomatyzowanego wdrażania LTI Podaj tę właściwość w CustomSettings.ini i BootStrap.ini. Pamiętaj jednak, że przechowywanie poświadczeń użytkownika w tych plikach przechowuje poświadczenia w postaci zwykłego tekstu i w związku z tym nie jest bezpieczna.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*Funkcja user_id*|Nazwa poświadczenia konta użytkownika, które są używane do dostępu do zasobów sieciowych|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSInstall=YES ScanStateArgs=/v:5 /o /c LoadStateArgs=/v:5 /c /lac DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UserDataLocation=NONE UserDomain=WOODGROVEBANK UserID=NYC-HelpDesk UserPassword=<complex_password>`|  

####  <a name="UserLocale"></a>UserLocale  
 Ustawienia regionalne użytkownika ma być używany z docelowego systemu operacyjnego. Jeśli nie zostanie określony, **Kreatora wdrażania** używa ustawień regionalnych użytkownika skonfigurowane w obrazie wdrażany.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*user_locale*|Ustawienia regionalne użytkownika na komputerze docelowym. Wartość jest określona jako wartość tekstową (en-us).|  

|**Przykład 1**|  
|-|  
|`[Settings] Priority=Default  [Default] UserLocale=en-us KeyboardLocale=0409:00000409`|  

|**Przykład 2**|  
|-|  
|`[Settings] Priority=Default  [Default] UserLocale=en-us KeyboardLocale=en-us`|  

####  <a name="UserPassword"></a>Hasła użytkownika  
 Hasło dla użytkownika poświadczeń określonych w **UserID** właściwości.  

> [!NOTE]
>  Całkowicie zautomatyzowanego wdrażania LTI Podaj tę właściwość w CustomSettings.ini i BootStrap.ini. Pamiętaj jednak, że przechowywanie poświadczeń użytkownika w tych plikach przechowuje poświadczenia w postaci zwykłego tekstu i w związku z tym nie jest bezpieczna.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|-||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*user_password*|Hasło dla poświadczeń konta użytkownika|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] UserDataLocation=NONE UserDomain=WOODGROVEBANK UserID=NYC-HelpDesk UserPassword=<complex_password>`|  

####  <a name="USMTConfigFile"></a>USMTConfigFile  
 Plik XML konfiguracji narzędzia USMT, które mają być używane podczas uruchamiania **Scanstate** i **Loadstate**.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*USMTConfigFile*|Nazwa pliku XML konfiguracji, które mają być używane podczas uruchamiania Scanstate.exe i Loadstate.exe|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSInstall=YES ScanStateArgs=/v:5 /o /c LoadStateArgs=/v:5 /c /lac DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ UDDir=%OSDComputerName% SLShare=\\NYC-AM-FIL-01\Logs$ USMTMigFiles1=MigApp.xml USMTMigFiles2=MigUser.xml USMTMigFiles3=MigSys.xml USMTMigFiles4=MigCustom.xml USMTConfigFile=USMTConfig.xml UserDataLocation=NONE`|  

####  <a name="USMTLocal"></a>USMTLocal  
 Ta właściwość określa, czy informacje o stanie użytkownika narzędzia USMT jest przechowywany lokalnie na komputerze docelowym. Ta właściwość jest głównie używana przez [ZTIUserState.wsf](#ZTIUserState.wsf) i [ZTIBackup.wsf](#ZTIBackup.wsf) skrypty w celu wskazania, że **Zażądaj magazynu stanów** i **stanu zlecenia Magazyn** są pomijane kroki sekwencji zadań dla wdrożeń programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [OSDStateStorePath](#OSDStateStorePath) właściwości.  

> [!NOTE]
>  Tej właściwości należy używać tylko w przypadku opisanego w [OSDStateStorePath](#OSDStateStorePath) właściwości).  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI||  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|**WARTOŚĆ TRUE**|Informacje o stanie użytkownika narzędzia USMT jest przechowywany lokalnie na komputerze docelowym i **Zażądaj magazynu stanów** i **Zwolnij Magazyn stanów** są pomijane kroki sekwencji zadań.|  
|**WARTOŚĆ FALSE**|Informacje o stanie użytkownika narzędzia USMT nie jest przechowywany lokalnie na komputerze docelowym i **Zażądaj magazynu stanów** i **Zwolnij Magazyn stanów** kroków sekwencji zadań są wykonywane.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSInstall=YES ScanStateArgs=/v:5 /o /c LoadStateArgs=/v:5 /c /lac DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ UDDir=%OSDComputerName% SLShare=\\NYC-AM-FIL-01\Logs$ USMTLocal=TRUE USMTMigFiles001=MigApp.xml USMTMigFiles002=MigUser.xml USMTMigFiles003=MigSys.xml USMTMigFiles004=MigCustom.xml UserDataLocation=NONE`|  

####  <a name="USMTMigFiles"></a>USMTMigFiles  
 Lista plików w formacie XML, które są używane przez narzędzie USMT (Scanstate.exe) do identyfikowania informacji o migracji stanu użytkownika do zapisania. Gdy ta właściwość nie jest określona, skrypt ZTIUserState.wsf używa MigApp.xml, MigUser.xml i MigSys.xml. W przeciwnym razie ZTIUserState.wsf używa plików jednoznacznego odwołania do tej właściwości. **USMTMigFiles** właściwość ma sufiks numeryczny (na przykład **USMTMigFiles001** lub **USMTMigFiles002**).  

> [!NOTE]
>  Ta właściwość umożliwia określenie plików XML, który ma być używany przez Scanstate.exe zamiast **/I** parametru w **ScanStateArgs** właściwości. Uniemożliwia to skrypt ZTIUserState.wsf potencjalnie duplikowania tę samą listę plików XML.  

> [!NOTE]
>  Nazwa tej właściwości można określić przy użyciu nomenklaturę jednocyfrowej (**USMTMigFiles1**) lub nomenklaturę triple cyfrowy (**USMTMigFiles001**).  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*USMTMigFile*|Nazwa pliku XML, który ma być używany jako dane wejściowe dla Scanstate.exe, w osobnych wierszach. Jeśli nie jest określony, wartością domyślną jest MigApp.xml, MigUser.xml i MigSys.xml.<br /><br /> Uwaga:<br /><br /> Jeśli ta wartość jest określona, domyślnych plików (MigApp.xml, MigUser.xml i MigSys.xml) również musi być dodana do listy, jeśli te pliki mają być uwzględnione.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSInstall=YES ScanStateArgs=/v:5 /o /c LoadStateArgs=/v:5 /c /lac DeployRoot=\\NYC-AM-FIL-01\Distribution$ ResourceRoot=\\NYC-AM-FIL-01\Resource$ UDShare=\\NYC-AM-FIL-01\MigData$ UDDir=%OSDComputerName% SLShare=\\NYC-AM-FIL-01\Logs$ USMTMigFiles001=MigApp.xml USMTMigFiles002=MigUser.xml USMTMigFiles003=MigSys.xml USMTMigFiles004=MigCustom.xml UserDataLocation=NONE`|  

####  <a name="USMTOfflineMigration"></a>USMTOfflineMigration  
 Ta właściwość określa, czy zestaw MDT używa narzędzia USMT do przeprowadzenia migracji stanu użytkownika w trybie offline. W przypadku migracji w trybie offline przechwytywania jest wykonywane w środowisku Windows PE zamiast istniejącego systemu operacyjnego.  

 Migracja w trybie offline jest przy użyciu narzędzia USMT jest wykonywane dla:  

-   UDI zawsze, bez względu na to ustawienie **USMTOfflineMigration** właściwości  

-   ZTI tylko w przypadku scenariusza wdrażania komputer odświeżania zestawu MDT i tylko wtedy, gdy **USMTOfflineMigration** właściwość jest ustawiona na **"Prawda"**  

    > [!NOTE]
    >  Nie można wykonać migracji stanu użytkownika w trybie offline narzędzia USMT w scenariuszu wdrożenia zestawu MDT nowego komputera przy użyciu ZTI.  

-   LTI dla:  

    1.  Przy użyciu scenariusz wdrożenia zestawu MDT nowy komputer **przenieść dane i ustawienia** strona kreatora w Kreatorze wdrażania  

    2.  Scenariusz wdrażania komputer odświeżania zestawu MDT i tylko wtedy, gdy **USMTOfflineMigration** właściwość jest ustawiona na **"Prawda"**  

 Aby uzyskać więcej informacji na temat używania zestawu MDT i narzędzia USMT do przeprowadzenia migracji stanu użytkownika w trybie offline Zobacz "Konfigurowanie narzędzia USMT w trybie Offline migracja stanu użytkownika".  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|**WARTOŚĆ TRUE**|Zestaw MDT używa narzędzia USMT do przeprowadzenia migracji stanu użytkownika w trybie offline.|  
|*Dowolna inna wartość*|Zestaw MDT nie przeprowadza migracji stanu użytkownika w trybie offline. Zamiast tego migracji stanu użytkownika są przechwytywane w istniejącego systemu operacyjnego. Jest to wartość domyślna.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] OSInstall=YES SkipUserData=YES USMTOfflineMigration=TRUE DoNotFormatAndPartition=YES OSDStateStorePath=\\WDG-MDT-01\StateStore$`|  

####  <a name="UUID"></a>IDENTYFIKATOR UUID  
 Uniwersalny unikatowy identyfikator (identyfikator UUID) przechowywanych w systemie BIOS zarządzania na komputerze docelowym.  

 Format identyfikatora UUID jest 16-bajtową wartość przy użyciu cyfr szesnastkowych w następującym formacie: *12345678-1234-1234-1234-123456789ABC*. Ta właściwość służy do tworzenia podsekcji, zawierający ustawienia przeznaczone dla określonego komputera.  

> [!NOTE]
>  Tej właściwości ustawiono dynamicznie przez zestaw MDT skrypty i nie może mieć jego wartość ustawiona w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu. Jednak służy tej właściwości w CustomSettings.ini lub zestaw MDT bazy danych, jak pokazano w poniższych przykładach ułatwiających definiując konfigurację komputera docelowego.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*IDENTYFIKATOR UUID*|Identyfikator UUID komputera docelowego|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="ValidateDomainCredentialsUNC"></a>ValidateDomainCredentialsUNC  
 Ta właściwość jest używana, aby określić ścieżkę UNC do udostępnionego folderu sieciowego, który jest używany do sprawdzania poprawności poświadczenia podane dla przyłączania komputera docelowego do domeny. Poprawność poświadczenia zostały określone w **administrator domeny**, **DomainAdminDomain**, i **DomainAdminPassword** właściwości.  

> [!NOTE]
>  Upewnij się, że żadne inne właściwości w zestawie MDT użycie serwera udostępnianie folderu w tej właściwości. Przy użyciu serwera, do którego odwołuje się już przez inne właściwości zestawu MDT może spowodować niewłaściwe weryfikację poświadczeń.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*unc_path*|Określa w pełni kwalifikowaną ścieżkę UNC do udostępnionego folderu sieciowego|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] ValidateDomainCredentialsUNC=\\wdg-fs-01\Source$`|  

####  <a name="VHDCreateDiffVHD"></a>VHDCreateDiffVHD  
 Ta właściwość jest używana do określenia nazwy różnicowego dysku VHD (znanej także jako *podrzędnych wirtualnego dysku twardego*) pliku. Różnicowy wirtualny dysk twardy jest podobny do dynamicznie powiększających się dysków VHD, ale zawiera tylko bloki modyfikacji dysku skojarzonego elementu nadrzędnego dysku VHD. Nadrzędnego dysku VHD jest tylko do odczytu, więc należy zmodyfikować różnicowego dysku VHD. Różnicowych plik wirtualnego dysku twardego jest tworzony w tym samym folderze, jak nadrzędnego wirtualnego dysku twardego, plików, tylko nazwa pliku jest określona w tej właściwości. Ta właściwość jest prawidłowa tylko dla scenariusza wdrożenia zestawu MDT nowego komputera.  

> [!NOTE]
>  Wszystkie pliki VHD nadrzędnego utworzonego przez zestaw MDT są przechowywane w folderze wirtualnego dysku twardego w folderze głównym dysku nadrzędnego.  

 Ta właściwość jest zwykle ustawiona za pomocą kroku sekwencji zadań utworzonych przy użyciu **tworzenia wirtualnych dysków twardych (VHD)** typ sekwencji zadań. Można zastąpić wartość **tworzenia wirtualnych dysków twardych (VHD)** krok sekwencji zadań ustawia przez skonfigurowanie tej właściwości w CustomSettings.ini.  

> [!NOTE]
>  Aby skonfigurować tę właściwość w CustomSettings.ini, należy dodać tę właściwość, aby **właściwości** wiersza w CustomSettings.ini.  

 Aby uzyskać powiązane właściwości, które są używane przez pliki VHD zobacz:  

-   **VHDCreateFileName**  

-   **VHDCreateSizeMax**  

-   **VHDCreateSource**  

-   **VHDCreateType**  

-   **Dyskivhd**  

-   **VHDInputVariable**  

-   **VHDOutputVariable**  

-   **VHDTargetDisk**  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*Nazwa pliku*|Określa nazwę różnicowych pliku wirtualnego dysku twardego, który znajduje się w tym samym folderze co plik VHD nadrzędnego<br /><br /> Różnicowe pliku wirtualnego dysku twardego nie może być taką samą nazwę pliku nadrzędnego dysku VHD.|  
|**LOSOWE**|Automatycznie generuje losową nazwę pliku VHD różnicowych znajduje się w tym samym folderze co plik VHD nadrzędnego|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] VHDCreateDiffVHD=Win7Diff_C.vhd VHDInputVariable=VHDTargetDisk`|  

####  <a name="VHDCreateFileName"></a>VHDCreateFileName  
 Ta właściwość jest używana do określenia nazwy pliku dysku VHD. Typ pliku wirtualnego dysku twardego jest oparty na wartość **VHDCreateType** właściwości. Właściwość tylko zawiera nazwę pliku, a nie ścieżkę do nazwy pliku i jest prawidłowy tylko w przypadku scenariusza wdrożenia zestawu MDT nowego komputera.  

> [!NOTE]
>  Pliki wirtualnego dysku twardego utworzonego przez zestaw MDT są przechowywane w folderze wirtualnego dysku twardego w folderze głównym dysku nadrzędnego.  

 Ta właściwość jest zwykle ustawiona za pomocą kroku sekwencji zadań utworzonych przy użyciu **tworzenia wirtualnych dysków twardych (VHD)** typ sekwencji zadań. Można zastąpić wartość **tworzenia wirtualnych dysków twardych (VHD)** krok sekwencji zadań ustawia przez skonfigurowanie tej właściwości w CustomSettings.ini.  

> [!NOTE]
>  Aby skonfigurować tę właściwość w CustomSettings.ini, należy dodać tę właściwość, aby **właściwości** wiersza w CustomSettings.ini.  

 Aby uzyskać powiązane właściwości, które są używane przez pliki VHD zobacz:  

-   **VHDCreateDiffVHD**  

-   **VHDCreateSizeMax**  

-   **VHDCreateSource**  

-   **VHDCreateType**  

-   **Dyskivhd**  

-   **VHDInputVariable**  

-   **VHDOutputVariable**  

-   **VHDTargetDisk**  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*nazwa_pliku*|Określa nazwę pliku wirtualnego dysku twardego|  
|**LOSOWE**|Automatycznie generuje losową nazwę pliku VHD, który znajduje się w folderze wirtualnego dysku twardego w folderze głównym dysku nadrzędnego|  
|Puste|Tym samym **losowych**|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] VHDCreateSizeMax=130048 VHDCreateType=EXPANDABLE VHDCreateFileName=Win7_C.vhd VHDInputVariable=VHDTargetDisk`|  

####  <a name="VHDCreateSizeMax"></a>VHDCreateSizeMax  
 Ta właściwość jest używana do określania maksymalny rozmiar pliku VHD w megabajtach (MB). Rozmiar pliku VHD w czasie tworzenia opiera się na typ tworzony plik wirtualnego dysku twardego. Aby uzyskać więcej informacji, zobacz [VHDCreateType](#VHDCreateType) właściwości. Ta właściwość jest prawidłowy tylko w przypadku scenariusza wdrożenia zestawu MDT nowego komputera.  

> [!NOTE]
>  Jeśli ta właściwość nie jest określona, wartością domyślną dla maksymalnego rozmiaru pliku wirtualnego dysku twardego wynosi 90% wolnego miejsca na dysku nadrzędnego.  

 Ta właściwość jest zwykle ustawiona za pomocą kroku sekwencji zadań utworzonych przy użyciu **tworzenia wirtualnych dysków twardych (VHD)** typ sekwencji zadań. Można zastąpić wartość która **tworzenia wirtualnych dysków twardych (VHD)** krok sekwencji zadań ustawia przez skonfigurowanie tej właściwości w CustomSettings.ini.  

> [!NOTE]
>  Aby skonfigurować tę właściwość w CustomSettings.ini, należy dodać tę właściwość, aby **właściwości** wiersza w CustomSettings.ini.  

 Aby uzyskać powiązane właściwości, które są używane przez pliki VHD zobacz:  

-   **VHDCreateDiffVHD**  

-   **VHDCreateFileName**  

-   **VHDCreateSource**  

-   **VHDCreateType**  

-   **Dyskivhd**  

-   **VHDInputVariable**  

-   **VHDOutputVariable**  

-   **VHDTargetDisk**  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*rozmiar*|Maksymalny rozmiar pliku VHD wyrażona w Megabajtach. Na przykład 130,048 MB równa 127 GB. Wartość domyślna wynosi 90% wolnego miejsca na dysku nadrzędnego.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] VHDCreateSizeMax=130048 VHDCreateType=FIXED VHDCreateFileName=Win7_C.vhd VHDInputVariable=VHDTargetDisk`|  

####  <a name="VHDCreateSource"></a>VHDCreateSource  
 Ta właściwość jest używana do określenia nazwy pliku dysku VHD, który jest używany jako szablon (źródło) do tworzenia nowego pliku wirtualnego dysku twardego. Można określić nazwę pliku przy użyciu ścieżki UNC, ścieżkę lokalną, ścieżką względną lub tylko nazwę pliku. Jeśli określono tylko nazwę pliku, zestawu MDT próbuje odnaleźć pliku wirtualnego dysku twardego na komputerze docelowym. Ta właściwość jest prawidłowy tylko w przypadku scenariusza wdrożenia zestawu MDT nowego komputera.  

 Ta właściwość jest zwykle ustawiona za pomocą kroku sekwencji zadań utworzonych przy użyciu **tworzenia wirtualnych dysków twardych (VHD)** typ sekwencji zadań. Można zastąpić wartość która **tworzenia wirtualnych dysków twardych (VHD)**krok sekwencji zadań ustawia przez skonfigurowanie tej właściwości w CustomSettings.ini.  

> [!NOTE]
>  Aby skonfigurować tę właściwość w CustomSettings.ini, należy dodać tę właściwość, aby **właściwości** wiersza w CustomSettings.ini.  

 Aby uzyskać powiązane właściwości, które są używane przez pliki VHD zobacz:  

-   **VHDCreateDiffVHD**  

-   **VHDCreateFileName**  

-   **VHDCreateSizeMax**  

-   **VHDCreateType**  

-   **Dyskivhd**  

-   **VHDInputVariable**  

-   **VHDOutputVariable**  

-   **VHDTargetDisk**  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*Nazwa*|Nazwa pliku określona za pomocą ścieżki UNC, ścieżkę lokalną, ścieżką względną lub tylko nazwę pliku. Jeśli określono tylko nazwę pliku, zestawu MDT próbuje odnaleźć pliku wirtualnego dysku twardego na komputerze docelowym.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] VHDCreateSizeMax=130048 VHDCreateSource=\\wdg-mdt-01\vhds\win7_template.vhd VHDCreateType=FIXED VHDCreateFileName=Win7_C.vhd VHDInputVariable=VHDTargetDisk`|  

####  <a name="VHDCreateType"></a>VHDCreateType  
 Ta właściwość jest używana do określania typu pliku wirtualnego dysku twardego, który określono w **VHDCreateFileName** właściwości i może być jedną z następujących typów plików wirtualnego dysku twardego:  

-   **Stały plik VHD**. Dla tego typu wirtualnego dysku twardego rozmiar określony podczas tworzenia dysku VHD jest przydzielane i nie zmienia się automatycznie po utworzeniu. Na przykład w przypadku utworzenia 24\-gigabajt \(GB\) stałej pliku VHD, plik zostanie rozmiar około 24 GB \(z odstępem używany dla wewnętrznej struktury wirtualnego dysku twardego\) niezależnie od tego, ile informacje są przechowywane w pliku wirtualnego dysku twardego.  

-   **Dynamicznie powiększający się plik VHD**. Dla tego typu wirtualnego dysku twardego jest przydzielany niewielkim odsetku rozmiar określony w czasie tworzenia dysku VHD. Następnie plik wirtualnego dysku twardego nadal się coraz więcej informacji znajduje się w nim. Jednak plik VHD nie można powiększać przekracza rozmiar określony podczas tworzenia. Na przykład jeśli tworzysz 24 GB dynamicznie powiększający się wirtualny dysk twardy będzie małych podczas tworzenia. Jednak jako informacje są przechowywane w pliku VHD, plik będzie rosnąć, ale nigdy nie przekracza maksymalny rozmiar 24 GB.  

 Ta właściwość jest prawidłowa tylko dla scenariusza wdrożenia zestawu MDT nowego komputera.  

> [!NOTE]
>  Maksymalny rozmiar pliku VHD jest określona w **VHDCreateSizeMax** właściwości.  

 Ta właściwość jest zwykle ustawiona za pomocą kroku sekwencji zadań utworzonych przy użyciu **Utwórz wirtualny dysk twardy \(wirtualnego dysku twardego\)**  typ sekwencji zadań. Można zastąpić wartość która **Utwórz wirtualny dysk twardy \(wirtualnego dysku twardego\)**  krok sekwencji zadań ustawia przez skonfigurowanie tej właściwości w CustomSettings.ini.  

> [!NOTE]
>  Aby skonfigurować tę właściwość w CustomSettings.ini, należy dodać tę właściwość, aby **właściwości** wiersza w CustomSettings.ini.  

 Aby uzyskać powiązane właściwości, które są używane przez pliki VHD zobacz:  

-   **VHDCreateDiffVHD**  

-   **VHDCreateFileName**  

-   **VHDCreateSizeMax**  

-   **VHDCreateSource**  

-   **Dyskivhd**  

-   **VHDInputVariable**  

-   **VHDOutputVariable**  

-   **VHDTargetDisk**  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|**ROZWIJANIA**|Tworzy plik stałego wirtualnego dysku twardego|  
|**STAŁE**|Tworzy plik dynamicznie powiększających się dysków VHD|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] VHDCreateSizeMax=130048 VHDCreateType=EXPANDABLE VHDCreateFileName=Win7_C.vhd VHDInputVariable=VHDTargetDisk`|  

####  <a name="VHDDisks"></a>Dyskivhd  
 Ta właściwość zawiera listę liczb dysku fizycznego, przypisane do plików VHD rozdzielone spacjami. Zawsze zostanie utworzony plik wirtualnego dysku twardego, zestawu MDT dodaje indeks dysku nowo utworzonego dysku do tej właściwości przy użyciu **indeksu** właściwość **Win32\_DiskDrive** klasy usługi WMI.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

 Ta właściwość jest zwykle ustawiona za pomocą kroku sekwencji zadań utworzonych przy użyciu **Utwórz wirtualny dysk twardy \(wirtualnego dysku twardego\)**  typ sekwencji zadań. Można zastąpić wartość która **Utwórz wirtualny dysk twardy \(wirtualnego dysku twardego\)**  krok sekwencji zadań ustawia przez skonfigurowanie tej właściwości w CustomSettings.ini.  

> [!NOTE]
>  Aby skonfigurować tę właściwość w CustomSettings.ini, należy dodać tę właściwość, aby **właściwości** wiersza w CustomSettings.ini.  

 Aby uzyskać powiązane właściwości, które są używane przez pliki VHD zobacz:  

-   **VHDCreateDiffVHD**  

-   **VHDCreateFileName**  

-   **VHDCreateSizeMax**  

-   **VHDCreateSource**  

-   **VHDCreateType**  

-   **VHDInputVariable**  

-   **VHDOutputVariable**  

-   **VHDTargetDisk**  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*index3 index2 indeks1*|Lista numerów dysku fizycznego, przypisane do plików VHD rozdzielone spacjami — na przykład *1 2 5*.|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="VHDInputVariable"></a>VHDInputVariable  
 Ta właściwość zawiera zmienna, która zawiera dysk na komputerze docelowym, w którym mają zostać utworzone pliki VHD. Zestaw MDT tworzy pliki wirtualnego dysku twardego w folderze wirtualnego dysku twardego w folderze głównym tego dysku.  

> [!NOTE]
>  Jeśli ta właściwość jest pominięty, zestawu MDT próbuje utworzyć pliki VHD w folderze wirtualnego dysku twardego w folderze głównym dysku systemowego pierwszy.  

 Ta właściwość jest zwykle ustawiona za pomocą kroku sekwencji zadań utworzonych przy użyciu **Utwórz wirtualny dysk twardy \(wirtualnego dysku twardego\)**  typ sekwencji zadań. Można zastąpić wartość która **Utwórz wirtualny dysk twardy \(wirtualnego dysku twardego\)**  krok sekwencji zadań ustawia przez skonfigurowanie tej właściwości w CustomSettings.ini.  

> [!NOTE]
>  Aby skonfigurować tę właściwość w CustomSettings.ini, należy dodać tę właściwość, aby **właściwości** wiersza w CustomSettings.ini.  

 Aby uzyskać powiązane właściwości, które są używane przez pliki VHD zobacz:  

-   **VHDCreateDiffVHD**  

-   **VHDCreateFileName**  

-   **VHDCreateSizeMax**  

-   **VHDCreateSource**  

-   **VHDCreateType**  

-   **VHDDrives**  

-   **VHDOutputVariable**  

-   **VHDTargetDisk**  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*Zmienna*|Zmienna, która zawiera literę dysku na komputerze docelowym, w którym mają zostać utworzone pliki VHD. Zestaw MDT tworzy pliki wirtualnego dysku twardego w folderze wirtualnego dysku twardego w folderze głównym tego dysku. Na przykład, jeśli ta właściwość ma wartość **VHDTargetDisk**, **VHDTargetDisk** właściwość zawiera literę dysku \(takich jak *H*\).|  

|**Przykład**|  
|-|  
|`VHDCreateSizeMax=130048 VHDCreateType=EXPANDABLE VHDCreateFileName=Win7_C.vhd  VHDInputVariable=VHDTargetDisk`|  

####  <a name="VHDOutputVariable"></a>VHDOutputVariable  
 Ta właściwość zawiera zmienna, która zawiera numer dysku fizycznego, który został przypisany do nowo utworzony plik VHD. Zawsze zostanie utworzony plik wirtualnego dysku twardego, zestawu MDT ustawia tę właściwość na indeks dysku przy użyciu nowo utworzony dysk **indeksu** właściwość **Win32\_DiskDrive** klasy usługi WMI.  

 Ta właściwość jest zwykle ustawiona za pomocą kroku sekwencji zadań utworzonych przy użyciu **Utwórz wirtualny dysk twardy \(wirtualnego dysku twardego\)**  typ sekwencji zadań. Można zastąpić wartość która **Utwórz wirtualny dysk twardy \(wirtualnego dysku twardego\)**  krok sekwencji zadań ustawia przez skonfigurowanie tej właściwości w CustomSettings.ini.  

> [!NOTE]
>  Aby skonfigurować tę właściwość w CustomSettings.ini, należy dodać tę właściwość, aby **właściwości** wiersza w CustomSettings.ini.  

 Aby uzyskać powiązane właściwości, które są używane przez pliki VHD zobacz:  

-   **VHDCreateDiffVHD**  

-   **VHDCreateFileName**  

-   **VHDCreateSizeMax**  

-   **VHDCreateSource**  

-   **VHDCreateType**  

-   **Dyskivhd**  

-   **VHDInputVariable**  

-   **VHDTargetDisk**  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|\-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*Zmienna*|Zmienna zostanie zawiera numer dysku fizycznego, przypisany do nowo utworzony plik VHD. Na przykład, jeśli ta właściwość ma wartość **OSDDiskIndex**, **OSDDiskIndex** właściwości będzie zawierać numer dysku fizycznego, przypisany do nowo utworzony plik VHD \(takich jak *4*\).|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="VHDTargetDisk"></a>VHDTargetDisk  
 Określa dysk, na komputerze docelowym, na którym ma być utworzony wirtualny dysk twardy. Ta właściwość jest później przywoływany w [VHDInputVariable](#VHDInputVariable) właściwości.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

 Aby uzyskać powiązane właściwości, które są używane przez pliki VHD zobacz:  

-   **VHDCreateDiffVHD**  

-   **VHDCreateFileName**  

-   **VHDCreateSizeMax**  

-   **VHDCreateSource**  

-   **VHDCreateType**  

-   **Dyskivhd**  

-   **VHDInputVariable**  

-   **VHDOutputVariable**  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|\-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*Dysk*|Określa dysk, na którym ma być utworzony wirtualny dysk twardy|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="VMHost"></a>VMHost  
 Określa nazwę Hyper\-V hosta z uruchomioną maszynę Wirtualną, gdy zestaw MDT jest uruchomiona. Ta właściwość jest dostępna tylko wtedy, gdy Hyper\-V składników integracji są zainstalowane i uruchomione.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

Tabela 4 zawiera listę systemów operacyjnych Windows tego zestawu MDT obsługuje i ich odpowiednich Hyper\-obsługuje składników integracji V.  

### <a name="table-4-windows-operating-systems-and-hyper-v-integration-components-support"></a>Tabela 4. Systemy operacyjne Windows i obsługi składniki integracji funkcji Hyper-V  

|**System operacyjny**|**Składniki integracji funkcji Hyper-V**|  
|-|-|  
|Windows PE|Składniki integracji są niedostępne.|  
|Windows 7|Domyślnie w wersjach Enterprise, Ultimate i Professional dostępne.|  
|Windows Server 2008 R2|Domyślnie we wszystkich wersjach dostępne.|  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*Nazwa*|Nazwa hosta funkcji Hyper-V uruchomione maszyny Wirtualnej, którym jest uruchomiona zestawu MDT|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="VMName"></a>VMName  
 Określa nazwę maszyny wirtualnej, w którym jest uruchomiona zestawu MDT. Ta właściwość jest tylko dostępne, gdy składniki integracji funkcji Hyper-V są zainstalowane i uruchomione.  

 Tabela 5 zawiera listę systemów operacyjnych Windows, które są obsługiwane przez zestaw MDT i ich odpowiednie składniki integracji funkcji Hyper-V pomocy technicznej.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

### <a name="table-5-windows-operating-systems-and-hyper-v-integration-components-support"></a>Tabela 5. Systemy operacyjne Windows i obsługi składniki integracji funkcji Hyper-V  

|**System operacyjny**|**Składniki integracji funkcji Hyper-V**|  
|-|-|  
|Windows PE|Składniki integracji są niedostępne.|  
|Windows 7|Domyślnie w wersjach Enterprise, Ultimate i Professional dostępne.|  
|Windows Server 2008 R2|Domyślnie we wszystkich wersjach dostępne.|  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*Nazwa*|Nazwa maszyny wirtualnej, w którym jest uruchomiona zestawu MDT|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="VMPlatform"></a>VMPlatform  
 Określa określone informacje na temat środowiska wirtualizacji dla komputera docelowego, gdy komputer docelowy jest maszyny Wirtualnej. Maszyna wirtualna platformy jest określany za pomocą usługi WMI.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|**Hyper-V**|Funkcja Hyper-V|  
|**VirtualBox**|Pole wirtualnego|  
|**VMware**|Platforma wirtualizacji VMware|  
|**Xen**|Citrix Xen Server|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="VRefresh"></a>VRefresh  
 Pionową częstotliwość odświeżania dla monitora na komputerze docelowym. Częstotliwość odświeżania pionowego jest określona w Hz. W tym przykładzie wartość **60** wskazuje częstotliwość odświeżania pionowego monitora 60 Hz. Ta wartość jest wstawiany odpowiednie ustawienia konfiguracji w pliku Unattend.xml.  

> [!NOTE]
>  Wartości domyślne (w pliku szablonu Unattend.xml) są rozdzielczość pozioma 1024 pikseli, rozdzielczość pionowa 768 pikseli, 32-bitowej głębi kolorów i częstotliwość odświeżania pionowego 60 Hz.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*refresh_rate*|Pionową częstotliwość odświeżania dla monitora na komputerze docelowym w Hz|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] BitsPerPel=32 VRefresh=60 XResolution=1024 YResolution=768`|  

####  <a name="VSSMaxSize"></a>VSSMaxSize  
 Ta właściwość jest używana do przekazania wartości do **maxsize** parametr **vssadmin resize shadowstorage** w **Vssadmin** polecenia. **Maxsize** parametr jest używany do określania maksymalną ilość miejsca na wolumin docelowy, który może służyć do przechowywania kopii w tle. Aby uzyskać więcej informacji na temat **maxsize** parametrów, zobacz [Vssadmin resize shadowstorage](http://technet.microsoft.com/library/cc788050\(WS.10\).aspx).  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*maxsize_value*|Określa maksymalną ilość miejsca, który może służyć do przechowywania kopii w tle. Można określić wartość w bajtach lub jako procent woluminu docelowego.<br /><br /> Aby określić wartość:<br /><br /> — W bajtach, wartość musi być 300 MB lub większy i akceptuje następujące sufiksy: KB, MB, GB, TB, PB i EB. Można również użyć jako sufiksy B, K, M, G, T, P i E — na przykład:<br /><br /> `VSSMaxSize=60G`<br /><br /> -Jako wartość procentową, należy użyć znaku % jako sufiks wartość liczbowa — na przykład:<br /><br /> `VSSMaxSize=20%`<br /><br /> Uwaga:<br /><br /> Jeśli nie podano sufiks, domyślny sufiks to bajtów. Na przykład `VSSMaxSize=1024` oznacza to, że **VSSMaxSize** zostanie ustawiona do 1024 bajty.<br /><br /> Jeśli wartość jest równa **UNBOUNDED**, nie jest umieszczona na ilość miejsca do magazynowania, który może służyć ograniczona — na przykład:<br /><br /> `VSSMaxSize=UNBOUNDED`|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] VSSMaxSize=25%`|  

####  <a name="WDSServer"></a>WDSServer  
 Komputer z systemem usług wdrażania systemu Windows, który jest używany do instalowania usług wdrażania systemu Windows obrazów. Wartością domyślną jest serwerem usług wdrażania systemu Windows, z którego obraz został zainicjowany.  

> [!NOTE]
>  Ta właściwość dynamicznie jest ustawiana przez skrypty MDT i nie jest skonfigurowany w CustomSettings.ini lub DB zestawu MDT. Traktować tę właściwość jako tylko do odczytu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|||||  
|ZESTAW MDT BAZY DANYCH|||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*WDS_server*|Nazwa komputera z usługami wdrażania systemu Windows|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="WindowsSource"></a>WindowsSource  
 Zestaw MDT używa tej właściwości można ustawić lokalizację folderu sources\sxs w udostępnionym folderze sieciowym, który zawiera pliki źródłowe systemu operacyjnego. Ta właściwość jest używana podczas:  

-   Zestaw MDT jest uruchomiona niestandardowej sekwencji zadań lub wdrażanie niestandardowego obrazu  

-   Zestaw MDT jest instalowania ról lub funkcji w systemie Windows 8 i Windows Server 2012  

-   Komputer nie ma dostępu do Internetu  

 Jeśli sytuacja opisana w występuje powyższej listy punktowanej MDT może być nie można znaleźć lokalnie plików źródłowych systemu operacyjnego i instalacji będzie podejmować próby pobierania plików z Internetu. Ponieważ komputer nie ma dostępu do Internetu, proces zakończy się niepowodzeniem. Ustawienie tej właściwości na odpowiednią wartość pomaga zapobiec występowaniu tego problemu.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|***folder_unc***|Ścieżka UNC do folderu Sources\sxs wdrażanego systemu operacyjnego.<br /><br /> Uwaga:<br /><br /> Ścieżka UNC musi zawierać folderu Sources\sxs.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] WindowsSource=%DeployRoot%\Operating Systems\Windows 8\Sources\sxs`|  

####  <a name="WipeDisk"></a>Narzędzia WipeDisk  
 Określa, czy można wyczyścić dysku. Jeśli **narzędzia WipeDisk** ma wartość PRAWDA, skrypt ZTIWipeDisk.wsf wyczyści dysku przy użyciu **Format** polecenia. **Format** polecenie nie jest najbardziej "bezpiecznego" sposobu czyszczenia danych z dysku.  

 Bezpiecznie czyszczenia danych z dysku należy zrobić to w sposób zgodny USA Departamentu Obrony 5220.22 standard-M, która stanowi "Aby"wyczyścić dyski magnetyczne, Zastąp wszystkie lokalizacje trzy razy (pierwszym znakiem, po raz drugi z jego dopełnieniem i trzecim razem ze znakiem losowe).  

 Gdy zestaw MDT czyści dysku, używa **Format** z **/P:3** przełącznika, który powoduje, że **Format** na zero, co sektora na woluminie i wykonywanie operacji trzech razy. Nie istnieje sposób sprawdzić **Format** polecenie, aby użyć określonego znaku lub losowych znaków.  

> [!NOTE]
>  Jeśli dysk musi być bezpiecznie czyszczone, narzędzie czyszczenia dysku bezpiecznego firmy Microsoft powinni zostać dodani do przy użyciu sekwencji zadań **Uruchom wiersz polecenia** krok sekwencji zadań.  

> [!CAUTION]
>  Wartość tej właściwości należy określić wielkimi literami, aby skrypty wdrażania prawidłowo może go odczytać.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|**WARTOŚĆ TRUE**|Jeśli **narzędzia WipeDisk** ustawiono **TRUE**, będą formatowane Win32_DiskPartition na DiskIndex 0 i pod indeksem 0.|  
|**WARTOŚĆ FALSE**|Dysk nie zostanie sformatowany.|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] WipeDisk=TRUE`|  

####  <a name="WizardSelectionProfile"></a>WizardSelectionProfile  
 Nazwa profilu jest używane przez kreatora w celu filtrowania wyświetlanie różne elementy.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*nazwa_profilu*|Nazwa profilu wykorzystywane przez kreatora w celu filtrowania wyświetlania różnych elementów|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] WizardSelectionProfile=SelectTaskSequenceOnly`|  

####  <a name="WSUSServer"></a>WSUSServer  
 Jest to nazwa serwera Windows Server Update Services (WSUS), która powinna być używana na komputerze docelowym, jeśli wyszukiwanie, pobieranie i instalowanie aktualizacji.  

 Aby uzyskać więcej informacji o jakie skrypt używa tej właściwości, zobacz [ZTIWindowsUpdate.wsf](#ZTIWindowsUpdate.wsf).  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*nazwa_serwera*|Nazwa serwera programu WSUS, określona w formacie HTTP|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] WSUSServer=http://WSUSServerName[Settings] Priority=Default  [Default] WSUSServer=http://WSUSServerName`|  

####  <a name="WUMU_ExcludeKB"></a>WUMU_ExcludeKB  
 Lista aktualizacji oprogramowania Windows Update/Microsoft Update do ignorowania (przez artykuły bazy wiedzy Knowledge Base).  

 Członkowie zespołu projektu wdrożenia jest przydatne do okresowego przeglądania listy aktualizacji instalowane przez skrypt ZTIWindowsUpdate.wsf, aby sprawdzić, czy każda aktualizacja spełnia potrzeby oraz oczekiwania projektu. Wszystkie aktualizacje są rejestrowane i rejestrowane w pliku ZTIWindowsUpdate.log, który jest generowany podczas wdrażania. Każda aktualizacja zostanie wskazać jej stan, jak zainstalować lub POMINĄĆ i wyświetla UpdateID, nazwę aktualizacji i QNumber skojarzone z każdą z aktualizacji. Jeśli aktualizacja musi zostać wyłączone, tej aktualizacji należy dodać do pliku CustomSettings.ini (wdrożeniach LTI).  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*WUMU_ExcludeKB*|Lista aktualizacji oprogramowania Windows Update/Microsoft Update, aby zignorować przez QNumber|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] WUMU_ExcludeKB1=925471`|  

#### <a name="wumuexcludeid"></a>WUMU_ExcludeID  
 Lista Windows Update/Microsoft Update aktualizacji oprogramowania, aby zignorować (przez identyfikator powiązanej aktualizacji).  

 Członkowie zespołu projektu wdrożenia jest przydatne do okresowego przeglądania listy aktualizacji instalowane przez skrypt ZTIWindowsUpdate.wsf, aby sprawdzić, czy każda aktualizacja spełnia potrzeby oraz oczekiwania projektu. Wszystkie aktualizacje są rejestrowane i rejestrowane w pliku ZTIWindowsUpdate.log, który jest generowany podczas wdrażania. Każda aktualizacja zostanie wskazać jej stan, jak zainstalować lub POMINĄĆ i wyświetla UpdateID, nazwę aktualizacji i QNumber skojarzone z każdą z aktualizacji. Jeśli aktualizacja powinien być wykluczony, tej aktualizacji należy można dodać do pliku CustomSettings.ini (wdrożeniach LTI).  

 Na przykład jeśli powinien być wykluczony instalacji narzędzia systemu Windows do usuwania złośliwego oprogramowania, wyszukiwania liniowego ZTIWindowsUpdate.log, pokazujący, gdzie zidentyfikowane i zainstalowanych aktualizacji, a następnie wybierz numer UpdateID. Na przykład numer UpdateID narzędzie systemu Windows do usuwania złośliwego oprogramowania jest d adbe6425-6560-4 40-9478-1e35b3cdab4f.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|||ZTI||  

|**Wartość**|**Opis**|  
|-|-|
|*WUMU_ExcludeID*|Lista aktualizacji oprogramowania Windows Update/Microsoft Update, aby zignorować numerem UpdateID|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] WUMU_ExcludeID1={adbe6425-6560-4d40-9478-1e35b3cdab4f}[Settings] Priority=Default  [Default] WUMU_ExcludeID1={adbe6425-6560-4d40-9478-1e35b3cdab4f}`|  

####  <a name="XResolution"></a>XResolution  
 Rozdzielczość pozioma monitora na komputerze docelowym określonym w pikselach. W tym przykładzie wartość **1024** wskazuje rozdzielczość pozioma monitora to 1024 pikseli. Ta wartość jest wstawiany odpowiednie ustawienia konfiguracji w pliku Unattend.xml.  

> [!NOTE]
>  Wartości domyślne (w pliku szablonu Unattend.xml) są rozdzielczość pozioma 1024 pikseli, rozdzielczość pionowa 768 pikseli, 32-bitowej głębi kolorów i częstotliwość odświeżania pionowego 60 Hz.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*horizontal_resolution*|Rozdzielczość pozioma monitora na komputerze docelowym w pikselach|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] BitsPerPel=32 VRefresh=60 XResolution=1024 YResolution=768[Settings] Priority=Default  [Default] BitsPerPel=32 VRefresh=60 XResolution=1024 YResolution=768`|  

####  <a name="YResolution"></a>YResolution  
 Rozdzielczość w pionie monitora na komputerze docelowym określonym w pikselach. W tym przykładzie wartość **768** oznacza rozdzielczość w pionie monitora 768 pikseli. Ta wartość wstawiany pobiera odpowiednie ustawienia konfiguracji w pliku Unattend.xml.  

> [!NOTE]
>  Wartości domyślne (w pliku szablonu Unattend.xml) są rozdzielczość pozioma 1024 pikseli, rozdzielczość pionowa 768 pikseli, 32-bitowej głębi kolorów i częstotliwość odświeżania pionowego 60 Hz.  

|**Właściwość skonfigurowane przez**|||**Właściwość ma zastosowanie do**||  
|-|-|-|-|-|  
|BootStrap.ini|||LTI|-|  
|CustomSettings.ini|-||||  
|ZESTAW MDT BAZY DANYCH|-||ZTI|-|  

|**Wartość**|**Opis**|  
|-|-|
|*vertical_resolution*|Rozdzielczość w pionie monitora na komputerze docelowym w pikselach|  

|**Przykład**|  
|-|  
|`[Settings] Priority=Default  [Default] BitsPerPel=32 VRefresh=60 XResolution=1024 YResolution=768[Settings] Priority=Default  [Default] BitsPerPel=32 VRefresh=60 XResolution=1024 YResolution=768`|  

###  <a name="ProvidingPropertiesforSkippedDeploymentWizardPages"></a>Udostępnia właściwości dla stron kreatora pominięto wdrożenia  
 Tabela 6 zawiera listę poszczególnych stron Kreatora wdrażania, właściwość pomijania odpowiedniej strony kreatora i właściwości, które można skonfigurować, pomijanie strony kreatora.  

 Jeśli **SkipWizard** właściwość jest używana, aby pominąć wszystkie strony Kreatora wdrażania, podaj wszystkie właściwości w **skonfigurować te właściwości**kolumny. Przykłady różnych scenariuszy wdrażania, które pominąć stron Kreatora wdrażania można znaleźć w sekcji "Pełni zautomatyzowany LTI scenariuszu wdrażania" w dokumencie MDT *Microsoft Deployment Toolkit przykłady Guide*.  

> [!NOTE]
>  W przypadkach gdy **skonfigurować te właściwości** kolumna jest pusta, ma właściwości, należy skonfigurować w przypadku pominięcia odpowiedni strony kreatora.  

### <a name="table-6-deployment-wizard-pages"></a>Tabela 6. Strony kreatora  

|**Pomiń tę stronę kreatora**|**Za pomocą tej właściwości**|**Skonfigurować te właściwości**|  
|-|-|-|  
|**Witamy**|SkipBDDWelcome||  
|**Określ poświadczenia do połączenia udziały sieciowe**|Pominięto zapewniając właściwości w następnej kolumnie|— Identyfikator użytkownika<br /><br /> -UserDomain<br /><br /> -Hasła użytkownika|  
|**Sekwencja zadań**|SkipTaskSequence|-TaskSequenceID|  
|**Szczegóły komputera**|SkipComputerName,<br /><br /> SkipDomainMembership|-OSDComputerName<br /><br /> -JoinWorkgroup<br /><br /> — lub —<br /><br /> -Przyłączania<br /><br /> -Administrator domeny|  
|**Dane użytkownika**|SkipUserData|-UDDir<br /><br /> -UDShare<br /><br /> -UserDataLocation|  
|**Przenoszenia danych i ustawień**|SkipUserData|-UDDir<br /><br /> -UDShare<br /><br /> -UserDataLocation|  
|**Dane użytkownika (przywracanie)**|SkipUserData|-UDDir<br /><br /> -UDShare<br /><br /> -UserDataLocation|  
|**Kopii zapasowych komputerów**|SkipComputerBackup|-BackupDir<br /><br /> -BackupShare<br /><br /> -ComputerBackupLocation|  
|**Klucz produktu**|SkipProductKey|-ProductKey<br /><br /> — lub —<br /><br /> -OverrideProductKey|  
|**Pakiety językowe**|SkipPackageDisplay|LanguagePacks|  
|**Ustawienia regionalne i czas**|SkipLocaleSelection, SkipTimeZone|-KeyboardLocale<br /><br /> -UserLocale<br /><br /> -UILanguage<br /><br /> -TimeZoneName|  
|**Role i funkcje**|SkipRoles|-OSRoles<br /><br /> -OSRoleServices<br /><br /> -OSFeatures|  
|**Aplikacje**|SkipApplications|Aplikacje|  
|**Hasło administratora**|SkipAdminPassword|adminPassword|  
|**Administratorzy lokalni**|SkipAdminAccounts|— Administratorzy|  
|**Przechwycenie obrazu**|SkipCapture|-ComputerBackupLocation|  
|**Funkcja BitLocker**|SkipBitLocker|-BDEDriveLetter<br /><br /> -BDEDriveSize<br /><br /> -BDEInstall<br /><br /> -BDEInstallSuppress<br /><br /> -BDERecoveryKey<br /><br /> -TPMOwnerPassword<br /><br /> -OSDBitLockerStartupKeyDrive<br /><br /> -OSDBitLockerWaitForEncryption|  
|**Gotowy do rozpoczęcia**|SkipSummary|—|  
|**Wdrożenie systemu operacyjnego została ukończona pomyślnie**|SkipFinalSummary|—|  
|**Wdrożenie systemu operacyjnego nie została pomyślnie ukończona.**|SkipFinalSummary|—|  

##  <a name="Scripts"></a>Skrypty  
 Skrypty używać we wdrożeniach LTI i ZTI właściwości odwołania, które określają ustawienia konfiguracji używane w procesie wdrażania i kroki tej procedury. Użyj tej sekcji odwołania, aby go określić poprawne skryptów do uwzględnienia w działaniach i nieprawidłowe argumenty podczas uruchamiania każdego skryptu. Poniższe informacje są przeznaczone dla każdego skryptu:  

-   **Nazwa**. Określa nazwę skryptu.  

-   **Opis elementu**. Zawiera opis przeznaczenia skrypt, a wszelkie stosowne informacje dotyczące dostosowywania skryptu.  

-   **Dane wejściowe**. Wskazuje pliki używane dla danych wejściowych do skryptu.  

-   **Dane wyjściowe**. Wskazuje pliki utworzone lub zmodyfikowane przez skrypt.  

-   **Odwołania**. Wskazuje inne skrypty lub pliki konfiguracyjne, które są używane przez skrypt.  

-   **Lokalizacja**. Wskazuje folder, w którym można znaleźć skryptu. W informacjach o lokalizacji są używane następujące zmienne:  

    -   **Program_Files**. Ta zmienna wskazuje lokalizację, w folderze Program Files na komputerze, w którym jest zainstalowany zestaw MDT.  

    -   **dystrybucji**. Ta zmienna wskazuje lokalizację folderu dystrybucji dla udziału wdrożenia.  

    -   **Platforma**. Ta zmienna jest symbolem zastępczym dla platformy systemu operacyjnego (x86 lub x64).  

-   **Użyj**. Udostępnia polecenia i opcje, które można określić.  

-   **Argumenty i opis**. Wskazuje nieprawidłowe argumenty może być określony dla skryptu i krótki opis oznacza każdy argument.  

-   **Właściwości**. Właściwości przywoływany przez skrypt.  

###  <a name="BDD_Autorun.wsf"></a>BDD_Autorun.wsf  
 Ten skrypt wyświetla okno dialogowe, wskazującą nośników wdrażania dodaje użytkownika utworzone przez proces MDT (na przykład rozruchowego dysku DVD lub wymiennym dysku twardym). Ten komunikat jest wyświetlany na 15 sekund. Jeśli nie podjęto żadnej akcji, skrypt zostanie uruchomiony LiteTouch.vbs.  

 Aby uzyskać więcej informacji na temat LiteTouch.vbs, zobacz odpowiedni temat w [skryptów](#Scripts).  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje wymagane przez skrypty w celu zakończenia procesu wdrażania|  
|**Dane wyjściowe**|Brak|  
|**Odwołania**|**LiteTouch.vbs**. Inicjuje LTI|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|Brak|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|Brak|Brak|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|Brak|||  

###  <a name="BDD_Welcome_ENU.xml"></a>BDD_Welcome_ENU.XML  
 Ten plik XML zawiera kod skryptu i układ HTML **wdrażania systemu Windows — Zapraszamy** strona, która jest wyświetlana na początku Kreatora wdrażania. Ten plik XML jest odczytywany przez Wizard.hta, w którym jest uruchomiona na stronach kreatora osadzonego w tym pliku XML.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|Brak|  
|**Dane wyjściowe**|Brak|  
|**Odwołania**|- **NICSettings_Definition_ENU.xml**. Umożliwia użytkownikowi określić ustawienia konfiguracji dla kart sieciowych<br /><br /> - **Wizard.hta**. Wyświetla strony Kreatora wdrażania<br /><br /> - **WPEUtil.exe**. Inicjuje środowisko Windows PE i połączeń sieciowych; Inicjuje LTI|  
|**Lokalizacja**|*dystrybucji*\Tools\\*platformy*|  
|**Użycie**|`mshta.exeWizard.hta BDD_Welcome_ENU.xml`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|Brak|Brak|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**KeyboardLocalePE**|-||  
|**WelcomeWizardCommand**||-|  
|**WizardComplete**||-|  

###  <a name="Credentials_ENU.xml"></a>Credentials_ENU.XML  
 Ten plik XML zawiera kod skryptu i układ HTML **Określ poświadczenia do nawiązywania połączenia z udziałami sieciowymi** strona kreatora w Kreatorze wdrażania. Ten plik XML jest odczytywany przez Wizard.hta, w którym jest uruchomiona na stronach kreatora osadzonego w tym pliku XML.  

> [!NOTE]
>  Ta strona kreatora jest wyświetlana tylko, jeśli występuje błąd podczas sprawdzania poprawności poświadczeń użytkownika wstępnie zdefiniowane.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|Brak|  
|**Dane wyjściowe**|Brak|  
|**Odwołania**|**Credentials_scripts.vbs**. Zawiera funkcje obsługi poświadczeń użytkownika|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`mshta.exe Wizard.hta /NotWizard /definition:Credentials_ENU.xml [/ValidateAgainstDomain:domain &#124; /ValidateAgainstUNCPath:uncpath]  </DoNotSave> </LeaveShareOpen>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|Brak|Brak|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|Brak|||  

###  <a name="Credentials_scripts.vbs"></a>Credentials_scripts.vbs  
 Ten skrypt analizuje argumenty, które zostały podane podczas ładowania pliku Credentials_ENU.xml w Kreatorze wdrażania. Wykonuje także sprawdzanie poprawności poświadczeń użytkownika. Ten skrypt jest odczytywany przez plik Credentials_ENU.xml.  

 Aby uzyskać więcej informacji na temat Credentials_ENU.xml, zobacz odpowiedni temat w [skryptów](#Scripts).  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|Brak|  
|**Dane wyjściowe**|Komunikat zdarzenia są zapisywane w tych plikach dziennika:<br /><br /> - **Credentials_scripts.log**. Plik dziennika zawierający zdarzenia wygenerowane przez ten skrypt<br /><br /> - **BDD.log**. Plik dziennika zawierający zdarzenia generowane przez wszystkie skrypty zestawu MDT|  
|**Odwołania**|Brak|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`<script language="VBScript" src="Credentials_scripts.vbs"/>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|Brak|Brak|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**UserCredentials**||-|  
|**UserDomain**|-||  

###  <a name="DeployWiz_Definition_ENU.xml"></a>DeployWiz_Definition_ENU.xml  
 Ten plik XML zawiera kod skryptów i układ HTML dla każdej strony Kreatora wdrażania. Ten plik jest odczytywany przez Wizard.hta, w którym jest uruchomiona na stronach kreatora osadzonego w tym pliku XML. Ten plik XML zawiera na następujących stronach kreatora:  

-   **Witamy**  

-   **Określ poświadczenia do połączenia udziały sieciowe**  

-   **Sekwencja zadań**  

-   **Szczegóły komputera**  

-   **Dane użytkownika**  

-   **Przenoszenia danych i ustawień**  

-   **Dane użytkownika (przywracanie)**  

-   **Kopii zapasowych komputerów**  

-   **Klucz produktu**  

-   **Pakiety językowe**  

-   **Ustawienia regionalne i czas**  

-   **Role i funkcje**  

-   **Aplikacje**  

-   **Hasło administratora**  

-   **Administratorzy lokalni**  

-   **Przechwycenie obrazu**  

-   **Funkcja BitLocker**  

-   **Gotowy do rozpoczęcia**  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|Brak|  
|**Dane wyjściowe**|Brak|  
|**Odwołania**|- **DeployWiz_Initialization.vbs**. Obejmuje funkcje pomocy technicznej i podprocedury używane przez skrypt<br /><br /> - **DeployWiz_Validation.vbs**. Obejmuje funkcje pomocy technicznej i podprocedury używane przez skrypt<br /><br /> - **ZTIBackup.wsf**. Tworzy kopię zapasową komputera docelowego<br /><br /> - **ZTIPatches.wsf**. Instaluje aktualizacje (pakiety językowe, aktualizacje zabezpieczeń itd.)<br /><br /> - **ZTIUserState.wsf**. Inicjuje migracji stanu użytkownika do przechwycenia i przywrócenia stanu użytkownika na komputerze docelowym|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|Brak|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|Brak|Brak|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**DeploymentMethod**|-||  
|**DeploymentType**|-||  
|**DoCapture**|-||  
|**ImageBuild**|-||  
|**ImageFlags**|-||  
|**IsBDE**|-||  
|**IsServerOS**|-||  
|**Przyłączania**|-||  
|**OSDComputerName**|-||  
|**OSVersion**|-||  
|**SkipAdminAccounts**|-||  
|**SkipAdminPassword**|-||  
|**SkipApplications**|-||  
|**SkipBitLocker**|-||  
|**SkipCapture**|-||  
|**SkipComputerBackup**|-||  
|**SkipComputerName**|-||  
|**SkipDomainMembership**|-||  
|**SkipLocaleSelection**|-||  
|**SkipPackageDisplay**|-||  
|**SkipProductKey**|-||  
|**SkipRoles**|-||  
|**SkipSummary**|-||  
|**SkipTaskSequence**|-||  
|**SkipTimeZone**|-||  
|**SkipUserData**|-||  
|**TaskSequenceTemplate**|-||  
|**UserDomain**|-||  
|**Nazwa użytkownika**|-||  
|**Hasła użytkownika**|-||  
|**USMTOfflineMigration**|-||  

###  <a name="DeployWiz_Initialization.vbs"></a>DeployWiz_Initialization.vbs  
 Ten skrypt inicjuje strony **Kreatora wdrażania** (przechowywane w [DeployWiz_Definition_ENU.xml](#DeployWiz_Definition_ENU.xml)). Zawiera również funkcje i procedur, które wywołuje Kreatora wdrażania podczas wdrażania LTI.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|- **DomainOUList.xm**l. Zawiera listę domen, jednostek organizacyjnych<br /><br /> - **ListOfLanguages.xml**<br /><br /> - **LocationServer.xml**. Zawiera listę akcji wdrażania dostępnych<br /><br /> - **Zmienne środowiskowe**. Zawiera listę wartości właściwości, niestandardowe właściwości połączenia bazy danych, reguły wdrażania i inne informacje, które skrypty wymagane do ukończeniu procesu wdrażania; zmienne środowiskowe są wypełniane przy ZTIGather.wsf|  
|**Dane wyjściowe**|Komunikat zdarzenia są zapisywane w tych plikach dziennika:<br /><br /> - **DeployWiz_Initialization.log**. Plik dziennika zawierający zdarzenia wygenerowane przez ten skrypt<br /><br /> - **BDD.log**. Plik dziennika zawierający zdarzenia generowane przez wszystkie skrypty zestawu MDT|  
|**Odwołania**|**ZTIApplications.wsf**. Inicjuje instalację aplikacji|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`<script language="VBScript" src="DeployWiz_Initialization.vbs"/>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|Brak|Brak|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**Architektura**|-||  
|**Aplikacje**|-||  
|**BackupDir**|-||  
|**Plik**|-||  
|**BackupShare**|-||  
|**BDEInstall**|-||  
|**BDEKeyLocation**|-||  
|**BDERecoveryKey**|-||  
|**BDEWaitForEncryption**|-||  
|**CapableArchitecture**|-||  
|**ComputerBackupLocation**|-||  
|**CustomWizardSelectionProfile**|-||  
|**DeploymentType**|-||  
|**DeployRoot**|-||  
|**Administrator domeny**|-||  
|**DomainAdminDomain**|-||  
|**DomainAdminPassword**|-||  
|**DomainOUs**|-||  
|**ImageBuild**|-||  
|**ImageFlags**|-||  
|**ImageLanguage**|-||  
|**ImageLanguage001**|-||  
|**ImageProcessor**|-||  
|**IsServerOS**|-||  
|**KeyboardLocale**|-||  
|**KeyboardLocale_Edit**|-||  
|**LanguagePacks**|-||  
|**LanguagePacks001**|-||  
|**LocalDeployRoot**|-||  
|**MandatoryApplications**|-||  
|**OSDComputerName**|-||  
|**OSCurrentBuild**|-||  
|**OSDBitLockerCreateRecoveryPassword**|-||  
|**OSDBitLockerMode**|-||  
|**OSDBitLockerStartupKeyDrive**|-||  
|**OSDBitLockerWaitForEncryption**|-||  
|**OSSKU**|-||  
|**OSVersion**|-||  
|**OverrideProductKey**|-||  
|**Klucz produktu**|-||  
|**SkipCapture**|-||  
|**SkipDomainMembership**|-||  
|**TaskSequenceID**|-||  
|**TimeZoneName**|-||  
|**TSGUID**|-||  
|**UDDir**|-||  
|**UDShare**|-||  
|**UILanguage**|-||  
|**UserDataLocation**|-||  
|**UserDomain**|-||  
|**Nazwa użytkownika**|-||  
|**UserLocale**|-||  
|**Hasła użytkownika**|-||  
|**WizardSelectionProfile**|-||  

###  <a name="DeployWiz_Validation.vbs"></a>DeployWiz_Validation.vbs  
 Ten skrypt inicjuje i weryfikuje informacje wpisane na stronach Kreatora wdrażania (przechowywane w [DeployWiz_Definition_ENU.xml](#DeployWiz_Definition_ENU.xml)). Ten skrypt zawiera funkcje i procedur, które wywołuje Kreatora wdrażania podczas wdrażania LTI.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|- **OperatingSystems.xml**. Zawiera listę systemów operacyjnych dla wdrożenia<br /><br /> - **Zmienne środowiskowe**. Zawiera listę wartości właściwości, niestandardowe właściwości połączenia bazy danych, reguły wdrażania i inne informacje wymagane przez skrypty w celu zakończenia procesu wdrażania; zmienne środowiskowe są wypełniane przy ZTIGather.wsf|  
|**Dane wyjściowe**|Brak|  
|**Odwołania**|- **Credentials_ENU.XML**. Wyświetla monit o poświadczenia, które będą używane podczas nawiązywania połączenia z zasobami sieciowymi<br /><br /> - **ZTIGather.wsf**. Zbiera informacje o właściwości i reguł przetwarzania|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`<script language="VBScript" src="DeployWiz_Validation.vbs"/>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|Brak|Brak|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**Architektura**|-||  
|**DeploymentType**|-|-|  
|**DeployTemplate**||-|  
|**ImageBuild**|-||  
|**ImageProcessor**|-|-|  
|**OSVersion**|-||  
|**TaskSequenceID**||-|  
|**TSGUID**|-||  
|**UserCredentials**|-||  
|**UserDomain**||-|  
|**Nazwa użytkownika**||-|  
|**Hasła użytkownika**||-|  

###  <a name="LiteTouch.vbs"></a>LiteTouch.vbs  
 Ten skrypt jest wywoływana przez Kreatora wdrażania, aby zainicjować LTI. Skrypt:  

-   Usuwa C:\MININT folder (jeśli istnieje)  

-   Sprawdza, czy komputer docelowy spełnia wymagania dotyczące uruchamiania Kreatora wdrażania przez wywołanie metody [ZTIPrereq.vbs](#ZTIPrereq.vbs)  

-   Uruchamia Kreatora wdrażania, uruchamiając [LiteTouch.wsf](#LiteTouch.wsf)  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|Brak|  
|**Dane wyjściowe**|Brak|  
|**Odwołania**|- **BDDRun.exe**<br /><br /> - **ZTIPrereq.vbs**. Używany do określenia, czy komputer docelowy spełnia wymagania wstępne dotyczące wdrażania nowego systemu operacyjnego<br /><br /> - **LiteTouch.wsf**. Kontrolowanie procesu wdrożenia LTI skryptu|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript LiteTouch.vbs </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> - **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> - **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu)|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|Brak|||  

###  <a name="LiteTouch.wsf"></a>LiteTouch.wsf  
 Ten skrypt jest wywoływany przez [LiteTouch.vbs](#LiteTouch.vbs) i jest odpowiedzialny za kontrolowanie proces wdrożenia LTI. Obejmuje to następujące działania:  

-   Uruchamianie Kreatora wdrażania  

-   Uruchomienie procesu wdrożenia LTI przy użyciu pliku sekwencji zadań odpowiednie  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|-***task_sequence_file*.xml**. Zawiera zadania i sekwencji zadań w procesie wdrożenia LTI<br /><br /> - **Zmienne środowiskowe**. Zawiera listę wartości właściwości, niestandardowe właściwości połączenia bazy danych, reguły wdrażania i inne informacje wymagane przez skrypty w celu zakończenia procesu wdrażania; zmienne środowiskowe są wypełniane przy ZTIGather.wsf|  
|**Dane wyjściowe**|-                          **LiteTouch.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|-                          **BDD_Welcome_ENU.XML**. Zostanie wyświetlony Kreator wdrażania **powitalnej** strony wdrożenia LTI<br /><br /> -                          **DeployWiz_Definition_ENU.xml**. Wyświetla strony Kreatora wdrażania dla wdrożenia LTI<br /><br /> -                          **DiskPart.exe**. Narzędzia, która umożliwia automatyczne zarządzanie partycji, woluminów i dysków<br /><br /> -                          **LTICleanup.wsf**. Wykonuje zadania oczyszczania, po zakończeniu wdrożenia<br /><br /> -                          **LTICopyScripts.wsf**. Kopiuje skryptów wdrażania do lokalnego dysku twardego na komputerze docelowym<br /><br /> -                          **MSHTA.exe**. Host aplikacji HTML<br /><br /> -                          **RecEnv.exe**. Jeśli istnieje to narzędzie, użytkownik jest monitowany o Określanie, czy można uruchomić środowisko odzyskiwania systemu Windows.<br /><br /> -                          **Regsvr32.exe**. Rejestruje pliki (.dll, .exe, .ocx itd.) w systemie operacyjnym<br /><br /> -                          **Summary_Definition_ENU.XML**. Wyświetla podsumowanie wyników dla wdrożenia LTI<br /><br /> -                          **TsmBootStrap.exe**. Narzędzie uruchamiania sekwencji zadań<br /><br /> -                          **Wizard.hta**. Wyświetla strony Kreatora wdrażania<br /><br /> -                          **WPEUtil.exe**. Inicjuje środowisko Windows PE i połączeń sieciowych; Inicjuje LTI<br /><br /> -                          **ZTIGather.wsf**. Zbiera informacje o właściwości i reguł przetwarzania<br /><br /> -                          **ZTIPrereq.vbs**. Sprawdza, czy komputer docelowy spełnia wymagania dotyczące uruchamiania Kreatora wdrażania<br /><br /> -                          **ZTINICConfig.wsf**. Konfiguruje kart sieciowych uaktywnione<br /><br /> -                          **ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur używanych przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`BDDRun.exe "wscript.exe <ScriptDirectory>\LiteTouch.wsf </debug:value>"`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu)|  
|**/ Start**|Tworzy skrót w nowego systemu operacyjnego, który jest uruchamiany po uruchomieniu powłoki|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**_DoNotCleanLiteTouch**|-||  
|**_SMSTSPackageName**||-|  
|**AdminPassword**|-||  
|**Architektura**|-|-|  
|**BootPE**|-|-|  
|**ComputerBackupLocation**||-|  
|**Nazwa_komputera**|-||  
|**DeployDrive**|-|-|  
|**DeploymentMethod**|-|-|  
|**DeploymentType**|-|-|  
|**DeployRoot**|-|-|  
|**DestinationLogicalDrive**||-|  
|**Administrator domeny**||-|  
|**DomainAdminDomain**||-|  
|**DomainAdminPassword**||-|  
|**FinishAction**|-||  
|**Nazwa hosta**|-||  
|**IsServerCoreOS**|-||  
|**Przyłączania**|-||  
|**JoinWorkgroup**|-|-|  
|**KeyboardLocalePE**|-||  
|**LTISuspend**|-||  
|**OSDAdapterCount**|-||  
|**OSDComputerName**|-|-|  
|**Faza**|-|-|  
|**ResourceDrive**|-|-|  
|**ResourceRoot**|-|-|  
|**RetVal**||-|  
|**SkipBDDWelcome**|-||  
|**SkipFinalSummary**|-|-|  
|**SkipWizard**|-||  
|**Zmiennej SMSTSLocalDataDrive**||-|  
|**TaskSequenceID**|-||  
|**TimeZoneName**||-|  
|**UserDataLocation**|-|-|  
|**UserDomain**|-||  
|**Nazwa użytkownika**|-||  
|**Hasła użytkownika**|-||  
|**WelcomeWizardCommand**|-||  
|**WizardComplete**|-||  

###  <a name="LTIApply.wsf"></a>LTIApply.wsf  
 Ten skrypt jest odpowiedzialny za instalowanie obraz środowiska Windows PE do komputera docelowego. Obraz środowiska Windows PE służy do zbierania informacji o komputerze docelowym i uruchamianie zadania wdrażania na komputerze docelowym.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, które skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **LTIApply.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **LTIApply_wdsmcast.log**. Plik dziennika zawierający zdarzenia generowane przez narzędzie Wdsmcast<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|-                          **CMD.exe**. Umożliwia uruchamianie narzędzia wiersza polecenia<br /><br /> -                          **Bootsect.exe**. Stosuje sektora rozruchowego na dysku twardym<br /><br /> -                          **ImageX.exe**. Narzędzie używane do tworzenia i zarządzania nimi pliki WIM<br /><br /> -                          **ZTIBCDUtility.vbs**. Zawiera funkcje narzędzie używane podczas wykonywania zadania Menedżera rozruchu<br /><br /> -                          **ZTIConfigFile.vbs**. Zawiera procedury dla przetwarzania plików XML<br /><br /> -                          **ZTIDiskUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur używanych przez skrypt<br /><br /> -                          **ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur używanych przez skrypt<br /><br /> -                          **Wdsmcast.exe**. Narzędzie, które komputery docelowe użyć w celu dołączenia transmisję w trybie multiemisji|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript LTIApply.wsf </pe> </post> </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/PE**|Używa procesu instalowania obraz środowiska Windows PE na komputerze docelowym|  
|**/POST**|Czyści niepotrzebnych plików po zainstalowaniu obrazu|  
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach .log; w przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu)|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**Architektura**|-||  
|**BootPE**||-|  
|**DeployRoot**|-||  
|**DestinationLogicalDrive**|-|-|  
|**OSGUID**|-||  
|**OSCurrentVersion**|-||  
|**OSVersion**|-||  
|**ImageBuild**|-||  
|**ImageFlags**|-||  
|**ImageProcessor**|-||  
|**ISBDE**|-||  
|**Ścieżka_źródłowa**||-|  
|**TaskSequenceID**|-||  
|**UserDomain**|-||  
|**Nazwa użytkownika**|-||  
|**Hasła użytkownika**|-||  
|**WDSServer**|-||  

###  <a name="LTICleanup.wsf"></a>LTICleanup.wsf  
 Ten skrypt powoduje usunięcie plików lub ustawienia konfiguracji (takich jak skrypty, folderów, wpisy rejestru lub ustawienia konfiguracji automatycznego logowania) z komputera docelowego po zakończeniu procesu wdrażania.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera listę wartości właściwości, niestandardowe właściwości połączenia bazy danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania. Zmienne środowiskowe są wypełniane przy ZTIGather.wsf.|  
|**Dane wyjściowe**|-                          **LTICleanup.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|-                          **Bootsect.exe**. Stosuje sektora rozruchowego na dysku twardym<br /><br /> -                          **NET.exe**. Wykonuje zadania zarządzania w sieci<br /><br /> -                          **RegSvr32.exe**. Rejestruje pliki (.dll, .exe, .ocx itd.) w systemie operacyjnym<br /><br /> -                          **ZTIBCDUtility.vbs**. Zawiera funkcje narzędzie używane podczas wykonywania zadania Menedżera rozruchu<br /><br /> -                          **ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur używanych przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript LTICleanup.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu)|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**_DoNotCleanLiteTouch**|-||  
|**DeployRoot**|-||  
|**DestinationLogicalDrive**|-||  
|**OSVersion**|-||  

###  <a name="LTICopyScripts.wsf"></a>LTICopyScripts.wsf  
 Ten skrypt kopiuje skrypty wdrażania do procesów wdrażania LTI i ZTI lokalny dysk twardy na komputerze docelowym.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|-                          **Summary_Definition_ENU.XML**. Wyświetla podsumowanie wyników dla wdrożenia LTI<br /><br /> -                          **Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **LTICopyScripts.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|**ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur używanych przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript LTICopyScripts.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu)|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|Brak|||  

###  <a name="LTIGetFolder.wsf"></a>LTIGetFolder.wsf  
 Ten skrypt wyświetla okno dialogowe, które umożliwia użytkownikowi przeglądań do folderu. Ścieżka wybrany folder jest przechowywana w zmiennej środowiskowej FOLDERPATH.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera listę wartości właściwości, niestandardowe właściwości połączenia bazy danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania. Zmienne środowiskowe są wypełniane przy ZTIGather.wsf.|  
|**Dane wyjściowe**|Brak|  
|**Odwołania**|-                          **ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt<br /><br /> -                          **WizUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, które używa interfejsu użytkownika (np. strony kreatora)|  
|**Lokalizacja**|-                          *dystrybucji*\Scripts<br /><br /> -                          *Program_Files*\Microsoft Deployment Toolkit\Scripts|  
|**Użycie**|`cscript LTIGetFolder.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/Debug:Value**|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu)|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**DefaultFolderPath**|-||  
|**FolderPath**||-|  

###  <a name="LTIOEM.wsf"></a>LTIOEM.wsf  
 Ten skrypt jest używany przez producenta OEM w scenariuszu LTI przez producenta OEM Aby skopiować zawartość udziału wdrożenia nośnika na dysk twardy na komputerze docelowym, aby przygotować go do duplikacji.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera listę wartości właściwości, niestandardowe właściwości połączenia bazy danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania. Zmienne środowiskowe są wypełniane przy ZTIGather.wsf.|  
|**Dane wyjściowe**|-                          **LTIOEM.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|-                          **RoboCopy.exe**. Narzędzia do kopiowania plików i folderów<br /><br /> -                          **ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript LTIOEM.wsf </BITLOCKER &#124; /BDE> </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu)|  
|**/ FUNKCJA BITLOCKER**|Włącza funkcję BitLocker|  
|**/ BDE**|Włącza funkcję BitLocker|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**_DoNotCleanLiteTouch**||-|  
|**DeployDrive**|-||  
|**DeployRoot**|-||  
|**TSGUID**|-||  

###  <a name="LTISuspend.wsf"></a>LTISuspend.wsf  
 Ten skrypt wstrzymuje sekwencji zadań umożliwia ręczne zadania do wykonania. Po uruchomieniu ten skrypt tworzy **wznowienie sekwencji zadań** skrót na pulpicie użytkownika, który umożliwia użytkownika o ponowne uruchomienie sekwencji zadań wykonywanych ręcznie po zakończeniu.  

> [!NOTE]
>  Ten skrypt jest obsługiwana tylko w pełnej wersji systemu operacyjnego.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera listę wartości właściwości, niestandardowe właściwości połączenia bazy danych, reguły wdrażania i inne informacje, które skrypty wymagane do ukończeniu procesu wdrażania. Zmienne środowiskowe są wypełniane przy ZTIGather.wsf.|  
|**Dane wyjściowe**|-                          **LTISuspend.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|-                          **LiteTouch.wsf**. Kontroluje proces wdrożenia LTI<br /><br /> -                          **LTICopyScripts.wsf**. Kopiuje skryptów wdrażania do lokalnego dysku twardego na komputerze docelowym<br /><br /> -                          **ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript LTISuspend.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu)|  
|**/ Wznowień**|—|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**LTISuspend**||-|  
|**Zmienna SMSTSRebootRequested**||-|  

###  <a name="LTISysprep.wsf"></a>LTISysprep.wsf  
 Ten skrypt program Sysprep przygotowuje komputer docelowy uruchamia narzędzie Sysprep na komputerze docelowym i sprawdza, czy program Sysprep został uruchomiony pomyślnie.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera listę wartości właściwości, niestandardowe właściwości połączenia bazy danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania. Zmienne środowiskowe są wypełniane przy ZTIGather.wsf.|  
|**Dane wyjściowe**|-                          **LTISysprep.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|-                          **Expand.exe**. Rozwija skompresowane pliki<br /><br /> -                          **Sysprep.exe**. Przygotowanie komputerów do duplikacji<br /><br /> -                          **ZTIConfigFile.vbs**. Zawiera procedury dla przetwarzania plików XML<br /><br /> -                          **ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript LTISysprep.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu).|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**Architektura**|-||  
|**DeployRoot**|-||  
|**DestinationLogicalDrive**|-||  
|**DoCapture**|-||  
|**OSCurrentBuild**|-||  
|**OSDAnswerFilePath**|-||  
|**OSGUID**|-||  
|**Ścieżka_źródłowa**|-|-|  
|**TaskSequenceID**|-||  

###  <a name="NICSettings_Definition_ENU.xml"></a>NICSettings_Definition_ENU.xml  
 Ten plik XML zawiera kod skryptu i układ HTML **skonfiguruj statyczne ustawienia sieci IP** strona kreatora w Kreatorze wdrażania. Podczas wdrożenia LTI Wizard.hta odczytuje ten plik i uruchamia strony kreatora osadzonych, które monituje wymagane adresowania konfiguracji sieci. Jeśli nie statyczne ustawienia adresów IP nie jest dostarczony, domyślnie za pomocą protokołu DHCP można uzyskać konfiguracji sieci wymagane skrypty wdrażania.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|Brak|  
|**Dane wyjściowe**|Brak|  
|**Odwołania**|**ZTINICUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|Brak|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|Brak|Brak|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**OSDAdapterxDNSServerList**||-|  
|**OSDAdapterxDNSSuffix**||-|  
|**OSDAdapterxGateways**||-|  
|**OSDAdapterxIPAddressList**||-|  
|**OSDAdapterxMacAddress**||-|  
|**OSDAdapterxSubnetMask**||-|  
|**OSDAdapterxWINSServerList**||-|  
|**OSDAdapterCount**||-|  

> [!NOTE]
>  *x*w nazwach właściwości wymienionych powyżej jest symbolem zastępczym dla tablicy liczony od zera, który zawiera informacje dotyczące karty sieciowej.  

###  <a name="Summary_Definition_ENU.xml"></a>Summary_Definition_ENU.XML  
 Ten plik XML zawiera kod skryptu i układ HTML **podsumowanie wdrożenia** strona kreatora w Kreatorze wdrażania. Podczas wdrożenia LTI Wizard.hta odczytuje ten plik i uruchamia strony kreatora osadzone, który wyświetla podsumowanie wyników dla wdrożenia LTI. Ten plik XML zawiera na następujących stronach kreatora:  

-   **Powodzenie**. Powiadomienie o pomyślnym zakończeniu zadania wdrażania  

-   **Błąd**. Powiadomienia dotyczące awarii do pomyślnego ukończenia zadania wdrażania  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|Brak|  
|**Dane wyjściowe**|Brak|  
|**Odwołania**|**Summary_Scripts.vbs**. Obejmuje funkcje pomocy technicznej i procedur, które strony kreatora osadzone w tym pliku XML|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|Brak|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|Brak|Brak|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**SkipFinalSummary**|-||  
|**RetVal**|-||  

###  <a name="Summary_scripts.vbs"></a>Summary_scripts.vbs  
 Ten skrypt jest wywoływany przez **Podsumowanie** strona kreatora Kreatora wdrażania. Zawiera on funkcje i podprocedury używany do inicjowania i sprawdzania poprawności.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|Komunikat zdarzenia są zapisywane w tych plikach dziennika:<br /><br /> -                          **Summary_scripts.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|Brak|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`<script language="VBScript" src="Summary_Scripts.vbs"/>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|Brak|Brak|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**DeploymentType**|-||  
|**RetVal**|-||  

###  <a name="Wizard.hta"></a>Wizard.hta  
 Ta aplikacja Hypertext Wyświetla strony Kreatora wdrażania.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera listę wartości właściwości, niestandardowe właściwości połączenia bazy danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania. Zmienne środowiskowe są wypełniane przy ZTIGather.wsf.|  
|**Dane wyjściowe**|-                          **Wizard.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|-                          **LTIGetFolder.wsf**. Plik skryptu, który inicjuje **BrowseForFolder** — okno dialogowe<br /><br /> -                          **ZTIConfigFile.vbs**. Zawiera procedury dla przetwarzania plików XML<br /><br /> -                          **ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt<br /><br /> -                          **WizUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|-                          *dystrybucji*\Scripts<br /><br /> -                          *Program_Files*\Microsoft Deployment Toolkit\Scripts|  
|**Użycie**|`mshta.exe Wizard.hta </definition:filename> </NotWizard> </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu).|  
|**/ NotWizard**|Umożliwia pominięcie monitów strony kreatora|  
|**/ Definicja: * Nazwa pliku***|Określa plik XML, który ma być ładowana do Kreatora|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**Definicja**|-||  
|**DefaultFolderPath**||-|  
|**FolderPath**|-||  
|**WizardComplete**||-|  

###  <a name="WizUtility.vbs"></a>WizUtility.vbs  
 Ten skrypt zawiera funkcje i procedur, które odwołują się do różnych skryptów Kreatora wdrażania.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **WizUtility.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|**LTIGetFolder.wsf**. Plik skryptu, który inicjuje **BrowseForFolder**— okno dialogowe|  
|**Lokalizacja**|-                          *dystrybucji*\Scripts<br /><br /> -                          *Program_Files*\Microsoft Deployment Toolkit\Scripts|  
|**Użycie**|`<script language="VBScript" src="WizUtility.vbs"/>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|Brak|Brak|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**DefaultFolderPath**||-|  
|**DefaultDestinationDisk**|-||  
|**DefaultDestinationIsDirty**|-||  
|**DefaultDestinationPartition**|-||  
|**DeploymentType**|-||  
|**DestinationDisk**|-||  
|**FolderPath**|-||  
|**OSVersion**|-||  
|**UserDomain**|-||  
|**UserCredentials**||-|  

###  <a name="ZTIApplications.wsf"></a>ZTIApplications.wsf  
 Ten skrypt inicjuje instalację aplikacji, które zostały skonfigurowane w węźle aplikacji w konsoli Deployment Workbench. Ten skrypt nie będzie próbować instalować dowolnej aplikacji, które:  

-   Nie obsługuje typu platformy na komputerze docelowym  

-   Nie obsługuje typu procesora komputera docelowego  

-   Posiada wpis Odinstaluj w kluczu rejestru **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion\Uninstall**  

> [!NOTE]
>  Jeśli listy aplikacji ma wszelkim aplikacjom zależnym zdefiniowane, ten skrypt próbuje zainstalować przed zainstalowaniem aplikacji wymienionych te aplikacje zależne.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTIApplications.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|-                          **ZTIConfigFile.vbs**. Zawiera procedury dla przetwarzania plików XML<br /><br /> -                          **ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt<br /><br /> -                          **BDDRun.exe**. Uruchamia polecenie wymaga interakcji użytkownika|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTIApplications.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu)|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**ApplicationGUID**|-||  
|**ApplicationSuccessCodes**|-||  
|**DependentApplications**|-||  
|**DeploymentMethod**|-||  
|**InstalledApplications**|-|-|  
|**ResourceDrive**|-||  
|**ResourceRoot**|-|-|  
|**Zmienna SMSTSRebootRequested**||-|  
|**SMSTSRetryRequested**||-|  

###  <a name="ZTIAppXmlGen.wsf"></a>ZTIAppXmlGen.wsf  
 Ten skrypt generuje Użyj file—ZTIAppXmlGen.xml—to XML, gdy automatycznie przechwytywanie danych użytkownika (dokumenty) skojarzone z zainstalowanych aplikacji. Tak więc za pomocą **HKEY_CLASSES_ROOT\Software\Classes** klucza rejestru i przechwytuje wszystkie aplikacje który:  

-   Nie są skojarzone z jednego z następujących rozszerzeń pliku: MP3, MOV, .wma, WMV, .chm, .evt, evtx, .exe, .com lub .fon  

-   Nie są skojarzone z programem Microsoft Office, takich jak 2007 Office system lub Microsoft Office 2003.  

-   Ma prawidłową obsługi Otwórz wymienione na **HKEY_CLASSES_ROOT\application\shell\open\command**  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTIAppXmlGen.xml**. Zawiera listę aplikacji zainstalowanych na komputerze docelowym<br /><br /> -                          **ZTIAppXmlGen.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|**ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTIAppXmlGen.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu).|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**DeploymentMethod**|-||  
|**DeploymentType**|-||  
|**ImageBuild**|-||  
|**OSCurrentVersion**|-||  
|**USMTMigFiles**|-|-|  

###  <a name="ZTIAuthorizeDHCP.wsf"></a>ZTIAuthorizeDHCP.wsf  
 Ten skrypt używa narzędzia Netsh, aby skonfigurować komputer docelowy, tak aby jest autoryzowany serwer DHCP w usługach AD DS.  

 Aby uzyskać więcej informacji na temat autoryzowania serwerów DHCP, zobacz [jak Netsh.exe używany do autoryzacji, Unauthorize i wyświetlić listę serwerów DHCP w usłudze Active Directory](http://support.microsoft.com/kb/303351).  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTIAuthorizeDHCP.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|-                          **Netsh.exe**. Narzędzie używane do automatyzowania konfiguracji składników sieciowych<br /><br /> -                          **ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTIAuthorizeDHCP.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu).|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**Adres IP**|-||  

###  <a name="ZTIBackup.wsf"></a>ZTIBackup.wsf  
 Ten skrypt wykonuje kopię zapasową komputera docelowego za pomocą narzędzia ImageX. Kopia zapasowa jest przechowywana w lokalizacji określonej w [BackupDir](#BackupDir) i [BackupShare](#BackupShare) właściwości.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTIBackup.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **ZTIBackup_imagex.log**. Plik dziennika zawierający zdarzenia, które generuje ImageX<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|-                          **ImageX.exe**. Narzędzie używane do tworzenia i zarządzania nimi pliki WIM<br /><br /> -                          **ZTIBCDUtility.vbs**. Zawiera funkcje narzędzie używane podczas wykonywania zadania Menedżera rozruchu<br /><br /> -                          **ZTIDiskUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt<br /><br /> -                          **ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTIBackup.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu)|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**BackupDir**|-||  
|**BackupDisk**|-||  
|**BackupDrive**|-||  
|**Plik**|-||  
|**BackupPartition**|-||  
|**BackupScriptComplete**||-|  
|**BackupShare**|-||  
|**ComputerBackupLocation**|-||  
|**DeploymentMethod**|-||  
|**DeploymentType**|-||  
|**DestinationLogicalDrive**|-|-|  
|**DoCapture**|-||  
|**ImageBuild**|-||  
|**ImageFlags**|-||  
|**OSDStateStorePath**|-||  
|**Faza**|-||  
|**TaskSequenceID**|-||  
|**USMTLocal**|-||  

###  <a name="ZTIBCDUtility.vbs"></a>ZTIBCDUtility.vbs  
 Ten skrypt zawiera funkcje narzędzia, które niektóre skrypty MDT używane podczas wykonywania zadania Menedżera rozruchu.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|Brak|  
|**Odwołania**|**BCDEdit.exe**. Narzędzia do edycji konfiguracji rozruchu systemu Windows|  
|**Lokalizacja**|-                          *dystrybucji*\Scripts<br /><br /> -                          *Program_Files*\Microsoft Deployment Toolkit\Scripts|  
|**Użycie**|`<script language="VBScript" src="ZTIBCDUtility.vbs"/>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|Brak|Brak|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|Brak|||  

###  <a name="ZTIBde.wsf"></a>ZTIBde.wsf  
 Ten skrypt instaluje i konfiguruje funkcji BitLocker na komputerze docelowym. Konfiguracja funkcji BitLocker jest ograniczona do nowego komputera scenariusze, które zostały skonfigurowane z jednej partycji dysków twardych.  

> [!NOTE]
>  W przypadku wdrożeń ZTI i UDI **UILanguage** właściwość musi być ustawiona w CustomSettings.ini lub w bazie danych zestawu MDT, ponieważ ZTIBde.wsf próbuje odczytać ustawień regionalnych z **UILanguage** właściwości.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTIBde.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **ZTIBdeFix_diskpart.log**. Plik dziennika zawierający zdarzenia, które generuje narzędzia Diskpart<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|-                          **CMD.exe**. Umożliwia uruchamianie narzędzia wiersza polecenia<br /><br /> -                          **Defrag.exe**. Defragmentacji dysku twardego<br /><br /> -                          **DiskPart.exe**. Narzędzia, która umożliwia automatyczne zarządzanie partycji, woluminów i dysków<br /><br /> -                          **ServerManagerCmd.exe**<br /><br /> -                          **ZTIDiskUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt<br /><br /> -                          **ZTIOSRole.wsf**. Instaluje ról serwera<br /><br /> -                          **ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTIBde.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu)|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**AdminPassword**|-||  
|**BDEDriveLetter**|-|-|  
|**BDEDriveSize**|-||  
|**BDEInstall**|-||  
|**BDEInstallSuppress**|-||  
|BDEKeyLocation|-||  
|**BDEPin**|-||  
|**BDERecoveryKey**|-||  
|**BDESecondPass**|-|-|  
|**BdeWaitForEncryption**|-||  
|**BitlockerInstalled**|-|-|  
|**DeploymentMethod**|-||  
|**ISBDE**|-||  
|**OSDBitLockerCreateRecoveryPassword**|-||  
|**OSDBitLockerMode**|-||  
|**OSDBitLockerStartupKey**|-||  
|**OSDBitLockerStartupKeyDrive**|-||  
|**OSDBitLockerTargetDrive**|-||  
|**OSDBitLockerWaitForEncryption**|-||  
|**OSCurrentBuild**|-||  
|**OSCurrentVersion**|-||  
|**OSFeatures**|-|-|  
|**OSRoles**|-|-|  
|**OSRoleServices**|-|-|  
|**OSVersion**|-||  
|**Zmienna SMSTSRebootRequested**|-|-|  
|**SMSTSRetryRequested**||-|  
|**TPMOwnerPassword**|-||  

###  <a name="ZTIBIOSCheck.wsf"></a>ZTIBIOSCheck.wsf  
 Ten skrypt sprawdza systemu BIOS na komputerze docelowym, a następnie sprawdza listę BIOS, które są niezgodne z systemem Windows. Lista niezgodne BIOS jest przechowywana w [ZTIBIOSCheck.xml](#ZTIBIOSCheck.xml) pliku.  

 Jeśli system BIOS na komputerze docelowym znajduje się w [ZTIBIOSCheck.xml](#ZTIBIOSCheck.xml) pliku, a następnie skrypt zwraca stan, który wskazuje systemu BIOS jest niezgodna z systemem Windows i proces wdrażania powinno zostać zakończone. Uzyskać informacji o wypełniania listy niezgodnych BIOS, zobacz [ZTIBIOSCheck.xml](#ZTIBIOSCheck.xml).  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|-                          **ZTIBIOSCheck.xml**. Zawiera listę BIOS, które są znane z niezgodności z systemem Windows<br /><br /> -                          **Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTIBIOSCheck.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|**ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTIBIOSCheck.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu)|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|Brak|||  

###  <a name="ZTICoalesce.wsf"></a>ZTICoalesce.wsf  
 Program Configuration Manager wymaga pakietów do numerowane kolejno począwszy **PACKAGES001**, z nie przerwy w sekwencji. W przeciwnym razie instalacja zakończy się niepowodzeniem.  

 Ten skrypt umożliwia definiowanie i nazwy zmiennych przy użyciu informacje identyfikujące program do uruchomienia — na przykład **ComputerPackages100**, **ComputerPackages110**, lub  **CollectionPackages150**. Następnie, po uruchomieniu tego skryptu programu Configuration Manager odnajduje wszystkie zmienne, które są zgodne ze wzorcem (na przykład wszystkie nazwy zmiennych, które zawierają ciąg znaków **pakiety**) i tworzy listę sekwencyjnych, bez przerw przy użyciu nazwy podstawowej  **PAKIETY**.  

 Na przykład, jeśli zdefiniowano następujące zmienne (przy użyciu zmienne dla komputera, zmienne kolekcji lub w CustomSettings.ini lub zestaw MDT bazy danych, na przykład):  

-   **ComputerPackages100 = XXX00001:Program**  

-   **ComputerPackages110 = XXX00002:Program**  

-   **CollectionPackages150 = XXX00003:Program**  

-   **Packages001 = XXX00004:Program**  

 Po uruchomieniu skryptu, będzie listy:  

-   **PACKAGES001 = XXX00004:Program**  

-   **PACKAGES002 = XXX00001:Program**  

-   **PACKAGES003 = XXX00002:Program**  

-   **PACKAGES004 = XXX00003:Program**  

 Następnie będzie można uruchamiać wszystkie cztery programy programu Configuration Manager.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTICoalesce.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|**ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTICoalesce.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu).|  
|**/ CoalesceDigits: * wartość***|Określa liczbę cyfr, które muszą być podawane podczas tworzenia numerowania sekwencji. Na przykład, wartość:<br /><br /> -                              **2** utworzyć PACKAGE03<br /><br /> -                              **3**utworzyć PACKAGE003<br /><br /> Jeśli ten argument nie zostanie podana wartość domyślna to **3**.|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**CoalescePattern**|-||  
|**CoalesceTarget**|-||  

###  <a name="ZTIConfigFile.vbs"></a>ZTIConfigFile.vbs  
 Ten skrypt zawiera procedury typowe dla przetwarzania plików XML zestawu MDT.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTIConfigFile.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|NET.exe|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`<script language="VBScript" src="ZTIConfigFile.vbs"/>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|Brak|Brak|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**IsSafeForWizardHTML**|-||  
|**MandatoryApplications**|-||  
|**SkipGroupSubFolders**|-||  

###  <a name="ZTIConfigure.wsf"></a>ZTIConfigure.wsf  
 Ten skrypt konfiguruje plik Unattend.xml z wartościami właściwości określone wcześniej w procesie wdrożenia zestawu MDT. Skrypt konfiguruje odpowiedniego pliku oparte na wdrażanego systemu operacyjnego.  

 Ten skrypt odczytuje plik ZTIConfigure.xml, aby określić, jak zaktualizować plik Unattend.xml z odpowiednimi wartościami określona we właściwościach wdrożenia. Plik ZTIConfigure.xml zawiera informacje tłumaczenie właściwości do ustawienia w pliku Unattend.xml.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|-                          **ZTIConfigure.xml**. Zawiera listę wartości właściwości (określone wcześniej w procesie wdrażania) i ich odpowiednich ustawień konfiguracji<br /><br /> -                          **Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTIConfigure.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|**ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTIConfigure.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu).|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**Nazwa_komputera**|-|-|  
|**DeploymentType**|-||  
|**DeploymentMethod**|-||  
|**DeployRoot**|-||  
|**DestinationLogicalDrive**|-||  
|DomainAdminDomain|-||  
|**ImageBuild**|-||  
|**OSDAnswerFilePath**|-||  
|**OSDAnswerFilePathSysprep**|-||  
|**OSDComputerName**|-||  
|**Faza**|-||  
|**TaskSequenceID**|-||  

###  <a name="ZTIConfigureADDS.wsf"></a>ZTIConfigureADDS.wsf  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTIConfigureADDS.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|-                          **Dcpromo.exe**. Instaluje i usuwania usług AD DS<br /><br /> -                          **NET.exe**. Wykonuje zadania zarządzania w sieci<br /><br /> -                          **ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTIConfigureADDS.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu).|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**ADDSLogPath**|-||  
|**ADDSPassword**|-||  
|**ADDSUserDomain**|-||  
|**ADDSUserName**|-||  
|**AutoConfigDNS**|-||  
|**Nazwa ChildName**|-||  
|**ConfirmGC**|-||  
|**DatabasePath**|-||  
|**DomainLevel**|-||  
|**DomainNetBiosName**|-||  
|**ForestLevel**|-||  
|**NewDomain**|-||  
|**NewDomainDNSName**|-||  
|**OSVersion**|-||  
|**ParentDomainDNSName**|-||  
|**ReplicaOrNewDomain**|-|-|  
|**ReplicaDomainDNSName**|-||  
|**ReplicationSourceDC**|-||  
|**SafeModeAdminPassword**|-||  
|**Nazwa witryny**|-||  
|**SysVolPath**|-||  

###  <a name="ZTIConfigureDHCP.wsf"></a>ZTIConfigureDHCP.wsf  
 Ten skrypt konfiguruje DHCP na komputerze docelowym.  

> [!NOTE]
>  DHCP powinien być zainstalowany na komputerze docelowym przed wykonaniem tego skryptu.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTIConfigureDHCP.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|-                          **Netsh.exe**. Narzędzie, które pozwala na automatyzację konfiguracji składników sieciowych<br /><br /> -                          **ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTIConfigureDHCP.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu).|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**DHCPScopesxDescription**|-||  
|**DHCPScopesxEndIP**|-||  
|**DHCPScopesxExcludeStartIP**|-||  
|**DHCPScopesxExcludeEndIP**|-||  
|**DHCPScopesxIP**|-||  
|**DHCPScopesxName**|-||  
|**DHCPScopesxOptionRouter**|-||  
|**DHCPScopesxOptionDNSDomainName**|-||  
|**DHCPScopesxOptionDNSServer**|-||  
|**DHCPScopesxOptionLease**|-||  
|**DHCPScopesxOptionNBTNodeType**|-||  
|**DHCPScopesxOptionPXEClient**|-||  
|**DHCPScopesxOptionWINSServer**|-||  
|**DHCPScopesxStartIP**|-||  
|**DHCPScopesxSubnetmask**|-||  
|**DHCPServerOptionDNSDomainName**|-||  
|DHCPServerOptionDNSServer|-||  
|**DHCPServerOptionNBTNodeType**|-||  
|**DHCPServerOptionPXEClient**|-||  
|**DHCPServerOptionRouter**|-||  
|**DHCPServerOptionWINSServer**|-||  

> [!NOTE]
>  *x*we właściwościach wymienione w tym miejscu jest symbolem zastępczym tablicę wartości nieujemnych zawierającą informacje o konfiguracji DHCP.  

###  <a name="ZTIConfigureDNS.wsf"></a>ZTIConfigureDNS.wsf  
 Ten skrypt konfiguruje DNS na komputerze docelowym. Aby wykonywać zadania rzeczywista konfiguracja, skrypt używa narzędzia Dnscmd.  

 Aby uzyskać więcej informacji na temat Dnscmd.exe, zobacz [omówienie Dnscmd](http://technet.microsoft.com/library/cc778513%28WS.10%29.aspx).  

> [!NOTE]
>  DNS powinien być zainstalowany na komputerze docelowym przed wykonaniem tego skryptu.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTIConfigureDNS.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|-                          **Dnscmd.exe**. Ułatwia administratorom zarządzanie systemem DNS<br /><br /> -                          **ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTIConfigureDNS.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu).|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**DNSServerOptionDisableRecursion**|-||  
|**DNSServerOptionBINDSecondaries**|-||  
|**DNSServerOptionFailOnLoad**|-||  
|**DNSServerOptionEnableRoundRobin**|-||  
|**DNSServerOptionEnableNetmaskOrdering**|-||  
|**DNSServerOptionEnableSecureCache**|-||  
|**DNSServerOptionNameCheckFlag**|-||  
|**DNSZonesxName**|-||  
|**DNSZonesxType**|-||  
|**DNSZonesxMasterIP**|-||  
|**DNSZonesxDirectoryPartition**|-||  
|**DNSZonesxFileName**|-||  
|**DNSZonesxScavenge**|-||  
|**DNSZonesxUpdate**|-||  

> [!NOTE]
>  *x*we właściwościach wymienione w tym miejscu jest symbolem zastępczym tablicę wartości nieujemnych zawierającą informacje o konfiguracji DNS.  

###  <a name="ZTIConnect.wsf"></a>ZTIConnect.wsf  
 Proces wdrożenia zestawu MDT używa tego skryptu do uwierzytelniania za pomocą komputera serwera (takich jak komputer z programem SQL Server lub innego serwera, który został udostępniony folder sieciowy). Po uruchomieniu tego skryptu, sprawdza czy można utworzyć połączenie do udostępnionego folderu sieciowego określone w **/uncpath** argumentu.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTIConnect.log**.  Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|**ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTIConnect.wsf /UNCPath:<uncpath> </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/UNCPath:uncpath**|Określa w pełni kwalifikowaną ścieżkę UNC do udostępnionego folderu sieciowego|  
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach .log; w przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu).|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|Brak|||  

###  <a name="ZTICopyLogs.wsf"></a>ZTICopyLogs.wsf  
 Skopiuj pliki Smsts.log i BDD.log są kopiowane do podfolderu poniżej udział który **SLShare** określa właściwości. Podfolder pobiera nazwę **OSDComputerName**, **_SMSTSMachineName**, lub **HostName** określa.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTICopyLogs.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|**ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTICopyLogs.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: *wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu).|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|Brak|||  

###  <a name="ZTIDataAccess.vbs"></a>ZTIDataAccess.vbs  
 Ten skrypt zawiera procedury wspólnej dla dostępu do bazy danych.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTIDataAccess.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|Brak|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`<script language="VBScript" src="ZTIDataAccess.vbs"/>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|Brak|Brak|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**_SMSTSReserved1**|-||  
|**_SMSTSReserved2**|-||  
|**RulesFile**|-||  
|**UserDomain**|-|-|  
|**Nazwa użytkownika**|-|-|  
|**Hasła użytkownika**|-|-|  

###  <a name="ZTIDisableBDEProtectors.wsf"></a>ZTIDisableBDEProtectors.wsf  
 Jeśli funkcja BitLocker jest włączona, ten skrypt wstrzymuje ochrony funkcji BitLocker, skonfigurowanym w systemie.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTIDisableBDEProtectors.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|**ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTIDisableBDEProtectors.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu).|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**ImageBuild**|-||  
|**ISBDE**||-|  
|**OSCurrentBuild**|-||  
|**OSCurrentVersion**|-||  
|**OSVersion**|-||  

###  <a name="ZTIDiskpart.wsf"></a>ZTIDiskpart.wsf  
 Ten skrypt tworzy partycji dysków na komputerze docelowym, wywołując narzędzia Diskpart. Określono parametry używane do konfigurowania dysku przez program Sequencer zadań lub w CustomSettings.ini. ZTIDiskpart.wsf przede wszystkim jest uruchamiany w scenariuszach nowego komputera. Proces przebiega następująco:  

1.  Proces wdrożenia zestawu MDT uruchamia skrypt ZTIDiskpart.wsf na podstawie kroki i kolejności etapów sekwencjonowania zadań.  

2.  ZTIDiskpart.wsf uruchamiania narzędzia Diskpart i wysyła je z poleceń wymaganej konfiguracji.  

3.  ZTIDiskpart.wsf działa Diskpart.exe i zapewnia pliku txt, jako parametr wiersza polecenia.  

4.  Dysk jest początkowo czyszczone, wysyłając Diskpart **wyczyść** polecenia.  

5.  Jeśli jest to pierwszy dysk i konfiguracja dysku nie został określony przez program Sequencer zadań lub w CustomSettings.ini, jednej partycji zostanie utworzony do przechowywania systemu operacyjnego. Jednak konfiguracji dysku został określony, będzie można skonfigurować zgodnie z określoną konfiguracją dysku.  

6.  Jeśli funkcja BitLocker ma zostać włączona, przeznaczona jest na końcu pierwszego dysku.  

7.  Wszystkie polecenia format są umieszczane w kolejce dopiero po zakończeniu działania polecenia Diskpart. Jeśli nie zostało określone przez program Sequencer zadań lub w CustomSettings.ini, ZTIDiskpart.wsf wykonuje szybkie formatowanie dysku C za pomocą następującego polecenia: `FORMAT C: /FS:NTFS /V:OSDisk /Q /Y`.  

8.  ZTIDiskpart.wsf kopiuje pliki ZTIDiskpart_diskpart.log i BDD.log z dysku RAM wstecz na dysku twardym.  

 Dostosować konfigurację dysku w komputerze docelowym, podając wymagane informacje w sekwencjonowania zadań lub CustomSettings.ini.  

 Aby uzyskać więcej informacji dotyczących konfigurowania dysków, zobacz dokument MDT *przy użyciu programu Microsoft Deployment Toolkit*.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTIDiskpart.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|-                          **DiskPart.exe**. Narzędzia, która umożliwia automatyczne zarządzanie partycji, woluminów i dysków<br /><br /> -                          **Format.com**. Sformatuje dysk twardy<br /><br /> -                          **ZTIDiskUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt<br /><br /> -                          **ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTIDiskpart.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu).|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**BDEDriveLetter**|-||  
|**BDEDriveSize**|-||  
|**BDEInstall**|-||  
|**DeployDrive**|-||  
|**DeploymentType**|-||  
|**DestinationDisk**|-||  
|**DestinationLogicalDrive**||-|  
|**DoNotCreateExtraPartition**|-||  
|**ImageBuild**|-||  
|**OSDDiskIndex**|-||  
|**OSDDiskpartBiosCompatibilityMode**|-|-|  
|**OSDDiskType**|-||  
|**OSDPartitions**|-||  
|**OSDPartitionStyle**|-||  
|**Zmiennej SMSTSLocalDataDrive**||-|  
|**VolumeLetterVariable**|-||  

###  <a name="ZTIDiskUtility.vbs"></a>ZTIDiskUtility.vbs  
 Ten skrypt zawiera funkcji związanych z dysku i że różnych skryptów w ramach wdrożenia zestawu MDT przetwarzania wywołania procedur.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|Brak|  
|**Dane wyjściowe**|-                          **ZTIDiskUtility.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|-                          **BcdBoot.exe**. Konfiguruje na partycji systemowej<br /><br /> -                          **DiskPart.exe**. Narzędzia, która umożliwia automatyczne zarządzanie partycji, woluminów i dysków|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`<script language="VBScript" src="ZTIDiskUtility.vbs"/>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|Brak|Brak|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**DestinationLogicalDrive**|-||  
|**UILanguage**|-|-|  

###  <a name="ZTIDomainJoin.wsf"></a>ZTIDomainJoin.wsf  
 Podczas fazy wdrożenia przywracania ten skrypt sprawdza, czy komputer jest przyłączony do domeny i odzyskiwania z nieudane próby przyłączenia do domeny.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTIDomainJoin.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|-                          **LTISuspend.wsf**<br /><br /> -                          **ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTIDomainJoin.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: *wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu).|  
|**/ DomainErrorRecovery: *wartość***|Próbuje przyłączyć komputer do domeny. W przypadku wartości określonej w wartości:<br /><br /> -                              **AUTOMATYCZNIE**. Spróbuj ponownie proces dołączania domeny. Uruchom ponownie, a następnie spróbuj ponownie. Jest to domyślne zachowanie skryptu.<br /><br /> -                              **NIEPOWODZENIE**. Zatrzymuje wszystkie przetwarzania. Zatrzymanie przetwarzania sekwencji wszystkich zadań.<br /><br /> -                              **RĘCZNE**. Zatrzymaj przetwarzanie; Zezwala użytkownikowi na ręczne dołączenie komputera do domeny.|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**Administrator domeny**|-||  
|**DomainAdminDomain**|-||  
|**DomainAdminPassword**|-||  
|**DomainErrorRecovery**|-||  
|**DomainJoinAttempts**|-|-|  
|**Przyłączania**|-||  
|**JoinWorkgroup**|-||  
|**LTISuspend**||-|  
|**MachineObjectOU**|-||  
|**Zmienna SMSTSRebootRequested**||-|  
|**SMSTSRetryRequested**||-|  

###  <a name="ZTIDrivers.wsf"></a>ZTIDrivers.wsf  
 Ten skrypt instaluje dodatkowe sterowniki urządzeń na komputerze docelowym, przed rozpoczęciem konfiguracji systemu operacyjnego. Ten skrypt odczytuje plik Drivers.xml i kopiuje listę plików sterowników urządzeń w pliku Drivers.xml (utworzony przez i zarządzane w węźle sterowniki w konsoli Deployment Workbench) do komputera docelowego.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **PnpEnum.xml**. Zawiera listę wszystkich urządzeń zainstalowanych na komputerze docelowym<br /><br /> -                          **ZTIDrivers.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|-                          **Attrib.exe**. Ustawia atrybuty plików i folderów<br /><br /> -                          **CMD.exe. Umożliwia uruchamianie narzędzia wiersza polecenia**<br /><br /> -                          **Microsoft.BDD.PnpEnum.exe**. Narzędzia, która wylicza urządzenia typu Plug and Play<br /><br /> -                          **Reg.exe**. Narzędzie rejestru konsoli do odczytywania i modyfikowania danych rejestru<br /><br /> -                          **ZTIConfigFile.vbs**. Zawiera procedury dla przetwarzania plików XML<br /><br /> -                          **ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTIDrivers.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu).|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**Architektura**|-||  
|**CustomDriverSelectionProfile**|-||  
|**DeploymentMethod**|-||  
|**DeploymentType**|-||  
|**DestinationLogicalDrive**|-|-|  
|**DoCapture**|-||  
|**DriverPaths**|-||  
|**DriverSelectionProfile**|-||  
|**ImageBuild**|-||  
|**InstallFromPath**|-||  
|**OSDAnswerFilePath**|-||  
|**OSDAnswerFilePathSysPrep**|-||  
|**OSDPlatformArch**|-||  
|**Faza**|-||  
|**ResourceRoot**|-||  

###  <a name="ZTIExecuteRunbook.wsf"></a>ZTIExecuteRunbook.wsf  
 Ten skrypt jest uruchamiany elementy runbook programu Orchestrator na komputerze docelowym. Orchestrator *runbook* sekwencja działań określająca sposób organizacji działań na komputerach i sieci. Możesz zainicjować elementy runbook programu Orchestrator za pomocą zestawu MDT [wykonania elementu Runbook](#ExecuteRunbook) zadań typ kroku sekwencji, który z kolei uruchamia ten skrypt.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|Zmienne środowiskowe zawierają wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania.|  
|**Dane wyjściowe**|— BDD.log zawiera zdarzenia, które generują wszystkie skrypty zestawu MDT.<br /><br /> -Zwrotny stan wykonania elementu runbook.<br /><br /> -Parametry zwrotu z danych wyjściowych elementu runbook.|  
|**Odwołania**|-ZTIUtility.vbs zawiera funkcje obsługi i procedur używanych przez skrypt.|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTIExecuteRunbook.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu).|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**OrchestratorServer**|-||  
|**RunbookName**|-||  
|**Element Runbook**|-||  
|**RunbookParameterMode**|-||  
|**RunbookParametersxParameterID**|-||  
|**RunbookParametersxParameterValue**|-||  
|***RunbookOutputParameters***<br /><br /> Uwaga:<br /><br /> Jeśli element runbook zwraca parametry wyjściowe, zmienną sekwencji zadań jest tworzony dla każdego parametru i zwracanych wartości parametru jest przypisany do zmiennej sekwencji zadań.||-|  

 Ten skrypt tworzy zmienne sekwencji zadań, które są wymienione w poniższej tabeli do użytku wewnętrznego skryptu. Nie ustawiaj te zmienne sekwencji zadań w CustomSettings.ini lub w bazie danych zestawu MDT.  

|**Nazwa**|**Opis**|  
|-|-|  
|**OrchestratorServer**|Nazwa serwera z uruchomionym programem Orchestrator określone w **serwera Orchestrator** w [wykonania elementu Runbook](#ExecuteRunbook) krok sekwencji zadań|  
|**RunbookName**|Nazwa elementu runbook określona w **Runbook** w [wykonania elementu Runbook](#ExecuteRunbook) krok sekwencji zadań|  
|**Element Runbook**|Identyfikator przypisany do elementu runbook na serwerze programu Orchestrator|  
|**RunbookParametersxParameterID**|Identyfikator przypisany do parametru określonego elementu runbook na serwerze programu Orchestrator|  
|**RunbookParametersxParameterName**|Nazwa przypisana do parametru określonego elementu runbook na serwerze programu Orchestrator|  
|**RunbookParametersxParameterValue**|Wartość przypisana do parametru określonego elementu runbook na serwerze programu Orchestrator|  

###  <a name="ZTIGather.wsf"></a>ZTIGather.wsf  
 Ten skrypt gromadzi właściwości i reguł przetwarzania, które kontrolują procesu wdrażania. Właściwości i reguł (znanej także jako *właściwości lokalnego*) są jawnie zdefiniowane w tym skrypcie i zawarte w pliku ZTIGather.xml, w pliku CustomSettings.ini i w bazie danych zestawu MDT (utworzonych w węźle bazy danych w ramach wdrożenia Workbench).  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTIGather.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|-                          **Wpeutil.exe**. Inicjuje środowisko Windows PE i połączeń sieciowych; Inicjuje LTI<br /><br /> -                          **ZTIDataAccess.vbs**. Zawiera procedury, aby uzyskać dostęp do bazy danych<br /><br /> -                          **ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTIGather.wsf </debug:value> </localonly> </inifile:ini_file_name>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu).|  
|**/localOnly**|Zwraca tylko informacje o komputerze docelowym i bieżący system operacyjny zainstalowany na komputerze docelowym. przeanalizować pliku .ini wejściowych (określony w **/inifile** argument); zwraca właściwości i reguły określone w pliku ini<br /><br /> Jeśli nie zostanie określony, skrypt zwraca informacje o komputerze docelowym i zainstalowanego systemu operacyjnego; analizuje pliku ini|  
|**/IniFile:ini_file_name**|Nazwa i ścieżka pliku wejściowego pliku ini, który zawiera właściwości i reguł używany w processIf wdrożenia nie określono, skrypt użyje wartości domyślnej w CustomSettings.ini|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**Wszystkie**|-|-|  

###  <a name="ZTIGroups.wsf"></a>ZTIGroups.wsf  
 Ten skrypt powoduje przechwycenie i przywrócenie członkostwo w lokalnej grupie na komputerze docelowym. Ten skrypt jest wywoływana z**/capture** argumentu, aby utworzyć kopię zapasową członkostwo w grupie z komputera docelowego przed wdrożeniem systemu operacyjnego. **CaptureGroups** właściwość zawiera listę grup, które skrypt tworzy kopie zapasowe. Skrypt jest wywoływany z**/restore** argumentu, aby przywrócić członkostwa grupy po wdrożeniu systemu operacyjnego. Podczas wykonywania operacji przywracania, także przywrócenie członkostwo wszystkich grup, których kopię zapasową utworzono podczas uruchamiania skryptu za pomocą **/capture** argumentu.  

> [!NOTE]
>  Podczas przywracania członkostwa w grupie, skrypt nie tworzy żadnych grupy docelowej, które jeszcze nie istnieje na komputerze docelowym. W związku z tym należy uwzględnić wszystkie wymagane grupy na komputerze odniesienia, podczas tworzenia pliku obrazu.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTIGroups.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generuje wszystkie skrypty zestawu MDT|  
|**Odwołania**|**ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTIGroups.wsf </debug:value> </backup> </restore>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu).|  
|**/ capture**|Tworzy kopię zapasową członkostwo grup lokalnych na komputerze docelowym, jak określono w **CaptureGroups** właściwości|  
|**/ Restore**|Przywraca członkostwo grupy lokalne kopie zapasowe wcześniej w procesie wdrażania|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**CaptureGroups**|-||  
|**Grupy**|-|-|  
|Nazwa hosta|-||  

###  <a name="ZTILangPacksOnline.wsf"></a>ZTILangPacksOnline.wsf  
 Ten skrypt instaluje pakiety językowe dla systemów operacyjnych Windows.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTILangPacksOnline.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|-                          **CMD.exe**. Umożliwia uruchamianie narzędzia wiersza polecenia<br /><br /> -                          **Lpksetup.exe**. Narzędzie Instalatora pakietów językowych, używane do dodawania lub usuwania pakietów językowych<br /><br /> -                          **ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTILangPacksOnline.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu).|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**Architektura**|-||  
|**OSVersion**|-||  

###  <a name="ZTIModifyVol.wsf"></a>ZTIModifyVol.wsf  
 Ten skrypt modyfikuje woluminu, aby ustawić GPT identyfikator i atrybuty woluminów narzędzia potrzebne do tworzenie partycji środowiska Windows RE na komputerach z interfejsem UEFI. Ten skrypt musi zostać wywołana podczas wdrażania na komputerach z interfejsem UEFI w takich sytuacjach:  

-   Gdzie struktury partycji niestandardowe (woluminu) są tworzone, takich jak tworzenie partycji pięć zamiast standardowego cztery partycje, które są przeznaczone do użycia z interfejsem UEFI typicaly wdrożenia LTI  

-   Wszystkie wdrożenia ZTI i UDI  

> [!NOTE]
>  Ten skrypt ma zostać wywołana tylko wtedy, gdy tworzenia struktury partycji do użycia z interfejsem UEFI. Podczas tworzenia struktury partycji do użycia we wdrożeniach bez UEFI nie należy wywoływać ten skrypt.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|BDD.log zawiera zdarzenia, które generują wszystkie skrypty zestawu MDT.|  
|**Odwołania**|ZTIUtility.vbs zawiera funkcje obsługi i procedur używanych przez skrypt.|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTIModifyVol.wsf /UtilityVol:value </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ UtilityVol: * wartość***|Zawiera literę dysku woluminu, który musi być skonfigurowana dla partycji narzędzia środowiska odzyskiwania systemu Windows dla komputerów z interfejsem UEFI (na przykład "E:")|  
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu).|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**UtilityVol**|-||  

###  <a name="ZTIMoveStateStore.wsf"></a>ZTIMoveStateStore.wsf  
 Ten skrypt przenosi C:\Windows\Temp\StateStore przechwyconego stanu użytkownika i pliki kopii zapasowej.  

> [!NOTE]
>  Ten skrypt jest uruchamiany tylko w przypadku wdrażania obrazów za pomocą programu Configuration Manager.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTIMoveStateStore.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|**ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTIMoveStateStore.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu).|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|Brak|||  

###  <a name="ZTINextPhase.wsf"></a>ZTINextPhase.wsf  
 Ten skrypt aktualizacji **fazy** właściwości do następnej fazy w procesie wdrażania. Sekwencjonowania zadań używa tych fazach, aby określić kolejność, w którym należy wykonać wszystkie zadania. **Fazy** właściwość zawiera następujące wartości:  

-   **SPRAWDZANIE POPRAWNOŚCI**. Określ, czy komputer docelowy ma możliwość uruchamiania skryptów niezbędne do ukończenia procesu wdrażania.  

-   **STATECAPTURE**. Zapisz wszelkie dane migracji stanu użytkownika przed wdrożeniem nowego docelowego systemu operacyjnego.  

-   **INSTALACJĄ**. Ukończ wszelkie zadania, które muszą być przeprowadzone (takich jak tworzenie nowych partycji), przed wdrożeniem docelowego systemu operacyjnego.  

-   **ZAINSTALUJ**. Zainstaluj docelowy system operacyjny na komputerze docelowym.  

-   **WYKONYWANE**. Ukończ wszelkie zadania, które należy wykonać przed przywróceniem danych migracji stanu użytkownika. Te zadania dostosować docelowego systemu operacyjnego, przed uruchomieniem komputera docelowego po raz pierwszy po wdrożeniu (na przykład instalowanie aktualizacji lub dodawanie sterowników).  

-   **STATERESTORE**. Przywróć zapisany w fazie przechwytywania stanu danych migracji stanu użytkownika.  

 Aby uzyskać więcej informacji na temat **fazy** właściwości, zobacz odpowiedni temat w [właściwości](#Properties).  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTINextPhase.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|**ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTINextPhase.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu).|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**DeploymentMethod**|-||  
|**Faza**|-|-|  

###  <a name="ZTINICConfig.wsf"></a>ZTINICConfig.wsf  
 Ten skrypt konfiguruje kart sieciowych aktywowane przy użyciu wartości, które ZTIGather.wsf przechwycone na podstawie właściwości wymienionych w pliku CustomSettings.ini lub zestaw MDT bazy danych (utworzonych w węźle bazy danych w konsoli Deployment Workbench).  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTINICConfig.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|-                          **ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt<br /><br /> -                          **ZTINicUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTINicConfig.wsf </debug:value> </ForceCapture> </RestoreWithinWinPE>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu).|  
|**/ ForceCapture**|Jeśli ma żadnych lokalnych sieci kart przy użyciu statycznych adresów IP zapisane, ten skrypt przechwytuje te ustawienia i zapisuje je w środowisku lokalnym, na przykład C:\MININT\SMSOSD\OSDLogs\Variables.dat. Ten skrypt może być przydatne podczas przechwytywania statyczne ustawienia IP dla wielu komputerów w celu automatyzacji.|  
|/ RestoreWithinWinPE|W przypadku dotyczy żadnych zapisanych ustawień sieci statycznego adresu IP komputera lokalnego, gdy jest to odpowiednie; używany do wewnętrznego tylko przetwarzania.|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**DeployDrive**|-|-|  
|**DeploymentMethod**|-||  
|**DeploymentType**|-||  
|**DeployRoot**|-||  
|**OSDAdapterCount**|-|-|  
|**OSGuid**|-||  
|**OSDMigrateAdapterSettings**|-||  
|**Faza**|-||  

###  <a name="ZTINICUtility.vbs"></a>ZTINICUtility.vbs  
 Ten skrypt zawiera funkcje związane z karty sieciowej i że różnych skryptów w ramach wdrożenia zestawu MDT przetwarzania wywołania procedur.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|Brak|  
|**Dane wyjściowe**|Brak|  
|**Odwołania**|-                          **CMD.exe**. Umożliwia uruchamianie narzędzia wiersza polecenia<br /><br /> -                          **Netsh.exe**. Narzędzie używane do automatyzowania konfiguracji składników sieciowych|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`<script language="VBScript" src="ZTINicUtility.vbs"/>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|Brak|Brak|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**OSDAdapter * AdapterIndexAdapterName***|-|-|  

> [!NOTE]
>  *AdapterIndex*w tej właściwości jest symbolem zastępczym dla tablicy liczony od zera, który zawiera informacje dotyczące karty sieciowej.  

###  <a name="ZTIOSRole.wsf"></a>ZTIOSRole.wsf  
 Ten skrypt instalacji ról serwera dla komputerów docelowych, na których działają systemy operacyjne Windows. Odczytuje **OSRoles**, **OSRoleServices**, i **OSFeatures** właściwości, aby określić, co powinna zostać zainstalowana.  

> [!NOTE]
>  Ten skrypt jest powinna być wywoływana tylko przez **zainstalować role i funkcje** i**odinstalowywanie ról i funkcji** czynności sekwencji zadań. Bezpośrednie wywoływanie ten skrypt nie jest obsługiwana.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTIOSRole.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|-                          **CMD.exe**. Umożliwia uruchamianie narzędzia wiersza polecenia<br /><br /> -                          **OCSetup.exe**. Dodaje lub usuwa opcjonalnych składników systemu Windows<br /><br /> -                          **ServerManagerCmd.exe**. Instaluje, konfiguruje i zarządza nimi role i funkcje systemu Windows Server<br /><br /> -                          **Sysocmgr.exe**. Dodaje lub usuwa składniki systemu Windows<br /><br /> -                          **ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTIOSRole.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu).|  
|**/ Dezinstalacji**|W przypadku tego argumentu wskazuje, że role i funkcje zostaną odinstalowane. Jeśli nie zostanie podany, skrypt przyjmuje role i funkcje zostaną zainstalowane.|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**IsServerCoreOS**|-||  
|**OSFeatures**|-||  
|**OSRoles**|-||  
|**OSRoleServices**|-||  
|**OSVersion**|-||  
|**Zmienna SMSTSRebootRequested**||-|  

###  <a name="ZTIPatches.wsf"></a>ZTIPatches.wsf  
 Ten skrypt instaluje aktualizacje (pakiety językowe, aktualizacje zabezpieczeń i tak dalej), które są wymienione w pliku Packages.xml. Skrypt zakończy własnym, jeśli wdrożenie nie jest w jednym z następujących stanów:  

-   **Faza** jest równe **PREINSTALACJI**  

-   **DeploymentMethod** jest równe **SCCM**  

 Skrypt uruchamia Pkgmgr, jeśli **DeploymentMethod** jest równe **SCCM**.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTIPatches.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|-                          **Expand.exe**. Rozwija skompresowane pliki<br /><br /> -                          **Pkgmgr.exe**. Instaluje lub w trybie offline aktualizacje systemu Windows Vista<br /><br /> -                          **ZTIConfigFile.vbs**. Zawiera procedury dla przetwarzania plików XML<br /><br /> -                          **ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTIPatches.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu).|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**Architektura**|-||  
|**CustomPackageSelectionProfile**|-||  
|**DeployRoot**|-||  
|**DeploymentMethod**|-||  
|**DeploymentType**|-||  
|**DestinationLogicalDrive**|-||  
|**LanguagePacks**|-||  
|**OSDAnswerFilePath**|-||  
|**OSDPlatformArch**|-||  
|**PackageSelectionProfile**|-||  
|**Faza**|-||  
|**ResourceRoot**|-||  

###  <a name="ZTIPowerShell.wsf"></a>ZTIPowerShell.wsf  
 Ten skrypt uruchamia skrypt programu Windows PowerShell przy użyciu hosta niestandardowego programu Windows PowerShell.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTIPowerShell.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT<br /><br /> -                          **Kod powrotu**. Wartość liczbowa zwróconych przez skrypt programu Windows PowerShell po zakończeniu, które wskazuje stan wykonania skryptu.|  
|**Odwołania**|-                          **Microsoft.BDD.TaskSequencePSHost.exe**. Niestandardowy host programu Windows PowerShell służące do uruchamiania skryptu programu Windows PowerShell.|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTIPowerShell.wsf`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**Brak**||  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**Brak**|||  

###  <a name="ZTIPrereq.vbs"></a>ZTIPrereq.vbs  
 Ten skrypt sprawdza, czy komputer docelowy ma wstępnie wymagane oprogramowanie zostało zainstalowane i funkcjonalności. Dostępne są następujące testy, które wykonuje skrypt:  

-   Ustal, czy wersja skryptów systemu Windows jest równa lub większa niż wersja 5.6.  

-   Sprawdź, czy nie występują żadne błędy podczas wystąpienia są tworzone MSXML2, którego Scripting.FileSystemObject obiektu WScript.Shell., Wscript.Network, odwołania do obiektów. DOMDocument oraz środowisko procesu.  

 Jeśli dowolny kontroli nie powiedzie się, występuje błąd, a skrypt zakończy pracę **ValidatePrereq** procedury.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|Brak|  
|**Dane wyjściowe**|Brak|  
|**Odwołania**|Brak|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`None`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|Brak|Brak|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|Brak|||  

###  <a name="ZTISCCM.wsf"></a>ZTISCCM.wsf  
 Ten skrypt inicjuje ZTI podczas wdrażania przy użyciu programu Configuration Manager. Skrypt wykonuje następujące procedury:  

1.  Jeśli debugowanie jest aktywna, skrypt tworzy OSD. Plik debugowania.  

2.  Skrypt konfiguruje następujące właściwości:  

    -   **ScriptRoot**ustawiono folder nadrzędny obecnie uruchamianie skryptu.  

    -   **DeployRoot** ustawiono folder nadrzędny **ScriptRoot**.  

    -   **ResourceRoot** ustawiono **DeployRoot**.  

    -   **DeploySystemDrive** ustawiono **C:**.  

    -   **DeploymentMethod** ustawiono **SCCM**.  

3.  Gdy **DeployRoot**zawiera **:\\***:*  

    -   **DeployRoot** folder jest kopiowany do **_SMSTSMDataPath**\WDPackage  

    -   **ScriptRoot** ustawiono **_SMSTSMDataPath**\WDPackage\Scripts  

    -   **DeployRoot** ustawiono folder nadrzędny **ScriptRoot**  

    -   **ResourceRoot** ustawiono **DeployRoot**  

4.  Gdy **fazy** jest **NULL**:  

    -   Jeśli zmienna środowiskowa % SystemDrive % jest **X:**, następnie **DeploymentType**ustawiono **NEWCOMPUTER** i **fazy** ma ustawioną wartość **INSTALACJĄ**. W przeciwnym razie**DeploymentType** ustawiono **Zastąp** i **fazy** ma ustawioną wartość **weryfikacji**.  

    -   Jeśli **OldComputer**istnieje folder nadrzędny bieżącego uruchamianie skryptu, plik .tag **DeploymentType** ustawiono **Zastąp** i **fazy**ma ustawioną wartość **weryfikacji**. W przeciwnym razie**DeploymentType** ustawiono **ODŚWIEŻ** i **fazy** ma ustawioną wartość **weryfikacji**.  

 Aby uzyskać więcej informacji na temat tych właściwości, zobacz odpowiednich tematów w [właściwości](#Properties).  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTISCCM.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|**ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTISCCM.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu).|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**_SMSTSMDataPath**|-||  
|**Architektura**|-||  
|**BDDPackageID**|-|-|  
|**DeploymentMethod**|-|-|  
|**DeploymentType**|-|-|  
|**DeployRoot**|-|-|  
|**Faza**|-|-|  
|**ResourceRoot**|-|-|  
|**ScriptRoot**|-|-|  
|**ToolRoot**|-|-|  

###  <a name="ZTISetVariable.wsf"></a>ZTISetVariable.wsf  
 Ten skrypt ustawia zmienną sekwencji określonego zadania globalne odpowiadający nazwy zawarte w **nazwa_zmiennej** wartości zawartych w **VariableValue**.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTISetVariable.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|**ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTISetVariable.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu).|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**Nazwa_zmiennej**|-||  
|**VariableValue**|-||  

###  <a name="ZTITatoo.wsf"></a>ZTITatoo.wsf  
 Ten skrypt tattoos do komputera docelowego z identyfikacji i informacje o wersji. Skrypt wykonuje następujące procedury:  

1.  Znajdź, a następnie skopiuj plik ZTITatoo.mof do folderu %SystemRoot%\System32\Wbem. Wszystkie istniejące wcześniej ZTITatoo.mof, który istnieje w miejscu docelowym zostaną usunięte przed uruchomieniem operacji kopiowania.  

2.  Mofcomp.exe zostanie wykonana przy użyciu następującego polecenia:  

    ```  
    %SystemRoot%\System32\Wbem\Mofcomp.exe -autorecover %SystemRoot%\System32\Wbem\ZTITatoo.mof.  
    ```  

3.  Dla wszystkich metod wdrażania (LTI, ZTI i UDI), te szczegóły wdrożenia są zapisywane dla wszystkich metod wdrażania w rejestrze w **HKEY_LOCAL_MACHINE\Software\Microsoft\Deployment 4**:  

    -   **Metody wdrażania** ustawiono metodę wdrażania i może być ustawiony na **LTI**, **ZTI**, lub **UDI**w zależności od wdrożenia trwa — metoda wykonywane.  

    -   **Źródło wdrożenia** ustawiono źródła wdrożenia i może być ustawiony na **OEM**, **nośnika**, lub wartość w **DeploymentMethod** właściwości.  

    -   **Typ wdrożenia** ustawiono **DeploymentType** właściwości.  

    -   **Sygnatura czasowa wdrożenia** jest ustawiona na bieżącą datę w formacie daty WMI.  

    -   **Wersja zestawu narzędzi wdrażania** ustawiono **wersji** właściwości.  

4.  We wdrożeniach LTI, te szczegóły wdrożenia są zapisywane w rejestrze w **HKEY_LOCAL_MACHINE\Software\Microsoft\Deployment 4**:  

    -   **Identyfikator sekwencji zadań** ustawiono **TaskSequenceID**właściwości.  

    -   **Nazwa sekwencji zadań** ustawiono **TaskSequenceName** właściwości.  

    -   **Wersja sekwencji zadań** ustawiono **TaskSequenceVersion** właściwości.  

5.  We wszystkich wdrożeniach programu Configuration Manager (ZTI i UDI programu Configuration Manager), te szczegóły wdrożenia są zapisywane w rejestrze w **HKEY_LOCAL_MACHINE\Software\Microsoft\Deployment 4**:  

    -   Identyfikator pakietu OSD ma ustawioną wartość **_SMSTSPackageID** zmienną sekwencji zadań.  

    -   **Nazwa programu OSD** ma zawsze wartość "**\***".  

    -   **Identyfikator anonsu OSD** ustawiono **_SMSTSAdvertID** zmienną sekwencji zadań.  

6.  We wdrożeniach LTI gdzie jest przechwycenie obrazu, te szczegóły wdrożenia są zapisywane w rejestrze w **HKEY_LOCAL_MACHINE\Software\Microsoft\Deployment 4**:  

    -   **Metoda przechwytywania** ustawiono metodę wdrażania i może być ustawiony na **LTI**, **ZTI**, lub **UDI**w zależności od wdrożenia trwa — metoda wykonywane.  

    -   **Przechwyć sygnatury czasowej** jest ustawiona na bieżącą datę w formacie daty WMI.  

    -   **Przechwytywanie wersji zestawu narzędzi** ustawiono **wersji** właściwości.  

    -   **Identyfikator sekwencji zadań Przechwyć** ustawiono **TaskSequenceID**właściwości.  

    -   **Nazwa sekwencji zadań Przechwyć** ustawiono **TaskSequenceName** właściwości.  

    -   **Przechwytywanie wersji sekwencji zadań** ustawiono **TaskSequenceVersion** właściwości.  

7.  We wdrożeniach wszystkich programu Configuration Manager (ZTI i UDI programu Configuration Manager) w których jest przechwycenie obrazu, te szczegóły wdrożenia są zapisywane w rejestrze w **HKEY_LOCAL_MACHINE\Software\Microsoft\Deployment 4** :  

    -   **Identyfikator pakietu OSD przechwytywania** ustawiono **_SMSTSPackageID** zmienną sekwencji zadań.  

    -   **Nazwa programu OSD przechwytywania** ma zawsze wartość "***".  

    -   **Przechwyć identyfikator anonsu OSD** ustawiono **_SMSTSAdvertID**zmienną sekwencji zadań.  

    > [!NOTE]
    >  Ten skrypt nie jest przeznaczony do uruchamiania w środowisku Windows PE.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTITatoo.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|-                          **Mofcomp.exe**. Kompilator pliku MOF wiersza polecenia<br /><br /> -                          **ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTITatoo.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu).|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**_SMSTSAdvertID**|-||  
|**_SMSTSPackageID**|-||  
|**_SMSTSSiteCode**|-||  
|**DeploymentMethod**|-||  
|**DeploymentType**|-||  
|**Wersja**|-||  
|**TaskSequenceID**|-||  
|**TaskSequenceName**|-||  
|**TaskSequenceVersion**|-||  

###  <a name="ZTIUserState.wsf"></a>ZTIUserState.wsf  
 Ten skrypt inicjuje narzędzia USMT do przechwycenia i przywrócenia stanu użytkownika na komputerze docelowym.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTIUserState.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|-                          **CMD.exe**. Umożliwia uruchamianie narzędzia wiersza polecenia<br /><br /> -                          **Loadstate.exe**. Depozyty dane stanu użytkownika na komputerze docelowym<br /><br /> -                          **Msiexec.exe**. Służy do zarządzania instalacją aplikacji msi<br /><br /> -                          **Scanstate.exe**. Służy do zbierania danych i ustawień użytkownika<br /><br /> -                          **Pliki aplikacji narzędzia USMT**<br /><br /> -                          **ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTIUserState.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|/Debug:Value|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu).|  
|**/ Przechwytywania**|—|  
|**/ Szacowania**|—|  
|**/ Przywracania**|—|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**Architektura**|-||  
|**DeploymentMethod**|-||  
|**DeploymentType**|-||  
|**DestinationLogicalDrive**|-||  
|**ImageBuild**|-||  
|**ImageSize**|-||  
|**ImageSizeMultiplier**|-||  
|**InstallFromPath**|-||  
|**IsServerOS**|-||  
|**LoadStateArgs**|-||  
|**OSCurrentVersion**|-||  
|**OSDMigrateAdditionalCaptureOptions**|-|-|  
|**OSDMigrateAdditionalRestoreOptions**|-|-|  
|**OSDPackagePath**|-||  
|**OSDStateStorePath**||-|  
|**OSVersion**|-||  
|**ScanStateArgs**|-||  
|**StatePath**|-|-|  
|**UDDir**|-||  
|**UDProfiles**|-||  
|**UDShare**|-||  
|**UserDataLocation**|-|-|  
|**USMTConfigFile**|-||  
|**USMTEstimate**|-|-|  
|**USMTLocal**||-|  
|**USMTMigFiles**|-||  

###  <a name="ZTIUtility.vbs"></a>ZTIUtility.vbs  
 Ten skrypt zawiera funkcje narzędzia, korzystających z większości skryptów zestawu MDT.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|Brak|  
|**Odwołania**|-                          **Credentials_ENU.XML**. Wyświetla monit o poświadczenia, które będą używane podczas nawiązywania połączenia z zasobami sieciowymi<br /><br /> -                          **IPConfig.exe**. Wyświetla wszystkie bieżące wartości konfiguracji sieci TCP/IP i odświeża ustawienia DHCP i DNS<br /><br /> -                          **MSHTA.exe**. Host aplikacji HTML<br /><br /> -                          **Regsvr32.exe**. Rejestruje pliki (.dll, .exe, .ocx itd.) w systemie operacyjnym<br /><br /> -                          **Xcopy.exe**. Kopiuje pliki i katalogi, w tym podkatalogów|  
|**Lokalizacja**|-                          *dystrybucji*\Scripts<br /><br /> -                          *Program_Files*\Microsoft Deployment Toolkit\Scripts|  
|**Użycie**|`<script language="VBScript" src="ZTIUtility.vbs"/>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|Brak|Brak|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**_SMSTSAdvertID**|-||  
|**_SMSTSCurrentActionName**|-||  
|**_SMSTSCustomProgressDialogMessage**|-||  
|**_SMSTSInstructionTableSize**|-||  
|**_SMSTSLogPath**|-||  
|**_SMSTSMachineName**|-||  
|**_SMSTSNextInstructionPointer**|-||  
|**_SMSTSOrgName**|-||  
|**_SMSTSPackageID**|-||  
|**_SMSTSPackageName**|-||  
|**_SMSTSPackagePath**|-||  
|**_SMSTSReserved1**|-||  
|**_SMSTSReserved2**|-||  
|**Architektura**|-||  
|**AssetTag**|-||  
|**Nazwa_komputera**|-||  
|**Debugowania**|-|-|  
|**DeploymentMethod**|-||  
|**DeployRoot**|-||  
|**DestinationDisk**|-|-|  
|**DestinationLogicalDrive**|-|-|  
|**DestinationPartition**|-|-|  
|**EventShare**|-||  
|**Nazwa hosta**|-||  
|**ImageBuild**|-|-|  
|**ImageFlags**||-|  
|**Sekcji ImageIndex**||-|  
|**ImageLanguage**||-|  
|**ImageProcessor**||-|  
|**ImageSize**||-|  
|**InstallFromPath**||-|  
|**Przyłączania**|-||  
|**Ścieżka dziennika**|-|-|  
|**MacAddress**|-||  
|**OSCurrentVersion**|-||  
|**OSDAdvertID**|-||  
|**OSDAnswerFilePath**|-|-|  
|**OSDAnswerFilePathSysprep**|-|-|  
|**OSDComputerName**|-|-|  
|**OSDPackageID**|-||  
|**OSDPackagePath**|-||  
|**OSDTargetSystemDrive**|-||  
|**OSGUID**||-|  
|**OSSKU**|-||  
|**OSVersion**|-||  
|**Faza**|-||  
|**Processor_Architecture**|-||  
|**ResourceRoot**|-||  
|**SLShare**|-||  
|**SLShareDynamicLogging**|-||  
|**TaskSequenceID**|-||  
|**TaskSequenceName**||-|  
|**TaskSequenceVersion**||-|  
|**UDDir**|-||  
|**UDShare**|-||  
|**UserDomain**|-|-|  
|**Nazwa użytkownika**|-|-|  
|**Hasła użytkownika**|-|-|  
|**IDENTYFIKATOR UUID**|-||  
|**Wersja**<br /><br /> **Uwaga:** Ta zmienna jest zmienna wewnętrzna, która reprezentuje wersji zestawu MDT.|-|-|  
|**WDSServer**|-||  

###  <a name="ZTIValidate.wsf"></a>ZTIValidate.wsf  
 Ten skrypt zapewnia bezpiecznego dla wdrożenia, aby kontynuować weryfikując warunek na komputerze docelowym. Dostępne są następujące procesy skryptu:  

-   Jeśli **DeploymentType** jest równe odświeżania i komputer docelowy jest serwerem, skrypt zakończy pracę.  

-   Jeśli **OSInstall** istnieje i nie jest równa tak, skrypt zakończy pracę.  

-   Sprawdź, czy minimalna ilość pamięci RAM istnieje na komputerze docelowym. Jeśli nie, skrypt zakończy pracę.  

-   Sprawdź, czy procesor spełnia minimalna wymagana szybkość; Jeśli nie, skrypt zakończy pracę.  

-   Sprawdź, czy rozmiar dysku twardego spełnia wymagania minimalnego rozmiaru; Jeśli nie, skrypt zakończy pracę.  

-   Sprawdź, czy system operacyjny na komputerze docelowym jest zainstalowany na dysku C; Jeśli nie, skrypt zakończy pracę.  

-   Jeśli **DeploymentType = odświeżania**, sprawdź, czy dysk C nie jest skompresowany, uruchamiając `Compact /u C:\`.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTIValidate.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|-                          **Compact.exe**. Wyświetla lub zmienia kompresję pliki na partycji systemu plików NTFS<br /><br /> -                          **ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTIValidate.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu).|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**DeploymentType**|-||  
|**DestinationLogicalDrive**|-|-|  
|**ImageBuild**|-||  
|**ImageMemory**|-||  
|**ImageProcessorSpeed**|-||  
|**ImageSize**|-||  
|**ImageSizeMultiplier**|-||  
|**IsServerOS**|-||  
|**Pamięć**|-||  
|**OSDPackagePath**|-||  
|**OSInstall**|-||  
|**ProcessorSpeed**|-||  
|**Zmiennej SMSTSLocalDataDrive**||-|  
|**VerifyOS**|-||  

###  <a name="ZTIVHDCreate.wsf"></a>ZTIVHDCreate.wsf  
 Ten skrypt jest używany do tworzenia pliku wirtualnego dysku twardego (VHD i avhd), na komputerze docelowym i instalowania plików VHD jako dysk. Następnie innych części procesu wdrożenia LTI wdrażania systemu operacyjnego i aplikacji do nowo utworzony wirtualny dysk twardy. Procesy skryptu są następujące:  

-   **Class_Initialize** metoda służy do inicjowania **VHDInputVariable** zmiennej.  

-   Sprawdzić, czy **VHDCreateSource** są zdefiniowane i lokalizuje plik VHD źródła (Jeśli określono).  

-   Generuj nazwę pliku VHD losowych, jeśli **VHDCreateFilename** jest równe losowych lub "" (null).  

-   Sprawdź, czy folder istnieje gdzie pliku VHD (określony w **VHDCreateFileName**) do utworzenia.  

-   Utwórz plik VHD za pomocą wartości w **VHDCreateSizePercent**, **VHDCreateSizeMax**, i **VHDCreateType**.  

-   Utworzyć dysku różnicowego (Jeśli określono) przy użyciu wartości w **VHDCreateDiffVHD**.  

-   Plik VHD nowo utworzona i opcjonalnie dysku różnicowego są zainstalowane.  

-   Numer dysku zainstalowanego wirtualnego dysku twardego jest zwracana.  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTIVHDCreate.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|-                          **ZTIDiskUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur używanych przez skrypt<br /><br /> -                          **ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTIVHDCreate.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu).|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**VHDCreateDiffVHD**|-||  
|**VHDCreateFileName**|-||  
|**VHDCreateSizeMax**|-||  
|**VHDCreateSource**|-||  
|**VHDCreateType**|-||  
|**Dyskivhd**||-|  
|**VHDInputVariable**|-||  
|**VHDOutputVariable**|-||  

###  <a name="ZTIWindowsUpdate.wsf"></a>ZTIWindowsUpdate.wsf  
 Ten skrypt pobiera i instaluje aktualizacje z komputerów w sieci firmowej, uruchomionych usług WSUS, usługi Windows Update lub Microsoft Update przy użyciu [Windows Update Agent (WUA)](http://msdn2.microsoft.com/library/Aa387099.aspx) interfejsu programowania aplikacji (API). Domyślnie ta funkcja jest wyłączona w poszczególnych sekwencji zadań i musi zostać aktywowany ręcznie do uruchomienia.  

 Większość przedsiębiorstw mają już zespołów i infrastruktury w celu aktualizacji nowo wdrożone komputery w sieci firmowej. Ten proces obejmuje śledzenia zestaw najnowszych poprawek, sterowniki i aktualizacje dostępne dla każdej konfiguracji pulpitu i określania, które aktualizacje powinny zostać pobrana i zainstalowana dla każdej konfiguracji. Jeśli organizacja już ma ustalonych proces ten skrypt nie może być konieczne. Ten skrypt został zaprojektowany do wypełnienia potrzebę zespoły wdrożenia, które nie może mieć ustalonych procesów, ale aby mieć pewność, że komputery docelowe są aktualizowane po wdrożeniu.  

 Ten skrypt skanuje komputer docelowy i automatycznie pobierze szeroką gamę aktualizacje, które zostały znalezione mają zastosowanie. Należą do nich:  

-   Dodatki service Pack systemu Windows  

-   Sterowniki firmy innej niż Microsoft, które zostały umieszczone w usłudze Windows Update  

-   Najnowsze poprawki  

-   Aktualizacje programu Microsoft Office  

-   Aktualizacje programu Microsoft Exchange Server i SQL Server  

-   Aktualizacje Microsoft Visual Studio®  

-   Niektóre aktualizacje aplikacji innych firm  

> [!TIP]
>  Wielu producentów sprzętu umieszczony ich sterowniki w witrynie Windows Update. Te sterowniki nie muszą już być obsługiwany w katalogu sterowników Out-of-Box. Wypróbuj przez usunięcie z udziału dystrybucyjnego, które są dostępne w usłudze Windows Update sterowniki. Należy pamiętać, że jeśli sterowniki nie są dołączone do systemu Windows domyślnie nie usuwaj sieci lub sterowników magazynu, ponieważ system operacyjny będzie wymagać wprowadzenia danych przez użytkownika.  

 Zestaw MDT obsługuje możliwość wdrażania zaktualizowaną wersję WUA jako część wdrożenia systemu operacyjnego. Dzięki temu komputery docelowe działają poprawna wersja programu Windows Update Agent podczas ich wdrażania. Pomaga również wyeliminować konieczność łączenia się z Internetem i pobrać najnowszą wersję programu Windows Update Agent po wdrożeniu.  

 Zestaw MDT można również skonfigurować usługa WUA mogła zbierać aktualizacje z komputerów w sieci firmowej, uruchomionych usług WSUS zamiast łączenie z Microsoft Updates za pośrednictwem Internetu. Zestaw MDT można opcjonalnie skonfigurować WUA do określonego komputera z systemem przy użyciu usług WSUS **WSUSServer** właściwości.  

 Aby uzyskać dodatkowe informacje oraz WUA instrukcje dotyczące wdrażania, zobacz [jak zainstalować program Windows Update Agent na komputerach klienckich](http://technet.microsoft.com/library/bb932139.aspx).  

 Uzyskać najnowszą wersję programu Windows Update Agent autonomicznego Instalatora dla:  

-   x86 wersji (WindowsUpdateAgent30-x86.exe) na [http://go.microsoft.com/fwlink/?LinkID=100334](http://go.microsoft.com/fwlink/?LinkID=100334)  

-   x64 wersji (WindowsUpdateAgent30-x64.exe) w [http://go.microsoft.com/fwlink/?LinkID=100335](http://go.microsoft.com/fwlink/?LinkID=100335)  

 Windows 7 i nowszych obejmują najnowszą wersję programu Windows Update Agent, uaktualnienie nie jest konieczne.  

 Aby uzyskać więcej informacji, zobacz [aktualizacja usługi Windows Update Agent](http://msdn2.microsoft.com/library/aa387285.aspx).  

 Po włączeniu w sekwencjonowania zadań, ten skrypt jest uruchamiany wiele razy znajduje się w stanie przywrócić fazy wdrożenia systemu operacyjnego. Najpierw uruchomieniu po uruchomieniu systemu operacyjnego po raz pierwszy. Upewnij się, że zainstalowano najnowsze aktualizacje i dodatków service pack przed rozpoczęciem instalacji wszystkie aplikacje, które może być zależna od określone aktualizacje lub dodatki service pack jest zainstalowany na komputerze docelowym. Na przykład aplikacja może być zależny od najnowszej wersji programu Microsoft .NET Framework jest zainstalowana.  

 Ten skrypt jest uruchamiany również po instalacji aplikacji, który zapewnia, że zastosowano najnowsze dodatki service Pack dla aplikacji i aktualizacji. Na przykład użyć tego skryptu, aby upewnić się, że najnowsze aktualizacje są stosowane do pakietu Microsoft Office 2010 lub Office 2007.  

 Jest to możliwe, podczas instalacji co najmniej jednej aktualizacji, komputer docelowy należy ponownie uruchomić, aby zezwolić na zakończenie pełnej instalacji aktualizacji. Aby upewnić się, że aktualizacje zostały poprawnie zainstalowane, jeśli skrypt wykryje, że instalacja aktualizacji wymaga ponownego uruchomienia komputera docelowego, skrypt automatycznie ponownie uruchomi komputer docelowy i wznawia Jeśli dodatkowe aktualizacje zostały wykryte i Oczekiwanie na instalację. Skrypt zakończy pracę, gdy ustali, że komputer docelowy jest w pełni aktualne. Błąd zostanie zarejestrowany, jeśli podczas aktualizowania komputera docelowego, skrypt ma siedmiu nieudanych prób zainstalowania aktualizacji i komputer docelowy nadal wymaga ponownego uruchomienia.  

 W czasie wykonywania skrypt wykonuje następujące zadania:  

-   Skonfiguruj komputer docelowy, aby użyć serwera programu WSUS, jeśli **WSUSServer** właściwość została określona.  

-   Sprawdź, czy najnowsza wersja usługi WUA jest zainstalowany na komputerze docelowym.  

-   Wyszukiwanie komputera docelowego dla odpowiednich aktualizacji, które nie są już zainstalowane i które mogą być zwykle ukryte.  

-   Każda aktualizacja ma skojarzoną **UpdateID** i **QNumber** właściwości:  

    -   **UpdateID** właściwości ma postać identyfikatora GUID, takich jak *67da2176-5c57-4614-a514-33abbdd51f67*.  

    -   **QNumber** właściwość ma wartość liczbową *987654*.  

-   Porównuje skrypt **UpdateID** i **KBArticle** wartości właściwości z listy wykluczeń określona we właściwościach zestawu MDT następujące:  

    -   **WUMU_ExcludeID**. Lista UpdateIDs do wykluczenia; wszelkie aktualizacji z **UpdateID** znaleziony w liście nie zostaną zainstalowane.  

    -   **WUMU_ExcludeKB**. Listę **QNumbers** do wykluczenia; dowolnej aktualizacji z **QNumber** znaleziony w liście nie zostaną zainstalowane.  

    -   Ponadto każda aktualizacja, która wymaga danych wejściowych użytkownika zostanie wyłączone i nie jest zainstalowany.  

-   Wszystkie aktualizacje, które wymagają zatwierdzenia z umowy licencyjnej użytkownika końcowego (EULA) są automatycznie zatwierdzane przez skrypt. Pamiętaj ręcznie odczytać i sprawdzić każdej umowy EULA przed wykonaniem tego skryptu w środowisku produkcyjnym.  

-   Działania dotyczące każdej aktualizacji są zapisywane do pliku ZTIWindowsUpdate.log z parametrami instalacji lub POMIŃ po zatwierdzeniu aktualizacji do instalacji, a także UpdateID, krótki opis aktualizacji i QNumber.  

-   Każda aktualizacja do zainstalowania jest pobierany i instalowany w partiach.  

-   Komputer docelowy może wymagać więcej niż jednego ponownego uruchomienia komputera w trakcie instalacji aktualizacji.  

> [!NOTE]
>  Windows Internet Explorer 7 wymaga interakcji użytkownika, więc nie jest zainstalowany za pomocą tego skryptu.  

> [!NOTE]
>  Domyślnie zawierają **QNumber 925471** w **WUMU_ExcludeKB** listy, aby uniemożliwić Windows Vista Ultimate instalowanie pakietów językowych dodatkowe.  

> [!NOTE]
>  Jeśli źródeł sieci intranet nie są dostępne, ten skrypt pobiera pliki z dwóch lokacji firmy Microsoft: [http://update.microsoft.com/redist/wuredist.cab](http://update.microsoft.com/redist/wuredist.cab) i [http://download.windowsupdate.com/v6/windowsupdate/ Redist/Standalone/muauth.cab](http://download.windowsupdate.com/v6/windowsupdate/redist/standalone/muauth.cab).  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTIWindowsUpdate.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|-                          **Expand.exe**. Rozwija skompresowane pliki<br /><br /> -                          **NET.exe**. Wykonuje zadania zarządzania w sieci<br /><br /> -                          **WindowsUpdateAgent30-x86.exe**. Instaluje WUA<br /><br /> -                          **WindowsUpdateAgent30-x64.exe**. Instaluje WUA<br /><br /> -                          **ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTIWindowsUpdate.wsf </debug:value> </UpdateCommand:"<IsInstalled=0&#124;1> <IsHidden=0&#124;1>"> </Query:true&#124;false>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu).|  
|**/ UpdateCommand: * param***|-                              **IsInstalled**. Ustaw **0** zapytania aktualizacji, które nie są zainstalowane.<br /><br /> -                              **IsHidden**. Ustaw **0** zapytania aktualizacji, które są ukryte.|  
|**/ Zapytania: * wartość***|-                              **Wartość true,**. Zapytanie tylko dla wymaganych aktualizacji. Nie pobrać i zainstalować wszystkie pliki binarne.<br /><br /> -                              **FALSE**. Wykonanie kwerendy i instalować wymagane aktualizacje. Pobierz i zainstaluj pliki binarne.|  

> [!NOTE]
>  W przypadku **UpdateCommand** wymaga co najmniej jedną opcję.  

> [!NOTE]
>  Jeśli Określanie obie opcje **UpdateCommand**, muszą być rozdzielane przy *i*.  

> [!NOTE]
>  Wartość domyślna dla **UpdateCommand** jest **IsInstalled = 0** i **IsHidden = 0**.  

> [!NOTE]
>  Aby uzyskać więcej informacji na temat **UpdateCommand**, zobacz [metody IUpdateSearcher::Search](http://msdn.microsoft.com/library/aa386526\(VS.85\).aspx).  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**Architektura**|-||  
|**DoCapture**|-||  
|**InstalledUpdates**||-|  
|**MSIT_WU_Count**|-|-|  
|**NoAutoUpdate_Previous**|-|-|  
|**Zmienna SMSTSRebootRequested**|-|-|  
|**SMSTSRetryRequested**|-|-|  
|**WSUSServer**|-||  
|**WUMU_ExcludeID**|-||  
|**WUMU_ExcludeKB**|-||  

###  <a name="ZTIWipeDisk.wsf"></a>ZTIWipeDisk.wsf  
 Ten skrypt sformatuje dysk twardy na komputerze docelowym. Skrypt:  

-   Kończy działanie, jeśli **narzędzia WipeDisk** nie jest równa **TRUE**  

-   Określa odpowiedni dysk do formatowania  

-   Formatuje dysk wywołując `cmd /c format <Drive> /fs:ntfs /p:3 /Y` (gdzie `<Drive>` to litera dysku twardego do sformatowania)  

|**Wartość**|**Opis**|  
|-|-|
|**Dane wejściowe**|**Zmienne środowiskowe**. Zawiera wartości właściwości, wartości właściwości niestandardowej, połączenia z bazą danych, reguły wdrażania i inne informacje, że skrypty wymagane do ukończeniu procesu wdrażania|  
|**Dane wyjściowe**|-                          **ZTIWipeDisk.log**. Plik dziennika zawierający zdarzenia, które generuje ten skrypt<br /><br /> -                          **BDD.log**. Plik dziennika zawierający zdarzenia, które generują wszystkie skrypty zestawu MDT|  
|**Odwołania**|-                          **CMD.exe**. Umożliwia uruchamianie narzędzia wiersza polecenia<br /><br /> -                          **Format.com**. Sformatuje dysk twardy<br /><br /> -                          **ZTIUtility.vbs**. Obejmuje funkcje pomocy technicznej i procedur, używane przez skrypt|  
|**Lokalizacja**|*dystrybucji*\Scripts|  
|**Użycie**|`cscript ZTIWipeDisk.wsf </debug:value>`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ debug: * wartość***|Wyświetla komunikaty dotyczące zdarzeń do konsoli i w plikach log. W przypadku wartości określonej w wartości:<br /><br /> -                              **Wartość TRUE,**, komunikaty o zdarzeniach są wysyłane do konsoli i pliki .log<br /><br /> -                              **FALSE**, komunikaty o zdarzeniach są wysyłane tylko do plików log (jest to zachowanie, gdy nie podano argumentu).|  

#### <a name="properties"></a>Właściwości  

|**Nazwa**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**Narzędzia WipeDisk**|-||  

##  <a name="SupportFiles"></a>Pliki obsługi  
 Narzędzia i skrypty używać we wdrożeniach LTI i ZTI plików konfiguracji zewnętrznych odwołań do określenia kroki tej procedury i ustawienia konfiguracji używane podczas procesu wdrażania.  

 Poniższe informacje są przeznaczone dla każdego narzędzia:  

-   **Nazwa**. Określa nazwę pliku  

-   **Opis elementu**. Zawiera opis przeznaczenia pliku  

-   **Lokalizacja**. Wskazuje folder, w którym można znaleźć pliku; w informacjach o lokalizacji są używane następujące zmienne:  

    -   **Program_Files**. Ta zmienna wskazuje lokalizację, w folderze Program Files na komputerze, w którym jest zainstalowany zestaw MDT.  

    -   **dystrybucji**. Ta zmienna wskazuje lokalizację folderu dystrybucji dla udziału wdrożenia.  

    -   **Platforma**. Ta zmienna jest symbolem zastępczym dla platformy systemu operacyjnego (x86 lub x64).  

###  <a name="ApplicationGroups.xml"></a>ApplicationGroups.xml  

> [!NOTE]
>  Ten plik XML jest zarządzana przez zestaw MDT i nie powinny wymagać modyfikacji.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|*dystrybucji*\Control|  

###  <a name="Applications.xml"></a>Applications.XML  

> [!NOTE]
>  Ten plik XML jest zarządzana przez zestaw MDT i nie powinny wymagać modyfikacji.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|*dystrybucji*\Control|  

###  <a name="BootStrap.ini"></a>BootStrap.ini  
 Używany, gdy komputer docelowy nie jest w stanie nawiązać połączenia z udziałem wdrożenia odpowiednie pliku konfiguracji. Ta sytuacja występuje w nowym komputerze i scenariusze Zastąp komputera.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|*dystrybucji*\Control|  

###  <a name="CustomSettings.ini"></a>CustomSettings.ini  
 Plik konfiguracji podstawowej dla zestawu MDT, przetwarzania reguły używane we wszystkich scenariuszach.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|*dystrybucji*\Control|  

###  <a name="Deploy.xml"></a>Deploy.XML  

> [!NOTE]
>  Ten plik XML jest zarządzana przez zestaw MDT i nie powinny wymagać modyfikacji.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|*Program_Files*\Microsoft Deployment Toolkit\Control|  

###  <a name="DriverGroups.xml"></a>DriverGroups.xml  

> [!NOTE]
>  Ten plik XML jest zarządzana przez zestaw MDT i nie powinny wymagać modyfikacji.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|*dystrybucji*\Control|  

###  <a name="Drivers.xml"></a>Drivers.XML  

> [!NOTE]
>  Ten plik XML jest zarządzana przez zestaw MDT i nie powinny wymagać modyfikacji.  

|**Wartość**|Opis|  
|-|-|  
|**Lokalizacja**|*dystrybucji*\Control|  

###  <a name="LinkedDeploymentShares.xml"></a>LinkedDeploymentShares.xml  

> [!NOTE]
>  Ten plik XML jest zarządzana przez zestaw MDT i nie powinny wymagać modyfikacji.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|*dystrybucji*\Scripts|  

###  <a name="ListOfLanguages.xml"></a>ListOfLanguages.xml  

> [!NOTE]
>  Ten plik XML jest zarządzana przez zestaw MDT i nie powinny wymagać modyfikacji.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|*dystrybucji*\Scripts|  

###  <a name="MediaGroups.xml"></a>MediaGroups.xml  

> [!NOTE]
>  Ten plik XML jest zarządzana przez zestaw MDT i nie powinny wymagać modyfikacji.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|*dystrybucji*\Scripts|  

###  <a name="Medias.xml"></a>Medias.XML  

> [!NOTE]
>  Ten plik XML jest zarządzana przez zestaw MDT i nie powinny wymagać modyfikacji.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|*dystrybucji*\Scripts|  

###  <a name="OperatingSystemGroups.xml"></a>OperatingSystemGroups.xml  

> [!NOTE]
>  Ten plik XML jest zarządzana przez zestaw MDT i nie powinny wymagać modyfikacji.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|*dystrybucji*\Control|  

###  <a name="OperatingSystems.xml"></a>OperatingSystems.xml  

> [!NOTE]
>  Ten plik XML jest zarządzana przez zestaw MDT i nie powinny wymagać modyfikacji.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|*dystrybucji*\Control|  

###  <a name="PackageGroups.xml"></a>PackageGroups.xml  

> [!NOTE]
>  Ten plik XML jest zarządzana przez zestaw MDT i nie powinny wymagać modyfikacji.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|*dystrybucji*\Control|  

###  <a name="Packages.xml"></a>Packages.XML  

> [!NOTE]
>  Ten plik XML jest zarządzana przez zestaw MDT i nie powinny wymagać modyfikacji.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|*dystrybucji*\Control|  

###  <a name="SelectionProfileGroups.xml"></a>SelectionProfileGroups.xml  

> [!NOTE]
>  Ten plik XML jest zarządzana przez zestaw MDT i nie powinny wymagać modyfikacji.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|*dystrybucji*\Control|  

###  <a name="SelectionProfiles.xml"></a>SelectionProfiles.xml  

> [!NOTE]
>  Ten plik XML jest zarządzana przez zestaw MDT i nie powinny wymagać modyfikacji.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|*dystrybucji*\Control|  

###  <a name="ServerManager.xml"></a>ServerManager.xml  

> [!NOTE]
>  Ten plik XML jest zarządzana przez zestaw MDT i nie powinny wymagać modyfikacji.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|*Program_Files*\Microsoft Deployment Toolkit\Bin|  

###  <a name="Settings.xml"></a>Settings.XML  

> [!NOTE]
>  Ten plik XML jest zarządzana przez zestaw MDT i nie powinny wymagać modyfikacji.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|*dystrybucji*\Control|  

###  <a name="TaskSequenceGroups.xml"></a>TaskSequenceGroups.xml  

> [!NOTE]
>  Ten plik XML jest zarządzana przez zestaw MDT i nie powinny wymagać modyfikacji.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|*dystrybucji*\Control|  

###  <a name="TaskSequences.xml"></a>TaskSequences.xml  

> [!NOTE]
>  Ten plik XML jest zarządzana przez zestaw MDT i nie powinny wymagać modyfikacji.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|*dystrybucji*\Control|  

###  <a name="TS.xml"></a>TS.xml  

> [!NOTE]
>  Ten plik XML jest zarządzana przez zestaw MDT i nie powinny wymagać modyfikacji.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|*dystrybucji*\Control\\*task_sequence_id*|  

> [!NOTE]
>  *Task_sequence_id* to symbol zastępczy identyfikator sekwencji zadań, która została przypisana do poszczególnych sekwencji zadań, jeśli został on utworzony w węźle sekwencje zadań w konsoli Deployment Workbench.  

###  <a name="Wimscript.ini"></a>Wimscript.ini  
 Ten plik .ini jest pliku konfiguracyjnego narzędzia ImageX, który zawiera listy folderów i plików, które będą wykluczone z obrazu. Odwołuje się do narzędzia ImageX w fazie przechwytywania LTI.  

 Aby uzyskać pomoc dotyczącą dostosowywania tego pliku, zobacz sekcję "Tworzenie pliku konfiguracyjnego narzędzia ImageX," w *Podręcznik użytkownika środowiska preinstalacji systemu Windows (Windows PE)*.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|*dystrybucji*\Tools\\*platformy*|  

###  <a name="ZTIBIOSCheck.xml"></a>ZTIBIOSCheck.xml  
 Ten plik XML zawierający metadane dotyczące BIOS dla komputerów docelowych. Ten plik jest ręcznie edytować i jest odczytywany przez [ZTIBIOSCheck.wsf](#ZTIBIOSCheck.wsf). Wyodrębnij niezbędne informacje z komputera docelowego, aby utworzyć wpis w pliku XML przy użyciu programu Microsoft Visual Basic® Scripting Edition (VBScript) (ZTIBIOS_Extract_Utility.vbs), który jest osadzony w tym pliku XML.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|*dystrybucji*\Scripts|  

###  <a name="ZTIConfigure.xml"></a>ZTIConfigure.xml  
 Ten plik XML jest używany przez [ZTIConfigure.wsf](#ZTIConfigure.wsf) skryptu tłumaczenie wartości właściwości (określone wcześniej w procesie wdrażania), aby skonfigurować ustawienia w pliku Unattend.xml. Ten plik jest już dostosować, aby wprowadzić odpowiednie tłumaczenia i nie powinny wymagać dalszej modyfikacji.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|*dystrybucji*\Scripts|  

###  <a name="ZTIGather.xml"></a>ZTIGather.xml  

> [!NOTE]
>  Ten plik XML jest wstępnie skonfigurowana i nie powinny wymagać modyfikacji. Definiowanie właściwości niestandardowe w pliku CustomSettings.ini lub DB zestawu MDT.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|*dystrybucji*\Scripts|  

###  <a name="ZTIUserState_config.xml"></a>ZTIUserState_config.xml  
 Ten plik XML jest używany przez [ZTIUserState.wsf](#ZTIUserState.wsf) skrypt jako domyślny plik konfiguracji narzędzia USMT. Ten plik jest używany domyślnie, jeśli nie określono żadnych pliku konfiguracji niestandardowej przez [USMTConfigFile](#USMTConfigFile) właściwości. Zobacz [pliku Config.xml](http://technet.microsoft.com/library/dd560760.aspx) tematu w dokumentacji narzędzia USMT, aby uzyskać więcej informacji na temat składni i użycia.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|*dystrybucji*\Scripts|  

###  <a name="ZTITatoo.mof"></a>ZTITatoo.mof  
 Ten plik MOF podczas importowania do repozytorium WMI na komputerze docelowym przy użyciu Mofcomp.exe, tworzy **Microsoft_BDD_Info** klasy usługi WMI. Ta klasa zawiera informacje dotyczące wdrażania, takie jak:  

-   DeploymentMethod  

-   deploymentType  

-   DeploymentTimestamp  

-   Identyfikatora BuildID  

-   BuildName  

-   BuildVersion  

-   OSDPackageID  

-   OSDProgramName  

-   OSDAdvertisementID  

-   TaskSequenceID  

-   TaskSequenceName  

-   TaskSequenceVersion  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|*dystrybucji*\Scripts|  

## <a name="utilities"></a>Narzędzia  
 Skrypty używane w LTI i ZTI odwołanie narzędzi służących do wykonywania zadań specjalne obsługi krokami podczas procesu wdrażania. Skorzystaj z poniższych informacji w celu określenia poprawnych narzędzi do uwzględnienia w działaniach i nieprawidłowe argumenty podczas każdego narzędzia.  

 Poniższe informacje są przeznaczone dla każdego narzędzia:  

-   **Nazwa**. Określa nazwę narzędzia  

-   **Opis elementu**. Zawiera opis przeznaczenia narzędzia  

-   **Lokalizacja**. Wskazuje folder, w którym znajduje się narzędzie; w informacjach o lokalizacji są używane następujące zmienne:  

    -   **Program_Files**. Ta zmienna wskazuje lokalizację, w folderze Program Files na komputerze, w którym jest zainstalowany zestaw MDT.  

    -   **dystrybucji**. Ta zmienna wskazuje lokalizację folderu dystrybucji dla udziału wdrożenia.  

    -   **Platforma**. Ta zmienna jest symbolem zastępczym dla platformy systemu operacyjnego (x86 lub x64).  

-   **Użyj**. Udostępnia polecenia i opcje, które można określić  

-   **Argumenty i opis**. Wskazuje nieprawidłowe argumenty dla narzędzia i krótki opis oznacza każdy argument  

###  <a name="BCDBoot.exe"></a>BCDBoot.exe  
 Jest ono narzędzie służące do szybko skonfigurować partycję systemową lub napraw środowisko rozruchowe znajduje się na partycji systemowej. Na partycji systemowej skonfigurowano przez skopiowanie niewielki zestaw plików środowiska rozruchowego z zainstalowanego obrazu systemu Windows. BCDBoot również tworzy magazyn danych konfiguracji rozruchu (BCD) na partycji systemowej nowy wpis rozruchu, to rozruch zainstalowanego obrazu systemu Windows w systemie Windows.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|Uwzględnione w plikach źródłowych z systemem Windows|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
||Zobacz Pomoc wiersza polecenia udostępniane przez to narzędzie.|  

###  <a name="BDDRun.exe"></a>BDDRun.exe  
 To narzędzie jest uruchamiane jako akcja przez sekwenser zadań dla plików wykonywalnych (na przykład skrypt lub inny kod), które wymagają interakcji użytkownika. Domyślnie sekwencja zadań nie można uruchomić pliku wykonywalnego, który wymaga interakcji użytkownika. To narzędzie umożliwia jednak programowi sekwencjonowania zadań uruchomić plik wykonywalny, który wymaga interakcji użytkownika.  

 Jako argument to narzędzie znajduje się plik wykonywalny, który wymaga interakcji użytkownika. To narzędzie uruchamia plik wykonywalny w środowisku osobne polecenie.  

> [!NOTE]
>  To narzędzie można używać tylko we wdrożeniach LTI. Wdrożenia ZTI uniemożliwiają interakcji z użytkownikiem.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|*dystrybucji*\Tools\\*platformy*|  
|**Użycie**|`BDDRun.exe commandline`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|*Wiersz polecenia*|Polecenie można uruchomić, która wymaga interakcji z użytkownikiem|  

> [!NOTE]
>  Podwójne cudzysłowy dowolną część *wiersza polecenia* część argumentu, który zawiera puste wartości. Na przykład: `BDDRun.exe MyAppInstall.exe /destinationdir: "%ProgramFiles%\AppName"`.  

###  <a name="Bootsect.exe"></a>Bootsect.exe  
 Bootsect.exe aktualizuje główny kod rozruchowy dla partycji dysku twardego w celu przełączania się między BOOTMGR lub NTLDR. Użyj tego narzędzia do przywrócenia sektora rozruchowego na komputerze.  

 Aby uzyskać więcej informacji dotyczących Bootsect.exe, zobacz sekcję "Opcje wiersza polecenia narzędzia Bootsect" w *Podręcznik użytkownika środowiska preinstalacji systemu Windows (Windows PE)*.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|*dystrybucji*\Tools\\*platformy*|  
|**Użycie**|`bootsect.exe /nt52 C:`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/ Help**|Wyświetla Użyj instrukcje przedstawione w tym miejscu.|  
|**/ nt52**|Stosuje główny kod rozruchowy zgodny z modułem NTLDR do **SYS**, **wszystkie**, lub *litera dysku*. System operacyjny zainstalowany na **SYS**, **wszystkie**, lub *litera dysku* musi być wcześniejszej wersji systemu Windows Vista.|  
|**/ NT60**|Stosuje główny kod rozruchowy zgodny z BOOTMGR do **SYS**, **wszystkie**, lub *litera dysku*. System operacyjny zainstalowany na **SYS**, **wszystkie**, lub *litera dysku* musi być system Windows Vista.|  
|**SYS**|Aktualizuje główny kod rozruchowy na partycji systemowej używany do rozruchu systemu Windows.|  
|**Wszystkie**|Aktualizuje główny kod rozruchowy na wszystkich partycji. **WSZYSTKIE** nie musi aktualizować kodu rozruchowego dla każdego woluminu. Zamiast tego ta opcja aktualizuje kod rozruchowy w woluminach, które mogą być używane jako woluminy rozruchowe systemu Windows, co wyklucza woluminy dynamiczne nie są połączone z partycją dysku. To ograniczenie istnieje, ponieważ kod musi znajdować się na początku partycji dysku.|  
|***Litera dysku***|Aktualizuje główny kod rozruchowy na woluminie skojarzonym z tę literę dysku. Kod nie zostanie zaktualizowany, jeśli dowolny (1) **litera dysku** nie jest skojarzony z woluminu lub (2) **litera dysku** jest skojarzony z woluminem, który nie jest podłączony do podstawowej partycji dysku.|  
|**/ Force**|Wymusza odinstalowywanie woluminów podczas aktualizacji kodu rozruchowego. Użyj tej opcji z rozwagą.|  

###  <a name="Compact.exe"></a>Compact.exe  
 Wyświetla lub zmienia kompresję pliki na partycji systemu plików NTFS.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|Uwzględnione w plikach źródłowych z systemem Windows|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**/C**|Kompresuje określonych plików. Tak, aby pliki dodane później zostanie skompresowany, zostaną oznaczone katalogów.|  
|**/V**|Dekompresuje określonych plików. Tak, aby pliki dodane później nie zostanie skompresowany, zostaną oznaczone katalogów.|  
|**/ S**|W podanym katalogu i wszystkie podkatalogi, wykonuje podanej operacji na plikach. Domyślny katalog jest to katalog bieżący.|  
|**/A**|Wyświetla pliki z ukrytego lub atrybutów systemowych. Pliki te są pomijane domyślnie.|  
|**/I**|Kontynuuje wykonywanie określonej operacji nawet po wystąpieniu błędów. Domyślnie Compact.exe zatrzymywana, gdy wystąpi błąd.|  
|**/F**|Wymusza wykonanie operacji kompresji dla wszystkich określonych plików, nawet te, które są już skompresowane. Już skompresowane pliki są pomijane domyślnie.|  
|**/Q**|Raporty tylko najważniejsze informacje.|  
|***Nazwa pliku***|Określa wzorzec, plik lub katalog.|  

###  <a name="Diskpart.exe"></a>DiskPart.exe  
 Narzędzia DiskPart jest interpreter poleceń tekstowej, który umożliwia zarządzanie obiektami (dyski, partycje lub woluminy) przy użyciu skryptów lub wprowadzania bezpośredniego w oknie wiersza polecenia.  

 Aby uzyskać więcej informacji dotyczących Diskpart.exe, zobacz sekcję "Opcje wiersza polecenia Diskpart" w *Podręcznik użytkownika środowiska preinstalacji systemu Windows (Windows PE)*.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|Uwzględnione w plikach źródłowych środowiska Preinstalacyjnego systemu Windows|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
||Można znaleźć w przewodniku, do którego odwołuje się opis narzędzia.|  

###  <a name="Expand.exe"></a>Expand.exe  
 To narzędzie jest uruchamiane rozszerzenia plików (extract) z skompresowane pliki.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|Uwzględnione w plikach źródłowych z systemem Windows|  
|**Użycie**|`Expand.exe -r wuredist.cab -F:wuRedist.xml %temp%`|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|**-r**|Zmienia nazwę rozwinięty plików|  
|**-D**|Wyświetla listę plików w katalogu źródłowym|  
|***Obiekt źródłowy***|Specyfikacja pliku źródła (można używać symboli wieloznacznych).|  
|**-F: * plików***|Nazwy plików, aby rozwinąć z pliku cab|  
|***Miejsce docelowe***|Plik docelowy &#124; Ścieżka (**docelowego** może być katalogiem. Jeśli **źródła** jest wiele plików i **- r** nie zostanie określony, **docelowego** musi być katalogiem.)|  

###  <a name="ImageX.exe"></a>ImageX.exe  
 ImageX to narzędzie wiersza polecenia, które umożliwia OEM i firmom przechwytywania, modyfikowania i stosowania obrazów dysku opartych na plikach do szybkiego wdrażania usługi. Narzędzia ImageX z plików WIM kopiowania do sieci, oraz może współpracować z innymi technologiami, które używają obrazy WIM, takie jak Instalatora systemu Windows i usługi wdrażania systemu Windows.  

 Aby uzyskać więcej informacji na temat narzędzia ImageX, zobacz sekcję "Co to jest ImageX" w *Podręcznik użytkownika środowiska preinstalacji systemu Windows (Windows PE)*.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|*dystrybucji*\Tools\\*platformy*|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
||Można znaleźć w przewodniku, do którego odwołuje się opis narzędzia.|  

###  <a name="Microsoft.BDD.PnpEnum.exe"></a>Microsoft.BDD.PnpEnum.exe  
 To narzędzie jest uruchamiane wyliczyć urządzeń Plug and Play zainstalowany na komputerze docelowym.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|*dystrybucji*\Tools\\*platformy*|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|Brak|—|  

###  <a name="Mofcomp.exe"></a>Mofcomp.exe  
 Mofcomp.exe jest kompilatora Managed Object Format, która analizuje plik, który zawiera instrukcje Managed Object Format i dodaje klas i wystąpień klas zdefiniowanych w pliku do repozytorium WMI. Mofcomp.exe stanowi pomoc w wierszu polecenia na przełączniku używa opcji.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|Uwzględnione w plikach źródłowych z systemem Windows|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
||Zobacz Pomoc wiersza polecenia, która zapewnia to narzędzie.|  

###  <a name="Netsh.exe"></a>Netsh.exe  
 Netsh.exe to narzędzie wiersza polecenia i skryptów do zautomatyzowania konfiguracji składników sieciowych. Aby uzyskać więcej informacji na temat Netsh.exe, zobacz [narzędzie wiersza polecenia Netsh](http://technet.microsoft.com/library/cc785383%28WS.10%29.aspx).  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|Uwzględnione w plikach źródłowych z systemem Windows|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
||Zobacz Pomoc wiersza polecenia, który to narzędzie oferuje lub informacje znajdujące się pod adresem URL na liście opis narzędzia.|  

###  <a name="Reg.exe"></a>Reg.exe  
 Narzędzie rejestru konsoli jest używane do odczytu i modyfikowania danych rejestru.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|Uwzględnione w plikach źródłowych z systemem Windows|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
||Zobacz Pomoc wiersza polecenia, która zapewnia to narzędzie.|  

###  <a name="Regsvr32.exe"></a>Regsvr32.exe  
 To narzędzie służy do rejestrowania w systemie operacyjnym (.dll, .exe, .ocx i tak dalej).  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|Uwzględnione w plikach źródłowych z systemem Windows|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
|***plik***|Nazwa pliku do zarejestrowania lub wyrejestrowania|  
|**/ s**|Uruchamia narzędzie w trybie dyskretnym|  
|**/u**|Wyrejestrowuje pliku|  

###  <a name="Wpeutil.exe"></a>Wpeutil.exe  
 Narzędzia systemu Windows PE (Wpeutil) jest narzędziem wiersza polecenia, z którym różne polecenia mogą być uruchamiane w sesji środowiska Windows PE. Na przykład administrator może zamknąć lub ponowny rozruch środowiska Preinstalacyjnego systemu Windows, aktywować lub dezaktywować zapory, skonfigurować ustawienia języka i zainicjuj sieci. Zestaw MDT używa narzędzie do inicjowania środowiska Windows PE i połączeń sieciowych i uruchamiania wdrożenia LTI.  

 Aby uzyskać więcej informacji o Wpeutil.exe, zobacz sekcję "Wpeutil" Opcje wiersza polecenia, w *Podręcznik użytkownika środowiska preinstalacji systemu Windows (Windows PE)*.  

|**Wartość**|**Opis**|  
|-|-|
|**Lokalizacja**|Uwzględnione w plikach źródłowych środowiska Preinstalacyjnego systemu Windows|  

#### <a name="arguments"></a>Argumenty  

|**Wartość**|**Opis**|  
|-|-|
||Można znaleźć w przewodniku, do którego odwołuje się opis narzędzia.|  

## <a name="mdt-windows-powershell-cmdlets"></a>Polecenia cmdlet programu PowerShell systemu Windows zestawu MDT  
 Oprócz konsoli Deployment Workbench udział wdrożenia zestawu MDT można zarządzać za pomocą poleceń cmdlet programu Windows PowerShell. Zestaw MDT środowiska Windows PowerShell polecenia cmdlet zostaną uwzględnione w przystawce in—Microsoft.BDD.PSSnapIn—which środowiska Windows PowerShell jest dołączana do instalacji zestawu MDT.  

 Polecenia cmdlet MDT należy uruchomić z konsoli środowiska Windows PowerShell, która ma środowiska Windows PowerShell dla zestawu MDT przystawki załadowany. Aby uzyskać więcej informacji na temat sposobu uruchamiania konsoli programu Windows PowerShell, która ma przystawkę programu Windows PowerShell dla zestawu MDT załadowane, zobacz "podczas ładowania zestawu MDT Windows PowerShell przystawki".  

 Tabela 7 zawiera listę poleceń cmdlet programu Windows PowerShell dla zestawu MDT i zawiera krótki opis każdego polecenia cmdlet. Każde polecenie cmdlet jest szczegółowo omówione w kolejnej sekcji.  

### <a name="table-7-mdt-windows-powershell-cmdlets"></a>Tabela 7. Polecenia cmdlet programu PowerShell systemu Windows zestawu MDT  

|**Polecenia cmdlet**|**Opis**|  
|-|-|  
|[Dodaj MDTPersistentDrive](#Add-MDTPersistentDrive)|Dodaje udział wdrożenia do listy zestawu MDT utrwalone dyski, które można przywrócić przy użyciu [MDTPersistentDrive przywracania](#Restore-MDTPersistentDrive) polecenia cmdlet.|  
|[Wyłącz MDTMonitorService](#Disable-MDTMonitorService)|Wyłącza monitorowanie usług zestaw MDT.|  
|[Włącz MDTMonitorService](#Enable-MDTMonitorService)|Umożliwia monitorowanie usług zestaw MDT.|  
|[Get-MDTDeploymentShareStatistics](#Get-MDTDeploymentShareStatistics)|Wyświetla statystyki dotyczące udziału wdrożenia, w tym liczba jednostek na głównych folder udziału wdrożenia.|  
|[Get-MDTMonitorData](#Get-MDTMonitorData)|Wyświetla zestaw MDT monitorowania zebrane dane co najmniej jednego monitorowanych MTD wdrożenia.|  
|[Get-MDTOperatingSystemCatalog](#Get-MDTOperatingSystemCatalog)|Zwraca katalogu systemu operacyjnego dla określonego systemu operacyjnego. Jeśli wykaz systemu operacyjnego nie istnieje lub jest nieaktualny, a następnie ponownego wygenerowania katalogu systemu operacyjnego.|  
|[Get-MDTPersistentDrive](#Get-MDTPersistentDrive)|Wyświetla listę udziałów wdrożenia, które można przywrócić przy użyciu [MDTPersistentDrive przywracania](#Restore-MDTPersistentDrive) polecenia cmdlet.|  
|[MDTApplication importu](#Import-MDTApplication)|Importuje aplikację do udziału wdrożenia.|  
|[MDTDriver importu](#Import-MDTDriver)|Importuje co najmniej jednego sterownika urządzenia do udziału wdrożenia.|  
|[MDTOperatingSystem importu](#Import-MDTOperatingSystem)|Importuje jednego lub kilku systemów operacyjnych do udziału wdrożenia.|  
|[MDTPackage importu](#Import-MDTPackage)|Importuje jeden lub więcej pakietów systemu operacyjnego do udziału wdrożenia.|  
|[MDTTaskSequence importu](#Import-MDTTaskSequence)|Importuje sekwencję zadań do udziału wdrożenia.|  
|[Nowe MDTDatabase](#New-MDTDatabase)|Tworzy lub uaktualnienie bazy danych MDT DB skojarzonego z udziałem wdrożenia.|  
|[Usuń MDTMonitorData](#Remove-MDTMonitorData)|Usuwa co najmniej jeden zestaw MDT monitorowania elementów danych z zebranych danych w udziale wdrażania monitorowania zestaw MDT.|  
|[Usuń MDTPersistentDrive](#Remove-MDTPersistentDrive)|Usuwa udział wdrożenia z listy zestawu MDT utrwalone dyski środowiska Windows PowerShell, które można przywrócić przy użyciu [MDTPersistentDrive przywracania](#Restore-MDTPersistentDrive) polecenia cmdlet.|  
|[Przywracanie MDTPersistentDrive](#Restore-MDTPersistentDrive)|Tworzy dysk programu Windows PowerShell dla każdego udziału wdrożenia zestawu mdt na liście trwałych dyski środowiska Windows PowerShell.|  
|[Zestaw MDTMonitorData](#Set-MDTMonitorData)|Tworzy nowy lub aktualizuje istniejący zestaw MDT monitorowania element danych w zebranych danych monitorowania zestawu MDT w udziału wdrożenia.|  
|[MDTDeploymentShare testu](#Test-MDTDeploymentShare)|Weryfikacja integralności udziału wdrożenia.|  
|[MDTMonitorData testu](#Test-MDTMonitorData)|Sprawdza, czy zestaw MDT monitorowanie usług jest poprawnie skonfigurowane i uruchomione.|  
|[MDTDatabaseSchema aktualizacji](#Update-MDTDatabaseSchema)|Aktualizacje schematu bazy danych DB zestawu MDT.|  
|[MDTDeploymentShare aktualizacji](#Update-MDTDeploymentShare)|Aktualizuje udziału wdrożenia.|  
|[MDTLinkedDS aktualizacji](#Update-MDTLinkedDS)|Replikuje zawartość z udziału wdrożenia do udziału wdrożenia połączony.|  
|[MDTMedia aktualizacji](#Update-MDTMedia)|Replikuje zawartość z udziału wdrożenia do folderu wdrożenia nośnika.|  

###  <a name="Add-MDTPersistentDrive"></a>Dodaj MDTPersistentDrive  
 W tej sekcji opisano **programu PowerShell Dodaj MDTPersistentDriveWindows** polecenia cmdlet. Uruchom to polecenie cmdlet z konsoli programu Windows PowerShell, która ma PowerShell zestawu MDT przystawki załadowany. Aby uzyskać więcej informacji na temat sposobu uruchamiania konsoli programu Windows PowerShell, która ma przystawki programu PowerShell zestawu MDT załadowane, zobacz "podczas ładowania zestawu MDT Windows PowerShell przystawki".  

#### <a name="syntax"></a>Składnia  

```  
Add-MDTPersistentDrive [-Name] <String> [[-InputObject] <PSObject>] [<CommonParameters>]  
```  

#### <a name="description"></a>Opis  
 To polecenie cmdlet dodaje istniejący dysk utworzony przy użyciu programu Windows PowerShell **MDTProvider** na listę dysków, które są trwałe w konsoli Deployment Workbench lub w sesji środowiska Windows PowerShell przy użyciu [ Przywracanie MDTPersistentDrive](#Restore-MDTPersistentDrive) polecenia cmdlet. To polecenie cmdlet jest wywoływana podczas tworzenia lub otwierania udziału wdrożenia w konsoli Deployment Workbench.  

> [!NOTE]
>  Utrwalona, wykaz **MDTProvider** dysków jest przechowywana na użytkownika na podstawie w profilu użytkownika.  

 Utrwalona, wykaz **MDTProvider** dyski są wyświetlane przy użyciu **Get-MDTPersistentDrive** polecenia cmdlet.  

#### <a name="parameters"></a>Parametry  
 Ta podsekcja zawiera informacje o różnych parametrów, które mogą być używane z **MDTPersistentDriveWindows Dodaj** polecenia cmdlet.  

##### <a name="-name-string"></a>-Nazwa < ciąg\>  
 Określa nazwę dysk programu Windows PowerShell utworzone przy użyciu dostawcy zestawu MDT i odnosi się do istniejącego udziału wdrożenia. Nazwa została utworzona przy użyciu [elementu PSDrive nowy](http://technet.microsoft.com/library/dd315340.aspx) polecenia cmdlet i określając **MDTProvider** w *PSProvider* parametru.  

 Aby uzyskać więcej informacji na temat sposobu tworzenia nowego środowiska Windows PowerShell dysków przy użyciu **MDTProvider** i sposobu tworzenia wdrożenia udostępnić przy użyciu programu Windows PowerShell, zobacz sekcję "Tworzenie wdrożenia udostępniać za pomocą środowiska Windows PowerShell" w Dokument MDT *Microsoft Deployment Toolkit przykłady Guide*.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość true**|  
|**Pozycja?**|**2** i **o nazwie**|  
|**Wartość domyślna**|Brak|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość true,** (**ByValue**)|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-inputobject-psobject"></a>-InputObject < PSObject\>  
 Ten parametr określa obiekt dysk programu Windows PowerShell, który został utworzony wcześniej w procesie. Wprowadź obiekt PSObject, taki jak generowane przez [elementu PSDrive nowy](http://technet.microsoft.com/library/dd315340.aspx) polecenia cmdlet.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**3** i **o nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość true,** (**ByValue**)|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 To polecenie cmdlet obsługuje następujące typowe parametry: *Verbose, Debug, ErrorAction, ErrorVariable, OutBuffer OutVariable, WarningAction* i *WarningVariable.* Aby uzyskać więcej informacji zobacz temat "about_CommonParameters", które można otworzyć, wpisując następujące polecenie, a następnie naciskając klawisz ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>dane wyjściowe  
 To polecenie cmdlet wyświetla **PSObject** typ obiektu dla obiekt dysk programu Windows PowerShell został dodany do listy utrwalonego dysków.  

 Również danych wyjściowych tego polecenia cmdlet **ciąg** typu object, jeśli *pełne* wspólnego parametru jest dołączony.  

#### <a name="example-1"></a>Przykład 1  

```  
Add-MDTPersistentDrive –Name DS001  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie dodaje udziału wdrożenia o nazwie dysk programu Windows PowerShell *DS001* do listy utrwalonego dysków.  

#### <a name="example-2"></a>Przykład 2  

```  
$MDTPSDrive = New-PSDrive -Name "DS001" -PSProvider "MDTProvider" –Root "C:\DeploymentShare$" -Description "MDT Deployment Share" -NetworkPath \\WDG-MDT-01\DeploymentShare$ -Verbose  
Add-MDTPersistentDrive –InputObject $MDTPSDrive  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie dodaje nazwę dysk programu Windows PowerShell *DS001,* utworzone przez [elementu PSDrive nowy](http://technet.microsoft.com/library/dd315340.aspx) polecenia cmdlet do listy utrwalonego MDT dyski za pomocą *$MDTPSDrive* zmiennej.  

#### <a name="example-3"></a>Przykład 3  

```  
New-PSDrive -Name "DS001" -PSProvider "MDTProvider" –Root "C:\DeploymentShare$" -Description "MDT Deployment Share" -NetworkPath \\WDG-MDT-01\DeploymentShare$ -Verbose | Add-MDTPersistentDrive –Verbose  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie dodaje nazwę dysk programu Windows PowerShell *DS001,* utworzone przez [elementu PSDrive nowy](http://technet.microsoft.com/library/dd315340.aspx) polecenia cmdlet do listy utrwalonego MDT dyski przez przekazanie w potoku nowo utworzony obiekt dysk programu Windows PowerShell do  **Dodaj MDTPersistentDrive** polecenia cmdlet.  

###  <a name="Disable-MDTMonitorService"></a>Wyłącz MDTMonitorService  
 W tej sekcji opisano **MDTMonitorService Wyłącz** polecenia cmdlet programu Windows PowerShell. Uruchom to polecenie cmdlet z konsoli programu Windows PowerShell, która ma PowerShell zestawu MDT przystawki załadowany. Aby uzyskać więcej informacji na temat sposobu uruchamiania konsoli programu Windows PowerShell, która ma przystawki programu PowerShell zestawu MDT załadowane, zobacz "podczas ładowania zestawu MDT Windows PowerShell przystawki".  

#### <a name="syntax"></a>Składnia  

```  
Disable-MDTMonitorService [<CommonParameters>]  
```  

#### <a name="description"></a>Opis  
 To polecenie cmdlet powoduje wyłączenie monitorowania usługi, które działają na komputerze, w którym jest zainstalowany zestaw MDT zestaw MDT. Zestaw MDT Usługa monitorowania zbiera informacje monitorowania, które mogą być wyświetlane:  

-   W węźle Monitorowanie w konsoli Deployment Workbench udział wdrożenia  

-   Przy użyciu [Get-MDTMonitorData](#Get-MDTMonitorData) polecenia cmdlet  

 Następnie można włączyć MDT monitorowanie usługi za pomocą [MDTMonitorService Włącz](#Enable-MDTMonitorService).  

 Aby uzyskać więcej informacji na temat zestaw MDT monitorowanie usługi, zobacz sekcję "Monitorowania wdrożenia zestawu MDT" w dokumencie MDT *przy użyciu programu Microsoft Deployment Toolkit*.  

#### <a name="parameters"></a>Parametry  
 Ta podsekcja zawiera informacje o różnych parametrów, które mogą być używane z **MDTMonitorService Wyłącz** polecenia cmdlet.  

##### <a name="commonparameters"></a>< CommonParameters\>  
 To polecenie cmdlet obsługuje następujące typowe parametry: *Verbose, Debug, ErrorAction, ErrorVariable, OutBuffer OutVariable, WarningAction* i *WarningVariable.* Aby uzyskać więcej informacji zobacz temat "about_CommonParameters," który można uzyskać dostępu do, wpisując następujące polecenie, a następnie naciskając klawisz ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>dane wyjściowe  
 To polecenie cmdlet wyświetla **ciąg** typu object, jeśli *pełne* wspólnego parametru jest uwzględnione; w przeciwnym razie generowane żadne dane wyjściowe.  

#### <a name="example-1"></a>Przykład 1  

```  
Disable-MDTMonitorService  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie powoduje wyłączenie MDT usługi monitorowania.  

###  <a name="Enable-MDTMonitorService"></a>Włącz MDTMonitorService  
 W tej sekcji opisano **MDTMonitorService Włącz** polecenia cmdlet programu Windows PowerShell. Uruchom to polecenie cmdlet z konsoli programu Windows PowerShell, która ma PowerShell zestawu MDT przystawki załadowany. Aby uzyskać więcej informacji na temat sposobu uruchamiania konsoli programu Windows PowerShell, która ma przystawki programu PowerShell zestawu MDT załadowane, zobacz "podczas ładowania zestawu MDT Windows PowerShell przystawki".  

#### <a name="syntax"></a>Składnia  

```  
Enable-MDTMonitorService [-EventPort] <Int32> [-DataPort] <Int32> [<CommonParameters>]  
```  

#### <a name="description"></a>Opis  
 To polecenie cmdlet umożliwia monitorowanie usługi, które działają na komputerze, w którym jest zainstalowany zestaw MDT zestaw MDT. Zestaw MDT Usługa monitorowania zbiera informacje monitorowania, które mogą być wyświetlane:  

-   W węźle Monitorowanie w udziale wdrażania w konsoli Deployment Workbench.  

-   Przy użyciu [Get-MDTMonitorData](#Get-MDTMonitorData) polecenia cmdlet  

 Zestaw MDT monitorowanie usługi można wyłączyć przy użyciu [MDTMonitorService Wyłącz](#Disable-MDTMonitorService).  

 Aby uzyskać więcej informacji na temat zestaw MDT monitorowanie usługi, zobacz sekcję "Monitorowania wdrożenia zestawu MDT" w dokumencie MDT *przy użyciu programu Microsoft Deployment Toolkit*.  

#### <a name="parameters"></a>Parametry  
 Ta podsekcja zawiera informacje o różnych parametrów, które mogą być używane z **MDTMonitorService Włącz** polecenia cmdlet.  

##### <a name="-eventport-int32"></a>-EventPort < Int32\>  
 Ten parametr określa TCP port używany jako port zdarzeń dla zestawu MDT, monitorowanie usługi.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**2** i **o nazwie**|  
|**Wartość domyślna**|**9800**|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-dataport-int32"></a>— Port danych < Int32\>  
 Ten parametr określa TCP port używany jako port danych dla zestawu MDT, monitorowanie usługi.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**3** i **o nazwie**|  
|**Wartość domyślna**|**9801**|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 To polecenie cmdlet obsługuje następujące typowe parametry: *Verbose, Debug, ErrorAction, ErrorVariable, OutBuffer OutVariable, WarningAction* i *WarningVariable.* Aby uzyskać więcej informacji zobacz temat "about_CommonParameters", które można otworzyć, wpisując następujące polecenie, a następnie naciskając klawisz ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>dane wyjściowe  
 To polecenie cmdlet wyświetla **ciąg** typu object, jeśli *pełne* wspólnego parametru jest uwzględnione; w przeciwnym razie generowane żadne dane wyjściowe.  

#### <a name="example-1"></a>Przykład 1  

```  
Enable-MDTMonitorService  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie umożliwia monitorowanie usługi na komputerze lokalnym przy użyciu wartości domyślnej z zestaw MDT **9800** portu zdarzeń i wartość **9801** portu danych na zestaw MDT usługi monitorowania.  

#### <a name="example-2"></a>Przykład 2  

```  
Enable-MDTMonitorService –EventPort 7000 –DataPort 7001  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie umożliwia monitorowanie usługi na komputerze lokalnym przy użyciu wartości zestaw MDT **7000** portu zdarzeń i wartość **7001** portu danych na zestaw MDT usługi monitorowania.  

###  <a name="Get-MDTDeploymentShareStatistics"></a>Get-MDTDeploymentShareStatistics  
 W tej sekcji opisano **Get-MDTDeploymentShareStatistics** polecenia cmdlet programu Windows PowerShell. Uruchom to polecenie cmdlet z konsoli programu Windows PowerShell, która ma PowerShell zestawu MDT przystawki załadowany. Aby uzyskać więcej informacji na temat sposobu uruchamiania konsoli programu Windows PowerShell, która ma przystawki programu PowerShell zestawu MDT załadowane, zobacz "podczas ładowania zestawu MDT Windows PowerShell przystawki".  

#### <a name="syntax"></a>Składnia  

```  
Get-MDTDeploymentShareStatistics [-Path <String>] [<CommonParameters>]  
```  

#### <a name="description"></a>Opis  
 To polecenie cmdlet wyświetla statystyki udziału wdrożenia oparte na dysku MDTProvder, który jest określony w *ścieżki* parametru. Statystyki obejmują liczbę elementów w udziale określonym wdrożeniu:  

-   Aplikacje  

-   Sterowniki  

-   Systemy operacyjne  

-   Pakiety  

-   Sekwencje zadań  

-   Profile zaznaczenia  

-   Udziały wdrożenia połączonego  

-   Nośnik zestawu MDT  

-   Komputery w bazie danych zestawu MDT  

-   Marka i modele w bazie danych zestawu MDT  

-   Lokalizacje w bazie danych zestawu MDT  

-   Role w bazie danych zestawu MDT  

> [!NOTE]
>  Wartości statystyk, które odnoszą się do zestawu MDT bazy danych nie są wypełnione i zawsze zwraca wartość zero.  

#### <a name="parameters"></a>Parametry  
 Ta podsekcja zawiera informacje o różnych parametrów, które mogą być używane z **Get-MDTDeploymentShareStatistics** polecenia cmdlet.  

##### <a name="-path-string"></a>-Path < ciąg\>  
 Ten parametr określa dysk programu Windows PowerShell MDTProvider udziału wdrożenia odpowiednie.  

> [!NOTE]
>  Jeśli ten parametr nie zostanie podany, do lokalizacji w ramach żądany dysk programu Windows PowerShell MDTProvider musi domyślny katalog roboczy programu Windows PowerShell.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**2** i **o nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 To polecenie cmdlet obsługuje następujące typowe parametry: *Verbose, Debug, ErrorAction, ErrorVariable, OutBuffer OutVariable, WarningAction* i *WarningVariable.* Aby uzyskać więcej informacji zobacz temat "about_CommonParameters", które można otworzyć, wpisując następujące polecenie, a następnie naciskając klawisz ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>dane wyjściowe  
 To polecenie cmdlet wyświetla **PSObject** obiekt typu, który zawiera statystyki dotyczące udziału wdrożenia.  

#### <a name="example-1"></a>Przykład 1  

```  
Get-MDTDeploymentShareStatistics –Path DS001:  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie zwraca statystyki udziału wdrożenia dla udziału wdrożenia, który określono w DS001: Dysk MDTProvider Windows PowerShell.  

#### <a name="example-2"></a>Przykład 2  

```  
cd DS001:  
Get-MDTDeploymentShareStatistics  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie zwraca statystyki udziału wdrożenia dla udziału wdrożenia, który określono w DS001: Dysk MDTProvider Windows PowerShell. Użyj **cd** polecenie, aby ustawić katalogu roboczego dla programu Windows PowerShell do DS001: Dysk MDTProvider Windows PowerShell.  

###  <a name="Get-MDTMonitorData"></a>Get-MDTMonitorData  
 W tej sekcji opisano **Get-MDTMonitorData** polecenia cmdlet programu Windows PowerShell. Uruchom to polecenie cmdlet z konsoli programu Windows PowerShell, która ma PowerShell zestawu MDT przystawki załadowany. Aby uzyskać więcej informacji na temat sposobu uruchamiania konsoli programu Windows PowerShell, która ma przystawki programu PowerShell zestawu MDT załadowane, zobacz "podczas ładowania zestawu MDT Windows PowerShell przystawki".  

#### <a name="syntax"></a>Składnia  

```  
Get-MDTMonitorData [-Path <String>] [-ID <Nullable>] [<CommonParameters>]  
```  

#### <a name="description"></a>Opis  
 To polecenie cmdlet wyświetla MDT monitorowania danych, który jest raportowany udziału wdrożenia, określonego w *ścieżki* parametru. Poniżej przedstawiono przykładowe dane wyjściowe z tego polecenia cmdlet:  

```  
Name               : WDG-REF-01  
PercentComplete    : 100  
Settings           :  
Warnings           : 0  
Errors             : 0  
DeploymentStatus   : 3  
StartTime          : 5/23/2012 6:45:39 PM  
EndTime            : 5/23/2012 8:46:32 PM  
ID                 : 1  
UniqueID           : 94a0830e-f2bb-421c-b1e0-6f86f9eb9fa1  
CurrentStep        : 88  
TotalSteps         : 88  
StepName           :  
LastTime           : 5/23/2012 8:46:32 PM  
DartIP             :  
DartPort           :  
DartTicket         :  
VMHost             : WDG-HOST-01  
VMName             : WDG-REF-01  
ComputerIdentities : {}  

```  

> [!NOTE]
>  Dysk MDTProvider Windows PowerShell, który odwołuje się do tego polecenia cmdlet, musi istnieć przed uruchomieniem tego polecenia cmdlet.  

#### <a name="parameters"></a>Parametry  
 Ta podsekcja zawiera informacje o różnych parametrów, których można używać z **Get - MDTMonitorData** polecenia cmdlet.  

##### <a name="-path-string"></a>-Path < ciąg\>  
 Ten parametr określa dysk programu Windows PowerShell MDTProvider udziału wdrożenia odpowiednie.  

> [!NOTE]
>  Jeśli ten parametr nie zostanie podany, do lokalizacji w ramach żądany dysk programu Windows PowerShell MDTProvider musi domyślny katalog roboczy programu Windows PowerShell.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**2** i **o nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-id-nullable"></a>-ID < wartość null\>  
 Ten parametr określa identyfikator określonej dla wdrożenia dla określonego komputera. Jeśli ten parametr nie jest określony, są wyświetlane wszystkie dane monitorowania wdrożeń w udziału wdrożenia.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**3** i **o nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 To polecenie cmdlet obsługuje następujące typowe parametry: *Verbose, Debug, ErrorAction, ErrorVariable, OutBuffer OutVariable, WarningAction* i *WarningVariable.* Aby uzyskać więcej informacji zobacz temat "about_CommonParameters", które można otworzyć, wpisując następujące polecenie, a następnie naciskając klawisz ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>dane wyjściowe  
 To polecenie cmdlet wyświetla **PSObject** typ obiektu dla każdego monitorowanego komputera, który zawiera dane monitorowania dla komputera.  

#### <a name="example-1"></a>Przykład 1  

```  
Get-MDTMonitorData –Path DS001:  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie zwraca dane monitorowania wszystkich wdrożeń określonej w DS001 udziału wdrożenia: Dysk MDTProvider Windows PowerShell.  

#### <a name="example-2"></a>Przykład 2  

```  
cd DS001:  
Get-MDTMonitorData  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie zwraca dane monitorowania wszystkich wdrożeń określonej w DS001 udziału wdrożenia: Dysk MDTProvider Windows PowerShell. Użyj **cd** polecenie, aby ustawić katalogu roboczego dla programu Windows PowerShell do DS001: Dysk MDTProvider Windows PowerShell.  

#### <a name="example-3"></a>Przykład 3  

```  
Get-MDTMonitorData –Path DS001: -ID 22  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie zwraca dane monitorowania wdrożenia o identyfikatorze 22 udziału wdrożenia, który jest określony w DS001: Dysk MDTProvider Windows PowerShell.  

###  <a name="Get-MDTOperatingSystemCatalog"></a>Get-MDTOperatingSystemCatalog  
 W tej sekcji opisano **Get-MDTOperatingSystemCatalog** polecenia cmdlet programu Windows PowerShell. Uruchom to polecenie cmdlet z konsoli programu Windows PowerShell, która ma PowerShell zestawu MDT przystawki załadowany. Aby uzyskać więcej informacji na temat sposobu uruchamiania konsoli programu Windows PowerShell, która ma przystawki programu PowerShell zestawu MDT załadowane, zobacz "podczas ładowania zestawu MDT Windows PowerShell przystawki".  

#### <a name="syntax"></a>Składnia  

```  
Get-MDTOperatingSystemCatalog [-ImageFile] <String> [-Index] <Int32> [<CommonParameters>]  
```  

#### <a name="description"></a>Opis  
 To polecenie cmdlet pobiera lub tworzy wykazu systemu operacyjnego dla obrazu niestandardowego systemu operacyjnego, dzięki czemu można modyfikować przy użyciu systemu Windows System Image Manager (WSIM) odpowiadający mu plik unattend.xml. Katalog systemu operacyjnego, nie jest dostępny lub istniejącego katalogu systemu operacyjnego jest nieprawidłowy lub nieaktualny, to polecenie cmdlet spowoduje wygenerowanie nowego katalogu systemu operacyjnego.  

> [!NOTE]
>  Proces generowania nowego katalogu systemu operacyjnego może zająć dużo czasu, jak niestandardowy obraz systemu operacyjnego musi być zainstalowany, inspekcji i odinstalować przed zakończeniem tworzenia katalogu systemów operacyjnych.  

#### <a name="parameters"></a>Parametry  
 Ta podsekcja zawiera informacje o różnych parametrów, które mogą być używane z **Get-MDTOperatingSystemCatalog** polecenia cmdlet.  

##### <a name="-imagefile-string"></a>Obiekt ImageFile — < ciąg\>  
 Ten parametr określa pełną ścieżkę do pliku obrazu niestandardowego systemu operacyjnego (plik wim), łącznie z nazwą pliku obrazu niestandardowego systemu operacyjnego.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość true**|  
|**Pozycja?**|**2** i **o nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-index-int32"></a>-Indeks < Int32\>  
 Ten parametr określa indeks obrazu odpowiedni system operacyjny w pliku obrazu systemu operacyjnego (plik wim).  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość true**|  
|**Pozycja?**|**3** i **o nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 To polecenie cmdlet obsługuje następujące typowe parametry: *Verbose, Debug, ErrorAction, ErrorVariable, OutBuffer OutVariable, WarningAction* i *WarningVariable.* Aby uzyskać więcej informacji zobacz temat "about_CommonParameters", które można otworzyć, wpisując następujące polecenie, a następnie naciskając klawisz ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>dane wyjściowe  
 To polecenie cmdlet wyświetla **PSObject** typu obiektu, który zawiera ścieżkę do katalogu systemu operacyjnego.  

#### <a name="example-1"></a>Przykład 1  

```  
Get-MDTOperatingSystemCatalog –ImageFile "DS001:\Operating Systems\Windows 8\sources\install.wim" –Index 2  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie zwraca katalogu systemu operacyjnego dla obrazu systemu operacyjnego pod indeksem 2 8\sources\install.wim DS001:\Operating Systems\Windows pliku obrazu systemu operacyjnego.  

###  <a name="Get-MDTPersistentDrive"></a>Get-MDTPersistentDrive  
 W tej sekcji opisano **Get-MDTPersistentDrive** polecenia cmdlet programu Windows PowerShell. Uruchom to polecenie cmdlet z konsoli programu Windows PowerShell, która ma PowerShell zestawu MDT przystawki załadowany. Aby uzyskać więcej informacji na temat sposobu uruchamiania konsoli programu Windows PowerShell, która ma przystawki programu PowerShell zestawu MDT załadowane, zobacz "podczas ładowania zestawu MDT Windows PowerShell przystawki".  

#### <a name="syntax"></a>Składnia  

```  
Get-MDTPersistentDrive [<CommonParameters>]  
```  

#### <a name="description"></a>Opis  
 To polecenie cmdlet wyświetla listę utrwalonego dysków programu Windows PowerShell dla zestawu MDT. Na liście utrwalonego dysków programu Windows PowerShell dla zestawu MDT odbywa się przy użyciu [MDTPersistentDrive Dodaj](#Add-MDTPersistentDrive) i [MDTPersistentDrive Usuń](#Remove-MDTPersistentDrive) poleceń cmdlet lub konsoli Deployment Workbench.  

 Dane wyjściowe tego polecenia cmdlet, zawiera następujące informacje:  

-   Nazwa dysku środowiska Windows PowerShell, takie jak DS001  

-   Ścieżka katalogu, takie jak \\\WDG-MDT-01\DeploymentShare$  

 Utrwalonych dysków programu Windows PowerShell dla zestawu MDT są podobne do mapowania dysków utrwalonego sieci.  

> [!NOTE]
>  Ta lista utrwalonego dysków programu Windows PowerShell dla zestawu MDT jest przechowywany w poszczególnych użytkowników i są przechowywane w profilu użytkownika.  

#### <a name="parameters"></a>Parametry  
 Ta podsekcja zawiera informacje o różnych parametrów, które mogą być używane z **Get - MDTPersistentDrive** polecenia cmdlet.  

##### <a name="commonparameters"></a>< CommonParameters\>  
 To polecenie cmdlet obsługuje następujące typowe parametry: *Verbose, Debug, ErrorAction, ErrorVariable, OutBuffer OutVariable, WarningAction* i *WarningVariable.* Aby uzyskać więcej informacji zobacz temat "about_CommonParameters", które można otworzyć, wpisując następujące polecenie, a następnie naciskając klawisz ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>dane wyjściowe  
 To polecenie cmdlet wyświetla **PSObject** typ obiektu dla każdego zestawu MDT utrwalone dysku, który jest taki sam jak **PSObject** typu obiektu, który [elementu PSDrive nowy](http://technet.microsoft.com/library/dd315340.aspx) polecenie cmdlet zwraca.  

#### <a name="example-1"></a>Przykład 1  

```  
Get-MDTPersistentDrive  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie wyświetla listę zestaw MDT utrwalone dysków.  

###  <a name="Import-MDTApplication"></a>MDTApplication importu  
 W tej sekcji opisano **MDTApplication importu** polecenia cmdlet programu Windows PowerShell. Uruchom to polecenie cmdlet z konsoli programu Windows PowerShell, która ma PowerShell zestawu MDT przystawki załadowany. Aby uzyskać więcej informacji na temat sposobu uruchamiania konsoli programu Windows PowerShell, która ma przystawki programu PowerShell zestawu MDT załadowane, zobacz "podczas ładowania zestawu MDT Windows PowerShell przystawki".  

#### <a name="syntax"></a>Składnia  

```  
Import-MDTApplication [-Path <String>] -Name <String> ApplicationSourcePath <String> -DestinationFolder <String> [-Move] [<CommonParameters>]  
```  

 — lub —  

```  
Import-MDTApplication [-Path <String>] -Name <String> NoSource [<CommonParameters>]  
```  

 — lub —  

```  
Import-MDTApplication [-Path <String>] -Name <String> Bundle [<CommonParameters>]  
```  

#### <a name="description"></a>Opis  
 To polecenie cmdlet Importuje aplikację do udziału wdrożenia. Za pomocą tego polecenia cmdlet można zaimportować następujących typów aplikacji:  

-   Aplikacje, które mają pliki źródłowe, za pomocą *ApplicationSourcePath*, *DestinationFolder*, i *Przenieś* parametrów. W pierwszym przykładzie składni przedstawiono użycie tego polecenia cmdlet dla tego typu aplikacji.  

-   Aplikacje bez plików źródłowych lub z plików źródłowych znajdujących się w innych sieci udostępnione foldery przy użyciu *NoSource* parametru. Drugi przykład składni przedstawiono użycie tego polecenia cmdlet dla tego typu aplikacji.  

-   Pakiety aplikacji, które są używane do grupowania zestawu powiązanych aplikacji, za pomocą *pakietu* parametru. Ostatni przykład składni przedstawiono użycie tego polecenia cmdlet dla tego typu aplikacji.  

#### <a name="parameters"></a>Parametry  
 Ta podsekcja zawiera informacje o różnych parametrów, które mogą być używane z **MDTApplication importu** polecenia cmdlet.  

##### <a name="-path-string"></a>-Path < ciąg\>  
 Ten parametr określa pełną ścieżkę do istniejącego folderu rozmieszczenia aplikacji importowanych w obrębie udziału wdrożenia. Jeśli *DestinationFolder* parametr jest używany, a następnie folder określony w *DestinationFolder* parametru jest tworzony poniżej folderu, w tym parametrze. Ten parametr jest używany w wszystkich składni użycia tego polecenia cmdlet.  

> [!NOTE]
>  Jeśli ten parametr nie zostanie podany, katalog roboczy programu Windows PowerShell musi być domyślnie do odpowiedniej lokalizacji w obrębie udziału wdrożenia.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-name-string"></a>-Nazwa < ciąg\>  
 Ten parametr określa nazwę aplikacji, które mają zostać dodane do udziału wdrożenia i muszą być unikatowe w obrębie udziału wdrożenia. Ten parametr jest używany w wszystkich składni użycia tego polecenia cmdlet.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość true**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-applicationsourcepath-string"></a>-ApplicationSourcePath < ciąg\>  
 Ten parametr określa w pełni kwalifikowana ścieżka do plików źródłowych aplikacji dla aplikacji, które zostaną zaimportowane do udziału wdrożenia. Ten parametr jest tylko prawidłowy do stosowania w pierwszym przykładzie składni.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość true**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-destinationfolder-string"></a>-DestinationFolder < ciąg\>  
 Ten parametr określa folder, w których pliki źródłowe aplikacji do zaimportowania udziału wdrożenia. Ten folder jest tworzony poniżej folder określony w *ścieżki* parametru. Ten parametr jest tylko prawidłowy do stosowania w pierwszym przykładzie składni.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość true**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-move-switchparameter"></a>-Przenieś [< parametr przełącznika\>]  
 Ten parametr określa, czy można przenosić pliki źródłowe aplikacji (zamiast skopiowany) z folderu, w którym znajdują się pliki źródłowe aplikacji, który został określony w *ApplicationSourcePath* parametru.  

 Jeśli ten parametr jest:  

-   Określony, a następnie przeniesieniu plików i pliki w folderze określone w *ApplicationSourcePath* parametru są usuwane.  

-   Nie określony, a następnie pliki są kopiowane i pliki w folderze określone w *ApplicationSourcePath* parametru są zachowywane.  

 Ten parametr jest tylko prawidłowy do stosowania w pierwszym przykładzie składni.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-nosource-switchparameter"></a>-NoSource [< parametr przełącznika\>]  
 Ten parametr określa, że aplikacja importowany jest aplikacja, która nie ma plików źródła do skopiowania. Korzystając z tego parametru, mają pliki źródłowe aplikacji:  

-   W udostępnionym folderze sieciowym, który został określony w ustawieniach aplikacji w instalacji wiersza polecenia lub pracy katalogu konfiguracji  

-   Znajdujących się już w obrazie systemu operacyjnego  

 Ten parametr jest tylko prawidłowy do stosowania w drugim przykładzie składni.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość true,** (**ByValue**)|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-bundle-switchparameter"></a>-Pakietu [< parametr przełącznika\>]  
 Ten parametr określa, że aplikacja importowany jest aplikacja, która jest pakiet dwóch lub więcej aplikacji. Ten parametr jest tylko prawidłowy do stosowania w ostatnim przykładzie składni.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość true,** (**ByValue**)|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 To polecenie cmdlet obsługuje następujące typowe parametry: *Verbose, Debug, ErrorAction, ErrorVariable, OutBuffer OutVariable, WarningAction* i *WarningVariable.* Aby uzyskać więcej informacji zobacz temat "about_CommonParameters", które można otworzyć, wpisując następujące polecenie, a następnie naciskając klawisz ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>dane wyjściowe  
 To polecenie cmdlet wyświetla **PSObject** typu obiektu, który odwołuje się do aplikacji, które właśnie zaimportowany.  

#### <a name="example-1"></a>Przykład 1  

```  
Import-MDTApplication -Path "DS001:\Applications" -Name "Office 2010 Professional Plus 32-bit" ApplicationSourcePath "\\WDG-MDT-01\Source$\Office2010ProPlus\x86" DestinationFolder "Office2010ProPlusx86"  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie importuje aplikacji z plików źródłowych z udostępnionego folderu sieciowego na \\\WDG-MDT-01\Source$\Office2010ProPlus\x86, jak i kopie plików źródłowych do DS001:\Applications\Office2010ProPlusx86 w obrębie udziału wdrożenia. Pliki źródłowe zostaną zachowane.  

#### <a name="example-2"></a>Przykład 2  

```  
Import-MDTApplication -Path "DS001:\Applications" -Name "Office 2010 Professional Plus 32-bit" ApplicationSourcePath "\\WDG-MDT-01\Source$\Office2010ProPlus\x86" DestinationFolder "Office2010ProPlusx86" -Move  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie importuje aplikacji z plików źródłowych z udostępnionego folderu sieciowego na \\\WDG-MDT-01\Source$\Office2010ProPlus\x86 i przenoszenie plików źródłowych do DS001:\Applications\Office2010ProPlusx86 w obrębie udziału wdrożenia. Pliki źródłowe są usuwane z udostępnionego folderu sieciowego na \\\WDG-MDT-01\Source$\Office2010ProPlus\x86. Aplikacja o nazwie *pakietu Office 2012 Professional Plus 32-bitowych.*  

#### <a name="example-3"></a>Przykład 3  

```  
Import-MDTApplication -Path "DS001:\Applications" -Name "Office 2010 Professional Plus 32-bit" NoSource  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie importuje aplikacji o nazwie *pakietu Office 2012 Professional Plus 32-bitowych* nie plików źródłowych.  

#### <a name="example-4"></a>Przykład 4  

```  
Import-MDTApplication -Path "DS001:\Applications" -Name "Woodgrove Bank Core Applications" Bundle  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie importuje pakietu aplikacji o nazwie *Woodgrove Bank podstawowych aplikacji.*  

###  <a name="Import-MDTDriver"></a>MDTDriver importu  
 W tej sekcji opisano **MDTDriver importu** polecenia cmdlet programu Windows PowerShell. Uruchom to polecenie cmdlet z konsoli programu Windows PowerShell, która ma PowerShell zestawu MDT przystawki załadowany. Aby uzyskać więcej informacji na temat sposobu uruchamiania konsoli programu Windows PowerShell, która ma przystawki programu PowerShell zestawu MDT załadowane, zobacz "podczas ładowania zestawu MDT Windows PowerShell przystawki".  

#### <a name="syntax"></a>Składnia  

```  
Import-MDTDriver [-Path <String>] -SourcePath <String[]> [ImportDuplicates] [<CommonParameters>]  
```  

#### <a name="description"></a>Opis  
 To polecenie cmdlet importuje co najmniej jednego sterownika urządzenia do udziału wdrożenia. To polecenie cmdlet wyszukuje sterowniki urządzeń, zaczynając od folder określony w *Ścieżka_źródłowa* parametru. To polecenie cmdlet zlokalizuje wiele sterowników urządzeń w tej struktury folderów.  

#### <a name="parameters"></a>Parametry  
 Ta podsekcja zawiera informacje o różnych parametrów, które mogą być używane z **MDTDriver importu** polecenia cmdlet.  

##### <a name="-path-string"></a>-Path < ciąg\>  
 Ten parametr określa pełną ścieżkę do istniejącego folderu, w którym sterownik urządzenia, które zostały zaimportowane zostaną umieszczone w obrębie udziału wdrożenia.  

> [!NOTE]
>  Jeśli ten parametr nie zostanie podany, do odpowiedniej lokalizacji w obrębie udziału wdrożenia musi domyślny katalog roboczy programu Windows PowerShell. Ten parametr musi być podany, jeśli *Ścieżka_źródłowa* nie podano parametru.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-sourcepath-string-"></a>-SourcePath < ciąg [] >  
 Ten parametr określa co najmniej jedną pełną ścieżkę w tablicy ciągów dla folderów źródło, gdzie znajdują się pliki sterownika urządzenia. Każdy struktury folderów, począwszy od folderu, w tym parametrze jest wyszukiwany sterowniki urządzeń, w tym wszystkie podfoldery i zawartość plików cab w strukturze folderu.  

> [!NOTE]
>  Jeśli ten parametr nie zostanie podana, do folderu, w którym znajdują się pliki sterownika urządzenia musi domyślny katalog roboczy programu Windows PowerShell. Ten parametr musi być podany, jeśli *ścieżka* nie podano parametru.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość true**|  
|**Pozycja?**|**1** i **o nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-importduplicates-switchparameter"></a>-ImportDuplicates [< parametr przełącznika\>]  
 Ten parametr określa, czy to polecenie cmdlet należy importować zduplikowanych sterowników urządzeń. Domyślnie nie są importowane zduplikowanych sterowników urządzeń. Zduplikowane sterowniki są wykrywane przez obliczania wartości skrótu, dla wszystkich plików w folderze sterownika urządzenia. Jeśli wartość skrótu obliczeniowej pasuje do innego sterownika urządzenia, do zaimportowania sterownika urządzenia jest uznany za duplikat.  

 Jeśli wykryto zduplikowane sterownika, a nie podano tego parametru, sterownika urządzenia zostanie dodane i połączone z oryginalne, istniejącego sterownika.  

 Jeśli ten parametr jest:  

-   Określony, następnie zduplikowane sterowniki zostały zaimportowane  

-   Nie jest określony, następnie sterowniki urządzeń zostanie dodany i połączone z oryginalnej, a istniejące sterowniki  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość true,** (**ByValue**)|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 To polecenie cmdlet obsługuje następujące typowe parametry: *Verbose, Debug, ErrorAction, ErrorVariable, OutBuffer OutVariable, WarningAction* i *WarningVariable.* Aby uzyskać więcej informacji zobacz temat "about_CommonParameters", które można otworzyć, wpisując następujące polecenie, a następnie naciskając klawisz ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>dane wyjściowe  
 To polecenie cmdlet wyświetla co najmniej jeden **PSObject** obiekty (po jednym dla każdego sterownika urządzenia zaimportowane) typu.  

#### <a name="example-1"></a>Przykład 1  

```  
Import-MDTDriver -Path "DS001:\Out-of-Box Drivers" SourcePath "\\WDG-MDT-01\Source$\Drivers"  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie importuje wszystkie sterowniki urządzeń w strukturze folderów z certyfikatem głównym struktury folderów na \\\WDG-MDT-01\Source$\Drivers. Sterowniki urządzeń są przechowywane w folderze Out-of-Box sterowniki w udziału wdrożenia, który jest zamapowany na DS001: Dysk MDTProvder Windows PowerShell. Duplikatów sterowników urządzenia zostaną wykryte, sterowniki urządzeń zostanie dodany i połączone z sterowników urządzeń oryginalny, a istniejące w udziału wdrożenia.  

#### <a name="example-2"></a>Przykład 2  

```  
$DriverSourcePath="\\WDG-MDT-01\Source$\VendorADrivers", "\\WDG-MDT-01\Source$\VendorBDrivers"  
Import-MDTDriver -Path "DS001:\Out-of-Box Drivers" SourcePath $DriverSourcePath ImportDuplicates  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie importuje wszystkie sterowniki urządzeń w strukturze folderów określone w tablicy ciągów $DriverSourcePath. Sterowniki urządzeń są przechowywane w folderze Out-of-Box sterowniki w udziału wdrożenia, który jest zamapowany na DS001: Dysk MDTProvder Windows PowerShell. Jeśli duplikatów sterowników urządzenia zostaną wykryte, zduplikowany sterowniki zostaną zaimportowane.  

###  <a name="Import-MDTOperatingSystem"></a>MDTOperatingSystem importu  
 W tej sekcji opisano **MDTOperatingSystem importu** polecenia cmdlet programu Windows PowerShell. Uruchom to polecenie cmdlet z konsoli programu Windows PowerShell, która ma PowerShell zestawu MDT przystawki załadowany. Aby uzyskać więcej informacji na temat sposobu uruchamiania konsoli programu Windows PowerShell, która ma przystawki programu PowerShell zestawu MDT załadowane, zobacz "podczas ładowania zestawu MDT Windows PowerShell przystawki".  

#### <a name="syntax"></a>Składnia  

```  
Import-MDTOperatingSystem [-Path <String>] -SourcePath <String> [-DestinationFolder <String>] [-Move] [<CommonParameters>]  
```  

 — lub —  

```  
Import-MDTOperatingSystem [-Path <String>] [DestinationFolder <String>] -SourceFile <String> [SetupPath <String>] [-Move] [<CommonParameters>]  
```  

 — lub —  

```  
Import-MDTOperatingSystem [-Path <String>] -WDSServer <String> [<CommonParameters>]  
```  

#### <a name="description"></a>Opis  
 To polecenie cmdlet importuje systemem operacyjnym do udziału wdrożenia. Można zaimportować następujących typów systemu operacyjnego za pomocą tego polecenia cmdlet:  

-   Systemy operacyjne z oryginalnych plików źródłowych, przy użyciu *Ścieżka_źródłowa* parametrów. W pierwszym przykładzie składni przedstawiono użycie tego polecenia cmdlet dla tego typu importu systemu operacyjnego.  

-   Pliki, takich jak obrazy przechwytywania z komputerów odniesienia, przy użyciu obrazów niestandardowych systemów operacyjnych *SourceFile* parametru. Drugi przykład składni przedstawiono użycie tego polecenia cmdlet dla tego typu importu systemu operacyjnego.  

-   Obrazy systemu operacyjnego, które znajdują się za pomocą usług wdrażania systemu Windows *WDSServer* parametru. Ostatni przykład składni przedstawiono użycie tego polecenia cmdlet dla tego typu importu systemu operacyjnego.  

#### <a name="parameters"></a>Parametry  
 Ta podsekcja zawiera informacje o różnych parametrów, które mogą być używane z **MDTOperatingSystem importu** polecenia cmdlet.  

##### <a name="-path-string"></a>-Path < ciąg\>  
 Ten parametr określa pełną ścieżkę do istniejącego folderu w obrębie udziału wdrożenia rozmieszczenia systemu operacyjnego zostały zaimportowane. Jeśli *DestinationFolder* parametr jest używany, a następnie folder określony w *DestinationFolder* parametru jest tworzony poniżej folderu, w tym parametrze. Ten parametr jest używany w wszystkich składni użycia tego polecenia cmdlet.  

> [!NOTE]
>  Jeśli ten parametr nie zostanie podany, do odpowiedniej lokalizacji w obrębie udziału wdrożenia musi domyślny katalog roboczy programu Windows PowerShell.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-sourcepath-string"></a>-SourcePath < ciąg\>  
 Ten parametr określa w pełni kwalifikowana ścieżka do plików źródłowych systemu operacyjnego, systemu operacyjnego, które zostaną zaimportowane do udziału wdrożenia. Ten parametr jest tylko prawidłowy do stosowania w pierwszym przykładzie składni.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość true**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-destinationfolder-string"></a>-DestinationFolder < ciąg\>  
 Ten parametr określa folder, w których plików źródłowych systemu operacyjnego do zaimportowania udziału wdrożenia. Ten folder jest tworzony poniżej folder określony w *ścieżki* parametru. Ten parametr jest tylko prawidłowy do stosowania w przykładach składni pierwszego i drugiego.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość true**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-move-switchparameter"></a>-Przenieś [< parametr przełącznika\>]  
 Ten parametr określa, czy można przenieść plików źródłowych systemu operacyjnego (zamiast skopiowany) z folderu, w którym znajdują się pliki źródłowe systemu operacyjnego, który został określony w *DestinationFolder* parametru.  

 Jeśli ten parametr jest:  

-   Określony, a następnie przeniesieniu plików i pliki w folderze określone w *DestinationFolder* parametru są usuwane.  

-   Nie określony, a następnie pliki są kopiowane i pliki w folderze określone w *DestinationFolder* parametru są zachowywane.  

 Ten parametr jest tylko prawidłowy do stosowania w przykładach składni pierwszego i drugiego.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-sourcefile-string"></a>-SourceFile < ciąg\>  
 Ten parametr określa w pełni kwalifikowana ścieżka do źródłowy plik wim systemu operacyjnego dla systemu operacyjnego, które zostaną zaimportowane do udziału wdrożenia. Ten parametr jest tylko prawidłowy do stosowania w drugim przykładzie składni.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość true**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-setuppath-string"></a>-SetupPath < ciąg\>  
 Ten parametr określa w pełni kwalifikowana ścieżka do plików instalacji systemu operacyjnego, które wymagają zaimportowania wraz z określonego w pliku wim *SourceFile* parametru. Ten parametr jest tylko prawidłowy do stosowania w drugim przykładzie składni.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość true**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-wdsserver-string"></a>-WDSServer < ciąg\>  
 Ten parametr określa nazwę serwera usług wdrażania systemu Windows, na którym znajdują się pliki obrazów systemu operacyjnego do zaimportowania. Wszystkie pliki obrazów działania na serwerze usług wdrażania systemu Windows zostaną zaimportowane do udziału wdrożenia. Pliki obrazów systemu operacyjnego nie są kopiowane do udziału wdrożenia. Zamiast tego udziału wdrożenia zawiera łącze do każdego pliku systemu operacyjnego na serwerze usług wdrażania systemu Windows.  

 Ten parametr jest tylko prawidłowy do stosowania w ostatnim przykładzie składni.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 To polecenie cmdlet obsługuje następujące typowe parametry: *Verbose, Debug, ErrorAction, ErrorVariable, OutBuffer OutVariable, WarningAction* i *WarningVariable.* Aby uzyskać więcej informacji zobacz temat "about_CommonParameters", które można otworzyć, wpisując następujące polecenie, a następnie naciskając klawisz ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>dane wyjściowe  
 To polecenie cmdlet wyświetla co najmniej jeden **PSObject** obiekty (po jednym dla każdego systemu operacyjnego, które zostały zaimportowane) typu.  

#### <a name="example-1"></a>Przykład 1  

```  
Import-MDTOperatingSystem -Path "DS001:\Operating Systems" SourcePath "\\WDGMDT01\Source$\Windows8" DestinationFolder "Windows8x64"  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie importuje systemem operacyjnym z udostępnionego folderu sieciowego na \\\WDG-MDT-01\Source$\Windows8, jak i kopie plików źródłowych do DS001:\Operating Systems\Windows8x64 w obrębie udziału wdrożenia. Pliki źródłowe zostaną zachowane.  

#### <a name="example-2"></a>Przykład 2  

```  
Import-MDTOperatingSystem -Path "DS001:\Operating Systems" SourcePath "\\WDGMDT01\Source$\Windows8" DestinationFolder "Windows8x64" -Move  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie importuje systemem operacyjnym z udostępnionego folderu sieciowego na \\\WDG-MDT-01\Source$\Windows8, jak i kopie plików źródłowych do DS001:\Operating Systems\Windows8x64 w obrębie udziału wdrożenia. Pliki źródłowe są usuwane z udostępnionego folderu sieciowego na \\\WDG-MDT-01\Source$\Windows8.  

#### <a name="example-3"></a>Przykład 3  

```  
Import-MDTOperatingSystem -Path "DS001:\Operating Systems" DestinationFolder "Windows8x64-Reference" –SourceFile "\\WDGMDT01\Capture$\WDG-REF-01_Capture.wim"  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie importuje plik przechwycone, niestandardowy obraz systemu operacyjnego (plik wim) z \\\WDG-MDT-01\ przechwytywania$ \WDG-REF-01_Capture.wim i kopiuje plik obrazu DS001:\Operating Systems\Windows8x64 — odwołanie w obrębie udziału wdrożenia. Źródłowy plik wim są przechowywane w udostępnionym folderze sieciowym.  

#### <a name="example-4"></a>Przykład 4  

```  
Import-MDTOperatingSystem -Path "DS001:\Operating Systems" WDSServer "WDG-WDS-01"  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie importuje wszystkie obrazy systemu operacyjnego z serwera usług wdrażania systemu Windows o nazwie WDG-WDS-01 i tworzy łącze do każdego obrazu systemu operacyjnego w systemach DS001:\Operating w obrębie udziału wdrożenia. Źródłowe pliki obrazów systemu operacyjnego na serwerze usług wdrażania systemu Windows są przechowywane na serwerze usług wdrażania systemu Windows.  

###  <a name="Import-MDTPackage"></a>MDTPackage importu  
 W tej sekcji opisano **MDTPackage importu** polecenia cmdlet programu Windows PowerShell. Uruchom to polecenie cmdlet z konsoli programu Windows PowerShell, która ma PowerShell zestawu MDT przystawki załadowany. Aby uzyskać więcej informacji na temat sposobu uruchamiania konsoli programu Windows PowerShell, która ma przystawki programu PowerShell zestawu MDT załadowane, zobacz "podczas ładowania zestawu MDT Windows PowerShell przystawki".  

#### <a name="syntax"></a>Składnia  

```  
Import-MDTPackage [-Path <String>] [[-SourcePath] <String[]>] [<CommonParameters>]  
```  

#### <a name="description"></a>Opis  
 To polecenie cmdlet importuje jeden lub więcej pakietów systemu operacyjnego do udziału wdrożenia. Typy pakietów systemu operacyjnego, które można importować obejmują aktualizacje zabezpieczeń, pakiety językowe lub nowych składników. Dodatki Service Pack nie powinny być importowane jako pakietów systemu operacyjnego, ponieważ nie można zainstalować w trybie offline.  

#### <a name="parameters"></a>Parametry  
 Ta podsekcja zawiera informacje o różnych parametrów, które mogą być używane z **MDTPackage importu** polecenia cmdlet.  

##### <a name="-path-string"></a>-Path < ciąg\>  
 Ten parametr określa pełną ścieżkę do istniejącego folderu w obrębie udziału wdrożenia rozmieszczenia importowanych pakietów systemu operacyjnego.  

> [!NOTE]
>  Jeśli ten parametr nie zostanie podany, do odpowiedniej lokalizacji w obrębie udziału wdrożenia musi domyślny katalog roboczy programu Windows PowerShell.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-sourcepath-string"></a>-SourcePath < ciąg\>  
 Ten parametr określa w pełni kwalifikowana ścieżka do strukturę folderów dla pakietów systemu operacyjnego do zaimportowania. Struktura określony folder będzie skanowanych plików cab i msu. Pliki .msu pliki cab wewnątrz plików msu są wyodrębniane automatycznie.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość true**|  
|**Pozycja?**|**1** i **o nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 To polecenie cmdlet obsługuje następujące typowe parametry: *Verbose, Debug, ErrorAction, ErrorVariable, OutBuffer OutVariable, WarningAction* i *WarningVariable.* Aby uzyskać więcej informacji zobacz temat "about_CommonParameters", które można otworzyć, wpisując następujące polecenie, a następnie naciskając klawisz ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>dane wyjściowe  
 To polecenie cmdlet wyświetla **PSObject** obiekt typu, który odwołuje się do pakietu, który został właśnie zaimportowany.  

#### <a name="example-1"></a>Przykład 1  

```  
Import-MDTOperatingSystem -Path "DS001:\Packages" SourcePath "\\WDGMDT01\Source$\OSPackages"  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie skanuje udostępnionego folderu sieciowego na \\\WDG-MDT-01\Source$\OSPackages dla systemu operacyjnego, pakietów i kopiuje pliki źródłowe do folderu DS001:\Packages w obrębie udziału wdrożenia. Pliki źródłowe są usuwane z udostępnionego folderu sieciowego na \\\WDG-MDT-01\Source$\OSPackages.  

###  <a name="Import-MDTTaskSequence"></a>MDTTaskSequence importu  
 W tej sekcji opisano **MDTTaskSequence importu** polecenia cmdlet programu Windows PowerShell. Uruchom to polecenie cmdlet z konsoli programu Windows PowerShell, która ma PowerShell zestawu MDT przystawki załadowany. Aby uzyskać więcej informacji na temat sposobu uruchamiania konsoli programu Windows PowerShell, która ma przystawki programu PowerShell zestawu MDT załadowane, zobacz "podczas ładowania zestawu MDT Windows PowerShell przystawki".  

#### <a name="syntax"></a>Składnia  

```  
Import-MDTTaskSequence [-Path <String>] -Template <String> -Name <String> -ID <String> [[-Comments] <String>] [[-Version] <String>] [-OperatingSystemPath <String>] [-OperatingSystem <PSObject>] [-FullName <String>] [-OrgName <String>] [-HomePage <String>] [-ProductKey <String>] [-OverrideProductKey <String>] [-AdminPassword <String>] [<CommonParameters>]  
```  

#### <a name="description"></a>Opis  
 To polecenie cmdlet importuje sekwencję zadań do udziału wdrożenia. Sekwencja zadań nowo zaimportowany będą oparte na istniejący szablon sekwencji zadań określone w *szablonu* właściwości.  

#### <a name="parameters"></a>Parametry  
 Ta podsekcja zawiera informacje o różnych parametrów, które mogą być używane z **MDTPackage importu** polecenia cmdlet.  

##### <a name="-path-string"></a>-Path < ciąg\>  
 Ten parametr określa pełną ścieżkę do istniejącego folderu w obrębie udziału wdrożenia rozmieszczenia sekwencji zadań, które zostały zaimportowane. Domyślnie powinny wskazywać ścieżkę folderu kontroli i lub podfolder folderu kontroli w udziału wdrożenia. Wartość *identyfikator* parametr będzie używany do utworzenia podfolderu w ścieżce określonej w tym parametrze.  

> [!NOTE]
>  Jeśli ten parametr nie zostanie podany, do odpowiedniej lokalizacji w obrębie udziału wdrożenia musi domyślny katalog roboczy programu Windows PowerShell.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-template-string"></a>-Template < ciąg\>  
 Ten parametr określa szablon sekwencji zadań do użycia na potrzeby importowania nowej sekwencji zadań. Szablony sekwencji zadań są pliki XML, które zawierają kroków sekwencji zadań dla danego typu sekwencji zadań. Jeśli szablon sekwencji zadań znajdują się na:  

-   *Installation_folder*\Templates folder (gdzie *installation_folder* to folder, w którym jest zainstalowany zestaw MDT), a następnie wymagana jest nazwa pliku XML.  

-   Innego folderu, a następnie pełną ścieżkę, łącznie z nazwą XML szablonu sekwencji zadań, jest wymagana.  

 Aby uzyskać więcej informacji dotyczących szablonów sekwencji zadań, które są dołączone do zestawu MDT we wdrożeniach LTI, zobacz sekcję "Tworzenie nowego zadania sekwencji w konsoli Deployment Workbench" w dokumencie MDT *przy użyciu programu Microsoft Deployment Toolkit*.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość true**|  
|**Pozycja?**|**1** i **o nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-name-string"></a>-Nazwa < ciąg\>  
 Ten parametr określa nazwę sekwencji zadań do zaimportowania. Wartość tego parametru musi być unikatowa w obrębie udziału wdrożenia.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość true**|  
|**Pozycja?**|**2** i **o nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-id-string"></a>-ID < ciąg\>  
 Ten parametr określa identyfikator sekwencji zadań do zaimportowania. Wartość tego parametru musi być unikatowa w obrębie udziału wdrożenia. Wartość przypisana do tego parametru powinny być pisane wielkimi literami i nie ma żadnych spacji ani znaków specjalnych. Ta wartość jest używana do utworzenia podfolderu w folderze określonym w *ścieżki* parametr, który powinien być w folderze kontroli w udziału wdrożenia.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość true**|  
|**Pozycja?**|**3** i **o nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-comments-string"></a>-Komentarzy < ciąg\>  
 Ten parametr określa tekst, który zawiera dodatkowe, opisowe informacje o sekwencji zadań do zaimportowania. Te informacje opisowe są widoczne w konsoli Deployment Workbench.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**4** i **o nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-version-string"></a>-Version < ciąg\>  
 Ten parametr określa numer wersji sekwencji zadań do zaimportowania. Wartość tego parametru ma tylko charakter informacyjny i nie jest używana przez zestaw MDT do przetwarzania związanych z wersją.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**4** i **o nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-operatingsystempath-string"></a>-OperatingSystemPath < ciąg\>  
 Ten parametr określa w pełni kwalifikowana ścieżka programu Windows PowerShell do folderu w udziału wdrożenia, który zawiera system operacyjny, który ma być używany z tej sekwencji zadań, takich jak DS001:\Operating Systems\Windows 8. System operacyjny musi już istnieć w udziału wdrożenia, w którym sekwencja zadań jest importowany.  

> [!NOTE]
>  Jeśli ten parametr nie zostanie określona i sekwencji zadań musi odwoływać się system operacyjny, a następnie podaj *OperatingSystem* parametru.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-operatingsystem-psobject"></a>-OperatingSystem < PSObject\>  
 Ten parametr określa obiekt systemu operacyjnego do użycia z tej sekwencji zadań. System operacyjny musi już istnieć w udziału wdrożenia, w którym sekwencja zadań jest importowany.  

 Można pobrać obiektu środowiska Windows PowerShell dla systemu operacyjnego za pomocą **elementu Get** polecenia cmdlet, takich jak na poniższym przykładzie:  

```  
$OS=Get-Item "DS001:\Operating Systems\Windows 8"  
```  

 Aby uzyskać więcej informacji na temat **elementu Get** polecenia cmdlet, zobacz [za pomocą polecenia Cmdlet Get-Item](http://technet.microsoft.com/library/ee176851).  

> [!NOTE]
>  Jeśli ten parametr nie zostanie określona i sekwencji zadań musi odwoływać się system operacyjny, a następnie podaj *OperatingSystemPath* parametru.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-fullname-string"></a>Imię i nazwisko — < ciąg\>  
 Ten parametr określa nazwę zarejestrowany właściciel systemu operacyjnego do użycia z tej sekwencji zadań. Ta nazwa jest zapisywany w **RegisteredOwner** klucza rejestru na **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion**. Wartość tego parametru jest wstrzykiwane do pliku Unattend.xml, który ma zostać skojarzony z tym sekwencji zadań.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-orgname-string"></a>-Nazwa_org < ciąg\>  
 Ten parametr określa nazwę organizacji zarejestrowany właściciel systemu operacyjnego, który ma być używany z tej sekwencji zadań. Ta nazwa jest zapisywany w **RegisteredOrganization** klucza rejestru na **HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion**. Wartość tego parametru jest wstrzykiwane do pliku Unattend.xml, który ma zostać skojarzony z tym sekwencji zadań.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-homepage-string"></a>— Strona główna < ciąg\>  
 Ten parametr określa adres URL, który ma być używany jako strony głównej w programie Internet Explorer. Wartość tego parametru jest wstrzykiwane do pliku Unattend.xml, który ma zostać skojarzony z tym sekwencji zadań.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-productkey-string"></a>-ProductKey < ciąg\>  
 Ten parametr określa klucz produktu do użycia dla systemu operacyjnego do użycia z tej sekwencji zadań. Ten klucz produktu jest prawidłowy tylko dla wersji detalicznej systemu operacyjnego. Wartość tego parametru jest wstrzykiwane do pliku Unattend.xml, który ma zostać skojarzony z tym sekwencji zadań.  

> [!NOTE]
>  Jeśli ten parametr nie zostanie podany, klucz produktu należy podać podczas wdrażania tej sekwencji zadań w Kreatorze wdrażania, w pliku CustomSettings.ini lub w bazie danych zestawu MDT.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-overrideproductkey-string"></a>-OverrideProductKey < ciąg\>  
 Ten parametr określa klucz MAK używanego systemu operacyjnego do użycia z tej sekwencji zadań. Ten klucz produktu jest prawidłowy tylko dla wersji licencji woluminu systemu Windows. Wartość tego parametru jest wstrzykiwane do pliku Unattend.xml, który ma zostać skojarzony z tym sekwencji zadań.  

> [!NOTE]
>  Jeśli ten parametr nie zostanie podany, Klucz MAK należy podać podczas wdrażania tej sekwencji zadań w Kreatorze wdrażania, w pliku CustomSettings.ini lub w bazie danych zestawu MDT.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-adminpassword-string"></a>-AdminPassword < ciąg\>  
 Ten parametr określa hasło do przypisania do wbudowanych, lokalnego konta administratora na komputerze docelowym. Wartość tego parametru jest wstrzykiwane do pliku Unattend.xml, który ma zostać skojarzony z tym sekwencji zadań.  

> [!NOTE]
>  Jeśli ten parametr nie zostanie podany, następnie hasło do przypisania do wbudowanego konta administratora lokalnego na komputerze docelowym należy podać podczas wdrażania tej sekwencji zadań w Kreatorze wdrażania, w pliku CustomSettings.ini lub w bazie danych zestawu MDT.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 To polecenie cmdlet obsługuje następujące typowe parametry: *Verbose, Debug, ErrorAction, ErrorVariable, OutBuffer OutVariable, WarningAction* i *WarningVariable.* Aby uzyskać więcej informacji zobacz temat "about_CommonParameters", które można otworzyć, wpisując następujące polecenie, a następnie naciskając klawisz ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>dane wyjściowe  
 To polecenie cmdlet wyświetla **PSObject** typu obiektu, który odwołuje się sekwencja zadań właśnie zaimportowany.  

#### <a name="example-1"></a>Przykład 1  

```  
Import-MDTTaskSequence -Path "DS001:\Control" –Template "Client.xml" –Name "Deploy Windows 8 to Reference Computer" –ID "WIN8REFERENCE" –Comments "Task sequence for deploying Windows 8 to the reference computer (WDG-REF-01)" –Version "1.00" –OperatingSystemPath "DS001:\Operating Systems\Windows 8_x64" –FullName "Woodgrove Bank Employee" –OrgName "Woodgrove Bank" HomePage "http://www.woodgrovebank.com"  OverrideProductKey "1234512345123451234512345" AdministratorPassword "P@ssw0rd"  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie importuje sekwencji zadań o nazwie *wdrażania systemu Windows 8 na komputerze odniesienia* i tworzenia sekwencji zadań w folderze DS001:\Control\WIN8REFERENCE w udziału wdrożenia. Komentarz "Sekwencję zadań pod kątem wdrażania systemu Windows 8 na komputerze odniesienia (WDG-REF-01)," jest przypisany do sekwencji zadań. Numer wersji sekwencja zadań ma ustawioną **1,00**.  

 System operacyjny skojarzone z sekwencją zadań znajduje się w 8_x64 DS001:\Operating Systems\Windows w udziału wdrożenia. Zarejestrowany właściciel systemu operacyjnego zostanie ustawiona do **pracownika banku Woodgrove**. Zarejestrowanej organizacji systemu operacyjnego zostanie ustawiona do **banku Woodgrove**. Strona główna programu Internet Explorer będzie domyślnie **http://www.woodgrovebank.com**. Hasło dla lokalnej, wbudowanego konta administratora zostanie ustawiona na wartość  **P@ssw0rd** . Klucz produktu systemu operacyjnego zostanie ustawiona do **1234512345123451234512345**.  

#### <a name="example-2"></a>Przykład 2  

```  
$OSObject=Get-Item "DS001:\Operating Systems\Windows 8_x64"  
Import-MDTTaskSequence -Path "DS001:\Control" –Template "Client.xml" –Name "Deploy Windows 8 to Reference Computer" –ID "WIN8REFERENCE" –Comments "Task sequence for deploying Windows 8 to the reference computer (WDG-REF-01)" –Version "1.00"–OperatingSystem $OSObject –FullName "Woodgrove Bank Employee" –OrgName "Woodgrove Bank" HomePage "http://www.woodgrovebank.com"  AdministratorPassword "P@ssw0rd"  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie importuje sekwencji zadań o nazwie *wdrażania systemu Windows 8 na komputerze odniesienia* i tworzenia sekwencji zadań w folderze DS001:\Control\WIN8REFERENCE w udziału wdrożenia. Komentarz "Sekwencję zadań pod kątem wdrażania systemu Windows 8 na komputerze odniesienia (WDG-REF-01)," jest przypisany do sekwencji zadań. Numer wersji sekwencja zadań ma ustawioną **1,00**.  

 Systemu operacyjnego skojarzonego z sekwencji zadań znajduje się pod adresem 8_x64 DS001:\Operating Systems\Windows w udziału wdrożenia, który jest przekazywany do polecenia cmdlet, za pomocą *$OSObject* zmiennej. *$OSObject* zmienna jest ustawiona na istniejącego systemu operacyjnego obiekt przy użyciu **elementu Get** polecenia cmdlet.  

 Zarejestrowany właściciel systemu operacyjnego zostanie ustawiona do **pracownika banku Woodgrove**. Zarejestrowanej organizacji systemu operacyjnego zostanie ustawiona do **banku Woodgrove**. Strona główna programu Internet Explorer będzie domyślnie **http://www.woodgrovebank.com**. Hasło dla lokalnej, wbudowanego konta administratora zostanie ustawiona na wartość  **P@ssw0rd** . Klucz produktu systemu operacyjnego, należy podać podczas wdrażania tej sekwencji zadań w Kreatorze wdrażania, w pliku CustomSettings.ini lub w bazie danych zestawu MDT.  

###  <a name="New-MDTDatabase"></a>Nowe MDTDatabase  
 W tej sekcji opisano **MDTDatabase nowy** polecenia cmdlet programu Windows PowerShell. Uruchom to polecenie cmdlet z konsoli programu Windows PowerShell, która ma PowerShell zestawu MDT przystawki załadowany. Aby uzyskać więcej informacji na temat sposobu uruchamiania konsoli programu Windows PowerShell, która ma przystawki programu PowerShell zestawu MDT załadowane, zobacz "podczas ładowania zestawu MDT Windows PowerShell przystawki".  

#### <a name="syntax"></a>Składnia  

```  
New-MDTDatabase [-Path <String>] [-Force] -SQLServer <String> [-Instance <String>] [-Port <String>] [-Netlib <String>] -Database <String> [-SQLShare <String>] [<CommonParameters>]  
```  

#### <a name="description"></a>Opis  
 To polecenie cmdlet tworzy nową bazę danych MDT DB skojarzonego z udziałem wdrożenia. Każdego udziału wdrożenia może być skojarzony z tylko jedną bazę danych DB zestawu MDT.  

#### <a name="parameters"></a>Parametry  
 Ta podsekcja zawiera informacje o różnych parametrów, które mogą być używane z **MDTDatabase nowy** polecenia cmdlet.  

##### <a name="-path-string"></a>-Path < ciąg\>  
 Ten parametr określa w pełni kwalifikowana ścieżka programu Windows PowerShell do udziału wdrożenia, do którego nowej bazy danych MDT DB zostaną skojarzone umieszczony.  

> [!NOTE]
>  Jeśli ten parametr nie zostanie podany, do odpowiedniej lokalizacji w obrębie udziału wdrożenia musi domyślny katalog roboczy programu Windows PowerShell.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-force-switchparameter"></a>-Force [< parametr przełącznika\>]  
 Ten parametr określa, że tabele w bazie danych zestawu MDT powinien być tworzony ponownie Jeśli bazy danych określona w *bazy danych* parametr już istnieje. Jeśli ten parametr jest:  

-   Podana, zostanie ponownie utworzony tabel w ramach istniejącego DB zestawu MDT  

-   Pominięty, następnie tabel w ramach istniejącego DB zestawu MDT nie zostanie ponownie utworzona  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość true,** (**ByValue**)|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-sqlserver-string"></a>-SQLServer < ciąg\>  
 Ten parametr określa nazwę komputera z programem SQL Server, w którym zostanie utworzona nowa baza danych DB zestawu MDT.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość true**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-instance-string"></a>-Wystąpienia < ciąg\>  
 Ten parametr określa wystąpienie programu SQL Server, w której zostanie utworzone nowe bazy danych DB zestawu MDT. Jeśli ten parametr zostanie pominięty, bazy danych DB zestaw MDT jest tworzony w domyślnym wystąpieniu programu SQL Server.  

> [!NOTE]
>  Na komputerze z programem SQL Server dla polecenia cmdlet, aby zlokalizować wystąpienia, w tym parametrze musi działać usługa SQL Browser.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-port-string"></a>— Port < ciąg\>  
 Ten parametr określa port TCP do użycia w ramach komunikacji z wystąpieniem serwera SQL określony w *SQLServer* parametru. Domyślny port używany przez program SQL Server jest port 1433. Określ ten parametr, gdy program SQL Server jest skonfigurowany do używania portu innego niż wartość domyślna. Wartość tego parametru musi być zgodna port skonfigurowany dla programu SQL Server.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-netlib-string"></a>-Netlib < ciąg\>  
 Ten parametr określa biblioteki sieciowej SQL używane do komunikacji z wystąpieniem serwera SQL określony w *SQLServer* parametru. Parametr można wybrać jedno z następujących wartości:  

-   **DBNMPNTW**, który służy do określania komunikacji nazwanych potoków  

-   **DBSMSOCN**, który służy do określania TCP/IP gniazda komunikacji  

 Jeśli ten parametr nie zostanie podany, biblioteki sieciowej SQL nazwanych potoków (DBNMPNTW) jest używany.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-database-string"></a>-Bazy danych < ciąg\>  
 Ten parametr określa nazwę bazy danych mogą być tworzone w wystąpieniu programu SQL Server, określona w *wystąpienia* parametru na serwerze SQL określony w *SQLServer* parametru. Domyślna lokalizacja i konwencji nazewnictwa będzie służyć do plików dziennika i bazy danych podczas tworzenia bazy danych.  

 Jeśli baza danych określona w tym parametrze już istnieje, nie zostaną odtworzone bazy danych. Tabele w bazie danych może zostać ponownie utworzone na podstawie *życie* parametru.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość true**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-sqlshare-string"></a>-SQLShare < ciąg\>  
 Ten parametr określa nazwę udostępnionego folderu sieciowego na komputerze, na którym działa program SQL Server. To połączenie jest używany do ustanawiania połączeń zintegrowane zabezpieczenia systemu Windows przy użyciu protokołu potoków nazwanych.  

> [!NOTE]
>  Jeśli ten parametr nie jest uwzględniona, bezpieczne połączenie $ IPC nie zostanie nawiązane. W związku z tym nazwane potoki, które komunikacji z programem SQL Server może zakończyć się niepowodzeniem.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 To polecenie cmdlet obsługuje następujące typowe parametry: *Verbose, Debug, ErrorAction, ErrorVariable, OutBuffer OutVariable, WarningAction* i *WarningVariable.* Aby uzyskać więcej informacji zobacz temat "about_CommonParameters", które można otworzyć, wpisując następujące polecenie, a następnie naciskając klawisz ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>dane wyjściowe  
 To polecenie cmdlet wyświetla **PSObject** typ obiektu bazy danych nowego zestawu MDT, który został utworzony.  

#### <a name="example-1"></a>Przykład 1  

```  
New-MDTDatabase -Path "DS001:" –SQLServer "WDGSQL01" Database "MDTDB" –SQLShare "\\WDGSQL01\MDTShare$"  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie jest tworzony DB MDT o nazwie *MDTDB* w domyślnym wystąpieniu programu SQL Server na komputerze o nazwie *WDG-SQL-01.* Jeśli baza danych już istnieje, nie zostaną odtworzone w tabelach w istniejącej bazy danych. Będzie można nawiązać połączenia przy użyciu domyślnego portu TCP programu SQL Server i w protokole nazwanych potoków.  

#### <a name="example-2"></a>Przykład 2  

```  
New-MDTDatabase -Path "DS001:" –Force –SQLServer "WDGSQL01" –Instance "MDTInstance" Database "MDTDB" –SQLShare "\\WDGSQL01\MDTShare$"  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie jest tworzony DB MDT o nazwie *MDTDB* w wystąpieniu programu SQL Server o nazwie *MDTInstance* na komputerze o nazwie *WDG-SQL-01.* Jeśli baza danych już istnieje, zostaną odtworzone w tabelach w istniejącej bazy danych. Będzie można nawiązać połączenia przy użyciu domyślnego portu TCP programu SQL Server i w protokole nazwanych potoków.  

###  <a name="Remove-MDTMonitorData"></a>Usuń MDTMonitorData  
 W tej sekcji opisano **Get-MDTPersistentDrive** polecenia cmdlet programu Windows PowerShell. Uruchom to polecenie cmdlet z konsoli programu Windows PowerShell, która ma PowerShell zestawu MDT przystawki załadowany. Aby uzyskać więcej informacji na temat sposobu uruchamiania konsoli programu Windows PowerShell, która ma przystawki programu PowerShell zestawu MDT załadowane, zobacz "podczas ładowania zestawu MDT Windows PowerShell przystawki".  

#### <a name="syntax"></a>Składnia  

```  
Remove-MDTMonitorData [-Path <String>] [-ID <Int32>] [<CommonParameters>]  
```  

 — lub —  

```  
Remove-MDTMonitorData [-Path <String>] [-ComputerObject <PSObject>] [<CommonParameters>]  
```  

#### <a name="description"></a>Opis  
 To polecenie cmdlet usuwa istniejące dane monitorowania zbierane w udziału wdrożenia zebranych danych monitorowania. Można zidentyfikować dane monitorowania do usunięcia, określając:  

-   Identyfikator elementu monitorowania udziału określonego wdrożenia. Monitorowania identyfikatory elementów są automatycznie generowane i przypisane do elementu po utworzeniu elementu dla udziału wdrożenia. W pierwszym przykładzie składni przedstawiono użycia.  

-   Obiekt komputera dla elementu monitorowania w udziału wdrożenia. Obiekt komputera można uzyskać za pomocą **Get-MDTMonitorData** polecenia cmdlet. Ostatni przykład składni ilustruje użycia.  

> [!NOTE]
>  Po usunięciu danych monitorowania nie istnieje metoda odzyskiwania informacji.  

#### <a name="parameters"></a>Parametry  
 Ta podsekcja zawiera informacje o różnych parametrów, które mogą być używane z **Get - MDTMonitorData** polecenia cmdlet.  

##### <a name="-path-string"></a>-Path < ciąg\>  
 Ten parametr określa **MDTProvider** dysk programu Windows PowerShell dla udziału wdrożenia odpowiednie.  

> [!NOTE]
>  Jeśli ten parametr nie zostanie podany, do lokalizacji w ramach żądany dysk programu Windows PowerShell MDTProvider musi domyślny katalog roboczy programu Windows PowerShell.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-id-nullable"></a>-ID < wartość null\>  
 Ten parametr określa element danych monitorowania ma zostać usunięty przy użyciu identyfikatora elementu danych monitorowania. Jeśli ten parametr nie jest określony, a następnie *ComputerObject* musi zostać określony parametr, aby zidentyfikować określonego elementu danych monitorowania.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość true,** (**ByValue**)|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-computerobject-psobject"></a>-ComputerObject < PSObject\>  
 Ten parametr określa monitorowania element danych, aby usunąć przy użyciu obiektu komputera. Jeśli ten parametr nie jest określony, a następnie *identyfikator* musi zostać określony parametr, aby zidentyfikować określonego elementu danych monitorowania.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość true,** (**ByValue**)|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 To polecenie cmdlet obsługuje następujące typowe parametry: *Verbose, Debug, ErrorAction, ErrorVariable, OutBuffer OutVariable, WarningAction* i *WarningVariable.* Aby uzyskać więcej informacji zobacz temat "about_CommonParameters", które można otworzyć, wpisując następujące polecenie, a następnie naciskając klawisz ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>dane wyjściowe  
 Może dane wyjściowe tego polecenia cmdlet **ciąg** typu object, jeśli *pełne* wspólnego parametru jest uwzględnione; w przeciwnym razie generowane żadne dane wyjściowe.  

#### <a name="example-1"></a>Przykład 1  

```  
Remove-MDTMonitorData -Path "DS001:" -ID 3  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie usuwa element danych monitorowania z Identyfikatorem, który ma wartość **3** z wdrożenia udziału w ścieżce programu Windows PowerShell DS001:.  

#### <a name="example-2"></a>Przykład 2  

```  
Remove-MDTMonitorData -ID 3  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie usuwa element danych monitorowania z Identyfikatorem, który ma wartość **3** z wdrożenia udział w domyślnej ścieżce środowiska Windows PowerShell.  

#### <a name="example-3"></a>Przykład 3  

```  
$MonitorObject=Get-MDTMonitorData | Where-Object {$_.Name eq 'WDG-REF-01'}  
Remove-MDTMonitorData -ComputerObject $MonitorObject  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie powoduje usunięcie dowolnego elementu danych monitorowania gdzie nazwa komputera jest WDG-REF-01. Obiekt znajduje się za pomocą **Get-MDTMonitorData** polecenia cmdlet i **Where-Object** polecenia cmdlet. Aby uzyskać więcej informacji na temat **Where-Object** polecenia cmdlet, zobacz [za pomocą polecenia Cmdlet Where-Object](http://technet.microsoft.com/library/ee177028.aspx).  

###  <a name="Remove-MDTPersistentDrive"></a>Usuń MDTPersistentDrive  
 W tej sekcji opisano **MDTPersistentDriveWindows Usuń** polecenia cmdlet programu Windows PowerShell. Uruchom to polecenie cmdlet z konsoli programu Windows PowerShell, która ma PowerShell zestawu MDT przystawki załadowany. Aby uzyskać więcej informacji na temat sposobu uruchamiania konsoli programu Windows PowerShell, która ma przystawki programu PowerShell zestawu MDT załadowane, zobacz "podczas ładowania zestawu MDT Windows PowerShell przystawki".  

#### <a name="syntax"></a>Składnia  

```  
Remove-MDTPersistentDrive [-Name] <String> [[-InputObject] <PSObject>] [<CommonParameters>]  
```  

#### <a name="description"></a>Opis  
 To polecenie cmdlet usuwa istniejący dysk utworzony przy użyciu programu Windows PowerShell **MDTProvider** z listy dysków, które są trwałe w konsoli Deployment Workbench lub w sesji środowiska Windows PowerShell przy użyciu [ Przywracanie MDTPersistentDrive](#Restore-MDTPersistentDrive) polecenia cmdlet. To polecenie cmdlet jest wywoływane, gdy udział wdrożenia zostanie zamknięty w (usunięte z) konsoli Deployment Workbench.  

> [!NOTE]
>  Utrwalona, wykaz **MDTProvider** dysków jest przechowywana na użytkownika na podstawie w profilu użytkownika.  

 Utrwalona, wykaz **MDTProvider** dyski są wyświetlane przy użyciu **Get-MDTPersistentDrive** polecenia cmdlet. Dysk MDTProvider można dodać do listy utrwalonego dysków przy użyciu **MDTPersistentDrive Dodaj** polecenia cmdlet.  

#### <a name="parameters"></a>Parametry  
 Ta podsekcja zawiera informacje o różnych parametrów, które mogą być używane z **MDTPersistentDriveWindows Dodaj** polecenia cmdlet.  

##### <a name="-name-string"></a>-Nazwa < ciąg\>  
 Określa nazwę dysk programu Windows PowerShell utworzone przy użyciu dostawcy zestawu MDT i odnosi się do istniejącego udziału wdrożenia. Nazwa została utworzona przy użyciu [elementu PSDrive nowy](http://technet.microsoft.com/library/dd315340.aspx) polecenia cmdlet i określając **MDTProvider** w *PSProvider* parametru.  

 Aby uzyskać więcej informacji na temat sposobu tworzenia nowego środowiska Windows PowerShell dysków przy użyciu **MDTProvider** i sposobu tworzenia wdrożenia udostępnić przy użyciu programu Windows PowerShell, zobacz sekcję "Tworzenie wdrożenia udostępniać za pomocą środowiska Windows PowerShell" w Dokument MDT *Microsoft Deployment Toolkit przykłady Guide*.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość true**|  
|**Pozycja?**|**1** i **o nazwie**|  
|**Wartość domyślna**|**Brak**|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość true,** (**ByValue**)|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-inputobject-psobject"></a>-InputObject < PSObject\>  
 Ten parametr określa obiekt dysk programu Windows PowerShell, który został utworzony wcześniej w procesie. Wprowadź **PSObject** obiekt, taki jak generowane przez [elementu PSDrive nowy](http://technet.microsoft.com/library/dd315340.aspx) polecenia cmdlet.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**2** i **o nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość true,** (**ByValue**)|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 To polecenie cmdlet obsługuje następujące typowe parametry: *Verbose, Debug, ErrorAction, ErrorVariable, OutBuffer OutVariable, WarningAction* i *WarningVariable.* Aby uzyskać więcej informacji zobacz temat "about_CommonParameters", które można otworzyć, wpisując następujące polecenie, a następnie naciskając klawisz ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>dane wyjściowe  
 To polecenie cmdlet nie zawiera żadnych danych wyjściowych.  

#### <a name="example-1"></a>Przykład 1  

```  
Remove-MDTPersistentDrive –Name "DS001:"  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie powoduje usunięcie udziału wdrożenia o nazwie dysk programu Windows PowerShell *DS001* z listy utrwalonego dysków.  

#### <a name="example-2"></a>Przykład 2  

```  
$MDTPSDrive = Get-PSDrive | Where-Object {$_.Root -eq "C:\DeploymentShare" -and $_.Provider -like "*MDTProvider"}   
Remove-MDTPersistentDrive –InputObject $MDTPSDrive  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie usuwa udziału wdrożenia na C:\DeploymentShare$ z listy utrwalonego dysków. **GetPSDrive** i **Where-Object** poleceń cmdlet są używane do zwrócenia, dysk programu Windows PowerShell, aby trwale zestaw MDT **MDTPersistentDrive Usuń** polecenia cmdlet przy użyciu *$MDTPSDrive* zmiennej. Aby uzyskać więcej informacji na temat **Where-Object** polecenia cmdlet, zobacz [za pomocą polecenia Cmdlet Where-Object](http://technet.microsoft.com/library/ee177028.aspx). Aby uzyskać więcej informacji na temat **elementu PSDrive Get** polecenia cmdlet, zobacz [za pomocą polecenia Cmdlet Get-elementu PSDrive](http://technet.microsoft.com/library/ee176856).  

###  <a name="Restore-MDTPersistentDrive"></a>Przywracanie MDTPersistentDrive  
 W tej sekcji opisano **MDTPersistentDrive przywracania** polecenia cmdlet programu Windows PowerShell. Uruchom to polecenie cmdlet z konsoli programu Windows PowerShell, która ma PowerShell zestawu MDT przystawki załadowany. Aby uzyskać więcej informacji na temat sposobu uruchamiania konsoli programu Windows PowerShell, która ma przystawki programu PowerShell zestawu MDT załadowane, zobacz "podczas ładowania zestawu MDT Windows PowerShell przystawki".  

#### <a name="syntax"></a>Składnia  

```  
Restore-MDTPersistentDrive [-Force] [<CommonParameters>]  
```  

#### <a name="description"></a>Opis  
 To polecenie cmdlet przywraca utrwalonego dysk programu Windows PowerShell dla zestawu MDT do listy aktywnych dysk programu Windows PowerShell dla każdego udziału wdrożenia, która została dodana do listy utrwalonego dysków programu Windows PowerShell dla zestawu MDT. Na liście utrwalonego dysków programu Windows PowerShell dla zestawu MDT odbywa się przy użyciu [MDTPersistentDrive Dodaj](#Add-MDTPersistentDrive) i [MDTPersistentDrive Usuń](#Remove-MDTPersistentDrive) poleceń cmdlet lub konsoli Deployment Workbench.  

 To polecenie cmdlet wymaga **elementu PSDrive nowy** , aby utworzyć dysk programu Windows PowerShell dla każdego dysku w zestawie MDT trwałych listy. Utrwalonych dysków programu Windows PowerShell dla zestawu MDT są podobne do mapowania dysków utrwalonego sieci.  

> [!NOTE]
>  Ta lista utrwalonego dysków programu Windows PowerShell dla zestawu MDT jest przechowywany w poszczególnych użytkowników i są przechowywane w profilu użytkownika.  

#### <a name="parameters"></a>Parametry  
 Ta podsekcja zawiera informacje o różnych parametrów, które mogą być używane z **MDTPersistentDrive przywracania** polecenia cmdlet.  

##### <a name="-force-switchparameter"></a>-Force [< parametr przełącznika\>]  
 Ten parametr określa, że udział wdrożenia można uaktualnić po przywróceniu (jeśli jest to wymagane). Jeśli ten parametr jest:  

-   Dostępne, a następnie udziału wdrożenia zostanie uaktualniony po przywróceniu (jeśli jest to wymagane)  

-   Pominięty, następnie udziału wdrożenia nie zostanie uaktualniony po przywróceniu  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość true,** (**ByValue**)|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 To polecenie cmdlet obsługuje następujące typowe parametry: *Verbose, Debug, ErrorAction, ErrorVariable, OutBuffer OutVariable, WarningAction* i *WarningVariable.* Aby uzyskać więcej informacji zobacz temat "about_CommonParameters", które można otworzyć, wpisując następujące polecenie, a następnie naciskając klawisz ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>dane wyjściowe  
 To polecenie cmdlet wyświetla **PSObject** obiekt typu dla każdego dysku MDT dostawcy Windows PowerShell, który zostanie przywrócony.  

#### <a name="example-1"></a>Przykład 1  

```  
Get-MDTPersistentDrive  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie przywraca listy zestawu MDT utrwalone dysków, tworząc środowiska Windows PowerShell dysków przy użyciu **MDTProvider** typu. Po przywróceniu udziału wdrożenia nie zostaną uaktualnione.  

#### <a name="example-2"></a>Przykład 2  

```  
Get-MDTPersistentDrive -Force  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie przywraca listy zestawu MDT utrwalone dysków, tworząc środowiska Windows PowerShell dysków przy użyciu **MDTProvider** typu. Udział wdrożenia zostanie uaktualniony po przywróceniu (jeśli jest to wymagane).  

###  <a name="Set-MDTMonitorData"></a>Zestaw MDTMonitorData  
 W tej sekcji opisano **Get-MDTPersistentDrive** polecenia cmdlet programu Windows PowerShell. Uruchom to polecenie cmdlet z konsoli programu Windows PowerShell, która ma PowerShell zestawu MDT przystawki załadowany. Aby uzyskać więcej informacji na temat sposobu uruchamiania konsoli programu Windows PowerShell, która ma przystawki programu PowerShell zestawu MDT załadowane, zobacz "podczas ładowania zestawu MDT Windows PowerShell przystawki".  

#### <a name="syntax"></a>Składnia  

```  
Set-MDTMonitorData [-Path <String>] [-ComputerObject <PSObject>] [-Settings <Hashtable>] [<CommonParameters>]  
```  

 — lub —  

```  
Set-MDTMonitorData [-Path <String>] [-MacAddress <String>] [Settings <Hashtable>] [<CommonParameters>]  
```  

#### <a name="description"></a>Opis  
 To polecenie cmdlet tworzy nowy element danych monitorowania lub aktualizuje istniejący monitorowania element danych, w udziału wdrożenia. Można zidentyfikować dane monitorowania do usunięcia, określając:  

-   Obiekt komputera dla elementu monitorowania w udziału wdrożenia. Obiekt komputera można uzyskać za pomocą **Get-MDTMonitorData** polecenia cmdlet. W pierwszym przykładzie składni przedstawiono użycia.  

-   Adres MAC karty sieciowej podstawowego elementu monitorowania udziału określonego wdrożenia. Adres MAC jest automatycznie przypisany do monitorowania elementu danych, po utworzeniu elementu dla udziału wdrożenia. Ostatni przykład składni ilustruje użycia.  

> [!NOTE]
>  Po usunięciu danych monitorowania nie istnieje metoda odzyskiwania informacji.  

#### <a name="parameters"></a>Parametry  
 Ta podsekcja zawiera informacje o różnych parametrów, które mogą być używane z **Get - MDTMonitorData** polecenia cmdlet.  

##### <a name="-path-string"></a>-Path < ciąg\>  
 Ten parametr określa dysk programu Windows PowerShell MDTProvider udziału wdrożenia odpowiednie.  

> [!NOTE]
>  Jeśli ten parametr nie zostanie podany, do lokalizacji w ramach żądany dysk programu Windows PowerShell MDTProvider musi domyślny katalog roboczy programu Windows PowerShell.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-computerobject-psobject"></a>-ComputerObject < PSObject\>  
 Ten parametr określa element danych monitorowania, należy utworzyć lub zaktualizować za pomocą obiektu komputera. Jeśli ten parametr nie jest określony, a następnie *MACAddress* musi zostać określony parametr, aby zidentyfikować określonego elementu danych monitorowania.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość true,** (**ByValue**)|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-macaddress-string"></a>-MACAddress < ciąg\>  
 Ten parametr określa element danych monitorowania, należy utworzyć lub zaktualizować za pomocą adresu MAC karty sieciowej głównej monitorowanego komputera. Format MACAddress jest *xx:xx:xx:xx:xx:xx,* gdzie *x* znaków szesnastkowych określono w wielkie litery (zgodnie z wymaganiami). Jeśli ten parametr nie jest określony, a następnie *ComputerObject* musi zostać określony parametr, aby zidentyfikować określonego elementu danych monitorowania.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość true,** (**ByValue**)|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-settings-hashtable"></a>-Ustawienia < Hashtable\>  
 Ten parametr określa ustawienia monitorowania danych monitorowania elementu danych do można utworzyć lub zaktualizować. Format hashtable udostępniane z tym parametrem jest `@{"Setting"="Value"; "Setting1"="Value1"; "Setting2"="Value2}`. Jeśli ten parametr nie jest określony, to zostanie utworzony element danych monitorowania, ale będą przechowywane żadne informacje monitorowania.  

 `"Setting"`może być dowolną właściwość wymieniona w pliku ZTIGather.xml. `Value`może mieć dowolną prawidłową wartość dla określonego właściwości w `"Setting"`.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość true,** (**ByValue**)|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 To polecenie cmdlet obsługuje następujące typowe parametry: *Verbose, Debug, ErrorAction, ErrorVariable, OutBuffer OutVariable, WarningAction* i *WarningVariable.* Aby uzyskać więcej informacji zobacz temat "about_CommonParameters", które można otworzyć, wpisując następujące polecenie, a następnie naciskając klawisz ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>dane wyjściowe  
 To polecenie cmdlet nie generuje żadnego wyniku.  

#### <a name="example-1"></a>Przykład 1  

```  
$MonitorObject=Get-MDTMonitorData | Where-Object {$_.Name eq 'WDG-REF-01'}  
Set-MDTMonitorData -ComputerObject $MonitorObject Setting @{"OSDComputerName"="WDG-MDT-01";"SkipWizard"="YES"}  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie powoduje usunięcie dowolnego elementu danych monitorowania gdzie nazwa komputera jest *WDG-REF-01.* Obiekt znajduje się za pomocą **Get-MDTMonitorData** polecenia cmdlet i **Where-Object** polecenia cmdlet. Aby uzyskać więcej informacji na temat **Where-Object** polecenia cmdlet, zobacz [za pomocą polecenia Cmdlet Where-Object](http://technet.microsoft.com/library/ee177028.aspx). [OSDComputerName](#OSDComputerName) właściwości jest rejestrowany jako mający wartość **WDG-MDT-01**i [SkipWizard](#SkipWizard) właściwości jest rejestrowany jako mający wartość **tak**.  

#### <a name="example-2"></a>Przykład 2  

```  
Set-MDTMonitorData -MACAddress "00:11:22:33:44:55" MonitorObject Setting @{"OSDComputerName"="WDG-MDT-01";"SkipWizard"="YES"}  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie tworzy lub aktualizuje element danych monitorowania z **MACAddress** , który ma wartość **00:11:22:33:44:55**. [OSDComputerName](#OSDComputerName) właściwości jest rejestrowany jako mający wartość **WDG-MDT-01**i [SkipWizard](#SkipWizard) właściwości jest rejestrowany jako mający wartość **tak**.  

###  <a name="Test-MDTDeploymentShare"></a>MDTDeploymentShare testu  
 Mimo że to polecenie cmdlet jest zwracany za pomocą **Get-Command** polecenia cmdlet jako w przystawce Microsoft.BDD.PSSnapIn, nie zostały zaimplementowane.  

###  <a name="Test-MDTMonitorData"></a>MDTMonitorData testu  
 W tej sekcji opisano **MDTMonitorData testu** polecenia cmdlet programu Windows PowerShell. Uruchom to polecenie cmdlet z konsoli programu Windows PowerShell, która ma PowerShell zestawu MDT przystawki załadowany. Aby uzyskać więcej informacji na temat sposobu uruchamiania konsoli programu Windows PowerShell, która ma przystawki programu PowerShell zestawu MDT załadowane, zobacz "podczas ładowania zestawu MDT Windows PowerShell przystawki".  

#### <a name="syntax"></a>Składnia  

```  
Test-MDTMonitorData -ServerName <String> -EventPort <Int32> -DataPort <Int32> [<CommonParameters>]  
```  

#### <a name="description"></a>Opis  
 To polecenie cmdlet sprawdza, czy zestaw MDT monitorowanie usługi, w którym jest uruchomiona na komputerze, na którym jest zainstalowany zestaw MDT, jest włączona i uruchomiona poprawnie. Zestaw MDT Usługa monitorowania zbiera informacje monitorowania, które mogą być wyświetlane:  

-   W węźle Monitorowanie w konsoli Deployment Workbench udział wdrożenia  

-   Przy użyciu [Get-MDTMonitorData](#Get-MDTMonitorData) polecenia cmdlet  

 Zestaw MDT monitorowanie usługi można wyłączyć przy użyciu [MDTMonitorService Wyłącz](#Disable-MDTMonitorService). Monitorowanie informacje mogą być zapisywane do zestawu MDT monitorowania usługi przy użyciu [MDTMonitorData zestaw](#Set-MDTMonitorData) polecenia cmdlet.  

> [!NOTE]
>  Dla tego polecenia cmdlet funkcji prawidłowo musi istnieć co najmniej jeden element danych monitorowania zestawu MDT w udziału wdrożenia. Jeśli nie zarejestrowano żadnych MDT monitorowania informacji udziału wdrożenia zakończy się niepowodzeniem testu.  

 Aby uzyskać więcej informacji na temat zestaw MDT monitorowanie usługi, zobacz sekcję "Monitorowania wdrożenia zestawu MDT" w dokumencie MDT *przy użyciu programu Microsoft Deployment Toolkit*.  

#### <a name="parameters"></a>Parametry  
 Ta podsekcja zawiera informacje o różnych parametrów, które mogą być używane z **MDTMonitorData testu** polecenia cmdlet.  

##### <a name="-server-string"></a>— Serwer < ciąg\>  
 Określa nazwę komputera, na którym jest zainstalowany zestaw MDT i działa MDT monitorowanie usługi.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość true**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|Brak|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-dataport-int32"></a>— Port danych < Int32\>  
 Ten parametr określa TCP port używany jako port danych dla zestawu MDT, monitorowanie usługi.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość true**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-eventport-int32"></a>-EventPort < Int32\>  
 Ten parametr określa TCP port używany jako port zdarzeń dla zestawu MDT, monitorowanie usługi.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość true**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 To polecenie cmdlet obsługuje następujące typowe parametry: *Verbose, Debug, ErrorAction, ErrorVariable, OutBuffer OutVariable, WarningAction* i *WarningVariable.* Aby uzyskać więcej informacji zobacz temat "about_CommonParameters", które można otworzyć, wpisując następujące polecenie, a następnie naciskając klawisz ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>dane wyjściowe  
 To polecenie cmdlet wyświetla wartość logiczna, która reprezentuje Powodzenie (true) lub Niepowodzenie (false) tekst.  

#### <a name="example-1"></a>Przykład 1  

```  
Test-MDTMonitorData -Server "WDG-MDT-01" -DataPort "9801" EventPort "9800"  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie sprawdza, czy zestaw MDT monitorowanie usługi na WDG-MDT-01 jest zainstalowana i uruchomiona. Polecenia cmdlet Sprawdź przy użyciu portu danych 9801 i portem zdarzeń 9800.  

###  <a name="Update-MDTDatabaseSchema"></a>MDTDatabaseSchema aktualizacji  
 W tej sekcji opisano **MDTDatabaseSchema aktualizacji** polecenia cmdlet programu Windows PowerShell. Uruchom to polecenie cmdlet z konsoli programu Windows PowerShell, która ma PowerShell zestawu MDT przystawki załadowany. Aby uzyskać więcej informacji na temat sposobu uruchamiania konsoli programu Windows PowerShell, która ma przystawki programu PowerShell zestawu MDT załadowane, zobacz "podczas ładowania zestawu MDT Windows PowerShell przystawki".  

#### <a name="syntax"></a>Składnia  

```  
Update-MDTDatabaseSchema -SQLServer <String> [-Instance <String>] [-Port <String>] [-Netlib <String>] -Database <String> [-SQLShare <String>] [<CommonParameters>]  
```  

#### <a name="description"></a>Opis  
 To polecenie cmdlet aktualizuje istniejącą bazę danych MDT DB do najnowszej wersji schematu bazy danych DB zestawu MDT. Każdego udziału wdrożenia może być skojarzony z tylko jedną bazę danych DB zestawu MDT.  

 To polecenie cmdlet automatycznie jest wywoływane, gdy trwa uaktualnianie udziału wdrożenia, takie jak czas uruchamiania [MDTPersistentDrive przywracania](#Restore-MDTPersistentDrive) polecenia cmdlet z *życie* parametru i [ Aktualizacja MDTDeploymentShare](#Update-MDTDeploymentShare) polecenia cmdlet.  

#### <a name="parameters"></a>Parametry  
 Ta podsekcja zawiera informacje o różnych parametrów, które mogą być używane z **MDTDatabaseSchema uaktualnienia** polecenia cmdlet.  

##### <a name="-sqlserver-string"></a>-SQLServer < ciąg\>  
 Ten parametr określa nazwę komputera z programem SQL Server, w której będzie można uaktualnić bazy danych DB zestawu MDT.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość true**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-instance-string"></a>-Wystąpienia < ciąg\>  
 Ten parametr określa wystąpienie programu SQL Server, na którym znajduje się baza danych MDT DB do uaktualnienia. Jeśli ten parametr zostanie pominięty, następnie bazy danych MDT DB zakłada się, że w domyślnym wystąpieniu programu SQL Server.  

> [!NOTE]
>  Na komputerze z programem SQL Server dla polecenia cmdlet, aby zlokalizować wystąpienia, w tym parametrze musi działać usługa SQL Browser.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-port-string"></a>— Port < ciąg\>  
 Ten parametr określa port TCP do użycia w ramach komunikacji z wystąpieniem serwera SQL określony w *SQLServer* parametru. Domyślny port używany przez program SQL Server jest port 1433. Określ ten parametr, gdy program SQL Server jest skonfigurowany do używania portu innego niż wartość domyślna. Wartość tego parametru musi być zgodna port skonfigurowany dla programu SQL Server.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-netlib-string"></a>-Netlib < ciąg\>  
 Ten parametr określa biblioteki sieciowej SQL, który jest używany w komunikacji z wystąpieniem serwera SQL określony w *SQLServer* parametru. Parametr można wybrać jedno z następujących wartości:  

-   **DBNMPNTW**, który służy do określania komunikacji nazwanych potoków  

-   **DBSMSOCN**, który służy do określania TCP/IP gniazda komunikacji  

 Jeśli ten parametr nie zostanie podany, biblioteka sieciowa nazwanych potoków SQL (**DBNMPNTW**) jest używany.  

> [!NOTE]
>  Konsoli Deployment Workbench nie udostępnia opcję konfigurowania biblioteki sieciowe SQL. Konsoli Deployment Workbench zawsze używa komunikacji nazwanych potoków. Jednak można skonfigurować w pliku CustomSettings.ini SQL biblioteki sieciowej.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-database-string"></a>-Bazy danych < ciąg\>  
 Ten parametr określa nazwę bazy danych do uaktualnienia w wystąpieniu serwera SQL określony w *wystąpienia* parametru w określonym w wystąpieniu programu SQL Server *SQLServer* parametru.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość true**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 To polecenie cmdlet obsługuje następujące typowe parametry: *Verbose, Debug, ErrorAction, ErrorVariable, OutBuffer OutVariable, WarningAction* i *WarningVariable.* Aby uzyskać więcej informacji zobacz temat "about_CommonParameters", które można otworzyć, wpisując następujące polecenie, a następnie naciskając klawisz ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>dane wyjściowe  
 To polecenie cmdlet wyświetla **PSObject** obiekt typu dla zestawu MDT bazy danych, który został uaktualniony. To polecenie cmdlet również Wyświetla **ciąg** typu danych, jeśli *pełne* wspólnego parametru jest dołączony.  

#### <a name="example-1"></a>Przykład 1  

```  
Update-MDTDatabaseSchema –SQLServer "WDGSQL01" Database "MDTDB"   
```  

##### <a name="description"></a>Opis  
 W tym przykładzie aktualizacje schematu dla zestawu MDT bazy danych o nazwie *MDTDB* w domyślnym wystąpieniu programu SQL Server na komputerze o nazwie *WDG-SQL-01.* Połączenie zostanie nawiązane z wystąpieniem programu SQL Server przy użyciu domyślnego portu TCP i w protokole nazwanych potoków.  

#### <a name="example-2"></a>Przykład 2  

```  
Update-MDTDatabaseSchema –SQLServer "WDGSQL01" –Instance "MDTInstance" -Port "6333" Database "MDTDB"  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie aktualizacje schematu dla zestawu MDT bazy danych o nazwie *MDTDB* w wystąpieniu programu SQL Server o nazwie *MDTInstance* na komputerze o nazwie *WDG-SQL-01.* Połączenie zostanie nawiązane serwer SQL używa portu TCP 6333 i w protokole nazwanych potoków.  

###  <a name="Update-MDTDeploymentShare"></a>MDTDeploymentShare aktualizacji  
 W tej sekcji opisano **MDTDeploymentShare aktualizacji** polecenia cmdlet programu Windows PowerShell. Uruchom to polecenie cmdlet z konsoli programu Windows PowerShell, która ma PowerShell zestawu MDT przystawki załadowany. Aby uzyskać więcej informacji na temat sposobu uruchamiania konsoli programu Windows PowerShell, która ma przystawki programu PowerShell zestawu MDT załadowane, zobacz "podczas ładowania zestawu MDT Windows PowerShell przystawki".  

#### <a name="syntax"></a>Składnia  

```  
Update-MDTDeploymentShare [-Path <String>] [-Force] [Compress] [<CommonParameters>]  
```  

#### <a name="description"></a>Opis  
 To polecenie cmdlet aktualizacji istniejącego udziału wdrożenia przy użyciu najnowszych plików z zestawu Windows ADK. To polecenie cmdlet również aktualizacji lub ponownie wygenerować wymagane obrazy rozruchowe Windows PE w formatach plików WIM jak ISO.  

#### <a name="parameters"></a>Parametry  
 Ta podsekcja zawiera informacje o różnych parametrów, które mogą być używane z **MDTDeploymentShare aktualizacji** polecenia cmdlet.  

##### <a name="-path-string"></a>-Path < ciąg\>  
 Ten parametr określa pełną ścieżkę do istniejącego folderu w udziale wdrożenia, która jest aktualizowana.  

> [!NOTE]
>  Jeśli ten parametr nie zostanie podany, do odpowiedniej lokalizacji w obrębie udziału wdrożenia musi domyślny katalog roboczy programu Windows PowerShell.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-force-switchparameter"></a>-Force [< parametr przełącznika\>]  
 Ten parametr określa, czy obrazy rozruchowe Windows PE (pliki .iso i wim) udziału wdrożenia powinien zostać odświeżony. Jeśli ten parametr jest:  

-   Dostępne, a następnie polecenie cmdlet tworzy nowe wersje obrazy rozruchowe Windows PE. Ten proces trwa dłużej niż optymalizacji istniejących obrazów rozruchowych środowiska Preinstalacyjnego systemu Windows.  

-   Pominięty, następnie polecenia cmdlet optymalizuje istniejących obrazów rozruchowych środowiska Preinstalacyjnego systemu Windows. Ten proces trwa krócej niż generowanie nowych wersji obrazy rozruchowe Windows PE. Jeśli ten parametr zostanie pominięty, *Kompresuj* parametru pozwala zmniejszyć rozmiar obrazów rozruchowych jako część procesu optymalizacji obrazu rozruchowego środowiska Windows PE.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość true,** (**ByValue**)|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="-compress-switchparameter"></a>-Kompresuj [< parametr przełącznika\>]  
 Ten parametr określa, czy obrazy rozruchowe Windows PE (pliki .iso i wim) udziału wdrożenia powinien być kompresowany są zoptymalizowane pod (bez *życie* parametru). Jeśli ten parametr jest:  

-   Podany, a następnie polecenia cmdlet kompresuje obrazy rozruchowe Windows PE, zgodnie z ich optymalizację  

-   Pominięty, następnie polecenia cmdlet nie Kompresuj obrazy rozruchowe Windows PE zgodnie z ich optymalizację  

> [!NOTE]
>  Ten parametr powinien zostać podany, jeśli *życie* nie podano parametru. Jeśli *życie* dołączono parametr, nowych obrazów rozruchowych środowiska Preinstalacyjnego systemu Windows są generowane i są kompresowane, minimalny rozmiar.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość false**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość true,** (**ByValue**)|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 To polecenie cmdlet obsługuje następujące typowe parametry: *Verbose, Debug, ErrorAction, ErrorVariable, OutBuffer OutVariable, WarningAction* i *WarningVariable.* Aby uzyskać więcej informacji zobacz temat "about_CommonParameters", które można otworzyć, wpisując następujące polecenie, a następnie naciskając klawisz ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>dane wyjściowe  
 To polecenie cmdlet wyświetla **ciąg** typu danych i daje dodatkowe **ciąg** typu danych, jeśli *pełne* wspólnego parametru jest dołączony.  

#### <a name="example-1"></a>Przykład 1  

```  
Update-MDTDepoymentShare   
```  

##### <a name="description"></a>Opis  
 W tym przykładzie aktualizuje udziału wdrożenia w katalogu roboczego programu Windows PowerShell. Obrazy rozruchowe Windows PE zostanie zoptymalizowane. Obrazy rozruchowe Windows PE nie zostanie skompresowany.  

#### <a name="example-2"></a>Przykład 2  

```  
Update-MDTDepoymentShare -Path "DS001:"  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie aktualizacji na dysk programu Windows PowerShell dla zestawu MDT o nazwie udziału wdrożenia *DS001:.* Obrazy rozruchowe Windows PE zostanie zoptymalizowane. Obrazy rozruchowe Windows PE nie zostanie skompresowany.  

#### <a name="example-3"></a>Przykład 3  

```  
Update-MDTDepoymentShare -Path "DS001:" -Compress  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie aktualizacji na dysk programu Windows PowerShell dla zestawu MDT o nazwie udziału wdrożenia *DS001:.* Obrazy rozruchowe Windows PE zostanie zoptymalizowane. Obrazy rozruchowe Windows PE zostaną skompresowane.  

#### <a name="example-4"></a>Przykład 4  

```  
Update-MDTDepoymentShare -Path "DS001:" -Force  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie aktualizacji na dysk programu Windows PowerShell dla zestawu MDT o nazwie udziału wdrożenia *DS001:.* Nowe wersje środowiska Windows PE obrazów rozruchowych zostanie wygenerowany.  

###  <a name="Update-MDTLinkedDS"></a>MDTLinkedDS aktualizacji  
 W tej sekcji opisano **MDTLinkedDS aktualizacji** polecenia cmdlet programu Windows PowerShell. Uruchom to polecenie cmdlet z konsoli programu Windows PowerShell, która ma PowerShell zestawu MDT przystawki załadowany. Aby uzyskać więcej informacji na temat sposobu uruchamiania konsoli programu Windows PowerShell, która ma przystawki programu PowerShell zestawu MDT załadowane, zobacz "podczas ładowania zestawu MDT Windows PowerShell przystawki".  

#### <a name="syntax"></a>Składnia  

```  
Update-MDTLinkedDS -Path <String> [<CommonParameters>]  
```  

#### <a name="description"></a>Opis  
 To polecenie cmdlet replikuje zawartość z udziału wdrożenia do udziału wdrożenia połączone za pomocą profilu wyboru używane do definiowania udziału wdrożenia połączone. Zachowanie replikacji jest określany na podstawie ustawień konfiguracji dla udziału wdrożenia połączony.  

#### <a name="parameters"></a>Parametry  
 Ta podsekcja zawiera informacje o różnych parametrów, które mogą być używane z **MDTLinkedDS aktualizacji** polecenia cmdlet.  

##### <a name="-path-string"></a>-Path < ciąg\>  
 Ten parametr określa w pełni kwalifikowana ścieżka do udziału wdrożenia połączone, która jest aktualizowana.  

> [!NOTE]
>  Jeśli ten parametr nie zostanie podany, do odpowiedniej lokalizacji w obrębie udziału wdrożenia musi domyślny katalog roboczy programu Windows PowerShell.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość true**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 To polecenie cmdlet obsługuje następujące typowe parametry: *Verbose, Debug, ErrorAction, ErrorVariable, OutBuffer OutVariable, WarningAction* i *WarningVariable.* Aby uzyskać więcej informacji zobacz temat "about_CommonParameters", które można otworzyć, wpisując następujące polecenie, a następnie naciskając klawisz ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>dane wyjściowe  
 To polecenie cmdlet wyświetla **ciąg** typu danych i daje dodatkowe **ciąg** typu danych, jeśli *pełne* wspólnego parametru jest dołączony.  

#### <a name="example-1"></a>Przykład 1  

```  
Update-MDTLinkedDS -Path "DS001:\Linked Deployment Shares\LINKED001"  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie replikuje zawartość z udziału wdrożenia na udział wdrożenia połączonych w folderze DS001:\Linked Deployment Shares\LINKED001 ścieżkę programu Windows PowerShell.  

###  <a name="Update-MDTMedia"></a>MDTMedia aktualizacji  
 W tej sekcji opisano **MDTMedia aktualizacji** polecenia cmdlet programu Windows PowerShell. Uruchom to polecenie cmdlet z konsoli programu Windows PowerShell, która ma PowerShell zestawu MDT przystawki załadowany. Aby uzyskać więcej informacji na temat sposobu uruchamiania konsoli programu Windows PowerShell, która ma przystawki programu PowerShell zestawu MDT załadowane, zobacz "podczas ładowania zestawu MDT Windows PowerShell przystawki".  

#### <a name="syntax"></a>Składnia  

```  
Update-MDTMedia -Path <String> [<CommonParameters>]  
```  

#### <a name="description"></a>Opis  
 To polecenie cmdlet replikuje zawartość z udziału wdrożenia do folderu, który zawiera nośnik wdrażania przy użyciu profilu wyboru używane do definiowania nośników wdrażania. Zachowanie replikacji jest określany na podstawie ustawień konfiguracji dla nośnika wdrażania.  

 Nośnik w programie LTI umożliwia wykonywanie wdrożenia LTI wyłącznie z nośnika lokalnego bez konieczności nawiązywania połączenia udziału wdrożenia. Nośnik można przechowywać na dysku DVD, USB dysk twardy lub inne przenośne urządzenie. Po utworzeniu nośnika generowanie obrazów rozruchowych WIM umożliwiających wdrożenia można wykonać z urządzeń przenośnych nośników dostępne lokalnie na komputerze docelowym.  

#### <a name="parameters"></a>Parametry  
 Ta podsekcja zawiera informacje o różnych parametrów, które mogą być używane z **MDTMedia aktualizacji** polecenia cmdlet.  

##### <a name="-path-string"></a>-Path < ciąg\>  
 Ten parametr określa w pełni kwalifikowana ścieżka do folderu, który zawiera nośnik wdrażania, która jest aktualizowana.  

> [!NOTE]
>  Jeśli ten parametr nie zostanie podany, do odpowiedniej lokalizacji w obrębie udziału wdrożenia musi domyślny katalog roboczy programu Windows PowerShell.  

|**Parametr**|**Wartość**|  
|-|-|  
|**Wymagane?**|**Wartość true**|  
|**Pozycja?**|**O nazwie**|  
|**Wartość domyślna**|—|  
|**Akceptowanie danych wejściowych potoku?**|**Wartość false**|  
|**Akceptowanie symboli wieloznacznych?**|**Wartość false**|  

##### <a name="commonparameters"></a>< CommonParameters\>  
 To polecenie cmdlet obsługuje następujące typowe parametry: *Verbose, Debug, ErrorAction, ErrorVariable, OutBuffer OutVariable, WarningAction* i *WarningVariable.* Aby uzyskać więcej informacji zobacz temat "about_CommonParameters", które można otworzyć, wpisując następujące polecenie, a następnie naciskając klawisz ENTER:  

```  
Get-Help about_CommonParameters  
```  

#### <a name="outputs"></a>dane wyjściowe  
 To polecenie cmdlet wyświetla **ciąg** typu danych i daje dodatkowe **ciąg** typu danych, jeśli *pełne* wspólnego parametru jest dołączony.  

#### <a name="example-1"></a>Przykład 1  

```  
Update-MDTMedia -Path "DS001:\Media\MEDIA001"  
```  

##### <a name="description"></a>Opis  
 W tym przykładzie replikuje zawartość z udziału wdrożenia do folderu zawierającego nośników wdrażania w folderze DS001:\Media \MEDIA001 ścieżki programu Windows PowerShell.  

## <a name="tables-and-views-in-the-mdt-db"></a>Tabele i widoki w bazie danych zestawu MDT  
 W zestawie MDT, wiele ustawień właściwości mogą być przechowywane z (zazwyczaj skonfigurowany w pliku CustomSettings.ini) w bazie danych. Konfigurowanie właściwości w bazie danych pomaga utworzyć ogólnego pliku CustomSettings.ini, który wymaga mniejszej liczby modyfikacji i zezwala na jeden plik CustomSettings.ini do użycia w więcej obrazów (ponieważ plik jest bardziej ogólnym).  

 Dostosowywanie bazy danych w węźle bazy danych w konsoli Deployment Workbench. Przy użyciu konsoli Deployment Workbench, ustawienia wdrożenia można konfigurować i zapisywane w tabelach.  

 Jednak zapytań o dane w tabelach są wykonywane przy użyciu widoków. Widoki ułatwić zapytania, dołączając wyniki z wielu tabel. Widoki zwrócić zestaw wyników zapytania ZTIGather.wsf **parametry** i **ParameterCondition** Określ właściwości.  

### <a name="tables-in-the-mdt-db"></a>Tabele w bazie danych zestawu MDT  
 W poniższej tabeli wymieniono tabele baz danych, które konsoli Deployment Workbench tworzy i którymi zarządza.  

|**Tabela**|**Opis**|  
|-|-|  
|ComputerIdentity|Używany do identyfikowania określonego komputera przy użyciu dowolnej kombinacji **AssetTag, identyfikatora UUID, numer seryjny**, i **MACAddress** właściwości. W tabeli przedstawiono **opis** kolumny, aby zapewnić przyjazny dla użytkownika metoda opisujące komputera (zazwyczaj nazwa komputera).|  
|Opisy|Zawiera opis wszystkich właściwości, które można konfigurować za pośrednictwem bazy danych.|  
|LocationIdentity|Umożliwia określenie lokalizacji geograficznych przy użyciu **lokalizacji** właściwości. Wartości dla tej właściwości są przechowywane w odpowiadającej mu kolumny w tabeli.|  
|LocationIdentity_DefaultGateway|Z lokalizacji określonej w tabeli LocationIdentity odnosi się wartości bramy domyślnej. Brak relacji jeden do wielu między tej tabeli i LocationIdentity tabeli.|  
|MakeModelIdentity|Używany do identyfikowania określonego producenta i modelu komputera przy użyciu **upewnij** i **modelu** właściwości. Wartości tych właściwości są przechowywane w odpowiedniej kolumny w tabeli.|  
|PackageMapping|Używane do kojarzenia nazwy w elemencie apletu Dodaj lub usuń programy w Panelu sterowania z pakietu programu Configuration Manager i programu do wdrożenia zamiast aplikacji w Dodaj lub usuń programy. Aby uzyskać więcej informacji dotyczących tej tabeli, zobacz sekcję "Wdrażanie aplikacji oparta na starszej wersji aplikacji", w dokumentacji zestawu MDT *Microsoft Deployment Toolkit przykłady Guide.*|  
|RoleIdentity|Umożliwia identyfikowanie przeznaczenia komputera lub użytkowników przy użyciu komputera **roli** właściwości. Wartości dla tej właściwości są przechowywane w odpowiadającej mu kolumny w tabeli.|  
|Ustawienia|Określa ustawienia, które są stosowane do pojedynczego komputera lub grupy komputerów, zgodnie z ustawieniami w lokalizacjach komputerów, role i upewnij i modelu węzłów w węźle bazy danych w konsoli Deployment Workbench.|  
|Settings_Administrators|Wskazuje, że konto użytkownika ma zostać dodany do lokalnej grupy administratorów na komputerze docelowym, zgodnie z ustawieniami w komputerach, ról, lokalizacji, a producent i Model węzłów w węźle bazy danych w konsoli Deployment Workbench.|  
|Settings_Applications|Identyfikuje aplikacje wdrażane na komputerze docelowym, zgodnie z ustawieniami w komputerach, ról, lokalizacji, a producent i Model węzłów w węźle bazy danych w konsoli Deployment Workbench.|  
|Settings_Packages|Identyfikuje pakiety do wdrażania na komputerze docelowym, zgodnie z ustawieniami w komputerach, ról, lokalizacji, a producent i Model węzłów w węźle bazy danych w konsoli Deployment Workbench.|  
|Settings_Roles|Określa role, które ma zostać skojarzony z komputerem docelowym, zgodnie z ustawieniami w lokalizacjach, komputery, a producent i Model węzłów w węźle bazy danych w konsoli Deployment Workbench.|  

### <a name="views-in-the-mdt-db"></a>Widoki w bazie danych zestawu MDT  
 Poniższa tabela zawiera listę oraz opis widoków bazy danych, które są używane podczas wykonywania zapytania w bazie danych zestawu MDT informacje o konfiguracji.  

|**Widok**|**Opis**|  
|-|-|
|ComputerAdministrators|Użyć w celu znalezienia wszystkich kont, które ma zostać wykonane członków lokalnej grupy Administratorzy na komputerze docelowym. Widok jest sprzężenie tabel ComputerIdentity i Settings_Administrators.|  
|ComputerApplications|Użyć w celu znalezienia wszystkich aplikacji w celu wdrażania na komputerze docelowym. Widok jest sprzężenie tabel ComputerIdentity i Settings_Applications.|  
|ComputerPackages|Użyć w celu znalezienia wszystkich pakietów do wdrażania na komputerze docelowym. Widok jest sprzężenie tabel ComputerIdentity i Settings_Packages.|  
|ComputerRoles|Użyć w celu znalezienia wszystkich ról, które mają być skojarzone z komputera docelowego. Widok jest sprzężenie tabel ComputerIdentity i Settings_Roles.|  
|ComputerSettings|Użyć w celu znalezienia wszystkich ustawień właściwości można skonfigurować dla komputera docelowego. Widok jest sprzężenie tabel ComputerIdentity i ustawień.|  
|LocationAdministrators|Użyć w celu znalezienia wszystkich kont, które ma zostać wykonane członkiem lokalnej grupy Administratorzy na komputerach docelowych w danej lokalizacji. Widok jest sprzężenie tabel LocationIdentity, LocationIdentity_DefaultGateway i Settings_Administrators.|  
|LocationApplications|Umożliwia znalezienie wszystkie aplikacje wdrażane na komputerach docelowych w danej lokalizacji. Widok jest sprzężenie tabel LocationIdentity, LocationIdentity_DefaultGateway i Settings_Applications.|  
|LocationPackages|Użyć w celu znalezienia wszystkich pakietów do wdrażania na komputerach docelowych w danej lokalizacji. Widok jest sprzężenie tabel LocationIdentity, LocationIdentity_DefaultGateway i Settings_Packages.|  
|LocationRoles|Użyć w celu znalezienia wszystkich ról, które mają być skojarzone z komputerów docelowych w danej lokalizacji. Widok jest sprzężenie tabel LocationIdentity, LocationIdentity_DefaultGateway i Settings_Roles.|  
|Lokalizacje|Umożliwia znalezienie adresów IP dla bramy domyślnej w ramach danej lokalizacji lub dla wszystkich lokalizacji, które zawierają określony adres IP bramy domyślnej. Widok jest sprzężenie tabel LocationIdentity i LocationIdentity_DefaultGateway.|  
|LocationSettings|Użyć w celu znalezienia wszystkich właściwości ustawień można skonfigurować dla komputerów docelowych w danej lokalizacji. Widok jest sprzężenie tabel LocationIdentity, LocationIdentity_DefaultGateway i ustawienia.|  
|MakeModelAdministrators|Użyć w celu znalezienia wszystkich kont, które ma zostać wykonane członków lokalnej grupy Administratorzy na komputerach docelowych przy użyciu danej marki i modelu. Widok jest sprzężenie tabel MakeModelIdentity i Settings_Administrators.|  
|MakeModelApplications|Użyć w celu znalezienia wszystkich aplikacji w celu wdrażania na komputerach docelowych przy użyciu danej marki i modelu. Widok jest sprzężenie tabel MakeModelIdentity i Settings_Applications.|  
|MakeModelPackages|Użyć w celu znalezienia wszystkich pakietów do wdrażania na komputerach docelowych przy użyciu danej marki i modelu. Widok jest sprzężenie tabel MakeModelIdentity i Settings_Applications.|  
|MakeModelRoles|Użyć w celu znalezienia wszystkich ról związanych z komputerów docelowych z danej marki i modelu. Widok jest sprzężenie tabel MakeModelIdentity i Settings_Roles.|  
|MakeModelSettings|Użyć w celu znalezienia wszystkich ustawień właściwości można skonfigurować dla komputerów docelowych z danej marki i modelu. Widok jest sprzężenie tabel MakeModelIdentity i ustawień.|  
|RoleAdministrators|Użyć w celu znalezienia wszystkich kont, które ma zostać wykonane członków lokalnej grupy Administratorzy na komputerach docelowych z danej roli. Widok jest sprzężenie tabel RoleIdentity i Settings_Administrators.|  
|RoleApplications|Użyć w celu znalezienia wszystkich aplikacji w celu wdrażania na komputerach docelowych z danej roli. Widok jest sprzężenie tabel RoleIdentity i Settings_Applications.|  
|RolePackages|Użyć w celu znalezienia wszystkich pakietów do wdrażania na komputerach docelowych z danej roli. Widok jest sprzężenie tabel RoleIdentity i Settings_Packages.|  
|RoleSettings|Użyć w celu znalezienia wszystkich ustawień właściwości można skonfigurować dla komputerów docelowych z danej roli. Widok jest sprzężenie tabel RoleIdentity i ustawień.|  

## <a name="windows-7-feature-dependency-reference"></a>Informacje dotyczące systemu Windows 7 funkcja zależności  
 Tabela 8 zawiera funkcje systemu Windows 7, funkcją nadrzędną i funkcji zależnych. Można użyć tych informacji do sprawdzania, jakie funkcje oraz role muszą być zainstalowane do obsługi określonych funkcji przy użyciu [zainstalować role i funkcje](#InstallRolesandFeatures) i [odinstalowywanie ról i funkcji](#UninstallRolesandFeatures) sekwencji zadań kroki.  

### <a name="table-8-windows-7-feature-dependency-reference"></a>Tabela 8. Informacje dotyczące systemu Windows 7 funkcja zależności  

|**Funkcja**|**Funkcja nadrzędnego**|**Funkcje zależne**|  
|-|-|-|  
|Centrum Media® systemu Windows|Funkcje nośnika|Może mieć wpływ na inne funkcje systemu Windows|  
|Maker dysku DVD systemu Windows|Funkcje nośnika|Może mieć wpływ na inne funkcje systemu Windows|  
|Windows Media Player|Funkcje nośnika|Może mieć wpływ na inne funkcje systemu Windows|  
|Usługa wyszukiwania systemu Windows|Brak|Może mieć wpływ na inne funkcje systemu Windows|  
|Program Internet Explorer (amd64)|Brak|Może mieć wpływ na inne funkcje systemu Windows|  
|Usługi sieci Web|Microsoft Internet Information Services (IIS)|— Pomocy technicznej firmy Microsoft usługi kolejkowania komunikatów (MSMQ) HTTP<br /><br /> — Windows Communication Foundation (WCF) HTTP aktywacji|  
|Zgodność z narzędziami WMI usług IIS 6|Usługi IIS, narzędzia zarządzania siecią Web, zgodność z narzędziami zarządzania usługami IIS 6|Narzędzia obsługi skryptów usług IIS 6|  
|Rozszerzenia architektury Microsoft .NET|Usługi IIS, usługi sieci World Wide Web, funkcje tworzenia aplikacji|-Microsoft ASP.NET<br /><br /> -Obsługa protokołu HTTP MSMQ<br /><br /> — Aktywacja HTTP programu WCF|  
|Dokument domyślny|Usługi IIS, usługi sieci World Wide Web, wspólne funkcje HTTP|Obsługa protokołu HTTP usługi MSMQ|  
|Przeglądanie katalogów|Usługi IIS, usługi sieci World Wide Web, wspólne funkcje HTTP|Obsługa protokołu HTTP usługi MSMQ|  
|Przekierowywanie HTTP|Usługi IIS, usługi sieci World Wide Web, wspólne funkcje HTTP|Obsługa protokołu HTTP usługi MSMQ|  
|Zawartość statyczna|Usługi IIS, usługi sieci World Wide Web, wspólne funkcje HTTP|-Opartych na sieci web Distributed Authoring and Versioning (WebDAV) publikowania<br /><br /> -Obsługa protokołu HTTP MSMQ|  
|Rejestrowanie niestandardowe|Usługi IIS, usługi sieci World Wide Web, kondycja i Diagnostyka|Obsługa protokołu HTTP usługi MSMQ|  
|Rejestrowanie HTTP|Usługi IIS, usługi sieci World Wide Web, kondycja i Diagnostyka|Obsługa protokołu HTTP usługi MSMQ|  
|Rejestrowanie ODBC|Usługi IIS, usługi sieci World Wide Web, kondycja i Diagnostyka|Obsługa protokołu HTTP usługi MSMQ|  
|Monitor żądań|Usługi IIS, usługi sieci World Wide Web, kondycja i Diagnostyka|Obsługa protokołu HTTP usługi MSMQ|  
|Śledzenie|Usługi IIS, usługi sieci World Wide Web, kondycja i Diagnostyka|Obsługa protokołu HTTP usługi MSMQ|  
|Kompresja zawartości statycznej|Usługi IIS, usługi sieci World Wide Web, funkcje wydajności|Obsługa protokołu HTTP usługi MSMQ|  
|Zabezpieczenia|Usługi IIS, usługi sieci Web|-Rozszerzalność Microsoft .NET<br /><br /> -Obsługa protokołu HTTP MSMQ<br /><br /> — Aktywacja HTTP programu WCF|  
|Filtrowanie żądań|Usługi IIS, usługi sieci World Wide Web, zabezpieczeń|-Rozszerzalność Microsoft .NET<br /><br /> -Obsługa protokołu HTTP MSMQ<br /><br /> — Aktywacja HTTP programu WCF|  
|Przeglądarka plików XPS|Brak|Może mieć wpływ na inne funkcje systemu Windows|  

## <a name="udi-reference"></a>UDI — informacje  
 To odwołanie zapewnia dodatkowe informacje o UDI i zawiera tematy na:  

-   Pojęcia UDI zgodnie z opisem w [UDI pojęcia](#UDIConcepts)  

-   OSDResults zgodnie z opisem w [OSDResults odwołania](#OSDResultsReference)  

-   Użytkownik na Instalatora aplikacji zgodnie z opisem w [odwołania Instalatora aplikacji Centric użytkownika](#UserCentricAppInstallerReference)  

-   UDI przygotuje zgodnie z opisem w [etap UDI — informacje](#UDIStageReference)  

-   UDI zadań zgodnie z opisem w [zadań UDI — informacje](#UDITaskReference)  

-   Moduły UDI zgodnie z opisem w [modułu sprawdzania poprawności UDI — informacje](#UDIValidatorReference)  

-   UDI stron kreatora, zgodnie z opisem w [UDI odwołania do strony kreatora](#UDIWizardPageReference)  

 W kolejnych sekcjach omówiono każdego z tych tematów odwołania.  

###  <a name="UDIConcepts"></a>UDI pojęcia  
 Ta sekcja zawiera pojęcia, które pomagają w opisie UDI, Kreator UDI i projektanta Kreatora instalacji UDI.  

####  <a name="DisplayName"></a>Nazwa wyświetlana  
 Nazwa wyświetlana jest używana do Podaj przyjazną dla użytkownika nazwę opisową dla strony kreatora w bibliotece strony w projektanta Kreatora instalacji UDI. Nazwa wyświetlana jest wyświetlany w kolorze niebieskim dla każdej strony kreatora biblioteki strony oraz na **przepływ** karcie projektanta Kreatora instalacji UDI.  

 Po dodaniu strony do biblioteki strony, należy podać nazwę wyświetlaną. Po Kreatora strony jest dodawane do biblioteki strony, nie można zmienić nazwę wyświetlaną.  

####  <a name="Flow"></a>Przepływ  
 **Przepływ** karta jest wyświetlana lista stron kreatora w UDI etapem projektanta Kreatora instalacji UDI. Można użyć **przepływ** kartę, aby wykonywać następujące zadania:  

-   Dodawanie strony kreatora z biblioteki strony do etapu UDI przeciągając strony z biblioteki strony do etapu UDI.  

-   Usuń strony kreatora z etapu UDI.  

-   Zmiana kolejności stron kreatora w ramach etapu UDI.  

####  <a name="PageLibrary"></a>Biblioteka stron  
 Biblioteka strony zawiera wszystkie strony załadowanych obecnie do projektanta Kreatora instalacji UDI. Podczas ładowania pliku konfiguracji kreatora UDI, zostaną wyświetlone wszystkie strony kreatora zdefiniowane w pliku konfiguracyjnym do biblioteki strony. Biblioteka strony zawiera strony kreatora w porządku alfabetycznym według typów stron. Każde wystąpienie typu określona strona jest wyświetlana w obszarze Typ strony.  

 Na przykład może potrzebne są dwa różne **WelcomePage** strony kreatora dla różnych etapach. Dwa **WelcomePage** stron kreatora zostaną wyświetlone w obszarze **WelcomePage** typ strony kreatora biblioteki strony w projektanta Kreatora instalacji UDI.  

 Ponadto każde wystąpienie strony kreatora w bibliotece strony wskazuje, ile razy strona kreatora jest używany w przepływach etapu. Po ustawieniu kursora strony kreatora biblioteki strony miniaturę strony kreatora jest wyświetlana wraz z etapów, które obejmują tej strony.  

####  <a name="PageName"></a>Nazwa strony  
 Nazwa strony jest używany do jednoznacznego identyfikowania stronę kreatora w bibliotece strony w projektanta Kreatora instalacji UDI. *Nazwy strony* jest nazwą etap UDI odwołuje się tak, aby Kreator UDI wie, które strona kreatora do wyświetlenia w ramach danego etapu UDI. Po dodaniu strony do biblioteki strony, należy podać nazwę strony. Po Kreatora strony jest dodawane do biblioteki strony, nie można zmienić nazwy strony. W projektanta Kreatora instalacji UDI nazwy strony jest wyświetlany u dołu każdej strony biblioteki strony w mniejszych, bold tekst.  

####  <a name="PrestagedMediaDeployments"></a>Wdrożenia z nośników wstępnie przygotowanych  
 Obsługa wstępnie przygotowanego nośnika jest funkcję wdrażania systemu operacyjnego w programie Configuration Manager umożliwiająca administratorowi skopiować i zastosować wstępnie przygotować nośnik rozruchowy i obraz systemu operacyjnego na dysku twardym przed obsługą administracyjną przetwarzania. Tę pracę można zmniejszyć obciążenie sieci oraz czas potrzebny na proces inicjowania obsługi administracyjnej. Wstępnie przygotowanego nośnika można wdrożyć w ramach procesu produkcyjnego lub w Centrum przygotowywania przedsiębiorstwa niepołączonym do środowiska programu Configuration Manager.  

 Aby uzyskać więcej informacji na temat wdrożenia z nośników wstępnie przygotowanych zobacz następujące zasoby:  

-   [Planowanie wdrożenia systemu operacyjnego z nośnika w programie Configuration Manager](http://technet.microsoft.com/library/hh499044.aspx)  

-   [O wstępnie przygotowanego nośnika do wdrażania systemu operacyjnego](http://technet.microsoft.com/library/gg294171.aspx)  

#### <a name="stage-group"></a>Etap grupy  
 Należy użyć etapy do grupy co najmniej jeden etap w projektanta Kreatora instalacji UDI. UDI etap grup są luźno związane z scenariusze wdrożenia zestawu MDT, ale nie nie sygnałowych dwa.  

####  <a name="Stage"></a>Etap  
 A *etap* jest podzbiorem wszystkich stron w pliku konfiguracji UDI kreatora, który używa scenariusz wdrożenia zestawu MDT. Podczas uruchamiania przy użyciu Kreatora UDI **kreatora UDI** krok sekwencji zadań, **/etap** parametr określa etap do uruchomienia, która z kolei określa zbiór stron do użycia. Wyświetl podgląd wygląd strony kreatora w fazie, klikając **Podgląd** w **Podgląd kreatora** na Wstążce. Etap UDI można użyć w więcej niż jeden scenariusz wdrożenia zestawu MDT, mimo że etap UDI jest zdefiniowany tylko raz w projektanta Kreatora instalacji UDI. Na etapie NewComputer można na przykład w środowiskach wdrożenia zestawu MDT nowe komputery i Zastąp.  

####  <a name="Task"></a>Zadanie  
 *Zadania UDI* to oprogramowanie, które jest uruchamiane na stronie kreatora do wykonywania określonych funkcji. W niektórych przypadkach te zadania są używane do Sprawdź, czy komputer docelowy jest gotowa do wdrożenia. Inne zadania mogą posłużyć do wykonania kroków wdrażania, takich jak kopiowanie plików konfiguracji lub wynik.  

> [!NOTE]
>  **Dalej** przycisk na stronie kreatora, których zadania są uruchamiane zostanie wyłączony, jeśli zadań zakończy się stanem zakończenia ostrzeżenia lub błędu.  

 UDI zawiera kilka wbudowanych zadania, które umożliwiają wykonywanie większości zadań niezbędnych do wdrożenia. Aby uzyskać więcej informacji o zadaniach wbudowanych UDI, zobacz [wbudowane zadania UDI](#BuiltinUDITasks).  

 **Wykonanie powłoki** wbudowanego zadania UDI umożliwia uruchamianie oprogramowania (skrypty), którego może zostać zainicjowany z wiersza polecenia, takich jak skrypty języka Visual Basic lub środowiska Windows PowerShell. Ta funkcja umożliwia tworzenie zadania przy użyciu znanych języków skryptów. Aby uzyskać więcej informacji, zobacz [powłoki wykonania zadań](#ShellExecuteTask).  

 Jeśli wymagania dotyczące wykracza poza skryptów, można pisać niestandardowe zadania UDI. *Zadania UDI* są napisane w języku C++ i wdrożenie **ITask** interfejsu. Zarejestruj plik DLL z biblioteką zadań projektanta Kreatora instalacji UDI, tworząc plik konfiguracji (config) projektanta Kreatora instalacji UDI i umieszczenie go w *installation_folder*\Bin\Config folder (gdzie *installation_ folder* to folder, w którym jest zainstalowany zestaw MDT). Aby uzyskać więcej informacji na temat tworzenia niestandardowych zadań UDI, zobacz sekcję "Tworzenie niestandardowych UDI zadań", w *przewodnik dla deweloperów instalacji sterowanej*.  

####  <a name="UDITaskSequence"></a>UDI sekwencji zadań  
 Należy utworzyć sekwencję zadań UDI przy użyciu jednej z następujących MDT UDI określonych zadań sekwencji szablonów, które Uruchom Kreatora UDI na odpowiedni krok w sekwencji zadań:  

-   **Sekwencja zadań instalacji za pomocą użytkownika.** Ten szablon sekwencji zadań służy do scenariuszy wdrażania nowego komputera, Odśwież komputera i Zastąp MDT komputera.  

-   **Sekwencja zadań Zamień instalacji za pomocą użytkownika.** Ten szablon sekwencji zadań jest pierwszym etapem dwuetapowy proces w scenariuszu wdrażania Zastąp komputera i służy do przechwytywania danych migracji stanu użytkownika. Drugim krokiem w dwuetapowy proces jest sekwencja zadań instalacji sterowanej szablonu sekwencji zadań, który umożliwia wdrażanie aplikacji docelowej i systemu operacyjnego i przywracania danych migracji stanu użytkownika zapisane w pierwszym kroku procesu.  

 Aby uzyskać więcej informacji na temat szablonów sekwencji zadań UDI, zobacz sekcję "Zidentyfikować UDI zadań sekwencji szablonów w MDT", w dokumentacji zestawu MDT *przy użyciu programu Microsoft Deployment Toolkit*. Aby uzyskać więcej informacji na temat tych składników, zobacz sekcję "Zidentyfikować UDI procesu składniki wdrażania", w dokumentacji zestawu MDT *przy użyciu programu Microsoft Deployment Toolkit*, która jest dostarczana z zestawu MDT.  

####  <a name="UDIWizard"></a>Kreator UDI  
 Kreator UDI udostępnia interfejs użytkownika do zbierania ustawienia wdrożenia sekwencji zadań UDI korzystać. Kreator UDI jest inicjowane w ramach sekwencji zadań UDI i zbiera informacje o konfiguracji niezbędne dostosowywania wdrażania systemów operacyjnych klienta systemu Windows i aplikacji. Strony kreatora odczytać ich ustawienia konfiguracji z pliku konfiguracji UDI kreatora, który jest dostosowane przy użyciu projektanta Kreatora instalacji UDI.  

 Kreator UDI jest inicjowane przez **kreatora UDI** krok sekwencji zadań w sekwencjach zadań utworzonych przy użyciu szablonów UDI sekwencji zadań. **Kreatora UDI** krok sekwencji zadań uruchamia skrypt UDIWizard.wsf, który z kolei inicjuje kreatora UDI (OSDSetupWizard.exe). 9 tabela zawiera listę parametrów wiersza polecenia UDI kreatora i zawiera krótki opis każdego z nich.  

### <a name="table-9-udi-wizard-command-line-parameters"></a>Tabela 9. Parametry wiersza polecenia UDI Kreatora  

|**Parametr**|**Opis**|  
|-|-|  
|**/ Preview**|Umożliwia wyświetlenie podglądu bieżącej konfiguracji kreatora, należy włączyć **dalej** przycisku, dzięki czemu można przenieść między Stronami bez konieczności prawidłowe wartości wejściowe.|  
|**XML**|Określa nazwę pliku konfiguracji kreatora UDI. Skrypt UDIWizard.wsf automatycznie ustawia tego parametru do pliku OSDSetupWizard.xml, który jest przechowywany w folderze, w którym sekwencja zadań przechowuje pliki dziennika. Ten parametr domyślnie pliku config.xml.<br /><br /> Poniżej przedstawiono składnię tego parametru (gdzie `<full_path>` jest w pełni kwalifikowana ścieżka do pliku XML, w tym nazwę pliku i rozszerzenie):<br /><br /> `/xml:<full_path>`|  
|**/Stage**|Określa nazwę etapu UDI do uruchomienia. Skrypt UDIWizard.wsf automatycznie ustawia tego parametru do etapu odpowiednie zgodnie z opisem w [UDI — informacje etap](#UDIStageReference). Ten parametr domyślnie pierwszego etap w pliku konfiguracyjnym UDI kreatora.<br /><br /> Poniżej przedstawiono składnię tego parametru (gdzie `<stage_name>` jest nazwa etapu na uruchamianie):<br /><br /> `/stage:<stage_name>`<br /><br /> Uwaga:<br /><br /> Wartość < stage_name > jest uwzględniana wielkość liter.|  
|**/ Locale**|Określa język do użycia w Kreatorze UDI w formie identyfikator ustawień regionalnych (LCID), który jest reprezentowany przez wartość liczbową. Aby uzyskać listę dostępnych LCID, zobacz [ustawień regionalnych identyfikatory przypisane przez firmę Microsoft](http://msdn.microsoft.com/goglobal/bb964664).<br /><br /> Czy ta lista służy do identyfikowania język, którego chcesz użyć, a następnie podaj odpowiedni identyfikator LCID.<br /><br /> Poniżej przedstawiono składnię tego parametru (gdzie `<locale_id>` jest wartość liczbowa LCID używanego):<br /><br /> `/locale:<locale_id>`|  

####  <a name="UDIWizardApplicationConfigurationFile"></a>Plik konfiguracji aplikacji Kreator UDI  
 **ApplicationPage** UDI kreatora pliku konfiguracji aplikacji, która przechowuje listę oprogramowania instalowanego konfiguruje strony kreatora. Ten plik zawiera wpis dla każdej aplikacji programu Configuration Manager lub program i pakiet, który został dodany za pomocą projektanta Kreatora instalacji UDI.  

 Ten plik ma taką samą nazwę jak plik konfiguracji UDI kreatora, ale z rozszerzeniem .app. Na przykład, jeśli nosi nazwę pliku konfiguracji kreatora UDI *pliku Config.xml,* , a następnie odpowiedniego pliku konfiguracji aplikacji UDI Kreator będzie *Config.xml.app.* Ten plik jest towarzyszącego UDI kreatora pliku konfiguracji.  

####  <a name="UDIWizardConfigurationFile"></a>Plik konfiguracji kreatora UDI  
 Kreator UDI odczytuje plik konfiguracji kreatora UDI ustalenie na stronach kreatora, który będzie wyświetlany, sekwencji stron kreatora, ustawienia domyślnego dla formantów na stronach kreatora, i określa, czy formanty są włączone lub wyłączone. Ten plik zawiera wszystkie ustawienia konfiguracji, które są wyświetlane w Kreatorze UDI i są konfigurowane za pomocą projektanta Kreatora instalacji UDI.  

 Plik konfiguracji oddzielne — pliku konfiguracji aplikacji Kreatora UDI — służy do konfigurowania aplikacji do zainstalowania na komputerze docelowym.  

####  <a name="UDIWizardDesigner"></a>Projektanta Kreatora instalacji UDI  
 Projektanta Kreatora instalacji UDI jest podstawowym narzędziem do dostosowywania stron kreatora dla różnych scenariuszy wdrażania obsługiwanych przez UDI. Zmiany wprowadzone w projektanta Kreatora instalacji UDI są zapisywane w pliku konfiguracji kreatora UDI i ostatecznie zostaną uwzględnione w środowisko użytkownika w Kreatorze UDI. Użytkownika przeprowadzającego wdrożenie będą widzieć tylko na stronach kreatora w Kreatorze UDI, który został wybrany i skonfigurowany za pomocą projektanta Kreatora instalacji UDI.  

 Mimo że Kreator UDI będzie uruchomiony z Kreatora UDI domyślny plik konfiguracji, na stronach kreatora może nie być poprawnie skonfigurowana. Zaleca się, że projektanta Kreatora instalacji UDI są używane do konfigurowania kreatora UDI środowisko użytkownika.  

> [!NOTE]
>  Aby uruchomić projektanta Kreatora instalacji UDI, musi mieć odpowiednie uprawnienia w programie Configuration Manager dostęp do obiektów, takich jak pakiety, aplikacje lub obrazów.  

####  <a name="Validator"></a>Moduł sprawdzania poprawności  
 Moduły weryfikacji UDI służy do zapewnienia, że poprawne informacje jest wprowadzany do pól tekstowych na stronach kreatora, w Kreatorze UDI. UDI zawiera kilka wbudowanych moduły weryfikacji, które wykonania typowych operacji sprawdzania poprawności z pola służące do wprowadzania tekstu, na przykład uniemożliwienie użytkownikom wprowadzanie nieprawidłowe znaki i zapewnia, że pole jest pomoc nie jest pusta. Jeśli moduł weryfikacji wykryje nieprawidłowy wpis w polu tekstowym, na stronie kreatora zostanie wyświetlony komunikat i **dalej** przycisk jest niedostępny, dopóki wszystkie nieprawidłowe wpisy zostaną rozwiązane.  

 UDI obejmuje wbudowane moduły weryfikacji, które umożliwiają wykonywanie większości weryfikacji, które są niezbędne do wdrożenia. Aby uzyskać więcej informacji na temat wbudowanych UDI modułów sprawdzania poprawności, zobacz [wbudowane moduły UDI](#BuiltinUDIValidators).  

 Jeśli wymagania dotyczące wykracza poza wbudowane moduły UDI, można pisać niestandardowe moduły UDI. *Moduły weryfikacji UDI* są bibliotek DLL w języku C++, które implementują **IValidator** interfejsu. Zarejestruj plik DLL z biblioteką modułu sprawdzania poprawności projektanta Kreatora instalacji UDI, tworząc plik konfiguracji (config) projektanta Kreatora instalacji UDI i umieszczenie go w *installation_folder*\Bin\Config folder (gdzie *installation_ folder* to folder, w którym jest zainstalowany zestaw MDT). Aby uzyskać więcej informacji na temat tworzenia niestandardowych zadań UDI, zobacz sekcję "Tworzenie niestandardowych UDI moduły", w dokumentacji zestawu MDT *przewodnik dla deweloperów instalacji sterowanej*.  

####  <a name="WizardPage"></a>Strona kreatora  
 Strona kreatora umożliwia zbieranie informacji o konfiguracji w Kreatorze UDI. Konfiguruj strony kreatora UDI za pomocą projektanta Kreatora instalacji UDI. Ustawienia konfiguracji są przechowywane w pliku konfiguracyjnym UDI kreatora i są odczytywane przez strony kreatora, po zainicjowaniu strony kreatora UDI.  

 Strony kreatora są przechowywane w Kreatorze biblioteki strony i może służyć etapami UDI jeden lub więcej. Ten projekt pozwala na skonfigurowanie stronę kreatora współużytkowanych etapy raz dla wszystkich etapów znacznie zmniejsza ilość wymagany nakład pracy i złożoność aktualizowania konfiguracji strony kreatora.  

 UDI zawiera strony kreatora wbudowanych i edytory strony kreatora, które są zwykle wystarczające dla większości wdrożeń. Aby uzyskać więcej informacji na temat stron kreatora wbudowane zobacz [wbudowanych stron kreatora UDI](#BuiltinUDIWizardPages).  

 Wymagania dotyczące wykracza poza wbudowane UDI strony kreatora i odpowiednie edytory strony kreatora, można pisać niestandardowe strony kreatora UDI i edytory strony kreatora. UDI strony kreatora są zaimplementowane jako biblioteki dll, które odczytuje kreatora UDI. Edytory strony kreatora są tworzone za pomocą języka C++ w programie Visual Studio.  

 Aby uzyskać więcej informacji na temat tworzenia niestandardowych stron kreatora UDI, zobacz sekcję "Tworzenie niestandardowych UDI stron kreatora", w dokumentacji zestawu MDT *przewodnik dla deweloperów instalacji sterowanej*.  

####  <a name="WizardPageEditor"></a>Edytor stron kreatora  
 Edytor stron kreatora używane do konfigurowania strony kreatora w projektanta Kreatora instalacji UDI. Edytor stron kreatora aktualizacji ustawienia konfiguracji strony kreatora w pliku konfiguracji kreatora UDI; UDI zawiera Edytor stron kreatora wbudowanych, dla każdej strony kreatora wbudowanych. Aby uzyskać więcej informacji na temat stron kreatora wbudowanych i edytory strony kreatora, zobacz [wbudowanych stron kreatora UDI](#BuiltinUDIWizardPages).  

 Wymagania dotyczące wykracza poza wbudowane UDI strony kreatora i odpowiednie edytory strony kreatora, można pisać niestandardowe strony kreatora UDI i edytory strony kreatora. Edytory strony kreatora UDI są zaimplementowane jako biblioteki dll, które odczytuje projektanta Kreatora instalacji UDI. Utwórz edytory za pomocą strony kreatora:  

-   [Windows Presentation Foundation](http://msdn.microsoft.com/library/ms754130.aspx) w wersji 4.0  

-   [Microsoft Prism](http://compositewpf.codeplex.com/) w wersji 4.0  

-   [Blok aplikacji platformy Unity Microsoft](http://unity.codeplex.com/) (Unity) w wersji 2.1  

 Aby uzyskać więcej informacji na temat tworzenia niestandardowych edytorów strony kreatora UDI, zobacz sekcję "Tworzenie niestandardowego Kreatora strony edytory", w dokumentacji zestawu MDT *przewodnik dla deweloperów instalacji sterowanej*.  

###  <a name="OSDResultsReference"></a>Odwołanie OSDResults  
 **OSDResults** część UDI, który wyświetla wyniki wdrożenia odbywa się przy użyciu UDI. **OSDResults** Wyświetla **ukończenia wdrożenia** okno dialogowe. **OSDResults** jest wyświetlany przed czasem pierwszego logowania systemu Windows jest uruchomiona na komputerze docelowym. Użytkownik może użyć **OSDResults** i informacje zawarte w **ukończenia wdrożenia** okno dialogowe, aby określić stan ukończenia procesu wdrażania i konfigurowania komputerów przed logowanie się po raz pierwszy. Ponadto, informacje w **OSDResults** może służyć do rozwiązywania problemów napotkanych podczas procesu wdrażania.  

 Można skonfigurować niektóre elementy interfejsu użytkownika dla **OSDResults** przy użyciu pliku OSDResults.exe.config, który znajduje się w Tools\OSDResults w zestawie MDT pliki pakietu programu Configuration Manager. Tabela 10 zawiera ustawienia konfiguracji w pliku OSDResults.exe.config.  

### <a name="table-10-configuration-settings-in-the-osdresultsexeconfig-file"></a>Tabela 10. Ustawienia konfiguracji w pliku OSDResults.exe.config  

|**Ustawienie**|**Opis**|  
|-|-|  
|**headerImagePath**|To ustawienie pozwala określić w pełni kwalifikowaną lub względną ścieżkę do pliku bmp, który jest wyświetlany w nagłówku **OSDResults** okno dialogowe.<br /><br /> Wartość domyślna to ustawienie jest następujący:<br /><br /> `images\UDI_Wizard_Banner.bmp`|  
|**backgroundWallpaper**|To ustawienie pozwala określić w pełni kwalifikowaną lub względną ścieżkę do pliku jpg, który jest wyświetlany jako tapety w **OSDResults** okno dialogowe.<br /><br /> Wartość domyślna to ustawienie jest następujący:<br /><br /> `images\Wallpaper.jpg`|  
|**welcomeText**|To ustawienie umożliwia określenie tekstu, chętnie zapozna się użytkownik, który zawiera informacje na temat procesu wdrażania. Jest on wyświetlany w **OSDResults** okno dialogowe.|  
|**completedText**|To ustawienie pozwala określić tekst, który wskazuje, czy Proces wdrażania jest pełny. Jest on wyświetlany w **OSDResults** okno dialogowe.|  
|**timeoutMinutes**|To ustawienie umożliwia określenie czasu **OSDResults** przed automatycznie wyświetlania ekranu logowania systemu Windows zostanie wyświetlone okno dialogowe. Wartość tego ustawienia jest określony w minutach.<br /><br /> Wartość domyślna dla tego ustawienia to zero (0), który wskazuje, że **OSDResults** wyświetli się okno dialogowe do czasu ich ręcznie zamknięty.|  

 Oto ogólny proces jak **OSDResults** funkcja działa w UDI:  

1.  Sekwencja zadań jest uruchamiana na komputerze docelowym.  

     Sekwencja zadań jest oparty na jeden z szablonów followUDI sekwencji zadań:  

    -   **Użytkownik zmiennych sekwencji zadań instalacji**. Ten szablon sekwencji zadań jest używany w scenariuszach wdrożenia zestawu MDT nowy komputer, Odśwież komputera i Zastąp MDT komputera.  

    -   **Użytkownik zmiennych sekwencji zadań instalacji Zamień**. Ten szablon sekwencji zadań jest pierwszym etapem dwuetapowy proces w scenariuszu wdrażania komputera Zastąp MDT i służy do przechwytywania danych migracji stanu użytkownika. Drugim krokiem w procesie dwóch etapów jest scenariusz wdrożenia zestawu MDT nowego komputera przy użyciu **sekwencji zadań instalacji zmiennych użytkownika** szablonu sekwencji zadań, który służy do wdrażania aplikacji docelowej i systemu operacyjnego i Przywróć zapisany w pierwszym kroku procesu dane migracji stanu użytkownika  

     Aby uzyskać więcej informacji na temat:  

    -   UDI szablony sekwencji zadań, zobacz sekcję "Zidentyfikować UDI zadań sekwencji szablonów w MDT", w dokumentacji zestawu MDT *przy użyciu programu Microsoft Deployment Toolkit*  

    -   Relacja między scenariusze wdrożenia zestawu MDT i UDI etapach, zobacz [etap UDI — informacje](#UDIStageReference)  

2.  Podczas sekwencji zadań, ustawienia konfiguracji podane przez zmienne sekwencji zadań oraz z danych wejściowych użytkownika w Kreatorze UDI są zapisywane w *DEPLOYROOT %*\Tools\OSDResults folderu na komputerze docelowym (gdzie *%D EPLOYROOT %* jest głównym folderu, w którym pliki zestawu MDT są buforowane lokalnie na komputerze docelowym).  

3.  W **OSD wyników i Branding** grupy sekwencji zadań następujące kroki sekwencji zadań są uruchamiane wpływają na **OSDResults**:  

    -   **Wyniki OSD pamięci podręcznej.** Ten krok sekwencji zadań kopiuje zawartość *DEPLOYROOT %*\Tools\OSDResults folderu do folderu %WINDIR%\UDI na komputerze docelowym. Daje to pewność, że zawartość folderu OSDResults zostaną utrwalone po zakończeniu sekwencji zadań.  

    -   **Uruchamianie OSD wyników.** Ten krok sekwencji zadań umożliwia skonfigurowanie komputera docelowego, aby uruchomić **OSDResults** przy pierwszym uruchomieniu komputera.  

4.  Komputer docelowy uruchamia się po raz pierwszy i OSDResults.exe jest uruchamiany przed ekranu logowania systemu Windows.  

     **Powitalnej** karcie **ukończenia wdrożenia** zostanie wyświetlone okno dialogowe. **Powitalnej** karta zawiera przydatne informacje dotyczące wdrażania i skontaktuj się z informacji w przypadku, gdy zostaną wykryte problemy dotyczące wdrożenia.  

     Przejrzyj informacje na **Wdrożęnia** i **aplikacje zainstalowane** karty, aby sprawdzić, czy system operacyjny i aplikacje zostały zainstalowane poprawnie. Po zakończeniu przeglądania te tabele, kliknij przycisk **Start systemu Windows** aby zalogować się do systemu Windows 7 po raz pierwszy.  

    > [!NOTE]
    >  Aplikacji programu Configuration Manager nie są wyświetlane na **aplikacje zainstalowane** kartę. Aplikacji programu Configuration Manager są wykrywane po zalogowaniu użytkownika na komputerze docelowym po raz pierwszy.  

5.  Zostanie wyświetlony ekran logowania systemu Windows, a następnie kontynuuje działanie procesu logowania.  

     AppInstall.exe jest uruchamiany po raz pierwszy użytkownik zaloguje się na komputerze docelowym. Aby uzyskać więcej informacji na ten proces, zobacz [skoncentrowane na użytkowniku odwołanie Instalatora aplikacji](#UserCentricAppInstallerReference).  

###  <a name="UserCentricAppInstallerReference"></a>Odwołanie skoncentrowane na użytkowniku Instalatora aplikacji  
 Funkcja skoncentrowane na użytkowniku Instalatora aplikacji w UDI jest używane do zgłaszania wszystkie aplikacje instalowane w ramach procesu wdrażania UDI do funkcji wykazu aplikacji w programie Configuration Manager. Funkcja skoncentrowane na użytkowniku Instalatora aplikacji zapewnia połączenie między aplikacjami wybranego na **ApplicatonPage** strona kreatora w Kreatorze UDI i wszelkich opcjonalnych aplikacji programu Configuration Manager anonsowany użytkownikom.  

 Aby uzyskać więcej informacji na temat funkcji katalogu aplikacji w programie Configuration Manager, zobacz [zarządzania aplikacjami w programie Configuration Manager](http://technet.microsoft.com/library/gg699373.aspx).  

 Oto ogólny proces działania funkcji Instalacja aplikacji UDI:  

1.  Aplikacji programu Configuration Manager są tworzone w programie Configuration Manager.  

     Aby uzyskać więcej informacji na temat tworzenia i zarządzania aplikacjami programu Configuration Manager zobacz następujące zasoby:  

    -   [Jak tworzyć aplikacje w programie Configuration Manager](http://technet.microsoft.com/library/gg682159.aspx)  

    -   [Operacje i Obsługa zarządzania aplikacjami w programie Configuration Manager](http://technet.microsoft.com/library/gg681963.aspx)  

2.  Kolekcje użytkowników programu Configuration Manager są tworzone, a użytkownicy są dodawani do kolekcji.  

     Aby uzyskać więcej informacji na temat tworzenia i Zarządzanie kolekcjami użytkowników i dodawanie użytkowników do kolekcji zobacz następujące zasoby:  

    -   [Kolekcje w programie Configuration Manager](http://technet.microsoft.com/library/gg682169.aspx)  

    -   [Jak utworzyć kolekcje w programie Configuration Manager](http://technet.microsoft.com/library/gg712295.aspx)  

3.  Aplikacji programu Configuration Manager są wdrażane w kolekcjach użytkowników.  

     Aby uzyskać więcej informacji o sposobie wdrażania aplikacji w kolekcjach użytkowników, zobacz [jak wdrażać aplikacje w programie Configuration Manager](http://technet.microsoft.com/library/gg682082.aspx).  

4.  Aplikacji programu Configuration Manager są udostępniane na **ApplicatonPage** za pomocą projektanta Kreatora instalacji UDI strony kreatora.  

     Aby uzyskać więcej informacji dotyczących sposobu udostępniania aplikacji programu Configuration Manager na **ApplicatonPage** strona kreatora, zobacz sekcję "krok 5-11: Dostosowywanie pliku konfiguracji kreatora UDI dla komputera docelowego"w dokumencie MDT *Przewodnik Szybki Start dla instalacji sterowanej*.  

5.  UDA jest konfigurowana przy użyciu jednej z następujących metod:  

    -   W konsoli programu Configuration Manager (Aby uzyskać więcej informacji o konfigurowaniu UDA w konsoli programu Configuration Manager, zobacz [jak zarządzać koligacją urządzeń użytkownika w programie Configuration Manager](http://technet.microsoft.com/library/gg699365.aspx).)  

    -   Na **UDAPage** strona kreatora w Kreatorze UDI (Aby uzyskać więcej informacji na temat **UDAPage** strona kreatora, zobacz [UDAPage](#UDAPage).)  

     Po skonfigurowaniu UDA określone konto użytkownika będzie głównego użytkownika komputera docelowego.  

    > [!NOTE]
    >  UDA można skonfigurować tylko przez UDI w scenariuszu wdrażania nowego komputera. Nie można skonfigurować w scenariuszach wdrażania Odśwież komputerze lub Zastąp.  

6.  Sekwencja zadań jest uruchomiona, a użytkownik wybierze aplikacji programu Configuration Manager na **ApplicatonPage** strona kreatora w Kreatorze UDI.  

     Uruchomiono kreatora UDI **kreatora UDI** krok sekwencji zadań **instalacją** grupy sekwencji zadań. Gdy użytkownik wybierze aplikacji programu Configuration Manager na **ApplicatonPage** strona kreatora strony kreatora tworzy zmienną sekwencji zadań osobne dla każdej aplikacji wybrane.  

     Aby uzyskać więcej informacji na temat wybierania aplikacji programu Configuration Manager na **ApplicatonPage** strona kreatora w Kreatorze UDI, zobacz sekcję "krok 6-4: Uruchom komputer docelowy z nośnika rozruchowego sekwencji zadań"w dokumencie MDT *Przewodnik Szybki Start dla instalacji sterowanej*.  

7.  Sekwencja zadań instaluje aplikacji programu Configuration Manager, które zostały wybrane w poprzednim kroku.  

     Aplikacji programu Configuration Manager są instalowane za pomocą poniższych kroków sekwencji zadań w **instalowanie aplikacji** w sekwencji zadań:  

    -   **Konwertowanie listy na dwie cyfry**  

    -   **Instalowanie aplikacji**  

8.  Sekwencja zadań wykonuje następujące zadania w **OSD wyników i Branding** grupy przed rozpoczęciem docelowy system operacyjny po raz pierwszy:  

    -   Kopiuje informacje używane do OSDResults.exe %WINDIR%\UDI folderu na komputerze docelowym w **pamięci podręcznej OSD wyniki** krok sekwencji zadań  

    -   Rejestruje utworzonego w kroku 6 dla aplikacji programu Configuration Manager w rejestrze na komputerze docelowym w zmiennych sekwencji zadań **znakowania na Reg** i **znakowania na Reg x64** czynności sekwencji zadań  

         Zmienne sekwencji zadań są zapisywane w następującej lokalizacji w rejestrze:  

         **HKEY_LOCAL_MACHINE\Software\Microsoft\MPSD\OSD**  

    -   Konfiguruje docelowy system operacyjny do automatycznego uruchamiania OSDResults.exe podczas uruchamiania komputera przed ekranu logowania systemu Windows w **Uruchom wyniki OSD** krok sekwencji zadań  

    -   Konfiguruje docelowy system operacyjny do automatycznego uruchamiania AppInstall.exe po zalogowaniu użytkownika na komputerze po raz pierwszy w **Uruchom wyniki OSD** krok sekwencji zadań  

    -   Konfiguruje zadania dla docelowego systemu operacyjnego, aby usunąć %WINDIR%\UDI folder jeden miesiąc od daty wdrożenia  

9. Na komputerze docelowym jest uruchomiona, a następnie uruchamiany jest OSDResults.exe.  

     Aby uzyskać więcej informacji o OSDResults.exe, zobacz [odwołania OSDResults](#OSDResultsReference).  

10. Użytkownik loguje się do komputera docelowego, a AppInstall.exe uruchamia się automatycznie.  

11. AppInstall sprawdza, czy aktualnie zalogowany użytkownik jest użytkownikiem podstawowym, który został skonfigurowany w UDA.  

     A *głównego użytkownika* jest użytkownik użyje urządzenia regularnie i jest uznawany za właściciela lub jednego właściciela urządzenia.  

     Jeśli aktualnie zalogowany użytkownik jest:  

    -   Nie użytkownikiem podstawowym, a następnie zatrzymuje AppInstall.exe  

    -   Podstawowy użytkownik, następnie AppInstall.exe odczytuje wpisy rejestru zapisany w kroku 8 w celu określenia, które aplikacje zostały zainstalowane  

12. AppIntaller łączy do programu Configuration Manager i odczytuje katalogu aplikacji, wykonując następujące czynności:  

    1.  AppInstall będzie czekać 5 minut po jego uruchomieniu umożliwić zasady programu Configuration Manager, które mają być dostępne.  

    2.  Po 5 minutach AppInstall próbuje nawiązać połączenie z katalogiem aplikacji.  

    3.  Jeśli AppInstall nie może się połączyć, następnie go będzie oczekiwał na pewien czas, przed podjęciem próby ponownego łączenia.  

    4.  AppInstall próbuje połączyć się maksymalnie pięć razy przed zakończeniem.  

     Można skonfigurować opóźnienie połączenia limitu czasu i liczby ponownych prób dla AppInstall przy użyciu pliku AppInstall.exe.config, który znajduje się w folderze Tools\OSDResults w pakiecie programu Configuration Manager plików zestawu MDT. 11 tabeli wymieniono ustawienia konfiguracji w pliku AppInstall.exe.config.  

### <a name="table-11-configuration-settings-in-the-appinstallexeconfig-file"></a>Tabela 11. Ustawienia konfiguracji w pliku AppInstall.exe.config  

|**Ustawienie**|**Opis**|  
|-|-|  
|**timeoutMinutes**|To ustawienie pozwala określić czas dla AppInstall oczekiwania na odpowiedź z katalogu aplikacji programu Configuration Manager przed przekroczeniem limitu czasu. Wartość jest określana w minutach. Wartość domyślna to ustawienie jest **5**.|  
|**delayTimer**|To ustawienie pozwala określić czas dla AppInstall oczekiwania przed przystąpieniem do połączenia z katalogiem aplikacji programu Configuration Manager. Wartość jest określana w minutach. Wartość domyślna to ustawienie jest **5**.|  

1.  AppInstall porównuje listę aplikacji w rejestrze z listy aplikacje z katalogu aplikacji Configuration Manager dla aktualnie zalogowanego użytkownika.  

     Jeśli aplikacja odnaleziony w rejestrze:  

    -   Jest dostępna w katalogu aplikacji, a następnie AppInstall.exe mapuje aplikacje i identyfikuje aplikacji, co istniejący zarówno w rejestrze i w katalogu aplikacji. Te aplikacje będą używane w następnym kroku.  

    -   Nie jest dostępna w katalogu aplikacji, a następnie AppInstall.exe nie powoduje mapowania. Te aplikacje nie będą obowiązywać w następnym kroku.  

2.  AppInstall używa interfejsów API programu Configuration Manager do inicjowania instalacji aplikacji mapowane.  

     Aplikacje używane w tym kroku zostały zamapowane w poprzednim kroku. To znaczy zostały zarówno wymienionych w rejestrze i w katalogu aplikacji.  

3.  W ramach procesu instalacji program Configuration Manager wykryje, czy aplikacja jest już zainstalowana.  

     Ponieważ aplikacja została już zainstalowana, rekordy programu Configuration Manager, że aplikacja została pomyślnie wdrożona na tego użytkownika, a aplikacja będzie wyświetlane w Centrum oprogramowania dla tego użytkownika. Configuration Manager rozpoczyna zarządzanie i monitorowanie aplikacji dla tego użytkownika.  

4.  Po 1 miesiąc zadania utworzone na komputerze docelowym w kroku 8 uruchamia i usuwa %WINDIR%\UDI folder.  

     Folder jest przechowywany dla 1 miesiąc, dzięki czemu użytkownicy podstawowi mógł być dziennika na i uruchom AppInstall.exe.  

###  <a name="UDIStageReference"></a>Etap UDI — informacje  
 Scenariusze wdrożenia zestawu MDT Użyj co najmniej jeden UDI [etapu](#Stage). Na każdym z etapów UDI używane w scenariuszach wdrożenia zestawu MDT opisanej w sekcji kolejne w kontekście tego scenariusza wdrożenia zestawu MDT. W niektórych scenariuszach wdrożenia zestawu MDT jest używany tylko jeden etap. W innych scenariuszach wdrożenia zestawu MDT wiele etapów są używane w ramach tego scenariusza. Aby uzyskać więcej informacji na temat scenariuszy wdrożenia zestawu MDT, zobacz sekcję "Identyfikowanie scenariuszy wdrożenia" w dokumencie MDT *przy użyciu programu Microsoft Deployment Toolkit.*  

 Tabela 12 zawiera listę scenariuszy wdrożenia zestawu MDT i zawiera krótki opis każdego, jak każdego scenariusza jest zaznaczone, a które stany UDI są używane w każdym ze scenariuszy wdrażania. Zestaw MDT automatycznie określa scenariusz wdrożenia zestawu MDT używany oparte na szablon sekwencji zadań zestawu MDT, który służy do tworzenia sekwencji zadań i jak zainicjowaniu sekwencji zadań.  

 Na każdym z etapów UDI używane w scenariuszach wdrożenia zestawu MDT opisanej w sekcji kolejne w kontekście tego scenariusza wdrożenia zestawu MDT. W niektórych scenariuszach wdrożenia zestawu MDT jest używany tylko jeden etap. W innych scenariuszach wdrożenia zestawu MDT wiele etapów są używane w ramach tego scenariusza. Aby uzyskać więcej informacji na temat scenariuszy wdrożenia zestawu MDT, zobacz sekcję "Identyfikowanie scenariuszy wdrożenia" w dokumencie MDT *przy użyciu programu Microsoft Deployment Toolkit.*  

### <a name="table-12-mdt-deployment-scenarios-and-udi-stages"></a>Tabela 12. UDI etapów i scenariusze wdrożenia zestawu MDT  

|**Scenariusz**|**Opis**|   
|-|-|  
|Nowy komputer|Zestaw MDT dla UDI automatycznie wybiera w tym scenariuszu podczas możesz:<br /><br /> -Utwórz sekwencję zadań anonsowany, za pomocą sekwencji zadań instalacji sterowanej szablonu sekwencji zadań<br /><br /> -Uruchomienia sekwencji zadań w środowisku Windows PE za pomocą rozruchu w środowisku PXE, nośnika rozruchowego sekwencji zadań lub wstępnie przygotowanego nośnika dla NEWCOMPUTER. Etap wstępnie przygotowanych<br /><br /> W tym scenariuszu można z tradycyjnego wdrożenia lub wdrożenia z nośników wstępnie przygotowanych jako obsługiwane w programie Configuration Manager. Uruchom Kreatora UDI z następujących etapów UDI na potrzeby obsługi każdego typu wdrożenia:<br /><br /> - **Etap NEWCOMPUTER.** Ten etap uruchomieniu kreatora UDI **sekwencji zadań instalacji sterowanej** sekwencji zadań, jeśli obraz systemu operacyjnego są przechowywane w punktach dystrybucji. Aby uzyskać więcej informacji, zobacz [etap NEWCOMPUTER](#NEWCOMPUTERStage).<br /><br /> -                         **NEWCOMPUTER. Wstępne przygotowanie etapu.** Ten etap uruchomieniu kreatora UDI **sekwencji zadań instalacji sterowanej** sekwencji zadań, jeśli obraz systemu operacyjnego są przechowywane na dysku lokalnym na komputerze docelowym (wstępnie). Aby uzyskać więcej informacji, zobacz [NEWCOMPUTER. Wstępnie przygotowane etap](#NEWCOMPUTERPrestagedStage).|  
|Odśwież komputer|Zestaw MDT dla UDI automatycznie wybiera w tym scenariuszu podczas możesz:<br /><br /> -Utwórz sekwencję zadań anonsowany, za pomocą sekwencji zadań instalacji sterowanej szablonu sekwencji zadań<br /><br /> -Uruchomienia sekwencji zadań w istniejącego systemu operacyjnego na komputerze docelowym (nie w systemie Windows PE)<br /><br /> -Uruchomiono kreatora UDI etapu odświeżania, aby obsługiwać ten scenariusz wdrażania. Aby uzyskać więcej informacji, zobacz [ODŚWIEŻ etap](#REFRESHStage).|  
|Zastąpienie komputera|Taki scenariusz obejmuje istniejącego komputera i komputera zastąpienia. Sekwencję zadań oddzielne jest utworzony i uruchom na każdym komputerze, zgodnie z opisem w poniższej procedurze:<br /><br /> -                          **Na istniejącego komputera.** Zestaw MDT dla UDI automatycznie wybiera tej części scenariusza podczas możesz:<br /><br /> -Utwórz sekwencję zadań anonsowany, przy użyciu szablonu sekwencji zadań instalacji sterowanej Zastąp sekwencji zadań<br /><br /> Uruchom sekwencję zadań w istniejącego systemu operacyjnego na komputerze docelowym (nie w systemie Windows PE)<br /><br /> Kreator UDI jest uruchamiana z następujących etapów UDI, aby obsługiwać ten scenariusz wdrażania:<br /><br /> - **Zastąp etapu.** Ten etap jest uruchamiana w istniejącego systemu operacyjnego Windows i przechwytywanie informacji o konfiguracji z poziomu systemu Windows.<br /><br /> -                          **ZASTĄP. Etap środowiska WinPE.** Ten etap, jest uruchamiany w środowisku Windows PE i zakończeniu przechwytywanie informacji o konfiguracji z istniejącego komputera — na przykład uruchamiania narzędzia USMT i przechwytywanie użytkownika danych o stanie migracji.<br /><br /> Dane stanu użytkownika są przechwytywane do udostępnionego folderu sieciowego lub na lokalnym dysku USB.<br /><br /> Aby uzyskać więcej informacji na ZASTĘPOWANIE i ZAMIEŃ. Etapy środowiska WinPE, zobacz [ZAMIEŃ i ZAMIEŃ. Etapy WinPE](#REPLACEandREPLACEWinPEStages).<br /><br /> -                          **Na komputerze zastąpienia.** Ta część scenariusza jest taka sama jak w scenariuszu z nowym komputerze, ale jest przywracany stan użytkownika przechwyconych w poprzednim kroku. Zestaw MDT dla UDI automatycznie wybiera tej części scenariusza podczas możesz:<br /><br /> -Utwórz sekwencję zadań anonsowany, za pomocą sekwencji zadań instalacji sterowanej szablonu sekwencji zadań<br /><br /> -Uruchomienia sekwencji zadań w środowisku Windows PE za pomocą rozruchu w środowisku PXE, nośnika rozruchowego sekwencji zadań lub wstępnie przygotowanego nośnika dla NEWCOMPUTER. Etap wstępnie przygotowanego.<br /><br /> Ta część tego scenariusza można z tradycyjnego wdrożenia lub wdrożenia z nośników wstępnie przygotowanych jako obsługiwane w programie Configuration Manager. W ramach tej części scenariusza po przywróceniu danych migracji stanu użytkownika. Kreator UDI jest uruchamiana z następujących etapów UDI na potrzeby obsługi każdego typu wdrożenia:<br /><br /> -                          **Etap NEWCOMPUTER.** Ten etap uruchomieniu kreatora UDI **sekwencji zadań instalacji sterowanej** sekwencji zadań, jeśli obraz systemu operacyjnego są przechowywane w punktach dystrybucji. Aby uzyskać więcej informacji, zobacz [etap NEWCOMPUTER](#NEWCOMPUTERStage).<br /><br /> -                          **NEWCOMPUTER. Wstępne przygotowanie etapu.** Ten etap uruchomieniu kreatora UDI **sekwencji zadań instalacji sterowanej** sekwencji zadań, jeśli obraz systemu operacyjnego są przechowywane na dysku lokalnym na komputerze docelowym (wstępnie). Aby uzyskać więcej informacji, zobacz [NEWCOMPUTER. Wstępnie przygotowane etap](#NEWCOMPUTERPrestagedStage).|  

#####  <a name="NEWCOMPUTERStage"></a>Etap NEWCOMPUTER  
 Rysunek 1 przedstawiono użycie etapu NEWCOMPUTER w sekwencji zadań utworzonych przy użyciu użytkownika\-szablonu sekwencji zadań zmiennych sekwencji zadań instalacji. Główną różnicą między sekwencje zadań, wywołując etap NEWCOMPUTER i NEWCOMPUTER. Wstępnie przygotowane etap jest to, że sekwencja zadań podczas wywoływania NEWCOMPUTER. Wstępnie przygotowany etapie nie można uruchomić **Zastosuj obraz systemu operacyjnego** sekwencji zadań, ponieważ znajduje się już w obrazie systemu operacyjnego na komputerze docelowym.  

 ![UDI — informacje 1](media/UDIReference1.jpg)  

 **Rysunek SEQ Figure \\ \* ARABIC 1. Przepływ procesu dla etapu NEWCOMPUTER**  

#####  <a name="NEWCOMPUTERPrestagedStage"></a>NEWCOMPUTER. Etap wstępnie przygotowanych  
 Rysunek 2 przedstawia wysoki\-przebieg procesu poziomu NEWCOMPUTER. Wstępnie przygotowane etap sekwencji zadań utworzonych przy użyciu użytkownika\-szablonu sekwencji zadań zmiennych sekwencji zadań instalacji. Główną różnicą między sekwencje zadań, wywołując etap NEWCOMPUTER i NEWCOMPUTER. Wstępnie przygotowane etap jest to, że sekwencja zadań podczas wywoływania NEWCOMPUTER. Wstępnie przygotowany etapie nie można uruchomić **Zastosuj obraz systemu operacyjnego** sekwencji zadań, ponieważ znajduje się już w obrazie systemu operacyjnego na komputerze docelowym.  

 ![UDI — informacje 2](media/UDIReference2.jpg)  

 **Rysunek 2. Przepływ procesu dla NEWCOMPUTER. Etap wstępnie przygotowanych**  

####  <a name="REFRESHStage"></a>ODŚWIEŻ etap  
 Rysunek 3 przedstawia wysoki\-przebieg procesu poziomu odświeżania etapem w sekwencji zadań utworzonych przy użyciu użytkownika\-szablonu sekwencji zadań zmiennych sekwencji zadań instalacji.  

 ![UDI — informacje 3](media/UDIReference3.jpg)  

 **Rysunek SEQ Figure \\ \* ARABIC 3. Przepływ procesu dla etapu odświeżania**  

####  <a name="REPLACEandREPLACEWinPEStages"></a>Zastąp i Zastąp. Etapy środowiska WinPE  
 Rysunek 4 przedstawia wysoki\-przebieg procesu poziomu ZAMIEŃ i ZAMIEŃ. Etapy środowiska WinPE w sekwencji zadań utworzonych przy użyciu użytkownika\-szablonu sekwencji zadań zmiennych instalacji Zastąp sekwencji zadań.  

 ![UDI — informacje 4](media/UDIReference4.jpg)  

 **Rysunek 4. Przepływ procesu dla ZAMIEŃ i ZAMIEŃ. Etapy środowiska WinPE**  

###  <a name="UDITaskReference"></a>Zadanie UDI — informacje  
 *Zadania UDI* to oprogramowanie, które jest uruchamiane na stronie kreatora, wykonywania określonych funkcji. W niektórych przypadkach te zadania są używane do Sprawdź, czy komputer docelowy jest gotowa do wdrożenia. Inne zadania mogą posłużyć do wykonania kroków wdrażania, takich jak kopiowanie plików konfiguracji lub wynik.  

> [!NOTE]
>  **Dalej** przycisk na stronie kreatora, których zadania są uruchamiane zostanie wyłączony, jeśli zadań zakończy się stanem zakończenia ostrzeżenia lub błędu.  

 Obejmuje to odwołanie:  

-   Omówienie UDI zadania, zgodnie z opisem w [UDI Omówienie zadań](#UDITaskOverview)  

-   Opis ustawienia konfiguracji dla UDI zadania, zgodnie z opisem w [ustawienia konfiguracji UDI zadań](#UDITaskConfigurationSettings)  

-   Opis wbudowanych\-w UDI poprawności, które są dostarczane z zestawu MDT, zgodnie z opisem w [wbudowane\-UDI zadań](#BuiltinUDITasks)  

####  <a name="UDITaskOverview"></a>Omówienie zadań UDI  
 UDI zadania umożliwiają uruchamianie oprogramowania na komputerze docelowym, który pomaga w procesie wdrażania. UDI zawiera kilka wbudowanych\-w zadań, które umożliwiają wykonywanie typowych zadań, na przykład zagwarantowaniu, że komputer docelowy nie jest zasilany z baterii i jest połączony z połączeniem sieci przewodowej.  

 Oprócz wbudowanych\-UDI zadań, umożliwia tworzenie niestandardowych zadań UDI przy użyciu zestawu UDI software development kit \(SDK\). Aby uzyskać więcej informacji na temat tworzenia niestandardowych zadań UDI przy użyciu zestawu SDK UDI, zobacz *użytkownika\-zmiennych przewodnik deweloperów instalacji*.  

####  <a name="UDITaskConfigurationSettings"></a>Ustawienia konfiguracji UDI zadań  
 Możesz zarządzać zadaniami za pomocą projektanta Kreatora instalacji UDI. Można dodać zadania, Usuń zadania i edytować konfiguracji zadania w projektanta Kreatora instalacji UDI. Ustawienia konfiguracji dla zadania są przechowywane w pliku konfiguracyjnym UDI kreatora i są odczytywane przez kreatora UDI, gdy zostanie wyświetlona strona kreatora, który zawiera zadania.  

 Zadania UTI mają niektóre ustawienia konfiguracji, które są wspólne dla wszystkich zadań UDI wymienionych w tabeli 13. Ustawienia konfiguracji, które są specyficzne dla każdego zadania UDI można znaleźć w odpowiedniej sekcji [wbudowane\-w zadaniach UDI](#BuiltinUDITasks).  

### <a name="table-13-configuration-settings-common-to-all-udi-tasks"></a>Tabela 13. Typowe ustawienia konfiguracji do wszystkich zadań UDI  

|**Zadanie**|**Opis**|  
|-|-|  
|**Nazwa pliku mapy bitowej**|Ten parametr określa grafiki służy do określania typu zadania.|  
|**Nazwa wyświetlana**|Określa nazwę zadania, które jest wyświetlane na stronie kreatora, gdy zadanie zostanie uruchomione.|  
|**Wartości kodów zakończenia**|Określa listę możliwych kodów powrotnych zadania. Element istnieje na liście każdego możliwe kodu powrotnego.|  
|**Wartości kodów błędów**|Określa listę możliwych nieoczekiwanego wyjątku, które można napotkać \(zgłoszony\) przez zadanie. Element istnieje na liście dla każdego z dopuszczalnych wyjątków.|  

####  <a name="BuiltinUDITasks"></a>Wbudowane\-UDI zadań  
 Tabela 14 zawiera listę wbudowanych\-UDI zadań. Każdy utworzony\-w UDI zadań została szczegółowo opisana w sekcji kolejne.  

### <a name="table-14-built-in-udi-tasks"></a>Tabela 14. Wbudowane\-UDI zadań  

|**Zadanie**|**Opis**|  
|-|-|  
|[Zasilacz wyboru](#ACPowerCheck)|To zadanie UDI służy do identyfikowania, czy komputer docelowy jest połączony z zasilaniem, a nie wyłącznie na poziomie naładowania baterii.|  
|[Odnajdywanie aplikacji](#ApplicationDiscovery)|To zadanie UDI służy do odnajdywania aplikacji zainstalowanych na komputerze docelowym.|  
|[CheckSMSFolderOnUSB](#CheckSMSFolderOnUSB)|To zadanie UDI służy do określania czy \_SMSTaskSequence folder znajduje się na dysku USB na komputerze docelowym.|  
|[Zadanie kopiowania plików](#CopyFilesTask)|To zadanie UDI służy do kopiowania plików, podczas gdy Kreator UDI jest uruchomiony na komputerze docelowym.|  
|[Powłoka wykonania zadania](#ShellExecuteTask)|To zadanie UDI służy do uruchomienia oprogramowania, które może być inicjowana przy użyciu wiersza polecenia.|  
|[Sprawdź sieci przewodowej](#WiredNetworkCheck)|To zadanie UDI służy do identyfikowania, czy komputer docelowy jest połączony z siecią przewodową nie nawiązano połączenie przy użyciu połączenia sieci bezprzewodowej.|  

#####  <a name="ACPowerCheck"></a>Zasilacz wyboru  
 To zadanie UDI służy do identyfikowania, czy komputer docelowy jest podłączony do zasilania Sieciowego. To zadanie używa tylko tych parametrów, które są wspólne dla wszystkich zadań UDI. Aby uzyskać więcej informacji na temat tych parametrów, zobacz [ustawienia konfiguracji zadania UDI](#UDITaskConfigurationSettings).  

 Tabela 15 zawiera błąd i kodów zakończenia **Sprawdź zasilania AC** generuje zadań.  

### <a name="table-15-error-and-exit-codes-for-the-ac-power-check-task"></a>Tabela 15. Zadanie sprawdzania błędów i kody wyjścia dla zasilania z sieci  

|**Kod błędu lub zakończenia**|**Wartość**|**Stan**|  
|-|-|-|  
|Zakończ|**0**|**Powodzenie**, co oznacza, że komputer docelowy jest podłączony do zasilania Sieciowego|  
|Zakończ|**\***|**Błąd**, co oznacza, że komputer docelowy nie jest podłączony do zasilania Sieciowego|  

#####  <a name="ApplicationDiscovery"></a>Odnajdywanie aplikacji  
 To zadanie UDI służy do odnajdywania aplikacji zainstalowanych na komputerze docelowym.  

 Tabela 16 opisano parametry, który **odnajdywania aplikacji** zadań używa.  

### <a name="table-16-parameters-used-by-the-application-discovery-task"></a>Tabela 16. Parametry używane przez zadanie wykrywania aplikacji  

|**Zadanie**|**Opis**|  
|-|-|  
|**Readcfg**|Ten parametr określa w pełni kwalifikowaną lub względną ścieżkę do lokalizacji pliku .app, który zawiera listę aplikacji dla zadań odnaleźć. Plik .app zawiera listę dostępnego oprogramowania elementów, z których użytkownik może wybrać.<br /><br /> **Odnajdywania aplikacji** zadania odczytuje plik .app i określa, czy te elementy oprogramowania jest zainstalowana. Jeśli jest zainstalowany element oprogramowania, jest dodania elementu do pliku określonego w **Writecfg** parametru.<br /><br /> Upewnij się, że ten parametr używa tej samej lokalizacji i nazwa pliku jako [ApplicationPage](#ApplicationPage) strony kreatora.|  
|**Writecfg**|Ten parametr określa w pełni kwalifikowaną lub względną ścieżkę do lokalizacji pliku XML, który zawiera listę aplikacji, wykrytych przez zadanie.|  
|**Dziennik**|Ten parametr określa w pełni kwalifikowaną lub względną ścieżkę do lokalizacji pliku dziennika wygenerowane przez to zadanie. Nazwa pliku w pliku dziennika jest informacje.|  

 Oprócz parametrów w tabeli 16 to zadanie używa parametrów, które są wspólne dla wszystkich zadań UDI. Aby uzyskać więcej informacji o tych wspólnych parametrów, zobacz [ustawienia konfiguracji zadania UDI](#UDITaskConfigurationSettings).  

 Tabela 17 zawiera błąd i kodów zakończenia **odnajdywania aplikacji** generuje zadań.  

### <a name="table-17-error-and-exit-codes-for-the-application-discovery-task"></a>Tabela 17. Błąd i kody zakończenia zadania odnajdywania aplikacji  

|**Kod błędu lub zakończenia**|**Wartość**|**Stan i opis**|  
|-|-|-|  
|Zakończ|**0**|**Powodzenie**, co oznacza, że zadanie pomyślnie skanowania w poszukiwaniu aplikacji|  
|Zakończ|**\***|**Ostrzeżenie**, co oznacza, że z nieznanej przyczyny nie może uruchomić aparatu odnajdywania aplikacji|  
|Zakończ|**1**|**Ostrzeżenie**, co oznacza, że aparat odnajdowania Aplikacja napotkała co najmniej jedno ostrzeżenie|  
|Zakończ|**16777216**|**Ostrzeżenie**, co oznacza, że podczas inicjowania aplikacji aparat odnajdowania napotkano błędy krytyczne|  
|Zakończ|**33554432**|**Ostrzeżenie**, co oznacza, że podczas przetwarzania wzorca listy aplikacji napotkano błędy krytyczne|  

#####  <a name="CheckSMSFolderOnUSB"></a>CheckSMSFolderOnUSB  
 To zadanie UDI służy do identyfikowania czy \_SMSTaskSequence folder znajduje się na dysku USB na komputerze docelowym. Domyślnie program sequencer zadań programu Configuration Manager umieszcza \_SMSTaskSequence folderu na dysku z najwięcej wolnego miejsca. Może to spowodować problemy w dalszej części procesu wdrażania, jeśli dysk USB zostanie usunięty.  

 To zadanie sprawdza, czy folder znajduje się na dysku USB i uniemożliwia wdrożenie przed kontynuowaniem, jeśli jest. To zadanie używa tylko tych parametrów, które są wspólne dla wszystkich zadań UDI. Aby uzyskać więcej informacji na temat tych parametrów, zobacz [ustawienia konfiguracji zadania UDI](#UDITaskConfigurationSettings).  

 Jeśli \_SMSTaskSequence folder znajduje się na dysku USB, to zadanie nie powiedzie się i uniemożliwia wdrożenia przed kontynuowaniem. Aby rozwiązać ten problem i wdrażanie, wykonaj następujące czynności:  

1.  Odłącz dysk USB z komputera docelowego przed uruchomieniem sekwencji zadań.  

2.  Uruchom sekwencję zadań.  

3.  Zaczekaj, aż zostanie uruchomiony Kreator UDI.  

4.  Podłącz dysk USB.  

5.  Ukończ pracę kreatora UDI.  

 Tabela 18 zawiera błąd i kodów zakończenia **CheckSMSFolderOnUSB** generuje zadań.  

### <a name="table-18-error-and-exit-codes-for-the-checksmsfolderonusb-task"></a>Tabela 18. Błąd i kody zakończenia zadania CheckSMSFolderOnUSB  

|**Kod błędu lub zakończenia**|**Wartość**|**Stan**|  
|-|-|-|  
|Zakończ|**0**|**Powodzenie**, co oznacza, że \_SMSTaskSequence folder nie znajduje się na dysku USB i można kontynuować wdrożenia.|  
|Zakończ|**\***|**Błąd**, co oznacza, że \_SMSTaskSequence folder znajduje się na dysku USB i wdrożenia nie może kontynuować.|  

#####  <a name="CopyFilesTask"></a>Zadanie kopiowania plików  
 To zadanie UDI służy do kopiowania plików, podczas gdy Kreator UDI jest uruchomiony na komputerze docelowym.  

 Tabela 19 opisano parametry, który **kopiowania plików** zadań używa.  

### <a name="table-19-parameters-used-by-the-copy-files-task"></a>Tabela 19. Parametry używane przez zadanie kopiowania plików  

|**Zadanie**|**Opis**|  
|-|-|  
|**Obiekt źródłowy**|Ten parametr określa w pełni kwalifikowaną lub względną ścieżkę do pliku źródłowego, który może zawierać symboli wieloznacznych, aby skopiować wielu plików za pomocą jednego zadania.|  
|**Miejsce docelowe**|Ten parametr określa w pełni kwalifikowaną lub względną ścieżkę do pliku docelowego bez nazwy pliku.|  

 Oprócz parametrów w tabeli 19 to zadanie używa parametrów wspólne dla wszystkich zadań UDI. Aby uzyskać więcej informacji na temat tych parametrów, zobacz [ustawienia konfiguracji zadania UDI](#UDITaskConfigurationSettings).  

 Tabela 20 zawiera błąd i kodów zakończenia **kopiowania plików** generuje zadań.  

### <a name="table-20-error-and-exit-codes-for-the-copy-files-task"></a>Tabela 20. Błąd i kody zakończenia zadania kopiowania plików  

|**Kod błędu lub zakończenia**|**Wartość**|**Stan i opis**|  
|-|-|-|  
|Zakończ|**0**|**Powodzenie**, co oznacza, że proces kopiowania powiodło się|  
|Zakończ|**\***|**Błąd**, co oznacza, że proces kopiowania nie powiodło się|  
|Błąd|**\-1**|**Błąd**, co oznacza, że proces kopiowania nie powiodło się|  

#####  <a name="ShellExecuteTask"></a>Powłoka wykonania zadania  
 To zadanie UDI służy do uruchomienia oprogramowania, które może być inicjowana przy użyciu wiersza polecenia.  

 Tabela 21 zawiera listę parametrów który **wykonanie powłoki** zadań używa.  

### <a name="table-21-parameters-used-by-the-shell-execute-task"></a>Tabela 21. Parametry używane przez powłokę wykonywanie zadania  

|**Zadanie**|**Opis**|  
|-|-|  
|**Nazwa pliku**|Ten parametr określa w pełni kwalifikowaną lub względną ścieżkę do polecenia do uruchomienia zadania.|  
|**Parametry**|Ten parametr określa polecenie\-wiersz parametrów, które mają być podane podczas uruchamiania polecenia.|  

 Oprócz parametrów w tabeli 21 to zadanie używa parametrów wspólne dla wszystkich zadań UDI. Aby uzyskać więcej informacji na temat tych parametrów, zobacz [ustawienia konfiguracji zadania UDI](#UDITaskConfigurationSettings).  

 Można również uruchamiać skrypty języka Visual Basic przeznaczonych do uruchamiania przy użyciu cscript.exe **wykonanie powłoki** zadań. Aby uruchamiać skrypty języka Visual Basic, wykonaj następujące czynności:  

1.  Wpisz następujący tekst w **Filename** parametru:  

    ```  
    %windir%\system32\cscript.exe  
    ```  

2.  Nazwa typu pliku skryptu języka Visual Basic \(pliku vbs\) w **parametry** parametru, w tym dowolne polecenie\-wiersz Parametry skryptu.  

     Na przykład, aby uruchomić skrypt w języku Visual Basic o nazwie *SelfTest.vbs* z wartością parametru **debugowania**, wpisz następujące polecenie \(gdzie *skryptu\_ścieżka*jest w pełni kwalifikowana ścieżka do pliku SelfTest.vbs\):  

    ```  
    <script_path>\SelfTest.vbs Debug  
    ```  

 Tabela 22 zawiera listę typowych błędów i kodów zakończenia **wykonanie powłoki** generuje zadań.  

> [!NOTE]
>  Na podstawie każdego określonego zadania **wykonanie powłoki** zadanie ma unikatowy zestaw kodów błędów i zakończenia. Sprawdź, czy kody powrotu do oprogramowania, które są uruchomione przy użyciu tego zadania.  

### <a name="table-22-common-error-and-exit-codes-for-the-shell-execute-task"></a>Tabela 22. Typowym błędem i kody wyjścia dla zadania wykonywania powłoki  

|**Kod błędu lub zakończenia**|**Wartość**|**Stan i opis**|  
|-|-|-|  
|Zakończ|**0**|**Powodzenie**, co oznacza, że zadanie zakończyło się pomyślnie|  
|Zakończ|**\***|**Błąd**, co oznacza, że zadanie nie powiodło się|  

#####  <a name="WiredNetworkCheck"></a>Sprawdź sieci przewodowej  
 To zadanie UDI służy do określenia, czy komputer docelowy jest połączony z siecią przewodową, nie za pomocą połączenia sieci bezprzewodowej. To zadanie używa tylko parametry wspólne dla wszystkich zadań UDI. Aby uzyskać więcej informacji na temat tych parametrów, zobacz [ustawienia konfiguracji zadania UDI](#UDITaskConfigurationSettings).  

 Tabela 23 zawiera listę typowych błędów i kodów zakończenia **Sprawdź sieci przewodowej** generuje zadań.  

### <a name="table-23-error-and-exit-codes-for-the-wired-network-check-task"></a>Tabela 23. Zadanie sprawdzania błędów i kody wyjścia dla sieci przewodowej  

|**Kod błędu lub zakończenia**|**Wartość**|**Stan i opis**|  
|-|-|-|  
|Zakończ|**0**|**Powodzenie**, co oznacza, że komputer docelowy jest podłączony do sieci przewodowej|  
|Zakończ|**\***|**Błąd**, co oznacza, że komputer docelowy nie jest połączony z siecią przewodową|  

###  <a name="UDIValidatorReference"></a>Moduł sprawdzania poprawności UDI — informacje  
 UDI moduły są używane do sprawdzania poprawności wartości wprowadzone w polach tekstowych na stronach kreatora. Moduł weryfikacji UDI wykrycie nieprawidłowy wpis dla pierwszego błędu napotkano w dolnej części strony kreatora zostanie wyświetlony komunikat. Następny komunikat o błędzie weryfikacji, jeśli istnieje, jest wyświetlany po rozwiązaniu pierwszy błąd sprawdzania poprawności. Ten proces jest kontynuowany do momentu rozwiązania są wszystkie błędy weryfikacji. **Dalej** przycisk jest niedostępny, dopóki wszystkie błędy weryfikacji na stronie kreatora zostaną rozwiązane.  

 Obejmuje to odwołanie:  

-   Omówienie UDI modułów sprawdzania poprawności, zgodnie z opisem w [UDI omówienie modułu sprawdzania poprawności](#UDIValidatorOverview)  

-   Opis wbudowanych\-w moduły UDI podany zestaw mdt, zgodnie z opisem w [wbudowane\-w UDI modułów sprawdzania poprawności](#BuiltinUDIValidators)  

####  <a name="UDIValidatorOverview"></a>Omówienie modułu sprawdzania poprawności UDI  
 UDI moduły są używane do pomocy, dzięki czemu użytkownicy podadzą poprawne informacje w polach tekstowych na stronach kreatora, w Kreatorze UDI. UDI zawiera kilka wbudowanych\-w moduły, które wykonania typowych operacji sprawdzania poprawności z pola służące do wprowadzania tekstu, na przykład uniemożliwienie użytkownikom wprowadzanie nieprawidłowe znaki lub zapewnia, że pole jest pomoc nie jest pusta.  

 Oprócz wbudowanych\-w UDI modułów sprawdzania poprawności, można tworzyć niestandardowe moduły UDI przy użyciu zestawu SDK UDI. Aby uzyskać więcej informacji na temat tworzenia niestandardowych UDI moduły weryfikacji przy użyciu zestawu SDK UDI, zobacz dokument MDT *użytkownika\-zmiennych przewodnik deweloperów instalacji*.  

####  <a name="BuiltinUDIValidators"></a>UDI wbudowanych modułów sprawdzania poprawności  
 Tabela 24 zawiera wbudowane moduły UDI. W kolejnych sekcji omówiono każdego wbudowany moduł sprawdzania poprawności. Jeśli moduł weryfikacji wykryje nieprawidłowy wpis w polu tekstowym, na stronie kreatora zostanie wyświetlony komunikat i **dalej** przycisk jest niedostępny, dopóki wszystkie nieprawidłowe wpisy zostaną rozwiązane.  

### <a name="table-24-built-in-udi-validators"></a>Tabela 24. UDI wbudowanych modułów sprawdzania poprawności  

|**Moduł sprawdzania poprawności**|**Opis**|  
|-|-|  
|[InvalidChars](#InvalidChars)|Ten moduł weryfikacji identyfikuje nieprawidłowych znaków, które zostały wprowadzone z listy, które można skonfigurować.|  
|[NamedPattern](#NamedPattern)|Ten moduł weryfikacji pomaga, upewnij się, że tekst jest zgodna ze wzorcem wstępnie zdefiniowane.|  
|[NonEmpty](#NonEmpty)|Ten moduł weryfikacji służy do wymagają tekst w polu.|  
|[Wyrażenia regularnego](#RegEx)|Ten moduł weryfikacji umożliwia upewnij się, że tekst pasuje do wyrażenia regularnego, określony jako część modułu sprawdzania poprawności.|  

#####  <a name="InvalidChars"></a>InvalidChars  
 Ten moduł weryfikacji uniemożliwia użytkownikom wprowadzanie określonych znaków. **Komunikat** pole umożliwia wpisz wiadomość, która jest wyświetlana, jeśli pole tekstowe zawiera nieprawidłowych znaków. **Nieprawidłowe znaki** pole służy do wprowadzania znaków, które są uznawane za nieprawidłowe. Znaki są wprowadzane bez spacji między nimi.  

#####  <a name="NamedPattern"></a>NamedPattern  
 Ten moduł weryfikacji pomaga, upewnij się, że tekst jest zgodna ze wzorcem wstępnie zdefiniowane. **Komunikat** pole umożliwia wpisz wiadomość, która jest wyświetlana, jeśli pole tekstowe nie pasuje do wzorca nazwanego. **Wzorzec o nazwie** pole pozwala wprowadzić nazwę wzorca wstępnie zdefiniowane i musi być **Username**, **ComputerName**, lub **grupy roboczej**.  Nazwy są bez uwzględniania wielkości liter.  

#####  <a name="NonEmpty"></a>NonEmpty  
 Użyj tego sprawdzania poprawności, aby wymagać tekst w polu. **Komunikat** pole umożliwia wpisz wiadomość, która jest wyświetlana, jeśli pole tekstowe jest pusta.  

#####  <a name="RegEx"></a>Wyrażenia regularnego  
 Ten moduł weryfikacji umożliwia upewnij się, że tekst pasuje do wyrażenia regularnego, określony jako część modułu sprawdzania poprawności. **Komunikat** pole umożliwia wpisz wiadomość, która jest wyświetlana, jeśli pole tekstowe nie odpowiada wyrażeniu regularnemu. **Wyrażenia regularnego** pole pozwala wprowadzić wyrażenie regularne służące do sprawdzania poprawności. Aby uzyskać więcej informacji o sposobie budowania wyrażeń regularnych dla tego modułu weryfikacji, zobacz [wyrażenia regularne TR1](http://msdn.microsoft.com/library/bb982727.aspx).  

###  <a name="UDIWizardPageReference"></a>UDI — informacje strony kreatora  
 Dodaj UDI [strona kreatora](#WizardPage) etapy z [biblioteki strony](#PageLibrary) w [projektanta Kreatora instalacji UDI](#UDIWizardDesigner). UDI strony kreatora są wyświetlane w [kreatora UDI](#UDIWizard).  

 Obejmuje to odwołanie:  

-   Omówienie UDI stron kreatora, zgodnie z opisem w [Omówienie strony kreatora UDI](#UDIWizardPageOverview)  

-   Opis stron kreatora UDI wbudowanych, dostarczanych z zestawu MDT, zgodnie z opisem w [wbudowane UDI strony kreatora](#BuiltinUDIWizardPages)  

####  <a name="UDIWizardPageOverview"></a>Omówienie strony kreatora UDI  
 Strony kreatora są wyświetlane w [kreatora UDI](#UDIWizard) i zbierać informacje wymagane do ukończenia procesu wdrażania. Możesz utworzyć za pomocą języka C++ w programie Visual Studio stron kreatora. Strony kreatora niestandardowego są zaimplementowane jako biblioteki dll, które odczytuje kreatora UDI.  

 Każda wbudowanych strona kreatora UDI ma odpowiednie UDI [Edytor stron kreatora](#WizardPageEditor), które są używane do konfigurowania strony kreatora w [projektanta Kreatora instalacji UDI](#UDIWizardDesigner).  

 Oprócz wbudowanych UDI stron kreatora można tworzyć niestandardowe strony kreatora UDI przy użyciu zestawu SDK UDI. Aby uzyskać więcej informacji na temat tworzenia niestandardowych stron kreatora UDI przy użyciu zestawu SDK UDI, zobacz dokument MDT *przewodnik dla deweloperów instalacji sterowanej*.  

 Każdej stronie kreatora mogą odwoływać się następujące zmienne:  

-   Zmienne sekwencji zadań  

-   Zmienne pamięci  

-   Zmienne środowiskowe  

 Możesz odwoływać się do sekwencji zadań i zmiennych środowiskowych przez zestawianie zmiennej przy użyciu procentu (%), takich jak *OSDImageIndex %.* Możesz odwoływać się do zmiennych pamięci przez zestawianie zmiennej przy użyciu dolara ($), takich jak *$VolumeArchitecture$.*  

> [!NOTE]
>  Jeśli zmienna sekwencji zadań i zmienną środowiskową mają taką samą nazwę, a następnie zmienną sekwencji zadań mają pierwszeństwo przed zmiennej środowiskowej.  

 Tabela 25 Wyświetla listę zmiennych pamięci, które są ustawione, po uruchomieniu kreatora UDI opis zmienne, i zarówno kreatora UDI odczytuje i zapisuje zmienne podczas uruchamiania.  

### <a name="table-25-memory-variables-set-by-the-udi-wizard-at-startup-and-their-descriptions"></a>Tabela 25. Zmienne pamięci ustawiane przez kreatora UDI przy rozruchu i ich opisy.  

|**Zmienna**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**Ścieżka dziennika**<br /><br /> Określa w pełni kwalifikowana ścieżka do plików dziennika dla Kreatora UDI. Można ustawić tę zmienną na jedną z następujących wartości:<br /><br /> — Wartość w **_SMSTSLogPath** zmienną sekwencji zadań<br /><br /> — Wartość if % TEMP % środowiska zmiennej **_SMSTSLogPath** nie ustawiono zmienną sekwencji zadań|Nie|Tak|  
|**WizardConfigFilename**<br /><br /> Określa nazwę pliku konfiguracji kreatora UDI aktualnie w użyciu. **ApplicationPage** strona kreatora odczytuje wartość tej zmiennej można znaleźć odpowiedniego pliku .app, który zawiera listę aplikacji. Na przykład, jeśli nosi nazwę pliku konfiguracji kreatora UDI *pliku config.xml,* , a następnie strony kreatora będzie szukać odpowiedniego pliku .app (config.xml.app).|Nie|Tak|  

####  <a name="BuiltinUDIWizardPages"></a>Wbudowane UDI strony kreatora  
 26 tabela zawiera listę wbudowanych UDI strony kreatora. Każdy wbudowana strona kreatora UDI została szczegółowo opisana w sekcji kolejne.  

### <a name="table-26-built-in-wizard-pages-and-their-descriptions"></a>26 tabeli. Strony kreatora wbudowanych i ich opisy  

|**Strona kreatora**|**Opis**|  
|-|-|  
|[AdminAccounts](#AdminAccounts)|Ta strona kreatora służy do należy ustawić hasło dla konta administratora lokalnego i dodać innych użytkowników do lokalnej grupy Administratorzy na komputerze docelowym.|  
|[ApplicationPage](#ApplicationPage)|Ta strona kreatora służy do konfigurowania listę aplikacji, które mogą być instalowane podczas instalacji. Te aplikacje mogą zawierać aplikacji lub pakietów i programów z programu Configuration Manager.|  
|[BitLockerPage](#BitLockerPage)|Ta strona kreatora służy do konfigurowania ustawień funkcji BitLocker dla komputera docelowego.|  
|[ComputerPage](#ComputerPage)|Ta strona kreatora służy do konfigurowania nazwę komputera, na komputerze docelowym, domenę lub grupę roboczą do przyłączenia i poświadczenia do użycia w przypadku przyłączania do domeny.|  
|[ConfigScanPage](#ConfigScanPage)|Ta strona kreatora służy do uruchamiania zadań UDI, skanujące konfiguracji komputera docelowego, aby określić, czy komputer docelowy jest gotowy do wdrożenia obrazu systemu operacyjnego. Ta gotowości zawiera wystarczających zasobów systemu i zapewnienie, że wszystkie wstępnie wymagane oprogramowanie jest zainstalowane i właściwie skonfigurowane.|  
|[LanguagePage](#LanguagePage)|Użyj tej strony kreatora, aby określić pakiet językowy, który powinien być zainstalowany, język domyślny dla docelowego systemu operacyjnego, ustawienia regionalne klawiatury i strefy czasowej, w którym komputer będzie fizycznie.|  
|[ProgressPage](#ProgressPage)|Ta strona kreatora służy do uruchamiania zadań UDI, które przechwytują dane migracji stanu użytkownika z komputera docelowego.|  
|[RebootPage](#RebootPage)|Ta strona kreatora służy do powiadamia użytkownika, który przechodzi do ponownego uruchomienia komputera docelowego. Można skonfigurować komunikatu powiadomienia za pomocą projektanta Kreatora instalacji UDI.|  
|[SummaryPage](#RebootPage)|Ta strona kreatora służy do powiadamia użytkownika o opcjach konfiguracji, które zostały wybrane podczas uruchamiania kreatora UDI. Informacje o konfiguracji wyświetlane na tej stronie kreatora automatycznie są zbierane z innych stron kreatora. Niektóre pola na innych stronach kreatora umożliwiają konfigurowanie podpis (etykieta) wyświetlane na tej stronie kreatora, za pomocą projektanta Kreatora instalacji UDI.|  
|[UDAPage](#UDAPage)|Ta strona kreatora służy do konfigurowania UDA między komputerem docelowym a określonego użytkownika. Definiowanie koligację między komputerem i użytkownikiem umożliwia automatyczną instalację oprogramowania, które jest wdrażana dla użytkownika. UDA funkcja jest dostępna tylko w programie Configuration Manager oraz scenariusz UDI nowy komputer.|  
|[UserStatePage](#UserStatePage)|Ta strona kreatora służy do konfigurowania ustawień przechwytywania lub przywracania danych migracji stanu użytkownika. Ta strona kreatora pozwala użytkownikowi na wybranie lokalizacji do migracji stanu użytkownika do przechwytywania lub przywracania danych migracji stanu użytkownika z.|  
|[VolumePage](#VolumePage)|Ta strona kreatora służy do konfigurowania ustawień dla woluminu dysku na komputerze docelowym wdrożonym systemu operacyjnego. Te ustawienia obejmują wybranie docelowego systemu operacyjnego, wybierając dysk docelowy, wszelkie instalacji systemu Windows oraz określanie, czy dysk docelowy powinien być sformatowany jako część procesu wdrażania.|  
|[WelcomePage](#WelcomePage)|Użyj tej strony kreatora o podanie informacji do użytkownika o UDI kreatora i procesu wdrażania. Można skonfigurować komunikatu powiadomienia za pomocą projektanta Kreatora instalacji UDI.|  

#####  <a name="AdminAccounts"></a>AdminAccounts  
 Użyj tej strony kreatora, aby ustawić hasło dla konta administratora lokalnego i dodać innego użytkownika do lokalnej grupy Administratorzy na komputerze docelowym.  

###### <a name="task-sequence-variables"></a>Zmienne sekwencji zadań  
 Wyświetla listę 27 tabeli **AdminAccounts** zmienne sekwencji opis zadań i określa, czy zmienna jest odczytywany przez strony kreatora zapisywane przez kreatora, czy można skonfigurować w pliku konfiguracyjnym UDI kreatora.  

### <a name="table-27-adminaccounts-task-sequence-variables"></a>27 tabeli. Zmienne sekwencji zadań AdminAccounts  

|**Zmienna**|**Odczyt**|**Zapisu**|**Konfiguracji**|  
|-|-|-|-|  
|**OSDAddAdmin**<br /><br /> Określa listę nazw dodatkowych użytkowników, które mają zostać dodane do lokalnej grupy Administratorzy na komputerze docelowym.|Tak|Tak|Tak|  
|**OSDLocalAdminPassword**<br /><br /> Określa hasło dla wbudowanego konta administratora lokalnego na komputerze docelowym.|Tak|Tak|Tak|  

#####  <a name="ApplicationPage"></a>ApplicationPage  
 Ta strona kreatora służy do konfigurowania listę aplikacji, którą można zainstalować podczas instalacji. Te aplikacje mogą zawierać aplikacji lub pakietów i programów z programu Configuration Manager.  

> [!NOTE]
>  Jeśli aplikacje wydają się być wyłączona, aplikacja może wymagać zatwierdzenia przez administratora, ale jeszcze nie została zatwierdzona. Jeśli **Wymagaj zgody administratora, jeśli użytkownicy zażądają tej aplikacji** zaznaczono pole wyboru dla aplikacji, upewnij się, że aplikacja została zatwierdzona. Aby uzyskać więcej informacji, zobacz [jak wdrażać aplikacje w programie Configuration Manager](http://technet.microsoft.com/library/gg682082.aspx).  

###### <a name="task-sequence-variables"></a>Zmienne sekwencji zadań  
 Wyświetla listę tabeli 28 **ApplicationPage** zmienne sekwencji, opis oraz czy zmienna jest odczytywany przez strony kreatora zapisywane przez kreatora, lub można skonfigurować w pliku konfiguracji kreatora UDI zadań.  

### <a name="table-28-applicationpage-task-sequence-variables"></a>28 tabeli. Zmienne sekwencji zadań ApplicationPage  

|**Zmienna**|**Odczyt**|**Zapisu**|**Konfiguracji**|  
|-|-|-|-|  
|**ApplicationBaseVariable**<br /><br /> Określa nazwę używaną jako podstawa dla nazwy zmiennych sekwencji zadań utworzonych dla każdej aplikacji programu Configuration Manager, wybrany na **ApplicationPage** strony kreatora. Ta zmienna jest konfigurowana przy użyciu **edytowanie ustawień oprogramowania** przycisk **edytowanie ustawień** na Wstążce w projektanta Kreatora instalacji UDI.<br /><br /> Zmienną sekwencji zadań oddzielne jest tworzona dla każdej aplikacji wybranej na tej stronie. Wartość domyślna dla tej zmiennej jest **aplikacji**. Tak, na przykład domyślne nazwy zadania sekwencji zmiennych utworzonych dla każdej aplikacji wybranej na tej stronie będą *APPLICATIONS001, APPLICATIONS002, APPLICATIONS003,* itd.|Nie|Tak|Tak|  
|**OSDApplicationList**<br /><br /> Określa listę identyfikatorów aplikacji, które powinny być początkowo zaznaczone. Zmienna zawiera listę wartości liczbowych, oddzielając je średnikami (;).<br /><br /> Identyfikatory aplikacji znajdują się w **identyfikator** atrybutu **aplikacji** elementu w pliku konfiguracyjnym aplikacji Kreatora UDI (UDIWizard_Config.xml.app). Brak oddzielnej **aplikacji** elementu dla każdej aplikacji wyświetlane na tej stronie kreatora.|Tak|Nie|Nie|  
|**OSDArchitecture**<br /><br /> Architektura procesora komputera docelowego. **ApplicationPage** strona kreatora używa tej zmiennej do filtrowania dostępnych aplikacji podczas **VolumeArchitecture** nie została ustawiona zmienna pamięci. Jednak jeśli **VolumeArchitecture** została ustawiona zmienna pamięci, zawsze pierwszeństwo przed ta zmienna sekwencji zadań w celu filtrowania dostępnych aplikacji.<br /><br /> Wartość tej zmiennej można:<br /><br /> -                                      **x86**, co oznacza 32-bitowy procesor<br /><br /> -                                      **AMD64**, co oznacza 64-bitowy procesor|Tak|Nie|Nie|  
|**OSDBaseVariableName**<br /><br /> Określa nazwę używaną jako podstawa dla nazwy zmiennych sekwencji zadań utworzonych dla każdego pakietu programu Configuration Manager i programem na **ApplicationPage** strony kreatora. Ta zmienna jest konfigurowana przy użyciu **edytowanie ustawień oprogramowania** przycisk **zachowanie strony** na Wstążce w projektanta Kreatora instalacji UDI.<br /><br /> Zmienną sekwencji zadań oddzielne jest tworzona dla każdej aplikacji wybranej na tej stronie. Wartość domyślna dla tej zmiennej jest **PAKIETY**. Tak, na przykład domyślne nazwy zadania sekwencji zmiennych utworzonych dla każdej aplikacji wybranej na tej stronie będą *PACKAGES001, PACKAGES002, PACKAGES003,* itd.|Nie|Tak|Tak|  

##### <a name="memory-variables"></a>Zmienne pamięci  
 Wyświetla listę 29 tabeli **ApplicationPage** zmiennych pamięci z opisu i określa, czy zmienna jest odczytywanych lub zapisywanych przez strony kreatora.  

### <a name="table-29-applicationpage-memory-variables"></a>29 tabeli. Zmienne ApplicationPage pamięci  

|**Zmienna**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**VolumeArchitecture**<br /><br /> Architektura procesora obrazu systemu operacyjnego docelowych wdrożenia (czy obraz zawiera 32-bitowy lub 64-bitowego systemu operacyjnego). Gdy ta strona jest wyświetlana, sprawdza, aby zobaczyć, jeśli ta zmienna została zmieniona. Jeśli zmienna została zmieniona od czasu ostatniego wyświetlania strony kreatora, strony kreatora filtruje programów dostępnych do wyboru oparty na architekturze docelowego systemu operacyjnego. Na przykład, jeśli 32-bitowym systemie operacyjnym ma zostać wdrożony, następnie strony kreatora usuwa (filtry) wszystkie aplikacje 64-bitowym z listy dostępnych aplikacji na stronie kreatora.|Tak|Nie|  
|**WizardConfigFilename**<br /><br /> Określa nazwę pliku konfiguracji kreatora UDI aktualnie w użyciu. Jeśli wartość **Link.Uri** metody ustawiającej właściwość jest pusta, **ApplicationPage** strona kreatora odczytuje wartość tej zmiennej można znaleźć odpowiedniego pliku .app, który zawiera listę aplikacji. Na przykład, jeśli nosi nazwę pliku konfiguracji kreatora UDI *pliku config.xml,* , a następnie strony kreatora będzie szukać odpowiedniego pliku .app (config.xml.app). Ta zmienna jest ustawiana po uruchomieniu kreatora UDI.<br /><br /> **Link.Uri** metody ustawiającej właściwość jest ustawiona na **ustawień oprogramowania** okno dialogowe, które można otworzyć za pomocą **edytowanie ustawień oprogramowania** przycisk **strony Zachowanie** na Wstążce w projektanta Kreatora instalacji UDI.|Tak|Nie|  

#####  <a name="BitLockerPage"></a>BitLockerPage  
 Ta strona kreatora służy do konfigurowania ustawień funkcji BitLocker dla komputera docelowego.  

###### <a name="task-sequence-variables"></a>Zmienne sekwencji zadań  
 30 tabela zawiera listę zmiennych sekwencji zadań BitLockerPage opis oraz czy zmienna jest odczytywany przez strony kreatora napisane przez strony kreatora lub w pliku konfiguracji UDI kreatora można skonfigurować.  

### <a name="table-30-bitlockerpage-task-sequence-variables"></a>30 tabeli. Zmienne sekwencji zadań BitLockerPage  

|**Zmienna**|**Odczyt**|**Zapisu**|**Konfiguracji**|  
|-|-|-|-|  
|**BDEInstallSuppress**<br /><br /> Określa, czy instalacja funkcji BitLocker powinno być pomijane. Jeśli zmienna jest ustawiona:<br /><br /> - **TAK**, a następnie **Włącz funkcję BitLocker** pole wyboru jest zaznaczone i instalacja jest przeprowadzana<br /><br /> - **NIE**, a następnie **Włącz funkcję BitLocker** pole wyboru jest wyczyszczone i instalacji nie jest wykonywana.|Tak|Tak|Tak|  
|**BDEKeyLocation**<br /><br /> Określa w pełni kwalifikowana ścieżka do lokalizacji przechowywania kluczy szyfrowania funkcją BitLocker, które mogą być lokalną lub ścieżkę UNC. Ta zmienna ma ustawioną wartość **KeyLocation** wartości metody ustawiającej w pliku konfiguracji kreatora UDI **BitLockerPage**. Ta zmienna jest tylko uważany za ważny kiedy **OSDBitLockerMode** ustawiono **TPMKEY** lub **klucza**.|Nie|Tak|Nie|  
|**BDEPin**<br /><br /> Określa wartość numeru PIN funkcji BitLocker, jeśli **Włącz funkcję BitLocker za pomocą modułu TPM i numer Pin** opcja jest zaznaczona.|Tak|Tak|Tak|  
|**OSDBitLockerCreateRecoveryPassword**<br /><br /> Określa, czy powinny być przechowywane hasła odzyskiwania funkcji BitLocker w usługach AD DS. Jeśli zmienna jest ustawiona:<br /><br /> -                                      **AD**, a następnie **w usłudze Active Directory** opcja jest zaznaczona i klucze odzyskiwania będą przechowywane w usługach AD DS (zalecane)<br /><br /> - **Brak**, a następnie **nie twórz klucza odzyskiwania** opcja jest zaznaczona i nie będą przechowywane klucze odzyskiwania w usługach AD DS (niezalecane)|Nie|Tak|Nie|  
|**OSDBitLockerMode**<br /><br /> Określa tryb, który będzie używany podczas włączania funkcji BitLocker na komputerze docelowym. Prawidłowe wartości to:<br /><br /> -                                      **MODUŁ TPM.** Ta wartość wskazuje, że **Włącz funkcję BitLocker za pomocą modułu TPM tylko** opcja jest zaznaczona, i że tylko modułu TPM będą używane podczas włączania funkcji BitLocker na komputerze docelowym.<br /><br /> -                                      **TPMPIN.** Ta wartość wskazuje, że **Włącz funkcję BitLocker za pomocą modułu TPM i numer Pin** opcja jest zaznaczona i że moduł TPM i numeru PIN użytkownik określił będą używane podczas włączania funkcji BitLocker na komputerze docelowym.<br /><br /> -                                      **TPMKEY.** Ta wartość wskazuje, że **Włącz funkcję BitLocker za pomocą modułu TPM i klucz uruchomienia** opcja jest zaznaczona i że moduł TPM i klucz uruchomienia będą używane podczas włączania funkcji BitLocker na komputerze docelowym.<br /><br /> - **KLUCZ.** Ta wartość wskazuje, że **Włącz funkcję BitLocker za pomocą tylko zewnętrzne klucz uruchomienia** opcja jest zaznaczona i klucz uruchomienia zewnętrznych będą używane podczas włączania funkcji BitLocker na komputerze docelowym.|Nie|Tak|Nie|  
|**OSDBitLockerStartupKeyDrive**<br /><br /> Określa literę dysku, na którym będzie przechowywany klucz zewnętrznych uruchomienia funkcji BitLocker na komputerze docelowym. Ta zmienna jest tylko uważany za ważny kiedy **OSDBitLockerMode** ustawiono **TPMKEY** lub **klucza**.|Nie|Tak|Nie|  
|**OSDBitLockerWaitForEncryption**<br /><br /> Określa, czy sekwencja zadań powinno czekać, aż zakończy szyfrowanie funkcją BitLocker. Jeśli zmienna jest ustawiona:<br /><br /> -                                      **TAK**, a następnie **poczekaj na zakończenie na wszystkich dyskach przed kontynuowaniem szyfrowania BitLocker** pole wyboru jest zaznaczone, a sekwencja zadań będzie czekać, aż do ukończenia instalacji<br /><br /> -                                      **NIE**, a następnie **poczekaj na zakończenie na wszystkich dyskach przed kontynuowaniem szyfrowania BitLocker** pole wyboru jest wyczyszczone i sekwencja zadań nie będzie czekać, aż do ukończenia instalacji|Tak|Tak|Tak|  

###### <a name="configuration-variables"></a>Zmienne konfiguracji  
 Wyświetla listę 31 tabeli **BitLockerPage** zmienne konfiguracji, opis oraz czy zmienna jest odczytywany przez strony kreatora zapisywane przez kreatora, lub można skonfigurować w pliku konfiguracyjnym UDI kreatora.  

### <a name="table-31-bitlockerpage-configuration-variables"></a>Tabela 31. Zmienne konfiguracji BitLockerPage  

|**Zmienna**|**Odczyt**|**Zapisu**|**Konfiguracji**|  
|-|-|-|-|  
|**KeyLocation**<br /><br /> Określa w pełni kwalifikowana ścieżka do lokalizacji przechowywania kluczy szyfrowania funkcją BitLocker, które mogą być lokalną lub ścieżkę UNC. Ta wartość konfiguracji jest używana do ustawienia wartości **BDEKeyLocation** zmiennej sekwencji zadań dla **BitLockerPage**. Ta zmienna jest tylko uważany za ważny kiedy **OSDBitLockerMode** ustawiono **TPMKEY** lub **klucza**.|Tak|Nie|Tak|  

#####  <a name="ComputerPage"></a>ComputerPage  
 Ta strona kreatora służy do konfigurowania nazwę komputera, na komputerze docelowym, domenę lub grupę roboczą do przyłączenia i poświadczenia, które mają być używane w przypadku przyłączania do domeny. Po skonfigurowaniu tej strony, aby przyłączyć komputer docelowy do domeny tej stronie kreatora zostanie przeprowadzona Weryfikacja poświadczenia podane przez użytkownika do dołączenia do domeny w usługach AD DS domyślnie. Następnie ta strona kreatora próbuje zmodyfikować obiekt komputera w usługach AD DS, aby sprawdzić, czy wprowadzone poświadczenia użytkownika na tej stronie mają uprawnienia do tworzenia lub modyfikowania obiektu komputera. Możesz wyłączyć jeden z tych zachowań. Jeśli wyłączysz weryfikację poświadczeń weryfikacji uprawnienia do tworzenia i modyfikowania obiektów komputerów również jest wyłączona. Obie te operacje sprawdzania poprawności wystąpić podczas **dalej** kliknięciu przycisku. Jeśli albo poprawności napotka błąd, zostanie wyświetlony komunikat o błędzie i tej stronie będą nadal wyświetlane.  

 Poniżej przedstawiono kolejność pierwszeństwa, określając domyślna nazwa komputera:  

1.  Jeśli **UserExistingComputerName** ma ustawioną wartość w pliku konfiguracji kreatora UDI **TRUE**, istniejącą nazwę komputera będzie używana \(Jeśli istnieje\).  

2.  Jeśli **OSDComputerName** ustawiono zmienną sekwencji zadań, a następnie nazwę komputera w tej zmiennej jest używany.  

3.  Jeśli określono wartość domyślną dla nazwy komputera w pliku konfiguracyjnym UDI kreatora, ta wartość jest używana.  

###### <a name="task-sequence-variables"></a>Zmienne sekwencji zadań  
 Wyświetla listę 32 tabeli **ComputerPage** zmienne sekwencji, opis oraz czy zmienna jest odczytywany przez strony kreatora zapisywane przez kreatora, lub można skonfigurować w pliku konfiguracji kreatora UDI zadań.  

### <a name="table-32-computerpage-task-sequence-variables"></a>Tabela 32. Zmienne sekwencji zadań ComputerPage  

|**Zmienna**|**Odczyt**|**Zapisu**|**Konfiguracji**|  
|-|-|-|-|  
|**OSDComputerName**<br /><br /> Określa nazwę komputera docelowego. Wartość tej zmiennej jest ustawiana w **nazwy komputera** pole.|Tak|Tak|Tak|  
|**Zmiennej OSDDomainName**<br /><br /> Określa nazwę domeny, do której ma być połączone z komputerem docelowym. Wartość tej zmiennej jest ustawiana w **domeny** pole.|Tak|Tak|Tak|  
|**OSDDomainOUName**<br /><br /> Określa nazwę jednostki Organizacyjnej w domenie, do której ma być przełączony docelowy obiekt komputera. Wartość tej zmiennej jest ustawiana w **jednostki organizacyjnej** pole.|Tak|Tak|Tak|  
|**OSDJoinAccount**<br /><br /> Określa konto użytkownika używane do przyłączenia komputera docelowego do domeny. Wartość tej zmiennej jest ustawiana w **nazwy użytkownika** pole.|Tak|Tak|Tak|  
|**OSDJoinPassword**<br /><br /> Określa hasło dla konta użytkownika używane do przyłączania komputera docelowego do domeny. Wartość tej zmiennej jest ustawiana w **hasło** i **Potwierdź hasło** pola.|Tak|Tak|Tak|  
|**OSDNetworkJoinType**<br /><br /> Określa, czy komputer docelowy ma należeć do grupy roboczej lub domeny. Jeśli wartość jest równa:<br /><br /> \-**0**, a następnie **domeny** opcja jest zaznaczona i komputer docelowy zostanie przyłączony do domeny<br /><br /> \-                                      **1**, a następnie **grupy roboczej** opcja jest zaznaczona i komputer docelowy zostanie przyłączony do grupy roboczej|Nie|Tak|Nie|  
|**SMSTSAssignUsersMode**<br /><br /> Określa tryb Konfigurowanie koligacji użytkownika w programie Configuration Manager. Użyj tej zmiennej można konfigurować zachowanie tworzenia koligację między kontom użytkowników i komputerów docelowych w **SMSTSUdaUsers** zmienną sekwencji zadań. Jeśli ta zmienna nie zostanie określony, przed wyświetleniem tej strony, wartość ta zmienna ma ustawioną **oczekujące**.<br /><br /> Możliwe wartości to zmiennej między innymi:<br /><br /> \-                                      **Automatycznie.** Przetwarzanie koligacji zostało automatycznie zatwierdzone przez program Configuration Manager.<br /><br /> \-**Oczekujące.** Koligacja przetwarzanie reguł wymaga zatwierdzenia przez administratora programu Configuration Manager.<br /><br /> \-                                      **Wyłączone.** Brak koligacji przetwarzania zostanie przeprowadzona.|Nie|Tak|Nie|  

###### <a name="configuration-variables"></a>Zmienne konfiguracji  
 Wyświetla listę 33 tabeli **ComputerPage** zmienne konfiguracji, opis oraz czy zmienna jest odczytywany przez strony kreatora zapisywane przez kreatora, lub można skonfigurować w pliku konfiguracyjnym UDI kreatora.  

### <a name="table-33-computerpage-configuration-variables"></a>Tabela 33. Zmienne konfiguracji ComputerPage  

|**Zmienna**|**Odczyt**|**Zapisu**|**Konfiguracji**|  
|-|-|-|-|  
|**ADComputerObjectCheck**<br /><br /> Określa, czy **ComputerPage** stronie kreatora zostanie Sprawdź, czy podane poświadczenia mają odpowiednie uprawnienia do modyfikowania obiektu komputera w usługach AD DS przed kontynuowaniem do następnej strony kreatora.<br /><br /> Uwaga:<br /><br /> Taka konfiguracja jest ignorowana, jeśli **ADCredentialCheck** ustawiono **FALSE**.<br /><br /> Jeśli wartość jest równa:<br /><br /> \-**TRUE**, programu **Active Directory komputera obiektu Sprawdź** zaznaczono pole wyboru w edytorze strony kreatora w **Join poświadczeń domeny** sekcji w Kreatorze UDI Projektant i uprawnienia do modyfikowania obiekt komputera dla poświadczenia są prawidłowe<br /><br /> \-**FALSE**, a następnie **Active Directory komputera obiektu Sprawdź** pole wyboru jest wyczyszczone w edytorze strony kreatora w **poświadczeń Dołącz do domeny** sekcji w Kreatorze UDI Projektant i uprawnienia do modyfikowania obiekt komputera dla poświadczenia nie są weryfikowane.|Tak|Nie|Tak|  
|**ADCredentialCheck**<br /><br /> Określa, czy **ComputerPage** stronie kreatora zostanie poprawnie zweryfikowany, poświadczenia podane dla przyłączanie do domeny, przed kontynuowaniem do następnej strony kreatora. Jeśli wartość jest równa:<br /><br /> \-                                      **Wartość TRUE,**, następnie przy użyciu **Active Directory poświadczeń Sprawdź** zaznaczono pole wyboru w edytorze strony kreatora w **poświadczeń Dołącz do domeny** części projektanta Kreatora instalacji UDI, i poświadczenia są prawidłowe.<br /><br /> Jeśli to ustawienie konfiguracji **TRUE**, poświadczenia są prawidłowe, nawet jeśli pól poświadczeń są wyłączone, a następnie \(zablokowany\).<br /><br /> \-**FALSE**, a następnie **Active Directory poświadczeń Sprawdź** pole wyboru jest wyczyszczone w edytorze strony kreatora w **poświadczeń Dołącz do domeny** sekcji w Kreatorze UDI Projektant i poświadczenia nie są weryfikowane.<br /><br /> Jeśli to ustawienie konfiguracji **FALSE**, a następnie **ADComputerObjectCheck** ustawienie konfiguracji jest ignorowany i weryfikacji, czy podane poświadczenia można zmodyfikować komputera obiektu w usługach AD DS nie jest wykonywane.|Tak|Nie|Tak|  
|**UseExistingComputerName**<br /><br /> Określa, czy **ComputerPage** strona kreatora użyje istniejącej nazwy komputera na komputerze docelowym jako domyślny dla nazwy komputera.<br /><br /> Uwaga:<br /><br /> To pole wyboru jest tylko istotne dla danego scenariusza wdrażania Odśwież komputer.<br /><br /> Jeśli wartość jest równa:<br /><br /> \-**TRUE**, a następnie **Użyj istniejącej nazwy komputera** zaznaczono pole wyboru w edytorze strony kreatora w **nazwy komputera** części projektanta Kreatora instalacji UDI i istniejące Nazwa komputera będzie używana jako domyślna nazwa komputera dla komputera docelowego po wdrożeniu nowego systemu operacyjnego<br /><br /> \-                                      **FALSE**, a następnie **Użyj istniejącej nazwy komputera** pole wyboru jest wyczyszczone w edytorze strony kreatora w **nazwy komputera** części projektanta Kreatora instalacji UDI i istniejącą nazwę komputera nie będą używane jako domyślne nazwy komputera dla komputera docelowego, po wdrożeniu nowego systemu operacyjnego|Tak|Nie|Tak|  

#####  <a name="ConfigScanPage"></a>ConfigScanPage  
 Ta strona kreatora służy do uruchamiania zadań UDI, skanujące konfiguracji komputera docelowego, aby określić, czy komputer docelowy jest gotowy do wdrożenia obrazu systemu operacyjnego. Ta gotowości zawiera wystarczających zasobów systemowych i wszystkie wstępnie wymagane oprogramowanie jest zainstalowane i właściwie skonfigurowane. Ponadto inne zadania UDI są uruchamiane w tej konfiguracji zbieranie informacje komputera docelowego, np. zidentyfikowanie:  

-   Określa, czy komputer jest podłączony do zasilania \(przeciwieństwie zasilany z baterii\)  

-   Określa, czy komputer jest podłączony do sieci przewodowej połączenia \(zamiast za pomocą połączenia sieci bezprzewodowej\)  

-   Wszystkie zainstalowane aplikacje.  

-   Wszystkie zainstalowane drukarki  

#####  <a name="LanguagePage"></a>LanguagePage  
 Użyj tej strony kreatora, aby określić, które pakiety językowe powinien być zainstalowany, język domyślny dla docelowego systemu operacyjnego, ustawienia regionalne klawiatury i strefy czasowej, w której znajdą się komputera.  

###### <a name="task-sequence-variables"></a>Zmienne sekwencji zadań  
 Wyświetla listę 34 tabeli **LanguagePage** zmienne sekwencji, opis oraz czy zmienna jest odczytywany przez strony kreatora zapisywane przez kreatora, lub można skonfigurować w pliku konfiguracji kreatora UDI zadań.  

### <a name="table-34-languagepage-task-sequence-variables"></a>34 tabeli. Zmienne sekwencji zadań LanguagePage  

|**Zmienna**|**Odczyt**|**Zapisu**|**Konfiguracji**|  
|-|-|-|-|  
|**InputLocale**<br /><br /> Określa ustawienia regionalne docelowego systemu operacyjnego. Ustaw wartość zmiennej w **format godziny i waluty** pole. Jeśli nie jest określony, używana jest ustawień regionalnych skonfigurowanych na obrazie.|Tak|Tak|Tak|  
|**KeyboardLocale**<br /><br /> Określa ustawienia regionalne klawiatury docelowego systemu operacyjnego. Ustaw wartość zmiennej w **układu klawiatury** pole. Jeśli nie zostanie określony, ustawienia regionalne klawiatury skonfigurowany w obrazie jest używany.|Tak|Tak|Tak|  
|**OSDTimeZone**<br /><br /> Określa strefy czasowej, gdy komputer docelowy będzie lokalizacji fizycznej. Ustaw wartość zmiennej w **strefy czasowej** pole. Jeśli nie zostanie określony, strefa czasowa skonfigurowany w obrazie jest używany.|Tak|Tak|Tak|  
|**UILanguage**<br /><br /> Określa domyślny język do użycia dla docelowego systemu operacyjnego. Ustaw wartość zmiennej w **języka Aby zainstalować** pole. Jeśli nie zostanie określony, używany jest język skonfigurowany w obrazie.|Tak|Tak|Tak|  

#####  <a name="ProgressPage"></a>ProgressPage  
 Ta strona kreatora służy do uruchamiania zadań UDI, które przechwytują dane migracji stanu użytkownika z komputera docelowego. Te zadania obejmują:  

-   Kopiowanie pliku odnajdywania aplikacji do lokalizacji wybranej na [UserStatePage](#UserStatePage) strony kreatora  

-   Kopiowanie pliku konfiguracji drukarek do lokalizacji wybranej na [UserStatePage](#UserStatePage) strony kreatora  

-   Kopiowanie listę zainstalowanych produktów w lokalizacji wybranego na [UserStatePage](#UserStatePage) strony kreatora  

-   Uruchamianie narzędzia USMT i zapisywanie użytkownika stanu migracji danych do lokalizacji wybranej na [UserStatePage](#UserStatePage) strony kreatora  

#####  <a name="RebootPage"></a>RebootPage  
 Ta strona kreatora służy do powiadamia użytkownika, który przechodzi do ponownego uruchomienia komputera docelowego. Można skonfigurować komunikatu powiadomienia za pomocą projektanta Kreatora instalacji UDI.  

#####  <a name="SummaryPage"></a>SummaryPage  
 Ta strona kreatora służy do powiadamia użytkownika o opcjach konfiguracji, które zostały wybrane podczas uruchamiania kreatora UDI. Informacje o konfiguracji wyświetlane na tej stronie kreatora automatycznie są zbierane z innych stron kreatora. Niektóre pola na innych stronach kreatora umożliwiają konfigurowanie podpis \(etykiety\) wyświetlane na tej stronie kreatora, za pomocą projektanta Kreatora instalacji UDI.  

#####  <a name="UDAPage"></a>UDAPage  
 Ta strona kreatora służy do konfigurowania UDA między komputerem docelowym a określonego użytkownika. Przypisanie użytkownika jako główny użytkownik komputera umożliwia automatyczną instalację oprogramowania, które zostało wdrożone dla użytkownika. UDA funkcja jest dostępna tylko w programie Configuration Manager i tylko w scenariuszu wdrażania nowego komputera.  

###### <a name="task-sequence-variables"></a>Zmienne sekwencji zadań  
 Wyświetla listę 35 tabeli **UDAPage** zmienne sekwencji, opis oraz czy zmienna jest odczytywany przez strony kreatora zapisywane przez kreatora, lub można skonfigurować w pliku konfiguracji kreatora UDI zadań.  

### <a name="table-35-udapage-task-sequence-variables"></a>35 tabeli. Zmienne sekwencji zadań UDAPage  

|**Zmienna**|**Odczyt**|**Zapisu**|**Konfiguracji**|  
|-|-|-|-|  
|**SMSTSAssignUsersMode**<br /><br /> Określa tryb Konfigurowanie koligacji użytkownika w programie Configuration Manager. Użyj tej zmiennej można konfigurować zachowanie tworzenia koligację między kontom użytkowników i komputerów docelowych w **SMSTSUdaUsers** zmienną sekwencji zadań. Aby ustawić tę zmienną, wybierz **koligacji urządzenia użytkownika użycia** pole wyboru.<br /><br /> Jeśli zmienna jest ustawiona:<br /><br /> \-                                      **Automatycznie**, następnie przetwarzania koligacji jest automatycznie zatwierdzane przez program Configuration Manager<br /><br /> \-**Oczekujące**, koligacji przetwarzanie reguł wymaga zatwierdzenia przez administratora programu Configuration Manager, a następnie \(jest to wartość użyta, gdy **koligacji urządzenia użytkownika użycia** jest pole wyboru wybrany.\)<br /><br /> \-                                      **Wyłączone**, a następnie nastąpi przetwarzanie nie koligacji|Nie|Tak|Nie|  
|**Zmienna SMSTSUdaUsers**<br /><br /> Określa użytkowników ma zostać skojarzony z komputerem docelowym. **Konta koligacji urządzeń użytkownika** ustawia tej zmiennej. Ta zmienna może mieć jednego lub wielu użytkowników określonych i jest w formacie `Domain\User1, Domain\User2`.|Tak|Tak|Tak|  

#####  <a name="UserStatePage"></a>UserStatePage  
 Ta strona kreatora służy do konfigurowania ustawień przechwytywania lub przywracania danych migracji stanu użytkownika. Ta strona kreatora jest używany zarówno w przypadku przechwytywania danych migracji stanu użytkownika, jak i przywracania.  

 **UserStatePage** można przechwytywania lub przywracania danych migracji stanu użytkownika z dysku lokalnego na komputerze docelowym, dysk USB do komputera docelowego lub udostępnionego folderu sieciowego. Ponadto można wybrać nie Przywróć wszelkie dane użytkowników. Kod logiki strony kreatora włącza, wyłącza lub automatycznie wybiera każdego z poniższych opcji opartych na scenariusz wdrażania i czy sformatowany dysk:  

-   **Brak danych do przywrócenia.** Ta opcja oznacza, że nie ma żadnych danych migracji stanu użytkownika do przywracania i zestawów **OSDUserStateMode** zmienną sekwencji zadań i **UserStateMode** zmienną **NoData**.  

-   **Lokalne.** Ta opcja wskazuje, że dane migracji stanu użytkownika powinny być przechowywane na dysku podłączonym lokalnie na komputerze docelowym i ustawia **OSDUserStateMode** zmienną sekwencji zadań i **UserStateMode** zmienną **lokalnego**.  

-   **USB.** Ta opcja oznacza, że na dysku USB lokalnie dołączony do komputera docelowego i zestawy powinny być przechowywane dane migracji stanu użytkownika **OSDUserStateMode** zmienną sekwencji zadań i **UserStateMode** zmienną **USB**.  

-   **Sieć.** Ta opcja wskazuje, że dane migracji stanu użytkownika powinny być przechowywane w folderze udostępniona w sieci i zestawy **OSDUserStateMode** zmienną sekwencji zadań i **UserStateMode** zmienną **Sieci**.  

######  <a name="NEWCOMPUTERStageBehavior"></a>Zachowanie etap NEWCOMPUTER  
 Na etapie NEWCOMPUTER jest używana dla komputerów, na których nie istnieją żadne dane migracji stanu użytkownika. Scenariusz wdrażania nowy komputer może służyć jako drugiej części scenariusza wdrażania Zastąp komputera. Jeśli użytkownik wybierze do:  

-   Sformatuj dysk komputera docelowego, a następnie **UserStatePage** przyjęto założenie, że nie dane migracji stanu użytkownika znajduje się na lokalnym dysku twardym, więc **lokalnego** opcja jest wyłączona, a wszystkie inne opcje są włączone  

-   Formatuj dysk na komputerze docelowym, a następnie **UserStatePage** założono, że istnieje danych migracji stanu użytkownika należy przywrócić i wszystkie opcje są wyłączone innych niż **lokalnego** opcji \(Przy użyciu **lokalnego** opcja zapewnia szybsze metodę przywracania użytkownika stanu migracji danych niż USB lub sieciową folderu udostępnionego metody.\)  

 36 tabeli przedstawiono zachowania opcje na stronie kreatora dla etapu NEWCOMPUTER. **Format** kolumna wskazuje, czy docelowy dysk twardy ma być sformatowany jako część wdrożenia. Innych kolumn wskazać konfiguracji opcji podczas **UserStatePage** jest załadowany.  

### <a name="table-36-behavior-of-options-for-the-newcomputer-stage"></a>36 tabeli. Zachowanie opcje dla etapu NEWCOMPUTER  

|**Format**|**NoData**|**Lokalne**|**USB**|**Sieć**|  
|-|-|-|-|-|  
|Tak|Włączono|Wyłączone|Włączono|Włączono|  
|Nie|Wyłączone|Wybrane|Wyłączone|Wyłączone|  

######  <a name="NewComputerPrestagedStageBehavior"></a>Zachowanie NewComputer.Prestaged etap  
 NEWCOMPUTER. Etap wstępnie przygotowany jest oparta na funkcji wstępnie przygotowanego nośnika w programie Configuration Manager. Ponieważ lokalnego dysku twardego jest nowa, nie ma żadnych danych migracji stanu użytkownika należy przywrócić z lokalnego dysku twardego, więc **lokalnego** opcja jest wyłączona. Wszystkie inne opcje są prawidłowe dla tego scenariusza wdrażania i są włączone. Nie opcji domyślnej jest zaznaczone.  

 37 tabeli przedstawiono zachowania opcje na stronie kreatora dla etapu NewComputer.Prestaged. **Format** kolumna wskazuje, czy docelowy dysk twardy ma być sformatowany jako część wdrożenia. Innych kolumn wskazać konfiguracji opcji podczas **UserStatePage** jest załadowany.  

### <a name="table-37-behavior-of-options-for-the-newcomputerprestaged-stage"></a>37 tabeli. Zachowanie opcje dla etapu NewComputer.Prestaged  

|**Format**|**NoData**|**Lokalne**|**USB**|**Sieć**|  
|-|-|-|-|-|  
|N\/A|Włączono|Wyłączone|Włączono|Włączono|  

######  <a name="REFRESHStageBehavior"></a>ODŚWIEŻ zachowanie etap  
 Na etapie odświeżania jest inicjowana w pełnym systemie operacyjnym Windows, zamiast środowiska Windows PE. Jeśli użytkownik wybierze do:  

-   Sformatuj dysk komputera docelowego, a następnie **UserStatePage** założono, że nie dane migracji stanu użytkownika jest przywrócenie i wszystkie opcje są wyłączone innych niż **NoData** opcji  

-   Formatuj dysk na komputerze docelowym, a następnie **UserStatePage** założono, że istnieje danych migracji stanu użytkownika należy przywrócić i wszystkie opcje są wyłączone innych niż **lokalnego** opcji \(Przy użyciu **lokalnego** opcja zapewnia szybsze metodę przywracania użytkownika stanu migracji danych niż USB lub sieciową folderu udostępnionego metody.\)  

 38 tabeli przedstawiono zachowania opcje na stronie kreatora dla etapu odświeżania. **Format** kolumna wskazuje, czy docelowy dysk twardy ma być sformatowany jako część wdrożenia. Innych kolumn wskazać konfiguracji opcji podczas **UserStatePage** jest załadowany.  

### <a name="table-38-behavior-of-options-for-the-refresh-stage"></a>Tabela 38. Zachowanie opcje dla etapu odświeżania  

|**Format**|**NoData**|**Lokalne**|**USB**|**Sieć**|  
|-|-|-|-|-|  
|Tak|Wybrane|Wyłączone|Wyłączone|Wyłączone|  
|Nie|Wyłączone|Wybrane|Wyłączone|Wyłączone|  

######  <a name="REPLACEWinPEStageBehavior"></a>ZASTĄP. Zachowanie środowiska WinPE, etap  
 ZAMIEŃ. Etap WinPE przechwytuje dane migracji stanu użytkownika z istniejącego \(starego\) komputera, a następnie przywraca dane migracji stanu użytkownika później za pomocą jednego ze scenariuszy wdrażania nowego komputera. Ponieważ we wdrożeniu są związane z dwóch różnych komputerach, dane migracji stanu użytkownika musi zostać zapisany na dysku USB lub do udostępnionego folderu sieciowego. Zapisywanie danych migracji stanu użytkownika na dysk lokalny jest niedostępny.  

 39 tabeli przedstawiono zachowania opcje na stronie kreatora dla ZAMIEŃ. Etap środowiska WinPE. **Format** kolumna wskazuje, czy docelowy dysk twardy ma być sformatowany jako część wdrożenia. Innych kolumn wskazać konfiguracji opcji podczas **UserStatePage** jest załadowany.  

### <a name="table-39-behavior-of-options-for-the-replacewinpe-stage"></a>39 tabeli. Zachowanie opcje dla ZAMIEŃ. Etap środowiska WinPE  

|**Format**|**NoData**|**Lokalne**|**USB**|**Sieć**|  
|-|-|-|-|-|  
|N\/A|Wyłączone|Wyłączone|Włączono|Włączono|  

###### <a name="task-sequence-variables"></a>Zmienne sekwencji zadań  
 Wyświetla listę 40 tabeli **UserStatePage** zmienne sekwencji, opis oraz czy zmienna jest odczytywany przez strony kreatora zapisywane przez kreatora, lub można skonfigurować w pliku konfiguracji kreatora UDI zadań.  

### <a name="table-40-userstatepage-task-sequence-variables"></a>40 tabeli. Zmienne sekwencji zadań UserStatePage  

|**Zmienna**|**Odczyt**|**Zapisu**|**Konfiguracji**|  
|-|-|-|-|  
|**\_SMSTsInWinPE**<br /><br /> Określa, czy Kreator UDI jest uruchomiony w środowisku Windows PE. Jeśli zmienna jest ustawiona:<br /><br /> \-**TRUE**, a następnie Kreator UDI jest uruchomiony w środowisku Windows PE<br /><br /> \-                                      **FALSE**, a następnie kreatora UDI nie działa w środowisku Windows PE, ale w pełną wersją systemu operacyjnego Windows|Tak|Nie|Nie|  
|**OSDDataSourceDirectory**<br /><br /> Określa katalog, w którym są przechowywane dane migracji stanu użytkownika.|Nie|Tak|Nie|  
|**OSDDataSourceDrive**<br /><br /> Określa dysk USB, używana do przechwytywania i przywracania danych migracji stanu użytkownika, które można wybierać **dysku USB docelowego** pole. Jeśli zmienna jest ustawiana przed przedstawiający stronie kreatora zostanie użyta wartość zmiennej jako wartości domyślnej.|Tak|Tak|Nie|  
|**OSDDiskPart**<br /><br /> Określa, czy sformatowany i podzielona na partycje dysku wybranym dla instalacji systemu operacyjnego docelowych. Ta zmienna jest ustawiona na [VolumePage](#VolumePage) strony kreatora i kodu na tej stronie Kreatora używa go do określenia, jakie opcje są zaznaczone i domyślnie włączona. Aby uzyskać więcej informacji, zobacz [UserStatePage](#UserStatePage).|Tak|Nie|Tak|  
|**OSDHardLinks**<br /><br /> Określa dane migracji stanu użytkownika do przechwycenia do czy jest przywracane z dysku lokalnego. Jeśli zmienna jest ustawiona:<br /><br /> \-                                      **Wartość TRUE,**, a następnie **lokalnego** wybrano opcję, a dane migracji stanu użytkownika zostaną przechwycone lub przywrócony z dysku lokalnego, który jest dołączony do komputera docelowego<br /><br /> \-**FALSE**, a następnie **lokalnego** opcja nie została wybrana, a nie danych migracji stanu użytkownika zostaną przechwycone lub przywrócone z dysku lokalnego, który jest dołączony do komputera docelowego|Nie|Tak|Nie|  
|**OSDRestoreData**<br /><br /> Określa, czy dane do przywrócenia. Jeśli zmienna jest ustawiona:<br /><br /> \-                                      **Wartość TRUE,**, a następnie **lokalnego**, **dysku USB docelowego**, lub **sieci** wybrano opcję, a dane migracji stanu użytkownika zostaną przechwycone lub przywrócony z na komputerze docelowym<br /><br /> \-**FALSE**, a następnie **braku danych do przywrócenia** wybrano opcję, a nie danych migracji stanu użytkownika zostaną przechwycone lub przywrócone z komputera docelowego|Nie|Tak|Nie|  
|**OSDUserStateKey**<br /><br /> Określa nazwę użytkownika używane w celu zabezpieczenia danych migracji stanu użytkownika. Nazwa użytkownika jest podawany, jeśli dane migracji stanu użytkownika są przechwytywane. Po przywróceniu danych migracji stanu użytkownika należy podać taką samą nazwę użytkownika i hasło. Ustaw wartość zmiennej w **nazwy użytkownika** pole.|Tak|Tak|Tak|  
|**OSDUserStateKeyPassword**<br /><br /> Określa hasło dla nazwy użytkownika, używany do zabezpieczania danych migracji stanu użytkownika. Ustaw wartość zmiennej w **hasło** i **Potwierdź hasło** pola.|Tak|Tak|Tak|  
|**OSDUserStateMode**<br /><br /> Określa tryb \(metody\) przechwytywanie i przywracanie danych migracji stanu użytkownika. Ta zmienna ma wartość przez wybrane opcje. Jeśli zmienna jest ustawiona:<br /><br /> \-**NoData**, a następnie **braku danych do przywrócenia** wybrano opcję, a nie dane migracji stanu użytkownika zostaną przechwycone lub przywrócić<br /><br /> \-**Lokalnego**, a następnie **lokalnego** wybrano opcję, a dane migracji stanu użytkownika zostaną przechwycone lub przywrócony z lokalnego dysku twardego na komputerze docelowym<br /><br /> \-**Sieci**, a następnie **sieci** wybrano opcję i stanu użytkownika **migracji** danych będzie przechwytywać do lub przywrócony z udostępnionego folderu sieciowego<br /><br /> \-Używana w trybie przechwytywania, opcja ta tworzy folder oparte na skrót nazwę użytkownika i hasło, aby tożsamość danych migracji stanu użytkownika jest chroniona. Dokładnie tej samej nazwy użytkownika i hasła, należy użyć podczas przywracania danych migracji stanu użytkownika, aby strona kreatora dokładnie można znaleźć folderu.<br /><br /> \-**USB**, a następnie **dysku USB docelowego** wybrano opcję, a dane migracji stanu użytkownika będzie przechwytywać do lub przywrócony z dysku USB, która jest fizycznie podłączona do komputera docelowego<br /><br /> \-Zachowanie strony kreatora dla dysków USB wpływa także **Format**, **FormatPrompt**, i **MinimumDriveSize** zmiennych.|Nie|Tak|Nie|  
|**SMSConnectNetworkFolderPath**<br /><br /> Określa sieć folder udostępniony służący do przechwytywania i przywracania danych migracji stanu użytkownika, która jest wybierana z **sieci** pole. **Sieci** w polu są wyświetlane użytkownikowi\-przyjazną nazwę dla sieci udostępnionego folderu, który jest skonfigurowany w **udziałów sieciowych** polu **pola kombi sieci** sekcja w edytorze strony kreatora w projektanta Kreatora instalacji UDI. Jeśli zmienna jest ustawiana przed przedstawiający stronie kreatora zostanie użyta wartość zmiennej jako wartości domyślnej.|Tak|Tak|Tak|  

###### <a name="memory-variables"></a>Zmienne pamięci  
 Wyświetla listę 41 tabeli **UserStatePage** zmienne pamięci, opis i określa, czy zmienna jest odczytywanych lub zapisywanych przez strony kreatora.  

### <a name="table-41-userstatepage-memory-variables"></a>41 tabeli. Zmienne UserStatePage pamięci  

|**Zmienna**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**Litera dysku**<br /><br /> Określa literę dysku dla wybranego dysku USB w **dysku USB docelowego** pola na stronie kreatora. Wartość tej zmiennej zostanie literę dysku, w tym sufiks dwukropka (:), takich jak *M:.*|Nie|Tak|  
|**TargetDrive**<br /><br /> Określa podpis wyświetlany w **dysku USB docelowego** pola na stronie kreatora dotyczące dysku USB wybranego na komputerze docelowym. Wartość tej zmiennej będzie podobny do poniższego przykładu:<br /><br /> `M: VendorA Ultra TD v1.0 USB Device (74.5 GB)`|Nie|Tak|  
|**UserStateMode**<br /><br /> Określa opcje wybrane opcje na stronie kreatora i ma ustawioną taką samą wartość jak **OSDUserStateMode** zmiennej. Prawidłowe wartości dla zmiennej następujące:<br /><br /> -                                      **NoData**, co oznacza, że **braku danych do przywrócenia** wybrano opcję<br /><br /> -                                      **Lokalne**, co oznacza, że **lokalnego** wybrano opcję<br /><br /> -                                      **USB**, co oznacza, że **dysku USB docelowego** wybrano opcję<br /><br /> - **Sieci**, co oznacza, że **sieci** wybrano opcję|Nie|Tak|  

###### <a name="configuration-variables"></a>Zmienne konfiguracji  
 Wyświetla listę 42 tabeli **UserStatePage** zmienne konfiguracji, opis oraz czy zmienna jest odczytywany przez strony kreatora zapisywane przez kreatora, lub można skonfigurować w pliku konfiguracyjnym UDI kreatora.  

### <a name="table-42-userstatepage-configuration-variables"></a>42 tabeli. Zmienne konfiguracji UserStatePage  

|**Zmienna**|**Odczyt**|**Zapisu**|**Konfiguracji**|  
|-|-|-|-|  
|**DataSourceText**<br /><br /> Określa komunikat informacyjny, który powoduje, że użytkownik wykonywania stanu użytkownika przechwytywania lub przywracania o sposobie używania strony kreatora. Ustaw wartość zmiennej w **tekst instrukcji** polu **komunikat** sekcji w Kreatorze stronicowanej edytora w projektanta Kreatora instalacji UDI.|Tak|Nie|Tak|  
|**Format**<br /><br /> Określa, czy dysk USB wybrane do przechwytywania stanu użytkownika na komputerze docelowym powinny być podzielona na partycje i sformatowany przed przechwyceniem danych migracji stanu użytkownika. Ustaw wartość tej zmiennej, wybierając **sformatuj dysk USB przed przechwytywania** pole wyboru w **pola kombi USB** sekcji w Kreatorze stronicowanej edytora w projektanta Kreatora instalacji UDI.<br /><br /> Jeśli zmienna jest ustawiona:<br /><br /> - **Wartość TRUE,**, a następnie dysk jest sformatowany przed przechwyceniem danych migracji stanu użytkownika<br /><br /> -                                      **FALSE**, a następnie dysk nie jest sformatowany przed przechwyceniem danych migracji stanu użytkownika|Tak|Nie|Tak|  
|**FormatPrompt**<br /><br /> Określa, czy użytkownik musi potwierdzić, że dysk USB, używana do przechwytywania danych migracji stanu użytkownika jest formatowania przed wykonaniem przechwytywania. Ustaw wartość tej zmiennej, wybierając **monit przed sformatowaniem dysku docelowego** pole wyboru w **pola kombi USB** sekcji w Kreatorze stronicowanej edytora w projektanta Kreatora instalacji UDI.<br /><br /> Uwaga:<br /><br /> Ta zmienna jest prawidłowy tylko jeśli **OSDUserStateMode** ustawiono zmienną sekwencji zadań **USB**.|Tak|Nie|Tak|  
|**MinimumDriveSize**<br /><br /> Określa minimalną wolnego miejsca na dysku w gigabajtach wymagane dla dysku był dostępny do przechowywania danych migracji stanu użytkownika. Wartość tej zmiennej pełni rolę filtru i ustaw go w **minimalny rozmiar dysku** polu tekstowym **pola kombi USB** sekcji w Kreatorze stronicowanej edytora w projektanta Kreatora instalacji UDI.|Tak|Nie|Tak|  
|**NetworkDrive**<br /><br /> Określa literę dysku, korzystającą z tej strony kreatora w celu mapowania do udostępnionego folderu sieciowego w **SMSConnectNetworkFolderPath** zmienną sekwencji zadań. Mapowanie folderu udostępnionego sieci służy do przechwytywania lub przywracania danych migracji stanu użytkownika. Ustaw wartość zmiennej w **zamapowane na literę dysku** polu **pola kombi sieci** sekcji w Kreatorze stronicowanej edytora w projektanta Kreatora instalacji UDI. Określona litera dysku musi zawierać dwukropka (:) po literę dysku i nie może być używany na komputerze docelowym. Na przykład jeśli komputer docelowy ma dysków C: i D:, następnie C: i D: nie można użyć tej zmiennej.<br /><br /> Uwaga:<br /><br /> Ta zmienna jest prawidłowy tylko jeśli **OSDUserStateMode** ustawiono zmienną sekwencji zadań **sieci**.|Tak|Nie|Tak|  
|**Stan**<br /><br /> Określa, czy strona kreatora jest używana do przechwytywania lub przywracania danych migracji stanu użytkownika. Ustaw wartość zmiennej w **przechwytywania lub przywracania** polu **lokalizacji przechwytywania i przywracania** sekcji w Kreatorze stronicowanej edytora w projektanta Kreatora instalacji UDI. Jeśli zmienna jest ustawiona:<br /><br /> - **Przechwyć**, a następnie strona kreatora służy do przechwytywania danych migracji stanu użytkownika<br /><br /> -                                      **Przywróć**, a następnie strona kreatora służy do przywracania danych migracji stanu użytkownika|Tak|Nie|Tak|  

#####  <a name="VolumePage"></a>VolumePage  
 Ta strona kreatora służy do konfigurowania ustawień dla woluminu dysku na komputerze docelowym, na którym zostanie wdrożony system operacyjny. Te ustawienia obejmują wybranie docelowego systemu operacyjnego, wybierając dysk docelowy, wszelkie instalacji systemu Windows oraz określanie, czy dysk docelowy powinien być sformatowany jako część procesu wdrażania.  

###### <a name="task-sequence-variables"></a>Zmienne sekwencji zadań  
 Wyświetla listę 43 tabeli **VolumePage** zmienne sekwencji, opis oraz czy zmienna jest odczytywany przez strony kreatora zapisywane przez kreatora, lub można skonfigurować w pliku konfiguracji kreatora UDI zadań.  

### <a name="table-43-volumepage-task-sequence-variables"></a>43 tabeli. Zmienne sekwencji zadań VolumePage  

|**Zmienna**|**Odczyt**|**Zapisu**|**Konfiguracji**|  
|-|-|-|-|  
|**OSDDiskPart**<br /><br /> Określa, czy dysk wybrany do wdrożenia docelowego systemu operacyjnego na komputerze docelowym powinny być podzielona na partycje i sformatowany przed przechwyceniem danych migracji stanu użytkownika. Ta zmienna ma wartość przez jeden z poniższych pól wyboru na stronie kreatora:<br /><br /> -                                      **Wyczyść wybranego woluminu.** To pole wyboru jest wyświetlany, gdy Kreator UDI jest uruchomiony w pełnym systemie operacyjnym Windows. Można skonfigurować za pomocą wiadomości tekstowych **FormatFullOS** metody ustawiającej właściwość strony kreatora w pliku konfiguracyjnym UDI kreatora.<br /><br /> -                                      **Partycje i sformatować dysk 0 na partycje.** To pole wyboru jest wyświetlany, gdy Kreator UDI jest uruchomiony w środowisku Windows PE. Można skonfigurować za pomocą wiadomości tekstowych **FormatWinPE** metody ustawiającej właściwość strony kreatora w pliku konfiguracyjnym UDI kreatora.<br /><br /> Kod logiki [UserStatePage](#UserStatePage) strona kreatora używa tej zmiennej do określenia, jakie opcje są zaznaczone i domyślnie włączona.<br /><br /> Jeśli zmienna jest ustawiona:<br /><br /> - **Wartość TRUE,**, a następnie dysk jest podzielona na partycje i sformatowany przed wdrożeniem docelowego systemu operacyjnego<br /><br /> -                                      **FALSE**, a następnie dysk nie jest podzielona na partycje i sformatowany przed wdrożeniem docelowego systemu operacyjnego|Tak|Tak|Tak|  
|**OSDImageIndex**<br /><br /> Określa indeksu liczbowego obrazu systemu operacyjnego w pliku wim, który wybrano w **wybór obrazu** pola kombi. Konfigurowanie listy obrazów systemu operacyjnego w **wybór obrazu** polu **wartości pola kombi obrazu** na liście **pola kombi obrazu** sekcję  **VolumePage** Edytor stron kreatora. Indeks obrazu jest skonfigurowany jako część każdego obrazu w **wartości pola kombi obrazu** listy.|Tak|Tak|Tak|  
|**OSDImageName**<br /><br /> Określa nazwę obrazu systemu operacyjnego w pliku wim, który wybrano w **wybór obrazu** pole. Listy obrazów systemu operacyjnego w **wybór obrazu** pola kombi jest skonfigurowany w **wartości pola kombi obrazu** na liście **pola kombi obrazu** sekcji na **VolumePage** Edytor stron kreatora. Nazwa obrazu jest skonfigurowana jako część każdego obrazu w **wartości pola kombi obrazu** listy.|Nie|Tak|Nie|  
|**OSDTargetDrive**<br /><br /> Określa literę dysku dla woluminu wybranego w **woluminu** pola na stronie kreatora. Wartość tej zmiennej zostanie literę dysku, w tym sufiks dwukropka (:), takich jak *C:.*|Nie|Tak|Nie|  
|**OSDWinPEWindir**<br /><br /> Określa lokalizację istniejącej instalacji systemu Windows na komputerze docelowym. Ustaw wartość zmiennej w **katalogu Windows** pola na stronie kreatora.|Nie|Tak|Nie|  

###### <a name="memory-variables"></a>Zmienne pamięci  
 Wyświetla listę 44 tabeli **VolumePage** zmienne pamięci, opis i określa, czy zmienna jest odczytywanych lub zapisywanych przez strony kreatora.  

### <a name="table-44-volumepage-memory-variables"></a>44 tabeli. Zmienne VolumePage pamięci  

|**Zmienna**|**Odczyt**|**Zapisu**|  
|-|-|-|  
|**VolumeArchitecture**<br /><br /> Architektura procesora systemu operacyjnego do wdrożenia, które wybrano w **wybór obrazu** pole. **VolumeArchitecture** strona kreatora zużywa tej zmiennej do filtrowania architektury aplikacji wyświetlane na tej stronie. Na przykład, jeśli 32-bitowym systemie operacyjnym, które ma zostać wdrożony a następnie **VolumeArchitecture** strona kreatora usuwa (filtry) wszystkie aplikacje 64-bitowym z listy dostępnych aplikacji.<br /><br /> Jeśli zmienna jest ustawiona:<br /><br /> -                                      **x86**, a następnie wybrano 32-bitowym systemie operacyjnym<br /><br /> - **AMD64**, a następnie wybrano 64-bitowym systemie operacyjnym|Nie|Tak|  

#####  <a name="WelcomePage"></a>WelcomePage  
 Użyj tej strony kreatora o podanie informacji do użytkownika o Kreatorze UDI i procesu wdrażania. Można skonfigurować komunikatu powiadomienia za pomocą projektanta Kreatora instalacji UDI.  

### <a name="udi-build-your-own-page-toolbox-control-reference"></a>UDI tworzenie własnych odwołania formantu strony przybornika  
 Funkcja kompilacji swój własny strony w UDI służy do tworzenia kreatora niestandardowych stron, które służy do zbierania informacji o dodatkowe wdrożenia do użycia w UDI. Można utworzyć za pomocą strony kreatora niestandardowego:  

-   **Tworzenie funkcji swój własny strony.** Ta funkcja służy do tworzenia niestandardowych kreatora do zbierania informacji o wdrożeniu bez konieczności pisania kodu lub ma umiejętności programowania. Użyj tej funkcji, jeśli chcesz zbierać podstawowe informacje bez interakcji z użytkownikiem zaawansowane. Na przykład nie można dodać żadnego kodu lub dostosować czcionki interfejsu użytkownika za pomocą tej funkcji.  

-   **UDI SDK i programu Visual Studio**. Użyj tego zestawu SDK, aby tworzyć zaawansowane, w pełni dostosowane kreatora w programie Visual Studio do zbierania informacji o wdrożeniu. Mimo że UDI zestaw SDK umożliwia tworzenie stron kreatora niestandardowych, takich jak dodawanie niestandardowego kodu lub zmiana czcionki, ta metoda wymaga umiejętności programowania.  

     Aby uzyskać więcej informacji na temat używania UDI zestawu SDK do tworzenia kreatora niestandardowych stron, zobacz "Tworzenie niestandardowych UDI stron kreatora" w *przewodnik dla deweloperów instalacji dysku użytkownika*.  

 Funkcja tworzenia swój własny strony obejmuje przybornika formantów, które można dodać do strony kreatora niestandardowego z przybornika kompilacji swój własny strony, która jest wyświetlana podczas przeglądania na stronie kreatora niestandardowego **Konfiguruj** kartę w Kreatorze UDI Projektant.  

 45 tabeli przedstawiono typy formantów do strony kreatora niestandardowego, w której przedstawiono na rysunku 5. Każdy z tych kontrolek jest szczegółowo omówione w dalszej części podrzędnego.  

### <a name="table-45-types-of-controls-in-the-udi-build-your-own-page-toolbox"></a>45 tabeli. Typy formantów w UDI kompilacji Przybornik strony  

|**Typ formantu**|**Opis**|  
|-|-|  
|[CheckBox — formant](#CheckboxControl)|Ten formant umożliwia zaznacz lub usuń zaznaczenie opcji konfiguracji i zachowuje się jak tradycyjnych pole wyboru interfejsu użytkownika.|  
|[ComboBox — formant](#ComboboxControl)|Ten formant służy do wybierania elementu z listy elementów i zachowuje się jak tradycyjnych listy rozwijanej interfejsu użytkownika.|  
|[Formant linii](#LineControl)|Ten formant umożliwia dodawanie linii poziomej do dzielenia jedną część z innej strony kreatora niestandardowego.|  
|[Label — formant](#LabelControl)|Ten formant umożliwia dodanie tekst opisowy, tylko do odczytu do strony kreatora.|  
|[Opcji sterowania](#RadioControl)|Tego formantu można wybrać jedną z opcji konfiguracji z grupy co najmniej dwie opcje.|  
|[Formant mapy bitowej](#BitmapControl)|Ten formant umożliwia dodanie grafiki mapa bitowa (BMP plik) do strony kreatora niestandardowego.|  
|[TextBox — formant](#TextboxControl)|Ten formant pozwala na wprowadzenie tekstu na stronie kreatora niestandardowego.|  

 Możesz dodać dowolną kombinację tych kontrolek do strony kreatora niestandardowego w oparciu o informacje, które mają być zbierane. Ponadto można użyć **Pokaż linie siatki** pole wyboru, aby pokazać lub ukryć linie siatki, który może służyć do celów wizualne projektowanie strony kreatora niestandardowego.  

 Rysunek 5 przedstawiono przykład strony kreatora niestandardowego i przybornika kompilacji swój własny strony.  

 ![UDI — informacje 5](media/UDIReference5.jpg)  

 **Rysunek SEQ Figure \\ \* ARABIC 5. Przykładowa strona kreatora niestandardowego**  

####  <a name="CheckboxControl"></a>CheckBox — formant  
 Ten formant umożliwia zaznacz lub usuń zaznaczenie opcji konfiguracji i zachowuje się jak tradycyjnych pole wyboru interfejsu użytkownika. Ten formant ma odpowiednie etykietę, którą można użyć do opisania celem pole wyboru. Stan tego formantu jest wartość PRAWDA, jeśli pole wyboru jest zaznaczone i wartość False, gdy pole wyboru jest wyczyszczone. Stan pola wyboru są przechowywane w zmiennej sekwencji zadań, które są skonfigurowane dla tego formantu.  

##### <a name="layout-properties"></a>Właściwości układu  
 Właściwości układu służą do skonfigurowania właściwości formantu interfejsu użytkownika i są skonfigurowane na **układu** karcie projektanta Kreatora instalacji UDI. 46 tabela zawiera listę właściwości układu **wyboru** kontroli i zawiera krótki opis każdego właściwości  

### <a name="table-46-checkbox-control-layout-properties"></a>46 tabeli. Właściwości układu CheckBox — formant  

|**Właściwość**|**Opis**|  
|-|-|  
|**X**|Ta właściwość służy do konfigurowania pozycji w poziomie formantu.|  
|**Y**|Ta właściwość służy do konfigurowania pozycji w pionie formantu.|  
|**Etykiety**|Ta właściwość służy do konfigurowania tekst opisu powiązany z polem wyboru.|  
|**Szerokość**|Ta właściwość służy do konfigurowania szerokość formantu.<br /><br /> **Uwaga** Jeśli wprowadzony tekst w **etykiety** właściwość jest dłuższa niż szerokość formantu, tekst jest przycinana i nie są wyświetlane.|  
|**Wysokość**|Ta właściwość służy do konfigurowania wysokość formantu.<br /><br /> **Uwaga** Jeśli wprowadzony tekst w **etykiety** właściwość jest większa niż wysokość formantu, zostanie obcięta.|  

##### <a name="settings-properties"></a>Ustawienia właściwości  
 Ustawienia właściwości są używane do konfigurowania dane początkowo wyświetlane w formancie (wartość domyślna), a gdzie informacje zbierane od użytkownika jest zapisywany. 47 tabela zawiera listę właściwości ustawień **wyboru** kontroli i zawiera krótki opis poszczególnych właściwości.  

### <a name="table-47-checkbox-control-settings-properties"></a>47 tabeli. Właściwości ustawień CheckBox — formant  

|**Właściwość**|**Opis**|  
|-|-|  
|**Wartość domyślna**|Ta właściwość służy do konfigurowania wartość domyślną dla formantu. Pole wyboru, wartością domyślną jest **False**.|  
|**Nazwa zmiennej sekwencji zadań**|Ta właściwość służy do konfigurowania zmiennej sekwencji zadań przechowywania informacji zebranych od użytkownika. Jeśli zmienna sekwencji zadań:<br /><br /> -Nie nie istnieje, utworzeniu zmiennej sekwencji zadań i udostępnia zestaw wartości użytkownika<br /><br /> -Już istnieje, istniejącą wartość zmiennej sekwencji zadań jest zastępowany wartość zawiera użytkownika|  
|**Przyjazną nazwę wyświetlaną widoczne na stronie podsumowania**|Ta właściwość służy do konfigurowania opisową nazwę, która pojawia się na **Podsumowanie** strony kreatora. Ta nazwa jest używana do opisu wartości, który został zapisany w **nazwy zmiennej sekwencji zadań** właściwości dla tego formantu.|  
|**Odblokowany**|Ta właściwość umożliwia skonfigurowanie, czy użytkownik ma możliwość interakcji z formantem. Formant jest domyślnie włączony. Ten przycisk otwiera następujących stanów:<br /><br /> - **Odblokowany.** Formant jest włączony, a użytkownicy mogą wprowadzić za pomocą go.<br /><br /> -                                  **Zablokowany.** Kontrolka jest wyłączona, a użytkownicy będą mogli wprowadź informacje dotyczące korzystania z niego.<br /><br /> **Uwaga** po wyłączeniu formantu (blokowanie), musisz podać informacje kontroli zbierane przez skonfigurowanie właściwości zestawu MDT w CustomSettings.ini lub w bazie danych zestawu MDT. W przeciwnym razie Kreator UDI zostaną zebrane informacje niezbędne i UDI wdrożenie zakończy się niepowodzeniem.|  

####  <a name="ComboboxControl"></a>ComboBox — formant  
 Ten formant służy do wybierania elementu z listy elementów i zachowuje się jak tradycyjnych listy rozwijanej interfejsu użytkownika. Ten formant umożliwia dodawanie i usuwanie elementów z listy i podaj odpowiadającą mu wartość, która zostanie ustawiona w zmiennej sekwencji zadań, które są skonfigurowane dla tego formantu.  

##### <a name="layout-properties"></a>Właściwości układu  
 Właściwości układu służą do skonfigurowania właściwości formantu interfejsu użytkownika i są skonfigurowane na **układu** karcie projektanta Kreatora instalacji UDI. 48 tabela zawiera listę właściwości układu **Combobox** kontroli i zawiera krótki opis poszczególnych właściwości.  

### <a name="table-48-combobox-control-layout-properties"></a>48 tabeli. Właściwości układu formantu ComboBox  

|**Właściwość**|**Opis**|  
|-|-|  
|**X**|Ta właściwość służy do konfigurowania pozycji w poziomie formantu.|  
|**Y**|Ta właściwość służy do konfigurowania pozycji w pionie formantu.|  
|**Szerokość**|Ta właściwość służy do konfigurowania szerokość formantu.<br /><br /> **Uwaga** Jeśli wprowadzony w formancie tekst jest dłuższy niż szerokość formantu, nie jest wyświetlany tekst.|  
|**Wysokość**|Ta właściwość służy do konfigurowania wysokość formantu.<br /><br /> **Uwaga** Jeśli wprowadzony w formancie tekst jest większa niż wysokość formantu, zostanie obcięta.|  
|**Elementy danych**|Ta właściwość służy do konfigurowania listy elementów danych wyświetlanych w formancie. Każdy element danych ma następujące właściwości:<br /><br /> -                                  **Wartość.** Wartość przechowywana w zmiennej sekwencji zadań, po wybraniu elementu danych<br /><br /> -                                  **Się pozycje DisplayValue.** Wartość wyświetlana użytkownikowi w formancie<br /><br /> Można:<br /><br /> -Dodaj elementy danych do listy przy użyciu przycisk niebieski znak plus natychmiast po prawej stronie listy elementów danych<br /><br /> -Usuń elementy danych z listy przy użyciu kolorem czerwonym **X** przycisk natychmiast po prawej stronie listy elementów danych<br /><br /> **Uwaga** element został dodany do listy sekwencji elementu danych na liście nie można zmienić. Upewnij się, wprowadź elementów danych w kolejności, które mają być wyświetlane w formancie.|  

##### <a name="settings-properties"></a>Ustawienia właściwości  
 Ustawienia właściwości są używane do konfigurowania danych, która początkowo jest wyświetlana w formancie (wartość domyślna) i lokalizacji zapisywania informacji zebranych od użytkownika. 49 tabela zawiera listę właściwości ustawień **Combobox** kontroli i zawiera krótki opis poszczególnych właściwości.  

### <a name="table-49-combobox-control-settings-properties"></a>49 tabeli. Właściwości ustawień ComboBox — formant  

|**Właściwość**|**Opis**|  
|-|-|  
|**Nazwa zmiennej sekwencji zadań**|Ta właściwość służy do konfigurowania zmiennej sekwencji zadań przechowywania informacji zebranych od użytkownika. Jeśli zmienna sekwencji zadań:<br /><br /> -Nie nie istnieje, utworzeniu zmiennej sekwencji zadań i udostępnia zestaw wartości użytkownika<br /><br /> -Już istnieje, istniejącą wartość zmiennej sekwencji zadań jest zastępowany wartość zawiera użytkownika|  
|**Przyjazną nazwę wyświetlaną widoczne na stronie podsumowania**|Ta właściwość służy do konfigurowania opisową nazwę, która pojawia się na **Podsumowanie** strony kreatora. Ta nazwa jest używana do opisu wartości, który został zapisany w **nazwy zmiennej sekwencji zadań** właściwości dla tego formantu.|  
|**Odblokowany**|Ta właściwość umożliwia skonfigurowanie, czy użytkownik ma możliwość interakcji z formantem. Formant jest domyślnie włączony. Ten przycisk otwiera następujących stanów:<br /><br /> -                                  **Odblokowany.** Formant jest włączony, a użytkownicy mogą wprowadzić za pomocą go.<br /><br /> - **Zablokowany.** Kontrolka jest wyłączona, a użytkownicy będą mogli wprowadź informacje dotyczące korzystania z niego.<br /><br /> **Uwaga** po wyłączeniu formantu (blokowanie), musisz podać informacje kontroli zbierane przez skonfigurowanie właściwości zestawu MDT w CustomSettings.ini lub w bazie danych zestawu MDT. W przeciwnym razie Kreator UDI zostaną zebrane informacje niezbędne i UDI wdrożenie zakończy się niepowodzeniem.|  

####  <a name="LineControl"></a>Formant linii  
 Ten formant umożliwia dodawanie linii poziomej do dzielenia jedną część z innej strony kreatora niestandardowego. Ten formant nie zbiera żadnych wartości konfiguracji, ale raczej służy do wizualne rozbudowywanie interfejsu użytkownika.  

##### <a name="layout-properties"></a>Właściwości układu  
 Właściwości układu służą do skonfigurowania właściwości formantu interfejsu użytkownika i są skonfigurowane na **układu** karcie projektanta Kreatora instalacji UDI. 50 tabela zawiera listę właściwości układu **wiersza** kontroli i zawiera krótki opis poszczególnych właściwości.  

### <a name="table-50-line-control-layout-properties"></a>50 tabeli. Właściwości układu formant linii  

|**Właściwość**|**Opis**|  
|-|-|  
|**X**|Ta właściwość służy do konfigurowania pozycji w poziomie formantu.|  
|**Y**|Ta właściwość służy do konfigurowania pozycji w pionie formantu.|  
|**Szerokość**|Ta właściwość służy do konfigurowania szerokość formantu.|  
|**Wysokość**|Ta właściwość służy do konfigurowania wysokość formantu.<br /><br /> **Uwaga** zwiększenie tej właściwości nie zwiększa wysokość lub szerokość wiersza.|  

##### <a name="settings-properties"></a>Ustawienia właściwości  
 **Wiersza** formant nie ma ustawienia właściwości.  

####  <a name="LabelControl"></a>Label — formant  
 Ten formant umożliwia dodanie tekst opisowy, tylko do odczytu do strony kreatora. Ten formant nie zbiera żadnych wartości konfiguracji, ale raczej służy do wizualne rozbudowywanie interfejsu użytkownika.  

##### <a name="layout-properties"></a>Właściwości układu  
 Właściwości układu służą do skonfigurowania właściwości formantu interfejsu użytkownika i są skonfigurowane na **układu** karcie projektanta Kreatora instalacji UDI. 51 tabela zawiera listę właściwości układu **etykiety** kontroli i zawiera krótki opis poszczególnych właściwości.  

### <a name="table-51-label-control-layout-properties"></a>51 tabeli. Właściwości układu formantu etykiety  

|**Właściwość**|**Opis**|  
|-|-|  
|**X**|Ta właściwość służy do konfigurowania pozycji w poziomie formantu.|  
|**Y**|Ta właściwość służy do konfigurowania pozycji w pionie formantu.|  
|**Etykiety**|Ta właściwość służy do konfigurowania tekst opisu powiązanego z tym formantem.|  
|**Szerokość**|Ta właściwość służy do konfigurowania szerokość formantu.<br /><br /> **Uwaga** Jeśli wprowadzony tekst w **etykiety** właściwość jest dłuższa niż szerokość formantu, tekst jest przycinana i nie są wyświetlane.|  
|**Wysokość**|Ta właściwość służy do konfigurowania wysokość formantu.<br /><br /> **Uwaga** Jeśli wprowadzony tekst w **etykiety** właściwość jest większa niż wysokość formantu, zostanie obcięta.|  

##### <a name="settings-properties"></a>Ustawienia właściwości  
 **Etykiety** formant nie ma ustawienia właściwości.  

####  <a name="RadioControl"></a>Opcji sterowania  
 Tego formantu można wybrać jedną z opcji z grupy co najmniej dwie opcje. Podobnie jak w przypadku przycisków radiowych tradycyjnych, można grupować dwie lub więcej z tych kontrolek; następnie użytkownik może wybrać jedną z opcji, w grupie.  

 Unikatowa wartość jest przypisany do każdego przycisku radiowego. Wartość przypisana do kontrolkę przycisku radiowego wybrane są zapisywane w zmiennej sekwencji zadań, które są skonfigurowane dla tego formantu.  

##### <a name="layout-properties"></a>Właściwości układu  
 Właściwości układu służą do skonfigurowania właściwości formantu interfejsu użytkownika i są skonfigurowane na **układu** karcie projektanta Kreatora instalacji UDI. 52 tabela zawiera listę właściwości układu **radiowych** kontroli i zawiera krótki opis poszczególnych właściwości.  

### <a name="table-52-radio-control-layout-properties"></a>Tabela 52. Właściwości układu radiowych formantu  

|**Właściwość**|**Opis**|  
|-|-|  
|**X**|Ta właściwość służy do konfigurowania pozycji w poziomie formantu.|  
|**Y**|Ta właściwość służy do konfigurowania pozycji w pionie formantu.|  
|**Etykiety**|Ta właściwość służy do konfigurowania tekst opisu powiązanego z przycisk radiowy.|  
|**Szerokość**|Ta właściwość służy do konfigurowania szerokość formantu.<br /><br /> **Uwaga** Jeśli wprowadzony tekst w **etykiety** właściwość jest dłuższa niż szerokość formantu, tekst jest przycinana i nie są wyświetlane.|  
|**Wysokość**|Ta właściwość służy do konfigurowania wysokość formantu.<br /><br /> **Uwaga** Jeśli wprowadzony tekst w **etykiety** właściwość jest większa niż wysokość formantu, zostanie obcięta.|  
|**RadioGroup**|Ta właściwość do grupy co najmniej dwa przyciski radiowe. Jeśli przycisków radiowych należą do tej samej grupy, można wybrać tylko jeden z przycisków radiowych w obrębie grupy.<br /><br /> Jeśli potrzebujesz wielu grup przycisków radiowych, skonfiguruj tej właściwości dla każdej odpowiedniej grupy przycisków radiowych.|  
|**Wartość**|Ta właściwość służy do konfigurowania wartości przechowywane w zmiennej sekwencji zadań, gdy przycisk radiowy zostanie wybrany.|  

##### <a name="settings-properties"></a>Ustawienia właściwości  
 Ustawienia właściwości są używane do konfigurowania dane początkowo wyświetlane w formancie (wartość domyślna), a gdzie informacje zbierane od użytkownika jest zapisywany. 53 tabela zawiera listę właściwości ustawień **radiowych** kontroli i zawiera krótki opis poszczególnych właściwości.  

### <a name="table-53-radio-control-settings-properties"></a>53 tabeli. Opcji sterowania ustawienia właściwości  

|**Właściwość**|**Opis**|  
|-|-|  
|**Wartość domyślna**|Ta właściwość służy do konfigurowania wartość domyślną dla formantu. Domyślnie wartość jest ustawiona na identyfikator formantu.|  
|**Nazwa zmiennej sekwencji zadań**|Ta właściwość służy do konfigurowania zmiennej sekwencji zadań przechowywania informacji zebranych od użytkownika. Jeśli zmienna sekwencji zadań:<br /><br /> -Nie nie istnieje, utworzeniu zmiennej sekwencji zadań i udostępnia zestaw wartości użytkownika<br /><br /> -Już istnieje, istniejącą wartość zmiennej sekwencji zadań jest zastępowany wartość zawiera użytkownika|  
|**Przyjazną nazwę wyświetlaną widoczne na stronie podsumowania**|Ta właściwość służy do konfigurowania opisową nazwę, która pojawia się na **Podsumowanie** strony kreatora. Ta nazwa jest używana do opisu wartości, który został zapisany w **nazwy zmiennej sekwencji zadań** właściwości dla tego formantu.|  
|**Odblokowany**|Ta właściwość umożliwia skonfigurowanie, czy użytkownik ma możliwość interakcji z formantem. Formant jest domyślnie włączony. Ten przycisk otwiera następujących stanów:<br /><br /> -                                  **Odblokowany.** Formant jest włączony, a użytkownicy mogą wprowadzić za pomocą go.<br /><br /> -                                  **Zablokowany.** Kontrolka jest wyłączona, a użytkownicy będą mogli wprowadź informacje dotyczące korzystania z niego.<br /><br /> **Uwaga** po wyłączeniu formantu (blokowanie), musisz podać informacje kontroli zbierane przez skonfigurowanie właściwości zestawu MDT w CustomSettings.ini lub w bazie danych zestawu MDT. W przeciwnym razie Kreator UDI zostaną zebrane informacje niezbędne i UDI wdrożenie zakończy się niepowodzeniem.|  

####  <a name="BitmapControl"></a>Formant mapy bitowej  
 Ten formant umożliwia dodanie grafiki mapa bitowa (BMP plik) do strony kreatora niestandardowego. Ten formant nie zbiera żadnych wartości konfiguracji, ale raczej służy do wizualne rozbudowywanie interfejsu użytkownika.  

##### <a name="layout-properties"></a>Właściwości układu  
 Właściwości układu służą do skonfigurowania właściwości formantu interfejsu użytkownika i są skonfigurowane na **układu** karcie projektanta Kreatora instalacji UDI. 54 tabela zawiera listę właściwości układu **mapy bitowej** kontroli i zawiera krótki opis poszczególnych właściwości.  

### <a name="table-54-bitmap-control-layout-properties"></a>54 tabeli. Bitmap właściwości układ formantu  

|**Właściwość**|**Opis**|  
|-|-|  
|**X**|Ta właściwość służy do konfigurowania pozycji w poziomie formantu.|  
|**Y**|Ta właściwość służy do konfigurowania pozycji w pionie formantu.|  
|**Szerokość**|Ta właściwość służy do konfigurowania szerokość formantu.<br /><br /> **Uwaga** zaznaczenie grafiki w **źródła** właściwość jest dłuższa niż szerokość formantu, grafiki zostanie obcięta.|  
|**Wysokość**|Ta właściwość służy do konfigurowania wysokość formantu.<br /><br /> **Uwaga** zaznaczenie grafiki w **źródła** właściwość jest większa niż wysokość formantu, grafiki zostanie obcięta.|  
|**Obiekt źródłowy**|Ta właściwość służy do konfigurowania w pełni kwalifikowana ścieżka do pliku bmp, łącznie z nazwą pliku. Ścieżka do pliku .bmp jest względną wobec lokalizacji kreatora UDI (OSDSetupWizard.exe), który jest jednym z następujących folderach (gdzie *mdt_tookit_package* jest lokalizacja pakietu narzędzi zestawu MDT w programie Configuration Manager):<br /><br /> -                                  *mdt_tookit_package*\Tools\x86<br /><br /> -                                  *mdt_tookit_package*\Tools\x64<br /><br /> Aby wyświetlić podczas przeglądania strony kreatora niestandardowego pliku .bmp musi znajdować się w następujących folderach (gdzie *mdt_install_folder* to folder, w którym zainstalowano zestaw MDT):<br /><br /> -                                  *mdt_install_folder*\Template\Distribution\Tools\x86<br /><br /> -                                  *mdt_install_folder* \Template\Distribution\Tools\x64|  

##### <a name="settings-properties"></a>Ustawienia właściwości  
 **Mapy bitowej** formant nie ma ustawienia właściwości.  

####  <a name="TextboxControl"></a>TextBox — formant  
 Ten formant pozwala na wprowadzenie tekstu na stronie kreatora niestandardowego. Tekstu w tym formancie są zapisywane w zmiennej sekwencji zadań, które są skonfigurowane dla tego formantu.  

##### <a name="layout-properties"></a>Właściwości układu  
 Właściwości układu służą do skonfigurowania właściwości formantu interfejsu użytkownika i są skonfigurowane na **układu** karcie projektanta Kreatora instalacji UDI. 55 tabela zawiera listę właściwości układu **pole tekstowe** kontroli i zawiera krótki opis poszczególnych właściwości.  

### <a name="table-55-textbox-control-layout-properties"></a>55 tabeli. Właściwości układu TextBox — formant  

|**Właściwość**|**Opis**|  
|-|-|  
|**X**|Ta właściwość służy do konfigurowania pozycji w poziomie formantu.|  
|**Y**|Ta właściwość służy do konfigurowania pozycji w pionie formantu.|  
|**Szerokość**|Ta właściwość służy do konfigurowania szerokość formantu.<br /><br /> **Uwaga** Jeśli wprowadzony w formancie tekst jest dłuższy niż szerokość formantu, tekst jest przycinana i nie są wyświetlane.|  
|**Wysokość**|Ta właściwość służy do konfigurowania wysokość formantu.<br /><br /> **Uwaga** Jeśli wprowadzony w formancie tekst jest większa niż wysokość formantu, zostanie obcięta.|  

##### <a name="settings-properties"></a>Ustawienia właściwości  
 Ustawienia właściwości są używane do konfigurowania danych, która początkowo jest wyświetlana w formancie (wartość domyślna) i lokalizacji zapisywania informacji zebranych od użytkownika. 56 tabela zawiera listę właściwości ustawień **pole tekstowe** kontroli i zawiera krótki opis każdego właściwości  

### <a name="table-56-textbox-control-settings-properties"></a>56 tabeli. Właściwości ustawień TextBox — formant  

|**Właściwość**|**Opis**|  
|-|-|  
|**Wartość domyślna**|Ta właściwość służy do konfigurowania wartość domyślną dla formantu.|  
|**Nazwa zmiennej sekwencji zadań**|Ta właściwość służy do konfigurowania zmiennej sekwencji zadań przechowywania informacji zebranych od użytkownika. Jeśli zmienna sekwencji zadań:<br /><br /> -Nie nie istnieje, utworzeniu zmiennej sekwencji zadań i udostępnia zestaw wartości użytkownika<br /><br /> -Już istnieje, istniejącą wartość zmiennej sekwencji zadań jest zastępowany wartość zawiera użytkownika|  
|**Przyjazną nazwę wyświetlaną widoczne na stronie podsumowania**|Ta właściwość służy do konfigurowania opisową nazwę, która pojawia się na **Podsumowanie** strony kreatora. Ta nazwa jest używana do opisu wartości, który został zapisany w **nazwy zmiennej sekwencji zadań** właściwości dla tego formantu.|  
|**Lista modułów weryfikacji przypisane do tego formantu**|Ta właściwość zawiera listę modułów weryfikacji używany do sprawdzenia, czy zawartość wprowadzona w polu tekstowym.<br /><br /> Można:<br /><br /> -Dodaj do listy przy użyciu przycisk niebieski znak plus natychmiast po prawej stronie listy modułów sprawdzania poprawności modułów sprawdzania poprawności<br /><br /> -Edytowanie modułów sprawdzania poprawności na liście przy użyciu przycisk ołówka natychmiast po prawej stronie listy modułów sprawdzania poprawności<br /><br /> -Usuń modułów sprawdzania poprawności z listy przy użyciu kolorem czerwonym **X** przycisk natychmiast po prawej stronie listy modułów sprawdzania poprawności|  
|**Odblokowany**|Ta właściwość umożliwia skonfigurowanie, czy użytkownik ma możliwość interakcji z formantem. Formant jest domyślnie włączony. Ten przycisk otwiera następujących stanów:<br /><br /> - **Odblokowany.** Formant jest włączony, a użytkownicy mogą wprowadzić za pomocą go.<br /><br /> -                                  **Zablokowany.** Kontrolka jest wyłączona, a użytkownicy będą mogli wprowadź informacje dotyczące korzystania z niego.<br /><br /> Uwaga:<br /><br /> **Uwaga** po wyłączeniu formantu (blokowanie), musisz podać informacje kontroli zbierane przez skonfigurowanie właściwości zestawu MDT w CustomSettings.ini lub w bazie danych zestawu MDT. W przeciwnym razie Kreator UDI zostaną zebrane informacje niezbędne i UDI wdrożenie zakończy się niepowodzeniem.|  

###  <a name="UDITaskSequenceVariables"></a>Zmienne sekwencji zadań UDI  
 Zmienne sekwencji zadań w tej sekcji są używane tylko w przypadku wdrożeń instalacji sterowanej (UDI). Oprócz tych zmiennych sekwencji zadań następujące zmienne sekwencji zadań ZTI są również używane przez UDI i są udokumentowane w ich odpowiednich sekcjach wcześniej w tym przewodniku:  

-   [KeyboardLocale](#KeyboardLocale)  

-   [OSDComputerName](#OSDComputerName)  

-   [UILanguage](#UILanguage)  

-   [UserLocale](#UserLocale)  

####  <a name="OSDAddAdmin"></a>OSDAddAdmin  
 Ta zmienna sekwencji zadań do określania listy kont oparte na domenie lub kont lokalnych, które mają zostać dodane do lokalnej grupy wbudowanych administratorów na komputerze docelowym.  

|**Wartość**|**Opis**|  
|-|-|
|*domain\account_name1; computer\account_name2*|Format konta, które ma zostać wykonane członkom grupy Administratorzy na komputerze docelowym w formacie *domena\konto* i oddzielone średnikami, gdzie *domeny* może być nazwa aktywnego Domena katalogu lub nazwy komputera docelowego.|  

|**Przykład**|  
|-|  
|`OSDAddAdmin=domain\user01;Win7-01\LocalUser01`|  

####  <a name="OSDApplicationList"></a>OSDApplicationList  
 Ta zmienna sekwencji zadań określa aplikacje, które należy wybrać domyślnie na **Zainstaluj oprogramowanie** strony Kreatora konfiguracji wdrożenia systemu operacyjnego (OSD).  

|**Wartość**|**Opis**|  
|-|-|
|*app_id1; app_id2*|Rozdzielana średnikami lista aplikacji, należy wybrać domyślnie na **Zainstaluj oprogramowanie** strony Kreatora konfiguracji wdrożenia systemu operacyjnego (OSD); każda aplikacja jest reprezentowany przez identyfikator aplikacji i oddzielone średnika. Identyfikator aplikacji jest pochodną **identyfikator** atrybutu każdej aplikacji w pliku UDIWizard_Config.xml. W poniższym fragmencie kodu z pliku UDIWizard_Config.xml, Microsoft Office system 2007 z dodatkiem SP2 aplikacji ma **identyfikator** atrybutu **1**:<br /><br /> `<Application DisplayName="Office 2007 SP2" State="Disabled" Id="1">`|  

|**Przykład**|  
|-|  
|`OSDApplicationList=2;3`|  

####  <a name="OSDArchitecture"></a>OSDArchitecture  
 Ta zmienna sekwencji zadań określa architektury procesora docelowego systemu operacyjnego do wdrożenia.  

|**Wartość**|**Opis**|  
|-|-|
|x86|Docelowy system operacyjny jest 32-bitowym systemie operacyjnym.|  
|AMD64|Docelowy system operacyjny jest 64-bitowym systemie operacyjnym.|  

|**Przykład**|  
|-|  
|`OSDArchitecture=amd64`|  

####  <a name="OSDBitlockerStatus"></a>OSDBitlockerStatus  
 Ta zmienna sekwencji zadań określa, jeśli funkcja BitLocker jest włączona na komputerze docelowym przez funkcję BitLocker kontroli wstępnej.  

|**Wartość**|**Opis**|  
|-|-|
|**CHRONIONE**|Komputer docelowy ma włączoną funkcją BitLocker.|  
|Nie istnieje|Jeśli komputer docelowy nie ma włączonej funkcji BitLocker, zmienną sekwencji zadań nie istnieje.|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="OSDDiskPart"></a>OSDDiskPart  
 Ta zmienna sekwencji zadań określa, czy powinien być sformatowany na partycji docelowej.  

|**Wartość**|**Opis**|  
|-|-|
|**WARTOŚĆ TRUE**|Na partycji docelowej zostaną sformatowane.|  
|**WARTOŚĆ FALSE**|Partycja docelowa dysku nie zostanie sformatowana.|  

|**Przykład**|  
|-|  
|`OSDDiskPart=TRUE`|  

####  <a name="OSDDomainName"></a>Zmiennej OSDDomainName  
 Ta zmienna sekwencji zadań określa nazwę domeny, do której dołączy komputer docelowy, jeśli komputer jest skonfigurowany do należeć do domeny.  

|**Wartość**|**Opis**|  
|-|-|
|*nazwa_domeny*|Nazwa domeny, do której dołączy komputer docelowy. Jeśli skonfigurowano **komputera** strona kreatora w Kreatorze konfiguracji wdrożenia systemu operacyjnego (OSD) jako **dyskretnej**, wartość ta zmienna sekwencji zadań musi odpowiadać wartości określone w UDI Projektant kreatora. W przeciwnym razie pojawi się strona kreatora.<br /><br /> Uwaga:<br /><br /> Ta zmienna sekwencji zadań jest wymagane tylko podczas tworzenia nowego konta komputera w jednostce Organizacyjnej. Jeśli konto komputera już istnieje, ta zmienna nie jest wymagana.|  

|**Przykład**|  
|-|  
|`OSDDomainName=domain01`|  

####  <a name="OSDDomainOUName"></a>OSDDomainOUName  
 Ta zmienna sekwencji zadań określa nazwę jednostki Organizacyjnej w domenie, do której zostanie utworzone konto komputera docelowego, po przyłączeniu komputera do domeny.  

|**Wartość**|**Opis**|  
|-|-|
|*ou_name*|Nazwa jednostki organizacyjnej w domenie, w której zostanie utworzone konto komputera<br /><br /> Uwaga:<br /><br /> Ta zmienna sekwencji zadań jest wymagane tylko podczas tworzenia nowego konta komputera w jednostce Organizacyjnej. Jeśli konto komputera już istnieje, ta zmienna nie jest wymagana.|  

|**Przykład**|  
|-|  
|`OSDDomainOUName=NewDeployOU`|  

####  <a name="OSDImageIndex2"></a>OSDImageIndex  
 Ta zmienna sekwencji zadań określa numer indeksu docelowego systemu operacyjnego w pliku WIM.  

|**Wartość**|**Opis**|  
|-|-|
|*numer_indeksu*|Numer indeksu target, który rozpoczyna się od indeksu liczbę 1 w przypadku pierwszego systemu operacyjnego w pliku WIM|  

|**Przykład**|  
|-|  
|`OSDImageIndex=1`|  

####  <a name="OSDImageName"></a>OSDImageName  
 Ta zmienna sekwencji zadań określa nazwę obrazu systemu operacyjnego w pliku wim, który wybrano w **wybór obrazu** polu na [VolumePage](#VolumePage) strony kreatora. Listy obrazów systemu operacyjnego w **wybór obrazu** pole jest skonfigurowany w **wartości pola kombi obrazu** na liście **pola kombi obrazu** sekcję [ VolumePage](#VolumePage) Edytor stron kreatora. Nazwa obrazu jest skonfigurowana jako część każdego obrazu w **wartości pola kombi obrazu** listy.  

> [!NOTE]
>  **Uwaga** ustawiono tę zmienną sekwencji zadań [VolumePage](#VolumePage) kreatora i nie powinno być skonfigurowane w pliku CustomSettings.ini lub w bazie danych zestawu MDT. Jednak ta zmienna sekwencji zadań można ustawić warunki dotyczące kroków sekwencji zadań, zgodnie z opisem w sekcji "Konfigurowanie UDI zadań sekwencji do wdrażania systemów operacyjnych", w dokumentacji zestawu MDT *przy użyciu Microsoft Deployment Zestaw narzędzi*.  

|**Wartość**|**Opis**|  
|-|-|
|*nazwa_obrazu*|Nazwa obrazu systemu operacyjnego w pliku wim, który wybrano w **wybór obrazu** polu na [VolumePage](#VolumePage) strony kreatora|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="OSDJoinAccount"></a>OSDJoinAccount  
 Ta zmienna sekwencji zadań określa oparte na domenie konto używane do przyłączenia komputera docelowego do domeny określonej w **zmiennej OSDDomainName** zmienną sekwencji zadań. Ta zmienna sekwencji zadań jest konieczne, jeśli komputer docelowy zostanie przyłączony do domeny.  

|**Wartość**|**Opis**|  
|-|-|
|*nazwa_konta*|Nazwa konta używanego do przyłączenia komputera docelowego do domeny w formacie *domena\konto*|  

|**Przykład**|  
|-|  
|`OSDJoinAccount=domain\admin01`|  

####  <a name="OSDJoinPassword"></a>OSDJoinPassword  
 Ta zmienna sekwencji zadań określa hasło dla opartych na domenie konto używane do przyłączenia komputera docelowego do domeny określonej w **OSDJoinAccount** zmienną sekwencji zadań. Ta zmienna sekwencji zadań jest konieczne, jeśli komputer docelowy zostanie przyłączony do domeny.  

|**Wartość**|**Opis**|  
|-|-|
|*hasło*|Hasło konta używanego do przyłączania do domeny|  

|**Przykład**|  
|-|  
|`OSDJoinPassword=P@ssw0rd10`|  

####  <a name="OSDLocalAdminPassword"></a>OSDLocalAdminPassword  
 Ta zmienna sekwencji zadań określa hasło dla wbudowanego konta lokalnego administratora na komputerze docelowym.  

|**Wartość**|**Opis**|  
|-|-|
|*hasło*|Hasło administratora lokalnego wbudowane konto na komputerze docelowym|  

|**Przykład**|  
|-|  
|`OSDLocalAdminPassword=P@ssw0rd10`|  

####  <a name="OSDNetworkJoinType"></a>OSDNetworkJoinType  
 Ta zmienna sekwencji zadań określa, czy komputer docelowy łączy domeny lub grupy roboczej.  

|**Wartość**|**Opis**|  
|-|-|
|**0**|Komputer docelowy zostanie dołączyć do domeny.<br /><br /> Jeśli tę opcję i skonfiguruj odpowiednie strony Kreatora konfiguracji wdrożenia systemu operacyjnego (OSD) być **dyskretnej**, należy również podać wartości **OSDJoinAccount**,  **OSDJoinPassword**, **zmiennej OSDDomainName**, i **OSDDomainOUName** odpowiednio się zmienne sekwencji zadań. Ponadto należy wybrać **domeny** w **domyślny wybór** w okienku obszaru roboczego na **strony komputera** w projektanta Kreatora instalacji UDI.|  
|**1**|Komputer docelowy zostanie Przyłącz do grupy roboczej.<br /><br /> Jeśli tę opcję i skonfiguruj odpowiednie strony Kreatora konfiguracji wdrożenia systemu operacyjnego (OSD) być **dyskretnej**, musisz także podać wartość dla **OSDWorkgroupName** sekwencji zadań Zmienna. Ponadto należy wybrać **grupy roboczej** w **domyślny wybór** w okienku obszaru roboczego na **strony komputera** w projektanta Kreatora instalacji UDI.|  

|**Przykład**|  
|-|  
|`OSDNetworkJoinType=0`|  

####  <a name="OSDSetupWizCancelled"></a>OSDSetupWizCancelled  
 Ta zmienna sekwencji zadań określa, czy użytkownik anulował Kreatora konfiguracji wdrożenia systemu operacyjnego (OSD).  

|**Wartość**|**Opis**|  
|-|-|
|**WARTOŚĆ TRUE**|Użytkownik anulował Kreatora konfiguracji wdrożenia systemu operacyjnego (OSD).|  
|Nie istnieje|Jeśli Kreator nie zostanie anulowana, zmienną sekwencji zadań nie istnieje.|  

|**Przykład**|  
|-|  
|Brak|  

####  <a name="OSDTargetDrive"></a>OSDTargetDrive  
 Ta zmienna sekwencji zadań Określa wolumin dysku, na którym zostanie wdrożony docelowego systemu operacyjnego.  

|**Wartość**|**Opis**|  
|-|-|
|*disk_volume*|Nazwa woluminu dysku|  

|**Przykład**|  
|-|  
|`OSDTargetDrive=C:`|  

####  <a name="OSDWinPEWinDir"></a>OSDWinPEWinDir  
 Ta zmienna sekwencji zadań określa folder, w którym system operacyjny Windows jest obecnie zainstalowany na komputerze docelowym.  

|**Wartość**|**Opis**|  
|-|-|
|*windows_directory*|Katalog, w którym jest obecnie zainstalowany system operacyjny Windows|  

|**Przykład**|  
|-|  
|`OSDWinPEWinDir=C:\Windows`|  

####  <a name="OSDWorkgroupName"></a>OSDWorkgroupName  
 Ta zmienna sekwencji zadań określa nazwę grupy roboczej, do której dołączy komputer docelowy, jeśli komputer jest skonfigurowany jako członek grupy roboczej.  

|**Wartość**|**Opis**|  
|-|-|
|*Nazwa_grupy_roboczej*|Nazwa grupy roboczej, do której dołączy komputer docelowy|  

|**Przykład**|  
|-|  
|`OSDWorkgroupName=WORKGROUP01`|  

###  <a name="OSDResultsexeconfigFileElementValues"></a>Wartości elementów OSDResults.exe.config pliku  
 Program OSD wyników, OSDResults.exe, jest uruchamiany po zakończeniu wdrażania UDI i wyświetla wyniki procesu wdrażania. Zachowanie programu OSD wyników można dostosować przez zmodyfikowanie wartości elementu OSDResults.exe.config w pliku. Plik OSDResults.exe.config jest przechowywany w Tools\OSDResults w pakiecie zestawu MDT w sekwencji zadań instalacji dysków w użytkownika.  

####  <a name="backgroundOpacity"></a>backgroundOpacity  
 Ten element XML konfiguruje opaqueness tapety obrazu tła określony jako wartość procentowa sformatowany dziesiętnych w **backgroundWallpaper** elementu.  

|**Wartość**|**Opis**|  
|-|-|
|*opacity_percent*|Procent opaqueness z **backgroundWallpaper** wyrażony w procentach dziesiętną sformatowany element — na przykład wartość **0,8** wyznacza opaqueness 80%.|  

|**Przykład**|  
|-|  
|`<add key="backgroundOpacity" value="0.8"/>`|  

####  <a name="backgroundWallpaper"></a>backgroundWallpaper  
 Ten element XML zawiera nazwę pliku i ścieżkę względną do obrazu, który jest wyświetlany jako tło w **wyniki OSD** okno dialogowe. Ścieżka jest względne wobec folderu Tools\OSDResults w pakiecie zestawu MDT.  

|**Wartość**|**Opis**|  
|-|-|
|*ścieżka\\\file_name*|Zawiera ścieżkę względną i nazwę pliku obrazu tła. Ścieżka jest rozdzielane ukośnikami double (/ /).|  

|**Przykład**|  
|-|  
|`<add key="backgroundWallpaper" value="images\\Wallpaper.jpg"/>`|  

####  <a name="completedText"></a>completedText  
 Ten element XML zawiera tekst, który jest wyświetlany w **wyniki OSD** okno dialogowe po zakończeniu wdrożenia.  

|**Wartość**|**Opis**|  
|-|-|
|*tekst*|Tekst, który ma być wyświetlany w **wyniki OSD** okno dialogowe w ofercie oznacza po zakończeniu wdrożenia|  

|**Przykład**|  
|-|  
|`<add key="completedText" value="Deployment Complete"/>`|  

####  <a name="headerImagePath"></a>headerImagePath  
 Ten element XML zawiera nazwę pliku i ścieżkę względną do obrazu, który jest wyświetlany w nagłówku **wyniki OSD** okno dialogowe. Ścieżka jest względne wobec folderu Tools\OSDResults w pakiecie zestawu MDT.  

|**Wartość**|**Opis**|  
|-|-|
|*ścieżka\\\file_name*|Zawiera ścieżkę względną i nazwę pliku obrazu nagłówka. Ścieżka rozdzielana ułamkowe odwrócone (\\\\).|  

|**Przykład**|  
|-|  
|`<add key="headerImagePath" value="images\\Windows7_h_rgb.png"/>`|  

####  <a name="timeoutMinutes"></a>timeoutMinutes  
 Ten element XML określa, ile minut **wynik OSD** zostanie wyświetlone okno dialogowe, zanim okno dialogowe jest automatycznie zamknięta i ponownym uruchomieniu komputera.  

|**Wartość**|**Opis**|  
|-|-|
|*Wartości inne niż alfanumeryczne*|Otwiera pozostaje okno dialogowe do **Start systemu Windows** zostanie kliknięty.|  
|*Wartość ujemna*|Otwiera pozostaje okno dialogowe do **Start systemu Windows** zostanie kliknięty.|  
|**0**|Otwiera pozostaje okno dialogowe do **Start systemu Windows** zostanie kliknięty.|  
|Obejmują dziesiętnego|Otwiera pozostaje okno dialogowe do **Start systemu Windows** zostanie kliknięty.|  
|**1 - 10080.**|Liczba minut, przez które wyświetli się okno dialogowe, z minimalną wartość 1 minutę i maksymalną wartość 10080 minut (1 tydzień).|  

|**Przykład**|  
|-|  
|`<add key="timeoutMinutes" value="30"/>`|  

####  <a name="welcomeText"></a>welcomeText  
 Ten element XML zawiera powitalnej tekst, który jest wyświetlany w **wyniki OSD** okno dialogowe.  

|**Wartość**|**Opis**|  
|-|-|
|*welcome_text*|Zapraszamy tekst do wyświetlenia w **wyniki OSD** okno dialogowe w cudzysłowie|  

|**Przykład**|  
|-|  
|`<add key="welcomeText" value="Congratulations, Windows 7 has been successfully deployed to your computer."/>`|
