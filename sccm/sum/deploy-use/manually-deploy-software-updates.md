---
title: Ręczne wdrażanie aktualizacji oprogramowania
titleSuffix: Configuration Manager
description: Aby ręcznie wdrożyć aktualizacje, wybierz aktualizacje z konsoli programu Configuration Manager i ręcznie wdrożyć je, lub do grupy aktualizacji dodawać aktualizacje i wdrożenie grupy.
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.date: 12/07/2016
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.assetid: 57184274-5fea-4d79-a2b4-22e08ed26daf
ms.openlocfilehash: 3f79da78df10e97813b221ffca3df25396591fbc
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
#  <a name="BKMK_ManualDeploy"></a> Ręczne wdrażanie aktualizacji oprogramowania  

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

 Ręczne wdrażanie aktualizacji oprogramowania polega na wyborze aktualizacji oprogramowania w konsoli programu Configuration Manager i ręcznym zainicjowaniu wdrażania. Wybrane aktualizacje oprogramowania można również dodać do grupy aktualizacji, a następnie ręcznie wdrożyć daną grupę. Metodę ręcznego wdrażania stosuje się najczęściej po to, aby uaktualnić urządzenia klienckie za pomocą wymaganych aktualizacji oprogramowania przed utworzeniem reguł ADR, które będą zarządzać ciągłymi, comiesięcznymi wdrożeniami aktualizacji oprogramowania. Ponadto ta metoda umożliwia wdrażanie aktualizacji oprogramowania poza pasmem. Jeśli potrzebujesz pomocy ustalenie wdrożenia, które jest odpowiednie dla Ciebie metody, zobacz [wdrażania aktualizacji oprogramowania](deploy-software-updates.md).

 Kroki, aby ręcznie wdrożyć aktualizacje oprogramowania można znaleźć w poniższych sekcjach.  

##  <a name="BKMK_1SearchCriteria"></a> Krok 1. Określanie kryteriów wyszukiwania aktualizacji oprogramowania  
 Potencjalnie są tysiące aktualizacji oprogramowania wyświetlanych w konsoli programu Configuration Manager. Pierwszym krokiem przepływu pracy ręcznego wdrażania aktualizacji oprogramowania jest ustalenie aktualizacji do wdrożenia. Istnieje na przykład możliwość określenia kryteriów pozwalających pobrać wszystkie aktualizacje oprogramowania wymagane na ponad 50 urządzeniach klienckich, które mają klasyfikację **Zabezpieczenia** lub **Krytyczne** .  

> [!IMPORTANT]  
>  Maksymalna liczba aktualizacji oprogramowania dostępnych w ramach jednego wdrożenia wynosi 1000.  

#### <a name="to-specify-search-criteria-for-software-updates"></a>Aby określić kryteria wyszukiwania aktualizacji oprogramowania  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym Biblioteka oprogramowania rozwiń listę **Aktualizacje oprogramowania**, a następnie kliknij pozycję **Wszystkie aktualizacje oprogramowania**. Zostaną wyświetlone zsynchronizowane aktualizacje oprogramowania.  

    > [!NOTE]  
    >  Na **wszystkie aktualizacje oprogramowania** węzła, programu Configuration Manager wyświetla wyłącznie aktualizacje oprogramowania z **krytyczny** i **zabezpieczeń** klasyfikacji i zostały wydane w ciągu ostatnich 30 dni.  

3.  Wybierz w okienku wyszukiwania filtr, aby ustalić wymagane aktualizacje, wykonując jedną lub obie następujące czynności:  

    -   W polu tekstowym wyszukiwania wpisz ciąg w celu filtrowania aktualizacji oprogramowania. Wpisz na przykład identyfikator artykułu lub biuletynu dotyczącego określonej aktualizacji oprogramowania albo wprowadź ciąg występujący w tytułach kilku aktualizacji.  

    -   Kliknij przycisk **Dodaj kryteria**, wybierz odpowiednie kryteria w celu filtrowania aktualizacji, kliknij przycisk **Dodaj**, a następnie określ wartości kryteriów.  

4.  Aby rozpocząć filtrowanie aktualizacji oprogramowania, kliknij przycisk **Wyszukaj** .  

    > [!TIP]  
    >  Na karcie **Wyszukiwanie** oraz w grupie **Zapisywanie** można zapisać kryteria filtrowania.  

