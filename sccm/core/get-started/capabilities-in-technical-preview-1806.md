---
title: Technical Preview 1806
titleSuffix: Configuration Manager
description: Więcej informacji na temat nowych funkcji dostępnych w wersji Configuration Manager Technical Preview 1806.
ms.date: 06/06/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 52d64ef0-8c0d-42c3-857e-07d7ec776f29
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 4933e4e6d9037edd01d80c9535627287275f7462
ms.sourcegitcommit: 10b3a571e2a822bbd7b58a25840ee1e6f703a7a2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2018
ms.locfileid: "34814301"
---
# <a name="capabilities-in-technical-preview-1806-for-system-center-configuration-manager"></a>Funkcje w wersji Technical Preview 1806 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*

W tym artykule przedstawiono funkcje, które są dostępne w wersji Technical Preview programu Configuration Manager, wersja 1806. Można zainstalować tę wersję, aby zaktualizować i dodać nowe funkcje do swojej witryny wersji zapoznawczej technical preview. 

Przegląd [Technical Preview](/sccm/core/get-started/technical-preview) artykuł przed zainstalowaniem tej aktualizacji. Ten artykuł zaznajomić z ogólne wymagania i ograniczenia dotyczące używania wersji technical preview, jak zaktualizować między wersjami i sposobu wyrazić swoją opinię.     


<!--  Known Issues Template
## Known Issues in this Technical Preview

### <a name="ki_ANCHOR"></a> Known issue title
<!--bugID--
Issue description and cause.

#### Workaround
Steps to workaround, if any.  
-->
## <a name="known-issues-in-this-technical-preview"></a>Znane problemy w tej wersji Technical Preview

### <a name="ki_contentlib"></a> Lokacji nie powiedzie się do uaktualnienia z biblioteki zdalnej zawartości
<!--514642-->
Lokacji nie powiedzie się do uaktualnienia z powodu następujących błędów w **cmupdate.log**:  
```  
Failed to find any valid drives  
GetContentLibraryParameters failed; 0x80070057  
ERROR: Failed to process configuration manager update.  
```  

Ten problem występuje w tej wersji, gdy biblioteka zawartości znajduje się w lokalizacji zdalnej.

