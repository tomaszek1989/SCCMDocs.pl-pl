---
title: Funkcje w wersji zapoznawczej Technical Preview 1601
titleSuffix: Configuration Manager
description: "Dowiedz się więcej o funkcjach dostępnych w wersji zapoznawczej Technical Preview programu System Center Configuration Manager, wersja 1601."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: aae1cf2f-2c04-4f68-a03a-f4a925433c09
caps.latest.revision: "7"
author: erikje
ms.author: erikje
manager: angrobe
robots: noindex,nofollow
ms.openlocfilehash: 70efb483ac15ba14497b884ed753032e8e48a4b5
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2017
---
# <a name="capabilities-in-technical-preview-1601-for-system-center-configuration-manager"></a>Funkcje w wersji Technical Preview 1601 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*

W tym artykule przedstawiono funkcje, które są dostępne w wersji Technical Preview programu System Center Configuration Manager, wersja 1601. Można zainstalować tę wersję, aby zaktualizować i dodać nowe funkcje do lokacji programu Configuration Manager technical preview.      Przed zainstalowaniem tej wersji technical Preview, przejrzyj temat wprowadzający [Technical Preview programu System Center Configuration Manager](../../core/get-started/technical-preview.md), aby zapoznać się z ogólne wymagania i ograniczenia dotyczące używania wersji technical preview, jak zaktualizować między wersjami i sposobu wyrazić swoją opinię na temat funkcji w wersji technical preview.  

 **Znane problemy dotyczące tej wersji Technical Preview:**  

-   Jeśli zarządzasz **opcje aktualizacji klienta** promowanie klienta przedprodukcyjnego do środowiska produkcyjnego, tekst pola wyboru Wyświetla wersję klienta zero (0) zamiast rzeczywistego numeru kompilacji klienta. Właściwej produkcji wstępnej wersji klienta jest wyświetlana powyżej tej opcji, a to wersja klienta jest podwyższany do środowiska produkcyjnego, po wybraniu tej opcji.  

-   Podczas aktualizacji do wersji Technical Preview 1601 i wybrania opcji testowania klienta programu Configuration Manager w kolekcji przedprodukcyjnej pakiet klienta dla kolekcji nie można uaktualnić. Ten problem występuje tylko dla wersji Technical Preview 1601.  

     Aby rozwiązać ten problem wykonaj jedną z wykonaj:  

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

    -   Dodaj nową rolę systemu lokacji punktu dystrybucji do lokacji laboratorium. Nowy punkt dystrybucji uaktualni kolekcji przedprodukcyjnej przy użyciu nowego pakietu klienta.  

**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  

##  <a name="bkmk_hybrid1"></a>Ulepszenia integracji programu Microsoft Intune  
W 1601 Technical Preview dodano obsługę następujących funkcji:  

### <a name="improvements-to-conditional-access"></a>Ulepszenia dostępu warunkowego  

