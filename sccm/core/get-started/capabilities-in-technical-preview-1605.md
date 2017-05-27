---
title: "Możliwości w Technical Preview 1605 programu Configuration Manager"
description: "Informacje na temat funkcji dostępnych w Technical Preview programu System Center Configuration Manager, wersja 1605."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2bafd028-1923-4463-9e3e-ee41bc0c437b
caps.latest.revision: 36
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 8b3d472c586e704ee48e9825138c72f655d89492
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="capabilities-in-technical-preview-1605-for-system-center-configuration-manager"></a>Możliwości w Technical Preview 1605 System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (Technical Preview)*

Ten artykuł wprowadza do funkcji, które są dostępne w Technical Preview programu System Center Configuration Manager, wersja 1605. Można zainstalować tę wersję, aby zaktualizować i dodawać nowe funkcje do lokacji programu Configuration Manager technical preview.      Przed zainstalowaniem tej wersji technical preview, przejrzyj temat wprowadzające [Technical Preview dla programu System Center Configuration Manager](../../core/get-started/technical-preview.md), aby zapoznać się z ogólne wymagania i ograniczenia dotyczące używania technical preview, jak zaktualizować między wersjami i jak Wyraź swoją opinię dotyczącą funkcji w technical preview.  

 **Znane problemy w tym Technical Preview:**  

-   Z 1605 Technical Preview po zaktualizowaniu właściwości punktu zarządzania po jej zainstalowaniu może zostać wyświetlony błąd konsoli, która wymusza zamknięcie konsoli.  W takim przypadku należy odinstalować punkt zarządzania i ponownie zainstalować punkt zarządzania przy użyciu odpowiednie ustawienia. Alternatywnie można zmodyfikować punktu zarządzania przed zainstalowaniem Technical Preview 1605.  

-   Gdy korzystanie ze Sklepu Windows funkcji biznesowych o 1604 Technical Preview, a następnie uaktualnić go do Technical Preview 1605, już nie można wyświetlić danych dołączania. Wszelkie inne funkcjonalnie będzie nadal działać. Jeśli użytkownik został załadowany z 1604 Technical Preview, pozostanie został załadowany po zainstalowaniu Technical Preview 1605 i muszą podejmować żadnych dodatkowych czynności.  

 **Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  

##  <a name="BKMK_PerAppVPN"></a>Urządzenia sieci VPN w systemie Windows 10 dla aplikacji  
 W przypadku urządzeń Windows 10 zarządzane przy użyciu programu Configuration Manager za pomocą usługi Intune można dodać listę aplikacji, które automatycznego otwierania połączenia VPN, który został skonfigurowany za pomocą konsoli administracyjnej programu Configuration Manager. Istnieje możliwość ograniczenia ruchu sieci VPN do tych aplikacji lub można kontynuować Zezwalaj na cały ruch przez połączenie VPN.  

 **Wymagania dotyczące**:  

-   Configuration Manager za pomocą usługi Intune  

-   Profil sieci VPN systemu Windows 10, który został wdrożony na co najmniej jedno urządzenie  

##  <a name="BKMK_InstallSU"></a>Ulepszenia sekwencja zadań instalacji aktualizacji oprogramowania  
 Do sekwencji zadań Zainstaluj aktualizacje oprogramowania zostały wprowadzone następujące ulepszenia:  

-   Nowej zmiennej sekwencji zadań, SMSTSSoftwareUpdateScanTimeout, jest dostępna daje możliwość kontroli limitu czasu na skanowanie aktualizacji oprogramowania podczas instalacji oprogramowania aktualizacje sekwencję zadań. Wartość domyślna to 30 minut.  

-   Zostały ulepszenia rejestrowania. Plik dziennika smsts.log będzie zawierać nowych wpisów dziennika odwołujące się do innych plików dziennika, które mogą pomóc rozwiązać problemy podczas procesu instalacji aktualizacji oprogramowania.  

##  <a name="BKMK_PrepareConfigMgrClient"></a>Ulepszenia przygotować klienta programu ConfigMgr dla kroku sekwencji zadań przechwytywania  
 Krok przygotować klienta programu ConfigMgr teraz spowoduje całkowite usunięcie klienta programu Configuration Manager, a nie tylko usunięcie informacji o kluczu. Po wdrożeniu przechwyconego obrazu systemu operacyjnego przez sekwencję zadań zainstalowania nowego klienta programu Configuration Manager zawsze.  

##  <a name="BKMK_Grace"></a>Okres prolongaty wdrożeń aplikacji  
 W niektórych przypadkach można umożliwić użytkownikom więcej czasu do Zainstaluj wdrożenia aplikacji poza żadnych terminy, które zostały skonfigurowane. Na przykład jeśli użytkownik końcowy właśnie został zwrócony z urlopie, konieczne może być oczekiwanie na długo jako aplikacja zaległe wdrożenia są instalowane. Mogą jednak nadal natychmiast zainstalować aplikacji w dowolnym momencie, które chcą.  

 Aby rozwiązać ten problem, można zdefiniować **okres prolongaty** przez wdrożenie ustawień klienta programu Configuration Manager do kolekcji.  

 Aby skonfigurować okres prolongaty, należy wykonać następujące czynności:  

1.  Na **Agent komputera** strony ustawień klienta, należy skonfigurować nową właściwość **okres prolongaty dla wymuszania po wdrożeniu termin ostateczny (w godzinach)** o wartości między **1** i **120** godzin.  

