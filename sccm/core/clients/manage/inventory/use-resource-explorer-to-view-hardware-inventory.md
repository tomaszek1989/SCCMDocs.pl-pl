---
title: "Widok spisu sprzętu | Dokumentacja firmy Microsoft | Eksplorator zasobów"
description: "Użycie Eksploratora zasobów do wyświetlania spisu sprzętu w programie System Center Configuration Manager."
ms.custom: na
ms.date: 01/03/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 375912f5-436d-4315-bdbe-d77afee6c9f3
caps.latest.revision: "7"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: e39fa60a5d215fa1b0a98d4463058497e63a4d4f
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="how-to-use-resource-explorer-to-view-hardware-inventory-in-system-center-configuration-manager"></a>Jak wyświetlać spis sprzętu za pomocą eksploratora zasobów w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Użyj Eksploratora zasobów w programie System Center Configuration Manager, aby wyświetlić informacje dotyczące spisu sprzętu zebrane z klientów w hierarchii.  

> [!NOTE]  
>  W eksploratorze zasobów nie są wyświetlane żadne dane spisu, zanim cykl spisu sprzętu nie zostanie uruchomiony na kliencie, z którym się łączysz.  

 Eksplorator zasobów zawiera następujące sekcje związane ze spisem sprzętu:  

-   **Sprzęt** — zawiera najnowszy spis sprzętu zebrane z urządzenia określonego klienta.  **Stan stacji roboczej** ma godzinę i datę, gdy urządzenie wykonania ostatniego spisu sprzętu.  

-   **Historia sprzętu** — zawiera historię elementów umieszczonych w spisie, które uległy zmianie od czasu ostatniego spisu sprzętu miało miejsce. Każdy element zawiera **bieżącego** węzeł i co najmniej jeden *< data\>*  węzłów. Możesz porównać informacje w węźle bieżącym z jednym z węzłów historycznych, aby odnaleźć elementy, które zostały zmienione.  

    > [!NOTE]  
    >  Configuration Manager przechowuje historię spisu sprzętu przez liczbę dni określoną w **Usuń przestarzałą historię spisu** zadanie obsługi lokacji  

> [!NOTE]  
>  Aby uzyskać informacje o wyświetlaniu spisu sprzętu z klientów z systemami Linux i UNIX, zobacz [Jak monitorować klientów dla serwerów z systemami Linux i UNIX w programie System Center Configuration Manager](../../../../core/clients/manage/monitor-clients-for-linux-and-unix-servers.md).  

### <a name="how-to-run-resource-explorer-from-the-configuration-manager-console"></a>Jak uruchomić eksploratora zasobów z konsoli programu Configuration Manager  

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność** > **urządzeń**, albo otwórz dowolną kolekcję zawierającą urządzenia.  

3.  Wybierz komputer zawierający spis, który chcesz wyświetlić, a następnie na **Home** kartę > **urządzeń** grupy, wybierz **Start** >  **Eksploratora zasobów**.   

4.  Kliknij prawym przyciskiem myszy dowolny element w prawym okienku **Eksploratora zasobów** okna i wybierz polecenie **właściwości** otworzyć *< nazwa elementu\>***właściwości** okno dialogowe, aby wyświetlić zebranych informacji spisu w bardziej czytelnym formacie.  

