---
title: "Możliwości w Technical Preview 1601 programu Configuration Manager"
description: "Informacje na temat funkcji dostępnych w Technical Preview programu System Center Configuration Manager, wersja 1601."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aae1cf2f-2c04-4f68-a03a-f4a925433c09
caps.latest.revision: 7
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: ef0db5b11ae2be5edcb4db87400c5c273c89972e
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1601-for-system-center-configuration-manager"></a>Możliwości w Technical Preview 1601 System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (Technical Preview)*

Ten artykuł wprowadza do funkcji, które są dostępne w Technical Preview programu System Center Configuration Manager, wersja 1601. Można zainstalować tę wersję, aby zaktualizować i dodawać nowe funkcje do lokacji programu Configuration Manager technical preview.      Przed zainstalowaniem tej wersji technical preview, przejrzyj temat wprowadzające [Technical Preview dla programu System Center Configuration Manager](../../core/get-started/technical-preview.md), aby zapoznać się z ogólnym wymagania i ograniczenia dotyczące używania technical preview, jak zaktualizować między wersjami i jak Wyraź swoją opinię dotyczącą funkcji w technical preview.  

 **Znane problemy dotyczące tej Technical Preview:**  

-   Podczas zarządzania **opcje aktualizacji klientów** do promowania produkcji wstępnej klienta do produkcji, kliencka wersja zero (0) zamiast numeru kompilacji klienta faktycznie wyświetlany tekst dla pola wyboru. Właściwej produkcji wstępnej wersji klienta jest wyświetlana na powierzchni powyżej tej opcji i jest wersja klienta, który zostanie podwyższony do produkcji, po wybraniu tej opcji.  

-   Podczas aktualizacji Technical Preview 1601 i wybierając pozycję testowanie klienta programu Configuration Manager w kolekcji przedprodukcyjnej pakiet klienta dla kolekcji nie zostaną uaktualnione. Ten problem występuje tylko dla Technical Preview 1601.  

     Do rozwiązania problemów z tym wykonaj jedną z wykonaj kroki:  

    -   Uruchom poniższy skrypt SQL w bazie danych lokacji głównej:  

        ```  
        DECLARE @PilotingPkgID NVARCHAR(8)  

        SELECT @PilotingPkgID = PilotingPackageID FROM ClientDeploymentSettings  

        MERGE INTO PkgServers_G AS T  
        USING (  
            SELECT @PilotingPkgID AS PkgID, NALPath, SiteCode, SiteName, SourceSite, RefreshTrigger, UpdateMask, [Action]  
            FROM PkgServers_G WHERE PkgID IN (SELECT UpgradePackageID FROM ClientDeploymentSettings)  
            ) AS S  
        ON T.PkgID = S.PkgID and T.NALPath = S.NALPath  

        WHEN NOT MATCHED THEN  
            INSERT (PkgID, NALPATH, SiteCode, SiteName, SourceSite, LastRefresh, RefreshTrigger, UpdateMask, [Action])  
            VALUES (S.PkgID, S.NALPath, S.SiteCode, S.SiteName, S.SourceSite, GetUTCDate(), S.RefreshTrigger, S.UpdateMask, S.[Action])  
        ;  

        ```  

    -   Dodaj nową rolę systemu lokacji punktu dystrybucji do witryny laboratorium. Nowy punkt dystrybucji spowoduje uaktualnienie kolekcji przedprodukcyjnej przy użyciu nowego pakietu klienta.  

**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  

##  <a name="bkmk_hybrid1"></a>Ulepszenia integracji programu Microsoft Intune  
W 1601 Technical Preview Dodaliśmy obsługę następujących funkcji:  

### <a name="improvements-to-conditional-access"></a>Ulepszenia dostępu warunkowego  

