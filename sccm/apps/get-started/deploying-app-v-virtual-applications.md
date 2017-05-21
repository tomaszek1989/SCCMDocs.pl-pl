---
title: "Wdrożenie aplikacji wirtualnych App-V | Dokumentacja firmy Microsoft"
description: "Zobacz uwagi, które należy wziąć pod uwagę podczas tworzenia i wdrażania aplikacji wirtualnych."
ms.custom: na
ms.date: 02/16/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ddcad9f2-a542-4079-83ca-007d7cb44995
caps.latest.revision: 11
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: c73373e6f2f28f8ddc197695e4b4e3488c9c1f5b
ms.openlocfilehash: 0808edbb9a0433dd658d37e8d005c89a4778735c
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="deploy-app-v-virtual-applications-with-system-center-configuration-manager"></a>Wdrożenie aplikacji wirtualnych App-V z System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Korzystając z programu Configuration Manager do zarządzania aplikacjami wirtualnymi, można zyskać następujące korzyści:  

-   Pojedynczej infrastruktury zarządzania  

-   Funkcje skalowalności, wdrażania i dystrybucji zawartości, takich jak kolekcje i koligacja urządzenia użytkownika  

-   Zaawansowanych funkcji zarządzania aplikacjami  

-   Wdrożenie systemu operacyjnego, spis sprzętu i oprogramowania, zliczania oprogramowania i analiza zasobów w celu obsługi aplikacji wirtualnych  

