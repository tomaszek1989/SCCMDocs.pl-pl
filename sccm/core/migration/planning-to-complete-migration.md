---
title: "Zakończenie migracji | Dokumentacja firmy Microsoft"
description: "Dowiedz się, jak zakończyć migracji do hierarchii docelowej programu System Center Configuration Manager po hierarchii źródłowej nie ma już danych."
ms.custom: na
ms.date: 1/12/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f4854b50-2e8c-414c-a872-9579554dca98
caps.latest.revision: 5
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0f4a10ba7bbe397f05d724141b562b6cd8b78ea8
ms.openlocfilehash: eb1d2e320df02b26423ed4341d5bd1568b9444ad
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="plan-to-complete-migration-in-system-center-configuration-manager"></a>Planowanie ukończenia migracji w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Za pomocą programu System Center Configuration Manager można ukończyć proces migracji po hierarchii źródłowej nie ma już dane, które chcesz migrować do hierarchii docelowej. Ukończenie migracji obejmuje następujące ogólne kroki:  

-   Upewnij się, że ma migracji danych, które są wymagane. Przed ukończeniem migracji z hierarchii źródłowej, upewnij się, że zostały pomyślnie zmigrowane wszystkie zasoby z hierarchii źródłowej wymagane w hierarchii docelowej. Może to obejmować danych i klientów.  

-   Zatrzymaj zbieranie danych z lokacji źródłowych. Aby ukończyć migrację z hierarchii źródłowej, należy najpierw zatrzymać gromadzenia danych z lokacji źródłowych.  

-   Czyszczenie danych migracji. Po zatrzymaniu zbierania danych ze wszystkich lokacji źródłowych w hierarchii źródłowej, można usunąć dane dotyczące procesu migracji i źródła hierarchii z bazy danych hierarchii docelowej.  

-   Zlikwidowanie hierarchii źródłowej. Po zakończeniu migracji z hierarchii źródłowej i hierarchia nie ma już zarządzanych zasobów, można zlikwidować Lokacje w hierarchii źródłowej i usunąć powiązaną z nimi infrastrukturę z danego środowiska. Aby uzyskać informacje o sposobach likwidowania lokacji i hierarchii źródłowych zajrzyj do dokumentacji danej wersji programu Configuration Manager.  

Użyj poniższych sekcjach ułatwiają planowanie ukończenia migracji z hierarchii źródłowej przez zatrzymanie gromadzenia danych i wyczyszczenie danych migracji:  

-   [Planowanie zatrzymywania gromadzenia danych](#Plan_to_Stop_Data_Gath)  

-   [Planowanie czyszczenia danych migracji](#Plan_to_clean_up)  

##  <a name="Plan_to_Stop_Data_Gath"></a>Planowanie zatrzymywania gromadzenia danych  
 Przed ukończeniem migracji i czyszczenia danych migracji należy zatrzymać zbieranie danych z każdej lokacji źródłowej w hierarchii źródłowej. Aby zatrzymać zbieranie danych z każdej lokacji źródłowej, należy wykonać **Zatrzymaj zbieranie danych** poleceń w lokacjach źródłowych najniższej warstwy, a następnie powtórzyć ten proces w każdej lokacji nadrzędnej. Ostatnią lokacją, w której należy zatrzymać gromadzenie danych, jest lokacja najwyższego poziomu hierarchii źródłowej. Należy zatrzymać zbieranie w każdej lokacji podrzędnej przed wykonaniem tego polecenia w lokacji nadrzędnej danych. Zwykle tylko zatrzymaniu zbierania danych, gdy wszystko będzie gotowe do zakończenia procesu migracji.  

 Po zatrzymaniu zbierania danych z lokacji źródłowej, współużytkowanych punktów dystrybucji w tej lokacji nie są już dostępne jako lokalizacje zawartości dla klientów w hierarchii docelowej. W związku z tym upewnij się, że wszelka zawartość zmigrowana, który klienci w hierarchii docelowej wymagają dostępu, pozostaje dostępne przy użyciu jednej z następujących opcji:  

-   W hierarchii docelowej należy rozpowszechnić zawartość do co najmniej jednego punktu dystrybucji.  

-   Przed zatrzymaniem gromadzenia danych z lokacji źródłowej należy uaktualnić lub ponownie przypisać współużytkowane punkty dystrybucji z zawartością wymagane. Więcej o uaktualnienie lub ponowne przypisywanie współużytkowanych punktów dystrybucji znajduje się w odpowiednich sekcjach [Planowanie strategii migracji wdrożenia zawartości w programie System Center Configuration Manager](../../core/migration/planning-a-content-deployment-migration-strategy.md).  

Po zatrzymaniu zbierania danych z każdej lokacji źródłowej w hierarchii źródłowej, możesz wyczyścić dane migracji. Do momentu wyczyszczenia danych migracji każde zadanie migracji, które zostało uruchomione lub jest zaplanowane do uruchomienia, pozostaje dostępne w konsoli programu Configuration Manager.  

Aby uzyskać więcej informacji o lokacjach źródłowych i gromadzeniu danych, zobacz [Planowanie strategii hierarchii źródłowej w programie System Center Configuration Manager](../../core/migration/planning-a-source-hierarchy-strategy.md).  

##  <a name="Plan_to_clean_up"></a>Planowanie czyszczenia danych migracji  
 Ostatnim krokiem wymaganym do zakończenia migracji jest czyszczenie danych migracji. Można użyć **Wyczyść dane migracji** polecenia po zatrzymaniu zbierania danych dla każdej lokacji źródłowej w hierarchii źródłowej. To opcjonalne działanie powoduje usunięcie danych o bieżącej hierarchii źródłowej z bazy danych hierarchii docelowej.  

 Podczas czyszczenia danych migracji większość danych dotyczących migracji jest usuwane z bazy danych hierarchii docelowej. Niemniej jednak szczegółowe informacje o zmigrowanych obiektach są zachowywane. W przypadku informacje te można używać **migracji** obszaru roboczego do zmiany konfiguracji hierarchii źródłowej zawierające dane, które zostały poddane migracji, aby wznowić migrację z tej hierarchii źródłowej lub przejrzeć obiekty i przynależność obiektów, które zostały już poprzednio zmigrowane do lokacji.  

