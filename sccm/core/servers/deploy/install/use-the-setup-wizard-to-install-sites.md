---
title: Kreator instalacji | Dokumentacja firmy Microsoft
ms.custom: na
ms.date: 7/24/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1f703376-5f2c-4fd2-8209-7028c931ddc7
caps.latest.revision: "3"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 678f1b35fe6f7649dacb766f7c671f4ec8ea1435
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="use-the-setup-wizard-to-install-system-center-configuration-manager-sites"></a>Instalowanie lokacji programu System Center Configuration Manager za pomocą Kreatora konfiguracji

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


Aby zainstalować nową witrynę programu System Center Configuration Manager przy użyciu interfejsu użytkownika z przewodnikiem, należy użyć Kreatora instalacji programu Configuration Manager (setup.exe). Kreator obsługuje instalowanie lokacji głównej lub centralnej lokacji administracyjnej. Możesz także użyć kreatora do [uaktualnienie instalacji wersji ewaluacyjnej](../../../../core/servers/deploy/install/upgrade-an-evaluation-install-to-a-full-install.md) programu Configuration Manager do w pełni licencjonowanej instalacji. Jeśli nie chcesz używać kreatora, należy użyć [skrypt instalacji](../../../../core/servers/deploy/install/use-a-command-line-to-install-sites.md) i uruchomić instalację nienadzorowaną wiersza polecenia.

Aby zainstalować lokację dodatkową, należy zainstalować lokacji z poziomu konsoli programu Configuration Manager. Lokacje dodatkowe nie obsługują instalację skryptową wiersza polecenia.

## <a name="bkmk_primary"></a>Instalowanie centralnej lokacji administracyjnej lub lokacji głównej
Użyj poniższej procedury do zainstalowania centralnej lokacji administracyjnej lub lokacji głównej lub uaktualnić lokację w wersji ewaluacyjne do pełni licencjonowanej lokacji programu Configuration Manager.   

Przed rozpoczęciem instalacji lokacji, należy zapoznać się ze szczegółowymi informacjami w następujących artykułach:
 -  [Przygotowanie do zainstalowania lokacji](../../../../core/servers/deploy/install/prepare-to-install-sites.md)
 -  [Wymagania wstępne dotyczące instalowania lokacji](../../../../core/servers/deploy/install/prerequisites-for-installing-sites.md)

