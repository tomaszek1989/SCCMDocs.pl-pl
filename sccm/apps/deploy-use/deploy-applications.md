---
title: Wdrażanie aplikacji
titleSuffix: Configuration Manager
description: Tworzenie i symulowanie wdrożenia aplikacji w kolekcji urządzeń lub użytkowników
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2629c376-ec43-4f0e-a78b-4223cc9302bf
caps.latest.revision: ''
caps.handback.revision: ''
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 0101ba0eade5775577f52920f301a782afd7bbda
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="deploy-applications-with-system-center-configuration-manager"></a>Wdrażanie aplikacji w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Tworzenie i symulowanie wdrożenia aplikacji do kolekcji urządzeń lub użytkowników w programie Configuration Manager. To wdrożenie zapewnia instrukcje do klienta programu Configuration Manager, jak i kiedy zainstalować oprogramowanie. 

Przed wdrożeniem aplikacji należy utworzyć co najmniej jeden typ wdrożenia dla aplikacji. Aby uzyskać więcej informacji, zobacz [tworzenie aplikacji](/sccm/apps/deploy-use/create-applications).

 Można także symulować wdrożenie aplikacji. Ta symulacja testować możliwość wdrożenia bez instalowania lub odinstalowywania aplikacji. Wdrożenie symulowane ocenia metodę wykrywania, wymagania i zależności dla typu wdrożenia i raportuje wyniki w **wdrożeń** węzła **monitorowanie** obszaru roboczego. Aby uzyskać więcej informacji, zobacz [symulowanie wdrożenia aplikacji](/sccm/apps/deploy-use/simulate-application-deployments).

> [!IMPORTANT]
>  Można symulować wdrożenie wymaganych aplikacji, ale nie pakiety ani aktualizacje oprogramowania.   
>  Zarządzanie urządzeniami Przenośnymi, zarejestrowane urządzenia nie obsługują wdrożeń symulowanych środowisko użytkownika i ustawień planowania.



## <a name="deploy-an-application"></a>Wdrażanie aplikacji

1.  W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** > **Zarządzanie aplikacjami** > **aplikacji**.

2.  Z listy **Aplikacje** wybierz aplikację, którą chcesz wdrożyć. Następnie na karcie **Narzędzia główne** w grupie **Wdrażanie** kliknij pozycję **Wdróż**.

### <a name="specify-general-information-about-the-deployment"></a>Określ informacje ogólne dotyczące wdrożenia

Na **ogólne** strony Kreatora wdrażania oprogramowania Podaj następujące informacje:

- **Oprogramowanie**: Ta wartość jest wyświetlana aplikacja do wdrożenia. Kliknij przycisk **Przeglądaj** aby wybrać inną aplikację.
- **Kolekcja**: Kliknij przycisk **Przeglądaj** aby wybrać kolekcję, aby wdrożyć aplikację.
- **Użyj domyślnych grup punktów dystrybucji powiązanych z tą kolekcją**: Umieścić zawartość aplikacji w domyślnej grupie punktów dystrybucji kolekcji. Jeśli wybrana Kolekcja nie został skojarzony z grupą punktów dystrybucji, ta opcja jest szary.
- **Dystrybuuj automatycznie zawartość dla zależności**: Jeśli jakieś typy wdrożenia w aplikacji zawierają zależności, lokacji również wysyła zawartość zależnej aplikacji do punktów dystrybucji.

    >[!IMPORTANT]
    > Po zaktualizowaniu aplikacji po wdrożeniu aplikacji głównej witryny nie automatycznej dystrybucji Nowa zawartość dla zależności.

- **Komentarze (opcjonalne)**: Opcjonalnie wprowadź opis dla tego wdrożenia.

### <a name="specify-content-options-for-the-deployment"></a>Określenie opcji zawartości wdrożenia

Na **zawartości** kliknij przycisk **Dodaj** można dodać zawartość skojarzona z tym wdrożeniem do punktów dystrybucji lub grupy punktów dystrybucji. W przypadku wybrania **Użyj domyślnych punktów dystrybucji powiązanych z tą kolekcją** na **ogólne** strony, a następnie ta opcja jest automatycznie wypełniane. Tylko członek roli zabezpieczeń Administrator aplikacji można zmodyfikować.

### <a name="specify-deployment-settings"></a>Określ ustawienia wdrożenia

