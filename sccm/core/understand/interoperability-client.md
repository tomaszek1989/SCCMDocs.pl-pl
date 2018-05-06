---
title: Rozszerzone współdziałanie klienta
titleSuffix: Configuration Manager
description: Informacje o używaniu rozszerzonej współdziałanie klienta do długoterminowego Obsługa statycznej klienta programu Configuration Manager z bieżącą lokacją gałęzi.
ms.date: 05/01/2018
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.topic: conceptual
ms.assetid: 600086d5-bd9e-4ac1-8ace-c7a62de80dc2
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: f46fdb622a55c7281de89c84d5e66e54ab149548
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="use-the-configuration-manager-client-software-for-extended-interoperability-with-future-versions-of-a-current-branch-site"></a>Użyj rozszerzonej współdziałanie z przyszłych wersji Current Branch lokacji oprogramowanie klienta programu Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*  

Wymagania biznesowe mogą nie pozwalają na regularnie aktualizację klienta programu Configuration Manager na niektórych urządzeniach. Na przykład konieczne może być zgodne z zasadami zarządzania zmiany lub urządzenie może być krytycznym. Uwzględnienia tych potrzeb przez zainstalowanie nowego klienta do użycia długoterminowej, wywołuje rozszerzoną współdziałanie klienta (EIC). EIC należy używać tylko dla określonych urządzeń, których nie można zaktualizować często, takie jak kiosku lub urządzeń w punktach sprzedaży. Nadal używać [automatyczne uaktualnianie klienta](/sccm/core/clients/manage/upgrade/upgrade-clients-for-windows-computers#use-automatic-client-upgrade) dla większości klientów. 

## <a name="how-this-scenario-works"></a>Jak działa w tym scenariuszu

Zwykle po zainstalowaniu nowego [aktualizacji w konsoli](/sccm/core/servers/manage/install-in-console-updates) programu Configuration Manager klienci automatycznie zaktualizować ich oprogramowanie klienckie aby mogli oni korzystać te nowe funkcje. W tym scenariuszu nadal aktualizacji do bieżącej gałęzi odbieranie nowe funkcje i aktualizacje. Większość urządzeń aktualizacji oprogramowania klienckiego programu Configuration Manager z każdego wersję aktualizacji, które będą instalowane. Jednak na podzbiór krytycznych systemów, które chcesz odbierać aktualizacje oprogramowania klienta, należy zainstalować klienta współdziałanie rozszerzonej. Tacy klienci nie należy instalować nowe oprogramowanie klienckie do momentu jawnie wdrożenia nowej wersji oprogramowania klienckiego do nich.



## <a name="supported-versions"></a>Obsługiwane wersje
W poniższej tabeli wymieniono wersje klienta programu Configuration Manager, które są obsługiwane dla tego scenariusza:

| Wersja  | Data udostępnienia  | Data zakończenia wsparcia  |
|---------|---------|---------|
|1802<br/>5.00.8634     | 1 maja 2018        | Nie wcześniej niż 1 może 2020        |
|1606<br/>5.00.8412     | 18 listopada 2016 r.        | 1 maja 2019        |

> [!TIP]  
> EIC jest obsługiwana dla co najmniej dwóch lat od daty wydania. Aby uzyskać więcej informacji na daty wydania, zobacz [pomocy technicznej dla programu System Center Configuration Manager bieżącej gałęzi wersji](/sccm/core/servers/manage/current-branch-versions-supported)).  

Planuje aktualizację klienta współdziałanie rozszerzonej na urządzeniach, którymi zarządzasz przy użyciu bieżącej gałęzi przed pomocy technicznej dla klienta wygaśnie. Aby to zrobić, pobrać nową wersję klienta firmy Microsoft, a następnie wdrożyć oprogramowanie zaktualizowanego klienta na urządzeniach korzystających z bieżącego rozszerzonej współdziałanie klienta.



## <a name="how-to-use-the-eic"></a>Jak używać EIC

1. Uzyskać obsługiwanej wersji programu EIC z `\SMSSETUP\Client` folderu nośnik instalacyjny aktualizacji programu Configuration Manager. Upewnij się, że należy skopiować całą zawartość folderu.  

2. Ręcznie zainstaluj EIC na tych urządzeniach. Aby uzyskać więcej informacji, zobacz [ręcznego zainstalowania klienta](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_Manual).  

    > [!Important]  
    > Podczas uaktualniania wersji 1606 klientów do wersji 1802, użyj opcji CCMSETUP **/AlwaysExcludeUpgrade:True**. W przeciwnym razie klient może otrzymać zasad z punktu zarządzania, aby automatycznie uaktualniał przed zasad wykluczania.

3. Te urządzenia można dodać do kolekcji, a wyłączenie tej kolekcji z automatycznych uaktualnień klienta. Aby uzyskać więcej informacji, zobacz [użycie automatycznego uaktualnienia klienta](/sccm/core/clients/manage/upgrade/upgrade-clients-for-windows-computers#use-automatic-client-upgrade).  

> [!TIP]  
> Można znaleźć na nośniku programu Configuration Manager w [Volume Licensing Service Center](https://www.microsoft.com/Licensing/servicecenter/Downloads/DownloadsAndKeys.aspx) (VLSC), przejdź do **pliki do pobrania i klucze** karcie, wyszukaj `System Center Config`, a następnie wybierz **programu System Center Config Mgr (wersji current branch)**.



## <a name="limitations-of-the-extended-interoperability-client"></a>Ograniczenia rozszerzonej współdziałanie klienta

- Aktualizacje oprogramowania klienckiego rozszerzonej współdziałanie nie są dostępne za pomocą aktualizacji w konsoli. Aby uzyskać więcej informacji na temat aktualizowania EIC klientów, zobacz [sposób użycia EIC](#how-to-use-the-eic).  

- EIC obsługuje tylko następujące funkcje:  

   - Aktualizacje oprogramowania  
   - Spis sprzętu i oprogramowania
   - Pakiety i programy



## <a name="next-steps"></a>Następne kroki

Aby upewnić się, że klienci są poprawnie zainstalowane na urządzenia, zobacz [jak monitorować klientów](/sccm/core/clients/manage/monitor-clients).
