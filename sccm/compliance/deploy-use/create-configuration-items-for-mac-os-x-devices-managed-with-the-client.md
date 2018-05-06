---
title: 'Tworzenie elementów konfiguracji dla komputerów zarządzanych przez klienta Mac '
titleSuffix: Configuration Manager
description: Umożliwia zarządzanie ustawieniami urządzeń z systemem Mac OS X, należy użyć elementu konfiguracji programu System Center Configuration Manager Mac OS X.
ms.date: 03/28/2017
ms.prod: configuration-manager
ms.technology: configmgr-compliance
ms.topic: conceptual
ms.assetid: 722d5bf5-bedc-4dfc-b324-6eeb773874e9
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: e6358c8e84d12c37418d7a1af459e775783efaa2
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-create-configuration-items-for-mac-os-x-devices-managed-with-the-system-center-configuration-manager-client"></a>Tworzenie elementów konfiguracji dla urządzeń z systemem Mac OS X zarządzanych za pomocą klienta programu System Center Configuration Manager
Użyj programu System Center Configuration Manager**systemu Mac OS X (niestandardowy)** element konfiguracji do zarządzania ustawieniami urządzeń systemu Mac OS X, które są zarządzane przez klienta programu Configuration Manager.  
  
 System operacyjny Mac OS X używa plików listy właściwości (plików plist) do przechowywania ustawień aplikacji. Użyj ustawień zgodności, aby ocenić i skorygować ustawienia w pliku listy właściwości. Ustawieniami systemu Mac OS X możesz także zarządzać za pomocą skryptu powłoki zwracającego wartość, którą można ocenić i skorygować w celu zachowania zgodności.  
  
### <a name="to-create-a-custom-mac-os-x-configuration-item"></a>Tworzenie niestandardowego elementu konfiguracji systemu Mac OS X  
  
1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność**.  
  
2.  W obszarze roboczym **Zasoby i zgodność** rozwiń węzeł **Ustawienia zgodności**, a następnie kliknij pozycję **Elementy konfiguracji**.  
  
3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij pozycję **Utwórz element konfiguracji**.  
  
4.  Na stronie **Ogólne** w **Kreatorze tworzenia elementu konfiguracji** podaj nazwę i opcjonalny opis elementu konfiguracji.  
  
5.  W obszarze **Określ typ elementu konfiguracji, który chcesz utworzyć** wybierz pozycję **Mac OS X (niestandardowy)**.  
  
6.  Kliknij przycisk **kategorii** możesz utworzyć i przypisać kategorie ułatwiające wyszukiwanie i filtrowanie elementów konfiguracji w konsoli programu Configuration Manager.  
  
7.  Na stronie **Obsługiwane platformy** kreatora wybierz wersje systemu Mac OS X, które będą oceniać element konfiguracji.  
  
8.  Na stronie **Ustawienia** kreatora dodasz nowe ustawienia, które będą oceniane pod kątem zgodności na komputerach Mac. Kliknij pozycję **Nowy**, aby otworzyć okno dialogowe **Tworzenie ustawienia**.  
  
9. W oknie dialogowym **Tworzenie ustawienia** podaj unikatową nazwę i opis ustawienia.  
  
