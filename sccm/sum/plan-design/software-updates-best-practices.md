---

title: "Najlepsze praktyki dotyczące aktualizacji oprogramowania | Dokumentacja firmy Microsoft"
description: "Należy stosować te najlepsze rozwiązania dotyczące aktualizacji oprogramowania System Center Configuration Manager."
keywords: 
author: dougeby
ms.author: dougeby
manager: angrobe
ms.date: 10/06/2016
ms.topic: article
ms.prod: configuration-manager
ms.service: 
ms.technology:
- configmgr-sum
ms.assetid: 6d20389a-9de2-4a64-bced-9fc4fa519174
ms.translationtype: Machine Translation
ms.sourcegitcommit: d94acac84f052a01de9d9c9f65f237c0006c45b8
ms.openlocfilehash: 5df20f3703442de1be6220ca2770e182e330c036
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017



---
# <a name="best-practices-for-software-updates-in-system-center-configuration-manager"></a>Najlepsze rozwiązania dotyczące aktualizacji oprogramowania w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Ten temat zawiera najlepsze rozwiązania dotyczące aktualizacji oprogramowania System Center Configuration Manager. Informacje zostały podzielone na najlepsze rozwiązania w zakresie instalacji początkowej oraz najlepsze rozwiązania w zakresie trwających operacji.  

## <a name="installation-best-practices"></a>Najlepsze rozwiązania dotyczące instalacji  
 Podczas instalowania aktualizacji oprogramowania w programie Configuration Manager, należy użyć następujących najlepszych rozwiązań.  

### <a name="use-a-shared-wsus-database-for-software-update-points"></a>Użycie udostępnionej bazy danych programu WSUS dla punktów aktualizacji oprogramowania  
 W przypadku instalowania w lokacji głównej więcej niż jednego punktu aktualizacji oprogramowania należy użyć tej samej bazy danych programu WSUS dla każdego punktu aktualizacji oprogramowania w tym samym lesie usługi Active Directory. Współużytkowanie tej samej bazy danych może znacząco zniwelować wpływ na wydajność klientów i sieci w przypadku, gdy klienci przełączają się na nowy punkt aktualizacji oprogramowania. Kiedy klient przełącza się na nowy punkt aktualizacji oprogramowania, który współużytkuje tę samą bazę danych co stary punkt aktualizacji oprogramowania, ciągle wykonywane jest skanowanie różnicowe, ale ta operacja jest wykonywana w znacznie mniejszym zakresie niż w przypadku, gdyby serwer WSUS miał własną bazę danych.  

