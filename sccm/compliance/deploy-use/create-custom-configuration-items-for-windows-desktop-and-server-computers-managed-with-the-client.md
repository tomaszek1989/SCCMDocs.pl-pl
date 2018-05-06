---
title: 'Tworzenie elementów konfiguracji dla komputerów zarządzanych przez klienta systemu Windows '
titleSuffix: Configuration Manager
description: Zarządzaj ustawieniami dla serwerów z niestandardowego elementu konfiguracji systemu Windows, komputerów stacjonarnych i serwerów i komputerów z systemem Windows.
ms.date: 11/18/2016
ms.prod: configuration-manager
ms.technology: configmgr-compliance
ms.topic: conceptual
ms.assetid: 1eb2fcaf-acac-4388-9b31-6cccafacaabe
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: b2b2af6c022d854a6c6d623e3901abac70d42c7a
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-create-custom-configuration-items-for-windows-desktop-and-server-computers-managed-with-the-system-center-configuration-manager-client"></a>Tworzenie niestandardowych elementów konfiguracji dla komputerów stacjonarnych i serwerów z systemem Windows zarządzanych za pomocą klienta programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


Użyj programu System Center Configuration Manager **niestandardowe systemu Windows, komputerów stacjonarnych i serwerów** element konfiguracji do zarządzania ustawieniami komputerów z systemem Windows i serwery, które są zarządzane przez klienta programu Configuration Manager.  

## <a name="start-the-create-configuration-item-wizard"></a>Uruchom Kreatora tworzenia elementu konfiguracji

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność** > **ustawień zgodności** > **elementy konfiguracji**.  

3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij pozycję **Utwórz element konfiguracji**.  

4.  Na stronie **Ogólne** w **Kreatorze tworzenia elementu konfiguracji**podaj nazwę i opcjonalny opis elementu konfiguracji.  

5.  W obszarze **Określ typ elementu konfiguracji, który chcesz utworzyć** wybierz pozycję **Komputery stacjonarne i serwery z systemem Windows (niestandardowy)**.  

    > [!TIP]  
    >  Jeśli chcesz określić ustawienia metody wykrywania, która służy do sprawdzania istnienia aplikacji, wybierz pozycję **Ten plik konfiguracji zawiera ustawienia aplikacji**.  

6.  Kliknij przycisk **kategorii** możesz utworzyć i przypisać kategorie ułatwiające wyszukiwanie i filtrowanie elementów konfiguracji w konsoli programu Configuration Manager.  

## <a name="provide-detection-method-information"></a>Podawanie informacji dotyczących metody wykrywania  
 Użyj tej procedury, aby podać informacje dotyczące metody wykrywania dla elementu konfiguracji.  

> [!NOTE]  
>  Ma ona zastosowanie tylko wtedy, gdy wybrano pozycję **Ten element konfiguracji zawiera ustawienia aplikacji** na stronie **Ogólne** kreatora.  

 Metoda wykrywania w programie Configuration Manager zawiera reguły, które są używane do wykrywania, czy aplikacja jest zainstalowana na komputerze. Wykrywanie ma miejsce przed oceną zgodności elementu konfiguracji. Aby wykryć, czy aplikacja jest zainstalowana, można wykryć obecność pliku Instalatora Windows aplikacji, użyć niestandardowego skryptu lub wybrać pozycję **Zawsze zakładaj, że aplikacja jest zainstalowana** w celu poddania ocenie zgodności elementu konfiguracji niezależnie od tego, czy aplikacja jest zainstalowana.  

 Użyj tych procedur, aby skonfigurować metody wykrywania w programie System Center Configuration Manager.  

### <a name="to-detect-an-application-installation-by-using-the-windows-installer-file"></a>Aby wykryć instalację aplikacji przy użyciu pliku Instalatora Windows  

1.  Na stronie **Metody wykrywania** w **Kreatorze tworzenia elementu konfiguracji** zaznacz pole wyboru **Użyj wykrywania przez Instalatora Windows**.  

