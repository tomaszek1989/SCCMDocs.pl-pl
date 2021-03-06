---
title: Symulowanie wdrożenia aplikacji
titleSuffix: Configuration Manager
description: Ocenia metodę wykrywania, wymagania i zależności dla typu wdrożenia bez instalowania aplikacji.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-app
ms.topic: conceptual
ms.assetid: 28b240a4-d358-40ce-8006-c697b1622ece
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: bd2f4f24a9bc22daac5b5c6e785ff2ea5d02f49a
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="simulate-application-deployments-with-system-center-configuration-manager"></a>Symulowanie wdrożenia aplikacji w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Wdrożenia symulowane służy do testowania wdrożenia aplikacji bez instalowania lub odinstalowywania aplikacji. Wdrożenie symulowane ocenia metodę wykrywania, wymagania i zależności dla typu wdrożenia. Raportuje wyniki w **wdrożeń** węzła **monitorowanie** obszaru roboczego. Użyj procedury w tym temacie, aby symulować wdrożenie aplikacji w programie System Center Configuration Manager (program Configuration Manager).  

> [!NOTE]  
> Wdrożeń symulowanych nie można używać dla kolekcji urządzeń przenośnych.  
>   
> Nie można wdrożyć aplikacji z celem wdrożenia **Odinstalowanie** , jeśli aktywne jest wdrożenie symulowane tej samej aplikacji.  

## <a name="configure-a-simulated-application-deployment"></a>Skonfiguruj symulowane wdrożenie aplikacji

1.  W konsoli programu Configuration Manager wybierz jedną z następujących czynności:  
    -   kolekcja użytkowników,  
    -   kolekcja urządzeń,  
    -   Aplikacji programu Configuration Manager.  

2.  Na **Home** karcie **wdrożenia** grupy, wybierz **wdrożenie symulowane**.  

3.  W Kreatorze symulowania wdrożenia aplikacji ustaw następujące szczegóły wdrożenia symulowanego:  

    -   **Aplikacja**. Wybierz **Przeglądaj**, a następnie wybierz aplikację, aby utworzyć symulowane wdrożenie.  

    -   **Kolekcja**. Wybierz **Przeglądaj**, a następnie wybierz kolekcję, do której chcesz użyć dla wdrożenia symulowanego.  

    -   **Akcja**. Wybierz z listy rozwijanej, czy chcesz symulować instalację czy deinstalację wybranej aplikacji.  

    -   **Wdróż automatycznie z logowaniem użytkownika lub bez**. Jeśli ta opcja jest zaznaczona, klienci będą oceniać wdrożenie symulowane czy klienci są zalogowani.  

4.  Kliknij przycisk **dalej**, zapoznaj się z informacjami na **Podsumowanie** strony, a następnie Zakończ pracę kreatora, aby utworzyć symulowane wdrożenie aplikacji.  

5.  Symulowane aplikacje pojawiają się w **wdrożeń** węzła **monitorowanie** obszaru roboczego z celem **Symulacja**. Aby uzyskać więcej informacji o sposobie monitorowania wdrażania aplikacji, zobacz [monitorowanie aplikacji z konsoli programu System Center Configuration Manager](../../apps/deploy-use/monitor-applications-from-the-console.md).  
