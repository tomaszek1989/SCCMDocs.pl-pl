---
title: Planowanie i konfigurowanie zarządzania aplikacjami
titleSuffix: Configuration Manager
description: Wdrożenie oraz skonfigurować zależności niezbędne do wdrażania aplikacji w programie System Center Configuration Manager.
ms.date: 11/07/2017
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: 2be84a1d-ebb9-47ae-8982-c66d5b92a52a
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 18d9fe80a1c5525457579dadbfeaeafa3425202d
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="plan-for-and-configure-application-management-in-system-center-configuration-manager"></a>Planowanie konfiguracji zarządzania aplikacjami w programie System Center Configuration Manager i przeprowadzanie konfiguracji

*Dotyczy: System Center Configuration Manager (wersji current branch)*

Skorzystaj z informacji w tym artykule ułatwiają zaimplementowanie zależności niezbędne do wdrożenia aplikacji w programie System Center Configuration Manager.  

## <a name="dependencies-external-to-configuration-manager"></a>Zależności poza programem Configuration Manager  

|Zależność|Więcej informacji|  
|------------------|----------------------|  
|Internet Information Services (IIS) jest wymagany na serwerach systemu lokacji z systemem punkt witryny sieci Web katalogu aplikacji, punkt usługi sieci web katalogu aplikacji, punkt zarządzania i punkt dystrybucji.|Aby uzyskać więcej informacji na temat tego wymagania, zobacz [obsługiwane konfiguracje](../../core/plan-design/configs/supported-configurations.md).|  
|Urządzenia przenośne, które są zarejestrowane przez program Configuration Manager|Gdy podpisać kod aplikacji można je wdrożyć na urządzeniach przenośnych, nie używaj certyfikatów wygenerowanych przy użyciu szablonu wersji 3 (**systemu Windows Server 2008, Enterprise Edition**). Ten szablon certyfikatu tworzy certyfikaty, które jest niezgodne z aplikacjami programu Configuration Manager dla urządzeń przenośnych.<br /><br /> Jeśli używasz usług certyfikatów Active Directory do podpisania kodu aplikacji przeznaczonych na urządzenia przenośne, nie używaj szablonu certyfikatu w wersji 3.|  
|Klienci musi być skonfigurowana do Przeprowadź inspekcję zdarzeń logowania, jeśli chcesz automatycznie tworzyć koligacje urządzenia użytkownika.|Klient programu Configuration Manager odczytuje zdarzenia logowania typu **Powodzenie** z dziennika zdarzeń zabezpieczeń komputera do określenia koligacji urządzeń użytkowników.  Zdarzenia te są włączane przez następujące zasady inspekcji dwóch:<br>**Przeprowadź inspekcję zdarzeń logowania na kontach**<br>**Przeprowadź inspekcję zdarzeń logowania**<br>Aby automatycznie utworzyć relacje między użytkownikami i urządzeniami, upewnij sie, że te dwa ustawienia są włączone na komputerach klienckich. Aby skonfigurować te ustawienia, można użyć zasad grup systemu Windows.|  

## <a name="configuration-manager-dependencies"></a>Zależności programu Configuration Manager   