2.  Kliknij polecenie **Otwórz**, przejdź do pliku Instalatora Windows (msi), który chcesz wykryć, a następnie kliknij przycisk **Otwórz**.  

3.  Pole **Wersja** jest automatycznie wypełniane numerem wersji wybranego pliku Instalatora Windows. W tym polu można wprowadzić nowy numer wersji, jeśli wyświetlana wartość jest nieprawidłowa.  

4.  Zaznacz pole wyboru **Ta aplikacja jest zainstalowana dla jednego lub większej liczby użytkowników**, aby wykryć profile wszystkich użytkowników na komputerze.  

### <a name="to-detect-a-specific-application-and-deployment-type"></a>Aby wykryć określony typ aplikacji i wdrożenia  

1.  Na stronie **Metody wykrywania** w **Kreatorze tworzenia elementu konfiguracji** zaznacz pole wyboru **Wykryj określoną aplikację i typ wdrożenia**, a następnie kliknij przycisk **Wybierz**.  

2.  W oknie dialogowym **Określanie aplikacji** wybierz aplikację i skojarzony typ wdrożenia, który ma zostać wykryty.  

### <a name="to-detect-an-application-installation-by-using-a-custom-script"></a>Aby wykryć instalację aplikacji przy użyciu niestandardowego skryptu  

1.  Na stronie **Metody wykrywania** w **Kreatorze tworzenia elementu konfiguracji** zaznacz pole wyboru **Użyj niestandardowego skryptu do wykrywania tej aplikacji**.  

2.  Z listy wybierz język skryptu, który chcesz otworzyć. Do wyboru są następujące skrypty:  

    -   **Skrypt VBScript**  

    -   **Języka JScript**  

    -   **PowerShell**  

3.  Kliknij przycisk **Otwórz**, przejdź do skryptu, którego chcesz użyć, a następnie kliknij przycisk **Otwórz**.  

##  <a name="configure-settings"></a>Konfigurowanie ustawień  
 Użyj tej procedury, aby skonfigurować ustawienia w elemencie konfiguracji.  

 Ustawienia reprezentują warunki biznesowe lub techniczne służące do oceny zgodności na urządzeniach klienckich. Możesz skonfigurować nowe ustawienie lub przejść do istniejącego ustawienia na komputerze odniesienia.  

1.  Na stronie **Ustawienia** w **Kreatorze tworzenia elementu konfiguracji** kliknij pozycję **Nowy**.  

