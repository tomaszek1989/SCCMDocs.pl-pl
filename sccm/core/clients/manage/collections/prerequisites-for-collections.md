---
title: "Wymagania wstępne dotyczące kolekcji | Dokumentacja firmy Microsoft"
description: "Pobierz wymagań wstępnych dotyczących używania kolekcji w programie System Center Configuration Manager."
ms.custom: na
ms.date: 2/22/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: a53e4cf1-518a-4210-9c16-022c4261d2fe
caps.latest.revision: "7"
caps.handback.revision: "0"
author: andredm7
ms.author: andredm
manager: angrobe
ms.openlocfilehash: 41fc3eb20a7441939eb0dc80bc121c8f3ea322b2
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="prerequisites-for-collections-in-system-center-configuration-manager"></a>Wymagania wstępne dotyczące kolekcji w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Kolekcje w programie System Center Configuration Manager zawiera tylko zależności w obrębie produktu.  

## <a name="configuration-manager-dependencies"></a>Zależności programu Configuration Manager  

|Zależność|Więcej informacji|  
|----------------|----------------------|  
|Punkt usług raportowania|Przed rozpoczęciem raportowania dotyczącego kolekcji należy skonfigurować rolę systemu lokacji punktu usług raportowania. Aby uzyskać więcej informacji, zobacz [Raportowanie w programie System Center Configuration Manager](../../../../core/servers/manage/reporting.md).|  
|W celu zarządzania kolekcjami należy przyznać określone uprawnienia zabezpieczeń|Do zarządzania ustawieniami zgodności wymagane są następujące uprawnienia zabezpieczeń:<br /><br /> -Aby utworzyć i Zarządzanie kolekcjami: **Utwórz**, **usunąć**, **zmodyfikować**, **Modyfikuj Folder**, **Przenieś obiekt**, **odczytu** i **odczytu zasobów** dla **kolekcji** obiektu.<br /><br /> — Umożliwia zarządzanie ustawieniami kolekcji: **Zmodyfikuj ustawienia kolekcji** dla **kolekcji** obiektu.<br /><br /> Uprawnienie **Modyfikuj folder** jest wymagane dla wszystkich folderów kolekcji, w tym folderu głównego.|  
