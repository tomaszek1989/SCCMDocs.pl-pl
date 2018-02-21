---
title: Alerty i systemu stanu
titleSuffix: Configuration Manager
description: "Skonfiguruj alerty oraz Użyj systemu stanu, aby uzyskiwać aktualne informacje o stanie wdrożenia programu Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7341cc6e-9e08-41e4-bcc6-6c1ff12e85ca
caps.latest.revision: 
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 84fe2fd0959051ea42e555cb484c95fb82ec8fb3
ms.sourcegitcommit: 1378532fac2620ddcfd31061982f344a290c2e67
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/20/2018
---
# <a name="use-alerts-and-the-status-system-for-system-center-configuration-manager"></a>Korzystanie z alertów i systemu stanu w programie System Center Configuration Manager

Dotyczy: Program System Center Configuration Manager (Current Branch)*

Skonfiguruj alerty oraz Użyj wbudowanego systemu stanu, aby uzyskiwać aktualne informacje o stanie wdrożenia programu System Center Configuration Manager.  


##  <a name="bkmk_Status"></a> System stanu  
 Wszystkie główne składniki lokacji generują komunikaty o stanie zapewniające informacje o operacjach w lokacji i hierarchii.    Te informacje pozwalają śledzić na bieżąco kondycję różnych procesów w lokacji. System alertów można dostosować w taki sposób, aby ignorował niepotrzebne informacje o znanych problemach przy jednoczesnym zwiększeniu możliwości wczesnego informowania o innych problemach, które mogą wymagać uwagi użytkownika.  

 Domyślnie system stanu programu Configuration Manager działa bez konfiguracji przy użyciu ustawień, które są odpowiednie dla większości środowisk. Można jednak skonfigurować poniższe elementy:  

-   **Składniki podsumowania stanu:** Można edytować składniki podsumowania w każdej lokacji, aby kontrolować częstotliwość komunikatów o stanie, które generują wskaźnika stanu zmianę dla następujących czterech składników podsumowania stanu:  

    -   Składnik podsumowania wdrażania aplikacji  

    -   Składnik podsumowania statystyk aplikacji  

    -   Moduł podsumowania stanu składników  

    -   Składnik podsumowania stanu systemu lokacji  

-   **Reguły filtra stanu:** Można utworzyć nowe reguły filtra stanu, zmodyfikować priorytet reguł, wyłączyć lub włączyć reguły i usunąć nieużywane reguły w poszczególnych lokacjach.  

    > [!NOTE]  
    >  Reguły filtra stanu nie obsługują użycia zmiennych środowiskowych w celu wykonywania poleceń zewnętrznych.  

-   **Raportowanie stanu:** Można skonfigurować serwera i klienta składnika raportowania można zmodyfikować sposób komunikaty o stanie są raportowane do systemu stanu programu Configuration Manager i określ, gdzie są wysyłane komunikaty o stanie.  

    > [!WARNING]  
    >  Ponieważ domyślne ustawienia raportowania są odpowiednie dla większości środowisk, należy zachować ostrożność przy ich zmianie. Zwiększenie poziomu raportowania stanu przez wybranie do raportu wszystkich szczegółów stanu może zwiększyć liczbę komunikatów o stanie się przetwarzane, co zwiększa obciążenie przetwarzania w lokacji programu Configuration Manager. Z kolei obniżenie poziomu raportowania stanu może ograniczyć przydatność składników podsumowania stanu.  

Ponieważ system stanu obsługuje oddzielne konfiguracje dla poszczególnych lokacji, należy edytować każdą lokację oddzielnie.  

###  <a name="bkmk_configstatus"></a> Procedury dotyczące konfigurowania systemu stanu  

##### <a name="to-configure-status-summarizers"></a>Aby skonfigurować składniki podsumowania stanu  

1.  W konsoli programu Configuration Manager przejdź do **administracji** > **konfiguracja lokacji** >**witryny**, a następnie wybierz lokację, dla której chcesz skonfigurować system stanu.  

