---
title: "Wyświetlanie spisu sprzętu | Dokumenty Microsoft | Eksplorator zasobów"
description: "Eksplorator zasobów umożliwia wyświetlenie spisu sprzętu w programie System Center Configuration Manager."
ms.custom: na
ms.date: 01/03/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 375912f5-436d-4315-bdbe-d77afee6c9f3
caps.latest.revision: 7
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: e39fa60a5d215fa1b0a98d4463058497e63a4d4f
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-use-resource-explorer-to-view-hardware-inventory-in-system-center-configuration-manager"></a>Jak wyświetlać spis sprzętu za pomocą eksploratora zasobów w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Użyj Eksploratora zasobów w programie System Center Configuration Manager do wyświetlania informacji dotyczących zapasów sprzętu, które zostały zebrane od klientów w hierarchii.  

> [!NOTE]  
>  W eksploratorze zasobów nie są wyświetlane żadne dane spisu, zanim cykl spisu sprzętu nie zostanie uruchomiony na kliencie, z którym się łączysz.  

 Eksplorator zasobów zawiera następujące sekcje związanych ze spisem sprzętu:  

-   **Sprzęt** -zawiera najnowsze spisu sprzętu zebrane z urządzenia określonego klienta.  **Stan stacji roboczej** ma godzinę i datę, kiedy urządzenie wykonywana ostatniego spisu sprzętu.  

-   **Historia sprzętu** -zawiera historię spisanych elementów, które uległy zmianie od czasu ostatniej inwentaryzacji sprzętu miało miejsce. Każdy element zawiera **bieżącej** węzła i co najmniej jeden *< data\>*  węzłów. Możesz porównać informacje bieżącego węzła do jednego z węzłów historycznych odnajdywanie elementów, które zostały zmienione.  

    > [!NOTE]  
    >  Menedżer konfiguracji zachowuje historię spisu sprzętu liczbę dni, można określić w **Usuń przestarzałą historię spisu** zadanie obsługi lokacji  

> [!NOTE]  
>  Aby uzyskać informacje o wyświetlaniu spisu sprzętu z klientów z systemami Linux i UNIX, zobacz [Jak monitorować klientów dla serwerów z systemami Linux i UNIX w programie System Center Configuration Manager](../../../../core/clients/manage/monitor-clients-for-linux-and-unix-servers.md).  

### <a name="how-to-run-resource-explorer-from-the-configuration-manager-console"></a>Jak uruchomić eksploratora zasobów z konsoli programu Configuration Manager  

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność** > **urządzeń**, albo otwórz dowolną kolekcję zawierającą urządzenia.  

3.  Wybierz komputer, zawierający magazynu, który chcesz wyświetlić i następnie na **Home** kartę > **urządzeń** grupy, wybierz **Start** >  **Eksploratora zasobów**.   

4.  Kliknij prawym przyciskiem myszy dowolny element w prawym okienku z **Eksploratora zasobów** okna i wybierz polecenie **właściwości** otworzyć *< nazwa elementu\>***właściwości** okno dialogowe, aby wyświetlić informacje zbierane spisu w bardziej czytelnym formacie.  


