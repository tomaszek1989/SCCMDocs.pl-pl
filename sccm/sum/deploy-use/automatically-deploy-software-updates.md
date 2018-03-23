---
title: Automatyczne wdrażanie aktualizacji oprogramowania
titleSuffix: Configuration Manager
description: Automatyczne wdrażanie aktualizacji oprogramowania, dodając nowe aktualizacje do grupy aktualizacji, która jest skojarzona z aktywnym wdrożeniu lub używając reguł ADR.
keywords: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.date: 03/22/2018
ms.topic: article
ms.prod: configuration-manager
ms.service: ''
ms.technology:
- configmgr-sum
ms.assetid: b27682de-adf8-4edd-9572-54886af8f7fb
ms.openlocfilehash: afa0bd21d23dc0be50d90452ad5dd5d909542279
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
#  <a name="BKMK_AutoDeploy"></a> Automatyczne wdrażanie aktualizacji oprogramowania  

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

 Reguły wdrażania automatycznego (ADR) można użyć zamiast dodawać nowe aktualizacje do istniejącej grupy aktualizacji oprogramowania. Zazwyczaj reguł ADR umożliwia wdrażanie comiesięcznych aktualizacji oprogramowania (znany jako aktualizacje wtorek poprawek) i zarządzania aktualizacjami definicji. Jeśli potrzebujesz pomocy ustalenie wdrożenia, które jest odpowiednie dla Ciebie metody, zobacz [wdrażania aktualizacji oprogramowania](deploy-software-updates.md).

<!--##  <a name="BKMK_AddUpdatesToExistingGroup"></a> Add software updates to a deployed update group  
After you create and deploy a software update group, you can add software updates to the update group and they will be automatically deployed.  

> [!IMPORTANT]  
>  When you add software updates to an existing software update group that has already been deployed, it might take several minutes before the additional software updates are added to the deployment.  

Use the following procedure to add software updates to an existing update group.  

#### To add software updates to an existing software update group  

1.  In the Configuration Manager console, navigate to **Software Library** > **Overview** > **Software Updates**.  

2.  Select the software updates that are to be added to the new software update group.  

3.  On the **Home** tab, in the **Update** group, click **Edit Membership**.  

4.  Select the software update group to which you want to add the software updates as members.  

5.  Click the **Software Update Groups** node to display the software update group.  

6.  Click the software update group, and in the **Home** tab, in the **Update** group, click **Show Members** to display a list of the software updates in the group.  --mstewart this is already doc'd on the SUG page. -->

##  <a name="BKMK_CreateAutomaticDeploymentRule"></a> Tworzenie reguły wdrażania automatycznego (ADR)  
Aktualizacje oprogramowania można automatycznie zatwierdzać i wdrażać przy użyciu reguły ADR. Może istnieć reguła dodająca aktualizacje oprogramowania do nowej grupy aktualizacji oprogramowania przy każdym uruchomieniu reguły lub dodająca aktualizacje oprogramowania do istniejącej grupy. Gdy zasada jest uruchamiana i dodaje aktualizacje oprogramowania do istniejącej grupy, reguła usuwa wszystkie aktualizacje z grupy, a następnie dodaje aktualizacje, które spełniają kryteria zdefiniowane przez użytkownika do grupy. 

> [!WARNING]  
>  Przed utworzeniem reguły ADR po raz pierwszy należy się upewnić, że ukończono synchronizację aktualizacji oprogramowania w lokacji. Jest to ważne podczas uruchamiania programu Configuration Manager z języka angielskiego, ponieważ klasyfikacje aktualizacji oprogramowania są wyświetlanej w języku angielskim przed pierwszą synchronizacji, a następnie wyświetlane w języku lokalnym po zainstalowaniu aktualizacji oprogramowania synchronizacja zakończyła się. Reguły utworzone przed zsynchronizowaniem aktualizacji oprogramowania mogą nie działać prawidłowo po przeprowadzeniu synchronizacji, ponieważ ciąg tekstu może nie być identyczny.  

 Aby utworzyć regułę ADR, wykonaj czynności opisane w poniższej procedurze.  

#### <a name="to-create-an-adr"></a>Aby utworzyć regułę ADR  

1.  W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** **omówienie** > **aktualizacji oprogramowania** > **reguły wdrażania automatycznego**.  

2.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz regułę wdrażania automatycznego**. Zostanie otworzony Kreator tworzenia reguły wdrażania automatycznego.  

