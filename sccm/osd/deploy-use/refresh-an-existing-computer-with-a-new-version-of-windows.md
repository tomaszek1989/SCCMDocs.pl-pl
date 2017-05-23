---
title: "Odśwież istniejącego komputera z nowej wersji systemu Windows | Dokumentacja firmy Microsoft"
description: "Można stosować różne metody w programie Configuration Manager na partycje i sformatowanie (czyszczenia) istniejącego komputera i zainstalować nowy system operacyjny na komputerze."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b189a346-8c0d-4870-a876-0719fbb0ab04
caps.latest.revision: 7
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 74341fb60bf9ccbc8822e390bd34f9eda58b4bda
ms.openlocfilehash: b247cbb68ed63a8eb99715a248686d68a28c53e2
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="refresh-an-existing-computer-with-a-new-version-of-windows-using-system-center-configuration-manager"></a>Odświeżenie istniejącego komputera przy użyciu nowej wersji systemu Windows za pomocą programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Ten temat zawiera ogólne kroki w System Center Configuration Manager na partycje i formatowania (czyszczenia) istniejącego komputera i zainstaluj nowy system operacyjny na komputerze. W tym scenariuszu są dostępne różne metody wdrażania, takie jak wdrażanie przy użyciu serwera PXE, nośnika rozruchowego lub Centrum oprogramowania. Można również zdecydować się na zainstalowanie punktu migracji stanu w celu zapisania ustawień i przywrócenia ich w nowym systemie operacyjnym po jego zainstalowaniu. Jeśli nie wiesz, że to jest scenariusz wdrażania prawa systemu operacyjnego dla Ciebie, zobacz [scenariusze wdrażania systemów operacyjnych enterprise](scenarios-to-deploy-enterprise-operating-systems.md).  

 Skorzystaj z poniższych sekcji, aby odświeżyć istniejący komputer za pomocą nowej wersji systemu Windows.  

##  <a name="BKMK_Plan"></a> Planowanieowanie  

-   **Planowanie i implementowanie wymagań dotyczących infrastruktury**  

     Istnieje kilka wymagań dotyczących infrastruktury, które muszą być spełnione przed wdrożeniem obsługiwanych systemów operacyjnych, takich jak Windows ADK, narzędzie migracji stanu użytkowników (USMT), usługi wdrażania systemu Windows (WDS), konfiguracje dysków twardych, itd. Aby uzyskać więcej informacji, zobacz [wymagania dotyczące wdrażania systemu operacyjnego infrastruktury](../plan-design/infrastructure-requirements-for-operating-system-deployment.md).  

-   **Instalowanie punktu migracji stanu (wymagane tylko w przypadku przenoszenia ustawień)**  

     Jeśli zamierzasz przechwycić ustawienia z istniejącego komputera, a następnie przywrócić je w nowym systemie operacyjnym, musisz zainstalować punkt migracji stanu. Aby uzyskać więcej informacji, zobacz [punkt migracji stanu](../get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_StateMigrationPoints).  

##  <a name="BKMK_Configure"></a> Konfiguracja  

