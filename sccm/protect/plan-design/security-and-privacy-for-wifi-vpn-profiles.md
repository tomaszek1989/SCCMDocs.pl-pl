---
title: "Profili sieci Wi-Fi i sieci VPN bezpieczeństwo i prywatność | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat zabezpieczenia najlepszych rozwiązań do zarządzania profilami sieci Wi-Fi i sieci VPN urządzeń w programie System Center Configuration Manager."
ms.custom: na
ms.date: 12/28/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ef3ab519-9cf7-47fc-8831-d400e0e96df8
caps.latest.revision: 4
caps.handback.revision: 0
author: Nbigman
ms.author: nbigman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 8a5dc7361da34f3e6b926acd35c72c0c0767ce70
ms.openlocfilehash: 6d1d0a393a2ce614ae5f819475bd47b05e699b45
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="security-and-privacy-for-wi-fi-and-vpn-profiles-in-system-center-configuration-manager"></a>Bezpieczeństwo i prywatność profili sieci Wi-Fi i sieci VPN w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

##  <a name="security-best-practices-for-wi-fi--and-vpn-profiles"></a>Najlepsze rozwiązania dotyczące sieci Wi-Fi i profile sieci VPN  
 Podczas zarządzania profilów sieci Wi-Fi i sieci VPN dla urządzeń, należy stosować poniższe najlepsze rozwiązania.  

|Najlepsze rozwiązanie w zakresie zabezpieczeń|Więcej informacji|  
|----------------------------|----------------------|  
|Jeśli to możliwe, należy wybrać najbardziej bezpieczne opcje obsługiwane w sieci Wi-Fi i VPN infrastruktury i systemy operacyjne klientów.|Profile sieci VPN i Wi-Fi Podaj to wygodna metoda centralnej dystrybucji i zarządzania ustawieniami sieci Wi-Fi i sieci VPN, które obsługiwanych już przez urządzenia. Menedżer konfiguracji nie można dodać funkcji obsługi sieci VPN lub sieci Wi-Fi.<br /><br /> Należy określić, wdrożyć i stosować wszelkie najlepsze rozwiązania dotyczące bezpieczeństwa zalecone dla używanych urządzeń i infrastruktury.|  

## <a name="privacy-information-for-wi-fi-profiles"></a>Informacje dotyczące poufności dla profili sieci Wi-Fi  
 Profile sieci Wi-Fi i sieci VPN umożliwiają skonfigurowanie urządzeń klienckich w celu połączenia z sieci Wi-Fi i serwery sieci VPN, a następnie ocenę, czy te urządzenia będą zgodne po zastosowaniu profili. Punkt zarządzania wysyła informacje o zgodności do serwera lokacji i są one przechowywane w bazie danych lokacji. Informacje są szyfrowane, gdy urządzenia wysyłają je do punktu zarządzania. Nie są one jednak przechowywane w zaszyfrowanej postaci w bazie danych lokacji. Baza danych zachowuje te informacje do momentu usunięcia ich przez zadanie obsługi lokacji **Usuń przestarzałe dane zarządzania konfiguracją** . Domyślny interwał usuwania wynosi 90 dni, ale można go zmienić. Informacje o zgodności nie są wysyłane do firmy Microsoft.  

 Domyślnie urządzenia nie oceniają profili sieci VPN i Wi-Fi. Ponadto należy skonfigurować profile, a następnie wdrożyć dla użytkowników.  

 Przed rozpoczęciem konfigurowania sieci Wi-Fi i profile sieci VPN, należy wziąć pod uwagę wymagania dotyczące ochrony prywatności.  

