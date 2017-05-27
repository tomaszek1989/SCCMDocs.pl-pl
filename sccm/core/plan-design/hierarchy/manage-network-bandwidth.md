---
title: "Zarządzanie przepustowością sieci zawartości | Dokumentacja firmy Microsoft"
description: "Skonfiguruj harmonogram, ograniczania i wstępnie przygotowanej zawartości dla programu System Center Configuration Manager."
ms.custom: na
ms.date: 2/6/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: e80d1151-91db-4a27-8411-a957297b67d0
caps.latest.revision: 15
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 37e4f27fcea0bbdd39c9fd3ab38aa46e3059f73a
ms.openlocfilehash: d9dff97126c34a726677de60dd7647370c553b6e
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---

# <a name="manage-network-bandwidth-for-content"></a>Zarządzanie przepustowością sieci zawartości
Aby ułatwić zarządzanie przepustowości sieci używanej dla procesu zarządzania zawartością programu System Center Configuration Manager, można formantów wbudowanych planowania i ograniczania przepustowości. Można również użyć wstępnie przygotowanej zawartości. W poniższych sekcjach opisano te opcje bardziej szczegółowo.

##  <a name="BKMK_PlanningForThrottling"></a>Planowania i ograniczania przepustowości  

 Podczas tworzenia pakietu, zmienić ścieżkę źródłową zawartości lub zaktualizować zawartość w punkcie dystrybucji, pliki są kopiowane ze ścieżki źródłowej do biblioteki zawartości na serwerze lokacji. Następnie zawartość jest kopiowana z biblioteki zawartości na serwerze lokacji do biblioteki zawartości w punktach dystrybucji. Gdy pliki zawartości źródłowej są aktualizowane i pliki źródłowe zostały już rozpowszechnione, Configuration Manager pobiera tylko nowe lub zaktualizowane pliki i wysyła je do punktu dystrybucji.

 Kontrolki planowania i ograniczania przepustowości służy do komunikacji z lokacjami i do komunikacji między serwerem lokacji a zdalnym punkcie dystrybucji. Jeśli przepustowość sieci jest ograniczona nawet po skonfigurowaniu opcji planowania i ograniczania przepustowości, należy rozważyć wstępne przygotowanie zawartości w punkcie dystrybucji.  

 W programie Configuration Manager można skonfigurować harmonogram i określ ustawienia ograniczania przepustowości w zdalnych punktach dystrybucji określających sposób dystrybucji zawartości jest wykonywana i. Każdy zdalny punkt dystrybucji może mieć różne konfiguracje pomagające określenia ograniczeń przepustowości sieci między serwerem lokacji do zdalnych punktów dystrybucji. Ustawienia planowania i ograniczania przepustowości do zdalnego punktu dystrybucji są podobne do ustawień adresu standardowego nadawcy. W tym przypadku są używane przez nowy składnik, Menedżer transferu pakietów.

 Menedżer transferu pakietów dystrybuuje zawartość z serwera lokacji z lokacji głównej lub lokacji dodatkowej do punktu dystrybucji zainstalowanego w systemie lokacji. Ustawienia ograniczania są określone na **limity szybkości** zaś ustawienia planowania są określone na **harmonogram** karty dla punktu dystrybucji, który nie znajduje się na serwerze lokacji. Ustawienia czasu są oparte na strefie czasowej witryny wysyłania, a nie punktu dystrybucji.  

> [!IMPORTANT]  
>  **Limity szybkości** i **harmonogram** będą wyświetlane tylko we właściwościach punktów dystrybucji, które nie są zainstalowane na serwerze lokacji.  

Aby uzyskać więcej informacji, zobacz [zainstalować i skonfigurować punkty dystrybucji programu System Center Configuration Manager](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points).  

##  <a name="BKMK_PrestagingContent"></a>Wstępnie przygotowanej zawartości  
 Zawartość, aby dodać pliki zawartości do biblioteki zawartości w punkcie dystrybucji lub serwera lokacji, przed rozpoczęciem dystrybucji zawartość można wstępnie przygotować. Pliki zawartości znajdują się już w bibliotece zawartości, dlatego nie przesyłają przez sieć podczas dystrybucji zawartości. Można wstępnie przygotować pliki zawartości aplikacji i pakietów.  

W konsoli programu Configuration Manager wybierz zawartość, który chcesz wstępnie przygotować, a następnie użyć **Tworzenie kreatora przygotowanego pliku zawartości**. Spowoduje to utworzenie skompresowanego, przygotowanego pliku zawartości, który zawiera pliki i skojarzone metadane dla zawartości. Następnie możesz ręcznie zaimportować zawartość w punkcie dystrybucji lub serwerze lokacji. Weź pod uwagę następujące kwestie:  

-   Podczas importowania wstępnie przygotowanego pliku zawartości na serwerze lokacji pliki zawartości są dodawane do biblioteki zawartości na serwerze lokacji, a następnie zarejestrowana w bazie danych serwera lokacji.  

