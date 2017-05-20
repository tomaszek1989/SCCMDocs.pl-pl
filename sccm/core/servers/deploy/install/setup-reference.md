---
title: "Informacje dotyczące instalacji | Dokumentacja firmy Microsoft"
description: "Przejrzyj to odwołanie ułatwiają przygotowanie do instalacji lokacji programu Configuration Manager lub hierarchii."
ms.custom: na
ms.date: 4/18/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cdb9fb0c-0912-41e4-b427-f40620971763
caps.latest.revision: 22
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 761c3f58f7c57d8f87ee802da37821895062546d
ms.openlocfilehash: 739461a6cca0fd67431093524c1e8158afd80d0f
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="reference-for-system-center-configuration-manager-setup"></a>Dokumentacja instalacji programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Instalacja programu System Center Configuration Manager zawiera łącza do tematów kilka, które są szczegółowo opisane w poniższych sekcjach. Przedstawione tutaj informacje ułatwiają przygotowanie do instalacji lokacji programu Configuration Manager lub hierarchii oraz uprościć niektóre decyzje, które należy wykonać podczas instalacji.  


##  <a name="bkmk_start"></a> Przed rozpoczęciem  
Przed zainstalowaniem nowej lokacji programu Configuration Manager, upewnij się, że zostały sprawdzone następujące informacje, które ułatwiają Ustawianie etapu projektu pomyślnego wdrożenia:  

-   [Podstawowe założenia programu System Center Configuration Manager](../../../../core/understand/fundamentals.md)  
-   [Planowanie infrastruktury programu System Center Configuration Manager](../../../plan-design/network/configure-firewalls-ports-domains.md)  
-   [Przygotowanie do instalacji lokacji programu System Center Configuration Manager](prepare-to-install-sites.md)  

##  <a name="bkmk_assess"></a> Sprawdzanie gotowość serwera  
Przed rozpoczęciem instalacji nowej lokacji, upewnij się, że serwer lokacji i serwerów systemu lokacji zdalnego, który ma być używany dla lokacji (na przykład serwer, który obsługuje bazę danych lokacji) spełniają wszystkie konfiguracje wymagań wstępnych. Te tematy w bibliotece dokumentacji dotyczącej mogą pomóc:  

-   [Obsługiwane konfiguracje dla programu System Center Configuration Manager](../../../../core/plan-design/configs/supported-configurations.md)  
-   [Narzędzie sprawdzania wymagań wstępnych](prerequisite-checker.md)  

##  <a name="bkmk_Addclients"></a> Klienci dla dodatkowych systemów operacyjnych  
Można pobrać oprogramowanie klienckie programu Configuration Manager z Microsoft Download Center dla następujących systemów operacyjnych:  

-   Mac (Apple)  
-   UNIX  
-   Linux  

Użyj następujących łączy do pobrania klientów z wersją programu Configuration Manager można użyć:  

-   Zobacz [programu Microsoft System Center Configuration Manager - klientów dla innych systemów operacyjnych](http://www.microsoft.com/download/details.aspx?id=47719)  

##  <a name="bkmk_usage"></a> Poziomy użycia danych i ustawienia  
Podczas instalowania pierwszej lokacji programu System Center Configuration Manager, Configuration Manager automatycznie instaluje i konfiguruje nowa rola systemu lokacji, **punktem połączenia usługi**, na serwerze lokacji. Punkt połączenia usługi ma te ustawienia domyślne:  

-   **Online** tryb (w trybie offline również jest dostępny)  
-   **Ulepszone** poziom zbierania danych (dwóch innych danych kolekcji, Basic i pełnych, także są dostępne poziomy)  

Gdy rola systemu lokacji punktu połączenia usługi jest w trybie online, Microsoft automatycznie może zbierać informacji diagnostycznych i użycia w Internecie. Zbierane informacje ułatwiają firmie Microsoft realizację następujących celów:  

-   Identyfikowanie i rozwiązywanie problemów  
-   Poprawa jakości produktów i usług firmy Microsoft  
-   Identyfikowanie aktualizacji dla programu Configuration Manager przeznaczonych dla wersji programu Configuration Manager używanej przez użytkownika  

### <a name="levels-of-data-collection"></a>Poziomy zbierania danych  
Zbieranie danych obejmuje następujące trzy poziomy:

-   **Podstawowe** zawiera dane o instalacji i uaktualniania, takie jak liczba lokacji i które funkcje programu Configuration Manager. Żadne dane osobowe są przesyłane.  

-   **Ulepszone** zawiera dane w podstawowych ustawienie poziomu plus go przesyła dane dotyczące hierarchii, jak używać (częstotliwość oraz czas trwania) każdej funkcji i rozszerzone informacje diagnostyczne, takich jak stan pamięci serwera, gdy system lub wystąpi awaria aplikacji. Żadne dane osobowe są przesyłane.  

-   **Pełna** zawiera dane w podstawowe i rozszerzone ustawienia poziomu, a także wysyła zaawansowane informacje diagnostyczne, takie jak pliki systemowe i migawki pamięci. Ta opcja może zawierać informacje osobiste, ale użyjemy tych informacji do identyfikacji lub skontaktować się z Tobą, lub reklamy docelowy dla Ciebie.  

Aby uzyskać więcej informacji, wraz z ujawnieniem informacji zbieranych przez każdy poziom zobacz [diagnostyki i danych użycia programu System Center Configuration Manager](../../../../core/plan-design/diagnostics/diagnostics-and-usage-data.md).  

Aby wyświetlić System Center Configuration Manager Privacy Statement on-line, przejdź do [http://go.microsoft.com/fwlink/?LinkID=626527](http://go.microsoft.com/fwlink/?LinkID=626527).

