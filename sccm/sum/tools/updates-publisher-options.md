---
title: Skonfiguruj opcje | Dokumentacja firmy Microsoft
description: "Skonfiguruj opcje za pomocą programu System Center Updates Publisher"
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4e620080-5400-45bb-87c2-fbdbc8aeacac
caps.latest.revision: 1
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31819a1df4e63e1114682490a9b3c3b4e5c99cfa
ms.openlocfilehash: b66ed0a5e1c87d8c82853da86e3d55b0e2c043bb
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="configure-options-for-updates-publisher"></a>Skonfiguruj opcje Updates Publisher

*Dotyczy: System Center Updates Publisher*

Przejrzyj i skonfiguruj opcje i powiązane ustawienia, które wpływają na działanie Updates Publisher.

Aby uzyskać dostęp do opcji Updates Publisher, w lewym górnym rogu konsoli kliknij **Updates Publisher** **właściwości** karcie, a następnie wybierz **opcje**.

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
Należy skonfigurować Updates Publisher do pracy z serwerem aktualizacji, takich jak systemu Windows serwera Update Services (WSUS), zanim możliwe [publikowanie aktualizacji](/sccm/sum/tools/manage-updates-with-updates-publisher#publish-updates-and-bundles). Należy określić serwer, publikowanie metody do nawiązania połączenia z tym serwerem podczas zdalnego z konsoli, a jest certyfikat podpisywania aktualizacji.

-   **Konfigurowanie serwera aktualizacji**. Podczas konfigurowania serwera aktualizacji, aby wszystkie lokacje podrzędne mają dostęp do aktualizacji, które można opublikować wybierz najwyższego poziomu serwera programu WSUS (serwera aktualizacji) w hierarchii programu Configuration Manager.

  Jeśli serwer aktualizacji jest zdalnie z serwera aktualizacji wydawcy, określ pełną nazwę domeny (FQDN) serwera, a jeśli będą łączyć za pomocą protokołu SSL. Podczas łączenia za pomocą protokołu SSL, domyślnym portem zmienia się z 8530 do 8531. Upewnij się, że ustawiony port dopasowuje co to jest używany przez serwer aktualizacji.

    > [!TIP]  
    > Jeśli serwer aktualizacji nie zostanie skonfigurowane, mogą nadal używać Updates Publisher utworzenia aktualizacji oprogramowania.

-   **Konfigurowanie certyfikatu podpisywania**. Należy skonfigurować i pomyślnie nawiązywania połączenia z serwerem aktualizacji, aby można było skonfigurować certyfikat podpisywania.

    Updates Publisher używa certyfikatu podpisywania do podpisania aktualizacji oprogramowania, które są publikowane na serwerze aktualizacji. Publikowanie kończy się niepowodzeniem, jeśli certyfikat cyfrowy nie jest dostępny w magazynie certyfikatów na serwerze aktualizacji lub komputer z uruchomioną wydawcy aktualizacji.

    Aby uzyskać więcej informacji na temat dodawania certyfikatu do magazynu certyfikatów, zobacz [certyfikatów i zabezpieczeń dla wydawcy aktualizacji](/sccm/sum/tools/updates-publisher-security).

    Jeśli certyfikat nie zostanie wykryta automatycznie dla serwera aktualizacji, wybierz jedną z następujących czynności:

    -   **Przeglądaj**: Przeglądania jest dostępna tylko w przypadku, gdy serwer aktualizacji jest zainstalowany na serwerze, na którym korzystania z konsoli. Po wybraniu certyfikatu, musisz wybrać **Utwórz** dodać ten certyfikat do magazynu certyfikatów usługi WSUS na serwerze aktualizacji. Należy wprowadzić **PFX** hasło pliku certyfikatów wybranych przez tę metodę.

    -   **Utwórz:** Ta opcja służy do tworzenia nowego certyfikatu. To również dodaje certyfikat do magazynu certyfikatów usługi WSUS na serwerze aktualizacji.

    **W przypadku utworzenia własnego certyfikatu podpisywania**, skonfiguruj następujące opcje:

    -   Włącz **Zezwalaj na eksportowanie klucza prywatnego** opcji.

    -   Ustaw **użycie klucza** do podpisu cyfrowego.

    -   Ustaw **minimalny rozmiar klucza** wartość równa lub większa niż 2048 bitów.

    Użyj **Usuń** opcję, aby usunąć certyfikat z magazynu certyfikatów usługi WSUS. Ta opcja jest dostępna, gdy serwer aktualizacji jest kontem lokalnym można użyć konsoli aktualizuje wydawcy lub gdy użyto **SSL** do nawiązania połączenia z serwerem zdalnym aktualizacji.

## <a name="configmgr-server"></a>Serwer programu ConfigMgr
Użyj tych opcji, jeśli korzystasz z programu Configuration Manager z programem Updates Publisher.

-   **Określ serwer programu Configuration Manager:** Po włączeniu obsługi programu Configuration Manager, należy określić lokalizację serwera lokacji najwyższego poziomu w hierarchii programu Configuration Manager. Jeśli serwer zdalny instalacyjnej Updates Publisher, określ nazwę FQDN serwera lokacji. Wybierz **Testuj połączenie** zapewnienie można połączyć się z serwerem lokacji.

-   **Konfigurowanie progów:** Progi są używane podczas publikowania aktualizacji przy użyciu typu publikacji automatyczny. Wartości progowe ustalić po opublikowaniu pełnej zawartości dla aktualizacji, a nie tylko metadane. Aby dowiedzieć się więcej typów publikacji, zobacz [przypisać aktualizacje do publikacji](/sccm/sum/tools/manage-updates-with-updates-publisher#assign-updates-and-bundles-to-a-publication)

    Można co najmniej jedno z następujących progów:

    -   **Żądany Próg liczby klienta:** Definiuje liczbę klientów należy zażądać aktualizacji, przed wydawcy aktualizuje automatycznie opublikować pełnego zestawu zawartości tej aktualizacji. Aż do określonej liczby klientów żądanie aktualizacji, tylko metadane aktualizacji została opublikowana.

    -   **Próg wielkości źródła pakietu (MB):** Zapobiega to automatycznego publikowania aktualizacji, których rozmiar przekracza rozmiar, które określisz. Jeśli rozmiar aktualizacji przekracza tę wartość, jest publikowana tylko metadane. Aktualizacje, które są mniejsze niż określony rozmiar może mieć ich pełnej zawartości opublikowane.

## <a name="proxy-settings"></a>Ustawienia serwera proxy
Updates Publisher używa ustawień serwera proxy podczas importowania katalogów oprogramowania z Internetu lub publikowanie aktualizacji w Internecie.

-   Określ nazwę FQDN lub adres IP serwera proxy. IPv4 i IPv6 są obsługiwane.

-   Serwer proxy uwierzytelnia użytkowników do dostępu do Internetu, należy określić nazwę systemu Windows. Zasada uniwersalnym (nazwy UPN) nie jest obsługiwane.

## <a name="trusted-publishers"></a>Zaufani wydawcy
Podczas importowania katalogu aktualizacji źródła ten katalog (oparte na certyfikacie) jest dodawana jako zaufanego wydawcę. Podobnie podczas publikowania aktualizacji źródła certyfikatu aktualizacji jest dodawane jako zaufanego wydawcę.

Można wyświetlić szczegóły certyfikatu dla każdego wydawcy i usunąć wydawcy z listy zaufanych wydawców.

Zawartość z wydawcy, które nie są zaufane potencjalnie może uszkodzić komputerów klienckich, gdy klient wyszukuje aktualizacje. Należy zaakceptować zawartość tylko z zaufanych wydawców.

## <a name="advanced"></a>Zaawansowane
Zaawansowane opcje są następujące:

-   **Lokalizacja repozytorium:** Wyświetlanie i modyfikowanie lokalizacji pliku bazy danych, **scupdb.sdf**. Ten plik jest repozytorium Updates Publisher.

-   **Sygnatura czasowa:** Po włączeniu sygnatura czasowa jest dodawany do aktualizacji możesz znak, który identyfikuje po podpisaniu. Po wygaśnięciu certyfikatu podpisywania można aktualizacji, który został podpisany, gdy certyfikat jest nieprawidłowy. Domyślnie nie można wdrożyć aktualizacji oprogramowania po wygaśnięciu certyfikatu podpisywania.

-   **Sprawdź dostępność aktualizacji subskrybowanego wykazów:** Każdym uruchomieniu Updates Publisher, jego może automatycznie sprawdzaj aktualizacje wykazów, które subskrybujesz. W przypadku odnalezienia aktualizacji katalogu szczegóły są przekazywane jako **ostatnie alerty** w **Przegląd** okna **aktualizacje obszaru roboczego**.

-   **Odwołania certyfikatów:** Wybierz tę opcję, aby włączyć sprawdzanie odwołania certyfikatu.

-   **Publikowanie lokalnego źródła:** Updates Publisher można użyć lokalnej kopii aktualizacji, który publikujesz przed pobraniem tej aktualizacji z Internetu. Lokalizacja musi być folderu na komputerze z uruchomionym Updates Publisher. Domyślnie jest to lokalizacja **Moje Documents\LocalSourcePublishing.** Użyj, gdy zostały wcześniej pobrane co najmniej jednej aktualizacji lub zmian do aktualizacji, którą chcesz wdrożyć.

-   **Kreator oczyszczania aktualizacji oprogramowania:** Uruchom Kreatora oczyszczania aktualizacji. Kreator wygasa aktualizacje, które znajdują się na serwerze aktualizacji, ale nie w repozytorium Updates Publisher. Zobacz [wygaszanie nieużywanej aktualizacji](#expire-unreferenced-software-updates) więcej szczegółów.

## <a name="updates"></a>Aktualizacje
 Updates Publisher może automatycznie sprawdzać dostępność nowych aktualizacji każdym otwarciu. Można również zrezygnować z do odbierania kompilacje wersji zapoznawczej programu Updates Publisher.

Aby ręcznie Sprawdź dostępność aktualizacji, w konsoli programu Updates Publisher polecenie ![właściwości](media/properties2.png)  
Aby otworzyć **właściwości wydawcy aktualizacji**, a następnie wybierz **sprawdzić aktualizacji**.

Po Updates Publisher znajdzie nowe aktualizacje, wyświetla **aktualizacji dostępnych** okna a następnie można go zainstalować. Można zrezygnować z instalacji aktualizacji, zostanie zaoferowana przy następnym otwarciu konsoli.

## <a name="logging"></a>Rejestrowanie
Updates Publisher rejestruje podstawowe informacje o wydawcy aktualizacji do  **&lt;* ścieżki*&gt;\Windows\Temp\UpdatesPublisher.log**.

Użyj Notatnika lub **CMTrace** do wyświetlania dziennika. CMTrace jest narzędzia plików dziennika programu Configuration Manager i znajduje się w **\SMSSetup\Tools** folderu nośnika źródłowego programu Configuration Manager.

Można zmienić rozmiar dziennika oraz jego poziom szczegółowości.

Po włączeniu rejestrowania bazy danych informacji o kwerendach, które są uruchamiane w bazie danych Updates Publisher są uwzględniane. Korzystanie z bazy danych rejestrowania może prowadzić do zmniejszenie wydajności komputera Updates Publisher.

Aby wyświetlić plik dziennika, w konsoli kliknij ![właściwości](media/properties2.png) otworzyć **właściwości wydawcy aktualizacji**, a następnie wybierz **Wyświetl plik dziennika**.

## <a name="expire-unreferenced-software-updates"></a>Wygaśnięcie aktualizacji oprogramowania nieużywane
Można uruchomić **Kreatora oczyszczania aktualizacji oprogramowania** wygaśnie aktualizacje, które znajdują się na serwerze aktualizacji, ale nie w repozytorium Updates Publisher. To powiadamia menedżera konfiguracji, który następnie usuwa te aktualizacje z dowolnym przyszłych wdrożeń.

Nie można cofnąć czynność wygasa aktualizacji. To zadanie należy wykonać tylko wtedy, gdy masz pewność, że wybrane aktualizacje oprogramowania nie jest już wymagane przez organizację.

### <a name="to-remove-expired-software-updates"></a>Aby usunąć wygasłe aktualizacje oprogramowania
1.  W konsoli programu Updates Publisher, kliknij na ![właściwości](media/properties2.png) otworzyć **właściwości wydawcy aktualizacji**, a następnie wybierz **opcje**.

2.  Wybierz **zaawansowane**, a następnie w obszarze **czystego Kreatora aktualizacji oprogramowania** wybierz **Start**.

3.  Wybierz aktualizacje oprogramowania, aby wygasa, a następnie wybierz **dalej**.

4.  Po przejrzeniu wybranych opcji, należy wybrać **dalej** Zaakceptuj ustawienia i wygaszanie tych aktualizacji.

5.  Po ukończeniu działania kreatora, wybierz **Zamknij** aby zakończyć pracę kreatora.

