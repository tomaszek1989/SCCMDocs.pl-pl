---
title: "Spis sprzętu — programu Configuration Manager | Dokumentacja firmy Microsoft"
description: "Wprowadzenie do spisu sprzętu w programie System Center Configuration Manager."
ms.custom: na
ms.date: 02/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 3969952e-9d05-49c9-82a2-e7e90ccef511
caps.latest.revision: "6"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: c64f0b42bff25e8e91cf9101d6fbb538634eab15
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="introduction-to-hardware-inventory-in-system-center-configuration-manager"></a>Wprowadzenie do spisu sprzętu w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Użyj spisu sprzętu w programie System Center Configuration Manager do zbierania informacji o konfiguracji sprzętu urządzeń klienckich w organizacji. Aby dane spisu sprzętu były zbierane, w ustawieniach klienta musi być włączone ustawienie **Włącz spis sprzętu na klientach** .  

 Po włączeniu spisu sprzętu i uruchomieniu cyklu spisu sprzętu przez klienta, klient wysyła informacje do punktu zarządzania w lokacji klienta. Punkt zarządzania przesyła następnie informacje spisu do serwera lokacji programu Configuration Manager, który zapisuje informacje spisu w bazie danych lokacji. Spis sprzętu jest uruchamiany na klientach zgodnie z harmonogramem określonym w ustawieniach klienta.  

 Kilka metod służy do wyświetlania danych spisu sprzętu, która gromadzi programu Configuration Manager. Należą do nich między innymi:  

-   [Tworzenie zapytań zwracających urządzenia, które są oparte na określonej konfiguracji sprzętu](../../../../core/servers/manage/queries-technical-reference.md).  

-   [Utwórz kolekcje oparte na zapytaniach, oparte na określonej konfiguracji sprzętu](../../../../core/clients/manage/collections/introduction-to-collections.md). Członkostwa w kolekcjach opartych na zapytaniach są automatycznie aktualizowane zgodnie z harmonogramem. Możesz użyć kolekcji w ramach kilku zadań, takich jak wdrażanie oprogramowania. .  

-   [Uruchamianie raportów wyświetlających konkretne szczegółowe informacje o konfiguracjach sprzętu w organizacji](../../../../core/servers/manage/reporting.md).   

-   [Użycie Eksploratora zasobów](../../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md) Aby wyświetlić szczegółowe informacje o spisie sprzętu zbieranych z urządzeń klienckich.   

 Przy uruchamianiu spisu sprzętu na urządzeniu klienckim pierwsze dane spisu zwracane przez klienta to zawsze pełny spis. Kolejne informacje spisu to tylko informacje różnicowe spisu. Serwer lokacji przetwarza informacje różnicowe spisu w kolejności, w jakiej zostały odebrane. Jeśli brakuje informacji różnicowych dla klienta, serwer lokacji odrzuca informacje różnicowe dodatkowe i nakazuje klientowi uruchomienie pełnego cyklu spisu.  

 Menedżer konfiguracji zapewnia ograniczoną obsługę komputerów uruchamiania. Configuration Manager mogą odnajdować komputery uruchamiające, ale został uruchomiony zwraca informacje spisu tylko z systemu operacyjnego, który był aktywny w momencie cyklu spisu.  

> [!NOTE]  
>  Aby uzyskać informacje o sposobie używania spisu sprzętu z klientów z systemami Linux i UNIX, zobacz [spis sprzętu dla systemów Linux i UNIX w programie System Center Configuration Manager](../../../../core/clients/manage/inventory/hardware-inventory-for-linux-and-unix.md).  

## <a name="extending-configuration-manager-hardware-inventory"></a>Rozszerzanie spisu sprzętu programu Configuration Manager  
 Oprócz z wbudowanego spisu sprzętu w programie Configuration Manager można także użyć jednej z następujących metod rozszerzania spisu sprzętu do gromadzenia dodatkowych informacji:  

- Możesz włączyć, wyłączyć, dodać i usunąć klasy spisu sprzętu, spisu z konsoli programu Configuration Manager. |  
- Użyj plików NOIDMIF, aby zbierać informacje o urządzeniach klienckich, które nie może zebrać spisu przez program Configuration Manager. Możesz na przykład zebrać numer zasobu urządzenia, który istnieje tylko w postaci etykiety na urządzeniu. Spis NOIDMIF jest automatycznie kojarzony z urządzeniem klienckim, z którego został zebrany.  
- Pliki IDMIF umożliwiają zbieranie informacji o zasoby, które nie są skojarzone z klientem programu Configuration Manager, na przykład, projektorach, kopiarkach i drukarkach sieciowych.  

 Aby uzyskać więcej informacji o używaniu tych metod rozszerzania spisu sprzętu programu Configuration Manager, zobacz [jak skonfigurować spis sprzętu w programie System Center Configuration Manager](../../../../core/clients/manage/inventory/configure-hardware-inventory.md).  
