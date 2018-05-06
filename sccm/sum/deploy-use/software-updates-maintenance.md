---
title: Obsługa aktualizacji oprogramowania
titleSuffix: Configuration Manager
description: Aby zachować aktualizacji w programie Configuration Manager, można zaplanować zadanie oczyszczania usług WSUS, lub uruchomić ją ręcznie.
author: aczechowski
ms.date: 10/06/2016
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.assetid: 4b0e2e90-aac7-4d06-a707-512eee6e576c
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 03eabbfcd070bb61b2930fac89a551bbeb111eb4
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="software-updates-maintenance"></a>Obsługa aktualizacji oprogramowania

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Możesz zaplanować i uruchamianie zadania oczyszczania usług WSUS z poziomu konsoli programu Configuration Manager lub można ręcznie uruchomić zadanie oczyszczania usług WSUS we właściwościach składnika punktu aktualizacji oprogramowania. Gdy wybierzesz opcję uruchomienia zadania oczyszczania usług WSUS, zostanie ono uruchomione podczas następnej synchronizacji aktualizacji oprogramowania. Stan wygasłych aktualizacji oprogramowania na serwerze WSUS zostanie ustawiony jako odrzucony i usługa Windows Update Agent na komputerach nie będzie więcej wyszukiwać tych aktualizacji oprogramowania. Domyślnie zadanie oczyszczania usług WSUS jest uruchamiane co 30 dni.  

#### <a name="to-schedule-and-run-the-wsus-cleanup-job"></a>Aby zaplanować i uruchomić zadanie oczyszczania usług WSUS  

1.  W konsoli programu Configuration Manager, przejdź do **administracji** > **omówienie** > **konfiguracja lokacji** > **witryny**.  

2.  Kliknij pozycję **Konfiguruj składniki lokacji** w grupie **Ustawienia** , a następnie kliknij pozycję **Punkt aktualizacji oprogramowania** , aby otworzyć okno Właściwości składnika punktu aktualizacji oprogramowania.  

3.  Kliknij kartę **Reguły zastępowania** , wybierz pozycję **Uruchom kreatora oczyszczania usług WSUS**, a następnie kliknij przycisk **OK**.
