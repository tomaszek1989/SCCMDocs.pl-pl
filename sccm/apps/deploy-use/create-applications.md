---
title: Tworzenie aplikacji
titleSuffix: Configuration Manager
description: Tworzenie aplikacji typy wdrożeń, metodach wykrywania i wymagania dotyczące instalowania oprogramowania.
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cc230ff4-7056-4339-a0a6-6a44cdbb2857
caps.latest.revision: ''
caps.handback.revision: ''
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 2569625daaf9a3e10dea26d86b01e10cacae0181
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="create-applications-with-system-center-configuration-manager"></a>Tworzenie aplikacji w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Aplikacji programu Configuration Manager ma co najmniej jeden typ wdrożenia. Te typy wdrożeń zawierają pliki instalacyjne i informacje niezbędne do zainstalowania oprogramowania na urządzeniach. Typ wdrożenia ma także zasady, takie jak metody wykrywania i wymagania, które określają, kiedy i jak klient nie zainstaluje oprogramowania.  

 Tworzenie aplikacji przy użyciu następujących metod:  

-   Automatyczne tworzenie aplikacji i typów wdrożenia przez odczytanie plików instalacyjnych aplikacji.  

-   ręczne utworzenie aplikacji, a następnie dodanie typów wdrożenia.  

-   Zaimportowanie aplikacji z pliku.  

> [!NOTE]  
>  Aby uzyskać szczegółowe informacje o tworzeniu Android aplikacje systemów iOS i Windows Phone, zobacz [tworzenie aplikacji dla urządzeń przenośnych](../../mdm/deploy-use/create-applications.md).  



## <a name="start-the-create-application-wizard"></a>Uruchom Kreatora tworzenia aplikacji  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **Zarządzanie aplikacjami** > **aplikacji**.  

3.  Na **Home** karcie **Utwórz** grupy, wybierz **tworzenie aplikacji**.  



## <a name="specify-whether-you-want-to-automatically-detect-application-information-or-manually-define-the-information"></a>Określ, czy chcesz automatycznie Wykryj informacje o aplikacji, lub ręcznie zdefiniować informacji o  

-   Automatycznie wykryj informacje o aplikacji do tworzenia aplikacji w warstwie podstawowa z pojedynczym typem wdrożenia. Na przykład plik Instalatora Windows, który nie ma zależności ani wymagań. Po utworzeniu aplikacji przy użyciu tej procedury można ją edytować w miarę potrzeby, aby dodawać lub zmieniać typy wdrożeń oraz dodawać metody wykrywania, zależności lub wymagania.  

-   Ręcznie określ informacje o aplikacji do tworzenia bardziej złożone aplikacje mające wiele typów wdrożeń, zależności, metod wykrywania lub wymagań.  

### <a name="automatically-detect-application-information"></a>Automatycznie wykryj informacje o aplikacji  

1.  Na **ogólne** strony kreatora tworzenia aplikacji wybierz **automatycznie Wykryj informacje o tej aplikacji z plików instalacyjnych**.  

