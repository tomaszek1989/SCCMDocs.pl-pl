---
title: 'Rejestruj urządzenia '
titleSuffix: Configuration Manager
description: Więcej informacji na temat metody do rejestrowania urządzeń na potrzeby zarządzania urządzeniami przenośnymi lokalnymi w programie System Center Configuration Manager.
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.technology: configmgr-hybrid
ms.topic: conceptual
ms.assetid: b58472e3-31a5-4305-8eb6-2522befebe02
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 7e3254fdad766260e3e162378894526e9b4a7249
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
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
