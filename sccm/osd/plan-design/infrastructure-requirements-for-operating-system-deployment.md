---
title: "Wymagania dotyczące wdrażania systemu operacyjnego infrastruktury | Dokumentacja firmy Microsoft"
description: "Upewnij się, że znasz zależności zewnętrzne i zależności produktu przed użyciem programu System Center 2012 Configuration Manager do wdrażania systemu operacyjnego."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-osd
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 1dc74219-7ff5-4e3b-b4f6-5aad663bb75b
caps.latest.revision: 24
author: Dougeby
ms.author: dougeby
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f809c9327db9f298168674add2d09820fdecd1b8
ms.openlocfilehash: a002bf5e03c3fd71a6346c8303be757b83092199
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="infrastructure-requirements-for-operating-system-deployment-in-system-center-configuration-manager"></a>Wymagania dotyczące infrastruktury dla wdrożenia systemu operacyjnego w programie System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Wdrożenie systemu operacyjnego w programie System Center 2012 Configuration Manager ma zależności zewnętrzne i zależności w obrębie produktu. Następujące sekcje zawierają informacje ułatwiające przygotowanie do wdrożenia systemu operacyjnego.  

##  <a name="BKMK_ExternalDependencies"></a> Zależności poza programem Configuration Manager  
 Następujące informacje o narzędziach zewnętrznych, zestawach instalacji i systemów operacyjnych, które są wymagane do wdrażania systemów operacyjnych w programie Configuration Manager.  

### <a name="windows-adk-for-windows-10"></a>Windows ADK dla systemu Windows 10  
 Windows ADK to zestaw narzędzi i dokumentacji ułatwiających konfigurację i wdrażanie systemów operacyjnych Windows. Program Configuration Manager używa zestawu Windows do automatyzowania instalacji systemu Windows, przechwytywania obrazów systemu Windows, migracji profili użytkowników oraz danych i tak dalej.  

 Poniższe funkcje zestawu Windows ADK muszą być zainstalowane na serwerze lokacji najwyższego poziomu hierarchii, na serwerze lokacji każdej lokacji głównej w hierarchii oraz na serwerze systemu lokacji dostawcy programu SMS:  

-   Narzędzia do migracji stanu użytkowników (USMT) <sup>1</sup>  

-   Narzędzia wdrażania systemu Windows  

-   Środowisko preinstalacji systemu Windows (Windows PE)  

 <sup>1</sup> Narzędzie USMT nie jest wymagane na serwerze systemu lokacji dostawcy programu SMS.  

> [!NOTE]  
>  Należy ręcznie zainstalować zestaw Windows ADK na każdym komputerze, który będzie obsługiwać centralnej lokacji administracyjnej lub serwerze lokacji głównej, przed zainstalowaniem lokacji programu Configuration Manager.  

 Aby uzyskać więcej informacji, zobacz:  

