---
title: Wprowadzenie do kwerend | Dokumentacja firmy Microsoft
description: "Tworzenia i uruchamiania kwerend do lokalizowania obiektów w hierarchii programu System Center Configuration Manager, które spełniają kryteria kwerendy."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 03d1b3a9-41db-4d3a-a70e-e05ab5dc8141
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 10b1010ccbf3889c58c55b87e70b354559243c90
ms.openlocfilehash: f84d518670c0ece3c08c890d2293335518f7f8e9
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="introduction-to-queries-in-system-center-configuration-manager"></a>Wprowadzenie do kwerend w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Można tworzyć i uruchamiać kwerendy do lokalizowania obiektów w hierarchii programu System Center Configuration Manager, spełniających podane kryteria kwerendy. Te obiekty obejmują elementy, takie jak określone typy komputerów lub grup użytkowników. Zapytania może zwracać większość typów obiektów programu Configuration Manager, w tym witryn, kolekcje, aplikacje i dane spisu.  

 Podczas tworzenia zapytania należy określić co najmniej dwa parametry: lokalizację, w której ma być wykonane wyszukiwanie, oraz wyszukiwany element. Na przykład, aby znaleźć ilość miejsca na dysku twardym, który jest dostępny na wszystkich komputerach w lokacji programu Configuration Manager, można utworzyć kwerendę w celu wyszukiwania **dysku logicznego** atrybutu klasy i **wolnego miejsca (MB)** atrybutu miejsce na dysku twardym.  

 Po utworzeniu początkowego zapytania można określić dodatkowe kryteria. Na przykład można określić, że wyniki zapytania zawierają tylko te komputery, które są przypisane do określonej lokacji. Można również zmodyfikować sposób wyświetlania wyników, aby mogły one być wyświetlane w sposób zrozumiały dla użytkownika. Można na przykład określić, że wyniki mają być sortowane według ilości wolnego miejsca na dysku twardym w porządku rosnącym lub malejącym.  

 Podczas tworzenia kwerendy jest przechowywane przez program Configuration Manager i wyświetlana w **kwerendy** w węźle **monitorowanie** obszaru roboczego. Z tej lokalizacji można utworzyć nowe zapytanie, a następnie uruchomić i zaktualizować istniejące zapytanie lub zarządzać nim.  

 Można również zaimportować kwerendy do zasadę kwerendy w kolekcji programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [tworzenie kolekcji w programie System Center Configuration Manager](../../../core/clients/manage/collections/create-collections.md).  

## <a name="see-also"></a>Zobacz też  
 [Dokumentacja techniczna zapytania dla programu System Center Configuration Manager](../../../core/servers/manage/queries-technical-reference.md)