2.  Na karcie **Narzędzia główne** w grupie **Ustawienia** kliknij przycisk **Składniki podsumowania stanu**.  

3.  W oknie dialogowym **Składniki podsumowania stanu** wybierz składnik podsumowania stanu, który chcesz skonfigurować, a następnie kliknij przycisk **Edytuj** w celu otwarcia właściwości tego składnika. Jeśli edytujesz składnik podsumowania wdrażania aplikacji lub statystyk aplikacji, przejdź do kroku 5. Jeśli edytujesz stan składnika, przejdź do kroku 6. Jeśli edytujesz składnik podsumowania stanu systemu lokacji, przejdź do kroku 7.  

4.  Po otwarciu strony właściwości składnika podsumowania wdrażania aplikacji lub statystyk aplikacji wykonaj poniższe czynności:  

    1.  Na karcie **Ogólne** strony właściwości składnika podsumowania ustaw interwały podsumowania, a następnie kliknij przycisk **OK** , aby zamknąć stronę właściwości.  

    2.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Składniki podsumowania stanu** i ukończyć tę procedurę.  

5.  Po otwarciu strony właściwości składnika podsumowania stanu składnika wykonaj poniższe czynności:  

    1.  Na **ogólne** karty strony właściwości składnika podsumowania Ustaw wartości replikacji i próg okresu.  

    2.  Na karcie **Progi** wybierz **typ komunikatu** , który chcesz skonfigurować, a następnie kliknij nazwę składnika na liście **Progi** .  

    3.  W oknie dialogowym **Właściwości progu stanu** zmodyfikuj wartości progu ostrzeżenia i progu krytycznego, a następnie kliknij przycisk **OK**.  

    4.  Powtórz kroki 6.b i 6.c zgodnie z potrzebami. Po zakończeniu kliknij przycisk **OK** , aby zamknąć właściwości składnika podsumowania.  

    5.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Składniki podsumowania stanu** i ukończyć tę procedurę.  

6.  Po otwarciu strony właściwości składnika podsumowania stanu systemu wykonaj poniższe czynności:  

    1.  Na **ogólne** karty strony właściwości składnika podsumowania Ustaw wartości replikacji i harmonogramu.  

    2.  Na karcie **Progi** określ wartości dla opcji **Domyślne progi** , aby skonfigurować domyślne progi w celu wyświetlania stanu krytycznego i ostrzeżenia.  

    3.  Aby edytować właściwości określonych **obiektów magazynu**, wybierz obiekt z listy **Określone progi** , a następnie kliknij przycisk **Właściwości** w celu uzyskania dostępu do progu ostrzeżenia i progu krytycznego dla obiektów magazynu oraz ich zmodyfikowania. Kliknij przycisk **OK** , aby zamknąć okno dialogowe właściwości obiektów magazynu.  

    4.  Aby utworzyć nowy obiekt magazynu, kliknij przycisk **Utwórz obiekt** i określ wartości obiektu magazynu. Kliknij przycisk **OK** , aby zamknąć właściwości obiektów.  

    5.  Aby usunąć obiekt magazynu, wybierz obiekt i kliknij przycisk **Usuń** .  

    6.  Powtórz kroki od 7.b do 7.e w razie potrzeby. Po zakończeniu kliknij przycisk **OK** , aby zamknąć właściwości składnika podsumowania.  

    7.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Składniki podsumowania stanu** i ukończyć tę procedurę.  

##### <a name="to-create-a-status-filter-rule"></a>Aby utworzyć regułę filtra stanu  

1.  W konsoli programu Configuration Manager przejdź do **administracji** > **konfiguracja lokacji** >**witryny**, a następnie wybierz lokację, w której chcesz skonfigurować system stanu.  

2.  Na karcie **Narzędzia główne** w grupie **Ustawienia** kliknij przycisk **Reguły filtra stanu**. Zostanie otwarte okno dialogowe **Reguły filtra stanu** .  

