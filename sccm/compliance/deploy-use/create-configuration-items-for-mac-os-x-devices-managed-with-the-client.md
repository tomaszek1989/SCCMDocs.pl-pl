---
title: "Tworzenie elementów konfiguracji dla zarządzanych przez klienta Mac - programu Configuration Manager | Dokumentacja firmy Microsoft"
description: "Element konfiguracji programu System Center Configuration Manager Mac OS X umożliwia zarządzanie ustawieniami dla urządzeń z systemem Mac OS X."
ms.custom: na
ms.date: 03/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 722d5bf5-bedc-4dfc-b324-6eeb773874e9
caps.latest.revision: 8
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 541e5ad629a9e2ed9c353dff150f9b86b9d12b7d
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-create-configuration-items-for-mac-os-x-devices-managed-with-the-system-center-configuration-manager-client"></a>Tworzenie elementów konfiguracji dla urządzeń z systemem Mac OS X zarządzanych za pomocą klienta programu System Center Configuration Manager
Użyj programu System Center Configuration Manager**systemu Mac OS X (niestandardowy)** elementu konfiguracji do zarządzania ustawieniami urządzenia systemu Mac OS X, które są zarządzane przez klienta programu Configuration Manager.  
  
 System operacyjny Mac OS X używa plików listy właściwości (plików plist) do przechowywania ustawień aplikacji. Użyj ustawień zgodności, aby ocenić i skorygować ustawienia w pliku listy właściwości. Ustawieniami systemu Mac OS X możesz także zarządzać za pomocą skryptu powłoki zwracającego wartość, którą można ocenić i skorygować w celu zachowania zgodności.  
  
### <a name="to-create-a-custom-mac-os-x-configuration-item"></a>Tworzenie niestandardowego elementu konfiguracji systemu Mac OS X  
  
1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność**.  
  
2.  W obszarze roboczym **Zasoby i zgodność** rozwiń węzeł **Ustawienia zgodności**, a następnie kliknij pozycję **Elementy konfiguracji**.  
  
3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij pozycję **Utwórz element konfiguracji**.  
  
4.  Na stronie **Ogólne** w **Kreatorze tworzenia elementu konfiguracji** podaj nazwę i opcjonalny opis elementu konfiguracji.  
  
5.  W obszarze **Określ typ elementu konfiguracji, który chcesz utworzyć** wybierz pozycję **Mac OS X (niestandardowy)**.  
  
6.  Kliknij przycisk **kategorii** należy utworzyć i przypisać kategorie ułatwiają wyszukiwanie i filtrowanie elementów konfiguracji w konsoli programu Configuration Manager.  
  
7.  Na stronie **Obsługiwane platformy** kreatora wybierz wersje systemu Mac OS X, które będą oceniać element konfiguracji.  
  
8.  Na stronie **Ustawienia** kreatora dodasz nowe ustawienia, które będą oceniane pod kątem zgodności na komputerach Mac. Kliknij pozycję **Nowy**, aby otworzyć okno dialogowe **Tworzenie ustawienia**.  
  
9. W oknie dialogowym **Tworzenie ustawienia** podaj unikatową nazwę i opis ustawienia.  
  
