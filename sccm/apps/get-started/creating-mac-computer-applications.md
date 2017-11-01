---
title: "Tworzenie aplikacji dla komputerów Mac"
titleSuffix: Configuration Manager
description: "Zobacz uwagi, które należy wziąć pod uwagę podczas tworzenia i wdrażania aplikacji dla komputerów Mac."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ab1aecdd-d943-44f5-b0a9-e8fe7439e5d6
caps.latest.revision: "9"
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.openlocfilehash: 912632c672c49deefc946e089dad6a82454c4b67
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="create-mac-computer-applications-with-system-center-configuration-manager"></a>Tworzenie aplikacji dla komputerów Mac w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Podczas tworzenia i wdrażania aplikacji dla komputerów Mac, należy pamiętać o następujących kwestiach.  

> [!IMPORTANT]  
>  Procedury przedstawione w tym temacie obejmują informacje dotyczące wdrażania aplikacji na komputerach Mac, na których zainstalowano klienta programu Configuration Manager. Komputery Mac zarejestrowane w usłudze Microsoft Intune nie obsługują wdrażania aplikacji.  

## <a name="general-considerations"></a>Zagadnienia ogólne  
 System Center Configuration Manager można użyć do wdrożenia aplikacji na komputerach Mac z zainstalowanym klientem programu Configuration Manager Mac. Proces wdrażania oprogramowania na komputerach Mac są podobne do czynności, aby wdrożyć oprogramowanie na komputerach z systemem Windows. Jednak przed tworzenia i wdrażania aplikacji dla komputerów Mac, które są zarządzane przez program Configuration Manager, należy wziąć pod uwagę następujące czynności:  

-   Przed wdrożeniem pakietów aplikacji na komputerach Mac, należy użyć **CMAppUtil** narzędzia na komputerze Mac, aby przekonwertować te aplikacje do formatu, który może zostać odczytany przez program Configuration Manager.  

-   Menedżer konfiguracji nie obsługuje wdrożenia aplikacji dla komputerów Mac dla użytkowników. Zamiast tego te wdrożenia muszą być wprowadzane do urządzenia. Podobnie dla wdrożenia aplikacji dla komputerów Mac, program Configuration Manager nie obsługuje **wykonaj wstępne wdrożenie oprogramowania na główne urządzenie użytkownika** opcja **ustawienia wdrażania** strony **Kreatora wdrażania oprogramowania**.  

-   W przypadku aplikacji dla komputerów Mac obsługiwane są wdrożenia symulowane.  

-   Nie można wdrożyć aplikacji na komputerach Mac, których cel to **Dostępne**.  

-   Opcja wysyłania pakietów wznawiania podczas wdrażania oprogramowania nie jest obsługiwana na komputerach Mac.  

-   Komputery Mac nie obsługują pobierania zawartości aplikacji usługi inteligentnego transferu w tle (BITS). Jeśli pobranie aplikacji nie powiedzie się, zostanie uruchomiony ponownie od samego początku.  

-   Podczas tworzenia typów wdrożenia dla komputerów Mac programu Configuration Manager nie obsługuje warunków globalnych.  

## <a name="steps-to-create-and-deploy-an-application"></a>Procedura tworzenia i wdrażania aplikacji  
 Poniższa tabela zawiera kroki, szczegóły i informacje dotyczące tworzenia i wdrażania aplikacji dla komputerów Mac.  

|Krok|Szczegóły|  
|----------|-------------|  
|**Krok 1**: Przygotowanie aplikacji dla komputerów Mac dla programu Configuration Manager|Przed utworzeniem aplikacji programu Configuration Manager z pakietów oprogramowania dla komputerów Mac, należy użyć **CMAppUtil** narzędzia na komputerze Mac w celu konwersji oprogramowania dla komputerów Mac do programu Configuration Manager**cmmac** pliku.|  
|**Krok 2**: Tworzenie aplikacji programu Configuration Manager zawierającej oprogramowanie dla komputerów Mac|Użyj **Kreatora tworzenia aplikacji** do tworzenia aplikacji dla oprogramowania dla komputerów Mac.|  
|**Krok 3**: Tworzenie typu wdrożenia dla aplikacji dla komputerów Mac|Ten krok jest wymagany tylko wtedy, gdy nie zaimportowano automatycznie tych informacji z aplikacji.|  
|**Krok 4**: Wdrażanie aplikacji dla komputerów Mac|Użyj **Kreatora wdrażania oprogramowania** do wdrożenia aplikacji na komputerach Mac.|  
|**Krok 5**: Monitorowanie wdrożenia aplikacji dla komputerów Mac|Należy sprawdzić, czy wdrożenia aplikacji na komputerach Mac zakończyły się powodzeniem.|  

