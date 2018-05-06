---
title: Najlepsze rozwiązania dotyczące zarządzania energią
titleSuffix: Configuration Manager
description: Pobierz najlepsze rozwiązania dotyczące zarządzania energią w programie System Center Configuration Manager.
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: 9f7142e1-c972-4384-853b-2da1568cb3e3
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 480f7a890e82b46e2b2d69180763f39504a47e0c
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="best-practices-for-power-management-in-system-center-configuration-manager"></a>Najlepsze rozwiązania dotyczące zarządzania energią w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Stosować następujące najlepsze rozwiązania dotyczące zarządzania energią w programie System Center Configuration Manager.  

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

 Aby uzyskać więcej informacji, zobacz [Konfigurowanie zarządzania energią w programie System Center Configuration Manager](../../../../core/clients/manage/power/configuring-power-management.md).  

## <a name="first-apply-power-plans-to-a-test-collection-of-computers"></a>Najpierw zastosuj plany zasilania do testowej kolekcji komputerów  
 Należy zawsze przetestować efekty zastosowania planu zarządzania energią w testowej kolekcji komputerów przed zastosowaniem planu zasilania w większej kolekcji komputerów.  

 Ustawienia zasilania zastosowane na komputerach z systemem Windows XP lub Windows Server 2003 nie są przywracane do oryginalnych wartości, nawet jeśli komputer jest wykluczany z zarządzania energią. W nowszych wersjach systemu Windows wykluczenie komputera z zarządzania energią powoduje przywrócenie oryginalnych wartości wszystkich ustawień zasilania. Nie można przywrócić oryginalnych wartości pojedynczych ustawień zasilania.  

## <a name="apply-power-plan-settings-individually"></a>Zastosuj ustawienia planu zasilania indywidualnie  
 Sprawdź efekt zastosowania każdego ustawienia zasilania przed zastosowaniem kolejnego, aby upewnić się, że wymagany efekt został osiągnięty. Aby uzyskać więcej informacji na temat ustawień planu zasilania, zobacz [ustawienia planu zarządzania energią dostępne](../../../../core/clients/manage/power/create-and-apply-power-plans.md#BKMK_Plans) w temacie [tworzenie i stosowanie planów zasilania w programie System Center Configuration Manager](../../../../core/clients/manage/power/create-and-apply-power-plans.md).  

## <a name="regularly-monitor-computers-to-see-if-they-have-multiple-power-plans-applied"></a>Regularnie monitoruj komputery, aby sprawdzić, czy zastosowano na nich wiele planów zasilania  
 Zarządzanie energią oferuje raport zawierający komputery, na których zastosowano więcej niż jeden plan zasilania.  

 Jeśli komputer należy do wielu kolekcji, w których są stosowane różne plany zasilania, zostaną wykonane następujące akcje:  

-   Plan zasilania: Jeśli wiele wartości dla ustawień zasilania są stosowane do komputera, jest używana wartość najmniej restrykcyjna.  

-   Godzina wznowienia: Jeśli na komputerze zastosowano wiele godzin wznowienia, będzie używana godzina najbliższa północy.  

     Aby uzyskać więcej informacji, zobacz [komputery z wieloma planami zasilania](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md#BKMK_Multiple) w temacie [jak monitorować i planować zarządzanie energią w programie System Center Configuration Manager](../../../../core/clients/manage/power/monitor-and-plan-for-power-management.md). Aby uzyskać więcej informacji na temat sposobu rozwiązywania konfliktów przez funkcję zarządzania energią, zobacz [tworzenie i stosowanie planów zasilania w programie System Center Configuration Manager](../../../../core/clients/manage/power/create-and-apply-power-plans.md).  

## <a name="save-or-export-power-management-information-during-the-monitoring-and-planning-phase-of-power-management"></a>Zapisuj lub eksportuj informacje o zarządzaniu energią w fazie monitorowania i planowania zarządzania energią  
 Informacje dotyczące zarządzania energią używane w codziennych raportach są przechowywane w bazie danych lokacji programu Configuration Manager przez 31 dni.  

 Informacje dotyczące zarządzania energią używane w miesięcznych raportach są przechowywane w bazie danych lokacji programu Configuration Manager przez 13 miesięcy.  

 Podczas uruchamiania raportów podczas fazy monitorowania i zapewniania zgodności zarządzania energią, Zapisz lub wyeksportuj wyniki wszystkich raportów, które mają być przechowywane dane późniejszego porównania na wypadek, gdyby zostały później usunięte przez program Configuration Manager.  