3.  Kliknij przycisk **Utwórz**.  

4.  Na stronie **Ogólne**w **Kreatorze tworzenia reguły filtru stanu** określa nazwę nowej reguły filtra stanu i kryteria dopasowywania komunikatów dla tej reguły, a następnie kliknij przycisk **Dalej**.  

5.  Na stronie **Akcje** określ akcje do wykonania, kiedy reguła stanu dopasuje komunikat o stanie, a następnie kliknij przycisk **Dalej**.  

6.  Zapoznaj się ze szczegółami nowej reguły na stronie **Podsumowanie** kreatora, a następnie ukończ jego pracę.  

    > [!NOTE]  
    >  Program Configuration Manager wymaga tylko, że nowa reguła filtru stanu ma nazwę. Jeśli utworzono regułę, ale nie określono żadnych kryteriów przetwarzania komunikatów o stanie, reguła filtra stanu nie będzie miała zastosowania. Umożliwia to utworzenie i uporządkowanie reguł przed skonfigurowaniem kryteriów filtrowania stanu dla każdej reguły.  

##### <a name="to-modify-or-delete-a-status-filter-rule"></a>Aby zmodyfikować lub usunąć regułę filtra stanu  

1.  W konsoli programu Configuration Manager przejdź do **administracji** > **konfiguracja lokacji** >**witryny**, a następnie wybierz lokację, w której chcesz skonfigurować system stanu.  

2.  Na karcie **Narzędzia główne** w grupie **Ustawienia** kliknij przycisk **Reguły filtra stanu**.  

3.  W oknie dialogowym **Reguły filtra stanu** wybierz regułę, którą chcesz zmodyfikować, a następnie wykonaj jedną z poniższych czynności.  

    -   Kliknij przycisk **Zwiększ priorytet** lub **Zmień priorytet** , aby zmienić kolejność przetwarzania reguły filtra stanu. Następnie wybierz inną akcję lub przejdź do kroku 8 tej procedury, aby zakończyć to zadanie.  

    -   Kliknij przycisk **Wyłącz** lub **Włącz** , aby zmienić stan reguły. Po dokonaniu zmiany stanu reguły wybierz inną akcję lub przejdź do kroku 8 tej procedury, aby zakończyć to zadanie.  

    -   Kliknij przycisk **Usuń** , aby usunąć regułę filtra stanu z tej lokacji, a następnie kliknij przycisk **Tak** w celu potwierdzenia. Po usunięciu reguły wybierz inną akcję lub przejdź do kroku 8 tej procedury, aby zakończyć to zadanie.  

    -   Kliknij przycisk **Edytuj** , jeśli chcesz zmienić kryteria reguły komunikatów o stanie, a następnie przejdź do kroku 5 tej procedury.  

4.  Na karcie **Ogólne** okna dialogowego właściwości reguły filtra stanu zmodyfikuj kryteria dopasowywania reguły i komunikatów.  

5.  Na stronie **Akcje** zmień akcje do wykonania, kiedy reguła stanu dopasuje komunikat o stanie.  

6.  Kliknij przycisk **OK** , aby zapisać zmiany.  

7.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Reguły filtra stanu** .  

##### <a name="to-configure-status-reporting"></a>Aby skonfigurować raportowanie stanu  

1.  W konsoli programu Configuration Manager przejdź do **administracji** > **konfiguracja lokacji** > **witryny**, a następnie wybierz lokację, w której chcesz skonfigurować system stanu.  

2.  Na karcie **Narzędzia główne** w grupie **Ustawienia** , kliknij przycisk **Konfiguruj składniki lokacji**, a następnie wybierz opcję **Raportowanie stanu**.  

3.  W oknie dialogowym **Właściwości składnika raportowania stanu** określ komunikaty o stanie składnika serwera i klienta, które chcesz raportować lub rejestrować:  

    1.  Skonfiguruj **raport** do wysyłania komunikatów o stanie do systemu komunikatów o stanie programu Configuration Manager.  

    2.  Ustaw opcję **Dziennik** , aby zapisywać typ i ważność komunikatów o stanie w dzienniku zdarzeń systemu Windows.  

