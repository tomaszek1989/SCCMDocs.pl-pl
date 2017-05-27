---
title: "Automatycznie kategoryzowanie urządzenia do kolekcji | Dokumentacja firmy Microsoft"
description: "Klasyfikowanie urządzenia do kolekcji automatycznie z System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 98b038b4-1a13-4228-bdb8-a12194e32b0e
caps.latest.revision: 5
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: d1b79fb091a6ae4b967d63843ae7b45a0cbeb555
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="automatically-categorize-devices-into-collections-with-system-center-configuration-manager"></a>Automatycznie kategoryzowanie urządzenia do kolekcji z programem System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Możesz utworzyć kategorie urządzeń, które mogą być używane do automatycznego umieszczania urządzeń w kolekcji urządzeń, podczas korzystania z programu Configuration Manager z Microsoft Intune. Następnie konieczność do wybierz kategorię urządzenia, gdy ich zarejestrować urządzenia w usłudze Intune. Z konsoli programu Configuration Manager można zmienić kategorię urządzenia.

> [!IMPORTANT]  
    >  Ta funkcja działa z **czerwca 2016** wersji programu Microsoft Intune i nowszych. Upewnij się, że masz zostały zaktualizowane do tej wersji przed podjęciem próby wykonania tych procedur.

## <a name="create-device-categories"></a>Tworzenie kategorii urządzenia

1.  Przejdź do **zasoby i zgodność** > **Przegląd** > **kolekcji urządzeń**.
2.  Na **Home** w karcie **kolekcji urządzeń** grupy, wybierz **Zarządzanie kategorie urządzeń**.
3.  Tworzenie, edytowanie lub usuwanie kategorii.

## <a name="associate-a-collection-with-a-device-category"></a>Skojarzenia kolekcji z kategorii urządzenia

Po skojarzeniu kolekcji z kategorii urządzenia, wszystkie urządzenia w tej kategorii zostanie dodany do kolekcji. Nie można dodać reguły kategorii urządzenia do kolekcji wbudowanych, takich jak **wszystkie systemy**.

1.  Na **reguł członkostwa** na karcie **właściwości** okno dialogowe dla kolekcji urządzeń wybierz **Dodaj regułę** > **regułę kategorii urządzenia**.
2.  W **wybierz kategorie urządzeń** okno dialogowe, wybierz co najmniej jednej kategorii urządzenia, które będą stosowane do wszystkich urządzeń w kolekcji.

## <a name="change-the-category-of-a-device"></a>Zmień kategorię urządzenia

1.  W **zasoby i zgodność** > **Przegląd** > **urządzeń**, wybierz urządzenie z **urządzeń** listy.
2.  Na **Home** w karcie **urządzenia** grupy, wybierz **Zmień kategorię**.
3.  Wybierz kategorię, a następnie wybierz **OK**.

## <a name="view-which-category-a-device-belongs-to"></a>Wyświetlanie urządzenie należy do kategorii

W **zasoby i zgodność** > **Przegląd** > **urządzeń**w **urządzeń** listy kategorii jest wyświetlany w **kategorię urządzenia** kolumny.

Jeśli **kategorię urządzenia** kolumny nie jest wyświetlany, kliknij prawym przyciskiem myszy nagłówek kolumny w **urządzeń** listy (takich jak **nazwa**), a następnie zaznacz pozycję **kategorię urządzenia**.

Jeśli przypisać urządzenia do kategorii, a następnie Usuń kategorię raportu **listy urządzeń zarejestrowanych przez użytkownika w programie Microsoft Intune** spowoduje wyświetlenie identyfikatora GUID w **kategorię urządzenia** kolumny, a nie nazwę kategorii.

