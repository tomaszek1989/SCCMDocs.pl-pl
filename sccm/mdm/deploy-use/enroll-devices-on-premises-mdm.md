---

title: "Rejestrowanie urządzeń | Dokumentacja firmy Microsoft"
description: "Więcej informacji na temat metody do rejestrowania urządzeń do zarządzania urządzeniami przenośnymi lokalnie w programie System Center Configuration Manager."
ms.custom: na
ms.date: 03/05/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-hybrid
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: b58472e3-31a5-4305-8eb6-2522befebe02
caps.latest.revision: 6
author: Mtillman
ms.author: mtillman
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3b1451edaed69a972551bd060293839aa11ec8b2
ms.openlocfilehash: 4abaef35969ef1a5340ae8ca8aa5699cd3942642
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="enroll-devices-for-on-premises-mobile-device-management-in-system-center-configuration-manager"></a>Rejestrowanie urządzeń do lokalnego zarządzania urządzeniami przenośnymi w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Aby zarządzać komputerami i urządzeniami w usłudze zarządzania urządzeniami przenośnymi lokalnego Menedżera konfiguracji centrum systemu, urządzenia muszą być zarejestrowane, tak że program Configuration Manager może komunikować się z urządzenia do zadań zarządzania. Program Configuration Manager udostępnia dwie metody rejestrowania urządzeń:  

-   **Rejestracja przez użytkownika** — w przypadku tej metody użytkownicy inicjują proces rejestracji na swoich urządzeniach. Do rejestracji użytkownika zakończyły się powodzeniem urządzenie musi mieć zaufany certyfikat główny na nim zainstalowany, a użytkownik musi być obsługiwana dla rejestracji przez program Configuration Manager.  Aby zarejestrować urządzenie, użytkownik musi tylko podać poświadczenia służbowe, a urządzenie zostanie zarejestrowane na potrzeby zarządzania.  

     Aby uzyskać więcej informacji, zobacz [jak użytkownicy rejestrują urządzenia z lokalnego zarządzania urządzeniami przenośnymi w programie System Center Configuration Manager](../../mdm/deploy-use/user-enroll-devices-on-premises-mdm.md)  

-   **Rejestracja zbiorcza** — w przypadku tej metody użytkownik urządzenia nie musi inicjować rejestracji. Zamiast tego pakiet rejestracji zbiorczej utworzone w programie Configuration Manager i jest następnie umieścić na urządzeniu i otworzyć. Otwarty pakiet zawiera informacje wymagane do zarejestrowania urządzenia.  

     Aby uzyskać więcej informacji, zobacz [sposób zbiorczego rejestrowania urządzeń za zarządzanie urządzeniami przenośnymi lokalnie w programie System Center Configuration Manager](../../mdm/deploy-use/bulk-enroll-devices-on-premises-mdm.md)  

 > [!NOTE]  
>  Bieżącej gałęzi programu Configuration Manager obsługuje rejestracji w zarządzanie urządzeniami przenośnymi lokalnie na urządzeniach z systemem w następujących systemach operacyjnych:  
>   
>  -   Windows 10 Enterprise  
> -   Windows 10 Pro  
> -   Zespół ds. systemu Windows 10 
> -   Windows 10 Mobile  
> -   Windows 10 Mobile Enterprise   

