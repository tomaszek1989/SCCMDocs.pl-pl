---
title: Wymagania wstępne dotyczące kolekcji
titleSuffix: Configuration Manager
description: Pobierz wymagań wstępnych dotyczących używania kolekcji w programie System Center Configuration Manager.
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: a53e4cf1-518a-4210-9c16-022c4261d2fe
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 12cbffb63ce449afedb9159174409fb5b1f7583f
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="prerequisites-for-collections-in-system-center-configuration-manager"></a>Wymagania wstępne dotyczące kolekcji w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Kolekcje w programie System Center Configuration Manager zawiera tylko zależności w obrębie produktu.  

## <a name="configuration-manager-dependencies"></a>Zależności programu Configuration Manager  

|Zależność|Więcej informacji|  
|----------------|----------------------|  
|Punkt usług raportowania|Przed rozpoczęciem raportowania dotyczącego kolekcji należy skonfigurować rolę systemu lokacji punktu usług raportowania. Aby uzyskać więcej informacji, zobacz [Raportowanie w programie System Center Configuration Manager](../../../../core/servers/manage/reporting.md).|  
|W celu zarządzania kolekcjami należy przyznać określone uprawnienia zabezpieczeń|Do zarządzania ustawieniami zgodności wymagane są następujące uprawnienia zabezpieczeń:<br /><br /> -Aby utworzyć i Zarządzanie kolekcjami: **Utwórz**, **usunąć**, **zmodyfikować**, **Modyfikuj Folder**, **Przenieś obiekt**, **odczytu** i **Odczytu zasobów** dla **kolekcji** obiektu.<br /><br /> — Umożliwia zarządzanie ustawieniami kolekcji: **Zmodyfikuj ustawienia kolekcji** dla **kolekcji** obiektu.<br /><br /> Uprawnienie **Modyfikuj folder** jest wymagane dla wszystkich folderów kolekcji, w tym folderu głównego.|  
