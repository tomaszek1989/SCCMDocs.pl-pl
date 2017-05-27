---
title: "Użyć multiemisji w celu wdrożenia systemu operacyjnego Windows za pośrednictwem sieci | Dokumentacja firmy Microsoft"
description: "Użyć multiemisji w środowisku programu System Center Configuration Manager, dzięki czemu wiele komputerów jednocześnie można pobrać obrazu systemu operacyjnego."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 4cafb7fc-380b-41b1-b83e-045aebfb7131
caps.latest.revision: 13
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: 55266696aa7340fddda3a57ff90e20222ff665a5
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="use-multicast-to-deploy-windows-over-the-network-with-system-center-configuration-manager"></a>Korzystania z multiemisji do wdrażania systemu Windows za pośrednictwem sieci z System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Multiemisja to metoda optymalizacji sieci, którego można używać w środowisku programu System Center Configuration Manager, w których wielu klientów mogą pobierać ten sam obraz systemu operacyjnego, w tym samym czasie. W przypadku multiemisji obraz systemu operacyjnego jest udostępniony w punkcie dystrybucji i może być jednocześnie pobierany z wielu komputerów. Punkt dystrybucji nie musi wysyłać kopii danych do każdego klienta w ramach oddzielnego połączenia.  

 Systemy operacyjne można wdrażać za pośrednictwem sieci przy użyciu multiemisji w następujących scenariuszach wdrażania systemu operacyjnego:  

-   [Odśwież istniejącego komputera z nowej wersji systemu Windows](refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [Zainstaluj nową wersję systemu Windows na nowym komputerze (od zera)](install-new-windows-version-new-computer-bare-metal.md)  

 Wykonaj kroki jednego ze scenariuszy wdrożenia systemu operacyjnego, a następnie użyj poniższych sekcji, aby udostępnić obsługę multiemisji.  

##  <a name="BKMK_Configure"></a> Konfigurowanie punktu dystrybucji w celu obsługi multiemisji  
 Aby użyć multiemisji podczas wdrażania systemu operacyjnego, musisz skonfigurować obsługę multiemisji dla punktu dystrybucji. Aby uzyskać więcej informacji, zobacz [skonfiguruj punkty dystrybucji do obsługi multiemisji](../get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_DPMulticast).  

## <a name="prepare-an-operating-system-image-for-multicast-deployments"></a>Przygotowywanie obrazu systemu operacyjnego dla wdrożeń za pomocą multiemisji  
 Aby skonfigurować pakiet obrazu systemu operacyjnego do obsługi multiemisji, zobacz [przygotować obraz systemu operacyjnego dla wdrożeń multiemisji](../get-started/manage-operating-system-images.md#BKMK_OSImageMulticast).  

##  <a name="BKMK_Deploy"></a> Wdrażanie sekwencji zadań  
 Wdróż system operacyjny w kolekcji docelowej. Aby uzyskać więcej informacji, zobacz [Wdrażanie sekwencji zadań](manage-task-sequences-to-automate-tasks.md#BKMK_DeployTS).  

