---
title: "Zarządzanie danymi konfiguracji | Dokumentacja firmy Microsoft"
description: "Po utworzeniu elementy konfiguracji i linii bazowych w programie System Center Configuration Manager, należy używać innych poleceń, można wykonywać różne akcje."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b48c693c-d2b0-4707-a5dd-fe92172c49fe
caps.latest.revision: 7
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9e939d871e95a3248d8e5d96cb73063a81fd5cf
ms.openlocfilehash: 1a6084834384e695b49a71fe23833049c86f8dbc
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="manage-configuration-data-in-system-center-configuration-manager"></a>Zarządzanie danymi konfiguracji w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Po utworzeniu elementy konfiguracji i linie bazowe konfiguracji w programie System Center Configuration Manager, zostaną udostępnione dodatkowe polecenia ułatwiają wykonywanie różnych czynności.  

## <a name="manage-configuration-items"></a>Zarządzanie elementami konfiguracji  

-   W **zasoby i zgodność** obszaru roboczego, rozwiń węzeł **ustawień zgodności** > **elementy konfiguracji**, wybierz element konfiguracji, aby zarządzać, a następnie wybierz zadanie zarządzania.  

|Zadanie zarządzania|Szczegóły|  
|---------------------|-------------|  
|**Tworzenie podrzędnego elementu konfiguracji**|Otwiera **Kreatora tworzenia podrzędnego elementu konfiguracji** umożliwiającego utworzenie podrzędnego elementu konfiguracji na podstawie wybranego elementu konfiguracji.<br /><br /> Nie można utworzyć podrzędnego elementu konfiguracji na podstawie elementu konfiguracji urządzenia przenośnego.<br /><br /> Aby uzyskać szczegółowe informacje, zobacz [Utwórz podrzędne elementy konfiguracji](../../compliance/deploy-use/create-child-configuration-items.md).|  
|**Historia poprawek**|Otwiera okno dialogowe **Historia poprawek elementu konfiguracji** , w którym można wyświetlać poprzednie wersje wybranego elementu konfiguracji i zarządzać nimi.|  
|**Wyświetlanie definicji XML**|Wyświetla plik definicji XML dla wybranego elementu konfiguracji w nowym oknie. Te informacje mogą być przydatne, gdy użytkownik chce ręcznie tworzyć dane konfiguracji.|  
|**Eksportowanie**|Eksportuje element konfiguracji w formacie pliku cabinet (cab) pod warunkiem, że został on utworzony w danej lokacji. Można następnie zaimportować go do tej samej lub innej lokacji programu Configuration Manager. Dane konfiguracji są konwertowane na skrót DCM.|  
|**Kopiuj**|Tworzy kopię wybranego elementu konfiguracji z wybraną przez Ciebie nazwą. Nowy element konfiguracji nie zachowuje żadnych relacji z oryginalnym elementem konfiguracji. Oznacza to, że zduplikowany element konfiguracji nie będzie dziedziczyć informacji o konfiguracji z oryginalnego elementu konfiguracji.|  
|**Usuwanie**|Otwiera okno dialogowe **Usuwanie elementu konfiguracji** , w którym można przejrzeć wszystkie odwołania do danego elementu konfiguracji.<br /><br /> Aby można było usunąć element konfiguracji, należy usunąć wszystkie odwołania do niego.|  

## <a name="manage-configuration-baselines"></a>Zarządzanie liniami bazowymi konfiguracji  

-   W **zasoby i zgodność** obszaru roboczego, rozwiń węzeł **ustawień zgodności** > **linie bazowe konfiguracji**wybierz linii bazowej konfiguracji do zarządzania, a następnie wybierz zadanie zarządzania.  


|Zadanie zarządzania|Szczegóły|  
|---------------------|-------------|  
|**Pokaż elementy członkowskie**|Wyświetla wszystkie elementy konfiguracji, do których odwołuje się linia bazowa konfiguracji.|  
|**Zaplanuj podsumowanie**|Konfiguruje harmonogram, według której dane wyświetlane w **linie bazowe konfiguracji** węzła w konsoli programu Configuration Manager zostanie zaktualizowany o najnowsze informacje z bazy danych lokacji.|  
|**Uruchom podsumowanie**|Podsumowanie umożliwia odświeżanie danych w węźle **Linie bazowe konfiguracji** przy użyciu najnowszych danych z bazy danych lokacji. Ta akcja może potrwać kilka minut. W celu wyświetlenia w konsoli najnowszych danych czasami trzeba kliknąć pozycję **Odśwież** .|  
|**Wyświetlanie definicji XML**|Wyświetla plik definicji XML dla wybranej linii bazowej konfiguracji w nowym oknie. Te informacje mogą być przydatne, gdy użytkownik chce ręcznie tworzyć dane konfiguracji.|  
|**Włączenie**|Włącza funkcję monitorowania zgodności dla linii bazowej konfiguracji.|  
|**Wyłącz**|Wyłącza linię bazową konfiguracji, aby jej zgodność nie była już oceniana na komputerach klienckich. Linie bazowe konfiguracji odwołujące się do tej linii bazowej konfiguracji również zostaną wyłączone.|  
|**Eksportowanie**|Eksportuje linię bazową konfiguracji w formacie pliku cabinet (cab) pod warunkiem, że została ona utworzona w danej lokacji. Można następnie zaimportować go do tej samej lub innej lokacji programu Configuration Manager. Dane konfiguracji są konwertowane na skrót DCM.<br /><br /> Aby uzyskać informacje o importowaniu danych konfiguracji, zobacz [importuje dane konfiguracji](../../compliance/deploy-use/import-configuration-data.md).|  
|**Kopiuj**|Tworzy kopię wybranej linii bazowej konfiguracji z wybraną przez Ciebie nazwą. Nowa linia bazowa konfiguracji nie zachowuje żadnych relacji z oryginalną linią bazową konfiguracji.|  
|**Usuwanie**|Otwiera okno dialogowe **Usuwanie linii bazowej konfiguracji** , w którym można przejrzeć wszystkie odwołania do danej linii bazowej konfiguracji.<br /><br /> Aby można było usunąć linię bazową konfiguracji, należy usunąć wszystkie odwołania do niej.|  
|**Wdróż**|Otwiera okno dialogowe **Wdrażanie linii bazowej konfiguracji** , w którym można wdrożyć co najmniej jedną linię bazową konfiguracji na urządzeniach w hierarchii.<br /><br /> Aby uzyskać szczegółowe informacje, zobacz [wdrażać linie bazowe konfiguracji](../../compliance/deploy-use/deploy-configuration-baselines.md).|  

