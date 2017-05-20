---
title: Ocena programu Configuration Manager | Dokumentacja firmy Microsoft
description: "Tworzenie środowiska laboratoryjnego do oceny programu System Center Configuration Manager do użycia w organizacji."
ms.custom: na
ms.date: 2/28/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 01b30260-f03a-4851-a549-d1b76e8cfc69
caps.latest.revision: 25
caps.handback.revision: 0
author: brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0ea90d3f3bef80b8acf9018a1338ae05fc948af4
ms.openlocfilehash: d7ea785ab1beee09b9adda735a87f89bc9481620
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="evaluate-system-center-configuration-manager-by-building-your-own-lab-environment"></a>Tworzenie własnego środowiska laboratoryjnego w celu oceny programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

 Informacje o tworzeniu środowiska laboratoryjnego do oceny programu System Center Configuration Manager w organizacji.  

 System Center Configuration Manager jest złożona i zaawansowane narzędzia do zarządzania użytkownikami, urządzeń i oprogramowania. Dzięki czemu można Wyjdź za pojęć związanych z ćwiczeniami tematyczne jest dobrym pomysłem jest dokładnie ocenić przed pełnym wdrożeniem programu System Center Configuration Manager.  

 Ten przewodnik jest przeznaczona głównie dla administratorów, którzy ocenia użycie programu Configuration Manager w środowisku firmowym:  

-   Administratorzy, którzy rozwiązania, aby w pełni zarządzać komputerami, serwerów i urządzeń przenośnych  

-   Administratorzy w branży wysokim poziomie zabezpieczeń, które wymagają zabezpieczeń lokalnych zarządzanie urządzeniami elastyczność zarządzania urządzeniami oparte na chmurze  

-   Administratorzy, którzy chcą zarządzać skalowanie w górę ich Architektura serwera lokalnego  

## <a name="what-this-lab-does"></a>Zadania w tym laboratorium  
 Tworzenie środowiska laboratoryjnego głównym celem jest daje ogólnej wiedzy, aby rozpocząć pracę z programem Configuration Manager i pomóc lepiej zrozumieć programu Configuration Manager. Możesz kroki omówimy przyspieszonego zestawu bieżącej wersji programu Configuration Manager za pomocą dwóch serwerów:  

-   Taki, który obsługuje usługi Active Directory, kontroler domeny i serwer DNS  

-   Taki, który obsługuje program Configuration Manager i wszystkie skojarzone składniki programu SQL Server  

Komputery klienckie są instalowane w ramach funkcji Hyper-V. Laboratorium można również uruchomić jako w pełni zwirtualizowany system na pojedynczym serwerze.  

## <a name="what-this-lab-does-not-do"></a>Zadania, które nie są wykonywane podczas tego laboratorium  
 To laboratorium nie wykonasz wszystkie scenariusze programu Configuration Manager. Nie służy do migracji bezpośrednio w środowisku active.  

 Wynikiem utworzenia tego laboratorium będzie funkcjonalne środowisko pracy. Ale tego środowiska nie będzie zoptymalizowane do czynników, takich jak wydajność systemu, zarządzania miejsca na dysku twardym i magazynu programu SQL Server.  

##  <a name="BKMK_EvalRec"></a>Zalecane odczytywanie przed utworzeniem laboratorium  
 Mnóstwo zawartość jest dostępna w [dokumentacji programu System Center Configuration Manager](http://docs.microsoft.com/sccm/). Firma Microsoft zaleca, przeczytaj następujące tematy z tej biblioteki przed przystąpieniem do tworzenia laboratorium:  

-   Dowiedz się więcej podstawowe pojęcia dotyczące konsoli programu Configuration Manager, portale przez użytkownika końcowego i przykładowe scenariusze, w [wprowadzenie programu System Center Configuration Manager](../../core/understand/introduction.md).  

-   Dowiedz się więcej o najważniejszych funkcjach zarządzania programu Configuration Manager w [funkcji i możliwości programu System Center Configuration Manager](../../core/plan-design/changes/features-and-capabilities.md).  

-   Rozwijaj swoją wiedzę z [podstawy programu System Center Configuration Manager](../../core/understand/fundamentals.md).  

-   Dowiedz się więcej o ważności ról zabezpieczeń w [podstawy administracji opartej na rolach dla programu System Center Configuration Manager](../../core/understand/fundamentals-of-role-based-administration.md).  

-   Więcej informacji na temat zarządzania zawartością w programie [pojęcia związane z zarządzaniem zawartością](../../core/plan-design/hierarchy/fundamental-concepts-for-content-management.md).  

-   Dowiedz się, jak pomyślnie obsługuje codziennych zadań w całym wdrożeniu w [zrozumieć, jak klienci znaleźć zasoby witryny i usługi dla programu System Center Configuration Manager](../../core/plan-design/hierarchy/understand-how-clients-find-site-resources-and-services.md).  

