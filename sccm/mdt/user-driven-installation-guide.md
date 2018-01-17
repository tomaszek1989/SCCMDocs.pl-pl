---
title: "Szybki Start - instalacji opartej na użytkownika"
titleSuffix: Microsoft Deployment Toolkit
description: "Guiide szybki start dotyczące usługi Microsoft Deployment Toolkit dla instalacji za pomocą użytkownika. "
ms.date: 09/09/2016
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: article
ms.assetid: dcddc250-9361-4e69-af45-472da4ef5fd5
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 56d65db90e87e67cb3d0dcdd3224206444d44888
ms.sourcegitcommit: 645cd5a324bdd299906efa27eaca5885eafc9e9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2018
---
# <a name="quick-start-guide-for-user-driven-installation"></a>Przewodnik Szybki Start dotyczący instalacji opartej na użytkownika  
 Microsoft Deployment Toolkit (MDT) 2013 udostępnia technologii wdrażania systemów operacyjnych Windows i program Microsoft Office. Ten przewodnik Szybki start pomaga szybko ocenić zestawu MDT 2013, dostarczając instrukcji skróconego, krok użytkowania go, aby zainstalować system operacyjny Windows 8.1 i Microsoft Office Professional Plus 2010 przy użyciu instalacji sterowanej (UDI) i Microsoft System Center 2012 R2 Configuration Manager. Ten przewodnik Szybki start pokazano, jak wykonać scenariusz wdrażania MDT nowy komputer, który obejmuje wdrażania systemu Windows 8.1 do nowego komputera. W tym scenariuszu przyjęto założenie, że nie istnieje lub profilu, aby zachować dane użytkownika.  

> [!NOTE]
>  W tym dokumencie *Windows* ma zastosowanie do systemów operacyjnych Windows 8.1, Windows 8, Windows 7, Windows Server® 2012 R2, Windows Server 2012 i Windows Server 2008 R2, chyba że określono inaczej. Zestaw MDT nie obsługuje wersji na podstawie procesora ARM systemu Windows. Podobnie *MDT* odwołuje się do zestawu MDT 2013, chyba że określono inaczej.  

 Po użyciu tego przewodnika, można obliczyć zestawu MDT, przejrzyj pozostałe wskazówki zestawu MDT, aby dowiedzieć się więcej o funkcjach zaawansowanych technologii.  

> [!NOTE]
>  Konfiguracja infrastruktury opisane w tym miejscu jest do celów ewaluacyjnych i nie jest przeznaczony dla systemu produkcji.  

## <a name="prerequisites"></a>Wymagania wstępne  
 Instalacji UDI przy użyciu programu System Center 2012 R2 Configuration Manager zostały spełnione następujące wymagania wstępne.  

### <a name="required-software"></a>Wymagane oprogramowanie  
 Aby ukończyć ten przewodnik, wymagane jest następujące oprogramowanie:  

-   Windows Server 2008 R2  

-   Microsoft SQL Server® 2008 R2  

-   SQL Server 2008 R2 z dodatkiem Service Pack 1 (SP1)  

-   Aktualizacja zbiorcza programu SQL Server 2008 R2 z dodatkiem SP1 6 (CU6)  

-   Windows 8.1  

-   System Center 2012 R2 Configuration Manager  

-   Office Professional Plus 2010 licencji zbiorczej, wersji 32-bitowych  

-   Microsoft .NET Framework w wersji 3.5 z dodatkiem SP1  

-   Windows PowerShell™ w wersji 2.0  

-   Środowisko preinstalacji systemu Windows (Windows PE), który jest dostępny w programie Configuration Manager  

-   Usługi sieciowe, w tym systemu nazw domen (DNS, Domain Name System) i protokół dynamicznej konfiguracji hosta (DHCP)  

-   Usługi domenowe Active Directory® (AD DS)  

> [!NOTE]
>  Sekwencjonowania zadań używać we wdrożeniach MDT wymaga przypisania Tworzenie obiektu globalnego prawo do poświadczenia używane do uzyskania dostępu i uruchamiania konsoli Deployment Workbench i procesu wdrażania. To prawo jest dostępne dla kont z uprawnieniami administratora na poziomie (chyba że jawnie usunięte). Ponadto specjalizowany zabezpieczeń — profil zabezpieczeń ograniczoną funkcjonalność (SSLF) usuwa uprawnienie do tworzenia obiektów globalnych i nie powinny być stosowane do komputerów wdrażane za pomocą zestawu MDT.  

### <a name="computer-configuration"></a>Konfiguracja komputera  
 Aby ukończyć w tym przewodniku, należy skonfigurować komputery wymienione w tabeli 1. Te komputery mogą być komputerów fizycznych lub maszynach wirtualnych (VM) z wymienionych zasobów systemowych.  

### <a name="table-1-computers-used-in-this-guide"></a>Tabela 1. Komputery używane w tym przewodniku  

|**Komputer** |**Opis i zasobów systemowych** |  
|-|-|  
|WDG-MDT-01|Ten komputer ma zestaw MDT infrastruktury i programu Configuration Manager. Na komputerze z systemem Windows Server 2008 R2 z następujących usług sieciowych zainstalowane:<br /><br /> -AD DS<br />— Serwer DNS<br />-Serwer DHCP<br />— Usługi wdrażania systemu Windows<br /><br /> Zasoby systemowe komputera są następujące:<br /><br /> — Procesor czterordzeniowe uruchomiony na procesor 2,66 gigaherca (GHz) lub szybszy<br />-4 gigabajty (GB) lub więcej pamięci fizycznej<br />-Partycji dysku, który ma co najmniej 40 GB dostępnego miejsca na dysku; stanie się partycji dysku c.<br />-CD-ROM lub DVD-ROM dysk, który zostanie przypisany literą dysku D<br />-Partycji dysku, który ma co najmniej 40 GB dostępnego miejsca na dysku; stanie się partycji E.|  
|WDG-REF-01|Jest to komputer odniesienia, w którym jest uruchomiona bez bieżącego systemu operacyjnego. Zasoby systemowe komputera są następujące:<br /><br /> — Procesor uruchomiona 1,4 GHz lub szybszy<br />— 1 GB lub więcej pamięci fizycznej<br />– 16 GB lub więcej dostępnego miejsca na dysku|  
|WDG-CLI-01|Jest to komputera docelowego, który jest uruchamiany bez bieżącego systemu operacyjnego. Zasoby systemowe komputera są następujące:<br /><br /> — Procesor uruchomiona 1,4 GHz lub szybszy<br />— 1 GB lub więcej pamięci fizycznej<br />– 16 GB lub więcej dostępnego miejsca na dysku|  

 Zasobów wymienionych w tabeli 1 odzwierciedlają zasobów systemowych zalecane do wykonania kroków tego podręcznika. Aby uzyskać informacje na minimalne wymagania systemowe programu zasobów:  

