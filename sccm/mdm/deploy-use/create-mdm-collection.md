---
title: "Tworzenie kolekcji zarządzania urządzeniami Przenośnymi za pomocą programu System Center Configuration Manager | Dokumentacja firmy Microsoft"
description: "Utwórz kolekcję zarządzania urządzeniami Przenośnymi za pomocą programu System Center Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d1b4337f-85e8-45e6-8bbe-9f18b49041c7
caps.latest.revision: 18
caps.handback.revision: 0
author: mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: fabbcfd2d5656d4fa8cb87feffe87e17998df145
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="create-an-mdm-collection-with-system-center-configuration-manager-and-microsoft-intune"></a>Tworzenie kolekcji zarządzania urządzeniami Przenośnymi za pomocą programu System Center Configuration Manager i Microsoft Intune

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Kolekcji użytkowników programu Configuration Manager jest wymagane w celu określenia użytkowników, którzy mogą rejestrować urządzenia do systemu zarządzania. Kolekcje użytkowników (a nie kolekcji urządzeń) można używać tylko w przypadku, ponieważ Intune licencje są przypisywane przez użytkownika.

> [!NOTE]
> Aby zarejestrować urządzenia za pomocą usługi Intune, nie należy przypisywać licencji do użytkowników w portalu usługi Office 365 lub portalu usługi Azure Active Directory. W tym użytkownicy w kolekcji, która pobiera skojarzone z subskrypcją usługi Intune (w [później krok](configure-intune-subscription.md)) to wszystkie, które są wymagane.

Do celów testowych można skonfigurować **reguły bezpośredniej** i dodać określonych użytkowników, którzy mogą rejestrować urządzenia. W konsoli programu Configuration Manager athe, należy wybrać, **zasoby i zgodność** > **kolekcji użytkowników**, kliknij przycisk **Home** kartę > **Utwórz** grupy, a następnie kliknij przycisk **tworzenia kolekcji użytkowników**. Szerszy dystrybucji należy używać **kwerendy reguł** do definiowania użytkowników. Aby uzyskać więcej informacji na temat kolekcji, zobacz [tworzenie kolekcji](https://technet.microsoft.com/library/mt629371.aspx).

![Tworzenie kolekcji użytkowników do zarządzania urządzeniami Przenośnymi](../media/mdm-create-user-collection.png)

> [!div class="button"]
[Następny krok >](confirm-dns.md)

