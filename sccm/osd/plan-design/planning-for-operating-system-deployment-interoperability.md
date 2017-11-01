---
title: "Planowanie współdziałania wdrożenia systemu operacyjnego"
titleSuffix: Configuration Manager
description: "Zrozumieć zagadnienia dotyczące współdziałania, kiedy różnych lokacji programu System Center Configuration Manager w jednej hierarchii korzystają z różnych wersji."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: e327ce38-6c07-4a27-b6eb-7e5bf74ed04b
caps.latest.revision: "10"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: b096ea4d6dfb4df13691c662d196f638d30d5da4
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="planning-for-operating-system-deployment-interoperability-in-system-center-configuration-manager"></a>Planowanie współdziałania w ramach wdrożenia systemu operacyjnego w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Jeśli w różnych witrynach programu System Center Configuration Manager w jednej hierarchii korzystają z różnych wersji, niektóre funkcje programu Configuration Manager nie jest dostępny. Zwykle funkcje nowszej wersji programu Configuration Manager nie jest dostępny w lokacjach lub dla klientów korzystających z starszej wersji. Aby uzyskać więcej informacji, zobacz [Współdziałanie różnych wersji programu System Center Configuration Manager](../../core/plan-design/hierarchy/interoperability-between-different-versions.md).  

 Po uaktualnieniu lokacji najwyższego poziomu w hierarchii oraz innych lokacji w hierarchii, uruchom Menedżera konfiguracji w starszej wersji, należy wziąć pod uwagę następujące:  

-   Pakiet instalacyjny klienta  

    -   Źródło domyślnego pakietu instalacyjnego klienta zostaje automatycznie uaktualnione, a wszystkie punkty dystrybucji w hierarchii są aktualizowane przy nowego pakietu instalacyjnego klienta, nawet w przypadku punktów dystrybucji w lokacjach w hierarchii, które są w starszej wersji.  

    -   Klienci, którzy z nową wersją nie można przypisać do lokacji, które nie zostały uaktualnione do nowej wersji. Przypisanie jest blokowane przez punkt zarządzania.  

-   Obrazy rozruchowe  

    -   Po uaktualnieniu lokacji najwyższego poziomu do najnowszej wersji programu Configuration Manager domyślne obrazy rozruchowe (x86 i x64) są automatycznie aktualizowane do obrazów rozruchowych opartych na programie Windows ADK dla systemu Windows 10, które używają systemu Windows PE 10. Pliki, które są skojarzone z domyślne obrazy rozruchowe zostały zaktualizowane do najnowszej wersji programu Configuration Manager plików. Niestandardowe obrazy rozruchowe nie są automatycznie aktualizowane. Należy zaktualizować ręcznie, niestandardowe obrazy rozruchowe w tym starsze wersje środowiska Windows PE.  

    -   Kiedy hierarchia lokacji zawiera różne wersje programu Configuration Manager, należy unikać użycia nośników dynamicznych. Należy używać nośników opartych na lokacji do kontaktowania się z określonym punktem zarządzania, do momentu uaktualnienia wszystkich lokacji do tej samej wersji programu Configuration Manager.  

    -   Sprawdź, czy najnowsze obrazy rozruchowe programu Configuration Manager zawierają żądane dostosowania, a następnie zaktualizować wszystkie punkty dystrybucji w lokacjach z najnowszą wersją programu Configuration Manager przy użyciu nowych obrazów rozruchowych.  

-   Narzędzia do migracji stanu użytkowników (USMT)  

    -   Po uaktualnieniu lokacji najwyższego poziomu do najnowszej wersji programu Configuration Manager domyślny pakiet narzędzia USMT jest automatycznie zaktualizowane do najnowszej wersji. Niestandardowe pakiety narzędzia USMT nie są automatycznie aktualizowane. Pakiety tego typu należy aktualizować ręcznie.  

-   Nowe kroki sekwencji zadań  

    -   Okresowo wprowadzane są nowe kroki sekwencji zadań do nowych wersji programu Configuration Manager. Wdrażanie sekwencji zadań z nowym krokiem na starszych klientach zakończy się niepowodzeniem sekwencji zadań. Przed wdrożeniem sekwencji zadań w nowym kroku upewnij się, że klienci w kolekcji docelowej zostaną zaktualizowani do nowych wersji.  