## <a name="supplemental-procedures-to-create-and-deploy-applications-for-mac-computers"></a>Dodatkowe procedury tworzenia i wdrażania aplikacji dla komputerów Mac  
 Poniższe procedury umożliwiają tworzenie i wdrażanie aplikacji dla komputerów Mac, które są zarządzane przez program Configuration Manager.  

###  <a name="step-1-prepare-mac-applications-for-configuration-manager"></a>Krok 1. Przygotowanie aplikacji dla komputerów Mac dla programu Configuration Manager  
 Proces tworzenia i wdrażania aplikacji programu Configuration Manager na komputerach Mac przypomina proces wdrażania dla komputerów z systemem Windows. Jednakże przed utworzeniem aplikacji programu Configuration Manager, które zawierają typy wdrożenia dla komputerów Mac należy przygotować aplikacje przy użyciu **CMAppUtil** narzędzia. To narzędzie jest pobierane z plikami instalacyjnymi klienta dla komputerów Mac. Narzędzie **CMAppUtil** umożliwia zebranie informacji o aplikacji, takich jak data wykrycia, z następujących pakietów dla komputerów Mac:  

-   Obraz dysku Apple (.dmg)  

-   Plik meta pakietu (.mpkg)  

-   Pakiet instalatora systemu Mac OS X (.pkg)  

-   Aplikacja systemu Mac OS X (.app)  

Po zebraniu informacji o aplikacji narzędzie **CMAppUtil** tworzy plik z rozszerzeniem **cmmac**. Ten plik zawiera pliki instalacyjne oprogramowania dla komputerów Mac i informacje dotyczące metod wykrywania, których można użyć do oceny, czy aplikacja jest już zainstalowana. Narzędzie**CMAppUtil** może także przetwarzać pliki **dmg** , które zawierają wiele aplikacji dla komputerów Mac, i tworzyć różne typy wdrożenia dla każdej aplikacji.  

1.  Skopiuj pakiet instalacyjny oprogramowania dla komputerów Mac do folderu na komputerze Mac, w którym wyodrębniono zawartość pliku **macclient.dmg** pobranego z Centrum pobierania firmy Microsoft.  

2.  Na tym samym komputerze Mac otwórz okno terminalu i przejdź do folderu, w którym wyodrębniono zawartość pliku **macclient.dmg** .  

3.  Przejdź do **narzędzia** folder i wpisz następujące polecenie w wierszu polecenia:  

     **./CMAppUtil** *<properties\>*  

     Załóżmy na przykład, że chcesz przekonwertować zawartość pliku obrazu dysku Apple o nazwie **MySoftware.dmg** przechowywanego w folderze pulpitu użytkowników do **cmmac** pliku w tym samym folderze. Chcesz utworzyć również **cmmac** plików dla wszystkich aplikacji, które znajdują się w pliku obrazu dysku. W tym celu wpisz w wierszu polecenia następujący tekst:  

     **./CMApputil –c /Users/** *<nazwa użytkownika\>* **/Desktop/MySoftware.dmg -o /Users/** *<nazwa użytkownika\>* **/Desktop -a**  

    > [!NOTE]  
    >  Nazwa aplikacji nie może być dłuższa niż 128 znaków.  

     Aby skonfigurować opcje narzędzia **CMAppUtil**, należy użyć właściwości wiersza polecenia podanych w następującej tabeli:  

  	|Właściwość|Więcej informacji|  
  	|--------------|----------------------|  
  	|**-h**|Umożliwia wyświetlenie dostępnych właściwości wiersze polecenia.|  
  	|**-r**|Umożliwia zapisanie zawartości pliku **detection.xml** dotyczącej dostępnego pliku **cmmac** do standardowego strumienia wyjściowego **stdout**. Dane wyjściowe zawierają parametry wykrywania i wersję narzędzia **CMAppUtil** , które zostało użyte do utworzenia pliku **cmmac** .|  
  	|**-c**|Określa plik źródłowy, który ma zostać przekonwertowany.|  
  	|**-o**|Ścieżka danych wyjściowych w połączeniu z właściwością – c.|  
  	|**-a**|Automatycznie tworzy plików .cmmac w połączeniu z właściwością – c dla wszystkich aplikacji i pakietów w pliku obrazu dysku.|  
  	|**-s**|Umożliwia pominięcie generowania pliku **detection.xml** , jeżeli nie znaleziono parametrów wykrywania, i wymuszenie utworzenia pliku **cmmac** bez pliku **detection.xml** .|  
  	|**-v**|Umożliwia wyświetlenie bardziej szczegółowych danych wyjściowych z narzędzia **CMAppUtil** wraz z informacjami diagnostycznymi.|  

4.  Sprawdź, czy plik **cmmac** został utworzony w podanym folderze wyjściowym.  

