---
title: "Użyj okna obsługi | Dokumentacja firmy Microsoft"
description: "Użyj kolekcje i okna obsługi skutecznie zarządzać klientami w programie System Center Configuration Manager."
ms.custom: na
ms.date: 02/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4564ebcb-41a8-4eb0-afdb-2e1f0795cfa2
caps.latest.revision: 6
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: fa67cf597c73bab47209c9b98539f97e174ae70b
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-use-maintenance-windows-in-system-center-configuration-manager"></a>Jak używać okna obsługi w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Okna obsługi umożliwiają definiowanie czas, kiedy można przeprowadzić operacje programu Configuration Manager w kolekcji urządzeń. Użytkownik używa okien obsługi, aby łatwiej dopilnować, by konfiguracji klienta zmian w okresach, które nie wpływają na wydajność.  

 Okna obsługi obsługi następujące operacje:  

-   Wdrożenia oprogramowania  

-   Wdrożenia aktualizacji oprogramowania  

-   Wdrożenie i ocena ustawień zgodności  

-   Wdrożenia systemu operacyjnego  

-   Wdrożenia sekwencji zadań  

 Skonfigurować okna obsługi się datę rozpoczęcia, rozpoczęcia i zakończenia czasu i wzorzec cyklu. Maksymalny czas trwania okna musi być krótszy niż 24 godziny. Domyślnie ponowne uruchomienia komputera spowodowane wdrożeniem są niedozwolone poza oknem konserwacji, ale można zastąpić domyślną. Okna obsługi obowiązują tylko podczas uruchamiania programu wdrożenia; aplikacje skonfigurowane do pobrania i lokalnego uruchomienia mogą pobierać zawartość poza oknem.  

 Gdy komputer kliencki jest członkiem kolekcji urządzeń oknem konserwacji, program wdrożenia działa tylko wtedy, gdy maksymalny dozwolony czas wykonywania nie przekracza czasu trwania skonfigurowanego dla okna. Jeśli uruchomienie programu nie powiedzie się, jest generowany alert, a wdrożenie jest uruchamiane ponownie w następnym zaplanowanym oknie obsługi, w którym jest dostępny czas.  

## <a name="using-multiple-maintenance-windows"></a>Używanie wielu okien obsługi  
 Komputer kliencki jest członkiem wielu kolekcji urządzeń, które okna obsługi, mają zastosowanie następujące zasady:  

-   Jeśli okna obsługi nie nakładają się na siebie, są traktowane jak dwa niezależne okna obsługi.  

-   Jeśli okna obsługi nakładają się na siebie, są traktowane jak jedno okno obsługi obejmujące przedział czasu zdefiniowany przez oba okna obsługi. Na przykład, jeśli dwa systemu windows, każde godzinę czas trwania nakładają się na siebie przez 30 minut, efektywny czas trwania okna obsługi wynosi 90 minut.  

 Użytkownik inicjuje instalację aplikacji z programu Software Center, aplikacja jest instalowana natychmiast niezależnie od wszelkich okien obsługi.  

 Jeśli ostateczny termin instalacji dla wdrożenia aplikacji z celem **Wymagane** przypada poza godzinami pracy skonfigurowanymi przez użytkownika w Centrum oprogramowania, aplikacja zostanie zainstalowana.  

### <a name="how-to-configure-maintenance-windows"></a>Konfigurowanie okien obsługi  

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność**>  **kolekcji urządzeń**.  

3.  W **kolekcji urządzeń** , wybierz kolekcję. Okien obsługi nie można tworzyć dla kolekcji **Wszystkie systemy** .  

4.  Na **Home** w karcie **właściwości** grupy, wybierz **właściwości**.  

5.  W **okna obsługi** na karcie  **&lt;Nazwa kolekcji\> właściwości** okno dialogowe Wybierz **New** ikona.  

6.  Ukończ  **&lt;nowy\> harmonogram** okna dialogowego.  

7.  Wybranie pozycji z **Zastosuj ten harmonogram do** listy rozwijanej.  

8.  Wybierz **OK** , a następnie Zamknij  **&lt;Nazwa kolekcji\> właściwości** okno dialogowe.  

