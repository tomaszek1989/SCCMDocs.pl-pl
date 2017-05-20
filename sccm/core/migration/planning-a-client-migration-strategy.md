---
title: "Planowanie migracji klientów | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat zadań, które migracji klientów z hierarchii źródłowej do hierarchii docelowej programu System Center Configuration Manager."
ms.custom: na
ms.date: 12/30/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 2e27b0b7-7bd3-45cd-bc99-9c991606c637
caps.latest.revision: 6
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: ac4576035fda943e38d960dd425d44b7a6ef6a01
ms.openlocfilehash: b52ca4059dfeed08cabf1f75319da40d6499622f
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="plan-a-client-migration-strategy-in-system-center-configuration-manager"></a>Planowanie strategii migracji klienta w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Migracji klientów z hierarchii źródłowej do hierarchii docelowej programu System Center Configuration Manager, należy wykonać dwa zadania. Należy dokonać migracji obiektów skojarzonych z klientem, a następnie zainstalować ponownie lub przypisać ponownie klientów z hierarchii źródłowej do hierarchii docelowej. Migrację obiektów należy przeprowadzić najpierw po to, żeby były dostępne podczas migracji klientów. Obiekty skojarzone z klientami migruje się za pomocą zadań migracji. Aby uzyskać informacje o sposobach migracji obiektów, które są skojarzone z klientem, zobacz [Planowanie strategii zadania migracji w programie System Center Configuration Manager](../../core/migration/planning-a-migration-job-strategy.md).  

 Informacje w poniższych sekcjach ułatwią planowanie migracji klientów do hierarchii docelowej.  

