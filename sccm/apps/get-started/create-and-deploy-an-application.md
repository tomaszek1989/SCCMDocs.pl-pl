---
title: "Tworzenie i wdrażanie aplikacji | Dokumentacja firmy Microsoft"
description: "Tworzenie i wdrażanie aplikacji zawierającej aplikacji biznesowych — i Dowiedz się, jak skutecznie zarządzać aplikacjami."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3bd1e487-ea18-43c1-b7c3-acbd9b86d429
caps.latest.revision: 15
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6516db6f4c09fdd173b498c58ccc411847752c4e
ms.openlocfilehash: bbbf278f5d31c51bfe061dd44e170f7ab1ca70ad
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="create-and-deploy-an-application-with-system-center-configuration-manager"></a>Tworzenie i wdrażanie aplikacji przy użyciu programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

W tym temacie możesz przejść bezpośrednio w i tworzenie aplikacji z System Center Configuration Manager. W tym przykładzie będzie tworzenie i wdrażanie aplikacji, która zawiera aplikacji biznesowych komputery z systemem Windows o nazwie **Contoso.msi**, musi być zainstalowany na wszystkie komputery z systemem Windows 10 w firmie. Po drodze dowiesz się o wielu czynności, które można wykonać, aby skutecznie zarządzać aplikacjami.  

 Ta procedura jest przeznaczona do zapewnia Przegląd sposobu tworzenia i wdrażania aplikacji programu Configuration Manager. Jednak nie obejmuje wszystkich konfiguracji opcji lub sposób tworzenia i wdrażania aplikacji na innych platformach.  

 Aby uzyskać szczegółowe informacje, które mają zastosowanie do wszystkich platform zobacz jeden z następujących tematów:  

-   [Tworzenie aplikacji systemu Windows](../../apps/get-started/creating-windows-applications.md)  
-   [Tworzenie aplikacji systemu iOS](../../apps/get-started/creating-ios-applications.md)  
-   [Tworzenie aplikacji systemu Android](../../apps/get-started/creating-android-applications.md)  
-   [Tworzenie aplikacji Windows Phone](../../apps/get-started/creating-windows-phone-applications.md)  
-   [Tworzenie aplikacji dla komputerów Mac komputera](../../apps/get-started/creating-mac-computer-applications.md)  
-   [Tworzenie aplikacji serwera z systemem Linux i UNIX](../../apps/get-started/creating-linux-and-unix-server-applications.md)
-   [Tworzenie aplikacji Windows Embedded](../../apps/get-started/creating-windows-embedded-applications.md)


Jeśli już znasz aplikacji programu Configuration Manager, można pominąć ten temat. Jednak warto przejrzeć [tworzenia aplikacji](../../apps/deploy-use/create-applications.md) Aby dowiedzieć się więcej o opcjach, które są dostępne podczas tworzenia i wdrażania aplikacji.  

## <a name="before-you-start"></a>Przed rozpoczęciem  

Upewnij się, że zostało sprawdzone informacje w [wprowadzenie do zarządzania aplikacjami](/sccm/apps/understand/introduction-to-application-management) tak, aby zostały przygotowane lokację do zainstalowania aplikacji i zrozumienie terminologii, który jest używany w tym temacie.  

 Ponadto upewnij się, że instalacja plików dla **Contoso.msi** aplikacji znajdują się w łatwo dostępnej lokalizacji w sieci.  

## <a name="create-the-configuration-manager-application"></a>Tworzenie aplikacji programu Configuration Manager  

### <a name="to-start-the-create-application-wizard-and-create-the-application"></a>Aby uruchomić Kreatora tworzenia aplikacji i tworzenie aplikacji  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **zarządzania aplikacjami** > **aplikacji**.  

3.  Na **Home** w karcie **Utwórz** grupy, wybierz **tworzenie aplikacji**.  

