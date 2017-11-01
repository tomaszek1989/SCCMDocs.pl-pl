---
title: "Rejestruj urządzenia "
titleSuffix: Configuration Manager
description: "Więcej informacji na temat metody do rejestrowania urządzeń na potrzeby zarządzania urządzeniami przenośnymi lokalnymi w programie System Center Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: b58472e3-31a5-4305-8eb6-2522befebe02
caps.latest.revision: "6"
author: dougeby
ms.author: dougeby
manager: angrobe
ms.openlocfilehash: aa1f085689f2d7d752f2887f9cbac5b8f642785e
ms.sourcegitcommit: c236214b2fcc13dae7bad96d7fb33f692868191d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2017
---
# <a name="enroll-devices-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>Rejestrowanie urządzeń do lokalnego zarządzania urządzeniami przenośnymi w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Do zarządzania komputerami i urządzeniami w usłudze System Center Configuration Manager na — lokalne zarządzanie urządzeniami przenośnymi, należy zarejestrować dzięki programowi Configuration Manager może komunikować się z urządzeniami dla zadań zarządzania urządzeniami. Configuration Manager udostępnia dwie metody rejestrowania urządzeń:  

-   **Rejestracja przez użytkownika** — w przypadku tej metody użytkownicy inicjują proces rejestracji na swoich urządzeniach. Aby rejestracja przez użytkownika do pomyślnego urządzenie musi mieć zaufanego certyfikatu głównego na nim zainstalowany, a użytkownika należy udostępnić rejestracji przez program Configuration Manager.  Aby zarejestrować urządzenie, użytkownik musi tylko podać poświadczenia służbowe, a urządzenie zostanie zarejestrowane na potrzeby zarządzania.  

     Aby uzyskać więcej informacji, zobacz [jak użytkownicy rejestrują urządzenia z zarządzania urządzeniami przenośnymi lokalnymi w programie System Center Configuration Manager](../../mdm/deploy-use/user-enroll-devices-on-premises-mdm.md)  

-   **Rejestracja zbiorcza** — w przypadku tej metody użytkownik urządzenia nie musi inicjować rejestracji. Zamiast tego pakiet rejestracji zbiorczej utworzony w programie Configuration Manager jest umieszczany na urządzeniu i otwierany. Otwarty pakiet zawiera informacje wymagane do zarejestrowania urządzenia.  

     Aby uzyskać więcej informacji, zobacz [jak rejestrować zbiorczo urządzenia za pomocą funkcji zarządzania urządzeniami przenośnymi lokalnymi w programie System Center Configuration Manager](../../mdm/deploy-use/bulk-enroll-devices-on-premises-mdm.md)  

 > [!NOTE]  
>  Bieżąca gałąź programu Configuration Manager obsługuje rejestrację w lokalnego zarządzania urządzeniami przenośnymi dla urządzeń z systemem następujących systemach operacyjnych:  
>   
>  -   Windows 10 Enterprise  
> -   Windows 10 Pro  
> -   Zespół ds. systemu Windows 10 
> -   Windows 10 Mobile  
> -   Windows 10 Mobile Enterprise   
