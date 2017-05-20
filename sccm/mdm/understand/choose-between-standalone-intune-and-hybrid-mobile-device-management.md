---
title: Wybierz Intune autonomiczny lub hybrydowe MDM | Dokumentacja firmy Microsoft
description: "Określ, czy wdrożyć hybrydowe zarządzanie urządzeniami przenośnymi za pomocą usługi Intune i program Configuration Manager lub uruchomić autonomicznej usługi Intune."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 73ff9bb9-e605-4b68-92a1-487684fed42d
caps.latest.revision: 10
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 2c723fe7137a95df271c3612c88805efd8fb9a77
ms.openlocfilehash: cbdcf686b9565c56c7a6fca6086d94d9e45f641a
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="choose-between-microsoft-intune-standalone-and-hybrid-mobile-device-management-with-system-center-configuration-manager"></a>Wybierz między Microsoft Intune autonomiczne, jak i hybrydowe zarządzanie urządzeniami przenośnymi za pomocą System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Jednym z najbardziej często zadawane pytania dotyczące zarządzania urządzeniami przenośnymi (MDM) w usłudze Microsoft Intune jest "Powinien I integracji usługi Intune z programem Configuration Manager (hybrydowy MDM) lub uruchom autonomiczna usługa Intune w konfiguracji tylko chmury?" Odpowiedzi na to pytanie, należy uważnie porównać dwie opcje i wziąć pod uwagę aktualizacji przychodzących na wczesnym 2017 autonomicznej usługi Intune.

## <a name="what-is-intune-standalone"></a>Co to jest autonomiczna usługa Intune?

Autonomiczna usługa Intune jest tylko na chmurze rozwiązanie MDM, które obejmuje żadnych zasobów lokalnych i odbywa się przy użyciu konsoli sieci web, który można uzyskać dostęp z dowolnego miejsca na świecie. Intune centrów danych znajdują się w Ameryce Północnej, Europie i Azji. Ponieważ Intune to usługa w chmurze, można wdrożyć Intune zarządzania urządzeniami w stosunkowo krótkim przedziale czasu. Autonomiczna usługa Intune może także wybrać, jeśli Twoja organizacja jest przenoszenie do chmury.

## <a name="what-is-hybrid-mdm-with-configuration-manager"></a>Co to jest hybrydowego zarządzania urządzeniami Przenośnymi za pomocą programu Configuration Manager?

Hybrydowe MDM to rozwiązanie, które używa usługi Intune jako kanał dostarczania dla zasad, profile i aplikacji dla urządzeń, ale używa infrastruktury lokalnej programu Configuration Manager do przechowywania i administrowanie zawartości i zarządzanie tymi urządzeniami. Możesz hybrydowe MDM, jeśli już masz znaczących inwestycji w programie Configuration Manager i rozszerzyć ją do zarządzania urządzeniami przenośnymi. Wdrożenia hybrydowego zapewnia kontrolę "jednego okienka szkła", co oznacza, że można użyć tej samej infrastruktury lokalnej i konsoli administracyjnej do zarządzania urządzeniami przenośnymi za pomocą usługi Intune, a także komputerami i serwerami przy użyciu tradycyjnych klienta programu Configuration Manager.

## <a name="whats-coming-to-intune-standalone-in-early-2017"></a>Wkrótce do autonomicznej usługi Intune w 2017 wczesne

Jeśli wybierzesz między autonomiczne, jak i hybrydowych, należy wziąć pod uwagę funkcje, które pochodzą z autonomicznej usługi Intune w wczesne 2017. Obecnie hybrydowe MDM ma kilka zaawansowanych funkcji, które zostały wcześniej Dlaczego niektórzy klienci wybierz do zarządzania urządzeniami z hybrydowego MDM zamiast autonomiczna usługa Intune:

-   Dostęp programistyczny (API) — opcje zarządzania SDK i środowiska PowerShell.

-   Niestandardowe raporty — Tworzenie niestandardowych raportów.

-   Kontrola dostępu oparta na rolach — ograniczenie dostępu do funkcji administracyjnych na podstawie przypisanych ról.

-   Skalowanie — wdrażanie i zarządzanie urządzeniami przenośnymi ponad 100 000.

-   Jednego okienka szkła — Zarządzanie tradycyjnych klientów PC i urządzenia zarządzane przez usługę Intune przy użyciu tej samej konsoli.

Jeśli są od początku do planowania wdrożenia usługi Intune już dziś i ma kilka miesięcy okna dla piloting, przyjęcia testowania i wdrażania, warto rozważyć wybór autonomiczna usługa Intune teraz przy założeniu, że aktualizacje pochodzące z usługi w chmurze zawierają więcej funkcji. W pierwszej połowie roku kalendarzowym 2017 autonomiczna usługa Intune otrzymają aktualizacje, które zawierają wiele zaawansowanych funkcji wdrożenia hybrydowego z programu Configuration Manager. Autonomiczna usługa Intune wkrótce będzie można przenoszenie do chmury platformy Microsoft Azure i z jego ma rozszerzoną skalowalności, oparty na roli dostęp za pośrednictwem portalu Azure, raportów niestandardowych i programowy dostęp za pośrednictwem interfejsu API programu Graph Azure.

Można przełączyć z hybrydowego do autonomicznej usługi Intune lub autonomicznego do hybrydowych, ale wymaga pomocy od pomocy technicznej firmy Microsoft i operacji. Wymaga to również anulowania rejestracji i ponownej rejestracji wszystkich urządzeń, po zmianie urzędu zarządzania.  Firma Microsoft pracuje nad poprawy obsługi przełączania konfiguracji w przyszłych aktualizacji.

