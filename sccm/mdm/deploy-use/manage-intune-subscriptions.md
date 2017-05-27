---
title: "Zarządzanie subskrypcji usługi Intune skojarzony z System Center Configuration Manager | Dokumentacja firmy Microsoft"
description: "Zarządzaj subskrypcji usługi Intune skojarzony z programem System Center Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9b494767-68c1-47b1-9a86-591bff0ad491
caps.latest.revision: 18
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: 2e0b3cd1070d0f8adb1219acd33c3126d2758a49
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="manage-an-intune-subscription-associated-with-system-center-configuration-manager"></a>Zarządzanie subskrypcji usługi Intune skojarzony z System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Dodaj Microsoft Intune (subskrypcji wersji próbnej lub płatnej subskrypcji) do programu Configuration Manager, a następnie musi przełączyć się do innej subskrypcji usługi Intune, należy usunąć zarówno **subskrypcja usługi Microsoft Intune** i **punktem połączenia usługi** z konsoli programu Configuration Manager, aby można było dodać nową subskrypcję.

> [!NOTE]
> Można skonfigurować tylko jednej subskrypcji usługi Intune w czasie w hybrydowego zarządzania urządzeniami przenośnymi.

## <a name="how-to-delete-an-intune-subscription-from-configuration-manager"></a>Sposób usuwania subskrypcji usługi Intune z programu Configuration Manager

> [!IMPORTANT]
>  Całą zawartość w tym rejestracje użytkownika, zasad i wdrożenia aplikacji skonfigurowany dla urządzeń zarządzanych przez subskrypcję usługi Intune zostaną usunięte po usunięciu subskrypcji.

1.  W konsoli programu Configuration Manager, przejdź do **Administracja** > **Przegląd** > **usług w chmurze** > **subskrypcje usługi Microsoft Intune**.

2.  Kliknij prawym przyciskiem myszy wymienionych **subskrypcja usługi Microsoft Intune**, a następnie kliknij przycisk **usunąć**.

3.   W kreatorze kliknij **Usuń subskrypcja usługi Microsoft Intune z programu Configuration Manager**, kliknij przycisk **dalej**, a następnie kliknij przycisk **dalej** ponownie, aby usunąć subskrypcję.


## <a name="how-to-remove-the-service-connection-point-role"></a>Jak usunąć rolę punktu połączenia usługi

1.  Przejdź do **Administracja** > **Przegląd** > **lokacji konfiguracji** > **serwery i role systemu lokacji**.

2.  Wybierz serwer, który hostuje rolę **Punkt połączenia z usługą** .

3.  Na liście **Role systemu lokacji** wybierz pozycję **Punkt połączenia z usługą**, a następnie na wstążce kliknij pozycję **Usuń rolę**. Potwierdź, że chcesz usunąć rolę. Punkt połączenia z usługą zostanie usunięty.

Teraz możesz utworzyć nowy punkt połączenia z usługą, dodać nową subskrypcję usługi Intune do programu Configuration Manager i ustawić program Configuration Manager jako urząd zarządzania urządzeniami przenośnymi.

## <a name="how-to-change-mdm-authority-to-intune"></a>Jak zmienić urzędu zarządzania urządzeniami Przenośnymi usługi Intune

Począwszy od wersji 1610, możesz przełączyć urzędu zarządzania urządzeniami Przenośnymi z programu Configuration Manager do usługi Intune. Informacje o tej funkcji będzie wkrótce dostępne.

