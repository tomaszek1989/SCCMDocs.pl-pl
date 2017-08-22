---
title: "Zarządzanie katalogami update | Dokumentacja firmy Microsoft"
description: "Zarządzanie katalogami aktualizacji oprogramowania programu System Center Updates Publisher"
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 887f8029-1a3a-423c-a9c1-31dc0d693386
caps.latest.revision: "1"
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.openlocfilehash: 7451d699e0e5e146b0538a57deca595188d113bf
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="manage-software-update-catalogs-in-updates-publisher"></a>Zarządzanie katalogami aktualizacji oprogramowania w Updates Publisher

*Dotyczy: Program System Center Updates Publisher*

Użyj **katalogi** **obszaru roboczego** Zarządzanie katalogami aktualizacji oprogramowania. W tym dodawanie nowych katalogów, zarządzanie istniejące subskrypcje katalogu i importowania informacji o aktualizacjach z wykazu do repozytorium Updates Publisher.

Katalogi aktualizacji oprogramowania zawierają informacje o odpowiednich aktualizacji, które są tworzone przez organizacje innych niż Microsoft. Inne organizacje obejmują własnej organizacji i dostawców oprogramowania innych firm, które zostały zarejestrowane ich katalogi z firmą Microsoft. Katalogi zarejestrowanych od dostawców oprogramowania są nazywane *partnera katalogi*. Katalogi, które należy utworzyć, a które nie są zarejestrowane z firmą Microsoft, są nazywane *użytkownika* katalogów.

## <a name="add-software-update-catalogs"></a>Dodaj katalogi aktualizacji oprogramowania
Należy dodać katalog aktualizacji do programu Updates Publisher, aby można było zarządzać aktualizacje, które zawiera. Po dodaniu wykaz Updates Publisher:
-   Tworzy subskrypcję do tego katalogu, więc można sprawdzić dostępność aktualizacji do tego katalogu.
-   Dodaje do listy w katalogu **Moje katalogi aktualizacji oprogramowania** okna **roboczym katalogi**.  

Informacje o każdego subskrybowanego katalogu są dostępne w konsoli. Informacje obejmują adres URL pobierania lub lokalizację, nazwy firmy lub organizacji, która utworzyła katalogu, a po jego ostatniego zaimportowane lub zmodyfikowany.

