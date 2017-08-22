---
title: "Obsługiwane klientów i urządzeń | Dokumentacja firmy Microsoft"
description: "Dowiedz się, które systemy operacyjne, w programie System Center Configuration Manager obsługuje klientów i urządzeń."
ms.custom: na
ms.date: 8/16/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 87f4e041-67df-4c61-aa98-7444faffe565
caps.latest.revision: "5"
author: arob98
ms.author: angrobe
manager: angrobe
ms.openlocfilehash: 82be9b005ec87199f3191612f720f4cc267a4e5c
ms.sourcegitcommit: db7b7ec347638efd05cdba474e8a8f8535516116
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/16/2017
---
# <a name="supported-operating-systems-for-clients-and-devices-for-system-center-configuration-manager"></a>Obsługiwane systemy operacyjne dla klientów i urządzeń dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*


 System Center Configuration Manager obsługuje instalowanie oprogramowania klienckiego na różnych komputerach z systemem Windows, Mac, Linux i UNIX.  

 **Wymagania i ograniczenia dotyczące wszystkich klientów:**  

-   Zmiana typu uruchamiania lub **Zaloguj się jako** ustawienia dla dowolnego programu Configuration Manager service nie jest obsługiwana i może uniemożliwić klucza usługi z poprawnie działać.    

-   Instalowanie i uruchamianie klienta programu Configuration Manager dla systemu Linux lub UNIX albo klienta dla komputerów Mac na komputerach przy użyciu konta innego niż główny nie jest obsługiwane. Dzięki temu można uniemożliwić prawidłowe działanie najważniejszych usług.  

##  <a name="windows-computers"></a>Komputery z systemem Windows  
 Można użyć klienta programu Configuration Manager dostępnej w programie Configuration Manager do zarządzania następujących systemów operacyjnych Windows. Aby uzyskać więcej informacji, zobacz [jak wdrożyć klientów na komputerach z systemem Windows w programie System Center Configuration Manager](../../../core/clients/deploy/deploy-clients-to-windows-computers.md).  

**Obsługiwane systemy operacyjne:**  


-  **Windows Server 2016**: Standard, Datacenter <sup>1</sup>
  - Ten system operacyjny jest obsługiwany począwszy od 1606 wersji programu Configuration Manager, z pakiet zbiorczy poprawek z KB3186654 (lub wersji linii bazowej 1606, wydanej w października 2016).  

-   **Windows Server 2012 R2** (x64): Standard, Datacenter <sup>1</sup>    

-   **Windows Storage Server 2012 R2** (x64)    

-   **Windows Server 2012** (x64): Standard, Datacenter <sup>1</sup>    

-   **Windows Storage Server 2012** (x64)    

-   **Windows Server 2008 R2 z dodatkiem SP1** (x64): Standard, Enterprise i Datacenter <sup>1</sup>    

-   **Windows Storage Server 2008 R2** (x86, x64): Workgroup, Standard i Enterprise    

-   **Windows Server 2008 z dodatkiem SP2** (x86, x64): Standard, Enterprise i Datacenter <sup>1</sup>    

-   **Windows 10**: Pro i Enterprise  
   Zobacz [pomocy technicznej dla wersji systemu Windows 10](/sccm/core/plan-design/configs/support-for-windows-10) szczegółowe informacje o różnych wersji systemu Windows 10 obsługiwanych przez różne wersje programu Configuration Manager.

-   **Windows 8.1** (x86, x64): Professional, Enterprise    

-   **Windows 8** (x86, x64): Professional, Enterprise    

-   **Windows 7 z dodatkiem SP1** (x86, x64): Professional, Enterprise i Ultimate    

-   **Instalacja Server Core systemu Windows Server 2016** (x64) <sup>2</sup>
  - Ten system operacyjny jest obsługiwany począwszy od wersji 1606 z pakiet zbiorczy poprawek z KB3186654 (lub wersji linii bazowej 1606, wydanej w października 2016).


-   **Instalacja Server Core systemu Windows Server 2012 R2** (x64) <sup>2</sup>    

-   **Instalacja Server Core systemu Windows Server 2012** (x64) <sup>2</sup>    

-   **Instalacja Server Core systemu Windows Server 2008 R2**  
    **(bez dodatku service pack lub z dodatkiem SP1)**  (x64)    

