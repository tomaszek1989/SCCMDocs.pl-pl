---
title: Konfigurowanie spisu sprzętu
titleSuffix: Configuration Manager
description: Konfigurowanie spisu sprzętu dla wszystkich klientów lub kolekcji w programie System Center Configuration Manager.
ms.date: 02/22/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 0e45290e-f8f7-4335-801e-570225d12c2b
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 7b282fdb2f7cf3a200950484e4da5b9505c5b71c
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="how-to-configure-hardware-inventory-in-system-center-configuration-manager"></a>Jak skonfigurować spis sprzętu w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Ta procedura umożliwia skonfigurowanie domyślnych ustawień klienta dla spisu sprzętu i ma zastosowanie do wszystkich klientów w hierarchii. Aby te ustawienia miały zastosowanie tylko do niektórych komputerów, należy utworzyć niestandardowe ustawienie urządzenia klienta i przypisać je do kolekcji zawierającej urządzenia, które mają korzystać ze spisu sprzętu. Zobacz [sposób konfigurowania ustawień klienta w programie System Center Configuration Manager](../../../../core/clients/deploy/configure-client-settings.md).  

> [!NOTE]  
>  Jeśli urządzenie klienckie odbiera ustawienia spisu sprzętu z wielu zestawów ustawień klienta, klasy spisu sprzętu z wszystkich zestawów ustawień zostaną scalone, gdy klient zgłosi spis sprzętu.  

### <a name="to-configure-hardware-inventory"></a>Aby skonfigurować spis sprzętu  

1.  W konsoli programu Configuration Manager wybierz **administracji** > **ustawień klienta** > **domyślne ustawienia klienta**.  

4.  Na **Home** karcie **właściwości** grupy, wybierz **właściwości**.  

5.  W **ustawienia domyślne** oknie dialogowym wybierz **spisu sprzętu**.  

6.  Na liście **Ustawienia urządzenia** skonfiguruj następujące ustawienia:  

    -   **Włącz spis sprzętu na klientach** — wybierz tę opcję **True**.  

    -   **Harmonogram spisu sprzętu** — kliknij przycisk **harmonogram** Aby określić interwał, w którym klienci zbierają spis sprzętu.  

7.  Konfigurowanie innych [ustawień spisu sprzętu klienta](../../../../core/clients/deploy/about-client-settings.md#hardware-inventory) wymagany.  

Urządzenia klienckie zostaną skonfigurowane przy użyciu tych ustawień podczas następnego pobierania zasad klienta. Aby dowiedzieć się, jak zainicjować pobieranie zasad dla jednego klienta, zobacz [Jak zarządzać klientami w programie System Center Configuration Manager](../../../../core/clients/manage/manage-clients.md).  
