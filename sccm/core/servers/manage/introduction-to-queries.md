---
title: "Wprowadzenie do zapytań | Dokumentacja firmy Microsoft"
description: "Tworzenie i uruchamianie zapytań do lokalizowania obiektów w hierarchii programu System Center Configuration Manager, które spełniają kryteria zapytania."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 03d1b3a9-41db-4d3a-a70e-e05ab5dc8141
caps.latest.revision: "5"
caps.handback.revision: "0"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: f84d518670c0ece3c08c890d2293335518f7f8e9
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="introduction-to-queries-in-system-center-configuration-manager"></a>Wprowadzenie do zapytań w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Możesz tworzyć i uruchamiać zapytania do lokalizowania obiektów w hierarchii programu System Center Configuration Manager, które spełniają kryteria zapytania. Te obiekty obejmują elementy, takie jak określone typy komputerów lub grup użytkowników. Zapytania mogą zwracać większość typów obiektów programu Configuration Manager, w tym lokacje, kolekcje, aplikacje i dane spisu.  

 Podczas tworzenia zapytania należy określić co najmniej dwa parametry: lokalizację, w której ma być wykonane wyszukiwanie, oraz wyszukiwany element. Na przykład, aby znaleźć ilość miejsca na dysku twardym, który jest dostępny na wszystkich komputerach w lokacji programu Configuration Manager, można utworzyć zapytanie w celu wyszukania **dysku logicznego** klasy atrybutu i **wolne miejsce (MB)** atrybutu miejsce na dysku twardym.  

 Po utworzeniu początkowego zapytania można określić dodatkowe kryteria. Na przykład można określić, że wyniki zapytania zawierają tylko te komputery, które są przypisane do określonej lokacji. Można również zmodyfikować sposób wyświetlania wyników, aby mogły one być wyświetlane w sposób zrozumiały dla użytkownika. Można na przykład określić, że wyniki mają być sortowane według ilości wolnego miejsca na dysku twardym w porządku rosnącym lub malejącym.  

 Podczas tworzenia zapytania jest przechowywany przez program Configuration Manager i wyświetlane w **zapytania** w węźle **monitorowanie** obszaru roboczego. Z tej lokalizacji można utworzyć nowe zapytanie, a następnie uruchomić i zaktualizować istniejące zapytanie lub zarządzać nim.  

 Można również zaimportować zapytanie do reguły zapytania w kolekcji programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [jak tworzyć kolekcje w programie System Center Configuration Manager](../../../core/clients/manage/collections/create-collections.md).  

## <a name="see-also"></a>Zobacz też  
 [Informacje techniczne dotyczące zapytań programu System Center Configuration Manager](../../../core/servers/manage/queries-technical-reference.md)
