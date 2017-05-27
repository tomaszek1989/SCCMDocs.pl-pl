---
title: Kreator instalacji | Dokumentacja firmy Microsoft
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1f703376-5f2c-4fd2-8209-7028c931ddc7
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f809c9327db9f298168674add2d09820fdecd1b8
ms.openlocfilehash: 14b4172ad713a3981b8a5abe182405e271d78c26
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="use-the-setup-wizard-to-install-system-center-configuration-manager-sites"></a>Kreator instalacji umożliwia zainstalowanie lokacji programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


Aby zainstalować nową witrynę programu System Center Configuration Manager za pomocą interfejsu użytkownika z przewodnikiem, należy użyć Kreatora instalacji programu Configuration Manager (setup.exe). Kreator obsługuje instalowanie lokacji głównej lub w witrynie Administracja centralna. Możesz także użyć kreatora do [uaktualnienie instalacji wersji ewaluacyjnej](../../../../core/servers/deploy/install/upgrade-an-evaluation-install-to-a-full-install.md) programu Configuration Manager do w pełni licencjonowaną instalacji. Jeśli nie chcesz użyć kreatora, należy użyć [skrypt instalacji](../../../../core/servers/deploy/install/use-a-command-line-to-install-sites.md) i uruchamianie nienadzorowanej instalacji wiersza polecenia.

Aby zainstalować lokację dodatkową, należy zainstalować z danej lokacji w konsoli programu Configuration Manager. Lokacje dodatkowe nie obsługują instalacji z wiersza polecenia przy użyciu skryptu.

## <a name="bkmk_primary"></a>Instalowanie centralnej lokacji administracyjnej lub lokacji głównej
Użyj poniższej procedury do instalacji centralnej lokacji administracyjnej lub lokacji głównej lub uaktualnienia lokacji oceny do lokacji programu Configuration Manager w pełni licencjonowaną.   

Przed rozpoczęciem instalacji lokacji, należy zapoznać się ze szczegółami w następujących artykułach:
 -  [Przygotowanie do zainstalowania lokacji](../../../../core/servers/deploy/install/prepare-to-install-sites.md)
 -  [Wymagania wstępne dotyczące instalacji lokacji](../../../../core/servers/deploy/install/prerequisites-for-installing-sites.md)

