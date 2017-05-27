---
title: "Zarządzanie publikacje | Dokumentacja firmy Microsoft"
description: "Zarządzanie grupami aktualizacji oprogramowania w postaci publikacji z programem System Center Updates Publisher"
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e6c1df1d-7728-4980-9199-bc32cde5439e
caps.latest.revision: 1
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31819a1df4e63e1114682490a9b3c3b4e5c99cfa
ms.openlocfilehash: ddea7af935d5be880b96e383401061f8aa11e6da
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="manage-publications-in-updates-publisher"></a>Zarządzanie publikacji w Updates Publisher

*Dotyczy: System Center Updates Publisher*

Publikacje umożliwia zarządzanie grupami aktualizacji i pakiety jako jeden obiekt. Obejmuje to publikowanie aktualizacji na serwerze zarządzania i eksportowanie publikacji jako grupy do użycia z innej instalacji programu Updates Publisher.

## <a name="create-publications"></a>Tworzenie publikacji
Publikacje tworzone są dwa sposoby:

-   Podczas zarządzania aktualizacje i pakiety w **obszar roboczy aktualizacje**, możesz [przypisać](/sccm/sum/tools/manage-updates-with-updates-publisher#assign-updates-and-bundles-to-a-publication) ich do nowej publikacji, która jest tworzona w tym czasie.

-   W **roboczym publikacje** można użyć **Utwórz** znajdującego się na **publikacji** karty wstążki. Ta metoda umożliwia tworzenie publikacji do użytku w przyszłości. Później po przypisaniu aktualizacji, można użyć tej publikacji.

## <a name="rename-a-publication"></a>Zmienianie nazwy publikacji
Aby zmienić nazwę publikacji, wybierz opcję publikacji z poziomu **roboczym publikacje**, a następnie na **publikacji** karta na Wstążce wybierz **edycji**.

## <a name="change-the-publication-type-of-updates-in-a-publication"></a>Zmień typ publikacji aktualizacji w publikacji
Z **obszaru roboczego publikacji**, można zmodyfikować **typ publikacji** aktualizacje i pakiety, które są przypisane do publikacji.

1. Wybierz publikacji, która zawiera aktualizacje, które chcesz zmodyfikować, a następnie wybierz co najmniej jedną aktualizację lub pakiety z **wszystkie &lt;nazwa publikacji > aktualizacji członków** listy.

2. Następnie na **Home** , wybierz jedną z następujących opcji. Dostępne opcje zależą od typu publikacji z wybranych aktualizacji.

  -   **Automatyczne**
  -   **Pełnej zawartości**
  -   **Tylko metadane**

Po wprowadzeniu zmiany, może być konieczne odświeżenie widoku publikacji, aby zobaczyć nowe wartości.

Informacje o typach innej publikacji, zobacz [przypisać aktualizacje i pakiety do publikacji](/sccm/sum/tools/manage-updates-with-updates-publisher#assign-updates-and-bundles-to-a-publication).

> [!TIP]    
> Po ustawieniu typu publikacji w pakiecie aktualizacji oprogramowania w tym pakiecie są publikowane z typem publikacji tego zbioru.

## <a name="remove-updates-from-a-publication"></a>Usuń aktualizacje z publikacji
Aby usunąć aktualizacji lub pakiety z publikacji, w **publikacje obszaru roboczego** wybierz publikacji, które chcesz zmodyfikować, a następnie wybierz aktualizacje i pakiety, które chcesz usunąć. Następnie na **Home** karta na Wstążce wybierz **usunąć**.

Po aktualizacji są usuwane z publikacji, nadal dostępne w repozytorium Updates Publisher.

## <a name="publish-publications"></a>Publikowanie publikacji
Po opublikowaniu aktualizacji i pakiety, Updates Publisher dodaje informacje o tych aktualizacjach i pakiety (metadane) i prawdopodobnie plików binarnych aktualizacji (pełna zawartość), na serwerze aktualizacji do wdrożenia na urządzeniach.

Zanim opcji publikowania, należy skonfigurować [serwera aktualizacji](/sccm/sum/tools/updates-publisher-options#update-server) opcję Updates Publisher. Aby otworzyć ta opcja konfiguracji, przejdź do **obszar roboczy aktualizacje** &gt; **Przegląd** i wybierz **konfigurowania programu WSUS i certyfikat podpisywania.** Możesz również do strony serwera aktualizacji w opcjach programu Updates Publisher.

> [!NOTE]   
> Updates Publisher można publikować tylko aktualizacje, które są 375 megabajtów (MB) lub mniej w rozmiarze.

### <a name="to-publish-a-publication"></a>Aby opublikować publikacji

1.  Przejdź do **roboczym publikacje**, a następnie wybierz publikacji, która zawiera grupę aktualizacji i pakiety, które chcesz opublikować lub wyeksportować. Następnie wybierz **publikowania** z **Home** karty wstążki.

2.  Na **wybierz** strony **publikowania** kreatora można wybrać do podpisania wszystkich aktualizacji przy użyciu nowego certyfikatu publikowania, ale nie można zmienić typu publikacji.

3.  Ukończ pracę kreatora.

  Jeśli publikowanie zakończy się niepowodzeniem, zostanie wyświetlona łącze do pliku UpdatesPublisher.log, który może zawierać dodatkowe informacje.

## <a name="export-a-publication"></a>Eksportowanie publikacji
Możesz wyeksportować publikacji z repozytorium Updates Publisher. Umożliwia to wyeksportowanie, aktualizacje i pakiety, które są przypisane do tej publikacji i tworzy katalog aktualizacji. Następnie możesz [dodać](/sccm/sum/tools/updates-publisher-catalogs#add-software-update-catalogs) i następnie [importowania](/sccm/sum/tools/updates-publisher-catalogs#mport-updates) tego katalogu do innego wystąpienia programu Updates Publisher. Możesz również [wyeksportować aktualizacji](/sccm/sum/tools/manage-updates-with-updates-publisher#export-updates) nie są częścią publikacji.

Aby wyeksportować publikacji, przejdź do **roboczym publikacje** i wybierz publikacji, która zawiera aktualizacje, które chcesz wyeksportować. Można wybrać tylko jedną publikację naraz.

Publikacja wybrana, wybierz polecenie **wyeksportować** z **Home** karty wstążki, a następnie podaj ścieżkę i nazwę pliku eksportu katalogu.

Istnieje również możliwość eksportowania (Dołącz) aktualizacje oprogramowania zależnych w ramach eksportu.

## <a name="rename-a-publication"></a>Zmienianie nazwy publikacji
Aby zmienić nazwę publikacji, wybierz opcję publikacji **roboczym publikacje**, a następnie wybierz **edytować** z **publikacji** karty wstążki.

## <a name="delete-a-publication"></a>Usuwanie publikacji
Aby usunąć publikację, wybierz publikacji **roboczym publikacje**, a następnie wybierz **usunąć** z **publikacji** karty wstążki.

Po usunięciu publikacji z Updates Publisher w repozytorium Updates Publisher pozostają dostępne aktualizacje, które znajdowały się w publikacji.

## <a name="expire-or-reactivate-updates-and-bundles"></a>Wygaśnięcia lub ponownie uaktywnić pakiety i aktualizacje
Można użyć **obszar roboczy aktualizacje** wybierz i wygaśnie lub ponownie uaktywnić pakiety i aktualizacje. Można wygaśnie i Uaktywnij ponownie aktualizacje i pakiety tyle razy, wybierz polecenie.

-   **Wygaśnięcie aktualizacji lub pakiety**, w polu Wybierz obszar roboczy aktualizacje jeden lub więcej aktualizacji lub razem, które nie są wygasł, a następnie wybierz **Wygaś** z **Home** kartę. Do czasu opublikowania pakietu jako wygasłe programu Configuration Manager lub aktualizacji, można ponownie uaktywnić.

    Przed usunięciem lub aktualizacji (Usuń) niestandardowy pakiet programu Configuration Manager, należy wygasić go, a następnie opublikuj wygasłe stanie programu Configuration Manager. Po aktualizacji lub pakiety wygasłe w programie Configuration Manager, nie jest już wdrożeniem lub ponownie uaktywnić pakietu lub aktualizacji.

-   **Aby ponownie uaktywnić aktualizacji lub pakiety**, w obszarze roboczym aktualizacje wybierz co najmniej jednej aktualizacji, które wygasły, a następnie wybierz **ponownie uaktywnić** z **Home** karty wstążki. Jeśli aktualizacja wygasła wcześniej została opublikowana jako wygasłe programu Configuration Manager, nie można uaktywnić go ponownie.

