---
title: "Tworzenie aplikacji dla komputerów Mac komputera | Dokumentacja firmy Microsoft"
description: "Zobacz uwagi, które należy wziąć pod uwagę podczas tworzenia i wdrażania aplikacji dla komputerów Mac."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ab1aecdd-d943-44f5-b0a9-e8fe7439e5d6
caps.latest.revision: 9
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: ba45f36c517114f7a8d2be8d9056e1b2a800dd4f
ms.openlocfilehash: ffd66a4047ec253704e9772e2c3e3a4d9db7c46f
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="create-mac-computer-applications-with-system-center-configuration-manager"></a>Tworzenie aplikacji dla komputerów Mac komputerów z System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Podczas tworzenia i wdrażania aplikacji dla komputerów Mac należy uwzględnić następujące kwestie.  

> [!IMPORTANT]  
>  Procedury przedstawione w tym temacie obejmować informacje dotyczące wdrażania aplikacji na komputerach Mac, na których zainstalowano klienta programu Configuration Manager. Komputery Mac zarejestrowane w usłudze Microsoft Intune nie obsługują wdrażania aplikacji.  

## <a name="general-considerations"></a>Zagadnienia ogólne  
 Aby wdrożyć aplikacje na komputerach Mac, uruchom klienta programu Configuration Manager Mac, można użyć programu System Center Configuration Manager. Kroki umożliwiające wdrożenie oprogramowania na komputerach Mac są podobne do kroki umożliwiające wdrożenie oprogramowania na komputerach z systemem Windows. Jednak przed tworzenia i wdrażania aplikacji dla komputerów Mac, które są zarządzane przez program Configuration Manager, należy wziąć pod uwagę następujące czynności:  

-   Przed wdrożeniem pakietów aplikacji dla komputerów Mac, należy użyć **CMAppUtil** narzędzie na komputerze Mac, aby przekonwertować te aplikacje do formatu, który może zostać odczytany przez program Configuration Manager.  

-   Menedżer konfiguracji nie obsługuje wdrożenia aplikacji dla komputerów Mac dla użytkowników. Zamiast tego należy te wdrożenia na urządzeniu. Podobnie w przypadku wdrożeń aplikacji Mac programu Configuration Manager nie obsługuje **wykonaj wstępne wdrożenie oprogramowania na główne urządzenie użytkownika** opcja **ustawienia wdrażania** strony **Kreatora wdrażania oprogramowania**.  

-   W przypadku aplikacji dla komputerów Mac obsługiwane są wdrożenia symulowane.  

-   Nie można wdrożyć aplikacji na komputerach Mac, których cel to **Dostępne**.  

-   Opcja wysyłania pakietów wznawiania podczas wdrażania oprogramowania nie jest obsługiwana na komputerach Mac.  

-   Komputery Mac nie obsługują pobierania zawartości aplikacji usługi inteligentnego transferu w tle (BITS). Jeżeli pobieranie aplikacji nie powiedzie się, zostanie ponownie od początku.  

-   Podczas tworzenia typów wdrożenia dla komputerów Mac programu Configuration Manager nie obsługuje warunków globalnych.  

## <a name="steps-to-create-and-deploy-an-application"></a>Procedura tworzenia i wdrażania aplikacji  
 Poniższa tabela zawiera kroki, szczegóły i informacje dotyczące tworzenia i wdrażania aplikacji dla komputerów Mac.  

|Krok|Szczegóły|  
|----------|-------------|  
|**Krok 1**: Przygotowanie aplikacji dla komputerów Mac dla programu Configuration Manager|Przed utworzeniem aplikacji programu Configuration Manager z pakietów oprogramowania dla komputerów Mac, należy użyć **CMAppUtil** na komputerze Mac, aby przekonwertować oprogramowanie dla komputerów Mac do Menedżera konfiguracji narzędzia**.cmmac** pliku.|  
|**Krok 2**: Tworzenie aplikacji programu Configuration Manager zawierającej oprogramowanie dla komputerów Mac|Użyj **Kreatora tworzenia aplikacji** do tworzenia aplikacji dla komputerów Mac oprogramowania.|  
|**Krok 3**: Tworzenie typu wdrożenia dla aplikacji dla komputerów Mac|Ten krok jest wymagany tylko wtedy, gdy nie zaimportowano automatycznie tych informacji z aplikacji.|  
|**Krok 4**: Wdrażanie aplikacji dla komputerów Mac|Użyj **Kreatora wdrażania oprogramowania** do wdrożenia aplikacji na komputerach Mac.|  
|**Krok 5**: Monitorowanie wdrożenia aplikacji dla komputerów Mac|Należy sprawdzić, czy wdrożenia aplikacji na komputerach Mac zakończyły się powodzeniem.|  

