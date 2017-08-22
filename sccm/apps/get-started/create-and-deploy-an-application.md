---
title: "Tworzenie i wdrażanie aplikacji | Dokumentacja firmy Microsoft"
description: "Tworzenie i wdrażanie aplikacji zawierającej aplikacji biznesowych z i Dowiedz się, jak skutecznie zarządzać aplikacjami."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3bd1e487-ea18-43c1-b7c3-acbd9b86d429
caps.latest.revision: "15"
caps.handback.revision: "0"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: bbbf278f5d31c51bfe061dd44e170f7ab1ca70ad
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="create-and-deploy-an-application-with-system-center-configuration-manager"></a>Tworzenie i wdrażanie aplikacji przy użyciu programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

W tym temacie możesz od razu i utworzyć aplikację w programie System Center Configuration Manager. W tym przykładzie zostanie utworzona i wdrożona aplikacja, która zawiera aplikacji biznesowych z komputerów z systemem Windows o nazwie **Contoso.msi**, która musi być zainstalowana na wszystkich komputerach z systemem Windows 10 w firmie. Na bieżąco dowiesz się o wiele czynników, które można wykonać, aby efektywnie zarządzać aplikacjami.  

 Celem tej procedury jest przedstawienie sposobu tworzenia i wdrażania aplikacji programu Configuration Manager. Jednak nie obejmuje całą konfigurację opcji, ani sposobu tworzenia i wdrażania aplikacji dla innych platform.  

 Aby uzyskać szczegółowe informacje, które mają zastosowanie do wszystkich platform Zobacz jedną z następujących tematów:  

-   [Tworzenie aplikacji systemu Windows](../../apps/get-started/creating-windows-applications.md)  
-   [Tworzenie aplikacji systemu iOS](../../apps/get-started/creating-ios-applications.md)  
-   [Tworzenie aplikacji systemu Android](../../apps/get-started/creating-android-applications.md)  
-   [Tworzenie aplikacji systemu Windows Phone](../../apps/get-started/creating-windows-phone-applications.md)  
-   [Tworzenie aplikacji dla komputerów Mac](../../apps/get-started/creating-mac-computer-applications.md)  
-   [Tworzenie aplikacji serwerów z systemami Linux i UNIX](../../apps/get-started/creating-linux-and-unix-server-applications.md)
-   [Tworzenie aplikacji systemu Windows Embedded](../../apps/get-started/creating-windows-embedded-applications.md)


Jeśli już znasz z aplikacjami programu Configuration Manager, możesz pominąć ten temat. Jednak warto przejrzeć [tworzenie aplikacji](../../apps/deploy-use/create-applications.md) Aby dowiedzieć się więcej o wszystkich opcjach dostępnych podczas tworzenia i wdrażania aplikacji.  

## <a name="before-you-start"></a>Przed rozpoczęciem  

Upewnij się, że zostało sprawdzone informacje w [wprowadzenie do zarządzania aplikacjami](/sccm/apps/understand/introduction-to-application-management) tak, aby zostały przygotowane witryny, aby zainstalować aplikacje i zapoznaj się z terminologią używaną w tym temacie.  

 Ponadto upewnij się, że pliki instalacyjne **Contoso.msi** aplikacji znajdują się w dostępnej lokalizacji w sieci.  

## <a name="create-the-configuration-manager-application"></a>Tworzenie aplikacji programu Configuration Manager  

### <a name="to-start-the-create-application-wizard-and-create-the-application"></a>Aby uruchomić Kreatora tworzenia aplikacji i tworzenie aplikacji  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **Zarządzanie aplikacjami** > **aplikacji**.  

3.  Na **Home** karcie **Utwórz** grupy, wybierz **tworzenie aplikacji**.  

