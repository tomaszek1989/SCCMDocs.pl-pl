---
title: "Wybierz autonomicznej usługi Intune lub hybrydowego zarządzania urządzeniami Przenośnymi | Dokumentacja firmy Microsoft"
description: "Określ, czy wdrożenia hybrydowego zarządzania urządzeniami przenośnymi z usługą Intune i programu Configuration Manager lub uruchomić autonomiczną usługę Intune."
ms.custom: na
ms.date: 07/18/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 73ff9bb9-e605-4b68-92a1-487684fed42d
caps.latest.revision: "10"
author: dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: 5c9e80fc5bc3f0629e1c27a4928b8a51cfe1ee7e
ms.sourcegitcommit: 948644072bd158b156f782a4376bcd50fac7c73a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2017
---
# <a name="choose-between-microsoft-intune-standalone-and-hybrid-mobile-device-management-with-system-center-configuration-manager"></a>Wybór między Microsoft Intune autonomiczne, jak i hybrydowe zarządzanie urządzeniami przenośnymi z System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Jednym z najbardziej często zadawane pytania dotyczące zarządzania urządzeniami przenośnymi (MDM) w usłudze Microsoft Intune jest "Powinien I integracji usługi Intune z programem Configuration Manager (hybrydowego zarządzania urządzeniami Przenośnymi) lub uruchomić autonomiczną usługę Intune w konfiguracji tylko w chmurze?" Odpowiedzi na to pytanie, należy ostrożnie porównać dwóch opcji.
 
## <a name="intune-standalone"></a>Autonomicznej usługi Intune.
Autonomicznej usługi Intune jest topologia wdrożenia zalecane przez firmę Microsoft. Autonomicznej usługi Intune jest tylko na chmurze rozwiązanie MDM i odbywa się przy użyciu konsoli sieci web, który można uzyskać z dowolnego miejsca na świecie. Usługi Intune w centrach danych znajdują się w Ameryce Północnej, Europie i Azji. Ponieważ usługa Intune jest usługą w chmurze, zarządzania usługi Intune można wdrożyć na urządzeniach w względnie krótkim przedziale czasu.

Klienci znaleźć zwykle szybsze i łatwiejsze do wdrożenia topologii autonomicznych, ponieważ nie istnieje żadne zależności dla składników lokalnymi. Autonomicznej usługi Intune jest teraz na platformie Microsoft Azure w chmurze i udostępnia wiele zaawansowanych funkcji, takich jak:
- Zintegrowane enterprise mobility zarządzania platformy — administrator i platformy w chmurze zintegrowane środowisko pracy w portalu Azure w przypadku usługi Intune, Azure AD Premium i Azure Information Protection.
- Zarządzanie urządzeniami przenośnymi — funkcje ochrony zarządzania i informacje o zaawansowanych urządzeń przenośnych.
- Skalowanie — wdrażanie i zarządzanie urządzeniami przenośnymi, nie martwiąc się o skali.
- Kontrola dostępu oparta na rolach — Ogranicz dostęp do funkcji administracyjnych na podstawie przypisane role i zakresy.
- Dostęp programistyczny (API) — Obsługa interfejsu API programu Microsoft Graph i opcje zarządzania zestawu SDK i programu PowerShell.
- Konsola sieci Web - konsoli opartych na języku HTML 5, oparte na standardach sieci web z obsługą najbardziej nowoczesnymi przeglądarkami sieci web.
- Zaawansowane raportowanie — możliwość tworzenia niestandardowych raportów.
- Elastyczność — Instalator proste i szybkie dostarczania nowych możliwości.


## <a name="hybrid-mdm-with-configuration-manager"></a>Hybrydowego zarządzania urządzeniami Przenośnymi w programie Configuration Manager
Hybrydowego zarządzania urządzeniami Przenośnymi to rozwiązanie, która integruje się możliwości zarządzania urządzeniami przenośnymi usługi Intune do programu Configuration Manager. Używa usługi Intune jako kanału dostarczania dla zasady, profile i aplikacji na urządzeniach, ale używa infrastruktury lokalnej programu Configuration Manager do zarządzania zawartością i zarządzania urządzeniami. Implementacja hybrydowa zapewnia kontrolę "jednego okienka awaryjne".  Oznacza to, że do zarządzania urządzeniami przenośnymi w usłudze Intune, a także komputerami i serwerami przy użyciu tradycyjnych klienta programu Configuration Manager można użyć tej samej infrastrukturze lokalnych i konsoli administracyjnej. Można wybrać hybrydowego zarządzania urządzeniami Przenośnymi z następujących powodów:  
- Chcesz zarządzać zarówno na urządzeniach przenośnych zarejestrowanych w usłudze Intune i urządzenia zarządzane za pomocą klienta programu Configuration Manager z tej samej konsoli administracyjnej
- Infrastruktura wymaga wielu serwerów usługi NDES w celu dostarczania certyfikatów na urządzeniach przenośnych
- Wymaga infrastruktury, czy masz wiele łączników programu Exchange
- Wymagana jest obsługa szyfrowania S/MIME


## <a name="changing-the-mdm-authority-setting"></a>Zmiana ustawienia urzędu zarządzania urządzeniami Przenośnymi
Jeśli musisz zmienić ustawienie urzędu zarządzania urządzeniami Przenośnymi, można zmienić go samodzielnie bez konieczności kontaktowania się Microsoft Support i bez konieczności wyrejestrowywania i Zarejestruj ponownie istniejących zarządzanych urządzeń. Aby uzyskać więcej informacji, zobacz [zmienić urzędu zarządzania urządzeniami Przenośnymi](../deploy-use/change-mdm-authority.md).

> [!NOTE]    
> Musi mieć programu Configuration Manager w wersji 1610 lub nowszej można zmienić urzędu zarządzania urządzeniami Przenośnymi na autonomicznej usługi Intune. Jeśli istnieje wcześniejszej wersji programu Configuration Manager można zmienić urząd zarządzania urządzeniami Przenośnymi, ale wymaga pomoc od operacji i pomocy technicznej firmy Microsoft. On również wymaga wyrejestrować i Zarejestruj ponownie wszystkie urządzenia, po zmianie urząd zarządzania urządzeniami Przenośnymi.  