## <a name="supplemental-procedures-to-create-and-deploy-applications-for-mac-computers"></a>Dodatkowe procedury tworzenia i wdrażania aplikacji dla komputerów Mac  
 Poniższe procedury umożliwiają tworzenie i wdrażanie aplikacji dla komputerów Mac, które są zarządzane przez program Configuration Manager.  

###  <a name="step-1-prepare-mac-applications-for-configuration-manager"></a>Krok 1: Przygotowanie aplikacji dla komputerów Mac dla programu Configuration Manager  
 Proces tworzenia i wdrażania aplikacji programu Configuration Manager na komputerach Mac przypomina proces wdrażania dla komputerów z systemem Windows. Jednak przed przystąpieniem do tworzenia aplikacji programu Configuration Manager, które zawierają typy wdrożenia dla komputerów Mac należy przygotować aplikacje za pomocą **CMAppUtil** narzędzia. To narzędzie jest pobierane z plikami instalacyjnymi klienta dla komputerów Mac. Narzędzie **CMAppUtil** umożliwia zebranie informacji o aplikacji, takich jak data wykrycia, z następujących pakietów dla komputerów Mac:  

-   Obraz dysku Apple (.dmg)  

-   Plik meta pakietu (.mpkg)  

-   Pakiet instalatora systemu Mac OS X (.pkg)  

-   Aplikacja systemu Mac OS X (.app)  

Po zebraniu informacji o aplikacji narzędzie **CMAppUtil** tworzy plik z rozszerzeniem **cmmac**. Ten plik zawiera pliki instalacyjne oprogramowania dla komputerów Mac i informacje dotyczące metod wykrywania, których można użyć do oceny, czy aplikacja jest już zainstalowana. Narzędzie**CMAppUtil** może także przetwarzać pliki **dmg** , które zawierają wiele aplikacji dla komputerów Mac, i tworzyć różne typy wdrożenia dla każdej aplikacji.  

1.  Skopiuj pakiet instalacyjny oprogramowania dla komputerów Mac do folderu na komputerze Mac, w którym wyodrębniono zawartość pliku **macclient.dmg** pobranego z Centrum pobierania firmy Microsoft.  

2.  Na tym samym komputerze Mac otwórz okno terminalu i przejdź do folderu, w którym wyodrębniono zawartość pliku **macclient.dmg** .  

3.  Przejdź do **narzędzia** folder i wpisz następujące polecenie w wierszu polecenia:  

     **./CMAppUtil** *<properties\>*  

     Załóżmy przykładowo chcesz przekonwertować zawartość pliku obrazu dysku Apple o nazwie **MySoftware.dmg** przechowywanego w folderze pulpitu użytkowników do **cmmac** pliku w tym samym folderze. Chcesz utworzyć również **cmmac** plików dla wszystkich aplikacji, które znajdują się w pliku obrazu dysku. W tym celu wpisz w wierszu polecenia następujący tekst:  

     **./CMApputil –c /Users/** *<nazwa użytkownika\>* **/Desktop/MySoftware.dmg -o /Users/** *<nazwa użytkownika\>* **/Desktop -a**  

    > [!NOTE]  
    >  Nazwa aplikacji nie może być dłuższa niż 128 znaków.  

     Aby skonfigurować opcje narzędzia **CMAppUtil**, należy użyć właściwości wiersza polecenia podanych w następującej tabeli:  

  	|Właściwość|Więcej informacji|  
  	|--------------|----------------------|  
  	|**-h**|Umożliwia wyświetlenie dostępnych właściwości wiersze polecenia.|  
  	|**-r**|Umożliwia zapisanie zawartości pliku **detection.xml** dotyczącej dostępnego pliku **cmmac** do standardowego strumienia wyjściowego **stdout**. Dane wyjściowe zawierają parametry wykrywania i wersję narzędzia **CMAppUtil** , które zostało użyte do utworzenia pliku **cmmac** .|  
  	|**-c**|Określa plik źródłowy, który ma zostać przekonwertowany.|  
  	|**-o**|Określa ścieżkę wyjściową w połączeniu z właściwością – c.|  
  	|**-a**|Automatycznie tworzy plików .cmmac w połączeniu z właściwością – c dla wszystkich aplikacji i pakietów w pliku obrazu dysku.|  
  	|**-s**|Umożliwia pominięcie generowania pliku **detection.xml** , jeżeli nie znaleziono parametrów wykrywania, i wymuszenie utworzenia pliku **cmmac** bez pliku **detection.xml** .|  
  	|**-v**|Umożliwia wyświetlenie bardziej szczegółowych danych wyjściowych z narzędzia **CMAppUtil** wraz z informacjami diagnostycznymi.|  

4.  Sprawdź, czy plik **cmmac** został utworzony w podanym folderze wyjściowym.  

