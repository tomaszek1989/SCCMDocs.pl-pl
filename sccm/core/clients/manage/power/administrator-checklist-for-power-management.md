---
title: "Lista kontrolna administratora dotycząca zarządzania energią"
titleSuffix: Configuration Manager
description: "Użyj Lista kontrolna administratora ułatwiają planowanie i Implementowanie zarządzania energią w programie System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 94e42cbe-9df8-4228-a04e-0ad7626180ca
caps.latest.revision: "6"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 547c364f4c33136ece9b90ceed298ec2fcb7329c
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="administrator-checklist-for-power-management-in-system-center-configuration-manager"></a>Lista kontrolna administratora dotycząca zarządzania energią w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Ta lista kontrolna administratora zawiera kroki zalecane do wykonania dla zarządzania energią programu System Center Configuration Manager w organizacji.  

## <a name="configuring-power-management"></a>Konfigurowanie zarządzania energią  
 Wykonanie tych kroków ułatwia skonfigurowanie hierarchii w celu zebrania informacji dotyczących zarządzania energią z komputerów klienckich.  

> [!IMPORTANT]  
>  Nie należy stosować planów zasilania na komputerach w hierarchii, dopóki dane dotyczące zasilania nie zostaną zebrane z komputerów klienckich i przeanalizowane. Zastosowanie nowych ustawień zarządzania energią na komputerach przed sprawdzeniem ustawień już istniejących może spowodować wzrost zużycia energii.  

|Zadanie|Szczegóły|  
|----------|-------------|  
|Przejrzyj pojęciami dotyczącymi zarządzania energią w bibliotece dokumentacji programu Configuration Manager.|Zobacz [wprowadzenie do zarządzania energią](introduction-to-power-management.md).|  
|Przegląd wymagań wstępnych zarządzania energią w bibliotece dokumentacji programu Configuration Manager.|Zobacz [wymagania wstępne dotyczące zarządzania energią](prerequisites-for-power-management.md).|  
|Zapoznaj się z informacjami o najlepszych rozwiązaniach dotyczących zarządzania energią.|Zobacz [najlepsze rozwiązania dotyczące zarządzania energią](best-practices-for-power-management.md).|  
|Konfigurowanie kolekcji zarządzania zużyciem energii z komputerów w danym środowisku.|Użyj **kolekcji do raportowania danych bazowych**, **kolekcji do raportowania danych bazowych**, **kolekcji komputerów zarządzać energią**, **kolekcji komputerów do zasilania, które zostaną zastosowane plany**, **kolekcji komputerów do zasilania, które zostaną zastosowane plany**, i **kolekcje komputerów z systemem Windows Server** ułatwiają zarządzanie ustawieniami zasilania dla komputerów w hierarchii. Można tworzyć wiele kolekcji i stosować różne plany zasilania do każdej kolekcji.|  
|Włącz zarządzanie energią.|Przed rozpoczęciem korzystania z funkcji zarządzania energią należy ją włączyć i skonfigurować wymagane ustawienia klientów. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zarządzania energią](configuring-power-management.md).|  
|Zbierz informacje dotyczące zarządzania energią z komputerów klienckich.|Danych zarządzania energią są zgłaszane przez klientów za pośrednictwem spisu sprzętu programu Configuration Manager. W zależności od skonfigurowanego harmonogramu spisu sprzętu pobieranie spisu ze wszystkich komputerów klienckich może potrwać jakiś czas.|  

## <a name="monitoring-and-planning-phase"></a>Faza monitorowania i planowania  

|Zadanie|Szczegóły|  
|----------|-------------|  
|Uruchom raport **Aktywność komputera**.|Raport **Aktywność komputera** zawiera wykres działania monitora, komputera i użytkownika dla określonej kolekcji w wybranym okresie. Ten raport łączy się z raportem **Szczegóły aktywności komputera** , który zawiera informacje na temat możliwości uśpienia i przebudzenia komputerów w określonej kolekcji. Aby uzyskać więcej informacji, zobacz [jak monitorować i planować zarządzanie energią](monitor-and-plan-for-power-management.md).|  
|Uruchom raport **Zużycie energii** lub **Dzienne zużycie energii**.|Raporty **Zużycie energii** i **Dzienne zużycie energii** zawierają całkowite miesięczne zużycie energii w kilowatach na godzinę (kWh) dla określonej kolekcji w wybranym okresie. Aby uzyskać więcej informacji, zobacz [jak monitorować i planować zarządzanie energią](monitor-and-plan-for-power-management.md).|  
|Uruchom raport **Wpływ na środowisko** lub  **Dzienny wpływ na środowisko**.|Raporty **Wpływ na środowisko** i **Dzienny wpływ na środowisko** zawierają wykres przedstawiający poziom oszczędności emisji dwutlenku węgla (CO2) dla określonej kolekcji komputerów w wybranym okresie. Aby uzyskać więcej informacji, zobacz [jak monitorować i planować zarządzanie energią](monitor-and-plan-for-power-management.md).|  
|Uruchom raport **Koszt energii** lub **Dzienny koszt energii**.|Raporty **Koszt energii** i **Dzienny koszt energii** zawierają całkowity koszt zużycia energii w wybranym okresie. Aby uzyskać więcej informacji, zobacz [jak monitorować i planować zarządzanie energią](monitor-and-plan-for-power-management.md).|  
|Uruchom raport **Możliwości zasilania**.|Raport **Możliwości zasilania** zawiera opis możliwości zarządzania energią dla komputerów w określonej kolekcji. Aby uzyskać więcej informacji, zobacz [jak monitorować i planować zarządzanie energią](monitor-and-plan-for-power-management.md).|  
|Uruchom raport **Ustawienia zasilania**.|Raport **Ustawienia zasilania** zawiera zagregowaną listę bieżących ustawień zasilania używanych na komputerach w określonej kolekcji. Aby uzyskać więcej informacji, zobacz [jak monitorować i planować zarządzanie energią](monitor-and-plan-for-power-management.md).|  
|Wyklucz wszystkie wymagane kolekcje komputerów z funkcji zarządzania energią.|Zobacz [Konfigurowanie zarządzania energią](configuring-power-management.md).|  

