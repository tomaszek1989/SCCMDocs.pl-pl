---
title: "Automatyczne wdrażanie aktualizacji oprogramowania | Dokumentacja firmy Microsoft"
description: "Automatyczne wdrażanie aktualizacji oprogramowania, dodając nowe aktualizacje do grupy aktualizacji, która jest skojarzona z aktywnym wdrożeniu lub używając reguł ADR."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: b27682de-adf8-4edd-9572-54886af8f7fb
ms.translationtype: Machine Translation
ms.sourcegitcommit: c6ee0ed635ab81b5e454e3cd85637ff3e20dbb34
ms.openlocfilehash: 804a9d7a32cfbdb498c6748c5d99a1874261c231
ms.contentlocale: pl-pl
ms.lasthandoff: 06/08/2017

---

#  <a name="BKMK_AutoDeploy"></a> Automatyczne wdrażanie aktualizacji oprogramowania  

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

 Można automatycznie wdrażać aktualizacje oprogramowania, dodając nowe aktualizacje oprogramowania do grupy aktualizacji skojarzona z aktywnym wdrożeniem lub użyć reguły wdrażania automatycznego (ADR). Zazwyczaj reguł ADR umożliwia wdrażanie comiesięcznych aktualizacji oprogramowania (znany jako aktualizacje wtorek poprawek) i zarządzania aktualizacjami definicji. Jeśli potrzebujesz pomocy ustalenie wdrożenia, które jest odpowiednie dla Ciebie metody, zobacz [wdrażania aktualizacji oprogramowania](deploy-software-updates.md)

##  <a name="BKMK_AddUpdatesToExistingGroup"></a> Dodawanie aktualizacji oprogramowania do wdrożonej grupy aktualizacji  
Po utworzeniu i wdrożeniu grupy aktualizacji oprogramowania, aktualizacje oprogramowania można dodać do grupy aktualizacji i zostaną one automatycznie wdrożone.  

> [!IMPORTANT]  
>  W przypadku dodawania aktualizacji oprogramowania do istniejącej grupy aktualizacji, która została już wdrożona, dodanie aktualizacji oprogramowania do wdrożenia może zająć kilka minut.  

Aby dodać aktualizacje oprogramowania do istniejącej grupy aktualizacji, należy wykonać następującą procedurę.  

#### <a name="to-add-software-updates-to-an-existing-software-update-group"></a>Aby dodać aktualizacje oprogramowania do istniejącej grupy aktualizacji  

1.  W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** > **omówienie** > **aktualizacji oprogramowania**.  

2.  Wybierz aktualizacje oprogramowania, które chcesz dodać do nowej grupy aktualizacji.  

3.  Na karcie **Narzędzia główne** w grupie **Aktualizacja** kliknij przycisk **Edytuj członkostwo**.  

4.  Wybierz grupę aktualizacji, do której chcesz dodać aktualizacje oprogramowania jako członków.  

5.  Kliknij węzeł **Grupy aktualizacji oprogramowania** , aby wyświetlić grupę aktualizacji oprogramowania.  

6.  Kliknij grupę aktualizacji oprogramowania, a na karcie **Narzędzia główne** w grupie **Aktualizacja** kliknij przycisk **Pokaż członków** , aby wyświetlić listę aktualizacji oprogramowania w grupie.  

##  <a name="BKMK_CreateAutomaticDeploymentRule"></a> Tworzenie reguły wdrażania automatycznego (ADR)  
Aktualizacje oprogramowania można automatycznie zatwierdzać i wdrażać przy użyciu reguły ADR. Może istnieć reguła dodająca aktualizacje oprogramowania do nowej grupy aktualizacji oprogramowania przy każdym uruchomieniu reguły lub dodająca aktualizacje oprogramowania do istniejącej grupy. Jeśli uruchomiona reguła dodaje aktualizacje oprogramowania do istniejącej grupy, reguła usuwa wszystkie aktualizacje oprogramowania z grupy, a następnie dodaje do grupy aktualizacje oprogramowania, które spełniają kryteria zdefiniowane przez użytkownika. Aby codziennie uruchamiać regułę ADR na przykład w celu wyszukania nowo wydanego oprogramowania i wdrożenia go na klientach, należy wybrać opcję utworzenia nowej grupy aktualizacji oprogramowania zamiast opcji dodawania aktualizacji oprogramowania do istniejącej grupy.  

> [!WARNING]  
>  Przed utworzeniem reguły ADR po raz pierwszy należy się upewnić, że ukończono synchronizację aktualizacji oprogramowania w lokacji. Jest to szczególnie ważne podczas uruchamiania programu Configuration Manager z języka angielskiego, ponieważ klasyfikacje aktualizacji oprogramowania są wyświetlanej w języku angielskim przed pierwszą synchronizacji, a następnie wyświetlane w języku lokalnym po ukończeniu synchronizacji aktualizacji oprogramowania. Reguły utworzone przed zsynchronizowaniem aktualizacji oprogramowania mogą nie działać prawidłowo po przeprowadzeniu synchronizacji, ponieważ ciąg tekstu może nie być identyczny.  

 Aby utworzyć regułę ADR, wykonaj czynności opisane w poniższej procedurze.  

#### <a name="to-create-an-adr"></a>Aby utworzyć regułę ADR  

1.  W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** **omówienie** > **aktualizacji oprogramowania** > **reguły wdrażania automatycznego**.  

2.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Utwórz regułę wdrażania automatycznego**. Zostanie otworzony Kreator tworzenia reguły wdrażania automatycznego.  

