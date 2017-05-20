---
title: "Funkcje w wersji wstępnej | Dokumentacja firmy Microsoft"
description: "Wstępna funkcji w programie System Center Configuration Manager"
ms.custom: na
ms.date: 4/24/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 6bce416b-761d-4b23-bd33-5b7c30edb10d
caps.latest.revision: 36
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: b12fcb3c372c34ee47306a9b536c3d0c4764b8be
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="pre-release-features-in-system-center-configuration-manager"></a>Wstępna funkcji w programie System Center Configuration Manager
*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Funkcje wersji wstępnej są funkcje, które znajdują się w bieżącej gałęzi dla wczesnych testowanie w środowisku produkcyjnym. Są w pełni obsługiwane, ale są nadal w rozwoju active i może zostać wyświetlony zmiany, dopóki ich wychodzenia kategorii wersji wstępnej.

 Przed użyciem funkcji wersji wstępnej, należy udzielić zgody, aby korzystały funkcji wersji wstępnej z konsoli programu Configuration Manager można wybrać i włączyć ich użycia.  

Wyrażenia zgody jest akcja jednorazowa danej hierarchii, którego nie można cofnąć. Dopóki zgody, nie można włączyć nowe funkcje wersji wstępnej dołączonej do aktualizacji.

Zgody, w konsoli przejdź do **Administracja** > **konfiguracja lokacji** > **witryny**, a następnie wybierz **ustawienia hierarchii**. Na **ogólne** , wybierz **zgodę na korzystanie z funkcji wersji wstępnej**.

 > [!NOTE]
 > Po włączeniu wcześniej funkcji wersji wstępnej z 1602 aktualizacji, przed zainstalowaniem aktualizacji nowszy, te funkcje pozostać włączone do użytku, nawet jeśli nie ma zgody na korzystanie z funkcji wersji wstępnej.

Po zainstalowaniu aktualizacji, która zawiera funkcje wersji wstępnej te funkcje są widoczne w programie obsługi kreatora i aktualizacje przy użyciu funkcji regularnych zawartych w aktualizacji:
  - **Jeśli wyrazić zgodę:** Funkcje wersji wstępnej z w ramach aktualizacji i obsługi kreatora można włączyć podczas instalowania aktualizacji. Aby to zrobić, wybierz funkcje wersji wstępnej w taki sam sposób, jak wszystkie inne funkcje.     

    Opcjonalnie można poczekać do włączenia funkcji wersji wstępnej, później z **Administracja** > **aktualizacji i obsługi** > **funkcje** węzeł konsoli. W **funkcji** węzła, wybierz tę funkcję, a następnie wybierz **włączyć**. Ta opcja jest wyszarzone, dopóki wyrażenia zgody. (Przed wersją 1702, aktualizacji i obsługi został pod **Administracja** > **usług w chmurze**.)
  -   **Jeśli nie można wyrazić zgodę:** Podczas instalowania aktualizacji funkcji wersji wstępnej są widoczne w Kreatorze obsługi i aktualizacji, ale są wygaszone i nie może być włączone. Po zainstalowaniu tej aktualizacji można wyświetlić te funkcje w **funkcji** węzła, ale nie można włączyć je do czasu po wyrazić zgodę **ustawienia hierarchii**.

Jeśli udostępniła zgody w autonomicznej lokacji głównej, a następnie rozwiń hierarchię przez zainstalowanie nowej witryny Administracja centralna, należy udzielić zgody ponownie w witrynie Administracja centralna.

 Po włączeniu funkcji wersji wstępnej, Menedżer hierarchii programu Configuration Manager (HMAN) musi przetworzyć zmiany przed danej funkcji staje się dostępny. Często jest bezpośrednim przetwarzanie zmiany, ale może potrwać do 30 minut, w zależności od HMAN cykl przetwarzania. Po przetworzeniu zmiany należy ponownie uruchomić konsolę można było wyświetlić nowy interfejs użytkownika powiązanych z daną funkcją.

**Dostępne są następujące funkcje wersji wstępnej:**

 |Funkcja          |Dodany jako wstępna | Dodane jako funkcja pełny|  
|------------------|---------------------|---------------------|
| Zarządzanie urządzeniami ochronę za pomocą programu Configuration Manager |  [Wersja 1702](/sccm/protect/deploy-use/use-device-guard-with-configuration-manager)|![Jeszcze nie](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Sprawdź, czy uruchomiony pliki wykonywalne przed zainstalowaniem aplikacji  |   [Wersja 1702](/sccm/apps/deploy-use/deploy-applications#how-to-check-for-running-executable-files-before-installing-an-application) |![Jeszcze nie](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Punkt usługi magazynu danych  |  [Wersja 1702](/sccm/core/servers/manage/data-warehouse) |![Jeszcze nie](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Buforowanie równorzędne dla dystrybucji zawartości do klientów |  [Wersja 1610](/sccm/core/plan-design/hierarchy/client-peer-cache) |![Jeszcze nie](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Brama zarządzania chmury |  [Wersja 1610](/sccm/core/clients/manage/plan-cloud-management-gateway) |![Jeszcze nie](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Pulpit nawigacyjny źródła danych klienta |  [Wersja 1610](/sccm/core/servers/deploy/configure/monitor-content-you-have-distributed#client-data-sources-dashboard) |![Jeszcze nie](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Łącznik programu Microsoft Operations zarządzania Suite  | [Wersja 1606](../../../core/clients/manage/sync-data-microsoft-operations-management-suite.md) |![Jeszcze nie](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
| Obsługa klastra kolekcji pamiętać (Usługa grupy serwerów)| [Wersja 1602](../../../core/get-started/capabilities-in-technical-preview-1605.md#BKMK_ServerGroups)|![Jeszcze nie](media/83c5d168-8faf-4e8e-920b-528e3c43ffd4.gif)|
|Dostęp warunkowy dla komputerów zarządzanych przez program System Center Configuration Manager | [Wersja 1602](../../../protect/deploy-use/manage-access-to-o365-services-for-pcs-managed-by-sccm.md)     | [Wersja 1702](/sccm/mdm/deploy-use/manage-access-to-services)                     |

