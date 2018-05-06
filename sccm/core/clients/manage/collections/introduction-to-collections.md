---
title: Wprowadzenie do kolekcji
titleSuffix: Configuration Manager
description: Wprowadzenie do przy użyciu kolekcji w programie System Center Configuration Manager.
ms.date: 01/03/2017
ms.prod: configuration-manager
ms.technology: configmgr-client
ms.topic: conceptual
ms.assetid: d17e1188-d277-438f-9236-db9cd213b421
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 48a0788d83ffcd7a373f5f73ee675b62508a6d86
ms.sourcegitcommit: 0b0c2735c4ed822731ae069b4cc1380e89e78933
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="introduction-to-collections-in-system-center-configuration-manager"></a>Wprowadzenie do kolekcji w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Kolekcje ułatwiają organizowania zasobów w jednostki zarządzane. Możesz utworzyć kolekcje w celu dostosowania potrzeb zarządzania klienta i do wykonywania operacji na wielu zasobach jednocześnie. 

Większość zadań zarządzania zależą od lub wymaga użycia co najmniej jednej kolekcji. Mimo że można użyć wbudowanej kolekcji wszystkie systemy, używa go do zadań zarządzania nie jest najlepszym rozwiązaniem. Tworzenie kolekcji niestandardowych w celu bardziej precyzyjnego identyfikowania urządzeń lub użytkowników dla tego zadania.  

 Kolekcje wbudowane i niestandardowe są wyświetlane w **kolekcje użytkowników** i **kolekcje urządzeń** węzłów w **zasoby i zgodność** obszaru roboczego w konsoli programu Configuration Manager.  

 Kolekcje ostatnio wyświetlane są wyświetlane w **użytkowników** węzeł i w **urządzeń** w węźle **zasoby i zgodność** obszaru roboczego.  

Oto kilka przykładów użycia kolekcji:  

|Operacja|Przykład|  
|---------|-------|  
|Grupowanie zasobów|Możesz utworzyć kolekcje, które zasoby grupy oparte na hierarchii organizacji.<br /><br /> Na przykład można utworzyć kolekcję zawierającą wszystkie komputery w "Centrala w Londynie" Active Directory jednostki organizacyjnej (OU). Aby uzyskać więcej informacji na temat tworzenia tego typu kolekcji, zobacz [jak tworzyć kolekcje w programie System Center Configuration Manager](../../../../core/clients/manage/collections/create-collections.md).<br /><br /> Dla operacji, takich jak konfigurowanie ustawień programu Endpoint Protection, konfigurowanie ustawień zarządzania energią urządzenia lub instalowanie klienta programu Configuration Manager, można użyć tej kolekcji.|  
|[Wdrażanie aplikacji]|Można utworzyć kolekcję zawierającą wszystkie komputery, które nie mają zainstalowany program Microsoft Office 2013, a następnie wdrożyć go na wszystkich komputerach w tej kolekcji.<br /><br /> W celu wykonania tego zadania można również użyć wymagań aplikacji. Aby uzyskać więcej informacji, zobacz [Jak tworzyć aplikacje w programie System Center Configuration Manager](../../../../apps/deploy-use/create-applications.md).|  
|[Zarządzanie ustawieniami klienta](../../../../core/clients/deploy/about-client-settings.md)|Mimo że domyślne ustawienia klienta w programie Configuration Manager mają zastosowanie do wszystkich urządzeń i wszystkich użytkowników, można tworzyć niestandardowe ustawienia klienta stosowane względem kolekcji urządzeń lub kolekcji użytkowników.<br /><br /> Na przykład zdalne sterowanie ma być dostępne na wszystkich, z wyjątkiem kilku urządzeniach należy skonfigurować ustawienia domyślne klienta Zezwól na zdalne sterowanie, a następnie skonfigurować niestandardowe ustawienia klienta, które nie zezwalaj na zdalne sterowanie i wdrożyć je na kolekcję wyjątkowych klientów. |  
|[Zarządzanie energią](../power/introduction-to-power-management.md)|Można skonfigurować ustawień zasilania określonych w jednej kolekcji.|  
|[Administracja oparta na rolach](../../../../core/servers/deploy/configure/configure-role-based-administration.md)|Za pomocą kolekcji, do której grupy użytkowników mają dostęp do różnych funkcji w konsoli programu Configuration Manager kontroli.|  
|[Okna obsługi](../../../../core/clients/manage/collections/use-maintenance-windows.md)|Z okien obsługi w czasie, gdy można wykonywać różne operacje programu Configuration Manager można zdefiniować w elementach członkowskich kolekcji urządzeń. |  


## <a name="collection-types-in-configuration-manager"></a>Typy kolekcji w programie Configuration Manager  
 Programu Configuration Manager zawiera wbudowane kolekcje typowych operacji, a można też utworzyć kolekcje niestandardowe.   

### <a name="built-in-collections"></a>Wbudowane kolekcje  
 Domyślnie program Configuration Manager zawiera następujące kolekcje, które nie może być modyfikowany.  

|**Nazwa kolekcji**|Opis|  
|-------------------------|-----------------|  
|**Wszystkie grupy użytkowników**|Zawiera grupy użytkowników, które zostały wykryte za pomocą funkcji odnajdywania grup zabezpieczeń w usłudze Active Directory.|  
|**Wszyscy użytkownicy**|Zawiera użytkowników, którzy zostali wykryci za pomocą funkcji odnajdywania użytkowników w usłudze Active Directory.|  
|**Wszyscy użytkownicy i grupy użytkowników**|Zawiera kolekcje Wszyscy użytkownicy i Wszystkie grupy użytkowników. Ta kolekcja zawiera największy zakres użytkowników oraz zasobów grup użytkowników.|  
|**Wszystkie komputery stacjonarne i klienci serwera**|Zawiera urządzenia serwerowe i stacjonarne, które mają zainstalowanego klienta programu Configuration Manager. Członkostwo jest obsługiwane przez wykrywanie interwału czasowego.|  
|**Wszystkie urządzenia przenośne**|Zawiera urządzenia przenośne, które są zarządzane przez program Configuration Manager. Członkostwo jest ograniczone do tych urządzeń przenośnych, które zostały pomyślnie przypisane do lokacji lub zostały odnalezione przez łącznik serwera Exchange.|  
|**Wszystkie systemy**|Zawiera wszystkie komputery stacjonarne i klienci serwera, wszystkie urządzenia przenośne i kolekcji wszystkie nieznane komputery i wszystkie urządzenia przenośne zarejestrowane przez program Microsoft Intune. Ta kolekcja zawiera największy zakres zasobów urządzeń.|  
|**Wszystkie nieznane komputery**|Zawiera ogólne rekordy komputerów dla wielu platform komputerowych. Można użyć tej kolekcji do wdrożenia systemu operacyjnego za pomocą sekwencji zadań i rozruchu w środowisku PXE, nośnika rozruchowego lub wstępnie przygotowanego nośnika.|  

### <a name="custom-collections"></a>Kolekcje niestandardowe  
 Podczas tworzenia kolekcji niestandardowej w programie Configuration Manager członkostwo tej kolekcji jest określany przez co najmniej jedną regułę kolekcji, zgodnie z opisem w [jak tworzyć kolekcje w programie System Center Configuration Manager](../../../../core/clients/manage/collections/create-collections.md). 

