---
title: "Zarządzanie publikacji"
titleSuffix: Configuration Manager
description: "Zarządzanie grupami aktualizacji oprogramowania jako publikacji z programem System Center Updates Publisher"
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e6c1df1d-7728-4980-9199-bc32cde5439e
caps.latest.revision: "1"
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.openlocfilehash: 07e0acadae6cab050f7f0c0b0165e2baa5ff4d68
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="manage-publications-in-updates-publisher"></a>Zarządzanie publikacji w Updates Publisher

*Dotyczy: Program System Center Updates Publisher*

Publikacje służy do zarządzania grupami aktualizacji oraz pakiety jako pojedynczego obiektu. W tym publikowania aktualizacji na serwerze zarządzania i eksportowanie publikacji jako grupy do użycia z innej instalacji programu Updates Publisher.

## <a name="create-publications"></a>Tworzenie publikacji
Publikacje są tworzone dwa sposoby:

-   Jeśli zarządzasz aktualizacje i pakiety w **roboczym aktualizacje**, możesz [przypisać](/sccm/sum/tools/manage-updates-with-updates-publisher#assign-updates-and-bundles-to-a-publication) ich nowych publikacji, który jest tworzony w tym czasie.

-   W **roboczym publikacji** można użyć **Utwórz** znajdującego się na **publikacji** karty wstążki. Ta metoda umożliwia utworzenie publikacji do użytku w przyszłości. Później po przypisaniu aktualizacji, można użyć tej publikacji.

## <a name="rename-a-publication"></a>Zmienianie nazwy publikacji
Aby zmienić nazwę publikacji, wybierz publikacji z poziomu **publikacji obszaru roboczego**, a następnie na **publikacji** kartę na Wstążce wybierz **Edytuj**.

## <a name="change-the-publication-type-of-updates-in-a-publication"></a>Zmień typ publikacji aktualizacji w publikacji
Z **roboczym publikacji**, można zmodyfikować **typu publikacji** aktualizacji i pakiety, które są przypisane do publikacji.

1. Wybierz publikacji, która zawiera aktualizacje, który chcesz zmodyfikować, a następnie wybierz co najmniej jednej aktualizacji lub pakietów z **wszystkie &lt;nazwa publikacji > aktualizacji członków** listy.

2. Następnie na **Home** karcie, wybierz jedną z następujących opcji. Dostępne opcje zależą od typu publikacji wybranych aktualizacji.

  -   **Automatyczne**
  -   **Pełna zawartość**
  -   **Tylko metadane**

Po wprowadzeniu zmian, może być konieczne odświeżenie widoku publikacji, aby zobaczyć nowe wartości.

Uzyskać informacji o typach innej publikacji, zobacz [Przypisz do publikacji aktualizacji i pakiety](/sccm/sum/tools/manage-updates-with-updates-publisher#assign-updates-and-bundles-to-a-publication).

> [!TIP]    
> W przypadku ustawienia typu publikacji w pakiecie, wszystkie aktualizacje oprogramowania w tym pakiecie są publikowane z typem publikacji tego pakietu.

## <a name="remove-updates-from-a-publication"></a>Usuń aktualizacje z publikacji
Aby usunąć aktualizacji lub pakietów z publikacji, w **roboczym publikacji** wybierz publikacji, który chcesz zmodyfikować, a następnie wybierz aktualizacje i pakiety, które chcesz usunąć. Następnie na **Home** kartę na Wstążce wybierz **Usuń**.

Po aktualizacji są usuwane z publikacji, są one nadal dostępne w repozytorium Updates Publisher.

## <a name="publish-publications"></a>Publikowanie publikacji
Po opublikowaniu aktualizacji i pakiety, Updates Publisher dodaje informacji na temat tych aktualizacji i pakietów (metadanymi) i prawdopodobnie plików binarnych aktualizacji (pełna zawartość), do wdrożenia na urządzeniach z serwera aktualizacji.

Aby mieć możliwość publikowania, należy skonfigurować [serwera aktualizacji](/sccm/sum/tools/updates-publisher-options#update-server) opcję dla programu Updates Publisher. Aby otworzyć tej opcji konfiguracji, przejdź do **roboczym aktualizacje** &gt; **omówienie** i wybierz **skonfigurować serwer WSUS i certyfikat podpisywania.** Można także przejść do strony serwera aktualizacji w opcjach programu Updates Publisher.

> [!NOTE]   
> Updates Publisher można publikować tylko aktualizacje, które są 375 megabajtów (MB) lub mniejszy rozmiar w.

### <a name="to-publish-a-publication"></a>Aby opublikować publikacji

1.  Przejdź do **roboczym publikacji**, a następnie wybierz publikacji, która zawiera grupę aktualizacji i pakiety, które chcesz opublikować lub wyeksportować. Następnie wybierz pozycję **publikowania** z **Home** karty wstążki.

2.  Na **wybierz** strony **publikowania** kreatora można wybrać podpisać wszystkie aktualizacje przy użyciu nowego certyfikatu publikowania, ale nie można zmienić typu publikacji.

3.  Ukończ pracę kreatora.

  Jeżeli publikowanie nie powiedzie się, zostanie mu przedstawiona Link do pliku UpdatesPublisher.log, który może dostarczyć więcej informacji.

## <a name="export-a-publication"></a>Eksportowanie publikacji
Możesz wyeksportować publikacji z repozytorium Updates Publisher. Dzięki temu eksportuje aktualizacje i pakiety, które są przypisane do tej publikacji i tworzy katalog aktualizacji. Następnie możesz [dodać](/sccm/sum/tools/updates-publisher-catalogs#add-software-update-catalogs) , a następnie [zaimportować](/sccm/sum/tools/updates-publisher-catalogs#mport-updates) tego katalogu do innego wystąpienia programu Updates Publisher. Możesz również [wyeksportować aktualizacji](/sccm/sum/tools/manage-updates-with-updates-publisher#export-updates) nie są częścią publikacji.

Aby wyeksportować publikacji, przejdź do **roboczym publikacji** i wybierz publikacji, która zawiera aktualizacje, które ma zostać wykonane eksportowanie. Można wybrać tylko jedną publikację naraz.

Z publikacją wybrana, wybierz **wyeksportować** z **Home** karty wstążki, a następnie podaj ścieżkę i nazwę pliku eksportu katalogu.

Masz również opcji eksportu (Dołącz) aktualizacje oprogramowania zależnych w ramach eksportowania.

## <a name="rename-a-publication"></a>Zmienianie nazwy publikacji
Można zmienić nazwy publikacji, wybierz publikacji **publikacji obszaru roboczego**, a następnie wybierz pozycję **Edytuj** z **publikacji** karty wstążki.

## <a name="delete-a-publication"></a>Usuwanie publikacji
Można usunąć publikacji, wybierz publikacji **roboczym publikacji**, a następnie wybierz pozycję **usunąć** z **publikacji** karty wstążki.

Po usunięciu publikacji z Updates Publisher w repozytorium Updates Publisher pozostają dostępne aktualizacje, które znajdowały się w publikacji.

## <a name="expire-or-reactivate-updates-and-bundles"></a>Wygaśnie lub ponownym uaktywnieniem aktualizacji i pakietów
Można użyć **roboczym aktualizacje** wybierz i wygaśnie lub ponownie uaktywnić aktualizacji i pakietów. Można wygaśnie i ponownie uaktywnić aktualizacje i pakiety tyle razy, wybierz polecenie.

-   **Wygaśnięcie aktualizacji lub pakietów**, wybierz obszar roboczy aktualizacje co najmniej jeden aktualizacji lub które zawiera w są nie utracił ważności, a następnie wybierz **wygaśnięcia** z **Home** kartę. Do czasu opublikowania aktualizacji lub pakietu jako wygasłe do programu Configuration Manager, można uaktywnić go ponownie.

    Przed usunięciem (Usuń) niestandardowego aktualizacji lub pakietu z programu Configuration Manager, musi ona wygaśnie, a następnie opublikuj stan wygasłych do programu Configuration Manager. Po aktualizacji lub pakietów wygasły w programie Configuration Manager, możesz już wdrażanie lub ponownie uaktywnić aktualizacji lub pakietu.

-   **Aby ponownie uaktywnić aktualizacji lub pakietów**, w obszarze roboczym aktualizacje wybierz co najmniej jednej aktualizacji, które wygasły, a następnie wybierz pozycję **ponownie uaktywnić** z **Home** karty wstążki. Jeśli aktualizacja wygasła wcześniej został opublikowany jako wygasłe do programu Configuration Manager, nie można uaktywnić go ponownie.
