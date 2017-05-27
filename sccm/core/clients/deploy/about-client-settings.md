---
title: Ustawienia klienta | Dokumentacja firmy Microsoft
description: "Wybierz ustawienia klienta za pomocą konsoli administratora programu System Center Configuration Manager."
ms.custom: na
ms.date: 03/24/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f7560876-8084-4570-aeab-7fd44f4ba737
caps.latest.revision: 15
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: ae60eb25383f4bd07faaa1265185a471ee79b1e9
ms.openlocfilehash: 3d90f16eac59b7069ff2f33170eba85d2cde65ef
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="about-client-settings-in-system-center-configuration-manager"></a>Informacje o ustawieniach klienta w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Wszystkimi ustawieniami klienta w programie System Center Configuration Manager są zarządzane w konsoli programu Configuration Manager z **ustawień klienta** w węźle **administracji** obszaru roboczego. Menedżer konfiguracji zawiera zbiór ustawień domyślnych. Zmiana ustawień domyślnych klienta, te ustawienia są stosowane do wszystkich klientów w hierarchii. Można również konfigurować niestandardowe ustawienia klienta, które zastąpią domyślne ustawienia klienta po ich przypisaniu do kolekcji. Aby uzyskać informacje na temat konfigurowania ustawień klienta, zobacz [Jak skonfigurować ustawienia klienta w programie System Center Configuration Manager](../../../core/clients/deploy/configure-client-settings.md).  

Wiele ustawień klienta nie wymaga wyjaśnień. Inne są opisane w tym miejscu.  

## <a name="background-intelligent-transfer-service"></a>Usługa inteligentnego transferu w tle  

-   **Ogranicz maksymalną przepustowość sieci dla transferów w tle wykonywanych przez usługę BITS**  

   Kiedy ta opcja jest **True** lub **tak**, klienci będą używać funkcji ograniczania przepustowości usługi BITS.  

-   **Godzina rozpoczęcia okna ograniczenia przepustowości**  

   Określ czas rozpoczęcia lokalnego dla okna ograniczenia przepustowości usługi BITS.  

-   **Godzina zakończenia okna ograniczenia przepustowości**  

   Określ czas zakończenia lokalnego dla okna ograniczenia przepustowości usługi BITS. Jeśli równa **godzina rozpoczęcia okna ograniczenia przepustowości**, ograniczenia przepustowości usługi BITS jest zawsze włączona.  

-   **Maksymalna szybkość transferu w oknie ograniczenia przepustowości (Kb/s)**  

   Określ maksymalną szybkość transmisji używanego przez klientów podczas okna.  

-   **Zezwalaj na pobieranie usługi BITS poza oknem ograniczenia przepustowości**  

   Wybierz tę opcję, aby umożliwić klientom programu Configuration Manager za pomocą osobnych ustawień usługi BITS poza określonym oknem.  

-   **Maksymalna szybkość transferu poza oknem ograniczenia przepustowości (Kb/s)**  

   Określ maksymalną szybkość transmisji którego klienci będą używać poza BITÓW ograniczania okna, gdy wybrano ograniczenia przepustowości poza oknem usługi BITS.  

## <a name="client-cache-settings"></a>Ustawienia pamięci podręcznej klienta