-   **Obsługa dostępu warunkowego dla komputerów, które są zarządzane przez program System Center Configuration Manager**  

     Teraz można ustawić zasady dostępu warunkowego dla komputerów zarządzanych przez System Center Configuration Manager, który będzie wymagać, aby komputery zgodne z zasadami zgodności w celu uzyskiwania dostępu do usług Online programu Exchange i usługi SharePoint Online.  Z tej nowej funkcji należy zarejestrować komputery z usługą Azure AD za pomocą zasad zgodności i monitorowanie i raportowanie o rejestracji usługi Azure AD.  

    > [!NOTE]  
    >  Dostęp warunkowy nie jest jeszcze obsługiwany w systemie Windows 10.  

    Poniżej przedstawiono wymagania wstępne, aby użyć tej funkcji:  

    -   Azure Active Directory Premium subskrypcji i synchronizacji usług AD FS.  

    -   Subskrypcja usługi Microsoft Intune. Subskrypcja usługi Microsoft Intune należy skonfigurować w konsoli programu Configuration Manager.  

    -   [Wymagania wstępne dotyczące usługi Azure AD autorejestrację](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/?rnd=1).  

    Do korzystania z opcji, należy utworzyć zasady zgodności w programie Configuration Manager z określonych zasad opisanych poniżej i ustawić zasady dostępu warunkowego w konsoli usługi Intune.  Ponadto, aby dostęp zgodny tylko z komputerów, musisz ustawić wymóg komputerze z systemem Windows **urządzenia muszą być zgodne** opcji. Poniżej wymieniono zgodne reguły, które mają zastosowanie do komputerów zarządzanych przez program System Center Configuration manager.  

    -   **Wymagaj rejestracji w usłudze Azure ActiveDirectory:** Ta reguła sprawdza, czy urządzenie użytkownika jest dołączony do usługi Azure AD miejscu pracy, a jeśli nie, urządzenie jest automatycznie zarejestrowany w usłudze Azure AD. Automatyczna rejestracja jest obsługiwana tylko w systemie Windows 8.1. W przypadku komputerów z systemem Windows 7 należy wdrożyć instalatora MSI w celu przeprowadzenia rejestracji automatycznej. Aby uzyskać więcej informacji, zobacz [tutaj](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/?rnd=1).  

    -   **Zainstalowano wszystkie wymagane aktualizacje z terminem starsze niż określoną liczbę dni:** Ta reguła sprawdza, czy urządzenie użytkownika ma wszystkie wymagane aktualizacje (określony w **wymagane aktualizacje automatyczne** zasada) w ramach terminu i okres prolongaty określone przez użytkownika i automatycznie zainstalować wszelkie oczekujące aktualizacje.  

    -   **Wymagaj szyfrowania dysków funkcją BitLocker:** Jest to sprawdź, czy dysk podstawowy (np. C:\\) na urządzeniu jest funkcją BitLocker zaszyfrowane. Jeśli szyfrowanie funkcją BitLocker nie jest włączone na głównym urządzeniu, dostęp do poczty e-mail i usług SharePoint jest zablokowany.  

    -   **Wymagaj ochrony przed złośliwym oprogramowaniem:** Jest to sprawdź, czy oprogramowanie ochrony przed złośliwym oprogramowaniem (System Center Endpoint Protection lub Windows Defender) jest włączona i uruchomiona.  
         Jeśli takie oprogramowanie nie jest włączone, dostęp do poczty e-mail i usług SharePoint jest zablokowany.  

    Użytkowników końcowych, którzy są blokowane z powodu niezgodności będą wyświetlać informacje o zgodności w Centrum oprogramowania SCCM i będzie inicjował nowej oceny zasad, gdy są rozwiązywane problemy ze zgodnością.  