###  <a name="create-a-configuration-manager-application-that-contains-the-mac-software"></a>Tworzenie aplikacji programu Configuration Manager zawierającej oprogramowanie dla komputerów Mac  

Użyj poniższej procedury ułatwiające tworzenie aplikacji dla komputerów Mac, które są zarządzane przez program Configuration Manager.  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **Zarządzanie aplikacjami** > **aplikacji**.  

3.  Na **Home** karcie **Utwórz** grupy, wybierz **tworzenie aplikacji**.  

4.  Na **ogólne** strony **Kreatora tworzenia aplikacji**, wybierz pozycję **automatycznie Wykryj informacje o tej aplikacji z plików instalacyjnych**.  

    > [!NOTE]  
    >  Jeśli chcesz samodzielnie określić informacje o aplikacji, wybierz **ręcznie określ informacje o aplikacji**. Aby uzyskać więcej informacji dotyczących ręcznego określania informacji, zobacz [Jak tworzyć aplikacje w programie System Center Configuration Manager](../../apps/deploy-use/create-applications.md).  

5.  Z listy rozwijanej **Typ** wybierz pozycję **Mac OS X**.  

6.  W **lokalizacji** Określ ścieżkę UNC w postaci  *\\ \\< server\>\\< udziału\>\\< nazwa pliku\>*  do pliku instalacji aplikacji dla komputerów Mac (**cmmac** pliku) który wykryje informacje o aplikacji. Możesz też wybrać **Przeglądaj** wskaż i określ lokalizację pliku instalacyjnego.  

    > [!NOTE]  
    >  Wymagany jest dostęp do ścieżki UNC zawierającej aplikację.  

7.  Wybierz **dalej**.  

8.  Na **Importuj informacje** strony **Kreatora tworzenia aplikacji**, przejrzyj zaimportowane informacje. Jeśli to konieczne, możesz wybrać **Wstecz** aby wrócić do poprzedniej strony i poprawić błędy. Wybierz **dalej** aby kontynuować.  

9. Na **ogólne informacje** strony **Kreatora tworzenia aplikacji**, podaj informacje o aplikacji, takie jak nazwa aplikacji, komentarze, wersja i opcjonalne odwołanie ułatwiające utworzenie odwołania do aplikacji w konsoli programu Configuration Manager.  

    > [!NOTE]  
    >  Niektóre informacje o aplikacji mogą być już na tej stronie, jeżeli zostały poprzednio pobrane z plików instalacyjnych aplikacji.  

10. Wybierz **dalej**, przejrzyj informacje o aplikacji na **Podsumowanie** , a następnie ukończ **Kreatora tworzenia aplikacji**.  

11. Nowa aplikacja jest wyświetlana w **aplikacji** węzła konsoli programu Configuration Manager.  

###  <a name="step-3-create-a-deployment-type-for-the-mac-application"></a>Krok 3. Tworzenie typu wdrożenia dla aplikacji dla komputerów Mac  
 Użyj poniższej procedury ułatwiające tworzenie typu wdrożenia dla komputerów Mac, które są zarządzane przez program Configuration Manager.  

> [!NOTE]  
>  Jeżeli automatycznie zaimportowano informacje o aplikacji w **Kreatora tworzenia aplikacji**, typ wdrożenia dla aplikacji mógł już zostać utworzony.  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **Zarządzanie aplikacjami** > **aplikacji**.  

3.  Wybierz aplikację. Następnie na **Home** karcie **aplikacji** grupy, wybierz **Utwórz typ wdrożenia** do utworzenia nowego typu wdrożenia dla tej aplikacji.  

    > [!NOTE]  
    >  Można również uruchomić **Kreatora tworzenia typu wdrożenia** z **Kreatora tworzenia aplikacji** i z **typy wdrożeń** karcie *< nazwa aplikacji\>*  **właściwości** okno dialogowe.  

4.  Na **ogólne** strony **Kreatora tworzenia typu wdrożenia**w **typu** listy rozwijanej wybierz **systemu Mac OS X**.  

5.  W **lokalizacji** Określ ścieżkę UNC w postaci \\ \\< server\>\\< udostępnianie\>\\< nazwa pliku\> do pliku instalacyjnego aplikacji (**cmmac** pliku). Możesz też wybrać **Przeglądaj** wskaż i określ lokalizację pliku instalacyjnego.  

    > [!NOTE]  
    >  Wymagany jest dostęp do ścieżki UNC zawierającej aplikację.  

6.  Wybierz **dalej**.  

7.  Na stronie **Importuj informacje** **Kreatora tworzenia typów wdrożeń**przejrzyj zaimportowane informacje. W razie potrzeby wybierz **Wstecz** aby wrócić do poprzedniej strony i poprawić błędy. Wybierz **dalej** aby kontynuować.  

