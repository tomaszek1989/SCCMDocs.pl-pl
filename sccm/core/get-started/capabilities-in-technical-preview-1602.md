---
title: "Możliwości w Technical Preview 1602 programu Configuration Manager"
description: "Informacje na temat funkcji dostępnych w Technical Preview programu System Center Configuration Manager, wersja 1602."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology:
- configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1b9265d1-b461-47f8-b7ef-885da0fdd969
caps.latest.revision: 6
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
ms.translationtype: Machine Translation
ms.sourcegitcommit: dab5da5a4b5dfb3606a8a6bd0c70a0b21923fff9
ms.openlocfilehash: 2354f885aaf69683004ad78f0e1978e78fee9145
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="capabilities-in-technical-preview-1602-for-system-center-configuration-manager"></a>Możliwości w Technical Preview 1602 System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (Technical Preview)*

Ten artykuł wprowadza do funkcji, które są dostępne w Technical Preview programu System Center Configuration Manager, wersja 1602. Można zainstalować tę wersję, aby zaktualizować i dodawać nowe funkcje do lokacji programu Configuration Manager technical preview. Przed zainstalowaniem tej wersji technical preview, przejrzyj temat wprowadzające [Technical Preview dla programu System Center Configuration Manager](../../core/get-started/technical-preview.md), aby zapoznać się z ogólnym wymagania i ograniczenia dotyczące używania technical preview, jak zaktualizować między wersjami i jak Wyraź swoją opinię dotyczącą funkcji w technical preview.  

 Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.  

##  <a name="BKMK_MDM"></a>Ulepszenia dotyczące zarządzania urządzeniami przenośnymi  

### <a name="ios-activation-lock"></a>iOS blokadę aktywacji  
 Program System Center Configuration Manager ułatwia zarządzanie blokadą aktywacji systemu iOS — funkcją aplikacji Znajdź mój iPhone dla urządzeń z systemem iOS 7.1 lub nowszym. Blokada aktywacji jest włączana automatycznie w przypadku użycia aplikacji Znajdź mój iPhone na urządzeniu. Jeśli ta funkcja została włączona, należy podać identyfikator Apple ID i hasło użytkownika, aby można było wykonać następujące czynności:  

-   Wyłączenie aplikacji Znajdź mój iPhone  

-   Wymazanie urządzenia  

-   Ponowne uaktywnienie urządzenia  

 Program Configuration Manager mogą poprosić o stan blokady aktywacji zarówno nadzorowanego i bez kontroli urządzeń z systemem iOS 7.1 i nowsze. W przypadku urządzeń nadzorowanych usługa Intune może pobrać kod obejścia blokady aktywacji i wystawić go bezpośrednio na urządzeniu.  

 Aby uzyskać szczegółowe informacje, zobacz [chronić iOS urządzeniami przy użyciu blokady aktywacji obejścia dla programu Configuration Manager](/sccm/mdm/deploy-use/manage-ios-activation-lock)  

##  <a name="BKMK_SC1601"></a>Ulepszenia programu Software Center w wersji 1602  

### <a name="refresh-pc-machine-and-user-policy-from-software-center"></a>Odświeżanie zasad komputera i użytkownika komputera z Centrum oprogramowania  
 Nowa opcja **zasady synchronizacji** został dodany do **opcje** > **Konserwacja komputera** strony Centrum oprogramowania, które powoduje, że komputer, aby odświeżyć jego programu Configuration Manager zasad komputera i użytkownika.  

##  <a name="BKMK_Win10Servicing"></a>Ulepszenia obsługi systemu Windows 10  
 W podglądzie techniczne 1602 dodaliśmy następujące udoskonalenia w zakresie obsługi systemu Windows 10:  

-   Nowe opcje filtrowania dla planów obsługi.  Teraz można filtrować przy użyciu **języka**, **wymagane**, i **tytuł**. Tylko uaktualnienia zgodne z określonymi kryteriami zostaną dodane do skojarzonego wdrożenia.  

-   Po wybraniu **uaktualnień** synchronizacji aktualizacji klasyfikacji dla oprogramowania, okno dialogowe Ostrzeżenie jest wyświetlany z informacją tego WSUS [poprawkę 3095113](https://support.microsoft.com/kb/3095113) jest wymagane do pomyślnej synchronizacji aktualizacji oprogramowania i obsługi systemu Windows 10 do poprawnego działania.  W oknie dialogowym możesz uzyskać w artykule bazy wiedzy knowledge base, poprawki.  

-   Dostępne systemu Windows 10 teraz uaktualnia tylko do wyświetlania w **obsługi systemu Windows 10** \ **wszystkie aktualizacje składników systemu Windows 10** węzeł konsoli programu Configuration Manager. Aktualizacje te nie są już wyświetlane w **aktualizacji oprogramowania** \ **wszystkie aktualizacje oprogramowania** węzła.  

-   Okno dialogowe umożliwiającą wiedzieć, że ich zaktualizuje ich system operacyjny, zostanie wyświetlony monit użytkowników końcowych, które zaczynają pakiet uaktualnienia systemu Windows 10.  

