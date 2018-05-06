---
title: Automatyczne kategoryzowanie urządzeń do kolekcji
titleSuffix: Configuration Manager
description: Kategoryzowanie urządzeń w kolekcji automatycznie z System Center Configuration Manager.
ms.date: 04/23/2016
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 98b038b4-1a13-4228-bdb8-a12194e32b0e
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: fcffc48431045fab2b2f69e112258c844ad184bb
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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