10. Wybierz wartość dla pozycji **Typ ustawienia**, a następnie podaj wymagane informacje przedstawione w poniższej tabeli:  
  
    -   **Preferencje systemu Mac OS X** -  
  
        -   **Identyfikator aplikacji** — określ identyfikator aplikacji dla pliku listy właściwości zawierającego klucz, który chcesz ocenić pod kątem zgodności.  
  
             Na przykład jeśli chcesz zmienić ustawienia przeglądarki sieci Web Safari, możesz użyć identyfikatora **com.apple.Safari.plist**.  
  
        -   **Klucz** — określ nazwę klucza, który chcesz ocenić pod kątem zgodności na komputerach Mac. Użyj następującej składni: */<słownik\>/<nazwa klucza\>*.  
  
            > [!IMPORTANT]  
            >  W nazwie klucza uwzględniana jest wielkość liter. Nazwa ta nie zostanie oceniona, jeśli będzie różnić się od nazwy klucza na komputerze Mac. Nie można także edytować nazwy klucza po jej określeniu. Jeśli chcesz zmienić nazwę klucza, usuń ustawienie i utwórz je ponownie.  
  
    -   **Skrypt** -  
  
        -   **Skrypt wykrywania** — kliknij polecenie **Dodaj skrypt**, a następnie podaj skrypt powłoki, aby ocenić ustawienia na komputerze Mac pod kątem zgodności. Użyj **echo** polecenie w skrypcie powłoki, aby powrócić do programu Configuration Manager wartości zgodności. Program Configuration Manager używa wyników zwróconych w **STDOUT** do oceny zgodności.  
  
            > [!IMPORTANT]  
            >  W skrypcie odnajdywania nie można umieścić polecenia **reboot**. Ponieważ skrypty odnajdywania są uruchamiane przy każdym ponownym uruchomieniu klienta, spowodowałoby to ciągłe ponowne uruchamianie komputera Mac.  
  
        -   **Skrypt korygujący (opcjonalny)** — opcjonalnie kliknij polecenie **Dodaj skrypt**, a następnie podaj skrypt powłoki, który służy do korygowania wszelkich niezgodnych ustawień znalezionych na komputerach klienckich Mac.  
  
            > [!IMPORTANT]  
            >  W celu zapewnienia, że w skrypcie nie znajdą się żadne znaki formatujące, których komputer Mac nie może zinterpretować, nie używaj funkcji kopiowania i wklejania, lecz wpisz skrypt.  
  
11. Wybierz wartość dla pozycji **Typ danych**, tzn. format danych zwracanych przez warunek, zanim zostaną one użyte do oceny ustawienia.  
  
    > [!NOTE]  
    >  Typ danych **Liczba zmiennoprzecinkowa** obsługuje tylko 3 cyfry po przecinku.  
    >   
    >  Menedżer konfiguracji nie obsługuje używania **logiczna** typ danych w ustawieniach skryptu elementu konfiguracji dla komputerów Mac. Zamiast tego należy ustawić typ danych na wartość **Liczba całkowita** i upewnić się, że skrypt zwraca liczbę całkowitą.  
  
12. Kliknij przycisk **OK**, aby zapisać ustawienia i zamknąć okno dialogowe **Tworzenie ustawienia**, a następnie dodaj tyle ustawień, ile potrzebujesz.  
  
13. Na stronie **Reguły zgodności** kreatora określisz warunki, które definiują zgodność elementu konfiguracji. Zanim będzie można ocenić ustawienie pod kątem zgodności, musi istnieć co najmniej jedna reguła zgodności. Kliknij pozycję **Nowa**, aby dodać nową regułę.  
  
