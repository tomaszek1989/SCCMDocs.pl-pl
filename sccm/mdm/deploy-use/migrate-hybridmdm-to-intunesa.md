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
ms.openlocfilehash: 30474f6dd0216078ab1ac1f4bd9f5044f1b174f0
ms.sourcegitcommit: 8c6e9355846ff6a73c534c079e3cdae09cf13c45
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/06/2017
---
# <a name="migrate-hybrid-mdm-users-and-devices-to-intune-standalone"></a>Migrowanie hybrydowego zarządzania urządzeniami Przenośnymi użytkowników i urządzeń do autonomicznej usługi Intune.

*Dotyczy: Program System Center Configuration Manager (Current Branch)*    

Jeśli zdecydujesz się, że wszystko będzie gotowe rozpocząć migrację z hybrydowego zarządzania urządzeniami Przenośnymi (usługą Intune zintegrowaną z programem Configuration Manager) do obsługi tylko w chmurze na platformie Azure przy użyciu usługi Intune, to tego artykułu jest dla Ciebie. Jeśli nadal nie masz, zobacz [wybór między Microsoft Intune autonomiczne, jak i hybrydowe zarządzanie urządzeniami przenośnymi z System Center Configuration Manager](https://docs.microsoft.com/sccm/mdm/understand/choose-between-standalone-intune-and-hybrid-mobile-device-management). 

Można uruchomić migracji do autonomicznej usługi Intune przy użyciu podejście etapowe, który umożliwia przetestowanie mały podzbiór użytkowników i urządzeń, podczas gdy większość użytkowników i urządzeń są nadal zarządzane przy użyciu hybrydowego zarządzania urządzeniami przenośnymi. Następnie po sprawdzeniu funkcji usługi Intune, można uruchomić Migrowanie więcej użytkowników do usługi Intune.    

Poniższe tematy zawierają opis etapów migrować użytkowników do autonomicznej usługi Intune przy użyciu podejście etapowe.    
  
1.  [Importuj dane programu Configuration Manager w usłudze Microsoft Intune](migrate-import-data.md)   
    Narzędzie odbierający dane Intune zbiera dane dotyczące obiekty, które należy wybrać z hierarchii programu Configuration Manager, zawiera szczegółowe informacje dotyczące obiektów, które można wybrać dla importu i dowiedzieć się, dlaczego nie można zaimportować niektórych obiektów i umożliwia zaimportowanego wybrane obiekty w dzierżawcy usługi Microsoft Intune. Gdy ten krok jest opcjonalny, go można zaoszczędzić dużo czasu dzięki automatyzacji procesu, aby odtworzyć obiektów z programu Configuration Manager do usługi Intune. 
2.  [Przygotowanie usługi Intune dla użytkowników](migrate-prepare-intune.md)    
    Sprawdzanie poprawności importowanych obiektów z programu Configuration Manager, tworzyć nowe obiekty, tworzenie grup w usłudze AAD i tworzenia przypisań obiektu do tych grup, zainstaluj łączniki usługi NDES i Exchange itd. Po ukończeniu czynności i rozpocząć migrację do autonomicznej usługi Intune, należy go niewidoczny dla użytkowników.  
3.  [Zmienić urząd zarządzania urządzeniami Przenośnymi dla określonych użytkowników (mieszane urzędu zarządzania urządzeniami Przenośnymi)](migrate-mixed-authority.md)    
    Mieszane urzędu zarządzania urządzeniami Przenośnymi można skonfigurować w ramach tej samej dzierżawy, wybierając niektórzy użytkownicy mają być zarządzane w usłudze Intune i inne urządzenia, nadal można zarządzać za pomocą hybrydowego zarządzania urządzeniami Przenośnymi (usługą Intune zintegrowaną z programem Configuration Manager). Można sprawdzić, czy funkcji usługi Intune działa zgodnie z oczekiwaniami na urządzeniach do małego podzbioru użytkowników przed rozpoczęciem migracji dodatkowych użytkowników. 
4.  [Zmień urzędu zarządzania urządzeniami Przenośnymi autonomicznej usługi Intune.](change-mdm-authority.md)     
    Zmienić urzędu zarządzania urządzeniami Przenośnymi na poziomie dzierżawy z programu Configuration Manager do usługi Intune. Wszystkich pozostałych użytkowników i urządzeń są migrowane do autonomicznej usługi Intune. Po przetestowano funkcji usługi Intune w poprzednim kroku i prawdopodobnie zostały zmigrowane większości lub wszystkich użytkowników już zmieni się urzędu zarządzania urządzeniami Przenośnymi na poziomie dzierżawy.