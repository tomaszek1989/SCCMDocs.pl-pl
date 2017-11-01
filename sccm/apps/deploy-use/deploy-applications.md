---
title: "Wdrażanie aplikacji"
titleSuffix: Configuration Manager
description: "Tworzenie typu wdrożenia lub symulować wdrożenie aplikacji za pomocą programu System Center Configuration Manager."
ms.custom: na
ms.date: 7/31/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2629c376-ec43-4f0e-a78b-4223cc9302bf
caps.latest.revision: "10"
caps.handback.revision: "0"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.openlocfilehash: 31c8a2e212de8c112b68d68e108db3463516142f
ms.sourcegitcommit: b36f8c8b06e4b2e13f8c1500a82af79a071ab4f6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/20/2017
---
# <a name="deploy-applications-with-system-center-configuration-manager"></a>Wdrażanie aplikacji w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Przed wdrożeniem aplikacji programu System Center Configuration Manager, należy utworzyć co najmniej jeden typ wdrożenia dla aplikacji. Aby uzyskać więcej informacji na temat tworzenia aplikacji i typów wdrożeń, zobacz [tworzenie aplikacji](/sccm/apps/deploy-use/create-applications).

 Można także symulować wdrożenie aplikacji. Ten typ wdrożenia pozwala testować możliwość wdrożenia aplikacji na komputerach bez instalowania lub odinstalowywania aplikacji. Wdrożenie symulowane ocenia metodę wykrywania, wymagania i zależności dla typu wdrożenia i raportuje wyniki w **wdrożeń** węzła **monitorowanie** obszaru roboczego. Aby uzyskać więcej informacji, zobacz [symulowanie wdrożenia aplikacji](/sccm/apps/deploy-use/simulate-application-deployments).

> [!IMPORTANT]
>  Można wdrożyć (zainstalować lub odinstalować) wymagane aplikacje, ale nie pakiety ani aktualizacje oprogramowania. Zarządzanie urządzeniami Przenośnymi, zarejestrowane urządzenia nie obsługują również wdrożenia symulowane, użytkowników lub ustawień planowania.

## <a name="deploy-an-application"></a>Wdrażanie aplikacji

1.  W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** > **Zarządzanie aplikacjami** > **aplikacji**.

2.  Z listy **Aplikacje** wybierz aplikację, którą chcesz wdrożyć. Następnie na karcie **Narzędzia główne** w grupie **Wdrażanie** kliknij pozycję **Wdróż**.

### <a name="specify-general-information-about-the-deployment"></a>Określ informacje ogólne dotyczące wdrożenia

Na **ogólne** strony Kreatora wdrażania oprogramowania Podaj następujące informacje:

- **Oprogramowanie**  
Spowoduje to wyświetlenie aplikację do wdrożenia. Można kliknąć przycisk **Przeglądaj** , aby wybrać inną aplikację.
- **Kolekcja**  
Kliknij przycisk **Przeglądaj** aby wybrać kolekcję, aby wdrożyć aplikację.
- **Użyj domyślnych grup punktów dystrybucji powiązanych z tą kolekcją**  
Wybierz tę opcję, jeśli chcesz umieścić zawartość aplikacji w domyślnej grupie punktów dystrybucji kolekcji. Jeśli wybrana Kolekcja nie został skojarzony z grupą punktów dystrybucji, ta opcja jest szary.
- **Dystrybuuj automatycznie zawartość dla zależności**  
Jeśli ta opcja jest włączona, a jakieś typy wdrożenia w aplikacji zawierają zależności, zawartość zależnej aplikacji zostanie także wysłana do punktów dystrybucji.

    >[!IMPORTANT]
    > Jeśli zależna aplikacja zostanie zaktualizowana po wdrożeniu podstawowej aplikacji, nowa zawartość zależności nie będzie automatycznie dystrybuowana.

- **Komentarze (opcjonalne)**  
Opcjonalnie wprowadź opis dla tego wdrożenia.

### <a name="specify-content-options-for-the-deployment"></a>Określenie opcji zawartości wdrożenia

Na **zawartości** kliknij przycisk **Dodaj** można dodać zawartość skojarzona z tym wdrożeniem do punktów dystrybucji lub grupy punktów dystrybucji. Jeśli wybrano **Użyj domyślnych punktów dystrybucji powiązanych z tą kolekcją** na **ogólne** strony, a następnie ta opcja jest wypełniane automatycznie i może zostać zmodyfikowany tylko członek roli zabezpieczeń Administrator aplikacji.