Aby uzyskać więcej informacji o sposobie tworzenia i sekwencjonowania aplikacji za pomocą Microsoft Application Virtualization (App-V), zobacz [Application Virtualization](https://technet.microsoft.com/library/cc843848.aspx) w bibliotece TechNet.  

Podczas tworzenia i wdrażania aplikacji wirtualnych oprócz inne wymagania programu System Center Configuration Manager i procedury dotyczące tworzenia aplikacji, należy wykonać pod uwagę następujące kwestie:

-   Aby wdrożyć aplikacje wirtualne na komputerach, musi mieć klienta programu Configuration Manager i zainstalowane na komputerach klienta App-V. Urządzeniami klienckimi mogą być komputery stacjonarne i przenośne oraz klienci infrastruktury pulpitu wirtualnego (VDI). Oprogramowania Configuration Manager i App-V Client współpracują w celu dostarczenia, lokalizując i uruchamiając pakiety aplikacji wirtualnych. Klient programu Configuration Manager zarządza dostarczaniem pakietów aplikacji wirtualnej do klienta App-V. Klient App-V Client uruchamia aplikację wirtualną na kliencie.  

-   Aby wdrożyć aplikację wirtualną, należy najpierw ją utworzyć przy użyciu sekwensera App-V Application Virtualization Sequencer. Sekwenser monitoruje proces instalacji i konfiguracji aplikacji oraz rejestruje informacje niezbędne do uruchomienia aplikacji w środowisku wirtualnym. Można również użyć go do ustawienia, które pliki i konfiguracje mają zastosowanie do wszystkich użytkowników oraz które konfiguracje mogą być dostosowywane.  

-   Podczas sekwencjonowania aplikacji należy zapisać pakiet miejsce, do którego można uzyskać dostęp do programu Configuration Manager. Następnie można utworzyć wdrożenie aplikacji zawierające tę aplikację wirtualną.  

-   Menedżer konfiguracji nie obsługuje korzystanie z funkcji udostępnione tylko do odczytu pamięci podręcznej programu App-V.  

-   Program Configuration Manager obsługuje funkcję magazynu zawartości udostępnione w App-V 5.  

-   Podczas tworzenia typu wdrożenia dla aplikacji wirtualnych programu Configuration Manager utworzy typ wdrożenia przy użyciu zawartości pliku manifestu aplikacji. Jest to plik XML, który zawiera informacje dotyczące aplikacji wirtualnej. Ponadto program Configuration Manager tworzy wymagań dotyczących typu wdrożenia na podstawie zawartości pliku .osd programu App-V, zawierający informacje o obsługiwanych systemach operacyjnych dla aplikacji wirtualnej.  

-   Aby wdrożyć aplikacje wirtualne w programie Configuration Manager, komputerów klienckich musi mieć co najmniej App-V 4.6 SP1 lub nowszy zainstalowany klient.  

-   Przed wdrożeniem aplikacji wirtualnych, należy zaktualizować klienta App-V poprawką opisaną w artykule bazy wiedzy [2645225](https://support.microsoft.com/kb/2645225).  

-   Użyciu grup połączeń w programie App-V 5.0 wdrożone aplikacje wirtualne mogą współużytkować ten sam system plików i rejestru na komputerach klienckich. W przeciwieństwie do standardowych aplikacji wirtualnych te aplikacje mogą udostępniać wzajemnie dane. Funkcja grup połączeń umożliwia również zachowanie ustawień użytkownika w odniesieniu do zawartych w nich aplikacji. Środowiska wirtualne App-V w programie Configuration Manager są używane do definiowania grup połączeń na komputerach klienckich. Środowiska wirtualne są tworzone i zmieniane na komputerach klienckich w momencie instalowania aplikacji oraz gdy następny klient oceni zainstalowane aplikacje. Aplikacjom można przypisać priorytety. Gdy wiele aplikacji próbuje zmienić system plików lub wartość rejestru, pierwszeństwo ma aplikacja o najwyższym priorytecie. Aby uzyskać więcej informacji, zobacz [środowisk wirtualnych App-V Utwórz](../../apps/deploy-use/create-app-v-virtual-environments.md).  

##  <a name="supported-app-v-versions"></a>Obsługiwane wersje programu App-V  
 Program Configuration Manager obsługuje następujące wersje programu App-V:  

-   **App-V 4.6**: Używanie aplikacji wirtualnych w programie Configuration Manager, komputery klienckie muszą mieć zainstalowanego klienta App-V 4.6 z dodatkiem SP1, App-V 4.6 z dodatkiem SP2 lub App-V 4.6 z dodatkiem SP3.  

     Przed wdrożeniem aplikacji wirtualnych, należy również zaktualizować klienta App-V 4.6 z dodatkiem SP1, instalując poprawkę opisaną w artykule bazy wiedzy [2645225](http://go.microsoft.com/fwlink/p/?LinkId=237322).  

-   **App-V 5, App-V 5.0 z dodatkiem SP1, App-V 5.0 z dodatkiem SP2, App-V 5.0 z dodatkiem SP3 i App-V 5.1**: App-V 5.0 z dodatkiem SP2 należy zainstalować [5 pakietu poprawki](https://support.microsoft.com/en-us/kb/2963211) lub za pomocą programu App-V 5.0 z dodatkiem SP3.  
-   **App-V 5.2**: To jest wbudowana w system Windows 10 Enterprise (aktualizacji rozliczenia i nowszych).

Aby uzyskać więcej informacji na temat App-V w systemie Windows 10 zobacz następujące tematy:

- [Nowości w programie App-V](https://technet.microsoft.com/itpro/windows/manage/appv-about-appv)
- [Wprowadzenie do programu App-V for Windows 10](https://technet.microsoft.com/itpro/windows/manage/appv-getting-started)
- [Uaktualnianie do programu App-V w systemie Windows 10 z istniejącej instalacji](https://technet.microsoft.com/itpro/windows/manage/appv-upgrading-to-app-v-for-windows-10-from-an-existing-installation)

##  <a name="steps-to-manage-app-v-virtual-applications"></a>Kroki, aby zarządzać aplikacjami wirtualnymi App-V  
 Aby zarządzać aplikacjami wirtualnymi App-V, wykonaj następujące kroki:  

1.   **Sekwencja**: Sekwencjonowanie to proces konwertowania aplikacji na aplikację wirtualną za pomocą programu App-V sequencer.

2.   **Utwórz**: Umożliwia Kreatora tworzenia typów wdrożeń zaimportuj sekwencjonowaną aplikację do typu wdrożenia programu Configuration Manager, który można następnie dodać do aplikacji. Istnieje także możliwość dodania środowisk wirtualnych umożliwiających współużytkowanie ustawień przez wiele aplikacji wirtualnych.

3.   **Dystrybucja**: Dystrybucja to proces udostępniania aplikacji App-V w punktach dystrybucji programu Configuration Manager.

4.   **Wdrażanie**: Wdrażanie to proces udostępniania aplikacji na komputerach klienckich. Jest to nazywane przesyłania strumieniowego w pełnej infrastrukturze App-V.  

##  <a name="configuration-manager-virtual-application-delivery-methods"></a>Metody dostarczania aplikacji wirtualnych programu Configuration Manager  
Program Configuration Manager obsługuje dwie metody dostarczania klientom aplikacji wirtualnych: strumieniowanie i dostarczanie lokalne (Pobieranie i uruchamianie).

W przypadku podejmując metody dostarczenia Porównaj zmniejszenie wymaganego miejsca na dysku dla dostarczania strumieniowego z gwarantowaną dostępnością aplikacji App-V w dostarczania lokalnego. Zwiększenie ilości miejsca na dysku klienta wymagane w przypadku dostarczania lokalnego może być korzystniejsze od dostarczania strumieniowego, ponieważ użytkownicy będą mieli wtedy dostęp do aplikacji w każdej lokalizacji.  

###  <a name="streaming-delivery"></a>Dostarczanie przez strumieniowanie
Korzystając z programu Configuration Manager do zarządzania klientem programu App-V, obsługuje przesyłania strumieniowego aplikacji wirtualnych za pośrednictwem protokołu HTTP lub HTTPS z punktu dystrybucji. Strumieniowanie za pośrednictwem protokołu HTTP lub HTTPS jest włączone domyślnie i konfiguruje się w oknie dialogowym Właściwości punktu dystrybucji. Podczas wdrażania aplikacji wirtualnej na komputery klienckie użytkownik uruchomi aplikację wirtualną, kontaktuje się z punktem zarządzania w celu określenia punktu dystrybucji, który umożliwia klienta programu Configuration Manager. Następnie aplikacja jest strumieniowana z punktu dystrybucji.  

Użyj informacje w poniższej tabeli pomogą określić, czy dostarczania strumieniowego jest najlepszą metodę dostarczania dla Ciebie:

|Zalety|Wady|  
|----------------|-------------------|  
|W ramach tej metody do strumieniowania zawartości pakietu z punktów dystrybucyjnych są używane standardowe protokoły sieciowe.<br /><br /> Skróty programów dla aplikacji wirtualnych wywołują połączenie z punktem dystrybucji, dzięki czemu aplikacja wirtualna jest dostarczana na żądanie.<br /><br /> Ta metoda jest najlepsza w przypadku klientów mających szerokopasmowe połączenie z punktami dystrybucji.<br /><br /> Zaktualizowane aplikacje wirtualne dystrybuowane w całym przedsiębiorstwie stają się dostępne, kiedy klienci otrzymują zasady informujące o zastąpieniu bieżącej wersji i pobierają tylko zmiany względem poprzedniej.<br /><br /> Uprawnienia dostępu są definiowane w punkcie dystrybucji w celu uniemożliwienia użytkownikom dostępu aplikacji lub pakietów, do których nie ma ją uprawnień.|Aplikacje wirtualne są strumieniowane dopiero po pierwszym uruchomieniu. W takim scenariuszu użytkownik może otrzymać skróty programu dla aplikacji wirtualnych i odłączyć się od sieci przed ich pierwszym uruchomieniem. Jeśli użytkownik spróbuje uruchomić aplikację wirtualną, gdy klient jest w trybie offline, użytkownik zobaczy następujący błąd i nie można uruchomić zwirtualizowanej aplikacji, ponieważ punkt dystrybucji programu Configuration Manager nie jest dostępne do przesyłania strumieniowego aplikacji. Aplikacja będzie niedostępna, dopóki użytkownik nie nawiąże połączenia z siecią i nie uruchomi aplikacji.<br /><br /> Aby tego uniknąć, można dostarczyć aplikację wirtualną klientom za pomocą metody lokalnego dostarczania, a także można włączyć internetowe zarządzanie klientami na potrzeby dostarczania strumieniowego.|  

###  <a name="local-delivery-download-and-execute"></a>Dostarczanie lokalne (Pobieranie i uruchamianie)  
Korzystając z metody lokalnego dostarczania, klient programu Configuration Manager najpierw pobiera cały pakiet aplikacji wirtualnej do pamięci podręcznej klienta programu Configuration Manager. Następnie instruuje klienta App-V do przesyłania strumieniowego aplikacji z pamięci podręcznej programu Configuration Manager do pamięci podręcznej programu App-V, programu Configuration Manager. Wdrażania aplikacji wirtualnej na komputerach klienckich, gdy jej zawartość nie będzie w pamięci podręcznej programu App-V, App-V Client najpierw prześle strumieniowo zawartość aplikacji z pamięci podręcznej klienta programu Configuration Manager do pamięci podręcznej programu App-V, a następnie uruchomi aplikację. Po udanym uruchomieniu aplikacji, można ustawić klienta programu Configuration Manager, aby usuwał starsze wersje pakietu w kolejnych cyklach usuwania lub zachowywał je w pamięci podręcznej klienta programu Configuration Manager.  

Użyj informacje w poniższej tabeli pomogą określić, czy dostarczania lokalnego jest najlepszą metodę dostarczania dla Ciebie:   

|Zalety|Wady|  
|----------------|-------------------|  
|Standardowe funkcje punktu dystrybucji służą do pobrania pakietu za pośrednictwem usługi inteligentnego transferu w tle (BITS).<br /><br /> Zawartość pakietu aplikacji wirtualnej jest dostarczana lokalnie do klienta. Oznacza to, że użytkownicy mogą uruchamiać je ich komputer nie jest podłączony do sieci.<br /><br /> Ta metoda jest przydatna w przypadku korzystania z powolnych lub zawodnych sieci oraz użytkowania komputerów sporadycznie łączących się z siecią.<br /><br /> Program Configuration Manager używa zdalnego (RDC Remote Differential Compression) do wysyłania do klientów tylko bajty plików, które uległy zmianie po zaktualizowaniu zawartości pakietu aplikacji wirtualnej. Klient programu Configuration Manager korzysta z kompresji RDC w celu skompilowania nowej wersji pakietu aplikacji wirtualnej na podstawie bieżącej wersji pakietu oraz wszelkie zmiany wysłane do klienta.<br /><br /> Ta metoda zapewnia odporność aplikacji użytkowników urządzeń przenośnych lub odłączonych. Administratorzy mogą wybrać zachowanie pakietu w pamięci podręcznej programu Configuration Manager po dostarczeniu, jeśli aplikacja wirtualna została wdrożona za pomocą działania instalacji. Pakiet w pamięci podręcznej klienta programu Configuration Manager służy jako lokalne, niezawodne źródło strumieniowania dla klienta App-V umieścić w swojej pamięci podręcznej.|Miejsce na dysku jest równe maksymalnie dwa razy rozmiar pakietu aplikacji wirtualnej jest wymagana na komputerze klienckim zachowania aplikacji wirtualnej w pamięci podręcznej programu Configuration Manager.|  

###  <a name="deployment-from-an-image"></a>Wdrożenia z obrazu

Aplikacje wirtualne można także preinstalować na komputerze, a następnie utworzyć obraz tego komputera w celu wdrożenia na innych. Jednak jeśli pakiet aplikacji wirtualnej został utworzony w innej lokacji, binarna replikacja różnicowa nie będą używane w celu pobrania aktualizacji aplikacji. Ta opcja może być przydatna w infrastrukturze pulpitu wirtualnego, gdzie aplikacje mają być dostępne natychmiast, a nie po ich pobraniu po zalogowaniu.    

##  <a name="migrating-from-an-app-v-infrastructure-to-a-configuration-manager-and-app-v-infrastructure"></a>Migracja z infrastruktury App-V do infrastruktury programu Configuration Manager i App-V  
Skorzystaj z poniższej tabeli ułatwią planowanie migracji z istniejącej infrastruktury programu App-V do zarządzania aplikacjami wirtualnymi w programie Configuration Manager.  

|Krok|Więcej informacji|  
|----------|----------------------|  
|Sprawdź bieżące aplikacje wirtualne, aby wybrać aplikacje, które mają zostać zmigrowane do infrastruktury programu Configuration Manager.|Brak dodatkowych informacji.|  
|Oceń użytkowników i urządzenia, dla których aplikacje wirtualne zostaną wdrożone.|Tworzenie kolekcji programu Configuration Manager, aby zgrupować użytkowników oraz urządzenia, dla których chcesz wdrożyć aplikacje wirtualne. Zobacz [wprowadzenie do kolekcji](/sccm/core/clients/manage/collections/introduction-to-collections).|  
|Migracja grup połączeń programu App-V 5 do środowisk wirtualnych programu Configuration Manager.|Zobacz [grup połączeń migracji App-V 5 do środowisk wirtualnych programu Configuration Manager](/sccm/apps/get-started/deploying-app-v-virtual-applications#migrate-app-v-5-connection-groups-to-configuration-manager-virtual-environments) w tym temacie.|  
|Sprawdź, czy którekolwiek aplikacje wirtualne istnieją jako pełne aplikacje w infrastrukturze programu Configuration Manager.|Aby ułatwić zarządzanie, można dodać aplikację wirtualną jako nowy typ wdrożenia do istniejącej pełnej aplikacji. Zobacz [tworzenia aplikacji](../../apps/deploy-use/create-applications.md).|  
|Utwórz aplikacje zastępujące istniejące pakiety programu App-V.|Zobacz [wprowadzenie do zarządzania aplikacjami](/sccm/apps/understand/introduction-to-application-management) i [tworzenia aplikacji](../../apps/deploy-use/create-applications.md).|  
|Rozpoczyna programu Configuration Manager do zarządzania aplikacjami wirtualnymi na kliencie po ich pierwszym wdrożeniu aplikacji wirtualnej. Dzięki temu programu Configuration Manager muszą zarządzać wszystkich aplikacji App-V na komputerze.|Brak dodatkowych informacji.|  
|Przekaż zawartość do odpowiednich punktów dystrybucji, aby umożliwić dostarczanie lokalne aplikacji.|Zobacz [zarządzania infrastrukturą zawartości i](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).|  
|Wdróż aplikację na klientów programu Configuration Manager.<br /><br /> Jeśli aplikacja App-V została utworzona przy użyciu starszej wersji programu sequencer, która nie tworzy pliku XML manifestu, można ją otworzyć i zapisać go w nowszej wersji programu sequencer w celu utworzenia pliku. Ten plik jest wymagany do wdrażania aplikacji wirtualnych za pomocą programu Configuration Manager.<br /><br /> App-V obsługuje pakiety aplikacji wirtualnych tworzone za pomocą wersji SoftGrid 4.1 SP1 lub 4.2 sekwensera.<br /><br /> Jeśli aplikacje zostały wcześniej zainstalowane lokalnie, należy je odinstalować przed wdrożeniem wirtualnej wersji danej aplikacji.|Zobacz [wdrażania aplikacji](../../apps/deploy-use/deploy-applications.md).|  
|System Center Configuration Manager nie obsługuje już pakietów i programów zawierających aplikacje wirtualne. Podczas migracji z programu Configuration Manager 2007 programu System Center Configuration Manager, Configuration Manager konwertuje te pakiety na aplikacje.<br /><br /> Anonse programu Configuration Manager 2007 są konwertowane na następujące typy wdrożeń:<br /><br /> -Migrowanie pakietów programu App-V bez anonsów:  Jeden typ wdrożenia, który używa domyślnych ustawień typu wdrożenia.<br /><br /> -Migrowanie pakietów programu App-V z jednym anonsem: Jeden typ wdrożenia, który korzysta z tych samych ustawień <br />                Anons programu Configuration Manager 2007.<br /><br /> -Migrowanie pakietów programu App-V wieloma anonsami: Typ wdrożenia dla każdego <br />                Anonse programu Configuration Manager 2007, który korzysta z ustawień tego anonsu.|Zobacz [planowanie migracji obiektów programu Configuration Manager programu System Center Configuration Manager](../../core/migration/planning-for-the-migration-of-objects.md).|  

##  <a name="migrating-app-v-5-connection-groups-to-configuration-manager-virtual-environments"></a>Migracja grup połączeń programu App-V 5 do środowisk wirtualnych programu Configuration Manager  
Środowiska wirtualne App-V w programie Configuration Manager umożliwiają aplikacjom wirtualnym wdrożono współużytkowanie tego samego systemu plików i rejestru na komputerach klienckich. Oznacza to, że w przeciwieństwie do standardowych aplikacji wirtualnych te aplikacje mogą udostępniać sobie dane. Środowiska wirtualne są tworzone i zmieniane na komputerach klienckich w momencie instalowania aplikacji oraz gdy następny klient oceni zainstalowane aplikacje. Środowiska wirtualne są podobne do grup połączeń w autonomicznym programie App-V 5.  

Podczas migracji grup połączeń z autonomicznego programu App-V 5 do środowisk wirtualnych programu Configuration Manager, należy zapewnić programu Configuration Manager prawidłowo założenie, że grupy połączeń, które już istnieją na komputerach klienckich oraz że środowisko użytkownika w tych grupach połączeń zostanie zachowane.  

Aby przekonwertować grupy połączeń programu App-V 5 do środowisk wirtualnych programu Configuration Manager:  

1.  Tworzenie aplikacji programu Configuration Manager dla wszystkich aplikacji, które były dostępne w programie App-V.  

2.  Wdróż te aplikacje dla użytkowników lub urządzeń z celem wdrożenia **Wymagane**. Wdrożenia dla użytkowników należy przeprowadzić dla tych samych użytkowników, którzy korzystali z aplikacji App-v. Wdrożenia dla komputerów należy przeprowadzić na tych samych komputerach, które były zainstalowane aplikacje programu App-V.  

3.  Po zakończeniu wdrożenia Utwórz środowiska wirtualne zgodne z grupami połączeń, które zostały opublikowane w samodzielnej aplikacji App-V. Środowisko wirtualne musi mieć tej samej pakietów (w szczególności typy wdrożeń aplikacji App-V 5) w tej samej kolejności.  

Aby uzyskać informacje o sposobie tworzenia środowisk wirtualnych App-V, zobacz [tworzenie środowisk wirtualnych App-V](../../apps/deploy-use/create-app-v-virtual-environments.md).  

Można też usunąć wszystkie grupy połączeń z klienta App-V, przed rozpoczęciem wdrażania aplikacji za pomocą programu Configuration Manager. Jednak ustawienia, które użytkownicy zapisanych w grupach połączeń programu App-V zostaną utracone.  

##  <a name="dynamic-suite-composition-in-app-v-46"></a>Tworzenie pakietów dynamicznych w kliencie App-v 4.6  
Tworzenie pakietów dynamicznych to funkcja, która umożliwia zdefiniowanie jednego pakietu aplikacji wirtualnej w zależności względem innego pakietu aplikacji wirtualnej. W czasie wykonywania aplikacji klient App-V obsługuje pakiet główny i pakiet zależny w tym samym środowisku wirtualnym aplikacji.  

Możesz używać tej funkcji w programie Configuration Manager oba pakiety musi być wdrożone i zarejestrowane za pomocą klienta App-V. Aby upewnić się, że zawartość pakietu zależnego jest obsługiwana lokalnie na komputerze klienckim, skonfigurować lokalne dostarczanie we wdrożeniu aplikacji (Pobierz i wykonaj).  

Więcej informacji o funkcji tworzenia pakietów dynamicznych programu App-V znajduje się w dokumentacji programu App-V.  

##  <a name="converting-app-v-46-applications-to-app-v-5-applications"></a>Konwertowanie aplikacji App-V 4.6 do aplikacji App-V 5  
W klientach App-V 4.6 i App-V 5 jest używany inny format pakietu aplikacji. Aplikacje sekwencjonowane za pomocą klienta App-V 4.6 nie są już obsługiwane. Ale App-V 5 zawiera narzędzie do konwersji pakietu, które można konwertować aplikacje. Więcej informacji zawiera [dokumentacja programu App-V 5](http://technet.microsoft.com/library/jj713472.aspx).  

Aby skonwertować aplikację App-V 4.6 do aplikacji App-V 5, wykonaj poniższe czynności:  

1.  Konwertuj lub zsekwencjonować pakiety App-V 4.6 do formatu App-V 5.  

2.  Wdróż klienta App-V 5 na komputerach w hierarchii.  

3.  Utwórz nowe aplikacje, które zawierają typy wdrożeń dla aplikacji App-V 5, a następnie utwórz reguły zastępowania w celu zastąpienia aplikacji App-V 4.6.  

4.  Utwórz środowiska wirtualne zgodnie z potrzebami.  

5.  Wdróż nowe aplikacje App-V 5 na komputerach.  

##  <a name="user-and-deployment-configuration-files"></a>Pliki konfiguracyjne użytkownika i wdrożenia  
Pliki konfiguracji wdrożenia i użytkownika mają ustawień, które kontrolują sposób działania aplikacji. Te pliki umożliwia zmianę ustawień aplikacji bez ponownie określanie kolejności aplikacji.  

Typowa aplikacja App-V 5 może zawierać następujące pliki:  

-   Plik pakietu (*.appv) aplikacji  

-   Plik konfiguracji użytkownika  

-   Plik konfiguracji wdrożenia  

Plik konfiguracji użytkownika zawiera ustawienia, które mają zastosowanie tylko do zalogowanego użytkownika. Można na przykład edytować pliki konfiguracji do zmiany informacji o skrócie aplikacji, który ma być wdrożony dla użytkowników. Można również utworzyć aplikację programu Configuration Manager z wieloma typami wdrożeń. Każdego typu wdrożenia może zawierać różne pliki konfiguracji użytkownika oraz zastosować reguły wymagań, aby upewnić się, że te pliki są zainstalowane dla odpowiednich użytkowników.  

Plik konfiguracji wdrożenia zawiera ustawienia, które są stosowane do komputera, takich jak ustawienia rejestru. Plik może także zawierać ustawienia użytkownika, które są stosowane do wszystkich użytkowników.  

Jeśli chcesz wdrożyć aplikacje wirtualne App-V 5 za pomocą programu Configuration Manager, wszystkie trzy pliki muszą być obecne w tym samym folderze podczas tworzenia typu wdrożenia App-V 5. W przypadku wielu plików w folderze, Configuration Manager będzie używać najnowszej.  

Więcej informacji zawiera [dokumentacja programu App-V 5](http://technet.microsoft.com/library/jj713466.aspx).  

##  <a name="app-v-local-interaction"></a>Lokalna interakcja klienta App-V  
W niektórych scenariuszach wdrażania aplikacje są instalowane lokalnie na komputerach klienckich, a inne są wdrażane na tych samych komputerach klienckich jako aplikacje wirtualne. Domyślnie aplikacje zainstalowane lokalnie nie widzą aplikacji zwirtualizowanych ani nie mogą się z nimi komunikować. To jest zamierzone zachowanie funkcji izolacji aplikacji, który zapewnia App-V. Interakcja lokalna to funkcji klienta App-V, który można włączyć dla każdej aplikacji umożliwić aplikacjom zainstalowane lokalnie, działające na komputerze klienckim, aby zobaczyć i komunikować się z aplikacji zwirtualizowanych. Program Configuration Manager i App-V w pełni obsługują funkcję interakcji lokalnej.  

Więcej informacji o funkcji tworzenia interakcji lokalnej App-V w dokumentacji programu App-V.  

##  <a name="app-v-5-shared-content-store"></a>Magazyn zawartości udostępnionej klienta App-V 5  
Program Configuration Manager obsługuje funkcję App-V 5 magazynu zawartości udostępnionej klienta. Więcej informacji zawiera temat [Planowanie udostępnionego magazynu zawartości (SCS) programu App-V 5.0](http://technet.microsoft.com/library/jj713431.aspx).  

##  <a name="monitoring-virtual-applications"></a>Monitorowanie aplikacji wirtualnych  

### <a name="virtual-application-reports"></a>Raporty aplikacji wirtualnych  
Za pomocą następujących raportów do monitorowania aplikacji App-V w środowisku programu Configuration Manager:  

|Nazwa raportu|Opis|  
|-----------------|-----------------|  
|Wyniki środowiska wirtualnego App-V|Przedstawia informacje o wybranym środowisku wirtualnym, który znajduje się w określonym stanie względem wybranej kolekcji (tylko App-V 5).|  
|Wyniki środowiska wirtualnego App-V dla zasobu|Przedstawia informacje o wybranym środowisku wirtualnym przy określonym zasobie i dowolnym typie wdrożenia środowiska (tylko App-V 5).|  
|Status środowiska wirtualnego App-V|Przedstawia informacje o zgodności wybranego środowiska wirtualnego w wybranej kolekcji. **Zachowywane** kolumny w tym raporcie zawiera zasoby, w których uprzednio skonfigurowane środowisko wirtualne nie ma już zastosowania, ale jest zachowane w celu utrzymania ustawień użytkownika w aplikacjach wykonywanych w środowisku wirtualnym (tylko App-V 5).|  
|Komputery z określoną aplikacją wirtualną|Przedstawia podsumowanie komputerów z określonym skrótem aplikacji App-V utworzenie Application Virtualization Management Sequencer (tylko App-V 4.6).|  
|Komputery z określonym pakietem aplikacji wirtualnych|Przedstawia listę komputerów, które zainstalowany określony App-V pakiet aplikacji (tylko App-V 4.6).|  
|Liczba wszystkich wystąpień pakietów aplikacji wirtualnych|Pokazuje liczbę wszystkich wykrytych pakietów aplikacji App-V (tylko App-V 4.6).|  
|Liczba wszystkich wystąpień aplikacji wirtualnych|Pokazuje liczbę wszystkich wykrytych aplikacji App-V (tylko App-V 4.6).|  

### <a name="log-files"></a>Pliki dziennika  
Program Configuration Manager rejestruje informacje o wdrożeniach aplikacji wirtualnych w plikach dziennika. Aby uzyskać informacje o dzienniku pliki przez aplikacje wirtualne i użycie zarządzania aplikacji programu Configuration Manager, zobacz [pliki dziennika w programie System Center Configuration Manager](../../core/plan-design/hierarchy/log-files.md).  

Dla systemu Windows Vista, Windows 7 i Windows 8 dzienniki klienta App-V można znaleźć w C:\ProgramData\Microsoft\Application Virtualization Client.  

