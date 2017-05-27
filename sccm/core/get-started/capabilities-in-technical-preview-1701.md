---
title: "Możliwości w Technical Preview 1701 programu Configuration Manager"
description: "Informacje na temat funkcji dostępnych w Technical Preview programu System Center Configuration Manager, wersja 1701."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 18598eaa-1131-44ff-8f8b-6093e87ac7a1
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: b330c97a0853d1673f1cf7e0691891b72407fa51
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1701-for-system-center-configuration-manager"></a>Możliwości w Technical Preview 1701 System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (Technical Preview)*



Ten artykuł wprowadza do funkcji, które są dostępne w Technical Preview programu System Center Configuration Manager, wersja 1701. Można zainstalować tę wersję, aby zaktualizować i dodawać nowe funkcje do lokacji programu Configuration Manager technical preview. Przed zainstalowaniem tej wersji technical preview, przejrzyj temat wprowadzające [Technical Preview dla programu System Center Configuration Manager](../../core/get-started/technical-preview.md), aby zapoznać się z ogólnym wymagania i ograniczenia dotyczące używania technical preview, jak zaktualizować między wersjami i jak Wyraź swoją opinię dotyczącą funkcji w technical preview.    


**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  

## <a name="boundary-groups-improvements-for-software-update-points"></a>Punkty aktualizacji ulepszenia grup granic dla oprogramowania
Począwszy od tej wersji zapoznawczej można teraz używać grup granic do skojarzenia z klientów z punktów aktualizacji oprogramowania. Jest to część kontynuowanie pracy, aby rozwinąć zmian dotyczących grup granic do zarządzania dodatkowe role systemu lokacji.  Zmiany grupy granic najpierw została wprowadzona w bieżącej gałęzi w wersji 1610 i Technical Preview 1609.  

Za pomocą tej wersji zapoznawczej można użyć nowych granic zachowanie grupy do zarządzania punkty aktualizacji oprogramowania, które klient może używać, podobnie jak zarządzać punkt dystrybucji, które klient może używać:  

- Konfigurowanie grup granic, aby skojarzyć jedną lub więcej serwerów, które obsługują oprogramowania punktu aktualizacji.
- Klienci, którzy szukają nowy punkt aktualizacji oprogramowania spróbuje użyć taki, który jest skojarzony z ich bieżącej grupy granic.
- Gdy klient nie może nawiązać połączenia ich bieżące oprogramowanie punktu aktualizacji i nie może znaleźć jednego z ich bieżącej grupy granic, klient używa rezerwowej zachowanie rozszerzenia dostępnej puli punktów aktualizacji oprogramowania, których można użyć.    

Aby uzyskać więcej informacji dotyczących grup granic, zobacz [grup granic](/sccm/core/servers/deploy/configure/boundary-groups) w zawartości dla bieżącej gałęzi.

Jednak za pomocą tej wersji zapoznawczej grup granic dla punktów aktualizacji oprogramowania są tylko częściowo zaimplementowany. Możesz dodać punkty aktualizacji oprogramowania i konfigurowania grup granic sąsiada, które zawierają punkty aktualizacji oprogramowania, ale rezerwowy czasu dla punktów aktualizacji oprogramowania nie jest jeszcze obsługiwany i klientów będzie czekać na dwie godziny przed uruchomieniem rezerwowego.

Poniżej opisano zachowanie dla punktów aktualizacji oprogramowania z tego technical preview:  

-    **Nowi klienci używają grup granic punkty aktualizacji oprogramowania, wybrać** klienta, czy zainstalować po zakończeniu instalacji wersji 1701 wybiera punkt od tych skojarzone z grupą granic klienta aktualizacji oprogramowania.

  Spowoduje to zastąpienie poprzednie zachowanie, gdy klienci wybierają punkt aktualizacji oprogramowania losowo z listy tych, które współużytkują lasu klientów.   

-    **Wcześniej klientów zainstalowanych nadal używać ich bieżącego punktu aktualizacji oprogramowania do czasu powrotu znaleźć nową.**
Klientów, które zostały wcześniej zainstalowane, a który jeszcze punkt aktualizacji oprogramowania będzie używać tego punktu aktualizacji oprogramowania do czasu powrotu. Obejmuje to punkty aktualizacji oprogramowania, które nie są skojarzone z grupą granic bieżącego klienta. Ich nie od razu należy znaleźć i korzystać z ich bieżącej grupie granic punktu aktualizacji oprogramowania.

  Klient, który ma już punkt aktualizacji oprogramowania rozpocznie korzystanie to nowe zachowanie grupy granic, tylko wtedy, gdy klient nie może dotrzeć do jego bieżący punkt aktualizacji oprogramowania i uruchamia rezerwowego.
