---
title: "Obsługiwane serwery systemu lokacji"
titleSuffix: Configuration Manager
description: "Dowiedz się, które wersje systemu Windows można użyć do hostowania lokacji programu System Center Configuration Manager lub rola systemu lokacji."
ms.custom: na
ms.date: 06/27/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 17905b4c-3895-4ad4-a69c-5e0d0fc5a8c3
caps.latest.revision: "44"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: e7606e087e2540b49e8aa23c09d09831651ee48b
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2017
---
# <a name="supported-operating-systems-for-system-center-configuration-manager-site-system-servers"></a>Obsługiwane systemy operacyjne dla serwerów systemu lokacji programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


Ten artykuł zawiera szczegóły dotyczące wersji systemu Windows, które służą do hostowania lokacji programu System Center Configuration Manager lub rola systemu lokacji.


Użyj informacji przedstawionych w tym temacie w połączeniu z informacjami znajdującymi się w następujących artykułach:
-   [Zalecany sprzęt dla programu Configuration Manager](../../../core/plan-design/configs/recommended-hardware.md)
-   [Witryny i wymagania wstępne systemu lokacji programu Configuration Manager](../../../core/plan-design/configs/site-and-site-system-prerequisites.md)
-   [Numery rozmiaru i skali dla programu Configuration Manager](../../../core/plan-design/configs/size-and-scale-numbers.md)



## <a name="windows-server-2016-standard-and-datacenter"></a>Windows Server 2016: Standard i Datacenter
Począwszy od wersji 1606 z pakiet zbiorczy poprawek z KB3186654 (lub wersji linii bazowej 1606, wydanej w października 2016) to system operacyjny jest obsługiwany dla następujących elementów:

**Serwery lokacji:**  

-   Centralna lokacja administracyjna  

-   Lokacja główna  

-   Lokacja dodatkowa  

**Serwery systemu lokacji:**  

-   Punkt usługi sieci Web Wykaz aplikacji  

-   Punkt witryny sieci Web katalogu aplikacji  

-   Punkt synchronizacji analizy zasobów  

-   Punkt rejestracji certyfikatu  