-   Nośniki wdrażania systemu operacyjnego  

    -   Wszystkie nośniki (rozruchowe, przechwycone, wstępnie przygotowane i autonomiczne) muszą zostać zaktualizowane nowego pakietu klienta programu Configuration Manager po zaktualizowaniu lokacji do nowej wersji.  

-   Rozszerzenia innych firm dotyczące wdrażania systemu operacyjnego  

    -   Jeśli masz rozszerzenia innych firm dotyczące wdrażania systemu operacyjnego i mają różne wersje lokacji programu Configuration Manager lub klientów programu Configuration Manager, czyli hierarchię mieszaną, mogą wystąpić problemy z rozszerzeniami.  

 Podczas aktywnego uaktualniania lokacji w hierarchii skorzystaj z poniższych sekcji, które zapewniają pomoc podczas wdrożeń systemu operacyjnego.  

## <a name="latest-version-of-configuration-manager-sites-in-a-mixed-hierarchy"></a>Najnowszą wersję lokacji programu Configuration Manager w hierarchii mieszanej  
 Podczas uaktualniania lokacji do najnowszej wersji programu Configuration Manager, sekwencje zadań, które odwołanie do domyślnego pakietu instalacyjnego klienta zostaną automatycznie uruchomione w celu wdrożenia najnowszej wersji klienta programu Configuration Manager. Sekwencje zadań, które odwołują się do niestandardowego pakietu instalacyjnego klienta będzie nadal wdrażać wersję klienta, który jest zawarty w tym pakiecie niestandardowym (najprawdopodobniej poprzedniej wersji programu Configuration Manager klienta) i muszą zostać zaktualizowane w celu uniknięcia niepowodzeń wdrażania sekwencji zadań. Jeśli masz sekwencji zadań, która jest skonfigurowana do używania niestandardowego pakietu instalacyjnego klienta, należy zaktualizować sekwencję zadań, aby używać najnowszej wersji programu Configuration Manager z pakietu instalacyjnego klienta lub zaktualizować pakiet niestandardowy w celu użycia najnowsze źródła instalacji klienta programu Configuration Manager.  

> [!IMPORTANT]  
>  Nie należy wdrażać sekwencji zadań, która odwołuje się do najnowszego pakietu instalacyjnego klienta programu Configuration Manager do klientów w starszych lokacji programu Configuration Manager. Gdy klienci przypisani do starszych lokacji programu Configuration Manager uaktualnienia do najnowszej wersji klienta programu Configuration Manager, Configuration Manager blokuje przypisanie do lokacji programu Configuration Manager starszej. Dlatego klient jest już przypisany do żadnej lokacji i pozostanie niezarządzany do momentu ręcznie przypisać klienta do najnowszej lokacji programu Configuration Manager lub ponownie zainstalować starszą wersję programu Configuration Manager klienta na komputerze.  

## <a name="older-versions-of-configuration-manager-in-a-mixed-hierarchy"></a>Starsze wersje programu Configuration Manager w hierarchii mieszanej  
 Po uaktualnieniu centralnej lokacji administracyjnej do najnowszej wersji programu Configuration Manager, należy wykonać następujący krok, aby upewnić się, że sekwencje zadań wdrożenia systemu operacyjnego, które są wdrażane na klientach przypisanych do starszych lokacji programu Configuration Manager (jeszcze nie uaktualnione do najnowszej wersji programu Configuration Manager) nie spowodują pozostawienia tych klientów w stanie niezarządzanym.  

-   Utwórz sekwencję zadań, który będzie używany do wdrażania na klientach tylko w lokacji programu Configuration Manager. Prawdopodobnie można utworzyć kopię sekwencji zadań, która była używana do wdrażania na klientach w najnowszej wersji lokacji programu Configuration Manager, a następnie zmodyfikować sekwencję zadań, aby umożliwić jej wdrażanie na klientach w starszych lokacji programu Configuration Manager. Następnie należy skonfigurować sekwencję zadań, aby odwołać pakietu instalacyjnego klienta, który używa starszej źródła instalacji klienta programu Configuration Manager. Jeśli nie masz już niestandardowy pakiet instalacyjny klienta odwołujących się do źródła instalacji klienta programu Configuration Manager starsze następnie należy ręcznie go utworzyć.  
