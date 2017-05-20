---
title: "Planowanie współdziałania wdrożenia systemu operacyjnego | Dokumentacja firmy Microsoft"
description: "Zagadnienia dotyczące współdziałania należy zrozumieć, kiedy różnych lokacji programu System Center Configuration Manager w jednej hierarchii korzystają z różnych wersji."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: e327ce38-6c07-4a27-b6eb-7e5bf74ed04b
caps.latest.revision: 10
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 50a4b75b8c8c1cb6f7a8e696abad285f99080fcd
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="planning-for-operating-system-deployment-interoperability-in-system-center-configuration-manager"></a>Planowanie współdziałania w ramach wdrożenia systemu operacyjnego w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Niektóre funkcje programu Configuration Manager różnych lokacji programu System Center Configuration Manager w jednej hierarchii korzystają z różnych wersji, nie jest dostępna. Zwykle funkcje nowszej wersji programu Configuration Manager nie są dostępne w lokacjach lub dla klientów korzystających z niższej wersji. Aby uzyskać więcej informacji, zobacz [Współdziałanie różnych wersji programu System Center Configuration Manager](../../core/plan-design/hierarchy/interoperability-between-different-versions.md).  

 Podczas uaktualniania lokacji najwyższego poziomu w hierarchii oraz innych lokacji w hierarchii uruchomić program Configuration Manager za pomocą starszej wersji, należy wziąć pod uwagę następujące czynności:  

-   Pakiet instalacyjny klienta  

    -   Źródło domyślnego pakietu instalacyjnego klienta zostaje uaktualnione automatycznie, a wszystkie punkty dystrybucji w hierarchii są aktualizowane przy użyciu nowego pakietu instalacyjnego klienta, nawet w przypadku punktów dystrybucji w lokacjach w hierarchii, które mają być w starszej wersji.  

    -   Klientów korzystających z nowej wersji nie można przypisać do lokacji, które nie zostały jeszcze uaktualnione do nowej wersji. Przypisanie jest blokowane przez punkt zarządzania.  

-   Obrazy rozruchowe  

    -   Po uaktualnieniu lokacji najwyższego poziomu do najnowszej wersji programu Configuration Manager domyślne obrazy rozruchowe (x86 i x64) są automatycznie aktualizowane do obrazów rozruchowych opartych na Windows ADK dla systemu Windows 10, które używają systemu Windows PE 10. Pliki, które są skojarzone z domyślne obrazy rozruchowe są aktualizowane z najnowszą wersją programu Configuration Manager plików. Niestandardowe obrazy rozruchowe nie są automatycznie aktualizowane. Należy zaktualizować ręcznie, niestandardowe obrazy rozruchowe w tym starszych wersji środowiska Windows PE.  

    -   Kiedy hierarchia lokacji zawiera różne wersje programu Configuration Manager, należy unikać użycia nośników dynamicznych. Zamiast tego należy użyć nośnika oparty na lokacji skontaktować się z określonym punktem zarządzania, do momentu uaktualnienia wszystkich lokacji do tej samej wersji programu Configuration Manager.  

    -   Sprawdź, czy najnowsze obrazy rozruchowe programu Configuration Manager zawierają żądane dostosowania, a następnie zaktualizować wszystkie punkty dystrybucji w lokacjach z najnowszą wersją programu Configuration Manager przy użyciu nowych obrazów rozruchowych.  

-   Narzędzia do migracji stanu użytkowników (USMT)  

    -   Po uaktualnieniu lokacji najwyższego poziomu do najnowszej wersji programu Configuration Manager do domyślnego pakietu narzędzia USMT jest automatycznie zaktualizowana do najnowszej wersji. Niestandardowe pakiety narzędzia USMT nie są automatycznie aktualizowane. Pakiety tego typu należy aktualizować ręcznie.  

-   Nowe kroki sekwencji zadań  

    -   Okresowo kroki nowej sekwencji zadań są wprowadzane do nowych wersji programu Configuration Manager. Wdrażanie sekwencji zadań z nowym krokiem na starszych klientach zakończy się niepowodzeniem sekwencji zadań. Przed wdrożeniem sekwencji zadań w nowym kroku upewnij się, że klienci w kolekcji docelowej zostaną zaktualizowani do nowych wersji.  

