---
title: Szybki Start - System Center 2012 R2 Configuration Manager
titleSuffix: Microsoft Deployment Toolkit
description: 'Przewodnik Szybki Start dla Microsoft Deployment Toolkit z System Center 2012 R2 Configuration Manager. '
ms.date: 09/09/2016
ms.prod: configuration-manager
ms.technology: configmgr-osd
ms.topic: article
ms.assetid: b12de852-a799-4c16-b51c-cc3abbd3ca3a
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 8f768ec6eef945163667b346118d2d65dcb2e3c6
ms.sourcegitcommit: 645cd5a324bdd299906efa27eaca5885eafc9e9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2018
---
# <a name="quick-start-guide-for-microsoft-system-center-2012-r2-configuration-manager"></a>Przewodnik Szybki Start dla programu Microsoft System Center 2012 R2 Configuration Manager  
 Microsoft Deployment Toolkit (MDT) 2013 udostępnia technologii wdrażania systemów operacyjnych Windows i program Microsoft Office. Ten przewodnik Szybki start pomaga szybko ocenić zestawu MDT 2013, dostarczając instrukcji skróconego, krok po kroku dotyczących korzystania z niego do zainstalowania systemu operacyjnego Windows 8.1 z programu Microsoft System Center 2012 R2 Configuration Manager. Ten przewodnik Szybki start pokazano, jak wykonać scenariusz wdrażania nowego komputera, który obejmuje wdrażania systemu Windows 8.1 do nowego komputera. W tym scenariuszu przyjęto założenie, że nie istnieje lub profilu, aby zachować dane użytkownika.  

> [!NOTE]     
>  W tym dokumencie *Windows* ma zastosowanie do systemów operacyjnych Windows 8.1, Windows 8, Windows 7, Windows Server® 2012 R2, Windows Server 2012 i Windows Server 2008 R2, chyba że określono inaczej. Zestaw MDT nie obsługuje wersji na podstawie procesora ARM systemu Windows. Podobnie *MDT* odwołuje się do zestawu MDT 2013, chyba że określono inaczej.  

 Po użyciu tego przewodnika, można obliczyć zestawu MDT, przejrzyj pozostałe wskazówki zestawu MDT, aby dowiedzieć się więcej o funkcjach zaawansowanych technologii.  

## <a name="prerequisites"></a>Wymagania wstępne  
 Instalacji zero Touch instalacji, przy użyciu programu Configuration Manager zostały spełnione następujące wymagania wstępne.  

### <a name="required-software"></a>Wymagane oprogramowanie  
 Aby ukończyć ten przewodnik, wymagane jest następujące oprogramowanie:  

-   Windows Server 2008 R2  

-   Microsoft SQL Server 2008 R2  

-   SQL Server 2008 R2 z dodatkiem Service Pack 1 (SP1)  

-   Aktualizacja zbiorcza programu SQL Server 2008 R2 z dodatkiem SP1 6 (CU6)  

-   Windows 8.1  

-   System Center 2012 R2 Configuration Manager  

-   Microsoft .NET Framework w wersji 3.5 z dodatkiem SP1  

-   Windows PowerShell w wersji 2.0  

-   Środowisko preinstalacji systemu Windows (Windows PE), który jest dostępny w programie Configuration Manager  

-   Usługi sieciowe, w tym systemu nazw domen (DNS, Domain Name System) i protokół dynamicznej konfiguracji hosta (DHCP)  