3.  Na stronie **Ogólne** skonfiguruj następujące ustawienia:  

    -   **Nazwa**: Określ nazwę reguły ADR. Nazwa musi być unikatowa, opisywać cel reguły oraz umożliwiać jej identyfikację spośród innych reguł, w lokacji programu Configuration Manager.  

    -   **Opis elementu**: Określ opis reguły ADR. Opis powinien zawierać omówienie reguły wdrażania i inne istotne informacje, który ułatwia odróżnienie reguły od innych użytkowników. Pole opisu jest opcjonalne, jego limit długości wynosi 256 znaków i jest domyślnie puste.  

    -   **Wybierz szablon wdrażania**: Określ, czy zastosować uprzednio zapisany szablon wdrażania. Można skonfigurować szablon wdrożenia zawierający wiele wspólnych właściwości wdrożenia aktualizacji, które mogą zostać użyte podczas tworzenia reguł ADR. Szablony ułatwiają zapewnienie spójności podobnych wdrożeń oraz umożliwiają zaoszczędzenie czasu.  

         - W Kreatorze tworzenia reguły wdrażania automatycznego można wybrać jeden z wbudowanych szablonów wdrożenia aktualizacji oprogramowania. Szablon **Aktualizacje definicji** zawiera najczęściej używane ustawienia podczas wdrażania aktualizacji definicji oprogramowania. Szablon **Wtorkowe poprawki** zawiera najczęściej używane ustawienia podczas wdrażania aktualizacji oprogramowania co miesiąc.  

    -   **Kolekcja**: Określa kolekcję docelową używaną na potrzeby wdrożenia. Członkowie kolekcji otrzymają aktualizacje oprogramowania określone we wdrożeniu.  

    -   Zdecyduj, czy dodać aktualizacje oprogramowania do nowej lub istniejącej grupy aktualizacji. W większości przypadków prawdopodobnie wybierzesz opcję utworzenia nowej grupy aktualizacji oprogramowania w momencie uruchamiania reguły ADR. Można jednak wybrać istniejącą grupę, jeśli reguła jest uruchamiana na podstawie bardziej aktywnego harmonogramu. Jeśli na przykład reguła jest uruchamiana codzienne w związku z aktualizacjami definicji, można dodać aktualizacje oprogramowania do istniejącej grupy aktualizacji.  

    -   **Włącz wdrożenie po uruchomieniu tej reguły**: Określ, czy włączyć wdrożenie aktualizacji oprogramowania po uruchomieniu reguły ADR. Związku z tą specyfikacją należy wziąć pod uwagę następujące czynności:  

        -   Po włączeniu wdrożenia aktualizacje, które spełniają kryteria zdefiniowane są dodawane do grupy aktualizacji oprogramowania. Zawartość aktualizacji oprogramowania jest pobierana w razie potrzeby. Zawartość zostanie skopiowana do określonych punktach dystrybucji, a aktualizacje są wdrażane na klientach w kolekcji docelowej.  

        -   Jeśli wdrożenie nie jest włączone, aktualizacje, które spełniają kryteria zdefiniowane są dodawane do grupy aktualizacji oprogramowania. Zasady wdrażania aktualizacji oprogramowania jest skonfigurowany. Jednak aktualizacje nie będą pobierane lub wdrażane na klientach. Taka sytuacja zapewnia czasu na przygotowanie się do wdrażania aktualizacji, Sprawdź aktualizacje, które spełniają kryteria są odpowiednie, a następnie włączenie wdrożenia w późniejszym czasie.  

4.  Na stronie Ustawienia wdrożenia skonfiguruj następujące ustawienia:  

    -   **Użyj funkcji Wake-on-LAN do wzbudzania klientów w celu dokonania wymaganych wdrożeń**: Określa, czy włączyć funkcję Wake On LAN, po upływie terminu wdrożenia, aby wysłać pakiety wznawiania do komputerów wymagających co najmniej jednej aktualizacji oprogramowania we wdrożeniu. Wszystkie komputery, które są w stanie uśpienia w ostatecznym terminie instalacji zostaną wznowione, aby umożliwić zainicjowanie instalacji. Klienci w stanie uśpienia niewymagający aktualizacji oprogramowania w ramach wdrożenia nie zostaną wznowieni. Domyślnie to urządzenie nie jest włączone. Aby użyć tej opcji, należy skonfigurować komputery i sieci do używania funkcji Wake On LAN. 

    -   **Poziom szczegółów**: Określ poziom szczegółów komunikatów stanu przesyłanych przez komputery klienckie.  

        > [!IMPORTANT]  
        >  Podczas wdrażania aktualizacji definicji, Ustaw poziom szczegółów do **tylko błąd** aby klienci wysyłali komunikat o stanie tylko w przypadku niepowodzenia aktualizacji definicji. W przeciwnym razie klienci będą wysyłać dużo komunikatów o stanie, co może negatywnie wpływać na wydajność działania serwera lokacji.  

    -   **Ustawienie postanowień licencyjnych**: Określ, czy wdrożyć automatycznie aktualizacje oprogramowania z powiązanymi postanowieniami licencyjnymi. Niektóre aktualizacje oprogramowania, na przykład dodatki Service Pack, zawierają postanowienia licencyjne. Podczas automatycznego wdrażania aktualizacji oprogramowania postanowienia licencyjne nie będą wyświetlane, nie będzie też wyświetlana opcja ich zaakceptowania. Istnieje możliwość automatycznego wdrożenia wszystkich aktualizacji oprogramowania niezależnie od powiązanymi postanowieniami licencyjnymi, lub wdrożyć tylko aktualizacje, które nie mają powiązanymi postanowieniami licencyjnymi.  
        - Aby przejrzeć postanowienia licencyjne dotyczące aktualizacji oprogramowania, należy wybrać aktualizację oprogramowania w **wszystkie aktualizacje oprogramowania** węzła **Biblioteka oprogramowania** obszaru roboczego. Na **Home** karcie **aktualizacji** kliknij przycisk **przegląd licencji**.    
        - Aby znaleźć aktualizacje oprogramowania z powiązanymi postanowieniami licencyjnymi, można dodać **postanowień licencyjnych** kolumny do okienka wyników w **wszystkie aktualizacje oprogramowania** węzła. Kliknij nagłówek kolumny sortować według aktualizacji oprogramowania z postanowieniami licencyjnymi.  

