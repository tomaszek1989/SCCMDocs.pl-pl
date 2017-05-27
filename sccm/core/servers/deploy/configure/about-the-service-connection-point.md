---
title: "Punkt połączenia usługi | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat tej roli systemu lokacji programu Configuration Manager i zrozumieć i planowanie jego zakresu zastosowań."
ms.custom: na
ms.date: 3/30/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: bc2282d5-0571-465b-9528-a555855eaacd
caps.latest.revision: 18
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6accec2d356861b273b25ba2b6338d9684a46ff6
ms.openlocfilehash: ad6df047beff670411d203220576b87f7d56d50c
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="about-the-service-connection-point-in-system-center-configuration-manager"></a>Informacje o punkcie połączenia z usługą w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Punkt połączenia usługi System Center Configuration Manager jest rola systemu lokacji, która obsługuje wiele ważnych funkcji dla hierarchii. Przed skonfigurowaniem punktu połączenia usługi i planowaniu jej w zakresie zastosowań, które mogą mieć wpływ na sposób skonfigurować tę rolę systemu lokacji:  

-   **Zarządzanie urządzeniami przenośnymi w usłudze Microsoft Intune** -zastępuje tę rolę łącznika usługi Windows Intune, który poprzednie wersje programu Configuration Manager używane, można skonfigurować za pomocą programu Szczegóły subskrypcji usługi Intune. Zobacz [hybrydowego zarządzania urządzeniami przenośnymi (MDM) za pomocą programu System Center Configuration Manager i Microsoft Intune](../../../../mdm/understand/hybrid-mobile-device-management.md).  

-   **Zarządzanie urządzeniami przenośnymi za pomocą lokalnych MDM** -tej roli zapewnia obsługę urządzeń lokalnych, które można zarządzać i które nie łączy się z Internetem. Zobacz [zarządzania urządzeniami przenośnymi z infrastruktury lokalnej w programie System Center Configuration Manager](../../../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md).  