###  <a name="create-a-configuration-manager-application-that-contains-the-mac-software"></a>Tworzenie aplikacji programu Configuration Manager zawierającej oprogramowanie dla komputerów Mac  

Użyj poniższej procedury ułatwiające tworzenie aplikacji dla komputerów Mac, które są zarządzane przez program Configuration Manager.  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **zarządzania aplikacjami** > **aplikacji**.  

3.  Na **Home** w karcie **Utwórz** grupy, wybierz **tworzenie aplikacji**.  

4.  Na **ogólne** strony **Kreatora tworzenia aplikacji**, wybierz opcję **automatycznie Wykryj informacje o tej aplikacji z plików instalacyjnych**.  

    > [!NOTE]  
    >  Jeśli chcesz samodzielnie określić informacje o aplikacji, wybierz **ręcznie określić informacje o aplikacji**. Aby uzyskać więcej informacji dotyczących ręcznego określania informacji, zobacz [Jak tworzyć aplikacje w programie System Center Configuration Manager](../../apps/deploy-use/create-applications.md).  

5.  Z listy rozwijanej **Typ** wybierz pozycję **Mac OS X**.  

6.  W **lokalizacji** wpisz ścieżkę UNC w postaci  *\\ \\< server\>\\< udostępnianie\>\\< nazwa pliku\>*  do pliku instalacyjnego aplikacji Mac (**.cmmac** pliku) który wykryje informacje o aplikacji. Alternatywnie, wybrać **Przeglądaj** przejdź do i określ lokalizację pliku instalacyjnego.  

    > [!NOTE]  
    >  Wymagany jest dostęp do ścieżki UNC zawierającej aplikację.  

7.  Wybierz **dalej**.  

8.  Na **Importuj informacje** strony **Kreatora tworzenia aplikacji**, przejrzyj zaimportowane informacje. Jeśli konieczne, można wybrać **Wstecz** przejść wstecz i poprawić błędy. Wybierz **dalej** aby kontynuować.  

9. Na **ogólne informacje** strony **Kreatora tworzenia aplikacji**, podaj informacje o aplikacji, takie jak nazwa aplikacji, komentarze, wersja i opcjonalne odwołanie ułatwiające utworzenie odwołania do aplikacji w konsoli programu Configuration Manager.  

    > [!NOTE]  
    >  Niektóre informacje o aplikacji mogą być już na tej stronie, jeżeli zostały poprzednio pobrane z plików instalacyjnych aplikacji.  

10. Wybierz **dalej**, przejrzyj informacje o aplikacji na **Podsumowanie** , a następnie ukończ **Kreatora tworzenia aplikacji**.  

11. Nowa aplikacja jest wyświetlana w **aplikacji** węzeł konsoli programu Configuration Manager.  

###  <a name="step-3-create-a-deployment-type-for-the-mac-application"></a>Krok 3: Tworzenie typu wdrożenia dla aplikacji dla komputerów Mac  
 Użyj poniższej procedury do utworzenia typu wdrożenia dla komputerów Mac, które są zarządzane przez program Configuration Manager.  

> [!NOTE]  
>  Jeżeli automatycznie zaimportowano informacje o aplikacji w **Kreatora tworzenia aplikacji**, typu wdrożenia dla aplikacji mógł już zostać utworzony.  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **zarządzania aplikacjami** > **aplikacji**.  

3.  Wybierz aplikację. Następnie na **Home** w karcie **aplikacji** grupy, wybierz **Utwórz typ wdrożenia** Aby utworzyć nowy typ wdrożenia dla tej aplikacji.  

    > [!NOTE]  
    >  Można również uruchomić **Kreatora tworzenia typu wdrożenia** z **Kreatora tworzenia aplikacji** i z **typy wdrożeń** na karcie *< nazwa aplikacji\>*  **właściwości** okno dialogowe.  

4.  Na **ogólne** strony **Kreatora tworzenia typu wdrożenia**w **typu** listy rozwijanej wybierz **systemu Mac OS X**.  

5.  W **lokalizacji** wpisz ścieżkę UNC w postaci \\ \\< server\>\\< udziału\>\\< nazwa pliku\> do pliku instalacyjnego aplikacji (***.cmmac** pliku). Alternatywnie, wybrać **Przeglądaj** przejdź do i określ lokalizację pliku instalacyjnego.  

    > [!NOTE]  
    >  Wymagany jest dostęp do ścieżki UNC zawierającej aplikację.  

6.  Wybierz **dalej**.  

7.  Na stronie **Importuj informacje** **Kreatora tworzenia typów wdrożeń**przejrzyj zaimportowane informacje. W razie potrzeby wybierz **Wstecz** przejść wstecz i poprawić błędy. Wybierz **dalej** aby kontynuować.  

