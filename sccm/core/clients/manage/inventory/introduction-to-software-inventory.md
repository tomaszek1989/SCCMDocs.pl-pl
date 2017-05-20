---
title: Spis oprogramowania | Dokumentacja firmy Microsoft
description: Pobierz wprowadzenie do spisu oprogramowania System Center Configuration Manager.
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 79eb49da-cd2b-4ffc-b355-b595aeba3aea
caps.latest.revision: 5
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f9097014c7e988ec8e139e518355c4efb19172b3
ms.openlocfilehash: 969f2d28649853ddc95860fe72597d6d2c9a94e9
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="introduction-to-software-inventory-in-system-center-configuration-manager"></a>Wprowadzenie do spisu oprogramowania System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Spis oprogramowania umożliwia zebranie informacji o plikach na urządzeniach klienckich. Zapasy oprogramowania można zbierać pliki z urządzeń klienckich i przechowywać je na serwerze lokacji. Są zbierane dane spisu oprogramowania w przypadku **Włącz spis oprogramowania na klientach** ustawienie w ustawieniach klienta, gdzie można także zaplanować operację.  

Po włączeniu spisu oprogramowania i klientów uruchomić cykl spisu oprogramowania, klient wysyła informacje do punktu zarządzania w lokacji klienta. Punkt zarządzania przesyła następnie informacje o spisie do serwera lokacji programu Configuration Manager, który przechowuje informacje w bazie danych lokacji.   

 Poniżej przedstawiono sposoby wyświetlania danych spisu oprogramowania:  

-   [Tworzenie zapytań](../../../../core/servers/manage/queries-technical-reference.md) zwracanych urządzeń z określonych plików.   

-   Tworzenie [kolekcje oparte na zapytaniach](../../../../core/clients/manage/collections/introduction-to-collections.md) zawierające urządzenia z określonych plików.   

-   [Uruchamianie raportów](../../../../core/servers/manage/reporting.md) zawierających szczegółowe informacje o plikach na urządzeniach.

-   Użyj [Eksploratora zasobów](../../../../core/clients/manage/inventory/use-resource-explorer-to-view-software-inventory.md) zbadać szczegółowe informacje na temat plików, które zostały spisanych i zbieranych z urządzeń klientów.   

 Po uruchomieniu spisu oprogramowania na urządzeniu klienckim pierwszy raport jest pełny spis. Kolejne raporty zawierają tylko informacje spisu zmian. Serwer lokacji przetwarza informacje zmian w kolejności odebrane. Jeśli brakuje informacji różnicowych dotyczących klienta, serwer lokacji odrzuci dalszych informacji różnicowych i instruuje klienta, aby uruchomić pełny spis.  

 Configuration Manager może wykrywać komputery uruchamiania, ale tylko zwraca informacje o spisie z systemu operacyjnego, który był aktywny w momencie spisu.  

**Urządzenia przenośne:** Zobacz [spisu oprogramowania na urządzenia przenośne zarejestrowane w usłudze Microsoft Intune](../../../../mdm/deploy-use/software-inventory-mobile-devices.md) informacje o zbieraniu spis aplikacje zainstalowane na urządzeniach przenośnych.

