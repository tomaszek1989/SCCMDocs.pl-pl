---
title: Technical Preview 1708
titleSuffix: Configuration Manager
description: "Dowiedz się więcej o funkcjach dostępnych w wersji zapoznawczej Technical Preview 1708 programu System Center Configuration Manager."
ms.custom: na
ms.date: 08/25/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3c061ceb-3bdb-4d4f-8c60-344964bd416b
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: b6868221f2efb766cf6a96e844617c75ad1e4c50
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="capabilities-in-technical-preview-1708-for-system-center-configuration-manager"></a>Funkcje w wersji Technical Preview 1708 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*

W tym artykule przedstawiono funkcje, które są dostępne w wersji Technical Preview programu System Center Configuration Manager, wersja 1708. Można zainstalować tę wersję, aby zaktualizować i dodać nowe funkcje do lokacji programu Configuration Manager technical preview. Przed zainstalowaniem tej wersji technical Preview, przejrzyj [Technical Preview programu System Center Configuration Manager](../../core/get-started/technical-preview.md) zapoznać się z ogólne wymagania i ograniczenia dotyczące używania wersji technical preview, jak zaktualizować między wersjami i sposobu wyrazić swoją opinię na temat funkcji w wersji technical preview.     


<!--  Known Issues Template   
**Known Issues in this Technical Preview:**
-   **Issue Name**. Details
    Workaround details.
