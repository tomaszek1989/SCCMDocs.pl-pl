---
title: Technical Preview 1802 | Dokumentacja firmy Microsoft
titleSuffix: Configuration Manager
description: Dowiedz się więcej o funkcjach dostępnych w wersji zapoznawczej Technical Preview 1802 programu System Center Configuration Manager.
ms.date: 02/09/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 4884a2d3-13ce-44e5-88c4-a66dc7ec6014
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: c960ee37e5f4b7b3b644afd06a04c2747cc1f1eb
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="capabilities-in-technical-preview-1802-for-system-center-configuration-manager"></a>Funkcje w wersji Technical Preview 1802 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*

W tym artykule przedstawiono funkcje, które są dostępne w wersji Technical Preview programu System Center Configuration Manager, wersja 1802. Można zainstalować tę wersję, aby zaktualizować i dodać nowe funkcje do lokacji programu Configuration Manager technical preview. 

Przegląd [Technical Preview programu System Center Configuration Manager](/sccm/core/get-started/technical-preview) przed zainstalowaniem tej wersji technical preview. Ten artykuł zaznajomić z ogólne wymagania i ograniczenia dotyczące używania wersji technical preview, jak zaktualizować między wersjami i sposobu wyrazić swoją opinię.     


<!--  Known Issues Template   
## Known Issues in this Technical Preview:
-   **Issue Name**. Details
    Workaround details.
