---
title: "Uaktualnij długoterminowej obsługi gałęzi do bieżącej gałęzi | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak przekonwertować oddziale długoterminowe obsługi do bieżącego oddziale."
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ec5b54cf-62b7-4ed1-9bb3-e8c63b9641c8
caps.latest.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 60631bc0346bd78d704e7129bb755af504c59b1b
ms.openlocfilehash: 6e7edc85630d22c5bbba1ff66bd1199903db76db
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---


# <a name="upgrade-the-long-term-servicing-branch-to-the-current-branch"></a>Uaktualnij długoterminowej obsługi gałęzi do bieżącej gałęzi

*Dotyczy: System Center Configuration Manager (długoterminowej obsługi oddziału)*

Umożliwia w tym temacie Informacje o sposobie uaktualniania (przekształcić) lokacji i hierarchii programu długoterminowe obsługi gałęzi (LTSB) programu Configuration Manager do bieżącej gałęzi.

Jeśli masz aktualną umowę Software Assurance (lub podobne licencja), które udziela użytkownikowi praw do korzystania z bieżącej gałęzi z LTSB bieżącej gałęzi można przekonwertować instalacji.  Jest to jednokierunkowe konwersji, ponieważ nie obsługuje konwersji do LTSB lokacji bieżącej gałęzi.

Jeśli masz wiele lokacji, wystarczy przekonwertować lokacja najwyższego poziomu w hierarchii. Po przekonwertowaniu lokacji najwyższego poziomu:
- Podrzędne Lokacje główne automatycznie przekonwertować.
-    Należy ręcznie zaktualizować dodatkowej lokacji z konsoli programu Configuration Manager.

## <a name="run-setup-to-convert-the-long-term-servicing-branch"></a>Uruchom Instalatora, aby przekonwertować gałęzi obsługi długoterminowe
W witrynie najwyższego poziomu w hierarchii, uruchom Instalatora programu Configuration Manager z kwalifikujących się nośnik linii bazowej i wybierz **lokacji konserwacji**.  Następnie gdy prezentowany stronie licencjonowania, wybierz opcję dla bieżącej gałęzi i Ukończ pracę kreatora.

Jeśli witryny został przekonwertowany na bieżącej gałęzi, wcześniej niedostępne funkcje i możliwości są dostępne do użycia.

> [!NOTE]  
> Kwalifikowanie nośnika linii bazowej jest nośnika, który ma wersji, która jest równa lub późniejsza niż LTSB instalacji.

Na przykład ponieważ LTSB wersji 1606 nośnika 1511 linii bazowej nie można użyć do konwersji na bieżącej gałęzi. Zamiast tego należy uruchomić Instalatora z tej samej wersji 1606 linii bazowej nośnik użytej do instalacji lokacji LTSB i wybierz opcję licencjonowania dla bieżącej gałęzi.  Alternatywnie został wydany później linii bazowej bieżącego gałęzi, można uruchomić Instalatora z tego nośnika linii bazowej.

Listę wersji linii bazowej, można znaleźć w temacie **linii bazowej i aktualizacji wersji** w [aktualizacji programu Configuration Manager](/sccm/core/servers/manage/updates).

## <a name="use-the-configuration-manager-console-to-convert-the-long-term-servicing-branch"></a>Konwertuj długoterminowej gałęzi obsługi za pomocą konsoli programu Configuration Manager
Jeśli witryna działa LTSB, służy Poniższa opcja w konsoli programu Configuration Manager do konwersji na bieżącej gałęzi:

 1. W konsoli, przejdź do **Administracja** > **konfiguracja lokacji** > **witryny**, a następnie otwórz **ustawienia hierarchii**.  

 2. Wybierz opcję, aby przekonwertować bieżącej gałęzi, a następnie wybierz **Zastosuj**.  

Jeśli witryny został przekonwertowany na bieżącej gałęzi, wcześniej niedostępne funkcje i możliwości są dostępne do użycia.

