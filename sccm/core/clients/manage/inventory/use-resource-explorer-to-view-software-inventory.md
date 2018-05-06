---
title: Widok spisu oprogramowania z Eksploratora zasobów
titleSuffix: Configuration Manager
description: Użycie Eksploratora zasobów do wyświetlania spisu oprogramowania w programie System Center Configuration Manager.
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 4b7aa5f6-5ebd-49be-b7f3-4206caadc187
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 2678904b9e5393ea4be557866dee8dfa754ebbc6
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-use-resource-explorer-to-view-software-inventory-in-system-center-configuration-manager"></a>Jak używać Eksploratora zasobów do wyświetlania spisu oprogramowania w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Użyj Eksploratora zasobów w programie System Center Configuration Manager, aby wyświetlić informacje dotyczące spisu oprogramowania zebrane z komputerów w hierarchii.  

> [!NOTE]  
>  Eksplorator zasobów nie będą wyświetlane wszystkie dane spisu, dopóki cykl spisu oprogramowania zostało uruchomione na komputerze klienckim.  

 Eksplorator zasobów zawiera następujące informacje spisu oprogramowania:  

-   **Oprogramowanie**:  

    -   **Zebrane pliki** -pliki, które zostały zebrane podczas tworzenia spisu oprogramowania.  

    -   **Szczegóły plików** — pliki w spisie zasobów podczas spisu oprogramowania, które nie są skojarzone z określonym produktem lub producentem.  

    -   **Ostatnie skanowanie oprogramowania** -Data i godzina ostatniego zebrania spisu i plików oprogramowania dla komputera klienckiego.  

    -   **Szczegółowe informacje o produkcie** -programów, które zostały umieszczone w spisie spisu oprogramowania, pogrupowane według producenta.  

## <a name="to-run-resource-explorer-from-the-configuration-manager-console"></a>Uruchamianie eksploratora zasobów z konsoli programu Configuration Manager  

1.  W konsoli programu Configuration Manager wybierz **zasoby i zgodność**

2.  W **zasoby i zgodność** obszaru roboczego wybierz **urządzeń** albo otwórz dowolną kolekcję zawierającą urządzenia.  

3.  Wybierz komputer zawierający spis, który chcesz wyświetlić, a następnie w **Home** kartę > **urządzeń** grupy, wybierz **Start** > **Eksploratora zasobów**.

4.  Możesz kliknąć prawym przyciskiem myszy dowolny element w prawym okienku okna Eksplorator zasobów i **właściwości** do wyświetlania zebranych informacji spisu w bardziej czytelnym formacie.  
 