-   **Dostępu warunkowego w usłudze kondycji zaświadczania** teraz można ograniczyć dostęp do poczty e-mail i usług 0365 na podstawie kondycji urządzeń zgłoszony przez usługę kondycji zaświadczania.  Ponadto urządzenia, które są zarządzane przez usługę Intune są ujęte w raportach kondycji urządzenia.  

    Nowe zasady zgodności dodano do konsoli programu configuration manager, który pozwala na określenie, czy urządzenia powinno być dozwolone lub zablokowane dostępu na podstawie ich stanu kondycji.  Aby utworzyć tę regułę, otwórz **Kreatora tworzenia zasad zgodności**i Dodaj nową regułę.  Wybierz **zgłaszane przez usługę Health zaświadczania kondycji** warunku i ustaw wartość na **True**.  Spowoduje to upewnij się, że tylko urządzeń, które są zgłaszane w dobrej kondycji będzie miał dostęp do zasobów firmy. Szczegółowe informacje o kondycji usługi zaświadczania i jak kondycji urządzeń jest zgłaszany w usłudze Intune, zobacz [zaświadczania kondycji urządzenia](#bkmk_devicehealth).  

-   **Nowe ustawienia zasad zgodności:** Nowe ustawienia zasad zgodności poprawić bezpieczeństwo i ochrona na urządzeniach, które umożliwiają dostęp do firmowej poczty e-mail i usług programu SharePoint:  

    -   **Wymagaj automatycznych aktualizacji:** Urządzenia z Windows 8.1 lub nowszym może wymagać Zezwalaj na automatyczne instalowanie aktualizacji, a także określ klasy aktualizacji, które są zainstalowane.  Albo użytkownik może: Zainstaluj tylko aktualizacje oznaczone jako ważne lub zainstaluj wszystkie zalecane aktualizacje.  

         Aby utworzyć regułę aktualizacje automatyczne, otwórz **Kreatora tworzenia zasad zgodności**i Dodaj nową regułę.  Wybierz **minimalna Klasyfikacja aktualizacji wymagane** jako warunek i ustawia wartość do jednej z dostępnych wartości: **Brak**, **zalecane**, i **ważne**.  

        -   **Brak:** Aktualizacje nie są instalowane automatycznie.  

        -   **Zalecane:** Wszystkie zalecane aktualizacje są instalowane.  

        -   **Ważne:** Są instalowane tylko aktualizacje sklasyfikowane jako ważne.  

    -   **Wymagaj hasła do odblokowania urządzeń przenośnych:** Gdy to ustawienie ma wartość **tak**, użytkownicy końcowi musi wprowadzić hasło, aby umożliwić dostęp do swoich urządzeń.  

         Aby utworzyć regułę dla hasła do odblokowania urządzeń przenośnych, otwórz **Kreatora tworzenia zasad zgodności**i Dodaj nową regułę. Wybierz **Wymagaj hasła do odblokowania bezczynności urządzenia** jako warunku i ustaw wartość na **True**.  

    -   **Liczba minut braku aktywności, zanim będzie wymagane hasło:**  Określa czas bezczynności, po którym użytkownik musi wprowadzić ponownie swoje hasło.  

         Aby utworzyć tę regułę, otwórz **Kreatora tworzenia zasad zgodności**i Dodaj nową regułę. **Wybierz liczba minut braku aktywności, zanim będzie wymagane hasło** jako warunek i ustaw wartość na jedną z dostępnych opcji: 1 minutę, 5 minut, 15 minut, 30 minut I godzinę.  

-   **Domyślna reguła zastąpienie — zawsze Zezwalaj zarejestrowane w usłudze Intune i urządzeń zgodnych z dostępu do lokalnego programu Exchange:**  

     Po zaznaczeniu tej opcji urządzenia, które są zarejestrowane w usłudze Intune i są zgodne z zasadami zgodności mogą uzyskać dostęp do lokalnego programu Exchange. Ta zasada zastępuje domyślne reguły, co oznacza, że nawet jeśli wartość domyślna zasada kwarantannę i blokowania dostępu zarejestrowane i urządzeń zgodnych nadal będą mogli uzyskać dostęp do lokalnego programu Exchange.  
     Użyj tego ustawienia, należy zarejestrować i urządzeń zgodnych zawsze ma dostęp do poczty e-mail za pośrednictwem lokalnego programu Exchange.  

     To jest obsługiwany na następujących platformach:  Windows Phone 8 i nowsze, iOS 6 i nowsze. Android 4.0 i nowsze, Samsung KNOX Standard 4.0 i nowszych.  

     Aby użyć tej opcji, przejdź do **ogólne** strony **skonfigurować kreatora zasady dostępu warunkowego** dla lokalnego programu Exchange.  

##  <a name="bkmk_clientStatus"></a>Stan online klienta  
Począwszy od technical preview 1601 można rozpoznać na pierwszy rzut oka czy klient jest online lub offline w konsoli programu Configuration Manager. Zaktualizowano ikonami i kolumn w konsoli listy urządzeń można ocenić stan klientów w środowisku do identyfikowania problemów oraz innych problemów, które mogą wymagać Twojej uwagi.  

Klient jest w trybie online, jeśli jest aktualnie połączona Rola systemu lokacji punktu zarządzania programu Configuration Manager. Tak długo, jak punkt zarządzania odbiera komunikaty ping podobne od klienta, jego stan jest w trybie online. Po 5 minut lub w celu zarządzania nie pojawi się komunikat, stan klienta zmieni się do trybu offline.  

### <a name="icons-for-client-status"></a>Ikony dla stanu klienta  

|||  
|-|-|  
|![ikona stanu online dla klientów](media/online-status-icon.png)|Klient jest w trybie online.|  
|![ikona stanu offline dla klientów](media/offline-status-icon.png)|Klient jest w trybie offline.|  
|![ikona nieznanego stanu dla klientów](media/unknown-status-icon.png)|Stan klienta jest nieznany.|  

### <a name="prerequisites"></a>Wymagania wstępne  
 Stan online klienta nie ma wymagań wstępnych. Można uruchomić przy użyciu go natychmiast po zainstalowaniu programu Configuration Manager technical preview 1601.  

### <a name="limitations"></a>Ograniczenia  
 Stan online klienta jest dostępna tylko dla komputerów z systemem Windows z zainstalowanym klientem programu Configuration Manager. Stan online klienta nie jest obsługiwana dla komputerów Mac, Linux lub UNIX komputera lub urządzenia zarządzane za pomocą na\-lokalnych zarządzanie urządzeniami przenośnymi.  

### <a name="to-view-client-online-status"></a>Aby wyświetlić stan online klienta  

1.  W konsoli programu Configuration Manager, przejdź do **zasoby i zgodność > Przegląd > urządzenia**.  

2.  Kliknij prawym przyciskiem myszy nagłówek kolumny, a następnie kliknij jedno z pól stanu online klientów ją dodać do widoku urządzeń. Pola są  

    -   **Stan online urządzenia** wskazuje, czy klient jest obecnie w trybie online, czy offline.  

    -   **Ostatni czas w trybie Online** wskazuje klienta online zmiany stanu z trybu offline do trybu online.  

    -   **Ostatni czas Offline** wskazuje zmiany stanu z trybu online i offline.  

 Aby wyświetlić ostatnie zmiany stanu klienta, Odśwież konsolę.  

##  <a name="bkmk_appmgmt1601"></a>Ulepszenia dotyczące zarządzania aplikacjami  
 W podglądzie techniczne 1601 Dodaliśmy obsługę następujących funkcji:  

### <a name="manage-volume-purchased-apps-for-ios-devices"></a>Zarządzanie zbiorczo zakupionymi aplikacjami dla urządzeń z systemem iOS  
 Niektóre sklepów dają możliwość zakupu licencji wielu aplikacji, które mają być uruchamiane w firmie. Dzięki temu można zmniejszyć koszty administracyjne śledzenia wielu zakupionych kopii aplikacji.  

 Program Configuration Manager pomaga teraz zarządzać aplikacjami, które zakupione w ramach takich programów importowanie informacji o licencji ze sklepu z aplikacjami i śledzenia, ile licencji jest używany.  

 Aby uzyskać szczegółowe informacje, zobacz [zarządzania aplikacjami zakupione w ramach programu zakupów woluminu z programu Configuration Manager](https://technet.microsoft.com/library/mt627954.aspx).  

### <a name="ios---app-configuration-for-applicationsbr-hybrid"></a>iOS - Konfiguracja aplikacji dla aplikacji<br />Hybrydowe  
 Niektóre aplikacje iOS obsługują wstępnie skonfigurowane ustawienia, takie jak serwer lub baza danych, z którą aplikacja powinna się połączyć. Program Configuration Manager obsługuje teraz wdrażanie aplikacji zasad konfiguracji do urządzenia, które umożliwiają użytkownikowi natychmiast korzystać z aplikacji bez potrzeby informacje te. Deweloperzy należy włączyć tę funkcję w swoich aplikacjach.  

 Ograniczoną liczbę publicznie wydanej aplikacji obsługuje obecnie wstępne konfigurowanie ustawień; Użytkownik może również we własnym zakresie opracowali aplikacje biznesowe, które je obsługują.  

#### <a name="prerequisites-for-this-scenario"></a>Wymagania wstępne dotyczące tego scenariusza  

-   Dodać subskrypcję Microsoft Intune do programu Configuration Manager.  

-   Certyfikat Apple APNs musi zostały dodane do subskrypcji usługi Intune.  

-   IOS aplikacji, która obsługuje konfigurację aplikacji musi być wdrożona.  

#### <a name="try-it-out"></a>Wypróbuj to!  
 Gdy powyższe wymagania wstępne są spełnione, należy utworzyć używający iOS typu wdrożenia aplikacji programu Configuration Manager. Aplikacji, którego używasz musi obsługiwać konfiguracji aplikacji. Zajrzyj do dokumentacji dostawcy aplikacji, aby dowiedzieć się, jakie określone elementy (pary nazwa/wartość), można skonfigurować.  

 Następnie należy skojarzyć zasady konfiguracji aplikacji z typu wdrożenia iOS podczas wdrażania aplikacji. Można także wdrożyć zasady z **zasady konfiguracji aplikacji** węzła przeznaczone do istniejącej aplikacji i kolekcji.  

 Spróbuj wykonać następujące zadania, a następnie przekaż nam jak pracy za pomocą informacji opinii w górnej części tego tematu:  

-   Jeśli masz aplikację iOS, która obsługuje konfigurację aplikacji, zapoznaj się dokumentacją dostawcy aplikacji aby dowiedzieć się, pary nazw i wartości, należy określić, aby skonfigurować aplikację.  

-   Uruchom **Tworzenie zasad konfiguracji aplikacji** kreatora. Na **zasad systemu iOS** kreatora, spróbuj Dodawanie pary nazw i wartości znalezionych w dokumentacji dostarczonej przez dostawcę aplikacji albo można zaimportować plik XML zawierający wymagane wartości.  

-   W **wdrażania oprogramowania** kreatora na **zasady konfiguracji aplikacji** pozycję skojarzyć zasady konfiguracji aplikacji utworzonych przy użyciu typu wdrożenia zgodny z aplikacji.  

##  <a name="bkmk_compliance1601"></a>Ulepszenia dotyczące ustawień zgodności  
 W podglądzie techniczne 1601 Dodaliśmy obsługę następujących funkcji:  

### <a name="microsoft-edge-browser-settings"></a>Ustawienia przeglądarki Microsoft Edge  
 Dodano nowe ustawienia przeglądarki Microsoft Edge **Windows 8.1 i Windows 10** elementu konfiguracji (ustawienia dotyczą tylko urządzenia z systemem Windows 10).  

 Aby zobaczyć nowe ustawienia, wybierz opcję **Microsoft Edge** z elementu konfiguracji **ustawienia urządzenia** strony **utworzyć element konfiguracji** kreatora.  

 Aby uzyskać więcej informacji, zobacz [tworzenie elementów konfiguracji dla urządzeń Windows 8.1 i Windows 10 zarządzane bez klienta programu System Center Configuration Manager](../../compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md).  

### <a name="compliance-settings-for-windows-10-team-devices"></a>Ustawienia zgodności dla urządzeń z systemem Windows 10 Team  
 Te nowe ustawienia zgodności umożliwiają konfigurowanie urządzeń z systemem Windows 10 zespołu, takie jak urządzenia Centrum powierzchni.  

 Aby zobaczyć nowe ustawienia, wybierz opcję **systemu Windows 10 Team** z elementu konfiguracji **ustawienia urządzenia** strony **utworzyć element konfiguracji** kreatora.  

 Aby uzyskać więcej informacji, zobacz [tworzenie elementów konfiguracji dla urządzeń Windows 8.1 i Windows 10 zarządzane bez klienta programu System Center Configuration Manager](../../compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md).  

### <a name="android---kiosk-mode-for-samsung-knox-standardbr-hybrid"></a>Android — tryb kiosku dla Samsung KNOX Standard<br />Hybrydowe  
 Tryb kiosku umożliwia blokowanie urządzenia w celu zezwolenia tylko określonych funkcji. Na przykład można zezwolić na uruchamianie na urządzeniu tylko określonej zarządzanej aplikacji albo można wyłączyć przyciski regulacji głośności na urządzeniu. Można użyć tych ustawień dla modeli pokazowych urządzenia lub dla urządzeń przeznaczonych do wykonywania tylko jednej funkcji — na przykład urządzeń w punkcie sprzedaży. Te ustawienia nie są dostępne dla urządzeń Samsung KNOX Standard w **Windows 8.1 i Windows 10** elementu konfiguracji (ustawienia dotyczą tylko urządzenia z systemem Windows 10).  

 Aby zobaczyć nowe ustawienia, wybierz opcję **tryb kiosku - Samsung KNOX** z elementu konfiguracji **ustawienia urządzenia** strony **utworzyć element konfiguracji** kreatora.  

 Aby uzyskać więcej informacji, zobacz [tworzenie elementów konfiguracji dla urządzeń Windows 8.1 i Windows 10 zarządzane bez klienta programu System Center Configuration Manager](../../compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md).  

