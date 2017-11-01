---
title: "Utwórz kolekcję usługi MDM"
titleSuffix: Configuration Manager
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
author: dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: f8b865c48f6c69fe1cfd7221273b09f5557075e9
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
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