Jeżeli instalujesz witryny Administracja centralna w ramach scenariusza rozszerzania lokacji, sprawdź, czy [rozszerzania autonomicznej lokacji głównej](../../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md#bkmk_expand) tego tematu przed użyciem poniższej procedury.

### <a name="bkmk_installpri"></a>Aby zainstalować lokację głównej lub centralnej administracji

1.  Na komputerze, na którym chcesz zainstalować lokacji, uruchom  **&lt;InstallationMedia\>\SMSSETUP\BIN\X64\Setup.exe** uruchomić **Kreatora instalacji programu System Center Configuration Manager**.  

    > [!NOTE]  
    > Podczas instalowania centralnej lokacji administracyjnej rozszerzania autonomicznej lokacji głównej, lub zainstaluj nowy podrzędnej lokacji głównej w istniejącej hierarchii, należy użyć nośnika instalacyjnego (plików źródłowych) jest zgodna z wersją z istniejącej witryny lub witryny. Jeśli po zainstalowaniu aktualizacji w konsoli, które zostały zmienione w wersji uprzednio zainstalowanej lokacji, nie używaj oryginalnego nośnika instalacyjnego. Zamiast tego należy użyć plików źródłowych z [dysku CD. Najnowszy folder](../../../../core/servers/manage/the-cd.latest-folder.md) zaktualizowanej witryny. Program Configuration Manager wymaga użycia pliki źródłowe, które pasują do wersji istniejącej lokacji, który nowej witryny będzie łączyć się.  

2.  Na **przed rozpoczęciem** wybierz **dalej**.  

3.  Na **wprowadzenie** wybierz typ obiektu, który chcesz zainstalować:  

    -   **Witryna Administracja centralna**, jako pierwszą lokację nowej hierarchii lub dotyczące rozszerzania autonomicznej lokacji głównej:  

        Wybierz **zainstalować witryny administracji centralnej programu Configuration Manager**.  

         W późniejszym etapie tej procedury są oferowane wyboru, aby zainstalować centralną lokację administracyjną jako pierwszą lokację nowej hierarchii lub zainstalować witryny administracji centralnej, aby rozwinąć autonomicznej lokacji głównej.  

    -    **Lokacja główna**, jako pierwszą lokację nowej hierarchii autonomicznej lokacji głównej lub jako element podrzędny głównej:  

        Wybierz **instalacji lokacji głównej programu Configuration Manager**.  

        > [!TIP]  
        > Zwykle, tylko wybierz opcję **Użyj typowych opcji instalacji dla autonomicznej lokacji głównej** gdy chcesz zainstalować autonomiczną lokację główną w środowisku testowym. Po wybraniu tej opcji instalacji:  

        > -   Automatycznie skonfiguruje lokację jako autonomiczną lokację główną.  
        > -   Używa domyślnej ścieżki instalacji.  
        > -   Używa lokalnej instalacji domyślnego wystąpienia programu SQL Server dla bazy danych lokacji.  
        > -   Instaluje na komputerze serwera lokacji punktu zarządzania i punkt dystrybucji.  
        > -   Skonfiguruje lokację z językiem angielskim i język systemu operacyjnego na serwerze lokacji głównej, jeśli jest on zgodny z językami obsługiwanymi przez program Configuration Manager.  

4.  Na **klucz produktu** strony:
    - Określ, czy zainstalować program Configuration Manager w wersji ewaluacyjnej lub licencjonowaną wersję.  

      -   Jeśli wybierzesz licencjonowaną wersję, wprowadź klucz produktu i wybierz **dalej**.  

      -   W przypadku wybrania wersji ewaluacyjnej wybierz **dalej**. (Można uaktualnić instalację w wersji ewaluacyjnej do pełnej instalacji później.)  
    - Począwszy od wersji 2016 października nośników linii bazowej 1606 wersji programu System Center Configuration Manager, można określić datę wygaśnięcia umowy Software Assurance. Na tej stronie, masz możliwość określenia **Data wygaśnięcia Software Assurance** umowy licencyjnej jako wygodny monitu dla Ciebie od tej daty. Jeśli nie podasz to podczas instalacji, można określić ją później za pomocą w konsoli programu Configuration Manager.

      > [!NOTE]   
      > Microsoft nie Sprawdź poprawność wprowadzonej daty wygaśnięcia i nie używa tej daty w celu weryfikacji licencji. W takim przypadku go użyć jako przypomnienie od daty wygaśnięcia. Jest to przydatne, ponieważ program Configuration Manager okresowo sprawdza dostępność nowych aktualizacji oprogramowania, oferowanych w trybie online — i Twojego stanu licencji na oprogramowanie assurance powinny być bieżącego, dzięki czemu masz prawo do korzystania z tych dodatkowych aktualizacji.    

      Aby uzyskać więcej informacji, zobacz [licencjonowania i gałęzie dla programu System Center Configuration Manager](/sccm/core/understand/learn-more-editions).

5.  Na **postanowień licencyjnych dotyczących oprogramowania Microsoft** strony, przeczytaj i zaakceptuj postanowienia licencyjne.  

6.  Na **licencje wymagań wstępnych** strony, przeczytaj i zaakceptuj postanowienia licencyjne wstępnie wymaganego oprogramowania. Instalator pobiera i automatycznie instaluje oprogramowanie systemy lokacji lub na klientach, gdy są wymagane. Przed kontynuowaniem do następnej strony, należy zaznaczyć wszystkie pola wyboru.  

7.  Na **pobieranie plików wymaganych wstępnie** Określ, czy Instalator ma pobrać najnowsze wymagane wstępnie pliki z Internetu lub użyj wcześniej pobranych plików:  

    -   Instalatora w celu pobrania plików w tej chwili, wybierz opcję **Pobierz wymagane pliki** i określ lokalizację do przechowywania plików w.  

    -   Jeżeli pliki zostały wcześniej pobrane przy użyciu [Narzędzie pobierania Instalatora](../../../../core/servers/deploy/install/setup-downloader.md), wybierz opcję **Użyj wcześniej pobranych plików** i określ folder pobierania.  

        > [!TIP]  
        > W przypadku używania wcześniej pobranych plików Sprawdź, czy ścieżka do folderu pobierania zawiera najnowszą wersję plików.  

8.  Na **wybór języka serwera** wybierz języki, które są dostępne dla konsoli programu Configuration Manager i raporty. (Język angielski jest wybrany domyślnie i nie można usunąć).  

9. Na **wybór języka klienta** wybierz języki, które są dostępne na komputerach klienckich, a następnie określ, czy włączyć obsługę wszystkich języków klienta dla klientów urządzeń przenośnych. (Język angielski jest wybrany domyślnie i nie można usunąć).  

    > [!IMPORTANT]  
    > Korzystając z witryny administracji centralnej, upewnij się, że języki klienta, które można skonfigurować w witrynie Administracja centralna obejmują wszystkie języki klienta, które można skonfigurować w każdej podrzędnej lokacji głównej. Jest tak, ponieważ klienci, którzy instalacji z punktu dystrybucji mają dostęp do języków klienta z lokacji najwyższego poziomu, gdy klienci, którzy instalacji z punktu zarządzania miał dostęp do języków klienta przypisanej lokacji głównej.  

10. Na **ustawienia lokacji i instalacji** określ dla nowej lokacji, który użytkownik instaluje następujące operacje:  

    -   **Kod lokacji:** [Każdy kod lokacji w hierarchii muszą być unikatowe](../../../../core/servers/deploy/install/prepare-to-install-sites.md#bkmk_sitecodes) i składają się z trzech cyfr alfanumeryczne (od A do Z) i cyfry od 0 do 9. Ponieważ kody lokacji są używane w nazwach folderów, nie należy używać systemu Windows zarezerwowanych nazw dla lokacji, w tym:    
        -   AUX  
        -   CON    
        -   NUL    
        -   PRN    
        -   SMS  

        > [!NOTE]  
        > Instalator nie sprawdza, czy należy określić kod lokacji jest już używana, czy ma ona zastrzeżona.  

    -   **Nazwa lokacji:** Każda lokacja wymaga tego przyjaznej nazwy, która może pomóc w zidentyfikowaniu lokacji.  

    -   **Folder instalacji:** Jest to ścieżka folderu instalacji programu Configuration Manager. Nie można zmienić lokalizacji po zainstalowaniu lokacji. Ponadto ścieżka nie może zawierać znaków Unicode lub spacje końcowe.  

11. Na **instalacji lokacji** Użyj poniższych opcji, odpowiadający scenariusza:  

    -   **Am I instalowanie centralnej lokacji administracyjnej:**  

         Na **instalacja centralnej lokacji administracyjnej** wybierz opcję **zainstalować jako pierwszą lokację w nowej hierarchii**, a następnie wybierz **dalej** aby kontynuować.  

    -   **Am I rozszerzania autonomicznej podstawowego do hierarchii z centralną lokacją administracyjną:**  

         Na **instalacja centralnej lokacji administracyjnej** wybierz opcję **rozszerzyć istniejących podstawowej autonomiczną do hierarchii**, określ nazwę FQDN serwera autonomicznej lokacji głównej, a następnie wybierz **dalej** aby kontynuować.  

         Nośnik, który można użyć do zainstalowania nowej centralnej lokacji administracyjnej musi odpowiadać wersji lokacji głównej.  

    -   **Am I zainstalowanie autonomicznej lokacji głównej:**  

         Na **instalacja lokacji głównej** wybierz opcję **zainstalować lokację główną jako autonomiczną**, a następnie wybierz **dalej**.  

    -   **Am I instalowanie podrzędnej lokacji głównej:**  

         Na **instalacja lokacji głównej** wybierz opcję **Dołącz lokację główną do istniejącej hierarchii**, określ nazwę FQDN centralnej lokacji administracyjnej, a następnie wybierz **dalej**.  

12. Na **bazy danych** określ następujące informacje:  

    -   **Nazwa serwera SQL (FQDN):** Domyślnie wynosi ona być komputera serwera lokacji.  

    -   **Nazwa wystąpienia:** Domyślnie to pole jest puste. Używa domyślnego wystąpienia programu SQL Server na komputerze serwera lokacji.  

    -   **Nazwa bazy danych:** Domyślnie wynosi ona CM_&lt;Kod_lokacji\>. Mogą używać innej nazwy, który określisz.  

    -   **Port brokera usług:** Domyślnie wynosi ona użyć domyślnego portu usługi SQL Server Service Broker (SSB) z 4022. SQL używa go komunikują się bezpośrednio z bazy danych lokacji w innych lokacjach.  

13. Na drugim **bazy danych** strony, można określić niestandardowe lokalizacje pliku danych programu SQL Server i pliku dziennika programu SQL Server dla bazy danych lokacji:  

    -   Podano domyślne lokalizacje plików dla programu SQL Server.  

    -   Można określić niestandardowe lokalizacje plików nie jest dostępna w przypadku używania klastra programu SQL Server.  

    -   Narzędzie sprawdzania wymagań wstępnych nie przeprowadza sprawdzenia wolnego miejsca dla innej niż domyślna lokalizacje plików.  

14. Na **ustawienia dostawcy programu SMS** Określ nazwę FQDN serwera, na którym chcesz zainstalować dostawcy programu SMS.  

    -   Domyślnie serwer lokacji jest określony.  

    -   Po zainstalowaniu lokacji można skonfigurować dodatkowych dostawców programu SMS.  

15. Na **ustawienia komunikacji klienta** wybierz, czy skonfigurować wszystkie systemy lokacji, aby akceptowały wyłącznie komunikację HTTPS od klientów lub metoda komunikacji ma być skonfigurowana dla poszczególnych ról systemu lokacji.  

    Po wybraniu **wszystkie role systemu lokacji akceptują tylko komunikację HTTPS od klientów**, komputer kliencki musi mieć prawidłowy certyfikat PKI umożliwiający uwierzytelnianie klientów. Aby uzyskać więcej informacji o wymaganiach dotyczących certyfikatów PKI, zobacz [wymagania dotyczące certyfikatu PKI dla programu Configuration Manager](https://technet.microsoft.com/library/gg699362.aspx).  

    > [!NOTE]  
    > W tym kroku dotyczy tylko po zainstalowaniu lokacji głównej. Jeśli instalujesz witryny administracji centralnej, Pomiń ten krok.  

16. Na **ról systemu lokacji** wybierz, czy zainstalować punktu zarządzania lub punktu dystrybucji. Dla każdej roli, którą chcesz mieć zainstalowane przez Instalatora:  

    -   Należy wprowadzić **FQDN** dla komputera, który będzie obsługiwać rolę i wybierz polecenie klienta metoda połączenia, że serwer będzie obsługiwać (HTTP lub HTTPS).  

    -   W przypadku wybrania **wszystkie role systemu lokacji akceptują tylko komunikację HTTPS od klientów** na poprzedniej stronie, ustawienia połączeń z klienta zostaną automatycznie skonfigurowane dla protokołu HTTPS i nie można zmienić, chyba że Przejdź wstecz i zmień ustawienie.  

    > [!NOTE]  
    > W tym kroku dotyczy tylko po zainstalowaniu lokacji głównej. Jeśli instalujesz witryny administracji centralnej, Pomiń ten krok.  

    > [!NOTE]  
    > Aby zainstalować role systemu lokacji, Instalator używa **konto instalacji systemu lokacji**. Domyślnie używa tego konta komputera lokacji głównej. To konto musi być administratorem lokalnym na komputerze zdalnym, zainstalować rolę systemu lokacji. Jeśli to konto nie ma wymaganych uprawnień, usuń zaznaczenie pola wyboru ról systemu lokacji i zainstalować je później z poziomu konsoli programu Configuration Manager, po skonfigurowaniu dodatkowe konta do użycia jako konta instalacji systemu lokacji.  

17. Na **dane użycia** , przejrzyj informacje o danych, że firma Microsoft zbiera, a następnie wybierz **dalej**.  

18. **Ustawienia punktu połączenia usługi** strona jest dostępna tylko podczas instalacji:  

    -   Podczas instalowania autonomicznej lokacji głównej.  

    -   Podczas instalowania centralnej lokacji administracyjnej.  

    > [!NOTE]  
    > Jeśli instalujesz podrzędnej lokacji głównej, należy pominąć ten krok (Ta strona jest niedostępna).  

     Jeśli ta rola jest już zainstalowana w autonomicznej lokacji głównej w przypadku instalowania centralnej lokacji administracyjnej w ramach scenariusza rozszerzania lokacji, należy odinstalować tę rolę w autonomicznej lokacji głównej. Dozwolony jest tylko jedno wystąpienie tej roli w hierarchii, a jest dozwolony tylko w lokacji najwyższego poziomu w hierarchii.  

     Po wybraniu opcji konfiguracji dla **punkt połączenia usługi**, wybierz **dalej**. (Po zakończeniu instalacji można zmienić tej konfiguracji z konsoli programu Configuration Manager).  

19. Na **Podsumowanie ustawień** Przejrzyj wybrane ustawienie. Gdy wszystko będzie gotowe, wybierz **dalej** uruchomić narzędzie sprawdzania wymagań wstępnych.  

20. Na **Sprawdzanie wymagań wstępnych instalacji** strony, wszelkie problemy, które mogą zostać zidentyfikowane są wymienione.  

    -   Gdy narzędzie sprawdzania wymagań wstępnych wykryje problem, wybierz element na liście, aby uzyskać szczegółowe informacje o sposobie rozwiązania tego problemu.  

    -   Należy rozwiązać każdy element ze stanem **niepowodzenie** przed kontynuowaniem instalacji lokacji. Elementy ze stanem **ostrzeżenie** powinny zostać rozwiązane, ale nie blokują instalacji lokacji.  

    -   Po rozwiązaniu problemów, wybierz **Uruchom sprawdzanie** ponownie uruchomić narzędzie sprawdzania wymagań wstępnych.  

     Po uruchomieniu narzędzia sprawdzania wymagań wstępnych, która otrzymywać żadnych testów **niepowodzenie** stanu, można wybrać **rozpoczęcie instalacji** do rozpoczęcia instalacji lokacji.  

    > [!TIP]  
    > Oprócz opinii, które jest dostępne w kreatorze, można znaleźć dodatkowe informacje na temat wymagań wstępnych problemy podczas wyświetlania **ConfigMgrPrereq.log** plik w folderze głównym dysku systemowym instalowany na komputerze. Lista reguł wymagań wstępnych instalacji oraz opisy, zobacz [listy o kontrolach warunków wstępnych dla programu System Center Configuration Manager](../../../../core/servers/deploy/install/list-of-prerequisite-checks.md).  

21. Na **instalacji** instalacyjnym jest wyświetlany stan instalacji. Po zakończeniu instalacji serwera lokacji podstawowej, uzyskasz możliwość **Zamknij** Kreatora instalacji. Po zamknięciu Kreatora instalacji i konfiguracji początkowej lokacji kontynuowana w tle.  

    -   Można połączyć konsolę programu Configuration Manager do lokacji, przed ukończeniem instalacji. Ta konsola łączy jako tylko do odczytu, a także wyświetlić obiekty i ustawienia, ale nie wolno wprowadzać zmian.  

    -   Po zakończeniu instalacji będzie można połączyć konsolę, które można edytować obiekty i ustawienia.  


## <a name="bkmk_expand"></a>Rozszerzanie autonomicznej lokacji głównej
Po zainstalowaniu autonomicznej lokacji głównej jako pierwszej lokacji, istnieje możliwość później, aby rozwinąć tej lokacji do większej hierarchii, instalując witryny administracji centralnej.   

Po rozszerzeniu autonomicznej lokacji głównej należy zainstalować nowej witryny Administracja centralna, który korzysta z istniejącej autonomicznej lokacji głównej bazy danych jako odwołanie. Po zainstalowaniu nowej centralnej lokacji administracyjnej autonomicznej lokacji głównej działa jako podrzędnej lokacji głównej.

-   Można rozwinąć tylko autonomicznej lokacji głównej do nowej hierarchii.  

-   Tylko jednej autonomicznej lokacji głównej można rozwinąć w określonej hierarchii. Tej opcji nie można użyć w celu dołączania dodatkowych autonomicznych lokacjach głównych do tej samej hierarchii. Zamiast tego należy użyć migracji do migracji danych z jednej hierarchii do innego.  

-   Po rozszerzeniu autonomicznej lokacji w hierarchii z centralną lokacją administracyjną, można dodać dodatkowe podrzędne głównych lokacji podrzędnych.  

-   Aby usunąć lokację główną z hierarchii z centralną lokacją administracyjną, należy odinstalować lokację główną.  

Aby rozszerzyć lokację, należy użyć Kreatora instalacji programu System Center Configuration Manager do zainstalowania nowej witryny Administracja centralna, z następującymi zastrzeżeniami:  

-   Przy użyciu tej samej wersji programu Configuration Manager jako autonomicznej lokacji głównej, należy zainstalować witryny administracji centralnej.  

-   Na **wprowadzenie** strony w Kreatorze instalacji wybierz opcję instalacji centralnej lokacji administracyjnej. Na późniejszym etapie instalacji będzie wybierz opcję rozszerzenia istniejącej autonomicznej lokacji głównej.  

-   Po skonfigurowaniu **wybór języka klienta** strony dla nowej witryny Administracja centralna, musisz wybrać te same języki klienta, które są skonfigurowane dla autonomicznej lokacji głównej w przypadku rozszerzania.  

-   Na **instalacji lokacji** strony, wybierz opcję, aby rozszerzyć autonomiczną lokację główną.  

Aby rozszerzyć autonomiczną lokację główną, należy najpierw sprawdzić [wymagania wstępne dotyczące rozszerzania lokacji](/sccm/core/servers/deploy/install/prerequisites-for-installing-sites#bkmk_expand), a następnie wykonać procedurę  *[instalowania lokacji głównej lub centralnej administracji](../../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md#bkmk_installpri)*, wcześniej w tym artykule.


## <a name="bkmk_secondary"></a>Instalowanie lokacji dodatkowej
 Konsoli programu Configuration Manager umożliwia instalowanie lokacji dodatkowej.  

-   Jeśli konsola, której używasz, nie jest podłączony do lokacji głównej, która będzie lokacji nadrzędnej do nowej lokacji dodatkowej, polecenia do zainstalowania lokacji będą replikowane do poprawnej lokacji głównej.  

-   Przed rozpoczęciem instalacji lokacji, upewnij się, że konto użytkownika ma uprawnienia wymagań wstępnych i czy komputer, który będzie hostem nowej lokacji dodatkowej spełnia wszystkie wymagania wstępne do użytku jako serwer lokacji dodatkowej.  

-   Po zainstalowaniu lokacji dodatkowej programu Configuration Manager konfiguruje nowej lokacji do korzystania z portów komunikacji klienta skonfigurowanych w nadrzędnej lokacji głównej.  

### <a name="bkmk_installsecondary"></a>Aby zainstalować lokację dodatkową  


1.  W konsoli programu Configuration Manager, przejdź do **Administracja** > **konfiguracja lokacji** > **witryny**. Wybierz lokację, która będzie nadrzędnej lokacji głównej w nowej lokacji dodatkowej.  

2.  Wybierz **tworzenia lokacji dodatkowej** uruchomić **Kreator tworzenia lokacji dodatkowej**.  

3.  Na **przed rozpoczęciem** upewnij się, że lokacji głównej, która znajduje się to lokacji, która ma być elementem nadrzędnym nowej lokacji dodatkowej. Następnie wybierz **dalej**.  

4.  Na **ogólne** strony, podaj następujące informacje:  

    -   **Kod lokacji**: Każdy kod lokacji w hierarchii musi być unikatowa i składają się z trzech cyfr alfanumeryczne (od A do Z) i cyfry od 0 do 9. Ponieważ kody lokacji są używane w nazwach folderów, nie należy używać systemu Windows zarezerwowanych nazw dla lokacji, w tym:  

        -   AUX    
        -   CON    
        -   NUL    
        -   PRN  
        -   SMS  

       > [!NOTE]  
       > Instalator nie sprawdza, czy należy określić kod lokacji jest już używana, lub jeśli jest nazwą zastrzeżoną.  

    -   **Nazwa serwera lokacji**: Jest to nazwa FQDN serwera, na którym będzie instalowany nowej lokacji dodatkowej.  

    -   **Nazwa witryny**: Każda lokacja wymaga tego przyjaznej nazwy, która może pomóc w zidentyfikowaniu lokacji.  

    -   **Folder instalacji**: Jest to ścieżka folderu instalacji programu Configuration Manager. Nie można zmienić lokalizacji po zainstalowaniu lokacji. Ścieżka nie może zawierać znaków Unicode lub spacje końcowe.  

    > [!IMPORTANT]  
    > Po określeniu szczegóły na tej stronie można wybrać **Podsumowanie** Aby użyć ustawień domyślnych w pozostałej części Opcje lokacji dodatkowej i przejść bezpośrednio do **Podsumowanie** w kreatorze.  

    > -   Tej opcji należy użyć tylko użytkownicy znający ustawienia domyślne, w tym kreatorze, gdy są to ustawienia, które chcesz użyć.  
    > -   Grupy granic nie są skojarzone z punktem dystrybucji w przypadku użycia ustawień domyślnych. W związku z tym konfigurowania grup granic, które zawierają serwera lokacji dodatkowej, klienci nie będą używać punktu dystrybucji zainstalowanego w tej lokacji dodatkowej jako lokalizacji źródła zawartości.  

5.  Na **plików źródłowych instalacji** wybierz uzyskiwania plików źródłowych instalacji lokacji komputera lokacji dodatkowej.  

     Używając plików źródłowych, które są przechowywane w sieci lub przechowywane na komputerze lokacji dodatkowej:  

    -   Lokalizacja pliku źródłowego musi zawierać folder o nazwie **Redist** zawierającej wszystkie pliki, które zostały wcześniej pobrane przy użyciu narzędzia pobierania Instalatora.  

    -   Jeśli dowolny z plików z **Redist** nie są dostępne, instalacja nie powiedzie się zainstalować lokacji pomocniczej.  

    -   Konto komputera lokacji dodatkowej musi mieć **odczytu** uprawnienia do źródła pliku udziału i folderu.  

6.  Na **ustawienia programu SQL Server** Określ wersji programu SQL Server do użycia, a następnie skonfiguruj odpowiednie ustawienia.  

    > [!NOTE]  
    > Instalator nie sprawdzi informacji wprowadzonej na tej stronie do momentu rozpoczęcia instalacji. Przed kontynuowaniem należy sprawdzić te ustawienia.  

     **Zainstaluj i skonfiguruj lokalną kopię programu SQL Express na komputerze lokacji dodatkowej**  

    -   **Port usługi SQL Server**: Określ port usługi SQL Server przez program SQL Server Express. Port usługi jest zazwyczaj skonfigurowany do używania portu TCP 1433, ale można skonfigurować inny port.  

    -   **Port usługi SQL Server Broker**: Określ port usługi SQL Server Service Broker (SSB) przez program SQL Server Express. Broker usług jest zazwyczaj skonfigurowany, aby używał portu TCP 4022, ale można skonfigurować inny port. Należy określić prawidłowy port, który jest używany nie witryny lub usługi i blokuje Zapora nie ogranicza.  

    > [!IMPORTANT]  
    > Podczas instalowania programu SQL Server Express programu Configuration Manager instaluje program SQL Server 2012 Express bez dodatku service pack:  

    > -   Dla lokacji dodatkowej są obsługiwane po jego zainstalowaniu, należy uaktualnić program SQL Server Express 2012 do [obsługiwanej wersji](/sccm/core/plan-design/configs/support-for-sql-server-versions#bkmk_SQLVersions).
    > -   Ponadto jeśli nowa instalacja lokacji dodatkowej zakończy się niepowodzeniem zakończyć, ale najpierw ukończy instalację programu SQL Server Express 2012, należy zaktualizować to wystąpienie programu SQL Server Express przed programu Configuration Manager może pomyślnie ponów próbę instalacji lokacji dodatkowej.  

     **Użyj istniejącego wystąpienia programu SQL Server**  

    -   **Nazwa FQDN serwera SQL**: Przejrzyj nazwę FQDN komputera z programem SQL Server. Należy użyć lokalnego serwera z uruchomionym programem SQL Server do obsługi bazy danych lokacji dodatkowej i nie można zmodyfikować to ustawienie.  

    -   **Wystąpienie programu SQL Server**: Określ wystąpienie programu SQL Server do użycia jako bazy danych lokacji dodatkowej. Pozostaw tę opcję pustą, aby użyć wystąpienia domyślnego.  

    -   **Nazwa bazy danych lokacji programu ConfigMgr**: Określ nazwę dla bazy danych lokacji dodatkowej.  

    -   **Port usługi SQL Server Broker**: Określ port usługi SQL Server Service Broker (SSB) dla programu SQL Server do użycia. Należy określić prawidłowy port, który jest używany nie witryny lub usługi, a zapora nie ogranicza bloku.  

    > [!TIP]  
    > Zobacz [wersji programu SQL Server obsługiwane](../../../../core/plan-design/configs/support-for-sql-server-versions.md) listę wersji programu SQL Server, które obsługuje System Center Configuration Manager.  

7.  Na **punktu dystrybucji** Skonfiguruj ustawienia punktu dystrybucji, który zostanie zainstalowany na serwerze lokacji dodatkowej.  

     **Wymagane ustawienia:**  

    -   **Określ sposób komunikacji urządzeń klienckich z punktem dystrybucji**: Wybierz między HTTP i HTTPS.  

    -   **Tworzenie certyfikatu z podpisem własnym lub zaimportuj certyfikat klienta PKI**: Wybierz między przy użyciu certyfikatu z podpisem własnym (co pozwala także zezwolić na anonimowe połączenia od klientów programu Configuration Manager do biblioteki zawartości) lub importowania certyfikatu z infrastruktury kluczy publicznych.  

         Certyfikat jest używany do uwierzytelniania punktu dystrybucji do punktu zarządzania przed wysłaniem przez dany punkt dystrybucji komunikatów o stanie.  

         Aby uzyskać informacje o wymaganiach dotyczących certyfikatów, zobacz [wymagania dotyczące certyfikatu PKI dla programu Configuration Manager](https://technet.microsoft.com/library/gg699362.aspx).  

    **Ustawienia opcjonalne:**  

    -   **Instalowanie i konfigurowanie usług IIS, jeśli jest to wymagane przez program Configuration Manager**: Wybierz to ustawienie, aby umożliwić programowi Configuration Manager Zainstaluj i skonfiguruj usługi Internet Information Services (IIS) na serwerze, jeśli jest nie został jeszcze zainstalowany. Usługi IIS muszą być zainstalowane we wszystkich punktach dystrybucji.  

        > [!NOTE]  
        > To ustawienie jest opcjonalne, usługi IIS muszą znajdować się na serwerze, aby umożliwić pomyślne zainstalowanie punktu dystrybucji.  

    -   **Włącz i skonfiguruj usługi BranchCache dla tego punktu dystrybucji**.  

    -   **Opis**. Jest to opis przyjazny dla punktu dystrybucji ułatwić go rozpoznać.  

    -   **Włącz ten punkt dystrybucji dla wstępnie przygotowanej zawartości**.  

8.  Na **ustawienia dysku** Określ ustawienia dysku dla punktu dystrybucji w lokacji dodatkowej.  

     Można skonfigurować maksymalnie dwóch dysków dla biblioteki zawartości oraz dwóch dysków dla udziału pakietu. Jednak program Configuration Manager może używać dodatkowych dysków, gdy dwa pierwsze osiągną skonfigurowaną rezerwę wolnego miejsca. **Ustawienia dysku** strona jest, gdzie można skonfigurować priorytet dysków oraz ilość wolnego miejsca na każdym z dysków.  

    -   **Rezerwacja miejsca (MB) na dysku**: Wartość skonfigurowana w tym ustawieniu określa ilość wolnego miejsca na dysku przed programu Configuration Manager wybierze inny dysk, aby kontynuować proces kopiowania z tego dysku. Pliki zawartości mogą znajdować się wiele dysków.  

    -   **Lokalizacje zawartości**: Określ lokalizacje zawartości dla udziału biblioteki i pakietu zawartości. Menedżer konfiguracji kopiuje zawartość do lokalizacji głównej zawartości do momentu osiągnięcia ilości wolnego miejsca wartość określona dla **zarezerwować miejsce na dysku (MB)**.

     Domyślnie lokalizacje zawartości są skonfigurowane **automatyczne**. Lokalizacją główną zawartości jest ustawiona na dysk o największej ilości wolnego miejsca podczas instalacji. Lokalizacja dodatkowa ustawiono dysk o największej ilości wolnego miejsca po dysku podstawowego. Gdy podstawowa i pomocnicza osiągną rezerwę wolnego miejsca, programu Configuration Manager wybierze inny dostępny dysk o największej ilości wolnego miejsca, aby kontynuować proces kopiowania.  

9. Na **weryfikacji zawartości** Określ, czy ma być sprawdzana integralność plików zawartości w punkcie dystrybucji.  

    -   Po włączeniu weryfikacji zawartości zgodnie z harmonogramem, Configuration Manager zainicjuje proces w zaplanowanym czasie, a cała zawartość w punkcie dystrybucji zostanie poddana weryfikacji.  

    -   Można również skonfigurować **priorytet weryfikacji zawartości**.  

    -   Aby wyświetlić wyniki procesu weryfikacji zawartości, w konsoli programu Configuration Manager, przejdź do **monitorowanie** > **stan dystrybucji** > **stan zawartości**. Jest wyświetlana zawartość poszczególnych typów pakietu (na przykład aplikacja, pakiet aktualizacji oprogramowania i obraz rozruchowy).  

10. Na **grup granic** zarządzać grup granic, przypisanych do tego punktu dystrybucji:  

    -   Podczas wdrażania zawartości klienty muszą znajdować się grupie granic powiązanej z punktem dystrybucji, aby używać go jako lokalizacji źródłowej zawartości.  

    -   Możesz wybrać **Zezwalaj na rezerwową lokalizację źródła zawartości** opcję, aby umożliwić klientom spoza grup granic na rezerwowe używanie punktu dystrybucji jako lokalizacji źródłowej zawartości, jeśli preferowane punkty dystrybucji nie są dostępne.  

     Aby uzyskać informacje na temat preferowanych punktów dystrybucji, zobacz [podstawowe pojęcia związane z zarządzaniem zawartością](../../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md) tematu.  

11. Na **Podsumowanie** , sprawdź ustawienia, a następnie wybierz **dalej** instalacji lokacji dodatkowej. Kiedy Kreator przedstawia **ukończenia** strony, można zamknąć kreatora. Instalacja lokacji dodatkowej będzie kontynuowana w tle.  


### <a name="bkmk_verify"></a>Aby zweryfikować stan instalacji lokacji dodatkowej  

1.  W konsoli programu Configuration Manager, przejdź do **Administracja** > **konfiguracja lokacji** > **witryny**.  

2.  Wybierz serwer lokacji dodatkowej, który instaluje, a następnie wybierz **Pokaż stan instalacji**.  

    > [!TIP]  
    > Po zainstalowaniu więcej niż jednej lokacji dodatkowej jednocześnie narzędzie sprawdzania wymagań wstępnych uruchamiana dla jednej lokacji w czasie i musi się zakończyć lokację przed wykonaniem Sprawdź dalej lokacji.  