4.  Na **ogólne** strony **Kreatora tworzenia aplikacji**, wybierz **automatycznie Wykryj informacje o tej aplikacji z plików instalacyjnych**. To wstępnie wypełnia niektóre informacje w Kreatorze informacjami, które są wyodrębniane z pliku instalacyjnego msi. Następnie określ następujące informacje:  

    -   **Typ**: Wybierz **Instalatora Windows (\*pliku .msi)**.  

    -   **Lokalizacja**: Wpisz lokalizację (lub wybierz **Przeglądaj** celu jej wybrania) pliku instalacyjnego **Contoso.msi**. Należy pamiętać, że lokalizacja musi być określona w postaci  *\\\Server\Share\File* programu Configuration Manager można znaleźć plików instalacyjnych.  

    Zostanie wyświetlone okno z coś, która wygląda podobnie Poniższy zrzut ekranu:  

    ![Strona kreatora Ogólne zarządzania aplikacji](/sccm/apps/get-started/media/App-management-wizard-general-page.png)  

5.  Wybierz **dalej**. Na **Importuj informacje** strony, zobaczysz niektóre informacje o aplikacji i skojarzone pliki, które zostały zaimportowane do programu Configuration Manager. Gdy wszystko będzie gotowe, wybierz **dalej** ponownie.  

6.  Na **ogólne informacje** strony, możesz podać dodatkowe informacje o aplikacji, aby ułatwić sortowanie i lokalizowanie jej w konsoli programu Configuration Manager.  

     Ponadto **program instalacyjny** pole pozwala określić pełny wiersz polecenia, która będzie służyć do instalowania aplikacji na komputerach. Można edytować, aby dodać własne właściwości (na przykład **/q** dla instalacji nienadzorowanej).  

    > [!TIP]  
    >  Niektóre pola na tej stronie kreatora mogą być automatycznie wypełniane podczas importowania plików instalacyjnych aplikacji.  

     Zostanie wyświetlone okno z ekranu, która wygląda podobnie do następującego zrzutu ekranu:  

     ![Strona ogólne informacje Kreatora zarządzania aplikacji](/sccm/apps/get-started/media/App-management-wizard-general-information-page.png)  

7.  Wybierz **dalej**. Na stronie Podsumowanie można potwierdzić ustawienia aplikacji, a następnie Zakończ pracę kreatora.  

 Po wykonaniu powyższych czynności tworzenie aplikacji zostanie ukończone. Aby ją znaleźć, w **Biblioteka oprogramowania** obszaru roboczego, rozwiń węzeł **zarządzania aplikacjami**, a następnie wybierz pozycję **aplikacji**. W przedstawionym przykładzie zostaną wyświetlone następujące informacje:  

 ![Grafika ostatecznej aplikacji](/sccm/apps/get-started/media/Final-app-graphic.png)  

## <a name="examine-the-properties-of-the-application-and-its-deployment-type"></a>Sprawdzanie właściwości aplikacji i jej typu wdrożenia  

Teraz, po utworzeniu aplikacji, jeśli zachodzi konieczność można dostosować ustawienia aplikacji. Aby przyjrzeć się właściwości aplikacji, wybierz aplikację, a następnie w **Home** karcie **właściwości** grupy, wybierz **właściwości**.  

 W **< Contoso\> właściwości aplikacji** okno dialogowe, pojawi się wiele elementów, które można skonfigurować tak, aby dostosować zachowanie aplikacji. Aby uzyskać szczegółowe informacje na temat wszystkich ustawień można skonfigurować, zobacz [tworzenie aplikacji](../../apps/deploy-use/create-applications.md). Dla celów tego przykładu zostaną zmienione tylko niektóre właściwości typu wdrożenia aplikacji.  

 Wybierz **typy wdrożeń** kartę > **aplikacja Contoso** typu wdrożenia > **Edytuj**.  

Zostanie wyświetlone okno dialogowe podobne do następującego:  

![Strony właściwości aplikacji zarządzania aplikacjami](/sccm/apps/get-started/media/App-management-app-properties-page.png)  