4.  Na **ogólne** strony **Kreatora tworzenia aplikacji**, wybierz **automatycznie Wykryj informacje o tej aplikacji z plików instalacyjnych**. To wstępnie wypełnia niektóre informacje w kreatorze informacje, które są wyodrębniane z instalacji pliku .msi. Następnie określ następujące informacje:  

    -   **Typ**: Wybierz **Instalatora Windows (\*pliku .msi)**.  

    -   **Lokalizacja**: Wprowadź lokalizację (lub wybierz **Przeglądaj** aby wybrać lokalizację) pliku instalacyjnego **Contoso.msi**. Należy zauważyć, że lokalizacja musi zostać określona w postaci  *\\\Server\Share\File* programu Configuration Manager do lokalizacji plików instalacji.  

    Otrzymasz z coś, co przypomina poniższy zrzut ekranu:  

    ![Strona kreatora Ogólne zarządzania aplikacji](/sccm/apps/get-started/media/App-management-wizard-general-page.png)  

5.  Wybierz **dalej**. Na **Importuj informacje** strony, zobaczysz niektóre informacje o aplikacji i wszystkie skojarzone pliki, które zostały zaimportowane do programu Configuration Manager. Gdy skończysz, wybierz **dalej** ponownie.  

6.  Na **ogólne informacje** strony, można podać dodatkowe informacje o aplikacji, aby sortować i odszukaj go w konsoli programu Configuration Manager.  

     Ponadto **program instalacyjny** pola pozwala określić pełny wiersz polecenia, który będzie służyć do instalowania aplikacji na komputerach. Aby dodać własne właściwości można edytować (na przykład **/q** do przeprowadzenia instalacji nienadzorowanej).  

    > [!TIP]  
    >  Niektóre pola na tej stronie kreatora mogą być automatycznie wypełniane podczas importowania plików instalacyjnych aplikacji.  

     Otrzymasz z ekranu, która wygląda podobnie do poniższej zrzut ekranu:  

     ![Strona ogólne informacje Kreatora zarządzania aplikacji](/sccm/apps/get-started/media/App-management-wizard-general-information-page.png)  

7.  Wybierz **dalej**. Na stronie Podsumowanie można potwierdzić ustawienia aplikacji i Ukończ pracę kreatora.  

 Po wykonaniu powyższych czynności tworzenie aplikacji zostanie ukończone. Znajdź go, w **Biblioteka oprogramowania** obszaru roboczego, rozwiń węzeł **zarządzania aplikacjami**, a następnie wybierz **aplikacji**. W przedstawionym przykładzie zostaną wyświetlone następujące informacje:  

 ![Grafika końcowego aplikacji](/sccm/apps/get-started/media/Final-app-graphic.png)  

## <a name="examine-the-properties-of-the-application-and-its-deployment-type"></a>Sprawdzanie właściwości aplikacji i jej typu wdrożenia  

Teraz, kiedy zostały utworzone aplikacji, aby można ją ustawienia aplikacji. Aby Sprawdź właściwości aplikacji, wybierz aplikację, a następnie w **Home** karcie w **właściwości** grupy, wybierz **właściwości**.  

 W **< Contoso\> właściwości aplikacji** okno dialogowe, zobaczysz wiele elementów, które można skonfigurować, aby zawęzić zachowanie aplikacji. Aby uzyskać szczegółowe informacje o wszystkich ustawień można skonfigurować, zobacz [tworzenia aplikacji](../../apps/deploy-use/create-applications.md). Dla celów tego przykładu zostaną zmienione tylko niektóre właściwości typu wdrożenia aplikacji.  

 Wybierz **typy wdrożeń** kartę > **aplikacji Contoso** typu wdrożenia > **edytować**.     

Zostanie wyświetlone okno dialogowe podobne do następującego:  

![Strona właściwości aplikacji zarządzania aplikacji](/sccm/apps/get-started/media/App-management-app-properties-page.png)  

