---
title: "Migrowanie hybrydowego zarządzania urządzeniami Przenośnymi użytkowników i urządzeń do autonomicznej usługi Intune."
titleSuffix: Configuration Manager
description: "Dowiedz się, jak przeprowadzić migrację hybrydowego zarządzania urządzeniami Przenośnymi użytkowników i urządzeń do usługi Intune na platformie Azure."
keywords: 
author: dougeby
manager: angrobe
ms.date: 09/12/2017
ms.topic: article
ms.prod: configmgr-hybrid
ms.service: 
ms.technology: 
ms.assetid: 1dd696ce-3e46-4dfa-a76d-592fe0f0320e
ms.openlocfilehash: a6e430248fdeedd310087c9a32c6d69ca1864a09
ms.sourcegitcommit: 986fc2d54f7c5fa965fd4df42f4db4ecce6b79cb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2017
---
# <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone"></a>Migrowanie hybrydowego zarządzania urządzeniami Przenośnymi użytkowników i urządzeń do autonomicznej usługi Intune.

*Dotyczy: Program System Center Configuration Manager (Current Branch)*    

Jeśli zdecydujesz się, że wszystko będzie gotowe rozpocząć migrację z hybrydowego zarządzania urządzeniami Przenośnymi (usługą Intune zintegrowaną z programem Configuration Manager) do obsługi tylko w chmurze na platformie Azure przy użyciu usługi Intune, to tego artykułu jest dla Ciebie. Jeśli nadal nie masz, zobacz [wybór między Microsoft Intune autonomiczne, jak i hybrydowe zarządzanie urządzeniami przenośnymi z System Center Configuration Manager](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management). 

Można uruchomić migracji do autonomicznej usługi Intune przy użyciu podejście etapowe, który umożliwia przetestowanie mały podzbiór użytkowników i urządzeń, podczas gdy większość użytkowników i urządzeń są nadal zarządzane przy użyciu hybrydowego zarządzania urządzeniami przenośnymi. Następnie po sprawdzeniu funkcji usługi Intune, można uruchomić Migrowanie więcej użytkowników do usługi Intune.    

Poniższe tematy zawierają opis etapów migrować użytkowników do autonomicznej usługi Intune przy użyciu podejście etapowe.    
  
1.  [Importuj dane programu Configuration Manager w usłudze Microsoft Intune](migrate-import-data.md)   
    Narzędzie odbierający dane Intune zbiera dane dotyczące obiekty, które należy wybrać z hierarchii programu Configuration Manager, zawiera szczegółowe informacje dotyczące obiektów, które można wybrać dla importu i dowiedzieć się, dlaczego nie można zaimportować niektórych obiektów i umożliwia zaimportowanego wybrane obiekty w dzierżawcy usługi Microsoft Intune. Gdy ten krok jest opcjonalny, informacjom mnóstwo czasu dzięki automatyzacji procesu, aby odtworzyć obiektów z programu Configuration Manager do usługi Intune. 
2.  [Przygotowanie usługi Intune dla użytkowników](migrate-prepare-intune.md)    
    Sprawdzanie poprawności importowanych obiektów z programu Configuration Manager, tworzyć nowe obiekty, tworzenie grup w usłudze AAD i tworzenia przypisań obiektu do tych grup, zainstaluj łączniki usługi NDES i Exchange itd. Po ukończeniu czynności i rozpocząć migrację do autonomicznej usługi Intune, należy go niewidoczny dla użytkowników.  
3.  [Zmienić urząd zarządzania urządzeniami Przenośnymi dla określonych użytkowników (mieszane urzędu zarządzania urządzeniami Przenośnymi)](migrate-mixed-authority.md)    
    Mieszane urzędu zarządzania urządzeniami Przenośnymi można skonfigurować w ramach tej samej dzierżawy, wybierając niektórzy użytkownicy mają być zarządzane w usłudze Intune i inne urządzenia, nadal można zarządzać za pomocą hybrydowego zarządzania urządzeniami Przenośnymi (usługą Intune zintegrowaną z programem Configuration Manager). Można sprawdzić, czy funkcji usługi Intune działa zgodnie z oczekiwaniami na urządzeniach do małego podzbioru użytkowników przed rozpoczęciem migracji dodatkowych użytkowników. 
4.  [Zmień urzędu zarządzania urządzeniami Przenośnymi autonomicznej usługi Intune.](change-mdm-authority.md)     
    Zmienić urzędu zarządzania urządzeniami Przenośnymi na poziomie dzierżawy z programu Configuration Manager do usługi Intune. Wszystkich pozostałych użytkowników i urządzeń są migrowane do autonomicznej usługi Intune. Po przetestowano funkcji usługi Intune w poprzednim kroku i prawdopodobnie zostały zmigrowane większości lub wszystkich użytkowników już zmieni się urzędu zarządzania urządzeniami Przenośnymi na poziomie dzierżawy.

<!--
The following provides a typical workflow for migrating users from hybrid MDM to Intune standalone:
1.  Admin runs the Microsoft Intune Data Importer Tool, selecting which objects and assignments to import. Selected objects are imported into Intune standalone.
    1. Some objects cannot be imported because they contain settings the tool does not understand or setting that are not available in Intune standalone.
    2. Assignments are migrated. However, only if the collection an object was targeted to is based on a single Active Directory (AD) security group and the same group exists in Azure Active Directory (AAD).
    > [!Note]    
    > If you want, you can skip this step and create the objects that you want directly in Intune in the Azure portal without running the Intune Data Importer Tool. 
2.  Admin logs into the Intune on Azure portal
    1. Creates any additional objects required for their organization that were not imported by the Microsoft Intune Data Importer tool.
    2. Creates any required AAD groups and makes any additional assignments for each object to AAD groups.
    3. Installs the NDES connector on an on-premises server if using SCEP or PFX certificate deployment.
    4. Installs the Exchange connector on an on-premises server if using conditional access. 
3.  Admin ensures that all existing Intune users in their organization have an Intune license assigned to them using AAD or the Office administrator portal.
4.  Admin selects some test users to migrate to Intune standalone and removes them from the collection associated with the Intune subscription in Configuration Manager.
5.  Once removed from the collection, the user and all devices are managed by Intune in the Azure portal. Remaining users and devices continue to be managed by hybrid mobile device management in Configuration Manager. 
6.  Admin validates that things are working as expected on the device and moves more users to Intune standalone by removing them from the collection associated with the Intune subscription in Configuration Manager.
7.  Once the admin is comfortable with the functionality in Intune standalone, they can move the rest of their users and devices by switching their MDM authority to Intune standalone. This can be done by removing the Intune subscription from SCCM and choosing to change the MDM authority. Tenant level policies will be automatically migrated to Intune standalone, all objects and assignments in Intune standalone will remain, and devices will not be required to re-enroll.
-->