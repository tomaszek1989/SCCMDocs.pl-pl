---
title: "Obsługiwane klientów i urządzeń | Dokumentacja firmy Microsoft"
description: "Dowiedz się, które systemy operacyjne, System Center Configuration Manager obsługuje klientów i urządzeń."
ms.custom: na
ms.date: 2/6/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 87f4e041-67df-4c61-aa98-7444faffe565
caps.latest.revision: 5
author: arob98
ms.author: angrobe
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d5166b16ffbe46af561b1ce98c0494cc4aaa72a8
ms.openlocfilehash: cd7b8bf35aeb26c8b7b37f6faa51c9a09138fdb9
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017

---
# <a name="supported-operating-systems-for-clients-and-devices-for-system-center-configuration-manager"></a>Obsługiwane systemy operacyjne klientów i urządzeń dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*


 System Center Configuration Manager obsługuje instalowanie oprogramowania klienckiego na różnych komputerach z systemem Windows, Mac, Linux i UNIX.  

 **Wymagania i ograniczenia dotyczące wszystkich klientów:**  

-   Zmiana typu uruchomienia lub **Zaloguj się jako** ustawienia dla dowolnego programu Configuration Manager service nie jest obsługiwane i może uniemożliwić klucza usługi poprawne działanie.    

-   Instalowanie i uruchamianie klienta programu Configuration Manager dla systemu Linux lub UNIX albo klienta dla komputerów Mac na komputerach przy użyciu konta innego niż główny nie jest obsługiwane. To może uniemożliwić poprawne działanie usługi klucza.  

##  <a name="windows-computers"></a>Komputery z systemem Windows  
 Można użyć klienta programu Configuration Manager dostępnej w programie Configuration Manager do zarządzania następującymi systemami operacyjnymi Windows. Aby uzyskać więcej informacji, zobacz [wdrażanie klientów na komputerach z systemem Windows w programie System Center Configuration Manager](../../../core/clients/deploy/deploy-clients-to-windows-computers.md).  

**Obsługiwane systemy operacyjne:**  


-  **Windows Server 2016**: Standard, Datacenter <sup>1</sup>
  - Ten system operacyjny jest obsługiwany, począwszy od 1606 wersji programu Configuration Manager, z listą poprawkę z KB3186654 (lub wersja referencyjna 1606, opublikowanym w 2016 października).  

-   **Windows Server 2012 R2** (x64): Standard, Datacenter <sup>1</sup>    

-   **Windows Storage Server 2012 R2** (x64)    

-   **Windows Server 2012** (x64): Standard, Datacenter <sup>1</sup>    

-   **Windows Storage Server 2012** (x64)    

-   **Windows Server 2008 R2 z dodatkiem SP1** (x64): Standard, Enterprise i Datacenter <sup>1</sup>    

-   **Windows Storage Server 2008 R2** (x86, x64): Grupa robocza, Standard, Enterprise    

-   **Windows Server 2008 z dodatkiem SP2** (x86, x64): Standard, Enterprise i Datacenter <sup>1</sup>    

-   **Windows 10**: Pro i Enterprise  
   Zobacz [obsługę wersji systemu Windows 10](/sccm/core/plan-design/configs/support-for-windows-10) szczegółowe informacje na temat różnych wersji systemu Windows 10 obsługiwanych przez różne wersje programu Configuration Manager.

-   **Windows 8.1** (x86, x64): Professional, Enterprise    

-   **Windows 8** (x86, x64): Professional, Enterprise    

-   **Windows 7 z dodatkiem SP1** (x86, x64): Professional, Enterprise i Ultimate    

-   **Instalacja Server Core systemu Windows Server 2016** (x64) <sup>2</sup>
  - Ten system operacyjny jest obsługiwany, począwszy od wersji 1606 z listą poprawkę z KB3186654 (lub wersja referencyjna 1606, opublikowanym w października 2016). 


-   **Instalacja Server Core systemu Windows Server 2012 R2** (x64) <sup>2</sup>    

-   **Instalacja Server Core systemu Windows Server 2012** (x64) <sup>2</sup>    

-   **Instalacja Server Core systemu Windows Server 2008 R2**  
    **(bez dodatku service pack lub z dodatkiem SP1)**  (x64)    

