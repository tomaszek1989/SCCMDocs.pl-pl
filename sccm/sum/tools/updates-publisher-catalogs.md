---
title: "Zarządzanie katalogami aktualizacji | Dokumentacja firmy Microsoft"
description: "Zarządzanie katalogami aktualizacji oprogramowania dla programu System Center aktualizuje wydawcy"
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 887f8029-1a3a-423c-a9c1-31dc0d693386
caps.latest.revision: 1
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31819a1df4e63e1114682490a9b3c3b4e5c99cfa
ms.openlocfilehash: 7451d699e0e5e146b0538a57deca595188d113bf
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="manage-software-update-catalogs-in-updates-publisher"></a>Zarządzanie katalogami aktualizacji oprogramowania w programie Publisher aktualizacji

*Dotyczy: System Center Updates Publisher*

Użyj **katalogi** **obszaru roboczego** Zarządzanie katalogi aktualizacji oprogramowania. W tym dodawanie nowych katalogów, Zarządzanie subskrypcjami istniejący katalog i importowania informacji o aktualizacjach z katalogu do repozytorium Updates Publisher.

Katalogi aktualizacji oprogramowania zawierają informacje o powiązanych aktualizacji, które są tworzone przez organizacje innych niż Microsoft. Innymi organizacjami obejmują własnych organizacji i dostawcami oprogramowania innych firm, zarejestrowanych swoje katalogi z firmą Microsoft. Katalogi zarejestrowanych dostawców oprogramowania są nazywane *współpracy wykazy*. Katalogi, które tworzysz i nie są zarejestrowane z firmą Microsoft, są nazywane *użytkownika* wykazów.

## <a name="add-software-update-catalogs"></a>Dodaj katalogi aktualizacji oprogramowania
Katalog aktualizacji należy dodać do Updates Publisher, aby można było zarządzać aktualizacje, które zawiera. Po dodaniu katalogu Updates Publisher:
-   Tworzy subskrypcję do tego katalogu, więc można sprawdzić dostępność aktualizacji do tego katalogu.
-   Dodaje do listy w katalogu **Moje katalogi aktualizacji oprogramowania** okna **roboczym katalogi**.  

Informacje o każdym subskrybowanego katalogu jest dostępna w konsoli. Informacje obejmują: adres URL pobierania lub lokalizacji, nazwę firmy lub organizacji, która utworzyła katalogu, a po jego ostatniego zaimportowane lub zmodyfikowany.

