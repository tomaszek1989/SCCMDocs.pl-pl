---
title: "Tworzenie warunków globalnych"
titleSuffix: Configuration Manager
description: "Tworzenie warunków globalnych, aby określić sposób aplikacja ma być dostarczana i wdrażana na urządzeniach klienckich."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2d5f871a-19dc-4bd3-a3ad-4230c7a69f1b
caps.latest.revision: "7"
caps.handback.revision: "0"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.openlocfilehash: 480e7a68308d458bc77ddb4956db2616eaaced97
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="how-to-create-global-conditions-in-system-center-configuration-manager"></a>Tworzenie warunków globalnych w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

W programie System Center Configuration Manager, warunki globalne to zasady reprezentujące warunki biznesowe lub techniczne używanych do określania, jak aplikacja ma być dostarczana i wdrażana na urządzeniach klienckich. Dostęp do warunków globalnych uzyskuje się za pośrednictwem strony **Wymagania** w Kreatorze tworzenia typów wdrożeń.  

> [!NOTE]  
>  Można edytować warunki globalne z witryny, w której zostały utworzone.  

 Poniższe procedury umożliwiają tworzenie warunków globalnych w programie Configuration Manager.  

## <a name="provide-basic-information-about-the-global-condition"></a>Podawanie ogólnych informacji o warunku globalnym  
 Dostępnych jest kilka różnych typów warunków globalnych. Z różnymi typami warunków globalnych są skojarzone różne opcje. Po wybraniu określonego typu warunku globalnego programu Configuration Manager zawiera opcje, które są stosowane do zaznaczenia.  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **Zarządzanie aplikacjami** > **warunków globalnych**.  

3.  Na **Home** karcie **Utwórz** grupy, wybierz **tworzenie warunku globalnego**.  

4.  W oknie dialogowym **Tworzenie warunku globalnego** podaj nazwę i opcjonalny opis warunku globalnego.  

5.  W **typu urządzenia** listy rozwijanej wybierz, czy warunek globalny ma dotyczyć **Windows** komputera lub **Windows Mobile** urządzenia.  

6.  Z listy rozwijanej **Typ warunku** wybierz jedną z następujących opcji:  

    -   **Ustawienie** – Ta opcja sprawdza istnienie jednego lub więcej elementów na urządzeniach klienckich. Na przykład można sprawdzić, czy na urządzeniu klienta istnieje wartość klucza pliku, folderu lub rejestru.  

    -   **Wyrażenie** — ta opcja pozwala skonfigurować bardziej złożone zasady w celu sprawdzenia, czy warunek jest spełniony na urządzeniach klienckich. Na przykład można sprawdzić, jeśli do zakresu od 2 GB do 4 GB pamięci fizycznej na komputerze lub urządzeniu przenośnym używa wprowadzanie danych przez ekran dotykowy.  

## <a name="set-up-rules-for-the-global-condition"></a>Skonfiguruj reguły dla warunku globalnego  
 Procedura do definiowania reguł warunku globalnego jest inna w zależności od tego, czy konfigurowane jest ustawienie lub wyrażenie. Aby skonfigurować ustawienie lub wyrażenie dla warunku globalnego, użyj odpowiedniej procedury.  

### <a name="to-set-up-a-setting-for-the-global-condition"></a>Aby skonfigurować ustawienie dla warunku globalnego  

1.  Z listy rozwijanej **Typ warunku** wybierz opcję **Ustawienie**.  

