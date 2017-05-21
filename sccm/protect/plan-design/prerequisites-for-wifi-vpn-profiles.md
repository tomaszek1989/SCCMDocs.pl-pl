---
title: "Wymagania wstępne dotyczące profili sieci Wi-Fi i sieci VPN | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat uprawnień zabezpieczeń wymaganych do zarządzania profile certyfikatów, profile sieci Wi-Fi i profile sieci VPN w programie System Center Configuration Manager."
ms.custom: na
ms.date: 11/23/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: d2dacb2d-ab3b-42a2-8dc8-94da31f993c2
caps.latest.revision: 5
caps.handback.revision: 0
author: Nbigman
ms.author: nbigman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 31b68ede677df8b86412a334d1d100041a0e659e
ms.openlocfilehash: 309b0363f9b3ec4a31b8323b9e64c9f73060c281
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="prerequisites-for-wi-fi-and-vpn-profiles-in-system-center-configuration-manager"></a>Wymagania wstępne dotyczące sieci Wi-Fi i profile sieci VPN w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Wi-Fi i profile sieci VPN w programie System Center Configuration Manager mają zależności tylko w obrębie produktu.  

 Wymagane są następujące uprawnienia zabezpieczeń w celu zarządzania ustawieniami dostępu do zasobów firmowych, takich jak profile certyfikatów, profile sieci Wi-Fi i profile sieci VPN:  

-   Aby wyświetlić i Zarządzanie alertami oraz raportami sieci Wi-Fi i profile: **Tworzenie**, **usunąć**, **Modyfikuj**, **modyfikowanie raportu**, **odczytu**, i **Uruchom raport** dla **alerty** obiektu.  

-   Aby utworzyć i zarządzać profilami certyfikatów: **Tworzenie zasad**, **modyfikowanie raportu**, **odczytu**, i **Uruchom raport** dla **profilu certyfikatu** obiektu.  

-   Aby zarządzać wdrożeniami profili sieci Wi-Fi, certyfikatów i sieci VPN: **Wdrażanie zasad konfiguracji**, **Modyfikuj Alert stanu klienta**, **odczytu**, i **Odczytaj zasób** dla **kolekcji** obiektu.  

-   Aby zarządzać wszystkimi zasadami konfiguracji: **Tworzenie**, **usunąć**, **Modyfikuj**, **odczytu**, i **Ustawianie zakresu zabezpieczeń** dla **zasady konfiguracji** obiektu.  

-   Aby uruchamiać kwerendy dotyczące profili sieci Wi-Fi i sieci VPN: **Odczyt** uprawnienia dla **zapytania** obiektu.  

-   Aby wyświetlić informacje o profilach sieci Wi-Fi i sieci VPN w konsoli programu System Center Configuration Manager: **Odczyt** uprawnienia dla **witryny** obiektu.  

-   Aby wyświetlać komunikaty o stanie dla profili sieci Wi-Fi i sieci VPN: **Odczyt** uprawnienia dla **komunikatów o stanie** obiektu.  

-   Aby utworzyć i modyfikować profil certyfikatu zaufanego urzędu certyfikacji: **Tworzenie zasad**, **modyfikowanie raportu**, **odczytu**, i **Uruchom raport** dla **profil zaufanego certyfikatu CA** obiektu.  

-   Aby utworzyć i zarządzać profilami sieci VPN: **Tworzenie zasad**, **modyfikowanie raportu**, **odczytu**, i **Uruchom raport** dla **profilu sieci VPN** obiektu.  

-   Aby utworzyć i zarządzać profilami sieci Wi-Fi: **Tworzenie zasad**, **modyfikowanie raportu**, **odczytu**, i **Uruchom raport** dla **profilu sieci Wi-Fi** obiektu.  

 **Menedżer dostępu do zasobów firmy** roli zabezpieczeń obejmuje uprawnienia wymagane do zarządzania profilami sieci Wi-Fi w programie System Center Configuration Manager. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zabezpieczeń w programie System Center Configuration Manager](../../core/plan-design/security/configure-security.md).