-   **Przekazywanie danych do użycia z infrastrukturą programu Configuration Manager** -można kontrolować poziom lub liczbę szczegółów, który należy przekazać. Przekazane dane ułatwiają firmie Microsoft realizację następujących celów:  

    -   Aktywne identyfikowanie i rozwiązywanie problemów  

    -   Poprawa jakości produktów i usług firmy Microsoft  

    -   Określenie aktualizacji programu Configuration Manager odnoszą się do wersji programu Configuration Manager można użyć  

  Informacji o poszczególnych poziomów zbiera dane i jak zmienić poziom kolekcji, po zainstalowaniu roli można uzyskać [diagnostyki i dane dotyczące użycia](/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data), a następnie wykonaj łącze dla używanej wersji programu Configuration Manager można użyć.  

  Aby uzyskać dodatkowe informacje, zobacz [poziomów danych użycia i ustawienia](../../../../core/servers/deploy/install/setup-reference.md#bkmk_usage).  

-   **Pobierz aktualizacje, które są stosowane do infrastruktury programu Configuration Manager** — tylko odpowiednie aktualizacje w infrastrukturze są udostępniane na podstawie danych użycia przekazywania.  

- **Każda hierarchia obsługuje pojedyncze wystąpienie tej roli:**  

 -   Rola systemu lokacji można zainstalować tylko w lokacji najwyższego poziomu w hierarchii, która jest centralnej lokacji administracyjnej lub autonomicznej lokacji głównej.  

  -   Po rozwinięciu autonomicznej lokacji głównej do większej hierarchii należy odinstalować tę rolę z lokacji głównej, a następnie można zainstalować w witrynie Administracja centralna.  


##  <a name="bkmk_modes"></a>Tryby działania  
 Punkt połączenia z usługą obsługuje dwa tryby operacyjne:  

-   W **trybu online**, punkt połączenia usługi automatycznie sprawdza co 24 godziny, aktualizacje, a następnie pobiera nowe aktualizacje, które są dostępne dla bieżącej wersji produktu i infrastruktury udostępnić je w konsoli programu Configuration Manager.  

-   W **trybu offline**, punkt połączenia usługi nie łączy się usługa w chmurze firmy Microsoft, a użytkownik będzie musiał ręcznie [użyć narzędzia połączenia usługi System Center Configuration Manager](../../../../core/servers/manage/use-the-service-connection-tool.md) do importowania dostępnych aktualizacji.  

Po zmianie między trybem online lub offline, po zainstalowaniu punktu połączenia usługi, należy ponownie uruchomić wątku SMS_DMP_DOWNLOADER usługi SMS_Executive programu Configuration Manager, zanim ta zmiana staje się obowiązująca. W tym celu należy użyć Menedżera usług programu Configuration Manager ponownie uruchomić tylko wątku SMS_DMP_DOWNLOADER usługę SMS_Executive. Można także ponownie uruchomić usługę SMS_Executive programu Configuration Manager, co spowoduje ponowne uruchomienie większość składników lokacji, lub możesz poczekać zaplanowanego zadania, takie jak kopii zapasowej lokacji, co zatrzymuje, a następnie później uruchamia ponownie usługę SMS_Executive dla Ciebie.  

Używać Menedżera usług programu Configuration Manager, w konsoli przejdź do **monitorowanie** > **stan systemu** > **stan składnika**, wybierz **Start**, a następnie wybierz **usług programu Configuration Manager**. W menedżerze usług:  

-   W okienku nawigacji rozwiń węzeł lokacji, rozwiń **składniki**, a następnie wybierz składnik, który chcesz ponownie uruchomić komputer.  

-   W okienku szczegółów kliknij prawym przyciskiem myszy składnik, a następnie wybierz **kwerendy**.  

-   Po potwierdzeniu stanu składnika, ponownie kliknij prawym przyciskiem myszy składnik, a następnie wybierz **zatrzymać**.  

-   **Kwerenda** składnik ponownie, aby potwierdzić, że jest zatrzymana, kliknij prawym przyciskiem myszy składnik jeszcze raz, a następnie wybierz **Start**.  

> [!IMPORTANT]  
>  Proces, który automatycznie dodaje subskrypcję Microsoft Intune do punktu połączenia usługi ustawia Rola systemu lokacji w trybie online. Punkt połączenia usługi nie obsługuje trybu offline, gdy jest skonfigurowana z subskrypcji usługi Intune.  

**Gdy rola instaluje na komputerze sterowanym zdalnie z serwera lokacji:**  

-   Konto komputera serwera lokacji musi być administratorem lokalnym na komputerze, który obsługuje połączenia usługi zdalnej.

-   Należy skonfigurować serwer systemu lokacji, który jest hostem roli przy użyciu konta instalacji systemu lokacji.  

-   Menedżer dystrybucji na serwerze lokacji używa konta instalacji systemu lokacji do transferowania aktualizacji z punktu połączenia usługi.

##  <a name="bkmk_urls"></a>Wymagania dotyczące dostępu do Internetu  
Aby włączyć operacji, komputera, który obsługuje punkt połączenia usługi i wszelkie zapory między tym komputerem a Internetem musi pomyślnie przejść komunikacji za pośrednictwem **port TCP 443** i **port TCP 443** w następujących lokalizacjach internetowych. Punkt połączenia usługi również obsługuje przy użyciu serwera proxy sieci web (z lub bez uwierzytelniania) do użycia w tych lokalizacjach.  Jeśli musisz skonfigurować konto serwera proxy sieci web, zobacz: [Obsługa serwera proxy w programie System Center Configuration Manager](/sccm/core/plan-design/network/proxy-server-support).

**Obsługa**  

-   *.akamaiedge.net  

-   *.manage.microsoft.com

-   go.microsoft.com

-   blob.core.windows.net  

-   download.microsoft.com  

-   Download.windowsupdate.com

-   sccmconnected-a01.cloudapp.net  

**Microsoft Intune**  

-   *manage.microsoft.com  
-   https://bspmts.MP.microsoft.com/V
-   https://login.microsoftonline.com/ {identyfikatora dzierżawcy}


**Obsługa systemu Windows 10**  

-   download.microsoft.com  

-   https://go.microsoft.com/fwlink/?LinkID=619849  

## <a name="install-the-service-connection-point"></a>Zainstaluj punkt połączenia usługi
Po uruchomieniu **instalacji** do zainstalowania lokacji najwyższego poziomu w hierarchii, należy zainstalować punkt połączenia usługi.

Po uruchomieniu instalacji lub ponownej Rola systemu lokacji, należy użyć **Dodaj role systemu lokacji** kreatora lub **Utwórz serwer systemu lokacji** kreatora w celu zainstalowania systemu lokacji na serwerze w lokacji najwyższego poziomu w hierarchii, to znaczy, centralnej lokacji administracyjnej lub autonomicznej lokacji głównej. Oba są na **Home** w konsoli programu na **Administracja** > **konfiguracja lokacji** > **serwery i role systemu lokacji**.

## <a name="log-files-used-by-the-service-connection-point"></a>Pliki dziennika używanych przez punkt połączenia usługi
Aby wyświetlić informacje o operacji przekazywania do firmy Microsoft, należy wyświetlić **Dmpuploader.log** na komputerze z uruchomionym punktu połączenia usługi.  Pliki do pobrania, w tym postęp pobierania aktualizacji, wyświetlanie **Dmpdownloader.log**. Pełna lista dzienniki dotyczące punktu połączenia usługi można znaleźć w temacie [punktem połączenia usługi](/sccm/core/plan-design/hierarchy/log-files#BKMK_WITLog) w temacie pliki dziennika programu Configuration Manager.

Umożliwia także następujące blokowych zrozumienie przepływ procesu i wpisy dziennika klucza pobierania aktualizacji i replikacji aktualizacji do innych lokacji:
 - [Schemat blokowy — Pobierz aktualizacje](/sccm/core/servers/manage/download-updates-flowchart)
 - [Schemat blokowy — aktualizacja replikacji](/sccm/core/servers/manage/update-replication-flowchart)

