---
title: "Możliwości w Technical Preview 1609 programu Configuration Manager"
description: "Informacje na temat funkcji dostępnych w Technical Preview programu System Center Configuration Manager, wersja 1609."
ms.custom: na
ms.date: 01/23/2017
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.topic: article
ms.assetid: e2a59116-b2e5-4dd2-90eb-0b8a5eb50b56
caps.latest.revision: 2
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5d08d1f9ccd995d544c3c21c4af52ede73343077
ms.openlocfilehash: 89a41c8a3137d0e54011ddf9a1d9b4894ecb7df8
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1609-for-system-center-configuration-manager"></a>Możliwości w Technical Preview 1609 System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (Technical Preview)*



Ten artykuł wprowadza do funkcji, które są dostępne w Technical Preview programu System Center Configuration Manager, wersja 1609. Można zainstalować tę wersję, aby zaktualizować i dodawać nowe funkcje do lokacji programu Configuration Manager technical preview.      Przed zainstalowaniem tej wersji technical preview, przejrzyj temat wprowadzające [Technical Preview dla programu System Center Configuration Manager](../../core/get-started/technical-preview.md), aby zapoznać się z ogólnym wymagania i ograniczenia dotyczące używania technical preview, jak zaktualizować między wersjami i jak Wyraź swoją opinię dotyczącą funkcji w technical preview.    

**Znane problemy w tym Technical Preview:**  
*  Po uaktualnieniu do programu Configuration Manager 1609 Technical Preview dowolnej wersji uaktualnienia zostały wdrożone zasady zostaną usunięte. Aby nadal korzystać z tych zasad, należy ponownie utworzyć i wdrożyć je.


**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  

## <a name="improvements-to-endpoint-protection"></a>Ulepszenia Endpoint Protection
Poprawy do ustawień zasad ochrony przed złośliwym oprogramowaniem Endpoint Protection — można teraz określić poziom jaką usługi Endpoint Protection chmury ochrony zablokuje podejrzanych plików. Nowe ustawienie umożliwia administratorom określenie "ryzykowne" komputery oparte na wysoki ilości złośliwego oprogramowania, które napotkają.

## <a name="increased-number-of-enrolled-devices"></a>Zwiększenie liczby zarejestrowanych urządzeń
Administratorzy mogą teraz włączyć użytkownikom na rejestrację maksymalnie 15 urządzeń w hybrydowe zarządzanie urządzeniami przenośnymi za pomocą usługi Intune. Limit został wcześniej 5 urządzeń dla poszczególnych użytkowników.

## <a name="additional-apple-dep-settings"></a>Dodatkowe ustawienia DEP firmy Apple

Administratorzy mogą teraz skonfigurować następujące ustawienia programu rejestracji urządzeń firmy Apple (DEP) w profilu DEP dla systemów iOS i Mac urządzenia:
- **Touch ID**
- **Powiększenie**
- **Siri**

Jeśli włączona, firmy Apple Asystenta monituje o tej usługi podczas aktywacji urządzenia.

## <a name="integration-with-upgrade-analytics"></a>Integracja z analizy uaktualnienia

Analiza uaktualnienia umożliwia oceny i analizowanie gotowości urządzenia i zgodności z systemem Windows 10, aby umożliwić łatwiejsze i sprawniej uaktualnień. Dzięki integracji z programami Analytics uaktualniania z programu Configuration Manager można uzyskać dostęp do danych zgodności z uaktualnieniem w konsoli administracyjnej programu Configuration Manager i następnie z listy urządzeń docelowych urządzeń do uaktualnienia lub korygowania.