8.  Na karcie **Informacje ogólne** **Kreatora tworzenia typów wdrożeń**podaj informacje o aplikacji, takie jak nazwa, komentarze i języki, w których dostępny jest typ wdrożenia.  

    > [!NOTE]  
    >  Niektóre informacje o typie wdrożenia mogą być już na tej stronie, jeżeli zostały poprzednio pobrane z plików instalacyjnych aplikacji.  

9. Wybierz **dalej**.  

10. Na **wymagania** strony **Kreatora tworzenia typu wdrożenia**, można określić warunki, które muszą zostać spełnione przed zainstalowaniem typu wdrożenia na komputerach Mac.  

11. Wybierz **Dodaj** otworzyć **tworzenie wymagania** okno dialogowe i dodać nowe wymaganie.  

    > [!NOTE]  
    >  Możesz także dodać nowe wymagania na **wymagania** na karcie *< Nazwa typu wdrożenia\>*  **właściwości** okno dialogowe.  

12. Na liście rozwijanej **Kategoria** zaznacz, że to wymaganie dotyczy urządzenia.  

13. Z **warunku** listy rozwijanej wybierz warunek, którego chcesz użyć do oceny, czy komputer Mac spełnia wymagania instalacyjne. Zawartość tej listy różni się w zależności od wybranej kategorii.  

14. Z **Operator** listy rozwijanej wybierz operator, aby użyć do porównania wybranego warunku z podaną wartością w celu oceny, czy użytkownik lub urządzenie spełnia wymagania instalacyjne. Dostępni Operatorzy różnią się w zależności od wybranego warunku.  

15. W **wartość** określ wartości do użycia z wybranym warunkiem i operator do oceny, czy użytkownik lub urządzenie spełnia wymaganie instalacyjne. Dostępne wartości różnią się w zależności od warunku i operatora, który wybierzesz.

16. Wybierz **OK** Aby zapisać zasadę wymagań i zamknąć **tworzenie wymagania** okno dialogowe.  

17. Na **wymagania** strony **Kreatora tworzenia typu wdrożenia**, wybierz **dalej**.  

18. Na stronie **Podsumowanie** **Kreatora tworzenia typów wdrożeń**przejrzyj akcje wykonywane przez kreatora.  W razie potrzeby wybierz **Wstecz** przejść wstecz i zmienić ustawienia typu wdrożenia. Wybierz **dalej** tworzenia typu wdrożenia.  

19. Po **postępu** zakończeniu pozycję Przejrzyj akcje, które zostały podjęte, a następnie wybierz **Zamknij** do ukończenia **Kreatora tworzenia typu wdrożenia**.  

20. Jeżeli uruchomiono tego kreatora z **Kreatora tworzenia aplikacji**, nastąpi powrót do **typy wdrożeń** strony.  

###  <a name="deploy-the-mac-application"></a>Wdrażanie aplikacji dla komputerów Mac  
 Kroki umożliwiające wdrożenie aplikacji na komputerach Mac są takie same, jako kroki umożliwiające wdrożenie aplikacji na komputerach z systemem Windows, z wyjątkiem następujących różnic:  

-   Wdrażanie aplikacji w przypadku użytkowników nie jest obsługiwane.  

-   Wdrożenia, których cel to **Dostępne** nie są obsługiwane.  

-   **Wykonaj wstępne wdrożenie oprogramowania na główne urządzenie użytkownika** opcja **ustawienia wdrażania** strony **Kreatora wdrażania oprogramowania** nie jest obsługiwane.  

-   Ponieważ komputery Mac nie obsługują Centrum oprogramowania, ustawienie **powiadomienia użytkownika** na **środowisko użytkownika** strony **Kreatora wdrażania oprogramowania** jest ignorowana.  

-   Opcja wysyłania pakietów wznawiania podczas wdrażania oprogramowania nie jest obsługiwana na komputerach Mac.  

> [!NOTE]  
>  Można utworzyć kolekcję, która zawiera tylko komputery Mac. W tym celu należy utworzyć kolekcje wykorzystującą zasadę kwerendy i użyć przykładowej kwerendy WQL Podanej w [tworzenie kwerend](../../core/servers/manage/create-queries.md) tematu.  

 Aby uzyskać więcej informacji, zobacz [wdrażania aplikacji](../../apps/deploy-use/deploy-applications.md).  

###  <a name="step-5-monitor-the-deployment-of-the-mac-application"></a>Krok 5. Monitorowanie wdrożenia aplikacji dla komputerów Mac  
 Ten sam proces służy do monitorowania wdrażania aplikacji na komputerach Mac, jak w przypadku monitorowania wdrożeń aplikacji na komputerach z systemem Windows.  

 Aby uzyskać więcej informacji, zobacz [monitorowania aplikacji](/sccm/apps/deploy-use/monitor-applications-from-the-console).  

