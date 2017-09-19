---
title: "Wprowadzenie do zarządzania energią | Dokumentacja firmy Microsoft"
description: "Wprowadzenie do zarządzania energią w programie System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3ddff2a7-99eb-4ef8-b969-f3f7f24053db
caps.latest.revision: "4"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: d7baabf1b223498f17f60de344e1c1d30f5a8120
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2017
---
# <a name="introduction-to-power-management-in-system-center-configuration-manager"></a>Wprowadzenie do zarządzania energią w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Zarządzania energią w programie System Center Configuration Manager eliminuje konieczność mające wiele organizacji do monitorowania i zmniejszyć zużycie energii swoje komputery. Funkcja korzysta z funkcji zarządzania energią wbudowanych w system Windows, co umożliwia stosowanie odpowiednich i spójnych ustawień dla komputerów w organizacji. Na komputerach możesz zastosować różne ustawienia zasilania dla godzin pracy i czasu poza godzinami pracy. Na przykład możesz zastosować bardziej restrykcyjny plan zasilania dla komputerów poza godzinami pracy. W przypadkach, w których komputery muszą być zawsze włączone, możesz zapobiec zastosowaniu ustawień zarządzania energią.  

 Zarządzanie energią w programie Configuration Manager udostępnia kilka raportów, które ułatwiają analizowanie zasilania zużycia i ustawień zasilania komputerów w organizacji. Możesz także użyć raportów do rozwiązywania problemów z zarządzaniem energią.  

 Aby uzyskać szczegółowy przepływ pracy o sposobie konfigurowania i korzystania z funkcji zarządzania energią, zobacz [Lista kontrolna administratora dotycząca zarządzania energią w programie System Center Configuration Manager](../../../../core/clients/manage/power/administrator-checklist-for-power-management.md).  

> [!IMPORTANT]  
>  Zarządzanie energią w programie Configuration Manager nie jest obsługiwana na maszynach wirtualnych. Nie możesz zastosować planów zasilania dla maszyn wirtualnych ani raportować z nich danych zasilania.  

## <a name="the-power-management-workflow"></a>Przepływ pracy zarządzania energią  
 Użyj następującego polecenia trzy etapy planowania i implementacji zarządzania energią w programie Configuration Manager.  

### <a name="monitoring-and-planning-phase"></a>Faza monitorowania i planowania  
 Zarządzanie energią używa spisu sprzętu programu Configuration Manager do zbierania danych dotyczących użycia i zasilania ustawienia komputera dla komputerów w lokacji. Istnieje kilka raportów, które umożliwiają przeanalizowanie tych danych i określenie optymalnych ustawień zarządzania energią dla komputerów. Na przykład w fazie monitorowania i planowania przepływu pracy zarządzania energią możesz utworzyć kolekcje oparte na danych w raporcie **Możliwości zasilania** i użyć tych danych do określenia komputerów, które nie obsługują zarządzania energią. Następnie możesz wykluczyć te komputery z zarządzania energią.  

> [!IMPORTANT]  
>  Nie należy stosować planów zasilania na komputerach w lokacji przed zebraniem i przeanalizowaniem danych dotyczących zasilania z komputerów klienckich. Zastosowanie nowych ustawień zarządzania energią na komputerach przed sprawdzeniem istniejących ustawień może spowodować wzrost zużycia energii.  

### <a name="enforcement-phase"></a>Faza wymuszania  
 Zarządzanie energią umożliwia utworzenie planów zasilania, które możesz zastosować dla kolekcji komputerów w lokacji. Te plany zasilania konfigurują ustawienia zarządzania energią systemu Windows na komputerach. Można użyć planów zasilania, które są uwzględniane w programie Configuration Manager lub skonfigurować własne niestandardowe plany zasilania. Możesz użyć danych zasilania zebranych w fazie monitorowania i planowania jako linii bazowej, aby łatwiej ocenić oszczędność energii po zastosowaniu planu zasilania na komputerach. Aby uzyskać więcej informacji, zobacz [Lista kontrolna administratora dotycząca zarządzania energią w programie System Center Configuration Manager](../../../../core/clients/manage/power/administrator-checklist-for-power-management.md).  

### <a name="compliance-phase"></a>Faza sprawdzania zgodności  
 W fazie sprawdzania zgodności możesz uruchomić raporty, które ułatwiają ocenę użycia energii i oszczędności związanych z wydatkami na energię w organizacji. Można także uruchomić raporty, które opisują redukcję ilości CO2 generowany przez komputery. Są także dostępne raporty, które ułatwiają zweryfikowanie, czy ustawienia zasilania zostały zastosowane poprawnie na komputerach, a także ułatwiają rozwiązywanie problemów z funkcją zarządzania energią.  