## <a name="add-a-requirement-to-the-deployment-type"></a>Dodawanie wymagania do typu wdrożenia  
 Wymagania określają warunki, które muszą zostać spełnione przed zainstalowaniem aplikacji na urządzeniu.  Dostępne są wbudowane wymagania lub utworzyć własny. W tym przykładzie należy dodać zainstalowana aplikacja będzie tylko pobrać na komputery z systemem Windows 10.  

1.  Ze strony właściwości typu wdrożenia został otwarty, wybierz **wymagania** kartę.  

2.  Wybierz **Dodaj** otworzyć **tworzenie wymagania** okno dialogowe.  

3.  W oknie dialogowym **Tworzenie wymagania** określ następujące informacje:  

    -   **Kategoria**: **Urządzenie**  

    -   **Warunek**: **System operacyjny**  

    -   **Reguła typu**: **Wartość**  

    -   **Operator**: **Jeden z**  

    -   Na liście systemów operacyjnych wybierz pozycję **Windows 10**.  

    Zostanie wyświetlone okno dialogowe podobne do następującego:  

    ![Strona wymagania dotyczące zarządzania aplikacji](/sccm/apps/get-started/media/App-management-requirements-page.png)  

4.  Wybierz **OK** zamknąć stronę właściwości otwartego. Następnie wróć do **aplikacji** listy w konsoli programu Configuration Manager.  

> [!TIP]  
>  Wymagania dotyczące może ograniczyć liczbę kolekcji programu Configuration Manager, które są potrzebne. Ponieważ właśnie określono, że aplikacja uzyskać zainstalowana tylko na komputerach z systemem Windows 10, można później wdrażać ją do kolekcji zawierającej komputery z systemem wielu różnych systemów operacyjnych. Jednak aplikacja będzie pobrać zainstalować tylko na komputery z systemem Windows 10.  

## <a name="add-the-application-content-to-a-distribution-point"></a>Dodawanie zawartości aplikacji do punktu dystrybucji  

Następnie do wdrożenia aplikacji na komputerach, upewnij się, że zawartość aplikacji jest kopiowany do punktu dystrybucji. Komputery uzyskują dostęp do punktu dystrybucji do zainstalowania aplikacji.  

