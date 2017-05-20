---
title: "Lokalizacja źródła zawartości | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat ustawienia programu System Center Configuration Manager, które umożliwiają klientom znaleźć zawartości na wolną sieć."
ms.custom: na
ms.date: 1/3/2017
ms.reviewer: na
ms.suite: na
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 70b5cbc0-64ba-49bd-8b34-fb4c09b2b95b
caps.latest.revision: 3
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 7f2fd3e550c7dc1b27996dc309b53f74e8c865e9
ms.openlocfilehash: a823458dc3b891b1c32d1cb44a96e8cafd376ed5
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="content-source-location-scenarios-in-system-center-configuration-manager"></a>Scenariusze lokalizacji źródła zawartości w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Przed wersją 1610 programu System Center Configuration Manager obsługuje kilka ustawień, które są połączone, zdefiniuj sposób i gdzie wyszukiwania zawartości przez klientów znajdujących się w wolną sieć. Możliwych kombinacji wpływ na wykorzystanie klientów lokalizacji zawartości i czy pomyślnie mogą korzystać podczas preferowanym źródłem rezerwowej lokalizacji zawartości nie jest dostępna.  

> [!IMPORTANT]  
> **Jeśli Lokacje uruchomić wersję 1511, 1602 lub 1606**, informacje przedstawione w tym temacie dotyczą infrastruktury. Zobacz też [grup granic dla wersji 1511,1602 i 1606](/sccm/core/servers/deploy/configure/boundary-groups-for-1511-1602-and-1606) informacji, które są specyficzne dla grupy granic z tych wersji programu Configuration Manager.
>
> **Jeśli Lokacje uruchomić wersję 1610 lub nowszej**, informacje zawarte w [zdefiniować granice lokacji i grup granic dla programu System Center Configuration Manager](/sccm/core/servers/deploy/configure/define-site-boundaries-and-boundary-groups#boundary-groups) zrozumienie znajdowania punktów dystrybucji zawierających dostępnej zawartości z klientów.





**Poniższe trzy ustawienia Definiowanie zachowania, gdy klienci żądają zawartości:**

-  **Zezwalaj na rezerwową lokalizację źródła zawartości** (włączona lub wyłączona): Jest to opcja, która pozwala na **grup granic** kartę punktu dystrybucji. Pozwala to klientowi korzystanie z punktu dystrybucji skonfigurowanego jako rezerwowej, gdy zawartość nie jest dostępna w preferowanym punkcie dystrybucji.  

 - **Zachowanie wdrażania dla danej szybkości połączenia sieciowego**: Każdego wdrożenia jest skonfigurowany przy użyciu jednego z następujących zachowań do użycia podczas połączenia z punktem dystrybucji jest wolne:  

    -   **Pobieranie zawartości z punktu dystrybucji i uruchom lokalnie**  

    -   **Nie pobieraj zawartości**: Ta opcja jest używana tylko wtedy, gdy klient używa rezerwowej uzyskanie zawartości.  

    Szybkość połączenia dla punktu dystrybucji jest skonfigurowany na **odwołania** grupy granic i są specyficzne dla tej grupy granic.  

 -  **Dystrybucji na żądanie** (do preferowanych punktów dystrybucji): Ta opcja jest włączona po wybraniu opcji **Dystrybuuj zawartość tego pakietu do preferowanych punktów dystrybucji** na **ustawienia dystrybucji** właściwości pakietu lub aplikacji. Po włączeniu tej opcji kieruje programu Configuration Manager do automatycznego kopiowania zawartości do punktu dystrybucji nie ma jeszcze zawartości po klient zażąda zawartości z tego punktu dystrybucji.  


 **Wszystkie scenariusze mają zastosowanie następujące wymagania:**


-   Zawartość jest dostępna w rezerwowym punkcie dystrybucji  

-   Punkty dystrybucji są w trybie online i jest dostępny  


## <a name="scenario-1"></a>Scenariusz 1  
 Mają zastosowanie, gdy istnieją następujące konfiguracje:  

-   **Zawartość jest dostępna w preferowanym punkcie dystrybucji**  

-   **Zezwalaj na powrót**: Niewłączone  

-   **Sposób działania wdrożenia w przypadku wolnej sieci**: Żadnej konfiguracji  


**Szczegóły:** (Konfiguracja dla dystrybucji na żądanie nie jest ważna w tym scenariuszu).  

1.  Klient wysyła żądanie zawartości do punktu zarządzania.  

2.  Lista lokalizacji zawartości jest zwracana do klienta z punktu zarządzania z preferowanymi punktami dystrybucji z zawartością.  

3.  Klient pobiera zawartość z preferowanego punktu dystrybucji na liście.  

## <a name="scenario-2"></a>Scenariusz 2  
 Istnieją następujące konfiguracje:  

-   **Zawartość jest dostępna w preferowanym punkcie dystrybucji**  

-   **Zezwalaj na powrót**: Włączono  

-   **Sposób działania wdrożenia w przypadku wolnej sieci**: Nie pobieraj zawartości  


**Szczegóły:** (Konfiguracja dla dystrybucji na żądanie nie jest ważna w tym scenariuszu).  

1.  Klient wysyła żądanie zawartości do punktu zarządzania. Klient dołącza flagę żądanie, która wskazuje, że rezerwowe punkty dystrybucji są dozwolone.  

2.  Lista lokalizacji zawartości jest zwracana do klienta z punktu zarządzania z preferowanymi oraz rezerwowymi punktami dystrybucji z zawartością.  

3.  Klient pobiera zawartość z preferowanego punktu dystrybucji na liście.  

## <a name="scenario-3"></a>Scenariusz 3  
 Istnieją następujące konfiguracje:  

-   **Zawartość jest dostępna w preferowanym punkcie dystrybucji**  

-   **Zezwalaj na powrót**: Włączono  

-   **Sposób działania wdrożenia w przypadku wolnej sieci**: Pobierz i zainstaluj zawartość  


**Szczegóły:** (Konfiguracja dla dystrybucji na żądanie nie jest ważna w tym scenariuszu).  

1.  Klient wysyła żądanie zawartości do punktu zarządzania. Klient dołącza flagę żądanie, która wskazuje, że rezerwowe punkty dystrybucji są dozwolone.  

2.  Lista lokalizacji zawartości jest zwracana do klienta z punktu zarządzania z preferowanymi oraz rezerwowymi punktami dystrybucji z zawartością.  

3.  Klient pobiera zawartość z preferowanego punktu dystrybucji na liście.  

## <a name="scenario-4"></a>Scenariusz 4  
 Istnieją następujące konfiguracje:  

-   **Zawartość nie jest dostępna w preferowanym punkcie dystrybucji**  

-   **Dystrybuuj zawartość tego pakietu do preferowanych punktów dystrybucji** nie jest włączona  

-   **Zezwalaj na powrót**: Niewłączone  

-   **Sposób działania wdrożenia w przypadku wolnej sieci**: Żadnej konfiguracji  


**Szczegóły:**  

1.  Klient wysyła żądanie zawartości do punktu zarządzania.  

2.  Lista lokalizacji zawartości jest zwracana do klienta z punktu zarządzania z preferowanymi punktami dystrybucji z zawartością. Nie ma żadnych punktów dystrybucji na liście.  

3.  Klient nie powiedzie się i zostanie wyświetlony komunikat **nie ma dostępnej zawartości** i przechodzi do trybu ponawiania próby. Żądanie nowej zawartości jest uruchamiany co godzinę.  

## <a name="scenario-5"></a>W scenariuszu 5  
 Istnieją następujące konfiguracje:  

-   **Zawartość nie jest dostępna w preferowanym punkcie dystrybucji**  

-   **Dystrybuuj zawartość tego pakietu do preferowanych punktów dystrybucji** nie jest włączona  

-   **Zezwalaj na powrót**: Włączono  

-   **Sposób działania wdrożenia w przypadku wolnej sieci**: Nie pobieraj zawartości  


**Szczegóły:**  

1.  Klient wysyła żądanie zawartości do punktu zarządzania. Klient dołącza flagę żądanie, która wskazuje, że rezerwowe punkty dystrybucji są dozwolone.  

2.  Lista lokalizacji zawartości jest zwracana do klienta z punktu zarządzania z preferowanymi punktami dystrybucji i rezerwowe punkty dystrybucji z zawartością. Nie ma żadnych preferowanych punktów dystrybucji z zawartością, ale ma co najmniej jeden rezerwowy punkt dystrybucji zawartości.  

3.  Zawartość nie jest pobierana, ponieważ właściwość wdrożenia określająca, kiedy klient ma korzystać z rezerwowego punktu dystrybucji jest ustawiona na **nie pobieraj zawartości** (który jest używany, gdy klient nawiąże rezerwowe uzyskać zawartość). Klient nie powiedzie się i zostanie wyświetlony komunikat **nie ma dostępnej zawartości** i przechodzi do trybu ponawiania próby. Klient wysyła żądanie nowej zawartości co godzinę.  

## <a name="scenario-6"></a>Scenariusz 6  
 Istnieją następujące konfiguracje:  

-   **Zawartość nie jest dostępna w preferowanym punkcie dystrybucji**  

-   **Dystrybuuj zawartość tego pakietu do preferowanych punktów dystrybucji** nie jest włączona  

-   **Zezwalaj na powrót**: Włączono  

-   **Sposób działania wdrożenia w przypadku wolnej sieci**: Pobierz i zainstaluj zawartość  


**Szczegóły:**  

1.  Klient wysyła żądanie zawartości do punktu zarządzania. Klient dołącza flagę żądania, który wskazuje, że rezerwowe punkty dystrybucji są włączone.  

2.  Lista lokalizacji zawartości jest zwracana do klienta z punktu zarządzania z preferowanymi punktami dystrybucji i rezerwowe punkty dystrybucji z zawartością. Istnieją preferowane punkty dystrybucji z zawartością, ale co najmniej jeden rezerwowy punkt dystrybucji z zawartością.  

3.  Zawartość jest pobierana z rezerwowego punktu dystrybucji na liście, ponieważ właściwość wdrożenia określająca, kiedy klient ma korzystać z rezerwowego punktu dystrybucji jest ustawiona na **Pobierz i zainstaluj zawartość**.  

## <a name="scenario-7"></a>Scenariusz 7  
 Istnieją następujące konfiguracje:  

-   **Zawartość nie jest dostępna w preferowanym punkcie dystrybucji**  

-   **Dystrybuuj zawartość tego pakietu do preferowanych punktów dystrybucji** jest włączone  

-   **Zezwalaj na powrót**: Niewłączone  

-   **Sposób działania wdrożenia w przypadku wolnej sieci**: Żadnej konfiguracji  


**Szczegóły:**  

1.  Klient wysyła żądanie zawartości do punktu zarządzania.  

2.  Lista lokalizacji zawartości jest zwracana do klienta z punktu zarządzania z preferowanymi punktami dystrybucji z zawartością. Nie istnieją punkty dystrybucji z zawartością.  

3.  Klient nie powiedzie się i zostanie wyświetlony komunikat **nie ma dostępnej zawartości** i przechodzi do trybu ponawiania próby. Żądanie nowej zawartości jest składane co godzinę.  

4.  Punkt zarządzania tworzy dla Menedżera dystrybucji wyzwalacz w celu dystrybucji zawartości do wszystkich preferowanych punktów dystrybucji klienta, który wysłał żądanie zawartości.  

5.  Menedżer dystrybucji dystrybuuje zawartość do wszystkich preferowanych punktów dystrybucji. W większości przypadków zawartość jest pomyślnie wysyłana do preferowanych punktów dystrybucji w ciągu godziny.  

6.  Żądanie nowej zawartości jest inicjowane przez klienta z punktem zarządzania.  

7.  Lista lokalizacji zawartości jest zwracana do klienta z punktu zarządzania z preferowanymi punktami dystrybucji z zawartością. Klient pobiera zawartość z preferowanego punktu dystrybucji na liście.  

## <a name="scenario-8"></a>Scenariusz 8  
 Istnieją następujące konfiguracje:  

-   **Zawartość nie jest dostępna w preferowanym punkcie dystrybucji**  

-   **Dystrybuuj zawartość tego pakietu do preferowanych punktów dystrybucji** jest włączone  

-   **Zezwalaj na powrót**: Włączono  

-   **Sposób działania wdrożenia w przypadku wolnej sieci**: Nie pobieraj zawartości  


**Szczegóły:**  

1.  Klient wysyła żądanie zawartości do punktu zarządzania. Klient dołącza flagę żądanie, która wskazuje, że rezerwowe punkty dystrybucji są dozwolone.  

2.  Lista lokalizacji zawartości jest zwracana do klienta z punktu zarządzania z preferowanymi punktami dystrybucji i rezerwowe punkty dystrybucji z zawartością. Nie ma żadnych preferowanych punktów dystrybucji z zawartością, ale ma co najmniej jeden rezerwowy punkt dystrybucji zawartości.  

3.  Zawartość nie jest pobierana, ponieważ właściwość wdrożenia określająca, kiedy klient ma korzystać z rezerwowego punktu dystrybucji jest ustawiona na **nie pobieraj**. Klient nie powiedzie się i zostanie wyświetlony komunikat **nie ma dostępnej zawartości** i przechodzi do trybu ponawiania próby. Klient wysyła żądanie nowej zawartości co godzinę.  

4.  Punkt zarządzania tworzy dla Menedżera dystrybucji wyzwalacz w celu dystrybucji zawartości do wszystkich preferowanych punktów dystrybucji klienta, który wysłał żądanie zawartości.  

5.  Menedżer dystrybucji dystrybuuje zawartość do wszystkich preferowanych punktów dystrybucji. W większości przypadków zawartość jest pomyślnie wysyłana do preferowanych punktów dystrybucji w ciągu godziny.  

6.  Żądanie nowej zawartości jest inicjowane przez klienta z punktem zarządzania.  

7.  Lista lokalizacji zawartości jest zwracana do klienta z punktu zarządzania z preferowanymi punktami dystrybucji z zawartością.  

8.  Klient pobiera zawartość z preferowanego punktu dystrybucji na liście.  

## <a name="scenario-9"></a>Scenariusz 9  
 Istnieją następujące konfiguracje:  

-   **Zawartość nie jest dostępna w preferowanym punkcie dystrybucji**  

-   **Dystrybuuj zawartość tego pakietu do preferowanych punktów dystrybucji** jest włączone  

-   **Zezwalaj na powrót**: Włączono  

-   **Sposób działania wdrożenia w przypadku wolnej sieci**: Pobierz i zainstaluj zawartość  


**Szczegóły:**  

1.  Klient wysyła żądanie zawartości do punktu zarządzania. Klient dołącza flagę żądanie, która wskazuje, że rezerwowe punkty dystrybucji są dozwolone.  

2.  Lista lokalizacji zawartości jest zwracana do klienta z punktu zarządzania z preferowanymi punktami dystrybucji i rezerwowe punkty dystrybucji z zawartością. Nie ma żadnych preferowanych punktów dystrybucji z zawartością, ale ma co najmniej jeden rezerwowy punkt dystrybucji zawartości.  

3.  Zawartość jest pobierana z rezerwowego punktu dystrybucji na liście, ponieważ właściwość wdrożenia określająca, kiedy klient ma korzystać z rezerwowego punktu dystrybucji jest ustawiona na **Pobierz i zainstaluj zawartość**. To ustawienie wdrożenia umożliwia klienta, które muszą używać rezerwowej lokalizacji zawartości do pobierania zawartości z tej lokalizacji.  

4.  Punkt zarządzania tworzy dla Menedżera dystrybucji wyzwalacz w celu dystrybucji zawartości do wszystkich preferowanych punktów dystrybucji klienta, który wysłał żądanie zawartości.  

5.  Menedżer dystrybucji dystrybuuje zawartość do wszystkich preferowanych punktów dystrybucji, co umożliwia dodatkowych klientów w celu uzyskania zawartości bez korzystania z rezerwowego punktu dystrybucji.  

