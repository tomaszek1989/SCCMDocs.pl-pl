---
title: Wymagania dotyczące infrastruktury OSD
titleSuffix: Configuration Manager
description: Poznaj zależności zewnętrzne i produktu i wymagania dotyczące wdrażania systemu operacyjnego
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 1dc74219-7ff5-4e3b-b4f6-5aad663bb75b
caps.latest.revision: ''
author: aczechowski
ms.author: aaroncz
manager: dougeby
ms.openlocfilehash: 36e49206154a1c061fb8266e0c8ed8691cc4d4f0
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="infrastructure-requirements-for-os-deployment-in-system-center-configuration-manager"></a>Wymagania dotyczące infrastruktury dla wdrożenia systemu operacyjnego w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Wdrażanie systemu operacyjnego w programie Configuration Manager ma zależności zewnętrznych, a także zależności w obrębie produktu. Użyj w tym artykule, aby ułatwić przygotowanie infrastruktury do wdrożenia systemu operacyjnego.  



##  <a name="BKMK_ExternalDependencies"></a> Zależności poza programem Configuration Manager  
 Ta sekcja zawiera informacje o narzędziach zewnętrznych, zestawach instalacji i wersji systemu operacyjnego, które są wymagane do wdrażania systemów operacyjnych w programie Configuration Manager.  

### <a name="windows-adk-for-windows-10"></a>Windows ADK dla systemu Windows 10  
 Windows Assessment and Deployment Kit (ADK) to zestaw narzędzi i dokumentacji ułatwiających konfigurację i wdrażania systemu Windows. Program Configuration Manager używa zestawu Windows ADK, aby automatyzować czynności, takie jak instalowanie systemu Windows, przechwytywania obrazów i migracji profili użytkowników oraz danych.  

 Poniższe funkcje zestawu Windows ADK muszą być zainstalowane na serwerze lokacji w lokacji najwyższego poziomu w hierarchii, na serwerze lokacji każdej lokacji głównej w hierarchii, a na serwerze systemu lokacji dostawcy programu SMS:  

-   Narzędzia do migracji stanu użytkowników (USMT) <sup>1</sup>  

-   Narzędzia wdrażania systemu Windows  

-   Środowisko preinstalacji systemu Windows (Windows PE)

Aby uzyskać listę wersji zestawu Windows 10 adk korzystające z różnymi wersjami programu Configuration Manager, zobacz [pomocy technicznej dla systemu Windows 10](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-adk).

 <sup>1</sup> narzędzie USMT nie jest wymagane na serwerze systemu lokacji dostawcy programu SMS.  

> [!NOTE]  
>  Należy ręcznie zainstalować zestaw Windows ADK na każdym serwerze lokacji, przed zainstalowaniem lokacji programu Configuration Manager.  

 Aby uzyskać więcej informacji, zobacz:  

-   [Scenariusze zestawu Windows ADK dla systemu Windows 10 dla informatyków](/windows/deployment/windows-adk-scenarios-for-it-pros)  

-   [Pobierz zestaw Windows ADK dla systemu Windows 10](/windows-hardware/get-started/adk-install)  

-   [Obsługa systemu Windows 10](/sccm/core/plan-design/configs/support-for-windows-10)  


### <a name="user-state-migration-tool-usmt"></a>Narzędzia do migracji stanu użytkowników (USMT)  
 Programu Configuration Manager korzysta z pakietu narzędzia USMT, który zawiera pliki źródłowe narzędzia USMT 10 do przechwytywania i przywracania stanu użytkownika w ramach wdrożenia systemu operacyjnego. Instalator programu Configuration Manager w lokacji najwyższego poziomu automatycznie tworzy pakiet narzędzia USMT. Narzędzie USMT 10 przechwytuje stan użytkownika z systemu Windows 7, Windows 8, Windows 8.1 i Windows 10.  

 Aby uzyskać więcej informacji, zobacz:  

-   [Typowe scenariusze migracji dla narzędzia USMT 10](/windows/deployment/usmt/usmt-common-migration-scenarios)  

-   [Zarządzanie stanem użytkownika](../get-started/manage-user-state.md)  

### <a name="windows-pe"></a>Windows PE  
 Środowisko Windows PE jest używane do uruchamiania komputera za pomocą obrazów rozruchowych. Jest wersja systemu Windows o ograniczonej liczbie usług używany podczas preinstalacji i wdrażania systemu Windows. Poniższa lista zawiera obsługiwanej wersji zestawu Windows adk dla programu Configuration Manager, bieżącej gałęzi:  

