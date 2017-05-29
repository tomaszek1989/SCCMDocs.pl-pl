---
title: "Dodawanie aktualizacji do grupy aktualizacji — Configuration Manager | Dokumentacja firmy Microsoft"
description: "Ręcznie lub automatycznie dodać aktualizacje oprogramowania do grupy aktualizacji oprogramowania w danym środowisku."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 01/23/2017
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: a0767664-fd60-46a8-9da5-86cc431ce53c
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4e44e2b8f6baf020c3b7742bafd607082ffacaa4
ms.openlocfilehash: 02e30ba48f3564fa8a31f21793c145054e02e002
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---

# <a name="add-software-updates-to-an-update-group"></a>Dodawanie aktualizacji oprogramowania do grupy aktualizacji  

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

 Grupy aktualizacji oprogramowania stanowią efektywną metodę organizowania aktualizacji oprogramowania w środowisku. Aktualizacje oprogramowania można ręcznie lub automatycznie dodawać do grupy aktualizacji oprogramowania przy użyciu reguły wdrażania automatycznego (ADR). Istnieje również możliwość wdrożenia grupy aktualizacji oprogramowania ręcznie lub automatycznie przy użyciu reguły ADR. Po wdrożeniu grupy aktualizacji oprogramowania można dodawać nowe aktualizacje oprogramowania do grupy i programu Configuration Manager automatycznie wdroży je. Aby dodać aktualizacje oprogramowania do nowej lub istniejącej grupy aktualizacji, wykonaj czynności opisane w poniższych procedurach.  

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
    >  Na **wszystkie aktualizacje oprogramowania** węzła, domyślnie programu Configuration Manager są wyświetlane tylko aktualizacje oprogramowania z **krytyczny** i **zabezpieczeń** Klasyfikacja opublikowane w ciągu ostatnich 30 dni.  

4.  Na karcie **Narzędzia główne** w grupie **Aktualizacja** kliknij przycisk **Edytuj członkostwo**.  

5.  Wybierz grupę aktualizacji, do której chcesz dodać aktualizacje oprogramowania.  

6.  Kliknij węzeł **Grupy aktualizacji oprogramowania** , aby wyświetlić grupę aktualizacji oprogramowania.  

7.  Wybierz grupę aktualizacji oprogramowania, a następnie na karcie **Narzędzia główne** w grupie **Aktualizacja** kliknij przycisk **Pokaż członków** , aby wyświetlić listę aktualizacji oprogramowania w grupie.  
