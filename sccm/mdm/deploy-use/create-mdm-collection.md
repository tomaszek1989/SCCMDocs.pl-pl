---
title: Utwórz kolekcję usługi MDM
titleSuffix: Configuration Manager
description: Utwórz kolekcję usługi zarządzania urządzeniami Przenośnymi za pomocą programu System Center Configuration Manager.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: d1b4337f-85e8-45e6-8bbe-9f18b49041c7
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: d271499baf48364fe24a8961cae767c46d05a332
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="create-an-mdm-collection-with-system-center-configuration-manager-and-microsoft-intune"></a>Utwórz kolekcję usługi zarządzania urządzeniami Przenośnymi z programu System Center Configuration Manager i Microsoft Intune

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Kolekcja użytkownika programu Configuration Manager jest wymagany do określania użytkowników, którzy mogą rejestrować urządzenia w systemie zarządzania. Kolekcje użytkowników (zamiast kolekcji urządzeń) można używać tylko licencji usługi Intune nie zostały przypisane przez użytkownika.

> [!NOTE]
> Aby zarejestrować urządzenia w usłudze Intune, nie musisz przypisać licencje do użytkowników w portalu usługi Office 365 lub portalu usługi Azure Active Directory. W tym użytkowników w kolekcji, która pobiera skojarzone z subskrypcją usługi Intune (w [później krok](configure-intune-subscription.md)) to wszystko, która jest wymagana.

Do celów testowych można zdefiniować **reguły bezpośredniej** i dodać określonych użytkowników, którzy mogą rejestrować urządzenia. W konsoli programu Configuration Manager, należy wybrać, **zasoby i zgodność** > **kolekcje użytkowników**, kliknij przycisk **Home** kartę > **Utwórz** grupy, a następnie kliknij przycisk **Utwórz kolekcję użytkowników**. Do szerszego grona dystrybucji należy używać **zapytania reguł** do definiowania użytkowników. Aby uzyskać więcej informacji o kolekcjach, zobacz [sposobach tworzenia kolekcji](https://technet.microsoft.com/library/mt629371.aspx).

![Utwórz kolekcję użytkowników do zarządzania urządzeniami Przenośnymi](../media/mdm-create-user-collection.png)

> [!div class="button"]
[Następny krok >](confirm-dns.md)