> [!IMPORTANT]  
>  Upewnij się, że zapisano informacje z raportów dotyczących zarządzania energią wygenerowanych w fazie monitorowania i planowania. Te dane można porównywać z informacjami dotyczącymi zarządzania energią wygenerowanymi w fazach wymuszania i sprawdzania zgodności w celu oszacowania oszczędności zużycia energii, kosztów energii i wpływu na środowisko, które wynikają z zastosowania planu zasilania na komputerach w hierarchii.  

## <a name="enforcement-phase"></a>Faza wymuszania  

|Zadanie|Szczegóły|  
|----------|-------------|  
|Wybierz istniejące plany zasilania lub utwórz nowe plany zasilania dla kolekcji komputerów w organizacji.|Zobacz [tworzenie i stosowanie planów zasilania](create-and-apply-power-plans.md).|  
|Zastosuj te plany zasilania na komputerach.|Zobacz [tworzenie i stosowanie planów zasilania](create-and-apply-power-plans.md).|  

## <a name="compliance-phase"></a>Faza sprawdzania zgodności  

|Zadanie|Szczegóły|  
|----------|-------------|  
|Uruchom raport **Aktywność komputera**.|Raport **Aktywność komputera** zawiera wykres działania monitora, komputera i użytkownika dla określonej kolekcji w wybranym okresie. Ten raport łączy się z raportem **Szczegóły aktywności związanej z zasilaniem komputera** , który zawiera informacje na temat możliwości uśpienia i przebudzenia komputerów w określonej kolekcji. Aby uzyskać więcej informacji, zobacz [jak monitorować i planować zarządzanie energią](monitor-and-plan-for-power-management.md).|  
|Uruchom raport **Zużycie energii** lub **Dzienne zużycie energii**.|Raporty **Zużycie energii** i **Dzienne zużycie energii** zawierają całkowite miesięczne zużycie energii w kilowatach na godzinę (kWh) dla określonej kolekcji w wybranym okresie. Aby uzyskać więcej informacji, zobacz [jak monitorować i planować zarządzanie energią](monitor-and-plan-for-power-management.md).|  
|Uruchom raport **Wpływ na środowisko** lub **Dzienny wpływ na środowisko**.|Raporty **Wpływ na środowisko** i **Dzienny wpływ na środowisko** zawierają wykres przedstawiający poziom oszczędności emisji dwutlenku węgla (CO2) dla określonej kolekcji komputerów w wybranym okresie. Aby uzyskać więcej informacji, zobacz [jak monitorować i planować zarządzanie energią](monitor-and-plan-for-power-management.md).|  
|Uruchom raport **Koszt energii** lub **Dzienny koszt energii**.|Raporty **Koszt energii** i **Dzienny koszt energii** zawierają całkowity koszt zużycia energii w wybranym okresie. Aby uzyskać więcej informacji, zobacz [jak monitorować i planować zarządzanie energią](monitor-and-plan-for-power-management.md).|  

## <a name="troubleshooting"></a>Rozwiązywanie problemów  

|Zadanie|Szczegóły|  
|----------|-------------|  
|Jeśli komputery w hierarchii nie zostały wprowadzone w stan uśpienia lub hibernacji, uruchom **Raport o braku usypiania zasilania na komputerze** , aby wyświetlić możliwe przyczyny.|**Raport o braku usypiania** przedstawia listę typowych przyczyn, które uniemożliwiały włączanie stanu uśpienia i hibernacji na komputerach, oraz liczbę komputerów, których te przyczyny dotyczyły, w określonym przedziale czasu. Aby uzyskać więcej informacji, zobacz [jak monitorować i planować zarządzanie energią](monitor-and-plan-for-power-management.md).|  
|W przypadku zastosowania wielu planów zasilania na jednym komputerze zostanie użyty najmniej restrykcyjny plan zasilania. Uruchom raport **Komputery z wieloma planami zasilania** , aby wyświetlić komputery, na których zastosowano wiele planów zasilania.|Zobacz **komputery z wieloma planami zasilania** w [jak monitorować i planować zarządzanie energią](monitor-and-plan-for-power-management.md).|  
