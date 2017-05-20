---
title: "Strategii hierarchii źródłowej | Dokumentacja firmy Microsoft"
description: "Skonfiguruj hierarchię źródłową i zebrać dane z lokacji źródłowej, przed skonfigurowaniem zadania migracji programu System Center Configuration Manager."
ms.custom: na
ms.date: 1/3/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4800a800-66c8-4c35-aebe-e413a23790c1
caps.latest.revision: 6
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: cb5f7bf52a53935ca61b0e1b66822919b17d33e2
ms.openlocfilehash: 0619de32f859f512ee1c9f5a9c83ef8d04a256ca
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="plan-a-source-hierarchy-strategy-in-system-center-configuration-manager"></a>Planowanie strategii hierarchii źródłowej w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Przed skonfigurowaniem zadania migracji w środowisku programu System Center Configuration Manager, należy skonfigurować hierarchię źródłową i zebrać dane z co najmniej jednej lokacji źródłowej w tej hierarchii. Użyj następujące sekcje zawierają informacje pomocne podczas konfigurowania hierarchii źródłowych i lokacji źródłowych oraz określania sposobu programu Configuration Manager gromadzi informacje z lokacji źródłowych w hierarchii źródłowej. 

##  <a name="BKMK_Source_Hierarchies"></a> Hierarchie źródłowe  
Hierarchia źródłowa jest hierarchii programu Configuration Manager zawierającej dane, które chcesz migrować. Podczas konfigurowania migracji i określania hierarchii źródłowej, możesz określić lokacji najwyższego poziomu hierarchii źródłowej. Ta lokacja nosi również nazwę lokacji źródłowej. Dodatkowe lokacje, które można migrować danych z hierarchii źródłowej są również nazywane lokacjami źródłowymi.  

-   Podczas konfigurowania zadania migracji do migracji danych z hierarchii źródłowej programu Configuration Manager 2007, należy skonfigurować ją do migracji danych z jednego lub więcej określonych lokacji źródłowych w hierarchii źródłowej.  

-   Podczas konfigurowania zadania migracji migracji danych z hierarchii źródłowej programu System Center 2012 Configuration Manager lub później, wystarczy określić lokację najwyższego poziomu.  

Można skonfigurować tylko jedną hierarchią źródłową jednocześnie.  

-   Po zdefiniowaniu nowej hierarchii źródłowej tej hierarchii automatycznie staje się bieżącą hierarchią źródłową, zastępując poprzednią hierarchię.  

-   Podczas konfigurowania hierarchii źródłowej należy określić lokację najwyższego poziomu hierarchii źródłowej i podaj poświadczenia dla programu Configuration Manager do nawiązania połączenia do dostawcy programu SMS i bazy danych lokacji w tej lokacji źródłowej.  

-   Program Configuration Manager używa tych poświadczeń do uruchamiania zbierania danych w celu uzyskania informacji o obiektach i punktach dystrybucji z lokacji źródłowej.  

-   W ramach procesu zbierania danych identyfikowane są lokacje podrzędne w hierarchii źródłowej.  

-   Jeśli Hierarchia źródłowa jest hierarchią programu Configuration Manager 2007, należy skonfigurować te dodatkowe Lokacje jako Lokacje źródłowe z osobnych poświadczeń dla każdej lokacji źródłowej.  

Mimo że można skonfigurować wiele hierarchii źródłowej w odstępie czasu, migracja będzie aktywna na tylko jedną hierarchią źródłową jednocześnie.  

-   Po skonfigurowaniu dodatkowa Hierarchia źródłowa przed ukończeniem migracji z bieżącej hierarchii źródłowej, Configuration Manager anuluje zadania active migracji i odłoży wszystkie zadania zaplanowane migracji dla bieżącej hierarchii źródłowej.  

-   Nowo skonfigurowana Hierarchia źródłowa stanie się bieżącą hierarchią źródłową i pierwotna Hierarchia źródłowa stanie się nieaktywna.  

-   Można następnie ustawić poświadczenia połączenia, dodatkowe Lokacje źródłowe i zadania migracji dla nowej hierarchii źródłowej.  

Jeśli przywrócenie nieaktywna Hierarchia źródłowa i nie był wcześniej używany **Wyczyść dane migracji**, można wyświetlić wcześniej skonfigurowanych zadań migracji dla tej hierarchii źródłowej. Zanim jednak będzie można kontynuować migrację z tej hierarchii, konieczne będzie ponowne skonfigurowanie poświadczeń w celu nawiązania połączenia z odpowiednimi lokacjami źródłowymi w hierarchii, a następnie ponowne zaplanowanie wszystkich nieukończonych zadań migracji.  

> [!CAUTION]  
>  Jeśli wykonywana jest migracja danych z więcej niż jednej hierarchii źródłowej, każda dodatkowa hierarchia źródłowa musi zawierać unikatowy zestaw kodów lokacji.  

