---
title: Ustawienia klienta
titleSuffix: Configuration Manager
description: "Wybierz ustawienia klienta przy użyciu konsoli administracyjnej programu System Center Configuration Manager."
ms.custom: na
ms.date: 12/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f7560876-8084-4570-aeab-7fd44f4ba737
caps.latest.revision: "15"
caps.handback.revision: "0"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: fe6b3508b7d54dca1d80818c159cfd4b723f7986
ms.sourcegitcommit: f1535281b2c3fecff773b722c3f7590bf6ba10a0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/03/2018
---
# <a name="about-client-settings-in-system-center-configuration-manager"></a>Informacje o ustawieniach klienta w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersji current branch)*

Zarządzanie wszystkimi ustawieniami klienta w konsoli programu Configuration Manager z **ustawień klienta** w węźle **administracji** obszaru roboczego. Menedżer konfiguracji jest dostarczany z zestawem ustawień domyślnych. Zmiana domyślnych ustawień klienta, te ustawienia są stosowane do wszystkich klientów w hierarchii. Można również skonfigurować niestandardowe ustawienia klienta, które zastąpią domyślne ustawienia klienta po przypisaniu te ustawienia do kolekcji. Aby uzyskać więcej informacji, zobacz [sposób konfigurowania ustawień klienta](../../../core/clients/deploy/configure-client-settings.md).  
 

## <a name="background-intelligent-transfer-service"></a>Usługa inteligentnego transferu w tle  

-   **Ogranicz maksymalną przepustowość sieci dla transferów w tle wykonywanych przez usługę BITS**   </br>
   Gdy ta opcja jest **tak**, klienci używają funkcji ograniczania przepustowości usługi BITS. Aby skonfigurować inne ustawienia w tej grupie, należy włączyć to ustawienie. 

-   **Godzina rozpoczęcia okna ograniczenia przepustowości**   </br>
   Określ czas rozpoczęcia lokalnego oknie ograniczenia przepustowości usługi BITS.  

-   **Godzina zakończenia okna ograniczenia przepustowości**   </br>
   Określ czas zakończenia lokalnego oknie ograniczenia przepustowości usługi BITS. Jeśli równa **godzina rozpoczęcia okna ograniczenia przepustowości**, ograniczenia przepustowości usługi BITS jest zawsze włączona.  

-   **Maksymalna szybkość transferu w oknie ograniczenia przepustowości (Kb/s)** </br>
    Określa maksymalną szybkość transmisji używanego przez klientów podczas okna.  

-   **Zezwalaj na pobieranie usługi BITS poza oknem ograniczenia przepustowości**   </br>
   Zezwalaj klientom na użycie oddzielnych ustawień usługi BITS poza określonym oknem.  

-   **Maksymalna szybkość transferu poza oknem ograniczenia przepustowości (Kb/s)**   </br>
   Określ maksymalną szybkość transmisji używanego przez klientów poza oknem ograniczenia przepustowości usługi BITS.  



## <a name="client-cache-settings"></a>Ustawienia pamięci podręcznej klienta

