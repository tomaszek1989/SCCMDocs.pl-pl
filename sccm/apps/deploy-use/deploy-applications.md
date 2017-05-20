---
title: "Wdrażanie aplikacji | Dokumentacja firmy Microsoft"
description: "Tworzenie typu wdrożenia lub symulowania wdrożenia aplikacji za pomocą programu System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2629c376-ec43-4f0e-a78b-4223cc9302bf
caps.latest.revision: 10
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 23b1d24e908d04b64c3bbfa518793a44e696d468
ms.openlocfilehash: 0eaa1d13e9c273a6649f50d73fb357f04464d94c
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="deploy-applications-with-system-center-configuration-manager"></a>Wdrażanie aplikacji z System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

 Przed wdrożeniem aplikacji System Center Configuration Manager, należy utworzyć co najmniej jeden typ wdrożenia dla aplikacji. Aby uzyskać więcej informacji o tworzeniu aplikacji i typów wdrożeń, zobacz [tworzenia aplikacji ](../../apps/deploy-use/create-applications.md).

 Można także symulować wdrożenie aplikacji. Ten typ wdrożenia pozwala testować możliwość wdrożenia aplikacji na komputerach bez instalowania lub odinstalowywania aplikacji. Wdrożenie symulowane ocenia metodę wykrywania, wymagania i zależności dla typu wdrożenia i raportuje wyniki w **wdrożeń** węzła **monitorowanie** obszaru roboczego. Aby uzyskać więcej informacji, zobacz [symulowania wdrożenia aplikacji ](../../apps/deploy-use/simulate-application-deployments.md).

> [!IMPORTANT]
>  Można wdrożyć (instalowania lub odinstalowywania) wymaganych aplikacji, ale nie pakiety ani aktualizacje oprogramowania. Zarejestrowane MDM urządzenia nie obsługują także wdrożeń symulowanych czynności użytkownika i ustawień planowania.

## <a name="deploy-an-application"></a>Wdrażanie aplikacji

1.  W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** > **zarządzania aplikacjami** > **aplikacji**.

2.  Z listy **Aplikacje** wybierz aplikację, którą chcesz wdrożyć. Następnie na karcie **Narzędzia główne** w grupie **Wdrażanie** kliknij pozycję **Wdróż**.

### <a name="specify-general-information-about-the-deployment"></a>Określ informacje ogólne dotyczące wdrażania

Na **ogólne** strony Kreatora wdrażania oprogramowania, określ następujące informacje:

- **Oprogramowanie**— tutaj wyświetlana jest aplikacja do wdrożenia. Można kliknąć przycisk **Przeglądaj** , aby wybrać inną aplikację.
- **Kolekcja**--kliknij **Przeglądaj** aby wybrać kolekcję, aby wdrożyć aplikację.
- **Użyj domyślnych grup punktów dystrybucji powiązanych z tą kolekcją**— wybierz tę opcję, jeśli chcesz umieścić zawartość aplikacji w domyślnej grupie punktów dystrybucji kolekcji. Jeśli wybrana Kolekcja nie został skojarzony z grupą punktów dystrybucji, ta opcja jest niedostępny.
- **Dystrybuuj automatycznie zawartość dla zależności**— Jeśli ta opcja jest włączona, a jeśli jakieś typy wdrożenia w aplikacji zawierają zależności, następnie zawartość zależnej aplikacji także zostanie wysłana do punktów dystrybucji.

    >[!IMPORTANT]
    > Jeśli zależna aplikacja zostanie zaktualizowana po wdrożeniu podstawowej aplikacji, nowa zawartość zależności nie będzie automatycznie dystrybuowana.

- **Komentarze (opcjonalnie)** — opcjonalnie wprowadź opis tego wdrożenia.

### <a name="specify-content-options-for-the-deployment"></a>Określ opcje zawartości dla wdrożenia

Na **zawartości** kliknij **Dodaj** do dodawania zawartości skojarzone z tym wdrożeniem do punktów dystrybucji lub grupy punktów dystrybucji. W przypadku wybrania **Użyj domyślnych punktów dystrybucji powiązanych z tą kolekcją** na **ogólne** strony, a następnie ta opcja zostanie automatycznie wypełniona, a mogą być modyfikowane tylko przez członkiem roli zabezpieczeń Administrator aplikacji.

### <a name="specify-deployment-settings"></a>Określ ustawienia wdrożenia

