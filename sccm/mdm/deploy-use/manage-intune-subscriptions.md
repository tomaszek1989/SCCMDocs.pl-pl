---
title: Zarządzanie subskrypcją usługi Intune
titleSuffix: Configuration Manager
description: Zarządzanie subskrypcję usługi Intune skojarzony z System Center Configuration Manager.
ms.date: 06/02/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 9b494767-68c1-47b1-9a86-591bff0ad491
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 1b8390faa557f37b2ee148299079df81d3c13299
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="manage-an-intune-subscription-associated-with-system-center-configuration-manager"></a>Zarządzanie subskrypcją usługi Intune skojarzony z System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Jeśli dodawanie Microsoft Intune (subskrypcję próbną lub płatną) do programu Configuration Manager, a następnie należy przełączyć się do innej subskrypcji usługi Intune, musisz usunąć **subskrypcję usługi Microsoft Intune** i **punkt połączenia z usługą** z konsoli programu Configuration Manager, aby można było dodać nową subskrypcję.

> [!NOTE]
> Można skonfigurować tylko jedną subskrypcję usługi Intune w czasie w hybrydowego zarządzania urządzeniami przenośnymi.

## <a name="how-to-delete-an-intune-subscription-from-configuration-manager"></a>Sposób usuwania subskrypcji usługi Intune z programu Configuration Manager

> [!IMPORTANT]
>  Całą zawartość w tym rejestracji użytkownika, zasady i wdrożeń aplikacji skonfigurowana dla urządzeń zarządzanych przez subskrypcję usługi Intune zostaną usunięte po usunięciu subskrypcji.

1.  W konsoli programu Configuration Manager, przejdź do **administracji** > **omówienie** > **usługi w chmurze** > **subskrypcje usługi Microsoft Intune**.

2.  Kliknij prawym przyciskiem myszy wymienionych **subskrypcję usługi Microsoft Intune**, a następnie kliknij przycisk **usunąć**.

3.   W kreatorze kliknij **usunąć subskrypcję usługi Microsoft Intune z programu Configuration Manager**, kliknij przycisk **dalej**, a następnie kliknij przycisk **dalej** ponownie, aby usunąć subskrypcję.


## <a name="how-to-remove-the-service-connection-point-role"></a>Jak usunąć rolę punktu połączenia usługi

1.  Przejdź do **administracji** > **omówienie** > **lokacji konfiguracji** > **serwery i role systemu lokacji**.

2.  Wybierz serwer, który hostuje rolę **Punkt połączenia z usługą** .

3.  Na liście **Role systemu lokacji** wybierz pozycję **Punkt połączenia z usługą**, a następnie na wstążce kliknij pozycję **Usuń rolę**. Potwierdź, że chcesz usunąć rolę. Punkt połączenia z usługą zostanie usunięty.

Teraz możesz utworzyć nowy punkt połączenia z usługą, dodać nową subskrypcję usługi Intune do programu Configuration Manager i ustawić program Configuration Manager jako urząd zarządzania urządzeniami przenośnymi.

## <a name="how-to-change-mdm-authority-to-intune"></a>Jak zmienić urząd zarządzania urządzeniami Przenośnymi do usługi Intune
Począwszy od 1610 wersji programu Configuration Manager i Microsoft Intune version 1705, można zmienić urzędu zarządzania urządzeniami Przenośnymi bez konieczności kontaktowania się Microsoft Support i bez konieczności wyrejestrowywania i Zarejestruj ponownie istniejących zarządzanych urządzeń. Aby uzyskać więcej informacji, zobacz [zmienić urzędu zarządzania urządzeniami Przenośnymi](/sccm/mdm/deploy-use/change-mdm-authority).
