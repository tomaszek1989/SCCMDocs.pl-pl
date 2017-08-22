---
title: "Wymagania wstępne dotyczące profili sieci Wi-Fi i sieci VPN | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat uprawnień zabezpieczeń wymaganych do zarządzania profile certyfikatów, profile sieci Wi-Fi i profile sieci VPN w programie System Center Configuration Manager."
ms.custom: na
ms.date: 11/23/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: d2dacb2d-ab3b-42a2-8dc8-94da31f993c2
caps.latest.revision: "5"
caps.handback.revision: "0"
author: Nbigman
ms.author: nbigman
manager: angrobe
ms.openlocfilehash: 309b0363f9b3ec4a31b8323b9e64c9f73060c281
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="prerequisites-for-wi-fi-and-vpn-profiles-in-system-center-configuration-manager"></a>Wymagania wstępne dotyczące sieci Wi-Fi i profile sieci VPN w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Wi-Fi i profile sieci VPN w programie System Center Configuration Manager mają zależności tylko w obrębie produktu.  

 Wymagane są następujące uprawnienia zabezpieczeń w celu zarządzania ustawieniami dostępu do zasobów firmowych, takich jak profile certyfikatów, profile sieci Wi-Fi i profile sieci VPN:  

-   Aby wyświetlić i Zarządzanie alertami oraz raportami dla sieci Wi-Fi i profile: **Utwórz**, **usunąć**, **Modyfikuj**, **modyfikowanie raportu**, **odczytu**, i **Uruchom raport** dla **alerty** obiektu.  

-   Aby utworzyć i zarządzać profilami certyfikatów: **Tworzenie zasad**, **modyfikowanie raportu**, **odczytu**, i **Uruchom raport** dla **profil certyfikatu** obiektu.  

-   Aby zarządzać wdrożeniami profili sieci Wi-Fi, certyfikatów i sieci VPN: **Wdrażanie zasad konfiguracji**, **modyfikowanie alertu stanu klienta**, **odczytu**, i **Odczytaj zasób** dla **kolekcji** obiektu.  

-   Aby zarządzać wszystkimi zasadami konfiguracji: **Utwórz**, **usunąć**, **Modyfikuj**, **odczytu**, i **Ustawianie zakresu zabezpieczeń** dla **zasady konfiguracji** obiektu.  

-   Uruchamianie zapytań dotyczących profilów sieci Wi-Fi i sieci VPN: **Odczyt** uprawnienie **zapytania** obiektu.  

-   Wyświetlanie informacji o profilach sieci Wi-Fi i sieci VPN w konsoli programu System Center Configuration Manager: **Odczyt** uprawnienie **lokacji** obiektu.  

-   Aby wyświetlić komunikaty o stanie dla profilów sieci Wi-Fi i sieci VPN: **Odczyt** uprawnienie **komunikaty o stanie** obiektu.  

-   Tworzenie i modyfikowanie profilu certyfikatu zaufanego urzędu certyfikacji: **Tworzenie zasad**, **modyfikowanie raportu**, **odczytu**, i **Uruchom raport** dla **profil zaufanego certyfikatu CA** obiektu.  

-   Aby utworzyć i zarządzać profilami sieci VPN: **Tworzenie zasad**, **modyfikowanie raportu**, **odczytu**, i **Uruchom raport** dla **profilu sieci VPN** obiektu.  

-   Aby utworzyć i zarządzać profilami sieci Wi-Fi: **Tworzenie zasad**, **modyfikowanie raportu**, **odczytu**, i **Uruchom raport** dla **profilu sieci Wi-Fi** obiektu.  

 **Menedżer dostępu do zasobów firmy** te uprawnienia, które są wymagane do zarządzania profilami sieci Wi-Fi w programie System Center Configuration Manager obejmuje rola zabezpieczeń. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zabezpieczeń w programie System Center Configuration Manager](../../core/plan-design/security/configure-security.md).