##  <a name="BKMK_2UpdateGroup"></a> Krok 2. Tworzenie grupy aktualizacji oprogramowania zawierającej aktualizacje oprogramowania  
 Grupy aktualizacji oprogramowania stanowią efektywną metodę organizowania aktualizacji oprogramowania podczas przygotowywania wdrożenia. Można ręcznie dodać aktualizacje oprogramowania do grupy aktualizacji oprogramowania lub programu Configuration Manager może automatycznie dodać aktualizacje oprogramowania do nowej lub istniejącej grupy aktualizacji przy użyciu reguły ADR. Aby ręcznie dodać aktualizacje oprogramowania do nowej grupy aktualizacji, wykonaj czynności opisane w poniższych procedurach.  

#### <a name="to-manually-add-software-updates-to-a-new-software-update-group"></a>Aby ręcznie dodać aktualizacje oprogramowania do nowej grupy aktualizacji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym Biblioteka oprogramowania kliknij przycisk **Aktualizacje oprogramowania**.  

3.  Wybierz aktualizacje oprogramowania, które chcesz dodać do nowej grupy aktualizacji.  

4.  Na karcie **Narzędzia główne** w grupie **Aktualizacja** kliknij przycisk **Utwórz grupę aktualizacji oprogramowania**.  

5.  Określ nazwę grupy aktualizacji oprogramowania i opcjonalnie wprowadź opis. Wprowadź nazwę i opis, które zapewniają odpowiednią ilość informacji w celu ustalenia typu aktualizacji oprogramowania znajdujących się w danej grupie. Aby kontynuować, kliknij przycisk **Utwórz**.  

6.  Kliknij węzeł **Grupy aktualizacji oprogramowania** , aby wyświetlić nową grupę aktualizacji oprogramowania.  

7.  Wybierz grupę aktualizacji oprogramowania, a następnie na karcie **Narzędzia główne** w grupie **Aktualizacja** kliknij przycisk **Pokaż członków** , aby wyświetlić listę aktualizacji oprogramowania w grupie.  

##  <a name="BKMK_3DownloadContent"></a> Krok 3. Pobieranie zawartości do grupy aktualizacji oprogramowania  
 Przed wdrożeniem aktualizacji oprogramowania można opcjonalnie pobrać zawartość aktualizacji oprogramowania znajdujących się w grupie aktualizacji. Dzięki temu istnieje możliwość sprawdzenia przed wdrożeniem aktualizacji oprogramowania, czy zawartość jest dostępna w punkcie dystrybucji. Pozwoli to zapobiec wszelkim nieoczekiwanym problemom związanym z dostarczeniem zawartości. W przypadku pominięcie tego kroku zawartość zostanie pobrana i skopiowana do punktów dystrybucji w ramach procesu wdrażania. Aby pobrać zawartość aktualizacji oprogramowania do grup aktualizacji, wykonaj czynności opisane w poniższej procedurze.  



#### <a name="to-download-content-for-the-software-update-group"></a>Aby pobrać zawartość do grupy aktualizacji oprogramowania
[!INCLUDE[downloadupdates](..\includes\downloadupdates.md)]
<!--- 1.  In the Configuration Manager console, click **Software Library**.  

2.  In the Software Library workspace, expand **Software Updates**, and click **Software Update Groups**.  

3.  Select the software update group for which you want to download content.  

4.  On the **Home** tab, in the **Update Group** group, click **Download**. The **Download Software Updates Wizard** opens.  

5.  On the **Deployment Package** page, configure the following settings:  

    1.  **Select deployment package**: Select this setting to use an existing deployment package for the software updates in the deployment.  

        > [!NOTE]  
        >  Software updates that have already been downloaded to the selected deployment package are not downloaded again.  

    2.  **Create a new deployment package**: Select this setting to create a new deployment package for the software updates in the deployment. Configure the following settings:  

        -   **Name**: Specifies the name of the deployment package. This must be a unique name that describes the package content. It is limited to 50 characters.  

        -   **Description**: Specifies the description of the deployment package. The package description provides information about the package contents and is limited to 127 characters.  

        -   **Package source**: Specifies the location of the software update source files.  Type a network path for the source location, for example, **\\\server\sharename\path**, or click **Browse** to find the network location. You must create the shared folder for the deployment package source files before you proceed to the next page.  

            > [!NOTE]  
            >  The deployment package source location that you specify cannot be used by another software deployment package.  

            > [!IMPORTANT]  
            >  The SMS Provider computer account and the user that is running the wizard to download the software updates must both have **Write** NTFS permissions on the download location. You should carefully restrict access to the download location in order to reduce the risk of attackers tampering with the software update source files.  

            > [!IMPORTANT]  
            >  You can change the package source location in the deployment package properties after Configuration Manager creates the deployment package. But if you do so, you must first copy the content from the original package source to the new package source location.  

     Click **Next**.  