2.  Na karcie **Ogólne** w oknie dialogowym **Tworzenie ustawienia** podaj następujące informacje:  

    -   **Nazwa:** Wprowadź unikatową nazwę ustawienia. Możesz wprowadzić maksymalnie 256 znaków.  

    -   **Opis:** Wprowadź opis ustawienia. Możesz wprowadzić maksymalnie 256 znaków.  

    -   **Typ ustawienia:** Na liście wybierz i skonfiguruj jedno z następujących typów ustawień dla tego ustawienia:  

        -   **Zapytanie usługi Active Directory**  

             **Prefiks LDAP** — określ prawidłowy prefiks zapytania usług domenowych Active Directory w celu oceny zgodności na komputerach klienckich. Możesz użyć prefiksu **LDAP://** lub **GC://**, aby wykonać globalne wyszukiwanie w katalogu.  

             **Nazwa wyróżniająca** — określ nazwę wyróżniającą obiektu usług domenowych Active Directory do użycia w celu oceny zgodności na komputerach klienckich.  

             Jeśli na przykład chcesz ocenić wartość skojarzoną z użytkownikiem o nazwie Jan Kowalski w domenie corp.contoso.com, wprowadź następujące informacje:  

            -   **Filtr wyszukiwania** — określ opcjonalny filtr LDAP w celu ograniczenia wyników zapytania usług domenowych Active Directory dla oceny zgodności na komputerach klienckich.  

                 Aby zostały zwrócone wszystkie wyniki zapytania, wprowadź wartość **(objectclass=\*)**.  

            -   **Zakres wyszukiwania** — określ zakres wyszukiwania w usługach domenowych Active Directory. Można wybrać jedną z następujących opcji:  

                -   **Bazowy** — wykonuje zapytanie tylko względem określonego obiektu.  

                -   **Jeden poziom** — ta opcja nie jest używana w tej wersji programu Configuration Manager.  

                -   **Poddrzewo** — wykonuje zapytanie względem określonego obiektu i jego pełnego poddrzewa w katalogu.  

            -   **Właściwość** — określ właściwość obiektu usług domenowych Active Directory do użycia w celu oceny zgodności na komputerach klienckich.  

                 Jeśli na przykład chcesz utworzyć zapytanie dotyczące właściwości usługi Active Directory **badPwdCount**, w której jest przechowywana liczba wprowadzeń nieprawidłowego hasła przez użytkownika, wprowadź wartość **badPwdCount** w tym polu.  

            -   **Zapytanie** — wyświetla zapytanie złożone z wpisów w polach **Prefiks LDAP**, **Nazwa wyróżniająca**, **Filtr wyszukiwania** (jeśli go określono) i **Właściwość**, które służą do oceny zgodności na komputerach klienckich.  

             Więcej informacji na temat tworzenia zapytań LDAP zawiera dokumentacja systemu Windows Server.  

        -   **Zestaw**  

             Skonfiguruj następujące parametry tego typu ustawienia:  

            -   **Nazwa zestawu:** Określa nazwę obiektu zestawu, który chcesz wyszukać. Nazwa nie może być taka sama jak nazwa innego obiektu zestawu tego samego typu, a ponadto musi być zarejestrowana w globalnej pamięci podręcznej zestawów. Nazwa zestawu może mieć maksymalnie 256 znaków.  

             Zestaw to fragment kodu, który może być współużytkowany przez różne aplikacje. Zestawy to pliki, które mogą mieć rozszerzenie .dll lub .exe. Globalna pamięć podręczna zestawów to folder o nazwie *%systemroot%\Assembly* na komputerach klienckich, w którym są magazynowane wszystkie współdzielone zestawy.  

        -   **System plików**  

            -   **Typ** — z listy wybierz, czy chcesz wyszukiwać **Plik**, czy **Folder**.  

            -   **Ścieżka** — podaj ścieżkę do określonego pliku lub folderu na komputerach klienckich. W ścieżce możesz określić systemowe zmienne środowiskowe i zmienną środowiskową *%USERPROFILE%*.  

                > [!NOTE]  
                >  Jeśli zmienna środowiskowa *%USERPROFILE%* jest używana w polach **Ścieżka** lub **Nazwa pliku lub folderu**, wyszukiwanie obejmuje wszystkie profile użytkowników komputerów klienckich, co powoduje znalezienie wielu wystąpień określonego pliku lub folderu.  
                >   
                >  Jeśli ustawienia zgodności nie mają dostępu do określonej ścieżki, generowany jest błąd odnajdywania. Dodatkowo jeśli wyszukiwany plik jest obecnie w użyciu, zostanie wygenerowany błąd odnajdywania.  

            -   **Nazwa pliku lub folderu** — określ nazwę pliku lub folderu wyszukiwanego obiektu. W nazwie pliku lub folderu możesz określić systemowe zmienne środowiskowe i zmienną środowiskową *%USERPROFILE%*. Możesz też stosować symbole wieloznaczne * i ? w nazwie pliku.  

                > [!NOTE]  
                >  Określ nazwę pliku lub folderu, użyj symboli wieloznacznych ta kombinacja może powodować generowanie dużej liczby wyników i może spowodować wysokim wykorzystaniem zasobów na komputerze klienckim i duże zwiększenie ruchu sieciowego podczas raportowania wyników do programu Configuration Manager.  

            -   **Uwzględnij podfoldery** — Włącz tę opcję, jeśli chcesz dodatkowo przeszukać wszystkie podfoldery znajdujące się we wskazanej ścieżce.  

            -   **Ten plik lub folder jest skojarzony z aplikacją 64-bitową** — jeśli ta opcja zostanie włączona, tylko lokalizacje plików 64-bitowych (takie jak folder *%ProgramFiles%*) będą sprawdzane na komputerach 64-bitowych. Jeśli ta opcja nie zostanie włączona, sprawdzane będą zarówno lokalizacje 32-bitowe (takie jak folder *%ProgramFiles(x86)%*), jak i 64-bitowe.  

                > [!NOTE]  
                >  Jeśli na jednym komputerze 64-bitowym ten sam plik lub folder istnieje zarówno w lokalizacji plików systemu 64-bitowego, jak i 32-bitowego, warunek globalny spowoduje odnalezienie wielu plików.  

             Ustawienie **System plików** nie obsługuje określania w polu **Ścieżka** ścieżki UNC prowadzącej do udziału sieciowego.  

        -   **Metabaza IIS**  

            -   **Ścieżka metabazy** — określ prawidłową ścieżkę do metabazy usług Internet Information Services (IIS).  

            -   **Identyfikator właściwości** — Określ właściwość numeryczną ustawienia metabazy usług IIS.  

        -   **Klucz rejestru**  

            -   **Gałąź** — z listy wybierz gałąź rejestru, w której ma nastąpić wyszukiwanie.  

            -   **Klucz** — określ nazwę klucza rejestru, który chcesz wyszukać. Użyj formatu *klucz\podklucz*.  

            -   **Ten klucz rejestru jest skojarzony z aplikacją 64-bitową** — wybierz, czy na klientach z uruchomioną 64-bitową wersją systemu Windows oprócz przeszukiwania 32-bitowych kluczy rejestru powinny być dodatkowo przeszukiwane 64-bitowe klucze rejestru.  

                > [!NOTE]  
                >  Jeśli na jednym komputerze 64-bitowym ten sam klucz rejestru istnieje zarówno w lokalizacji rejestru 64-bitowego, jak i 32-bitowego, warunek globalny spowoduje odnalezienie obydwu kluczy rejestru.  

        -   **Wartość rejestru**  

            -   **Gałąź** — z listy wybierz gałąź rejestru, w której ma nastąpić wyszukiwanie.  

            -   **Klucz** — Określ nazwę klucza rejestru, który chcesz wyszukać. Użyj formatu *klucz\podklucz*.  

            -   **Wartość** — określ wartość, która musi być zawarta w określonym kluczu rejestru.  

            -   **Ten klucz rejestru jest skojarzony z aplikacją 64-bitową** — wybierz, czy na klientach z uruchomioną 64-bitową wersją systemu Windows oprócz przeszukiwania 32-bitowych kluczy rejestru powinny być dodatkowo przeszukiwane 64-bitowe klucze rejestru.  

                > [!NOTE]  
                >  Jeśli na jednym komputerze 64-bitowym ten sam klucz rejestru istnieje zarówno w lokalizacji rejestru 64-bitowego, jak i 32-bitowego, warunek globalny spowoduje odnalezienie obydwu kluczy rejestru.  

             Możesz również kliknąć przycisk **Przeglądaj**, aby przejść do lokalizacji w rejestrze na komputerze lub na komputerze zdalnym. Aby móc przeglądać zawartość komputera zdalnego, należy mieć prawa administratora na komputerze zdalnym i na komputerze tym musi być uruchomiona usługa rejestru zdalnego.  

        -   **Skrypt**  

            -   **Skrypt odnajdywania** — kliknij przycisk **Dodaj** w celu wprowadzenia albo wskazania skryptu, którego chcesz użyć. Możesz używać skryptów Windows PowerShell, VBScript lub Microsoft JScript.  

            -   **Uruchom skrypty, używając poświadczeń zalogowanego użytkownika** — po włączeniu tej opcji skrypt będzie uruchamiany na komputerach klienckich z wykorzystaniem poświadczeń zalogowanych użytkowników.  

                > [!NOTE]  
                >  Wartość zwrócona przez ten skrypt zostanie użyta do oceny zgodności warunku globalnego. Na przykład w przypadku użycia skryptu VBScript można użyć polecenia **WScript.Echo Result** w celu zwrócenia wartości zmiennej *Result* do warunku globalnego.  

        -   **Zapytanie SQL**  

            -   **Wystąpienie programu SQL Server** — Wybierz, czy zapytanie SQL ma być uruchamiane w wystąpieniu domyślnym, we wszystkich wystąpieniach czy w określonej nazwie wystąpienia bazy danych.  

                > [!NOTE]  
                >  Nazwa wystąpienia musi odwoływać się do lokalnego wystąpienia programu SQL Server. Aby odwołać się do wystąpienia klastrowanego serwera programu SQL, należy użyć ustawienia skryptu.  

            -   **Baza danych** — określ nazwę bazy danych programu Microsoft SQL Server, dla której będzie uruchamiane zapytanie SQL.  

            -   **Kolumna** — określ nazwę kolumny zwróconą przez instrukcję Transact-SQL, która jest używana do oceny zgodności warunku globalnego.  

            -   **Instrukcja Transact-SQL** — określ pełne zapytanie SQL do użycia dla warunku globalnego. Możesz też kliknąć przycisk **Otwórz** i otworzyć istniejące zapytanie SQL.  

                > [!IMPORTANT]  
                >  Ustawienia zapytań SQL nie obsługują żadnych poleceń SQL, które modyfikują bazę danych. Możesz używać tylko poleceń SQL, które odczytują informacje z bazy danych.  

        -   **Zapytanie WQL**  

            -   **Obszar nazw** — określ przestrzeń nazw Instrumentacji zarządzania Windows (WMI), która zostanie użyta w celu skonstruowania zapytania WQL do oceny pod kątem zgodności na komputerach klienckich. Wartość domyślna to Root\cimv2.  

            -   **Klasa** — określa klasę WMI, która zostanie użyta w celu skonstruowania zapytania WQL do oceny pod kątem zgodności na komputerach klienckich.  

            -   **Właściwość** — określa właściwość WMI, która zostanie użyta w celu skonstruowania zapytania WQL do oceny pod kątem zgodności na komputerach klienckich.  

            -   **Klauzula WHERE zapytania WQL** — Elementu **Klauzula WHERE zapytania WQL** możesz użyć do określenia klauzuli WHERE, która zostanie zastosowana do określonego obszaru nazw, klasy i właściwości na komputerach klienckich.  

        -   **Zapytanie XPath**  

            -   **Ścieżka** — określ ścieżkę do pliku XML na komputerach klienckich do użycia w celu oceny zgodności. Program Configuration Manager obsługuje korzystanie z wszystkich zmiennych środowiskowych systemu Windows i *% USERPROFILE %* zmiennej użytkownika w nazwie ścieżki.  

            -   **Nazwa pliku XML** — określ nazwę pliku zawierającego zapytanie XML do użycia w celu oceny zgodności na komputerach klienckich.  

            -   **Uwzględnij podfoldery** — Włącz tę opcję, jeśli chcesz dodatkowo przeszukać wszystkie podfoldery znajdujące się we wskazanej ścieżce.  

            -   **Ten plik jest skojarzony z aplikacją 64-bitowych** — wybierz, czy lokalizacja plików systemu 64-bitowego (*% windir %* \System32) powinna być dodatkowo przeszukiwana oprócz lokalizacji plików systemu 32-bitowych (*% windir %* \Syswow64) na komputerach klienckich programu Configuration Manager z uruchomioną 64-bitowej wersji systemu Windows.  

            -   **Zapytanie XPath** — określ prawidłowe pełne zapytanie w języku XML Path Language (XPath) do użycia w celu oceny zgodności na komputerach klienckich.  

            -   **Obszary nazw** — otwiera okno dialogowe **Obszary nazw XML**, które pozwala zidentyfikować przestrzenie nazw i prefiksy do zastosowania w zapytaniu XPath.  

             W przypadku próby odnalezienia zaszyfrowanego pliku xml plik zostanie odnaleziony przez ustawienia zgodności, ale zapytanie XPath nie wyświetli żadnych wyników i nie zostanie wygenerowany błąd.  

             Jeśli zapytanie XPath jest nieprawidłowe, to ustawienie jest traktowane jako niezgodne na komputerach klienckich.  

    -   **Typ danych:** Na liście wybierz format, w którym warunek zwraca dane, zanim zostanie on użyty do oceny ustawienia. Dla niektórych typów ustawień lista **Typ danych** nie jest wyświetlana.  

        > [!NOTE]  
        >  Typ danych **Liczba zmiennoprzecinkowa** obsługuje tylko 3 cyfry po przecinku.  

