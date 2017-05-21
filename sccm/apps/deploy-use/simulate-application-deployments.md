---
title: "Symulowanie wdrożenia aplikacji | Dokumentacja firmy Microsoft"
description: "Należy ocenić metodę wykrywania, wymagania i zależności dla typu wdrożenia bez instalowania aplikacji."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 28b240a4-d358-40ce-8006-c697b1622ece
caps.latest.revision: 6
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0ad42d07d260581099046f11255ee312046b2595
ms.openlocfilehash: b06539ded21eac71dda7da89dae96fda7a801260
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="simulate-application-deployments-with-system-center-configuration-manager"></a>Symulowanie wdrożenia aplikacji z System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Wdrożenia symulowane służy do testowania wdrożenia aplikacji bez instalowania lub odinstalowywania aplikacji. Wdrożenie symulowane ocenia metodę wykrywania, wymagania i zależności dla typu wdrożenia. Raportuje wyniki w **wdrożeń** węźle **monitorowanie** obszaru roboczego. Procedura w tym temacie umożliwia symulację wdrożenia aplikacji w programie System Center Configuration Manager (Menedżer konfiguracji).  

> [!NOTE]  
> Wdrożeń symulowanych nie można używać dla kolekcji urządzeń przenośnych.  
>   
> Nie można wdrożyć aplikacji z celem wdrożenia **Odinstalowanie** , jeśli aktywne jest wdrożenie symulowane tej samej aplikacji.  

## <a name="configure-a-simulated-application-deployment"></a>Skonfiguruj symulowane wdrożenie aplikacji

1.  W konsoli programu Configuration Manager wybierz jedną z następujących czynności:  
    -   kolekcja użytkowników,  
    -   kolekcja urządzeń,  
    -   Aplikacji programu Configuration Manager.  

2.  Na **Home** w karcie **wdrożenia** grupy, wybierz **wdrożenie symulowane**.  

3.  W Kreatorze symulowania wdrożenia aplikacji ustaw następujące szczegóły symulowanego wdrożenia:  

    -   **Aplikacja**. Wybierz **Przeglądaj**, a następnie wybierz aplikację, aby utworzyć symulowane wdrożenie dla.  

    -   **Kolekcja**. Wybierz **Przeglądaj**, a następnie wybierz kolekcję, której chcesz użyć dla wdrożenia symulowanego.  

    -   **Akcja**. Wybierz z listy rozwijanej, czy chcesz symulować instalację lub deinstalację wybranej aplikacji.  

    -   **Wdróż automatycznie z logowaniem użytkownika lub bez**. Jeśli ta opcja jest zaznaczona, klienci będą oceniać wdrożenie symulowane nieodpłatnie lub klienci są zalogowani.  

4.  Kliknij przycisk **dalej**, zapoznaj się z informacjami na **Podsumowanie** strony, a następnie Zakończ pracę kreatora, aby utworzyć symulowane wdrożenie aplikacji.  

5.  Symulowane aplikacje pojawiają się w **wdrożeń** węzła **monitorowanie** obszaru roboczego z celem **Symulacja**. Aby uzyskać więcej informacji o sposobie monitorowania wdrażania aplikacji, zobacz [monitorowanie aplikacji z konsoli programu System Center Configuration Manager](../../apps/deploy-use/monitor-applications-from-the-console.md).  