-   Podczas importowania wstępnie przygotowanego pliku zawartości w punkcie dystrybucji pliki zawartości są dodawane do biblioteki zawartości w punkcie dystrybucji. Komunikat o stanie są wysyłane do serwera lokacji, który informuje o lokacji, czy zawartość jest dostępna w punkcie dystrybucji.  

Opcjonalnie można skonfigurować punkt dystrybucji jako **wstępnie** ułatwia zarządzanie dystrybucją zawartości. Następnie podczas dystrybucji zawartości można wybrać, czy ma być:  

-   Wstępne przygotowanie zawartości w punkcie dystrybucji.  

-   Wstępnie przygotowywać zawartość początkową pakietu, a następnie stosować standardowy proces dystrybucji zawartości, gdy są dostępne aktualizacje zawartości.  

-   Zawsze stosować standardowy proces dystrybucji zawartości w pakiecie.  

###  <a name="BKMK_DetermineToPrestageContent"></a>Określanie, czy należy wstępnie przygotować zawartość  
 Należy rozważyć wstępne przygotowanie zawartości aplikacji i pakietów w następujących scenariuszach:  

-   **Aby rozwiązać problem z ograniczoną przepustowością z serwera lokacji do punktu dystrybucji.** Jeśli planowanie i dławienie nie są wystarczający, aby rozwiązują problemów dotyczących przepustowości, należy rozważyć wstępne przygotowanie zawartości w punkcie dystrybucji. Każdy punkt dystrybucji ma **Włącz ten punkt dystrybucji dla wstępnie przygotowanej zawartości** ustawienie, które są dostępne we właściwościach punktu dystrybucji. Po włączeniu tej opcji punkt dystrybucji został rozpoznany jako wstępnie przygotowany punkt dystrybucji, a można wybrać sposób zarządzania zawartością w poszczególnych pakietów.  

    Następujące ustawienia są dostępne w oknie właściwości aplikacji, pakietu, pakietu sterowników, obrazu rozruchowego, Instalatora systemu operacyjnego i obraz. Te ustawienia umożliwiają wybieranie sposobu zarządzania dystrybucją w zdalnych punktach dystrybucji rozpoznanych jako wstępnie przygotowane zawartości:  

    -   **Automatycznie Pobierz zawartość po przypisaniu pakietów do punktów dystrybucji**: Użyj tej opcji, gdy masz mniejszych pakietów, a ustawienia planowania i ograniczania przepustowości zapewniają wystarczającą kontrolę nad dystrybucją zawartości.  

    -   **Pobieraj tylko zmiany zawartości w punkcie dystrybucji**: Użyj tej opcji, jeśli oczekujesz, że przyszłe aktualizacje zawartości w pakiecie będą generalnie mniejsze niż początkowego pakietu. Na przykład ponieważ rozmiar początkowego pakietu przekracza 700 MB i jest zbyt duży, aby wysłać za pośrednictwem sieci mogą wstępnie przygotować aplikacji, takie jak Microsoft Office. Jednak aktualizacje zawartości tego pakietu może być mniejsza niż 10 MB, a co umożliwia ich dystrybucję za pośrednictwem sieci. Innym przykładem mogą być pakiety sterowników, których pakiet wstępny jest duży, lecz kolejne dodatki do pakietu mogą mieć niewielkie rozmiary.  

    -   **Ręcznie skopiuj zawartość tego pakietu do punktu dystrybucji**: Tej opcji należy użyć, gdy dużych pakietów zawierających na przykład system operacyjny i nigdy nie chcesz używać sieci do dystrybucji zawartości do punktu dystrybucji. Po wybraniu tej opcji należy wstępnie przygotować zawartość w punkcie dystrybucji.  

    > [!IMPORTANT]  
    >  Poprzednie opcje można stosować poszczególnych pakietów, pod warunkiem punkt dystrybucji został rozpoznany jako wstępnie przygotowane. Punkty dystrybucji, które nie zostały zidentyfikowane jako wstępnie przygotowane będą ignorować te ustawienia. W takim przypadku zawartość będzie zawsze dystrybuowana przez sieć z serwera lokacji do punktów dystrybucji.  

-   **Aby przywrócić bibliotekę zawartości na serwerze lokacji.** W przypadku awarii serwera lokacji informacje o pakietach i aplikacjach znajdujące się w bibliotece zawartości przywróceniu bazy danych lokacji w ramach procesu przywracania, ale nie przywrócono plików biblioteki zawartości w ramach procesu. Jeśli nie masz kopii zapasowej systemu plików umożliwiająca przywrócenie biblioteki zawartości, można utworzyć wstępnie przygotowany plik zawartości z innej lokacji, który zawiera pakiety i aplikacje, które są potrzebne. Następnie można wyodrębnić wstępnie przygotowany plik zawartości na odzyskanym serwerze lokacji. Aby uzyskać więcej informacji o kopii zapasowej serwera lokacji i odzyskiwania, zobacz [kopii zapasowych i odzyskiwania dla programu System Center Configuration Manager](/sccm/protect/understand/backup-and-recovery).  

