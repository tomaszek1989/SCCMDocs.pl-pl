---
title: Wybierz zakres migracji | Dokumentacja firmy Microsoft
description: "Dowiedz się, które można migrować dane i dane, które nie można dokonać migracji programu System Center Configuration Manager."
ms.custom: na
ms.date: 12/29/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 99222dc8-0e1e-4513-8302-7a1acf671e9b
caps.latest.revision: 6
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d37261c03fddc3d576fcef73fabd7189e4c46d38
ms.openlocfilehash: 9dc5f6c9f58e1fc33b2dc9dd76737ae23af81993
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="determine-whether-to-migrate-data-to-system-center-configuration-manager"></a>Określanie, czy migrować dane do programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Migracja w System Center Configuration Manager udostępnia proces przesyłania danych i konfiguracji, które zostały utworzone z obsługiwanych wersji programu Configuration Manager do nowej hierarchii.  Procesu migracji można użyć do:  

-   Łączenie wielu hierarchii w jeden.  

-   Przenieś danych i konfiguracji z wdrażaniem laboratorium do wdrożenia produkcyjnego.

-   Przenoszenie danych i konfiguracji z poprzedniej wersji programu Configuration Manager, takich jak programu Configuration Manager 2007, nie ma uaktualnienia ścieżki programu System Center Configuration Manager, lub System Center 2012 Configuration Manager (co jest obsługiwana ścieżka uaktualnienia programu System Center Configuration Manager).  

Z wyjątkiem roli systemu lokacji typu punkt dystrybucji oraz komputerów, które obsługują punkty dystrybucji, między hierarchiami nie mogą być udostępniane żadne infrastruktury (w tym lokacje, role systemów lokacji ani komputery obsługujące rolę systemu lokacji), migracje i transfery.  

 Chociaż nie można migrować infrastruktury serwera, można migrować klientów programu Configuration Manager między hierarchiami. Migracja klienta oznacza migrację danych używanych przez klienta z hierarchii źródłowej do hierarchii docelowej, a następnie instalację lub ponowne przypisanie oprogramowania klienta, tak aby klient mógł raportować do nowej hierarchii.

Po zainstalowaniu klienta do nowej hierarchii i przesłaniu jego danych, jego unikatowy identyfikator programu Configuration Manager pomaga skojarzyć poprzednio zmigrowanych danych z każdego komputera klienckiego programu Configuration Manager.  

 Funkcje, które jest zapewniane przez migrację ułatwiają zarządzanie inwestycjami w konfiguracje i wdrożenia podczas pozwala w pełni korzystać z najważniejszych zmian w produkcie pierwszy (które po raz pierwszy wprowadzone w programie System Center 2012 Configuration Manager i następnie kontynuowane w programie System Center Configuration Manager). Te zmiany to między innymi uproszczona hierarchii programu Configuration Manager, która wykorzystuje mniejszą liczbę lokacji i zasobów oraz ulepszone przetwarzanie, który pochodzi z za pomocą macierzystego kodu 64-bitowego uruchamianego na 64-bitowym sprzęcie.  

 Informacje o wersji programu Configuration Manager obsługują migrację, zobacz [wymagania wstępne dotyczące migracji w programie System Center Configuration Manager](../../core/migration/prerequisites-for-migration.md).  

 Poniższe sekcje zawierają informacje ułatwiające planowanie danych, który może lub nie może przeprowadzić migracji:  