Na **ustawienia wdrażania** strony Kreatora wdrażania oprogramowania, określ następujące informacje:

- **Akcja**— z listy rozwijanej wybierz, czy to wdrożenie służy do **zainstalować** lub **Odinstaluj** aplikacji.

    > [!NOTE]
    >  Jeśli aplikacja zostanie dwukrotnie wdrożona na urządzeniu, jeden raz z akcją **Instaluj** , a drugi raz z akcją **Odinstaluj**, wyższy priorytet będzie miało wdrożenie aplikacji z akcją **Instaluj** .

Po utworzeniu wdrożenia nie można zmienić jego akcji.

- **Cel**— z listy rozwijanej wybierz jedną z następujących opcji:
    - **Dostępne**— Jeśli aplikacja jest wdrażana dla użytkownika, użytkownik będzie widział opublikowaną aplikację w programie Software Center i może zainstalować ją na żądanie.
    - **Wymagane**— aplikacja zostanie wdrożona automatycznie zgodnie z harmonogramem. Jeśli stan wdrożenia aplikacji nie jest ukryty, nazwiska za pomocą aplikacji można śledzić jego stan wdrożenia i zainstaluj aplikację z Centrum oprogramowania przed upływem ostatecznego terminu.

    > [!NOTE]   
    >  Kiedy akcja wdrożenia jest ustawiona na **Odinstaluj**, dla celu wdrożenia jest automatycznie ustawiana opcja **Wymagane** i nie można jej zmienić.  

- **Wdróż automatycznie zgodnie z harmonogramem, czy użytkownik jest zalogowany**— Jeśli wdrażanie jest dla użytkownika, wybierz tę opcję, aby wdrożyć aplikację na podstawowych urządzeniach użytkownika. To ustawienie nie wymaga, aby użytkownik był zalogowany przed uruchomieniem wdrożenia. Nie wybieraj tej opcji, jeśli użytkownik musi podać dane wejściowe w celu ukończenia instalacji. Ta opcja jest dostępna tylko w przypadku, gdy wdrożenie ma cel **Wymagane**.


- **Wysyłanie pakietów wznawiania**— Jeśli dla celu wdrożenia wybrano opcję **wymagane** i wybrano tę opcję, przed zainstalowaniem wdrożenia na komputerach zostanie wysłany pakiet wznawiania. Ten pakiet wznowi komputery w ostatecznym terminie instalacji. Aby użyć tej opcji, należy skonfigurować komputery i sieci do używania funkcji Wake On LAN.
- **Zezwalaj klientom mierzonego połączenia internetowego na pobieranie zawartości po upływie ostatecznego terminu instalacji, co może pociągnąć za sobą dodatkowe koszty**— ta opcja jest dostępna tylko dla wdrożeń z celem **wymagane**.
- **Automatycznie Zamknij wszystkie uruchomione pliki wykonywalne określone na karcie zachowanie instalacji okna dialogowego właściwości typu wdrożenia** — Aby uzyskać więcej informacji o sposobie konfigurowania listy plików wykonywalnych, które mogą uniemożliwić zainstalowanie aplikacji, zobacz **sprawdzania systemem plików wykonywalnych przed zainstalowaniem aplikacji** dalszej części tego tematu.
- **Wymagaj zgody administratora, jeśli użytkownicy zażądają tej aplikacji**— Jeśli ta opcja jest zaznaczona, administrator musi zatwierdzić wszystkie żądania użytkowników dla aplikacji, aby można było zainstalować. Ta opcja jest niedostępne, gdy cel wdrożenia jest **wymagane** lub aplikacja jest wdrażana w kolekcji urządzeń.

    > [!NOTE]
    >  Żądania zatwierdzenia aplikacji są wyświetlane w węźle **Żądania zatwierdzenia** w sekcji **Zarządzanie aplikacjami** w obszarze roboczym **Biblioteka oprogramowania** . Żądanie nie zostanie zatwierdzone w ciągu 45 dni, zostaną usunięte. Ponadto ponownego instalowania klienta programu Configuration Manager może anulować wszystkie żądania oczekuje na zatwierdzenie.
    >  Po zatwierdzeniu aplikacji dla instalacji, później możesz odrzuciła żądanie, klikając **Odmów** w konsoli programu Configuration Manager (wcześniej, ten przycisk został wyszarzone po zatwierdzeniu).
    >  Ta akcja nie powoduje aplikacji do odinstalowania z dowolnego urządzenia, ale zatrzymuje użytkownikom instalowanie nowej kopii aplikacji z Centrum oprogramowania.