#### <a name="workaround"></a>Obejście
Przenoszenia biblioteki zawartości na dysk lokalny na serwerze lokacji. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zdalnego biblioteki zawartości na serwerze lokacji](/sccm/core/get-started/capabilities-in-technical-preview-1804#configure-a-remote-content-library-for-the-site-server). 



</br>

**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  



## <a name="bkmk-3pupdate"></a> Aktualizacje oprogramowania innych firm
<!--1352101-->
Iteracje dalej w tej wersji na obsługę aktualizacji oprogramowania innych firm w Twojej [opinii z witryny UserVoice](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/8803711-3rd-party-patching-scup-integration-with-sccm-co). Użyj programu System Center aktualizacje wydawcy (SCUP) nie jest już wymagany dla niektórych typowych scenariuszy. Nowy **katalogi aktualizowanie oprogramowania innych firm** węzeł w konsoli programu Configuration Manager umożliwia subskrybowanie katalogi innych firm, publikowanie ich aktualizacji do punktu aktualizacji oprogramowania i wdrożenia go na klientach. 

Następujące katalogi aktualizacji oprogramowania innych firm są dostępne w tej wersji:
 | Wydawca | Nazwa katalogu |
 |--------|---------------------|
 | HP | HP klienta aktualizacji katalogu |

SCUP w dalszym ciągu obsługuje inne katalogi i scenariuszy. Lista katalogów, w węźle katalogi aktualizacji oprogramowania innych firm w konsoli programu Configuration Manager jest dynamiczny, a zostanie zaktualizowany zgodnie z kolejnych wykazów jest dostępny i obsługiwany.


### <a name="prerequisites"></a>Wymagania wstępne
- Konfigurowanie oprogramowania aktualizuje zarządzania, punkt aktualizacji oprogramowania z włączonym protokołem HTTPS. Aby uzyskać więcej informacji, zobacz [przygotowanie do oprogramowania aktualizuje zarządzania](/sccm/sum/get-started/prepare-for-software-updates-management).  
   - Punkt aktualizacji oprogramowania musi być na serwerze lokacji dla tej funkcji w tej wersji. <!--515810--> 

- Wystarczająca ilość miejsca na aktualizacji oprogramowania punktu folderu WSUSContent do przechowywania zawartości binarnej źródła aktualizacji oprogramowania innych firm. Ilość wymaganego miejsca w magazynie w zależności od dostawcy, typy, aktualizacji i aktualizacje, które publikowania dla wdrożenia. Jeśli musisz przenieść folderu WSUSContent na inny dysk z większą ilością wolnego miejsca, zobacz WSUS obsługuje w blogu zespołu [sposób zmienić lokalizację, w której WSUS przechowuje aktualizacje lokalnie](https://blogs.technet.microsoft.com/sus/2008/05/19/wsus-how-to-change-the-location-where-wsus-stores-updates-locally/).  

- Włączyć i wdrożyć ustawienia klienta [Włącz aktualizacje oprogramowania innych firm](/sccm/core/clients/deploy/about-client-settings#enable-third-party-software-updates) w **aktualizacji oprogramowania** grupy.  

- Serwer lokacji wymaga dostępu do Internetu na witrynie download.microsoft.com za pośrednictwem portu HTTPS 443. Usługa synchronizacji aktualizacji oprogramowania innych firm obecnie działa na serwerze lokacji. Ta usługa aktualizuje listę dostępnych katalogów innych firm, pliki do pobrania katalogi podczas subskrybowania i pobiera aktualizacje po opublikowaniu. Konfigurowanie ustawień internetowego serwera proxy, jeśli to konieczne, na **Proxy** karta Właściwości roli systemu lokacji na komputerze serwera lokacji.  


### <a name="try-it-out"></a>Wypróbuj
 Spróbuj wykonać zadania. Wyślij [opinii](capabilities-in-technical-preview-1804.md#bkmk_feedback) zawiadomienie nas o tym, jak Ci poszło.


#### <a name="phase-1-enable-and-set-up-the-feature"></a>Faza 1: Włącz i skonfiguruj funkcję
Wykonaj poniższe kroki *raz dla hierarchii* można włączyć i skonfigurować funkcję do użycia:  

1. W konsoli programu Configuration Manager, przejdź do **administracji** obszaru roboczego. Rozwiń węzeł **konfiguracja lokacji**i wybierz **witryny** węzła.  

2. Wybierz lokację najwyższego poziomu w hierarchii. Na wstążce kliknij **Konfiguruj składniki lokacji**i wybierz **punkt aktualizacji oprogramowania**.  

3. Przełącz się do **aktualizacji innych firm** kartę. Wybierz opcję **Włącz aktualizacje oprogramowania innych firm**. Aby uzyskać więcej informacji na temat opcji certyfikatu, zobacz [ulepszenia dotyczące włączania oprogramowania innych firm aktualizacja obsługi](/sccm/core/get-started/capabilities-in-technical-preview-1805#improvements-for-enabling-third-party-software-update-support).  

   > [!Note]  
   > W przypadku wybrania opcji domyślnej programu Configuration Manager do zarządzania tego certyfikatu, nowy certyfikat typu **podpisywania WSUS innych firm** jest tworzony w **certyfikaty** węźle  **Zabezpieczenia** w **administracji** obszaru roboczego.  


#### <a name="phase-2-subscribe-to-a-third-party-catalog-and-sync-updates"></a>Faza 2: Subskrybuj katalogu innych firm i synchronizacji aktualizacji
Wykonaj poniższe kroki, aby *każdego katalogu innych firm* do której należy do subskrypcji:  

1. W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** obszaru roboczego. Rozwiń węzeł **aktualizacji oprogramowania** i wybierz **katalogi aktualizacji oprogramowania innych firm** węzła.  

2. Wybierz katalog do subskrypcji, a następnie kliknij przycisk **subskrybować katalogu** na Wstążce.   

3. Wyświetl i zatwierdź certyfikatu katalogu.  

   > [!Note]  
   > Po zasubskrybowaniu katalogu aktualizacji oprogramowania innych firm certyfikat, który przeglądu i zatwierdzania w kreatorze jest dodawany do lokacji. Ten certyfikat jest typu **aktualizacje oprogramowania innych firm**. Można zarządzać nim z **certyfikaty** węźle **zabezpieczeń** w **administracji** obszaru roboczego.  

4. Ukończ pracę kreatora.  

   > [!Tip]  
   > Po początkowej subskrypcji katalogu należy zacząć pobrać. Resyncs ją następnie co 24 godziny, w tej wersji. Jeśli nie chcesz czekać na katalog, aby automatycznie pobrać, kliknij przycisk **Synchronizuj teraz** na Wstążce.  
   > 
   > Po pobraniu katalogu metadanych produktu należy zsynchronizować punkt aktualizacji oprogramowania. Aby uzyskać więcej informacji na temat tego procesu oraz aby ręcznie zainicjować zobacz [synchronizowanie aktualizacji oprogramowania](/sccm/sum/get-started/synchronize-software-updates). W tym momencie można zobaczyć aktualizacji innych firm w **wszystkie aktualizacje** węzła. 

5. Skonfiguruj punkt aktualizacji oprogramowania **produktów** katalogu innych firm, do którego masz subskrypcję. Aby uzyskać więcej informacji, zobacz [skonfigurować klasyfikacje i produkty do zsynchronizowania](/sccm/sum/get-started/configure-classifications-and-products). Po zmianie kryteria produktu ponownie musi nastąpić synchronizacja aktualizacji oprogramowania.

Zanim zobaczysz wyniki oceny zgodności z klientów potrzebuje do skanowania i oceny aktualizacji. Ten cykl w Panelu sterowania programu Configuration Manager na komputerze klienckim mogą ręcznie uruchomić, uruchamiając **oprogramowania cykl skanowania aktualizacji** akcji. Aby uzyskać więcej informacji na temat procesu, zobacz [wprowadzenia aktualizacji oprogramowania](/sccm/sum/understand/software-updates-introduction).


#### <a name="phase-3-deploy-third-party-software-updates"></a>Faza 3: Wdrażanie aktualizacji oprogramowania innych firm
Wykonaj poniższe kroki, aby *wszystkie aktualizacje oprogramowania innych firm* mają zostać wdrożone na klientach:  

1. W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** obszaru roboczego. Rozwiń węzeł **aktualizacji oprogramowania** i wybierz **wszystkie aktualizacje oprogramowania** węzła.  

   > [!Tip]  
   > Kliknij przycisk **Dodaj kryteria** Aby przefiltrować listę aktualizacji. Na przykład dodać **dostawcy** dla **Adobe Systems, Inc.** Aby wyświetlić wszystkie aktualizacje firmy Adobe.  

2. Wybierz aktualizacje, które są wymagane przez klientów. Kliknij przycisk **publikowania innych firm zawartości aktualizacji oprogramowania** i sprawdzić postęp w SMS_ISVUPDATES_SYNCAGENT.log. Ta akcja pobiera pliki binarne aktualizacji od dostawcy i przechowuje je w folderze WSUSContent na punkcie aktualizacji oprogramowania. Zmienia także stanu aktualizacji od tylko metadane do zawartości i możliwych do wdrożenia.  

   > [!Note]  
   > Podczas publikowania zawartości aktualizacji oprogramowania innych firm, wszystkie certyfikaty używane do podpisywania zawartości są dodawane do lokacji. Te certyfikaty są typu **zawartości aktualizacji oprogramowania innych firm**. Zarządzać nimi z **certyfikaty** węźle **zabezpieczeń** w **administracji** obszaru roboczego.  

3. Wdróż aktualizacje przy użyciu istniejącego procesu zarządzania aktualizacji oprogramowania. Aby uzyskać więcej informacji, zobacz [wdrażania aktualizacji oprogramowania](/sccm/sum/deploy-use/deploy-software-updates). Na **lokalizacje** strony Kreatora wdrażania aktualizacji oprogramowania wybierz opcję domyślną **Pobierz aktualizacje oprogramowania z Internetu**. W tym scenariuszu zawartości został już opublikowany w punkcie aktualizacji oprogramowania, który służy do pobierania zawartości pakietu wdrożeniowego.


### <a name="monitoring-progress-of-third-party-software-updates"></a>Monitorowanie postępu aktualizacji oprogramowania innych firm
Synchronizacja aktualizacji oprogramowania innych firm jest obsługiwany przez składnik SMS_ISVUPDATES_SYNCAGENT na serwerze lokacji. Wyświetlanie komunikatów o stanie tego składnika lub wyświetlić bardziej szczegółowy stan w SMS_ISVUPDATES_SYNCAGENT.log. Ten dziennik jest na serwerze lokacji w **dzienniki** podfolder katalogu instalacyjnego lokacji. Domyślnie ta ścieżka jest `C:\Program Files\Microsoft Configuration Manager\Logs`. Aby uzyskać więcej informacji dotyczących monitorowania proces zarządzania aktualizacjami oprogramowania ogólne, zobacz [monitorowanie aktualizacji oprogramowania](/sccm/sum/deploy-use/monitor-software-updates).


### <a name="known-issues"></a>Znane problemy
- Usługa synchronizacji aktualizacji oprogramowania innych firm nie obsługuje punkt aktualizacji oprogramowania skonfigurowany do używania **konta połączenia serwera WSUS**. Jeśli to konto jest skonfigurowane na **ustawienia konta serwera Proxy i** kartę stronę właściwości punktu aktualizacji oprogramowania, zostanie wyświetlony następujący błąd w SMS_ISVUPDATES_SYNCAGENT.log:  
`WSUS access account appears to be configured, it is not yet supported for third party updates sync.`  
Aby uzyskać więcej informacji dotyczących tego konta, zobacz [konto połączenia punktu aktualizacji oprogramowania](/sccm/core/plan-design/hierarchy/accounts#software-update-point-connection-account).<!--515492-->  

- Nie można mieszać korzystanie z innych narzędzi, takich jak SCUP dzięki tej nowej funkcji aktualizacji w postaci zintegrowanego oprogramowania innych firm. Usługa synchronizacji aktualizacji oprogramowania innych firm nie można opublikować tylko metadane aktualizacji, które zostały dodane do programu WSUS przez inną aplikację, narzędzie lub skrypt, takich jak SCUP zawartości. **Publikowanie zawartości aktualizacji oprogramowania innych firm** akcja zakończy się niepowodzeniem na tych aktualizacji. Jeśli zajdzie potrzeba wdrożenia aktualizacji innych firm, które jeszcze nie obsługuje tej funkcji, należy użyć istniejącego procesu w pełni do wdrażania tych aktualizacji.<!--515497-->  



## <a name="configure-windows-defender-smartscreen-settings-for-microsoft-edge"></a>Skonfiguruj ustawienia systemu Windows Defender SmartScreen Microsoft Edge
<!--1353701-->
Ta wersja dodaje trzy ustawienia [Windows Defender SmartScreen](/windows/security/threat-protection/windows-defender-smartscreen/windows-defender-smartscreen-overview) do [zasady ustawień zgodności przeglądarki Microsoft Edge](/sccm/compliance/deploy-use/browser-profiles). Zasady zawiera teraz następujące dodatkowe ustawienia na **ustawień filtru SmartScreen** strony:
- **Zezwalaj na SmartScreen**: Określa, czy program Windows Defender SmartScreen jest dozwolone. Aby uzyskać więcej informacji, zobacz [AllowSmartScreen przeglądarki zasad](/windows/client-management/mdm/policy-csp-browser#browser-allowsmartscreen).
- **Użytkownicy mogą zastępować SmartScreen wiersza dla witryn**: Określa, czy użytkownicy mogą zastępować ostrzeżeń filtru SmartScreen usługi Windows Defender o potencjalnie złośliwych witryn sieci Web. Aby uzyskać więcej informacji, zobacz [PreventSmartScreenPromptOverride przeglądarki zasad](/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverride).
- **Użytkownicy mogą zastępować SmartScreen wiersza dla plików**: Określa, czy użytkownicy mogą zastępować ostrzeżeń filtru SmartScreen usługi Windows Defender dotyczące pobierania plików niezweryfikowane. Aby uzyskać więcej informacji, zobacz [PreventSmartScreenPromptOverrideForFiles przeglądarki zasad](/windows/client-management/mdm/policy-csp-browser#browser-preventsmartscreenpromptoverrideforfiles).



## <a name="sync-mdm-policy-from-microsoft-intune-for-a-co-managed-device"></a>Zasady zarządzania urządzeniami Przenośnymi synchronizacji z Microsoft Intune dla wspólnie zarządzanego urządzenia
<!--1357377-->
Uruchamianie w tej wersji możesz [przełącznika obciążenia zarządzania wspólnej](/sccm/core/clients/manage/co-management-switch-workloads), wspólnie zarządzanych urządzeń Synchronizuj automatycznie zasad zarządzania urządzeniami Przenośnymi z Microsoft Intune. Ta synchronizacja występuje także po zainicjowaniu **Pobierz zasady komputera** akcji z powiadomieniami klienta w konsoli programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [rozpocząć pobieranie zasad klienta za pomocą powiadomień klienta](/sccm/core/clients/manage/manage-clients#initiate-client-policy-retrieval-using-client-notification).



## <a name="transition-office-365-workload-to-intune-using-co-management"></a>Obciążenie usługi Office 365 przechodzenia do usługi Intune przy użyciu wspólnej zarządzania
<!--1357841-->
Po włączeniu wspólnego zarządzania można teraz przejść obciążenie usługi Office 365 z programu Configuration Manager w usłudze Microsoft Intune. Do przejścia to obciążenie, przejdź do strony właściwości wspólnego zarządzania i przesuń suwak z programu Configuration Manager do pilotażu lub. Aby uzyskać więcej informacji, zobacz [urządzenia zarządzania wspólnej dla systemu Windows 10](/sccm/core/clients/manage/co-management-overview).

Istnieje również nowy warunek globalny **aplikacji usługi Office 365 są zarządzane przez usługę Intune na urządzeniu**. Ten stan jest domyślnie dodawany jako wymaganie do nowej aplikacji usługi Office 365. Jeśli przejście to obciążenie, wspólnie zarządzanych klientów nie spełnia wymagań dla aplikacji, w związku z tym nie należy instalować usługi Office 365 wdrożony za pomocą programu Configuration Manager.

### <a name="known-issue"></a>Znany problem
- Ten proces przejścia obciążenia aktualnie ma zastosowanie tylko do wdrożenia usługi Office 365. Kontynuuje programu Configuration Manager do zarządzania aktualizacjami usługi Office 365.<!--510876--> Aby uzyskać więcej informacji, łącznie możliwe rozwiązania, zobacz 1802 wersji programu Configuration Manager, należy pamiętać o wersji [ustawienia klienta usługi Office 365 zmiana nie ma zastosowania](/sccm/core/servers/deploy/install/release-notes#changing-office-365-client-setting-doesnt-apply).



## <a name="package-conversion-manager"></a>Programu Package Conversion Manager 
<!--1357861-->
Menedżer konwersji pakietów jest teraz zintegrowane narzędzia, który pozwala konwertować pakiety ze starszych wersji programu Configuration Manager 2007 do programu Configuration Manager aktualnie używane aplikacje gałęzi. Następnie można użyć funkcji aplikacji, takich jak zależności, reguły wymagań i koligacja urządzenia użytkownika.

> [!Tip]  
> Istniejące funkcje programu Package Conversion Manager w starszej wersji dokumentacji jest dostępna w [TechNet](https://technet.microsoft.com/library/hh531519.aspx). Proces migracji do biblioteki docs.microsoft.com jest istotne informacje.

### <a name="try-it-out"></a>Wypróbuj
 Spróbuj wykonać zadania. Wyślij [opinii](capabilities-in-technical-preview-1804.md#bkmk_feedback) zawiadomienie nas o tym, jak Ci poszło.

> [!Important]  
> Jeśli wcześniej zainstalowana starsza wersja programu Package Conversion Manager, najpierw ją odinstalować przed uaktualnieniem lokacji. Nowa wersja zintegrowane nie wymagają instalacji, ale może powodować konflikt z istniejącymi wersjami.  

1. W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** obszaru roboczego. Rozwiń węzeł **Zarządzanie aplikacjami** i wybierz **pakiety**.  
2. Wybierz pakiet. Poniższe trzy opcje są dostępne w **konwersji pakietu** grupę na Wstążce:  
     - **Analizuj pakiet**: Uruchom proces konwersji, analizując pakietu.
     - **Konwertuj pakiet**: Niektóre pakiety mogą być konwertowane łatwe do aplikacji za pomocą tej akcji.
     - **Naprawa i konwersja**: Niektóre pakiety wymagają problemów należy naprawić przed dokonaniem konwersji na aplikacje.  

   Aby uzyskać więcej informacji dotyczących tych działań, zobacz [analizowanie i konwertowanie pakietów](https://docs.microsoft.com/previous-versions/system-center/system-center-2012-R2/hh846244%28v%3dtechnet.10%29).  

3. Przejdź do **monitorowanie** obszar roboczy i wybierz **stan konwersji pakietu**. Tego nowego pulpitu nawigacyjnego przedstawia ogólny stan analizy i konwersji pakietów w lokacji. Nowe zadanie w tle automatycznie podsumowuje dane analizy.  

   > [!Tip]  
   > Programu Package Conversion Manager nie wymaga zaplanowania analizy pakietów. Ta akcja jest teraz obsługiwany przez zadanie podsumowania zintegrowanego.  

![Zrzut ekranu pakietu stan konwersji pulpitu nawigacyjnego](media/1357861-pcm-dashboard.png)



## <a name="deploy-software-updates-without-content"></a>Wdrażanie aktualizacji oprogramowania bez zawartości
<!--1357933-->
Teraz można wdrożyć aktualizacje oprogramowania na urządzeniach bez uprzedniego pobierania i dystrybucji zawartości aktualizacji oprogramowania do punktów dystrybucji. Ta funkcja jest przydatne podczas pracy z bardzo dużej aktualizacji zawartości lub należy zawsze klientom na pobieranie zawartości z usługi w chmurze usługi Microsoft Update. Klienci, w tym scenariuszu można również pobrać zawartość od elementów równorzędnych, które mają już wymaganej zawartości. W związku z tym Configuration Manager nadal zarządza pobierania zawartości, klient może korzystać z funkcji programu Configuration Manager równorzędnej pamięci podręcznej ani innych technologii, takich jak Optymalizacja dostarczania. Ta funkcja obsługuje dowolny typ aktualizacji obsługiwane przez zarządzanie aktualizacjami oprogramowania programu Configuration Manager, w tym systemu Windows i aktualizacji pakietu Office. 

### <a name="try-it-out"></a>Wypróbuj
 Spróbuj wykonać zadania. Wyślij [opinii](capabilities-in-technical-preview-1804.md#bkmk_feedback) zawiadomienie nas o tym, jak Ci poszło.

1. Uruchom wdrożenie aktualizacji oprogramowania na normalny. Aby uzyskać więcej informacji, zobacz [wdrażania aktualizacji oprogramowania](/sccm/sum/deploy-use/deploy-software-updates).
2. W Kreatorze wdrażania aktualizacji oprogramowania na **pakietu wdrożeniowego** wybierz nową opcję **nie pakietu wdrożeniowego**.

### <a name="known-issues"></a>Znane problemy
- Ikona aktualizacji z tego ustawienia nieprawidłowo Wyświetla z czerwonym symbolem X tak, jakby aktualizacji jest nieprawidłowy. Aby uzyskać więcej informacji, zobacz [ikony stosowane przy aktualizacjach oprogramowania](/sccm/sum/understand/software-updates-icons). <!--515556-->  
- To ustawienie jest tylko zintegrowane z Kreatora wdrażania aktualizacji oprogramowania. Nie jest obecnie dostępna przy użyciu reguł wdrażania automatycznego. <!--515558-->  



## <a name="office-customization-tool-integration-with-the-office-365-installer"></a>Integracja narzędzia dostosowywania pakietu Office przy użyciu pakietu Office 365 Instalatora
<!--1358149-->
Narzędzia dostosowywania pakietu Office jest teraz zintegrowana z Instalatorem Office 365 w konsoli programu Configuration Manager. Podczas tworzenia wdrożenia dla usługi Office 365, można teraz dynamicznie skonfigurować najnowsze ustawienia urzędu zarządzania. Narzędzia dostosowywania pakietu Office jest aktualizowana w tym samym czasie jako wersja nowych kompilacji usługi Office 365. Możesz teraz możliwe jest zastosowanie nowych ustawień zarządzania w usłudze Office 365 natychmiast po ich udostępnieniu. 

### <a name="prerequisites"></a>Wymagania wstępne
- Komputer z uruchomioną konsolą programu Configuration Manager wymaga dostępu do Internetu za pośrednictwem protokołu HTTPS portu 443. Kreator instalacji klienta Office 365 otwiera za pomocą przeglądarki sieci web standard systemu Windows interfejsu API https://config.office.com. Jeśli używany jest internetowy serwer proxy, użytkownik musi mieć możliwość dostępu tego adresu URL.

### <a name="try-it-out"></a>Wypróbuj
 Spróbuj wykonać zadania. Wyślij [opinii](capabilities-in-technical-preview-1804.md#bkmk_feedback) zawiadomienie nas o tym, jak Ci poszło.

1. W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** obszaru roboczego, a następnie wybierz **zarządzania klienta usługi Office 365** węzła.
2. Kliknij przycisk **Office 365 Instalator** kafelka na pulpicie nawigacyjnym, aby uruchomić Kreatora instalacji klienta pakietu Office 365. Aby uzyskać więcej informacji, zobacz [aplikacji wdrożenia usługi Office 365](/sccm/sum/deploy-use/manage-office-365-proplus-updates#deploy-office-365-apps).
3. Na **ustawienie Office** kliknij przycisk **przejdź do strony sieci Web pakietu Office**. Użyj narzędzia dostosowywania pakietu Office online do określenia ustawień dla tego wdrożenia. 
4. Kliknij przycisk **przesyłania** w prawym górnym rogu po zakończeniu. Zakończ pracę Kreatora instalacji klienta usługi Office 365.



## <a name="improvements-to-cloud-management-gateway"></a>Ulepszenia zarządzania bramy w chmurze
Ta wersja zawiera następujące ulepszenia z bramą zarządzania chmury (CMG):

### <a name="simplified-client-bootstrap-command-line"></a>Wiersz polecenia uruchamiania uproszczony klienta
<!--1358215-->
Podczas instalowania klienta programu Configuration Manager w Internecie za pośrednictwem CMG, mniej właściwości wiersza polecenia są teraz wymagane. Aby uzyskać więcej informacji na jednym z przykładów tego scenariusza, zobacz [wiersza polecenia do zainstalowania klienta programu Configuration Manager](/sccm/core/clients/manage/co-management-prepare#command-line-to-install-configuration-manager-client) podczas przygotowywania do wspólnego zarządzania. 

Następujące właściwości wiersza polecenia są wymagane we wszystkich scenariuszach:
  - CCMHOSTNAME  
  - SMSSITECODE  

W przypadku używania usługi Azure AD dla uwierzytelniania klienta, zamiast certyfikatów uwierzytelniania klienta PKI, wymagane są następujące właściwości:
  - AADCLIENTAPPID  
  - AADRESOURCEURI  

Następująca właściwość jest wymagany, jeśli klient zostanie są przekazywane do sieci intranet:
  - SMSMP  

Poniższy przykład zawiera wszystkie właściwości powyżej:   
`ccmsetup.exe CCMHOSTNAME=CONTOSO.CLOUDAPP.NET/CCM_Proxy_MutualAuth/72186325152220500 SMSSiteCode=ABC AADCLIENTAPPID=7506ee10-f7ec-415a-b415-cd3d58790d97 AADRESOURCEURI=https://contososerver SMSMP=https://mp1.contoso.com`

Aby uzyskać więcej informacji, zobacz [właściwości instalacji klienta](/sccm/core/clients/deploy/about-client-installation-properties).

### <a name="download-content-from-a-cmg"></a>Pobieranie zawartości z CMG
<!--1358651-->
Wcześniej trzeba było wdrożyć punkt dystrybucji w chmurze i CMG jako poszczególne role. Teraz w tej wersji CMG może również udostępniać zawartość do klientów. Ta funkcja ogranicza wymaganych certyfikatów i kosztów maszyn wirtualnych platformy Azure. Aby włączyć tę funkcję, należy włączyć opcję Nowy **Zezwalaj CMG do działania jako punkt dystrybucji w chmurze i udostępniać zawartość z usługi Azure storage** na **ustawienia** karta właściwości CMG. 

### <a name="trusted-root-certificate-isnt-required-with-azure-ad"></a>Zaufany certyfikat główny nie jest wymagane w usłudze Azure AD
<!--503899-->
Podczas tworzenia CMG już nie musisz podać [zaufany certyfikat główny](/sccm/core/clients/manage/cmg/certificates-for-cloud-management-gateway#cmg-trusted-root-certificate-to-clients) na stronie Ustawienia. Ten certyfikat nie jest wymagana, gdy do uwierzytelniania klientów za pomocą usługi Azure Active Directory (Azure AD), ale używana jest wymagane w kreatorze.

> [!Important]  
> Jeśli używasz certyfikatów uwierzytelniania klienta PKI, następnie należy nadal dodać zaufany certyfikat główny do CMG.



## <a name="improvements-to-secure-client-communications"></a>Ulepszenia do zabezpieczania komunikacji z klientem
<!--1358278,1358279-->
Tej wersji w dalszym ciągu iterację [ulepszone komunikacji z klientem bezpiecznego](/sccm/core/get-started/capabilities-in-technical-preview-1805#improved-secure-client-communications) przez usunięcie zależności dodatkowe na konto dostępu do sieci. Po włączeniu nowej opcji lokacji, która **wygenerowane za pomocą konfiguracji Menedżera certyfikatów dla protokołu HTTP z systemami lokacji**, następujące scenariusze nie wymaga konta dostępu do sieci, aby pobrać zawartość z punktu dystrybucji:  

- Sekwencje zadań uruchomiona z nośnika rozruchowego lub środowiska PXE
- Sekwencje zadań uruchomiony za pośrednictwem programu Software Center  

Te sekwencje zadań można do wdrożenia systemu operacyjnego lub niestandardowy. Jest też obsługiwana dla komputerów grupy roboczej.



## <a name="software-center-infrastructure-improvements"></a>Ulepszenia infrastruktury Centrum oprogramowania
<!--1358309-->
Ról wykazu aplikacji nie są już wymagane, aby wyświetlić aplikacje dostępne dla użytkowników w programie Software Center. Ta zmiana pomaga ograniczyć infrastruktury serwera, wymaganych do dostarczenia aplikacji dla użytkowników. Program Software Center teraz, opiera się na punkt zarządzania, aby uzyskać informacje, które pomaga większych środowiskach skali lepiej przez przypisywanie ich do [grup granic](/sccm/core/servers/deploy/configure/boundary-groups#management-points).

### <a name="try-it-out"></a>Wypróbuj
 Spróbuj wykonać zadania. Wyślij [opinii](capabilities-in-technical-preview-1804.md#bkmk_feedback) zawiadomienie nas o tym, jak Ci poszło.

1. Usuń wszystkie role katalogu aplikacji z lokacji. Role te obejmują punkt usługi sieci web katalogu aplikacji i punkt witryny sieci Web katalogu aplikacji.
2. Wdrażanie aplikacji jako dostępne do kolekcji użytkowników.
3. Użyj programu Software Center jako docelowych użytkownikowi przeglądanie, żądanie i instalowanie aplikacji.

### <a name="known-issue"></a>Znany problem
- Jeśli używasz klienta przyłączonych do usługi Azure Active Directory przy użyciu tej funkcji, nie Konfigurowanie lokacji w celu **wygenerowany używać programu Configuration Manager certyfikatów dla protokołu HTTP z systemami lokacji**. Obecnie występują konflikty z tej funkcji.<!--515846--> Aby uzyskać więcej informacji o tym ustawieniu, zobacz [ulepszone komunikacji z klientem bezpiecznego](/sccm/core/get-started/capabilities-in-technical-preview-1805#improved-secure-client-communications).



## <a name="provision-windows-app-packages-for-all-users-on-a-device"></a>Zapewnij pakiety aplikacji systemu Windows dla wszystkich użytkowników na urządzeniu
<!--1358310-->
Teraz można udostępnić aplikacji przy użyciu pakietu aplikacji systemu Windows dla wszystkich użytkowników na urządzeniu. Przykładem typowych tego scenariusza aprowizacji aplikacji z Microsoft Store dla firm i edukacji, takich jak Minecraft: Education Edition, aby wszystkie urządzenia używane przez studentów w szkole. Wcześniej programu Configuration Manager obsługuje tylko instalowania tych aplikacji dla poszczególnych użytkowników. Po zalogowaniu się na inne urządzenie, student musi czekać na dostęp do aplikacji. Teraz po zainicjowaniu obsługi aplikacji na urządzeniu dla wszystkich użytkowników, mogą być wydajni szybciej.

> [!Important]  
> Należy zachować ostrożność, instalowanie, inicjowanie obsługi administracyjnej i aktualizowanie różne wersje tego samego pakietu aplikacji systemu Windows na urządzeniu, co może spowodować nieoczekiwane wyniki. To zachowanie może wystąpić, gdy przy użyciu programu Configuration Manager do udostępnienia aplikacji, ale następnie zezwolenie użytkownikom na aktualizowanie aplikacji z Microsoft Store. Aby uzyskać więcej informacji, zobacz dalej wskazówki krok po możesz [zarządzać aplikacjami z Microsoft Store dla firm](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business#next-steps).  

Podczas inicjowania obsługi administracyjnej aplikację z licencją offline, programu Configuration Manager nie zezwala na Windows mają być automatycznie aktualizowane z Microsoft Store.  

### <a name="try-it-out"></a>Wypróbuj
 Spróbuj wykonać zadania. Wyślij [opinii](capabilities-in-technical-preview-1804.md#bkmk_feedback) zawiadomienie nas o tym, jak Ci poszło.

1. Utwórz nową aplikację. Ta aplikacja musi pochodzić z pakietu aplikacji systemu Windows lub aplikacji licencjonowanych w trybie offline, która zsynchronizowaniu z Microsoft Store dla firm i Education.  

2. Na **ogólne informacje** strony kreatora tworzenia aplikacji, włącz opcję **udostępnienia tej aplikacji dla wszystkich użytkowników na urządzeniu**.  

   > [!Tip]  
   > W przypadku modyfikowania istniejącej aplikacji, to ustawienie jest włączone **środowisko użytkownika** karta właściwości aplikacji.  

3. Wdrażanie aplikacji w kolekcji urządzeń.  

4. Zaloguj się do urządzenia docelowego z różnych kont użytkowników i uruchomienia aplikacji.  

> [!Note]  
> Jeśli konieczne jest odinstalowanie elastycznie aplikacji z urządzeń, do których użytkownicy mają już zalogowanego, należy utworzyć dwa odinstalować wdrożenia. Docelowy pierwszy odinstalować wdrożenie w kolekcji urządzeń zawierającej urządzenia. Docelowa drugi wdrożenie do kolekcji użytkowników, która zawiera użytkowników, którzy zalogowali się już do urządzeń z aplikacją elastycznie odinstalowania. Podczas odinstalowywania elastycznie aplikację na urządzeniu, Dezinstalacja systemu Windows obecnie nie danej aplikacji dla użytkowników, jak również. 



## <a name="improvements-to-the-surface-dashboard"></a>Udoskonalenia powierzchni pulpitu nawigacyjnego
<!--1358654-->
W tej wersji dodano następujące ulepszenia [powierzchni pulpitu nawigacyjnego](/sccm/core/clients/manage/surface-device-dashboard):
- Powierzchni pulpitu nawigacyjnego zostanie wyświetlona lista odpowiednich urządzeń, po wybraniu sekcje wykresu.
   - Kliknięcie **procent urządzeń Surface** kafelka Otwiera listę urządzeń powierzchni.
   - Klikając pasek w **górnej pięć wersji oprogramowania układowego** kafelka Otwiera listę powierzchni urządzeń z tą wersją określonego oprogramowania układowego.
- Podczas wyświetlania tych list urządzenia z powierzchni pulpitu nawigacyjnego, można kliknij prawym przyciskiem myszy urządzenie i wykonywanie typowych akcji.



## <a name="hardware-inventory-default-unit-revision"></a>Poprawki jednostki domyślne spisu sprzętu
<!--514442-->
W [1710 wersji programu Configuration Manager](/sccm/core/plan-design/changes/whats-new-in-version-1710#site-infrastructure), zmienić jednostki domyślne używane w wielu widoków raportowania z megabajtów (MB) gigabajtów (GB). Ze względu na [ulepszenia spis sprzętu dla dużej liczby całkowite](/sccm/core/get-started/capabilities-in-technical-preview-1805#improvement-to-hardware-inventory-for-large-integer-values), i na podstawie opinii klientów, ta wartość jednostki jest teraz MB ponownie.



## <a name="next-steps"></a>Następne kroki
Uzyskać informacji dotyczących instalowania lub aktualizowania gałęzi wersji zapoznawczej technical preview, zobacz [Technical Preview programu System Center Configuration Manager](/sccm/core/get-started/technical-preview).    
