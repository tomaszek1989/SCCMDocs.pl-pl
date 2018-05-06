---
title: Usunięcie punktu aktualizacji oprogramowania
titleSuffix: Configuration Manager
description: Wykonaj tę procedurę, aby usunąć rolę systemu lokacji punktu aktualizacji oprogramowania w lokacji z konsoli programu Configuration Manager.
author: aczechowski
ms.date: 10/06/2016
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.assetid: 2486375c-d4a2-4cf2-9124-9bee02bbf173
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 585077c44b13d79da55e8ab140fd93998b8371c1
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
#  <a name="BKMK_RemoveSUP"></a> Usuwanie roli systemu lokacji punktu aktualizacji oprogramowania  

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Można usunąć rolę systemu lokacji punktu aktualizacji oprogramowania w lokacji z konsoli programu Configuration Manager. Aby usunąć punkt aktualizacji oprogramowania z listy, następuje aktualizacja zasady klienta. Po usunięciu z lokacji ostatniego punktu aktualizacji oprogramowania lista tych punktów nie będzie zawierać żadnych wpisów, co w praktyce oznacza wyłączenie aktualizacji oprogramowania w tej lokacji. Jeśli w lokacji głównej jest więcej niż jeden punkt aktualizacji oprogramowania i usuniesz punkt aktualizacji oprogramowania skonfigurowany jako źródło synchronizacji, musisz wybrać w tej lokacji inny punkt aktualizacji oprogramowania i skonfigurować go jako nowe źródło synchronizacji.  

> [!NOTE]  
>  Po usunięciu roli punktu aktualizacji oprogramowania z systemu lokacji należy odczekać co najmniej 15 minut przed ponownym zainstalowaniem roli punktu aktualizacji oprogramowania.  

 Aby usunąć punkt aktualizacji oprogramowania, należy wykonać poniższe czynności.  

#### <a name="to-remove-the-software-update-point"></a>Aby usunąć punkt aktualizacji oprogramowania  

1.  W konsoli programu **Configuration Manager** kliknij przycisk **Administracja**.  

2.  W obszarze roboczym Administracja rozwiń węzeł **Konfiguracja lokacji**, a następnie kliknij przycisk **Serwery i role systemu lokacji**.  

3.  Wybierz serwer systemu lokacji zawierający punkt aktualizacji oprogramowania, który chcesz usunąć, a następnie na stronie **Role systemu lokacji**wybierz pozycję **Punkt aktualizacji oprogramowania**.  

4.  Na karcie **Rola lokacji** w grupie **Rola lokacji** kliknij przycisk **Usuń rolę**. Potwierdź, że chcesz usunąć punkt aktualizacji oprogramowania lub wybrać nowe źródło synchronizacji dla innych punktów aktualizacji oprogramowania w lokacji.  
