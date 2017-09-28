---
title: Nowa wersja 1702 | Dokumentacja firmy Microsoft
description: "Uzyskiwanie szczegółowych informacji dotyczących zmian i nowych możliwości wprowadzonych w wersji 1702 programu System Center Configuration Manager."
ms.custom: na
ms.date: 05/02/2017
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 409e26e1-7716-4f1d-a0ee-34feabf20792
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: ff7f6c3b9f183502c95a2c551b1131c5abf1dd90
ms.sourcegitcommit: 474e6ddbaaeac4ba17d8172321e08deeb0140d0a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2017
---
# <a name="what39s-new-in-version-1702-of-system-center-configuration-manager"></a>Jaki &#39; s nowego w wersji 1702 programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Zaktualizuj 1702 dla bieżącej gałęzi programu System Center Configuration Manager jest dostępna jako aktualizacja w konsoli dla zainstalowanych wcześniej lokacji, w których jest uruchomiona wersja 1602, 1606 lub 1610. Jest również dostępny jako wersji linii bazowej, używanego podczas instalowania nowego wdrożenia.

> [!TIP]  
> Aby zainstalować nową lokację, należy użyć wersji bazowej programu Configuration Manager.  
>  Dowiedz się więcej o:    
>   - [Instalowanie nowej lokacji](https://technet.microsoft.com/library/mt590197.aspx)  
>   - [Instalowanie aktualizacji w lokacjach](https://technet.microsoft.com/library/mt607046.aspx)  
>   - [Wersje linii bazowej i aktualizacji](/sccm/core/servers/manage/updates#a-namebkmkbaselinesa-baseline-and-update-versions)  

Poniższe sekcje zawierają szczegółowe informacje dotyczące zmian i nowych możliwości wprowadzonych w wersji 1702 programu Configuration Manager.  

## <a name="deprecated-features-and-operating-systems"></a>Przestarzałe funkcje i systemów operacyjnych
Dowiedz się więcej o obsługę zmiany przed ich wdrożeniem w [usunięte i przestarzałe funkcje](/sccm/core/plan-design/changes/removed-and-deprecated-features).

Wersja 1702 porzucania obsługę następujących produktów:
- **SQL Server 2008 R2**, serwerów baz danych lokacji. Zaniechania obsługi został [najpierw ogłoszenia](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-support-for-sql-server-versions-as-a-site-database) na 10 lipca 2015 r. Ta wersja programu SQL Server jest obsługiwany w przypadku korzystania z wersji programu Configuration Manager, poprzedzające wersję 1702.
- **Windows Server 2008 R2**dla serwerów systemu lokacji i większości ról systemu lokacji. Zaniechania obsługi został [najpierw ogłoszenia](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-operating-systems) na 10 lipca 2015 r. Ta wersja systemu Windows jest obsługiwany w przypadku korzystania z wersji programu Configuration Manager, poprzedzające wersję 1702.  
- **Windows Server 2008**dla serwerów systemu lokacji i większości ról systemu lokacji. Zaniechania obsługi został [najpierw ogłoszenia](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-operating-systems) na 10 lipca 2015 r.
- **Windows XP Embedded**, jako systemu operacyjnego klienta. Oczekiwany był [najpierw ogłoszenia](/sccm/core/plan-design/changes/removed-and-deprecated-features#deprecated-operating-systems) na 10 lipca 2015 r. Ta wersja systemu Windows jest obsługiwany w przypadku korzystania z wersji programu Configuration Manager, poprzedzające wersję 1702.




## <a name="site-infrastructure"></a>Infrastruktura lokacji

### <a name="improvements-for-in-console-search"></a>Ulepszenia wyszukiwania w konsoli
Ulepszenia za pomocą wyszukiwania w konsoli programu Configuration Manager są następujące:
 - **Ścieżka obiektu:**  
  Wiele obiektów obsługuje teraz kolumny o nazwie **ścieżki obiektu**.  Podczas wyszukiwania i zawierało tej kolumny w wynikach wyświetlania, można wyświetlić ścieżkę do każdego obiektu. Na przykład, jeśli podczas wykonywania wyszukiwania dla aplikacji w węźle aplikacje są również wyszukiwanie węzły podrzędne *ścieżki obiektu* kolumny w okienku wyników zostanie wyświetlona ścieżka do każdego obiektu, który jest zwracany.   

- **Zachowanie szukany tekst:**  
  Podczas wprowadzania tekstu w polu tekstowym wyszukiwania, a następnie przełączać się między wyszukiwanie węzła podrzędnego i bieżącego węzła, tekst, który został wpisany teraz utrwalić i pozostają dostępne dla nowego wyszukiwania bez konieczności ponownego wprowadzania go.

- **Zachowanie zdecydować, czy wyszukiwanie węzły podrzędne:**  
 Wybraną opcję wyszukiwania *bieżącego węzła* lub *wszystkie węzły podrzędne* teraz będzie nadal występować po zmianie pracujesz w węźle. To nowe zachowanie oznacza, że nie muszą stale zresetować tej decyzji podczas przenoszenia wokół konsoli. Domyślnie po otwarciu konsoli jest opcja wyszukiwania z bieżącego węzła.


### <a name="send-feedback-from-the-configuration-manager-console"></a>Wyślij opinię z konsoli programu Configuration Manager

 Opcje opinii w konsoli aby wysłać opinię bezpośrednio do zespołu deweloperów.

 Można znaleźć **opinii** opcji:
 -  Na Wstążce, w lewym karcie Narzędzia główne w każdym węźle.  
    ![Wstążka](./media/feedback-home.png)

 -  Po kliknięciu prawym przyciskiem myszy dowolnego obiektu w konsoli.   
     ![Kopiowanie kliknięcia](./media/feedback-option.png)   

 Wybieranie **opinii** Otwiera przeglądarkę, aby [witryny sieci Web programu Configuration Manager UserVoice opinii](https://go.microsoft.com/fwlink/?linkid=617029).


###  <a name="changes-for-updates-and-servicing"></a>Zmiany dotyczące aktualizacji i obsługi
Dostępne są następujące zmiany w aktualizacji i obsługi:

- **Lokalizacja węzła**   
  Po zainstalowaniu wersji 1702, **aktualizacje i obsługa** węzeł jest wyświetlany jako węzeł najwyższego poziomu w obszarze **administracji**. Nie jest już elementem podrzędnym poniżej **usługi w chmurze**.

- **Nowe stany aktualizacji**  
  Po wyświetleniu dostępne aktualizacje w konsoli, istnieją dwie nowe stany:  
  - **Dostępne do instalacji** — jest to aktualizacja, które zostały pobrane i są gotowe do zainstalowania.
  - **Gotowy do pobrania** — ta aktualizacja jest dostępna, ale nie została pobrana. Można wybrać pobrać tę aktualizację, ale została zastąpiona przez najnowszą aktualizację.


- **Prostsze opcje aktualizacji**  
  Przy następnym infrastruktury kwalifikuje się w przypadku aktualizacji co najmniej dwa pobrać tylko najnowszą aktualizację. Na przykład, jeśli bieżąca wersja lokacji jest dwa lub więcej starsze niż najnowszej wersji, która jest dostępna, tylko że najnowsza wersja aktualizacji jest pobierany automatycznie.  

  Możesz pobrać i zainstalować inne dostępne aktualizacje, nawet wtedy, gdy nie są one najbardziej aktualnej wersji. Jeśli aktualizacja starsze otrzyma ostrzeżenie, że aktualizacja została zastąpiona nowszą. Aby pobrać aktualizację, która jest *dostępne do pobrania*, wybierz aktualizację, w konsoli, a następnie kliknij przycisk **Pobierz**.

- **Ulepszone czyszczenie starszych aktualizacji**   
  Dodano funkcję automatycznego czyszczenia, która usuwa zbędne pobrane pliki z folderu "EasySetupPayload" na serwerze lokacji. Ponieważ jest to wprowadzonym w wersji 1702, oczyszczania zaczyna działać po zainstalowaniu kolejnych aktualizacji, takich jak pakiet zbiorczy aktualizacji lub wersji przyszłej aktualizacji.  


### <a name="data-warehouse-service-point"></a>Punkt usługi magazynu danych
 Korzystanie z punktu usługi Magazyn danych, do przechowywania i raport dotyczący długoterminowe dane historyczne dla danego wdrożenia programu Configuration Manager.

 Magazyn danych obsługuje maksymalnie 2 TB danych z sygnaturami czasowymi, śledzenie zmian. Przechowywanie danych odbywa się przez automatyczne synchronizacje z bazy danych lokacji programu Configuration Manager do bazy danych magazynu danych. Te informacje są dostępne z punktu usług Reporting Services.

 Aby uzyskać więcej informacji, zobacz [punktu usługi Magazyn danych](/sccm/core/servers/manage/data-warehouse).


### <a name="peer-cache-improvements"></a>Ulepszenia pamięci podręcznej elementów równorzędnych
 Począwszy od wersji 1702 komputerze źródła równorzędnej pamięci podręcznej żądania zawartości podczas odrzuci komputer źródłowy równorzędnej pamięci podręcznej spełnia żadnego z następujących warunków:  
  -  Jest w trybie niskim poziomie naładowania baterii.
  -  Obciążenie procesora CPU przekracza 80% w czasie żądanej zawartości.
  -  We/Wy dysku ma *AvgDiskQueueLength* przekraczający 10.
  -  Brak dostępnego połączenia z tym komputerem.   
Aby uzyskać więcej informacji, zobacz **ograniczony dostęp do źródła równorzędnej pamięci podręcznej** w [buforowania równorzędnego klientów programu Configuration Manager](/sccm/core/plan-design/hierarchy/client-peer-cache).   

Ponadto trzy nowe raporty są dodawane do punktu raportowania. Te raporty można użyć, aby poznać więcej szczegółów na temat odrzuconych żądań zawartości, w tym granic, których uczestniczyła grupy, komputera i zawartości. Zobacz [monitorowanie](/sccm/core/plan-design/hierarchy/client-peer-cache#monitoring) w temacie równorzędnej pamięci podręcznej.

### <a name="content-library-cleanup-tool"></a>Narzędzia do oczyszczania biblioteki zawartości
 Użyj [narzędzia do oczyszczania biblioteki zawartości](/sccm/core/plan-design/hierarchy/content-library-cleanup-tool) Aby usunąć zawartość z punktów dystrybucji, gdy zawartość nie jest już skojarzony z aplikacją.


### <a name="use-the-oms-connector-with-the-azure-government-cloud"></a>Korzystania z łącznika OMS z chmury Azure dla instytucji rządowych
Łącznik OMS służy do nawiązania połączenia analizy dzienników OMS w chmurze Microsoft Azure dla instytucji rządowych. Należy zmodyfikować plik konfiguracji, przed zainstalowaniem łącznika OMS, tak aby łącznik może współpracować z chmury dla instytucji rządowych. Aby uzyskać więcej informacji, zobacz [korzystania z łącznika OMS z chmury Azure dla instytucji rządowych](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite#fairfaxconfig).

### <a name="software-update-points-are-added-to-boundary-groups"></a>Punkty aktualizacji oprogramowania są dodawane do grupy granic
Począwszy od wersji 1702, klienci używają grup granic w celu znalezienia punktu aktualizacji oprogramowania, a powrotu i Znajdź nowej aktualizacji oprogramowania punktu, jeśli ich aktualny plan nie jest już dostępny. Punkty aktualizacji oprogramowania można dodać do różnych grup granic do serwerów, które klient można znaleźć formantu. Aby uzyskać więcej informacji, zobacz [punktów aktualizacji oprogramowania](/sccm/core/servers/deploy/configure/boundary-groups#software-update-points) w [konfigurowania grup granic](/sccm/core/servers/deploy/configure/boundary-groups) tematu.


<!-- ## Migration  -->

<!-- ## Client management  -->

## <a name="compliance-settings"></a>Ustawienia zgodności

### <a name="new-compliance-settings-for-ios"></a>Nowe ustawienia zgodności dla systemu iOS

Dodaliśmy wiele nowych ustawień dla urządzeń z systemem iOS do zgodne z tymi, które są dostępne w usłudze Microsoft Intune.
Aby uzyskać listę wszystkich dostępnych ustawień, zobacz [tworzenie elementów konfiguracji dla systemów iOS i Mac OS X urządzeń zarządzanych przez usługę Intune](/sccm/mdm/deploy-use/create-configuration-items-for-ios-and-mac-os-x-devices-managed-without-the-client).


## <a name="application-management"></a>Zarządzanie aplikacjami

### <a name="improved-support-for-windows-store-for-business-apps"></a>Ulepszona obsługa aplikacji biznesowych dla Sklepu Windows

Teraz można wdrożyć licencjonowane aplikacje ze Sklepu Windows dla firm komputerów z systemem Windows 10 można zarządzać za pomocą klienta programu Configuration Manager.
Aby uzyskać więcej informacji, zobacz [Zarządzanie aplikacjami ze Sklepu Windows dla firm](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business).

### <a name="check-for-running-executable-files-before-installing-an-application"></a>Sprawdź, czy uruchamianie plików wykonywalnych przed zainstalowaniem aplikacji

W **właściwości** okno dialogowe wdrożenia wpisz na **zainstalować zachowanie** kartę, można teraz określić jedną więcej pliki wykonywalne, jeśli uruchomiony, blokuje instalację typu wdrożenia. Użytkownik musi zamknąć plik wykonywalny uruchomiona (lub może zostać zamknięty w automatycznie w przypadku wdrożeń z celem wymagane) przed wdrożeniem można było zainstalować typ.

Jeśli aplikacja została wdrożona jako **dostępne**i użytkownik końcowy próbuje zainstalować aplikację, będą oni musieli podać do Zamknij wszystkie uruchomione pliki wykonywalne określona zanim można kontynuować instalacji.

Jeśli aplikacja została wdrożona jako **wymagane**wraz z opcją **automatycznie Zamknij wszystkie uruchomione pliki wykonywalne określone na karcie zachowanie instalacji okna dialogowego właściwości typu wdrożenia** jest zaznaczone, zobaczą okno dialogowe, które informuje, że pliki wykonywalne określonego zostaną automatycznie zamknięte po osiągnięciu ostatecznego terminu instalacji aplikacji.

### <a name="app-management-improvements-for-hybrid-mdm"></a>Ulepszenia zarządzania aplikacji hybrydowego zarządzania urządzeniami Przenośnymi

- [Wdrażanie aplikacji dla systemu iOS zakupionymi zbiorczo do kolekcji urządzeń](#deploy-volume-purchased-ios-apps-to-device-collections)
- [Obsługa systemu iOS Volume Purchase Program dla instytucji edukacyjnych](#support-for-ios-volume-purchase-program-for-education)
- [Obsługa wielu tokenów program zakupów zbiorczych](#support-for-multiple-volume-purchase-program-tokens)


## <a name="operating-system-deployment"></a>Wdrożenie systemu operacyjnego

### <a name="expire-stand-alone-media"></a>Nośnik samodzielny wygaśnie
Podczas tworzenia nośnika autonomicznego, istnieją nowe opcje można ustawić opcjonalny daty rozpoczęcia i wygaśnięcia na nośniku. Te ustawienia są domyślnie wyłączone. Dane są porównywane z czasem systemowym na komputerze przed uruchomieniem nośnika autonomicznego. Gdy czas systemowy jest wcześniejsza niż godzina rozpoczęcia lub późniejsza niż godzina wygaśnięcia, nośnika samodzielnego nie jest uruchomiona. Te opcje są również dostępne za pomocą polecenia cmdlet New-CMStandaloneMedia środowiska PowerShell. Aby uzyskać więcej informacji, zobacz [tworzenia nośnika samodzielnego](/sccm/osd/deploy-use/create-stand-alone-media).

### <a name="package-id-displayed-in-task-sequence-steps"></a>Identyfikator pakietu wyświetlany w krokach sekwencji zadań
Dowolny etap sekwencji zadań odwołuje się do pakietu, pakietu sterowników, obrazu systemu operacyjnego, obraz rozruchowy lub pakiet uaktualnienia systemu operacyjnego będzie teraz wyświetlany identyfikator pakietu odwołuje się do obiektu. Gdy krok sekwencji zadań odwołuje się do aplikacji, będą wyświetlane identyfikatora obiektu.

### <a name="support-for-additional-content-in-stand-alone-media"></a>Obsługę dodatkowej zawartości w nośniku samodzielnym
Dodatkowa zawartość jest teraz obsługiwana w przypadku nośników autonomicznych. Możesz wybrać dodatkowe pakiety, pakiety sterowników i aplikacji do przemieszczony na nośniku oraz zawartość, do którego odwołuje się sekwencja zadań. Wcześniej tylko zawartość, do którego odwołuje się sekwencja zadań została umieszczone na nośniku autonomicznym. Aby uzyskać więcej informacji, zobacz [tworzenia nośnika samodzielnego](/sccm/osd/deploy-use/create-stand-alone-media).

### <a name="hardware-inventory-collects-uefi-information"></a>Spisu sprzętu zbiera informacje z interfejsem UEFI
Nową klasę spisu sprzętu (**SMS_Firmware**), a właściwość (**UEFI**) są dostępne pomóc w określeniu, czy komputer jest uruchamiany w trybie UEFI. Gdy komputer jest uruchamiany w trybie UEFI, **UEFI** właściwość jest ustawiona na **TRUE**. Ta opcja jest włączona w spisie sprzętu, domyślnie. Aby uzyskać więcej informacji dotyczących zapasów sprzętu, zobacz [jak skonfigurować spis sprzętu](/sccm/core/clients/manage/inventory/configure-hardware-inventory).

### <a name="improvements-to-software-center-warning-messages-for-high-impact-task-sequences"></a>Ulepszenia Centrum oprogramowania ostrzeżenia o dużym znaczeniu sekwencji zadań
Ta wersja zawiera wprowadzono następujące ulepszenia Centrum oprogramowania ostrzeżenia o dużym znaczeniu wdrożenia sekwencji zadań:

- W oknie właściwości dla sekwencji zadań można teraz skonfigurować wszystkie sekwencje zadań, w tym sekwencji zadań systemu operacyjnego jako wdrożenie wysokiego ryzyka. Wszystkie sekwencje zadań, która spełnia określone warunki automatycznie jest zdefiniowany jako dużym znaczeniu. Aby uzyskać więcej informacji, zobacz [zarządzania wdrożeniami o wysokim ryzyku](/sccm/protect/understand/settings-to-manage-high-risk-deployments).
- W oknie właściwości dla sekwencji zadań można użyć domyślnego komunikatu powiadomienia lub utworzyć własne niestandardowe powiadomienie w przypadku wdrożeń o dużym znaczeniu.
- We właściwościach sekwencji zadań można skonfigurować właściwości, które obejmują upewnij ponownego uruchomienia wymaganych, Centrum oprogramowania rozmiar pobierania sekwencji zadań i szacowany czas wykonywania.
- W komunikacie wdrożenia poważnych domyślne w miejscu uaktualnia teraz stanów automatycznie migracji aplikacji, danych i ustawień. Wcześniej, domyślną wiadomość do wszelkich instalacji systemu operacyjnego wskazuje, że wszystkie aplikacje, dane i ustawienia, może spowodować utratę, który nie jest spełniony dla uaktualnienia w miejscu.

Aby uzyskać więcej informacji, zobacz [Konfigurowanie ustawień sekwencji zadań o dużym wpływie na działanie](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#set-a-task-sequence-as-a-high-impact-task-sequence)

### <a name="return-to-previous-page-when-a-task-sequence-fails"></a>Powrót do poprzedniej strony, gdy sekwencja zadań nie powiodło się.
Można teraz wróć do poprzedniej strony po uruchomieniu sekwencji zadań i awarii. Przed tą wersją trzeba było ponownego uruchomienia sekwencji zadań, jeśli wystąpił błąd. Na przykład można użyć **Wstecz** przycisk w następujących scenariuszach:

- Gdy komputer jest uruchamiany w środowisku Windows PE, dialogowym bootstrap sekwencji zadań może być wyświetlany, zanim sekwencja zadań będzie dostępna. Po kliknięciu przycisku Dalej w tym scenariuszu sekwencja zadań na ostatniej stronie wyświetla komunikat, że nie dostępnych sekwencji zadań. Teraz, możesz kliknąć **Wstecz** ponowić wyszukiwanie uzyskać dostępne sekwencje zadań. Ten proces można powtarzać do czasu udostępnienia sekwencji zadań.
- Po uruchomieniu sekwencji zadań, ale zależnych pakietów zawartości nie są jeszcze dostępne w punktach dystrybucji, sekwencja zadań kończy się niepowodzeniem. Możesz teraz dystrybuować brakującą zawartość (jeśli go nie została jeszcze rozesłana) lub poczekaj, aż zawartości, które mają być dostępne w punktach dystrybucji, a następnie kliknij **Wstecz** mają wyszukiwania sekwencji zadań ponownie dla zawartości.

### <a name="pre-cache-content-for-available-deployments-and-task-sequences"></a>Wstępne wypełnienie pamięci podręcznej dla wdrożeń dostępnych i sekwencji zadań
Począwszy od wersji 1702, w przypadku wdrożeń dostępnych sekwencji zadań, można użyć wstępne wypełnienie pamięci podręcznej. Wstępne wypełnienie pamięci podręcznej udostępnia opcję, aby umożliwić klientom pobieranie tylko zawartość dotyczy zaraz po otrzymaniu wdrożenia. W związku z tym, kiedy użytkownik kliknie **zainstalować** w programie Software Center zawartości są gotowe, a instalacja uruchamia się szybko, ponieważ zawartość znajduje się na lokalnym dysku twardym. Aby uzyskać więcej informacji, zobacz [skonfigurować wstępne wypełnienie pamięci podręcznej](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#configure-pre-cache-content).

### <a name="convert-from-bios-to-uefi-during-an-in-place-upgrade"></a>Konwertowanie systemu BIOS na UEFI podczas uaktualniania w miejscu
Windows 10 twórców aktualizacji wprowadzono narzędzie konwersji proste automatyzuje proces ponownego podziału dysku twardego z obsługą interfejsu UEFI sprzętu i integruje narzędzia konwersji system Windows 7 do procesu uaktualniania w miejscu systemu Windows 10. Połączenie to narzędzie z sekwencji zadań uaktualniania systemu operacyjnego i narzędzie OEM, który konwertuje oprogramowanie układowe BIOS z interfejsem UEFI, można przekonwertować komputerów z systemem BIOS na UEFI podczas uaktualniania w miejscu do systemu Windows 10 twórców aktualizacji. Aby uzyskać więcej informacji, zobacz [zadania sekwencji kroki, aby zarządzać systemu BIOS z interfejsem UEFI konwersji](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#convert-from-bios-to-uefi-during-an-in-place-upgrade).

### <a name="improvements-to-the-install-applications-task-sequence-step"></a>Ulepszenia dotyczące instalowania aplikacji sekwencji zadań krok
Tej wersji wprowadzono następujące ulepszenia:
- Zwiększyć maksymalną liczbę aplikacji, które można zainstalować do 99 w **instalowanie aplikacji** krok sekwencji zadań. Poprzednie maksymalną liczbę został 9 aplikacji.
- Po dodaniu aplikacji do **instalowanie aplikacji** krok sekwencji zadań w edytorze sekwencji zadań, możesz teraz wybrać wiele aplikacji z **wybierz aplikację do zainstalowania** okienka.

### <a name="improvements-to-the-auto-apply-driver-task-sequence"></a>Ulepszenia dotyczące sekwencji zadań automatycznie Zastosuj sterowniki
Nowe zmienne sekwencji zadań są teraz dostępne do konfigurowania wartość limitu czasu w kroku sekwencji zadań automatycznie Zastosuj sterownik podczas tworzenia żądania HTTP katalogu. Dostępne są następujące zmienne i wartości domyślnych (w sekundach):
   - SMSTSDriverRequestResolveTimeOut  
     Wartość domyślna: 60
   - SMSTSDriverRequestConnectTimeOut  
     Wartość domyślna: 60
   - SMSTSDriverRequestSendTimeOut  
     Wartość domyślna: 60
   - SMSTSDriverRequestReceiveTimeOut  
     Wartość domyślna: 480

### <a name="windows-10-adk-tracked-by-build-version"></a>Windows 10 ADK śledzone przez wersję kompilacji
Zestaw Windows 10 ADK teraz jest śledzony przez wersję kompilacji, aby zapewnić więcej dostępnych możliwości dostosowywania obrazów rozruchowych systemu Windows 10. Na przykład jeśli witryna korzysta z systemu Windows ADK dla systemu Windows 10, wersji 1607, tylko obrazy rozruchowe z wersją 10.0.14393 można dostosować w konsoli. Aby uzyskać więcej informacji dotyczących dostosowywania wersje środowiska WinPE, zobacz [dostosowywanie obrazów rozruchowych](/sccm/osd/get-started/customize-boot-images).

### <a name="default-boot-image-source-path-can-no-longer-be-changed"></a>Nie można zmienić ścieżki źródłowej obrazu rozruchowego domyślne
Domyślne obrazy rozruchowe są zarządzane przez program Configuration Manager i nie można zmienić ścieżki źródłowej obrazu rozruchowego domyślne, w konsoli programu Configuration Manager lub przy użyciu zestawu SDK programu Configuration Manager. Możesz skonfigurować ścieżkę źródła niestandardowego dla niestandardowych obrazów rozruchowych.

### <a name="default-boot-images-are-regenerated-after-upgrading-configuration-manager-to-a-new-version"></a>Domyślne obrazy rozruchowe są generowane po uaktualnieniu do nowej wersji programu Configuration Manager
Począwszy od tej wersji, podczas uaktualniania wersji zestawu Windows ADK i użyj aktualizacje i obsługa, aby zainstalować najnowszą wersję programu Configuration Manager, Configuration Manager generuje domyślne obrazy rozruchowe. W tym nową wersją środowiska Windows PE z zaktualizowany zestaw Windows ADK, nowej wersji klienta programu Configuration Manager, sterowniki, dostosowywanie, itp. Niestandardowe obrazy rozruchowe nie są modyfikowane. Aby uzyskać więcej informacji, zobacz [zarządzanie obrazami rozruchowymi](/sccm/osd/get-started/manage-boot-images#BKMK_BootImageDefault).

## <a name="software-updates"></a>Aktualizacje oprogramowania

### <a name="deploy-office-365-apps-to-clients"></a>Wdrażanie aplikacji usługi Office 365 na klientach
Począwszy od wersji 1702, z poziomu pulpitu nawigacyjnego zarządzania klienta usługi Office 365, możesz uruchomić Instalatora 365 pakietu Office, które umożliwia konfigurowanie ustawień instalacji usługi Office 365, pobierania plików z pakietu Office sieci dostarczania zawartości (CDN) i wdrożenia plików jako aplikacji w programie Configuration Manager. Aby uzyskać więcej informacji, zobacz [aktualizacji z zarządzania usługi Office 365 ProPlus](/sccm/sum/deploy-use/manage-office-365-proplus-updates#deploy-office-365-apps).

> [!IMPORTANT]
> Tworzenie i wdrażanie za pomocą Kreatora aplikacji pakietu Office 365 w Menedżerze konfiguracji aplikacji usługi Office 365 nie jest automatycznie zarządzane przez program Configuration Manager do momentu włączenia **Włącz zarządzanie Office 365 klienta ponownie** ustawienia agenta klienta aktualizacji oprogramowania. Aby uzyskać więcej informacji, zobacz [informacje o ustawieniach klienta](/sccm/core/clients/deploy/about-client-settings).

### <a name="manage-express-installation-files-for-windows-10-updates"></a>Zarządzanie plikami instalacji ekspresowej aktualizacji systemu Windows 10
Począwszy od wersji 1702, program Configuration Manager obsługuje pliki instalacji ekspresowej aktualizacji systemu Windows 10. Korzystając z obsługiwanej wersji systemu Windows 10, umożliwia ustawień programu Configuration Manager Pobierz tylko zmiany między bieżącego miesiąca systemu Windows 10 aktualizacji zbiorczej i aktualizacją poprzedniego miesiąca. Bez plików instalacji ekspresowej programu Configuration Manager pobiera pełnego systemu Windows 10 aktualizacji zbiorczej (w tym wszystkie aktualizacje z ostatnich miesięcy) każdego miesiąca. Przy użyciu plików instalacji ekspresowej zapewnia mniejsze pliki do pobrania i instalacji szybsze na klientach. Aby uzyskać więcej informacji, zobacz [Zarządzanie plików instalacji ekspresowej, aktualizacji systemu Windows 10](/sccm/sum/deploy-use/manage-express-installation-files-for-windows-10-updates).


<!-- ## Reporting  -->

<!-- ## Inventory  -->

## <a name="mobile-device-management"></a>Zarządzanie urządzeniami przenośnymi

### <a name="android-and-ios-versions-are-no-longer-targetable-in-creation-wizards-for-hybrid-mdm"></a>Wersje systemów android i iOS nie są już targetable w kreatorach tworzenia dla hybrydowego zarządzania urządzeniami Przenośnymi

Począwszy od wersji 1702 hybrydowego zarządzania urządzeniami przenośnymi (MDM), nie trzeba docelowych określonych wersji systemu Android i iOS, podczas tworzenia nowych zasad i profilów dla urządzeń zarządzanych przez usługę Intune. Zamiast tego należy wybrać jedną z następujących typów urządzeń:

- Android
- Samsung KNOX Standard 4.0 lub nowszy
- urządzenia iPhone
- iPad

Ta zmiana wpływa na kreatorów tworzenia następujące elementy:

- Elementy konfiguracji
- Zasady zgodności
- Profile certyfikatów
- Profile poczty e-mail
- Profile sieci VPN
- Profile sieci Wi-Fi

Dzięki tej zmianie hybrydowych wdrożeń można zapewnić obsługę szybciej nowe wersje systemów Android i iOS bez konieczności nową wersję programu Configuration Manager lub rozszerzenia. Gdy nowa wersja jest obsługiwana w autonomicznej usługi Intune, użytkownicy będą mogli uaktualnić swoje urządzenia przenośne do tej wersji.

Aby zapobiec problemom podczas uaktualniania z wcześniejszych wersji programu Configuration Manager, wersje systemów operacyjnych urządzeń przenośnych są nadal dostępne na stronach właściwości dla tych elementów. Jeśli nadal potrzebujesz pod kątem określonej wersji, można utworzyć nowego elementu, a następnie określ wersję docelową na stronie właściwości nowo utworzonego elementu. 

> [!NOTE]
> Ostatnia wersja przenośnego systemu operacyjnego, dostępnych na stronach właściwości ma zastosowanie do tej wersji i wszystkie kolejne wersje. Strony właściwości podanie przeznaczonych dla systemów operacyjnych starszych niż 7 dla systemu Android i iOS 10 następujące opcje: 
> - **Android 7 lub nowszej**
> - **Wszystkie z systemem iOS 10 i wyższe urządzenia iPhone i iPod touch**
> - **Wszystkie z systemem iOS 10 i wyższe urządzenia iPad**

### <a name="android-for-work-support"></a>Android obsługę pracy
Począwszy od 1702 hybrydowego zarządzania urządzeniami przenośnymi w usłudze Microsoft Intune obsługuje teraz system Android rejestracji urządzeń w pracy i zarządzania. Android zarządzanych orientacji urządzenia roboczych:

- [Rejestrowanie pracy urządzeń systemu Android](/sccm/mdm/deploy-use/enroll-hybrid-android#enable-android-enrollment)
- [Zatwierdzanie i wdrażanie systemu Android dla aplikacji służbowych](/sccm/mdm/deploy-use/creating-android-applications#approve-and-deploy-android-for-work-apps)
- [Tworzenie elementów konfiguracji dla systemu Android for Work](/sccm/mdm/deploy-use/create-configuration-items-for-android-and-samsung-knox-devices-managed-without-the-client#android-for-work-configuration-items)
- [Selektywne czyszczenie danych w systemie Android pracy urządzeń](/sccm/mdm/deploy-use/wipe-lock-reset-devices#selective-wipe)
- [Profile poczty e-mail dla systemu Android for Work](/sccm/mdm/deploy-use/create-exchange-activesync-profiles)
- [Zasady zgodności dla systemu Android for Work](/sccm/mdm/deploy-use/create-compliance-policy)


### <a name="deploy-volume-purchased-ios-apps-to-device-collections"></a>Wdrażanie aplikacji dla systemu iOS zakupionymi zbiorczo do kolekcji urządzeń

Teraz można wdrożyć licencjonowane aplikacje na urządzeniach, jak i użytkowników. W zależności od aplikacji możliwość obsługi urządzenia licencjonowania odpowiednią licencję będzie wymagana, wdrażając go w następujący sposób:

|||||
|-|-|-|-|
|Wersja programu Configuration Manager|Aplikacja obsługuje licencjonowania urządzeń?|Typ kolekcji wdrażania|Oświadczeniem licencji|
|Wcześniejsza niż 1702|Tak|Użytkownik|Licencja użytkownika|
|Wcześniejsza niż 1702|Nie|Użytkownik|Licencja użytkownika|
|Wcześniejsza niż 1702|Tak|Urządzenie|Licencja użytkownika|
|Wcześniejsza niż 1702|Nie|Urządzenie|Licencja użytkownika|
|1702 i nowsze|Tak|Użytkownik|Licencja użytkownika|
|1702 i nowsze|Nie|Użytkownik|Licencja użytkownika|
|1702 i nowsze|Tak|Urządzenie|Licencja urządzenia|
|1702 i nowsze|Nie|Urządzenie|Licencja użytkownika|

Aby uzyskać więcej informacji o aplikacji dla systemu iOS zakupionymi zbiorczo, zobacz [Zarządzanie aplikacjami zakupionymi zbiorczo systemu iOS](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps).

### <a name="support-for-ios-volume-purchase-program-for-education"></a>Obsługa systemu iOS Volume Purchase Program dla instytucji edukacyjnych

Teraz można również wdrożyć i śledzenie aplikacji, które zostały zakupione od iOS Volume Purchase Program dla instytucji edukacyjnych.
Aby uzyskać więcej informacji o aplikacji dla systemu iOS zakupionymi zbiorczo, zobacz [Zarządzanie aplikacjami zakupionymi zbiorczo systemu iOS](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps).

### <a name="support-for-multiple-volume-purchase-program-tokens"></a>Obsługa wielu tokenów program zakupów zbiorczych

Teraz można skojarzyć wiele tokenów program zakupów zbiorczych firmy Apple z programem Configuration Manager.
Aby uzyskać więcej informacji o aplikacji dla systemu iOS zakupionymi zbiorczo, zobacz [Zarządzanie aplikacjami zakupionymi zbiorczo systemu iOS](/sccm/mdm/deploy-use/manage-volume-purchased-ios-apps).

### <a name="support-for-line-of-business-apps-in-windows-store-for-business"></a>Obsługa aplikacji biznesowych w Sklepie Windows dla firm

Niestandardowe aplikacje biznesowe w Sklepie Windows dla firm mogą teraz synchronizować.

### <a name="conditional-access-device-compliance-policy-improvements"></a>Ulepszenia zasad zgodności urządzenia dostępu warunkowego

Dostępny jest nowy reguły zasad zgodności urządzenia możesz zablokować dostęp do zasobów firmy, które obsługują dostęp warunkowy, gdy użytkownicy korzystają z aplikacji, które są częścią listę niezgodnych aplikacji. Lista niezgodnych aplikacji można definiować przez administratora podczas dodawania nowej reguły zgodne **aplikacji, których nie można zainstalować**. Ta zasada wymaga administratora, aby wprowadzić **Nazwa aplikacji**, **identyfikator aplikacji**i **wydawcę aplikacji** (opcjonalnie), podczas dodawania do listy niezgodnych aplikacji. To ustawienie dotyczy tylko urządzeń iOS i Android.

Ponadto pomaga organizacjom ograniczyć wycieku danych za pośrednictwem niezabezpieczonej aplikacji i zapobiec zużycie nadmiernej ilości danych za pośrednictwem niektórych aplikacji.

- Dowiedz się więcej [sposób działania zasad zgodności urządzenia](/sccm/mdm/deploy-use/device-compliance-policies).
- Dowiedz się więcej [jak utworzyć zasady zgodności urządzeń](/sccm/mdm/deploy-use/create-compliance-policy).

### <a name="new-mobile-threat-defense-monitoring-tools"></a>Nowe przed zagrożeniami Mobile narzędzia do monitorowania

Począwszy od wersji 1702, masz nowe sposoby monitorowania stanu zgodności z dostawcą usług Mobile przed zagrożeniami.

- Dowiedz się więcej [sposobu monitorowania zgodności przed zagrożeniami Mobile](https://docs.microsoft.com/sccm/mdm/deploy-use/monitor-mobile-threat-defense-compliance).

## <a name="protect-devices"></a>Ochrona urządzeń

### <a name="detect-outdated-antimalware-client-versions"></a>Wykrywanie wersji klienta nieaktualne ochrony przed złośliwym oprogramowaniem
Począwszy od wersji 1702, możesz skonfigurować alert, aby upewnić się, że klientów programu Endpoint Protection nie są przestarzałe. Aby uzyskać więcej informacji, zobacz [alertu nieaktualne przed złośliwym oprogramowaniem klienta](/sccm/protect/deploy-use/endpoint-configure-alerts#detect-outdated-antimalware-client-versions).

### <a name="device-health-attestation-updates"></a>Aktualizacje zaświadczania o kondycji urządzenia
Usługi zaświadczania o kondycji urządzenia dla lokalnych klientów teraz można konfigurować i zarządzać z punktu zarządzania. Aby uzyskać więcej informacji, zobacz [zaświadczania o kondycji](/sccm/core/servers/manage/health-attestation).

### <a name="certificate-profiles-for-windows-hello-for-business"></a>Profile certyfikatów dla usługi Windows Hello dla firm

Jeśli zamierzasz profile certyfikatów są przechowywane w usługi Windows Hello dla firm kontenera kluczy i rozszerzenie EKU logowania karty inteligentnej korzysta z profilu certyfikatu, należy skonfigurować uprawnienia dla klucza rejestracji upewnij się, że certyfikat jest zweryfikowany pomyślnie.
Aby uzyskać więcej informacji, zobacz [usługi Windows Hello dla firm ustawienia](/sccm/protect/deploy-use/windows-hello-for-business-settings).

### <a name="new-windows-hello-for-business-notification-for-end-users"></a>Nowe usługi Windows Hello dla firm powiadomienia dla użytkowników końcowych
Nowe powiadomienie systemu Windows 10 informuje o użytkowników końcowych, że ich należy wykonać dodatkowe akcje do wykonania Windows Hello dla firm Instalatora (na przykład konfigurowania numeru PIN).
