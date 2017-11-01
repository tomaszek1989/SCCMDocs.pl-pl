---
title: "Informacje dotyczące instalacji"
titleSuffix: Configuration Manager
description: "Przejrzyj to odwołanie, aby pomóc w przygotowaniu do zainstalowania lokacji programu Configuration Manager lub w hierarchii."
ms.custom: na
ms.date: 4/18/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: cdb9fb0c-0912-41e4-b427-f40620971763
caps.latest.revision: "22"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: b7228da1623b5caf1679455e535e282ecf20724a
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="reference-for-system-center-configuration-manager-setup"></a>Dokumentacja instalacji programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Instalator programu System Center Configuration Manager zawiera łącza do różnych tematów, które są szczegółowo opisane w poniższych sekcjach. Informacje przedstawione w tym miejscu może pomóc w przygotowaniu się do zainstalowania lokacji programu Configuration Manager lub hierarchii i pomóc w przygotowaniu dla niektórych decyzje, które należy wykonać podczas instalacji.  


##  <a name="bkmk_start"></a> Przed rozpoczęciem  
Przed zainstalowaniem nowych lokacji programu Configuration Manager, upewnij się, że należy przejrzeć następujące informacje, które ułatwiają przygotowanie się do pomyślnego projektowania wdrożenia:  

-   [Podstawowe informacje na temat programu System Center Configuration Manager](../../../../core/understand/fundamentals.md)  
-   [Planowanie infrastruktury programu System Center Configuration Manager](../../../plan-design/network/configure-firewalls-ports-domains.md)  
-   [Przygotowanie do instalacji lokacji programu System Center Configuration Manager](prepare-to-install-sites.md)  

##  <a name="bkmk_assess"></a> Sprawdzanie gotowość serwera  
Przed rozpoczęciem instalacji nowej lokacji, upewnij się, że serwer lokacji i serwery systemu lokacji zdalnej, które będą używane dla lokacji (na przykład serwer, który jest hostem bazy danych lokacji) spełnia wszystkie wymagania wstępne konfiguracji. Mogą pomóc w tych tematach w bibliotece dokumentacji:  

-   [Obsługiwane konfiguracje programu System Center Configuration Manager](../../../../core/plan-design/configs/supported-configurations.md)  
-   [Narzędzie sprawdzania wymagań wstępnych](prerequisite-checker.md)  

##  <a name="bkmk_Addclients"></a> Klienci dla dodatkowych systemów operacyjnych  
Możesz pobrać oprogramowanie klienckie programu Configuration Manager z Microsoft Download Center dla następujących systemów operacyjnych:  

-   Mac (Apple)  
-   UNIX  
-   Linux  

Użyj następujących łączy do pobrania klientów dla używanej wersji programu Configuration Manager należy użyć:  

-   Zobacz [programu Microsoft System Center Configuration Manager — klienci dla dodatkowych systemów operacyjnych](http://www.microsoft.com/download/details.aspx?id=47719)  

##  <a name="bkmk_usage"></a> Poziomy użycia danych i ustawienia  
Podczas instalowania pierwszej lokacji programu System Center Configuration Manager, Configuration Manager automatycznie instalowana i konfigurowana nowa rola systemu lokacji, **punkt połączenia z usługą**, na serwerze lokacji. Punkt połączenia usługi ma te ustawienia domyślne:  

-   **Online** trybu (tryb offline również jest dostępna)  
-   **Ulepszone** poziom zbierania danych (dwa inne poziomy zbierania danych, podstawowy i pełny, również są dostępne)  

W przypadku roli systemu lokacji punktu połączenia usługi jest w trybie online, Microsoft automatycznie można zbierać informacje diagnostyczne i użycia w Internecie. Zbierane informacje ułatwiają firmie Microsoft realizację następujących celów:  

-   Identyfikowanie i rozwiązywanie problemów  
-   Poprawa jakości produktów i usług firmy Microsoft  
-   Identyfikowanie aktualizacji dla programu Configuration Manager przeznaczonych dla wersji programu Configuration Manager używanej przez użytkownika  

### <a name="levels-of-data-collection"></a>Poziomy zbierania danych  
Zbieranie danych obejmuje następujące trzy poziomy:

-   **Podstawowe** obejmuje dane dotyczące instalacji i uaktualniania, takie jak liczba lokacji oraz włączonych funkcjach programu Configuration Manager, które. Są przesyłane żadne dane osobowe.  

-   **Ulepszone** obejmuje dane poziomu ustawienia podstawowy, oraz jej przesyła dane dotyczące hierarchii, sposobu każdej funkcji jest używana (częstotliwości i czasu używania), a także zaawansowane informacje diagnostyczne, takie jak stan pamięci serwera podczas systemu lub wystąpienia awarii aplikacji. Są przesyłane żadne dane osobowe.  

-   **Pełna** obejmuje dane poziomu ustawień podstawowy i rozszerzony, a także wysyła zaawansowane informacje diagnostyczne, takie jak migawki plików systemu i pamięci. Ta opcja może obejmować dane osobowe, ale nie używamy tych informacji do identyfikacji lub skontaktować się z Tobą, lub do nich reklam docelowej.  

Aby uzyskać więcej informacji, w tym o ujawnianiu informacji zbieranych na każdym poziomie, zobacz [diagnostycznych i danych użycia programu System Center Configuration Manager](../../../../core/plan-design/diagnostics/diagnostics-and-usage-data.md).  

Aby wyświetlić System Center Configuration Manager Privacy Statement online, przejdź do [http://go.microsoft.com/fwlink/?LinkID=626527](http://go.microsoft.com/fwlink/?LinkID=626527).
