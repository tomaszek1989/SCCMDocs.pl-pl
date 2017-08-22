---
title: "Lokalizacja źródła zawartości | Dokumentacja firmy Microsoft"
description: "Dowiedz się więcej o ustawieniach System Center Configuration Manager, które pozwalają klientom znaleźć zawartości w wolnej sieci."
ms.custom: na
ms.date: 1/3/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 70b5cbc0-64ba-49bd-8b34-fb4c09b2b95b
caps.latest.revision: "3"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: a823458dc3b891b1c32d1cb44a96e8cafd376ed5
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="content-source-location-scenarios-in-system-center-configuration-manager"></a>Scenariusze lokalizacji źródła zawartości w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Poprzedzające wersję 1610 System Center Configuration Manager obsługuje kilka ustawień, które definiują sposób i gdzie klienci znaleźć zawartości, gdy są one w wolnej sieci połączone. Możliwe kombinacje wpływ na wykorzystanie klientów lokalizacji zawartości i czy można pomyślnie używają rezerwowy, gdy preferowanym źródłem zawartości nie jest dostępny.  

> [!IMPORTANT]  
> **Jeśli Lokacje uruchomione w wersji 1511, 1602 lub 1606**, informacje przedstawione w tym temacie dotyczą infrastruktury. Zobacz też [grup granic dla wersji 1511,1602 i 1606](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606) informacje, które są specyficzne dla grupy granic z tymi wersjami programu Configuration Manager.
>
> **Jeśli Lokacje wersją 1610 lub nowszym**, skorzystaj z informacji w [Definiowanie granic lokacji i grup granic dla programu System Center Configuration Manager](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups) zrozumieć, jak klienci znajdują punkty dystrybucji, które ma dostępnej zawartości.





**Poniższe trzy ustawienia Definiowanie zachowania, gdy klienci żądają zawartości:**

-  **Zezwalaj na rezerwową lokalizację źródła zawartości** (włączona lub wyłączona): Jest to opcja, która pozwala na **grup granic** kartę punktu dystrybucji. Dzięki temu klient może używać punktu dystrybucji skonfigurowanego jako rezerwowy, gdy zawartość nie jest dostępna w preferowanym punkcie dystrybucji.  

 - **Zachowanie wdrażania dla danej szybkości połączenia sieciowego**: Każde wdrożenie jest skonfigurowane z jednym z następujących zachowań do użycia podczas połączenia z punktem dystrybucji jest wolne:  

    -   **Pobierz zawartość z punktu dystrybucji i uruchom lokalnie**  

    -   **Nie pobieraj zawartości**: Ta opcja jest używana tylko w przypadku, gdy klient używa lokalizacji rezerwowej w celu uzyskania zawartości.  

    Szybkość połączenia dla punktu dystrybucji jest skonfigurowany na **odwołania** karcie grupy granic i jest specyficzna dla tej grupy granic.  

 -  **Dystrybucji pakietów na żądanie** (do preferowanych punktów dystrybucji): Ta opcja jest włączona po wybraniu opcji **Dystrybuuj zawartość tego pakietu do preferowanych punktów dystrybucji** na **ustawienia dystrybucji** na karcie właściwości pakietu lub aplikacji. Po włączeniu ta opcja nakazuje programowi Configuration Manager automatyczne kopiowanie zawartości do punktu dystrybucji, który nie ma jeszcze zawartości po klient zażąda zawartości z tego punktu dystrybucji.  


 **Poniższe wymagania dotyczą wszystkich scenariuszy:**


-   Zawartość jest dostępna w rezerwowym punkcie dystrybucji  

-   Punkty dystrybucji są w trybie online i jest dostępny  


## <a name="scenario-1"></a>Scenariusz 1  
 Ma zastosowanie, gdy istnieją następujące konfiguracje:  

-   **Zawartość jest dostępna w preferowanym punkcie dystrybucji.**  

-   **Zezwalaj na przełączanie awaryjne**: Niewłączona  

-   **Zachowanie wdrażania w przypadku wolnej sieci**: Żadnej konfiguracji  