- **Automatycznie Uaktualnij wszystkie zastąpione wersje tej aplikacji**— w przypadku wybrania tej opcji wszystkie zastąpione wersje aplikacji zostaną uaktualnione przy użyciu aplikacji zastępującej.

### <a name="specify-scheduling-settings-for-the-deployment"></a>Określ ustawienia planowania wdrożenia

Na **Planowanie** strony wdrażania oprogramowania kreatora, ustaw czas, kiedy ta aplikacja zostanie wdrożona lub udostępnione na urządzeniach klienckich.
Opcje na tej stronie będą się różnić w zależności od tego, czy ustawiono akcję wdrożenia **Dostępne** lub **Wymagane**.

W niektórych przypadkach można umożliwić użytkownikom więcej czasu do instalacji wymagane wdrożenia aplikacji lub aktualizacji oprogramowania poza wszystkie terminy zdefiniowane. To jest zwykle być wymagane po komputerze została wyłączona przez dłuższy czas i musi zainstalować wiele aktualizacji lub wdrożenia aplikacji. Na przykład jeśli użytkownik ma tylko zwróciła urlopie, konieczne może być odczekaj przez długi czas, jak wdrożenia zaległe aplikacji są instalowane. Aby rozwiązać ten problem, można zdefiniować okres prolongaty wymuszania przez wdrożenie ustawień klienta programu Configuration Manager do kolekcji.

Aby skonfigurować okres prolongaty, należy wykonać następujące czynności:

- Na **Agent komputera** strony ustawień klienta, należy skonfigurować nową właściwość **okres prolongaty dla wymuszania po wdrożeniu termin ostateczny (w godzinach)** o wartości między **1** i **120** godzin.
- Na **Planowanie** strony w nowe wdrożenia aplikacji lub we właściwościach istniejącego wdrożenia, zaznacz pole **opóźnienie wymuszania tego wdrożenia, zgodnie z preferencjami użytkownika do okresu prolongaty zdefiniowane w ustawieniach klienta**. Okres prolongaty wymuszania jest używany przez wszystkie wdrożenia, które to zaznaczone pole i są przeznaczone dla urządzeń, do których również wdrożyć ustawienia klienta.

Po zainstalowaniu aplikacji ostatecznego terminu, aplikacja zostanie zainstalowana w pierwszym oknie-business użytkownika skonfigurowanego do tego okresu prolongaty. Jednak nadal użytkownika Otwórz Centrum oprogramowania i aplikacji w dowolnym momencie, które chcą zainstalować. Po wygaśnięciu okresu prolongaty wymuszania przywraca normalne zachowanie w przypadku wdrożeń zaległe.

Jeśli wdrażana aplikacja zastępuje inną aplikację, można ustawić termin ostateczny, użytkownicy otrzymają nową aplikację. W tym celu użyj ustawienia **termin ostateczny** celu aktualizacji użytkowników z zastąpioną aplikacją.

### <a name="specify-user-experience-settings-for-the-deployment"></a>Określ ustawienia czynności użytkownika wdrożenia


Na **środowisko użytkownika** strony Kreatora wdrażania oprogramowania, podaj informacje dotyczące sposobu interakcji użytkowników z instalacją aplikacji.

Wdrażając aplikacje na urządzeniach z systemem Windows Embedded z włączoną obsługą filtru zapisu, można określić, czy zainstalować aplikację na tymczasowej nakładce i zatwierdzić zmiany później lub czy zatwierdzić zmiany w ostatecznym terminie instalacji bądź w oknie obsługi. Po zatwierdzeniu zmian w ostatecznym terminie instalacji bądź w oknie obsługi, należy ponownie uruchomić urządzenie. Trwale zapisać zmiany na urządzeniu.

>[!NOTE]
    >  Po wdrożeniu aplikacji do urządzenia z systemem Windows Embedded upewnij się, że urządzenie należy do kolekcji ze skonfigurowanym oknem obsługi. Aby uzyskać więcej informacji dotyczących sposobu obsługi systemu windows są używane podczas wdrażania aplikacji na urządzeniach Windows Embedded, zobacz [utworzyć Windows Embedded aplikacji](../../apps/get-started/creating-windows-embedded-applications.md).
    > Opcje **Instalacja oprogramowania** i **Ponowne uruchomienie systemu (jeśli wymagane w celu zakończenia instalacji)** nie są używane, jeśli dla celu wdrożenia wybrano opcję **Dostępne**. Można także skonfigurować poziom powiadomienia wyświetlanego użytkownikom po zainstalowaniu aplikacji.

