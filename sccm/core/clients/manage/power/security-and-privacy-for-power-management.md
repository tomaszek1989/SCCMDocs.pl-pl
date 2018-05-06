---
title: Bezpieczeństwo i prywatność funkcji zarządzania energią
titleSuffix: Configuration Manager
description: Pobierz informacje o zabezpieczeniach i prywatności dotyczące zarządzania energią w programie System Center Configuration Manager.
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 469ff35f-59a1-484d-902b-107dd6070baf
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 47ddbf358426b7683dab42b4f7a6a89ad8e631de
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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
