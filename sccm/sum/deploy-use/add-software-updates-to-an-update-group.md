---
title: 'Dodawanie aktualizacji do grupy aktualizacji '
titleSuffix: Configuration Manager
description: Ręcznie lub automatycznie dodawać aktualizacje oprogramowania do grupy aktualizacji oprogramowania w danym środowisku.
author: aczechowski
ms.date: 01/23/2017
ms.topic: conceptual
ms.prod: configuration-manager
ms.technology: configmgr-sum
ms.assetid: a0767664-fd60-46a8-9da5-86cc431ce53c
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: df213206ee673e872852958233973e4f091728b9
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="add-software-updates-to-an-update-group"></a>Dodawanie aktualizacji oprogramowania do grupy aktualizacji  

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

 Grupy aktualizacji oprogramowania stanowią efektywną metodę organizowania aktualizacji oprogramowania w środowisku. Aktualizacje oprogramowania można ręcznie lub automatycznie dodawać do grupy aktualizacji oprogramowania przy użyciu reguły wdrażania automatycznego (ADR). Istnieje również możliwość wdrożenia grupy aktualizacji oprogramowania ręcznie lub automatycznie przy użyciu reguły ADR. Po wdrożeniu grupy aktualizacji oprogramowania można dodawać nowe aktualizacje oprogramowania do grupy i programu Configuration Manager automatycznie wdraża je. Aby dodać aktualizacje oprogramowania do nowej lub istniejącej grupy aktualizacji, wykonaj czynności opisane w poniższych procedurach.  

#### <a name="to-add-software-updates-to-a-new-software-update-group"></a>Aby dodać aktualizacje oprogramowania do nowej grupy aktualizacji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym Biblioteka oprogramowania rozwiń listę **Aktualizacje oprogramowania**, a następnie kliknij pozycję **Wszystkie aktualizacje oprogramowania**.  

3.  Wybierz aktualizacje oprogramowania do dodania do nowej grupy aktualizacji.  

4.  Na karcie **Narzędzia główne** w grupie **Aktualizacja** kliknij przycisk **Utwórz grupę aktualizacji oprogramowania**.  

5.  Określ nazwę grupy aktualizacji oprogramowania i opcjonalnie wprowadź opis. Wprowadź nazwę i opis, które zapewniają odpowiednią ilość informacji w celu ustalenia typu aktualizacji oprogramowania znajdujących się w danej grupie. Aby kontynuować, kliknij przycisk **Utwórz**.  

6.  Kliknij węzeł **Grupy aktualizacji oprogramowania** , aby wyświetlić nową grupę aktualizacji oprogramowania.  

7.  Wybierz grupę aktualizacji oprogramowania, a następnie na karcie **Narzędzia główne** w grupie **Aktualizacja** kliknij przycisk **Pokaż członków** , aby wyświetlić listę aktualizacji oprogramowania w grupie.  

#### <a name="to-add-software-updates-to-an-existing-software-update-group"></a>Aby dodać aktualizacje oprogramowania do istniejącej grupy aktualizacji  

1.  W konsoli programu Configuration Manager kliknij przycisk **Biblioteka oprogramowania**.  

2.  W obszarze roboczym Biblioteka oprogramowania rozwiń listę **Aktualizacje oprogramowania**, a następnie kliknij pozycję **Wszystkie aktualizacje oprogramowania**.  

3.  Wybierz aktualizacje oprogramowania do dodania do nowej grupy aktualizacji.  

    > [!NOTE]  
    >  Na **wszystkie aktualizacje oprogramowania** węzła, domyślnie program Configuration Manager wyświetla wyłącznie aktualizacje oprogramowania z **krytyczny** i **zabezpieczeń** klasyfikacji i które zostały wydane w ciągu ostatnich 30 dni.  

4.  Na karcie **Narzędzia główne** w grupie **Aktualizacja** kliknij przycisk **Edytuj członkostwo**.  

5.  Wybierz grupę aktualizacji, do której chcesz dodać aktualizacje oprogramowania.  

6.  Kliknij węzeł **Grupy aktualizacji oprogramowania** , aby wyświetlić grupę aktualizacji oprogramowania.  

7.  Wybierz grupę aktualizacji oprogramowania, a następnie na karcie **Narzędzia główne** w grupie **Aktualizacja** kliknij przycisk **Pokaż członków** , aby wyświetlić listę aktualizacji oprogramowania w grupie.  