> [!IMPORTANT]  
>  Foldery lokalne zawartości programu WSUS również muszą zostać udostępnione w przypadku korzystania z udostępnionej bazy danych programu WSUS na potrzeby punktów aktualizacji oprogramowania.  

 Aby uzyskać więcej informacji o przełączaniu punktów aktualizacji oprogramowania, zobacz [przełączaniu punktów aktualizacji oprogramowania](../../sum/plan-design/plan-for-software-updates.md#BKMK_SUPSwitching) w sekcji [planowania aktualizacji oprogramowania System Center Configuration Manager](../../sum/plan-design/plan-for-software-updates.md) tematu.  

### <a name="when-configuration-manager-and-wsus-use-the-same-sql-server-configure-one-of-these-to-use-a-named-instance-and-the-other-to-use-the-default-instance-of-sql-server"></a>Kiedy programy Configuration Manager i WSUS używają tego samego programu SQL Server, należy skonfigurować jeden z tych programów do użycia wystąpienia nazwanego, a drugi do użycia wystąpienia domyślnego serwera SQL.  
 W przypadku baz danych programu Configuration Manager i WSUS używają tego samego serwera SQL i współużytkują to samo wystąpienie programu SQL Server, nie może łatwo określić użycia zasobów, między dwiema aplikacjami. Używasz innego wystąpienia programu SQL Server dla programu Configuration Manager i programu WSUS jest łatwiejsze Rozwiązywanie problemów i diagnozowanie problemów z wykorzystaniem zasobów, które mogą wystąpić w przypadku każdej aplikacji.  

### <a name="specify-the-store-updates-locally-setting-for-the-wsus-installation"></a>Określenie ustawienia „Przechowuj aktualizacje lokalnie” dla instalacji programu WSUS  
 Podczas instalowania programu WSUS, wybierz **Przechowuj aktualizacje lokalnie** ustawienie. W takim przypadku postanowienia licencyjne, które są powiązane z aktualizacjami oprogramowania, zostają pobrane podczas procesu synchronizacji i zapisane na lokalnym dysku twardym dla serwera WSUS. Jeśli to ustawienie nie zostanie wybrane, na komputerach klienckich może się nie powieść skanowanie pod kątem zgodności z aktualizacjami oprogramowania, które mają postanowienia licencyjne. Podczas instalacji punktu aktualizacji oprogramowania menedżer synchronizacji programu WSUS sprawdza domyślnie co 60 minut, czy to ustawienie jest włączone.  

## <a name="operational-best-practices"></a>Najlepsze rozwiązanie w zakresie operacji  
 Podczas korzystania z aktualizacji oprogramowania należy stosować poniższe najlepsze rozwiązania:  

### <a name="limit-software-updates-to-1000-in-a-single-software-update-deployment"></a>Ograniczenie do 1000 liczby aktualizacji oprogramowania w pojedynczym wdrożeniu aktualizacji  
 Liczbę aktualizacji oprogramowania w każdym wdrożeniu aktualizacji oprogramowania należy ograniczyć do 1000. Podczas tworzenia zasady wdrażania automatycznego należy upewnić się, że określone kryteria nie zwrócą więcej niż 1000 aktualizacji oprogramowania. W przypadku ręcznego wdrażania aktualizacji oprogramowania nie należy wybierać więcej niż 1000 aktualizacji.  

### <a name="create-a-new-software-update-group-each-time-an-automatic-deployment-rule-runs-for-patch-tuesday-and-for-general-deployment"></a>Utwórz nową grupę aktualizacji oprogramowania zawsze, gdy zasady wdrażania automatycznego jest wykonywana WE "Wtorek poprawek" oraz na potrzeby ogólnego wdrożenia  
 Istnieje limit 1000 aktualizacji oprogramowania w jednym wdrożeniu. Podczas tworzenia zasady wdrażania automatycznego można określić, czy należy użyć istniejącej grupy aktualizacji lub utworzyć nową grupę aktualizacji za każdym razem, gdy zasada jest wykonywana. Jeśli w zasadach wdrażania automatycznego są określane kryteria, których wynikiem jest wiele aktualizacji oprogramowania, a zasada będzie wykonywana zgodnie z harmonogramem cyklicznym, należy określić opcję tworzenia nowej grupy aktualizacji oprogramowania za każdym razem, gdy zasada jest wykonywana. Pozwoli to zapobiec sytuacji, w której zostanie przekroczony limit 1000 aktualizacji oprogramowania na wdrożenie.  

### <a name="use-an-existing-software-update-group-for-automatic-deployment-rules-for-endpoint-protection-definition-updates"></a>Użycie istniejącej grupy aktualizacji oprogramowania dla zasad wdrażania automatycznego dotyczących aktualizacji definicji programu Endpoint Protection  
 Zawsze należy używać istniejącej grupy aktualizacji oprogramowania dla zasady wdrażania automatycznego w celu regularnego wdrażania aktualizacji definicji programu Endpoint Protection. W przeciwnym razie w miarę upływu czasu mogą zostać utworzone setki grup aktualizacji oprogramowania. Zwykle wydawcy aktualizacji oprogramowania określają wygaśnięcie aktualizacji po ich zastąpieniu przez cztery nowsze aktualizacje. Z tego powodu grupa aktualizacji oprogramowania, które zostaje utworzona przez zasadę wdrażania automatycznego, nigdy nie będzie zawierać więcej niż czterech aktualizacji definicji dla danego wydawcy: są to jedna aktualizacja aktywna i trzy aktualizacje zastąpione.  

## <a name="see-also"></a>Zobacz też  
 [Zaplanuj aktualizacje oprogramowania System Center Configuration Manager](../../sum/plan-design/plan-for-software-updates.md)

