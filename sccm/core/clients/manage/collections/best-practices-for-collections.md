---
title: "Kolekcje najlepszych rozwiązań | Dokumentacja firmy Microsoft"
description: "Pobierz najlepsze rozwiązania w zakresie zbierania danych w programie System Center Configuration Manager."
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7a2abb79-9ae5-4a25-9e18-5dcf528de3bf
caps.latest.revision: 4
caps.handback.revision: 0
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: fd62af3910c0745e0f1105417701b894e10cbbac
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="best-practices-for-collections-in-system-center-configuration-manager"></a>Najlepsze praktyki dotyczące kolekcje w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Stosować następujące najlepsze rozwiązania dla kolekcji w programie System Center Configuration Manager.  

## <a name="do-not-use-incremental-updates-for-a-large-number-of-collections"></a>Nie używaj aktualizacji przyrostowych dla dużej liczby kolekcji  
 W przypadku wybrania opcji **Użyj aktualizacji przyrostowych dla tej kolekcji** ta konfiguracja może spowodować opóźnienia oceny włączonej dla wielu kolekcji. Próg wynosi około 200 kolekcji w hierarchii. Dokładna liczba zależy od następujących czynników:  

-   Łączna liczba kolekcji  

-   Częstotliwość dodawania i modyfikowania nowych zasobów w hierarchii  

-   Liczba klientów w hierarchii  

-   Złożoność reguł członkostwa w kolekcji w hierarchii  

## <a name="make-sure-that-maintenance-windows-are-large-enough-to-deploy-critical-software-updates"></a>Należy sprawdzić, czy czas trwania okien obsługi jest wystarczający, aby wdrożyć krytyczne aktualizacje oprogramowania.  
 Można skonfigurować okna obsługi kolekcji urządzeń, aby ograniczyć czas programu Configuration Manager może instalować oprogramowanie na tych urządzeniach. Jeśli wartość określona dla czasu trwania okna obsługi będzie zbyt mała, instalacja krytycznych aktualizacji oprogramowania przez klienta może nie być możliwa, co sprawi, że klient będzie narażony na atak, którego skuteczność została osłabiona przez aktualizację oprogramowania.  