Na **ustawienia wdrażania** strony Kreatora wdrażania oprogramowania Podaj następujące informacje:

- **Akcja**: Z listy rozwijanej wybierz, czy to wdrożenie ma **zainstalować** lub **Odinstaluj** aplikacji.

    > [!NOTE]
    >  Jeśli aplikacja zostanie dwukrotnie wdrożona na urządzeniu, jeden raz z akcją **zainstalować** i drugi raz z akcją **Odinstaluj**, wdrożenie aplikacji z akcją **zainstalować** ma wyższy priorytet.

  Akcja wdrożenia nie można zmienić po jego utworzeniu.

- **Cel**: Z listy rozwijanej wybierz jedną z następujących opcji:  
    - **Dostępne**: Jeśli aplikacja jest wdrażana dla użytkownika, użytkownik widzi opublikowaną aplikację w programie Software Center i może zainstalować ją na żądanie.
    - **Wymagane**: Aplikacja zostanie wdrożona automatycznie zgodnie z harmonogramem. Jeśli stan wdrożenia aplikacji nie jest ukryty, wszystkich osób korzystających z aplikacji można śledzić stan wdrożenia i instalować aplikacji z Centrum oprogramowania przed upływem ostatecznego terminu.

    > [!NOTE]   
    >  Kiedy akcja wdrożenia jest ustawiona na **Odinstaluj**, cel wdrożenia jest automatycznie ustawiana **wymagane**. Nie można zmienić to zachowanie.  

- **Wdróż automatycznie zgodnie z harmonogramem, czy użytkownik jest zalogowany**: Jeśli wdrożenie dla użytkownika, wybierz tę opcję, aby wdrożyć aplikację na podstawowych urządzeniach użytkownika. To ustawienie nie wymaga, aby użytkownik był zalogowany przed uruchomieniem wdrożenia. Nie wybieraj tej opcji, jeśli użytkownik może interakcyjnie przeprowadzić instalację. Ta opcja jest dostępna tylko w przypadku, gdy wdrożenie ma cel **Wymagane**.

