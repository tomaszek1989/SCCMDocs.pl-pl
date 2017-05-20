---
title: "Wdrażać linie bazowe konfiguracji | Dokumentacja firmy Microsoft"
description: "Wdrażania linii bazowych konfiguracji do definiowania wdrożenia linii bazowej konfiguracji, a także dodawanie lub usuwanie linii bazowych konfiguracji wdrożenia."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9be8aaf3-075e-4acd-abd2-7459254e16e2
caps.latest.revision: 7
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9e939d871e95a3248d8e5d96cb73063a81fd5cf
ms.openlocfilehash: 9c9e6b7780c7c10c20a60dbbbf506e916031eb88
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-deploy-configuration-baselines-in-system-center-configuration-manager"></a>Jak wdrażać linie bazowe konfiguracji w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Linie bazowe konfiguracji w programie System Center Configuration Manager należy wdrożyć do jednej lub kilku kolekcji użytkowników lub urządzeń przed urządzeń klienckich w tych kolekcjach można ocenić ich zgodność z linią bazową konfiguracji.  

Użyj okna dialogowego **Wdrażanie linii bazowych konfiguracji** , aby zdefiniować wdrożenia linii bazowej konfiguracji, w tym dodać lub usunąć linie bazowe konfiguracji z wdrożenia (oprócz określenia harmonogramu szacowania).  

## <a name="deploy-a-configuration-baseline"></a>Wdrażanie linii bazowej konfiguracji  

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność** > **ustawień zgodności** > **linie bazowe konfiguracji**.  

3.  Na liście **Linie bazowe konfiguracji** wybierz linię bazową konfiguracji, którą chcesz wdrożyć, a następnie na karcie **Narzędzia główne** w grupie **Wdrażanie** kliknij pozycję **Wdróż**.  

4.  W oknie dialogowym **Wdrażanie linii bazowych konfiguracji** wybierz linie bazowe konfiguracji do wdrożenia z listy **Dostępne linie bazowe konfiguracji** . Kliknij pozycję **Dodaj** , aby dodać je do listy **Wybrane linie bazowe konfiguracji** .  

    > [!IMPORTANT]  
    >  Jeśli zmienisz element konfiguracji, który został dodany do wdrożonej linii bazowej konfiguracji, zmodyfikowany element konfiguracji nie będzie oceniany pod względem zgodności do momentu uruchomienia następnej zaplanowanej oceny.  

5.  Podaj następujące informacje dodatkowe:  

    -   **Koryguj niezgodne reguły, jeśli są obsługiwane** — automatycznie koryguje wszystkich reguł, które są niezgodne dla Instrumentacji zarządzania Windows (WMI), rejestru, skrypty i wszystkich ustawień dla urządzeń przenośnych, które są zarejestrowane przez program Configuration Manager.  

    -   **Zezwalaj na korygowanie poza oknem obsługi** — jeśli okno obsługi zostało skonfigurowane dla kolekcji, w której wdrażasz linię bazową konfiguracji, włącz tę opcję, aby pozwolić na korygowanie wartości przy użyciu ustawień zgodności poza oknem obsługi. Aby uzyskać więcej informacji dotyczących okien obsługi, zobacz [sposobu używania okien obsługi](/sccm/core/clients/manage/collections/use-maintenance-windows).  

6.  **Generowanie alertu** — konfiguruje alert jest generowany, gdy zgodności podstawy konfiguracji jest mniejsza niż określony procent określonej daty i godziny. Możesz również określić, czy chcesz wysyłać alert do programu System Center Operations Manager.  

7.  **Kolekcja** — kliknij pozycję **Przeglądaj** , aby wybrać kolekcję, w której chcesz wdrożyć linię bazową konfiguracji.  

8.  **Określ harmonogram oceny zgodności dla tej linii bazowej konfiguracji** określa harmonogram oceny linii bazowej konfiguracji wdrożonych na komputerach klienckich. Może to być harmonogram prosty lub niestandardowy.  

    > [!NOTE]  
    >  Jeśli linia bazowa konfiguracji jest wdrażana na komputerze, jej zgodność jest oceniana w ciągu dwóch godzin od zaplanowanej godziny rozpoczęcia. Jeśli jest wdrażana do użytkownika, zgodność będzie oceniana, gdy użytkownik się zaloguje.  

9. Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Wdrażanie linii bazowych konfiguracji** i utworzyć wdrożenie. Aby uzyskać więcej informacji o sposobie monitorowania wdrażania, zobacz [monitorowania ustawień zgodności](/sccm/compliance/deploy-use/monitor-compliance-settings).  

