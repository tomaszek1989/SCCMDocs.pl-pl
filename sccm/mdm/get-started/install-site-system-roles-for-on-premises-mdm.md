---
title: "Instalowanie ról dla lokalnych MDM — Configuration Manager | Dokumentacja firmy Microsoft"
description: "Zainstaluj role systemu lokacji dla zarządzania urządzeniami przenośnymi lokalnie w programie System Center Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: c3cf9f64-c2b9-4ace-9527-2aba6d4eef04
caps.latest.revision: 9
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: 4913606e2f8a36e0004f711b24ecd836d0485124
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="install-site-system-roles-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>Instalowanie ról systemu lokacji dla zarządzania urządzeniami przenośnymi lokalnie w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

System Center Configuration Manager na\-lokalnego zarządzania urządzeniami przenośnymi wymaga następujących ról systemu lokacji w infrastrukturze lokacji programu Configuration Manager:  

-   Punkt rejestracji  

-   Punkt proxy rejestracji  

-   Punkt dystrybucji  

-   Punkt zarządzania urządzeniami  

-   Punkt połączenia usługi  

 W przypadku dodawania na\-lokalnego zarządzania urządzeniami przenośnymi dla organizacji mającej większości komputerami i urządzeniami zarządzanymi przy użyciu oprogramowania klienckiego programu Configuration Manager może być większość ról systemu lokacji, które są już zainstalowane w ramach istniejącej infrastruktury. Jeśli nie, zobacz [Dodaj role systemu lokacji dla programu System Center Configuration Manager](../../core/servers/deploy/configure/add-site-system-roles.md) pełne informacje dotyczące sposobu dodawania ich do witryny.  

> [!NOTE]  
>  Użycie replik baz danych z z rolą systemu lokacji punktu urządzenia zarządzanie nowo zarejestrowane urządzenia początkowo nie będzie łączył punktu zarządzania urządzeniami do momentu repliki bazy danych synchronizuje się z nim. Ten błąd połączenia występuje, ponieważ repliki bazy danych nie ma informacji o nowo zarejestrowane urządzenia niezbędne do pomyślnego połączenia. Repliki są synchronizowane co 5 minut, więc urządzenia nie będzie można połączyć z pierwszym 5 minut po rejestracji (zwykle 2 próby połączenia), po upływie którego urządzenia będą łączyć pomyślnie.  

 Czy używasz istniejących ról systemu lokacji lub dodaje nowe, należy skonfigurować je służący do zarządzania nowoczesnych urządzeń. Wykonaj poniższe kroki, aby skonfigurować punkt dystrybucji i punktu zarządzania urządzeniami do poprawnego dla na\-lokalnych zarządzanie urządzeniami przenośnymi:  

> [!NOTE]  
>  Bieżącej gałęzi programu Configuration Manager obsługuje tylko połączenia intranetu z urządzeń do punktów dystrybucji i punkty zarządzania urządzeniami na\-lokalnych zarządzanie urządzeniami przenośnymi. Jednak również w przypadku zarządzania komputerami Mac OS X, tych klientów wymaga połączenia internetowe do tych ról systemu lokacji. W takim przypadku podczas konfigurowania właściwości punktu dystrybucji i punktu zarządzania urządzeniami, należy użyć **dozwolone połączenia sieci intranet i Internetu** zamiast tego ustawienia.  

### <a name="to-configure-site-system-roles-to-manage-modern-devices"></a>Aby skonfigurować role systemu lokacji do zarządzania nowoczesnych urządzeń:  

1.  W konsoli programu Configuration Manager kliknij **Administracja** > **Przegląd** > **konfiguracja lokacji** > **serwery i role systemu lokacji**.  

2.  Serwer systemu lokacji wybierz punkt dystrybucji lub punktu zarządzania urządzeniami chcesz skonfigurować, otwórz właściwości **systemu lokacji** i upewnij się, ma ona określone nazwy FQDN. Kliknij przycisk **OK**.  

3.  Otwórz okno właściwości dystrybucji punktu Rola systemu lokacji. Na karcie Ogólne, upewnij się, **HTTPS** jest zaznaczone i wybierz opcję **zezwala na połączenia intranetowe**.  

     Jeśli również osobno w przypadku zarządzania komputerami Mac za pomocą klienta programu Configuration Manager, użyj **dozwolone połączenia sieci intranet i Internetu** zamiast tego.  

    > [!NOTE]  
    >  Punkty dystrybucji skonfigurowane dla połączeń w intranecie wymagają granic lokacji do skonfigurowania dla nich. Bieżącej gałęzi programu Configuration Manager obsługuje tylko IPv4 granice zakresu na\-lokalnych zarządzanie urządzeniami przenośnymi. Aby uzyskać więcej informacji na temat konfigurowania granic lokacji, zobacz [zdefiniować granice lokacji i grup granic dla programu System Center Configuration Manager](../../core/servers/deploy/configure/define-site-boundaries-and-boundary-groups.md).  

4.  Kliknij pole wyboru obok **Zezwalaj urządzeniom przenośnym na połączenia z tym punktem dystrybucji**, a następnie kliknij przycisk **OK**.  

5.  Otwórz okno właściwości w celu zarządzania punktu Rola systemu lokacji. Na karcie Ogólne, upewnij się, **HTTPS** jest zaznaczone i wybierz opcję **zezwala na połączenia intranetowe**.  

     Jeśli również osobno w przypadku zarządzania komputerami Mac za pomocą klienta programu Configuration Manager, użyj **dozwolone połączenia sieci intranet i Internetu** zamiast tego.  

6.  Kliknij pole wyboru obok **Zezwalaj na urządzeniach przenośnych i komputerów Mac na użycie tego punktu zarządzania**. Kliknij przycisk **OK**.  

     W praktyce pozwala punkt zarządzania do punktu zarządzania urządzeniami.  

 Po dodaniu ról systemu lokacji i skonfigurowane do zarządzania nowoczesnych urządzeń, następnie należy skonfigurować serwery obsługujące ról jako zaufanych punktów końcowych rejestrowania i komunikacji z zarządzanych urządzeń. Zobacz [Konfigurowanie certyfikatów zaufanych komunikacji dla lokalnego zarządzania urządzeniami przenośnymi w programie System Center Configuration Manager](../../mdm/get-started/set-up-certificates-on-premises-mdm.md) uzyskać więcej informacji.  

