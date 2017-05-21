---
title: "Konfigurowanie spisu sprzętu | Dokumentacja firmy Microsoft"
description: "Konfigurowanie spisu sprzętu dla wszystkich klientów lub kolekcję w programie System Center Configuration Manager."
ms.custom: na
ms.date: 02/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 0e45290e-f8f7-4335-801e-570225d12c2b
caps.latest.revision: 5
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: 0baadb95ec8dbb945f1a611ebb95a03cec3199bd
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-configure-hardware-inventory-in-system-center-configuration-manager"></a>Jak skonfigurować spis sprzętu w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Ta procedura umożliwia skonfigurowanie domyślnych ustawień klienta dla spisu sprzętu i ma zastosowanie do wszystkich klientów w hierarchii. Aby te ustawienia miały zastosowanie tylko do niektórych komputerów, należy utworzyć niestandardowe ustawienie urządzenia klienta i przypisać je do kolekcji zawierającej urządzenia, które mają korzystać ze spisu sprzętu. Zobacz [sposób konfigurowania ustawień klienta w programie System Center Configuration Manager](../../../../core/clients/deploy/configure-client-settings.md).  

> [!NOTE]  
>  Jeśli urządzenie klienckie odbiera ustawienia spisu sprzętu z wielu zestawów ustawień klienta, klasy spisu sprzętu z wszystkich zestawów ustawień zostaną scalone, gdy klient zgłosi spis sprzętu.  

### <a name="to-configure-hardware-inventory"></a>Aby skonfigurować spis sprzętu  

1.  W konsoli programu Configuration Manager wybierz **Administracja** > **ustawień klienta** > **domyślne ustawienia klienta**.  

4.  Na **Home** w karcie **właściwości** grupy, wybierz **właściwości**.  

5.  W **ustawienia domyślne** okno dialogowe Wybierz **spisu sprzętu**.  

6.  Na liście **Ustawienia urządzenia** skonfiguruj następujące ustawienia:  

    -   **Włącz zapasy sprzętu na klientach** — wybierz **True**.  

    -   **Harmonogram spisu sprzętu** -kliknij **harmonogram** Aby określić interwał, w którym klienci zbierania spisu sprzętu.  

7.  Konfigurowanie innych [ustawienia klienta zapasów sprzętu](../../../../core/clients/deploy/about-client-settings.md#hardware-inventory) potrzebne.  

Urządzenia klienckie zostaną skonfigurowane przy użyciu tych ustawień podczas następnego pobierania zasad klienta. Aby dowiedzieć się, jak zainicjować pobieranie zasad dla jednego klienta, zobacz [Jak zarządzać klientami w programie System Center Configuration Manager](../../../../core/clients/manage/manage-clients.md).  

