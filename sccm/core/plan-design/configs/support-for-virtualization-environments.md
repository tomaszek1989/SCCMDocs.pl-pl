---
title: Obsługa wirtualizacji
titleSuffix: Configuration Manager
description: Pobierz wymagania dotyczące instalowania programu System Center Configuration Manager klienta a role systemu lokacji w środowisku wirtualizacji.
ms.date: 1/12/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 1098e8c5-9676-4c2b-841b-ec88bd04e495
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 374a1643c5ea439a7406bbb1f6b53322caa50871
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="support-for-virtualization-environments-for-system-center-configuration-manager"></a>Obsługa środowisk wirtualizacji dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Program Configuration Manager obsługuje instalowanie klienta i ról systemu lokacji w obsługiwanych systemach operacyjnych działających jako maszyny wirtualne, w środowiskach wirtualizacji, które są wymienione w tym artykule. Ta obsługa istnieje, nawet jeśli host maszyny wirtualnej (środowisko wirtualizacji) nie jest obsługiwane jako klient lub serwer lokacji.  

 Na przykład jeśli używasz programu Microsoft Hyper-V Server 2012 do hostowania maszyny wirtualnej z systemem Windows Server 2012, można zainstalować klienta lub role systemu lokacji na maszynie wirtualnej (z systemem Windows Server 2012), ale nie na hoście (Microsoft Hyper-V Server 2012).  

|Środowisko wirtualizacji|  
|--------------------------------|  
|Windows Server 2008 R2|  
|Microsoft Hyper-V Server 2008 R2|  
|Windows Server 2012|  
|Microsoft Hyper-V Server 2012|  
|Windows Server 2012 R2|
|Windows Server 2016 <sup>(zobacz *uwagą 1*)</sup>|
|Microsoft Hyper-V Server 2016 <sup>(zobacz *uwagą 1*)|
-  *Należy pamiętać, 1*: Program Configuration Manager nie obsługuje [zagnieżdżonych wirtualizacji](https://technet.microsoft.com/windows-server-docs/compute/hyper-v/what-s-new-in-hyper-v-on-windows#a-namebkmknestedanested-virtualization-new), co jest nowego w systemie Windows Server 2016.


 Każdego komputera wirtualnego, którego używasz, musi spełnia lub przekracza sam sprzęt i wymagania dotyczące oprogramowania, których używasz dla komputera fizycznego programu Configuration Manager.  

 Aby zweryfikować, czy środowisko wirtualizacji jest obsługiwane dla programu Configuration Manager za pomocą programu weryfikacji wirtualizacji serwera i jego online Kreatora zasad obsługi programu wirtualizacji. Aby uzyskać więcej informacji na temat programu weryfikacji wirtualizacji serwera, zobacz [systemu Windows Server Virtualization Validation Program](https://www.windowsservercatalog.com/svvp.aspx).  

> [!NOTE]  
>  Menedżer konfiguracji nie obsługuje programu Virtual PC i Virtual Server systemów operacyjnych gościa, które są uruchamiane na komputerach Mac.  

Configuration Manager nie może zarządzać maszynami wirtualnymi, o ile nie są w trybie online. Nie można zaktualizować obrazu maszyny wirtualnej w trybie offline, nie można przeprowadzić spisu przy użyciu klienta programu Configuration Manager na komputerze hosta.  

Maszyny wirtualne nie są traktowane w specjalny sposób. Na przykład programu Configuration Manager może Określa, czy aktualizacja ma należy ponownie zastosować do obrazu maszyny wirtualnej, jeśli maszyna wirtualna została zatrzymana i uruchomiona ponownie bez zapisania stanu maszyny wirtualnej, do której zastosowano aktualizację.  

##  <a name="bkmk_Azure"></a> Maszyny wirtualne na platformie Microsoft Azure  
 Program Configuration Manager można uruchomić na maszynach wirtualnych platformy Azure tak samo, jak działa lokalnie w fizycznej sieci firmowej. Program Configuration Manager z maszyn wirtualnych platformy Azure w następujących scenariuszach:  

-   **Scenariusz 1:** Można uruchomić programu Configuration Manager na maszynie wirtualnej platformy Azure i przy jego użyciu zarządzać klientów, które są zainstalowane na innych maszynach wirtualnych platformy Azure.  

-   **Scenariusz 2:** Można uruchomić programu Configuration Manager na maszynie wirtualnej platformy Azure i przy jego użyciu zarządzać klientami, którzy nie działają na platformie Azure.  

-   **Scenariusz 3:** Różne role systemu lokacji programu Configuration Manager można uruchomić na maszynach wirtualnych Azure podczas uruchamiania innych ról w fizycznej sieci firmowej (z odpowiednią łącznością sieciową na potrzeby komunikacji).  

Te same wymagania programu System Center Configuration Manager dotyczące sieci, obsługiwane konfiguracje i wymagania sprzętowe, które dotyczą instalowania programu Configuration Manager lokalnie w fizycznej sieci firmowej również zastosować do instalacji na maszynach wirtualnych Azure.  

Aby uzyskać więcej informacji, zobacz [programu Configuration Manager na platformie Azure — często zadawane pytania](/sccm/core/understand/configuration-manager-on-azure).

> [!IMPORTANT]  
>  Lokacje programu Configuration Manager i klienci korzystający z maszyn wirtualnych platformy Azure obowiązują te same wymagania licencyjne co w przypadku instalacji lokalnych.  
