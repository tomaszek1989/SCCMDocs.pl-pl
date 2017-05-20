---
title: "Obsługiwane konfiguracje dla LTSB | Dokumentacja firmy Microsoft"
description: "Zrozumieć, co systemy operacyjne i produkty zależne działają z długoterminowe obsługi gałęzi programu System Center Configuration Manager."
ms.custom: na
ms.date: 5/10/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: f0f818d4-7f45-402f-8758-dc88bc024953
caps.latest.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: f809c9327db9f298168674add2d09820fdecd1b8
ms.openlocfilehash: ec33d5febcbf7b57e220f7fe27db9671080fecff
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="supported-configurations-for-the-long-term-servicing-branch-of-system-center-configuration-manager"></a>Obsługiwane konfiguracje dla długoterminowej gałęzi obsługi programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (długoterminowej obsługi oddziału)*

Informacje przedstawione w tym temacie zrozumienie, jakie systemy operacyjne i zależności produktu są obsługiwane przez długoterminowe obsługi gałęzi (LTSB) programu Configuration Manager.
Jeśli nie zaznaczono inaczej, w tym lub LTSB określonych tematów, te same konfiguracje i ograniczenia, które mają zastosowanie do wersji bieżącej gałęzi 1606 się LTSB.  Gdy występują konflikty, za pomocą informacji, które mają zastosowanie do używanej wersji. Zazwyczaj LTSB jest bardziej ograniczone niż bieżącej gałęzi.

