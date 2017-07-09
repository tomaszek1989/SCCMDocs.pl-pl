---
title: "Użyj programu Software Center wdrażanie systemu Windows za pośrednictwem sieci | Dokumentacja firmy Microsoft"
description: "System operacyjny można wdrożyć do programu Software Center odświeżenie istniejącego komputera przy użyciu nowej wersji systemu Windows lub uaktualnić system Windows do najnowszej wersji."
ms.custom: na
ms.date: 6/16/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 919e3636-53fe-4119-ad14-2d03702b391b
caps.latest.revision: 5
author: mattbriggs
ms.author: mabrigg
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f4c46bfab9b40b29654f4e883817a5508ab25b74
ms.openlocfilehash: 8988409c68b7f69439ed03872c316b2139d25616
ms.contentlocale: pl-pl
ms.lasthandoff: 06/28/2017


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

