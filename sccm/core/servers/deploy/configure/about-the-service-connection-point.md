---
title: Punkt połączenia usługi
titleSuffix: Configuration Manager
description: Więcej informacji na temat tej roli systemu lokacji programu Configuration Manager i Poznaj i Zaplanuj zakres jego zastosowań.
ms.date: 1/29/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: bc2282d5-0571-465b-9528-a555855eaacd
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 7328d7053d1fb06487e255fe4a24d6955c99c4b0
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="about-the-service-connection-point-in-system-center-configuration-manager"></a>Informacje o punkcie połączenia z usługą w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Punkt połączenia z usługą System Center Configuration Manager jest rolą systemu lokacji pełniącą kilka ważnych funkcji dla hierarchii. Przed skonfigurowaniem punktu połączenia z usługą Poznaj i Zaplanuj zakres jego zastosowań.  Planowanie użycia może mieć wpływ na sposób konfigurowania tej roli systemu lokacji:  

-   **Zarządzanie urządzeniami przenośnymi w usłudze Microsoft Intune** — ta rola zastępuje łącznik usługi Windows Intune, poprzednie wersje programu Configuration Manager używane, a także można skonfigurować za pomocą Szczegóły subskrypcji usługi Intune. Zobacz [hybrydowego zarządzania urządzeniami przenośnymi (MDM) z programu System Center Configuration Manager i Microsoft Intune](../../../../mdm/understand/hybrid-mobile-device-management.md).  

-   **Zarządzanie urządzeniami przenośnymi za pomocą lokalnego zarządzania urządzeniami Przenośnymi** — ta rola zapewnia obsługę urządzeń lokalnych, które można zarządzać i które nie łączą się z Internetem. Zobacz [zarządzanie urządzeniami przenośnymi za pomocą infrastruktury lokalnej w programie System Center Configuration Manager](../../../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md).  