- **Wyślij pakiety wznawiania**: Jeśli dla celu wdrożenia wybrano **wymagane**, przed klient uruchamia wdrożenie do komputerów zostanie wysłany pakiet wznawiania. Ten pakiet wznawia pracę komputerów w ostatecznym terminie instalacji. Przed użyciem tej opcji, komputerów i sieci musi być skonfigurowany dla funkcji Wake On LAN.
- **Zezwalaj klientom mierzonego połączenia internetowego na pobieranie zawartości po upływie ostatecznego terminu instalacji, co może pociągnąć za sobą dodatkowe koszty**: Ta opcja jest dostępna tylko dla wdrożeń z celem **wymagane**.
- **Automatycznie Zamknij wszystkie uruchomione pliki wykonywalne określone na karcie zachowanie instalacji okna dialogowego właściwości typu wdrożenia**: Aby uzyskać więcej informacji, zobacz [Sprawdź, czy uruchamianie plików wykonywalnych przed zainstalowaniem aplikacji](#how-to-check-for-running-executable-files-before-installing-an-application).

- **Wymagaj zgody administratora, jeśli użytkownicy zażądają tej aplikacji**: Dla wersji 1710 i poprzednie administrator zatwierdza wszystkie żądania użytkowników dla aplikacji, zanim użytkownik może go zainstalować. Ta opcja jest niedostępne, gdy cel wdrożenia jest **wymagane**, lub gdy aplikacja jest wdrażana w kolekcji urządzeń.  

    > [!NOTE]
    >  Żądania zatwierdzenia aplikacji są wyświetlane w węźle **Żądania zatwierdzenia** w sekcji **Zarządzanie aplikacjami** w obszarze roboczym **Biblioteka oprogramowania** . Jeśli żądanie nie zostało zatwierdzone w ciągu 45 dni, zostanie ono usunięte. Zainstalowanie klienta może spowodować anulowanie wszystkich żądań oczekuje na zatwierdzenie.  
    >  Po zostały zatwierdzone do instalacji aplikacji, możesz **Odmów** żądania w konsoli programu Configuration Manager. Ta akcja nie powoduje klienta do odinstalowania aplikacji z dowolnego urządzenia, ale zatrzymać użytkownikom instalowanie nowych kopii aplikacji z Centrum oprogramowania.

- **Administrator musi zatwierdzić żądanie dla tej aplikacji na urządzeniu**: Począwszy od wersji 1802 administrator zatwierdza wszystkie żądania użytkowników dla aplikacji, zanim użytkownik może go zainstalować na urządzeniu żądanej. Administrator zatwierdza żądanie, użytkownik jest tylko możliwość instalowania aplikacji na tym urządzeniu. Użytkownik musi przesłać innego żądania, aby zainstalować aplikację na innym urządzeniu. Ta opcja jest niedostępne, gdy cel wdrożenia jest **wymagane**, lub gdy aplikacja jest wdrażana w kolekcji urządzeń. <!--1357015-->  

    Jest to opcjonalna funkcja. Aby uzyskać więcej informacji, zobacz [Włącz funkcje opcjonalne aktualizacji](/sccm/core/servers/manage/install-in-console-updates#bkmk_options). Jeśli ta funkcja nie jest włączona, zobaczysz już pewne doświadczenie.  

    > [!Important]  
    > Klient programu Configuration Manager musi być w wersji 1802 również. Musisz również korzystać z nowego centrum oprogramowania.  

    > [!Note]  
    > Widok **żądań zatwierdzenia** w obszarze **Zarządzanie aplikacjami** w **Biblioteka oprogramowania** obszaru roboczego w konsoli programu Configuration Manager. Obecnie **urządzenia** kolumny na liście dla każdego żądania. Po wykonaniu akcji na żądanie żądań aplikacji w oknie dialogowym także nazwa urządzenia, z którego użytkownik przesłane żądanie.  
    >  Jeśli żądanie nie zostało zatwierdzone w ciągu 45 dni, zostanie ono usunięte. Zainstalowanie klienta może spowodować anulowanie wszystkich żądań oczekuje na zatwierdzenie.  
    >  Po zostały zatwierdzone do instalacji aplikacji, możesz **Odmów** żądania w konsoli programu Configuration Manager. Ta akcja nie powoduje klienta do odinstalowania aplikacji z dowolnego urządzenia, ale zatrzymać użytkownikom instalowanie nowych kopii aplikacji z Centrum oprogramowania.

- **Automatycznie Uaktualnij wszystkie zastąpione wersje tej aplikacji**: Klient uaktualnia wszystkie zastąpione wersje aplikacji przy użyciu aplikacji zastępującej.    

    > [!NOTE]  
    > Począwszy od wersji 1802, w obu **dostępne** lub **wymagane** zainstalować cel, można włączyć lub wyłączyć tę opcję. <!--1351266--> 


### <a name="specify-scheduling-settings-for-the-deployment"></a>Określ ustawienia planowania wdrożenia

Na **Planowanie** strony wdrażania oprogramowania, ustawiając czas, kiedy ta aplikacja jest wdrożony lub jest niedostępny na urządzeniach klienckich.
Opcje na tej stronie są różne w zależności od tego, czy ustawiono akcję wdrożenia **dostępne** lub **wymagane**.

W niektórych przypadkach można umożliwić użytkownikom więcej czasu do instalacji wymagane wdrożenia aplikacji lub aktualizacji oprogramowania poza wszystkie terminy skonfigurowane. To zachowanie jest zwykle wymagane, gdy komputer został wyłączony przez długi czas i musi zainstalować wiele aplikacji. Na przykład jeśli użytkownik został zwrócony z urlopu, może być mają oczekiwać przez długi czas i wdrożeń aplikacji zaległe są zainstalowane. Aby rozwiązać ten problem, można zdefiniować okres prolongaty wymuszania przez wdrożenie ustawienia klienta programu Configuration Manager do kolekcji.

Aby skonfigurować okres prolongaty, należy wykonać następujące czynności:

- Na **Agent komputera** strony ustawień klienta, należy skonfigurować nową właściwość **okres prolongaty wymuszania po wdrożeniu terminu wdrożenia (godziny)** z wartością pomiędzy **1** i **120** godzin.
- Na **Planowanie** strony wdrażania wymaganej aplikacji, należy wybrać opcję **Opóźnij wymuszenie dotyczące tego wdrożenia zgodnie z preferencjami użytkownika do okresu prolongaty zdefiniowanego w ustawieniach klienta**. Okres prolongaty wymuszania ma zastosowanie do wszystkich wdrożeń przy użyciu tej opcji, włączona i przeznaczone dla urządzeń, na których wdrożono również ustawienie klienta.

Po osiągnięciu ostatecznego terminu instalacji aplikacji klient instaluje aplikację w pierwszym oknie-business użytkownik skonfigurowany do tego okresu prolongaty. Jednak użytkownik może nadal otworzyć programu Software Center i zainstalować aplikację w dowolnym momencie, które mają. Po wygaśnięciu okresu prolongaty wymuszania wraca do normalnej zachowaniem wdrożeń zaległe.

Jeśli aplikacji, który jest wdrażany zastępuje inną aplikację, możesz ustawić ostateczny termin instalacji, gdy użytkownicy otrzymają nową aplikację. Ustaw **ostateczny termin instalacji** celu aktualizacji użytkowników z zastąpioną aplikacją.

### <a name="specify-user-experience-settings-for-the-deployment"></a>Określ ustawienia czynności użytkownika dla wdrożenia

Na **środowisko użytkownika** strony Kreatora wdrażania oprogramowania Podaj informacje dotyczące sposobu interakcji użytkowników z instalacją aplikacji.

Podczas wdrażania aplikacji na urządzeniach Windows Embedded z obsługą filtru zapisu, można określić, aby zainstalować aplikację na tymczasowej nakładce oraz zatwierdzić zmiany później. Można również określić, aby zatwierdzić zmiany w ostatecznym terminie instalacji bądź w oknie obsługi. Zatwierdź zmiany, w terminie ostatecznym instalacji lub w oknie obsługi, należy ponownie uruchomić urządzenie. Trwale zapisać zmiany na urządzeniu.

>[!NOTE]
    >  Podczas wdrażania aplikacji na urządzeniu z systemem Windows Embedded upewnij się, że jest elementem członkowskim kolekcji z okna obsługi. Aby uzyskać więcej informacji na temat obsługi systemu windows i urządzeń z systemem Windows Embedded, zobacz [aplikacji Utwórz systemu Windows Embedded](../../apps/get-started/creating-windows-embedded-applications.md).
    > Opcje **Instalacja oprogramowania** i **Ponowne uruchomienie systemu (jeśli wymagane w celu zakończenia instalacji)** nie są używane, jeśli dla celu wdrożenia wybrano opcję **Dostępne**. Można także skonfigurować poziom powiadomienia wyświetlanego użytkownikom po zainstalowaniu aplikacji.

### <a name="specify-alert-options-for-the-deployment"></a>Określ opcje alertów dla wdrożenia

Na **alerty** Kreatora wdrażania oprogramowania Skonfiguruj sposób generowania alertów dotyczących tego wdrożenia programu Configuration Manager i System Center Operations Manager. Można skonfigurować progi dla alertów raportowania lub wyłączyć raportowanie na czas wdrażania.

### <a name="associate-the-deployment-with-an-ios-app-configuration-policy"></a>Skojarz wdrożenia przy użyciu zasad konfiguracji aplikacji systemu iOS

Na **zasady konfiguracji aplikacji** kliknij przycisk **nowy** Aby skojarzyć to wdrożenie przy użyciu zasad konfiguracji aplikacji systemu iOS (jeśli został utworzony). Aby uzyskać więcej informacji na temat tego typu zasad, zobacz [Konfigurowanie aplikacji systemu iOS przy użyciu zasad konfiguracji aplikacji](../../apps/deploy-use/configure-ios-apps-with-app-configuration-policies.md).

### <a name="deployment-properties"></a>Właściwości wdrożenia

Znajdź nowego wdrożenia w **wdrożeń** węzła **monitorowanie** obszaru roboczego. Można dokonać edycji właściwości tego wdrożenia lub usunąć wdrożenie z karty **Wdrożenia** okienka szczegółów aplikacji.



## <a name="delete-an-application-deployment"></a>Usunięcie wdrożenia aplikacji

1.  W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** > **Zarządzanie aplikacjami** > **aplikacji**.
3.  W **aplikacji** listy, wybierz aplikację, która zawiera wdrożenia należy usunąć.
4.  Na karcie **Wdrożenia** listy *<nazwa aplikacji\>* wybierz wdrożenie aplikacji do usunięcia. Następnie na **wdrożenia** karcie **wdrożenia** kliknij przycisk **usunąć**.

Po usunięciu wdrożenia aplikacji nie zostaną usunięte wszystkie wystąpienia aplikacji, które zostały już zainstalowane. Aby usunąć te aplikacje, należy wdrożyć na komputerach aplikację z **Odinstaluj**. Jeżeli usunięcie wdrożenia aplikacji lub usunięcie zasobu z kolekcji, który jest wdrażany do aplikacji nie jest już widoczna w Centrum oprogramowania.



## <a name="user-notifications-for-required-deployments"></a>Powiadomienia użytkowników w celu dokonania wymaganych wdrożeń
Gdy pojawi się wymagane oprogramowanie z **Odłóż i Przypomnij** ustawienie, można wybrać z listy rozwijanej następujące wartości:
- **Później**: Określa, czy powiadomienia zostały zaplanowane na podstawie ustawień powiadomień skonfigurowanego w ustawieniach klienta.
- **Stały czas**: Określa, czy powiadomienie jest zaplanowane do wyświetlenia ponownie po wybrana wartość czasu. Na przykład w przypadku wybrania 30 minut, powiadomienie będzie wyświetlane ponownie w ciągu 30 minut.

![Agent komputera w domyślnej grupie ustawień klienta](media/ComputerAgentSettings.png)

Czas włączenia trybu czuwania maksymalną zawsze opiera się na wartości powiadomień skonfigurowanego w ustawieniach klienta w czasie, co na osi czasu wdrażania. Na przykład:
- Możesz skonfigurować **wdrożenia termin ostateczny dłuższego niż 24 godziny, przypominaj użytkowników co (godziny)** ustawienie **Agent komputera** strony do 10 godzin.
- Klient Wyświetla okno dialogowe powiadomienia przed upływem ostatecznego terminu wdrożenia więcej niż 24 godziny.
- Okno dialogowe przedstawia opcje włączenia trybu czuwania do, ale nigdy nie większa niż 10 godzin. 
- Jak zbliża się termin ostateczny wdrożenia, okno dialogowe zawiera mniej opcji. Te opcje są zgodne z ustawieniami klienta odpowiedniego dla każdego składnika oś czasu wdrożenia.

W przypadku wysokiego ryzyka, takiego jak wdrożenie sekwencji zadań, która wdraża system operacyjny powiadomienia użytkowników jest bardziej natrętnych. Zamiast powiadomienie przejściowej paska zadań okno dialogowe, tak jak poniżej wyświetla za każdym razem musisz powiadomi, że konserwacji krytyczne oprogramowanie jest wymagane:

![Okno dialogowe wymagane oprogramowanie powiadamia o krytyczne oprogramowanie konserwacji](media/client-toast-notification.png)



## <a name="how-to-check-for-running-executable-files-before-installing-an-application"></a>Jak sprawdzić uruchamiania plików wykonywalnych przed zainstalowaniem aplikacji

W **właściwości** okno dialogowe wdrożenia wpisz na **zainstalować zachowanie** karcie, należy określić co najmniej jednego pliku wykonywalnego. Jeśli jeden z tych plików wykonywalnych jest uruchomiona na kliencie, blokuje instalację typu wdrożenia. Użytkownik należy zamknąć plik wykonywalny uruchomiona, zanim klienta można zainstalować typ wdrożenia. W przypadku wdrożeń z celem wymagane, klient automatycznie zamknąć plik wykonywalny działa prawidłowo.

1. Otwórz **właściwości** okno dialogowe dla każdego typu wdrożenia.
2. Na **zainstalować zachowanie** karcie *<deployment type name>* **właściwości** okno dialogowe, kliknij przycisk **Dodaj**.
3. W **Dodaj lub Edytuj plik wykonywalny** okna dialogowego wprowadź nazwę pliku wykonywalnego, że jeśli uruchomiona, blokuje instalację aplikacji. Opcjonalnie można także wprowadzić przyjazną nazwę dla aplikacji, aby ułatwić jego identyfikację na liście.
4. Kliknij przycisk **OK**, następnie Zamknij *<deployment type name>* **właściwości** okno dialogowe.
5. Podczas wdrażania aplikacji, na **ustawienia wdrażania** strony Kreatora wdrażania oprogramowania, wybierz **automatycznie Zamknij wszystkie uruchomione pliki wykonywalne określone na karcie zachowanie instalacji typu wdrożenia okno dialogowe właściwości**.

Po klienci odbierają wdrażania, stosowane są następujące rozwiązania:

- Jeśli wdrażana aplikacja jako **dostępne**, a użytkownik końcowy próbuje zainstalować ją, klient monituje użytkownika o zamknąć określone pliki uruchamianie pliku wykonywalnego przed kontynuowaniem instalacji.

- Jeśli wdrażana aplikacja jako **wymagane**, a określony do **automatycznie Zamknij wszystkie uruchomione pliki wykonywalne określone na karcie zachowanie instalacji okna dialogowego właściwości typu wdrożenia**, następnie użytkownik zobaczy okno dialogowe z informacją, że określone pliki wykonywalne są automatycznie zamknięte po osiągnięciu ostatecznego terminu instalacji aplikacji. Można zaplanować tych okien dialogowych w **ustawień klienta** > **Agent komputera**. Jeśli nie chcesz, aby użytkownik końcowy, aby wyświetlić te komunikaty, wybierz **Ukryj w programie Software Center i wszystkie powiadomienia** na **środowisko użytkownika** we właściwościach wdrożenia.

- Jeśli wdrażana aplikacja jako **wymagane**i nie określono do **automatycznie Zamknij wszystkie uruchomione pliki wykonywalne określone na karcie zachowanie instalacji okna dialogowego właściwości typu wdrożenia**, następnie instalacja aplikacji kończy się niepowodzeniem, jeśli jeden lub więcej określonych aplikacji są uruchomione.



## <a name="deploy-user-available-applications-on-azure-ad-joined-devices"></a>Wdróż aplikacje dostępne dla użytkowników na urządzeniach przyłączonych do usługi AD platformy Azure
<!-- 1322613 -->
W przypadku wdrażania aplikacji jako dostępnych dla użytkowników, począwszy od wersji 1802 mogą przeglądać i zainstalować je za pomocą Centrum oprogramowania na urządzeniach w usłudze Azure Active Directory (Azure AD).  

#### <a name="prerequisites"></a>Wymagania wstępne

- Włącz protokół HTTPS w punkcie zarządzania  

- Integracja lokacji z [usługi Azure AD](/sccm/core/servers/deploy/configure/azure-services-wizard) dla **zarządzania chmurą**  

    - Skonfiguruj [odnajdowanie użytkowników usługi Azure AD](/sccm/core/servers/deploy/configure/configure-discovery-methods#azureaadisc)  

- Wdrażanie aplikacji jako dostępne do kolekcji użytkowników z usługi Azure AD  

- Dystrybuuj zawartość aplikacji do [punktu dystrybucji w chmurze](/sccm/core/plan-design/hierarchy/use-a-cloud-based-distribution-point)  

- Włącz ustawienie klienta **Użyj nowego centrum oprogramowania** w [agent komputera](/sccm/core/clients/deploy/about-client-settings#computer-agent) grupy  

- System operacyjny klienta musi być system Windows 10 i dołączone do usługi Azure AD. Albo jako czysto chmury przyłączonych do domeny lub hybrydowego Azure przyłączonych do usługi AD.  

- Do obsługi klientów internetowych:  

    - [Brama zarządzania w chmurze](/sccm/core/clients/manage/plan-cloud-management-gateway)  

    - Włącz ustawienie klienta: **Włącz żądania zasad użytkownika od klientów internetowych** w [zasady klienta](/sccm/core/clients/deploy/about-client-settings#client-policy) grupy  

- Do obsługi klientów w intranecie:  

    - Dodaj punkt dystrybucji w chmurze do grupy granic używane przez klientów  

    - Klienci muszą być w stanie rozpoznać w pełni kwalifikowaną nazwę (FQDN) punktu zarządzania z włączonym protokołem HTTPS  



## <a name="next-steps"></a>Następne kroki

   -  [Ustawienia zarządzania wdrożeniami o wysokim ryzyku](../../protect/understand/settings-to-manage-high-risk-deployments.md)  
   -  [Jak skonfigurować ustawienia klienta](../../core/clients/deploy/configure-client-settings.md)
   -  [Podręcznik użytkownika Centrum oprogramowania](/sccm/core/understand/software-center)