## <a name="add-a-requirement-to-the-deployment-type"></a>Dodawanie wymagania do typu wdrożenia  
 Wymagania określają warunki, które muszą zostać spełnione przed zainstalowaniem aplikacji na urządzeniu.  Możesz wybrać spośród wbudowanych wymagań lub utworzyć własny. W tym przykładzie należy dodać wymaganie, że aplikacja tylko pobrać zainstalowana na komputerach z systemem Windows 10.  

1.  Ze strony właściwości typu wdrożenia został otwarty, wybierz **wymagania** kartę.  

2.  Wybierz **Dodaj** otworzyć **tworzenie wymagania** okno dialogowe.  

3.  W oknie dialogowym **Tworzenie wymagania** określ następujące informacje:  

    -   **Kategoria**: **Urządzenie**  

    -   **Warunek**: **System operacyjny**  

    -   **Typ reguły**: **Wartość**  

    -   **Operator**: **Jeden z**  

    -   Na liście systemów operacyjnych wybierz pozycję **Windows 10**.  

    Zostanie wyświetlone okno dialogowe podobne do następującego:  

    ![Strony wymagania dotyczące zarządzania aplikacji](/sccm/apps/get-started/media/App-management-requirements-page.png)  

4.  Wybierz **OK** aby zamknąć stronę właściwości otwartego. Następnie wróć do **aplikacji** listy w konsoli programu Configuration Manager.  

> [!TIP]  
>  Wymagania dotyczące może pomóc zmniejszyć liczbę kolekcji programu Configuration Manager, które są potrzebne. Ponieważ właśnie zostało określone, że aplikacja uzyskać zainstalowana tylko na komputerach z systemem Windows 10, możesz później wdrożyć ją do kolekcji zawierającej komputery z systemem wielu różnych systemów operacyjnych. Ale aplikacji zostanie uzyskać zainstalowana tylko na komputerach z systemem Windows 10.  

## <a name="add-the-application-content-to-a-distribution-point"></a>Dodawanie zawartości aplikacji do punktu dystrybucji  

Następnie można wdrożyć aplikacji na komputerach, upewnij się, że zawartość aplikacji został skopiowany do punktu dystrybucji. Komputery dostęp do punktu dystrybucji, aby zainstalować aplikację.  

