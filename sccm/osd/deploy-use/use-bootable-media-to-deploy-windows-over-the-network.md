---
title: "Wdrażanie systemu Windows za pośrednictwem sieci przy użyciu nośnika rozruchowego"
titleSuffix: Configuration Manager
description: "Wdrożenia za pomocą nośnika rozruchowego w programie System Center Configuration Manager do wdrażania systemu operacyjnego podczas uruchamiania komputera docelowego."
ms.custom: na
ms.date: 6/16/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 999b5409-7e72-48d2-8554-4d44427ce383
caps.latest.revision: "5"
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 7ba166225c93440ddc56eb39692c80680330a94d
ms.sourcegitcommit: 08f9854fb6c6d21e1e923b13e38a64d0bc2bc9a4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2017
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