Aby uzyskać więcej informacji o konfigurowaniu hierarchii źródłowej, zobacz [Konfigurowanie hierarchii źródłowych i lokacji źródłowych na potrzeby migracji programu System Center Configuration Manager](../../core/migration/configuring-source-hierarchies-and-source-sites-for-migration.md)  

##  <a name="BKMK_Source_Sites"></a> Lokacje źródłowe  
 Lokacje źródłowe to lokacje w hierarchii źródłowej zawierające dane, które mają zostać poddane migracji. Lokacja najwyższego poziomu w hierarchii źródłowej zawsze stanowi pierwszą lokację źródłową. Kiedy migracja zbiera dane z pierwszej lokacji źródłowej nowej hierarchii źródłowej, odnajduje informacje o dodatkowych lokacjach w tej hierarchii.  

 Kolejne czynności po zakończeniu zbierania danych dotyczących początkowej lokacji źródłowej są zależne od wersji produktu w hierarchii źródłowej.  

### <a name="source-sites-that-run-configuration-manager-2007-sp2"></a>Lokacje źródłowe z programem Configuration Manager 2007 SP2  
 Dane są zbierane z początkowej lokacji źródłowej hierarchii programu Configuration Manager 2007 z dodatkiem SP2, nie trzeba konfigurować dodatkowych lokacji źródłowych przed utworzeniem zadań migracji. Jednak przed przeprowadzeniem migracji danych z dodatkowych lokacji, należy skonfigurować dodatkowe Lokacje jako Lokacje źródłowe, a System Center Configuration Manager musi pomyślnie zebrać dane z tych witryn.  

 Aby zebrać dane z dodatkowych lokacji, indywidualnie skonfigurowaniu każdej lokacji jako lokację źródłową. Wymaga to podania poświadczeń programu System Center Configuration Manager do łączenia się z dostawcą programu SMS i bazy danych lokacji w każdej lokacji źródłowej. Po skonfigurowaniu poświadczeń dla lokacji źródłowej rozpoczyna się proces zbierania danych dla tej lokacji.  

 Podczas konfigurowania dodatkowych lokacji źródłowych w hierarchii źródłowej programu Configuration Manager 2007 z dodatkiem SP2 należy skonfigurować Lokacje źródłowe z góry, co oznacza, że należy skonfigurować Lokacje najniższej warstwy ostatnio. Lokacje źródłowe w gałęzi hierarchii można skonfigurować w dowolnej chwili, ale należy skonfigurować lokację jako lokację źródłową przed skonfigurowaniem jakiejkolwiek jej lokacji podrzędnej jako lokacji źródłowej.  

> [!NOTE]  
>  Tylko Lokacje główne w hierarchii programu Configuration Manager 2007 z dodatkiem SP2 są obsługiwane dla migracji.  

### <a name="source-sites-that-run-system-center-2012-configuration-manager-or-later"></a>Źródło lokacji z Uruchom System Center 2012 Configuration Manager lub nowszy  
 Dane są zbierane z początkowej lokacji źródłowej programu System Center 2012 Configuration Manager lub nowszego hierarchii, nie trzeba skonfigurować dodatkowe Lokacje źródłowe w tej hierarchii źródłowej. Jest to spowodowane w przeciwieństwie do programu Configuration Manager 2007, te wersje programu Configuration Manager używają udostępnionej bazy danych i udostępnionej bazy danych umożliwia identyfikację i następnie przeprowadzenie migracji wszystkich dostępnych obiektów z początkowej lokacji źródłowej.  

 Podczas konfigurowania kont dostępu do zbierania danych może być konieczne przyznanie **konto dostawcy programu SMS lokacji źródłowej** dostęp do wielu komputerów w hierarchii źródłowej. Może to być pożądane, gdy lokacja źródłowa obsługuje wiele wystąpień dostawcy programu SMS, z których każde znajduje się na innym komputerze. Kiedy rozpoczyna się zbieranie danych, lokacja najwyższego poziomu w hierarchii docelowej kontaktuje się z lokacją najwyższego poziomu w hierarchii źródłowej, aby zidentyfikować lokalizacje dostawcy programu SMS dla tej lokacji. Identyfikowane jest tylko pierwsze wystąpienie dostawcy programu SMS. Jeśli proces zbierania danych nie może uzyskać dostępu do dostawcy programu SMS w zidentyfikowanej lokalizacji, proces kończy się niepowodzeniem i nie podejmuje próby połączenia z dodatkowymi komputerami z innym wystąpieniem dostawcy programu SMS dla danej lokacji.  