-   [Scenariusze dotyczące zestawu Windows ADK dla systemu Windows 10 dla informatyków](https://technet.microsoft.com/library/mt280162\(v=vs.85\).aspx)  

-   [Pobierz zestaw Windows ADK dla systemu Windows 10](https://msdn.microsoft.com/windows/hardware/dn913721.aspx#adkwin10)  

-   [Obsługa systemu Windows 10](/sccm/core/plan-design/configs/support-for-windows-10)  


### <a name="user-state-migration-tool-usmt"></a>Narzędzia do migracji stanu użytkowników (USMT)  
 Program Configuration Manager używa pakiet narzędzia USMT, który zawiera pliki źródłowe narzędzia USMT 10 do przechwycenia i przywrócenia stanu użytkownika w ramach wdrażania systemu operacyjnego. Instalator programu Configuration Manager w lokacji najwyższego poziomu automatycznie tworzy pakiet narzędzia USMT. Za pomocą narzędzia USMT 10 można przechwytywać stan użytkownika z systemu Windows 7, Windows 8, Windows 8.1 i Windows 10. Narzędzie USMT 10 jest dystrybuowane w Zestawie do oceny i wdrażania systemu Windows (Windows ADK) dla systemu Windows 10.  

 Aby uzyskać więcej informacji, zobacz:  

-   [Typowe scenariusze migracji dla narzędzia USMT 10](https://technet.microsoft.com/library/mt299169\(v=vs.85\).aspx)  

-   [Zarządzanie stanem użytkowników](../get-started/manage-user-state.md)  

### <a name="windows-pe"></a>Windows PE  
 Środowisko Windows PE jest używane do uruchamiania komputera za pomocą obrazów rozruchowych. Windows PE to system operacyjny Windows o ograniczonej liczbie usług używany podczas preinstalacji i wdrażania systemów operacyjnych Windows. Następujące zawiera wersję programu Configuration Manager i obsługiwanej wersji zestawu Windows, wersja środowiska Windows PE, na której oparto obraz rozruchowy, który można dostosować z konsoli programu Configuration Manager i wersji systemu Windows PE, na których oparto obraz rozruchowy który można dostosować przy użyciu narzędzia DISM, a następnie dodać obraz do określonej wersji programu Configuration Manager.  

#### <a name="configuration-manager-version-1511"></a>Program Configuration Manager w wersji 1511  
 Poniżej zamieszczono obsługiwanej wersji zestawu Windows ADK, wersję środowiska Windows PE, na której oparto obraz rozruchowy, który można dostosować z konsoli programu Configuration Manager i wersji systemu Windows PE, na których oparto obraz rozruchowy który można dostosować przy użyciu narzędzia DISM, a następnie dodać obraz do programu Configuration Manager.  

-   **Wersja zestawu Windows ADK**  

     Windows ADK dla systemu Windows 10  

-   **Wersje systemu Windows PE dla obrazów rozruchowych modyfikowalnych z konsoli programu Configuration Manager**  

     Windows PE 10  

-   **Obsługiwane wersje systemu Windows PE dla obrazów rozruchowych modyfikowalnych z konsoli programu Configuration Manager**  

     Windows PE 3.1<sup>1</sup> i Windows PE 5  

     <sup>1</sup> można dodawać tylko obraz rozruchowy do programu Configuration Manager, gdy jest on oparty na systemie Windows PE 3.1. Zainstaluj uzupełnienie Windows AIK dla systemu Windows 7 z dodatkiem SP1, aby uaktualnić zestaw Windows AIK dla systemu Windows 7 (oparty na środowisku Windows PE3) z uzupełnieniem Windows AIK dla systemu Windows 7 z dodatkiem SP1 (oparte na środowisku Windows PE 3.1). Uzupełnienie Windows AIK dla systemu Windows 7 z dodatkiem SP1 możesz pobrać z [Centrum pobierania Microsoft](http://www.microsoft.com/download/details.aspx?id=5188).  

     Na przykład jeśli korzystasz z programu Configuration Manager, można dostosować obrazy rozruchowe program Windows ADK dla systemu Windows 10 (oparte na systemie Windows PE 10) z konsoli programu Configuration Manager. Chociaż obrazy rozruchowe bazujące na środowisku Windows PE 5 są obsługiwane, należy je dostosować za pomocą innego komputera i użyć wersji narzędzia DISM zainstalowanej z zestawem Windows ADK dla systemu Windows 8. Następnie można dodać obraz rozruchowy do konsoli programu Configuration Manager. Aby uzyskać więcej informacji o czynności pozwalające na dostosowanie obrazu rozruchowego (z dodaniem opcjonalnych składników i sterowników), włączenie obsługi wiersza polecenia w obrazie rozruchowym, dodanie obrazu rozruchowego do konsoli programu Configuration Manager i Aktualizuj punkty dystrybucji z obrazu rozruchowego, zobacz [obrazów rozruchowych Customize](../get-started/customize-boot-images.md). Aby uzyskać więcej informacji na temat obrazów rozruchowych, zobacz [Zarządzanie obrazami rozruchowymi](../get-started/manage-boot-images.md).  

### <a name="windows-server-update-services-wsus"></a>Program Windows Server Update Services (WSUS)  
Należy zainstalować następujące poprawki WSUS 4.0:
  - [Hotfix 3095113](https://support.microsoft.com/kb/3095113) jest niezbędny do obsługi systemu Windows 10, w ramach której używana jest infrastruktura aktualizacji oprogramowania do uzyskania uaktualnień funkcji systemu Windows 10. W przypadku używania programu WSUS 3.2 do uaktualnienia systemu Windows 10 należy użyć sekwencji zadań. Aby uzyskać więcej informacji, zobacz [Zarządzanie systemem Windows jako usługa](../deploy-use/manage-windows-as-a-service.md).  
  - [Poprawka 3159706](https://support.microsoft.com/kb/3159706) trzeba użyć obsługi w celu uaktualnienia komputera do usługi Windows Update rocznice 10, a także podsekwencją wersje systemu Windows 10. Istnieją ręczne wykonanie czynności opisane w artykule pomocy technicznej, że należy wykonać, aby zainstalować tę poprawkę. Aby uzyskać więcej informacji, zobacz [Zarządzanie systemem Windows jako usługa](../deploy-use/manage-windows-as-a-service.md).


### <a name="internet-information-services-iis-on-the-site-system-servers"></a>Internetowe usługi informacyjne (IIS) na serwerach systemu lokacji  
 Program IIS jest wymagany na potrzeby punktu dystrybucji, punktu migracji stanu i punktu zarządzania. Aby uzyskać więcej informacji dotyczących tego wymagania, zobacz [lokacji i wymagań wstępnych systemu lokacji](../../core/plan-design/configs/site-and-site-system-prerequisites.md).  

### <a name="windows-deployment-services-wds"></a>usługami wdrażania systemu Windows (WDS),  
 Usługi wdrażania systemu Windows są wymagane dla wdrożeń PXE, gdy korzysta się z multiemisji do optymalizowania przepustowości w ramach wdrożeń oraz obsługi obrazów w trybie offline. Jeśli dostawca jest zainstalowany na serwerze zdalnym, należy zainstalować usługi wdrażania systemu Windows na serwerze lokacji i dostawcy zdalnym. Więcej informacji zawiera sekcja [Usługi wdrażania systemu Windows](#BKMK_WDS) w tym temacie.  

### <a name="dynamic-host-configuration-protocol-dhcp"></a>Protokół DHCP  
 Dla wdrożeń środowiska PXE wymagany jest protokół DHCP. Aby wdrażać systemy operacyjne, używając środowiska PXE, należy dysponować działającym serwerem DHCP z aktywnym hostem. Aby uzyskać więcej informacji dotyczących wdrożeń środowiska PXE, zobacz [środowiska PXE używany do wdrażania systemu Windows za pośrednictwem sieci](../deploy-use/use-pxe-to-deploy-windows-over-the-network.md).  

### <a name="supported-operating-systems-and-hard-disk-configurations"></a>Obsługiwane systemy operacyjne i konfiguracje dysku twardego  
 Aby uzyskać więcej informacji dotyczących wersji systemu operacyjnego i konfiguracji dysków twardych, które są obsługiwane przez program Configuration Manager w przypadku wdrażania systemów operacyjnych, zobacz [obsługiwanych systemów operacyjnych](#BKMK_SupportedOS) i [obsługiwane konfiguracje dysków](#BKMK_SupportedDiskConfig).  

### <a name="windows-device-drivers"></a>Sterowniki urządzeń dla systemu Windows  
 Sterowników urządzeń dla systemu Windows można użyć w przypadku instalacji systemu operacyjnego na komputerze docelowym i uruchamiania systemu Windows PE za pomocą obrazu rozruchowego. Aby uzyskać więcej informacji o sterownikach urządzeń, zobacz [zarządzania sterownikami](../get-started/manage-drivers.md).  

##  <a name="BKMK_InternalDependencies"></a> Zależności programu Configuration Manager  
 Następujące informacje dotyczące systemu operacyjnego programu Configuration Manager wymagania wstępne dotyczące wdrażania.  

### <a name="operating-system-image"></a>Obraz systemu operacyjnego  
 Obrazy systemu operacyjnego w programie Configuration Manager to pliki w formacie WIM (Windows Imaging) stanowiące skompresowaną kolekcję plików i folderów odniesienia wymaganych do pomyślnej instalacji i konfiguracji systemu operacyjnego na komputerze. Aby uzyskać więcej informacji, zobacz [zarządzania obrazami systemu operacyjnego](../get-started/manage-operating-system-images.md).  

### <a name="driver-catalog"></a>Katalog sterowników  
 Aby wdrożyć sterownik urządzenia, należy zaimportować sterownik urządzenia, włączyć i udostępnić w punkcie dystrybucji, które ma dostęp do klienta programu Configuration Manager. Aby uzyskać więcej informacji o katalogu sterowników, zobacz [zarządzania sterownikami](../get-started/manage-drivers.md).  

### <a name="management-point"></a>Punkt zarządzania  
 Punkty zarządzania przesyłają informacje między komputerami klienckimi a lokacją programu Configuration Manager. Klient korzysta z punktu zarządzania w celu uruchomienia wszystkich sekwencji zadań wymaganych do ukończenia wdrożenia systemu operacyjnego.  

 Aby uzyskać więcej informacji o sekwencjach zadań, zobacz [uwagi dotyczące automatyzacji zadań planowania](planning-considerations-for-automating-tasks.md).  

### <a name="distribution-point"></a>Punkt dystrybucji  
 Punkty dystrybucji są używane w większości wdrożeń do przechowywania danych używanych w celu wdrożenia systemu operacyjnego, na przykład obrazu systemu operacyjnego lub pakietów sterowników urządzeń. Sekwencje zadań zwykle pobierają dane z punktu dystrybucji w celu wdrożenia systemu operacyjnego.  

 Aby uzyskać więcej informacji o instalacji punktów dystrybucji i zarządzaniu zawartością, zobacz [zarządzania infrastrukturą zawartości i](../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

### <a name="pxe-enabled-distribution-point"></a>Punkt dystrybucji z obsługą środowiska PXE  
 Aby wykonać wdrożenia zainicjowane ze środowiska PXE, należy tak skonfigurować punkt dystrybucji, aby akceptował żądania środowiska PXE od klientów. Aby uzyskać więcej informacji o sposobie konfigurowania punktu dystrybucji, zobacz [konfigurowania punktu dystrybucji](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#pxe).  

### <a name="multicast-enabled-distribution-point"></a>Punkt dystrybucji z obsługą multiemisji  
 Aby zoptymalizować wdrożenia systemu operacyjnego, za pomocą multiemisji, należy skonfigurować punkt dystrybucji w celu obsługi multiemisji. Aby uzyskać więcej informacji o sposobie konfigurowania punktu dystrybucji, zobacz [konfigurowania punktu dystrybucji](/sccm/core/servers/deploy/configure/install-and-configure-distribution-points#multicast).   

### <a name="state-migration-point"></a>punkt migracji stanu  
 W przypadku przechwytywania i przywracana danych stanu użytkownika dla wdrożeń równoczesnych i odświeżających należy skonfigurować punkt migracji stanu w celu przechowywania danych stanu użytkownika na innym komputerze.  

 Więcej informacji o sposobie konfigurowania punktu migracji stanu znajduje się w temacie [Punkt migracji stanu](../get-started/prepare-site-system-roles-for-operating-system-deployments.md#BKMK_StateMigrationPoints).  

 Aby uzyskać informacje o sposobie przechwytywania i przywracania stanu użytkownika, zobacz [zarządzania stanem użytkownika](../get-started/manage-user-state.md).  

### <a name="service-connection-point"></a>Punkt połączenia usługi  
 Korzystając z systemu Windows jako usługi (WaaS) do wdrażania bieżącej gałęzi systemu Windows 10, należy mieć zainstalowany punkt połączenia usługi. Aby uzyskać więcej informacji, zobacz [Zarządzanie systemem Windows jako usługa](../deploy-use/manage-windows-as-a-service.md).  

### <a name="reporting-services-point"></a>Punkt usług raportowania  
 Aby używać raportów programu Configuration Manager dla wdrożeń systemu operacyjnego, należy zainstalować i skonfigurować punkt usług raportowania. Aby uzyskać więcej informacji, zobacz [raportowania](../../core/servers/manage/reporting.md).  

### <a name="security-permissions-for-operating-system-deployments"></a>Uprawnienia zabezpieczeń dla wdrożeń systemu operacyjnego  
 Rola zabezpieczeń **Menedżer wdrożenia systemu operacyjnego** jest wbudowana i nie można jej zmienić. Można jednak skopiować rolę, wprowadzić zmiany, a następnie zapisać je jako nową, niestandardową rolę zabezpieczeń. Poniżej podano niektóre uprawnienia, które dotyczą bezpośrednio wdrożeń systemu operacyjnego:  

-   **Pakiet obrazu rozruchowego**: Utwórz, Usuń, Modyfikuj, Modyfikuj Folder, Przenieś obiekt, Odczytaj, ustaw zakres zabezpieczeń  

-   **Sterowniki urządzeń**: Utwórz, Usuń, Modyfikuj, Modyfikuj Folder, Modyfikuj raport, Przenieś obiekt, Odczytaj, uruchom raport  

-   **Pakiet sterowników**: Utwórz, Usuń, Modyfikuj, Modyfikuj Folder, Przenieś obiekt, Odczytaj, ustaw zakres zabezpieczeń  

-   **Obraz systemu operacyjnego**: Utwórz, Usuń, Modyfikuj, Modyfikuj Folder, Przenieś obiekt, Odczytaj, ustaw zakres zabezpieczeń  

-   **Pakiet instalacyjny systemu operacyjnego**: Utwórz, Usuń, Modyfikuj, Modyfikuj Folder, Przenieś obiekt, Odczytaj, ustaw zakres zabezpieczeń  

-   **Pakiet sekwencji zadań**: Utwórz, Utwórz zadanie nośnik sekwencji, Usuń, Modyfikuj, Modyfikuj Folder, Modyfikuj raport, Przenieś obiekt, Odczytaj, uruchom raport, ustaw zakres zabezpieczeń  

 Więcej informacji o niestandardowych rolach zabezpieczeń znajduje się w sekcji [Tworzenie niestandardowych ról zabezpieczeń](../../core/servers/deploy/configure/configure-role-based-administration.md#BKMK_CreateSecRole).  

### <a name="security-scopes-for-operating-system-deployments"></a>Zakresy zabezpieczeń dla wdrożeń systemu operacyjnego  
 Zakresy zabezpieczeń umożliwiają zapewnienie użytkownikom administracyjnym dostępu do obiektów zabezpieczanych używanych we wdrożeniach systemu operacyjnego, takich jak obrazy systemu operacyjnego i obrazy rozruchowe, pakiety sterowników i pakiety sekwencji zadań. Aby uzyskać więcej informacji, zobacz [Zakresy zabezpieczeń](../../core/understand/fundamentals-of-role-based-administration.md#bkmk_PlanScope).  

##  <a name="BKMK_WDS"></a> Usługi wdrażania systemu Windows  
 Usługi wdrażania systemu Windows (WDS) muszą być zainstalowane na tym samym serwerze co punkty dystrybucji konfigurowane do obsługi środowiska PXE lub multiemisji. Usługi wdrażania systemu Windows są zawarte w systemie operacyjnym serwera. W przypadku wdrożeń za pomocą środowiska PXE Usługi wdrażania systemu Windows wykonują rozruch w środowisku PXE. Po zainstalowaniu punktu dystrybucji i włączeniu obsługi środowiska PXE, Configuration Manager instaluje dostawcę do usług wdrażania systemu Windows, który używa funkcji rozruchu w środowisku PXE.  

> [!NOTE]  
>  Jeżeli serwer będzie wymagał ponownego uruchomienia, instalacja Usług wdrażania systemu Windows może zakończyć się niepowodzeniem.  

 Inne konfiguracje Usług wdrażania systemu Windows, które należy uwzględnić, są następujące:  

-   Instalacja Usług wdrażania systemu Windows na serwerze wymaga, aby administrator był członkiem grupy administratorów lokalnych.  

-   Serwer Usług wdrażania systemu Windows musi być członkiem domeny usługi Active Directory lub kontrolera domeny usługi Active Directory. Wszystkie konfiguracje domeny systemu Windows i lasu obsługują Usługi wdrażania systemu Windows.  

-   Jeśli dostawca jest zainstalowany na serwerze zdalnym, należy zainstalować usługi wdrażania systemu Windows na serwerze lokacji i dostawcy zdalnym.  

###  <a name="BKMK_WDSandDHCP"></a> Zagadnienia dotyczące sytuacji, gdy na tym samym serwerze istnieją Usługi wdrażania systemu Windows i protokół DHCP  
 Jeśli punkt dystrybucji ma być obsługiwany również na serwerze z uruchomionym protokołem DHCP, należy wziąć pod uwagę poniższe kwestie konfiguracyjne.  

-   Należy dysponować działającym serwerem DHCP z aktywnym zakresem. Usługi wdrażania systemu Windows korzystają z środowiska PXE, które wymaga serwera DHCP.  

-   Protokół DHCP i usługa wdrażania systemu Windows wymagają portu numer 67. W przypadku jednoczesnego hostowania serwera DHCP i usług wdrażania systemu Windows serwer DHCP lub punkt dystrybucji skonfigurowany do obsługi środowiska PXE można przenieść na oddzielny serwer. Można również użyć poniższej procedury, aby skonfigurować serwer usług wdrażania systemu Windows do nasłuchiwania na innym porcie.  

    #### <a name="to-configure-the-windows-deployment-services-server-to-listen-on-a-different-port"></a>Aby skonfigurować serwer usług wdrażania systemu Windows do nasłuchiwania na innym porcie  

    1.  Zmień poniższy klucz rejestru:  

         **HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\WDSServer\Providers\WDSPXE**  

    2.  Ustaw wartość rejestru na: **UseDHCPPorts = 0**  

    3.  Aby nowa konfiguracja została zastosowana, uruchom na serwerze poniższe polecenie:  

         `WDSUTIL /Set-Server /UseDHCPPorts:No /DHCPOption60:Yes`  

-   Do pracy usług wdrażania systemu Windows jest wymagany serwer DNS.  

-   Na serwerze usług wdrażania systemu Windows muszą być otwarte poniższe porty UDP.  

    -   Port 67 (DHCP)  

    -   Port 69 (TFTP)  

    -   Port 4011 (PXE)  

    > [!NOTE]  
    >  Jeśli dodatkowo na serwerze jest wymagana autoryzacja DHCP, na serwerze musi być otwarty port numer 68 klienta DHCP.  

##  <a name="BKMK_SupportedOS"></a> Obsługiwane systemy operacyjne  
 Wszystkie systemy operacyjne Windows wyświetlane jako obsługiwane systemy operacyjne klienta w [obsługiwanych systemów operacyjnych dla klientów i urządzeń](../../core/plan-design/configs/supported-operating-systems-for-clients-and-devices.md) są obsługiwane w przypadku wdrożeń systemu operacyjnego.  

##  <a name="BKMK_SupportedDiskConfig"></a> Obsługiwane konfiguracje dysków  
 W poniższej tabeli przedstawiono kombinacje konfiguracji dysków twardych w komputerach referencyjnych i docelowych, które są obsługiwane w przypadku wdrażania systemu operacyjnego programu Configuration Manager.  

|Konfiguracja dysków twardych komputera referencyjnego|Konfiguracja dysków twardych komputera docelowego|  
|------------------------------------------------|--------------------------------------------------|  
|Dysk podstawowy|Dysk podstawowy|  
|Wolumin prosty na dysku dynamicznym|Wolumin prosty na dysku dynamicznym|  

 Program Configuration Manager obsługuje przechwytywanie obrazu systemu operacyjnego tylko na komputerach, które są skonfigurowane przy użyciu woluminów prostych. Następujące konfiguracje dysków twardych nie są obsługiwane:  

-   woluminy łączone,  

-   woluminy rozłożone (RAID 0),  

-   woluminy dublowane (RAID 1),  

-   woluminy z parzystością (RAID 5).  

 Poniższa tabela zawiera dodatkową konfigurację dysków w komputerach referencyjnych i docelowych, które jest nieobsługiwane w przypadku wdrażania systemu operacyjnego programu Configuration Manager.  

|Konfiguracja dysków twardych komputera referencyjnego|Konfiguracja dysków twardych komputera docelowego|  
|------------------------------------------------|--------------------------------------------------|  
|Dysk podstawowy|Dysk dynamiczny|  

## <a name="next-steps"></a>Następne kroki
[Przygotowanie do wdrożenia systemu operacyjnego](../get-started/prepare-for-operating-system-deployment.md)
