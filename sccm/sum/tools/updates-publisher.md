---
title: Aktualizuje wydawcy | Dokumentacja firmy Microsoft
description: "Umożliwia zarządzanie niestandardowe aktualizacje programu System Center Updates Publisher"
ms.custom: na
ms.date: 4/29/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2200b02b-e76b-4aa7-a77a-6dc5e70f1333
caps.latest.revision: 1
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: NOINDEX, NOFOLLOW
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31819a1df4e63e1114682490a9b3c3b4e5c99cfa
ms.openlocfilehash: f4951c204b32da58174b94a539b380c278fa9756
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="system-center-updates-publisher"></a>System Center Updates Publisher

*Dotyczy: System Center Updates Publisher*

System Center Updates Publisher (Updates Publisher) jest autonomicznym narzędziem, które umożliwia niezależnych dostawców oprogramowania lub deweloperzy aplikacji biznesowych — Zarządzanie aktualizacji niestandardowych. W tym aktualizacji, które mają zależności, takich jak sterowniki i pakiety aktualizacji.

Za pomocą Updates Publisher, można:

-   Importuj aktualizacje z katalogów zewnętrznych (katalogi aktualizacji innych niż firmy Microsoft).
-   Modyfikowanie definicji aktualizacji, w tym możliwość zastosowania i metadane wdrażania.
-   Eksportuj aktualizacje do katalogów zewnętrznych.
-   Publikowanie aktualizacji na serwerze aktualizacji.

Po opublikowaniu aktualizacji na serwerze aktualizacji, można następnie użyć programu System Center Configuration Manager do wykrywania i wdrażania tych aktualizacji na zarządzanych urządzeniach.

> [!TIP]  
> Poprzednia wersja, [System Center Updates Publisher 2011](http://go.microsoft.com/fwlink/?LinkId=848111), pozostaje w pomocy technicznej. Zaktualizowana wersja zachowuje tę samą funkcję, ale obsługuje innych systemów operacyjnych, nowe funkcje, aby uprościć niektóre zadania i ma zaktualizowanego interfejsu użytkownika.

## <a name="workspaces"></a>Obszary robocze
Po otwarciu Updates Publisher domyślnie węźle Przegląd *obszar roboczy aktualizacje.*

![Aktualizacje konsoli wydawcy](media/console1.png)   


Updates Publisher ma cztery obszarów roboczych, aby ułatwić organizowanie go.


**Obszar roboczy aktualizacje:** Użyj tego obszaru roboczego do [tworzenie](/sccm/sum/tools/create-updates-with-updates-publisher) i [zarządzanie](/sccm/sum/tools/manage-updates-with-updates-publisher) aktualizacji oprogramowania i pakietów aktualizacji. Obejmuje przypisanie aktualizacji i razem w publikacji, publikowanie i eksportowanie do innego repozytorium Updates Publisher.

**Publikacje obszaru roboczego:** Jest to, gdy użytkownik [Zarządzanie publikacje](/sccm/sum/tools/updates-publisher-publications). Publikacja jest grupa aktualizacji tworzenia uprościć eksportu i publikowania aktualizacji.

Zarządzanie publikacje obejmuje publikowania aktualizacji na serwerze, więc klientów można znaleźć i ich zainstalowanie, eksportowanie aktualizacje i pakiety do użytku przez inne instalacje Updates Publisher lub modyfikowanie zawartość lub szczegóły publikacji.



**Obszar roboczy reguły:** Oto, gdzie możesz [Zarządzanie zasady stosowania](/sccm/sum/tools/updates-publisher-applicability-rules) który zapisane i następnie używać z wdrożeniem aktualizacji. Istnieją dwa typy zasad:

-   Reguły instalowalnych — te reguły ustalić, jeśli klient należy zainstalować aktualizację.
-   Zainstalowane reguły — te zasady, sprawdź, czy aktualizacja jest już zainstalowana.

**Katalogi obszaru roboczego:** Użyj tego obszaru roboczego, aby dodać i [Zarządzanie katalogami aktualizacji oprogramowania](/sccm/sum/tools/updates-publisher-catalogs). W tym importu aktualizacji oprogramowania z tych katalogów do repozytorium Updates Publisher.
## <a name="first-steps"></a>Pierwsze kroki
Aby rozpocząć, najpierw [zainstalować](/sccm/sum/tools/install-updates-publisher), a następnie [skonfigurować opcje](/sccm/sum/tools/updates-publisher-options) przez program Updates Publisher.

