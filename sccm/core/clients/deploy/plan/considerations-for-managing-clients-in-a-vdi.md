---
title: "Zarządzanie klientem infrastruktury pulpitów wirtualnych (VDI) | Dokumentacja firmy Microsoft "
description: "Zarządzanie klientami programu System Center Configuration Manager w infrastrukturze pulpitu wirtualnego (VDI)."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: abd45393-d84e-4583-bc80-74bbb3709577
caps.latest.revision: "7"
caps.handback.revision: "0"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: d73daf6427b8c58d21d579f3b41df513cc3e3b0b
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="considerations-for-managing-system-center-configuration-manager-clients--in-a-virtual-desktop-infrastructure-vdi"></a>Uwagi dotyczące zarządzania klientami programu System Center Configuration Manager w infrastrukturze pulpitu wirtualnego (VDI)

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

System Center Configuration Manager obsługuje instalowanie klienta programu Configuration Manager w następujących scenariuszach infrastruktury pulpitu wirtualnego (VDI):  

-   **Osobiste maszyny wirtualne** — osobiste maszyny wirtualne są zazwyczaj stosowane, gdy chce mieć pewność, że dane użytkownika i ustawienia są przechowywane na maszynie wirtualnej między sesjami.  

-   **Sesje usług pulpitu zdalnego** -usług pulpitu zdalnego umożliwia serwerowi wielu równoczesnych sesji klienta. Użytkownicy mogą połączyć się z sesją i następnie uruchamiać aplikacje na tym serwerze.  

-   **Maszyny wirtualne w puli** — maszyny wirtualne w puli nie są zachowywane między sesjami. Po zamknięciu sesji wszystkie dane i ustawienia zostaną odrzucone. Maszyny wirtualne w puli są przydatne, gdy nie można użyć usług pulpitu zdalnego, ponieważ wymagana aplikacja biznesowa nie można uruchomić na serwerze systemu Windows obsługującego sesji klienta.  

 Poniższa tabela zawiera uwagi dotyczące zarządzania klientem programu Configuration Manager w infrastrukturze pulpitu wirtualnego.  

|Typ maszyny wirtualnej|Uwagi|  
|--------------------------|--------------------|  
|Osobiste maszyny wirtualne|Configuration Manager traktuje osobiste maszyny wirtualne tak samo jak fizyczny komputer. Klienta programu Configuration Manager może być preinstalowany w obrazie maszyny wirtualnej lub wdrożony po udostępnieniu maszyny wirtualnej.|  
|Usługi pulpitu zdalnego|Nie zainstalowano klienta programu Configuration Manager dla indywidualnych sesji pulpitu zdalnego. Zamiast tego klient jest instalowany tylko raz na serwerze usług pulpitu zdalnego. Wszystkie funkcje programu Configuration Manager może służyć na serwerze usług pulpitu zdalnego.|  
|Maszyny wirtualne w puli|Po zlikwidowaniu maszyny wirtualnej jest likwidowany, wszystkie zmiany wprowadzone przy użyciu programu Configuration Manager zostaną utracone.<br /><br /> Dane zwrócone z funkcji programu Configuration Manager, takie jak spis sprzętu, zapasy oprogramowania i pomiar użytkowania oprogramowania mogą nie odpowiadać potrzebom użytkownika ponieważ maszyna wirtualna może działać tylko przez krótki czas. Należy rozważyć wykluczenie maszyny wirtualne w puli z inwentaryzacji.|  

 Wirtualizacja obsługuje uruchamianie wielu klientów programu Configuration Manager na tym samym komputerze fizycznym, wiele operacji klienta ma wbudowane losowe opóźnienie dla zaplanowanych akcji, takich jak sprzętu i skanuje spisu oprogramowania i ochrony przed złośliwym kodem, instalacje oprogramowania i aktualizacji oprogramowania skanowania. To opóźnienie pomaga w rozłożeniu transmisji danych i przetwarzania procesora CPU dla komputera, który ma wiele maszyn wirtualnych z klientem programu Configuration Manager.  

> [!NOTE]  
>  Z wyjątkiem klientów Windows Embedded, które są w trybie obsługi klienci programu Configuration Manager, które nie są uruchomieni w środowiskach zwirtualizowanych używają tego losowego opóźnienia. W przypadku wielu wdrożonych klientów to zachowanie zapobiega powstawianiu szczytów przepustowości sieci i zmniejsza wymaganie przetwarzania przez procesor CPU w systemach lokacji programu Configuration Manager, takie jak punkt zarządzania i lokacji serwer. Interwał opóźnienia zależy od możliwości programu Configuration Manager.  
>   
>  Losowe opóźnienie można wyłączyć domyślnie dla wymaganych aktualizacji oprogramowania i wymaganych wdrożeń aplikacji przy użyciu następującego ustawienia klienta: **Agent komputera**: **Wyłącz losowe generowanie terminu ostatecznego**.