**Szczegóły:** (Konfiguracja dystrybucji pakietów na żądanie nie jest ważna w tym scenariuszu).  

1.  Klient wysyła żądanie zawartości do punktu zarządzania.  

2.  Lista lokalizacji zawartości jest zwracana do klienta z punktu zarządzania z preferowanymi punktami dystrybucji z zawartością.  

3.  Klient pobiera zawartość z preferowanego punktu dystrybucji na liście.  

## <a name="scenario-2"></a>Scenariusz 2  
 Istnieją następujące konfiguracje:  

-   **Zawartość jest dostępna w preferowanym punkcie dystrybucji.**  

-   **Zezwalaj na przełączanie awaryjne**: Włączono  

-   **Zachowanie wdrażania w przypadku wolnej sieci**: Nie pobieraj zawartości  


**Szczegóły:** (Konfiguracja dystrybucji pakietów na żądanie nie jest ważna w tym scenariuszu).  

1.  Klient wysyła żądanie zawartości do punktu zarządzania. Klient dołącza flagę żądania, która wskazuje, że rezerwowymi punktami dystrybucji są dozwolone.  

2.  Lista lokalizacji zawartości jest zwracana do klienta z punktu zarządzania z preferowanych punktów dystrybucji i rezerwowymi punktami dystrybucji z zawartością.  

3.  Klient pobiera zawartość z preferowanego punktu dystrybucji na liście.  

## <a name="scenario-3"></a>Scenariusz 3  
 Istnieją następujące konfiguracje:  

-   **Zawartość jest dostępna w preferowanym punkcie dystrybucji.**  

-   **Zezwalaj na przełączanie awaryjne**: Włączono  

-   **Zachowanie wdrażania w przypadku wolnej sieci**: Pobieraj i instaluj zawartość  


**Szczegóły:** (Konfiguracja dystrybucji pakietów na żądanie nie jest ważna w tym scenariuszu).  

1.  Klient wysyła żądanie zawartości do punktu zarządzania. Klient dołącza flagę żądania, która wskazuje, że rezerwowymi punktami dystrybucji są dozwolone.  

2.  Lista lokalizacji zawartości jest zwracana do klienta z punktu zarządzania z preferowanych punktów dystrybucji i rezerwowymi punktami dystrybucji z zawartością.  

3.  Klient pobiera zawartość z preferowanego punktu dystrybucji na liście.  

## <a name="scenario-4"></a>Scenariusz 4  
 Istnieją następujące konfiguracje:  

-   **Zawartość nie jest dostępna w preferowanym punkcie dystrybucji.**  

-   **Dystrybuuj zawartość tego pakietu do preferowanych punktów dystrybucji** nie jest włączone  

-   **Zezwalaj na przełączanie awaryjne**: Niewłączona  

-   **Zachowanie wdrażania w przypadku wolnej sieci**: Żadnej konfiguracji  


**Szczegóły:**  

1.  Klient wysyła żądanie zawartości do punktu zarządzania.  

2.  Lista lokalizacji zawartości jest zwracana do klienta z punktu zarządzania z preferowanych punktów dystrybucji zawierających daną zawartość. Istnieją preferowane punkty dystrybucji na liście.  

3.  Klient nie powiedzie się z komunikatem **zawartość nie jest dostępna** i przechodzi do trybu ponawiania próby. Żądanie nowej zawartości jest uruchamiane co godzinę.  

## <a name="scenario-5"></a>W scenariuszu 5  
 Istnieją następujące konfiguracje:  

-   **Zawartość nie jest dostępna w preferowanym punkcie dystrybucji.**  

-   **Dystrybuuj zawartość tego pakietu do preferowanych punktów dystrybucji** nie jest włączone  

-   **Zezwalaj na przełączanie awaryjne**: Włączono  

-   **Zachowanie wdrażania w przypadku wolnej sieci**: Nie pobieraj zawartości  


**Szczegóły:**  

1.  Klient wysyła żądanie zawartości do punktu zarządzania. Klient dołącza flagę żądania, która wskazuje, że rezerwowymi punktami dystrybucji są dozwolone.  

