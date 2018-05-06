---
title: Skonfiguruj opcje
titleSuffix: Configuration Manager
description: Skonfiguruj opcje przy użyciu programu System Center Updates Publisher
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.topic: conceptual
ms.assetid: 4e620080-5400-45bb-87c2-fbdbc8aeacac
author: aczechowski
ms.author: aaroncz
manager: dougeby
robots: NOINDEX, NOFOLLOW
ms.openlocfilehash: 497ff025dafcdb135e466a18f2f6661ca0f21a00
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="configure-options-for-updates-publisher"></a>Skonfiguruj opcje dla programu Updates Publisher

*Dotyczy: System Center Updates Publisher*

Przejrzyj i skonfiguruj opcje i powiązane ustawienia, które mają wpływ na działanie programu Updates Publisher.

Aby uzyskać dostęp do opcji Updates Publisher, w lewym górnym rogu konsoli, kliknij polecenie **Updates Publisher** **właściwości** karcie, a następnie wybierz pozycję **opcje**.

![Opcje](media/properties1.png)   


Opcje są podzielone na następujące czynności:

-   Serwer aktualizacji
-   Serwer programu ConfigMgr
-   Ustawienia serwera proxy
-   Zaufani wydawcy
-   Zaawansowane
-   Aktualizacje
-   Rejestrowanie

