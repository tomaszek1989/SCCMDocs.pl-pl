---
title: Wykorzystanie danych diagnostyki | Dokumentacja firmy Microsoft
description: "Dowiedz się, jak firma Microsoft używa diagnostyki i System Center Configuration Manager służy do zbierania danych użycia."
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a8021bc8-2799-41f4-83c2-e27d1242028c
caps.latest.revision: 5
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 24a233516058e645df2a43623855665b97b041b0
ms.openlocfilehash: 9864f6ba7b9a2211c99b1a5d9ebd582e01ccfeb6
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-diagnostics-and-usage-data-is-used-for-system-center-configuration-manager"></a>Jak używane są dane diagnostyczne i dane użycia dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

System Center Configuration Manager służy do zbierania danych diagnostycznych i użycia zawiera Microsoft niemal natychmiastowe opinię na temat sposobu produktu działa i jest używany do dostosowania przyszłych aktualizacji. Może także wyświetlić dane konfiguracji, które pomagają opracowywać i testować konfiguracje znajdujące się na etapie produkcji. Na przykład:  

-   Wersje serwera z systemem Windows, które są używane przez serwery lokacji  

-   Zainstalowanych pakietów językowych  

-   Różnica między schematem SQL i domyślną konfiguracją produktu  

Te dane ułatwiają zespołowi inżynierów planowanie przyszłych testów, które zapewnią najlepsze środowisko dla najbardziej typowych konfiguracji. Aktualizacje programu Configuration Manager zostaną zwolnione na szybsze wydawania oprogramowania (w celu lepszej obsługi szybkim przesuwaniem technologii, takich jak Microsoft Intune i Windows 10), te dane są najważniejsze szybkie dostosowywanie i dostosowania.  

Równie ważne jest jak danych diagnostycznych i użycia nie jest używany. Firma Microsoft nie używa tych danych do następujących celów:  

-   Inspekcje związane z licencjonowaniem, takie jak porównywanie użycia przez klientów z umowami licencyjnymi.  

-   Inspekcja produktów, dla których pomoc techniczna nie jest dostępna.  

-   Reklamy oparte na dostępnych danych, takich jak użycie funkcji lub używanie funkcji geolokalizacji (strefa czasowa)  

##  <a name="bkmk_improve"></a>Przykłady jak danych diagnostycznych i użycia poprawia produktu  
Firma Microsoft używa dostępnych danych do ulepszenia produktu. Poniżej przedstawiono kilka przykładów:  

-   **Zweryfikowana pomoc techniczna dla starszych systemów operacyjnych serwera:**  

     Początkowa pomocy technicznej oferowanej przez bieżącej gałęzi programu System Center Configuration Manager ograniczone oś czasu pomocy technicznej dla systemu Windows Server 2008 R2. Po zbadaniu danych użycia od klientów, którzy były uaktualnione do programu Configuration Manager w bieżącej gałęzi, możemy zidentyfikować konieczność skorygowania i rozszerzenia oś czasu do obsługi klientów, którzy nadal korzystać z tego systemu operacyjnego serwera hosta serwerów lokacji i ról systemu lokacji.  

-   **Ulepszone sprawdzanie wymagań wstępnych:**  

     Na podstawie danych użycia, firma Microsoft ma ulepszoną Sprawdzanie wymagań wstępnych instalacji aktualizacji, aby usunąć przestarzałe reguły, konta w przypadku, gdy dodatkowe, a w niektórych przypadkach automatycznie rozwiązać niektóre problemy.  