> [!TIP]  
>  Aby dowiedzieć się więcej na temat punktów dystrybucji i zarządzania zawartością w programie Configuration Manager, zobacz [zarządzanie zawartością i infrastrukturą zawartości](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania**.  

2.  W **Biblioteka oprogramowania** obszaru roboczego, rozwiń węzeł **aplikacji**. Następnie na liście aplikacji zaznacz **aplikacja Contoso** utworzony.  

3.  Na **Home** karcie **wdrożenia** grupy, wybierz **Dystrybuuj zawartość**.  

4.  Na **ogólne** strony **kreatora dystrybucji zawartości**, sprawdź, czy nazwa aplikacji jest prawidłowa, a następnie wybierz **dalej**.  

5.  Na **zawartości** Przejrzyj informacje, które zostaną skopiowane do punktu dystrybucji, a następnie wybierz pozycję **dalej**.  

6.  Na **miejsce docelowe zawartości** wybierz pozycję **Dodaj** zaznacz jeden lub więcej punktów dystrybucji lub grupy punktów dystrybucji, na których chcesz zainstalować zawartość aplikacji.  

7.  Ukończ pracę kreatora.  

Możesz sprawdzić, czy zawartość aplikacji została pomyślnie skopiowane do punktu dystrybucji z **monitorowanie** obszaru roboczego, w obszarze **stan dystrybucji** > **stan zawartości**.  

## <a name="deploy-the-application"></a>Wdrażanie aplikacji  

Następnie wdróż aplikację w kolekcji urządzeń w hierarchii. W tym przykładzie wdrożenia aplikacji na **wszystkie systemy** kolekcji urządzeń.  

> [!TIP]  
>  Należy pamiętać, że tylko komputery z systemem Windows 10 aplikacja zostanie zainstalowana ze względu na wymagania, które wcześniej wybrano.  

1.  W konsoli programu Configuration Manager wybierz **Biblioteka oprogramowania** > **Zarządzanie aplikacjami** > **aplikacji**.  

3.  Z listy aplikacji, wybierz aplikację, którą wcześniej utworzony (**aplikacja Contoso**), a następnie na **Home** karcie w **wdrożenia** grupy, wybierz **Wdróż**.  

4.  Na **ogólne** strony **Kreatora wdrażania oprogramowania**, wybierz **Przeglądaj** wybierz **wszystkie systemy** kolekcji urządzeń.  

5.  Na **zawartości** strony, należy sprawdzić, czy wybrano punkt dystrybucji, z którego komputery mają zainstalować aplikację.  

6.  Na **ustawienia wdrażania** upewnij się, że akcja wdrożenia jest ustawiona na **zainstalować**, a celem wdrożenia jest ustawiona na **wymagane**.  

    > [!TIP]  
    >  Ustawiając cel wdrożenia **wymagane**, należy upewnić się, że aplikacja jest zainstalowana na komputerach, które spełniają wymagania, które można ustawić. W przypadku ustawienia wartości **Dostępne**użytkownicy mogą zainstalować aplikację na żądanie z Centrum oprogramowania.  

7.  Na stronie **Planowanie** możesz skonfigurować, kiedy aplikacja zostanie zainstalowana. W ramach tego przykładu wybierz pozycję **Tak szybko jak to możliwe po dostępnej godzinie**.  

8.  Na **środowisko użytkownika** wybierz pozycję **dalej** zaakceptować wartości domyślne.  

9. Ukończ pracę kreatora.  

Użyj informacji podanych w następujących **monitorowania aplikacji** sekcję, aby wyświetlić stan wdrożenia aplikacji.  

## <a name="monitor-the-application"></a>Monitorowanie aplikacji  
 W tej sekcji zostaną wykonane szybko wyświetlić stan wdrożenia aplikacji, która została wdrożona.  

### <a name="to-review-the-deployment-status"></a>Aby sprawdzić stan wdrożenia  

1.  W konsoli programu Configuration Manager wybierz **monitorowanie** > **wdrożeń**.  

3.  Z listy wdrożeń wybierz pozycję **Aplikacja Contoso**.  

4.  Na **Home** karcie **wdrożenia** grupy, wybierz **Wyświetl stan**.  

5.  Wybierz jedną z następujących kart, aby zobaczyć więcej aktualizacji stanu wdrożenia aplikacji:  

    -   **Powodzenie**: Aplikacja została pomyślnie zainstalowana na wskazanych komputerach.  

    -   **Trwa**: Aplikacja nie została jeszcze ukończona instalacji.  

    -   **Błąd**: Wystąpił błąd podczas instalowania aplikacji na wskazanych komputerach. Wyświetlane są również dodatkowe informacje o błędzie.  

    -   **Wymagania nie zostały spełnione**: Nie instalacji podjęto na wskazanych urządzeniach, ponieważ nie spełniły one skonfigurowanych wymagań (w tym przykładzie, ponieważ nie można uruchamiać w systemie Windows 10).  

    -   **Nieznany**: Nie można zgłosić stanu wdrożenia programu Configuration Manager. Sprawdź go ponownie później.  

> [!TIP]  
>  Istnieje kilka metod monitorowania wdrożenia aplikacji. Aby uzyskać szczegółowe informacje, zobacz [monitorowania aplikacji](/sccm/apps/deploy-use/monitor-applications-from-the-console).  

## <a name="end-user-experience"></a>Środowisko użytkownika końcowego  

Użytkownicy, którzy mają komputery, które są zarządzane przez program Configuration Manager i uruchomiony system Windows 10 komunikat informujący o konieczności zainstalowania aplikacji Contoso. Po zaakceptowaniu instalacji aplikacja zostanie zainstalowana.  