Więcej informacji dotyczących uaktualniania Analytics w [wprowadzenie uaktualnienia Analytics](https://technet.microsoft.com/itpro/windows/deploy/upgrade-analytics-get-started).

## <a name="native-connection-types-for-windows-10-vpn-hybrid-profiles"></a>Profile VPN hybrydowe typy połączeń macierzystego for Windows 10

Korzystając z programu Configuration Manager za pomocą usługi Intune, możesz teraz utworzyć profile sieci VPN systemu Windows 10 Automatic firmy Microsoft, IKEv2, PPTP i L2TP dla typów połączenia w konsoli programu Configuration Manager bez użycia OMA-URI.

## <a name="enhancements-to-windows-store-for-business-integration-with-configuration-manager"></a>Rozszerzenia do Sklepu Windows biznesowych integracji z programem Configuration Manager

W tej wersji Zaktualizowaliśmy [Sklep Windows dla integracji Business](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business) z tych nowych funkcji:

**Aktualizacja:** W bieżącej wersji technical preview natychmiastową synchronizację funkcja nie działa.

- Wcześniej można wdrożyć tylko bezpłatnej aplikacji ze Sklepu Windows dla firm. Program Configuration Manager teraz ponadto obsługuje wdrażanie płatności online licencjonowane aplikacje (tylko w przypadku zarejestrowanych w usłudze Intune urządzeń).
- Teraz można zainicjować natychmiastową synchronizację między Sklepu Windows dla firm i Configuration Manager.
- Można również zmodyfikować klucz tajny klienta został pobrany z usługi Azure Active Directory

### <a name="try-it-out"></a>Wypróbuj to!

#### <a name="purchase-and-sync-a-paid-online-licensed-app"></a>Zakup i synchronizacji płatnego online licencjonowane aplikacji

1. Zakupów online płatną licencjonowanego aplikacji ze Sklepu Windows dla firm.
2. W **Administracja** obszaru roboczego w konsoli programu Configuration Manager, kliknij przycisk **usług w chmurze** > **aktualizacji i obsługi** > **Sklepu Windows dla firm**.
3. Na **Home** w karcie **synchronizacji** , kliknij przycisk **Synchronizuj teraz**.
4. Wkrótce po zakupiono aplikacja pojawi się w **informacji o licencji dla aplikacji do sklepu** węzła **zarządzania aplikacjami** obszaru roboczego.

#### <a name="create-and-deploy-a-configuration-manager-application-from-the-synchronized-app-data"></a>Tworzenie i wdrażanie aplikacji programu Configuration Manager z danych zsynchronizowanych aplikacji

Procedura tworzenia i wdrażania aplikacji programu Configuration Manager z płatnych sklepu jest taki sam, jak w przypadku tworzenia aplikacji z bezpłatnej aplikacji. Zobacz sekcję **tworzenie i wdrażanie aplikacji programu Configuration Manager w Sklepie Windows dla aplikacji biznesowych** w [zarządzania aplikacjami ze Sklepu Windows dla firm z System Center Configuration Manager](/sccm/apps/deploy-use/manage-apps-from-the-windows-store-for-business).


#### <a name="modify-the-client-secret-key-from-azure-active-directory"></a>Zmodyfikuj klucz tajny klienta z usługi Azure Active Directory

1. W **Administracja** obszaru roboczego w konsoli programu Configuration Manager, kliknij przycisk **usług w chmurze** > **aktualizacji i obsługi** > **Sklepu Windows dla firm**.
2. Wybierz Sklepu Windows dla konta firmowego, a następnie kliknij przycisk **właściwości**.
3. W **Sklep Windows dla właściwości konta firmy** okna dialogowego wprowadź nowy klucz w **klucz tajny klienta** , a następnie kliknij przycisk **Sprawdź**. Po zweryfikowaniu, kliknij przycisk **Zastosuj**, zamknij okno dialogowe.


## <a name="new-compliance-settings-for-configuration-items"></a>Nowe ustawienia zgodności dla elementów konfiguracji

Dodaliśmy wiele nowych ustawień, którego można użyć w swoich elementów konfiguracji dla różnych platform urządzeń.
Są to ustawienia, które wcześniej były dostępne w programie Microsoft Intune w konfiguracji autonomicznej i są teraz dostępne przy użyciu usługi Intune z programem Configuration Manager.
Jeśli potrzebujesz pomocy przy użyciu tych ustawień, otwórz [zarządzać ustawieniami i funkcjami urządzeń z zasadami firmy Microsoft Intune](https://docs.microsoft.com/en-us/intune/deploy-use/manage-settings-and-features-on-your-devices-with-microsoft-intune-policies) a następnie wybierz podrzędny ustawień mają platformy.


### <a name="new-settings-for-android-devices"></a>Nowe ustawienia dla urządzeń z systemem Android

#### <a name="password-settings"></a>Ustawienia hasła

- **Pamiętaj historię haseł**
- **Zezwalaj na podstawie linii papilarnych odblokowania**

#### <a name="security-settings"></a>Ustawienia zabezpieczeń

- **Wymagaj szyfrowania kart pamięci**
- **Zezwalaj na przechwytywanie ekranu**
- **Zezwalaj na przesłanie danych diagnostycznych**

#### <a name="browser-settings"></a>Ustawienia przeglądarki

- **Zezwalaj na używanie przeglądarki sieci web**
- **Zezwalaj na automatyczne uzupełnianie**
- **Zezwalaj na blokowanie wyskakujących okienek**
- **Zezwalaj na pliki cookie**
- **Zezwalaj na wykonywanie aktywnych skryptów**

#### <a name="app-settings"></a>Ustawienia aplikacji

- **Zezwalaj na sklep Google Play**

#### <a name="device-capability-settings"></a>Ustawienia możliwości urządzenia

- **Zezwalaj na używanie magazynu wymiennego**
- **Zezwalaj na tethering Wi-Fi**
- **Zezwalaj na używanie funkcji geolokalizacji**
- **Zezwalaj na komunikację NFC**
- **Zezwalaj na połączenia Bluetooth**
- **Zezwalaj na Roaming połączeń głosowych**
- **Zezwalaj na roaming danych**
- **Zezwalaj na obsługę wiadomości SMS/MMS**
- **Zezwalaj na Asystenta głosowego**
- **Zezwalaj na wybieranie głosowe**
- **Zezwalaj na kopiowanie i wklejanie**


### <a name="new-settings-for-ios-devices"></a>Nowe ustawienia dla urządzeń z systemem iOS

#### <a name="password-settings"></a>Ustawienia hasła

- **Złożone wymagana liczba znaków w haśle**
- **Zezwalaj na proste hasła**
- **Liczba minut braku aktywności, zanim będzie wymagane hasło**
- **Pamiętaj historię haseł**

### <a name="new-settings-for-mac-os-x-devices"></a>Nowe ustawienia dla urządzeń z systemem Mac OS X

#### <a name="password-settings"></a>Ustawienia hasła

- **Złożone wymagana liczba znaków w haśle**
- **Zezwalaj na proste hasła**
- **Pamiętaj historię haseł**
- **Liczba minut braku aktywności przed włączeniem wygaszacza**

### <a name="new-settings-for-windows-10-desktop-and-mobile-devices"></a>Nowe ustawienia dla urządzeń z systemem Windows 10 Desktop oraz Mobile

#### <a name="password-settings"></a>Ustawienia hasła

- **Minimalna liczba zestawów znaków**
- **Pamiętaj historię haseł**
- **Wymagaj hasła, gdy urządzenie powraca ze stanu bezczynności**

#### <a name="security-settings"></a>Ustawienia zabezpieczeń

- **Wymagaj szyfrowania na urządzeniu przenośnym**
- **Zezwalaj na ręczne unenrollment**

#### <a name="device-capability-settings"></a>Ustawienia możliwości urządzenia

- **Zezwalaj na sieć VPN przez sieć komórkową**
- **Zezwalaj na roaming sieci VPN przez sieć komórkową**
- **Zezwalaj na resetowanie telefonu**
- **Zezwalaj na połączenie USB**
- **Zezwalaj na Cortana**
- **Zezwalaj na powiadomienia Centrum akcji**

### <a name="new-settings-for-windows-10-team-devices"></a>Nowe ustawienia dla urządzeń z systemem Windows 10 Team

#### <a name="device-settings"></a>Ustawienia urządzeń

- **Włącz usługi Azure Operational Insights**
- **Włącz Miracast projekcji bezprzewodowej**
- **Wybierz spotkania informacje wyświetlane na ekranie powitalnym**
- **Adres URL obrazu tła Lockscreen**


### <a name="new-settings-for-windows-81-devices"></a>Nowe ustawienia dla urządzeń Windows 8.1

#### <a name="applicability-settings"></a>Stosowanie ustawień

- **Zastosuj wszystkie konfiguracje dla systemu Windows 10**

#### <a name="password-settings"></a>Ustawienia hasła

- **Wymagany typ hasła**
- **Minimalna liczba zestawów znaków**
- **Minimalna długość hasła**
- **Liczba dopuszczalnych nieudanych logowań przed wyczyszczeniem danych z urządzenia**
- **Liczba minut braku aktywności przed wyłączeniem ekranu**
- **Wygaśnięcie hasła (dni)**
- **Pamiętaj historię haseł**
- **Zapobiegaj ponownemu używaniu poprzednich haseł**
- **Zezwalaj na hasło obrazkowe i numer PIN**

#### <a name="browser-settings"></a>Ustawienia przeglądarki

- **Zezwalaj na automatyczne wykrywanie sieci intranet**


### <a name="new-settings-for-windows-phone-81-devices"></a>Nowe ustawienia dla urządzeń Windows Phone 8.1

#### <a name="applicability-settings"></a>Stosowanie ustawień

- **Zastosuj wszystkie konfiguracje dla systemu Windows 10**

#### <a name="password-settings"></a>Ustawienia hasła

- **Minimalna liczba zestawów znaków**
- **Zezwalaj na proste hasła**
- **Pamiętaj historię haseł**

#### <a name="device-capability-settings"></a>Ustawienia możliwości urządzenia

- **Zezwalaj na automatyczne łączenie z bezpłatnymi punktami HotSpot Wi-Fi**


## <a name="improvements-for-boundary-groups"></a>Udoskonalenia w zakresie grup granic
Ta wersja zapoznawcza wprowadza ważne zmiany do grupy granic oraz ich współdziałaniu z punktami dystrybucji. Te zmiany uprości projektowania infrastruktury zawartości podczas co daje większą kontrolę nad jak i kiedy klienci powrotu do wyszukiwania dystrybucji dodatkowych punktów jako lokalizacji źródła zawartości. Obejmuje to zarówno lokalnie, jak i punkty dystrybucji w chmurze.

Te ulepszenia zastąpić pojęcia i zachowania może być znasz już dziś (np. Konfigurowanie punktów dystrybucji za dużą lub małą) i zastępuje je nowy model, który powinien być łatwiejsze do instalacji i konserwacji. Zmiany te są również przygotowawczych przyszłe zmiany zwiększające inne role systemu lokacji, którą można skojarzyć do grup granic.  

Podczas uaktualniania do 1609 uaktualnienia konwertuje bieżącej konfiguracji grupy granic do nowego modelu, aby te zmiany nie przeszkadzać konfiguracje dystrybucji zawartości (zobacz [aktualizowanie istniejących grup granic do nowego modelu](/sccm/core/get-started/capabilities-in-technical-preview-1609#bkmk_update)).

W poniższych sekcjach opisano zmiany wprowadzone w programie Podgląd, jak działa nowy model i czego można oczekiwać po uaktualnieniu lokacji, która już ma skonfigurowane grupy granic.



### <a name="changes-in-ui-and-behavior-for-boundary-groups-and-content-locations"></a>Zmiany w interfejsie użytkownika i zachowanie dla grupy granic i lokalizacji zawartości
Dostępne są następujące zmiany klucza do grupy granic i znajdowania zawartości klientom. Wiele z tych zmian i pojęcia współpracują ze sobą.
-    **Konfiguracje szybko lub wolno zostaną usunięte:** Można już konfigurować poszczególne punkty dystrybucji do szybkiego lub powolnego.  Zamiast tego każdy system lokacji skojarzone z grupą granic jest traktowany takie same. Z powodu tej zmiany **odwołania** karta właściwości grupy granic nie obsługuje już konfiguracji Fast lub niska.
-     **Nową grupę granic domyślne w każdej lokacji:**  Każda lokacja główna ma nowej grupy granic domyślna o nazwie ***granicy grupy, domyślne lokacji w-\<kod_lokacji >***.  Gdy klient nie jest w lokalizacji sieciowej, która jest przypisana do grupy granic, ten klient użyje systemy lokacji skojarzone z grupą domyślne z przypisanej mu lokacji. Zaplanuj użycie tej grupy granic zastępujący koncepcję rezerwowej lokalizacji zawartości.      
 -    **"Zezwalaj na lokalizacje rezerwowego źródła zawartości"** zostanie usunięty: Nie jest już jawnie skonfigurować punkt dystrybucji ma być używany dla powrotu i opcje tę są usuwane z interfejsu użytkownika.

    Ponadto wynik ustawienie **Zezwalaj klientom na użycie rezerwowej lokalizacji źródła zawartości** na wdrożenie zmienił się typ dla aplikacji. To ustawienie w typie wdrożenia teraz umożliwia klienta do używania domyślnej grupy granic lokacji jako lokalizację źródła zawartości.

 -    **Relacje grupy granic:** Każda grupa granic może zostać powiązany z co najmniej jedną grupę granic dodatkowe. Te łącza tworzą relacje, które są skonfigurowane na karcie właściwości nowej grupy granic o nazwie **relacje**:
     -    Każdą grupą granic, klient jest bezpośrednio z którym skojarzony jest nazywany **bieżącej** grupy granic.  
    -     Każda grupa granic klient może korzystać z powodu skojarzenia między ten klient *bieżącej* nosi nazwę grupy granic i innej grupy **sąsiada** grupy granic.
    -  Znajduje się ona na **relacji** kartę dodawanej grupy granic, które mogą być używane jako *sąsiada* grupy granic. Można również skonfigurować czas w minutach, które określa, kiedy klient, który nie może odnaleźć zawartości z punktu dystrybucji w *bieżącej* grupy rozpocznie się wyszukiwanie lokalizacji zawartości z tymi *sąsiada* grup granic.

        Podczas dodawania lub zmiany konfiguracji grupy granic, trzeba będzie opcja powrotu do tej grupy granic określone z bieżącej grupy, które są konfigurowane w bloku.

    Aby użyć nowej konfiguracji, definiowanie skojarzeń jawne (linki) z jednej grupy granic do innego i skonfiguruj wszystkie punkty dystrybucji w tej grupie skojarzone z tym samym czasie, w minutach. Podczas konfigurowania Określa, kiedy klient, który nie może odnaleźć Źródło zawartości z jej *bieżącej* grupy granic można rozpocząć wyszukiwanie źródła zawartości z tej grupy granic sąsiada.

    Oprócz grup granic, które jawnie skonfigurować każdą grupą granic ma dorozumianych łącze do domyślnej grupy granic lokacji. To łącze staje się aktywny po 120 minut po tym czasie domyślna grupa granic lokacji staje się grupie granic sąsiada, która umożliwia klientom korzystanie z punktów dystrybucji skojarzone z daną grupą granic jako lokalizacji źródła zawartości.

    To zachowanie zastępuje, co było wcześniej nazywane rezerwowych dla zawartości.  Można zastąpić to domyślne zachowanie 120 minut dokonując jawnie domyślna grupa granic lokacji do *bieżącej* grupy i ustawienie określony czas w minutach lub blokowanie powrotu całkowicie uniemożliwić korzystanie z niego.


-     **Klienci próbują uzyskać zawartości z poszczególnych punktów dystrybucji przez maksymalnie 2 minuty:** Gdy klient wyszukuje lokalizacji źródła zawartości, podejmie dostępu do poszczególnych punktów dystrybucji przez 2 minut przed podjęciem próby następnie innego punktu dystrybucji. Jest zmiany z poprzednich wersji, której klienci próbował łączyć się z punktem dystrybucji przez maksymalnie 2 godziny.

    - Pierwszy punkt dystrybucji, klient próbuje użyć losowo z puli dostępnych punktów dystrybucji na komputerze klienckim *bieżącej* grupy granic (lub grup).

    - Po upływie dwóch minut Jeśli klient ma nie można odnaleźć zawartości, go przełącza się do nowego punktu dystrybucji i próbuje pobrać zawartości z tego serwera. Ten proces jest powtarzany co dwie minuty, dopóki klient znajdzie zawartość lub osiągnie ostatniego serwera jej puli.

    - Jeśli klient nie może znaleźć lokalizację prawidłowego źródła zawartości z jego *bieżącej* puli przed okres powrotu do *sąsiada* osiągnięciu grupy granic, klient następnie dodaje punktów dystrybucji niż *sąsiada* grupę w celu jego bieżącej listy, a następnie będzie szukał rozwiniętej grupy lokalizacje źródłowe, która zawiera punkty dystrybucji z obu grup granic.

        > [!TIP]  
        > Po utworzeniu jawne łącze z bieżącej grupy granic do domyślnej grupy granic lokacji i zdefiniować rezerwowy godzinę, która jest mniejsza niż czas rezerwowy dla łącza do grupy granic sąsiada, klienci rozpocznie się wyszukiwanie lokalizacje źródłowe do domyślnej grupy granic lokacji przed tym grupy sąsiada.

    - Gdy klient nie może pobrać zawartości z ostatnich serwera w puli, rozpoczyna proces ponownie.


### <a name="how-the-new-model-works"></a>Jak działa nowy model
Podczas konfigurowania grup granic można skojarzyć granic (lokalizacje sieciowe) i role systemu lokacji, takich jak punkty dystrybucji do grupy granic. Pozwala to klientów na serwerach systemu lokacji, takich jak punkty dystrybucji, które znajdują się w pobliżu klientów w sieci.   
-    Tej samej granicy można przypisać do wielu grup granic
-    Serwery systemu lokacji, takich jak punkty dystrybucji można skojarzyć z wielu grup granic w celu udostępnienia większej liczbie lokalizacji sieciowych
-    Jeśli punkt dystrybucji nie jest skojarzony z grupą granic, klienci nie będą mogli używać tego punktu dystrybucji jako lokalizacji źródła zawartości.

Począwszy od tej technical preview, należy zdefiniować relacje grupy granic, aby skonfigurować zachowanie rezerwowej lokalizacji źródła zawartości. To nowe zachowanie jest skonfigurowany na nowym **relacje** na karcie właściwości grupy granic i zamienia Konfigurowanie systemów lokacji jako wolne lub szybkiego i konfigurowania grupy granic, aby zezwolić na rezerwową lokalizację źródła zawartości.

Na karcie relacje można dodać inne grupy granic do konfigurowania relacji do tych grup. Każda relacja jest jednokierunkowe łącze z **bieżącej** grupy granic do grupy granic można dodać, która jest wywoływana **sąsiada**. Dla każdego tworzonego łącza można skonfigurować punkty dystrybucji z rezerwowego czas w minutach. Ten czas jest używana do określenia po ile klientów w *bieżącej* grupy granic można rozpocząć korzystanie z punktów dystrybucji w *sąsiada* grupy granic, jeśli nie można odnaleźć lokalizacji prawidłowego źródła zawartości z ich bieżącej grupy granic.

Gdy klient nie może odnaleźć zawartości i rozpocznie się wyszukiwanie lokalizacji z grupy granic sąsiada, zwiększa puli dostępnych punktów dystrybucji dla tego klienta w kontrolowany sposób.  

-    Grupa granic może mieć więcej niż jedną relację. Dzięki temu można skonfigurować powrotu do różnych sąsiadów nastąpi po różnych okresach czasu.
-    Klienci będą tylko powrotu do grupy granic, która jest bezpośrednie sąsiada ich bieżącej grupy granic.
-    Gdy klient jest członkiem wielu grup granic, bieżącą grupę granic jest zdefiniowany jako sumę tego klienta grup granic.  Ten klient może następnie powrotu do sąsiada któregokolwiek z tych grup granic oryginalnej.

Oprócz łącza, które należy zdefiniować istnieje dorozumianych łącze, które jest tworzone automatycznie między grupami granic, tworzonych i domyślnej grupy granic są tworzone dla każdej lokacji. To łącze automatyczne:
-    Jest używana przez klientów, którzy są nie w granicach automatycznie skojarzony z żadną inną grupą granic w hierarchii używają domyślnej grupy granic z przypisanej lokacji do identyfikowania lokalizacji prawidłowego źródła zawartości.   
-     To domyślne opcji rezerwowej z bieżącej grupy granic do domyślnej grupy granic lokacji jest używana po 120 minut.

**Przykład użycia nowego modelu:**     
Utwórz trzy grupy granic, które nie mają granice lub serwerów systemu lokacji:
-    Grupa BG_A z punktami dystrybucji DP_A1 i DP_A2 skojarzonego z grupą
-    Grupa BG_B z punktami dystrybucji DP_B1 i DP_B2 skojarzonego z grupą
-    Grupa BG_C z punktami dystrybucji DP_C1 i DP_C2 skojarzonego z grupą

Dodaj lokalizacje sieci klientów tylko do grupy granic BG_A i można następnie skonfigurować relacji z tej grupy granic do innych dwóch grup granic:
-    Konfigurowanie punktów dystrybucji w pierwszym *sąsiada* grupy (BG_B) do użycia po 10 minutach. Ta grupa zawiera punkty dystrybucji DP_B1 i DP_B2. Oba są dobrze połączony z pierwszym lokalizacje granic grup.
-    Skonfiguruj drugi *sąsiada* grupy (BG_C) do użycia po upływie 20 minut. Ta grupa zawiera punkty dystrybucji DP_C1 i DP_C2. Oba są w sieci WAN z innych dwóch grup granic.
-    Również dodać punkt dystrybucji dodatkowe znajdujący się na serwerze lokacji do grupy granic lokacji domyślnej witryny. To jest najmniej polecana lokalizacji źródła zawartości, ale znajduje centralnie do grup granic.

    Przykład grupy granic i czasy rezerwowego:

     ![BG_Fallack](media/BG_Fallback.png)


W przypadku tej konfiguracji:
-    Klient rozpoczyna wyszukiwanie zawartości z punktów dystrybucji w jego *bieżącej* grupy granic (BG_A), wyszukiwanie dystrybucji każdego punktu dla dwóch minut przed przejściem do następnego punktu dystrybucji w grupie granic. Pula klientów z lokalizacji prawidłowego źródła zawartości zawiera DP_A1 i DP_A2.
-    Jeśli klient nie może odnaleźć zawartości z jego *bieżącej* grupy granic po przeszukaniu przez 10 minut, następnie dodaje punkty dystrybucji z grupy granic BG_B do wyszukiwania. Następnie nadal wyszukiwania zawartości z punktu dystrybucji w jego połączonych puli punktów dystrybucji, która zawiera te z BG_A i BG_B grup granic. Klient w dalszym ciągu skontaktować się z każdym punkcie dystrybucji dla dwóch minut przed przejściem do następnego punktu dystrybucji z puli. Pula klientów z lokalizacji prawidłowego źródła zawartości obejmuje DP_A1, DP_A2, DP_B1 i DP_B2.
-    Po 10 minutach dodatkowe (całkowita liczba 20 minut) Jeśli klient nadal ma nie można odnaleźć punktu dystrybucji z zawartością, rozszerza puli dostępnych punktów dystrybucji te od drugiego *sąsiada* grupie grupy granic BG_C. Klient jest teraz ma 6 punktów dystrybucji do wyszukiwania (DP_A1, DP_A2, DP_B2, DP_B2, DP_C1 i DP_C2) i kontynuuje wprowadzanie zmian do nowego punktu dystrybucji, co dwie minuty, aż do znalezienia zawartości.
-    Jeśli klient nie odnalazł zawartości po łącznie 120 minut, jego powraca do obejmują *domyślna grupa granic lokacji* w ramach jego ciągłego wyszukiwania. Teraz puli punktów dystrybucji zawiera wszystkie punkty dystrybucji z trzech skonfigurowanych grup granic i punktu końcowego dystrybucji znajdujących się na komputerze serwera lokacji.  Klient kontynuuje wyszukiwanie zawartości, zmiana punktów dystrybucji, co dwie minuty, aż do znalezienia zawartości.

Konfigurując grupy różnych sąsiada była dostępna w różnym czasie kontrolować po dodaniu konkretnych punktów dystrybucji jako lokalizacji źródła zawartości i gdy lub jeśli klient korzysta z powrotu do domyślnej grupy granic lokacji jako zabezpieczenie zawartości, które nie są dostępne z innej lokalizacji.


### <a name="bkmk_update"></a>Aktualizowanie istniejących grup granic do nowego modelu
Po zainstalowaniu wersji 1609 i zaktualizować witryny, automatycznie stają się następujące konfiguracje. Są one przeznaczone do upewnij się, że Twoje bieżące zachowanie rezerwowego, pozostaje dostępna, dopóki nie zostanie skonfigurowana nowej grupy granic i relacje.  
-    Punkty dystrybucji niechronionych w lokacji są dodawane do *granicy grupy, domyślne lokacji w-\<kod lokacji >* grupy granic tej lokacji.
-    Kopię składa się z każdej istniejącej grupy granic, która zawiera serwer lokacji, skonfigurowany z wolnego połączenia. Nazwa nowej grupy jest *** \<oryginalna nazwa grupy granic > - wolno — Tmp***:  
    -    Systemy lokacji z szybkim połączeniu są pozostawiane w oryginalnej grupie granic.
    -    Kopię systemów lokacji, które ma powolne połączenie są dodawane do skopiowania grupy granic. Oryginalny systemów lokacji, skonfigurowany jako wolne pozostają w oryginalnej grupie granic dla zgodności z poprzednimi wersjami, ale nie są używane z tej grupy granic.
    -     Ta kopia grupy granic nie ma granicach skojarzonych z nim. Jednakże tworzone jest połączenie rezerwowy między oryginalna grupa i nową kopię grupa granic zawiera rezerwowy czas, należy ustawić na zero.

 W poniższej tabeli przedstawiono nowe zachowanie rezerwowego można spodziewać się z kombinacji oryginalnego ustawienia wdrożenia i punktu dystrybucji konfiguracje:

"Nie uruchamiaj programu" w sieci o niskiej prędkości oryginalna konfiguracja wdrożenia  |Punkt dystrybucji oryginalna konfiguracja "Client Zezwalaj na użycie rezerwowej lokalizacji źródła zawartości"  |Nowe działanie rezerwowe  
---------|---------|---------
Wybrane     |  Wybrane    |  **Nie powrotu** -punktów dystrybucji należy używać tylko w bieżącej grupie granic       
Wybrane     |  Nie wybrano|  **Nie powrotu** -punktów dystrybucji należy używać tylko w bieżącej grupie granic       
Nie wybrano |  Nie wybrano|  **Powrót do sąsiada** — używać punktów dystrybucji w bieżącej grupie granic, a następnie dodaj punkty dystrybucji z grupy granic sąsiada. Chyba że jawne łącze do domyślnej grupy granic lokacji jest skonfigurowany, klienci nie będą powrotu do tej grupy.    
Nie wybrano | Wybrane        |   **Normalne powrotu** -używać punktów dystrybucji w bieżącej grupie granic, a następnie te z sąsiada i lokacji domyślne grupy granic

 Inne konfiguracje wdrożenia spowodować **normalnego powrotu**.  



## <a name="office-365-client-management-dashboard"></a>Pulpit nawigacyjny zarządzania klientami usługi Office 365  
Program Configuration Manager 1609 Technical Preview wprowadzono nowy pulpit nawigacyjny. Aby wyświetlić pulpit nawigacyjny, w konsoli programu Configuration Manager przejdź do **Biblioteka oprogramowania** > **Przegląd** > **Zarządzanie klientem usługi Office 365**.
>[!NOTE]
>W **What's New** obszaru roboczego w konsoli programu Configuration Manager, nowy pulpit nawigacyjny jest niepoprawna **Office 365 obsługi pulpitu nawigacyjnego**.

Na pulpicie nawigacyjnym wykresy dla następujących elementów:

- Liczba klientów usługi Office 365
- Wersje klienta usługi Office 365
- Języki klienta usługi Office 365
- Kanały klienta usługi Office 365     
Aby uzyskać więcej informacji, zobacz [kanały przegląd aktualizacji dla Office 365 ProPlus](https://technet.microsoft.com/library/mt455210.aspx).
- Reguły automatycznego wdrażania pakietu Office 365 klienta wybrana w zestawie produktów.

Na pulpicie nawigacyjnym, można wykonać następujące czynności:
- W górnej części pulpitu nawigacyjnego, należy użyć **kolekcji** ustawienie listy rozwijanej do filtrowania danych pulpitu nawigacyjnego przez elementy członkowskie określonej kolekcji.
- W prawej górnej części pulpitu nawigacyjnego kliknij polecenie **Office 365 Instalator** uruchomić Kreatora instalacji pakietu Office 365 klienta do wdrażania aplikacji Office 365 na klientach. Aby uzyskać szczegółowe informacje, zobacz [aplikacje wdrażania usługi Office 365 klientom](#deploy-office-365-apps-to-clients).
- Na środku po prawej stronie pulpitu nawigacyjnego, kliknij przycisk **utworzyć ADR** otworzyć kreatorze reguły wdrażania automatycznego, aby utworzyć nową regułę automatycznego wdrażania (ADR). Aby utworzyć ADR dla aplikacji usługi Office 365, wybierz **Office 365 klienta** po wybraniu produktu. Aby uzyskać więcej informacji, zobacz [automatyczne wdrażanie aktualizacji oprogramowania](/sccm/sum/deploy-use/automatically-deploy-software-updates).
- W prawej dolnej części pulpitu nawigacyjnego kliknij polecenie **utworzyć ustawienia agenta klienta** otworzyć ustawienia agenta klienta. Aby uzyskać więcej informacji, zobacz [informacje o ustawieniach klienta](/sccm/core/clients/deploy/about-client-settings).



Aby uzyskać więcej informacji o aktualizacjach Office 365 ProPlus, zobacz [zarządzania Office 365 ProPlus aktualizacji z programu Configuration Manager](/sccm/sum/deploy-use/manage-office-365-proplus-updates).

## <a name="deploy-office-365-apps-to-clients"></a>Wdrażanie aplikacji Office 365 na klientów
W tej wersji z poziomu pulpitu nawigacyjnego zarządzania klientami usługi Office 365 można uruchomić Instalatora 365 pakietu Office, który pozwala skonfigurować ustawienia instalacji usługi Office 365, pobierać pliki z pakietu Office sieci dostarczania zawartości (CDN) i wdrożyć pliki aplikacji w programie Configuration Manager.

### <a name="limitations-of-office-365-deployment"></a>Ograniczenia dotyczące wdrażania usługi Office 365
- Konieczne może być problemy podczas próby zaimportowania istniejących ustawień klienta (XML) w Kreatorze instalacji programu Office 365 aplikacji. Można ręcznie skonfigurować ustawienia klienta bez problemu.

#### <a name="to-deploy-office-365-apps-to-clients"></a>Do wdrażania aplikacji Office 365 na klientach
1. W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** > **Przegląd** > **Zarządzanie klientem usługi Office 365**.
2. Kliknij przycisk **Office 365 Instalator** w prawym górnym okienku. Zostanie otwarty Kreator instalacji klienta Office 365.
3. Na **ustawienia aplikacji** , podaj nazwę i opis aplikacji, wprowadź lokalizację pobierania plików, a następnie kliknij przycisk **dalej**. Należy zauważyć, że lokalizacja musi być określony w formie &#92; &#92; *server*&#92; *udostępnianie*.
4. Na **importowania ustawień klienta** wybierz, czy do importowania ustawień klienta usługi Office 365 z istniejący plik konfiguracyjny XML lub ręcznie określ ustawienia, a następnie kliknij przycisk **dalej**.
Gdy istniejący plik konfiguracyjny, wprowadź lokalizację pliku, a następnie przejdź do kroku 7. Należy zauważyć, że lokalizacja musi być określony w formie &#92; &#92; *server*&#92; *udostępnianie*&#92;* Nazwa pliku*. PLIK XML.

    > [!IMPORTANT]
    >Konieczne może być problemy podczas próby zaimportowania istniejących ustawień klienta (XML) w tym technical preview.

5. Na **produkty klienta** , Office 365 wybierz pakiet, który można użyć, wybierz aplikacje, które chcesz dołączyć, zaznacz dodatkowe produkty pakietu Office, które powinny być uwzględnione, a następnie kliknij **dalej**.
6. Na **ustawień klienta** wybierz ustawienia do uwzględnienia, a następnie kliknij przycisk **dalej**.
7. Na **wdrożenia** wybierz, czy wdrożyć aplikację, a następnie kliknij przycisk **dalej**.
Jeśli nie wdrożyć pakiet w kreatorze, przejdź do kroku 9.
8. W pozostałej części strony kreatora należy skonfigurować, tak jak w przypadku wdrażania Typowa aplikacja. Aby uzyskać więcej informacji, zobacz [tworzenia i wdrażania aplikacji](/sccm/apps/get-started/create-and-deploy-an-application).
9. Ukończ pracę kreatora.
10. Można wdrożyć lub edytować aplikację, podobnie jak dowolnej innej aplikacji w programie Configuration Manager z **Biblioteka oprogramowania** > **Przegląd** > **zarządzania aplikacjami** > **aplikacji**.

>[!NOTE]
>Po wdrożeniu aplikacji Office 365, można utworzyć reguły automatycznego wdrażania do obsługi aplikacji. Aby utworzyć ADR dla aplikacji usługi Office 365, kliknij przycisk **utworzyć ADR**i wybierz **Office 365 klienta** po wybraniu produktu. Aby uzyskać więcej informacji, zobacz [automatyczne wdrażanie aktualizacji oprogramowania](/sccm/sum/deploy-use/automatically-deploy-software-updates).

## <a name="BKMK_UEFIConversion"></a>Ulepszenia systemu BIOS z interfejsem UEFI konwersji
Teraz można dostosować sekwencję zadań wdrażania systemu operacyjnego za pomocą nowej zmiennej TSUEFIDrive, tak, aby krok Uruchom ponownie komputer będzie przygotować przejścia do UEFI FAT32 partycji na dysku twardym. Poniższa procedura zawiera przykładowy sposób tworzenia kroki sekwencji zadań, aby przygotować dysk twardy do systemu BIOS z interfejsem UEFI konwersji.

#### <a name="to-prepare-the-fat32-partition-for-the-conversion-to-uefi"></a>Aby przygotować partycji FAT32 do konwersji na UEFI:
W istniejącej sekwencji zadań w celu zainstalowania systemu operacyjnego dodasz nową grupę czynności BIOS z interfejsem UEFI konwersji.

1. Utwórz nową grupę sekwencji zadań, po kroki, aby przechwytywać pliki i ustawienia, a przed czynności w celu zainstalowania systemu operacyjnego. Na przykład utwórz grupę po **Przechwyć pliki i ustawienia** grupy o nazwie **z systemu BIOS z interfejsem UEFI**.
2. Na **opcje** kartę w nowej grupie, należy dodać zmienną sekwencji zadań jako warunek gdzie **_SMSTSBootUEFI** jest **jest równa** do **true**. Zapobiega to uruchomione, gdy komputer jest już w trybie UEFI czynności w grupie.
![System BIOS z interfejsem UEFI grupy](media/BIOS-to-UEFI-group.png)
3. W ramach nowej grupy, należy dodać **Uruchom ponownie komputer** sekwencji zadań. W **Określ, co uruchomić po ponownym uruchomieniu**, wybierz opcję **obraz rozruchowy przypisany do tej sekwencji zadań jest wybrane** do uruchomienia komputera w środowisku Windows PE.  
4. Na **opcje** , Dodaj zmienną sekwencji zadań jako warunek gdzie **_SMSTSInWinPE jest równa false**. Ten krok to zapobiega uruchamianiu, jeśli komputer jest już w środowisku Windows PE.

    ![Uruchom ponownie komputer](media/Restart-in-Windows-PE.png)
5. Dodaj krok, aby uruchomić narzędzie OEM, który przekonwertuje oprogramowania sprzętowego BIOS z interfejsem UEFI. Są to zazwyczaj **Uruchom wiersz polecenia** sekwencji zadań przy użyciu wiersza polecenia, aby uruchomić narzędzie OEM.
5.    Dodaj krok sekwencji zadań Formatuj dysk partycji i podzielić na partycje i sformatuj dysk twardy. W kroku wykonaj następujące czynności:
    1.    Utwórz partycję FAT32, który zostanie przekonwertowany na UEFI, przed zainstalowaniem systemu operacyjnego. Wybierz **GPT** dla **dysku typu**.
    ![Format i partycji dysku kroku](media/Format-and-partition-disk.png)
    2.    Przejdź do właściwości partycji FAT32. Wprowadź **TSUEFIDrive** w **zmiennej** pola. Jeśli sekwencja zadań wykryje tej zmiennej, przygotuje przejścia UEFI przed ponownym uruchomieniem komputera.
    ![Właściwości partycji.](media/Partition-properties.png)
    3. Utwórz partycję NTFS używany przez aparat sekwencji zadań do zapisania stanu oraz do przechowywania plików dziennika.
6.    Dodaj **Uruchom ponownie komputer** sekwencji zadań. W **Określ, co uruchomić po ponownym uruchomieniu**, wybierz opcję **obraz rozruchowy przypisany do tej sekwencji zadań jest wybrane** do uruchomienia komputera w środowisku Windows PE.  




## <a name="intune-compliance-charts"></a>Wykresy zgodności Intune
W tej wersji można uzyskać szybki widok ogólnej zgodności dla urządzeń i do górnej przyczyn braku zgodności, za pomocą nowych wykresów w obszarze **obszaru roboczego monitorowanie** w konsoli programu Configuration Manager.

#### <a name="to-view-the-intune-compliance-charts"></a>Aby wyświetlać wykresy zgodności Intune
1. W konsoli programu Configuration Manager, przejdź do **monitorowanie** > **Przegląd** > **ustawień zgodności**.
2. **Ogólnej zgodności urządzenia** wykresu jest wyświetlana.
3. Kliknij przycisk **zasady zgodności** węzeł, aby wyświetlić **ogólnej zgodności urządzenia** i **przyczyn niezgodność pierwszych** wykresów.

### <a name="limitations-of-intune-compliance-charts-in-tp-1609"></a>Ograniczenia Intune zgodności wykresy w TP 1609
- Przejście do **ogólnej zgodności urządzenia** wykresu aktualnie generuje błąd.
- **Najważniejsze powody niezgodność** wykres zawiera nazwę zasady i nie poszczególnych przyczyn braku zgodności. Możesz kliknąć zasady przechodzenia i urządzenia, które są niezgodne dla tej zasady.

### <a name="try-it-out"></a>Wypróbuj to
Wykonaj poniższe sekcje w kolejności:

#### <a name="check-overall-compliance-chart"></a>Sprawdzanie zgodności ogólnej wykresu
1. Dodać na dwa iOS zasady zgodności w programie Configuration Manager. Jedna zasada powinien mieć jeden zestaw ustawień dla urządzeń (na przykład zestaw długość numeru PIN do 6). Inne zasady powinien mieć inny zestaw ustawień (na przykład złożoności numeru PIN). Ustawienia zasad nie nakładają się ani wystąpił konflikt.
2. Wdrażanie zasad dwóch zestawu użytkowników.
3. Zarejestruj dwa urządzenia z systemem iOS w usłudze Intune przy użyciu tego samego konta użytkownika, a konta, które otrzymał zasady w poprzednim kroku. Urządzenia nie powinny spełniać kryteria zasady zgodności.
4. Sprawdź w Menedżerze konfiguracji **ogólnej zgodności urządzenia** wykresu. Oba urządzenia należy zgłaszać jako niezgodny.
<!-- 5. Click the **Non-compliant** section of the chart. Both devices should appear in the filtered view under **Assets and Compliance** > **Overview** > **Device**. -->

#### <a name="check-the-top-non-compliance-reasons-chart"></a>Sprawdź wykres najważniejsze powody niezgodność
5. Sprawdź **najważniejsze powody niezgodność** wykresu. Ten wykres zawiera listę pierwsze 5 przyczyn braku zgodności, ale tylko dwa ustawienia zgodności zostały ustawione przez zasady tylko pierwszych 2 niezgodności przyczyny są wyświetlane.
6. Kliknij jedną z sekcji na wykresie. Oba urządzenia powinny być wyświetlane w filtrowanym widoku w obszarze **zasoby i zgodność** > **Przegląd** > **urządzenia**.

#### <a name="make-devices-compliant-and-check-the-charts"></a>Zapewnienia zgodności urządzenia i sprawdź wykresów
7. Wprowadź jedną z urządzenia zgodne z jedną z zasad. Sprawdź **ogólnej zgodności urządzenia** ponownie wykresu. Jedno urządzenie zgodnych i niezgodnych jeden wykres powinien być wyświetlany.
8. Inne urządzenie zapewnienia zgodności z tych samych zasad. Spowoduje to jedno urządzenie zgodne z zasadami i jednego urządzenia zgodne z tylko jedną z zasad.
9. Sprawdź **najważniejsze powody niezgodność** wykresu. Należy tylko jedną z wymienionych przyczyn braku zgodności.
<!--7. Click the **Compliant** section of the chart. Only the compliant device should appear in the filtered view. -->





## <a name="see-also"></a>Zobacz też
[Technical Preview dla programu System Center Configuration Manager](../../core/get-started/technical-preview.md)