### <a name="specify-deployment-settings"></a>Określ ustawienia wdrożenia

Na **ustawienia wdrażania** strony Kreatora wdrażania oprogramowania Podaj następujące informacje:

- **Akcja**  
Z listy rozwijanej wybierz, czy to wdrożenie służy do **zainstalować** lub **Odinstaluj** aplikacji.

    > [!NOTE]
    >  Jeśli aplikacja zostanie dwukrotnie wdrożona na urządzeniu, jeden raz z akcją **zainstalować** i drugi raz z akcją **Odinstaluj**, wdrożenie aplikacji z akcją **zainstalować** ma wyższy priorytet.

Po utworzeniu wdrożenia nie można zmienić jego akcji.

- **Cel**  
Z listy rozwijanej wybierz jedną z następujących opcji:
    - **Dostępne**  
    Jeśli aplikacja jest wdrażana dla użytkownika, użytkownik widzi opublikowaną aplikację w programie Software Center i może zainstalować ją na żądanie.
    - **Wymagane**  
    Aplikacja zostanie wdrożona automatycznie zgodnie z harmonogramem. Jeśli stan wdrożenia aplikacji nie jest ukryty, wszystkich osób korzystających z aplikacji można śledzić stan wdrożenia i instalować aplikacji z Centrum oprogramowania przed upływem ostatecznego terminu.

    > [!NOTE]   
    >  Kiedy akcja wdrożenia jest ustawiona na **Odinstaluj**, dla celu wdrożenia jest automatycznie ustawiana opcja **Wymagane** i nie można jej zmienić.  

- **Wdróż automatycznie zgodnie z harmonogramem, czy użytkownik jest zalogowany**  
Jeśli wdrożenie dla użytkownika, wybierz tę opcję, aby wdrożyć aplikację na podstawowych urządzeniach użytkownika. To ustawienie nie wymaga, aby użytkownik był zalogowany przed uruchomieniem wdrożenia. Nie wybieraj tej opcji, jeśli użytkownik musi podać dane wejściowe w celu ukończenia instalacji. Ta opcja jest dostępna tylko w przypadku, gdy wdrożenie ma cel **Wymagane**.

- **Wyślij pakiety wznawiania**  
Jeśli dla celu wdrożenia wybrano opcję **wymagane** i wybrano tę opcję, przed zainstalowaniem wdrożenia do komputerów jest wysłany pakiet wznawiania. Ten pakiet wznawia pracę komputerów w ostatecznym terminie instalacji. Aby użyć tej opcji, należy skonfigurować komputery i sieci do używania funkcji Wake On LAN.
- **Zezwalaj klientom mierzonego połączenia internetowego na pobieranie zawartości po upływie ostatecznego terminu instalacji, co może pociągnąć za sobą dodatkowe koszty**  
Ta opcja jest dostępna tylko dla wdrożeń z celem **wymagane**.
- **Automatycznie Zamknij wszystkie uruchomione pliki wykonywalne określone na karcie zachowanie instalacji okna dialogowego właściwości typu wdrożenia**  
Aby uzyskać więcej informacji o sposobie konfigurowania listy plików wykonywalnych, które mogą uniemożliwić zainstalowanie aplikacji, zobacz **sprawdzania uruchamianie plików wykonywalnych przed zainstalowaniem aplikacji** dalszej części tego tematu.
- **Wymagaj zgody administratora, jeśli użytkownicy zażądają tej aplikacji**  
Jeśli ta opcja jest zaznaczona, administrator musi zatwierdzić wszystkie żądania użytkowników dla aplikacji, aby można było zainstalować. Ta opcja jest niedostępne, gdy cel wdrożenia jest **wymagane** lub gdy aplikacja jest wdrażana w kolekcji urządzeń.

    > [!NOTE]
    >  Żądania zatwierdzenia aplikacji są wyświetlane w węźle **Żądania zatwierdzenia** w sekcji **Zarządzanie aplikacjami** w obszarze roboczym **Biblioteka oprogramowania** . Jeśli żądanie nie zostanie zatwierdzone w ciągu 45 dni, zostanie ono usunięte. Ponadto ponowne zainstalowanie klienta programu Configuration Manager może spowodować anulowanie wszystkich żądań oczekuje na zatwierdzenie.
    >  Po zatwierdzeniu aplikacji do instalacji, później możesz odrzuciła żądanie, klikając **Odmów** w konsoli programu Configuration Manager (wcześniej, to przycisk został szary po zatwierdzeniu).
    >  Ta akcja nie powoduje aplikacji ma zostać odinstalowany z dowolnego urządzenia, ale zatrzymać użytkownikom instalowanie nowych kopii aplikacji z Centrum oprogramowania.

