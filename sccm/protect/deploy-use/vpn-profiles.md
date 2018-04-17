---
title: Profile sieci VPN
titleSuffix: Configuration Manager
description: Dowiedz się, jak profile sieci VPN w programie System Center Configuration Manager umożliwiają wdrażanie ustawień sieci VPN dla użytkowników w organizacji.
ms.custom: na
ms.date: 04/10/2018
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
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: d30e7cc834f1693f2cbcf2db840d650421062a19
ms.sourcegitcommit: fb84bcb31d825f454785e3d9d8be669e00fe2b27
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="vpn-profiles-in-system-center-configuration-manager"></a>Profile sieci VPN w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

<!--1283610-->
Aby wdrożyć ustawienia sieci VPN dla użytkowników w organizacji, profile sieci VPN w programie Configuration Manager. Przez wdrożenie tych ustawień można maksymalnie ułatwić użytkownikom końcowym nawiązywanie połączeń z zasobami w sieci firmowej.  

 Na przykład chcesz skonfigurować wszystkie urządzenia z systemem Windows 10 przy użyciu ustawień wymaganych do połączenia z udziałem plików w sieci firmowej. Można utworzyć profil sieci VPN przy użyciu ustawień potrzebnych do połączenia z siecią firmową. Następnie można wdrożyć ten profil dla wszystkich użytkowników, którzy mają urządzenia z systemem Windows 10. Ci użytkownicy widzieli połączenie VPN na liście dostępnych sieci i można się połączyć przy minimalnym nakładzie pracy.  

 Podczas tworzenia profilu sieci VPN, można dołączyć szeroki zakres ustawień zabezpieczeń. Te ustawienia obejmują certyfikaty do weryfikacji serwera i uwierzytelnianie klienta, który można udostępnić przy użyciu profilów certyfikatów programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [profile certyfikatów](introduction-to-certificate-profiles.md).  

> [!Note]  
> Ta funkcja opcjonalna nie włączyć domyślne programu Configuration Manager. Należy włączyć tę funkcję, przed jego użyciem. Aby uzyskać więcej informacji, zobacz [Włącz funkcje opcjonalne aktualizacji](/sccm/core/servers/manage/install-in-console-updates#bkmk_options).<!--505213-->  


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
