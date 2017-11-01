---
title: Funkcje w wersji zapoznawczej Technical Preview 1701
titleSuffix: Configuration Manager
description: "Dowiedz się więcej o funkcjach dostępnych w wersji zapoznawczej Technical Preview programu System Center Configuration Manager, wersja 1701."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 18598eaa-1131-44ff-8f8b-6093e87ac7a1
caps.latest.revision: "5"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 56c2ceea56eec984715d61f8d195c1b47fd3c571
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="capabilities-in-technical-preview-1701-for-system-center-configuration-manager"></a>Funkcje w wersji Technical Preview 1701 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*



W tym artykule przedstawiono funkcje, które są dostępne w wersji Technical Preview programu System Center Configuration Manager, wersja 1701. Można zainstalować tę wersję, aby zaktualizować i dodać nowe funkcje do lokacji programu Configuration Manager technical preview. Przed zainstalowaniem tej wersji technical Preview, przejrzyj temat wprowadzający [Technical Preview programu System Center Configuration Manager](../../core/get-started/technical-preview.md), aby zapoznać się z ogólne wymagania i ograniczenia dotyczące używania wersji technical preview, jak zaktualizować między wersjami i sposobu wyrazić swoją opinię na temat funkcji w wersji technical preview.    


**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  

## <a name="boundary-groups-improvements-for-software-update-points"></a>Punkty aktualizacji ulepszenia grup granic dla oprogramowania
Począwszy od tej wersji zapoznawczej, możesz teraz używać grup granic do skojarzenia z klientów z punktów aktualizacji oprogramowania. Jest to część kontynuowanie pracy, aby rozwinąć zmian w grupach granic w celu zarządzania dodatkowe role systemu lokacji.  Zmiany dotyczące grupy granic została wprowadzona w Technical Preview 1609 i w wersji 1610 bieżącej gałęzi.  

W tej wersji zapoznawczej można użyć nowych granic zachowanie grupy do zarządzania punktów aktualizacji oprogramowania, których klient może używać, podobnie jak zarządzać punktu dystrybucji, których klient może używać:  

- Konfigurowania grup granic można skojarzyć jedną lub więcej serwerów, które hostują oprogramowania punktu aktualizacji.
- Klienci, którzy szukają nowy punkt aktualizacji oprogramowania podejmie próbę użycia, który jest skojarzony z grupą granic, ich bieżący.
- Gdy klient nie może nawiązać połączenia ich aktualne oprogramowanie punktu aktualizacji i nie można odnaleźć jednego z jego bieżącej grupy granic, klient używa rezerwowej zachowanie do zwiększenia dostępnej puli punktów aktualizacji oprogramowania, które mogą być używane.    

Aby uzyskać więcej informacji dotyczących grup granic, zobacz [grup granic](/sccm/core/servers/deploy/configure/boundary-groups) w zawartości dla bieżącej gałęzi.

Jednak w tej wersji zapoznawczej grup granic dla punktów aktualizacji oprogramowania są tylko częściowo zaimplementowany. Można dodać punktów aktualizacji oprogramowania i skonfigurować grupy granic sąsiada, zawierające punkty aktualizacji oprogramowania, rezerwowy czasu dla punktów aktualizacji oprogramowania nie jest jeszcze obsługiwana, ale, a klientów będzie czekać dwie godziny przed uruchomieniem rezerwowego.

Poniżej przedstawiono zachowania dla punktów aktualizacji oprogramowania z tej wersji technical preview:  

-   **Nowi klienci używają grup granic do punktów aktualizacji oprogramowania, zaznaczyć** klienta instalacji po instalacji wersji 1701 wybiera skojarzonych z grupą granic klienta punktu aktualizacji oprogramowania.

  Spowoduje to zastąpienie poprzedniego zachowanie, gdzie klienci wybierają punkt aktualizacji oprogramowania losowo z listy osób mających lasu klientów.   

-   **Wcześniej zainstalowanych klientów nadal używać ich bieżący punkt aktualizacji oprogramowania do nich rezerwowy można znaleźć nową.**
Klientów, które poprzednio były zainstalowane i które mają już punkt aktualizacji oprogramowania będą w dalszym ciągu używać tego punktu aktualizacji oprogramowania do nich rezerwowy. Obejmuje to punkty aktualizacji oprogramowania, które nie są skojarzone z grupą granic bieżącego klienta. Ich nie natychmiast należy znaleźć i używać punktu aktualizacji oprogramowania z ich bieżącej grupy granic.

  Umożliwia to nowe zachowanie grupy granic tylko wtedy, gdy klient nie powiedzie się do bieżącego punktu aktualizacji oprogramowania i uruchamia rezerwowy rozpoczyna się klienta, który ma już punkt aktualizacji oprogramowania.
