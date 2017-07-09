---
title: "Wdrażanie systemu Windows za pośrednictwem sieci przy użyciu nośnika rozruchowego | Dokumentacja firmy Microsoft"
description: "Wdrożenia za pomocą nośnika rozruchowego w programie System Center Configuration Manager do wdrażania systemu operacyjnego podczas uruchamiania komputera docelowego."
ms.custom: na
ms.date: 6/16/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 999b5409-7e72-48d2-8554-4d44427ce383
caps.latest.revision: 5
author: mattbriggs
ms.author: mattbriggs
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f4c46bfab9b40b29654f4e883817a5508ab25b74
ms.openlocfilehash: 9b20e5e2a66d92038033e816e6fc701581c48a7f
ms.contentlocale: pl-pl
ms.lasthandoff: 06/28/2017


---
# <a name="use-bootable-media-to-deploy-windows-over-the-network-with-system-center-configuration-manager"></a>Wdrażanie systemu Windows za pośrednictwem sieci w programie System Center Configuration Manager przy użyciu nośnika rozruchowego

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Podczas uruchamiania komputera docelowego przy użyciu nośnika rozruchowego wdrożenia może wdrożenia systemu operacyjnego. Nośnik zawiera wskaźnik do sekwencję zadań, obraz systemu operacyjnego oraz inną wymaganą zawartość z sieci. Podczas uruchamiania komputera docelowego, komputer pobiera elementów, do którego odwołuje się wskaźnik myszy. Z nośnika rozruchowego bez zawartości należy zaktualizować element docelowy bez konieczności go zamienić na nośniku.

Systemy operacyjne mogą wdrażać za pośrednictwem sieci przy użyciu multiemisji w następujących scenariuszach wdrażania systemu operacyjnego:

-   [Odświeżanie istniejącego komputera za pomocą nowej wersji systemu Windows](refresh-an-existing-computer-with-a-new-version-of-windows.md)

-   [Instalowanie nowej wersji systemu Windows na nowym komputerze (od zera)](install-new-windows-version-new-computer-bare-metal.md)  

-   [Zastępowanie istniejącego komputera i transferowanie ustawień](replace-an-existing-computer-and-transfer-settings.md)  

Wykonaj kroki jednego ze scenariuszy wdrażania systemu operacyjnego, a następnie użyj poniższych sekcji w celu wdrożenia systemu operacyjnego za pomocą nośnika rozruchowego.  

## <a name="configure-deployment-settings"></a>Konfigurowanie ustawień wdrażania  
Korzystając z nośnika rozruchowego do rozpoczęcia procesu wdrażania systemu operacyjnego, należy skonfigurować wdrożenie w celu udostępnienia systemu operacyjnego nośnikowi. Można ustawić tę opcję na **ustawienia wdrażania** strony Kreatora wdrażania oprogramowania lub w **ustawienia wdrażania** we właściwościach wdrożenia. Dla ustawienia **Udostępnij dla następujących** wybierz jedną z poniższych wartości:

-   Klienci programu Configuration Manager, nośniki i PXE

-   Tylko nośniki i PXE

-   Tylko nośniki i PXE (ukryte)

## <a name="create-the-bootable-media"></a>Tworzenie nośnika rozruchowego
Może określić, czy nośnik rozruchowy jest dyskiem flash USB, czy zestawem dysków CD/DVD. Komputer, który uruchamia nośnik musi obsługiwać opcję wybrany jako dysk rozruchowy. Aby uzyskać więcej informacji, zobacz [tworzenia nośnika rozruchowego](create-bootable-media.md).  

##  <a name="BKMK_Deploy"></a> Instalowanie systemu operacyjnego z nośnika rozruchowego  
Włóż nośnik rozruchowy do napędu rozruchowego na komputerze, a następnie włącz go w celu zainstalowania systemu operacyjnego.

