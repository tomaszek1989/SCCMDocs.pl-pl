---
title: "Bezpieczeństwo i prywatność zarządzania energią | Dokumentacja firmy Microsoft"
description: "Uzyskaj informacje o zabezpieczeniach i prywatności zarządzania energią w programie System Center Configuration Manager."
ms.custom: na
ms.date: 04/23/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 469ff35f-59a1-484d-902b-107dd6070baf
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 690d03d9c8c49a815bd318df549d7401a855bc5d
ms.openlocfilehash: 94d5418c364c318dba92dc9f9066f54d1130aa34
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="security-and-privacy-for-power-management-in-system-center-configuration-manager"></a>Bezpieczeństwo i prywatność zarządzania zużyciem energii w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Ta sekcja zawiera informacje o zabezpieczeniach i prywatności dla zarządzania zużyciem energii w programie System Center Configuration Manager.  

## <a name="security-best-practices-for-power-management"></a>Najlepsze rozwiązania w zakresie zabezpieczeń dla funkcji zarządzania energią  
 Funkcji zarządzania energią nie dotyczą żadne najlepsze rozwiązania w zakresie zabezpieczeń.  

## <a name="privacy-information-for-power-management"></a>Informacje o ochronie prywatności dla funkcji zarządzania energią  
 Zarządzanie energią używa funkcji wbudowanych systemu Windows do monitorowania zużycia energii i stosowania ustawień zasilania dla komputerów podczas godzin pracy i poza nimi. Configuration Manager zbiera informacje o wykorzystaniu energii z komputerów, zawierającego dane dotyczące gdy użytkownik korzysta z komputera. Mimo że program Configuration Manager monitoruje zużycie energii dla kolekcji, a nie dla każdego komputera, Kolekcja może zawierać tylko jeden komputer. Zarządzanie energią nie jest domyślnie włączone i musi zostać skonfigurowane przez administratora.  

 Informacje o użyciu zasilania są przechowywane w bazie danych programu Configuration Manager i nie są wysyłane do firmy Microsoft. Szczegółowe informacje są przechowywane w bazie danych przez 31 dni, a podsumowania przez 13 miesięcy. Nie możesz skonfigurować interwału usuwania.  

 Przed skonfigurowaniem zarządzania energią rozważ wymogi związane z ochroną prywatności.  