Updates Publisher automatycznie sprawdzić subskrypcji w programie zmiany każdym uruchomieniu. To jest skonfigurowany jako [zaawansowanych opcji](/sccm/sum/tools/updates-publisher-options#advanced). Po skonfigurowaniu Updates Publisher odwołuje się do informacji adres URL lub lokalizację pobierania dla subskrypcji i alertów, gdy istnieją zmiany do katalogu, które zostały wprowadzone od czasu ostatniego zaimportowane do repozytorium.

Ręczne sprawdzanie aktualizacji katalogu, wybierz katalogu z **Moje katalogi aktualizacji oprogramowania** listy, a następnie wybierz **Odśwież** na Wstążce.

Oprócz dodania wykazów i wyświetlanie informacji o subskrybowanego katalogów, można:
-  **Edytuj** informacje o *użytkownika* wykazów.
-  **Usuń** (Usuń) katalogu z Updates Publisher.
-  **Importuj** aktualizacje z wykazu do repozytorium Updates Publisher. Po zaimportowaniu aktualizacji, należy zaimportować wszystkie aktualizacje zawarte w tym katalogu. Aktualizacje można wyświetlić w obszarze roboczym aktualizacje, w którym można wybrać i publikowanie aktualizacji na serwerze aktualizacji.

> [!NOTE]   
> Usuwanie katalogu z Updates Publisher powoduje aktualizacje w tym katalogu zostaną usunięte z repozytorium. Nie ma to wpływu na aktualizacje, które zostały opublikowane na serwerze aktualizacji. Aby usunąć aktualizacji z serwera aktualizacji, które nie są już w repozytorium, zobacz [wygaśnie aktualizacje oprogramowania nieużywanej](/sccm/sum/tools/updates-publisher-options#expire-unreferenced-software-updates).

## <a name="manage-update-catalogs"></a>Zarządzanie katalogami aktualizacji
Można wyświetlić katalogi listy zaimportowano w **Moje katalogi aktualizacji oprogramowania** okna **roboczym katalogi**. W tym obszarze roboczym możesz:

-   **Dodaj katalog partnera:** Użyj jedną z następujących czynności, aby znaleźć nowych katalogów partnera:

    -   W konsoli, przejdź do **obszar roboczy aktualizacje** > **Przegląd**. W **wprowadzenie** okna, wybierz **dodać katalogi aktualizacje oprogramowania partnera**.

    -   W konsoli, przejdź do **roboczym katalogi** > **Moje katalogi**. Następnie na Wstążce wybierz **dodać katalogi**.

-   **Dodaj katalog użytkownika:** W konsoli, przejdź do **roboczym katalogi** > **Moje katalogi**. Następnie na Wstążce wybierz **dodać katalogi**. Oprócz lokalizacji pliku cab należy określić wydawcę, nazwę i opis do identyfikacji katalogu.


-   **Sprawdź dostępność aktualizacji wykazów:** Wybierz jeden lub więcej katalogów, a następnie wybierz **Odśwież** na Wstążce.

-   **Przeprowadź edycję katalogu użytkownika:** Wybierz *użytkownika* katalogu, a następnie wybierz **edytować** na Wstążce. Następnie można zmodyfikować właściwości zdefiniowane przez użytkownika.

-   **Usuwanie katalogów:** Wybierz jeden lub więcej katalogów, a następnie wybierz **Usuń** na Wstążce. Spowoduje to usunięcie katalogu, subskrypcji i aktualizacje z tych katalogów z repozytorium Updates Publisher.

-   **Dodaj aktualizacje z wykazu do repozytorium**: Wybierz **importowania** na Wstążce, aby uruchomić **importu katalogu** kreatora. Więcej infomration można znaleźć w temacie [aktualizacje importowania](#import-updates)

## <a name="import-updates"></a>Importuj aktualizacje
Podczas importowania katalogu Menedżera aktualizacji dodaje do repozytorium Updates Publisher aktualizacje z tego katalogu. Po zaimportowaniu aktualizacji, można publikować je z serwerem aktualizacji, aby udostępnić je do zarządzanych urządzeń.

### <a name="to-import-updates"></a>Aby zaimportować aktualizacje
1.  Aby uruchomić **importu katalogu** kreatora wybierz **importowania** na Wstążce w jednym z następujących obszarów roboczych:

    -   Katalogi obszaru roboczego

    -   Obszar roboczy aktualizacje

2.  Na **typu importu** wybierz jeden lub więcej katalogów do wydawcy aktualizacje zostały dodane lub określ ścieżkę do katalogu nie zostały jeszcze dodane subskrypcji. Wybrana opcja **dalej** Aby wyświetlić ekran podsumowania, a gdy będzie gotowe, wybierz **dalej** uruchomić importu.

3.  Na **ostrzeżenie o zabezpieczeniach — Weryfikacja katalogu** , przejrzyj certyfikatu katalogu, a gdy będzie gotowe, wybrać **Akceptuj** Aby zaimportować aktualizacje.

    > [!CAUTION]    
    > Akceptować aktualizacje tylko z zaufanych wydawców. Aktualizacje oprogramowania z niezaufanych wydawców może być szkodliwy dla komputerów klienckich podczas skanowania w poszukiwaniu aktualizacji.

    >  Jeśli wydawca nie jest już zaufany, należy usunąć tego wydawcy z listy zaufanych wydawców. Aby znaleźć więcej informacji na temat przyjmuje katalogi, kliknij przycisk **Powiedz mi więcej** w **ostrzeżenie o zabezpieczeniach — Weryfikacja katalogu** okno dialogowe.

    Jeśli wybierzesz zawsze Akceptuj katalogi od wydawcy, że wydawca jest dodawany do [listy zaufanych wydawców](/sccm/sum/tools/updates-publisher-options#trusted-publishers). Można sprawdzić i edytować tej listy jako opcja Updates Publisher.

4.  Import pomija importu aktualizacji, gdy aktualizacja jest już w repozytorium i jest spełniony jeden z następujących czynności:

    -   Aktualizacja jest bez zmian od czasu ostatniego została zaimportowana.

    -   Aktualizacja została zmodyfikowana i ma nowego skrótu cyfrowego. Edytowanie aktualizacji zapobiega zastępowaniu oryginalnego, jak może więc zastąpić zmian, który został wdrożony nowych aktualizacji.

5.  Na **potwierdzenia** strony w wynikach importu.

6.  Kliknij przycisk **Zamknij** aby zakończyć pracę kreatora. Aktualizacje dla tego katalogu można wyświetlać w obszarze roboczym aktualizacje.

## <a name="next-steps"></a>Następne kroki
Po zaimportowaniu aktualizacji wspólnego działania obejmują:
-   [Zarządzanie aktualizacjami](/sccm/sum/tools/manage-updates-with-updates-publisher) pakietu, przypisywania i wdrażanie ich serwera aktualizacji.
-   [Utwórz zasady stosowania](/sccm/sum/tools/updates-publisher-applicability-rules) w celu określenia, podczas wdrażania aktualizacji na serwerze aktualizacji.

