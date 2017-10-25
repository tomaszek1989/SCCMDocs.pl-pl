---
title: "Profili sieci Wi-Fi i sieci VPN zabezpieczenia i prywatność | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat zabezpieczeń najlepsze rozwiązania dotyczące zarządzania profilami sieci Wi-Fi i VPN dla urządzeń w programie System Center Configuration Manager."
ms.custom: na
ms.date: 12/28/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: ef3ab519-9cf7-47fc-8831-d400e0e96df8
caps.latest.revision: "4"
caps.handback.revision: "0"
author: Nbigman
ms.author: nbigman
manager: angrobe
ms.openlocfilehash: 6d1d0a393a2ce614ae5f819475bd47b05e699b45
ms.sourcegitcommit: 51fc48fb023f1e8d995c6c4eacfda7dbec4d0b2f
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/07/2017
---
# <a name="security-and-privacy-for-wi-fi-and-vpn-profiles-in-system-center-configuration-manager"></a>Bezpieczeństwo i prywatność profilów sieci Wi-Fi i sieci VPN w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

##  <a name="security-best-practices-for-wi-fi--and-vpn-profiles"></a>Najlepsze rozwiązania dotyczące sieci Wi-Fi i profile sieci VPN  
 Użyj następujących rozwiązań zabezpieczeń podczas zarządzania profilami sieci Wi-Fi i VPN dla urządzeń.  

|Najlepsze rozwiązanie w zakresie zabezpieczeń|Więcej informacji|  
|----------------------------|----------------------|  
|Jeśli to możliwe, należy wybrać najbardziej bezpieczne opcje obsługiwane w sieci Wi-Fi i VPN infrastruktury i systemy operacyjne klientów.|Wi-Fi i profile sieci VPN zapewniają to wygodna metoda centralnej dystrybucji i zarządzania ustawieniami sieci Wi-Fi i sieci VPN, które obsługiwanych już przez urządzenia. Menedżer konfiguracji nie dodaje sieci Wi-Fi lub VPN funkcji.<br /><br /> Należy określić, wdrożyć i stosować wszelkie najlepsze rozwiązania dotyczące bezpieczeństwa zalecone dla używanych urządzeń i infrastruktury.|  

## <a name="privacy-information-for-wi-fi-profiles"></a>Informacje dotyczące poufności dla profili sieci Wi-Fi  
 Profile sieci Wi-Fi i VPN można użyć do konfigurowania urządzeń klienckich do nawiązania połączenia sieci Wi-Fi i serwery sieci VPN, a następnie ocenę, czy te urządzenia będą zgodne po zastosowaniu profili. Punkt zarządzania wysyła informacje o zgodności do serwera lokacji i są one przechowywane w bazie danych lokacji. Informacje są szyfrowane, gdy urządzenia wysyłają je do punktu zarządzania. Nie są one jednak przechowywane w zaszyfrowanej postaci w bazie danych lokacji. Baza danych zachowuje te informacje do momentu usunięcia ich przez zadanie obsługi lokacji **Usuń przestarzałe dane zarządzania konfiguracją** . Domyślny interwał usuwania wynosi 90 dni, ale można go zmienić. Informacje o zgodności nie są wysyłane do firmy Microsoft.  

 Domyślnie urządzenia nie oceniają Wi-Fi i profile sieci VPN. Ponadto należy skonfigurować profile i wdrażać je dla użytkowników.  

 Aby skonfigurować sieci Wi-Fi lub profilów sieci VPN, należy wziąć pod uwagę wymagania dotyczące ochrony prywatności.  
