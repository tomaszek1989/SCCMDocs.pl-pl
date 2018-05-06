---
title: 'Instalowanie ról do lokalnego zarządzania urządzeniami Przenośnymi '
titleSuffix: Configuration Manager
description: Instalowanie ról systemu lokacji do zarządzania urządzeniami przenośnymi lokalnymi w programie System Center Configuration Manager.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: c3cf9f64-c2b9-4ace-9527-2aba6d4eef04
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: dc3efe5438d583bc5d850261a1bb80253a608c6c
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="install-site-system-roles-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>Instalowanie ról systemu lokacji do zarządzania urządzeniami przenośnymi lokalnymi w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

System Center Configuration Manager na\-lokalne zarządzanie urządzeniami przenośnymi wymaga następujących ról systemu lokacji w infrastrukturze lokacji programu Configuration Manager:  

-   Punkt rejestracji  

-   Punkt proxy rejestracji  

-   Punkt dystrybucji  

-   Punkt zarządzania urządzeniami  

-   Punkt połączenia usługi  

 Jeśli dodajesz na\-lokalne zarządzanie urządzeniami przenośnymi dla organizacji, która zawiera większość komputerów i urządzeń zarządzanych za pomocą oprogramowania klienckiego programu Configuration Manager może być większość ról systemu lokacji, które są już zainstalowane w ramach istniejącej infrastruktury. Jeśli nie, zobacz [Dodaj role systemu lokacji dla programu System Center Configuration Manager](../../core/servers/deploy/configure/add-site-system-roles.md) pełne informacje dotyczące sposobu dodawania ich do swojej witryny.  

> [!NOTE]  
>  Użycie replik baz danych z Twojej roli systemu lokacji punktu urządzenia zarządzania nowo zarejestrowane urządzenia początkowo nie będą mogły połączyć się z punktem zarządzania urządzeniami, dopóki repliki bazy danych nie zsynchronizuje się z. Ten błąd połączenia występuje, ponieważ replika bazy danych nie ma informacji o nowo zarejestrowanym urządzeniu niezbędnych do pomyślnego nawiązania połączenia. Repliki są synchronizowane co 5 minut, urządzenia będą mogły nawiązać połączenia przez pierwsze 5 minut po rejestracji (zwykle 2 próby połączenia), po którym połączenie zostanie nawiązane pomyślnie.  

 Określa, czy używasz istniejących ról systemu lokacji lub dodajesz nowe, należy je skonfigurować ma być używany do zarządzania nowoczesnymi urządzeniami. Wykonaj poniższe kroki, aby skonfigurować punkt dystrybucji i punkt zarządzania urządzeniem do prawidłowego działania dla w\-lokalnych zarządzanie urządzeniami przenośnymi:  

> [!NOTE]  
>  Bieżąca gałąź programu Configuration Manager obsługuje tylko połączenia intranetowe z urządzeń do punktów dystrybucji i punktów zarządzania urządzeniem na\-lokalnych zarządzanie urządzeniami przenośnymi. Jednak w przypadku zarządzania także komputerami Mac OS X, klienci wymagają wymaga połączenia internetowego z tymi rolami systemu lokacji. W takim przypadku podczas konfigurowania właściwości punktu dystrybucji i punkt zarządzania urządzeniami należy używać **Zezwalaj na połączenia intranetowe i internetowe** zamiast tego ustawienia.  

### <a name="to-configure-site-system-roles-to-manage-modern-devices"></a>Aby skonfigurować role systemu lokacji do zarządzania nowoczesnymi urządzeniami:  

1.  W konsoli programu Configuration Manager kliknij **administracji** > **omówienie** > **konfiguracja lokacji** > **serwery i role systemu lokacji**.  

2.  Wybierz serwer systemu lokacji z punktem dystrybucji lub punkt zarządzania urządzeniem, aby skonfigurować, otwórz właściwości **systemu lokacji** i upewnij się, że ma ona niego nazwę FQDN. Kliknij przycisk **OK**.  

3.  Roli systemu lokacji punktu dystrybucji Otwórz właściwości. Na karcie Ogólne upewnij się, **HTTPS** jest zaznaczone i wybierz **Zezwalaj tylko na połączenia intranetowe**.  

     Jeśli zarządzasz także osobno komputerami Mac z klienta programu Configuration Manager, użyj **Zezwalaj na połączenia intranetowe i internetowe** zamiast tego.  

    > [!NOTE]  
    >  Punkty dystrybucji skonfigurowane dla połączeń intranetowych wymagają granic lokacji można skonfigurować dla nich. Bieżąca gałąź programu Configuration Manager obsługuje tylko granice zakresów IPv4 dla na\-lokalnych zarządzanie urządzeniami przenośnymi. Aby uzyskać więcej informacji o konfigurowaniu granic lokacji, zobacz [Definiowanie granic lokacji i grup granic dla programu System Center Configuration Manager](../../core/servers/deploy/configure/define-site-boundaries-and-boundary-groups.md).  

4.  Kliknij pole wyboru obok pozycji **Zezwalaj urządzeniom przenośnym na łączenie z tym punktem dystrybucji**, a następnie kliknij przycisk **OK**.  

5.  Otwórz właściwości zarządzania roli systemu lokacji punktu. Na karcie Ogólne upewnij się, **HTTPS** jest zaznaczone i wybierz **Zezwalaj tylko na połączenia intranetowe**.  

     Jeśli zarządzasz także osobno komputerami Mac z klienta programu Configuration Manager, użyj **Zezwalaj na połączenia intranetowe i internetowe** zamiast tego.  

6.  Kliknij pole wyboru obok pozycji **Zezwalaj urządzeniom przenośnym i komputerom Mac na korzystanie z tego punktu zarządzania**. Kliknij przycisk **OK**.  

     W praktyce zmienia to punkt zarządzania w punkt zarządzania urządzeniem.  

 Po dodaniu ról systemu lokacji i skonfigurowane do zarządzania nowoczesnymi urządzeniami, należy skonfigurować serwery hostujące role jako zaufane punkty końcowe dla rejestracji i komunikacji z zarządzanymi urządzeniami. Zobacz [Konfigurowanie certyfikatów dla zaufanej komunikacji na potrzeby zarządzania urządzeniami przenośnymi lokalnymi w programie System Center Configuration Manager](../../mdm/get-started/set-up-certificates-on-premises-mdm.md) Aby uzyskać więcej informacji.  