6.  On the Distribution Points page, select the distribution points or distribution point groups that are used to host the software update files defined in the new deployment package, and then click **Next**.  

7.  On the Distribution Settings page, specify the following settings:  

    -   **Distribution priority**: Use this setting to specify the distribution priority for the deployment package. The distribution priority applies when the deployment package is sent to distribution points at child sites. Distribution packages are sent in priority order: **High**, **Medium**, or **Low**. Packages with identical priorities are sent in the order in which they were created. If there is no backlog, the package will process immediately regardless of its priority. By default, packages are sent using **Medium** priority.  

    -   **Distribute the content for this package to preferred distribution points**: Use this setting to enable on-demand content distribution to preferred distribution points. When this setting is enabled, the management point creates a trigger for the distribution manager to distribute the content to all preferred distribution points when a client requests the content for the package and the content is not available on any preferred distribution points. For more information about preferred distribution points and on-demand content, see [Content source location scenarios](../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md#bkmk_CSLscenarios).  

    -   **Prestaged distribution point settings**: Use this setting to specify how you want to distribute content to prestaged distribution points. Choose one of the following options:  

        -   **Automatically download content when packages are assigned to distribution points**: Use this setting to ignore the prestage settings and distribute content to the distribution point.  

        -   **Download only content changes to the distribution point**: Use this setting to prestage the initial content to the distribution point, and then distribute content changes to the distribution point.  

        -   **Manually copy the content in this package to the distribution point**: Use this setting to always prestage content on the distribution point. This is the default setting.  

         For more information about prestaging content to distribution points, see [Use Prestaged content](../../core/servers/deploy/configure/deploy-and-manage-content.md#bkmk_prestage).  

     Click **Next**.  

8.  On the Download Location page, specify location that Configuration Manager will use to download the software update source files. As needed, use the following options:  

    -   **Download software updates from the Internet**: Select this setting to download the software updates from the location on the Internet. This is the default setting.  

    -   **Download software updates from a location on the local network**: Select this setting to download software updates from a local folder or shared network folder. Use this setting when the computer running the wizard does not have Internet access.  

        > [!NOTE]  
        >  When you use this setting, download the software updates from any computer with Internet access, and then copy the software updates to a location on the local network that is accessible from the computer running the wizard.  

     Click **Next**.  

9. On the Language Selection page, specify the languages for which the selected software updates are to be downloaded, and then click **Next**. Configuration Manager downloads the software updates only if they are available in the selected languages. Software updates that are not language-specific are always downloaded.  

10. On the Summary page, verify the settings that you selected in the wizard, and then click **Next** to download the software updates.  

11. On the Completion page, verify that the software updates were successfully downloaded, and then click **Close**. --->

#### <a name="to-monitor-content-status"></a>Aby monitorować stan zawartości
1. Aby monitorować stan zawartości pod kątem aktualizacji oprogramowania, kliknij przycisk **monitorowanie** w konsoli programu Configuration Manager.  

2. W obszarze roboczym Monitorowanie rozwiń węzeł **Stan dystrybucji**, a następnie kliknij przycisk **Stan zawartości**.  

3. Wybierz pakiet aktualizacji oprogramowania wskazany uprzednio w celu pobrania aktualizacji oprogramowania w grupie aktualizacji oprogramowania.  

4. Na karcie **Narzędzia główne** w grupie **Zawartość** kliknij przycisk **Wyświetl stan**.  

##  <a name="BKMK_4DeployUpdateGroup"></a> Krok 4. Wdrożenie grupy aktualizacji oprogramowania  
 Po określeniu, które aktualizacje oprogramowania mają zostać wdrożone i dodaniu owych aktualizacji do grupy aktualizacji oprogramowania można ręcznie wdrożyć aktualizacje w grupie. Aby ręcznie wdrożyć aktualizacje oprogramowania w grupie aktualizacji oprogramowania, należy wykonać następującą procedurę.  

#### <a name="to-manually-deploy-the-software-updates-in-a-software-update-group"></a>Aby ręcznie wdrożyć aktualizacje oprogramowania w grupie aktualizacji oprogramowania:  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym Biblioteka oprogramowania rozwiń listę **Aktualizacje oprogramowania**, a następnie kliknij pozycję **Grupy aktualizacji oprogramowania**.  

3.  Wybierz grupę aktualizacji oprogramowania, które zamierzasz wdrożyć.  

4.  Na karcie **Narzędzia główne** w grupie **Wdrażanie** kliknij przycisk **Wdróż**. Zostanie otworzony **Kreator wdrażania aktualizacji oprogramowania** .  

5.  Na stronie Ogólne skonfiguruj następujące ustawienia:  

    -   **Nazwa**: Określ nazwę wdrożenia. Wdrożenie musi mieć unikatową nazwę opisującą jego cel wdrożenia i odróżniającą je od innych wdrożeń w lokacji programu Configuration Manager. Domyślnie program Configuration Manager poda automatycznie nazwę wdrożenia w następującym formacie: **Microsoft Software Updates -** <*data*><*czasu*>  

    -   **Opis elementu**: Określ opis wdrożenia. Opis zawiera omówienie wdrożenia i inne istotne informacje pomocne w identyfikacji i odróżnienia wdrożenia między innymi w lokacji programu Configuration Manager. Pole opisu jest opcjonalne, jego limit długości wynosi 256 znaków i jest domyślnie puste.  

    -   **Grupy aktualizacji oprogramowania/aktualizacji oprogramowania**: Sprawdź, czy wyświetlana grupa aktualizacji oprogramowania lub aktualizacja oprogramowania jest poprawna.  

    -   **Wybierz szablon wdrażania**: Określ, czy zastosować uprzednio zapisany szablon wdrażania. Można skonfigurować szablon wdrażania zawierający wiele wspólnych właściwości wdrożenia aktualizacji oprogramowania, a następnie zastosować go podczas wdrażania kolejnych aktualizacji oprogramowania w celu zapewnienia spójności podobnych wdrożeń oraz zaoszczędzenia czasu.  

    -   **Kolekcja**: Określ kolekcję dla wdrożenia, jeśli ma zastosowanie. Członkowie kolekcji otrzymają aktualizacje oprogramowania określone we wdrożeniu.  

6.  Na stronie Ustawienia wdrożenia skonfiguruj następujące ustawienia:  

    -   **Typ wdrożenia**: Określ typ wdrożenia dla wdrożenia aktualizacji oprogramowania. Wybierz opcję **Wymagane** , aby utworzyć wymagane wdrożenie aktualizacji oprogramowania, w ramach którego aktualizacje oprogramowania zostaną automatycznie zainstalowane na klientach przed upływem skonfigurowanego ostatecznego terminu instalacji. Wybierz opcję **Dostępne** , aby utworzyć opcjonalne wdrożenie aktualizacji oprogramowania, dostępne dla użytkowników do zainstalowania z programu Software Center.  

        > [!IMPORTANT]  
        >  Po utworzeniu wdrożenia aktualizacji oprogramowania nie będzie można zmienić jego typu.  

        > [!NOTE]  
        >  Grupy aktualizacji oprogramowania wdrożone jako **wymagane** zostaną pobrane w tle z uwzględnieniem ustawień usługi BITS, jeśli są skonfigurowane.  
        > Jednak grupy aktualizacji oprogramowania wdrożone jako **dostępne** zostaną pobrane na pierwszym planie, a ustawienia usługi BITS zostaną zignorowane.  

    -   **Użyj funkcji Wake-on-LAN do wzbudzania klientów w celu dokonania wymaganych wdrożeń**: Określ, czy włączyć funkcję Wake On LAN, po upływie terminu wdrożenia, aby wysłać pakiety wznawiania do komputerów wymagających co najmniej jednej aktualizacji oprogramowania we wdrożeniu. Wszelkie komputery w stanie uśpienia w ostatecznym terminie instalacji zostaną wznowione, aby umożliwić zainicjowanie instalacji aktualizacji oprogramowania. Klienci w stanie uśpienia niewymagający aktualizacji oprogramowania w ramach wdrożenia nie zostaną wznowieni. Domyślnie to ustawienie jest wyłączone i jest dostępne wyłącznie po wybraniu opcji **Wymagane** w ustawieniu **Typ wdrożenia**.  

        > [!WARNING]  
        >  Aby użyć tej opcji, należy skonfigurować komputery i sieci do używania funkcji Wake On LAN.  

    -   **Poziom szczegółów**: Określ poziom szczegółów komunikatów stanu przesyłanych przez komputery klienckie.  

7.  Na stronie Planowanie skonfiguruj następujące ustawienia:  

    -   **Szacowanie harmonogramu**: Określ, czy dostępny czas i ostateczny termin instalacji będzie szacowany przy użyciu czasu UTC lub czasu lokalnego komputera z konsolą programu Configuration Manager.  

        > [!NOTE]  
        >  Gdy wybrania czasu lokalnego, a następnie wybierz **jak najszybciej** dla **czas dostępności oprogramowania** lub **ostateczny termin instalacji**czas bieżący na komputerze z systemem konsoli programu Configuration Manager służy do oceny, kiedy aktualizacje są dostępne lub kiedy są instalowane na komputerze klienckim. Jeśli klient znajduje się w innej strefie czasowej, akcje te wystąpią, gdy czas klienta osiągnie czas oceny.  

    -   **Czas dostępności oprogramowania**: Wybierz jedną z następujących ustawień, aby określić, kiedy aktualizacje oprogramowania będą dostępne dla klientów:  

        -   **Jak najszybciej**: Wybierz to ustawienie, aby udostępnić aktualizacje oprogramowania we wdrożeniu klientom tak szybko, jak to możliwe. Po utworzeniu wdrożenia zasady klienta zostaną zaktualizowane, klienci zostaną powiadomieni we wdrożeniu w następnym cyklu sondowania zasad klienta, a następnie aktualizacje oprogramowania zostaną udostępnione do zainstalowania.  

        -   **Określony czas**: Wybierz to ustawienie, aby udostępnić aktualizacje oprogramowania we wdrożeniu klientów w określonym dniu i godzinie. Po utworzeniu wdrożenia zasady klienta zostaną zaktualizowane, a klienci zostaną powiadomieni we wdrożeniu w następnym cyklu sondowania zasad klienta. Aktualizacje oprogramowania we wdrożeniu nie będą jednak dostępne do zainstalowania do określonej daty i godziny.  

    -   **Ostateczny termin instalacji**: Wybierz jedną z następujących ustawień, aby określić ostateczny termin instalacji aktualizacji oprogramowania we wdrożeniu.  

        > [!NOTE]  
        >  Ustawienie ostatecznego terminu instalacji można skonfigurować wyłącznie po wybraniu opcji **Wymagane** ustawienia **Typ wdrożenia** na stronie Ustawienia wdrożenia.  

        -   **Jak najszybciej**: Wybierz to ustawienie, aby automatycznie zainstalować aktualizacje oprogramowania we wdrożeniu najszybciej, jak to możliwe.  

        -   **Określony czas**: Wybierz to ustawienie, aby automatycznie zainstalować aktualizacje oprogramowania we wdrożeniu w określonym dniu i godzinie.  

        > [!NOTE]  
        >  Rzeczywisty ostateczny termin instalacji to skonfigurowany czas wydłużony o przypadkowy czas wynoszący maksymalnie 2 godziny. Pozwala to ograniczyć potencjalny wpływ jednoczesnego instalowania aktualizacji oprogramowania we wdrożeniu przez wszystkie komputery kliencie w kolekcji docelowej.  
        >   
        >  Można skonfigurować ustawienie klienta **Agent komputera** , **Wyłącz losowe generowanie terminu ostatecznego** , aby wyłączyć losowe opóźnienie instalacji wymaganych aktualizacji oprogramowania. Aby uzyskać więcej informacji, zobacz sekcję [Agent komputera](../../core/clients/deploy/about-client-settings.md#computer-agent).  

8.  Na stronie Czynności użytkownika skonfiguruj następujące ustawienia:  

    -   **Powiadomienia użytkowników**: Określ, czy mają być wyświetlane powiadomienia o aktualizacjach oprogramowania w programie Software Center na komputerze klienckim zgodnie ze skonfigurowanym ustawieniem **czas dostępności oprogramowania** oraz czy wyświetlać powiadomienia użytkowników na komputerach klienckich. Jeśli w ustawieniu **Typ wdrożenia** na stronie Ustawienia wdrożenia wybrano opcję **Dostępne** , nie będzie można wybrać opcji **Ukryj w programie Software Center i ukryj wszystkie powiadomienia**.  

    -   **Zachowanie ostatecznego terminu wdrożenia**: Dostępne tylko wtedy, gdy **typu wdrożenia** ustawiono **wymagane** na stronie Ustawienia wdrożenia.   
    Określ zachowanie pożądane po osiągnięciu ostatecznego terminu wdrożenia aktualizacji oprogramowania. Określ, czy zainstalować aktualizacje oprogramowania we wdrożeniu oraz czy uruchomić ponownie system po zainstalowaniu aktualizacji oprogramowania niezależnie od skonfigurowanego okna obsługi. Aby uzyskać więcej informacji dotyczących okien obsługi, zobacz [używanie okien obsługi](../../core/clients/manage/collections/use-maintenance-windows.md).  

    -   **Zachowanie ponownego uruchamiania urządzenia**: Dostępne tylko wtedy, gdy **typu wdrożenia** ustawiono **wymagane** na stronie Ustawienia wdrożenia.    
    Określ, czy pominąć ponowne uruchomienie systemu na serwerach i stacjach roboczych po zainstalowaniu aktualizacji oprogramowania i ponowne uruchomienie systemu jest wymagane do ukończenia instalacji.  

        > [!IMPORTANT]  
        >  Pominięcie ponownego uruchomienia systemu może być przydatne w środowisku serwerów lub w przypadku, gdy nie chcesz, aby komputery, na których zainstalowano aktualizacje oprogramowania, zostały domyślnie uruchomione ponownie. Może to jednak spowodować, że komputery znajdą się w stanie niezabezpieczonym, podczas gdy zezwolenie na wymuszone ponowne uruchomienie gwarantuje niezwłoczne ukończenie instalacji aktualizacji oprogramowania.

    -   **Obsługa filtru zapisu dla urządzeń z systemem Windows Embedded**: Podczas wdrażania aktualizacji oprogramowania na urządzeniach Windows Embedded z włączoną obsługą filtru zapisu, można określić do zainstalowania aktualizacji oprogramowania na tymczasowej nakładce i zatwierdzić zmiany później lub czy zatwierdzić zmiany w ostatecznym terminie instalacji bądź w oknie konserwacji. Po zatwierdzeniu zmian w dniu ostatecznego terminu instalacji lub w oknie obsługi należy ponownie uruchomić komputer, aby trwale zapisać zmiany na urządzeniu.  

        > [!NOTE]  
        >  Po wdrożeniu aktualizacji oprogramowania do urządzenia z systemem Windows Embedded upewnij się, że urządzenie należy do kolekcji ze skonfigurowanym oknem obsługi.  

    - **Zachowanie ponownej oceny wdrożenia po ponownym uruchomieniu aktualizacji oprogramowania**: Począwszy od 1606 wersji programu Configuration Manager, wybierz to ustawienie, aby skonfigurować wdrożenia aktualizacji oprogramowania, aby klienci uruchamiali skanowanie zgodności aktualizacji oprogramowania natychmiast po zainstalowaniu klienta oprogramowania, aktualizacji i ponownego uruchomienia. Dzięki temu klient może wyszukiwać dodatkowe aktualizacje oprogramowania, które stają się odpowiednie po ponownym uruchomieniu komputera, a następnie instalować je (i zapewniać zgodność) w tym samym oknie obsługi.

9. Na stronie Alerty Skonfiguruj sposób generowania alertów dotyczących tego wdrożenia w programu Configuration Manager i System Center Operations Manager. Alerty można skonfigurować wyłącznie po wybraniu opcji **Wymagane** ustawienia **Typ wdrożenia** na stronie Ustawienia wdrożenia.  

    > [!NOTE]  
    >  Ostatnie alerty dotyczące aktualizacji oprogramowania można wyświetlić w węźle **Aktualizacje oprogramowania** w obszarze roboczym **Biblioteka oprogramowania** .  

10. Na stronie Ustawienia pobierania skonfiguruj następujące ustawienia:  

    - Określ, czy klient pobierze i zainstaluje aktualizacje oprogramowania przy użyciu połączenia z powolną siecią lub rezerwowej lokalizacji zawartości.  

    - Określ, czy klient ma pobrać i zainstalować aktualizacje oprogramowania z rezerwowego punktu dystrybucji, jeśli zawartość aktualizacji oprogramowania będzie niedostępna w preferowanym punkcie dystrybucji.  

    - **Zezwalaj klientom na współużytkowanie zawartości z innymi klientami w tej samej podsieci**: Określ, czy włączyć usługę BranchCache dla pobierania zawartości. Aby uzyskać więcej informacji na temat usługi BranchCache, zobacz [podstawowe pojęcia związane z zarządzaniem zawartością](../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md#branchcache).  

    - **Jeśli aktualizacje oprogramowania nie są dostępne w punkcie dystrybucji w bieżącym, sąsiada lub lokacji grup, Pobierz zawartość z usługi Microsoft Updates**: Wybierz to ustawienie, aby klienci, które są połączone z intranetem mają pobierać aktualizacje oprogramowania z witryny Microsoft Update, jeśli aktualizacje oprogramowania nie są dostępne w punktach dystrybucji. Klienci internetowi zawsze można przejść do witryny Microsoft Update zawartości aktualizacji oprogramowania.

    - Określ, czy zezwolić klientom używającym taryfowego połączenia z Internetem na pobieranie aktualizacji oprogramowania po upływie ostatecznego terminu instalacji. Dostawcy Internetu czasami naliczają opłaty według ilości wysyłanych i odbieranych danych podczas taryfowego połączenia z Internetem.  

    > [!NOTE]  
    >  Klienci żądają lokalizacji zawartości z punktu zarządzania odnośnie do aktualizacji oprogramowania we wdrożeniu. Zachowanie pobierania jest uzależnione od konfiguracji punktu pobierania, pakietu wdrożeniowego oraz ustawień na tej stronie. Aby uzyskać więcej informacji, zobacz [Scenariusze lokalizacji źródła zawartości](../../core/plan-design/hierarchy/content-source-location-scenarios.md).  

11. Jeśli wykonano procedurę [krok 3: Pobieranie zawartości do grupy aktualizacji oprogramowania](#BKMK_3DownloadContent), następnie strony pakiet wdrożeniowy, punkty dystrybucji oraz wybieranie języka nie będą wyświetlane i można przejść do kroku 15 kreatora.  

    > [!IMPORTANT]  
    >  Aktualizacje oprogramowania pobrane uprzednio do biblioteki zawartości na serwerze lokacji nie zostaną pobrane ponownie. Dotyczy to również tworzenia nowego pakietu wdrożeniowego aktualizacji oprogramowania. Jeśli pobrano wcześnie wszystkie aktualizacje oprogramowania, kreator przejdzie do strony **Wybieranie języka** (krok 15).  

12. Na stronie Pakiet wdrażania wybierz istniejący pakiet wdrożeniowy lub skonfiguruj następujące ustawienia, aby określić nowy pakiet wdrożeniowy:  

    1.  **Nazwa**: Określ nazwę pakietu wdrożeniowego. To musi być unikatowa nazwa opisująca zawartość pakietu. Maksymalna długość to 50 znaków.  

    2.  **Opis elementu**: Określ opis zawierający informacje o pakiecie wdrożeniowym. Długość opisu jest ograniczona do 127 znaków.  

    3.  **Źródło pakietu**: Określ lokalizację plików źródłowych aktualizacji oprogramowania.  Wpisz ścieżkę sieciową do lokalizacji źródłowej, na przykład **\\\serwer\nazwa_udziału\ścieżka**, lub kliknij przycisk **Przeglądaj** , aby znaleźć lokalizację sieciową. Przed kontynuowaniem do następnej strony należy utworzyć folder udostępniony dla plików źródłowych pakietu wdrożeniowego.  

        > [!NOTE]  
        >  Określona lokalizacja źródłowa pakietu wdrożeniowego nie może być używana przez inny pakiet wdrożeniowy oprogramowania.  

        > [!IMPORTANT]  
        >  Zarówno konto komputera dostawcy programu SMS, jak i użytkownik, który uruchamia kreatora w celu pobrania aktualizacji oprogramowania, muszą mieć uprawnienia systemu plików NTFS **Zapis** w lokalizacji pobierania. Aby zapobiec naruszeniu plików źródłowych aktualizacji oprogramowania przez osoby atakujące, należy odpowiednio ograniczyć dostęp do lokalizacji pobierania.  

        > [!IMPORTANT]  
        >  Można zmienić lokalizację źródłową pakietu w oknie właściwości pakietu wdrażania po programu Configuration Manager tworzy pakietu wdrożeniowego. Jednak w celu wykonania tej czynności należy najpierw skopiować zawartość z pierwotnego źródła pakietu do nowej lokalizacji źródłowej pakietu.  

    4.  **Priorytet wysyłania**: Określ priorytet wysyłania pakietu wdrożeniowego. Configuration Manager używa priorytetu wysyłania pakietu wdrożeniowego, gdy wysyła pakiet do punktów dystrybucji. Pakiety wdrożeniowe są wysyłane w kolejności priorytetu: Wysoki, średni lub niski. Pakiety o identycznych priorytetach są wysyłane w kolejności ich utworzenia. Jeżeli nie występuje zaległość, przetwarzanie pakietu rozpocznie się natychmiast niezależnie od jego priorytetu.  

13. Na stronie Punkty dystrybucji określ punkty dystrybucji lub grupy punktów dystrybucji, które będą obsługiwać pliki aktualizacji oprogramowania. Więcej informacji dotyczących punktów dystrybucji znajduje się w sekcji [Konfiguracje punktów dystrybucji](../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_configs).  

14. Na stronie Lokalizacja pobierania określ, czy pobrać pliki aktualizacji oprogramowania z Internetu lub sieci lokalnej. Skonfiguruj następujące ustawienia:  

    -   **Pobierz aktualizacje oprogramowania z Internetu**: Wybierz to ustawienie, aby pobrać aktualizacje oprogramowania z określonej lokalizacji w Internecie. To ustawienie jest domyślnie włączone.  

    -   **Pobierz aktualizacje oprogramowania z lokalizacji w sieci lokalnej**: Wybierz to ustawienie, aby pobrać aktualizacje oprogramowania z folderu lokalnego lub udostępnionego folderu sieciowego. To ustawienie jest przydatne, jeśli komputer, na którym uruchamiasz kreatora, nie ma dostępu do Internetu. Aktualizacje oprogramowania można wstępnie pobrać z dowolnego komputera z dostępem do Internetu i zapisać w lokalizacji w sieci lokalnej w celu zapewnienia późniejszego dostępu do nich na potrzeby instalacji.  

15. Na stronie Wybieranie języka wybierz języki, dla których zostaną pobrane wybrane aktualizacje oprogramowania. Aktualizacje oprogramowania zostaną pobrane, pod warunkiem że będą dostępne w wybranych językach. Aktualizacje oprogramowania bez określonego języka będą pobierane zawsze. Domyślnie kreator wybierze języki skonfigurowane we właściwościach punktu aktualizacji oprogramowania. Przed przejściem do następnej strony należy wybrać co najmniej jeden język. W przypadku wybrania wyłącznie języków nieobsługiwanych przez aktualizację oprogramowania pobranie aktualizacji oprogramowania zakończy się niepowodzeniem.  

16. Na stronie Podsumowanie przejrzyj ustawienia. Aby zapisać ustawienia w szablonie wdrożenia, kliknij przycisk **Zapisz jako szablon**, wprowadź nazwę i wybierz ustawienia, które chcesz uwzględnić w szablonie, a następnie kliknij przycisk **Zapisz**. Aby zmienić skonfigurowane ustawienie, kliknij powiązaną stronę kreatora i zmień ustawienie.  

    > [!WARNING]  
    >  Nazwa szablonu może zawierać alfanumeryczne znaki ASCII oraz znak **\\** (ukośnik odwrotny) lub **‘** (cudzysłów pojedynczy).  

17. Kliknij przycisk **Dalej** , aby wdrożyć aktualizację oprogramowania.  

 Po ukończeniu kreatora programu Configuration Manager pobierze oprogramowanie aktualizacji do biblioteki zawartości na serwerze lokacji, roześle je do skonfigurowanych punktów dystrybucji, a następnie wdraża oprogramowania grupę aktualizacji na klientach w kolekcji docelowej. Więcej informacji o procesie wdrażania znajduje się w sekcji [Proces wdrażania aktualizacji oprogramowania](../understand/software-updates-introduction.md#BKMK_DeploymentProcess).

## <a name="next-steps"></a>Następne kroki
[Monitorowanie aktualizacji oprogramowania](monitor-software-updates.md)
