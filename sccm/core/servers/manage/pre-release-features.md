---
title: Funkcje wersji wstępnej
titleSuffix: Configuration Manager
description: Funkcje wersji wstępnej są funkcje, które znajdują się w bieżącej gałęzi do wczesnego testowania w środowisku produkcyjnym.
ms.date: 05/01/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 6bce416b-761d-4b23-bd33-5b7c30edb10d
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: d4e9664832b37dd05f001404012acab80fd87a43
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="pre-release-features-in-system-center-configuration-manager"></a>Funkcje wersji wstępnej programu System Center Configuration Manager
*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Funkcje wersji wstępnej są funkcje, które znajdują się w bieżącej gałęzi do wczesnego testowania w środowisku produkcyjnym. Te funkcje są w pełni obsługiwane, ale są nadal w fazie projektowania active i może odbierać zmiany, dopóki ich wychodzenia z kategorii wersji wstępnej.

 Przed użyciem funkcji wersji wstępnej, należy udzielić zgody, aby korzystały funkcje wersji wstępnej z poziomu konsoli programu Configuration Manager można wybrać i włączyć ich używania.  

Wyrażenia zgody to działanie jednorazowe dla hierarchii, którego nie można cofnąć. Dopóki zgody, nie można włączyć nowe funkcje wersji wstępnej dołączone do aktualizacji. Po włączeniu funkcji wersji wstępnej, nie można wyłączyć go.

Aby udzielić zgody, w konsoli przejdź do **administracji** > **konfiguracja lokacji** > **witryny**, a następnie wybierz pozycję **ustawienia hierarchii**. Na **ogólne** , wybierz pozycję **wyrażenia zgody na korzystanie z funkcji wersji wstępnej**.

Po zainstalowaniu aktualizacji, która zawiera funkcje wersji wstępnej, te funkcje są widoczne w węźle aktualizacje i obsługa kreatora z standardowe funkcje zawarte w aktualizacji:
  - **Jeśli musisz wyrazić zgodę:** Funkcje wersji wstępnej z aktualizacji i obsługi kreatora można włączyć podczas instalowania aktualizacji. Aby to zrobić, wybierz funkcje wersji wstępnej w taki sam sposób, jak wszystkie inne funkcje.     

    Opcjonalnie można poczekać do włączenia funkcji wersji wstępnej później w **administracji** > **aktualizacje i obsługa** > **funkcje** węzła konsoli. W **funkcje** węzła wybierz funkcję, a następnie wybierz **włączyć**. Ta opcja jest szary, dopóki wyrażenia zgody. (Przed wersji 1702, aktualizacje i obsługa znajdowało się pod **administracji** > **usługi w chmurze**.)
  -   **Jeśli nie mają zgody:** Podczas instalowania aktualizacji, funkcje wersji wstępnej są widoczne w węźle aktualizacje i obsługa kreatora, ale są wygaszone i nie można włączyć. Po zainstalowaniu tej aktualizacji można wyświetlić te funkcje w **funkcje** węzła. Jednak nie można włączyć je dopiero po wyrazić zgodę **ustawienia hierarchii**.


> [!Important]  
> W hierarchii wielu lokacji można włączyć tylko funkcje opcjonalne lub wersji wstępnej z centralnej lokacji administracyjnej. Takie zachowanie gwarantuje, że nie ma żadnych konfliktów całej hierarchii. <!--507197-->  
> Jeśli udzielił zgody w autonomicznej lokacji głównej, a następnie rozwiń węzeł hierarchii, instalując nową centralną lokację administracyjną, należy wyrazić zgodę ponownie w witrynie Administracja centralna.  

 Po włączeniu funkcji wersji wstępnej, Menedżer hierarchii programu Configuration Manager (HMAN) musi przetworzyć zmiany, zanim ta funkcja stanie się dostępny. Przetwarzanie zmiana jest często natychmiastowe, ale może potrwać do 30 minut, w zależności od HMAN cykl przetwarzania. Po przetworzeniu zmiana wymaga ponownego uruchomienia konsoli można wyświetlić nowy interfejs użytkownika związane z tej funkcji.

**Dostępne są następujące funkcje wersji wstępnej:**

 |Funkcja          |Dodany jako wersji wstępnej | Dodaje funkcję Pełna|  
