---
title: Updates Publisher
titleSuffix: Configuration Manager
description: Umożliwia zarządzanie niestandardowe aktualizacje programu System Center Updates Publisher
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.topic: conceptual
ms.assetid: 2200b02b-e76b-4aa7-a77a-6dc5e70f1333
author: aczechowski
ms.author: aaroncz
manager: dougeby
robots: NOINDEX, NOFOLLOW
ms.openlocfilehash: 3a9c7758e394118041700192a393aff98f0d9087
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="system-center-updates-publisher"></a>Program System Center Updates Publisher

*Dotyczy: System Center Updates Publisher*

System Center Updates Publisher (Updates Publisher) jest autonomicznym narzędziem pozwala niezależnym dostawcom oprogramowania lub deweloperzy aplikacji biznesowych — Zarządzanie aktualizacji niestandardowych. Dotyczy to również aktualizacji, które są zależne, takie jak sterowniki i pakiety aktualizacji.

Przy użyciu Updates Publisher, można:

-   Importowanie aktualizacji z katalogów zewnętrznych (katalogi aktualizacji firmy Microsoft).
-   Modyfikowanie definicji aktualizacji w tym możliwość zastosowania i metadane wdrażania.
-   Wyeksportuj aktualizacji do katalogów zewnętrznych.
-   Publikowanie aktualizacji na serwerze aktualizacji.

Po opublikowaniu aktualizacji serwera aktualizacji, można następnie użyć programu System Center Configuration Manager do wykrywania i wdrażanie tych aktualizacji na zarządzanych urządzeniach.

> [!TIP]  
> Poprzednia wersja [System Center Updates Publisher 2011](http://go.microsoft.com/fwlink/?LinkId=848111), pozostaje w pomocy technicznej. Zaktualizowana wersja zachowuje tę samą funkcję, ale obsługuje dodatkowych systemów operacyjnych, nowe funkcje, aby uprościć niektóre zadania i ma zaktualizowany interfejs użytkownika.

## <a name="workspaces"></a>Obszary robocze
Po otwarciu Updates Publisher, domyślnie przyjmowana do węzła omówienie *roboczym aktualizacje.*

![Aktualizacje konsoli wydawcy](media/console1.png)   


Updates Publisher ma cztery obszarów roboczych, aby ułatwić organizowanie go.


**Obszar roboczy aktualizacje:** Użyj tego obszaru roboczego do [utworzyć](/sccm/sum/tools/create-updates-with-updates-publisher) i [zarządzanie](/sccm/sum/tools/manage-updates-with-updates-publisher) aktualizacji oprogramowania i pakietów aktualizacji. Obejmuje Przypisywanie aktualizacji i zawiera również w publikacji, publikowanie i eksportowanie do innego repozytorium Updates Publisher.

**Publikacje obszaru roboczego:** Jest to, gdy użytkownik [Zarządzanie publikacji](/sccm/sum/tools/updates-publisher-publications). Publikacja jest grupa aktualizacji tworzenia uprościć eksportu i publikowania aktualizacji.

Zarządzanie publikacji obejmuje publikowania aktualizacji na serwerze, umożliwiając klientom wyszukiwanie i ich zainstalowanie, eksportowanie aktualizacje i pakiety do użytku przez inne instalacje Updates Publisher lub modyfikowania zawartości lub szczegóły publikacji.



**Obszar roboczy zasady:** Oto, gdzie można [zarządzać decydują zasady stosowania](/sccm/sum/tools/updates-publisher-applicability-rules) czy zapisać i następnie używana wdrażanych aktualizacji. Istnieją dwa typy zasad:

-   Reguły instalowalnych — te reguły ustalić Jeśli klient należy zainstalować aktualizację.
-   Zainstalowane reguły — te reguły, sprawdź, czy aktualizacja jest już zainstalowany.

**Katalogi obszaru roboczego:** Użyj tego obszaru roboczego, aby dodać i [Zarządzanie katalogami aktualizacji oprogramowania](/sccm/sum/tools/updates-publisher-catalogs). Dotyczy to również importowania aktualizacje oprogramowania z tych katalogów do repozytorium Updates Publisher.
## <a name="first-steps"></a>Pierwsze kroki
Aby rozpocząć, najpierw [zainstalować](/sccm/sum/tools/install-updates-publisher), a następnie [skonfigurować opcje](/sccm/sum/tools/updates-publisher-options) dla programu Updates Publisher.
