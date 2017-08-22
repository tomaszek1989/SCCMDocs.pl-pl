---
title: "Zapewnianie zgodności urządzeń | Dokumentacja firmy Microsoft"
description: "Zarządzanie konfiguracją i zgodnością urządzeń w Twojej organizacji za pomocą programu System Center Configuration Manager."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.technology: configmgr-other
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 7568c9aa-b99e-4466-bfc8-0301aa376930
caps.latest.revision: "8"
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.openlocfilehash: f7ecfe550d2e28579ea873442b2a68dc1c7c5483
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="ensure-device-compliance-with-system-center-configuration-manager"></a>Zapewnianie zgodności urządzeń za pomocą programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Ustawienia zgodności w programie System Center Configuration Manager udostępnia narzędzia i zasoby wymagane do zarządzania konfiguracją i zgodnością urządzeń w Twojej organizacji. Ułatwia to spełnianie następujących wymagań biznesowych:  

-   Porównywanie konfiguracji zarządzanych komputerów z systemem Windows, komputerów Mac, serwerów i urządzeń przenośnych z konfiguracjami z zastosowaniem najlepszych rozwiązań utworzonych lub uzyskanych od innych dostawców  

-   Identyfikowanie nieupoważnionych konfiguracji urządzeń  

-   Raportowanie zgodności z zasadami wynikającymi z wymogów prawnych i zasadami zabezpieczeń wewnętrznych  

-   Identyfikowanie luk w zabezpieczeniach  

-   Przekazywanie pomocy technicznej informacji umożliwiających wykrywanie potencjalnych przyczyn zgłoszonych zdarzeń i problemów dzięki identyfikacji niezgodnych konfiguracji  

-   Automatyczne korygowanie niektórych niezgodnych ustawień na urządzeniach przenośnych  

-   Korygowanie niezgodności przez wdrażanie aplikacji, pakietów i programów lub skryptów do kolekcji, która jest automatycznie wypełniane przy użyciu urządzeń, które zgłosiły informacja o braku zgodności  


## <a name="get-started"></a>Wprowadzenie  
 Poznaj podstawowe informacje o ustawieniach zgodności i zadaniach, które można wykonać przy ich użyciu.  

 [Wprowadzenie do ustawień zgodności](../../compliance/get-started/get-started-with-compliance-settings.md)  

## <a name="plan-and-design"></a>Planowanie i projektowanie  
 Przed rozpoczęciem pracy z ustawieniami zgodności upewnij się, że zastosowano wymagania wstępne opisane w tym temacie.  

 [Planowanie i konfigurowanie ustawień zgodności](../../compliance/plan-design/plan-for-and-configure-compliance-settings.md)  

## <a name="common-tasks"></a>Wspólne zadania  
 W tej sekcji znajdują się, że niektórych typowych scenariuszy, które pomogą Ci poznać, aby używać ustawień zgodności w programie Configuration Manager.  

 [Typowe zadania zarządzania zgodnością](../../compliance/plan-design/common-tasks-for-managing-compliance.md)  

## <a name="remote-connection-profiles"></a>Profile połączenia zdalnego  
 Ten typ elementu konfiguracji umożliwia skonfigurowanie komputerów użytkowników do zdalnego łączenia się z komputerami służbowymi, gdy użytkownicy nie są połączeni z domeną lub jeśli ich komputery osobiste łączą się przez Internet.  

 [Tworzenie profilów połączenia zdalnego](/sccm/compliance/deploy-use/create-remote-connection-profiles)  

## <a name="user-data-and-profiles"></a>Profile i dane użytkownika  
 Ten typ elementu konfiguracji zawiera ustawienia umożliwiające użytkownikom w hierarchii zarządzanie przekierowaniem folderu, plikami trybu offline i profilami mobilnymi na komputerach z systemem Windows 8 i nowszymi.  

 [Tworzenie elementów konfiguracji danych i profilów użytkownika](/sccm/compliance/deploy-use/create-user-data-and-profiles-configuration-items)  

## <a name="windows-edition-upgrade-policy"></a>Zasady uaktualniania wydania systemu Windows  
 Zasady uaktualniania wersji umożliwiają automatyczne uaktualnianie urządzeń z systemem Windows 10 do nowszej wersji. Można określić klucz produktu do uaktualnienia stacjonarnych wersji systemu Windows 10 lub plik licencji umożliwiający uaktualnienie urządzeń z systemem Windows 10 Mobile i Windows 10 Holographic.  

 [Uaktualnianie urządzeń z systemem Windows za pomocą zasad uaktualniania wersji](/sccm/compliance/deploy-use/upgrade-windows-version)  
