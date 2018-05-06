---
title: Modyfikowanie infrastruktury
titleSuffix: Configuration Manager
description: Dowiedz się, jak wprowadzić zmiany lub wykonać akcje, które mają wpływ na infrastruktury programu Configuration Manager, które zostały wdrożone.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: a7975dc8-46ab-4dae-86b6-dc3e3cf3b2f0
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 7f798fdb1183b852bded92711cc5f489666f4f2a
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="modify-your-system-center-configuration-manager-infrastructure"></a>Modyfikowanie infrastruktury programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Po zainstalowaniu co najmniej jednej lokacji może zaistnieć potrzeba zmodyfikowania konfiguracji lub podjęcia działań, które będą miały wpływ na wdrożoną infrastrukturę.  


##  <a name="BKMK_ManageSMSprovider"></a> Zarządzanie dostawcą programu SMS  
 Dostawca programu SMS (plik biblioteki dołączanej: smsprov.dll) zapewnia konsolom programu Configuration Manager punkt kontaktu administracyjnego. W przypadku instalowania wielu dostawców programu SMS można zapewnić nadmiarowość punktów kontaktu w celu administrowania lokacją i hierarchią.  

 W każdej lokacji programu Configuration Manager można ponownie uruchomić Instalatora, aby:  

-   Dodania dodatkowego wystąpienia dostawcy programu SMS (każde dodatkowe wystąpienie dostawcy programu SMS musi być na innym komputerze)  

-   Usuwanie wystąpienia dostawcy programu SMS (Aby usunąć ostatniego dostawcę programu SMS dla lokacji, należy odinstalować lokację)  

 Instalację lub usuwanie dostawcy programu SMS można monitorować, przeglądając dziennik **ConfigMgrSetup.log** w folderze głównym serwera lokacji, na którym jest uruchamiany Instalator.  

 Przed zmodyfikowaniem dostawcy programu SMS w lokacji należy zapoznać się z informacjami w temacie [Planowanie dostawcy programu SMS dla programu System Center Configuration Manager](../../../core/plan-design/hierarchy/plan-for-the-sms-provider.md).  

#### <a name="to-manage-the-sms-provider-configuration-for-a-site"></a>Aby zarządzać konfiguracją dostawcy programu SMS dla lokacji  

1.  Uruchom **Instalatora programu Configuration Manager** z  **&lt;folder instalacji lokacji programu Configuration Manager\>\BIN\X64\setup.exe**.  

2.  Na stronie **Pierwsze kroki** wybierz pozycję **Przeprowadź obsługę lokacji lub zresetuj tę lokację**, a następnie kliknij przycisk **Dalej**.  

3.  Na stronie **Obsługa lokacji** wybierz pozycję **Modyfikuj konfigurację dostawcy programu SMS**, a następnie kliknij przycisk **Dalej**.  

4.  Na stronie **Zarządzanie dostawcami programu SMS** wybierz jedną z poniższych opcji i zgodnie z nią dokończ działanie kreatora:  

    -   Aby dodać w witrynie dodatkowego dostawcę programu SMS:  

         Wybierz pozycję **Dodaj nowego dostawcę programu SMS**, określ nazwę FQDN komputera, który będzie — a aktualnie nie jest — hostem dostawcy programu SMS, a następnie kliknij przycisk **Dalej**.  

    -   Aby usunąć dostawcę programu SMS z serwera:  

         Wybierz opcję **Odinstaluj określonego dostawcę programu SMS**, wybierz nazwę komputera, z którego chcesz usunąć dostawcę programu SMS, kliknij przycisk **Dalej**, a następnie potwierdź tę akcję.  

        > [!TIP]  
        >  Aby przenieść dostawcę programu SMS między dwoma komputerami, należy zainstalować dostawcę programu SMS na nowym komputerze, a potem usunąć dostawcę programu SMS z lokalizacji początkowej. Nie ma osobnej opcji, która służyłaby przeniesieniu dostawcy programu SMS między komputerami w ramach jednego procesu.  

 Po zakończeniu działania Kreatora instalacji konfiguracja dostawcy programu SMS zostanie ukończona. Na karcie **Ogólne** w oknie dialogowym **Właściwości** danej lokacji można zweryfikować komputery, które mają zainstalowanego dostawcę programu SMS dla jednej z lokacji.  

##  <a name="bkmk_Console"></a> Zarządzanie konsoli programu Configuration Manager  
 Poniżej przedstawiono zadania, które można wykonywać, aby zarządzać konsoli programu Configuration Manager:  

