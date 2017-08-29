---
title: "Utwórz kolekcję usługi zarządzania urządzeniami Przenośnymi za pomocą programu System Center Configuration Manager | Dokumentacja firmy Microsoft"
description: "Utwórz kolekcję usługi zarządzania urządzeniami Przenośnymi za pomocą programu System Center Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d1b4337f-85e8-45e6-8bbe-9f18b49041c7
caps.latest.revision: "18"
caps.handback.revision: "0"
author: mtillman
ms.author: mtillman
manager: angrobe
ms.openlocfilehash: 43316e4915b27aaeca563eaf52b51f053a839222
ms.sourcegitcommit: 974fbc4408028c8be28911e5cd646efcf47c7f15
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/28/2017
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