|------------------|---------------------|---------------------|
|Obsługuje Cisco AnyConnect 4.0.07x i później dla systemu iOS<!--1357393-->|[Wersja 1802](/sccm/mdm/deploy-use/create-vpn-profiles)|![Jeszcze nie](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
|Etapowego wdrażania<!--1356837-->|[Wersja 1802](/sccm/osd/deploy-use/create-phased-deployment-for-task-sequence)|![Jeszcze nie](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Uruchom sekwencję zadań <!-- 1261338 --> |  [Wersja 1710](/sccm/osd/understand/task-sequence-steps#child-task-sequence) |[Wersja 1802](/sccm/osd/deploy-use/manage-task-sequences-to-automate-tasks#add-child-task-sequences-to-a-task-sequence)|
| Windows Defender wykorzystać zabezpieczenia <!-- 1355468 --> |  [Wersja 1710](/sccm/protect/deploy-use/create-deploy-exploit-guard-policy) |[Wersja 1802](/sccm/protect/deploy-use/create-deploy-exploit-guard-policy)|
| Ocena zaświadczania o kondycji urządzenia dla zasad dostępu warunkowego zgodności <!-- 1235616 --> |  [Wersja 1710](/sccm/mdm/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm) |[Wersja 1802](/sccm/mdm/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm)|
| Tworzenie i uruchamianie skryptów programu PowerShell z poziomu konsoli programu Configuration Manager <!-- 1236459 --> |  [Wersja 1706](/sccm/apps/deploy-use/create-deploy-scripts)|[Wersja 1802](/sccm/apps/deploy-use/create-deploy-scripts)|
| Zarządzanie aktualizacjami sterownik Microsoft Surface <!-- 1098490 --> |  [Wersja 1706](/sccm/sum/get-started/configure-classifications-and-products) | [Wersja 1710](/sccm/sum/get-started/configure-classifications-and-products)|
| Zarządzanie urządzeniami Guard z programu Configuration Manager <!-- 1319346 --> |  [Wersja 1702](/sccm/protect/deploy-use/use-device-guard-with-configuration-manager)|![Jeszcze nie](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Zadanie sekwencji wstępnie buforowanie zawartości <!-- 1021244 --> |  [Wersja 1702](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#configure-pre-cache-content) | [Wersja 1710](/sccm/osd/deploy-use/create-a-task-sequence-to-upgrade-an-operating-system#configure-pre-cache-content)|
| Sprawdź, czy uruchamianie plików wykonywalnych przed zainstalowaniem aplikacji <!-- 1284624 --> |   [Wersja 1702](/sccm/apps/deploy-use/deploy-applications#how-to-check-for-running-executable-files-before-installing-an-application) |[Wersja 1706](/sccm/apps/deploy-use/deploy-applications#how-to-check-for-running-executable-files-before-installing-an-application)|
| Punkt usługi magazynu danych <!-- 1277922 --> |  [Wersja 1702](/sccm/core/servers/manage/data-warehouse) |[Wersja 1706](/sccm/core/servers/manage/data-warehouse)|
| Równorzędnej pamięci podręcznej w celu dystrybucji zawartości do klientów <!-- 1101436 --> |  [Wersja 1610](/sccm/core/plan-design/hierarchy/client-peer-cache) | [Wersja 1710](/sccm/core/plan-design/hierarchy/client-peer-cache)|
| Brama zarządzania w chmurze <!-- 1101764 --> |  [Wersja 1610](/sccm/core/clients/manage/plan-cloud-management-gateway) |[Wersja 1802](/sccm/core/clients/manage/plan-cloud-management-gateway)|
| Łącznika programu Microsoft Operations Management Suite <!-- 1236739 --> | [Wersja 1606](../../../core/clients/manage/sync-data-microsoft-operations-management-suite.md) |[Wersja 1802](../../../core/clients/manage/sync-data-microsoft-operations-management-suite.md)|
| Obsługa kolekcji wykrywania klastra (Usługa grupy serwera) <!-- 1081776 --> | [Wersja 1602](../../../core/get-started/capabilities-in-technical-preview-1605.md#BKMK_ServerGroups)|![Jeszcze nie](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Dostęp warunkowy dla komputerów zarządzanych przez program System Center Configuration Manager <!--  --> | [Wersja 1602](/sccm/mdm/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm)     | [Wersja 1702](/sccm/mdm/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm)                     |
<!--Image used = ![Not yet](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif) -->

> [!Tip]  
> Aby uzyskać więcej informacji na funkcje — się w wersji pre, które należy najpierw włączyć, zobacz [Włącz funkcje opcjonalne aktualizacji](/sccm/core/servers/manage/install-in-console-updates#bkmk_options).  
> Aby uzyskać więcej informacji na temat funkcji, które są dostępne tylko w wersji zapoznawczej technical preview gałęzi, zobacz [Technical Preview](/sccm/core/get-started/technical-preview).  
