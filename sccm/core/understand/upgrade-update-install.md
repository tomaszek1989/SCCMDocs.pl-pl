---
title: O uaktualnienie, aktualizacji i zainstaluj | Dokumentacja firmy Microsoft
description: "Różnice między terminy instalacji, aktualizacji i uaktualnienia, podczas zarządzania infrastrukturą programu Configuration Manager."
ms.custom: na
ms.date: 1/11/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 17fab17f-304d-4f6a-87c7-30ab4f5521ed
caps.latest.revision: 0
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0d0735c170820259ac8bb6706aac7cc5569a1628
ms.openlocfilehash: 6bd6cd7ea3c41fa1d70e17a1290c9f1f74cc9e37
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---

# <a name="about-upgrade-update-and-install-for-site-and-hierarchy-infrastructure"></a>O uaktualnienie aktualizacji i zainstalować infrastruktury lokacji i hierarchii

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


Podczas zarządzania lokacji programu System Center Configuration Manager i infrastruktury hierarchii, warunki *uaktualnienia*, *aktualizacji*, i *zainstalować* są używane do opisywania trzy oddzielne pojęcia.

## <a name="upgrade"></a>Upgrade
*Uaktualnij* lub *uaktualnienia w miejscu*, jest używana podczas konwersji lokacji programu Configuration Manager 2012 lub hierarchii na taki, który jest uruchamiany System Center Configuration Manager.
Po uaktualnieniu programu System Center 2012 Configuration Manager programu System Center Configuration Manager, możesz nadal używać tej samej serwerów do obsługi lokacji i serwerów lokacji i zachować istniejące dane i konfiguracje programu Configuration Manager.  To różni się od [migracji](/sccm/core/migration/migrate-data-between-hierarchies) czyli sposób zachowania Twoje konfiguracje i dane dotyczące zarządzanych urządzeń podczas korzystania z nowych lokacji programu System Center Configuration Manager zainstalowane na nowy sprzęt.

Aby uzyskać więcej informacji, zobacz [uaktualnienia programu System Center Configuration Manager](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager).



## <a name="update"></a>Aktualizacja
*Aktualizacja* służy do instalowania aktualizacji w konsoli programu System Center Configuration Manager i aktualizacji poza pasmem, które są aktualizacje, które nie mogą zostać dostarczone z konsoli programu Configuration Manager. Aktualizacji w konsoli zmodyfikować wersji lokacji bieżącej gałęzi (lub witryny Technical Preview), tak aby była uruchamiana nowszej wersji. Można na przykład, jeśli witryna jest uruchamiana wersja 1606, można zainstalować aktualizację wersji 1610. Aktualizacje można również zainstalować poprawki dla znany problem, bez konieczności modyfikacji wersji witryn.      

Zazwyczaj aktualizacje Dodaj poprawki zabezpieczeń, poprawy jakości oraz nowe funkcje do istniejącego wdrożenia. Jeśli używasz gałęzi Technical Preview aktualizację można zainstalować w nowszej wersji programu Technical Preview.
-    Można wybrać termin instalacji aktualizacji w konsoli, począwszy od lokacji najwyższego poziomu w hierarchii.
- Można zainstalować dowolną aktualizację, która jest dostępna w konsoli. Na przykład, jeśli witryna jest uruchamiana wersja 1602 zarówno 1606 i 1610 są oferowane, należy rozważyć zainstalowanie wersji 1610, ponieważ każda wersja zawiera funkcje, które zostały po raz pierwszy udostępniona w wydanych wersjach.
- Po ukończeniu instalacji w lokacji najwyższego poziomu nowe aktualizacje podrzędne Lokacje główne automatycznie uruchomić proces, do aktualizacji. Jednak można ustawić [usługi Windows](/sccm/core/servers/manage/install-in-console-updates#a-namebkmkservicewindowa-service-windows-for-site-servers) kontrolować terminy aktualizacji.
- Lokacje dodatkowe nie są instalowane automatycznie aktualizacji. Zamiast tego należy ręcznie uruchomić aktualizację z w ramach konsoli programu Configuration Manager.

Aby uzyskać więcej informacji, zobacz [aktualizacji dla programu System Center Configuration Manager](/sccm/core/servers/manage/updates), i [Technical Preview dla programu System Center Configuration Manager](/sccm/core/get-started/technical-preview).



## <a name="install"></a>Zainstaluj
*Zainstaluj* jest używany w przypadku tworzenia nowej hierarchii programu Configuration Manager od początku lub dodanie dodatkowych lokacji do istniejącej hierarchii.  

Po zainstalowaniu nowej lokacji głównej lub w witrynie Administracja centralna lokalizacja setup.exe i jego pokrewne pliki źródłowe używane zależy od tego scenariusza instalacji.

Aby uzyskać więcej informacji, zobacz [przygotowanie do zainstalowania lokacji](/sccm/core/servers/deploy/install/prepare-to-install-sites).

