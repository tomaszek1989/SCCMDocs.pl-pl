---
title: "Migracji zawartości"
titleSuffix: Configuration Manager
description: "Punkty dystrybucji umożliwia zarządzanie zawartością podczas migracji danych do hierarchii docelowej programu System Center Configuration Manager."
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 66f7759c-6272-4116-aad7-0d05db1d46cd
caps.latest.revision: "8"
caps.handback.revision: "0"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 7332ff4bf0ad10bd18e42485fb548eee70deaf04
ms.sourcegitcommit: ca9d15dfb1c9eb47ee27ea9b5b39c9f8cdcc0748
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2018
---
# <a name="plan-a-content-deployment-migration-strategy-in-system-center-configuration-manager"></a>Planowanie strategii migracji wdrożenia zawartości w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Podczas migrowania aktywnie danych do hierarchii docelowej programu System Center Configuration Manager, klienci programu Configuration Manager w źródłowym i docelowym hierarchiach mogą zachować dostęp do zawartości wdrożonej w hierarchii źródłowej. Umożliwia także migracji do uaktualnienia lub ponownego przypisania punktów dystrybucji z hierarchii źródłowej, aby ustawić je jako punkty dystrybucji w hierarchii docelowej. Po udostępnieniu i uaktualnieniu lub ponownym przypisaniu punktów dystrybucji ta strategia może wyeliminować konieczność ponownego wdrażania zawartości na nowych serwerach w hierarchii docelowej w przypadku migrowanych klientów.  

Mimo że można ponownie utworzyć i dystrybuować zawartość w hierarchii docelowej, można także użyć następujących opcji do zarządzania tą zawartością:  

-   Udostępnić punkty dystrybucji w hierarchii źródłowej klientom w hierarchii docelowej.  

-   Uaktualnić punkty dystrybucji programu Configuration Manager 2007 autonomicznej lub dodatkowej lokacji programu Configuration Manager 2007 w hierarchii źródłowej, aby ustawić je jako punkty dystrybucji w hierarchii docelowej.  

-   Ponownie przypisać punkty dystrybucji z hierarchii źródłowej programu System Center Configuration Manager do lokacji w hierarchii docelowej.  

Informacje w poniższych sekcjach ułatwią planowanie wdrażania zawartości podczas migracji:  