2.  Lista lokalizacji zawartości jest zwracana do klienta z punktu zarządzania z preferowanych punktów dystrybucji i rezerwowymi punktami dystrybucji z zawartością. Istnieją preferowane punkty dystrybucji z zawartością, ale co najmniej jeden rezerwowy punkt dystrybucji ma zawartość.  

3.  Zawartość nie jest pobierana, ponieważ właściwość wdrożenia określająca, kiedy klient ma korzystać z rezerwowego punktu dystrybucji jest ustawiona **nie pobieraj zawartości** (który jest używany, gdy klient nawiąże rezerwowe uzyskanie zawartości). Klient nie powiedzie się z komunikatem **zawartość nie jest dostępna** i przechodzi do trybu ponawiania próby. Klient wysyła żądanie nowej zawartości co godzinę.  

## <a name="scenario-6"></a>Scenariusz 6  
 Istnieją następujące konfiguracje:  

-   **Zawartość nie jest dostępna w preferowanym punkcie dystrybucji.**  

-   **Dystrybuuj zawartość tego pakietu do preferowanych punktów dystrybucji** nie jest włączone  

-   **Zezwalaj na przełączanie awaryjne**: Włączono  

-   **Zachowanie wdrażania w przypadku wolnej sieci**: Pobieraj i instaluj zawartość  


**Szczegóły:**  

1.  Klient wysyła żądanie zawartości do punktu zarządzania. Klient dołącza flagę żądania, która wskazuje, czy są włączone rezerwowymi punktami dystrybucji.  

2.  Lista lokalizacji zawartości jest zwracana do klienta z punktu zarządzania z preferowanych punktów dystrybucji i rezerwowymi punktami dystrybucji z zawartością. Istnieją preferowane punkty dystrybucji z zawartością, ale co najmniej jeden rezerwowy punkt dystrybucji z zawartością.  

3.  Zawartość jest pobierana z rezerwowego punktu dystrybucji na liście, ponieważ właściwość wdrożenia określająca, kiedy klient ma korzystać z rezerwowego punktu dystrybucji jest ustawiona **pobieraj i instaluj zawartość**.  

## <a name="scenario-7"></a>Scenariusz 7  
 Istnieją następujące konfiguracje:  

-   **Zawartość nie jest dostępna w preferowanym punkcie dystrybucji.**  

-   **Dystrybuuj zawartość tego pakietu do preferowanych punktów dystrybucji** jest włączone  

-   **Zezwalaj na przełączanie awaryjne**: Niewłączona  

-   **Zachowanie wdrażania w przypadku wolnej sieci**: Żadnej konfiguracji  


**Szczegóły:**  

1.  Klient wysyła żądanie zawartości do punktu zarządzania.  

2.  Lista lokalizacji zawartości jest zwracana do klienta z punktu zarządzania z preferowanych punktów dystrybucji zawierających daną zawartość. Nie istnieją preferowane punkty dystrybucji z zawartością.  

3.  Klient nie powiedzie się z komunikatem **zawartość nie jest dostępna** i przechodzi do trybu ponawiania próby. Żądanie nowej zawartości jest składane co godzinę.  

4.  Punkt zarządzania tworzy wyzwalacz dla menedżerowi dystrybucji rozesłanie zawartości do wszystkich preferowanych punktów dystrybucji klienta, który wysłał żądanie zawartości.  

5.  Menedżer dystrybucji dystrybuuje zawartość do wszystkich preferowanych punktów dystrybucji. W większości przypadków zawartość jest pomyślnie wysyłana do preferowanych punktów dystrybucji w ciągu godziny.  

6.  Żądanie nowej zawartości jest inicjowane przez klienta do punktu zarządzania.  

7.  Lista lokalizacji zawartości jest zwracana do klienta z punktu zarządzania z preferowanych punktów dystrybucji zawierających daną zawartość. Klient pobiera zawartość z preferowanego punktu dystrybucji na liście.  

## <a name="scenario-8"></a>Scenariusz 8  
 Istnieją następujące konfiguracje:  

