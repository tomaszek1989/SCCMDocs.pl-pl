---
title: "Obsługa serwera proxy | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat obsługi programu System Center Configuration Manager dla serwerów proxy, korzystających z serwerami systemu lokacji i klientów."
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9123a87a-0b6f-43c7-b5c2-fac5d09686b1
caps.latest.revision: 6
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: c4f30e4839709722b216262b21d7b51c07d24d1e
ms.openlocfilehash: dc36be47310d2c2178c974a2b503d0b5f9f6e2ec
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="proxy-server-support-in-system-center-configuration-manager"></a>Obsługa serwerów proxy w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Zarówno serwery systemu lokacji programu System Center Configuration Manager, jak i klienci mogą używać serwera proxy.  

## <a name="site-system-servers"></a>Serwery systemu lokacji  
Role systemu lokacji muszą łączyć się z Internetem, można skonfigurować do korzystania z serwera proxy.  

-   Komputer, który obsługuje serwer systemu lokacji obsługuje jedną konfigurację serwera proxy współużytkowana przez wszystkie role systemu lokacji na tym samym komputerze. Jeśli potrzebujesz rozdzielić serwerów proxy dla różnych ról lub wystąpień roli, należy umieścić na serwerach systemu lokacji oddzielnych tych ról.  

-   Podczas konfigurowania nowych ustawień serwera proxy dla serwera systemu lokacji, która ma już konfiguracji serwera proxy jest zastępowany oryginalną konfigurację.  

-   Połączenia z serwerem proxy korzystają z konta **System** komputera, który hostuje role systemu lokacji.  

Następujące role systemu lokacji łączy się z Internetem i może wymagać serwera proxy.  Z jednym wyjątkiem, role systemu lokacji, które mogą używać serwera proxy, robią to bez dodatkowej konfiguracji. Wyjątkiem jest punkt aktualizacji oprogramowania. Poniższa lista zawiera informacje o dodatkowych konfiguracjach, które wymaga punktu aktualizacji oprogramowania:  

**Punkt synchronizacji analizy zasobów** -ta rola systemu lokacji łączy do firmy Microsoft i używa konfiguracji serwera proxy na komputerze, który obsługuje punkt synchronizacji analizy zasobów.  

**Punkt dystrybucji w chmurze** —, aby skonfigurować serwer proxy dla punktu dystrybucji w chmurze, można skonfigurować serwera proxy w lokacji głównej zarządzającej punktem dystrybucji w chmurze.  

W przypadku tej konfiguracji serwer lokacji głównej:  

-   Musi być w stanie nawiązać połączenia z programem Microsoft Azure do konfigurowania, monitorowania i dystrybucji zawartości do punktu dystrybucji.  

-   Używane konto systemu tego komputera do nawiązania połączenia.  

-   Używa tego komputera domyślną przeglądarkę sieci web.  

Nie można skonfigurować serwera proxy w punkcie chmury dystrybucji platformy Microsoft Azure.  

**Punkt połączenia w chmurze** -ta rola systemu lokacji łączy się z usługą chmury programu Configuration Manager do pobierania aktualizacji w wersji dla programu Configuration Manager i korzysta z serwera proxy, który jest skonfigurowany na komputerze, który jest hostem punktu połączenia usługi.  

**Łącznik serwera Exchange** -ta rola systemu lokacji łączy się z serwerem Exchange i używa konfiguracji serwera proxy na komputerze, który obsługuje łącznik serwera Exchange.  

**Punkt połączenia usługi** -ta rola systemu lokacji łączy się Microsoft Intune i używa konfiguracji serwera proxy na komputerze, który jest hostem punktu połączenia usługi.  

**Punkt aktualizacji oprogramowania** — ta rola systemu lokacji może używać serwera proxy w przypadku połączeń z usługą Microsoft Update w celu pobrania poprawek i synchronizowania informacji dotyczących aktualizacji. Punkty aktualizacji oprogramowania serwer proxy należy używać tylko do poniższych opcji po włączeniu tej opcji, jak skonfigurować punkt aktualizacji oprogramowania:  

-   **Użyj serwera proxy podczas synchronizowania aktualizacji oprogramowania**  

-   **Użyj serwera proxy podczas pobierania zawartości za pomocą reguł wdrażania automatycznego** (gdy są dostępne do użycia, to ustawienie jest nie używane przez punkty aktualizacji oprogramowania w lokacjach dodatkowych.)  

Skonfiguruj ustawienia serwera proxy na stronie punkt aktualizacji oprogramowania aktywnego w Kreatorze dodawania ról systemu lokacji lub na **ogólne** karcie w **właściwości składnika punktu aktualizacji oprogramowania**.  

-   Ustawienia serwera proxy są skojarzone tylko z punktem aktualizacji oprogramowania w lokacji.  

-   Opcje serwera proxy są dostępne tylko w przypadku, gdy serwer proxy jest już ustawiony dla serwera systemu lokacji, który jest hostem punktu aktualizacji oprogramowania.  

> [!NOTE]  
>  Domyślnie do łączenia się z Internetem i pobierania aktualizacji oprogramowania podczas uruchamiania zasad wdrażania automatycznego służy konto **System** na serwerze, na którym dana zasada wdrażania automatycznego została utworzona.  
>   
>  Gdy to konto nie ma dostępu do Internetu, nie będą mogli pobierać aktualizacje oprogramowania i ruleengine.log jest rejestrowany następujący wpis: **Nie można pobrać aktualizacji z Internetu. Błąd = 12007**.  

#### <a name="to-set-up-the-proxy-server-for-a-site-system-server"></a>Aby skonfigurować serwer proxy dla serwera systemu lokacji  

1.  W konsoli programu Configuration Manager wybierz **Administracja**, rozwiń węzeł **konfiguracja lokacji**, a następnie wybierz **serwery i role systemu lokacji**.  

2.  Wybierz serwer systemu lokacji, który chcesz edytować, w okienku szczegółów prawym przyciskiem myszy **system lokacji**, a następnie wybierz **właściwości**.  

3.  Właściwości systemu lokacji, wybierz **serwera Proxy** karcie, a następnie skonfiguruj ustawienia serwera proxy dla serwera lokacji głównej.  

4.  Wybierz **OK** Aby zapisać konfigurację serwera proxy nowe.  