To opóźnienie w przełączanie nowe zachowanie jest celowe. Jest to spowodowane zmianą punktu aktualizacji oprogramowania może spowodować duże wykorzystanie przepustowości sieci jako klient synchronizuje dane z punktem aktualizacji oprogramowania. Opóźnienie w okresie przejściowym może pomóc uniknąć nasycanie sieci wszystkich klientów przełączyć się do nowego oprogramowania zaktualizować punktów w tym samym czasie.

-    **Konfiguracje rezerwowy czasu:** Konfiguracje dla rozpoczęcia powrotu do wyszukiwania nowego punktu aktualizacji oprogramowania klienci nie są obsługiwane w tym technical preview. Obejmuje to konfiguracje **powrotu czasu (w minutach)** i **nigdy rezerwowy**, że można skonfigurować dla różnych granic relacje grupy.

  Zamiast tego klienci zachowują ich bieżące zachowanie, gdy klient próbuje połączyć się jego bieżący punkt aktualizacji oprogramowania na dwie godziny przed rozpoczęciem rezerwowego, aby znaleźć nowy punkt aktualizacji oprogramowania, których można użyć.

  Używając klienta rezerwowych, użyje konfiguracji grupy granic dla powrotu utworzyć pulę punkty aktualizacji oprogramowania dostępne. Ta pula zawiera wszystkie punkty aktualizacji oprogramowania z klientów *bieżącą grupę granic*, *sąsiada grup granic*, a klientami *grupy granic domyślnej witryny*.

- **Konfigurowanie domyślnej grupy granic lokacji:**  
 Należy rozważyć dodanie punktu aktualizacji oprogramowania w celu *granicy grupy, domyślne lokacji w-&lt;kod_lokacji >*. Dzięki temu klienci, którzy nie są członków innej grupy granic można powrotu do znalezienia oprogramowania punktu aktualizacji.


