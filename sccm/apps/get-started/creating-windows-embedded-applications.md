---
title: Tworzenie aplikacji Windows Embedded | Dokumentacja firmy Microsoft
description: "Zobacz uwagi, które należy wziąć pod uwagę podczas tworzenia i wdrażania aplikacji na urządzeniach Windows Embedded."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-app
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 16acfd63-0c40-424c-82f4-8c63f7f1c30b
caps.latest.revision: 7
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 557888d1f1f899e3198c430bbe5ccdd44178f824
ms.openlocfilehash: cb0c22f3060ba654778dca958d620f1e1725b93c
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="create-windows-embedded-applications-with-system-center-configuration-manager"></a>Tworzenie aplikacji Windows Embedded z System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Oprócz innych wymagania programu System Center Configuration Manager i procedury dotyczące tworzenia aplikacji należy również wykonać pod uwagę następujące kwestie podczas tworzenia i wdrażania aplikacji na urządzeniach Windows Embedded.  

## <a name="general-considerations"></a>Zagadnienia ogólne  

-   Podczas wdrażania aplikacji na urządzeniach Windows Embedded, które są włączone do filtrowania zapisu, można określić, czy wyłączyć filtr zapisu na urządzeniu podczas wdrażania aplikacji. Następnie można ponownie uruchomić filtr zapisu po wdrożeniu aplikacji. Jeśli filtr zapisu nie zostanie wyłączony, oprogramowanie zostanie wdrożone w tymczasowej nakładce. Oznacza to, że jeśli inne wdrożenie nie wymusi utrwalenia zmian, oprogramowanie zostanie nie zostanie zainstalowane po ponownym uruchomieniu urządzenia.  

-   Po wdrożeniu aplikacji do urządzenia z systemem Windows Embedded upewnij się, że urządzenie należy do kolekcji ze skonfigurowanym oknem obsługi. Pozwoli to zarządzać czasem włączania i wyłączania filtru zapisu oraz czasem ponownego uruchomienia urządzenia.  

-   Ustawienia kontrolujące zachowanie filtra zapisu ma postać pola wyboru o nazwie **Zatwierdź zmiany po upływie terminu wdrożenia lub w oknie obsługi (wymaga ponownego uruchomienia)**.  

## <a name="tips-for-deploying-applications"></a>Wskazówki dotyczące wdrażania aplikacji  

**Używaj wymaganych aplikacji, a nie aplikacji dostępnych dla urządzeń Windows Embedded, które mają włączone filtry zapisu.** Ponieważ użytkownicy nie mogą instalować aplikacje z Centrum oprogramowania na urządzeniu z systemem Windows Embedded, które ma włączone filtry zapisu, zawsze należy wdrażać aplikacji z celem wdrożenia **wymagane** zamiast **dostępne** na tych urządzeniach. Zazwyczaj nie jest to problem, ponieważ komputery z systemem systemu operacyjnego Windows Embedded często jest wykonywana pojedyncza aplikacja, która musi działać w taki sam sposób dla wielu użytkowników. Z tego powodu takie urządzenia są ściśle zarządzane, a dostęp do nich jest blokowany przez działy IT. Do tej sytuacji bardzo dobrze pasują aplikacje wymagane.

 Jeśli jednak użytkownicy uruchamiają więcej niż jedną aplikację na urządzeniach z systemem osadzonym przy włączonych filtrach zapisu, należy ich poinformować o następujących ograniczeniach:  

-   Użytkownicy nie mogą instalować wymaganego oprogramowania z programu Software Center.  

-   Użytkownicy nie mogą zmieniać godzin roboczych na karcie Opcje Centrum oprogramowania.  

-   Użytkownicy nie mogą odkładać instalacji wymaganych aplikacji.  

Dodatkowo użytkownicy z niskim poziomem uprawnień nie można zalogować w okresie konserwacji Jeśli zatwierdza zmiany w instalacjach i aktualizacjach oprogramowania Configuration Manager. W tym czasie użytkownikom jest wyświetlany komunikat z informacją, że urządzenie jest niedostępne z powodu trwającej obsługi.  

**Nie należy wdrażać aplikacji dla systemu Windows Embedded urządzeń, które mają włączone, jeśli aplikacje wymagają od użytkownika akceptacji postanowień licencyjnych filtry zapisu.** Podczas zapisu filtry są wyłączone, tak że program Configuration Manager można zainstalować oprogramowania na urządzenia osadzone, użytkownicy z niskimi uprawnieniami nie mogą logować się do urządzenia. Jeśli instalacja wymaga od użytkownika akceptacji postanowień licencyjnych, nie będzie to możliwe i instalacja się nie powiedzie. Upewnij się, że nie wdrażasz oprogramowania na urządzeniach Windows Embedded, jeśli instalacja wymaga interakcji użytkownika. Do odfiltrowania takich systemów operacyjnych można użyć listy Odpowiednie platformy.  

