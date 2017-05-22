---
title: "Konfigurowanie zarządzania energią | Dokumentacja firmy Microsoft"
description: "Konfigurowanie zarządzania zużyciem energii w programie System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 435c923c-ea30-4dce-8afd-48962ed85502
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 1a4a9da88caba55d9e340c7fb1f31f4e3b957f3e
ms.openlocfilehash: e111ac2545dd9e0b96a50c10246bb75d286a737a
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="configuring-power-management-in-system-center-configuration-manager"></a>Konfigurowanie zarządzania zużyciem energii w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Przed użyciem zarządzania zużyciem energii w programie System Center Configuration Manager, należy wykonać następujące kroki konfiguracji.  

## <a name="enable-and-configure-power-management-client-settings"></a>Włączanie i konfigurowanie ustawień klienta dla zarządzania energią  
 Ta procedura umożliwia skonfigurowanie domyślnych ustawień klienta dla zarządzania energią i dotyczy wszystkich komputerów w hierarchii. Jeśli te ustawienia mają być stosowane tylko dla niektórych komputerów, utwórz niestandardowe ustawienie klienta urządzenia i przypisz je do kolekcji zawierającej komputery, na których chcesz zarządzać energią. Aby uzyskać więcej informacji na temat tworzenia niestandardowych ustawień urządzenia, zobacz [sposób konfigurowania ustawień klienta w programie System Center Configuration Manager](../../../../core/clients/deploy/configure-client-settings.md).  

#### <a name="to-enable-power-management-and-configure-client-settings"></a>Włączanie zarządzania energią i konfigurowanie ustawień klienta  

1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

2.  W obszarze roboczym **Administracja** kliknij przycisk **Ustawienia klienta**.  

3.  Kliknij przycisk **Ustawienia domyślne klienta**.  

4.  Na karcie **Narzędzia główne** w grupie **Właściwości** kliknij przycisk **Właściwości**.  

5.  W oknie dialogowym **Domyślne ustawienia klienta** kliknij pozycję **Zarządzanie energią**.  

6.  Skonfiguruj następującą wartość dla ustawień klienta zarządzania energią:  

    -   **Zezwalaj na zarządzanie zasilaniem urządzeń** — z listy rozwijanej wybierz pozycję **Prawda** , aby włączyć zarządzanie energią.  

7.  Skonfiguruj wymagane ustawienia klienta. Lista ustawień klienta zarządzania energią, które można skonfigurować, zobacz [zarządzania energią](../../../../core/clients/deploy/about-client-settings.md#power-management) w sekcji [informacje o ustawieniach klienta w programie System Center Configuration Manager](../../../../core/clients/deploy/about-client-settings.md) tematu.  

8.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe **Ustawienia domyślne klienta** .  

 Klienci zostaną skonfigurowani przy użyciu tych ustawień podczas następnego pobierania zasad klienta. Aby dowiedzieć się, jak zainicjować pobieranie zasad dla jednego klienta, zobacz [Jak zarządzać klientami w programie System Center Configuration Manager](../../../../core/clients/manage/manage-clients.md).  

## <a name="exclude-computers-from-power-management"></a>Wykluczanie komputerów z zarządzania energią  
 Możesz skonfigurować kolekcje komputerów w taki sposób, aby nie odbierały ustawień zarządzania energią. Jeśli komputer jest elementem członkowskim kolekcji, która jest wykluczona z odbierania ustawień zarządzania energią, dla tego komputera nie zostaną zastosowane ustawienia zarządzania energią, nawet jeśli jest on członkiem innej kolekcji, dla której są stosowane ustawienia zarządzania energią.  

 Możliwe powody wykluczenia komputerów z zarządzania energią:  

-   Wymagania biznesowe nakazują, aby komputery były włączone przez cały czas.  

-   Masz utworzoną kontrolną kolekcję komputerów, dla których nie chcesz stosować ustawień zarządzania energią.  

-   Niektóre z komputerów nie mogą zastosować ustawień zarządzania energią.  

-   Chcesz wykluczyć komputery z systemem Windows Server z zarządzania energią.  

> [!NOTE]  
>  Jeśli opcja **Zezwalaj użytkownikom na wykluczanie swoich urządzeń z zarządzania zasilaniem** jest skonfigurowana w ustawieniach klienta, użytkownicy mogą wykluczyć własne komputery z zarządzania energią za pomocą Centrum oprogramowania.  

 Aby dowiedzieć się, które komputery zostały wykluczone z zarządzania energią, uruchom raport **Wykluczone komputery**. Więcej informacji na temat tego raportu można znaleźć w temacie [wykluczone komputery](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md#BKMK_Excluded) w [monitora i planu na potrzeby zarządzania zużyciem energii w programie System Center Configuration Manager](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md).  

> [!IMPORTANT]  
>  W przypadku ustawień zasilania zastosowanych na komputerach z systemem Windows XP lub Windows Server 2003 nie są przywracane oryginalne wartości, nawet jeśli komputer zostanie wykluczony z zarządzania energią. W nowszych wersjach systemu Windows wykluczenie komputera z zarządzania energią powoduje przywrócenie oryginalnych wartości wszystkich ustawień zasilania. Nie można przywrócić oryginalnych wartości pojedynczych ustawień zasilania.  

#### <a name="to-exclude-a-collection-of-computers-from-power-management"></a>Wykluczanie kolekcji komputerów z zarządzania energią  

1.  W konsoli programu Configuration Manager kliknij przycisk **Zasoby i zgodność**.  

2.  W obszarze roboczym **Zasoby i zgodność** kliknij przycisk **Kolekcje urządzeń**.  

3.  Na liście **Kolekcje urządzeń** wybierz kolekcję, którą chcesz wykluczyć z zarządzania energią, a następnie na karcie **Narzędzia główne** w grupie **Właściwości** kliknij pozycję **Właściwości**.  

4.  W **zarządzania energią** na karcie *< nazwa kolekcji\>***właściwości** okno dialogowe, wybierz opcję **nigdy nie dotyczą ustawienia zarządzania zasilaniem komputerów w tej kolekcji**.  

5.  Kliknij przycisk **OK** zamknąć *< nazwa kolekcji\>***właściwości** okno dialogowe i zapisać ustawienia.  