-   **Modyfikowanie języka wyświetlanego w konsoli programu Configuration Manager** — Aby zmodyfikować zainstalowane języki, zobacz sekcję [język konsoli zarządzania programu Configuration Manager](#BKMK_ManageConsoleLanguages) w tym temacie.  

-   **Instalowanie dodatkowych konsol** — Aby zainstalować dodatkowe konsole, zobacz [konsole instalacji programu System Center Configuration Manager](/sccm/core/servers/deploy/install/install-consoles).  

-   **Konfigurowanie modelu DCOM** — Aby skonfigurować uprawnienia modelu DCOM umożliwia konsolom sterowanym zdalnie z serwera lokacji do połączenia, zobacz [skonfigurować uprawnienia modelu DCOM dla zdalnej konsoli programu Configuration Manager](#BKMK_ConfigDCOMforRemoteConsole) w tym temacie.  

-   **Modyfikowanie uprawnień w celu ograniczenia, co użytkownicy administracyjni mogą wyświetlać w konsoli** — Aby zmodyfikować uprawnienia administracyjne ograniczające co użytkownicy mogą i w konsoli można znaleźć [modyfikacja zakresu administracyjnego użytkownika administracyjnego ](/sccm/core/servers/deploy/configure/configure-role-based-administration#BKMK_ModAdminUser).     

###  <a name="BKMK_ManageConsoleLanguages"></a> Zarządzanie językiem konsoli programu Configuration Manager  
 Podczas instalacji serwera lokacji pliki instalacyjne konsoli programu Configuration Manager oraz obsługiwane pakiety języków lokacji są kopiowane do  **&lt;Ścieżka_instalacji_programu_configmgr\>\Tools\ConsoleSetup** podfolderu na serwerze lokacji.  

-   Po rozpoczęciu instalacji konsoli programu Configuration Manager z tego folderu na serwerze lokacji, konsola programu Configuration Manager i pliki pakietu obsługiwanego języka są kopiowane do komputera  

-   Gdy pakiet języka jest dostępny z bieżącym ustawieniem języka na komputerze, w tym języku otwarciu konsoli programu Configuration Manager  

-   Jeśli powiązany pakiet języka nie jest dostępny dla konsoli programu Configuration Manager, konsola otworzy się w języku angielskim  

Na przykład Rozważmy scenariusz, w którym zainstalowano konsolę programu Configuration Manager z serwera lokacji obsługującego język angielski, niemiecki i francuski. Po otwarciu konsoli programu Configuration Manager na komputerze z skonfigurowano ustawienie języka francuskiego, konsola otworzy się w języku francuskim. Po otwarciu konsoli programu Configuration Manager na komputerze ze skonfigurowanym ustawieniem języka japońskiego, konsola otworzy w języku angielskim, ponieważ pakiet języka japońskiego nie będzie dostępny.  

 Zawsze, gdy zostanie otwarta konsola programu Configuration Manager, on określa ustawień języka skonfigurowanych na komputerze, sprawdza, czy powiązany pakiet języka jest dostępny dla konsoli programu Configuration Manager, a następnie otworzeniem konsoli przy użyciu odpowiedniego pakietu języka. Aby otworzyć konsolę programu Configuration Manager w języku angielskim niezależnie od ustawień języka skonfigurowanych na komputerze, należy ręcznie należy usunąć albo zmienić pliki pakietu języka na komputerze.  

 Aby uruchomić konsolę programu Configuration Manager w języku angielskim niezależnie od ustawień regionalnych skonfigurowanych na komputerze, należy użyć poniższych procedur.  

##### <a name="to-install-an-english-only-version-of-the-configuration-manager-console-on-computers"></a>Aby zainstalować wyłącznie anglojęzyczną wersję konsoli programu Configuration Manager na komputerach  

1.  W Eksploratorze Windows przejdź do  **&lt;Ścieżka_instalacji_programu_configmgr\>\Tools\ConsoleSetup\LanguagePack**  

2.  Zmień nazwy plików **msp** i **mst**. Możesz na przykład zmienić nazwę **&lt;nazwa pliku\>.MSP na** **&lt;nazwa pliku\>.MSP.disabled**.  

3.  Zainstaluj konsolę programu Configuration Manager na komputerze.  

    > [!IMPORTANT]  
    >  Po skonfigurowaniu nowych języków dla serwera lokacji, pliki .msp i .mst zostaną ponownie skopiowane do **LanguagePack** folderu, na które należy powtórzyć całą procedurę, aby zainstalować nowe konsole programu Configuration Manager wyłącznie w języku angielskim.  

##### <a name="to-temporarily-disable-a-console-language-on-an-existing-configuration-manager-console-installation"></a>Aby tymczasowo wyłączyć język konsoli w istniejącej instalacji konsoli programu Configuration Manager  

1.  Na komputerze, na którym jest uruchomiona konsola programu Configuration Manager Zamknij konsolę programu Configuration Manager.  

2.  W Eksploratorze Windows przejdź do &lt; *Ścieżka_instalacji_konsoli*> \Bin\ na komputerze konsoli programu Configuration Manager.  

3.  Zmień nazwę odpowiedniego folderu języka skonfigurowanego na komputerze. Jeśli na przykład ustawienia języka komputera skonfigurowano na język niemiecki, można zmienić nazwę folderu **de** na **de.disabled**.  

4.  Aby otworzyć konsolę programu Configuration Manager w języku skonfigurowanym na komputerze, Zmień nazwę folderu oryginalną nazwę. Na przykład zmień nazwę folderu **de.disabled** na **de**.  

##  <a name="BKMK_ConfigDCOMforRemoteConsole"></a> Konfigurowanie uprawnień modelu DCOM dla zdalnej konsoli programu Configuration Manager  
 Konto użytkownika, na którym uruchomiona jest konsola programu Configuration Manager wymaga uprawnień dostępu do bazy danych lokacji za pomocą dostawcy programu SMS. Jednak użytkownik administracyjny używający zdalnej konsoli programu Configuration Manager wymaga również **aktywacji zdalnej** uprawnień modelu DCOM na:  

-   komputerze serwera lokacji;  

-   każdym komputerze, na którym znajduje się wystąpienie dostawcy programu SMS.  

 Dostępu do dostawcy programu SMS na komputerze udziela grupa zabezpieczeń **Administratorzy programu SMS**, która może też służyć do udzielenia wymaganych uprawnień dotyczących modelu DCOM. (Ta grupa jest lokalnych dla komputera, gdy dostawca programu SMS działa na serwerze członkowskim i jest grupą lokalną domeny, gdy dostawca programu SMS działa na kontrolerze domeny).  

> [!IMPORTANT]  
>  Konsola programu Configuration Manager używa Instrumentacji zarządzania Windows (WMI) do łączenia się z dostawcą programu SMS, a WMI wewnętrznie używa modelu DCOM. W związku z tym program Configuration Manager wymaga uprawnień do aktywacji serwera DCOM na komputerze dostawcy programu SMS, jeśli konsola programu Configuration Manager jest uruchomiona na komputerze innym niż komputer dostawcy programu SMS. Domyślnie aktywacji zdalnej otrzymuje się tylko członkom wbudowanej grupy administratorów. W przypadku przyznania uprawnienia do aktywacji zdalnej całej grupie Administratorzy programu SMS członek tej grupy mógłby próbować ataków DCOM na komputer dostawcy programu SMS. Taka konfiguracja zwiększa także obszar komputera narażony na ataki. Aby osłabić to zagrożenie, należy starannie monitorować członkostwo w grupie Administratorzy programu SMS.  

 Użyj poniższej procedury można skonfigurować każdą lokację administracji centralnej serwera lokacji głównej i każdy komputer z zainstalowanym dostawcą programu SMS można udzielić dostępu do konsoli dla użytkowników administracyjnych zdalnego programu Configuration Manager.  

#### <a name="to-configure-dcom-permissions-for-remote-configuration-manager-console-connections"></a>Aby skonfigurować uprawnienia modelu DCOM dotyczące zdalnych połączeń z konsolą programu Configuration Manager  

1.  Otwórz okno dialogowe **Usługi składowe**, uruchamiając plik **Dcomcnfg.exe**.  

2.  W **usługi składowe**, kliknij przycisk **katalog główny konsoli** >  **usługi składowe** > **komputerów**, a następnie kliknij przycisk **Mój komputer**. W menu **Akcja** kliknij polecenie **Właściwości**.  

3.  W oknie dialogowym **Właściwości mojego komputera** na karcie **Zabezpieczenia COM** w sekcji **Uprawnienia uruchamiania i aktywacji** kliknij przycisk **Edytuj limity**.  

4.  W oknie dialogowym **Uprawnienia uruchamiania i aktywacji** kliknij przycisk **Dodaj**.  

5.  W **Wybieranie użytkowników, komputerów, kont usług lub grup** okna dialogowego, **wprowadź nazwy obiektów do wybrania (przykłady)** wpisz **Administratorzy programu SMS**, a następnie kliknij przycisk **OK**.  

    > [!NOTE]  
    >  Aby móc odnaleźć grupę Administratorzy programu SMS, może być konieczna zmiana ustawienia w polu **Z tej lokalizacji**. Grupa jest lokalną grupą komputera, kiedy dostawca programu SMS jest uruchamiany na serwerze członkowskim, i jest grupą lokalną domeny, kiedy dostawca programu SMS działa na kontrolerze domeny.  

6.  W sekcji **Uprawnienia administratorów programu SMS**, w celu zezwolenia na aktywację zdalną, zaznacz pole wyboru **Aktywacja zdalna**.  

7.  Kliknij przycisk **OK**, ponownie kliknij przycisk **OK**, a następnie zamknij okno **Zarządzanie komputerem**. Komputer jest teraz skonfigurowane i umożliwiają zdalne programu Configuration Manager dostęp do członków grupy Administratorzy programu SMS.  

 Powtórz tę procedurę na każdym komputerze dostawcy programu SMS, który ma obsługiwać zdalne konsole programu Configuration Manager.  

##  <a name="bkmk_dbconfig"></a> Modyfikowanie konfiguracji bazy danych lokacji  
 Po zainstalowaniu lokacji można zmodyfikować konfigurację jej bazy danych i serwera bazy danych, uruchamiając Instalatora na serwerze centralnej lokacji administracyjnej lub lokacji głównej. Bazę danych lokacji można przenieść do nowego wystąpienia programu SQL Server na tym samym komputerze lub do innego komputera z uruchomioną obsługiwaną wersją programu SQL Server. Te i pokrewne zmiany nie są obsługiwane dla konfiguracji bazy danych w lokacjach dodatkowych.  

 Aby uzyskać więcej informacji na temat limitów pomocy technicznej, zobacz [Zasady pomocy technicznej dotyczące ręcznego wprowadzania zmian w bazach danych w środowisku programu Configuration Manager](https://support.microsoft.com/kb/3106512).  

> [!NOTE]  
>  Podczas modyfikowania konfiguracji bazy danych lokacji programu Configuration Manager ponownie uruchamia lub instaluje usługi programu Configuration Manager na serwerze lokacji i serwery zdalnego systemu lokacji komunikujących się z bazą danych.  

**Aby zmodyfikować konfigurację bazy danych**, uruchom Instalatora na serwerze lokacji i wybierz opcję **Przeprowadź obsługę lokacji lub zresetuj tę lokację**. Następnie wybierz opcję **Modyfikuj konfigurację serwera SQL**. Można zmienić następujące konfiguracje bazy danych lokacji:  

-   Serwer z systemem Windows, który bazę danych.  

-   Wystąpienie programu SQL Server używane na serwerze hostującym jego bazę danych  

-   Nazwa bazy danych.  

-   Port usługi SQL Server używany przez program Configuration Manager  

-   Port brokera usług serwera SQL używane przez program Configuration Manager  

**Jeśli przeniesiesz bazy danych lokacji, należy skonfigurować następujące czynności:**  

-   **Konfigurowanie dostępu:** Po przeniesieniu bazy danych lokacji do nowego komputera Dodaj konto komputera serwera lokacji do **Administratorzy lokalni** na komputerze z uruchomionym programem SQL Server. W przypadku używania klastra programu SQL Server w ramach bazy danych lokacji należy dodać konto komputera do grupy **Administratorzy lokalni** na każdym komputerze węzła klastra systemu Windows Server.  

-   **Włącz integrację środowiska uruchomieniowego (języka wspólnego CLR):**  W przypadku przenoszenia bazy danych do nowego wystąpienia w programie SQL Server lub do nowego komputera programu SQL Server, należy włączyć integrację środowiska uruchomieniowego (języka wspólnego CLR). Aby włączyć integrację środowiska CLR, użyj **programu SQL Server Management Studio** połączyć się z wystąpieniem programu SQL Server, który jest hostem bazy danych lokacji i uruchom następującą procedurę składowaną jako zapytanie: **procedury składowanej sp_configure 'clr enabled', 1; ponownie skonfigurować**.  
-  **Upewnij się, że nowy serwer SQL nie ma dostępu do lokalizacji kopii zapasowej:** Gdy używasz UNC do przechowywania kopii zapasowej bazy danych lokacji po przeniesieniu bazy danych do nowego serwera, włącznie z przejściem do grupy dostępności AlwaysOn programu SQL Server lub klastra programu SQL Server, upewnij się, konto komputera nowego serwera SQL ma **zapisu** uprawnieniami do lokalizacji UNC.  


> [!IMPORTANT]  
>  Przed przeniesieniem bazy danych zawierającej co najmniej jedną replikę dla punktów zarządzania należy najpierw usunąć repliki bazy danych. Po przeniesieniu bazy danych można ponownie skonfigurować repliki bazy danych. Aby uzyskać więcej informacji, zobacz [Repliki bazy danych dla punktów zarządzania programu System Center Configuration Manager](../../../core/servers/deploy/configure/database-replicas-for-management-points.md).  

##  <a name="bkmk_SPN"></a> Zarządzanie główną nazwę usługi dla serwera bazy danych lokacji  
Możliwe jest wybranie konta, na którym uruchomiono usługi SQL Services dla bazy danych lokacji:  

-   Gdy usługi są uruchomione przy użyciu konta systemowego komputerów, główna nazwa usługi jest automatycznie rejestrowana.  

-   Gdy usługi są uruchomione przy użyciu lokalnego konta użytkownika domeny, należy ręcznie zarejestrować główną nazwę usługi, aby zapewnić klientom SQL i innym systemom lokacji możliwość przeprowadzenia uwierzytelniania przy użyciu protokołu Kerberos. Bez przeprowadzenia uwierzytelniania przy użyciu protokołu Kerberos komunikacja z bazą danych może zakończyć się niepowodzeniem.  

Dokumentacja programu SQL Server może ułatwić [ręczne zarejestrowanie głównej nazwy usługi](https://technet.microsoft.com/library/ms191153\(v=sql.120\).aspx) i zapewnienie dodatkowych informacji uzupełniających na temat głównych nazw usług i połączeń przy użyciu protokołu Kerberos.  

> [!IMPORTANT]  
>  -   Po utworzeniu głównej nazwy usługi klastrowanego programu SQL Server należy określić nazwę wirtualną klastra programu SQL Server jako nazwę komputera z programem SQL Server.  
> -   Polecenie rejestrowania głównej nazwy usługi nazwanego wystąpienia programu SQL Server jest takie samo jak polecenie używane podczas rejestrowania głównej nazwy usługi domyślnego wystąpienia, ale numer portu musi być zgodny z portem używanym przez to nazwane wystąpienie.  

Główną nazwę usługi konta usługi programu SQL Server na serwerze bazy danych lokacji można zarejestrować za pomocą narzędzia **Setspn**. Narzędzie Setspn należy uruchomić na komputerze należącym do domeny programu SQL Server, używając poświadczeń administratora domeny.  

 Poniższe procedury zawierają przykładowe sposoby zarządzania nazwą SPN konta usługi programu SQL Server przy użyciu narzędzia Setspn w systemie Windows Server 2008 R2. Dokładne wskazówki dotyczące narzędzia Setspn znajdują się w temacie [Setspn — omówienie](http://go.microsoft.com/fwlink/p/?LinkId=226343) lub w podobnej dokumentacji dotyczącej używanego systemu operacyjnego.  

> [!NOTE]  
>  Poniższe procedury odwołują się narzędzie wiersza polecenia Setspn. Narzędzie wiersza polecenia Setspn jest dostępne w przypadku, po zainstalowaniu narzędzi obsługi systemu Windows Server 2003 z dysku CD produktu lub [Microsoft Download Center](http://go.microsoft.com/fwlink/p/?LinkId=100114). Więcej informacji o sposobie instalowania narzędzi obsługi systemu Windows z dysku CD produktu znajduje się w temacie [Instalowanie narzędzi obsługi systemu Windows](http://go.microsoft.com/fwlink/p/?LinkId=62270).  

#### <a name="to-manually-create-a-domain-user-service-principal-name-spn-for-the-sql-server-service-account"></a>Aby ręcznie utworzyć użytkownika domeny głównej nazwy usługi (SPN) dla konta usługi programu SQL Server  

1.  W menu **Start** kliknij pozycję **Uruchom**, a następnie wpisz w oknie dialogowym Uruchamianie polecenie **cmd**.  

2.  W wierszu polecenia przejdź do katalogu instalacyjnego narzędzi obsługi systemu Windows Server. Domyślnie te narzędzia znajdują się w **C:\Program Files\Support Tools** katalogu.  

3.  Wprowadź prawidłowe polecenie, aby utworzyć nazwę SPN. Aby utworzyć nazwę SPN, można użyć nazwy NetBIOS lub w pełni kwalifikowaną nazwę (FQDN) komputera z programem SQL Server. Należy jednak utworzyć nazwę SPN zarówno w ramach nazwy NetBIOS, jak i FQDN.  

    > [!IMPORTANT]  
    >  Po utworzeniu nazwy SPN klastrowanego programu SQL Server należy określić nazwę wirtualną klastra programu SQL Server jako nazwę komputera z programem SQL Server.  

    -   Aby utworzyć nazwę SPN dla nazwy NetBIOS komputera programu SQL Server, wpisz następujące polecenie: **setspn – MSSQLSvc /&lt;nazwa komputera serwera SQL\>: 1433 &lt;domena\konto >**  

    -   Aby utworzyć nazwę SPN dla nazwy FQDN komputera programu SQL Server, wpisz następujące polecenie: **setspn – MSSQLSvc /&lt;nazwa FQDN programu SQL Server\>: 1433 &lt;domena\konto >**  

    > [!NOTE]  
    >  Polecenie rejestrowania nazwy SPN nazwanego wystąpienia programu SQL Server jest takie samo jak polecenie używane podczas rejestrowania nazwy SPN domyślnego wystąpienia, ale numer portu musi być zgodny z portem używanym przez to nazwane wystąpienie.  

#### <a name="to-verify-the-domain-user-spn-is-registered-correctly-by-using-the-setspn-command"></a>Aby sprawdzić, czy nazwa SPN użytkownika domeny została prawidłowo zarejestrowana przy użyciu polecenia Setspn  

1.  W menu **Start** kliknij pozycję **Uruchom**, a następnie wpisz w oknie dialogowym **Uruchamianie** polecenie **cmd**.  

2.  W wierszu polecenia wprowadź następujące polecenie: **setspn -L &lt;domena\konto usługi SQL >**.  

3.  Sprawdź zarejestrowaną nazwę **ServicePrincipalName**, aby upewnić się, że utworzono prawidłową nazwę SPN dla programu SQL Server.  

#### <a name="to-verify-the-domain-user-spn-is-registered-correctly-when-using-the-adsiedit-mmc-console"></a>Aby sprawdzić, czy nazwa SPN użytkownika domeny została prawidłowo zarejestrowana przy użyciu konsoli MMC ADSIEdit  

1.  W menu **Start** kliknij pozycję **Uruchom**, a następnie wpisz **adsiedit.msc**, aby uruchomić konsolę MMC ADSIEdit.  

2.  W razie potrzeby połącz się z domeną serwera lokacji.  

3.  W okienku konsoli rozwiń domenę serwera lokacji, rozwiń **DC =&lt;nazwa wyróżniająca serwera\>**, rozwiń węzeł **CN = Users**, kliknij prawym przyciskiem myszy **CN =&lt;użytkownik konta usługi\>**, a następnie kliknij przycisk **właściwości**.  

4.  W **CN =&lt;użytkownik konta usługi\> właściwości** okno dialogowe, przejrzyj **servicePrincipalName** wartość, aby upewnić się, że prawidłowa nazwa SPN została utworzona i skojarzonych z komputerem programu SQL Server.  

#### <a name="to-change-the-sql-server-service-account-from-local-system-to-a-domain-user-account"></a>Aby zmienić konto usługi SQL Server z systemu lokalnego na konto użytkownika domeny  

1.  Utwórz lub wybierz konto użytkownika systemu lokalnego albo domeny, które ma być używane jako konto usługi SQL Server.  

2.  Otwórz **Menedżera konfiguracji programu SQL Server**.  

3.  Kliknij przycisk **usług SQL Server**, a następnie kliknij dwukrotnie **programu SQL Server&lt;nazwa wystąpienia\>**.  

4.  Na karcie **Logowanie** wybierz opcję **To konto**, a następnie wybierz nazwę użytkownika i hasło do konta użytkownika domeny utworzonego w kroku 1 lub kliknij przycisk **Przeglądaj**, aby znaleźć konto użytkownika w usługach domenowych Active Directory, a następnie kliknij przycisk **Zastosuj**.  

5.  W oknie dialogowym **Potwierdź zmianę konta** kliknij przycisk **Tak**, aby potwierdzić zmianę konta i uruchomić ponownie usługę SQL Server.  

6.  Po pomyślnej zmianie konta usługi kliknij przycisk **OK**.  

##  <a name="bkmk_reset"></a> Uruchamianie resetowania lokacji  
 Gdy resetowanie lokacji ma miejsce w centralnej lokacji administracyjnej lub lokacji głównej, przeprowadzane jest:  

-   Ponowne zastosowanie programu Configuration Manager domyślne uprawnienia plików i rejestru  

-   Ponowna instalacja wszystkich składników lokacji i wszystkich ról systemu lokacji  

Resetowanie lokacji nie jest możliwe w lokacjach dodatkowych.  

Resetowanie lokacji może być uruchamiane ręcznie, w wybranym momencie, ale może zostać również uruchomione automatycznie po zmodyfikowaniu konfiguracji lokacji.  

Na przykład jeśli wprowadzono zmiany w kontach używanych przez składniki programu Configuration Manager, należy rozważyć ręcznego resetowania lokacji, aby upewnić się, że składniki lokacji zostaną zaktualizowane do używania nowych szczegółów konta. Jednak przypadku zmodyfikowania języków serwera lub klienta w lokacji programu Configuration Manager automatycznie uruchamia resetuje lokację, ponieważ jest to wymagane, aby lokacja mogła zastosować tę zmianę.  

> [!NOTE]  
>  Resetowanie lokacji nie resetowania uprawnień dostępu do obiektów — Configuration Manager.  

Podczas resetowania lokacji:  

1.  Instalator przerywa działanie i uruchamia ponownie **SMS_SITE_COMPONENT_MANAGER** oraz składniki wątków usługi **SMS_EXECUTIVE** usługi.  

2.  Instalator usuwa, a następnie tworzy ponownie systemu lokacji folder udostępniony i **SMS Executive** na komputerze lokalnym oraz na komputerach zdalnego systemu lokacji.  

3.  Instalator ponownie uruchamia **SMS_SITE_COMPONENT_MANAGER** usługa ta usługa instaluje **SMS_EXECUTIVE** i **SMS_SQL_MONITOR** usług.  

Ponadto resetowanie lokacji powoduje przywrócenie następujących obiektów:  

-   Klucze rejestru **SMS** lub **NAL** oraz wszystkie domyślne podklucze należące do tych kluczy.  

-   Drzewo katalogów plików programu Configuration Manager i wszystkie domyślne pliki lub podkatalogi w drzewie katalogów tego pliku.  

**Wymagania wstępne dotyczące uruchamiania resetowania lokacji**  

Konto, którego chcesz użyć do wykonania resetu lokacji, musi mieć przyznane następujące uprawnienia:  

-   Konto, którego chcesz użyć do wykonania resetu lokacji, musi mieć przyznane następujące uprawnienia:  

    -   **Centralna lokacja administracyjna**: Konto, którego używasz do wykonywania resetu w tej lokacji musi być administratorem lokalnym na serwerze centralnej lokacji administracyjnej oraz musi mieć przyznane uprawnienia równoważne **administrator o pełnych uprawnieniach** roli zabezpieczeń administracji opartej na rolach.  

    -   **Lokacja główna**: Konto, którego używasz do wykonywania resetu w tej lokacji musi być administratorem lokalnym na serwerze lokacji głównej oraz musi mieć przyznane uprawnienia równoważne **administrator o pełnych uprawnieniach** roli zabezpieczeń administracji opartej na rolach. Jeśli lokacja główna znajduje się w hierarchii z centralną lokacją administracyjną, to konto musi być także kontem lokalnego administratora na serwerze centralnej lokacji administracyjnej.  

**Ograniczenia dotyczące resetowania lokacji**
  - Począwszy od wersji 1602, nie można użyć resetowania lokacji, aby zmienić serwer lub zainstalowanym na dodatkowe tak długo, jak hierarchii jest skonfigurowany do obsługi pakietów językowych klienta [testowanie uaktualnień klienta w kolekcji środowiska przedprodukcyjnego](/sccm/core/clients/manage/upgrade/test-client-upgrades).

#### <a name="to-perform-a-site-reset"></a>Aby wykonać reset lokacji  

1.  Uruchom **Instalatora programu Configuration Manager** z  **&lt;folder instalacji lokacji programu Configuration Manager\>\BIN\X64\setup.exe**.  

    > [!TIP]  
    >  Można również uruchomić Resetowanie lokacji przez uruchamianie Instalatora programu Configuration Manager na **Start** menu komputera serwera lokacji lub z nośnika źródłowego programu Configuration Manager.  

2.  Na stronie **Pierwsze kroki** wybierz pozycję **Przeprowadź obsługę lokacji lub zresetuj tę lokację**, a następnie kliknij przycisk **Dalej**.  

3.  Na stronie **Obsługa lokacji** wybierz polecenie **Resetuj lokację** bez zmian konfiguracji, a następnie kliknij przycisk **Dalej**.  

4.  Kliknij przycisk **Tak**, aby rozpocząć reset lokacji.  

Po zakończeniu resetowania lokacji kliknij przycisk **Zamknij**, aby dokończyć procedurę.  

##  <a name="bkmk_sitelang"></a> Zarządzanie pakietami językowymi w lokacji  
Po zainstalowaniu lokacji można zmienić używane pakiety językowe serwera i klienta:  

**Pakiety językowe serwera:**  

-   **Dotyczy:**  

     Instalacje konsoli programu Configuration Manager  

     Nowe instalacje odpowiednich ról systemu lokacji  

-   **Szczegóły:**  

     Po zaktualizowaniu pakietów językowych serwera w lokacji można dodać obsługę pakietów językowych do konsol programu Configuration Manager.  

     Aby dodać obsługę pakietu językowego serwera do konsoli programu Configuration Manager, należy zainstalować konsolę programu Configuration Manager z **ConsoleSetup** folderu na serwerze lokacji, który zawiera pakiet językowy, który ma być używany. Jeśli została już zainstalowana konsola programu Configuration Manager, należy najpierw odinstalować go w celu włączenia nowa instalacja nie rozpozna bieżącej listy obsługiwanych pakietów językowych.  

**Pakiety językowe klienta:**  

-   **Dotyczy:**  

     Zmiany pakietów językowych klienta powodują aktualizację plików źródłowych instalacji klienta, dzięki czemu nowe instalacje i uaktualnienia klienta umożliwiają obsługę zaktualizowanej listy języków klienta.  

-   **Szczegóły:**  

     Po zaktualizowaniu pakietów językowych w lokacji musisz zainstalować każdego klienta, który będzie używać tych pakietów, za pomocą plików źródłowych zawierających pakiety językowe klienta.  

Aby uzyskać informacje o językach klienta i serwera, które są obsługiwane przez program Configuration Manager, zobacz [pakiety językowe w programie System Center Configuration Manager](../../../core/servers/deploy/install/language-packs.md)  

#### <a name="to-modify-the-language-packs-that-are-supported-at-a-site"></a>Aby zmodyfikować pakiety językowe obsługiwane w lokacji  

1.  Na serwerze lokacji uruchom Instalatora programu Configuration Manager z  **&lt;folder instalacji lokacji programu Configuration Manager\>\BIN\X64\setup.exe.**  

2.  Na stronie **Pierwsze kroki** wybierz pozycję **Przeprowadź obsługę lokacji lub zresetuj tę lokację**, a następnie kliknij przycisk **Dalej**.  

3.  Na stronie **Obsługa lokacji** wybierz polecenie **Modyfikuj konfigurację języka**, a następnie kliknij przycisk **Dalej**.  

4.  Na stronie **Pobieranie plików wymaganych wstępnie** wybierz polecenie **Pobierz wymagane pliki**, aby pobrać aktualizacje pakietów językowych, lub wybierz polecenie **Użyj wcześniej pobranych plików**, aby użyć wcześniej pobranych plików zawierających pakiety językowe, które chcesz dodać do lokacji. Kliknij przycisk **Dalej**, aby zweryfikować pliki i kontynuować.  

5.  Na stronie **Wybór języka serwera** zaznacz pola wyborów obok języków serwera obsługiwanych przez tę lokację, a następnie kliknij przycisk **Dalej**.  

6.  Na stronie **Wybór języka klienta** zaznacz pola wyborów obok języków klienta obsługiwanych przez tę lokację, a następnie kliknij przycisk **Dalej**.  

7.  Kliknij przycisk **Dalej**, aby zmodyfikować języki obsługiwane w lokacji.  

    > [!NOTE]  
    >  Inicjuje programu Configuration Manager reset lokacji, co spowoduje również ponowne zainstalowanie wszystkich ról systemu lokacji w lokacji.  

8.  Po zakończeniu tej procedury kliknij przycisk **Zamknij**.  

##  <a name="BKMK_ModDBAlert"></a> Modyfikowanie progu alertu serwera bazy danych  
 Domyślnie program Configuration Manager generuje alerty, gdy brakuje wolnego miejsca na dysku na serwerze bazy danych lokacji. Według domyślnych ustawień ostrzeżenie będzie generowane, gdy ilość wolnego miejsca na dysku osiągnie 10 GB lub mniej, natomiast próg alertu krytycznego wynosi 5 GB lub mniej. Można zmodyfikować te wartości lub wyłączyć funkcję alertów w poszczególnych lokacjach.  

 Aby zmienić te ustawienia:  

1.  W obszarze roboczym **Administracja** rozwiń węzeł **Konfiguracja lokacji**, a następnie kliknij przycisk **Lokacje**.  

2.  Wybierz lokację, którą chcesz skonfigurować i otwórz tej lokacji **właściwości**.  

3.  W tej witrynie **właściwości** okno dialogowe, wybierz opcję **alertu** karcie, a następnie Edytuj ustawienia.  

4.  Kliknij przycisk **OK**, aby zamknąć okno dialogowe właściwości tej lokacji.  