To opóźnienie w przełączenie za pośrednictwem na nowe zachowanie jest zamierzone. Jest to spowodowane Zmiana punktu aktualizacji oprogramowania może spowodować duże wykorzystanie przepustowości sieci, jak klient synchronizuje dane z nowego punktu aktualizacji oprogramowania. Opóźnienie w przejście może pomóc uniknąć nasycenia sieci, na wszystkich klientach przełącznik nowe oprogramowanie zaktualizować punkty w tym samym czasie.

-   **Konfiguracje rezerwowy czas:** Konfiguracje dla rozpoczęcia powrotu do wyszukiwania dla nowego punktu aktualizacji oprogramowania klienci nie są obsługiwane w tej wersji technical preview. Dotyczy to również konfiguracje dla **powrotu czas (w minutach)** i **nigdy rezerwowy**, że można skonfigurować dla różnych granic relacje grupy.

  Zamiast tego klienci zachowują ich bieżące zachowanie, w którym klient próbuje połączyć się jego bieżący punkt aktualizacji oprogramowania przez dwie godziny przed rozpoczęciem rezerwowej, aby znaleźć nowego punktu aktualizacji oprogramowania, którego może użyć.

  Korzystając z klienta rezerwowe, aby utworzyć pulę punktów aktualizacji oprogramowania dostępne zostanie użyty konfiguracjach grupy granic na rezerwowe. Ta pula zawiera wszystkie punkty aktualizacji oprogramowania z klientów *bieżącą grupę granic*, *sąsiada grup granic*oraz klientów programu *grupy granic domyślnej witryny*.

- **Skonfiguruj grupy granic lokacji domyślne:**  
 Rozważ dodanie punktu aktualizacji oprogramowania do *domyślna--grupy granic lokacji&lt;kod lokacji >*. Dzięki temu klientów, które nie są elementami członkowskimi innej grupy granic można powrotu można znaleźć na oprogramowanie w punkcie aktualizacji.