Jeśli instalujesz centralną lokację administracyjną w ramach scenariusza rozszerzania lokacji, przejrzyj [rozszerzania autonomicznej lokacji głównej](../../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md#bkmk_expand) tego tematu, aby można było używać poniższej procedury.

### <a name="bkmk_installpri"></a>Aby zainstalować lokację głównej lub centralnej administracji

1.  Na komputerze, na którym chcesz zainstalować lokację, uruchom  **&lt;InstallationMedia\>\SMSSETUP\BIN\X64\Setup.exe** uruchomić **Kreatora instalacji programu System Center Configuration Manager**.  

    > [!NOTE]  
    > Podczas instalowania centralnej lokacji administracyjnej rozszerzania autonomicznej lokacji głównej, lub instalowania nowej podrzędnej lokacji głównej w istniejącej hierarchii, należy użyć nośnika instalacyjnego (plików źródłowych), który jest zgodny z wersją istniejącej lokacji lub lokacji. Jeśli po zainstalowaniu aktualizacji w konsoli, które zmieniły wersję zainstalowanych wcześniej lokacji, nie używaj oryginalnego nośnika instalacyjnego. Zamiast tego należy użyć plików źródłowych z [dysku CD. Najnowszy folder](../../../../core/servers/manage/the-cd.latest-folder.md) zaktualizowane witryny. Configuration Manager wymaga użycia plików źródłowych odpowiadających wersji istniejącej lokacji, które będą się łączyć nowej witryny.  

2.  Na **przed rozpoczęciem** wybierz pozycję **dalej**.  

3.  Na **wprowadzenie** wybierz typ lokacji, który chcesz zainstalować:  

    -   **Centralna lokacja administracyjna**, jako pierwszą lokację nowej hierarchii lub podczas rozszerzania autonomicznej lokacji głównej:  

        Wybierz **zainstalować lokację administracji centralnej programu Configuration Manager**.  

         Podczas kolejnych kroków tej procedury są oferowane wyboru, aby zainstalować centralną lokację administracyjną jako pierwszą lokację nowej hierarchii, lub zainstalować centralną lokację administracyjną do rozszerzenia autonomicznej lokacji głównej.  

    -    **Lokacja główna**, jako autonomicznej lokacji głównej, która jest pierwszą lokację nowej hierarchii lub jako element podrzędny głównej:  

        Wybierz **zainstalować lokację główną programu Configuration Manager**.  

        > [!TIP]  
        > Zazwyczaj wybiera się jedynie opcję opcję **Użyj typowych opcji instalacji dla autonomicznej lokacji głównej** Aby zainstalować autonomiczną lokację główną w środowisku testowym. Po wybraniu tej opcji Instalator:  

        > -   Automatycznie skonfiguruje lokację jako autonomiczną lokację główną.  
        > -   Używa domyślnej ścieżki instalacji.  
        > -   Używa lokalnej instalacji domyślnego wystąpienia programu SQL Server dla bazy danych lokacji.  
        > -   Instaluje punkt zarządzania i punkt dystrybucji na komputerze serwera lokacji.  
        > -   Skonfiguruje lokację z językiem angielskim i język wyświetlania systemu operacyjnego na serwerze lokacji głównej, jeśli jest to jeden z języków obsługiwanych w programie Configuration Manager.  

4.  Na **klucz produktu** strony:
    - Wybierz, czy ma zostać zainstalowany jako wersja ewaluacyjna, czy licencjonowaną wersję programu Configuration Manager.  

      -   Jeśli wybierzesz wersję licencjonowaną, podaj klucz produktu i wybierz pozycję **dalej**.  

      -   Jeśli wybierzesz wersję ewaluacyjną, wybierz **dalej**. (Można uaktualnić instalację w wersji ewaluacyjnej do pełnej instalacji później.)  
    - Począwszy od wersji października 2016 nośnika linii bazowej 1606 wersji programu System Center Configuration Manager, można określić datę wygaśnięcia umowy Software Assurance. Na tej stronie, masz możliwość określenia **Data wygaśnięcia Software Assurance** umowy licencyjnej jako wygodny monitu dla użytkownika z tą datą. Jeśli nie zostanie wprowadzony to podczas instalacji, możesz podać go później z w konsoli programu Configuration Manager.

      > [!NOTE]   
      > Microsoft nie zweryfikować wprowadzona data wygaśnięcia i sprawdzanie oryginalności licencji nie będą używać tej daty. Należy zamiast tego należy używać go jako przypomnienie daty wygaśnięcia. Jest to przydatne, ponieważ programu Configuration Manager okresowo sprawdza dostępność nowych aktualizacji oprogramowania oferowanych w trybie online — i stan licencji gwarancji oprogramowania powinna być bieżącego, dzięki czemu masz prawo do korzystania z tych dodatkowych aktualizacji.    

      Aby uzyskać więcej informacji, zobacz [licencjonowania i gałęzi programu System Center Configuration Manager](/sccm/core/understand/learn-more-editions).

5.  Na **postanowienia licencyjne dotyczące oprogramowania firmy Microsoft** przeczytaj i zaakceptuj postanowienia licencyjne.  

6.  Na **licencje wymagań wstępnych** strony, przeczytaj i zaakceptuj postanowienia licencyjne wstępnie wymaganego oprogramowania. Instalator pobiera i automatycznie instaluje oprogramowanie w systemach lokacji lub klientów, gdy są wymagane. Przed kontynuowaniem do następnej strony, musisz zaznaczyć wszystkie pola.  

7.  Na **pobieranie plików wymaganych wstępnie** Określ, czy Instalator ma pobrać najnowsze wymagane wstępnie pliki z Internetu lub użyj wcześniej pobranych plików:  

    -   Instalator ma pobrać pliki teraz, wybierz opcję **Pobierz wymagane pliki** i określ lokalizację do zapisania plików.  

    -   Jeżeli pliki zostały wcześniej pobrane przy użyciu [Narzędzie pobierania Instalatora](../../../../core/servers/deploy/install/setup-downloader.md), wybierz pozycję **Użyj wcześniej pobranych plików** i określ folder pobierania.  

        > [!TIP]  
        > W przypadku używania wcześniej pobranych plików Sprawdź, czy ścieżka do folderu pobierania zawiera najnowszą wersję plików.  

8.  Na **wybór języka serwera** wybierz języki, które są dostępne dla konsoli programu Configuration Manager i raporty. (Język angielski jest wybrany domyślnie i nie można usunąć).  

9. Na **wybór języka klienta** wybierz języki, które są dostępne na komputerach klienckich i określ, czy włączyć obsługę wszystkich języków klienta dla klientów urządzeń przenośnych. (Język angielski jest wybrany domyślnie i nie można usunąć).  

    > [!IMPORTANT]  
    > Korzystając z centralnej lokacji administracyjnej, upewnij się, że języki klienta, które można skonfigurować w centralnej lokacji administracyjnej obejmuje wszystkie języki klienckie, które można skonfigurować w każdej podrzędnej lokacji głównej. Jest to spowodowane instalowanych z punktu dystrybucji klientów korzystać języków klienta z lokacji najwyższego poziomu podczas instalowanych z punktem zarządzania klientów korzystać języków klienta z przypisanej lokacji głównej.  

10. Na **ustawienia lokacji i instalacji** strony, określ następujące informacje dla nowej lokacji, który użytkownik instaluje:  

    -   **Kod lokacji:** [Każdy kod lokacji w hierarchii musi być unikatowa](../../../../core/servers/deploy/install/prepare-to-install-sites.md#bkmk_sitecodes) i składającej się z trzech znaków alfanumerycznych (od A do Z) i od 0 do 9. Ponieważ kody lokacji są używane w nazwach folderów, nie należy używać systemu Windows, zastrzeżonych nazw lokacji, w tym:    
        -   AUX  
        -   KON    
        -   NUL    
        -   PRN    
        -   SMS  

        > [!NOTE]  
        > Instalator nie Sprawdź, czy należy określić kod lokacji jest już używana lub jeśli ma ona zastrzeżona.  

    -   **Nazwa lokacji:** Każda lokacja wymaga podania przyjaznej nazwy, która ułatwia zidentyfikowanie lokacji.  

    -   **Folder instalacji:** To jest ścieżka folderu do instalacji programu Configuration Manager. Nie można zmienić lokalizacji po zainstalowaniu lokacji. Ponadto ścieżka nie może zawierać znaków Unicode ani końcowych spacji.  

11. Na **instalacji lokacji** strony, użyj opcji odpowiadającej Twojemu scenariuszowi:  

    -   **Instaluję centralną lokację administracyjną:**  

         Na **instalacja centralnej lokacji administracyjnej** wybierz pozycję **Zainstaluj jako pierwszą lokację w nowej hierarchii**, a następnie wybierz pozycję **dalej** aby kontynuować.  

    -   **Rozszerzam autonomiczną lokację główną do hierarchii z centralną lokacją administracyjną:**  

         Na **instalacja centralnej lokacji administracyjnej** wybierz pozycję **rozszerzyć istniejącą autonomiczną lokację główną do hierarchii**, określ nazwę FQDN serwera autonomicznej lokacji głównej, a następnie wybierz pozycję **dalej** aby kontynuować.  

         Nośniki, które należy zainstalować nową centralną lokację administracyjną musi być zgodna z wersją lokacji głównej.  

    -   **Instaluję autonomiczną lokację główną:**  

         Na **instalacja lokacji głównej** wybierz pozycję **zainstalować lokację główną jako autonomiczną**, a następnie wybierz pozycję **dalej**.  

    -   **Instaluję podrzędną lokację główną:**  

         Na **instalacja lokacji głównej** wybierz pozycję **dołączyć lokację podstawową do istniejącej hierarchii**, określ nazwę FQDN centralnej lokacji administracyjnej, a następnie wybierz pozycję **dalej**.  

12. Na **informacje o bazie danych** Podaj następujące informacje:  

    -   **Nazwa programu SQL Server (FQDN):** To jest domyślnie jako komputer serwera lokacji.

     Jeśli używasz port niestandardowy, Dodaj ten port na nazwę FQDN programu SQL Server. Aby to zrobić, wykonaj nazwę FQDN serwera oprogramowania sequel z przecinek i numer portu.   Na przykład w przypadku serwera *SQLServer1.fabrikam.com*, aby określić port skorzystaj z następujących *1551*:  **SQLServer1.fabrikam.com, 1551**

    -   **Nazwa wystąpienia:** Domyślnie to pole jest puste. Używa domyślnego wystąpienia programu SQL Server na komputerze serwera lokacji.  

    -   **Nazwa bazy danych:** Domyślnie jest to wartość to CM_&lt;Kod_lokacji\>. Mogą używać innej nazwy, który określisz.  

    -   **Port brokera usług:** Domyślnie ta jest ustawiona na używany jest domyślny port usług SQL Server Service Broker (SSB) 4022. SQL używa go do komunikowania się bezpośrednio do bazy danych lokacji w innych lokacjach.  

13. Na drugiej stronie **informacje o bazie danych** strony, można określić innych niż domyślne lokalizacje pliku danych programu SQL Server i pliku dziennika programu SQL Server dla bazy danych lokacji:  

    -   Podano domyślne lokalizacje plików dla programu SQL Server.  

    -   Można określić innych niż domyślne lokalizacje plików nie jest dostępna w przypadku używania klastra programu SQL Server.  

    -   Narzędzie sprawdzania wymagań wstępnych nie przeprowadza sprawdzenia wolnego miejsca na dysku dla innych niż domyślne lokalizacji plików.  

14. Na **ustawienia dostawcy programu SMS** strony, określ nazwę FQDN serwera, na którym chcesz zainstalować dostawcy programu SMS.  

    -   Domyślnie jest określony serwer lokacji.  

    -   Po zainstalowaniu lokacji, możesz skonfigurować dodatkowych dostawców programu SMS.  

15. Na **ustawienia komunikacji klienta** wybierz, czy skonfigurować wszystkie systemy lokacji, aby akceptowały wyłącznie komunikację HTTPS od klientów lub metoda komunikacji ma być skonfigurowana dla poszczególnych ról systemu lokacji.  

    Po wybraniu **wszystkie role systemu lokacji akceptują tylko komunikację HTTPS od klientów**, komputer kliencki musi mieć ważny certyfikat PKI do uwierzytelniania klientów. Aby uzyskać więcej informacji na temat wymagań dotyczących certyfikatów PKI, zobacz [wymagania dotyczące certyfikatu PKI dla programu Configuration Manager](https://technet.microsoft.com/library/gg699362.aspx).  

    > [!NOTE]  
    > Ten krok ma zastosowanie tylko podczas instalowania lokacji głównej. Jeśli instalujesz centralną lokację administracyjną, Pomiń ten krok.  

16. Na **ról systemu lokacji** wybierz, czy zainstalować punktu zarządzania lub punktu dystrybucji. Dla każdej roli wybranej do zainstalowania przez Instalatora:  

    -   Należy wprowadzić **FQDN** dla komputera, który będzie obsługiwać rolę i wybierz klienta metody połączenia, czy serwer będzie obsługiwać (HTTP lub HTTPS).  

    -   W przypadku wybrania **wszystkie role systemu lokacji akceptują tylko komunikację HTTPS od klientów** na poprzedniej stronie, ustawienia połączeń z klienta zostaną automatycznie skonfigurowane dla protokołu HTTPS i nie można zmienić, chyba że Przejdź wstecz i zmień ustawienie.  

    > [!NOTE]  
    > Ten krok ma zastosowanie tylko podczas instalowania lokacji głównej. Jeśli instalujesz centralną lokację administracyjną, Pomiń ten krok.  

    > [!NOTE]  
    > Aby zainstalować role systemu lokacji, Instalator używa **konta instalacji systemu lokacji**. Domyślnie używa konta komputera lokacji głównej. To konto musi być administratorem lokalnym na komputerze zdalnym, aby zainstalować rolę systemu lokacji. Jeśli to konto nie ma wymaganych uprawnień, usuń zaznaczenie ról systemu lokacji i zainstalować je później z poziomu konsoli programu Configuration Manager po skonfigurowaniu dodatkowych kont do użycia jako konta instalacji systemu lokacji.  

17. Na **dane użycia** strony, przejrzyj informacje na temat danych tego zbieranych przez firmę Microsoft, a następnie wybierz **dalej**.  

18. **Konfiguracja punktu połączenia usługi** strona jest dostępna tylko podczas instalacji:  

    -   Jeśli instalujesz autonomicznej lokacji głównej.  

    -   Jeśli instalujesz centralną lokację administracyjną.  

    > [!NOTE]  
    > Jeśli instalujesz podrzędnej lokacji głównej, należy pominąć ten krok, (Ta strona nie jest dostępna).  

     Jeśli instalujesz centralną lokację administracyjną w ramach scenariusza rozszerzania lokacji, a ta rola jest już zainstalowana w autonomicznej lokacji głównej, należy odinstalować tę rolę z autonomicznej lokacji głównej. W hierarchii jest dozwolone tylko jedno wystąpienie tej roli, i jest dozwolona tylko w lokacji najwyższego poziomu w hierarchii.  

     Po wybraniu konfiguracji dla **punkt połączenia z usługą**, wybierz **dalej**. (Po zakończeniu instalacji można zmienić tej konfiguracji z poziomu konsoli programu Configuration Manager).  

19. Na **Podsumowanie ustawień** Przejrzyj ustawienia, która zostanie wybrana. Gdy wszystko jest gotowe, wybierz pozycję **dalej** można uruchomić narzędzie sprawdzania wymagań wstępnych.  

20. Na **Sprawdzanie wymagań wstępnych instalacji** strony, wszelkie problemy, które mogą zostać zidentyfikowane są wyświetlane.  

    -   Gdy narzędzie sprawdzania wymagań wstępnych wykryje problem, wybierz element na liście, aby uzyskać więcej informacji dotyczących sposobu rozwiązania problemu.  

    -   Musisz rozwiązać każdy element ze stanem **niepowodzeniem** przed kontynuowaniem instalacji lokacji. Elementy ze stanem **ostrzeżenie** powinny zostać rozwiązane, ale nie blokują instalacji lokacji.  

    -   Po rozwiązaniu problemów, wybierz **Uruchom sprawdzanie** Aby ponownie uruchomić narzędzie sprawdzania wymagań wstępnych.  

     Po uruchomieniu narzędzia sprawdzania wymagań wstępnych i odbierania nie są sprawdzane **niepowodzeniem** stanu, możesz wybrać **Rozpocznij instalację** do rozpoczęcia instalacji lokacji.  

    > [!TIP]  
    > Oprócz uwag, które jest dostępne w kreatorze, można znaleźć dodatkowe informacje na temat problemów z wymaganiami wstępnymi, przeglądając **ConfigMgrPrereq.log** pliku w folderze głównym dysku systemowego komputera, instalowana na. Aby uzyskać listę reguły wymagań wstępnych instalacji i opisy, zobacz [listy z Sprawdzanie wymagań wstępnych programu System Center Configuration Manager](../../../../core/servers/deploy/install/list-of-prerequisite-checks.md).  

21. Na **instalacji** Instalator wyświetla stan instalacji. Po zakończeniu podstawowej instalacji serwera lokacji, będziesz mieć możliwość **Zamknij** Kreatora instalacji. Po zamknięciu Kreatora instalacji i konfiguracji początkowej lokacji kontynuowane w tle.  

    -   Można połączyć konsolę programu Configuration Manager do lokacji, przed ukończeniem instalacji. Ta konsola łączy się tylko do odczytu i umożliwia wyświetlanie obiektów oraz ustawień, ale nie ich edytowanie.  

    -   Po zakończeniu instalacji będzie można połączyć konsolę, która umożliwia edytowanie obiektów i ustawień.  


## <a name="bkmk_expand"></a>Rozszerzenia autonomicznej lokacji głównej
Jeśli po zainstalowaniu autonomicznej lokacji głównej jako pierwszej lokacji, masz opcję później rozszerzyć tę lokację w większej hierarchii, instalując centralną lokację administracyjną.   

Po rozwinięciu autonomicznej lokacji głównej, należy zainstalować nową centralną lokację administracyjną korzystającej z istniejącej autonomicznej lokacji głównej bazy danych jako odwołanie. Po zainstalowaniu nowej centralnej lokacji administracyjnej autonomiczna lokacja główna działa jako podrzędnej lokacji głównej.

-   Tylko autonomiczną lokację główną można rozszerzyć do nowej hierarchii.  

-   Tylko jedną autonomiczną lokację główną można rozszerzyć do określonej hierarchii. Nie można użyć tej opcji, aby przyłączyć dodatkowe autonomiczne Lokacje główne do tej samej hierarchii. Zamiast tego należy użyć migracji do migracji danych z jednej hierarchii do innego.  

-   Po rozszerzeniu autonomicznej lokacji w hierarchii z centralną lokacją administracyjną, można dodać dodatkowe podrzędne Lokacje główne.  

-   Aby usunąć lokację główną z hierarchii z centralną lokacją administracyjną, należy odinstalować lokację główną.  

Aby rozszerzyć lokację, należy użyć Kreatora instalacji programu System Center Configuration Manager do zainstalowania nowej centralnej lokacji administracyjnej z następującymi zastrzeżeniami:  

-   Przy użyciu tej samej wersji programu Configuration Manager jako autonomiczną lokację główną, należy zainstalować centralną lokację administracyjną.  

-   Na **wprowadzenie** strony Kreatora konfiguracji wybierz opcję instalacji centralnej lokacji administracyjnej. Na późniejszym etapie instalacji możesz wybrać opcję rozszerzenia istniejącej autonomicznej lokacji głównej.  

-   Po skonfigurowaniu **wybór języka klienta** strony dla nowej centralnej lokacji administracyjnej, musisz wybrać te same języki klienta, które są skonfigurowane dla autonomicznej lokacji głównej, która jest rozszerzanie.  

-   Na **instalacji lokacji** strony, wybierz opcję rozszerzenia autonomicznej lokacji głównej.  

Aby rozszerzyć autonomiczną lokację główną, należy najpierw zobacz [wymagania wstępne dotyczące rozszerzania lokacji](/sccm/core/servers/deploy/install/prerequisites-for-installing-sites#bkmk_expand), a następnie wykonać procedurę  *[instalacji lokacji głównej lub centralnej administracji](../../../../core/servers/deploy/install/use-the-setup-wizard-to-install-sites.md#bkmk_installpri)*we wcześniejszej części tego artykułu.


## <a name="bkmk_secondary"></a>Instalacja lokacji dodatkowej
 Aby zainstalować lokację dodatkową używa się konsoli programu Configuration Manager.  

-   Jeśli konsola, której używasz, nie jest podłączony do lokacji głównej, który ma być lokacją nadrzędną nowej lokacji dodatkowej, polecenie zainstalowania lokacji zostaną zreplikowane do prawidłowej lokacji głównej.  

-   Przed rozpoczęciem instalacji lokacji, upewnij się, że konto użytkownika ma uprawnienia wymagań wstępnych i że komputer, który będzie hostem nowej lokacji dodatkowej spełnia wszystkie wymagania wstępne dotyczące serwera lokacji dodatkowej.  

-   Po zainstalowaniu lokacji dodatkowej programu Configuration Manager skonfiguruje nową lokację w celu użycia portów komunikacyjnych klienta skonfigurowanych w nadrzędnej lokacji głównej.  

### <a name="bkmk_installsecondary"></a>Aby zainstalować lokację dodatkową  


1.  W konsoli programu Configuration Manager, przejdź do **administracji** > **konfiguracja lokacji** > **witryny**. Wybierz lokację, która będzie nadrzędną lokacją główną nowej lokacji dodatkowej.  

2.  Wybierz **Utwórz lokację dodatkową** uruchomić **Kreator tworzenia lokacji dodatkowej**.  

3.  Na **przed rozpoczęciem** pozycję Potwierdź, że wymieniona lokacja główna jest lokacji, który ma być lokacją nadrzędną nowej lokacji dodatkowej. Następnie wybierz pozycję **dalej**.  

4.  Na **ogólne** strony, podaj następujące informacje:  

    -   **Kod lokacji**: Każdy kod lokacji w hierarchii musi być unikatowa i składającej się z trzech znaków alfanumerycznych (od A do Z) i od 0 do 9. Ponieważ kody lokacji są używane w nazwach folderów, nie należy używać systemu Windows, zastrzeżonych nazw lokacji, w tym:  

        -   AUX    
        -   KON    
        -   NUL    
        -   PRN  
        -   SMS  

       > [!NOTE]  
       > Instalator nie Sprawdź, czy należy określić kod lokacji jest już w użyciu lub jeśli jest nazwą zastrzeżoną.  

    -   **Nazwa serwera lokacji**: Jest to nazwa FQDN serwera, na którym zostanie zainstalowana nowa lokacja dodatkowa.  

    -   **Nazwa witryny**: Każda lokacja wymaga podania przyjaznej nazwy, która ułatwia zidentyfikowanie lokacji.  

    -   **Folder instalacji**: To jest ścieżka folderu do instalacji programu Configuration Manager. Nie można zmienić lokalizacji po zainstalowaniu lokacji. Ścieżka nie może zawierać znaków Unicode ani końcowych spacji.  

    > [!IMPORTANT]  
    > Po określeniu szczegółów na tej stronie możesz wybrać **Podsumowanie** Aby użyć wartości domyślnych dla pozostałych opcji lokacji dodatkowej i przejść bezpośrednio do **Podsumowanie** stronie kreatora.  

    > -   Tej opcji należy używać tylko wtedy, gdy znasz domyślne ustawienia kreatora i są to ustawienia, którego chcesz użyć.  
    > -   Grupy granic nie są skojarzone z punktem dystrybucji, korzystając z ustawień domyślnych. W związku z tym dopóki nie skonfigurujesz grup granic obejmujących serwer lokacji dodatkowej, klienci nie będą używać punktu dystrybucji zainstalowanego w tej lokacji dodatkowej jako lokalizacji źródła zawartości.  

5.  Na **plików źródłowych instalacji** wybierz, jak komputera lokacji dodatkowej ma uzyskać pliki źródłowe instalacji lokacji.  

     Jeśli używasz plików źródłowych, które są przechowywane w sieci lub przechowywane na komputerze lokacji dodatkowej:  

    -   Lokalizacji plików źródłowych musi znajdować się folder o nazwie **Redist** zawierającą wszystkie pliki, które zostały wcześniej pobrane przy użyciu narzędzia pobierania Instalatora.  

    -   Jeśli dowolny z plików z **Redist** nie są dostępne, Instalator nie będzie można zainstalować lokacji pomocniczej.  

    -   Konto komputera lokacji dodatkowej musi mieć **odczytu** uprawnień do źródłowego folderu i udziału plików.  

6.  Na **ustawienia programu SQL Server** Określ wersji programu SQL Server do użycia, a następnie skonfiguruj odpowiednie ustawienia.  

    > [!NOTE]  
    > Instalator nie zweryfikować wprowadzonej na tej stronie do momentu rozpoczęcia instalacji. Przed kontynuowaniem należy sprawdzić te ustawienia.  

     **Zainstaluj i skonfiguruj lokalną kopię programu SQL Express na komputerze lokacji dodatkowej**  

    -   **Port usługi SQL Server**: Określ port usługi SQL Server dla programu SQL Server Express do użycia. Port usługi jest zazwyczaj skonfigurowany, by używał portu TCP 1433, ale można skonfigurować inny port.  

    -   **Port brokera usług serwera SQL**: Określ port usługi SQL Server Service Broker (SSB) programu SQL Server Express do użycia. Broker usług jest zazwyczaj skonfigurowany, aby używał portu TCP 4022, ale można skonfigurować inny port. Należy określić prawidłowy port, który żaden lokacji ani usługa nie używa i blokuje Zapora nie ogranicza.  

    > [!IMPORTANT]  
    > Program Configuration Manager instaluje program SQL Server Express, instaluje program SQL Server Express 2012 bez dodatku service pack:  

    > -   Dla lokacji dodatkowej do obsługi po jej zainstalowaniu należy uaktualnić program SQL Server Express 2012 do [obsługiwanej wersji](/sccm/core/plan-design/configs/support-for-sql-server-versions#bkmk_SQLVersions).
    > -   Ponadto jeśli nowa instalacja lokacji dodatkowej zakończy się niepowodzeniem zakończyć, ale najpierw ukończy instalację programu SQL Server Express 2012, musisz zaktualizować to wystąpienie programu SQL Server Express przed programu Configuration Manager mógł pomyślnie ponowić próbę instalacji lokacji dodatkowej.  

     **Użyj istniejącego wystąpienia programu SQL Server**  

    -   **Nazwa FQDN serwera SQL**: Przejrzyj nazwę FQDN komputera z programem SQL Server. Należy użyć lokalnego serwera z uruchomionym programem SQL Server do hostowania bazy danych lokacji dodatkowej, a nie można zmodyfikować to ustawienie.  

    -   **Wystąpienie programu SQL Server**: Określ wystąpienie programu SQL Server do użycia jako baza danych lokacji dodatkowej. Tę opcję, pozostaw pole puste, aby użyć wystąpienia domyślnego.  

    -   **Nazwa bazy danych lokacji programu ConfigMgr**: Określ nazwę dla bazy danych lokacji dodatkowej.  

    -   **Port brokera usług serwera SQL**: Określ port usługi SQL Server Service Broker (SSB) programu SQL Server do użycia. Należy określić prawidłowy port, czy żaden lokacji ani usługa nie używa i czy Zapora nie ogranicza bloku.  

    > [!TIP]  
    > Zobacz [wersji programu SQL Server obsługiwane](../../../../core/plan-design/configs/support-for-sql-server-versions.md) listę wersji programu SQL Server obsługiwanych przez usługę System Center Configuration Manager.  

7.  Na **punktu dystrybucji** Skonfiguruj ustawienia punktu dystrybucji, który zostanie zainstalowany na serwerze lokacji dodatkowej.  

     **Wymagane ustawienia:**  

    -   **Określ sposób komunikacji urządzeń klienckich z punktem dystrybucji**: Wybierz wartość HTTP lub HTTPS.  

    -   **Utwórz certyfikat z podpisem własnym lub zaimportuj certyfikat klienta PKI**: Wybór między przy użyciu certyfikatu z podpisem własnym (który umożliwia także połączenia anonimowe z klientów programu Configuration Manager do biblioteki zawartości) lub zaimportowania certyfikatu z infrastruktury kluczy publicznych.  

         Certyfikat jest używany do uwierzytelniania punktu dystrybucji do punktu zarządzania przed wysłaniem przez dany punkt dystrybucji komunikatów o stanie.  

         Aby uzyskać informacje o wymaganiach dotyczących certyfikatów, zobacz [wymagania dotyczące certyfikatu PKI dla programu Configuration Manager](https://technet.microsoft.com/library/gg699362.aspx).  

    **Ustawienia opcjonalne:**  

    -   **Instalowanie i konfigurowanie usług IIS, jeśli jest to wymagane przez program Configuration Manager**: Wybierz to ustawienie, aby umożliwić programowi Configuration Manager Zainstaluj i skonfiguruj usługi Internet Information Services (IIS) na serwerze, jeśli to nie jest jeszcze zainstalowana. Usługi IIS muszą być zainstalowane we wszystkich punktach dystrybucji.  

        > [!NOTE]  
        > Mimo że to ustawienie jest opcjonalne, usługi IIS muszą zainstalowane na serwerze, aby można było pomyślnie zainstalować punkt dystrybucji.  

    -   **Włącz i skonfiguruj usługę BranchCache dla tego punktu dystrybucji**.  

    -   **Opis elementu**. Jest to przyjazny opis punktu dystrybucji ułatwić jego zidentyfikowanie.  

    -   **Włącz ten punkt dystrybucji dla wstępnie przygotowanej zawartości**.  

8.  Na **ustawienia dysku** Określ ustawienia dysku dla punktu dystrybucji w lokacji dodatkowej.  

     Można skonfigurować maksymalnie dwóch dysków dla biblioteki zawartości oraz dwóch dysków dla udziału pakietu. Jednak programu Configuration Manager może używać dodatkowych dysków, gdy dwa pierwsze osiągną skonfigurowaną rezerwę wolnego miejsca. **Ustawienia dysku** strona jest, którym można skonfigurować priorytet dysków oraz ilość wolnego miejsca na każdym z dysków.  

    -   **Rezerwacja miejsca (MB) na dysku**: Wartość skonfigurowana w tym ustawieniu określa ilość wolnego miejsca na dysku przed programu Configuration Manager wybierze inny dysk, aby kontynuować proces kopiowania do tego dysku. Pliki zawartości mogą znajdować się na wielu dyskach.  

    -   **Lokalizacje zawartości**: Określ lokalizacje zawartości dla zawartości biblioteki i udziału pakietu. Menedżer konfiguracji kopiuje zawartość do lokalizacji głównej zawartości do momentu osiągnięcia ilości wolnego miejsca ustawieniu wartości określonej dla **Rezerwacja miejsca na dysku (MB)**.

     Domyślnie lokalizacje zawartości są skonfigurowane **automatyczne**. Lokalizacją główną zawartości jest ustawiona na dysk o największej ilości wolnego miejsca podczas instalacji. Dodatkowej lokalizacja jest ustawiana na dysku, który ma najwięcej wolnego miejsca na dysku po dysku podstawowego. Gdy podstawowych i pomocniczych osiągną rezerwę wolnego miejsca, programu Configuration Manager wybierze inny dostępny dysk o największej ilości wolnego miejsca, aby kontynuować proces kopiowania.  

9. Na **weryfikacji zawartości** Określ, czy można zweryfikować integralność plików zawartości w punkcie dystrybucji.  

    -   Po włączeniu weryfikacji zawartości zgodnie z harmonogramem, programu Configuration Manager zainicjuje proces w zaplanowanym czasie, a cała zawartość w punkcie dystrybucji zostanie poddana weryfikacji.  

    -   Można również skonfigurować **priorytet weryfikacji zawartości**.  

    -   Aby wyświetlić wyniki procesu weryfikacji zawartości, w konsoli programu Configuration Manager, przejdź do **monitorowanie** > **stan dystrybucji** > **stan zawartości**. Jest wyświetlana zawartość poszczególnych typów pakietu (na przykład aplikacja, pakiet aktualizacji oprogramowania i obraz rozruchowy).  

10. Na **grup granic** możesz zarządzać grupami granic, przypisane do tego punktu dystrybucji:  

    -   Podczas wdrażania zawartości klienci muszą być w grupie granic skojarzonej z punktem dystrybucji, aby używać go jako źródłowej lokalizacji zawartości.  

    -   Możesz wybrać **Zezwalaj na rezerwową lokalizację źródła zawartości** opcję, aby umożliwić klientom spoza grup granic na rezerwowe używanie punktu dystrybucji jako lokalizacji źródłowej zawartości jeśli preferowane punkty dystrybucji nie są dostępne.  

     Aby uzyskać informacje na temat preferowanych punktów dystrybucji, zobacz [podstawowe pojęcia związane z zarządzaniem zawartością](../../../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md) tematu.  

11. Na **Podsumowanie** strony, sprawdź ustawienia, a następnie wybierz **dalej** do instalacji lokacji dodatkowej. Gdy Kreator wyświetli **zakończenia** strony, możesz zamknąć kreatora. Instalacja lokacji dodatkowej będzie kontynuowana w tle.  


### <a name="bkmk_verify"></a>Aby sprawdzić stan instalacji lokacji dodatkowej  

1.  W konsoli programu Configuration Manager, przejdź do **administracji** > **konfiguracja lokacji** > **witryny**.  

2.  Wybierz serwer lokacji dodatkowej, który instaluje, a następnie wybierz pozycję **Pokaż stan instalacji**.  

    > [!TIP]  
    > Po zainstalowaniu więcej niż jednej lokacji dodatkowej jednocześnie narzędzie sprawdzania wymagań wstępnych jest uruchamiana dla jednej lokacji w czasie i musi zakończyć lokacji, przed wykonaniem Sprawdź dalej lokacji.  