- **Automatycznie Uaktualnij wszystkie zastąpione wersje tej aplikacji**  
Jeśli ta opcja jest zaznaczona, wszystkie zastąpione wersje aplikacji jest uaktualniony przy użyciu aplikacji zastępującej.

### <a name="specify-scheduling-settings-for-the-deployment"></a>Określ ustawienia planowania wdrożenia

Na **Planowanie** strony wdrażania oprogramowania, ustawiając czas, kiedy ta aplikacja jest wdrożony lub jest niedostępny na urządzeniach klienckich.
Opcje na tej stronie są różne w zależności od tego, czy ustawiono akcję wdrożenia **dostępne** lub **wymagane**.

W niektórych przypadkach można umożliwić użytkownikom więcej czasu do instalacji wymagane wdrożenia aplikacji lub aktualizacji oprogramowania poza wszystkie terminy skonfigurowane. Jest to zwykle wymagane, jeśli komputer został wyłączony przez dłuższy czas i musi zainstalować wiele aktualizacji lub wdrożenia aplikacji. Na przykład jeśli użytkownik został zwrócony z urlopu, może być mają oczekiwać przez długi czas i wdrożeń aplikacji zaległe są zainstalowane. Aby rozwiązać ten problem, można zdefiniować okres prolongaty wymuszania przez wdrożenie ustawienia klienta programu Configuration Manager do kolekcji.

Aby skonfigurować okres prolongaty, należy wykonać następujące czynności:

- Na **Agent komputera** strony ustawień klienta, należy skonfigurować nową właściwość **okres prolongaty wymuszania po wdrożeniu terminu wdrożenia (godziny)** z wartością pomiędzy **1** i **120** godzin.
- Na **Planowanie** strony w ramach nowego wdrożenia wymaganej aplikacji lub we właściwościach istniejącego wdrożenia, zaznacz pole **Opóźnij wymuszenie dotyczące tego wdrożenia zgodnie z preferencjami użytkownika do okresu prolongaty zdefiniowanego w ustawieniach klienta**. Okres prolongaty wymuszania jest używany przez wszystkie wdrożenia zaznaczone to pole, które są przeznaczone dla urządzeń, na których wdrożono również ustawienie klienta.

Po zainstalowaniu aplikacji terminu ostatecznego, aplikacja zostanie zainstalowana w pierwszym oknie-business skonfigurowanego przez użytkownika do tego okresu prolongaty. Jednak użytkownik może nadal otworzyć programu Software Center i zainstalować aplikację w dowolnym momencie, które mają. Po wygaśnięciu okresu prolongaty wymuszania wraca do normalnej zachowaniem wdrożeń zaległe.

W przypadku aplikacji, które wdrażasz zastępuje inną aplikację, można ustawić ostateczny termin instalacji, gdy użytkownicy otrzymają nową aplikację. To zrobić za pomocą ustawienia **ostateczny termin instalacji** celu aktualizacji użytkowników z zastąpioną aplikacją.

### <a name="specify-user-experience-settings-for-the-deployment"></a>Określ ustawienia czynności użytkownika dla wdrożenia


Na **środowisko użytkownika** strony Kreatora wdrażania oprogramowania Podaj informacje dotyczące sposobu interakcji użytkowników z instalacją aplikacji.

Wdrażając aplikacje na urządzeniach z systemem Windows Embedded z włączoną obsługą filtru zapisu, można określić, czy zainstalować aplikację na tymczasowej nakładce i zatwierdzić zmiany później lub czy zatwierdzić zmiany w ostatecznym terminie instalacji bądź w oknie obsługi. Po zatwierdzeniu zmian w terminie ostatecznym instalacji lub w oknie obsługi należy ponownie uruchomić urządzenie. Trwale zapisać zmiany na urządzeniu.

>[!NOTE]
    >  Po wdrożeniu aplikacji do urządzenia z systemem Windows Embedded upewnij się, że urządzenie należy do kolekcji ze skonfigurowanym oknem obsługi. Aby uzyskać więcej informacji o sposobie oknach obsługi używanych podczas wdrażania aplikacji na urządzeniach Windows Embedded, zobacz [aplikacji Utwórz systemu Windows Embedded](../../apps/get-started/creating-windows-embedded-applications.md).
    > Opcje **Instalacja oprogramowania** i **Ponowne uruchomienie systemu (jeśli wymagane w celu zakończenia instalacji)** nie są używane, jeśli dla celu wdrożenia wybrano opcję **Dostępne**. Można także skonfigurować poziom powiadomienia wyświetlanego użytkownikom po zainstalowaniu aplikacji.

