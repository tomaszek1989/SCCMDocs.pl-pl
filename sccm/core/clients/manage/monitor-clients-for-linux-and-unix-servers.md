---
title: "Monitorowanie klientów systemu Linux/UNIX "
titleSuffix: Configuration Manager
description: "Monitorowanie klientów na serwerach Linux i UNIX w programie System Center Configuration Manager."
ms.custom: na
ms.date: 08/04/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d827cf91-b18f-4ee7-b538-24ba6f003ab9
caps.latest.revision: "6"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 777842307b280a4f269d68bcb993f3cec6f2e3e3
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="how-to-monitor-clients-for-linux-and-unix-servers-in-system-center-configuration-manager"></a>Jak monitorować klientów dla serwerów z systemami Linux i UNIX w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Informacje z serwerów Linux i UNIX można wyświetlić w konsoli programu System Center Configuration Manager przy użyciu tych samych metod, które służy do wyświetlania informacji z klientów z systemem Windows.  

 Można wyświetlić następujące informacje:  

-   Szczegóły stanu od klientów, w pulpity nawigacyjne z konsoli programu Configuration Manager  

-   Szczegółowe informacje o klientach w domyślnych raportach programu Configuration Manager  

-   Szczegóły spisu w Eksploratorze zasobów  

 W poniższych sekcjach opisano, jak uzyskać te informacje z Eksploratora zasobów i raportów.  

##  <a name="BKMK_UseResourceExpforLnU"></a>Użycie Eksploratora zasobów do wyświetlania spisu serwerów Linux i UNIX  

 Po klienta programu Configuration Manager przesyła spisu sprzętu do lokacji programu Configuration Manager, można użyć Eksploratora zasobów, aby wyświetlić te informacje. Klient programu Configuration Manager dla systemów Linux i UNIX nie dodaje żadnych nowych klas ani widoków spisu do Eksploratora zasobów. Dane dotyczące spisu dla systemów Linux i UNIX są mapowane na istniejące klasy WMI. Używając Eksploratora zasobów, można wyświetlić szczegóły spisu serwerów z systemami Linux i UNIX w klasyfikacjach opartych na systemie Windows.  

 Na przykład można zebrać listę wszystkich natywnie zainstalowanych programów na serwerach z systemami Linux i UNIX. Przykładami natywnie zainstalowanych programów w systemie Linux mogą być pliki **.rpms** , a w systemie Solaris pliki **.pkgs** . Po przesłaniu spisu przez klienta systemu Linux lub UNIX, można wyświetlić listę wszystkich natywnie zainstalowanych programów systemu Linux lub UNIX w Eksploratorze zasobów w konsoli programu Configuration Manager.  

 Aby uzyskać informacje o sposobie używania Eksploratora zasobów, zobacz [jak używać Eksploratora zasobów do wyświetlania spisu sprzętu w programie System Center Configuration Manager](../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md).  

##  <a name="BKMK_UseReportsforLnU"></a> Jak używać raportów do wyświetlania informacji o serwerach z systemami Linux i UNIX  
 Raporty programu Configuration Manager obejmują informacje z serwerów Linux i UNIX, wraz z informacjami z komputerów z systemem Windows. Integracja danych z systemów Linux i UNIX w raportach nie wymaga wykonania żadnych dodatkowych kroków konfiguracji.  

 Jeśli na przykład uruchamiany jest raport o nazwie Liczba wersji systemu operacyjnego, wyświetlana jest lista systemów operacyjnych i liczba klientów, na których działa każdy z tych systemów. Raport jest oparty na informacji o spisie sprzętu, który został wysłany przez różnych klientów programu Configuration Manager, które są uruchamiane w różnych systemach operacyjnych.  

 Istnieje również możliwość utworzenia raportów niestandardowych, które są specyficzne dla danych serwerów z systemami Linux i UNIX. Właściwość **Podpis** klasy spisu sprzętu o nazwie **System operacyjny** jest przydatnym atrybutem umożliwiającym identyfikowanie poszczególnych systemów operacyjnych w zapytaniach raportu.  

 Aby uzyskać informacje o raportach w programie Configuration Manager, zobacz [raportowania w programie System Center Configuration Manager](../../../core/servers/manage/reporting.md).  