2.  W nowe wdrożenia aplikacji lub we właściwościach istniejącego wdrożenia na **Planowanie** strony, zaznacz pole wyboru **opóźnienie wymuszania tego wdrożenia, zgodnie z preferencjami użytkownika**, aż do okresu prolongaty zdefiniowane w ustawieniach klienta.  

     Wszystkie wdrożenia, które mają to pole wyboru, zaznaczone i które są przeznaczone dla urządzeń, do których również wdrożyć ustawienia klienta użyje okresu prolongaty.  

 W tej wersji okres prolongaty, które można skonfigurować nie jest używany przez urządzenia klienckie. Jeśli skonfigurowano okres prolongaty, a następnie zaznacz pole wyboru, aplikacja zostanie zainstalowana w pierwszym oknie-business użytkownika skonfigurowane po upływie ostatecznego terminu.  

 Podobne opcje zostały dodane do Kreatora wdrażania aktualizacji oprogramowania, Kreator reguł wdrażania automatycznego i stron właściwości. Jednak te nie są obecnie implementowane w tym technical preview.  

##  <a name="BKMK_Remote"></a>Nowe środowisko dla akcji urządzenie zdalne  
 Udoskonalono obsługę wykonanie akcji urządzenia zdalnego z konsoli programu Configuration Manager.  
Typowe akcje, takie jak **wycofywania i czyszczenia**, **resetowania kodu dostępu**, **zdalnego blokowania**, i **obejścia blokady aktywacji** można znaleźć w **zdalnego akcji urządzenia** dostępne z menu **zasoby i zgodność** obszaru roboczego.  

 ![Nowe akcje urządzenia zdalnego zrzut ekranu](media/New-Remote-Device-Actions.png)  

 Stan dla każdego z tych operacji można znaleźć w następujących miejscach:  

-   W okienku szczegółów po wybraniu urządzenia z **urządzeń** węzła.  

-   Na **właściwości** strony dla urządzenia.  

-   Na stronie głównej **urządzeń** węzła (nie wszystkie kolumny mogą być widoczne domyślnie).  

 Aby uzyskać więcej informacji na temat iOS obejścia blokady aktywacji, zobacz [chronić iOS urządzeniami przy użyciu blokady aktywacji obejścia dla programu Configuration Manager](/sccm/mdm/deploy-use/manage-ios-activation-lock), w szczególności **bieżącego znane problemy związane z blokadę aktywacji obejścia w Menedżerze konfiguracji Technical Preview** sekcji.  

