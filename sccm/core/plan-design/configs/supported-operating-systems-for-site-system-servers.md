---
title: Obsługiwane serwery systemu lokacji
titleSuffix: Configuration Manager
description: Dowiedz się, które wersje systemu Windows można użyć do hostowania lokacji programu System Center Configuration Manager lub rola systemu lokacji.
ms.custom: na
ms.date: 04/17/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 17905b4c-3895-4ad4-a69c-5e0d0fc5a8c3
caps.latest.revision: 44
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 092fc9d47e0dc7bb7afe0e078bd835dd2d091226
ms.sourcegitcommit: e23350fe65ff99228274e465b24b5e163769f38f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2018
---
# <a name="supported-operating-systems-for-system-center-configuration-manager-site-system-servers"></a>Obsługiwane systemy operacyjne dla serwerów systemu lokacji programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


Ten artykuł zawiera szczegóły dotyczące wersji systemu Windows, które służą do hostowania lokacji programu Configuration Manager lub rola systemu lokacji.


Informacje przedstawione w tym artykule z informacjami w następujących artykułach:
-   [Zalecany sprzęt dla programu Configuration Manager](../../../core/plan-design/configs/recommended-hardware.md)
-   [Witryny i wymagania wstępne systemu lokacji programu Configuration Manager](../../../core/plan-design/configs/site-and-site-system-prerequisites.md)
-   [Numery rozmiaru i skali dla programu Configuration Manager](../../../core/plan-design/configs/size-and-scale-numbers.md)



## <a name="windows-server-2016-standard-and-datacenter"></a>Windows Server 2016: Standard i Datacenter
Ten pakiet zbiorczy poprawek z KB3186654 ten system operacyjny jest obsługiwana dla następujących ról:

**Serwery lokacji:**  

-   Centralna lokacja administracyjna  

-   Lokacja główna  

-   Lokacja dodatkowa  

**Serwery systemu lokacji:**  

-   Punkt usługi sieci Web Wykaz aplikacji  

-   Punkt witryny sieci Web wykazu aplikacji  

-   Punkt synchronizacji analizy zasobów  

-   Punkt rejestracji certyfikatu  

