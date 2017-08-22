---
title: Monitorowanie aplikacji z konsoli programu System Center Configuration Manager | Dokumentacja firmy Microsoft
description: "Monitorowanie wdrożenia oprogramowania, w tym aktualizacji, ustawień zgodności i aplikacji przy użyciu obszaru roboczego monitorowania w programie Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 784c295c-b8b8-4202-ab9f-665908d49d6d
caps.latest.revision: "5"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: 42d21d10489bffe32b875384f8801686239a0ba4
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="monitor-applications-from-the-system-center-configuration-manager-console"></a>Monitorowanie aplikacji z konsoli programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


W programie System Center Configuration Manager, można monitorować wdrażanie każdego oprogramowania, w tym aktualizacji oprogramowania, ustawień zgodności, aplikacje, sekwencje zadań oraz pakietów i programów. Wdrożenia można monitorować za pomocą **monitorowanie** obszaru roboczego w konsoli programu Configuration Manager lub za pomocą raportów.  

 Aplikacje w programie Configuration Manager obsługują monitorowanie oparte na stanie, co pozwala śledzić ostatni stan wdrożenia aplikacji dla użytkowników i urządzeń. Te komunikaty o stanie zawierają informacje o poszczególnych urządzeniach. Na przykład jeśli aplikacja jest wdrażana w kolekcji użytkowników, w konsoli programu Configuration Manager można wyświetlić stan zgodności oraz cel wdrożenia.  

## <a name="learn-about-compliance-states-in-system-center-configuration-manager"></a>Dowiedz się więcej o stanach zgodności w programie System Center Configuration Manager
 Stan wdrożenia aplikacji może mieć jeden z następujących stanów zgodności:  

-   **Sukces** — wdrożenie aplikacji powiodło się lub aplikacja była już zainstalowana.  

-   **W toku** — wdrożenie aplikacji jest w toku.  

-   **Nieznane** — określenie stanu wdrożenia aplikacji nie było możliwe. Ten stan nie ma zastosowania do wdrożeń z celem **Dostępne**. Ten stan jest zwykle wyświetlany, gdy komunikaty o stanie nie zostały jeszcze odebrane od klienta.  

-   **Wymagania nie zostały spełnione** — aplikacja nie została wdrożona, ponieważ nie była zgodna z zależnością lub zasadą wymagań albo system operacyjny, na którym miała być wdrożona, był nieodpowiedni.  

-   **Błąd** — wdrożenie aplikacji nie powiodło się z powodu błędu.  

Można wyświetlić dodatkowe informacje dotyczące poszczególnych stanów zgodności, w tym podkategorii stanów zgodności oraz liczby użytkowników i urządzeń w tej kategorii. Na przykład stan zgodności **Błąd** zawiera następujące podkategorie:  

-   Wymogi oceny błędu  

-   Błędy związane z zawartością  

-   Błędy instalacji  

 Jeśli do wdrożenia aplikacji ma zastosowanie więcej niż jeden błąd zgodności, można zobaczyć stan zagregowany reprezentujący najniższy poziom zgodności. Na przykład:  

    -   Jeśli użytkownik zaloguje się na dwóch urządzeniach, a aplikacja została pomyślnie zainstalowana na jednym urządzeniu, ale nie można zainstalować na urządzeniu drugiego, zagregowany stan wdrożenia aplikacji dla tego użytkownika będzie wyświetlany jako **błąd**.  

    -   Jeśli aplikacja jest wdrażana dla wszystkich użytkowników, którzy Zaloguj się do komputera, pojawi się wiele wyników wdrożenia dla tego komputera. Jeśli jedno z wdrożeń się nie powiedzie, zagregowany stan wdrożenia dla tego komputera będzie wyświetlany jako **Błąd**.  

Stan wdrożeń pakietów i programów nie jest agregowany.  

 Te podkategorie ułatwiają szybkę identyfikację ważnych problemów związanych z wdrażaniem aplikacji. Można również wyświetlić dodatkowe informacje o urządzeniach, które należą do konkretnej podkategorii stanu zgodności.  

 Zarządzanie aplikacjami w programie Configuration Manager zawiera wiele wbudowanych raportów umożliwiających monitorowanie informacji o aplikacjach i wdrożeniach. Te raporty mają kategorię **Dystrybucja oprogramowania — Monitorowanie aplikacji**.  

 Aby uzyskać więcej informacji o sposobie konfiguracji raportowania w programie Configuration Manager, zobacz [raportowania w programie System Center Configuration Manager](../../core/servers/manage/reporting.md).  

## <a name="monitor-the-state-of-an-application-in-the-configuration-manager-console"></a>Monitor stanu aplikacji w konsoli programu Configuration Manager  

1.  W konsoli programu Configuration Manager wybierz **monitorowanie** > **wdrożeń**.  

3.  Aby wyświetlić szczegóły wdrożenia dotyczące poszczególnych stanów zgodności oraz urządzenia będące w tym stanie, wybierz wdrożenie, a następnie na **Home** karcie **wdrożenia** grupy, wybierz **Wyświetl stan** otworzyć **stan wdrożenia** okienka. W tym okienku są widoczne zasoby z poszczególnymi stanami zgodności. Wybierz zasób, aby wyświetlić bardziej szczegółowe informacje o stanie wdrożenia.  

    > [!NOTE]  
    >  Liczba elementów, które można wyświetlić w okienku **Stan wdrożenia** , jest ograniczona do 20 000. Jeśli chcesz zobaczyć więcej elementów, użyj raportów programu Configuration Manager do wyświetlenia danych stanu aplikacji.  
    >   
    >  Stan typów wdrożenia w okienku **Stan wdrożenia** jest agregowany. Aby wyświetlić bardziej szczegółowe informacje o typach wdrożenia, użyj raportu **Szczegóły błędów infrastruktury aplikacji** w kategorii **Dystrybucja oprogramowania — Monitorowanie aplikacji**.  

4.  Aby wyświetlić ogólne informacje o stanie wdrożenia aplikacji, wybierz wdrożenie, a następnie wybierz **Podsumowanie** karcie **wybrane wdrożenie** okna.  

5.  Aby przejrzeć informacje o typie wdrożenia aplikacji, wybierz wdrożenie, a następnie wybierz **typy wdrożeń** karcie **wybrane wdrożenie** okna.  

Informacje podane w **stan wdrożenia** okienko po wybraniu **Wyświetl stan** na żywo dane z bazy danych programu Configuration Manager. Informacje podane w **Podsumowanie** kartę i **typy wdrożeń** to dane podsumowujące.

Jeśli dane wyświetlane w **Podsumowanie** kartę i **typy wdrożeń** kartę nie pasują do danych jest wyświetlany w obszarze **stan wdrożenia** okienku wybierz **Uruchom Podsumowanie** , aby zaktualizować dane w tych kartach. Domyślny interwał podsumowania wdrożenia aplikacji można skonfigurować w następujący sposób:  

1. W konsoli programu Configuration Manager wybierz **administracji** > **konfiguracja lokacji** > **witryny**.

2. Z **witryny** listy, wybierz lokację, dla której chcesz skonfigurować interwał podsumowania, a następnie w **Home** karcie **ustawienia** grupy, wybierz **składniki podsumowania stanu**.

3. W **składniki podsumowania stanu** oknie dialogowym wybierz **składnik podsumowania wdrażania aplikacji**, a następnie wybierz pozycję **Edytuj**.  

4. W **właściwości składnika podsumowania wdrażania aplikacji** okno dialogowe, skonfiguruj wymagane interwały podsumowania, a następnie wybierz pozycję **OK**.  
