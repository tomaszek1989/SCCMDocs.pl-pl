---
title: "Spis sprzętu — Configuration Manager | Dokumentacja firmy Microsoft"
description: "Pobierz wprowadzenie do spisu sprzętu w programie System Center Configuration Manager."
ms.custom: na
ms.date: 02/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 3969952e-9d05-49c9-82a2-e7e90ccef511
caps.latest.revision: 6
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: c64f0b42bff25e8e91cf9101d6fbb538634eab15
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="introduction-to-hardware-inventory-in-system-center-configuration-manager"></a>Wprowadzenie do spisu sprzętu w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Zbieranie informacji o konfiguracji sprzętu w urządzeniach klienckich w organizacji, należy użyć spisu sprzętu w programie System Center Configuration Manager. Aby dane spisu sprzętu były zbierane, w ustawieniach klienta musi być włączone ustawienie **Włącz spis sprzętu na klientach** .  

 Po włączeniu spisu sprzętu i cykl spisu sprzętu jest uruchamiany przez klienta, klient wysyła informacje do punktu zarządzania w lokacji klienta. Punkt zarządzania przesyła następnie informacje o spisie do serwera lokacji programu Configuration Manager, który przechowuje informacje o spisie w bazie danych lokacji. Spis sprzętu jest uruchamiany na klientach zgodnie z harmonogramem określonym w ustawieniach klienta.  

 Kilka metod służy do wyświetlania danych spisu sprzętu, która gromadzi programu Configuration Manager. Należą do nich między innymi:  

-   [Tworzenie zapytań, które zwracają urządzeń, które są oparte na określonej konfiguracji sprzętu](../../../../core/servers/manage/queries-technical-reference.md).  

-   [Tworzenie kolekcji na podstawie kwerendy oparte na określonej konfiguracji sprzętu](../../../../core/clients/manage/collections/introduction-to-collections.md). Członkostwa w kolekcjach opartych na zapytaniach są automatycznie aktualizowane zgodnie z harmonogramem. Możesz użyć kolekcji w ramach kilku zadań, takich jak wdrażanie oprogramowania. .  

-   [Uruchom raporty zawierające szczegółowe informacje o konfiguracji sprzętu w organizacji](../../../../core/servers/manage/reporting.md).   

-   [Użyj Eksploratora zasobów](../../../../core/clients/manage/inventory/use-resource-explorer-to-view-hardware-inventory.md) Aby wyświetlić szczegółowe informacje o spisie sprzętu wykonywanym dla urządzeń klienckich.   

 Przy uruchamianiu spisu sprzętu na urządzeniu klienckim pierwsze dane spisu zwracane przez klienta to zawsze pełny spis. Kolejne informacje spisu to tylko informacje różnicowe spisu. Serwer lokacji przetwarza informacje różnicowe spisu w kolejności, w jakiej zostały odebrane. Jeśli brakuje informacji różnicy dla klienta, serwera lokacji odrzuca zmian dodatkowe informacje i instruuje klienta, aby uruchomić Cykl pełny spis.  

 Program Configuration Manager zapewnia ograniczoną obsługę uruchamiania komputerów. Programu Configuration Manager może wykrywać komputery uruchamiania, ale zostało wykonane tylko zwraca informacje o spisie z systemu operacyjnego, który był aktywny w czasie cyklu spisu.  

> [!NOTE]  
>  Informacje o sposobie używania spisu sprzętu z klientów z systemem Linux i UNIX, można znaleźć w temacie [spisu sprzętu dla systemów Linux i UNIX w programie System Center Configuration Manager](../../../../core/clients/manage/inventory/hardware-inventory-for-linux-and-unix.md).  

## <a name="extending-configuration-manager-hardware-inventory"></a>Rozszerzanie spisu sprzętu programu Configuration Manager  
 Oprócz spis sprzętu wbudowanych w programie Configuration Manager umożliwia także jedną z następujących metod do rozszerzania zapasów sprzętu, aby zbierać dodatkowe informacje:  

- Możesz włączyć, wyłączyć, dodawać i usuwać klasy spisu zapasów sprzętowych z konsoli programu Configuration Manager. |  
- Pliki NOIDMIF umożliwia zbieranie informacji o urządzeń klienckich, które nie mogą być spisane przez program Configuration Manager. Możesz na przykład zebrać numer zasobu urządzenia, który istnieje tylko w postaci etykiety na urządzeniu. Spis NOIDMIF jest automatycznie kojarzony z urządzeniem klienckim, z którego został zebrany.  
- Pliki IDMIF umożliwia zbieranie informacji o zasoby, które nie są skojarzone z klientem programu Configuration Manager, na przykład, projektory, photocopiers i drukarek sieciowych.  

 Aby uzyskać więcej informacji na temat przy użyciu tych metod rozszerzania zapasów sprzętu programu Configuration Manager, zobacz [Konfigurowanie spisu sprzętu w programie System Center Configuration Manager](../../../../core/clients/manage/inventory/configure-hardware-inventory.md).  

