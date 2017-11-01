---
title: "Automatyczne kategoryzowanie urządzeń do kolekcji"
titleSuffix: Configuration Manager
description: "Kategoryzowanie urządzeń w kolekcji automatycznie z System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 98b038b4-1a13-4228-bdb8-a12194e32b0e
caps.latest.revision: "5"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 2a9b311b0abbeb56d9043410ecbeb54ec244fbef
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="automatically-categorize-devices-into-collections-with-system-center-configuration-manager"></a>Automatycznie kategoryzowanie urządzeń do kolekcji w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Możesz utworzyć kategorie urządzeń, które mogą być używane do automatycznego umieszczania urządzeń w kolekcji urządzeń, gdy używasz programu Configuration Manager w usłudze Microsoft Intune. Następnie konieczność do wybierz kategorię urządzeń, gdy rejestrują urządzenia w usłudze Intune. Możesz zmienić kategorii urządzeń w konsoli programu Configuration Manager.

> [!IMPORTANT]  
    >  Ta funkcja działa z **czerwca 2016** wersji programu Microsoft Intune lub nowszego. Upewnij się, że możesz zostały zaktualizowane do tej wersji przed wypróbowanie tych procedur.

## <a name="create-device-categories"></a>Tworzenie kategorii urządzeń

1.  Przejdź do **zasoby i zgodność** > **omówienie** > **kolekcje urządzeń**.
2.  Na **Home** karcie **kolekcje urządzeń** grupy, wybierz **Zarządzanie kategorie urządzeń**.
3.  Tworzenie, edytowanie lub usuwanie kategorii.

## <a name="associate-a-collection-with-a-device-category"></a>Skojarzenia kolekcji z kategorii urządzeń

Gdy kolekcja jest skojarzona z kategorii urządzeń, wszystkie urządzenia w tej kategorii zostanie dodany do kolekcji. Nie można dodać regułę kategorii urządzenia do wbudowanej kolekcji, takie jak **wszystkie systemy**.

1.  Na **reguł członkostwa** karcie **właściwości** okno dialogowe w kolekcji urządzeń, wybierz opcję **Dodaj regułę** > **regułę kategorii urządzenia**.
2.  W **wybierz kategorie urządzeń** okno dialogowe, wybierz co najmniej jednej kategorii urządzenia, które będą stosowane do wszystkich urządzeń w kolekcji.

## <a name="change-the-category-of-a-device"></a>Zmień kategorię urządzenia

1.  W **zasoby i zgodność** > **omówienie** > **urządzeń**, wybierz urządzenie z **urządzeń** listy.
2.  Na **Home** karcie **urządzenia** grupy, wybierz **Zmień kategorię**.
3.  Wybierz kategorię, a następnie wybierz pozycję **OK**.

## <a name="view-which-category-a-device-belongs-to"></a>Wyświetl urządzenie należy do kategorii

W **zasoby i zgodność** > **omówienie** > **urządzeń**w **urządzeń** listy kategorii jest wyświetlany w **kategorii urządzeń** kolumny.

Jeśli **kategorii urządzeń** kolumna nie jest wyświetlana, kliknij prawym przyciskiem myszy nagłówek kolumny w **urządzeń** listy (takich jak **nazwa**), a następnie wybierz pozycję **kategorii urządzeń**.

Jeśli przypisywanie urządzeń do kategorii, a następnie usunąć kategorię raportu **listy urządzeń zarejestrowanych przez użytkownika w programie Microsoft Intune** wyświetli identyfikator GUID w **kategorii urządzeń** kolumny, a nie nazwy kategorii.