> [!TIP]  
>  Aby dowiedzieć się więcej na temat zarządzania zawartością w programie Configuration Manager i punktów dystrybucji, zobacz [zarządzania infrastrukturą zawartości i](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania**.  

2.  W **Biblioteka oprogramowania** obszaru roboczego, rozwiń węzeł **aplikacji**. Następnie na liście aplikacji, wybierz **aplikacji Contoso** utworzony.  

3.  Na **Home** w karcie **wdrożenia** grupy, wybierz **dystrybucji zawartości**.  

4.  Na **ogólne** strony **kreatora dystrybucji zawartości**, sprawdź, czy nazwa aplikacji jest poprawna, a następnie wybierz **dalej**.  

5.  Na **zawartości** Przejrzyj informacje, które zostaną skopiowane do punktu dystrybucji, a następnie wybierz **dalej**.  

6.  Na **miejsce docelowe zawartości** wybierz **Dodaj** zaznacz jeden lub więcej punktów dystrybucji lub grupy punktów dystrybucji, na którym jest instalowany zawartości aplikacji.  

7.  Ukończ pracę kreatora.  

Można sprawdzić, czy zawartość aplikacji został pomyślnie skopiowane do punktu dystrybucji z **monitorowanie** obszaru roboczego, w obszarze **stan dystrybucji** > **stan zawartości**.  

## <a name="deploy-the-application"></a>Wdrażanie aplikacji  

Następnie wdróż aplikację w kolekcji urządzeń w hierarchii. W tym przykładzie należy wdrożyć aplikację na **wszystkie systemy** kolekcji urządzeń.  

> [!TIP]  
>  Należy pamiętać, że tylko komputery z systemem Windows 10 zainstaluj aplikację ze względu na wymagania, które wybrano wcześniej.  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **zarządzania aplikacjami** > **aplikacji**.  

3.  Z listy aplikacji, wybierz aplikację, która utworzone wcześniej (**aplikacji Contoso**), a następnie na **Home** karcie w **wdrożenia** grupy, wybierz **Wdróż**.  

4.  Na **ogólne** strony **Kreatora wdrażania oprogramowania**, wybierz **Przeglądaj** zaznacz **wszystkie systemy** kolekcji urządzeń.  

5.  Na **zawartości** strony, sprawdź, czy wybrano punktu dystrybucji, z którego mają komputery do zainstalowania aplikacji.  

6.  Na **ustawienia wdrażania** upewnij się, że akcja wdrożenia jest ustawiona na **zainstalować**, i w celu wdrożenia wybrano opcję **wymagane**.  

    > [!TIP]  
    >  Ustawiając cel wdrożenia **wymagane**, należy upewnić się, że aplikacja jest zainstalowana na komputerach, które spełniają wymagania, które można ustawić. W przypadku ustawienia wartości **Dostępne**użytkownicy mogą zainstalować aplikację na żądanie z Centrum oprogramowania.  

7.  Na stronie **Planowanie** możesz skonfigurować, kiedy aplikacja zostanie zainstalowana. W ramach tego przykładu wybierz pozycję **Tak szybko jak to możliwe po dostępnej godzinie**.  

8.  Na **środowisko użytkownika** wybierz **dalej** zaakceptować wartości domyślne.  

9. Ukończ pracę kreatora.  

Informacje zawarte w następujących **monitorowanie aplikacji** sekcję, aby wyświetlić stan wdrożenia aplikacji.  

## <a name="monitor-the-application"></a>Monitorowanie aplikacji  
 W tej sekcji zostaną wykonane rzucić okiem na stan wdrożenia aplikacji, która została wdrożona.  

### <a name="to-review-the-deployment-status"></a>Aby sprawdzić stan wdrożenia  

1.  W konsoli programu Configuration Manager wybierz **monitorowanie** > **wdrożeń**.  

3.  Z listy wdrożeń wybierz pozycję **Aplikacja Contoso**.  

4.  Na **Home** w karcie **wdrożenia** grupy, wybierz **Wyświetl stan**.  

5.  Wybierz jedną z następujących kart, aby zobaczyć więcej aktualizacji stanu wdrożenia aplikacji:  

    -   **Powodzenie**: Aplikacja została pomyślnie zainstalowana na komputerach wskazane.  

    -   **W toku**: Aplikacja nie zostało jeszcze zakończone instalacji.  

    -   **Błąd**: Instalowanie aplikacji na komputerach wskazanej wystąpił błąd. Wyświetlane są również dodatkowe informacje o błędzie.  

    -   **Wymagania nie zostały spełnione**: Podjęto próbę nie instalacji na urządzeniach wskazane, ponieważ mogły nie spełniać wymagań dotyczących konfiguracji (w tym przykładzie, ponieważ nie można uruchamiać w systemie Windows 10).  

    -   **Nieznany**: Menedżer konfiguracji nie może zgłosić stan wdrożenia. Sprawdź go ponownie później.  

> [!TIP]  
>  Istnieje kilka sposobów wdrożenia aplikacji można monitorować. Aby uzyskać szczegółowe informacje, zobacz [monitorowania aplikacji](/sccm/apps/deploy-use/monitor-applications-from-the-console).  

## <a name="end-user-experience"></a>Środowisko użytkownika końcowego  

Użytkownicy, którzy mają komputery, które są zarządzane przez program Configuration Manager i uruchamianie systemu Windows 10 wyświetlony komunikat z informacją o ich zainstalowanie aplikacji Contoso. Po ich zaakceptowaniu instalacji aplikacji są instalowane.  