Aby zarządzać punkty aktualizacji oprogramowania do grup granic, użyj [procedur z dokumentacji bieżącej gałęzi](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#procedures-for-boundary-groups), należy jednak pamiętać, że czasy rezerwowy może skonfigurować nie są jeszcze używane dla punktów aktualizacji oprogramowania.


## <a name="hardware-inventory-collects-uefi-information"></a>Spis sprzętu zbiera informacje z interfejsem UEFI
Nowe klasy spisu sprzętu (**SMS_Firmware**) i właściwości (**UEFI**) są dostępne w celu określenia, czy komputer jest uruchamiany w trybie UEFI. Kiedy komputer jest uruchamiany w trybie UEFI, **UEFI** właściwość jest ustawiona na **TRUE**. To jest domyślnie włączona w programie spisu sprzętu. Aby uzyskać więcej informacji na temat zapasów sprzętu, zobacz [Konfigurowanie spisu sprzętu](/sccm/core/clients/manage/inventory/configure-hardware-inventory).

## <a name="improvements-to-operating-system-deployment"></a>Ulepszenia dotyczące wdrażania systemu operacyjnego
Wprowadzono następujące ulepszenia wprowadzone do wdrożenia systemu operacyjnego, z których wiele zostały wynik opinii głosu użytkownika.
- [**Obsługa więcej aplikacji dla kroku sekwencji zadań instalacji aplikacji**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/17062207-task-sequence-allow-more-than-9-applications-in-t): Udało nam się zwiększyć maksymalną liczbę aplikacji, które można zainstalować do 99 w **instalowanie aplikacji** sekwencji zadań. Poprzednie maksymalną liczbę była 9 aplikacji.
- [**Wybierz wiele aplikacji w kroku sekwencji zadań zainstaluj aplikację**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/15459978-when-adding-items-to-an-install-application-step): Po dodaniu krok aplikacji do instalowania aplikacji sekwencji zadań w edytorze sekwencji zadań, można teraz wybrać wiele aplikacji z **wybierz aplikację do zainstalowania** okienka.
- [**Wygaśnie nośnika autonomicznego**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/14448564-provide-a-method-for-expiring-standalone-media): Po utworzeniu nośnika autonomicznego istnieją nowe opcje Ustaw opcjonalne daty rozpoczęcia i wygaśnięcia na nośniku. Te ustawienia są domyślnie wyłączone. Daty są porównywane z czasem systemowym na komputerze przed uruchomieniem nośników samodzielnych. Gdy czas systemowy jest wcześniejsza niż godzina rozpoczęcia lub późniejsza niż godzina wygaśnięcia, nośnika samodzielnego nie jest uruchomiona. Te opcje są również dostępne przy użyciu polecenia cmdlet New-CMStandaloneMedia środowiska PowerShell.
- [**Obsługę dodatkowej zawartości w nośniku samodzielnym**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/8341257-support-installation-of-packages-apps-via-dynamic): Dodatkowa zawartość jest teraz obsługiwana w nośniku samodzielnym. Można wybrać dodatkowe pakiety, pakiety sterowników i aplikacjom przemieszczony na nośniku oraz zawartość, do którego odwołuje się sekwencja zadań. Wcześniej tylko zawartość, do którego odwołuje się sekwencja zadań została przygotowywane na nośnikach autonomicznych.
- [**Można skonfigurować limit czasu dla kroku sekwencji zadań automatycznie Zastosuj sterowniki**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/17153660-auto-apply-driver-timeout): Nowe zmienne sekwencji zadań są teraz dostępne skonfigurować wartość limitu czasu w kroku sekwencji zadań automatycznie Zastosuj sterowniki podczas tworzenia żądania HTTP katalogu. Dostępne są następujące zmienne i domyślne wartości (w sekundach):
   - Domyślnie SMSTSDriverRequestResolveTimeOut: 60
   - Domyślnie SMSTSDriverRequestConnectTimeOut: 60
   - Domyślnie SMSTSDriverRequestSendTimeOut: 60
   - Domyślnie SMSTSDriverRequestReceiveTimeOut: 480
- [**Identyfikator pakietu jest teraz wyświetlany w krokach sekwencji zadań**](https://configurationmanager.uservoice.com/forums/300492-ideas/suggestions/16167430-display-packageid-when-viewing-a-task-sequence-ste): Dowolny etap sekwencji zadań odwołuje się do pakietu, pakietu sterowników, obrazu systemu operacyjnego, obraz rozruchowy lub pakiet uaktualnienia systemu operacyjnego wyświetli identyfikator pakietu odwołuje się do obiektu. Gdy krok sekwencji zadań odwołuje się do aplikacji zostanie wyświetlona identyfikator obiektu.
- **Windows 10 ADK śledzona przez wersję kompilacji**: Windows 10 ADK teraz są śledzone przez wersję kompilacji, aby zapewnić więcej możliwości w przypadku dostosowywania obrazów rozruchowych systemu Windows 10. Na przykład jeśli w witrynie Windows ADK dla systemu Windows 10, wersja 1607, jest używane tylko obrazy rozruchowe z wersją 10.0.14393 można dostosować w konsoli. Aby uzyskać szczegółowe informacje o dostosowywaniu wersji środowiska WinPE, zobacz [dostosowywanie obrazów rozruchowych](/sccm/osd/get-started/customize-boot-images).
- **Nie można zmienić ścieżki źródłowej obrazu rozruchowego domyślne**: Domyślne obrazy rozruchowe są zarządzane przez program Configuration Manager i nie zostaną zmienione ścieżki źródłowej obrazu rozruchowego domyślne, w konsoli programu Configuration Manager lub za pomocą zestawu SDK programu Configuration Manager. Możesz skonfigurować ścieżkę źródłową niestandardowe niestandardowe obrazy rozruchowe.

## <a name="host-software-updates-on-cloud-based-distribution-points"></a>Aktualizacje oprogramowania w punktach dystrybucji w chmurze
Począwszy od tej wersji wstępnej, można użyć punktu dystrybucji w chmurze do obsługi pakietu aktualizacji oprogramowania. Jednakże ponieważ można skonfigurować klientów, aby pobrać aktualizacje oprogramowania bezpośrednio z witryny Microsoft Update, należy rozważyć może pociągnąć za sobą dodatkowe koszty niezbędne do wdrożenia oprogramowania pakietu aktualizacji do punktu dystrybucji w chmurze.

Informacje o korzystaniu z punktów dystrybucji w chmurze, można znaleźć w temacie [przy użyciu punktu dystrybucji w chmurze](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point) w zawartości dla bieżącej gałęzi programu Configuration Manager.

## <a name="validate-device-health-attestation-data-via-management-points"></a>Sprawdzanie poprawności danych zaświadczania kondycji urządzenia przy użyciu punktów zarządzania

Począwszy od tej wersji wstępnej, można skonfigurować punkty zarządzania, aby zweryfikować zaświadczania kondycji raportowania danych usługi zaświadczania kondycji chmurze lub lokalnie. Nowy **opcje zaawansowane** karcie w **właściwości składnika punktu zarządzania** okno dialogowe pozwala **Add**, **edycji**, lub **Usuń** **lokalnego adresu URL usługi zaświadczania kondycji urządzenia**. Można również określić **niestandardowych ustawień urządzenia** dla agenta klienta do **użycia lokalnej usługi kondycji zaświadczania**.  Ustawienie **tak** dla tego ustawienia spowoduje włączenie raportowania do lokalnego punktu zarządzania zamiast usługa w chmurze.

### <a name="try-it-out"></a>Wypróbuj to

- **Włącz zaświadczania kondycji urządzeń lokalnych w punkcie zarządzania**<br>  W konsoli programu Configuration Manager, przejdź do punktu zarządzania i Otwórz **właściwości składnika punktu zarządzania** , a następnie kliknij przycisk **opcje zaawansowane** kartę. Kliknij przycisk **Dodaj** i podaj adres URL lokalnych (na przykład https://10.10.10.10) dla **lokalnego adresy URL usługi zaświadczania kondycji urządzenia**.
- **Włącz lokalnego zarządzania punktu kondycji zaświadczania raportowania dla agenta klienta**<br>W konsoli programu Configuration Manager wybierz **Administracja** > **ustawień klienta** i kliknij dwukrotnie ikonę lub utworzyć nowy **niestandardowych ustawień urządzenia**. Wybierz **Agent komputera** i ustaw **użycia lokalnej usługi kondycji zaświadczania** do **tak**. Jeśli **włączenia komunikacji z usługą zaświadczania kondycji urządzenia** jest ustawiona na **tak** i **użycia lokalnego zaświadczania kondycji** jest ustawiona na **nr**, punkt zarządzania będzie używać usługi zaświadczania kondycji chmurze urządzenia.

## <a name="use-the-oms-connector-for-microsoft-azure-government-cloud"></a>Użyj łącznika usługi OMS chmury Microsoft Azure Rząd
Z tego technical preview można teraz używać łącznika usługi Microsoft Operations Management Suite (OMS) się połączyć z obszarem roboczym usługi OMS znajdującego się w chmurze Microsoft Azure Rząd.  

W tym celu należy zmodyfikować plik konfiguracji do punktu w chmurze instytucji rządowych, a następnie zainstalować łącznik usługi OMS.

### <a name="set-up-an-oms-connector-to-microsoft-azure-government-cloud"></a>Skonfiguruj łącznik usługi OMS do chmury Microsoft Azure Rząd
1.  Na dowolnym komputerze z zainstalowaną konsolą programu Configuration Manager należy edytować następujący plik konfiguracji do punktu w chmurze rząd:  ***&lt;Ścieżka instalacji CM > \AdminConsole\bin\Microsoft.configurationManagmenet.exe.config***

  **Zmiany:**

    Zmień wartość atrybutu Nazwa ustawienia *FairFaxArmResourceID* powinna być równa "https://management.usgovcloudapi.net/"

   - **Oryginalne:** 
      &lt;Nazwa ustawienia = "FairFaxArmResourceId" serializeAs = "String" >   
      &lt;wartość > &lt; /value >   
      &lt;/ Ustawienia >

   - **Edycji:**     
      &lt;Nazwa ustawienia = "FairFaxArmResourceId" serializeAs = "String" > &lt;wartość > https://management.usgovcloudapi.net/ &lt; /value >  
      &lt;/ Ustawienia >

  Zmień wartość atrybutu Nazwa ustawienia *FairFaxAuthorityResource* powinna być równa "https://login.microsoftonline.com/"

  - **Oryginalne:** &lt;Nazwa ustawienia = "FairFaxAuthorityResource" serializeAs = "String" >   
    &lt;wartość > &lt; /value >

    - **Edytować:** &lt;ustawienie name = "FairFaxAuthorityResource" serializeAs = "String" >   
    &lt;wartość > https://login.microsoftonline.com/ &lt; /value >

2.    Po zapisaniu pliku z dwie zmiany, ponownie uruchom konsolę programu Configuration Manager na tym samym komputerze, a następnie użyj konsoli instalacji łącznika usługi OMS. Aby zainstalować łącznik, informacje zawarte w [synchronizowanie danych z programu Configuration Manager do pakietu zarządzania Microsoft Operations](/sccm/core/clients/manage/sync-data-microsoft-operations-management-suite)i wybierz **obszaru roboczego pakiet zarządzania Operations** znajdujący się w chmurze Microsoft Azure Rząd.

3.    Po zainstalowaniu łącznika usługi OMS połączenia w chmurze rząd jest dostępna, korzystając z każdej konsoli, który połączy się z lokacją.

## <a name="android-and-ios-versions-are-no-longer-targetable-in-creation-wizards-for-hybrid-mdm"></a>Android i iOS wersje nie są już targetable w kreatorze tworzenia hybrydowe MDM

Począwszy od tej technical preview dla hybrydowego zarządzania urządzeniami przenośnymi (MDM), nie jest już konieczne docelowych określonych wersji Android i iOS przy tworzeniu nowych zasad i profile dla urządzeń zarządzanych przez usługę Intune. Zamiast tego można wybrać jedną z następujących typów urządzeń:

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