4.  Kliknij przycisk **OK**.  

###  <a name="BKMK_MonitorSystemStatus"></a> Monitorowanie systemu stanu programu Configuration Manager  
 **Stan systemu** w programie Configuration Manager udostępnia przegląd ogólnych operacji lokacji i lokacji operacji serwera w hierarchii. Może ujawnić problemów operacyjnych dla serwerów systemu lokacji lub składniki i stanu systemu można używać określonego szczegółowych informacji o różnych operacji programu Configuration Manager. Można monitorować stan systemu z **stan systemu** węzła **monitorowanie** obszaru roboczego w konsoli programu Configuration Manager.  

 Większość ról systemu lokacji programu Configuration Manager i składniki generują komunikaty o stanie. Szczegółowe informacje dotyczące komunikatów o stanie są rejestrowane w dzienniku działania każdego składnika, ale także przesyłane do bazy danych lokacji, gdzie są podsumowywane i przedstawiane jako ogólne informacje zbiorcze o kondycji każdego składnika lub systemu lokacji. Te podsumowania komunikatów o stanie zawierają szczegółowe informacje o regularnych operacjach, ostrzeżeniach i błędach. Można skonfigurować progi wyświetlania ostrzeżeń lub błędów i dostosować ustawienia systemu tak, aby ignorować w informacjach zbiorczych znane problemy, które nie są istotne podczas analizy ważnych problemów dotyczących serwerów lub operacji komponentów.  

 Stan systemu jest replikowany do innych lokacji w hierarchii jako dane lokacji, a nie dane globalne. Oznacza to, że może zobaczyć tylko stan lokacji, z którym nawiązuje połączenie z konsolą programu Configuration Manager i wszystkich lokacji podrzędnych tej lokacji. W związku z tym warto rozważyć połączenie konsoli programu Configuration Manager do lokacji najwyższego poziomu w hierarchii, podczas wyświetlania stanu systemu.  

 W poniższej tabeli wymieniono różne widoki stanu systemu wraz z informacjami o sposobie ich użycia.  

|Węzeł|Więcej informacji|  
|----------|----------------------|  
|Stan lokacji|Ten węzeł umożliwia wyświetlenie zbiorczego stanu każdego systemu lokacji w celu określenia kondycji każdego serwera systemu lokacji. Kondycja systemu lokacji jest określana na podstawie progów skonfigurowanych dla każdej lokacji w **Składniku podsumowania stanu systemu lokacji**.<br /><br /> Korzystając z funkcji **Menedżer usług programu Configuration Manager**, można wyświetlić komunikaty o stanie dla każdego systemu lokacji, ustawić progi komunikatów o stanie i zarządzać działaniem składników w systemach lokacji.|  
|Stan składnika|Ten węzeł umożliwia wyświetlenie zbiorczych informacji o stanie każdego składnika programu Configuration Manager w celu poznania kondycji operacyjnej składnika. Kondycja składnika jest określana na podstawie progów skonfigurowanych dla każdej lokacji w **Składniku podsumowania stanu składnika**.<br /><br /> Korzystając z funkcji **Menedżer usług programu Configuration Manager**, można wyświetlić komunikaty o stanie dla każdego składnika, ustawić progi komunikatów o stanie i zarządzać działaniem składników.|  
|Rekordy powodujące konflikty|Ten węzeł umożliwia wyświetlenie komunikatów o stanie dotyczących klientów, na których mogą występować rekordy powodujące konflikt.<br /><br /> Configuration Manager używa Identyfikatora sprzętu próbuje identyfikować klientów, którzy mogą stanowić duplikaty, alertów rekordy powodujące konflikt. Na przykład mając ponownej instalacji komputera jego identyfikator sprzętu będzie taki sam, ale identyfikator GUID, który korzysta z programu Configuration Manager może ulec zmianie.|  
|Kwerendy komunikatów o stanie|Ten węzeł umożliwia tworzenie kwerend komunikatów o stanie dla określonych zdarzeń i powiązanych szczegółów. Kwerendy dotyczące komunikatów o stanie umożliwiają znalezienie komunikatów o stanie dotyczących określonych zdarzeń.<br /><br /> Często służą kwerendy komunikatów o stanie do identyfikacji czasu modyfikacji określonego składnika, operacji lub obiektu programu Configuration Manager, a konto, którego użyto do modyfikacji. Przykładowo można uruchomić wbudowaną kwerendę **Utworzone, zmodyfikowane lub usunięte kolekcje** , aby określić kiedy dana kolekcja została utworzona oraz użytego w tym celu konta użytkownika.|  

