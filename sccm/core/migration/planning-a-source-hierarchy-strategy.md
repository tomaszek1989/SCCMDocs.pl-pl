---
title: "Strategii hierarchii źródłowej"
titleSuffix: Configuration Manager
description: "Skonfigurować hierarchię źródłową i zebrać dane z lokacji źródłowej przed skonfigurowaniem zadania migracji programu System Center Configuration Manager."
ms.custom: na
ms.date: 1/3/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4800a800-66c8-4c35-aebe-e413a23790c1
caps.latest.revision: "6"
caps.handback.revision: "0"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: f6020cb9a995069c7542200ecb0ce2520ff25bb8
ms.sourcegitcommit: ca9d15dfb1c9eb47ee27ea9b5b39c9f8cdcc0748
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/04/2018
---
# <a name="plan-a-source-hierarchy-strategy-in-system-center-configuration-manager"></a>Planowanie strategii hierarchii źródłowej w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Przed skonfigurowaniem zadania migracji w środowisku programu System Center Configuration Manager, należy skonfigurować hierarchię źródłową i zebrać dane z przynajmniej jednej lokacji źródłowej w tej hierarchii. Skorzystaj z poniższych sekcji pomocne podczas konfigurowania hierarchii źródłowych i lokacji źródłowych oraz określania sposobu programu Configuration Manager zbiera informacje z lokacji źródłowych w hierarchii źródłowej. 

##  <a name="BKMK_Source_Hierarchies"></a> Hierarchie źródłowe  
Hierarchia źródłowa jest hierarchii programu Configuration Manager zawierającej dane, które chcesz migrować. Po skonfigurowaniu migracji i określ hierarchię źródłową, można określić lokacji najwyższego poziomu w hierarchii źródłowej. Ta lokacja nosi również nazwę lokacji źródłowej. Dodatkowe lokacje, które można migrować danych z hierarchii źródłowej są także nazywane lokacjami źródłowymi.  

-   Podczas konfigurowania zadania migracji do migracji danych z hierarchii źródłowej programu Configuration Manager 2007, należy skonfigurować go do migracji danych z jednego lub więcej określonych lokacji źródłowych w hierarchii źródłowej.  

-   Podczas konfigurowania zadania migracji do migracji danych z hierarchii źródłowej, z programem System Center 2012 Configuration Manager lub później, wystarczy określić lokację najwyższego poziomu.  

Można skonfigurować tylko jedną hierarchię źródłową jednocześnie.  

-   Jeśli konfigurujesz nowej hierarchii źródłowej tej hierarchii automatycznie stanie się bieżącą hierarchią źródłową, zastępując poprzednią hierarchię.  

-   Podczas konfigurowania hierarchii źródłowej należy określić lokację najwyższego poziomu hierarchii źródłowej i podaj poświadczenia dla programu Configuration Manager na potrzeby łączenia się z dostawcą programu SMS i bazy danych lokacji w tej lokacji źródłowej.  

-   Configuration Manager używa tych poświadczeń do uruchamiania zbierania danych w celu uzyskania informacji o obiektach i punktach dystrybucji z lokacji źródłowej.  

-   W ramach procesu zbierania danych identyfikowane są lokacje podrzędne w hierarchii źródłowej.  

-   Jeśli Hierarchia źródłowa to hierarchia programu Configuration Manager 2007, można skonfigurować te dodatkowe Lokacje jako Lokacje źródłowe z osobnych poświadczeń dla każdej lokacji źródłowej.  

Mimo że można skonfigurować wielu hierarchii źródłowych kolejno, migracja będzie aktywna na tylko jedną hierarchię źródłową jednocześnie.  

-   Jeśli dodatkowa Hierarchia źródłowa zostanie skonfigurowany przed ukończeniem migracji z bieżącej hierarchii źródłowej, Configuration Manager anuluje wszystkie zadania active migracji i odłoży wszystkie zadania zaplanowane migracji dla bieżącej hierarchii źródłowej.  

-   Nowo skonfigurowana Hierarchia źródłowa stanie się bieżącą hierarchią źródłową, a pierwotna Hierarchia źródłowa będzie nieaktywna.  

-   Konfigurowanie poświadczeń dla połączenia, dodatkowe Lokacje źródłowe i zadania migracji można następnie ustawić dla nowej hierarchii źródłowej.  

Jeśli przywrócenie nieaktywna Hierarchia źródłowa i nie był wcześniej używany **Wyczyść dane migracji**, można wyświetlić wcześniej skonfigurowanych zadań migracji dla tej hierarchii źródłowej. Zanim jednak będzie można kontynuować migrację z tej hierarchii, konieczne będzie ponowne skonfigurowanie poświadczeń w celu nawiązania połączenia z odpowiednimi lokacjami źródłowymi w hierarchii, a następnie ponowne zaplanowanie wszystkich nieukończonych zadań migracji.  

