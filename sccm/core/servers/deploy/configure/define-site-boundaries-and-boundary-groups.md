---
title: "Użyj granic i grup granic"
titleSuffix: Configuration Manager
description: "Użyj granic i grup granic, aby zdefiniować lokalizacje sieciowe i systemy lokacji dostępne dla urządzeń, którymi zarządzasz."
ms.custom: na
ms.date: 3/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 54aa20d5-791e-4416-9db4-5aaea472c0b7
caps.latest.revision: "10"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 5980b33cef6e7711e09c3199150bf60008d1a73b
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="define-site-boundaries-and-boundary-groups-for-system-center-configuration-manager"></a>Definiowanie granic lokacji i grup granic dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Granice programu System Center Configuration Manager definiują lokalizacje sieciowe w intranecie, które mogą zawierać urządzenia, które mają być zarządzane. Grupy granic to logiczne grupy granic, które można skonfigurować.

 Hierarchia może zawierać dowolną liczbę grup granic, a każda grupa granic może zawierać dowolną kombinację następujących typów granic:  

-   Podsieć IP  
-   Nazwa lokacji usługi Active Directory  
-   Prefiks adresów IPv6  
-   Zakres adresów IP  

Klienci w intranecie oceniają swoją bieżącą lokalizację sieciową, a następnie używają tej informacji do zidentyfikowania grup granic, do których należą.  

 Klienci używają grup granic do:  
-   **Znajdowania przypisanej lokacji:** Grupy granic pozwalają klientom znaleźć lokację główną dla przypisania klienta (automatyczne przypisanie lokacji).  
-   **Znajdź określone role systemu lokacji, które mogą używać:** Gdy grupa granic jest kojarzona z niektórych ról systemu lokacji, grupa granic dostarcza klientom listę systemów lokacji do użytku podczas lokalizacji zawartości i jako preferowane punkty zarządzania.  

Klienci znajdujący się w Internecie lub skonfigurowani jako klienci wyłącznie internetowi nie używają informacji o granicach. Tacy klienci nie mogą używać automatycznego przypisania lokacji i zawsze mogą pobierać zawartość z dowolnego punktu dystrybucji w przypisanej lokacji, gdy tylko punkt dystrybucji jest skonfigurowany tak, aby zezwalał na połączenia klienckie z Internetu.  

**Aby rozpocząć:**
- Najpierw [definiują lokalizacje sieciowe jako granic](/sccm/core/servers/deploy/configure/boundaries).
- Następnie kontynuuj przez [konfigurowania grup granic](/sccm/core/servers/deploy/configure/boundary-groups) do klientów w tych granicach na serwerach systemu lokacji, mogą używać skojarzenia.



##  <a name="BKMK_BoundaryBestPractices"></a>Najlepsze rozwiązania dotyczące granic i grup granic  

-   **Użyj kombinacji najmniejszej granice, które odpowiadają Twoim potrzebom:**  
   W przeszłości firma Microsoft zaleca użycie niektórych typów granic przez innych użytkowników. Zmiany, aby poprawić wydajność, możemy teraz zaleca się użyć, niezależnie od typu granicy lub typy możesz wybrać, które działa dla środowiska i umożliwiające używać najmniejszej liczby granice można uprościć zadania związane z zarządzaniem.      

-   **Należy unikać nakładania się granic na potrzeby automatycznego przypisywania lokacji:**  
     Mimo że każda grupa granic obsługuje konfiguracje przypisania lokacji oraz konfiguracje lokalizacji zawartości, najlepiej jest tworzyć osobne zestawy grup granic do użycia tylko dla przypisania lokacji. Innymi słowy, należy upewnić się, że żadna granica w grupie granic nie jest elementem członkowskim innej grupy granic z innym przypisaniem lokacji. Jest tak, ponieważ:  

    -   Pojedyncza granica może zostać uwzględniona w wielu grupach granic.  

    -   Każdą grupę granic można skojarzyć z inną lokacją główną na potrzeby przypisania lokacji.  

    -   Klient w granicy, która jest elementem członkowskim dwóch różnych grup granic z różnymi przypisaniami lokacji, będzie losowo wybierać lokację na potrzeby przyłączenia i może to być lokacja inna od zamierzonej.  Ta konfiguracja jest nazywana nakładającymi się granicami.  

     Nakładające się granice nie stanowią problemu dla lokalizacji zawartości, a często są nawet pożądaną konfiguracją, która zapewnia klientom dodatkowe zasoby lub lokalizacje zawartości do użycia.  