####  <a name="bkmk_managestatus"></a> Zarządzanie stanem lokacji i stanem składnika  
 Poniższe informacje umożliwiają zarządzanie stanem lokacji i stanem składnika:  

-   Informacje o konfigurowaniu progów dla stanu systemu znajdują się w temacie [Procedury dotyczące konfigurowania systemu stanu](#bkmk_configstatus).  

-   Aby zarządzać poszczególnymi składnikami w programie Configuration Manager, należy użyć **Menedżera usług programu Configuration Manager**.  

####  <a name="bkmk_view"></a> Wyświetlanie komunikatów o stanie  
 Komunikaty o stanie można wyświetlić dla poszczególnych serwerów i składników systemu lokacji.  

 Aby wyświetlić komunikaty o stanie w konsoli programu Configuration Manager, należy wybrać określony serwer systemu lokacji lub składnik, a następnie kliknij **Pokaż komunikaty**. Gdy wyświetlane są komunikaty, można wybrać wyświetlanie określonych typów komunikatów lub komunikatów z danego okresu i filtrować wyniki na podstawie szczegółów dotyczących komunikatów o stanie.  

##  <a name="bkmk_Alerts"></a> Alerty  
 Alerty programu Configuration Manager są generowane przez niektóre operacje, po wystąpieniu określonego warunku.  

-   Zwykle alerty są generowane po wystąpieniu błędu wymagającego usunięcia.  

-   Alerty mogą być generowane, aby ostrzec użytkownika o określonym stanie i umożliwić mu dalsze monitorowanie sytuacji.  

-   Niektóre alerty wymagają konfiguracji, na przykład alerty programu Endpoint Protection i stanu klienta, a inne alerty są konfigurowane automatycznie.  

-   Można skonfigurować subskrypcje alertów, które umożliwiają następnie wysyłanie szczegółowych informacji pocztą e-mail, przyczyniając się do zwiększenia świadomości kluczowych problemów.  

 Aby uzyskać informacje o sposobie konfigurowania alertów i subskrypcji alertów w programie Configuration Manager, skorzystaj z poniższej tabeli:  


|Akcja|Więcej informacji|  
|------------|----------------------|  
|Konfigurowanie alertów programu Endpoint Protection dla kolekcji|Zobacz **jak skonfigurować alerty programu Endpoint Protection w programie Configuration Manager** w [Konfigurowanie programu Endpoint Protection w programie System Center Configuration Manager](../../../protect/deploy-use/configure-endpoint-protection.md)|  
|Konfigurowanie alertów stanu klienta dla kolekcji|Zobacz [jak skonfigurować stan klienta w programie System Center Configuration Manager](../../../core/clients/deploy/configure-client-status.md).|  
|Zarządzanie alertami programu Configuration Manager|Zapoznaj się z sekcją [Management tasks for alerts](#BKMK_Manage) w tym temacie.|  
|Konfigurowanie subskrypcji e-mail alertów|Zobacz sekcję [Management tasks for alerts](#BKMK_Manage) w tym temacie.|  
|Monitorowanie alertów|Zapoznaj się z sekcją [Monitorowanie alertów](#BKMK_MonitorAlerts)|  

###  <a name="BKMK_Manage"></a> Management tasks for alerts  

##### <a name="to-manage-general-alerts"></a>Aby zarządzać alertami ogólnymi  

1.  W konsoli programu Configuration Manager przejdź do **monitorowanie** > **alerty**, a następnie wybierz zadanie zarządzania.  

  Więcej informacji o zadaniach zarządzania, które mogą przed wybraniem wymagać dodatkowego opisu, znajduje się w poniższej tabeli.  

|Zadanie zarządzania|Szczegóły|  
    |---------------------|-------------|  
    |**Ustaw opcję**|Otwiera  *&lt;nazwa alertu*\>**właściwości** okno dialogowe, w którym można zmodyfikować nazwę, ważność i progi dla wybranego alertu. Zmień ważność alertu, ta konfiguracja wpływa na sposób wyświetlania alertów w konsoli programu Configuration Manager.|  
    |**Edytuj komentarz**|Wprowadź komentarz dotyczący wybranych alertów. Te komentarze są wyświetlane wraz z alertem w konsoli programu Configuration Manager.|  
    |**Odłóż**|Wstrzymuje monitorowanie alertu, aż do osiągnięcia określonej daty. W tym czasie zostanie zaktualizowany stan alertu.<br /><br /> Alert można odroczyć tylko wtedy, gdy jest włączony.|  
    |**Utwórz subskrypcję**|Otwiera okno dialogowe **Nowa subskrypcja** , w którym można utworzyć subskrypcję e-mail wybranego alertu.|  

<!--##### To configure Endpoint Protection alerts for a collection  

1.  pending  -->

##### <a name="to-configure-client-status-alerts-for-a-collection"></a>Aby skonfigurować alerty stanu klienta dla kolekcji  

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność** >   **kolekcje urządzeń**.  

2.  Na liście **Kolekcje urządzeń** wybierz kolekcję, dla której chcesz skonfigurować alerty, a następnie na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**.  

    > [!NOTE]  
    >  Nie można skonfigurować alertów dla kolekcji użytkowników.  

3.  Na **alerty** karcie  *&lt;Nazwa kolekcji*\>**właściwości** okno dialogowe, kliknij przycisk **Dodaj**.  

    > [!NOTE]  
    >  Karta **Alerty** jest widoczna tylko w przypadku, gdy rola zabezpieczeń, z którą została skojarzony użytkownik, ma uprawnienia do alertów.  

4.  W oknie dialogowym **Dodaj nowe alerty kolekcji** wybierz alerty, które mają być generowane, gdy progi stanu klienta spadną poniżej określonej wartości, a następnie kliknij przycisk **OK**.  

5.  Z listy **Warunki** na karcie **Alerty** wybierz poszczególne alerty stanu klienta, a następnie określ poniższe informacje.  

    -   **Nazwa alertu** — zaakceptuj nazwę domyślną lub wprowadź nową nazwę alertu.  

    -   **Ważność alertu** — z listy rozwijanej wybierz poziom alertu, który będzie wyświetlany w konsoli programu Configuration Manager.  

    -   **Zgłoś alert** — Określ procentowy próg alertu.  

6.  Kliknij przycisk **OK** zamknąć  *&lt;Nazwa kolekcji*\>**właściwości** okno dialogowe.  

##### <a name="to-configure-email-notification-for-alerts"></a>Aby skonfigurować powiadomienia e-mail o alertach  

1.  W konsoli programu Configuration Manager przejdź do **monitorowanie** > **alerty** > **subskrypcje**.  

2.  Na karcie **Narzędzia główne** , w grupie **Utwórz** , kliknij przycisk **Konfiguruj powiadomienie e-mail**.  

3.  W oknie dialogowym **Właściwości składnika powiadomień e-mail** wprowadź następujące informacje:  

    -   **Włączanie powiadomień e-mail dla alertów**: Zaznacz to pole wyboru, aby program Configuration Manager do korzystania z serwera SMTP do wysyłania alertów e-mail.  

    -   **Nazwa FQDN lub adres IP serwera SMTP do wysyłania alertów e-mail**: Wprowadź w pełni kwalifikowaną nazwę (FQDN) lub adres IP i SMTP port dla serwera poczty e-mail, który ma być używany dla tych alertów.  

    -   **Konto połączenia serwera SMTP**: Określ metodę uwierzytelniania dla programu Configuration Manager można używać do łączenia z serwerem poczty e-mail.  

    -   **Adres nadawcy alertów e-mail**: Określ adres e-mail, z którego są wysyłane wiadomości e-mail alertów.  

    -   **Testuj serwer SMTP**: Wysyła testową wiadomość e-mail na adres e-mail określony w **adres nadawcy alertów e-mail**.  

4.  Kliknij przycisk **OK** , aby zapisać ustawienia i zamknąć okno dialogowe **Właściwości składnika ustawień poczty e-mail** .  

##### <a name="to-subscribe-to-email-alerts"></a>Aby subskrybować alerty e-mail  

1.  W konsoli programu Configuration Manager przejdź do **monitorowanie** > **alerty**.  

2.  Wybierz alert, a następnie na karcie **Narzędzia główne** w grupie **Subskrypcja** kliknij pozycję **Utwórz subskrypcję**.  

3.  W oknie dialogowym **Nowa subskrypcja** wprowadź następujące informacje:  

    -   **Nazwa**: Wprowadź nazwę identyfikującą subskrypcję e-mail. Można użyć do 255 znaków.  

    -   **Adres e-mail**: Wprowadź adresy e-mail, które mają wysyłany alert. Poszczególne adresy e-mail można rozdzielić średnikami.  

    -   **Język wiadomości e-mail**: Na liście wybierz język wiadomości e-mail.  

4.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Nowa subskrypcja** i utworzyć subskrypcję e-mail.  

    > [!NOTE]  
    >  Można usuwać i edytować subskrypcje w obszarze roboczym **Monitorowanie** , rozwijając węzeł **Alerty** i klikając węzeł **Subskrypcje** .  

###  <a name="BKMK_MonitorAlerts"></a> Monitorowanie alertów  
 Alerty można wyświetlić w węźle **Alerty** obszaru roboczego **Monitorowanie** . Alerty mają jeden z następujących stanów:  

-   **Nigdy nie wyzwolone**: Warunek uruchomienia alertu nie został spełniony.  

-   **Aktywne**: Warunek alertu został spełniony.  

-   **Anulowane**: Warunek aktywnego alertu nie jest już spełniany. Ten stan oznacza, że warunek, który spowodował alert został usunięty.  

-   **Odroczone**: Użytkownik administracyjny skonfigurował programu Configuration Manager do oceny stanu alertu w późniejszym czasie.  

-   **Wyłączone**: Ten alert został wyłączony przez użytkownika administracyjnego. Gdy alert znajdzie się w tym stanie, programu Configuration Manager nie aktualizuje alertu nawet, jeśli stan alertu zmieni się.  

 Gdy program Configuration Manager generuje alert można wykonać jedną z następujących czynności:  

-   Usunąć stan, który spowodował alert, na przykład rozwiązać problem dotyczący sieci lub konfiguracji, który wygenerował alert. Po programu Configuration Manager wykryje, że problem już nie istnieje, stan alertu zmieni się **anulować**.  

-   Jeżeli alert to znany problem można odroczyć go na określony czas. W tym czasie program Configuration Manager zaktualizuje alert do bieżącego stanu.  

     Alert można odroczyć tylko wtedy, gdy jest aktywny.  

-   Zawartość pola **Komentarz** alertu można edytować, aby użytkownicy administracyjni widzieli, że masz świadomość alertu. W komentarzu można na przykład podać informacje o sposobie usunięcia stanu, informacje o bieżącym statusie stanu lub wyjaśnić, dlaczego odroczono alert.  
