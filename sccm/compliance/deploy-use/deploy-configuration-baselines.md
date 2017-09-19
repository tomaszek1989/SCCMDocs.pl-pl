---
title: "Wdrażanie linii bazowych konfiguracji | Dokumentacja firmy Microsoft"
description: "Wdrażanie linii bazowych konfiguracji, aby zdefiniować wdrożenia linii bazowej konfiguracji, a także dodać lub usunąć linie bazowe konfiguracji z wdrożenia."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9be8aaf3-075e-4acd-abd2-7459254e16e2
caps.latest.revision: "7"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: b9c46766b953016d852c21317db72b45e23f1ee7
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2017
---
# <a name="how-to-deploy-configuration-baselines-in-system-center-configuration-manager"></a>Jak wdrożyć linie bazowe konfiguracji w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Linie bazowe konfiguracji w programie System Center Configuration Manager należy wdrożyć w co najmniej jednej kolekcji użytkowników lub urządzeń, zanim urządzeń klienckich w tych kolekcjach mogły osiągać zgodność z linią bazową konfiguracji.  

Użyj okna dialogowego **Wdrażanie linii bazowych konfiguracji** , aby zdefiniować wdrożenia linii bazowej konfiguracji, w tym dodać lub usunąć linie bazowe konfiguracji z wdrożenia (oprócz określenia harmonogramu szacowania).  

## <a name="deploy-a-configuration-baseline"></a>Wdrażanie linii bazowej konfiguracji  

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność** > **ustawień zgodności** > **linie bazowe konfiguracji**.  

3.  Na liście **Linie bazowe konfiguracji** wybierz linię bazową konfiguracji, którą chcesz wdrożyć, a następnie na karcie **Narzędzia główne** w grupie **Wdrażanie** kliknij pozycję **Wdróż**.  

4.  W oknie dialogowym **Wdrażanie linii bazowych konfiguracji** wybierz linie bazowe konfiguracji do wdrożenia z listy **Dostępne linie bazowe konfiguracji** . Kliknij pozycję **Dodaj** , aby dodać je do listy **Wybrane linie bazowe konfiguracji** .  

    > [!IMPORTANT]  
    >  Jeśli zmienisz element konfiguracji, który został dodany do wdrożonej linii bazowej konfiguracji, zmodyfikowany element konfiguracji nie będzie oceniany pod względem zgodności do momentu uruchomienia następnej zaplanowanej oceny.  

5.  Podaj następujące informacje dodatkowe:  

    -   **Koryguj niezgodne reguły, jeśli są obsługiwane** — automatycznie rozwiąże problemy z reguł, które są niezgodne dla Instrumentacji zarządzania Windows (WMI), rejestru, skrypty i wszystkich ustawień dla urządzeń przenośnych, które są zarejestrowane przez program Configuration Manager.  

    -   **Zezwalaj na korygowanie poza oknem obsługi** — jeśli okno obsługi zostało skonfigurowane dla kolekcji, w której wdrażasz linię bazową konfiguracji, włącz tę opcję, aby pozwolić na korygowanie wartości przy użyciu ustawień zgodności poza oknem obsługi. Aby uzyskać więcej informacji dotyczących okien obsługi, zobacz [używanie okien obsługi](/sccm/core/clients/manage/collections/use-maintenance-windows).  

6.  **Generuj alert** — konfiguruje alert jest generowany, gdy zgodności linii bazowej konfiguracji jest mniejsza niż określony procent określonej daty i godziny. Możesz również określić, czy chcesz wysyłać alert do programu System Center Operations Manager.  

7.  **Kolekcja** — kliknij pozycję **Przeglądaj** , aby wybrać kolekcję, w której chcesz wdrożyć linię bazową konfiguracji.  

8.  **Określ harmonogram oceny zgodności dla tej linii bazowej konfiguracji** Określ harmonogram oceny linii bazowej konfiguracji wdrożonej na komputerach klienckich. Może to być harmonogram prosty lub niestandardowy.  

    > [!NOTE]  
    >  Jeśli linia bazowa konfiguracji jest wdrażana na komputerze, jej zgodność jest oceniana w ciągu dwóch godzin od zaplanowanej godziny rozpoczęcia. Jeśli jest wdrażana do użytkownika, zgodność będzie oceniana, gdy użytkownik się zaloguje.  

9. Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Wdrażanie linii bazowych konfiguracji** i utworzyć wdrożenie. Aby uzyskać więcej informacji o sposobie monitorowania wdrażania, zobacz [monitorować ustawienia zgodności](/sccm/compliance/deploy-use/monitor-compliance-settings).  
