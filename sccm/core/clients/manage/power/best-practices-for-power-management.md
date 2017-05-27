---
title: "Najlepsze praktyki zarządzania energią | Dokumentacja firmy Microsoft"
description: "Pobierz najlepsze rozwiązania w zakresie zarządzania energią w programie System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 9f7142e1-c972-4384-853b-2da1568cb3e3
caps.latest.revision: 5
caps.handback.revision: 0
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: fc392e4440e84614f92218e9c7a09ec1c2c64f53
ms.openlocfilehash: d3cc24c7923141f039dcda26ac27489cb0143e89
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="best-practices-for-power-management-in-system-center-configuration-manager"></a>Najlepsze rozwiązania w zakresie zarządzania zużyciem energii w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Użyj następujących najlepszych rozwiązań zarządzania energią w programie System Center Configuration Manager.  

## <a name="perform-the-monitoring-phase-at-a-representative-time"></a>Przeprowadzanie fazy monitorowania w czasie reprezentatywnym  
 Faza monitorowania zarządzania energią umożliwia uzyskiwanie informacji o zużyciu energii, działaniach, możliwościach zarządzania energią i wpływie komputerów w organizacji na środowisko. Upewnij się, że wybierasz reprezentatywny czas do przeprowadzenia fazy monitorowania. Na przykład przeprowadzenie fazy monitorowania w dniu wolnym nie spowoduje utworzenia realistycznego raportu zużycia energii komputera.  

## <a name="create-a-control-collection-of-computers-with-no-power-plans-applied"></a>Tworzenie kolekcji kontrolnej komputerów bez zastosowanych planów zasilania  
 Utwórz dwie kolekcje komputerów, aby ułatwić monitorowanie efektów zastosowania planów zasilania na komputerach. Pierwsza kolekcja powinna zawierać większość komputerów, do których chcesz zastosować ustawienia zasilania, a druga (kolekcja kontrolna) — pozostałe komputery. Zastosuj wymagany plan zarządzania energią do kolekcji zawierającej większość komputerów. Następnie możesz uruchomić raporty w celu porównania kosztów energii, zużycia energii i wpływu na środowisko komputerów, do których zostały zastosowane ustawienia zasilania, z kolekcją kontrolną, w której ustawienia energii nie zostały zastosowane.  

## <a name="run-the-power-settings-report-before-you-apply-a-power-management-plan"></a>Uruchom raport ustawień zasilania przed zastosowaniem planu zarządzania energią  
 Przed zainstalowaniem planu zarządzania energią do kolekcji komputerów uruchom raport **Ustawienia zasilania** , aby lepiej zrozumieć ustawienia zarządzania energią, które zostały już skonfigurowane na komputerach w kolekcji. Zastosowanie nowych ustawień zarządzania energią na komputerach przed sprawdzeniem ustawień już istniejących może spowodować wzrost zużycia energii.  

## <a name="exclude-servers-from-power-management"></a>Wyklucz serwery z zarządzania zasilaniem  
 Zarządzanie energią dla komputerów z systemem Windows Server nie jest obsługiwane (chociaż dane użycia są zbierane). Upewnij się, że serwery zostały dodane do kolekcji, a kolekcja wykluczona z zarządzania energią.  

## <a name="exclude-computers-that-you-do-not-want-to-manage"></a>Wyklucz komputery, którymi nie chcesz zarządzać  
 Jeśli masz komputery, którymi nie chcesz zarządzać za pomocą zarządzania energią, dodaj je do kolekcji i upewnij się, że kolekcja została wykluczona z zarządzania energią.  

 Przykłady komputerów, które można wykluczyć z zarządzania energią:  

-   Komputery, które muszą pozostać włączone.  

-   Komputery, z którymi użytkownicy muszą łączyć się przy użyciu połączenia pulpitu zdalnego.  

-   Komputery, na których nie można używać zarządzania energią.  

-   Komputery z rolą systemu lokacji punktu dystrybucji.  

