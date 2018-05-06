---
title: Wdrażanie linii bazowych konfiguracji
titleSuffix: Configuration Manager
description: Wdrażanie linii bazowych konfiguracji, aby zdefiniować wdrożenia linii bazowej konfiguracji, a także dodać lub usunąć linie bazowe konfiguracji z wdrożenia.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-compliance
ms.topic: conceptual
ms.assetid: 9be8aaf3-075e-4acd-abd2-7459254e16e2
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: c55382bf1fc377fd7e86f433a0cb92a5240eafa1
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-deploy-configuration-baselines-in-system-center-configuration-manager"></a>Jak wdrożyć linie bazowe konfiguracji w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Linie bazowe konfiguracji w programie System Center Configuration Manager należy wdrożyć w co najmniej jednej kolekcji użytkowników lub urządzeń, zanim urządzeń klienckich w tych kolekcjach mogły osiągać zgodność z linią bazową konfiguracji.  

Użyj **wdrażanie linii bazowych konfiguracji** okno dialogowe, aby zdefiniować wdrożenia linii bazowej konfiguracji, w tym dodać lub usunąć linie bazowe konfiguracji z wdrożenia oprócz określenia harmonogramu szacowania.  

## <a name="deploy-a-configuration-baseline"></a>Wdrażanie linii bazowej konfiguracji  

1.  W konsoli programu Configuration Manager kliknij **zasoby i zgodność** > **ustawień zgodności** > **linie bazowe konfiguracji**.  

3.  W **linie bazowe konfiguracji** listy, wybierz linię bazową konfiguracji, który chcesz wdrożyć, a następnie w **Home** karcie **wdrożenia** kliknij przycisk  **Wdrażanie**.  

4.  W **wdrażanie linii bazowych konfiguracji** oknie dialogowym Wybierz linie bazowe konfiguracji, które mają zostać wdrożone w **dostępne linie bazowe konfiguracji** listy. Kliknij przycisk **Dodaj** je dodać do **wybrane linie bazowe konfiguracji** listy.  

    > [!IMPORTANT]  
    >  Jeśli zmienisz element konfiguracji, który został dodany do linii bazowej konfiguracji wdrożonej zmodyfikowany element konfiguracji nie jest oceniane pod kątem zgodności, do momentu jego następnej zaplanowanej oceny.  

5.  Podaj następujące informacje dodatkowe:  

    -   **Koryguj niezgodne reguły, jeśli są obsługiwane** — automatycznie rozwiąże problemy z wszystkimi regułami określającymi są niezgodne dla Instrumentacji zarządzania Windows (WMI), rejestru, skrypty i wszystkich ustawień dla urządzeń przenośnych, które są zarejestrowane w konfiguracji Menedżer.  

    -   **Zezwalaj na korygowanie poza oknem obsługi** — Jeśli okno obsługi zostało skonfigurowane dla kolekcji, w której wdrażasz linię bazową konfiguracji, Włącz tę opcję, aby pozwolić na korygowanie wartości przy użyciu poza ustawień zgodności okna obsługi. Aby uzyskać więcej informacji dotyczących okien obsługi, zobacz [używanie okien obsługi](/sccm/core/clients/manage/collections/use-maintenance-windows).  

6.  **Generuj alert** — konfiguruje alert jest generowany, gdy zgodności linii bazowej konfiguracji jest mniejsza niż określony procent określonej daty i godziny. Możesz również określić, czy chcesz wysyłać alert do programu System Center Operations Manager.  

7.  **Kolekcja** — kliknij przycisk **Przeglądaj** aby wybrać kolekcję, w której chcesz wdrożyć linię bazową konfiguracji.  

8.  **Określ harmonogram oceny zgodności dla tej linii bazowej konfiguracji** Określ harmonogram oceny linii bazowej konfiguracji wdrożonej na komputerach klienckich. Może to być harmonogram prosty lub niestandardowy.  

    > [!NOTE]  
    >  Jeśli linia bazowa konfiguracji jest wdrażana na komputerze, jej zgodność jest oceniana w ciągu dwóch godzin od zaplanowanej godziny rozpoczęcia. Jeśli jest wdrażana do użytkownika, zgodność będzie oceniana, gdy użytkownik się zaloguje.  

9. Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Wdrażanie linii bazowych konfiguracji** i utworzyć wdrożenie. Aby uzyskać więcej informacji o sposobie monitorowania wdrażania, zobacz [monitorować ustawienia zgodności](/sccm/compliance/deploy-use/monitor-compliance-settings).  
