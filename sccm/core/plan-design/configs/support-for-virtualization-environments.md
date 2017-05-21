---
title: "Obsługa wirtualizacji | Dokumentacja firmy Microsoft"
description: "Pobierz wymagania dotyczące instalowania ról systemu lokacji i klientów programu System Center Configuration Manager w środowisku wirtualizacji."
ms.custom: na
ms.date: 1/12/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1098e8c5-9676-4c2b-841b-ec88bd04e495
caps.latest.revision: 6
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 10192da2633555ab3bae60dbb1156d1926f9a4a0
ms.openlocfilehash: b49bd179da850cee35b2487a353bb1788df03d58
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="support-for-virtualization-environments-for-system-center-configuration-manager"></a>Obsługa wirtualizacji środowiska programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Program Configuration Manager obsługuje instalowanie klienta i role systemu lokacji na obsługiwane systemy operacyjne, które działają jako maszyn wirtualnych w środowiskach wirtualizacji, które są wymienione w tym artykule. Ta obsługa istnieje, nawet jeśli host maszyny wirtualnej (środowisko wirtualizacji) nie jest obsługiwane jako klient lub serwer lokacji.  

 Na przykład jeśli używasz Microsoft Hyper-V Server 2012 do hostowania maszyny wirtualnej z systemem Windows Server 2012, należy zainstalować role systemu lokacji lub klienta na maszynie wirtualnej (Windows Server 2012), ale nie na hoście (Microsoft Hyper-V Server 2012).  

|Środowisko wirtualizacji|  
|--------------------------------|  
|Windows Server 2008 R2|  
|Microsoft Hyper-V Server 2008 R2|  
|Windows Server 2012|  
|Microsoft Hyper-V Server 2012|  
|Windows Server 2012 R2|
|Windows Server 2016 <sup>(zobacz *Uwaga 1*)</sup>|
|Microsoft Hyper-V Server 2016 <sup>(zobacz *Uwaga 1*)|
-  *Uwaga 1*: Menedżer konfiguracji nie obsługuje [zagnieżdżonych wirtualizacji](https://technet.microsoft.com/windows-server-docs/compute/hyper-v/what-s-new-in-hyper-v-on-windows#a-namebkmknestedanested-virtualization-new), co jest nowego w usłudze Windows Server 2016.


 Każdego komputera wirtualnego, którego używasz musi spełniać lub przekroczenia tego samego sprzętu i wymagania dotyczące oprogramowania, których używasz dla komputera fizycznego programu Configuration Manager.  

 Można sprawdzić, czy środowiska wirtualizacji jest obsługiwana dla programu Configuration Manager za pomocą programu weryfikacji wirtualizacji serwera i jego online Kreatora zasad pomocy technicznej programu wirtualizacji. Aby uzyskać więcej informacji o programie weryfikacji wirtualizacji serwera, zobacz [Program weryfikacji wirtualizacja systemu Windows Server](https://www.windowsservercatalog.com/svvp.aspx).  

> [!NOTE]  
>  Menedżer konfiguracji nie obsługuje Virtual PC lub Virtual Server systemów operacyjnych gościa, uruchamiane na komputerach Mac.  

Configuration Manager nie może zarządzać maszyn wirtualnych, o ile nie są w trybie online. Nie można zaktualizować obrazu offline maszyny wirtualnej ani spisu można zbierać za pomocą klienta programu Configuration Manager na komputerze-hoście.  

Maszyny wirtualne nie są traktowane w specjalny sposób. Na przykład programu Configuration Manager może Określa, czy aktualizacja ma ponownego zastosowania do obrazu maszyny wirtualnej, jeśli maszyna wirtualna została zatrzymana i ponownie uruchomiony bez zapisywania stanu maszyny wirtualnej, do którego zastosowano aktualizację.  

##  <a name="bkmk_Azure"></a> Maszyny wirtualne na platformie Microsoft Azure  
 Program Configuration Manager można uruchomić na maszynach wirtualnych platformy Azure tak, jak działa lokalnie w firmowej sieci fizycznej. Program Configuration Manager z maszyny wirtualnej platformy Azure w następujących scenariuszach:  

-   **Scenariusz 1:** Można uruchomić program Configuration Manager na maszynie wirtualnej platformy Azure i korzystać z niego do zarządzania klientami, które są zainstalowane na inne maszyny wirtualne platformy Azure.  

-   **Scenariusz 2:** Można uruchomić program Configuration Manager na maszynie wirtualnej platformy Azure i korzystać z niego do zarządzania klientami, które nie są uruchomione na platformie Azure.  

-   **Scenariusz 3:** Różne role systemu lokacji programu Configuration Manager można uruchomić na maszynach wirtualnych Azure podczas wykonywania innych ról w sieci firmowej fizycznej (z połączeniem sieciowym odpowiednie dla komunikacji).  

Takie same wymagania programu System Center Configuration Manager w sieci, obsługiwane konfiguracje i wymagania sprzętowe, które dotyczą Instalowanie programu Configuration Manager lokalnych w sieci firmowej fizycznego dotyczą również instalacji na maszynach wirtualnych platformy Azure.  

Aby uzyskać więcej informacji, zobacz [programu Configuration Manager na platformie Azure — często zadawane pytania](/sccm/core/understand/configuration-manager-on-azure).

> [!IMPORTANT]  
>  Lokacje programu Configuration Manager i klientów uruchamianych na maszynach wirtualnych Azure podlegają licencją lokalnej instalacji.  

