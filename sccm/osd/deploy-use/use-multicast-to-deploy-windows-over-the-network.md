---
title: "Wdrażanie systemu Windows za pośrednictwem sieci przy użyciu multiemisji"
titleSuffix: Configuration Manager
description: "Użyj multiemisji w środowisku programu System Center Configuration Manager tak, aby wiele komputerów jednocześnie można pobrać obrazu systemu operacyjnego."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4cafb7fc-380b-41b1-b83e-045aebfb7131
caps.latest.revision: "13"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 00f42e9b29d3140577d27c1f311600fcfa409a81
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="use-multicast-to-deploy-windows-over-the-network-with-system-center-configuration-manager"></a>Wdrażanie systemu Windows za pośrednictwem sieci w programie System Center Configuration Manager przy użyciu multiemisji

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Multiemisja to metoda optymalizacji sieci, którego można używać w środowisku programu System Center Configuration Manager, w których wielu klientów mogą pobierać ten sam obraz systemu operacyjnego, w tym samym czasie. W przypadku multiemisji obraz systemu operacyjnego jest udostępniony w punkcie dystrybucji i może być jednocześnie pobierany z wielu komputerów. Punkt dystrybucji nie musi wysyłać kopii danych do każdego klienta w ramach oddzielnego połączenia.  

 Systemy operacyjne można wdrażać za pośrednictwem sieci przy użyciu multiemisji w następujących scenariuszach wdrażania systemu operacyjnego:  

-   [Odświeżanie istniejącego komputera za pomocą nowej wersji systemu Windows](refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [Instalowanie nowej wersji systemu Windows na nowym komputerze (od zera)](install-new-windows-version-new-computer-bare-metal.md)  

 Wykonaj kroki jednego ze scenariuszy wdrożenia systemu operacyjnego, a następnie użyj poniższych sekcji, aby udostępnić obsługę multiemisji.  

##  <a name="BKMK_Configure"></a> Konfigurowanie punktu dystrybucji w celu obsługi multiemisji  
 Aby użyć multiemisji podczas wdrażania systemu operacyjnego, musisz skonfigurować obsługę multiemisji dla punktu dystrybucji. Aby uzyskać więcej informacji, zobacz [Konfigurowanie punktów dystrybucji do obsługi multiemisji](../get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_DPMulticast).  

## <a name="prepare-an-operating-system-image-for-multicast-deployments"></a>Przygotowywanie obrazu systemu operacyjnego dla wdrożeń za pomocą multiemisji  
 Aby skonfigurować pakiet obrazu systemu operacyjnego w celu obsługi multiemisji, zobacz [przygotować obraz systemu operacyjnego dla wdrożeń multiemisji](../get-started/manage-operating-system-images.md#BKMK_OSImageMulticast).  

##  <a name="BKMK_Deploy"></a> Wdrażanie sekwencji zadań  
 Wdróż system operacyjny w kolekcji docelowej. Aby uzyskać więcej informacji, zobacz [Wdrażanie sekwencji zadań](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS).  
