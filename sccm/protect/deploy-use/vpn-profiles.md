---
title: Profile sieci VPN w programie System Center Configuration Manager | Dokumentacja firmy Microsoft
description: "Dowiedz się, jak profile sieci VPN w programie System Center Configuration Manager umożliwiają wdrażanie ustawień sieci VPN dla użytkowników w organizacji."
ms.custom: na
ms.date: 11/27/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c0f094f1-852e-4606-91db-97846d8f0772
caps.latest.revision: 6
caps.handback.revision: 0
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 199096db7a23fb14db98b95e75246ed254848ab7
ms.openlocfilehash: e07a80c1a59043b74cda7219f78c5fef66989ba8
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="vpn-profiles-in-system-center-configuration-manager"></a>Profile sieci VPN w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


Profile sieci VPN w programie System Center Configuration Manager (znanej także jako programu ConfigMgr lub SCCM) umożliwia wdrażanie ustawień sieci VPN dla użytkowników w organizacji. Przez wdrożenie tych ustawień można maksymalnie ułatwić użytkownikom końcowym nawiązywanie połączeń z zasobami w sieci firmowej.  

 Na przykład użytkownik chce udostępnić wszystkie urządzenia z systemem Windows RT systemu operacyjnego za pomocą ustawienia wymagane do połączenia z udziałem plików w sieci firmowej. Można utworzyć profil sieci VPN zawierający ustawienia wymagane do nawiązania połączenia z siecią firmową, a następnie wdrożyć ten profil dla wszystkich użytkowników, którzy mają urządzenia z systemem Windows RT w hierarchii. Użytkownicy urządzeń z systemem Windows RT Zobacz połączenia sieci VPN na liście dostępnych sieci i można połączyć z tą siecią przy minimalnym wysiłku.  

 Podczas tworzenia profilu sieci VPN można zastosować wiele różnych ustawień zabezpieczeń, takich jak certyfikaty do weryfikacji serwera i uwierzytelnianie klienta, które zostały udostępnione przy użyciu profili certyfikatów programu System Center Configuration Manager. Aby uzyskać więcej informacji na temat profilów certyfikatów zobacz [Profile certyfikatów w programie System Center Configuration Manager](introduction-to-certificate-profiles.md).  

 W poniższych sekcjach opisano urządzeń, jakie można skonfigurować za pomocą profili sieci VPN, jeśli używasz programu Configuration Manager.

 Zobacz [profile sieci VPN na urządzeniach przenośnych](/sccm/mdm/deploy-use/create-vpn-profiles) do przeglądania urządzenia można skonfigurować przy użyciu programu Configuration Manager w usłudze Microsoft Intune.  

## <a name="vpn-profiles-when-using-configuration-manager"></a>Profile sieci VPN przy użyciu programu Configuration Manager  
 W poniższej tabeli opisano profile sieci VPN, które można skonfigurować dla różnych platform urządzeń.  

|Typ połączenia|Windows 8.1|Windows RT|Windows RT 8.1|Windows 10|  
|---------------------|-----------------|----------------|--------------------|----------------|  
|**Cisco AnyConnect**|Nie|Nie|Nie|Nie|  
|**Bezpieczne Puls**|Tak|Nie|Tak|Tak|  
|**F5 Edge Client**|Tak|Nie|Tak|Tak|  
|**Dell SonicWALL Mobile Connect**|Tak|Nie|Tak|Tak|  
|**Sprawdź sieć Mobile VPN punktu**|Tak|Nie|Tak|Tak|  
|**Microsoft SSL (SSTP)**|Tak|Tak|Tak|Nie|  
|**Tryb automatyczny firmy Microsoft**|Tak|Tak|Tak|Nie|  
|**Protokół IKEv2**|Tak|Tak|Tak|Nie|  
|**PPTP**|Tak|Tak|Tak|Nie|  
|**L2TP**|Tak|Tak|Tak|Nie|  

### <a name="next-steps"></a>Następne kroki  
 Użyj następujących tematach ułatwiają planowanie, konfigurowanie, obsługę i konserwację profili sieci VPN w programie Configuration Manager.  

-   [Wymagania wstępne dotyczące profili sieci VPN w programie System Center Configuration Manager](../plan-design/prerequisites-for-wifi-vpn-profiles.md)  

-   [Bezpieczeństwo i prywatność profili sieci VPN w programie System Center Configuration Manager](../plan-design/security-and-privacy-for-wifi-vpn-profiles.md)

