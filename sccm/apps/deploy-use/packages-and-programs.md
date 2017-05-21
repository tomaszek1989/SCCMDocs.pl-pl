---
title: Pakiety i programy | Dokumentacja firmy Microsoft
description: "Obsługuje wdrożenia z wykorzystaniem pakietów i programów lub aplikacji z System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: caad0507-9913-415a-b13d-d36f8f0a1b80
caps.latest.revision: 8
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6c5b23270501c11ed5aba9a6045734c73095d1bf
ms.openlocfilehash: 6146bcf4e5aa9df6fe0b8cf71898e488ecf217cc
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="packages-and-programs-in-system-center-configuration-manager"></a>Pakiety i programy w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

System Center Configuration Manager nadal obsługuje pakiety i programy, które były używane w programie Configuration Manager 2007. Wdrożenie korzystające z pakietów i programów może być odpowiedniejsze od wdrożenia korzystającego z aplikacji, gdy wdraża się poniższe elementy:  

- Aplikacje na serwerach z systemem Linux i UNIX
- Skrypty nieinstalujące aplikacji na komputerze, na przykład skrypt defragmentacji dysku komputera.
- „Jednorazowe” skrypty, które nie muszą być stale monitorowane.  
- Skrypty uruchamiane zgodnie z cyklicznym harmonogramem, które nie mogą korzystać z globalnej ewaluacji.

W przypadku migracji pakietów z wcześniejszej wersji programu Configuration Manager, można je wdrożyć w hierarchii programu Configuration Manager. Po zakończeniu migracji pakiety są widoczne w węźle **Pakiety** w obszarze roboczym **Biblioteka oprogramowania**.

Można modyfikować i wdrażać te pakiety w taki sam sposób jak przy użyciu dystrybucji oprogramowania. **Importuj pakiet w Kreatorze definicji** pozostaje w programie Configuration Manager do importowania pakietów starszej wersji. Anonse są konwertowane na wdrożenia podczas migracji z programu Configuration Manager 2007 do hierarchii programu Configuration Manager.  