2.  Z listy rozwijanej **Typ ustawienia** wybierz element do użycia w charakterze warunku, pod kątem którego będą sprawdzane wymagania. Dostępne są następujące typy ustawień i konfiguracji.  

    -   **Zapytanie usługi Active Directory**  

        -   **Prefiks LDAP** — Określ prawidłowy prefiks LDAP zapytania usług domenowych Active Directory w celu oceny zgodności na komputerach klienckich. Możesz użyć albo prefiksu **LDAP://** albo prefiksu **GC://**.  

        -   **Nazwa wyróżniająca (DN)** — Podaj nazwę wyróżniającą obiektu usług domenowych w usłudze Active Directory, który będzie oceniana pod kątem zgodności na komputerach klienckich.  

        -   **Filtr wyszukiwania** — Określ opcjonalny filtr LDAP w celu ograniczenia wyników zapytania usług domenowych Active Directory dla oceny zgodności na komputerach klienckich.  

        -   **Zakres wyszukiwania** — Określ zakres wyszukiwania w usługach domenowych Active Directory:  

            -   **Podstawa** — odpytuje tylko określony obiekt.  

            -   **Jeden poziom** — ta opcja nie jest używana w tej wersji programu Configuration Manager.  

            -   **Poddrzewo** — odpytuje określony obiekt i jego pełne poddrzewo w katalogu.  

        -   **Właściwość** — Określ właściwość obiektu usług domenowych Active Directory do użycia w celu oceny zgodności na komputerach klienckich.  

        -   **Zapytanie** -pokazuje kwerendy LDAP, który jest tworzony na podstawie wpisów w **prefiks LDAP**, **nazwa wyróżniająca (DN)**, **filtr wyszukiwania** Jeśli zostanie określona, i **właściwości**. To zapytanie zostanie użyte do oceny zgodności na komputerach klienckich.  

    -   **Zestaw**  

        -   **Nazwa zestawu** — Określa nazwę obiektu zestawu, który ma być wyszukiwany. Nazwa nie może być taka sama jak innego obiektu zestawu tego samego typu, a nazwa musi być zarejestrowana w globalnej pamięci podręcznej zestawów. Nazwa zestawu może zawierać maksymalnie 256 znaków.  

        > [!NOTE]  
        >  Zestaw to fragment kodu, który może być współużytkowany przez różne aplikacje. Zestawy mogą mieć rozszerzenie nazwy pliku .dll lub .exe. Global Assembly Cache to folder o nazwie *%systemroot%\assembly* na komputerach klienckich, w którym są magazynowane wszystkie współużytkowane zestawy.  

    -   **System plików**  

        -   **Typ** — z listy rozwijanej wybierz, czy chcesz wyszukać **pliku** lub **folderu**.  

        -   **Ścieżka** — Określ ścieżkę do określonego pliku lub folderu na komputerach klienckich. W ścieżce możesz określić systemowe zmienne środowiskowe i zmienną środowiskową *%USERPROFILE%* .  

            > [!NOTE]  
            >  Jeśli użyjesz zmiennej środowiskowej *%USERPROFILE%* w polach **Ścieżka** lub **Nazwa pliku lub folderu** , zostaną przeszukane wszystkie profile użytkowników na komputerze klienckim. Może to skutkować odnalezieniem wielu wystąpień danego pliku lub folderu.  

        -   **Nazwa pliku lub folderu** — Określ nazwę obiektu pliku lub folderu, który ma zostać wyszukany. W nazwie pliku lub folderu możesz określić systemowe zmienne środowiskowe i zmienną środowiskową *%USERPROFILE%* . Można również użyć * i? symbole wieloznaczne w nazwie pliku.  

            > [!NOTE]  
            >  Jeśli podczas określania nazwy pliku lub folderu użyjesz symboli wieloznacznych, może to spowodować wytworzenie dużej liczby wyników. Może to spowodować wysokim wykorzystaniem zasobów na komputerze klienckim i duże zwiększenie ruchu sieciowego podczas raportowania wyników do programu Configuration Manager.  

        -   **Uwzględnij podfoldery** — Włącz tę opcję, jeśli chcesz dodatkowo przeszukać wszystkie podfoldery znajdujące się we wskazanej ścieżce.  

        -   **Ten plik lub folder jest skojarzony z aplikacją 64-bitowych** — wybierz, czy lokalizacja plików systemu 64-bitowego (*% windir %*\system32) powinna być dodatkowo przeszukiwana oprócz lokalizacji plików systemu 32-bitowych (*% windir %*\syswow64) na klientach programu Configuration Manager, z uruchomioną 64-bitowej wersji systemu Windows.  

            > [!NOTE]  
            >  Jeśli na jednym komputerze 64-bitowym ten sam plik lub folder istnieje zarówno w lokalizacji plików systemu 64-bitowego, jak i 32-bitowego, warunek globalny spowoduje odnalezienie wielu plików.  

         Ustawienie **System plików** nie obsługuje określania w polu **Ścieżka** ścieżki UNC prowadzącej do udziału sieciowego.  

    -   **Metabaza IIS**  

        -   **Ścieżka metabazy** — Określ prawidłową ścieżkę do metabazy usług IIS.  

        -   **Identyfikator właściwości** — Określ właściwość numeryczną ustawienia metabazy usług IIS.  

    -   **Klucz rejestru**  

        -   **Gałąź** — z listy rozwijanej wybierz gałąź rejestru, który ma nastąpić wyszukiwanie.  

        -   **Klucz** — Określ nazwę klucza rejestru, który chcesz wyszukać. Zastosuj format *klucz\podklucz*.  

        -   **Ten klucz rejestru jest skojarzony z aplikacją 64-bitową** — Wybierz, czy na klientach z uruchomioną 64-bitową wersją systemu Windows oprócz przeszukiwania 32-bitowych kluczy rejestru powinny być dodatkowo przeszukiwane 64-bitowe klucze rejestru.  

            > [!NOTE]  
            >  Jeśli na jednym komputerze 64-bitowym ten sam klucz rejestru istnieje zarówno w lokalizacji rejestru 64-bitowego, jak i 32-bitowego, warunek globalny spowoduje odnalezienie obydwu kluczy rejestru.  

    -   **Wartość rejestru**  

        -   **Gałąź** — Z listy rozwijanej wybierz gałąź rejestru, w której ma nastąpić wyszukiwanie.  

        -   **Klucz** — Określ nazwę klucza rejestru, który chcesz wyszukać. Zastosuj format *klucz\podklucz*.  

        -   **Wartość** — Określ wartość, która musi być zawarta w określonym kluczu rejestru.  

        -   **Ten klucz rejestru jest skojarzony z aplikacją 64-bitową** — Wybierz, czy na klientach z uruchomioną 64-bitową wersją systemu Windows oprócz przeszukiwania 32-bitowych kluczy rejestru powinny być dodatkowo przeszukiwane 64-bitowe klucze rejestru.  

            > [!NOTE]  
            >  Jeśli na jednym komputerze 64-bitowym ten sam klucz rejestru istnieje zarówno w lokalizacji rejestru 64-bitowego, jak i 32-bitowego, warunek globalny spowoduje odnalezienie obydwu kluczy rejestru.  

    -   **Skrypt**  

        -   **Skrypt wykrywania** — wybierz **Dodaj** celu wprowadzenia albo w trybie przeglądania wybierz skrypt do użycia. Można użyć skryptów środowiska Windows PowerShell, VBScript lub JScript.  

        -   **Uruchom skrypty, używając poświadczeń zalogowanego** — po włączeniu tej opcji skrypt będzie uruchamiany na komputerach klienckich przy użyciu poświadczeń użytkownika, który jest zalogowany.  

            > [!NOTE]  
            >  Wartość zwrócona przez ten skrypt zostanie użyta do oceny zgodności warunku globalnego. Na przykład w przypadku użycia skryptu VBScript można użyć **WScript.Echo wynik** polecenia w celu zwrócenia wartości zmiennej wynik do warunku globalnego.  
            >   
            >  Jeśli skrypt zwraca wiele wartości, te wartości muszą być w jednym wierszu i oddzielonych średnikami. Jeśli każda wartość będzie w osobnym wierszu, obliczenia zakończą się niepowodzeniem.  

    -   **Zapytanie SQL**  

        -   **Wystąpienie programu SQL Server** — Wybierz, czy zapytanie SQL ma być uruchamiane w wystąpieniu domyślnym, we wszystkich wystąpieniach czy w określonej nazwie wystąpienia bazy danych.  

            > [!NOTE]  
            >  Nazwa wystąpienia musi odwoływać się do lokalnego wystąpienia programu SQL Server. Aby odwołać się do wystąpienia klastrowanego serwera programu SQL, należy użyć ustawienia skryptu.  

        -   **Baza danych** — Określ nazwę bazy danych programu Microsoft SQL Server, dla której będzie uruchamiane zapytanie SQL.  

        -   **Kolumna** — Określ nazwę kolumny zwróconą przez instrukcję Transact-SQL w celu jej użycia do oceny zgodności warunku globalnego.  

        -   **Instrukcja Transact-SQL** — Określ pełne zapytanie SQL do użycia dla warunku globalnego. Można również wybrać **Otwórz** i otworzyć istniejące zapytanie SQL.  

    -   **Zapytanie WQL**  

        -   **Obszar nazw** — Określ obszar nazw WMI, który zostanie użyty w celu skonstruowania zapytania WQL do oceny pod kątem zgodności na komputerach klienckich. Wartość domyślna to Root\cimv2.  

        -   **Klasa** — Określa klasę WMI, która zostanie użyta w celu skonstruowania zapytania WQL do oceny pod kątem zgodności na komputerach klienckich.  

        -   **Właściwość** — Określa właściwość WMI, która zostanie użyta w celu skonstruowania zapytania WQL do oceny pod kątem zgodności na komputerach klienckich.  

        -   **Klauzula WHERE zapytania WQL** — Elementu **Klauzula WHERE zapytania WQL** możesz użyć do określenia klauzuli WHERE, która zostanie zastosowana do określonego obszaru nazw, klasy i właściwości na komputerach klienckich.  

    -   **Zapytanie XPath**  

        -   **Ścieżka** — Określ ścieżkę do pliku XML na komputerach klienckich do użycia w celu oceny zgodności. Program Configuration Manager obsługuje korzystanie z wszystkich zmiennych środowiskowych systemu Windows i *% USERPROFILE %* zmiennej użytkownika w nazwie ścieżki.  

        -   **Nazwa pliku XML** — Określ nazwę pliku zawierającego zapytanie XML do użycia w celu oceny zgodności na komputerach klienckich.  

        -   **Uwzględnij podfoldery** — Włącz tę opcję, jeśli chcesz dodatkowo przeszukać wszystkie podfoldery znajdujące się we wskazanej ścieżce.  

        -   **Ten plik jest skojarzony z aplikacją 64-bitowych** — wybierz, czy lokalizacja plików systemu 64-bitowego (*% windir %*\system32) powinna być dodatkowo przeszukiwana oprócz lokalizacji plików systemu 32-bitowych (*% windir %*\syswow64) na klientach programu Configuration Manager, z uruchomioną 64-bitowej wersji systemu Windows.  

        -   **Zapytanie XPath** — Określ prawidłowe pełne zapytanie w języku XML Path Language (XPath) do użycia w celu oceny zgodności na komputerach klienckich.  

        -   **Obszary nazw** — Otwiera okno dialogowe **Obszary nazw XML** , które pozwala zidentyfikować obszary nazw i prefiksy do zastosowania w zapytaniu XPath.  