Updates Publisher może automatycznie sprawdzać subskrypcji zmiany każdym uruchomieniu. Te ustawienia zostaną skonfigurowane jako [zaawansowanych opcji](/sccm/sum/tools/updates-publisher-options#advanced). Po skonfigurowaniu Updates Publisher odwołuje się do pobierania adresu URL lub lokalizacji informacje dotyczące subskrypcji oraz alerty, gdy istnieją zmiany do katalogu, które zostały wprowadzone od czasu ostatniego zaimportowane do repozytorium.

Aby ręcznie sprawdzić dostępność aktualizacji katalogu, wybierz opcję katalog z **Moje katalogi aktualizacji oprogramowania** listy, a następnie wybierz pozycję **Odśwież** na Wstążce.

Oprócz dodania wykazów i wyświetlanie informacji o subskrybowanego katalogów, możesz:
-  **Edytuj** informacje dotyczące *użytkownika* katalogów.
-  **Usuń** (Usuń) katalogu z programem Updates Publisher.
-  **Importuj** aktualizacje z katalogu do repozytorium Updates Publisher. Po zaimportowaniu aktualizacji, należy zaimportować wszystkie aktualizacje zawarte w tym katalogu. Aktualizacje można wyświetlić w obszarze roboczym aktualizacje, w którym można wybrać i opublikować aktualizacje na serwerze aktualizacji.

> [!NOTE]   
> Powoduje usunięcie katalogu z programem Updates Publisher aktualizacje w tym katalogu usuwana z repozytorium. Nie ma to wpływu na aktualizacje, które zostały opublikowane na serwerze aktualizacji. Aby usunąć serwer aktualizacji, które nie są już w repozytorium aktualizacji, zobacz [wygaśnięcie aktualizacji oprogramowania bez odwołań](/sccm/sum/tools/updates-publisher-options#expire-unreferenced-software-updates).

## <a name="manage-update-catalogs"></a>Zarządzanie katalogami aktualizacji
Można wyświetlić katalogi listy został zaimportowany w **Moje katalogi aktualizacji oprogramowania** okna **roboczym katalogi**. Z tego obszaru roboczego, które można wykonywać następujące czynności:

-   **Dodaj katalog partnera:** Użyj jednej z poniższych, aby znaleźć nowych katalogów partnera:

    -   W konsoli przejdź do **roboczym aktualizacje** > **omówienie**. W **wprowadzenie** okna, wybierz **Dodaj katalogi aktualizacje oprogramowania partnera**.

    -   W konsoli przejdź do **roboczym katalogi** > **Moje katalogi**. Następnie na Wstążce wybierz **Dodaj katalogi**.

-   **Dodaj katalog użytkownika:** W konsoli przejdź do **roboczym katalogi** > **Moje katalogi**. Następnie na Wstążce wybierz **Dodaj katalogi**. Oprócz lokalizację pliku cab należy także określić wydawcy, nazwę i opis do identyfikacji katalogu.


-   **Sprawdź, czy są aktualizacje do katalogów:** Wybierz jeden lub więcej katalogów, a następnie wybierz pozycję **Odśwież** na Wstążce.

-   **Edytowanie katalogu użytkownika:** Wybierz *użytkownika* katalogu, a następnie wybierz pozycję **Edytuj** na Wstążce. Następnie można zmodyfikować właściwości zdefiniowane przez użytkownika.

-   **Usuwanie katalogów:** Wybierz jeden lub więcej katalogów, a następnie wybierz pozycję **Usuń** na Wstążce. Spowoduje to usunięcie katalogu, subskrypcję i aktualizacje z tych katalogów z repozytorium Updates Publisher.

-   **Dodaj aktualizacje z wykazu do repozytorium**: Wybierz **importu** na Wstążce, aby uruchomić **Import Catalog** kreatora. Aby uzyskać więcej infomration, zobacz [importowanie aktualizacji](#import-updates)

## <a name="import-updates"></a>Importowanie aktualizacji
Po zaimportowaniu wykaz Menedżera aktualizacji dodaje aktualizacje z tego katalogu do repozytorium Updates Publisher. Aktualizacje są importowane, można publikować na serwerze aktualizacji, aby były dostępne dla zarządzanych urządzeń.

### <a name="to-import-updates"></a>Aby zaimportować aktualizacje
1.  Aby uruchomić **Import Catalog** kreatora wybierz **importu** na Wstążce w jednym z następujących obszarów roboczych:

    -   Obszar roboczy katalogów

    -   Obszar roboczy aktualizacje

2.  Na **typ importu** wybierz jeden lub więcej katalogów zostały dodane do programu Updates Publisher lub określ ścieżkę do katalogu, nie zostały jeszcze dodane jako subskrypcji. Wybrana opcja **dalej** można wyświetlić podsumowanie ekranu oraz gdy będzie gotowe, wybierz **dalej** można uruchomić importu.

3.  Na **ostrzeżenie o zabezpieczeniach — Weryfikacja katalogu** , przejrzyj certyfikatu katalogu, a gdy będzie gotowe, wybierz opcję **Akceptuj** Aby zaimportować aktualizacje.

    > [!CAUTION]    
    > Akceptować aktualizacje tylko z zaufanych wydawców. Aktualizacje oprogramowania z wydawców niezaufanych mogą też uszkodzić komputery klienckie podczas skanowania w poszukiwaniu aktualizacji.

    >  Jeśli nie ufasz wydawcy, Usuń tego wydawcy z listy zaufanych wydawców. Aby uzyskać więcej informacji na temat akceptowanie katalogi, kliknij przycisk **Powiedz mi więcej** w **ostrzeżenie o zabezpieczeniach — Weryfikacja katalogu** okno dialogowe.

    Jeśli zdecydujesz się na zawsze Akceptuj katalogi od wydawcy, tego wydawcy jest dodawany do [listy zaufanych wydawców](/sccm/sum/tools/updates-publisher-options#trusted-publishers). Możesz przejrzeć i edytować tej listy jako opcja Updates Publisher.

4.  Import pomija importowanie aktualizacji, gdy aktualizacja jest już w repozytorium i jest spełniony jeden z następujących czynności:

    -   Aktualizacja różni się od czasu ostatniego został zaimportowany.

    -   Aktualizacja został zmodyfikowany i ma nowy skrót cyfrowego. Edytowanie aktualizacji zapobiega zastępowaniu oryginalnej, ponieważ spowoduje to zastąpienie zmiany, które zostały wdrożone nowe aktualizacje.

5.  Na **potwierdzenie** strony Przegląd wyników importu.

6.  Kliknij przycisk **Zamknij** aby zakończyć pracę kreatora. Aktualizacje dla tego wykazu można teraz wyświetlać w obszarze roboczym aktualizacje.

## <a name="next-steps"></a>Następne kroki
Po zaimportowaniu aktualizacji typowe akcje obejmują:
-   [Zarządzanie aktualizacjami](/sccm/sum/tools/manage-updates-with-updates-publisher) pakietów, należy przypisać i wdrożenia ich serwera aktualizacji.
-   [Tworzenie reguły stosowania](/sccm/sum/tools/updates-publisher-applicability-rules) w celu określenia, podczas wdrażania aktualizacji z serwerem aktualizacji.
