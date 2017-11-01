---
title: "Zdalnie zsynchronizować zasad na urządzeniach zarejestrowanych w usłudze Intune"
titleSuffix: Configuration Manager
description: "Dowiedz się, jak zsynchronizować zasad zarejestrowane w usłudze Intune urządzenia z konsoli programu Configuration Manager"
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: b3731ad0-2a24-4042-994e-5e4c1230e3fe
caps.latest.revision: "18"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: a03ba69c679bcfdc54744314c7a4cb3ef8b2a7a0
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="remotely-synchronize-policy-on-intune-enrolled-devices-from-the-configuration-manager-console"></a>Zdalnie synchronizować zasady na zarejestrowane w usłudze Intune urządzenia z konsoli programu Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


Możesz poprosić o zasady synchronizacji urządzenie jest zarejestrowane w usłudze Intune z poziomu konsoli programu Configuration Manager, bez konieczności żądania synchronizacji z aplikacji Portal firmy na urządzeniu. 

Wykonaj następujące czynności:

1.  Wybierz urządzenie pod adresem **zasoby i zgodność** > **omówienie** > **urządzeń**.
2.  Kliknij przycisk **Wyślij żądanie synchronizacji** w **akcje urządzeń zdalnych** menu.


Po pięciu do dziesięciu minut wszelkie zmiany w zasadach będą synchronizowane z urządzeniem. Informacje o stanie żądania synchronizacji można wyświetlić w nowej kolumnie w widokach urządzenia o nazwie **stan synchronizacji zdalnej**, jak również w sekcji danych odnajdywania **właściwości** okno dialogowe dla każdego urządzenia.
