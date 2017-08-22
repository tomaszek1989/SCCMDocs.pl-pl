---
title: "Spis oprogramowania dla urządzeń przenośnych zarejestrowanych w usłudze Microsoft Intune | Dokumentacja firmy Microsoft"
description: "Spis oprogramowania dla urządzeń przenośnych zarejestrowanych w usłudze Microsoft Intune."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a0eae17a-60a8-4132-91af-0b10ad338c92
caps.latest.revision: "18"
caps.handback.revision: "0"
author: mtillman
ms.author: mtillman
manager: angrobe
ms.openlocfilehash: 2ed79d02535768de136947e4a5b63ad186d9a3cd
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="software-inventory-for-mobile-devices-enrolled-with-microsoft-intune"></a>Spis oprogramowania dla urządzeń przenośnych zarejestrowanych w usłudze Microsoft Intune

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

 Możliwość zbierania spisu aplikacji zainstalowanych na urządzeniach przenośnych. Wybór aplikacji do uwzględnienia w spisie będzie zależeć od tego, czy urządzenie należy do firmy, czy też do osoby prywatnej. Dla urządzeń osobistych spisie zostaną uwzględnione tylko aplikacje to aplikacje, które są zarządzane przez program Microsoft Intune.  

> [!NOTE]  
>  Do spisu aplikacji zainstalowanych na urządzeniach przenośnych są zbierane w ramach [spisu sprzętu](mobile-device-hardware-inventory-hybrid.md) procesu.  

 Poniżej przedstawiono aplikacje, które są uwzględniane w spisie dla urządzenia osobiste lub należące do firmy.  

|Platforma|Urządzenia osobiste|Urządzenia należące do firmy|  
|--------------|---------------------------------|--------------------------------|  
|Windows 10 (bez klienta programu Configuration Manager)|Tylko aplikacje zarządzane|Tylko aplikacje zarządzane|
|Windows 8.1 (bez klienta programu Configuration Manager)|Tylko aplikacje zarządzane|Tylko aplikacje zarządzane|  
|Windows Phone 8|Tylko aplikacje zarządzane|Tylko aplikacje zarządzane|  
|Windows RT|Tylko aplikacje zarządzane|Tylko aplikacje zarządzane|  
|iOS|Tylko aplikacje zarządzane|Wszystkie aplikacje zainstalowane na urządzeniu|  
|Android|Tylko aplikacje zarządzane|Wszystkie aplikacje zainstalowane na urządzeniu|  

Zobacz [wprowadzenie do spisu oprogramowania](../../core/clients/manage/inventory/introduction-to-software-inventory.md) i [jak skonfigurować spis oprogramowania ](../../core/clients/manage/inventory/configure-software-inventory.md) szczegółowe informacje o użyciu spisu oprogramowania do zbierania informacji o pliku na urządzeniach klienckich.
