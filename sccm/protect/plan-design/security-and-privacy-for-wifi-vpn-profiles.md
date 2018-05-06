---
title: Profili sieci Wi-Fi i sieci VPN zabezpieczenia i prywatność
titleSuffix: Configuration Manager
description: Więcej informacji na temat zabezpieczeń najlepsze rozwiązania dotyczące zarządzania profilami sieci Wi-Fi i VPN dla urządzeń w programie System Center Configuration Manager.
ms.date: 12/28/2016
ms.prod: configuration-manager
ms.technology: configmgr-protect
ms.topic: conceptual
ms.assetid: ef3ab519-9cf7-47fc-8831-d400e0e96df8
author: aczechowski
manager: dougeby
ms.author: aaroncz
ms.openlocfilehash: 6ba2cf8139cd1a5f416ff7877afc0a6b7b1ad081
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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
