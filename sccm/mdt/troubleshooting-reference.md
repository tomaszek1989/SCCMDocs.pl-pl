---
title: Rozwiązywanie problemów z zestawu MDT
titleSuffix: Microsoft Deployment Toolkit
description: 'Rozwiązywanie problemów z odwołania dla programu Microsoft Deployment Toolkit '
ms.date: 09/09/2016
ms.prod: configuration-manager
ms.technology:
- configmgr-osd
ms.topic: article
ms.assetid: 91a7a69a-deac-4b0f-aac9-b7bd187c53fb
author: aczechowski
ms.author: aaroncz
manager: angrobe
ms.openlocfilehash: efb65086878a46bfb3485fdd8b0be6f613225261
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/27/2018
---
# <a name="troubleshooting-reference-for-the-microsoft-deployment-toolkit"></a>Rozwiązywanie problemów z odwołania do zestawu narzędzi firmy Microsoft do wdrażania
 Wdrażanie systemów operacyjnych i aplikacji, a także migracji stanu użytkownika może być trudne pozwala, nawet wtedy, gdy są wyposażone odpowiednich narzędzi i wskazówek. To odwołanie, który jest częścią programu Microsoft® Deployment Toolkit (MDT) 2013, dostarcza informacji na temat obecnie znane problemy, możliwe obejścia tych problemów i wskazówki dotyczące rozwiązywania problemów.  

> [!NOTE]
>  W tym dokumencie *Windows* ma zastosowanie do systemów operacyjnych Windows 8.1, Windows 8, Windows 7, Windows Server 2012 R2, Windows Server 2012 i Windows Server 2008 R2, chyba że określono inaczej. Zestaw MDT nie obsługuje wersji na podstawie procesora ARM systemu Windows. Podobnie *MDT* odwołuje się do zestawu MDT 2013, chyba że określono inaczej.  