-   Windows Server 2008 R2, zobacz [Instalowanie systemu Windows Server 2008 R2](http://technet.microsoft.com/library/dd379511\(WS.10\).aspx)  

-   SQL Server 2008 R2, zobacz [wymagania sprzętowe i programowe instalacji programu SQL Server 2008 R2](http://technet.microsoft.com/library/ms143506.aspx)  

> [!NOTE]
>  W tym przewodniku założono, że zestaw MDT jest oceniana na komputerach fizycznych lub wirtualnych 64-bitowej (x 64). Jeśli ocena MDT na różnych platformach 32-bitowej (x 86), Pobierz i zainstaluj x86 wersji zestawu MDT i składników, które opisano w tym przewodniku.  

## <a name="step-1-prepare-the-prerequisite-infrastructure"></a>Krok 1. Przygotowanie wymagań wstępnych dotyczących infrastruktury  
 Do celów tego przewodnika, wszystkich wymagań wstępnych dotyczących infrastruktury usługi są uruchomione na komputerze o nazwie *WDG-MDT-01*. Zainstaluj wstępnie wymagane oprogramowanie, role serwera i usługi na tym komputerze, przed rozpoczęciem instalacji zestawu MDT.  

> [!NOTE]
>  W tej sekcji założono, że w przypadku tworzenia nowej infrastruktury programu Configuration Manager zestawu MDT. Jeśli korzystasz z istniejącej infrastruktury programu Configuration Manager, przejrzyj kroki opisane w tej sekcji i Zastąp istniejące nazwy zasobów dla zasobów utworzone w tej sekcji (takie jak nazwa komputera i udostępnionych folderów sieciowych). Po zapoznaniu się w tej sekcji, przejdź do [krok 2: Przygotowanie środowiska zestawu MDT](#PreparetheMDTEnvironment)  

 Przygotowanie infrastruktury wymagań wstępnych przed rozpoczęciem instalacji zestawu MDT przez:  

-   Instalowanie systemu Windows Server 2008 R2, zgodnie z opisem w [krok 1-1: Zainstaluj system Windows Server 2008 R2](#InstallWindowsServer2008)  

-   Tworzenie wymagane foldery i sieciowych udziałów zgodnie z opisem w [krok 1 i 2: Tworzenie wymagane folderów i udziałów sieciowych](#CreatetheRequiredFoldersandNetworkShares)  

-   Uzyskiwanie oprogramowania wymaganego do wykonania kroków tego podręcznika, zgodnie z opisem w [krok 1: 3: Uzyskanie wymaganego oprogramowania](#ObtaintheRequiredSoftware)  

-   Instalowanie roli serwera usług AD DS, zgodnie z opisem w [krok 1-4: Instalowanie roli serwera DS AD](#InstalltheADDSServerRole)  

-   Instalowanie roli serwera serwer DHCP, zgodnie z opisem w [krok 1-5: Instalowanie roli serwera serwer DHCP](#InstalltheDHCPServerServerRole)  

-   Instalowanie roli serwera usług sieci Web (IIS), zgodnie z opisem w [krok 1 — 6: Zainstaluj rolę serwera sieci Web Services (IIS)](#InstalltheWebServicesServerRole)  

-   Dodanie wymaganych funkcji systemu Windows Server 2008 R2, zgodnie z opisem w [kroku 1-7: Dodać funkcje wymagane systemu Windows Server 2008 R2](#AddtheRequiredWindowsServer2008Features)  

-   Tworzenie kont użytkowników i usług wymaganych do wykonania kroków tego podręcznika, zgodnie z opisem w [krok 1 — 8: Utwórz wymagane użytkownika i kont usług](#CreatetheRequiredUserandServiceAccounts)  

-   Instalowanie programu SQL Server 2008 R2 dla programu Configuration Manager do używania zgodnie z opisem w [krok 1 — 9: Zainstaluj program SQL Server 2008 R2](#InstallSQLServer2008)  

-   Dodawanie serwera lokacji do grupy zabezpieczeń Administratorzy, zgodnie z opisem w [krok 1 – 10: Dodaj serwer lokacji do grupy zabezpieczeń Administratorzy](#AddtheSiteServertotheAdministratorsSecurityGroup)  

-   Instalowanie programu Configuration Manager, zgodnie z opisem w [krok 1 — 11: Instalowanie programu Configuration Manager](#InstallConfigurationManager)  

-   Konfigurowanie konta dostępu do sieci, używanego przez klientów programu Configuration Manager można uzyskać dostępu do dystrybucji programu Configuration Manager punktów zgodnie z opisem w [krok 1-12: Konfigurowanie konta dostępu do sieci](#ConfiguretheNetworkAccessAccount)  

-   Konfigurowanie granic lokacji programu Configuration Manager i grup granic, zgodnie z opisem w [krok 1 — 13: Konfigurowanie granic lokacji programu Configuration Manager i grup granic](#ConfiguretheConfigurationManagerSiteBoundaries)  

-   Konfigurowanie publikowania informacji o lokacji w usługach AD DS i DNS, zgodnie z opisem w [krok 1 — 14: Skonfiguruj publikowanie informacji o lokacji w usługach AD DS i systemu DNS](#ConfigurethePublishingofSiteIntofrmation)  

-   Konfigurowanie odnajdywania użytkowników w usługach AD DS, zgodnie z opisem w [krok 1 — 15: Konfigurowanie odnajdywania użytkowników usługi Active Directory](#ConfigureDiscoveryofActiveDirectoryUsers)  

###  <a name="InstallWindowsServer2008"></a>Krok 1-1. Zainstaluj system Windows Server 2008 R2  
 Skorzystaj z informacji w wersji 2 do zainstalowania systemu Windows Server 2008 R2. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

### <a name="table-2-information-for-installing-windows-server-2008-r2"></a>Tabela 2. Informacje dotyczące instalowania systemu Windows Server 2008 R2  

|**Po wyświetleniu monitu o** |**Podaj te wartości** |  
|-|-|  
|**Gdzie chcesz zainstalować system Windows?** |**0 nieprzydzielonego miejsca na dysku** |  
|**Hasło** |Wszelkie silne hasło.|  
|**Nazwa komputera** |**WDG-MDT-01** |  
|**Formatowanie woluminów C i E** |**SYSTEMU PLIKÓW NTFS** |  
|**Konfiguracja protokołu TCP/IP** |Skonfiguruj z konfiguracją statycznego adresu IP, z innymi TCP/IP opcje konfiguracji na potrzeby środowiska|  

###  <a name="CreatetheRequiredFoldersandNetworkShares"></a>Krok 1 i 2. Tworzenie wymagane folderów i udziałów sieciowych  
 Proces wdrożenia zestawu MDT wymaga dodatkowych folderów, które są używane jako źródło dla plików lub do przechowywania plików utworzonych w procesie wdrożenia zestawu MDT. Niektóre z tych folderów muszą być udostępniane, dzięki czemu są one dostępne z innych komputerów.  

 **Aby utworzyć wymagane folderów i udziałów**  

1.  Tworzenie folderów i udziałów wymienionych w tabeli 3 uprawnienia określone dla każdego udziału  

    ### <a name="table-3-folders-that-the-mdt-deployment-process-requires"></a>Tabela 3. Foldery, które wymaga proces wdrożenia zestawu MDT  

    |**Utwórz folder** |**Ta nazwa udziału** |**Te uprawnienia udziału** |  
    |-|-|-|  
    |E:\Source$|Źródło$|**Administratorzy**: Współwłaściciel<br /><br /> **Wszyscy**: Odczyt|  
    |E:\Images$|Obrazy$|**Administratorzy**: Współwłaściciel<br /><br /> **Wszyscy**: Odczyt|  
    |E:\Capture$|Przechwyć$|**Administratorzy**: Współwłaściciel<br /><br /> **Wszyscy**: Odczyt|  
    |E:\Packages$|Pakiety$|**Administratorzy**: Współwłaściciel<br /><br /> **Wszyscy**: Odczyt|  

2.  Utwórz następujące foldery:  

    -   E:\CMDownloads  

    -   E:\Source$\CustomSettings  

    -   E:\Source$\Drivers  

    -   E:Source$ Windows_8-1  

    -   E:Source$ MDT_2013  

    -   E:Source$ SQL2008R2  

    -   E:Source$ SQL2008R2SP1  

    -   E:Source$ SQL2008R2CU6  

    -   E:Source$ OfficeProPlus2010  

    -   E:Source$ ConfigMgr  

    -   Sterowniki $ E:Packages  

3.  Skopiuj E:\Source$\Drivers sterowniki urządzenia komputera odniesienia (WDG-REF-01) i na komputerze docelowym (WDG-CLI-01).  

    > [!NOTE]
    >  Procesy w tym przewodniku założono, że komputer odniesienia oraz komputer docelowy ma tych samych urządzeń i nie wymagają sterowników urządzeń.  

###  <a name="ObtaintheRequiredSoftware"></a>Krok 1-3. Uzyskanie wymaganego oprogramowania  
 Oprócz Windows Server 2008 R2, Windows 8.1 i System Center 2012 R2 Configuration Manager niektórych oprogramowanie jest wymagane do obliczenia MDT oparte na procesy w tym przewodniku. Tabela 4 zawiera listę oprogramowania wymagane do przeprowadzenia wdrożenia przy użyciu zestawu MDT, gdzie można uzyskać oprogramowanie i gdzie należy umieścić oprogramowania na WDG-MDT-01.  

### <a name="table-4-additional-software-required-for-deployment-using-mdt"></a>Tabela 4. Dodatkowe oprogramowanie wymagane do wdrożenia przy użyciu zestawu MDT  

|**Uzyskaj tego oprogramowania** |**Umieść w tym folderze** |  
|-|-|  
|ZESTAW MDT 2013|E:\Source$\MDT_2013|  
|Windows 8.1, pliki dystrybucyjne z nośnika produktu|E:\Source$\Windows_8-1|  
|Sterowniki urządzeń wymagane w komputerach referencyjnych i docelowych (WDG-REF-01 i WDG-CLI-01)|E:\Source$\Drivers|  
|SQL Server 2008 R2 z nośnika produktu|E:\Source$\SQL2008|  
|SQL Server 2008 R2 SP1, dostępne pod adresem [http://www.microsoft.com/download/en/details.aspx?id=26727](http://www.microsoft.com/download/en/details.aspx?id=26727)|E:\Source$\SQL2008R2SP1|  
|SQL Server 2008 R2 z dodatkiem SP1 CU6, dostępne pod adresem [http://support.microsoft.com/kb/2679367](http://support.microsoft.com/kb/2679367)|E:\Source$\SQL2008R2SP1CU6|  
|System Center 2012 R2 Configuration Manager z nośnika produktu|E:\Source$\ConfigMgr|  
|Wersja pakietu Office Professional Plus 2010 32-bitowych licencjonowania zbiorowego z nośnika produktu|E:\ \OfficeProPlus2010 $ źródła|  

###  <a name="InstalltheADDSServerRole"></a>Krok 1-4. Instalowanie roli serwera DS AD  
 Usługi AD DS jest wymagana do zapewnienia uwierzytelniania i działa jako repozytorium dla wartości konfiguracji dla produktów firmy Microsoft i technologie, które używa zestawu MDT, takich jak Microsoft SQL Server i programu Configuration Manager.  

 Do zainstalowania usług AD DS, uruchom Kreatora DCPROMO, aby skonfigurować komputer jako kontroler domeny. Instalowanie usług AD DS, korzystając z informacji w tabeli 5, akceptując wartości domyślne, chyba że określono inaczej.  

### <a name="table-5-information-for-installing-ad-ds"></a>Tabela 5. Informacje dotyczące instalowania usług AD DS  

|**Po wyświetleniu monitu** |**W tym** |  
|-|-|  
|Dla typu domeny|Utwórz nową domenę w nowym lesie.|  
|Aby uzyskać w pełni kwalifikowaną nazwę domeny|Typ **mdt2013.corp.woodgrovebank.com**.|  
|Aby uzyskać poziom funkcjonalności lasu|Wybierz **systemu Windows Server 2008 R2.** |  
|Aby zainstalować usługę serwera DNS w ramach procesu instalacji kontrolera domeny|Kliknij przycisk **Tak**.|  

###  <a name="InstalltheDHCPServerServerRole"></a>Krok 1-5. Instalowanie roli serwera serwer DHCP  
 Rola serwera serwer DHCP są wymagane do świadczenia automatycznej konfiguracji adresu IP dla komputerów docelowych. Zainstaluj serwer DHCP, korzystając z informacji w tabeli 6, akceptując wartości domyślne, chyba że określono inaczej.  

> [!NOTE]
>  Jeśli używasz środowisku zwirtualizowanym, wyłącz całą konfigurację protokołu DHCP, która zapewnia oprogramowania wirtualizacji komputerów. Upewnij się, że usługa serwera DHCP, systemem WDG-MDT-01 jest to jedyny dostawca konfiguracji adresu IP za pomocą protokołu DHCP.  

### <a name="table-6-information-for-installing-the-dhcp-server-server-role"></a>Tabela 6. Informacje dotyczące instalowania roli serwera serwer DHCP  

|**Na tej stronie kreatora** |**W tym** |  
|-|-|  
|**Autoryzuj serwer DHCP w usłudze Active Directory** |Autoryzacja WDG-zestawu MDT-01, aby zapewnić konfiguracji adresu IP klienta.|  
|**Zakresy DHCP** |Utwórz odpowiedni zakres, który może służyć do automatycznego konfigurowania protokołu TCP/IP dla WDG-REF-01 i WDG-CLI-01.|  
|**Konfiguracji trybu bezstanowego protokołu DHCPv6** |Wyłącz tryb bezstanowego protokołu DHCPv6 dla tego serwera.|  

###  <a name="InstalltheWebServicesServerRole"></a>Krok 1 — 6: Zainstaluj rolę serwera sieci Web Services (IIS)  
 Zainstaluj rolę serwera usług sieci Web (IIS) z usług ról, wymienione w tabeli 7, które są wymagane dla programu SQL Server 2008 R2 i Configuration Manager. Jeżeli nie określono inaczej, należy użyć wartości domyślnych.  

### <a name="table-7-information-for-installing-the-web-services-iis-server-role"></a>Tabela 7. Informacje dotyczące instalowania roli serwera sieci Web Services (IIS)  

|**Usługi roli** |**Stan** |  
|-|-|  
|Serwer sieci Web|zainstalowany|  
|Wspólne funkcje HTTP|zainstalowany|  
|Zawartość statyczna|zainstalowany|  
|Dokument domyślny|zainstalowany|  
|Przeglądanie katalogów|zainstalowany|  
|Błędy HTTP|zainstalowany|  
|Przekierowywanie HTTP|zainstalowany|  
|Publikowanie WebDAV|zainstalowany|  
|Projektowanie aplikacji|zainstalowany|  
|Platforma ASP.NET|zainstalowany|  
|Rozszerzenia platformy .NET|zainstalowany|  
|ASP|Nie jest zainstalowany|  
|CGI|Nie jest zainstalowany|  
|Rozszerzenia ISAPI|zainstalowany|  
|Filtry ISAPI|zainstalowany|  
|Dołączenia po stronie serwera|Nie jest zainstalowany|  
|Kondycja i Diagnostyka|zainstalowany|  
|Rejestrowanie HTTP|zainstalowany|  
|Narzędzia rejestrowania|zainstalowany|  
|Monitor żądań|zainstalowany|  
|Śledzenie|zainstalowany|  
|Rejestrowanie niestandardowe|Nie jest zainstalowany|  
|Rejestrowanie ODBC|Nie jest zainstalowany|  
|Zabezpieczenia|zainstalowany|  
|uwierzytelniania podstawowego|Nie jest zainstalowany|  
|Uwierzytelnianie systemu Windows|zainstalowany|  
|Uwierzytelnianie szyfrowane|Nie jest zainstalowany|  
|Uwierzytelnianie mapowań certyfikatów klientów|Nie jest zainstalowany|  
|Uwierzytelnianie mapowań certyfikatów klientów usług IIS|Nie jest zainstalowany|  
|Autoryzacja adresów URL|Nie jest zainstalowany|  
|Filtrowanie żądań|zainstalowany|  
|Adres IP i ograniczenia domeny|Nie jest zainstalowany|  
|Wydajność|zainstalowany|  
|Kompresja zawartości statycznej|zainstalowany|  
|Kompresja zawartości dynamicznej|Nie jest zainstalowany|  
|Narzędzia zarządzania|zainstalowany|  
|Konsola zarządzania usługami IIS|zainstalowany|  
|Narzędzia i skrypty zarządzania usługami IIS|Nie jest zainstalowany|  
|Usługa zarządzania|Nie jest zainstalowany|  
|Zgodność z narzędziami zarządzania usługami IIS 6|zainstalowany|  
|Zgodność z metabazą usług IIS 6|zainstalowany|  
|Zgodność z usługą WMI dla usług IIS 6|zainstalowany|  
|Narzędzia obsługi skryptów 6 w usługach IIS|Nie jest zainstalowany|  
|Konsola 6 zarządzania usługami IIS|Nie jest zainstalowany|  
|Usługa publikowania FTP|Nie jest zainstalowany|  
|Serwer FTP|Nie jest zainstalowany|  
|Konsola zarządzania usługą FTP|Nie jest zainstalowany|  
|Mogące pełnić rolę hosta sieci Web usług IIS|Nie jest zainstalowany|  

###  <a name="AddtheRequiredWindowsServer2008Features"></a>Krok 1-7: Dodać funkcje wymagane systemu Windows Server 2008 R2  
 Oprócz instalowanie wymaganych ról serwera Windows Server 2008 R2, Dodaj następujące wymagane funkcje w Menedżerze serwera w **Podsumowanie funkcji** sekcji:  

-   Usługa inteligentnego transferu w tle  

-   Kompresja RDC  

###  <a name="CreatetheRequiredUserandServiceAccounts"></a>Krok 1 – 8. Utwórz wymagane użytkownika i kont usług  
 Program Configuration Manager i programu SQL Server 2008 R2 wymagają konta użytkowników podczas procesu instalacji. Tabela 8 zawiera informacje potrzebne do tworzenia tych kont.  

### <a name="table-8-information-for-creating-the-required-accounts"></a>Tabela 8. Informacje dotyczące tworzenia konta wymagane  

|**To konto** |**Przy użyciu tych ustawień** |  
|-|-|  
|Konto usługi programu SQL Server Agent|1.  W **imię**, typ **SQL Agent**.<br />2.  W **nazwisko**, typ **konta usługi**.<br />3.  W **nazwa logowania użytkownika**, typ **SQLAgent**.<br />4.  W **hasło** i **Potwierdź hasło**, typ  **P@ssw0rd** .<br />5.  Wyczyść **użytkownik musi zmienić hasło przy następnym logowaniu** pole wyboru.<br />6.  Wybierz **hasło nigdy nie wygasa** pole wyboru.<br />7.  Należy to konto jest członkiem grupy zabezpieczeń Administratorzy domeny.<br />8.  W **opis**, typ **konto używane do uruchamiania usługi agenta programu SQL Server 2008 R2 usługi**.|  
|Konto usługi aparatu bazy danych programu SQL Server|1.  W **imię**, typ **aparat bazy danych SQL**.<br />2.  W **nazwisko**, typ **konta usługi**.<br />3.  W **nazwa logowania użytkownika**, typ **SQLDBEngine**.<br />4.  W **hasło** i **Potwierdź hasło**, typ  **P@ssw0rd** .<br />5.  Wyczyść **użytkownik musi zmienić hasło przy następnym logowaniu** pole wyboru.<br />6.  Wybierz **hasło nigdy nie wygasa** pole wyboru.<br />7.  Należy to konto jest członkiem grupy zabezpieczeń Administratorzy domeny.<br />8.  W **opis**, typ **konto używane do uruchamiania aparatu bazy danych programu SQL Server 2008 R2 usługi**.|  
|Konto usługi programu SQL Server Reporting Services|1.  W **imię**, typ **SQL Reporting**.<br />2.  **W nazwie ostatniego**, typ **konta usługi**.<br />3.  W **nazwa logowania użytkownika**, typ **SQLReport**.<br />4.  W **hasło** i **Potwierdź hasło**, typ  **P@ssw0rd** .<br />5.  Wyczyść **użytkownik musi zmienić hasło przy następnym logowaniu** pole wyboru.<br />6.  Wybierz **hasło nigdy nie wygasa** pole wyboru.<br />7.  Należy to konto jest członkiem grupy zabezpieczeń Administratorzy domeny.<br />8.  W **opis**, typ **konto używane do uruchamiania programu SQL Server 2008 R2 reporting services usługi**.|  
|Konta dostępu do sieci klienta Menedżera konfiguracji centrum systemowego|1.  W **imię**, typ **CM 2012**.<br />2.  W **nazwisko**, typ **dostępu do sieci klienta**.<br />3.  W **logowania użytkownika** nazw, typu **CMNetAccess**.<br />4.  W **hasło** i **Potwierdź hasło**, typ  **P@ssw0rd** .<br />5.  Wyczyść **użytkownik musi zmienić hasło przy następnym logowaniu** pole wyboru.<br />6.  Wybierz **hasło nigdy nie wygasa** pole wyboru.<br />7.  W **opis**, typ **konto używane jako konto dostępu do sieci dla klienta programu Configuration Manager usługi**.|  

###  <a name="InstallSQLServer2008"></a>Krok 1-9. Zainstaluj program SQL Server 2008 R2  
 Przed zainstalowaniem programu Configuration Manager, należy zainstalować program SQL Server 2008 R2 z dodatkiem SP1 i CU6.  

> [!NOTE]
>  Aby włączyć wszystkie funkcje programu SQL Server 2008 R2, należy zainstalować rolę serwera usług sieci Web (IIS), przed zainstalowaniem programu SQL Server 2008 R2.  

 **Aby zainstalować program SQL Server 2008 R2**  

1.  Uruchomić Centrum instalacji programu SQL Server.  

2.  W Centrum instalacji programu SQL Server, w okienku nawigacji kliknij **instalacji**.  

3.  W okienku podglądu kliknij **nowej instalacji lub dodać funkcje do istniejącej instalacji**.  

     Zostanie uruchomiony Kreator instalacji programu SQL Server 2008 R2.  

4.  Zainstaluj program SQL Server 2008 R2, korzystając z informacji w tabeli 9, zaakceptuj ustawienia domyślne, chyba że określono inaczej.  

    ### <a name="table-9-information-for-installing-sql-server-2008-r2"></a>Tabela 9. Informacje dotyczące instalowania programu SQL Server 2008 R2  

    |**Na tej stronie kreatora** |**W tym** |  
    |-|-|  
    |**Reguły obsługi instalacji** |Kliknij przycisk **OK**.|  
    |**Klucz produktu** |Kliknij przycisk **Dalej**.|  
    |**Postanowienia licencyjne** |Wybierz **akceptuję postanowienia licencyjne** pole wyboru, a następnie kliknij przycisk **dalej**.|  
    |**Pliki obsługi Instalatora** |Kliknij pozycję **Zainstaluj**.|  
    |**Reguły obsługi instalacji** |Upewnij się, czy istnieje dla reguł krytyczne nie zwróciło żadnych wyników, a następnie kliknij **dalej**.|  
    |**Rola Instalatora** |Kliknij przycisk **instalacja funkcji programu SQL Server**, a następnie kliknij przycisk **dalej**.|  
    |**Wybór funkcji** |1.  Wybierz **usługi aparatu bazy danych** pole wyboru.<br />2.  Wybierz **usług Reporting Services** pole wyboru.<br />3.  Wybierz **wyszukiwanie pełnotekstowe** pole wyboru.<br />4.  Wybierz **narzędzia do zarządzania — zakończenie** pole wyboru.<br />5.  Kliknij przycisk **Dalej**.|  
    |**Reguły instalacji** |Kliknij przycisk **Dalej**.|  
    |**Konfiguracja wystąpienia** |Kliknij przycisk **Dalej**.|  
    |**Wymagania dotyczące miejsca na dysku** |Kliknij przycisk **Dalej**.|  
    |**Konfiguracja serwera** |1.  Dla **programu SQL Server Agent**w **nazwa konta**, typ **MDT2013\SQLAgent**w **hasło**, typ  **P@ssw0rd** .<br />2.  Dla **aparatu bazy danych programu SQL Server**w **nazwa konta**, typ **MDT2013\SQLDBEngine**w **hasło**, typ  **P@ssw0rd** .<br />3.  Dla **programu SQL Server Reporting Services**w **nazwa konta**, typ **MDT2013\SQLReport**w **hasło**, typ  **P@ssw0rd** .<br />4.  Kliknij przycisk **Dalej**.|  
    |**Konfiguracja aparatu bazy danych** |Kliknij przycisk **Dodaj bieżącego użytkownika**, a następnie kliknij przycisk **dalej**.|  
    |**Konfiguracja usług raportowania** |Kliknij przycisk **Dalej**.|  
    |**Raportowanie błędów** |Kliknij przycisk **Dalej**.|  
    |**Reguły konfiguracji instalacji** |Kliknij przycisk **Dalej**.|  
    |**Gotowy do instalacji** |Kliknij pozycję **Zainstaluj**.|  
    |**Zakończenie** |Kliknij przycisk **Zamknij**.|  

5.  Zamknij Centrum instalacji programu SQL Server.  

 **Aby zainstalować program SQL Server 2008 R2 z dodatkiem SP1**  

1.  W Eksploratorze Windows przejdź do E:\Source$\SQL2008R2SP1, a następnie kliknij dwukrotnie **SQLServer2008R2SP1-KB2528583-x64-ENU.exe**.  

     **Wyodrębnianie plików** proces wyodrębniania pliku wyświetla okno dialogowe. Po zakończeniu procesu zostanie uruchomiony Kreator konfiguracji SQL Server 2008 R2 Service Pack 1 aktualizacji.  

2.  Zainstaluj program SQL Server 2008 R2 SP1 korzystając z informacji w tabeli 10, zaakceptuj ustawienia domyślne, chyba że określono inaczej.  

    ### <a name="table-10-information-for-installing-sql-server-2008-r2-sp1"></a>Tabela 10. Informacje dotyczące instalowania programu SQL Server 2008 R2 z dodatkiem SP1  

    |**Na tej stronie kreatora** |**W tym** |  
    |-|-|  
    |**Aktualizacja programu SQL Server 2008 R2** |Kliknij przycisk **Dalej**.|  
    |**Postanowienia licencyjne** |Wybierz **akceptuję postanowienia licencyjne** pole wyboru, a następnie kliknij przycisk **dalej**.|  
    |**Wybieranie funkcji** |Kliknij przycisk **Dalej**.|  
    |**Sprawdź pliki w użyciu** |Kliknij przycisk **Dalej**.|  
    |**Gotowy do aktualizacji** |Kliknij przycisk **aktualizacji**.|  
    |**Postęp aktualizacji** |Postęp jest wyświetlany na stronie kreatora aktualizacji jest wykonywane i zakończeniu.|  
    |**Zakończenie** |Kliknij przycisk **Zamknij**.|  

 **Aby zainstalować program SQL Server 2008 R2 z dodatkiem SP1 CU6**  

1.  W Eksploratorze Windows przejdź do E:\Source$\SQL2008R2SP1CU6, a następnie kliknij dwukrotnie **446622_intl_x64_zip.exe**.  

     **Microsoft Extractor** zostanie wyświetlone okno dialogowe.  

2.  W **Microsoft Extractor** okno dialogowe, kliknij przycisk **Kontynuuj**.  

3.  W **Microsoft Extractor** okna dialogowego, **wybierz folder, w którym ma zostać rozpakowane pliki**, typ **E:\Source$\SQL2008R2SP1CU6**, a następnie kliknij przycisk  **OK**.  

    > [!NOTE]
    >  Możesz kliknąć na przeglądanie w poszukiwaniu folderu E:\Source$\SQL2008R2SP1CU6 wielokropka (...).  

     Proces wyodrębniania jest wyświetlany. Po zakończeniu procesu wyświetlany jest stan ukończenia.  

4.  W **Microsoft Extractor** okno dialogowe, kliknij przycisk **OK**.  

5.  W Eksploratorze Windows przejdź do E:\Source$\SQL2008R2SP1CU6, a następnie kliknij dwukrotnie **SQLServer2008R2-KB2679367-x64.exe**.  

     **Wyodrębnianie plików** proces wyodrębniania pliku wyświetla okno dialogowe. Po zakończeniu procesu uruchamiania programu SQL 2008 R2 z dodatkiem Service Pack 1 CU6 aktualizacji Kreatora instalacji serwera.  

6.  Zainstaluj program SQL Server 2008 R2 z dodatkiem SP1 CU6 korzystając z informacji w tabeli 11, zaakceptuj ustawienia domyślne, chyba że określono inaczej.  

    ### <a name="table-11-information-for-installing-sql-server-2008-r2-sp1-cu6"></a>Tabela 11. Informacje dotyczące instalowania programu SQL Server 2008 R2 z dodatkiem SP1 CU6  

    |**Na tej stronie kreatora** |**W tym** |  
    |-|-|  
    |**Aktualizacja programu SQL Server 2008 R2** |Kliknij przycisk **Dalej**.|  
    |**Postanowienia licencyjne** |Wybierz **akceptuję postanowienia licencyjne** pole wyboru, a następnie kliknij przycisk **dalej**.|  
    |**Wybieranie funkcji** |Kliknij przycisk **Dalej**.|  
    |**Sprawdź pliki w użyciu** |Kliknij przycisk **Dalej**.|  
    |**Gotowy do aktualizacji** |Kliknij przycisk **aktualizacji**.|  
    |**Postęp aktualizacji** |Postęp jest wyświetlany na stronie kreatora aktualizacji jest wykonywane i zakończeniu.|  
    |**Zakończenie** |Kliknij przycisk **Zamknij**.|  

     **Zainstalowanie aktualizacji programu SQL Server 2008 R2** zostanie wyświetlone okno dialogowe monitowania użytkownika o ponowne uruchomienie komputera w celu ukończenia instalacji.  

7.  W **zainstalowanie aktualizacji programu SQL Server 2008 R2** okno dialogowe, kliknij przycisk **OK**.  

8.  Uruchom ponownie komputer.  

9. Po zainstalowaniu programu SQL Server 2008 R2 z dodatkiem SP1 CU6, numer kompilacji programu SQL Server należy 10.51.2811.0.  

    > [!TIP]
    >  Sprawdź numer kompilacji programu SQL Server, wyświetlając zastosowanych w aplecie Programy i funkcje w Panelu sterowania po kliknięciu elementu aktualizacji programu SQL Server **Wyświetl zainstalowane aktualizacje**.  

###  <a name="AddtheSiteServertotheAdministratorsSecurityGroup"></a>Krok 1-10. Dodaj serwer lokacji do grupy zabezpieczeń Administratorzy  
 Gdy wszystkie komputery znajdują się w tym samym lesie, należy ręcznie dodać konto komputera serwera lokacji do lokalnej grupy administratorów na każdym komputerze. Ten krok należy wykonać przed rozpoczęciem konfigurowania komputera jako system lokacji.  

 **Aby dodać serwer lokacji do grupy zabezpieczeń Administratorzy**  

1.  Kliknij przycisk **Start**, wskaż polecenie **narzędzia administracyjne**, a następnie kliknij przycisk **użytkownicy usługi Active Directory i komputery**.  

2.  W drzewie konsoli Użytkownicy usługi Active Directory i komputery przejdź do mdt2013.corp.woodgrovebank.com/Builtin.  

3.  W okienku podglądu kliknij prawym przyciskiem myszy **Administratorzy**, a następnie kliknij przycisk **właściwości**.  

4.  W **właściwości Administratorzy** okno dialogowe, kliknij przycisk **członków** , a następnie kliknij pozycję **Dodaj**.  

5.  W **Wybieranie: użytkownicy, kontakty, komputery lub grupy** okno dialogowe, kliknij przycisk **typy obiektów**.  

6.  W **typy obiektów** okna dialogowego, **typy obiektów**, wybierz pozycję **komputerów**, a następnie kliknij przycisk **OK**.  

7.  W **Wybieranie: użytkownicy, kontakty, komputery lub grupy** okna dialogowego, **wprowadź nazwy obiektów do wybrania**, typ **WDG-MDT-01**. Kliknij przycisk **Sprawdź nazwy**, a następnie kliknij przycisk **OK**.  

8.  Zamknij wszystkie otwarte okna.  

###  <a name="InstallConfigurationManager"></a>Krok 1-11. Instalowanie programu Configuration Manager  
 Podczas instalowania innych produktów i technologii, instalowanie programu Configuration Manager. Przed dokonaniem, jednak rozszerzyć schemat usługi Active Directory, aby komputery mogły zlokalizować punkty dystrybucji, punkty lokalizatora usług i innych ról serwera. Ponadto można rozszerzyć schemat, po zainstalowaniu programu Configuration Manager. Aby uzyskać więcej informacji na temat rozszerzania schematu usługi Active Directory programu Configuration Manager zobacz sekcję "Rozszerzyć schemat usługi Active Directory" w bibliotece dokumentacji programu Configuration Manager, który jest instalowany z programem Configuration Manager.  

 Po rozszerzeniu schematu usługi Active Directory, można zainstalować programu Configuration Manager. Konfiguracja WDG-MDT-01 obsługi programu Configuration Manager dla tego przykładu. Konfiguracja komputerów w sieci produkcyjnej może się różnić. Aby dowiedzieć się więcej na temat wymagań wstępnych dotyczących instalowania programu Configuration Manager, zobacz [obsługiwane konfiguracje programu Configuration Manager](http://technet.microsoft.com/library/gg682077.aspx).  

 **Aby zainstalować program Configuration Manager**  

1.  Uruchom Instalator programu System Center 2012 R2 Configuration Manager ekranu powitalnego.  

2.  Na ekranie powitalnym Instalator programu System Center 2012 R2 Configuration Manager kliknij przycisk **zainstalować** łącza.  

     Uruchamia Kreatora programu Microsoft System Center 2012 R2 Configuration Manager Instalatora.  

3.  Ukończ Kreatora programu Microsoft System Center 2012 R2 konfiguracji Menedżera konfiguracji korzystając z informacji w tabeli 12. Zaakceptuj ustawienia domyślne, chyba że określono inaczej.  

    ### <a name="table-12-information-for-installing-configuration-manager"></a>Tabela 12. Informacje dotyczące instalowania programu Configuration Manager  

    |**Na tej stronie kreatora** |**W tym** |  
    |-|-|  
    |**Przed rozpoczęciem** |Kliknij przycisk **Dalej**.|  
    |**Wprowadzenie** |Kliknij przycisk **Dalej**.|  
    |**Klucz produktu** |W **wprowadź klucz produktu 25-znakowy**, typ ***klucz_produktu*** (gdzie *klucz_produktu* jest klucz produktu programu Configuration Manager).|  
    |**Postanowienia licencyjne dotyczące oprogramowania firmy Microsoft** |Wybierz **akceptuję postanowienia licencyjne** pole wyboru, a następnie kliknij przycisk **dalej**.|  
    |**Aktualizacja wstępnie wymagane składniki** |W **pobrania i zastosowania najnowszych aktualizacji. Aktualizacje zostaną zapisane w następującej lokalizacji**, typ **E:\CMDownloads**, a następnie kliknij przycisk **dalej**.|  
    |**Wybór języka serwera** |Kliknij przycisk **Dalej**.|  
    |**Wybór języka klienta** |Kliknij przycisk **Dalej**.|  
    |**Ustawienia lokacji i instalacji** |1.  W **kod lokacji**, typ **NYC**.<br />2.  W **nazwa witryny**, typ **lokacji nowego Jorku**.<br />3.  Kliknij przycisk **Dalej**.|  
    |**Instalacja lokacji podstawowej** |1.  Kliknij przycisk **zainstalować lokację główną jako autonomiczną**.<br />2.  Kliknij przycisk **Dalej**.<br />     **Programu Configuration Manager** zostanie wyświetlone okno dialogowe potwierdzenia chcesz zainstalować tę lokację jako autonomiczną lokację.<br />3.  W **programu Configuration Manager** okno dialogowe, kliknij przycisk **tak**.|  
    |**Informacje o bazie danych** |Kliknij przycisk **Dalej**.|  
    |**Ustawienia dostawcy programu SMS** |Kliknij przycisk **Dalej**.|  
    |**Ustawienia komunikacji z komputerem klienckim** |Kliknij przycisk **Konfiguruj metodę komunikacji w każdej roli systemu lokacji**, a następnie kliknij przycisk **dalej**.|  
    |**Role systemu lokacji** |Kliknij przycisk **Dalej**.|  
    |**Konfiguracja programu poprawy jakości obsługi klienta** |Wybierz odpowiedni udział w programie poprawy jakości obsługi klienta dla Twojej organizacji, a następnie kliknij przycisk **dalej**.|  
    |**Podsumowanie ustawień** |Kliknij przycisk **Dalej**.|  
    |**Sprawdzanie wymagań wstępnych** |Kliknij przycisk **rozpocząć instalację**.|  
    |**Instalowanie** |Monitorowanie procesu instalacji, do czasu jego zakończenie, a następnie kliknij przycisk **Zamknij**.|  

4.  Zamknij wszystkie otwarte okna i oknach dialogowych.  

 Po ukończeniu działania kreatora programu Configuration Manager jest zainstalowany.  

###  <a name="ConfiguretheNetworkAccessAccount"></a>Krok 1-12. Konfigurowanie konta dostępu do sieci  
 Klient programu Configuration Manager potrzebuje konta, aby podać poświadczenia podczas uzyskiwania dostępu do punktów dystrybucji programu Configuration Manager, udział wdrożenia zestawu MDT i folderów udostępnionych. To konto jest nazywany *konta dostępu do sieci*. Konto CMNetAccess zostało utworzone wcześniej w trakcie procesu do użycia jako konto dostępu do sieci.  

 **Aby skonfigurować konto dostępu do sieci**  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **administracji**.  

3.  W obszarze roboczym Administracja go — Omówienie/lokacji konfiguracji/lokacji.  

4.  W okienku podglądu kliknij **NYC — lokacji nowego Jorku**.  

5.  Na wstążce kliknij **ustawienia**, kliknij przycisk **Konfiguruj składniki lokacji**, a następnie kliknij przycisk **dystrybucji oprogramowania**.  

6.  W **właściwości dystrybucji oprogramowania** okno dialogowe, kliknij przycisk **konta dostępu do sieci** kartę.  

7.  W **konta dostępu do sieci**, kliknij przycisk **Określ konto, który uzyskał dostęp do lokalizacji sieciowych**, kliknij przycisk **ustawić**, a następnie kliknij przycisk **nowe konto**.  

     **Konta użytkownika systemu Windows** zostanie wyświetlone okno dialogowe.  

8.  Zakończenie **konta użytkownika systemu Windows** korzystając z informacji w tabeli 13, a następnie kliknij okno dialogowe **OK**.  

    ### <a name="table-13-information-required-to-complete-the-windows-user-account-dialog-box"></a>Tabela 13. Informacje wymagane do utworzenia okna dialogowego konta użytkownika systemu Windows  

    |**Dla tego** |**W tym** |  
    |-|-|  
    |**Nazwa użytkownika** |Typ **MDT2013\CMNetAccess**.|  
    |**Hasło** |Typ  **P@ssw0rd** .|  
    |**Potwierdź hasło** |Typ  **P@ssw0rd** .|  

9. W **właściwości dystrybucji oprogramowania** okno dialogowe, kliknij przycisk **OK**.  

10. Zamknij wszystkie otwarte okna.  

###  <a name="ConfiguretheConfigurationManagerSiteBoundaries"></a>Krok 1-13. Konfigurowanie granic lokacji programu Configuration Manager i grup granic  
 Klient programu Configuration Manager musi znać granice lokacji. O ile nie określono granicach lokacji, klient zakłada, że komputera z uruchomionym programu Configuration Manager w lokacji zdalnej. Dodaj granicę lokacji, na podstawie podsieci IP tego WDG-MDT-01, WDG-REF-01 i użycie WDG-CLI-01. Następnie należy dodać granicę lokacji do grupy granic lokacji.  

 **Aby utworzyć granicę lokacji programu Configuration Manager**  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsola programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **administracji**.  

3.  W obszarze roboczym Administracja go — omówienie/hierarchia konfiguracji/granic.  

4.  Na wstążce kliknij **Utwórz granicę**.  

     **Utwórz granicę** zostanie otwarte okno dialogowe.  

5.  Zakończenie **Utwórz granicę** korzystając z informacji w tabeli 14, a następnie kliknij okno dialogowe **OK**.  

    > [!NOTE]
    >  Dla tego przykładu granicę lokacji jest określany przez adres sieciowy. Jednak można również określić lokacji granice lokacji za pomocą usług AD DS, nazwa lub zakres adresów IP.  

    ### <a name="table-14-information-required-to-complete-the-create-boundary-dialog-box"></a>Tabela 14. Informacje wymagane do ukończenia tworzenie granic, okno dialogowe  

    |**Dla tego** |**W tym** |  
    |-|-|  
    |**Opis** |Typ **granicę podsieci IP**.|  
    |**Typ** |Wybierz **podsieci IP**.|  
    |Sieć|Typ ***network_address*** (gdzie *network_address* jest adres sieciowy podsieci, gdy komputery są zainstalowane).|  
    |**Maska podsieci** |Typ ***subnet_mask*** (gdzie *subnet_mask* to maska podsieci podsieci, gdy komputery są zainstalowane).|  

 **Aby dodać granicę lokacji programu Configuration Manager do grupy granic lokacji**  

1.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **administracji**.  

2.  W obszarze roboczym Administracja przejdź do grupy konfiguracji/granic przegląd/hierarchii.  

3.  Na wstążce kliknij **Utwórz grupę granicę**.  

     **Utwórz grupę granicę** zostanie otwarte okno dialogowe.  

4.  Zakończenie **ogólne** karcie **Utwórz grupę granicę** okno dialogowe, korzystając z informacji w tabeli 15.  

    ### <a name="table-arabic-15-information-required-to-complete-the-general-tab-of-the-create-boundary-group-dialog-box"></a>Tabela ARABIC 15. Informacje wymagane do utworzenia karty Ogólne okno dialogowe Tworzenie grupy granic  

    |**Dla tego** |**W tym** |  
    |-|-|  
    |**Nazwa** |Typ **grupy granic w Nowym Jorku**.|  
    |Opis|Typ **grupy granic do granic lokacji w lokacji nowego Jorku**.|  
    |**Granice** |1.  Kliknij pozycję **Dodaj**.<br />     **Dodać granice** zostanie wyświetlone okno dialogowe.<br />2.  W **dodać granice** okno dialogowe, wybierz opcję ***site_boundary*** (gdzie *site_boundary* jest granicę lokacji został utworzony wcześniej w procesie), a następnie kliknij przycisk **OK**.<br />     Granicę lokacji zostanie wyświetlony na liście granic.|  

5.  Zakończenie **odwołania** karty **Utwórz grupę granicę** korzystając z informacji w tabeli 16, a następnie kliknij okno dialogowe **OK**.  

    ### <a name="table-16-information-required-to-complete-the-references-tab-of-the-create-boundary-group-dialog-box"></a>Tabela 16. Informacje wymagane do ukończenia karcie odwołania grupy granic, okno dialogowe Tworzenie  

    |**Dla tego** |**W tym** |  
    |-|-|  
    |**Przypisanie lokacji** |Wybierz **Użyj tej grupy granic do przypisania lokacji** pole wyboru.|  
    |**Lokalizacja zawartości** |1.  Kliknij pozycję **Dodaj**.<br />     **Dodać systemy lokacji** zostanie wyświetlone okno dialogowe.<br />2.  W **dodać systemy lokacji** okno dialogowe, wybierz opcję  **\\\WDG-MDT-01.mdt2013.corp.woodgrovebank.com**, a następnie kliknij przycisk **OK**.<br />     Serwer systemu lokacji zostanie wyświetlony na liście serwerów systemu lokacji.|  

6.  Zamknij wszystkie otwarte okna.  

###  <a name="ConfigurethePublishingofSiteIntofrmation"></a>Krok 1-14. Skonfiguruj publikowanie informacji o lokacji w usługach AD DS i systemu DNS  
 Klient programu Configuration Manager musi zlokalizować różne role serwera programu Configuration Manager. Modyfikuj właściwości lokacji do publikowania informacji o lokacji w usługach AD DS, a w systemie DNS.  

 **Aby skonfigurować publikowanie informacji o lokacji w usługach AD DS, a w systemie DNS**  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **administracji**.  

3.  W obszarze roboczym Administracja go — Omówienie/lokacji konfiguracji/lokacji.  

4.  W okienku podglądu kliknij **NYC — lokacji nowego Jorku**.  

5.  Na wstążce kliknij **właściwości**.  

6.  W **właściwości lokacji nowego Jorku** na okna dialogowego **publikowania** karcie, upewnij się, że **mdt2013.corp.woodgrovebank.com** lasu usługi Active Directory jest wyświetlana, i następnie kliknij przycisk **anulować**.  

7.  Zamknij wszystkie otwarte okna.  

###  <a name="ConfigureDiscoveryofActiveDirectoryUsers"></a>Krok 1 – 15. Konfigurowanie odnajdywania użytkowników usługi Active Directory  
 W niektórych przypadkach oprogramowanie zostanie wdrożone w kolekcjach użytkowników, które umożliwia odnalezienie programu Configuration Manager. Menedżer konfiguracji może odnajdywania kont użytkowników przechowywanych w usługach AD DS za pomocą metody odnajdywania użytkownika usługi Active Directory.  

 **Aby skonfigurować odnajdywanie użytkowników usługi Active Directory**  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **administracji**.  

3.  W obszarze roboczym Administracja przejdź do metody odnajdywania-przegląd/hierarchii.  

4.  W okienku podglądu kliknij **odnajdywania użytkownika usługi Active Directory**.  

5.  Na wstążce na **Home** , kliknij pozycję **właściwości**.  

     **Właściwości odnajdywania użytkownika usługi Active Directory** zostanie wyświetlone okno dialogowe.  

6.  W **właściwości odnajdywania użytkownika usługi Active Directory** na okna dialogowego **ogólne** karcie, wykonaj następujące czynności:  

    1.  Wybierz **włączyć użytkownika odnajdywania usługi Active Directory** pole wyboru.  

    2.  W **kontenerach usługi Active Directory**, kliknij przycisk **nowy**.  

         **Nowy kontener usługi Active Directory** zostanie wyświetlone okno dialogowe.  

    3.  W **nowy kontener usługi Active Directory** okna dialogowego, **ścieżki**, kliknij przycisk **Przeglądaj**.  

         **Wybierz nowy kontener** zostanie wyświetlone okno dialogowe.  

    4.  W **wybierz nowy kontener** okno dialogowe, kliknij przycisk **mdt2013**, a następnie kliknij przycisk **OK**.  

         W **nowy kontener usługi Active Directory** , ścieżka dostępu protokołu LDAP (Lightweight Directory) zostanie wyświetlone okno dialogowe w **ścieżki** pole.  

    5.  W **nowy kontener usługi Active Directory** oknie dialogowym kliknij przycisk OK.  

     Ścieżkę protokołu LDAP jest wyświetlana w **kontenerach usługi Active Directory** pola listy.  

7.  W **właściwości odnajdywania użytkownika usługi Active Directory** okno dialogowe, kliknij przycisk **OK**.  

     **Programu Configuration Manager** zostanie wyświetlone okno dialogowe, podczas badania czy chcesz przeprowadzić odnajdowanie jak najszybciej.  

8.  W **programu Configuration Manager** okno dialogowe, kliknij przycisk **tak**.  

9. W konsoli programu Configuration Manager, w okienku nawigacji kliknij **zasoby i zgodność**.  

10. W zasoby i zgodność obszaru roboczego, przejdź do użytkowników/Przegląd.  

     W okienku podglądu zostanie wyświetlona lista użytkowników wykrytych w usługach AD DS.  

11. Zamknij wszystkie otwarte okna.  

##  <a name="PreparetheMDTEnvironment"></a>Krok 2. Przygotowanie środowiska zestawu MDT  
 Pierwszym krokiem w procesie wdrażania jest aby przygotować środowisko zestawu MDT. Po zakończeniu tego kroku możesz utworzyć komputer odniesienia i wdrażać przechwycony obraz do komputera docelowego (WDG-CLI-01) przy użyciu integracji programu Configuration Manager z zestawu MDT.  

 Przygotowanie środowiska MDT przez:  

-   Instalowanie zestawu MDT, zgodnie z opisem w [krok 2-1: Instalowanie zestawu MDT](#InstallMDT)  

-   Włączanie integracji konsoli programu Configuration Manager, uruchamiając Kreatora konfigurowania integracji programu ConfigMgr, zgodnie z opisem w [krok 2-2: Włącz integrację z konsoli programu Configuration Manager](#EnableConfigurationManagerConsoleIntegration)  

###  <a name="InstallMDT"></a>Krok 2-1. Instalowanie zestawu MDT  
 Aby zainstalować zestaw MDT, wykonaj następujące czynności:  

1.  W Eksploratorze Windows przejdź do E:\Source$\MDT_2013.  

2.  Kliknij dwukrotnie **MicrosoftDeploymentToolkit2013_x64.msi** (dla 64-bitowych systemach operacyjnych) lub **MicrosoftDeploymentToolkit2013_x86.msi** (dla 32-bitowych systemach operacyjnych), a następnie kliknij przycisk **Zainstalować**.  

     Uruchamia Kreatora instalacji programu Microsoft Deployment Toolkit 2013.  

3.  Ukończ Microsoft Deployment Toolkit 2013 Kreatora instalacji korzystając z informacji w tabeli 17. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    ### <a name="table-17-information-for-completing-the-microsoft-deployment-toolkit-2013-setup-wizard"></a>Tabela 17. Informacje dotyczące Kończenie pracy Kreatora instalacji programu Microsoft Deployment Toolkit 2013  

    |**Na tej stronie kreatora** |**W tym** |  
    |-|-|  
    |**Kreator instalacji 2013 Microsoft Deployment Toolkit — Zapraszamy!** |Kliknij przycisk **Dalej**.|  
    |**Umowa licencyjna użytkownika oprogramowania** |Kliknij przycisk **akceptuję warunki umowy licencyjnej**, a następnie kliknij przycisk **dalej**.|  
    |**Instalacja niestandardowa** |Kliknij przycisk **Dalej**.|  
    |**Gotowy do zainstalowania programu Microsoft Deployment Toolkit 2013** |Kliknij pozycję **Zainstaluj**.|  
    |**Instalowanie zestawu narzędzi firmy Microsoft do wdrażania 2013** |Zostanie wyświetlony pasek postępu instalacji zestawu MDT.|  
    |**Ukończono Kreatora instalacji programu Microsoft Deployment Toolkit 2013** |Kliknij przycisk **Zakończ**.|  

 Ukończeniu działania Kreatora instalacji programu Microsoft Deployment Toolkit 2013 i zestaw MDT jest zainstalowany na WDG-MDT-01.  

###  <a name="EnableConfigurationManagerConsoleIntegration"></a>Krok 2-2. Włącz integrację z konsoli programu Configuration Manager  
 Przed użyciem programu Configuration Manager funkcje integracji zestawu mdt, uruchom Kreatora konfigurowania integracji programu ConfigMgr. Ten kreator skopiuje pliki integracji odpowiednie do folderu, w którym program Configuration Manager jest zainstalowany. Kreator dodaje również klas Instrumentacji zarządzania Windows (WMI), nowe akcje niestandardowe zestawu MDT. Kompilowanie nowego pliku Managed Object Format (MOF), który zawiera nowe definicje klas są dodawane klasy.  

 **Aby włączyć integrację z konsoli programu Configuration Manager**  

> [!NOTE]
>  Upewnij się, że konsola programu Configuration Manager zostały zamknięte podczas wykonywania tych kroków.  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **Konfigurowanie integracji programu ConfigMgr**.  

     Zostanie uruchomiony Kreator konfigurowania integracji programu ConfigMgr.  

2.  Ukończ korzystając z informacji w tabeli 18 Kreatora konfigurowania integracji programu ConfigMgr. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    ### <a name="table-18-information-for-completing-the-configure-configmgr-integration-wizard"></a>Tabela 18. Informacje o zakończeniu konfigurowania Kreator integracji programu ConfigMgr  

    |**Na tej stronie kreatora** |**W tym** |  
    |-|-|  
    |**Opcje** |1.  Sprawdź, czy **Instalowanie zestawu MDT rozszerzeń konsoli programu ConfigMgr 2012** pole wyboru jest zaznaczone.<br />2.  Sprawdź, czy **Dodaj akcje sekwencji zadań zestawu MDT do serwera programu ConfigMgr** pole wyboru jest zaznaczone.<br />3.  W **nazwa serwera lokacji**, sprawdź, czy wartość jest **WDG — MDT-01.mdt2013.corp.woodgrovebank.com**.<br />4.  W **kod lokacji**, sprawdź, czy wartość jest **NYC**.<br />5.  Kliknij przycisk **Dalej**.|  
    |**Potwierdzenie** |Kliknij przycisk **Zakończ**.|  

 Zakończeniu pracy Kreatora konfigurowania integracji programu ConfigMgr, a zestaw MDT jest zintegrowany z programem Configuration Manager.  

## <a name="step-3-create-and-configure-a-task-sequence-to-create-a-reference-computer"></a>Krok 3. Tworzenie i konfigurowanie sekwencji zadań w celu utworzenia komputera odniesienia  
 Po przygotowaniu środowiska zestawu MDT, należy utworzyć komputer odniesienia. Komputer odniesienia jest szablon do wdrażania nowych obrazów na komputerach docelowych. Dokładnie tak, jak skonfiguruje komputerów docelowych, należy skonfigurować komputer (WDG-REF-01). Następnie zostanie przechwycony obraz komputera odniesienia i wdrażania obrazu na komputerach docelowych.  

 Utwórz komputer odniesienia WDG-REF-01 przez:  

-   Tworzenie sekwencji zadań zestawu MDT do wdrożenia Windows 8.1 na komputerze odniesienia, zgodnie z opisem w [krok 3-1: Utwórz sekwencję zadań zestawu MDT do wdrażania na komputerze odniesienia](#CreateMDTTaskSequenceforDeployingReferenceComputer)  

-   Wybieranie punktów dystrybucji dla nowych pakietów i obrazów, które tworzy Kreatora tworzenia sekwencji zadań zestawu MDT, zgodnie z opisem w [krok 3-2: Wybierz punkty dystrybucji dla nowych pakietów i obrazów](#SelectDistributionPointsfortheNewPackages)  

-   Dodawanie sterowników urządzeń na potrzeby nowego pakietu dysku i obrazy rozruchowe odpowiednie zgodnie z opisem w [kroku nr 3, 3: Dodaj sterowniki urządzeń wymagane](#AddtheNecessaryDeviceDrivers)  

-   Włącz monitorowanie procesu wdrożenia zestawu MDT, zgodnie z opisem w [krok 3 — 4: Włącz wdrożenia zestawu MDT monitorowania procesu](#EnableMDTDeploymentProcessMonitoring)  

-   Konfigurowanie pliki konfiguracyjne zestawu MDT dla komputera odniesienia — w szczególności pliku CustomSettings.ini — zgodnie z opisem w [krok 3 – 5: Dostosowywanie pliki konfiguracyjne zestawu MDT dla komputera odniesienia](#CustomizeMDTConfigFilesforReferenceComputer)  

-   Aktualizowanie punkty dystrybucji programu Configuration Manager dla pakietu pliki ustawień niestandardowych, zgodnie z opisem w [krok 3 – 6: Aktualizuj punkty dystrybucji dla pakietu plików ustawień niestandardowych](#UpdateDistributionPointsforCustomSettings)  

-   Dostosowywanie sekwencji zadań dla komputera odniesienia, zgodnie z opisem w [kroku 3-7: Dostosowywanie sekwencji zadań dla komputera odniesienia](#CustomizeTaskSequenceforReferenceComputer)  

###  <a name="CreateMDTTaskSequenceforDeployingReferenceComputer"></a>Krok 3-1. Utwórz sekwencję zadań zestawu MDT do wdrażania na komputerze odniesienia  
 Użyj Kreatora tworzenia sekwencji zadań zestawu MDT w konsoli programu Configuration Manager do tworzenia sekwencji zadań w programie Configuration Manager, które są zintegrowane z zestawu MDT. Zestaw MDT obejmuje szablonu standardowe sekwencję zadań klienta, który służy do wdrażania na komputerze odniesienia.  

 Kreatora tworzenia sekwencji zadań zestawu MDT zastępuje pakiety i obrazy wybrane symboli zastępczych w szablonach sekwencji zadań. Po zakończeniu pracy Kreatora nowej sekwencji zadań odwołuje się do odpowiednich pakietów i obrazów.  

> [!NOTE]
>  Zawsze używać Kreatora tworzenia sekwencji zadań zestawu MDT do tworzenia sekwencji zadań na podstawie szablonów sekwencji zadań zestawu MDT. Mimo że można ręcznie zaimportować szablony sekwencji zadań, firma Microsoft zaleca tego procesu.  

 **Aby utworzyć sekwencję zadań do wdrażania na komputerze odniesienia**  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **Biblioteka oprogramowania**.  

3.  W obszarze roboczym Biblioteka oprogramowania przejdź do Przegląd/operacyjnego systemów lub zadanie sekwencji.  

4.  Na wstążce na **Home** karcie **sekwencje zadań** kliknij przycisk **Utwórz sekwencję zadań zestawu MDT**.  

     Uruchamia Kreatora tworzenia sekwencji zadań zestawu MDT.  

5.  Ukończ MDT Kreatora tworzenia sekwencji zadań przy użyciu informacji w tabeli 19. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    ### <a name="table-19-information-for-completing-the-create-mdt-task-sequence-wizard"></a>Tabela 19. Informacje o zakończeniu Kreator tworzenia sekwencji zadań zestawu MDT  

    |**Na tej stronie kreatora** |**W tym** |  
    |-|-|  
    |**Wybieranie szablonu** |Wybierz **sekwencję zadań klienta**, a następnie kliknij przycisk **dalej**.|  
    |**Wybierz szablon: Ogólne** |1.  W **nazwę sekwencji zadań**, typ **Windows 8.1 odwołanie wdrożenia**.<br />2.  W **komentarze sekwencji zadań**, typ **sekwencję zadań pod kątem wdrażania na komputerze odniesienia (WDG-REF-01) Windows 8.1**, a następnie kliknij przycisk **dalej**.|  
    |**Wybierz szablon: Szczegóły** |1.  Kliknij przycisk **Przyłącz do grupy roboczej**.<br />2.  W **grupy roboczej**, typ **grupy roboczej**.<br />3.  W **nazwy użytkownika**, typ **pracownika banku Woodgrove**.<br />4.  W **nazwa organizacji**, typ **banku Woodgrove**.<br />5.  W **klucz produktu**, typ ***klucz_produktu*** (gdzie *klucz_produktu* jest klucz produktu dla Windows 8.1).<br />6.  Kliknij przycisk **Dalej**.|  
    |**Wybierz szablon: Przechwyć ustawienia** |<ol><li>Kliknij przycisk **ta sekwencja zadań może służyć do przechwytywania i obrazów**.</li><li>W **miejsce docelowe przechwytywania**, typ  **\\\WDG-MDT-01\Capture$\WDG-REF-01.wim**.</li><li>W **konto przechwytywania**, kliknij przycisk **ustawić**.</li><li>Zakończenie **konta użytkownika systemu Windows** okno dialogowe, wykonując następujące czynności:<br /><br /> <ol><li>W **nazwy użytkownika**, typ **MDT2013\Administrator**.</li><li>W **hasło** i **Potwierdź hasło**, typ  **P@ssw0rd** .</li></ol></li><li>Kliknij przycisk **OK**.</li><li>Kliknij przycisk **Dalej**.</li></ol>|  
    |**Obraz rozruchowy** |1.  Kliknij przycisk **utworzyć nowy pakiet obrazu rozruchowego**.<br />2.  W **folderu źródłowego pakietu należy utworzyć**, typ  **\\\WDG-MDT-01\Packages$\WINPE_Custom**, a następnie kliknij przycisk **dalej**.|  
    |**Obraz rozruchowy: Ustawienia ogólne** |1.  W **nazwa**, typ **niestandardowych systemu Windows PE**.<br />2.  W **wersji**, typ **1,00**.<br />3.  W **komentarze**, typ **dostosowane wersję środowiska Windows PE do użycia we wdrożeniu komputerów referencyjnych i docelowych**, a następnie kliknij przycisk **dalej**.|  
    |**Obraz rozruchowy: Opcje** |W obszarze **platformy**, kliknij przycisk **x64**, a następnie kliknij przycisk **dalej**.|  
    |**Obraz rozruchowy: Składniki** |Kliknij przycisk **Dalej**.|  
    |**Obraz rozruchowy: Dostosowywanie** |Kliknij przycisk **Dalej**.|  
    |**Pakiet zestawu MDT** |1.  Kliknij przycisk **utworzyć nowy pakiet plików zestawu narzędzi wdrażania Microsoft**.<br />2.  W **folderu źródłowego pakietu należy utworzyć**, typ  **\\\WDG-MDT-01\Packages$\MDT_Files**, a następnie kliknij przycisk **dalej**.|  
    |**Zestaw MDT pakietu: Szczegóły zestawu MDT** |1.  W **nazwa**, typ **pliki zestawu MDT**.<br />2.  W **wersji**, typ **1,00**.<br />3.  W **komentarze**, typ **zapewnia dostęp do plików zestawu MDT podczas procesu wdrażania programu Configuration Manager**, a następnie kliknij przycisk **dalej**.|  
    |**Obraz systemu operacyjnego** |1.  Kliknij przycisk **pakiet instalacyjny Tworzenie nowego systemu operacyjnego**.<br />2.  W **lokalizacja folderu instalacji systemu operacyjnego**, typ  **\\\WDG-MDT-01\Source$\Windows_8-1**.<br />3.  W **folderu źródłowego pakietu należy utworzyć**, typ  **\\\WDG-MDT-01\Packages$\Windows_8-1**, a następnie kliknij przycisk **dalej**.|  
    |**Obraz systemu operacyjnego: Szczegóły obrazu** |1.  W **nazwa**, typ **Windows 8.1**.<br />2.  W **wersji**, typ **1,00**.<br />3.  W **komentarze**, typ **pakietu Windows 8.1 używane do wdrażania na komputerach odniesienia**, a następnie kliknij przycisk **dalej**.|  
    |**Metody wdrażania** |Kliknij przycisk **Dalej**.|  
    |**Pakiet klienta** |Kliknij przycisk **utworzenia nowego pakietu klienta programu ConfigMgr**, a następnie kliknij przycisk **dalej**.|  
    |**Pakiet USMT** |1.  Kliknij przycisk **utworzyć nowy pakiet narzędzia USMT**.<br />2.  W **folderu źródłowego pakietu należy utworzyć**, typ  **\\\WDG-MDT-01\Packages$\USMT**, a następnie kliknij przycisk **dalej**.|  
    |**Pakiet narzędzia USMT: Szczegóły narzędzia USMT** |1.  W **nazwa**, typ **USMT**.<br />2.  W **wersji**, typ **1,00**.<br />3.  W **komentarze**, typ **pliki narzędzia USMT służące do przechwytywania i przywracania informacje o migracji stanu użytkownika**, a następnie kliknij przycisk **dalej**.|  
    |**Ustawienia pakietu** |1.  Kliknij przycisk **utworzyć nowy pakiet ustawienia**.<br />2.  W **folderu źródłowego pakietu należy utworzyć**, typ  **\\\WDG-MDT-01\Packages$\CustomSettings_Reference**, a następnie kliknij przycisk **dalej**.|  
    |**Pakiet ustawień: Szczegóły ustawień** |1.  W **nazwa**, typ **ustawień niestandardowych komputera odniesienia MDT**.<br />2.  W **wersji**, typ **1,00**.<br />3.  W **komentarze**, typ **ustawienia konfiguracji dla zestawu MDT procesu wdrażania (na przykład CustomSettings.ini) dla komputera odniesienia**, a następnie kliknij przycisk **dalej**.|  
    |**Pakiet programu Sysprep** |Kliknij przycisk **Dalej**.|  
    |**Podsumowanie** |Przejrzyj informacje w **szczegóły** czy podane podczas wykonywania poprzednich stron kreatora, a następnie kliknij przycisk **dalej**.|  
    |**Postęp** |Zostanie wyświetlony pasek postępu tworzenia sekwencji zadań.|  
    |**Potwierdzenie** |Kliknij przycisk **Zakończ**.|  

 Nowej sekwencji zadań zostanie wyświetlony w okienku podglądu.  

###  <a name="SelectDistributionPointsfortheNewPackages"></a>Krok 3-2. Wybierz punkty dystrybucji dla nowych pakietów i obrazów  
 Kreatora tworzenia sekwencji zadań zestawu MDT tworzy pakietów i obrazów. Po utworzeniu te pakiety i obrazów, wybierz punkty dystrybucji, z których pakietów i obrazy będą kopiowane i dostępne dla komputerów docelowych.  

> [!NOTE]
>  W tym przykładzie istnieje tylko jeden punkt dystrybucji (WDG-MDT-01). Jednak większość sieci produkcyjnej ma wiele punktów dystrybucji. Podczas wykonywania tego kroku w środowisku produkcyjnym, wybierz odpowiednie punkty dystrybucji w sieci.  

 **Aby wybrać punkty dystrybucji dla pakietów dystrybucji oprogramowania**  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **Biblioteka oprogramowania**.  

3.  W obszarze roboczym Biblioteka oprogramowania przejdź do Przegląd/operacyjnego systemów lub zadanie sekwencji.  

4.  W okienku podglądu wybierz **Windows 8.1 odwołanie wdrożenia**.  

5.  Na wstążce na **Home** karcie **wdrożenia** kliknij przycisk **Dystrybuuj zawartość**.  

     Uruchamia Kreatora dystrybucji zawartości.  

6.  Ukończ Kreatora dystrybucji zawartości korzystając z informacji w 20. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    ### <a name="table-20-information-for-completing-the-distribute-content-wizard"></a>Tabela 20. Informacje o zakończeniu dystrybucji zawartości Kreatora  

    |**Na tej stronie kreatora** |**W tym** |  
    |-|-|  
    |**Ogólne** |Kliknij przycisk **Dalej**.|  
    |**Ogólne: Zawartość** |Kliknij przycisk **Dalej**.|  
    |**Ogólne: Miejsce docelowe zawartości** |1.  Kliknij przycisk **Dodaj**, a następnie kliknij przycisk **punktu dystrybucji**.<br />     **Punktów dystrybucji Dodaj** zostanie wyświetlone okno dialogowe.<br />2.  W **punktów dystrybucji Dodaj** okno dialogowe, wybierz opcję  **\\\WDGMDT01.mdt2013.corp.woodgrovebank.com**, a następnie kliknij przycisk **OK**.<br />     \\\WDGMDT01.mdt2013.corp.woodgrovebank.com pojawia się w **miejsce docelowe zawartości** listy.<br />3.  Kliknij przycisk **Dalej**.|  
    |**Podsumowanie** |Przejrzyj informacje w **szczegóły** czy podane podczas wykonywania poprzednich stron kreatora, a następnie kliknij przycisk **dalej**.|  
    |**Postęp** |Zostanie wyświetlony pasek postępu do dystrybucji oprogramowania.|  
    |**Zakończenie** |Kliknij przycisk **Zamknij**.|  

7.  Zamknij wszystkie otwarte okna i oknach dialogowych.  

###  <a name="AddtheNecessaryDeviceDrivers"></a>Krok 3-3. Dodaj sterowniki urządzeń wymagane  
 Po utworzeniu sekwencji zadań zestawu MDT, należy dodać sterowniki urządzeń wymagane dla komputera odniesienia (WDG-REF-01) do systemu Windows PE obrazu rozruchowego i obrazu Windows 8.1. Dodaj sterowniki urządzeń w węźle sterowniki w konsoli programu Configuration Manager. Utwórz pakiet zawierający sterowniki urządzeń i Wstaw sterowniki do niestandardowego obrazu środowiska Windows PE utworzony wcześniej w procesie.  

 Po utworzeniu pakietu, który zawiera sterowniki urządzeń, wybierz opcję dystrybucji punktu, do którego będzie można wdrożyć pakietu.  

 **Aby dodać sterowniki urządzeń wymagane**  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **Biblioteka oprogramowania**.  

3.  W obszarze roboczym Biblioteka oprogramowania go — omówienie/operacyjnego systemów/sterowniki.  

4.  Na wstążce na **Home** karcie **Utwórz** kliknij przycisk **Importuj sterownik**.  

     Uruchamia Kreatora importowania nowego sterownika.  

5.  Ukończ Kreatora importowania nowego sterownika korzystając z informacji w tabeli 21. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    ### <a name="table-21-information-for-completing-the-import-new-driver-wizard"></a>Tabela 21. Informacje dotyczące Kończenie pracy Kreatora importowania nowego sterownika  

    |**Na tej stronie kreatora** |**W tym** |  
    |-|-|  
    |**Zlokalizuj sterownik** |**W folderze źródłowym**, typ  **\\\WDG-MDT-01\Source$\Drivers**, a następnie kliknij przycisk **dalej**.|  
    |**Znajdź sterowników: Szczegóły sterownika** |Kliknij przycisk **Dalej**.|  
    |**Znajdź sterowników: Dodaj sterownik do pakietu** |<ol><li>Kliknij przycisk **nowy pakiet**.</li><li>Zakończenie **nowy pakiet sterowników** okno dialogowe, wykonując następujące czynności:<br /><br /> <ol><li>W **nazwa**, typ ***device_driver_name*** **pakietu** (gdzie *device_driver_name* jest nazwę opisową dla sterowników urządzeń).</li><li>W **komentarz**, typ **sterowniki urządzeń, które są niezbędne dla komputerów referencyjnych i docelowych**.</li></ol></li><li>W **źródła pakietu sterowników**, typ  **\\\WDG-MDT-01\Packages$\Drivers**, a następnie kliknij przycisk **OK**.</li><li>Kliknij przycisk **Dalej**.</li></ol>|  
    |**Znajdź sterowników: Dodaj sterownik do obrazów rozruchowych** |1.  Listy obrazów, wybierz **niestandardowych systemu Windows PE** pole wyboru.<br />2.  Wybierz **Aktualizuj punkty dystrybucji po zakończeniu** pole wyboru, a następnie kliknij przycisk **dalej**.|  
    |**Podsumowanie** |Przejrzyj informacje w **szczegóły** czy podane podczas wykonywania poprzednich stron kreatora, a następnie kliknij przycisk **dalej**.|  
    |**Postęp** |Zostanie wyświetlony pasek postępu do importowania sterowników urządzeń.|  
    |**Potwierdzenie** |Kliknij przycisk **Zamknij**.|  

 **Aby wybrać punkty dystrybucji dla pakietu sterowników**  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **Biblioteka oprogramowania**.  

3.  W obszarze roboczym Biblioteka oprogramowania przejdź do pakietów systemów/Driver Przegląd/operacyjnych.  

4.  W okienku podglądu kliknij ***device_driver_name*** **pakietu** (gdzie *device_driver_name* jest nazwę opisową dla sterowników urządzeń).  

5.  Na wstążce na **Home** karcie **wdrożenia** kliknij przycisk **Dystrybuuj zawartość**.  

     Uruchamia Kreatora dystrybucji zawartości.  

6.  Ukończ Kreatora dystrybucji zawartości korzystając z informacji w tabeli 22. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    ### <a name="table-22-information-for-completing-the-distribute-content-wizard"></a>Tabela 22. Informacje o zakończeniu dystrybucji zawartości Kreatora  

    |**Na tej stronie kreatora** |**W tym** |  
    |-|-|  
    |**Ogólne** |Kliknij przycisk **Dalej**.|  
    |**Ogólne: Zawartość** |Kliknij przycisk **Dalej**.|  
    |**Ogólne: Miejsce docelowe zawartości** |1.  Kliknij przycisk **Dodaj**, a następnie kliknij przycisk **punktu dystrybucji**.<br />     **Punktów dystrybucji Dodaj** zostanie wyświetlone okno dialogowe.<br />2.  W **punktów dystrybucji Dodaj** okno dialogowe, wybierz opcję  **\\\WDG-MDT-01.mdt2013.corp.woodgrovebank.com**, a następnie kliknij przycisk **OK**.<br />     \\\WDGMDT01.mdt2013.corp.woodgrovebank.com pojawia się w **miejsce docelowe zawartości** listy.<br />3.  Kliknij przycisk **Dalej**.|  
    |**Podsumowanie** |Przejrzyj informacje w **szczegóły** czy podane podczas wykonywania poprzednich stron kreatora, a następnie kliknij przycisk **dalej**.|  
    |**Postęp** |Zostanie wyświetlony pasek postępu do dystrybucji oprogramowania.|  
    |Zakończenie|Kliknij przycisk **Zamknij**.|  

7.  Zamknij wszystkie otwarte okna i oknach dialogowych.  

###  <a name="EnableMDTDeploymentProcessMonitoring"></a>Krok 3 — 4: Włącz wdrożenia zestawu MDT monitorowania procesu  
 Przed wdrożeniem na komputerze odniesienia (WDG-REF-01) z nośnika rozruchowego sekwencji zadań, aby włączyć monitorowanie MDT ZTI procesu wdrażania. Monitorowanie na **monitorowanie** kartę na udział wdrożenia **właściwości** okno dialogowe. W dalszej części procesu, można monitorować proces wdrożenia ZTI przy użyciu konsoli Deployment Workbench lub **Get-MDTMonitorData** polecenia cmdlet.  

 **Aby włączyć monitorowanie procesu wdrażania ZTI zestawu MDT**  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench przejdź do wdrożenia środowiska roboczego/wdrożenia udziałów.  

3.  W okienku Akcje **kliknij nowe udziały wdrożenia**.  

     Uruchamia Kreatora nowego udziału wdrożenia.  

4.  Ukończ Kreatora nowego udziału wdrożenia korzystając z informacji w tabeli 23.  

    ### <a name="table-23-information-for-completing-the-new-deployment-share-wizard"></a>Tabela 23. Informacje dotyczące Kończenie pracy Kreatora nowego udziału wdrażania  

    |**Na tej stronie kreatora** |**W tym** |  
    |-|-|  
    |**Ścieżka** |**W ścieżce udziału wdrożenia**, typ **C:\DeploymentShare$**, a następnie kliknij przycisk **dalej**.|  
    |**Udostępnij** |Kliknij przycisk **Dalej**.|  
    |**Opisowa nazwa** |Kliknij przycisk **Dalej**.|  
    |**Opcje** |Kliknij przycisk **Dalej**.|  
    |**Podsumowanie** |Kliknij przycisk **Dalej**.|  
    |**Postęp** |Zostanie wyświetlony pasek postępu tworzenia udziału wdrożenia.|  
    |**Potwierdzenie** |Kliknij przycisk Zakończ.|  

     Zakończenie Kreatora nowego udziału wdrożenia, a nowy udział wdrożenia — udział wdrożenia zestawu MDT (C:\DeploymentShare$)—appears w okienku szczegółów.  

5.  W okienku szczegółów kliknij **udział wdrożenia zestawu MDT (C:\DeploymentShare$)**.  

6.  W okienku Akcje kliknij polecenie Właściwości.  

     **Właściwości udziału wdrożenia zestawu MDT (C:\DeploymentShare$)** zostanie otwarte okno dialogowe.  

7.  W **właściwości udział wdrożenia zestawu MDT (C:\DeploymentShare$)** na okna dialogowego **monitorowanie** wybierz opcję **Włącz monitorowanie dla tego udziału wdrożenia** pole wyboru , a następnie kliknij przycisk **Zastosuj**.  

8.  W **właściwości udziału wdrożenia zestawu MDT (C:\DeploymentShare$)** na okna dialogowego **reguły** karcie, zwróć uwagę, że **EventService** właściwość została dodana do Plik CustomSettings.ini, a następnie kliknij przycisk **OK**.  

     **EventService** właściwości wygląda następująco:  

    ```  
    EventService=http://WDG-MDT-01:9800  
    ```  

9. Zamknij wszystkie otwarte okna i oknach dialogowych.  

###  <a name="CustomizeMDTConfigFilesforReferenceComputer"></a>Krok 3 – 5. Dostosowywanie pliki konfiguracyjne zestawu MDT dla komputera odniesienia  
 Po utworzeniu sekwencji zadań zestawu MDT, należy dostosować pliki konfiguracyjne zestawu MDT, które zapewniają ustawienia konfiguracji wdrażania Windows 8.1 z komputerem docelowym. W szczególności Dostosowywanie pliku CustomSettings.ini.  

 Po zakończeniu dostosowywania pliku CustomSettings.ini, Zapisz zaktualizowane pliki do folderu źródłowego pakietu ustawień niestandardowych komputera odniesienia MDT utworzony wcześniej w procesie (E:\Packages$\CustomSettings_Reference). Następnie należy dodać **DoCapture** i **EventService** właściwości i wartości odpowiadające CustomSettings.ini pliku tak, aby proces wdrożenia zestawu MDT przechwycenie (komputer odniesienia WDG-REF-01) po wdrożeniu Windows 8.1.  

 **Aby dostosować pliki konfiguracyjne zestawu MDT dla komputera odniesienia**  

1.  W Eksploratorze Windows przejdź do E:\Packages$\CustomSettings_Reference, a następnie kliknij dwukrotnie **CustomSettings.ini**.  

2.  Otwórz Microsoft Notepad, a następnie dodaj następujące wiersze na końcu pliku CustomSettings.ini, jak pokazano na wyświetlanie 1:  

    ```  
    DoCapture=YES  
    EventService=http://WDG-MDT-01:9800  
    ```  

    > [!NOTE]
    >  Upewnij się, usunięcie ustawienia dodatkowe inny niż pokazany na wyświetlanie 1.  

     **Wyświetlanie listy 1. Plik CustomSettings.ini po dodaniu właściwości DoCapture**  

    ```  
    [Settings]  
    Priority=Default  
    Properties=MyCustomProperty  

    [Default]  
    OSInstall=Y  
    SkipCapture=YES  
    SkipAdminPassword=NO  
    SkipProductKey=YES  
    DoCapture=YES  
    EventService=http://WDG-MDT-01:9800  
    ```  

3.  Zapisz plik, a następnie Zakończ działanie Notatnika.  

###  <a name="UpdateDistributionPointsforCustomSettings"></a>Krok 3 – 6. Aktualizuj punkty dystrybucji dla pakietu plików ustawień niestandardowych  
 Po zaktualizowaniu folderu źródłowego pakietu ustawień niestandardowych komputera odniesienia zestawu MDT w programie Configuration Manager zaktualizować punkty dystrybucji dla pakietu pliki ustawień niestandardowych komputera odniesienia zestawu MDT. Udziały wdrażania określony w pakiecie aktualizacji punktów dystrybucji kopiuje zaktualizowaną wersję pliku CustomSettings.ini.  

 **Aby zaktualizować dystrybucji punkty pakietu niestandardowych ustawień**  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **Biblioteka oprogramowania**.  

3.  W obszarze roboczym Biblioteka oprogramowania przejdź do aplikacji/Przegląd/pakiety zarządzania.  

4.  W okienku podglądu kliknij **ustawień niestandardowych komputera odniesienia MDT**.  

5.  Na wstążce na **Home** karcie **wdrożenia** kliknij przycisk **Aktualizuj punkty dystrybucji**.  

     **Programu Configuration Manager** zostanie otwarte okno dialogowe, informujący, że chcesz zaktualizować pakiet we wszystkich punktach dystrybucji.  

6.  W **programu Configuration Manager** okno dialogowe, kliknij przycisk **OK**.  

7.  Zamknij wszystkie otwarte okna i oknach dialogowych.  

 Menedżer konfiguracji uruchamia aktualizowania punktów dystrybucji z najnowszej wersji pliku CustomSettings.ini. Ten proces może potrwać kilka minut. Sprawdź stan pakietu do momentu **ostatniej aktualizacji** wartość Stan pakietu została zaktualizowana w celu ostatnie daty i godziny.  

###  <a name="CustomizeTaskSequenceforReferenceComputer"></a>Krok 3 do 7. Dostosowywanie sekwencji zadań dla komputera odniesienia  
 W przypadku większości wdrożeń **Windows 8.1 odwołanie wdrożenia** sekwencji zadań utworzonej wcześniej w procesie wykonuje wszystkie niezbędne kroki bez żadnych modyfikacji. W tym przykładzie zmodyfikowania sekwencji zadań, aby ustawić hasło dla konta administratora lokalnego do żadnej znanej wartości. Domyślnie sekwencja zadań ustawia hasło dla konta administratora lokalnego na losowych wartości. Dalsze dostosowanie sekwencji zadań mogą być wymagane w zależności od środowiska.  

 **Aby dostosować sekwencji zadań wdrażania odwołanie Windows 8.1**  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **Biblioteka oprogramowania**.  

3.  W obszarze roboczym Biblioteka oprogramowania przejdź do Przegląd/operacyjnego systemów lub zadanie sekwencji.  

4.  W okienku podglądu kliknij **Windows 8.1 odwołanie wdrożenia**.  

5.  Na wstążce na **Home** karcie **sekwencji zadań** kliknij przycisk **Edytuj**.  

     **Edytora sekwencji zadań wdrażania Windows 8.1 odwołanie** zostanie otwarte okno dialogowe.  

6.  W **edytora sekwencji zadań wdrażania Windows 8.1 odwołanie** okno dialogowe, przejdź do wykonywane/Zastosuj ustawienia systemu Windows.  

7.  Na **właściwości** , kliknij pozycję **Włącz konto i określ hasło administratora lokalnego**.  

8.  Na **właściwości** karcie **hasło** i **Potwierdź hasło**, typ  **P@ssw0rd** , a następnie kliknij przycisk **Zastosuj** .  

9. Wprowadź dodatkowe zmiany, aby sekwencja zadań, która wymaga środowiska, a następnie kliknij przycisk **OK**.  

10. Zamknij wszystkie otwarte okna i oknach dialogowych.  

## <a name="step-4-deploy-windows-81-and-capture-an-image-of-the-reference-computer"></a>Krok 4. Windows 8.1, wdrażania i przechwytywania obrazu komputera odniesienia  
 Po utworzeniu sekwencji zadań do wdrożenia Windows 8.1 na komputerze odniesienia i przechwycić obraz komputera odniesienia, należy uruchomić sekwencję zadań. Utwórz przechwytywania systemu operacyjnego przy użyciu Kreatora nośnika sekwencji zadań w konsoli programu Configuration Manager.  

 Windows 8.1, wdrażania i przechwytywania obrazu komputera odniesienia przy:  

-   Dodawanie do bazy danych lokacji programu Configuration Manager na komputerze odniesienia, zgodnie z opisem w [krok 4-1: Dodaj komputer odniesienia do bazy danych lokacji programu Configuration Manager](#AddReferenceComputertoConfigurationManagerSite)  

-   Tworzenie kolekcji, która zawiera komputer odniesienia dodaną zgodnie z opisem w [krok 4-2: Utwórz kolekcję, która zawiera komputer odniesienia](#CreateCollectionthatContainsReferenceComputer)  

-   Wdrożenie sekwencji zadań komputera odniesienia, zgodnie z opisem w [kroku nr 3, 4: Wdrożenie sekwencji zadań komputera odniesienia](#DeployReferenceComputerTaskSequence)  

-   Za pomocą Kreatora nośnika sekwencji zadań do utworzenia nośnika rozruchowego na dysku zgodnie z opisem w sekwencji zadań [krok 4-4: Tworzenie nośnika rozruchowego sekwencji zadań](#CreateTaskSequenceBootableMedia)  

-   Uruchamianie na komputerze odniesienia z nośnika rozruchowego na dysku zgodnie z opisem w sekwencji zadań [krok 4-5: Uruchom komputer odniesienia z nośnika rozruchowego sekwencji zadań](#StartReferenceComputerwithTaskSequenceBootableMedia)  

###  <a name="AddReferenceComputertoConfigurationManagerSite"></a>Krok 4-1. Dodaj komputer odniesienia do bazy danych lokacji programu Configuration Manager  
 Aby wdrożyć system operacyjny bez nośnika autonomicznego na nowy komputer, który nie zarządza aktualnie programu Configuration Manager, należy dodać nowy komputer do bazy danych lokacji programu Configuration Manager przed zainicjowaniem procesu wdrażania systemu operacyjnego. Configuration Manager może automatycznie odnajdować komputery w sieci, które mają zainstalowany; systemu operacyjnego Windows Jednak jeśli komputer bez zainstalowanego systemu operacyjnego, należy użyć Kreatora importowania informacji o komputerze do importowania informacji o nowym komputerze.  

 **Aby dodać komputer odniesienia do bazy danych lokacji programu Configuration Manager**  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **zasoby i zgodność**.  

3.  W zasoby i zgodność obszaru roboczego, przejdź do przegląd/urządzeń.  

4.  Na wstążce na **Home** karcie **Utwórz** kliknij przycisk **importu informacji o komputerze**.  

     Uruchamia Kreatora importowania informacji o komputerze.  

5.  Ukończ Kreatora importowania informacji o komputerze, korzystając z informacji w 24. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    ### <a name="table-24-information-for-completing-import-computer-information-wizard"></a>Tabela 24. Informacje dotyczące Kończenie pracy Kreatora importu informacji o komputerze  

    |**Na tej stronie kreatora** |**W tym** |  
    |-|-|  
    |**Wybierz źródło** |Kliknij przycisk **Importuj pojedynczy komputer**, a następnie kliknij przycisk **dalej**.|  
    |Wybierz źródło: Pojedynczego komputera|1.  W **nazwy komputera**, typ **WDG-REF-01**.<br />2.  W **adres MAC**, typ ***adres_MAC*** (gdzie *adres_MAC* jest adres media access control [MAC] sieci podstawowej karty sieciowej dla komputera odniesienia WDG-REF-01).<br />3.  Kliknij przycisk **Dalej**.|  
    |**Wybierz źródło: Podgląd danych** |Kliknij przycisk **Dalej**.|  
    |**Wybierz źródło: Wybierz kolekcję docelową** |Kliknij przycisk **Dalej**.|  
    |**Podsumowanie** |Przejrzyj informacje w **szczegóły** czy podane podczas wykonywania poprzednich stron kreatora, a następnie kliknij przycisk **dalej**.|  
    |**Postęp** |Postęp importowania komputera jest wyświetlana.|  
    |**Potwierdzenie** |Kliknij przycisk **Zamknij**.|  

 Aby uzyskać więcej informacji na temat dodawania nowego komputera do bazy danych lokacji programu Configuration Manager zobacz sekcję "Aby zaimportować informacje dotyczące jednego komputera," w sekcji "Jak do wdrażania systemów operacyjnych w programie Configuration Manager" w konfiguracji Biblioteka dokumentacji Manager instalowanych z programem Configuration Manager.  

###  <a name="CreateCollectionthatContainsReferenceComputer"></a>Krok 4-2. Utwórz kolekcję, która zawiera komputer odniesienia  
 W konsoli programu Configuration Manager utwórz kolekcję, która zawiera komputer odniesienia (WDG-REF-01). Ta kolekcja komputera jest używany później podczas anonsowanie sekwencji zadań utworzony wcześniej w procesie.  

 **Aby utworzyć kolekcję, która zawiera komputer odniesienia**  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **zasoby i zgodność**.  

3.  W zasoby i zgodność obszaru roboczego, przejdź do kolekcji omówienie lub urządzeniu.  

4.  Na wstążce na **Home** karcie **Utwórz** kliknij przycisk **Utwórz**, a następnie kliknij przycisk **Utwórz kolekcję urządzeń**.  

     Uruchamia Kreatora tworzenia kolekcji urządzeń.  

5.  Ukończ korzystając z informacji w tabeli 25 Kreatora tworzenia kolekcji urządzeń. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    ### <a name="table-25-information-for-completing-the-create-device-collection-wizard"></a>Tabela 25. Informacje o zakończeniu Kreator tworzenia kolekcji urządzeń  

    |**Na tej stronie kreatora** |**W tym** |  
    |-|-|  
    |**Ogólne** |<ol><li>W **nazwa**, typ **Microsoft, Deployment — komputer odniesienia**.</li><li>W **komentarz**, typ **komputera, który ma być komputer odniesienia dla komputerów docelowych, które mają zostać wdrożone**.</li><li>W **ograniczone kolekcji**, kliknij przycisk **Przeglądaj**.<br /><br />     **Wybieranie kolekcji** zostanie wyświetlone okno dialogowe. Wypełnij okno dialogowe, wykonując następujące czynności:<br /><br /> <ol><li>W **nazwa**, kliknij przycisk **wszystkie systemy**.</li><li>Kliknij przycisk **OK**.</li></ol></li><li>Kliknij przycisk **Dalej**.</li></ol>|  
    |**Reguły członkostwa** |<ol><li>Kliknij przycisk **Dodaj regułę**, a następnie kliknij przycisk **reguły bezpośredniej**.<br /><br />     Uruchamia Kreatora tworzenia reguły członkostwa bezpośredniego.</li><li>Wykonaj Kreatora tworzenia reguły członkostwa bezpośredniego, wykonując następujące czynności:<br /><br /> <ol><li>Na stronie **Zapraszamy** kliknij przycisk **Dalej**.</li><li>Na **wyszukiwanie zasobów** strony w **klasy zasobów**, wybierz pozycję **zasób systemowy**; na liście **nazwa atrybutu**, wybierz pozycję  **Nazwa**; na liście **wartość**, typ **WDG-REF-01**; a następnie kliknij przycisk **dalej**.</li><li>Na **zasobów wybierz** wybierz **WDG-REF-01**, a następnie kliknij przycisk **dalej**.</li><li>Na **Podsumowanie** kliknij przycisk **dalej**.</li><li>Na **postępu** Wyświetl postęp do tworzenia nowej reguły członkostwa.</li><li>Na **zakończenia** kliknij przycisk **Zamknij**.</li></ol></li><li>Kliknij przycisk **Dalej**.</li></ol>|  
    |**Podsumowanie** |Przejrzyj informacje w **szczegóły** czy podane podczas wykonywania poprzednich stron kreatora, a następnie kliknij przycisk **dalej**.|  
    |**Postęp** |Zostanie wyświetlony pasek postępu tworzenia kolekcji urządzeń.|  
    |**Zakończenie** |Kliknij przycisk **Zamknij**.|  

 Aby uzyskać więcej informacji zobacz sekcję "Jak Aby utworzyć kolekcje w programie Configuration Manager" w bibliotece dokumentacji programu Configuration Manager, który jest instalowany z programem Configuration Manager.  

###  <a name="DeployReferenceComputerTaskSequence"></a>Krok 4: 3. Wdrożenie sekwencji zadań komputera odniesienia  
 W konsoli programu Configuration Manager należy wdrożyć sekwencję zadań, utworzony wcześniej w procesie do kolekcji urządzeń, która zawiera komputer odniesienia utworzony wcześniej w procesie.  

 **Aby wdrożyć sekwencję zadań**  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **Biblioteka oprogramowania**.  

3.  W obszarze roboczym Biblioteka oprogramowania przejdź do Przegląd/operacyjnego systemów lub zadanie sekwencji.  

4.  W okienku podglądu kliknij **Windows 8.1 odwołanie wdrożenia**.  

5.  Na wstążce na **Home** karcie **wdrożenia** kliknij przycisk **Wdróż**.  

     Uruchamia Kreatora wdrażania oprogramowania.  

6.  Ukończ korzystając z informacji w tabeli 26 Kreatora wdrażania oprogramowania. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    ### <a name="table-arabic-26-information-for-completing-the-deploy-software-wizard"></a>Tabela ARABIC 26. Informacje dotyczące Kończenie pracy Kreatora wdrażania oprogramowania  

    |**Na tej stronie kreatora** |**W tym** |  
    |-|-|  
    |**Ogólne** |1.  W **kolekcji**, kliknij przycisk **Przeglądaj**.<br />2.  W **Przeglądaj kolekcji** okno dialogowe, kliknij przycisk **Microsoft, Deployment — komputer odniesienia**, a następnie kliknij przycisk **OK**.<br />3.  W **komentarz**, typ **wdrażanie Windows 8.1 do komputera odniesienia, a następnie przechwytywania obrazu komputera odniesienia**.<br />4.  Kliknij przycisk **Dalej**.|  
    |**Ustawienia wdrożenia** |1.  W **celu**, wybierz pozycję **dostępne**.<br />2.  Wybierz **Udostępnij nośnikom rozruchowym i środowisku PXE** pole wyboru.<br />3.  Kliknij przycisk **Dalej**.|  
    |**Ustawienia wdrożenia: Harmonogram** |Kliknij przycisk **Dalej**.|  
    |**Ustawienia wdrożenia: Środowisko użytkownika** |Kliknij przycisk **Dalej**.|  
    |**Ustawienia wdrożenia: Alerty** |Kliknij przycisk **Dalej**.|  
    |**Ustawienia wdrożenia: Punkty dystrybucji** |Kliknij przycisk **Dalej**.|  
    |**Podsumowanie** |Przejrzyj informacje w **szczegóły** czy podane podczas wykonywania poprzednich stron kreatora, a następnie kliknij przycisk **dalej**.|  
    |**Postęp** |Zostanie wyświetlony pasek postępu wdrażania sekwencji zadań.|  
    |**Zakończenie** |Kliknij przycisk **Zamknij**.|  

 Aby uzyskać więcej informacji zobacz sekcję "Jak do wdrażania sekwencji zadań," w bibliotece dokumentacji programu Configuration Manager, który jest instalowany z programem Configuration Manager.  

###  <a name="CreateTaskSequenceBootableMedia"></a>Krok 4-4. Tworzenie nośnika rozruchowego sekwencji zadań  
 Aby zainicjować proces zestawu MDT, udostępnia metody uruchamiania komputera za pomocą środowiska Windows PE i niezbędne oprogramowania przez utworzenie dysku rozruchowego nośnika sekwencji zadań. Użyj Kreatora nośnika sekwencji zadań w konsoli programu Configuration Manager do tworzenia nośnika rozruchowego dla magazynu na dysku flash USB, dysk CD lub DVD.  

 **Aby utworzyć dysk nośnika rozruchowego sekwencji zadań**  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **Biblioteka oprogramowania**.  

3.  W obszarze roboczym Biblioteka oprogramowania przejdź do Przegląd/operacyjnego systemów lub zadanie sekwencji.  

4.  Na wstążce na **Home** karcie **Utwórz** kliknij przycisk **tworzenia nośnika sekwencji zadań**.  

     Uruchamia Kreatora tworzenia nośnika sekwencji zadań.  

5.  Wykonaj zadania Kreatora tworzenia nośnika sekwencji korzystając z informacji w tabeli 27. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    ### <a name="table-27-information-for-completing-the-create-task-sequence-media-wizard"></a>27 tabeli. Informacje dotyczące Kończenie pracy Kreatora nośnika sekwencji zadań tworzenia  

    |**Na tej stronie kreatora** |**W tym** |  
    |-|-|  
    |**Wybierz typ nośnika** |1.  Kliknij przycisk **nośnika rozruchowego**.<br />2.  Wyczyść **Zezwalaj na nienadzorowane wdrożenie systemu operacyjnego** pole wyboru.<br />3.  Kliknij przycisk **Dalej**.|  
    |**Wybierz typ nośnika: Zarządzanie nośnikiem** |Kliknij przycisk **nośnik oparty na lokacji**, a następnie kliknij przycisk **dalej**.|  
    |**Wybierz typ nośnika: Typ nośnika** |W **pliku multimedialnego**, typ  **\\\WDG-MDT-01\Capture$\CM2012_TS_Boot_Media.iso**, a następnie kliknij przycisk **dalej**.|  
    |**Wybierz typ nośnika: Zabezpieczeń** |W **hasło** i **Potwierdź hasło**, typ  **P@ssw0rd** , a następnie kliknij przycisk **dalej**.|  
    |**Wybierz typ nośnika: Obraz rozruchowy** |1.  W **obrazu rozruchowego**, kliknij przycisk **Przeglądaj**.<br />2.  W **wybierz obraz rozruchowy** okno dialogowe, kliknij przycisk **niestandardowych systemu Windows PE**, a następnie kliknij przycisk **OK**.<br />3.  W **punktu dystrybucji**, kliknij przycisk  **\\\WDG-MDT-01.mdt2013.corp.woodgrovebank.com**, a następnie kliknij przycisk **OK**.<br />4.  W **punkt zarządzania**, kliknij przycisk  **\\\WDG-MDT-01.mdt2013.corp.woodgrovebank.com**, a następnie kliknij przycisk **OK**.<br />5.  Kliknij przycisk **Dalej**.|  
    |**Wybierz typ nośnika: Dostosowywanie** |Kliknij przycisk **Dalej**.|  
    |**Podsumowanie** |Przejrzyj informacje w **szczegóły** czy podane podczas wykonywania poprzednich stron kreatora, a następnie kliknij przycisk **dalej**.|  
    |**Postęp** |Zostanie wyświetlony pasek postępu tworzenia nośnika sekwencji zadań.|  
    |**Zakończenie** |Kliknij przycisk **Zamknij**.|  

     Kreator tworzy plik CM2012_TS_Boot_Media.iso w folderze udostępnionym $ WDG — MDT-01Capture.  

6.  WDG-REF-01 w przypadku komputera fizycznego, Utwórz dysk CD lub DVD Międzynarodowej Organizacji Normalizacyjnej (ISO) pliku. WDG-REF-01 w przypadku maszyny Wirtualnej, należy uruchomić maszyny Wirtualnej bezpośrednio z pliku ISO.  

 Aby uzyskać więcej informacji na temat tworzenia dysku rozruchowego nośnika sekwencji zadań zobacz sekcję "Jak do tworzenia nośnika rozruchowego," w bibliotece dokumentacji programu Configuration Manager, który jest instalowany z programem Configuration Manager.  

###  <a name="StartReferenceComputerwithTaskSequenceBootableMedia"></a>Krok 4 – 5. Uruchom komputer odniesienia z nośnika rozruchowego sekwencji zadań  
 Uruchom komputer odniesienia (WDG-REF-01) przy użyciu utworzony wcześniej w procesie dysk nośnika rozruchowego sekwencji zadań. Ten nośnik uruchamia środowisko Windows PE na komputerze odniesienia i inicjuje proces zestawu MDT. Na końcu procesu zestawu MDT Windows 8.1 jest wdrażany na komputerze odniesienia i zapisaniu obrazu komputera odniesienia do \WDG-MDT-01\Capture$\WDG-REF-01.wim.  

> [!NOTE]
>  Można także zainicjować proces zestawu MDT, uruchamiając na komputerze docelowym za pomocą usług wdrażania systemu Windows.  

 **Aby uruchomić komputer odniesienia z nośnika rozruchowego sekwencji zadań**  

1.  Uruchom WDG-REF-01 z nośnika rozruchowego sekwencji zadań, utworzony wcześniej w procesie.  

     Uruchamia środowisko Windows PE, a następnie uruchamia Kreatora sekwencji zadań.  

2.  Ukończ pracę Kreatora sekwencji zadań, korzystając z informacji w tabeli 28. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    ### <a name="table-28-information-for-completing-the-task-sequence-wizard"></a>28 tabeli. Informacje dotyczące Kończenie pracy Kreatora sekwencji zadań  

    |**Na tej stronie kreatora** |**W tym** |  
    |-|-|  
    |**Witamy w Kreatorze sekwencji zadań** |W **hasło**, typ  **P@ssw0rd** , a następnie kliknij przycisk **dalej**.|  
    |**Wybierz sekwencję zadań** |W polu listy, wybierz **Windows 8.1 odwołanie wdrożenia**, a następnie kliknij przycisk **dalej**.|  

 **Aby monitorować proces wdrażania komputera odniesienia przy użyciu konsoli Deployment Workbench**  

1.  Na WDG-MDT-01, kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench przejdź do wdrożenia środowiska roboczego/wdrożenia udziałów/udział wdrożenia zestawu MDT (C:\DeploymentShare$)/Monitoring.  

3.  W okienku szczegółów wyświetlić procesu wdrażania WDG-REF-01.  

4.  W okienku Akcje kliknij okresowo **Odśwież**.  

     Stan procesu wdrażania jest aktualizowana w okienku szczegółów. Nadal monitorować proces wdrażania, aż do ukończenia procesu.  

5.  W okienku szczegółów kliknij **WDG-REF-01**.  

6.  W okienku Akcje kliknij polecenie **właściwości**.  

     **Właściwości WDG-REF-01** zostanie wyświetlone okno dialogowe.  

7.  W **właściwości WDG-REF-01** na okna dialogowego **tożsamości** pozycję Wyświetl monitorowania dostarczone informacje na temat procesu wdrażania zgodnie z opisem w tabeli 29.  

    ### <a name="table-29-monitoring-information-about-the-deployment-process"></a>29 tabeli. Monitorowanie informacji na temat procesu wdrażania  

    |**Informacje** |**Opis** |  
    |-|-|  
    |**IDENTYFIKATOR** |Unikatowy identyfikator dla komputera wdrażany.|  
    |**Nazwa komputera** |Nazwa komputera jest wdrożony.|  
    |Stan wdrożenia|Bieżący stan komputera wdrożony; Stan może być jedną z następujących czynności:<br /><br /> -   **Uruchomiona**. Sekwencja zadań jest dobra i uruchomiona.<br />-   **Nie powiodło się**. Sekwencja zadań nie powiodło się, a proces wdrażania nie powiodło się.<br />-   **Ukończono**. Sekwencja zadań została ukończona.<br />-   **Odpowiadać**. Sekwencja zadań jego stan nie został zaktualizowany w ciągu ostatnich czterech godzin i zostanie uznany za nieodpowiadający.|  
    |**Krok** |Bieżącego kroku sekwencji zadań uruchamiana.|  
    |**Postęp** |Ogólny postęp sekwencji zadań. Pasek postępu wskazuje, ile kroków sekwencji zadań zostały uruchomione poza całkowita liczba kroków sekwencji zadań.|  
    |**Początek** |Czas rozpoczęcia procesu wdrażania.|  
    |**Koniec** |Czas zakończenia procesu wdrażania.|  
    |**Który upłynął** |Czas procesu wdrażania była uruchomiona lub trwało do uruchomienia, jeśli zakończenie procesu wdrażania.|  
    |**Błędy** |Liczba błędów napotkanych podczas procesu wdrażania.|  
    |**Ostrzeżenia** |Liczba ostrzeżeń podczas procesu wdrażania.|  
    |**Pulpit zdalny** |Ten przycisk służy do ustanawiania połączenia pulpitu zdalnego z komputerem wdrażany przy użyciu funkcji pulpitu zdalnego systemu Windows. Ta metoda zakłada się, że:<br /><br /> -Docelowy system operacyjny jest uruchomiony i ma włączoną obsługę usług pulpitu zdalnego<br />-   **mstsc.exe** znajduje się w ścieżce **Uwaga:**  Ten przycisk jest zawsze widoczne, ale nie można ustanowić sesji usług pulpitu zdalnego Jeśli monitorowanym komputerze środowiska Preinstalacyjnego systemu Windows, instalacja docelowego systemu operacyjnego nie zostało zakończone lub nie ma włączenie tej funkcji pulpitu zdalnego.|  
    |**Połączenie maszyn wirtualnych** |Ten przycisk służy do ustanowienia połączenia pulpitu zdalnego z maszyną wirtualną w HyperV®. Ta metoda zakłada się, że:<br /><br /> -Wdrożenie jest wykonywane do maszyny Wirtualnej z systemem w funkcji Hyper-V<br />-   **vmconnect.exe** znajduje się w folderze %ProgramFiles%\Hyper-V **Uwaga:**  Ten przycisk jest wyświetlany, gdy ZTIGather.wsf wykryje, że składniki integracji funkcji Hyper-V są uruchomione na monitorowanym komputerze. W przeciwnym razie ten przycisk, nie będą widoczne.|  
    |**DaRT zdalnego sterowania** |Ten przycisk pozwala ustanowić sesję zdalnego sterowania należy użyć funkcji Podgląd zdalnego w Diagnostics and Recovery Toolkit (DaRT).<br /><br /> Ta metoda zakłada się, że:<br /><br /> -DaRT został wdrożony na komputerze docelowym i jest aktualnie uruchomiona<br />-   **DartRemoteViewer.exe** znajduje się w folderze %ProgramFiles%\Microsoft DaRT 7\v7 **Uwaga:**  Ten przycisk jest wyświetlany, gdy ZTIGather.wsf wykryje, że DaRT jest uruchomiony na monitorowanym komputerze. W przeciwnym razie ten przycisk, nie będą widoczne.|  
    |**Automatyczne odświeżanie te informacje co 10 sekund** |Pole wyboru, która kontroluje, czy informacje w oknie dialogowym są odświeżane automatycznie. Jeśli pole wyboru jest:<br /><br /> -Zaznaczone, dane są odświeżane co 10 sekund<br />-Wyczyszczone, nie jest automatycznie odświeżany informacje i musi być odświeżane ręcznie przy użyciu **Odśwież teraz** przycisku|  
    |**Odśwież teraz** |Ten przycisk natychmiast odświeża informacje wyświetlane w oknie dialogowym.|  

8.  W **właściwości WDG-REF-01** okno dialogowe, kliknij przycisk **OK**.  

9. Zamknięcie konsoli Deployment Workbench.  

 **Aby monitorować proces wdrażania komputera odniesienia przy użyciu polecenia cmdlet Get-MDTMonitorData**  

1.  Na WDG-MDT-01, kliknij przycisk **Start**, wskaż polecenie **narzędzia administracyjne**, a następnie kliknij przycisk **moduły programu Windows PowerShell**.  

     Zostanie otwarty wiersz polecenia moduły programu Windows PowerShell.  

2.  Utwórz dysk programu Windows PowerShell, który używa dostawcy programu PowerShell zestawu MDT, uruchamiając [elementu PSDrive nowy](http://technet.microsoft.com/library/hh849829.aspx) polecenia cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    New-PSDrive -Name DS001 -PSProvider mdtprovider -Root d:\DeploymentShare$  
    ```  

3.  Wyświetl zestaw MDT proces monitorowania, uruchamiając **Get-MDTMonitorData** polecenia cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    Get-MDTMonitorData -Path DS001:  
    ```  

     To polecenie zwraca dane monitorowania zbierane przez zestaw MDT monitorowania usługa jest uruchomiona na tym samym komputerze hostującym udziału wdrożenia, jak pokazano w poniższym przykładzie danych wyjściowych:  

    ```  
    Name               : WDG-REF-01  
    PercentComplete    : 96  
    Settings           :  
    Warnings           : 0  
    Errors             : 0  
    DeploymentStatus   : 1  
    StartTime          : 6/7/2012 6:45:39 PM  
    EndTime            :   
    ID                 : 1  
    UniqueID           : 94a0830e-f2bb-421c-b1e0-6f86f9eb9fa1  
    CurrentStep        : 130  
    TotalSteps         : 134  
    StepName           : Gather  
    LastTime           : 6/7/2012 8:46:32 PM  
    DartIP             :  
    DartPort           :  
    DartTicket         :  
    VMHost             : XYL-DC-02  
    VMName             : WDG-REF-01  
    ComputerIdentities : {}  
    ```  

4.  Zamknij konsolę programu Windows PowerShell.  

 Po wystąpieniu problemów podczas wdrażania, zapoznaj się z pomocą techniczną firmy dokumentu zestawu MDT *Rozwiązywanie problemów z odwołania*. Po zakończeniu przechwycony obraz komputera odniesienia powinien istnieć w \\\WDG-MDT-01\Capture$\WDG-REF-01.wim.  

## <a name="step-5-create-and-configure-a-task-sequence-to-deploy-the-target-computer"></a>Krok 5. Tworzenie i konfigurowanie sekwencji zadań w celu wdrażania na komputerze docelowym  
 Po zakończeniu sekwencji zadań do wdrożenia na komputerze odniesienia (WDG-REF-01) przechwycony obraz komputera odniesienia znajduje się w \\\WDG-MDT-01\Capture$\WDG-REF-01.wim. Teraz należy utworzyć sekwencję zadań, które nastąpi wdrożenie przechwycony obraz komputera odniesienia na komputerze docelowym (WDG-CLI-01). Po zakończeniu tego kroku można wdrożyć przechwycony obraz komputera odniesienia do komputera docelowego.  

 Utwórz i skonfiguruj sekwencję zadań do wdrożenia na komputerze docelowym przez:  

-   Importowanie pliku wim, przechwycone w poprzednim kroku do programu Configuration Manager za pomocą Kreatora dodawania obrazu systemu operacyjnego, zgodnie z opisem w [krok 5-1: Zaimportuj plik wim przechwyconych do programu Configuration Manager](#ImportCapturedwimFileintoCOnfigurationManager)  

-   Za pomocą Kreatora tworzenia sekwencji zadań zestawu MDT, aby utworzyć szablon sekwencji zadań zestawu MDT do wdrażania przechwyconego obrazu komputera odniesienia do komputera docelowego, zgodnie z opisem w [krok 5-2: Utwórz sekwencję zadań zestawu MDT do wdrażania przechwyconego obrazu](#CreateMDTTaskSequencetoDeployCapturedImage)  

-   Wybieranie punktów dystrybucji dla nowych pakietów i obrazów, które tworzy Kreatora tworzenia sekwencji zadań zestawu MDT, zgodnie z opisem w [krok 5-3: Wybierz punkty dystrybucji dla nowych pakietów i obrazów](#SelectDistributionPointsforNewPackagesandImages)  

-   Dostosowywanie pliki konfiguracyjne zestawu MDT dla komputera docelowego — w szczególności pliku CustomSettings.ini — zgodnie z opisem w [krok 5 — 4: Dostosowywanie pliki konfiguracyjne zestawu MDT](#CustomizeMDTConfigurationFiles)  

-   Aktualizowanie punkty dystrybucji programu Configuration Manager dla pakietu ustawienia niestandardowe, zgodnie z opisem w [krok 5-5: Aktualizuj punkty dystrybucji dla pakietu ustawienia niestandardowe](#UpdateDistributionPointsforCustomSettingsPackage)  

-   Dostosowywanie sekwencji zadań dla komputera docelowego, zgodnie z opisem w [krok 5 — 6: Dostosowywanie sekwencji zadań dla komputera docelowego](#CustomizeTaskSequenceforTargetComputer)  

-   Konfigurowanie instalacji nienadzorowanej programu Office Professional Plus 2010, zgodnie z opisem w [krok 5-7: Konfigurowanie instalacji nienadzorowanej pakietu Office Professional Plus 2010](#ConfigureUnattendedInstallationofOfficeProPlus)  

-   Tworzenie aplikacji programu Configuration Manager, aby wdrożyć pakiet Office Professional Plus 2010, zgodnie z opisem w [krok 5 – 8: Tworzenie pakietu Office Professional Plus 2010 aplikacji](#CreateOfficeProPlusApplication)  

-   Dystrybucja aplikacji Office Professional Plus 2010 do punktów dystrybucji, zgodnie z opisem w [krok 5 – 9: Dystrybuuj pakiet Office Professional Plus 2010 aplikacji](#DistributeOfficePeoPlusApplication)  

-   Udostępnianie aplikacji Office Professional Plus 2010 dla wszystkich użytkowników zgodnie z opisem w [krok 5 – 10: Być Office Professional Plus 2010 aplikacji dla wszystkich użytkowników](#MakeOfficeProPlusApplicationAvailable)  

-   Dostosowywanie pliku konfiguracji kreatora UDI zgodnie z opisem w [krok 5 — 11: Dostosowywanie pliku konfiguracji kreatora UDI dla komputera docelowego](#CustomizeUDIWizardConfigFile)  

-   Tworzenie nowej strony kreatora niestandardowego do zbierania informacji o dodatkowe wdrożenia, zgodnie z opisem w [krok 5 — 13: Utwórz nową stronę kreatora niestandardowego](#CreateNewCustomWizardPage)  

-   Dodawanie formantów do nowej strony kreatora niestandardowego zgodnie z opisem w [krok 5 — 14: Dodawanie formantów do nowej strony kreatora niestandardowego](#AddControlstoNewcustomWizardPage)  

-   Aktualizowanie zestaw MDT pliki pakietu zawierającego zaktualizowany plik konfiguracji kreatora UDI zgodnie z opisem w [krok 5 – 15: Aktualizuj punkty dystrybucji dla pakietu plików zestawu MDT](#UpdateDistributionPointsforMDTFilesPackage)  

###  <a name="ImportCapturedwimFileintoCOnfigurationManager"></a>Krok 5-1. Zaimportuj plik wim przechwyconych do programu Configuration Manager  
 Przechwycony obraz komputera odniesienia (WDG-REF-01) w pliku wim, należy zaimportować plik wim przechwyconych do programu Configuration Manager. Zaimportuj plik wim przechwyconych do węzła obrazy systemu operacyjnego przy użyciu Kreatora dodawania obrazu systemu operacyjnego.  

 Przechwycony plik WIM zawiera dwa obrazy, jeden dla każdej partycji na komputerze odniesienia. Zidentyfikuj obrazów mającego przechwycony system operacyjny Windows 8.1 za pomocą Windows 8.1 zawierający opis obrazu. Indeks obrazu można użyć podczas tworzenia sekwencji zadań do wdrażania przechwyconego obrazu na komputerze docelowym.  

 **Aby zaimportować plik wim przechwyconych do programu Configuration Manager**  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **Biblioteka oprogramowania**.  

3.  W obszarze roboczym Biblioteka oprogramowania przejdź do obrazów systemu operacyjnego/systemów Przegląd/operacyjnych.  

4.  Na Wstążce w **Utwórz** kliknij przycisk **Dodaj obraz systemu operacyjnego**.  

     Zostanie uruchomiony Kreator dodawania obrazu systemu operacyjnego.  

5.  Ukończ korzystając z informacji w tabeli 30 Kreatora dodawania obrazu systemu operacyjnego. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    ### <a name="table-30-information-for-completing-the-add-operating-system-image-wizard"></a>30 tabeli. Informacje o zakończeniu Kreator dodawania obrazu systemu operacyjnego  

    |**Na tej stronie kreatora** |**W tym** |  
    |-|-|  
    |**Źródło danych** |W polu Ścieżka wpisz  **\\\WDG-MDT-01\Capture$\WDG-REF-01.wim**, a następnie kliknij przycisk **dalej**.|  
    |**Ogólne** |1.  W **nazwa**, typ **obraz odniesienia Windows 8.1**.<br />2.  W **wersji**, typ **1,00**.<br />3.  W **komentarze**, typ **Windows 8.1 przechwycony obraz komputera odniesienia (WDG-REF-01) używane do wdrażania na komputerach docelowych**, a następnie kliknij przycisk **dalej**.|  
    |**Podsumowanie** |Przejrzyj informacje w **szczegóły** czy podane podczas wykonywania poprzednich stron kreatora, a następnie kliknij przycisk **dalej**.|  
    |**Postęp** |Zostanie wyświetlony pasek postępu do importowania obrazu systemu operacyjnego.|  
    |**Zakończenie** |Kliknij przycisk **Zamknij**.|  

6.  W okienku podglądu kliknij **obraz odniesienia Windows 8.1**.  

7.  W okienku podglądu kliknij **szczegóły** kartę.  

     Zostanie wyświetlona lista partycji systemu operacyjnego przechwytywane w pliku wim. Indeks obrazu, który zawiera Windows 8.1 jest indeks obrazu, który będzie określać później w kreatorze tworzenia sekwencji zadań zestawu MDT.  

8.  Zanotuj indeks obrazu, który zawiera Windows 8.1.  

    > [!TIP]
    >  Na potrzeby tego przykładu indeks obrazu 2 powinny mieć system operacyjny Windows 8.1.  

###  <a name="CreateMDTTaskSequencetoDeployCapturedImage"></a>Krok 5-2. Utwórz sekwencję zadań zestawu MDT do wdrażania przechwyconego obrazu  
 Po przechwyceniu obrazu, należy utworzyć sekwencję zadań do wdrażania przechwyconego obrazu komputera odniesienia (WDG-REF-01) do komputera docelowego (WDG-CLI-01). Większość pakietów potrzebne do tej sekwencji zadań zostały utworzone wcześniej w procesie. Jednak należy utworzyć nowy pakiet zestawu MDT niestandardowych ustawień ma prawidłowe ustawienia konfiguracji dla komputera docelowego, który tworzy obraz systemu operacyjnego przechwycony obraz komputera odniesienia.  

 **Aby utworzyć szablon sekwencji zadań do wdrażania przechwyconego obrazu na komputerze docelowym**  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **Biblioteka oprogramowania**.  

3.  W obszarze roboczym Biblioteka oprogramowania przejdź do Przegląd/operacyjnego systemów lub zadanie sekwencji.  

4.  Na wstążce na **Home** karcie **sekwencje zadań** kliknij przycisk **Utwórz sekwencję zadań zestawu MDT**.  

     Uruchamia Kreatora tworzenia sekwencji zadań zestawu MDT.  

5.  Ukończ MDT Kreatora tworzenia sekwencji zadań przy użyciu informacji w tabeli 31. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    ### <a name="table-31-information-for-completing-the-create-mdt-task-sequence-wizard"></a>Tabela 31. Informacje o zakończeniu Kreator tworzenia sekwencji zadań zestawu MDT  

    |**Na tej stronie kreatora** |**W tym** |  
    |-|-|  
    |**Wybieranie szablonu** |Wybierz **sekwencję zadań klienta**, a następnie kliknij przycisk **dalej**.|  
    |**Wybierz szablon: Ogólne** |1.  W **nazwę sekwencji zadań**, typ **UDI — Windows 8.1 docelowe wdrożenie**.<br />2.  W **komentarze sekwencji zadań**, typ **sekwencję zadań pod kątem wdrażania przechwycony obraz komputera odniesienia na komputerze docelowym (WDG-CLI-01) przy użyciu UDI**, a następnie kliknij przycisk **dalej**.|  
    |Wybierz szablon: Szczegóły|1.  W **Użyj nazwy**, typ **pracownika banku Woodgrove**.<br />2.  W **nazwa organizacji**, typ **banku Woodgrove**.<br />3.  Kliknij przycisk **Dalej**.|  
    |**Wybierz szablon: Przechwyć ustawienia** |Kliknij przycisk **Dalej**.|  
    |**Obraz rozruchowy** |1.  W **Określ istniejący pakiet obrazów rozruchowych**, kliknij przycisk **Przeglądaj**.<br />2.  W **wybierz pakiet** okno dialogowe, kliknij przycisk **niestandardowych systemu Windows PE**, a następnie kliknij przycisk **OK**.<br />3.  Kliknij przycisk **Dalej**.|  
    |**Pakiet zestawu MDT** |1.  W **Określ istniejący pakiet plików zestawu narzędzi wdrażania Microsoft**, kliknij przycisk **Przeglądaj**.<br />2.  W **wybierz pakiet** okno dialogowe, kliknij przycisk **pliki zestawu MDT**, a następnie kliknij przycisk **OK**.<br />3.  Kliknij przycisk **Dalej**.|  
    |**Obraz systemu operacyjnego** |1.  Kliknij przycisk **Określ istniejącego systemu operacyjnego obrazu**.<br />2.  W **Określ istniejącego systemu operacyjnego obrazu**, kliknij przycisk **Przeglądaj**.<br />3.  W **wybierz pakiet** okno dialogowe, kliknij przycisk **obraz odniesienia Windows 8.1**, a następnie kliknij przycisk **OK**.<br />4.  Kliknij przycisk **Dalej**.|  
    |**Obraz systemu operacyjnego: Indeks obrazu systemu operacyjnego** |1.  W **pliku obrazu (WIM) wybranego systemu operacyjnego zawiera wiele obrazów. Określ obraz, który chcesz wdrożyć**, wybierz pozycję ***indeks obrazu*** (gdzie *indeks obrazu* jest indeks obrazu obrazu, który zawiera Windows 8.1, który został zidentyfikowany w [Krok 5-1: Importuj wim Captured pliku do programu Configuration Manager](#ImportCapturedwimFileintoCOnfigurationManager); na potrzeby tego przewodnika, wybierz opcję 2).<br />2.  Kliknij przycisk **Dalej**.|  
    |**Metody wdrażania** |Kliknij przycisk **instalacji "sterowanej"**, a następnie kliknij przycisk **dalej**.|  
    |**Pakiet klienta** |1.  W **Określ istniejący pakiet klienta programu ConfigMgr**, kliknij przycisk **Przeglądaj**.<br />2.  W **wybierz pakiet** okno dialogowe, kliknij przycisk **uaktualniania klienta programu Microsoft Configuration Manager**, a następnie kliknij przycisk **OK**.<br />3.  Kliknij przycisk **Dalej**.|  
    |**Pakiet USMT** |1.  W **Określ istniejący pakiet narzędzia USMT**, kliknij przycisk **Przeglądaj**.<br />2.  W **wybierz pakiet** okno dialogowe, kliknij przycisk **USMT**, a następnie kliknij przycisk **OK**.<br />3.  Kliknij przycisk **Dalej**.|  
    |Ustawienia pakietu|1.  Kliknij przycisk **utworzyć nowy pakiet ustawienia**.<br />2.  W **folderu źródłowego pakietu należy utworzyć**, typ  **\\\WDG-MDT-01\Packages$\UDICustomSettings_Target**, a następnie kliknij przycisk **dalej**.|  
    |**Pakiet ustawień: Szczegóły ustawień** |1.  W **nazwa**, typ **ustawienia niestandardowe komputera docelowego UDI**.<br />2.  W **wersji**, typ **1,00**.<br />3.  W **komentarze**, typ **ustawienia konfiguracji dla zestawu MDT procesu wdrażania przy użyciu UDI (na przykład CustomSettings.ini) dla komputera docelowego**, a następnie kliknij przycisk **dalej**.|  
    |**Pakiet programu Sysprep** |Kliknij przycisk **Dalej**.|  
    |**Podsumowanie** |Przejrzyj informacje w **szczegóły** czy podane podczas wykonywania poprzednich stron kreatora, a następnie kliknij przycisk **dalej**.|  
    |**Postęp** |Zostanie wyświetlony pasek postępu tworzenia sekwencji zadań.|  
    |**Potwierdzenie** |Kliknij przycisk **Zakończ**.|  

 Zostanie wyświetlona lista sekwencji zadań. Sekwencja zadań, który został właśnie utworzony (**UDI — Windows 8.1 docelowe wdrożenie**) znajduje się na liście sekwencji zadań.  

###  <a name="SelectDistributionPointsforNewPackagesandImages"></a>Krok 5-3. Wybierz punkty dystrybucji dla nowych pakietów i obrazów  
 Uruchamianie zestawu MDT Kreatora tworzenia sekwencji zadań tworzenia sekwencji zadań dla elementu docelowego generuje nowy pakiet dystrybucji oprogramowania i nowy obraz. Podczas tworzenia pakietu i obrazów, wybierz punkty dystrybucji, z których pakietu i obrazu będą kopiowane i dostępne dla komputerów docelowych.  

> [!NOTE]
>  W tym przykładzie istnieje tylko jeden punkt dystrybucji (WDG-MDT-01). Jednak większość sieciach produkcyjnych ma wiele punktów dystrybucji. Podczas wykonywania tego kroku w środowisku produkcyjnym, wybierz odpowiednie punkty dystrybucji w sieci.  

 Wybierz punkty dystrybucji dla pakietu dystrybucji oprogramowania (nowy pakiet niestandardowe ustawienia komputera docelowego o nazwie *zestawu MDT 2013 docelowym komputerze niestandardowych ustawień*) i pakiet obrazu systemu operacyjnego (dla nowego wywołuje plik wim przechwycony z komputera odniesienia *obraz odniesienia Windows 8.1*).  

 **Aby wybrać punkty dystrybucji dla pakietu dystrybucji oprogramowania**  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **Biblioteka oprogramowania**.  

3.  W obszarze roboczym Biblioteka oprogramowania przejdź do Przegląd/operacyjnego systemów lub zadanie sekwencji.  

4.  W okienku podglądu wybierz **UDI — Windows 8.1 docelowe wdrożenie**.  

     Na wstążce na **Home** karcie **wdrożenia** kliknij przycisk **Dystrybuuj zawartość**.  

     Uruchamia Kreatora dystrybucji zawartości.  

5.  Ukończ Kreatora dystrybucji zawartości korzystając z informacji w tabeli 32. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    ### <a name="table-32-information-for-completing-the-distribute-content-wizard"></a>Tabela 32. Informacje o zakończeniu dystrybucji zawartości Kreatora  

    |**Na tej stronie kreatora** |**W tym** |  
    |-|-|  
    |**Ogólne** |Kliknij przycisk **Dalej**.|  
    |**Zawartość** |Kliknij przycisk **Dalej**.|  
    |**Ogólne: Miejsce docelowe zawartości** |1.  Kliknij przycisk **Dodaj**, a następnie kliknij przycisk **punktu dystrybucji**.<br />     **Punktów dystrybucji Dodaj** zostanie wyświetlone okno dialogowe.<br />2.  W **punktów dystrybucji Dodaj** okno dialogowe, wybierz opcję  **\\\WDGMDT01.mdt2013.corp.woodgrovebank.com**, a następnie kliknij przycisk **OK**.<br />     \\\WDGMDT01.mdt2013.corp.woodgrovebank.com pojawia się w **miejsce docelowe zawartości** listy.<br />3.  Kliknij przycisk **Dalej**.|  
    |**Podsumowanie** |Przejrzyj informacje w **szczegóły** czy podane podczas wykonywania poprzednich stron kreatora, a następnie kliknij przycisk **dalej**.|  
    |**Postęp** |Zostanie wyświetlony pasek postępu do dystrybucji oprogramowania.|  
    |**Zakończenie** |Kliknij przycisk **Zamknij**.|  

###  <a name="CustomizeMDTConfigurationFiles"></a>Krok 5 — 4: Dostosowywanie pliki konfiguracyjne zestawu MDT  
 Jeśli sekwencja zadań został utworzony na komputerze docelowym, dostosować pliki konfiguracyjne zestawu MDT, które zapewniają ustawienia konfiguracji wdrażania Windows 8.1 z komputerem docelowym — w szczególności CustomSettings.ini.  

 Po dostosowaniu pliku CustomSettings.ini, Zapisz zaktualizowane pliki do folderu źródłowego pakietu MDT niestandardowych ustawień utworzonego wcześniej w procesie (E:\Packages$\CustomSettings_Target).  

 **Aby dostosować pliki konfiguracyjne zestawu MDT dla komputera docelowego**  

1.  W Eksploratorze Windows przejdź do folderu E:\Packages$\CustomSettings_Target, a następnie kliknij dwukrotnie **CustomSettings.ini**.  

2.  Otwórz Notatnik, a następnie dodaj następujący wiersz do pliku CustomSettings.ini, który wymaga środowiska, jak pokazano na wyświetlanie 2:  

     To ustawienie umożliwia skonfigurowanie monitorowania wdrożenia komputera docelowego.  

    > [!NOTE]
    >  Wprowadź wszelkie zmiany wymagane w danym środowisku.  

     **Wyświetlanie listy 2. Domyślny plik CustomSettings.ini**  

    ```  
    [Settings]  
    Priority=Default  
    Properties=MyCustomProperty  

    [Default]  
    OSInstall=Y  
    SkipCapture=YES  
    SkipAdminPassword=NO  
    SkipProductKey=YES  
    EventService=http://WDG-MDT-01:9800  
    ```  

3.  Zapisz plik, a następnie zamknij Notatnik.  

###  <a name="UpdateDistributionPointsforCustomSettingsPackage"></a>Krok 5-5. Aktualizuj punkty dystrybucji dla pakietu ustawienia niestandardowe  
 Po zaktualizowaniu folderu źródłowego pakietu ustawienia niestandardowe komputera docelowego zestawu MDT w programie Configuration Manager zaktualizować punkty dystrybucji dla pakietu ustawienia niestandardowe komputera docelowego zestawu MDT. Udziały wdrażania określony w pakiecie aktualizacji punktów dystrybucji kopiuje zaktualizowaną wersję pliku CustomSettings.ini.  

 **Aby zaktualizować dystrybucji punkty pakietu niestandardowych ustawień**  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **Biblioteka oprogramowania**.  

3.  W obszarze roboczym Biblioteka oprogramowania przejdź do aplikacji/Przegląd/pakiety zarządzania.  

4.  W okienku podglądu kliknij **ustawienia niestandardowe komputera docelowego zestawu MDT**.  

5.  Na wstążce na **Home** karcie **wdrożenia** kliknij przycisk **Aktualizuj punkty dystrybucji**.  

     **Programu Configuration Manager** zostanie otwarte okno dialogowe, informujący, że chcesz zaktualizować pakiet we wszystkich punktach dystrybucji.  

6.  W **programu Configuration Manager** okno dialogowe, kliknij przycisk **OK**.  

7.  Zamknij wszystkie otwarte okna i oknach dialogowych.  

###  <a name="CustomizeTaskSequenceforTargetComputer"></a>Krok 5 — 6: Dostosowywanie sekwencji zadań dla komputera docelowego  
 Dla większości wdrożeń sekwencji zadań wdrożenia docelowego Windows 8.1 utworzony wcześniej w procesie wykonuje wszystkie niezbędne kroki bez żadnych modyfikacji. W tym przykładzie zmodyfikuj szablon sekwencji zadań, aby wprowadzić hasło do konta administratora lokalnego do żadnej znanej wartości. (Domyślnie sekwencja zadań ustawia hasło dla konta administratora lokalnego do losowych wartości.) Sekwencja zadań może wymagać dalszej dostosowania, w zależności od środowiska.  

 **Aby dostosować sekwencja zadań wdrożenia docelowego Windows 8.1**  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **Biblioteka oprogramowania**.  

3.  W obszarze roboczym Biblioteka oprogramowania przejdź do Przegląd/operacyjnego systemów lub zadanie sekwencji.  

4.  W okienku podglądu kliknij **UDI — Windows 8.1 docelowe wdrożenie**.  

5.  Na wstążce na **Home** karcie **sekwencji zadań** kliknij przycisk **Edytuj**.  

     **Edytora sekwencji zadań wdrażania Windows 8.1 odwołanie** zostanie otwarte okno dialogowe.  

6.  W **edytora sekwencji zadań wdrażania Windows 8.1 odwołanie** okno dialogowe, przejdź do wykonywane/Zastosuj ustawienia systemu Windows.  

7.  Na **właściwości** , kliknij pozycję **Włącz konto i określ hasło administratora lokalnego**.  

8.  Na **właściwości** karcie **hasło** i **Potwierdź hasło**, typ  **P@ssw0rd** , a następnie kliknij przycisk **Zastosuj** .  

9. Wprowadź dodatkowe zmiany, aby sekwencja zadań, która wymaga środowiska, a następnie kliknij przycisk **OK**.  

10. Zamknij wszystkie otwarte okna i oknach dialogowych.  

###  <a name="ConfigureUnattendedInstallationofOfficeProPlus"></a>Krok 5-7: Konfigurowanie instalacji nienadzorowanej pakietu Office Professional Plus 2010  
 Configuration Manager dystrybuuje pliki i foldery służące do wdrażania pakietu Office Professional Plus 2010, ale nie zapewnia metody do wykonania instalacji nienadzorowanej po dystrybucji. Zamiast tego instalacji nienadzorowanej musi być skonfigurowany za pomocą metody dostarczone w pakiecie Office Professional Plus 2010. Instalacja nienadzorowana (dyskretna) pakietu Office Professional Plus 2010 można skonfigurować przy użyciu jednej z następujących metod:  

-   Utwórz plik dostosowania instalacji narzędzia dostosowywania pakietu Office (OCT) (plików .msp).  

-   Modyfikowanie pliku Config.xml.  

 Aby uzyskać więcej informacji na temat każdego z tych metod, zobacz [dostosować ustawienia przed zainstalowaniem pakietu Office 2010](http://technet.microsoft.com/library/cc179121.aspx).  

 Na potrzeby tego przewodnika instalacji nienadzorowanej programu Office Professional Plus 2010 zostanie to zrobione, tworząc plik dostosowania instalacji OCT (plików .msp). Instalator OCT powoduje zapisanie pliku dostosowania w folderze aktualizacji, który jest automatycznie skanowany za pomocą Kreatora instalacji pakietu Office Professional Plus 2010.  

 **Aby skonfigurować instalację nienadzorowaną Office Professional Plus 2010**  

1.  W wierszu polecenia wpisz następujące polecenie, a następnie naciśnij klawisz ENTER.  

    ```  
    e:  
    ```  

2.  W wierszu polecenia wpisz następujące polecenie, a następnie naciśnij klawisz ENTER.  

    ```  
    cd \Source$\OfficeProPlus2010\  
    ```  

3.  W wierszu polecenia wpisz następujące polecenie, a następnie naciśnij klawisz ENTER.  

    ```  
    setup /admin  
    ```  

     OCT zostanie uruchomiony oraz **produktu wybierz** zostanie otwarte okno dialogowe.  

4.  W OCT w **produktu wybierz** okno dialogowe, kliknij przycisk **OK**.  

     OCT ładuje odpowiednie informacje, a następnie wyświetla ustawienia, które można dostosować w pliku .msp.  

5.  W OCT, w okienku nawigacji przejdź do nazwy lokalizacji i organizacji instalacji/instalacji.  

6.  W okienku podglądu w **nazwa organizacji**, typ **banku Woodgrove**.  

7.  W OCT, w okienku nawigacji przejdź do instalacji/licencjonowania i interfejs użytkownika.  

8.  W okienku podglądu wybierz **akceptuję warunki umowy licencyjnej** pole wyboru.  

9. W okienku podglądu w **wyświetlić poziom**, wybierz pozycję **Brak**.  

10. Z **pliku** menu, kliknij przycisk **Zapisz jako**.  

     **Zapisz jako** zostanie otwarte okno dialogowe.  

11. W **Zapisz jako** okno dialogowe, typ **E:\Source$\OfficeProPlus2010\Updates\OPP2010_Unattend**, a następnie kliknij przycisk **zapisać**.  

     Plik OPP2010_Unattend.msp zostanie zapisany.  

12. Zamknij wszystkie otwarte okna i oknach dialogowych.  

###  <a name="CreateOfficeProPlusApplication"></a>Krok 5 – 8. Tworzenie pakietu Office Professional Plus 2010 aplikacji  
 Jedną z zalet do przeprowadzania wdrożenia zestawu MDT, za pomocą UDI jest możliwość przez użytkownika wybrać aplikacje do zainstalowania podczas wdrażania. Można dodać dowolną liczbę aplikacji programu Configuration Manager, a następnie wybierz aplikacje podczas uruchamiania kreatora UDI, zgodnie z opisem w [krok 6-4: Uruchom komputer docelowy z nośnika rozruchowego sekwencji zadań](#StartTargetComputerwithTaskSequenceBootableMedia).  

 Można skonfigurować aplikacje, które są wyświetlane w Kreatorze UDI za pomocą projektanta Kreatora instalacji UDI, zgodnie z opisem w [krok 5 — 11: Dostosowywanie pliku konfiguracji kreatora UDI dla komputera docelowego](#CustomizeUDIWizardConfigFile).  

 **Aby utworzyć aplikację Office Professional Plus 2010**  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **Biblioteka oprogramowania**.  

3.  W obszarze roboczym Biblioteka oprogramowania przejdź do aplikacji/Przegląd/aplikacje do zarządzania.  

4.  Na wstążce na **Home** karcie **Utwórz** kliknij przycisk **tworzenie aplikacji**.  

     Uruchamia Kreatora tworzenia aplikacji.  

5.  Ukończ korzystając z informacji w tabeli 33 Kreatora tworzenia aplikacji. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    ### <a name="table-3-information-for-completing-the-create-application-wizard"></a>Tabela 3. Informacje dotyczące Kończenie pracy Kreatora tworzenia aplikacji  

    |**Na tej stronie kreatora** |**W tym** |  
    |-|-|  
    |**Ogólne** |Kliknij przycisk **ręcznie określ informacje o aplikacji**, a następnie kliknij przycisk **dalej**.|  
    |**Ogólne: Ogólne** |1.  W **nazwa**, typ **pakietu Microsoft Office Professional Plus 2010 — x86**.<br />2.  W **komentarze administratora**, typ **32-bitowej wersji pakietu Microsoft Office Professional Plus 2010**.<br />3.  Wybierz **zezwolić tej aplikacji do zainstalowania z akcji sekwencji zadań zainstaluj aplikację zamiast wdrażania ręcznego** pole wyboru.<br />4.  Kliknij przycisk **Dalej**.|  
    |**Ogólne: Katalog aplikacji** |1.  W **zlokalizowany opis**, typ **32-bitowa wersja programu Microsoft Office Professional Plus 2010 do użytku przez pracowników banku Woodgrove**.<br />2.  W **słowa kluczowe**, **wpisz Office Professional Plus 2010**.<br />3.  Kliknij przycisk **Dalej**.|  
    |**Ogólne: Typ wdrożenia s** |<ol><li>Kliknij pozycję **Dodaj**.<br /><br />     Utwórz zostaje uruchomiony Kreator typu wdrożenia.</li><li>W **Kreatora tworzenia typu wdrożenia**na **ogólne** kliknij przycisk **ręcznie określ informacje o typie wdrożenia** , a następnie kliknij przycisk **dalej**.</li><li>Na **ogólne: Informacje ogólne** , wykonaj następujące czynności, a następnie kliknij przycisk **dalej**:<br /><br /> <ol><li>W **nazwa**, typ **pakietu Microsoft Office Professional Plus 2010 — x32 (Instalator Windows)**.</li><li>W **komentarze administratora**, typ **wdrażanie pakietu Microsoft Office Professional Plus 2010 za pomocą natywnego Instalatora Windows**.</li></ol></li><li>Na **ogólne: Zawartości** , wykonaj następujące czynności, a następnie kliknij przycisk **dalej**:<br /><br /> <ol><li>W **lokalizacja zawartości**, typ  **\\\WDGMDT01\Source$\OfficeProPlus2010**.</li><li>W **program instalacyjny**, typ **setup.exe**.</li><li>W **program dezinstalacyjny**, typ **setup.exe / uninstall PROPLUS**.</li></ol></li><li>Na **ogólne: Metoda wykrywania** , wykonaj następujące czynności, a następnie kliknij przycisk **dalej**:<br /><br /> <ol><li>Kliknij przycisk Dodaj **klauzuli**,<br /><br />         **Reguły wykrywania** zostanie wyświetlone okno dialogowe.</li><li>W **reguły wykrywania** okna dialogowego, **typu ustawienia**, wybierz pozycję **Instalatora Windows**.</li><li>W **kod produktu**, kliknij przycisk **Przeglądaj**<br /><br />         **Otwórz** zostanie wyświetlone okno dialogowe.</li><li>W **otwartych oknach** w polu **nazwę pliku**, typ  **\\\WDGMDT01\Source$\OfficeProPlus2010\ProPlus.WW\ProPlusWW.msi**, a następnie kliknij przycisk **Otwórz**.<br /><br />         Kod produktu pakietu Office Professional Plus 2010, zostanie wyświetlony w **kod produktu** pole.</li><li>W **reguły wykrywania** okno dialogowe, kliknij przycisk **OK**.</li></ol></li><li>Na **ogólne: Środowisko użytkownika** , wykonaj następujące czynności, a następnie kliknij przycisk **dalej**:<br /><br /> <ol><li>W **zachowanie podczas instalacji**, wybierz pozycję **zainstaluj dla systemu**.</li><li>W **wymagane zalogowanie**, wybierz pozycję **czy użytkownik jest zalogowany**.</li><li>W **widoczność programu instalacyjnego**, wybierz pozycję **normalny**.</li><li>W **szacowany czas instalacji**, typ **120**.</li></ol></li><li>Na **wymagania** kliknij przycisk **dalej**.</li><li>Na **zależności** kliknij przycisk **dalej**.</li><li>Na **Podsumowanie** kliknij przycisk **dalej**.</li><li>Na **zakończenia** kliknij przycisk **Zamknij**.<br /><br />     Uruchamia Kreatora tworzenia aplikacji.</li><li>Kliknij przycisk **Dalej**.</li></ol>|  
    |**Podsumowanie** |Przejrzyj informacje w **szczegóły** czy podane podczas wykonywania poprzednich stron kreatora, a następnie kliknij przycisk **dalej**.|  
    |**Postęp** |Zostanie wyświetlony pasek postępu tworzenia aplikacji.|  
    |**Zakończenie** |Kliknij przycisk **Zamknij**.|  

 Pakiet Office Professional Plus 2010 — x86 aplikacji zostanie wyświetlony w okienku podglądu.  

###  <a name="DistributeOfficePeoPlusApplication"></a>Krok 5 – 9. Dystrybuuj pakiet Office Professional Plus 2010 aplikacji  
 Po utworzeniu aplikacji Office Professional Plus 2010 należy dystrybucji aplikacji do punktów dystrybucji. Dzięki temu instalacja aplikacji z punktów dystrybucji. Na potrzeby tego przewodnika istnieje tylko jeden punkt dystrybucji (WDG-MDT-01). W typowych wdrożeniach programu Configuration Manager są zazwyczaj wiele punktów dystrybucji.  

 **Do dystrybucji aplikacji Office Professional Plus 2010**  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **Biblioteka oprogramowania**.  

3.  W obszarze roboczym Biblioteka oprogramowania przejdź do aplikacji/Przegląd/aplikacje do zarządzania.  

4.  W okienku podglądu kliknij **pakietu Microsoft Office Professional Plus 2012 — x86**.  

5.  Na wstążce na **Home** karcie **wdrożenia** kliknij przycisk **Dystrybuuj zawartość**.  

     Uruchamia Kreatora dystrybucji zawartości.  

6.  Ukończ Kreatora dystrybucji zawartości korzystając z informacji w tabeli 34. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    ### <a name="table-34-information-for-completing-the-distribute-content-wizard"></a>34 tabeli. Informacje o zakończeniu dystrybucji zawartości Kreatora  

    |**Na tej stronie kreatora** |**W tym** |  
    |-|-|  
    |**Ogólne** |Kliknij przycisk **Dalej**.|  
    |**Ogólne: Zawartość** |Kliknij przycisk **Dalej**.|  
    |**Ogólne: Miejsce docelowe zawartości** |1.  Kliknij przycisk **Dodaj**, a następnie kliknij przycisk **punktu dystrybucji**.<br />     **Dodać dystrybucji** zostanie wyświetlone okno dialogowe punktów.<br />2.  W **punktów dystrybucji Dodaj** okno dialogowe, wybierz opcję  **\\\WDGMDT01.mdt2013.corp.woodgrovebank.com**, a następnie kliknij przycisk **OK**.<br />     \\\WDGMDT01.mdt2013.corp.woodgrovebank.com pojawi się na liście miejsce docelowe zawartości.<br />3.  Kliknij przycisk **Dalej**.|  
    |Podsumowanie|Przejrzyj informacje w **szczegóły** czy podane podczas wykonywania poprzednich stron kreatora, a następnie kliknij przycisk **dalej**.|  
    |**Postęp** |Jest wyświetlany postęp dystrybucji aplikacji.|  
    |**Zakończenie** |Kliknij przycisk **Zamknij**.|  

7.  Zamknij wszystkie otwarte okna i oknach dialogowych.  

###  <a name="MakeOfficeProPlusApplicationAvailable"></a>Krok 5 – 10. Być Office Professional Plus 2010 aplikacji dla wszystkich użytkowników  
 Po utworzeniu aplikacji Office Professional Plus 2010 należy dystrybucji aplikacji do punktów dystrybucji. Dzięki temu instalacja aplikacji z punktów dystrybucji. Na potrzeby tego przewodnika istnieje tylko jeden punkt dystrybucji (WDG-MDT-01). W typowych wdrożeniach programu Configuration Manager są zazwyczaj wiele punktów dystrybucji.  

 **Aby udostępnić wszystkim użytkownikom aplikacji Office Professional Plus 2010**  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **Biblioteka oprogramowania**.  

3.  W obszarze roboczym Biblioteka oprogramowania przejdź do aplikacji/Przegląd/aplikacje do zarządzania.  

4.  W okienku podglądu kliknij **pakietu Microsoft Office Professional Plus 2010 — x86**.  

5.  Na wstążce na **Home** karcie **wdrożenia** kliknij przycisk **Wdróż**.  

     Uruchamia Kreatora wdrażania oprogramowania.  

6.  Ukończ korzystając z informacji w tabeli 35 Kreatora wdrażania oprogramowania. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    ### <a name="table-35-information-for-completing-the-deploy-software-wizard"></a>35 tabeli. Informacje dotyczące Kończenie pracy Kreatora wdrażania oprogramowania  

    |**Na tej stronie kreatora** |**W tym** |  
    |-|-|  
    |**Ogólne** |1.  W **kolekcji**, kliknij przycisk **Przeglądaj**.<br />     **Wybieranie kolekcji** zostanie wyświetlone okno dialogowe.<br />2.  W **Wybieranie kolekcji** okno dialogowe, kliknij przycisk **wszyscy użytkownicy**, a następnie kliknij przycisk **OK**.<br />3.  W **komentarze**, typ **upewnij Microsoft Office Professional Plus 2010 dostępny do wdrożenia dla wszystkich użytkowników**.<br />4.  Kliknij przycisk **Dalej**.|  
    |**Zawartość** |Kliknij przycisk **Dalej**.|  
    |**Ustawienia wdrożenia** |Kliknij przycisk **Dalej**.|  
    |**Planowanie** |Kliknij przycisk **Dalej**.|  
    |**Alerty** |Kliknij przycisk **Dalej**.|  
    |**Podsumowanie** |Przejrzyj informacje w **szczegóły** czy podane podczas wykonywania poprzednich stron kreatora, a następnie kliknij przycisk **dalej**.|  
    |**Postęp** |Zostanie wyświetlony pasek postępu wdrażania aplikacji.|  
    |**Zakończenie** |Kliknij przycisk **Zamknij**.|  

7.  Zamknij wszystkie otwarte okna i oknach dialogowych.  

###  <a name="CustomizeUDIWizardConfigFile"></a>Krok 5-11. Dostosowywanie pliku konfiguracji kreatora UDI dla komputera docelowego  
 Szablon instalacji sterowanej sekwencji zadań zawiera krok sekwencji zadań, który uruchamia Kreatora UDI. Po uruchomieniu kreatora UDI krok sekwencji zadań krok odwołujący się plik XML, który określa konfigurację kreatora UDI. Plik UDIWizard_Config.xml w folderze skryptów kontroluje sposób działania kreatora UDI. Dostosowywanie pliku UDIWizard_Config.xml za pomocą projektanta Kreatora instalacji UDI.  

 Projektanta Kreatora instalacji UDI obejmują grupy wstępnie zdefiniowanych etapu dla Kreatora UDI wymienionych w tabeli 36. Można dodawać i usuwać stronach kreatora, które są wyświetlane w Kreatorze UDI i sekwencja każdej stronie kreatora dla każdej grupy etapu.  

### <a name="table-36-predefined-stage-groups-for-each-supported-mdt-deployment-scenario"></a>36 tabeli. Etap wstępnie zdefiniowanych grup dla każdego scenariusza wdrażania obsługiwanych zestawu MDT  

|**Etap grupy** |**Opis** |  
|-|-|  
|**Nowy komputer** |Jako podstawę dla danego wdrożenia, jeśli nowa instalacja systemu operacyjnego Windows została wdrożona do nowego komputera i stanu użytkownika, nie są migrowane, użyj tej grupy etapu.|  
|**Odśwież** |Użyj jako podstawy tej grupy etapu dla danego wdrożenia odświeżeniu komputera, w tym komputerów, które muszą być ponownym utworzeniu obrazu normalizacji obrazu lub w celu rozwiązania problemu.|  
|**Zamień** |Użyj tej grupy etap jako podstawa dla danego wdrożenia po jednym komputerze zastępuje inny komputer. Istniejące dane migracji stanu użytkownika jest zapisany z oryginalnego komputera. Następnie w nowej instalacji systemu Windows jest wdrażana na nowym komputerze. Ponadto dane stanu użytkownika został przywrócony do nowego komputera.|  

 **Aby dostosować plik konfiguracji kreatora UDI dla komputera odniesienia**  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **projektanta Kreatora instalacji UDI**.  

     Uruchamia projektanta Kreatora instalacji UDI.  

2.  Na wstążce na **Home** karcie **Menu Plik** kliknij przycisk **Otwórz**.  

3.  W **Otwórz** okna dialogowego, **nazwę pliku**, typ  **\\\WDG-MDT-01\Packages$\MDT_Files\Scripts\UDIWizard_Config.xml**, a następnie kliknij przycisk **Otwórz**.  

    > [!NOTE]
    >  Spowoduje to otwarcie kopię pliku UDIWizard_Config.xml, który znajduje się w folderze pakietu zestawu MDT, utworzony wcześniej w procesie został uruchomiony program Microsoft Deployment Kreatora tworzenia sekwencji zadań.  

4.  W bibliotece strony kliknij **zainstalować programy**.  

5.  Na wstążce na **Home** karcie **edytowanie ustawień** kliknij przycisk **programu Configuration Manager**.  

     **Ustawienia lokacji** zostanie wyświetlone okno dialogowe.  

6.  W **okno dialogowe Ustawienia lokacji** , wykonaj następujące czynności, a następnie kliknij przycisk **OK**:  

    1.  W **nazwa serwera lokacji**, typ **WDG-MDT-01**.  

    2.  W **kod lokacji**, typ **NYC**.  

    3.  Kliknij przycisk **zweryfikować lokacji**.  

    4.  W **kolekcji aplikacji**, typ **wszyscy użytkownicy**.  

        > [!NOTE]
        >  Kolekcję programu Configuration Manager, w tym polu musi być zgodna kolekcję programu Configuration Manager, w której są wdrożone aplikacje. W tym przewodniku wybrania kolekcji wszystkich użytkowników w [krok 5 – 10: Być Office Professional Plus 2010 aplikacji dla wszystkich użytkowników](#MakeOfficeProPlusApplicationAvailable).  

7.  W okienku podglądu na **przepływ** karcie, rozwiń **StageGroup: Nowy komputer**.  

     Lista stron kreatora używanych w StageGroup: Nowy przepływ komputera jest wyświetlana.  

    > [!NOTE]
    >  Zwróć uwagę na sekwencji strony kreatora z StageGroup: Nowy przepływ komputera w projektanta Kreatora instalacji UDI. Zobaczysz takiej samej kolejności stron kreatora, po uruchomieniu kreatora UDI [krok 6-4: Uruchom komputer docelowy z nośnika rozruchowego sekwencji zadań](#StartTargetComputerwithTaskSequenceBootableMedia).  

8.  Skonfiguruj **StageGroup: Nowy komputer** przepływu, korzystając z informacji o każdej strony wymienione w tabeli 37. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    ### <a name="table-37-information-for-configuring-udi-wizard-designer-pages"></a>37 tabeli. Informacje o konfigurowaniu stron projektanta kreatora UDI  

    |**Strona kreatora** |**Kliknij kartę Konfiguracja i wykonaj następujące czynności** |  
    |-|-|  
    |**BitLocker** |<ol><li>W obszarze **tryb funkcji BitLocker**, rozwiń węzeł **tryb funkcji BitLocker**. W **wyboru funkcji BitLocker**, wyczyść **początkowo zaznacz to pole wyboru** pole wyboru.</li><li>W obszarze **tryb funkcji BitLocker**, kliknij przycisk **odblokowany** dla każdego z następujących opcji konfiguracji:<br /><br /> <ul><li>**Pole wyboru funkcji BitLocker**</li><li>**Przyciski radiowe tryb funkcji BitLocker**</li><li>**Pole tekstowe numeru PIN**</li></ul></li></ol><br /> Zmiany stanu dla każdej opcji konfiguracji na **zablokowany**, która uniemożliwia użytkownikom zmianę tych opcji w Kreatorze UDI.|  
    |**Wolumin** |<ol><li>W obszarze **pola kombi obrazu**, rozwiń węzeł **zachowanie kombi obraz**w obszarze **wartości pola kombi obrazu**, kliknij prawym przyciskiem myszy **Windows 8.1 (x 86) wersji RTM**, i następnie cliczk wybierz **obrazu systemu operacyjnego**.<br /><br />     **Wybierz obraz systemu operacyjnego** zostanie wyświetlone okno dialogowe.</li><li>Zakończenie **wybierz obraz systemu operacyjnego** okno dialogowe, wykonując następujące czynności, a następnie kliknij przycisk **OK**:<br /><br /> <ol><li>W **wybierz Instalatora systemu operacyjnego obrazu/dodać**, kliknij przycisk ***indeks obrazu*** (gdzie *indeks obrazu* jest indeks obrazu obrazu, który zawiera Windows 8.1, która była określone w [krok 5-1: Importuj wim Captured pliku do programu Configuration Manager](#ImportCapturedwimFileintoCOnfigurationManager); na potrzeby tego przewodnika, wybierz opcję **2**).</li><li>W **Nazwa wyświetlana**, typ **obraz odniesienia Windows 8.1 — x64**.</li></ol></li><li>W obszarze **pola kombi obrazu**, rozwiń węzeł **zachowanie kombi obraz**; w obszarze **wartości pola kombi obrazu**, kliknij prawym przyciskiem myszy **Windows 8.1 (x 86) wersji RTM**, i następnie kliknij przycisk **Usuń element**.<br /><br />     **Potwierdzenie usunięcia elementu** zostanie wyświetlone okno dialogowe.</li><li>W **potwierdzenie usunięcia elementu** okno dialogowe, kliknij przycisk **tak**.</li><li>W obszarze **danych i ustawień użytkownika**, rozwiń węzeł **zachowanie kombi danych użytkownika**, a następnie wybierz **Format: Czyszczenie wszystkich danych dla woluminu docelowego podczas instalacji** pole wyboru.</li><li>W obszarze **zachowanie kombi danych użytkownika**, kliknij przycisk **odblokowany** dla każdego z następujących opcji konfiguracji:<br /><br /> <ul><li>**Format dysku**</li><li>**Katalog systemu Windows**</li></ul></li></ol><br /> Zmiany stanu dla każdej opcji konfiguracji na **zablokowany**, która uniemożliwia użytkownikom zmianę tych opcji w Kreatorze UDI.|  
    |**Szczegóły nowego komputera** |1.  W obszarze **szczegóły sieci**, rozwiń węzeł **szczegóły sieci**; na liście **domeny lub grupy roboczej przycisków radiowych**, kliknij przycisk **domeny**.<br />2.  W obszarze **domeny lub grupy roboczej przycisków radiowych**, kliknij przycisk **odblokowany**.<br />     Stan zmieni się na **zablokowany**, która uniemożliwia użytkownikom zmianę tej opcji w Kreatorze UDI.<br />3.  W obszarze **szczegóły sieci**, rozwiń węzeł **domen i jednostek organizacyjnych**, a następnie kliknij przycisk **Dodawanie domeny**.<br />     **Utwórz lub Edytuj informacje o domenie** zostanie wyświetlone okno dialogowe.<br />4.  W **Utwórz lub Edytuj informacje o domenie** okna dialogowego, **nazwy domeny** typu **mdt2013.corp.woodgrovebank.com**.<br />5.  W **Utwórz lub Edytuj informacje o domenie** okna dialogowego, **przyjazną nazwę**, typ **Woodgrove Bank domeny usługi Active Directory**, a następnie kliknij przycisk **OK**.|  
    |**Zainstaluj programy** |<ol><li>W obszarze **oprogramowania i grup**, kliknij prawym przyciskiem myszy pusty obszar, a następnie kliknij przycisk **Dodaj grupę oprogramowania**.<br /><br />     **Dodawać i edytować grupę oprogramowania** zostanie wyświetlone okno dialogowe.</li><li>W **dodawać i edytować grupę oprogramowania** okna dialogowego, **nazwa**, typ **aplikacji banku Woodgrove**, a następnie kliknij przycisk **OK**.</li><li>W obszarze **oprogramowania i grup**, kliknij przycisk **aplikacji banku Woodgrove**.</li><li>Na wstążce na **Home** karcie **ogólne ustawienia elementu oprogramowania** kliknij przycisk **Dodaj**, a następnie kliknij przycisk **Dodaj oprogramowanie do grupy**.<br /><br />     Dodaj oprogramowanie do kreatora grupy zostanie uruchomiony.</li><li>Wykonaj Dodaj oprogramowanie do kreatora grupy, wykonując następujące czynności:<br /><br /> <ol><li>Na **jakiego typu element oprogramowania czy chcesz dodać** kliknij przycisk **I chcesz dodać aplikację**, a następnie kliknij przycisk **dalej**.</li><li>Na **wyszukiwania programu Configuration Manager dla elementu oprogramowania do dodania** strony w **Nazwa wyświetlana**, typ **pakietu Microsoft Office Professional Plus 2010 — x86**.</li><li>Na **wyszukiwania programu Configuration Manager dla elementu oprogramowania do dodania** kliknij przycisk **wybierz**.<br /><br />         **Aplikacji wyszukiwania** zostanie wyświetlone okno dialogowe.</li><li>W **aplikacji wyszukiwania** okno dialogowe, kliknij przycisk **wyszukiwania**, kliknij przycisk **pakietu Microsoft Office Professional Plus 2010 — X86**, a następnie kliknij przycisk **OK** .</li><li>Na **wyszukiwania programu Configuration Manager dla elementu oprogramowania do strony Dodaj**, kliknij przycisk **Zakończ**.</li></ol><br />     **Microsoft Office Professional Plus 2010 — x86** pojawia się poniżej **aplikacji banku Woodgrove** grupy oprogramowania.</li><li>W obszarze **oprogramowania i grup**, kliknij przycisk **oprogramowania ogólne**.</li><li>Na wstążce na **Home** karcie **ogólne ustawienia elementu oprogramowania** kliknij przycisk **Dodaj**, a następnie kliknij przycisk **Usuń element**.<br /><br />     **Usuń zaznaczony element** zostanie wyświetlone okno dialogowe.</li><li>W **Usuń zaznaczony element** okno dialogowe, kliknij przycisk **tak**.</li><li>W obszarze **oprogramowania i grup**, zaznacz pole wyboru dla **aplikacji banku Woodgrove**.<br /><br />     Grupy i Microsoft Office Professional Plus 2010 — x86 są wybrane.</li></ol>|  

9. Na wstążce na **Home** , kliknij pozycję **zapisać**.  

     **Zapisz plik** zostanie wyświetlone okno dialogowe.  

10. W **zapisywanie pliku** okno dialogowe, kliknij przycisk **OK**.  

11. Pozostaw projektanta Kreatora instalacji UDI otwarty do następnego kroku.  

###  <a name="CreateNewCustomWizardPage"></a>Krok 5-13. Utwórz nową stronę kreatora niestandardowego  
 Można utworzyć strony kreatora niestandardowych, które umożliwiają zbieranie informacji o wdrożeniu oprócz informacji zbieranych na innych stronach kreatora UDI. Tworzenie stron kreatora niestandardowego na podstawie **kompilacji swój własny strony** typ strony kreatora. Po utworzeniu strony kreatora niestandardowego można Dodaj formanty do niej i konfigurować zmienne sekwencji zadań Formanty ustawić.  

 Ten przewodnik banku Woodgrove chce Zezwalaj użytkownikom na wprowadzanie nazwy i dział one działać. Banku Woodgrove jest departmentalized według lokalizacji geograficznej. Tych informacji będzie służyć do konfigurowania nazwę zarejestrowanego użytkownika i organizacji w systemie Windows. W tym kroku należy dodać nową stronę kreatora niestandardowego do grupy etap nowy komputer.  

 **Aby utworzyć nową stronę kreatora niestandardowego**  

1.  Na wstążce na **Home** karcie **biblioteki strony** kliknij przycisk **Dodawanie strony**. **Dodaj nową stronę** zostanie wyświetlone okno dialogowe.  

2.  W **Dodaj nową stronę** okna dialogowego, **typ strony** kolumny, kliknij przycisk **kompilacji swój własny strony**.  

3.  W **Nazwa wyświetlana**, typ **informacje o użytkowniku**.  

4.  W **nazwy strony**, typ **UserInformationPage**, a następnie kliknij przycisk **OK**.  

     **Informacje o użytkowniku** w bibliotece strona zostanie wyświetlona strona.  

5.  W okienku szczegółów kliknij **przepływ** kartę.  

6.  Na **przepływ** karcie, rozwiń grupę etap nowego komputera.  

     Zostanie wyświetlona lista stron kreatora w grupie etap nowego komputera.  

7.  W bibliotece strony przeciągnij **informacje o użytkowniku** strony bezpośrednio przed punktem **funkcji BitLocker** strony w grupie etap nowego komputera na **przepływ** kartę.  

8.  Na wstążce na **Home** , kliknij pozycję **zapisać**.  

     **Zapisz plik** zostanie wyświetlone okno dialogowe.  

9. W **zapisywanie pliku** okno dialogowe, kliknij przycisk **OK**.  

10. Pozostaw projektanta Kreatora instalacji UDI otwarty do następnego kroku.  

###  <a name="AddControlstoNewcustomWizardPage"></a>Krok 5-14. Dodawanie formantów do nowej strony kreatora niestandardowego  
 Po dodaniu do nowego komputera z grupy etap stronie kreatora niestandardowego UDI kontrole musi zostać dodany do nowej strony kreatora niestandardowego. Formanty są dodawane do strony kreatora niestandardowego z przybornika kompilacji swój własny strony, która jest wyświetlana podczas przeglądania na stronie kreatora niestandardowego **Konfiguruj** karcie projektanta Kreatora instalacji UDI.  

 38 tabeli przedstawiono typy formantów do strony kreatora niestandardowego, w której przedstawiono na rysunku 1.  

### <a name="table-38-types-of-controls-in-the-udi-build-your-own-page-toolbox"></a>Tabela 38. Typy formantów w UDI kompilacji Przybornik strony  

|**Typ formantu** |**Opis** |  
|-|-|  
|**Pole wyboru** |Ten formant umożliwia zaznacz lub usuń zaznaczenie opcji konfiguracji i zachowuje się jak pole wyboru użytkownika tradycyjnego interfejsu użytkownika. Ten formant ma odpowiednie etykietę, którą można użyć do opisania celem pole wyboru. Stan tego formantu jest wartość PRAWDA, jeśli pole wyboru jest zaznaczone i wartość False, gdy pole wyboru jest wyczyszczone. Stan pola wyboru są przechowywane w zmiennej sekwencji zadań, które są skonfigurowane dla tego formantu. Aby uzyskać więcej informacji dotyczących tego formantu, zobacz "Formant wyboru" w dokumencie MDT *odwołanie do zestawu narzędzi*.|  
|**Pola kombi ComboBox** |Ten formant służy do wybierania elementu z listy elementów i zachowuje się jak tradycyjnych listy rozwijanej interfejsu użytkownika. Ten formant umożliwia dodawanie i usuwanie elementów z listy i podaj odpowiadającą mu wartość, która zostanie ustawiona w zmiennej sekwencji zadań, które są skonfigurowane dla tego formantu. Aby uzyskać więcej informacji dotyczących tego formantu, zobacz "Formantu Combobox" w dokumencie MDT *odwołanie do zestawu narzędzi*.|  
|**Wiersz** |Ten formant umożliwia dodawanie linii poziomej do dzielenia jedną część z innej strony kreatora niestandardowego. Ten formant nie zbiera żadnych wartości konfiguracji, ale raczej służy do wizualne rozbudowywanie interfejsu użytkownika. Aby uzyskać więcej informacji dotyczących tego formantu, zobacz "Wiersza" w dokumencie MDT *odwołanie do zestawu narzędzi*.|  
|**Label** |Ten formant umożliwia dodanie tekst opisowy, tylko do odczytu do strony kreatora. Ten formant nie zbiera żadnych wartości konfiguracji, ale raczej służy do wizualne rozbudowywanie interfejsu użytkownika. Aby uzyskać więcej informacji dotyczących tego formantu, zobacz "Formantu etykiety" w dokumencie MDT *odwołanie do zestawu narzędzi*.|  
|**Radio** |Tego formantu można wybrać jedną z opcji konfiguracji z grupy co najmniej dwie opcje. Podobnie jak w przypadku przycisków radiowych tradycyjne, co najmniej dwa z tych kontrolek można grupować, a następnie użytkownik może wybrać jedną z opcji w grupie przycisków radiowych. Unikatowa wartość jest przypisany do każdej opcji. Wartość przypisana do sterowania zaznaczoną opcję są zapisywane w zmiennej sekwencji zadań, które są skonfigurowane dla tego formantu. Aby uzyskać więcej informacji dotyczących tego formantu, zobacz "Radio Control" w dokumencie MDT *odwołanie do zestawu narzędzi*.|  
|**Bitmap** |Ten formant umożliwia dodanie grafiki mapa bitowa (BMP plik) do strony kreatora niestandardowego. Ten formant nie zbiera żadnych wartości konfiguracji, ale raczej służy do wizualne rozbudowywanie interfejsu użytkownika. Ścieżka do pliku .bmp jest względną wobec lokalizacji kreatora UDI (OSDSetupWizard.exe). Aby uzyskać więcej informacji dotyczących tego formantu, zobacz "Formant mapy bitowej" w dokumencie MDT *odwołanie do zestawu narzędzi*.|  
|**Textbox** |Ten formant pozwala na wprowadzenie tekstu na stronie kreatora niestandardowego. Tekstu w tym formancie są zapisywane w zmiennej sekwencji zadań, które są skonfigurowane dla tego formantu. Aby uzyskać więcej informacji dotyczących tego formantu, zobacz "W formancie Textbox" w dokumencie MDT *odwołanie do zestawu narzędzi*.|  

 Możesz dodać dowolną kombinację tych kontrolek do strony kreatora niestandardowego w oparciu o informacje, które mają być zbierane. Ponadto można użyć **Pokaż linie siatki** pole wyboru, aby pokazać lub ukryć linie siatki, który może służyć do celów wizualne projektowanie strony kreatora niestandardowego.  

 Na potrzeby tego przykładu spowoduje utworzenie niestandardowego kreatora, jak pokazano na rysunku 1.  

 ![QuickStartGuideforUDI](media/QuickStartGuideforUDI.jpg "QuickStartGuideforUDI")  
Rysunek 1. Strona kreatora niestandardowego do utworzenia  

 **Rysunek 1. Strona kreatora niestandardowego do utworzenia**  

 **Aby dodać kontrolki do nowej strony kreatora niestandardowego**  

1.  W bibliotece strony kliknij **informacje o użytkowniku** strony.  

2.  W okienku szczegółów kliknij **Konfiguruj** kartę.  

     Kompilacji swój własny strona przybornika i pusty kreatora są wyświetlane.  

3.  W przyborniku kompilacji swój własny strony przeciągnij **etykiety** kontrolki na stronie kreatora pusta w przybliżeniu następujące współrzędne:  

    -   *x* = 30  

    -   *y* = 5  

     Formantu etykiety jest umieszczany na stronie kreatora i nosi nazwę *label1*.  

4.  Na stronie kreatora niestandardowego kliknij **label1** (formantu etykiety dodanej w kroku 3).  

     Ten formant zachowuje się jak nagłówek strony kreatora niestandardowych i opisującą jego cel strony.  

5.  Konfigurowanie właściwości układu **label1** na **układu** karcie, korzystając z informacji w tabeli 39. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    ### <a name="table-39-label1-layout-properties"></a>39 tabeli. Właściwości układu label1  

    |**Właściwość** |**Wartość** |  
    |-|-|  
    |**Label** |Informacje o użytkowniku i organizacji|  
    |**X** |30|  
    |**Y** |5|  

6.  W przyborniku kompilacji swój własny strony przeciągnij **etykiety** kontrolki na stronie kreatora pusta w przybliżeniu następujące współrzędne:  

    -   *x* = 60  

    -   *y* = 60  

     Formantu etykiety jest umieszczany na stronie kreatora i nosi nazwę *label2*.  

7.  Na stronie kreatora niestandardowego kliknij **label2** (kontrola dodanym w poprzednim kroku).  

     Ten formant działa jako etykietę dla pola tekstowego służy do wprowadzania nazwy użytkownika.  

8.  Konfigurowanie właściwości układu **label2** na **układu** karcie, korzystając z informacji w tabeli 40. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    ### <a name="table-40-lable2-layout-properties"></a>Table 40. Właściwości układu lable2  

    |**Właściwość** |**Wartość** |  
    |-|-|  
    |**Label** |Nazwa użytkownika|  
    |**X** |60|  
    |**Y** |60|  

9. W przyborniku kompilacji swój własny strony kliknij i przeciągnij **pole tekstowe** kontrolki na stronie kreatora pusta w przybliżeniu następujące współrzędne:  

    -   *x* = 60  

    -   *y* = 80  

     **Pole tekstowe** formant jest umieszczany na stronie kreatora i nosi nazwę *Tekst1*.  

10. Na stronie kreatora niestandardowego kliknij **Tekst1** (kontrola dodanym w poprzednim kroku).  

     Ten formant jest pole tekstowe służące do wprowadzania nazwy użytkownika.  

11. Konfigurowanie właściwości układu **Tekst1** na **układu** karcie, korzystając z informacji w tabeli 41. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    ### <a name="table-41-text1-layout-properties"></a>41 tabeli. Właściwości układu Tekst1  

    |**Właściwość** |**Wartość** |  
    |-|-|  
    |**X** |60|  
    |**Y** |80|  
    |**Szerokość** |400|  

12. Skonfiguruj ustawienia właściwości **Tekst1** na **ustawienia** karcie, korzystając z informacji w tabeli 42. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    ### <a name="table-42-text1-settings-properties"></a>42 tabeli. Właściwości ustawień Tekst1  

    |**Właściwość** |**Wartość** |  
    |-|-|  
    |**Nazwa zmiennej sekwencji zadań** |**FullName** |  
    |**Przyjazną nazwę wyświetlaną widoczne na stronie podsumowania** |Nazwę zarejestrowanego użytkownika|  

13. W przyborniku kompilacji swój własny strony przeciągnij **etykiety** kontrolki na stronie kreatora pusta w przybliżeniu następujące współrzędne:  

    -   *x* = 60  

    -   *y* = 60  

     **Etykiety** formant jest umieszczany na stronie kreatora i nosi nazwę *label3*.  

14. Na stronie kreatora niestandardowego kliknij **label3** (kontrola dodanym w poprzednim kroku).  

     Ten formant działa jako etykieta pola kombi użyć, aby wybrać nazwę organizacji lub działu dla użytkownika.  

15. Konfigurowanie właściwości układu **lable3** na **układu** karcie, korzystając z informacji w tabeli 43. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    ### <a name="table-43-lable3-layout-properties"></a>43 tabeli. Właściwości układu lable3  

    |**Właściwość** |**Wartość** |  
    |-|-|  
    |**Label** |Nazwa organizacji lub działu|  
    |**X** |60|  
    |**Y** |121|  

16. W przyborniku kompilacji swój własny strony przeciągnij **Combobox** kontrolki na stronie kreatora pusta w przybliżeniu następujące współrzędne:  

    -   *x* = 60  

    -   *y* = 140  

     **Combobox** formant jest umieszczany na stronie kreatora i nosi nazwę *combo1*.  

17. Na stronie kreatora niestandardowego kliknij **combo1** (kontrola dodanym w poprzednim kroku).  

     Ten formant jest pola kombi, aby wybrać nazwę organizacji.  

18. Konfigurowanie właściwości układu **combo1** na **układu** karcie, korzystając z informacji w tabeli 44. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    ### <a name="table-44-combo1-layout-properties"></a>44 tabeli. Właściwości układu combo1  

    |**Właściwość** |**Wartość** |  
    |-|-|  
    |**X** |60|  
    |**Y** |80|  
    |**Szerokość** |400|  

19. Dodaj elementy danych do właściwości układu **combo1** na **układu** karcie, korzystając z informacji w tabeli 45. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    ### <a name="table-45-combo1-data-items"></a>45 tabeli. combo1 elementów danych  

    |**Wartość** |**Wartości wyświetlania** |  
    |-|-|  
    |**Banku Woodgrove Bank — nowego Jorku** |Banku Woodgrove Bank — nowego Jorku|  
    |**Banku Woodgrove Bank — Dallas** |Banku Woodgrove Bank — Dallas|  
    |**Woodgrove Bank – Chicago** |Woodgrove Bank – Chicago|  
    |**Banku Woodgrove Bank — Seattle** |Banku Woodgrove Bank — Seattle|  

20. Skonfiguruj ustawienia właściwości **combo1** na **ustawienia** karcie, korzystając z informacji w tabeli 46. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    ### <a name="table-46-combo1-settings-properties"></a>46 tabeli. Właściwości ustawień combo1  

    |**Właściwość** |**Wartość** |  
    |-|-|  
    |**Nazwa zmiennej sekwencji zadań** |**OrgName** |  
    |Przyjazną nazwę wyświetlaną widoczne na stronie podsumowania|Nazwę zarejestrowanej organizacji|  

21. Na wstążce na **Home** , kliknij pozycję **zapisać**.  

     **Zapisz plik** zostanie wyświetlone okno dialogowe.  

22. W **zapisywanie pliku** okno dialogowe, kliknij przycisk **OK**.  

23. Zamknij projektanta Kreatora instalacji UDI.  

###  <a name="UpdateDistributionPointsforMDTFilesPackage"></a>Krok 5 – 15. Aktualizuj punkty dystrybucji dla pakietu plików zestawu MDT  
 Po pliku konfiguracyjnego kreatora UDI UDIWizard_Config.xml, zostały zaktualizowane dla zestawu MDT plików pakietu w programie Configuration Manager, Aktualizuj punkty dystrybucji dla pakietu pliki zestawu MDT. Aktualizowanie punktów dystrybucji kopiuje zaktualizowaną wersję pliku UDIWizard_Config.xml udziałów wdrożenia określony w pakiecie.  

 **Aby zaktualizować punkty dystrybucji dla pakietu pliki zestawu MDT**  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **Biblioteka oprogramowania**.  

3.  W obszarze roboczym Biblioteka oprogramowania przejdź do aplikacji/Przegląd/pakiety zarządzania.  

4.  W okienku podglądu kliknij **pliki zestawu MDT**.  

5.  Na wstążce na **Home** karcie **wdrożenia** kliknij przycisk **Aktualizuj punkty dystrybucji**.  

     **Programu Configuration Manager** zostanie otwarte okno dialogowe, informujący, że chcesz zaktualizować pakiet we wszystkich punktach dystrybucji.  

6.  W **programu Configuration Manager** okno dialogowe, kliknij przycisk **OK**.  

7.  Zamknij wszystkie otwarte okna i oknach dialogowych.  

 Menedżer konfiguracji uruchamia aktualizowania punktów dystrybucji z najnowszej wersji pliku UDIWizard_Config.xml. Ten proces może potrwać kilka minut. Sprawdź stan pakietu do momentu **ostatniej aktualizacji** wartość Stan pakietu została zaktualizowana w celu ostatnie daty i godziny.  

## <a name="step-6-deploy-the-captured-image-of-the-reference-computer-to-the-target-computer"></a>Krok 6. Wdrażanie przechwycony obraz komputera odniesienia do komputera docelowego  
 Gdy przechwycony obraz komputera odniesienia i utworzyć i skonfigurować sekwencję zadań wdrażania przechwyconego obrazu. Skonfiguruj zestawu MDT, aby podać wszystkie ustawienia konfiguracji niezbędne do wdrożenia na komputerze docelowym. Po zainicjowaniu procesu wdrażania, obraz komputera odniesienia z systemem Windows 8.1 jest wdrażany na komputerze docelowym i automatycznie skonfigurowane ustawienia zdefiniowane.  

 Wdrażania przechwyconego obrazu przez:  

-   Dodawanie do bazy danych lokacji programu Configuration Manager na komputerze docelowym, zgodnie z opisem w [krok 6-1: Dodać komputer docelowy do bazy danych lokacji programu Configuration Manager](#AddTargetComputertoConfigureManagerSite)  

-   Tworzenie kolekcji komputerów, która zawiera komputer docelowy zgodnie z opisem w [krok 6-2: Tworzenie kolekcji komputerów, która zawiera komputer docelowy](#CreateComputerCollectionThatIncludesTargetComputer)  

-   Wdrażanie sekwencji zadań, utworzonej wcześniej w procesie, zgodnie z opisem w [kroku nr 3, 6: Wdrożenie sekwencji zadań komputera docelowego](#DeployTargetComputerTaskSequence)  

-   Uruchamianie komputera docelowego z nośnika rozruchowego sekwencji zadań, zgodnie z opisem w [krok 6-4: Uruchom komputer docelowy z nośnika rozruchowego sekwencji zadań](#StartTargetComputerwithTaskSequenceBootableMedia)  

###  <a name="AddTargetComputertoConfigureManagerSite"></a>Krok 6-1. Dodać komputer docelowy do bazy danych lokacji programu Configuration Manager  
 Aby wdrożyć system operacyjny bez nośnika autonomicznego na nowy komputer, który nie zarządza aktualnie programu Configuration Manager, należy dodać nowy komputer do bazy danych lokacji programu Configuration Manager przed zainicjowaniem procesu wdrażania systemu operacyjnego. Configuration Manager może automatycznie odnajdować komputery w sieci, które mają zainstalowany; systemu operacyjnego Windows Jednak jeśli komputer bez zainstalowanego systemu operacyjnego, należy użyć Kreatora importowania informacji o komputerze do importowania informacji o nowym komputerze.  

 **Aby dodać komputer docelowy do bazy danych lokacji programu Configuration Manager**  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **zasoby i zgodność**.  

3.  W zasoby i zgodność obszaru roboczego, przejdź do przegląd/urządzeń.  

4.  Na wstążce na **Home** karcie **Utwórz** kliknij przycisk **importu informacji o komputerze**.  

     Uruchamia Kreatora importowania informacji o komputerze.  

5.  Ukończ Kreatora importowania informacji o komputerze, korzystając z informacji w tabeli 47. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    ### <a name="table-47-information-for-completing-import-computer-information-wizard"></a>47 tabeli. Informacje dotyczące Kończenie pracy Kreatora importu informacji o komputerze  

    |Na tej stronie kreatora |Wykonaj te czynności |  
    |-|-|  
    |**Wybierz źródło** |Kliknij przycisk **Importuj pojedynczy komputer**, a następnie kliknij przycisk **dalej**.|  
    |**Wybierz źródło: Pojedynczego komputera** |1.  W **nazwy komputera**, typ **WDG-CLI-01**.<br />2.  W *adres MAC*, typ ***adres_MAC*** (gdzie *adres_MAC* adres MAC karty sieciowej głównej dla komputera docelowego, WDG-CLI-01).<br />3.  Kliknij przycisk **Dalej**.|  
    |**Wybierz źródło: Podgląd danych** |Kliknij przycisk **Dalej**.|  
    |**Wybierz źródło: Wybierz kolekcję docelową** |Kliknij przycisk **Dalej**.|  
    |**Podsumowanie** |Przejrzyj informacje w **szczegóły** czy podane podczas wykonywania poprzednich stron kreatora, a następnie kliknij przycisk **dalej**.|  
    |**Postęp** |Postęp importowania komputera jest wyświetlana.|  
    |**Potwierdzenie** |Kliknij przycisk **Zamknij**.|  

 Aby uzyskać więcej informacji na temat dodawania nowego komputera do bazy danych lokacji programu Configuration Manager zobacz sekcję "Aby zaimportować informacje dotyczące jednego komputera," w sekcji "Jak do wdrażania systemów operacyjnych w programie Configuration Manager" w konfiguracji Biblioteka dokumentacji Manager instalowanych z programem Configuration Manager.  

###  <a name="CreateComputerCollectionThatIncludesTargetComputer"></a>Krok 6-2. Tworzenie kolekcji komputerów, która zawiera komputer docelowy  
 W konsoli programu Configuration Manager utwórz kolekcję, która zawiera komputer docelowy (WDG-CLI-01). Można użyć tej kolekcji komputer później, podczas anonsowanie sekwencji zadań, utworzonej wcześniej w procesie.  

 **Aby utworzyć kolekcję komputerów, która zawiera komputer docelowy**  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **zasoby i zgodność**.  

3.  W zasoby i zgodność obszaru roboczego, przejdź do kolekcji omówienie lub urządzeniu.  

4.  Na wstążce na **Home** karcie **Utwórz** kliknij przycisk **Utwórz kolekcję urządzeń**.  

     Uruchamia Kreatora tworzenia kolekcji urządzeń.  

5.  Ukończ korzystając z informacji w tabeli 48 Kreatora tworzenia kolekcji urządzeń. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    ### <a name="table-48-information-for-completing-the-create-device-collection-wizard"></a>48 tabeli. Informacje o zakończeniu Kreator tworzenia kolekcji urządzeń  

    |**Na tej stronie kreatora** |**W tym** |  
    |-|-|  
    |**Ogólne** |<ol><li>W **nazwa**, typ **Microsoft, Deployment — 01 partii**.</li><li>W **komentarz**, typ **komputerów, które mają być uwzględniane w pierwszym partii komputerów wdrożone**.</li><li>W **ograniczone kolekcji**, kliknij przycisk **Przeglądaj**.<br /><br />     **Przeglądać kolekcje** zostanie wyświetlone okno dialogowe. Wypełnij okno dialogowe, wykonując następujące czynności:<br /><br /> <ol><li>W **Przeglądaj kolekcji** okna dialogowego, **nazwa**, kliknij przycisk **wszystkie systemy**.</li><li>Kliknij przycisk **OK**.</li></ol></li><li>Kliknij przycisk **Dalej**.</li></ol>|  
    |**Reguły członkostwa** |<ol><li>Kliknij przycisk **Dodaj regułę**, a następnie kliknij przycisk **reguły bezpośredniej**.<br /><br />     Uruchamia Kreatora tworzenia reguły członkostwa bezpośredniego.</li><li>Wykonaj Kreatora tworzenia reguły członkostwa bezpośredniego, wykonując następujące czynności:<br /><br /> <ol><li>Na stronie **Zapraszamy** kliknij przycisk **Dalej**.</li><li>Na **wyszukiwanie zasobów** strony w **klasy zasobów**, wybierz pozycję **zasób systemowy**; na liście **nazwa atrybutu**, wybierz pozycję  **Nazwa**; na liście **wartość**, typ **WDG-CLI-01**; a następnie kliknij przycisk **dalej**.</li><li>Na **zasobów wybierz** wybierz **WDG-CLI-01**, a następnie kliknij przycisk **dalej**. **Uwaga:**          Proces dodawania komputera docelowego (WDG-CLI-01) we wszystkich systemach może zająć kilka minut, aby zakończyć. Jeśli na liście nie ma WDG-CLI-01, powtórz kroki b i c, aż pojawi się WDGCLI01.</li><li>Na **Podsumowanie** kliknij przycisk **dalej**.</li><li>Na **zakończenia** kliknij przycisk **Zamknij**.</li></ol></li><li>Kliknij przycisk **Dalej**.</li></ol>|  
    |**Podsumowanie** |Przejrzyj informacje w **szczegóły** czy podane podczas wykonywania poprzednich stron kreatora, a następnie kliknij przycisk **dalej**.|  
    |**Postęp** |Zostanie wyświetlony pasek postępu tworzenia kolekcji urządzeń.|  
    |**Zakończenie** |Kliknij przycisk **Zamknij**.|  

 Aby uzyskać więcej informacji zobacz sekcję "Jak Aby utworzyć kolekcje w programie Configuration Manager" w bibliotece dokumentacji programu Configuration Manager, który jest instalowany z programem Configuration Manager.  

###  <a name="DeployTargetComputerTaskSequence"></a>Krok 6-3. Wdrożenie sekwencji zadań komputera docelowego  
 W konsoli programu Configuration Manager należy wdrożyć sekwencję zadań, utworzony wcześniej w procesie dla komputerów docelowych. Wdróż sekwencję zadań do kolekcji komputerów docelowych utworzony wcześniej w procesie.  

 **Aby wdrożyć sekwencję zadań**  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **Biblioteka oprogramowania**.  

3.  W obszarze roboczym Biblioteka oprogramowania przejdź do Przegląd/operacyjnego systemów lub zadanie sekwencji.  

4.  W okienku podglądu kliknij **UDI — Windows 8.1 docelowe wdrożenie**.  

5.  Na wstążce na **Home** karcie **wdrożenia** kliknij przycisk **Wdróż**.  

     Uruchamia Kreatora wdrażania oprogramowania.  

6.  Ukończ korzystając z informacji w tabeli 49 Kreatora wdrażania oprogramowania. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    ### <a name="table-49-information-for-completing-the-deploy-software-wizard"></a>49 tabeli. Informacje dotyczące Kończenie pracy Kreatora wdrażania oprogramowania  

    |**Na tej stronie kreatora** |**W tym** |  
    |-|-|  
    |**Ogólne** |1.  W **kolekcji**, kliknij przycisk **Przeglądaj**.<br />2.  W **Przeglądaj kolekcji** okno dialogowe, kliknij przycisk **Microsoft, Deployment — 01 partii**, a następnie kliknij przycisk **OK**.<br />3.  W **komentarz**, typ **wdrażanie Windows 8.1 do pierwszej partii komputerów docelowych przy użyciu UDI**.<br />4.  Kliknij przycisk **Dalej**.|  
    |**Ustawienia wdrożenia** |1.  W **celu**, wybierz pozycję **dostępne**.<br />2.  Wybierz **Udostępnij nośnikom rozruchowym i środowisku PXE** pole wyboru.<br />3.  Kliknij przycisk **Dalej**.|  
    |**Ustawienia wdrożenia: Schedule** |Kliknij przycisk **Dalej**.|  
    |**Ustawienia wdrożenia: Środowisko użytkownika** |Kliknij przycisk **Dalej**.|  
    |**Ustawienia wdrożenia: Alerty** |Kliknij przycisk **Dalej**.|  
    |**Ustawienia wdrożenia: Punkty dystrybucji** |Kliknij przycisk **Dalej**.|  
    |**Podsumowanie** |Przejrzyj informacje w **szczegóły** czy podane podczas wykonywania poprzednich stron kreatora, a następnie kliknij przycisk **dalej**.|  
    |**Postęp** |Zostanie wyświetlony pasek postępu tworzenia sekwencji zadań wdrażania.|  
    |**Zakończenie** |Kliknij przycisk **Zamknij**.|  

 Aby uzyskać więcej informacji zobacz sekcję "Jak do wdrażania sekwencji zadań," w bibliotece dokumentacji programu Configuration Manager, który jest instalowany z programem Configuration Manager.  

###  <a name="StartTargetComputerwithTaskSequenceBootableMedia"></a>Krok 6-4. Uruchom komputer docelowy z nośnika rozruchowego sekwencji zadań  
 Uruchom komputer docelowy (WDG-CLI-01) przy użyciu nośnika rozruchowego sekwencji zadań, utworzony wcześniej w procesie. Ten nośnik uruchamia środowisko Windows PE na komputerze odniesienia i inicjuje proces zestawu MDT. Po zakończeniu procesu zestawu MDT Windows 8.1 jest wdrażany na komputerze docelowym.  

> [!NOTE]
>  Można także zainicjować proces zestawu MDT, uruchamiając na komputerze docelowym za pomocą usług wdrażania systemu Windows.  

 **Do uruchomienia komputera docelowego z nośnika rozruchowego sekwencji zadań**  

1.  Uruchom WDG-CLI-01 z nośnika rozruchowego sekwencji zadań, utworzony wcześniej w procesie.  

     Uruchamia środowisko Windows PE, a następnie uruchamia Kreatora sekwencji zadań.  

2.  Ukończ pracę Kreatora sekwencji zadań, korzystając z informacji w tabeli 50. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    ### <a name="table-50-information-for-completing-the-task-sequence-wizard"></a>50 tabeli. Informacje dotyczące Kończenie pracy Kreatora sekwencji zadań  

    |**Na tej stronie kreatora** |**W tym** |  
    |-|-|  
    |**Witamy w Kreatorze sekwencji zadań** |W **hasło**, typ  **P@ssw0rd** , a następnie kliknij przycisk **dalej**.|  
    |**Wybierz sekwencję zadań** |W polu listy, wybierz **UDI — Windows 8.1 docelowe wdrożenie**, a następnie kliknij przycisk **dalej**.|  

     W kroku sekwencji zadań odpowiednie uruchomieniu Kreatora wdrażania UDI.  

3.  Ukończ pracę Kreatora wdrażania UDI, korzystając z informacji w tabeli 51. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    ### <a name="table-51-information-for-udi-deployment-wizard"></a>51 tabeli. Informacje dotyczące UDI Kreatora wdrażania  

    |**Na tej stronie kreatora** |**W tym** |  
    |-|-|  
    |**Welcome** |Kliknij przycisk **Dalej**.|  
    |**Informacje o użytkowniku** |1.  W **nazwę użytkownika,** typu **pracownika Chicago banku Woodgrove**.<br />2.  W **organizacji lub nazwa działu**, wybierz pozycję **banku Woodgrove Bank — Chicago**.<br />3.  Kliknij przycisk **Dalej**.|  
    |**BitLocker** |Kliknij przycisk **Dalej**.|  
    |**Wolumin** |Kliknij przycisk **Dalej**.|  
    |**Wybierz element docelowy** |Kliknij przycisk **Dalej**.|  
    |**Gotowość do wdrożenia** |1.  Przejrzyj kontrole konfiguracji i upewnij się, że ustawiono stan wszystkich kontroli **Powodzenie**.<br />2.  Kliknij przycisk *Next* (Dalej).|  
    |**Szczegóły nowego komputera** |1.  W **nazwy komputera**, typ **WDG-CLI-01**. **Uwaga:**      W scenariuszach nieznanych komputerów użytkownicy mogą zmieniać nazwę komputera na odpowiednią wartość.<br />2.  W **nazwy użytkownika**, typ **MDT2013\Administrator**.<br />3.  W **hasło** i **Potwierdź hasło**, typ  **P@ssw0rd** .<br />4.  Kliknij przycisk **Dalej**.|  
    |**Hasło administratora** |1.  W **hasło administratora** i **Potwierdź hasło**, typ  **P@ssw0rd** .<br />2.  Kliknij przycisk **Dalej**.|  
    |**Koligacja urządzenia użytkownika** |Wybierz **zestaw podstawowy użytkownik** pole wyboru, a następnie kliknij przycisk **dalej**.|  
    |**Język** |Kliknij przycisk **Dalej**.|  
    |**Zainstaluj programy** |Sprawdź, czy **pakietu Microsoft Office Professional Plus 2010 — x86** pole wyboru jest zaznaczone, a następnie kliknij przycisk **dalej**.|  
    |Podsumowanie|Przejrzyj informacje podanych podczas wykonanie poprzednich stron kreatora, a następnie kliknij przycisk **Zakończ**.|  

 **Aby monitorować proces wdrażania komputera odniesienia przy użyciu konsoli Deployment Workbench**  

1.  Na WDG-MDT-01, kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench przejdź do wdrożenia środowiska roboczego/wdrożenia udziałów/udział wdrożenia zestawu MDT (C:\DeploymentShare$)/Monitoring.  

3.  W okienku szczegółów wyświetlić procesu wdrażania WDG-REF-01.  

4.  W okienku Akcje kliknij okresowo **Odśwież**.  

     Stan procesu wdrażania jest aktualizowana w okienku szczegółów. Nadal monitorować proces wdrażania, aż do ukończenia procesu.  

5.  W okienku szczegółów kliknij **WDG-REF-01**.  

6.  W okienku Akcje kliknij polecenie **właściwości**.  

     **Właściwości WDG-REF-01** zostanie wyświetlone okno dialogowe.  

7.  W **właściwości WDG-REF-01** na okna dialogowego **tożsamości** pozycję Wyświetl monitorowania dostarczone informacje na temat procesu wdrażania zgodnie z opisem w tabeli 52.  

    ### <a name="table-52-monitoring-information-about-the-deployment-process"></a>Tabela 52. Monitorowanie informacji na temat procesu wdrażania  

    |**Informacje** |**Opis** |  
    |-|-|  
    |**ID** |Unikatowy identyfikator dla komputera wdrażany.|  
    |**Nazwa komputera** |Nazwa komputera jest wdrożony.|  
    |Stan wdrożenia|Bieżący stan komputera wdrożony; Stan może być jedną z następujących czynności:<br /><br /> -   **Uruchomiona**. Sekwencja zadań jest dobra i uruchomiona.<br />-   **Nie powiodło się**. Sekwencja zadań nie powiodło się, a proces wdrażania nie powiodło się.<br />-   **Ukończono**. Sekwencja zadań została ukończona.<br />-   **Odpowiadać**. Sekwencja zadań jego stan nie został zaktualizowany w ciągu ostatnich czterech godzin i zostanie uznany za nieodpowiadający.|  
    |**Krok** |Bieżącego kroku sekwencji zadań uruchamiana.|  
    |**Postęp** |Ogólny postęp sekwencji zadań. Pasek postępu wskazuje, ile kroków sekwencji zadań zostały uruchomione poza całkowita liczba kroków sekwencji zadań.|  
    |**Początek** |Czas rozpoczęcia procesu wdrażania.|  
    |**Koniec** |Czas zakończenia procesu wdrażania.|  
    |**Który upłynął** |Czas procesu wdrażania była uruchomiona lub trwało do uruchomienia, jeśli zakończenie procesu wdrażania.|  
    |**Błędy** |Liczba błędów napotkanych podczas procesu wdrażania.|  
    |**Ostrzeżenia** |Liczba ostrzeżeń podczas procesu wdrażania.|  
    |**Pulpit zdalny** |Ten przycisk służy do ustanawiania połączenia pulpitu zdalnego z komputerem wdrażany przy użyciu funkcji pulpitu zdalnego systemu Windows. Ta metoda zakłada się, że:<br /><br /> -Docelowy system operacyjny jest uruchomiony i ma włączoną obsługę usług pulpitu zdalnego<br />-   **mstsc.exe** znajduje się w ścieżce **Uwaga:**  Ten przycisk jest zawsze widoczne, ale nie można ustanowić sesji usług pulpitu zdalnego Jeśli monitorowanym komputerze środowiska Preinstalacyjnego systemu Windows, instalacja docelowego systemu operacyjnego nie zostało zakończone lub nie ma włączenie tej funkcji pulpitu zdalnego.|  
    |**Połączenie maszyn wirtualnych** |Ten przycisk służy do ustanowienia połączenia pulpitu zdalnego do maszyny Wirtualnej w funkcji Hyper-v. Ta metoda zakłada się, że:<br /><br /> -Wdrożenie jest wykonywane do maszyny Wirtualnej z systemem w funkcji Hyper-V<br />-   **vmconnect.ex**e znajduje się w folderze %ProgramFiles%\Hyper-V **Uwaga:**  Ten przycisk jest wyświetlany, gdy ZTIGather.wsf wykryje, że składniki integracji funkcji Hyper-V są uruchomione na monitorowanym komputerze. W przeciwnym razie ten przycisk, nie będą widoczne.|  
    |**DaRT zdalnego sterowania** |Ten przycisk pozwala ustanowić sesję zdalnego sterowania w DaRT przy użyciu funkcji podglądu zdalnego.<br /><br /> Ta metoda zakłada się, że:<br /><br /> -DaRT został wdrożony na komputerze docelowym i jest aktualnie uruchomiona<br />-   **DartRemoteViewer.exe** znajduje się w folderze %ProgramFiles%\Microsoft DaRT 7\v7 **Uwaga:**  Ten przycisk jest wyświetlany, gdy ZTIGather.wsf wykryje, że DaRT jest uruchomiony na monitorowanym komputerze. W przeciwnym razie ten przycisk, nie będą widoczne.|  
    |**Automatyczne odświeżanie te informacje co 10 sekund** |Pole wyboru, która kontroluje, czy informacje w oknie dialogowym są odświeżane automatycznie. Jeśli pole wyboru jest:<br /><br /> -Zaznaczone, dane są odświeżane co 10 sekund<br />-Wyczyszczone, nie jest automatycznie odświeżany informacje i musi być odświeżane ręcznie przy użyciu **Odśwież** teraz przycisku|  
    |**Odśwież teraz** |Ten przycisk natychmiast odświeża informacje wyświetlane w oknie dialogowym.|  

8.  W **właściwości WDG-REF-01** okno dialogowe, kliknij przycisk **OK**.  

9. Zamknięcie konsoli Deployment Workbench.  

 **Aby monitorować proces wdrażania komputera odniesienia przy użyciu polecenia cmdlet Get-MDTMonitorData**  

1.  Na WDG-MDT-01, kliknij przycisk **Start**, wskaż polecenie **narzędzia administracyjne**, a następnie kliknij przycisk **moduły programu Windows PowerShell**.  

     Zostanie otwarty wiersz polecenia moduły programu Windows PowerShell.  

2.  Utwórz dysk programu Windows PowerShell, który używa dostawcy programu PowerShell zestawu MDT, uruchamiając [elementu PSDrive nowy](http://technet.microsoft.com/library/hh849829.aspx) polecenia cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    New-PSDrive -Name DS001 -PSProvider mdtprovider -Root d:\DeploymentShare$  
    ```  

3.  Wyświetl zestaw MDT proces monitorowania, uruchamiając **Get-MDTMonitorData** polecenia cmdlet, jak pokazano w poniższym przykładzie:  

    ```  
    Get-MDTMonitorData -Path DS001:  
    ```  

     To polecenie zwraca dane monitorowania zbierane przez zestaw MDT monitorowania usługa jest uruchomiona na tym samym komputerze hostującym udziału wdrożenia jak pokazano w poniższym przykładzie danych wyjściowych:  

    ```  
    Name               : WDG-REF-01  
    PercentComplete    : 96  
    Settings           :  
    Warnings           : 0  
    Errors             : 0  
    DeploymentStatus   : 1  
    StartTime          : 6/7/2012 6:45:39 PM  
    EndTime            :   
    ID                 : 1  
    UniqueID           : 94a0830e-f2bb-421c-b1e0-6f86f9eb9fa1  
    CurrentStep        : 130  
    TotalSteps         : 134  
    StepName           : Gather  
    LastTime           : 6/7/2012 8:46:32 PM  
    DartIP             :  
    DartPort           :  
    DartTicket         :  
    VMHost             : XYL-DC-02  
    VMName             : WDG-REF-01  
    ComputerIdentities : {}  

    Name               : WDG-CLI-01  
    PercentComplete    : 26  
    Settings           :  
    Warnings           : 0  
    Errors             : 0  
    DeploymentStatus   : 1  
    StartTime          : 6/7/2012 3:07:13 AM  
    EndTime            :   
    ID                 : 2  
    UniqueID           : 94a0830e-f2bb-421c-b1e0-6f86f9eb9fa1  
    CurrentStep        : 49  
    TotalSteps         : 134  
    StepName           : Capture Network Settings using MDT  
    LastTime           : 6/7/2012 3:08:32 AM  
    DartIP             :  
    DartPort           :  
    DartTicket         :  
    VMHost             :   
    VMName             :   
    ComputerIdentities : {}  
    ```  

4.  Zamknij konsolę programu Windows PowerShell.  

 Po wystąpieniu problemów podczas wdrażania, zapoznaj się z pomocą techniczną firmy dokumentu zestawu MDT *Rozwiązywanie problemów z odwołania*. Po pomyślnym ukończeniu komputer docelowy jest uruchomiony system operacyjny Windows 8.1 skonfigurowane tak jak na komputerze odniesienia.  

 Po zakończeniu procesu wdrażania, Windows 8.1 rozpoczyna się po raz pierwszy i **powitalnej** karcie w **ukończenia wdrożenia** zostanie wyświetlone okno dialogowe. **Powitalnej** wyświetla przydatne informacje dotyczące wdrażania i udostępnia informacje kontaktowe, w przypadku, gdy występują problemy dotyczące wdrożenia.  

 Przejrzyj informacje na **Wdrożęnia** i **aplikacje zainstalowane** karty, aby sprawdzić, czy Windows 8.1 i pakiet Office Professional Plus 2010 zostały zainstalowane poprawnie. Po obejrzeniu te tabele, kliknij przycisk **Start systemu Windows** aby zalogować się do Windows 8.1 po raz pierwszy.  

> [!NOTE]
>  Aplikacji programu Configuration Manager nie są wyświetlane na **aplikacje zainstalowane** kartę. Zamiast tego są one wykrywane po zalogowaniu użytkownika na komputerze docelowym po raz pierwszy.