-   [Udostępnianie punktów dystrybucji między hierarchiami źródłowymi a docelowymi](#About_Shared_DPs_in_Migration)  

-   [Planowanie uaktualnienia programu Configuration Manager 2007 współużytkowanych punktów dystrybucji](#Planning_to_Upgrade_DPs)  

    -   [Proces uaktualniania punktu dystrybucji](#BKIMK_UpgradeProcess)  

    -   [Planowanie uaktualnienia lokacji dodatkowych programu Configuration Manager 2007](#BKMK_UpgradeSS)  

-   [Planowanie ponownego przypisania punktów dystrybucji programu System Center Configuration Manager](#BKMK_ReassignDistPoint)  

    -   [Proces ponownego przypisywania punktu dystrybucji](#BKMK_ReassignProcess)  

-   [Kwestia prawa własności do zawartości podczas migracji](#About_Migrating_Content)  

##  <a name="About_Shared_DPs_in_Migration"></a> Udostępnianie punktów dystrybucji między hierarchiami źródłowymi a docelowymi  
Podczas migracji można udostępnić punkty dystrybucji z hierarchii źródłowej w hierarchii docelowej. Współużytkowanych punktów dystrybucji można użyć w celu natychmiastowego udostępnienia zawartości migrowanej z hierarchii źródłowej klientom w hierarchii docelowej bez konieczności ponownego tworzenia tej zawartości, a następnie jej dystrybucji w nowych punktach dystrybucji w hierarchii docelowej. Gdy klienci w hierarchii docelowej zażądają zawartości wdrożonej w udostępnionych punktach dystrybucji, współużytkowane punkty dystrybucji można zaoferować klientom jako prawidłowe lokalizacje zawartości.  

 Oprócz podczas migracji z hierarchii źródłowej pozostaje aktywna prawidłową lokalizację zawartości dla klientów w hierarchii docelowej, jest możliwość uaktualnienia lub ponownego przypisania punktu dystrybucji do hierarchii docelowej. Można uaktualnić programu Configuration Manager 2007 współużytkowane punkty dystrybucji i ponowne przypisywanie punktów dystrybucji udostępnionych System Center 2012 Configuration Manager. Po uaktualnieniu lub ponownym przypisaniu udostępnionego punktu dystrybucji jest on usuwany z hierarchii źródłowej i staje się punktem dystrybucji w hierarchii docelowej. Po uaktualnieniu lub ponownym przypisaniu współużytkowanego punktu dystrybucji można nadal korzystać z punktu dystrybucji w hierarchii docelowej po zakończeniu migracji z hierarchii źródłowej. Aby uzyskać więcej informacji o sposobie uaktualniania współużytkowanego punktu dystrybucji, zobacz [Plan uaktualniania programu Configuration Manager 2007 współużytkowanych punktów dystrybucji](#Planning_to_Upgrade_DPs). Aby uzyskać więcej informacji na temat sposobu ponownego przypisania współużytkowanego punktu dystrybucji, zobacz [Planowanie ponownego przypisania System Center Configuration Manager punktów dystrybucji](#BKMK_ReassignDistPoint).  

 Punkty dystrybucji można udostępnić z dowolnej lokacji źródłowej w hierarchii źródłowej. Po udostępnieniu punktów dystrybucji dla lokacji źródłowej, podrzędnych lokacji dodatkowych są udostępniane w każdym kwalifikującego punkcie dystrybucji w tej lokacji głównej i w każdej lokacji głównych. Aby zakwalifikować się współużytkowanego punktu dystrybucji, należy skonfigurować serwer systemu lokacji, który hostuje punkt dystrybucji z w pełni kwalifikowaną nazwą domeny (FQDN). Żadnych punktów dystrybucji, które są skonfigurowane przy użyciu nazwy NetBIOS, są ignorowane.  

> [!TIP]  
>  Programu Configuration Manager 2007 nie wymaga konfigurowania nazwy FQDN dla serwerów systemu lokacji.  

Poniższe informacje ułatwią planowanie dotyczące współużytkowanych punktów dystrybucji:  

-   Udostępniane punkty dystrybucji muszą spełniać wymagania wstępne współużytkowanych punktów dystrybucji. Aby uzyskać więcej informacji o tych wymaganiach wstępnych, zobacz [konfiguracje wymagane do migracji](../../core/migration/prerequisites-for-migration.md#BKMK_Required_Configurations) w [wymagania wstępne dotyczące migracji w programie System Center Configuration Manager](../../core/migration/prerequisites-for-migration.md).  

-   Akcja udostępniania punktu dystrybucji to ustawienie dotyczące całej lokacji, które wszystkie kwalifikujące punkty dystrybucji w lokacji źródłowej i wszystkich bezpośrednich podrzędnych lokacjach dodatkowych. Po włączeniu udostępniania punktu dystrybucji nie można wybrać poszczególnych punktów dystrybucji w celu ich udostępnienia.  

-   Klienci w hierarchii docelowej mogą odbierać informacje o lokalizacji zawartości dla pakietów dystrybuowanych do punktów dystrybucji udostępnianych z hierarchii źródłowej. W przypadku punktów dystrybucji z hierarchii źródłowej programu Configuration Manager 2007 w tym punkty dystrybucji gałęzi, punkty dystrybucji w udziałach serwerów i standardowe punkty dystrybucji.  

    > [!WARNING]  
    >  Jeżeli hierarchia źródłowa zostanie zmieniona, współużytkowane punkty dystrybucji z oryginalnej hierarchii źródłowej nie będą już dostępne i nie będzie można ich zaoferować jako lokalizacji zawartości klientom w hierarchii docelowej. Jeżeli migracja zostanie skonfigurowana ponownie tak, aby korzystała z oryginalnej hierarchii źródłowej, poprzednio udostępnione punkty dystrybucji zostaną przywrócone jako prawidłowe serwery lokalizacji zawartości.  

-   W przypadku migracji pakietu hostowanego na współużytkowanym punkcie dystrybucji wersja pakietu musi być taka sama w hierarchii źródłowej i docelowej. Jeżeli wersja pakietu nie jest taka sama w hierarchii źródłowej i docelowej, klienci w hierarchii docelowej nie mogą pobrać tej zawartości ze współużytkowanego punktu dystrybucji. Dlatego w przypadku aktualizowania pakietu w hierarchii źródłowej należy przeprowadzić ponową migrację danych pakietu zanim klienci w hierarchii docelowej będą mogli pobrać tę zawartość ze współużytkowanego punktu dystrybucji.  

    > [!NOTE]  
    >  Podczas wyświetlania szczegółów pakietu hostowanego na udostępnionych dystrybucji punktu, liczba pakietów wyświetlanych w **hostowane pakiety migracji** w lokacji źródłowej **współużytkowane punkty dystrybucji** nie jest aktualizowana, aż do następnego cyklu zbierania danych.  

-   Współużytkowane punkty dystrybucji i ich właściwości można wyświetlić **hierarchii źródłowej** węzła **administracji** obszaru roboczego w konsoli programu Configuration Manager, który łączy do hierarchii docelowej.  

-   Nie można użyć współużytkowanego punktu dystrybucji z hierarchii źródłowej programu Configuration Manager 2007 do hostowania pakietów dla programu Microsoft Application Virtualization (App-V). W celu użycia przez klientów w hierarchii docelowej pakiety App-V muszą zostać migrowane i przekonwertowane. Jednak można użyć współużytkowanego punktu dystrybucji z hierarchii źródłowej programu System Center 2012 Configuration Manager lub System Center Configuration Manager do hostowania pakietów App-V dla klientów w hierarchii docelowej.  

-   Po udostępnieniu chronionego punktu dystrybucji z hierarchii źródłowej programu Configuration Manager 2007, hierarchia docelowa tworzy grupę granic zawierającą chronione lokalizacje sieciowe tego punktu dystrybucji. Nie można zmienić tej grupy granic w hierarchii docelowej. Jednak w przypadku zmiany informacji o chronionych granicach dla punktu dystrybucji w hierarchii źródłowej programu Configuration Manager 2007, zmiana ta jest uwzględniana w hierarchii docelowej po zakończeniu następnego cyklu zbierania danych.  

    > [!NOTE]  
    >  Lokacje programu System Center 2012 Configuration Manager i System Center Configuration Manager korzystają z preferowanych punktów dystrybucji zamiast chronionych punktów dystrybucji. Ten warunek dotyczy tylko punktów dystrybucji, które są udostępniane z lokacji źródłowych programu Configuration Manager 2007.  

Przed udostępnieniem punktów dystrybucji z lokacji źródłowej kwalifikujące się punkty dystrybucji nie są widoczne w konsoli programu Configuration Manager. Po udostępnieniu punktów dystrybucji wyświetlane są tylko te punkty dystrybucji, które zostały pomyślnie udostępnione.  

Po udostępnieniu punktów dystrybucji można zmienić konfigurację dowolnego punktu dystrybucji w hierarchii źródłowej. Zmiany wprowadzone w konfiguracji punktu dystrybucji są uwzględniane w hierarchii docelowej po następnym cyklu zbierania danych. Punkty dystrybucji zaktualizowane w celu kwalifikacji do udostępnienia są udostępniane automatycznie, a te, które już się nie kwalifikują, zatrzymują udostępnianie punktów dystrybucji. Na przykład może być punkt dystrybucji, który nie jest skonfigurowany przy użyciu intranetowej nazwy FQDN i nie został początkowo udostępniony w hierarchii docelowej. Po skonfigurowaniu nazwy FQDN dla tego punktu dystrybucji następny cykl zbierania danych identyfikuje tę konfigurację, a punkt dystrybucji jest następnie udostępniany w hierarchii docelowej.  

##  <a name="Planning_to_Upgrade_DPs"></a>Planowanie uaktualnienia programu Configuration Manager 2007 współużytkowanych punktów dystrybucji  
W przypadku migracji z hierarchii źródłowej programu Configuration Manager 2007, można uaktualnić współużytkowany punkt dystrybucji aby stał się punkt dystrybucji programu System Center Configuration Manager. Możesz uaktualnić punkty dystrybucji w lokacjach głównych i lokacjach dodatkowych. Proces uaktualniania powoduje usunięcie punktu dystrybucji z hierarchii programu Configuration Manager 2007 i ustawienie go jako serwera systemu lokacji w hierarchii docelowej. Ten proces powoduje także skopiowanie istniejącej zawartości w punkcie dystrybucji do nowej lokalizacji na komputerze punktu dystrybucji. Następnie proces uaktualniania modyfikuje kopię zawartości, aby utworzyć magazyn SIS do użytku z wdrożeniem zawartości w hierarchii docelowej. Dlatego po uaktualnieniu punktu dystrybucji, nie trzeba ponownej dystrybucji migrowanej zawartości hostowanej w punkcie dystrybucji programu Configuration Manager 2007.  

Po programu Configuration Manager konwertuje zawartości w magazyn pojedynczego wystąpienia, programu Configuration Manager usuwa oryginalną zawartość źródłową na komputerze punktu dystrybucji, aby zwolnić miejsce na dysku. Menedżer konfiguracji nie używa oryginalnej lokalizacji zawartości źródłowej.  

Nie wszystkie punkty dystrybucji programu Configuration Manager 2007, które można udostępniać kwalifikujące się do uaktualnienia do programu System Center Configuration Manager. Aby kwalifikować się do uaktualnienia, punkt dystrybucji programu Configuration Manager 2007 musi spełniać warunki uaktualnienia. Te warunki obejmować serwer systemu lokacji na którym zainstalowano punkt dystrybucji i punktu dystrybucji programu Configuration Manager 2007 typ, który jest zainstalowany. Nie można na przykład uaktualnić żadnego typu punktu dystrybucji zainstalowanego na komputerze serwera lokacji w lokacji głównej, ale można uaktualnić standardowy punkt dystrybucji zainstalowany na komputerze serwera lokacji w lokacji dodatkowej.  

> [!NOTE]  
>  Można uaktualnić tylko te programu Configuration Manager 2007 współużytkowanych punktów dystrybucji znajdujących się na komputerze, na którym jest uruchomiona wersja systemu operacyjnego jest obsługiwana w przypadku punktów dystrybucji w hierarchii docelowej. Na przykład można udostępnić punkt dystrybucji programu Configuration Manager 2007, który znajduje się na komputerze z systemem Windows Vista, nie można uaktualnić tego współużytkowanego punktu dystrybucji, ponieważ system operacyjny nie jest obsługiwany przez program System Center Configuration Manager do użycia jako punkt dystrybucji.  

W poniższej tabeli wymieniono obsługiwane lokalizacje dla każdego typu punktu dystrybucji programu Configuration Manager 2007, który można uaktualnić.  

|Typ punktu dystrybucji|Punkt dystrybucji na komputerze systemu lokacji innym niż serwer lokacji|Punkt dystrybucji na komputerze systemu lokacji innym niż serwer lokacji i hostujący inne role systemu lokacji|Punkt dystrybucji na dodatkowym serwerze lokacji|  
|--------------------------------|-----------------------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|---------------------------------------------------|  
|Standardowy punkt dystrybucji|Tak|Nie|Tak|  
|Punkt dystrybucji w udziałach serwera<sup>1</sup>|Tak|Nie|Nie|  
|Punkt dystrybucji gałęzi|Tak|Nie|Nie|  

 <sup>1</sup> system Center Configuration Manager nie obsługuje udziałów serwera dla systemów lokacji, ale obsługuje uaktualnienie punktu dystrybucji programu Configuration Manager 2007, który znajduje się w udziale serwera. Po uaktualnieniu punktu dystrybucji programu Configuration Manager 2007, który znajduje się w udziale serwera typ punktu dystrybucji jest automatycznie konwertowany do serwera i należy wybrać dysk na komputerze punktu dystrybucji, z którym będzie przechowywany magazyn SIS zawartości.  

> [!WARNING]  
>  Przed uaktualnieniem punktu dystrybucji gałęzi należy odinstalować oprogramowanie klienckie programu Configuration Manager 2007. Po uaktualnieniu punktu dystrybucji gałęzi, który ma zainstalowane oprogramowanie klienckie programu Configuration Manager 2007, zawartość wcześniej wdrożona na komputerze jest usuwana z komputera, a uaktualnienie punktu dystrybucji kończy się niepowodzeniem.  

Aby zidentyfikować punkty dystrybucji, które kwalifikują się do uaktualnienia, w konsoli programu Configuration Manager w **hierarchii źródłowej** węzła, wybierz lokację źródłową, a następnie wybierz **współużytkowane punkty dystrybucji** kartę. Punktów dystrybucji **tak** w **kwalifikuje się do uaktualnienia** kolumny.  

Po uaktualnieniu punktu dystrybucji, który jest zainstalowany na serwerze lokacji dodatkowej programu Configuration Manager 2007, lokacja dodatkowa zostanie odinstalowana z hierarchii źródłowej. Ten scenariusz jest nazywany uaktualnieniem lokacji dodatkowej, jednak dotyczy tylko roli systemu lokacji punktu dystrybucji. W jego wyniku lokacja dodatkowa nie zostanie uaktualniona, lecz odinstalowana. Spowoduje to pozostawienie punktu dystrybucji z hierarchii docelowej na komputerze, który był serwera lokacji dodatkowej. Jeśli planujesz uaktualnić punkt dystrybucji w lokacji dodatkowej, zobacz [zaplanować uaktualnienie lokacji dodatkowych programu Configuration Manager 2007](#BKMK_UpgradeSS) w tym temacie.  

###  <a name="BKIMK_UpgradeProcess"></a> Proces uaktualniania punktu dystrybucji  
Aby uaktualnić punkty dystrybucji programu Configuration Manager 2007, które zostały udostępnione hierarchii docelowej, można użyć konsoli programu Configuration Manager. Podczas uaktualniania współużytkowanego punktu dystrybucji, punktu dystrybucji zostanie odinstalowana z lokacji programu Configuration Manager 2007. Następnie jest instalowana jako punkt dystrybucji, która jest połączona z lokacją główną lub dodatkową określoną w hierarchii docelowej. Podczas procesu uaktualniania zostanie utworzona kopia zawartości poddanej migracji i przechowywanej w punkcie dystrybucji, a następnie owa kopia zostanie skonwertowana na magazyn zawartości pojedynczego wystąpienia. Kiedy program Configuration Manager skonwertuje pakietu na magazyn zawartości pojedynczego wystąpienia, usuwa tego pakietu z udziału SMSPKG na komputerze punktu dystrybucji, chyba że pakiet ma co najmniej jeden anonsów, które są ustawione na **Uruchom program z punktu dystrybucji**.  

Aby uaktualnić punkt dystrybucji, program Configuration Manager używa **konta dostępu do lokacji źródłowej** skonfigurowane do zbierania danych od dostawcy programu SMS lokacji źródłowej. Mimo że to konto wymaga jedynie **odczytu** uprawnień do obiektów lokacji w celu zebrania danych z lokacji źródłowej, musi mieć jednak również **usunąć** i **Modyfikuj** uprawnienia do **lokacji** pomyślne usunięcie punktu dystrybucji z lokacji programu Configuration Manager 2007 podczas uaktualniania.  

> [!NOTE]  
>  Configuration Manager można konwertowanie zawartości w magazyn pojedynczego wystąpienia w tylko jednym punkcie dystrybucji w czasie. Po skonfigurowaniu kilku uaktualnień punktu dystrybucji, punkty dystrybucji są umieszczane w kolejce do uaktualnienia i przetwarzane pojedynczo.  

Przed uaktualnieniem współużytkowanego punktu dystrybucji należy się upewnić, że przeprowadzono migrację całej zawartości wdrożonej w punkcie dystrybucji. Zawartość niepoddana migracji przed uaktualnieniem punktu dystrybucji nie będzie dostępna w hierarchii docelowej po uaktualnieniu. Podczas uaktualniania punktu dystrybucji zawartość pakietów poddanych migracji zostanie skonwertowana do formatu zgodnego z magazynem jednego wystąpienia (SIS) w hierarchii docelowej.  

Aby uaktualnić punkt dystrybucji z poziomu konsoli programu Configuration Manager, serwer systemu lokacji programu Configuration Manager 2007 muszą spełniać następujące warunki:  

-   Konfiguracja i lokalizacja punktu dystrybucji muszą kwalifikować się do uaktualnienia.  

-   Na komputerze punktu dystrybucji musi mieć wystarczające miejsce na dysku dla zawartości, który ma zostać przekonwertowany z formatu magazynu zawartości programu Configuration Manager 2007 do formatu magazynu jednego wystąpienia. Ta konwersja wymaga wolnego miejsca na dysku równego rozmiarowi największego pakietu przechowywanego w punkcie dystrybucji.  

-   Na komputerze punktu dystrybucji musi być zainstalowany system operacyjny w wersji obsługiwanej jako punkt dystrybucji w hierarchii docelowej.  

    > [!NOTE]  
    >  Gdy program Configuration Manager sprawdza kwalifikuje się do uaktualnienia punktu dystrybucji, nie sprawdza wersję systemu operacyjnego na komputerze punktu dystrybucji.  

Aby uaktualnić punkt dystrybucji w **administracji** obszaru roboczego, rozwiń węzeł **migracji**, rozwiń węzeł **hierarchii źródłowej** węzeł, a następnie wybierz lokację zawierającą dystrybucji wskaż, czy chcesz uaktualnić. Następnie w okienku szczegółów na karcie **Współużytkowane punkty dystrybucji** wybierz punkt dystrybucji do uaktualnienia.  

Można potwierdzić, że punkt dystrybucji jest gotowy do uaktualnienia, sprawdzając jego stan w kolumnie **Kwalifikuje się do ponownego przypisania** .  Następnie konsoli programu Configuration Manager na wstążce na **punktów dystrybucji** karcie **punktu dystrybucji** grupy wybierz **ponownie przypisać**. Spowoduje to otwarcie kreatora, którego używasz do zakończenia uaktualniania punktu dystrybucji.  

Przeprowadzając uaktualnienie współużytkowanego punktu dystrybucji, należy przypisać go do wybranej lokacji głównej lub dodatkowej w hierarchii docelowej. Po uaktualnieniu punktu dystrybucji zarządzania punktem dystrybucji jako dystrybucji punktów w hierarchii docelowej, takich jak dowolnego innego punktu dystrybucji.  

Można monitorować postępy uaktualniania punktu dystrybucji w konsoli programu Configuration Manager, wybierając **migracja punktu dystrybucji** węźle **migracji** węzła **administracji** obszaru roboczego. Można również wyświetlić informacje w dzienniku **Migmctrl.log** na serwerze centralnej lokacji administracyjnej hierarchii docelowej lub w dzienniku **distmgr.log** na serwerze lokacji w hierarchii docelowej służącej do zarządzania uaktualnionym punktem dystrybucji.  

> [!NOTE]  
>  Po uaktualnieniu punktu dystrybucji do hierarchii docelowej Rola systemu lokacji punktu dystrybucji jest usuwane z lokacji źródłowej programu Configuration Manager 2007. Pakiety, które zostały wysłane do punktu dystrybucji nie są aktualizowane w hierarchii programu Configuration Manager 2007. W konsoli programu Configuration Manager 2007 pakietach przesłanych do punktu dystrybucji nadal komputera systemu lokacji jako dystrybucji punktów z **typu** z **nieznany**. Kolejne uaktualnienia pakietu w programie Configuration Manager 2007 powoduje zgłoszenie błędów w dzienniku distmgr.log dotyczącym tej lokacji, jeśli lokacja dokona próby uaktualnienia pakietu w systemie nieznanej lokacji przez Menedżera dystrybucji.  

Jeśli zdecydujesz się z uaktualnienia współużytkowanego punktu dystrybucji, można nadal zainstalować punkt dystrybucji z hierarchii docelowej na wcześniejsze punktu dystrybucji programu Configuration Manager 2007. Przed zainstalowaniem nowego punktu dystrybucji, musisz najpierw odinstalować wszystkie role systemu lokacji programu Configuration Manager 2007 z komputera punktu dystrybucji. Dotyczy to również lokacji programu Configuration Manager 2007, jeśli pełni rolę komputera serwera lokacji. Podczas dezinstalacji punktu dystrybucji programu Configuration Manager 2007, zawartość, która została wdrożona w punkcie dystrybucji nie jest usuwany z komputera.  

###  <a name="BKMK_UpgradeSS"></a>Planowanie uaktualnienia lokacji dodatkowych programu Configuration Manager 2007  
 Podczas migracji do uaktualnienia współużytkowanego punktu dystrybucji hostowanego na serwerze lokacji dodatkowej programu Configuration Manager 2007, programu Configuration Manager uaktualnia roli systemu lokacji punktu dystrybucji do punktu dystrybucji w hierarchii docelowej. Także dezinstalację lokacji dodatkowej z hierarchii źródłowej. Wynik jest punkt dystrybucji programu System Center Configuration Manager, lecz nie lokacja dodatkowa.  

 Dla punktu dystrybucji na komputerze serwera lokacji kwalifikował się do uaktualnienia programu Configuration Manager musi być w stanie odinstalować lokację dodatkową i każdej z ról systemu lokacji na tym komputerze. Zazwyczaj współużytkowanego punktu dystrybucji w udziale serwera programu Configuration Manager 2007 nie kwalifikuje się do uaktualnienia. Jeśli jednak udział serwera znajduje się na serwerze lokacji dodatkowej, punkty dystrybucji owej lokacji oraz wszelkie inne współużytkowane punkty dystrybucji na komputerze nie będą kwalifikowały się do uaktualnienia. Jest to spowodowane udziału serwera jest traktowany jako dodatkowy obiekt systemu lokacji, podczas procesu podejmuje próbę dezinstalacji lokacji dodatkowej, a ten proces nie można odinstalować tego obiektu. W tym scenariuszu można włączyć standardowy punkt dystrybucji na serwerze lokacji dodatkowej, a następnie przeprowadzić ponowną dystrybucję zawartości do tego standardowego punktu dystrybucji. Ten proces nie używa przepustowości sieci, a po zakończeniu można odinstalować punkt dystrybucji w udziale serwera, usunąć udział serwera, a następnie Uaktualnij punktu dystrybucji i lokacji dodatkowej.  

 Przed uaktualnieniem współużytkowanego punktu dystrybucji, sprawdź konfigurację punktu dystrybucji w programie Configuration Manager 2007, aby uniknąć uaktualnienia punktu dystrybucji w lokacji dodatkowej, który chcesz nadal korzystać z programu Configuration Manager 2007. To jest dobrym rozwiązaniem, ponieważ po uaktualnieniu współużytkowanego punktu dystrybucji znajdującego się na serwerze lokacji dodatkowej serwer systemu lokacji zostanie usunięty z hierarchii programu Configuration Manager 2007 i nie jest już dostępne w tej hierarchii. Usunięcie lokacji dodatkowej spowoduje oddzielenie wszelkich punktów dystrybucji pozostałych w tej lokacji. Oznacza to, zarządzać przy użyciu programu Configuration Manager 2007 i nie są już współużytkowane ani kwalifikuje się do uaktualnienia.  

> [!WARNING]  
>  Podczas wyświetlania współużytkowanych punktów dystrybucji w konsoli programu Configuration Manager, nie są widoczne żadne oznaki, który jest współużytkowany punkt dystrybucji na zdalnym serwerze systemu lokacji lub na serwerze lokacji dodatkowej.  

 Jeśli w zdalnej lokalizacji sieciowej, który jest używany głównie do kontrolowania wdrażania zawartości w owej lokalizacji lokacji dodatkowej, należy rozważyć uaktualnienie lokacji dodatkowych współużytkowanego punktu dystrybucji. Ponieważ można skonfigurować kontrolę przepustowości podczas dystrybucji zawartości do punktu dystrybucji programu System Center Configuration Manager, można często uaktualnić lokację dodatkową do punktu dystrybucji, skonfiguruj punkt dystrybucji do kontroli przepustowości i uniknąć instalowania lokacji dodatkowej w tej lokalizacji sieciowej w hierarchii docelowej.  

 Proces uaktualniania współużytkowanego punktu dystrybucji na serwerze lokacji dodatkowej jest taki sam jak inne uaktualniania punktu dystrybucji udostępnionych. Zawartość jest kopiowana i konwertowana do magazynu jednego wystąpienia używany przez hierarchię docelową. Jednak po uaktualnieniu współużytkowanego punktu dystrybucji znajdującego się na serwerze lokacji dodatkowej proces uaktualniania spowoduje również odinstalowanie punktu zarządzania (jeśli istnieje), a następnie odinstalowanie lokacji dodatkowej z serwera. Wynik jest, że lokacja dodatkowa zostanie usunięta z hierarchii programu Configuration Manager 2007. Aby odinstalować lokację dodatkową, programu Configuration Manager przy użyciu konta, który jest skonfigurowany do zbierania danych z lokacji źródłowej.  

 Podczas uaktualniania nastąpi opóźnienie między po odinstalowaniu lokacji dodatkowej programu Configuration Manager 2007 i kiedy rozpoczyna się instalacja punktu dystrybucji w hierarchii docelowej. Cykl zbierania danych określa tego opóźnienia na maksymalnie cztery godziny. Opóźnienie mają na celu dostarczenie czasu dla lokacji dodatkowej odinstalować przed rozpoczęciem instalacji nowego punktu dystrybucji.  

 Aby uzyskać więcej informacji o sposobie uaktualniania współużytkowanego punktu dystrybucji, zobacz [Plan uaktualniania programu Configuration Manager 2007 współużytkowanych punktów dystrybucji](#Planning_to_Upgrade_DPs).  

##  <a name="BKMK_ReassignDistPoint"></a>Planowanie ponownego przypisania punktów dystrybucji programu System Center Configuration Manager  
 Podczas migracji z obsługiwanej wersji programu System Center 2012 Configuration Manager do hierarchii tej samej wersji, można ponownie przypisać współużytkowany punkt dystrybucji z hierarchii źródłowej do lokacji w hierarchii docelowej. Przypomina koncepcji uaktualniania punktu dystrybucji programu Configuration Manager 2007 do roli punktu dystrybucji w hierarchii docelowej. Można ponownie przypisać punkty dystrybucji z lokacji głównej i dodatkowej. Działanie ponownego przypisania punktu dystrybucji powoduje usunięcie punktu dystrybucji z hierarchii źródłowej i sprawia, że komputer i jego serwera systemu lokacji punktu dystrybucji lokacji wybranej w hierarchii docelowej.  

 Przypisując ponownie punkt dystrybucji, nie trzeba przeprowadzać ponownej dystrybucji zawartości poddanej migracji obsługiwanej przez punkt dystrybucji lokacji źródłowej. Ponadto w przeciwieństwie do uaktualniania punktu dystrybucji programu Configuration Manager 2007, ponowne przypisanie punktu dystrybucji nie wymaga dodatkowego miejsca na dysku na komputerze punktu dystrybucji. Jest to spowodowane od programu System Center 2012 Configuration Manager, punkty dystrybucji używają formatu magazynu jednego wystąpienia dla zawartości. Zawartość na komputerze punktu dystrybucji nie muszą zostać przekonwertowane, gdy punkt dystrybucji jest ponownie przypisywane między hierarchiami.  

 Dla punktu dystrybucji programu System Center 2012 Configuration Manager na kwalifikować się do ponownego przypisania musi spełniać następujące kryteria:  

-   Współużytkowany punkt dystrybucji musi być zainstalowany na komputerze innym niż serwer lokacji.  

-   Współużytkowany punkt dystrybucji nie może być przydzielony wspólnie z innymi rolami systemu lokacji.  

Aby zidentyfikować punkty dystrybucji, które kwalifikują się do ponownego przypisania, w konsoli programu Configuration Manager w **hierarchii źródłowej** węzła, wybierz lokację źródłową, a następnie wybierz **współużytkowane punkty dystrybucji** kartę. Punktów dystrybucji **tak** w **kwalifikuje się do ponownego przypisania** kolumny (Ta kolumna nosiła nazwę **kwalifikuje się do uaktualnienia** przed System Center 2012 R2 Program Configuration Manager).  

###  <a name="BKMK_ReassignProcess"></a> Proces ponownego przypisywania punktu dystrybucji  
 Do ponownego przypisania punktów dystrybucji, współużytkowanych z aktywnej hierarchii źródłowej, można użyć konsoli programu Configuration Manager. Podczas ponownego przypisania współużytkowanego punktu dystrybucji, punktu dystrybucji jest odinstalowany z lokacji źródłowej, a następnie zainstalowany jako punkt dystrybucji, która jest połączona z lokacją główną lub dodatkową określoną w hierarchii docelowej.  

 Do ponownego przypisania punktu dystrybucji, hierarchia docelowa używa konta dostępu do lokacji źródłowej skonfigurowanego na zbieranie danych od dostawcy programu SMS lokacji źródłowej. Aby uzyskać informacje o wymaganych uprawnieniach i dodatkowych wymaganiach wstępnych, zobacz [wymagania wstępne dotyczące migracji w programie System Center Configuration Manager](../../core/migration/prerequisites-for-migration.md).  

## <a name="migrate-multiple-shared-distribution-points-at-the-same-time"></a>Migrowanie wielu współużytkowanych punktów dystrybucji w tym samym czasie
Począwszy od wersji 1610, można użyć **punktu dystrybucji do ponownego przypisania** mają proces programu Configuration Manager równolegle ponownego przypisania do 50 współużytkowanych punktów dystrybucji, w tym samym czasie. Współużytkowane punkty dystrybucji z lokacji źródłowych obsługiwanych, które są uruchamiane w tym:  
- Configuration Manager 2007
- System Center 2012 Configuration Manager
- System Center 2012 R2 Configuration Manager
- Program System Center Configuration Manager (Current Branch)

Podczas ponownego przypisania punktów dystrybucji, każdy punkt dystrybucji muszą kwalifikować się można uaktualnić lub ponownie przypisany. Nazwa akcji i procesu związanego (uaktualnienia lub ponownego przypisania) zależy od tego, która wersja programu Configuration Manager w lokacji źródłowej działa. Wyników zakończenia dla obu akcje są takie same: punkt dystrybucji jest przypisany do jednej z jego zawartością w miejscu witryn bieżącej gałęzi.

Przed wersją 1610 programu Configuration Manager można przetworzyć tylko jeden punkt dystrybucji w czasie. Teraz można ponownie przypisać dowolną liczbę punktów dystrybucji z następującymi zastrzeżeniami:  
- Mimo że nie można przypisywać ponownie, gdy zostały umieszczone w kolejce więcej niż jednego punktów dystrybucji wyboru wielokrotnego, programu Configuration Manager będzie przetwarzać je równolegle, zamiast czekać na zakończenie jednego przed rozpoczęciem następnej.  
- Domyślnie maksymalnie 50 dystrybucji punktów są przetwarzane równolegle w czasie. Po zakończeniu operacji ponownego przypisania pierwszego punktu dystrybucji programu Configuration Manager rozpocznie przetwarzanie 51 i tak dalej.  
- Gdy używasz zestawu SDK programu Configuration Manager, można zmienić **SharedDPImportThreadLimit** Aby dostosować liczbę punktów dystrybucji przypisywać ich programu Configuration Manager może przetwarzać równolegle.


##  <a name="About_Migrating_Content"></a>Przypisz własność zawartości podczas migracji zawartości  
 Przeprowadzając migrację zawartości w celu jej wdrożenia, należy przypisać obiekt zawartości do lokacji w hierarchii docelowej. Ta lokacja stanie się następnie właścicielem treści w hierarchii docelowej. Mimo że lokacji najwyższego poziomu w hierarchii docelowej lokację, która wykonuje migrację metadane dla zawartości, jest przypisanej lokacji, która używa oryginalnych plików źródłowych zawartości w sieci.  

 Aby zminimalizować obciążenie przepustowości sieci podczas migrowania zawartości, warto zastanowić się nad przeniesieniem własności zawartości do lokacji w hierarchii docelowej znajdującej się blisko sieciowej lokalizacji zawartości w hierarchii źródłowej. Ponieważ informacje o zawartości w hierarchii docelowej są udostępniane globalnie, będą dostępne we wszystkich lokacjach.  

 Chociaż informacje o zawartości są udostępniane wszystkim lokacjom przy użyciu replikacji bazy danych, zawartość przypisana do lokacji głównej, a następnie wdrożyć do dystrybucji punktów w innych lokacjach głównych transferu za pomocą replikacji opartej na plikach. Transfer jest kierowany przez centralną lokację administracyjną do dodatkowej lokacji głównej. Centralizując pakiety przeznaczone do dystrybucji do wielu lokacji głównych przed lub w trakcie migracji po przypisaniu lokacji jako właściciela zawartości, można zredukować transfery danych w sieciach o niskiej przepustowości.
