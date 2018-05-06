---
title: Wykorzystanie danych diagnostycznych
titleSuffix: Configuration Manager
description: Więcej informacji o używaniu Microsoft diagnostycznych i danych użycia, która gromadzi System Center Configuration Manager.
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: a8021bc8-2799-41f4-83c2-e27d1242028c
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: fac92818a56b9ef7c7e8e6b923fb0d833f9053c2
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-diagnostics-and-usage-data-is-used-for-system-center-configuration-manager"></a>Jak używane są dane diagnostyczne i dane użycia dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Dane diagnostyczne i użycia, która gromadzi System Center Configuration Manager udostępnia Microsoft niemal natychmiast uzyskuje opinie na temat jak produkt działa i jest używane do dostosowywania przyszłych aktualizacji. Może także wyświetlić dane konfiguracji, które pomagają opracowywać i testować konfiguracje znajdujące się na etapie produkcji. Na przykład:  

-   Wersje serwera z systemem Windows, które są używane przez serwery lokacji  

-   Pakiety językowe zainstalowany  

-   Różnica między schematem SQL i domyślną konfiguracją produktu  

Te dane ułatwiają zespołowi inżynierów planowanie przyszłych testów, które zapewnią najlepsze środowisko dla najbardziej typowych konfiguracji. Aktualizacje do programu Configuration Manager zostaną zwolnione na szybko (w celu skuteczniejszej obsługi szybko rozwijających się technologii, takich jak Windows 10 i Microsoft Intune), dane te są niezwykle ważny do szybkiego dostosowywania i adaptowania.  

Równie ważne jest sposób danych diagnostycznych i użycia nie jest używany. Firma Microsoft nie używa tych danych do następujących celów:  

-   Inspekcje związane z licencjonowaniem, takie jak porównywanie użycia przez klientów z umowami licencyjnymi.  

-   Inspekcja produktów, dla których pomoc techniczna nie jest dostępna.  

-   Reklamy oparte na dostępnych danych, takich jak użycie funkcji lub geolokalizacja (strefa czasowa)  

##  <a name="bkmk_improve"></a> Przykłady sposobu diagnostyczne i dane użycia zwiększa produktu  
Firma Microsoft używa dostępnych danych do ulepszenia produktu. Poniżej przedstawiono kilka przykładów:  

-   **Zweryfikowana pomoc techniczna dla starszych systemów operacyjnych serwera:**  

     Początkowej pomocy technicznej oferowanej przez bieżącej gałęzi programu System Center Configuration Manager ograniczoną osi czasu pomocy technicznej dla systemu Windows Server 2008 R2. Po zbadaniu danych użycia od klientów, którzy przeprowadzili uaktualnienie do programu Configuration Manager current branch, określiliśmy, że trzeba zweryfikowanie i rozszerzenie tej osi czasu w celu obsługi klientów, którzy nadal korzystać z tego systemu operacyjnego hosta serwerów lokacji i ról systemu lokacji.  

-   **Ulepszone sprawdzanie wymagań wstępnych:**  

     Na podstawie danych użycia, firma Microsoft ulepszyła Sprawdzanie wymagań wstępnych dotyczące instalowania aktualizacji, usuwając przestarzałe reguły, uwzględniając dodatkowe przypadki, a w niektórych przypadkach automatyczne rozwiązywanie niektórych problemów.  