-   **Wersja zestawu Windows ADK**  

     Zestaw Windows ADK dla systemu Windows 10. Aby uzyskać więcej informacji, zobacz [pomocy technicznej dla systemu Windows 10](/sccm/core/plan-design/configs/support-for-windows-10#windows-10-adk).

-   **Wersje systemu Windows PE dla obrazów rozruchowych modyfikowalnych z konsoli programu Configuration Manager**  

     Windows PE 10  

-   **Obsługiwane wersje systemu Windows PE dla obrazów rozruchowych modyfikowalnych z konsoli programu Configuration Manager**  

     Windows PE 3.1<sup>1</sup> i Windows PE 5  

     <sup>1</sup> można dodawać tylko obraz rozruchowy do programu Configuration Manager bazujące na środowisku Windows PE 3.1. Zainstaluj uzupełnienie Windows AIK dla systemu Windows 7 z dodatkiem SP1, aby uaktualnić zestaw Windows AIK dla systemu Windows 7 (oparty na środowisku Windows PE3) z uzupełnieniem Windows AIK dla systemu Windows 7 z dodatkiem SP1 (oparte na środowisku Windows PE 3.1). Uzupełnienie Windows AIK dla systemu Windows 7 z dodatkiem SP1 możesz pobrać z [Centrum pobierania Microsoft](https://www.microsoft.com/download/details.aspx?id=5188).  

     Na przykład gdy program Configuration Manager, można dostosować obrazy rozruchowe zestawu Windows ADK dla systemu Windows 10 (oparte na systemie Windows PE 10) z konsoli programu Configuration Manager. Chociaż obrazy rozruchowe bazujące na środowisku Windows PE 5 są obsługiwane, należy je dostosować za pomocą innego komputera i użyć wersji narzędzia DISM zainstalowanej z zestawem Windows ADK dla systemu Windows 8. Następnie można dodać obraz rozruchowy do konsoli programu Configuration Manager. Aby uzyskać więcej informacji o czynności pozwalające na dostosowanie obrazu rozruchowego (Dodawanie opcjonalnych składników i sterowników), włączenie obsługi wiersza polecenia w obrazie rozruchowym, dodanie obrazu rozruchowego do konsoli programu Configuration Manager i Aktualizuj punkty dystrybucji o obraz rozruchowy, zobacz [dostosowywanie obrazów rozruchowych](../get-started/customize-boot-images.md). Aby uzyskać więcej informacji na temat obrazów rozruchowych, zobacz [Zarządzanie obrazami rozruchowymi](../get-started/manage-boot-images.md).  


### <a name="windows-server-update-services-wsus"></a>Program Windows Server Update Services (WSUS)  
 WSUS jest wymagana dla punktu aktualizacji oprogramowania, co jest wymagane do zainstalowania aktualizacji oprogramowania podczas wdrażania systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [Konfigurowanie oprogramowania zainstalować punkt aktualizacji](/sccm/sum/get-started/install-a-software-update-point).


### <a name="internet-information-services-iis-on-the-site-system-servers"></a>Internetowe usługi informacyjne (IIS) na serwerach systemu lokacji  
 Program IIS jest wymagana dla punktu dystrybucji, punktu migracji stanu i punktu zarządzania. Aby uzyskać więcej informacji, zobacz [Site and site system prerequisites](../../core/plan-design/configs/site-and-site-system-prerequisites.md) (Wymagania wstępne dotyczące lokacji i systemu lokacji).  


### <a name="windows-deployment-services-wds"></a>usługami wdrażania systemu Windows (WDS),  
 Usługi wdrażania systemu Windows jest wymagany dla wdrożeń środowiska PXE i w przypadku korzystania z multiemisji do optymalizacji przepustowości we wdrożeniach. Aby uzyskać więcej informacji, zobacz [usług wdrażania systemu Windows](#BKMK_WDS) w tym artykule.  


### <a name="dynamic-host-configuration-protocol-dhcp"></a>Protokół DHCP  
 Dla wdrożeń środowiska PXE wymagany jest protokół DHCP. Aby wdrażać systemy operacyjne, używając środowiska PXE, należy dysponować działającym serwerem DHCP z aktywnym hostem. Aby uzyskać więcej informacji dotyczących wdrożeń środowiska PXE, zobacz [przy użyciu środowiska PXE do wdrażania systemu Windows za pośrednictwem sieci](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  


### <a name="supported-operating-systems-and-hard-disk-configurations"></a>Obsługiwane systemy operacyjne i konfiguracje dysku twardego  
 Aby uzyskać więcej informacji o wersji systemu operacyjnego i konfiguracjach dysku twardego, które są obsługiwane przez program Configuration Manager w przypadku wdrażania systemów operacyjnych, zobacz [obsługiwanych systemów operacyjnych](#BKMK_SupportedOS) i [obsługiwane konfiguracji dysków](#BKMK_SupportedDiskConfig).  


### <a name="windows-device-drivers"></a>Sterowniki urządzeń dla systemu Windows  
 Sterowniki urządzeń systemu Windows można po zainstalowaniu systemu operacyjnego na komputerze docelowym. Są one również używane podczas uruchamiania systemu Windows PE obrazu rozruchowego. Aby uzyskać więcej informacji, zobacz [zarządzania sterownikami](../get-started/manage-drivers.md).  



##  <a name="BKMK_InternalDependencies"></a> Zależności programu Configuration Manager  
 Ta sekcja zawiera informacje dotyczące systemu operacyjnego programu Configuration Manager wymagania wstępne dotyczące wdrażania.  


### <a name="os-image"></a>Obraz systemu operacyjnego  
 Obrazy systemu operacyjnego w programie Configuration Manager są przechowywane w formacie plików obrazów systemu Windows (WIM). Reprezentują skompresowaną kolekcję plików i folderów odniesienia. Te obrazy są wymagane do pomyślnej instalacji i konfiguracji systemu operacyjnego na komputerze. Aby uzyskać więcej informacji, zobacz [zarządzanie obrazami systemu operacyjnego](../get-started/manage-operating-system-images.md).  


### <a name="driver-catalog"></a>Katalog sterowników  
 Aby wdrożyć sterownik urządzenia, musi zaimportować sterownik urządzenia, włączyć i udostępnić w punkcie dystrybucji dostępnym dla klienta programu Configuration Manager. Aby uzyskać więcej informacji o katalogu sterowników, zobacz [zarządzania sterownikami](../get-started/manage-drivers.md).  


### <a name="management-point"></a>Punkt zarządzania  
 Punkty zarządzania przesyłają informacje między klientami a lokacją programu Configuration Manager. Klient używa punktu zarządzania do uruchomienia sekwencji zadań wdrażania systemu operacyjnego. Aby uzyskać więcej informacji o sekwencjach zadań, zobacz [uwagi dotyczące planowania automatyzacji zadań](planning-considerations-for-automating-tasks.md).  


### <a name="distribution-point"></a>Punkt dystrybucji  
 Punkty dystrybucji są używane w większości wdrożeń do przechowywania danych, który służy do wdrażania systemu operacyjnego, takich jak obraz lub sterownik pakietów. Sekwencje zadań zwykle pobierają dane z punktu dystrybucji w celu wdrożenia systemu operacyjnego. Aby uzyskać więcej informacji o instalacji punktów dystrybucji i zarządzaniu zawartością, zobacz [zarządzanie zawartością i infrastrukturą zawartości](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  


### <a name="pxe-enabled-distribution-point"></a>Punkt dystrybucji z obsługą środowiska PXE  
 Aby wykonać wdrożenia zainicjowane ze środowiska PXE, należy tak skonfigurować punkt dystrybucji, aby akceptował żądania środowiska PXE od klientów. Aby uzyskać więcej informacji, zobacz [konfigurowania punktu dystrybucji](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#pxe).


### <a name="multicast-enabled-distribution-point"></a>Punkt dystrybucji z obsługą multiemisji  
 Aby zoptymalizować wdrożeń systemu operacyjnego za pomocą multiemisji, należy skonfigurować punkt dystrybucji do obsługi multiemisji. Aby uzyskać więcej informacji, zobacz [konfigurowania punktu dystrybucji](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#multicast).   


### <a name="state-migration-point"></a>punkt migracji stanu  
 W przypadku przechwytywania i przywracana danych stanu użytkownika dla wdrożeń równoczesnych i odświeżających należy skonfigurować punkt migracji stanu w celu przechowywania danych stanu użytkownika na innym komputerze.  

 Więcej informacji o sposobie konfigurowania punktu migracji stanu znajduje się w temacie [Punkt migracji stanu](../get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_StateMigrationPoints).  

 Aby uzyskać informacje o sposobie przechwytywania i przywracania stanu użytkownika, zobacz [Zarządzanie stanem użytkownika](../get-started/manage-user-state.md).  


### <a name="reporting-services-point"></a>Punkt usług raportowania  
 Aby użyć raportów programu Configuration Manager w przypadku wdrożeń systemu operacyjnego, należy zainstalować i skonfigurować punkt usług raportowania. Aby uzyskać więcej informacji, zobacz [raportowania](../../core/servers/manage/reporting.md).  


### <a name="security-permissions-for-os-deployments"></a>Uprawnienia zabezpieczeń dla wdrożeń systemu operacyjnego  
 **Menedżer wdrożenia systemu operacyjnego** roli zabezpieczeń jest wbudowana i nie można zmienić. Można jednak skopiować rolę, wprowadzić zmiany, a następnie zapisać je jako nową, niestandardową rolę zabezpieczeń. Poniżej podano niektóre uprawnienia, które dotyczą bezpośrednio wdrożeń systemu operacyjnego:  

-   **Pakiet obrazu rozruchowego**: Utwórz, Usuń, Modyfikuj, Modyfikuj Folder, Przenieś obiekt, Odczytaj, ustaw zakres zabezpieczeń  

-   **Sterowniki urządzeń**: Tworzenie, Usuń, Modyfikuj, Modyfikuj Folder, Modyfikuj raport, Przenieś obiekt, Odczytaj, uruchom raport  

-   **Pakiet sterowników**: Utwórz, Usuń, Modyfikuj, Modyfikuj Folder, Przenieś obiekt, Odczytaj, ustaw zakres zabezpieczeń  

-   **Obraz systemu operacyjnego**: Utwórz, Usuń, Modyfikuj, Modyfikuj Folder, Przenieś obiekt, Odczytaj, ustaw zakres zabezpieczeń  

-   **Pakiet instalacyjny systemu operacyjnego**: Utwórz, Usuń, Modyfikuj, Modyfikuj Folder, Przenieś obiekt, Odczytaj, ustaw zakres zabezpieczeń  

-   **Pakiet sekwencji zadań**: Utwórz, Utwórz zadanie nośnik sekwencji, Usuń, Modyfikuj, Modyfikuj Folder, Modyfikuj raport, Przenieś obiekt, Odczytaj, uruchom raport, ustaw zakres zabezpieczeń  

 Aby uzyskać więcej informacji, zobacz [Tworzenie niestandardowych ról zabezpieczeń](../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_CreateSecRole).  


### <a name="security-scopes-for-os-deployments"></a>Zakresy zabezpieczeń dla wdrożeń systemu operacyjnego  
 Zakresy zabezpieczeń umożliwiają zapewnienie użytkownikom administracyjnym dostępu do obiektów zabezpieczanych używanych w przypadku wdrożeń systemu operacyjnego, takich jak obrazy systemu operacyjnego i rozruchowy, pakietów sterowników i pakiety sekwencji zadań. Aby uzyskać więcej informacji, zobacz [Zakresy zabezpieczeń](../../core/understand/fundamentals-of-role-based-administration.md#bkmk_PlanScope).  



##  <a name="BKMK_WDS"></a> Usługi wdrażania systemu Windows  
 Usługi wdrażania systemu Windows (WDS) muszą być zainstalowane na tym samym serwerze co punkty dystrybucji konfigurowane do obsługi środowiska PXE lub multiemisji. Usługi wdrażania systemu Windows są zawarte w systemie operacyjnym serwera. W przypadku wdrożeń za pomocą środowiska PXE Usługi wdrażania systemu Windows wykonują rozruch w środowisku PXE. Po zainstalowaniu punktu dystrybucji i włączeniu obsługi środowiska PXE, programu Configuration Manager instaluje dostawcę do wdrażania systemu Windows używającego funkcji rozruchu w środowisku PXE.  

> [!NOTE]  
>  Jeśli serwer wymaga ponownego uruchomienia, instalacja usług wdrażania systemu Windows może zakończyć się niepowodzeniem. 


### <a name="wds-requirements"></a>Wymagania dotyczące usług wdrażania systemu Windows  

-   Instalacja usług wdrażania systemu Windows na serwerze wymaga, aby administrator był członkiem lokalnej grupy administratorów.  

-   Serwer Usług wdrażania systemu Windows musi być członkiem domeny usługi Active Directory lub kontrolera domeny usługi Active Directory. Wszystkie konfiguracje domeny systemu Windows i lasu obsługują Usługi wdrażania systemu Windows.  

-   Jeśli dostawca jest zainstalowany na serwerze zdalnym, należy zainstalować usługi wdrażania systemu Windows na serwerze lokacji i dostawcy zdalnym.  


###  <a name="BKMK_WDSandDHCP"></a> Zagadnienia dotyczące sytuacji, gdy na tym samym serwerze istnieją Usługi wdrażania systemu Windows i protokół DHCP  
 Jeśli punkt dystrybucji ma być obsługiwany również na serwerze z uruchomionym protokołem DHCP, należy wziąć pod uwagę poniższe kwestie konfiguracyjne.  

-   Należy dysponować działającym serwerem DHCP z aktywnym zakresem. Usługi wdrażania systemu Windows używają środowiska PXE, które wymaga serwera DHCP.  

-   DHCP i usług wdrażania systemu Windows wymagają portu numer 67. Można hostowane usługi WDS i DHCP, należy przenieść DHCP lub punkt dystrybucji, który jest skonfigurowany do środowiska PXE na osobny serwer. Lub Poniższa procedura umożliwia skonfigurowanie serwera WDS do nasłuchiwania na innym porcie.  

    #### <a name="to-configure-the-wds-server-to-listen-on-a-different-port"></a>Aby skonfigurować serwer usług wdrażania systemu Windows do nasłuchiwania na innym porcie  

    1.  Zmień poniższy klucz rejestru:  

         `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WDSServer\Providers\WDSPXE`  

    2.  Ustaw wartość rejestru **UseDHCPPorts** do **0**.  

    3.  Aby nowa konfiguracja została zastosowana, uruchom na serwerze poniższe polecenie:  

         `WDSUTIL /Set-Server /UseDHCPPorts:No /DHCPOption60:Yes`  

-   Serwer DNS jest wymagany do uruchamiania usług wdrażania systemu Windows.  

-   Poniższe porty UDP musi być otwarty na serwerze usług wdrażania systemu Windows.  

    -   Port 67 (DHCP)  

    -   Port 69 (TFTP)  

    -   Port 4011 (PXE)  

    > [!NOTE]  
    >  Jeśli na serwerze jest wymagana autoryzacja DHCP, należy port klienta DHCP 68 być otwarte na serwerze.  



##  <a name="BKMK_SupportedOS"></a> Obsługiwane systemy operacyjne  
 Wszystkie systemy operacyjne Windows wymienionym obsługiwani klienci w [obsługiwane systemy operacyjne dla klientów i urządzeń](../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices.md) są obsługiwane w przypadku wdrażania systemu operacyjnego.  



##  <a name="BKMK_SupportedDiskConfig"></a> Obsługiwane konfiguracje dysków  
 W poniższej tabeli przedstawiono kombinacje konfiguracji dysków twardych w komputerach referencyjnych i docelowych, które są obsługiwane w przypadku wdrażania systemu operacyjnego programu Configuration Manager:  

|Konfiguracja dysków twardych komputera referencyjnego|Konfiguracja dysków twardych komputera docelowego|  
|------------------------------------------------|--------------------------------------------------|  
|Dysk podstawowy|Dysk podstawowy|  
|Wolumin prosty na dysku dynamicznym|Wolumin prosty na dysku dynamicznym|  

 Program Configuration Manager obsługuje przechwytywanie obrazu systemu operacyjnego tylko na komputerach, które są skonfigurowane przy użyciu woluminów prostych. Nie jest obsługiwane dla następujących konfiguracji dysków twardych:  

-   woluminy łączone,  

-   woluminy rozłożone (RAID 0),  

-   woluminy dublowane (RAID 1),  

-   woluminy z parzystością (RAID 5).  

 W poniższej tabeli przedstawiono dodatkową konfigurację dysków w komputerach referencyjnych i docelowych, które nie jest obsługiwane z wdrożeniem systemu operacyjnego programu Configuration Manager.  

|Konfiguracja dysków twardych komputera referencyjnego|Konfiguracja dysków twardych komputera docelowego|  
|------------------------------------------------|--------------------------------------------------|  
|Dysk podstawowy|Dysk dynamiczny|  



## <a name="next-steps"></a>Następne kroki
- [Przygotowanie ról systemu lokacji dla wdrożenia systemu operacyjnego](/sccm/osd/get-started/prepare-site-system-roles-for-operating-system-deployments)
- [Przygotowanie do wdrożenia systemu operacyjnego](../get-started/prepare-for-operating-system-deployment.md)
