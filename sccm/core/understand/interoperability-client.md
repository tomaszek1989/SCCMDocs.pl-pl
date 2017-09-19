---
title: "Należy użyć klienta programu Configuration Manager rozszerzonej współdziałanie z bieżącej gałęzi | Dokumentacja firmy Microsoft"
description: "Informacje o używaniu klienta z długoterminowe obsługi gałęzi programu Configuration Manager z lokacją bieżącej gałęzi."
ms.custom: na
ms.date: 08/09/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 600086d5-bd9e-4ac1-8ace-c7a62de80dc2
caps.latest.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 9772224be78eee2777137225a59b53b1fd77a627
ms.sourcegitcommit: b438515490e04fb09c82a8af642d38e9a0605178
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2017
---
# <a name="use-the-configuration-manager-client-software-for-extended-interoperability-with-future-versions-of-a-current-branch-site"></a>Użyj rozszerzonej współdziałanie z przyszłych wersji Current Branch lokacji oprogramowanie klienta programu Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch), (długoterminowej obsługi Branch)*  

W niektórych przypadkach zasad firmy może nie pozwalają na regularnie aktualizację klienta programu Configuration Manager na niektórych komputerach. Na przykład konieczne może być zgodne z zasadami zarządzania zmiany lub urządzenie może być krytycznym.

Gdy powinno być kontynuowane użycie automatycznego uaktualnienia klienta, gdy to możliwe w dla większości klientów, w programie Configuration Manager zaktualizuje 1610, mogą obsługiwać te potrzeby przez zainstalowanie nowego klienta do użycia długoterminowej, wywołuje rozszerzoną współdziałanie klienta (EIC).

EIC jest zgodna z wersją 1610 lokacji programu Configuration Manager lub nowszego. EIC należy używać tylko dla określonych komputerów, które nie może być często aktualizowana, takich jak kiosku lub urządzeń w punktach sprzedaży. Korzystając z najnowszych klienta programu Configuration Manager dla wszystkich innych komputerów.

## <a name="how-this-scenario-works"></a>Jak działa w tym scenariuszu

Zwykle po zainstalowaniu nowej aktualizacji w konsoli dla bieżącej gałęzi klientów automatycznie aktualizuje oprogramowanie klienckie, ich aby mogli oni korzystać te nowe funkcje.

W tym scenariuszu możesz użyć bieżącej gałęzi i odbierać nowe funkcje i aktualizacje. Większość klientów uruchomione oprogramowanie klienckie z bieżącej gałęzi i może je aktualizować przy każdej wersji aktualizacji, które należy zainstalować oprogramowanie klienta. Jednak na podzbiór krytycznych systemów, które chcesz odbierać aktualizacje oprogramowania klienta, należy zainstalować klienta współdziałanie rozszerzonej. Ci klienci nie należy instalować nowe oprogramowanie klienckie, dopóki nie zostanie jawnie wdrożony nowej wersji oprogramowania klienckiego do nich.

>[!IMPORTANT]
>Bieżąca gałąź witryny musi być zainstalowana wersja 1610 lub nowszej.

## <a name="how-to-use-the-eic"></a>Jak używać EIC

1. Uzyskaj EIC (wersja klienta 5.00.8412) z folderu \SMSSETUP\Client z nośnika instalacyjnego programu Configuration Manager 1606 aktualizacji. Upewnij się, że należy skopiować całą zawartość folderu.
2. Ręcznie zainstaluj EIC na tych urządzeniach. [Przeczytaj więcej informacji o sposobie ręcznego zainstalowania klienta](/sccm/core/clients/deploy/deploy-clients-to-windows-computers#BKMK_Manual).
3. Wyklucz tej kolekcji uaktualnienia klienta.

>[!TIP]
>Aby znaleźć System Center Configuration Manager w wersji 1606 w wolumin licencjonowania Service Center (VLSC), przejdź do **pliki do pobrania i klucze** karcie [VLSC](https://www.microsoft.com/Licensing/servicecenter/Downloads/DownloadsAndKeys.aspx), wyszukaj "system center konfiguracji", a następnie wybierz **System Center Config Mgr (bieżącej gałęzi i LTSB)**.

## <a name="the-extended-interoperability-client-software"></a>Oprogramowanie klienckie rozszerzonej współdziałanie

Bieżący EIC będą nadal obsługiwane zaktualizowane wersje programu Configuration Manager bieżącej gałęzi do momentu co najmniej 18 listopada 2018. Po upływie tego czasu Sprawdź na tej stronie Szczegóły nowego EIC lub rozszerzenia obsługi EIC istniejących.

>[!TIP]
>EIC jest obsługiwana w przypadku co najmniej dwóch lat od daty wydania (zobacz [pomocy technicznej dla programu System Center Configuration Manager bieżącej gałęzi wersji](/sccm/core/servers/manage/current-branch-versions-supported)). Na przykład obsługa bieżącego EIC wynosi dwa lata po wydaniu 1610, czyli 18 listopada 2018.

Planuje aktualizację klienta współdziałanie rozszerzonej na urządzeniach, którymi zarządzasz przy użyciu bieżącej gałęzi przed pomocy technicznej dla klienta wygaśnie. Aby to zrobić, pobrać nową wersję klienta firmy Microsoft, a następnie wdrożyć oprogramowanie zaktualizowanego klienta na urządzeniach korzystających z bieżącego rozszerzonej współdziałanie klienta.

## <a name="limitations-of-the-extended-interoperability-client"></a>Ograniczenia rozszerzonej współdziałanie klienta

- Aktualizacje oprogramowania klienckiego rozszerzonej współdziałanie nie są dostępne za pomocą aktualizacji w konsoli. Dodatkowe szczegóły dotyczące wdrażania oprogramowania zaktualizowanego klienta są udostępniane po zwolnieniu zaktualizowanego klienta.
- EIC obsługuje tylko aktualizacje oprogramowania, spisu i pakietów i programów.

## <a name="next-steps"></a>Następne kroki

Skorzystaj z informacji w [jak monitorować klientów](/sccm/core/clients/manage/monitor-clients) aby upewnić się, że klienci są poprawnie zainstalowane na urządzeniach ma.