14. W oknie dialogowym **Tworzenie reguły** podaj następujące informacje:  
  
    -   **Nazwa:** Wprowadź nazwę reguły zgodności.  
  
    -   **Opis:** Wprowadź opis reguły zgodności.  
  
    -   **Wybrane ustawienie:** Kliknij przycisk **Przeglądaj** otworzyć **wybierz ustawienie** okno dialogowe. Wybierz ustawienie, dla którego chcesz zdefiniować regułę, lub kliknij pozycję **Nowe ustawienie**. Po zakończeniu kliknij pozycję **Wybierz**.  
  
        > [!TIP]  
        >  Możesz również kliknąć pozycję **Właściwości**, aby wyświetlić informacje dotyczące aktualnie wybranego ustawienia.  
  
    -   **Typ reguły:** Wybierz typ reguły zgodności, którego chcesz użyć:  
  
        -   **Wartość:** Utwórz regułę porównującą wartość zwróconą przez element konfiguracji z określonej wartości.  
  
        -   **Egzystencjalna** — tworzy regułę, która ocenia ustawienie w zależności od tego, czy istnieje na urządzeniu.  
  
    -   Dla reguły typu **Wartość** podaj następujące informacje:  
  
        -   Ustawienie musi być zgodne z następującą regułą — wybierz operator i wartość, która zostanie oceniona pod kątem zgodności z wybranym ustawieniem. Możesz użyć następujących operatorów:  
  
            -   **Equals**  
  
            -   **Nie równa się**  
  
            -   **Większa niż**  
  
            -   **Mniej niż**  
  
            -   **Między**  
  
            -   **Większe lub równe**  
  
            -   **Mniejsze niż lub równe**  
  
            -   **Jedno z** — w polu tekstowym określ jedną pozycję w każdym wierszu.  
  
            -   **Żadne z** — w polu tekstowym określ jedną pozycję w każdym wierszu.  
  
        -   **Koryguj niezgodne reguły, jeśli są obsługiwane** — wybierz tę opcję, jeśli program Configuration Manager ma automatycznie korygować niezgodne reguły.  
  
            > [!IMPORTANT]  
            >  Możesz korygować niezgodne reguły tylko wtedy, gdy operator reguły to **Równa się**.  
  
        -   **Zgłaszaj brak zgodności, jeśli wystąpienie tego ustawienia nie zostanie odnalezione** — element konfiguracji zgłasza niezgodność, jeśli to ustawienie nie zostanie znalezione na komputerze Mac.  
  
    -   **Ważność niezgodności raportów** — określ poziom ważności zgłaszany w przypadku wykrycia niezgodności przez regułę. Poniżej przedstawiono dostępne poziomy ważności:  
  
        -   **Brak** — komputery, które nie spełniają tej zasady zgodności nie będą zgłaszać ważności niepowodzenia dla raportów programu Configuration Manager.  
  
        -   **Informacje o** -komputerów, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **informacji** dla raportów programu Configuration Manager.  
  
        -   **Ostrzeżenie** -komputerów, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **ostrzeżenie** dla raportów programu Configuration Manager.  
  
        -   **Krytyczne** -komputerów, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczne** dla raportów programu Configuration Manager.  
  
        -   **Krytyczne ze zdarzeniem** -komputerów, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczne** dla raportów programu Configuration Manager. Ten poziom ważności jest również rejestrowany przez komputer kliencki Mac.  
  
    -   Dla typu reguły **Egzystencjalna** podaj następujące informacje:  
  
        -   Wybierz jedną z opcji:  
  
            -   **Ustawienie musi istnieć na urządzeniach klienckich**  
  
            -   **Ustawienie nie może istnieć na urządzeniach klienckich**  
  
        -   **Waga niezgodności do raportów:** Określ poziom ważności zgłaszany w przypadku niepowodzenia reguły niezgodności. Poniżej przedstawiono dostępne poziomy ważności:  
  
            -   **Brak** — komputery, które nie spełniają tej zasady zgodności nie będą zgłaszać ważności niepowodzenia dla raportów programu Configuration Manager.  
  
            -   **Informacje o** -komputerów, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **informacji** dla raportów programu Configuration Manager.  
  
            -   **Ostrzeżenie** -komputerów, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **ostrzeżenie** dla raportów programu Configuration Manager.  
  
            -   **Krytyczne** -komputerów, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczne** dla raportów programu Configuration Manager.  
  
            -   **Krytyczne ze zdarzeniem** -komputerów, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczne** dla raportów programu Configuration Manager. Ten poziom ważności jest również rejestrowany przez komputer kliencki Mac.  
  
        > [!NOTE]  
        >  Wyświetlone opcje mogą różnić się w zależności od typu ustawienia, dla którego jest konfigurowana reguła.  
  
    -   Kliknij przycisk **OK**, aby zamknąć okno dialogowe **Tworzenie reguły**.  
  
15. Na stronie **Podsumowanie** potwierdź ustawienia nowego elementu konfiguracji, a następnie zakończ pracę kreatora.  
  
 Nowy element konfiguracji jest wyświetlany w węźle **Elementy konfiguracji** w obszarze roboczym **Zasoby i zgodność**.  
  
 Jeśli chcesz teraz dodać ten element konfiguracji do linii bazowej konfiguracji, zobacz [Tworzenie linii bazowych konfiguracji w programie System Center Configuration Manager](../../compliance/deploy-use/create-configuration-baselines.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy konfiguracji dla urządzeń zarządzanych za pomocą klienta programu System Center Configuration Manager](../../compliance/deploy-use/configuration-items-for-devices-managed-with-the-client.md)