> [!CAUTION]  
>  Jeśli wykonywana jest migracja danych z więcej niż jednej hierarchii źródłowej, każda dodatkowa hierarchia źródłowa musi zawierać unikatowy zestaw kodów lokacji.  

Aby uzyskać więcej informacji o konfigurowaniu hierarchii źródłowej, zobacz [Konfigurowanie hierarchii źródłowych i lokacji źródłowych na potrzeby migracji do programu System Center Configuration Manager](../../core/migration/configuring-source-hierarchies-and-source-sites-for-migration.md)  

##  <a name="BKMK_Source_Sites"></a> Lokacje źródłowe  
 Lokacje źródłowe to lokacje w hierarchii źródłowej zawierające dane, które mają zostać poddane migracji. Lokacja najwyższego poziomu w hierarchii źródłowej zawsze stanowi pierwszą lokację źródłową. Kiedy migracja zbiera dane z pierwszej lokacji źródłowej nowej hierarchii źródłowej, odnajduje informacje o dodatkowych lokacjach w tej hierarchii.  

 Kolejne czynności po zakończeniu zbierania danych dotyczących początkowej lokacji źródłowej są zależne od wersji produktu w hierarchii źródłowej.  

### <a name="source-sites-that-run-configuration-manager-2007-sp2"></a>Lokacje źródłowe z programem Configuration Manager 2007 SP2  
 Dane są zbierane z początkowej lokacji źródłowej hierarchii programu Configuration Manager 2007 z dodatkiem SP2, nie jest konieczne konfigurowanie dodatkowych lokacji źródłowych przed utworzeniem zadań migracji. Jednak przed przeprowadzeniem migracji danych z dodatkowych lokacji, należy skonfigurować dodatkowe Lokacje jako Lokacje źródłowe, a System Center Configuration Manager musi pomyślnie zebrać dane z tych witryn.  

 Aby zebrać dane z dodatkowych lokacji, indywidualnie skonfigurowaniu każdej lokacji jako lokacji źródłowej. Wymaga to podania poświadczeń programu System Center Configuration Manager do łączenia się z dostawcą programu SMS i bazy danych lokacji w każdej lokacji źródłowej. Po skonfigurowaniu poświadczeń dla lokacji źródłowej rozpoczyna się proces zbierania danych dla tej lokacji.  

 Podczas konfigurowania dodatkowych lokacji źródłowych w hierarchii źródłowej programu Configuration Manager 2007 z dodatkiem SP2 należy skonfigurować Lokacje źródłowe z góry w dół, co oznacza, że należy skonfigurować Lokacje najniższej warstwy ostatnio. W dowolnym momencie można skonfigurować Lokacje źródłowe w gałęzi hierarchii, ale należy skonfigurować lokację jako lokację źródłową przed skonfigurowaniem poszczególnych jej lokacji podrzędnych jako lokacji źródłowych.  

> [!NOTE]  
>  Migracja obsługuje tylko Lokacje główne w hierarchii programu Configuration Manager 2007 z dodatkiem SP2.  

### <a name="source-sites-that-run-system-center-2012-configuration-manager-or-later"></a>Lokacje źródłowe z Uruchom System Center 2012 Configuration Manager lub nowszego  
 Dane są zbierane z początkowej lokacji źródłowej programu System Center 2012 Configuration Manager lub nowszego hierarchii, jest konieczne konfigurowanie dodatkowych lokacji źródłowych w tej hierarchii źródłowej. Jest tak, ponieważ w przeciwieństwie do programu Configuration Manager 2007 te wersje programu Configuration Manager używają udostępnionej bazy danych i udostępnionej bazy danych umożliwia określenie, a następnie przeprowadzenie migracji wszystkich dostępnych obiektów z początkowej lokacji źródłowej.  

 Podczas konfigurowania kont dostępu do zbierania danych może być konieczne przyznanie **konto dostawcy programu SMS lokacji źródłowej** dostęp do wielu komputerów w hierarchii źródłowej. Może to być pożądane, gdy lokacja źródłowa obsługuje wiele wystąpień dostawcy programu SMS, z których każde znajduje się na innym komputerze. Kiedy rozpoczyna się zbieranie danych, lokacja najwyższego poziomu w hierarchii docelowej kontaktuje się z lokacją najwyższego poziomu w hierarchii źródłowej, aby zidentyfikować lokalizacje dostawcy programu SMS dla tej lokacji. Identyfikowane jest tylko pierwsze wystąpienie dostawcy programu SMS. Jeśli proces zbierania danych nie może uzyskać dostępu do dostawcy programu SMS w zidentyfikowanej lokalizacji, proces kończy się niepowodzeniem i nie podejmuje próby połączenia z dodatkowymi komputerami z innym wystąpieniem dostawcy programu SMS dla danej lokacji.  