-   Usługi domenowe Active Directory (AD DS)  

 Zobacz [obsługiwane konfiguracje programu Configuration Manager](http://technet.microsoft.com/library/gg682077.aspx) dla kombinacji dodatkowego oprogramowania, które mogą służyć do instalowania programu Configuration Manager.  

> [!NOTE]   
>  Sekwencjonowania zadań używać we wdrożeniach MDT wymaga przypisania Tworzenie obiektu globalnego prawo do poświadczenia używane do uzyskania dostępu i uruchamiania konsoli Deployment Workbench i procesu wdrażania. To prawo jest dostępne dla kont z uprawnieniami administratora na poziomie (chyba że jawnie usunięte). Ponadto specjalizowany zabezpieczeń — profil zabezpieczeń ograniczoną funkcjonalność (SSLF) usuwa uprawnienie do tworzenia obiektów globalnych i nie powinny być stosowane do komputerów wdrażane za pomocą zestawu MDT.  

### <a name="computer-configuration"></a>Konfiguracja komputera  
 Aby ukończyć w tym przewodniku, należy skonfigurować komputery wymienione w poniższej tabeli. Te komputery mogą być komputerów fizycznych lub maszynach wirtualnych (VM) z wymienionych zasobów systemowych.  


|**Komputer**|**Opis i zasobów systemowych**|  
|-|-|  
|WDG-MDT-01|Ten komputer ma zestaw MDT infrastruktury i programu Configuration Manager. Na komputerze z systemem Windows Server 2008 R2 z następujących usług sieciowych zainstalowane:<br /><br /> -AD DS<br />— Serwer DNS<br />-Serwer DHCP<br />— Usługi wdrażania systemu Windows<br /><br /> Zasoby systemowe komputera są następujące:<br /><br /> — Procesor czterordzeniowe uruchomiony na procesor 2,66 gigaherca (GHz) lub szybszy<br />-4 gigabajty (GB) lub więcej pamięci fizycznej<br />-Partycji dysku, który ma co najmniej 40 GB dostępnego miejsca na dysku; stanie się partycji dysku c.<br />-CD-ROM lub DVD-ROM dysk, który zostanie przypisany literą dysku D<br />-Partycji dysku, który ma co najmniej 40 GB dostępnego miejsca na dysku; stanie się partycji E.|  
|WDG-REF-01|Jest to komputer odniesienia, w którym jest uruchomiona bez bieżącego systemu operacyjnego. Zasoby systemowe komputera są następujące:<br /><br /> — Procesor uruchomiona 1,4 GHz lub szybszy<br />— 1 GB lub więcej pamięci fizycznej<br />– 16 GB lub więcej dostępnego miejsca na dysku|  
|WDG-CLI-01|Jest to komputera docelowego, który jest uruchamiany bez bieżącego systemu operacyjnego. Zasoby systemowe komputera są następujące:<br /><br /> — Procesor uruchomiona 1,4 GHz lub szybszy<br />— 1 GB lub więcej pamięci fizycznej<br />– 16 GB lub więcej dostępnego miejsca na dysku|  

 Zasoby wymienione w powyższej tabeli odzwierciedlają zasobów systemowych zalecane do wykonania kroków tego podręcznika. Aby uzyskać informacje na minimalne wymagania systemowe programu zasobów:  

-   Windows Server 2008 R2, zobacz [Instalowanie systemu Windows Server 2008 R2](http://technet.microsoft.com/library/dd379511.aspx)  

-   SQL Server 2008 R2, zobacz [wymagania sprzętowe i programowe instalacji programu SQL Server 2008 R2](http://technet.microsoft.com/library/ms143506.aspx)  

> [!NOTE]   
>  W tym przewodniku założono, że zestaw MDT jest oceniana na komputerach fizycznych lub wirtualnych 64-bitowej (x 64). Jeśli ocena MDT na różnych platformach 32-bitowej (x 86), Pobierz i zainstaluj x86 wersji zestawu MDT i składników, które opisano w tym przewodniku.  

## <a name="step-1-prepare-the-prerequisite-infrastructure"></a>Krok 1. Przygotowanie wymagań wstępnych dotyczących infrastruktury  
 Do celów tego przewodnika, wszystkich wymagań wstępnych dotyczących infrastruktury usługi są uruchomione na komputerze o nazwie *WDG-MDT-01*. Zainstaluj wstępnie wymagane oprogramowanie, role serwera i usługi na tym komputerze, przed rozpoczęciem instalacji zestawu MDT.  

> [!NOTE]   
>  W tej sekcji założono, że w przypadku tworzenia nowej infrastruktury programu Configuration Manager zestawu MDT. Jeśli korzystasz z istniejącej infrastruktury programu Configuration Manager, przejrzyj kroki opisane w tej sekcji i Zastąp istniejące nazwy zasobów dla zasobów utworzone w tej sekcji (takie jak nazwa komputera i udostępnionych folderów sieciowych). Po zapoznaniu się w tej sekcji, przejdź do [krok 2: Przygotowanie środowiska MDT](#PrepareMDTEnvironment).  

 Przygotowanie infrastruktury wymagań wstępnych przed rozpoczęciem instalacji zestawu MDT przez:  

-   Instalowanie systemu Windows Server 2008 R2, zgodnie z opisem w [krok 1-1: Zainstaluj system Windows Server 2008 R2](#InstallWindowsServer)  

-   Tworzenie wymagane foldery i sieciowych udziałów zgodnie z opisem w [krok 1 i 2: Tworzenie wymagane folderów i udziałów sieciowych](#CreateRequiredFolders)  

-   Uzyskiwanie oprogramowania wymaganego do wykonania kroków tego podręcznika, zgodnie z opisem w [krok 1: 3: Uzyskanie wymaganego oprogramowania](#ObtainRequiredSoftware)  

-   Instalowanie roli serwera usług AD DS, zgodnie z opisem w [krok 1-4: Instalowanie roli serwera DS AD](#InstallADDSRole)  

-   Instalowanie roli serwera serwer DHCP, zgodnie z opisem w [krok 1-5: Instalowanie roli serwera serwer DHCP](#InstallDHCPServerRole)  

-   Instalowanie roli serwera usług sieci Web (IIS), zgodnie z opisem w [krok 1 — 6: Zainstaluj rolę serwera sieci Web Services (IIS)](#InstallIISRole)  

-   Dodanie wymaganych funkcji systemu Windows Server 2008 R2, zgodnie z opisem w [kroku 1-7: Dodać funkcje wymagane systemu Windows Server 2008 R2](#AddRequiredServerFeatures)  

-   Tworzenie kont użytkowników i usług wymaganych do wykonania kroków tego podręcznika, zgodnie z opisem w [krok 1 — 8: Utwórz wymagane użytkownika i kont usług](#CreateRequiredUserAccounts)  

-   Instalowanie programu SQL Server 2008 R2 dla programu Configuration Manager do używania zgodnie z opisem w [krok 1 — 9: Zainstaluj program SQL Server 2008 R2](#InstallSQLServer)  

-   Dodawanie serwera lokacji do grupy zabezpieczeń Administratorzy, zgodnie z opisem w [krok 1 – 10: Dodaj serwer lokacji do grupy zabezpieczeń Administratorzy](#AddSiteSecuritytoAdminGroup)  

-   Instalowanie programu Configuration Manager, zgodnie z opisem w [krok 1 — 11: Instalowanie programu Configuration Manager](#InstallConfigManager)  

-   Konfigurowanie konta dostępu do sieci, używanego przez klientów programu Configuration Manager można uzyskać dostępu do dystrybucji programu Configuration Manager punktów zgodnie z opisem w [krok 1-12: Konfigurowanie konta dostępu do sieci](#ConfigureNetworkAccessAccount)  

-   Konfigurowanie granic lokacji programu Configuration Manager i grup granic, zgodnie z opisem w [krok 1 — 13: Konfigurowanie granic lokacji programu Configuration Manager i grup granic](#ConfigurationManagerSiteBoundaries)  

-   Konfigurowanie publikowania informacji o lokacji w usługach AD DS i DNS, zgodnie z opisem w [krok 1 — 14: Skonfiguruj publikowanie informacji o lokacji w usługach AD DS i systemu DNS](#ConfigurePublishingSiteInfo)  

###  <a name="InstallWindowsServer"></a>Krok 1-1. Zainstaluj system Windows Server 2008 R2  
  Informacje dotyczące instalowania systemu Windows Server 2008 R2.  Zaakceptuj wartości domyślne, chyba że określono inaczej.  

|Po wyświetleniu monitu o| Podaj te wartości|   
|-|-|  
|**Gdzie chcesz zainstalować system Windows?**|**0 nieprzydzielonego miejsca na dysku**|  
|**Hasło**|Wszelkie silne hasło.|  
|**Nazwa komputera**|**WDG-MDT-01**|  
|**Formatowanie woluminów C i E**|**SYSTEMU PLIKÓW NTFS**|  
|**Konfiguracja protokołu TCP/IP**|Skonfiguruj z konfiguracją statycznego adresu IP, z innymi TCP/IP opcje konfiguracji na potrzeby środowiska|  

###  <a name="CreateRequiredFolders"></a>Krok 1 i 2. Tworzenie wymagane folderów i udziałów sieciowych  
 Proces wdrożenia zestawu MDT wymaga dodatkowych folderów, które są używane jako źródło dla plików lub do przechowywania plików utworzonych w procesie wdrożenia zestawu MDT. Niektóre z tych folderów muszą być udostępniane, dzięki czemu są one dostępne z innych komputerów.  

#### <a name="to-create-the-required-folders-and-share"></a>Aby utworzyć wymagane foldery i udostępniać  
1. Proces wdrożenia zestawu MDT wymaga kilku folderów. Utwórz następujące foldery i udziały z określonymi uprawnieniami dla każdego udziału.    

  |Utwórz folder  |Ta nazwa udziału  |Te uprawnienia udziału  |  
  |----|----|----|  
  |E:\Source$|Źródło$|**Administratorzy:** Współwłaściciel<br /><br /> **Wszyscy:** Odczyt|  
  |E:\Images$|Obrazy$|**Administratorzy:** Współwłaściciel<br /><br /> **Wszyscy:** Odczyt|  
  |E:\Capture$|Przechwyć$|**Administratorzy:** Współwłaściciel<br /><br /> **Wszyscy:** Odczyt|  
  |E:\Packages$|Pakiety$|**Administratorzy:** Współwłaściciel<br /><br /> **Wszyscy:** Odczyt|  

2. Utwórz następujące foldery:  

    -   E:\CMDownloads  

    -   E:\Source$\CustomSettings  

    -   E:\Source$\Drivers  

    -   E:\Source$\Windows_8-1  

    -   E:Source$ MDT_2013  

    -   E:Source$ SQL2008R2  

    -   E:Source$ SQL2008R2SP1  

    -   E:Source$ SQL2008R2CU6  

    -   E:Source$ ConfigMgr  

    -   Sterowniki $ E:Packages  

3. Skopiuj E:\Source$\Drivers sterowniki urządzenia komputera odniesienia (WDG-REF-01) i na komputerze docelowym (WDG-CLI-01).  

> [!NOTE]   
>  Procesy w tym przewodniku założono, że komputer odniesienia oraz komputer docelowy ma tych samych urządzeń i nie wymagają sterowników urządzeń.  

###  <a name="ObtainRequiredSoftware"></a>Krok 1-3. Uzyskanie wymaganego oprogramowania  
 Oprócz Windows Server 2008 R2, Windows 8.1 i programu Configuration Manager konkretnego oprogramowania jest wymagane do obliczenia MDT oparte na procesy w tym przewodniku.  W poniższej tabeli wymieniono oprogramowanie wymagane do przeprowadzenia wdrożenia przy użyciu zestawu MDT, gdzie można uzyskać oprogramowanie i gdzie należy umieścić oprogramowania na WDG-MDT-01.  

 |**Uzyskaj tego oprogramowania**|**Umieść w tym folderze**|  
 |-|-|  
 |ZESTAW MDT 2013|E:\Source$\MDT_2013|  
 |Windows 8.1, pliki dystrybucyjne z nośnika produktu|E:\Source$\Windows_8-1|  
 |Sterowniki urządzeń wymagane w komputerach referencyjnych i docelowych (WDG-REF-01 i WDG-CLI-01)|E:\Source$\Drivers|  
 |SQL Server 2008 R2 z nośnika produktu|E:\Source$\SQL2008R2|  
 |SQL Server 2008 R2 SP1, dostępne pod adresem [http://www.microsoft.com/download/details.aspx?id=26727](http://www.microsoft.com/download/details.aspx?id=26727)|E:\Source$\SQL2008R2SP1|  
 |SQL Server 2008 R2 z dodatkiem SP1 CU6, dostępne pod adresem [http://support.microsoft.com/kb/2679367](http://support.microsoft.com/kb/2679367)|E:\Source$\SQL2008R2SP1CU6|  
 |Menedżer konfiguracji z nośnika produktu|E:\Source$\ConfigMgr|  

###  <a name="InstallADDSRole"></a>Krok 1-4. Instalowanie roli serwera DS AD  
 Usługi AD DS jest wymagana do zapewnienia uwierzytelniania i działa jako repozytorium dla wartości konfiguracji dla produktów firmy Microsoft i technologie, które używa zestawu MDT, takich jak SQL Server 2008 R2 i Configuration Manager.  

 Do zainstalowania usług AD DS, uruchom Kreatora DCPROMO, aby skonfigurować komputer jako kontroler domeny. Instalacja usług AD DS za pomocą następujących informacji, akceptując wartości domyślne, chyba że określono inaczej.  

|**Po wyświetleniu monitu**|**W tym**|
|-|-|   
|Dla typu domeny|Utwórz nową domenę w nowym lesie.|  
|Aby uzyskać w pełni kwalifikowaną nazwę domeny|Typ **mdt2013.corp.woodgrovebank.com**.|  
|Aby uzyskać poziom funkcjonalności lasu|Wybierz **systemu Windows Server 2008 R2**.|  
|Aby zainstalować usługę serwera DNS w ramach procesu instalacji kontrolera domeny|Kliknij przycisk **Tak**.|  

###  <a name="InstallDHCPServerRole"></a>Krok 1-5. Instalowanie roli serwera serwer DHCP  
 Rola serwera serwer DHCP są wymagane do świadczenia automatycznej konfiguracji adresu IP dla komputerów docelowych. Zainstaluj serwer DHCP korzystając z poniższych informacji, akceptując wartości domyślne, chyba że określono inaczej.  

> [!NOTE]   
>  Jeśli używasz środowisku zwirtualizowanym, wyłącz całą konfigurację protokołu DHCP, która zapewnia oprogramowania wirtualizacji komputerów. Upewnij się, że usługa serwera DHCP, systemem WDG-MDT-01 jest to jedyny dostawca konfiguracji adresu IP za pomocą protokołu DHCP.  

|**Na tej stronie kreatora**|**W tym**|  
|-|-|  
|**Autoryzuj serwer DHCP w usłudze Active Directory**|Autoryzacja WDG-zestawu MDT-01, aby zapewnić konfiguracji adresu IP klienta.|  
|**Zakresy DHCP**|Utwórz odpowiedni zakres, który może służyć do automatycznego konfigurowania protokołu TCP/IP dla WDG-REF-01 i WDG-CLI-01.|  
|**Konfiguracji trybu bezstanowego protokołu DHCPv6**|Wyłącz tryb bezstanowego protokołu DHCPv6 dla tego serwera.|  

###  <a name="InstallIISRole"></a>Krok 1 — 6: Zainstaluj rolę serwera sieci Web Services (IIS)  
 Zainstaluj rolę serwera usług sieci Web (IIS) z usługami roli wymienione w poniższej tabeli.  Te usługi roli są wymagane dla programu SQL Server 2008 R2 i Configuration Manager. Jeżeli nie określono inaczej, należy użyć wartości domyślnych.  

|Usługi roli|Stan|  
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

###  <a name="AddRequiredServerFeatures"></a>Krok 1-7: Dodać funkcje wymagane systemu Windows Server 2008 R2  
 Oprócz instalowanie wymaganych ról serwera Windows Server 2008 R2, Dodaj następujące wymagane funkcje w Menedżerze serwera w **Podsumowanie funkcji** sekcji:  

-   Usługa inteligentnego transferu w tle  

-   Kompresja RDC  

###  <a name="CreateRequiredUserAccounts"></a>Krok 1 – 8. Utwórz wymagane użytkownika i kont usług  
 Program Configuration Manager i programu SQL Server 2008 R2 wymagają konta użytkowników podczas procesu instalacji.  Skorzystaj z poniższych informacji do tworzenia tych kont.  


|**To konto**|**Przy użyciu tych ustawień**|  
|-|-|  
|Konto usługi programu SQL Server Agent|1.  W **imię**, typ **SQL Agent**.<br />2.  W **nazwisko**, typ **konta usługi**.<br />3.  W **nazwa logowania użytkownika**, typ **SQLAgent**.<br />4.  W **hasło** i **Potwierdź hasło**, typ  **P@ssw0rd** .<br />5.  Wyczyść **użytkownik musi zmienić hasło przy następnym logowaniu** pole wyboru.<br />6.  Wybierz **hasło nigdy nie wygasa** pole wyboru.<br />7.  Należy to konto jest członkiem grupy zabezpieczeń Administratorzy domeny.<br />8.  W **opis**, typ **konto używane do uruchamiania usługi agenta programu SQL Server 2008 R2 usługi**.|  
|Konto usługi aparatu bazy danych programu SQL Server|1.  W **imię**, typ **aparat bazy danych SQL**.<br />2.  W **nazwisko**, typ **konta usługi**.<br />3.  W **nazwa logowania użytkownika**, typ **SQLDBEngine**.<br />4.  W **hasło** i **Potwierdź hasło**, typ  **P@ssw0rd** .<br />5.  Wyczyść **użytkownik musi zmienić hasło przy następnym logowaniu** pole wyboru.<br />6.  Wybierz **hasło nigdy nie wygasa** pole wyboru.<br />7.  Należy to konto jest członkiem grupy zabezpieczeń Administratorzy domeny.<br />8.  W **opis**, typ **konto używane do uruchamiania aparatu bazy danych programu SQL Server 2008 R2 usługi**.|  
|Konto usługi programu SQL Server Reporting Services|1.  W **imię**, typ **SQL Reporting**.<br />2.  W **nazwisko**, typ **konta usługi**.<br />3.  W **nazwa logowania użytkownika**, typ **SQLReport**.<br />4.  W **hasło** i **Potwierdź hasło**, typ  **P@ssw0rd** .<br />5.  Wyczyść **użytkownik musi zmienić hasło przy następnym logowaniu** pole wyboru.<br />6.  Wybierz **hasło nigdy nie wygasa** pole wyboru.<br />7.  Należy to konto jest członkiem grupy zabezpieczeń Administratorzy domeny.<br />8.  W **opis**, typ **konto używane do uruchamiania programu SQL Server 2008 R2 reporting services usługi**.|  
|Konta dostępu do sieci klienta Menedżera konfiguracji centrum systemowego|1.  W **imię**, typ **CM 2012**.<br />2.  W **nazwisko**, typ **dostępu do sieci klienta**.<br />3.  W **nazwa logowania użytkownika**, typ **CMNetAccess**.<br />4.  W **hasło** i **Potwierdź hasło**, typ  **P@ssw0rd** .<br />5.  Wyczyść **użytkownik musi zmienić hasło przy następnym logowaniu** pole wyboru.<br />6.  Wybierz **hasło nigdy nie wygasa** pole wyboru.<br />7.  W **opis**, typ **konto używane jako konto dostępu do sieci dla klienta programu Configuration Manager usługi**.|  

###  <a name="InstallSQLServer"></a>Krok 1-9. Zainstaluj program SQL Server 2008 R2  
 Przed zainstalowaniem programu Configuration Manager, należy zainstalować program SQL Server 2008 R2 z dodatkiem SP1 i CU6 z dodatkiem SP1.  

> [!NOTE]   
>  Aby włączyć wszystkie funkcje programu SQL Server 2008 R2, należy zainstalować rolę serwera usług sieci Web (IIS), przed zainstalowaniem programu SQL Server 2008 R2.  

#### <a name="to-install-sql-server-2008-r2"></a>Aby zainstalować program SQL Server 2008 R2
1.  Uruchomić Centrum instalacji programu SQL Server.  

2.  W Centrum instalacji programu SQL Server, w okienku nawigacji kliknij **instalacji**.  

3.  W okienku szczegółów kliknij **nowej instalacji lub dodać funkcje do istniejącej instalacji**.  

     Zostanie uruchomiony Kreator instalacji programu SQL Server 2008 R2.  

4.  Zainstaluj program SQL Server 2008 R2 korzystając z poniższych informacji, zaakceptuj ustawienia domyślne, chyba że określono inaczej.  

  |**Na tej stronie kreatora**|**W tym**|  
  |-|-|  
  |**Reguły obsługi instalacji**|Kliknij przycisk **OK**.|  
  |**Klucz produktu**|Kliknij przycisk **Dalej**.|  
  |**Postanowienia licencyjne**|Wybierz **akceptuję postanowienia licencyjne** pole wyboru, a następnie kliknij przycisk **dalej**.|  
  |**Pliki obsługi Instalatora**|Kliknij pozycję **Zainstaluj**.|  
  |**Reguły obsługi instalacji**|Upewnij się, czy istnieje dla reguł krytyczne nie zwróciło żadnych wyników, a następnie kliknij **dalej**.|  
  |**Rola Instalatora**|Kliknij przycisk **instalacja funkcji programu SQL Server**i kliknij przycisk **dalej**.|  
  |**Wybór funkcji**|1.  Wybierz **usługi aparatu bazy danych** pole wyboru.<br />2.  Wybierz **usług Reporting Services** pole wyboru.<br />3.  Wybierz **wyszukiwanie pełnotekstowe** pole wyboru.<br />4.  Wybierz **narzędzia do zarządzania — zakończenie** pole wyboru.<br />5.  Kliknij przycisk **Dalej**.|  
  |**Reguły instalacji**|Kliknij przycisk **Dalej**.|  
  |**Konfiguracja wystąpienia**|Kliknij przycisk **Dalej**.|  
  |**Wymagania dotyczące miejsca na dysku**|Kliknij przycisk **Dalej**.|  
  |**Konfiguracja serwera**|1.  Dla **programu SQL Server Agent**w **nazwa konta**, typ **MDT2013\SQLAgent**i w **hasło**, typ  **P@ssw0rd**.<br />2.  Dla **aparatu bazy danych programu SQL Server**w **nazwa konta**, typ **MDT2013\SQLDBEngine**w **hasło**, typ  **P@ssw0rd** .<br />3.  Dla **programu SQL Server Reporting Services**w **nazwa konta**, typ **MDT2013\SQLReport**w **hasło**, typ  **P@ssw0rd** .<br />4.  Kliknij przycisk **Dalej**.|  
  |**Konfiguracja aparatu bazy danych**|Kliknij przycisk **Dodaj bieżącego użytkownika**i kliknij przycisk **dalej**.|  
  |**Konfiguracja usług raportowania**|Kliknij przycisk **Dalej**.|  
  |**Raportowanie błędów**|Kliknij przycisk **Dalej**.|  
  |**Reguły konfiguracji instalacji**|Kliknij przycisk **Dalej**.|  
  |**Gotowy do instalacji**|Kliknij pozycję **Zainstaluj**.|  
  |**Zakończenie**|Kliknij przycisk **Zamknij**.|  

5.  Zamknij Centrum instalacji programu SQL Server.  

#### <a name="to-install-sql-server-2008-r2-sp1"></a>Aby zainstalować program SQL Server 2008 R2 z dodatkiem SP1
1.  W Eksploratorze Windows przejdź do E:\Source$\SQL2008R2SP1, a następnie kliknij dwukrotnie **SQLServer2008R2SP1-KB2528583-x64-ENU.exe**.  

     **Wyodrębnianie plików** proces wyodrębniania pliku wyświetla okno dialogowe. Po zakończeniu procesu zostanie uruchomiony Kreator konfiguracji SQL Server 2008 R2 Service Pack 1 aktualizacji.  

2.  Zainstaluj program SQL Server 2008 R2 SP1 korzystając z poniższych informacji, zaakceptuj ustawienia domyślne, chyba że określono inaczej.        

  |**Na tej stronie kreatora**|**W tym**|  
  |-|-|  
  |**Aktualizacja programu SQL Server 2008 R2**|Kliknij przycisk **Dalej**.|  
  |**Postanowienia licencyjne**|Wybierz **akceptuję postanowienia licencyjne** pole wyboru, a następnie kliknij przycisk **dalej**.|  
  |**Wybieranie funkcji**|Kliknij przycisk **Dalej**.|  
  |**Sprawdź pliki w użyciu**|Kliknij przycisk **Dalej**.|  
  |**Gotowy do aktualizacji**|Kliknij przycisk **aktualizacji**.|  
  |**Postęp aktualizacji**|Postęp jest wyświetlany na stronie kreatora aktualizacji jest wykonywane i zakończeniu.|  
  |**Zakończenie**|Kliknij przycisk **Zamknij**.|  

#### <a name="to-install-sql-server-2008-r2-sp1-cu6"></a>Aby zainstalować program SQL Server 2008 R2 z dodatkiem SP1 CU6
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

6.  Zainstaluj program SQL Server 2008 R2 z dodatkiem SP1 CU6 korzystając z poniższych informacji, zaakceptuj ustawienia domyślne, chyba że określono inaczej.  

  |**Na tej stronie kreatora**|**W tym**|  
  |-|-|  
  |**Aktualizacja programu SQL Server 2008 R2**|Kliknij przycisk **Dalej**.|  
  |**Postanowienia licencyjne**|Wybierz **akceptuję postanowienia licencyjne** pole wyboru, a następnie kliknij przycisk **dalej**.|  
  |**Wybieranie funkcji**|Kliknij przycisk **Dalej**.|  
  |**Sprawdź pliki w użyciu**|Kliknij przycisk **Dalej**.|  
  |**Gotowy do aktualizacji**|Kliknij przycisk **aktualizacji**.|  
  |**Postęp aktualizacji**|Postęp jest wyświetlany na stronie kreatora jako aktualizacja jest wykonywana.|  
  |**Zakończenie**|Kliknij przycisk **Zamknij**.|  

  **Instalacji programu SQL Server 2008 R2 Update** zostanie wyświetlone okno dialogowe monitowania użytkownika o ponowne uruchomienie komputera w celu ukończenia instalacji.  

7.  W **zainstalowanie aktualizacji programu SQL Server 2008 R2** okno dialogowe, kliknij przycisk **OK**.  

8.  Uruchom ponownie komputer.  

9. Po zainstalowaniu programu SQL Server 2008 R2 z dodatkiem SP1 CU6, numer kompilacji programu SQL Server należy 10.51.2811.0.  

    > [!TIP]    
    >  Sprawdź numer kompilacji programu SQL Server, wyświetlając zastosowanych w aplecie Programy i funkcje w Panelu sterowania po kliknięciu elementu aktualizacji programu SQL Server **Wyświetl zainstalowane aktualizacje**.  

###  <a name="AddSiteSecuritytoAdminGroup"></a>Krok 1-10. Dodaj serwer lokacji do grupy zabezpieczeń Administratorzy  
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

###  <a name="InstallConfigManager"></a>Krok 1-11. Instalowanie programu Configuration Manager  
 Podczas instalowania innych produktów i technologii, instalowanie programu Configuration Manager. Przed dokonaniem, jednak rozszerzyć schemat usługi Active Directory, aby komputery mogły zlokalizować punkty dystrybucji, punkty lokalizatora usług i innych ról serwera. Ponadto można rozszerzyć schemat, po zainstalowaniu programu Configuration Manager. Aby uzyskać więcej informacji na temat rozszerzania schematu usługi Active Directory programu Configuration Manager zobacz sekcję "Rozszerzyć schemat usługi Active Directory" w bibliotece dokumentacji programu Configuration Manager, który jest instalowany z programem Configuration Manager.  

 Po rozszerzeniu schematu usługi Active Directory, można zainstalować programu Configuration Manager. Konfiguracja WDG-MDT-01 obsługi programu Configuration Manager dla tego przykładu. Konfiguracja komputerów w sieci produkcyjnej może się różnić. Aby dowiedzieć się więcej na temat wymagań wstępnych dotyczących instalowania programu Configuration Manager, zobacz [obsługiwane konfiguracje programu Configuration Manager](http://technet.microsoft.com/library/gg682077.aspx).  

#### <a name="to-install-configuration-manager"></a>Aby zainstalować program Configuration Manager
1.  Uruchom Instalator programu System Center 2012 R2 Configuration Manager ekranu powitalnego.  

2.  Na ekranie powitalnym Instalator programu System Center 2012 R2 Configuration Manager kliknij przycisk **zainstalować** łącza.  

     Uruchamia Kreatora programu Microsoft System Center 2012 R2 Configuration Manager Instalatora.  

3.  Ukończ Kreatora programu Microsoft System Center 2012 R2 konfiguracji Menedżera konfiguracji korzystając z poniższych informacji, zaakceptuj ustawienia domyślne, chyba że określono inaczej.  

  |**Na tej stronie kreatora**|**W tym**|  
  |-|-|  
  |**Przed rozpoczęciem**|Kliknij przycisk **Dalej**.|  
  |**Wprowadzenie**|Kliknij przycisk **Dalej**.|  
  |**Klucz produktu**|W **wprowadź klucz produktu 25-znakowy**, typ ***klucz_produktu*** (gdzie *klucz_produktu* jest klucz produktu programu Configuration Manager).|  
  |**Postanowienia licencyjne dotyczące oprogramowania firmy Microsoft**|Wybierz **akceptuję postanowienia licencyjne** pole wyboru, a następnie kliknij przycisk **dalej**.|  
  |**Licencje wymagań wstępnych**|1.  W **programu Microsoft SQL Server 2008 R2 Express** zaznacz **akceptuję niniejsze postanowienia licencyjne** pole wyboru.<br />2.  W **Microsoft SQL Server 2008 Native Client** zaznacz **akceptuję niniejsze postanowienia licencyjne** pole wyboru.<br />3.  W **Microsoft Silverlight 4** zaznacz **akceptuję te postanowienia licencyjne i aktualizacje automatyczne programu Silverlight** pole wyboru.<br />4.  Kliknij przycisk **Dalej**.|  
  |**Aktualizacja wstępnie wymagane składniki**|W **pobrania i zastosowania najnowszych aktualizacji. Aktualizacje zostaną zapisane w następującej lokalizacji**, typ **E:\CMDownloads**, a następnie kliknij przycisk **dalej**.|  
  |**Wybór języka serwera**|Kliknij przycisk **Dalej**.|  
  |**Wybór języka klienta**|Kliknij przycisk **Dalej**.|  
  |**Ustawienia lokacji i instalacji**|1.  W **kod lokacji**, typ **NYC**.<br />2.  W **nazwa witryny**, typ **lokacji nowego Jorku**.<br />3.  Kliknij przycisk **Dalej**.|  
  |**Instalacja lokacji podstawowej**|1.  Kliknij przycisk **zainstalować lokację główną jako autonomiczną**.<br />2.  Kliknij przycisk **Dalej**.<br />     **Programu Configuration Manager** zostanie wyświetlone okno dialogowe potwierdzenia chcesz zainstalować tę lokację jako autonomiczną lokację.<br />3.  W **programu Configuration Manager** okno dialogowe, kliknij przycisk **tak**.|  
  |**Informacje o bazie danych**|Kliknij przycisk **Dalej**.|  
  |**Ustawienia dostawcy programu SMS**|Kliknij przycisk **Dalej**.|  
  |**Ustawienia komunikacji z komputerem klienckim**|Kliknij przycisk **Konfiguruj metodę komunikacji w każdej roli systemu lokacji**, a następnie kliknij przycisk **dalej**.|  
  |**Role systemu lokacji**|Kliknij przycisk **Dalej**.|  
  |**Konfiguracja programu poprawy jakości obsługi klienta**|1.  Wybierz odpowiedni udział w programie poprawy jakości obsługi klienta dla Twojej organizacji.<br />2.  Kliknij przycisk **Dalej**.|  
  |**Podsumowanie ustawień**|Kliknij przycisk **Dalej**.|  
  |**Sprawdzanie wymagań wstępnych**|Kliknij przycisk **rozpocząć instalację**.|  
  |**Instalowanie**|1.  Monitoruje proces instalacji, do czasu ukończenia.<br />2.  Kliknij przycisk **Zamknij**.|  

4.  Zamknij wszystkie otwarte okna i oknach dialogowych.  

 Po ukończeniu działania kreatora programu Configuration Manager jest zainstalowany.  

###  <a name="ConfigureNetworkAccessAccount"></a>Krok 1-12. Konfigurowanie konta dostępu do sieci  
 Klient programu Configuration Manager potrzebuje konta, aby podać poświadczenia podczas uzyskiwania dostępu do punktów dystrybucji programu Configuration Manager, udział wdrożenia zestawu MDT i folderów udostępnionych. To konto jest nazywany *konta dostępu do sieci*. Konto CMNetAccess zostało utworzone wcześniej w trakcie procesu do użycia jako konto dostępu do sieci.  

#### <a name="to-configure-the-network-access-account"></a>Aby skonfigurować konto dostępu do sieci  
1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **administracji**.  

3.  W obszarze roboczym Administracja go — Omówienie/lokacji konfiguracji/lokacji.  

4.  W okienku podglądu kliknij **NYC — lokacji nowego Jorku**.  

5.  Na wstążce kliknij **ustawienia**, kliknij przycisk **Konfiguruj składniki lokacji**, a następnie kliknij przycisk **dystrybucji oprogramowania**.  

6.  W **właściwości składnika dystrybucji oprogramowania** okno dialogowe, kliknij przycisk **konta dostępu do sieci** kartę.  

7.  W **konta dostępu do sieci**, kliknij przycisk **Określ konto, który uzyskał dostęp do lokalizacji sieciowych**, kliknij przycisk **ustawić**, a następnie kliknij przycisk **nowe konto**.  

     **Konta użytkownika systemu Windows** zostanie wyświetlone okno dialogowe.  

8.  Zakończenie **konta użytkownika systemu Windows** za pomocą poniższych informacji, a następnie kliknij okno dialogowe **OK**.    

 |**Dla tego**|**W tym**|  
 |-|-|  
 |**Nazwa użytkownika**|Typ **MDT2013\CMNetAccess**.|  
 |**Hasło**|Typ  **P@ssw0rd** .|  
 |**Potwierdź hasło**|Typ  **P@ssw0rd** .|  

9. W **właściwości składnika dystrybucji oprogramowania** okno dialogowe, kliknij przycisk **OK**.  

10. Zamknij wszystkie otwarte okna.  

###  <a name="ConfigurationManagerSiteBoundaries"></a>Krok 1-13. Konfigurowanie granic lokacji programu Configuration Manager i grup granic  
 Klient programu Configuration Manager musi znać granice lokacji. O ile nie określono granicach lokacji, klient zakłada, że komputera z uruchomionym programu Configuration Manager w lokacji zdalnej. Dodaj granicę lokacji, na podstawie podsieci IP tego WDG-MDT-01, WDG-REF-01 i użycie WDG-CLI-01. Następnie dodaj granicę lokacji do grupy granic lokacji.  

#### <a name="to-create-a-configuration-manager-site-boundary"></a>Aby utworzyć granicę lokacji programu Configuration Manager
1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **administracji**.  

3.  W obszarze roboczym Administracja go — omówienie/hierarchia konfiguracji/granic.  

4.  Na wstążce kliknij **Utwórz granicę**.  

     **Utwórz granicę** zostanie otwarte okno dialogowe.  

5.  Zakończenie **Utwórz granicę** za pomocą poniższych informacji, a następnie kliknij okno dialogowe **OK**.  

    > [!NOTE]   
    >  Dla tego przykładu granicę lokacji jest określany przez adres sieciowy. Jednak można również określić lokacji granice lokacji za pomocą usług AD DS, nazwa lub zakres adresów IP.  

   |**Dla tego**|**W tym**|  
   |-|-|  
   |**Opis**|Typ **granicę podsieci IP**.|  
   |**Typ**|Wybierz **podsieci IP**.|  
   |**Sieć**|Typ ***network_address*** (gdzie *network_address* jest adres sieciowy podsieci, gdy komputery są zainstalowane).|  
   |**Maska podsieci**|Typ ***subnet_mask*** (gdzie *subnet_mask* to maska podsieci podsieci, gdy komputery są zainstalowane).|  

#### <a name="to-add-the-configuration-manager-site-boundary-to-a-site-boundary-group"></a>Aby dodać granicę lokacji programu Configuration Manager do grupy granic lokacji  
1.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **administracji**.  

2.  W obszarze roboczym Administracja przejdź do grupy konfiguracji/granic przegląd/hierarchii.  

3.  Na wstążce kliknij **Utwórz grupę granicę**.  

     **Utwórz grupę granicę** zostanie otwarte okno dialogowe.  

4.  Zakończenie **ogólne** karcie **Utwórz grupę granicę** okno dialogowe, korzystając z poniższych informacji.

  |**Dla tego**|**W tym**|  
  |-|-|  
  |**Nazwa**|Typ **grupy granic w Nowym Jorku**.|  
  |**Opis**|Typ **jest to grupa granic dla granic lokacji w lokacji nowego Jorku**.|  
  |Granice|1.  Kliknij pozycję **Dodaj**.<br />     **Dodać granice** zostanie wyświetlone okno dialogowe.<br />2.  W **dodać granice** okno dialogowe, wybierz opcję ***site_boundary*** (gdzie *site_boundary* jest granicę lokacji został utworzony wcześniej w procesie), a następnie kliknij przycisk **OK**.<br />     Granicę lokacji zostanie wyświetlony na liście granic.|  

5.  Zakończenie **odwołania** karty **Utwórz grupę granicę** za pomocą poniższych informacji, a następnie kliknij okno dialogowe **OK**.  

  |**Dla tego**|**W tym**|  
  |-|-|  
  |**Przypisanie lokacji**|Wybierz **Użyj tej grupy granic do przypisania lokacji** pole wyboru.|  
  |**Lokalizacja zawartości**|1.  Kliknij pozycję **Dodaj**.<br />     **Dodać systemy lokacji** zostanie wyświetlone okno dialogowe.<br />2.  W **dodać systemy lokacji** okno dialogowe, wybierz opcję  **\\\WDG-MDT-01.mdt2013.corp.woodgrovebank.com**, a następnie kliknij przycisk **OK**.<br />     Serwer systemu lokacji zostanie wyświetlony na liście serwerów systemu lokacji.|  

6.  Zamknij wszystkie otwarte okna.  

###  <a name="ConfigurePublishingSiteInfo"></a>Krok 1-14. Skonfiguruj publikowanie informacji o lokacji w usługach AD DS i systemu DNS  
 Klient programu Configuration Manager musi zlokalizować różne role serwera programu Configuration Manager. Modyfikuj właściwości lokacji do publikowania informacji o lokacji w usługach AD DS, a w systemie DNS.  

 **Aby skonfigurować publikowanie informacji o lokacji w usługach AD DS, a w systemie DNS**  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **administracji**.  

3.  W obszarze roboczym Administracja go — Omówienie/lokacji konfiguracji/lokacji.  

4.  W okienku podglądu kliknij **NYC — lokacji nowego Jorku**.  

5.  Na wstążce kliknij **właściwości**.  

6.  W **właściwości lokacji nowego Jorku** na okna dialogowego **publikowania** karcie, upewnij się, że **mdt2013.corp.woodgrovebank.com** lasu usługi Active Directory jest wyświetlana, i następnie kliknij przycisk **anulować**.  

7.  Zamknij wszystkie otwarte okna.  

##  <a name="PrepareMDTEnvironment"></a>Krok 2. Przygotowanie środowiska zestawu MDT  
 Pierwszym krokiem w procesie wdrażania jest aby przygotować środowisko zestawu MDT. Po zakończeniu tego kroku możesz utworzyć komputer odniesienia i wdrażać przechwycony obraz do komputera docelowego (WDG-CLI-01) przy użyciu integracji programu Configuration Manager z zestawu MDT.  

 Przygotowanie środowiska MDT przez:  

-   Instalowanie zestawu MDT, zgodnie z opisem w [krok 2-1: Instalowanie zestawu MDT](#InstallMDT)  

-   Włączanie integracji konsoli programu Configuration Manager przez uruchomienie skryptu Konfigurowanie integracji programu ConfigMgr, zgodnie z opisem w [krok 2-2: Włącz integrację z konsoli programu Configuration Manager](#EnableConfigManagerConsole)  

###  <a name="InstallMDT"></a>Krok 2-1. Instalowanie zestawu MDT  
 Aby zainstalować zestaw MDT, wykonaj następujące czynności:  

1.  W Eksploratorze Windows przejdź do E:\Source$\MDT_2013.  

2.  Kliknij dwukrotnie **MicrosoftDeploymentToolkit2013_x64.msi** (dla 64-bitowych systemach operacyjnych) lub **MicrosoftDeploymentToolkit2013_x86.msi** (dla 32-bitowych systemach operacyjnych), a następnie kliknij przycisk **Zainstalować**.  

     Uruchamia Kreatora instalacji programu Microsoft Deployment Toolkit 2013.  

3.  Ukończ Microsoft Deployment Toolkit 2013 Kreatora instalacji korzystając z informacji w poniższej tabeli.  Zaakceptuj wartości domyślne, chyba że określono inaczej.  

  |**Na tej stronie kreatora**|**W tym**|  
  |-|-|  
  |**Kreator instalacji 2013 Microsoft Deployment Toolkit — Zapraszamy!**|Kliknij przycisk **Dalej**.|  
  |**Umowa licencyjna użytkownika oprogramowania**|Kliknij przycisk **akceptuję warunki umowy licencyjnej**, a następnie kliknij przycisk **dalej**.|  
  |**Instalacja niestandardowa**|Kliknij przycisk **Dalej**.|  
  |**Gotowy do zainstalowania programu Microsoft Deployment Toolkit 2013**|Kliknij pozycję **Zainstaluj**.|  
  |**Instalowanie zestawu narzędzi firmy Microsoft do wdrażania 2013**|Zostanie wyświetlony pasek postępu instalacji zestawu MDT.|  
  |**Kończenie pracy Kreatora instalacji programu Microsoft Deployment Toolkit 2013**|Kliknij przycisk **Zakończ**.|  

 Ukończeniu działania Kreatora instalacji programu Microsoft Deployment Toolkit 2013 i zestaw MDT jest zainstalowany na WDG-MDT-01.  

###  <a name="EnableConfigManagerConsole"></a>Krok 2-2. Włącz integrację z konsoli programu Configuration Manager  
 Przed użyciem programu Configuration Manager funkcje integracji zestawu mdt, uruchom skrypt Konfigurowanie integracji programu ConfigMgr. Ten skrypt kopiuje pliki integracji odpowiednie do folderu, w którym program Configuration Manager jest zainstalowany. Skrypt ten dodaje również klas Instrumentacji zarządzania Windows (WMI), nowe akcje niestandardowe zestawu MDT. Kompilowanie nowego pliku Managed Object Format (MOF), który zawiera nowe definicje klas są dodawane klasy.  

 **Aby włączyć integrację z konsoli programu Configuration Manager**  

> [!NOTE]   
>  Upewnij się, że konsola programu Configuration Manager zostały zamknięte podczas wykonywania tych kroków.  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **Konfigurowanie integracji programu ConfigMgr**.  

     Zostanie uruchomiony Kreator konfigurowania integracji programu ConfigMgr.  

2.  Ukończ Kreatora konfiguracji programu ConfigMgr integracji korzystając z informacji w poniższej tabeli. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

  |**Na tej stronie kreatora**|**W tym**|  
  |-|-|  
  |**Opcje**|1.  Sprawdź, czy **zainstalować rozszerzenia konsoli zestawu MDT dla programu System Center 2012 R2 Configuration Manager** pole wyboru jest zaznaczone.<br />2.  Sprawdź, czy **Dodaj akcje sekwencji zadań zestawu MDT do serwera programu System Center 2012 R2 Configuration Manager** pole wyboru jest zaznaczone.<br />3.  W **nazwa serwera lokacji**, sprawdź, czy wartość jest **WDG — MDT-01.mdt2013.corp.woodgrovebank.com**.<br />4.  W **kod lokacji**, sprawdź, czy wartość jest **NYC**.<br />5.  Kliknij przycisk **Dalej**.|  
  |**Potwierdzenie**|Kliknij przycisk **Zakończ**.|  

 Zakończeniu pracy Kreatora konfigurowania integracji programu ConfigMgr, a zestaw MDT jest zintegrowany z programem Configuration Manager.  

## <a name="step-3-create-and-configure-a-task-sequence-to-create-a-reference-computer"></a>Krok 3. Tworzenie i konfigurowanie sekwencji zadań w celu utworzenia komputera odniesienia  
 Po przygotowaniu środowiska zestawu MDT, należy utworzyć komputer odniesienia. Komputer odniesienia jest szablon do wdrażania nowych obrazów na komputerach docelowych. Dokładnie tak, jak skonfiguruje komputerów docelowych, należy skonfigurować komputer (WDG-REF-01). Następnie zostanie przechwycony obraz komputera odniesienia i wdrażania obrazu na komputerach docelowych.  

 Utwórz komputer odniesienia WDG-REF-01 przez:  

-   Tworzenie sekwencji zadań zestawu MDT do wdrożenia Windows 8.1 na komputerze odniesienia, zgodnie z opisem w [krok 3-1: Utwórz sekwencję zadań zestawu MDT do wdrażania na komputerze odniesienia](#CreateMDTTaskSequence)  

-   Wybieranie punktów dystrybucji dla nowych pakietów i obrazów, które tworzy Kreatora tworzenia sekwencji zadań zestawu MDT, zgodnie z opisem w [krok 3-2: Wybierz punkty dystrybucji dla nowych pakietów i obrazów](#SelectDistroPoints)  

-   Dodawanie sterowników urządzeń na potrzeby nowego pakietu dysku i obrazy rozruchowe odpowiednie zgodnie z opisem w [kroku nr 3, 3: Dodaj sterowniki urządzeń wymagane](#AddDeviceDrivers)  

-   Włącz monitorowanie procesu wdrożenia zestawu MDT, zgodnie z opisem w [krok 3 — 4: Włącz wdrożenia zestawu MDT monitorowania procesu](#EnableMDTDeployProcess)  

-   Konfigurowanie pliki konfiguracyjne zestawu MDT dla komputera odniesienia — w szczególności pliku CustomSettings.ini — zgodnie z opisem w [krok 3 – 5: Dostosowywanie pliki konfiguracyjne zestawu MDT dla komputera odniesienia](#CustomizeMDTConfigFiles)  

-   Aktualizowanie punkty dystrybucji programu Configuration Manager dla pakietu pliki ustawień niestandardowych, zgodnie z opisem w [krok 3 – 6: Aktualizuj punkty dystrybucji dla pakietu plików ustawień niestandardowych](#UpdateDistroPoint)  

-   Dostosowywanie sekwencji zadań dla komputera odniesienia, zgodnie z opisem w [kroku 3-7: Dostosowywanie sekwencji zadań dla komputera odniesienia](#CustomizeTaskSequence)  

###  <a name="CreateMDTTaskSequence"></a>Krok 3-1. Utwórz sekwencję zadań zestawu MDT do wdrażania na komputerze odniesienia  
 Użyj Kreatora tworzenia sekwencji zadań zestawu MDT w konsoli programu Configuration Manager do tworzenia sekwencji zadań w programie Configuration Manager, które są zintegrowane z zestawu MDT. Zestaw MDT obejmuje szablonu standardowe sekwencję zadań klienta, który służy do wdrażania na komputerze odniesienia.  

 Kreatora tworzenia sekwencji zadań zestawu MDT zastępuje pakiety i obrazy wybrane symboli zastępczych w szablonach sekwencji zadań. Po zakończeniu pracy Kreatora nowej sekwencji zadań odwołuje się do odpowiednich pakietów i obrazów.  

> [!NOTE]   
>  Zawsze używać Kreatora tworzenia sekwencji zadań zestawu MDT do tworzenia sekwencji zadań na podstawie szablonów sekwencji zadań zestawu MDT. Mimo że można ręcznie zaimportować szablony sekwencji zadań, firma Microsoft zaleca tego procesu.  

#### <a name="to-create-a-task-sequence-for-deploying-the-reference-computer"></a>Aby utworzyć sekwencję zadań do wdrażania na komputerze odniesienia  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **Biblioteka oprogramowania**.  

3.  W obszarze roboczym Biblioteka oprogramowania przejdź do Przegląd/operacyjnego systemów lub zadanie sekwencji.  

4.  Na wstążce na **Home** karcie **sekwencje zadań** kliknij przycisk **Utwórz sekwencję zadań zestawu MDT**.  

     Uruchamia Kreatora tworzenia sekwencji zadań zestawu MDT.  

5.  Ukończ MDT Kreatora tworzenia sekwencji zadań przy użyciu informacji w poniższej tabeli. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

  |**Na tej stronie kreatora**|**W tym**|  
  |-|-|  
  |**Wybieranie szablonu**|Wybierz **sekwencję zadań klienta**, a następnie kliknij przycisk **dalej**.|  
  |**Wybierz szablon: Ogólne**|1.  W **nazwę sekwencji zadań**, typ **Windows 8.1 odwołanie wdrożenia**.<br />2.  W **komentarze sekwencji zadań**, typ **sekwencję zadań pod kątem wdrażania na komputerze odniesienia (WDG-REF-01) Windows 8.1**, a następnie kliknij przycisk **dalej**.|  
  |**Wybierz szablon: Szczegóły**|1.  Kliknij przycisk **Przyłącz do grupy roboczej**.<br />2.  W **grupy roboczej**, typ **grupy roboczej**.<br />3.  W **nazwy użytkownika**, typ **pracownika banku Woodgrove**.<br />4.  W **nazwa organizacji**, typ **banku Woodgrove**.<br />5.  W **klucz produktu**, typ ***klucz_produktu*** (gdzie *klucz_produktu* jest klucz produktu dla Windows 8.1).<br />6.  Kliknij przycisk **Dalej**.|  
  |**Wybierz szablon: Przechwyć ustawienia**|<ol><li>Kliknij przycisk **ta sekwencja zadań może służyć do przechwytywania i obrazów**.</li><li>W **miejsce docelowe przechwytywania**, typ  **\\\WDG-MDT-01\Capture$\WDG-REF-01.wim**.</li><li>W **konto przechwytywania**, kliknij przycisk **ustawić**.</li><li>Zakończenie **konta użytkownika systemu Windows** okno dialogowe, wykonując następujące czynności:<br /><br /> <ol><li>W **nazwy użytkownika**, typ **MDT2013\Administrator**.</li><li>W **hasło** i **Potwierdź hasło**, typ  **P@ssw0rd** .</li></ol></li><li>Kliknij przycisk **OK**.</li><li>Kliknij przycisk **Dalej**.</li></ol>|  
  |**Obraz rozruchowy**|1.  Kliknij przycisk **utworzyć nowy pakiet obrazu rozruchowego**.<br />2.  W **folderu źródłowego pakietu należy utworzyć**, typ  **\\\WDG-MDT-01\Packages$\WINPE_Custom**, a następnie kliknij przycisk **dalej**.|  
  |**Obraz rozruchowy: Ustawienia ogólne**|1.  W **nazwa**, typ **niestandardowych systemu Windows PE**.<br />2.  W **wersji**, typ **1,00**.<br />3.  W **komentarze**, typ **dostosowane wersję środowiska Windows PE do użycia we wdrożeniu komputerów referencyjnych i docelowych**, a następnie kliknij przycisk **dalej**.|  
  |**Obraz rozruchowy: Opcje**|W obszarze **platformy**, kliknij przycisk **x64**, a następnie kliknij przycisk **dalej**.|  
  |**Obraz rozruchowy: Składniki**|Kliknij przycisk **Dalej**.|  
  |**Obraz rozruchowy: Dostosowywanie**|Kliknij przycisk **Dalej**.|  
  |**Pakiet zestawu MDT**|1.  Kliknij przycisk **utworzyć nowy pakiet plików zestawu narzędzi wdrażania Microsoft**.<br />2.  W **folderu źródłowego pakietu należy utworzyć**, typ  **\\\WDG-MDT-01\Packages$\MDT_Files**, a następnie kliknij przycisk **dalej**.|  
  |**Zestaw MDT pakietu: Szczegóły zestawu MDT**|1.  W **nazwa**, typ **pliki zestawu MDT**.<br />2.  W **wersji**, typ **1,00**.<br />3.  W **komentarze**, typ **zapewnia dostęp do plików zestawu MDT podczas procesu wdrażania programu Configuration Manager**, a następnie kliknij przycisk **dalej**.|  
  |**Obraz systemu operacyjnego**|1.  Kliknij przycisk **pakiet instalacyjny Tworzenie nowego systemu operacyjnego**.<br />2.  W **lokalizacja folderu instalacji systemu operacyjnego**, typ  **\\\WDG-MDT-01\Source$\Windows_7**.<br />3.  W **folderu źródłowego pakietu należy utworzyć**, typ  **\\\WDG-MDT-01\Packages$\Windows_7**, a następnie kliknij przycisk **dalej**.|  
  |**Obraz systemu operacyjnego: Szczegóły obrazu**|1.  W **nazwa**, typ **Windows 8.1**.<br />2.  W **wersji**, typ **1,00**.<br />3.  W **komentarze**, typ **pakietu Windows 8.1 używane do wdrażania na komputerach odniesienia**, a następnie kliknij przycisk **dalej**.|  
  |**Metody wdrażania**|Kliknij przycisk **Dalej**.|  
  |**Pakiet klienta**|Kliknij przycisk **utworzenia nowego pakietu klienta programu ConfigMgr**, a następnie kliknij przycisk **dalej**.|  
  |**Pakiet USMT**|1.  Kliknij przycisk **utworzyć nowy pakiet narzędzia USMT**.<br />2.  W **folderu źródłowego pakietu należy utworzyć**, typ  **\\\WDG-MDT-01\Packages$\USMT**, a następnie kliknij przycisk **dalej**.|  
  |**Pakiet narzędzia USMT: Szczegóły narzędzia USMT**|1.  W **nazwa**, typ **USMT**.<br />2.  W **wersji**, typ **1,00**.<br />3.  W **komentarze**, typ **pliki narzędzia USMT służące do przechwytywania i przywracania informacje o migracji stanu użytkownika**, a następnie kliknij przycisk **dalej**.|  
  |**Ustawienia pakietu**|1.  Kliknij przycisk **utworzyć nowy pakiet ustawienia**.<br />2.  W **folderu źródłowego pakietu należy utworzyć**, typ  **\\\WDG-MDT-01\Packages$\CustomSettings_Reference**, a następnie kliknij przycisk **dalej**.|  
  |**Pakiet ustawień: Szczegóły ustawień**|1.  W **nazwa**, typ **ustawień niestandardowych komputera odniesienia MDT**.<br />2.  W **wersji**, typ **1,00**.<br />3.  W **komentarze**, typ **ustawienia konfiguracji dla zestawu MDT procesu wdrażania (na przykład CustomSettings.ini) dla komputera odniesienia**, a następnie kliknij przycisk **dalej**.|  
  |**Pakiet programu Sysprep**|Kliknij przycisk **Dalej**.|  
  |**Podsumowanie**|1.  Przejrzyj informacje w **szczegóły** pola, czy podane podczas wykonywania poprzednich stron kreatora.<br />2.  Kliknij przycisk **Dalej**.|  
  |**Postęp**|Zostanie wyświetlony pasek postępu tworzenia sekwencji zadań.|  
  |**Potwierdzenie**|Kliknij przycisk **Zakończ**.|  

   Nowej sekwencji zadań zostanie wyświetlony w okienku podglądu.  

###  <a name="SelectDistroPoints"></a>Krok 3-2. Wybierz punkty dystrybucji dla nowych pakietów i obrazów  
 Kreatora tworzenia sekwencji zadań zestawu MDT tworzy pakietów i obrazów. Po utworzeniu te pakiety i obrazów, wybierz punkty dystrybucji, z których pakietów i obrazy będą kopiowane i dostępne dla komputerów docelowych.  

> [!NOTE]   
>  W tym przykładzie istnieje tylko jeden punkt dystrybucji (WDG-MDT-01). Jednak większość sieci produkcyjnej ma wiele punktów dystrybucji. Podczas wykonywania tego kroku w środowisku produkcyjnym, wybierz odpowiednie punkty dystrybucji w sieci.  

#### <a name="to-select-the-distribution-points-for-software-distribution-packages"></a>Aby wybrać punkty dystrybucji dla pakietów dystrybucji oprogramowania  
1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **Biblioteka oprogramowania**.  

3.  W obszarze roboczym Biblioteka oprogramowania przejdź do Przegląd/operacyjnego systemów lub zadanie sekwencji.  

4.  W okienku podglądu wybierz **Windows 8.1 odwołanie wdrożenia**.  

5.  Na wstążce na **Home** karcie **wdrożenia** kliknij przycisk **Dystrybuuj zawartość**.  

     Uruchamia Kreatora dystrybucji zawartości.  

6.  Ukończ Kreatora dystrybucji zawartości przy użyciu informacji w poniższej tabeli. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

  |**Na tej stronie kreatora**|**W tym**|  
  |-|-|  
  |**Ogólne**|Kliknij przycisk **Dalej**.|  
  |**Ogólne: Zawartość**|Kliknij przycisk **Dalej**.|  
  |**Ogólne: Miejsce docelowe zawartości**|1.  Kliknij przycisk **Dodaj**, a następnie kliknij przycisk **punktu dystrybucji**.<br />     **Punktów dystrybucji Dodaj** zostanie wyświetlone okno dialogowe.<br />2.  W **punktów dystrybucji Dodaj** okno dialogowe, wybierz opcję **WDG — MDT-01.mdt2013.corp.woodgrovebank.com**, a następnie kliknij przycisk **OK**.<br />     WDG — MDT-01.corp.woodgrovebank.com pojawia się w **miejsce docelowe zawartości** listy.<br />3.  Kliknij przycisk **Dalej**.|  
  |**Podsumowanie**|1.  Przejrzyj informacje w **szczegóły** pola, czy podane podczas wykonywania poprzednich stron kreatora.<br />2.  Kliknij przycisk **Dalej**.|  
  |**Postęp**|Zostanie wyświetlony pasek postępu do dystrybucji oprogramowania.|  
  |**Zakończenie**|Kliknij przycisk **Zamknij**.|  

7.  Zamknij wszystkie otwarte okna i oknach dialogowych.  

###  <a name="AddDeviceDrivers"></a>Krok 3-3. Dodaj sterowniki urządzeń wymagane  
 Po utworzeniu sekwencji zadań zestawu MDT, należy dodać sterowniki urządzeń wymagane dla komputera odniesienia (WDG-REF-01) do systemu Windows PE obrazu rozruchowego i obrazu Windows 8.1. Dodaj sterowniki urządzeń w węźle sterowniki w konsoli programu Configuration Manager. Utwórz pakiet zawierający sterowniki urządzeń i Wstaw sterowniki do niestandardowego obrazu środowiska Windows PE utworzony wcześniej w procesie.  

 Po utworzeniu pakietu, który zawiera sterowniki urządzeń, wybierz opcję dystrybucji punktu, do którego będzie można wdrożyć pakietu.  

#### <a name="to-add-the-necessary-device-drivers"></a>Aby dodać sterowniki urządzeń wymagane
1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **Biblioteka oprogramowania**.  

3.  W obszarze roboczym Biblioteka oprogramowania go — omówienie/operacyjnego systemów/sterowniki.  

4.  Na wstążce na **Home** karcie **Utwórz** kliknij przycisk **Importuj sterownik**.  

     Uruchamia Kreatora importowania nowego sterownika.  

5.  Ukończ Kreatora importowania nowego sterownika korzystając z informacji w poniższej tabeli.  Zaakceptuj wartości domyślne, chyba że określono inaczej.  

  |**Na tej stronie kreatora**|**W tym**|  
  |-|-|  
  |**Zlokalizuj sterownik**|W **folder źródłowy**, typ  **\\\WDG-MDT-01\Source$\Drivers**, a następnie kliknij przycisk **dalej**.|  
  |**Znajdź sterowników: Szczegóły sterownika**|Kliknij przycisk **Dalej**.|  
  |**Znajdź sterowników: Dodaj sterownik do pakietu**|<ol><li>Kliknij przycisk **nowy pakiet**.</li><li>Zakończenie **nowy pakiet sterowników** okno dialogowe, wykonując następujące czynności:<br /><br /> <ol><li>W **nazwa**, typ ***device_driver_name*** pakietu (gdy *device_driver_name* jest nazwę opisową dla sterowników urządzeń).</li><li>W **komentarz**, typ **sterowniki urządzeń, które są niezbędne dla komputerów referencyjnych i docelowych**.</li></ol></li><li>W **źródła pakietu sterowników**, typ  **\\\WDG-MDT-01\Packages$\Drivers**, a następnie kliknij przycisk **OK**.</li><li>Kliknij przycisk **Dalej**.</li></ol>|  
  |**Znajdź sterowników: Dodaj sterownik do obrazów rozruchowych**|1.  Listy obrazów, wybierz **niestandardowych systemu Windows PE** pole wyboru.<br />2.  Wybierz **Aktualizuj punkty dystrybucji po zakończeniu** pole wyboru, a następnie kliknij przycisk **dalej**.|  
  |**Podsumowanie**|1.  Przejrzyj informacje w **szczegóły** pola, czy podane podczas wykonywania poprzednich stron kreatora.<br />2.  Kliknij przycisk **Dalej**.|  
  |**Postęp**|Zostanie wyświetlony pasek postępu do importowania sterowników urządzeń.|  
  |**Potwierdzenie**|Kliknij przycisk **Zamknij**.|  

#### <a name="to-select-the-distribution-points-for-the-driver-package"></a>Aby wybrać punkty dystrybucji dla pakietu sterowników
1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **Biblioteka oprogramowania**.  

3.  W obszarze roboczym Biblioteka oprogramowania przejdź do pakietów systemów/Driver Przegląd/operacyjnych.  

4.  W okienku podglądu kliknij ***device_driver_name*** **pakietu** (gdzie *device_driver_name* jest nazwę opisową dla sterowników urządzeń).  

5.  Na wstążce na **Home** karcie **wdrożenia** kliknij przycisk **Dystrybuuj zawartość**.  

     Uruchamia Kreatora dystrybucji zawartości.  

6.  Ukończ Kreatora dystrybucji zawartości korzystając z poniższych informacji. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

  |**Na tej stronie kreatora**|**W tym**|  
  |-|-|  
  |**Ogólne**|Kliknij przycisk **Dalej**.|  
  |**Ogólne: Zawartość**|Kliknij przycisk **Dalej**.|  
  |**Ogólne: Miejsce docelowe zawartości**|1.  Kliknij przycisk **Dodaj**, a następnie kliknij przycisk **punktu dystrybucji**.<br />     **Punktów dystrybucji Dodaj** zostanie wyświetlone okno dialogowe.<br />2.  W **punktów dystrybucji Dodaj** okno dialogowe, wybierz opcję  **\\\WDG-MDT-01.mdt2013.corp.woodgrovebank.com**, a następnie kliknij przycisk **OK**.<br />     \\\WDGMDT01.mdt2013.corp.woodgrovebank.com pojawia się w **miejsce docelowe zawartości** listy.<br />3.  Kliknij przycisk **Dalej**.|  
  |**Podsumowanie**|1.  Przejrzyj informacje w **szczegóły** pola, czy podane podczas wykonywania poprzednich stron kreatora.<br />2.  Kliknij przycisk **Dalej**.|  
  |**Postęp**|Zostanie wyświetlony pasek postępu do dystrybucji oprogramowania.|  
  |**Zakończenie**|Kliknij przycisk **Zamknij**.|  

7.  Zamknij wszystkie otwarte okna i oknach dialogowych.  

###  <a name="EnableMDTDeployProcess"></a>Krok 3 — 4: Włącz wdrożenia zestawu MDT monitorowania procesu  
 Przed wdrożeniem na komputerze odniesienia (WDG-REF-01) z nośnika rozruchowego sekwencji zadań, aby włączyć monitorowanie MDT ZTI procesu wdrażania. Monitorowanie na **monitorowanie** kartę na udział wdrożenia **właściwości** okno dialogowe. W dalszej części procesu, można monitorować proces wdrożenia ZTI przy użyciu konsoli Deployment Workbench lub **Get-MDTMonitorData** polecenia cmdlet.  

 **Aby włączyć monitorowanie procesu wdrażania ZTI zestawu MDT**  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench przejdź do wdrożenia środowiska roboczego/wdrożenia udziałów.  

3.  W okienku Akcje kliknij polecenie **nowe udziały wdrożenia**.  

     Uruchamia Kreatora nowego udziału wdrożenia.  

4.  Ukończyć Kreatora nowego udziału wdrożenia korzystając z poniższych informacji

   |**Na tej stronie kreatora**|**W tym**|  
   |-|-|  
   |**Na tej stronie kreatora**|**W tym**|  
   |**Ścieżka**|W **ścieżka udziału wdrożenia**, typ **C:\DeploymentShare$**, a następnie kliknij przycisk **dalej**.|  
   |**Udostępnij**|Kliknij przycisk **Dalej**.|  
   |**Opisowa nazwa**|Kliknij przycisk **Dalej**.|  
   |**Opcje**|Kliknij przycisk **Dalej**.|  
   |**Podsumowanie**|Kliknij przycisk **Dalej**.|  
   |**Postęp**|Zostanie wyświetlony pasek postępu tworzenia udziału wdrożenia.|  
   |**Potwierdzenie**|Kliknij przycisk **Zakończ**.|  

  Zakończenie Kreatora nowego udziału wdrożenia, a nowy udział wdrożenia — udział wdrożenia zestawu MDT (C:\DeploymentShare$)—appears w okienku szczegółów.  


5.  W okienku szczegółów kliknij **udział wdrożenia zestawu MDT (C:\DeploymentShare$)**.  

6.  W okienku Akcje kliknij polecenie **właściwości**.  

     **Właściwości udziału wdrożenia zestawu MDT (C:\DeploymentShare$)** zostanie otwarte okno dialogowe.  

7.  W **właściwości udział wdrożenia zestawu MDT (C:\DeploymentShare$)** na okna dialogowego **monitorowanie** wybierz opcję **Włącz monitorowanie dla tego udziału wdrożenia** pole wyboru , a następnie kliknij przycisk **Zastosuj**.  

8.  W **właściwości udziału wdrożenia zestawu MDT (C:\DeploymentShare$)** na okna dialogowego **reguły** karcie, zwróć uwagę, że **EventService** właściwość została dodana do Plik CustomSettings.ini, a następnie kliknij przycisk **OK**.  

  **EventService** właściwości wygląda następująco:  

    ```  
    EventService=http://WDG-MDT-01:9800  
    ```  

9. Zamknij wszystkie otwarte okna i oknach dialogowych.  

###  <a name="CustomizeMDTConfigFiles"></a>Krok 3 – 5. Dostosowywanie pliki konfiguracyjne zestawu MDT dla komputera odniesienia  
 Po utworzeniu sekwencji zadań zestawu MDT, należy dostosować pliki konfiguracyjne zestawu MDT, które zapewniają ustawienia konfiguracji wdrażania Windows 8.1 z komputerem docelowym. W szczególności Dostosowywanie pliku CustomSettings.ini.  

 Po zakończeniu dostosowywania pliku CustomSettings.ini, Zapisz zaktualizowane pliki do folderu źródłowego pakietu ustawień niestandardowych komputera odniesienia MDT utworzony wcześniej w procesie (E:\Packages$\CustomSettings_Reference). Następnie należy dodać **DoCapture** i **EventService** właściwości i wartości odpowiadające CustomSettings.ini pliku tak, aby proces wdrożenia zestawu MDT przechwycenie (komputer odniesienia WDG-REF-01) po wdrożeniu Windows 8.1.  

#### <a name="to-customize-the-mdt-configuration-files-for-the-reference-computer"></a>Aby dostosować pliki konfiguracyjne zestawu MDT dla komputera odniesienia

1.  W Eksploratorze Windows przejdź do E:\Packages$\CustomSettings_Reference, a następnie kliknij dwukrotnie **CustomSettings.ini**.  

2.  Otwórz program Microsoft Notepad, a następnie dodaj następujące wiersze na końcu pliku CustomSettings.ini:

    ```  
    DoCapture=YES  
    EventService=http://WDG-MDT-01:9800  
    ```  

    Przykład pliku CustomSettings.ini po dodaniu właściwości DoCapture:

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

3.  W programie Notatnik Zapisz plik, a następnie Zakończ działanie Notatnika.  

###  <a name="UpdateDistroPoint"></a>Krok 3 – 6. Aktualizuj punkty dystrybucji dla pakietu plików ustawień niestandardowych  
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

###  <a name="CustomizeTaskSequence"></a>Krok 3 do 7. Dostosowywanie sekwencji zadań dla komputera odniesienia  
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

-   Dodawanie do bazy danych lokacji programu Configuration Manager na komputerze odniesienia, zgodnie z opisem w [krok 4-1: Dodaj komputer odniesienia do bazy danych lokacji programu Configuration Manager](#AddRefComptoConfigDB)  

-   Tworzenie kolekcji, która zawiera komputer odniesienia dodaną zgodnie z opisem w [krok 4-2: Utwórz kolekcję, która zawiera komputer odniesienia](#CreateCollectionContainRefComp)  

-   Wdrożenie sekwencji zadań komputera odniesienia, zgodnie z opisem w [kroku nr 3, 4: Wdrożenie sekwencji zadań komputera odniesienia](#DeployRefCompTaskSeq)  

-   Za pomocą Kreatora nośnika sekwencji zadań do utworzenia nośnika rozruchowego na dysku zgodnie z opisem w sekwencji zadań [krok 4-4: Tworzenie nośnika rozruchowego sekwencji zadań](#CreateTaskSeqBootMedia)  

-   Uruchamianie na komputerze odniesienia z nośnika rozruchowego na dysku zgodnie z opisem w sekwencji zadań [krok 4-5: Uruchom komputer odniesienia z nośnika rozruchowego sekwencji zadań](#StartRefCompwithTaskSeqBootMedia)  

###  <a name="AddRefComptoConfigDB"></a>Krok 4-1. Dodaj komputer odniesienia do bazy danych lokacji programu Configuration Manager  
 Aby wdrożyć system operacyjny bez nośnika autonomicznego na nowy komputer, który nie zarządza aktualnie programu Configuration Manager, należy dodać nowy komputer do bazy danych lokacji programu Configuration Manager przed zainicjowaniem procesu wdrażania systemu operacyjnego. Configuration Manager może automatycznie odnajdować komputery w sieci, które mają zainstalowany; systemu operacyjnego Windows Jednak jeśli komputer bez zainstalowanego systemu operacyjnego, należy użyć Kreatora importowania informacji o komputerze do importowania informacji o nowym komputerze.  

#### <a name="to-add-the-reference-computer-to-the-configuration-manager-site-database"></a>Aby dodać komputer odniesienia do bazy danych lokacji programu Configuration Manager  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **zasoby i zgodność**.  

3.  W zasoby i zgodność obszaru roboczego, przejdź do przegląd/urządzeń.  

4.  Na wstążce na **Home** karcie **Utwórz** kliknij przycisk **importu informacji o komputerze**.  

     Uruchamia Kreatora importowania informacji o komputerze.  

5.  Ukończ Kreatora importowania informacji o komputerze, korzystając z poniższych informacji. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

  |**Na tej stronie kreatora**|**W tym**|  
  |-|-|  
  |**Wybierz źródło**|Kliknij przycisk **Importuj pojedynczy komputer**, a następnie kliknij przycisk **dalej**.|  
  |**Wybierz źródło: Pojedynczego komputera**|1.  W **nazwy komputera**, typ **WDG-REF-01**.<br />2.  W **adres MAC**, typ ***adres_MAC*** (gdzie *adres_MAC* jest adres media access control [MAC] sieci podstawowej karty sieciowej dla komputera odniesienia WDG-REF-01).<br />3.  Kliknij przycisk **Dalej**.|  
  |**Wybierz źródło: Podgląd danych**|Kliknij przycisk **Dalej**.|  
  |**Wybierz źródło: Wybierz kolekcję docelową**|Kliknij przycisk **Dalej**.|  
  |**Podsumowanie**|1.  Przejrzyj informacje w **szczegóły** pola, czy podane podczas wykonywania poprzednich stron kreatora.<br />2.  Kliknij przycisk **Dalej**.|  
  |**Postęp**|Postęp importowania komputera jest wyświetlana.|  
  |**Potwierdzenie**|Kliknij przycisk **Zamknij**.|  

 Aby uzyskać więcej informacji na temat dodawania nowego komputera do bazy danych lokacji programu Configuration Manager zobacz sekcję "Aby zaimportować informacje dotyczące jednego komputera," w sekcji "Jak do wdrażania systemów operacyjnych w programie Configuration Manager" w konfiguracji Biblioteka dokumentacji Manager instalowanych z programem Configuration Manager.  

###  <a name="CreateCollectionContainRefComp"></a>Krok 4-2. Utwórz kolekcję, która zawiera komputer odniesienia  
 W konsoli programu Configuration Manager utwórz kolekcję, która zawiera komputer odniesienia (WDG-REF-01). Ta kolekcja komputera jest używany później podczas anonsowanie sekwencji zadań utworzony wcześniej w procesie.  

 **Aby utworzyć kolekcję, która zawiera komputer odniesienia**  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **zasoby i zgodność**.  

3.  W zasoby i zgodność obszaru roboczego, przejdź do kolekcji omówienie lub urządzeniu.  

4.  Na wstążce na **Home** karcie **Utwórz** kliknij przycisk **Utwórz**, a następnie kliknij przycisk Utwórz urządzenie **kolekcji**.  

     Uruchamia Kreatora tworzenia kolekcji urządzeń.  

5.  Ukończ Kreatora tworzenia kolekcji urządzeń korzystając z poniższych informacji. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    |**Na tej stronie kreatora**|**W tym**|  
    |-|-|  
    |**Ogólne**|<ol><li>W **nazwa**, typ **Microsoft, Deployment — komputer odniesienia**.</li><li>W **komentarz**, typ **komputera, który ma być komputer odniesienia dla komputerów docelowych, które mają zostać wdrożone**.</li><li>W **ograniczone kolekcji**, kliknij przycisk **Przeglądaj**.<br /><br />     **Wybieranie kolekcji** zostanie wyświetlone okno dialogowe. Wypełnij okno dialogowe, wykonując następujące czynności:<br /><br /> <ol><li>W **nazwa**, kliknij przycisk **wszystkie systemy**.</li><li>Kliknij przycisk **OK**.</li></ol></li><li>Kliknij przycisk **Dalej**.</li></ol>|  
    |**Reguły członkostwa**|<ol><li>Kliknij przycisk **Dodaj regułę**, a następnie kliknij przycisk **reguły bezpośredniej**.<br /><br />     Uruchamia Kreatora tworzenia reguły członkostwa bezpośredniego.</li><li>Wykonaj Kreatora tworzenia reguły członkostwa bezpośredniego, wykonując następujące czynności:<br /><br /> <ol><li>Na stronie **Zapraszamy** kliknij przycisk **Dalej**.</li><li>Na **wyszukiwanie zasobów** strony w **klasy zasobów**, wybierz pozycję **zasób systemowy**; na liście **nazwa atrybutu**, wybierz pozycję  **Nazwa**; na liście **wartość**, typ **WDG-REF-01**; a następnie kliknij przycisk **dalej**.</li><li>Na **zasobów wybierz** wybierz **WDG-REF-01**, a następnie kliknij przycisk **dalej**.</li><li>Na **Podsumowanie** kliknij przycisk **dalej**.</li><li>Na **postępu** Wyświetl postęp do tworzenia nowej reguły członkostwa.</li><li>Na **zakończenia** kliknij przycisk **Zamknij**.</li></ol></li><li>Kliknij przycisk **Dalej**.</li></ol>|  
    |**Podsumowanie**|1.  Przejrzyj informacje w **szczegóły** pola, czy podane podczas wykonywania poprzednich stron kreatora.<br />2.  Kliknij przycisk **Dalej**.|  
    |**Postęp**|Zostanie wyświetlony pasek postępu tworzenia kolekcji urządzeń.|  
    |**Zakończenie**|Kliknij przycisk **Zamknij**.|  

 Aby uzyskać więcej informacji zobacz sekcję "Jak Aby utworzyć kolekcje w programie Configuration Manager" w bibliotece dokumentacji, która jest instalowana z programem Configuration Manager programu Configuration manager.  

###  <a name="DeployRefCompTaskSeq"></a>Krok 4: 3. Wdrożenie sekwencji zadań komputera odniesienia  
 W konsoli programu Configuration Manager należy wdrożyć sekwencję zadań, utworzony wcześniej w procesie do kolekcji urządzeń, która zawiera komputer odniesienia utworzony wcześniej w procesie.  

#### <a name="to-deploy-the-task-sequence"></a>Aby wdrożyć sekwencję zadań
1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **Biblioteka oprogramowania**.  

3.  W obszarze roboczym Biblioteka oprogramowania przejdź do Przegląd/operacyjnego systemów lub zadanie sekwencji.  

4.  W okienku podglądu kliknij **Windows 8.1 odwołanie wdrożenia**.  

5.  Na wstążce na **Home** karcie **wdrożenia** kliknij przycisk **Wdróż**.  

     Uruchamia Kreatora wdrażania oprogramowania.  

6.  Ukończ Kreatora wdrażania oprogramowania korzystając z poniższych informacji. Zaakceptuj wartości domyślne, chyba że określono inaczej.

    |**Na tej stronie kreatora**|**W tym**|  
    |-|-|  
    |**Ogólne**|1.  W **kolekcji**, kliknij przycisk **Przeglądaj**.<br />2.  W **Przeglądaj kolekcji** okno dialogowe, kliknij przycisk **Microsoft, Deployment — komputer odniesienia**, a następnie kliknij przycisk **OK**.<br />3.  W **komentarz**, typ **wdrażanie Windows 8.1 do komputera odniesienia, a następnie przechwytywania obrazu komputera odniesienia**.<br />4.  Kliknij przycisk **Dalej**.|  
    |**Ustawienia wdrożenia**|1.  W **celu**, wybierz pozycję **dostępne**.<br />2.  Wybierz **Udostępnij nośnikom rozruchowym i środowisku PXE** pole wyboru.<br />3.  Kliknij przycisk **Dalej**.|  
    |**Ustawienia wdrożenia: Harmonogram**|Kliknij przycisk **Dalej**.|  
    |**Ustawienia wdrożenia: Środowisko użytkownika**|Kliknij przycisk **Dalej**.|  
    |**Ustawienia wdrożenia: Alerty**|Kliknij przycisk **Dalej**.|  
    |**Ustawienia wdrożenia: Punkty dystrybucji**|Kliknij przycisk **Dalej**.|  
    |**Podsumowanie**|1.  Przejrzyj informacje w **szczegóły** pola, czy podane podczas wykonywania poprzednich stron kreatora.<br />2.  Kliknij przycisk **Dalej**.|  
    |**Postęp**|Zostanie wyświetlony pasek postępu wdrażania sekwencji zadań.|  
    |**Zakończenie**|Kliknij przycisk **Zamknij**.|  

 Aby uzyskać więcej informacji zobacz sekcję "Jak do wdrażania sekwencji zadań," w bibliotece dokumentacji, która jest instalowana z programem Configuration Manager programu Configuration manager.  

###  <a name="CreateTaskSeqBootMedia"></a>Krok 4-4. Tworzenie nośnika rozruchowego sekwencji zadań  
 Aby zainicjować proces zestawu MDT, udostępnia metody uruchamiania komputera za pomocą środowiska Windows PE i niezbędne oprogramowania przez utworzenie dysku rozruchowego nośnika sekwencji zadań. Użyj Kreatora nośnika sekwencji zadań w konsoli programu Configuration Manager do tworzenia nośnika rozruchowego dla magazynu na dysku flash USB, dysk CD lub DVD.  

#### <a name="to-create-a-task-sequence-bootable-media-disk"></a>Aby utworzyć dysk nośnika rozruchowego sekwencji zadań  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż pozycję Microsoft System Center 2012. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **Biblioteka oprogramowania**.  

3.  W obszarze roboczym Biblioteka oprogramowania przejdź do Przegląd/operacyjnego systemów lub zadanie sekwencji.  

4.  Na wstążce na **Home** karcie **Utwórz** kliknij przycisk **tworzenia nośnika sekwencji zadań**.  

     Uruchamia Kreatora tworzenia nośnika sekwencji zadań.  

5.  Wykonaj zadania Kreatora tworzenia nośnika sekwencji korzystając z poniższych informacji. Zaakceptuj wartości domyślne, chyba że określono inaczej.

    |**Na tej stronie kreatora**|**W tym**|  
    |-|-|  
    |**Wybierz typ nośnika**|1.  Kliknij przycisk **nośnika rozruchowego**.<br />2.  Wyczyść **Zezwalaj na nienadzorowane wdrożenie systemu operacyjnego** pole wyboru.<br />3.  Kliknij przycisk **Dalej**.|  
    |**Wybierz typ nośnika: Zarządzanie nośnikiem**|Kliknij przycisk **nośnik oparty na lokacji**, a następnie kliknij przycisk **dalej**.|  
    |**Wybierz typ nośnika: Typ nośnika**|W **pliku multimedialnego**, typ  **\\\WDG-MDT-01\Capture$\CM2012_TS_Boot_Media.iso**, a następnie kliknij przycisk **dalej**.|  
    |**Wybierz typ nośnika: Zabezpieczeń**|W **hasło** i **Potwierdź hasło**, typ  **P@ssw0rd** , a następnie kliknij przycisk **dalej**.|  
    |**Wybierz typ nośnika: Obraz rozruchowy**|1.  W **obrazu rozruchowego**, kliknij przycisk **Przeglądaj**.<br />2.  W **wybierz obraz rozruchowy** okno dialogowe, kliknij przycisk **niestandardowych systemu Windows PE**, a następnie kliknij przycisk **OK**.<br />3.  W **punktu dystrybucji**, kliknij przycisk  **\\\WDG-MDT-01.mdt2013.corp.woodgrovebank.com**, a następnie kliknij przycisk **OK**.<br />4.  W **punkt zarządzania**, kliknij przycisk  **\\\WDG-MDT-01.mdt2013.corp.woodgrovebank.com**, a następnie kliknij przycisk **OK**.<br />5.  Kliknij przycisk **Dalej**.|  
    |**Wybierz typ nośnika: Dostosowywanie**|Kliknij przycisk **Dalej**.|  
    |**Podsumowanie**|1.  Przejrzyj informacje w **szczegóły** pola, czy podane podczas wykonywania poprzednich stron kreatora.<br />2.  Kliknij przycisk **Dalej**.|  
    |**Postęp**|Zostanie wyświetlony pasek postępu tworzenia nośnika sekwencji zadań.|  
    |**Zakończenie**|Kliknij przycisk **Zamknij**.|  

    Kreator tworzy plik CM2012_TS_Boot_Media.iso w folderze udostępnionym $ WDG — MDT-01Capture.  

6.  WDG-REF-01 w przypadku komputera fizycznego, Utwórz dysk CD lub DVD Międzynarodowej Organizacji Normalizacyjnej (ISO) pliku. WDG-REF-01 w przypadku maszyny Wirtualnej, należy uruchomić maszyny Wirtualnej bezpośrednio z pliku ISO.  

 Aby uzyskać więcej informacji na temat tworzenia dysku rozruchowego nośnika sekwencji zadań zobacz sekcję "Jak do tworzenia nośnika rozruchowego," w bibliotece dokumentacji, która jest instalowana z programem Configuration Manager programu Configuration manager.  

###  <a name="StartRefCompwithTaskSeqBootMedia"></a>Krok 4 – 5. Uruchom komputer odniesienia z nośnika rozruchowego sekwencji zadań  
 Uruchom komputer odniesienia (WDG-REF-01) przy użyciu utworzony wcześniej w procesie dysk nośnika rozruchowego sekwencji zadań. Ten nośnik uruchamia środowisko Windows PE na komputerze odniesienia i inicjuje proces zestawu MDT. Na końcu procesu zestawu MDT Windows 8.1 jest wdrażany na komputerze odniesienia i zapisaniu obrazu komputera odniesienia do \WDG-MDT-01\Capture$\WDG-REF-01.wim.  

> [!NOTE]   
>  Można także zainicjować proces zestawu MDT, uruchamiając na komputerze docelowym za pomocą usług wdrażania systemu Windows.  

#### <a name="to-start-the-reference-computer-with-the-task-sequence-bootable-media"></a>Aby uruchomić komputer odniesienia z nośnika rozruchowego sekwencji zadań

1.  Uruchom WDG-REF-01 z nośnika rozruchowego sekwencji zadań, utworzony wcześniej w procesie.  

     Uruchamia środowisko Windows PE, a następnie uruchamia Kreatora sekwencji zadań.  

2.  Ukończ pracę Kreatora sekwencji zadań, korzystając z poniższych informacji. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    |**Na tej stronie kreatora**|**W tym**|  
    |-|-|  
    |**Witamy w Kreatorze sekwencji zadań**|W **hasło**, typ  **P@ssw0rd** , a następnie kliknij przycisk **dalej**.|  
    |**Wybierz sekwencję zadań**|W polu listy, wybierz **Windows 8.1 odwołanie wdrożenia**, a następnie kliknij przycisk **dalej**.|  

#### <a name="to-monitor-the-reference-computer-deployment-process-using-the-deployment-workbench-complete-the-following-steps-on-wdg-mdt-01"></a>Aby monitorować proces wdrażania komputera odniesienia przy użyciu konsoli Deployment Workbench, wykonaj następujące czynności na WDG-MDT-01

1.  Na WDG-MDT-01, kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench przejdź do wdrożenia środowiska roboczego/wdrożenia udziałów/udział wdrożenia zestawu MDT (C:\DeploymentShare$)/Monitoring.  

3.  W okienku szczegółów wyświetlić proces wdrażania **WDG-REF-01**.  

4.  W okienku Akcje kliknij okresowo **Odśwież**.  

     Stan procesu wdrażania jest aktualizowana w okienku szczegółów. Nadal monitorować proces wdrażania, aż do ukończenia procesu.  

5.  W okienku szczegółów kliknij **WDG-REF-01**.  

6.  W okienku Akcje kliknij polecenie **właściwości**.  

     **Właściwości WDG-REF-01** zostanie wyświetlone okno dialogowe.  

7.  W **właściwości WDG-REF-01** na okna dialogowego **tożsamości** pozycję Wyświetl monitorowania dostarczone informacje na temat procesu wdrażania w następujący sposób:

    |**Informacje**|**Opis**|  
    |-|-|  
    |**IDENTYFIKATOR**|Unikatowy identyfikator dla komputera wdrażany.|  
    |**Nazwa komputera**|Nazwa komputera jest wdrożony.|  
    |**Stan wdrożenia**|Bieżący stan komputera wdrożony; Stan może być jedną z następujących czynności:<br /><br /> -   **Uruchomiona**. Sekwencja zadań jest dobra i uruchomiona.<br />-   **Nie powiodło się**. Sekwencja zadań nie powiodło się, a proces wdrażania nie powiodło się.<br />-   **Ukończono**. Sekwencja zadań została ukończona.<br />-   **Odpowiadać**. Sekwencja zadań jego stan nie został zaktualizowany w ciągu ostatnich czterech godzin i zostanie uznany za nieodpowiadający.|  
    |**Krok**|Bieżącego kroku sekwencji zadań uruchamiana.|  
    |**Postęp**|Ogólny postęp sekwencji zadań. Pasek postępu wskazuje, ile kroków sekwencji zadań zostały uruchomione poza całkowita liczba kroków sekwencji zadań.|  
    |**Początek**|Czas rozpoczęcia procesu wdrażania.|  
    |**Koniec**|Czas zakończenia procesu wdrażania.|  
    |**Który upłynął**|Czas procesu wdrażania była uruchomiona lub trwało do uruchomienia, jeśli zakończenie procesu wdrażania.|  
    |**Błędy**|Liczba błędów napotkanych podczas procesu wdrażania.|  
    |**Ostrzeżenia**|Liczba ostrzeżeń podczas procesu wdrażania.|  
    |**Pulpit zdalny**|Ten przycisk służy do ustanawiania połączenia pulpitu zdalnego z komputerem wdrażany przy użyciu funkcji pulpitu zdalnego systemu Windows. Ta metoda zakłada się, że:<br /><br /> -Docelowy system operacyjny jest uruchomiony i ma włączoną obsługę usług pulpitu zdalnego<br />-   **mstsc.exe** znajduje się w ścieżce **Uwaga:**  Ten przycisk jest zawsze widoczne, ale nie można ustanowić sesji usług pulpitu zdalnego Jeśli monitorowanym komputerze środowiska Preinstalacyjnego systemu Windows, instalacja docelowego systemu operacyjnego nie zostało zakończone lub nie ma włączenie tej funkcji pulpitu zdalnego.|  
    |**Połączenie maszyn wirtualnych**|Ten przycisk służy do ustanowienia połączenia pulpitu zdalnego z maszyną wirtualną w HyperV®. Ta metoda zakłada się, że:<br /><br /> -Wdrożenie jest wykonywane do maszyny Wirtualnej z systemem w funkcji Hyper-V<br />-   **vmconnect.exe** znajduje się w folderze %ProgramFiles%\Hyper-V **Uwaga:**  Ten przycisk jest wyświetlany, gdy ZTIGather.wsf wykryje, że składniki integracji funkcji Hyper-V są uruchomione na monitorowanym komputerze. W przeciwnym razie ten przycisk, nie będą widoczne.|  
    |**DaRT zdalnego sterowania**|Ten przycisk pozwala ustanowić sesję zdalnego sterowania należy użyć funkcji Podgląd zdalnego w Diagnostics and Recovery Toolkit (DaRT).<br /><br /> Ta metoda zakłada się, że:<br /><br /> -DaRT został wdrożony na komputerze docelowym i jest aktualnie uruchomiona<br />-   **DartRemoteViewer.exe** znajduje się w folderze %ProgramFiles%\Microsoft DaRT 7\v7 **Uwaga:**  Ten przycisk jest wyświetlany, gdy ZTIGather.wsf wykryje, że DaRT jest uruchomiony na monitorowanym komputerze. W przeciwnym razie ten przycisk, nie będą widoczne.|  
    |**Automatyczne odświeżanie te informacje co 10 sekund**|Pole wyboru, która kontroluje, czy informacje w oknie dialogowym są odświeżane automatycznie. Jeśli pole wyboru jest:<br /><br /> -Zaznaczone, dane są odświeżane co 10 sekund<br />-Wyczyszczone, nie jest automatycznie odświeżany informacje i musi być odświeżane ręcznie przy użyciu **Odśwież teraz** przycisku|  
    |**Odśwież teraz**|Ten przycisk natychmiast odświeża informacje wyświetlane w oknie dialogowym.|  

8.  W **właściwości WDG-REF-01** okno dialogowe, kliknij przycisk **OK**.  

9. Zamknięcie konsoli Deployment Workbench.  

#### <a name="to-monitor-the-reference-computer-deployment-process-using-the-get-mdtmonitordata-cmdlet-complete-the-following-steps-on-wdg-mdt-01"></a>Aby monitorować proces wdrażania komputera odniesienia przy użyciu polecenia cmdlet Get-MDTMonitorData, wykonaj następujące czynności na WDG-MDT-01

1.  Na WDG-MDT-01, kliknij przycisk **Start**, następnie kliknij pozycję **narzędzia administracyjne**, a następnie kliknij przycisk **moduły programu Windows PowerShell**.  

     Zostanie otwarty wiersz polecenia moduły programu Windows PowerShell.  

2.  Utwórz dysk programu PowerShell, który używa dostawcy programu PowerShell zestawu MDT, uruchamiając [elementu PSDrive nowy](http://technet.microsoft.com/library/hh849829.aspx) polecenia cmdlet, jak pokazano w poniższym przykładzie:  

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

-   Importowanie pliku wim, przechwycone w poprzednim kroku do programu Configuration Manager za pomocą Kreatora dodawania obrazu systemu operacyjnego, zgodnie z opisem w [krok 5-1: Zaimportuj plik wim przechwyconych do programu Configuration Manager](#ImportCapturedwimFile)  

-   Za pomocą Kreatora tworzenia sekwencji zadań zestawu MDT, aby utworzyć szablon sekwencji zadań zestawu MDT do wdrażania przechwyconego obrazu komputera odniesienia do komputera docelowego, zgodnie z opisem w [krok 5-2: Utwórz sekwencję zadań zestawu MDT do wdrażania przechwyconego obrazu](#CreateMDTTaskSeqDeployCapturedImage)  

-   Wybieranie punktów dystrybucji dla nowych pakietów i obrazów, które tworzy Kreatora tworzenia sekwencji zadań zestawu MDT, zgodnie z opisem w [krok 5-3: Wybierz punkty dystrybucji dla nowych pakietów i obrazów](#SelectDistroPointsNewPackagesImages)  

-   Dostosowywanie pliki konfiguracyjne zestawu MDT dla komputera docelowego — w szczególności pliku CustomSettings.ini — zgodnie z opisem w [krok 5 — 4: Dostosowywanie pliki konfiguracyjne zestawu MDT](#CustomizetheMDTConfigFiles)  

-   Aktualizowanie punkty dystrybucji programu Configuration Manager dla pakietu ustawienia niestandardowe, zgodnie z opisem w [krok 5-5: Aktualizuj punkty dystrybucji dla pakietu ustawienia niestandardowe](#UpdateDistroPointsforCustomSettings)  

-   Dostosowywanie sekwencji zadań dla komputera docelowego, zgodnie z opisem w [krok 5 — 6: Dostosowywanie sekwencji zadań dla komputera docelowego](#CustomizeTaskSequenceTargetComputer)  

###  <a name="ImportCapturedwimFile"></a>Krok 5-1. Zaimportuj plik wim przechwyconych do programu Configuration Manager  
 Przechwycony obraz komputera odniesienia (WDG-REF-01) w pliku wim, należy zaimportować plik wim przechwyconych do programu Configuration Manager. Zaimportuj plik wim przechwyconych do węzła obrazy systemu operacyjnego przy użyciu Kreatora dodawania obrazu systemu operacyjnego.  

 Przechwycony wim zawiera dwa obrazy, jeden dla każdej partycji na komputerze odniesienia. Identyfikowanie obrazów mającego przechwycony system operacyjny Windows 8.1, sprawdzając zawierający opis obrazu *Windows 8.1*. Indeks obrazu będzie używany podczas tworzenia sekwencji zadań do wdrażania przechwyconego obrazu na komputerze docelowym.  

 **Aby zaimportować plik wim przechwyconych do programu Configuration Manager**  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **Biblioteka oprogramowania**.  

3.  W obszarze roboczym Biblioteka oprogramowania przejdź do obrazów systemu operacyjnego/systemów Przegląd/operacyjnych.  

4.  Na Wstążce w **Utwórz** kliknij przycisk **Dodaj obraz systemu operacyjnego**.  

     Zostanie uruchomiony Kreator dodawania obrazu systemu operacyjnego.  

5.  Ukończ korzystając z poniższych informacji Kreatora dodawania obrazu systemu operacyjnego. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    |**Na tej stronie kreatora**|**W tym**|  
    |-|-|  
    |**Na tej stronie kreatora**|**W tym**|  
    |**Źródło danych**|W **ścieżki**, typ  **\\\WDG-MDT-01\Capture$\WDG-REF-01.wim**, a następnie kliknij przycisk **dalej**.|  
    |**Ogólne**|1.  W **nazwa**, typ **obraz odniesienia Windows 8.1**.<br /><br /> 1.  W **wersji**, typ **1,00**.<br /><br /> 1.  W **komentarze**, typ **Windows 8.1 przechwycony obraz komputera odniesienia (WDG-REF-01) używane do wdrażania na komputerach docelowych**, a następnie kliknij przycisk **dalej**.|  
    |**Podsumowanie**|1.  Przejrzyj informacje w **szczegóły** pola, czy podane podczas wykonywania poprzednich stron kreatora.<br />2.  Kliknij przycisk **Dalej**.|  
    |**Postęp**|Zostanie wyświetlony pasek postępu do importowania obrazu systemu operacyjnego.|  
    |**Zakończenie**|Kliknij przycisk **Zamknij**.|  

6.  W okienku podglądu kliknij **obraz odniesienia Windows 8.1**.  

7.  W okienku podglądu kliknij **szczegóły** kartę.  

     Zostanie wyświetlona lista przechwytywane wim partycji systemu operacyjnego. Indeks obrazu, który zawiera Windows 8.1 jest indeks obrazu, który będzie określać później w kreatorze tworzenia sekwencji zadań zestawu MDT.  

8.  Zanotuj indeks obrazu, który zawiera Windows 8.1.  

    > [!TIP]    
    >  Na potrzeby tego przykładu indeks obrazu 2 powinny mieć system operacyjny Windows 8.1.  

###  <a name="CreateMDTTaskSeqDeployCapturedImage"></a>Krok 5-2. Utwórz sekwencję zadań zestawu MDT do wdrażania przechwyconego obrazu  
 Po przechwyceniu obrazu, należy utworzyć sekwencję zadań do wdrażania przechwyconego obrazu komputera odniesienia (WDG-REF-01) do komputera docelowego (WDG-CLI-01). Większość pakietów potrzebne do tej sekwencji zadań zostały utworzone wcześniej w procesie. Jednak należy utworzyć nowy pakiet zestawu MDT niestandardowych ustawień ma prawidłowe ustawienia konfiguracji dla komputera docelowego, który tworzy obraz systemu operacyjnego przechwycony obraz komputera odniesienia.  

#### <a name="to-create-a-task-sequence-template-to-deploy-the-captured-image-to-the-target-computer"></a>Aby utworzyć szablon sekwencji zadań do wdrażania przechwyconego obrazu na komputerze docelowym  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **Biblioteka oprogramowania**.  

3.  W obszarze roboczym Biblioteka oprogramowania przejdź do Przegląd/operacyjnego systemów lub zadanie sekwencji.  

4.  Na wstążce na **Home** karcie **sekwencje zadań** kliknij przycisk **Utwórz sekwencję zadań zestawu MDT**.  

     Uruchamia Kreatora tworzenia sekwencji zadań zestawu MDT.  

5.  Ukończ MDT Kreatora tworzenia sekwencji zadań korzystając z poniższych informacji. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    |**Na tej stronie kreatora**|**W tym**|  
    |-|-|  
    |**Wybieranie szablonu**|Wybierz **sekwencję zadań klienta**, a następnie kliknij przycisk **dalej**.|  
    |**Wybierz szablon: Ogólne**|1.  W **nazwę sekwencji zadań**, typ **wdrożenia docelowego Windows 8.1**.<br />2.  W **komentarze sekwencji zadań**, typ **sekwencję zadań pod kątem wdrażania przechwycony obraz komputera odniesienia na komputerze docelowym (WDG-CLI-01)**, a następnie kliknij przycisk **dalej**.|  
    |**Wybierz szablon: Szczegóły**|<ol><li>Kliknij przycisk **Przyłącz do domeny**.</li><li>W **domeny**, typ **mdt2013.corp.woodgrovebank.com**.</li><li>W **konta**, kliknij przycisk **ustawić**, a następnie ukończ **konta użytkownika systemu Windows** okno dialogowe, wykonując następujące czynności:<br /><br /> <ol><li>W **nazwy użytkownika**, typ **MDT2013\Administrator**.</li><li>W **hasło** i **Potwierdź hasło**, typ  **P@ssw0rd** .</li><li>Kliknij przycisk **OK**.</li></ol></li><li>W **nazwy użytkownika**, typ **pracownika banku Woodgrove**.</li><li>W **nazwa organizacji**, typ **banku Woodgrove**.</li><li>W **klucz produktu**, typ ***klucz_produktu*** (gdzie *klucz_produktu* jest klucz produktu dla Windows 8.1).</li><li>Kliknij przycisk **Dalej**.</li></ol>|  
    |**Wybierz szablon: Przechwyć ustawienia**|Kliknij przycisk **Dalej**.|  
    |**Obraz rozruchowy**|1.  W **Określ istniejący pakiet obrazów rozruchowych**, kliknij przycisk **Przeglądaj**.<br />2.  W **wybierz pakiet** okno dialogowe, kliknij przycisk **niestandardowych systemu Windows PE**, a następnie kliknij przycisk **OK**.<br />3.  Kliknij przycisk **Dalej**.|  
    |**Pakiet zestawu MDT**|1.  W **Określ istniejący pakiet plików zestawu narzędzi wdrażania Microsoft**, kliknij przycisk **Przeglądaj**.<br />2.  W **wybierz pakiet** okno dialogowe, kliknij przycisk **pliki zestawu MDT**, a następnie kliknij przycisk **OK**.<br />3.  Kliknij przycisk **Dalej**.|  
    |**Obraz systemu operacyjnego**|1.  Kliknij przycisk **Określ istniejącego systemu operacyjnego obrazu**.<br />2.  W **Określ istniejącego systemu operacyjnego obrazu**, kliknij przycisk **Przeglądaj**.<br />3.  W **wybierz pakiet** okno dialogowe, kliknij przycisk **obraz odniesienia Windows 8.1**, a następnie kliknij przycisk **OK**.<br />4.  Kliknij przycisk **Dalej**.|  
    |**Obraz systemu operacyjnego: Indeks obrazu systemu operacyjnego**|1.  W **pliku obrazu (WIM) wybranego systemu operacyjnego zawiera wiele obrazów**. **Określ obraz, który chcesz wdrożyć**, wybierz pozycję ***indeks obrazu*** (gdzie *indeks obrazu* jest indeks obrazu obrazu, który zawiera Windows 8.1, który został zidentyfikowany w sekcji [Krok 5-1: Importuj wim Captured pliku do programu Configuration Manager](#ImportCapturedwimFile); na potrzeby tego przewodnika, wybierz opcję **2**).<br />2.  Kliknij przycisk **Dalej**.|  
    |**Metody wdrażania**|Kliknij przycisk **Dalej**.|  
    |**Pakiet klienta**|1.  W **Określ istniejący pakiet klienta programu ConfigMgr**, kliknij przycisk **Przeglądaj**.<br />2.  W **wybierz pakiet** okno dialogowe, kliknij przycisk **uaktualniania klienta programu Microsoft Configuration Manager**, a następnie kliknij przycisk **OK**.<br />3.  Kliknij przycisk **Dalej**.|  
    |**Pakiet USMT**|1.  W **Określ istniejący pakiet narzędzia USMT**, kliknij przycisk **Przeglądaj**.<br />2.  W **wybierz pakiet** okno dialogowe, kliknij przycisk **USMT**, a następnie kliknij przycisk **OK**.<br />3.  Kliknij przycisk **Dalej**.|  
    |**Ustawienia pakietu**|1.  Kliknij przycisk **utworzyć nowy pakiet ustawienia**.<br />2.  W **folderu źródłowego pakietu należy utworzyć**, typ  **\\\WDG-MDT-01\Packages$\CustomSettings_Target**, a następnie kliknij przycisk **dalej**.|  
    |**Pakiet ustawień: Szczegóły ustawień**|1.  W **nazwa**, typ **ustawienia niestandardowe komputera docelowego zestawu MDT**.<br />2.  W **wersji**, typ **1,00**.<br />3.  W **komentarze**, typ **ustawienia konfiguracji dla zestawu MDT procesu wdrażania (na przykład CustomSettings.ini) dla komputera docelowego**, a następnie kliknij przycisk **dalej**.|  
    |**Pakiet programu Sysprep**|Kliknij przycisk **Dalej**.|  
    |**Podsumowanie**|1.  Przejrzyj informacje w **szczegóły** pola, czy podane podczas wykonywania poprzednich stron kreatora.<br />2.  Kliknij przycisk **Dalej**.|  
    |**Postęp**|Zostanie wyświetlony pasek postępu tworzenia sekwencji zadań.|  
    |**Potwierdzenie**|Kliknij przycisk **Zakończ**.|  

 Zostanie wyświetlona lista sekwencji zadań. Sekwencja zadań właśnie utworzony (Windows 8.1 docelowych wdrożenia) znajduje się na liście sekwencji zadań.  

###  <a name="SelectDistroPointsNewPackagesImages"></a>Krok 5-3. Wybierz punkty dystrybucji dla nowych pakietów i obrazów  
 Kreatora tworzenia sekwencji zadań zestawu MDT tworzy pakietów i obrazów. Po utworzeniu te pakiety i obrazów, wybierz punkty dystrybucji, z których pakietów i obrazy będą kopiowane i dostępne dla komputerów docelowych.  

> [!NOTE]
>  W tym przykładzie istnieje tylko jeden punkt dystrybucji (WDG-MDT-01). Jednak większość sieci produkcyjnej ma wiele punktów dystrybucji. Podczas wykonywania tego kroku w środowisku produkcyjnym, wybierz odpowiednie punkty dystrybucji w sieci.  

#### <a name="to-select-the-distribution-points-for-software-distribution-packages"></a>Aby wybrać punkty dystrybucji dla pakietów dystrybucji oprogramowania  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **Biblioteka oprogramowania**.  

3.  W obszarze roboczym Biblioteka oprogramowania przejdź do Przegląd/operacyjnego systemów lub zadanie sekwencji.  

4.  W okienku podglądu wybierz **wdrożenia docelowego Windows 8.1**.  

5.  Na wstążce na **Home** karcie **wdrożenia** kliknij przycisk **Dystrybuuj zawartość**.  

     Uruchamia Kreatora dystrybucji zawartości.  

6.  Ukończ Kreatora dystrybucji zawartości korzystając z poniższych informacji. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    |**Na tej stronie kreatora**|**W tym**|  
    |-|-|  
    |**Ogólne**|Kliknij przycisk **Dalej**.|  
    |**Zawartość**|Kliknij przycisk **Dalej**.|  
    |**Ogólne: Zawartość**|Kliknij przycisk **Dalej**.|  
    |**Ogólne: Miejsce docelowe zawartości**|1.  Kliknij przycisk **Dodaj**, a następnie kliknij przycisk **punktu dystrybucji**.<br />     **Punktów dystrybucji Dodaj** zostanie wyświetlone okno dialogowe.<br />2.  W **punktów dystrybucji Dodaj** okno dialogowe, wybierz opcję  **\\\WDGMDT01.mdt2013.corp.woodgrovebank.com**, a następnie kliknij przycisk **OK**.<br />     \\\WDGMDT01.mdt2013.corp.woodgrovebank.com pojawia się w **miejsce docelowe zawartości** listy.<br />3.  Kliknij przycisk **Dalej**.|  
    |**Podsumowanie**|1.  Przejrzyj informacje w **szczegóły** pola, czy podane podczas wykonywania poprzednich stron kreatora.<br />2.  Kliknij przycisk **Dalej**.|  
    |**Postęp**|Zostanie wyświetlony pasek postępu do dystrybucji oprogramowania.|  
    |**Zakończenie**|Kliknij przycisk **Zamknij**.|  

7.  Zamknij wszystkie otwarte okna i oknach dialogowych.  

###  <a name="CustomizetheMDTConfigFiles"></a>Krok 5 — 4: Dostosowywanie pliki konfiguracyjne zestawu MDT  
 Jeśli sekwencja zadań został utworzony na komputerze docelowym, dostosować pliki konfiguracyjne zestawu MDT, które zapewniają ustawienia konfiguracji wdrażania Windows 8.1 z komputerem docelowym — w szczególności CustomSettings.ini.  

 Po dostosowaniu pliku CustomSettings.ini, Zapisz zaktualizowane pliki do folderu źródłowego pakietu MDT niestandardowych ustawień utworzonego wcześniej w procesie (E:\Packages$\CustomSettings_Target).  

#### <a name="to-customize-the-mdt-configuration-files-for-the-target-computer"></a>Aby dostosować pliki konfiguracyjne zestawu MDT dla komputera docelowego  

1.  W Eksploratorze Windows przejdź do folderu E:\Packages$\CustomSettings_Target, a następnie kliknij dwukrotnie **CustomSettings.ini**.  

2.  Otwórz Notatnik, a następnie dodaj następujące wiersze do pliku CustomSettings.ini:  

    ```  
    EventService=http://WDG-MDT-01:9800  
    ```  

     To ustawienie służy do konfigurowania monitorowania wdrożenia komputera docelowego.  

    > [!NOTE]
    >  Wprowadź wszelkie zmiany, które są wymagane w danym środowisku.  

     **Przykład edytowanego pliku CustomSettings.ini:**  

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

###  <a name="UpdateDistroPointsforCustomSettings"></a>Krok 5-5. Aktualizuj punkty dystrybucji dla pakietu ustawienia niestandardowe  
 Po zaktualizowaniu folderu źródłowego pakietu ustawienia niestandardowe komputera docelowego zestawu MDT w programie Configuration Manager zaktualizować punkty dystrybucji dla pakietu ustawienia niestandardowe komputera docelowego zestawu MDT. Udziały wdrażania określony w pakiecie aktualizacji punktów dystrybucji kopiuje zaktualizowaną wersję pliku CustomSettings.ini.  

#### <a name="to-update-the-distribution-points-for-the-custom-settings-package"></a>Aby zaktualizować dystrybucji punkty pakietu niestandardowych ustawień  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **Biblioteka oprogramowania**.  

3.  W obszarze roboczym Biblioteka oprogramowania przejdź do aplikacji/Przegląd/pakiety zarządzania.  

4.  W okienku podglądu kliknij **ustawienia niestandardowe komputera docelowego zestawu MDT**.  

5.  Na wstążce na **Home** karcie **wdrożenia** kliknij przycisk **Aktualizuj punkty dystrybucji**.  

     **Programu Configuration Manager** zostanie otwarte okno dialogowe, informujący, że chcesz zaktualizować pakiet we wszystkich punktach dystrybucji.  

6.  W **programu Configuration Manager** okno dialogowe, kliknij przycisk **OK**.  

7.  Zamknij wszystkie otwarte okna i oknach dialogowych.  

###  <a name="CustomizeTaskSequenceTargetComputer"></a>Krok 5 — 6: Dostosowywanie sekwencji zadań dla komputera docelowego  
 Dla większości wdrożeń sekwencji zadań wdrożenia docelowego Windows 8.1 utworzony wcześniej w procesie wykonuje wszystkie niezbędne kroki bez żadnych modyfikacji. W tym przykładzie zmodyfikuj szablon sekwencji zadań, aby wprowadzić hasło do konta administratora lokalnego do żadnej znanej wartości. (Domyślnie sekwencja zadań ustawia hasło dla konta administratora lokalnego do losowych wartości.) Sekwencja zadań może wymagać dalszej dostosowania, w zależności od środowiska.  

#### <a name="to-customize-the-windows-81-target-deployment-task-sequence"></a>Aby dostosować sekwencja zadań wdrożenia docelowego Windows 8.1

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



## <a name="step-6-deploy-the-captured-image-of-the-reference-computer-to-the-target-computer"></a>Krok 6. Wdrażanie przechwycony obraz komputera odniesienia do komputera docelowego  
 Gdy przechwycony obraz komputera odniesienia i utworzyć i skonfigurować sekwencję zadań wdrażania przechwyconego obrazu. Skonfiguruj zestawu MDT, aby podać wszystkie ustawienia konfiguracji niezbędne do wdrożenia na komputerze docelowym. Po zainicjowaniu procesu wdrażania, obraz komputera odniesienia z systemem Windows 8.1 jest wdrażany na komputerze docelowym i automatycznie skonfigurowane ustawienia zdefiniowane.  

 Wdrażania przechwyconego obrazu przez:  

-   Dodawanie do bazy danych lokacji programu Configuration Manager na komputerze docelowym, zgodnie z opisem w [krok 6-1: Dodać komputer docelowy do bazy danych lokacji programu Configuration Manager](#AddTargetComptoConfigManager)  

-   Tworzenie kolekcji komputerów, która zawiera komputer docelowy zgodnie z opisem w [krok 6-2: Tworzenie kolekcji komputerów, która zawiera komputer docelowy](#CreateComputerCollectionIncludesTarget)  

-   Wdrażanie sekwencji zadań utworzony wcześniej w procesie, zgodnie z opisem w [kroku nr 3, 6: Wdrożenie sekwencji zadań komputera docelowego](#DeployTargetComputerTaskSequence)  

-   Uruchamianie komputera docelowego z nośnika rozruchowego sekwencji zadań, zgodnie z opisem w [krok 6-4: Uruchom komputer docelowy z nośnika rozruchowego sekwencji zadań](#StartTargetComputerTaskSequenceMedia)  

###  <a name="AddTargetComptoConfigManager"></a>Krok 6-1. Dodać komputer docelowy do bazy danych lokacji programu Configuration Manager  
 Aby wdrożyć system operacyjny bez nośnika autonomicznego na nowy komputer, który nie zarządza aktualnie programu Configuration Manager, należy dodać nowy komputer do bazy danych lokacji programu Configuration Manager przed zainicjowaniem procesu wdrażania systemu operacyjnego. Configuration Manager może automatycznie odnajdować komputery w sieci, które mają zainstalowany; systemu operacyjnego Windows Jednak jeśli komputer bez zainstalowanego systemu operacyjnego, należy użyć Kreatora importowania informacji o komputerze do importowania informacji o nowym komputerze.  

#### <a name="to-add-the-target-computer-to-the-configuration-manager-site-database"></a>Aby dodać komputer docelowy do bazy danych lokacji programu Configuration Manager  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **zasoby i zgodność**.  

3.  W zasoby i zgodność obszaru roboczego, przejdź do przegląd/urządzeń.  

4.  Na wstążce na **Home** karcie **Utwórz** kliknij przycisk **importu informacji o komputerze**.  

     Uruchamia Kreatora importowania informacji o komputerze.  

5.  Ukończ Kreatora importowania informacji o komputerze, korzystając z poniższych informacji. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    |**Na tej stronie kreatora**|**W tym**|  
    |-|-|  
    |**Wybierz źródło**|Kliknij przycisk **Importuj pojedynczy komputer**, a następnie kliknij przycisk **dalej**.|  
    |**Wybierz źródło: Pojedynczego komputera**|1.  W **nazwy komputera**, typ **WDG-CLI-01**.<br />2.  W **adres MAC**, typ ***adres_MAC*** (gdzie *adres_MAC* adres MAC karty sieciowej głównej dla komputera docelowego, WDG-CLI-01).<br />3.  Kliknij przycisk **Dalej**.|  
    |**Wybierz źródło: Podgląd danych**|Kliknij przycisk **Dalej**.|  
    |**Wybierz źródło: Wybierz kolekcję docelową**|Kliknij przycisk **Dalej**.|  
    |**Podsumowanie**|1.  Przejrzyj informacje w **szczegóły** pola, czy podane podczas wykonywania poprzednich stron kreatora.<br />2.  Kliknij przycisk **Dalej**.|  
    |**Postęp**|Postęp importowania komputera jest wyświetlana.|  
    |**Potwierdzenie**|Kliknij przycisk **Zamknij**.|  

 Aby uzyskać więcej informacji na temat dodawania nowego komputera do bazy danych lokacji programu Configuration Manager zobacz sekcję "Aby zaimportować informacje dotyczące jednego komputera," w sekcji "Jak do wdrażania systemów operacyjnych w programie Configuration Manager" w konfiguracji Menedżer biblioteka dokumentacji, która jest instalowana z programem Configuration Manager.  

###  <a name="CreateComputerCollectionIncludesTarget"></a>Krok 6-2. Tworzenie kolekcji komputerów, która zawiera komputer docelowy  
 W konsoli programu Configuration Manager utwórz kolekcję, która zawiera komputer docelowy (WDG-CLI-01). Można użyć tej kolekcji komputer później, podczas anonsowanie sekwencji zadań, utworzonej wcześniej w procesie.  

#### <a name="to-create-a-computer-collection-that-includes-the-target-computer"></a>Aby utworzyć kolekcję komputerów, która zawiera komputer docelowy

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **zasoby i zgodność**.  

3.  W zasoby i zgodność obszaru roboczego, przejdź do kolekcji omówienie lub urządzeniu.  

4.  Na wstążce na **Home** karcie **Utwórz** kliknij przycisk **Utwórz kolekcję urządzeń**.  

     Uruchamia Kreatora tworzenia kolekcji urządzeń.  

5.  Ukończ Kreatora tworzenia kolekcji urządzeń korzystając z poniższych informacji. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    |**Na tej stronie kreatora**|**W tym**|  
    |-|-|  
    |**Na tej stronie kreatora**|**W tym**|  
    |**Ogólne**|<ol><li>W **nazwa**, typ **Microsoft, Deployment — 01 partii**.</li><li>W **komentarz**, typ **komputerów, które mają być uwzględniane w pierwszym partii komputerów wdrożone**.</li><li>W **ograniczone kolekcji**, kliknij przycisk **Przeglądaj**.<br /><br />     **Wybieranie kolekcji** zostanie wyświetlone okno dialogowe. Wypełnij okno dialogowe, wykonując następujące czynności:<br /><br /> <ol><li>W **Wybieranie kolekcji** okna dialogowego, **nazwa**, kliknij przycisk **wszystkie systemy**.</li><li>Kliknij przycisk **OK**.</li></ol></li><li>Kliknij przycisk **Dalej**.</li></ol>|  
    |**Reguły członkostwa**|<ol><li>Kliknij przycisk **Dodaj regułę**, a następnie kliknij przycisk **reguły bezpośredniej**.<br /><br />     Uruchamia Kreatora tworzenia reguły członkostwa bezpośredniego.</li><li>Wykonaj Kreatora tworzenia reguły członkostwa bezpośredniego, wykonując następujące czynności:<br /><br /> <ol><li>Na stronie **Zapraszamy** kliknij przycisk **Dalej**.</li><li>Na **wyszukiwanie zasobów** strony w **klasy zasobów**, wybierz pozycję **zasób systemowy**; na liście **nazwa atrybutu**, wybierz pozycję  **Nazwa**; na liście **wartość**, typ **WDG-CLI-01**; a następnie kliknij przycisk **dalej**.</li><li>Na **zasobów wybierz** wybierz **WDG-CLI-01**, a następnie kliknij przycisk **dalej**. **Uwaga:**          Proces dodawania komputera docelowego (WDG-CLI-01) we wszystkich systemach może zająć kilka minut. Jeśli na liście nie ma WDG-CLI-01, powtórz kroki b i c, aż pojawi się WDGCLI01.</li><li>Na **Podsumowanie** kliknij przycisk **dalej**.</li><li>Na **zakończenia** kliknij przycisk **Zamknij**.</li></ol></li><li>Kliknij przycisk **Dalej**.</li></ol>|  
    |**Podsumowanie**|1.  Przejrzyj informacje w **szczegóły** pola, czy podane podczas wykonywania poprzednich stron kreatora.<br />2.  Kliknij przycisk **Dalej**.|  
    |**Postęp**|Zostanie wyświetlony pasek postępu tworzenia kolekcji urządzeń.|  
    |**Zakończenie**|Kliknij przycisk **Zamknij**.|  

 Aby uzyskać więcej informacji zobacz sekcję "Jak Aby utworzyć kolekcje w programie Configuration Manager" w bibliotece dokumentacji, która jest instalowana z programem Configuration Manager programu Configuration manager.  

###  <a name="DeployTargetComputerTaskSequence"></a>Krok 6-3. Wdrożenie sekwencji zadań komputera docelowego  
 W konsoli programu Configuration Manager należy wdrożyć sekwencję zadań, utworzony wcześniej w procesie dla komputerów docelowych. Wdróż sekwencję zadań do kolekcji komputerów docelowych utworzony wcześniej w procesie.  

#### <a name="to-deploy-the-task-sequence"></a>Aby wdrożyć sekwencję zadań  

1.  Kliknij przycisk **Start**, wskaż polecenie **wszystkie programy**, a następnie wskaż **Microsoft System Center 2012**. Wskaż **programu Configuration Manager**, a następnie kliknij przycisk **konsoli programu Configuration Manager**.  

2.  W konsoli programu Configuration Manager, w okienku nawigacji kliknij **Biblioteka oprogramowania**.  

3.  W obszarze roboczym Biblioteka oprogramowania przejdź do Przegląd/operacyjnego systemów lub zadanie sekwencji.  

4.  W okienku podglądu kliknij **wdrożenia docelowego Windows 8.1**.  

5.  Na wstążce na **Home** karcie **wdrożenia** kliknij przycisk **Wdróż**.  

     Uruchamia Kreatora wdrażania oprogramowania.  

6.  Ukończ Kreatora wdrażania oprogramowania korzystając z poniższych informacji.  Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    |**Na tej stronie kreatora**|**W tym**|  
    |-|-|  
    |**Ogólne**|1.  W **kolekcji**, kliknij przycisk **Przeglądaj**.<br />2.  W **Przeglądaj kolekcji** okno dialogowe, kliknij przycisk **Microsoft, Deployment — 01 partii**, a następnie kliknij przycisk **OK**.<br />3.  W **komentarz**, typ **wdrażanie Windows 8.1 do pierwszej partii komputerów docelowych**.<br />4.  Kliknij przycisk **Dalej**.|  
    |**Ustawienia wdrożenia**|1.  W **celu**, wybierz pozycję **dostępne**.<br />2.  Wybierz **Udostępnij nośnikom rozruchowym i środowisku PXE** pole wyboru.<br />3.  Kliknij przycisk **Dalej**.|  
    |**Ustawienia wdrożenia: Harmonogram**|Kliknij przycisk **Dalej**.|  
    |**Ustawienia wdrożenia: Środowisko użytkownika**|Kliknij przycisk **Dalej**.|  
    |**Ustawienia wdrożenia: Alerty**|Kliknij przycisk **Dalej**.|  
    |**Ustawienia wdrożenia: Punkty dystrybucji**|Kliknij przycisk **Dalej**.|  
    |**Podsumowanie**|1.  Przejrzyj informacje w **szczegóły** pola, czy podane podczas wykonywania poprzednich stron kreatora.<br />2.  Kliknij przycisk **Dalej**.|  
    |**Postęp**|Zostanie wyświetlony pasek postępu wdrażania sekwencji zadań.|  
    |**Zakończenie**|Kliknij przycisk **Zamknij**.|  

 Aby uzyskać więcej informacji zobacz sekcję "Jak do wdrażania sekwencji zadań," w bibliotece dokumentacji, która jest instalowana z programem Configuration Manager programu Configuration manager.  

###  <a name="StartTargetComputerTaskSequenceMedia"></a>Krok 6-4. Uruchom komputer docelowy z nośnika rozruchowego sekwencji zadań  
 Uruchom komputer docelowy (WDG-CLI-01) przy użyciu nośnika rozruchowego sekwencji zadań, utworzony wcześniej w procesie. Ten nośnik uruchamia środowisko Windows PE na komputerze odniesienia i inicjuje proces zestawu MDT. Po zakończeniu procesu zestawu MDT Windows 8.1 jest wdrażany na komputerze docelowym.  

> [!NOTE]
>  Można także zainicjować proces zestawu MDT, uruchamiając na komputerze docelowym za pomocą usług wdrażania systemu Windows.  

#### <a name="to-start-the-target-computer-with-the-task-sequence-bootable-media"></a>Do uruchomienia komputera docelowego z nośnika rozruchowego sekwencji zadań

1.  Uruchom WDG-CLI-01 z nośnika rozruchowego sekwencji zadań, utworzony wcześniej w procesie.  

     Uruchamia środowisko Windows PE, a następnie uruchamia Kreatora sekwencji zadań.  

2.  Ukończ pracę Kreatora sekwencji zadań, korzystając z poniższych informacji. Zaakceptuj wartości domyślne, chyba że określono inaczej.  

    |**Na tej stronie kreatora**|**W tym**|  
    |-|-|      
    |**Witamy w Kreatorze sekwencji zadań**|W **hasło**, typ  **P@ssw0rd** , a następnie kliknij przycisk **dalej**.|  
    |**Wybierz sekwencję zadań**|W polu listy, wybierz **wdrożenia docelowego Windows 8.1**, a następnie kliknij przycisk **dalej**.|  

#### <a name="to-monitor-the-reference-computer-deployment-process-using-the-deployment-workbench"></a>Aby monitorować proces wdrażania komputera odniesienia przy użyciu konsoli Deployment Workbench

1.  Na WDG-MDT-01, kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft Deployment Toolkit**, a następnie kliknij przycisk **konsoli Deployment Workbench**.  

2.  W drzewie konsoli Deployment Workbench przejdź do wdrożenia środowiska roboczego/wdrożenia udziałów/udział wdrożenia zestawu MDT (C:\DeploymentShare$)/Monitoring.  

3.  W okienku szczegółów wyświetlić proces wdrażania **WDG-CLI-01**.  

4.  W okienku Akcje kliknij okresowo **Odśwież**.  

     Stan procesu wdrażania jest aktualizowana w okienku szczegółów. Nadal monitorować proces wdrażania, aż do ukończenia procesu.  

5.  W okienku szczegółów kliknij **WDG-CLI-01**.  

6.  W okienku Akcje kliknij polecenie **właściwości**.  

     **Właściwości WDG-CLI-01** zostanie wyświetlone okno dialogowe.  

7.  W **właściwości WDG-CLI-01** na okna dialogowego **tożsamości** pozycję Wyświetl monitorowania dostarczone informacje na temat procesu wdrażania zgodnie z opisem w poniższej tabeli:

    |**Informacje**|**Opis**|  
    |-|-|  
    |**IDENTYFIKATOR**|Unikatowy identyfikator dla komputera wdrażany.|  
    |**Nazwa komputera**|Nazwa komputera jest wdrożony.|  
    |**Stan wdrożenia**|Bieżący stan komputera wdrożony; Stan może być jedną z następujących czynności:<br /><br /> -   **Uruchomiona**. Sekwencja zadań jest dobra i uruchomiona.<br />-   **Nie powiodło się**. Sekwencja zadań nie powiodło się, a proces wdrażania nie powiodło się.<br />-   **Ukończono**. Sekwencja zadań została ukończona.<br />-   **Odpowiadać**. Sekwencja zadań jego stan nie został zaktualizowany w ciągu ostatnich czterech godzin i zostanie uznany za nieodpowiadający.|  
    |**Krok**|Bieżącego kroku sekwencji zadań uruchamiana.|  
    |**Postęp**|Ogólny postęp sekwencji zadań. Pasek postępu wskazuje, ile kroków sekwencji zadań zostały uruchomione poza całkowita liczba kroków sekwencji zadań.|  
    |**Początek**|Czas rozpoczęcia procesu wdrażania.|  
    |**Koniec**|Czas zakończenia procesu wdrażania.|  
    |**Który upłynął**|Czas procesu wdrażania była uruchomiona lub trwało do uruchomienia, jeśli zakończenie procesu wdrażania.|  
    |**Błędy**|Liczba błędów napotkanych podczas procesu wdrażania.|  
    |**Ostrzeżenia**|Liczba ostrzeżeń podczas procesu wdrażania.|  
    |**Pulpit zdalny**|Ten przycisk służy do ustanawiania połączenia pulpitu zdalnego z komputerem wdrażany przy użyciu funkcji pulpitu zdalnego systemu Windows. Ta metoda zakłada się, że:<br /><br /> -Docelowy system operacyjny jest uruchomiony i ma włączoną obsługę usług pulpitu zdalnego<br />-   **mstsc.exe** znajduje się w ścieżce **Uwaga:**  Ten przycisk jest zawsze widoczne, ale nie można ustanowić sesji usług pulpitu zdalnego Jeśli monitorowanym komputerze środowiska Preinstalacyjnego systemu Windows, instalacja docelowego systemu operacyjnego nie zostało zakończone lub nie ma włączenie tej funkcji pulpitu zdalnego.|  
    |**Połączenie maszyn wirtualnych**|Ten przycisk służy do ustanowienia połączenia pulpitu zdalnego z maszyną wirtualną w funkcji Hyper-V. Ta metoda zakłada się, że:<br /><br /> -Wdrożenie jest wykonywane do maszyny Wirtualnej z systemem w funkcji Hyper-V<br />-   **vmconnect.exe** znajduje się w folderze %ProgramFiles%\Hyper-V **Uwaga:**  Ten przycisk jest wyświetlany, gdy ZTIGather.wsf wykryje, że składniki integracji funkcji Hyper-V są uruchomione na monitorowanym komputerze. W przeciwnym razie ten przycisk, nie będą widoczne.|  
    |**DaRT zdalnego sterowania**|Ten przycisk pozwala ustanowić sesję zdalnego sterowania należy użyć funkcji Podgląd zdalnego w Diagnostics and Recovery Toolkit (DaRT).<br /><br /> Ta metoda zakłada się, że:<br /><br /> -DaRT został wdrożony na komputerze docelowym i jest aktualnie uruchomiona<br />-   **DartRemoteViewer.exe** znajduje się w folderze %ProgramFiles%\Microsoft DaRT 7\v7 **Uwaga:**  Ten przycisk jest wyświetlany, gdy ZTIGather.wsf wykryje, że DaRT jest uruchomiony na monitorowanym komputerze. W przeciwnym razie ten przycisk, nie będą widoczne.|  
    |**Automatyczne odświeżanie te informacje co 10 sekund**|Pole wyboru, która kontroluje, czy informacje w oknie dialogowym są odświeżane automatycznie. Jeśli pole wyboru jest:<br /><br /> -Zaznaczone, dane są odświeżane co 10 sekund<br />-Wyczyszczone, nie jest automatycznie odświeżany informacje i musi być odświeżane ręcznie przy użyciu **Odśwież teraz** przycisku|  
    |**Odśwież teraz**|Ten przycisk natychmiast odświeża informacje wyświetlane w oknie dialogowym.|  

8.  W **właściwości WDG-REF-01** okno dialogowe, kliknij przycisk **OK**.  

9. Zamknięcie konsoli Deployment Workbench.  

#### <a name="to-monitor-the-reference-computer-deployment-process-using-the-get-mdtmonitordata-cmdlet"></a>Aby monitorować proces wdrażania komputera odniesienia przy użyciu polecenia cmdlet Get-MDTMonitorData

1.  Na WDG-MDT-01, kliknij przycisk **Start**, wskaż polecenie **narzędzia administracyjne**, a następnie kliknij przycisk **moduły programu Windows PowerShell**. Zostanie otwarty wiersz polecenia moduły programu Windows PowerShell.  

2.  Utwórz dysk programu PowerShell, który używa dostawcy programu PowerShell zestawu MDT, uruchamiając [elementu PSDrive nowy](http://technet.microsoft.com/library/hh849829.aspx) polecenia cmdlet, jak pokazano w poniższym przykładzie:  

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
