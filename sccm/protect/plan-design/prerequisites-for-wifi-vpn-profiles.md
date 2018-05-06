---
title: Wymagania wstępne dotyczące profili sieci Wi-Fi i sieci VPN
titleSuffix: Configuration Manager
description: Więcej informacji na temat uprawnień zabezpieczeń wymaganych do zarządzania profile certyfikatów, profile sieci Wi-Fi i profile sieci VPN w programie System Center Configuration Manager.
ms.date: 11/23/2016
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: d2dacb2d-ab3b-42a2-8dc8-94da31f993c2
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 894717df4b5acb7142aa7d171a8b8b63a28f8dc0
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="prerequisites-for-wi-fi-and-vpn-profiles-in-system-center-configuration-manager"></a>Wymagania wstępne dotyczące sieci Wi-Fi i profile sieci VPN w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Wi-Fi i profile sieci VPN w programie System Center Configuration Manager mają zależności tylko w obrębie produktu.  

 Wymagane są następujące uprawnienia zabezpieczeń w celu zarządzania ustawieniami dostępu do zasobów firmowych, takich jak profile certyfikatów, profile sieci Wi-Fi i profile sieci VPN:  

-   Aby wyświetlić i Zarządzanie alertami oraz raportami dla sieci Wi-Fi i profile: **Utwórz**, **usunąć**, **zmodyfikować**, **Modyfikuj raport**, **odczytu**, i **Uruchom raport** Aby uzyskać **alerty** obiektu.  

-   Aby utworzyć i zarządzać profilami certyfikatów: **Tworzenie zasad**, **modyfikowanie raportu**, **odczytu**, i **Uruchom raport** dla **profil certyfikatu** obiektu.  

-   Aby zarządzać wdrożeniami profili sieci Wi-Fi, certyfikatów i sieci VPN: **Wdrażanie zasad konfiguracji**, **Modyfikuj Alert stanu klienta**, **odczytu**, i **odczytu zasobów** dla **kolekcji**obiektu.  

-   Aby zarządzać wszystkimi zasadami konfiguracji: **Utwórz**, **usunąć**, **zmodyfikować**, **odczytu**, i **Ustaw zakres zabezpieczeń** dla **zasady konfiguracji**  obiektu.  

-   Uruchamianie zapytań dotyczących profilów sieci Wi-Fi i sieci VPN: **Odczyt** uprawnienie **zapytania** obiektu.  

-   Wyświetlanie informacji o profilach sieci Wi-Fi i sieci VPN w konsoli programu System Center Configuration Manager: **Odczyt** uprawnienie **lokacji** obiektu.  

-   Aby wyświetlić komunikaty o stanie dla profilów sieci Wi-Fi i sieci VPN: **Odczyt** uprawnienie **komunikaty o stanie** obiektu.  

-   Tworzenie i modyfikowanie profilu certyfikatu zaufanego urzędu certyfikacji: **Tworzenie zasad**, **modyfikowanie raportu**, **odczytu**, i **Uruchom raport** dla **profil zaufanego certyfikatu CA** obiektu.  

-   Aby utworzyć i zarządzać profilami sieci VPN: **Tworzenie zasad**, **modyfikowanie raportu**, **odczytu**, i **Uruchom raport** dla **profilu sieci VPN** obiektu.  

-   Aby utworzyć i zarządzać profilami sieci Wi-Fi: **Tworzenie zasad**, **modyfikowanie raportu**, **odczytu**, i **Uruchom raport** dla **profilu sieci Wi-Fi** obiektu.  

 **Menedżer dostępu do zasobów firmy** te uprawnienia, które są wymagane do zarządzania profilami sieci Wi-Fi w programie System Center Configuration Manager obejmuje rola zabezpieczeń. Aby uzyskać więcej informacji, zobacz [Konfigurowanie zabezpieczeń w programie System Center Configuration Manager](../../core/plan-design/security/configure-security.md).
