---
title: Ocena programu Configuration Manager | Dokumentacja firmy Microsoft
description: "Tworzenie środowiska laboratoryjnego do oceny programu System Center Configuration Manager do użytku w Twojej organizacji."
ms.custom: na
ms.date: 2/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 01b30260-f03a-4851-a549-d1b76e8cfc69
caps.latest.revision: "25"
caps.handback.revision: "0"
author: brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: d7ea785ab1beee09b9adda735a87f89bc9481620
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="evaluate-system-center-configuration-manager-by-building-your-own-lab-environment"></a>Tworzenie własnego środowiska laboratoryjnego w celu oceny programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

 Informacje o tworzeniu środowiska laboratoryjnego do oceny programu System Center Configuration Manager w organizacji.  

 System Center Configuration Manager jest złożone i zaawansowane narzędzie do zarządzania użytkownikami, urządzeniami i oprogramowania. Jest dobrym pomysłem jest dokładnie oceń System Center Configuration Manager przed pełnym wdrożeniem, dzięki czemu można zrozumieć odpowiednie koncepcje Ćwiczenia praktyczne.  

 Ten przewodnik jest przeznaczony głównie dla administratorów, którzy są oceniają zastosowanie programu Configuration Manager w środowisku firmowym:  

-   Administratorzy, którzy rozwiązania, aby w pełni zarządzać komputerami, serwerami i urządzeniami przenośnymi  

-   Administratorzy w branżach wysokim poziomie zabezpieczeń, które wymagają bezpieczeństwa lokalnego zarządzania urządzeniami elastyczność zarządzania urządzeniami w chmurze  

-   Administratorzy, którzy chcą zarządzać skalowaniem ich Architektura serwera lokalnego  

## <a name="what-this-lab-does"></a>Zadania w tym laboratorium  
 Głównym celem tworzenia tego środowiska laboratorium jest zapewnienie ogólnej wiedzy, aby rozpocząć pracę z programem Configuration Manager, a także lepsze zrozumienie działania programu Configuration Manager. Będzie przeprowadzenie przyspieszonego zestawu bieżącej wersji programu Configuration Manager przy użyciu dwóch serwerów:  

-   Jeden, który jest hostem usługi Active Directory, kontroler domeny i serwer DNS  

-   Jeden, który jest hostem programu Configuration Manager i wszystkie skojarzone składniki programu SQL Server  

Komputery klienckie są instalowane w ramach funkcji Hyper-V. Laboratorium można również uruchomić jako w pełni zwirtualizowany system na pojedynczym serwerze.  

## <a name="what-this-lab-does-not-do"></a>Zadania, które nie są wykonywane podczas tego laboratorium  
 W tym laboratorium użytkownik nie zostanie przeprowadzony przez wszystkie scenariusze programu Configuration Manager. Nie jest przeznaczony do natychmiastowej migracji do aktywnego środowiska.  

 Wynikiem utworzenia tego laboratorium będzie funkcjonalne środowisko pracy. Jednak tego środowiska nie będzie zoptymalizowane pod kątem czynniki, takie jak wydajność systemu, zarządzania miejscem na dysku twardym i magazyn programu SQL Server.  

##  <a name="BKMK_EvalRec"></a>Zalecane materiały do przeczytania przed utworzeniem laboratorium  
 Wiele materiałów jest dostępnych w [dokumentacji programu System Center Configuration Manager](http://docs.microsoft.com/sccm/). Firma Microsoft zaleca, przeczytaj następujące tematy z tej biblioteki, przed przystąpieniem do tworzenia laboratorium należy utworzyć:  

-   Podstawowe pojęcia dotyczące konsoli programu Configuration Manager, portale użytkownika końcowego i przykładowe scenariusze w [wprowadzenie do programu System Center Configuration Manager](../../core/understand/introduction.md).  

-   Dowiedz się więcej o najważniejszych funkcjach zarządzania programu Configuration Manager w [funkcje i możliwości programu System Center Configuration Manager](../../core/plan-design/changes/features-and-capabilities.md).  

-   Niemal swoją wiedzę o [podstawowe informacje na temat programu System Center Configuration Manager](../../core/understand/fundamentals.md).  

-   Informacje dotyczące znaczenia ról zabezpieczeń w [podstawowe informacje dotyczące administrowania opartego na rolach dla programu System Center Configuration Manager](../../core/understand/fundamentals-of-role-based-administration.md).  

-   Więcej informacji na temat zarządzania zawartością w programie [pojęcia związane z zarządzaniem zawartością](../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md).  

-   Dowiedz się, jak skutecznie obsługiwać codzienne zadania podczas wdrażania w [zrozumieć, jak klienci znajdują zasoby i usługi programu System Center Configuration Manager lokacji](../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md).  
