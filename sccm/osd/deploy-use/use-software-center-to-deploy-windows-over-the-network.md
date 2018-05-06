---
title: Wdrażanie systemu Windows za pośrednictwem sieci przy użyciu programu Software Center
titleSuffix: Configuration Manager
description: System operacyjny można wdrożyć do programu Software Center odświeżenie istniejącego komputera przy użyciu nowej wersji systemu Windows lub uaktualnić system Windows do najnowszej wersji.
ms.date: 6/16/2017
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: conceptual
ms.assetid: 919e3636-53fe-4119-ad14-2d03702b391b
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 3fd4853a35c4bfa1112e61286add1e1f458e8b6f
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="use-software-center-to-deploy-windows-over-the-network-with-system-center-configuration-manager"></a>Wdrażanie systemu Windows za pośrednictwem sieci przy użyciu programu Software Center i System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Użytkownik może utworzyć sekwencję zadań, która instaluje system operacyjny w System Center Configuration Manager dostępne w programie Software Center. Może wdrożyć system operacyjny do programu Software Center w następujących scenariuszach wdrażania systemu operacyjnego:

-   [Odświeżanie istniejącego komputera za pomocą nowej wersji systemu Windows](refresh-an-existing-computer-with-a-new-version-of-windows.md)

-   [Uaktualnianie systemu Windows do najnowszej wersji](upgrade-windows-to-the-latest-version.md)

Wykonaj kroki jednego ze scenariuszy wdrażania systemu operacyjnego. Następnie użyj poniższych sekcjach do przygotowania do wdrożeń dostępnych w programie Software Center.

## <a name="configure-deployment-settings"></a>Konfigurowanie ustawień wdrażania  
Aby udostępnić wdrożenie systemu operacyjnego w programie Software Center, należy skonfigurować wdrożenie. Można skonfigurować wdrożenie w **ustawienia wdrażania** strony Kreatora wdrażania oprogramowania lub **ustawienia wdrażania** we właściwościach wdrożenia. Dla ustawienia **Udostępnij dla następujących** wybierz wartość **Tylko klienci programu Configuration Manager** lub **Klienci programu Configuration Manager, nośniki i PXE**. Po systemie wdraża system operacyjny, system operacyjny będzie wyświetlany w programie Software Center dla członków kolekcji docelowej.

##  <a name="BKMK_Deploy"></a> Wdrażanie sekwencji zadań na komputerach  
Wdróż system operacyjny w kolekcji docelowej. Aby uzyskać więcej informacji, zobacz [Wdrażanie sekwencji zadań](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS). Podczas wdrażania systemów operacyjnych w programie Software Center można skonfigurować, czy wdrożenie jest wymagane, czy dostępne.

-   **Wdrożenie wymagane**: Wymagane wdrożenia udostępnienia systemu operacyjnego w programie Software Center, ale jego zostanie uruchomiony automatycznie zgodnie ze skonfigurowanym harmonogramem przypisywania.

-   **Wdrożenie dostępne**: System operacyjny będzie dostępny w programie Software Center i użytkownik może go zainstalować na żądanie.