8.  Na karcie **Informacje ogólne** **Kreatora tworzenia typów wdrożeń**podaj informacje o aplikacji, takie jak nazwa, komentarze i języki, w których dostępny jest typ wdrożenia.  

    > [!NOTE]  
    >  Niektóre informacje o typie wdrożenia mogą być już na tej stronie, jeżeli zostały poprzednio pobrane z plików instalacyjnych aplikacji.  

9. Wybierz **dalej**.  

10. Na **wymagania** strony **Kreatora tworzenia typu wdrożenia**, można określić warunki, które muszą zostać spełnione przed zainstalowaniem typu wdrożenia na komputerach Mac.  

11. Wybierz **Dodaj** otworzyć **tworzenie wymagania** okno dialogowe i dodać nowe wymaganie.  

    > [!NOTE]  
    >  Możesz także dodać nowe wymagania na **wymagania** karcie *< Nazwa typu wdrożenia\>*  **właściwości** okno dialogowe.  

12. Na liście rozwijanej **Kategoria** zaznacz, że to wymaganie dotyczy urządzenia.  

13. Z **warunku** listy rozwijanej wybierz warunek, którego chcesz użyć do oceny, czy komputer Mac spełnia wymagania instalacyjne. Zawartość tej listy różni się w zależności od wybranej kategorii.  

14. Z **Operator** listy rozwijanej wybierz operator, aby użyć do porównania wybranego warunku z podaną wartością w celu oceny, czy użytkownik lub urządzenie spełnia wymagania instalacyjne. Dostępni Operatorzy różnią się w zależności od wybranego warunku.  

15. W **wartość** określ wartości do użycia z wybranym warunkiem i Operator służący do oceny, czy użytkownik lub urządzenie spełnia wymaganie instalacyjne. Dostępne wartości różnią się w zależności od warunkiem i operator, który można wybrać.

16. Wybierz **OK** Aby zapisać zasadę wymagań i zamknąć **tworzenie wymagania** okno dialogowe.  

17. Na **wymagania** strony **Kreatora tworzenia typu wdrożenia**, wybierz **dalej**.  

18. Na stronie **Podsumowanie** **Kreatora tworzenia typów wdrożeń**przejrzyj akcje wykonywane przez kreatora.  W razie potrzeby wybierz **Wstecz** aby wrócić i zmienić ustawienia typu wdrożenia. Wybierz **dalej** do utworzenia typu wdrożenia.  

19. Po **postępu** Przejrzyj akcje, które zostały podjęte, a następnie wybierz zakończenie, **Zamknij** do ukończenia **Kreatora tworzenia typu wdrożenia**.  

20. Jeżeli uruchomiono tego kreatora z **Kreatora tworzenia aplikacji**, nastąpi powrót do **typy wdrożeń** strony.  

###  <a name="deploy-the-mac-application"></a>Wdrażanie aplikacji dla komputerów Mac  
 Kroki wdrażania aplikacji na komputerach Mac są takie same jak kroki wdrażania aplikacji na komputerach z systemem Windows, z wyjątkiem następujących różnic:  

-   Wdrażanie aplikacji w przypadku użytkowników nie jest obsługiwane.  

-   Wdrożenia, których cel to **Dostępne** nie są obsługiwane.  

-   **Wykonaj wstępne wdrożenie oprogramowania na główne urządzenie użytkownika** opcja **ustawienia wdrażania** strony **Kreatora wdrażania oprogramowania** nie jest obsługiwane.  

-   Ponieważ komputery Mac nie obsługują Centrum oprogramowania, ustawienie **powiadomienia użytkownika** na **środowisko użytkownika** strony **Kreatora wdrażania oprogramowania** jest ignorowana.  

-   Opcja wysyłania pakietów wznawiania podczas wdrażania oprogramowania nie jest obsługiwana na komputerach Mac.  

> [!NOTE]  
>  Można utworzyć kolekcję, która zawiera tylko komputery Mac. W tym celu utwórz kolekcję wykorzystującą regułę zapytania i Użyj przykładowego zapytania WQL Podanego w [jak tworzyć zapytania](../../core/servers/manage/create-queries.md) tematu.  

 Aby uzyskać więcej informacji, zobacz [wdrażania aplikacji](../../apps/deploy-use/deploy-applications.md).  

###  <a name="step-5-monitor-the-deployment-of-the-mac-application"></a>Krok 5. Monitorowanie wdrożenia aplikacji dla komputerów Mac  
 Ten sam proces służy do monitorowania wdrażania aplikacji na komputerach Mac, jak w przypadku monitorowania wdrożeń aplikacji na komputerach z systemem Windows.  

 Aby uzyskać więcej informacji, zobacz [monitorowania aplikacji](/sccm/apps/deploy-use/monitor-applications-from-the-console).  