-   Punkt dystrybucji  

     Punkty dystrybucji obsługują kilka różnych konfiguracji czy o różnych wymaganiach. W niektórych przypadkach te konfiguracje obsługują instalację nie tylko na serwerach, ale w systemach operacyjnych klienta. Aby uzyskać więcej informacji na temat opcji dostępnych dla punktów dystrybucji, zobacz [zarządzanie zawartością i infrastrukturą zawartości](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

-   Punkt ochrony punktu końcowego  

-   Punkt rejestracji  

-   Punkt proxy rejestracji  

-   Rezerwowy punkt stanu  

-   Punkt zarządzania

-   Punkt usług raportowania  

-   Punkt połączenia usługi  

-   Serwer bazy danych lokacji  

     Serwery bazy danych lokacji nie są obsługiwane na kontrolerze domeny tylko do odczytu (RODC). Więcej informacji znajduje się w artykule [You may encounter problems when installing SQL Server on a domain controller](https://go.microsoft.com/fwlink/p/?LinkId=264856) (W przypadku instalowania programu SQL Server w kontrolerze domeny mogą wystąpić problemy) w bazie wiedzy Microsoft Knowledge Base. Ponadto serwery lokacji dodatkowych nie są obsługiwane na żadnym kontrolerze domeny.  

-   SMS_Provider  

-   Punkt aktualizacji oprogramowania  

-   punkt migracji stanu



## <a name="windows-storage-server-2016"></a>System Windows Storage Server 2016

**Serwer systemu lokacji:**  

-   Punkt dystrybucji  



## <a name="windows-server-2012-r2-x64-standard-and-datacenter"></a>Windows Server 2012 R2 (x 64): Standard i Datacenter  
**Serwery lokacji:**  

-   Centralna lokacja administracyjna  

-   Lokacja główna  

-   Lokacja dodatkowa  

**Serwery systemu lokacji:**  

-   Punkt usługi sieci Web Wykaz aplikacji  

-   Punkt witryny sieci Web wykazu aplikacji  

-   Punkt synchronizacji analizy zasobów  

-   Punkt rejestracji certyfikatu  

-   Punkt dystrybucji  

     Punkty dystrybucji obsługują kilka różnych konfiguracji czy o różnych wymaganiach. W niektórych przypadkach te konfiguracje obsługują instalację nie tylko na serwerach, ale w systemach operacyjnych klienta. Aby uzyskać więcej informacji na temat opcji dostępnych dla punktów dystrybucji, zobacz [zarządzanie zawartością i infrastrukturą zawartości](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

-   Punkt ochrony punktu końcowego  

-   Punkt rejestracji  

-   Punkt proxy rejestracji  

-   Rezerwowy punkt stanu  

-   Punkt zarządzania

-   Punkt usług raportowania  

-   Punkt połączenia usługi  

-   Serwer bazy danych lokacji  

     Serwery bazy danych lokacji nie są obsługiwane na kontrolerze domeny tylko do odczytu (RODC). Więcej informacji znajduje się w artykule [You may encounter problems when installing SQL Server on a domain controller](https://go.microsoft.com/fwlink/p/?LinkId=264856) (W przypadku instalowania programu SQL Server w kontrolerze domeny mogą wystąpić problemy) w bazie wiedzy Microsoft Knowledge Base. Ponadto serwery lokacji dodatkowych nie są obsługiwane na żadnym kontrolerze domeny.  

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

-   Punkt witryny sieci Web wykazu aplikacji  

-   Punkt synchronizacji analizy zasobów  

-   Punkt rejestracji certyfikatu  

-   Punkt dystrybucji  

     Punkty dystrybucji obsługują kilka różnych konfiguracji czy o różnych wymaganiach. W niektórych przypadkach te konfiguracje obsługują instalację nie tylko na serwerach, ale w systemach operacyjnych klienta. Aby uzyskać więcej informacji na temat opcji dostępnych dla punktów dystrybucji, zobacz [zarządzanie zawartością i infrastrukturą zawartości](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

-   Punkt ochrony punktu końcowego  

-   Punkt rejestracji  

-   Punkt proxy rejestracji  

-   Rezerwowy punkt stanu  

-   Punkt zarządzania

-   Punkt usług raportowania  

-   Punkt połączenia usługi  

-   Serwer bazy danych lokacji  

     Serwery bazy danych lokacji nie są obsługiwane na kontrolerze domeny tylko do odczytu (RODC). Więcej informacji znajduje się w artykule [You may encounter problems when installing SQL Server on a domain controller](https://go.microsoft.com/fwlink/p/?LinkId=264856) (W przypadku instalowania programu SQL Server w kontrolerze domeny mogą wystąpić problemy) w bazie wiedzy Microsoft Knowledge Base. Ponadto serwery lokacji dodatkowych nie są obsługiwane na żadnym kontrolerze domeny.  

-   SMS_Provider  

-   Punkt aktualizacji oprogramowania  

-   punkt migracji stanu  



## <a name="windows-server-2008-r2-with-sp1-x64-standard-enterprise-and-datacenter"></a>Windows Server 2008 R2 z dodatkiem SP1 (x 64): Standard, Enterprise i Datacenter  
 Windows Server 2008 R2 jest obecnie obowiązuje wsparcie i nie jest już dostępne podstawowe wsparcie, zgodnie z opisem w [Microsoft Cykl wsparcia technicznego produktów](https://support.microsoft.com/lifecycle). Aby uzyskać więcej informacji na temat wsparcia w przyszłości dla tych systemów operacyjnych jako serwerów systemu lokacji z programem Configuration Manager, zobacz [przestarzałe systemy operacyjne serwera](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-server#deprecated-server-operating-systems).  

 Ten system operacyjny nie jest obsługiwany dla serwerów lokacji i większości ról systemu lokacji. Nadal jest obsługiwane dla roli lokacji punktu dystrybucji systemu, w tym ściągające punkty dystrybucji i środowiska PXE i multiemisji.

**Serwery systemu lokacji:**  
-   Punkt dystrybucji  

    -   Punkty dystrybucji, w tym systemie operacyjnym nie obsługują multiemisji.  

    -   Punkty dystrybucji, w tym systemie operacyjnym obsługują środowisko PXE.

    -   Punkty dystrybucji obsługują kilka różnych konfiguracji czy o różnych wymaganiach. W niektórych przypadkach te konfiguracje obsługują instalację nie tylko na serwerach, ale w systemach operacyjnych klienta. Aby uzyskać więcej informacji na temat opcji dostępnych dla punktów dystrybucji, zobacz [zarządzanie zawartością i infrastrukturą zawartości](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  



## <a name="windows-server-2008-with-sp2-x86-x64-standard-enterprise-and-datacenter"></a>Windows Server 2008 z dodatkiem SP2 (x 86, x 64): Standard, Enterprise i Datacenter  
 Windows Server 2008 jest obecnie obowiązuje wsparcie i nie jest już dostępne podstawowe wsparcie, zgodnie z opisem w [Microsoft Cykl wsparcia technicznego produktów](https://support.microsoft.com/lifecycle). Aby uzyskać więcej informacji na temat wsparcia w przyszłości dla tych systemów operacyjnych jako serwerów systemu lokacji z programem Configuration Manager, zobacz [przestarzałe systemy operacyjne serwera](/sccm/core/plan-design/changes/deprecated/removed-and-deprecated-server#deprecated-server-operating-systems).  

Ten system operacyjny nie jest obsługiwany dla serwerów lokacji i ról systemu lokacji, z wyjątkiem punktu dystrybucji i punktu dystrybucji ściągania. Można nadal używać tego systemu operacyjnego jako punkt dystrybucji, do momentu ogłoszenia zaniechania tej obsługi lub zakończenia okresu rozszerzonej pomocy technicznej tego systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [instalacji programu System Center Configuration Manager CB i LTSB zakończy się niepowodzeniem w systemie Windows Server 2008](https://support.microsoft.com/help/4015095).

**Serwery systemu lokacji:**  
-   Punkt dystrybucji  

    -   Punkty dystrybucji, w tym systemie operacyjnym nie obsługują multiemisji.  

    -   Punkty dystrybucji, w tym systemie operacyjnym obsługują środowisko PXE, ale nie obsługują rozruchu przez sieć komputerów klienckich w trybie EFI. Obsługiwane są komputery klienckie z systemem BIOS lub z rozruchem EFI w trybie zgodności.  

    -   Punkty dystrybucji obsługują kilka różnych konfiguracji czy o różnych wymaganiach. W niektórych przypadkach te konfiguracje obsługują instalację nie tylko na serwerach, ale w systemach operacyjnych klienta. Aby uzyskać więcej informacji na temat opcji dostępnych dla punktów dystrybucji, zobacz [zarządzanie zawartością i infrastrukturą zawartości](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  



## <a name="windows-10-x86-x64-pro-and-enterprise"></a>Windows 10 (x86, x64): Pro i Enterprise  
**Serwery systemu lokacji:**  

-   Punkt dystrybucji  

    -   Punkty dystrybucji, w tym systemie operacyjnym nie obsługują środowisko PXE. 

    -   Punkty dystrybucji w tej wersji systemu operacyjnego nie obsługują multiemisji.  

    -   Punkty dystrybucji obsługują kilka różnych konfiguracji czy o różnych wymaganiach. W niektórych przypadkach te konfiguracje obsługują instalację nie tylko na serwerach, ale w systemach operacyjnych klienta. Aby uzyskać więcej informacji na temat opcji dostępnych dla punktów dystrybucji, zobacz [zarządzanie zawartością i infrastrukturą zawartości](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  



## <a name="windows-81-x86-x64-professional-and-enterprise"></a>Windows 8.1 (x86, x64): Professional i Enterprise  
**Serwery systemu lokacji:**  

-   Punkt dystrybucji  

    -   Punkty dystrybucji, w tym systemie operacyjnym nie obsługują środowisko PXE.  

    -   Punkty dystrybucji w tej wersji systemu operacyjnego nie obsługują multiemisji.  

    -   Punkty dystrybucji obsługują kilka różnych konfiguracji czy o różnych wymaganiach. W niektórych przypadkach te konfiguracje obsługują instalację nie tylko na serwerach, ale w systemach operacyjnych klienta. Aby uzyskać więcej informacji na temat opcji dostępnych dla punktów dystrybucji, zobacz [zarządzanie zawartością i infrastrukturą zawartości](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  



## <a name="windows-7-with-sp1-x86-x64-professional-enterprise-and-ultimate"></a>W systemie Windows 7 z dodatkiem SP1 (x 86, x 64): Professional, Enterprise i Ultimate  
**Serwery systemu lokacji:**  

-   Punkt dystrybucji  

    -   Punkty dystrybucji, w tym systemie operacyjnym nie obsługują środowisko PXE.  

    -   Punkty dystrybucji w tej wersji systemu operacyjnego nie obsługują multiemisji.  

    -   Punkty dystrybucji obsługują kilka różnych konfiguracji czy o różnych wymaganiach. W niektórych przypadkach te konfiguracje obsługują instalację nie tylko na serwerach, ale w systemach operacyjnych klienta. Aby uzyskać więcej informacji na temat opcji dostępnych dla punktów dystrybucji, zobacz [zarządzanie zawartością i infrastrukturą zawartości](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

## <a name="the-server-core-installation-of-windows-server-version-1709"></a>Instalacja server core systemu Windows Server w wersji 1709
W programie Configuration Manager 1710, [w systemie Windows Server w wersji 1709](https://docs.microsoft.com/windows-server/get-started/get-started-with-1709) jest obsługiwana w przypadku użycia jako dystrybucji punktu z następującymi ograniczeniami:  
  -   Obsługiwana jest tylko wersja x64-bitowych.
  -   Punkty dystrybucji w tym systemie operacyjnym nie obsługują środowiska PXE lub multiemisji.  

## <a name="the-server-core-installation-of-windows-server-2016"></a>Instalacja server core systemu Windows Server 2016
Ten pakiet zbiorczy poprawek z KB3186654, ten system operacyjny jest obsługiwana jako dystrybucji do punktu z następującymi ograniczeniami:  
  -   Obsługiwana jest tylko wersja x64-bitowych.
  -   Punkty dystrybucji w tym systemie operacyjnym nie obsługują środowiska PXE lub multiemisji.  



## <a name="the-server-core-installation-of-windows-server-2012-r2"></a>Instalacja Server Core systemu Windows Server 2012 R2  
 Instalacja server core systemu Windows Server 2012 R2 jest obsługiwany jako dystrybucji do punktu z następującymi ograniczeniami:  

-   Obsługiwana jest tylko wersja x64-bitowych.

-   Punkty dystrybucji w tym systemie operacyjnym nie obsługują środowiska PXE lub multiemisji.  



## <a name="the-server-core-installation-of-windows-server-2012"></a>Instalacja Server Core systemu Windows Server 2012  
 Instalacja server core systemu Windows Server 2012 jest obsługiwany jako dystrybucji do punktu z następującymi ograniczeniami:  

-   Obsługiwana jest tylko wersja 64-bitowych.  

-   Punkty dystrybucji w tym systemie operacyjnym nie obsługują środowiska PXE lub multiemisji.
