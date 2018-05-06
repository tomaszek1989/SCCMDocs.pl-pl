---
title: Zdalnie zsynchronizować zasad na urządzeniach zarejestrowanych w usłudze Intune
titleSuffix: Configuration Manager
description: Dowiedz się, jak zsynchronizować zasad zarejestrowane w usłudze Intune urządzenia z konsoli programu Configuration Manager
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: b3731ad0-2a24-4042-994e-5e4c1230e3fe
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 3ecd2c480ab67a82539edff6daa18ef0f93628c6
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="remotely-synchronize-policy-on-intune-enrolled-devices-from-the-configuration-manager-console"></a>Zdalnie synchronizować zasady na zarejestrowane w usłudze Intune urządzenia z konsoli programu Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


Możesz poprosić o zasady synchronizacji urządzenie jest zarejestrowane w usłudze Intune z poziomu konsoli programu Configuration Manager, bez konieczności żądania synchronizacji z aplikacji Portal firmy na urządzeniu. 

Wykonaj następujące czynności:

1.  Wybierz urządzenie pod adresem **zasoby i zgodność** > **omówienie** > **urządzeń**.
2.  Kliknij przycisk **Wyślij żądanie synchronizacji** w **akcje urządzeń zdalnych** menu.


Po pięciu do dziesięciu minut wszelkie zmiany w zasadach będą synchronizowane z urządzeniem. Informacje o stanie żądania synchronizacji można wyświetlić w nowej kolumnie w widokach urządzenia o nazwie **stan synchronizacji zdalnej**, jak również w sekcji danych odnajdywania **właściwości** okno dialogowe dla każdego urządzenia.
