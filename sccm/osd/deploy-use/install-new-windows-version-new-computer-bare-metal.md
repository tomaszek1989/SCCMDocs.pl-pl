---
title: "Zainstaluj system Windows na nowym komputerze — Configuration Manager | Dokumentacja firmy Microsoft"
description: "Użyj Menedżera konfiguracji, aby zainstalować system operacyjny na nowym komputerze (od zera) przy użyciu środowiska PXE, producenta OEM lub nośników autonomicznych."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f5ad22d5-7df1-49c6-8a0f-db1c3f0cda19
caps.latest.revision: "8"
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 584dad7d8b05a2da9f7a66b73028ae99ff1a594f
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="install-a-new-version-of-windows-on-a-new-computer-bare-metal-with-system-center-configuration-manager"></a>Instalowanie nowej wersji systemu Windows na nowym komputerze (od zera) przy użyciu programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

W tym temacie przedstawiono ogólne kroki w System Center Configuration Manager do zainstalowania systemu operacyjnego na nowym komputerze. W tym scenariuszu są dostępne różne metody wdrażania, takie jak wdrażanie przy użyciu serwera PXE, producenta OEM lub nośników autonomicznych. Jeśli nie wiesz, że jest to scenariusz wdrażania prawo systemu operacyjnego, zobacz [scenariusze wdrażania systemów operacyjnych dla przedsiębiorstw](scenarios-to-deploy-enterprise-operating-systems.md).  

Skorzystaj z poniższych sekcji, aby odświeżyć istniejący komputer za pomocą nowej wersji systemu Windows.  

##  <a name="BKMK_Plan"></a> Planowanieowanie  

-   **Planowanie i implementowanie wymagań dotyczących infrastruktury**  

     Istnieje kilka wymagań dotyczących infrastruktury, które należy spełnić przed przystąpieniem do wdrażania systemów operacyjnych, takich jak zestaw Windows ADK, usługi wdrażania systemu Windows (WDS), obsługiwane konfiguracje dysków twardych itd. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące infrastruktury dla wdrożenia systemu operacyjnego](../plan-design/infrastructure-requirements-for-operating-system-deployment.md).

##  <a name="BKMK_Configure"></a> Konfiguracja  

1.  **Przygotowywanie obrazu rozruchowego**  

     Obrazy rozruchowe pozwalają uruchomić komputer w środowisku Windows PE (minimalny system operacyjny z ograniczonymi składnikami i usługami), które umożliwia instalację pełnego systemu operacyjnego Windows na komputerze.   Podczas wdrażania systemów operacyjnych należy wybrać obraz rozruchowy i wykonać jego dystrybucję do punktu dystrybucji. Aby przygotować obraz rozruchowy, skorzystaj z następujących informacji:  

    -   Aby dowiedzieć się więcej na temat obrazów rozruchowych, zobacz [zarządzanie obrazami rozruchowymi](../get-started/manage-boot-images.md).  

    -   Aby uzyskać więcej informacji o sposobie dostosowywania obrazu rozruchowego, zobacz [dostosowywanie obrazów rozruchowych](../get-started/customize-boot-images.md).  

    -   Roześlij obraz rozruchowy do punktów dystrybucji. Aby uzyskać więcej informacji, zobacz [dystrybucji zawartości](../../core/servers/deploy/configure/deploy-and-manage-content.md#a-namebkmkdistributea-distribute-content).  

2.  **Przygotowywanie obrazu systemu operacyjnego**  

     Obraz systemu operacyjnego zawiera pliki niezbędne do zainstalowania systemu operacyjnego na komputerze docelowym. Aby przygotować obraz systemu operacyjnego, skorzystaj z następujących informacji:  

    -   Aby dowiedzieć się więcej o sposobie tworzenia obrazu systemu operacyjnego, zobacz [zarządzanie obrazami systemu operacyjnego](../get-started/manage-operating-system-images.md).

    -   Roześlij obraz systemu operacyjnego do punktów dystrybucji. Aby uzyskać więcej informacji, zobacz [dystrybucji zawartości](../../core/servers/deploy/configure/deploy-and-manage-content.md#a-namebkmkdistributea-distribute-content).

3.  **Tworzenie sekwencji zadań w celu wdrożenia systemu operacyjnego za pośrednictwem sieci**  

     Sekwencje zadań umożliwiają zautomatyzowanie procesu instalacji systemu operacyjnego za pośrednictwem sieci. Wykonaj kroki w [tworzenia sekwencji zadań w celu zainstalowania systemu operacyjnego](create-a-task-sequence-to-install-an-operating-system.md) tworzenia sekwencji zadań do wdrażania systemu operacyjnego. W zależności od wybranej metody wdrażania mogą istnieć dodatkowe zagadnienia dotyczące sekwencji zadań.  

##  <a name="BKMK_Deploy"></a> Wdróż  

-   Użyj jednej z poniższych metod wdrażania, aby wdrożyć system operacyjny:  

    -   [Wdrażanie systemu Windows za pośrednictwem sieci przy użyciu środowiska PXE](use-pxe-to-deploy-windows-over-the-network.md)  

    -   [Wdrażanie systemu Windows za pośrednictwem sieci przy użyciu multiemisji](use-multicast-to-deploy-windows-over-the-network.md)  

    -   [Tworzenie obrazu dla producenta OEM w fabryce lub lokalnym magazynie](create-an-image-for-an-oem-in-factory-or-a-local-depot.md)  

    -   [Zastosowanie nośników samodzielnych do wdrażania systemu Windows bez użycia sieci](use-stand-alone-media-to-deploy-windows-without-using-the-network.md)  

    -   [Wdrażanie systemu Windows za pośrednictwem sieci przy użyciu nośnika rozruchowego](use-bootable-media-to-deploy-windows-over-the-network.md)  

## <a name="monitor"></a>Monitor  

-   **Monitorowanie wdrożenia sekwencji zadań**  

     Aby monitorować wdrożenia sekwencji zadań instalacji systemu operacyjnego, zobacz [monitorowanie wdrożeń systemu operacyjnego](monitor-operating-system-deployments.md).  