### <a name="specify-alert-options-for-the-deployment"></a>Określ opcje alertów dla wdrożenia

Na **alerty** Kreatora wdrażania oprogramowania Skonfiguruj sposób generowania alertów dotyczących tego wdrożenia programu Configuration Manager i System Center Operations Manager. Można skonfigurować progi dla alertów raportowania lub wyłączyć raportowanie na czas wdrażania.

### <a name="associate-the-deployment-with-an-ios-app-configuration-policy"></a>Skojarz wdrożenia przy użyciu zasad konfiguracji aplikacji systemu iOS

Na **zasady konfiguracji aplikacji** kliknij przycisk **nowy** Aby skojarzyć to wdrożenie przy użyciu zasad konfiguracji aplikacji systemu iOS (jeśli został utworzony). Aby uzyskać więcej informacji na temat tego typu zasad, zobacz [Konfigurowanie aplikacji systemu iOS przy użyciu zasad konfiguracji aplikacji](../../apps/deploy-use/configure-ios-apps-with-app-configuration-policies.md).

### <a name="finish-up"></a>Aby zakończyć

Na **Podsumowanie** strony Kreatora wdrażania oprogramowania Przejrzyj akcje, które są pobierane przez to wdrożenie, a następnie kliknij przycisk **dalej** aby zakończyć pracę kreatora.

Nowe wdrożenie jest wyświetlany w **wdrożeń** na liście **wdrożeń** węzła **monitorowanie** obszaru roboczego. Można dokonać edycji właściwości tego wdrożenia lub usunąć wdrożenie z karty **Wdrożenia** okienka szczegółów aplikacji.

## <a name="delete-an-application-deployment"></a>Usunięcie wdrożenia aplikacji

1.  W konsoli programu Configuration Manager, przejdź do **Biblioteka oprogramowania** > **Zarządzanie aplikacjami** > **aplikacji**.
3.  W **aplikacji** listy, wybierz aplikację, która zawiera wdrożenia należy usunąć.
4.  Na karcie **Wdrożenia** listy *<nazwa aplikacji\>* wybierz wdrożenie aplikacji do usunięcia. Następnie na **wdrożenia** karcie **wdrożenia** kliknij przycisk **usunąć**.

Podczas usuwania wdrożenia aplikacji nie są usuwane żadne wystąpienia aplikacji, które zostały już zainstalowane. Aby usunąć te aplikacje, należy wdrożyć na komputerach aplikację z **Odinstaluj**. Usunięcie wdrożenia aplikacji lub usunięcie zasobu z kolekcji wdrażania spowoduje, że aplikacja nie będzie już widoczna w programie Software Center.

## <a name="user-notifications-for-required-deployments"></a>Powiadomienia użytkowników w celu dokonania wymaganych wdrożeń
Gdy pojawi się wymagane oprogramowanie z **Odłóż i Przypomnij** ustawienie, można wybrać z listy rozwijanej następujące wartości:
- **Później**  
Określa, czy powiadomienia zostały zaplanowane na podstawie ustawień powiadomień skonfigurowanego w ustawieniach agenta klienta.
- **Stały czas**  
Określa, że powiadomienie zostanie zaplanowane do wyświetlenia ponownie po wybrana wartość czasu. Na przykład w przypadku wybrania 30 minut, powiadomienie będzie wyświetlane ponownie w ciągu 30 minut.

![Konfiguracja agenta w ustawieniach agenta klienta](media/ComputerAgentSettings.png)

Czas włączenia trybu czuwania maksymalną zawsze opiera się na wartości powiadomień skonfigurowanego w ustawieniach agenta klienta w czasie, co na osi czasu wdrażania. Na przykład jeśli **wdrożenia termin ostateczny dłuższego niż 24 godziny, przypominaj użytkowników co (godziny)** ustawienie **Agent komputera** strona jest skonfigurowana do 10 godzin i po uruchomieniu okna dialogowego jest więcej niż 24 godziny przed upływem ostatecznego terminu, zostanie obejmowałoby z zestawu opcji włączenia trybu czuwania do lecz nigdy nie więcej niż 10 godzin. Jak zbliża się termin, okno dialogowe zawiera mniej opcji zgodne z odpowiednimi ustawieniami agenta klienta dla każdego składnika oś czasu wdrożenia.

