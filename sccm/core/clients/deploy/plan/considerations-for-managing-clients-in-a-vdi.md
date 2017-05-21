---
title: "Zarządzanie klientem infrastruktury pulpitu wirtualnego (VDI) | Dokumentacja firmy Microsoft "
description: "Zarządzanie klientami programu System Center Configuration Manager w infrastrukturze pulpitu wirtualnego (VDI)."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: abd45393-d84e-4583-bc80-74bbb3709577
caps.latest.revision: 7
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: d73daf6427b8c58d21d579f3b41df513cc3e3b0b
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="considerations-for-managing-system-center-configuration-manager-clients--in-a-virtual-desktop-infrastructure-vdi"></a>Uwagi dotyczące zarządzania klientami programu System Center Configuration Manager w infrastrukturze pulpitu wirtualnego (VDI)

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

System Center Configuration Manager obsługuje instalowanie klienta programu Configuration Manager w następujących scenariuszach infrastruktury pulpitu wirtualnego (VDI):  

-   **Osobiste maszyny wirtualne** -osobiste maszyny wirtualne są zazwyczaj stosowane, gdy chcesz upewnić się, że dane użytkownika i ustawienia są przechowywane na maszynie wirtualnej między sesjami.  

-   **Sesje usług pulpitu zdalnego** -usług pulpitu zdalnego umożliwiają uruchomienie na serwerze wielu równoczesnych sesji klienta. Użytkownicy mogą połączyć się z sesją i następnie uruchamiać aplikacje na tym serwerze.  

-   **Maszyny wirtualne w puli** -maszyny wirtualne w puli nie są zachowywane między sesjami. Po zamknięciu sesji wszystkie dane i ustawienia zostaną odrzucone. Maszyny wirtualne w puli są przydatne, gdy nie można użyć usług pulpitu zdalnego, ponieważ wymagana aplikacja biznesowa nie można uruchomić na serwerze systemu Windows obsługującego sesji klienta.  

 Poniższa tabela zawiera uwagi dotyczące zarządzania klientem programu Configuration Manager w infrastrukturze pulpitu wirtualnego.  

|Typ maszyny wirtualnej|Uwagi|  
|--------------------------|--------------------|  
|Osobiste maszyny wirtualne|Menedżer konfiguracji traktuje osobiste maszyny wirtualne tak samo jak na komputerze fizycznym. Klient programu Configuration Manager można preinstalowany w obrazie maszyny wirtualnej lub wdrożony po udostępnieniu maszyny wirtualnej.|  
|Usługi pulpitu zdalnego|Nie zainstalowano klienta programu Configuration Manager dla indywidualnych sesji pulpitu zdalnego. Zamiast tego klient jest instalowany tylko jeden raz na serwerze usług pulpitu zdalnego. Wszystkie funkcje programu Configuration Manager może służyć na serwerze usług pulpitu zdalnego.|  
|Maszyny wirtualne w puli|Po zlikwidowaniu maszyny wirtualnej jest likwidowany, wszelkie zmiany wprowadzone za pomocą Menedżera konfiguracji zostaną utracone.<br /><br /> Dane zwrócone z funkcji programu Configuration Manager, takie jak spis sprzętu, zapasy oprogramowania i pomiar użytkowania oprogramowania mogą nie odpowiadać potrzebom użytkownika jako maszyna wirtualna może działać tylko przez krótki czas. Należy rozważyć wykluczenie maszyny wirtualne w puli z inwentaryzacji.|  

 Wirtualizacja obsługuje uruchamianie wielu klientów programu Configuration Manager na tym samym komputerze fizycznym, dlatego wiele operacji klienta ma wbudowane losowe opóźnienie dla zaplanowanych akcji, takich jak sprzętu i skanuje spisu oprogramowania, ochrony przed złośliwym oprogramowaniem, instalacje oprogramowania i aktualizacji oprogramowania skanowania. To opóźnienie pomaga w rozłożeniu transmisji danych i przetwarzania Procesora dla komputera, który ma wiele maszyn wirtualnych z systemem klienta programu Configuration Manager.  

> [!NOTE]  
>  Z wyjątkiem klientów Windows Embedded, które są w trybie obsługi klienci programu Configuration Manager, które nie są uruchomione w zwirtualizowanych środowiskach używają tego losowego opóźnienia. W przypadku wielu wdrożonych klientów to zachowanie zapobiega powstawianiu szczytów przepustowości sieci i zmniejsza wymaganie przetwarzania przez procesor CPU w systemach lokacji programu Configuration Manager, takich jak serwer lokacji i punktu zarządzania. Interwał opóźnienia zależy od możliwości programu Configuration Manager.  
>   
>  Opóźnienie losowe jest domyślnie wyłączona dla wymaganych aktualizacji oprogramowania i wdrożeń aplikacji wymagane przy użyciu następującego ustawienia klienta: **Agent komputera**: **Wyłącz losowe generowanie terminu ostatecznego**.

