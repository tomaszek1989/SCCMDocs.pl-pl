---
title: "Wdrażanie certyfikatów PKI | Dokumentacja firmy Microsoft"
description: "Przykład krok po kroku, aby dowiedzieć się, jak utworzyć i wdrożyć System Center Configuration Manager używa certyfikatów PKI, należy wykonać."
ms.custom: na
ms.date: 02/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 3417ff88-7177-4a0d-8967-ab21fe7eba17
caps.latest.revision: 11
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: b15f85b4483bbae2444d4e73d2e2aa0b3979d9ab
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="step-by-step-example-deployment-of-the-pki-certificates-for-system-center-configuration-manager-windows-server-2008-certification-authority"></a>Przykład krok po kroku wdrożenia certyfikatów PKI dla programu System Center Configuration Manager: Urząd certyfikacji systemu Windows Server 2008

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

W tym przykładzie krok po kroku, używa urząd certyfikacji (CA) systemu Windows Server 2008 i wdrożeniu procedur pokazujących, jak utworzyć i wdrożyć certyfikaty infrastruktury kluczy publicznych (PKI), których używa System Center Configuration Manager. W procedurach korzysta się z urzędu certyfikacji przedsiębiorstwa i z szablonów certyfikatów. Kroki procedur są właściwe tylko na użytek sieci testowej, jako weryfikacja koncepcji.  

 Ponieważ nie ma jednej właściwej metody wdrażania wymaganych certyfikatów, należy się zapoznać z dokumentacją wdrożeniową konkretnej infrastruktury PKI w zakresie wymaganych procedur i najlepszych praktyk wdrażania wymaganych certyfikatów w środowisku produkcyjnym. Aby uzyskać więcej informacji o wymaganiach dotyczących certyfikatów, zobacz [wymagania dotyczące certyfikatu PKI dla programu System Center Configuration Manager](../../../core/plan-design/network/pki-certificate-requirements.md).  

> [!TIP]  
>  Można dostosować instrukcje w tym temacie, aby systemy operacyjne, które nie zostały udokumentowane w części wymagania dotyczące sieci testowej. Niemniej jednak w przypadku uruchamiania urzędu certyfikacji wystawiającego certyfikat w systemie Windows Server 2012 nie jest wyświetlany monit o wersję szablonu certyfikatu. Zamiast tego należy określić to na **zgodności** we właściwościach szablonu:  
>   
>  -   **Urząd certyfikacji**: **Windows Server 2003**  
> -   **Odbiorca certyfikatu**: **Windows XP / Server 2003**  