5.  Na stronie Aktualizacje oprogramowania skonfiguruj kryteria aktualizacji oprogramowania pobieranych przez regułę ADR i dodawanych do grupy aktualizacji oprogramowania. Limit liczby aktualizacji oprogramowania w regule ADR wynosi 1000. W razie potrzeby można filtrować na rozmiar zawartości dla aktualizacji oprogramowania w zasadach wdrażania automatycznego. Aby uzyskać więcej informacji, zobacz [programu Configuration Manager i uproszczone Obsługa systemu Windows na dół systemami operacyjnymi](https://blogs.technet.microsoft.com/enterprisemobility/2016/10/07/configuration-manager-and-simplified-windows-servicing-on-down-level-operating-systems/).


6.  Na stronie Harmonogram szacowania określ, czy włączyć uruchamianie reguły ADR na podstawie harmonogramu. W przypadku włączenia tej opcji kliknij przycisk **Dostosuj** , aby skonfigurować harmonogram cykliczny. Konfiguracji czas rozpoczęcia harmonogramu jest oparty na czasie lokalnym komputera, na którym uruchomiona jest konsola programu Configuration Manager.
    - Konfiguracji czas rozpoczęcia harmonogramu jest oparty na czasie lokalnym komputera, na którym uruchomiona jest konsola programu Configuration Manager.
    - Szacowanie reguły ADR można wykonywać nawet trzy razy dziennie.
    - Nie można ustawić harmonogramie szacowania częstotliwości, która przekracza harmonogramu synchronizacji aktualizacji oprogramowania. Harmonogram synchronizacji punktu aktualizacji oprogramowania jest wyświetlany, aby ułatwić określenie częstotliwości harmonogramu oceny. 
    - Aby ręcznie uruchomić regułę ADR, wybierz regułę, a następnie na karcie **Narzędzia główne** w grupie **Reguła wdrażania automatycznego** kliknij przycisk **Uruchom teraz** .
    
       > [!NOTE]  
       >Począwszy od programu Configuration Manager w wersji 1802 reguł ADR można zaplanować do oceny przesunięcie od dnia podstawowa. To znaczy, jeśli poprawka wtorek faktycznie znajduje się w środę dla Ciebie, harmonogram oceny można ustawić dla drugi wtorek miesiąca przesunięcie przez jeden dzień. <!--1357133-->
       > - Podczas planowania oceny występuje z przesunięciem w ostatnim tygodniu miesiąca, oceny zostanie zaplanowane w ciągu ostatniego dnia miesiąca, jeśli zachodzi przesunięcie wybranego w następnym miesiącu. <!--506731-->

       > ![Przesunięcie harmonogramu niestandardowego obliczania ADR od dnia podstawowa](./media/ADR-evaluation-schedule-offset.PNG)

   
7.  Na stronie Harmonogram wdrażania skonfiguruj następujące ustawienia:  

    -   **Szacowanie harmonogramu**: Określ, czy programu Configuration Manager ma szacować dostępny czas i termin ostateczny instalacji przy użyciu czasu UTC lub czasu lokalnego komputera, na którym jest uruchomiona konsola programu Configuration Manager.  
         - Gdy wybrania czasu lokalnego, a następnie wybierz **jak najszybciej** dla **czas dostępności oprogramowania** lub **ostateczny termin instalacji**czas bieżący na komputerze z systemem konsoli programu Configuration Manager służy do oceny, kiedy aktualizacje są dostępne lub kiedy są instalowane na komputerze klienckim. Jeśli klient znajduje się w innej strefie czasowej, akcje te wystąpią, gdy czas klienta osiągnie czas oceny.  

    -   **Czas dostępności oprogramowania**: Wybierz jedną z następujących ustawień, aby określić, kiedy aktualizacje oprogramowania są dostępne dla klientów:  

        -   **Jak najszybciej**: Sprawia, że aktualizacje oprogramowania uwzględnione we wdrożeniu dostępne na komputerach klienckich tak szybko, jak to możliwe. Po utworzeniu wdrożenia tego ustawienia aktualizacje zasad klienta programu Configuration Manager. W następnym cyklu sondowania zasad klienta klienci zostaną powiadomieni o wdrożeniu i mogli uzyskać aktualizacje dostępne do instalacji.  

        -   **Określony czas**: Sprawia, że aktualizacje oprogramowania uwzględnione we wdrożeniu dostępne na komputerach klienckich na określoną datę i godzinę. Podczas tworzenia wdrożenia to ustawienie jest włączone, aktualizacje zasad klienta programu Configuration Manager. Następnie w kolejnym cyklu sondowania zasad klienta klienci zostaną powiadomieni o wdrożeniu. Aktualizacje oprogramowania we wdrożeniu nie będą jednak dostępne do zainstalowania do skonfigurowanej daty i godziny.  

    -   **Ostateczny termin instalacji**: Wybierz jedną z następujących ustawień, aby określić ostateczny termin instalacji aktualizacji oprogramowania we wdrożeniu:  

        -   **Jak najszybciej**: Wybierz to ustawienie, aby automatycznie zainstalować aktualizacje oprogramowania we wdrożeniu najszybciej, jak to możliwe.  

        -   **Określony czas**: Wybierz to ustawienie, aby automatycznie zainstalować aktualizacje oprogramowania we wdrożeniu w określonym dniu i godzinie. Configuration Manager określa ostateczny termin instalacji aktualizacji oprogramowania przez dodanie skonfigurowanego **określony czas** interwał **czas dostępności oprogramowania**.  

            - Rzeczywista instalacja ostateczny termin to czasu wyświetlanych terminu wydłużony o przypadkowy czas maksymalnie do dwóch godzin. Losowe pozwala ograniczyć potencjalny wpływ komputerów klienckich w kolekcji, instalowania aktualizacji we wdrożeniu w tym samym czasie.  
          
             - Można skonfigurować ustawienie klienta **Agent komputera** , **Wyłącz losowe generowanie terminu ostatecznego** , aby wyłączyć losowe opóźnienie instalacji wymaganych aktualizacji oprogramowania. Aby uzyskać więcej informacji, zobacz sekcję [Agent komputera](../../core/clients/deploy/about-client-settings.md#computer-agent).  

8. Na stronie Czynności użytkownika skonfiguruj następujące ustawienia:  

    -   **Powiadomienia użytkowników**: Określ, czy mają być wyświetlane powiadomienia o aktualizacjach oprogramowania w programie Software Center na komputerze klienckim zgodnie ze skonfigurowanym ustawieniem **czas dostępności oprogramowania** oraz czy wyświetlać powiadomienia użytkowników na komputerach klienckich.  

    -   **Zachowanie ostatecznego terminu wdrożenia**: Określ zachowanie pożądane po osiągnięciu ostatecznego terminu wdrożenia aktualizacji oprogramowania. Określ, czy zainstalować aktualizacje oprogramowania we wdrożeniu oraz czy uruchomić ponownie system po zainstalowaniu aktualizacji oprogramowania niezależnie od skonfigurowanego okna obsługi. Aby uzyskać więcej informacji dotyczących okien obsługi, zobacz [używanie okien obsługi](../../core/clients/manage/collections/use-maintenance-windows.md).  

    -   **Zachowanie ponownego uruchamiania urządzenia**: Określ, czy pominąć ponowne uruchomienie systemu na serwerach i stacjach roboczych, jeśli ponowne uruchomienie jest wymagane do ukończenia instalacji aktualizacji.  

        > [!WARNING]  
        >  Pominięcie ponownego uruchomienia systemu może być przydatne w środowisku serwerów lub w przypadku, gdy nie chcesz, aby komputery, na których zainstalowano aktualizacje oprogramowania, zostały domyślnie uruchomione ponownie. Może to jednak spowodować, że komputery znajdą się w stanie niezabezpieczonym, podczas gdy zezwolenie na wymuszone ponowne uruchomienie gwarantuje niezwłoczne ukończenie instalacji aktualizacji oprogramowania.  

    -   **Obsługa filtru zapisu dla urządzeń z systemem Windows Embedded**: Podczas wdrażania aktualizacji oprogramowania na urządzeniach Windows Embedded z włączoną obsługą filtru zapisu, można określić do zainstalowania aktualizacji oprogramowania na tymczasowej nakładce i zatwierdzić zmiany później lub czy zatwierdzić zmiany w ostatecznym terminie instalacji bądź w oknie konserwacji. Po zatwierdzeniu zmian w dniu ostatecznego terminu instalacji lub w oknie obsługi należy ponownie uruchomić komputer, aby trwale zapisać zmiany na urządzeniu.  

           -  Podczas wdrażania aktualizacji oprogramowania na urządzeniu z systemem Windows Embedded, upewnij się, że urządzenie jest członkiem do kolekcji ze skonfigurowanym oknem obsługi.  

    - **Zachowanie ponownej oceny wdrożenia po ponownym uruchomieniu aktualizacji oprogramowania**: Wybierz to ustawienie, aby skonfigurować wdrożenia aktualizacji oprogramowania, aby klienci uruchamiali skanowanie zgodności aktualizacji oprogramowania natychmiast po Klient instaluje aktualizacje oprogramowania i ponowne uruchomienie. To ustawienie umożliwia klientowi Sprawdź, czy są dostępne dodatkowe aktualizacje, które stają się odpowiednie po ponownym uruchomieniu klienta, instaluje je w tym samym oknie obsługi.

9. Na stronie Alerty Skonfiguruj sposób generowania alertów dotyczących tego wdrożenia w programu Configuration Manager i System Center Operations Manager. Ostatnie alerty dotyczące aktualizacji oprogramowania można wyświetlić w węźle **Aktualizacje oprogramowania** w obszarze roboczym **Biblioteka oprogramowania** .  

10. Na stronie Ustawienia pobierania skonfiguruj następujące ustawienia:  

    - Określ, czy klientów, należy pobrać i zainstalować aktualizacje, gdy są połączeni z powolną siecią lub rezerwowej lokalizacji zawartości.  

    - Określ, czy klienci Pobierz i zainstaluj aktualizacje oprogramowania z rezerwowego punktu dystrybucji, gdy zawartość aktualizacji oprogramowania nie jest dostępna w preferowanym punkcie dystrybucji.  

    - **Zezwalaj klientom na współużytkowanie zawartości z innymi klientami w tej samej podsieci**: Określ, czy włączyć usługę BranchCache dla pobierania zawartości. Aby uzyskać więcej informacji na temat usługi BranchCache, zobacz [Pojęcia związane z zarządzaniem zawartością](../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md#branchcache).  

    - **Jeśli aktualizacje oprogramowania nie są dostępne w punkcie dystrybucji w bieżącym, sąsiada lub lokacji grup, Pobierz zawartość z usługi Microsoft Updates**: Wybierz to ustawienie, aby klienci w intranecie połączone Pobierz aktualizacje oprogramowania z witryny Microsoft Update, jeśli aktualizacje nie są dostępne w punktach dystrybucji. Klienci internetowi zawsze można przejść do witryny Microsoft Update zawartości aktualizacji oprogramowania.

    - Określ, czy zezwolić klientom używającym taryfowego połączenia z Internetem na pobieranie aktualizacji oprogramowania po upływie ostatecznego terminu instalacji. Dostawcy Internetu czasami naliczają opłaty według ilości wysyłanych i odbieranych danych podczas taryfowego połączenia z Internetem.  

    > [!NOTE]  
    >  Klienci żądają lokalizacji zawartości z punktu zarządzania odnośnie do aktualizacji oprogramowania we wdrożeniu. Zachowanie pobierania jest uzależnione od konfiguracji punktu pobierania, pakietu wdrożeniowego oraz ustawień na tej stronie. Aby uzyskać więcej informacji, zobacz [Scenariusze lokalizacji źródła zawartości](../../core/plan-design/hierarchy/content-source-location-scenarios.md).  

11. Na stronie Pakiet wdrażania wybierz istniejący pakiet wdrożeniowy lub skonfiguruj następujące ustawienia, aby utworzyć nowy pakiet wdrożeniowy:  

    1.  **Nazwa**: Określ nazwę pakietu wdrożeniowego. Użyj unikatowej nazwy opisująca zawartość pakietu. Maksymalna długość to 50 znaków.  

    2.  **Opis elementu**: Określ opis zawierający informacje o pakiecie wdrożeniowym. Długość opisu jest ograniczona do 127 znaków.  

    3.  **Źródło pakietu**: Określa lokalizację plików źródłowych aktualizacji oprogramowania.  Wpisz ścieżkę sieciową do lokalizacji źródłowej, na przykład **\\\serwer\nazwa_udziału\ścieżka**, lub kliknij przycisk **Przeglądaj** , aby znaleźć lokalizację sieciową. Przed kontynuowaniem do następnej strony, należy utworzyć folder udostępniony dla plików źródłowych pakietu wdrożeniowego.  

        - Określona lokalizacja źródłowa pakietu wdrożeniowego nie może być używany przez inny pakiet wdrożeniowy oprogramowania.
        - Można zmienić lokalizację źródłową pakietu w oknie właściwości pakietu wdrażania po programu Configuration Manager tworzy pakietu wdrożeniowego. Ale jeśli zrobić, należy najpierw skopiować zawartość pierwotnego źródła pakietu do nowej lokalizacji źródłowej pakietu  
        -  Zarówno konto komputera dostawcy programu SMS, jak i użytkownik, który uruchamia kreatora w celu pobrania aktualizacji oprogramowania, muszą mieć uprawnienia systemu plików NTFS **Zapis** w lokalizacji pobierania. Aby zapobiec naruszeniu plików źródłowych aktualizacji oprogramowania przez osoby atakujące, należy odpowiednio ograniczyć dostęp do lokalizacji pobierania.  
       

    4.  **Priorytet wysyłania**: Określ priorytet wysyłania pakietu wdrożeniowego. Configuration Manager używa priorytetu wysyłania pakietu wdrożeniowego, gdy wysyła pakiet do punktów dystrybucji. Pakiety wdrożeniowe są wysyłane w kolejności priorytetu: Wysoki, średni lub niski. Pakiety o identycznych priorytetach są wysyłane w kolejności ich utworzenia. Jeżeli nie występuje zaległość, przetwarzanie pakietu rozpocznie się natychmiast niezależnie od jego priorytetu.  

12. Na stronie Punkty dystrybucji określ punkty dystrybucji lub grupy punktów dystrybucji, które będą obsługiwać pliki aktualizacji oprogramowania. Więcej informacji dotyczących punktów dystrybucji znajduje się w sekcji [Konfiguracje punktów dystrybucji](../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_configs). Ta strona jest dostępna wyłącznie w przypadku utworzenia nowego pakietu wdrożeniowego aktualizacji oprogramowania.
  

13. Na stronie Lokalizacja pobierania określ, czy pobrać pliki aktualizacji oprogramowania z Internetu lub sieci lokalnej. Skonfiguruj następujące ustawienia:  

    -   **Pobierz aktualizacje oprogramowania z Internetu**: Wybierz to ustawienie, aby pobrać aktualizacje oprogramowania z określonej lokalizacji w Internecie. To ustawienie jest domyślnie włączone.  

    -   **Pobierz aktualizacje oprogramowania z lokalizacji w sieci lokalnej**: Wybierz to ustawienie, aby pobrać aktualizacje oprogramowania z katalogu lokalnego lub folderu udostępnionego. To ustawienie jest przydatne, jeśli komputer, na którym uruchamiasz kreatora, nie ma dostępu do Internetu. Aktualizacje oprogramowania można wstępnie pobrać z dowolnego komputera z dostępem do Internetu i zapisać w lokalizacji w sieci lokalnej dostępnej dla komputera, na którym będzie uruchamiany kreator.  

14. Na stronie Wybieranie języka wybierz języki, dla których zostaną pobrane wybrane aktualizacje oprogramowania. Aktualizacje oprogramowania zostaną pobrane, pod warunkiem że będą dostępne w wybranych językach. Aktualizacje oprogramowania bez określonego języka będą pobierane zawsze. Domyślnie kreator wybierze języki skonfigurowane we właściwościach punktu aktualizacji oprogramowania. Przed przejściem do następnej strony należy wybrać co najmniej jeden język. Po wybraniu tylko języki, które nie są obsługiwane przez aktualizację oprogramowania pobranie zakończy się niepowodzeniem dla aktualizacji.  

15. Na stronie Podsumowanie przejrzyj ustawienia. Aby zapisać ustawienia w szablonie wdrożenia, kliknij przycisk **Zapisz jako szablon**. Wprowadź nazwę i wybierz ustawienia, aby uwzględnić w szablonie, a następnie kliknij przycisk **zapisać**. Aby zmienić skonfigurowane ustawienie, kliknij powiązaną stronę kreatora i zmień ustawienie.  
    -  Nazwa szablonu może zawierać alfanumeryczne znaki ASCII oraz znak **\\** (ukośnik odwrotny) lub **‘** (cudzysłów pojedynczy).  

16. Kliknij przycisk **Dalej** , aby utworzyć regułę ADR.  

 Reguła ADR zostanie uruchomiona po zakończeniu pracy kreatora. Spowoduje to dodanie aktualizacji oprogramowania, które spełniają określone kryteria do grupy aktualizacji oprogramowania. Następnie ADR pobierze aktualizacje do biblioteki zawartości na serwerze lokacji i rozpowszechnia je do skonfigurowanych punktów dystrybucji. ADR następnie wdroży grupę aktualizacji oprogramowania na klientach w kolekcji docelowej.  

##  <a name="BKMK_AddDeploymentToADR"></a> Dodawanie nowego wdrożenia do istniejącej reguły ADR  
 Po utworzeniu reguły ADR można dodać do niej dodatkowe wdrożenia. Dzięki temu można uprościć wdrażanie różnych aktualizacji w różnych kolekcjach. Dla każdego nowego wdrożenia dostępny jest pełny zakres funkcji wraz z możliwością monitorowania wdrożenia.  

#### <a name="to-add-a-new-deployment-to-an-existing-adr"></a>Aby dodać nowe wdrożenie do istniejącej reguły ADR  

1.  W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** > **omówienie** > **aktualizacji oprogramowania** > **reguły wdrażania automatycznego**, a następnie wybierz odpowiednią regułę.  

2.  Na karcie **Narzędzia główne** w grupie **Reguła wdrażania automatycznego** kliknij przycisk **Dodaj wdrożenie**. Zostanie otwarty Kreator dodawania wdrożenia.  

3.  Na stronie **Kolekcja** skonfiguruj następujące ustawienia:  

    -   **Kolekcja**: Określa kolekcję docelową używaną na potrzeby wdrożenia. Członkowie kolekcji otrzymają aktualizacje oprogramowania określone we wdrożeniu.  

    -   **Włącz wdrożenie po uruchomieniu tej reguły**: Określ, czy włączyć wdrożenie aktualizacji oprogramowania po uruchomieniu reguły ADR. Związku z tą specyfikacją należy wziąć pod uwagę następujące czynności:  

        -   Po włączeniu wdrożenia aktualizacje, które spełniają kryteria zdefiniowane są dodawane do grupy aktualizacji oprogramowania. Zawartość aktualizacji oprogramowania jest pobierana w razie potrzeby. Zawartość zostanie skopiowana do określonych punktach dystrybucji, a aktualizacje są wdrażane na klientach w kolekcji docelowej.  

        -  Jeśli wdrożenie nie jest włączone, aktualizacje, które spełniają kryteria zdefiniowane są dodawane do grupy aktualizacji oprogramowania. Zasady wdrażania aktualizacji oprogramowania jest skonfigurowany. Jednak aktualizacje nie będą pobierane lub wdrażane na klientach. Taka sytuacja zapewnia czasu na przygotowanie się do wdrażania aktualizacji, Sprawdź aktualizacje, które spełniają kryteria są odpowiednie, a następnie włączenie wdrożenia w późniejszym czasie.  

4.  Na stronie Ustawienia wdrożenia skonfiguruj następujące ustawienia:  

    -   **Użyj funkcji Wake-on-LAN do wzbudzania klientów w celu dokonania wymaganych wdrożeń**: Określa, czy włączyć funkcję Wake On LAN, po upływie terminu wdrożenia, aby wysłać pakiety wznawiania do komputerów wymagających co najmniej jednej aktualizacji oprogramowania we wdrożeniu. Wszystkie komputery, które są w stanie uśpienia w ostatecznym terminie instalacji zostaną wznowione, aby umożliwić zainicjowanie instalacji. Klienci w stanie uśpienia niewymagający aktualizacji oprogramowania w ramach wdrożenia nie zostaną wznowieni. Domyślnie to urządzenie nie jest włączone. Aby użyć tej opcji, należy skonfigurować komputery i sieci do używania funkcji Wake On LAN.  

    -   **Poziom szczegółów**: Określ poziom szczegółów komunikatów stanu przesyłanych przez komputery klienckie.  

        > [!IMPORTANT]  
        >  Wdrażając aktualizacje definicji, ustaw poziom szczegółów na **Tylko błąd** , aby klienci wysyłali komunikat o stanie tylko w przypadku niepowodzenia dostarczenia aktualizacji definicji do klienta. W przeciwnym razie klienci będą wysyłać dużo komunikatów o stanie, co może negatywnie wpływać na wydajność działania serwera lokacji.  

5.  Na stronie Harmonogram wdrażania skonfiguruj następujące ustawienia:  

    -   **Szacowanie harmonogramu**: Określ, czy programu Configuration Manager ma szacować dostępny czas i termin ostateczny instalacji przy użyciu czasu UTC lub czasu lokalnego komputera, na którym jest uruchomiona konsola programu Configuration Manager.  

           -  Gdy wybrania czasu lokalnego, a następnie wybierz **jak najszybciej** dla **czas dostępności oprogramowania** lub **ostateczny termin instalacji**czas bieżący na komputerze z systemem konsoli programu Configuration Manager służy do oceny, kiedy aktualizacje są dostępne lub kiedy są instalowane na komputerze klienckim. Jeśli klient znajduje się w innej strefie czasowej, akcje te wystąpią, gdy czas klienta osiągnie czas oceny.  

    -   **Czas dostępności oprogramowania**: Wybierz jedną z następujących ustawień, aby określić, kiedy aktualizacje oprogramowania są dostępne dla klientów:  

        -   **Jak najszybciej**: Wybierz to ustawienie, aby aktualizacje oprogramowania uwzględnione we wdrożeniu dostępne na komputerach klienckich tak szybko, jak to możliwe. Po utworzeniu wdrożenia tego ustawienia aktualizacje zasad klienta programu Configuration Manager. W następnym cyklu sondowania zasad klienta klienci zostaną powiadomieni o wdrożeniu i mogli uzyskać aktualizacje dostępne do instalacji.  

        -   **Określony czas**: Sprawia, że aktualizacje oprogramowania uwzględnione we wdrożeniu dostępne na komputerach klienckich na określoną datę i godzinę. Podczas tworzenia wdrożenia to ustawienie jest włączone, aktualizacje zasad klienta programu Configuration Manager. Następnie w kolejnym cyklu sondowania zasad klienta klienci zostaną powiadomieni o wdrożeniu. Aktualizacje oprogramowania we wdrożeniu nie będą jednak dostępne do zainstalowania do skonfigurowanej daty i godziny. 

    -   **Ostateczny termin instalacji**: Wybierz jedną z następujących ustawień, aby określić ostateczny termin instalacji aktualizacji oprogramowania we wdrożeniu:  

        -   **Jak najszybciej**: Wybierz to ustawienie, aby automatycznie zainstalować aktualizacje oprogramowania we wdrożeniu najszybciej, jak to możliwe.  

        -   **Określony czas**: Wybierz to ustawienie, aby automatycznie zainstalować aktualizacje oprogramowania we wdrożeniu w określonym dniu i godzinie. Configuration Manager określa ostateczny termin instalacji aktualizacji oprogramowania przez dodanie skonfigurowanego **określony czas** interwał **czas dostępności oprogramowania**.  

               - Rzeczywista instalacja ostateczny termin to czasu wyświetlanych terminu wydłużony o przypadkowy czas maksymalnie do dwóch godzin. Pozwala to ograniczyć potencjalny wpływ komputerów klienckich w kolekcji, instalowania aktualizacji we wdrożeniu w tym samym czasie.  
              - Można skonfigurować ustawienie klienta **Agent komputera** , **Wyłącz losowe generowanie terminu ostatecznego** , aby wyłączyć losowe opóźnienie instalacji wymaganych aktualizacji oprogramowania. Aby uzyskać więcej informacji, zobacz sekcję [Agent komputera](../../core/clients/deploy/about-client-settings.md#computer-agent).  

6.  Na stronie Czynności użytkownika skonfiguruj następujące ustawienia:  

    -   **Powiadomienia użytkowników**: Określ, czy mają być wyświetlane powiadomienia o aktualizacjach oprogramowania w programie Software Center na komputerze klienckim zgodnie ze skonfigurowanym ustawieniem **czas dostępności oprogramowania** oraz czy wyświetlać powiadomienia użytkowników na komputerach klienckich.  

    -   **Zachowanie ostatecznego terminu wdrożenia**: Określ zachowanie pożądane po osiągnięciu ostatecznego terminu wdrożenia aktualizacji oprogramowania. Określ, czy zainstalować aktualizacje oprogramowania we wdrożeniu oraz czy uruchomić ponownie system po zainstalowaniu aktualizacji oprogramowania niezależnie od skonfigurowanego okna obsługi. Aby uzyskać więcej informacji dotyczących okien obsługi, zobacz [używanie okien obsługi](../../core/clients/manage/collections/use-maintenance-windows.md).  

    -   **Zachowanie ponownego uruchamiania urządzenia**: Określ, czy pominąć ponowne uruchomienie systemu na serwerach i stacjach roboczych, jeśli ponowne uruchomienie jest wymagane do ukończenia instalacji aktualizacji.  
 
           > [!WARNING]  
           >  Pominięcie ponownego uruchomienia systemu może być przydatne w środowisku serwerów lub w przypadku, gdy nie chcesz, aby komputery, na których zainstalowano aktualizacje oprogramowania, zostały domyślnie uruchomione ponownie. Może to jednak spowodować, że komputery znajdą się w stanie niezabezpieczonym, podczas gdy zezwolenie na wymuszone ponowne uruchomienie gwarantuje niezwłoczne ukończenie instalacji aktualizacji oprogramowania.  

    - **Obsługa filtru zapisu dla urządzeń z systemem Windows Embedded**: Podczas wdrażania aktualizacji oprogramowania na urządzeniach Windows Embedded z włączoną obsługą filtru zapisu, można określić do zainstalowania aktualizacji oprogramowania na tymczasowej nakładce i zatwierdzić zmiany później lub czy zatwierdzić zmiany w ostatecznym terminie instalacji bądź w oknie konserwacji. Po zatwierdzeniu zmian w dniu ostatecznego terminu instalacji lub w oknie obsługi należy ponownie uruchomić komputer, aby trwale zapisać zmiany na urządzeniu.  

        - Po wdrożeniu aktualizacji oprogramowania do urządzenia z systemem Windows Embedded upewnij się, że urządzenie należy do kolekcji ze skonfigurowanym oknem obsługi.  

7.  Na stronie Alerty Skonfiguruj sposób generowania alertów dotyczących tego wdrożenia w programu Configuration Manager i System Center Operations Manager. Ostatnie alerty dotyczące aktualizacji oprogramowania można wyświetlić w węźle **Aktualizacje oprogramowania** w obszarze roboczym **Biblioteka oprogramowania** .  

8. Na stronie Ustawienia pobierania skonfiguruj następujące ustawienia:  

    - Określ, czy klientów, należy pobrać i zainstalować aktualizacje oprogramowania, gdy są połączeni z powolną siecią lub rezerwowej lokalizacji zawartości.  

    - Określ, czy klient ma pobrać i zainstalować aktualizacje oprogramowania z rezerwowego punktu dystrybucji, jeśli zawartość aktualizacji oprogramowania będzie niedostępna w preferowanym punkcie dystrybucji.  

    - **Zezwalaj klientom na współużytkowanie zawartości z innymi klientami w tej samej podsieci**: Określ, czy włączyć usługę BranchCache dla pobierania zawartości. Aby uzyskać więcej informacji na temat usługi BranchCache, zobacz [Pojęcia związane z zarządzaniem zawartością](../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md#branchcache).  

    - **Jeśli aktualizacje oprogramowania nie są dostępne w punkcie dystrybucji w bieżącym, sąsiada lub lokacji grup, Pobierz zawartość z usługi Microsoft Updates**: Wybierz to ustawienie, aby klienci w intranecie połączone Pobierz aktualizacje oprogramowania z witryny Microsoft Update, jeśli aktualizacje nie są dostępne w punktach dystrybucji. Klienci internetowi zawsze można przejść do witryny Microsoft Update zawartości aktualizacji oprogramowania.

    - Określ, czy zezwolić klientom używającym taryfowego połączenia z Internetem na pobieranie aktualizacji oprogramowania po upływie ostatecznego terminu instalacji. Dostawcy Internetu czasami naliczają opłaty według ilości wysyłanych i odbieranych danych podczas taryfowego połączenia z Internetem.  

    > [!NOTE]  
    > Klienci żądają lokalizacji zawartości z punktu zarządzania odnośnie do aktualizacji oprogramowania we wdrożeniu. Zachowanie pobierania jest uzależnione od konfiguracji punktu pobierania, pakietu wdrożeniowego oraz ustawień na tej stronie. Aby uzyskać więcej informacji, zobacz [Scenariusze lokalizacji źródła zawartości](../../core/plan-design/hierarchy/content-source-location-scenarios.md).  

Więcej informacji o procesie wdrażania znajduje się w sekcji [Proces wdrażania aktualizacji oprogramowania](../../sum/understand/software-updates-introduction.md#BKMK_DeploymentProcess).

## <a name="next-steps"></a>Następne kroki
[Monitorowanie aktualizacji oprogramowania](monitor-software-updates.md)
