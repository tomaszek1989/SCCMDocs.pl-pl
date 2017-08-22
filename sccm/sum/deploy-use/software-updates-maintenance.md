---
title: Aktualizacje oprogramowania konserwacji | Dokumentacja firmy Microsoft
description: "Aby zachować aktualizacji w programie Configuration Manager, można zaplanować zadanie oczyszczania usług WSUS, lub uruchomić ją ręcznie."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology: configmgr-sum
ms.assetid: 4b0e2e90-aac7-4d06-a707-512eee6e576c
ms.openlocfilehash: 1590c623f7bc2f42a8617f110de5321212732a03
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="software-updates-maintenance"></a>Obsługa aktualizacji oprogramowania

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Możesz zaplanować i uruchamianie zadania oczyszczania usług WSUS z poziomu konsoli programu Configuration Manager lub można ręcznie uruchomić zadanie oczyszczania usług WSUS we właściwościach składnika punktu aktualizacji oprogramowania. Gdy wybierzesz opcję uruchomienia zadania oczyszczania usług WSUS, zostanie ono uruchomione podczas następnej synchronizacji aktualizacji oprogramowania. Stan wygasłych aktualizacji oprogramowania na serwerze WSUS zostanie ustawiony jako odrzucony i usługa Windows Update Agent na komputerach nie będzie więcej wyszukiwać tych aktualizacji oprogramowania. Domyślnie zadanie oczyszczania usług WSUS jest uruchamiane co 30 dni.  

#### <a name="to-schedule-and-run-the-wsus-cleanup-job"></a>Aby zaplanować i uruchomić zadanie oczyszczania usług WSUS  

1.  W konsoli programu Configuration Manager, przejdź do **administracji** > **omówienie** > **konfiguracja lokacji** > **witryny**.  

2.  Kliknij pozycję **Konfiguruj składniki lokacji** w grupie **Ustawienia** , a następnie kliknij pozycję **Punkt aktualizacji oprogramowania** , aby otworzyć okno Właściwości składnika punktu aktualizacji oprogramowania.  

3.  Kliknij kartę **Reguły zastępowania** , wybierz pozycję **Uruchom kreatora oczyszczania usług WSUS**, a następnie kliknij przycisk **OK**.
