---
title: "Odnajdywanie urządzeń lub użytkowników zasobów | Dokumentacja firmy Microsoft"
description: "Przeczytaj omówienie odnajdywania procesów i odnajdywanie rekordów danych."
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 30844519-ce14-456f-bfb8-4318b578e9f6
caps.latest.revision: 20
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 7b6674f331c82cc7899b8661cf38b9d3022cf21b
ms.openlocfilehash: 647826e9d340d3ef97abab0dba51041a3727dedc
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="run-discovery-for-system-center-configuration-manager"></a>Uruchamianie odnajdywania dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Umożliwia co najmniej jednej metody odnajdywania w programie System Center Configuration Manager znaleźć zasoby urządzeń i użytkowników, którymi można zarządzać. Odnajdywanie umożliwia również określenie infrastruktury sieci w danym środowisku. Istnieje kilka różnych metod, używanej do odnajdywania różnych rzeczy, a każda metoda ma swoje własne konfiguracje i ograniczenia.  

## <a name="overview-of-discovery"></a>Omówienie odnajdywania  
 Odnajdywanie to proces, za pomocą którego program Configuration Manager uczy się rzeczy, którymi można zarządzać. Dostępne są następujące metody odnajdywania:  

-   Odnajdywanie lasu usługi Active Directory  

-   Odnajdywanie grupy usługi Active Directory  

-   Odnajdywanie systemu usługi Active Directory  

-   odnajdywanie użytkownika usługi Active Directory  

-   Odnajdywanie pulsu  

-   Odnajdywanie sieci  

-   Odnajdywanie serwera  

> [!TIP]  
>  Informacje o poszczególnych metodach odnajdywania znajdują się w temacie [Informacje o metodach odnajdywania dla programu System Center Configuration Manager](../../../../core/servers/deploy/configure/about-discovery-methods.md).  
>   
>  Aby uzyskać pomoc przy wyborze metod do użycia i w których lokacjach w hierarchii, zobacz [Wybieranie metod odnajdywania do użycia dla programu System Center Configuration Manager](../../../../core/servers/deploy/configure/select-discovery-methods-to-use.md).  

 Aby użyć większości metod odnajdywania, należy włączyć metodę w lokacji i skonfigurowany do wyszukiwania określonego sieci lub lokalizacji usługi Active Directory. Po uruchomieniu, zapytanie określonej lokalizacji informacje dotyczące urządzeń lub użytkowników, którzy mogą zarządzać programu Configuration Manager. Gdy Metoda odnajdywania pomyślnie wykryje informacje o zasobie, zapisuje te informacje w pliku o nazwie rekord danych odnajdywania (DDR). Ten plik jest następnie przetwarzana przez lokacji głównej lub centralnej administracji. Przetwarzanie pliku DDR tworzy nowy rekord w bazie danych lokacji, zawierający nowe odnalezione zasoby, lub aktualizuje istniejące rekordy o nowe informacje.  

 Niektóre metody odnajdywania może generować duże natężenie ruchu sieciowego i produkują rekordy DDR mogą powodować znaczne użycie zasobów procesora CPU podczas przetwarzania. Dlatego też należy zaplanować używanie tylko metod odnajdywania wymaganych do zrealizowania określonych celów. Możesz zacząć od jednej lub dwóch metod odnajdywania, a następnie w kontrolowany sposób włączyć dodatkowe metody, aby rozszerzyć zakres odnajdywania w środowisku.  

 Po dodaniu informacji dotyczących odnajdywania do bazy danych lokacji, następnie informacje są replikowane do wszystkich lokacji w hierarchii, niezależnie od tego, gdzie zostały odnalezione lub przetworzone. W związku z tym podczas gdy można skonfigurować różne harmonogramy i ustawień dla metody odnajdywania w różnych lokacjach, można uruchamiać metody odnajdywania określonych w jednej lokacji. Zmniejsza użycie przepustowości sieci za pomocą akcji zduplikowane odnajdywania i zmniejsza przetwarzania danych odnajdywania nadmiarowe w wielu lokacjach.  

 Dane odnajdywania służy do tworzenia niestandardowych kolekcje i kwerendy, które logicznie grupują zasoby zadań zarządzania. Na przykład:  

-   Wypychanie instalacji klientów lub uaktualniania.  

-   Wdrażanie zawartości dla użytkowników lub urządzeń.  

-   Wdrażanie ustawień klienta i konfiguracje pokrewne.

##  <a name="BKMK_DDRs"></a>Informacje o rekordach danych odnajdywania  
 Liczba rekordów DDR to pliki tworzone przez metodę odnajdywania. Zawierają one informacje o zasobie, można zarządzać w programie Configuration Manager, takie jak komputerów, użytkowników i w niektórych przypadkach, infrastrukturze sieci. Są przetwarzane w lokacjach głównych lub w centralnych lokacjach administracyjnych. Po wprowadzeniu informacji o zasobie z rekordu DDR do bazy danych, rekord DDR jest usuwany, a informacja replikowana jako dane globalne do wszystkich lokacji w hierarchii.  

 Lokacja, w które następuje przetworzenie rekordu DDR, zależy od informacji jakie zawiera:  

-   Liczba rekordów DDR dla nowo odnalezionych zasobów, które są nie w bazie danych są przetwarzane w lokacji najwyższego poziomu w hierarchii. Lokacja najwyższego poziomu tworzy w bazie danych nowy rekord zasobu i przypisuje mu unikatowy identyfikator. Rekordy DDR są przesyłane za pomocą replikacji opartych na plikach, dopóki nie znajdą się w lokacji najwyższego poziomu.  

-   Rekordy DDR dla poprzednio odnalezionych obiektów są przetwarzane w lokacjach głównych. Podrzędne lokacje główne nie przesyłają rekordów DDR do centralnej lokacji administracyjnej, gdy rekord DDR zawiera informacje o zasobie, który znajduje się w bazie danych.  

-   Lokacje dodatkowe nie przetwarza rekordów DDR i zawsze przesyła je za pomocą replikacji opartych na plikach do ich nadrzędnej lokacji głównej.  

Pliki rekordów DDR mają rozszerzenie ddr i zwykle rozmiar około 1 KB.  

## <a name="get-started-with-discovery"></a>Rozpoczynanie pracy z odnajdywaniem:  
 Przed użyciem konsoli programu Configuration Manager, aby skonfigurować odnajdywanie, należy zapoznać się różnice między metodami, co można zrobić, a w niektórych przypadkach ich ograniczeń.  

Następujące tematy mogą tworzyć foundation, który pomoże Ci przy użyciu metod odnajdywania pomyślnie:  

-   [Metody odnajdowania dla programu System Center Configuration Manager — informacje](../../../../core/servers/deploy/configure/about-discovery-methods.md)  

-   [Wybieranie metod odnajdywania do użycia dla programu System Center Configuration Manager](../../../../core/servers/deploy/configure/select-discovery-methods-to-use.md)  

Następnie, gdy zrozumieć metod, którego chcesz użyć, Znajdź wskazówek, aby skonfigurować każdej metody w [skonfiguruj metody odnajdywania dla programu System Center Configuration Manager](../../../../core/servers/deploy/configure/configure-discovery-methods.md).  

