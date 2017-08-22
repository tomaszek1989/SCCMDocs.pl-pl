---
title: "Kolekcje najlepsze rozwiązania | Dokumentacja firmy Microsoft"
description: "Pobierz najlepsze rozwiązania dotyczące kolekcji w programie System Center Configuration Manager."
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7a2abb79-9ae5-4a25-9e18-5dcf528de3bf
caps.latest.revision: "4"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: fd62af3910c0745e0f1105417701b894e10cbbac
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="best-practices-for-collections-in-system-center-configuration-manager"></a>Najlepsze rozwiązania dotyczące kolekcji w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Użyj następujące najlepsze rozwiązania dotyczące kolekcji w programie System Center Configuration Manager.  

## <a name="do-not-use-incremental-updates-for-a-large-number-of-collections"></a>Nie używaj aktualizacji przyrostowych dla dużej liczby kolekcji  
 W przypadku wybrania opcji **Użyj aktualizacji przyrostowych dla tej kolekcji** ta konfiguracja może spowodować opóźnienia oceny włączonej dla wielu kolekcji. Próg wynosi około 200 kolekcji w hierarchii. Dokładna liczba zależy od następujących czynników:  

-   Łączna liczba kolekcji  

-   Częstotliwość dodawania i modyfikowania nowych zasobów w hierarchii  

-   Liczba klientów w hierarchii  

-   Złożoność reguł członkostwa w kolekcji w hierarchii  

## <a name="make-sure-that-maintenance-windows-are-large-enough-to-deploy-critical-software-updates"></a>Należy sprawdzić, czy czas trwania okien obsługi jest wystarczający, aby wdrożyć krytyczne aktualizacje oprogramowania.  
 Można skonfigurować okna obsługi kolekcji urządzeń ograniczyć czas programu Configuration Manager może instalować oprogramowanie na tych urządzeniach. Jeśli wartość określona dla czasu trwania okna obsługi będzie zbyt mała, instalacja krytycznych aktualizacji oprogramowania przez klienta może nie być możliwa, co sprawi, że klient będzie narażony na atak, którego skuteczność została osłabiona przez aktualizację oprogramowania.  