3.  Skonfiguruj dodatkowe szczegóły dotyczące tego ustawienia na liście **Typ ustawienia**. Elementy dostępne do konfigurowania mogą być różne w zależności od wybranego typu ustawienia.  

    > [!NOTE]  
    >  Podczas tworzenia ustawień typu **System plików**, **Klucz rejestru** i **Wartość rejestru** możesz kliknąć przycisk **Przeglądaj**, aby skonfigurować ustawienie na podstawie wartości z komputera odniesienia. Aby przejść do klucza lub wartości rejestru na komputerze zdalnym, musi na nim być włączona usługa Rejestr zdalny.  

4.  Kliknij przycisk **OK**, aby zapisać ustawienie i zamknąć okno dialogowe **Tworzenie ustawienia**.  

##  <a name="configure-compliance-rules"></a>Konfigurowanie reguł zgodności  
 Użyj poniższej procedury, aby skonfigurować reguły zgodności dla elementu konfiguracji.  

 Reguły zgodności określają warunki, które definiują zgodność elementu konfiguracji. Zanim będzie można ocenić ustawienie pod kątem zgodności, musi istnieć co najmniej jedna reguła zgodności. Ustawienia usługi WMI, rejestru i skryptu umożliwiają skorygowanie wartości rozpoznanych jako niezgodne. Możesz utworzyć nowe reguły lub przejść do istniejącego ustawienia w dowolnym elemencie konfiguracji, aby wybrać zawarte w nim reguły.  