-   Nośniki wdrażania systemu operacyjnego  

    -   Po zaktualizowaniu witryny do nowej wersji wszystkich nośników (przechwycenie dyskiem rozruchowym, przygotowanego i autonomicznych) muszą zostać zaktualizowane nowego pakietu klienta programu Configuration Manager.  

-   Rozszerzenia innych firm dotyczące wdrażania systemu operacyjnego  

    -   Gdy rozszerzenia innych firm w celu wdrożenia systemu operacyjnego i korzystają z różnych wersji lokacji programu Configuration Manager lub klientów programu Configuration Manager, hierarchii mieszanej, mogą wystąpić problemy z rozszerzeniami.  

 Podczas aktywnego uaktualniania lokacji w hierarchii skorzystaj z poniższych sekcji, które zapewniają pomoc podczas wdrożeń systemu operacyjnego.  

## <a name="latest-version-of-configuration-manager-sites-in-a-mixed-hierarchy"></a>Najnowszą wersję lokacji programu Configuration Manager w hierarchii mieszanej  
 Podczas uaktualniania lokacji do najnowszej wersji programu Configuration Manager, sekwencje zadań, które automatycznie rozpocznie odwołanie do domyślnego pakietu instalacyjnego klienta, aby wdrożyć najnowszą wersję klienta programu Configuration Manager. Sekwencje zadań, które odwołują się do pakietu instalacyjnego klienta będzie nadal wdrażać wersję klienta zawartą w tym pakiecie niestandardowym (najprawdopodobniej poprzedniej wersji programu Configuration Manager klienta) i muszą zostać zaktualizowane w celu uniknięcia niepowodzeń wdrażania sekwencji zadań. Jeżeli sekwencja zadań, który jest skonfigurowany do użycia niestandardowego pakietu instalacyjnego klienta, należy zaktualizować sekwencję zadań, aby korzystać z najnowszej wersji programu Configuration Manager z pakietu instalacyjnego klienta lub zaktualizować pakiet niestandardowy w celu używania najnowszych źródła instalacji klienta programu Configuration Manager.  

> [!IMPORTANT]  
>  Nie należy wdrażać sekwencji zadań, która odwołuje się do najnowszego pakietu instalacyjnego klienta programu Configuration Manager do klientów w starszych lokacji programu Configuration Manager. Podczas uaktualniania klientów przypisanych do starszych lokacji programu Configuration Manager do najnowszej wersji klienta programu Configuration Manager, Configuration Manager blokuje przypisanie do lokacji programu Configuration Manager starszej. W związku z tym klient nie będzie już przypisany do żadnej lokacji i pozostanie niezarządzany do momentu ręcznie przypisać klienta do najnowszej lokacji programu Configuration Manager lub ponownie zainstalować starszą wersję klienta programu Configuration Manager na komputerze.  

## <a name="older-versions-of-configuration-manager-in-a-mixed-hierarchy"></a>Starsze wersje programu Configuration Manager w hierarchii mieszanej  
 Po uaktualnieniu centralnej lokacji administracyjnej do najnowszej wersji programu Configuration Manager, należy wykonać następujące czynności w celu zapewnienia, że sekwencje zadań wdrażania systemu operacyjnego, które są wdrażane na klientach przypisanych do starszych lokacji programu Configuration Manager (jeszcze nie uaktualnione do najnowszej wersji programu Configuration Manager) nie spowodują pozostawienia tych klientów w stanie niezarządzanym.  

-   Tworzenie sekwencji zadań, które będą używane do wdrażania na klientach tylko w lokacji programu Configuration Manager. Prawdopodobne należy utworzyć kopię sekwencji zadań, która umożliwia wdrażanie na klientach w najnowszej wersji lokacji programu Configuration Manager, a następnie zmodyfikować sekwencję zadań, aby można go wdrożyć na klientach w starszych lokacji programu Configuration Manager. Następnie należy skonfigurować sekwencję zadań, aby odwołać pakietu instalacyjnego klienta, który używa starszej źródła instalacji klienta programu Configuration Manager. Jeśli nie masz już niestandardowego pakietu instalacyjnego klienta odwołujący się starsze źródła instalacji klienta programu Configuration Manager następnie należy ręcznie utworzyć jeden.  