10. Wybierz wartość dla pozycji **Typ ustawienia**, a następnie podaj wymagane informacje przedstawione w poniższej tabeli:  
  
    -   **Mac OS X preferencje** -  
  
        -   **Identyfikator aplikacji** — określ identyfikator aplikacji dla pliku listy właściwości zawierającego klucz, który chcesz ocenić pod kątem zgodności.  
  
             Na przykład jeśli chcesz zmienić ustawienia przeglądarki sieci Web Safari, możesz użyć identyfikatora **com.apple.Safari.plist**.  
  
        -   **Klucz** — określ nazwę klucza, który chcesz ocenić pod kątem zgodności na komputerach Mac. Użyj następującej składni: */<słownik\>/<nazwa klucza\>*.  
  
            > [!IMPORTANT]  
            >  W nazwie klucza uwzględniana jest wielkość liter. Nazwa ta nie zostanie oceniona, jeśli będzie różnić się od nazwy klucza na komputerze Mac. Nie można także edytować nazwy klucza po jej określeniu. Jeśli chcesz zmienić nazwę klucza, usuń ustawienie i utwórz je ponownie.  
  
    -   **Skrypt** -  
  
        -   **Skrypt wykrywania** — kliknij polecenie **Dodaj skrypt**, a następnie podaj skrypt powłoki, aby ocenić ustawienia na komputerze Mac pod kątem zgodności. Użyj **echo** polecenia skryptu powłoki do zwracania wartości do programu Configuration Manager dla zgodności. Program Configuration Manager używa wyników zwróconych w **STDOUT** do oceny zgodności.  
  
            > [!IMPORTANT]  
            >  W skrypcie odnajdywania nie można umieścić polecenia **reboot**. Ponieważ skrypty odnajdywania są uruchamiane przy każdym ponownym uruchomieniu klienta, spowodowałoby to ciągłe ponowne uruchamianie komputera Mac.  
  
        -   **Skrypt korygujący (opcjonalny)** — opcjonalnie kliknij polecenie **Dodaj skrypt**, a następnie podaj skrypt powłoki, który służy do korygowania wszelkich niezgodnych ustawień znalezionych na komputerach klienckich Mac.  
  
            > [!IMPORTANT]  
            >  W celu zapewnienia, że w skrypcie nie znajdą się żadne znaki formatujące, których komputer Mac nie może zinterpretować, nie używaj funkcji kopiowania i wklejania, lecz wpisz skrypt.  
  
11. Wybierz wartość dla pozycji **Typ danych**, tzn. format danych zwracanych przez warunek, zanim zostaną one użyte do oceny ustawienia.  
  
    > [!NOTE]  
    >  Typ danych **Liczba zmiennoprzecinkowa** obsługuje tylko 3 cyfry po przecinku.  
    >   
    >  Menedżer konfiguracji nie obsługuje korzystania **Boolean** ustawieniach skryptu elementu konfiguracji Mac — typ danych. Zamiast tego należy ustawić typ danych na wartość **Liczba całkowita** i upewnić się, że skrypt zwraca liczbę całkowitą.  
  
12. Kliknij przycisk **OK**, aby zapisać ustawienia i zamknąć okno dialogowe **Tworzenie ustawienia**, a następnie dodaj tyle ustawień, ile potrzebujesz.  
  
13. Na stronie **Reguły zgodności** kreatora określisz warunki, które definiują zgodność elementu konfiguracji. Zanim będzie można ocenić ustawienie pod kątem zgodności, musi istnieć co najmniej jedna reguła zgodności. Kliknij pozycję **Nowa**, aby dodać nową regułę.  
  