Aby zarządzać punktów aktualizacji oprogramowania do grup granic, należy użyć [procedur z dokumentacji Current Branch](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#procedures-for-boundary-groups), należy jednak pamiętać, że rezerwowy godziny można skonfigurować nie są jeszcze używane dla punktów aktualizacji oprogramowania.


## <a name="hardware-inventory-collects-uefi-information"></a>Spisu sprzętu zbiera informacje z interfejsem UEFI
Nową klasę spisu sprzętu (**SMS_Firmware**), a właściwość (**UEFI**) są dostępne pomóc w określeniu, czy komputer jest uruchamiany w trybie UEFI. Gdy komputer jest uruchamiany w trybie UEFI, **UEFI** właściwość jest ustawiona na **TRUE**. Ta opcja jest włączona w spisie sprzętu, domyślnie. Aby uzyskać więcej informacji dotyczących zapasów sprzętu, zobacz [jak skonfigurować spis sprzętu](/sccm/core/clients/manage/inventory/configure-hardware-inventory).

## <a name="improvements-to-operating-system-deployment"></a>Ulepszenia dotyczące wdrażania systemu operacyjnego
Wprowadzono następujące ulepszenia do wdrożenia systemu operacyjnego, z których wiele zostały wynik opinii głosu użytkownika.
- [**Obsługa więcej aplikacji dla kroku sekwencji zadań Zainstaluj aplikacje**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/17062207-task-sequence-allow-more-than-9-applications-in-t): Udało nam się zwiększyć maksymalną liczbę aplikacji, które można zainstalować do 99 w **instalowanie aplikacji** krok sekwencji zadań. Poprzednie maksymalną liczbę został 9 aplikacji.
- [**Wybierz wiele aplikacji w kroku sekwencji zadań zainstaluj aplikację**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/15459978-when-adding-items-to-an-install-application-step): Po dodaniu aplikacji do sekwencji zadań zainstaluj aplikację kroku w edytorze sekwencji zadań, można teraz wybrać wiele aplikacji z **wybierz aplikację do zainstalowania** okienka.
- [**Ważność nośnika autonomicznego**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/14448564-provide-a-method-for-expiring-standalone-media): Podczas tworzenia nośnika autonomicznego, istnieją nowe opcje można ustawić opcjonalny daty rozpoczęcia i wygaśnięcia na nośniku. Te ustawienia są domyślnie wyłączone. Dane są porównywane z czasem systemowym na komputerze przed uruchomieniem nośnika autonomicznego. Gdy czas systemowy jest wcześniejsza niż godzina rozpoczęcia lub późniejsza niż godzina wygaśnięcia, nośnika samodzielnego nie jest uruchomiona. Te opcje są również dostępne za pomocą polecenia cmdlet New-CMStandaloneMedia środowiska PowerShell.
- [**Obsługę dodatkowej zawartości w nośniku samodzielnym**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/8341257-support-installation-of-packages-apps-via-dynamic): Dodatkowa zawartość jest teraz obsługiwana w przypadku nośników autonomicznych. Możesz wybrać dodatkowe pakiety, pakiety sterowników i aplikacji do przemieszczony na nośniku oraz zawartość, do którego odwołuje się sekwencja zadań. Wcześniej tylko zawartość, do którego odwołuje się sekwencja zadań została umieszczone na nośniku autonomicznym.
- [**Można skonfigurować limit czasu dla kroku sekwencji zadań automatycznie Zastosuj sterownik**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/17153660-auto-apply-driver-timeout): Nowe zmienne sekwencji zadań są teraz dostępne do konfigurowania wartość limitu czasu w kroku sekwencji zadań automatycznie Zastosuj sterownik podczas tworzenia żądania HTTP katalogu. Dostępne są następujące zmienne i wartości domyślnych (w sekundach):
   - Domyślnie SMSTSDriverRequestResolveTimeOut: 60
   - Domyślnie SMSTSDriverRequestConnectTimeOut: 60
   - Domyślnie SMSTSDriverRequestSendTimeOut: 60
   - Domyślnie SMSTSDriverRequestReceiveTimeOut: 480
- [**Identyfikator pakietu jest teraz wyświetlany w krokach sekwencji zadań**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/16167430-display-packageid-when-viewing-a-task-sequence-ste): Dowolny etap sekwencji zadań odwołuje się do pakietu, pakietu sterowników, obrazu systemu operacyjnego, obraz rozruchowy lub pakiet uaktualnienia systemu operacyjnego będzie teraz wyświetlany identyfikator pakietu odwołuje się do obiektu. Gdy krok sekwencji zadań odwołuje się do aplikacji spowoduje wyświetlenie identyfikatora obiektu.
- **Windows 10 ADK śledzone przez wersję kompilacji**: Zestaw Windows 10 ADK teraz jest śledzony przez wersję kompilacji, aby zapewnić więcej dostępnych możliwości dostosowywania obrazów rozruchowych systemu Windows 10. Na przykład jeśli witryna korzysta z systemu Windows ADK dla systemu Windows 10, wersji 1607, tylko obrazy rozruchowe z wersją 10.0.14393 można dostosować w konsoli. Aby uzyskać więcej informacji dotyczących dostosowywania wersje środowiska WinPE, zobacz [dostosowywanie obrazów rozruchowych](/sccm/osd/get-started/customize-boot-images).
- **Nie można zmienić ścieżki źródłowej obrazu rozruchowego domyślne**: Domyślne obrazy rozruchowe są zarządzane przez program Configuration Manager i nie można zmienić ścieżki źródłowej obrazu rozruchowego domyślne, w konsoli programu Configuration Manager lub przy użyciu zestawu SDK programu Configuration Manager. Możesz skonfigurować ścieżkę źródła niestandardowego dla niestandardowych obrazów rozruchowych.

## <a name="host-software-updates-on-cloud-based-distribution-points"></a>Aktualizacje oprogramowania w punktach dystrybucji w chmurze
Począwszy od tej wersji zapoznawczej, można użyć punktu dystrybucji w chmurze do obsługi pakietu aktualizacji oprogramowania. Jednak ponieważ można skonfigurować klientów, aby pobrać aktualizacje oprogramowania bezpośrednio z witryny Microsoft Update, należy rozważyć może pociągnąć za sobą dodatkowe koszty, które wdrażania oprogramowania, aktualizacji pakietu do punktu dystrybucji w chmurze.

Aby uzyskać informacje o korzystaniu z punktów dystrybucji w chmurze, zobacz [użycia punktu dystrybucji w chmurze](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point) w zawartości dla bieżącej gałęzi programu Configuration Manager.

## <a name="validate-device-health-attestation-data-via-management-points"></a>Sprawdzanie poprawności danych zaświadczania o kondycji urządzenia za pośrednictwem punktów zarządzania

Począwszy od tej wersji zapoznawczej, można skonfigurować punkty zarządzania, aby zweryfikować zaświadczania o kondycji raportowania danych dla chmury lub lokalnej usługi zaświadczania o kondycji. Nowy **zaawansowane opcje** karcie **właściwości składnika punktu zarządzania** okno dialogowe umożliwia **Dodaj**, **Edytuj**, lub **Usuń** **lokalny adres URL usługi zaświadczania o kondycji urządzenia**. Można również określić **niestandardowych ustawień urządzenia** dla agenta klienta do **Użyj lokalnej usługi zaświadczania o kondycji**.  Ustawienie **tak** dla tego ustawienia spowoduje włączenie raportowania do lokalnego punktu zarządzania zamiast usług chmurowych.

### <a name="try-it-out"></a>Podczas próby

- **Włączanie zaświadczania o kondycji urządzenia lokalnego punktu zarządzania**<br>  W konsoli programu Configuration Manager, przejdź do punktu zarządzania i Otwórz **właściwości składnika punktu zarządzania** , a następnie kliknij przycisk **zaawansowane opcje** kartę. Kliknij przycisk **Dodaj** i określić adres URL lokalnej (na przykład https://10.10.10.10) dla **URL usługi zaświadczania o kondycji urządzenia lokalnymi**.
- **Włącz lokalnymi zarządzania punktu zaświadczania o kondycji raportowania dla agenta klienta**<br>W konsoli programu Configuration Manager wybierz **administracji** > **ustawień klienta** i kliknij dwukrotnie lub utworzyć nowy **niestandardowych ustawień urządzenia**. Wybierz **Agent komputera** i ustaw **Użyj lokalnej usługi zaświadczania o kondycji** do **tak**. Jeśli **Włącz komunikację z usługą zaświadczania o kondycji urządzenia** ustawiono **tak** i **wykorzystanie lokalnych zaświadczania o kondycji** ma ustawioną wartość **nr**, punkt zarządzania użyje usługę zaświadczania o kondycji urządzenia oparte na chmurze.

## <a name="use-the-oms-connector-for-microsoft-azure-government-cloud"></a>Korzystania z łącznika OMS chmury Microsoft Azure dla instytucji rządowych
Z tej wersji technical preview można teraz używać łącznika programu Microsoft Operations Management Suite (OMS) do nawiązania połączenia obszar roboczy OMS, który znajduje się w chmurze Microsoft Azure dla instytucji rządowych.  

Aby to zrobić, zmodyfikuj plik konfiguracji do punktu w chmurze dla instytucji rządowych, a następnie zainstaluj łącznik OMS.

### <a name="set-up-an-oms-connector-to-microsoft-azure-government-cloud"></a>Skonfiguruj łącznik OMS do chmury Microsoft Azure dla instytucji rządowych
1.  Na każdym komputerze konsoli programu Configuration Manager zainstalowane należy edytować następujący plik konfiguracji do punktu w chmurze dla instytucji rządowych:  ***&lt;Ścieżka instalacji CM > \AdminConsole\bin\Microsoft.configurationManagmenet.exe.config***

  **Zmiany:**

    Zmień wartość atrybutu Nazwa ustawienia *FairFaxArmResourceID* powinna być równa "https://management.usgovcloudapi.net/"

   - **Oryginalne:** &lt;ustawienie name = "FairFaxArmResourceId" serializeAs = "String" >   
      &lt;wartość > &lt; /value >   
      &lt;/ Ustawienia >

   - **Edycji:**     
      &lt;Nazwa ustawienia = "FairFaxArmResourceId" serializeAs = "String" > &lt;wartość > https://management.usgovcloudapi.net/ &lt; /value >  
      &lt;/ Ustawienia >

  Zmień wartość atrybutu Nazwa ustawienia *FairFaxAuthorityResource* powinna być równa "https://login.microsoftonline.com/"

  - **Oryginalne:** &lt;ustawienie name = "FairFaxAuthorityResource" serializeAs = "String" >   
    &lt;wartość > &lt; /value >

    - **Edytowane:** &lt;ustawienie name = "FairFaxAuthorityResource" serializeAs = "String" >   
    &lt;wartość > https://login.microsoftonline.com/ &lt; /value >

2.  Po zapisaniu pliku z dwie zmiany ponownie uruchomić konsolę programu Configuration Manager na tym samym komputerze, a następnie użyj konsoli, aby zainstalować łącznik OMS. Aby zainstalować łącznik, skorzystaj z informacji w [synchronizowanie danych z programu Configuration Manager do programu Microsoft Operations Management Suite](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite)i wybierz **obszar roboczy usługi Operations Management Suite** znajdujący się w chmurze Microsoft Azure dla instytucji rządowych.

3.  Po zainstalowaniu łącznika OMS połączenia do chmury dla instytucji rządowych jest dostępna, gdy używasz dowolnego konsoli, która jest połączona z lokacją.

## <a name="android-and-ios-versions-are-no-longer-targetable-in-creation-wizards-for-hybrid-mdm"></a>Wersje systemów android i iOS nie są już targetable w kreatorach tworzenia dla hybrydowego zarządzania urządzeniami Przenośnymi

Począwszy od tej wersji technical preview hybrydowego zarządzania urządzeniami przenośnymi (MDM), nie trzeba docelowych określonych wersji systemu Android i iOS, podczas tworzenia nowych zasad i profilów dla urządzeń zarządzanych przez usługę Intune. Zamiast tego należy wybrać jedną z następujących typów urządzeń:

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
