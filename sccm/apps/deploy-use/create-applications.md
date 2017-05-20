---
title: Tworzenie aplikacji | Dokumentacja firmy Microsoft
description: "Tworzenie i wdrażanie aplikacji i typów wdrożeń z System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cc230ff4-7056-4339-a0a6-6a44cdbb2857
caps.latest.revision: 14
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9097014c7e988ec8e139e518355c4efb19172b3
ms.openlocfilehash: da86fc2f61ce8229fb0d3f58a4f8a24d1514b30e
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="create-applications-with-system-center-configuration-manager"></a>Tworzenie aplikacji z System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Aplikacji programu System Center Configuration Manager zawiera pliki i informacje niezbędne do wdrożenia oprogramowania na urządzeniu. Aplikacja ma co najmniej jeden typ wdrożenia obejmujący pliki instalacyjne oraz informacje niezbędne do zainstalowania oprogramowania. Typu wdrożenia zawiera również zasady określające czas i sposób wdrożenia oprogramowania.  

 Możesz tworzyć aplikacje przy użyciu następujących metod:  

-   Automatyczne utworzenie aplikacji i typów wdrożenia przez odczytanie plików instalacyjnych aplikacji.  

-   ręczne utworzenie aplikacji, a następnie dodanie typów wdrożenia.  

-   Importowanie aplikacji z pliku.  

> [!NOTE]  
>  [Tworzenie aplikacji dla urządzeń przenośnych ](../../mdm/deploy-use/create-applications.md) zawiera szczegółowe informacje o tworzeniu aplikacji systemu Android, Windows Phone oraz iOS.  

Poniższe kroki umożliwia tworzenie aplikacji programu Configuration Manager i typów wdrożeń.  

## <a name="start-the-create-application-wizard"></a>Uruchom Kreatora tworzenia aplikacji  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **zarządzania aplikacjami** > **aplikacji**.  

3.  Na **Home** w karcie **Utwórz** grupy, wybierz **tworzenie aplikacji**.  

## <a name="specify-whether-you-want-to-automatically-detect-application-information-or-manually-define-the-information"></a>Określ, czy chcesz automatycznie wykrywać informacje o aplikacji lub definiować ręcznie informacje  

-   Automatyczne wykrywanie informacji o aplikacji, gdy chcesz utworzyć prostą aplikację mającą jeden typ wdrożenia, takich jak plik Instalatora Windows, który bez zależności lub wymagań. Po utworzeniu aplikacji przy użyciu tej procedury można ją edytować w miarę potrzeby, aby dodawać lub zmieniać typy wdrożeń oraz dodawać metody wykrywania, zależności lub wymagania.  

-   Ręcznie określ informacje o aplikacji, aby utworzyć bardziej złożone aplikacje mające wiele typów wdrożeń, zależności, metod wykrywania lub wymagań.  

### <a name="automatically-detect-application-information"></a>Automatycznie wykryj informacje o aplikacji  

1.  Na **ogólne** strona kreatora tworzenia aplikacji wybierz **automatycznie Wykryj informacje o tej aplikacji z plików instalacyjnych**.  

