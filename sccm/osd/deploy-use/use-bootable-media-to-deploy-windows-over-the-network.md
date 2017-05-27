---
title: "Wdrażanie systemu Windows za pośrednictwem sieci przy użyciu nośnika rozruchowego | Dokumentacja firmy Microsoft"
description: "Użyj wdrożenia z nośników rozruchowych w programie System Center Configuration Manager do wdrażania systemu operacyjnego podczas uruchamiania komputera docelowego."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 999b5409-7e72-48d2-8554-4d44427ce383
caps.latest.revision: 5
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: beb730efbe4d9bae7c4c97f4e587c8919bd79049
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="use-bootable-media-to-deploy-windows-over-the-network-with-system-center-configuration-manager"></a>Wdrażanie systemu Windows za pośrednictwem sieci z System Center Configuration Manager przy użyciu nośnika rozruchowego

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Wdrożenia z nośników rozruchowych w programie System Center Configuration Manager umożliwiają wdrażanie systemu operacyjnego podczas uruchamiania komputera docelowego. W chwili uruchomienia komputer docelowy pobiera sekwencję zadań, obraz systemu operacyjnego oraz inną wymaganą zawartość z sieci. Ponieważ ta zawartość nie jest dołączona na nośniku, można ją aktualizować bez konieczności ponownego tworzenia nośnika.  

 Systemy operacyjne można wdrażać za pośrednictwem sieci przy użyciu multiemisji w następujących scenariuszach wdrażania systemu operacyjnego:  

-   [Odśwież istniejącego komputera z nowej wersji systemu Windows](refresh-an-existing-computer-with-a-new-version-of-windows.md)  

-   [Zainstaluj nową wersję systemu Windows na nowym komputerze (od zera)](install-new-windows-version-new-computer-bare-metal.md)  

-   [Zastąp istniejący komputer i przenieść ustawień](replace-an-existing-computer-and-transfer-settings.md)  

 Wykonaj kroki jednego ze scenariuszy wdrażania systemu operacyjnego, a następnie użyj poniższych sekcji w celu wdrożenia systemu operacyjnego za pomocą nośnika rozruchowego.  

## <a name="configure-deployment-settings"></a>Konfigurowanie ustawień wdrażania  
 W przypadku wykorzystania nośnika rozruchowego do rozpoczęcia procesu wdrażania systemu operacyjnego należy skonfigurować wdrożenie w celu udostępnienia systemu operacyjnego nośnikowi. Tę konfigurację można określić na stronie **Ustawienia wdrożenia** Kreatora wdrażania oprogramowania lub na karcie **Ustawienia wdrożenia** we właściwościach wdrożenia.  Dla ustawienia **Udostępnij dla następujących** skonfiguruj jedną z poniższych wartości:  

-   **Klienci programu Configuration Manager, nośniki i PXE**  

-   **Tylko nośniki i PXE**  

-   **Tylko nośniki i PXE (ukryte)**  

## <a name="create-the-bootable-media"></a>Tworzenie nośnika rozruchowego  
 Możesz określić, czy nośnik rozruchowy jest dyskiem flash USB, czy zestawem dysków CD/DVD. Komputer, dla którego nośnik ma zostać użyty, musi obsługiwać rozruch przy użyciu wybranego napędu rozruchowego. Aby uzyskać więcej informacji, zobacz [tworzenia nośnika rozruchowego](create-bootable-media.md).  

##  <a name="BKMK_Deploy"></a> Instalowanie systemu operacyjnego z nośnika rozruchowego  
 Włóż nośnik rozruchowy do napędu rozruchowego na komputerze, a następnie włącz go w celu zainstalowania systemu operacyjnego.  

