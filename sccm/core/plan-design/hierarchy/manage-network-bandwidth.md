---
title: "Zarządzanie przepustowością sieci dla zawartości"
titleSuffix: Configuration Manager
description: "Skonfiguruj harmonogram, ograniczania i wstępnie przygotowanej zawartości programu System Center Configuration Manager."
ms.custom: na
ms.date: 2/6/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e80d1151-91db-4a27-8411-a957297b67d0
caps.latest.revision: "15"
caps.handback.revision: "0"
author: aaroncz
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 907d937a7aef7fb4173c5d4a45aef0bc210bf96f
ms.sourcegitcommit: 7fe45ff75f05f7cc03ad021db8119791abe18049
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/01/2017
---
# <a name="manage-network-bandwidth-for-content"></a>Zarządzanie przepustowością sieci dla zawartości
Aby ułatwić zarządzanie przepustowością sieci, który jest używany przez proces zarządzania zawartością programu System Center Configuration Manager, używając formantów wbudowanych planowania i ograniczania przepustowości. Można również użyć wstępnie przygotowanej zawartości. W poniższych sekcjach opisano te opcje bardziej szczegółowo.

##  <a name="BKMK_PlanningForThrottling"></a>Planowania i ograniczania przepustowości  

 Podczas tworzenia pakietów, zmienić ścieżkę źródłową zawartości lub zaktualizować zawartość w punkcie dystrybucji, pliki są kopiowane ze ścieżki źródłowej do biblioteki zawartości na serwerze lokacji. Następnie zawartość jest kopiowana z biblioteki zawartości na serwerze lokacji do biblioteki zawartości w punktach dystrybucji. Gdy pliki zawartości źródłowej są aktualizowane i pliki źródłowe zostały już rozpowszechnione, programu Configuration Manager pobiera tylko nowe lub zaktualizowane pliki, a następnie wysyła je do punktu dystrybucji.

 Kontrolki planowania i ograniczania przepustowości służy do komunikacji lokacja lokacja i komunikacji między serwerem lokacji a zdalnym punkcie dystrybucji. Jeśli przepustowość sieci jest ograniczona nawet po skonfigurowaniu kontrolki planowania i ograniczania przepustowości, należy rozważyć wstępne przygotowanie zawartości w punkcie dystrybucji.  

 W programie Configuration Manager można skonfigurować harmonogram i określ ustawienia ograniczenia przepustowości w zdalnych punktach dystrybucji określających sposób dystrybucji zawartości jest wykonywane i. Poszczególnych zdalnych punktów dystrybucji mogą mieć różne konfiguracje pomagające określenia ograniczeń przepustowości sieci między serwerem lokacji do zdalnych punktów dystrybucji. Kontrolki planowania i ograniczania przepustowości do zdalnego punktu dystrybucji są podobne do ustawień adresu standardowego nadawcy. W takim przypadku ustawienia są używane przez nowy składnik, Menedżer transferu pakietów.

 Menedżer transferu pakietów dystrybucji zawartości z serwera lokacji jako lokacji głównej lub lokacji dodatkowej do punktu dystrybucji zainstalowanego w systemie lokacji. Ustawienia ograniczenia przepustowości są określone na **limity szybkości** określono zaś ustawienia planowania na **harmonogram** karty dla punktu dystrybucji, który nie znajduje się na serwerze lokacji. Ustawienia czasu są oparte na strefie czasowej witryny wysyłania, a nie punktu dystrybucji.  

> [!IMPORTANT]  
>  **Limity szybkości** i **harmonogram** będą wyświetlane tylko we właściwościach punktów dystrybucji, które nie są zainstalowane na serwerze lokacji.  

Aby uzyskać więcej informacji, zobacz [zainstalować i skonfigurować punkty dystrybucji programu System Center Configuration Manager](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points).  

##  <a name="BKMK_PrestagingContent"></a>Wstępnie przygotowanej zawartości  
 Można wstępnie przygotować zawartość, aby dodać pliki zawartości do biblioteki zawartości w lokacji serwera lub punktu dystrybucji, przed rozpoczęciem dystrybucji zawartości. Pliki zawartości znajdują się już w bibliotece zawartości, dlatego nie są one przesyłane za pośrednictwem sieci podczas dystrybucji zawartości. Można wstępnie przygotować pliki zawartości aplikacji i pakietów.  

W konsoli programu Configuration Manager, należy wybrać zawartość, która ma zostać wstępnie przygotowana, a następnie użyć **Tworzenie kreatora przygotowanego pliku zawartości**. Spowoduje to utworzenie skompresowany, wstępnie przygotowany plik zawartości obejmujący pliki oraz skojarzone metadane wybranej zawartości. Następnie można ręcznie zaimportować zawartość na lokacji serwera lub punktu dystrybucji. Należy uwzględnić następujące kwestie:  

-   Podczas importowania wstępnie przygotowanego pliku zawartości na serwerze lokacji pliki zawartości są dodawane do biblioteki zawartości na serwerze lokacji, a następnie rejestrowane w bazie danych serwera lokacji.  

