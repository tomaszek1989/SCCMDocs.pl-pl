---
title: "Obsługa serwerów proxy | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat obsługi programu System Center Configuration Manager dla serwerów proxy, korzystających z serwerami systemu lokacji i klientów."
ms.custom: na
ms.date: 2/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9123a87a-0b6f-43c7-b5c2-fac5d09686b1
caps.latest.revision: "6"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: dc36be47310d2c2178c974a2b503d0b5f9f6e2ec
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="proxy-server-support-in-system-center-configuration-manager"></a>Obsługa serwerów proxy w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Zarówno serwery systemu lokacji programu System Center Configuration Manager, jak i klientów można użyć serwera proxy.  

## <a name="site-system-servers"></a>Serwery systemu lokacji  
Role systemu lokacji muszą łączyć się z Internetem, można skonfigurować je, aby użyć serwera proxy.  

-   Komputer hostujący serwer systemu lokacji obsługuje jedną konfigurację serwera proxy współużytkowaną przez wszystkie role systemu lokacji na tym samym komputerze. Jeśli potrzebujesz oddzielnych serwerów proxy dla różnych ról lub wystąpień roli, należy umieścić te role na oddzielnych serwerach systemu lokacji.  

-   Podczas konfigurowania nowych ustawień serwera proxy dla serwera systemu lokacji, która ma już konfigurację serwera proxy, oryginalna konfiguracja zostanie zastąpiona.  

-   Połączenia z serwerem proxy korzystają z konta **System** komputera, który hostuje role systemu lokacji.  

Następujące role systemu lokacji połączenie z Internetem i mogą wymagać serwera proxy.  Z jednym wyjątkiem, role systemu lokacji, które mogą używać serwera proxy, robią to bez dodatkowej konfiguracji. Wyjątkiem jest punkt aktualizacji oprogramowania. Poniższa lista zawiera informacje o dodatkowych konfiguracjach wymaganych przez punkt aktualizacji oprogramowania:  

**Punkt synchronizacji analizy zasobów** — ta rola systemu lokacji łączy do firmy Microsoft i używa konfiguracji serwera proxy na komputerze, który hostuje punkt synchronizacji analizy zasobów.  

**Punkt dystrybucji w chmurze** — Aby skonfigurować serwer proxy dla punktu dystrybucji w chmurze, można skonfigurować serwera proxy w lokacji głównej zarządzającej punktem dystrybucji w chmurze.  

W przypadku tej konfiguracji serwer lokacji głównej:  

-   Musi mieć możliwość połączenia z platformą Microsoft Azure do konfigurowania, monitorowania i dystrybucji zawartości do punktu dystrybucji.  

-   Używa konta System danego komputera do nawiązania połączenia.  

-   Używa domyślnej przeglądarki sieci web danego komputera.  

Nie można skonfigurować serwer proxy w chmurze na podstawie — punkt dystrybucji w systemie Microsoft Azure.  

**Punkt połączenia z chmurą** — ta rola systemu lokacji łączy się z usługą chmury programu Configuration Manager, aby pobierać aktualizacje wersji dla programu Configuration Manager i korzysta z serwera proxy, który jest skonfigurowany na komputerze, który hostuje punkt połączenia usługi.  

**Łącznik serwera Exchange** — ta rola systemu lokacji łączy się z serwerem programu Exchange i używa konfiguracji serwera proxy na komputerze, który hostuje łącznik serwera Exchange.  

**Punkt połączenia z usługą** — ta rola systemu lokacji łączy się Microsoft Intune i używa konfiguracji serwera proxy na komputerze, który hostuje punkt połączenia usługi.  

**Punkt aktualizacji oprogramowania** — ta rola systemu lokacji może używać serwera proxy w przypadku połączeń z usługą Microsoft Update w celu pobrania poprawek i synchronizowania informacji dotyczących aktualizacji. Punkty aktualizacji oprogramowania użyć serwera proxy tylko w przypadku następujących opcji, po włączeniu tej opcji, po skonfigurowaniu punktu aktualizacji oprogramowania:  

-   **Użyj serwera proxy podczas synchronizowania aktualizacji oprogramowania**  

-   **Pobierania zawartości za pomocą reguł wdrażania automatycznego Użyj serwera proxy** (dostępne do użycia, to ustawienie nie jest używane przez punkty aktualizacji oprogramowania w lokacjach dodatkowych.)  

Skonfiguruj ustawienia serwera proxy na stronie punkt aktualizacji oprogramowania aktywnego Kreatora dodawania ról systemu lokacji lub na **ogólne** karcie **właściwości składnika punktu aktualizacji oprogramowania**.  

-   Ustawienia serwera proxy są skojarzone tylko z punktem aktualizacji oprogramowania w lokacji.  

-   Opcje serwera proxy są dostępne tylko w przypadku, gdy serwer proxy jest już skonfigurowane dla serwera systemu lokacji, który jest hostem punktu aktualizacji oprogramowania.  

> [!NOTE]  
>  Domyślnie do łączenia się z Internetem i pobierania aktualizacji oprogramowania podczas uruchamiania zasad wdrażania automatycznego służy konto **System** na serwerze, na którym dana zasada wdrażania automatycznego została utworzona.  
>   
>  Gdy to konto nie ma dostępu do Internetu, aktualizacji oprogramowania nie udaje się pobrać i ruleengine.log jest rejestrowany następujący wpis: **Nie można pobrać aktualizacji z Internetu. Błąd = 12007**.  

#### <a name="to-set-up-the-proxy-server-for-a-site-system-server"></a>Aby skonfigurować serwer proxy dla serwera systemu lokacji  

1.  W konsoli programu Configuration Manager wybierz **administracji**, rozwiń węzeł **konfiguracja lokacji**, a następnie wybierz pozycję **serwery i role systemu lokacji**.  

2.  Wybierz serwer systemu lokacji, który chcesz edytować, w okienku szczegółów kliknij prawym przyciskiem **system lokacji**, a następnie wybierz pozycję **właściwości**.  

3.  W oknie Właściwości systemu lokacji wybierz **Proxy** karcie, a następnie skonfigurować ustawienia serwera proxy dla serwera lokacji głównej.  

4.  Wybierz **OK** do zapisywania nowego serwera proxy z konfiguracji serwera.  