3.  Na stronie **Ogólne** skonfiguruj następujące ustawienia:  

    -   **Nazwa**: Określ nazwę reguły ADR. Nazwa musi być unikatowa, opisywać cel reguły oraz umożliwiać jej identyfikację spośród innych reguł, w lokacji programu Configuration Manager.  

    -   **Opis elementu**: Określ opis reguły ADR. Opis powinien zawierać omówienie reguły wdrażania i inne istotne informacje pomocne w identyfikacji reguły i odróżnienia od innych planów w lokacji programu Configuration Manager. Pole opisu jest opcjonalne, jego limit długości wynosi 256 znaków i jest domyślnie puste.  

    -   **Wybierz szablon wdrażania**: Określ, czy zastosować uprzednio zapisany szablon wdrażania. Można skonfigurować szablon wdrożenia zawierający wiele typowych właściwości wdrożenia aktualizacji oprogramowania, którego można później używać przy tworzeniu reguł ADR. Szablony ułatwiają zapewnienie spójności podobnych wdrożeń oraz umożliwiają zaoszczędzenie czasu.  

         W Kreatorze tworzenia reguły wdrażania automatycznego można wybrać jeden z wbudowanych szablonów wdrożenia aktualizacji oprogramowania. Szablon **Aktualizacje definicji** zawiera najczęściej używane ustawienia podczas wdrażania aktualizacji definicji oprogramowania. Szablon **Wtorkowe poprawki** zawiera najczęściej używane ustawienia podczas wdrażania aktualizacji oprogramowania co miesiąc.  

    -   **Kolekcja**: Określa kolekcję docelową używaną na potrzeby wdrożenia. Członkowie kolekcji otrzymają aktualizacje oprogramowania określone we wdrożeniu.  

    -   Zdecyduj, czy dodać aktualizacje oprogramowania do nowej lub istniejącej grupy aktualizacji. W większości przypadków prawdopodobnie wybierzesz opcję utworzenia nowej grupy aktualizacji oprogramowania w momencie uruchamiania reguły ADR. Można jednak wybrać istniejącą grupę, jeśli reguła jest uruchamiana na podstawie bardziej aktywnego harmonogramu. Jeśli na przykład reguła jest uruchamiana codzienne w związku z aktualizacjami definicji, można dodać aktualizacje oprogramowania do istniejącej grupy aktualizacji.  

    -   **Włącz wdrożenie po uruchomieniu tej reguły**: Określ, czy włączyć wdrożenie aktualizacji oprogramowania po uruchomieniu reguły ADR. W związku z tą specyfikacją należy wziąć pod uwagę następujące kwestie:  

        -   Po włączeniu wdrożenia aktualizacje oprogramowania spełniające kryteria zdefiniowane w regule zostaną dodane do grupy aktualizacji oprogramowania, zawartość aktualizacji oprogramowania zostanie pobrana w razie potrzeby i skopiowana do określonych punktów dystrybucji, a następnie aktualizacje oprogramowania zostaną wdrożone na klientach w kolekcji docelowej.  

        -   Jeśli wdrożenie nie zostanie włączone, aktualizacje oprogramowania spełniające kryteria zdefiniowane w regule zostaną dodane do grupy aktualizacji oprogramowania, a zasady wdrażania aktualizacji oprogramowania zostaną skonfigurowane, jednak aktualizacje oprogramowania nie zostaną pobrane ani wdrożone na klientach. Taka sytuacja zapewnia niezbędny czas na przygotowania wdrożenia aktualizacji oprogramowania, sprawdzenie, czy aktualizacje oprogramowania spełniające kryteria, są odpowiednie, a następnie włączenie wdrożenia w późniejszym czasie.  

4.  Na stronie Ustawienia wdrożenia skonfiguruj następujące ustawienia:  

    -   **Użyj funkcji Wake-on-LAN do wzbudzania klientów w celu dokonania wymaganych wdrożeń**: Określa, czy włączyć funkcję Wake On LAN, po upływie terminu wdrożenia, aby wysłać pakiety wznawiania do komputerów wymagających co najmniej jednej aktualizacji oprogramowania we wdrożeniu. Wszelkie komputery w stanie uśpienia w ostatecznym terminie instalacji zostaną wznowione, aby umożliwić zainicjowanie instalacji aktualizacji oprogramowania. Klienci w stanie uśpienia niewymagający aktualizacji oprogramowania w ramach wdrożenia nie zostaną wznowieni. Domyślnie to urządzenie nie jest włączone.  

        > [!WARNING]  
        >  Aby użyć tej opcji, należy skonfigurować komputery i sieci do używania funkcji Wake On LAN.  

    -   **Poziom szczegółów**: Określ poziom szczegółów komunikatów stanu przesyłanych przez komputery klienckie.  

        > [!IMPORTANT]  
        >  Wdrażając aktualizacje definicji, ustaw poziom szczegółów na **Tylko błąd** , aby klienci wysyłali komunikat o stanie tylko w przypadku niepowodzenia dostarczenia aktualizacji definicji do klienta. W przeciwnym razie klienci będą wysyłać dużo komunikatów o stanie, co może negatywnie wpływać na wydajność działania serwera lokacji.  

    -   **Ustawienie postanowień licencyjnych**: Określ, czy wdrożyć automatycznie aktualizacje oprogramowania z powiązanymi postanowieniami licencyjnymi. Niektóre aktualizacje oprogramowania, na przykład dodatki Service Pack, zawierają postanowienia licencyjne. Podczas automatycznego wdrażania aktualizacji oprogramowania postanowienia licencyjne nie będą wyświetlane, nie będzie też wyświetlana opcja ich zaakceptowania. Można wybrać opcję automatycznego wdrożenia wszystkich aktualizacji oprogramowania bez względu na powiązane z nimi postanowienia licencyjne lub wdrożyć tylko aktualizacje oprogramowania bez powiązanych postanowień licencyjnych.  

        > [!NOTE]  
        >  Aby przejrzeć postanowienia licencyjne aktualizacji oprogramowania, można wybrać aktualizację oprogramowania w węźle **Wszystkie aktualizacje oprogramowania** w obszarze roboczym **Biblioteka oprogramowania** , a następnie na karcie **Narzędzia główne** w grupie **Aktualizacja** kliknąć przycisk **Przejrzyj licencję**.  
        >   
        >  Aby znaleźć aktualizacje oprogramowania z powiązanymi postanowieniami licencyjnymi, można dodać kolumnę **Postanowienia licencyjne** do okienka wyników w węźle **Wszystkie aktualizacje oprogramowania** , a następnie kliknąć nagłówek kolumny, aby sortować według aktualizacji oprogramowania z postanowieniami licencyjnymi.  

