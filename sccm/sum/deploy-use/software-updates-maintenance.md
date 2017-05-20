---

title: "Obsługa aktualizacji oprogramowania | Dokumentacja firmy Microsoft"
description: "Aby zachować aktualizacji w programie Configuration Manager, można zaplanować zadania oczyszczania programu WSUS lub uruchomić ją ręcznie."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 4b0e2e90-aac7-4d06-a707-512eee6e576c
ms.translationtype: Machine Translation
ms.sourcegitcommit: e6cf8c799b5be2f7dbb6fadadddf702ec974ae45
ms.openlocfilehash: 1590c623f7bc2f42a8617f110de5321212732a03
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017



---
# <a name="software-updates-maintenance"></a>Obsługa aktualizacji oprogramowania

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Możesz zaplanować i uruchamiania programu WSUS oczyszczania zadań z konsoli programu Configuration Manager lub zadania oczyszczania WSUS można uruchomić ręcznie we właściwościach składnika punktu aktualizacji oprogramowania. Gdy wybierzesz opcję uruchomienia zadania oczyszczania usług WSUS, zostanie ono uruchomione podczas następnej synchronizacji aktualizacji oprogramowania. Stan wygasłych aktualizacji oprogramowania na serwerze WSUS zostanie ustawiony jako odrzucony i usługa Windows Update Agent na komputerach nie będzie więcej wyszukiwać tych aktualizacji oprogramowania. Domyślnie zadanie oczyszczania usług WSUS jest uruchamiane co 30 dni.  

#### <a name="to-schedule-and-run-the-wsus-cleanup-job"></a>Aby zaplanować i uruchomić zadanie oczyszczania usług WSUS  

1.  W konsoli programu Configuration Manager, przejdź do **Administracja** > **Przegląd** > **konfiguracja lokacji** > **witryny**.  

2.  Kliknij pozycję **Konfiguruj składniki lokacji** w grupie **Ustawienia** , a następnie kliknij pozycję **Punkt aktualizacji oprogramowania** , aby otworzyć okno Właściwości składnika punktu aktualizacji oprogramowania.  

3.  Kliknij kartę **Reguły zastępowania** , wybierz pozycję **Uruchom kreatora oczyszczania usług WSUS**, a następnie kliknij przycisk **OK**.