## <a name="general-statement-of-support"></a>Ogólne oświadczenie zespołu pomocy technicznej
Następujące produkty i technologie są obsługiwane przez tej gałęzi programu Configuration Manager. Jednak włączenie ich do tej zawartości nie express rozszerzenie pomocy technicznej dla dowolnego produktu lub wersji poza cyklu pomocy technicznej poszczególnych tego produktu. Produkty, które wykraczają poza ich zasady świadczenia pomocy technicznej nie są obsługiwane do użytku z programem Configuration Manager. Aby uzyskać więcej informacji, odwiedź stronę [zasady świadczenia pomocy technicznej firmy Microsoft](http://go.microsoft.com/fwlink/p/?LinkId=208270) witryny sieci Web i odczytu [zasady cyklu pomocy technicznej: Microsoft FAQ](http://go.microsoft.com/fwlink/p/?LinkId=31976).

Ponadto, produktów i wersji produktu, które nie są wymienione w poniższych tematach nie są obsługiwane, chyba że zostały ogłoszone na [blogu zabezpieczeń i Enterprise Mobility](https://blogs.technet.microsoft.com/enterprisemobility/).

**Ograniczenia dotyczące obsługi przyszłych:** LTSB mającym ograniczoną obsługę przyszłych systemów operacyjnych serwera i klienta i zależności produktu. Lista platform dla LTSB zostanie usunięty przez cały okres istnienia wersji:

**Windows:**
- Obsługiwane są tylko jakości i aktualizacje zabezpieczeń dla systemu Windows.
- Brak obsługi jest dodawany do bieżącej gałęzi (CB), bieżący oddziałów firmy (CBB) lub LTSB systemu Windows 10.
-    Nowe wersje główne systemu Windows Server nie są obsługiwane.

**Program SQL Server:**
- Jakość i aktualizacji zabezpieczeń lub niewielkie uaktualnienia, takich jak dodatki service pack, jest obsługiwana dla programu SQL Server.
- Nowe wersje główne programu SQL Server nie są obsługiwane.  

## <a name="site-systems-and-servers"></a>Systemy lokacji i serwerów
LTSB obsługuje korzystanie z następującymi systemami operacyjnymi Windows komputera jako systemy lokacji.  Każdy system operacyjny ma o wymaganiach i ograniczeniach w tej samej pozycji w [obsługiwanych systemów operacyjnych dla serwerów systemu lokacji](/sccm/core/plan-design/configs/supported-operating-systems-for-site-system-servers).  Na przykład instalacji Server Core systemu Windows 2012 R2 musi być x64 wersji, jest obsługiwany tylko do obsługi punktu dystrybucji, a nie obsługuje środowiska PXE lub multiemisji.

**Obsługiwane systemy operacyjne:**
- Windows Server 2016
- Windows Server 2012 (x 64): Standard, Datacenter
- Windows Server 2008 R2 z dodatkiem SP1 (x 64): Standard, Enterprise i Datacenter
- Windows Server 2008 z dodatkiem SP2 (x 86, x 64): Standard, Enterprise i Datacenter *(patrz Uwaga 1)*
- Windows 10 Enterprise 2015 LTSB (x86, x64)
- Windows 10 Enterprise 2016 LTSB (x86, x64)
- Windows 8.1 (x86, x64): Professional, Enterprise
- Windows 7 z dodatkiem SP1 (x 86, x 64): Professional, Enterprise, Ultimate
- Instalacja Server Core systemu Windows Server 2012
- Instalacja Server Core systemu Windows Server 2012 R2    

*Uwaga 1*: Ten system operacyjny nie jest obsługiwany dla serwerów lokacji lub role systemu lokacji, z wyjątkiem punktu dystrybucji i punktu dystrybucji. Można nadal używać tego systemu operacyjnego jako punkt dystrybucji, aż do Amortyzacja ta obsługa jest ogłaszane lub okresu rozszerzonej pomocy technicznej tego systemu operacyjnego. Aby uzyskać więcej informacji, zobacz [instalacji programu System Center Configuration Manager CB i LTSB kończy się niepowodzeniem w systemie Windows Server 2008](https://support.microsoft.com/help/4015095).

## <a name="client-management"></a>Zarządzanie klientami
W poniższych sekcjach podano klienckich systemów operacyjnych, którymi można zarządzać za pomocą LTSB. LTSB nie obsługuje dodawania nowych systemów operacyjnych jako obsługiwanych klientów.

### <a name="windows-computers"></a>Komputery z systemem Windows
LTSB można użyć do zarządzania następującymi systemami operacyjnymi komputerów Windows w oprogramowaniu klienckim programu Configuration Manager dostępnej w programie Configuration Manager. Aby uzyskać więcej informacji, zobacz [wdrażanie klientów na komputerach z systemem Windows w programie System Center Configuration Manager](/sccm/core/clients/deploy/deploy-clients-to-windows-computers).

**Obsługiwane systemy operacyjne:**
- Windows Server 2016
- Windows Server 2012 R2 (x 64): Standard, Datacenter (Uwaga 1)
- Windows Server 2012 (x 64): Standard, Datacenter (Uwaga 1)
- Windows Storage Server 2012 R2 (x 64)
- Windows Storage Server 2012 (x 64)
- Windows Server 2008 R2 z dodatkiem SP1 (x 64): Standard, Enterprise i Datacenter (Uwaga 1)
- Windows Storage Server 2008 R2 (x 86, x 64): Grupa robocza, Standard, Enterprise
- Windows Server 2008 z dodatkiem SP2 (x 86, x 64): Standard, Enterprise i Datacenter (Uwaga 1)
- Windows 10 Enterprise 2015 LTSB (x86, x64)
- Windows 10 Enterprise 2016 LTSB (x86, x64)
- Windows 8.1 (x86, x64): Professional, Enterprise
- Windows 7 z dodatkiem SP1 (x 86, x 64): Professional, Enterprise, Ultimate
- Instalacja Server Core systemu Windows Server 2012 R2 (x64) (Uwaga 2)
- Instalacja Server Core systemu Windows Server 2012 (x64) (Uwaga 2)
- Instalacja Server Core systemu Windows Server 2008 R2 z dodatkiem SP1 (x64)
- Instalacja Server Core systemu Windows Server 2008 z dodatkiem SP2 (x86, x64)

**(Uwaga 1)**  Wersji Centrum danych są obsługiwane, lecz nie ma certyfikatu dla programu Configuration Manager.  
**(Uwaga 2)**  Do obsługi instalacji wypychanej klienta, na komputerze z tą wersją systemu operacyjnego należy uruchomić usługę roli serwera plików dla roli serwera usługi plików i magazynowania. Informacje o instalowaniu funkcji systemu Windows na komputerze instalacja Server Core, zobacz [instalowania ról i funkcji serwera na serwera Server Core](https://technet.microsoft.com/library/jj574158(v=ws.11).aspx) w bibliotece TechNet programu Windows Server 2012.

### <a name="windows-embedded"></a>Windows Embedded
LTSB można użyć do zarządzania następującymi urządzeniami Windows Embedded przez zainstalowanie oprogramowania klienta na urządzeniu.  Aby uzyskać więcej informacji, zobacz [Planowanie wdrożenia klientów na urządzeniach Windows Embedded w programie System Center Configuration Manager](/sccm/core/clients/deploy/plan/planning-for-client-deployment-to-windows-embedded-devices).

**Wymagania i ograniczenia:**  

-   Wszystkie funkcje klienta są obsługiwane w obsługiwanych Windows Embedded systems, które nie mają włączone filtry zapisu.  

-   Obsługiwane są wszystkie funkcje z wyjątkiem zarządzania energią klientów korzystających z jedną z następujących:  

    -   Rozszerzone filtry zapisu (EWF)    

    -   Pamięć RAM filtry zapisu oparte na plikach (FBWF)    

    -   Filtry zapisu Unified (UWF)  

-   Katalog aplikacji nie jest obsługiwane dla urządzeń Windows Embedded.  

-   Przed można monitorować wykrytego złośliwego oprogramowania na urządzeniach Windows Embedded oparte na systemie Windows XP, należy zainstalować pakiet skryptów systemu Microsoft Windows WMI na urządzeniu osadzonym. Windows Embedded docelowy Designer należy zainstalować ten pakiet. *WBEMDISP. Biblioteka DLL* i *WBEMDISP. TLB* plików musi istnieć i być zarejestrowana w folderze %windir%\System32\WBEM na osadzonych urządzenia zapewniające wykryto złośliwe oprogramowanie jest raportowana.  

**Obsługiwane systemy operacyjne:**  
-   Windows 10 Enterprise 2016 LTSB (x86, x64)  
-   Windows 10 Enterprise 2015 LTSB (x86, x64)  
-   Windows Embedded 8.1 Industry (x86, x64)    
-   Komputer Windows elastycznej (x86, x64)    
-   Windows Embedded POSReady 7 (x86, x64)    
-   Windows Embedded Standard 7 z dodatkiem SP1 (x 86, x 64)    
-   Windows Embedded POSReady 2009 (x86)   
-   Windows Embedded Standard 2009 (x86)  

### <a name="windows-ce"></a>Windows CE  
 Urządzenia systemu Windows CE można zarządzać w programie Configuration Manager starszego klienta urządzenia przenośnego dostępnej w programie Configuration Manager.  

**Wymagania i ograniczenia:**  

-   Klient urządzenia przenośnego wymaga 0.78 MB miejsca do instalacji klienta. Urządzenie przenośne może potrwać maksymalnie 256 KB dodatkowego miejsca do logowania.    

-   Funkcje dla tych urządzeń przenośnych różnią się zależnie od platformy i klient typu. Informacje dotyczące rodzaju funkcjach zarządzania obsługiwanych przez program Configuration Manager dla starszych klientów urządzeń przenośnych, zobacz [wybierz rozwiązanie do zarządzania urządzeniami programu System Center Configuration Manager](/sccm/core/plan-design/choose-a-device-management-solution).  

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

### <a name="mac-computers"></a>Komputery Mac  
 LTSB można użyć do zarządzania komputerami Mac OS X z klienta programu Configuration Manager dla komputerów Macintosh.

Pakiet instalacyjny klienta Mac nie znajduje się na nośniku programu Configuration Manager. Możesz pobrać jako część pobierania "klientów dla innych systemów operacyjnych" na [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=525184).  

Obsługa systemów operacyjnych Mac jest ograniczone do tych wymienionych w tej sekcji. Obsługa nie ma innych systemów operacyjnych, które mogą być obsługiwane przez przyszłej aktualizacji do pakietów instalacyjnych klienta Mac dla bieżącej gałęzi.

Aby uzyskać więcej informacji, zobacz [sposobu wdrażania klientów w programie System Center Configuration Manager Mac](/sccm/core/clients/deploy/deploy-clients-to-macs).

**Obsługiwane wersje:**  
-   Mac OS X 10.9 (Mavericks)  
-   Mac OS X 10.10 (Yosemite)  
-   Mac OS X 10.11 (El Capitan)  

## <a name="linux-and-unix-servers"></a>Serwery z systemem Linux i UNIX
LTSB służy do zarządzania serwerami z systemem Linux i UNIX za pomocą klienta programu Configuration Manager dla systemu Linux i UNIX.

Pakiety instalacyjne klienta z systemem Linux i UNIX nie są dostarczane z nośnika programu Configuration Manager. Można pobrać jako część pobierania "klientów dla innych systemów operacyjnych" na [Microsoft Download Center](http://go.microsoft.com/fwlink/?LinkID=525184). Oprócz pakietów instalacyjnych klienta pobierania klienta obejmuje skryptu instalacji, który zarządza instalacją klienta na każdym komputerze.

Obsługa systemów operacyjnych Linux i UNIX jest ograniczone do tych wymienionych w tej sekcji. Obsługa nie ma innych systemów operacyjnych, które mogą być obsługiwane przez przyszłej aktualizacji do pakietów klienta systemu Linux i UNIX dla bieżącej gałęzi.

**Wymagania i ograniczenia:**  

-   Aby przejrzeć zależności plików systemu operacyjnego klienta dla systemu Linux i UNIX, zobacz [wymagania wstępne dotyczące wdrażania klientów na serwerach Linux i UNIX](/sccm/core/clients/deploy/plan/planning-for-client-deployment-to-linux-and-unix-computers#bkmk_clientdeployprereqforlnu).  
-   Omówienie funkcji zarządzania, obsługiwane na komputerach z systemem UNIX lub Linux, zobacz [wdrażanie klientów do serwerów systemu UNIX i Linux w programie System Center Configuration Manager](/sccm/core/clients/deploy/deploy-clients-to-unix-and-linux-servers).  
-   W przypadku obsługiwanych wersji systemów UNIX i Linux wymienionych wersji obejmuje wszystkie kolejne wersje pomocnicze. Na przykład wskazana pomocy technicznej dla CentOS w wersji 6 obejmuje również kolejne wersja pomocnicza 6 CentOS, takie jak CentOS 6.3. Podobnie gdy liście pomocy technicznej dla systemu operacyjnego, który używa dodatków service Pack systemu SUSE Linux Enterprise Server 11 z dodatkiem SP1, obsługa obejmuje kolejnymi dodatkami service Pack dla danej wersji systemu operacyjnego.
-   Informacje dotyczące pakietów instalacyjnych klienta i agenta uniwersalnego, zobacz [wdrażanie klientów do serwerów systemu UNIX i Linux w programie System Center Configuration Manager](/sccm/core/clients/deploy/deploy-clients-to-unix-and-linux-servers).


**Obsługiwane wersje:**   
Obsługiwane są następujące wersje przy użyciu .tar wskazanego pliku.  
### <a name="aix"></a>AIX  

|Wersja|Plik|  
|-|-|  
|Wersja 5.3 (Power)|CCM-Aix53ppc. &lt;kompilacji\>.tar|  
|W wersji 6.1 (Power)|CCM-Aix61ppc. &lt;kompilacji\>.tar|  
|W wersji 7.1 (Power)|CCM-Aix71ppc. &lt;kompilacji\>.tar|  

### <a name="centos"></a>CentOS  

|Wersja|Plik|  
|-|-|  
|W wersji 5 x86|CCM-Universalx86. &lt;kompilacji\>.tar|  
|W wersji 5 x64|CCM-Universalx64. &lt;kompilacji\>.tar|  
|W wersji 6 x86|CCM-Universalx86. &lt;kompilacji\>.tar|  
|W wersji 6 x64|CCM-Universalx64. &lt;kompilacji\>.tar|  
|W wersji 7 x64|CCM-Universalx64. &lt;kompilacji\>.tar|  

### <a name="debian"></a>Debian  

|Wersja|Plik|    
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

|Wersja|Plik|  
|-|-|  
|Wersja 11iv2 na komputerach IA64|CCM-HpuxB.11.23i64. &lt;kompilacji\>.tar|  
|Wersja 11iv2 PA-RISC|CCM-HpuxB.11.23PA. &lt;kompilacji\>.tar|  
|Wersja 11iv3 na komputerach IA64|CCM-HpuxB.11.31i64. &lt;kompilacji\>.tar|  
|Wersja 11iv3 PA-RISC|CCM-HpuxB.11.31PA. &lt;kompilacji\>.tar|  

### <a name="oracle-linux"></a>Oracle Linux  

|Wersja|Plik|    
|-|-|  
|W wersji 5 x86|CCM-Universalx86. &lt;kompilacji\>.tar|  
|W wersji 5 x64|CCM-Universalx64. &lt;kompilacji\>.tar|  
|W wersji 6 x86|CCM-Universalx86. &lt;kompilacji\>.tar|  
|W wersji 6 x64|CCM-Universalx64. &lt;kompilacji\>.tar|  
|W wersji 7 x64|CCM-Universalx64. &lt;kompilacji\>.tar|  

### <a name="red-hat-enterprise-linux-rhel"></a>Red Hat Enterprise Linux (RHEL)  

|Wersja|Plik|  
|-|-|  
|W wersji 4 x86|CCM-RHEL4x86. &lt;kompilacji\>.tar|  
|W wersji 4 x64|CCM-RHEL4x64. &lt;kompilacji\>.tar|  
|W wersji 5 x86|CCM-Universalx86. &lt;kompilacji\>.tar|  
|W wersji 5 x64|CCM-Universalx64. &lt;kompilacji\>.tar|  
|W wersji 6 x86|CCM-Universalx86. &lt;kompilacji\>.tar|  
|W wersji 6 x64|CCM-Universalx64. &lt;kompilacji\>.tar|  
|W wersji 7 x64|CCM-Universalx64. &lt;kompilacji\>.tar|  

### <a name="solaris"></a>Solaris  

|Wersja|Plik|   
|-|-|  
|W wersji 9 SPARC|CCM-Sol9sparc. &lt;kompilacji\>.tar|  
|W wersji 10 x86|CCM-Sol10x86. &lt;kompilacji\>.tar|  
|W wersji 10 SPARC|CCM-Sol10sparc. &lt;kompilacji\>.tar|  
|W wersji 11 x86|CCM-Sol11x86. &lt;kompilacji\>.tar|  
|W wersji 11 SPARC|CCM-Sol11sparc. &lt;kompilacji\>.tar|  

### <a name="suse-linux-enterprise-server-sles"></a>SUSE Linux Enterprise Server (wypełniania)  

|Wersja|Plik|  
|-|-|  
|W wersji 9 x86|CCM-SLES9x86. &lt;kompilacji\>.tar|  
|SP1 w wersji 10 x86|CCM-Universalx86. &lt;kompilacji\>.tar|  
|SP1 w wersji 10 x64|CCM-Universalx64. &lt;kompilacji\>.tar|  
|SP1 w wersji 11 x86|CCM-Universalx86. &lt;kompilacji\>.tar|  
|SP1 w wersji 11 x64|CCM-Universalx64. &lt;kompilacji\>.tar|  
|Wersja 12 x64|CCM-Universalx64. &lt;kompilacji\>.tar|  

### <a name="ubuntu"></a>Ubuntu  

|Wersja|Plik|    
|-|-|  
|Wersja 10.04 KÓW x86|CCM-Universalx86. &lt;kompilacji\>.tar|  
|Wersja 10.04 KÓW x64|CCM-Universalx64. &lt;kompilacji\>.tar|  
|Wersja 12.04 KÓW x86|CCM-Universalx86. &lt;kompilacji\>.tar|  
|Wersja 12.04 KÓW x64|CCM-Universalx64. &lt;kompilacji\>.tar|  
|Wersja 14.04 KÓW x86|CCM-Universalx86. &lt;kompilacji\>.tar|  
|Wersja 14.04 KÓW x64|CCM-Universalx64. &lt;kompilacji\>.tar|  

### <a name="exchange-server-connector"></a>Łącznik serwera Exchange
 LTSB obsługuje ograniczone Zarządzanie urządzeń łączących się z wystąpieniem serwera Exchange bez instalowania oprogramowania klienckiego. Aby uzyskać więcej informacji, zobacz [Zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i Exchange](/sccm/mdm/deploy-use/manage-mobile-devices-with-exchange-activesync).

 **Wymagania i ograniczenia:**  

-   Program Configuration Manager oferuje ograniczone zarządzanie dla urządzeń przenośnych. Ograniczone zarządzanie jest dostępna, gdy używany jest łącznik serwera Exchange dla urządzeń obsługujących Exchange Active Sync (EAS) łączących się z serwerem z systemem Exchange Server lub Exchange Online.  

-   Aby uzyskać więcej informacji o funkcjach zarządzania obsługiwanych przez program Configuration Manager dla urządzeń przenośnych zarządzanych przez łącznik serwera Exchange, zobacz [wybierz rozwiązanie do zarządzania urządzeniami programu System Center Configuration Manager](/sccm/core/plan-design/choose-a-device-management-solution).  

**Obsługiwane wersje programu Exchange Server:**  
-   Exchange Server 2010 z dodatkiem SP1  
-   Exchange Server 2010 z dodatkiem SP2  
-   Exchange Server 2013  

> [!NOTE]
> LTSB nie obsługuje zarządzania urządzeniami łączących się za pośrednictwem usługi online, takich jak Exchange Online (Office 365).


## <a name="configuration-manager-console"></a>Konsola programu Configuration Manager
LTSB obsługuje następujące systemy operacyjne, aby uruchomić konsolę programu Configuration Manager. Każdy komputer, który jest hostem konsoli musi mieć minimalnej wersji .NET Framework 4.5.2, z wyjątkiem systemu Windows 10, który wymaga co najmniej programu .NET Framework 4.6.

**Obsługiwane systemy operacyjne:**
- Windows Server 2016
- Windows Server 2012 R2 (x 64): Standard, Datacenter
- Windows Server 2012 (x 64): Standard, Datacenter
- Windows Server 2008 R2 z dodatkiem SP1 (x 64): Standard, Enterprise i Datacenter
- Windows Server 2008 z dodatkiem SP2 (x 86, x 64): Standard, Enterprise i Datacenter
- Windows 10 Enterprise 2016 LTSB (x86, x64)
- Windows 10 Enterprise 2015 LTSB (x86, x64)
- Windows 8.1 (x86, x64): Professional, Enterprise
- Windows 7 z dodatkiem SP1 (x 86, x 64): Professional, Enterprise, Ultimate


## <a name="sql-server-versions-supported-for-the-site-database-and-reporting-point"></a>Bazy danych lokacji i punkt raportowania obsługiwane wersje programu SQL Server
LTSB obsługuje następujące wersje programu SQL Server do obsługi bazy danych lokacji i punkt raportowania. Obsługiwane każdej wersji, te same wymagania konfiguracji i ograniczenia, które są wyświetlane w [obsługę wersji programu SQL Server](/sccm/core/plan-design/configs/support-for-sql-server-versions) dla bieżącej gałęzi dotyczą LTSB.  Obejmuje to korzystanie z klastra programu SQL Server lub grupy dostępności AlwaysOn programu SQL Server.  

**Obsługiwane wersje:**

- Program SQL Server 2016: Standard, Enterprise
- SQL Server 2014 z dodatkiem SP2: Standard, Enterprise
- SQL Server 2014 SP1: Standard, Enterprise
- SQL Server 2012 z dodatkiem SP3: Standard, Enterprise
- SQL Server 2008 R2 z dodatkiem SP3: Standard, Enterprise i Datacenter
- Program SQL Server 2016 Express
- SQL Server 2014 Express z dodatkiem SP2
- SQL Server 2014 Express SP1
- SQL Server 2012 Express SP3

## <a name="support-for-active-directory-domains"></a>Obsługa domen usługi Active Directory
Wszystkie systemy lokacji LTSB muszą należeć do domeny usługi Active Directory systemu Windows obsługiwane. Obsługę domen usługi Active Directory ma tę samą wymagania i ograniczenia, jak te, które są wyświetlane w [obsługę domen usługi Active Directory](/sccm/core/plan-design/configs/support-for-active-directory-domains), ale jest ograniczone do następujących poziomów funkcjonalności domeny:

**Obsługiwane poziomy:**
- Windows Server 2008
- Windows Server 2008 R2
- Windows Server 2012
- Windows Server 2012 R2

## <a name="additional-support-topics-that-apply-to-the-long-term-servicing-branch"></a>Tematy dotyczące gałęzi obsługi długoterminowe dodatkowej pomocy
Informacje w poniższych tematach bieżącej gałęzi dotyczą LTSB:
- [Numery rozmiaru i skali](/sccm/core/plan-design/configs/size-and-scale-numbers)
- [Wymagania wstępne systemu lokacji i lokacji](/sccm/core/plan-design/configs/site-and-site-system-prerequisites)
- [Opcje wysokiej dostępności](/sccm/protect/understand/high-availability-options)
- [Zalecany sprzęt](/sccm/core/plan-design/configs/recommended-hardware)
- [Obsługa sieci i funkcji systemu Windows](/sccm/core/plan-design/configs/support-for-windows-features-and-networks)
- [Obsługa środowisk wirtualizacji](/sccm/core/plan-design/configs/support-for-virtualization-environments)

