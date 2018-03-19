---
title: Informacje o wersji
titleSuffix: MDT 2013 release notes
description: "Zrozumieć wymagania wstępne i ograniczenia dotyczące programu Microsoft Deployment Toolkit 2013. "
ms.date: 09/09/2016
ms.prod: configuration-manager
ms.technology:
- configmgr-osd
ms.topic: article
ms.assetid: 6e32ce6d-585d-4801-a345-ff0f6f2d90ad
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: 11b3eb6ed778cca78823c58b606d98166ded9b55
ms.sourcegitcommit: 645cd5a324bdd299906efa27eaca5885eafc9e9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2018
---
# <a name="microsoft-deployment-toolkit-2013-release-notes"></a>Informacje o wersji 2013 zestawu narzędzi firmy Microsoft do wdrażania  
 Witamy w informacjach o wersji dla Microsoft® Deployment Toolkit (MDT) 2013. Przeczytaj te informacje o wersji dokładnie przed rozpoczęciem instalacji zestawu MDT 2013, ponieważ zawierają one informacje potrzebne do pomyślnego zainstalowania zestawu narzędzi, które nie mogą obejmować w dokumentacji Pomocy zestawu MDT 2013.  

 Ta wersja obsługuje wdrażania systemu Windows 8.1, Windows 8, Windows 7, alokowania komputera z systemem Windows, Windows Embedded POSReady 7 (POSReady 7), systemu Windows Server 2012 R2, Windows Server 2012 i systemów operacyjnych Windows Server 2008 R2. Zawiera Microsoft biblioteka dokumentacji zestaw narzędzi do wdrażania, dostarczanego z zestawem MDT 2013 pełną dokumentację w tej wersji.  

> [!NOTE]
>  W tym dokumencie *Windows* ma zastosowanie do systemów operacyjnych Windows 8.1, Windows 8, Windows 7, Windows Server 2012 R2, Windows Server 2012 i Windows Server 2008 R2, chyba że określono inaczej. Zestaw MDT nie obsługuje wersji na podstawie procesora ARM systemu Windows. Podobnie *MDT* odwołuje się do zestawu MDT 2013, chyba że określono inaczej.  

## <a name="prerequisites"></a>Wymagania wstępne  
 W przypadku wdrożeń Lite Touch Installation (LTI) zestawu MDT wymaga następujących składników:  

 Aby zainstalować zestaw MDT na:  

-   Windows 7 lub Windows Server 2008 R2 należy zainstalować lub włączyć następujące składniki na komputerze, na którym jest zainstalowany zestaw MDT:  

    -   Wersja programu Microsoft Management Console 3.0  

    -   Microsoft .NET Framework 3.5 z dodatkiem Service Pack 1 (SP1)  

    -   Windows PowerShell™ w wersji 2.0  

    -   Windows Assessment and Deployment Kit (ADK) dla Windows 8.1 (składniki narzędzia wdrażania systemu Windows PE i narzędzia migracji stanu użytkownika)  

-   Windows 8.1, Windows 8, Windows Server 2012 R2 lub Windows Server 2012, należy zainstalować lub włączyć następujące składniki na komputerze, na którym jest zainstalowany zestaw MDT:  

    -   Windows ADK dla Windows 8.1 (składniki narzędzia wdrażania systemu Windows PE i narzędzia migracji stanu użytkownika)  

    -   Microsoft .NET Framework 4.0 (który jest dostępny w systemie operacyjnym)  

    -   Windows PowerShell w wersji 3.0 (który jest dostępny w systemie operacyjnym)  

 W przypadku wdrożeń Zero Touch instalacji (ZTI) zestawu MDT wymaga następujących składników:  

-   Microsoft System Center 2012 R2 Configuration Manager  

> [!NOTE]
>  Zobacz dokumentację produktu Configuration Manager dodatkowe wymagania.  

 W przypadku wdrożeń instalacji sterowanej (UDI) zestawu MDT wymaga następujących składników:  

-   Microsoft System Center 2012 R2 Configuration Manager  

-   Microsoft System Center 2012 Configuration Manager  

-   Microsoft System Center Configuration Manager 2007 R3  