- **Konfiguruj usługę BranchCache** </br>
  Użyj tego ustawienia, aby skonfigurować komputer kliencki [usługi Windows BranchCache](/sccm/core/plan-design/configs/support-for-windows-features-and-networks#branchcache). Aby zezwolić na buforowanie usługi BranchCache na kliencie, **Włącz usługę BranchCache** do **tak**.

    - **Włącz usługę BranchCache** </br>
    Włącza funkcję BranchCache na komputerach klienckich.

    - **Maksymalny rozmiar pamięci podręcznej usługi BranchCache (część procentowa dysku)** </br>
    Wartość procentowa dysku, który umożliwia usługi BranchCache do użycia. 

- **Skonfiguruj rozmiar pamięci podręcznej klienta** </br>
  Pamięci podręcznej klienta programu Configuration Manager na komputerach z systemem Windows są przechowywane tymczasowe pliki służące do instalacji aplikacji i programów. Jeśli ta opcja jest **nr**, domyślny rozmiar to 5,120 MB.</br>
    Wybierz **tak**, następnie określ:
    - **Maksymalny rozmiar pamięci podręcznej (MB)**
    - **Maksymalny rozmiar pamięci podręcznej (procent dysku)** </br>
    Rozmiar pamięci podręcznej klienta zostanie rozszerzony do maksymalnego rozmiaru w megabajtach (MB) lub wartość procentowa dysku, *ta wartość jest mniejsza*. 

- **Włącz klienta programu Configuration Manager w pełnej wersji systemu operacyjnego, aby udostępnić zawartość** </br>
    Umożliwia [elementu równorzędnego pamięci podręcznej](/sccm/core/plan-design/hierarchy/client-peer-cache) klientów programu Configuration Manager. Wybierz **tak**, następnie określić informacje o portach za pomocą której klient komunikuje się z komputerem równorzędnym. 
    - **Port początkowego rozgłaszania sieciowego** (domyślna 8004)
    - **Port pobierania zawartości z elementu równorzędnego** (domyślna 8003) </br>
    Menedżer konfiguracji automatycznie konfiguruje reguł zapory systemu Windows, aby zezwolić na ten ruch. Jeśli używasz innej zapory, należy ręcznie skonfigurować reguły zezwalające na ten ruch.




## <a name="client-policy"></a>Zasady klienta  

-   **Interwał sondowania zasad klienta (minuty)**  </br>
     Określa częstotliwość pobierania zasad klienta przez następujących klientów programu Configuration Manager:  
      -   Komputery z systemem Windows (na przykład komputery stacjonarne, serwery, komputery przenośne)  
      -   Urządzenia przenośne, które rejestruje programu Configuration Manager  
      -   Komputery Mac  
      -   Komputery z systemem Linux lub UNIX  

-   **Włącz zasady użytkownika na klientach**   </br>
   Po ustawieniu tej opcji **tak**i użyj [odnajdywania użytkownika usługi](../../../core/servers/deploy/configure/about-discovery-methods.md#bkmk_aboutUser), następnie klienci odbierają aplikacje i programy przeznaczone dla zalogowanego użytkownika.  

    Katalog aplikacji otrzymuje listę oprogramowania dostępnego dla użytkowników z serwera lokacji. W związku z tym to ustawienie nie ma być **tak** dla użytkowników wyświetlić aplikacje i zażądać ich z katalogu aplikacji. Jeśli to ustawienie jest **nr**, użytkownicy korzystają z katalogu aplikacji nie będą działać następujące zachowania:  

      -   Użytkownicy nie mogą instalować aplikacji widocznych w wykazie aplikacji.  

      -   Użytkownicy nie widzą powiadomień dotyczących ich żądań zatwierdzenia aplikacji. Zamiast tego muszą odświeżyć katalog aplikacji i sprawdzić stan zatwierdzenia.  

      -   Użytkownicy nie otrzymywali poprawek i aktualizacji aplikacji, które są publikowane w katalogu aplikacji. Użytkownicy widzą zmiany informacji o aplikacjach w katalogu aplikacji.  

      -   Po usunięciu wdrożenia aplikacji, po zainstalowaniu klienta aplikacji z katalogu aplikacji, klienci będą sprawdzać, czy aplikacja jest zainstalowana na maksymalnie dwa dni.  

    Ponadto, gdy to ustawienie jest **nr**, użytkownicy nie otrzymywali wymaganych aplikacji wdrażanych dla użytkowników. Użytkownicy również nie mają inne zadania zarządzania w zasadach użytkownika.  

    To ustawienie dotyczy użytkowników, gdy komputer będzie połączony z siecią intranet lub Internetem. Musi to być **tak** Jeśli chcesz również włączyć zasady użytkownika w Internecie.  

-   **Włącz żądania dotyczące zasad użytkownika od klientów internetowych**   </br>
   Skonfiguruj to ustawienie, aby **tak** użytkownikom będą otrzymywali zasady użytkownika na komputerach opartych na Internet. Również należy zastosować następujące wymagania:  

      -   Klienta i lokację skonfigurowano do internetowego zarządzania

      -   **Włącz zasady użytkownika na klientach** jest ustawienie **tak**  

      -   Punkt zarządzania internetowego pomyślnie uwierzytelnił użytkownika za pomocą uwierzytelniania systemu Windows (Kerberos lub NTLM)  

       Jeśli zostanie wybrana opcja jako **nr**, lub wszelkie poprzednie wymagania nie są spełnione, a następnie komputer połączony z Internetem tylko otrzyma zasady komputera. Przy takim scenariuszu użytkownicy mogą nadal oglądać i instalować aplikacje oraz zażądać ich z internetowego katalogu aplikacji. Jeśli to ustawienie jest **nr**, ale **Włącz zasady użytkownika na klientach** jest **tak**, użytkownicy nie otrzymywali zasad użytkownika do momentu komputer jest połączony z intranetem.  

       Aby uzyskać więcej informacji na temat zarządzania klientami przez Internet, zobacz [uwagi dotyczące komunikacji klientów z Internetu lub niezaufanego lasu](../../../core/plan-design/hierarchy/communications-between-endpoints.md#BKMK_clientspan).  

      > [!NOTE]  
      >  Żądania zatwierdzenia aplikacji od użytkowników nie wymagają zasad użytkownika ani uwierzytelnienia użytkownika.  


## <a name="cloud-services"></a>Usługi w chmurze

-   **Zezwalaj na dostęp do punktu dystrybucji w chmurze** </br>
    Skonfiguruj to ustawienie, aby **tak** dla klientów w celu uzyskania zawartości z punktu dystrybucji chmury. To ustawienie nie wymaga urządzeń internetowych.

-    **Automatycznego rejestrowania nowych urządzeń przyłączonych do domeny systemu Windows 10 w usłudze Azure Active Directory** </br> Po skonfigurowaniu usługi Azure Active Directory do obsługi sprzężenia hybrydowe programu Configuration Manager konfiguruje urządzenia z systemem Windows 10 dla tej funkcji. Aby uzyskać więcej informacji, zobacz [jak do skonfigurowania hybrydowego przyłączonych do usługi Azure Active Directory urządzeń](https://docs.microsoft.com/azure/active-directory/device-management-hybrid-azuread-joined-devices-setup).

-   **Umożliwia klientom używać bramy zarządzania chmury** </br>
    Domyślnie używają dostępne wszystkich klientów mobilnych Internet [brama zarządzania chmury](/sccm/core/clients/manage/plan-cloud-management-gateway). Kiedy należy skonfigurować to ustawienie, aby przykładem **nr** to zakres użycia usługi, na przykład podczas projektu pilotażowego lub w celu ograniczenia kosztów.



##  <a name="compliance-settings"></a>Ustawienia zgodności  

-   **Włącz ocenę zgodności na klientach** </br>
    Skonfiguruj to ustawienie, aby **tak** skonfigurować inne ustawienia w tej grupie.
 
-   **Zaplanuj ocenę zgodności**   </br>
     Kliknij przycisk **harmonogram** Aby utworzyć domyślny harmonogram dla konfiguracji wdrożenia linii bazowej. Ta wartość jest można skonfigurować dla każdej podstawy w **wdrażanie podstawy konfiguracji** okno dialogowe.  

-   **Włącz dane użytkownika i profile**   </br>
     Wybierz **tak** Jeśli chcesz wdrożyć [dane użytkownika i profile](../../../compliance/deploy-use/create-user-data-and-profiles-configuration-items.md) elementów konfiguracji.



## <a name="computer-agent"></a>Agent komputera  
-   Powiadomienia użytkowników w celu dokonania wymaganych wdrożeń </br>
    Aby uzyskać więcej informacji na temat następujących ustawień, zobacz [powiadomienia użytkowników w celu dokonania wymaganych wdrożeń](/sccm/apps/deploy-use/deploy-applications#user-notifications-for-required-deployments):
    -   **Termin ostateczny wdrożenia powyżej 24 godzin, Przypominaj użytkownikowi co (godziny)**
    -   **Wdrożenie termin ostateczny mniej niż 24 godziny, Przypominaj użytkownikowi co (godziny)**  </br>
    -   **Wdrożenia ostatecznego terminu wdrożenia poniżej 1 godziny, Przypominaj użytkownikowi co (minuty)**  </br>

-   **Domyślny punkt witryny sieci Web katalogu aplikacji**   </br>
     Configuration Manager używa tego ustawienia, aby łączyć użytkowników z katalogiem aplikacji w Centrum oprogramowania. Kliknij przycisk **witryny sieci Web zestawu** umożliwia określenie serwera obsługującego punkt witryny sieci Web katalogu aplikacji. Wprowadź jego nazwę NetBIOS lub nazwę FQDN, automatyczne wykrywanie lub określ adres URL wdrożeń dostosowanych. W większości przypadków najlepszym wyborem będzie automatyczne wykrywanie, które ma następujące zalety:  

    -   Jeśli witryna ma punkt witryny sieci Web katalogu aplikacji, następnie klienci automatycznie otrzymują punkt witryny sieci Web katalogu aplikacji z ich lokacji.  

    -   Klient preferuje tylko HTTP serwery punktów witryny sieci Web katalogu aplikacji z obsługą protokołu HTTPS w sieci intranet. Ta funkcja pomaga w ochronie przed serwerami nieautoryzowanymi.

    -   Punkt zarządzania zapewnia Klienci internetowi punkt witryny sieci Web katalogu aplikacji internetowych. Punkt zarządzania zapewnia klienci intranetowi punkt witryny sieci Web katalogu aplikacji opartych na sieci intranet.  

     Automatyczne wykrywanie nie gwarantuje, że klienci otrzymają najbliższy punkt witryny sieci Web katalogu aplikacji. Użytkownik może zrezygnować z funkcji **Wykryj automatycznie** z następujących przyczyn:  

     -   Użytkownik chce ręcznie skonfigurować najbliższy serwer dla klientów lub uniemożliwić klientom łączenie się z serwerem przez wolne połączenie sieciowe.  

     -   Użytkownik chce kontrolować, którzy klienci łączą się z którym serwerem. Ta konfiguracja może być do testowania wydajności lub z przyczyn biznesowych.  

     -   Nie chcesz czekać do 25 godzin lub na zmianę sieci, aby klienci mogli używać innej witryny sieci Web katalogu aplikacji punktu.  

     Jeśli punkt witryny sieci Web katalogu aplikacji należy określić zamiast używać automatycznego wykrywania, określ nazwę NetBIOS zamiast intranetową nazwę FQDN. Ta konfiguracja ogranicza prawdopodobieństwo, że przeglądarka sieci web monituje użytkowników o poświadczenia podczas uzyskiwania dostępu do katalogu aplikacji opartych na sieci intranet. Aby korzystać z nazwy NetBIOS, muszą być spełnione następujące warunki:  

     -   Nazwa NetBIOS została określona we właściwościach punktu witryny sieci Web katalogu aplikacji.  

     -   Korzystanie z usługi WINS lub wszyscy klienci znajdują się w tej samej domenie co punkt witryny sieci Web katalogu aplikacji.  

     -   Skonfiguruj punkt witryny sieci Web katalogu aplikacji dla połączeń klienckich HTTP, lub skonfigurować serwer do obsługi protokołu HTTPS i certyfikatu serwera sieci web ma nazwę NetBIOS.  

     Zwykle użytkownicy są monitowani o podanie poświadczeń, gdy adres URL ma nazwę FQDN, ale nie w przypadku, gdy adres URL jest nazwą NetBIOS. Monit będzie wyświetlany zawsze wtedy, gdy użytkownicy będą się łączyć z Internetu, ponieważ to połączenie musi korzystać z internetowej nazwy FQDN. Przy użyciu klienta internetowego i przeglądarki sieci web monituje użytkowników o poświadczenia, upewnij się, że punkt witryny sieci Web katalogu aplikacji połączenie się z kontrolerem domeny dla konta użytkownika. Ta konfiguracja umożliwia użytkownikom uwierzytelnianie przy użyciu protokołu Kerberos.  

    > [!NOTE]  
    >  Opis działania automatycznego wykrywania:  
    >   
    >  Klient wysyła żądanie lokalizacji usługi do punktu zarządzania. Jeśli w tej samej lokacji, w której znajduje się klient, istnieje punkt witryny sieci Web katalogu aplikacji, serwer zostanie przekazany klientowi jako serwer, który ma być wykorzystywany jako serwer katalogu aplikacji. Gdy więcej niż jeden punkt witryny sieci Web katalogu aplikacji jest dostępna w lokacji, z włączonym protokołem HTTPS serwera mają pierwszeństwo przed serwerem, który nie jest włączony dla protokołu HTTPS. Po powyższym filtrowaniu wszyscy klienci otrzymają jeden z serwerów, które ma być używana jako katalog aplikacji; Menedżer konfiguracji nie równoważy obciążenia między wieloma serwerami. Gdy lokacja klienta nie ma punkt witryny sieci Web katalogu aplikacji, punkt zarządzania zwróci w sposób niedeterministyczny punkt witryny sieci Web katalogu aplikacji z hierarchii.  
    >   
    >  Dla klientów sieci intranet Jeśli konfigurujesz punkt witryny sieci Web katalogu aplikacji przy użyciu nazwy NetBIOS dla adresu URL katalogu aplikacji, punkt zarządzania zapewnia klientów tę nazwę NetBIOS zamiast intranetową nazwę FQDN. Dla klientów internetowych punkt zarządzania zapewnia internetowej nazwy FQDN tylko do klienta.  
    >   
    >  Klient wysyła to żądanie lokalizacji usługi co 25 godzin lub po wykryciu zmiany sieci. Na przykład jeśli klient zostanie przeniesiony z sieci intranet do Internetu, a klient zlokalizuje punkt zarządzania internetowego, internetowy punkt zarządzania zapewnia serwerów punktu witryny sieci Web katalogu aplikacji internetowych do klientów.  

-   **Dodaj domyślną witrynę sieci Web katalogu aplikacji do strefy Zaufane witryny programu Internet Explorer**   </br>
     Jeśli ta opcja jest **tak**, klient automatycznie dodaje bieżący adres URL witryny sieci Web katalogu aplikacji domyślne do strefy Zaufane witryny programu Internet Explorer.  

     To ustawienie zapewnia, że tryb chroniony programu Internet Explorer jest wyłączony. Jeśli tryb chroniony jest włączony, klient programu Configuration Manager nie może być mógł instalować aplikacji z katalogu aplikacji. Domyślnie strefa Zaufane witryny obsługuje również logowanie użytkownika do katalogu aplikacji, co wymaga uwierzytelnienia systemu Windows.  

     Jeśli opuścisz tę opcję **nr**, klientów programu Configuration Manager nie można instalować aplikacji z katalogu aplikacji. Alternatywną metodą jest konfigurowania tych ustawień programu Internet Explorer w innej strefie dla adresu URL katalogu aplikacji używanego przez klientów.  

    > [!NOTE]  
    >  Zawsze, gdy programu Configuration Manager dodaje domyślny katalog aplikacji do strefy Zaufane witryny, programu Configuration Manager spowoduje usunięcie wszelkich poprzednio dodany adres URL katalogu aplikacji.  
    >   
    >  Jeśli adres URL został już określony w jednej ze stref zabezpieczeń, programu Configuration Manager nie może dodać adresu URL. W tym scenariuszu należy usunąć adres URL z innej strefy lub ręcznie skonfigurować wymagane ustawienia programu Internet Explorer.  

-   **Pozwól na uruchamianie aplikacji Silverlight w trybie podwyższonego zaufania**   </br>
     To ustawienie musi być **tak** użytkownikom korzystania z katalogu aplikacji.  

     Zmiana tego ustawienia będzie wprowadzona po kolejnym załadowaniu przeglądarki lub odświeżeniu obecnie otwartego okna przeglądarki przez użytkowników.  

     Aby uzyskać więcej informacji o tym ustawieniu, zobacz [certyfikatów dla programu Microsoft Silverlight 5 i tryb podwyższonego zaufania wymagany przez katalog aplikacji](../../../apps/plan-design/security-and-privacy-for-application-management.md#BKMK_CertificatesSilverlight5).  

-   **Nazwa organizacji wyświetlana w Centrum oprogramowania**   </br>
     Wpisz nazwę wyświetlaną użytkownikom w Centrum oprogramowania. Te informacje o znakowaniu ułatwiają użytkownikom zidentyfikowanie tej aplikacji jako pochodzącej z zaufanego źródła.  

-   **Użyj nowego Centrum oprogramowania**   </br>
     Jeśli skonfigurujesz to ustawienie klienta **tak**, a następnie wszystkie komputery klienckie używają nowego centrum oprogramowania. Program Software Center zawiera aplikacje dostępne dla użytkowników, które były wcześniej dostępne tylko w katalogu aplikacji. Katalog aplikacji wymaga programu Silverlight, która nie jest wymagane w przypadku nowego centrum oprogramowania.   

     Punkt witryny sieci Web katalogu aplikacji i usług sieci web katalogu aplikacji punktu systemu lokacji, które role są nadal wymagane dla aplikacje dostępne dla użytkowników, które mają być widoczne w Centrum oprogramowania.  

     Aby uzyskać więcej informacji, zobacz [planowanie i Konfigurowanie zarządzania aplikacjami](../../../apps/plan-design/plan-for-and-configure-application-management.md).  

-   **Włącz komunikację z usługą zaświadczania o kondycji**  </br>
    Skonfiguruj to ustawienie, aby **tak** dla urządzeń z systemem Windows 10 do użycia [zaświadczania o kondycji](/sccm/core/servers/manage/health-attestation). Gdy to ustawienie jest włączone, poniższe ustawienie jest również dostępny do konfiguracji.

    -   **Użyj lokalnej usługi zaświadczania o kondycji** </br>
        Skonfiguruj to ustawienie, aby **tak** urządzeń przy użyciu usługi lokalnej. Skonfiguruj to ustawienie, aby **nr** dla urządzeń, aby używać usług chmurowych firmy Microsoft.  

-   **Uprawnienia do instalacji**   </br>
    > [!WARNING]  
    >  To ustawienie dotyczy katalogu aplikacji i Centrum oprogramowania. To ustawienie nie ma żadnego efektu, jeśli użytkownicy korzystają z portalu firmy.  

     Konfigurowanie sposobu inicjowania instalacji oprogramowania, aktualizacji oprogramowania oraz sekwencji zadań przez użytkowników:  

    -   **Wszyscy użytkownicy**: Użytkownicy z dowolnymi uprawnieniami oprócz gościa uprawnień  

    -   **Tylko Administratorzy**: Użytkownicy muszą być członkiem lokalnej grupy administratorów  

    -   **Tylko administratorzy i użytkownicy podstawowi**: Użytkownicy muszą być członkiem lokalnej grupy administratorów lub użytkownikiem podstawowym komputera  

    -   **Użytkownicy nie**: Użytkownicy zalogowani na komputerze klienckim nie mogą inicjować instalację oprogramowania, aktualizacji oprogramowania i sekwencji zadań. Wdrożenia wymagane dla komputera są zawsze instalować w terminie ostatecznym. Użytkownicy nie mogą inicjować instalację oprogramowania z katalogu aplikacji lub Centrum oprogramowania.  

-   **Zawieś wprowadzanie numeru PIN funkcji BitLocker przy ponownym uruchomieniu**  </br>
     Jeśli komputery wymagają wprowadzania numeru PIN funkcji BitLocker, ta opcja pomija konieczność podania numeru PIN, po ponownym uruchomieniu komputera po zainstalowaniu oprogramowania.  

    -   **Zawsze**: Configuration Manager tymczasowo zawiesi funkcji BitLocker po zainstalowaniu oprogramowania wymagającego ponownego uruchomienia i zainicjował ponowne uruchomienie komputera. To ustawienie ma zastosowanie tylko do ponownego uruchomienia komputera zainicjowanych przez program Configuration Manager. To ustawienie nie wstrzymuje wymagania podania numeru PIN funkcji BitLocker po ponownym uruchomieniu komputera przez użytkownika. Wymaganie wprowadzania numeru PIN funkcji BitLocker zostanie wznowione po uruchomieniu systemu Windows.

    -   **Nigdy nie**: Menedżer konfiguracji nie zawiesił funkcji BitLocker przy następnym uruchomieniu komputera po zainstalowaniu oprogramowania wymagającego ponownego uruchomienia. Przy takim scenariuszu instalowanie oprogramowania nie zostanie zakończone przed wprowadzeniem numeru PIN przez użytkownika w celu ukończenia standardowego procesu uruchamiania i załadowania systemu Windows.

-   **Wdrażanie aplikacji oraz aktualizowanie oprogramowania jest zarządzane przez dodatkowe oprogramowanie**  </br>
     Tę opcję należy włączyć tylko po spełnieniu jednego z następujących warunków:  

    -   Użytkownik korzysta z rozwiązania dostawcy wymagającego, aby to ustawienie było włączone.  

    -   Korzystając z programu Configuration Manager zestaw software development kit (SDK) w celu zarządzania powiadomieniami agentem klienta i instalacji aplikacji i aktualizacji oprogramowania.  

    > [!WARNING]  
    >  Jeśli wybierzesz tę opcję, jeśli żadna z tych warunków zastosować, nie można zainstalować klienta aktualizacji oprogramowania i wymaganych aplikacji. To ustawienie nie uniemożliwić użytkownikom instalowanie aplikacji z katalogu aplikacji lub pakietów, programów i sekwencji zadań instalacji.  

-   **Zasady wykonywania programu PowerShell**  </br>
     Skonfiguruj sposób klientów programu Configuration Manager może uruchamiać skrypty programu Windows PowerShell. Skrypty te są często używane do wykrywania w elementach konfiguracji ustawień zgodności. Mogą być również wysyłane w ramach wdrożenia jako skrypty standardowe.  

    -   **Obejście**: Klient programu Configuration Manager pomija konfigurację programu Windows PowerShell na komputerze klienckim, co umożliwia uruchamianie niepodpisanych skryptów.  

    -   **Ograniczone**: Klient programu Configuration Manager korzysta z bieżącej konfiguracji środowiska Windows PowerShell na komputerze klienckim. Ta konfiguracja Określa, czy można uruchamiać niepodpisane skrypty.  

    -   **Wszystko podpisane**: Klient programu Configuration Manager uruchamia skrypty tylko wtedy, gdy podpisała ich zaufanego wydawcę. To ograniczenie obowiązuje niezależnie od bieżącej konfiguracji programu Windows PowerShell na komputerze klienckim.  

     Ta opcja wymaga co najmniej programu Windows PowerShell w wersji 2.0. Wartość domyślna to **wszystko podpisane**.  

    > [!TIP]  
    >  Jeśli nie ze względu na to ustawienie klienta uruchomienie niepodpisanych skryptów, program Configuration Manager zaraportuje ten błąd w następujący sposób:  
    >   
    > -   **Monitorowanie** w obszarze roboczym w konsoli wyświetlane identyfikator błąd stanu wdrożenia **0x87D00327** i opis **skrypt nie jest podpisany.**  
    > -   Raporty zawierają typ błędu **błąd odnajdywania**, a następnie albo kod błędu **0x87D00327** i opis **skrypt nie jest podpisany**, lub kod błędu  **0x87D00320** i opis **host skryptów nie został jeszcze zainstalowany**. Przykładowy raport jest **szczegóły błędów elementów konfiguracji w linii bazowej konfiguracji dla zasobu**.  
    > -   **DcmWmiProvider.log** pliku wyświetli komunikat **skrypt nie jest podpisany (błąd: 87D 00327; Źródło: CCM)**.  

-   **Pokaż powiadomienia o nowych wdrożeniach**  </br>
     Wybierz **tak** powiadomienia w przypadku wdrożeń dostępnych mniej niż tydzień mają być wyświetlane.  Ten komunikat jest wyświetlany zawsze, gdy agent klienta uruchamia.

-   **Wyłącz losowe generowanie terminu ostatecznego**  </br>
     Po upływie ostatecznego terminu wdrożenia to ustawienie określa, czy klient stosuje maksymalnie dwugodzinne opóźnienie aktywacji w celu zainstalowania wymaganych aktualizacji oprogramowania. Opóźnienie aktywacji jest domyślnie wyłączone.  

     W scenariuszach infrastruktury pulpitu wirtualnego (VDI) to opóźnienie pomaga w rozłożeniu przetwarzania procesora CPU i transfer danych do komputera hosta o wiele maszyn wirtualnych. Nawet wtedy, gdy infrastruktura VDI nie jest używana, wielu klientów instalowanie te same aktualizacje, w tym samym czasie może to zwiększyć użycie procesora CPU na serwerze lokacji. To zachowanie można również spowolnić punkty dystrybucji i znacznie zmniejszyć dostępną przepustowość sieci.  

     Jeśli klienci muszą zostać zainstalowane wymagane aktualizacje oprogramowania w terminie ostatecznym wdrożenia bez opóźnień, a następnie skonfiguruj to ustawienie, aby **tak**. 

-   **Okres prolongaty wymuszania po wdrożenia terminu wdrożenia (godziny)** </br>
     Jeśli chcesz umożliwić użytkownikom więcej czasu, aby zainstalować wymaganej aplikacji lub wdrożenia aktualizacji oprogramowania po upływie terminu, należy skonfigurować to ustawienie, aby **tak**. Tego okresu prolongaty jest wyłączona na dłuższy czas komputera, a użytkownik chce zainstalować wielu aplikacji lub wdrożenia aktualizacji. Na przykład jeśli użytkownik zwraca z urlopu i oczekuje na długi czas podczas instalacji klienta wdrożeń zaległe aplikacji. 

     Ustaw okres prolongaty 1 do 120 godzin. Użyj tego ustawienia, oraz właściwość wdrożenia **Opóźnij wymuszenie dotyczące tego wdrożenia zgodnie z preferencjami użytkownika**. Aby uzyskać więcej informacji, zobacz [wdrażania aplikacji](/sccm/apps/deploy-use/deploy-applications).



##  <a name="computer-restart"></a>Ponowne uruchomienie komputera  
 Następujące ustawienia musi być krótszy czas trwania od najkrótszego okna obsługi zastosowane do komputera.  

 Aby uzyskać więcej informacji o korzystaniu z okien obsługi, zobacz [Używanie okien obsługi w programie System Center Configuration Manager](../../../core/clients/manage/collections/use-maintenance-windows.md).  

-   **Wyświetl tymczasowe powiadomienie dla użytkownika, określające czas przed wylogowaniem lub komputer uruchamia ponownie (w minutach)**
-   **Wyświetl okno dialogowe, którego użytkownik nie może zamknąć, wyświetlające odliczanie przed wylogowaniem użytkownika lub ponownego uruchomienia komputera (minuty)**



##  <a name="endpoint-protection"></a>Program Endpoint Protection  
>  [!Tip]   
> Oprócz poniższych informacji, można znaleźć dodatkowe informacje dotyczące korzystania z ustawienia klienta programu Endpoint Protection [przykładowy scenariusz: Używanie programu System Center Endpoint Protection do ochrony komputerów przed złośliwym oprogramowaniem w programie System Center Configuration Manager](/sccm/protect/deploy-use/scenarios-endpoint-protection).

-   **Zarządzanie klientem programu Endpoint Protection na komputerach klienckich**  </br>
     Wybierz **tak** Jeśli chcesz zarządzać istniejącymi klientami programu Endpoint Protection i usługi Windows Defender na komputerach w hierarchii.  

     Wybierz tę opcję, jeśli użytkownik zainstalował już klienta programu Endpoint Protection i chce możesz nim zarządzać za pomocą programu Configuration Manager.  Ta instalacja oddzielne obejmuje proces przy użyciu skryptu przy użyciu Menedżera konfiguracji aplikacji lub pakietów i programów.

-   **Zainstaluj klienta programu Endpoint Protection na komputerach klienckich**   </br>
     Wybierz **tak** Aby zainstalować i włączyć klienta programu Endpoint Protection na komputerach klienckich nie został jeszcze uruchomiony klient.  

    > [!NOTE]  
    >  Jeśli jest już zainstalowany klient programu Endpoint Protection, wybierając **nr** nie powoduje odinstalowania klienta programu Endpoint Protection. Aby odinstalować klienta programu Endpoint Protection, **klienta zarządzania Endpoint Protection na komputerach klienckich** ustawienia klienta dotyczącego **nr**. Następnie należy wdrożyć pakiet i program, aby odinstalować klienta programu Endpoint Protection.  

-   **Automatycznie usuwaj wcześniej zainstalowane ochrony przed złośliwym oprogramowaniem, przed zainstalowaniem programu Endpoint Protection** </br>
    Skonfiguruj to ustawienie, aby **tak** dla klienta programu Endpoint Protection spróbować odinstalować aplikacje innych ochrony przed złośliwym oprogramowaniem. Wielu klientów ochrony przed złośliwym kodem na tym samym urządzeniu mogą występować konflikty i wpływać na wydajność systemu.

-   **Zezwalaj klienta programu Endpoint Protection instalacji oraz jego ponowne uruchamianie poza oknami obsługi. Okna obsługi muszą mieć przynajmniej 30 minut dla instalacji klienta** </br>
    Skonfiguruj to ustawienie, aby **tak** zastąpić zachowania typowej instalacji z okien obsługi. To ustawienie spełnia wymagania biznesowe priorytetu konserwacji systemu ze względów bezpieczeństwa. 

-   **W przypadku urządzeń Windows Embedded z filtrami zapisu należy zatwierdzić instalację klienta programu Endpoint Protection (wymaga ponownego uruchomienia)**  </br>
     Wybierz **tak** wyłączyć filtr zapisu na urządzeniu Windows Embedded, a następnie ponownie uruchomić urządzenie. Ta akcja zatwierdzenie instalacji na urządzeniu.  

     Jeśli skonfigurujesz to ustawienie, aby **nr**, a następnie klient jest instalowany na tymczasowej nakładce, która usuwa po ponownym uruchomieniu urządzenia. W tym scenariuszu klient programu Endpoint Protection nie pełni instaluje aż inna instalacja zatwierdza zmiany na urządzeniu. Ta konfiguracja jest ustawieniem domyślnym.  

-   **Pomiń wszystkie wymagane ponowne uruchomienie komputera po zainstalowaniu klienta programu Endpoint Protection**  </br>
     Wybierz **tak** pominąć ponowne uruchomienie komputera, w razie potrzeby po zainstalowaniu klienta programu Endpoint Protection.  

    > [!IMPORTANT]  
    >  Jeśli klient programu Endpoint Protection wymaga ponownego uruchomienia komputera, a to ustawienie jest **nr**, następnie komputer zostanie ponownie uruchomiony niezależnie od skonfigurowanych okien obsługi.  

-   **Dozwolony okres czasu, użytkownicy mogą odłożyć ponowne uruchomienie w celu ukończenia instalacji programu Endpoint Protection (godziny)**  </br>
     Jeśli konieczne jest ponowne uruchomienie komputera, po zainstalowaniu klienta programu Endpoint Protection, to ustawienie określa liczbę godzin, który użytkownicy mogą odłożyć ponowne uruchomienie. To ustawienie wymaga **Pomiń wszystkie wymagane ponowne uruchomienie komputera po zainstalowaniu klienta programu Endpoint Protection** jest ustawienie **nr**.  

-   **Wyłącz źródła alternatywne (takie jak Microsoft Windows Update, Microsoft Windows Server Update Services lub udziały UNC) dla wstępnej aktualizacji definicji na komputerach klienckich**  </br>
     Wybierz **tak** Jeśli program Configuration Manager do zainstalowania wyłącznie wstępną aktualizację definicji na komputerach klienckich. To ustawienie pomaga uniknąć niepotrzebnych połączeń sieciowych i ograniczyć przepustowość podczas wstępnej instalacji aktualizacji definicji.  



##  <a name="enrollment"></a>Rejestrowanie

-   **Interwał sondowania dla starszych klientów urządzeń przenośnych** </br>
    Kliknij przycisk **Ustaw interwał** Aby określić czas, w minutach lub godzinach, które starszych urządzeń przenośnych sondowania zasad. Urządzenia te obejmują platformach, na przykład systemu Windows CE, Mac OS X i Unix lub Linux.

-   **Interwał sondowania dla nowoczesnych urządzeń (w minutach)** </br>
    Wprowadź liczbę minut nowoczesnych urządzeń sondowania zasad. To ustawienie jest dla urządzeń z systemem Windows 10 zarządzanych za pomocą lokalnego zarządzania urządzeniami przenośnymi.

-   **Zezwalaj użytkownikom na rejestrację urządzeń przenośnych i komputerów Mac.** </br>
    Aby włączyć oparta na użytkowniku rejestracji starszych urządzeń, należy skonfigurować to ustawienie, aby **tak**, a następnie skonfiguruj następujące ustawienia:

    -   **Profil rejestracji** </br>
        Kliknij przycisk **Ustaw profil** do tworzenia lub wybierz profil rejestracji. Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień klienta dla rejestracji](/sccm/core/clients/deploy/deploy-clients-to-macs#configure-client-settings-for-enrollment).

-   **Zezwalaj użytkownikom na rejestrowanie nowoczesnych urządzeń** </br>
    Aby włączyć oparta na użytkowniku rejestracji nowoczesnych urządzeń, należy skonfigurować to ustawienie, aby **tak**, a następnie skonfiguruj następujące ustawienia:

    -   **Profil rejestracji nowoczesnego urządzenia** </br>
        Kliknij przycisk **Ustaw profil** do tworzenia lub wybierz profil rejestracji. Aby uzyskać więcej informacji, zobacz [Utwórz profil rejestracji, który pozwala użytkownikom na rejestrowanie nowoczesnych urządzeń](/sccm/mdm/get-started/set-up-device-enrollment-on-premises-mdm#bkmk_createProf).



##  <a name="hardware-inventory"></a>Spis sprzętu  

-   **Włącz spis sprzętu na klientach** </br>
    To ustawienie ma wartość **tak** domyślnie. Aby uzyskać więcej informacji, zobacz [wprowadzenie do spisu sprzętu](/sccm/core/clients/manage/inventory/introduction-to-hardware-inventory).

-   **Harmonogram spisu sprzętu** </br>
    Kliknij przycisk **harmonogram** Aby dostosować częstotliwość cyklu klienci uruchamiali spisu sprzętu. Domyślnie ten cykl występuje co siedem dni.

-   **Maksymalne opóźnienie losowe (w minutach)** </br>
    Określ maksymalną liczbę minut dla klienta programu Configuration Manager wygenerować losowy spisu sprzętu cykl ze zdefiniowanego harmonogramu. Losowe przez wszystkich klientów pomaga przetwarzanie spisu równoważenia obciążenia na serwerze lokacji. Można określić wartość 0 lub 480 minut. Domyślnie ta wartość jest równa 240 minut (czterech godzin).

-   **Maksymalny rozmiar niestandardowego pliku MIF (KB)**  </br>
     Określ maksymalny rozmiar w kilobajtach (KB), dozwoloną dla każdego niestandardowego pliku Management Information Format (MIF), który klient zbiera podczas cyklu tworzenia spisu sprzętu. Agent inwentaryzacji sprzętu programu Configuration Manager nie może przetwarzać niestandardowe pliki MIF o większym rozmiarze. Można określić o rozmiarze 1 KB do 5,120 KB. Wartością domyślną jest 250 KB. To ustawienie nie wpływa na rozmiar standardowego pliku danych zapasów sprzętu.  

    > [!NOTE]  
    >  To ustawienie jest dostępne tylko w domyślnych ustawieniach klienta.  

-   **Klasy zapasów sprzętu**  </br>
     Kliknij przycisk **Ustaw klasy** rozszerzyć informacje o sprzęcie zbierane od klientów bez konieczności ręcznego modyfikowania pliku sms_def.mof. Aby uzyskać więcej informacji, zobacz [jak skonfigurować spis sprzętu](../../../core/clients/manage/inventory/configure-hardware-inventory.md).  

-   **Zbierz pliki MIF**  </br>
     To ustawienie umożliwia określenie, czy do zbierania plików MIF z klientów programu Configuration Manager podczas tworzenia spisu sprzętu.  

     Plik MIF mają zostać zebrane przez spis sprzętu musi być w poprawnej lokalizacji na komputerze klienckim. Domyślnie pliki znajdują się w następujących ścieżkach:  

    -   **Pliki IDMIF** powinien znajdować się w folderze Windows\System32\CCM\Inventory\Idmif 

    -   **Pliki NOIDMIF** powinien znajdować się w folderze Windows\System32\CCM\Inventory\Noidmif

    > [!NOTE]  
    >  To ustawienie jest dostępne tylko w domyślnych ustawieniach klienta.

   

##  <a name="metered-internet-connections"></a>Mierzonych połączeń internetowych  
 Zarządzanie systemem Windows 8 i nowszych komputerach wykorzystania mierzonych połączeń internetowych do komunikowania się z programem Configuration Manager. Dostawcy Internetu czasami naliczają opłaty według ilości wysyłanych i odbieranych danych podczas taryfowego połączenia z Internetem.  

> [!NOTE]  
>  Skonfigurowane ustawienie klienta nie jest stosowane w następujących scenariuszach:  
>   
> -   Komputer jest zasilany z połączenia danych w roamingu: Klient programu Configuration Manager wykonuje wszystkie zadania, które wymagają danych do przeniesienia do lokacji programu Configuration Manager.  
> -   Właściwości połączenia sieciowego systemu Windows są skonfigurowane jako inną niż taryfową: Klient programu Configuration Manager zachowuje się tak, jakby połączenie jest nietaryfowe i transferuje dane do lokacji.  

-   **Komunikacja z klientem w przypadku mierzonych połączeń internetowych**  </br>
     Wybierz jedną z następujących opcji dla tego ustawienia:  

    -   **Zezwalaj na**: Cała komunikacja z klientem są dozwolone przez taryfowe połączenie internetowe, chyba że urządzenie klienckie korzysta z połączenia danych w roamingu.  

    -   **Limit**: Wyłącznie następująca komunikacja z klientem są dozwolone przez taryfowe połączenie internetowe:  

        -   Pobieranie zasad klienta  

        -   Komunikaty o stanie klienta, które będą wysłane do lokacji  

        -   Żądania instalacji oprogramowania wynikające z korzystania z katalogu aplikacji  

        -   Wymagane wdrożenia (po osiągnięciu ostatecznego terminu instalacji)  

        > [!IMPORTANT]  
        >  Klient zawsze zezwala na instalacje oprogramowania z programu Software Center ani katalogu aplikacji, niezależnie od ustawień mierzonego połączenia internetowego.  

         Po osiągnięciu limitu transferu danych mierzonego połączenia internetowego, klient nie próbuje nawiązać połączenia z lokacji programu Configuration Manager.  

    -   **Blok**: Klient programu Configuration Manager nie będzie próbował komunikować się z lokacji programu Configuration Manager, gdy znajduje się w mierzonego połączenia internetowego. Ta opcja jest domyślnie.  



##  <a name="power-management"></a>Zarządzanie energią  

-   **Zezwalaj na zarządzanie zasilaniem urządzeń** </br>
    Skonfiguruj to ustawienie, aby **tak** umożliwienie zarządzania energią na komputerach klienckich. Aby uzyskać więcej informacji, zobacz [wprowadzenie do zarządzania energią](/sccm/core/clients/manage/power/introduction-to-power-management).

-   **Zezwalaj użytkownikom na wykluczanie swoich urządzeń z zarządzania zasilaniem**  </br>
     Wybierz **tak** aby umożliwić użytkownikom w programie Software Center wykluczenie ich komputera ze skonfigurowanych ustawień zarządzania energią.  

-   **Włącz serwer proxy wznawiania** </br> 
     Wybierz opcję **Tak** , aby uzupełnić ustawienie funkcji Wake On LAN lokacji, jeżeli została skonfigurowana dla pakietów emisji pojedynczej.  

     Aby uzyskać więcej informacji o serwerze proxy wznawiania, zobacz [planowanie sposobu wznawiania działania klientów w programie System Center Configuration Manager](../../../core/clients/deploy/plan/plan-wake-up-clients.md).  

    > [!WARNING]  
    >  Nie należy włączać serwera proxy wznawiania w sieci produkcyjnej bez wcześniejszego zrozumienia sposobu jego działania i oceny w środowisku testowym.  

    Następnie należy skonfigurować następujące dodatkowe ustawienia, odpowiednio do potrzeb:

    -   **Numer portu serwera proxy wznawiania (UDP)**  </br>
         Numer portu używanego przez klientów do wysyłania pakietów wznawiania do komputerów w stanie uśpienia. Zachowaj domyślny port 25536 lub zmienić numer na wybraną wartość.  

    -   **Numer portu funkcji Wake On LAN (UDP)** </br> 
         Należy zachować wartość domyślną 9, chyba że zmieniono numer portu Wake On LAN (UDP) na **porty** kartę witryny **właściwości**.  

        > [!IMPORTANT]  
        >  Ten numer musi być zgodny z wartością w oknie **Właściwości**lokacji. W przypadku zmiany tego numeru w jednym miejscu, nie jest aktualizowana w innym miejscu.  

    -   **Wyjątek zapory systemu Windows Defender dla serwera proxy wznawiania** </br>
         Klient programu Configuration Manager automatycznie konfiguruje numer portu serwera proxy wznawiania na urządzeniach, na których działa Zapora systemu Windows Defender. Kliknij przycisk **Konfiguruj** do określania profilów żądanego zaporą.

        Jeżeli na klientach działa inna zapora, należy ręcznie skonfigurować go, aby umożliwić **numer portu serwera proxy wznawiania (UDP)**.  
        
    -   **Prefiksy IPv6, jeśli jest to wymagane przez DirectAccess lub inne pośredniczące urządzenia sieciowe. Użyj przecinka, aby określić wiele wpisów** </br>
        Wprowadź niezbędne prefiksów IPv6 dla serwera proxy wznawiania działa w sieci.



##  <a name="remote-tools"></a>Zdalne narzędzia  

-   **Włącz zdalne sterowanie na klientach** z opisem **Profile wyjątków zapory**  </br>
     Kliknij przycisk **Konfiguruj** do włączenia tej funkcji zdalnego sterowania programu Configuration Manager. Opcjonalnie skonfigurować ustawienia zapory, aby umożliwić zdalne sterowanie do pracy na komputerach klienckich.  

     Zdalne sterowanie jest domyślnie wyłączone.  

    > [!IMPORTANT]  
    >  Jeżeli ustawienia zapory nie zostaną skonfigurowane, zdalne sterowanie może nie działać prawidłowo.  

-   **Użytkownicy mogą zmieniać zasady lub ustawienia powiadomień w programie Software Center**  </br>
     Wybierz, czy użytkownicy mogą zmieniać opcje zdalnego sterowania z programu Software Center.  

-   **Zezwalaj na zdalne sterowanie komputerem nienadzorowanym**  </br>
     Wybierz, czy administrator może użyć sterowania zdalnego dostępu do komputera klienta, który jest wylogowanego lub zablokowanego. Tylko zalogowanymi i odblokowanymi komputer można sterować zdalnie, gdy to ustawienie jest wyłączone.  

-   **Monituj użytkownika o zezwolenie na zdalne sterowanie**  </br>
     Wybierz, czy komputer kliencki pokazuje komunikat z pytaniem o zezwolenie użytkownika przed zezwoleniem na sesję zdalnego sterowania.  

-   **Monituj użytkownika o zgodę na przesyłanie zawartości z udostępnionego Schowka** </br>
    Zezwalaj użytkownikom możliwość zaakceptowania lub odrzucenia transferu plików przed przesyłania zawartości z udostępnionego Schowka podczas sesji zdalnego sterowania. Użytkownicy potrzebują tylko można udzielić uprawnienia raz na sesji i Podgląd ma możliwość udzielenia sobie uprawnień, aby kontynuować transfer plików.

-   **Przyznaj uprawnienie do zdalnego sterowania lokalnej grupie administratorów**  </br>
     Wybierz, czy Administratorzy lokalni na serwerze inicjującym połączenie zdalnego sterowania mogą nawiązywać sesje zdalnego sterowania na komputerach klienckich.  

-   **Dozwolony poziom dostępu**  </br>
     Określ poziom dostępu zdalnego sterowania. Wybierz jedną z następujących ustawień:  
    - **Brak dostępu**
    - **Wyświetl tylko**
    - **Pełna kontrola**  

-   **Dopuszczone podglądy zdalnego sterowania i pomocy zdalnej**  </br>
     Kliknij przycisk **Ustaw podglądy** można określić nazwy użytkowników systemu Windows, którzy mogą nawiązywać sesje zdalnego sterowania na komputerach klienckich.  

-   **Pokaż ikonę powiadomienia sesji na pasku zadań**  </br>
     Skonfiguruj to ustawienie, aby **tak** ikona na pasku zadań systemu Windows klienta wskazująca aktywną sesję zdalnego sterowania.  

-   **Pokaż pasek połączenia sesji**  </br>
     Skonfiguruj to ustawienie, aby **tak** pokazanie pasek połączenia sesji wysokiej widoczności na klientach, aby wskazać aktywną sesję zdalnego sterowania.  

-   **Odtwórz dźwięk na kliencie**  </br>
     Skonfiguruj to ustawienie, aby użyć dźwięku sygnalizującego, kiedy sesja zdalnego sterowania jest aktywna na komputerze klienckim. Wybierz jedną z następujących opcji:
    - **Brak dźwięku**
    - **Początku i wysyłania sesji** (ustawienie domyślne)
    - **Wielokrotnie podczas sesji**  

-   **Zarządzaj ustawieniami nieżądanej pomocy zdalnej**  </br>
     Skonfiguruj to ustawienie, aby **tak** aby umożliwić programowi Configuration Manager Zarządzanie sesjami nieżądanej pomocy zdalnej.  

     W sesji nieżądanej pomocy zdalnej użytkownika na komputerze klienckim nie wysyłanie żądań pomocy do zainicjowania sesji.  

-   **Zarządzaj ustawieniami pomocy zdalnej na żądanie**  </br>
     Skonfiguruj to ustawienie, aby **tak** aby umożliwić programowi Configuration Manager Zarządzanie sesjami pomocy zdalnej na żądanie.  

     W sesji Pomocy zdalnej na żądanie użytkownika na komputer kliencki wysłał żądanie do administratora o pomoc zdalną.  

-   **Poziom dostępu dla pomocy zdalnej**  </br>
     Wybierz poziom dostępu przypisany do sesji Pomocy zdalnej, inicjowanych w konsoli programu Configuration Manager.  Wybierz jedną z następujących opcji:
    - **Brak** (ustawienie domyślne)
    - **Zdalne wyświetlanie**
    - **Pełna kontrola**

    > [!NOTE]  
    >  Użytkownik przy komputerze klienckim musi zawsze udzielić zezwolenia, aby można było rozpocząć sesję pomocy zdalnej.  

-   **Zarządzaj ustawieniami pulpitu zdalnego**  </br>
     Skonfiguruj to ustawienie, aby **tak** aby umożliwić programowi Configuration Manager Zarządzanie sesjami pulpitu zdalnego dla komputerów.  

-   **Zezwalaj dopuszczonym podglądom na połączenie za pomocą programu Podłączanie pulpitu zdalnego**  </br>
     Skonfiguruj to ustawienie, aby **tak** do dodawania użytkowników określonych na liście dopuszczonych podglądów do grupy użytkowników lokalnych usług pulpitu zdalnego na komputerach klienckich.  

-   **Wymagaj uwierzytelniania na poziomie sieci na komputerach z systemem operacyjnym Windows Vista i nowszymi wersjami**  </br>
     Skonfiguruj to ustawienie, aby **tak** na potrzeby uwierzytelniania na poziomie sieci (NLA) nawiązania połączeń pulpitu zdalnego na komputerach klienckich. NLA początkowo wymaga mniej zasobów na komputerze zdalnym, ponieważ uwierzytelnianie użytkownika zostanie zamknięty przed nawiązaniem połączenia pulpitu zdalnego. Za pomocą uwierzytelniania na poziomie sieci jest bezpieczniejsza konfiguracja. NLA pomaga chronić komputer przed złośliwymi użytkownikami lub oprogramowaniem i zmniejsza zagrożenie atakami typu "odmowa usługi".  



## <a name="software-center"></a>Centrum oprogramowania

-   **Wybierz te nowe ustawienia, aby określić informacje o firmie** </br>
    Skonfiguruj to ustawienie, aby **tak**, a następnie określ następujące ustawienia, aby brand Centrum oprogramowania dla Twojej organizacji:

    - **Nazwa firmy** </br>
        Wprowadź nazwę organizacji wyświetlaną użytkownikom w programie Software Center.
    - **Schemat kolorów w programie Software Center** </br>
        Kliknij przycisk **wybierz kolor** do definiowania kolor podstawowy używany przez Centrum oprogramowania.
    - **Wybierz logo, które w programie Software Center** </br>
        Kliknij przycisk **Przeglądaj** wybierz obraz do wyświetlenia w programie Software Center. Logo musi być formatem JPEG lub PNG 400 x 100 pikseli o maksymalnym rozmiarze 750 KB.

-   Widoczność kartę Centrum oprogramowania </br>
    Skonfiguruj dodatkowe ustawienia w tej grupie mają **tak** uwidocznić w programie Software Center następujące karty:
    - **Aplikacje**
    - **Aktualizacje**
    - **Systemy operacyjne**
    - **Stan instalacji**
    - **Zgodność urządzeń**
    - **Opcje**

    Na przykład, jeśli Twoja organizacja nie korzysta z zasadami zgodności i chcesz ukryć kartę zgodności urządzeń w programie Software Center, skonfigurować **włączyć zgodności urządzenia, na karcie** ustawienie **nr**.



## <a name="software-deployment"></a>Wdrażanie oprogramowania  

-   **Zaplanuj ponowną ocenę dla wdrożeń**  </br>
     Należy skonfigurować harmonogram, gdy program Configuration Manager ponownie ocenia reguły wymagań dla wszystkich wdrożeń. Wartość domyślna to co siedem dni.  

    > [!IMPORTANT]  
    >  Zaleca się, że nie zmienisz tę wartość na mniejszą wartość niż domyślne. Bardziej aktywnego harmonogramu ponownej oceny miało negatywny wpływ na wydajność sieci i klienta komputerów.  

     Zainicjować tę akcję od klienta, wybierając **cykl oceny wdrażania aplikacji** z **akcje** karcie **programu Configuration Manager** Panelu sterowania.  



##  <a name="software-inventory"></a>Zapasy oprogramowania  

-   **Włącz spis oprogramowania na klientach** </br>
    To ustawienie ma wartość **tak** domyślnie. Aby uzyskać więcej informacji, zobacz [wprowadzenie do spisu oprogramowania](/sccm/core/clients/manage/inventory/introduction-to-software-inventory).

-   **Zaplanuj spis oprogramowania i plików zbieranie** </br>
    Kliknij przycisk **harmonogram** można dostosować częstotliwość, że klienci mają uruchamiać oprogramowania cykle kolekcji spisu i plików. Domyślnie ten cykl występuje co siedem dni.

-   **Szczegóły raportowania spisu**  </br>
     Określ jedną z następujących poziomów informacje o pliku do magazynu:
    - **Tylko plik**
    - **Tylko produktu**
    - **Pełne szczegóły** (ustawienie domyślne)

-   **Następujące typy plików do spisu**  </br>
     Jeśli chcesz określić typy plików do spisu, kliknij przycisk **Ustaw typy**, a następnie skonfiguruj następujące opcje:  

    > [!NOTE]  
    >  Jeśli wielu niestandardowych ustawień klienta są stosowane do komputera, magazynu, która zwraca każdego ustawienia są scalane.  

    -   Kliknij przycisk **nowy** ikonę, aby dodać do spisu nowy typ pliku. Następnie określ następujące informacje w **właściwości zinwentaryzowanych plików** okno dialogowe:  

        -   **Nazwa**: Podaj nazwę pliku, który chcesz dodać do spisu. Użyj gwiazdki (**&#42;**) symbolu wieloznacznego oznaczającego dowolny ciąg tekstu i znaku zapytania (**?**) do reprezentowania dowolny pojedynczy znak. Na przykład, jeśli chcesz dodać do spisu wszystkie pliki z rozszerzeniem doc, określ nazwę pliku  **\*doc**.  

        -   **Lokalizacja**: Kliknij przycisk **ustawić** otworzyć **właściwości ścieżki** okno dialogowe. Konfigurowanie spisu oprogramowania w celu wyszukania na dyskach twardych wszystkich klientów określonego pliku, określonej ścieżki (na przykład **C:\Folder**), lub Wyszukaj określonej zmiennej (na przykład *% windir %*). Można także przeszukać wszystkie podfoldery w określonej ścieżce.  

        -   **Wyklucz pliki zaszyfrowane i skompresowane**: Po wybraniu tej opcji pliki skompresowane lub zaszyfrowane nie są dodane do spisu.  

        -   **Wyklucz pliki zawarte w folderze systemu Windows**: Po wybraniu tej opcji pliki w folderze systemu Windows i jego podfolderach nie są dodane do spisu.  

    -   Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Właściwości zinwentaryzowanych plików** .  

    -   Dodaj wszystkie pliki, które mają być spisu, a następnie kliknij przycisk **OK** zamknąć **Konfiguruj ustawienie klienta** okno dialogowe.  

-   **Zbierz pliki**  </br>
     Jeśli chcesz zebrać pliki z komputerów klienckich, kliknij przycisk **Ustaw pliki** , a następnie skonfiguruj następujące ustawienia:  

    > [!NOTE]  
    >  Jeśli wielu niestandardowych ustawień klienta są stosowane do komputera, magazynu, która zwraca każdego ustawienia są scalane.  

    -   W **Konfiguruj ustawienie klienta** okno dialogowe, kliknij przycisk **nowy** ikonę, aby dodać plik do zebrania.  

    -   W oknie dialogowym **Właściwości zebranych plików** wprowadź następujące informacje:  

        -   **Nazwa**: Podaj nazwę pliku, który chcesz zebrać. Użyj gwiazdki (**&#42;**) symbolu wieloznacznego oznaczającego dowolny ciąg tekstu i znaku zapytania (**?**) do reprezentowania dowolny pojedynczy znak.  

        -   **Lokalizacja**: Kliknij przycisk **ustawić** otworzyć **właściwości ścieżki** okno dialogowe. Konfigurowanie spisu oprogramowania do wyszukania na dyskach twardych wszystkich klientów pliku do zebrania, określonej ścieżki (na przykład **C:\Folder**), lub Wyszukaj określonej zmiennej (na przykład *% windir %*). Można także przeszukać wszystkie podfoldery w określonej ścieżce.  

        -   **Wyklucz pliki zaszyfrowane i skompresowane**: Po wybraniu tej opcji pliki skompresowane lub zaszyfrowane nie są zbierane.  

        -   **Zatrzymaj zbieranie plików, gdy łączny rozmiar plików przekracza (KB)**: Określ rozmiar pliku w kilobajtach (KB), po którym klient zatrzymuje zbieranie określonych plików.  

          > [!NOTE]  
          >  Serwer lokacji zbiera pięć ostatnio zmienionych wersji zebranych plików i zapisuje je w  *&lt;katalog instalacyjny programu ConfigMgr\>*\Inboxes\Sinv.box\Filecol katalogu. Jeśli plik nie został zmieniony od ostatniego cyklu spisu oprogramowania, plik nie jest zebrany ponownie.  
          >   
          >  Spis oprogramowania nie zbiera pliki większe niż 20 MB.  
          >   
          >  Wartość **maksymalny rozmiar wszystkich zebranych plików (KB)** w **Konfiguruj ustawienie klienta** wyświetlane okno dialogowe maksymalny rozmiar wszystkich zebranych plików. Po osiągnięciu tego rozmiaru zatrzymuje zbieranie plików. Wszystkie już zebrane pliki są zachowywane i wysłane do serwera lokacji.  

          > [!IMPORTANT]
          >  Jeśli konfigurujesz zapasy oprogramowania w celu zebrania wielu dużych plików, ta konfiguracja może negatywnie wpłynąć na wydajność sieci i lokacji serwera.  

        Aby uzyskać informacje o sposobie wyświetlania zebranych plików, zobacz [jak używać Eksploratora zasobów do wyświetlania spisu oprogramowania](../../../core/clients/manage/inventory/use-resource-explorer-to-view-software-inventory.md).  

    -   Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Właściwości zebranych plików** .  

    -   Dodaj wszystkie pliki, które chcesz zebrać, a następnie kliknij przycisk **OK** zamknąć **Konfiguruj ustawienie klienta** okno dialogowe.  

-   **Ustaw nazwy**  </br>
     Agent spisu oprogramowania pobiera producenta i nazw produktów z informacji w nagłówku pliku. Te nazwy nie zawsze są standardowe informacje nagłówka pliku. Podczas wyświetlania spisu oprogramowania w Eksploratorze zasobów, może się pojawić różne wersje tego samego producenta lub nazwy produktu. Aby ustandaryzować te wyświetlane nazwy, kliknij przycisk **Ustaw nazwy** , a następnie skonfiguruj następujące ustawienia:  

    -   **Nazwa typu**: Spis oprogramowania zbiera informacje o producentach i produktach. Wybierz, czy chcesz skonfigurować nazwy wyświetlane dla **producenta** lub **produktu**.  

    -   **Nazwa wyświetlana**: Określ nazwę wyświetlaną, która ma być używany zamiast nazw na **zinwentaryzowane nazwy** listy. Kliknij przycisk **nowy** ikonę, aby określić nową nazwę wyświetlaną.  

    -   **Zinwentaryzowane nazwy**: Kliknij przycisk **nowy** ikonę, aby dodać nazwę uwzględnionych w spisie. Ta nazwa zostanie zastąpiona w spisie oprogramowania przez nazwę wybraną w **Nazwa wyświetlana** listy. Można dodać wiele nazw w celu zastąpienia.  



##  <a name="software-metering"></a>Pomiar użytkowania oprogramowania

-   **Włącz zliczanie oprogramowania na klientach** </br>
    To ustawienie ma wartość **tak** domyślnie. Aby uzyskać więcej informacji, zobacz [pomiaru użytkowania oprogramowania](/sccm/apps/deploy-use/monitor-app-usage-with-software-metering#configure-software-metering).

-   **Planowanie zbierania danych** </br>
    Kliknij przycisk **harmonogram** można dostosować częstotliwość, że klienci mają uruchamiać cyklu zliczania oprogramowania. Domyślnie ten cykl występuje co siedem dni.



##  <a name="software-updates"></a>Aktualizacje oprogramowania  

-   **Włącz aktualizacje oprogramowania na klientach**  </br>
     To ustawienie umożliwia włączenie aktualizacji oprogramowania na klientach programu Configuration Manager. Gdy to ustawienie zostanie wyłączone, programu Configuration Manager usunie istniejące zasady wdrażania z klienta. Po ponownym włączeniu tego ustawienia klient pobierze bieżące zasady wdrażania.  

    > [!IMPORTANT]  
    >  Po wyłączeniu tego ustawienia zasad zgodności, które są oparte na aktualizacji oprogramowania nie będzie już działać.  

-   **Harmonogram skanowania w poszukiwaniu aktualizacji oprogramowania**  </br>
     Kliknij przycisk **harmonogram** Aby określić, jak często klient inicjuje skanowania oceny zgodności. To skanowanie Określa stan aktualizacji oprogramowania na kliencie (na przykład wymagane lub zainstalowane). Aby uzyskać więcej informacji na temat oceny zgodności, zobacz [oceny zgodności aktualizacji oprogramowania](../../../sum/understand/software-updates-introduction.md#BKMK_SUMCompliance).  

     Domyślnie ten tryb skanowania używa prostego harmonogramu zainicjować co siedem dni. Można utworzyć harmonogramu niestandardowego, aby określić dokładną dnia i godziny rozpoczęcia, użyj uniwersalnego czasu koordynowanego (UTC) lub czas lokalny i skonfigurować interwał powtarzania dla określonego dnia tygodnia.  

    > [!NOTE]  
    >  Jeśli w przypadku określenia interwału krótszego niż jeden dzień, programu Configuration Manager automatycznie domyślnie jeden dzień.  

    > [!WARNING]  
    >  Rzeczywista godzina uruchomienia na komputerach klienckich to godzina rozpoczęcia wydłużony o przypadkowy czas maksymalnie do dwóch godzin. Losowe zapobiega komputery klienckie z Inicjowanie skanowania i jednocześnie nawiązywania połączenia z aktywnym punktem aktualizacji oprogramowania.  

-   **Zaplanuj ponowną ocenę wdrożenia**  </br>
     Kliknij przycisk **harmonogram** skonfigurować częstotliwość aktualizacji oprogramowania klienta agenta ponownie ocenia aktualizacje oprogramowania dla stanu instalacji na komputerach klienckich programu Configuration Manager. Po aktualizacji wcześniej zainstalowane oprogramowanie znajduje się już na klientach, ale nadal są wymagane, klient ponownie instaluje aktualizacje oprogramowania.

     Dostosuj ten harmonogram zasadą firmową dotyczącą zgodności aktualizacji oprogramowania i określa, czy użytkownicy można odinstalować aktualizacji oprogramowania. Każdy cykl ponownej oceny wdrożenia powoduje aktywności procesora komputera klienta i sieci. Domyślnie to ustawienie powoduje użycie prostego harmonogramu zainicjować skanowanie ponownej oceny wdrożenia co siedem dni.  

    > [!NOTE]  
    >  Jeśli w przypadku określenia interwału krótszego niż jeden dzień, programu Configuration Manager automatycznie domyślnie jeden dzień.  

-   **Po osiągnięciu ostatecznego terminu wdrożenia dowolnej aktualizacji oprogramowania zainstaluj wszystkie pozostałe wdrożenia aktualizacji oprogramowania z terminem wypadającym w danym okresie czasu**  </br>
     Skonfiguruj to ustawienie, aby **tak** Aby zainstalować wszystkie aktualizacje oprogramowania z wymaganych wdrożeń z terminami występujące w danym okresie czasu. Podczas wdrażania aktualizacji oprogramowania wymagane przez nią miejsce osiągnie termin, instalacja aktualizacji oprogramowania we wdrożeniu inicjowania przez klienta. To ustawienie określa, czy zainstalować aktualizacje oprogramowania z innych wymaganych wdrożeniach, które mają terminy w określonym czasie.  

     To ustawienie umożliwia przyspieszenie instalacji wymaganych aktualizacji oprogramowania. To ustawienie zwiększa również potencjalnie zabezpieczeń klienta, potencjalnie zmniejsza powiadomienia użytkownika końcowego i potencjalnie zmniejsza klienta zostanie ponownie uruchomiony. Domyślnie to ustawienie ma wartość **nr** w związku z tym wyłączona.  

-   **Okres czasu, w którym wszystkie oczekujące wdrożenia z terminem wypadającym w tym okresie także zostaną zainstalowane**  </br>
     To ustawienie umożliwia określenie długości czasu dla poprzedniego ustawienia. Można wprowadzić wartość od 1 do 23 godzin oraz 1 do 365 dni. Domyślnie to ustawienie jest skonfigurowane na siedem dni.  

-   **Włącz instalację plików instalacji ekspresowej na klientach** </br>
    Skonfiguruj to ustawienie, aby **tak** do Zezwalaj klientom na użycie plików instalacji ekspresowej. Aby uzyskać więcej informacji, zobacz [instalacji zarządzania Express pliki aktualizacji systemu Windows 10](/sccm/sum/deploy-use/manage-express-installation-files-for-windows-10-updates).

    -   **Port używany do pobierania zawartości plików instalacji ekspresowej** </br>
        To ustawienie określa port lokalny dla odbiornika HTTP do pobierania zawartości express. Domyślnie jest ustawiona na 8005. Nie trzeba otworzyć ten port w zaporze klienta.

-   **Włącz zarządzanie agenta klienta Office 365** </br>
    To ustawienie umożliwia włączanie zarządzania agenta klienta Office 365. Jeśli ustawisz wartość **tak**, umożliwia konfigurację usługi Office 365 ustawienia instalacji, pobierania plików z pakietu Office sieci dostarczania zawartości (CDN) i wdrażanie plików jako aplikacji w programie Configuration Manager. Aby uzyskać więcej informacji, zobacz [zarządzania usługi Office 365 ProPlus](/sccm/sum/deploy-use/manage-office-365-proplus-updates).



## <a name="state-messaging"></a>Do obsługi komunikatów stanu

-   **Komunikat o stanie raportowania cyklu (w minutach)**  </br>
     Określa, jak często klienci zgłaszania komunikatów o stanie. To ustawienie jest 15 minut domyślnie.



##  <a name="user-and-device-affinity"></a>Koligacja użytkowników i urządzeń  

-   **Próg użycia dla koligacji użytkownika i urządzenia (minuty)**  </br>
     Określ liczbę minut, zanim programu Configuration Manager tworzy mapowanie koligacji urządzenia użytkownika.  Domyślnie ta wartość jest 2880 minut (dwa dni).

-   **Próg użycia dla koligacji użytkownika i urządzenia (dni)**  </br>
     Określ liczbę dni, przez jaką klient mierzy próg koligacji na podstawie użycia urządzeń.  Domyślnie ta wartość wynosi 30 dni.

    > [!NOTE]  
    >  Na przykład określić **próg użycia koligacji urządzenia użytkownika (w minutach)** jako **60** minut i **próg użycia koligacji użytkownika i urządzenia (dni)** jako **5**  dni. Następnie użytkownik musi używać urządzenia przez 60 minut w okresie 5 dni na tworzenie koligacji automatyczne z urządzeniem.  

-   **Automatycznie konfiguruj koligację użytkownika i urządzenia na podstawie danych użycia**  </br>
     Wybierz **tak** na tworzenie koligacji urządzenia użytkownika automatycznego na podstawie informacji użycia, która gromadzi programu Configuration Manager.  

-   **Zezwalaj użytkownikowi na definiowanie urządzeń podstawowych** </br>
    Gdy to ustawienie jest **tak** , a następnie użytkownikom identyfikację własne urządzenia podstawowe w Centrum oprogramowania.



## <a name="windows-analytics"></a>Module analiz systemu Windows

Aby uzyskać więcej informacji na temat tych ustawień, zobacz [skonfigurować klientów do danych raportu do analiz systemu Windows](/sccm/core/clients/manage/monitor-windows-analytics#configure-clients-to-report-data-to-windows-analytics).
    