> [!NOTE]
>  Microsoft Diagnostics and Recovery Toolset (DaRT) zawiera zaawansowanych narzędzi do odzyskiwania i rozwiązywanie problemów z komputerów klienckich, które nie są uruchamiane lub stać się niestabilny. DaRT można użyć, aby ustalić przyczynę awarii, utracone pliki i tak dalej. Umożliwia także DaRT rozwiązywania problemów z narzędziem podczas projektowania i wdrażania systemu operacyjnego Windows. Na przykład, jeśli wbudowanych obrazu nie powiedzie się poprawnie, możesz uruchomić komputera klienckiego, zawierający obraz przy użyciu dysku Naprawczego dowódcy — diagnostycznych środowiska. Następnie można eksplorować dysku twardego na komputerze klienckim, wyświetlanie dziennika zdarzeń, usunąć aktualizacje, zmiany ustawień systemu operacyjnego i itd. DaRT jest częścią pakietu Microsoft Desktop Optimization Pack w celu zapewnienia bezpieczeństwa oprogramowania. Aby dowiedzieć się więcej na temat DaRT, zobacz [ http://www.microsoft.com/windows/enterprise/products-and-technologies/mdop/dart.aspx ](http://www.microsoft.com/windows/enterprise/products-and-technologies/mdop/dart.aspx).  

## <a name="understanding-logs"></a>Opis dzienników  
 Przed rozpoczęciem skuteczne rozwiązywanie problemów z zestawu mdt musisz mieć przejrzysty wiele plików log, używane podczas wdrażania systemu operacyjnego. Gdy wiesz, plików dziennika, które się dowiedzieć, jakie warunku błędu oraz porę, problemów, które zostały raz brzmieć tajemniczo i trudne do zrozumienia mogą stać się wyczyść i zrozumieć.  

 Format pliku dziennika zestawu MDT jest przeznaczony do odczytu przez (trace32) zostało, która jest częścią programu System Center Configuration Manager 2007 Toolkit V2, można pobrać z [Microsoft Download Center](http://www.microsoft.com/download/details.aspx?id=9257). Dzienniki również mogą być odczytywane przez Configuration Manager Trace Log Tool (CMTrace), która jest dostępna w programie System Center 2012 Configuration Manager i nowszych wersjach. Należy użyć tych narzędzi, jeśli to możliwe odczytać pliki dziennika, ponieważ jego znacznie ułatwia wyszukiwanie błędów.  

 Pozostałej części tej sekcji opisano szczegółowo pliki dziennika utworzone podczas wdrażania, a także podczas instalacji systemu Windows. Ta sekcja zawiera również przykłady, kiedy należy używać plików do rozwiązywania problemów.  

### <a name="mdt-logs"></a>Dzienniki zestawu MDT  
 Podczas uruchamiania skryptu każdego zestawu MDT automatycznie tworzy pliki dziennika. Nazwy plików dziennika zgodna z nazwą skryptu — na przykład ZTIGather.wsf tworzy plik dziennika o nazwie *ZTIGather.log*. Każdy skrypt aktualizuje również typowe wzorca plik dziennika (BDD.log), który agreguje zawartość pliki dziennika utworzone przez skrypty zestawu MDT. Pliki dziennika zestawu MDT znajdują się w C:\MININT\SMSOSD\OSDLOGS podczas procesu wdrażania. W zależności od typu wdrożenia, które są wykonywane pliki dziennika zostaną przeniesione z chwilą zakończenia wdrożenia %WINDIR%\SMSOSD lub % WINDIR%\TEMP\SMSOSD. W przypadku wdrożeń Lite Touch Installation (LTI) dzienniki uruchomienie w C:\MININT\SMSOSD\OSDLogs. Są one umieszczane w %WINDIR%\TEMP\DeploymentLogs po zakończeniu przetwarzania sekwencji zadań.  

 Zestaw MDT utworzy następujące pliki dziennika:  

-   **BDD.log**. Plik dziennika zestawu MDT zagregowane, który jest kopiowany do lokalizacji sieciowej na końcu wdrożenia, jeśli określono **SLShare** właściwość w pliku Customsettings.ini.  

-   **LiteTouch.log**. Ten plik jest tworzony podczas wdrożenia LTI. Znajdują się w %WINDIR%\TEMP\DeploymentLogs chyba że zostanie **/debug:true** opcji.  

-   **Scriptname*.log**. Ten plik jest tworzony za pomocą skryptu każdego zestawu MDT. *Scriptname* reprezentuje nazwę danego skryptu.  

-   **SMSTS.log**. Ten plik jest tworzony przez program Sequencer zadań oraz opis wszystkich transakcji sekwencjonowania zadań. W zależności od scenariusza wdrożenia może znajdować się w folderze % TEMP %, % WINDIR%\System32\ccm\logs lub C:\\\_SMSTaskSequence lub C:\SMSTSLog.  

-   **Wizard.log**. Kreatorzy wdrożenia tworzenia i aktualizacji tego pliku.  

-   **WPEinit.log**. Ten plik jest tworzony podczas inicjowania środowiska Preinstalacyjnego systemu Windows i jest przydatna do rozwiązywania problemów z błędami podczas uruchamiania systemu Windows PE.  

-   **DeploymentWorkbench_*identyfikator*log**. Ten plik dziennika jest tworzony w folderze % temp % po określeniu **/ Debug** podczas uruchamiania konsoli Deployment Workbench.  

### <a name="configuration-manager-operating-system-deployment-logs"></a>Dzienniki wdrożenia systemu operacyjnego programu Configuration Manager  
 Aby uzyskać informacje dotyczące systemu operacyjnego wdrożenia pliki dzienników są tworzone przez program Microsoft System Center 2012 R2 Configuration Manager, zobacz [techniczne dla plików dziennika w programie Configuration Manager](http://technet.microsoft.com/library/hh427342.aspx).  

 Podczas uruchamiania systemu Windows użytkownika stanu migracji narzędzia (USMT), zestawu MDT automatycznie dodaje opcji rejestrowania, aby zapisać pliki dziennika narzędzia USMT do lokalizacji pliku dziennika zestawu MDT. Pliki dziennika i kiedy są tworzone są następujące:  

-   **USMTEstimate.log**. Tworzone podczas szacowania wymagań dotyczących narzędzia USMT  

-   **USMTCapture.log**. Utworzony przez narzędzie USMT podczas przechwytywania danych  

-   **USMTRestore.log**. Utworzony przez narzędzie USMT podczas przywracania danych  

 Skrypt ZeroTouchInstallation.vbs automatycznie skanuje pliki narzędzia USMT postępu dziennik błędów i ostrzeżeń. Skrypt generuje identyfikator zdarzenia 41010 do programu Microsoft System Center Operations Manager z podsumowaniem następujące (gdzie *usmt_type* jest **szacowania**, **SCANSTATE**, lub  **LOADSTATE**; *error_count* jest to całkowita liczba błędów; i *warning_count* jest to całkowita liczba ostrzeżeń znaleziono):  

```  
ZTI USMT <usmt_type> reported <error_count> errors and <warning_count> warnings  
```  

 Jeżeli liczba błędów jest większa niż 0, to zdarzenie jest typem błędu. Jeśli liczba ostrzeżeń jest większa niż 0 bez błędów, zdarzenie jest typem ostrzeżenie. W przeciwnym razie zdarzenie jest typem informacyjny.  

## <a name="identifying-error-codes"></a>Identyfikowanie kody błędów  
Tabela 1 zawiera listę kodów błędów, tworzonych przez skrypty MDT i opisano poszczególne kody błędów. Te kody błędów są rejestrowane w pliku BDD.log.  

### <a name="table-1-error-codes-and-their-description"></a>Tabela 1. Kody błędów wraz z opisami  

|**Kod błędu:**|**Opis**|  
|-|-|  
|5201|Nie można nawiązać połączenia z udziałem wdrożenia. Wdrożenie nie będzie kontynuowana.|  
|5203|Nie można nawiązać połączenia z udziałem wdrożenia. Wdrożenie nie będzie kontynuowana.|  
|5205|Nie można nawiązać połączenia z udziałem wdrożenia. Wdrożenie nie będzie kontynuowana.|  
|5206|Kreator wdrażania zostało anulowane lub zakończyło się niepowodzeniem. Wdrożenie nie będzie kontynuowana.|  
|5207|Nie można nawiązać połączenia z udziałem wdrożenia. Wdrożenie nie będzie kontynuowana.|  
|5208|**DeploymentType** nie jest ustawiona. Należy ustawić wartość niektórych **SkipWizard**.|  
|5208|Nie można odnaleźć programu Sequencer zadań programu SMS. Wdrożenie nie będzie kontynuowana.|  
|5400|Tworzenie obiektu: **Ustaw *class_instance* = New *class_name***|  
|5490|Create MSXML2.DOMDocument.|  
|5495|Create MSXML2.DOMDocument.ParseErr.ErrCode.|  
|5496|LoadControlFile.FindFile: *ConfigFile*|  
|5601|Sprawdź identyfikator guid systemu operacyjnego: OSGUID % istnieje.|  
|5602|Otwórz XML z OSGUID: % OSGUID %.|  
|5610|Sprawdź plik.|  
|5630|Sprawdź plik: *ImagePath*.|  
|5640|Sprawdź plik: *ImagePath*.|  
|5641|FindFile: ImageX.exe.|  
|5643|Znajdź BootSect.exe.|  
|5650|Sprawdzanie katalogu: *Ścieżka_źródłowa*.|  
|5651|Sprawdzanie katalogu: *SourcePath*\Platform.|  
|5652|FindFile: bootsect.exe.|  
|6001|Sprawdź dysk.|  
|6002|Sprawdź dysk.|  
|6010|Test na TSGUID.|  
|6020|ROBOCOPY zwrócił wartość: *Wartość*.|  
|6021|ROBOCOPY zwrócił wartość: *Wartość*.|  
|6101|Sprawdź, czy plik: *DeployCab*.|  
|6102|Rozwiń pliki narzędzia Sysprep z wdrażania. PLIK CAB.|  
|6111|Uruchom Sysprep.exe.|  
|6121|Uruchom program Sysprep.|  
|6191|Badanie **CloneTag** w rejestrze, aby sprawdzić Sysprep ukończone.|  
|6192|Badanie **SystemSetupInProgress** w rejestrze, aby sprawdzić Sysprep ukończone.|  
|6401|Autoryzowany serwer DHCP.|  
|6501|Kopia zapasowa komputera nie jest możliwe, nie ma ścieżki sieciowej (**BackupShare**, **BackupDir**) określony.|  
|6502|BŁĄD — nie można zlokalizować narzędzia IMAGEX, nie można wykonać kopii zapasowej.|  
|6601|GetObject (... głównego/wmi:BCDStore).|  
|6602|BCD. OpenStore (*BCDStore*).|  
|6701|Funkcje ochrony skonfigurowane.|  
|6702|Przenieść pliki rozruchowe.|  
|6703|Utwórz partycję BDE.|  
|6704|Defragmentacji dysku.|  
|6705|Zmniejszanie dysku.|  
|6706|Testowanie dla więcej niż 1 partycji.|  
|6707|Tworzenie plików rozruchowych.|  
|6708|Szyfrowanie dysku.|  
|6709|Połącz się z dostawcą MicrosoftVolumeEncryption WMI.|  
|6710|Szyfrowanie dysku.|  
|6711|**ProtectKeyWithTPM**.|  
|6712|**ProtectKeyWithTPMAndPIN**.|  
|6713|**ProtectKeyWithTPMAndStartupKey**.|  
|6714|Zapisz klucz zewnętrzny w pliku.|  
|6715|Chronić za pomocą klucza zewnętrznego.|  
|6716|Zapisz klucz zewnętrzny w pliku.|  
|6717|Ochrony klucza z numerycznym hasłem.|  
|6718|**GetKeyProtectorNumberialP@ssword.**|  
|6718|Zapisz hasło do pliku.|  
|6719|Otwórz *wartości PasswordFile*.|  
|6720|Szyfrowania dysku.|  
|6721|Otwórz *DiskPartFile*.|  
|6722|Utwórz partycję.|  
|6723|Pobierz istniejący dysk BDE.|  
|6724|Otwórz *DiskPartFile*.|  
|6727|Próba otwarcia *DiskPartFile*.|  
|6729|Utwórz plik tekstowy *DiskPartFile*.|  
|6730|Wykonanie **cmd /c DISKPART. EXE /s *DiskPartFile* >> *LogPath*\ZTIMarkActive_diskpart.log 2 > & 1**|  
|6731|Znajdź bcdboot.exe.|  
|6732|Połączyć z dostawcą TPM firmy Microsoft.|  
|6733|Pobierz wystąpienia łącznika TPM klasy dostawcy.|  
|6734|Pobierz wystąpienia łącznika TPM.|  
|6735|Sprawdź, czy jest włączony moduł TPM.|  
|6736|Sprawdź, czy moduł TPM jest uaktywniony.|  
|6737|Sprawdź, czy moduł TPM jest właścicielem.|  
|6738|Sprawdź, czy jest dozwolone własność modułu TPM.|  
|6739|Sprawdź, czy jest włączony moduł TPM.|  
|6740|Sprawdź, czy moduł TPM jest uaktywniony.|  
|6741|Sprawdź, czy moduł TPM jest właścicielem i własność jest dozwolone.|  
|6741|Ustawianie hasła właściciela modułu TPM|  
|6742|Właściciela modułu TPM P@ssword ustawioną **AdminP@ssword**.|  
|6743|Ustawianie właściciela modułu TPM P@ssword wartości.|  
|6744|Sprawdź, czy jest włączony moduł TPM.|  
|6745|Sprawdź właściciela modułu TPM.|  
|6746|Sprawdź, czy pary kluczy poręczenia.|  
|6747|Sprawdź, czy moduł TPM jest uaktywniony.|  
|6748|Sprawdź, czy jest dozwolone własność modułu TPM.|  
|6749|Konwertuj właściciela p@ssword do autoryzacji właściciela.|  
|6750|Utworzenie pary kluczy poręczenia.|  
|6751|Zmień właściciela autoryzacji.|  
|6752|Uruchom **Cmd**.|  
|6753|Sprawdzanie poprawności modułu TPM.|  
|6754|Pobierz wystąpienia BDE.|  
|6755|Ochrony klucza moduł TPM.|  
|6756|Sprawdź, czy nośnik wymienny, aby skonfigurować. **ProtectKeyWithTpmAndStartupKey**.|  
|6757|Ochrony klucza moduł TPM i klucz uruchomienia.|  
|6758|Poszukaj BDE numeru pin.|  
|6759|Ochrony klucza modułu TPM i numeru Pin.|  
|6760|Znajdź nośnik wymienny dla **BDEKeyLocation**.|  
|6761|Chronić za pomocą klucza zewnętrznego.|  
|6762|Odzyskiwanie P@ssword zapisywany *wartości PasswordFile*.|  
|6764|Konfigurowanie zasad funkcji BitLocker.|  
|7000|Nie można zlokalizować ZTIConfigure.xml; zostanie przerwany.|  
|7001|Wyszukiwanie instalacji nienadzorowanej plik odpowiedzi.|  
|7100|Błąd — ten skrypt należy uruchomić tylko w pełnej wersji systemu operacyjnego.|  
|7101|Błąd — za mało wartości dostarczane na potrzeby generowania pliku odpowiedzi DCPromo.|  
|7102|Błąd — wymagane właściwości do utworzenia nowej repliki kontrolera domeny nie zostały określone.|  
|7103|Błąd — wymagane właściwości do utworzenia nowej domeny podrzędnej nie zostały określone.|  
|7104|Błąd — wymagane właściwości do utworzenia nowego lasu nie zostały określone.|  
|7105|Błąd — wymagane właściwości do utworzenia nowego lasu nie zostały określone.|  
|7200|Nie można skonfigurować serwer DHCP, ponieważ usługa nie jest zainstalowana.|  
|7201|Nie można odczytać szczegółów zakresu; `GetScopeDetails()` nie powiodło się.|  
|7202|Za mało wartości określona na potrzeby tworzenia zakresu.|  
|7203|Za mało wartości ustawiono zakres adresów IP w tym zakresie.|  
|7204|Nie określono wartości dla zakresu wykluczeń.|  
|7300|Nie można wydać polecenia DNS.|  
|7700|Nie scenariusz nowego komputera; Kończenie partycji dysku.|  
|7701|Dysk nie jest wystarczająco duży dla partycji systemu i BDE wymagane = 1,5 GB.|  
|7702|Dysk nie jest wystarczająco duży dla partycji systemu i środowiska WinRE, wymagane = 10 GB.|  
|7703|DeployRoot znajduje się na dysku # *DiskIndex*. Uruchomiony scenariusz OEM: Skip.|  
|7704|Uruchomiony scenariusz OEM: Skip.|  
|7704|Partycje rozszerzone i logiczne są niedozwolone z funkcją BitLocker.|  
|7712|Sprawdź dysk /*woluminu dysku* jest obecny. Format.|  
|7900|Findfile: Microsoft.BDD.PnpEnum.exe.|  
|7901|**AllDrivers.Exists("*GUID*").**|  
|7904|**AllDrivers.Exists("*GUID*").**|  
|9200|Findfile(PkgMgr.exe).|  
|9601|Błąd — zadanie przywracania stanu ZTITatoo powinna być uruchomiona w pełnym systemie operacyjnym; zostanie przerwany.|  
|9701|Niezerowy kod powrotny z narzędzia USMT szacowania, rc = *błąd*.|  
|9702|Przechwytywania stanu użytkownika nie jest możliwe; za mało miejsca na lokalnym i nie określono ścieżki sieciowej (UDShare, UDDir).|  
|9703|Niezerowy kod powrotny z narzędzia USMT przechwytywania, rc = *błąd*.|  
|9704|Brak opcji prawidłowym wierszem polecenia została określona.|  
|9801|Błąd — próby wdrożenia systemu operacyjnego klienta do komputera z systemem operacyjnym serwera.|  
|9802|Błąd — próby wdrożenia systemu operacyjnego serwera na maszynę z systemem operacyjnym klienta.|  
|9803|Błąd - komputer nie ma uprawnień do uaktualnienia (OSInstall =*OSInstall*); Trwa przerywanie.|  
|9804|Błąd — *pamięci* MB pamięci są niewystarczające. Co najmniej *pamięci* MB pamięci jest wymagana.|  
|9805|Błąd — prędkości procesora *ProcessorSpeed* MHz jest niewystarczająca.  Co najmniej *ProcessorSpeed* MHz procesora jest wymagana.|  
|9806|Błąd — za mało miejsca jest dostępne na *dysków*. Dodatkowe *rozmiar* MB jest wymagana.|  
|9807|Błąd — za mało miejsca jest dostępne na *dysków*. Dodatkowe *rozmiar* MB jest wymagana.|  
|9901|Skrypt ZTIWindowsUpdate nie może działać w środowisku Windows PE.|  
|9902|ZTIWindowsUpdate ma uruchomić i nie powiodło się zbyt wiele razy. Liczba = *liczba*.|  
|9903|Nieoczekiwany problem Instalowanie zaktualizowanych Windows Update Agent, rc = *błąd*.|  
|9904|Nie można utworzyć obiektu: **Microsoft.Update.Session**.|  
|9905|Nie można utworzyć obiektu: **Microsoft.Update.UpdateColl**.|  
|9906|Krytyczne pliku *pliku* nie został znaleziony; zostanie przerwany.|  
|10000|Tworzenie obiektu: **Ustaw oLTICleanup = nowy LTICleanup**.|  
|10201|Nie można przyłączyć do domeny *domeny*. Zatrzymywanie instalacji.|  
|10203|FindFile(LTISuspend.wsf).|  
|10204|Uruchom Program *LTISuspend*.|  
|41024|Uruchom narzędzia ImageX.|  
|52012|Wszystkie parametry kreatora nie zostały ustawione.|  

 Wyświetlanie listy 1 zawiera fragment pliku dziennika, która ilustruje sposób znaleźć kod błędu. W tym fragmencie kodu kod błędu zgłoszony to 5001.  

 **Wyświetlanie listy 1. Fragment pliku SMSTS.log, który zawiera kod błędu 5001**  

```  
.  
.  
.  
The operating system installation failed. Please contact your system administrator for assistance.  

The action "Zero Touch Installation - Validation" failed with exit code 5001  
.  
.  
.  

```  

### <a name="converting-error-codes"></a>Konwertowanie kody błędów  
 Wiele kodów błędów w plikach dziennika wydawać się one niezrozumiałe i trudne do skorelowania do warunku błędu. Jednak następujący proces pokazano, jak przekonwertować kod błędu i Uzyskaj przydatne informacje, które mogą ułatwić rozwiązanie problemu.  

 **Problem**: Przechwytywanie obrazu kończy się niepowodzeniem z kodem błędu 0x80070040.  

 **Możliwe rozwiązanie 1**: Podany kod błędu jest w formacie szesnastkowym, który należy przekonwertować na format dziesiętny. Aby to zrobić, należy naukowych Kalkulator i Kalkulator dołączonych do systemów operacyjnych Windows jest dobrze nadają się do tego zadania.  

 **Aby przekonwertować kod błędu:**  

1.  Kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Akcesoria**, a następnie kliknij przycisk **Kalkulator**.  

2.  Z **widoku** menu, kliknij przycisk **wykładniczej**.  

3.  Wybierz **Hex**, a następnie wprowadź cztery ostatnie cyfry kodu — w takim przypadku **0040**, jak pokazano na rysunku 1.  

     ![TroubleshootingReference1](media/TroubleshootingReference1.jpg "TroubleshootingReference1")  
Rysunek 1. Błąd konwersji  

     **Rysunek 1. Błąd konwersji**  

     Zwróć uwagę, że zera wiodące nie są wyświetlane, gdy Kalkulator jest w formacie szesnastkowym.  

4.  Wybierz **gru**.  

     Wartość szesnastkowa *40* jest konwertowana na wartość dziesiętna *64*.  

5.  Otwórz okno wiersza polecenia, wpisz **NET HELPMSG 64**, a następnie naciśnij klawisz ENTER.  

     **NET HELPMSG** polecenia przekształca kod błędu liczbowe w łatwy do rozpoznania tekst. W przypadku kodu błędu podane w tym miejscu tłumaczy "określonej nazwy sieci nie jest już dostępne."  

 Te informacje wskazuje, że problem z siecią może istnieć na komputerze docelowym lub między komputerem docelowym i serwera, na którym znajduje się udział wdrożenia. Te problemy mogą obejmować sterowniki sieciowe nie są poprawnie zainstalowane lub niezgodność dupleksu ustawień i szybkości.  

 **Możliwe rozwiązanie 2:** Użyj narzędzia Microsoft Exchange Server błąd kodu wyszukiwania. To narzędzie wiersza polecenia jest przydatna w z tłumaczenia kodu błędu. Nie jest dostępny do pobrania z [Microsoft Download Center](http://www.microsoft.com/download/details.aspx?id=985).  

### <a name="review-of-sample-logs"></a>Przejrzyj dzienniki próbki  
 Zestaw MDT utworzy plików dziennika, które służy do rozwiązywania problemów w procesie wdrożenia zestawu MDT. Poniższe sekcje zawierają przykłady sposobów użycia pliki dziennika zestawu MDT rozwiązywać proces wdrażania:  

-   Problemy z błędami dostępu do bazy danych MDT (MDT DB), zgodnie z opisem w [błąd dostępu do bazy danych](#FailuretoAccesstheDatabase)  

####  <a name="FailuretoAccesstheDatabase"></a> Błąd dostępu do bazy danych  
 **Problem:** Błąd występuje podczas uruchamiania wdrożenia, który plik CustomSettings.ini, zawierający wiele sekcje i określenie, z **priorytet** właściwości, priorytet każdej sekcji, aby można było przetworzyć. BDD.log zawiera następujące komunikaty o błędach:  

-   ```  
    ERROR - Opening Record Set (Error Number = -2147217911) (Error Description: The SELECT permission was denied on the object 'ComputerAdministrators', database 'AdminDB', schema 'dbo'.)  
    ```  

-   ```  
    ADO error: The SELECT permission was denied on the object 'ComputerAdministrators', database 'AdminDB', schema 'dbo'. (Error #-2147217911; Source: Microsoft OLE DB Provider for SQL Server; SQL State: 42000; NativeError: 229  
    ```  

-   ```  
    ERROR - Unhandled error returned by ZTIGather: Object required (424)  
    ```  

> [!NOTE]
>  Dla uzyskania przejrzystości, powyżej zawartość pliku dziennika już reprezentowane, jak wyglądają będąc wyświetlać za pomocą programu (trace32) zostało.  

 **Możliwe rozwiązania:** Problem, jak wskazano w pierwszym wierszu przykładowy plik dziennika, polega na odmówiono uprawnień do dostępu do bazy danych. W związku z tym skryptu nie można ustanowić bezpiecznego połączenia z bazą danych, prawdopodobnie ponieważ identyfikator użytkownika i hasło nie była możliwa. W związku z tym dostęp do bazy danych podjęto, używając konta komputera. Najprostszym sposobem obejścia tego problemu jest przyznać wszystkim dostęp do odczytu do bazy danych.  

## <a name="troubleshooting"></a>Rozwiązywanie problemów  
 Przed wdrożeniem w\-głębokość procedur rozwiązywania problemów, przejrzyj następujące elementy i upewnij się, że wszystkie skojarzone wymagania zostały spełnione:  

-   Jeśli nie zostały spełnione wszystkie wymagania wstępne dotyczące sprzętu i oprogramowania, może spowodować problemy z instalacją.  

### <a name="application-installation"></a>Instalacja aplikacji  
 Przejrzyj problemy i rozwiązania problemów dotyczących instalacji aplikacji:  

-   Pliki źródłowe instalacji, które są blokowane ze względów bezpieczeństwa, zgodnie z opisem w [zablokowane pliki wykonywalne](#BlockedExecutables)  

-   Utratę łączności sieciowej, zgodnie z opisem w [utraty połączenia sieciowe](#LostNetworkConnections)  

-   Błąd instalacji 30029 podczas instalowania systemu Microsoft Office 2007 lub powiązane pliki, zgodnie z opisem w [pakietu Microsoft Office 2007](#MicrosoftOfficeSystem)  

####  <a name="BlockedExecutables"></a> Zablokowane pliki wykonywalne  
 **Problem:** Jeśli pliki źródłowe instalacji są pobierane z Internetu, jest prawdopodobne, że zostaną oznaczone z co najmniej jeden NTFS pliku system strumieni danych. Aby uzyskać więcej informacji na temat strumienie danych systemu plików NTFS, zobacz [strumieni pliku](http://msdn2.microsoft.com/library/aa364404\(VS.85\).aspx). Istnienie strumienie danych systemu plików NTFS może spowodować **Otwórz plik — ostrzeżenie o zabezpieczeniach** monit, który będzie wyświetlany. Instalacja nie będzie kontynuowana dopiero po kliknięciu przycisku **Uruchom** w wierszu.  

 Na rysunku 2 przedstawiono, można wyświetlić NTFS pliku system strumienie danych **więcej** polecenia i [strumieni narzędzie](http://technet.microsoft.com/sysinternals/bb897440.aspx).  

 ![TroubleshootingReference2](media/TroubleshootingReference2.jpg "TroubleshootingReference2")  
Rysunek 2. Strumienie danych systemu plików NTFS  

 **Rysunek 2. Strumienie danych systemu plików NTFS**  

 **Możliwe rozwiązanie 1:** Prawo\-kliknij plik źródłowy instalacji, a następnie kliknij przycisk **właściwości**. Kliknij przycisk **Odblokuj**, a następnie kliknij przycisk **OK** do usunięcia z pliku strumienie danych systemu plików NTFS. Powtórz ten proces dla każdego pliku źródłowego instalacji, który jest blokowany przez istnienie jednego lub więcej NTFS pliku system strumieni danych.  

 **Możliwe rozwiązanie 2:** Użyj narzędzia strumieni jako REF \_Ref308173670 \\h na rysunku 2 przedstawiono, aby usunąć NTFS plików strumieni danych systemu z pliku źródłowego instalacji. Strumienie danych systemu plików NTFS narzędzie strumieni można usunąć z jednego lub więcej plików lub folderów na raz.  

####  <a name="LostNetworkConnections"></a> Utracone połączenia sieciowe  
 **Problem:** Instalacja może zakończyć się niepowodzeniem, jeśli umożliwia instalowanie sterowników urządzeń lub zmienia urządzenia i konfiguracji sieci. Te zmiany może spowodować wygaśnięcie w łączności sieciowej, która powoduje niepowodzenie instalacji.  

 **Możliwe rozwiązania:** Wdrożenie skryptu ZTICacheUtil.vbs umożliwienie pobierania i wykonywania instalacji. Ten skrypt jest przeznaczona do dostosować anons włączyć pobierania i wykonywania. Procesy pobierania korzystają z usługi inteligentnego transferu w tle \(BITÓW\) czy punkt dystrybucji programu Configuration Manager Web\-na podstawie Distributed Authoring i przechowywanie wersji i Usługa BITS włączona. W tym samym czasie modyfikuje program Configuration Manager, uruchom skrypt ZTICache.vbs co staje się, że program nie powoduje usunięcia samego podczas procesu wdrażania.  

####  <a name="MicrosoftOfficeSystem"></a> Microsoft Office System 2007  
 **Problem:** Podczas wdrażania pakietu Office 2007 i poprawki Instalatora Windows, w tym \(MSP\) pliku, instalacja może zakończyć się niepowodzeniem z kodem błędu 30029.  

 Dalsza analiza w ZTIApplications.log zawiera następujące komunikaty:  

-   ```  
    About to run command: \\Server\Deployment$\Tools\X86\bddrun.exe \\Server\Share\Microsoft\Office\2007\Professional\setup.exe /adminfile \\Server\Share\Microsoft\Office\2007\Professional\file.msp  
    ```  

-   ```  
    ZTI Heartbeat: command has been running for 12 minutes (process ID 1600) Return code from command = 30029  
    ```  

-   ```  
    Application Microsoft Office 2007 Professional returned an unexpected return code: 30029  
    ```  

 **Możliwe rozwiązanie 1:** Przenieś plik MSP do katalogu aktualizacji, a następnie uruchom setup.exe bez określania  **\/adminfile** opcji. Aby uzyskać więcej informacji na temat wdrażania aktualizacji podczas instalacji, zobacz [wdrażania pakietu Office 2007](http://technet.microsoft.com/library/cc303395\(v=Office.12\).aspx).  

 **Możliwe rozwiązanie 2:** Sprawdź, czy plik MSP nie są **modalne Pomiń** zaznaczone pole wyboru. Aby uzyskać więcej informacji na temat konfigurowania tego ustawienia, zobacz [Omówienie pakietu Office 2007](http://technet.microsoft.com/library/bb490141.aspx).  

### <a name="autologon"></a>Logowanie automatyczne  
 Przejrzyj problemy i rozwiązania problemów, automatycznego logowania:  

-   Przerwanie LTI i Zero Touch instalacji \(ZTI\) procesów wdrażania z powodu logowania zabezpieczeń transparentach zgodnie z opisem w [transparentach zabezpieczeń logowania](#LogonSecutiryBanners)  

-   Przerwanie wdrożenia LTI i ZTI przetwarzania z powodu wyświetla monit o poświadczenia użytkownika, zgodnie z opisem w [wyświetlony monit o podanie poświadczeń użytkownika](#PromtedforUserCredentials)  

####  <a name="LogonSecutiryBanners"></a> Transparentach zabezpieczeń logowania  
 **Problem:** Zestaw MDT sekwencje zadań są przetwarzane podczas interaktywnej sesji użytkownika, który wymaga zezwolenia komputer docelowy do logowania się automatycznie przy użyciu określonego konta administracyjnego. Jeśli obiekt zasad grupy \(obiektu zasad grupy\) jest w miejscu, które egzekwuje transparent zabezpieczeń logowania, to automatyczne logowanie będzie nie można kontynuować, ponieważ transparent zabezpieczeń przerywa proces logowania podczas oczekiwania na Zaakceptuj podane zasady użytkownika.  

 **Możliwe rozwiązania:** Pamiętaj, że obiekt zasad grupy jest stosowane do określonych jednostek organizacyjnych \(jednostek organizacyjnych\) i nie jest uwzględniony w domenie domyślnej obiektu zasad grupy. Podczas dodawania komputerów do domeny, określ, czy można dodać z jednostką Organizacyjną, która nie ma wpływu na obiekt zasad grupy, wymusza transparent zabezpieczeń logowania. W edytorze sekwencji zadań, jako jeden z ostatnich kroków sekwencji zadań obejmują skrypt, który przenosi konta komputera do żądanej jednostki Organizacyjnej.  

> [!NOTE]
>  Jeśli ponownego użycia istniejącej usługi Active Directory® domeny \(usług AD DS\) kont, upewnij się, że w przed wdrożeniem do komputera docelowego konta na komputerze docelowym ma przeniesiony z jednostką Organizacyjną, która nie ma wpływu na obiekt zasad grupy, który wymusza stosowanie transparent logowania zabezpieczeń.  

####  <a name="PromtedforUserCredentials"></a> Zostanie wyświetlony monit o poświadczenia użytkownika  
 **Problem:** Utworzono obrazu komputera, który został przyłączony do domeny. Podczas wdrażania nowego obrazu na komputerze docelowym, procesy wdrażania zatrzymanie, ponieważ automatycznie\-logowania nie występuje, a użytkownik zostanie poproszony o wprowadź odpowiednie poświadczenia. Proces wdrażania zostanie wznowione, gdy podano poświadczenia i użytkownik jest zalogowany.  

 **Możliwe rozwiązania:** Podczas przechwytywania obrazów, komputer źródłowy nie powinien być połączony z domeną. Jeśli komputer został przyłączony do domeny, przyłącz komputer do grupy roboczej, re\-przechwycenie obrazu, a następnie spróbuj wdrożenia na komputerze docelowym w celu określenia, czy problem został rozwiązany.  

### <a name="bios"></a>BIOS  
 **Problem:** Podczas wdrażania na komputerze docelowym, który jest wyposażone w technologię Intel vPro, wdrożenie może zakończyć się błędem stop. Mimo że wszystkie zaktualizowane sterowniki zostały włączone jako limit\-z\-sterowniki w konsoli Deployment Workbench, na komputerze docelowym nie uruchamia.  

 Możliwe rozwiązania: Sprawdź ustawienia w danych wejściowych podstawowego komputera docelowego\/output system \(systemu BIOS\) ustalenie, czy domyślny tryb Serial Advanced Technology Attachment jest skonfigurowany jako zaawansowany interfejs kontrolera hosta \( AHCI\). Niestety niektóre systemy operacyjne Windows nie obsługują AHCI domyślnie.  

### <a name="database-problems"></a>Problemy z bazą danych  
 Przegląd bazy danych\-związane problemy i rozwiązania:  

-   Błędy generowane w nieprawidłowo skonfigurowane zapory na serwerze bazy danych, zgodnie z opisem w [zablokowanych żądań przeglądarki serwera SQL](#BlockedSQLServerBrowserRequests)  

-   Błędy wygenerowanego w wyniku zerwane połączenia z serwerem bazy danych, zgodnie z opisem w [o nazwie połączenia potoku](#NamedPipeConnections)  

####  <a name="BlockedSQLServerBrowserRequests"></a> Żądania przeglądarki zablokowanych SQL Server  
 **Problem:** W procesie wdrożenia zestawu MDT można pobrać informacji z Microsoft SQL Server® baz danych. Jednak błędy mogą być generowane, które dotyczą nieprawidłowo skonfigurowanej zapory na serwerze bazy danych.  

 **Możliwe rozwiązania:** Zapora systemu Windows w systemie Windows Server pomaga zapobiec nieautoryzowanemu dostępowi do zasobów komputera. Jednak jeśli Zapora jest niepoprawnie skonfigurowana, próbuje nawiązać połączenia z wystąpieniem programu SQL Server mogą być zablokowane. Aby uzyskać dostęp do wystąpienia programu SQL Server, który znajduje się za zaporą, należy skonfigurować zaporę na komputerze, na którym działa program SQL Server. Aby uzyskać więcej informacji na temat konfigurowania portów zapory dla programu SQL Server, zobacz artykuł Microsoft Support [jak otworzyć port zapory dla programu SQL Server w systemie Windows Server 2008?](http://support.microsoft.com/kb/968872)  

####  <a name="NamedPipeConnections"></a> Połączenia nazwanego potoku  
 **Problem:** W procesie wdrożenia zestawu MDT można pobrać informacji z bazy danych programu SQL Server. Jednak błędy mogą być generowane, które dotyczą zerwane połączenia programu SQL Server. Powodem może być, nie włączając połączenia nazwanego potoku w programie Microsoft SQL Server.  

 **Możliwe rozwiązania:** Aby rozwiązać te problemy, należy włączyć nazwanych potoków w programie SQL Server. Można też określić **SQLShare** właściwość, która jest wymagana podczas nawiązywania połączenia do zewnętrznej bazy danych przy użyciu nazwanych potoków. Podczas nawiązywania połączenia, używając potoków nazwanych, używaj zintegrowanych zabezpieczeń do nawiązania połączenia z bazą danych. W przypadku wdrożenia LTI konto użytkownika, który określisz sprawia, że połączenie z bazą danych. W przypadku wdrożeń ZTI korzystających z programu Configuration Manager konta dostępu do sieci nawiązuje połączenie z bazą danych. Ponieważ środowisko Windows PE domyślnie nie ma żadnego kontekstu zabezpieczeń, należy połączenie sieciowe z serwerem bazy danych, aby ustanowić kontekst zabezpieczeń dla użytkownika, który będzie wykonywać połączenie.  

 Udział sieciowy, który **SQLShare** właściwość określa stanowi sposób łączenia się z serwerem, aby uzyskać kontekst zabezpieczeń właściwy. Musi mieć dostęp do odczytu do udziału. Po nawiązaniu połączenia można ustanowić połączenia nazwanego potoku do bazy danych. **SQLShare** właściwości nie są potrzebne i nie powinna być używana podczas wprowadzania TCP\/IP połączenie z bazą danych.  

 Włącz połączenia nazwanego potoku przy wykonywaniu następujących zadań na podstawie wersji programu SQL Server używane są:  

-   Włącz o nazwie połączenia potoku dla programu SQL Server 2008 R2, zgodnie z opisem w [włączyć o nazwie połączenia potoku w programie SQL Server 2008 R2](#EnableNamedPipeConnectionsinSQLServer).  

-   Włącz o nazwie potoku połączenia programu SQL Server 2005, zgodnie z opisem w [włączyć o nazwie połączenia potoku w programie SQL Server 2005](#EnableNamedPipeConnectionsinSQL).  

#####  <a name="EnableNamedPipeConnectionsinSQLServer"></a> Włącz połączenia nazwanego potoku w programie SQL Server 2008 R2  
 Aby włączyć połączenia nazwanego potoku w programie SQL Server 2008 R2, wykonaj następujące czynności:  

1.  Na komputerze programu SQL Server 2008 R2 znajduje się baza danych ma zostać zbadany, kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft SQL Server 2008 R2**, a następnie kliknij przycisk **programu SQL Server Management Studio**.  

2.  W **Microsoft SQL Server Management Studio** konsoli w **Eksplorator obiektów** prawo\-kliknij ***sql\_serwera\_nazwa***, a następnie kliknij przycisk **właściwości** \(gdzie *sql\_serwera\_nazwa* jest nazwą komputera z programem SQL Server, aby skonfigurować\).  

3.  Właściwości serwera \- ***sql\_serwera\_nazwa*** zostanie wyświetlone okno dialogowe.  

4.  W **właściwości serwera** \- ***sql\_serwera\_nazwa*** okna dialogowego, **wybierz stronę**, kliknij przycisk  **Połączenia**.  

5.  Na **połączeń** upewnij się, **zezwolenie na zdalne połączenia z tym serwerem** Sprawdź pole jest zaznaczone, a następnie kliknij przycisk **OK**.  

6.  Zamknij konsolę programu Microsoft SQL Server Management Studio.  

7.  Na komputerze programu SQL Server 2008 R2 znajduje się baza danych ma zostać zbadany, kliknij przycisk **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft SQL Server 2008 R2**, wskaż polecenie **narzędzia do konfiguracji**, a następnie kliknij przycisk **SQL Server Configuration Manager**.  

8.  W **Sql Server Configuration Manager** konsoli przejdź do programu SQL Server Configuration Manager \(lokalnego\) \/ konfigurację sieci programu SQL Server \/ protokoły dla  *SQL\_wystąpienia* \(gdzie *sql\_wystąpienia* nazwy wystąpienia programu SQL Server należy skonfigurować\).  

9. W okienku szczegółów kliknij prawym przyciskiem myszy\-kliknij **potoków nazwanych**, a następnie kliknij przycisk **włączyć**.  

     Zostanie wyświetlone okno dialogowe ostrzeżenia, wskazujący, że zmiany zostaną zapisane, ale nie zacznie obowiązywać, dopóki usługa jest zatrzymana i uruchomiona ponownie.  

10. W **ostrzeżenie** okno dialogowe, kliknij przycisk **OK**.  

11. W **Sql Server Configuration Manager** konsoli przejdź do programu SQL Server Configuration Manager \(lokalnego\) \/ usług SQL Server.  

12. W okienku szczegółów kliknij prawym przyciskiem myszy\-kliknij **programu SQL Server*\(sql\_wystąpienia\)***, a następnie kliknij przycisk **Uruchom ponownie** \(gdzie *sql\_wystąpienia* nazwy wystąpienia programu SQL Server, skonfigurowanego w kroku 2\).  

     Jest wyświetlany pasek postępu programu SQL Server Configuration Manager, który zawiera stan ponowne uruchomienie usług. Po ponownym uruchomieniu usługi, zamyka pasek postępu.  

13. Zamknij konsolę programu SQL Server Configuration Manager.  

 Aby uzyskać dodatkowe informacje [włączania połączeń zdalnych w programie SQL Server 2008](http://blogs.msdn.com/b/walzenbach/archive/2010/04/14/how-to-enable-remote-connections-in-sql-server-2008.aspx).  

#####  <a name="EnableNamedPipeConnectionsinSQL"></a> Włącz połączenia nazwanego potoku w programie SQL Server 2005  
 Aby włączyć połączenia nazwanego potoku w programie SQL Server 2005, wykonaj następujące czynności:  

1.  Na komputerze z programem SQL Server 2005, które obsługuje bazę danych w kliknij **Start**, a następnie wskaż **wszystkie programy**. Wskaż **Microsoft SQL Server 2005**, wskaż **narzędzia do konfiguracji**, a następnie kliknij przycisk **programu SQL Server Surface Area Configuration**.  

2.  W **Konfiguracja programu SQL Server 2005 obszaru powierzchni** okno dialogowe, kliknij przycisk **konfiguracji obszaru powierzchni usług i połączeń**.  

3.  W **konfiguracji obszaru powierzchni usług i połączeń — *serwera\_nazwa***  okno dialogowe \(gdzie *serwera\_nazwa*jest nazwą komputera z programem SQL Server 2005\)w **wybierz składnik, a następnie skonfiguruj połączenia i usług**, przejdź do MSSQLSERVER\\aparatu bazy danych, a następnie kliknij przycisk  **Połączenia zdalne**.  

4.  Kliknij przycisk **połączeń lokalnych i zdalnych**, kliknij przycisk **za pomocą zarówno protokołu TCP\/IP i nazwane potoki**, a następnie kliknij przycisk **Zastosuj**.  

5.  W **konfiguracji obszaru powierzchni usług i połączeń — *serwera\_nazwa***  okno dialogowe \(gdzie *serwera\_nazwa*jest nazwą komputera z programem SQL Server 2005\)w **wybierz składnik, a następnie skonfiguruj połączenia i usług**, przejdź do MSSQLSERVER\\aparatu bazy danych, a następnie kliknij przycisk  **Usługa**.  

6.  Kliknij przycisk **zatrzymać**.  

     Powoduje zatrzymanie usługi MSSQLSERVER.  

7.  Kliknij przycisk **Uruchom**.  

     Uruchamia usługi MSSQLSERVER.  

8.  Kliknij przycisk **OK**.  

9. Zamknij konfiguracji programu SQL Server 2005 powierzchni.  

 Aby uzyskać dodatkowe informacje, zobacz artykuł Microsoft Support [sposób konfigurowania programu SQL Server 2005, aby zezwolić na połączenia zdalne](http://support.microsoft.com/kb/914277)  

### <a name="deployment-scripts"></a>Skrypty wdrażania  
 Przejrzyj MDT\-związane problemy i rozwiązania:  

-   Zostanie wyświetlony monit o poświadczenia użytkownika i może zostać wyświetlony błąd 0x80070035 zgodnie z opisem w [Credentials_script](#Credentials_script)  

-   Komunikat o błędzie "Nie można odnaleźć Wuredist.cab" pojawia się zgodnie z opisem w [ZTIWindowsUpdate](#ZTIWindowsUpdate)  

####  <a name="Credentials_script"></a> Poświadczenia\_skryptu  
 **Problem:** Podczas ostatniego uruchomienia\-się nowo wdrożonym komputerze, użytkownik jest monitowany o podanie poświadczeń użytkownika i może zostać wyświetlony błąd 0x80070035, co oznacza, że nie znaleziono ścieżki sieciowej.  

 **Możliwe rozwiązania:** Pamiętaj, że pliku WIM nie obejmuje MININT lub \_SMSTaskSequence folderu. Aby usunąć te foldery, najpierw zainstaluj plik WIM za pomocą narzędzia ImageX, a następnie usuń foldery.  

> [!NOTE]
>  Jeśli dostęp zabroniony, wystąpi błąd podczas próby usunięcia foldery z pliku WIM, Otwórz okno wiersza polecenia, przełącz się do katalogu głównego obrazu zawarte w pliku WIM, a następnie uruchom **MININT usług pulpitu zdalnego** i **usług pulpitu zdalnego \_ SMSTaskSequence**.  

####  <a name="ZTIWindowsUpdate"></a> ZTIWindowsUpdate  
 **Problem:** Jeśli używasz skryptu ZTIWindowsUpdate.wsf do zastosowania podczas wdrażania aktualizacji oprogramowania, należy pamiętać, że ten skrypt może komunikować się bezpośrednio z witryny Microsoft Update, aby pobrać i zainstalować wymagane pliki binarne usługi Windows Update Agent skanowania pod kątem odpowiednich aktualizacje oprogramowania, Pobierz pliki binarne dla odpowiednich aktualizacji oprogramowania, a następnie zainstaluj pobranych plików binarnych. Ten proces wymaga skonfigurowania infrastruktury sieci zezwalająca na komputerze docelowym uzyskać dostęp do witryny Microsoft Update.  

 Jeśli udział wdrożenia nie zawiera pliki instalacyjne programu Windows Update Agent na komputerze docelowym nie ma odpowiedniego dostępu do Internetu, w plikach ZTIWindowsUpdate.log i BDD.log zgłaszany jest błąd "nie można odnaleźć wuredist.cab".  

 **Możliwe rozwiązania:** Wykonaj kroki opisane w sekcji "ZTIWindowsUpdate.wsf" w dokumencie MDT *odwołanie do zestawu narzędzi*.  

### <a name="deployment-shares"></a>Udziały wdrożenia  
 Przejrzyj problemy związane z udziału wdrożenia i rozwiązania:  

-   Aktualizowanie WIM pliki kończy się niepowodzeniem podczas aktualizowania udziału wdrożenia, zgodnie z opisem w [Niepowodzenie aktualizacji plików WIM](#FailuretoUpdateWIMFiles).  

####  <a name="FailuretoUpdateWIMFiles"></a> Niepowodzenie aktualizacji plików WIM  
 W środowisku "prosta":  

-   Zestaw MDT przejmuje zwykle WIMGAPI. Biblioteki DLL z C:\\Windows\\system32 \(zawsze w ścieżce\). Wersja tego WIMGAPI. Biblioteka DLL musi być zgodna z wersją \(kompilacji\) systemu operacyjnego.  

-   64\--bitowy system operacyjny, zestawu MDT zawsze używa x64 WIMGAPI. Pliku DLL. w systemie ścieżki powinny być tylko ten plik. Na 32\--bitowy system operacyjny, zestawu MDT zawsze używa x86 WIMGAPI. Pliku DLL. w systemie ścieżki powinny być tylko ten plik. \(Inne produkty, takie jak Menedżer konfiguracji, użyj 32\-bitowej wersji WIMGAPI. Biblioteki DLL, nawet w przypadku 64\-bitową wersją systemu operacyjnego, ale zarządzanie i zainstalować tę wersję.\)  

 **Problem:** Podczas próby zaktualizowania udziału wdrożenia, użytkownik zostanie poinformowany, czy nie powiodła się instalacja co najmniej jeden plik wim.  

 **Możliwe rozwiązania:** Otwórz okno wiersza polecenia i uruchom **gdzie WIMGAPI. Biblioteki DLL**. Dla pierwszego wpisu na liście \(pierwszej lokalizacji znalezione przez wyszukiwanie ścieżki\), upewnij się, że **wersji** właściwość odpowiada kompilacji z zestawu Windows Assessment and Deployment Kit \(systemu Windows ADK\) zainstalowane. Upewnij się również, że właściwość jest zgodna z liczbą kompilacji systemu operacyjnego.  

### <a name="the-windows-deployment-wizard"></a>Kreator wdrażania systemu Windows  
 Przejrzyj problemy związane z Kreatora wdrażania systemu Windows i rozwiązań:  

-   Strony Kreatora wdrażania systemu Windows są wyświetlane nawet wtedy, gdy LTI jest skonfigurowany do pomijania na stronach kreatora, zgodnie z opisem w [Kreatora strony są pomijane](#WizardPagesareNotSkipped).  

####  <a name="WizardPagesareNotSkipped"></a> Strony kreatora nie są pomijane.  
 **Problem:** Strona kreatora jest wyświetlana, nawet jeśli plik zestawu MDT DB lub CustomSettings.ini określa, że kreator ma być pomijana.  

 **Możliwe rozwiązania:** Poprawnie Aby przejść do strony kreatora, zawierają wszystkie właściwości, które będzie można określić na tej stronie kreatora odpowiednim w pliku zestawu MDT DB lub CustomSettings.ini oraz odpowiednie wartości. Jeśli właściwość jest niepoprawnie skonfigurowane dla strony kreatora zostało pominięte, będą wyświetlane tej strony. Aby uzyskać więcej informacji o tym, które właściwości są wymagane, aby upewnić się, że strona kreatora jest pomijane, zobacz sekcję "Dostarczanie właściwości dla pominięte wdrożenie stron kreatora", w dokumentacji zestawu MDT *odwołanie do zestawu narzędzi*.  

### <a name="disks-and-partitioning"></a>Dyski i partycjonowania  
 Przejrzyj dysku partycjonowania problemy i rozwiązania:  

-   Szyfrowanie dysków® BitLocker wystawia zgodnie z opisem w [szyfrowania dysków funkcją BitLocker](#BitLockerDriveEncryption)  

-   Partycje błędy, zgodnie z opisem w błędów partycjonowania dysku  

-   Błędy w scenariuszach wdrażania Odśwież komputera spowodowane dyskach logicznych lub dynamicznych, zgodnie z opisem w [obsługę logicznych, jak i dysków dynamicznych](#SupportforLoogicalandDynamicDisks)  

####  <a name="BitLockerDriveEncryption"></a> Szyfrowanie dysków funkcją BitLocker  
 Wdrażanie funkcji BitLocker wymaga określonej konfiguracji dla prawidłowego wdrażania. Poniższe problemy mogą być związane z konfiguracji komputera docelowego:  

-   W przypadku wdrożeń ZTI i UDI ZTIBde.wsf skrypt zakończy się niepowodzeniem z powodu błędu "nie można otworzyć klucza rejestru" HKEY\_bieżącego\_użytkownika\\Panelu sterowania\\międzynarodowej\\LocaleName "do odczytu", jako opisany w [ZTIBde.wsf skrypt zakończy się niepowodzeniem z powodu błędu "Nie można otworzyć klucza rejestru"HKEY_CURRENT_USER\Control Panel\International\LocaleName"do odczytu"](#ZTIBde.wsf).  

-   Urządzenia USB, dysków CD, stacji dysków DVD lub innych urządzeń nośników wymiennych, na komputerze docelowym, które są wyświetlane jako wiele litery dysku, zgodnie z opisem w [urządzenia są wyświetlane jako wiele litery dysku](#DevicesAppearasMultipleDriveLetters)  

-   Zmniejszanie dysku c. na komputerze docelowym, aby zapewnić wystarczającą nieprzydzielone miejsce na dysku, zgodnie z opisem w [problemy z dyskami zmniejszanie](#ProblemswithShrinkingDisks)  

#####  <a name="ZTIBde.wsf"></a> ZTIBde.wsf skrypt zakończy się niepowodzeniem z powodu błędu "nie można otworzyć klucza rejestru" HKEY\_bieżącego\_użytkownika\\Panelu sterowania\\międzynarodowej\\LocaleName "do odczytu"  
 **Problem:** Podczas próby wdrożenia funkcji BitLocker na komputerze docelowym w ZTI i UDI, ZTIBde.wsf skrypt zakończy się niepowodzeniem z powodu błędu "nie można otworzyć klucza rejestru" HKEY\_bieżącego\_użytkownika\\Panelu sterowania\\międzynarodowej\\LocaleName "do odczytu."  

 **Możliwe rozwiązania:** Określ ustawienia regionalne w **UILanguage** właściwości. ZTI i UDI ZTIBde.wsf uruchomieniu skryptu w formancie systemu, nie załadowano profil użytkownika pełna. Jeśli skrypt ZTIBde.wsf próbuje odczytać informacji o ustawieniach regionalnych nie znajduje się w rejestrze, ponieważ rejestr \(profilu użytkownika\) nie został całkowicie załadowany. Jako obejście, określ ustawienia regionalne w **UILanguage** właściwości.  

#####  <a name="DevicesAppearasMultipleDriveLetters"></a> Urządzenia są wyświetlane jako litery dysków wielu  
 **Problem:** Niektóre urządzenia może pojawić się jako wiele litery dysku logicznego, w zależności od tego, jak są dzielone. W niektórych przypadkach może emulować 1,44\-megabajt \(MB\) dyskietek i dysku magazynu pamięci. W związku z tym systemu Windows może przypisać tego samego urządzenia litery dysku A i B dla emulacji dyskietki i F dla dysku magazynu pamięci. Domyślnie zestaw MDT skryptów używać najniższy litery dysku \(w tym przykładzie, A\).  

 **Możliwe rozwiązania:** Zastąp domyślne ustawienie w **Określ szczegóły odzyskiwania funkcji BitLocker** w Kreatorze wdrażania systemu Windows. Strona podsumowania Kreatora wdrażania systemu Windows wyświetli ostrzeżenie, aby poinformować użytkownika, literę dysku, który został wybrany do przechowywania informacji odzyskiwania funkcji BitLocker. Ponadto pliki BDD.log i ZTIBDE.log rejestrować urządzenia nośników wymiennych wykryte i urządzenia, które zostały wybrane do przechowywania informacji odzyskiwania funkcji BitLocker.  

#####  <a name="ProblemswithShrinkingDisks"></a> Problemy z zmniejszanie dysków  
 **Problem:** Nie ma wystarczającej ilości nieprzydzielonego miejsca na dysku istnieje na komputerze docelowym w celu włączenia funkcji BitLocker. Aby wdrożyć funkcję BitLocker na komputerze docelowym, co najmniej 2 gigabajty \(GB\) dysku nieprzydzielonego miejsca wymaganego do utworzenia woluminu systemowego. *Wolumin systemowy* jest wolumin, który zawiera sprzęt\-określone pliki potrzebne do załadowania systemu Windows po systemie BIOS ma rozruchu komputera.  

 **Możliwe rozwiązanie 1:** Na istniejących komputerów Użyj narzędzia Diskpart się zmniejszanie dysku C, aby wolumin systemowy można utworzyć. W niektórych przypadkach, narzędzia Diskpart może nie móc zmniejszyć rozmiar dysku c. wystarczająco zapewnienie 2 GB nieprzydzielonego miejsca na dysku, prawdopodobnie z powodu fragmentacji ilości miejsca w dysku C.  

 Możliwe rozwiązanie tego problemu jest defragmentacji dysku C. Aby to zrobić, wykonaj następujące czynności:  

1.  Uruchom polecenia Diskpart **zmniejszyć querymax** polecenie, aby zidentyfikować maksymalną ilość miejsca na dysku, które mogą być nieprzydzielonego.  

2.  Jeśli wartość zwracana w kroku 1 jest mniejszy niż 2 GB, wyczyść dysk C niepotrzebne pliki, a następnie zdefragmentować go.  

3.  Uruchom polecenia Diskpart **zmniejszyć querymax** polecenie ponownie, aby sprawdzić, czy więcej niż 2 GB miejsca na dysku może być nieprzydzielonego.  

4.  Jeśli wartość zwracana w kroku 3 jest nadal może być mniejszy niż 2 GB, wykonaj jedną z następujących czynności:  

    -   Defragmentacji dysku c. wiele razy, aby upewnić się, że pełni jest zoptymalizowany.  

    -   Kopię zapasową danych na dysku C, usuń istniejącą partycję, utworzyć nową partycję, a następnie przywróć dane do nowej partycji.  

 **Możliwe rozwiązanie 2:** Skrypt ZTIBDE.wsf uruchamia narzędzie do przygotowywania dysku \(bdehdcfg.exe\) i konfiguruje system partycji rozmiar woluminu do 2 GB domyślnie. W razie potrzeby można dostosować skrypt ZTIBDE.wsf, aby zmienić ustawienie domyślne. Modyfikowanie skryptów zestawu MDT nie jest jednak zalecane.  

####  <a name="SupportforLoogicalandDynamicDisks"></a> Obsługa dysków logicznych i dynamicznych  
 **Problem:** Podczas wykonywania scenariusz wdrażania Odśwież komputer, proces wdrażania może zakończyć się niepowodzeniem podczas wdrażania na komputerze docelowym, który używa dysków logicznych lub dysków dynamicznych.  

 **Możliwe rozwiązania:** Zestaw MDT nie obsługuje wdrażanie systemów operacyjnych do dysków logicznych lub dysków dynamicznych.  

### <a name="domain-join"></a>Domain Join  
 **Problem:** Podczas wdrażania umożliwia Kreatora wdrażania systemu Windows Podaj wszystkie konieczne informacje dla komputera docelowego, łącznie z poświadczeniami, informacji dotyczących przyłączania domeny i konfiguracji statycznych adresów IP. Po zakończeniu instalacji widać, że system nie został przyłączony do domeny i należy do grupy roboczej.  

 **Możliwe rozwiązania:** Wdrożenia LTI zestawu mdt konfiguruje informacje statycznego adresu IP, po skonfigurowaniu i uruchomieniu systemu operacyjnego. Jeśli komputer docelowy znajduje się w segmencie sieci, który nie ma Dynamic Host Configuration Protocol \(DHCP\), przyłączanie do domeny zautomatyzowane, określona w pliku Unattend.xml zakończy się niepowodzeniem podczas DHCP nie jest obecny.  

 Skonfiguruj Unattend.xml do dołączenia do grupy roboczej. Następnie należy użyć wbudowanych\-w **odzyskać z domeny** krok sekwencji zadań, aby dodać krok w sekwencji zadań w celu przyłączenia do domeny, po zastosowaniu statyczny adres IP.  

### <a name="driver-installation"></a>Instalacja sterownika  
 Aby zapewnić najlepsze możliwe środowisko korzystania, instalacja urządzenia i sterowniki, należy uruchomić bezproblemowo jak to możliwe, niewielkiego lub żadnego interwencji użytkownika. Firma Microsoft udostępnia narzędzia i wskazówki ułatwiające tworzenie pakietów instalacyjnych, które spełniają tego celu. Aby uzyskać ogólne informacje o instalacji sterowników, zobacz [instalacji sterowników urządzeń i](http://www.microsoft.com/whdc/driver/install/default.mspx).  

 Sprawdź problemy związane z instalacji sterownika urządzenia i rozwiązania:  

-   Problemy występujące podczas korzystania z zestawu MDT, zgodnie z opisem w sterowniki pamięci masowej $OEM$ połączyć sterowników pamięci masowej $OEM$ z logiką magazynu masowego zestawu MDT  

-   Sterownik instalacji rozwiązywania problemów z urządzeniami przy użyciu pliku SetupAPI.log zgodnie z opisem w [Rozwiązywanie problemów z instalacją urządzeń z SetupAPI.log](#TroubleshootDeviceInstallationwithSetupAPI.log)  

####  <a name="TroubleshootDeviceInstallationwithSetupAPI.log"></a> Rozwiązywanie problemów z instalacją urządzeń z SetupAPI.log  
 Oficjalny dokument [Rozwiązywanie problemów z instalacją urządzeń z plikiem dziennika SetupAPI](http://msdn.microsoft.com/windows/hardware/gg463393.aspx) zawiera informacje o debugowaniu Instalacja urządzenia z systemem Windows. W szczególności papieru wskazówki dla deweloperów sterowników i testerów zinterpretować SetupAPI pliku dziennika.  

 Jednym z najbardziej przydatne plików dziennika dla celów debugowania jest plik SetupAPI.log. To zwykły\-pliku tekstowego przechowuje informacje SetupAPI rekordy dotyczące instalacji urządzeń usługi pakietu instalacji i instalacji aktualizacji. W szczególności pliku rejestrują urządzenie i sterownik zmiany, a także zmiany główne systemu, począwszy od ostatniej instalacji systemu Windows. Ten dokument koncentruje się na korzystanie z pliku dziennika SetupAPI rozwiązywania problemów z instalacją urządzenia; nie opisano w sekcji pliku dziennika, które są skojarzone z dodatkiem service pack i aktualizacji instalacji.  

### <a name="new-computer-deployments"></a>Nowych wdrożeń komputerów  
 Przejrzyj problemy i rozwiązania dla scenariuszy wdrażania nowego komputera:  

-   Problemy związane z uruchamianiem procesu wdrażania przy użyciu wstępnie\-środowiska wykonania rozruchu \(PXE\) rozruch zgodnie z opisem w [rozruchu w środowisku PXE](#PXEBoot)  

####  <a name="PXEBoot"></a> W środowisku PXE  
 Krótko mówiąc protokołu PXE działa w następujący sposób: Komputer kliencki inicjuje protokół przez emituje odnajdywania protokołu DHCP pakiet zawierający rozszerzenie, które identyfikuje żądania jako pochodzący z komputera klienckiego, który implementuje ten protokół PXE. Przy założeniu, że serwer rozruchu, implementacja protokołu rozszerzonej jest dostępny, serwer rozruchu wysyła ofertę zawierający adres IP serwera, który będzie obsługiwać klienta. Klient używa Trivial File Transfer Protocol, aby pobrać plik wykonywalny z rozruchu serwera. Na koniec komputer kliencki uruchamia pobieranego programu ładowania początkowego.  

 Fazy wstępnej tego protokołu piggybacks w podzestawie komunikaty DHCP, aby umożliwić klientowi wykryć serwer rozruchu \(oznacza to, że serwer, który dostarcza pliki wykonywalne dla nowej konfiguracji komputera\). Komputer kliencki może używać możliwość do uzyskiwania adresów IP \(której jest to oczekiwane zachowanie\) , ale nie jest wymagane w tym celu.  

 Na drugim etapie tego protokołu odbywa się między komputerem klienckim a serwerem rozruchu i używa DHCP format komunikatu jako wygodnym formacie komunikacji. Drugim etapie, w przeciwnym razie jest związana z standardowe usługi DHCP. Kilku następnych stronach konspektu kroku\-przez\-kroku procesu podczas inicjowania komputera klienta środowiska PXE.  

 Aby uzyskać więcej informacji na temat rozwiązywania środowisko PXE rozruch\-problemy związane z usług wdrażania systemu Windows działa w trybie starszych lub Mixed, zobacz artykuł Microsoft Support [opis środowiska PXE interakcji między PXE klienta, DHCP i serwera usług RIS ](http://support.microsoft.com/kb/244036).  

 Przejrzyj następujące rozwiązania problemów rozruchu środowiska PXE:  

-   Wyłącz rejestrowanie środowiska Preinstalacyjnego systemu Windows, aby SetupAPI.log zgodnie z opisem w [Wyłącz rejestrowanie środowiska Preinstalacyjnego systemu Windows w usługach wdrażania systemu Windows](#DisableWindowsPELogginginWindowsDeploymentServices).  

-   Upewnij się, że DHCP jest skonfigurowany prawidłowo, zgodnie z opisem w [zapewnienia właściwej konfiguracji DHCP](#EnsuretheProperDHCPConfiguration).  

-   Skrócić czas odpowiedzi do przypisywania adresów IP na komputerach klienckich środowiska PXE, zgodnie z opisem w [zwiększyć czas reakcji przypisania PXE IP adres](#ImprovePXEIPAddressAssignmentResponseTime).  

#####  <a name="DisableWindowsPELogginginWindowsDeploymentServices"></a> Wyłącz logowanie usług wdrażania systemu Windows w środowisku Windows PE  
 Pierwsza procedura zalecane jest upewnienie się, czy rejestrowanie do pliku setupapi.log zostało wyłączone.  

#####  <a name="EnsuretheProperDHCPConfiguration"></a> Sprawdź konfigurację prawidłowego DHCP  
 W zależności od modeli router w użyciu, może być obsługiwana konfiguracja routera określonych emisji przekazywania DHCP do jednej podsieci \(lub interfejs routera\) lub określonego hosta. Jeśli serwery DHCP i komputera z usługami wdrażania systemu Windows są osobne komputery, upewnij się, że routery przekazywania DHCP emituje są zaprojektowane tak, aby serwery DHCP i usług wdrażania systemu Windows odbierać transmisji klienta. w przeciwnym razie komputer kliencki nie odbiera odpowiedź na żądania rozruchu zdalnego.  

 Istnieje już router między komputerem klienckim a serwerem instalacji zdalnej, która nie zezwala na DHCP\-na podstawie żądań lub odpowiedzi za pośrednictwem? Gdy komputer kliencki usług wdrażania systemu Windows i serwera usług wdrażania systemu Windows znajdują się w różnych podsieciach, należy skonfigurować router między tymi dwoma systemami do przekazywania pakietów DHCP do serwera usług wdrażania systemu Windows. To rozmieszczenie jest to konieczne, ponieważ komputery klienckie usług wdrażania systemu Windows wykryć serwer usług wdrażania systemu Windows przy użyciu wiadomości emisji DHCP. Bez funkcji przekazywania zestawu na routerze protokołu DHCP na komputerach klienckich DHCP emituje dociera do serwera usług wdrażania systemu Windows. DHCP, ten proces przesyłania jest czasami nazywany *DHCP Proxy* lub *adresem IP pomocnika* w instrukcji konfiguracji routera. Zapoznaj się z instrukcjami routera, aby uzyskać więcej informacji o konfigurowaniu przekazywania DHCP określonego routera.  

#####  <a name="ImprovePXEIPAddressAssignmentResponseTime"></a> Poprawia czas odpowiedzi przypisania adresów IP środowiska PXE  
 Jeśli trwa zbyt długo, sprawdź następujące elementy \(15 – 20 sekund\) dla komputera klienckiego środowiska PXE można pobrać adresu IP:  

-   Czy karty sieciowej na komputerze docelowym i przełącznik lub router szybkości tego samego \(automatyczne, dwukierunkowego pełnego i itd.\)  

-   To adres IP serwera usług wdrażania systemu Windows w pliku pomocy IP na routerze za pośrednictwem której nawiązaniu połączenia? Lista adresów IP w pliku pomocy IP jest długi, należy przenieść adres serwera usług wdrażania systemu Windows u góry  

### <a name="restarting-the-deployment-process"></a>Ponowne uruchomienie procesu wdrażania  
 **Problem:** Podczas testowania i rozwiązywania problemów sekwencji zadań nowych lub zmodyfikowanych, może być konieczne ponowne uruchomienie komputera docelowego, tak, aby uruchomić proces wdrożenia za pośrednictwem od początku. Mogą wystąpić nieoczekiwane problemy, ponieważ zestaw MDT przechowuje informacje o postępie przez zapisywanie danych na dysku twardym; wszelkie ponownego uruchomienia komputera docelowego ma wznowić, którym przerwał w poprzednim ponowne uruchomienie zestawu MDT.  

 **Możliwe rozwiązania:** Aby zezwolić na proces wdrażania ponownie uruchomić od początku, Usuń dysku C:\\MININT i C:\\\_SMSTaskSequence folderów przed ponownym uruchomieniem komputera docelowego.  

### <a name="sysprep"></a>Narzędzie Sysprep  
 Przejrzyj Sysprep\-związane problemy i rozwiązania:  

-   Na komputerze docelowym nie pojawia się w jednostce Organizacyjnej poprawne DS AD zgodnie z opisem w [komputer konto znajduje się w niewłaściwej jednostki Organizacyjnej](#ComputerAccountisintheWrongOU).  

####  <a name="ComputerAccountisintheWrongOU"></a> Konto komputera jest w niewłaściwej jednostki Organizacyjnej  
 **Problem:** Komputer docelowy jest prawidłowo przyłączony do domeny, ale konto komputera jest w niewłaściwej jednostce Organizacyjnej.  

 **Możliwe rozwiązanie 1:** Jeśli wstępnie konta\-istnieje na komputerze docelowym, konto pozostanie w oryginalnej jednostce Organizacyjnej. Aby przenieść konta w określonej jednostce Organizacyjnej, Dodaj krok sekwencji zadań, który używa narzędzia automatyzacji, takich jak Microsoft Visual Basic® Scripting Edition, aby przenieść konta.  

 **Możliwe rozwiązanie 2:** Sprawdź, czy określona jednostka Organizacyjna jest w nieprawidłowym formacie i czy istnieje. Powinna być poprawnym formacie jednostki Organizacyjnej `OU=Reception,OU=NYC,DC=Woodgrovebank,DC=com`.  

### <a name="configuration-manager"></a>Menedżer konfiguracji  
 **Problem:** Komunikat o błędzie wyświetlany w REF \_Ref308174600 \\h rysunek 3 jest wyświetlany podczas próby utworzenia usługi środowiska PXE programu Configuration Manager punktu, przy użyciu **tworzenie własnych\-PXE certyfikat z podpisem** Opcja.  

 ![TroubleshootingReference3](media/TroubleshootingReference3.jpg "TroubleshootingReference3")  
Rysunek SEQ Figure \\ \* ARABIC 3. Błąd punktu Usługi środowiska PXE  

 **Rysunek SEQ Figure \\ \* ARABIC 3. Błąd punktu Usługi środowiska PXE**  

 **Możliwe rozwiązania:** Jeśli punkt obsługi środowiska PXE wcześniej istniały na serwerze, który jest konfigurowany, punkt obsługi środowiska PXE nie usunięta samodzielnie\-utworzenia certyfikatów, należy go odinstalować. Usuń folder certyfikatu środowiska PXE z C:\\Documents and Settings\\*użytkownika\_nazwa*\\danych aplikacji\\Microsoft\\kryptograficznego\\RSA, gdzie *użytkownika\_nazwa* jest nazwą użytkownika wykonującego bieżącej konfiguracji lub kto wykonał poprzedniej konfiguracji. Kreatorze nowej roli lokacji w konsoli programu Configuration Manager powinien pomyślnie zakończyć usunięcie folderu.  

### <a name="task-sequences"></a>Sekwencje zadań  
 Sprawdź problemy związane z sekwencji zadań i rozwiązania:  

-   Sekwencja zadań nie zakończy się pomyślnie lub ma nieprzewidywalne zachowanie, zgodnie z opisem w [zadań sekwencji jest Zakończ pomyślnie](#TaskSequenceDoesNotFinishSuccessfully).  

-   Original equipment manufacturer \(OEM\) zgodnie z opisem w sekwencji zadań w programie LTI znajdują się na obrazy rozruchowe z architekturą procesora przeciwną [OEM zadań sekwencji niepoprawnie pojawia się obraz rozruchowy utworzony dla Architektura procesora różnych](#OEMTaskSequenceIncorrectlyAppearsforBootImage).  

-   Kreator wdrażania systemu Windows wyświetla komunikat o błędzie "Zły element sekwencji zadania \(nieprawidłowy identyfikator GUID systemu operacyjnego\)" zgodnie z opisem w [komunikat Zły element sekwencji zadania (nieprawidłowy identyfikator GUID systemu operacyjnego) w Kreatorze wdrażania systemu Windows](#BadTaskSequenceItem).  

-   Podczas konfigurowania nazwę połączenia sieciowego, komunikat "Wprowadź prawidłową nazwę karty sieciowej" jest wyświetlany zgodnie z opisem w [Zastosuj ustawienia sieci](#ApplyNetworkSettings).  

-   Problemy, które mogą wystąpić w wyniku niepoprawna konfiguracja kontynuować Błąd ustawienia konfiguracyjne dla kroków sekwencji zadań, zgodnie z opisem w [Użyj Kontynuuj przy błędzie](#UseContinueonError).  

####  <a name="TaskSequenceDoesNotFinishSuccessfully"></a> Sekwencja zadań nie zakończyła się pomyślnie  
 **Problem:** Sekwencja zadań może nie zakończyła się pomyślnie lub nie ma nieprzewidywalne zachowanie.  

 **Możliwe rozwiązania:** **Zainstaluj System operacyjny** krok sekwencji zadań \(dla LTI\) lub **Zastosuj obraz systemu operacyjnego** krok sekwencji zadań \(UDI i ZTI\)mogły zostać zmodyfikowane po tworzenie kroku sekwencji zadań może spowodować nieoczekiwane wyniki. Na przykład, jeśli utworzono sekwencję zadań do wdrożenia 32\--bitowy obraz Windows 8.1, a następnie kontynuować **Zainstaluj System operacyjny** krok sekwencji zadań lub **Zastosuj obraz systemu operacyjnego** zadań krok sekwencji została zmieniona na odwołanie 64\-bit Windows 8.1 obrazu, sekwencja zadań mogą nie działać prawidłowo.  

 Zaleca się utworzenia nowej sekwencji zadań do wdrażania obrazów systemów operacyjnych.  

####  <a name="OEMTaskSequenceIncorrectlyAppearsforBootImage"></a> Sekwencja zadań przez producenta OEM niepoprawnie pojawia się obraz rozruchowy utworzony dla architektury procesora różnych  
 **Problem:** Sekwencję zadań na podstawie szablonu LTI OEM sekwencji zadań jest wyświetlane, odkąd dla obrazu rozruchowego z inną architekturą procesora. Na przykład OEM sekwencji zadań wdrażającej 64\-bitowy system operacyjny jest wyświetlany na 32\-bitowego obrazu rozruchowego.  

 **Możliwe rozwiązania:** Jest to oczekiwane zachowanie jako sekwencji zadań przez producenta OEM w LTI nie są uważane za "platformy\-określonych" będzie zawsze wyświetlane, niezależnie od architektury procesora obrazu rozruchowego.  

####  <a name="BadTaskSequenceItem"></a> Element sekwencji zadania zły \(nieprawidłowy identyfikator GUID systemu operacyjnego\) wiadomości w Kreatorze wdrażania systemu Windows  
 **Problem:** Podczas uruchamiania Kreatora wdrażania systemu Windows, Kreator wyświetli komunikat o błędzie "Zły element sekwencji zadania \(nieprawidłowy identyfikator GUID systemu operacyjnego\)." System operacyjny znajduje się w pliku OperatingSystem.xml; system operacyjny nie jest wyświetlana w konsoli Deployment Workbench.  

 **Możliwe rozwiązania:** Oryginalne źródło systemu operacyjnego ma co najmniej dwa pliki WIM skojarzone. Jednostka SKU, który jest skojarzony z sekwencją zadań są usuwane; jednak inne wersje systemu operacyjnego źródła nadal istnieje. Po wybraniu sekwencji zadań, która odwołuje się do usuniętej jednostki SKU na **wybierz sekwencję zadań do wykonania na tym komputerze** strona kreatora w Kreatorze wdrażania systemu Windows, komunikat o błędzie "Zły element sekwencji zadania \( Nieprawidłowy identyfikator GUID systemu operacyjnego\)"jest wyświetlany po kliknięciu **dalej** na stronie kreatora.  

 Aby rozwiązać ten problem, wykonaj jedną z następujących czynności:  

-   Usuń wszystkie jednostki SKU ze źródła systemu operacyjnego. Kreator wdrażania systemu Windows działa normalnie, a nie jest wyświetlany komunikat o błędzie.  

-   Zmień sekwencji zadań w celu użyć obrazu innego systemu operacyjnego.  

####  <a name="ApplyNetworkSettings"></a> Zastosuj ustawienia sieci  
 **Problem:** W przypadku konfigurowania nazwę połączenia sieciowego w konsoli Deployment Workbench, błąd sprawdzania poprawności wyświetla komunikat, "Wprowadź prawidłową nazwę karty sieciowej."  

 **Możliwe rozwiązania:** Usuń wszystkie spacje i nieprawidłowych znaków z nazwy określonego połączenia.  

####  <a name="UseContinueonError"></a> Użyj Kontynuuj przy błędzie  
 Jeśli sekwencja zadań zestawu MDT skonfigurowano nie Kontynuuj przy błędzie i sekwencja zadań zwraca błąd, są pomijane wszystkich pozostałych sekwencji zadań w tej grupie sekwencji zadań. Jednak pozostałe grupy sekwencji zadań są przetwarzane. Rozważ następujące opcje:  

 Utworzono dwie grupy sekwencji zadań, a każda grupa zawiera więcej niż jeden krok sekwencji zadań:  

-   Grupa A  

    -   Krok  

    -   Kroku B  

-   Grupa B  

    -   Krok  

    -   Kroku B  

 Jeśli grupa A\\krok jest skonfigurowany, aby nie Kontynuuj przy błędzie, a następnie grupy A\\B kroku nie będą przetwarzane. Jednak wszystkie kroki sekwencji zadań w grupie B będą przetwarzane.  

### <a name="the-user-state-migration-tool"></a>Narzędzie migracji stanu użytkownika  
 Przejrzyj USMT\-związane problemy i rozwiązania:  

-   Skróty, które wskazują dokumentami przechowywanymi w udostępnianych folderach sieciowych mogą nie zostać przywrócone prawidłowo zgodnie z opisem w [Brak skróty pulpitu](#MissingDesktopShortcuts).  

####  <a name="MissingDesktopShortcuts"></a> Brak skrótów pulpitu  
 **Problem:** Podczas migracji danych użytkownika za pomocą narzędzia USMT, skróty wskazujące sieci dokumenty nie mogą zostać przywrócone. Skróty są przechwytywane podczas Scanstate; jednak ich nigdy nie przywrócono do komputera docelowego podczas Loadstate.  

 **Możliwe rozwiązania:** Edytuj plik MigUser.xml ujmij w komentarz następujący wiersz:  

 Oryginał:  

```  
<include> filter='MigXmlHelper.IgnoreIrrelevantLinks()'>  
```  

 Zmodyfikowane:  

```  
<include> <!-- filter='MigXmlHelper.IgnoreIrrelevantLinks()'> -->  
```  

### <a name="windows-imaging-format-files"></a>Windows Imaging Format plików  
 Przejrzyj WIM\-związane problemy i rozwiązania:  

-   Wdrożenia LTI i ZTI się niepowodzeniem oraz błędy w pliku WIM w pliku BDD.log zgodnie z opisem w [uszkodzenie pliku WIM](#CorruptWIMFile).  

####  <a name="CorruptWIMFile"></a> Uszkodzenie pliku WIM  
 **Problem:** Podczas wdrażania obrazu, wdrożenie zakończy się niepowodzeniem z następujące wpisy w pliku BDD.log:  

-   ```  
    The image \\Server\Deployment$\Operating Systems\Windows\version1.wim was not applied successfully by ImageX, rc = 2  
    ```  

-   ```  
    LTIApply COMPLETED.  Return Value = 2  
    ```  

-   ```  
    ZTI ERROR - Non-zero return code by LTIApply, rc = 2  
    ```  

 Zbadaj problem, instalując pliku WIM za pomocą narzędzia ImageX wyniki w dzienniku błędów, "dane są nieprawidłowe." Dalsza analiza pokazuje, że sygnaturę daty pliku wim jest wiele lat przed bieżącą datą. Istnieje możliwość, że inny proces, takie jak skaner wirusów, został zawierający pliku wim Otwórz wcześniej zostało zamknięte po zakończeniu procesu odczytu lub zapisu.  

 **Możliwe rozwiązania:** Przywróć plik wim z nośnika kopii zapasowej.  

### <a name="windows-pe"></a>Windows PE  
 Przejrzyj problemy związane ze środowiska Preinstalacyjnego systemu Windows i rozwiązań:  

-   Proces wdrażania LTI lub ZTI nie jest inicjowane ze względu na niewystarczającą ilość pamięci RAM lub kart sieci bezprzewodowych, zgodnie z opisem w [niezainicjowany procesu wdrażania — ograniczoną ilością pamięci RAM lub kartę sieci bezprzewodowej](#LimitedRamorWirelessNetworkAdapter).  

-   Proces wdrażania LTI lub ZTI nie jest inicjowane ze względu na brakujące składniki systemu Windows PE, zgodnie z opisem w [niezainicjowany procesu wdrażania — Brak składników](#MissingComponents).  

-   Proces wdrażania LTI lub ZTI nie jest inicjowane ze względu na niewystarczające lub niepoprawne sterowniki urządzeń, zgodnie z opisem w [niezainicjowany procesu wdrażania — Brak lub niepoprawne sterowniki](#MissingorIncorrectDrivers).  

####  <a name="LimitedRamorWirelessNetworkAdapter"></a> Nie zainicjowano proces wdrażania — ograniczoną ilością pamięci RAM lub karty sieci bezprzewodowej  
 **Problem:** Podczas wdrażania obrazu na niektórych komputerach docelowych, uruchamiania systemu Windows PE, uruchamia **wpeinit**, zostanie otwarte okno wiersza polecenia, ale nie uruchamia procesu wdrażania. W rozwiązaniu problemu przez mapowanie dysku sieciowego z komputera docelowego wskazuje, że sterowniki karty sieciowej nie są ładowane.  

 **Możliwe rozwiązanie 1:**Kreatora wdrażania nie uruchamia się, ponieważ jest za mało pamięci RAM. Sprawdź, czy komputer docelowy ma co najmniej 512 MB pamięci RAM i że nie wideo pamięci współużytkowanej wykorzystuje więcej niż 64 MB 512 MB.  

 Nie można uruchomić na komputerze docelowym, który ma mniej niż 512 MB pamięci RAM są wersje środowiska Windows PE, która zestawu MDT obsługuje.  

 **Możliwe rozwiązanie 2:** Nie dołączaj sterowników sieci bezprzewodowej w obrazie środowiska Preinstalacyjnego systemu Windows.  

####  <a name="MissingComponents"></a> Nie zainicjowano proces wdrażania — Brak składników  
 **Problem:** Rozwiązywanie problemów z niepowodzeniem wdrożenia, przejrzyj pliku BDD.log znajdują się następujący wpis:  

```  
ERROR - Unable to create ADODB.Connection object, impossible to query SQL Server: ActiveX component can't create object (429).  
```  

 **Możliwe rozwiązania:** Ten błąd może wskazywać, że obraz środowiska Windows PE nie został utworzony przy użyciu zestawu MDT. Jeśli korzystasz z programu Configuration Manager, nie należy używać jednego z istniejących obrazów środowiska Windows PE, które programu Configuration Manager utworzone; Zamiast tego utworzyć obraz przy użyciu Kreatora sekwencji importu zadań wdrożenia firmy Microsoft.  

> [!NOTE]
>  Obrazów środowiska Windows PE, które tworzy programu Configuration Manager zawiera składniki, które obsługuje wykonywanie skryptów XML i Instrumentacji zarządzania Windows (WMI), ale nie zawierają składników, które obsługuje program Microsoft® danych ADO (ActiveX Objects).  

####  <a name="MissingorIncorrectDrivers"></a> Nie zainicjowano proces wdrażania — brakiem lub niepoprawnymi sterownikami  
 **Problem:** Podczas wdrażania na niektórych komputerach docelowych, uruchamiania systemu Windows PE, uruchamia **wpeinit**, zostanie otwarte okno wiersza polecenia, ale nie uruchamia procesu wdrażania. Rozwiązywanie problemów z przez mapowanie dysku sieciowego z komputera docelowego wskazuje sterowniki karty sieciowej nie są ładowane. Przejrzyj znajdujące się w pliku SetupAPI.log *X*: \Windows\System32\Inf wskazuje, czy środowisko Windows PE jest skonfigurowanie karty sieciowej, z których jeden jest, generuje błędy "ten sterownik nie jest przeznaczona dla tej platformy." Sterowniki w **sterowniki Out-of-Box** listy mają zostały dodane do obrazu.  

 **Możliwe rozwiązania:** Istnieje możliwość, że sterownik konflikt z innym sterownikiem występują środowiska Windows PE. Podczas konfigurowania ustawień dla obrazów środowiska Preinstalacyjnego systemu Windows w konsoli Deployment Workbench, Utwórz grupę sterowniki systemu Windows PE, która zawiera tylko sterowniki magazynów i karty sieciowej, a następnie skonfiguruj udział wdrożenia do użycia tylko grupy sterowników systemu Windows PE.  

## <a name="deployment-process-flow-charts"></a>Wykresy przepływu procesów wdrażania  
 Ta sekcja zawiera dwa zestawy MDT wykresów przepływu: jeden dla wdrożenia LTI i jeden dla wdrożenia ZTI z programem Configuration Manager. Każdy schemat blokowy przedstawia zadania uruchamiane podczas tego typu wdrożenia.  

 Należy się zapoznać w przypadku wykresów przepływu procesu wdrażania przez:  

-   Przeglądanie zaprezentowane procesu wdrożenia LTI, zgodnie z opisem w [zaprezentowane procesu wdrożenia LTI](#LTIDeploymentProcessFlowcharts)  

-   Przeglądanie zaprezentowane procesu wdrożenia ZTI zgodnie z opisem w [zaprezentowane procesu wdrożenia ZTI](#ZTIDevelopmentProcessFlowcharts)  

###  <a name="LTIDeploymentProcessFlowcharts"></a> Blokowe procesu wdrożenia LTI  
 Wykresy przepływu są udostępniane dla następujących faz:  

-   Walidacja (rysunek 4)  

-   Przechwytywanie stanu (rysunek 5 i 6 rysunek)  

-   Instalacją (rysunek 7, 8 rysunek i na rysunku nr 9)  

-   Zainstaluj (rysunek 10)  

-   Wykonywane (Rysunek 11 i rysunek 12)  

-   Przywracanie stanu (rysunek 13, rysunek 14 rys. 15 i 16 rysunek)  

 ![TroubleshootingReference4](media/TroubleshootingReference4.jpg "TroubleshootingReference4")  
Rysunek 4. Schemat blokowy fazę Weryfikacja  

 **Rysunek 4. Schemat blokowy fazę Weryfikacja**  

 ![TroubleshootingReference5](media/TroubleshootingReference5.jpg "TroubleshootingReference5")  
Rysunek 5. Schemat blokowy fazę Przechwytywanie stanu (1 z 2)  

 **Rysunek 5. Schemat blokowy fazę Przechwytywanie stanu (1 z 2)**  

 ![TroubleshootingReference6](media/TroubleshootingReference6.jpg "TroubleshootingReference6")  
Rysunek 6. Schemat blokowy fazę Przechwytywanie stanu (2 z 2)  

 **Rysunek 6. Schemat blokowy fazę Przechwytywanie stanu (2 z 2)**  

 ![TroubleshootingReference7](media/TroubleshootingReference7.jpg "TroubleshootingReference7")  
Rysunek 7. Schemat blokowy fazy preinstalacji (1 z 3)  

 **Rysunek 7. Schemat blokowy fazy preinstalacji (1 z 3)**  

 ![TroubleshootingReference8](media/TroubleshootingReference8.jpg "TroubleshootingReference8")  
Rysunek 8. Schemat blokowy fazy preinstalacji (2 z 3)  

 **Rysunek 8. Schemat blokowy fazy preinstalacji (2 z 3)**  

 ![TroubleshootingReference9](media/TroubleshootingReference9.jpg "TroubleshootingReference9")  
Rysunek 9. Schemat blokowy fazy preinstalacji (3 z 3)  

 **Rysunek 9. Schemat blokowy fazy preinstalacji (3 z 3)**  

 ![TroubleshootingReference10](media/TroubleshootingReference10.jpg "TroubleshootingReference10")  
Figure 10. Schemat blokowy w fazie instalacji  

 **Rysunek 10. Schemat blokowy w fazie instalacji**  

 ![TroubleshootingReference11](media/TroubleshootingReference11.jpg "TroubleshootingReference11")  
Rysunek 11. Schemat blokowy fazy wykonywane (1 z 2)  

 **Rysunek 11. Schemat blokowy fazy wykonywane (1 z 2)**  

 ![TroubleshootingReference12](media/TroubleshootingReference12.jpg "TroubleshootingReference12")  
Schemat blokowy rysunek 12 fazy wykonywane (2 z 2)  

 **Schemat blokowy rysunek 12 fazy wykonywane (2 z 2)**  

 ![TroubleshootingReference13](media/TroubleshootingReference13.jpg "TroubleshootingReference13")  
Figure 13. Schemat blokowy fazę Przywracanie stanu (1, 4)  

 **Rysunek 13. Schemat blokowy fazę Przywracanie stanu (1, 4)**  

 ![TroubleshootingReference14](media/TroubleshootingReference14.jpg "TroubleshootingReference14")  
Rysunek 14. Schemat blokowy fazę Przywracanie stanu (2, 4)  

 **Rysunek 14. Schemat blokowy fazę Przywracanie stanu (2, 4)**  

 ![TroubleshootingReference15](media/TroubleshootingReference15.jpg "TroubleshootingReference15")  
Figure 15. Schemat blokowy fazę Przywracanie stanu (3, 4)  

 **Figure 15. Schemat blokowy fazę Przywracanie stanu (3, 4)**  

 ![TroubleshootingReference16](media/TroubleshootingReference16.jpg "TroubleshootingReference16")  
Rysunek 16. Schemat blokowy fazę Przywracanie stanu (4 z 4)  

 **Rysunek 16. Schemat blokowy fazę Przywracanie stanu (4 z 4)**  

###  <a name="ZTIDevelopmentProcessFlowcharts"></a> Blokowe procesu wdrożenia ZTI  
 Wykresy przepływu są udostępniane dla następujących faz wdrożenia ZTI z programem Configuration Manager:  

-   Inicjowanie (rysunek 17)  

-   Walidacja (rysunek 18)  

-   Przechwytywanie stanu (rysunek 19)  

-   Instalacją (rysunek 20)  

-   Zainstaluj (rysunek 21)  

-   Wykonywane (rysunek 22)  

-   Przywracanie stanu (rysunek 23 i 24 rysunek)  

-   Przechwyć (25 rysunek)  

 ![TroubleshootingReference17](media/TroubleshootingReference17.jpg "TroubleshootingReference17")  
Figure 17. Schemat blokowy faza inicjowania  

 **Rysunek 17. Schemat blokowy faza inicjowania**  

 ![TroubleshootingReference18](media/TroubleshootingReference18.jpg "TroubleshootingReference18")  
Rysunek 18. Schemat blokowy fazę Weryfikacja  

 **Rysunek 18. Schemat blokowy fazę Weryfikacja**  

 ![TroubleshootingReference19](media/TroubleshootingReference19.jpg "TroubleshootingReference19")  
Rysunek 19. Schemat blokowy fazę Przechwytywanie stanu  

 **Rysunek 19. Schemat blokowy fazę Przechwytywanie stanu**  

 ![TroubleshootingReference20](media/TroubleshootingReference20.jpg "TroubleshootingReference20")  
Rysunek 20. Schemat blokowy fazy preinstalacji  

 **Rysunek 20. Schemat blokowy fazy preinstalacji**  

 ![TroubleshootingReference21](media/TroubleshootingReference21.jpg "TroubleshootingReference21")  
Rysunek 21. Schemat blokowy w fazie instalacji  

 **Rysunek 21. Schemat blokowy w fazie instalacji**  

 ![TroubleshootingReference22](media/TroubleshootingReference22.jpg "TroubleshootingReference22")  
Rysunek 22. Schemat blokowy fazy wykonywane  

 **Rysunek 22. Schemat blokowy fazy wykonywane**  

 ![TroubleshootingReference23](media/TroubleshootingReference23.jpg "TroubleshootingReference23")  
Rysunek 23. Schemat blokowy fazę Przywracanie stanu (1 z 2)  

 **Rysunek 23. Schemat blokowy fazę Przywracanie stanu (1 z 2)**  

 ![TroubleshootingReference24](media/TroubleshootingReference24.jpg "TroubleshootingReference24")  
Rysunek 24. Schemat blokowy fazę Przywracanie stanu (2 z 2)  

 **Rysunek 24. Schemat blokowy fazę Przywracanie stanu (2 z 2)**  

 ![TroubleshootingReference25](media/TroubleshootingReference25.jpg "TroubleshootingReference25")  
Rysunek 25. Schemat blokowy fazę przechwytywania  

 **Rysunek 25. Schemat blokowy fazę przechwytywania**  

## <a name="finding-additional-help"></a>Znajdowanie dodatkowego pomocy  
 Znajdź dodatkową pomoc w rozwiązywaniu problemów z wdrażaniem MDT przez:  

-   Trwa nawiązywanie kontaktu z Support firmy Microsoft zgodnie z opisem w [Support firmy Microsoft](#MicrosoftSupport)  

-   Uzyskania dodatkowej pomocy technicznej za pośrednictwem blogów i innych zasobów w Internecie, zgodnie z opisem w [obsługuje Internet](#InternetSupport)  

###  <a name="MicrosoftSupport"></a> Pomoc techniczna firmy Microsoft  
 Firma Microsoft udostępnia Premier i Professional poziomu obsługę programu Microsoft Deployment Toolkit.  

 Professional poziom obsługi: [http://support.microsoft.com/](http://support.microsoft.com/)  

 Premier poziom obsługi: [https://premier.microsoft.com/](https://premier.microsoft.com/)  

> [!NOTE]
>  Po skontaktowaniu się z pomocą techniczną, jest jasne, czy problem dotyczy zestawu MDT i określonej wersji.  

###  <a name="InternetSupport"></a> Obsługę Internetu  
 Wiele źródeł online zapewnianie dodatkowego pomocy rozwiązywania problemów dla zestawu MDT poza co zostało opisane w niniejszej dokumentacji. Tych źródeł online obejmują:  

-   Blogi hostowanej Microsoft  

    -   [Blog zespołu zestawu MDT](http://blogs.technet.com/b/msdeployment/)  

    -   [Blog zespołu programu Configuration Manager](http://blogs.technet.com/b/configmgrteam/)  

    -   [Blog Michael Niehaus](http://blogs.technet.com/b/mniehaus/) (Michael Niehaus zapisuje na wdrożenie systemu Windows i program Microsoft Office).  

-   Hostowanej Microsoft grupy dyskusyjne i fora:  

     Obsługa przez pracowników firmy Microsoft, branży elementów równorzędnych i ważnych pracowników firmy Microsoft dostępne są następujące grupy dyskusyjne i fora:  

    -   [Configuration Manager — wdrażania systemu operacyjnego](http://social.technet.microsoft.com/Forums/home?forum=configmanagerosd)  

    -   [Instalacja systemu Windows 8, instalacji i wdrażania](http://social.technet.microsoft.com/Forums/windows/home?forum=w8itproinstall)  

-   Informacje dotyczące wdrażania źródła poza firmy Microsoft:  

    -   [DeployVista.com](http://www.deployvista.com/)  

    -   [myITforum.com](http://www.myitforum.com/)