-   **Obsługa dostępu warunkowego dla komputerów, które są zarządzane przez program System Center Configuration Manager**  

     Można teraz ustawić zasady dostępu warunkowego dla komputerów zarządzanych przez System Center Configuration Manager, który będzie wymagać, aby komputery się zgodne z zasadami zgodności, aby uzyskać dostęp do usługi Exchange Online i SharePoint Online.  Dzięki tej nowej funkcji można również zarejestrować komputery z usługą Azure AD za pomocą zasad zgodności oraz monitorowania i raportowania rejestrację usługi Azure AD.  

    > [!NOTE]  
    >  Dostęp warunkowy nie jest jeszcze obsługiwana w systemie Windows 10.  

    Poniżej podano wymagania wstępne, aby użyć tej funkcji:  

    -   Azure Active Directory Premium subskrypcji i ADFS Sync.  

    -   Subskrypcja usługi Microsoft Intune. Subskrypcja usługi Microsoft Intune należy skonfigurować w konsoli programu Configuration Manager.  

    -   [Wymagania wstępne dotyczące rejestracji automatycznej usługi Azure AD](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/?rnd=1).  

    Aby użyć opcji, należy utworzyć zasady zgodności w programie Configuration Manager za pomocą określonych reguł opisanych poniżej i ustawić zasady dostępu warunkowego w konsoli usługi Intune.  Ponadto aby upewnić się, mogą uzyskiwać dostęp tylko dla zgodnych komputerów, należy ustawić wymaganie na komputerze z systemem Windows **urządzenia muszą być zgodne** opcji. Poniżej przedstawiono reguły zasad zgodności, które mają zastosowanie do komputerów zarządzanych przez program System Center Configuration manager.  

    -   **Wymagaj rejestracji w usłudze Azure ActiveDirectory:** Ta reguła sprawdza, czy urządzenie użytkownika miejscu pracy zostało dołączone do usługi Azure AD, a jeśli nie, urządzenie jest automatycznie rejestrowane w usłudze Azure AD. Automatyczna rejestracja jest obsługiwana tylko w systemie Windows 8.1. W przypadku komputerów z systemem Windows 7 należy wdrożyć instalatora MSI w celu przeprowadzenia rejestracji automatycznej. Aby uzyskać więcej informacji, zobacz [tutaj](https://azure.microsoft.com/en-us/documentation/articles/active-directory-conditional-access-automatic-device-registration/?rnd=1).  

    -   **Zainstalowano wszystkie wymagane aktualizacje z ostatecznym terminem przypadającym wcześniej niż określona liczba dni temu:** Ta reguła sprawdza, czy urządzenie użytkownika ma wszystkie wymagane aktualizacje (określone w **wymagane aktualizacje automatyczne** reguły) w ramach terminu ostatecznego i okresu prolongaty określonego przez użytkownika i automatycznie instaluje wszystkie oczekujące wymagane aktualizacje.  

    -   **Wymagaj szyfrowania dysków funkcją BitLocker:** Jest to sprawdzenie, czy dysk podstawowy (np. C:\\) na urządzeniu jest funkcją BitLocker zaszyfrowany. Jeśli szyfrowanie funkcją BitLocker nie jest włączone na głównym urządzeniu, dostęp do poczty e-mail i usług SharePoint jest zablokowany.  

    -   **Wymagaj ochrony przed złośliwym oprogramowaniem:** Jest to sprawdzenie, czy oprogramowanie chroniące przed złośliwym kodem (System Center Endpoint Protection lub usługa Windows Defender) jest włączona i uruchomiona.  
         Jeśli takie oprogramowanie nie jest włączone, dostęp do poczty e-mail i usług SharePoint jest zablokowany.  

    Użytkownicy końcowi, którzy są zablokowane z powodu niezgodności zostaną wyświetlone informacje o zgodności w Centrum oprogramowania SCCM i zostanie zainicjowana nowa ocena zasad, gdy problemy ze zgodnością zostaną rozwiązane.  

-   **Dostęp warunkowy i usługa zaświadczania o kondycji** teraz możesz ograniczyć dostęp do poczty e-mail i usług 0365 na podstawie kondycji urządzeń zgłoszonej przez usługę zaświadczania o kondycji.  Ponadto urządzenia zarządzane przez usługę Intune są ujęte w raportach o kondycji urządzeń.  

    Do konsoli programu configuration manager, który służy do określenia, czy urządzeniu powinno być dozwolone, czy zablokowała dostęp na podstawie stanu kondycji została dodana nowa reguła zgodności.  Aby utworzyć tę regułę, otwórz **Kreatora tworzenia zasad zgodności**i Dodaj nową regułę.  Wybierz **zgłoszone jako kondycji przez usługę zaświadczania o kondycji** dla warunku i ustaw wartość **True**.  Spowoduje to upewnij się, że tylko urządzenia zgłoszone jako poprawne będą mieli dostęp do zasobów firmy. Aby uzyskać szczegółowe informacje o usłudze zaświadczania o kondycji i sposobie zgłaszania kondycji urządzeń w usłudze Intune, zobacz [zaświadczania o kondycji](#bkmk_devicehealth).  

-   **Nowe ustawienia zasad zgodności:** Nowe ustawienia zasad zgodności zwiększyć bezpieczeństwo i ochrona na urządzeniach, które są używane do dostępu do firmowej poczty e-mail i usług programu SharePoint:  

    -   **Wymagaj aktualizacji automatycznych:** Urządzenia z Windows 8.1 lub nowszym można wymagać, aby zezwalały na automatyczne instalowanie aktualizacji, a także określić klasę aktualizacji, które są zainstalowane.  Użytkownik może wybrać: instalowane tylko aktualizacje oznaczone jako ważne lub wszystkie zalecane aktualizacje.  

         Aby utworzyć regułę dla aktualizacji automatycznych, otwórz **Kreatora tworzenia zasad zgodności**i Dodaj nową regułę.  Wybierz **minimalna Klasyfikacja wymaganych aktualizacji** jako warunek i ustaw wartość na jedną z dostępnych wartości: **Brak**, **zalecane**, i **ważne**.  

        -   **Brak:** Aktualizacje nie są instalowane automatycznie.  

        -   **Zalecane:** Wszystkie zalecane aktualizacje są instalowane.  

        -   **Ważne:** Instalowane są tylko aktualizacje sklasyfikowane jako ważne.  

    -   **Wymagaj hasła do odblokowania urządzeń przenośnych:** Jeśli to ustawienie jest równa **tak**, użytkownicy końcowi muszą wprowadzić hasło przed uzyskaniem dostępu do swoich urządzeń.  

         Aby utworzyć regułę dla hasła do odblokowania urządzeń przenośnych, otwórz **Kreatora tworzenia zasad zgodności**i Dodaj nową regułę. Wybierz **Wymagaj hasła do odblokowania bezczynnego urządzenia** jako warunek i ustaw wartość **True**.  

    -   **Liczba minut braku aktywności, zanim będzie wymagane hasło:**  Określa czas bezczynności, po którym użytkownik musi wprowadzić ponownie swoje hasło.  

         Aby utworzyć tę regułę, otwórz **Kreatora tworzenia zasad zgodności**i Dodaj nową regułę. **Wybierz liczba minut braku aktywności, zanim będzie wymagane hasło** jako warunek i ustaw dla niego jedną z dostępnych opcji: 1 minutę, 5 minut, 15 minut, 30 minut I godzinę.  

-   **Przesłonięcie reguły domyślnej — zawsze Zezwalaj urządzeniom zgodnym i zarejestrowanym w usłudze Intune w celu uzyskania dostępu do lokalnego programu Exchange:**  

     Po zaznaczeniu tej opcji urządzenia zarejestrowane w usłudze Intune i zgodne z zasadami zgodności mogą uzyskać dostęp do lokalnego programu Exchange. Ta reguła zastępuje regułę domyślną, co oznacza, że nawet w przypadku ustawienia reguły domyślnej na kwarantannę lub blokowanie dostępu, zarejestrowane i zgodne urządzenia nadal będzie można uzyskać dostęp do lokalnego programu Exchange.  
     Użyj tego ustawienia, aby zarejestrowane i zgodne urządzenia zawsze miały dostęp do poczty e-mail za pośrednictwem lokalnego programu Exchange.  

     Jest to obsługiwane na następujących platformach:  Windows Phone 8 i nowsze, iOS 6 i nowsze. System android 4.0 i nowsze, Samsung KNOX Standard 4.0 lub nowszy.  

     Aby użyć tej opcji, przejdź do **ogólne** strony **warunkowego Kreatora konfiguracji zasad dostępu** dla lokalnego programu Exchange.  

##  <a name="bkmk_clientStatus"></a>Stan online klienta  
Począwszy od wersji zapoznawczej technical preview 1601, można określić jeden rzut oka czy klient jest w trybie online lub offline w konsoli programu Configuration Manager. Dzięki zaktualizowanym ikonom i kolumn w liście urządzeń konsoli można ocenić stan klientów w środowisku w celu zidentyfikowania obszarów problemów oraz innych problemów, które mogą wymagać Twojej uwagi.  

Klient jest w trybie online, jeśli jest on aktualnie połączony z rolą systemu lokacji punktu zarządzania Configuration Manager. Tak długo, jak punkt zarządzania odbiera komunikaty typu ping od klienta, jest w stanie online. Jeśli punkt zarządzania nie odbierze komunikatu do 5 minut, stan klienta zmieni się na offline.  

### <a name="icons-for-client-status"></a>Ikony stanu klienta  

|||  
|-|-|  
|![ikona stanu online dla klientów](media/online-status-icon.png)|Klient jest w trybie online.|  
|![ikona stanu offline dla klientów](media/offline-status-icon.png)|Klient jest w trybie offline.|  
|![ikona nieznanego stanu dla klientów](media/unknown-status-icon.png)|Stan klienta jest nieznany.|  

### <a name="prerequisites"></a>Wymagania wstępne  
 Stan online klienta nie ma wymagań wstępnych. Możesz rozpocząć korzystanie z niej natychmiast po zainstalowaniu programu Configuration Manager technical preview 1601.  

### <a name="limitations"></a>Ograniczenia  
 Stan online klienta jest dostępna dla komputerów z systemem Windows tylko z zainstalowanym klientem programu Configuration Manager. Stan online klienta nie jest obsługiwana dla komputerów Mac, Linux lub UNIX komputera lub urządzeń zarządzanych za pomocą na\-lokalnych zarządzanie urządzeniami przenośnymi.  

### <a name="to-view-client-online-status"></a>Aby wyświetlić stan online klienta  

1.  W konsoli programu Configuration Manager, przejdź do **zasoby i zgodność > Przegląd > urządzenia**.  

2.  Kliknij prawym przyciskiem myszy nagłówek kolumny, a następnie kliknij jedno z pól stanu online klienta, aby dodać go do widoku urządzeń. Pola są  

    -   **Stan online urządzenia** wskazuje, czy klient jest obecnie w trybie online, czy offline.  

    -   **Godzina ostatniej obecności Online** wskazuje, kiedy stan online klienta zmienił z trybu offline do trybu online.  

    -   **Godzina ostatniej obecności Offline** wskazuje zmiany stanu z trybu online do trybu offline.  

 Aby wyświetlić ostatnie zmiany stanu klienta, Odśwież konsolę.  

##  <a name="bkmk_appmgmt1601"></a>Ulepszenia dotyczące zarządzania aplikacjami  
 W wersji zapoznawczej Technical Preview 1601 dodano obsługę następujących funkcji:  

### <a name="manage-volume-purchased-apps-for-ios-devices"></a>Zarządzanie zbiorczo zakupionymi aplikacjami dla urządzeń z systemem iOS  
 Niektóre sklepy z aplikacjami umożliwiają zakup wielu licencji dla aplikacji, które mają być uruchamiane w firmie możliwości. Dzięki temu można zmniejszyć koszty administracyjne śledzenia wielu zakupionych kopii aplikacji.  

 Menedżer konfiguracji ułatwia teraz Zarządzanie aplikacjami zakupionymi za pośrednictwem takiego programu przez zaimportowanie informacji o licencji ze sklepu z aplikacjami i śledzenie, ile licencji jest używanych.  

 Aby uzyskać więcej informacji, zobacz [Zarządzanie aplikacjami zakupionymi za pośrednictwem programu zakupów zbiorczych z programem Configuration Manager](https://technet.microsoft.com/library/mt627954.aspx).  

### <a name="ios---app-configuration-for-applicationsbr-hybrid"></a>iOS — Konfiguracja aplikacji dla aplikacji<br />Hybrydowe  
 Niektóre aplikacje iOS obsługują wstępnie skonfigurowane ustawienia, takie jak serwer lub baza danych, z którą aplikacja powinna się połączyć. Program Configuration Manager obsługuje teraz wdrażanie zasad konfiguracji aplikacji na urządzeniu, które umożliwiają użytkownikowi natychmiastowe korzystanie z aplikacji bez konieczności się z następującymi informacjami. Deweloperzy muszą włączyć tę funkcję w swoich aplikacjach.  

 Ograniczona liczba publicznie wydanych aplikacji obsługuje obecnie wstępne skonfigurowanie ustawienia; może również we własnym zakresie zdobyciu aplikacje biznesowe, które je obsługują.  

#### <a name="prerequisites-for-this-scenario"></a>Wymagania wstępne dotyczące tego scenariusza  

-   Należy dodać subskrypcję Microsoft Intune do programu Configuration Manager.  

-   Należy dodać poprawny certyfikat usługi APNs firmy Apple do subskrypcji usługi Intune.  

-   Należy wdrożyć aplikację systemu iOS, która obsługuje konfigurację aplikacji.  

#### <a name="try-it-out"></a>Wypróbuj  
 Gdy powyższe wymagania wstępne są spełnione, należy utworzyć aplikację programu Configuration Manager, która używa typu wdrożenia iOS. Aplikację, której używasz musi obsługiwać funkcję konfiguracji aplikacji. Zapoznaj się z dokumentacją dostawcy aplikacji, aby dowiedzieć się, jakie określone elementy (pary nazwa/wartość), można skonfigurować.  

 Następnie należy skojarzyć zasady konfiguracji aplikacji z typem wdrożenia iOS podczas wdrażania aplikacji. Można także wdrożyć zasady z **zasady konfiguracji aplikacji** węzła, przeznaczone dla istniejącej aplikacji i kolekcji.  

 Spróbuj wykonać następujące zadania, a następnie użyj formularza opinii u góry tego tematu, aby poinformować nas, jak Ci poszło:  

-   Jeśli masz aplikację iOS, która obsługuje konfigurację aplikacji, zapoznaj się z dokumentacją dostawcy aplikacji, aby dowiedzieć się, pary nazw i wartości, należy określić w celu skonfigurowania aplikacji.  

-   Uruchom **Tworzenie zasad konfiguracji aplikacji** kreatora. Na **zasady systemu iOS** kreatora spróbuj dodać pary nazw i wartości znalezione w dokumentacji dostawcy aplikacji albo można zaimportować plik XML zawierający wymagane wartości.  

-   W **wdrażanie oprogramowania** kreatora na **zasady konfiguracji aplikacji** Skojarz zasady konfiguracji aplikacji utworzone przy użyciu typu wdrożenia zgodnego z aplikacji.  

##  <a name="bkmk_compliance1601"></a>Ulepszenia dotyczące ustawień zgodności  
 W wersji zapoznawczej Technical Preview 1601 dodano obsługę następujących funkcji:  

### <a name="microsoft-edge-browser-settings"></a>Ustawienia przeglądarki Microsoft Edge  
 Dodano nowe ustawienia przeglądarki Microsoft Edge do **Windows 8.1 i Windows 10** elementu konfiguracji (ustawienia dotyczą tylko urządzeń z systemem Windows 10).  

 Aby wyświetlić nowe ustawienia, wybierz pozycję **Microsoft Edge** z elementu konfiguracji **ustawienia urządzenia** strony **tworzenia elementu konfiguracji** kreatora.  

 Aby uzyskać więcej informacji, zobacz [jak utworzyć elementy konfiguracji dla urządzeń Windows 8.1 i Windows 10 zarządzanych bez klienta programu System Center Configuration Manager](../../compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md).  

### <a name="compliance-settings-for-windows-10-team-devices"></a>Ustawienia zgodności dla urządzeń z systemem Windows 10 Team  
 Te nowe ustawienia zgodności umożliwiają konfigurowanie urządzeń z systemem Windows 10 team, na przykład urządzeń Surface Hub.  

 Aby wyświetlić nowe ustawienia, wybierz pozycję **systemu Windows 10 Team** z elementu konfiguracji **ustawienia urządzenia** strony **tworzenia elementu konfiguracji** kreatora.  

 Aby uzyskać więcej informacji, zobacz [jak utworzyć elementy konfiguracji dla urządzeń Windows 8.1 i Windows 10 zarządzanych bez klienta programu System Center Configuration Manager](../../compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md).  

### <a name="android---kiosk-mode-for-samsung-knox-standardbr-hybrid"></a>Android — tryb kiosku dla Samsung KNOX Standard<br />Hybrydowe  
 Tryb kiosku umożliwia blokowanie urządzenia w celu zezwolenia tylko określonych funkcji. Na przykład można zezwolić na uruchamianie na urządzeniu tylko określonej zarządzanej aplikacji albo można wyłączyć przyciski regulacji głośności na urządzeniu. Można użyć tych ustawień dla modeli pokazowych urządzenia lub dla urządzeń przeznaczonych do wykonywania tylko jednej funkcji — na przykład urządzeń w punkcie sprzedaży. Te ustawienia są niedostępne w przypadku urządzeń Samsung KNOX Standard w **Windows 8.1 i Windows 10** elementu konfiguracji (ustawienia dotyczą tylko urządzeń z systemem Windows 10).  

 Aby wyświetlić nowe ustawienia, wybierz pozycję **tryb kiosku — Samsung KNOX** z elementu konfiguracji **ustawienia urządzenia** strony **tworzenia elementu konfiguracji** kreatora.  

 Aby uzyskać więcej informacji, zobacz [jak utworzyć elementy konfiguracji dla urządzeń Windows 8.1 i Windows 10 zarządzanych bez klienta programu System Center Configuration Manager](../../compliance/deploy-use/create-configuration-items-for-windows-8.1-and-windows-10-devices-managed-without-the-client.md).  