## <a name="update-server"></a>Serwer aktualizacji
Należy skonfigurować Updates Publisher, aby pracować z serwera aktualizacji, takie jak Windows Server Update Services (WSUS), zanim będzie można [publikowania aktualizacji](/sccm/sum/tools/manage-updates-with-updates-publisher#publish-updates-and-bundles). Należy określić serwer, publikowanie metod na łączenie z tym serwerem, gdy jest zdalnego z konsoli i certyfikat podpisywania aktualizacji.

-   **Konfigurowanie serwera aktualizacji**. Podczas konfigurowania serwera aktualizacji, tak aby wszystkie lokacje podrzędne mają dostęp do aktualizacji, które można opublikować wybierz najwyższego poziomu serwera WSUS (serwera aktualizacji) w hierarchii programu Configuration Manager.

  Jeśli serwer aktualizacji jest zdalnie z serwera programu Updates Publisher, określ w pełni kwalifikowaną nazwę (FQDN) serwera, a jeśli ma zostać nawiązane połączenie za pomocą protokołu SSL. Po ustanowieniu połączenia za pomocą protokołu SSL domyślny port zmienia 8530 do 8531. Upewnij się, że ustawiony port odpowiada elementom używany przez serwer aktualizacji.

    > [!TIP]  
    > Jeśli serwer aktualizacji nie zostanie skonfigurowane, do tworzenia, aktualizacji oprogramowania można nadal używać Updates Publisher.

-   **Konfigurowanie podpisywania certyfikatu**. Należy skonfigurować i pomyślnie nawiązywać połączenia z serwerem aktualizacji, aby można było skonfigurować certyfikat podpisywania.

    Aktualizacje Wydawca używa certyfikatu podpisywania do podpisania aktualizacji oprogramowania, które są publikowane na serwerze aktualizacji. Publikowanie nie powiedzie się, jeśli certyfikat cyfrowy nie jest dostępna w magazynie certyfikatów serwera aktualizacji lub komputerze z uruchomionym programem Updates Publisher.

    Aby uzyskać więcej informacji o dodawaniu certyfikat do magazynu certyfikatów, zobacz [certyfikatach i zabezpieczeniach dla programu Updates Publisher](/sccm/sum/tools/updates-publisher-security).

    Jeśli certyfikat nie zostanie automatycznie wykryta dla serwera aktualizacji, wybierz jedną z następujących czynności:

    -   **Przeglądaj**: Przeglądania jest dostępna tylko w przypadku, gdy serwer aktualizacji jest zainstalowany na serwerze, gdzie uruchomić konsolę. Po wybraniu certyfikatu, musisz wybrać **Utwórz** można dodać certyfikatu do magazynu certyfikatów usług WSUS na serwerze aktualizacji. Należy wprowadzić **PFX** hasło do pliku dla certyfikatów, które wybierz przez tę metodę.

    -   **Utwórz:** Ta opcja umożliwia utworzenie nowego certyfikatu. Spowoduje to również dodanie certyfikatu do magazynu certyfikatów usług WSUS na serwerze aktualizacji.

    **W przypadku utworzenia certyfikatu podpisywania**, skonfiguruj następujące opcje:

    -   Włącz **Zezwalaj na eksportowanie klucza prywatnego** opcji.

    -   Ustaw **użycie klucza** do podpisu cyfrowego.

    -   Ustaw **minimalny rozmiar klucza** wartość równa lub większa niż 2048 bitów.

    Użyj **Usuń** opcję, aby usunąć certyfikat z magazynu certyfikatów usług WSUS. Ta opcja jest dostępna, gdy serwer aktualizacji jest lokalny dla konsoli programu Updates Publisher używasz lub gdy użyto **SSL** do nawiązania połączenia z serwerem aktualizacji zdalnej.

## <a name="configmgr-server"></a>Serwer programu ConfigMgr
Użyj tych opcji, korzystając z programu Configuration Manager z programem Updates Publisher.

-   **Określ serwer programu Configuration Manager:** Po włączeniu pomocy technicznej programu Configuration Manager, należy określić lokalizację serwera lokacji najwyższego poziomu w hierarchii programu Configuration Manager. Jeśli serwer zdalny z instalacji Updates Publisher, określ nazwę FQDN serwera lokacji. Wybierz **Testuj połączenie** aby upewnić się, można połączyć się z serwerem lokacji.

-   **Skonfiguruj progi:** Progi są używane podczas publikowania aktualizacji z typem publikacji automatyczny. Wartości progowe ustalić po opublikowaniu pełnej zawartości dla aktualizacji zamiast tylko metadane. Aby dowiedzieć się więcej typów publikacji, zobacz [przypisać aktualizacji do publikacji](/sccm/sum/tools/manage-updates-with-updates-publisher#assign-updates-and-bundles-to-a-publication)

    Można co najmniej jednej z następujących progów:

    -   **Żądana Próg liczby klientów:** Definiuje liczbę klientów, należy zażądać aktualizacji przed Updates Publisher automatycznie opublikować pełny zestaw zawartości tej aktualizacji. Dopóki aktualizacja poprosić o określoną liczbę klientów, jest publikowany tylko metadane aktualizacji.

    -   **Próg rozmiaru źródła pakietu (MB):** Zapobiega to automatycznego publikowania aktualizacji, które przekraczają rozmiar, które określisz. Jeśli rozmiar aktualizacji przekracza tę wartość, publikowane są tylko metadane. Aktualizacje, które są mniejsze niż określony rozmiar może mieć ich pełnej zawartości opublikowane.

## <a name="proxy-settings"></a>Ustawienia serwera proxy
Updates Publisher używa ustawień serwera proxy podczas importowania katalogi oprogramowania z Internetu lub publikowania aktualizacji przez Internet.

-   Określ nazwę FQDN lub adres IP serwera proxy. IPv4 i IPv6 są obsługiwane.

-   Jeśli serwer proxy uwierzytelnia użytkowników do dostępu do Internetu, należy określić nazwę systemu Windows. Nazwa zasady uniwersalnych (UPN) nie jest obsługiwana.

## <a name="trusted-publishers"></a>Zaufani wydawcy
Podczas importowania katalogu aktualizacji, źródła w tym katalogu (oparte na certyfikacie), jest dodawana jako zaufanego wydawcę. Podobnie podczas publikowania aktualizacji źródło certyfikatu aktualizacji jest dodawana jako zaufanego wydawcę.

Możesz wyświetlić szczegóły certyfikatu dla każdego wydawcy i usunąć wydawcy z listy zaufanych wydawców.

Zawartość od wydawców, które nie są zaufane może być szkodliwe komputerów klienckich, gdy klient skanuje w poszukiwaniu aktualizacji. Należy zaakceptować zawartość tylko z zaufanych wydawców.

## <a name="advanced"></a>Zaawansowane
Zaawansowane opcje są następujące:

-   **Lokalizacja repozytorium:** Wyświetlanie i modyfikowanie lokalizacja pliku bazy danych, **scupdb.sdf**. Ten plik jest repozytorium dla programu Updates Publisher.

-   **Sygnatura czasowa:** Po włączeniu sygnatury czasowej jest dodawany do aktualizacji możesz znak, który identyfikuje po podpisaniu. Po wygaśnięciu certyfikatu podpisywania można aktualizacji, który został podpisany, gdy certyfikat był nieprawidłowy. Domyślnie nie można wdrożyć aktualizacji oprogramowania po wygaśnięciu certyfikatu podpisywania.

-   **Sprawdź, czy są aktualizacje do subskrybowanego katalogów:** Każdym uruchomieniu Updates Publisher, może ono automatycznie sprawdzić aktualizacje katalogi, które subskrybujesz. Po znalezieniu aktualizacji katalogu szczegółowe informacje są przekazywane jako **ostatnie alerty** w **omówienie** okna **aktualizacji obszaru roboczego**.

-   **Odwoływanie certyfikatów:** Wybierz tę opcję, aby włączyć sprawdzanie odwołań certyfikatów.

-   **Publikowanie lokalne źródło:** Updates Publisher można użyć kopii lokalnej aktualizacji, które publikują przed pobraniem tej aktualizacji z Internetu. Lokalizacja musi być folderem na komputerze z uruchomionym programem Updates Publisher. Domyślnie ta lokalizacja jest **Documents\LocalSourcePublishing Moje.** Użyj go, jeśli wcześniej pobrano co najmniej jednej aktualizacji lub zmian do aktualizacji, które chcesz wdrożyć.

-   **Kreator czyszczenia aktualizacji oprogramowania:** Uruchom Kreatora oczyszczania aktualizacji. Kreator wygasa aktualizacje na serwerze aktualizacji, ale nie w repozytorium Updates Publisher. Zobacz [wygaśnie nieużywane aktualizacje](#expire-unreferenced-software-updates) więcej szczegółów.

## <a name="updates"></a>Aktualizacje
 Updates Publisher można automatycznie sprawdzać dostępność nowych aktualizacji każdym razem, gdy zostanie otwarty. Można także włączyć do odbierania kompilacji wersji zapoznawczej programu Updates Publisher.

Aby ręcznie Sprawdź dostępność aktualizacji w konsoli programu Updates Publisher polecenie ![właściwości](media/properties2.png)  
Aby otworzyć **właściwości wydawcy aktualizacji**, a następnie wybierz pozycję **Wyszukaj aktualizację**.

Po Updates Publisher znajdzie nowe aktualizacje, wyświetla **aktualizacji dostępnych** okna, a następnie można go zainstalować. Jeśli wybierzesz nie, zainstaluj aktualizację, więc jest oferowany przy następnym otwarciu konsoli.

## <a name="logging"></a>Rejestrowanie
Updates Publisher rejestruje podstawowych informacji dotyczących programu Updates Publisher, aby  **&lt; *ścieżki*&gt;\Windows\Temp\UpdatesPublisher.log**.

Użyj Notatnik lub **CMTrace** Aby przejrzeć dziennik. CMTrace jest narzędzia plików dziennika programu Configuration Manager i znajduje się w **\SMSSetup\Tools** folderu nośnika źródłowego programu Configuration Manager.

Możesz zmienić rozmiar dziennika oraz jego poziom szczegółowości.

Po włączeniu rejestrowania bazy danych informacji o zapytaniach, które są uruchamiane bazy danych programu Updates Publisher są uwzględniane. Korzystanie z bazy danych rejestrowania może spowodować zmniejszenie wydajności komputera Updates Publisher.

Aby wyświetlić plik dziennika, w konsoli kliknij ![właściwości](media/properties2.png) otworzyć **właściwości wydawcy aktualizacji**, a następnie wybierz pozycję **Wyświetl plik dziennika**.

## <a name="expire-unreferenced-software-updates"></a>Wygaśnięcie aktualizacji oprogramowania bez odwołań
Można uruchomić **Kreatora oczyszczania aktualizacji oprogramowania** wygaśnie aktualizacje na serwerze aktualizacji, ale nie w repozytorium Updates Publisher. To powiadamia menedżera konfiguracji, który następnie usuwa je z wszystkich przyszłych wdrożeń.

Nie można cofnąć czynność wygasa aktualizacji. To zadanie należy wykonać tylko wtedy, gdy masz pewność, że wybrane aktualizacje oprogramowania nie są już wymagane przez Twoją organizację.

### <a name="to-remove-expired-software-updates"></a>Aby usunąć wygasłe aktualizacje oprogramowania
1.  W konsoli programu Updates Publisher, kliknij polecenie ![właściwości](media/properties2.png) otworzyć **właściwości wydawcy aktualizacji**, a następnie wybierz pozycję **opcje**.

2.  Wybierz **zaawansowane**, a następnie w obszarze **czystą Kreator aktualizacji oprogramowania** wybierz **Start**.

3.  Wybierz aktualizacje oprogramowania, które chcesz wygasa, a następnie wybierz pozycję **dalej**.

4.  Po przejrzeniu wybranych opcji, należy wybrać **dalej** zaakceptuj wartości i wygaśnie te aktualizacje.

5.  Po zakończeniu pracy kreatora wybierz **Zamknij** aby zakończyć pracę kreatora.
