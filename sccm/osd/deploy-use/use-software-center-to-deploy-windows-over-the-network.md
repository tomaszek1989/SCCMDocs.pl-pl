---
title: "Korzystanie z Centrum oprogramowania do wdrożenia systemu operacyjnego Windows za pośrednictwem sieci | Dokumentacja firmy Microsoft"
description: "System operacyjny można wdrożyć do Centrum oprogramowania, aby odświeżyć istniejącego komputera z nowej wersji systemu Windows lub uaktualnienie do najnowszej wersji systemu Windows."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 919e3636-53fe-4119-ad14-2d03702b391b
caps.latest.revision: 5
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 4c3ec20396da37d36f908af527f445a7a736e0ac
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="use-software-center-to-deploy-windows-over-the-network-with-system-center-configuration-manager"></a>Wdrażanie systemu Windows za pośrednictwem sieci przy użyciu programu Software Center i System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Sekwencji zadań w celu zainstalowania systemu operacyjnego w programie System Center Configuration Manager mogą być udostępniane w Centrum oprogramowania. System operacyjny można wdrożyć do programu Software Center w następujących scenariuszach wdrażania systemu operacyjnego:  

-   [Odśwież istniejącego komputera z nowej wersji systemu Windows](refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [Uaktualnij do najnowszej wersji systemu Windows](upgrade-windows-to-the-latest-version.md)  

 Wykonaj kroki jednego ze scenariuszy wdrażania systemu operacyjnego, a następnie użyj poniższych sekcji w celu przygotowania do wdrożeń dostępnych w programie Software Center.  

## <a name="configure-deployment-settings"></a>Konfigurowanie ustawień wdrażania  
 Wdrożenie systemu operacyjnego, który ma być dostępny w Centrum oprogramowania, należy należy skonfigurować wdrożenie, aby udostępnić system operacyjny klientów programu Configuration Manager. Tę konfigurację można określić na stronie **Ustawienia wdrożenia** Kreatora wdrażania oprogramowania lub na karcie **Ustawienia wdrożenia** we właściwościach wdrożenia.  Dla ustawienia **Udostępnij dla następujących** wybierz wartość **Tylko klienci programu Configuration Manager** lub **Klienci programu Configuration Manager, nośniki i PXE**. Po wdrożeniu systemu operacyjnego będzie on wyświetlany w Centrum oprogramowania dla elementów członkowskich kolekcji docelowej.  

##  <a name="BKMK_Deploy"></a> Wdrażanie sekwencji zadań na komputerach  
 Wdróż system operacyjny w kolekcji docelowej. Aby uzyskać więcej informacji, zobacz [Wdrażanie sekwencji zadań](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS). Podczas wdrażania systemów operacyjnych w programie Software Center możesz określić, czy wdrożenie jest wymagane, czy dostępne.  

-   **Wdrożenie wymagane**: Wymagane wdrożenia udostępni systemu operacyjnego w programie Software Center, ale zostanie automatycznie uruchomiona zgodnie z harmonogramem skonfigurowanym przypisania.  

-   **Wdrożenie dostępne**: System operacyjny jest dostępny w Centrum oprogramowania i użytkownik może zainstalować ją na żądanie.  