> [!NOTE]  
>  Do konwersji pakietów i programów do aplikacji programu Configuration Manager, można użyć Menedżera konwersji pakietu Microsoft System Center Configuration Manager.  
>   
>  Aby uzyskać więcej informacji, zobacz [Configuration Manager Package Conversion Manager](https://technet.microsoft.com/library/hh531519.aspx).  

Pakiety można użyć nowe funkcje programu Configuration Manager, łącznie z grupami punktów dystrybucji i monitorowania. Nie można dystrybuować aplikacji Microsoft Application Virtualization (App-V) przy użyciu pakietów i programów w programie Configuration Manager. Do rozsyłania aplikacji wirtualnej, należy utworzyć je jako aplikacji programu Configuration Manager.  

##  <a name="create-a-package-and-program"></a>Tworzenie pakietu i programu  
 Użyj jednej z tych procedur ułatwiających tworzenie lub importowanie pakietów i programów.  

### <a name="create-a-package-and-program-using-the-create-package-and-program-wizard"></a>Tworzenie pakietu i programu za pomocą Kreatora tworzenia pakietu i programu.  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **zarządzania aplikacjami** > **pakiety**.  

3.  W **Home** w karcie **Utwórz** grupy, wybierz **Tworzenie pakietu**.  

4.  Na **pakietu** strony **Kreatora tworzenia pakietu i programu**, podaj następujące informacje:  

    -   **Nazwa**: Określ nazwę pakietu z maksymalnie 50 znaków.  

    -   **Opis**: Określ opis dla tego pakietu z maksymalnie 128 znaków.  

    -   **Producent** (opcjonalnie): Określ nazwę producenta, aby pomóc w zidentyfikowaniu pakiet w konsoli programu Configuration Manager. Ta nazwa może się składać z maksymalnie 32 znaków.

    -   **Język** (opcjonalnie): Określ wersję językową pakietu o maksymalnej długości 32 znaków.  

    -   **Wersja** (opcjonalnie):  Określ numer wersji pakietu o maksymalnej długości 32 znaków.

    -   **Ten pakiet zawiera pliki źródłowe**: To ustawienie wskazuje, czy pakiet wymaga pliki źródłowe do znajdować się na urządzeniach klienckich. Domyślnie to pole wyboru jest zaznaczone, a Menedżer konfiguracji nie używa punktów dystrybucji pakietu. Gdy to pole wyboru jest zaznaczone, punkty dystrybucji są używane.  

    -   **Folder źródłowy**: Jeżeli pakiet zawiera pliki źródłowe, wybierz **Przeglądaj** otworzyć **Ustaw Folder źródłowy** okna dialogowego, a następnie wskaż lokalizację plików źródłowych pakietu.  

        > [!NOTE]  
        >  Konto komputera serwera lokacji musi mieć uprawnienia dostępu Odczyt we wskazanym folderze źródłowym.  

5.  Na **typu programu** strony **Kreatora tworzenia pakietu i programu**, wybierz typ programu do tworzenia, a następnie wybierz **dalej**. Można utworzyć program dla komputera lub urządzenia albo pominąć ten krok i utworzyć program później.  

    > [!TIP]  
    >  Aby utworzyć nowy program dla istniejącego pakietu, należy najpierw zaznaczyć pakietu. Następnie w **Home** w karcie **pakietu** grupy, wybierz **utworzyć Program** otworzyć **Kreatora tworzenia programu**.  

6.  Użyj jednej z następujących procedur, aby utworzyć program standardowy lub program urządzenia.  

    #### <a name="create-a-standard-program"></a>Tworzenie standardowego programu  

  1.  Na **typu programu** strony **Kreatora tworzenia pakietu i programu**, wybierz **standardowego programu**, a następnie wybierz **dalej**.     

    2.  Na **standardowego programu** określ następujące informacje:  

        -   **Nazwa:** Określ nazwę programu z maksymalnie 50 znaków.  

            > [!NOTE]  
            >  Nazwa programu musi być unikatowa w ramach pakietu. Po utworzeniu programu nie można zmodyfikować jego nazwy.  

        -   **Wiersz polecenia**: Wprowadź wiersza polecenia do uruchamiania tego programu lub wybierz **Przeglądaj** przejdź do lokalizacji pliku.  

            Jeśli nazwa pliku nie ma rozszerzenia, które jest określony, program Configuration Manager próbuje użyć .com, .exe i .bat jako możliwe rozszerzenia.  

             Gdy program jest uruchamiany na komputerze klienckim, program Configuration Manager najpierw szuka nazwę wiersza polecenia pliku w pakiecie wyszukiwania obok w lokalnym folderze systemu Windows i wyszukuje w lokalnej *% path %*. Jeśli pliku nie uda się znaleźć, działanie programu zakończy się niepowodzeniem.  

        -   **Folder początkowy** (opcjonalnie): Określ folder, z którego program działa, maksymalnie 127 znaków. Ten folder może być ścieżką bezwzględną na kliencie lub ścieżką względną do folderu punktu dystrybucji, który zawiera pakiet.

        -   **Uruchom**: Określ tryb wykonywania programu na komputerach klienckich. Wybierz jedną z poniższych opcji:  

            -   **Normalny**: Program jest uruchamiany w trybie normalnym na podstawie ustawień domyślnych systemu i programu. Jest to tryb domyślny.  

            -   **Zminimalizowane**: Program jest uruchamiany w trybie zminimalizowanym na urządzeniach klienckich. Użytkownicy mogą widzieć działania instalacyjne w obszarze powiadomień lub na pasku zadań.  

            -   **Zmaksymalizowane**: Program jest uruchamiany w trybie zmaksymalizowanym na urządzeniach klienckich. Użytkownicy widzą wszystkie działania instalacyjne.  

            -   **Ukryte**: Program uruchamiany ukryte na urządzeniach klienckich. Użytkownicy nie będą widzieli żadnych działań instalacyjnych.  

        -   **Program można uruchomić**: Określ, czy program ma być uruchamiany tylko wtedy, gdy użytkownik jest zalogowany, tylko wtedy, gdy żaden użytkownik nie jest podpisany w lub niezależnie od tego, czy użytkownik jest zalogowany na komputerze klienckim.  

        -   **Tryb uruchamiania**: Określ, czy program ma być uruchamiany z uprawnieniami administracyjnymi lub z uprawnieniami użytkownika, który jest obecnie zalogowany.  

        -   **Zezwalaj użytkownikom na wyświetlanie i interakcję z instalacji programu**: Użyj tego ustawienia, jeśli jest dostępne określić, czy zezwalać użytkownikom na interakcję z instalacji programu. To pole wyboru jest dostępne tylko wtedy, gdy **tylko, gdy żaden użytkownik nie jest zalogowany** lub **, czy użytkownik jest zalogowany** został wybrany do **Program można uruchomić** i kiedy **Uruchom z prawami administracyjnymi** został wybrany do **tryb uruchamiania**.  

        -   **Tryb dysku**: Określ informacje dotyczące działania tego programu w sieci. Wybierz jedną z następujących opcji:  

            -   **Jest uruchamiany z nazwą UNC**: Określ, czy program jest uruchamiany z nazwą Universal Naming Convention (UNC). To jest ustawienie domyślne.  

            -   **Wymaga litery dysku**: Określ, czy program wymaga literę dysku do pełnej kwalifikacji jego lokalizacji. Dla tego ustawienia programu Configuration Manager można użyć dowolnej litery dysku na komputerze klienckim.  

            -   **Wymaga określonej litery dysku** : Określ, czy program wymaga określonej litery dysku przez użytkownika do pełnej kwalifikacji lokalizacji (na przykład **Z:**). Jeśli określona litera dysku będzie już używana na kliencie, program nie zostanie uruchomiony.  

        -   **Połącz ponownie do punktu dystrybucji w dzienniku na**: To pole wyboru służy do wskazania, czy komputer kliencki ponownie nawiąże połączenie z punktem dystrybucji podczas logowania użytkownika. To pole wyboru jest domyślnie wyczyszczone.  

  3.  Na **wymagania** strony **Program kreatora tworzenia pakietu i** Podaj następujące informacje:  

        -   **Uruchom najpierw inny program**: To ustawienie umożliwia określenie pakiet i program uruchamiany przed uruchomieniem tego pakietu i programu.  

        -   **Wymagania dotyczące platformy**: Wybierz **ten program można uruchomić na dowolnej platformie** lub **ten program można uruchomić tylko na określonych platformach**, a następnie wybierz systemy operacyjne, klienci muszą być uruchomione, aby można było zainstalować pakiet i program.  

        -   **Szacowane miejsce na dysku**: Określ ilość miejsca na dysku przez oprogramowanie wymaga do uruchomienia na komputerze. Dla tego ustawienia można wybrać opcję **Unknown** (ustawienie domyślne) lub ustawić liczbę całkowitą nie mniejszą od zera. Jeśli zostanie podana wartość, należy wskazać dla niej jednostkę.  

        -   **Maksymalny dozwolony czas wykonywania (w minutach)**: Określ maksymalny czas program jest uruchamiany na komputerze klienckim. Dla tego ustawienia można wybrać opcję **Unknown** (ustawienie domyślne) lub ustawić liczbę całkowitą większą od zera.  

             Wartością domyślną jest 120 minut.  

            > [!IMPORTANT]  
            >  Jeśli używasz okna obsługi dla kolekcji, na którym ten program jest uruchomiony, może wystąpić konflikt, jeśli **maksymalny dozwolony czas wykonywania** jest większa od czasu zaplanowanego okna obsługi. Jednak jeśli maksymalny czas wykonywania ustawiono **nieznany**, program zaczyna działać podczas okna obsługi i kontynuuje działanie w razie potrzeby po zamknięciu okna obsługi. Jeżeli użytkownik ustawi maksymalnego czasu działania określonego okresu przekracza długość dowolnej z dostępnych okien obsługi, program nie działa.  

             Jeśli wartość jest równa **nieznany**, Configuration Manager Ustawia maksymalny dozwolony czas wykonywania jako 12 godzin (720 minut).  

            > [!NOTE]  
            >  Po przekroczeniu maksymalnego czasu (ustawionego przez użytkownika lub jako wartość domyślna) wykonywania programu Configuration Manager zatrzymuje program, jeśli **Uruchom z prawami administracyjnymi** jest zaznaczone i **Zezwalaj użytkownikom na wyświetlanie i interakcję z instalacji programu** nie jest zaznaczone.  

  4.  Wybierz **dalej**.  

    #### <a name="create-a-device-program"></a>Tworzenie programu urządzenia  

  1.  Na **typ programu** strony **Kreatora tworzenia pakietu i programu**, wybierz opcję **programu dla urządzenia**, a następnie wybierz **dalej**.  

  2.  Na **programu dla urządzenia** strony, podaj następujące informacje:  

        -   **Nazwa**: Określ nazwę programu z maksymalnie 50 znaków.  

            > [!NOTE]  
            >  Nazwa programu musi być unikatowa w ramach pakietu. Po utworzeniu programu nie można zmodyfikować jego nazwy.  

        -   **Komentarz** (opcjonalnie): Określ komentarz dotyczący tego programu urządzenia z maksymalnie 127 znaków.  

        -   **Pobierz folder**: Podaj nazwę folderu na urządzeniu Windows CE, w którym będą przechowywane pliki źródłowe pakietu. Wartość domyślna to **\Temp\\\**.  

        -   **Wiersz polecenia**: Wprowadź wiersza polecenia do uruchamiania tego programu lub wybierz **Przeglądaj** przejdź do lokalizacji pliku.  

        -   **Uruchom wiersz polecenia w folderze pobierania**: Wybierz tę opcję, aby uruchomić program z folderu wcześniej pobierania.  

        -   **Uruchom wiersz polecenia z tego folderu**: Wybierz tę opcję, aby określić inny folder, z którym ma być uruchamiany program.  

    3.  Na **wymagania** strony, podaj następujące informacje:  

        -   **Szacowane miejsce na dysku**: Określ ilość miejsca na dysku wymaganego oprogramowania. To jest wyświetlana dla użytkowników urządzeń przenośnych, przed zainstalowaniem programu.  

        -   **Pobierz program**: Określ informacje dotyczące gdy można pobrać ten program na urządzeniach przenośnych. Do wyboru są następujące opcje: **Jak najszybciej**, **Tylko przez szybką sieć** i **Tylko gdy urządzenie jest zadokowane**.  

        -   **Dodatkowe wymagania**: Określ wszelkie dodatkowe wymagania dla tego programu. Są one widoczne dla użytkowników przed zainstalowaniem oprogramowania. Na przykład można powiadamiać użytkowników, że przed uruchomieniem tego programu trzeba zamknąć wszystkie inne aplikacje.  

  4.  Wybierz **dalej**.  

  7.  Na **Podsumowanie** Przejrzyj akcje, które zostaną wykonane, a następnie Zakończ pracę kreatora.  

 Sprawdź, czy nowy pakiet i program są wyświetlane w **pakiety** węzła **Biblioteka oprogramowania** obszaru roboczego.  

## <a name="create-a-package-and-program-from-a-package-definition-file"></a>Tworzenie pakietu i programu na podstawie pliku definicji pakietu  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **zarządzania aplikacjami** > **pakiety**.  

3.  Na **Home** w karcie **Utwórz** grupy, wybierz **Utwórz pakiet z definicji**.  

4.  Na **definicji pakietu** strony **Utwórz pakiet z definicji kreatora**, wybierz istniejący plik definicji pakietu lub **Przeglądaj** do otwierania pliku definicji pakietu. Po określeniu pliku definicji pakietu, wybierz go z **pakiet definicji** , a następnie wybierz **dalej**.  

5.  Na **pliki źródłowe** strony, podaj informacje o wszelkie pliki źródłowe wymagane przez pakiet i program, a następnie wybierz **dalej**.  

6.  Jeśli pakiet wymaga plików źródłowych na **Folder źródłowy** Określ lokalizację, z której pliki źródłowe mają można uzyskać, a następnie wybierz **dalej**.  

7.  Na **Podsumowanie** Przejrzyj akcje, które zostaną wykonane, a następnie Zakończ pracę kreatora. Nowy pakiet i program są wyświetlane w **pakiety** węzła **Biblioteka oprogramowania** obszaru roboczego.  

 Aby uzyskać więcej informacji na temat plików definicji pakietu, zobacz [o formacie pliku definicji pakietu](/sccm/apps/deploy-use/packages-and-programs#about-the-package-definition-file-format) w tym temacie.  

##  <a name="deploy-packages-and-programs"></a>Wdrażanie pakietów i programów  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **zarządzania aplikacjami** > **pakiety**.  

2.  Wybierz pakiet, który chcesz wdrożyć, a następnie w **Home** karcie w **wdrożenia** grupy, wybierz **Wdróż**.  

3.  Na **ogólne** strony **Kreatora wdrażania oprogramowania**, określ nazwę pakietu i programu chcesz wdrożyć kolekcji, do której chcesz wdrożyć pakiet i program i opcjonalne komentarze dla wdrożenia.  

     Wybierz opcję **Użyj domyślnych grup punktów dystrybucji powiązanych z tą kolekcją**, jeśli chcesz umieścić zawartość pakietu w domyślnej grupie punktów dystrybucji kolekcji. Jeśli wybrana Kolekcja nie skojarzono z grupą punktów dystrybucji, ta opcja jest niedostępna.  

4.  Na **zawartości** wybierz **Dodaj**, a następnie wybierz punkty dystrybucji lub grupy punktów dystrybucji, do których chcesz wdrożyć zawartość, która jest skojarzona z tym pakietem i programem.  

5.  Na **ustawienia wdrażania** strony, wybierz cel dla tego wdrożenia i określ opcje dla pakietów wznawiania i mierzonych połączeń:  

    -   **Cel**: Wybierz spośród opcji:  

        -   **Dostępne**: Jeśli aplikacja jest wdrażana dla użytkownika, użytkownik będzie widział opublikowany pakiet i program w katalogu aplikacji i może ją na żądanie. Jeśli pakiet i program jest wdrażana na urządzeniu, użytkownik będzie ją widział w Centrum oprogramowania i można ją zainstalować na żądanie.  

        -   **Wymagane**: Pakiet i program zostanie wdrożona automatycznie zgodnie ze skonfigurowanym harmonogramem. Użytkownik może jednak śledzić stan wdrożenia pakietu i programu oraz zainstalować je przed upływem ostatecznego terminu przy użyciu Centrum oprogramowania.  

    -   **Wyślij pakiety wzbudzania**: Jeśli w celu wdrożenia wybrano opcję **wymagane** i wybrano tę opcję, przed zainstalowaniem wdrożenia do wznowienia w ostatecznym terminie instalacji do komputerów zostanie wysłany pakiet wznawiania. Aby użyć tej opcji, należy skonfigurować komputery do używania funkcji Wake On LAN.  

    -  **Zezwalaj klientom mierzonego połączenia internetowego na pobieranie zawartości po upływie ostatecznego terminu instalacji, co może pociągnąć za sobą dodatkowe koszty**: Wybierz, jeśli są wymagane.  

    > [!NOTE]  
    >  Opcja **Wykonaj wstępne wdrożenie oprogramowania na główne urządzenie użytkownika** nie jest dostępna podczas wdrażania pakietów i programów.  

6.  Na **Planowanie** skonfiguruj, czy ten pakiet i program zostanie wdrożone lub udostępnione na urządzeniach klienckich.  

     Opcje na tej stronie są różne, w zależności od tego, czy ustawiono akcję wdrożenia **dostępne** lub **wymagane**.  

7.  Jeśli w celu wdrożenia wybrano opcję **wymagane**, skonfigurować zachowanie ponownie uruchom program z **zachowanie ponownego uruchamiania** menu rozwijanego. Wybierz jedną z następujących opcji:  

    |Zachowanie ponownego uruchamiania|Więcej informacji|  
    |--------------------|----------------------|  
    |Nigdy nie uruchamiaj ponownie wdrożonego programu|Program nie będzie można ponownie uruchomić na kliencie, nawet jeśli program pierwotnie nie powiodła się lub zostały zmienione pliki programu.|  
    |Zawsze uruchamiaj ponownie program|Program będzie zawsze uruchamiana ponownie na kliencie podczas planowania wdrożenia, nawet jeśli program został uruchomiony pomyślnie. Może to być przydatne w przypadku używania wdrożeń cyklicznych, w ramach których program jest aktualizowany, na przykład o oprogramowanie antywirusowe.|  
    |Uruchom ponownie, jeśli poprzednia próba nie powiodła się|Program zostanie uruchomiona ponownie, gdy wdrożenie jest zaplanowane tylko wtedy, gdy nie można go na Poprzednia próba uruchomienia.|  
    |Uruchom ponownie, jeśli poprzednia próba powiodła się|Program zostanie uruchomiona ponownie tylko wtedy, gdy wcześniej uruchomiony pomyślnie na kliencie. To ustawienie jest przydatne w przypadku używania cyklicznych anonsów, w których program jest cyklicznie aktualizowany, gdy każda aktualizacja wymaga pomyślnego zainstalowania poprzedniej aktualizacji.|  

8. Na stronie **Środowisko użytkownika** określ następujące informacje:  

    -   **Zezwalaj użytkownikom na uruchamianie programu niezależnie od przypisań**: Jeśli włączona, użytkownicy mogą instalować to oprogramowanie z Centrum oprogramowania niezależnie od wszelkich zaplanowany czas instalacji.  

    -   **Instalacja oprogramowania**: Umożliwia zainstalowanie poza oknami obsługi skonfigurowane oprogramowanie.  

    -   **Ponowne uruchomienie systemu (jeśli jest to wymagane do ukończenia instalacji)**: Jeżeli instalacja oprogramowania wymaga ponownego uruchomienia urządzenia w celu zakończenia, pozwala to niepożądane poza skonfigurowanymi oknami obsługi.  

    -   **Urządzenia osadzone**: Podczas wdrażania pakietów i programów na urządzeniach Windows Embedded, które są włączone filtrów zapisu, można określić, pakiety i programy zainstalowania na tymczasowej nakładce i zatwierdzić zmiany później. Alternatywnie zatwierdzasz zmiany w ostatecznym terminie instalacji bądź w oknie obsługi. Po zatwierdzeniu zmian w ostatecznym terminie instalacji bądź w oknie obsługi, wymagane jest ponowne uruchomienie i trwale zapisać zmiany na urządzeniu.  

        > [!NOTE]  
        >  Po wdrożeniu pakietu lub programu na urządzeniu z systemem Windows Embedded upewnij się, że urządzenie należy do kolekcji ze skonfigurowanym oknem obsługi. Aby uzyskać więcej informacji dotyczących sposobu obsługi systemu windows są używane podczas wdrażania pakietów i programów na urządzeniach Windows Embedded, zobacz [tworzenie Windows Embedded aplikacji](../../apps/get-started/creating-windows-embedded-applications.md).  

9. Na stronie **Punkty dystrybucji** określ następujące informacje:  

    -   **Opcje wdrażania**: Określ akcje, które klient powinien wykonać do uruchomienia programu zawartości. Można określić zachowanie klienta znajdującego się w granicach szybkiej sieci lub wolnej bądź zawodnej sieci.  

    -   **Zezwalaj klientom na współużytkowanie zawartości z innymi klientami w tej samej podsieci**: Wybierz tę opcję, aby zmniejszyć obciążenie sieci, zezwalając klientom na pobieranie zawartości z innych klientów w sieci, na których już pobrana zawartość w pamięci podręcznej. Ta opcja korzysta z usługi Windows BranchCache i jest dostępna na komputerach z systemem operacyjnym Windows Vista SP2 lub nowszym.  

    -   **Zezwalaj klientom na użycie rezerwowej lokalizacji źródła zawartości**:  

        -  **W wersji wcześniejszej niż 1610**: Możesz wybrać **Zezwalaj na rezerwową lokalizację źródła zawartości pola wyboru** aby umożliwić klientom spoza granic grup na powrót i używanie dystrybucji jako punktu lokalizacji źródła zawartości podczas inne punkty dystrybucji nie są dostępne.

        - **Wersja 1610 i nowsze**: Nie można skonfigurować **Zezwalaj na rezerwową lokalizację źródła zawartości**.  Zamiast tego należy skonfigurować relacje między grupami granic, które określają, gdy klient można rozpocząć wyszukiwanie grup dodatkowe granic dla lokalizacji prawidłowego źródła zawartości.

10. Na **Podsumowanie** Przejrzyj akcje, które zostaną wykonane, a następnie Zakończ pracę kreatora.  

     Wdrożenia można obejrzeć w węźle **Wdrożenia** obszaru roboczego **Monitorowanie** i w okienku szczegółów na karcie wdrożenia pakietu po wybraniu wdrożenia. Aby uzyskać więcej informacji, zobacz [monitorować pakiety i programy](/sccm/apps/deploy-use/packages-and-programs#monitor-packages-and-programs) w tym temacie.  

> [!IMPORTANT]  
>  Jeśli została skonfigurowana opcja **Uruchom program z punktu dystrybucji** na **punktów dystrybucji** strony **Kreatora wdrażania oprogramowania**, nie należy wyczyścić opcję **skopiuj zawartość tego pakietu do udziału pakietu w punktach dystrybucji** ponieważ sprawia to, że niedostępny uruchamiała się z punktami dystrybucji pakietu.  

##  <a name="monitor-packages-and-programs"></a>Monitor pakietów i programów  
 Aby monitorować wdrożenia pakietów i programów, należy użyć tej samej procedury, które służy do monitorowania aplikacji, jak określono w [monitorowania aplikacji](/sccm/apps/deploy-use/monitor-applications-from-the-console).  

 Pakiety i programy zawiera także szereg wbudowanych raportów, które umożliwiają monitorowanie informacji o stanie wdrożenia pakietów i programów. Te raporty mają kategorię **Dystrybucja oprogramowania — pakiety i programy** oraz **Dystrybucja oprogramowania — stan wdrażania pakietów i programów**.  

 Aby uzyskać więcej informacji o sposobie konfiguracji raportowania w programie Configuration Manager, zobacz [raportowania w programie System Center Configuration Manager](../../core/servers/manage/reporting.md).  

##  <a name="manage-packages-and-programs"></a>Zarządzanie pakietów i programów  
 W **Biblioteka oprogramowania** obszaru roboczego, rozwiń węzeł **zarządzania aplikacjami**, wybierz **pakiety**, wybierz pakiet, który chcesz zarządzać, a następnie wybierz zadanie zarządzania z poniższej tabeli:  

|Zadanie|Więcej informacji|  
|----------|----------------------|  
|**Utwórz wstępnie przygotowany plik zawartości**|Otwiera **Tworzenie kreatora przygotowanego pliku zawartości**, co umożliwia tworzenie pliku zawierającego zawartości pakietu, które mogą być importowane ręcznie do innej lokacji. Przydaje się to, gdy przepustowość sieci między serwerem lokacji i punktem dystrybucji jest mała.|  
|**Tworzenie programów**|Otwiera **Kreatora tworzenia programu**, które umożliwia utworzenie nowego programu dla tego pakietu.|  
|**Eksportowanie**|Otwiera **Kreator eksportu pakietu**, co umożliwia eksportowanie wybranego pakietu i jego zawartość do pliku.<br /><br /> Aby uzyskać informacje o sposobie importowania pakietów i programów, zobacz [tworzenie pakietów i programów](/sccm/apps/deploy-use/packages-and-programs#create-packages-and-programs) w tym temacie.|  
|**Wdrażanie**|Otwiera **Kreatora wdrażania oprogramowania**, co umożliwia wdrażanie wybranych pakietów i programów do kolekcji. Aby uzyskać więcej informacji, zobacz [wdrażania pakietów i programów](/sccm/apps/deploy-use/packages-and-programs#deploy-packages-and-programs) w tym temacie.|  
|**Dystrybuuj zawartość**|Otwiera **kreatora dystrybucji zawartości**, co umożliwia wysyłanie zawartość, która jest skojarzona z pakietu i programu do wybranych punktów dystrybucji lub grupy punktów dystrybucji.|  
|**Aktualizuj punkty dystrybucji**|Aktualizuje punkty dystrybucji o najnowszą zawartość dla wybranego pakietu i programu.|  

##  <a name="about-the-package-definition-file-format"></a>O formacie pliku definicji pakietu  
 Pliki definicji pakietu, które są skrypty można użyć w celu automatyzacji tworzenia pakietów i programów z programu Configuration Manager. Zapewniają one wszystkich danych programu Configuration Manager musi utworzyć pakiet i program, z wyjątkiem lokalizacji plików źródłowych pakietu. Każdy plik definicji pakietu jest plik tekstowy ASCII lub UTF-8 używające formatu pliku .ini i zawiera następujące sekcje:  

###  <a name="pdf"></a>[PDF]  
 W tej sekcji wskazywany jest plik definicji pakietu. Zawiera ona następujące informacje:  

-   **Wersja**: Określ wersję używanego przy użyciu pliku formatu pliku definicji pakietu. Odpowiada to wersję System Management Server (SMS) lub Configuration Manager, dla której został zapisany. Ten wpis jest wymagany.  

###  <a name="package-definition"></a>[Package Definition]  
 Określ właściwości pakietów i programów. Udostępnia ona następujące informacje:  

-   **Nazwa**: Nazwa pakietu maksymalnie 50 znaków.  

-   **Wersja** (opcjonalnie): Wersja pakietu do 32 znaków.  

-   **Ikona** (opcjonalnie): Plik, który zawiera ikonę, aby użyć tego pakietu. Jeśli jest określony, ta ikona zastępuje domyślną ikonę pakietu w konsoli programu Configuration Manager.

-   **Wydawca**: Wydawca pakietu do 32 znaków.

-   **Język**: Wersja językowa pakietu do 32 znaków.

-   **Komentarz** (opcjonalnie): Komentarz dotyczący pakietu do 127 znaków.

-   **ContainsNoFiles**: Ten wpis wskazuje, czy źródło jest skojarzone z pakietem.  

-   **Programy**: Programy, które są zdefiniowane dla tego pakietu. Każda nazwa programu odpowiada sekcji **[Program]** w tym pliku definicji pakietu.  

     Przykład:  

     `Programs=Typical, Custom, Uninstall`  

-   **MIFFileName**: Nazwa pliku formatu MIF (Management Information), który zawiera stan pakietu, maksymalnie 50 znaków.  

-   **MIFName**: Nazwa pakietu (do dopasowania pliku MIF), maksymalnie 50 znaków.  

-   **MIFVersion**: Numer wersji pakietu (do dopasowania pliku MIF), maksymalnie 32 znaki.  

-   **MIFPublisher**: Wydawca oprogramowania pakietu (do dopasowania pliku MIF), maksymalnie 32 znaki.  

###  <a name="program"></a>[Program]  
 Dla każdego programu, który określono w **programy** wpisowi **[Package Definition]** sekcji pliku definicji pakietu musi zawierać sekcję [Program], która definiuje tego programu. Każda sekcja Program zawiera następujące informacje:  

-   **Nazwa**: Nazwa programu, do 50 znaków. Ten wpis musi być unikatowy w ramach pakietu. Ta nazwa jest używana podczas definiowania anonsów. Na komputerach klienckich nazwa programu jest pokazywana w obszarze **Uruchom programy anonsowane** w Panelu sterowania.  

-   **Ikona** (opcjonalnie): Określ plik, który zawiera ikonę dla tego programu. Jeśli określony, ta ikona zastępuje domyślne ikona programu w konsoli programu Configuration Manager i jest wyświetlana na komputerach klienckich, gdy program jest anonsowana.

-   **Komentarz** (opcjonalnie): Komentarz dotyczący programu do 127 znaków.

-   **Wiersz polecenia**: Określ wiersz polecenia dla programu do 127 znaków. To polecenie jest względne wobec folderu źródłowego pakietu.

-   **Uruchamianego**: Określ folder roboczy program do 127 znaków. Ten wpis może być ścieżką bezwzględną na kliencie lub ścieżką względną do folderu źródłowego pakietu.

-   **Uruchom**: Określ tryb programu, w którym działa program. Można określić wartość **Minimized**, **Maximized** lub **Hidden**. Jeśli nie dołączono ten wpis, program jest uruchamiany w trybie normalnym.  

-   **AfterRunning**: Określ specjalnej operacji, który następuje po pomyślnym zakończeniu działania programu. Dostępne opcje to **SMSRestart**, **ProgramRestart** i **SMSLogoff**. Jeśli nie dołączono ten wpis, program nie działa żadnych specjalnych czynności.  

-   **EstimatedDiskSpace**: Określ ilość miejsca na dysku przez oprogramowanie wymaga do uruchomienia na komputerze. Dla tego ustawienia można wybrać opcję **Unknown** (ustawienie domyślne) lub ustawić liczbę całkowitą nie mniejszą od zera. Jeśli zostanie podana wartość, należy wskazać dla niej jednostkę.  

     Przykład:  

     `EstimatedDiskSpace=38MB`  

-   **EstimatedRunTime**: Określ szacowany czas trwania (w minutach) oczekiwanej program do uruchomienia na komputerze klienckim. Dla tego ustawienia można wybrać opcję **Unknown** (ustawienie domyślne) lub ustawić liczbę całkowitą większą od zera.  

     Przykład:  

     `EstimatedRunTime=25`  

-   **SupportedClients**: Określ procesory i systemów operacyjnych, na których jest uruchomiony ten program. Podawane platformy muszą być rozdzielane przecinkami. Jeśli nie dołączono ten wpis, sprawdzania obsługiwanych platform jest wyłączona dla tego programu.  

-   **SupportedClientMinVersionX**, **SupportedClientMaxVersionX**: Określ zakres początkowego do końcowego numery wersji systemów operacyjnych, które są określone w **SupportedClients** wpis.  

     Przykład:  

    ```  
    SupportedClients=Win NT (I386),Win NT (IA64),Win NT (x64)  
    Win NT (I386) MinVersion1=5.00.2195.4  
    Win NT (I386) MaxVersion1=5.00.2195.4  
    Win NT (I386) MinVersion2=5.10.2600.2  
    Win NT (I386) MaxVersion2=5.10.2600.2  
    Win NT (I386) MinVersion3=5.20.0000.0  
    Win NT (I386) MaxVersion3=5.20.9999.9999  
    Win NT (I386) MinVersion4=5.20.3790.0  
    Win NT (I386) MaxVersion4=5.20.3790.2  
    Win NT (I386) MinVersion5=6.00.0000.0  
    Win NT (I386) MaxVersion5=6.00.9999.9999  
    Win NT (IA64) MinVersion1=5.20.0000.0  
    Win NT (IA64) MaxVersion1=5.20.9999.9999  
    Win NT (x64) MinVersion1=5.20.0000.0  
    Win NT (x64) MaxVersion1=5.20.9999.9999  
    Win NT (x64) MinVersion2=5.20.3790.0  
    Win NT (x64) MaxVersion2=5.20.9999.9999  
    Win NT (x64) MinVersion3=5.20.3790.0  
    Win NT (x64) MaxVersion3=5.20.3790.2  
    Win NT (x64) MinVersion4=6.00.0000.0  
    Win NT (x64) MaxVersion4=6.00.9999.9999   
    ```  

-   **AdditionalProgramRequirements** (opcjonalnie): Podaj wszelkie inne dane i wymagania dotyczące komputerów klienckich do 127 znaków.

-   **CanRunWhen**: Określ stan użytkownika, który program wymaga do uruchomienia na komputerze klienckim. Dostępne wartości to **UserLoggedOn**, **NoUserLoggedOn** i **AnyUserStatus**. Wartość domyślna to **UserLoggedOn**.  

-   **UserInputRequired**: Określ, czy program wymaga interakcji z użytkownikiem. Dostępne wartości to **True** i **False**. Wartość domyślna to **True**. Ten wpis jest ustawiony na wartość **False**, jeśli wpis **CanRunWhen** nie jest ustawiony na wartość **UserLoggedOn**.  

-   **AdminRightsRequired**: Określ, czy program wymaga poświadczeń administracyjnych na komputerze do uruchomienia. Dostępne wartości to **True** i **False**. Wartość domyślna to **False**. Ten wpis jest ustawiony na wartość **True**, jeśli wpis **CanRunWhen** nie jest ustawiony na wartość **UserLoggedOn**.  

-   **UseInstallAccount**: Określ, czy program używa konta instalacji oprogramowania klienta na komputerach klienckich. Wartością domyślną jest **False**. Ten wpis jest też ustawiony na wartość **False**, jeśli wpis **CanRunWhen** jest ustawiony na wartość **UserLoggedOn**.  

-   **DriveLetterConnection**: Określ, czy program wymaga połączenia literę dysku do plików pakietu, które znajdują się w punkcie dystrybucji. Można określić wartość **True** lub **False**. Wartość domyślna to **False**, dzięki czemu program do używania połączenia Universal Naming Convention (UNC). Jeśli ta wartość jest równa **True**, służy następną dostępną literę dysku (począwszy od z: i nastąpi przejście wstecz).  

-   **SpecifyDrive** (opcjonalnie): Określ literę dysku, który program wymaga, aby nawiązać połączenie plików pakietu w punkcie dystrybucji. Określenie tej wartości wymusza stosowanie wskazanej litery dysku w połączeniach klienta z punktami dystrybucji.

-   **ReconnectDriveAtLogon**: Określ, czy komputer ponownie łączy do punktu dystrybucji, gdy użytkownik loguje się. Dostępne wartości to **True** i **False**. Wartość domyślna to **False**.  

-   **DependentProgram**: Określ program tego pakietu, który należy uruchomić przed bieżącego programu. Ten wpis ma format **DependentProgram**=<**nazwa_programu>**, gdzie **<nazwa_programu\>** to wpis **Name** dla danego programu w pliku definicji pakietu. Jeśli nie ma żadnych programów zależnych, ten wpis należy pozostawić pusty.  

     Przykład:  

     DependentProgram=Admin  
    DependentProgram=  

-   **Przypisanie**: Określ, jak program jest przypisane do użytkowników. Ta wartość może być: **FirstUser** (tylko pierwszy użytkownik, który zaloguje się klient uruchamia program) lub **EveryUser** (każdy użytkownik, który zaloguje się uruchamia program). Gdy wpis **CanRunWhen** nie jest ustawiony na wartość **UserLoggedOn**, ten wpis jest ustawiony na wartość **FirstUser**.  

-   **Wyłączone**: Określ, czy ten program może być anonsowany klientom. Dostępne wartości to **True** i **False**. Wartość domyślna to **False**.  