- **Konfigurowanie usługi BranchCache**

  Począwszy od wersji 1606, użyj tego ustawienia, aby skonfigurować komputer kliencki pod kątem [usługi BranchCache](/sccm/core/plan-design/configs/support-for-windows-features-and-networks#branchcache). Aby zezwolić na komputerze klienckim pamięci podręcznej usługi BranchCache, **Włącz usługę BranchCache** do **tak**.

- **Skonfiguruj rozmiar pamięci podręcznej klienta**

  Pamięci podręcznej klienta na komputerach z systemem Windows są przechowywane tymczasowe pliki używane do zainstalowania aplikacji i programów. Wybierz **tak** do określenia **maksymalny rozmiar pamięci podręcznej** (w megabajtach lub procent dysku). Jeśli ta opcja jest **nr**, domyślny rozmiar to 5,120 MB.

## <a name="client-policy"></a>Zasady klienta  

-   **Interwał sondowania zasad klienta (minuty)**  

   Określ częstotliwość pobierania zasad klienta przez następujących klientów programu Configuration Manager:  

  -   Komputery z systemem Windows (na przykład komputery stacjonarne, serwery, komputery przenośne)  

  -   Urządzenia przenośne, które rejestruje programu Configuration Manager  

  -   Komputery Mac  

  -   Komputery z systemem Linux lub UNIX  

-   **Włącz sondowanie zasad użytkownika na klientach**  

   Po ustawieniu tej opcji **True** lub **tak**, a Configuration Manager ma [odnalezione użytkownika](../../../core/servers/deploy/configure/about-discovery-methods.md#bkmk_aboutUser), klientów na komputerach będą otrzymywać aplikacje i programy przeznaczone dla zalogowanego użytkownika.  

   Ponieważ katalog aplikacji otrzymuje listę oprogramowania dostępnego dla użytkowników z serwera lokacji, to ustawienie nie ma być **True** lub **tak** dla użytkowników, aby wyświetlić aplikacje i zażądać ich z katalogu aplikacji. Jeśli to ustawienie jest jednak **False** lub **nr**, następujące nie będzie działać, jeśli użytkownicy korzystają z katalogu aplikacji:  

  -   Użytkownicy nie mogą instalować aplikacji widocznych w wykazie aplikacji.  

  -   Użytkownicy nie będą widzieć powiadomień dotyczących ich żądań zatwierdzenia aplikacji. Zamiast tego muszą odświeżyć katalog aplikacji i sprawdzić stan zatwierdzenia.  

  -   Użytkownicy nie będą otrzymywać poprawek i aktualizacji aplikacji, które są opublikowane w katalogu aplikacji. Jednak zobaczą zmiany w informacjach o aplikacji w katalogu aplikacji.  

  -   Jeśli użytkownik usunie wdrożenie aplikacji po zainstalowaniu przez klienta aplikacji z katalogu aplikacji, klienci będą sprawdzać przez maksymalnie dwa dni, czy aplikacja jest zainstalowana.  

   Ponadto, gdy to ustawienie jest **False** lub **nr**, użytkownicy nie będą otrzymywali wymaganych aplikacji wdrażanych dla użytkowników lub innych zadań administracyjnych w zasadach użytkownika.  

   To ustawienie dotyczy użytkowników, gdy komputer będzie połączony z siecią intranet lub Internetem. Musi być **True** lub **tak** Jeśli chcesz również włączyć zasady użytkownika w Internecie.  

-   **Włącz żądania dotyczące zasad użytkownika od klientów internetowych**  

   Kiedy klienta i lokację skonfigurowano do internetowego zarządzania i zostanie wybrana opcja jako **True** lub **tak** i oba poniższe warunki są spełnione, użytkownicy będą otrzymywali zasad użytkownika, gdy komputer jest połączony z Internetem:  

  -   **Włącz sondowanie zasad użytkownika na klientach** ustawienia klienta jest **True**, lub **Włącz zasady użytkownika na klientach** jest **tak**.  

  -   Internetowy punkt zarządzania pomyślnie uwierzytelnił użytkownika za pomocą uwierzytelniania systemu Windows (Kerberos lub NTLM).  

   Jeśli dla tej opcji nie zostanie określona inna wartość niż **Fałsz** lub **Nie**, lub gdy jeden z warunków nie zostanie spełniony, komputer połączony z Internetem będzie otrzymywał wyłącznie zasady komputera. Przy takim scenariuszu użytkownicy mogą nadal oglądać i instalować aplikacje oraz zażądać ich z internetowego katalogu aplikacji. Jeśli to ustawienie jest **False** lub **nr** , ale **Włącz sondowanie zasad użytkownika na klientach** jest **True** lub **Włącz zasady użytkownika na klientach** jest **tak**, użytkownicy nie będą otrzymywali zasady użytkownika, dopóki komputer jest połączony z siecią intranet.  

   Aby uzyskać więcej informacji dotyczących zarządzania klientami w Internecie, zobacz [uwagi dotyczące komunikacji klienta z Internetu lub niezaufanego lasu](../../../core/plan-design/hierarchy/communications-between-endpoints.md#BKMK_clientspan) w [komunikację między punktami końcowymi w programie System Center Configuration Manager](../../../core/plan-design/hierarchy/communications-between-endpoints.md).  

  > [!NOTE]  
  >  Żądania zatwierdzenia aplikacji od użytkowników nie wymagają zasad użytkownika ani uwierzytelnienia użytkownika.  

##  <a name="compliance-settings"></a>Ustawienia zgodności  

-   **Zaplanuj ocenę zgodności**  

     Wybierz **harmonogram** utworzyć domyślny harmonogram, która będzie wyświetlana użytkownikom podczas wdrażania linii bazowej konfiguracji. Tę wartość można skonfigurować dla każdej podstawy w oknie dialogowym **Wdrażanie podstawy konfiguracji** .  

-   **Włącz dane użytkownika i profile**  

     Wybierz **tak** Jeśli chcesz wdrożyć [dane użytkownika i profile](../../../compliance/deploy-use/create-user-data-and-profiles-configuration-items.md) elementy konfiguracji na komputerach z systemem Windows 8 w hierarchii.  

## <a name="computer-agent"></a>Agent komputera  

-   **Domyślny punkt witryny sieci Web katalogu aplikacji**  

     Program Configuration Manager używa tego ustawienia, aby łączyć użytkowników z katalogiem aplikacji w Centrum oprogramowania. Użytkownik może określić serwer hostujący punkt witryny sieci Web katalogu aplikacji przy użyciu nazwy NetBIOS lub FQDN, automatyczne wykrywanie lub adres URL wdrożeń dostosowanych. W większości przypadków najlepszym wyborem będzie automatyczne wykrywanie, które ma następujące zalety:  

    -   Klienci automatycznie otrzymują punkt witryny sieci Web katalogu aplikacji z ich lokacji, jeśli ich witryny ma punkt witryny sieci Web katalogu aplikacji.  

    -   Punktów wykazu aplikacji witryny sieci Web w sieci intranet skonfigurowane dla protokołu HTTPS są preferowane względem tych, które nie są skonfigurowane dla protokołu HTTPS. Pozwala to chronić przed serwerami nieautoryzowanymi.

    -   Gdy klienci są skonfigurowani do zarządzania klientami sieci intranet i internetowy, otrzymają oni punkt witryny sieci Web katalogu aplikacji internetowych połączonymi z Internetem oraz intranetowy punkt witryny sieci Web katalogu aplikacji znajdujących się w sieci intranet.  

     Automatyczne wykrywanie nie gwarantuje, że klienci otrzymają najbliższy punkt witryny sieci Web katalogu aplikacji. Użytkownik może zrezygnować z funkcji **Wykryj automatycznie** z następujących przyczyn:  

     -   Użytkownik chce ręcznie skonfigurować najbliższy serwer dla klientów lub uniemożliwić klientom łączenie się z serwerem przez wolne połączenie sieciowe.  

     -   Użytkownik chce kontrolować, którzy klienci łączą się z którym serwerem. Może to być przydatne przy testowaniu, ze względu na wydajność lub z przyczyn biznesowych.  

     -   Użytkownik nie chce czekać do 25 godzin na zmianę sieci, aby klienci zostali skonfigurowani przy użyciu innego punktu witryny sieci Web katalogu aplikacji.  

     Jeśli punktu witryny sieci Web katalogu aplikacji zamiast korzystać z automatycznego wykrywania, określ nazwę NetBIOS zamiast intranetową nazwę FQDN. Pozwala to zmniejszyć prawdopodobieństwo, że użytkownicy będą monitowani o poświadczenia podczas nawiązywania połączenia z katalogiem aplikacji w sieci intranet. Aby korzystać z nazwy NetBIOS, muszą być spełnione następujące warunki:  

     -   Nazwa NetBIOS została określona we właściwościach punktu witryny sieci Web katalogu aplikacji.  

     -   Korzystać z usługi WINS lub wszyscy klienci należą do tej samej domeny co punkt witryny sieci Web katalogu aplikacji.  

     -   Punkt witryny sieci Web katalogu aplikacji został skonfigurowany dla połączeń klienta HTTP, lub jest skonfigurowany do połączeń klienckich HTTPS i certyfikatu serwera sieci web ma nazwę NetBIOS.  

     Zazwyczaj użytkownicy są monitowani o poświadczenia, gdy adres URL ma nazwę FQDN, ale nie w przypadku, gdy adres URL jest nazwą NetBIOS. Monit będzie wyświetlany zawsze wtedy, gdy użytkownicy będą się łączyć z Internetu, ponieważ to połączenie musi korzystać z internetowej nazwy FQDN. Jeśli jest wyświetlany monit o podanie poświadczeń gdy użytkownicy są połączeni z Internetem, należy sprawdzić, czy serwer, na którym jest uruchomiony punkt witryny sieci Web katalogu aplikacji, może się połączyć z kontrolerem domeny konta użytkownika, co umożliwi uwierzytelnienie użytkownika przy użyciu protokołu Kerberos.  

    > [!NOTE]  
    >  Opis działania automatycznego wykrywania:  
    >   
    >  Klient wysyła żądanie lokalizacji usługi do punktu zarządzania. Jeśli w tej samej lokacji, w której znajduje się klient, istnieje punkt witryny sieci Web katalogu aplikacji, serwer zostanie przekazany klientowi jako serwer, który ma być wykorzystywany jako serwer katalogu aplikacji. Gdy więcej niż jeden punkt witryny sieci Web katalogu aplikacji jest dostępna w lokacji, serwer obsługujący protokół HTTPS ma pierwszeństwo przed serwerem nie obsługującym protokołu HTTPS. Po powyższym filtrowaniu wszyscy klienci otrzymają jeden z serwerów, który będzie używany jako katalog aplikacji; Menedżer konfiguracji nie równoważy obciążenia między wieloma serwerami. Gdy lokacja klienta nie ma punkt witryny sieci Web katalogu aplikacji, punkt zarządzania zwróci w sposób niedeterministyczny punkt witryny sieci Web katalogu aplikacji z hierarchii.  
    >   
    >  Jeśli klient znajduje się w sieci intranet, jeśli wybrany punkt witryny sieci Web katalogu aplikacji jest skonfigurowany przy użyciu nazwy NetBIOS dla adresu URL katalogu aplikacji, klienci otrzymają tę nazwę NetBIOS zamiast nazwy FQDN w sieci intranet. Po stwierdzeniu, że klient znajduje się w Internecie, klient otrzyma wyłącznie internetową nazwę FQDN.  
    >   
    >  Klient wysyła to żądanie lokalizacji usługi co 25 godzin lub po wykryciu zmiany sieci. Na przykład, jeśli klient zostanie przeniesiony z sieci intranet do Internetu i zlokalizuje internetowy punkt zarządzania, internetowy punkt zarządzania udostępni klientom internetowe serwery punktów witryny sieci Web katalogu aplikacji.  

-   **Dodaj domyślną witrynę sieci Web katalogu aplikacji do strefy Zaufane witryny programu Internet Explorer**  

     Jeśli ta opcja jest **True** lub **tak**, bieżący domyślny katalog aplikacji witryny sieci Web adres URL jest automatycznie dodawany do strefy Zaufane witryny w programie Internet Explorer na komputerach klienckich.  

     To ustawienie zapewnia, że tryb chroniony programu Internet Explorer jest wyłączony. Jeśli tryb chroniony jest włączony, klient programu Configuration Manager nie może być mogli instalować aplikacje z katalogu aplikacji. Domyślnie strefa Zaufane witryny obsługuje również logowanie użytkownika do katalogu aplikacji, co wymaga uwierzytelnienia systemu Windows.  

     Jeśli opuścisz tę opcję jako **False**, klientów programu Configuration Manager nie można instalować aplikacji z katalogu aplikacji, chyba że te ustawienia programu Internet Explorer są skonfigurowane w innej strefie dla adresu URL katalogu aplikacji używanego przez klientów.  

    > [!NOTE]  
    >  Zawsze, gdy program Configuration Manager doda domyślnego katalogu aplikacji do strefy Zaufane witryny, programu Configuration Manager usunięcie poprzedniej domyślny adres URL katalogu aplikacji że było dodaje nowy wpis, należy dodać program Configuration Manager.  
    >   
    >  Menedżer konfiguracji nie może dodać adresu URL, jeśli został już określony w jednej ze stref zabezpieczeń. W tym scenariuszu należy usunąć adres URL z innej strefy lub ręcznie skonfigurować wymagane ustawienia programu Internet Explorer.  

-   **Pozwól na uruchamianie aplikacji Silverlight w trybie podwyższonego zaufania**  

     To ustawienie musi być **tak** Jeśli użytkownicy uruchamiają klienta programu Configuration Manager i korzystać z katalogu aplikacji.  

     Zmiana tego ustawienia będzie wprowadzona po kolejnym załadowaniu przeglądarki lub odświeżeniu obecnie otwartego okna przeglądarki przez użytkowników.  

     Aby uzyskać więcej informacji na temat tego ustawienia, zobacz [certyfikaty programu Microsoft Silverlight 5 i tryb podwyższonego zaufania wymagany przez katalog aplikacji](../../../apps/plan-design/security-and-privacy-for-application-management.md#BKMK_CertificatesSilverlight5) w [bezpieczeństwo i prywatność zarządzania aplikacjami w programie System Center Configuration Manager](../../../apps/plan-design/security-and-privacy-for-application-management.md).  

-   **Nazwa organizacji wyświetlana w Centrum oprogramowania**  

     Wpisz nazwę wyświetlaną użytkownikom w Centrum oprogramowania. Te informacje o znakowaniu ułatwiają użytkownikom zidentyfikowanie tej aplikacji jako pochodzącej z zaufanego źródła.  

-   **Użyj nowego Centrum oprogramowania**  

     Włączenie wszystkich komputerów klienckich przez te ustawienia klienta użyje nowego centrum oprogramowania. Centrum oprogramowania pokazuje dostępne użytkownika aplikacje, które były wcześniej dostępne tylko w katalogu aplikacji Silverlight zależne.  

     Punkt witryny sieci Web katalogu aplikacji i usług sieci web katalogu aplikacji punktu są nadal wymagane dostępnych użytkownika aplikacji pojawią się w Centrum oprogramowania role systemu lokacji.  

     Aby uzyskać więcej informacji, zobacz [Planowanie konfiguracji zarządzania aplikacjami w programie System Center Configuration Manager i przeprowadzanie konfiguracji](../../../apps/plan-design/plan-for-and-configure-application-management.md).  

-   **Uprawnienia do instalacji**  

    > [!WARNING]  
    >  To ustawienie dotyczy katalogu aplikacji i Centrum oprogramowania. To ustawienie nie obowiązuje, gdy użytkownicy korzystają z portalu firmy.  

     Konfigurowanie sposobu inicjowania instalacji oprogramowania, aktualizacji oprogramowania oraz sekwencji zadań przez użytkowników:  

    -   **Wszyscy użytkownicy**: Użytkownicy zalogowani do komputera klienckiego z dowolnymi uprawnieniami oprócz gościa uprawnień można inicjować instalację oprogramowania, aktualizacji oprogramowania i sekwencji zadań.  

    -   **Tylko Administratorzy**: Użytkownicy zalogowani do komputera klienckiego musi być członkiem lokalnej grupy administratorów, aby inicjować instalację oprogramowania, aktualizacji oprogramowania i sekwencji zadań.  

    -   **Tylko administratorzy i użytkownicy podstawowi**: Użytkownicy zalogowani do komputera klienckiego musi być członkiem lokalnej grupy Administratorzy lub być użytkownikiem podstawowym komputera do inicjowania instalacji oprogramowania, aktualizacji oprogramowania i sekwencji zadań.  

    -   **Użytkownicy nie**: Użytkownicy zalogowani do komputera klienckiego nie mogą inicjować instalację oprogramowania, aktualizacji oprogramowania i sekwencji zadań. Wdrożenia wymagane dla komputera są zawsze instalowane po upływie terminu wdrożenia. Użytkownicy nie mogą inicjować instalowania oprogramowania z katalogu aplikacji lub Centrum oprogramowania.  

-   **Zawieś wprowadzanie numeru PIN funkcji BitLocker przy ponownym uruchomieniu**  

     Jeśli na komputerach skonfigurowano wprowadzanie numeru PIN funkcji BitLocker, za pomocą tej opcji można pominąć wymaganie wprowadzania numeru PIN przy ponownym uruchomieniu komputera po zainstalowaniu oprogramowania.  

    -   **Zawsze**: Program Configuration Manager tymczasowo zawiesi funkcji BitLocker po zainstalowaniu oprogramowania wymagającego ponownego uruchomienia i zainicjował ponowne uruchomienie komputera. To ustawienie dotyczy tylko ponowne uruchomienie komputera, który jest inicjowane przez program Configuration Manager i nie zawiesza wymagania wprowadzania numeru PIN funkcji BitLocker po ponownym uruchomieniu komputera przez użytkownika. Wymaganie wprowadzania numeru PIN funkcji BitLocker zostanie wznowione po uruchomieniu systemu Windows.

    -   **Nigdy nie**: Program Configuration Manager nie zawiesi funkcji BitLocker przy następnym uruchomieniu komputera po zainstalowaniu oprogramowania wymagającego ponownego uruchomienia. Przy takim scenariuszu instalowanie oprogramowania nie zostanie zakończone przed wprowadzeniem numeru PIN przez użytkownika w celu ukończenia standardowego procesu uruchamiania i załadowania systemu Windows.

-   **Wdrażanie aplikacji oraz aktualizowanie oprogramowania jest zarządzane przez dodatkowe oprogramowanie**  

     Tę opcję należy włączyć tylko po spełnieniu jednego z następujących warunków:  

    -   Użytkownik korzysta z rozwiązania dostawcy wymagającego, aby to ustawienie było włączone.  

    -   Możesz użyć zestawie programu Configuration Manager software development kit (SDK) w celu zarządzania powiadomieniami agentem klienta i instalowaniem aplikacji i aktualizacji oprogramowania.  

    > [!WARNING]  
    >  Jeśli wybierzesz tę opcję, gdy żaden z powyższych warunków nie ma zastosowania, aktualizacji oprogramowania i wymagane aplikacje nie zainstaluje na komputerach klienckich. To ustawienie nie uniemożliwia użytkownikom instalowanie aplikacji z katalogu aplikacji lub uniemożliwić im zainstalowanie na komputerach klienckich pakietów, programów i sekwencji zadań.  

-   **Zasady wykonywania programu PowerShell**  

     Skonfiguruj sposób klientów programu Configuration Manager mogą uruchamiać skrypty programu Windows PowerShell. Skrypty te są często używane do wykrywania w elementach konfiguracji ustawień zgodności. Mogą być również wysyłane w ramach wdrożenia jako skrypty standardowe.  

    -   **Obejście**: Klient programu Configuration Manager pomija konfigurację programu Windows PowerShell na komputerze klienckim, co umożliwia uruchamianie niepodpisanych skryptów.  

    -   **Ograniczone**: Klient programu Configuration Manager korzysta z bieżącej konfiguracji środowiska Windows PowerShell na komputerze klienckim. Ta konfiguracja Określa, czy umożliwia uruchamianie niepodpisanych skryptów.  

    -   **Wszystko podpisane**: Klient programu Configuration Manager uruchamia skrypty tylko wtedy, gdy podpisała ich zaufanego wydawcę. To ograniczenie obowiązuje niezależnie od bieżącej konfiguracji programu Windows PowerShell na komputerze klienckim.  

     Ta opcja wymaga co najmniej programu Windows PowerShell w wersji 2.0. Wartość domyślna to **wszystko podpisane**.  

    > [!TIP]  
    >  Jeśli zakończy się niepowodzeniem ze względu na to ustawienie klienta uruchomienie niepodpisanych skryptów, Configuration Manager zgłosi ten błąd w następujący sposób:  
    >   
    > -   Identyfikator błędu **0X87D00327** i opis **skrypt nie jest podpisany** jako błąd stanu wdrożenia w **monitorowanie** obszaru roboczego w konsoli programu Configuration Manager.  
    > -   Kody błędów i opisy **0X87D00327** i **skrypt nie jest podpisany** lub **0X87D00320** i **host skryptów nie został jeszcze zainstalowany** z typem błąd **błąd odnajdywania** w raportach. Na przykład **szczegóły błędów elementów konfiguracji w linii bazowej konfiguracji dla zasobu**.  
    > -   Komunikat **skrypt nie jest podpisany (błąd: 87D 00327; Źródło: CCM)** w **DcmWmiProvider.log** pliku.  

-   **Wyłącz losowe generowanie terminu ostatecznego**  

     To ustawienie określa, czy klient stosuje maksymalnie 2 godziny opóźnienie aktywacji w celu zainstalowania wymaganych aktualizacji oprogramowania po osiągnięciu terminu ostatecznego. Opóźnienie aktywacji jest domyślnie wyłączone.  

     W scenariuszach infrastruktury pulpitu wirtualnego (VDI) to opóźnienie może pomóc w rozłożeniu obliczeniowej Procesora i transferu danych dla komputera, który ma wiele maszyn wirtualnych z systemem klienta programu Configuration Manager. Nawet jeśli nie używasz VDI, jeśli wielu klientów instaluje jednocześnie te same aktualizacje, to może to zwiększyć użycie Procesora na serwerze lokacji. Można go również spowolnić punkty dystrybucji i znacznie zmniejszyć dostępną przepustowość sieci.  

     Jeśli wymagane aktualizacje oprogramowania muszą być zainstalowane niezwłocznie po osiągnięciu terminu ostatecznego, wybierz **tak** dla tego ustawienia.  

-   **Okres prolongaty dla wymuszania po (w godzinach) ostatecznego terminu wdrożenia**

     W niektórych przypadkach można umożliwić użytkownikom więcej czasu do instalacji wymagane wdrożenia aplikacji lub aktualizacji oprogramowania poza żadnych terminy, które zostały skonfigurowane. Może to zazwyczaj być wymagane po komputerze została wyłączona przez dłuższy czas i musi zainstalować dużej liczby wdrożeń aplikacji lub aktualizacji. Na przykład jeśli użytkownik ma tylko zwróciła urlopie, konieczne może być oczekiwanie na długo jako aplikacja zaległe wdrożenia są instalowane. Aby rozwiązać ten problem, można zdefiniować okres prolongaty wymuszania przez wdrożenie ustawień klienta programu Configuration Manager do kolekcji.

     Można ustawić okres prolongaty 1 do 120 godzin. To ustawienie jest używane w połączeniu z właściwością wdrożenia **opóźnienie wymuszania tego wdrożenia, zgodnie z preferencjami użytkownika**. Aby uzyskać więcej informacji, zobacz [wdrażania aplikacji](/sccm/apps/deploy-use/deploy-applications).

##  <a name="computer-restart"></a>Ponowne uruchomienie komputera  
 Po określeniu tych ustawień dotyczących ponownego uruchomienia komputera należy sprawdzić, czy wartość interwału tymczasowego powiadamiania o ponownym uruchomieniu i wartość interwału odliczania końcowego są krótsze od najkrótszego okna obsługi ustawionego dla komputera.  

 Aby uzyskać więcej informacji o korzystaniu z okien obsługi, zobacz [Używanie okien obsługi w programie System Center Configuration Manager](../../../core/clients/manage/collections/use-maintenance-windows.md).  

##  <a name="endpoint-protection"></a>Program Endpoint Protection  

-   **Zarządzanie klientem programu Endpoint Protection na komputerach klienckich**  

     Wybierz **True** lub **tak** Jeśli chcesz zarządzać istniejącymi klientami programu Endpoint Protection na komputerach w hierarchii.  

     Wybierz tę opcję, jeśli zainstalowano klienta programu Endpoint Protection i chce nim zarządzać za pomocą programu Configuration Manager.  

     Ponadto należy wybrać tę opcję, jeśli chcesz utworzyć skrypt w celu odinstalowania istniejącego rozwiązania chroniące przed złośliwym kodem, zainstalować klienta programu Endpoint Protection i wdrożenia tego skryptu za pomocą Menedżera konfiguracji aplikacji lub pakietów i programów.  

-   **Zainstaluj klienta programu Endpoint Protection na komputerach klienckich**  

     Wybierz **True** lub **tak** Aby zainstalować i włączyć klienta programu Endpoint Protection na komputerach klienckich, gdy go nie jest jeszcze zainstalowany.  

    > [!NOTE]  
    >  Jeśli jest już zainstalowany klient programu Endpoint Protection, wybierając **False** lub **nr** nie spowoduje odinstalowania klienta programu Endpoint Protection. Aby odinstalować klienta programu Endpoint Protection, **klienta zarządzania Endpoint Protection na komputerach klienckich** ustawienie klienta **False** lub **nr**. Następnie można wdrożyć pakiet i program, aby odinstalować klienta programu Endpoint Protection.  

-   **W przypadku urządzeń Windows Embedded z filtrami zapisu należy zatwierdzić instalację klienta programu Endpoint Protection (wymaga to ponownego uruchomienia komputera).**  

     Wybierz **tak** wyłączyć filtr zapisu na urządzeniu Windows Embedded, a następnie ponownie uruchomić urządzenie. co spowoduje zatwierdzenie instalacji na urządzeniu.  

     Po określeniu dla opcji wartości **Nie** klient zostanie zainstalowany na tymczasowej nakładce, która zostanie wyczyszczona po ponownym uruchomieniu urządzenia. Przy takim scenariuszu klient programu Endpoint Protection nie zostanie zatwierdzony przed zatwierdzeniem zmian na urządzeniu przez inną instalację. To jest ustawienie domyślne.  

-   **Pomija wszelkie wymagane ponowne uruchomienie komputera po zainstalowaniu klienta programu Endpoint Protection**  

     Wybierz **True** lub **tak** pominąć ponowne uruchomienie komputera, jeśli jest ono wymagane po zainstalowaniu klienta programu Endpoint Protection.  

    > [!IMPORTANT]  
    >  Jeśli klient programu Endpoint Protection wymaga ponownego uruchomienia komputera, a to ustawienie jest **False**, ponowne uruchomienie nastąpi niezależnie od wszelkich okien obsługi, które zostały skonfigurowane.  

-   **Dozwolony okres czasu użytkownicy mogą odłożyć ponowne uruchomienie w celu ukończenia instalacji programu Endpoint Protection (godziny)**  

     Określ liczbę godzin, który użytkownicy mogą odłożyć ponowne uruchomienie komputera, jeśli jest to wymagane po zainstalowaniu klienta programu Endpoint Protection. Tej opcji można skonfigurować tylko wtedy, gdy **Pomiń wszystkie wymagane ponowne uruchomienie komputera po zainstalowaniu klienta programu Endpoint Protection** jest opcja **False**.  

-   **Wyłącz źródła alternatywne (takie jak Windows Update, Microsoft Windows Server Update Services lub udziały UNC) dla wstępnej aktualizacji definicji na komputerach klienckich**  

     Wybierz **True** lub **tak** Jeśli program Configuration Manager do zainstalowania wyłącznie wstępną aktualizację definicji na komputerach klienckich. To ustawienie pomaga uniknąć niepotrzebnych połączeń sieciowych i ograniczyć przepustowość podczas wstępnej instalacji aktualizacji definicji.  

##  <a name="hardware-inventory"></a>Spis sprzętu  

-   **Maksymalny rozmiar niestandardowego pliku MIF (KB)**  

     Określ maksymalny rozmiar w kilobajtach niestandardowych plików formatu MIF (Management Information), które będą zebrane od klientów w cyklu wykonywania zapasów sprzętu. Pliki MIF o większym rozmiarze, spis sprzętu programu Configuration Manager nie będzie przetwarzał je. Można określić rozmiar od 1 do 5000 KB. Wartością domyślną jest 250 KB. To ustawienie nie wpływa na rozmiar standardowego pliku danych zapasów sprzętu.  

    > [!NOTE]  
    >  To ustawienie jest dostępne wyłącznie w domyślnych ustawieniach klienta.  

-   **Klasy zapasów sprzętu**  

     W programie Configuration Manager można rozszerzyć informacje o sprzęcie zbierane od klientów bez konieczności ręcznego modyfikowania pliku sms_def.mof. Wybierz **Ustaw klasy** Jeśli chcesz rozszerzyć zapasy sprzętu programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [Konfigurowanie spisu sprzętu w programie System Center Configuration Manager](../../../core/clients/manage/inventory/configure-hardware-inventory.md).  

-   **Zbierz pliki MIF**  

     To ustawienie umożliwia określenie, czy do zbierania plików MIF z klientów programu Configuration Manager podczas tworzenia spisu sprzętu.  

     Aby plik MIF został zebrany w ramach spisu sprzętu musi ona w prawidłowej lokalizacji na komputerze klienckim. Domyślnie pliki znajdują się w następujący sposób:  

    -   Pliki IDMIF powinny znajdować się w folderze Windows\System32\CCM\Inventory\Idmif.  

    -   Pliki NOIDMIF powinny znajdować się w folderze Windows\System32\CCM\Inventory\Noidmif.  

    > [!NOTE]  
    >  To ustawienie jest dostępne wyłącznie w domyślnych ustawieniach klienta.

-   **Maksymalne opóźnienie losowe**

    Zbiór informacji o sprzęcie jest wybierane przez maksymalnie cztery godziny, tak aby operacja nie została wykonana, jednocześnie na wszystkich klientów. Aby ograniczyć czas, w którym odbywa się operacji można ustawić maksymalne opóźnienie.      

##  <a name="metered-internet-connections"></a>Mierzonych połączeń internetowych  
 Można zarządzać sposób komputery klienckie systemu Windows 8 komunikacji z lokacji programu Configuration Manager, jeśli korzystają z mierzonych połączeń internetowych. Dostawcy Internetu czasami naliczają opłaty według ilości wysyłanych i odbieranych danych podczas taryfowego połączenia z Internetem.  

> [!NOTE]  
>  Skonfigurowane ustawienie klienta nie zostanie zastosowane na komputerach klienckich z systemem Windows 8 w następujących scenariuszach:  
>   
> -   Komputer korzysta z połączenia danych w roamingu: Klient programu Configuration Manager nie wykonuje żadnych zadań, które wymagają danych przekazywanych do lokacji programu Configuration Manager.  
> -   Właściwości połączenia sieciowego systemu Windows są skonfigurowane jako niemierzone: Klient programu Configuration Manager zachowuje się tak, jakby to niemierzone połączenie internetowe i transferuje dane do lokacji programu Configuration Manager.  

-   **Komunikacja z klientem w przypadku mierzonych połączeń internetowych**  

     Dla komputerów klienckich z systemem Windows 8 należy wybrać z listy rozwijanej jedną z następujących opcji:  

    -   **Zezwalaj na**: Cała komunikacja z klientem przez mierzone połączenie internetowe jest dozwolona, chyba że urządzenie klienckie korzysta z roamingu połączenie danych.  

    -   **Limit**: Przez mierzone połączenie internetowe może wyłącznie następująca komunikacja z klientem:  

        -   Pobieranie zasad klienta  

        -   Komunikaty o stanie klienta, które będą wysłane do lokacji  

        -   Żądania instalacji oprogramowania wynikające z korzystania z katalogu aplikacji  

        -   Wymagane wdrożenia (po osiągnięciu ostatecznego terminu instalacji)  

        > [!IMPORTANT]  
        >  Po zainicjowaniu przez użytkownika instalacji oprogramowania z poziomu Centrum oprogramowania lub katalogu aplikacji instalacje te będą zawsze dozwolone, niezależnie od ustawień mierzonego połączenia internetowego.  

         Po osiągnięciu limitu transferu danych mierzonego połączenia internetowego klient nie jest już próbuje nawiązać połączenia z lokacji programu Configuration Manager.  

    -   **Blok**: Klient programu Configuration Manager nie próbuje komunikować się z lokacji programu Configuration Manager po mierzonego połączenia internetowego. Jest to wartość domyślna.  

##  <a name="power-management"></a>Zarządzanie energią  

-   **Zezwalaj użytkownikom na wykluczanie swoich urządzeń z zarządzania zasilaniem**  

     Z listy rozwijanej wybierz **True** lub **tak** umożliwi użytkownikom programu Software Center wykluczenie ich komputera ze skonfigurowanych ustawień zarządzania energią.  

-   **Włącz serwer proxy wznawiania**  

     Wybierz opcję **Tak** , aby uzupełnić ustawienie funkcji Wake On LAN lokacji, jeżeli została skonfigurowana dla pakietów emisji pojedynczej.  

     Aby uzyskać więcej informacji o serwerze proxy wznawiania, zobacz [planowanie sposobu wznawiania działania klientów w programie System Center Configuration Manager](../../../core/clients/deploy/plan/plan-wake-up-clients.md).  

    > [!WARNING]  
    >  Nie należy włączać serwera proxy wznawiania w sieci produkcyjnej bez wcześniejszego zrozumienia sposobu jego działania i oceny w środowisku testowym.  

-   **Numer portu serwera proxy wznawiania (UDP)**  

     Należy zachować wartość domyślną numeru portu, który zarządzanych komputerach do wysyłania pakietów wznawiania do uśpionych komputerów. Można również zmienić numer na wybraną wartość.  

     Określony tutaj numer portu jest automatycznie konfigurowana dla klientów, którzy działa Zapora systemu Windows, korzystając z **wyjątek zapory systemu Windows dla serwera proxy wznawiania** opcji. Jeżeli na klientach działa inna zapora, należy skonfigurować ją ręcznie w celu zezwolenia na użycie numeru portu UDP określonego dla tego ustawienia.  

-   **Numer portu funkcji Wake On LAN (UDP)**  

     Należy zachować wartość domyślną 9, chyba że zmieniono numer portu Wake On LAN (UDP) na **porty** kartę witryny **właściwości**.  

    > [!IMPORTANT]  
    >  Ten numer musi być zgodny z wartością w oknie **Właściwości**lokacji. Po zmianie tego numeru w jednym miejscu, nie są automatycznie aktualizowane w innym miejscu.  

##  <a name="remote-tools"></a>Zdalne narzędzia  

-   **Włącz zdalne sterowanie na klientach** z opisem **Profile wyjątków zapory**  

     Wybierz, czy zdalnego sterowania programu Configuration Manager jest włączone dla wszystkich komputerów klienckich, które odbierają te ustawienia klienta. Wybierz **Konfiguruj** włączyć zdalne sterowanie. Opcjonalnie można skonfigurować ustawienia zapory, aby zezwolić na zdalne sterowanie do pracy na komputerach klienckich.  

     Zdalne sterowanie jest domyślnie wyłączone.  

    > [!IMPORTANT]  
    >  Jeżeli ustawienia zapory nie zostaną skonfigurowane, zdalne sterowanie może nie działać prawidłowo.  

-   **Użytkownicy mogą zmieniać zasady lub ustawienia powiadomień w programie Software Center**  

     Wybierz, czy użytkownicy mogą zmieniać opcje zdalnego sterowania z programu Software Center.  

-   **Zezwalaj na zdalne sterowanie komputerem nienadzorowanym**  

     Wybierz, czy administrator może używać zdalnego sterowania do dostęp do wylogowanego lub zablokowanego komputera klienckiego. Tylko zalogowanymi i odblokowanymi komputerami można sterować zdalnie, gdy to ustawienie jest wyłączone.  

-   **Monituj użytkownika o zezwolenie na zdalne sterowanie**  

     Wybierz, czy komputer kliencki pojawi się komunikat z pytaniem o zezwolenie użytkownika przed włączeniem sesji zdalnego sterowania.  

-   **Przyznaj uprawnienie do zdalnego sterowania lokalnej grupie administratorów**  

     Wybierz, czy Administratorzy lokalni na serwerze inicjującym połączenie zdalnego sterowania mogą nawiązywać sesje zdalnego sterowania na komputerach klienckich.  

-   **Dozwolony poziom dostępu**  

     Należy określić dozwolony poziom dostępu za pomocą zdalnego sterowania. Można wybrać jedną z następujących opcji:  

    -   Pełna kontrola  

    -   Wyświetl tylko  

    -   Brak  

-   **Dopuszczone podglądy**  

     Wybierz **Ustaw podglądy** otworzyć **Konfiguruj ustawienie klienta** okna dialogowego i określ nazwy użytkowników systemu Windows, którzy mogą nawiązywać sesje zdalnego sterowania z komputerami klienckimi.  

-   **Pokaż ikonę powiadomienia sesji na pasku zadań**  

     Wybierz tę opcję, aby ikona była wyświetlana na pasku zadań klienta komputerów w celu wskazania, że sesja zdalnego sterowania jest aktywna.  

-   **Pokaż pasek połączenia sesji**  

     Wybierz tę opcję, aby wyświetlić pasek połączenia sesji wysokiej widoczności na kliencie komputerów w celu wskazania, że sesja zdalnego sterowania jest aktywna.  

-   **Odtwórz dźwięk na kliencie**  

     Wybierz tę opcję, aby użyć dźwięku sygnalizującego, kiedy sesja zdalnego sterowania jest aktywna na komputerze klienckim. Dźwięk można odtworzyć po połączeniu lub rozłączeniu sesji albo odtwarzać go wielokrotnie podczas sesji.  

-   **Zarządzaj ustawieniami nieżądanej pomocy zdalnej**  

     Wybierz tę opcję, aby umożliwić programowi Configuration Manager Zarządzanie sesjami nieżądanej pomocy zdalnej.  

     W sesji nieżądanej pomocy zdalnej użytkownika na komputerze klienckim nie żądanie pomocy w zainicjowaniu sesji.  

-   **Zarządzaj ustawieniami pomocy zdalnej na żądanie**  

     Wybierz tę opcję, aby umożliwić programowi Configuration Manager Zarządzanie sesjami pomocy zdalnej na żądanie.  

     W ramach sesji Pomocy zdalnej na żądanie użytkownika na komputer kliencki wysłał żądanie do administratora o pomoc zdalną.  

-   **Poziom dostępu dla pomocy zdalnej**  

     Wybierz poziom dostępu przypisany do sesji Pomocy zdalnej, które są inicjowane w konsoli programu Configuration Manager.  

    > [!NOTE]  
    >  Użytkownik przy komputerze klienckim musi zawsze udzielić zezwolenia, aby można było rozpocząć sesję pomocy zdalnej.  

-   **Zarządzaj ustawieniami pulpitu zdalnego**  

     Wybierz tę opcję, aby umożliwić programowi Configuration Manager Zarządzanie sesjami pulpitu zdalnego dla komputerów.  

-   **Zezwalaj dopuszczonym podglądom na połączenie za pomocą programu Podłączanie pulpitu zdalnego**  

     Wybierz tę opcję, aby umożliwić użytkownikom określonych na liście dopuszczonych podglądów do dodania do grupy użytkowników lokalnych usług pulpitu zdalnego na komputerach klienckich.  

-   **Wymagaj uwierzytelniania na poziomie sieci na komputerach z systemem operacyjnym Windows Vista i nowszymi wersjami**  

     Wybierz tę bezpieczniejszą opcję, jeśli chcesz używać uwierzytelniania na poziomie sieci może nawiązywać połączenia pulpitu zdalnego z komputerów klienckich z systemem Windows Vista lub nowszy. Uwierzytelnianie na poziomie sieci wymaga początkowo mniejszej ilości zasobów na komputerze zdalnym ponieważ kończyło uwierzytelnianie użytkownika przed nawiązaniem połączenia pulpitu zdalnego. Ta metoda jest bezpieczniejsza, ponieważ może ułatwić ochronę komputera przed złośliwymi użytkownikami lub oprogramowaniem i zmniejsza ryzyko ataków typu „odmowa usługi”.  

## <a name="software-deployment"></a>Wdrażanie oprogramowania  

-   **Zaplanuj ponowną ocenę dla wdrożeń**  

     Skonfigurować harmonogram dla programu Configuration Manager ponownej oceny zasad wymagań dla wszystkich wdrożeń. Domyślna wartość to co 7 dni.  

    > [!IMPORTANT]  
    >  Zaleca się, że nie zmienisz tę wartość na mniejszą wartość niż domyślna. Które może negatywnie wpłynąć na wydajność Twojej sieci i komputerów klienckich.  

     Ta akcja z komputera klienckiego programu Configuration Manager może również inicjować, wybierając akcję **cykl oceny wdrażania aplikacji** z **akcje** na karcie **programu Configuration Manager** w Panelu sterowania.  

##  <a name="software-inventory"></a>Zapasy oprogramowania  

-   **Szczegóły raportowania spisu**  

     Należy określić poziom informacji o plikach umieszczanych w spisie. Można dodać do spisu szczegółowe informacje o pliku, szczegóły dotyczące produktu skojarzonego z plikiem lub wszystkie informacje o pliku.  

-   **Następujące typy plików do spisu**  

     Jeśli chcesz określić typy plików do spisu, wybierz **Ustaw typy** , a następnie skonfiguruj następujące opcje w **Konfiguruj ustawienie klienta** okno dialogowe:  

    > [!NOTE]  
    >  Jeśli kilka niestandardowych ustawień klienta są stosowane do komputera, spisu, która zwraca każde ustawienie zostanie scalony.  

    -   Wybierz **New** ikonę, aby dodać do spisu nowy typ pliku. Następnie określ następujące informacje w **właściwości zinwentaryzowanych plików** okno dialogowe:  

        -   **Nazwa**: Podaj nazwę pliku, który chcesz dodać do spisu. Można użyć * *\**  znaku oznaczającego dowolny ciąg tekstu i **?** oznaczającego pojedynczy znak. Na przykład, jeśli chcesz dodać do spisu wszystkie pliki z rozszerzeniem doc, należy określić nazwę pliku  **\*doc**.  

        -   **Lokalizacja**: Wybierz **ustawić** otworzyć **właściwości ścieżki** okno dialogowe. Można skonfigurować zapasy oprogramowania w celu wyszukania na dyskach twardych wszystkich klientów określonego pliku, określonej ścieżki (na przykład **C:\Folder**), albo wyszukaj określonej zmiennej (na przykład *% windir %*). Można także przeszukać wszystkie podfoldery w określonej ścieżce.  

        -   **Wyklucz pliki zaszyfrowane i skompresowane**: Po wybraniu tej opcji pliki skompresowane lub zaszyfrowane nie podlega ewidencjonowaniu.  

        -   **Wyklucz pliki w folderze systemu Windows**: Po wybraniu tej opcji nie podlega ewidencjonowaniu wszystkie pliki w folderze systemu Windows i jego podfolderach.  

    -   Wybierz **OK** zamknąć **właściwości zinwentaryzowanych plików** okno dialogowe.  

    -   Dodaj wszystkie pliki, które chcesz spisu, a następnie wybierz **OK** zamknąć **Konfiguruj ustawienie klienta** okno dialogowe.  

-   **Zbierz pliki**  

     Aby zebrać pliki z komputerów klienckich, należy wybrać **Ustaw pliki** , a następnie skonfiguruj następujące czynności:  

    > [!NOTE]  
    >  Jeśli kilka niestandardowych ustawień klienta są stosowane do komputera, spisu, która zwraca każde ustawienie zostanie scalony.  

    -   W **Konfiguruj ustawienie klienta** okno dialogowe Wybierz **New** ikonę, aby dodać plik do zebrania.  

    -   W oknie dialogowym **Właściwości zebranych plików** wprowadź następujące informacje:  

        -   **Nazwa**: Podaj nazwę pliku, który chcesz zebrać. Można użyć * *\**  znaku oznaczającego dowolny ciąg tekstu i **?** oznaczającego pojedynczy znak.  

        -   **Lokalizacja**: Wybierz **ustawić** otworzyć **właściwości ścieżki** okno dialogowe. Można skonfigurować zapasy oprogramowania w celu wyszukania na wszystkich dyskach twardych klienta dla pliku, który chcesz zebrać, określonej ścieżki (na przykład **C:\Folder**), albo wyszukaj określonej zmiennej (na przykład *% windir %*). Można także przeszukać wszystkie podfoldery w określonej ścieżce.  

        -   **Wyklucz pliki zaszyfrowane i skompresowane**: Po wybraniu tej opcji pliki skompresowane lub zaszyfrowane nie będą zbierane.  

        -   **Zatrzymaj zbieranie plików, gdy łączny rozmiar plików przekracza (KB)**: Określ rozmiar pliku (w kilobajtach), po przekroczeniu którego kolejne pliki określone w obszarze **nazwa** zostaną zebrane.  

          > [!NOTE]  
          >  Serwer lokacji zbiera pięć ostatnio zmienionych wersji zebranych plików i zapisuje je w  *&lt;katalogu instalacyjnego programu ConfigMgr\>*\Inboxes\Sinv.box\Filecol katalogu. Jeżeli plik nie został zmieniony od momentu ostatniego zebrania spisu oprogramowania, plik nie zostanie zebrany ponownie.  
          >   
          >  Spis oprogramowania nie są zbierane pliki większe niż 20 MB.  
          >   
          >  Wartość **maksymalny rozmiar wszystkich zebranych plików (KB)** w **Konfiguruj ustawienie klienta** okno dialogowe zawiera maksymalny rozmiar wszystkich zebranych plików. Po osiągnięciu tego rozmiaru zbieranie zostanie zatrzymane. Wszystkie już zebrane pliki są zachowywane i wysłane do serwera lokacji.  

          > [!IMPORTANT]
          >  Jeśli skonfigurowano zapasy oprogramowania w celu zebrania wielu dużych plików, może to negatywnie wpłynąć na wydajność sieci i serwera lokacji.  

        Aby uzyskać informacje o sposobie wyświetlania zebranych plików, zobacz [jak używać Eksploratora zasobów do wyświetlenia spisu oprogramowania System Center Configuration Manager](../../../core/clients/manage/inventory/use-resource-explorer-to-view-software-inventory.md).  

    -   Wybierz **OK** zamknąć **właściwości zebranych plików** okno dialogowe.  

    -   Dodaj wszystkie pliki, które chcesz zebrać, a następnie wybierz **OK** zamknąć **Konfiguruj ustawienie klienta** okno dialogowe.  

-   **Ustaw nazwy**  

     Podczas tworzenia spisu oprogramowania nazwy producentów i produktów są pobierane z informacji w nagłówku plików zainstalowanych na klientach w lokacji. Ponieważ te nazwy w informacjach w nagłówkach plików nie zawsze są standardowe, podczas wyświetlania informacji o spisie oprogramowania w programie Eksplorator zasobów lub wykonywania kwerend mogą zostać wyświetlone różne wersje tego samego producenta lub nazwy produktu. Jeśli chcesz ustandaryzować te wyświetlane nazwy, wybierz **Ustaw nazwy** , a następnie skonfiguruj następujące opcje w **Konfiguruj ustawienie klienta** okno dialogowe:  

    -   **Nazwa typu**: Zapasów oprogramowania zbiera informacje o producentach i produktach. Z listy rozwijanej wybierz, czy chcesz skonfigurować nazwy wyświetlane dla **producenta** lub **produktu**.  

    -   **Nazwa wyświetlana**: Określ nazwę wyświetlaną, którego chcesz używać zamiast nazw na **nazwy zinwentaryzowane** listy. Można wybrać **New** ikonę, aby określić nową nazwę wyświetlaną.  

    -   **Nazwy zinwentaryzowane**: Wybierz **nowy** ikonę, aby dodać nową zinwentaryzowaną nazwę, która zostanie zastąpiona w spisie oprogramowania przez nazwę wybraną w **Nazwa wyświetlana** listy. Można dodać kilka nazw, które zostaną zastąpione.  

##  <a name="software-updates"></a>Aktualizacje oprogramowania  

-   **Włącz aktualizacje oprogramowania na klientach**  

     To ustawienie umożliwia włączenie aktualizacji oprogramowania na klientach programu Configuration Manager. Gdy to ustawienie jest wyłączone, Configuration Manager usunie istniejące zasady wdrażania z klienta. Po ponownym włączeniu tego ustawienia klient pobierze bieżące zasady wdrażania.  

    > [!IMPORTANT]  
    >  Gdy to ustawienie jest wyłączone, ochrony dostępu do sieci zasady i ustawień zgodności korzystające z ustawienia urządzenia aktualizacji oprogramowania nie będzie już działać.  

-   **Harmonogram skanowania w poszukiwaniu aktualizacji oprogramowania**  

     To ustawienie umożliwia określenie częstotliwości inicjowania przez klienta skanowania w celu oceny zgodności aktualizacji oprogramowania. Skanowanie w celu oceny zgodności określa stan aktualizacji oprogramowania na kliencie (na przykład wymagane lub zainstalowane). Aby uzyskać więcej informacji na temat oceny zgodności, zobacz [oceny zgodności aktualizacji oprogramowania](../../../sum/understand/software-updates-introduction.md#BKMK_SUMCompliance).  

     Domyślnie używany jest prosty harmonogram i skanowania zgodności jest inicjowane co 7 dni. Można wybrać utworzenie harmonogramu niestandardowego w celu dokładnego określenia dnia i godziny rozpoczęcia, wybrać, czy ma być używany czas UTC czy lokalny i skonfigurować interwał powtarzania dla określonego dnia tygodnia.  

    > [!NOTE]  
    >  W przypadku określenia interwału krótszego niż 1 dzień, program Configuration Manager automatycznie domyślnie 1 dzień.  

    > [!WARNING]  
    >  Rzeczywista godzina uruchomienia na komputerach klienckich to godzina uruchomienia plus przypadkowy czas wynoszący maksymalnie 2 godziny. Zapobiega to inicjowaniu przez komputery klienckie jednoczesnego skanowania i łączenia się z usługami Windows Server Update Services (WSUS) na serwerze punktu aktualizacji oprogramowania aktywnego.  

-   **Zaplanuj ponowną ocenę wdrożenia**  

     To ustawienie umożliwia skonfigurowanie, jak często Agent klienta aktualizacji oprogramowania ponownie ocenia aktualizacje oprogramowania pod kątem stanu instalacji na komputerach klienckich programu Configuration Manager. Gdy zainstalowane wcześniej aktualizacje oprogramowania znajdują się już na komputerach klienckich i są nadal wymagane, są one ponownie.

     Harmonogram ponownej oceny wdrożenia należy dostosować zgodnie z zasadą firmową dotyczącą zgodności aktualizacji oprogramowania, czy użytkownicy mają możliwość odinstalowania aktualizacji oprogramowania i tak dalej. Należy pamiętać, że każdy cykl ponownej oceny wdrożenia powoduje niektórych działanie Procesora komputera klienta i sieci. Domyślnie używany jest prosty harmonogram, a skanowanie w celu ponownej oceny wdrożenia jest inicjowane co 7 dni.  

    > [!NOTE]  
    >  W przypadku określenia interwału krótszego niż 1 dzień, program Configuration Manager automatycznie domyślnie 1 dzień.  

-   **Po osiągnięciu ostatecznego terminu dowolnej aktualizacji oprogramowania zainstaluj wszystkie pozostałe wdrożenia aktualizacji oprogramowania z terminem wypadającym w danym czasie**  

     To ustawienie umożliwia zainstalowanie wszystkich aktualizacji oprogramowania w wymaganych wdrożeniach, których terminy wypadają w danym czasie. Po osiągnięciu terminu wymaganego oprogramowania wdrożenia aktualizacji, instalacja zostanie zainicjowana klientów pod kątem aktualizacji oprogramowania we wdrożeniu. To ustawienie określa, czy ma być dodatkowo inicjowana instalacja aktualizacji oprogramowania w innych wymaganych wdrożeniach, których termin wypada w określonym czasie.  

     To ustawienie umożliwia przyspieszenie instalacji wymaganych aktualizacji oprogramowania, potencjalne zwiększenie bezpieczeństwa, potencjalne zmniejszenie liczby wyświetlanych powiadomień oraz potencjalne zmniejszenie liczby ponownych uruchomień systemów na komputerach klienckich. Domyślnie to urządzenie nie jest włączone.  

-   **Okres czasu, w którym wszystkie oczekujące wdrożenia z terminem wypadającym w tym okresie także zostaną zainstalowane**  

     To ustawienie umożliwia określenie przedziału czasu dla poprzedniego ustawienia. Można wprowadzić wartość od 1 do 23 godzin oraz 1 do 365 dni. Domyślne ustawienie to 7 dni.  

-   **Włącz instalację pliki instalacji ekspresowej na klientach**

-   **Port używany do pobierania zawartości plików instalacji ekspresowej**

-   **Zezwalaj na zarządzanie Office 365 klienta ponownie** to ustawienie umożliwia włączenie zarządzania agenta klienta Office 365. Jeśli zostanie ustawiona wartość **tak**, pozwala na konfigurowanie ustawień instalacji usługi Office 365, pobierać pliki z pakietu Office sieci dostarczania zawartości (CDN) i wdrożyć pliki aplikacji w programie Configuration Manager.

##  <a name="user-and-device-affinity"></a>Koligacja użytkowników i urządzeń  

-   **Próg użycia dla koligacji użytkownika i urządzenia (minuty)**  

     Określ liczbę minut, zanim program Configuration Manager tworzy mapowanie koligacji urządzenia użytkownika.  

-   **Próg użycia dla koligacji użytkownika i urządzenia (dni)**  

     Określ liczbę dni, przez jaką jest mierzony próg koligacji na podstawie użycia.  

    > [!NOTE]  
    >  Na przykład jeśli **próg użycia koligacji urządzenia użytkownika (w minutach)** jest określony jako **60** minut i **próg użycia koligacji użytkownika i urządzenia (dni)** jest określony jako **5** dni, użytkownik musi używać urządzenia przez 60 minut w okresie 5 dni do automatycznego tworzenia koligacji urządzenia użytkownika.  

-   **Automatycznie konfiguruj koligację użytkownika i urządzenia na podstawie danych użycia**  

     Wybierz **True** lub **tak** umożliwia programowi Configuration Manager automatycznego utworzenia koligacji urządzenia na podstawie zebranych informacji użycia użytkowników.  

##  <a name="mobile-devices"></a>Urządzenia przenośne  

-   **Profil rejestracji urządzenia przenośnego**  

     Przed skonfigurowaniem tego ustawienia musisz wybrać opcję **Prawda** ustawienia **Zezwalaj użytkownikom na rejestrację urządzeń przenośnych**użytkownika urządzenia przenośnego. Następnie można wybrać **Ustaw profil** Aby określić profil rejestracji zawierający informacje o szablon certyfikatu do użycia podczas procesu rejestracji, lokację zawierającą punkt rejestracji i punkt proxy rejestracji oraz lokację, która ma zarządzać urządzeniem po wdrożeniu.  

    > [!IMPORTANT]  
    >  Upewnij się, że przed skonfigurowaniem tej opcji został skonfigurowany szablon certyfikatu, który ma być używany z rejestracją urządzenia przenośnego.  

##  <a name="enrollment"></a>Rejestrowanie  

-   **Profil rejestracji urządzenia przenośnego**  

     Przed skonfigurowaniem tego ustawienia musisz wybrać opcję **Tak** ustawienia **Zezwalaj użytkownikom na rejestrację urządzeń przenośnych i komputerów Mac**użytkownika rejestracji. Następnie można wybrać **Ustaw profil** Aby określić profil rejestracji zawierający informacje o szablon certyfikatu do użycia podczas procesu rejestracji, lokację zawierającą punkt rejestracji i punkt proxy rejestracji oraz lokację, która ma zarządzać urządzeniem po wdrożeniu.  

    > [!IMPORTANT]  
    >  Upewnij się, że przed skonfigurowaniem tej opcji został skonfigurowany szablon certyfikatu, który ma być używany z rejestracją urządzenia przenośnego lub rejestracją certyfikatu klienta na komputery Mac.  

## <a name="user-and-device-affinity"></a>Koligacja użytkowników i urządzeń  

-   **Zezwalaj użytkownikowi na definiowanie urządzeń podstawowych**  

     Określ, czy użytkownicy mogą identyfikować własne urządzenia podstawowe na **Moje urządzenia** kartę katalogu aplikacji.  

