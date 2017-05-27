---
title: Nowa wersja 1702 | Dokumentacja firmy Microsoft
description: "Uzyskiwanie szczegółowych informacji dotyczących zmian oraz nowe funkcje wprowadzone w wersji 1702 programu System Center Configuration Manager."
ms.custom: na
ms.date: 05/02/2017
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 409e26e1-7716-4f1d-a0ee-34feabf20792
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f4cb711f369698fe8e045f8c83dd96ec6fb29d70
ms.openlocfilehash: a2954b3c6f9a09b7246347e780c4cfc49ba39ca1
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="what39s-new-in-version-1702-of-system-center-configuration-manager"></a>Co &#39; s nowe w wersji 1702 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Zaktualizuj 1702 dla bieżącej gałęzi System Center Configuration Manager jest dostępna jako aktualizacja w konsoli dla witryn zainstalowane wcześniej, których jest uruchomiona wersja 1602, 1606 lub 1610. Jest również dostępna jako wersję linii bazowej, którą można skorzystać w przypadku instalowania nowego wdrożenia.

> [!TIP]  
> Aby zainstalować nową lokację, należy użyć wersji linii bazowej programu Configuration Manager.  
>  Więcej informacji na temat:    
>   - [Instalowanie nowych witryn](https://technet.microsoft.com/library/mt590197.aspx)  
>   - [Instalowanie aktualizacji w lokacjach](https://technet.microsoft.com/library/mt607046.aspx)  
>   - [Wersje linii bazowej i aktualizacji](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions)  

Poniższe sekcje zawierają szczegółowe informacje dotyczące zmiany i nowe możliwości wprowadzona w wersji 1702 programu Configuration Manager.  

## <a name="deprecated-features-and-operating-systems"></a>Przestarzałe funkcje i systemy operacyjne
Więcej informacji na temat obsługi zmian przed ich wdrożeniem w [usunięta i zastąpiona funkcji](/sccm/core/plan-design/changes/removed-and-deprecated-features).

Obsługa wersji docelowych 1702 dla następujących produktów:
- **SQL Server 2008 R2**, serwerów baz danych lokacji. Amortyzacja obsługi został [przedstawiona po raz pierwszy](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-support-for-sql-server-versions-as-a-site-database) na 10 lipca 2015. Ta wersja programu SQL Server będzie obsługiwane przy użyciu wersji programu Configuration Manager, przed wersją 1702.
- **Windows Server 2008 R2**dla większości ról systemu lokacji i serwerów systemu lokacji. Amortyzacja obsługi został [przedstawiona po raz pierwszy](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-operating-systems) na 10 lipca 2015. Ta wersja systemu Windows będzie obsługiwane przy użyciu wersji programu Configuration Manager, przed wersją 1702.  
- **Windows Server 2008**dla większości ról systemu lokacji i serwerów systemu lokacji. Amortyzacja obsługi został [przedstawiona po raz pierwszy](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-operating-systems) na 10 lipca 2015.
- **Windows XP Embedded**, jako systemu operacyjnego klienta. Oczekiwany był [przedstawiona po raz pierwszy](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-operating-systems) na 10 lipca 2015. Ta wersja systemu Windows będzie obsługiwane przy użyciu wersji programu Configuration Manager, przed wersją 1702.




## <a name="site-infrastructure"></a>Infrastruktura lokacji

### <a name="improvements-for-in-console-search"></a>Udoskonalenia w zakresie wyszukiwania w konsoli
Ulepszenia dotyczące korzystania z wyszukiwania w konsoli programu Configuration Manager są następujące:
 - **Ścieżka obiektu:**  
  Wiele obiektów obsługuje teraz kolumny o nazwie **ścieżki obiektu**.  Podczas wyszukiwania i zawierało tej kolumny w wynikach wyświetlania, można wyświetlić ścieżkę do każdego obiektu. Na przykład, jeśli podczas wykonywania wyszukiwania dla aplikacji w węźle aplikacje wyszukiwania węzły podrzędne *ścieżki obiektu* kolumny w okienku wyników zostanie wyświetlona ścieżka do każdego obiektu, który jest zwracany.   

- **Zachowania wyszukiwany tekst:**  
  Gdy wprowadź tekst w polu tekstowym wyszukiwania, a następnie przełączać się między wyszukiwanie węzła podrzędnego i bieżącego węzła, wpisany tekst teraz utrwalić i pozostaną dostępne dla nowego wyszukiwania bez konieczności ponownego wprowadzania go.

- **Zachowania zdecydować, aby wyszukać węzły podrzędne:**  
 Wybraną opcję wyszukiwania *bieżącego węzła* lub *wszystkie węzły podrzędne* teraz będzie nadal występować po zmianie pracy w węźle. To nowe zachowanie oznacza, że nie muszą stale zresetować ta decyzja jak przenosić konsoli. Domyślnie po otwarciu konsoli opcja jest wyszukiwanie tylko bieżącego węzła.


### <a name="send-feedback-from-the-configuration-manager-console"></a>Wyślij opinię z konsoli programu Configuration Manager

 Opcje opinii w konsoli wysyłanie opinii bezpośrednio do zespołu programistycznego.

 Można znaleźć **opinii** opcji:
 -  Na Wstążce po lewej karcie głównej każdego węzła.  
    ![Wstążka](./media/feedback-home.png)

 -  Po kliknięciu prawym przyciskiem myszy dowolnego obiektu w konsoli.   
     ![Prawej kliknięcia](./media/feedback-option.png)   

 Wybieranie **opinii** Otwiera przeglądarkę, aby [witryny sieci Web programu Configuration Manager UserVoice opinii](https://go.microsoft.com/fwlink/?linkid=617029).


###  <a name="changes-for-updates-and-servicing"></a>Zmiany aktualizacji i obsługi
Zmiany aktualizacji i obsługi są następujące:

- **Lokalizacja węzła**   
  Po zainstalowaniu wersji 1702, **aktualizacji i obsługi** węzeł jest widoczny jako węzeł najwyższego poziomu w obszarze **administracji**. Nie jest już elementem podrzędnym poniżej **usług w chmurze**.

- **Nowe stany aktualizacji**  
  Podczas wyświetlania dostępnych aktualizacji w konsoli, istnieją dwie nowe stany:  
  - **Dostępne do instalacji** — jest to aktualizacja, która ma zostać pobrane i gotowe do zainstalowania.
  - **Gotowy do pobrania** -ta aktualizacja jest dostępna, ale nie została pobrana. Użytkownik może pobrać tę aktualizację, ale została zastąpiona przez nowszą aktualizację.


- **Prostsze opcje aktualizacji**  
  Przy następnym infrastruktury kwalifikuje się do dwóch lub większej liczby aktualizacji, pobrać najnowszą aktualizację. Na przykład, jeśli bieżąca wersja lokacji wynosi dwa lub więcej starsze niż najnowszą wersję, która jest dostępna, tylko że najnowsza wersja aktualizacji jest pobierany automatycznie.  

  Można pobrać i zainstalować dostępne aktualizacje, nawet jeśli nie są one najbardziej aktualnej wersji. Jeśli aktualizacja starsze otrzymasz ostrzeżenie, że aktualizacja została zastąpiona przez nowszej. Do pobierania aktualizacji, która jest *dostępne do pobrania*, wybierz aktualizację, w konsoli, a następnie kliknij przycisk **pobrać**.

- **Ulepszone oczyszczanie starszych aktualizacji**   
  Dodaliśmy funkcję automatycznego czyszczenia, która usuwa niepotrzebne pliki do pobrania z folderu "EasySetupPayload" na serwerze lokacji. Ponieważ wprowadza się z wersją 1702, oczyszczania zaczyna działać po zainstalowaniu kolejnych aktualizacji, takich jak pakiet zbiorczy aktualizacji lub wersji przyszłych aktualizacji.  


### <a name="data-warehouse-service-point"></a>Punkt usługi magazynu danych
 Punkt usługi Magazyn danych jest używany do przechowywania i raport dotyczący długoterminowe dane historyczne dla danego wdrożenia programu Configuration Manager.

 Magazyn danych obsługuje maksymalnie 2 TB danych znacznikami śledzenia zmian. Przechowywanie danych odbywa się przy automatycznych synchronizacji z bazy danych lokacji programu Configuration Manager do bazy danych magazynu danych. Te informacje są dostępne z punktu usług Reporting Services.

 Aby uzyskać więcej informacji, zobacz [magazyn danych usługi punktu](/sccm/core/servers/manage/data-warehouse).


### <a name="peer-cache-improvements"></a>Ulepszenia pamięci podręcznej elementu równorzędnego
 Począwszy od wersji 1702 komputera źródłowego pamięci podręcznej elementu równorzędnego będą odrzucać żądania zawartości, gdy komputer źródłowy pamięci podręcznej elementu równorzędnego spełnia żadnego z następujących warunków:  
  -  Jest w trybie niskim poziomie naładowania baterii.
  -  Obciążenie procesora CPU przekracza 80% w czasie żądania zawartości.
  -  We/Wy dysku ma *AvgDiskQueueLength* który przekracza 10.
  -  Nie ma ma więcej dostępnych połączeń z komputerem.   
Aby uzyskać więcej informacji, zobacz **ograniczony dostęp do źródła pamięci podręcznej elementu równorzędnego** w [Buforowanie równorzędne dla klientów programu Configuration Manager](/sccm/core/plan-design/hierarchy/client-peer-cache).   

Ponadto trzy nowe raporty są dodawane do punktu raportowania. Aby poznać więcej szczegółów na temat odrzuconych żądań zawartości, łącznie z których granic brał udział grupy, komputera i zawartości można używać tych raportów. Zobacz [monitorowanie](/sccm/core/plan-design/hierarchy/client-peer-cache#monitoring) w temacie pamięci podręcznej elementów równorzędnych.

### <a name="content-library-cleanup-tool"></a>Narzędzie do oczyszczania biblioteki zawartości
 Użyj [narzędzia Oczyszczanie biblioteki zawartości](/sccm/core/plan-design/hierarchy/content-library-cleanup-tool) usunąć zawartość z punktów dystrybucji, gdy zawartość nie jest już skojarzona z aplikacją.


### <a name="use-the-oms-connector-with-the-azure-government-cloud"></a>Użyj łącznika usługi OMS z chmurą Rząd Azure
Łącznik usługi OMS umożliwia łączenie do analizy dziennika usługi OMS w chmurze Microsoft Azure Rząd. Należy zmodyfikować plik konfiguracji zainstalować łącznik usługi OMS łącznika może pracować z chmurą Rząd. Aby uzyskać więcej informacji, zobacz [korzystania z łącznika usługi OMS z chmury Azure Rząd](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite#fairfaxconfig).

### <a name="software-update-points-are-added-to-boundary-groups"></a>Punkty aktualizacji oprogramowania są dodawane do grupy granic
Począwszy od wersji 1702, klienci używają grup granic do znajdowania punktu aktualizacji oprogramowania, a do powrotu i Znajdź nowe aktualizacje oprogramowania punktu ich aktualny plan nie jest już dostępny. Punkty aktualizacji oprogramowania można dodać do grupy granic różnych do serwerów, które klient może znaleźć formantu. Aby uzyskać więcej informacji, zobacz [punkty aktualizacji oprogramowania](/sccm/core/servers/deploy/configure/boundary-groups#software-update-points) w [Konfigurowanie grup granic](/sccm/core/servers/deploy/configure/boundary-groups) tematu.


<!-- ## Migration  -->

<!-- ## Client management  -->

## <a name="compliance-settings"></a>Ustawienia zgodności

### <a name="new-compliance-settings-for-ios"></a>Nowe ustawienia zgodności dla systemu iOS

Dodaliśmy wiele nowe ustawienia dla urządzeń z systemem iOS odpowiadać te, które są dostępne w usłudze Microsoft Intune.
Lista wszystkich dostępnych ustawień, zobacz [tworzenie elementów konfiguracji dla systemów iOS i Mac OS X urządzeń zarządzanych za pomocą usługi Intune](/sccm/mdm/deploy-use/create-configuration-items-for-ios-and-mac-os-x-devices-managed-without-the-client).


## <a name="application-management"></a>Zarządzanie aplikacjami

### <a name="improved-support-for-windows-store-for-business-apps"></a>Ulepszona obsługa aplikacji biznesowych dla Sklepu Windows

Teraz można wdrożyć online licencjonowane aplikacje ze Sklepu Windows w przedsiębiorstwie do zarządzania przy użyciu klienta programu Configuration Manager komputery z systemem Windows 10.
Aby uzyskać więcej informacji, zobacz [zarządzania aplikacjami ze Sklepu Windows dla firm](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business).

### <a name="check-for-running-executable-files-before-installing-an-application"></a>Sprawdź, czy uruchomiony pliki wykonywalne przed zainstalowaniem aplikacji

W **właściwości** okno dialogowe wdrożenia typu na **zainstalować zachowanie** kartę, można teraz określić jedną więcej plików wykonywalnych, które działa, spowoduje zablokowania instalacji typu wdrożenia. Użytkownik należy zamknąć plik wykonywalny jest uruchomiona (lub może zostać zamknięty w automatycznie w przypadku wdrożeń z celem wymagane) przed wdrożeniem typ może być instalowany.

Jeśli aplikacja została wdrożona jako **dostępne**i użytkownik końcowy spróbuje zainstalować aplikację, zostanie wyświetlony monit do Zamknij wszystkie uruchomione plików wykonywalnych określona zanim można kontynuować instalacji.

Jeśli aplikacja została wdrożona jako **wymagane**, a opcja **automatycznie Zamknij wszystkie uruchomione pliki wykonywalne określone na karcie zachowanie instalacji okna dialogowego właściwości typu wdrożenia** jest zaznaczone, zobaczy okno dialogowe, które informuje, że określone pliki wykonywalne zostaną automatycznie zamknięte po osiągnięciu ostatecznego terminu instalacji aplikacji.

### <a name="app-management-improvements-for-hybrid-mdm"></a>Ulepszenia zarządzania aplikacji hybrydowych MDM

- [Wdrażanie aplikacji iOS kupionymi woluminu do kolekcji urządzeń](#deploy-volume-purchased-ios-apps-to-device-collections)
- [Obsługa iOS Program zakupu woluminu edukacja](#support-for-ios-volume-purchase-program-for-education)
- [Obsługa wielu tokenów program woluminu zakupu](#support-for-multiple-volume-purchase-program-tokens)


## <a name="operating-system-deployment"></a>Wdrożenie systemu operacyjnego

### <a name="expire-stand-alone-media"></a>Nośnik samodzielny wygaśnie
Po utworzeniu nośnika autonomicznego istnieją nowe opcje Ustaw opcjonalne daty rozpoczęcia i wygaśnięcia na nośniku. Te ustawienia są domyślnie wyłączone. Daty są porównywane z czasem systemowym na komputerze przed uruchomieniem nośników samodzielnych. Gdy czas systemowy jest wcześniejsza niż godzina rozpoczęcia lub późniejsza niż godzina wygaśnięcia, nośnika samodzielnego nie jest uruchomiona. Te opcje są również dostępne przy użyciu polecenia cmdlet New-CMStandaloneMedia środowiska PowerShell. Aby uzyskać szczegółowe informacje, zobacz [tworzenia nośnika samodzielnego](/sccm/osd/deploy-use/create-stand-alone-media).

### <a name="package-id-displayed-in-task-sequence-steps"></a>Identyfikator pakietu wyświetlane w krokach sekwencji zadań
Dowolny etap sekwencji zadań odwołuje się do pakietu, pakietu sterowników, obrazu systemu operacyjnego, obraz rozruchowy lub pakiet uaktualnienia systemu operacyjnego wyświetli identyfikator pakietu odwołuje się do obiektu. Gdy krok sekwencji zadań odwołuje się do aplikacji, zostanie wyświetlona identyfikator obiektu.

### <a name="support-for-additional-content-in-stand-alone-media"></a>Obsługę dodatkowej zawartości w nośniku samodzielnym
Dodatkowa zawartość jest teraz obsługiwana w nośniku samodzielnym. Można wybrać dodatkowe pakiety, pakiety sterowników i aplikacjom przemieszczony na nośniku oraz zawartość, do którego odwołuje się sekwencja zadań. Wcześniej tylko zawartość, do którego odwołuje się sekwencja zadań została przygotowywane na nośnikach autonomicznych. Aby uzyskać szczegółowe informacje, zobacz [tworzenia nośnika samodzielnego](/sccm/osd/deploy-use/create-stand-alone-media).

### <a name="hardware-inventory-collects-uefi-information"></a>Spis sprzętu zbiera informacje z interfejsem UEFI
Nowe klasy spisu sprzętu (**SMS_Firmware**) i właściwości (**UEFI**) są dostępne w celu określenia, czy komputer jest uruchamiany w trybie UEFI. Kiedy komputer jest uruchamiany w trybie UEFI, **UEFI** właściwość jest ustawiona na **TRUE**. To jest domyślnie włączona w programie spisu sprzętu. Aby uzyskać więcej informacji na temat zapasów sprzętu, zobacz [Konfigurowanie spisu sprzętu](/sccm/core/clients/manage/inventory/configure-hardware-inventory).

### <a name="improvements-to-software-center-warning-messages-for-high-impact-task-sequences"></a>Ulepszenia komunikaty ostrzegawcze Centrum oprogramowania dla sekwencji zadań wysoki wpływ
Ta wersja zawiera następujące udoskonalenia komunikaty ostrzegawcze Centrum oprogramowania dla sekwencji zadań wdrażania wysoki wpływ:

- W oknie właściwości dla sekwencji zadań można teraz skonfigurować dowolnej sekwencji zadań, w tym sekwencji zadań systemu operacyjnego jako wdrożenie o wysokim ryzyku. Wszystkie sekwencje zadań, która spełnia określone warunki automatycznie jest zdefiniowany jako wysoki wpływ. Aby uzyskać szczegółowe informacje, zobacz [Zarządzanie wdrożeniami o wysokim ryzyku](/sccm/protect/understand/settings-to-manage-high-risk-deployments).
- W oknie właściwości dla sekwencji zadań można użyć domyślnego komunikatu powiadomienia lub utworzyć własne niestandardowe powiadomienie wysoki wpływ wdrożenia.
- W oknie właściwości dla sekwencji zadań można skonfigurować właściwości, które obejmują wprowadzić wymagane ponowne uruchomienie Centrum oprogramowania rozmiar pobierania sekwencji zadań i szacowany czas wykonywania.
- Komunikat domyślny wysoki wpływ wdrożenia dla miejscowego uaktualnienia teraz stany automatycznie migracji aplikacji, danych i ustawień. Wcześniej, komunikat domyślny dla każdej instalacji systemu operacyjnego wskazane, że wszystkie aplikacje, dane i ustawienia zostałyby utracone, która nie obowiązuje dla uaktualnienia w miejscu.

Aby uzyskać szczegółowe informacje, zobacz [Konfigurowanie ustawień sekwencji zadań wysoki wpływ](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#set-a-task-sequence-as-a-high-impact-task-sequence)

### <a name="return-to-previous-page-when-a-task-sequence-fails"></a>Powrócić do poprzedniej strony, gdy sekwencja zadań zakończy się niepowodzeniem.
Możesz teraz powrócić do poprzedniej strony podczas uruchamiania sekwencji zadań i awarii. Przed tej wersji było konieczne ponowne uruchomienie sekwencji zadań, gdy wystąpił błąd. Na przykład można użyć **Wstecz** przycisku w następujących scenariuszach:

- Po uruchomieniu komputera w środowisku Windows PE, okno dialogowe ładowania sekwencji zadań może być wyświetlany, zanim sekwencja zadań będzie dostępna. Po kliknięciu przycisku Dalej w tym scenariuszu na ostatniej stronie sekwencji zadań wyświetla komunikat, że są sekwencji zadań. Teraz, można kliknąć przycisk **Wstecz** ponowić wyszukiwanie uzyskać dostępne sekwencje zadań. Ten proces można powtarzać momentu udostępnienia sekwencji zadań.
- Podczas uruchamiania sekwencji zadań, ale zależne pakiety zawartości nie są jeszcze dostępne w punktach dystrybucji, sekwencja zadań kończy się niepowodzeniem. Możesz teraz dystrybucji brakującą zawartość (jeśli go nie została jeszcze rozesłana) lub poczekaj, aż zawartość ma być dostępna w punktach dystrybucji, a następnie kliknij **Wstecz** mieć wyszukiwania sekwencji zadań ponownie dla zawartości.

### <a name="pre-cache-content-for-available-deployments-and-task-sequences"></a>Wstępnie buforowanie zawartości dla wdrożeń o dostępności i sekwencji zadań
Począwszy od wersji 1702, w przypadku wdrożeń dostępnych sekwencji zadań, można korzystać z zawartości pamięci podręcznej wstępnego. Wstępne buforowania zawartości zawiera opcję, aby umożliwić klientowi tylko pobierania zawartości odpowiednich zaraz po otrzymaniu wdrożenia. W związku z tym, kiedy użytkownik kliknie przycisk **zainstalować** w Centrum oprogramowania, zawartość jest gotowa i instalacji uruchamia się szybko, ponieważ zawartość znajduje się na lokalnym dysku twardym. Aby uzyskać szczegółowe informacje, zobacz [skonfigurować zawartość pamięci podręcznej przed](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#configure-pre-cache-content).

### <a name="convert-from-bios-to-uefi-during-an-in-place-upgrade"></a>Konwersji z systemu BIOS z interfejsem UEFI podczas uaktualnienia w miejscu
Windows 10 twórcy aktualizacji wprowadzono konwersji proste narzędzie, które automatyzuje proces na partycje dysk twardy sprzęt obsługujący UEFI i narzędzie konwersji integruje się z systemu Windows 7 do procesu uaktualniania w miejscu systemu Windows 10. Podczas tego narzędzia można połączyć z sekwencji zadań uaktualnienia systemu operacyjnego i narzędzia OEM, która konwertuje oprogramowania sprzętowego BIOS z interfejsem UEFI, można przekonwertować komputerów z systemem BIOS z interfejsem UEFI podczas uaktualniania w miejscu do usługi Windows Update twórcy 10. Aby uzyskać szczegółowe informacje, zobacz [czynności sekwencji do zarządzania systemu BIOS z interfejsem UEFI konwersji](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#convert-from-bios-to-uefi-during-an-in-place-upgrade).

### <a name="improvements-to-the-install-applications-task-sequence-step"></a>Ulepszenia dotyczące instalowania aplikacji sekwencji zadań krok
Tej wersji wprowadzono następujące ulepszenia:
- Zwiększono maksymalną liczbę aplikacji, które można zainstalować do 99 w **instalowanie aplikacji** sekwencji zadań. Poprzednie maksymalną liczbę była 9 aplikacji.
- Po dodaniu aplikacjom **instalowanie aplikacji** krok sekwencji zadań w edytorze sekwencji zadań, można teraz wybrać wiele aplikacji z **wybierz aplikację do zainstalowania** okienka.

### <a name="improvements-to-the-auto-apply-driver-task-sequence"></a>Ulepszenia sekwencji zadań automatycznie Zastosuj sterowniki
Nowe zmienne sekwencji zadań są teraz dostępne skonfigurować wartość limitu czasu w kroku sekwencji zadań automatycznie Zastosuj sterowniki podczas tworzenia żądania HTTP wykazu. Dostępne są następujące zmienne i domyślne wartości (w sekundach):
   - SMSTSDriverRequestResolveTimeOut  
     Wartość domyślna: 60
   - SMSTSDriverRequestConnectTimeOut  
     Wartość domyślna: 60
   - SMSTSDriverRequestSendTimeOut  
     Wartość domyślna: 60
   - SMSTSDriverRequestReceiveTimeOut  
     Wartość domyślna: 480

### <a name="windows-10-adk-tracked-by-build-version"></a>Windows ADK 10 śledzony przez wersję kompilacji
Windows 10 ADK teraz są śledzone przez wersję kompilacji, aby zapewnić więcej możliwości w przypadku dostosowywania obrazów rozruchowych systemu Windows 10. Na przykład jeśli w witrynie Windows ADK dla systemu Windows 10, wersja 1607, jest używane tylko obrazy rozruchowe z wersją 10.0.14393 można dostosować w konsoli. Aby uzyskać szczegółowe informacje o dostosowywaniu wersji środowiska WinPE, zobacz [dostosowywanie obrazów rozruchowych](/sccm/osd/get-started/customize-boot-images).

### <a name="default-boot-image-source-path-can-no-longer-be-changed"></a>Nie można zmienić ścieżki źródłowej obrazu rozruchowego domyślne
Domyślne obrazy rozruchowe są zarządzane przez program Configuration Manager i nie zostaną zmienione ścieżki źródłowej obrazu rozruchowego domyślne, w konsoli programu Configuration Manager lub za pomocą zestawu SDK programu Configuration Manager. Możesz skonfigurować ścieżkę źródłową niestandardowe niestandardowe obrazy rozruchowe.

### <a name="default-boot-images-are-regenerated-after-upgrading-configuration-manager-to-a-new-version"></a>Domyślne obrazy rozruchowe są generowane po uaktualnieniu do nowej wersji programu Configuration Manager
Począwszy od tej wersji, podczas uaktualniania wersji zestawu Windows ADK i użyj aktualizacji i obsługi, aby zainstalować najnowszą wersję programu Configuration Manager, Configuration Manager generuje domyślne obrazy rozruchowe. W tym nową wersję środowiska Windows PE z zaktualizowanego zestawu Windows nowej wersji klienta programu Configuration Manager, sterowniki, dostosowania itp. Niestandardowe obrazy rozruchowe nie są modyfikowane. Aby uzyskać szczegółowe informacje, zobacz [obrazów rozruchowych Zarządzaj](/sccm/osd/get-started/manage-boot-images#BKMK_BootImageDefault).

## <a name="software-updates"></a>Aktualizacje oprogramowania

### <a name="deploy-office-365-apps-to-clients"></a>Wdrażanie aplikacji Office 365 na klientów
Począwszy od wersji 1702, z poziomu pulpitu nawigacyjnego zarządzania klientami usługi Office 365, można uruchomić Instalatora 365 pakietu Office, który pozwala skonfigurować ustawienia instalacji usługi Office 365, pobierać pliki z pakietu Office sieci dostarczania zawartości (CDN) i wdrożyć pliki aplikacji w programie Configuration Manager. Aby uzyskać szczegółowe informacje, zobacz [aktualizuje zarządzania Office 365 ProPlus](/sccm/sum/deploy-use/manage-office-365-proplus-updates#deploy-office-365-apps).

> [!IMPORTANT]
> Aplikacji Office 365, który można utworzyć i wdrożyć za pomocą Kreatora aplikacji Office 365 w programie Configuration Manager nie jest automatycznie zarządzane przez program Configuration Manager do momentu włączenia **włączyć funkcję zarządzania Office 365 klienta ponownie** ustawienia agenta klienta aktualizacji oprogramowania. Aby uzyskać szczegółowe informacje, zobacz [informacje o ustawieniach klienta](/sccm/core/clients/deploy/about-client-settings).

### <a name="manage-express-installation-files-for-windows-10-updates"></a>Zarządzanie pliki instalacji ekspresowej aktualizacji systemu Windows 10
Począwszy od wersji 1702, Configuration Manager obsługuje pliki instalacji ekspresowej aktualizacji systemu Windows 10. Korzystając z obsługiwanych wersji systemu Windows 10, umożliwia ustawień programu Configuration Manager Pobierz tylko zmiany między bieżącym miesiącu systemu Windows 10 zbiorczej aktualizacji i aktualizacji w poprzednim miesiącu. Bez pliki instalacji ekspresowej programu Configuration Manager pobiera pełnego systemu Windows 10 aktualizacji zbiorczej (w tym wszystkie aktualizacje z poprzednich miesięcy) każdego miesiąca. Przy użyciu plików instalacji ekspresowej zapewnia mniejsze pliki do pobrania i skrócenie czasu instalacji na komputerach klienckich. Aby uzyskać szczegółowe informacje, zobacz [Zarządzanie pliki instalacji ekspresowej aktualizacji systemu Windows 10](/sccm/sum/deploy-use/manage-express-installation-files-for-windows-10-updates).


<!-- ## Reporting  -->

<!-- ## Inventory  -->

## <a name="mobile-device-management"></a>Zarządzanie urządzeniami przenośnymi

### <a name="android-and-ios-versions-are-no-longer-targetable-in-creation-wizards-for-hybrid-mdm"></a>Android i iOS wersje nie są już targetable w kreatorze tworzenia hybrydowe MDM

Począwszy od wersji 1702 do hybrydowego zarządzania urządzeniami przenośnymi (MDM), nie jest już konieczne docelowych określonych wersji Android i iOS przy tworzeniu nowych zasad i profile dla urządzeń zarządzanych przez usługę Intune. Zamiast tego można wybrać jedną z następujących typów urządzeń:

- Android
- KNOX Samsung Standard 4.0 i nowsze
- iPhone
- iPad

Ta zmiana dotyczy kreatorzy tworzenia następujące elementy:

- Elementy konfiguracji
- Zasady zgodności
- Profile certyfikatów
- Profile poczty e-mail
- Profile sieci VPN
- Profile sieci Wi-Fi

Z tą zmianą wdrożenia hybrydowego można zapewnić obsługę szybciej nowe wersje Android i iOS bez konieczności nowej wersji programu Configuration Manager lub rozszerzenia. Gdy nowa wersja jest obsługiwana w autonomicznej usługi Intune, użytkownicy będą mogli uaktualnić urządzeń przenośnych do nowszej wersji.

Aby zapobiec problemom podczas uaktualniania z poprzednich wersji programu Configuration Manager, wersje przenośnego systemu operacyjnego są nadal dostępne dla tych elementów na stronach właściwości. Jeśli nadal potrzebujesz pod kątem określonej wersji, można utworzyć nowy element, a następnie określ wersję docelową na stronie właściwości nowo utworzonego elementu.

### <a name="android-for-work-support"></a>Android obsługi pracy
Począwszy od 1702 hybrydowego zarządzania urządzeniami przenośnymi w usłudze Microsoft Intune obsługuje teraz Android rejestracji urządzeń w pracy i zarządzania. Zarządzane Android pracy urządzenia wskazówki:

- [Rejestrowanie pracy urządzeń Android](/sccm/mdm/deploy-use/enroll-hybrid-android#enable-android-enrollment)
- [Zatwierdzanie i wdrażanie Android dla aplikacji do pracy](/sccm/mdm/deploy-use/creating-android-applications#approve-and-deploy-android-for-work-apps)
- [Tworzenie elementów konfiguracji dla systemu Android do pracy](/sccm/mdm/deploy-use/create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client#android-for-work-configuration-items)
- [Selektywne czyszczenie danych w systemie Android pracy urządzeń](/sccm/mdm/deploy-use/wipe-lock-reset-devices#selective-wipe)
- [Profile poczty e-mail dla systemu Android do pracy](/sccm/mdm/deploy-use/create-exchange-activesync-profiles)
- [Zasady zgodności dla systemu Android do pracy](/sccm/mdm/deploy-use/create-compliance-policy)


### <a name="deploy-volume-purchased-ios-apps-to-device-collections"></a>Wdrażanie aplikacji iOS kupionymi woluminu do kolekcji urządzeń

Teraz można wdrożyć licencjonowane aplikacje na urządzeniach, jak i użytkowników. W zależności od funkcji aplikacji do obsługi urządzeń licencjonowania odpowiedniej licencji będzie wymagana podczas wdrażania, w następujący sposób:

|||||
|-|-|-|-|
|Wersja programu Configuration Manager|Aplikacja obsługuje licencjonowania urządzenia?|Typ kolekcji wdrożenia|Oświadczeniem licencji|
|Starsze niż 1702|Tak|Użytkownik|Licencja użytkownika|
|Starsze niż 1702|Nie|Użytkownik|Licencja użytkownika|
|Starsze niż 1702|Tak|Urządzenie|Licencja użytkownika|
|Starsze niż 1702|Nie|Urządzenie|Licencja użytkownika|
|1702 i nowsze|Tak|Użytkownik|Licencja użytkownika|
|1702 i nowsze|Nie|Użytkownik|Licencja użytkownika|
|1702 i nowsze|Tak|Urządzenie|Licencję urządzenia|
|1702 i nowsze|Nie|Urządzenie|Licencja użytkownika|

Aby uzyskać więcej informacji o aplikacjach iOS kupionymi woluminu, zobacz [zarządzania aplikacjami zakupione woluminu iOS](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps).

### <a name="support-for-ios-volume-purchase-program-for-education"></a>Obsługa iOS Program zakupu woluminu edukacja

Teraz można również wdrażać i śledzić aplikacji uzyskany z iOS Program zakupu zbiorczej dla instytucji edukacyjnych.
Aby uzyskać więcej informacji o aplikacjach iOS kupionymi woluminu, zobacz [zarządzania aplikacjami zakupione woluminu iOS](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps).

### <a name="support-for-multiple-volume-purchase-program-tokens"></a>Obsługa wielu tokenów program woluminu zakupu

Można teraz skojarzyć wiele tokenów program zakupu woluminu Apple z programu Configuration Manager.
Aby uzyskać więcej informacji o aplikacjach iOS kupionymi woluminu, zobacz [zarządzania aplikacjami zakupione woluminu iOS](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps).

### <a name="support-for-line-of-business-apps-in-windows-store-for-business"></a>Obsługa aplikacji biznesowych w Sklepie Windows dla firm

Niestandardowe aplikacje biznesowe w Sklepie Windows dla firm mogą teraz synchronizować.

### <a name="conditional-access-device-compliance-policy-improvements"></a>Ulepszenia zasady zgodności urządzeń dostępu warunkowego

Dostępny jest nową regułę zasad zgodności urządzeń blokowania dostępu do zasobów firmy, które obsługują dostęp warunkowy, gdy użytkownicy korzystają z aplikacji, które są częścią listę niezgodnych aplikacji. Lista niezgodnych aplikacji może być zdefiniowany przez administratora podczas dodawania nowej reguły zgodne **aplikacji, których nie można zainstalować**. Ta reguła wymaga administratora, aby wprowadzić **Nazwa aplikacji**, **Identyfikatora aplikacji**i **wydawcę aplikacji** (opcjonalnie), dodając do listy niezgodnych aplikacji. To ustawienie dotyczy tylko systemów iOS i android.

Ponadto pomaga organizacjom uniknięcie wycieku danych za pośrednictwem niezabezpieczonej aplikacje i zapobiec zużycie nadmiernej ilości danych za pośrednictwem niektórych aplikacji.

- Dowiedz się więcej [działanie zasadami zgodności urządzeń](/sccm/mdm/deploy-use/device-compliance-policies).
- Dowiedz się więcej [jak utworzyć zasady zgodności urządzeń](/sccm/mdm/deploy-use/create-compliance-policy).

### <a name="new-mobile-threat-defense-monitoring-tools"></a>Przed zagrożeniami Mobile nowe narzędzia do monitorowania

Począwszy od wersji 1702, możesz mają nowe możliwości monitorowania stanu zgodności z dostawcą usług przed zagrożeniami Mobile.

- Dowiedz się więcej [sposób monitorowania zgodności przed zagrożeniami Mobile](https://docs.microsoft.com/sccm/mdm/deploy-use/monitor-mobile-threat-defense-compliance).

## <a name="protect-devices"></a>Ochrony urządzeń

### <a name="detect-outdated-antimalware-client-versions"></a>Wykryj wersje klienta nieaktualne ochrony przed złośliwym oprogramowaniem
Począwszy od wersji 1702, można skonfigurować alert, aby upewnić się, że klienci ochrony punktu końcowego nie są nieaktualne. Aby uzyskać więcej informacji, zobacz [alertów dla klienta nieaktualne przed złośliwym oprogramowaniem](/sccm/protect/deploy-use/endpoint-configure-alerts#detect-outdated-antimalware-client-versions).

### <a name="device-health-attestation-updates"></a>Aktualizacje zaświadczania kondycji urządzeń
Usługa zaświadczania kondycji urządzeń dla lokalnych klienci mogą teraz skonfigurowane i zarządzane z punktu zarządzania. Aby uzyskać więcej informacji, zobacz [zaświadczania kondycji](/sccm/core/servers/manage/health-attestation).

### <a name="certificate-profiles-for-windows-hello-for-business"></a>Profile certyfikatów dla systemu Windows Hello dla firm

Jeśli użytkownik zamierza przechowywać profili certyfikatów w Windows Hello dla kontenera kluczy biznesowych i EKU logowania karty inteligentnej korzysta z profilu certyfikatu, należy skonfigurować uprawnienia dla klucza rejestracji upewnić się, że certyfikat zostanie zweryfikowany poprawnie.
Aby uzyskać więcej informacji, zobacz [Windows Hello ustawień Business](/sccm/protect/deploy-use/windows-hello-for-business-settings).

### <a name="new-windows-hello-for-business-notification-for-end-users"></a>Nowy Windows Hello Powiadomienia biznesowe dla użytkowników końcowych
Nowe powiadomienie systemu Windows 10 informuje użytkownicy końcowi muszą zabrać dodatkowe akcje do wykonania Windows Hello Instalatora biznesowych (na przykład ustawienie kodu PIN).