-   [Planowanie migracji klientów do hierarchii docelowej](#Planning_for_Client_Agent_Migration)  

-   [Planowanie obsługi danych zachowywanych na klientach podczas migracji](#Planning_for_Client_Data_Migration)  

-   [Zaplanuj migrację danych spisu i zgodności podczas migracji](#Planning_for_Inventory_data_migration)  

##  <a name="Planning_for_Client_Agent_Migration"></a> Planowanie migracji klientów do hierarchii docelowej  
 Podczas migracji klientów z hierarchii źródłowej, oprogramowanie klienckie na komputerze klienckie jest uaktualniane do dopasowania do wersji produktu hierarchii docelowej.  

-   **Hierarchia źródłowa programu Configuration Manager 2007:** Podczas migracji klientów z hierarchii źródłowej, która działa obsługiwana wersja programu Configuration Manager, oprogramowanie klienckie jest uaktualniane do wersji klienckiej dla hierarchii docelowej.  

-   **System Center 2012 Configuration Manager lub nowszego hierarchii źródłowej:** Podczas migracji klientów między hierarchiami tej samej wersji produktu oprogramowanie klienckie nie zmienić lub uaktualnić. Zamiast tego następuje zmiana przypisania klienta z hierarchii źródłowej do lokacji w hierarchii docelowej.  

    > [!NOTE]  
    >  Jeśli wersja produktu jakiejś hierarchii nie jest obsługiwana pod kątem migracji do hierarchii docelowej, należy uaktualnić wszystkie lokacje i klientów w hierarchii źródłowej do zgodnej wersji produktu. Po uaktualnieniu hierarchii źródłowej do obsługiwanej wersji produktu będzie można dokonać migracji między hierarchiami. Aby uzyskać więcej informacji, zobacz [wersje programu Configuration Manager obsługujące migrację](../../core/migration/prerequisites-for-migration.md#BKMK_SupportedMigrationVersions) w [wymagania wstępne dotyczące migracji w programie System Center Configuration Manager](../../core/migration/prerequisites-for-migration.md).  

W planowaniu migracji klientów mogą pomóc następujące informacje:  

-   Aby uaktualnić klientów lub zmienić ich przypisanie z lokacji źródłowej na lokację docelową, można użyć dowolnej metody wdrażania klientów, która jest obsługiwana w celu wdrażania klientów w hierarchii docelowej. Do typowych metod wdrażania klientów należą: instalacja wypychana klienta, dystrybucja oprogramowania, instalacja klienta oparta na zasadach grupy i instalacja klienta oparta na aktualizacji oprogramowania. Aby uzyskać więcej informacji, zobacz [metody instalacji klienta w programie System Center Configuration Manager](../../core/clients/deploy/plan/client-installation-methods.md).  

-   Upewnij się, że urządzenie uruchomionym oprogramowaniem klienckim w hierarchii źródłowej spełnia minimalne wymagania sprzętowe i dysponuje systemem operacyjnym, który jest obsługiwany przez wersję programu Configuration Manager w hierarchii docelowej.  

-   Przed migracją klienta należy uruchomić zadanie migracji informacji, który będzie używany przez klienta w hierarchii docelowej.  

-   Uaktualnieni klienci zachowują swoją historię uruchomień wdrożeń. Zapobiega to niepotrzebnemu ponownemu uruchamianiu w hierarchii docelowej wdrożeń.  

    -   Dla klientów programu Configuration Manager 2007 jest zachowywana historia uruchamiania anonsu.  

    -   W przypadku klientów z System Center 2012 Configuration Manager lub System Center Configuration Manager jest zachowywana historia uruchamiania wdrożenia.  

-   Klientów można migrować z lokacji w hierarchii źródłowej w dowolnie wybranej kolejności. Jednakże należy rozważyć Migrowanie ograniczonej liczby klientów fazami zamiast dużej liczby klientów naraz. Migracja fazami zmniejsza wymagania związane z przepustowością sieci i obciążenie serwera przetwarzaniem pojawiające się, kiedy każdy nowo uaktualniony klient przekazuje swój wstępny pełny stan zapasów i dane dotyczące zgodności przypisanej do niego lokacji.  

-   Podczas migrowania klientów programu Configuration Manager 2007 istniejące oprogramowanie klienta zostaje odinstalowane z komputera klienckiego i nowe oprogramowanie klienckie jest zainstalowane.  

-   Menedżer konfiguracji nie można migrować klient programu Configuration Manager 2007 z klienta App-V zainstalowany, chyba że wersja klienta App-V 4.6 SP1 lub nowszym.  

Można monitorować postęp migracji klientów w **migracji** węzła **administracji** obszaru roboczego w konsoli programu Configuration Manager.  

Po przeprowadzeniu migracji klienta do hierarchii docelowej, nie będzie można zarządzać danym urządzeniem za pomocą hierarchii źródłowej i należy rozważyć usunięciu klienta z hierarchii źródłowej. Chociaż nie jest to wymaganie związane z migracją hierarchii, może to pomóc zapobiec identyfikowaniu zmigrowanego klienta w raporcie hierarchii źródłowej lub nieprawidłowemu obliczaniu zasobów obydwu hierarchii podczas migracji. Na przykład kiedy zmigrowany klient pozostaje w bazie danych lokacji źródłowej, uruchomienie raportu o aktualizacjach oprogramowania może nieprawidłowo zidentyfikować komputer jako zasób niezarządzany, podczas gdy zarządza nim już hierarchia docelowa.  

##  <a name="Planning_for_Client_Data_Migration"></a> Planowanie obsługi danych zachowywanych na klientach podczas migracji  
Podczas migracji klienta z hierarchii źródłowej do hierarchii docelowej część informacji jest pozostawiana na urządzeniu, podczas gdy inne informacje przestają być na nim dostępne po migracji.  

Na urządzeniu klienckim są zachowywane następujące informacje:  

-   Unikatowy identyfikator (GUID), który kojarzy klienta z informacjami o nim w bazie danych programu Configuration Manager.  

-   Historia anonsowania lub wdrażania, która zapobiega niepotrzebnemu ponownemu uruchamianiu anonsowań lub wdrożeń na klientach w hierarchii docelowej.  

Na urządzeniu klienckim nie są zachowywane następujące informacje:  

-   Pliki z pamięci podręcznej klienta. Jeśli klient wymaga tych plików do instalacji oprogramowania, pobiera je ponownie z hierarchii docelowej.  

-   Informacje z hierarchii źródłowej o ewentualnych anonsach lub wdrożeniach, które nie zostały jeszcze uruchomione. Aby móc uruchomić na kliencie anonse lub wdrożenia po jego migracji, należy ponownie wdrożyć je na kliencie w hierarchii docelowej.  

-   Informacje o stanie zapasów. Klient wysyła te informacje do swojej przypisanej lokacji w hierarchii docelowej ponownie po migracji i wygenerowaniu nowych danych klienta.  

-   Dane zgodności. Klient wysyła te informacje do swojej przypisanej lokacji w hierarchii docelowej ponownie po migracji i wygenerowaniu nowych danych klienta.  

Podczas migracji klienta, nie są zachowywane informacje, który znajduje się w ścieżce rejestru i plików klienta programu Configuration Manager. Po migracji należy ponownie zastosować te ustawienia. Typowe ustawienia obejmują między innymi:  

-   Schematy zasilania  

-   Ustawienia logowania  

-   Ustawienia zasad lokalnych  

Ponadto może zajść konieczność ponownego zainstalowania niektórych aplikacji.  

##  <a name="Planning_for_Inventory_data_migration"></a> Planowanie stanu zapasów i danych zgodności podczas migracji  
Stan zapasów i dane zgodności klienta nie są zachowywane podczas migracji klienta do hierarchii docelowej. Zamiast tego informacje te są odtwarzane w hierarchii docelowej, kiedy klient po raz pierwszy wysyła informacje do przypisanej do niego lokacji. Aby pomóc w zmniejszeniu odnośnych wymagań związanych z przepustowością sieci i obciążenie serwera przetwarzaniem warto rozważyć migrowanie ograniczonej liczby klientów fazami zamiast dużej liczby klientów naraz.  

 Nie można ponadto migrować dostosowań zapasów sprzętowych z hierarchii źródłowej. Należy wprowadzić je w hierarchii docelowej niezależnie od migracji. Aby uzyskać informacje o sposobach rozszerzania zapasów sprzętu, zobacz [Konfigurowanie spisu sprzętu w programie System Center Configuration Manager](../../core/clients/manage/inventory/configure-hardware-inventory.md).  