2.  W **typu** listy rozwijanej, wybierz typ pliku instalacyjnego aplikacji którego chcesz użyć do wykrywania informacji o aplikacji. Informacje o dostępnych typach instalacji znajdują się w sekcji [Typy wdrożeń obsługiwane przez program Configuration Manager](/sccm/apps/deploy-use/create-applications#deployment-types-supported-by-configuration-manager) w tym temacie.  

3.  W **lokalizacji** Określ ścieżkę UNC (w postaci  *\\ \\serwera\\udostępnianie\\\filename*) lub łącze do pliku instalacyjnego aplikacji, którego chcesz używać do wykrywania informacji o aplikacji magazynu. Można też kliknąć przycisk **Przeglądaj**, aby przejść do lokalizacji pliku instalacyjnego.  

    > [!IMPORTANT]  
    >  Po wybraniu **Instalatora Windows (\*pliku .msi)** jako typu aplikacji wszystkie pliki w folderze określonym przez użytkownika zostaną zaimportowane z aplikacją i zostanie wysłany do punktów dystrybucji. Upewnij się, że folder zostanie zawiera tylko pliki, które są niezbędne do zainstalowania aplikacji. Menedżer konfiguracji został sprawdzony pod kątem obsługi maksymalnie 20 000 plików aplikacji w pakiecie aplikacji. Jeśli aplikacja ma więcej plików, należy rozważyć utworzenie wielu aplikacji zawierających mniejszą liczbę plików.  

    >  Musi mieć dostęp do ścieżki UNC aplikacji i wszelkich podfolderów z zawartością aplikacji.  

4.  Na **Importuj informacje** strona kreatora tworzenia aplikacji przejrzyj informacje, które zostały zaimportowane, a następnie wybierz **dalej**. Jeśli konieczne, można wybrać **Wstecz** przejść wstecz i naprawić wszystkie błędy.  

5.  Na **ogólne informacje** strona kreatora tworzenia aplikacji Podaj następujące informacje:  

    > [!NOTE]  
    >  Niektóre z tych informacji mogą już być podane, jeśli zostały uzyskane automatycznie z plików instalacyjnych aplikacji. Wyświetlane opcje mogą się ponadto różnić w zależności od typu tworzonej aplikacji.  

    -   Ogólne informacje o aplikacji, takie jak nazwa aplikacji, komentarze, wersja i opcjonalne informacje w celu znalezienia aplikacji w konsoli programu Configuration Manager.  

    -   **Program instalacyjny**— Określ program instalacyjny oraz wszelkie wymagane właściwości niezbędne do zainstalowania typu wdrożenia aplikacji.  

        > [!TIP]  
        >  Jeśli program instalacyjny nie jest wyświetlany, wybierz **Przeglądaj** i przejdź do lokalizacji programu instalacyjnego.  

    -   **Zachowanie podczas instalowania**— Określ, czy typ wdrożenia aplikacji zostanie zainstalowany tylko dla obecnie zalogowanego użytkownika lub dla wszystkich użytkowników. Można również określić, czy typ wdrożenia zostanie zainstalowany dla wszystkich użytkowników w przypadku wdrożenia na urządzeniu lub tylko do określonego użytkownika w przypadku jest wdrażana dla użytkownika.  

    -   **Użyj automatycznego połączenia VPN (jeśli jest skonfigurowane)**— Jeśli profil sieci VPN został wdrożony na urządzeniu, na którym uruchomiono aplikację, uruchom połączenie sieci VPN po uruchomieniu aplikacji (Windows 8.1 i Windows Phone 8.1 tylko).  

         Na urządzeniach Windows Phone 8.1 automatyczne połączenia VPN nie są obsługiwane, jeśli więcej niż jeden profil sieci VPN został wdrożony na urządzeniu.  

         Aby uzyskać więcej informacji o profilach VPN, zobacz [profile sieci VPN](../../protect/deploy-use/vpn-profiles.md).  

6.  Wybierz **dalej**, przejrzyj informacje o aplikacji na **Podsumowanie** strony, a następnie Zakończ pracę Kreatora tworzenia aplikacji.  

Nowa aplikacja pojawi się w **aplikacji** węźle konsoli programu Configuration Manager, a ukończeniu tworzenia aplikacji. Informacje o dodawaniu większej liczby typów wdrożenia do aplikacji znajdują się w sekcji [Tworzenie typów wdrożenia aplikacji](/sccm/apps/deploy-use/create-applications#create-deployment-types-for-the-application) w tym temacie.  

### <a name="manually-specify-application-information"></a>Ręcznie określ informacje o aplikacji  

1.  Na **ogólne** strona kreatora tworzenia aplikacji wybierz **ręcznie określić informacje o aplikacji**, a następnie wybierz **dalej**.  

2.  Określ ogólne informacje o aplikacji, takie jak nazwa aplikacji, komentarze, wersja i opcjonalne informacje ułatwiają znajdowanie aplikacji w konsoli programu Configuration Manager.  

3.  Na **katalogu aplikacji** strona kreatora tworzenia aplikacji Podaj następujące informacje:  

    -   **Wybrany język**— z listy rozwijanej wybierz wersję językową aplikacji, którą chcesz skonfigurować. Wybierz **Dodaj lub usuń** Aby skonfigurować więcej języków aplikacji.  

    -   **Zlokalizowana nazwa aplikacji**— Określ nazwę aplikacji w języku wybranym **wybrany język** listy rozwijanej.  

        > [!IMPORTANT]  
        >  Podaj zlokalizowaną nazwę aplikacji dla każdej wersji językowej, który został ustawiony.  

    -   **Kategorie użytkowników**--wybierz **edytować** Aby określić kategorie aplikacji w języku wybranym **wybrany język** listy rozwijanej. Użytkownicy Centrum oprogramowania mogą używać owych wybranych kategorii do filtrowania i sortowania dostępnych aplikacji.  

    -   **Dokumentacja użytkownika**--wybierz **Przeglądaj** Aby określić adres URL lub UNC ścieżkę i nazwę pliku, który może odczytać użytkowników w programie Software Center, aby uzyskać więcej informacji o tej aplikacji.  

    -   **Tekst łącza**— Określ tekst wyświetlany zamiast adresu URL aplikacji.  

    -   **Adres URL aplikacji prywatności**— Określ adres URL prowadzący do zasad zachowania poufności informacji dla aplikacji.  

    -   **Zlokalizowany opis**--wprowadź opis dla tej aplikacji w języku wybranym **wybrany język** listy rozwijanej.  

    -   **Słowa kluczowe**--wprowadź listę słów kluczowych w języku wybranym **wybranego języka** listy rozwijanej. Słowa kluczowe ułatwią użytkownikom wyszukiwanie Centrum oprogramowania dla aplikacji.  

    -   **Ikona**--wybierz **Przeglądaj** aby wybrać ikonę tej aplikacji spośród dostępnych ikon. Jeśli nie określisz ikony, ikona domyślna będzie używany dla tej aplikacji.  

    -   **Wyświetlaj jako polecaną aplikację i wyróżnij w portalu firmy**— wybierz tę opcję, aby wyróżnić aplikację w portalu firmy.  

4.  Na **typy wdrożeń** strona kreatora tworzenia aplikacji wybierz **Dodaj** Aby utworzyć nowy typ wdrożenia.  

 Aby uzyskać więcej informacji, zobacz [tworzenia typów wdrożenia dla aplikacji](/sccm/apps/deploy-use/create-applications#create-deployment-types-for-the-application).  

5.  Wybierz **dalej**, przejrzyj informacje o aplikacji na **Podsumowanie** strony, a następnie Zakończ pracę Kreatora tworzenia aplikacji.  

Nowa aplikacja pojawi się w **aplikacji** węzeł konsoli programu Configuration Manager.  

##  <a name="create-deployment-types-for-the-application"></a>Tworzenie typów wdrożenia aplikacji  
 W przypadku wybrania **automatycznie Zidentyfikuj informacje o tym typie wdrożenia z plików instalacyjnych** na **ogólne** strona kreatora tworzenia typu wdrożenia może nie być konieczny na zakończenie niektórych czynności następujących procedur.  

## <a name="start-the-create-deployment-type-wizard"></a>Uruchomienie Kreatora tworzenia typu wdrożenia  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **zarządzania aplikacjami** > **aplikacji**.  

3.  Wybierz aplikację, a następnie na **Home** w karcie **aplikacji** grupy, wybierz **Utwórz typ wdrożenia**.  

> [!TIP]  
>  Można również uruchomić Kreatora tworzenia typu wdrożenia z Kreatora tworzenia aplikacji i **typy wdrożeń** na karcie *< nazwa aplikacji\>*  **właściwości** okno dialogowe.  

## <a name="specify-whether-you-want-to-automatically-detect-deployment-type-information-or-manually-set-up-the-information"></a>Określ, czy chcesz automatycznie Wykryj informacje o typie wdrożenia, lub ręcznie ustawić informacje  
 Należy użyć jednej z następujących procedur, aby wykrywać automatycznie lub ręcznie skonfigurować informacje o typie wdrożenia.  

### <a name="automatically-detect-deployment-type-information"></a>Automatycznie wykryj informacje o typie wdrożenia  

1.  Na **ogólne** Kreatora tworzenia typu wdrożenia wybierz opcję **automatycznie Zidentyfikuj informacje o tym typie wdrożenia z plików instalacyjnych**.  

2.  W **typu** wybierz typ pliku instalacyjnego aplikacji, którego chcesz użyć do wykrywania informacji o typie wdrożenia.  

3.  W **lokalizacji** Określ ścieżkę UNC (w postaci  *\\ \\serwera\\udostępnianie\\filename*) lub określ łącze do magazynu zawierającego pliki instalacyjne aplikacji oraz zawartość, której chcesz użyć do wykrywania informacji o typie wdrożenia. Można również wybrać **Przeglądaj** zlokalizować pliku instalacyjnego.  

    > [!NOTE]  
    >  Musi mieć dostęp do ścieżki UNC aplikacji i wszelkich podfolderów z zawartością aplikacji.  

4.  Na **Importuj informacje** strona kreatora tworzenia typu wdrożenia Przejrzyj informacje, które zostały zaimportowane, a następnie wybierz **dalej**. Można również wybrać **Wstecz** przejść wstecz i naprawić wszystkie błędy.  

5.  Na **ogólne informacje** strona kreatora tworzenia typu wdrożenia Podaj następujące informacje:  

    > [!NOTE]  
    >  Niektóre informacje o typie wdrożenia mogą już być obecne, jeśli zostały odczytane z plików instalacyjnych aplikacji. Ponadto wyświetlane opcje mogą się różnić, w zależności od tworzonego typu wdrożenia.  

    -   Ogólne informacje o typie wdrożenia, takie jak nazwa, komentarze administratora oraz dostępne języki.  

    -   **Program instalacyjny**— Określ program instalacyjny i wszystkie właściwości, które są potrzebne do zainstalowania typu wdrożenia.  

    -   **Zachowanie podczas instalowania**— Określ, czy do zainstalowania typu wdrożenia dla bieżącego użytkownika lub dla wszystkich użytkowników. Można również określić, czy do zainstalowania typu wdrożenia dla wszystkich użytkowników, jeśli jest wdrażana na urządzeniu, lub czy ma być zainstalowany dla użytkownika tylko wtedy, gdy jest wdrażana dla użytkownika.  

    -   **Użyj automatycznego połączenia VPN (jeśli jest skonfigurowane)**— Jeśli profil sieci VPN został wdrożony na urządzeniu, na którym uruchomiono aplikację, uruchom połączenie sieci VPN po uruchomieniu aplikacji (Windows 8.1 i Windows Phone 8.1 tylko). Jeśli wiele profilów sieci VPN wdrożonych na urządzeniu Windows 8.1, pierwszy profilu VPN jest używany domyślnie.  

         Na urządzeniach Windows Phone 8.1 automatyczne połączenia VPN nie są obsługiwane, jeśli więcej niż jeden profil sieci VPN został wdrożony na urządzeniu.  

         Aby uzyskać więcej informacji o profilach VPN, zobacz [profile sieci VPN w programie System Center Configuration Manager](../../protect/deploy-use/vpn-profiles.md).  

6.  Wybierz **dalej**, a następnie przejdź do [określenie opcji zawartości typu wdrożenia](/sccm/apps/deploy-use/create-applications#specify-content-options-for-the-deployment-type).  

### <a name="manually-set-up-the-deployment-type-information"></a>Ręczne konfigurowanie informacji o typie wdrożenia  

1.  Na **ogólne** Kreatora tworzenia typu wdrożenia wybierz opcję **ręcznie określić informacje o typie wdrożenia**.  

2.  W **typu** , wybierz typ pliku instalacyjnego aplikacji, którego chcesz użyć do wykrywania informacji o typie wdrożenia. Można wybrać typy instalacji używane w przypadku automatycznego wykrywania informacji o typie wdrożenia, a także można określić skrypt instalacji typu wdrożenia.  

3.  Na **ogólne informacje** strona kreatora tworzenia typu wdrożenia Określ nazwę typu wdrożenia, opcjonalny opis oraz języki, w których chcesz udostępnić tego typu wdrożenia, a następnie wybierz **dalej**.  

4.  Przejdź do sekcji [Określenie opcji zawartości typu wdrożenia](/sccm/apps/deploy-use/create-applications#specify-content-options-for-the-deployment-type).  

##  <a name="specify-content-options-for-the-deployment-type"></a>Określenie opcji zawartości typu wdrożenia  

1.  Na **zawartości** strona kreatora tworzenia typu wdrożenia Podaj następujące informacje:  

    -   **Lokalizacja zawartości**— Określ lokalizację zawartości dla tego typu wdrożenia, lub wybierz **Przeglądaj** wybrać folder zawartości typu wdrożenia.  

        > [!IMPORTANT]  
        >  To konto systemu komputera serwera lokacji musi mieć uprawnienia do określonej lokalizacji zawartości.  

    -   **Zachowania zawartości w pamięci podręcznej klienta**— wybierz tę opcję, aby określić, czy zawartość powinna być przechowywana w pamięci podręcznej komputera klienta przez czas nieokreślony, nawet jeśli został już uruchomiony. Ta opcja może być przydatna w przypadku niektórych wdrożeń, takich jak Instalator Windows oparte na oprogramowaniu, które wymaga kopii lokalnej była dostępna do zastosowania aktualizacji, jednak będą zmniejszenia ilości dostępnej pamięci podręcznej. Wybierz tę opcję, może spowodować duże niepowodzenie wdrożenia w późniejszym czasie pamięci podręcznej nie ma wystarczająco dużo miejsca.  

    -   **Zezwalaj klientom na współużytkowanie zawartości z innymi klientami w tej samej podsieci**— wybierz tę opcję, aby zmniejszyć obciążenie sieci, zezwalając klientom na pobieranie zawartości z innych klientów lokalnych w sieci, w których znajduje się już pobrana zawartość w pamięci podręcznej. Ta opcja korzysta z technologii Windows BranchCache.  

    -   **Program instalacyjny**— Określ nazwę programu instalacyjnego oraz wszelkie wymagane parametry instalacji lub wybierz **Przeglądaj** zlokalizować pliku instalacyjnego.  

    -   **Instalacja rozpocznie się za**— Opcjonalnie określ folder zawierający program instalacyjny typu wdrożenia. Ten folder może być ścieżką bezwzględną na kliencie lub ścieżką do folderu punktu dystrybucji, który zawiera pliki instalacyjne.  

    -   **Program dezinstalacyjny**— opcjonalnie, określ nazwę programu dezinstalacyjnego oraz wszelkie wymagane parametry lub wybierz **Przeglądaj** go zlokalizować.  

    -   **Dezinstalacja rozpocznie się za**— Opcjonalnie określ folder zawierający program dezinstalacyjny typu wdrożenia. Ten folder może być ścieżką bezwzględną na kliencie lub ścieżką względną do folderu punktu dystrybucji, który zawiera pakiet.  

    -   **Uruchom program instalacyjny i dezinstalacyjny jako proces 32-bitowy na klientach 64-bitowych**--umożliwia 32-bitowego lokalizacje plików i rejestru na komputerach z systemem Windows uruchom program instalacyjny typu wdrożenia.  

2.  Wybierz **dalej**.  

## <a name="set-up-detection-methods-to-indicate-the-presence-of-the-deployment-type-windows-pcs-only"></a>Konfigurowanie metod wykrywania obecności typu wdrożenia (tylko komputery z systemem Windows)  
 Ta procedura konfiguruje metodę wykrywania, która wskazuje, czy typ wdrożenia jest już zainstalowany.  

1.  Na **metodę wykrywania** Kreatora tworzenia typu wdrożenia wybierz opcję **Skonfiguruj reguły wykrywania obecności tego typu wdrożenia**, a następnie wybierz **Dodaj klauzulę**.  

    > [!NOTE]  
    >  Można również wybrać opcję **Użyj skryptu niestandardowego do wykrycia obecności tego typu wdrożenia**. Aby uzyskać więcej informacji, zobacz [Używanie skryptu niestandardowego do sprawdzania obecności typu wdrożenia](/sccm/apps/deploy-use/create-applications#Use-a-custom-script-to-check-for-the-presence-of-a-deployment-type).  

2.  W oknie dialogowym **Reguła wykrywania** z listy rozwijanej **Typ ustawienia** wybierz metodę, której chcesz używać do wykrywania obecności typu wdrożenia. Można wybrać jedną z następujących metod:  

    -   **System plików**— ta metoda służy do wykrywania, czy określony plik lub folder istnieje na urządzeniu klienckim, co wskazuje, że aplikacja jest zainstalowana.  

        > [!NOTE]  
        >  **System plików** typu nie obsługuje określania ścieżki UNC do udziału sieciowego w polu Ścieżka. Na urządzeniu klienta można określić wyłącznie ścieżkę lokalną.  
        >   
        >  Aby sprawdzić lokalizacje plików 32-bitowych pod kątem określonego pliku lub folderu, wybierz opcję **ten plik lub folder jest skojarzony z aplikacją 32-bitowych w systemach 64-bitowych** pierwszy. Jeśli plik lub folder nie zostaną znalezione, zostaną przeszukane lokalizacje plików 64-bitowych.  

    -   **Rejestr**--wykryć, czy istnieje określony klucz rejestru lub wartość rejestru na urządzeniu klienckim, co wskazuje, że aplikacja jest zainstalowana przy użyciu tej metody.  

        > [!NOTE]  
        >  Aby sprawdzić lokalizacje 32-bitowego rejestru dla określonego klucza rejestru, wybierz opcję **ten klucz rejestru jest skojarzony z aplikacją 32-bitowych w systemach 64-bitowych** pierwszy. Jeśli klucz rejestru nie zostaną znaleziony, zostaną przeszukane lokalizacje plików 64-bitowych.  

    -   **Instalator Windows**— ta metoda służy do wykrywania, czy na urządzeniu klienckim, co wskazuje, że aplikacja jest zainstalowana istnieje określony plik Instalatora Windows.  

3.  Określ szczegóły element, którego chcesz użyć do wykrycia, czy zainstalowana jest tego typu wdrożenia. Możesz na przykład użyć pliku, folderu, klucza rejestru, wartości rejestru lub kodu produktu Instalatora Windows.  

4.  Określ szczegóły dotyczące wartości, którą chcesz ocenić na podstawie pozycji użytej do wykrycia, czy dany typ wdrożenia został zainstalowany. Na przykład, jeśli plik jest używany do sprawdzania, czy typ wdrożenia został zainstalowany, możesz wybrać **aby wskazywanie obecności tej aplikacji w systemie docelowym musi istnieć ustawienie systemu plików**.  

5.  Wybierz **dalej** zamknąć **reguły wykrywania** okno dialogowe.  

###  <a name="use-a-custom-script-to-check-for-the-presence-of-a-deployment-type"></a>Używanie skryptu niestandardowego do sprawdzania obecności typu wdrożenia  

1.  Na **metodę wykrywania** Kreatora tworzenia typu wdrożenia wybierz opcję **Używanie skryptu niestandardowego do wykrycia obecności tego typu wdrożenia** polu, a następnie wybierz **edytować**.  

2.  W oknie dialogowym **Edytor skryptów** z listy rozwijanej **Typ skryptu** wybierz język skryptu, którego chcesz używać do wykrywania obecności typu wdrożenia.  

3.  W **skryptu zawartość** wprowadź skrypt, którego chcesz użyć. Możesz również wkleić w tym polu zawartość istniejącego skryptu, lub **Otwórz** aby przejść do istniejącego zapisanego skryptu. Program Configuration Manager sprawdza wyniki skryptu, odczytując wartości, które są zapisywane do strumienia wyjściowego Standard Out (STDOUT), strumień wyjściowy Standard Error (STDERR) oraz kod zakończenia ze skryptu. Jeśli kod zakończenia ma wartość niezerową, oznacza to, że działanie skryptu zakończyło się niepowodzeniem, a stan wykrywania aplikacji jest nieznany. Jeśli kod zakończenia ma wartość zero i STDOUT zawiera dane, stan wykrywania aplikacji jest zainstalowany.  

 Skorzystaj z poniższej tabeli, aby zobaczyć, jak używać wyjściowym skryptu do sprawdzania, czy aplikacja jest zainstalowana.  

|Kod zakończenia skryptu|Szczegóły|
|--------------------------------|-----------------|
|0|**Dane odczytane ze strumienia wyjściowego STDOUT**— pusty<br /><br /> **Dane odczytane ze strumienia wyjściowego STDERR**— pusty<br /><br /> **Wynik skryptu**— Powodzenie<br /><br /> **Stan wykrywania aplikacji**--nie jest zainstalowany|  
|0|**Dane odczytane ze strumienia wyjściowego STDOUT**— pusty<br /><br /> **Dane odczytane ze strumienia wyjściowego STDERR**--nie jest pusty<br /><br /> **Wynik skryptu**— błąd<br /><br /> **Stan wykrywania aplikacji**— nieznany|  
|0|**Dane odczytane ze strumienia wyjściowego STDOUT**--nie jest pusty<br /><br /> **Dane odczytane ze strumienia wyjściowego STDERR**— pusty<br /><br /> **Wynik skryptu**— Powodzenie<br /><br /> **Stan wykrywania aplikacji**--zainstalowany|  
|0|**Dane odczytane ze strumienia wyjściowego STDOUT**--nie jest pusty<br /><br /> **Dane odczytane ze strumienia wyjściowego STDERR**--nie jest pusty<br /><br /> **Wynik skryptu**— Powodzenie<br /><br /> **Stan wykrywania aplikacji**--zainstalowany|  
|Wartość niezerowa|**Dane odczytane ze strumienia wyjściowego STDOUT**— pusty<br /><br /> **Dane odczytane ze strumienia wyjściowego STDERR**— pusty<br /><br /> **Wynik skryptu**— błąd<br /><br /> **Stan wykrywania aplikacji**— nieznany|  
|Wartość niezerowa|**Dane odczytane ze strumienia wyjściowego STDOUT**— pusty<br /><br /> **Dane odczytane ze strumienia wyjściowego STDERR**--nie jest pusty<br /><br /> **Wynik skryptu**— błąd<br /><br /> **Stan wykrywania aplikacji**— nieznany|  
|Wartość niezerowa|**Dane odczytane ze strumienia wyjściowego STDOUT**--nie jest pusty<br /><br /> **Dane odczytane ze strumienia wyjściowego STDERR**— pusty<br /><br /> **Wynik skryptu**— błąd<br /><br /> **Stan wykrywania aplikacji**— nieznany|  
|Wartość niezerowa|**Dane odczytane ze strumienia wyjściowego STDOUT**--nie jest pusty<br /><br /> **Dane odczytane ze strumienia wyjściowego STDERR**--nie jest pusty<br /><br /> **Wynik skryptu**— błąd<br /><br /> **Stan wykrywania aplikacji**— nieznany|  

Poniższa tabela zawiera Microsoft Visual Basic (VB) przykładowe skrypty, które można użyć do napisania własnych skryptów wykrywania aplikacji.  

|Przykładowy skrypt Visual Basic|Opis|  
|--------------------------------|-----------------|  
|**WScript.Quit(1)**|Skrypt zwraca kod zakończenia o wartości innej niż zero, co oznacza, że jego niepomyślne wykonanie. W takiej sytuacji stan wykrywania aplikacji będzie nieznany.|  
|**WScript.StdErr.Write "Skryptu nie powiodło się"**<br /><br /> **WScript.Quit(0)**|Skrypt zwraca kod zakończenia o wartości wynoszącej zero, jednak wartość strumienia wyjściowego STDERR nie będzie pusta, co oznacza niepomyślne wykonanie skryptu. W takiej sytuacji stan wykrywania aplikacji będzie nieznany.|  
|**WScript.Quit(0)**|Skrypt zwraca kod zakończenia o wartości zero, co oznacza jego pomyślne wykonanie. Wartość strumienia wyjściowego STDOUT jest jednak pusta, co oznacza, że aplikacja nie jest zainstalowana.|  
|**WScript.StdOut.Write "aplikacja jest zainstalowana"**<br /><br /> **WScript.Quit(0)**|Skrypt zwraca kod zakończenia o wartości zero, co oznacza jego pomyślne wykonanie. Wartość strumienia wyjściowego STDOUT nie jest pusta, co oznacza, że aplikacja jest zainstalowana.|  
|**WScript.StdOut.Write "aplikacja jest zainstalowana"**<br /><br /> **WScript.StdErr.Write "Ukończone"**<br /><br /> **WScript.Quit(0)**|Skrypt zwraca kod zakończenia o wartości zero, co oznacza jego pomyślne wykonanie. Wartości strumieni wyjściowych STDOUT i STDERR nie są puste, co oznacza, że aplikacja jest zainstalowana.|  

 > [!NOTE]  
 >  Maksymalny rozmiar skryptu, jakiego można użyć, to 32 kilobajty (KB).  

4.  Wybierz **OK** zamknąć **Edytor skryptów** okno dialogowe.  

## <a name="specify-user-experience-options-for-the-deployment-type"></a>Określenie opcji czynności użytkownika dotyczących typu wdrożenia  
 Te ustawienia określają, jak aplikacja zostanie zainstalowana na urządzeniach i jakie będą wyświetlane dla użytkownika.  

1.  Na **środowisko użytkownika** strona kreatora tworzenia typu wdrożenia Podaj następujące informacje:  

    -   **Zachowanie podczas instalacji**— z listy rozwijanej wybierz jedną z następujących opcji:  

        -   **Zainstaluj dla użytkownika**— aplikacja zostanie zainstalowana tylko dla użytkownika, do którego aplikacja jest wdrażana.  

        -   **Zainstaluj dla systemu**— aplikacja zostanie zainstalowana tylko raz i będzie dostępna dla wszystkich użytkowników.  

        -   **Zainstaluj dla systemu, jeśli zasób jest urządzeniem; w przeciwnym razie zainstaluj dla użytkownika**— Jeśli aplikacja jest wdrażana na urządzeniu, zostanie zainstalowany dla wszystkich użytkowników. Jeśli aplikacja jest wdrażana dla użytkownika, zostanie ona zainstalowana tylko dla tego użytkownika.  

    -   **Wymagane zalogowanie**— Określ wymagania dotyczące logowania dla tego typu wdrożenia przy użyciu następujących opcji:  

        -   **Tylko wtedy, gdy użytkownik jest zalogowany**  

        -   **Określa, czy użytkownik jest zalogowany**  

        -   **Tylko wtedy, gdy żaden użytkownik nie jest zalogowany**  

        > [!NOTE]  
        >  Domyślnie ta opcja **tylko wtedy, gdy użytkownik jest zalogowany**, i nie można zmienić, jeśli został wybrany **zainstaluj dla użytkownika** w **zachowanie podczas instalacji** listy rozwijanej.  

    -   **Widoczność programu instalacyjnego**— Określ tryb, w którym typ wdrażania będzie uruchamiany na urządzeniach klienckich. Dostępne są następujące opcje:  

        -   **Zmaksymalizowane**— typ wdrożenia zostanie uruchomiony w trybie zmaksymalizowanym na urządzeniach klienckich. Użytkownicy będą widzieć wszystkie działania instalacyjne.  

        -   **Normalny**— typ wdrożenia zostanie uruchomiony w trybie normalnym na podstawie ustawień domyślnych systemu i programu. Jest to tryb domyślny.  

        -   **Zminimalizowane**— typ wdrożenia zostanie uruchomiony w trybie zminimalizowanym na urządzeniach klienckich. Użytkownicy mogą widzieć działania instalacyjne w obszarze powiadomień lub na pasku zadań.  

        -   **Ukryte**— typ wdrożenia zostanie ukryta na urządzeniach klienckich, a użytkownicy będą widzieć żadnych działań instalacyjnych.  

    -   **Zezwalaj użytkownikom na wyświetlanie i interakcję z instalacji programu**— Określ, czy użytkownik może interakcyjnie przeprowadzić instalację typu wdrożenia, aby skonfigurować opcje instalacji.  

        > [!NOTE]  
        >  Ta opcja jest włączona domyślnie w przypadku wybrania **zainstaluj dla użytkownika** opcję w **zachowanie podczas instalacji** listy rozwijanej.  

    -   **Maksymalny dozwolony czas wykonywania (w minutach)**— Określ maksymalny czas, który program powinien uruchomić na komputerze klienckim. To ustawienie musi być liczbą całkowitą większą niż zero. Domyślne ustawienie to 120 minut.  

         Ta wartość jest używana do:  

        -   Monitorowania wyników typu wdrożenia.  

        -   Sprawdź, czy typ wdrożenia zostanie zainstalowany podczas na urządzeniu klienckim są zdefiniowane okna obsługi. Jeśli okno obsługi w miejscu, program zostanie uruchomiony tylko wtedy, gdy jest wystarczająco dużo czasu, jest dostępna w oknie obsługi, aby dopasować **maksymalny dozwolony czas wykonywania** ustawienie.  

        > [!IMPORTANT]  
        >  Może wystąpić konflikt, jeśli **maksymalny dozwolony czas wykonywania** jest większa od czasu zaplanowanego okna obsługi. Jeśli maksymalny czas wykonywania ustawiony przez użytkownika będzie większy od długości każdego z dostępnych okien obsługi, typ wdrożenia nie zostanie uruchomiony.  

2.  **Szacowany czas instalacji (w minutach)**— Określ szacowany czas trwania instalacji typu wdrożenia. Ta informacja będzie wyświetlana użytkownikom Centrum oprogramowania.  

## <a name="specify-requirements-for-the-deployment-type"></a>Określenie wymagań dotyczących typu wdrożenia  

1.  Na **wymagania** strona kreatora tworzenia typu wdrożenia wybierz **Dodaj** otworzyć **tworzenie wymagania** okna dialogowego i dodać nowe wymaganie.  

    > [!NOTE]  
    >  Możesz także dodać nowe wymagania na **wymagania** na karcie *< Nazwa typu wdrożenia\>*  **właściwości** okno dialogowe.  

2.  Z listy rozwijanej **Kategoria** wybierz, czy wymaganie dotyczy urządzenia, czy użytkownika, lub wybierz opcję **Niestandardowe**, aby użyć poprzednio utworzonego warunku globalnego. Po wybraniu **niestandardowy**, można także **Utwórz** Aby utworzyć nowy warunek globalny. Aby uzyskać więcej informacji o warunkach globalnych, zobacz [tworzenie warunków globalnych](../../apps/deploy-use/create-global-conditions.md).  

    > [!IMPORTANT]  
    >  Wszelkie wymagania z kategorii **użytkownika** oraz warunku **urządzenie podstawowe** zostanie zignorowana w przypadku wdrażania aplikacji w kolekcji urządzeń.  
    >   
    >  Jeśli utworzono pakiet systemu Windows oraz program lub sekwencję zadań wymagającą systemu Windows 10 przy użyciu programu System Center 2012 R2 Configuration Manager SP1, a następnie dokonano aktualizacji programu System Center Configuration Manager, wymagania dotyczące systemu Windows 10 mogą zostać usunięte. Aby rozwiązać ten problem, należy ponownie określić wymagania. Należy pamiętać, że chociaż wymóg został usunięty z wyświetlania wymagania, jest nadal przetwarzane poprawnie na urządzeniach.  

3.  W **warunku** listy rozwijanej wybierz warunek, którego chcesz użyć do oceny, czy użytkownik lub urządzenie spełnia wymagania instalacyjne. Zawartość tej listy różni się w zależności od wybranej kategorii.  

4.  W **Operator** listy rozwijanej wybierz operator, który zostanie użyty do porównania wybranego warunku z podaną wartością w celu oceny, czy użytkownik lub urządzenie spełnia wymagania instalacyjne. Dostępni operatorzy różnią się w zależności od wybranego warunku.  

    > [!IMPORTANT]  
    >  Dostępne wymagania będą się różnić w zależności od typu urządzenia, który używa typu wdrożenia.  

5.  W **wartość** należy określić wartości, które będą używane z wybranym warunkiem i operator do oceny, czy użytkownik lub urządzenie spełnia wymagania instalacyjne. Dostępne wartości różnią się w zależności od wybranych warunku i operatora.  

6.  Wybierz **OK** wymaganie Zapisz i Zamknij **tworzenie wymagania** okno dialogowe.  

## <a name="specify-dependencies-for-the-deployment-type"></a>Określenie zależności dotyczących typu wdrożenia  
 Zależności definiują jeden lub więcej typów wdrożeń z innej aplikacji, którą należy zainstalować przed zainstalowaniem typu wdrożenia. Można ustawić zależnych typów wdrożeń można automatycznie zainstalować przed zainstalowaniem typu wdrożenia.  

> [!IMPORTANT]  
>  W niektórych przypadkach typ wdrożenia jest zależny od typu wdrożenia, który również ma zależności. Maksymalna liczba obsługiwanych zależności w łańcuchu wynosi pięć.  

1.  Na **zależności** strona kreatora tworzenia typu wdrożenia wybierz **Dodaj** Jeśli chcesz określić typy wdrożeń, które należy zainstalować przed zainstalowaniem tego typu wdrożenia.  

    > [!IMPORTANT]  
    >  Można również dodać nowych zależności na **zależności** na karcie *< Nazwa typu wdrożenia\>*  **właściwości** okno dialogowe.  

2.  W **Dodawanie zależności** okno dialogowe Wybierz **Dodaj**.  

3.  W **Określ wymaganą aplikację** okno dialogowe, wybierz istniejącą aplikację i jeden z wdrożenia aplikacji typów do użycia w charakterze zależności.  

    > [!TIP]  
    >  Można wybrać **widoku** Aby wyświetlić właściwości wybranej aplikacji lub typu wdrożenia.  

4.  Wybierz **OK** zamknąć **Określ wymaganą aplikację** okno dialogowe.  

5.  Jeśli chcesz, aby automatycznie zainstalować aplikację zależną, wybierz **automatyczna instalacja** obok aplikacji.  

    > [!NOTE]  
    >  Zależna aplikacja nie musi wdrożenie zostaną zainstalowane automatycznie.  

6.  W **Dodawanie zależności** okno dialogowe, w obszarze **Nazwa grupy zależności**, wprowadź nazwę, aby odwoływać się do tej grupy zależności aplikacji.  

7.  Opcjonalnie użyj **Zwiększ priorytet** i **Zmniejsz priorytet** przyciski, aby zmienić kolejność, w jakiej są oceniane poszczególne zależności.  

8.  Wybierz **OK** zamknąć **Dodawanie zależności** okno dialogowe.  

## <a name="confirm-the-deployment-type-settings-and-finish-the-wizard"></a>Potwierdzenie ustawień typu wdrożenia i Zakończ pracę kreatora  

1.  Na **Podsumowanie** strona kreatora tworzenia typu wdrożenia Przejrzyj akcje wykonywane przez kreatora. Wybierz **dalej** do utworzenia typu wdrożenia, lub wybierz **Wstecz** przejść wstecz i zmienić ustawienia typu wdrożenia.  

2.  Po **postępu** zakończeniu pozycję Przejrzyj akcje wykonane przez kreatora, a następnie wybierz **Zamknij** aby zakończyć pracę kreatora.  

3.  Jeśli Kreator tworzenia typu wdrożenia został uruchomiony z Kreatora tworzenia aplikacji, nastąpi powrót do **typy wdrożeń** Kreatora tworzenia aplikacji.  

## <a name="set-up-additional-options-for-deployment-types-that-contain-virtual-applications"></a>Konfigurowanie dodatkowych opcji typów wdrożeń zawierających aplikacje wirtualne  
 Poniższe procedury umożliwiają konfigurowanie dodatkowych opcji typów wdrożeń zawierających aplikacje wirtualne.  

### <a name="set-up-content-options-for-application-virtualization-app-v-deployment-types"></a>Ustaw opcje zawartości dla typów wdrożeń programu Application Virtualization (App-V)  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **aplikacji**.  

2.  W **aplikacji** , wybierz aplikację, która ma typ wdrożenia programu App-V. Następnie na **Home** w karcie **właściwości** grupy, wybierz **właściwości**.  

3.  W *< nazwa aplikacji\>*  **właściwości** okna dialogowego na **typy wdrożeń** karcie, wybierz typ wdrożenia programu App-V, a następnie wybierz **edytować**.  

4.  W *< Nazwa typu wdrożenia\>*  **właściwości** okna dialogowego na **zawartości** kartę, ustaw poniższe opcje, w razie potrzeby:  

    -   **Zachowania zawartości w pamięci podręcznej klienta**— wybierz tę opcję, aby upewnić się, że zawartość dla tego typu wdrożenia nie zostanie usunięta z pamięci podręcznej klienta programu Configuration Manager.  

    -   **Załaduj zawartość do pamięci podręcznej programu App-V przed uruchomieniem**— wybierz tę opcję, aby upewnić się, że cała zawartość dla aplikacji wirtualnej zostanie załadowana do pamięci podręcznej programu App-V, przed uruchomieniem aplikacji. Zaznaczenie tej opcji gwarantuje również, że zawartość aplikacji nie zostanie trwale zatrzymana w pamięci podręcznej i mogą zostać usunięte zgodnie z wymaganiami.  

5.  Wybierz **OK** zamknąć *< Nazwa typu wdrożenia\>*  **właściwości** okno dialogowe.  

6.  Wybierz **OK** zamknąć *< nazwa aplikacji\>*  **właściwości** okno dialogowe.  

### <a name="set-up-publishing-options-for-app-v-deployment-types"></a>Ustawianie opcji typów wdrożeń App-V publikowania  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **aplikacji**.  

3.  W **aplikacji** , wybierz aplikację, która ma typ wdrożenia programu App-V. Następnie na **Home** w karcie **właściwości** grupy, wybierz **właściwości**.  

4.  W *< nazwa aplikacji\>*  **właściwości** okna dialogowego na **typy wdrożeń** karcie, wybierz typ wdrożenia programu App-V, a następnie wybierz **edytować**.  

5.  W *< Nazwa typu wdrożenia\>*  **właściwości** okna dialogowego na **publikowania** , a następnie wybierz elementy w aplikacji wirtualnej, który chcesz opublikować.  

6.  Wybierz **OK** zamknąć *< Nazwa typu wdrożenia\>*  **właściwości** okno dialogowe.  

7.  Wybierz **OK** zamknąć *< nazwa aplikacji\>*  **właściwości** okno dialogowe.  

## <a name="import-an-application"></a>Importowanie aplikacji  
 Poniższa procedura umożliwia importowanie aplikacji do programu Configuration Manager. Aby uzyskać informacje o sposobie eksportowania aplikacji, zobacz [zadania zarządzania dla programu System Center Configuration Manager aplikacji](../../apps/deploy-use/management-tasks-applications.md).  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **zarządzania aplikacjami** > **aplikacji**.   

3.  Na **Home** w karcie **Utwórz** grupy, wybierz **Importuj aplikację**.  

4.  Na **ogólne** strony **Kreatora importowania aplikacji**, wybierz **Przeglądaj**, a następnie określ ścieżkę UNC do pliku zip, który ma aplikacji do zaimportowania.  

5.  Na **zawartość pliku** wybierz akcję, która będzie wykonywana, gdy aplikację, którą próbujesz zaimportować jest duplikatem istniejącej aplikacji. Możesz utworzyć nową aplikację lub zignorować duplikat i dodać nową wersję istniejącej aplikacji.  

6.  Na **Podsumowanie** Przejrzyj akcje do wykonania, a następnie Zakończ pracę kreatora.  

 Nowa aplikacja pojawi się w węźle **Aplikacje**.  

> [!TIP]  
>  Polecenia cmdlet środowiska Windows PowerShell **Export-CMApplication** ma taką samą funkcję jak tej procedury. Aby uzyskać więcej informacji, zobacz [Export-CMApplication](https://technet.microsoft.com/library/jj821738.aspx) w Microsoft systemu Center 2012 Configuration Manager z dodatkiem SP1 polecenia Cmdlet Reference.  

##  <a name="deployment-types-supported-by-configuration-manager"></a>Typy wdrożeń obsługiwane przez program Configuration Manager  

|Nazwa typu wdrożenia|Więcej informacji|  
|--------------------------|----------------------|  
|**Instalator systemu Windows (\*pliku .msi)**|Tworzy typ wdrożenia na podstawie pliku Instalatora systemu Windows.|  
|**Pakiet aplikacji systemu Windows (\*appx, \*.appxbundle)**|Tworzy typ wdrożenia dla systemu operacyjnego Windows 8 lub Windows RT albo nowszego na podstawie pliku pakietu aplikacji systemu Windows lub pakietu zbioru aplikacji systemu Windows.|  
|**Pakiet aplikacji systemu Windows (w Sklepie Windows)**|Tworzy typ wdrożenia dla systemu Windows 8, Windows RT lub później za pośrednictwem łącza do aplikacji w Sklepie Windows lub sklepu, aby wybrać aplikację, które są wymagane.<br /><br /> Jeśli chcesz wdrożyć aplikację jako łącze do Sklepu Windows, upewnij się, że ustawienie zasady grupy **wyłączyć aplikacji magazynu** jest ustawiona na **wyłączone** lub **nieskonfigurowane**. Jeśli to ustawienie jest włączone, klienci nie będą mogli połączyć się ze Sklepem Windows w celu pobrania i zainstalowania aplikacji.<br /><br /> Typy wdrożeń systemu Windows 8 korzystające z linku do sklepu są zawsze oceniane przed innymi typami wdrożeń, niezależnie od ich priorytetu.|  
|**Instalator skryptowy**|Tworzy typ wdrożenia określający skrypt uruchamiany na urządzeniach klienckich w celu zainstalowania zawartości lub wykonaj akcję.|  
|**Microsoft Application Virtualization 4**|Tworzy typ wdrożenia na podstawie manifestu aplikacji Microsoft Application Virtualization 4|  
|**Microsoft Application Virtualization 5**|Tworzy typ wdrożenia na podstawie pliku pakietu aplikacji Microsoft Application Virtualization 5.|  
|**Pakiet aplikacji Windows Phone (\*plik xap)**|Tworzy typ wdrożenia na podstawie pliku pakietu aplikacji systemu Windows Phone.|  
|**Pakiet aplikacji Windows Phone (w Sklepie Windows Phone)**|Tworzy typ wdrożenia przez określenie linku do aplikacji w sklepie Windows Phone Store.|  
|**Plik Cabinet przenośnych systemu Windows**|Tworzy typ wdrożenia dla urządzeń z systemem Windows Mobile na podstawie pliku cabinet systemu Windows Mobile (CAB).|  
|**Pakiet aplikacji dla systemu iOS (\*pliku .ipa)**|Tworzy typ wdrożenia na podstawie pliku pakietu aplikacji dla systemu iOS.|  
|**Pakiet aplikacji dla systemu iOS ze sklepu z aplikacjami**|Tworzy typ wdrożenia za pośrednictwem łącza do aplikacji dla systemu iOS ze sklepu App Store.|  
|**Pakiet aplikacji dla systemu Android (\*pliku .apk)**|Tworzy typ wdrożenia na podstawie pliku pakietu aplikacji dla systemu Android.|  
|**Pakiet aplikacji dla systemu Android w witrynie Google Play**|Tworzy typ wdrożenia za pośrednictwem łącza do aplikacji w witrynie Google Play.|  
|**Mac OS X**|Tworzy typ wdrożenia dla komputerów Mac na podstawie pliku *.cmmac, który został utworzony przy użyciu narzędzia CMAppUtil.<br /><br /> Dotyczy tylko komputerów Mac z klienta programu Configuration Manager.|  
|**Aplikacja sieci Web**|Tworzy typ wdrożenia określający łącze do aplikacji sieci web. Typ wdrożenia instaluje skrót do aplikacji sieci web na urządzeniu użytkownika.<br /><br /> Jeśli zainstalowano Intune managed browser na iOS lub Android urządzeń, którymi można zarządzać, można zapewnić, że użytkownicy tylko służy do otwierania aplikacji managed browser. W tym celu należy użyć jednej z następujących formatów podaj łącze do aplikacji za pomocą zastąpienia **http:** z **http intunemam:** lub **https:** z **https intunemam:**<br /><br /> - **http intunemam: / / < ścieżka do aplikacji sieci web\>**<br /><br /> - **HTTPS intunemam: / / < ścieżka do aplikacji sieci web\>**<br /><br /> Wymagania aplikacji programu Configuration Manager umożliwia zainstalowanie aplikacji, które chcesz skojarzyć z managed browser są tylko do iOS i android.<br /><br /> Aby uzyskać więcej informacji o Intune managed browser, zobacz [Internet zarządzać dostępu przy użyciu zarządzanego zasady przeglądarki](../../apps/deploy-use/manage-internet-access-using-managed-browser-policies.md).|  
|**Instalator Windows przy użyciu oprogramowania MDM (\*.msi)**|Ten typ Instalatora umożliwia tworzenie i wdrażanie aplikacji opartych na Instalatorze systemu Windows do komputerów z systemem Windows 10.<br /><br /> W przypadku korzystania z instalatora tego typu należy wziąć pod uwagę następujące kwestie:<br><br>-Użytkownik może przekazać tylko jeden plik z rozszerzeniem pliku .msi.<br /><br /> -Kod produktu i wersja produktu plików są używane do wykrywania aplikacji.<br /><br /> -Domyślne zachowanie ponownego uruchamiania aplikacji będą używane. Menedżer konfiguracji nie kontroluje to.<br /><br /> -Pakiety MSI użytkownika zostanie zainstalowany dla jednego użytkownika.<br /><br /> -Pakiety MSI dla poszczególnych komputerów zostanie zainstalowany dla wszystkich użytkowników na urządzeniu.<br /><br /> -Pakiety MSI podwójne obecnie instalować tylko dla wszystkich użytkowników na urządzeniu.<br /><br /> -App aktualizacje są obsługiwane, gdy kod produktu MSI każdej wersji jest taki sam.|  

