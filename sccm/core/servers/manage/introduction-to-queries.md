---
title: Wprowadzenie do zapytań
titleSuffix: Configuration Manager
description: Tworzenie i uruchamianie zapytań do lokalizowania obiektów w hierarchii programu System Center Configuration Manager, które spełniają kryteria zapytania.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 03d1b3a9-41db-4d3a-a70e-e05ab5dc8141
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: ebc5c1b7f7efb1ba9c3f1fc7b36f82b6be59858f
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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
