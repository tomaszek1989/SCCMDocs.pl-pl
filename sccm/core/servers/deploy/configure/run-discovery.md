---
title: "Odnajdywanie zasobów urządzenia i użytkownika | Dokumentacja firmy Microsoft"
description: "Odczytywanie omówienie odnajdywania i odnajdowanie podczas procesu rekordów danych."
ms.custom: na
ms.date: 2/8/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 30844519-ce14-456f-bfb8-4318b578e9f6
caps.latest.revision: "20"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 647826e9d340d3ef97abab0dba51041a3727dedc
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="run-discovery-for-system-center-configuration-manager"></a>Uruchamianie odnajdywania dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Używasz co najmniej jednej metody odnajdywania w programie System Center Configuration Manager można znaleźć zasoby komputerów i użytkowników, którymi można zarządzać. Odnajdywanie umożliwia również identyfikację infrastruktury sieci w Twoim środowisku. Istnieje kilka różnych metod, które umożliwia wykrywanie różnych rzeczy, a każda metoda charakteryzuje się własną konfiguracją i ograniczeniami.  

## <a name="overview-of-discovery"></a>Omówienie odnajdywania  
 Odnajdywanie jest procesem, za pomocą którego programu Configuration Manager poznaje elementy, którymi można zarządzać. Dostępne są następujące metody odnajdywania:  

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
>  Aby uzyskać pomoc przy wyborze metod do zastosowania i w których lokacjach w hierarchii, zobacz [Wybieranie metod odnajdywania do użycia dla programu System Center Configuration Manager](../../../../core/servers/deploy/configure/select-discovery-methods-to-use.md).  

 Aby użyć większości metod odnajdywania, należy włączyć metodę w lokacji i skonfigurowany do wyszukiwania określonej sieci lub lokalizacji usługi Active Directory. Po uruchomieniu kwerendy określonej lokalizacji dla informacji na temat urządzeń lub użytkowników, którzy mogą zarządzać programu Configuration Manager. Jeśli metoda odnajdywania pomyślnie znajdzie informacje o zasobie, umieszcza je w pliku nazywanym rekordem danych odnajdowania (DDR). Ten plik jest następnie przetwarzana przez głównej lub centralnej lokacji administracyjnej. Przetwarzanie pliku DDR tworzy nowy rekord w bazie danych lokacji, zawierający nowe odnalezione zasoby, lub aktualizuje istniejące rekordy o nowe informacje.  

 Niektóre metody odnajdywania mogą generować dużą ilość ruchu sieciowego i spowodować rekordów DDR mogą powodować znaczne użycie zasobów procesora CPU podczas przetwarzania. Dlatego Zaplanuj używanie tylko metod odnajdywania wymaganych do zrealizowania określonych celów. Możesz zacząć od jednej lub dwóch metod odnajdywania, a następnie w kontrolowany sposób włączyć dodatkowe metody, aby rozszerzyć zakres odnajdywania w środowisku.  

 Po dodaniu informacji dotyczących odnajdywania do bazy danych lokacji, następnie informacje są replikowane do wszystkich lokacji w hierarchii, niezależnie od tego, gdzie zostały odnalezione lub przetworzone. W związku z tym podczas można skonfigurować różne harmonogramy i ustawienia metod odnajdywania w różnych lokacjach, daną metodę odnajdywania może działać w jednej lokacji. Zmniejsza użycie przepustowości sieci dzięki akcjom odnajdywania duplikatów i zmniejsza przetwarzania nadmiarowych danych odnajdywania w wielu lokacjach.  

 Dane odnajdywania umożliwia utworzenie kolekcji niestandardowych i zapytań, które logicznie grupują zasoby zadań zarządzania. Na przykład:  

-   Wypychanie klienta instalacji lub uaktualniania.  

-   Wdrażanie zawartości dla użytkowników lub urządzeń.  

-   Wdrażanie ustawień klienta i pokrewnych konfiguracji.

##  <a name="BKMK_DDRs"></a>Informacje o rekordach danych odnajdywania  
 Liczba rekordów DDR to pliki tworzone przez metodę odnajdywania. Zawierają one informacje o zasobie, można zarządzać w programie Configuration Manager, takich jak komputery, użytkowników, a w niektórych przypadkach, infrastrukturze sieci. Są przetwarzane w lokacjach głównych lub w centralnych lokacjach administracyjnych. Po wprowadzeniu informacji o zasobie z rekordu DDR do bazy danych, rekord DDR jest usuwany, a informacja replikowana jako dane globalne do wszystkich lokacji w hierarchii.  

 Lokacja, w które następuje przetworzenie rekordu DDR, zależy od informacji jakie zawiera:  

-   Rekordy DDR dla nowo odnalezionych zasobów, które są nie w bazie danych są przetwarzane w lokacji najwyższego poziomu w hierarchii. Lokacja najwyższego poziomu tworzy nowy rekord zasobu w bazie danych i przypisuje mu unikatowy identyfikator. Rekordy DDR są przesyłane za pomocą replikacji opartej na plikach, aż do osiągnięcia lokacji najwyższego poziomu.  

-   Rekordy DDR dla poprzednio odnalezionych obiektów są przetwarzane w lokacjach głównych. Podrzędne lokacje główne nie przesyłają rekordów DDR do centralnej lokacji administracyjnej, gdy rekord DDR zawiera informacje o zasobie, który znajduje się w bazie danych.  

-   Lokacje dodatkowe nie przetwarzają rekordów DDR i zawsze przesyłają je za pomocą replikacji opartej na plikach do ich nadrzędnej lokacji głównej.  

Pliki rekordów DDR mają rozszerzenie ddr i zwykle rozmiar około 1 KB.  

## <a name="get-started-with-discovery"></a>Rozpoczynanie pracy z odnajdywaniem:  
 Przed rozpoczęciem korzystania z konsoli programu Configuration Manager, aby skonfigurować odnajdywanie, należy poznać różnice między metodami, co można zrobić, a w niektórych przypadkach ich ograniczenia.  

Poniższe tematy można tworzyć podstawę, która ułatwi skuteczne stosowanie metod odnajdywania:  

-   [Metody odnajdywania dla programu System Center Configuration Manager — informacje](../../../../core/servers/deploy/configure/about-discovery-methods.md)  

-   [Wybieranie metod odnajdywania do użycia dla programu System Center Configuration Manager](../../../../core/servers/deploy/configure/select-discovery-methods-to-use.md)  

Następnie, jeśli chcesz użyć metod są zrozumiałe, Znajdź wskazówki dotyczące konfigurowania poszczególnych metod w [skonfiguruj metody odnajdywania dla programu System Center Configuration Manager](../../../../core/servers/deploy/configure/configure-discovery-methods.md).  