2.  W **typu** listy rozwijanej, wybierz typ pliku instalacyjnego aplikacji którego chcesz użyć do wykrywania informacji o aplikacji. Informacje o dostępnych typach instalacji znajdują się w sekcji [Typy wdrożeń obsługiwane przez program Configuration Manager](/sccm/apps/deploy-use/create-applications#deployment-types-supported-by-configuration-manager) w tym temacie.  

3.  W **lokalizacji** Określ ścieżkę UNC (w postaci  *\\ \\serwera\\udostępnianie\\\filename*) lub łącze do pliku instalacyjnego aplikacji, które chcesz użyć do wykrywania informacji o aplikacji magazynu. Można też kliknąć przycisk **Przeglądaj**, aby przejść do lokalizacji pliku instalacyjnego.  

    > [!IMPORTANT]  
    >  Po wybraniu **Instalatora Windows (\*pliku .msi)** w ustawieniu typu aplikacji wszystkie pliki w określonym folderze zostały zaimportowane i są wysyłane do punktów dystrybucji. Upewnij się, że folder zostanie zawiera tylko pliki, które są niezbędne do zainstalowania aplikacji. Menedżer konfiguracji został sprawdzony pod kątem obsługi maksymalnie 20 000 plików aplikacji w pakiecie aplikacji. Jeśli aplikacja ma więcej plików, należy rozważyć utworzenie wielu aplikacji zawierających mniejszą liczbę plików.  

    >  Musi mieć dostęp do ścieżki UNC, do której ma aplikacji i wszelkich podfolderów, które zawierają zawartość aplikacji.  

4.  Na **Importuj informacje** strony kreatora tworzenia aplikacji przejrzyj informacje, które zostały zaimportowane, a następnie wybierz pozycję **dalej**. Jeśli to konieczne, możesz wybrać **Wstecz** aby wrócić do poprzedniej strony i poprawić błędy.  

5.  Na **ogólne informacje** strony kreatora tworzenia aplikacji Podaj następujące informacje:  

    > [!NOTE]  
    >  Jeśli Menedżer konfiguracji automatycznie wykrywa te informacje z plików instalacyjnych aplikacji, jest on już wypełniany tutaj. Wyświetlane opcje mogą się ponadto różnić w zależności od typu tworzonej aplikacji.  

    -   Ogólne informacje o aplikacji, takie jak nazwa aplikacji, komentarze i wersji. Ułatwia znajdowanie aplikacji w konsoli programu Configuration Manager, należy określić opcjonalne informacje dodatkowe.  

    -   **Program instalacyjny**: Określ program instalacyjny oraz wszelkie wymagane właściwości, które są niezbędne do zainstalowania typu wdrożenia aplikacji.  

        > [!TIP]  
        >  Jeśli program instalacyjny nie jest wyświetlane, wybierz **Przeglądaj** i przejdź do lokalizacji programu instalacyjnego.  

    -   **Zachowanie podczas instalowania**: Określ, czy typ wdrożenia aplikacji jest zainstalowany tylko dla obecnie zalogowanego użytkownika lub dla wszystkich użytkowników. Trzecia opcja jest instalowane dla wszystkich użytkowników, jeśli Jeśli jest wdrażana dla użytkownika jest wdrożony na urządzeniu lub tylko do określonego użytkownika.  

    -   **Użyj automatycznego połączenia VPN (jeśli jest skonfigurowane)**: Jeśli profil sieci VPN został wdrożony na urządzeniu, na którym uruchomiono aplikację, uruchom połączenie sieci VPN po uruchomieniu aplikacji (Windows 8.1 i Windows Phone 8.1 tylko).  

         Na urządzeniach Windows Phone 8.1 automatyczne połączenia VPN nie są obsługiwane, jeśli więcej niż jeden profil sieci VPN został wdrożony na urządzeniu.  

         Aby uzyskać więcej informacji, zobacz [profilów sieci VPN](../../protect/deploy-use/vpn-profiles.md).  

6.  Wybierz **dalej**, przejrzyj informacje o aplikacji na **Podsumowanie** strony, a następnie Zakończ pracę Kreatora tworzenia aplikacji.  

Nowa aplikacja pojawi się w **aplikacji** węzła konsoli programu Configuration Manager, i ukończeniu tworzenia aplikacji. Informacje o dodawaniu większej liczby typów wdrożenia do aplikacji znajdują się w sekcji [Tworzenie typów wdrożenia aplikacji](/sccm/apps/deploy-use/create-applications#create-deployment-types-for-the-application) w tym temacie.  

### <a name="manually-specify-application-information"></a>Ręcznie określ informacje o aplikacji  

1.  Na **ogólne** strony kreatora tworzenia aplikacji wybierz **ręcznie określ informacje o aplikacji**, a następnie wybierz pozycję **dalej**.  

2.  Określ ogólne informacje o aplikacji, takie jak nazwa aplikacji, komentarze i wersji. Ułatwia znajdowanie aplikacji w konsoli programu Configuration Manager, należy określić opcjonalne informacje dodatkowe.  

3.  Na **katalogu aplikacji** strony kreatora tworzenia aplikacji Podaj następujące informacje:  

    -   **Wybrany język**: Na liście rozwijanej wybierz wersję językową aplikacji, którą chcesz skonfigurować. Wybierz **Dodaj lub usuń** Aby skonfigurować więcej języków aplikacji.  

    -   **Nazwa zlokalizowanej aplikacji**: Określ nazwę aplikacji w języku wybranym **wybrany język** listy rozwijanej.  

        > [!IMPORTANT]  
        >  Podaj zlokalizowaną nazwę aplikacji dla każdej skonfigurowanej wersji.  

    -   **Kategorie użytkowników**: Wybierz **Edytuj** Aby określić kategorie aplikacji w języku wybranym **wybrany język** listy rozwijanej. Użytkownicy Centrum oprogramowania można używać owych wybranych kategorii do filtrowania i sortowania dostępnych aplikacji.  

    -   **Dokumentacja użytkownika**: Wybierz **Przeglądaj** Określ lokalizację pliku, który użytkownicy Centrum oprogramowania mogą odczytać w celu uzyskania dodatkowych informacji o tej aplikacji. Ta lokalizacja jest adres URL lub ścieżkę i nazwę sieci.

    -   **Tekst łącza**: Określ tekst wyświetlany zamiast adresu URL aplikacji.  

    -   **Adres URL aplikacji prywatności**: Określ adres URL prowadzący do zasad zachowania poufności informacji dla aplikacji.  

    -   **Zlokalizowany opis**: Wprowadź opis dla tej aplikacji w języku wybranym **wybrany język** listy rozwijanej.  

    -   **Keywords**: Wprowadź listę słów kluczowych w języku wybranym **wybrany język** listy rozwijanej. Te słowa kluczowe ułatwią użytkownikom Centrum oprogramowania wyszukiwanie aplikacji.  

    -   **Ikona**: Wybierz **Przeglądaj** aby wybrać ikonę tej aplikacji spośród dostępnych ikon. Jeśli nie określisz ikony, ikony domyślnej jest używana dla tej aplikacji. Można teraz ustawić ikonę z wymiarów z maksymalnie 512 x 512.

    -   **Wyświetlaj jako polecaną aplikację i wyróżnij w portalu firmy**: Ta opcja powoduje wyświetlenie wyraźnie aplikacji w portalu firmy.  

4.  Na **typy wdrożeń** strony kreatora tworzenia aplikacji wybierz **Dodaj** do utworzenia nowego typu wdrożenia.  

 Aby uzyskać więcej informacji, zobacz [tworzenia typów wdrożenia dla aplikacji](/sccm/apps/deploy-use/create-applications#create-deployment-types-for-the-application).  

5.  Wybierz **dalej**, przejrzyj informacje o aplikacji na **Podsumowanie** strony, a następnie Zakończ pracę Kreatora tworzenia aplikacji.  

Nowa aplikacja pojawi się w **aplikacji** węzła konsoli programu Configuration Manager.  



##  <a name="create-deployment-types-for-the-application"></a>Tworzenie typów wdrożenia dla aplikacji  
 Jeśli automatycznie Wykryj informacje o aplikacji, nie może być konieczne Zakończ niektóre czynności opisane w tych procedurach.  

### <a name="start-the-create-deployment-type-wizard"></a>Uruchomienie Kreatora tworzenia typu wdrożenia  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **Zarządzanie aplikacjami** > **aplikacji**.  

3.  Wybierz aplikację, a następnie na **Home** karcie **aplikacji** grupy, wybierz **Utwórz typ wdrożenia**.  

> [!TIP]  
>  Można również uruchomić Kreatora tworzenia typu wdrożenia z Kreatora tworzenia aplikacji i **typy wdrożeń** karcie *< nazwa aplikacji\>*  **właściwości** okno dialogowe.  

### <a name="specify-whether-you-want-to-automatically-detect-deployment-type-information-or-manually-set-up-the-information"></a>Określ, czy mają być automatycznie Wykryj informacje o typie wdrożenia, lub ręcznie skonfigurować informacje  
 Użyj jednej z następujących procedur, aby wykrywać automatycznie lub ręcznie skonfigurować informacje o typie wdrożenia.  

#### <a name="automatically-detect-deployment-type-information"></a>Automatycznie wykryj informacje o typie wdrożenia  

1.  Na **ogólne** strony kreatora tworzenia typu wdrożenia wybierz **automatycznie Zidentyfikuj informacje o tym typie wdrożenia z plików instalacyjnych**.  

2.  W **typu** wybierz typ pliku instalacyjnego aplikacji, którego chcesz użyć do wykrywania informacji o typie wdrożenia.  

3.  W **lokalizacji** polu, określ ścieżkę sieciową lub określić linku do plików instalacyjnych aplikacji w sklepie. Configuration Manager używa tych plików do wykrywania informacji o typie wdrożenia. Można również wybrać **Przeglądaj** aby wskazać plik instalacyjny.  

    > [!NOTE]  
    >  Musi mieć dostęp do lokalizacji sieciowej, która ma aplikacji i wszelkich podfolderów, które zawierają zawartość aplikacji.  

4.  Na **Importuj informacje** strony kreatora tworzenia typu wdrożenia Przejrzyj informacje, które zostały zaimportowane, a następnie wybierz pozycję **dalej**. Można również wybrać **Wstecz** aby wrócić do poprzedniej strony i poprawić błędy.  

5.  Na **ogólne informacje** strony kreatora tworzenia typu wdrożenia Podaj następujące informacje:  

    > [!NOTE]  
    >  Niektóre informacje o typie wdrożenia mogą już być obecne, jeśli zostały odczytane z plików instalacyjnych aplikacji. Ponadto wyświetlane opcje mogą się różnić w zależności od typu wdrożenia, które tworzysz.  

    -   Ogólne informacje o typie wdrożenia, takie jak nazwa, komentarze administratora oraz dostępne języki.  

    -   **Program instalacyjny**: Określ program instalacyjny oraz wszelkie właściwości niezbędne do zainstalowania typu wdrożenia.  

    -   **Zachowanie podczas instalowania**: Określ, czy do zainstalowania typu wdrożenia dla bieżącego użytkownika lub dla wszystkich użytkowników. Trzecia opcja jest instalowane dla wszystkich użytkowników, jeśli Jeśli jest wdrażana dla użytkownika jest wdrożony na urządzeniu lub tylko do określonego użytkownika.  

    -   **Użyj automatycznego połączenia VPN (jeśli jest skonfigurowane)**: Jeśli profil sieci VPN został wdrożony na urządzeniu, na którym uruchomiono aplikację, uruchom połączenie sieci VPN po uruchomieniu aplikacji (Windows 8.1 i Windows Phone 8.1 tylko). Jeśli wiele profilów sieci VPN zostały wdrożone na urządzeniu Windows 8.1, pierwszy wdrożonego profilu sieci VPN jest używany domyślnie.  

         Na urządzeniach Windows Phone 8.1 automatyczne połączenia VPN nie są obsługiwane, jeśli więcej niż jeden profil sieci VPN został wdrożony na urządzeniu.  

         Aby uzyskać więcej informacji, zobacz [profilów sieci VPN](../../protect/deploy-use/vpn-profiles.md).  

6.  Wybierz **dalej**, a następnie przejdź do [określenie opcji zawartości typu wdrożenia](/sccm/apps/deploy-use/create-applications#specify-content-options-for-the-deployment-type).  

#### <a name="manually-set-up-the-deployment-type-information"></a>Ręcznie skonfigurować informacje o typie wdrożenia  

1.  Na **ogólne** strony Utwórz typ wdrożenia w kreatorze **typu** listy rozwijanej wybierz typ pliku instalacyjnego aplikacji dla tego typu wdrożenia. 

2.  Wybierz **ręcznie określ informacje o typie wdrożenia**, a następnie kliknij przycisk **dalej**.

3.  Na **ogólne informacje** strony kreatora tworzenia typu wdrożenia Określ nazwę typu wdrożenia. Opcjonalnie określ opis oraz języki, dla tego typu wdrożenia, a następnie kliknij przycisk **dalej**.  

4.  Przejdź do sekcji [Określenie opcji zawartości typu wdrożenia](/sccm/apps/deploy-use/create-applications#specify-content-options-for-the-deployment-type).  

###  <a name="specify-content-options-for-the-deployment-type"></a>Określenie opcji zawartości typu wdrożenia  

1.  Na **zawartości** strony kreatora tworzenia typu wdrożenia Podaj następujące informacje:  

    -   **Lokalizacja zawartości**: Określ lokalizację zawartości dla tego typu wdrożenia, lub wybierz **Przeglądaj** wybrać folder zawartości typu wdrożenia.  

        > [!IMPORTANT]  
        >  Konto System na komputerze serwera lokacji musi mieć uprawnienia do określonej lokalizacji zawartości.  

    -   **Odinstaluj ustawienia zawartości**: Określ jedną z następujących opcji:
        - **Taka sama, jak zainstalować zawartość**: Jeśli instalowania i odinstalowywania zawartości są takie same, wybierz tę opcję. Ta opcja jest domyślnie.
        - **Nie odinstalowania zawartości**: Jeśli aplikacja nie wymaga do odinstalowania zawartości, wybierz tę opcję.
        - **Inna niż instalacja zawartości**: Jeśli zawartość Odinstaluj różni się od instalacji zawartości, wybierz tę opcję. Następnie określ lokalizację zawartości aplikacji, który służy do odinstalowania aplikacji.
5. Kliknij przycisk **OK** aby zamknąć okno dialogowe właściwości typu wdrożenia.

    -   **Utrwal zawartość w pamięci podręcznej klienta**: Wybierz tę opcję, aby określić, czy klient zawsze zachowuje zawartość w pamięci podręcznej. Klient zachowuje zawartość, nawet jeśli aplikacja jest już zainstalowana. Ta opcja jest przydatna w przypadku niektórych wdrożeń, takich jak oprogramowania wdrażanego przez Instalatora systemu Windows. Instalator systemu Windows musi lokalną kopię źródła zawartości dla stosowania aktualizacji. Mimo że ta opcja zmniejszenie ilości dostępnej pamięci podręcznej. Wybierz tę opcję, może spowodować dużego wdrożenia Niepowodzenie w późniejszym czasie, jeśli pamięć podręczna nie ma wystarczająco dużo miejsca.  

    -   **Zezwalaj klientom na współużytkowanie zawartości z innymi klientami w tej samej podsieci**: Aby zmniejszyć obciążenie sieci, wybierz tę opcję. Klienci pobierają zawartość z innych klientów lokalnych w sieci, w których znajduje się już pobrana zawartość w pamięci podręcznej. Ta opcja korzysta z technologii Windows BranchCache.  

    -   **Program instalacyjny**: Określ nazwę programu instalacyjnego oraz wszelkie wymagane parametry instalacji lub wybierz **Przeglądaj** aby wskazać plik instalacyjny.  

    -   **Instalacja rozpocznie się za**: Opcjonalnie określ folder zawierający program instalacyjny typu wdrożenia. Ten folder może być ścieżką bezwzględną na kliencie lub ścieżką do folderu punktu dystrybucji, który zawiera pliki instalacyjne.  

    -   **Program dezinstalacyjny**: Opcjonalnie określ nazwę programu dezinstalacyjnego oraz wszelkie wymagane parametry, lub wybierz **Przeglądaj** ich wyszukanie.  

    -   **Dezinstalacja rozpocznie się za**: Opcjonalnie określ folder zawierający program dezinstalacyjny typu wdrożenia. Ten folder może być ścieżką bezwzględną na kliencie. Można też ścieżkę względną w punkcie dystrybucji folderu z pakietem.  

    -   **Uruchom program instalacyjny i dezinstalacyjny jako proces 32-bitowy na klientach 64-bitowych**: Użyj lokalizacje 32-bitowych plików i rejestru na komputerach z systemem Windows, aby uruchomić program instalacyjny typu wdrożenia.  

2.  Wybierz **dalej**.  

### <a name="set-up-detection-methods-to-indicate-the-presence-of-the-deployment-type-windows-pcs-only"></a>Konfigurowanie metod wykrywania obecności typu wdrożenia (tylko komputery z systemem Windows)  
 Ta procedura konfiguruje metodę wykrywania, która wskazuje, czy typ wdrożenia jest już zainstalowany.  

1.  Na **metody wykrywania** strony kreatora tworzenia typu wdrożenia wybierz **Konfiguruj reguły do wykrycia obecności tego typu wdrożenia**, a następnie wybierz pozycję **Dodaj klauzulę**.  

    > [!NOTE]  
    >  Można również wybrać opcję **Użyj skryptu niestandardowego do wykrycia obecności tego typu wdrożenia**. Aby uzyskać więcej informacji, zobacz [Użyj niestandardowego skryptu w celu sprawdzenia obecności typu wdrożenia](/sccm/apps/deploy-use/create-applications#Use-a-custom-script-to-check-for-the-presence-of-a-deployment-type).  

2.  W oknie dialogowym **Reguła wykrywania** z listy rozwijanej **Typ ustawienia** wybierz metodę, której chcesz używać do wykrywania obecności typu wdrożenia. Można wybrać jedną z następujących metod:  

    -   **System plików**: Wykryj, czy na urządzeniu klienta istnieje określony plik lub folder. Wykrywanie wskazuje, że aplikacja jest zainstalowana.  

        > [!NOTE]  
        >  **System plików** ustawienie typu nie obsługuje określania w polu Ścieżka ścieżki UNC do udziału sieciowego. Na urządzeniu klienta można określić wyłącznie ścieżkę lokalną.  
        >   
        >  Aby sprawdzić lokalizacje plików 32-bitowych pod kątem określonego pliku lub folderu, wybierz najpierw **ten plik lub folder jest skojarzony z aplikacją 32-bitowych na 64-bitowym**. Jeśli plik lub folder nie zostanie odnaleziony, 64-bitowych lokalizacje zostaną przeszukane.  

    -   **Rejestru**: Wykryj, czy na urządzeniu klienta istnieje określony klucz rejestru lub wartość rejestru. Wykrywanie wskazuje, że aplikacja jest zainstalowana.  

        > [!NOTE]  
        >  Aby sprawdzić lokalizacje 32-bitowego rejestru pod kątem obecności określonego klucza rejestru, należy najpierw zaznaczyć **ten klucz rejestru jest skojarzony z aplikacją 32-bitowych na 64-bitowym**. Jeśli nie odnaleziono klucza rejestru, 64-bitowych lokalizacje zostaną przeszukane.  

    -   **Instalator Windows**: Wykryj, czy na urządzeniu klienta istnieje określony plik Instalatora Windows. Wykrywanie wskazuje, że aplikacja jest zainstalowana.  

3.  Określ szczegóły element, aby wykryć, czy ten typ wdrożenia został zainstalowany. Możesz na przykład użyć pliku, folderu, klucza rejestru, wartości rejestru lub kodu produktu Instalatora Windows.  

4.  Określ, czy element musi istnieć czy spełniają reguły. Na przykład, jeśli zostaną wykryte przy użyciu pliku, wybierz **aby wskazywanie obecności tej aplikacji w systemie docelowym musi istnieć ustawienie systemu plików**.  

5.  Wybierz **dalej** zamknąć **reguły wykrywania** okno dialogowe.  

####  <a name="use-a-custom-script-to-check-for-the-presence-of-a-deployment-type"></a>Użyj niestandardowego skryptu w celu sprawdzenia obecności typu wdrożenia  

1.  Na **metody wykrywania** strony kreatora tworzenia typu wdrożenia wybierz **Użyj skryptu niestandardowego do wykrycia obecności tego typu wdrożenia** polu, a następnie wybierz pozycję **Edytuj**.  

2.  W oknie dialogowym **Edytor skryptów** z listy rozwijanej **Typ skryptu** wybierz język skryptu, którego chcesz używać do wykrywania obecności typu wdrożenia.  

3.  W **skryptu zawartość** wprowadź skrypt, którego chcesz użyć. Możesz również wkleić w tym polu zawartość istniejącego skryptu lub wybrać **Otwórz** aby przejść do istniejącego zapisanego skryptu. Program Configuration Manager sprawdza wyniki ze skryptu. Odczytuje wartości zapisane w strumieniu wyjściowym standard (STDOUT), strumienia błędów (STDERR) oraz kod zakończenia przez skrypt. Jeśli skrypt zakończy pracę z wartość niezerową, skrypt zakończy się niepowodzeniem, a stan wykrywania aplikacji jest nieznany. Jeśli kod zakończenia to zero, a STDOUT zawiera dane, stan wykrywania aplikacji jest zainstalowany.  

 Skorzystaj z poniższej tabeli, aby sprawdzić, czy aplikacja jest zainstalowana z danych wyjściowych ze skryptu:  

|Kod zakończenia skryptu|Szczegóły|
|--------------------------------|-----------------|
|0|**Dane odczytane ze strumienia wyjściowego STDOUT**: pusty<br /><br /> **Dane odczytane ze strumienia wyjściowego STDERR**: pusty<br /><br /> **Wynik skryptu**: Powodzenie<br /><br /> **Stan wykrywania aplikacji**: Nie jest zainstalowany|  
|0|**Dane odczytane ze strumienia wyjściowego STDOUT**: pusty<br /><br /> **Dane odczytane ze strumienia wyjściowego STDERR**: Nie jest pusty<br /><br /> **Wynik skryptu**: Błąd<br /><br /> **Stan wykrywania aplikacji**: Nieznane|  
|0|**Dane odczytane ze strumienia wyjściowego STDOUT**: Nie jest pusty<br /><br /> **Dane odczytane ze strumienia wyjściowego STDERR**: pusty<br /><br /> **Wynik skryptu**: Powodzenie<br /><br /> **Stan wykrywania aplikacji**: zainstalowany|  
|0|**Dane odczytane ze strumienia wyjściowego STDOUT**: Nie jest pusty<br /><br /> **Dane odczytane ze strumienia wyjściowego STDERR**: Nie jest pusty<br /><br /> **Wynik skryptu**: Powodzenie<br /><br /> **Stan wykrywania aplikacji**: zainstalowany|  
|Wartość niezerowa|**Dane odczytane ze strumienia wyjściowego STDOUT**: pusty<br /><br /> **Dane odczytane ze strumienia wyjściowego STDERR**: pusty<br /><br /> **Wynik skryptu**: Błąd<br /><br /> **Stan wykrywania aplikacji**: Nieznane|  
|Wartość niezerowa|**Dane odczytane ze strumienia wyjściowego STDOUT**: pusty<br /><br /> **Dane odczytane ze strumienia wyjściowego STDERR**: Nie jest pusty<br /><br /> **Wynik skryptu**: Błąd<br /><br /> **Stan wykrywania aplikacji**: Nieznane|  
|Wartość niezerowa|**Dane odczytane ze strumienia wyjściowego STDOUT**: Nie jest pusty<br /><br /> **Dane odczytane ze strumienia wyjściowego STDERR**: pusty<br /><br /> **Wynik skryptu**: Błąd<br /><br /> **Stan wykrywania aplikacji**: Nieznane|  
|Wartość niezerowa|**Dane odczytane ze strumienia wyjściowego STDOUT**: Nie jest pusty<br /><br /> **Dane odczytane ze strumienia wyjściowego STDERR**: Nie jest pusty<br /><br /> **Wynik skryptu**: Błąd<br /><br /> **Stan wykrywania aplikacji**: Nieznane|  

Poniższa tabela zawiera Microsoft Visual Basic (VB) przykładowe skrypty, które służy do pisania własnych skryptów wykrywania aplikacji.  

|Przykładowy skrypt Visual Basic|Opis|  
|--------------------------------|-----------------|  
|**WScript.Quit(1)**|Skrypt zwraca kod zakończenia o wartości innej niż zero, co oznacza, że jego niepomyślne wykonanie. W takiej sytuacji stan wykrywania aplikacji będzie nieznany.|  
|**WScript.StdErr.Write "Skrypt nie powiodło się"**<br /><br /> **WScript.Quit(0)**|Skrypt zwraca kod zakończenia o wartości zero, ale wartość strumienia wyjściowego STDERR nie jest pusty. Wynik tego wskazuje, że skrypt nie uruchomili pomyślnie. W takiej sytuacji stan wykrywania aplikacji będzie nieznany.|  
|**WScript.Quit(0)**|Skrypt zwraca kod zakończenia o wartości zero, co oznacza jego pomyślne wykonanie. Wartość strumienia wyjściowego STDOUT jest jednak pusta, co oznacza, że aplikacja nie jest zainstalowana.|  
|**WScript.StdOut.Write "aplikacja jest zainstalowane"**<br /><br /> **WScript.Quit(0)**|Skrypt zwraca kod zakończenia o wartości zero, co oznacza jego pomyślne wykonanie. Wartość strumienia wyjściowego STDOUT nie jest pusta, co oznacza, że aplikacja jest zainstalowana.|  
|**WScript.StdOut.Write "aplikacja jest zainstalowane"**<br /><br /> **WScript.StdErr.Write "Ukończone"**<br /><br /> **WScript.Quit(0)**|Skrypt zwraca kod zakończenia o wartości zero, co oznacza jego pomyślne wykonanie. Wartości strumieni wyjściowych STDOUT i STDERR nie są puste, co oznacza, że aplikacja jest zainstalowana.|  

 > [!NOTE]  
 >  Maksymalny rozmiar skryptu, jakiego można użyć, to 32 kilobajty (KB).  

4.  Wybierz **OK** zamknąć **Edytor skryptów** okno dialogowe.  

### <a name="specify-user-experience-options-for-the-deployment-type"></a>Określenie opcji czynności użytkownika dotyczących typu wdrożenia  
 Te ustawienia określają, jak Klient instaluje aplikację na urządzeniach, a użytkownik zobaczy.  

1.  Na **środowisko użytkownika** strony kreatora tworzenia typu wdrożenia Podaj następujące informacje:  

    -   **Zachowanie podczas instalacji**: Na liście rozwijanej wybierz jedną z następujących opcji:  

        -   **Zainstaluj dla użytkownika**: Aplikacja zostanie zainstalowana tylko dla użytkownika, do której aplikacja jest wdrażana.  

        -   **Zainstaluj dla systemu**: Aplikacja zostanie zainstalowana tylko raz i będzie dostępna dla wszystkich użytkowników.  

        -   **Zainstaluj dla systemu, jeśli zasób jest urządzeniem; w przeciwnym razie zainstaluj dla użytkownika**: Jeśli aplikacja jest wdrażana na urządzeniu, Klient instaluje go dla wszystkich użytkowników. Jeśli aplikacja jest wdrażana dla użytkownika, Klient instaluje je tylko dla tego użytkownika.  

    -   **Wymagane zalogowanie**: Określ wymagania dotyczące logowania dla tego typu wdrożenia przy użyciu następujących opcji:  

        -   **Tylko wtedy, gdy użytkownik jest zalogowany**  

        -   **Określa, czy użytkownik jest zalogowany**  

        -   **Tylko wtedy, gdy użytkownik nie jest zalogowany**  

        > [!NOTE]  
        >  Domyślnie ta opcja **tylko, gdy użytkownik jest zalogowany**. W przypadku wybrania **zainstaluj dla użytkownika** w **zachowanie podczas instalacji** listy rozwijanej, nie można zmienić tej opcji.  

    -   **Widoczność programu instalacyjnego**: Określ tryb, w którym typ wdrożenia zostanie uruchomiony na urządzeniach klienckich. Dostępne są następujące opcje:  

        -   **Zmaksymalizowane**: Typ wdrożenia zostanie uruchomiony w trybie zmaksymalizowanym na urządzeniach klienckich. Użytkownicy widzą wszystkie działania instalacyjne.  

        -   **Normalny**: Typ wdrożenia zostanie uruchomiony w trybie normalnym na podstawie ustawień domyślnych systemu i programu. Ten tryb jest ustawieniem domyślnym.  

        -   **Zminimalizowany**: Typ wdrożenia zostanie uruchomiony w trybie zminimalizowanym na urządzeniach klienckich. Użytkownicy będą widzieć działanie instalacji w obszarze powiadomień lub na pasku zadań.  

        -   **Ukryte**: Typ wdrożenia zostanie ukryta na urządzeniach klienckich. Użytkownicy widzą żadnych działań instalacyjnych.  

    -   **Zezwalaj użytkownikom na wyświetlanie i interakcji z instalacją programu**: Określ, czy użytkownik może interakcyjnie przeprowadzić instalację typu wdrożenia, aby skonfigurować opcje instalacji.  

        > [!NOTE]  
        >  W przypadku wybrania **zainstaluj dla użytkownika** opcji **zachowanie podczas instalacji** listy rozwijanej, ta opcja jest domyślnie włączona.  

        > [!IMPORTANT]
        > Począwszy od wersji 1802, to ustawienie jest opcjonalne po wybraniu **zainstaluj dla systemu** zachowanie. Ta zmiana jest głównie umożliwia użytkownikowi końcowemu możliwość interakcji z instalacją podczas sekwencji zadań. Na przykład do uruchamiania procesu instalacji które monituje użytkownika końcowego dla różnych opcji. Niektóre instalatory aplikacji nie może mieć zignorowane monity użytkownika lub proces instalacji może wymagać tylko znane użytkownikowi wartości określonej konfiguracji. <!--1356976-->
        > 
        > Instalowanie w kontekście systemu i zezwolenie użytkownikom na interakcję z instalacji nie jest bezpieczną konfigurację. Aby uzyskać więcej informacji, zobacz [bezpieczeństwo i prywatność zarządzania aplikacjami](/sccm/apps/plan-design/security-and-privacy-for-application-management#bkmk_interact).

    -   **Maksymalny dozwolony czas wykonywania (w minutach)**: Określ maksymalny czas, który program powinien być wykonywany na komputerze klienckim. To ustawienie musi być liczbą całkowitą większą niż zero. Domyślne ustawienie to 120 minut.  

         Ta wartość jest używana do:  

        -   Monitorowania wyników typu wdrożenia.  

        -   Sprawdź, czy typ wdrożenia jest zainstalowany, gdy na urządzeniach klienckich są zdefiniowane okna obsługi. Jeśli okno obsługi, program uruchamia tylko wtedy, jeśli wystarczająco dużo czasu jest dostępna w oknie obsługi, aby pomieścić **maksymalny dozwolony czas wykonywania** ustawienie.  

        > [!IMPORTANT]  
        >  Może wystąpić konflikt, jeśli **maksymalny dozwolony czas wykonywania** jest większa od czasu zaplanowanego okna obsługi. Jeżeli użytkownik ustawi maksymalny czas wykonywania do okresu większa niż długość dowolnej z dostępnych okien obsługi, typ wdrożenia nie działa.  

    -   **Szacowany czas instalacji (w minutach)**: Określ szacowany czas instalacji typu wdrożenia. Użytkownicy widzą teraz w programie Software Center.  

    -   **Określ zachowanie określonych ponowny rozruch**: Określ akcję po instalacji. Dostępne są następujące opcje:  

        -   **Określ zachowanie na podstawie kodów powrotnych**: Obsługa ponownego uruchomienia na podstawie kodów skonfigurowanego na karcie kody powrotne. Wyświetla Centrum oprogramowania **może wymagać ponownego uruchomienia**. Jeśli użytkownik jest zalogowany podczas instalacji, zostanie poproszony w zależności od konfiguracji środowiska użytkownika wdrożenia.  

        -   **Nie określonej akcji**: Nie wymagany jest ponowny rozruch po zakończeniu instalacji. Centrum oprogramowania zgłosił, że ponowny rozruch komputera nie jest wymagane.  
        -   **Program instalacyjny oprogramowania może wymusić ponowne uruchomienie urządzenia**: Configuration Manager nie kontroluje ani zainicjować ponowne uruchomienie komputera, ale rzeczywista instalacja może to zrobić bez ostrzeżenia. Użyj tego ustawienia, aby zapobiec raportowania niepowodzenia instalacji, gdy Instalator inicjuje ponowne uruchomienie programu Configuration Manager. Wyświetla Centrum oprogramowania **może wymagać ponownego uruchomienia**.  

        -   **Klient programu Configuration Manager wymusi obowiązkowe ponowne uruchomienie urządzenia**: Menedżer konfiguracji wymusza ponowne uruchomienie urządzenia po pomyślnej instalacji. Centrum oprogramowania zgłosił, że ponowne uruchomienie jest wymagane. Jeśli użytkownik jest zalogowany podczas instalacji, zostanie poproszony w zależności od konfiguracji środowiska użytkownika wdrożenia.

### <a name="specify-requirements-for-the-deployment-type"></a>Określenie wymagań dotyczących typu wdrożenia  

1.  Na **wymagania** strony kreatora tworzenia typu wdrożenia wybierz **Dodaj** otworzyć **tworzenie wymagania** okna dialogowego i Dodaj nowe wymaganie.  

    > [!NOTE]  
    >  Możesz także dodać nowe wymagania na **wymagania** karcie *< Nazwa typu wdrożenia\>*  **właściwości** okno dialogowe.  

2.  W **kategorii** listy rozwijanej wybierz, czy wymaganie dotyczy urządzenia lub użytkownika. Wybierz **niestandardowy** Aby użyć poprzednio utworzonego warunku globalnego. Po wybraniu **niestandardowy**, można także **Utwórz** Aby utworzyć nowy warunek globalny. Aby uzyskać więcej informacji o warunkach globalnych, zobacz [tworzenie warunków globalnych](../../apps/deploy-use/create-global-conditions.md).  

    > [!IMPORTANT]  
    >  W przypadku wdrożenia aplikacji w kolekcji urządzeń, klient ignoruje wszystkie wymagania należącego do kategorii **użytkownika** i warunku **urządzenie podstawowe**.  
    >   
    >  Jeśli został użyty do utworzenia Windows pakiet i program lub zadanie sekwencji zawierającej systemu Windows 10 jako wymóg System Center 2012 R2 Configuration Manager SP1, a następnie uaktualnić do programu System Center Configuration Manager, wymagania dotyczące systemu Windows 10 mogą zostać usunięte. Aby rozwiązać ten problem, należy ponownie określić wymagania. Chociaż wymaganie został usunięty z wyświetlania wymagania, jest ono nadal przetwarzane prawidłowo na urządzeniach.  

3.  W **warunku** listy rozwijanej wybierz warunek, którego chcesz użyć do oceny, czy użytkownik lub urządzenie spełnia wymagania instalacyjne. Zawartość tej listy różni się w zależności od wybranej kategorii.  

4.  W **Operator** listy rozwijanej wybierz operator do użycia. Ten operator porównuje wybranego warunku z podaną wartością. Ocenia ona, czy użytkownik lub urządzenie spełnia wymagania instalacyjne. Dostępni Operatorzy różnią się w zależności od wybranego warunku.  

    > [!IMPORTANT]  
    >  Dostępne wymagania różnią się w zależności od typu urządzenia, która używa typu wdrożenia.  

5.  W **wartość** określ wartości do użycia. Wartości te, wraz z wybranym warunkiem i operator, sprawdzić, czy użytkownik lub urządzenie spełnia wymagania instalacyjne. Dostępne wartości różnią się w zależności od wybranego warunku i operatora.  

6.  Wybierz **OK** Aby zapisać wymaganie i zamknąć **tworzenie wymagania** okno dialogowe.  

### <a name="specify-dependencies-for-the-deployment-type"></a>Określenie zależności dotyczących typu wdrożenia  
 Zależności definiują jeden lub więcej typów wdrożeń z innej aplikacji, którą należy zainstalować przed zainstalowaniem typu wdrożenia. Można ustawić zależnych typów wdrożeń można automatycznie zainstalować przed zainstalowaniem typu wdrożenia.  

> [!IMPORTANT]  
>  W niektórych przypadkach typ wdrożenia jest zależny od typu wdrożenia, który również ma zależności. Maksymalna liczba obsługiwanych zależności w łańcuchu wynosi pięć.  

1.  Na **zależności** strony kreatora tworzenia typu wdrożenia wybierz **Dodaj**.  

    > [!IMPORTANT]  
    >  Można także dodać nowe zależności na **zależności** karcie *< Nazwa typu wdrożenia\>*  **właściwości** okno dialogowe.  

2.  W **Dodawanie zależności** oknie dialogowym wybierz **Dodaj**.  

3.  W **Określ wymaganą aplikację** okno dialogowe, wybierz istniejącą aplikację i jedno wdrożenie aplikacji typów do użycia jako zależność.  

    > [!TIP]  
    >  Możesz wybrać **widoku** Aby wyświetlić właściwości wybranej aplikacji lub typu wdrożenia.  

4.  Wybierz **OK** zamknąć **Określ wymaganą aplikację** okno dialogowe.  

5.  Jeśli chcesz, aby aplikacja zależna była instalowana automatycznie, wybierz opcję **automatyczna instalacja** obok aplikacji.  

    > [!NOTE]  
    >  Nie trzeba wdrożyć aplikację zależną, aby była instalowana automatycznie.  

6.  W **Dodawanie zależności** okno dialogowe, w obszarze **Nazwa grupy zależności**, wprowadź nazwę umożliwiającą odwoływanie się do tej grupy zależności aplikacji.  

7.  Można też użyć **Zwiększ priorytet** i **Zmniejsz priorytet** przycisków. Te akcje zmienić kolejność, w którym klient oceni poszczególne zależności.  

8.  Wybierz **OK** zamknąć **Dodawanie zależności** okno dialogowe.  

### <a name="confirm-the-deployment-type-settings-and-finish-the-wizard"></a>Potwierdzenie ustawień typu wdrożenia i Zakończ pracę kreatora  

1.  Przegląd **Podsumowanie**. Wybierz **dalej** do utworzenia typu wdrożenia. Wybierz **Wstecz** aby wrócić i zmienić ustawienia typu wdrożenia.  

2.  Po **postępu** Przejrzyj akcje wykonane przez kreatora, a następnie wybierz pozycję zakończenie, **Zamknij** aby zakończyć pracę kreatora.  

3.  Jeśli Kreator tworzenia typu wdrożenia został uruchomiony z Kreatora tworzenia aplikacji, możesz powrócić do **typy wdrożeń** strony kreatora tworzenia aplikacji.  



## <a name="set-up-additional-options-for-deployment-types-that-contain-virtual-applications"></a>Konfigurowanie dodatkowych opcji typów wdrożeń zawierających aplikacje wirtualne  
 Poniższe procedury umożliwiają konfigurowanie dodatkowych opcji typów wdrożeń, które obejmują aplikacje wirtualne.  

### <a name="set-up-content-options-for-application-virtualization-app-v-deployment-types"></a>Ustaw opcje zawartości dla typów wdrożeń Application Virtualization (App-V)  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **aplikacji**.  

2.  W **aplikacji** listy, wybierz aplikację, która ma typ wdrożenia programu App-V. Następnie na **Home** karcie **właściwości** grupy, wybierz **właściwości**.  

3.  W *< nazwa aplikacji\>*  **właściwości** na okna dialogowego **typy wdrożeń** karcie, wybierz typ wdrożenia programu App-V, a następnie wybierz **Edytuj**.  

4.  W *< Nazwa typu wdrożenia\>*  **właściwości** na okna dialogowego **zawartości** kartę, skonfiguruj następujące opcje, w razie potrzeby:  

    -   **Utrwal zawartość w pamięci podręcznej klienta**: Wybierz tę opcję, aby upewnić się, że zawartość dla tego typu wdrożenia nie zostanie usunięta z pamięci podręcznej klienta programu Configuration Manager.  

    -   **Załaduj zawartość do pamięci podręcznej programu App-V przed uruchomieniem**: Wybierz tę opcję, aby upewnić się, że cała zawartość dla aplikacji wirtualnej zostanie załadowana do pamięci podręcznej programu App-V przed uruchomieniem aplikacji. Tej opcji gwarantuje również, że zawartość aplikacji nie jest przypięty w pamięci podręcznej. Klient spowoduje usunięcie zawartości zgodnie z potrzebami.  

5.  Wybierz **OK** zamknąć *< Nazwa typu wdrożenia\>*  **właściwości** okno dialogowe.  

6.  Wybierz **OK** zamknąć *< nazwa aplikacji\>*  **właściwości** okno dialogowe.  

### <a name="set-up-publishing-options-for-app-v-deployment-types"></a>Ustawianie opcji typów wdrożeń App-V publikowania  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **aplikacji**.  

3.  W **aplikacji** listy, wybierz aplikację, która ma typ wdrożenia programu App-V. Następnie na **Home** karcie **właściwości** grupy, wybierz **właściwości**.  

4.  W *< nazwa aplikacji\>*  **właściwości** na okna dialogowego **typy wdrożeń** karcie, wybierz typ wdrożenia programu App-V, a następnie wybierz **Edytuj**.  

5.  W *< Nazwa typu wdrożenia\>*  **właściwości** na okna dialogowego **publikowania** , a następnie wybierz elementy aplikacji wirtualnej, który chcesz opublikować.  

6.  Wybierz **OK** zamknąć *< Nazwa typu wdrożenia\>*  **właściwości** okno dialogowe.  

7.  Wybierz **OK** zamknąć *< nazwa aplikacji\>*  **właściwości** okno dialogowe.  



## <a name="import-an-application"></a>Importuj aplikację  
 Użyj poniższej procedury, aby zaimportować aplikację do programu Configuration Manager. Aby uzyskać informacje o sposobie eksportowania aplikacji, zobacz [zadania zarządzania dla aplikacji programu System Center Configuration Manager](../../apps/deploy-use/management-tasks-applications.md).  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **Zarządzanie aplikacjami** > **aplikacji**.   

3.  Na **Home** karcie **Utwórz** grupy, wybierz **Importuj aplikację**.  

4.  Na **ogólne** strony **Kreatora importowania aplikacji**, wybierz **Przeglądaj**. Następnie określ ścieżkę sieciową do pliku zip z aplikacji do zaimportowania.  

5.  Na **zawartość pliku** wybierz działanie w przypadku aplikacji, którą próbowano zaimportować jest duplikatem istniejącej aplikacji. Możesz utworzyć nową aplikację lub zignorować duplikat i dodać nową poprawkę do istniejącej aplikacji.  

6.  Na **Podsumowanie** Przejrzyj akcje wykonywane, a następnie Zakończ pracę kreatora.  

 Nowa aplikacja pojawi się w węźle **Aplikacje**.  

> [!TIP]  
>  Polecenia cmdlet programu Windows PowerShell **Export-CMApplication** ma taką samą funkcję jak tej procedury. Aby uzyskać więcej informacji, zobacz [Export-CMApplication](https://docs.microsoft.com/powershell/module/configurationmanager/import-cmapplication?view=sccm-ps).  



##  <a name="deployment-types-supported-by-configuration-manager"></a>Typy wdrożeń obsługiwane przez program Configuration Manager  

|Nazwa typu wdrożenia|Więcej informacji|  
|--------------------------|----------------------|  
|**Instalator systemu Windows (\*pliku .msi)**|Tworzy typ wdrożenia na podstawie pliku Instalatora systemu Windows.|  
|**Pakiet aplikacji systemu Windows (\*appx, \*.appxbundle)**|Tworzy typ wdrożenia dla systemu Windows 8 lub nowszym. Wybierz plik pakietu aplikacji systemu Windows lub pakietu pakietu aplikacji systemu Windows.|  
|**Pakiet aplikacji systemu Windows (w Sklepie Windows)**|Tworzy typ wdrożenia dla systemu Windows 8 lub nowszym. Podaj łącze do aplikacji w Sklepie Windows lub przejdź do sklepu, aby wybrać aplikację.<br /><br /> Aby wdrożyć aplikację jako łącze do Sklepu Windows, należy skonfigurować ustawienie zasad grupy **Wyłącz aplikację sklep** do **wyłączone** lub **nieskonfigurowane**. Jeśli to ustawienie jest włączone, klienci nie mogą łączyć się ze sklepem Windows, aby pobrać i zainstalować aplikacje.<br /><br /> Typy wdrożeń systemu Windows 8 korzystające z linku do sklepu są zawsze oceniane przed innymi typami wdrożeń, niezależnie od ich priorytetu.|  
|**Instalator skryptowy**|Tworzy typ wdrożenia określający skrypt uruchamiany na urządzeniach klienckich w celu zainstalowania zawartości lub wykonaj akcję.|  
|**Microsoft Application Virtualization 4**|Tworzy typ wdrożenia na podstawie manifestu aplikacji Microsoft Application Virtualization 4|  
|**Microsoft Application Virtualization 5**|Tworzy typ wdrożenia na podstawie pliku pakietu aplikacji Microsoft Application Virtualization 5.|  
|**Pakiet aplikacji Windows Phone (\*plik xap)**|Tworzy typ wdrożenia na podstawie pliku pakietu aplikacji systemu Windows Phone.|  
|**Pakiet aplikacji Windows Phone (w Sklepie Windows Phone)**|Tworzy typ wdrożenia przez określenie linku do aplikacji w sklepie Windows Phone Store.|  
|**Pakiet aplikacji dla systemu iOS (\*plik IPA)**|Tworzy typ wdrożenia na podstawie pliku pakietu aplikacji dla systemu iOS.|  
|**Pakiet aplikacji dla systemu iOS ze sklepu z aplikacjami**|Tworzy typ wdrożenia za pośrednictwem łącza do aplikacji dla systemu iOS ze sklepu App Store.|  
|**Pakiet aplikacji dla systemu Android (\*pliku apk)**|Tworzy typ wdrożenia na podstawie pliku pakietu aplikacji dla systemu Android.|  
|**Pakiet aplikacji dla systemu Android w witrynie Google Play**|Tworzy typ wdrożenia za pośrednictwem łącza do aplikacji w witrynie Google Play.|  
|**Mac OS X**|Tworzy typ wdrożenia dla komputerów Mac na podstawie pliku *.cmmac, który został utworzony przy użyciu narzędzia CMAppUtil.<br /><br /> Dotyczy tylko na komputerach Mac, na którym jest uruchomiony klient programu Configuration Manager.|  
|**Aplikacja sieci Web**|Tworzy typ wdrożenia określający łącze do aplikacji sieci web. Typ wdrożenia instaluje skrót do aplikacji sieci web na urządzeniu użytkownika.<br /><br /> Jeśli zainstalowano program Microsoft Intune managed browser na urządzeniach Android lub iOS, upewnij się, że użytkowników tylko przy użyciu programu managed browser do otwarcia aplikacji. Użyj jednego z następujących formatów po określeniu łącza do wybranej aplikacji: Zastąp **http:** z **http-intunemam:** lub **https:** z **https-intunemam:**<br /><br /> - **http-intunemam: / / < ścieżka do aplikacji sieci web\>**<br /><br /> - **HTTPS-intunemam: / / < ścieżka do aplikacji sieci web\>**<br /><br /> Aby upewnić się, że aplikacje, które chcesz skojarzyć z przeglądarką zarządzaną są instalowane tylko na urządzeń iOS i Android, można użyć wymagań aplikacji programu Configuration Manager.<br /><br /> Aby uzyskać więcej informacji o usłudze Intune managed browser, zobacz [Zarządzanie Internetu dostępu za pomocą zasad programu managed browser](../../apps/deploy-use/manage-internet-access-using-managed-browser-policies.md).|  
|**Instalator Windows korzystający z zarządzania urządzeniami Przenośnymi (\*.msi)**|Ten typ Instalatora umożliwia tworzenie i wdrażanie aplikacji opartych na Instalatorze Windows na komputerach z systemem Windows 10.<br /><br /> W przypadku korzystania z instalatora tego typu należy wziąć pod uwagę następujące kwestie:<br><br>-Należy przekazać tylko pojedynczy plik z rozszerzeniem msi.<br /><br /> Kod produktu i wersja produktu pliku są używane do wykrywania aplikacji.<br /><br /> Domyślne zachowanie ponownego uruchamiania aplikacji jest używany. Menedżer konfiguracji nie kontroluje ponowne uruchomienie.<br /><br /> -Pakiety MSI użytkownika są zainstalowane dla pojedynczego użytkownika.<br /><br /> Pakiety MSI na maszynach są instalowane dla wszystkich użytkowników na urządzeniu.<br /><br /> -Pakiety MSI podwójne obecnie instalować tylko dla wszystkich użytkowników na urządzeniu.<br /><br /> — Aktualizacje aplikacji są obsługiwane, jeśli kod produktu MSI dla każdej wersji jest taki sam.|  



## <a name="next-steps"></a>Następne kroki

Po utworzeniu aplikacji w programie Configuration Manager, następnym krokiem jest [wdrożyć aplikację](/sccm/apps/deploy-use/deploy-applications).