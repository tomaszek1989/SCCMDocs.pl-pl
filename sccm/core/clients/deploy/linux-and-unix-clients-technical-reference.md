---
title: "Usługi składników klienta systemu UNIX/Linux i polecenia | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat usługi składowe i poleceń na klientach z systemem Linux i UNIX w programie System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e5a8c79f-5791-49c5-8055-086d742e5559
caps.latest.revision: 6
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 89668f3e2e0a3e2e0178e5b2c91b2508f583649f
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="linux-and-unix-clients-component-services-and-commands-for-system-center-configuration-manager"></a>Usługi składowe klienci z systemem Linux i UNIX i polecenia dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


 W poniższej tabeli przedstawiono usługi klienta składnika klienta programu Configuration Manager dla systemu Linux i UNIX.  

|Nazwa pliku|Więcej informacji|  
|---------------|----------------------|  
|ccmexec.bin|Usługa ta jest równoważna usłudze ccmexc na kliencie systemu Windows. Jest odpowiedzialny za cała komunikacja z rolami systemu lokacji programu Configuration Manager, a także komunikuje się z usługą omiserver.bin, aby zbierać zapasy sprzętu z komputera lokalnego.<br /><br /> Aby uzyskać listę obsługiwanych argumentów wiersza polecenia, uruchom polecenie **ccmexec -h**|  
|omiserver.bin|Ta usługa jest serwerem modelu wspólnych informacji. Serwer modelu wspólnych informacji zapewnia platformę dla podłączanych modułów oprogramowania nazywanych dostawcami. Dostawcy wchodzą w interakcje z zasobami komputera z systemem Linux oraz UNIX i zbierają dane spisu sprzętu. Na przykład **dostawca procesu** dla komputera z systemem Linux zbiera dane skojarzone z procesami systemu operacyjnego Linux.|  

 Następująca tabela zawiera listę poleceń, za pomocą których można uruchamiać, zatrzymywać i restartować usługi klienckie (ccmexec.bin i omiserver.bin) na każdej wersji systemu Linux lub UNIX. Uruchomienie lub zatrzymanie usługi ccmexec powoduje również uruchomienie lub zatrzymanie usługi omiserver.  

|System operacyjny|Polecenia|  
|----------------------|--------------|  
|Universal Agent<br /><br /> RHEL 4 i SLES 9|Uruchamianie: **/etc/init d/ccmexecd start**<br /><br /> Zatrzymywanie: **/etc/init d/ccmexecd stop**<br /><br /> Ponowne uruchamianie: **/etc/init d/ccmexecd restart**|  
|Solaris 9|Uruchamianie: **/etc/init d/ccmexecd start**<br /><br /> Zatrzymywanie: **/etc/init d/ccmexecd stop**<br /><br /> Ponowne uruchamianie: **/etc/init d/ccmexecd restart**|  
|Solaris 10|Uruchamianie:<br /><br /> **Włącz svcadm svc -s: / omiserver/zarządzania/aplikacji**<br /><br /> **Włącz svcadm svc -s: / ccmexecd/zarządzania/aplikacji**<br /><br /> Zatrzymywanie:<br /><br /> **Wyłącz svcadm svc -s: / ccmexecd/zarządzania/aplikacji**<br /><br /> **Wyłącz svcadm svc -s: / omiserver/zarządzania/aplikacji**|  
|Solaris 11|Uruchamianie:<br /><br /> **Włącz svcadm svc -s: / omiserver/zarządzania/aplikacji**<br /><br /> **Włącz svcadm svc -s: / ccmexecd/zarządzania/aplikacji**<br /><br /> Zatrzymywanie:<br /><br /> **Wyłącz svcadm svc -s: / ccmexecd/zarządzania/aplikacji**<br /><br /> **Wyłącz svcadm svc -s: / omiserver/zarządzania/aplikacji**|  
|AIX|Uruchamianie:<br /><br /> **startsrc -s omiserver**<br /><br /> **startsrc -s ccmexec**<br /><br /> Zatrzymywanie:<br /><br /> **stopsrc -s ccmexec**<br /><br /> **stopsrc omiserver -s**|  
|HP-UX|Uruchamianie: **/sbin/init.d/ccmexecd start**<br /><br /> Zatrzymywanie: **/sbin/init.d/ccmexecd stop**<br /><br /> Ponowne uruchamianie: **/sbin/init.d/ccmexecd restart**|  

