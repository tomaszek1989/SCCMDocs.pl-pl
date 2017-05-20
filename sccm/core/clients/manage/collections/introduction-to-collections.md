---
title: Wprowadzenie do kolekcji | Dokumentacja firmy Microsoft
description: "Pobierz wprowadzenie do przy użyciu kolekcji w programie System Center Configuration Manager."
ms.custom: na
ms.date: 01/03/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: d17e1188-d277-438f-9236-db9cd213b421
caps.latest.revision: 8
author: andredm7
ms.author: andredm
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9c5d1e48b76392beaf54b5377c69b648537e86f8
ms.openlocfilehash: 547d231d48ccbc8241e9f1f8f71e3750b266b73e
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="introduction-to-collections-in-system-center-configuration-manager"></a>Wprowadzenie do kolekcji w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Kolekcje ułatwiają organizowanie zasobów w jednostki zarządzane. Istnieje możliwość utworzenia kolekcji w celu dostosowania potrzeb zarządzania klienta i do wykonywania operacji na wielu zasobów w tym samym czasie. 

Większość zadań związanych z zarządzaniem zależne od lub wymaga użycia co najmniej jednej kolekcji. Mimo że można użyć wbudowanej kolekcji wszystkie systemy, używany do zadań zarządzania nie jest najlepszym rozwiązaniem. Utwórz niestandardowe kolekcji, aby dokładniej określić urządzeń lub użytkowników dla zadania.  

 Kolekcje wbudowane i niestandardowe są wyświetlane w **kolekcji użytkowników** i **kolekcji urządzeń** węzłów w **zasoby i zgodność** obszaru roboczego w konsoli programu Configuration Manager.  

 Kolekcje ostatnio wyświetlane są wyświetlane w **użytkowników** węzeł i w **urządzeń** w węźle **zasoby i zgodność** obszaru roboczego.  

Oto kilka przykładów użycia kolekcji:  

|Operacja|Przykład|  
|---------|-------|  
|Grupowanie zasobów|Istnieje możliwość utworzenia kolekcji, które grupy zasobów w oparciu o hierarchii organizacji.<br /><br /> Na przykład można utworzyć kolekcję wszystkie komputery w "Londyn centrali" Active Directory organizacji jednostki (OU). Aby uzyskać więcej informacji o sposobie tworzenia tego typu kolekcji, zobacz [tworzenie kolekcji w programie System Center Configuration Manager](../../../../core/clients/manage/collections/create-collections.md).<br /><br /> Operacje takie jak konfigurowanie ustawień ochrony punktu końcowego, konfigurowanie ustawień zarządzania energią urządzenia lub instalacji klienta programu Configuration Manager, można użyć tej kolekcji.|  
|[Wdrożenia aplikacji]|Można utworzyć kolekcję wszystkie komputery, które nie mają zainstalowany program Microsoft Office 2013 i wdrożyć go dla wszystkich komputerów w tej kolekcji.<br /><br /> W celu wykonania tego zadania można również użyć wymagań aplikacji. Aby uzyskać więcej informacji, zobacz [Jak tworzyć aplikacje w programie System Center Configuration Manager](../../../../apps/deploy-use/create-applications.md).|  
|[Zarządzanie ustawieniami klienta](../../../../core/clients/deploy/about-client-settings.md)|Mimo że domyślne ustawienia klienta w programie Configuration Manager mają zastosowanie do wszystkich urządzeń i wszystkich użytkowników, można tworzyć niestandardowe ustawienia klienta stosowane względem kolekcji urządzeń lub kolekcji użytkowników.<br /><br /> Na przykład chcąc zdalnego sterowania mają być dostępne na wszystkich, ale kilka urządzeń, należy skonfigurować domyślne ustawienia klienta, aby umożliwić zdalnego sterowania, a następnie skonfigurować niestandardowe ustawienia klienta nie zezwalaj na zdalne sterowanie i wdrażania tych wyjątkowych klientów w kolekcji. |  
|[Zarządzanie energią](../power/introduction-to-power-management.md)|Można skonfigurować ustawienia zasilania określonych w jednej kolekcji.|  
|[Administracja oparta na rolach](../../../../core/servers/deploy/configure/configure-role-based-administration.md)|Przy użyciu kolekcji do kontroli, które grupy użytkowników mają dostęp do różnych funkcji w konsoli programu Configuration Manager.|  
|[Okna obsługi](../../../../core/clients/manage/collections/use-maintenance-windows.md)|Za pomocą okna obsługi można zdefiniować w czasie, gdy różne operacje programu Configuration Manager mogą być przeprowadzane elementów członkowskich kolekcji urządzeń. |  


## <a name="collection-types-in-configuration-manager"></a>Typy kolekcji w programie Configuration Manager  
 Program Configuration Manager ma wbudowane kolekcje typowych operacji i można również utworzyć niestandardowe kolekcje.   

### <a name="built-in-collections"></a>Wbudowane kolekcje  
 Domyślnie program Configuration Manager obejmuje następujące kolekcje, które nie mogą być modyfikowane.  

|**Nazwa kolekcji**|Opis|  
|-------------------------|-----------------|  
|**Wszystkie grupy użytkowników**|Zawiera grupy użytkowników, które zostały wykryte za pomocą funkcji odnajdywania grup zabezpieczeń w usłudze Active Directory.|  
|**Wszyscy użytkownicy**|Zawiera użytkowników, którzy zostali wykryci za pomocą funkcji odnajdywania użytkowników w usłudze Active Directory.|  
|**Wszyscy użytkownicy i grupy użytkowników**|Zawiera kolekcje Wszyscy użytkownicy i Wszystkie grupy użytkowników. Ta kolekcja zawiera największy zakres użytkowników i zasoby grupy użytkowników.|  
|**Wszystkie komputery stacjonarne i klienci serwera**|Zawiera urządzeń serwera i pulpitu, które mają zainstalowanego klienta programu Configuration Manager. Członkostwo jest obsługiwane przez wykrywanie interwału czasowego.|  
|**Wszystkie urządzenia przenośne**|Zawiera urządzeń przenośnych, które są zarządzane przez program Configuration Manager. Członkostwo jest ograniczone do tych urządzeń przenośnych, które zostały pomyślnie przypisane do lokacji lub zostały odnalezione przez łącznik serwera Exchange.|  
|**Wszystkie systemy**|Zawiera wszystkie komputery stacjonarne i klienci serwera, wszystkie urządzenia przenośne i kolekcji wszystkie nieznane komputery i wszystkie urządzenia przenośne zarejestrowane przez program Microsoft Intune. Ta kolekcja zawiera największy zakres zasobów urządzenia.|  
|**Wszystkie nieznane komputery**|Zawiera ogólne rekordy komputerów dla wielu platform komputerowych. Można użyć tej kolekcji do wdrożenia systemu operacyjnego za pomocą sekwencji zadań i rozruchu w środowisku PXE, nośnika rozruchowego lub wstępnie przygotowanego nośnika.|  

### <a name="custom-collections"></a>Kolekcje niestandardowe  
 Podczas tworzenia kolekcji niestandardowych w programie Configuration Manager, członkostwo w tej kolekcji jest określana przez co najmniej jednej zasady kolekcji, zgodnie z opisem w [tworzenie kolekcji w programie System Center Configuration Manager](../../../../core/clients/manage/collections/create-collections.md). 