-   Podczas importowania wstępnie przygotowanego pliku zawartości w punkcie dystrybucji pliki zawartości są dodawane do biblioteki zawartości w punkcie dystrybucji. Komunikat o stanie są wysyłane do serwera lokacji, które informują witryny, czy zawartość jest dostępna w punkcie dystrybucji.  

Opcjonalnie można skonfigurować punkt dystrybucji jako **wstępnie** aby ułatwić zarządzanie dystrybucją zawartości. Następnie podczas dystrybucji zawartości można wybrać do:  

-   Zawsze wstępnie przygotowywać zawartość w punkcie dystrybucji.  

-   Wstępne przygotowanie początkowej zawartości pakietu, a następnie użyj standardowy proces dystrybucji zawartości, gdy są dostępne aktualizacje zawartości.  

-   Zawsze stosować standardowy proces dystrybucji zawartości zawartości w pakiecie.  

###  <a name="BKMK_DetermineToPrestageContent"></a>Określanie, czy należy wstępnie przygotować zawartość  
 Należy rozważyć wstępne przygotowanie zawartości aplikacji i pakietów w następujących scenariuszach:  

-   **Aby rozwiązać problem ograniczona przepustowość sieci między serwerem lokacji do punktu dystrybucji.** Jeśli planowania i ograniczania przepustowości nie rozwiązują problemów dotyczących przepustowości tyle, należy rozważyć wstępne przygotowanie zawartości w punkcie dystrybucji. Każdy punkt dystrybucji ma **Włącz ten punkt dystrybucji dla wstępnie przygotowanej zawartości** ustawienie, które są dostępne we właściwościach punktu dystrybucji. Po włączeniu tej opcji punkt dystrybucji został rozpoznany jako wstępnie przygotowanym punkcie dystrybucji, a następnie można wybrać sposób zarządzania zawartością w poszczególnych pakietów.  

    Następujące ustawienia są dostępne we właściwościach aplikacji, pakietów, pakiet sterowników, obrazu rozruchowego, Instalatora systemu operacyjnego i obrazu. Te ustawienia umożliwiają wybieranie sposobu zarządzania dystrybucją w zdalnych punktach dystrybucji rozpoznanych jako wstępnie przygotowane zawartości:  

    -   **Automatycznie Pobierz zawartość po przypisaniu pakietów do punktów dystrybucji**: Użyj tej opcji, gdy masz mniejszych pakietów, a ustawienia planowania i ograniczania przepustowości zapewniają wystarczającą kontrolę nad dystrybucją zawartości.  

    -   **Pobierz tylko zmiany zawartości w punkcie dystrybucji**: Użyj tej opcji, jeśli będziesz przyszłe aktualizacje zawartości w pakiecie będą generalnie mniejsze niż początkowego pakietu. Na przykład przygotować wstępnie aplikacji, takie jak Microsoft Office, ponieważ rozmiar wstępnego pakietu przekracza 700 MB czym jest zbyt duży do wysyłania za pośrednictwem sieci. Niemniej jednak aktualizacje zawartości tego pakietu może być mniejsza niż 10 MB, a co umożliwia ich dystrybucję za pośrednictwem sieci. Innym przykładem mogą być pakiety sterowników, których rozmiar początkowego pakietu duży, lecz kolejne dodatki do pakietu mogą mieć niewielkie.  

    -   **Ręcznie skopiuj zawartość tego pakietu do punktu dystrybucji**: Użyj tej opcji, gdy masz dużych pakietów zawierających na przykład system operacyjny i nigdy nie chcesz używać sieci do dystrybucji zawartości do punktu dystrybucji. Po wybraniu tej opcji należy wstępnie przygotować zawartość w punkcie dystrybucji.  

    > [!IMPORTANT]  
    >  Poprzednie opcje są stosowane na poszczególnych pakietów i są używane tylko, gdy punkt dystrybucji został rozpoznany jako wstępnie przygotowane. Punkty dystrybucji, które nie zostały zidentyfikowane jako wstępnie przygotowane będą ignorować te ustawienia. W takim przypadku zawartość będzie zawsze dystrybuowana za pośrednictwem sieci z serwera lokacji do punktów dystrybucji.  

-   **Aby przywrócić bibliotekę zawartości na serwerze lokacji.** W przypadku awarii serwera lokacji informacje o pakietach i aplikacjach znajdujące się w bibliotece zawartości są odzyskiwane do bazy danych lokacji w ramach procesu przywracania, ale nie przywrócono plików biblioteki zawartości w ramach procesu. Jeśli nie masz kopii zapasowej systemu plików do przywrócenia biblioteki zawartości, można utworzyć wstępnie przygotowany plik zawartości z innej lokacji, który zawiera pakiety i aplikacje, które są potrzebne. Następnie można wyodrębnić wstępnie przygotowany plik zawartości na odzyskanym serwerze lokacji. Aby uzyskać więcej informacji na temat kopii zapasowej serwera lokacji i odzyskiwania, zobacz [kopii zapasowych i odzyskiwania dla programu System Center Configuration Manager](/sccm/protect/understand/backup-and-recovery).  
