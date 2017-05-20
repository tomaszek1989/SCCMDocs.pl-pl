---
title: "Monitoruj klientów systemu Linux/UNIX - programu Configuration Manager | Dokumentacja firmy Microsoft"
description: "Monitoruj klientów na serwerach z systemem Linux i UNIX w programie System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-client
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d827cf91-b18f-4ee7-b538-24ba6f003ab9
caps.latest.revision: 6
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: d6478fa75c27e07e22702f3f8d5577df73ebdd48
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="how-to-monitor-clients-for-linux-and-unix-servers-in-system-center-configuration-manager"></a>Jak monitorować klientów dla serwerów z systemami Linux i UNIX w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Można wyświetlić dane z serwerów z systemem Linux i UNIX, w konsoli programu System Center Configuration Manager za pomocą tych samych metod, które służy do wyświetlania informacji z klientów z systemem Windows.  

 Można wyświetlić następujące informacje:  

-   Szczegóły stanu od klientów w pulpitach nawigacyjnych konsoli programu Configuration Manager  

-   Szczegółowe informacje o klientach w domyślnych raportów programu Configuration Manager  

-   Szczegóły spisu w Eksploratorze zasobów  

 W poniższych sekcjach opisano motyka, aby uzyskać szczegółowe informacje z Eksploratora zasobów i raportów.  

##  <a name="BKMK_UseResourceExpforLnU"></a>Użyj Eksploratora zasobów, aby wyświetlić spisu dla serwerów Linux i UNIX  

 Po klienta programu Configuration Manager przesyła spisu sprzętu do lokacji programu Configuration Manager, można użyć Eksploratora zasobów do wyświetlania tych informacji. Klient programu Configuration Manager dla systemu Linux i UNIX nie są dodawane nowe klasy lub widoki na potrzeby magazynu Eksploratora zasobów. Dane dotyczące spisu dla systemów Linux i UNIX są mapowane na istniejące klasy WMI. Używając Eksploratora zasobów, można wyświetlić szczegóły spisu serwerów z systemami Linux i UNIX w klasyfikacjach opartych na systemie Windows.  

 Na przykład można zebrać listę wszystkich natywnie zainstalowanych programów na serwerach z systemami Linux i UNIX. Przykładami natywnie zainstalowanych programów w systemie Linux mogą być pliki **.rpms** , a w systemie Solaris pliki **.pkgs** . Po magazynu został przesłany przez klienta systemu UNIX lub Linux, można wyświetlić listę wszystkich natywnie zainstalowanych programów systemu Linux lub UNIX w Eksploratorze zasobów w konsoli programu Configuration Manager.  

 Aby uzyskać informacje o sposobie używania Eksploratora zasobów, zobacz [jak używać Eksploratora zasobów do wyświetlenia spisu sprzętu w programie System Center Configuration Manager](../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md).  

##  <a name="BKMK_UseReportsforLnU"></a> Jak używać raportów do wyświetlania informacji o serwerach z systemami Linux i UNIX  
 Raporty programu Configuration Manager obejmują informacje z serwerów z systemem Linux i UNIX, wraz z informacjami z komputerów z systemem Windows. Integracja danych z systemów Linux i UNIX w raportach nie wymaga wykonania żadnych dodatkowych kroków konfiguracji.  

 Jeśli na przykład uruchamiany jest raport o nazwie Liczba wersji systemu operacyjnego, wyświetlana jest lista systemów operacyjnych i liczba klientów, na których działa każdy z tych systemów. Raport jest oparty na informacje dotyczące spisu sprzętu, który został wysłany przez różnych klientów programu Configuration Manager, które działają w różnych systemach operacyjnych.  

 Istnieje również możliwość utworzenia raportów niestandardowych, które są specyficzne dla danych serwerów z systemami Linux i UNIX. Właściwość **Podpis** klasy spisu sprzętu o nazwie **System operacyjny** jest przydatnym atrybutem umożliwiającym identyfikowanie poszczególnych systemów operacyjnych w zapytaniach raportu.  

 Informacje o raportach w programie Configuration Manager, zobacz [raportowania w programie System Center Configuration Manager](../../../core/servers/manage/reporting.md).  