1.  **Przygotowywanie obrazu rozruchowego**  

     Obrazy rozruchowe pozwalają uruchomić komputer w środowisku Windows PE (minimalny system operacyjny z ograniczonymi składnikami i usługami), które umożliwia instalację pełnego systemu operacyjnego Windows na komputerze.   Podczas wdrażania systemów operacyjnych należy wybrać obraz rozruchowy i wykonać jego dystrybucję do punktu dystrybucji. Aby przygotować obraz rozruchowy, skorzystaj z następujących informacji:  

    -   Aby dowiedzieć się więcej na temat obrazów rozruchowych, zobacz [obrazów rozruchowych Zarządzaj](../get-started/manage-boot-images.md).  

    -   Aby uzyskać więcej informacji o sposobie dostosowywania obrazu rozruchowego, zobacz [dostosowywanie obrazów rozruchowych](../get-started/customize-boot-images.md).  

    -   Roześlij obraz rozruchowy do punktów dystrybucji. Aby uzyskać więcej informacji, zobacz [dystrybucji zawartości](../../core/servers/deploy/configure/deploy-and-manage-content.md#a-namebkmkdistributea-distribute-content).  

2.  **Przygotowywanie obrazu systemu operacyjnego**  

     Obraz systemu operacyjnego zawiera pliki niezbędne do zainstalowania systemu operacyjnego na komputerze docelowym. Aby przygotować obraz systemu operacyjnego, skorzystaj z następujących informacji:  

    -   Aby dowiedzieć się więcej o tworzeniu obrazu systemu operacyjnego, zobacz [zarządzania obrazami systemu operacyjnego](../get-started/manage-operating-system-images.md).  

    -   Roześlij obraz systemu operacyjnego do punktów dystrybucji. Aby uzyskać więcej informacji, zobacz [dystrybucji zawartości](../../core/servers/deploy/configure/deploy-and-manage-content.md#a-namebkmkdistributea-distribute-content).  

3.  **Tworzenie sekwencji zadań w celu wdrożenia systemu operacyjnego za pośrednictwem sieci**  

     Sekwencje zadań umożliwiają zautomatyzowanie procesu instalacji systemu operacyjnego za pośrednictwem sieci. Wykonaj kroki w [tworzenia sekwencji zadań w celu zainstalowania systemu operacyjnego](create-a-task-sequence-to-install-an-operating-system.md) do tworzenia sekwencji zadań w celu wdrożenia systemu operacyjnego. W zależności od wybranej metody wdrażania mogą istnieć dodatkowe zagadnienia dotyczące sekwencji zadań.  

    > [!NOTE]  
    >  W tym scenariuszu sekwencja zadań formatuje i dzieli na partycje dyski twarde na komputerze. Aby przechwycić ustawienia użytkownika, należy użyć punktu migracji stanu i wybrać pozycję **Zapisz ustawienia użytkownika i pliki w punkcie migracji stanu** na stronie **Migracja stanu** w kreatorze tworzenia sekwencji zadań. Jeśli zapiszesz ustawienia użytkownika i pliki lokalnie, ich zostaną utracone po sformatowaniu dysku twardego i programu Configuration Manager nie będzie można przywrócić ustawienia. Aby uzyskać więcej informacji, zobacz [zarządzania stanem użytkownika](../get-started/manage-user-state.md).  

##  <a name="BKMK_Deploy"></a> Wdróż  

-   Użyj jednej z poniższych metod wdrażania, aby wdrożyć system operacyjny:  

    -   [Użyj środowiska PXE do wdrażania systemu Windows za pośrednictwem sieci](use-pxe-to-deploy-windows-over-the-network.md)  

    -   [Korzystania z multiemisji do wdrażania systemu Windows za pośrednictwem sieci](use-multicast-to-deploy-windows-over-the-network.md)  

    -   [Tworzenie obrazu dla producenta OEM w fabryce lub lokalnego magazynu](create-an-image-for-an-oem-in-factory-or-a-local-depot.md)  

    -   [Do wdrażania systemu Windows bez użycia sieci należy używać nośników samodzielnych](use-stand-alone-media-to-deploy-windows-without-using-the-network.md)  

    -   [Wdrażanie systemu Windows za pośrednictwem sieci przy użyciu nośnika rozruchowego](use-bootable-media-to-deploy-windows-over-the-network.md)  

    -   [Wdrażanie systemu Windows za pośrednictwem sieci za pomocą Centrum oprogramowania](use-software-center-to-deploy-windows-over-the-network.md)  

## <a name="monitor"></a>Monitor  

-   **Monitorowanie wdrożenia sekwencji zadań**  

     Aby monitorować wdrożenia sekwencji zadań w celu zainstalowania systemu operacyjnego, zobacz [monitorowania wdrożeń systemu operacyjnego](monitor-operating-system-deployments.md).  

