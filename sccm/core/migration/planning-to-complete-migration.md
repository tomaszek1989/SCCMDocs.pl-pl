---
title: Kończenie migracji
titleSuffix: Configuration Manager
description: Dowiedz się, jak zakończyć migracji do hierarchii docelowej programu System Center Configuration Manager po hierarchii źródłowej nie ma już danych.
ms.date: 1/12/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: f4854b50-2e8c-414c-a872-9579554dca98
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: b9bdffc9271b1e59bbe459dffc0e3c69578a4711
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="plan-to-complete-migration-in-system-center-configuration-manager"></a>Planowanie kończenia migracji w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Z programem System Center Configuration Manager można ukończyć proces migracji w przypadku hierarchii źródłowej nie ma już dane, które chcesz zmigrować do hierarchii docelowej. Ukończenie migracji obejmuje następujące ogólne czynności:  

-   Upewnij się, że migrację danych, które są wymagane. Przed ukończeniem migracji z hierarchii źródłowej, upewnij się, że zostały pomyślnie zmigrowane wszystkie zasoby z hierarchii źródłowej, która jest wymagana w hierarchii docelowej. Może to obejmować danych i klientów.  

-   Zatrzymaj zbieranie danych z lokacji źródłowych. Aby ukończyć migrację z hierarchii źródłowej, musisz najpierw zatrzymać zbieranie danych z lokacji źródłowych.  

-   Wyczyść dane migracji. Po zatrzymaniu zbierania danych ze wszystkich lokacji źródłowych w hierarchii źródłowej, możesz usunąć dane dotyczące migracji procesu i hierarchii źródłowej z bazy danych hierarchii docelowej.  

-   Zlikwidowanie hierarchii źródłowej. Po zakończeniu migracji z hierarchii źródłowej i hierarchia zawiera już zasobów, którymi zarządzasz, można zlikwidować Lokacje w hierarchii źródłowej i usunąć powiązaną infrastrukturę ze środowiska. Aby uzyskać informacje o sposobach likwidowania lokacji i hierarchii źródłowych zajrzyj do dokumentacji danej wersji programu Configuration Manager.  

Użyj sekcje ułatwią planowanie kończenia migracji z hierarchii źródłowej przez zatrzymanie gromadzenia danych i wyczyszczenie danych migracji:  

-   [Planowanie zatrzymywania gromadzenia danych](#Plan_to_Stop_Data_Gath)  

-   [Planowanie czyszczenia danych migracji](#Plan_to_clean_up)  

##  <a name="Plan_to_Stop_Data_Gath"></a> Planowanie zatrzymywania gromadzenia danych  
 Przed ukończeniem migracji i wyczyść dane migracji należy zatrzymać zbieranie danych z każdej lokacji źródłowej w hierarchii źródłowej. Aby zatrzymać zbieranie danych z każdej lokacji źródłowej, należy wykonać **Zatrzymaj zbieranie danych** poleceń w lokacjach źródłowych najniższej warstwy, a następnie powtórzyć ten proces w każdej lokacji nadrzędnej. Ostatnią lokacją, w której należy zatrzymać gromadzenie danych, jest lokacja najwyższego poziomu hierarchii źródłowej. Należy zatrzymać zbieranie w każdej lokacji podrzędnej przed wykonaniem tego polecenia w lokacji nadrzędnej danych. Zazwyczaj można tylko zatrzymać zbieranie danych, gdy wszystko będzie gotowe zakończyć proces migracji.  

 Po zatrzymaniu zbierania danych z lokacji źródłowej, współużytkowane punkty dystrybucji w tej lokacji nie są już dostępne jako lokalizacje zawartości dla klientów w hierarchii docelowej. W związku z tym upewnij się, że wszelka zawartość zmigrowana, która klientów w hierarchii docelowej wymaga dostępu do jest nadal dostępny przy użyciu jednej z następujących opcji:  

-   W hierarchii docelowej dystrybuować zawartość do co najmniej jednego punktu dystrybucji.  

-   Przed zatrzymaniem zbierania danych z lokacji źródłowej, należy uaktualnić lub ponownie przypisać współużytkowane punkty dystrybucji z zawartością wymagane. Więcej informacji o uaktualnienie lub ponowne przypisywanie współużytkowanych punktów dystrybucji znajduje się w stosownych częściach [Planowanie strategii migracji wdrożenia zawartości w programie System Center Configuration Manager](../../core/migration/planning-a-content-deployment-migration-strategy.md).  

Po zatrzymaniu zbierania danych z każdej lokacji źródłowej w hierarchii źródłowej, możesz wyczyścić dane migracji. Do momentu wyczyszczenia danych migracji każde zadanie migracji, które zostało uruchomione lub jest zaplanowane do uruchomienia, pozostaje dostępne w konsoli programu Configuration Manager.  

Aby uzyskać więcej informacji o lokacjach źródłowych i gromadzeniu danych, zobacz [Planowanie strategii hierarchii źródłowej w programie System Center Configuration Manager](../../core/migration/planning-a-source-hierarchy-strategy.md).  

##  <a name="Plan_to_clean_up"></a> Planowanie czyszczenia danych migracji  
 Ostatni krok wymagany do zakończenia migracji jest czyszczenie danych migracji. Można użyć **Wyczyść dane migracji** po zatrzymaniu gromadzenia danych dla każdej lokacji źródłowej w hierarchii źródłowej. To opcjonalne działanie powoduje usunięcie danych dotyczących bieżącej hierarchii źródłowej z bazy danych hierarchii docelowej.  

 Czyszczenie danych migracji większość danych dotyczących migracji usunięcie z bazy danych hierarchii docelowej. Niemniej jednak szczegółowe informacje o zmigrowanych obiektach są zachowywane. Dysponując tymi szczegółowymi informacjami, można użyć **migracji** obszaru roboczego do zmiany konfiguracji hierarchii źródłowej, która zawiera dane, które zostały poddane migracji, aby wznowić migrację z tej hierarchii źródłowej, lub aby przejrzeć obiekty i przynależność obiektów, które zostały już poprzednio zmigrowane do lokacji.  