-   Punkt dystrybucji  

     Punkty dystrybucji obsługują kilka różnych konfiguracji czy o różnych wymaganiach. W niektórych przypadkach te konfiguracje obsługują instalację nie tylko na serwerach, ale w systemach operacyjnych klienta. Aby uzyskać więcej informacji na temat opcji dostępnych dla punktów dystrybucji, zobacz [zarządzanie zawartością i infrastrukturą zawartości programu System Center Configuration Manager](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

-   Punkt ochrony punktu końcowego  

-   Punkt rejestracji  

-   Punkt proxy rejestracji  

-   Rezerwowy punkt stanu  

-   Punkt zarządzania

-   Punkt usług raportowania  

-   Punkt połączenia usługi  

-   Serwer bazy danych lokacji  

     Serwery bazy danych lokacji nie są obsługiwane na kontrolerze domeny tylko do odczytu (RODC). Więcej informacji znajduje się w artykule [You may encounter problems when installing SQL Server on a domain controller](http://go.microsoft.com/fwlink/p/?LinkId=264856) (W przypadku instalowania programu SQL Server w kontrolerze domeny mogą wystąpić problemy) w bazie wiedzy Microsoft Knowledge Base. Ponadto serwery lokacji dodatkowych nie są obsługiwane na żadnym kontrolerze domeny.  

-   SMS_Provider  

-   Punkt aktualizacji oprogramowania  

-   punkt migracji stanu

## <a name="windows-server-2012-r2-x64-standard-and-datacenter"></a>Windows Server 2012 R2 (x 64): Standard i Datacenter  
**Serwery lokacji:**  

-   Centralna lokacja administracyjna  

-   Lokacja główna  

-   Lokacja dodatkowa  

**Serwery systemu lokacji:**  

-   Punkt usługi sieci Web Wykaz aplikacji  

-   Punkt witryny sieci Web katalogu aplikacji  

-   Punkt synchronizacji analizy zasobów  

-   Punkt rejestracji certyfikatu  

-   Punkt dystrybucji  

     Punkty dystrybucji obsługują kilka różnych konfiguracji czy o różnych wymaganiach. W niektórych przypadkach te konfiguracje obsługują instalację nie tylko na serwerach, ale w systemach operacyjnych klienta. Aby uzyskać więcej informacji na temat opcji dostępnych dla punktów dystrybucji, zobacz [zarządzanie zawartością i infrastrukturą zawartości programu System Center Configuration Manager](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

-   Punkt ochrony punktu końcowego  

-   Punkt rejestracji  

-   Punkt proxy rejestracji  

-   Rezerwowy punkt stanu  

-   Punkt zarządzania

-   Punkt usług raportowania  

-   Punkt połączenia usługi  

-   Serwer bazy danych lokacji  

     Serwery bazy danych lokacji nie są obsługiwane na kontrolerze domeny tylko do odczytu (RODC). Więcej informacji znajduje się w artykule [You may encounter problems when installing SQL Server on a domain controller](http://go.microsoft.com/fwlink/p/?LinkId=264856) (W przypadku instalowania programu SQL Server w kontrolerze domeny mogą wystąpić problemy) w bazie wiedzy Microsoft Knowledge Base. Ponadto serwery lokacji dodatkowych nie są obsługiwane na żadnym kontrolerze domeny.  

-   SMS_Provider  

-   Punkt aktualizacji oprogramowania  

-   punkt migracji stanu  

## <a name="windows-server-2012-x64-standard-and-datacenter"></a>Windows Server 2012 (x 64): Standard i Datacenter  
**Serwery lokacji:**  

-   Centralna lokacja administracyjna  

-   Lokacja główna  

-   Lokacja dodatkowa  

**Serwery systemu lokacji:**  

-   Punkt usługi sieci Web Wykaz aplikacji  

-   Punkt witryny sieci Web katalogu aplikacji  

-   Punkt synchronizacji analizy zasobów  

-   Punkt rejestracji certyfikatu  

-   Punkt dystrybucji  

     Punkty dystrybucji obsługują kilka różnych konfiguracji czy o różnych wymaganiach. W niektórych przypadkach te konfiguracje obsługują instalację nie tylko na serwerach, ale w systemach operacyjnych klienta. Aby uzyskać więcej informacji na temat opcji dostępnych dla punktów dystrybucji, zobacz [zarządzanie zawartością i infrastrukturą zawartości programu System Center Configuration Manager](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

-   Punkt ochrony punktu końcowego  

-   Punkt rejestracji  

-   Punkt proxy rejestracji  

-   Rezerwowy punkt stanu  

-   Punkt zarządzania

-   Punkt usług raportowania  

-   Punkt połączenia usługi  

-   Serwer bazy danych lokacji  

     Serwery bazy danych lokacji nie są obsługiwane na kontrolerze domeny tylko do odczytu (RODC). Więcej informacji znajduje się w artykule [You may encounter problems when installing SQL Server on a domain controller](http://go.microsoft.com/fwlink/p/?LinkId=264856) (W przypadku instalowania programu SQL Server w kontrolerze domeny mogą wystąpić problemy) w bazie wiedzy Microsoft Knowledge Base. Ponadto serwery lokacji dodatkowych nie są obsługiwane na żadnym kontrolerze domeny.  

-   SMS_Provider  

-   Punkt aktualizacji oprogramowania  

-   punkt migracji stanu  

## <a name="windows-server-2008-r2-with-sp1-x64-standard-enterprise-and-datacenter"></a>Windows Server 2008 R2 z dodatkiem SP1 (x 64): Standard, Enterprise i Datacenter  
 Windows Server 2008 R2 jest obecnie obowiązuje wsparcie i nie jest już dostępne podstawowe wsparcie, zgodnie z opisem w [Microsoft Cykl wsparcia technicznego produktów](https://support.microsoft.com/lifecycle). Aby uzyskać więcej informacji na temat wsparcia w przyszłości dla tych systemów operacyjnych jako serwerów systemu lokacji z programem Configuration Manager, zobacz [usunięte i przestarzałe funkcje programu System Center Configuration Manager](../../../core/plan-design/changes/removed-and-deprecated-features.md).  

 Począwszy od programu Configuration Manager w wersji 1702 ten system operacyjny nie jest obsługiwany dla serwerów lokacji i większości ról systemu lokacji, ale w dalszym ciągu obsługiwany dla roli systemu lokacji punktu dystrybucji (w tym ściągające punkty dystrybucji i środowiska PXE i multiemisji).

 Wersje starsze niż 1702 w dalszym ciągu obsługuje jej użycia do wykonania poniższych czynności.


**Serwery lokacji:**  

-   Centralna lokacja administracyjna  

-   Lokacja główna  

-   Lokacja dodatkowa  

**Serwery systemu lokacji:**  

-   Punkt usługi sieci Web Wykaz aplikacji  

-   Punkt witryny sieci Web katalogu aplikacji  

-   Punkt synchronizacji analizy zasobów  

-   Punkt rejestracji certyfikatu  

-   Punkt dystrybucji  

     Punkty dystrybucji obsługują kilka różnych konfiguracji czy o różnych wymaganiach. W niektórych przypadkach te konfiguracje obsługują instalację nie tylko na serwerach, ale w systemach operacyjnych klienta. Aby uzyskać więcej informacji na temat opcji dostępnych dla punktów dystrybucji, zobacz [zarządzanie zawartością i infrastrukturą zawartości programu System Center Configuration Manager](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

-   Punkt ochrony punktu końcowego  

-   Punkt rejestracji  

-   Punkt proxy rejestracji  

-   Rezerwowy punkt stanu  

-   Punkt zarządzania

-   Punkt usług raportowania  

-   Punkt połączenia usługi  

-   Serwer bazy danych lokacji  

     Serwery bazy danych lokacji nie są obsługiwane na kontrolerze domeny tylko do odczytu (RODC). Więcej informacji znajduje się w artykule [You may encounter problems when installing SQL Server on a domain controller](http://go.microsoft.com/fwlink/p/?LinkId=264856) (W przypadku instalowania programu SQL Server w kontrolerze domeny mogą wystąpić problemy) w bazie wiedzy Microsoft Knowledge Base. Ponadto serwery lokacji dodatkowych nie są obsługiwane na żadnym kontrolerze domeny.  

-   SMS_Provider  

-   Punkt aktualizacji oprogramowania  

-   punkt migracji stanu  

## <a name="windows-server-2008-with-sp2-x86-x64-standard-enterprise-and-datacenter"></a>Windows Server 2008 z dodatkiem SP2 (x 86, x 64): Standard, Enterprise i Datacenter  
 Windows Server 2008 jest obecnie obowiązuje wsparcie i nie jest już dostępne podstawowe wsparcie, zgodnie z opisem w [Microsoft Cykl wsparcia technicznego produktów](https://support.microsoft.com/lifecycle). Aby uzyskać więcej informacji na temat wsparcia w przyszłości dla tych systemów operacyjnych jako serwerów systemu lokacji z programem Configuration Manager, zobacz [usunięte i przestarzałe funkcje programu System Center Configuration Manager](../../../core/plan-design/changes/removed-and-deprecated-features.md).  

Ten system operacyjny nie jest obsługiwany dla serwerów lokacji i ról systemu lokacji, z wyjątkiem punktu dystrybucji i punktu dystrybucji ściągania. Można nadal używać tego systemu operacyjnego jako punkt dystrybucji, do momentu ogłoszenia zaniechania tej obsługi lub zakończenia okresu rozszerzonej pomocy technicznej tego systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [instalacji programu System Center Configuration Manager CB i LTSB zakończy się niepowodzeniem w systemie Windows Server 2008](https://support.microsoft.com/help/4015095).

**Serwery systemu lokacji:**  
-   Punkt dystrybucji  

    -   Punkty dystrybucji w tym systemie operacyjnym nie obsługują multiemisji.  

    -   Punkty dystrybucji w tym systemie operacyjnym obsługują środowisko PXE, ale nie obsługują rozruchu przez sieć komputerów klienckich w trybie EFI. Obsługiwane są komputery klienckie z systemem BIOS lub z rozruchem EFI w trybie zgodności.  

    -   Punkty dystrybucji obsługują kilka różnych konfiguracji czy o różnych wymaganiach. W niektórych przypadkach te konfiguracje obsługują instalację nie tylko na serwerach, ale w systemach operacyjnych klienta. Aby uzyskać więcej informacji na temat opcji dostępnych dla punktów dystrybucji, zobacz [zarządzanie zawartością i infrastrukturą zawartości programu System Center Configuration Manager](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  



## <a name="windows-10-x86-x64-pro-and-enterprise"></a>Windows 10 (x86, x64): Pro i Enterprise  
**Serwery systemu lokacji:**  

-   Punkt dystrybucji  

    -   Punkty dystrybucji w tym systemie operacyjnym nie obsługują środowiska PXE.  

    -   Punkty dystrybucji w tym systemie operacyjnym nie obsługują multiemisji.  

    -   Punkty dystrybucji obsługują kilka różnych konfiguracji czy o różnych wymaganiach. W niektórych przypadkach te konfiguracje obsługują instalację nie tylko na serwerach, ale w systemach operacyjnych klienta. Aby uzyskać więcej informacji na temat opcji dostępnych dla punktów dystrybucji, zobacz [zarządzanie zawartością i infrastrukturą zawartości programu System Center Configuration Manager](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

## <a name="windows-81-x86-x64-professional-and-enterprise"></a>Windows 8.1 (x86, x64): Professional i Enterprise  
**Serwery systemu lokacji:**  

-   Punkt dystrybucji  

    -   Punkty dystrybucji w tym systemie operacyjnym nie obsługują środowiska PXE.  

    -   Punkty dystrybucji w tym systemie operacyjnym nie obsługują multiemisji.  

    -   Punkty dystrybucji obsługują kilka różnych konfiguracji czy o różnych wymaganiach. W niektórych przypadkach Instalacja obsługi tych konfiguracji nie tylko na serwerach, ale w systemach operacyjnych klienta. Aby uzyskać więcej informacji na temat opcji dostępnych dla punktów dystrybucji, zobacz [zarządzanie zawartością i infrastrukturą zawartości programu System Center Configuration Manager](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

## <a name="windows-8-x86-x64-professional-and-enterprise"></a>Windows 8 (x86, x64): Professional i Enterprise
**Serwery systemu lokacji:**  

-   Punkt dystrybucji  

    -   Punkty dystrybucji w tym systemie operacyjnym nie obsługują środowiska PXE.  

    -   Punkty dystrybucji w tym systemie operacyjnym nie obsługują multiemisji.  

    -   Punkty dystrybucji obsługują kilka różnych konfiguracji czy o różnych wymaganiach. W niektórych przypadkach te konfiguracje obsługują instalację nie tylko na serwerach, ale w systemach operacyjnych klienta. Aby uzyskać więcej informacji na temat opcji dostępnych dla punktów dystrybucji, zobacz [zarządzanie zawartością i infrastrukturą zawartości programu System Center Configuration Manager](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

## <a name="windows-7-with-sp1-x86-x64-professional-enterprise-and-ultimate"></a>W systemie Windows 7 z dodatkiem SP1 (x 86, x 64): Professional, Enterprise i Ultimate  
**Serwery systemu lokacji:**  

-   Punkt dystrybucji  

    -   Punkty dystrybucji w tym systemie operacyjnym nie obsługują środowiska PXE.  

    -   Punkty dystrybucji w tym systemie operacyjnym nie obsługują multiemisji.  

    -   Punkty dystrybucji obsługują kilka różnych konfiguracji czy o różnych wymaganiach. W niektórych przypadkach te konfiguracje obsługują instalację nie tylko na serwerach, ale w systemach operacyjnych klienta. Aby uzyskać więcej informacji na temat opcji dostępnych dla punktów dystrybucji, zobacz [zarządzanie zawartością i infrastrukturą zawartości programu System Center Configuration Manager](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  


## <a name="the-server-core-installation-of-windows-server-2016"></a>Instalacja server core systemu Windows Server 2016
Począwszy od wersji 1606 z pakiet zbiorczy poprawek z KB3186654 (lub wersji linii bazowej 1606, wydanej w października 2016) to system operacyjny jest obsługiwany jako dystrybucji do punktu z następującymi ograniczeniami:  
  -   Obsługiwana jest tylko wersja x64-bitowych.
  -   Punkty dystrybucji w tym systemie operacyjnym nie obsługują środowiska PXE lub multiemisji.  


## <a name="the-server-core-installation-of-windows-server-2012-r2"></a>Instalacja Server Core systemu Windows Server 2012 R2  
 Oprócz starszych systemach operacyjnych, które są wyświetlane instalacja server core systemu Windows Server 2012 R2 jest obsługiwane do użytku jako punkty dystrybucji z następującymi ograniczeniami:  

-   Obsługiwana jest tylko wersja x64-bitowych.

-   Punkty dystrybucji w tym systemie operacyjnym nie obsługują środowiska PXE lub multiemisji.  

## <a name="the-server-core-installation-of-windows-server-2012"></a>Instalacja Server Core systemu Windows Server 2012  
 Oprócz starszych systemach operacyjnych, które są wyświetlane, instalacji server core systemu Windows Server 2012 jest również obsługiwany jako dystrybucji do punktu z następującymi ograniczeniami:  

-   Obsługiwana jest tylko wersja 64-bitowych.  

-   Punkty dystrybucji w tym systemie operacyjnym nie obsługują środowiska PXE lub multiemisji.
