---
title: "Usługi składowe klienta systemu UNIX/Linux i poleceń | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat poleceń na klientach z systemem Linux i UNIX w programie System Center Configuration Manager i usługi składowe."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e5a8c79f-5791-49c5-8055-086d742e5559
caps.latest.revision: "6"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: f11795b05f1b422e97fd32e7457c44b708fa93e4
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2017
---
# <a name="linux-and-unix-clients-component-services-and-commands-for-system-center-configuration-manager"></a>Polecenia dla programu System Center Configuration Manager i usługi składowe klientów systemu Linux i UNIX

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


 W poniższej tabeli przedstawiono usługi składowe klienta programu Configuration Manager klienta dla systemów Linux i UNIX.  

|Nazwa pliku|Więcej informacji|  
|---------------|----------------------|  
|ccmexec.bin|Usługa ta jest równoważna usłudze ccmexc na kliencie systemu Windows. Jest odpowiedzialna za całą komunikację z rolami systemu lokacji programu Configuration Manager, a także komunikuje się z usługą omiserver.bin, aby zbierać spis sprzętu z komputera lokalnego.<br /><br /> Aby uzyskać listę obsługiwanych argumentów wiersza polecenia, uruchom polecenie **ccmexec -h**|  
|omiserver.bin|Ta usługa jest serwerem modelu wspólnych informacji. Serwer modelu wspólnych informacji zapewnia platformę dla podłączanych modułów oprogramowania nazywanych dostawcami. Dostawcy wchodzą w interakcje z zasobami komputera z systemem Linux oraz UNIX i zbierają dane spisu sprzętu. Na przykład **dostawca procesu** dla komputera z systemem Linux zbiera dane skojarzone z procesami systemu operacyjnego Linux.|  

 Następująca tabela zawiera listę poleceń, za pomocą których można uruchamiać, zatrzymywać i restartować usługi klienckie (ccmexec.bin i omiserver.bin) na każdej wersji systemu Linux lub UNIX. Uruchomienie lub zatrzymanie usługi ccmexec powoduje również uruchomienie lub zatrzymanie usługi omiserver.  

|System operacyjny|Polecenia|  
|----------------------|--------------|  
|Universal Agent<br /><br /> RHEL 4 i SLES 9|Uruchamianie: **/etc/init d/ccmexecd start**<br /><br /> Zatrzymywanie: **/etc/init d/ccmexecd stop**<br /><br /> Ponowne uruchamianie: **/etc/init d/ccmexecd restart**|  
|Solaris 9|Uruchamianie: **/etc/init d/ccmexecd start**<br /><br /> Zatrzymywanie: **/etc/init d/ccmexecd stop**<br /><br /> Ponowne uruchamianie: **/etc/init d/ccmexecd restart**|  
|Solaris 10|Uruchamianie:<br /><br /> **svcadm włączyć svc -s: / omiserver/zarządzania/aplikacji**<br /><br /> **svcadm włączyć svc -s: / ccmexecd/zarządzania/aplikacji**<br /><br /> Zatrzymywanie:<br /><br /> **svcadm wyłączyć svc -s: / ccmexecd/zarządzania/aplikacji**<br /><br /> **svcadm wyłączyć svc -s: / omiserver/zarządzania/aplikacji**|  
|Solaris 11|Uruchamianie:<br /><br /> **svcadm włączyć svc -s: / omiserver/zarządzania/aplikacji**<br /><br /> **svcadm włączyć svc -s: / ccmexecd/zarządzania/aplikacji**<br /><br /> Zatrzymywanie:<br /><br /> **svcadm wyłączyć svc -s: / ccmexecd/zarządzania/aplikacji**<br /><br /> **svcadm wyłączyć svc -s: / omiserver/zarządzania/aplikacji**|  
|AIX|Uruchamianie:<br /><br /> **startsrc -s omiserver**<br /><br /> **startsrc -s ccmexec**<br /><br /> Zatrzymywanie:<br /><br /> **stopsrc ccmexec -s**<br /><br /> **stopsrc omiserver -s**|  
|HP-UX|Uruchamianie: **/sbin/init.d/ccmexecd start**<br /><br /> Zatrzymywanie: **/sbin/init.d/ccmexecd stop**<br /><br /> Ponowne uruchamianie: **/sbin/init.d/ccmexecd restart**|  