##  <a name="BKMK_Data_Gathering"></a> Gromadzenie danych  
 Natychmiast po określeniu hierarchii źródłowej, skonfigurować poświadczenia dla każdej dodatkowej lokacji źródłowej w hierarchii źródłowej lub udostępnieniu punktów dystrybucji dla lokacji źródłowej programu Configuration Manager rozpoczyna zbieranie danych z lokacji źródłowej.  

 Proces zbierania danych jest następnie powtarzany zgodnie z prostym harmonogramem, aby zachować synchronizację ze wszystkimi zmianami danych w lokacji źródłowej. Domyślnie ten proces jest powtarzany co cztery godziny. Harmonogram tego cyklu można zmienić, edytując **właściwości** lokacji źródłowej. Początkowy proces zbierania danych musi przejrzeć wszystkie obiekty w bazie danych programu Configuration Manager i może zająć dużo czasu na zakończenie. Kolejne procesy zbierania danych identyfikują tylko zmiany w danych, przez co zostają ukończone szybciej.  

 Aby zebrać dane, lokacja najwyższego poziomu w hierarchii docelowej łączy się z dostawcą programu SMS i bazą danych lokacji źródłowej, aby pobrać listę obiektów i punktów dystrybucji. Te połączenia używają kont dostępu lokacji źródłowej. Aby uzyskać informacje o konfiguracjach wymaganych w celu zbierania danych, zobacz [wymagania wstępne dotyczące migracji w programie System Center Configuration Manager](../../core/migration/prerequisites-for-migration.md).  

 Można uruchomić i zatrzymać procesu zbierania przy użyciu danych **Zbierz dane teraz** i **Zatrzymaj zbieranie danych** w konsoli programu Configuration Manager.  

 Po użyciu **Zatrzymaj zbieranie danych** dla lokacji źródłowej z jakiegokolwiek powodu, należy ponownie skonfigurować poświadczenia dla lokacji, zanim będzie możliwe dalsze zbieranie danych z tej lokacji ponownie. Do momentu ponownego skonfigurowania lokacji źródłowej, Menedżer konfiguracji nie może zidentyfikować nowych obiektów ani zmian do wcześniej migrowanych obiektów w tej lokacji.  

> [!NOTE]  
>  Przed rozszerzeniem autonomicznej lokacji głównej do hierarchii z centralną lokacją administracyjną, należy zatrzymać wszystkie zbierania danych. Można ponownie skonfigurować zbieranie po rozszerzeniu lokacji danych.  

### <a name="gather-data-now"></a>Zbierz dane teraz  
 Po wykonaniu początkowego zbierania danych dla lokacji ten proces jest powtarzany, aby zidentyfikować obiekty zaktualizowane od ostatniego cyklu zbierania danych. Można również użyć **Zbierz dane teraz** akcji w konsoli programu Configuration Manager, aby natychmiast uruchomić proces i zresetować czas rozpoczęcia następnego cyklu.  

 Po pomyślnym zakończeniu procesu zbierania danych dla lokacji źródłowej można udostępnić punkty dystrybucji z lokacji źródłowej i skonfigurować zadania migracji danych z lokacji. Zbieranie danych to powtarzalny proces migracji i nadal do momentu zmiany hierarchii źródłowej lub użycia **Zatrzymaj zbieranie danych** zakończenia procesu zbierania danych dla tej lokacji.  

### <a name="stop-gathering-data"></a>Zatrzymaj zbieranie danych  
 Można użyć **Zatrzymaj zbieranie danych** aby zakończyć proces zbierania danych dla lokacji źródłowej gdy nie są już potrzebne Configuration Manager, aby identyfikować nowych lub zmienionych obiektów w tej lokacji. Ta akcja uniemożliwia także programu Configuration Manager oferowanie klientom w hierarchii docelowej współużytkowanych punktów dystrybucji ze źródła jako lokalizacje zawartości dla zawartości poddanej migracji.  

 Aby zatrzymać zbieranie danych z każdej lokacji źródłowej, należy uruchomić **Zatrzymaj zbieranie danych** w lokacjach źródłowych najniższej warstwy, a następnie powtórz ten proces w każdej lokacji nadrzędnej. Ostatnią lokacją, w której należy zatrzymać gromadzenie danych, jest lokacja najwyższego poziomu hierarchii źródłowej. Przed zatrzymaniem zbierania danych w lokacji nadrzędnej należy wykonać tę akcję w każdej lokacji podrzędnej. Najczęściej gromadzenie danych zatrzymuje się dopiero w momencie gotowości do ukończenia procesu migracji.  

 Po zatrzymaniu zbierania danych dla lokacji źródłowej, wcześniej zebrane informacje o obiektach i kolekcjach z tej lokacji pozostają dostępne do użycia podczas konfigurowania nowych zadań migracji. Jednak nie są widoczne żadne nowe obiekty ani kolekcje, ani nie możesz zobaczyć zmiany wprowadzone w istniejących obiektach. Jeśli lokacja źródłowa zostanie ponownie skonfigurowana i rozpocznie się zbieranie danych, zostaną wyświetlone informacje o obiektach wcześniej poddanych migracji i ich stan.  

