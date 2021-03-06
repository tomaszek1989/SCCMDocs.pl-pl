---
title: O uaktualnienie, aktualizacji i instalacji
titleSuffix: Configuration Manager
description: Różnice między warunki instalacji, aktualizacji i uaktualnień, podczas zarządzania infrastrukturą programu Configuration Manager.
ms.date: 1/11/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 17fab17f-304d-4f6a-87c7-30ab4f5521ed
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: ba59f4139a46ff5f073d15495196324540f7857a
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="about-upgrade-update-and-install-for-site-and-hierarchy-infrastructure"></a>O uaktualnienie aktualizacji i zainstalować infrastruktury lokacji i hierarchii

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


Podczas zarządzania w lokacji programu System Center Configuration Manager i infrastruktury hierarchii, warunki *uaktualnienia*, *aktualizacji*, i *zainstalować* służą do opisywania trzy oddzielne pojęcia.

## <a name="upgrade"></a>Upgrade
*Uaktualnij* lub *uaktualnienia w miejscu*, jest używany podczas konwertowania lokacji programu Configuration Manager 2012 lub hierarchii do wersji, która uruchamia System Center Configuration Manager.
Po uaktualnieniu programu System Center 2012 Configuration Manager do programu System Center Configuration Manager, będziesz nadal używać tych samych serwerów do hostowania witryn i serwerów lokacji i zachować istniejące dane i konfiguracje programu Configuration Manager.  Różni się to od [migracji](/sccm/core/migration/migrate-data-between-hierarchies) czyli sposób zachowania podczas korzystania z nowych lokacji programu System Center Configuration Manager zainstalowana na nowy sprzęt sieci konfiguracje i dane dotyczące zarządzanych urządzeń.

Aby uzyskać więcej informacji, zobacz [uaktualnienia do programu System Center Configuration Manager](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager).



## <a name="update"></a>Aktualizacja
*Aktualizacja* jest używany do instalowania aktualizacji w konsoli programu System Center Configuration Manager, a aktualizacje poza pasmem, które są aktualizacje, które nie może być dostarczone z poziomu konsoli programu Configuration Manager. Aktualizacje w konsoli można zmodyfikować wersji Current Branch lokacji (lub lokacji Technical Preview), aby został uruchomiony w nowszej wersji. Możesz na przykład, jeśli w lokalizacji uruchomiono wersję 1606, można zainstalować aktualizację dla wersji 1610. Aktualizacje można również zainstalować poprawki dla znany problem, bez konieczności modyfikacji wersji lokacji.      

Zazwyczaj aktualizacje Dodaj poprawki zabezpieczeń, poprawa jakości i nowe funkcje do istniejącego wdrożenia. Jeśli używasz gałęzi Technical Preview, aktualizację można zainstalować nowszej wersji Technical Preview.
-   Można wybrać podczas instalowania aktualizacji w konsoli, zaczynając od lokacji najwyższego poziomu w hierarchii.
- Można zainstalować żadnych aktualizacji, które są dostępne za pośrednictwem konsoli. Na przykład jeśli witryna będzie używana wersja 1602, zarówno 1606 i 1610 są oferowane należy rozważyć zainstalowanie wersji 1610, ponieważ każda wersja zawiera funkcje, które zostały po raz pierwszy udostępniona w wydanych wersji.
- Po zakończeniu instalacji w lokacji najwyższego poziomu nową aktualizację podrzędne Lokacje główne automatycznie uruchomić proces aktualizacji. Jednak można ustawić [usługi Windows](/sccm/core/servers/manage/install-in-console-updates#a-namebkmkservicewindowa-service-windows-for-site-servers) do kontrolowania czasu aktualizacji.
- Lokacje dodatkowe nie instalują automatycznie aktualizacji. Zamiast tego należy ręcznie uruchomić aktualizacji z poziomu konsoli programu Configuration Manager.

Aby uzyskać więcej informacji, zobacz [aktualizacji dla programu System Center Configuration Manager](/sccm/core/servers/manage/updates), i [Technical Preview programu System Center Configuration Manager](/sccm/core/get-started/technical-preview).



## <a name="install"></a>Zainstaluj
*Zainstaluj* jest używane podczas tworzenia nowej hierarchii programu Configuration Manager od początku lub dodanie dodatkowych lokacji do istniejącej hierarchii.  

Podczas instalowania nowej lokacji głównej lub centralnej lokacji administracyjnej, lokalizację setup.exe i jego pliki źródłowe powiązanych, których używasz zależy od danego scenariusza instalacji.

Aby uzyskać więcej informacji, zobacz [przygotowaniu się do zainstalowania lokacji](/sccm/core/servers/deploy/install/prepare-to-install-sites).
