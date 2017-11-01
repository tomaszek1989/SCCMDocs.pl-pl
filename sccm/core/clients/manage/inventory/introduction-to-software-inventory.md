---
title: Zapasy oprogramowania
titleSuffix: Configuration Manager
description: Wprowadzenie do spisu oprogramowania w programie System Center Configuration Manager.
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 79eb49da-cd2b-4ffc-b355-b595aeba3aea
caps.latest.revision: "5"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: f3928e1f90b45c3dcf0d3b5202ae1a84bbe408fb
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="introduction-to-software-inventory-in-system-center-configuration-manager"></a>Wprowadzenie do spisu oprogramowania w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Spis oprogramowania umożliwia zebranie informacji o plikach na urządzeniach klienckich. Zapasy oprogramowania można zbierać pliki z urządzeń klienckich i przechowywać je na serwerze lokacji. Spis oprogramowania są zbierane w przypadku **Włącz spis oprogramowania na klientach** ustawienie w ustawieniach klienta, gdzie można również zaplanować operację.  

Po włączeniu spisu oprogramowania i klientów, uruchom cykl spisu oprogramowania, klient wysyła informacje do punktu zarządzania w lokacji klienta. Punkt zarządzania przesyła następnie informacje spisu do serwera lokacji programu Configuration Manager, który zapisuje informacje w bazie danych lokacji.   

 Poniżej przedstawiono sposoby wyświetlania danych spisu oprogramowania:  

-   [Tworzenie zapytań](../../../../core/servers/manage/queries-technical-reference.md) które zwracają urządzenia z określonych plików.   

-   Utwórz [kolekcje oparte na zapytaniach](../../../../core/clients/manage/collections/introduction-to-collections.md) zawierające urządzenia z określonych plików.   

-   [Uruchamianie raportów](../../../../core/servers/manage/reporting.md) które zapewniają szczegółowe informacje o plikach na urządzeniach.

-   Użyj [Eksploratora zasobów](../../../../core/clients/manage/inventory/use-resource-explorer-to-view-software-inventory.md) do analizowania szczegółowych informacji o plikach uwzględnionych w spisie i zebranych z urządzeń klienckich.   

 Po uruchomieniu spisu oprogramowania na urządzeniu klienckim pierwszy raport jest pełny spis. Kolejne raporty zawierają tylko informacje różnicowe spisu. Serwer lokacji przetwarza informacje różnicowe w kolejności odebrane. Jeśli brakuje informacji różnicowych dla klienta, serwer lokacji odrzuca dodatkowe informacje różnicowe i nakazuje klientowi uruchomienie pełnego spisu inwentarza.  

 Menedżer konfiguracji mogą odnajdować komputery uruchamiające, ale zwraca informacje spisu tylko z systemu operacyjnego, który był aktywny w momencie uruchomienia spisu.  

**Urządzenia przenośne:** Zobacz [spisu oprogramowania dla urządzeń przenośnych zarejestrowanych w usłudze Microsoft Intune](../../../../mdm/deploy-use/software-inventory-mobile-devices.md) informacje o zbieraniu spisu aplikacji zainstalowanych na urządzeniach przenośnych.