3.  Z listy rozwijanej **Typ danych** wybierz format, w którym dane zostaną zwrócone przez warunek, zanim zostaną użyte do sprawdzenia wymagań.  

    > [!NOTE]  
    >  **— Typ danych** listy rozwijanej nie jest wyświetlane dla niektórych typów ustawień.  

4.  Skonfiguruj dalsze szczegóły tego ustawienia pod **ustawienie typu** listy rozwijanej. Elementy, które można skonfigurować będą się różnić w zależności od wybranego typu ustawienia.  

5.  Wybierz **OK** Aby zapisać zasadę i zamknąć **tworzenie warunku globalnego** okno dialogowe.  

### <a name="set-up-an-expression-for-the-global-condition"></a>Skonfigurować wyrażenie dla warunku globalnego  

1.  Z listy rozwijanej **Typ warunku** wybierz opcję **Wyrażenie**.  

2.  Wybierz **Dodaj klauzulę** otworzyć **Dodaj klauzulę** okno dialogowe.  

3.  Z listy rozwijanej **Wybierz kategorię** wybierz, czy wyrażenie dotyczy urządzenia, czy użytkownika. Możesz też wybrać opcję **Niestandardowe** , aby użyć wcześniej skonfigurowanego warunku globalnego.  

4.  Z listy rozwijanej **Wybierz warunek** wybierz warunek, którego chcesz użyć do oceny, czy użytkownik lub urządzenie spełnia wymagania zasady. Zawartość tej listy różni się w zależności od wybranej kategorii.  

5.  Z listy rozwijanej **Wybierz operator** wybierz operator, który zostanie użyty do porównania wybranego warunku z podaną wartością w celu oceny, czy użytkownik lub urządzenie spełnia wymagania zasady. Dostępni operatorzy różnią się w zależności od wybranego warunku.  

6.  W polu **Wartość** wpisz wartości, które będą używane z wybranym warunkiem i operator służący do oceny, czy użytkownik lub urządzenie spełnia wymagania zasady. Dostępne wartości różnią się w zależności od wybranych warunku i operatora.  

7.  Wybierz **OK** Aby zapisać wyrażenie i zamknąć **Dodaj klauzulę** okno dialogowe.  

8.  Kiedy zakończysz dodawanie klauzul do warunku globalnego, wybierz **OK** zamknąć **tworzenie warunku globalnego** okno dialogowe i zapisać warunek globalny.  