-   **Zawartość nie jest dostępna w preferowanym punkcie dystrybucji.**  

-   **Dystrybuuj zawartość tego pakietu do preferowanych punktów dystrybucji** jest włączone  

-   **Zezwalaj na przełączanie awaryjne**: Włączono  

-   **Zachowanie wdrażania w przypadku wolnej sieci**: Nie pobieraj zawartości  


**Szczegóły:**  

1.  Klient wysyła żądanie zawartości do punktu zarządzania. Klient dołącza flagę żądania, która wskazuje, że rezerwowymi punktami dystrybucji są dozwolone.  

2.  Lista lokalizacji zawartości jest zwracana do klienta z punktu zarządzania z preferowanych punktów dystrybucji i rezerwowymi punktami dystrybucji z zawartością. Istnieją preferowane punkty dystrybucji z zawartością, ale co najmniej jeden rezerwowy punkt dystrybucji ma zawartość.  

3.  Zawartość nie jest pobierana, ponieważ właściwość wdrożenia określająca, kiedy klient ma korzystać z rezerwowego punktu dystrybucji jest ustawiona **nie pobieraj**. Klient nie powiedzie się z komunikatem **zawartość nie jest dostępna** i przechodzi do trybu ponawiania próby. Klient wysyła żądanie nowej zawartości co godzinę.  

4.  Punkt zarządzania tworzy wyzwalacz dla menedżerowi dystrybucji rozesłanie zawartości do wszystkich preferowanych punktów dystrybucji klienta, który wysłał żądanie zawartości.  

5.  Menedżer dystrybucji dystrybuuje zawartość do wszystkich preferowanych punktów dystrybucji. W większości przypadków zawartość jest pomyślnie wysyłana do preferowanych punktów dystrybucji w ciągu godziny.  

6.  Żądanie nowej zawartości jest inicjowane przez klienta do punktu zarządzania.  

7.  Lista lokalizacji zawartości jest zwracana do klienta z punktu zarządzania z preferowanych punktów dystrybucji zawierających daną zawartość.  

8.  Klient pobiera zawartość z preferowanego punktu dystrybucji na liście.  

## <a name="scenario-9"></a>Scenariusz 9  
 Istnieją następujące konfiguracje:  

-   **Zawartość nie jest dostępna w preferowanym punkcie dystrybucji.**  

-   **Dystrybuuj zawartość tego pakietu do preferowanych punktów dystrybucji** jest włączone  

-   **Zezwalaj na przełączanie awaryjne**: Włączono  

-   **Zachowanie wdrażania w przypadku wolnej sieci**: Pobieraj i instaluj zawartość  


**Szczegóły:**  

1.  Klient wysyła żądanie zawartości do punktu zarządzania. Klient dołącza flagę żądania, która wskazuje, że rezerwowymi punktami dystrybucji są dozwolone.  

2.  Lista lokalizacji zawartości jest zwracana do klienta z punktu zarządzania z preferowanych punktów dystrybucji i rezerwowymi punktami dystrybucji z zawartością. Istnieją preferowane punkty dystrybucji z zawartością, ale co najmniej jeden rezerwowy punkt dystrybucji ma zawartość.  

3.  Zawartość jest pobierana z rezerwowego punktu dystrybucji na liście, ponieważ właściwość wdrożenia określająca, kiedy klient ma korzystać z rezerwowego punktu dystrybucji jest ustawiona **pobieraj i instaluj zawartość**. To ustawienie wdrożenia umożliwia klientowi musi używać rezerwowej lokalizacji zawartości, uzyskanie zawartości z tej lokalizacji.  

4.  Punkt zarządzania tworzy wyzwalacz dla menedżerowi dystrybucji rozesłanie zawartości do wszystkich preferowanych punktów dystrybucji klienta, który wysłał żądanie zawartości.  

5.  Menedżer dystrybucji dystrybuuje zawartość do wszystkich preferowanych punktów dystrybucji, co umożliwia dodatkowym klientom uzyskanie zawartości bez korzystania z rezerwowego punktu dystrybucji.  