### <a name="specify-alert-options-for-the-deployment"></a>Określ opcje alertów dla wdrożenia

Na **alerty** Kreatora wdrażania oprogramowania, skonfiguruj sposób generowania alertów dotyczących tego wdrożenia w programu Configuration Manager i System Center Operations Manager. Można skonfigurować progi dla alertów raportowania lub wyłączyć raportowanie na czas wdrażania.

### <a name="associate-the-deployment-with-an-ios-app-configuration-policy"></a>Kojarzenie wdrożenia z zasad konfiguracji systemu iOS aplikacji

Na **zasady konfiguracji aplikacji** kliknij **New** do skojarzenia tego wdrożenia z zasad konfiguracji systemu iOS aplikacji (jeśli został utworzony). Aby uzyskać więcej informacji o tym typie zasad, zobacz [skonfigurowanie aplikacji systemu iOS z zasady konfiguracji aplikacji](../../apps/deploy-use/configure-ios-apps-with-app-configuration-policies.md).

### <a name="finish-up"></a>Zakończ w

Na **Podsumowanie** strony Kreatora wdrażania oprogramowania, przejrzyj akcje, które zostaną wykonane przez to wdrożenie, a następnie kliknij przycisk **dalej** aby zakończyć pracę kreatora.

Nowe wdrożenie zostanie wyświetlone na liście **Wdrożenia** w węźle **Wdrożenia** obszaru roboczego **Monitorowanie** . Można dokonać edycji właściwości tego wdrożenia lub usunąć wdrożenie z karty **Wdrożenia** okienka szczegółów aplikacji.

## <a name="delete-an-application-deployment"></a>Usunięcie wdrożenia aplikacji

1.  W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** > **zarządzania aplikacjami** > **aplikacji**.

3.  W **aplikacji** listy, wybierz aplikację, która obejmuje wdrażanie spowoduje usunięcie.

4.  Na karcie **Wdrożenia** listy *<nazwa aplikacji\>* wybierz wdrożenie aplikacji do usunięcia. Następnie na **wdrożenia** w karcie **wdrożenia** , kliknij przycisk **usunąć**.

 Podczas usuwania wdrożenia aplikacji nie są usuwane żadne wystąpienia aplikacji, które zostały już zainstalowane. Aby usunąć te aplikacje, należy wdrożyć aplikację na komputerach z **Odinstaluj**. Usunięcie wdrożenia aplikacji lub usunięcie zasobu z kolekcji wdrażania spowoduje, że aplikacja nie będzie już widoczna w programie Software Center.

## <a name="user-notifications-for-required-deployments"></a>Powiadomienia użytkowników w przypadku wymaganych wdrożeń
Po otrzymaniu wymaganego oprogramowania z **Odłóż i Przypomnij mi** ustawienie, możesz wybrać z listy rozwijanej następujące wartości:
- **Później**--Określa zaplanowane powiadomienia na podstawie ustawień powiadomień skonfigurowanym w ustawieniach agenta klienta.
- **Stały czas**— Określa, czy powiadomienia są planowane do wyświetlenia ponownie po zaznaczony czas. Na przykład w przypadku wybrania 30 minut powiadomienia wyświetli się ponownie w ciągu 30 minut.

![Komputer agenta strony w ustawieniach agenta klienta](media/ComputerAgentSettings.png)

Czas maksymalny odłożenia zawsze opiera się na wartości powiadomienia skonfigurowanym w ustawieniach agenta klienta w każdej chwili wzdłuż osi czasu wdrożenia. Na przykład jeśli **wdrożenia termin ostateczny dłużej niż 24 godziny, przypominaj użytkowników co (godziny)** ustawienie na **Agent komputera** strony jest skonfigurowany do 10 godzin i jest więcej niż 24 godziny przed upływem ostatecznego terminu przy uruchomieniu okna dialogowego, użytkownik będzie udostępniana zestaw opcji czuwania do ale nigdy nie większa niż 10 godzin. Jak zbliża się termin, okno dialogowe wyświetli mniej opcji zgodne z odpowiednimi ustawieniami agenta klienta dla każdego składnika oś czasu wdrożenia.