### <a name="to-create-a-compliance-rule"></a>Aby utworzyć regułę zgodności  

1.  Na stronie **Reguły zgodności** w **Kreatorze tworzenia elementu konfiguracji** kliknij pozycję **Nowa**.  

2.  W oknie dialogowym **Tworzenie reguły** podaj następujące informacje:  

    -   **Nazwa:** Wprowadź nazwę reguły zgodności.  

    -   **Opis:** Wprowadź opis reguły zgodności.  

    -   **Wybrane ustawienie:** Kliknij przycisk **Przeglądaj** otworzyć **wybierz ustawienie** okno dialogowe. Wybierz ustawienie, dla którego chcesz zdefiniować regułę, lub kliknij pozycję **Nowe ustawienie**. Po zakończeniu kliknij pozycję **Wybierz**.  

        > [!NOTE]  
        >  Możesz również kliknąć pozycję **Właściwości**, aby wyświetlić informacje dotyczące aktualnie wybranego ustawienia.  

    -   **Typ reguły:** Wybierz typ reguły zgodności, którego chcesz użyć:  

        -   **Wartość** — tworzy regułę porównującą wartość zwróconą przez element konfiguracji z określoną wartością.  

        -   **Egzystencjalna** — tworzy regułę, która ocenia ustawienie w zależności od tego, czy istnieje na urządzeniu klienckim, lub na podstawie liczby odnalezionych wystąpień.  

    -   Dla reguły typu **Wartość** podaj następujące informacje:  

        -   **Ustawienie musi być zgodne z następującą regułą** — wybierz operator i wartość, która zostanie oceniona pod kątem zgodności z wybranym ustawieniem. Możesz użyć następujących operatorów:  

            |Operator|Więcej informacji|  
            |--------------|----------------------|  
            |Równa się|Brak dodatkowych informacji|  
            |Nie równa się|Brak dodatkowych informacji|  
            |Większe niż|Brak dodatkowych informacji|  
            |Mniejsze niż|Brak dodatkowych informacji|  
            |Między|Brak dodatkowych informacji|  
            |Większe niż lub równe|Brak dodatkowych informacji|  
            |Mniejsze niż lub równe|Brak dodatkowych informacji|  
            |Jedno z|W polu tekstowym określ jedną pozycję w każdym wierszu.|  
            |Żadne z|W polu tekstowym określ jedną pozycję w każdym wierszu.|  

        -   **Koryguj niezgodne reguły, jeśli są obsługiwane** — wybierz tę opcję, jeśli program Configuration Manager ma automatycznie korygować niezgodne reguły. Menedżer konfiguracji automatycznie koryguje następujące typy reguł:  

            -   **Wartość rejestru** — wartość rejestru jest korygowana, jeśli jest niezgodna, i jest tworzona, jeśli nie istnieje.  

            -   **Skrypt** (przez automatyczne uruchomienie skryptu korygowania).  

            -   **Kwerendy WQL**  

            > [!IMPORTANT]  
            >  Możesz korygować niezgodne reguły tylko wtedy, gdy operator reguły to **Równa się**.  

        -   **Zgłaszaj brak zgodności, jeśli wystąpienie tego ustawienia nie zostanie odnalezione** — element konfiguracji zgłasza niezgodność, jeśli to ustawienie nie zostanie znalezione na komputerach klienckich.  

        -   **Waga niezgodności do raportów:** Określ poziom ważności zgłaszany (w raportach programu Configuration Manager) w przypadku niepowodzenia reguły niezgodności. Poniżej przedstawiono dostępne poziomy ważności:  

            -   **Brak** komputerów, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia.  

            -   **Informacje o** komputerów, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **informacji**.  

            -   **Ostrzeżenie** komputerów, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **ostrzeżenie**.  

            -   **Krytyczne** komputerów, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczne**.  

            -   **Krytyczne ze zdarzeniem** komputerów, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczne**. Ten poziom ważności jest rejestrowany także jako zdarzenie systemu Windows w dzienniku zdarzeń aplikacji.  

        -   Dla typu reguły **Egzystencjalna** podaj następujące informacje:  

            > [!NOTE]  
            >  Wyświetlone opcje mogą różnić się w zależności od typu ustawienia, dla którego jest konfigurowana reguła.  

            -   **Ustawienie musi istnieć na urządzeniach klienckich**  

            -   **Ustawienie nie może istnieć na urządzeniach klienckich**  

            -   **Występuje następującą liczbę razy:**  

        -   **Waga niezgodności do raportów:** Określ poziom ważności zgłaszany (w raportach programu Configuration Manager) w przypadku niepowodzenia reguły niezgodności. Poniżej przedstawiono dostępne poziomy ważności:  

            -   **Brak** komputerów, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia.  

            -   **Informacje o** komputerów, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **informacji**.  

            -   **Ostrzeżenie** komputerów, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **ostrzeżenie**.  

            -   **Krytyczne** komputerów, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczne**.  

            -   **Krytyczne ze zdarzeniem** komputerów, które nie spełniają tej zasady zgodności, będą zgłaszać ważność niepowodzenia **krytyczne**. Ten poziom ważności jest rejestrowany także jako zdarzenie systemu Windows w dzienniku zdarzeń aplikacji.  

3.  Kliknij przycisk **OK**, aby zamknąć okno dialogowe **Tworzenie reguły**.  

##  <a name="specify-supported-platforms"></a>Określanie obsługiwanych platform  
 Obsługiwane platformy to systemy operacyjne, w których elementy konfiguracji są poddawane ocenie pod kątem zgodności.  

Z listy na stronie **Obsługiwane platformy** w **Kreatorze tworzenia elementu konfiguracji** wybierz wersje systemu Windows, w których element konfiguracji ma być poddawany ocenie pod kątem zgodności, lub kliknij pozycję **Zaznacz wszystko**.  

## <a name="complete-the-wizard"></a>Ukończ pracę kreatora  
 Na stronie **Podsumowanie** kreatora zapoznaj się z akcjami, które zostaną podjęte, a następnie zakończ pracę kreatora. Nowy element konfiguracji jest wyświetlany w węźle **Elementy konfiguracji** w obszarze roboczym **Zasoby i zgodność**.  