-->
## <a name="known-issues-in-this-technical-preview"></a>Znane problemy w tej wersji Technical Preview
-   **Aktualizacja do nowej wersji zapoznawczej nie powiedzie się, jeśli masz serwer lokacji w trybie pasywnym**. Jeśli masz [serwera lokacji głównej w trybie pasywnym](/sccm/core/get-started/capabilities-in-technical-preview-1706#site-server-role-high-availability), a następnie przed uaktualnieniem do nowej wersji zapoznawczej musi odinstalować serwer lokacji w trybie pasywnym. Zakończone aktualizacji lokacji można ponownie zainstalować serwer lokacji w trybie pasywnym.

  Aby odinstalować serwer lokacji w trybie pasywnym:
  1. W konsoli programu Configuration Manager, przejdź do **administracji** > **omówienie** > **konfiguracja lokacji**  >  **Serwery i role systemu lokacji**, a następnie wybierz serwer lokacji w trybie pasywnym.
  2. W **ról systemu lokacji** okienku kliknij prawym przyciskiem myszy **serwera lokacji** roli, a następnie wybierz pozycję **Usuń rolę**.
  3. Kliknij prawym przyciskiem myszy na serwerze lokacji w trybie pasywnym, a następnie wybierz pozycję **usunąć**.
  4. Po odinstalowaniu serwera lokacji, na serwerze lokacji głównej active Uruchom ponownie usługę **CONFIGURATION_MANAGER_UPDATE**.
<!--sms 489412-->


</br>

**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  


## <a name="transition-endpoint-protection-workload-to-intune-using-co-management"></a>Obciążenia programu Endpoint Protection przejścia do usługi Intune przy użyciu wspólnej zarządzania    
<!-- 1357365 -->
W tej wersji można teraz przejście obciążenia programu Endpoint Protection z programu Configuration Manager do usługi Intune po włączeniu wspólnego zarządzania. Do przejścia obciążenia programu Endpoint Protection, przejdź do strony właściwości wspólnego zarządzania i przesuń suwak z programu Configuration Manager do **pilotażu** lub **wszystkich**. Aby uzyskać więcej informacji, zobacz [urządzenia zarządzania wspólnej dla systemu Windows 10](/sccm/core/clients/manage/co-management-overview).


 
## <a name="configure-windows-delivery-optimization-to-use-configuration-manager-boundary-groups"></a>Konfigurowanie optymalizacji dostarczania systemu Windows do użycia grup granic w programie Configuration Manager
<!-- 1324696 -->
Grupy granic w programie Configuration Manager służy do definiowania i uregulowanie dystrybucji zawartości w sieci firmowej i biurach zdalnych. [Optymalizacja dostarczania Windows](/windows/deployment/update/waas-delivery-optimization) jest oparta na chmurze, peer-to-peer technologii do udostępniania zawartości między urządzeniami z systemem Windows 10. Począwszy od tej wersji, skonfiguruj optymalizacji dostarczania do grup granic udostępniania zawartości między elementami równorzędnymi. Nowe ustawienie klienta stosuje identyfikator grupy granic, jako identyfikator grupy optymalizacji dostarczania na kliencie. Gdy klient komunikuje się z usługą w chmurze optymalizacji dostarczania, używa tego identyfikatora można zlokalizować elementów równorzędnych o żądanej zawartości. 

### <a name="prerequisites"></a>Wymagania wstępne
- Optymalizacja dostarczania jest dostępna tylko na klientów systemu Windows 10

### <a name="try-it-out"></a>Wypróbuj
 Spróbuj wykonać zadania. Wyślij **opinii** z **Home** karty wstążki zawiadomienie nas o tym, jak Ci poszło.

1. W konsoli programu Configuration Manager **administracji** roboczym **ustawień klienta** węźle, utworzyć zasady niestandardowe ustawienia urządzenia.
2. Wybierz nową **optymalizacji dostarczania** grupy.
3. Włącz ustawienie **grup granic Użyj Configuration Manager dla Identyfikatora grupy optymalizacji dostarczania**.

Aby uzyskać więcej informacji, zobacz **grupy** w trybie dostarczania w [opcje optymalizacji dostarczania](/windows/deployment/update/waas-delivery-optimization#group-id).



## <a name="windows-10-in-place-upgrade-task-sequence-via-cloud-management-gateway"></a>Sekwencji zadań uaktualniania w miejscu systemu Windows 10 za pośrednictwem bramy zarządzania w chmurze
<!-- 1357149 -->

Windows 10 [sekwencji zadań uaktualniania w miejscu](/sccm/osd/deploy-use/upgrade-windows-to-the-latest-version) teraz obsługuje wdrażanie na klientach internetowych zarządzanych za pomocą [brama zarządzania chmury](/sccm/core/clients/manage/plan-cloud-management-gateway). Dzięki tej możliwości użytkownicy zdalni łatwiej uaktualniania do systemu Windows 10, bez konieczności nawiązywania połączenia z siecią firmową. 

Upewnij się, cała zawartość odwołuje się sekwencja zadań uaktualniania w miejscu jest dystrybuowana do [punktu dystrybucji w chmurze](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point). W przeciwnym razie urządzenia nie można uruchomić sekwencji zadań.

Podczas wdrażania sekwencji zadań uaktualniania, należy użyć następujących ustawień:
- **Zezwalaj na sekwencję zadań do wykonania dla klienta w Internecie**, na karcie środowiska użytkownika wdrożenia.
- **Pobierz całą zawartość lokalnie przed uruchomieniem sekwencji zadań**, na karcie punktów dystrybucji wdrożenia. Inne opcje, takie jak **Pobierz zawartość lokalnie przez uruchomienie sekwencji zadań** nie działają w tym scenariuszu. Aparat sekwencji zadań nie może obecnie pobierać zawartość z punktu dystrybucji chmury. Klient programu Configuration Manager musi pobrać zawartość z punktu dystrybucji chmury przed uruchomieniem sekwencji zadań.
- (*Opcjonalnie*) **wstępnie pobrać zawartość do tej sekwencji zadań**, na karcie Ogólne we wdrożeniu. Aby uzyskać więcej informacji, zobacz [skonfigurować wstępne wypełnienie pamięci podręcznej](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#configure-pre-cache-content).



## <a name="improvements-to-windows-10-in-place-upgrade-task-sequence"></a>Ulepszenia dotyczące sekwencji zadań uaktualniania w miejscu systemu Windows 10
<!-- 1357425 -->
Domyślny szablon sekwencji zadań dla uaktualnienia w miejscu systemu Windows 10 zawiera teraz dodatkowe grupy z zalecane działania, aby dodać przed i po zakończeniu uaktualniania. Te akcje są wspólne dla wielu klientów, którzy pomyślnie uaktualniania urządzeń do systemu Windows 10. 

### <a name="new-groups-under-prepare-for-upgrade"></a>Nowe grupy w obszarze **przygotować do uaktualnienia**
- **Sprawdza baterii**: Dodaj kroki do tej grupy, aby sprawdzić, czy komputer używa baterii lub przewodowej zasilania. Ta akcja wymaga niestandardowego skryptu lub narzędzia do wykonania tego sprawdzenia.
- **Sieci/przewodowe połączenie kontroli**: Dodaj kroki do tej grupy, aby sprawdzić, czy komputer jest połączony z siecią, a nie korzysta z połączenia bezprzewodowego. Ta akcja wymaga niestandardowego skryptu lub narzędzia do wykonania tego sprawdzenia.
- **Usunięcia niezgodnych aplikacji**: Dodaj kroki do tej grupy, aby usunąć wszystkie aplikacje, które są niezgodne z tą wersją systemu Windows 10. Metoda do odinstalowania aplikacji może być różna. Jeśli aplikacja używa Instalatora Windows, skopiuj **program dezinstalacyjny** wiersz polecenia z **programy** karcie we właściwościach typu wdrażania aplikacji Instalatora Windows. Następnie dodaj **Uruchom wiersz polecenia** krok w tej grupie przy użyciu wiersza polecenia Odinstaluj program. Na przykład: </br>`msiexec /x {150031D8-1234-4BA8-9F52-D6E5190D1CBA} /q`</br> 
- **Usuń niezgodnych sterowników**: Dodaj kroki do tej grupy, aby usunąć wszystkie sterowniki, które nie są zgodne z tą wersją systemu Windows 10.
- **Usuń/zawiesić zabezpieczeń innych firm**: Dodaj kroki do tej grupy, usunięcia lub zawiesić programów zabezpieczeń innych firm, takich jak oprogramowanie antywirusowe.
   - Jeśli używasz programu szyfrowania dysku innych firm, podaj jej szyfrowania sterownika w Instalatorze systemu Windows z **/ReflectDrivers** [opcji wiersza polecenia](/windows-hardware/manufacture/desktop/windows-setup-command-line-options). Dodaj [Ustaw zmienną sekwencji zadań](/sccm/osd/understand/task-sequence-steps#BKMK_SetTaskSequenceVariable) krok do sekwencji zadań w tej grupie. Ustaw zmienną sekwencji zadań **OSDSetupAdditionalUpgradeOptions**. Ustaw wartość na **/ReflectDriver** ze ścieżką do sterownika. To [zmiennej akcji sekwencji zadań](/sccm/osd/understand/task-sequence-action-variables#upgrade-operating-system) dołącza wiersza polecenia Instalatora systemu Windows używane przez sekwencję zadań. Wszelkie dodatkowe wskazówki dotyczące tego procesu, skontaktuj się z dostawcą oprogramowania.

### <a name="new-groups-under-post-processing"></a>Nowe grupy w obszarze **przetwarzanie końcowe**
- **Zastosuj sterowniki instalacją**: Dodaj kroki do tej grupy, aby zainstalować sterowniki oparte na Instalatora (.exe) z pakietów.
- **Instalacja/enable zabezpieczeń innych firm**: Dodaj kroki do tej grupy, aby zainstalować lub włączyć programów zabezpieczeń innych firm, takich jak oprogramowanie antywirusowe. 
- **Ustaw aplikacji domyślne systemu Windows i skojarzenia**: Dodaj kroki opisane w tej grupie można ustawić aplikacji domyślne systemu Windows i skojarzeń plików. Najpierw przygotować komputer odniesienia z sieci skojarzenia żądanej aplikacji. Następnie uruchom następujące polecenie, aby wyeksportować: </br>`dism /online /Export-DefaultAppAssociations:"%UserProfile%\Desktop\DefaultAppAssociations.xml"`</br>Dodaj plik XML do pakietu. Następnie dodaj [Uruchom wiersz polecenia](/sccm/osd/understand/task-sequence-steps#BKMK_RunCommandLine) krok w tej grupie. Określ pakiet, który zawiera plik XML, a następnie wprowadzić następujący wiersz polecenia: </br>`dism /online /Import-DefaultAppAssociations:DefaultAppAssocations.xml`</br> Aby uzyskać więcej informacji, zobacz [eksportu lub importu domyślna skojarzenia aplikacji](/windows-hardware/manufacture/desktop/export-or-import-default-application-associations).
- **Zastosowanie dostosowań i personalizacji**: Dodaj kroki do tej grupy do stosowania dostosowania menu Start, takie jak organizowanie grup programu. Aby uzyskać więcej informacji, zobacz [dostosowywanie ekranu startowego](/windows-hardware/manufacture/desktop/customize-the-start-screen).

### <a name="additional-recommendations"></a>Zalecenia dodatkowe
- Przejrzyj dokumentację systemu Windows [błędy uaktualniania rozwiązać systemu Windows 10](/windows/deployment/upgrade/resolve-windows-10-upgrade-errors). Ten artykuł zawiera także szczegółowe informacje na temat procesu uaktualniania.
- Domyślny **Sprawdź gotowość** kroku, należy włączyć funkcję **zapewnić minimalną ilość wolnego miejsca (MB)**. Ustaw wartość na co najmniej **16384** (16 GB) dla 32-bitowego systemu operacyjnego pakietu, uaktualnienia lub **20480** (20 GB) dla wersji 64-bitowych. 
- Użyj **SMSTSDownloadRetryCount** [wbudowanej zmiennej sekwencji zadań](/sccm/osd/understand/task-sequence-built-in-variables) do pobierania zasady ponawiania. Obecnie domyślnie klient ponawia próbę dwukrotnie; Ta zmienna jest ustawiona dwóch (2). Jeśli klienci nie są na połączenie z firmową siecią przewodową, dodatkowych ponownych prób pomocy Uzyskaj zasady klienta. Za pomocą tej zmiennej powoduje, że nie negatywny wpływ po stronie niż błąd opóźnionego Jeśli nie można pobrać zasad.<!-- 501016 --> Również zwiększyć **SMSTSDownloadRetryDelay** zmiennej z domyślnej 15 sekund.
- Przeprowadzenie oceny zgodności wbudowanego. 
   - Dodaj drugi **Uaktualnij System operacyjny** krok wczesne **przygotować do uaktualnienia** grupy. Nadaj mu nazwę *oceny uaktualnienia*. Określ tego samego pakietu uaktualnienia, a następnie włącz opcję **skanowanie zgodności wykonywania Instalatora Windows bez rozpoczynania uaktualniania**. Włącz **Kontynuuj przy błędzie** na karcie Opcje. 
   - Natychmiast po tym *oceny uaktualnienia* kroku, należy dodać **Uruchom wiersz polecenia** kroku. Określ następujący wiersz polecenia:</br> `cmd /c exit %_SMSTSOSUpgradeActionReturnCode%`</br>Na **opcje** , Dodaj następujący warunek: </br>`Task Sequence Variable _SMSTSOSUpgradeActionReturnCode not equals 3247440400` </br>Tego kodu powrotnego jest wartość dziesiętną MOSETUP_E_COMPAT_SCANONLY (0xC1900210), czyli skanowania zgodności pomyślnie bez żadnych problemów. Jeśli *ocena uaktualnienia* krok zakończy się pomyślnie i zwraca ten kod, ten krok zostanie pominięty. W przeciwnym razie jeśli etap oceny zwraca innych kod powrotny, ten krok zakończy się niepowodzeniem sekwencji zadań z kodem powrotu z skanowanie zgodności Instalatora systemu Windows.
   - Aby uzyskać więcej informacji, zobacz [Uaktualnij system operacyjny](/sccm/osd/understand/task-sequence-steps#BKMK_UpgradeOS).
- Jeśli chcesz zmienić urządzenia z systemem BIOS do UEFI podczas tej sekwencji zadań, zobacz [Konwertowanie systemu BIOS na UEFI podczas uaktualniania w miejscu](/sccm/osd/deploy-use/task-sequence-steps-to-manage-bios-to-uefi-conversion#convert-from-bios-to-uefi-during-an-in-place-upgrade).

Wyślij **opinii** z **Home** karty wstążki, jeśli masz dodatkowe zalecenia lub sugestie.



## <a name="improvements-to-pxe-enabled-distribution-points"></a>Ulepszenia do punktów dystrybucji z włączoną obsługą środowiska PXE
<!-- 1357580 -->
Aby wyjaśnić zachowanie [nowych funkcji PXE](/sccm/core/get-started/capabilities-in-technical-preview-1706#pxe-network-boot-support-for-ipv6) po raz pierwszy wprowadzone w wersji zapoznawczej Technical Preview 1706, możemy zmienić nazwy **obsługi protokołu IPv6** opcji. Na **PXE** kartę Właściwości punktu dystrybucji, sprawdź **włączyć obiekt odpowiadający środowiska PXE bez usług wdrażania systemu Windows**. 

Ta opcja umożliwia obiekt odpowiadający środowiska PXE w punkcie dystrybucji, które nie wymagają usług wdrażania systemu Windows (WDS). Po włączeniu tej opcji nowego punktu dystrybucji, który jest już obsługą środowiska PXE programu Configuration Manager wstrzymuje usługi wdrażania systemu Windows. Jeśli możesz wyłączyć to nowa opcja, ale jest nadal **Włącz obsługę środowiska PXE dla klientów**, a następnie ponownie usług wdrażania systemu Windows umożliwia punktu dystrybucji.

Ponieważ usługi wdrażania systemu Windows nie jest wymagana, punktu dystrybucji obsługującego środowisko PXE może być serwera lub klienta systemu operacyjnego, systemu Windows Server Core. Nowej usługi obiektu odpowiadającego w środowisku PXE nadal obsługuje protokół IPv6, a także zwiększa elastyczność punktów dystrybucji z włączoną obsługą środowiska PXE w biurach zdalnych.

> [!NOTE]
> Ta usługa korzysta z tej samej technologii podstawowych jako [Usługa obiektu odpowiadającego w klienckich środowiska PXE](/sccm/core/get-started/capabilities-in-technical-preview-1712#client-based-pxe-responder-service) w wersji zapoznawczej Technical Preview 1712. Ta funkcja nie wymaga obciążenie roli punktu dystrybucji.

### <a name="multicast"></a>Multiemisji
Aby włączyć i skonfigurować multiemisji na **multiemisji** kartę Właściwości punktu dystrybucji, punktu dystrybucji należy użyć usług wdrażania systemu Windows. 
- Jeśli zostanie **Włącz obsługę środowiska PXE dla klientów** i **Włącz multiemisję w celu jednoczesnego wysyłania danych do wielu klientów**, a następnie można **włączyć obiekt odpowiadający środowiska PXE bez usług wdrażania systemu Windows** .
- Jeśli zostanie **Włącz obsługę środowiska PXE dla klientów** i **włączyć obiekt odpowiadający środowiska PXE bez usług wdrażania systemu Windows**, a następnie można **Włącz multiemisję w celu jednoczesnego wysyłania danych do wielu klientów**



## <a name="deployment-templates-for-task-sequences"></a>Szablony wdrażania dla sekwencji zadań
<!-- 1357391 -->
Kreator wdrażania dla sekwencji zadań można teraz utworzyć szablon wdrożenia. Szablon wdrożenia można zapisać i zastosowane do istniejącej lub nowej sekwencji zadań w celu utworzenia wdrożenia. 

### <a name="try-it-out"></a>Wypróbuj  
Spróbuj wykonać zadania. Wyślij **opinii** z **Home** karty wstążki zawiadomienie nas o tym, jak Ci poszło. 

 **Tworzenie szablonu wdrożenia nowego wdrożenia sekwencji zadań** <br/> 
1. W **Biblioteka oprogramowania** obszaru roboczego, rozwiń węzeł **systemów operacyjnych**i wybierz **sekwencje zadań**.
2. Kliknij prawym przyciskiem myszy w sekwencji zadań i wybierz **Wdróż**. 
3. Na **ogólne** karcie, należy pamiętać, jest teraz dostępna opcja **wybierz szablon wdrażania**. 
4. Kontynuuj **Kreatora wdrażania oprogramowania** wybranie ustawienia wdrożenia dla sekwencji zadań. 
5. Po przejściu **Podsumowanie** karcie **Kreatora wdrażania oprogramowania**, kliknij **Zapisz jako szablon**.
6. Nadaj nazwę szablonu, a następnie wybierz ustawienia do zapisania w szablonie. 
7. Kliknij przycisk **Zapisz**. Szablon jest teraz dostępna do użycia z **wybierz szablon wdrażania** opcji.



## <a name="product-lifecycle-dashboard"></a>Produkt cyklu życia w pulpit nawigacyjny
<!--1319632-->
Nowy [pulpitu nawigacyjnego cyklu życia produktów](/sccm/core/clients/manage/asset-intelligence/product-lifecycle-dashboard) przedstawia stan zasad cykl życia produktów firmy Microsoft dla produktów firmy Microsoft zainstalowane na urządzeniach zarządzanych przez program Configuration Manager. Pulpit nawigacyjny udostępnia informacje o produktach firmy Microsoft w środowisku, możliwości obsługi stanu i daty zakończenia wsparcia. Pulpit nawigacyjny umożliwia zrozumieć dostępność obsługi dla każdego produktu. 

Aby uzyskać dostępu do pulpitu nawigacyjnego cyklu życia, w konsoli programu Configuration Manager, przejdź do **zasoby i zgodność** >**analizy zasobów** >**cyklu życia produktów**



## <a name="improvements-to-reporting"></a>Ulepszenia dotyczące raportowania
<!--1357653-->
W [swoją opinię](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/32434147-new-builtin-reports-about-windows-10-versions-and) dodano nowy raport **szczegóły obsługi systemu Windows 10 dla określonej kolekcji**. Ten raport przedstawia identyfikator zasobu, nazwy NetBIOS, nazwa systemu operacyjnego, Nazwa wersji systemu operacyjnego, kompilacji, gałąź systemu operacyjnego i obsługi stanu dla urządzeń z systemem Windows 10. Aby uzyskać dostęp do raportu, przejdź do **monitorowanie** >**raportowania** >**raporty** >**systemów operacyjnych**  > **Szczegóły obsługi systemu Windows 10 dla określonej kolekcji**.



## <a name="improvements-to-software-center"></a>Ulepszenia Centrum oprogramowania
<!--1357592-->
W [swoją opinię](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/13002684-software-center-show-only-available-software-hid) zainstalowanych aplikacji teraz mogą być ukryte w programie Software Center. Aplikacje, które są już zainstalowane nie będą już wyświetlane na karcie aplikacje gdy ta opcja jest włączona. 

### <a name="try-it-out"></a>Wypróbuj
Włącz **Ukryj w programie Software Center zainstalowanych aplikacji** ustawienie w ustawieniach klienta programu Software Center. Gdy użytkownik końcowy instaluje aplikację, należy przyjrzeć się zachowaniu w Centrum oprogramowania.



## <a name="improvements-to-run-scripts"></a>Ulepszenia na uruchamianie skryptów
<!--1236459-->
[Uruchamianie skryptów](/sccm/apps/deploy-use/create-deploy-scripts) funkcja zwraca teraz skryptu wyjściowe JSON formatowania. Ten format spójnie zwraca dane wyjściowe skryptu do odczytu. Skrypty, których nie można uruchomić nie może pobrać dane wyjściowe zwrócone. 



## <a name="boundary-group-fallback-for-management-points"></a>Grupy granic rezerwowy dla punktów zarządzania
<!-- 1324594 -->
Począwszy od tej wersji, można skonfigurować relacje rezerwowy dla punktów zarządzania między [grup granic](/sccm/core/servers/deploy/configure/boundary-groups). To zachowanie zapewnia większą kontrolę dla punktów zarządzania używanych przez klientów. Na **relacje** karcie właściwości grupy granic, jest nową kolumnę dla punktu zarządzania. Podczas dodawania nowej grupy granic rezerwowego rezerwowy punkt zarządzania jest obecnie zawsze zero (0). To zachowanie jest takie samo dla **domyślne zachowanie** w domyślnej grupie granic lokacji.

Wcześniej, to powszechny problem występuje, gdy chroniony punkt zarządzania w bezpiecznej sieci. Zasady obejmujące tego punktu zarządzania chronionym, jest wyświetlany w klientom w sieci firmowej głównym, nawet jeśli nie mogli komunikować się z nim przez zaporę. Aby rozwiązać ten problem, należy użyć **nigdy rezerwowy** opcję, aby zapewnić, że tylko powrotu do zarządzania klientami wskazuje, z którym mogą komunikować.

Podczas uaktualniania lokacji do tej wersji, programu Configuration Manager doda wszystkie punkty zarządzania z systemem innym niż — internetowy w domyślnej grupie granic lokacji. To zachowanie zapewnia, że starsze wersje klienta do komunikowania się z punktami zarządzania. Aby w pełni korzystać z tej funkcji, należy przenieść punkty zarządzania do grup granic żądany.

Rezerwa grupy granic punktu zarządzania nie zmienia zachowanie podczas instalacji klienta (ccmsetup). Jeśli w wierszu polecenia nie określa początkowy punkt zarządzania za pomocą parametru /MP, nowy klient otrzymuje pełną listę dostępnych punktów zarządzania. Dla początkowego procesu ładowania początkowego klient używa pierwszego punktu zarządzania, który można uzyskać dostęp. Gdy klient rejestruje z lokacją, otrzymuje listę punktów zarządzania poprawnie sortowane z to nowe zachowanie. 

### <a name="prerequisites"></a>Wymagania wstępne
- Włącz [preferowanych punktów zarządzania](/sccm/core/servers/deploy/configure/boundary-groups#preferred-management-points). W konsoli programu Configuration Manager, przejdź do **administracji** obszaru roboczego. Rozwiń węzeł **konfiguracja lokacji** i wybierz **witryny**. Kliknij przycisk **ustawienia hierarchii** na Wstążce. Na **ogólne** pozycję Włącz **klienci wolą używać punktów zarządzania określonych w grupach granic**. 

### <a name="known-issues"></a>Znane problemy
- Procesy wdrażania systemu operacyjnego nie są znane grup granic.

### <a name="troubleshooting"></a>Rozwiązywanie problemów
Nowe wpisy zostaną wyświetlone w **LocationServices.log**. **Miejscowości** atrybut identyfikuje jeden z następujących stanów:
- 0: Nieznane
- 1: Z określonym punktem zarządzania jest tylko w grupie granic lokacji domyślnej jako metody rezerwowej
- 2: Z określonym punktem zarządzania znajduje się w grupie granic sąsiada lub zdalnym. Gdy punkt zarządzania jest zarówno sąsiada i domyślnych grup granic lokacji, lokalizacja jest 2.
- 3: Z określonym punktem zarządzania znajduje się w grupie granic lokalnego lub bieżący. Gdy punkt zarządzania znajduje się w bieżącej grupie granic, a także sąsiada lub domyślnej grupie granic lokacji, lokalizacja jest 3. Lokalizacja, jeśli preferowane punkty zarządzania w hierarchii ustawień nie zostanie włączone, jest zawsze 3 niezależnie od tego, które granic grupa punkt zarządzania znajduje się w.

Klienci używają punktów zarządzania lokalnego pierwszej (miejscowości 3), drugi zdalnego (miejscowości 2), a następnie powrotu (miejscowości 1). 

Gdy klient otrzymuje pięć błędy w ciągu 10 minut, a nie do komunikowania się z punktem zarządzania w jego bieżącej grupy granic, próbuje skontaktować się z punktem zarządzania w sąsiada lub w domyślnej grupie granic lokacji. Jeśli punkt zarządzania w bieżącej grupie granic później wraca do trybu online, klient powróci do punktu zarządzania lokalnego w następnym cyklu odświeżania. Cykl odświeżania jest 24 godzin lub po uruchomieniu usługi agenta programu Configuration Manager.



## <a name="improved-support-for-cng-certificates"></a>Ulepszona obsługa certyfikatów CNG
<!-- 1357314 -->
Wersja programu Configuration Manager (wersji current branch) 1710 obsługuje [kryptografii: Next Generation (CNG) certyfikaty](/sccm/core/plan-design/network/cng-certificates-overview). Obsługuje limity 1710 wersji do certyfikatów klienta w kilku scenariuszach. 

Począwszy od tej wersji technical preview, należy użyć certyfikatów CNG dla następujących ról serwera obsługującego protokół HTTPS:
- Punkt zarządzania
- Punkt dystrybucji
- Punkt aktualizacji oprogramowania

Lista [nieobsługiwanych scenariuszy](/sccm/core/plan-design/network/cng-certificates-overview#unsupported-scenarios) jest taka sama.



## <a name="cloud-management-gateway-support-for-azure-resource-manager"></a>Obsługa brama zarządzania usługi Azure Resource Manager w chmurze
<!-- 1324735 -->
Podczas tworzenia wystąpienia [brama zarządzania chmury](/sccm/core/clients/manage/plan-cloud-management-gateway) (CMG), Kreator udostępnia teraz opcję, aby utworzyć **wdrożenia usługi Azure Resource Manager**. [Usługa Azure Resource Manager](/azure/azure-resource-manager/resource-group-overview) nowoczesnych platforma do zarządzania wszystkimi zasobami rozwiązania jako pojedynczy element o nazwie [grupy zasobów](/azure/azure-resource-manager/resource-group-overview#resource-groups). W przypadku wdrażania CMG za pomocą Menedżera zasobów Azure, lokacji używa usługi Azure Active Directory (Azure AD) do uwierzytelniania i Utwórz zasoby niezbędne chmury. To wdrożenie zmodernizowanej nie wymaga certyfikatu zarządzania platformy Azure w klasycznym.  

Kreator CMG nadal udostępnia opcję **wdrożenia usługi klasycznego** używa certyfikatu zarządzania platformy Azure. Aby uprościć wdrażanie i zarządzanie zasobami, zaleca się przy użyciu modelu wdrażania usługi Azure Resource Manager dla wszystkich nowych wystąpień CMG. Jeśli to możliwe należy ponownie wdrożyć istniejących wystąpień CMG za pomocą Menedżera zasobów.

Programu Configuration Manager nie może zmigrować istniejących wystąpień CMG klasycznego modelu wdrażania usługi Azure Resource Manager. Tworzenie nowych wystąpień CMG przy użyciu wdrożenia usługi Azure Resource Manager, a następnie usuń wystąpienia CMG klasycznego. 

> [!IMPORTANT]
> Ta funkcja nie obsługuje dla dostawców usług Azure chmurze (CSP). Wdrożenie CMG z usługi Azure Resource Manager w dalszym ciągu używa usługi w chmurze klasycznego, który nie obsługuje dostawca usług Kryptograficznych. Aby uzyskać więcej informacji, zobacz [dostępnych usług Azure w dostawcy usług Kryptograficznych Azure](/azure/cloud-solution-provider/overview/azure-csp-available-services).  

### <a name="prerequisites"></a>Wymagania wstępne
- Integracja z [usługi Azure AD](/sccm/core/clients/deploy/deploy-clients-cmg-azure). Odnajdowanie użytkowników usługi Azure AD nie jest wymagane.
- Taki sam [wymagania dotyczące bramy zarządzania chmury](/sccm/core/clients/manage/plan-cloud-management-gateway#requirements-for-cloud-management-gateway), z wyjątkiem certyfikat zarządzania platformy Azure.

### <a name="try-it-out"></a>Wypróbuj  
 Spróbuj wykonać zadania. Wyślij **opinii** z **Home** karty wstążki zawiadomienie nas o tym, jak Ci poszło.

1. W konsoli programu Configuration Manager **administracji** obszaru roboczego, rozwiń węzeł **usługi w chmurze**i wybierz **brama zarządzania chmury**. Kliknij przycisk **Tworzenie bramy zarządzania chmury** na Wstążce. 
2. Na **ogólne** wybierz pozycję **wdrożenia usługi Azure Resource Manager**. Kliknij przycisk **Zaloguj** do uwierzytelniania przy użyciu konta administratora subskrypcji platformy Azure. Kreator automatycznego wypełniania pozostałe pola z informacji o subskrypcji usługi Azure AD, przechowywane podczas integracji wymagań wstępnych. Jeśli masz wiele subskrypcji wybierz odpowiednią subskrypcję. Kliknij przycisk **Dalej**.  
3. Na **ustawienia** Podaj plik certyfikatu PKI serwera w zwykły sposób. Ten certyfikat umożliwia określenie nazwy usługi CMG na platformie Azure. Wybierz **Region**, a następnie wybierz opcję grupy zasobów, albo **Utwórz nowy** lub **Użyj istniejącego**. Wprowadź nazwę nowej grupy zasobów lub wybierz istniejącą grupę zasobów z listy rozwijanej. 
4. Ukończ pracę kreatora.

> [!NOTE] 
> Dla wybranej usługi Azure AD aplikacji serwera Azure przypisuje subskrypcji **współautora** uprawnienia. 

Monitorowanie postępu wdrożenia usługi za pomocą **cloudmgr.log** w punkcie połączenia usługi.



## <a name="approve-application-requests-for-users-per-device"></a>Zatwierdzanie żądań aplikacji dla użytkowników na urządzenie
<!-- 1357015 -->
Uruchamianie w tej wersji, gdy użytkownik zażąda aplikację wymagającej zatwierdzenia, nazwę określonego urządzenia jest teraz częścią żądania. Administrator zatwierdza żądanie, użytkownik jest tylko możliwość instalowania aplikacji na tym urządzeniu. Użytkownik musi przesłać innego żądania, aby zainstalować aplikację na innym urządzeniu. 

> [!NOTE]
> Ta funkcja jest opcjonalne. Podczas aktualizacji do tej wersji, należy włączyć tę funkcję w Kreatorze aktualizacji. Można również włączyć funkcję w konsoli później. Aby uzyskać więcej informacji, zobacz [Włącz funkcje opcjonalne aktualizacji](/sccm/core/servers/manage/install-in-console-updates#bkmk_options).

### <a name="prerequisites"></a>Wymagania wstępne
- Uaktualnij do najnowszej wersji klienta programu Configuration Manager
- Włącz ustawienie klienta **Użyj nowego centrum oprogramowania** w [agent komputera](/sccm/core/clients/deploy/about-client-settings#computer-agent) grupy

### <a name="try-it-out"></a>Wypróbuj
 Spróbuj wykonać zadania. Wyślij **opinii** z **Home** karty wstążki zawiadomienie nas o tym, jak Ci poszło.

1. Wdrażanie aplikacji jako dostępne do kolekcji użytkowników.
2. Na **ustawienia wdrażania** strony, włącz opcję: **Administrator musi zatwierdzić żądanie dla tej aplikacji na urządzeniu**.
3. Jako użytkownik docelowych Prześlij żądanie do aplikacji przy użyciu programu Software Center. 
4. Widok **żądań zatwierdzenia** w obszarze **Zarządzanie aplikacjami** w **Biblioteka oprogramowania** obszaru roboczego w konsoli programu Configuration Manager. Obecnie **urządzenia** kolumny na liście dla każdego żądania. Po wykonaniu akcji na żądanie żądań aplikacji w oknie dialogowym także nazwa urządzenia, z którego użytkownik przesłane żądanie.



## <a name="use-software-center-to-browse-and-install-user-available-applications-on-azure-ad-joined-devices"></a>Przeglądanie i instalowanie aplikacji dostępne dla użytkowników na urządzeniach przyłączonych do usługi AD platformy Azure przy użyciu programu Software Center
<!-- 1322613 -->
W przypadku wdrażania aplikacji jako dostępnych dla użytkowników mogą teraz Przeglądaj i zainstalować je za pomocą Centrum oprogramowania na urządzeniach w usłudze Azure Active Directory (Azure AD).  

### <a name="prerequisites"></a>Wymagania wstępne
- Włącz protokół HTTPS w punkcie zarządzania
- Integracja lokacji z [usługi Azure AD](/sccm/core/clients/deploy/deploy-clients-cmg-azure)
- Wdrażanie aplikacji jako dostępne do kolekcji użytkowników
- Dystrybuuj zawartość aplikacji do [punktu dystrybucji w chmurze](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point)
- Włącz ustawienie klienta **Użyj nowego centrum oprogramowania** w [agent komputera](/sccm/core/clients/deploy/about-client-settings#computer-agent) grupy
- Klient musi mieć: 
   - Windows 10
   - Azure przyłączonych do usługi AD, znanej także jako chmury przyłączonych do domeny
- Do obsługi klientów internetowych:
    - [Brama zarządzania w chmurze](/sccm/core/clients/manage/plan-cloud-management-gateway) 
    - Włącz ustawienie klienta: **Włącz żądania zasad użytkownika od klientów internetowych** w [zasady klienta](/sccm/core/clients/deploy/about-client-settings#client-policy) grupy
- Do obsługi klientów w sieci firmowej:
    - Dodaj punkt dystrybucji w chmurze do grupy granic używane przez klientów
    - Klienci muszą być w stanie rozpoznać w pełni kwalifikowaną nazwę (FQDN) punktu zarządzania z włączonym protokołem HTTPS



## <a name="report-on-windows-autopilot-device-information"></a>Raport dotyczący informacji o urządzeniu AutoPilot systemu Windows
<!-- 1351442 -->
AutoPilot systemu Windows to rozwiązanie dotyczące dołączania i konfigurowania nowych urządzeń z systemem Windows 10 w nowoczesnych sposób. Aby uzyskać więcej informacji, zobacz [omówienie Windows AutoPilot](https://docs.microsoft.com/windows/deployment/windows-autopilot/windows-10-autopilot). Jedną z metod rejestrowania istniejących urządzeń z systemem Windows AutoPilot jest przekazywanie informacji o urządzeniu do Store firmy Microsoft dla firm i Education. Informacje te obejmują numer seryjny urządzenia, identyfikator produktu systemu Windows i identyfikatora sprzętu. Zbieranie i raportowanie informacji tego urządzenia przy użyciu Menedżera konfiguracji. 

### <a name="prerequisites"></a>Wymagania wstępne
- Informacje o urządzeniu ma zastosowanie tylko do klientów w systemie Windows 10, wersja 1703 i nowsze

### <a name="try-it-out"></a>Wypróbuj
 Spróbuj wykonać zadania. Wyślij **opinii** z **Home** karty wstążki zawiadomienie nas o tym, jak Ci poszło.

1. W konsoli programu Configuration Manager **monitorowanie** obszaru roboczego, rozwiń węzeł **raportowania** węzła, rozwiń węzeł **raporty**i wybierz **sprzęt — ogólne**  węzła.
2. Uruchom nowy raport **informacje o urządzeniu AutoPilot Windows** i wyświetlić wyniki. 
3. W podglądzie raportów kliknij **wyeksportować** ikonę, a następnie wybierz **CSV (rozdzielany przecinkami)** opcji.
4. Po zapisaniu pliku, należy przekazać dane do Microsoft Store dla firm i Education. Aby uzyskać więcej informacji, zobacz [urządzenia można dodać na Microsoft Store dla firm i Education](https://docs.microsoft.com/microsoft-store/add-profile-to-devices#add-devices-and-apply-autopilot-deployment-profile). 



## <a name="improvements-to-configuration-manager-policies-for-windows-defender-exploit-guard"></a>Ulepszenia zasad programu Configuration Manager dla usługi Windows Defender wykorzystać zabezpieczenia
<!-- 1356220 -->
Dodatkowe ustawienia zasad dla składników służącym do zmniejszania możliwości ataków i kontrolowane dostępu do folderu zostały dodane w programie Configuration Manager dla [Windows Defender wykorzystać zabezpieczenia](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-exploit-guard/windows-defender-exploit-guard).

**Nowe ustawienia dla dostępu do folderu kontrolowanych**<br/>
Podczas konfigurowania dostępu do folderu kontrolowanych istnieją dwie dodatkowe opcje: **Blokuj tylko sektory dysku mają** i **inspekcji sektory dysku mają tylko**. Te dwa ustawienia dostęp do kontrolowanych folderu można włączyć tylko sektory rozruchowe i nie obsługuje ochrony foldery lub foldery domyślne chronione. 

**Nowe ustawienia dla służącym do zmniejszania możliwości ataków**
- Użyj zaawansowaną ochronę przed ransomware.
- Blokowanie kradzież podsystemu Windows urzędu zabezpieczeń lokalnych poświadczeń. 
- Blokowanie plików wykonywalnych, chyba że spełniają one występowania, wieku lub lista zaufanych kryteriów. 
- Blok procesów niezaufanych i bez znaku, które uruchamiane z dysku USB.



## <a name="microsoft-edge-browser-policies"></a>Zasady przeglądarki Microsoft Edge
<!-- 1357310 -->
Dla klientów, którzy korzystają z [Microsoft Edge](https://technet.microsoft.com/microsoft-edge/bb265256) przeglądarki sieci web na klientach systemu Windows 10, możesz teraz utworzyć zasady ustawień zgodności programu Configuration Manager, aby skonfigurować kilka ustawień Microsoft Edge. Ta zasada zawiera obecnie następujące ustawienia:
- **Przeglądarki Microsoft Edge Ustaw jako domyślny**: konfiguruje ustawienia aplikacji systemu Windows 10 domyślną przeglądarką sieci web Microsoft Edge
- **Zezwalaj na adres paska listy rozwijanej**: Wymaga systemu Windows 10 w wersji 1703 lub nowszej. Aby uzyskać więcej informacji, zobacz [AllowAddressBarDropdown przeglądarki zasad](/windows/client-management/mdm/policy-csp-browser#browser-allowaddressbardropdown).
- **Zezwalaj na ulubione synchronizacji między przeglądarki Microsoft**: Wymaga systemu Windows 10 w wersji 1703 lub nowszej. Aby uzyskać więcej informacji, zobacz [SyncFavoritesBetweenIEAndMicrosoftEdge przeglądarki zasad](/windows/client-management/mdm/policy-csp-browser#browser-syncfavoritesbetweenieandmicrosoftedge).
- **Zezwalaj na przeglądanie Wyczyść dane na wyjściu**: Wymaga systemu Windows 10 w wersji 1703 lub nowszej. Aby uzyskać więcej informacji, zobacz [ClearBrowsingDataOnExit przeglądarki zasad](/windows/client-management/mdm/policy-csp-browser#browser-clearbrowsingdataonexit).
- **Zezwalaj na nagłówki nie Śledź**: Aby uzyskać więcej informacji, zobacz [AllowDoNotTrack przeglądarki zasad](/windows/client-management/mdm/policy-csp-browser#browser-allowdonottrack).
- **Zezwalaj na automatyczne uzupełnianie**: Aby uzyskać więcej informacji, zobacz [AllowAutofill przeglądarki zasad](/windows/client-management/mdm/policy-csp-browser#browser-allowautofill).
- **Zezwalaj na pliki cookie**: Aby uzyskać więcej informacji, zobacz [AllowCookies przeglądarki zasad](/windows/client-management/mdm/policy-csp-browser#browser-allowcookies).
- **Zezwalaj na blokowanie wyskakujących okienek**: Aby uzyskać więcej informacji, zobacz [AllowPopups przeglądarki zasad](/windows/client-management/mdm/policy-csp-browser#browser-allowpopups).
- **Zezwalaj na podpowiedzi wyszukiwania na pasku adresu**: Aby uzyskać więcej informacji, zobacz [AllowSearchSuggestionsinAddressBar przeglądarki zasad](/windows/client-management/mdm/policy-csp-browser#browser-allowsearchsuggestionsinaddressbar).
- **Zezwalaj na wysyłanie ruchu intranetowego do programu Internet Explorer**: Aby uzyskać więcej informacji, zobacz [SendIntranetTraffictoInternetExplorer przeglądarki zasad](/windows/client-management/mdm/policy-csp-browser#browser-sendintranettraffictointernetexplorer).
- **Zezwalaj na hasło Menedżera**: Aby uzyskać więcej informacji, zobacz [AllowPasswordManager przeglądarki zasad](/windows/client-management/mdm/policy-csp-browser#browser-allowpasswordmanager).
- **Zezwalaj na Developer Tools**: Aby uzyskać więcej informacji, zobacz [AllowDeveloperTools przeglądarki zasad](/windows/client-management/mdm/policy-csp-browser#browser-allowdevelopertools).
- **Zezwalaj na rozszerzenia**: Aby uzyskać więcej informacji, zobacz [AllowExtensions przeglądarki zasad](/windows/client-management/mdm/policy-csp-browser#browser-allowextensions).

### <a name="prerequisites"></a>Wymagania wstępne
- Klient systemu Windows 10, które są przyłączone do usługi Azure Active Directory. 

### <a name="known-issues"></a>Znane problemy
- Urządzeń przyłączonych do domeny lokalnej nie można zastosować te zasady w tej wersji. Ten problem dotyczy również hybrydowych urządzeń przyłączonych do domeny.

### <a name="try-it-out"></a>Wypróbuj  
 Spróbuj wykonać zadania. Wyślij **opinii** z **Home** karty wstążki zawiadomienie nas o tym, jak Ci poszło.

**Tworzenie zasad**
1. W konsoli programu Configuration Manager, przejdź do **zasoby i zgodność** obszaru roboczego. Rozwiń węzeł **ustawień zgodności** i wybierz nową **profile przeglądarki Edge Microsoft** węzła. Kliknij opcję wstążki **Utwórz zasady przeglądarki Microsoft Edge**.
2. Określ **nazwa** zasad, opcjonalnie wprowadzić **opis**i kliknij przycisk **dalej**.
3. Na **ustawienia** strony, zmień wartość na **skonfigurowana** ustawień do uwzględnienia w tych zasad, a następnie kliknij przycisk **dalej**.
4. Na **obsługiwane platformy** Wybierz wersje systemów operacyjnych i architektur, do których ta zasada ma zastosowanie i kliknij przycisk **dalej**. 
5. Ukończ pracę kreatora.

**Wdrażanie zasad**
1. Wybierz zasady, a następnie kliknij opcję wstążki do **Wdróż**.
2. Kliknij przycisk **Przeglądaj** aby wybrać kolekcję użytkowników lub urządzeń, dla której chcesz wdrożyć zasady. 
3. Wybierz dodatkowe opcje, w razie potrzeby. Generować alerty, gdy zasady są niezgodne. Ustaw harmonogram, według której klient oceni zgodności urządzenia z tymi zasadami.
4. Kliknij przycisk **OK** utworzyć wdrożenie.

Podobnie jak wszelkie zasady ustawień zgodności ustawienia zgodnie z harmonogramem, które określisz rozwiąże problemy z klienta. [Monitor i tworzenia raportów dotyczących zgodności urządzeń](/sccm/compliance/deploy-use/monitor-compliance-settings) w konsoli programu Configuration Manager.



## <a name="report-for-default-browser-counts"></a>Raport dotyczący liczby przeglądarka domyślna
<!-- 1357830 -->
Teraz jest nowy raport do wyświetlenia liczba klientów z przeglądarką internetową określonego jako domyślny systemu Windows. 

### <a name="known-issues"></a>Znane problemy
- Przy pierwszym otwarciu raportu, pokazywane są tylko liczby i nie BrowserProgID. Aby obejść ten problem, Edytuj zapytanie raportu do następującej składni:  
    `select BrowserProgId00 as BrowserProgId, Count(*) as Count`  
    `from DEFAULT_BROWSER_DATA as dbd`  
    `group by BrowserProgId00`

### <a name="try-it-out"></a>Wypróbuj  
 Spróbuj wykonać zadania. Wyślij **opinii** z **Home** karty wstążki zawiadomienie nas o tym, jak Ci poszło.
1. W **programu Configuration Manager** konsoli **monitorowanie** obszaru roboczego, rozwiń węzeł **raportowania**, rozwiń węzeł **raporty**, wybierz **Oprogramowanie — firmy i produkty**.
2. Uruchom **liczby domyślnej przeglądarki** raportu.

Użyj następującego odwołania dla typowych BrowserProgIDs:
- **AppXq0fevzme2pys62n3e0fbqa7peapykr8v**: Microsoft Edge
- **IE.HTTP**: Microsoft Internet Explorer
- **ChromeHTML**: Google Chrome
- **OperaStable**: Opera oprogramowania
- **FirefoxURL-308046B0AF4A39CB**: Mozilla Firefox



## <a name="support-for-windows-10-arm64-devices"></a>Obsługa urządzeń z systemem Windows 10 ARM64
<!-- 1353704 -->
Począwszy od tej wersji klienta programu Configuration Manager jest obsługiwana na urządzeniach z systemem Windows 10 ARM64. Istniejące funkcje zarządzania klient powinien współpracować z tych nowych urządzeń. Na przykład sprzętu i spisu oprogramowania, aktualizacji oprogramowania i zarządzania aplikacjami. Wdrożenie systemu operacyjnego nie jest obecnie obsługiwane. 

## <a name="changes-to-phased-deployments"></a>Zmiany do wdrożenia etapowego
<!-- 1357405 -->
Wdrożenia etapowego zautomatyzować skoordynowane, Sekwencyjna wdrażanie oprogramowania w wielu kolekcjach. W tej wersji Technical Preview można wykonać kreatora etapowego wdrażania dla sekwencji zadań w konsoli administracyjnej i wdrożenia są tworzone. Jednak na drugim etapie nie zostanie uruchomiony automatycznie po spełniające kryteria sukcesu fazy pierwszego. Na drugim etapie można uruchomić ręcznie za pomocą instrukcji SQL.   

### <a name="try-it-out"></a>Wypróbuj  
  Spróbuj wykonać zadania. Wyślij **opinii** z **Home** karty wstążki zawiadomienie nas o tym, jak Ci poszło.
 
**Tworzenie wdrożenia fazowego dla sekwencji zadań** </br>
1. W **Biblioteka oprogramowania** obszaru roboczego, rozwiń węzeł **systemów operacyjnych**i wybierz **sekwencje zadań**.
2. Kliknij prawym przyciskiem myszy na istniejącej sekwencji zadań i wybierz **tworzenia wdrożenia stopniowo**. 
3. Na **ogólne** karcie, określ etapowego wdrażania nazwę, opis (opcjonalnie) i wybierz **automatycznie Utwórz wdrożenie fazy dwa domyślne**. 
4. Wypełnij **pierwsza kolekcja** i **druga Kolekcja** pola. Wybierz **dalej**.
5. Na **ustawienia** , wybierz jedną z opcji dla każdego ustawienia planowania i wybierz **dalej** po zakończeniu. 
6. Na **fazy** karcie, Edytuj poszczególnych faz, jeśli to konieczne, a następnie kliknij przycisk **dalej**.
7. Potwierdź wybrane opcje na **Podsumowanie** karcie, a następnie kliknij przycisk **dalej** aby kontynuować.
8. Po osiągnięciu kryteria sukcesu fazy pierwszego postępuj zgodnie z instrukcjami, można uruchomić na drugim etapie za pomocą instrukcji SQL.
 
**Drugi etap rozpoczynać się od instrukcji SQL**
1. Zidentyfikuj PhasedDeploymentID wdrożenia utworzone za pomocą następującej kwerendy SQL:<br/> `Select * from PhasedDeployment`
2. Uruchom następującą instrukcję można uruchomić na etapie produkcji:<br/> `UPDATE PhasedDeployment SET EvaluatePhasedDeployment = 1, Action = 3 WHERE PhasedDeploymentID = <Phased Deployment ID>`


## <a name="next-steps"></a>Następne kroki
Uzyskać informacji dotyczących instalowania lub aktualizowania gałęzi wersji zapoznawczej technical preview, zobacz [Technical Preview programu System Center Configuration Manager](/sccm/core/get-started/technical-preview).    