-   **Instalacja Server Core systemu Windows Server 2008 z dodatkiem SP2** (x86, x64)  

 <sup>1</sup> wersje Datacenter są obsługiwane, ale nie są certyfikowane dla programu Configuration Manager. Obsługa poprawek nie jest oferowany problemów, które są specyficzne dla systemu Windows Server Datacenter Edition.  

 <sup>2</sup> do obsługi instalacji wypychanej klienta, komputera, na którym działa ta wersja systemu operacyjnego należy uruchomić usługę roli serwera plików dla roli serwera usług plików i magazynowania. Aby uzyskać informacji na temat instalowania funkcji systemu Windows na komputerze instalacja Server Core, zobacz [instalowania ról i funkcji serwera na serwerze Server Core](http://go.microsoft.com/fwlink/p/?LinkId=299359) w bibliotece TechNet systemu Windows Server 2012.  


##  <a name="windows-embedded-computers"></a>Komputery z systemem Windows Embedded  
 Instalując oprogramowanie klienta programu Configuration Manager na urządzeniu można zarządzać urządzeniami Windows Embedded.  Aby uzyskać więcej informacji, zobacz [Planowanie wdrożenia klientów na urządzeniach Windows Embedded w programie System Center Configuration Manager](../../../core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices.md).  

**Wymagania i ograniczenia:**  

-   Wszystkie funkcje klienta są obsługiwane przez system Windows Embedded systemów, które nie mają włączonych filtrów zapisu.  

-   Wszystkich funkcji oprócz zarządzania energią obsługuje klientów korzystających z jednego z następujących czynności:  

    -   Rozszerzone filtry zapisu (EWF)    

    -   Filtrów zapisu opartych na plikach pamięci RAM (FBWF)    

    -   Ujednolicone filtry zapisu (UWF)  

-   Wykaz aplikacji nie jest obsługiwany na urządzeniach z systemem Windows Embedded.  

-   Przed można monitorować wykryte złośliwe oprogramowanie na urządzeniach Windows Embedded, które są oparte na systemie Windows XP, należy zainstalować pakiet skryptów Microsoft Windows WMI na urządzeniu. Windows Embedded Target Designer należy zainstalować ten pakiet.
Pliki **WBEMDISP. Biblioteki DLL** i **WBEMDISP. TLB** musi istnieć i być zarejestrowane w folderze **%windir%\System32\WBEM** na urządzeniu osadzonym w celu zapewnienia wykrytego złośliwego oprogramowania.  

**Obsługiwane systemy operacyjne:**  

-   **Windows 10 Enterprise** (x86, x64)  

-   **Windows 10 Enterprise IoT** (x86, x64)  

-   **Windows Embedded 8.1 Industry** (x86, x64)    

-   **System Windows Embedded 8 Industry** (x86, x64)    

-   **Windows Embedded 8 Standard** (x86, x64)    

-   **Windows Embedded 8 Pro** (x86, x64)    

-   **Windows elastycznej PC** (x86, x64)    

-   **Windows Embedded POSReady 7** (x86, x64)    

-   **Windows Embedded Standard 7 z dodatkiem SP1** (x86, x64)    

Następujące systemy operacyjne są oparte na systemie Windows XP Embedded i obsługiwane tylko z 1610 wersji programu Configuration Manager i wcześniejszych. [Począwszy od wersji 1702, te osadzone systemy operacyjne nie są już obsługiwane](/sccm/core/plan-design/changes/removed-and-deprecated-features#client-operating-systems).  

-   **WEPOS 1.1 z dodatkiem SP3** (x86)    

-   **Windows Embedded POSReady 2009** (x86)    

-   **Windows Fundamentals dla starszych komputerów (WinFLP)** (x86)    

-   **Windows XP Embedded z dodatkiem SP3** (x86)    

-   **Windows Embedded Standard 2009** (x86)  

## <a name="windows-ce-computers"></a>Komputery z systemem Windows CE
 Urządzenia z systemem Windows CE można zarządzać w programie Configuration Manager starszego klienta urządzenia przenośnego dostępnej w programie Configuration Manager.  

**Wymagania i ograniczenia**  

-   Klient urządzenia przenośnego wymaga 0,78 MB miejsca do magazynowania dla instalacji. Logowania może wymagać do 256 KB dodatkowego miejsca.    

-   Funkcje dotyczące tych urządzeń przenośnych zależą od platformy i klienta typu. Aby uzyskać informacje dotyczące zarządzania, które funkcje są obsługiwane, zobacz [wybór rozwiązania do zarządzania urządzeniami programu System Center Configuration Manager](../../../core/plan-design/choose-a-device-management-solution.md).  

**Obsługiwane systemy operacyjne:**  

-   Windows CE 7.0 (ARM i x86 procesorów)  

**Obsługiwane języki:**  

-   Chiński (uproszczony i tradycyjny)    

-   Angielski (USA)    

-   Francuski (Francja)    

-   niemiecki    

-   włoski    

-   japoński  

-   koreański  

-   portugalski (Brazylia)  

-   rosyjski  

-   Hiszpański (Hiszpania)  

## <a name="mac-computers"></a>Komputery Mac  
 Można zarządzać komputerami Mac OS X przy użyciu klienta programu Configuration Manager dla komputerów Mac.  

 Pakiet instalacyjny klienta Mac nie jest dostarczany na nośnikach programu Configuration Manager. Pobierz **klienci dla dodatkowych systemów operacyjnych** z [Centrum pobierania Microsoft](http://go.microsoft.com/fwlink/?LinkID=525184).  

 Aby uzyskać więcej informacji, zobacz [jak wdrożyć klientów na komputerach Mac w programie System Center Configuration Manager](../../../core/clients/deploy/deploy-clients-to-macs.md).  

**Obsługiwane wersje:**  

-   **System Mac OS X 10.6** (śniegu Leopard)

-   **System Mac OS X 10,7** (Lion)

-   **System Mac OS X 10.8** (Mountain Lion)

-   **System Mac OS X 10.9** (Mavericks)

-   **System Mac OS X 10.10** (Yosemite)  

-   **System Mac OS X 10.11** (El Capitan)  

-   **Mac OS X 10.12** (macOS Sierra)

##  <a name="linux-and-unix-servers"></a>Serwery z systemami Linux i UNIX  
 Serwery z systemami Linux i UNIX można zarządzać przy użyciu klienta programu Configuration Manager dla systemów Linux i UNIX.  

 Instalacja klienta systemów Linux i UNIX, pakiety nie są dostarczane na nośnikach programu Configuration Manager. Pobierz **klienci dla dodatkowych systemów operacyjnych** z [Centrum pobierania Microsoft](http://go.microsoft.com/fwlink/?LinkID=525184). Oprócz pakietów instalacyjnych klienta pobranie klienta obejmuje skrypt, który służy do zarządzania instalacją klienta na każdym komputerze.  

**Wymagania i ograniczenia:**  

-   Aby przejrzeć zależnościach plików systemów operacyjnych klienta dla systemów Linux i UNIX, zobacz [wymagania wstępne dotyczące wdrażania klientów na serwerach Linux i UNIX](../../../core/clients/deploy/plan/planning-for-client-deployment-to-linux-and-unix-computers.md#BKMK_ClientDeployPrereqforLnU).  

-   Omówienie funkcji zarządzania obsługiwanych dla systemu Linux lub UNIX, zobacz [jak wdrożyć klientów na serwerach UNIX i Linux w programie System Center Configuration Manager](../../../core/clients/deploy/deploy-clients-to-unix-and-linux-servers.md).  

-   W przypadku obsługiwanych wersji systemów Linux i UNIX wymieniona wersja obejmuje wszystkie kolejne wersje pomocnicze. Na przykład CentOS w wersji 6 zawiera CentOS 6.3. Podobnie Obsługa systemu operacyjnego że używa dodatków service pack (na przykład SUSE Linux Enterprise Server 11 z dodatkiem SP1) zawiera kolejne dodatki service Pack dla danej wersji systemu operacyjnego.  

-   Aby uzyskać informacji na temat pakietów instalacyjnych klienta i agenta uniwersalnego, zobacz [jak wdrożyć klientów na serwerach UNIX i Linux w programie System Center Configuration Manager](../../../core/clients/deploy/deploy-clients-to-unix-and-linux-servers.md).  

**Obsługiwane wersje:** Obsługiwane są następujące wersje przy użyciu podanego pliku tar.  

### <a name="aix"></a>AIX  

|||  
|-|-|  
|W wersji 5.3 (Power)|CCM-Aix53ppc. &lt;kompilacji\>tar|  
|W wersji 6.1 (Power)|CCM-Aix61ppc. &lt;kompilacji\>tar|  
|W wersji 7.1 (Power)|CCM-Aix71ppc. &lt;kompilacji\>tar|  

### <a name="centos"></a>CentOS  

|||  
|-|-|  
|W wersji 5 x86|CCM-Universalx86. &lt;kompilacji\>tar|  
|W wersji 5 x64|CCM-Universalx64. &lt;kompilacji\>tar|  
|W wersji 6 x86|CCM-Universalx86. &lt;kompilacji\>tar|  
|W wersji 6 x64|CCM-Universalx64. &lt;kompilacji\>tar|  
|Wersja 7 x64|CCM-Universalx64. &lt;kompilacji\>tar|  

### <a name="debian"></a>Debian  

|||  
|-|-|  
|W wersji 5 x86|CCM-Universalx86. &lt;kompilacji\>tar|  
|W wersji 5 x64|CCM-Universalx64. &lt;kompilacji\>tar|  
|W wersji 6 x 86|CCM-Universalx86. &lt;kompilacji\>tar|  
|W wersji 6 x64|CCM-Universalx64. &lt;kompilacji\>tar|  
|Wersja 7 x86|CCM-Universalx86. &lt;kompilacji\>tar|  
|Wersja 7 x64|CCM-Universalx64. &lt;kompilacji\>tar|  
|W wersji 8 x86|CCM-Universalx86. &lt;kompilacji\>tar|  
|W wersji 8 x64|CCM-Universalx64. &lt;kompilacji\>tar|  

### <a name="hp-ux"></a>HP-UX  

|||  
|-|-|  
|Wersja 11iv2 IA64|CCM-HpuxB.11.23i64. &lt;kompilacji\>tar|  
|Wersja 11iv2 PA-RISC|CCM-HpuxB.11.23PA. &lt;kompilacji\>tar|  
|Wersja 11iv3 IA64|CCM-HpuxB.11.31i64. &lt;kompilacji\>tar|  
|Wersja 11iv3 PA-RISC|CCM-HpuxB.11.31PA. &lt;kompilacji\>tar|  

### <a name="oracle-linux"></a>Oracle Linux  

|||  
|-|-|  
|W wersji 5 x86|CCM-Universalx86. &lt;kompilacji\>tar|  
|W wersji 5 x64|CCM-Universalx64. &lt;kompilacji\>tar|  
|W wersji 6 x86|CCM-Universalx86. &lt;kompilacji\>tar|  
|W wersji 6 x64|CCM-Universalx64. &lt;kompilacji\>tar|  
|Wersja 7 x64|CCM-Universalx64. &lt;kompilacji\>tar|  

### <a name="red-hat-enterprise-linux-rhel"></a>Red Hat Enterprise Linux (RHEL)  

|||  
|-|-|  
|W wersji 4 x86|CCM-RHEL4x86. &lt;kompilacji\>tar|  
|W wersji 4 x64|CCM-RHEL4x64. &lt;kompilacji\>tar|  
|W wersji 5 x86|CCM-Universalx86. &lt;kompilacji\>tar|  
|W wersji 5 x64|CCM-Universalx64. &lt;kompilacji\>tar|  
|W wersji 6 x86|CCM-Universalx86. &lt;kompilacji\>tar|  
|W wersji 6 x64|CCM-Universalx64. &lt;kompilacji\>tar|  
|Wersja 7 x64|CCM-Universalx64. &lt;kompilacji\>tar|  

### <a name="solaris"></a>Solaris  

|||  
|-|-|  
|W wersji 9 SPARC|CCM-Sol9sparc. &lt;kompilacji\>tar|  
|W wersji 10 x86|CCM-Sol10x86. &lt;kompilacji\>tar|  
|W wersji 10 SPARC|CCM-Sol10sparc. &lt;kompilacji\>tar|  
|W wersji 11 x86|CCM-Sol11x86. &lt;kompilacji\>tar|  
|W wersji 11 SPARC|CCM-Sol11sparc. &lt;kompilacji\>tar|  

### <a name="suse-linux-enterprise-server-sles"></a>SUSE Linux Enterprise Server (SLES)  

|||  
|-|-|  
|W wersji 9 x86|CCM-SLES9x86. &lt;kompilacji\>tar|  
|Z dodatkiem SP1 w wersji 10 x86|CCM-Universalx86. &lt;kompilacji\>tar|  
|Z dodatkiem SP1 w wersji 10 x64|CCM-Universalx64. &lt;kompilacji\>tar|  
|Z dodatkiem SP1 w wersji 11 x86|CCM-Universalx86. &lt;kompilacji\>tar|  
|Z dodatkiem SP1 w wersji 11 x64|CCM-Universalx64. &lt;kompilacji\>tar|  
|W wersji 12 x64|CCM-Universalx64. &lt;kompilacji\>tar|  

### <a name="ubuntu"></a>Ubuntu  

|||  
|-|-|  
|Wersja 10.04 LTS x86|CCM-Universalx86. &lt;kompilacji\>tar|  
|Wersja 10.04 LTS x64|CCM-Universalx64. &lt;kompilacji\>tar|  
|Wersja 12.04 LTS x86|CCM-Universalx86. &lt;kompilacji\>tar|  
|Wersja 12.04 LTS x64|CCM-Universalx64. &lt;kompilacji\>tar|  
|Wersja 14.04 LTS x86|CCM-Universalx86. &lt;kompilacji\>tar|  
|Wersja 14.04 LTS x64|CCM-Universalx64. &lt;kompilacji\>tar|  

##  <a name="mobile-devices-enrolled-by-microsoft-intune"></a>Urządzenia przenośne zarejestrowane przez program Microsoft Intune  
 Aby uzyskać szczegółowe informacje dotyczące komputerów i urządzeń, którymi można zarządzać po zintegrowaniu programu Microsoft Intune z programem Configuration Manager Zobacz dwa następujące tematy w bibliotece dokumentacji programu Microsoft Intune:  

-   [Możliwości zarządzania urządzeniami przenośnymi w programie Microsoft Intune](https://docs.microsoft.com/intune/get-started/choose-how-to-manage-devices)  
-   [Możliwości zarządzania Komputerami z systemem Windows w Microsoft Intune](https://docs.microsoft.com/intune/get-started/windows-pc-management-capabilities-in-microsoft-intune)  

##  <a name="bkmk_OnpremOS"></a>W ramach lokalnego zarządzania urządzeniami przenośnymi  
 Configuration Manager ma wbudowane funkcje zarządzania urządzeniami, które są lokalnymi bez konieczności instalowania oprogramowania klienta.  Aby uzyskać więcej informacji, zobacz [zarządzanie urządzeniami przenośnymi za pomocą infrastruktury lokalnej w programie System Center Configuration Manager](../../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md).  

 **Wymagania i ograniczenia:**  

-   Należy skonfigurować **punkt połączenia z usługą** w lokacji najwyższego poziomu w hierarchii.  

**Obsługiwane systemy operacyjne:**  

- **Windows 10 Pro** (x86, x64)  

- **Windows 10 Enterprise Pro** (x86, x64)  

- **Windows 10 Enterprise IoT** (x86, x64)

- **Windows 10 Mobile**  

- **Windows 10 Enterprise przenośnych**  

- **Windows 10 Enterprise IoT Mobile**

- **System Windows 10 Team dla powierzchni Centrum**

##  <a name="bkmk_ExSrvConOS"></a>Łącznik serwera Exchange  
Program Configuration Manager obsługuje ograniczone Zarządzanie urządzeń łączących się z serwerem Exchange, bez konieczności instalowania klienta programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [Zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i Exchange](../../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md).  

 **Wymagania i ograniczenia:**  

-   Configuration Manager oferuje ograniczone zarządzanie urządzeniami przenośnymi, gdy używasz urządzenia z łącznika serwera Exchange dla programu Exchange Active Sync, które nawiązują połączenie z serwerem z systemem Exchange Server lub Exchange Online.  

-   Aby uzyskać więcej informacji na temat funkcji zarządzania, które program Configuration Manager obsługuje dla urządzeń przenośnych zarządzanych przez łącznik serwera Exchange, zobacz Określanie sposobu zarządzania urządzeniami przenośnymi w programie Configuration Manager.  

**Obsługiwane wersje programu Exchange Server:**  

-   **Exchange Server 2010 z dodatkiem SP1**  

-   **Exchange Server 2010 z dodatkiem SP2**  

-   **Program Exchange Server 2013**  

-   **Exchange Online (Office 365)**: Dotyczy to również Business Productivity Online Standard Suite  
