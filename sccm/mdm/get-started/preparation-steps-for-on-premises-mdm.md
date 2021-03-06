---
title: 'Procedura przygotowująca '
titleSuffix: Configuration Manager
description: Przygotowanie do zarządzania urządzeniami w usłudze zarządzania urządzeniami przenośnymi lokalnymi w programie System Center Configuration Manager.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: 1ef60106-8f31-46d6-95a6-25a6495f22c7
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 711af365353d68020a7bbbef8026f452d4203ce3
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="preparation-steps-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>Czynności przygotowujące do lokalnego zarządzania urządzeniami przenośnymi w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Zarządzanie urządzeniami w usłudze System Center Configuration Manager na\-lokalnych zarządzanie urządzeniami przenośnymi wymaga infrastruktury programu Configuration Manager można skonfigurować tak, aby wymagane role systemu lokacji (punkt proxy rejestracji, punkt rejestracyjny, punkt zarządzania urządzeniami i punkt dystrybucji) można komunikują się za pośrednictwem zaufanego kanału z urządzeniami przenośnymi, które mają być zarządzane.  

 Następujące zadania wysokiego poziomu są wymagane w celu przygotowania systemu programu Configuration Manager na\-lokalnych zarządzanie urządzeniami przenośnymi:  

-   [Skonfiguruj subskrypcję Microsoft Intune do zarządzania urządzeniami przenośnymi lokalnymi w programie System Center Configuration Manager](../../mdm/get-started/set-up-intune-subscription-on-premises-mdm.md)  

     W tym zadaniu Zarejestruj się w usłudze Microsoft Intune, a następnie dodać subskrypcję do programu Configuration Manager za pośrednictwem konsoli programu Configuration Manager. Ten krok jest wymagany tylko do celów licencjonowania. Usługa Intune nie jest używana do zarządzania urządzeniami ani do przechowywania informacji o zarządzaniu. Wszystkie koordynacji i zarządzanie urządzeniami jest organizacja użytkownika przy użyciu lokalnej infrastruktury programu Configuration Manager.  

-   [Instalowanie ról systemu lokacji do zarządzania urządzeniami przenośnymi lokalnymi w programie System Center Configuration Manager](../../mdm/get-started/install-site-system-roles-for-on-premises-mdm.md)  

     W tym zadaniu zainstalowaniem i skonfigurowaniem ról systemu lokacji, które są wymagane do zarządzania urządzeniami przy użyciu lokalnej infrastruktury programu Configuration Manager. Na\-lokalne zarządzanie urządzeniami przenośnymi wymaga co najmniej punkt proxy rejestracji, punkt rejestracyjny, punkt zarządzania urządzeniami i dystrybucji rolami systemu lokacji punktu.  

-   [Konfigurowanie certyfikatów dla zaufanej komunikacji na potrzeby zarządzania urządzeniami przenośnymi lokalnymi w programie System Center Configuration Manager](../../mdm/get-started/set-up-certificates-on-premises-mdm.md)  

     To zadanie służy do konfigurowania infrastruktury programu Configuration Manager lokalnego, aby umożliwić zaufaną komunikację (HTTPS) między zarządzanymi urządzeniami a serwerami hostującymi wymagane role systemu lokacji.  

-   [Konfigurowanie rejestracji urządzeń do zarządzania urządzeniami przenośnymi lokalnymi w programie System Center Configuration Manager](../../mdm/get-started/set-up-device-enrollment-on-premises-mdm.md)  

     W tym zadaniu nadajesz użytkownikom uprawnienie do rejestrowania komputerów i urządzeń, a następnie instalujesz zaufany certyfikat główny na urządzeniach (zwykle tych, które nie są przyłączone do domeny), aby umożliwić połączenia HTTPS z serwerami systemu lokacji.  