##  <a name="BKMK_WSFB"></a>Sklep Windows dla aplikacji biznesowych  
 [Sklepu Windows dla firm](https://www.microsoft.com/business-store) pozwala znaleźć i zakupić aplikacji dla danej organizacji, pojedynczo lub w woluminie. Łącząc sklepu do programu Configuration Manager, można zarządzać zakupione woluminu aplikacji z konsoli programu Configuration Manager, na przykład:  

-   Listy zakupionych aplikacji można synchronizować z programu Configuration Manager  

-   Aplikacje, które są synchronizowane są wyświetlane w konsoli programu Configuration Manager i można wdrożyć takich jak inne aplikacje  

-   Co 24 godziny, Configuration Manager pobiera informacje o licencjonowaniu aplikacji ze sklepu i można to sprawdzić w konsoli programu Configuration Manager  

 W wersji 1604 technical preview można synchronizować i wyświetlić aplikacje w Sklepie Windows dla firm w konsoli programu Configuration Manager. W tej wersji dodaliśmy możliwość tworzenia i wdrażania aplikacji programu Configuration Manager z aplikacji do sklepu zsynchronizowane.  

### <a name="set-up-windows-store-for-business-synchronization"></a>Konfigurowanie magazynu systemu Windows dla synchronizacji biznesowe  

1.  W usłudze Azure Active Directory należy zarejestrować programu Configuration Manager jako narzędzia do zarządzania "API sieci Web i/lub aplikacji sieci Web". Zapewni to identyfikator klienta, który trzeba będzie później.  

    1.  W węźle usługi Active Directory [https://manage.windowsazure.com](https://manage.windowsazure.com), wybierz Azure Active Directory, a następnie kliknij przycisk **aplikacje** > **Dodaj**.  

    2.  Kliknij przycisk **Dodawanie mojej organizacji jest opracowywanie aplikacji**.  

    3.  Wprowadź nazwę aplikacji, wybierz opcję **aplikacji sieci Web** i/lub **interfejsu API sieci Web**, następnie kliknij przycisk **dalej** strzałki.  

    4.  Wprowadź ten sam adres URL dla obu **adres URL logowania jednokrotnego** i **URI Identyfikatora aplikacji**. Adres URL może być dowolny i nie musi rozpoznać adres rzeczywisty. Na przykład, można wprowadzić **https://&lt;domena > / sccm**.  

    5.  Ukończ pracę kreatora.  

2.  W usłudze Azure Active Directory Utwórz klucz klienta dla narzędzia do zarządzania zarejestrowane.  

    1.  Wyróżnij aplikacji został utworzony, a następnie kliknij przycisk **Konfiguruj**.  

    2.  W obszarze **klucze**, wybierz czas trwania z listy i kliknij przycisk **zapisać**. Spowoduje to utworzenie nowego klucza klienta. Nie opuścić tę stronę, dopóki nie został pomyślnie dołączono maszynę wirtualną Sklepu Windows dla firm do programu Configuration Manager.  

3.  W Sklepie Windows dla firmy należy skonfigurować jako narzędzie do zarządzania magazynami programu Configuration Manager.  

    1.  Otwórz [https://businessstore.microsoft.com/en-us/managementtools](https://businessstore.microsoft.com/managementtools) i zaloguj się po wyświetleniu monitu.  

    2.  Zaakceptuj warunki użytkowania, jeśli jest to wymagane.  

    3.  W obszarze **narzędzia do zarządzania**, kliknij przycisk **Dodaj narzędzia do zarządzania**.  

    4.  W **Wyszukaj według nazwy narzędzie**, wpisz nazwę aplikacji utworzonych w AAD wcześniej, a następnie kliknij przycisk **Dodaj**.  

    5.  Kliknij przycisk **uaktywnienia** obok aplikacji zostały zaimportowane.  

    6.  W **aplikacje Show Offline-Licensed** kreatora, kliknij przycisk **tak** Jeśli chcesz zezwolić offline licencjonowane aplikacje do zakupu.  

4.  Zachęcamy do zakupu co najmniej jednej aplikacji ze Sklepu Windows dla firm.  

5.  W **Administracja** obszaru roboczego w konsoli programu Configuration Manager, rozwiń węzeł **usług w chmurze**, następnie kliknij przycisk **Sklepu Windows dla firm.**  

6.  Na **Home** w karcie **Utwórz** , kliknij przycisk **Dodaj Sklep Windows dla konta firmowego**.  

7.  Dodaj identyfikator dzierżawcy, identyfikatora klienta i klucz klienta z usługi Azure Active Directory, a następnie Ukończ pracę kreatora.  

8.  Gdy wszystko będzie gotowe, zobaczysz konta skonfigurowanego w **Sklep Windows dla konta firmowe** listy w konsoli programu Configuration Manager.  

### <a name="try-it-out"></a>Wypróbuj to!  
 Spróbuj wykonać następujące zadania, a następnie poinformuj nas o tym jak pracy za pomocą naszego formularza opinii na [program Configuration Manager opinii](https://connect.microsoft.com/ConfigurationManagervnext/ConfigMgr%20Customer%20Feedback) w witrynie Microsoft Connect:  

 Tworzenie i wdrażanie aplikacji programu Configuration Manager w Sklepie Windows dla trybu offline licencjonowanego aplikacji biznesowych.  

1.  W **Biblioteka oprogramowania** obszaru roboczego w konsoli programu Configuration Manager, rozwiń węzeł **zarządzania aplikacjami**, następnie kliknij przycisk **informacji o licencji dla aplikacji do sklepu**.  

2.  Wybierz aplikację, którą chcesz wdrożyć, a następnie w **Home** w karcie **Utwórz** , kliknij przycisk **tworzenie aplikacji**.  

 Tworzenia aplikacji programu Configuration Manager zawierający Sklepu Windows dla aplikacji biznesowych. Można następnie wdrażać i monitorować tej aplikacji, jak w przypadku innych aplikacji programu Configuration Manager.  

> [!IMPORTANT]  
>  Podczas tworzenia aplikacji programu Configuration Manager z pojedynczym typem wdrożenia z trybu offline licencjonowanego aplikacji, to można wdrożyć na urządzeniach, które są MDM zarządzane, a także zarządzane przy użyciu klienta programu Configuration Manager. Jeśli zostanie podjęta próba wdrożenia aplikacji z wieloma typami wdrożeń, instalacja nie powiedzie się.  
>   
>  Obecnie nie można wdrożyć online licencjonowane aplikacje za pomocą programu Configuration Manager.  

##  <a name="BKMK_VPP2"></a>Ulepszenia ogólne zakupione woluminu aplikacji  

-   W tej wersji, zakupione woluminu aplikacje ze Sklepu Windows dla firm i aplikacji systemu iOS magazynu zostały skonsolidowane w jednym widoku **dla aplikacji do przechowywania informacji o licencji**.  

-   Aplikacje dla systemu iOS kupionymi woluminu, karta programu zakupów firmy Apple wolumin został usunięty z **pakiet aplikacji dla przeglądarki systemu iOS** okno dialogowe, w kreatorze tworzenia aplikacji. Aby utworzyć aplikację zakupione woluminu dla systemu iOS, wykonaj następujące kroki:  

    1.  1.  W **Biblioteka oprogramowania** obszaru roboczego w konsoli programu Configuration Manager, rozwiń węzeł **zarządzania aplikacjami**, następnie kliknij przycisk **informacji o licencji dla aplikacji do sklepu**.  

    2.  2.  Wybierz aplikację, którą chcesz wdrożyć, a następnie w **Home** w karcie **Utwórz** , kliknij przycisk **tworzenie aplikacji**.  

-   Lokalizacja get i przekaż token VPP firmy Apple dla zakupionych woluminu aplikacji w konsoli programu Configuration Manager za pomocą została zmieniona. Teraz można to zrobić w **Admin** obszaru roboczego w **usług w chmurze** > **tokenów Program firmy Apple woluminu zakupu** węzła.  

##  <a name="BKMK_VPP"></a>Ochrona danych przedsiębiorstwa (EDP)  
 Można utworzyć elementy konfiguracji, które umożliwiają wdrażanie zasad ochrony (EDP) danych przedsiębiorstwa, tym, co pozwala wybrać chronionego aplikacji, poziom ochrony EDP i jak znaleźć dane przedsiębiorstwa w sieci. Aby uzyskać więcej informacji na temat EDP zobacz następujące tematy:  

-   [Ochrona danych przedsiębiorstwa przy użyciu ochrony danych przedsiębiorstwa (EDP)](https://technet.microsoft.com/itpro/windows/keep-secure/protect-enterprise-data-using-edp)  

-   [Tworzenie i wdrażanie zasad ochrony (EDP) danych przedsiębiorstwa za pomocą programu System Center Configuration Manager](https://technet.microsoft.com/itpro/windows/keep-secure/create-edp-policy-using-sccm)  

##  <a name="BKMK_End"></a>Użytkownicy końcowi mogą instalować aplikacje z portalu firmy  
 Lokalnych MDM wprowadzono w System Center Configuration Manager w wersji 1511. W poprzednich wersjach, można wdrożyć aplikacje na urządzeniach zarządzanych MDM systemu Windows 10 z celem wdrożenia **wymagane** zainstalować lokalnie urządzeń zarządzanych MDM dla.  

 W tej wersji mogą obecnie wdrażać aplikacje z celem wdrożenia **dostępne** użytkowników lokalnych MDM komputerów zarządzanych przez system Windows 10, a użytkownicy mogą teraz zainstalować te same aplikacje z portalu firmy.
W tym technical preview Jeśli Portal firmy jest otwarty na więcej niż 15 minut, użytkownik końcowy zostanie wyświetlony komunikat o błędzie. Aby obejść ten problem, uruchom ponownie Portal firmy.  

### <a name="before-you-start"></a>Przed rozpoczęciem  

#### <a name="server-prerequisites"></a>Wymagania wstępne serwera  

-   .NET 4.5 lub nowszy (wymaga ponownego uruchomienia)  

-   Program PowerShell 3.0 skryptu konfiguracji (wymaga ponownego uruchomienia)  

#### <a name="client-prerequisites"></a>Wymagania wstępne klienta  

-   Windows 10 Desktop 1511 (OS kompilacji 10586.218) lub nowszy  

#### <a name="general-prerequisites"></a>Ogólne wymagania wstępne  

-   Upewnij się, zostały ukończone [kroki przygotowania do zarządzania urządzeniami przenośnymi lokalnych](https://technet.microsoft.com/library/mt613153.aspx) i [zarejestrowane urządzenia](https://technet.microsoft.com/library/mt627870.aspx).  

-   Stosowania najlepszych doświadczeń zainstalować przy użyciu portalu firmy, upewnij się, że program Configuration Manager ma aktywne połączenie z programem Microsoft Intune.  

-   Po wybraniu opcji rejestracji zbiorczej, należy skonfigurować koligację urządzenia użytkownika dla urządzeń zarejestrowanych przed podjęciem próby wykonania tego scenariusza.  

### <a name="configuration-steps"></a>Kroki konfiguracji  

#### <a name="install-the-application-catalog-roles-and-enable-mobile-device-management-support"></a>Instalowanie ról katalogu aplikacji i Włącz obsługę zarządzania urządzeniami przenośnymi  

1.  Dodawanie ról usługi sieci Web katalogu aplikacji i witryny sieci Web  

    1.  Wybierz **tryb HTTPS** i **Zezwalaj urządzeniom przenośnym na użycie tego punktu usługi sieci Web katalogu aplikacji** opcji.  

    2.  Ograniczenia w tym Technical Preview:  

        -   Przed wybraniem opcji na urządzeniach przenośnych połączyć, należy odinstalować wszystkie istniejące role katalogu aplikacji.  

        -   Upewnij się, istnieje tylko jeden zestaw ról wykazu aplikacji i role wspólnie znajdują się w systemie lokacji punktu rejestracji i ról punktu Proxy rejestracji.  

2.  Sprawdź, czy działają w węźle stan składnika w konsoli programu Configuration Manager następujące składniki:  

    -   **SMS_AWEBSVC_CONTROL_MANAGER**  

    -   **SMS_DMAPPSVC_CONTROL_MANAGER**  

    -   **SMS_DMCONTENTSVC_CONTROL_MANAGER**  

    -   **SMS_PORTALWEB_CONTROL_MANAGER**  

### <a name="configure-boundaries"></a>Konfigurowanie granic  
 Skonfiguruj wymagane granice intranetowe punktów dystrybucji.  

> [!NOTE]  
>  Tylko IPv4 granice zakresu są obsługiwane w tej chwili do zarządzania urządzeniami przenośnymi.  

### <a name="deploy-the-company-portal-application-and-configuration"></a>Wdrażanie aplikacji portalu firmy i konfiguracji  

1.  Skrypt konfiguracji dołączony technical preview umożliwia przygotowanie wdrożenia portalu firmy i konfiguracji:  

    1.  Otwórz okno polecenia programu PowerShell z podwyższonym poziomem uprawnień.  

    2.  Uruchom **RemoteSigned set-executionPolicy**  

    3.  Z folderu  **&lt;katalog instalacyjny programu SCCM\>\cd.latest\SMSSETUP\TOOLS\MDM** Uruchom **.\ConfigurationScript.ps1**  

     Skrypt konfiguracji wykonuje następujące czynności:  

    1.  Tworzy aplikację programu Configuration Manager z systemu Windows aplikacji pakiet wdrażania typu przy użyciu **CompanyPortalOnPremisesMDM.appx** w tym samym folderze.  

    2.  Tworzy element konfiguracji i linii bazowej konfiguracji, który konfiguruje portalu firmy.  

    3.  Wdraża zarówno linii bazowej konfiguracji, jak i aplikacji, a następnie dodaje aplikację do wszystkich punktów dystrybucji.  

    > [!NOTE]  
    >  Jeśli ról katalogu aplikacji nie znajdują się w lokacji głównej, należy wykonać następujące czynności:  
    >   
    >  -   W **zasoby i zgodność** obszaru roboczego, Znajdź **OnPremMDM Portal konfiguracji CI - adresy URL serwerów** elementu konfiguracji  
    > -   Zmień **reguły zgodności** wartość do w pełni kwalifikowana nazwa domeny systemu lokacji, gdzie znajdują się ról katalogu aplikacji.  

2.  Po wdrożeniu są oba aplikacji portalu firmy i jego konfigurację, sprawdź podstawy aplikacji i konfiguracji są zgodne danego urządzenia za pomocą **wdrożeń** części konsoli programu Configuration Manager. Portal firmy będzie wyświetlany jako **Portal firmy (Technical Preview)** w menu Start na urządzeniu.  

### <a name="try-it-out"></a>Wypróbuj to!  
 Spróbuj wykonać następujące zadania, a następnie poinformuj nas o tym jak pracy za pomocą naszego formularza opinii na [program Configuration Manager opinii](https://connect.microsoft.com/ConfigurationManagervnext/ConfigMgr%20Customer%20Feedback) w witrynie Microsoft Connect:  

1.  Wdrażanie aplikacji kilka z typów obsługiwanych wdrożenia do kolekcji użytkowników z celem wdrożenia **dostępne**. W tym technical preview aplikacje, które wymagają zatwierdzenia administratora nie są obsługiwane i nie będą wyświetlane w portalu firmy.  

2.  Użytkownicy mogą następnie wyszukaj i instalować aplikacje z portalu firmy.  

     Po otwarciu portalu firmy zostanie wyświetlone pole okna dialogowego uwierzytelniania o nazwie **programu System Center Configuration Manager** Określ poświadczenia użytkownika usługi Active Directory (w postaci user@domain lub domena\użytkownik) do logowania.  

##  <a name="BKMK_SW1"></a>Nowe karty aktualizacji i systemów operacyjnych w programie Software Center  
 W tej wersji wprowadzono następujące zmiany poprawianie układu aplikacji programu Software Center:  

-   **Aplikacje** karta została podzielona na trzy oddzielne karty **aktualizacje**, **systemów operacyjnych** (które zarówno wcześniej nie odnaleziono w **filtry** listy), i **aplikacji**.  

##  <a name="BKMK_ServerGroups"></a>Usługa grupy serwerów  
 Technical Preview programu System Center Configuration Manager, wersja 1511, dołączony umożliwia tworzenie kolekcji, gdzie wszystkie urządzenia w kolekcji tworzą grupę serwera. Następnie można skonfigurować ustawienia grupy serwerów do użycia podczas wdrażania aktualizacji oprogramowania do grupy serwerów formantu procent komputerów, które zostały zaktualizowane w danym momencie, i skonfigurować przed wdrożeniem i po wdrożeniu skryptów PowerShell do uruchamiania działań niestandardowych.  

 Technical Preview programu System Center Configuration Manager, wersja 1605, dodaje możliwość aktualizacji komputerów w grupie serwerów w określonej kolejności, zdefiniuj, dodaje monitorowaniu w celu wyświetlania stanu dla komputerów w grupie serwerów i zapewnia możliwość wyczyszczenia blokady wdrażania, który jest przydatne, gdy klienci nie powiodła się instalacja aktualizacji oprogramowania i uniemożliwiają zainstalowanie ich aktualizacje oprogramowania innych klientów.  

### <a name="try-it-out"></a>Wypróbuj to!  
 Spróbuj wykonać następujące zadania, a następnie poinformuj nas o tym jak pracy za pomocą naszego formularza opinii na [program Configuration Manager opinii](https://connect.microsoft.com/ConfigurationManagervnext/ConfigMgr%20Customer%20Feedback) w witrynie Microsoft Connect:  

-   Można utworzyć kolekcję, który reprezentuje grupę serwerów. Dla tego testu można skonfigurować reguł członkostwa zbieranie mieć maszyn 2 w tej kolekcji.   

-   Można określić, że komputery w grupie serwera zainstalować aktualizacje oprogramowania w określonej kolejności, zgodnie z ustawieniami grupy serwera dla kolekcji. Użyj przykładowe skrypty w procedurze, aby określić skrypty przed wdrożeniem i po wdrożeniu.  

-   Można wdrożyć aktualizacji oprogramowania do tej kolekcji. Sprawdź pliki start.txt i end.txt (utworzone na podstawie przykładowe skrypty) w C:\temp oraz godziny rozpoczęcia i zakończenia dla wdrożenia na komputerach w grupie serwerów. Przejrzyj plik UpdatesDeployment.log, aby uzyskać więcej informacji.  

#### <a name="to-create-a-collection-for-a-server-group"></a>Aby utworzyć kolekcję grupy serwerów  

1.  [Utwórz kolekcję urządzeń](https://technet.microsoft.com/library/gg712295.aspx) zawierający komputery w grupie serwera.  

2.  W **zasoby i zgodność** obszaru roboczego, kliknij przycisk **kolekcji urządzeń**, kliknij prawym przyciskiem myszy w kolekcji zawierającej komputery w grupie serwera, a następnie kliknij przycisk **właściwości**.  

3.  Na **ogólne** zaznacz **wszystkie urządzenia są częścią tej samej grupy serwera**, a następnie kliknij przycisk **ustawienia**.  

4.  Na **ustawienia grupy serwerów** Określ jeden z następujących ustawień:  

    -   **Zezwalaj na wartości procentowej maszyn aktualizacji w tym samym czasie**: Określa, że tylko pewien procent klientów są aktualizowane w dowolnym momencie. Jeśli na przykład kolekcja zawiera 10 klientów i kolekcja jest skonfigurowana do aktualizacji 30% klientów w tym samym czasie tylko 3 klientów zainstaluje aktualizacje oprogramowania w danym momencie.  

    -   **Zezwalanie na liczbę maszyn aktualizacji w tym samym czasie**: Określa, że tylko pewna liczba klientów są aktualizowane w dowolnym momencie.  

    -   **Określ sekwencję obsługi**: Określa czy klientów w kolekcji zostanie zaktualizowane pojedynczo w sekwencji, które można skonfigurować. Klient zainstaluje tylko aktualizacje oprogramowania po klienta, który jest przed jej na liście zakończył instalowanie aktualizacji jej oprogramowania.  

5.  Określ, czy skrypt przed wdrożeniem (opróżniania węzła) lub skrypt po wdrożeniu (Wznów węzeł).  

    > [!TIP]  
    >  Poniżej przedstawiono przykłady, że można użyć do testowania wdrożenia przed i po wdrożeniu skrypty, które zapisu bieżący czas do pliku tekstowego:  
    >   
    >  **Przed wdrożeniem**  
    >   
    >  `#Start`  
    >   
    >  `$a = Get-Date`  
    >   
    >  `Write-Output "Universal Time: " + $a.ToUniversalTime()  |`  
    >   
    >  `Out-File C:\temp\start.txt`  
    >   
    >  **Po wdrożeniu**  
    >   
    >  `#End`  
    >   
    >  `$a = Get-Date`  
    >   
    >  `Write-Output "Universal Time: " + $a.ToUniversalTime()  |`  
    >   
    >  `Out-File C:\temp\end.txt`  

#### <a name="to-deploy-software-updates-to-the-server-group-and-monitor-status"></a>Aby wdrożyć aktualizacje oprogramowania do grupy i monitorowanie stanu serwera  

1.  [Wdrażanie aktualizacji oprogramowania](https://technet.microsoft.com/library/gg712304.aspx) kolekcji grupy z serwera.  

2.  [Monitorowanie wdrożenia aktualizacji oprogramowania](https://technet.microsoft.com/library/gg712304.aspx). Oprócz standardowych widoków monitorowania dla wdrożenia aktualizacji oprogramowania nowy opis stanu jest wyświetlana, gdy klient oczekuje na swoją kolej, aby zainstalować aktualizacje oprogramowania. **Oczekiwanie na blokadę** jest wyświetlany dla tego nowego stanu.  

#### <a name="to-clear-the-deployment-locks-for-computers-in-a-server-group"></a>Aby wyczyścić blokady wdrażania dla komputerów w grupie serwerów  

1.  W **zasoby i zgodność** obszaru roboczego, kliknij przycisk **kolekcji urządzeń**i kliknij kolekcję, aby wyczyścić blokady wdrażania.  

2.  Na **Home** w karcie **wdrożenia** , kliknij przycisk **blokuje wdrożenia grupy serwera wyczyść**. Gdy klienci nie powiodła się instalacja aktualizacji oprogramowania i uniemożliwiają zainstalowanie ich aktualizacje oprogramowania innych klientów, blokady wdrażania można ręcznie wyczyścić.  

##  <a name="BKMK_ATP"></a>Obsługa usługi ochrony zaawansowane zagrożenia programu Windows Defender  
 Windows Defender zaawansowane zagrożenia ochrony (ATP) jest nową usługę, która pomoże przedsiębiorstwa do wykrywania, badanie i reagowania na zaawansowane ataki w ich sieciach. Dowiedz się więcej o [Windows Defender ATP](https://blogs.windows.com/windowsexperience/2016/03/01/announcing-windows-defender-advanced-threat-protection). Configuration Manager może pomóc dołączeniu i monitorować zarządzanych urządzeń klienckich systemu Windows 10 rozliczenia Edition.  

### <a name="try-it-now"></a>Wypróbuj teraz!  
 Spróbuj wykonać następujące zadania, a następnie poinformuj nas o tym jak pracy za pomocą naszego formularza opinii na [program Configuration Manager opinii](https://connect.microsoft.com/ConfigurationManagervnext/ConfigMgr%20Customer%20Feedback) w witrynie Microsoft Connect:  

-   Urządzenia zintegrowane z usługą online Windows Defender zaawansowane zagrożenia ochrony (ATP)  

-   Monitoruj wdrożenie systemu Windows Defender ATP do zarządzanych urządzeń  

 **Wymagania wstępne**  

-   Subskrypcja usługi online ochrony zaawansowane zagrożenia programu Windows Defender  

-   Klienci z systemem Windows 10, wydanie rozliczenia (kompilacja 14328 i nowszych)  

-   Tworzenie pliku konfiguracji klienta dołączania  

    ##### <a name="how-to-create-an-onboarding-configuration-file"></a>Jak utworzyć plik konfiguracji dołączania  

    1.  Logowanie do usługi Windows Defender ATP online  

    2.  Kliknij **klienta na pokład** elementu menu  

    3.  Wybierz **programu System Center Configuration Manager** i kliknij przycisk **pakiet**.  

    4.  Pobierz plik archiwum skompresowany (.zip) i Wyodrębnij zawartość.  


##### <a name="onboard-devices-for-windows-defender-atp"></a>Urządzenia zintegrowane dla programu Windows Defender ATP  

1.  W konsoli programu Configuration Manager Przejdź **zasoby i zgodność** > **Przegląd** > **Endpoint Protection** > **Windows Defender ATP zasady** i kliknij przycisk **Utwórz zasady systemu Windows Defender ATP**. Zostanie otwarty Kreator zasad systemu Windows Defender ATP.  

2.  Typ **nazwa** i **opis** dla systemu Windows Defender ATP zasad i wybierz **dołączania**. Kliknij przycisk Dalej.  

3.  **Przeglądaj** do pliku konfiguracji, dostarczone przez dzierżawcy usługi chmury Windows Defender ATP Twojej organizacji. Kliknij przycisk **Dalej**.  

4.  Określ próbki plików, które są zbierane i udostępniane z zarządzanych urządzeń do analizy.  

    -   **Brak** — nie przykładowe pliki nie są zbierane dla analizy  

    -   **Przenośne pliki wykonywalne** — pliki (.exe), pliki łącze biblioteki dynamicznie (dll), pliki czcionek programów plików, takich jak i podobne pliki, które można wykorzystać w cyberattacks są zbierane i udostępnione do analizy  

     Kliknij przycisk **Dalej**.  

5.  Przejrzyj podsumowanie i Zakończ pracę kreatora.  

6.  Teraz można wdrożyć zasady Windows Defender ATP do komputerów klientów zarządzanych przez kliknięcie przycisku **Wdróż**.  

##### <a name="monitor-windows-defender-atp"></a>Monitor systemu Windows Defender ATP  

1.  W konsoli programu Configuration Manager Przejdź **monitorowanie** > **Przegląd** > **zabezpieczeń** , a następnie kliknij przycisk **Windows Defender ATP**.  

2.  Sprawdź pulpit nawigacyjny ochrony zaawansowane zagrożenia programu Windows Defender.  

    -   **Stan wdrożenia agenta programu Windows Defender** — liczba i procent komputerów klientów zarządzanych kwalifikujących się z aktywnego dołączono maszynę wirtualną systemu Windows Defender ATP zasad  

    -   **Kondycja agenta programu Windows Defender ATP** — procent komputerów klienckich raportowania stanu dla ich agenta programu Windows Defender ATP  

        -   **Dobra** -działa prawidłowo  

        -   **Nieaktywne** -żadne dane wysyłane do usługi w okresie  

        -   **Stan agenta** — usługa systemu dla agenta w systemie Windows nie jest uruchomiona  

        -   **Nie został załadowany** - zastosowania zasad, ale agent nie zgłosił dołączeniu zasad  

##  <a name="BKMK_DHA"></a>Poświadczenie zdrowia urządzeń lokalnych  
 Poświadczenie zdrowia dla urządzeń z systemem Windows 10 można teraz skonfigurowane do komunikacji przy użyciu infrastruktury lokalnej. Administratorzy mogą określić, czy raportowania odbywa się za pośrednictwem chmury lub lokalnych zasobów. Zaznaczenie lokalnego do raportowania zaświadczenia kondycji adres URL można określić dla usługi. Dzięki temu komputery klienta bez dostępu do Internetu Włącz urządzeń i zarządzanie nimi za pomocą zaświadczania kondycji.  

### <a name="enable-health-attestation-for-on-premises-devices"></a>Włącz zaświadczania kondycji dla urządzeń lokalnych  
 W 1605 firma Microsoft została ustalona kilka błędy wykryte w 1604 Technical Preview.  Spróbuj go, należy skonfigurować usługi zaświadczania kondycji lokalnie przy użyciu ustawień agenta klienta.  

1.  W konsoli programu Configuration Manager Przejdź **Administracja** > **Przegląd** > **ustawień klienta**, a następnie ustaw **użycia lokalnej usługi kondycji zaświadczania** do **tak**.  

2.  Określ adres w polu **Adres URL lokalnej usługi zaświadczania o kondycji**, a następnie kliknij przycisk **OK**.  

##  <a name="BKMK_RestartOptions"></a>Nowe opcje dla klientów systemu Windows 10 ponownego uruchamiania po zainstalowaniu aktualizacji oprogramowania  
 Gdy aktualizacja oprogramowania wymaga ponownego uruchomienia komputera jest wdrożony za pomocą programu Configuration Manager i zainstalować na komputerze, oczekuje na ponowne uruchomienie zaplanowano i zostanie wyświetlone okno dialogowe ponownego uruchomienia. Obecnie dla systemu Windows 8 i powyżej, jeśli zostanie wyłączony lub ponownie uruchom komputer, używając opcji zasilania systemu Windows (a nie z okna dialogowego ponownego uruchomienia), pozostanie okno dialogowe ponownego uruchomienia po ponownym uruchomieniu komputera i komputer wymaga ponownego uruchomienia po upływie terminu. W tym technical preview opcję **zaktualizować i ponownie uruchom** i **aktualizacji i zamykania** będzie dostępna na komputerach z systemem Windows 10 w Opcje zasilania systemu Windows, gdy istnieje oczekujące ponowne uruchomienie komputera dla aktualizacji oprogramowania programu Configuration Manager. W przypadku skorzystania z dowolnej z tych opcji okno dialogowe ponownego uruchamiania nie zostanie wyświetlone po ponownym uruchomieniu komputera.  

##  <a name="BKMK_IMEI"></a>Wstępnie zadeklarować firmowych urządzeń o numerze seryjnym IMEI lub iOS  
 Można zidentyfikować firmowych urządzeń przez zaimportowanie numerów międzynarodowych stacji urządzeń przenośnych tożsamości (IMEI). Możesz przekazać plik wartości rozdzielanych przecinkami (.csv) zawierający numery IMEI urządzenia lub można ręcznie wprowadzić informacje o urządzeniu.  Można także zaimportować numerów seryjnych urządzeń z systemem iOS.  Zaimportowane informacje spowoduje ustawienie własności urządzeń, które są rejestrowane jako "Firma".  Licencja Intune jest nadal wymagana dla każdego użytkownika uzyskującego dostęp do usługi.  

### <a name="try-it-out"></a>Wypróbuj to!  
 Spróbuj wykonać następujące zadania, a następnie poinformuj nas o tym jak pracy za pomocą naszego formularza opinii na [program Configuration Manager opinii](https://connect.microsoft.com/ConfigurationManagervnext/ConfigMgr%20Customer%20Feedback) w witrynie Microsoft Connect:  

-   Importowanie zbioru liczb IMEI w pliku CSV. Każdy wiersz może zawierać numer IMEI następuje pola szczegółów.  

-   Numery IMEI należy zaimportować ręcznie z konsoli programu Configuration Manager.  

-   Importowanie zestawu iOS numerów seryjnych w pliku CSV. Ponownie każdy wiersz zawiera wiele następuje żadnych szczegółów dla urządzenia.  

##### <a name="pre-declare-corporate-owned-devices-with-imei-or-ios-serial-number"></a>Wstępne deklarowanie urządzeń należących do przedsiębiorstwa przy użyciu numeru IMEI lub numeru seryjnego systemu iOS  

1.  W konsoli programu Configuration Manager Przejdź **zasoby i zgodność** > **Przegląd** > **wszystkie urządzenia należące** > **urządzeń Pre-declared**, a następnie kliknij przycisk **tworzenie urządzeń Pre-declared**. Zostanie otwarty Kreator Pre-declared urządzenia.  

2.  Określ, jak chcesz dodać informacje o urządzeniu:  

    -   **Przekaż plik CSV zawierający numery IMEI i szczegóły** — Aby przekazać listę liczb, zobacz krok 3.  

    -   **Ręcznie Dodaj numery IMEI i szczegóły** — do ręcznie wprowadzić informacje, wpisz numer IMEI lub iOS numery seryjne i szczegóły dla urządzeń, a następnie przejdź do kroku 4.  

3.  Dla przekazane pliki przejdź do pliku CSV zawierającego informacje o wstępnie zadeklarować firmowych urządzeń. Plik musi mieć następujący format, z wyłączeniem górny wiersz (udostępnione tylko do celów informacyjnych):  

    |**KOD IMEI #**|**iOS seryjnych**|**SYSTEM OPERACYJNY**|**Szczegóły**|
    |---|---|---|---|
    |123456789012345||SYSTEMU WINDOWS|Należące do firmy urządzenie z systemem Windows|
    |123456789012|A0BCD0EFGH0J|IOS|Urządzenia z systemem iOS należące do firmy|
    |123456789012346||ANDROID|Należące do firmy urządzeń z systemem Android|

     **Kolumny:**  

    -   Kolumna 1: Kod IMEI — albo IMEI numer lub iOS numer seryjny jest wymagany dla każdego wiersza  

    -   Kolumna 2: numer seryjny iOS — tylko numery seryjne iOS może być wstępnie zadeklarowane. Użyj numeru IMEI dla innych platform urządzeń  

    -   Kolumna 3: System operacyjny urządzenia (wymagane wielkości liter):  

        -   IOS — wszystkie urządzenia z systemem iOS  

        -   System WINDOWS — zawiera Windows Phone, Windows 10 Mobile i komputery z systemem Windows  

        -   ANDROID — wszystkie urządzenia Android  

    -   Kolumna 4: Szczegóły — informacje dodatkowe urządzenia, które pojawiają się w konsoli programu Configuration Manager  

     Kliknij przycisk **Dalej**.  

4.  Przejrzyj wyniki importu pliku. Wcześniej zaimportowanych IMEI lub numery seryjne zostaną ich szczegóły zaktualizowano o nowe szczegółowe informacje.  Kliknij przycisk **dalej** aby kontynuować lub **ponownie** Aby zachować szczegóły zaktualizowane, a następnie Zakończ pracę kreatora.  

