---

title: "Zarządzania synchronizacją aktualizacji oprogramowania | Dokumentacja firmy Microsoft"
description: "Wykonaj te kroki, aby zaplanować synchronizację aktualizacji oprogramowania, ręcznie uruchomić synchronizację aktualizacji oprogramowania i monitorowanie synchronizacji aktualizacji oprogramowania."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: ea8698c4-9df5-4cf5-8b62-ab93115b4769
ms.translationtype: Machine Translation
ms.sourcegitcommit: e6cf8c799b5be2f7dbb6fadadddf702ec974ae45
ms.openlocfilehash: e68170a16a6a908e035247ed9c0f3cc6cdbe1983
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017



---

#  <a name="BKMK_SUMSync"></a> Synchronizacja aktualizacji oprogramowania

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

 Synchronizacja aktualizacji oprogramowania w programie Configuration Manager to proces pobierania metadanych aktualizacji oprogramowania, która spełnia kryteria, które można skonfigurować. W tym określonych produktów, klasyfikacji i języków. Zazwyczaj punkt aktualizacji oprogramowania w centralnej lokacji administracyjnej lub autonomicznej lokacji głównej pobiera metadane z witryny Microsoft Update. Następnie w lokacji najwyższego poziomu wyśle żądanie synchronizacji do innych lokacji. Kiedy dana lokacja odbiera żądanie synchronizacji od lokacji nadrzędnej, punkt aktualizacji oprogramowania dla lokacji pobiera metadane aktualizacji oprogramowania ze swojego nadrzędnego [źródło synchronizacji](../plan-design/plan-for-software-updates.md#BKMK_SyncSource). Aby uzyskać więcej informacji na temat procesu synchronizacji aktualizacji oprogramowania, zobacz [synchronizacji aktualizacji oprogramowania](../understand/software-updates-introduction.md#BKMK_Synchronization).

Konfigurowanie synchronizacji aktualizacji oprogramowania do uruchamiania zgodnie z harmonogramem we właściwościach punktu aktualizacji oprogramowania w lokacji najwyższego poziomu. Po skonfigurowaniu harmonogramu synchronizacji zazwyczaj nie zmienia się owego harmonogramu w ramach normalnych operacji. Można jednak ręcznie zainicjować synchronizację aktualizacji oprogramowania w razie potrzeby.

  > [!NOTE]  
  >  Punkty aktualizacji oprogramowania musi być podłączony do ich nadrzędnym źródłem synchronizacji do synchronizacji aktualizacji oprogramowania. Kiedy punkt aktualizacji oprogramowania zostanie odłączony od swojego nadrzędnego źródła synchronizacji, do synchronizacji aktualizacji oprogramowania można użyć metody polegającej na eksporcie i imporcie. Aby uzyskać więcej informacji, zobacz [Synchronizowanie aktualizacji oprogramowania z odłączonego punktu aktualizacji oprogramowania](synchronize-software-updates-disconnected.md).  

## <a name="schedule-software-updates-synchronization"></a>Harmonogram synchronizacji aktualizacji oprogramowania
Po skonfigurowaniu harmonogramu synchronizacji aktualizacji oprogramowania, punkt aktualizacji oprogramowania najwyższego poziomu rozpoczyna synchronizację z usługą Microsoft Update w zaplanowanym terminie. Harmonogram niestandardowy pozwala na synchronizowanie aktualizacji oprogramowania do dnia i godziny, gdy zapotrzebowanie z serwera WSUS, serwera lokacji oraz sieci jest niskie. Na przykład można ustawić harmonogram aktualizacji oprogramowania są zsynchronizowane raz w tygodniu o 2:00 w NOCY. Podczas zaplanowanej synchronizacji wszystkie zmiany metadanych aktualizacji oprogramowania od ostatniej zaplanowanej synchronizacji są wstawiane do bazy danych lokacji. Dotyczy to nowych metadanych aktualizacji oprogramowania lub zmodyfikowanych, usuniętych bądź nieważnych metadanych.

Aby zaplanować synchronizację aktualizacji oprogramowania, użyj poniższych procedur w lokacji najwyższego poziomu.  

#### <a name="to-schedule-software-updates-synchronization"></a>Aby zaplanować synchronizację aktualizacji oprogramowania  

  1.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

  2.  W obszarze roboczym Administracja rozwiń węzeł **Konfiguracja lokacji**, a następnie kliknij przycisk **Lokacje**.  

  3.  W okienku wyników kliknij centralną lokację administracyjną lub autonomiczną lokację główną.  

  4.  Na karcie **Narzędzia główne** w grupie **Ustawienia** rozwiń węzeł **Konfiguruj składniki lokacji**, a następnie kliknij opcję **Punkt aktualizacji oprogramowania**.  

  5.  W oknie dialogowym Właściwości składnika punktu aktualizacji oprogramowania wybierz opcję **Włącz synchronizację według harmonogramu**, a następnie określ harmonogram synchronizacji.  

## <a name="manually-start-software-updates-synchronization"></a>Ręcznie uruchom synchronizację aktualizacji oprogramowania
Można ręcznie zainicjować synchronizację aktualizacji oprogramowania w lokacji najwyższego poziomu w konsoli programu Configuration Manager z **wszystkie aktualizacje oprogramowania** w węźle **Biblioteka oprogramowania** obszaru roboczego.  

Użyj poniższych procedur w lokacji najwyższego poziomu, aby ręcznie zainicjować synchronizację aktualizacji oprogramowania.  

#### <a name="to-manually-start-software-updates-synchronization"></a>Aby ręcznie uruchomić oprogramowania synchronizację aktualizacji  

  1.  W konsoli programu Configuration Manager, który jest połączony z centralnej lokacji administracyjnej lub autonomicznej lokacji głównej, kliknij przycisk **Biblioteka oprogramowania**.  

  2.  W obszarze roboczym Biblioteka oprogramowania rozwiń listę **Aktualizacje oprogramowania** i kliknij pozycję **Wszystkie aktualizacje oprogramowania** lub **Grupy aktualizacji oprogramowania**.  

  3.  Na karcie **Narzędzia główne** w grupie **Tworzenie** kliknij przycisk **Synchronizuj aktualizacje oprogramowania**. Kliknij w oknie dialogowym przycisk **Tak** , aby potwierdzić zainicjowanie procesu synchronizacji.  

   Po zainicjowaniu procesu synchronizacji w punkcie aktualizacji oprogramowania można monitorować proces synchronizacji z konsoli programu Configuration Manager dla wszystkich punktów aktualizacji oprogramowania w hierarchii. Aby monitorować proces synchronizacji aktualizacji oprogramowania, wykonaj czynności opisane w poniższej procedurze.  


## <a name="monitor-software-updates-synchronization"></a>Monitor synchronizacji aktualizacji oprogramowania
Po zainicjowaniu procesu synchronizacji, można użyć konsoli programu Configuration Manager do monitorowania procesu we wszystkich punktach aktualizacji oprogramowania w hierarchii. Aby monitorować proces synchronizacji aktualizacji oprogramowania, należy użyć następującej procedury. Więcej informacji na temat monitorowania aktualizacji oprogramowania, proces synchronizacji, w tym temacie [monitorowania aktualizacji oprogramowania](../deploy-use/monitor-software-updates.md).

#### <a name="to-monitor-the-software-updates-synchronization-process"></a>Aby monitorować proces synchronizacji aktualizacji oprogramowania  

  1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

  2.  W obszarze roboczym **Monitorowanie** kliknij przycisk **Stan synchronizacji punktu aktualizacji oprogramowania**.  

    Punkty aktualizacji oprogramowania w hierarchii programu Configuration Manager są wyświetlane w okienku wyników. Z poziomu tego widoku możesz monitorować stan synchronizacji wszystkich punktów aktualizacji oprogramowania. Aby zapoznać się z bardziej szczegółowymi informacjami na temat procesu synchronizacji, można przejrzeć plik wsyncmgr.log, znajdujący się w folderze <*ścieżka_instalacji_Configuration_Manager*>\Logs na każdym serwerze lokacji.  

## <a name="next-steps"></a>Następne kroki
Po zsynchronizowaniu aktualizacji oprogramowania po raz pierwszy lub po dostępnych nowych klasyfikacji lub produktów, należy [Konfigurowanie nowej klasyfikacji i produktów](configure-classifications-and-products.md) do synchronizowania aktualizacji oprogramowania do nowych kryteriów.

Po zsynchronizowaniu aktualizacji oprogramowania z kryteriami, które są potrzebne, [Zarządzanie ustawieniami aktualizacji oprogramowania](manage-settings-for-software-updates.md).  