5.  Na stronie Aktualizacje oprogramowania skonfiguruj kryteria aktualizacji oprogramowania pobieranych przez regułę ADR i dodawanych do grupy aktualizacji oprogramowania.  

    > [!IMPORTANT]  
    >  Limit liczby aktualizacji oprogramowania w regule ADR wynosi 1000. Aby upewnić się, że kryteria określone na tej stronie będą skutkowały pobraniem nie więcej niż 1000 aktualizacji oprogramowania, rozważ skonfigurowanie takich samych kryteriów w węźle **Wszystkie aktualizacje oprogramowania** w obszarze roboczym **Biblioteka oprogramowania** .  

    > [!NOTE]
    > Począwszy od programu Configuration Manager w wersji 1610 można filtrować na rozmiar zawartości dla aktualizacji oprogramowania w zasadach wdrażania automatycznego. Na przykład można ustawić **zawartości rozmiar (KB)** filtrowane w celu **< 2048** tylko pobrać aktualizacje oprogramowania, które są mniejsze niż 2 MB. Przy użyciu tego filtru uniemożliwia aktualizacje oprogramowania dużych automatyczne pobieranie lepsze uproszczone Obsługa systemu Windows niższego poziomu obsługi, gdy przepustowość sieci jest ograniczona. Aby uzyskać więcej informacji, zobacz [programu Configuration Manager i uproszczone Obsługa systemu Windows na dół systemami operacyjnymi](https://blogs.technet.microsoft.com/enterprisemobility/2016/10/07/configuration-manager-and-simplified-windows-servicing-on-down-level-operating-systems/).

6.  Na stronie Harmonogram szacowania określ, czy włączyć uruchamianie reguły ADR na podstawie harmonogramu. W przypadku włączenia tej opcji kliknij przycisk **Dostosuj** , aby skonfigurować harmonogram cykliczny.  

    > [!IMPORTANT]  
    >  Zostanie wyświetlony harmonogram synchronizacji punktu aktualizacji oprogramowania, aby ułatwić określenie częstotliwości harmonogramu szacowania. Nie należy konfigurować w harmonogramie szacowania częstotliwości większej niż wynikająca z harmonogramu synchronizacji aktualizacji oprogramowania. Konfiguracji czas rozpoczęcia harmonogramu jest oparty na czasie lokalnym komputera, na którym uruchomiona jest konsola programu Configuration Manager.  

    > [!NOTE]  
    >  Aby ręcznie uruchomić regułę ADR, wybierz regułę, a następnie na karcie **Narzędzia główne** w grupie **Reguła wdrażania automatycznego** kliknij przycisk **Uruchom teraz** . Przed ręcznym uruchomieniem reguły ADR upewnij się, że od czasu ostatniego uruchomienia reguły przeprowadzono synchronizację aktualizacji oprogramowania.  

    > [!IMPORTANT]  
    >  Szacowanie reguły ADR można wykonywać nawet trzy razy dziennie.  

7.  Na stronie Harmonogram wdrażania skonfiguruj następujące ustawienia:  

    -   **Szacowanie harmonogramu**: Określ, czy programu Configuration Manager ma szacować dostępny czas i termin ostateczny instalacji przy użyciu czasu UTC lub czasu lokalnego komputera, na którym jest uruchomiona konsola programu Configuration Manager.  

        > [!NOTE]  
        >  Gdy wybrania czasu lokalnego, a następnie wybierz **jak najszybciej** dla **czas dostępności oprogramowania** lub **ostateczny termin instalacji**czas bieżący na komputerze z systemem konsoli programu Configuration Manager służy do oceny, kiedy aktualizacje są dostępne lub kiedy są instalowane na komputerze klienckim. Jeśli klient znajduje się w innej strefie czasowej, akcje te wystąpią, gdy czas klienta osiągnie czas oceny.  

    -   **Czas dostępności oprogramowania**: Wybierz jedną z następujących ustawień, aby określić, kiedy aktualizacje oprogramowania są dostępne dla klientów:  

        -   **Jak najszybciej**: Wybierz to ustawienie, aby aktualizacje oprogramowania uwzględnione we wdrożeniu dostępne na komputerach klienckich tak szybko, jak to możliwe. Po utworzeniu wdrożenia tego ustawienia aktualizacje zasad klienta programu Configuration Manager. Następnie w kolejnym cyklu sondowania zasad klienta klienci zostaną powiadomieni o wdrożeniu i będą mogli uzyskać aktualizacje dostępne do zainstalowania.  

        -   **Określony czas**: Wybierz to ustawienie, aby aktualizacje oprogramowania uwzględnione we wdrożeniu dostępne na komputerach klienckich w określonym dniu i godzinie. Podczas tworzenia wdrożenia to ustawienie jest włączone, aktualizacje zasad klienta programu Configuration Manager. Następnie w kolejnym cyklu sondowania zasad klienta klienci zostaną powiadomieni o wdrożeniu. Aktualizacje oprogramowania we wdrożeniu nie będą jednak dostępne do zainstalowania do skonfigurowanej daty i godziny.  

    -   **Ostateczny termin instalacji**: Wybierz jedną z następujących ustawień, aby określić ostateczny termin instalacji aktualizacji oprogramowania we wdrożeniu:  

        -   **Jak najszybciej**: Wybierz to ustawienie, aby automatycznie zainstalować aktualizacje oprogramowania we wdrożeniu najszybciej, jak to możliwe.  

        -   **Określony czas**: Wybierz to ustawienie, aby automatycznie zainstalować aktualizacje oprogramowania we wdrożeniu w określonym dniu i godzinie. Configuration Manager określa ostateczny termin instalacji aktualizacji oprogramowania przez dodanie skonfigurowanego **określony czas** interwał **czas dostępności oprogramowania**.  

        > [!NOTE]  
        >  Rzeczywisty ostateczny termin instalacji to wyświetlany czas ostatecznego terminu wydłużony o przypadkowy czas wynoszący maksymalnie 2 godziny. Pozwala to ograniczyć potencjalny wpływ jednoczesnego instalowania aktualizacji oprogramowania we wdrożeniu przez wszystkie komputery kliencie w kolekcji docelowej.  
        >   
        >  Można skonfigurować ustawienie klienta **Agent komputera** , **Wyłącz losowe generowanie terminu ostatecznego** , aby wyłączyć losowe opóźnienie instalacji wymaganych aktualizacji oprogramowania. Aby uzyskać więcej informacji, zobacz sekcję [Agent komputera](../../core/clients/deploy/about-client-settings.md#computer-agent).  

8. Na stronie Czynności użytkownika skonfiguruj następujące ustawienia:  

    -   **Powiadomienia użytkowników**: Określ, czy mają być wyświetlane powiadomienia o aktualizacjach oprogramowania w programie Software Center na komputerze klienckim zgodnie ze skonfigurowanym ustawieniem **czas dostępności oprogramowania** oraz czy wyświetlać powiadomienia użytkowników na komputerach klienckich.  

    -   **Zachowanie ostatecznego terminu wdrożenia**: Określ zachowanie pożądane po osiągnięciu ostatecznego terminu wdrożenia aktualizacji oprogramowania. Określ, czy zainstalować aktualizacje oprogramowania we wdrożeniu oraz czy uruchomić ponownie system po zainstalowaniu aktualizacji oprogramowania niezależnie od skonfigurowanego okna obsługi. Aby uzyskać więcej informacji dotyczących okien obsługi, zobacz [używanie okien obsługi](../../core/clients/manage/collections/use-maintenance-windows.md).  

    -   **Zachowanie ponownego uruchamiania urządzenia**: Określ, czy pominąć ponowne uruchomienie systemu na serwerach i stacjach roboczych po zainstalowaniu aktualizacji oprogramowania i ponowne uruchomienie systemu jest wymagane do ukończenia instalacji.  

        > [!IMPORTANT]  
        >  Pominięcie ponownego uruchomienia systemu może być przydatne w środowisku serwerów lub w przypadku, gdy nie chcesz, aby komputery, na których zainstalowano aktualizacje oprogramowania, zostały domyślnie uruchomione ponownie. Może to jednak spowodować, że komputery znajdą się w stanie niezabezpieczonym, podczas gdy zezwolenie na wymuszone ponowne uruchomienie gwarantuje niezwłoczne ukończenie instalacji aktualizacji oprogramowania.  

    -   **Obsługa filtru zapisu dla urządzeń z systemem Windows Embedded**: Podczas wdrażania aktualizacji oprogramowania na urządzeniach Windows Embedded z włączoną obsługą filtru zapisu, można określić do zainstalowania aktualizacji oprogramowania na tymczasowej nakładce i zatwierdzić zmiany później lub czy zatwierdzić zmiany w ostatecznym terminie instalacji bądź w oknie konserwacji. Po zatwierdzeniu zmian w dniu ostatecznego terminu instalacji lub w oknie obsługi należy ponownie uruchomić komputer, aby trwale zapisać zmiany na urządzeniu.  

        > [!NOTE]  
        >  Po wdrożeniu aktualizacji oprogramowania do urządzenia z systemem Windows Embedded upewnij się, że urządzenie należy do kolekcji ze skonfigurowanym oknem obsługi.  

    - **Zachowanie ponownej oceny wdrożenia po ponownym uruchomieniu aktualizacji oprogramowania**: Począwszy od 1606 wersji programu Configuration Manager, wybierz to ustawienie, aby skonfigurować wdrożenia aktualizacji oprogramowania, aby klienci uruchamiali skanowanie zgodności aktualizacji oprogramowania natychmiast po zainstalowaniu klienta oprogramowania, aktualizacji i ponownego uruchomienia. Dzięki temu klient może wyszukiwać dodatkowe aktualizacje oprogramowania, które stają się odpowiednie po ponownym uruchomieniu komputera, a następnie instalować je (i zapewniać zgodność) w tym samym oknie obsługi.

9. Na stronie Alerty Skonfiguruj sposób generowania alertów dotyczących tego wdrożenia w programu Configuration Manager i System Center Operations Manager.  

    > [!NOTE]  
    >  Ostatnie alerty dotyczące aktualizacji oprogramowania można wyświetlić w węźle **Aktualizacje oprogramowania** w obszarze roboczym **Biblioteka oprogramowania** .  

10. Na stronie Ustawienia pobierania skonfiguruj następujące ustawienia:  

    - Określ, czy klient pobierze i zainstaluje aktualizacje oprogramowania przy użyciu połączenia z powolną siecią lub rezerwowej lokalizacji zawartości.  

    - Określ, czy klient ma pobrać i zainstalować aktualizacje oprogramowania z rezerwowego punktu dystrybucji, jeśli zawartość aktualizacji oprogramowania będzie niedostępna w preferowanym punkcie dystrybucji.  

    - **Zezwalaj klientom na współużytkowanie zawartości z innymi klientami w tej samej podsieci**: Określ, czy włączyć usługę BranchCache dla pobierania zawartości. Aby uzyskać więcej informacji na temat usługi BranchCache, zobacz [Pojęcia związane z zarządzaniem zawartością](../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md#branchcache).  

    - **Jeśli aktualizacje oprogramowania nie są dostępne w punkcie dystrybucji w bieżącym, sąsiada lub lokacji grup, Pobierz zawartość z usługi Microsoft Updates**: Wybierz to ustawienie, aby klienci, które są połączone z intranetem mają pobierać aktualizacje oprogramowania z witryny Microsoft Update, jeśli aktualizacje oprogramowania nie są dostępne w punktach dystrybucji. Klienci internetowi zawsze można przejść do witryny Microsoft Update zawartości aktualizacji oprogramowania.

    - Określ, czy zezwolić klientom używającym taryfowego połączenia z Internetem na pobieranie aktualizacji oprogramowania po upływie ostatecznego terminu instalacji. Dostawcy Internetu czasami naliczają opłaty według ilości wysyłanych i odbieranych danych podczas taryfowego połączenia z Internetem.  

    > [!NOTE]  
    >  Klienci żądają lokalizacji zawartości z punktu zarządzania odnośnie do aktualizacji oprogramowania we wdrożeniu. Zachowanie pobierania jest uzależnione od konfiguracji punktu pobierania, pakietu wdrożeniowego oraz ustawień na tej stronie. Aby uzyskać więcej informacji, zobacz [Scenariusze lokalizacji źródła zawartości](../../core/plan-design/hierarchy/content-source-location-scenarios.md).  

11. Na stronie Pakiet wdrażania wybierz istniejący pakiet wdrożeniowy lub skonfiguruj następujące ustawienia, aby utworzyć nowy pakiet wdrożeniowy:  

    1.  **Nazwa**: Określ nazwę pakietu wdrożeniowego. To musi być unikatowa nazwa opisująca zawartość pakietu. Maksymalna długość to 50 znaków.  

    2.  **Opis elementu**: Określ opis zawierający informacje o pakiecie wdrożeniowym. Długość opisu jest ograniczona do 127 znaków.  

    3.  **Źródło pakietu**: Określa lokalizację plików źródłowych aktualizacji oprogramowania.  Wpisz ścieżkę sieciową do lokalizacji źródłowej, na przykład **\\\serwer\nazwa_udziału\ścieżka**, lub kliknij przycisk **Przeglądaj** , aby znaleźć lokalizację sieciową. Przed kontynuowaniem do następnej strony należy utworzyć folder udostępniony dla plików źródłowych pakietu wdrożeniowego.  

        > [!NOTE]  
        >  Określona lokalizacja źródłowa pakietu wdrożeniowego nie może być używana przez inny pakiet wdrożeniowy oprogramowania.  

        > [!IMPORTANT]  
        >  Zarówno konto komputera dostawcy programu SMS, jak i użytkownik, który uruchamia kreatora w celu pobrania aktualizacji oprogramowania, muszą mieć uprawnienia systemu plików NTFS **Zapis** w lokalizacji pobierania. Aby zapobiec naruszeniu plików źródłowych aktualizacji oprogramowania przez osoby atakujące, należy odpowiednio ograniczyć dostęp do lokalizacji pobierania.  

        > [!IMPORTANT]  
        >  Można zmienić lokalizację źródłową pakietu w oknie właściwości pakietu wdrażania po programu Configuration Manager tworzy pakietu wdrożeniowego. Jednak w celu wykonania tej czynności należy najpierw skopiować zawartość z pierwotnego źródła pakietu do nowej lokalizacji źródłowej pakietu.  

    4.  **Priorytet wysyłania**: Określ priorytet wysyłania pakietu wdrożeniowego. Configuration Manager używa priorytetu wysyłania pakietu wdrożeniowego, gdy wysyła pakiet do punktów dystrybucji. Pakiety wdrożeniowe są wysyłane w kolejności priorytetu: Wysoki, średni lub niski. Pakiety o identycznych priorytetach są wysyłane w kolejności ich utworzenia. Jeżeli nie występuje zaległość, przetwarzanie pakietu rozpocznie się natychmiast niezależnie od jego priorytetu.  

12. Na stronie Punkty dystrybucji określ punkty dystrybucji lub grupy punktów dystrybucji, które będą obsługiwać pliki aktualizacji oprogramowania. Więcej informacji dotyczących punktów dystrybucji znajduje się w sekcji [Konfiguracje punktów dystrybucji](../../core/servers/deploy/configure/install-and-configure-distribution-points.md#bkmk_configs).  

    > [!NOTE]  
    >  Ta strona jest dostępna wyłącznie w przypadku utworzenia nowego pakietu wdrożeniowego aktualizacji oprogramowania.  

13. Na stronie Lokalizacja pobierania określ, czy pobrać pliki aktualizacji oprogramowania z Internetu lub sieci lokalnej. Skonfiguruj następujące ustawienia:  

    -   **Pobierz aktualizacje oprogramowania z Internetu**: Wybierz to ustawienie, aby pobrać aktualizacje oprogramowania z określonej lokalizacji w Internecie. To ustawienie jest domyślnie włączone.  

    -   **Pobierz aktualizacje oprogramowania z lokalizacji w sieci lokalnej**: Wybierz to ustawienie, aby pobrać aktualizacje oprogramowania z katalogu lokalnego lub folderu udostępnionego. To ustawienie jest przydatne, jeśli komputer, na którym uruchamiasz kreatora, nie ma dostępu do Internetu. Aktualizacje oprogramowania można wstępnie pobrać z dowolnego komputera z dostępem do Internetu i zapisać w lokalizacji w sieci lokalnej dostępnej dla komputera, na którym będzie uruchamiany kreator.  

14. Na stronie Wybieranie języka wybierz języki, dla których zostaną pobrane wybrane aktualizacje oprogramowania. Aktualizacje oprogramowania zostaną pobrane, pod warunkiem że będą dostępne w wybranych językach. Aktualizacje oprogramowania bez określonego języka będą pobierane zawsze. Domyślnie kreator wybierze języki skonfigurowane we właściwościach punktu aktualizacji oprogramowania. Przed przejściem do następnej strony należy wybrać co najmniej jeden język. W przypadku wybrania wyłącznie języków nieobsługiwanych przez aktualizację oprogramowania pobranie aktualizacji oprogramowania zakończy się niepowodzeniem.  

15. Na stronie Podsumowanie przejrzyj ustawienia. Aby zapisać ustawienia w szablonie wdrożenia, kliknij przycisk **Zapisz jako szablon**, wprowadź nazwę i wybierz ustawienia, które chcesz uwzględnić w szablonie, a następnie kliknij przycisk **Zapisz**. Aby zmienić skonfigurowane ustawienie, kliknij powiązaną stronę kreatora i zmień ustawienie.  

    > [!NOTE]  
    >  Nazwa szablonu może zawierać alfanumeryczne znaki ASCII oraz znak **\\** (ukośnik odwrotny) lub **‘** (cudzysłów pojedynczy).  

16. Kliknij przycisk **Dalej** , aby utworzyć regułę ADR.  

 Reguła ADR zostanie uruchomiona po zakończeniu pracy kreatora. Reguła doda aktualizacje oprogramowania spełniające określone kryteria do grupy aktualizacji oprogramowania, pobierze aktualizacje oprogramowania do biblioteki zawartości na serwerze lokacji, roześle aktualizacje oprogramowania do skonfigurowanych punktów dystrybucji, a następnie wdroży grupę aktualizacji oprogramowania na klientach z kolekcji docelowej.  

##  <a name="BKMK_AddDeploymentToADR"></a> Dodawanie nowego wdrożenia do istniejącej reguły ADR  
 Po utworzeniu reguły ADR można dodać do niej dodatkowe wdrożenia. Dzięki temu można uprościć wdrażanie różnych aktualizacji w różnych kolekcjach. Dla każdego nowego wdrożenia dostępny jest pełny zakres funkcji wraz z możliwością monitorowania wdrożenia.  

#### <a name="to-add-a-new-deployment-to-an-existing-adr"></a>Aby dodać nowe wdrożenie do istniejącej reguły ADR  

1.  W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** > **omówienie** > **aktualizacji oprogramowania** > **reguły wdrażania automatycznego**, a następnie wybierz odpowiednią regułę.  

2.  Na karcie **Narzędzia główne** w grupie **Reguła wdrażania automatycznego** kliknij przycisk **Dodaj wdrożenie**. Zostanie otwarty Kreator dodawania wdrożenia.  

3.  Na stronie **Kolekcja** skonfiguruj następujące ustawienia:  

    -   **Kolekcja**: Określa kolekcję docelową używaną na potrzeby wdrożenia. Członkowie kolekcji otrzymają aktualizacje oprogramowania określone we wdrożeniu.  

    -   **Włącz wdrożenie po uruchomieniu tej reguły**: Określ, czy włączyć wdrożenie aktualizacji oprogramowania po uruchomieniu reguły ADR. W związku z tą specyfikacją należy wziąć pod uwagę następujące kwestie:  

        -   Po włączeniu wdrożenia aktualizacje oprogramowania spełniające kryteria zdefiniowane w regule zostaną dodane do grupy aktualizacji oprogramowania, zawartość aktualizacji oprogramowania zostanie pobrana w razie potrzeby i skopiowana do określonych punktów dystrybucji, a następnie aktualizacje oprogramowania zostaną wdrożone na klientach w kolekcji docelowej.  

        -   Jeśli wdrożenie nie zostanie włączone, aktualizacje oprogramowania spełniające kryteria zdefiniowane w regule zostaną dodane do grupy aktualizacji oprogramowania, a zasady wdrażania aktualizacji oprogramowania zostaną skonfigurowane, jednak aktualizacje oprogramowania nie zostaną pobrane ani wdrożone na klientach. Taka sytuacja zapewnia niezbędny czas na przygotowania wdrożenia aktualizacji oprogramowania, sprawdzenie, czy aktualizacje oprogramowania spełniające kryteria, są odpowiednie, a następnie włączenie wdrożenia w późniejszym czasie.  

4.  Na stronie Ustawienia wdrożenia skonfiguruj następujące ustawienia:  

    -   **Użyj funkcji Wake-on-LAN do wzbudzania klientów w celu dokonania wymaganych wdrożeń**: Określa, czy włączyć funkcję Wake On LAN, po upływie terminu wdrożenia, aby wysłać pakiety wznawiania do komputerów wymagających co najmniej jednej aktualizacji oprogramowania we wdrożeniu. Wszelkie komputery w stanie uśpienia w ostatecznym terminie instalacji zostaną wznowione, aby umożliwić zainicjowanie instalacji aktualizacji oprogramowania. Klienci w stanie uśpienia niewymagający aktualizacji oprogramowania w ramach wdrożenia nie zostaną wznowieni. Domyślnie to urządzenie nie jest włączone.  

        > [!WARNING]  
        >  Aby użyć tej opcji, należy skonfigurować komputery i sieci do używania funkcji Wake On LAN.  

    -   **Poziom szczegółów**: Określ poziom szczegółów komunikatów stanu przesyłanych przez komputery klienckie.  

        > [!IMPORTANT]  
        >  Wdrażając aktualizacje definicji, ustaw poziom szczegółów na **Tylko błąd** , aby klienci wysyłali komunikat o stanie tylko w przypadku niepowodzenia dostarczenia aktualizacji definicji do klienta. W przeciwnym razie klienci będą wysyłać dużo komunikatów o stanie, co może negatywnie wpływać na wydajność działania serwera lokacji.  

5.  Na stronie Harmonogram wdrażania skonfiguruj następujące ustawienia:  

    -   **Szacowanie harmonogramu**: Określ, czy programu Configuration Manager ma szacować dostępny czas i termin ostateczny instalacji przy użyciu czasu UTC lub czasu lokalnego komputera, na którym jest uruchomiona konsola programu Configuration Manager.  

        > [!NOTE]  
        >  Gdy wybrania czasu lokalnego, a następnie wybierz **jak najszybciej** dla **czas dostępności oprogramowania** lub **ostateczny termin instalacji**czas bieżący na komputerze z systemem konsoli programu Configuration Manager służy do oceny, kiedy aktualizacje są dostępne lub kiedy są instalowane na komputerze klienckim. Jeśli klient znajduje się w innej strefie czasowej, akcje te wystąpią, gdy czas klienta osiągnie czas oceny.  

    -   **Czas dostępności oprogramowania**: Wybierz jedną z następujących ustawień, aby określić, kiedy aktualizacje oprogramowania są dostępne dla klientów:  

        -   **Jak najszybciej**: Wybierz to ustawienie, aby aktualizacje oprogramowania uwzględnione we wdrożeniu dostępne na komputerach klienckich tak szybko, jak to możliwe. Po utworzeniu wdrożenia tego ustawienia aktualizacje zasad klienta programu Configuration Manager. Następnie w kolejnym cyklu sondowania zasad klienta klienci zostaną powiadomieni o wdrożeniu i będą mogli uzyskać aktualizacje dostępne do zainstalowania.  

        -   **Określony czas**: Wybierz to ustawienie, aby aktualizacje oprogramowania uwzględnione we wdrożeniu dostępne na komputerach klienckich w określonym dniu i godzinie. Podczas tworzenia wdrożenia to ustawienie jest włączone, aktualizacje zasad klienta programu Configuration Manager. Następnie w kolejnym cyklu sondowania zasad klienta klienci zostaną powiadomieni o wdrożeniu. Aktualizacje oprogramowania we wdrożeniu nie będą jednak dostępne do zainstalowania do skonfigurowanej daty i godziny.  

    -   **Ostateczny termin instalacji**: Wybierz jedną z następujących ustawień, aby określić ostateczny termin instalacji aktualizacji oprogramowania we wdrożeniu:  

        -   **Jak najszybciej**: Wybierz to ustawienie, aby automatycznie zainstalować aktualizacje oprogramowania we wdrożeniu najszybciej, jak to możliwe.  

        -   **Określony czas**: Wybierz to ustawienie, aby automatycznie zainstalować aktualizacje oprogramowania we wdrożeniu w określonym dniu i godzinie. Configuration Manager określa ostateczny termin instalacji aktualizacji oprogramowania przez dodanie skonfigurowanego **określony czas** interwał **czas dostępności oprogramowania**.  

        > [!NOTE]  
        >  Rzeczywisty ostateczny termin instalacji to wyświetlany czas ostatecznego terminu wydłużony o przypadkowy czas wynoszący maksymalnie 2 godziny. Pozwala to ograniczyć potencjalny wpływ jednoczesnego instalowania aktualizacji oprogramowania we wdrożeniu przez wszystkie komputery kliencie w kolekcji docelowej.  
        >   
        >  Można skonfigurować ustawienie klienta **Agent komputera** , **Wyłącz losowe generowanie terminu ostatecznego** , aby wyłączyć losowe opóźnienie instalacji wymaganych aktualizacji oprogramowania. Aby uzyskać więcej informacji, zobacz sekcję [Agent komputera](../../core/clients/deploy/about-client-settings.md#computer-agent).  

6.  Na stronie Czynności użytkownika skonfiguruj następujące ustawienia:  

    -   **Powiadomienia użytkowników**: Określ, czy mają być wyświetlane powiadomienia o aktualizacjach oprogramowania w programie Software Center na komputerze klienckim zgodnie ze skonfigurowanym ustawieniem **czas dostępności oprogramowania** oraz czy wyświetlać powiadomienia użytkowników na komputerach klienckich.  

    -   **Zachowanie ostatecznego terminu wdrożenia**: Określ zachowanie pożądane po osiągnięciu ostatecznego terminu wdrożenia aktualizacji oprogramowania. Określ, czy zainstalować aktualizacje oprogramowania we wdrożeniu oraz czy uruchomić ponownie system po zainstalowaniu aktualizacji oprogramowania niezależnie od skonfigurowanego okna obsługi. Aby uzyskać więcej informacji dotyczących okien obsługi, zobacz [używanie okien obsługi](../../core/clients/manage/collections/use-maintenance-windows.md).  

    -   **Zachowanie ponownego uruchamiania urządzenia**: Określ, czy pominąć ponowne uruchomienie systemu na serwerach i stacjach roboczych po zainstalowaniu aktualizacji oprogramowania i ponowne uruchomienie systemu jest wymagane do ukończenia instalacji.  

        > [!IMPORTANT]  
        >  Pominięcie ponownego uruchomienia systemu może być przydatne w środowisku serwerów lub w przypadku, gdy nie chcesz, aby komputery, na których zainstalowano aktualizacje oprogramowania, zostały domyślnie uruchomione ponownie. Może to jednak spowodować, że komputery znajdą się w stanie niezabezpieczonym, podczas gdy zezwolenie na wymuszone ponowne uruchomienie gwarantuje niezwłoczne ukończenie instalacji aktualizacji oprogramowania.  

    -   **Obsługa filtru zapisu dla urządzeń z systemem Windows Embedded**: Podczas wdrażania aktualizacji oprogramowania na urządzeniach Windows Embedded z włączoną obsługą filtru zapisu, można określić do zainstalowania aktualizacji oprogramowania na tymczasowej nakładce i zatwierdzić zmiany później lub czy zatwierdzić zmiany w ostatecznym terminie instalacji bądź w oknie konserwacji. Po zatwierdzeniu zmian w dniu ostatecznego terminu instalacji lub w oknie obsługi należy ponownie uruchomić komputer, aby trwale zapisać zmiany na urządzeniu.  

        > [!NOTE]  
        >  Po wdrożeniu aktualizacji oprogramowania do urządzenia z systemem Windows Embedded upewnij się, że urządzenie należy do kolekcji ze skonfigurowanym oknem obsługi.  

7.  Na stronie Alerty Skonfiguruj sposób generowania alertów dotyczących tego wdrożenia w programu Configuration Manager i System Center Operations Manager.  

    > [!WARNING]  
    >  Ostatnie alerty dotyczące aktualizacji oprogramowania można wyświetlić w węźle **Aktualizacje oprogramowania** w obszarze roboczym **Biblioteka oprogramowania** .  

8. Na stronie Ustawienia pobierania skonfiguruj następujące ustawienia:  

    - Określ, czy klient pobierze i zainstaluje aktualizacje oprogramowania przy użyciu połączenia z powolną siecią lub rezerwowej lokalizacji zawartości.  

    - Określ, czy klient ma pobrać i zainstalować aktualizacje oprogramowania z rezerwowego punktu dystrybucji, jeśli zawartość aktualizacji oprogramowania będzie niedostępna w preferowanym punkcie dystrybucji.  

    - **Zezwalaj klientom na współużytkowanie zawartości z innymi klientami w tej samej podsieci**: Określ, czy włączyć usługę BranchCache dla pobierania zawartości. Aby uzyskać więcej informacji na temat usługi BranchCache, zobacz [Pojęcia związane z zarządzaniem zawartością](../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md#branchcache).  

    - **Jeśli aktualizacje oprogramowania nie są dostępne w punkcie dystrybucji w bieżącym, sąsiada lub lokacji grup, Pobierz zawartość z usługi Microsoft Updates**: Wybierz to ustawienie, aby klienci, które są połączone z intranetem mają pobierać aktualizacje oprogramowania z witryny Microsoft Update, jeśli aktualizacje oprogramowania nie są dostępne w punktach dystrybucji. Klienci internetowi zawsze można przejść do witryny Microsoft Update zawartości aktualizacji oprogramowania.

    - Określ, czy zezwolić klientom używającym taryfowego połączenia z Internetem na pobieranie aktualizacji oprogramowania po upływie ostatecznego terminu instalacji. Dostawcy Internetu czasami naliczają opłaty według ilości wysyłanych i odbieranych danych podczas taryfowego połączenia z Internetem.  

    > [!NOTE]  
    > Klienci żądają lokalizacji zawartości z punktu zarządzania odnośnie do aktualizacji oprogramowania we wdrożeniu. Zachowanie pobierania jest uzależnione od konfiguracji punktu pobierania, pakietu wdrożeniowego oraz ustawień na tej stronie. Aby uzyskać więcej informacji, zobacz [Scenariusze lokalizacji źródła zawartości](../../core/plan-design/hierarchy/content-source-location-scenarios.md).  

Więcej informacji o procesie wdrażania znajduje się w sekcji [Proces wdrażania aktualizacji oprogramowania](../../sum/understand/software-updates-introduction.md#BKMK_DeploymentProcess).

## <a name="next-steps"></a>Następne kroki
[Monitorowanie aktualizacji oprogramowania](monitor-software-updates.md)