-->
**Znane problemy w tej wersji Technical Preview:**
-   **Aktualizacja do wersji 1708 podglądu zakończy się niepowodzeniem, jeśli masz serwer lokacji w trybie pasywnym**. Po uruchomieniu wersji zapoznawczej 1706 lub 1707 i mieć [serwera lokacji głównej w trybie pasywnym](/sccm/core/get-started/capabilities-in-technical-preview-1706#site-server-role-high-availability), aby może pomyślnie zaktualizować lokację preview do wersji 1708 należy najpierw odinstalować serwer lokacji w trybie pasywnym. Po lokalizacji uruchomiono wersję 1708 można ponownie zainstalować serwer lokacji w trybie pasywnym.

  Aby odinstalować serwer lokacji w trybie pasywnym:
  1. W konsoli przejdź do **administracji** > **omówienie** > **konfiguracja lokacji** > **serwery i role systemu lokacji**, a następnie wybierz serwer lokacji w trybie pasywnym.
  2. W **ról systemu lokacji** okienku, kliknij prawym przyciskiem myszy **serwera lokacji** roli, a następnie wybierz pozycję **Usuń rolę**.
  3. Kliknij prawym przyciskiem myszy na serwerze lokacji w trybie pasywnym, a następnie wybierz pozycję **usunąć**.
  4. Po odinstalowaniu serwera lokacji, na serwerze lokacji głównej active Uruchom ponownie usługę **CONFIGURATION_MANAGER_UPDATE**.




**Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.**  

<!--  Rough Section Template
##  FEATURE

### Procedure 1
### Try it out!  
 Try to complete the following tasks and then send us **Feedback** from the **Home** tab of the Ribbon to let us know how it worked:
 -  Task 1
 -  Task 2              
-->

## <a name="improvements-for-specifying-script-parameters-when-you-deploy-powershell-scripts-from-configuration-manager"></a>Ulepszenia określając Parametry skryptu, podczas wdrażania skryptów programu PowerShell z programu Configuration Manager
<!-- 1236459 -->

Za pomocą konfiguracji i jego nowszych wersjach 1706 Manager, można [tworzenia i uruchamiania skryptów programu PowerShell z poziomu konsoli programu Configuration Manager](/sccm/apps/deploy-use/create-deploy-scripts).

W [Technical Preview 1707](/sccm/core/get-started/capabilities-in-technical-preview-1707#add-parameters-when-you-deploy-powershell-scripts-from-configuration-manager), możemy rozwinięty w tej funkcji, aby umożliwić programowi Configuration Manager odczytywać Parametry skryptu.

W tej wersji Technical Preview możemy zostały rozszerzone możliwości Parametry skryptu do wykrywania, które parametry są obowiązkowe i opcjonalnych i wyświetlenie monitu o wprowadzenie tych.

### <a name="try-it-out"></a>Wypróbuj

1. Postępuj zgodnie z instrukcjami, aby [tworzenia i uruchamiania skryptów programu PowerShell z poziomu konsoli programu Configuration Manager](/sccm/apps/deploy-use/create-deploy-scripts).
2. Na nowym **Parametry skryptu** strony **Kreatora tworzenia skryptu**, wybierz parametr, a następnie edytować jej wartości.
Kreator wyświetla parametry, które są obowiązkowe i opcjonalnych.
4. Po zakończeniu edytowania parametrów, Zakończ pracę kreatora.

Po uruchomieniu skryptu, będzie on używać żadnych wartości parametrów, które zostały skonfigurowane. Jeśli nie skonfigurowano to parametr obowiązkowy, użytkownik końcowy poprosimy Cię o Podaj parametr, po uruchomieniu skryptu.

## <a name="management-insights"></a>Informacje na temat technologii zarządzania
<!-- 1353967 -->
Można teraz uzyskać wgląd w bieżący stan środowiska na podstawie analizy danych w bazie danych lokacji. Szczegółowe informacje ułatwiają lepszego zrozumienia środowiska i podejmij działania oparte na wiedzę. Przejrzyj informacje na temat technologii zarządzania w konsoli programu Configuration Manager pod adresem **administracji** > **Insights zarządzania** > **wszystkie informacje na temat technologii**. W tej wersji poniższe szczegółowe informacje są dostępne:

- **Aplikacje bez wdrożeń**: Wyświetla listę aplikacji w danym środowisku, które nie ma aktywnych wdrożeń. Dzięki temu można znaleźć oraz usunąć nieużywane aplikacje, aby uprościć na liście aplikacji wyświetlane w konsoli.
- **Puste kolekcje**: Zawiera kolekcje w danym środowisku, które mają żadnych elementów członkowskich. Można usunąć te kolekcje, aby uprościć listy wyświetlane, gdy na przykład wdrażania obiektów, kolekcji.


## <a name="restart-computers-from-the-configuration-manager-console"></a>Uruchom ponownie komputer za pomocą konsoli programu Configuration Manager   
<!-- 1356283 -->
Począwszy od tej wersji, można użyć konsoli programu Configuration Manager do identyfikowania urządzenia klienckie, które wymagają ponownego uruchomienia a następnie użyć akcji powiadamiania klienta uruchomić je ponownie.

Aby zidentyfikować urządzenia, które oczekują na ponowne uruchomienie komputera, przejdź do **zasoby i zgodność** > **urządzeń** i wybrać odpowiednią kolekcję z urządzeniami, które mogą wymagać ponownego uruchomienia komputera. Po wybraniu kolekcji można wyświetlić stan dla każdego urządzenia w okienku szczegółów w nowej kolumnie o nazwie **oczekiwanie na ponowny rozruch**. Każde urządzenie ma wartość **tak**, lub **nr**.

Aby utworzyć powiadomienie klienta, aby ponownie uruchomić urządzenie:
1.  Znajdź urządzenie, którego chcesz ponownie uruchomić komputer w węźle urządzenia w konsoli.
2.  Kliknij prawym przyciskiem myszy na urządzeniu, wybierz opcję **powiadomienie klienta**, a następnie wybierz **ponowny rozruch**. Spowoduje to otwarcie okna informacje o ponownym uruchomieniu. Kliknij przycisk **OK** o potwierdzenie żądania ponownego uruchomienia.

Po otrzymaniu powiadomienia przez klienta, **Centrum oprogramowania** zostanie otwarte okno powiadomienia informują użytkownika o ponowne uruchomienie. Domyślnie uruchomiony ponownie po upływie 90 minut. Można zmodyfikować czas ponownego uruchamiania, konfigurując [ustawień klienta](/sccm/core/clients/deploy/configure-client-settings). Ustawienia zachowania ponownego uruchamiania znajdują się na [ponownego uruchomienia komputera](/sccm/core/clients/deploy/about-client-settings#computer-restart) karta Ustawienia domyślne.


### <a name="try-it-out"></a>Wypróbuj
Spróbuj wykonać następujące zadania, a następnie wyślij do nas **opinii** z **Home** kartę na Wstążce, aby poinformować nas, jak Ci poszło:
1.  Wdrażanie aplikacji lub aktualizacji do urządzenia, które będzie wymagać tego urządzenia, aby uruchomić ponownie, aby zakończyć instalację.
2.  Znajdź urządzenia w **zasoby i zgodność** > **urządzeń** węzła konsoli i Potwierdź Wyświetla **tak** w **oczekiwanie na ponowny rozruch** kolumny. Może potrwać maksymalnie 20 minut, aż Stan Oczekiwanie na ponowny rozruch zostaną odzwierciedlone w konsoli.
3.  Monitorowanie urządzeń, aby upewnić się, że powiadomienia programu Software Center otwiera i że pomyślnie ponownego uruchomienia urządzenia.


## <a name="software-center-customization"></a>Dostosowywanie Centrum oprogramowania
<!-- 1351224 -->
Można dodać znakowanie elementów przedsiębiorstwa i określ widoczność karty w Centrum oprogramowania. Można dodać nazwę firmy określonego programu Software Center, ustawić motyw kolorów konfiguracji programu Software Center, ustawienie logo firmy i ustawienie kartach widoczny na urządzeniach klienckich.

### <a name="customize-software-center"></a>Dostosowywanie Centrum oprogramowania

Aby zmodyfikować Centrum oprogramowania:

1. W **programu Configuration Manager** konsoli, wybierz **administracji** > **ustawień klienta**. Polecenie wystąpienia ustawienie żądaną klienta.
2. Na **Home** karcie **właściwości** grupy, wybierz **właściwości**.
3. W **ustawienia domyślne** oknie dialogowym wybierz **Centrum oprogramowania**.
4. Wybierz **tak** do **wybierz nowe ustawienia, aby określić informacje o firmie** Aby włączyć ustawienia dostosowywania Centrum oprogramowania.
5. Typ użytkownika **nazwa firmy**.
6. Wybierz użytkownika **schemat w programie Software Center kolorów**.
7. Kliknij przycisk **Przeglądaj** można przejść do logo w programie Software Center. Logo musi być formatem JPEG lub PNG 400 x 100 pikseli o maksymalnym rozmiarze 750 KB.
8. Wybierz **tak** uwidocznić karty w Centrum oprogramowania na urządzeniach klienckich. Co najmniej jedną kartę musi być widoczny:

    -  Włącz kartę aplikacje
    -  Włącz kartę Aktualizacje
    -  Włącz kartę systemów operacyjnych
    -  Włącz kartę Stan instalacji
    -  Włącz kartę zgodności urządzenia
    -  Włącz kartę Opcje

### <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej o zarządzaniu aplikacjami w programie Configuration Manager, zobacz [wprowadzenie do zarządzania aplikacjami w programie System Center Configuration Manager](\sccm\apps\understand\introduction-to-application-management).
