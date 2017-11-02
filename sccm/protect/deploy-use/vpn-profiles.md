---
title: Profile sieci VPN
titleSuffix: Configuration Manager
description: "Dowiedz się, jak profile sieci VPN w programie System Center Configuration Manager umożliwiają wdrażanie ustawień sieci VPN dla użytkowników w organizacji."
ms.custom: na
ms.date: 11/27/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c0f094f1-852e-4606-91db-97846d8f0772
caps.latest.revision: "6"
caps.handback.revision: "0"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 02d9178dbfe8cb00d38367d0dfcb2f521d4c26a0
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="vpn-profiles-in-system-center-configuration-manager"></a>Profile sieci VPN w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


Profile sieci VPN w System Center Configuration Manager (znanej także jako programu ConfigMgr lub SCCM) umożliwiają wdrażanie ustawień sieci VPN dla użytkowników w organizacji. Przez wdrożenie tych ustawień można maksymalnie ułatwić użytkownikom końcowym nawiązywanie połączeń z zasobami w sieci firmowej.  

 Na przykład chcesz udostępnić wszystkie urządzenia z systemem Windows RT systemu operacyjnego przy użyciu ustawień wymaganych do łączenia z udziałem plików w sieci firmowej. Można utworzyć profil sieci VPN zawierający ustawienia wymagane do połączenia z siecią firmową, a następnie wdrożyć ten profil dla wszystkich użytkowników, którzy mają urządzenia z systemem Windows RT w hierarchii. Użytkownicy urządzeń z systemem Windows RT widzieli połączenie VPN na liście dostępnych sieci i można połączyć z tą siecią przy minimalnym wysiłku.  

 Podczas tworzenia profilu sieci VPN, można dołączyć szeroki zakres ustawień zabezpieczeń, takich jak certyfikaty do weryfikacji serwera i uwierzytelnianie klienta, które zostały udostępnione przy użyciu profilów certyfikatów w programie System Center Configuration Manager. Aby uzyskać więcej informacji na temat profilów certyfikatów zobacz [Profile certyfikatów w programie System Center Configuration Manager](introduction-to-certificate-profiles.md).  

 W poniższych rozdziałach opisano urządzeń, jakie można skonfigurować przy użyciu profilów sieci VPN, jeśli używasz programu Configuration Manager.

 Zobacz [profilów sieci VPN na urządzeniach przenośnych](/sccm/mdm/deploy-use/create-vpn-profiles) do przegląd urządzeń można skonfigurować przy użyciu programu Configuration Manager w usłudze Microsoft Intune.  

## <a name="vpn-profiles-when-using-configuration-manager"></a>Profile sieci VPN w przypadku korzystania z programu Configuration Manager  
 W poniższej tabeli opisano profilów sieci VPN, które można skonfigurować dla różnych platform urządzeń.  

|Typ połączenia|Windows 8.1|Windows RT|Windows RT 8.1|Windows 10|  
|---------------------|-----------------|----------------|--------------------|----------------|  
|**Cisco AnyConnect**|Nie|Nie|Nie|Nie|  
|**Pulse Secure**|Tak|Nie|Tak|Tak|  
|**F5 Edge Client**|Tak|Nie|Tak|Tak|  
|**Dell SonicWALL Mobile Connect**|Tak|Nie|Tak|Tak|  
|**Sprawdź punktu Mobile VPN**|Tak|Nie|Tak|Tak|  
|**Microsoft SSL (SSTP)**|Tak|Tak|Tak|Nie|  
|**Tryb automatyczny firmy Microsoft**|Tak|Tak|Tak|Nie|  
|**Protokół IKEv2**|Tak|Tak|Tak|Nie|  
|**PPTP**|Tak|Tak|Tak|Nie|  
|**L2TP**|Tak|Tak|Tak|Nie|  

### <a name="next-steps"></a>Następne kroki  
 Użyj następujących tematach ułatwiają planowanie, konfigurowanie, obsługę i konserwację profili sieci VPN w programie Configuration Manager.  

-   [Wymagania wstępne dotyczące profilów sieci VPN w programie System Center Configuration Manager](../plan-design/prerequisites-for-wifi-vpn-profiles.md)  

-   [Zabezpieczenia i prywatność profilów sieci VPN w programie System Center Configuration Manager](../plan-design/security-and-privacy-for-wifi-vpn-profiles.md)