-   [Dane, które można migrować programu System Center Configuration Manager](#Can_Migrate)  

-   [Dane, które nie można dokonać migracji programu System Center Configuration Manager](#Cannot_migrate)  

##  <a name="Can_Migrate"></a>Dane, które można migrować programu System Center Configuration Manager  
 Migracja pozwala migrować większość obiektów między obsługiwanej hierarchii programu Configuration Manager. Migrowane wystąpienia niektórych obiektów z obsługiwanej wersji programu Configuration Manager 2007 należy zmodyfikować, aby być zgodna z formatem schematu i obiekt System Center 2012 Configuration Manager.

Te modyfikacje nie wpływają na dane w bazie danych lokacji źródłowej. Obiekty, które są migrowane z obsługiwanej wersji programu System Center 2012 Configuration Manager lub System Center Configuration Manager nie wymagają modyfikacji.  

 Poniżej przedstawiono obiekty, które można migrować zależnie od używanej wersji programu Configuration Manager w hierarchii źródłowej. Niektóre obiekty, takie jak zapytania, nie są migrowane. Aby nadal używać tych obiektów, które nie są migrowane, należy je ponownie utworzyć w nowej hierarchii. Inne obiekty, w tym niektóre dane klienta, są automatycznie ponownie tworzone w nowej hierarchii podczas zarządzania klientami w tej hierarchii.  

### <a name="objects-that-you-can-migrate-from-system-center-2012-configuration-manager-or-system-center-configuration-manager-current-branch"></a>Obiekty, które można migrować z bieżącej gałęzi System Center 2012 Configuration Manager lub System Center Configuration Manager

-   Anonse  

-   Aplikacje dla programu System Center 2012 Configuration Manager i nowszych wersji  

-   Środowisko wirtualne App-V dla programu System Center 2012 Configuration Manager lub nowszy  

-   Dostosowania analizy zasobów  

-   Granice  

-   Kolekcje: Aby zmigrować kolekcje z obsługiwanej wersji programu System Center 2012 Configuration Manager lub System Center Configuration Manager, należy użyć zadania migracji obiektów.  

-   Ustawienia zgodności:  

    -   Linie bazowe konfiguracji  

    -   Elementy konfiguracji  

-   Wdrożenie systemu operacyjnego:  

    -   Obrazy rozruchowe  

    -   Pakiety sterowników  

    -   Sterowniki  

    -   Obrazy  

    -   Pakiety  

    -   Sekwencje zadań  

-   Wyniki wyszukiwania: Zapisane kryteria wyszukiwania  

-   Aktualizacje oprogramowania:  

    -   Wdrożenia  

    -   Pakiety wdrożeniowe  

    -   Szablony  

    -   Listy aktualizacji oprogramowania  

-   Pakiety dystrybucji oprogramowania  

-   Zasady pomiaru użytkowania oprogramowania  

-   Pakiety aplikacji wirtualnych  

### <a name="objects-that-you-can-migrate-from-configuration-manager-2007-sp2"></a>Obiekty, które można migrować z programu Configuration Manager 2007 z dodatkiem SP2

-   Anonse  

-   Aplikacje dla programu System Center 2012 Configuration Manager i nowszych wersji  

-   Środowisko wirtualne App-V dla programu System Center 2012 Configuration Manager lub nowszy  

-   Dostosowania analizy zasobów  

-   Granice  

-   Kolekcje: Kolekcje migracji z obsługiwanej wersji programu Configuration Manager 2007 przy użyciu zadania migracji kolekcji.  

-   Ustawienia zgodności (nazywane w programie Configuration Manager 2007 zarządzaniem wymaganą konfiguracją):  

    -   Linie bazowe konfiguracji  

    -   Elementy konfiguracji  

-   Wdrożenie systemu operacyjnego:  

    -   Obrazy rozruchowe  

    -   Pakiety sterowników  

    -   Sterowniki  

    -   Obrazy  

    -   Pakiety  

    -   Sekwencje zadań  

-   Wyniki wyszukiwania: Foldery wyszukiwania  

-   Aktualizacje oprogramowania:  

    -   Wdrożenia  

    -   Pakiety wdrożeniowe  

    -   Szablony  

    -   Listy aktualizacji oprogramowania  

-   Pakiety dystrybucji oprogramowania  

-   Zasady pomiaru użytkowania oprogramowania  

-   Pakiety aplikacji wirtualnych  

##  <a name="Cannot_migrate"></a>Dane, które nie można dokonać migracji programu System Center Configuration Manager  
 Nie można migrować obiektów następujących typów:  

-   Informacje o udostępnianiu klientów AMT  

-   Pliki klientów, w tym:  

    -   Dane spisu i historii klienta  

    -   Pliki z pamięci podręcznej klienta  

-   Kwerendy  

-   Uprawnienia zabezpieczeń programu Configuration Manager 2007 oraz wystąpienia lokacji i obiektów  

-   Raporty programu Configuration Manager 2007 z programu SQL Server Reporting Services  

-   Raporty sieci web programu Configuration Manager 2007  

-   Raporty programu System Center 2012 Configuration Manager i System Center Configuration Manager  

-   System Center 2012 Configuration Manager i System Center Configuration Manager liczby administracji opartej na rolach:  

    -   Role zabezpieczeń  

    -   Zakresy zabezpieczeń  