Ponadto dla wysokiego ryzyka, takiego jak wdrożenie sekwencji zadań, która wdraża system operacyjny użytkowników powiadomień jest teraz bardziej natrętnych. Zamiast powiadomienie zadań przejściowy okno dialogowe, tak jak poniżej przedstawia na komputerze zawsze należy są powiadamiani, czy konserwacji krytyczne oprogramowanie jest wymagane:

![Wymagane oprogramowanie okna dialogowego](media/client-toast-notification.png)

## <a name="how-to-check-for-running-executable-files-before-installing-an-application"></a>Jak sprawdzić uruchamiania plików wykonywalnych przed zainstalowaniem aplikacji

>[!Tip]
>Z wersją 1702 jest to funkcja wersji wstępnej. Aby ją włączyć, zobacz [w programie System Center Configuration Manager funkcje wersji wstępnej](https://docs.microsoft.com/sccm/core/servers/manage/pre-release-features).
> Począwszy od wersji 1706, ta funkcja nie jest już funkcji wersji wstępnej.

W **właściwości** okno dialogowe wdrożenia wpisz na **zainstalować zachowanie** kartę, można określić jedną lub więcej pliki wykonywalne, jeśli uruchomiony, blokuje to instalacji typu wdrożenia. Użytkownik musi zamknąć plik wykonywalny uruchomiona (lub może zostać zamknięty w automatycznie w przypadku wdrożeń z celem wymagane) przed wdrożeniem można było zainstalować typ. Aby skonfigurować to:

1. Otwórz **właściwości** okno dialogowe dla każdego typu wdrożenia.
2. Na **zainstalować zachowanie** karcie  *<deployment type name>*  **właściwości** okno dialogowe, kliknij przycisk **Dodaj**.
3. W **Dodaj lub Edytuj plik wykonywalny** okna dialogowego wprowadź nazwę pliku wykonywalnego, że jeśli uruchomiona, blokuje instalację aplikacji. Opcjonalnie można także wprowadzić przyjazną nazwę dla aplikacji, aby ułatwić jego identyfikację na liście.
4. Kliknij przycisk **OK**, następnie Zamknij  *<deployment type name>*  **właściwości** okno dialogowe.
5. Następnie podczas wdrażania aplikacji na **ustawienia wdrażania** strony Kreatora wdrażania oprogramowania, wybierz **automatycznie Zamknij wszystkie uruchomione pliki wykonywalne określone na karcie zachowanie instalacji okna dialogowego właściwości typu wdrożenia**, następnie kontynuuj wdrożyć aplikację.

Po aplikacja osiągnie komputerów klienckich, stosuje się następujące działania:

- Jeśli aplikacja została wdrożona jako **dostępne**, a użytkownik końcowy próbuje zainstalować go, są monitowani o Zamknij wszystkie uruchomione pliki wykonywalne określona zanim można kontynuować instalacji.

- Jeśli aplikacja została wdrożona jako **wymagane**wraz z opcją **automatycznie Zamknij wszystkie uruchomione pliki wykonywalne określone na karcie zachowanie instalacji okna dialogowego właściwości typu wdrożenia** jest zaznaczone, zobacz okno dialogowe z informacją o tym, że pliki wykonywalne określonego automatycznie są zamknięte po osiągnięciu ostatecznego terminu instalacji aplikacji. Można zaplanować tych okien dialogowych w **ustawień klienta** > **Agent komputera**. Jeśli nie chcesz, aby użytkownik końcowy, aby wyświetlić te komunikaty, wybierz **Ukryj w programie Software Center i wszystkie powiadomienia** na **środowisko użytkownika** we właściwościach wdrożenia.

- Jeśli aplikacja została wdrożona jako **wymagane** wraz z opcją **automatycznie Zamknij wszystkie uruchomione pliki wykonywalne określone na karcie zachowanie instalacji okna dialogowego właściwości typu wdrożenia** nie jest zaznaczone, a następnie instalacja aplikacji kończy się niepowodzeniem, jeśli jeden lub więcej określonych aplikacji jest uruchomione.

## <a name="for-more-information"></a>Więcej informacji

   -  [Ustawienia zarządzania wdrożeniami o wysokim ryzyku](../../protect/understand/settings-to-manage-high-risk-deployments.md)  
   -  [Jak skonfigurować ustawienia klienta](../../core/clients/deploy/configure-client-settings.md)