Ponadto dla wdrożenia o wysokim ryzyku, takie jak sekwencji zadań, która wdraża system operacyjny, proces powiadamiania użytkownika jest teraz bardziej niepożądanego. Zamiast powiadomień paska zadań przejściowy okno dialogowe, takich jak następujące wyświetla na tym komputerze zawsze możesz jest wyświetlane powiadomienie, że konserwacji krytyczne oprogramowanie jest wymagane:

![Wymagane oprogramowanie okna dialogowego](media/client-toast-notification.png)

## <a name="how-to-check-for-running-executable-files-before-installing-an-application"></a>Informacje o sprawdzaniu systemem plików wykonywalnych przed zainstalowaniem aplikacji

>[!Tip]
>Wprowadzona w wersji 1702, jest to funkcja wersji wstępnej. Aby ją włączyć, zobacz [funkcje w programie System Center Configuration Manager w wersji wstępnej](https://docs.microsoft.com/sccm/core/servers/manage/pre-release-features).

W **właściwości** okno dialogowe wdrożenia typu na **zainstalować zachowanie** karcie, można określić jeden więcej plików wykonywalnych, które działa, spowoduje zablokowania instalacji typu wdrożenia. Użytkownik należy zamknąć plik wykonywalny jest uruchomiona (lub może zostać zamknięty w automatycznie w przypadku wdrożeń z celem wymagane) przed wdrożeniem typ może być instalowany. Aby skonfigurować to:

1. Otwórz **właściwości** okno dialogowe dla każdego typu wdrożenia.
2. Na **zainstalować zachowanie** na karcie  *<deployment type name>*  **właściwości** okno dialogowe, kliknij przycisk **Dodaj**.
3. W **Dodaj lub Edytuj plik wykonywalny** oknie dialogowym Wprowadź nazwę pliku wykonywalnego, który działa, spowoduje zablokowania instalacji aplikacji. Opcjonalnie można także wprowadzić przyjazną nazwę dla aplikacji, aby ułatwić jego identyfikację na liście.
4. Kliknij przycisk **OK**, następnie Zamknij  *<deployment type name>*  **właściwości** okno dialogowe.
5. Następnie podczas wdrażania aplikacji na **ustawienia wdrażania** strony Kreatora wdrażania oprogramowania, wybierz **automatycznie Zamknij wszystkie uruchomione pliki wykonywalne określone na karcie zachowanie instalacji okna dialogowego właściwości typu wdrożenia**, następnie przejdź do wdrożenia aplikacji.

Po aplikacji osiągnie komputerów klienckich, stosuje się następujące działania:

- Jeśli aplikacja została wdrożona jako **dostępne**i użytkownik końcowy spróbuje go zainstalować, zostanie wyświetlony monit do Zamknij wszystkie uruchomione pliki wykonywalne określone przed kontynuacją instalacji.

- Jeśli aplikacja została wdrożona jako **wymagane**, a opcja **automatycznie Zamknij wszystkie uruchomione pliki wykonywalne określone na karcie zachowanie instalacji okna dialogowego właściwości typu wdrożenia** jest zaznaczone, zobaczy okno dialogowe, które informuje, że określone pliki wykonywalne zostaną automatycznie zamknięte po osiągnięciu ostatecznego terminu instalacji aplikacji. Można zaplanować tych okien dialogowych w **ustawień klienta** > **Agent komputera**. Jeśli nie chcesz użytkownika końcowego, aby wyświetlić te wiadomości, wybierz **Ukryj w programie Software Center i wszystkie powiadomienia** na **środowisko użytkownika** kartę właściwości wdrożenia.

- Jeśli aplikacja została wdrożona jako **wymagane** i opcję **automatycznie Zamknij wszystkie uruchomione pliki wykonywalne określone na karcie zachowanie instalacji okna dialogowego właściwości typu wdrożenia** nie jest zaznaczone, a następnie instalacja aplikacji zakończy się niepowodzeniem, jeśli jeden lub więcej określonych aplikacji są uruchomione.

## <a name="for-more-information"></a>Aby uzyskać więcej informacji:
- [Ustawienia zarządzania wdrożeniami o wysokim ryzyku](../../protect/understand/settings-to-manage-high-risk-deployments.md)
- [Jak skonfigurować ustawienia klienta](../../core/clients/deploy/configure-client-settings.md)