-   **Przekazywanie danych użycia z infrastruktury programu Configuration Manager** — można kontrolować poziom lub ilość szczegółów przekazywania. Przekazane dane ułatwiają:  

    -   Aktywne identyfikowanie i rozwiązywanie problemów  

    -   Poprawa jakości produktów i usług firmy Microsoft  

    -   Identyfikowanie aktualizacji dla programu Configuration Manager, które mają zastosowanie do wersji programu Configuration Manager używanej  

  Aby uzyskać informacje o danych, która gromadzi każdy poziom oraz sposobu zmiany poziomie kolekcji po zainstalowaniu roli, zobacz [diagnostyczne i dane użycia](/sccm/core/plan-design/diagnostics/diagnostics-and-usage-data). Następnie kliknij link dla programu Configuration Manager używanej wersji.  

  Aby uzyskać więcej informacji, zobacz [poziomy użycia danych i ustawień](../../../../core/servers/deploy/install/setup-reference.md#bkmk_usage).  

-   **Pobierz aktualizacje, które są stosowane do infrastruktury programu Configuration Manager** — tylko odpowiednie aktualizacje dla infrastruktury są udostępniane na podstawie danych użycia, możesz przekazać.  

- **Każda hierarchia obsługuje jedno wystąpienie tej roli:**  

 -   Rola systemu lokacji można zainstalować tylko w lokacji najwyższego poziomu w hierarchii, która jest centralnej lokacji administracyjnej lub autonomicznej lokacji głównej.  

  -   Po rozwinięciu autonomicznej lokacji głównej do większej hierarchii, należy odinstalować tę rolę z lokacji głównej, a następnie zainstalować ją w centralnej lokacji administracyjnej.  


##  <a name="bkmk_modes"></a> Tryby pracy  
 Punkt połączenia z usługą obsługuje dwa tryby operacyjne:  

-   W **trybu online**, punkt połączenia z usługą automatycznie sprawdza co 24 godziny dla aktualizacji. Pobiera nowe aktualizacje, które są dostępne dla bieżącej infrastruktury i wersji produktu, aby udostępnić je w konsoli programu Configuration Manager.  

-   W **w trybie offline**, punkt połączenia usługi nie połączyć z usługą w chmurze firmy Microsoft. [Użyj narzędzia połączenia z usługą System Center Configuration Manager](../../../../core/servers/manage/use-the-service-connection-tool.md) ręcznie importować dostępne aktualizacje.  

Jeśli zmienisz między trybami online lub offline, po zainstalowaniu punktu połączenia usługi przed zmiana zacznie obowiązywać należy ponownie uruchomić wątek SMS_DMP_DOWNLOADER usługi SMS_Executive programu Configuration Manager. Można użyć Menedżera usług programu Configuration Manager do ponownego uruchomienia tylko wątku sms_dmp_downloader usługi SMS_Executive. Można również uruchomić ponownie usługę SMS_Executive dla programu Configuration Manager, co spowoduje ponowne uruchomienie większości składników lokacji. Ewentualnie możesz poczekać zaplanowanego zadania, takie jak kopii zapasowej lokacji, które spowoduje zatrzymanie i później ponowne uruchomienie w usługę SMS_Executive dla Ciebie.  

Aby użyć Menedżera usług programu Configuration Manager, w konsoli przejdź do **monitorowanie** > **stan systemu** > **stan składnika**, wybierz **Start**, a następnie wybierz pozycję **Menedżera usług programu Configuration Manager**. W menedżerze usług:  

-   W okienku nawigacji rozwiń węzeł lokacji, rozwiń **składniki**, a następnie wybierz składnik, który chcesz ponownie uruchomić komputer.  

-   W okienku szczegółów kliknij prawym przyciskiem myszy składnik, a następnie wybierz pozycję **zapytania**.  

-   Po potwierdzeniu stanu składnika ponownie kliknij prawym przyciskiem myszy składnik, a następnie wybierz **zatrzymać**.  

-   **Zapytanie** składnik ponownie, aby potwierdzić, czy jest zatrzymana. Kliknij prawym przyciskiem myszy składnik jeszcze raz, a następnie wybierz pozycję **Start**.  

> [!IMPORTANT]  
>  Proces, który dodaje subskrypcję Microsoft Intune do punktu połączenia z usługą automatycznie ustawia rolę systemu lokacji w trybie online. Punkt połączenia usługi nie obsługuje w trybie offline, gdy jest skonfigurowana z subskrypcji usługi Intune.  

**Gdy rola jest instalowana na komputerze sterowanym zdalnie z serwera lokacji:**  

-   Konto komputera serwera lokacji musi być administratorem lokalnym na komputerze, który obsługuje połączenia zdalne usługi.

-   Należy skonfigurować serwer systemu lokacji, który jest hostem roli przy użyciu konta instalacji systemu lokacji.  

-   Menedżer dystrybucji na serwerze lokacji używa konta instalacji systemu lokacji do przesyłania aktualizacji z punktu połączenia usługi.

##  <a name="bkmk_urls"></a> Wymagania dotyczące dostępu do Internetu  
Aby umożliwić wykonanie operacji, komputera, który jest hostem punktu połączenia usługi, a wszystkie zapory między tym komputerem i Internetu musi umożliwiała komunikację za pomocą portu wychodzącego **TCP 443** dla protokołu HTTPS i wychodzący port  **TCP 80** dla protokołu HTTP do poniżej lokalizacji w Internecie. Punkt połączenia usługi również obsługuje przy użyciu serwera proxy sieci web (z lub bez uwierzytelniania) Aby użyć tych lokalizacji.  Jeśli musisz skonfigurować konto użytkownika serwera proxy sieci web, zobacz: [Obsługa serwerów proxy w programie System Center Configuration Manager](/sccm/core/plan-design/network/proxy-server-support).

**Aktualizacje i obsługa**  

-   *.akamaiedge.net  

-   *.akamaitechnologies.com 

-   *.manage.microsoft.com

-   go.microsoft.com

-   blob.core.windows.net  

-   download.microsoft.com  

-   download.windowsupdate.com

-   sccmconnected-a01.cloudapp.net  

**Microsoft Intune**  

-   *manage.microsoft.com  
-   https://bspmts.mp.microsoft.com/V
-   https://login.microsoftonline.com/{TenantID}


**Obsługa systemu Windows 10**  

-   download.microsoft.com  

-   https://go.microsoft.com/fwlink/?LinkID=619849  

## <a name="install-the-service-connection-point"></a>Zainstaluj punkt połączenia usługi
Po uruchomieniu **Instalator** Aby zainstalować lokację najwyższego poziomu hierarchii, masz możliwość zainstalowania punktu połączenia usługi.

Po uruchomieniu instalacji lub ponownej instalacji roli systemu lokacji, należy użyć **dodawania ról systemu lokacji** kreatora lub **Utwórz serwer systemu lokacji** kreatora w celu zainstalowania systemu lokacji na serwerze w lokacji najwyższego poziomu w hierarchii, oznacza to, centralnej lokacji administracyjnej lub autonomicznej lokacji głównej. Oba znajdują się na **Home** w konsoli w **administracji** > **konfiguracja lokacji** > **serwery i role systemu lokacji**.

## <a name="log-files-used-by-the-service-connection-point"></a>Pliki dziennika używanych przez punkt połączenia usługi
Aby wyświetlić informacje dotyczące przekazywania do firmy Microsoft, Wyświetl **Dmpuploader.log** na komputerze z uruchomionym programem punkt połączenia usługi.  Pliki do pobrania, w tym postęp pobierania aktualizacji, wyświetlić **Dmpdownloader.log**. Aby uzyskać pełną listę dzienników powiązane z punktem połączenia usługi, zobacz [punkt połączenia z usługą](/sccm/core/plan-design/hierarchy/log-files#BKMK_WITLog) w artykule pliki dziennika programu Configuration Manager.

Umożliwia także następujące zaprezentowane przepływ procesu i wpisy dziennika klucza dla pobierania aktualizacji i replikacja aktualizacji do innych lokacji:
 - [Schemat blokowy — pobieranie aktualizacji](/sccm/core/servers/manage/download-updates-flowchart)
 - [Schemat blokowy — aktualizacja replikacji](/sccm/core/servers/manage/update-replication-flowchart)