|Zależność|Więcej informacji|  
|------------------|----------------------|  
|Punkt zarządzania|Klienci kontaktują się z punktem zarządzania w celu pobierania zasad klienta, aby zlokalizować zawartość i nawiązanie połączenia z katalogiem aplikacji.<br /><br /> Jeśli klienci nie mogą uzyskać dostęp do punktu zarządzania, nie mogą używać katalogu aplikacji.|  
|Punkt dystrybucji|Przed wdrożeniem aplikacji na klientach do hierarchii należy dodać co najmniej jeden punkt dystrybucji. Domyślnie podczas standardowej instalacji rola punktu dystrybucji jest włączana na serwerze lokacji. Liczba i lokalizacja punktów dystrybucji się różnić zależnie od konkretnych wymogów obowiązujących w przedsiębiorstwie.<br /><br /> Aby uzyskać więcej informacji o instalacji punktów dystrybucji i zarządzaniu zawartością, zobacz [zarządzanie zawartością i infrastrukturą zawartości](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).|  
|Ustawienia klienta|Wiele ustawień klienta kontrolować sposób instalacji aplikacji na kliencie i użytkownik obsługi na kliencie. Te ustawienia klienta są następujące:<br /><br /><ul><li>Agent komputera</li><li>Ponowne uruchomienie komputera</li><li>Wdrażanie oprogramowania</li><li>Koligacja użytkowników i urządzeń</li></ul> Aby uzyskać więcej informacji o tych ustawieniach klienta, zobacz [informacje o ustawieniach klienta](../../core/clients/deploy/about-client-settings.md).<br /><br /> Aby uzyskać więcej informacji o sposobie konfigurowania ustawień klienta, zobacz [sposób konfigurowania ustawień klienta](../../core/clients/deploy/configure-client-settings.md).|  
|Wykryte konta użytkowników dla katalogu aplikacji |Menedżer konfiguracji musi najpierw odnajdywania kont użytkowników, zanim użytkownicy mogą wyświetlać i zażądać aplikacji z katalogu aplikacji. Aby uzyskać więcej informacji, zobacz [odnajdywania](/sccm/core/servers/deploy/configure/run-discovery).|  
|Klienci App-V 4.6 SP1 lub nowsi do uruchamiania aplikacji wirtualnych|Aby tworzyć aplikacje wirtualne w programie Configuration Manager, komputery klienckie musi mieć App-V 4.6 z dodatkiem SP1 lub nowszy zainstalowany klient.<br /><br /> Należy również zaktualizować klienta App-V poprawką opisaną w [artykułu bazy wiedzy 2645225](http://go.microsoft.com/fwlink/p/?LinkId=237322) przed wdrożeniem aplikacji wirtualnych.|  
|Punkt usługi sieci Web Wykaz aplikacji|Punkt usługi sieci Web katalogu aplikacji to rola systemu lokacji, która zapewnia witrynie sieci Web katalogu aplikacji informacje o oprogramowaniu dostępnym w bibliotece oprogramowania.<br /><br /> Aby uzyskać więcej informacji na temat konfigurowania tej roli systemu lokacji, zobacz [Configure Software Center i wykaz aplikacji (tylko komputery z systemem Windows)](/sccm/apps/plan-design/plan-for-and-configure-application-management#configure-software-center-and-the-application-catalog-windows-pcs-only) w tym artykule.|  
|Punkt witryny sieci Web wykazu aplikacji|Punkt witryny sieci Web katalogu aplikacji to rola systemu lokacji, która dostarcza użytkownikom listę dostępnego oprogramowania.<br /><br /> Aby uzyskać więcej informacji na temat konfigurowania tej roli systemu lokacji, zobacz [Configure Software Center i wykaz aplikacji (tylko komputery z systemem Windows)](/sccm/apps/plan-design/plan-for-and-configure-application-management#configure-software-center-and-the-application-catalog-windows-pcs-only) w tym artykule.|  
|Punkt usług raportowania|Aby użyć raportów w programie Configuration Manager do zarządzania aplikacjami, należy najpierw zainstalować i skonfigurować punkt usług raportowania.<br /><br /> Aby uzyskać więcej informacji, zobacz [Raportowanie w programie System Center Configuration Manager](../../core/servers/manage/reporting.md).|  
|Uprawnienia zabezpieczeń w zarządzaniu aplikacjami|Musi mieć następujące uprawnienia zabezpieczeń do zarządzania aplikacjami:<br /><br /> **Autor aplikacji** wymienione wyżej uprawnienia, które są wymagane do utworzenia, zmiany i wycofywania aplikacji w programie Configuration Manager obejmuje rola zabezpieczeń.<br /><br /> **Wdrażanie aplikacji:**<br /><br /> **Menedżer wdrażania aplikacji** wymienione wyżej uprawnienia, które są wymagane do wdrażania aplikacji w programie Configuration Manager obejmuje rola zabezpieczeń.<br /><br /> **Administrator aplikacji** rola zabezpieczeń ma wszystkie uprawnienia z obu **Autor aplikacji** i **Menedżer wdrażania aplikacji** ról zabezpieczeń.<br /><br /> Aby uzyskać więcej informacji, zobacz [Konfigurowanie administracji opartej na rolach](../../core/servers/deploy/configure/configure-role-based-administration.md).|  

##  <a name="configure-software-center-and-the-application-catalog-windows-pcs-only"></a>Konfigurowanie Centrum oprogramowania i wykazu aplikacji (tylko komputery z systemem Windows)  

 W programie System Center Configuration Manager, teraz są dwie opcje dla użytkowników zmienić ustawienia, przeglądać aplikacje i instalowanie aplikacji:  

-   **Nowe Centrum oprogramowania**: Nowe Centrum oprogramowania ma nowoczesny wygląd. Aplikacje, które wcześniej znajdowały się tylko w wykazie aplikacji zależnych od Silverlight (aplikacje dostępne dla użytkowników) teraz wyświetlane w Centrum oprogramowania w obszarze **aplikacji** kartę. Katalog aplikacji nadal będą dostępne za pośrednictwem łącza w obszarze **stan instalacji** Centrum oprogramowania.  

     Możesz skonfigurować klientów pod kątem używania nowego Centrum oprogramowania, włączając ustawienie klienta **Agent komputera** > **Użyj nowego Centrum oprogramowania**.  

    > [!IMPORTANT]  
    >  Chociaż nie trzeba się łączyć z katalogiem aplikacji, możesz nadal muszą skonfigurować punkt witryny sieci Web katalogu aplikacji i punkt usługi sieci web katalogu aplikacji zgodnie z opisem w następnej sekcji.  

-   **Poprzednie Centrum oprogramowania i wykaz aplikacji**: Domyślnie użytkownicy nadal do łączenia z poprzedniej wersji programu Software Center i Połącz z wykazem aplikacji (wymagany przeglądarki sieci web obsługujących technologię Silverlight) do przeglądania dostępnych aplikacji.  

 Niezależnie od wersji chcesz użyć, Software Center jest instalowany automatycznie podczas instalowania klienta programu Configuration Manager na komputerach z systemem Windows.  

    > [!TIP]  
    >  Wersja Centrum oprogramowania, które użytkownicy widzą zależy od ustawień klienta programu Configuration Manager. Zapewnia to elastyczność kontroli wersji, która jest używana oparta na niestandardowe ustawienia klienta, które można wdrożyć w kolekcji. 

    > [!IMPORTANT]
    > W najbliższych miesiącach firma Microsoft będzie usuwanie poprzedniej wersji Centrum oprogramowania, a nie będą dostępne.
    > Możesz skonfigurować klientów pod kątem używania nowego Centrum oprogramowania, włączając ustawienie klienta **Agent komputera** > **Użyj nowego Centrum oprogramowania**. 

## <a name="steps-to-install-and-configure-the-application-catalog-and-software-center"></a>Kroki instalowania i konfigurowania wykazu aplikacji i Centrum oprogramowania  

> [!IMPORTANT]  
>  Przed wykonaniem tych kroków upewnij się, że zostały spełnione wszystkie wymagania wstępne wymienione wcześniej.  

|Kroki|Szczegóły|Więcej informacji|  
|-----------|-------------|----------------------|  
|**Krok 1.** Jeśli używali połączeń HTTPS, upewnij się, że został wdrożony certyfikat serwera sieci web na serwerach systemu lokacji.|Wdróż certyfikat serwera sieci Web na serwerze systemu lokacji, na których zostanie uruchomiony punkt witryny sieci Web katalogu aplikacji i punkt usługi sieci Web katalogu aplikacji.<br /><br /> Ponadto jeśli klienci powinni używać katalogu aplikacji z Internetu, należy wdrożyć certyfikat serwera sieci web na serwerze systemu lokacji punktu zarządzania co najmniej jeden i skonfiguruj ją dla połączeń klientów z Internetu.|Aby uzyskać więcej informacji o wymaganiach dotyczących certyfikatów, zobacz [wymagania dotyczące certyfikatu PKI](../../core/plan-design/network/pki-certificate-requirements.md).|  
|**Krok 2.** Jeśli używasz certyfikatu PKI klienta dla połączeń z punktami zarządzania, należy wdrożyć certyfikat uwierzytelniania klienta na komputerach klienckich.|Mimo że klienci nie używają certyfikatu PKI klienta do nawiązania połączenia z katalogiem aplikacji, musi łączą się z punktem zarządzania przed użyciem katalogu aplikacji. Certyfikat uwierzytelniania klienta należy wdrożyć na klientach w następujących scenariuszach:<br /><br /><ul><li>Wszystkie punkty zarządzania w intranecie akceptują tylko połączenia klienckie HTTPS.</li><li>Klienci nawiązują połączenie z katalogiem aplikacji z Internetu.</li></ul>|Aby uzyskać więcej informacji o wymaganiach dotyczących certyfikatów, zobacz [wymagania dotyczące certyfikatu PKI](../../core/plan-design/network/pki-certificate-requirements.md).|  
|**Krok 3.** Zainstaluj i skonfiguruj punkt usługi sieci web katalogu aplikacji i witryny sieci Web katalogu aplikacji.|W tej samej lokacji, należy zainstalować obie role systemu lokacji. Nie masz do zainstalowania go na tym samym serwerze systemu lokacji lub w tym samym lesie usługi Active Directory. Jednak punkt usługi sieci web katalogu aplikacji musi być w tym samym lesie co baza danych lokacji.|Aby uzyskać więcej informacji o umieszczaniu ról systemu lokacji, zobacz [Planowanie serwerów systemu lokacji i ról systemu lokacji](../../core/plan-design/hierarchy/plan-for-site-system-servers-and-site-system-roles.md).<br /><br /> Aby skonfigurować punkt usługi sieci web katalogu aplikacji i punkt witryny sieci Web katalogu aplikacji, zobacz **krok 3: Instalowanie i konfigurowanie ról systemu lokacji katalogu aplikacji**.|  
|**Krok 4.** Konfigurowanie ustawień klienta dla wykazu aplikacji i Centrum oprogramowania.|Skonfiguruj domyślne ustawienia klienta, jeśli wszyscy użytkownicy mają korzystać z tych samych ustawień. W przeciwnym razie skonfiguruj niestandardowe ustawienia klienta dla określonych kolekcji.|Aby uzyskać więcej informacji dotyczących ustawień klienta, zobacz [informacje o ustawieniach klienta](../../core/clients/deploy/about-client-settings.md).<br /><br /> Aby uzyskać więcej informacji o sposobie konfigurowania tych ustawień klienta, zobacz **krok 4: Konfigurowanie ustawień klienta dla wykazu aplikacji i Centrum oprogramowania**.|  
|**Krok 5.** Sprawdź, czy katalog aplikacji działa.|Można użyć katalogu aplikacji bezpośrednio z poziomu przeglądarki lub Centrum oprogramowania.|Zobacz **krok 5: Sprawdź, czy katalog aplikacji działa**.|  

## <a name="supplemental-procedures-to-install-and-configure-the-application-catalog-and-software-center"></a>Dodatkowe procedury w celu zainstalowania i skonfigurowania katalogu aplikacji i programu Software Center  
 Jeżeli kroki opisane w poprzedniej tabeli wymagają wykonania dodatkowych czynności, zapoznaj się z poniższymi informacjami.  

###  <a name="step-3-install-and-configure-the-application-catalog-site-system-roles"></a>Krok 3. Instalowanie i konfigurowanie ról systemu lokacji katalogu aplikacji  
 Te procedury umożliwiają skonfigurowanie ról systemu lokacji dla katalogu aplikacji. Wybierz jedną z dwóch poniższych procedur w zależności od tego, czy będzie instalował nowy serwer systemu lokacji lub użyj istniejącego serwera systemu lokacji:  

> [!NOTE]  
>  Katalogu aplikacji nie można zainstalować w lokacji pomocniczej ani w centralnej lokacji administracyjnej.  

####  <a name="to-install-and-configure-the-application-catalog-site-systems-new-site-system-server"></a>Aby zainstalować i skonfigurować systemy lokacji wykazu aplikacji: Nowy serwer systemu lokacji  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **konfiguracja lokacji** > **serwery i role systemu lokacji**.  

3.  Na **Home** karcie **Utwórz** grupy, wybierz **Utwórz serwer systemu lokacji**.  

4.  Na **ogólne** strony Określ ustawienia ogólne systemu lokacji, a następnie wybierz pozycję **dalej**.  

    > [!TIP]  
    >  Jeśli chcesz, aby komputery klienckie mają używać katalogu aplikacji przez internet, określ w pełni kwalifikowana nazwa domeny (FQDN) przez internet.  

5.  Na **Wybór roli systemu** wybierz pozycję **punkt usługi sieci web katalogu aplikacji** i **punkt witryny sieci Web katalogu aplikacji** z listy dostępnych ról, a następnie wybierz pozycję **dalej**.  

6.  Wykonaj pozostałe kroki.  

####  <a name="to-install-and-configure-the-application-catalog-site-systems-existing-site-system-server"></a>Aby zainstalować i skonfigurować systemy lokacji wykazu aplikacji: Istniejący serwer systemu lokacji  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **konfiguracja lokacji** > **serwery i role systemu lokacji**, a następnie wybierz serwer, na potrzeby katalogu aplikacji.  

3.  Na **Home** karcie **serwera** grupy, wybierz **dodawania ról systemu lokacji**.  

4.  Na **ogólne** strony Określ ustawienia ogólne systemu lokacji, a następnie wybierz pozycję **dalej**.  

    > [!TIP]  
    >  Jeśli chcesz, aby komputery klienckie mają używać katalogu aplikacji przez internet, określ w pełni kwalifikowana nazwa domeny (FQDN) przez internet.  

5.  Na **Wybór roli systemu** wybierz pozycję **punkt usługi sieci web katalogu aplikacji** i **punkt witryny sieci Web katalogu aplikacji** z listy dostępnych ról, a następnie wybierz pozycję **dalej**.  

6.  Wykonaj pozostałe kroki.  

7. Instalację tych ról serwera lokacji można zweryfikować, korzystając z komunikatów o stanie i przeglądając pliki dzienników:  

    Komunikaty o stanie: Użyj składników **SMS_PORTALWEB_CONTROL_MANAGER** i **SMS_AWEBSVC_CONTROL_MANAGER**.  

    Przykładowo, identyfikator stanu **1015** dla **SMS_PORTALWEB_CONTROL_MANAGER** potwierdza, że Menedżer składników lokacji pomyślnie zainstalował punkt witryny sieci Web katalogu aplikacji.  

    Pliki dziennika: Wyszukaj **SMSAWEBSVCSetup.log** i **SMSPORTALWEBSetup.log**.  

    Aby uzyskać więcej informacji, wyszukaj **awebsvcMSI.log** i **portlwebMSI.log** pliki dziennika.  

###  <a name="step-4-configure-the-client-settings-for-the-application-catalog-and-software-center"></a>Krok 4. Konfigurowanie ustawień klienta dla wykazu aplikacji i Centrum oprogramowania  
 Ta procedura umożliwia skonfigurowanie domyślnych ustawień klienta dla wykazu aplikacji i Centrum oprogramowania mające zastosowanie do wszystkich urządzeń w hierarchii. Jeśli chcesz, aby te ustawienia miały zastosowanie tylko do niektórych urządzeń, można utworzyć niestandardowe ustawienie klienta i wdróż je do kolekcji, która ma urządzenia z określonych ustawień. Aby uzyskać więcej informacji na temat tworzenia niestandardowych ustawień urządzeń, zobacz [jak utworzyć i wdrożyć niestandardowe ustawienia klienta](../../core/clients/deploy/configure-client-settings.md#create-and-deploy-custom-client-settings) sekcji [sposób konfigurowania ustawień klienta w programie System Center Configuration Manager](../../core/clients/deploy/configure-client-settings.md).  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **ustawień klienta** > **domyślne ustawienia klienta**.  

3.  Na **Home** karcie **właściwości** grupy, wybierz **właściwości**.  

4.  Przejrzyj i skonfiguruj ustawienia związane z powiadomieniami użytkowników, katalogiem aplikacji i programem Software Center. Na przykład:  

    1.  Grupa**Agent komputera** :  

        -   **Domyślny punkt witryny sieci Web katalogu aplikacji**.  

        -   **Dodaj domyślną witrynę sieci Web z katalogu aplikacji do strefy Zaufane witryny programu Internet Explorer**.  

        -   **Nazwa organizacji wyświetlana w Centrum oprogramowania**.  

            > [!TIP]  
            >  Aby określić nazwę organizacji, która jest wyświetlana w katalogu aplikacji i skonfigurować motyw witryny sieci Web, należy użyć **dostosowywania** we właściwościach witryny sieci Web katalogu aplikacji.  

        -   **Użyj nowego centrum oprogramowania**. Ustaw **tak** Jeśli chcesz użyć nowego centrum oprogramowania, która umożliwia użytkownikom wyszukiwanie i instalowanie dostępnych aplikacji bez potrzeby dostępu do katalogu aplikacji (co wymaga przeglądarki sieci web obsługującą program Silverlight).  

        -   **Uprawnienia do instalacji**.  

        -   **Pokaż powiadomienia o nowych wdrożeniach**.  

    2.  Grupa**Zarządzanie energią** :  

        -   **Zezwalaj użytkownikom na wykluczanie swoich urządzeń z zarządzania energią**.  

    3.  Grupa**Zdalne narzędzia** :  

        -   **Użytkownicy mogą zmieniać zasady lub ustawienia powiadomień w programie Software Center**.  

    4.  Grupa**Koligacja użytkowników i urządzeń** :  

        -   **Zezwalaj użytkownikom na definiowanie urządzeń podstawowych**.  

    > [!NOTE]  
    >  Aby uzyskać dodatkowe informacje dotyczące ustawień klienta, zobacz [Informacje o ustawieniach klienta w programie System Center Configuration Manager](../../core/clients/deploy/about-client-settings.md).  

5.  Wybierz **OK** zamknąć **domyślne ustawienia klienta** okno dialogowe.  

Klienci zostaną skonfigurowani przy użyciu tych ustawień podczas następnego pobierania zasad klienta. Aby zainicjować pobieranie zasad dla jednego klienta, zobacz [jak zarządzać klientami](../../core/clients/manage/manage-clients.md).

#### <a name="to-customize-software-center-branding"></a>Aby dostosować znakowania programu Software Center

Znakowanie niestandardowych w programie Software Center jest stosowane zgodnie z następującymi zasadami:

1. Jeśli nie zainstalowano roli serwera lokacji punktu witryny sieci Web katalogu aplikacji, a następnie Centrum oprogramowania będzie wyświetlana nazwa organizacji określona w **Agent komputera** ustawienia klienta **nazwa organizacji** wyświetlana w Centrum oprogramowania. Aby uzyskać instrukcje, zobacz [sposób konfigurowania ustawień klienta](https://docs.microsoft.com/sccm/core/clients/deploy/configure-client-settings).
2. Po zainstalowaniu roli serwera lokacji punktu witryny sieci Web katalogu aplikacji, Centrum oprogramowania będzie wyświetlana nazwa organizacji i kolor określone we właściwościach roli serwera lokacji katalogu aplikacji witryny sieci Web punktu. Aby uzyskać więcej informacji, zobacz [opcji konfiguracji dla punktu witryny sieci Web katalogu aplikacji](https://docs.microsoft.com/sccm/core/servers/deploy/configure/configuration-options-for-site-system-roles#BKMK_ApplicationCatalog_Website).
3. Jeśli subskrypcję Microsoft Intune jest skonfigurowana i połączona do programu Configuration Manager, Centrum oprogramowania będzie wyświetlana nazwa organizacji, kolor i logo firmy określone we właściwościach subskrypcji usługi Intune. Aby uzyskać więcej informacji, zobacz [Konfigurowanie subskrypcji usługi Microsoft Intune](https://docs.microsoft.com/sccm/mdm/deploy-use/setup-hybrid-mdm#step-3-configure-intune-subscription).

#### <a name="to-manually-set-software-center-branding"></a>Aby ręcznie ustawić znakowania programu Software Center
<!-- 1351224 -->
Wraz z wydaniem 1710 można ręcznie dodać znakowanie elementów przedsiębiorstwa i określ widoczność karty w Centrum oprogramowania. Można dodać nazwę firmy określonego programu Software Center, ustawić motyw kolorów konfiguracji programu Software Center, ustawienie logo firmy i ustawienie kartach widoczny na urządzeniach klienckich.

1. W **programu Configuration Manager** konsoli, wybierz **administracji** > **ustawień klienta**. Polecenie wystąpienia ustawienie żądaną klienta.
2. Na **Home** karcie **właściwości** grupy, wybierz **właściwości**.
3. W **ustawienia domyślne** oknie dialogowym wybierz **Centrum oprogramowania**.
4. Wybierz **tak** do **wybierz nowe ustawienia, aby określić informacje o firmie** Aby włączyć ustawienia dostosowywania Centrum oprogramowania.
5. Typ użytkownika **nazwa firmy**.
6. Wybierz użytkownika **schemat w programie Software Center kolorów**.
7. Kliknij przycisk **Przeglądaj** można przejść do logo w programie Software Center. Logo musi być formatem JPEG lub PNG 400 x 100 pikseli o maksymalnym rozmiarze 750 KB.
8. Wybierz **tak** uwidocznić karty w Centrum oprogramowania na urządzeniach klienckich. Co najmniej jedną kartę musi być widoczny:

    -  Włącz kartę aplikacje
    -  Włącz kartę Aktualizacje
    -  Włącz kartę systemów operacyjnych
    -  Włącz kartę Stan instalacji
    -  Włącz kartę zgodności urządzenia
    -  Włącz kartę Opcje

> [!IMPORTANT]  
>  Znakowanie Centrum oprogramowania są synchronizowane z usługą Intune na 14 dni. W związku z tym może wystąpić opóźnienie przed zmiany wprowadzone w usłudze Intune są wyświetlane w programie Configuration Manager.

###  <a name="step-5-verify-that-the-application-catalog-is-operational"></a>Krok 5. Sprawdź, czy katalog aplikacji działa  
 Poniższe procedury umożliwiają sprawdzenie, czy katalog aplikacji działa. Można użyć katalogu aplikacji bezpośrednio z poziomu przeglądarki lub Centrum oprogramowania.  

> [!NOTE]  
>  Katalog aplikacji wymaga programu Microsoft Silverlight, który jest instalowany automatycznie jak wymaganie wstępne klienta programu Configuration Manager. Jeśli używasz katalogu aplikacji bezpośrednio z poziomu przeglądarki przy użyciu komputera, który nie jest zainstalowany klient programu Configuration Manager, najpierw sprawdź, czy na komputerze jest zainstalowany program Microsoft Silverlight.  

> [!TIP]  
>  Brakujące warunki wstępne są typowe przyczyny katalogu aplikacji niepoprawnego działania po zakończeniu instalacji. Potwierdź wymagania wstępne ról systemu lokacji katalogu aplikacji. Można to zrobić za pomocą [obsługiwane konfiguracje](../../core/plan-design/configs/supported-configurations.md) artykułu.  

> [!NOTE]  
>  Jeśli zalogowano się przy użyciu konta administratora domeny, nie będą wyświetlane komunikaty powiadomień z klienta programu Configuration Manager (na przykład wiadomości wskazującą, czy dostępne jest nowe oprogramowanie).  

### <a name="to-use-the-application-catalog-directly-from-a-browser"></a>Aby używać katalogu aplikacji z przeglądarki  

-   W przeglądarce wprowadź adres witryny sieci Web katalogu aplikacji i upewnij się, że strona sieci Web zawiera trzy karty: **Katalog aplikacji**, **Moje żądania aplikacji**, i **urządzeń**.  

     Wybierz i użyj odpowiedni adres z poniższej listy dla katalogu aplikacji, których &lt;serwera&gt; to nazwa komputera, intranetowej nazwy FQDN lub nazwa FQDN internetowego:  

    -   Połączenia HTTPS klientów i domyślne ustawienia roli systemu lokacji: **https://&lt;serwera&gt;/CMApplicationCatalog**  

    -   Połączenia HTTP klientów i domyślne ustawienia roli systemu lokacji: **http://&lt;serwera&gt;/CMApplicationCatalog**  

    -   HTTPS połączenia klientów i niestandardowe ustawienia systemu lokacji roli: **https://&lt;serwera&gt;:&lt;portu&gt;/&lt;nazwę aplikacji sieci web&gt;**  

    -   Połączenia HTTP klientów i niestandardowe ustawienia systemu lokacji roli: **http://&lt;serwera&gt;:&lt;portu&gt;/&lt;nazwę aplikacji sieci web&gt;**  

### <a name="to-use-the-application-catalog-from-software-center-does-not-apply-to-the-new-version-of-software-center"></a>Aby używać katalogu aplikacji z Centrum oprogramowania (nie ma zastosowania do nowej wersji Centrum oprogramowania)  

1.  Na komputerze klienckim, wybierz **Start** > **wszystkie programy** > **Microsoft System Center 2012** > **programu Configuration Manager** > **Centrum oprogramowania**.  

2.  Jeśli wcześniej skonfigurowano nazwę organizacji dla programu Software Center jako ustawienie klienta, upewnij się, że jest wyświetlana ustawiona nazwa.  

3.  Wybierz **Wyszukaj dodatkowe aplikacje z katalogu aplikacji** i upewnij się, że strona zawiera trzy karty: **Katalog aplikacji**, **Moje żądania aplikacji**, i **urządzeń**.  

> [!WARNING]  
>  Po zainstalowaniu ról systemu lokacji katalogu aplikacji, użytkownik nie będzie wyświetlany natychmiast katalogu aplikacji po wybraniu **Wyszukaj dodatkowe aplikacje z katalogu aplikacji** łącza z programu Software Center. Katalog aplikacji staje się dostępny w programie Software Center, gdy klient następnym razem pobierze zasady klienta lub po upływie maksymalnie 25 godzin od momentu zainstalowania ról systemu lokacji katalogu aplikacji.  