##  <a name="BKMK_Data_Gathering"></a> Gromadzenie danych  
 Natychmiast po określeniu hierarchii źródłowej, Ustawianie poświadczeń dla każdej dodatkowej lokacji źródłowej w hierarchii źródłowej lub udostępnieniu punktów dystrybucji dla lokacji źródłowej programu Configuration Manager rozpoczyna zbieranie danych z lokacji źródłowej.  

 Proces zbierania danych jest następnie powtarzany zgodnie z prostym harmonogramem, aby zachować synchronizację ze wszystkimi zmianami danych w lokacji źródłowej. Domyślnie ten proces jest powtarzany co cztery godziny. Harmonogram tego cyklu można zmienić, edytując **właściwości** lokacji źródłowej. Początkowy proces zbierania danych musi przejrzeć wszystkie obiekty w bazie danych programu Configuration Manager i może zająć dużo czasu, aby zakończyć. Kolejne procesy zbierania danych identyfikują tylko zmiany w danych, przez co zostają ukończone szybciej.  

 Aby zebrać dane, lokacja najwyższego poziomu w hierarchii docelowej łączy się z dostawcą programu SMS i bazą danych lokacji źródłowej, aby pobrać listę obiektów i punktów dystrybucji. Te połączenia używają kont dostępu lokacji źródłowej. Aby uzyskać informacje o konfiguracjach wymaganych w celu zbierania danych, zobacz [wymagania wstępne dotyczące migracji w programie System Center Configuration Manager](../../core/migration/prerequisites-for-migration.md).  

 Można uruchomić i zatrzymać procesu zbierania przy użyciu danych **Zbierz dane teraz** i **Zatrzymaj zbieranie danych** w konsoli programu Configuration Manager.  

 Po użyciu **Zatrzymaj zbieranie danych** dla lokacji źródłowej jakiejkolwiek przyczyny, należy ponownie skonfigurować poświadczenia dla lokacji, zanim będzie możliwe dalsze zbieranie danych z tej lokacji ponownie. Do momentu ponownego skonfigurowania lokacji źródłowej programu Configuration Manager nie może zidentyfikować nowych obiektów ani zmian do wcześniej migrowanych obiektów w tej lokacji.  

> [!NOTE]  
>  Przed rozszerzeniem autonomicznej lokacji głównej do hierarchii z centralną lokacją administracyjną, należy zatrzymać wszystkie zbierania danych. Można ponownie skonfigurować zbieranie po rozszerzeniu lokacji danych.  

### <a name="gather-data-now"></a>Zbierz dane teraz  
 Po wykonaniu początkowego zbierania danych dla lokacji ten proces jest powtarzany, aby zidentyfikować obiekty zaktualizowane od ostatniego cyklu zbierania danych. Można również użyć **Zbierz dane teraz** akcji w konsoli programu Configuration Manager, aby natychmiast uruchomić proces i zresetować czas rozpoczęcia następnego cyklu.  

 Po pomyślnym zakończeniu procesu zbierania danych dla lokacji źródłowej można udostępnić punkty dystrybucji z lokacji źródłowej i skonfigurować zadania migracji danych z lokacji. Zbieranie danych to powtarzalny proces migracji, a nadal do momentu zmiany hierarchii źródłowej lub użycia **Zatrzymaj zbieranie danych** do zakończenia procesu zbierania danych dla tej lokacji.  

### <a name="stop-gathering-data"></a>Zatrzymaj zbieranie danych  
 Można użyć **Zatrzymaj zbieranie danych** aby zakończyć proces zbierania danych dla lokacji źródłowej gdy już program Configuration Manager ma identyfikować nowych lub zmienionych obiektów w tej lokacji. Ta akcja uniemożliwia także programowi Configuration Manager oferowanie klientom w hierarchii docelowej współużytkowanych punktów dystrybucji ze źródła jako bieżących lokalizacji zawartości dla zawartości poddanej migracji.  

 Aby zatrzymać zbieranie danych z każdej lokacji źródłowej, należy uruchomić **Zatrzymaj zbieranie danych** w lokacjach źródłowych najniższej warstwy, a następnie powtórz proces w każdej lokacji nadrzędnej. Ostatnią lokacją, w której należy zatrzymać gromadzenie danych, jest lokacja najwyższego poziomu hierarchii źródłowej. Przed zatrzymaniem zbierania danych w lokacji nadrzędnej należy wykonać tę akcję w każdej lokacji podrzędnej. Najczęściej gromadzenie danych zatrzymuje się dopiero w momencie gotowości do ukończenia procesu migracji.  

 Po zatrzymaniu zbierania danych dla lokacji źródłowej, wcześniej zebrane informacje o obiektach i kolekcjach z tej lokacji pozostają dostępne do użycia podczas konfigurowania nowych zadaniach migracji. Jednak nie ma żadnych nowe obiekty ani kolekcje nie są wyświetlane zmiany dokonane w istniejących obiektach. Jeśli lokacja źródłowa zostanie ponownie skonfigurowana i rozpocznie się zbieranie danych, zostaną wyświetlone informacje o obiektach wcześniej poddanych migracji i ich stan.  