14. W oknie dialogowym **Tworzenie reguły** podaj następujące informacje:  
  
    -   **Nazwa:** Wprowadź nazwę zasady zgodności.  
  
    -   **Opis:** Wprowadź opis zasady zgodności.  
  
    -   **Wybrane ustawienie:** Kliknij przycisk **Przeglądaj** otworzyć **wybierz ustawienie** okno dialogowe. Wybierz ustawienie, dla którego chcesz zdefiniować regułę, lub kliknij pozycję **Nowe ustawienie**. Po zakończeniu kliknij pozycję **Wybierz**.  
  
        > [!TIP]  
        >  Możesz również kliknąć pozycję **Właściwości**, aby wyświetlić informacje dotyczące aktualnie wybranego ustawienia.  
  
    -   **Typ reguły:** Wybierz typ zasady zgodności, którego chcesz używać:  
  
        -   **Wartość:** Utwórz regułę, która porównuje wartości zwracanej przez element konfiguracji względem wartości, który określisz.  
  
        -   **Egzystencjalna** — tworzy regułę, która ocenia ustawienie w zależności od tego, czy istnieje na urządzeniu.  
  
    -   Dla reguły typu **Wartość** podaj następujące informacje:  
  
        -   Ustawienie musi być zgodne z następującą regułą — wybierz operator i wartość, która zostanie oceniona pod kątem zgodności z wybranym ustawieniem. Możesz użyć następujących operatorów:  
  
            -   **Równa się**  
  
            -   **Nie równa się**  
  
            -   **Większe niż**  
  
            -   **Mniej niż**  
  
            -   **Między**  
  
            -   **Większe niż lub równe**  
  
            -   **Mniejsze niż lub równe**  
  
            -   **Jedno z** — w polu tekstowym określ jedną pozycję w każdym wierszu.  
  
            -   **Żadne z** — w polu tekstowym określ jedną pozycję w każdym wierszu.  
  
        -   **Koryguj niezgodne reguły, jeśli są obsługiwane** — wybierz tę opcję, jeśli program Configuration Manager ma automatycznie korygować niezgodne reguły.  
  
            > [!IMPORTANT]  
            >  Możesz korygować niezgodne reguły tylko wtedy, gdy operator reguły to **Równa się**.  
  
        -   **Zgłaszaj brak zgodności, jeśli wystąpienie tego ustawienia nie zostanie odnalezione** — element konfiguracji zgłasza niezgodność, jeśli to ustawienie nie zostanie znalezione na komputerze Mac.  
  
    -   **Ważność niezgodności raportów** — określ poziom ważności zgłaszany w przypadku wykrycia niezgodności przez regułę. Poniżej przedstawiono dostępne poziomy ważności:  
  
        -   **Brak** -komputerów, które nie spełniają tej zasady zgodności, będą zgłaszać ważności niepowodzenia dla raportów programu Configuration Manager.  
  
        -   **Informacje o** -komputerów, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **informacji** dla raportów programu Configuration Manager.  
  
        -   **Ostrzeżenie** -komputerów, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **ostrzeżenie** dla raportów programu Configuration Manager.  
  
        -   **Krytyczne** -komputerów, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczny** dla raportów programu Configuration Manager.  
  
        -   **Krytyczne ze zdarzeniem** -komputerów, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczny** dla raportów programu Configuration Manager. Ten poziom ważności jest również rejestrowany przez komputer kliencki Mac.  
  
    -   Dla typu reguły **Egzystencjalna** podaj następujące informacje:  
  
        -   Wybierz jedną z opcji:  
  
            -   **Ustawienie musi istnieć na urządzeniach klienckich**  
  
            -   **Ustawienie nie może istnieć na urządzeniach klienckich**  
  
        -   **Waga niezgodności raportów:** Określ poziom ważności, który jest zgłaszany w przypadku tej zasady zgodności zakończy się niepowodzeniem. Poniżej przedstawiono dostępne poziomy ważności:  
  
            -   **Brak** -komputerów, które nie spełniają tej zasady zgodności, będą zgłaszać ważności niepowodzenia dla raportów programu Configuration Manager.  
  
            -   **Informacje o** -komputerów, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **informacji** dla raportów programu Configuration Manager.  
  
            -   **Ostrzeżenie** -komputerów, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **ostrzeżenie** dla raportów programu Configuration Manager.  
  
            -   **Krytyczne** -komputerów, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczny** dla raportów programu Configuration Manager.  
  
            -   **Krytyczne ze zdarzeniem** -komputerów, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczny** dla raportów programu Configuration Manager. Ten poziom ważności jest również rejestrowany przez komputer kliencki Mac.  
  
        > [!NOTE]  
        >  Wyświetlone opcje mogą różnić się w zależności od typu ustawienia, dla którego jest konfigurowana reguła.  
  
    -   Kliknij przycisk **OK**, aby zamknąć okno dialogowe **Tworzenie reguły**.  
  
15. Na stronie **Podsumowanie** potwierdź ustawienia nowego elementu konfiguracji, a następnie zakończ pracę kreatora.  
  
 Nowy element konfiguracji jest wyświetlany w węźle **Elementy konfiguracji** w obszarze roboczym **Zasoby i zgodność**.  
  
 Jeśli chcesz teraz dodać ten element konfiguracji do linii bazowej konfiguracji, zobacz [Tworzenie linii bazowych konfiguracji w programie System Center Configuration Manager](../../compliance/deploy-use/create-configuration-baselines.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Elementy konfiguracji dla urządzeń zarządzanych za pomocą klienta programu System Center Configuration Manager](../../compliance/deploy-use/configuration-items-for-devices-managed-with-the-client.md)

