---
title: Funkcje w wersji zapoznawczej Technical Preview 1602 programu Configuration Manager
description: "Dowiedz się więcej o funkcjach dostępnych w wersji zapoznawczej Technical Preview programu System Center Configuration Manager, wersji 1602."
ms.custom: na
ms.date: 01/23/2017
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 1b9265d1-b461-47f8-b7ef-885da0fdd969
caps.latest.revision: "6"
author: Brenduns
ms.author: brenduns
manager: angrobe
robots: noindex,nofollow
ms.openlocfilehash: 2354f885aaf69683004ad78f0e1978e78fee9145
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="capabilities-in-technical-preview-1602-for-system-center-configuration-manager"></a>Funkcje w wersji Technical Preview 1602 programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (wersja zapoznawcza Technical Preview)*

W tym artykule przedstawiono funkcje, które są dostępne w wersji Technical Preview programu System Center Configuration Manager, wersji 1602. Można zainstalować tę wersję, aby zaktualizować i dodać nowe funkcje do lokacji programu Configuration Manager technical preview. Przed zainstalowaniem tej wersji technical Preview, przejrzyj temat wprowadzający [Technical Preview programu System Center Configuration Manager](../../core/get-started/technical-preview.md), aby zapoznać się z ogólne wymagania i ograniczenia dotyczące używania wersji technical preview, jak zaktualizować między wersjami i sposobu wyrazić swoją opinię na temat funkcji w wersji technical preview.  

 Poniżej przedstawiono nowe funkcje, które można wypróbować z tą wersją.  

##  <a name="BKMK_MDM"></a>Ulepszenia zarządzania urządzeniami przenośnymi  

### <a name="ios-activation-lock"></a>Blokady aktywacji systemu iOS  
 Program System Center Configuration Manager ułatwia zarządzanie blokadą aktywacji systemu iOS — funkcją aplikacji Znajdź mój iPhone dla urządzeń z systemem iOS 7.1 lub nowszym. Blokada aktywacji jest włączana automatycznie w przypadku użycia aplikacji Znajdź mój iPhone na urządzeniu. Jeśli ta funkcja została włączona, należy podać identyfikator Apple ID i hasło użytkownika, aby można było wykonać następujące czynności:  

-   Wyłączenie aplikacji Znajdź mój iPhone  

-   Wymazanie urządzenia  

-   Ponowne uaktywnienie urządzenia  

 Menedżer konfiguracji może wysłać żądanie stanu blokady aktywacji na nadzorowanych i nienadzorowanych urządzeniach z systemem iOS 7.1 lub nowszy. W przypadku urządzeń nadzorowanych usługa Intune może pobrać kod obejścia blokady aktywacji i wystawić go bezpośrednio na urządzeniu.  

 Aby uzyskać więcej informacji, zobacz [Łatwiejsza ochrona urządzeń z blokady aktywacji obejścia dla programu Configuration Manager dla systemu iOS](/sccm/mdm/deploy-use/manage-ios-activation-lock)  

##  <a name="BKMK_SC1601"></a>Ulepszenia Centrum oprogramowania w wersji 1602  

### <a name="refresh-pc-machine-and-user-policy-from-software-center"></a>Odświeżanie zasad użytkownika i komputera PC z Centrum oprogramowania  
 Nowa opcja **zasady synchronizacji** został dodany do **opcje** > **Konserwacja komputera** w Centrum oprogramowania, który powoduje odświeżenie jej programu Configuration Manager na komputerze zasad użytkownika i komputera.  

##  <a name="BKMK_Win10Servicing"></a>Ulepszenia obsługi systemu Windows 10  
 W wersji zapoznawczej Technical Preview 1602 dodaliśmy następujące ulepszenia obsługi systemu Windows 10:  

-   Nowe opcje filtrowania planów obsługi.  Obecnie można filtrować przy **języka**, **wymagane**, i **tytuł**. Tylko uaktualnienia zgodne z określonymi kryteriami zostaną dodane do skojarzonego wdrożenia.  

-   Po wybraniu **uaktualnień** synchronizacji aktualizacji oprogramowania klasyfikacji, wyświetlone okno dialogowe ostrzeżenia z informacją tego WSUS [poprawkę 3095113](https://support.microsoft.com/kb/3095113) jest wymagane do pomyślnej synchronizacji aktualizacji oprogramowania i obsługi systemu Windows 10 działała poprawnie.  W oknie dialogowym można przejść do artykułu bazy wiedzy dotyczącego poprawki.  

-   10 systemu Windows dostępne uaktualnienia są teraz wyświetlane tylko w **obsługi systemu Windows 10** \ **wszystkie aktualizacje systemu Windows 10** węzła konsoli programu Configuration Manager. Te aktualizacje nie są już wyświetlane w **aktualizacji oprogramowania** \ **wszystkie aktualizacje oprogramowania** węzła.  

-   Użytkownicy końcowi, którzy uruchomić pakiet uaktualnienia systemu Windows 10, zostanie wyświetlony monit z okna dialogowego, które umożliwia go poinformować, że będą uaktualniać ich systemu operacyjnego.  