-   Komputery publiczne, takie jak kioski w miejscu publicznym, monitory informacyjne oraz konsole monitorowania, w przypadku których komputer i monitor muszą być zawsze włączone.  

 Aby uzyskać więcej informacji, zobacz [Konfigurowanie zarządzania zużyciem energii w programie System Center Configuration Manager](../../../../core/clients/manage/power/configuring-power-management.md).  

## <a name="first-apply-power-plans-to-a-test-collection-of-computers"></a>Najpierw zastosuj plany zasilania do testowej kolekcji komputerów  
 Należy zawsze przetestować efekty zastosowania planu zarządzania energią w testowej kolekcji komputerów przed zastosowaniem planu zasilania w większej kolekcji komputerów.  

 Ustawienia zasilania zastosowane na komputerach z systemem Windows XP lub Windows Server 2003 nie są przywracane do oryginalnych wartości, nawet jeśli komputer jest wykluczany z zarządzania energią. W nowszych wersjach systemu Windows wykluczenie komputera z zarządzania energią powoduje przywrócenie oryginalnych wartości wszystkich ustawień zasilania. Nie można przywrócić oryginalnych wartości pojedynczych ustawień zasilania.  

## <a name="apply-power-plan-settings-individually"></a>Zastosuj ustawienia planu zasilania indywidualnie  
 Sprawdź efekt zastosowania każdego ustawienia zasilania przed zastosowaniem kolejnego, aby upewnić się, że wymagany efekt został osiągnięty. Aby uzyskać więcej informacji na temat ustawienia planu zasilania, zobacz [ustawień zarządzania energią dostępne w planie](../../../../core/clients/manage/power/create-and-apply-power-plans.md#BKMK_Plans) w temacie [sposób tworzenia i stosowania planów zasilania w programie System Center Configuration Manager](../../../../core/clients/manage/power/create-and-apply-power-plans.md).  

## <a name="regularly-monitor-computers-to-see-if-they-have-multiple-power-plans-applied"></a>Regularnie monitoruj komputery, aby sprawdzić, czy zastosowano na nich wiele planów zasilania  
 Zarządzanie energią oferuje raport zawierający komputery, na których zastosowano więcej niż jeden plan zasilania.  

 Jeśli komputer należy do wielu kolekcji, w których są stosowane różne plany zasilania, zostaną wykonane następujące akcje:  

-   Plan zasilania: Jeśli wiele wartości dla ustawień zasilania są stosowane do komputera, najmniej restrykcyjnego wartość jest używana.  

-   Godzina wznowienia: Jeśli wiele razy wznowienia są stosowane do komputera stacjonarnego, będą używane najbliżej północy czasu.  

     Aby uzyskać więcej informacji, zobacz [komputery z wieloma planów zasilania](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md#BKMK_Multiple) w temacie [monitora i planu na potrzeby zarządzania zużyciem energii w programie System Center Configuration Manager](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md). Aby uzyskać więcej informacji dotyczących sposobu zarządzania energią rozwiązywania konfliktów, zobacz [sposób tworzenia i stosowania planów zasilania w programie System Center Configuration Manager](../../../../core/clients/manage/power/create-and-apply-power-plans.md).  

## <a name="save-or-export-power-management-information-during-the-monitoring-and-planning-phase-of-power-management"></a>Zapisuj lub eksportuj informacje o zarządzaniu energią w fazie monitorowania i planowania zarządzania energią  
 Power management informacje używane przez raporty codzienne są przechowywane w bazie danych lokacji programu Configuration Manager 31 dni.  

 Informacje zarządzania energią używane przez miesięczne raporty są przechowywane w bazie danych lokacji programu Configuration Manager dla 13 miesięcy.  

 Podczas uruchamiania raportów fazach monitorowania i planowania i zgodności zarządzania energią, zapisać lub wyeksportować wyniki z wszystkie raporty, które mają być przechowywane dane dla porównania później w przypadku, gdy są nowsze usunięte przez program Configuration Manager.  

