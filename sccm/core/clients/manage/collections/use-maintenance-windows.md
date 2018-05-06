---
title: Używanie okien obsługi
titleSuffix: Configuration Manager
description: Efektywnie zarządzać klientami w programie System Center Configuration Manager, należy użyć kolekcji i okna obsługi.
ms.date: 02/22/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 4564ebcb-41a8-4eb0-afdb-2e1f0795cfa2
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 18a870b111b141cb9b95664a2f66403ea37cb99e
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-use-maintenance-windows-in-system-center-configuration-manager"></a>Używanie okien obsługi w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Okna obsługi umożliwiają definiowanie czasu, podczas operacji programu Configuration Manager może zostać przeprowadzona w kolekcji urządzeń. Okna obsługi można użyć do zapewnienia tego klienta zmiany konfiguracji będą wykonywane w okresach, które nie mają wpływu na wydajność.  

 Następujące operacje obsługują okna obsługi:  

-   Wdrożenia oprogramowania  

-   Wdrożenia aktualizacji oprogramowania  

-   Wdrożenie i ocena ustawień zgodności  

-   Wdrożenia systemu operacyjnego  

-   Wdrożenia sekwencji zadań  

 Konfigurowanie okien obsługi z datą rozpoczęcia i rozpoczęcia i zakończenia czasu i wzorzec cyklu. Maksymalny czas trwania okna musi być krótszy niż 24 godziny. Domyślnie ponowne uruchomienie komputera spowodowane wdrożeniem jest niedozwolone poza oknem konserwacji, ale można zastąpić domyślną. Okna obsługi dotyczą tylko czasu podczas wykonywania programu wdrożenia; aplikacje skonfigurowane do pobierania i uruchom lokalnie mogą pobierać zawartość poza oknem.  

 Gdy komputer kliencki jest członkiem kolekcji urządzeń oknem obsługi, program wdrożenia jest uruchamiana tylko wtedy, gdy maksymalny dozwolony czas wykonywania nie przekracza czasu trwania skonfigurowanego dla okna. Jeśli uruchomienie programu nie powiedzie się, jest generowany alert, a wdrożenie jest uruchamiane ponownie w następnym zaplanowanym oknie obsługi, w którym jest dostępny czas.  

## <a name="using-multiple-maintenance-windows"></a>Używanie wielu okien obsługi  
 Gdy komputer kliencki jest członkiem wielu kolekcji urządzeń, które mają okna obsługi, zastosuj następujące reguły:  

-   Jeśli okna obsługi nie nakładają się na siebie, są traktowane jak dwa niezależne okna obsługi.  

-   Jeśli okna obsługi nakładają się na siebie, są traktowane jak jedno okno obsługi obejmujące przedział czasu zdefiniowany przez oba okna obsługi. Na przykład, jeśli dwa systemu windows, każdej godziny, nakładają na czas trwania przez 30 minut, efektywny czas trwania okna obsługi wynosi 90 minut.  

 Gdy użytkownik inicjuje instalację aplikacji z Centrum oprogramowania, aplikacja jest zainstalowana, niezależnie od oknami obsługi.  

 Jeśli ostateczny termin instalacji dla wdrożenia aplikacji z celem **Wymagane** przypada poza godzinami pracy skonfigurowanymi przez użytkownika w Centrum oprogramowania, aplikacja zostanie zainstalowana.  

### <a name="how-to-configure-maintenance-windows"></a>Konfigurowanie okien obsługi  

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność**>  **kolekcje urządzeń**.  

3.  W **kolekcje urządzeń** listy, wybierz kolekcję. Okien obsługi nie można tworzyć dla kolekcji **Wszystkie systemy** .  

4.  Na **Home** karcie **właściwości** grupy, wybierz **właściwości**.  

5.  W **okna obsługi** karcie  **&lt;Nazwa kolekcji\> właściwości** okna dialogowego wybierz **nowy** ikony.  

6.  Zakończenie  **&lt;nowe\> harmonogram** okna dialogowego.  

7.  Wybierz odpowiednią pozycję z **Zastosuj ten harmonogram do** listy rozwijanej.  

8.  Wybierz **OK** , a następnie Zamknij  **&lt;Nazwa kolekcji\> właściwości** okno dialogowe.  