-   **Instalacja Server Core systemu Windows Server 2008 z dodatkiem SP2** (x86, x64)  

 <sup>1</sup> wersji Centrum danych są obsługiwane, lecz nie ma certyfikatu dla programu Configuration Manager. Obsługa poprawek nie jest oferowana problemy, które są specyficzne dla systemu Windows Server Datacenter Edition.  

 <sup>2</sup> do obsługi instalacji wypychanej klienta, na komputerze z tą wersją systemu operacyjnego należy uruchomić usługę roli serwera plików dla roli serwera usługi plików i magazynowania. Informacje o instalowaniu funkcji systemu Windows na komputerze instalacja Server Core, zobacz [instalowania ról i funkcji serwera na serwera Server Core](http://go.microsoft.com/fwlink/p/?LinkId=299359) w bibliotece TechNet programu Windows Server 2012.  


##  <a name="windows-embedded-computers"></a>Komputery z systemem Windows Embedded  
 Instalując oprogramowanie klienta programu Configuration Manager na urządzeniu można zarządzać urządzeniami z systemem Windows Embedded.  Aby uzyskać więcej informacji, zobacz [Planowanie wdrożenia klientów na urządzeniach Windows Embedded w programie System Center Configuration Manager](../../../core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices.md).  

**Wymagania i ograniczenia:**  

-   Wszystkie funkcje klienta są obsługiwane w Windows Embedded systems, które nie mają włączone filtry zapisu.  

-   Obsługiwane są wszystkie funkcje z wyjątkiem zarządzania energią klientów korzystających z jedną z następujących:  

    -   Rozszerzone filtry zapisu (EWF)    

    -   Pamięć RAM filtry zapisu oparte na plikach (FBWF)    

    -   Filtry zapisu Unified (UWF)  

-   Katalog aplikacji nie jest obsługiwane dla urządzeń Windows Embedded.  

-   Przed można monitorować wykrytego złośliwego oprogramowania na urządzeniach Windows Embedded, które są oparte na systemie Windows XP, należy zainstalować pakiet skryptów systemu Microsoft Windows WMI na urządzeniu. Windows Embedded docelowy Designer należy zainstalować ten pakiet.
Pliki **WBEMDISP. Biblioteka DLL** i **WBEMDISP. TLB** musi istnieć i być zarejestrowana w folderze **%windir%\System32\WBEM** na urządzeniu osadzonym w celu zapewnienia wykryte złośliwe oprogramowanie jest raportowana.  

**Obsługiwane systemy operacyjne:**  

-   **System Windows 10 Enterprise** (x86, x64)  

-   **System Windows 10 Enterprise IoT** (x86, x64)  

-   **Windows Embedded 8.1 Industry** (x86, x64)    

-   **System Windows Embedded 8 Industry** (x86, x64)    

-   **Windows Embedded 8 Standard** (x86, x64)    

-   **Windows Embedded 8 Pro** (x86, x64)    

-   **Windows zubożonych PC** (x86, x64)    

-   **Windows Embedded POSReady 7** (x86, x64)    

-   **Windows Embedded Standard 7 z dodatkiem SP1** (x86, x64)    

-   **WEPOS 1.1 z dodatkiem SP3** (x86)    

-   **Windows Embedded POSReady 2009** (x86)    

-   **Narzędzie Windows Fundamentals dla starszych komputerów PC (WinFLP)** (x86)    

-   **Windows XP Embedded z dodatkiem SP3** (x86)    

-   **Windows Embedded Standard 2009** (x86)  

## <a name="windows-ce-computers"></a>Komputery z systemem Windows CE
 Urządzenia systemu Windows CE można zarządzać w programie Configuration Manager starszego klienta urządzenia przenośnego dostępnej w programie Configuration Manager.  

**Wymagania i ograniczenia**  

-   Klient urządzenia przenośnego wymaga 0.78 MB miejsca do magazynowania dla instalacji. Logowanie może wymagać dodatkowego miejsca do 256 KB.    

-   Funkcje dla tych urządzeń przenośnych różnią się zależnie od platformy i klient typu. Aby uzyskać informacje dotyczące zarządzania, z którym funkcje są obsługiwane, zobacz [wybierz rozwiązanie do zarządzania urządzeniami programu System Center Configuration Manager](../../../core/plan-design/choose-a-device-management-solution.md).  

**Obsługiwane systemy operacyjne:**  

-   Windows CE 7.0 (ARM i x86 procesorów)  

**Obsługiwane języki obejmują:**  

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
 Można zarządzać komputerami Mac OS X z klienta programu Configuration Manager dla komputerów Macintosh.  

 Pakiet instalacyjny klienta Mac nie znajduje się na nośniku programu Configuration Manager. Pobierz **klientów dla innych systemów operacyjnych** z [Centrum pobierania Microsoft](http://go.microsoft.com/fwlink/?LinkID=525184).  

 Aby uzyskać więcej informacji, zobacz [sposobu wdrażania klientów w programie System Center Configuration Manager Mac](../../../core/clients/deploy/deploy-clients-to-macs.md).  

**Obsługiwane wersje:**  

-   **Mac OS X 10.6** (śniegu Leopard)

-   **Mac OS X 10,7** (dużą)

-   **Mac OS X 10.8** (górski dużą)

-   **Mac OS X 10.9** (Mavericks)

-   **Mac OS X 10.10** (Yosemite)  

-   **Mac OS X 10.11** (El Capitan)  

-   **Mac OS X 10.12** (macOS Sierra)

##  <a name="linux-and-unix-servers"></a>Serwery z systemem Linux i UNIX  
 Serwery z systemem Linux i UNIX można zarządzać przy użyciu klienta programu Configuration Manager dla systemu Linux i UNIX.  

 Instalacji klienta z systemem Linux i UNIX, to pakiety, które nie są dostarczane z nośnika programu Configuration Manager. Pobierz **klientów dla innych systemów operacyjnych** z [Centrum pobierania Microsoft](http://go.microsoft.com/fwlink/?LinkID=525184). Oprócz pakietów instalacyjnych klienta pobierania klienta obejmuje skrypt, który zarządza instalacją klienta na każdym komputerze.  

**Wymagania i ograniczenia:**  

-   Aby przejrzeć zależności plików systemu operacyjnego klienta dla systemu Linux i UNIX, zobacz [wymagania wstępne dotyczące wdrażania klientów na serwerach Linux i UNIX](../../../core/clients/deploy/plan/planning-for-client-deployment-to-linux-and-unix-computers.md#BKMK_ClientDeployPrereqforLnU).  

-   Omówienie funkcji zarządzania obsługiwanych dla systemu UNIX lub Linux, zobacz [wdrażanie klientów do serwerów systemu UNIX i Linux w programie System Center Configuration Manager](../../../core/clients/deploy/deploy-clients-to-unix-and-linux-servers.md).  

-   W przypadku obsługiwanych wersji systemów UNIX i Linux wymienionych wersji obejmuje wszystkie kolejne wersje pomocnicze. Na przykład CentOS w wersji 6 zawiera CentOS 6.3. Podobnie obsługę systemu operacyjnego, że używa dodatków service pack (na przykład SUSE Linux Enterprise Server 11 z dodatkiem SP1) zawiera kolejnymi dodatkami service Pack dla danej wersji systemu operacyjnego.  

-   Informacje dotyczące pakietów instalacyjnych klienta i agenta uniwersalnego, zobacz [wdrażanie klientów do serwerów systemu UNIX i Linux w programie System Center Configuration Manager](../../../core/clients/deploy/deploy-clients-to-unix-and-linux-servers.md).  

**Obsługiwane wersje:** Obsługiwane są następujące wersje przy użyciu .tar wskazanego pliku.  

### <a name="aix"></a>AIX  

|||  
|-|-|  
|Wersja 5.3 (Power)|CCM-Aix53ppc. &lt;kompilacji\>.tar|  
|W wersji 6.1 (Power)|CCM-Aix61ppc. &lt;kompilacji\>.tar|  
|W wersji 7.1 (Power)|CCM-Aix71ppc. &lt;kompilacji\>.tar|  

### <a name="centos"></a>CentOS  

|||  
|-|-|  
|W wersji 5 x86|CCM-Universalx86. &lt;kompilacji\>.tar|  
|W wersji 5 x64|CCM-Universalx64. &lt;kompilacji\>.tar|  
|W wersji 6 x86|CCM-Universalx86. &lt;kompilacji\>.tar|  
|W wersji 6 x64|CCM-Universalx64. &lt;kompilacji\>.tar|  
|W wersji 7 x64|CCM-Universalx64. &lt;kompilacji\>.tar|  

### <a name="debian"></a>Debian  

|||  
|-|-|  
|W wersji 5 x86|CCM-Universalx86. &lt;kompilacji\>.tar|  
|W wersji 5 x64|CCM-Universalx64. &lt;kompilacji\>.tar|  
|W wersji 6 x 86|CCM-Universalx86. &lt;kompilacji\>.tar|  
|W wersji 6 x64|CCM-Universalx64. &lt;kompilacji\>.tar|  
|W wersji 7 x86|CCM-Universalx86. &lt;kompilacji\>.tar|  
|W wersji 7 x64|CCM-Universalx64. &lt;kompilacji\>.tar|  
|W wersji 8 x86|CCM-Universalx86. &lt;kompilacji\>.tar|  
|W wersji 8 x64|CCM-Universalx64. &lt;kompilacji\>.tar|  

### <a name="hp-ux"></a>HP-UX  

|||  
|-|-|  
|Wersja 11iv2 na komputerach IA64|CCM-HpuxB.11.23i64. &lt;kompilacji\>.tar|  
|Wersja 11iv2 PA-RISC|CCM-HpuxB.11.23PA. &lt;kompilacji\>.tar|  
|Wersja 11iv3 na komputerach IA64|CCM-HpuxB.11.31i64. &lt;kompilacji\>.tar|  
|Wersja 11iv3 PA-RISC|CCM-HpuxB.11.31PA. &lt;kompilacji\>.tar|  

### <a name="oracle-linux"></a>Oracle Linux  

|||  
|-|-|  
|W wersji 5 x86|CCM-Universalx86. &lt;kompilacji\>.tar|  
|W wersji 5 x64|CCM-Universalx64. &lt;kompilacji\>.tar|  
|W wersji 6 x86|CCM-Universalx86. &lt;kompilacji\>.tar|  
|W wersji 6 x64|CCM-Universalx64. &lt;kompilacji\>.tar|  
|W wersji 7 x64|CCM-Universalx64. &lt;kompilacji\>.tar|  

### <a name="red-hat-enterprise-linux-rhel"></a>Red Hat Enterprise Linux (RHEL)  

|||  
|-|-|  
|W wersji 4 x86|CCM-RHEL4x86. &lt;kompilacji\>.tar|  
|W wersji 4 x64|CCM-RHEL4x64. &lt;kompilacji\>.tar|  
|W wersji 5 x86|CCM-Universalx86. &lt;kompilacji\>.tar|  
|W wersji 5 x64|CCM-Universalx64. &lt;kompilacji\>.tar|  
|W wersji 6 x86|CCM-Universalx86. &lt;kompilacji\>.tar|  
|W wersji 6 x64|CCM-Universalx64. &lt;kompilacji\>.tar|  
|W wersji 7 x64|CCM-Universalx64. &lt;kompilacji\>.tar|  

### <a name="solaris"></a>Solaris  

|||  
|-|-|  
|W wersji 9 SPARC|CCM-Sol9sparc. &lt;kompilacji\>.tar|  
|W wersji 10 x86|CCM-Sol10x86. &lt;kompilacji\>.tar|  
|W wersji 10 SPARC|CCM-Sol10sparc. &lt;kompilacji\>.tar|  
|W wersji 11 x86|CCM-Sol11x86. &lt;kompilacji\>.tar|  
|W wersji 11 SPARC|CCM-Sol11sparc. &lt;kompilacji\>.tar|  

### <a name="suse-linux-enterprise-server-sles"></a>SUSE Linux Enterprise Server (wypełniania)  

|||  
|-|-|  
|W wersji 9 x86|CCM-SLES9x86. &lt;kompilacji\>.tar|  
|SP1 w wersji 10 x86|CCM-Universalx86. &lt;kompilacji\>.tar|  
|SP1 w wersji 10 x64|CCM-Universalx64. &lt;kompilacji\>.tar|  
|SP1 w wersji 11 x86|CCM-Universalx86. &lt;kompilacji\>.tar|  
|SP1 w wersji 11 x64|CCM-Universalx64. &lt;kompilacji\>.tar|  
|Wersja 12 x64|CCM-Universalx64. &lt;kompilacji\>.tar|  

### <a name="ubuntu"></a>Ubuntu  

|||  
|-|-|  
|Wersja 10.04 KÓW x86|CCM-Universalx86. &lt;kompilacji\>.tar|  
|Wersja 10.04 KÓW x64|CCM-Universalx64. &lt;kompilacji\>.tar|  
|Wersja 12.04 KÓW x86|CCM-Universalx86. &lt;kompilacji\>.tar|  
|Wersja 12.04 KÓW x64|CCM-Universalx64. &lt;kompilacji\>.tar|  
|Wersja 14.04 KÓW x86|CCM-Universalx86. &lt;kompilacji\>.tar|  
|Wersja 14.04 KÓW x64|CCM-Universalx64. &lt;kompilacji\>.tar|  

##  <a name="mobile-devices-enrolled-by-microsoft-intune"></a>Urządzenia przenośne zarejestrowane przez program Microsoft Intune  
 Aby uzyskać szczegółowe informacje dotyczące komputerów i urządzeń, którymi można zarządzać po zintegrowaniu programu Microsoft Intune z programem Configuration Manager zobacz następujące tematy dwóch w bibliotece Microsoft Intune:  

-   [Możliwości zarządzania urządzeniami przenośnymi w programie Microsoft Intune](https://docs.microsoft.com/intune/get-started/choose-how-to-manage-devices)  
-   [Możliwości zarządzania Komputerami z systemem Windows w Microsoft Intune](https://docs.microsoft.com/intune/get-started/windows-pc-management-capabilities-in-microsoft-intune)  

##  <a name="bkmk_OnpremOS"></a>Zarządzanie urządzeniami przenośnymi lokalnego  
 Program Configuration Manager ma wbudowane możliwości zarządzania urządzeniami, które lokalnych bez instalowania oprogramowania klienckiego.  Aby uzyskać więcej informacji, zobacz [zarządzania urządzeniami przenośnymi z infrastruktury lokalnej w programie System Center Configuration Manager](../../../mdm/understand/manage-mobile-devices-with-on-premises-infrastructure.md).  

 **Wymagania i ograniczenia:**  

-   Należy skonfigurować **punktem połączenia usługi** w lokacji najwyższego poziomu w hierarchii.  

**Obsługiwane systemy operacyjne:**  

- **Windows 10 Pro** (x86, x64)  

- **System Windows 10 Pro Enterprise** (x86, x64)  

- **System Windows 10 Enterprise IoT** (x86, x64)

- **Windows 10 Mobile**  

- **System Windows 10 Enterprise przenośnych**  

- **System Windows 10 IoT Mobile Enterprise**

- **Zespół systemu Windows 10 dla Centrum powierzchni**

##  <a name="bkmk_ExSrvConOS"></a>Łącznik serwera Exchange  
Program Configuration Manager obsługuje ograniczone Zarządzanie urządzeń łączących się z serwerem Exchange, bez konieczności instalowania klienta programu Configuration Manager. Aby uzyskać więcej informacji, zobacz [Zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i Exchange](../../../mdm/deploy-use/manage-mobile-devices-with-exchange-activesync.md).  

 **Wymagania i ograniczenia:**  

-   Programu Configuration Manager oferuje ograniczone zarządzanie dla urządzeń przenośnych, używając urządzenia za pomocą łącznika serwera Exchange dla programu Exchange Active Sync łączyć się z serwerem, na którym działa serwer Exchange lub usługą Exchange Online.  

-   Aby uzyskać więcej informacji na temat funkcji zarządzania, które obsługuje program Configuration Manager dla urządzeń przenośnych zarządzanych przez łącznik serwera Exchange, zobacz określić, jak zarządzać urządzeniami przenośnymi w programie Configuration Manager.  

**Obsługiwane wersje programu Exchange Server:**  

-   **Exchange Server 2010 z dodatkiem SP1**  

-   **Exchange Server 2010 z dodatkiem SP2**  

-   **Program Exchange Server 2013**  

-   **Exchange Online (Office 365)**: Obejmuje to Business Productivity Online Suite standardowa  