## <a name="in-this-section"></a>W tej sekcji  
 W poniższych sekcjach zawarto przykładowe instrukcje krok po kroku dotyczące tworzenia i wdrażania następujących certyfikatów, których można użyć z System Center Configuration Manager:  

 [Wymagania dotyczące sieci testowej](#BKMK_testnetworkenvironment)  

 [Przegląd certyfikatów](#BKMK_overview2008)  

 [Wdrażanie certyfikatu serwera sieci web dla systemów lokacji z usługami IIS](#BKMK_webserver2008_cm2012)  

 [Wdrażanie certyfikatu usługi dla punktów dystrybucji w chmurze](#BKMK_clouddp2008_cm2012)  

 [Wdrażanie certyfikatu klienta dla komputerów z systemem Windows](#BKMK_client2008_cm2012)  

 [Wdrażanie certyfikatu klienta dla punktów dystrybucji](#BKMK_clientdistributionpoint2008_cm2012)  

 [Wdrażanie certyfikatu rejestracji dla urządzeń przenośnych](#BKMK_mobiledevices2008_cm2012)  

 [Wdrażanie certyfikatów dla komputerów AMT](#BKMK_AMT2008_cm2012)  

 [Wdrażanie certyfikatu klienta dla komputerów Mac](#BKMK_MacClient_SP1)  

##  <a name="BKMK_testnetworkenvironment"></a>Wymagania dotyczące sieci testowej  
 Z instrukcjami krok po kroku wiążą się następujące wymagania:  

-   W sieci testowej działają usługi domenowe Active Directory z systemem Windows Server 2008; instalacja to pojedyncza domena, pojedynczy las.  

-   Istnieje serwer członkowski z systemem Windows Server 2008 Enterprise Edition, został na nim zainstalowany Rola usług certyfikatów w usłudze Active Directory, która jest skonfigurowana jako główny urząd certyfikacji przedsiębiorstwa (CA).  

-   Masz jeden komputer, który ma system Windows Server 2008 (Standard Edition lub Enterprise Edition R2 lub nowszy) na nim zainstalowany tego komputera jest wyznaczony jako serwer członkowski, i usługi Internet Information Services (IIS) jest na nim zainstalowany. Ten komputer będzie serwerem systemu lokacji programu System Center Configuration Manager, skonfigurowanego przy użyciu sieci intranet w pełni kwalifikowaną nazwę domeny (FQDN), do obsługi połączeń klienckich w sieci intranet i internetowej nazwy FQDN, jeśli zachodzi potrzeba obsługi urządzeń przenośnych zarejestrowanych w programie System Center Configuration Manager i klientów w Internecie.  

-   Istnieje jeden klient systemu Windows Vista z zainstalowanym pakietem service najnowsze, a ten komputer jest skonfigurowany przy użyciu nazwy komputera, by zawierała znaki ASCII, który jest przyłączony do domeny. Ten komputer będzie komputera klienckiego programu System Center Configuration Manager.  

-   Możesz zalogować się przy użyciu konta administratora domeny głównej lub konta administratora domeny przedsiębiorstwa i wykorzystać to konto do wszystkich procedur tego przykładowego wdrożenia.  

##  <a name="BKMK_overview2008"></a>Przegląd certyfikatów  
 Poniższa tabela zawiera listę typów certyfikatów PKI, które mogą być wymagane dla programu System Center Configuration Manager i opisuje, jak są używane.  

|Wymagany certyfikat|Opis certyfikatu|  
|-----------------------------|-----------------------------|  
|Certyfikat serwera sieci Web dla systemów lokacji z usługami IIS|Ten certyfikat służy do szyfrowania danych i uwierzytelniania serwera wobec klientów. Należy zainstalować zewnętrznie z programu System Center Configuration Manager na serwerach systemów lokacji z systemem Internet Information Services (IIS) i które są skonfigurowane w programie System Center Configuration Manager do używania protokołu HTTPS.<br /><br /> Instrukcje konfiguracji i instalacji tego certyfikatu, zobacz [wdrażania certyfikatu serwera sieci web dla systemów lokacji z usługami IIS](#BKMK_webserver2008_cm2012) w tym temacie.|  
|Certyfikat usługi dla klientów do łączenia się z chmurowymi punktami dystrybucji|Instrukcje konfiguracji oraz instalacji tego certyfikatu, zobacz [wdrożenia certyfikatu usługi dla punktów dystrybucji w chmurze](#BKMK_clouddp2008_cm2012) w tym temacie.<br /><br /> **Ważne:** Ten certyfikat jest używany w połączeniu z certyfikatem zarządzania systemu Windows Azure. Aby uzyskać więcej informacji o certyfikacie zarządzania, zobacz [jak utworzyć certyfikat zarządzania](http://go.microsoft.com/fwlink/p/?LinkId=220281) i [jak dodać certyfikat zarządzania do subskrypcji systemu Windows Azure](http://go.microsoft.com/fwlink/?LinkId=241722) w sekcji platformy Windows Azure w bibliotece MSDN.|  
|Certyfikat klienta dla komputerów z systemem Windows|Ten certyfikat służy do uwierzytelniania komputerów klienckich programu System Center Configuration Manager do systemów lokacji, które są skonfigurowane do używania protokołu HTTPS. Może również służyć dla punktów zarządzania i punktów migracji stanu do monitorowania stanu operacyjnego, gdy są one skonfigurowane do używania protokołu HTTPS. Należy zainstalować zewnętrznie z programu System Center Configuration Manager na komputerach.<br /><br /> Instrukcje konfiguracji i instalacji tego certyfikatu, zobacz [wdrażania certyfikatu klienta dla komputerów z systemem Windows](#BKMK_client2008_cm2012) w tym temacie.|  
|Certyfikat klienta dla punktów dystrybucji|Ten certyfikat ma dwa cele:<br /><br /> Certyfikat służy do uwierzytelniania punktu dystrybucji wobec punktu zarządzania z włączonym protokołem HTTPS przed wysłaniem przez dany punkt dystrybucji komunikatów o stanie.<br /><br /> Po wybraniu w punkcie dystrybucji opcji **Włącz obsługę środowiska PXE dla klientów** certyfikat zostanie wysłany do komputerów przeprowadzających rozruch w środowisku PXE, aby umożliwić im połączenie z punktem zarządzania z włączoną obsługą HTTPS podczas wdrażania systemu operacyjnego.<br /><br /> Instrukcje konfiguracji i instalacji tego certyfikatu, zobacz [wdrażania certyfikatu klienta dla punktów dystrybucji](#BKMK_clientdistributionpoint2008_cm2012) w tym temacie.|  
|Certyfikat rejestracji dla urządzeń przenośnych|Ten certyfikat służy do uwierzytelniania klientów urządzeń przenośnych programu System Center Configuration Manager do systemów lokacji, które są skonfigurowane do używania protokołu HTTPS. Musi być zainstalowany w ramach rejestracji urządzeń przenośnych w programie System Center Configuration Manager i wybierz szablon certyfikatu skonfigurowanym jako ustawienie klienta urządzenia przenośnego.<br /><br /> Instrukcje konfiguracji tego certyfikatu, zobacz [wdrożenia certyfikatu rejestracji dla urządzeń przenośnych](#BKMK_mobiledevices2008_cm2012) w tym temacie.|  
|Certyfikaty dla komputerów Intel AMT|Trzy certyfikaty odnoszą się do zarządzania poza pasmem dla komputerów opartych na technologii Intel AMT:<ul><li>Certyfikat udostępniania technologii zarządzania aktywnego (AMT)</li><li>Certyfikat serwera sieci web AMT</li><li>Opcjonalnie certyfikat uwierzytelniania klienta dla 802.1 X sieci przewodowej lub bezprzewodowej</li></ul>Certyfikat udostępniania AMT musi być zainstalowany zewnętrznie z programu System Center Configuration Manager na komputerze punktu obsługi poza pasmem, a następnie wybierz certyfikat zainstalowany we właściwościach punktu Usługi poza pasmem. Certyfikat serwera sieci web AMT i certyfikat uwierzytelniania klienta są instalowane podczas udostępniania AMT i zarządzania, a następnie wybierz skonfigurowane szablony certyfikatów we właściwościach składnika zarządzania poza pasmem.<br /><br /> Instrukcje konfiguracji tych certyfikatów, zobacz [wdrożyć certyfikaty dla komputerów AMT](#BKMK_AMT2008_cm2012) w tym temacie.|  
|Certyfikat klienta dla komputerów Mac|Można zażądać i zainstaluj ten certyfikat na komputerze Mac, gdy używasz rejestracji programu System Center Configuration Manager i wybierz jako ustawienie klienta urządzenia przenośnego skonfigurowany szablon certyfikatu.<br /><br /> Instrukcje konfiguracji tego certyfikatu, zobacz [wdrażania certyfikatu klienta dla komputerów Mac](#BKMK_MacClient_SP1) w tym temacie.|  

##  <a name="BKMK_webserver2008_cm2012"></a>Wdrażanie certyfikatu serwera sieci web dla systemów lokacji z usługami IIS  
 Wdrożenie tego certyfikatu jest objęte następującymi procedurami:  

-   Utworzyć i wystawić szablon certyfikatu w urzędzie certyfikacji serwera sieci web  

-   Żądanie certyfikatu serwera sieci web  

-   Konfigurowanie usługi IIS do używania certyfikatu serwera sieci web  

###  <a name="BKMK_webserver22008"></a>Utworzyć i wystawić szablon certyfikatu w urzędzie certyfikacji serwera sieci web  
 Ta procedura powoduje utworzenie szablonu certyfikatu dla systemów lokacji programu System Center Configuration Manager i dodanie go do urzędu certyfikacji.  

##### <a name="to-create-and-issue-the-web-server-certificate-template-on-the-certification-authority"></a>Aby utworzyć i wystawić szablon certyfikatu serwera sieci Web w urzędzie certyfikacji  

1.  Utwórz grupę zabezpieczeń o nazwie **serwery IIS programu ConfigMgr** zawierającej serwery Członkowskie do zainstalowania systemów lokacji programu System Center Configuration Manager, z uruchomionymi usługami IIS.  

2.  Na serwerze członkowskim z usługami certyfikatów zainstalowane, w konsoli Urząd certyfikacji kliknij prawym przyciskiem myszy **szablonów certyfikatów** , a następnie wybierz **Zarządzaj** załadować **szablonów certyfikatów** konsoli.  

3.  W okienku wyników kliknij prawym przyciskiem myszy wpis **serwera sieci Web** w **Nazwa wyświetlana szablonu** kolumny, a następnie wybierz **Duplikuj szablon**.  

4.  W **Duplikuj szablon** dialogowe Sprawdź, czy **systemu Windows Server 2003, Enterprise Edition** jest zaznaczone, a następnie wybierz **OK**.  

    > [!IMPORTANT]  
    >  Nie wybieraj systemu **Windows 2008 Server, Enterprise Edition**.  

5.  W **właściwości nowego szablonu** okna dialogowego na **ogólne** , wprowadź nazwę szablonu, jak **certyfikatu serwera sieci Web programu ConfigMgr**, w celu wygenerowania certyfikatów sieci web, które będą używane w systemach lokacji programu Configuration Manager.  

6.  Wybierz **nazwa podmiotu** karcie i upewnij się, że **Dostarcz w żądaniu** jest zaznaczone.  

7.  Wybierz **zabezpieczeń** karcie, a następnie usuń **rejestracja** zgody **Administratorzy domeny** i **Administratorzy przedsiębiorstwa** grup zabezpieczeń.  

8.  Wybierz **Dodaj**, wprowadź **serwery IIS programu ConfigMgr** w tekście pole, a następnie wybierz **OK**.  

9. Wybierz **rejestracja** dla tej grupy uprawnienie i nie usuwaj **odczytu** uprawnienia.  

10. Wybierz **OK**, a następnie Zamknij **konsoli Szablony certyfikatów**.  

11. W konsoli Urząd certyfikacji kliknij prawym przyciskiem myszy **szablonów certyfikatów**, wybierz **nowy**, a następnie wybierz **szablon certyfikatu do wystawienia**.  

12. W **Włączanie szablonu certyfikatu** okno dialogowe, wybierz nowego szablonu, który został właśnie utworzony, **certyfikatu serwera sieci Web programu ConfigMgr**, a następnie wybierz **OK**.  

13. Jeśli nie ma potrzeby tworzenia i wystawiania certyfikatów Zamknij **urząd certyfikacji**.  

###  <a name="BKMK_webserver32008"></a>Żądanie certyfikatu serwera sieci web  
 Ta procedura pozwala określić wartości intranetowej i internetowej nazwy FQDN zdefiniowanych we właściwościach serwera systemu lokacji, a następnie instaluje certyfikat serwera sieci web na serwerze członkowskim z uruchomionymi usługami IIS.  

##### <a name="to-request-the-web-server-certificate"></a>Aby zażądać certyfikatu serwera sieci Web  

1.  Uruchom ponownie serwer członkowski, z uruchomionymi usługami IIS, aby upewnić się, że komputer ma dostęp do szablonu certyfikatu, który został utworzony za pomocą **odczytu** i **rejestracja** skonfigurowanych uprawnień.  

2.  Wybierz **Start**, wybierz **Uruchom**, a następnie wpisz **mmc.exe.** W pustej konsoli kliknij **pliku**, a następnie wybierz **Dodaj/Usuń przystawkę**.  

3.  W **Dodawanie lub usuwanie przystawek** okno dialogowe Wybierz **certyfikaty** z listy **dostępne przystawki**, a następnie wybierz **Dodaj**.  

4.  W **certyfikatów w przystawce** okno dialogowe Wybierz **konto komputera**, a następnie wybierz **dalej**.  

5.  W **wybierz komputer** okna dialogowego Sprawdź, czy **komputer lokalny: (komputer ten jest uruchomiona konsola)** jest zaznaczone, a następnie wybierz **Zakończ**.  

6.  W **Dodawanie lub usuwanie przystawek** okno dialogowe Wybierz **OK**.  

7.  W konsoli rozwiń **certyfikaty (komputer lokalny)**, a następnie wybierz **osobiste**.  

8.  Kliknij prawym przyciskiem myszy **certyfikaty**, wybierz **wszystkie zadania**, a następnie wybierz **Żądaj nowego certyfikatu**.  

9. Na **przed rozpoczęciem** wybierz **dalej**.  

10. Jeśli widzisz **wybierz zasady rejestracji certyfikatu** wybierz **dalej**.  

11. Na **Żądaj certyfikatów** Znajdź **certyfikatu serwera sieci Web programu ConfigMgr** z listy dostępnych certyfikatów, a następnie wybierz **do zarejestrowania tego certyfikatu jest wymaganych więcej informacji. Kliknij tutaj, aby skonfigurować ustawienia**.  

12. W **właściwości certyfikatu** dialogowym **podmiotu** karcie, nie należy wprowadzać żadnych zmian do **nazwa podmiotu**. Inaczej mówiąc, pole **Wartość** w sekcji **Nazwa podmiotu** pozostanie puste. Zamiast tego w **alternatywna nazwa** wybierz **typu** listy rozwijanej, a następnie wybierz **DNS**.  

13. W **wartość** określ te wartości nazw FQDN, które zostaną określone we właściwościach systemu lokacji programu System Center Configuration Manager, a następnie wybierz **OK** zamknąć **właściwości certyfikatu** okno dialogowe.  

     Przykłady:  

    -   Jeśli system lokacji przyjmuje tylko połączenia klienckie z intranetu, a intranetowa nazwa FQDN serwera systemu lokacji to **server1.internal.contoso.com**, wprowadź **server1.internal.contoso.com**, a następnie wybierz **Dodaj**.  

    -   Jeśli system lokacji przyjmuje połączenia klienckie i z intranetu, i z Internetu, przy czym intranetowa nazwa FQDN serwera systemu lokacji to **server1.internal.contoso.com** , a internetowa nazwa FQDN serwera systemu lokacji to **server.contoso.com**:  

        1.  Wprowadź **server1.internal.contoso.com**, a następnie wybierz **Dodaj**.  

        2.  Wprowadź **server.contoso.com**, a następnie wybierz **Dodaj**.  

        > [!NOTE]  
        >  Można określić nazwy FQDN dla programu System Center Configuration Manager w dowolnej kolejności. Należy jednak sprawdzić, czy wszystkie urządzenia, które będą posługiwać się certyfikatem, takie jak urządzenia przenośne i serwery proxy sieci web, można użyć nazwy alternatywnej podmiotu (SAN) certyfikatu oraz wielu wartości w sieci SAN. Jeśli urządzenia obsługują ograniczoną liczbę wartości SAN w certyfikatach, może zajść potrzeba zmiany kolejności nazw FQDN lub użycia zamiast nich wartości Podmiot.  

14. Na **Żądaj certyfikatów** wybierz **certyfikatu serwera sieci Web programu ConfigMgr** z listy dostępnych certyfikatów, a następnie wybierz **rejestracja**.  

15. Na **wyniki instalacji certyfikatów** , poczekaj, aż certyfikat został zainstalowany, a następnie wybierz **Zakończ**.  

16. Zamknij konsolę **Certyfikaty (komputer lokalny)**.  

###  <a name="BKMK_webserver42008"></a>Konfigurowanie usługi IIS do używania certyfikatu serwera sieci web  
 Ta procedura wiąże zainstalowany certyfikat z **Domyślną witryną sieci Web**usług IIS.  

##### <a name="to-set-up-iis-to-use-the-web-server-certificate"></a>Aby skonfigurować usługi IIS do używania certyfikatu serwera sieci web  

1.  Na serwerze członkowskim, na którym są zainstalowane usługi IIS, wybierz **Start**, wybierz **programy**, wybierz **narzędzia administracyjne**, a następnie wybierz **Internet Information Services (IIS) Manager**.  

2.  Rozwiń węzeł **witryny**, kliknij prawym przyciskiem myszy **domyślna witryna sieci Web**, a następnie wybierz **Edytuj powiązania**.  

3.  Wybierz **https** wpis, a następnie wybierz **edytować**.  

4.  W **edytowanie powiązań witryny** okno dialogowe, wybierz certyfikat, którego zażądano za pomocą szablonu certyfikat serwera sieci Web programu ConfigMgr, a następnie wybierz **OK**.  

    > [!NOTE]  
    >  Jeśli nie masz pewności, który jest poprawny certyfikat, wybierz jedną, a następnie wybierz **widoku**. Pozwala to porównać szczegóły wybranego certyfikatu certyfikatów w przystawce Certyfikaty. Na przykład przystawki Certyfikaty zawiera szablon certyfikatu, który został użyty do żądania certyfikatu. Możesz następnie porównać odcisk palca certyfikatu, którego zażądano za pomocą szablonu certyfikat serwera sieci Web programu ConfigMgr do odcisk palca certyfikatu aktualnie wybranego w **edytowanie powiązań witryny** okno dialogowe.  

5.  Wybierz **OK** w **edytowanie powiązań witryny** okna dialogowego pole, a następnie wybierz **Zamknij**.  

6.  Zamknij **Menedżera internetowych usług informacyjnych (IIS)**.  

 Serwer członkowski jest teraz skonfigurowane przy użyciu certyfikatu serwera sieci web programu System Center Configuration Manager.  

> [!IMPORTANT]  
>  Po zainstalowaniu serwera systemu lokacji programu System Center Configuration Manager na tym komputerze, upewnij się, określić tej samej nazwy FQDN we właściwościach systemu lokacji, ponieważ określone podczas żądania certyfikatu.  

##  <a name="BKMK_clouddp2008_cm2012"></a>Wdrażanie certyfikatu usługi dla punktów dystrybucji w chmurze  

Wdrożenie tego certyfikatu jest objęte następującymi procedurami:  

-   [Utwórz i wystaw szablon certyfikatu w urzędzie certyfikacji serwera sieci web niestandardowe](#BKMK_clouddpcreating2008)  

-   [Żądanie certyfikatu serwera sieci web niestandardowe](#BKMK_clouddprequesting2008)  

-   [Eksportowanie certyfikatu serwera sieci web niestandardowe dla punktów dystrybucji w chmurze](#BKMK_clouddpexporting2008)  

###  <a name="BKMK_clouddpcreating2008"></a>Utwórz i wystaw szablon certyfikatu w urzędzie certyfikacji serwera sieci web niestandardowe  
 Ta procedura powoduje utworzenie niestandardowego szablonu certyfikatu opartego na szablonie certyfikatu serwera sieci web. Certyfikat jest przeznaczony dla punktów dystrybucji w chmurze programu System Center Configuration Manager, a klucz prywatny musi być eksportowalny. Po utworzeniu szablon certyfikatu jest dodawany do urzędu certyfikacji.  

> [!NOTE]  
>  Ta procedura używa innego szablonu certyfikatu z utworzonego szablonu certyfikatu serwera sieci web dla systemów lokacji z usługami IIS. Mimo że oba certyfikaty wymagają funkcji uwierzytelniania serwera, certyfikat dla punktów dystrybucji w chmurze wymaga wprowadzenia niestandardowej wartości parametru Nazwa podmiotu i klucz prywatny musi zostać wyeksportowany. Zabezpieczeń najlepszym rozwiązaniem, czy nie skonfigurowane szablony certyfikatów, aby wyeksportować klucza prywatnego, chyba że taka konfiguracja jest wymagana. Punkt dystrybucji w chmurze wymaga tej konfiguracji, ponieważ należy zaimportować certyfikat jako plik, zamiast wybierz go z magazynu certyfikatów.  
>   
>  Podczas tworzenia nowego szablonu certyfikatu dla tego certyfikatu pozwala ograniczyć komputerów, które można zażądać certyfikatu, którego klucz prywatny można eksportować. W sieci produkcyjnej można także rozważyć wprowadzenie następujących zmian dla tego certyfikatu:  
>   
>  -   Wymaganie zatwierdzenia instalacji certyfikatu w celu zapewnienia dodatkowych zabezpieczeń.  
> -   Wydłużenie okresu ważności certyfikatu. Ponieważ należy wyeksportować i zaimportować certyfikat za każdym razem przed wygaśnięciem, wzrost okresu ważności zmniejsza częstotliwość powtarzania tej procedury. Jednak wzrost okresu ważności również zmniejszenie bezpieczeństwa certyfikatu, ponieważ zapewnia to osobie atakującej na odszyfrowanie klucza prywatnego i kradzież certyfikatu więcej czasu.  
> -   Użycie niestandardowej wartości nazwa alternatywnej podmiotu (SAN) w celu łatwiejszego odróżnienia tego certyfikatu od standardowych certyfikatów serwera sieci Web używanego z programem IIS.  

##### <a name="to-create-and-issue-the-custom-web-server-certificate-template-on-the-certification-authority"></a>Aby utworzyć i wystawić szablon certyfikatu w urzędzie certyfikacji serwera sieci web niestandardowe  

1.  Utwórz grupę zabezpieczeń o nazwie **serwerów lokacji programu ConfigMgr** zawierającej serwery Członkowskie do zainstalowania serwerów lokacji podstawowej programu System Center Configuration Manager, które będą zarządzać punktami dystrybucji w chmurze.  

2.  Na serwerze członkowskim, na którym jest uruchomiona konsola urzędu certyfikacji, kliknij prawym przyciskiem myszy **szablonów certyfikatów**, a następnie wybierz **Zarządzaj** załadować Konsolę zarządzania szablonami certyfikatów.  

3.  W okienku wyników kliknij prawym przyciskiem myszy wpis **serwera sieci Web** w **Nazwa wyświetlana szablonu** kolumny, a następnie wybierz **Duplikuj szablon**.  

4.  W **Duplikuj szablon** dialogowe Sprawdź, czy **systemu Windows Server 2003, Enterprise Edition** jest zaznaczone, a następnie wybierz **OK**.  

    > [!IMPORTANT]  
    >  Nie wybieraj systemu **Windows 2008 Server, Enterprise Edition**.  

5.  W **właściwości nowego szablonu** okna dialogowego na **ogólne** , wprowadź nazwę szablonu, jak **certyfikat punktu dystrybucji w chmurze programu ConfigMgr**, w celu wygenerowania certyfikatu serwera sieci web dla punktów dystrybucji w chmurze.  

6.  Wybierz **obsługiwanie żądań** karcie, a następnie wybierz **Zezwalaj na eksportowanie klucza prywatnego**.  

7.  Wybierz **zabezpieczeń** karcie, a następnie usuń **rejestracja** zgody **Administratorzy przedsiębiorstwa** grupy zabezpieczeń.  

8.  Wybierz **Dodaj**, wprowadź **serwerów lokacji programu ConfigMgr** w tekście pole, a następnie wybierz **OK**.  

9. Wybierz dla tej grupy uprawnienie **Rejestracja** i nie usuwaj zaznaczenia uprawnienia **Odczyt** .  

10. Wybierz **OK**, a następnie Zamknij **konsoli Szablony certyfikatów**.  

11. W konsoli Urząd certyfikacji kliknij prawym przyciskiem myszy **szablonów certyfikatów**, wybierz **nowy**, a następnie wybierz **szablon certyfikatu do wystawienia**.  

12. W **Włączanie szablonu certyfikatu** okno dialogowe, wybierz nowego szablonu, który został właśnie utworzony, **certyfikat punktu dystrybucji w chmurze programu ConfigMgr**, a następnie wybierz **OK**.  

13. Jeśli nie masz tworzenia i wystawiania certyfikatów Zamknij **urząd certyfikacji**.  

###  <a name="BKMK_clouddprequesting2008"></a>Żądanie certyfikatu serwera sieci web niestandardowe  
 Tej procedury żądanie, a następnie instaluje certyfikat serwera sieci web niestandardowe na serwerze członkowskim, który będzie uruchamiany na serwerze lokacji.  

##### <a name="to-request-the-custom-web-server-certificate"></a>Aby zażądać niestandardowego certyfikatu serwera sieci Web  

1.  Uruchom ponownie serwer członkowski po utworzeniu i skonfigurowaniu **serwerów lokacji programu ConfigMgr** grupy zabezpieczeń, aby upewnić się, że komputer ma dostęp do szablonu certyfikatu, który został utworzony za pomocą **odczytu** i **rejestracja** skonfigurowanych uprawnień.  

2.  Wybierz **Start**, wybierz **Uruchom**, a następnie wprowadź **mmc.exe.** W pustej konsoli kliknij **pliku**, a następnie wybierz **Dodaj/Usuń przystawkę**.  

3.  W **Dodawanie lub usuwanie przystawek** okno dialogowe Wybierz **certyfikaty** z listy **dostępne przystawki**, a następnie wybierz **Dodaj**.  

4.  W **certyfikatów w przystawce** okno dialogowe Wybierz **konto komputera**, a następnie wybierz **dalej**.  

5.  W **wybierz komputer** okna dialogowego Sprawdź, czy **komputer lokalny: (komputer ten jest uruchomiona konsola)** jest zaznaczone, a następnie wybierz **Zakończ**.  

6.  W **Dodawanie lub usuwanie przystawek** okno dialogowe Wybierz **OK**.  

7.  W konsoli rozwiń **certyfikaty (komputer lokalny)**, a następnie wybierz **osobiste**.  

8.  Kliknij prawym przyciskiem myszy **certyfikaty**, wybierz **wszystkie zadania**, a następnie wybierz **Żądaj nowego certyfikatu**.  

9. Na **przed rozpoczęciem** wybierz **dalej**.  

10. Jeśli widzisz **wybierz zasady rejestracji certyfikatu** wybierz **dalej**.  

11. Na **Żądaj certyfikatów** Znajdź **certyfikat punktu dystrybucji w chmurze programu ConfigMgr** z listy dostępnych certyfikatów, a następnie wybierz **więcej informacji jest wymagany do zarejestrowania dla tego certyfikatu. Wybierz tutaj skonfigurować ustawienia**.  

12. W **właściwości certyfikatu** okna dialogowego, **podmiotu** karcie dla **nazwa podmiotu**, wybierz **nazwa pospolita** jako **typu**.  

13. W polu **Wartość** określ wybór nazwy usługi i nazwy domeny, używając formatu FQDN. Na przykład: **clouddp1.contoso.com**.  

    > [!NOTE]  
    >  Unikatowość nazwy usługi w danym obszarze nazw. Zostanie użyty system DNS w celu utworzenia aliasu (rekordu CNAME) i odwzorowania tej nazwy usługi na automatycznie generowany identyfikator (GUID) i adres IP z usługi Windows Azure.  

14. Wybierz **Dodaj**, a następnie wybierz **OK** zamknąć **właściwości certyfikatu** okno dialogowe.  

15. Na **Żądaj certyfikatów** wybierz **certyfikat punktu dystrybucji w chmurze programu ConfigMgr** z listy dostępnych certyfikatów, a następnie wybierz **rejestracja**.  

16. Na **wyniki instalacji certyfikatów** , poczekaj, aż certyfikat został zainstalowany, a następnie wybierz **Zakończ**.  

17. Zamknij konsolę **Certyfikaty (komputer lokalny)**.  

###  <a name="BKMK_clouddpexporting2008"></a>Eksportowanie certyfikatu serwera sieci web niestandardowe dla punktów dystrybucji w chmurze  
 Ta procedura umożliwia wyeksportowanie niestandardowego certyfikatu serwera sieci Web do pliku, aby można go było zaimportować po utworzeniu chmurowego punktu dystrybucji.  

##### <a name="to-export-the-custom-web-server-certificate-for-cloud-based-distribution-points"></a>Aby wyeksportować niestandardowy certyfikat serwera sieci Web dla chmurowych punktów dystrybucji  

1.  W **certyfikaty (komputer lokalny)** konsoli, kliknij prawym przyciskiem myszy właśnie zainstalowany certyfikat, wybierz polecenie **wszystkie zadania**, a następnie wybierz **wyeksportować**.  

2.  W Kreatorze eksportu certyfikatów wybierz **dalej**.  

3.  Na **eksportowanie klucza prywatnego** wybierz **tak, Eksportuj klucz prywatny**, a następnie wybierz **dalej**.  

    > [!NOTE]  
    >  Jeżeli ta opcja nie jest dostępna, certyfikat został utworzony bez opcji eksportu klucza prywatnego. W tym scenariuszu nie można wyeksportować certyfikatu w wymaganym formacie. Należy skonfigurować szablon certyfikatu, aby klucz prywatny można eksportować, a następnie zażądać certyfikatu ponownie.  

4.  Na **Format pliku eksportu** strony, upewnij się, że **wymiany informacji osobistych — PKCS #12 (. PFX)** opcja jest zaznaczona.  

5.  Na **hasło** Określ silne hasło, aby zabezpieczyć wyeksportowany certyfikat kluczem prywatnym, a następnie wybierz **dalej**.  

6.  Na **Eksport pliku** Określ nazwę pliku, który chcesz wyeksportować, a następnie wybierz **dalej**.  

7.  Aby zamknąć kreatora, wybierz **Zakończ** w **Kreatora eksportu certyfikatów** , a następnie wybierz **OK** w oknie dialogowym potwierdzenia.  

8.  Zamknij konsolę **Certyfikaty (komputer lokalny)**.  

9. Zapisz plik w bezpiecznym miejscu i upewnij się, że można do niego dostęp z konsoli programu System Center Configuration Manager.  

 Certyfikat jest teraz gotowy do zaimportowania po utworzeniu chmurowego punktu dystrybucji.  

##  <a name="BKMK_client2008_cm2012"></a>Wdrażanie certyfikatu klienta dla komputerów z systemem Windows  
 Wdrożenie tego certyfikatu jest objęte następującymi procedurami:  

-   Utwórz i wystaw szablon certyfikatu uwierzytelniania stacji roboczej w urzędzie certyfikacji  

-   Konfigurowanie automatycznej rejestracji szablonu uwierzytelniania stacji roboczej za pomocą zasad grupy  

-   Automatyczne rejestrowanie certyfikatu uwierzytelniania stacji roboczej i zweryfikować jego instalację na komputerach  

###  <a name="BKMK_client02008"></a>Utwórz i wystaw szablon certyfikatu uwierzytelniania stacji roboczej w urzędzie certyfikacji  
 Ta procedura powoduje utworzenie szablonu certyfikatu dla klienta programu System Center Configuration Manager z komputerów i dodanie go do urzędu certyfikacji.  

##### <a name="to-create-and-issue-the-workstation-authentication-certificate-template-on-the-certification-authority"></a>Aby utworzyć i wydać szablon certyfikatu uwierzytelniania stacji roboczej w urzędzie certyfikacji  

1.  Na serwerze członkowskim, na którym jest uruchomiona konsola urzędu certyfikacji, kliknij prawym przyciskiem myszy **szablonów certyfikatów**, a następnie wybierz **Zarządzaj** załadować Konsolę zarządzania szablonami certyfikatów.  

2.  W okienku wyników kliknij prawym przyciskiem myszy wpis **Uwierzytelnianie stacji roboczej** w **Nazwa wyświetlana szablonu** kolumny, a następnie wybierz **Duplikuj szablon**.  

3.  W **Duplikuj szablon** dialogowe Sprawdź, czy **systemu Windows Server 2003, Enterprise Edition** jest zaznaczone, a następnie wybierz **OK**.  

    > [!IMPORTANT]  
    >  Nie wybieraj systemu **Windows 2008 Server, Enterprise Edition**.  

4.  W **właściwości nowego szablonu** okna dialogowego na **ogólne** , wprowadź nazwę szablonu, jak **certyfikat klienta programu ConfigMgr**, w celu wygenerowania certyfikatów klienta, które będą używane na komputerach klienckich programu Configuration Manager.  

5.  Wybierz **zabezpieczeń** zaznacz **komputerów w domenie** grupę, a następnie wybierz dodatkowe uprawnienia **odczytu** i **Autorejestrowanie**. Nie usuwaj zaznaczenia opcji **Rejestracja**.  

6.  Wybierz **OK**, a następnie Zamknij **konsoli Szablony certyfikatów**.  

7.  W konsoli Urząd certyfikacji kliknij prawym przyciskiem myszy **szablonów certyfikatów**, wybierz **nowy**, a następnie wybierz **szablon certyfikatu do wystawienia**.  

8.  W **Włączanie szablonu certyfikatu** okno dialogowe, wybierz nowego szablonu, który został właśnie utworzony, **certyfikat klienta programu ConfigMgr**, a następnie wybierz **OK**.  

9. Jeśli nie ma potrzeby tworzenia i wystawiania certyfikatów Zamknij **urząd certyfikacji**.  

###  <a name="BKMK_client12008"></a>Konfigurowanie automatycznej rejestracji szablonu uwierzytelniania stacji roboczej za pomocą zasad grupy  
 Ta procedura konfiguruje zasady grupy celu autorejestracji certyfikatu klienta na komputerach.  

##### <a name="to-set-up-autoenrollment-of-the-workstation-authentication-template-by-using-group-policy"></a>Aby skonfigurować autorejestrację szablonu uwierzytelniania stacji roboczej za pomocą zasad grupy  

1.  Na kontrolerze domeny, wybierz **Start**, wybierz **narzędzia administracyjne**, a następnie wybierz **Zarządzanie zasadami grupy**.  

2.  Przejdź do odpowiedniej domeny, kliknij prawym przyciskiem myszy domenę, a następnie wybierz **Utwórz obiekt GPO w tej domenie i umieść tu łącze**.  

    > [!NOTE]  
    >  W tym kroku wykorzystano najlepsze rozwiązanie dotyczące tworzenia nowej zasady grupy dla ustawień niestandardowych zamiast edycji domyślnych zasad domeny instalowanych za pomocą usług domenowych w usłudze Active Directory. Po przypisaniu zasad grupy na poziomie domeny spowoduje ich zastosowania do wszystkich komputerów w domenie. W środowisku produkcyjnym można ograniczyć autorejestrację tak, aby dotyczyła ona tylko wybranych komputerów. Można przypisać zasad grupy na poziomie jednostki organizacyjnej, lub można filtrować zasady grupy za pomocą grupy zabezpieczeń domeny, dzięki czemu dotyczy tylko komputerów w grupie. W przypadku ograniczenia autorejestracji należy pamiętać o uwzględnieniu serwera skonfigurowanego jako punkt zarządzania.  

3.  W **nowego obiektu zasad grupy** okna dialogowego wprowadź nazwę, jak **autorejestrowanie certyfikatów**, nowych zasad grupy, a następnie wybierz **OK**.  

4.  W okienku wyników na **powiązane obiekty zasad grupy** karcie, kliknij prawym przyciskiem myszy nową zasadę grupy, a następnie wybierz **edytować**.  

5.  W **Edytor zarządzania zasadami grupy**, rozwiń węzeł **zasad** pod **konfiguracji komputera**, a następnie przejdź do **ustawienia systemu Windows** / **ustawienia zabezpieczeń** / **zasady kluczy publicznych**.  

6.  Kliknij prawym przyciskiem myszy typ obiektu o nazwie **klient usług certyfikatów — automatyczne rejestrowanie**, a następnie wybierz **właściwości**.  

7.  Z **Model konfiguracji** listy rozwijanej wybierz pozycję **włączone**, wybierz **Odnów wygasłe certyfikaty, aktualizuj oczekujące certyfikaty, usuń odwołane certyfikaty**, wybierz **Aktualizuj certyfikaty, które używają szablonów certyfikatów**, a następnie wybierz **OK**.  

8.  Zamknij okno **Zarządzanie zasadami grupy**.  

###  <a name="BKMK_client22008"></a>Automatyczne rejestrowanie certyfikatu uwierzytelniania stacji roboczej i zweryfikować jego instalację na komputerach  
 Ta procedura powoduje zainstalowanie certyfikatu klienta na komputerach i weryfikację instalacji.  

##### <a name="to-automatically-enroll-the-workstation-authentication-certificate-and-verify-its-installation-on-the-client-computer"></a>Aby automatycznie zarejestrować certyfikat uwierzytelniania stacji roboczej i zweryfikować jego instalację na komputerze klienckim  

1.  Uruchom ponownie stację roboczą i poczekaj kilka minut przed zalogowaniem.  

    > [!NOTE]  
    >  Ponowne uruchomienie komputera to najbardziej niezawodna metoda zapewnienia pomyślnej autorejestracji certyfikatu.  

2.  Zaloguj się przy użyciu konta z uprawnieniami administracyjnymi.  

3.  W polu wyszukiwania wprowadź **mmc.exe.**, a następnie naciśnij klawisz **Enter**.  

4.  W pustej konsoli zarządzania, wybierz **pliku**, a następnie wybierz **Dodaj/Usuń przystawkę**.  

5.  W **Dodawanie lub usuwanie przystawek** okno dialogowe Wybierz **certyfikaty** z listy **dostępne przystawki**, a następnie wybierz **Dodaj**.  

6.  W **certyfikatów w przystawce** okno dialogowe Wybierz **konto komputera**, a następnie wybierz **dalej**.  

7.  W **wybierz komputer** okna dialogowego Sprawdź, czy **komputer lokalny: (komputer ten jest uruchomiona konsola)** jest zaznaczone, a następnie wybierz **Zakończ**.  

8.  W **Dodawanie lub usuwanie przystawek** okno dialogowe Wybierz **OK**.  

9. W konsoli rozwiń **certyfikaty (komputer lokalny)**, rozwiń węzeł **osobiste**, a następnie wybierz **certyfikaty**.  

10. W okienku wyników sprawdź, czy certyfikat ma **uwierzytelnianie klienta** w **zamierzony cel** kolumny, a **certyfikat klienta programu ConfigMgr** w **szablonu certyfikatu** kolumny.  

11. Zamknij konsolę **Certyfikaty (komputer lokalny)**.  

12. Powtórz kroki od 1 do 11 dla serwera członkowskiego sprawdzić, czy serwer, który zostanie skonfigurowany jako punkt zarządzania także zawiera certyfikat klienta.  

 Komputer jest skonfigurowany z certyfikatem klienta programu System Center Configuration Manager.  

##  <a name="BKMK_clientdistributionpoint2008_cm2012"></a>Wdrażanie certyfikatu klienta dla punktów dystrybucji  

> [!NOTE]  
>  Tego certyfikatu można także użyć dla obrazów nośników, które nie używają rozruchu PXE, ponieważ wymagania dotyczące certyfikatu są takie same.  

 Wdrożenie tego certyfikatu jest objęte następującymi procedurami:  

-   Utworzyć i wydać niestandardowy szablon certyfikatu uwierzytelniania stacji roboczej w urzędzie certyfikacji  

-   Żądanie niestandardowego certyfikatu uwierzytelniania stacji roboczej  

-   Eksportowanie certyfikatu klienta dla punktów dystrybucji  

###  <a name="BKMK_clientdistributionpoint02008"></a>Utworzyć i wydać niestandardowy szablon certyfikatu uwierzytelniania stacji roboczej w urzędzie certyfikacji  
 Ta procedura powoduje utworzenie niestandardowego szablonu certyfikatu dla punktów dystrybucji programu System Center Configuration Manager, aby klucz prywatny można eksportować i dodanie szablonu certyfikatu do urzędu certyfikacji.  

> [!NOTE]  
>  Ta procedura wykorzystuje inny szablon certyfikatu z szablonu certyfikatu, który został utworzony dla komputerów klienckich. Mimo że oba certyfikaty wymagają możliwości uwierzytelniania klienta, certyfikat dla punktów dystrybucji wymaga wyeksportowania klucza prywatnego. Zabezpieczeń najlepszym rozwiązaniem, czy nie skonfigurowane szablony certyfikatów, więc klucz prywatny można eksportować, chyba że taka konfiguracja jest wymagana. Punkt dystrybucji wymaga tej konfiguracji, ponieważ należy zaimportować certyfikat jako plik zamiast wybierz go z magazynu certyfikatów.  
>   
>  Podczas tworzenia nowego szablonu certyfikatu dla tego certyfikatu pozwala ograniczyć komputerów, które można zażądać certyfikatu, którego klucz prywatny można eksportować. W naszym przykładowym wdrożeniu będzie to grupa zabezpieczeń utworzona uprzednio dla serwerów systemu lokacji programu System Center Configuration Manager z usługami IIS. W używanej sieci, która dystrybuuje role systemu lokacji usług IIS, należy rozważyć utworzenie nowej grupy zabezpieczeń dla serwerów, na których działają punkty dystrybucji, aby można było ograniczyć certyfikaty tylko do tych serwerów systemu lokacji. Można także rozważyć wprowadzenie następujących modyfikacji certyfikatu:  
>   
>  -   Wymaganie zatwierdzenia instalacji certyfikatu w celu zapewnienia dodatkowych zabezpieczeń.  
> -   Wydłużenie okresu ważności certyfikatu. Ponieważ należy wyeksportować i zaimportować certyfikat za każdym razem przed wygaśnięciem, wzrost okresu ważności zmniejsza częstotliwość powtarzania tej procedury. Jednak wzrost okresu ważności również zmniejszenie bezpieczeństwa certyfikatu, ponieważ zapewnia to osobie atakującej na odszyfrowanie klucza prywatnego i kradzież certyfikatu więcej czasu.  
> -   Użycie niestandardowej wartości w polu Podmiot certyfikatu lub nazwy alternatywnej podmiotu (SAN), aby ułatwić odróżnienie tego certyfikatu od standardowych certyfikatów klientów. Może to być szczególnie przydatne, jeżeli ten sam certyfikat jest używany dla kilku punktów dystrybucji.  

##### <a name="to-create-and-issue-the-custom-workstation-authentication-certificate-template-on-the-certification-authority"></a>Aby utworzyć i wydać niestandardowy szablon certyfikatu uwierzytelniania stacji roboczej w urzędzie certyfikacji  

1.  Na serwerze członkowskim, na którym jest uruchomiona konsola urzędu certyfikacji, kliknij prawym przyciskiem myszy **szablonów certyfikatów**, a następnie wybierz **Zarządzaj** załadować Konsolę zarządzania szablonami certyfikatów.  

2.  W okienku wyników kliknij prawym przyciskiem myszy wpis **Uwierzytelnianie stacji roboczej** w **Nazwa wyświetlana szablonu** kolumny, a następnie wybierz **Duplikuj szablon**.  

3.  W **Duplikuj szablon** dialogowe Sprawdź, czy **systemu Windows Server 2003, Enterprise Edition** jest zaznaczone, a następnie wybierz **OK**.  

    > [!IMPORTANT]  
    >  Nie wybieraj systemu **Windows 2008 Server, Enterprise Edition**.  

4.  W **właściwości nowego szablonu** okna dialogowego na **ogólne** , wprowadź nazwę szablonu, jak **certyfikat punktu dystrybucji klienta programu ConfigMgr**, aby wygenerować certyfikat uwierzytelniania klienta dla punktów dystrybucji.  

5.  Wybierz **obsługiwanie żądań** karcie, a następnie wybierz **Zezwalaj na eksportowanie klucza prywatnego**.  

6.  Wybierz **zabezpieczeń** karcie, a następnie usuń **rejestracja** zgody **Administratorzy przedsiębiorstwa** grupy zabezpieczeń.  

7.  Wybierz **Dodaj**, wprowadź **serwery IIS programu ConfigMgr** w tekście pole, a następnie wybierz **OK**.  

8.  Wybierz dla tej grupy uprawnienie **Rejestracja** i nie usuwaj zaznaczenia uprawnienia **Odczyt** .  

9. Wybierz **OK**, a następnie Zamknij **konsoli Szablony certyfikatów**.  

10. W konsoli Urząd certyfikacji kliknij prawym przyciskiem myszy **szablonów certyfikatów**, wybierz **nowy**, a następnie wybierz **szablon certyfikatu do wystawienia**.  

11. W **Włączanie szablonu certyfikatu** okno dialogowe, wybierz nowego szablonu, który został właśnie utworzony, **certyfikat punktu dystrybucji klienta programu ConfigMgr**, a następnie wybierz **OK**.  

12. Jeśli nie masz tworzenia i wystawiania certyfikatów Zamknij **urząd certyfikacji**.  

###  <a name="BKMK_clientdistributionpoint12008"></a>Żądanie niestandardowego certyfikatu uwierzytelniania stacji roboczej  
 Ta procedura żądanie, a następnie instalację niestandardowego certyfikatu klienta na serwerze członkowskim z systemem usług IIS, który zostanie skonfigurowany jako punkt dystrybucji.  

##### <a name="to-request-the-custom-workstation-authentication-certificate"></a>Aby zażądać niestandardowego certyfikatu uwierzytelniania stacji roboczej  

1.  Wybierz **Start**, wybierz **Uruchom**, a następnie wprowadź **mmc.exe.** W pustej konsoli kliknij **pliku**, a następnie wybierz **Dodaj/Usuń przystawkę**.  

2.  W **Dodawanie lub usuwanie przystawek** okno dialogowe Wybierz **certyfikaty** z listy **dostępne przystawki**, a następnie wybierz **Dodaj**.  

3.  W **certyfikatów w przystawce** okno dialogowe Wybierz **konto komputera**, a następnie wybierz **dalej**.  

4.  W **wybierz komputer** okna dialogowego Sprawdź, czy **komputer lokalny: (komputer ten jest uruchomiona konsola)** jest zaznaczone, a następnie wybierz **Zakończ**.  

5.  W **Dodawanie lub usuwanie przystawek** okno dialogowe Wybierz **OK**.  

6.  W konsoli rozwiń **certyfikaty (komputer lokalny)**, a następnie wybierz **osobiste**.  

7.  Kliknij prawym przyciskiem myszy **certyfikaty**, wybierz **wszystkie zadania**, a następnie wybierz **Żądaj nowego certyfikatu**.  

8.  Na **przed rozpoczęciem** wybierz **dalej**.  

9. Jeśli widzisz **wybierz zasady rejestracji certyfikatu** wybierz **dalej**.  

10. Na **Żądaj certyfikatów** wybierz **certyfikat punktu dystrybucji klienta programu ConfigMgr** z listy dostępnych certyfikatów, a następnie wybierz **rejestracja**.  

11. Na **wyniki instalacji certyfikatów** , poczekaj, aż certyfikat został zainstalowany, a następnie wybierz **Zakończ**.  

12. W okienku wyników sprawdź, czy certyfikat ma **uwierzytelnianie klienta** w **zamierzony cel** kolumny i że **certyfikat punktu dystrybucji klienta programu ConfigMgr** w **szablonu certyfikatu** kolumny.  

13. Nie zamykaj konsoli **Certyfikaty (komputer lokalny)**.  

###  <a name="BKMK_exportclientdistributionpoint22008"></a>Eksportowanie certyfikatu klienta dla punktów dystrybucji  
 Ta procedura umożliwia wyeksportowanie niestandardowego certyfikatu uwierzytelniania stacji roboczej do pliku, można go zaimportować do właściwości punktu dystrybucji.  

##### <a name="to-export-the-client-certificate-for-distribution-points"></a>Aby wyeksportować certyfikat klienta dla punktów dystrybucji  

1.  W **certyfikaty (komputer lokalny)** konsoli, kliknij prawym przyciskiem myszy właśnie zainstalowany certyfikat, wybierz polecenie **wszystkie zadania**, a następnie wybierz **wyeksportować**.  

2.  W Kreatorze eksportu certyfikatów wybierz **dalej**.  

3.  Na **eksportowanie klucza prywatnego** wybierz **tak, Eksportuj klucz prywatny**, a następnie wybierz **dalej**.  

    > [!NOTE]  
    >  Jeżeli ta opcja nie jest dostępna, certyfikat został utworzony bez opcji eksportu klucza prywatnego. W tym scenariuszu nie można wyeksportować certyfikatu w wymaganym formacie. Należy skonfigurować szablon certyfikatu, aby klucz prywatny można eksportować i zażądać certyfikatu ponownie.  

4.  Na **Format pliku eksportu** strony, upewnij się, że **wymiany informacji osobistych — PKCS #12 (. PFX)** opcja jest zaznaczona.  

5.  Na **hasło** Określ silne hasło, aby zabezpieczyć wyeksportowany certyfikat kluczem prywatnym, a następnie wybierz **dalej**.  

6.  Na **Eksport pliku** Określ nazwę pliku, który chcesz wyeksportować, a następnie wybierz **dalej**.  

7.  Aby zamknąć kreatora, wybierz **Zakończ** na **Kreatora eksportu certyfikatów** strony i wybierz polecenie **OK** w oknie dialogowym potwierdzenia.  

8.  Zamknij konsolę **Certyfikaty (komputer lokalny)**.  

9. Zapisz plik w bezpiecznym miejscu i upewnij się, że można do niego dostęp z konsoli programu System Center Configuration Manager.  

 Certyfikat jest teraz gotowy do zaimportowania podczas konfigurowania punktu dystrybucji.  

> [!TIP]  
>  Można użyć tego samego pliku certyfikatu, konfigurując obrazy nośników do wdrożenia systemu operacyjnego, które nie używają rozruchu PXE i sekwencji zadań w celu instalacji obrazu musi kontaktować się z punktem zarządzania wymagającym połączeń klienckich HTTPS.  

##  <a name="BKMK_mobiledevices2008_cm2012"></a>Wdrażanie certyfikatu rejestracji dla urządzeń przenośnych  
 W tym wdrożeniu certyfikatu zarówno utworzenie, jak i wystawienie szablonu certyfikatu rejestracji w urzędzie certyfikacji jest objęte tą samą procedurą.  

### <a name="create-and-issue-the-enrollment-certificate-template-on-the-certification-authority"></a>Utwórz i wystaw szablon certyfikatu rejestracji w urzędzie certyfikacji  
 Ta procedura powoduje utworzenie szablonu certyfikatu rejestracji dla urządzeń przenośnych programu System Center Configuration Manager i dodanie go do urzędu certyfikacji.  

##### <a name="to-create-and-issue-the-enrollment-certificate-template-on-the-certification-authority"></a>Aby utworzyć i wystawić szablon certyfikatu rejestracji w urzędzie certyfikacji  

1.  Utwórz grupę zabezpieczeń zawierającą użytkowników, którzy będą rejestrować urządzenia przenośne w programie System Center Configuration Manager.  

2.  Na serwerze członkowskim z usługami certyfikatów zainstalowane, w konsoli Urząd certyfikacji kliknij prawym przyciskiem myszy **szablonów certyfikatów**, a następnie wybierz **Zarządzaj** załadować Konsolę zarządzania szablonami certyfikatów.  

3.  W okienku wyników kliknij prawym przyciskiem myszy wpis **sesja uwierzytelniona** w **Nazwa wyświetlana szablonu** kolumny, a następnie wybierz **Duplikuj szablon**.  

4.  W **Duplikuj szablon** dialogowe Sprawdź, czy **systemu Windows Server 2003, Enterprise Edition** jest zaznaczone, a następnie wybierz **OK**.  

    > [!IMPORTANT]  
    >  Nie wybieraj systemu **Windows 2008 Server, Enterprise Edition**.  

5.  W **właściwości nowego szablonu** okna dialogowego na **ogólne** , wprowadź nazwę szablonu, jak **certyfikat rejestracji urządzeń przenośnych programu ConfigMgr**, w celu wygenerowania certyfikatów rejestracji dla urządzeń przenośnych, które mają być zarządzane przez program System Center Configuration Manager.  

6.  Wybierz **nazwa podmiotu** i upewnij się, że **Konstruuj z tej informacji usługi Active Directory** jest wybrany, wybierz pozycję **nazwa pospolita** dla **format nazwy podmiotu:**, a następnie wyczyść **główna nazwa użytkownika (UPN)** z **Dołącz tę informację do alternatywnej nazwy podmiotu**.  

7.  Wybierz **zabezpieczeń** karcie, wybrać grupę zabezpieczeń zawierającą użytkowników z urządzeniami przenośnymi do zarejestrowania i wybierz uprawnienie dodatkowe **rejestracja**. Nie usuwaj zaznaczenia opcji **Odczyt**.  

8.  Wybierz **OK**, a następnie Zamknij **konsoli Szablony certyfikatów**.  

9. W konsoli Urząd certyfikacji kliknij prawym przyciskiem myszy **szablonów certyfikatów**, wybierz **nowy**, a następnie wybierz **szablon certyfikatu do wystawienia**.  

10. W **Włączanie szablonu certyfikatu** okno dialogowe, wybierz nowego szablonu, który został właśnie utworzony, **certyfikat rejestracji urządzeń przenośnych programu ConfigMgr**, a następnie wybierz **OK**.  

11. Jeśli nie są potrzebne do tworzenia i wystawiania certyfikatów, zamknij konsolę Urząd certyfikacji.  

 Szablon certyfikatu rejestracji urządzeń przenośnych jest teraz gotowy do wybrania podczas konfigurowania profilu rejestracji urządzenia przenośnego w ustawieniach klienta.  

##  <a name="BKMK_AMT2008_cm2012"></a>Wdrażanie certyfikatów dla komputerów AMT  
 Wdrożenie tego certyfikatu jest objęte następującymi procedurami:  

-   Tworzenie, wydawania i instalowanie certyfikatu udostępniania AMT  

-   Utwórz i wystaw certyfikat serwera sieci web dla komputerów opartych na technologii AMT  

-   Utwórz i wystaw certyfikaty uwierzytelniania 802.1 X AMT komputery klienta  

###  <a name="BKMK_AMTprovisioning2008"></a>Tworzenie, wydawania i instalowanie certyfikatu udostępniania AMT  
 Z wewnętrznego urzędu certyfikacji należy utworzyć certyfikat udostępniania, gdy komputery oparte na technologii AMT są skonfigurowane z odciskiem palca wewnętrzny główny urząd certyfikacji. Kiedy nie jest to i należy użyć zewnętrznego urzędu certyfikacji, należy postępować zgodnie z instrukcjami firmy, który wystawił certyfikat udostępniania AMT, co może często oznaczać między innymi żądanie certyfikatu za pośrednictwem publicznej witryny sieci web danej firmy. Można także znaleźć szczegółowe informacje na temat wybranego zewnętrznego urzędu certyfikacji [Intel vPro Expert Center: Witryny sieci web Microsoft vPro Manageability](http://go.microsoft.com/fwlink/?LinkId=132001).  

> [!IMPORTANT]  
>  Zewnętrzne urzędy certyfikacji mogą nie obsługiwać identyfikatora obiektu udostępniania Intel AMT. W takim przypadku należy podać **Intel(R) Client Setup Certificate** atrybut jednostki Organizacyjnej.  

 W przypadku żądania certyfikatu udostępniania AMT od zewnętrznego urzędu certyfikacji, należy zainstalować certyfikat w magazynie certyfikatów osobistych komputera na serwerze członkowskim, który będzie hostem punktu Usługi poza pasmem.  

##### <a name="to-request-and-issue-the-amt-provisioning-certificate"></a>Aby zażądać certyfikatu udostępniania AMT i go wystawić  

1.  Utwórz grupę zabezpieczeń zawierającą konta komputerów serwerów systemu lokacji, z których będzie uruchamiany punkt obsługi poza pasmem.  

2.  Na serwerze członkowskim z usługami certyfikatów zainstalowane, w konsoli Urząd certyfikacji kliknij prawym przyciskiem myszy **szablonów certyfikatów**, a następnie wybierz **Zarządzaj** załadować **szablonów certyfikatów** konsoli.  

3.  W okienku wyników kliknij prawym przyciskiem myszy wpis **serwera sieci Web** w **Nazwa wyświetlana szablonu** kolumny, a następnie wybierz **Duplikuj szablon**.  

4.  W **Duplikuj szablon** dialogowe Sprawdź, czy **systemu Windows Server 2003, Enterprise Edition** jest zaznaczone, a następnie wybierz **OK**.  

    > [!IMPORTANT]  
    >  Nie wybieraj systemu **Windows 2008 Server, Enterprise Edition**.  

5.  W **właściwości nowego szablonu** okna dialogowego na **ogólne** , wprowadź nazwę szablonu, jak **udostępniania AMT programu ConfigMgr**, dla szablonu certyfikatu udostępniania AMT.  

6.  Wybierz **nazwa podmiotu** , wybierz **Konstruuj z tej informacji usługi Active Directory**, a następnie wybierz **nazwa pospolita**.  

7.  Wybierz **rozszerzenia** i upewnij się, że **zasady aplikacji** jest zaznaczone, a następnie wybierz **edytować**.  

8.  W **Edytowanie rozszerzenia zasad aplikacji** okno dialogowe Wybierz **Dodaj**.  

9. W **Dodawanie zasady aplikacji** okno dialogowe Wybierz **nowy**.  

10. W **Nowa zasada aplikacji** dialogowe wprowadź **udostępniania AMT** w **nazwa** pola, a następnie wpisz następujący ciąg liczb w **identyfikator obiektu**: **2.16.840.1.113741.1.2.3**.  

11. Wybierz **OK**, a następnie wybierz **OK** w **Dodawanie zasady aplikacji** okno dialogowe.  

12. Wybierz **OK** w **Edytowanie rozszerzenia zasad aplikacji** okno dialogowe.  

13. W **właściwości nowego szablonu** następujące okno dialogowe jest wyświetlane jako **zasady aplikacji** opis: **Uwierzytelnianie serwera** i **udostępniania AMT**.  

14. Wybierz **zabezpieczeń** karcie, a następnie usuń **rejestracja** zgody **Administratorzy domeny** i **Administratorzy przedsiębiorstwa** grup zabezpieczeń.  

15. Wybierz **Dodaj**, wprowadź nazwę grupy zabezpieczeń, która ma konto komputera dla roli systemu lokacji punktu Usługi poza pasmem, a następnie wybierz **OK**.  

16. Wybierz **rejestracja** dla tej grupy uprawnienie i nie usuwaj **odczytu** uprawnienie...  

17. Wybierz **OK**, a następnie Zamknij **szablonów certyfikatów** konsoli.  

18. W **urząd certyfikacji**, kliknij prawym przyciskiem myszy **szablonów certyfikatów**, wybierz **nowy**, a następnie wybierz **szablon certyfikatu do wystawienia**.  

19. W **Włączanie szablonu certyfikatu** okno dialogowe, wybierz nowego szablonu, który został właśnie utworzony, **udostępniania AMT programu ConfigMgr**, a następnie wybierz **OK**.  

    > [!NOTE]  
    >  Jeśli nie możesz ukończyć kroku 18 lub 19, sprawdź, czy na pewno korzystasz z systemu Windows Server 2008 w wersji Enterprise Edition. Mimo że można skonfigurować szablony z systemu Windows Server Standard Edition oraz usług certyfikatów, nie można wdrażać certyfikatów przy użyciu zmodyfikowanych szablonów certyfikatów, chyba że w przypadku korzystania z systemu Windows Server 2008 Enterprise Edition.  

20. Nie zamykaj konsoli **Urząd certyfikacji**.  

 Certyfikat udostępniania AMT z wewnętrznego urzędu certyfikacji jest teraz gotowy do zainstalowania na komputerze punktu obsługi poza pasmem.  

##### <a name="to-install-the-amt-provisioning-certificate"></a>Aby zainstalować certyfikat udostępniania AMT  

1.  Uruchom ponownie serwer członkowski, z uruchomionymi usługami IIS, aby upewnić się, że można uzyskać dostęp do szablonu certyfikatu przy użyciu skonfigurowanych uprawnień.  

2.  Wybierz **Start**, wybierz **Uruchom**, a następnie wprowadź **mmc.exe.** W pustej konsoli kliknij **pliku**, a następnie wybierz **Dodaj/Usuń przystawkę**.  

3.  W **Dodawanie lub usuwanie przystawek** okno dialogowe Wybierz **certyfikaty** z listy **dostępne przystawki**, a następnie wybierz **Dodaj**.  

4.  W **certyfikatów w przystawce** okno dialogowe Wybierz **konto komputera**, a następnie wybierz **dalej**.  

5.  W **wybierz komputer** okna dialogowego Sprawdź, czy **komputer lokalny: (komputer ten jest uruchomiona konsola)** jest zaznaczone, a następnie wybierz **Zakończ**.  

6.  W **Dodawanie lub usuwanie przystawek** okno dialogowe Wybierz **OK**.  

7.  W konsoli rozwiń **certyfikaty (komputer lokalny)**, a następnie wybierz **osobiste**.  

8.  Kliknij prawym przyciskiem myszy **certyfikaty**, wybierz **wszystkie zadania**, a następnie wybierz **Żądaj nowego certyfikatu**.  

9. Na **przed rozpoczęciem** wybierz **dalej**.  

10. Jeśli widzisz **wybierz zasady rejestracji certyfikatu** wybierz **dalej**.  

11. Na **Żądaj certyfikatów** wybierz opcję **udostępniania AMT** z listy dostępnych certyfikatów, a następnie wybierz **rejestracja**.  

12. Na **wyniki instalacji certyfikatów** , poczekaj, aż certyfikat został zainstalowany, a następnie wybierz **Zakończ**.  

13. Zamknij konsolę **Certyfikaty (komputer lokalny)**.  

 Certyfikat udostępniania AMT z wewnętrznego urzędu certyfikacji jest teraz zainstalowany i jest gotowy do wybrania we właściwościach punktu obsługi poza pasmem.  

### <a name="create-and-issue-the-web-server-certificate-for-amt-based-computers"></a>Utwórz i wystaw certyfikat serwera sieci web dla komputerów opartych na technologii AMT  
 Użyj poniższej procedury, aby przygotować certyfikaty serwera sieci Web dla komputerów opartych na technologii AMT.  

##### <a name="to-create-and-issue-the-web-server-certificate-template"></a>Aby utworzyć i wystawić szablon certyfikatu serwera sieci web  

1.  Utwórz grupy zabezpieczeń pusty, która zawiera konta komputerów AMT tworzone podczas udostępniania AMT System Center Configuration Manager.  

2.  Na serwerze członkowskim z usługami certyfikatów zainstalowane, w konsoli Urząd certyfikacji kliknij prawym przyciskiem myszy **szablonów certyfikatów**, a następnie wybierz **Zarządzaj** załadować **szablonów certyfikatów** konsoli.  

3.  W okienku wyników kliknij prawym przyciskiem myszy wpis **serwera sieci Web** w **Nazwa wyświetlana szablonu** kolumny, a następnie wybierz **Duplikuj szablon**.  

4.  W **Duplikuj szablon** dialogowe Sprawdź, czy **systemu Windows Server 2003, Enterprise Edition** jest zaznaczone, a następnie wybierz **OK**.  

    > [!IMPORTANT]  
    >  Nie wybieraj systemu **Windows 2008 Server, Enterprise Edition.**  

5.  W **właściwości nowego szablonu** okna dialogowego na **ogólne** , wprowadź nazwę szablonu, jak **certyfikatu serwera sieci Web AMT programu ConfigMgr**, w celu wygenerowania certyfikatów sieci web, które będą używane do zarządzania poza pasmem na komputerach AMT.  

6.  Wybierz **nazwa podmiotu** , wybierz **Konstruuj z tej informacji usługi Active Directory**, wybierz **nazwa pospolita** dla **format nazwy podmiotu**, a następnie wyczyść **główna nazwa użytkownika (UPN)** dla alternatywnej nazwy podmiotu.  

7.  Wybierz **zabezpieczeń** karcie, a następnie usuń **rejestracja** zgody **Administratorzy domeny** i **Administratorzy przedsiębiorstwa** grup zabezpieczeń.  

8.  Wybierz **Dodaj**i wprowadź nazwę grupy zabezpieczeń utworzonej dla udostępniania AMT, a następnie wybierz **OK**.  

9. Wybierz następujące **Zezwalaj** uprawnienia dla tej grupy zabezpieczeń: **Odczyt** i **zarejestrować**.  

10. Wybierz **OK**, a następnie Zamknij **szablonów certyfikatów** konsoli.  

11. W **urząd certyfikacji** konsoli, kliknij prawym przyciskiem myszy **szablonów certyfikatów**, wybierz **nowy**, a następnie wybierz **szablon certyfikatu do wystawienia**.  

12. W **Włączanie szablonu certyfikatu** okno dialogowe, wybierz nowego szablonu, który został właśnie utworzony, **certyfikatu serwera sieci Web AMT programu ConfigMgr**, a następnie wybierz **OK**.  

13. Jeśli nie masz tworzenia i wystawiania certyfikatów Zamknij **urząd certyfikacji**.  

 Szablon serwera sieci Web AMT jest teraz gotowy do konfigurowania komputerów opartych na technologii AMT certyfikatów serwera sieci web. Wybierz ten szablon certyfikatu we właściwościach składnika zarządzania poza pasmem.  

### <a name="create-and-issue-the-client-authentication-certificates-for-8021x-amt-based-computers"></a>Utwórz i wystaw certyfikaty uwierzytelniania 802.1 X AMT komputery klienta  
 Użyj poniższej procedury, jeśli komputery oparte na technologii AMT będą używać certyfikatów klienta dla uwierzytelnianych sieci przewodowych i bezprzewodowych 802.1X.  

##### <a name="to-create-and-issue-the-client-authentication-certificate-template-on-the-ca"></a>Aby utworzyć i wydać szablon certyfikatu uwierzytelniania klienta w urzędzie certyfikacji  

1.  Na serwerze członkowskim z usługami certyfikatów zainstalowane, w konsoli Urząd certyfikacji kliknij prawym przyciskiem myszy **szablonów certyfikatów**, a następnie wybierz **Zarządzaj** załadować **szablonów certyfikatów** konsoli.  

2.  W okienku wyników kliknij prawym przyciskiem myszy wpis **Uwierzytelnianie stacji roboczej** w **Nazwa wyświetlana szablonu** kolumny, a następnie wybierz **Duplikuj szablon**.  

    > [!IMPORTANT]  
    >  Nie wybieraj systemu **Windows 2008 Server, Enterprise Edition.**  

3.  W **właściwości nowego szablonu** okna dialogowego na **ogólne** , wprowadź nazwę szablonu, jak **certyfikat uwierzytelniania klienta programu ConfigMgr AMT 802.1 X**, w celu wygenerowania certyfikatów klienta, które będą używane do zarządzania poza pasmem na komputerach AMT.  

4.  Wybierz **nazwa podmiotu** , wybierz **Konstruuj z tej informacji usługi Active Directory**, a następnie wybierz **nazwa pospolita** dla **format nazwy podmiotu**. Wyczyść **nazwy DNS** dla podmiotu alternatywnych nazw, a następnie wybierz **główna nazwa użytkownika (UPN)**.  

5.  Wybierz **zabezpieczeń** karcie, a następnie usuń **rejestracja** zgody **Administratorzy domeny** i **Administratorzy przedsiębiorstwa** grup zabezpieczeń.  

6.  Wybierz **Dodaj**, wprowadź nazwę grupy zabezpieczeń, który zostanie określone we właściwościach składnika zarządzania poza pasmem zawiera konta komputerów opartych na technologii AMT, a następnie wybierz **OK**.  

7.  Wykonaj następujące czynności **Zezwalaj** uprawnienia dla tej grupy zabezpieczeń: **Odczyt** i **zarejestrować**.  

8.  Wybierz **OK**, a następnie Zamknij **szablonów certyfikatów** konsoli zarządzania **certtmpl - [szablony certyfikatów]**.  

9. W **urząd certyfikacji** konsoli zarządzania kliknij prawym przyciskiem myszy **szablonów certyfikatów**, wybierz **nowy**, a następnie wybierz **szablon certyfikatu do wystawienia**.  

10. W **Włączanie szablonu certyfikatu** okno dialogowe, wybierz nowego szablonu, który został właśnie utworzony, **certyfikat uwierzytelniania klienta programu ConfigMgr AMT 802.1 X**, a następnie wybierz **OK**.  

11. Jeśli nie ma potrzeby tworzenia i wystawiania certyfikatów Zamknij **urząd certyfikacji**.  

 Szablon certyfikatu uwierzytelniania klienta jest teraz gotowy do wystawiania komputerom opartym na technologii AMT certyfikatów, których można będzie użyć do uwierzytelniania klientów 802.1X. Wybierz ten szablon certyfikatu we właściwościach składnika zarządzania poza pasmem.  

##  <a name="BKMK_MacClient_SP1"></a>Wdrażanie certyfikatu klienta dla komputerów Mac  

W tym wdrożeniu certyfikatu zarówno utworzenie, jak i wystawienie szablonu certyfikatu rejestracji w urzędzie certyfikacji jest objęte tą samą procedurą.  

###  <a name="BKMK_MacClient_CreatingIssuing"></a>Utwórz i wystaw szablon certyfikatu w urzędzie certyfikacji klienta Mac  
 Ta procedura powoduje utworzenie niestandardowego szablonu certyfikatu dla komputerów Mac programu System Center Configuration Manager i dodanie szablonu certyfikatu do urzędu certyfikacji.  

> [!NOTE]  
>  Ta procedura korzysta z innego szablonu certyfikatu niż szablony certyfikatów, które być może utworzono wcześniej dla klientów z systemem Windows lub dla punktów dystrybucji.  
>   
>  Podczas tworzenia nowego szablonu certyfikatu dla tego certyfikatu, możesz ograniczyć żądanie certyfikatu do użytkowników autoryzowanych.  

##### <a name="to-create-and-issue-the-mac-client-certificate-template-on-the-certification-authority"></a>Aby utworzyć i wydać szablon certyfikatu klienta Mac w urzędzie certyfikacji  

1.  Utwórz grupę zabezpieczeń zawierającą konta użytkownika dla użytkowników administracyjnych, którzy będą rejestrowali ten certyfikat na komputerze Mac za pomocą programu System Center Configuration Manager.  

2.  Na serwerze członkowskim, na którym jest uruchomiona konsola urzędu certyfikacji, kliknij prawym przyciskiem myszy **szablonów certyfikatów**, a następnie wybierz **Zarządzaj** załadować Konsolę zarządzania szablonami certyfikatów.  

3.  W okienku wyników kliknij prawym przyciskiem myszy wpis opisany jako **sesja uwierzytelniona** w **Nazwa wyświetlana szablonu** kolumny, a następnie wybierz **Duplikuj szablon**.  

4.  W **Duplikuj szablon** dialogowe Sprawdź, czy **systemu Windows Server 2003, Enterprise Edition** jest zaznaczone, a następnie wybierz **OK**.  

    > [!IMPORTANT]  
    >  Nie wybieraj systemu **Windows 2008 Server, Enterprise Edition**.  

5.  W **właściwości nowego szablonu** okna dialogowego na **ogólne** , wprowadź nazwę szablonu, jak **certyfikat klienta Mac ConfigMgr**, aby wygenerować certyfikat klienta Mac.  

6.  Wybierz **nazwa podmiotu** i upewnij się, że **Konstruuj z tej informacji usługi Active Directory** jest zaznaczony, wybierz **nazwa pospolita** dla **format nazwy podmiotu:**, a następnie wyczyść **główna nazwa użytkownika (UPN)** z **Dołącz tę informację do alternatywnej nazwy podmiotu**.  

7.  Wybierz **zabezpieczeń** karcie, a następnie usuń **rejestracja** zgody **Administratorzy domeny** i **Administratorzy przedsiębiorstwa** grup zabezpieczeń.  

8.  Wybierz **Dodaj**, określ grupę zabezpieczeń utworzoną w pierwszym kroku, a następnie wybierz **OK**.  

9. Wybierz **rejestracja** dla tej grupy uprawnienie i nie usuwaj **odczytu** uprawnienia.  

10. Wybierz **OK**, a następnie Zamknij **konsoli Szablony certyfikatów**.  

11. W konsoli Urząd certyfikacji kliknij prawym przyciskiem myszy **szablonów certyfikatów**, wybierz **nowy**, a następnie wybierz **szablon certyfikatu do wystawienia**.  

12. W **Włączanie szablonu certyfikatu** okno dialogowe, wybierz nowego szablonu, który został właśnie utworzony, **certyfikat klienta Mac ConfigMgr**, a następnie wybierz **OK**.  

13. Jeśli nie masz tworzenia i wystawiania certyfikatów Zamknij **urząd certyfikacji**.  

 Szablon certyfikatu klienta Mac jest teraz gotowy do wybrania podczas konfigurowania ustawień klienta do rejestracji.