> [!NOTE]
>  Zobacz dokumentację produktu Configuration Manager dodatkowe wymagania.  

 Aby zainicjować Microsoft System Center 2012 R2 Orchestrator runbook przy użyciu zestawu MDT, należy zainstalować [aktualizacja ADO.NET Data Services dla programu .NET Framework 3.5 SP1 dla systemu Windows 7 i Windows Server 2008 R2](http://www.microsoft.com/download/details.aspx?displaylang=en&id=2343).  

## <a name="installing-mdt"></a>Instalowanie zestawu MDT  
 Upewnij się, że masz pełnej kopii zapasowej serwera przed rozpoczęciem instalacji zestawu MDT na komputerze, który ma istniejącej instalacji zestawu mdt.  

 Proces instalacji zestawu MDT usuwa istniejące wystąpienia zestawu mdt zainstalowany na tym samym komputerze. Istniejące udziały wdrażania, punkty dystrybucji i baz danych są zachowywane w trakcie tego procesu, ale należy uaktualnić po zakończeniu instalacji.  

### <a name="support-for-upgrading-from-previous-versions-of-mdt"></a>Obsługa uaktualniania z poprzednich wersji zestawu mdt  
 Zestaw MDT 2013 obsługuje uaktualnianie z następujących wersji zestawu MDT:  

-   MDT 2012 Update 1  

> [!NOTE]
>  Utwórz kopię zapasową istniejącej infrastruktury MDT przed próbą uaktualnienia.  

### <a name="usmt-download-requirements"></a>Wymagania dotyczące pobierania narzędzia USMT  
 Nie trzeba oddzielnie Pobierz zestaw Windows użytkownika stanu migracji narzędzia (USMT). Narzędzie USMT w wersji 6 jest częścią zestawu ADK systemu Windows na Windows 8.1. Narzędzie USMT 6 obsługuje przechwytywania stanu użytkownika z wszystkich wersji systemu Windows 8.1, Windows 8 i Windows 7.  

### <a name="the-lti-upgrade-process"></a>Proces uaktualniania LTI  
 Po zainstalowaniu zestawu MDT, możesz uaktualnić istniejącego udziału wdrożenia, uruchamiając kreatora Otwórz udziału wdrożenia w węźle udziałów wdrożenia w konsoli Deployment Workbench. Określ ścieżkę do istniejącego katalogu udziału wdrożenia, a następnie wybierz **uaktualnienia** pole wyboru. Należy pamiętać, że w ten sposób również uaktualnia istniejących udziałów wdrożenia sieci i udziałów wdrożenia nośnika, więc te powinny być dostępne. Nie wykonuj tego uaktualnienia podczas wykonywania wdrożenia, ponieważ pliki w użyciu może spowodować problemy z uaktualnianiem.  

### <a name="the-zti-upgrade-process"></a>Proces uaktualniania ZTI  
 Istniejącej sekwencji zadań zestawu MDT w programie System Center 2012 Configuration Manager nie są modyfikowane w trakcie procesu instalacji zestawu mdt i będą nadal działać bez jakikolwiek problem. Nie jest mechanizmu w celu uaktualnienia tych sekwencji zadań. Jeśli chcesz użyć innych nowych funkcji zestawu MDT, tworzenie nowej sekwencji zadań.  

 Po zakończeniu uaktualniania:  

-   **Uruchom Kreatora integracji programu ConfigMgr konfiguracji.** Po uaktualnieniu do rejestrowania nowych składników i zainstaluj zaktualizowane szablony sekwencji zadań ZTI należy uruchomić tego kreatora.  

-   **Upewnij się, że Utwórz nowy pakiet plików Toolkit wdrożenia firmy Microsoft dla nowej sekwencji zadań ZTI utworzone.** Można użyć istniejącego pakietu plików Toolkit wdrożenia firmy Microsoft dla sekwencji zadań ZTI utworzone przed uaktualnieniem, ale należy utworzyć nowy pakiet plików Toolkit wdrożenia firmy Microsoft dla nowej sekwencji zadań ZTI.  

## <a name="known-issues"></a>Znane problemy  
 Znane problemy w zestawie MDT 2013 są podzielone na następujące kategorie:  

-   Ogólne problemy, zgodnie z opisem w [znane problemy ogólne](#KnownIssue)  

-   Tylko we wdrożeniach LTI zgodnie z opisem w [znanych problemów związanych z tylko wdrożenia LTI](#KnownIssuesLTI)  

-   We wdrożeniach LTI oraz ZTI, zgodnie z opisem w [znanych problemów związanych z LTI i wdrożenia ZTI](#KnownIssuesLTIZTI)  

-   W przypadku wdrożeń UDI, zgodnie z opisem w [znane problemy w przypadku wdrożeń UDI](#KnownIssuesUDI)  

###  <a name="KnownIssue"></a>Znane problemy ogólne  
 Następujące problemy nie są specyficzne dla dowolnej metody wdrażania.  

#### <a name="compiled-html-help-files-are-not-up-to-date"></a>Skompilowane pliki Pomocy HTML nie są aktualne  
 Wszystkie skompilowane pliki Pomocy HTML (. Uwzględnione CHM) z zestawem MDT 2013, w tym "Microsoft Deployment Toolkit dokumentacji Library.chm" i "Release Notes.chm" są aktualne w wersji zestawu MDT 2012 Update 1. Wszystkie łącza "Help" w konsoli Deployment Workbench otworzy zawartości w tych plikach.  

 OBEJŚCIE PROBLEMU: Ten dokument zawiera informacje o wersji 2013 zestawu MDT i zastępuje "Wersji Notes.chm" w katalogu instalacyjnym.  

 Planowany zaktualizowanej biblioteki dokumentacji zestawu MDT w formacie programu Microsoft Word ma być dostępny z Microsoft Download Center.  

#### <a name="modifying-key-task-sequence-steps-can-lead-to-unpredictable-results"></a>Modyfikowanie kroków sekwencji zadań klucza może spowodować nieoczekiwane wyniki  
 Modyfikowanie **Zainstaluj System operacyjny** krok sekwencji zadań lub **Zastosuj obraz systemu operacyjnego** krok sekwencji zadań po tworzenie kroku sekwencji zadań może spowodować nieoczekiwane wyniki. Na przykład, jeśli należy utworzyć sekwencję zadań do wdrożenia 32-bitowego obrazu systemu Windows 7, a później zmieni **Zainstaluj System operacyjny** krok sekwencji zadań lub **Zastosuj obraz systemu operacyjnego** krok sekwencji zadań Aby odwołać 64-bitowego obrazu systemu Windows 7, sekwencja zadań nie może działać prawidłowo.  

 OBEJŚCIE PROBLEMU: Utwórz nową sekwencję zadań do wdrażania obrazów systemów operacyjnych.  

#### <a name="domain-join-fails-when-an-organizational-unit-ou-contains-special-characters"></a>Przyłączanie do domeny nie powiedzie się, gdy jednostki organizacyjnej (OU) zawiera znaki specjalne.  
 Przyłączanie do domeny nie powiedzie się, gdy jednostki organizacyjnej (OU) zawiera znaki specjalne w formacie Unicode. Nazwa jednostki Organizacyjnej zawiera spacje, metod opisanych poniżej powinny działać poprawnie. Jeśli jednostki Organizacyjnej zawiera znaki, takie jak znaki specyficzne dla języka, zastąp znaki ich równoważne znaków ANSI. Na przykład zmieniłby Cońtoso firmie Contoso.  

 OBEJŚCIE PROBLEMU: Wybierz jedną z następujących metod, aby rozwiązać ten problem:  

-   Użyj **MachineObjectOU** właściwości, jak pokazano w poniższym przykładzie, aby określić jednostkę organizacyjną dla komputera w pliku CustomSettings.ini lub w bazie danych zestawu MDT (MDT DB).  

    ```  
    [Settings]   
    Priority=MacAddress, Default   
    Properties=MyCustomProperty   

    [Default]   
    OSinstall=Y  

    [00:15:1d:ee:2a:aa]   
    OSDComputername=WDG-CLI-01   
    MachineObjectOU=OU=HelpDesk,OU=Corp,DC=Woodgrovebank,DC=com  
    ```  

-   Użyj **DomainOUs** właściwości, jak pokazano w poniższym przykładzie, aby utworzyć listę jednostek organizacyjnych w pliku CustomSettings.ini, lub w bazie danych zestawu MDT, który można wybrać w Kreatorze wdrażania.  

    ```  
    [Settings]   
    Priority=MacAddress, Default   
    Properties=MyCustomProperty   

    [Default]  
    OSInstall=Y  
    SkipAppsOnUpgrade=YES  
    SkipCapture=YES  
    SkipAdminPassword=NO  
    SkipProductKey=YES  
    DoCapture=YES  
    DomainOUs1=OU=Users,OU=Corp,DC=Woodgrovebank,DC=com   
    DomainOUs2=OU=HelpDesk,OU=corp,DC=Woodgrovebank,DC=com  
    ```  

-   Użyj pliku DomainOUList.xml, jak pokazano w poniższym przykładzie, aby utworzyć listę jednostek organizacyjnych, które można wybrać w Kreatorze wdrażania.  

    ```  
    <?xml version="1.0" encoding="utf-8"?>   
    <DomainOUs>   
       <DomainOU>   
          OU=Users,OU=Corp,DC=Woodgrovebank,DC=com  
       </DomainOU>   
       <DomainOU>   
         OU=HelpDesk,OU=corp,DC=Woodgrovebank,DC=com  
       </DomainOU>   
    </DomainOUs>  
    ```  

     Należy utworzyć plik DomainOUList.xml za pomocą dowolnego języka XML w edytorze. Umieść plik DomainOUList.xml w folderze skryptów w udział wdrożenia do LTI lub pakiet plików zestawu MDT ZTI i UDI.  

#### <a name="configure-adds-step-does-not-have-an-option-for-windows-server-2012-domain-and-forest-functional-levels"></a>Skonfiguruj DODAJE krok nie jest dostępna opcja dla systemu Windows Server 2012 domeny i lasu poziomów funkcjonalności  
 Podczas konfigurowania zaawansowane opcje kroku "Konfigurowanie DODAJE" list poziom funkcjonalności lasu i poziom funkcjonalności domeny nie ma możliwości systemu Windows Server 2012.  

 OBEJŚCIE PROBLEMU: Ustaw DomainLevel = 5 i/lub ForestLevel = 5 w CustomSettings.ini. Zobacz odwołanie do zestawu narzędzi, aby uzyskać więcej informacji na temat tych ustawień.  

#### <a name="gpo-packs-do-not-exist"></a>Pakiety obiektu zasad grupy nie istnieją.  
 Menedżer zgodności zabezpieczeń (SCM) pakiety obiektu zasad grupy nie są dołączone do zestawu MDT 2013. Krok "Zastosuj pakiet lokalny obiekt zasad grupy" (ZTIApplyGPOPack.wsf) będzie rejestrować wpis podobny do jednego z następujących czynności:  

 "Ścieżka pakietu obiektu zasad grupy — Templates\GPOPacks\ jest nieprawidłowa. Obiekt zasad grupy nie zostały zastosowane."  

 "Domyślny zestaw MDT obiektu zasad grupy pakiet nie istnieje dla tego systemu operacyjnego."  

 OBEJŚCIE PROBLEMU: Utwórz GPOPacks podfolderze szablonów w udziału wdrożenia (na przykład C:\DeploymentShare\Templates\GPOPacks). Eksportowanie kopii zapasowej obiektu zasad grupy z SCM lub konsoli zarządzania zasadami grupy, a następnie dodaj następujące pliki z SCM:  

-   GPOPack.wsf  

-   LocalPol.exe  

-   LocalSecurityDB.sdb  

 Utwórz w podfolderze GPOPacks i skopiuj tę zawartość. Następnie należy określić nazwę katalogu we właściwości GPOPackPath w CustomSettings.ini.  

#### <a name="the-configuration-manager-console-will-crash-if-mdt-is-uninstalled-without-removing-the-console-extensions"></a>Konsola programu Configuration Manager ulegnie awarii, w przypadku odinstalowania zestawu MDT bez usuwania rozszerzenia konsoli.  
 Podczas uruchamiania **Konfigurowanie integracji programu ConfigMgr**, jeśli Usuń zaznaczenie pola wyboru opcji **usuwanie rozszerzeń zestawu MDT, programu Configuration Manager 2012**, wystąpi następujący błąd podczas próby uruchomienia Konsola programu Configuration Manager:  

```  
Couldn’t load sqmapi.dll from bin\x86\sqmapi.dll. Last Error = (126)  
```  

 OBEJŚCIE PROBLEMU: Brak  

#### <a name="oobe-settings-missing-from-windows-81-unattendxml-template"></a>Ustawienia OOBE brakuje szablonu Unattend.xml Windows 8.1  
 Sekwencje zadań Windows 8.1 użyj starszych szablonu Unattend.xml, który nie zawiera wiele właściwości w < OOBE\> sekcję, taką jak HideWirelessSetupInOOBE, który może wymagać ręcznego interakcji z wdrożeniami w systemach z sieci bezprzewodowej Karta sieciowa.  

 OBEJŚCIE PROBLEMU: Dodaj następujące wpisy do < OOBE\> części sekwencji zadań Unattend.xml dla Windows 8.1.  

```  
<OOBE>  
    <HideEULAPage>true</HideEULAPage>  
    <NetworkLocation>Work</NetworkLocation>  
    <ProtectYourPC>1</ProtectYourPC>  
    <HideLocalAccountScreen>true</HideLocalAccountScreen>  
    <HideOnlineAccountScreens>true</HideOnlineAccountScreens>  
    <HideWirelessSetupInOOBE>true</HideWirelessSetupInOOBE>  
</OOBE>  
```  

#### <a name="some-features-are-listed-incorrectly-for-windows-81"></a>Niektóre funkcje są niepoprawnie skonfigurowane dla Windows 8.1  
 Korzystając z **zainstalować role i funkcje** lub **odinstalowywanie ról i funkcji** kroki i wybierając pozycję Windows 8.1, zastosuj następujące problemy:  

-   **Internet Explorer 10 (x86)**, które odwołuje się do funkcji Internet-Explorer — opcjonalnie — x86 i **programu Internet Explorer 10 (amd64)**, które odwołuje się do funkcji Internet-Explorer — opcjonalnie — amd64 jest wyświetlany w systemie Windows 8.1 "Internet Explorer 11."  

-   **Klienta folderów roboczych** (WorkFolders klienta) nie ma na liście.  

 OBEJŚCIE PROBLEMU: Internet Explorer 10... Wybrane elementy można nadal używać, ale będzie włączać lub wyłączać programu Internet Explorer 11, zamiast programu Internet Explorer 10, wymienione. Klient folderów roboczych musi być włączone lub wyłączone w oddzielnej **Uruchom wiersz polecenia** kroku przy użyciu narzędzia DISM, na przykład:  

```  
Dism /online /Enable-Feature /FeatureName:WorkFolders-Client  
```  

###  <a name="KnownIssuesLTI"></a>Znane problemy tylko we wdrożeniach LTI  
 Oto lista znanych problemów, które dotyczą tylko wdrożenia LTI.  

#### <a name="check-for-updates-downloads-an-older-list-of-components"></a>Wyszukaj aktualizacje, pobieranie starszej listy składników  
 W konsoli Deployment Workbench, Centrum informacji węzeł składników, wybierając **Sprawdź aktualizacje** z **akcji** menu pobierze starsza wersja programu bddmanifest.cab, przywrócenie składnika co spowoduje manifest (ComponentList.xml) do starszej wersji.  

 OBEJŚCIE PROBLEMU: Nie używaj **Sprawdź aktualizacje**; ta funkcja jest przestarzała i zostanie usunięte w przyszłości.  

#### <a name="windows-81-appx-cleanup-maintenance-task-can-affect-sysprep"></a>Zadanie konserwacji czyszczenia AppX Windows 8.1 może wpływać na programu Sysprep  
 Po zainstalowaniu Windows 8.1 wbudowane zadanie konserwacji, Pre-Staged App Cleanup, zostanie uruchomiony po 60 minutach używania komputera, następuje 15 minutach czas bezczynności komputera. Jeśli po zakończeniu tego zadania konserwacji zostanie uruchomiony, generuje on ostrzeżenia w pliku setupact.log przez program Sysprep. Jeśli ten obraz jest następnie przechwycony i wdrożony, środowisko użytkownika końcowego może ulec pogorszeniu. W szczególności pakietów zasobów opartych na języku, skalę i pakietach DXFL, które nie zostały zainstalowane dla bieżących kont użytkowników zostaną usunięte. Ten obraz jest wdrażana dla komputera, na których mają zastosowanie tych pakietów zasobów, musi być zainstalowany jako aktualizacji przy użyciu sklepu lub za pośrednictwem mechanizmu ładowania bezpośredniego w przedsiębiorstwie.  

 OBEJŚCIE PROBLEMU: Dostępne są dwie opcje, aby zminimalizować ten problem. Najpierw upewnij się, że zostanie uruchomiony w ciągu 75 minut od instalacji systemu Windows 8.1. Po drugie Jeśli nie powiodło się, że program Sysprep będzie uruchamiana w ciągu 75 minut od instalacji systemu Windows 8.1, należy wyłączyć zadanie konserwacji.  

 Aby automatycznie wyłączyć zadanie konserwacji kompilacji zestawu MDT w ramach sekwencji zadań i przechwytywania, natychmiast po **Zbierz tylko lokalne** krok **przywracania** grupy Wstaw nowy **Uruchom wiersz polecenia** kroku z następującego polecenia:  

```  
Schtasks.exe /change /disable /tn "\Microsoft\Windows\AppxDeploymentClient\Pre-staged app cleanup"  
```  

 Na przykład  

 ![Zestawu MDT 2013 Release Notes obrazu 1](media/MDT2013ReleaseNotesImage1.jpg "MDT2013ReleaseNotesImage1")  

 Ten krok można dodawać tylko do sekwencji zadań uruchamiających program Sysprep na Windows 8.1. System Windows automatycznie ponownie włączy zadanie konserwacji podczas Sysprep fazy uogólniania.  

#### <a name="existing-databases-will-retain-50-character-application-names-when-upgrading-to-mdt-2013"></a>Istniejące bazy danych zostaną zachowane nazwy aplikacji usługi 50 znaków, podczas uaktualniania do zestawu MDT 2013  
 Zestaw MDT 2013 obejmuje zmiany do bazy danych, aby rozszerzyć pole Nazwa aplikacji od 50 do 255 znaków. Nową bazę danych w zestawie MDT 2013 użyje długość pola 255 znaków. Istniejąca baza danych uaktualniony do zestawu MDT 2013 zestawu MDT 2012 Update 1, zachowują długość pola 50 znaków.  

 OBEJŚCIE PROBLEMU: Po uaktualnieniu do wersji zestawu MDT 2013 ręcznie zmienić tabeli bazy danych za pomocą następujących poleceń SQL:  

```  
ALTER TABLE [dbo].[Settings_Applications]   
ALTER COLUMN [Applications] [nvarchar] (256)  
```  

#### <a name="the-deployment-will-fail-on-a-legacy-bios-system-if-bitlocker-is-enabled-and-a-data-partition-is-created"></a>Wdrożenie zakończą się na starszej wersji systemu BIOS, jeśli funkcja BitLocker jest włączona i zostanie utworzona partycja danych  
 Jeśli wdrożenie powoduje włączenie funkcji BitLocker, wartość domyślna "Format i partycji" krok w sekwencji zadań jest edytowany uwzględnienie dodatkowych danych partycji (na przykład OSDisk [Podstawowy] 60% danych [Podstawowy] 100%), i sekwencja zadań jest wdrożona starszy system BIOS System, wdrożenie zakończy się niepowodzeniem do rozruchu w systemie Windows z powodu błędu:  

```  
Boot Device Not Found  
Please install an OS on your hard disk  
Hard Disk - (3F0)  
```  

 OBEJŚCIE PROBLEMU: Brak  

#### <a name="provisioning-of-windows-store-applications-does-not-include-dependencies"></a>Inicjowanie obsługi administracyjnej aplikacji ze Sklepu Windows nie ma zależności  
 Zależności skonfigurowane dla aplikacji Sklepu Windows (appx) nie zostanie zainstalowana w razie sekwencja zadań instaluje aplikacje.  

 OBEJŚCIE PROBLEMU: Bezpośrednio w sekwencji zadań należy zainstalować zależności aplikacji.  

#### <a name="gpt-drives-are-partitioned-as-mbr"></a>Dyski GPT są dzielone jako MBR  
 Dysk jest skonfigurowany do używania partycji tabeli partycji GUID (GPT) system w **Format i partycji** kroku sekwencji zadań, ale jest wdrażane za pomocą główny rekord rozruchowy (MBR) partycji systemu, zamiast tego. Ten problem może być spowodowany na komputerach z systemem BIOS mające drugi dysków, które są większe niż 2 GB i wymagają systemu partycjonowania GPT.  

 OBEJŚCIE: wykonaj następujące czynności:  

1.  W sekwencji zadań, który chcesz zmodyfikować, w **instalacją** w **nowy komputer tylko** grupy, bezpośrednio przed **Format i partycji** krok sekwencji zadań dla danego dysku tworzenia sekwencji zadań na podstawie **Ustaw zmienną sekwencji zadań** zadań typ sekwencji, aby wymusić użycie system partycji dysku GPT, korzystając z poniższych informacji.

    |Dla tego ustawienia|Użyj tej wartości|  
    |-|-|  
    |Nazwa|Wymuszenie korzystania z systemu partycji dysku GPT|  
    |Opis|Wymuś następujący Format i partycji kroku sekwencji zadań przy użyciu systemu partycji dysku GPT.|  
    |Zmienną sekwencji zadań|OSDDiskType|  
    |Wartość|GPT|  

2.  Natychmiast po **Format i partycji** krok sekwencji zadań, zostały zidentyfikowane w poprzednim kroku, Utwórz krok sekwencji zadań na podstawie **Ustaw zmienną sekwencji zadań** typ sekwencji można zresetować zadania Użyj systemu partycji dysku GPT, korzystając z poniższych informacji.

    |Dla tego ustawienia|Użyj tej wartości|  
    |-|-|  
    |Nazwa|Resetuj korzystania z systemu partycji dysku GPT|  
    |Opis|Zezwalaj na wszystkie kolejne zadania Format i partycji sekwencji kroki, aby używać systemu partycji dysku określonego przez system BIOS.|  
    |Zmienną sekwencji zadań|OSDDiskType|  
    |Wartość||  

    > [!NOTE]
    >  Pozostaw wartość **OSDDiskType** właściwości wprowadzone w **wartość** puste.  

#### <a name="domain-join-fails-due-to-default-variable-values"></a>Przyłączanie do domeny kończy się niepowodzeniem z powodu domyślnych wartości zmiennych  
 Gdy pomijanie danych wejściowych członkostwo w domenie wartości na **szczegóły komputera** strona kreatora w Kreatorze wdrażania (przy użyciu **SkipDomainMembership** właściwości), wartości  **DomainAdminDomain**, **DomainAdminUser**, i **DomainAdminPassword** właściwości są ustawione na wartości domyślne i nie może sprzężenia właściwości domeny na komputerze docelowym. Ten problem może być spowodowane nie można dodać wartości tych właściwości w pliku CustomSettings.ini lub w bazie danych zestawu MDT.  

 OBEJŚCIE PROBLEMU: Określ co najmniej jedną z następujących właściwości w pliku CustomSettings.ini lub zestaw MDT bazy danych:  

-   **DomainAdminDomain**  

-   **DomainAdminUser**  

-   **DomainAdminPassword**  

 Rozważmy na przykład poniższy fragment pliku CustomSettings.ini:  

```  
SkipDomainMembership=YES  
DomainAdminDomain=Contoso  
JoinDomain=Contoso.com  
```  

 Określenie jednego z tych właściwości umożliwi użytkownikowi wprowadzanie wartości członkostwo domeny na **szczegóły komputera** strona kreatora w Kreatorze wdrażania.  

> [!NOTE]
>  Można również całkowicie pominąć **szczegóły komputera** strona kreatora, podając wszystkie właściwości wymienionych w pliku CustomSettings.ini lub w bazie danych zestawu MDT. Aby uzyskać więcej informacji, zobacz sekcję "Dostarczanie właściwości dla pominięte wdrożenie stron kreatora," w dokumencie MDT *odwołanie do zestawu narzędzi*.  

#### <a name="user-data-may-not-be-restored-from-usb"></a>Nie można przywrócić dane użytkownika z dysku USB  
 Nie można przywrócić dane migracji stanu użytkownika podczas zapisywania danych migracji stanu użytkownika na dysku USB. Jest to spowodowane przez zmianę na literę dysku USB podczas procesu wdrażania.  

 OBEJŚCIE PROBLEMU: Brak  

#### <a name="user-mapped-network-drive-z-is-not-restored"></a>Użytkownik zamapowany dysk sieciowy, który nie jest przywracana Z:  
 Tło pulpitu użytkownika, a nie dyski sieciowe zostaną przywrócone w scenariuszu wdrażania Odśwież komputer. Może to być spowodowane, gdy użytkownik ma zamapowany na dysk Z dysku sieciowym. Po zakończeniu **podsumowanie wdrożenia** okno dialogowe tło pulpitu użytkownika zostaną przywrócone. Jednak użytkownik może być konieczne ponowne utworzenie mapowania dysku Z.  

 OBEJŚCIE PROBLEMU: Brak  

#### <a name="bare-metal-deployment-fails-with-fixed-disk-usb-flash-drive-on-uefi-system"></a>Wdrożenia bez systemu operacyjnego nie powiodło się "stały dysk" dysk flash USB w systemie UEFI  
 Podczas przeprowadzania wdrożenia bez systemu operacyjnego, na podstawie nośnika na Unified Extensible Firmware interfejsu (UEFI) systemu za pomocą nowszej USB flash dysku wykrytego jako "dysk stały" UFD wykrycia jako dysk 1 (wstępnie przypisany literą dysku C) i wewnętrzny dysk twardy jest dysk 0 na partycje. Po wewnętrzny dysk twardy jest podzielona na partycje i sformatowany, jest taka, że jest parametr OSDisk C i UFD ponownego przypisywania litery dysku W. Wdrożenie zakończy się niepowodzeniem na etapie kopiowania skryptu.  

 OBEJŚCIE PROBLEMU: Uruchom ponownie komputer i uruchomić nowe wdrożenie. Zostanie OSDisk można przypisać literę dysku C, zostanie UFD można przypisać D i będzie wdrożenie nadal pomyślnie.  

#### <a name="lti-progress-on-the-windows-81-desktop-is-not-visible-from-the-start-screen"></a>LTI postępu na pulpicie Windows 8.1 nie jest widoczny na ekranie startowym  
 Instalacji lite touch Installation (LTI) będzie automatycznie logować się jako administrator lokalny, aby kontynuować sekwencję zadań, jednak Windows 8.1 domyślnie, zaloguj się do ekranu startowego. LTI uruchamia przy logowaniu zgodnie z oczekiwaniami, ale wskaźnik postępu jest wyświetlany tylko na pulpicie.  

 OBEJŚCIE PROBLEMU: Istnieją dwa możliwe obejścia. Najpierw użytkownika za pomocą konsoli można kliknij ikony pulpitu na ekranie startowym, aby wyświetlić postęp LTI.  

 Po drugie, można dodać następującego polecenia do sekcji Unattend.xml FirstLogonCommands, aby włączyć ustawienie zasad grupy, **przejść do pulpitu zamiast uruchamiania przy logowaniu się w**.  

```  
<FirstLogonCommands>  
  <SynchronousCommand wcm:action="add">  
    <CommandLine>wscript.exe %SystemDrive%\LTIBootstrap.vbs</CommandLine>  
    <Description>Lite Touch new OS</Description>  
    <Order>1</Order>  
  </SynchronousCommand>  
  <SynchronousCommand wcm:action="add">  
    <CommandLine>cmd /c reg add "HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows\Explorer" /v GoToDesktopOnSignIn /t REG_DWORD /d 00000001 /f </CommandLine>  
    <Description>GoToDesktopOnSignIn</Description>  
    <Order>2</Order>  
  </SynchronousCommand>   </FirstLogonCommands>  
```  

> [!NOTE]
>  tylko **drugi** SynchronousCommand element jest dodawany; pierwszy będzie już istnieje w szablonie Unattend.xml  

 Innym mechanizmem musi również później usunąć ustawienie tymczasowego, takie jak zasady grupy usługi Active Directory lub usunięcie klucza rejestru później w sekwencji zadań. Na przykład  

 ![Zestawu MDT 2013 Release Notes obrazu 2](media/MDT2013ReleaseNotesImage2.png "MDT2013ReleaseNotesImage2")  

### <a name="known-issues-for-all-configuration-manager-deployments"></a>Znane problemy dotyczące wszystkich wdrożeń programu Configuration Manager  
 Poniżej przedstawiono listę znanych problemów, które odnoszą się do wdrożenia ZTI i UDI, korzystające z programu System Center 2012 R2 Configuration Manager:  

#### <a name="default-os-image-installed-to-d-drive"></a>Domyślny obraz systemu operacyjnego zainstalowana dysku D:  
 Importowanie domyślnego obrazu systemu operacyjnego (install.wim) i wdrażanie w ramach sekwencji zadań ZTI spowoduje systemu Windows można zainstalować na dysku D: zamiast standardowego dysku C:.  

 OBEJŚCIE PROBLEMU: Ustaw zmienną sekwencji zadań OSDPreserveDriveLetter do pustej wartości domyślnych wartość False.  

#### <a name="bitlocker-tasks-fails-during-zti"></a>Funkcja BitLocker zadań kończy się niepowodzeniem podczas ZTI  
 **UILanguage** podczas używania ZTIBde.wsf w sekwencji zadań ZTI musi zostać ustawiona zmienna sekwencji zadań. W przeciwnym razie ZTIBde.wsf zakończy się niepowodzeniem.  

 OBEJŚCIE PROBLEMU: Brak  

#### <a name="the-task-sequence-fails-when-local-administrator-accounts-exist"></a>Sekwencja zadań zakończy się niepowodzeniem, gdy istnieją konta administratora lokalnego  
 Odświeżanie komputera za pomocą ZTI i UDI sekwencji zadań zakończy się niepowodzeniem, gdy konta administratora lokalnego na komputerze. Sekwencje zadań również zakończyć się niepowodzeniem podczas domyślnie **Przechwyć stan użytkownika** krok ma **Przechwyć wszystkie profile użytkowników z opcjami standardowymi** wybrane, ale domyślnie **Przywróć stan użytkownika** krok ma **Przywróć profile użytkowników komputera lokalnego** wyczyszczone pole wyboru i programu Configuration Manager nie może migrować nowych kont bez przypisywania do nich haseł.  

 OBEJŚCIE PROBLEMU: Ręcznie zmodyfikować sekwencję zadań, wybierając opcję przeprowadzenia migracji kont lokalnych i określ hasło do użycia przy użyciu lokalnego konta. Aby uzyskać więcej informacji, zobacz [Przechwyć stan użytkownika](http://technet.microsoft.com/library/bb680924.aspx).  

### <a name="known-issues-for-zti-deployments-only"></a>Znane problemy dotyczące ZTI tylko w przypadku wdrożeń  
 Oto lista znanych problemów, które dotyczą tylko wdrożenia ZTI.  

#### <a name="installing-chinese-windows-7-prompts-for-user-input"></a>Instalowanie języka chińskiego systemu Windows 7 monit o podanie danych wejściowych użytkownika  
 Podczas wdrażania systemu Windows 7 z języka chińskiego, proces instalacji zatrzymuje oczekiwanie na dane wejściowe użytkownika. Przyczyną jest błąd w pliku Lang.ini w systemie Windows 7.  

 OBEJŚCIE PROBLEMU: Zaktualizuj plik Lang.ini, co zostało przedstawione poniżej.  

 Oryginalny plik Lang.ini:  

```  
[Available UI Languages]  
zh-CN = 3  

[Fallback Languages]  
zh-CN = en-us  
```  

 Plik Lang.ini po modyfikacji:  

```  
zh-CN = 2  
en-us = 3  

[Fallback Languages]  
zh-CN = en-us  
```  

#### <a name="restore-user-state-step-is-skipped-during-replace-scenario"></a>Przywróć stan użytkownika krok zostanie pominięty podczas scenariusza zamiany  
 W przypadku wdrażania komputera Zastąp **Przywróć stan użytkownika** krok sekwencji zadań jest pomijane, jeśli **OSDStateStorePath** właściwości ustawiono nieprawidłowy lokalnej lub ścieżki Universal Naming Convention.  

 OBEJŚCIE PROBLEMU: Ustaw **USMTLocal** właściwości na wartość TRUE. Dzięki temu wymusza UserState.wsf ZTI rozpoznać ścieżki **OSDStateStorePath** właściwości. Jest to spowodowane pomijany kroku sekwencji zadań żądanie przechowania stanu i poprzednie wartości w **OSDStateStorePath** właściwości są zachowywane.  

#### <a name="the-task-sequence-may-fail-with-separate-system-or-active-partitions"></a>Sekwencja zadań może się nie powieść z oddzielnym systemie lub aktywnych partycjach  
 Ten dysk jest inny niż dysk, na którym znajduje się system operacyjny Windows nie będzie przypisać literę dysku System lub aktywną partycję. Jeśli największy partycji jest również System lub aktywną partycję, sekwencja zadań może się nie powieść wznowić w nowym systemie operacyjnym.  

 OBEJŚCIE PROBLEMU: Upewnij się, że System "lub" aktywny partycja nie jest większy niż partycji systemu operacyjnego, korzystając z wielu partycji.  

#### <a name="usmt-targetwindows7-switch-fails-in-offline-scenario"></a>Narzędzie USMT /TargetWindows7 przełącznika nie powiedzie się w scenariuszu w trybie offline  
 Wystąpił następujący błąd w scanstate.log podczas wykonywania scenariusz wdrażania komputer odświeżania zestawu MDT podczas przechwytywania informacji o stanie użytkownika przy użyciu funkcji migracji w trybie offline narzędzia USMT za pomocą ZTI:  

```  
USMT error code 27: [gle=0x00000006]  
```  

 OBEJŚCIE PROBLEMU: Brak; jest to znany problem przy użyciu narzędzia USMT.  

#### <a name="configure-adds-step-does-not-save-correctly"></a>Skonfiguruj DODAJE krok nie poprawnie zapisać.  
 Przy użyciu **skonfigurować DODAJE** poziomów funkcjonalności ustawioną w systemie Windows Server 2008 spowoduje krok, właściwości zaawansowane, aby ustawić lasu i poziomów funkcjonalności domeny systemu Windows Server 2003 lub Windows Server 2008 R2.  

 OBEJŚCIE PROBLEMU: Ustaw DomainLevel = 5 i/lub ForestLevel = 5 w CustomSettings.ini. Zobacz odwołanie do zestawu narzędzi, aby uzyskać więcej informacji na temat tych ustawień.  

#### <a name="server-task-sequence-template-fails-on-uefi-system"></a>Szablon sekwencji zadań serwera nie powiedzie się w systemie UEFI  
 Po zintegrowaniu przy użyciu szablonu sekwencji zadań zestawu MDT 2013 serwera w programie System Center 2012 R2 Configuration Manager, wdrożenia zakończy się niepowodzeniem w niektórych systemach Unified Extensible Firmware Interface (UEFI), podczas uruchamiania **Format i partycji dysku (UEFI)**  krok z powodu błędu aplikacji w OsdDiskPart.exe podobny do następującego: "Instrukcja pod 0x6e2c8374 odwołuje się do pamięci w 0x00000120. Nie można odczytać pamięci. Kliknij przycisk OK, aby zakończyć program. "  

 OBEJŚCIE PROBLEMU: Żadna ze scenariuszem ZTI. LTI lub tylko do programu ConfigMgr scenariusze działać.  

###  <a name="KnownIssuesLTIZTI"></a>Znane problemy dotyczące LTI i wdrożenia ZTI  
 Poniżej znajduje się lista znanych problemów, które odnoszą się do wdrożenia zarówno LTI, jak i ZTI.  

#### <a name="roles-and-features-requiring-multiple-restarts-cause-problems-for-task-sequences"></a>Role i funkcje wymagające wielu problemów Przyczyna ponownego uruchomienia sekwencji zadań  
 Instalowanie ról lub funkcji, takich jak **MICROSOFT-HYPER-V-ALL** lub **licencji usług pulpitu zdalnego serwera** które wymagają wielokrotne ponowne uruchomienie lub są zależne od takich ról lub funkcji może spowodować problemy podczas zadania Sekwencja i należy unikać.  

 OBEJŚCIE PROBLEMU: Zainstalować odpowiednią rolę lub funkcję na komputerze odniesienia i przechwycić obraz ma odpowiednią rolę lub funkcję już zainstalowana.  

#### <a name="multiple-logs-created-during-deployment"></a>Wiele dzienników utworzonych podczas wdrażania  
 Podczas procesu Scanstate i Loadstate wielu kopii plików dziennika można tworzyć, na przykład BDD.log, BDD log (1), ZTIUserstate.log i ZTIUserstate log (1).  

 OBEJŚCIE PROBLEMU: Podczas uruchamiania Scanstate i Loadstate, z wyjątkiem plików dziennika lub katalogów dziennika.  

###  <a name="KnownIssuesUDI"></a>Znane problemy dotyczące wdrożeń UDI  
 Poniżej znajduje się lista znanych problemów, które odnoszą się do wdrożeń UDI.  

#### <a name="udi-wizard-hides-no-data-option-on-user-state-page-in-capture-mode"></a>Kreator UDI ukrywa opcja braku danych na stronie stanu użytkownika w trybie przechwytywania  
 Na stronie wartości parametru UserState nie można dostosować za pomocą przycisk radiowy "Braku danych" gdy jest on w tryb przechwytywania.  

 OBEJŚCIE PROBLEMU: Otwórz w Notatniku plik konfiguracji kreatora i dodaj następującą właściwość do sekcji strony "Wybierz miejsce docelowe" działający w trybie przechwytywania:  

```  
<Setter Property="DisplayNoDataInCaptureMode">true</Setter>  
```  

 Na przykład  

```  
<Setter Property="DataSourceText">Please select a location where user data will be captured.</Setter>  
<Setter Property="Format">disable</Setter>  
<Setter Property="FormatPrompt">disable</Setter>  
<Setter Property="MinimumDriveSize">10</Setter>  
<Setter Property="State">Capture</Setter>  
<Setter Property="NetworkDrive">n:</Setter>  
<Setter Property="DisplayNoDataInCaptureMode">true</Setter>  
```  

 Aby ukryć dane"No" przycisk radiowy powyżej wartości FALSE lub usuń wpis.  

#### <a name="the-time-and-currency-language-format-is-not-configured"></a>Format godziny i waluty języka nie jest skonfigurowany.  
 Format języka godziny i waluty nie skonfigurowano poprawnie na komputerze docelowym, mimo że wybrano właściwy język w **format godziny i waluty (ustawienia regionalne)** listy na **języka** UDI Strona kreatora. Ten problem może być spowodowane przez błąd w pliku UDIWizard.wsf. Plik UDIWizard.wsf znajduje się w *mdt_files*folderu \Scripts (gdzie *mdt_files* jest folder, który jest źródłem dla zestawu MDT pliki pakietu, który używa sekwencji zadań).  

 OBEJŚCIE PROBLEMU: Aby naprawić ten błąd w pliku UDIWizard.wsf, wykonaj następujące czynności:  

1.  Edytuj plik UDIWizard.wsf, który znajduje się w *mdt_files*folderu \Scripts (gdzie *mdt_files* jest folder, który jest źródłem dla zestawu MDT pliki pakietu, który używa sekwencji zadań).  

2.  Usuń następujący wiersz z pliku UDIWizard.wsf:  

    ```  
    oEnvironment.Item("UserLocale") = oEnvironment.Item("InputLocale")  
    ```  

    > [!NOTE]
    >  Tekst wymienionych powyżej jest jeden wiersz w pliku UDIWizard.wsf. Wszelkie zawijania jest spowodowany przez ograniczenia formatowania dokumentu.  

3.  Zapisz plik UDIWizard.wsf.  

4.  Aktualizuj punkty dystrybucji z zmodyfikowanej wersji zestawu MDT pakiet plików, który zawiera zaktualizowanego pliku UDIWizard.wsf.  

#### <a name="applications-do-not-appear-after-added"></a>Aplikacje nie są wyświetlane po dodaniu  
 Aplikacji nie widać w Projektancie UDI lub UDI kreatora po ich dodaniu w Projektancie UDI. Ten problem może wystąpić, ponieważ nie wybrano grupy aplikacji docelowej przed dodaniem aplikacji.  

 OBEJŚCIE PROBLEMU: Wybierz grupy aplikacji docelowej przed dodaniem aplikacji.  

#### <a name="applications-may-not-be-installed"></a>Aplikacje mogą nie być zainstalowane.  
 Instalator aplikacji (AppInstall.exe) nie może poprawnie zainstalować aplikacje, które zostały wdrożone dla użytkowników. Ten problem może być spowodowany **Zezwalaj użytkownikowi na definiowanie urządzeń podstawowych** ustawiany **nr**.  

 OBEJŚCIE PROBLEMU: Ustaw wartość **Zezwalaj użytkownikowi na definiowanie urządzeń podstawowych** do **tak**. **Zezwalaj użytkownikowi na definiowanie urządzeń podstawowych** formant znajduje się w **koligacja użytkowników i urządzeń** sekcji w **ustawienia domyślne** okno dialogowe, w Overview\Client W węźle ustawienia **administracji** okienko nawigacji w konsoli programu Configuration Manager.  

#### <a name="deployment-time-is-not-correct-during-stand-alone-media-deployment"></a>Podczas wdrażania nośników autonomicznych czasu wdrożenia jest nieprawidłowy  
 Jeśli korzystasz z nośnika autonomicznego, wartość wyświetlana dla **czas wdrażania** przez **OSDResults** po zakończeniu wdrożenia nie jest gwarantowana prawidłowe, ponieważ połączenie sieciowe nie zakłada się, że dostępne, gdy przy użyciu nośników autonomicznych. W związku z tym zegara system podstawowych operacji wejścia/wyjścia (BIOS) na komputerze nie można zsynchronizować nieprawidłową godzinę. W niektórych przypadkach czas wdrażania mogą być wyświetlane ujemny number, ponieważ występuje, gdy czas dostępne ze środowiska Windows PE na początku nieprawidłowego ustawienia z wartością, która faktycznie późniejsza od czasu, jaką zakończeniu wdrożenia.  

 OBEJŚCIE PROBLEMU: Brak  

#### <a name="osddomainname-variable-does-not-work-as-expected"></a>Zmienna zmiennej OSDDomainName nie działa zgodnie z oczekiwaniami  
 W przypadku UDI **zmiennej OSDDomainName** zmienną sekwencji zadań jest rozróżniana wielkość liter.  

 OBEJŚCIE PROBLEMU: Podczas ustawiania **zmiennej OSDDomainName** wartość za pomocą kroku sekwencji zadań lub CS.ini, musi być dokładnego dopasowania do domeny wartość ustawiona w pliku konfiguracji UDI.
