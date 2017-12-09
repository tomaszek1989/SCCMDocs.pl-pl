---
title: Wykorzystanie danych diagnostycznych
titleSuffix: Configuration Manager
description: "Więcej informacji o używaniu Microsoft diagnostycznych i danych użycia, która gromadzi System Center Configuration Manager."
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a8021bc8-2799-41f4-83c2-e27d1242028c
caps.latest.revision: "5"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: d34305ddb158a01c0d79189705af597344a56f8d
ms.sourcegitcommit: da27d37cc4e4e06cf23758846cdd7acb617f744b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/08/2017
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

##  <a name="bkmk_improve"></a>Przykłady sposobu diagnostyczne i dane użycia zwiększa produktu  
Firma Microsoft używa dostępnych danych do ulepszenia produktu. Poniżej przedstawiono kilka przykładów:  

-   **Zweryfikowana pomoc techniczna dla starszych systemów operacyjnych serwera:**  

     Początkowej pomocy technicznej oferowanej przez bieżącej gałęzi programu System Center Configuration Manager ograniczoną osi czasu pomocy technicznej dla systemu Windows Server 2008 R2. Po zbadaniu danych użycia od klientów, którzy przeprowadzili uaktualnienie do programu Configuration Manager current branch, określiliśmy, że trzeba zweryfikowanie i rozszerzenie tej osi czasu w celu obsługi klientów, którzy nadal korzystać z tego systemu operacyjnego hosta serwerów lokacji i ról systemu lokacji.  

-   **Ulepszone sprawdzanie wymagań wstępnych:**  

     Na podstawie danych użycia, firma Microsoft ulepszyła Sprawdzanie wymagań wstępnych dotyczące instalowania aktualizacji, usuwając przestarzałe reguły, uwzględniając dodatkowe przypadki, a w niektórych przypadkach automatyczne rozwiązywanie niektórych problemów.  
