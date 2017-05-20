---
title: Kroki przygotowania | Dokumentacja firmy Microsoft
description: "Przygotowanie do zarządzania urządzeniami przy użyciu lokalnego zarządzania urządzeniami przenośnymi w programie System Center Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 1ef60106-8f31-46d6-95a6-25a6495f22c7
caps.latest.revision: 4
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 6424fb07802b62820b4dc78a58ab30d3b956abef
ms.openlocfilehash: 85bdadaaaeed9a42cfa5165d2b9f0f3ef434dc03
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="preparation-steps-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>Czynności przygotowujące do lokalnego zarządzania urządzeniami przenośnymi w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Zarządzanie urządzeniami za pomocą System Center Configuration Manager na\-lokalnych zarządzanie urządzeniami przenośnymi wymaga infrastruktury programu Configuration Manager można skonfigurować tak, aby role systemu lokacji wymagane (punkt proxy rejestracji, punkt rejestracji, punkt zarządzania urządzeniami i punkt dystrybucji) można komunikują się za pośrednictwem kanału zaufany z urządzeniami przenośnymi, które mają być zarządzane.  

 Następujące zadania wysokiego poziomu są wymagane do przygotowania systemu programu Configuration Manager na\-lokalnych zarządzanie urządzeniami przenośnymi:  

-   [Konfigurowanie subskrypcji usługi Microsoft Intune dla lokalnego zarządzania urządzeniami przenośnymi w programie System Center Configuration Manager](../../mdm/get-started/set-up-intune-subscription-on-premises-mdm.md)  

     To zadanie Zarejestruj się w usłudze Microsoft Intune, a następnie Dodaj subskrypcję programu Configuration Manager za pomocą konsoli programu Configuration Manager. Ten krok jest wymagany tylko do celów licencjonowania. Intune nie jest używany do zarządzania urządzeniami lub przechowywanie informacji zarządzania. Wszystkie koordynacji i zarządzanie urządzeniami jest z organizacji przedsiębiorstwa przy użyciu lokalnej infrastruktury programu Configuration Manager.  

-   [Instalowanie ról systemu lokacji dla zarządzania urządzeniami przenośnymi lokalnie w programie System Center Configuration Manager](../../mdm/get-started/install-site-system-roles-for-on-premises-mdm.md)  

     To zadanie należy zainstalować i skonfigurować role systemu lokacji, które są wymagane do zarządzania urządzeniami z infrastruktury lokalnej programu Configuration Manager. Na\-lokalnego zarządzania urządzeniami przenośnymi wymaga co najmniej punkt proxy rejestracji, punkt rejestracji, punkt zarządzania urządzeniami i dystrybucji rolami systemu lokacji punktu.  

-   [Konfigurowanie certyfikatów zaufanych komunikacji dla lokalnego zarządzania urządzeniami przenośnymi w programie System Center Configuration Manager](../../mdm/get-started/set-up-certificates-on-premises-mdm.md)  

     To zadanie należy skonfigurować infrastrukturę programu Configuration Manager lokalną, aby umożliwić komunikację zaufanych (HTTPS) między zarządzanymi urządzeniami i serwerów obsługujących role systemu lokacji wymagane.  

-   [Konfigurowanie rejestracji urządzeń do zarządzania urządzeniami przenośnymi lokalnie w programie System Center Configuration Manager](../../mdm/get-started/set-up-device-enrollment-on-premises-mdm.md)  

     W tym zadaniu nadajesz użytkownikom uprawnienie do rejestrowania komputerów i urządzeń, a następnie instalujesz zaufany certyfikat główny na urządzeniach (zwykle tych, które nie są przyłączone do domeny), aby umożliwić połączenia HTTPS z serwerami systemu lokacji.  

