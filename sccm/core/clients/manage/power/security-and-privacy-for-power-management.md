---
title: "Bezpieczeństwo i prywatność funkcji zarządzania energią | Dokumentacja firmy Microsoft"
description: "Pobierz informacje o zabezpieczeniach i prywatności dotyczące zarządzania energią w programie System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 469ff35f-59a1-484d-902b-107dd6070baf
caps.latest.revision: "5"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 51a29eec13373f92a65ac09dfb23d1b5cdd1683a
ms.sourcegitcommit: f6a428a8db7145affa388f59e0ad880bdfcf17b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2017
---
# <a name="security-and-privacy-for-power-management-in-system-center-configuration-manager"></a>Bezpieczeństwo i prywatność funkcji zarządzania energią w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Ta sekcja zawiera informacje o bezpieczeństwie i prywatności dotyczące zarządzania energią w programie System Center Configuration Manager.  

## <a name="security-best-practices-for-power-management"></a>Najlepsze rozwiązania w zakresie zabezpieczeń dla funkcji zarządzania energią  
 Funkcji zarządzania energią nie dotyczą żadne najlepsze rozwiązania w zakresie zabezpieczeń.  

## <a name="privacy-information-for-power-management"></a>Informacje o ochronie prywatności dla funkcji zarządzania energią  
 Zarządzanie energią używa funkcji wbudowanych systemu Windows do monitorowania zużycia energii i stosowania ustawień zasilania dla komputerów podczas godzin pracy i poza nimi. Programu Configuration Manager gromadzi informacje o zużyciu energii z komputerów, które obejmują dane o podczas korzystania z komputera użytkownika. Mimo że program Configuration Manager monitoruje zużycia energii dla kolekcji, a nie dla każdego komputera, Kolekcja może zawierać tylko jeden komputer. Zarządzanie energią nie jest domyślnie włączone i musi zostać skonfigurowane przez administratora.  

 Informacje o zużyciu energii są przechowywane w bazie danych programu Configuration Manager i nie są wysyłane do firmy Microsoft. Szczegółowe informacje są przechowywane w bazie danych przez 31 dni, a podsumowania przez 13 miesięcy. Nie możesz skonfigurować interwału usuwania.  

 Przed skonfigurowaniem zarządzania energią rozważ wymogi związane z ochroną prywatności.  
