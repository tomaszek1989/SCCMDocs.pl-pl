---
title: "Informacje o wersji — Configuration Manager | Dokumentacja firmy Microsoft"
description: "Te informacje, przejrzyj pilnych problemów, które nie zostały jeszcze ustalone w produkcie lub omówione w artykule bazy wiedzy Microsoft."
ms.custom: na
ms.date: 05/11/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 030947fd-f5e0-4185-8513-2397fb2ec96f
caps.latest.revision: 41
caps.handback.revision: 0
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d5166b16ffbe46af561b1ce98c0494cc4aaa72a8
ms.openlocfilehash: 9da6f9678a7fb5c76f365a3522f5e5e0fdfec037
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="release-notes-for-system-center-configuration-manager"></a>Informacje o wersji dla programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Za pomocą programu System Center Configuration Manager informacje o wersji produktu są ograniczone do pilnych problemów, które nie zostały jeszcze ustalone w produkcie (dostępne za pośrednictwem aktualizacji w konsoli) lub szczegółowo opisano w artykule bazy wiedzy Microsoft.  

 W przypadku znanych problemów wpływających na podstawowe scenariusze te informacje zamieszczono w dokumentacji online produktu w bibliotece dokumentacji programu System Center Configuration Manager.  

> [!TIP]  
>  Ten temat zawiera informacje o wersji dla bieżącej gałęzi programu System Center Configuration Manager. Technical Preview dla programu System Center Configuration Manager można znaleźć w temacie [Technical Preview dla programu System Center Configuration Manager](../../../../core/get-started/technical-preview.md)  

## <a name="setup-and-upgrade"></a>Instalowanie i uaktualnianie  

### <a name="after-you-update-a-configuration-manager-console-using-consolesetupexe-from-the-site-server-folder-recent-language-pack-changes-are-not-available"></a>Po zaktualizowaniu konsoli programu Configuration Manager za pomocą ConsoleSetup.exe z folderu serwera lokacji najnowsze zmiany w pakiecie językowym nie są dostępne
<!--  SMS 486420  Applicability should be 1610 and 1702.  -->
Po uruchomieniu aktualizacji w miejscu do konsoli przy użyciu ConsoleSetup.exe z folderu instalacji serwerów lokacji langauge ostatnio zainstalowane pakiety mogą być są one dostępne. W takim przypadku:
- Witryna uruchomiona wersja 1610 lub 1702.
- Konsola zostanie zaktualizowana w miejscu przy użyciu ConsoleSetup.exe z folderu instalacji serwera lokacji.

W przypadku wystąpienia tego problemu ponownie konsoli nie używa zestawu najnowsze pakiety językowe, które zostały skonfigurowane. Nie są zwracane nie błędy, ale będzie avaialble pakietów językowych w konsoli nie zostały zmienione.  

**Obejście problemu:** Odinstalować bieżącą konsolę, a następnie ponownie zainstaluj konsoli jako nową instalację. ConsoleSetup.exe można użyć z folderu instalacji serwerów lokacji. Podczas instalacji upewnij się wybrać pliki pakietu języka, którego chcesz użyć.


### <a name="with-version-1702-the-default-site-boundary-group-is-configured-for-use-for-site-assignment"></a>Z wersją 1702 domyślna grupa granic lokacji jest skonfigurowana do użycia dla przypisania lokacji
<!--  SMS 486380   Applicability should only be to 1702. -->
Z wersją 1702 kartę odwołanie do grupy granic lokacji domyślny ma sprawdzenia **Użyj tej grupy granic dla przypisania lokacji**, wyświetla listę lokacji jako **przypisana lokacja**i jest wyszarzone, dzięki czemu konfiguracji nie można edytować ani usunąć.

**Obejście problemu:** Brak. Możesz zignorować to ustawienie. Choć grupy jest włączona dla przypisania lokacji, domyślna grupa granic lokacji nie jest używany do przypisywania lokacji. Za pomocą 1702 ta konfiguracja zapewnia, że domyślna grupa granic lokacji jest skojarzony z odpowiedniej lokacji.



### <a name="when-installing-a-long-term-service-branch-site-using-version-1606-a-current-branch-site-is-installed"></a>Podczas instalowania lokacji długoterminowe gałęzi usługi przy użyciu wersji 1606, instalowania lokacji bieżącej gałęzi
<!-- Consider move to core content  -->
Podczas instalowania lokacji długoterminowe obsługi gałęzi (LTSB) za pomocą nośników linii bazowej 1606 wersji z października 2016 wersji należy Instalator instaluje zamiast lokacji bieżącej gałęzi. Dzieje się tak, ponieważ nie wybrano opcję instalacji punkt połączenia usługi z instalacji lokacji.

 - Punkt połączenia usługi nie jest wymagany, należy wybrać do zainstalowania podczas instalacji, aby zainstalować lokację LTSB.

Po zakończeniu instalacji można odinstalować punkt połączenia usługi.  Jednakże musi mieć połączenia usługi punktu w trybie offline lub online w celu przesłania danych telemetrii i uzyskać aktualizacje zabezpieczeń dla bieżącej gałęzi i LTSB witryn.

Jeśli witryny zainstalowany w lokacji bieżącej gałęzi, ale trzeba zainstalować LTSB, należy odinstalować lokacji i zainstalować go ponownie. Alternatywnie, można wywołać [Microsoft Help i pomocy technicznej](http://go.microsoft.com/fwlink/?LinkId=243064) celu uzyskania pomocy.  

Aby upewnić się, która gałąź zainstalowane, w konsoli pod adresem **Administracja** > **konfiguracja lokacji** > **witryny**i Otwórz **ustawienia hierarchii**. Opcja konwersji lokacji do lokacji bieżącej gałęzi jest dostępna tylko w przypadku, gdy witryna jest uruchamiana LTSB.  

**Obejście problemu:**  Brak.   



### <a name="the--sql-server-backup-model-in-use-by-configuration-manager-can-change-from-full-to-simple"></a>Model kopii zapasowej programu SQL Server używany przez program Configuration Manager może zostać zmieniony z pełnego na prosty  
<!-- Confirm applicability for upgrade to later baselines. 1511 is out of support. 1606 is minmum supported baseline  -->

 Podczas uaktualniania do programu System Center Configuration Manager w wersji 1511 model kopii zapasowej programu SQL Server, używany przez programu Configuration Manager, może zostać zmieniony z pełnego na prosty.  

-   Jeśli używasz niestandardowego zadania tworzenia kopii zapasowej programu SQL Server z modelem pełnej kopii zapasowej (zamiast wbudowanego zadania tworzenia kopii zapasowej dla programu Configuration Manager), uaktualnienie może zmienić model kopii zapasowej z pełnego na prosty.  

**Obejście**: Po uaktualnieniu do wersji 1511 Sprawdź konfigurację programu SQL Server, a następnie przywróć ją do pełnego w razie potrzeby.  



### <a name="an-update-is-stuck-with-a-state-of-downloading-in-the-updates-and-servicing-node-of-the-configuration-manager-console"></a>Aktualizacja jest wstrzymywana podczas pobierania w węźle Aktualizacje i obsługa konsoli programu Configuration Manager  
<!-- Source bug pending. Consider move to core content.  -->
Podczas automatycznego pobierania aktualizacji przez punkt połączenia usługi online, aktualizacja może zostać wstrzymana ze stanem Pobieranie. W przypadku wstrzymania aktualizacji podczas pobierania we wskazanych plikach dziennika wyświetlane są pozycje podobne do poniższych:  

Dziennik DMPdownloader:  

-   BŁĄD: Nie można pobrać redist dla 037cd17e-4d7b-40e1-802b-14bb682364c7 za pomocą polecenia /RedistUrl http://go.microsoft.com/fwlink/?LinkID=724436 /LnManifestUrl http://go.microsoft.com/fwlink/?LinkID=724434 RedistVersion 112015/noui "D:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist"  

ConfigMgrSetup.log:  

-   Błąd: Nie można zweryfikować podpisu authenticode 'd:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist\sqlncli.msi'.  

-   Błąd: Sprawdzenie podpisu pliku nie powiodło się dla 'd:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist\sqlncli.msi  

**Obejście**: Na serwerze lokacji, należy zmodyfikować następujący klucz rejestru odpowiada następujący kod i następnie uruchom ponownie usługę SMS_Executive albo poczekaj na następny cykl automatyczne pobieranie do 24 godzin.  

-   **Klucz do edycji**: Publikowanie Providers\Software HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\WinTrust\Trust  

-   **Wartość stanu**:  Ustaw **146944** dziesiętną lub **0x00023e00** szesnastkowe  


###  <a name="setup-fails-when-using-redist-files-from-the-cdlatest-folder-with-a-manifest-verification-error"></a>Instalacja nie powiedzie się, używając redist pliki z dysku CD. Najnowsze folderu z powodu błędu weryfikacji manifestu
<!-- Source bug pending  -->

Po uruchomieniu Instalatora z dysku CD. Najnowsze folderu utworzonego dla wersji 1606 i korzystać z plików redist dołączonej do tego dysku CD. Najnowszy folder, instalacja nie powiedzie się z następujące błędy w dzienniku instalacji programu Configuration Manager:

  - BŁĄD: Sprawdzenie skrótu pliku defaultcategories.dll nie powiodło się
  - BŁĄD: Nie można zweryfikować manifestu. Nieprawidłowa wersja manifestu?

**Obejście problemu:**  Użyj jednej z następujących czynności:
 - Podczas instalacji wybrać opcję pobrania najnowszych plików redist firmy Microsoft do użycia zamiast uwzględnionych w dysku CD. Najnowszy folder.
 - Ręcznie usuń *cd.latest\redist\languagepack\zhh* folder, a następnie uruchom ponownie Instalatora.

### <a name="service-connection-tool-throws-an-exception-when-sql-server-is-remote-or-when-shared-memory-is-disabled"></a>Narzędzie połączenia usług zgłasza wyjątek po zdalnego programu SQL server lub po wyłączeniu pamięci współużytkowanej
Począwszy od wersji 1606, narzędzie połączenia usługi generuje wyjątek, gdy jest spełniony jeden z następujących czynności:  
 -    Baza danych lokacji znajduje się zdalnie z komputera, na którym znajduje się punkt połączenia usługi i używa niestandardowego portu (port inny niż 1433)
 -     Baza danych lokacji znajduje się na tym samym serwerze co punkt połączenia usługi, ale protokół SQL **pamięci współużytkowanej** jest wyłączona

Wyjątkiem jest podobny do następującego:
 - *Nieobsługiwany wyjątek: System.Data.SqlClient.SqlException: Wystąpił błąd sieci lub danego wystąpienia podczas nawiązywania połączenia z serwerem SQL. Serwer nie został znaleziony lub był niedostępny. Sprawdź, czy nazwa wystąpienia jest prawidłowa i czy program SQL Server jest skonfigurowany do zezwalania na połączenia zdalne. (Dostawca: Dostawca nazwanych potoków, błąd: 40 - nie można otworzyć połączenia z serwerem SQL)--*

**Obejście**: Podczas używania narzędzia należy zmodyfikować rejestr serwera, który jest hostem punktu połączenia usługi w celu uwzględnienia informacji o porcie programu SQL Server:

   1.    Przed rozpoczęciem korzystania z narzędzia, Edytuj następujący klucz rejestru, a następnie dodaj numer portu, który jest używany do nazwy serwera SQL:
    - Klucz:   HKLM\Microsoft\SMS\COMPONENTS\SMS_DMP_UPLOADER\
      - Wartość: &lt;Nazwa programu SQL Server >
    - Dodaj: **,&lt;PORT >**

    Na przykład, aby dodać port *15001* na serwerze o nazwie *testserver.test.net*, będzie wynikowe klucza: ***HKLM\Software\Microsoft\SMS\COMPONENTS\SMS_DMP_UPLOADER\testserver.test.NET,15001***

   2.    Po dodaniu portu do rejestru, narzędzie powinien działać normalnie.  

   3.    Po użyciu narzędzia zarówno dla **-połączyć** i **-zaimportować** kroków, zmienić wartość klucza rejestru do oryginalnej wartości.  




<!-- No current Backup and Recovery relenotes
## Backup and recovery
-->



## <a name="client-deployment-and-upgrade"></a>Wdrażanie i uaktualnianie klientów  

### <a name="client-installation-fails-with-error-code-0x8007064c"></a>Instalacja klienta kończy się niepowodzeniem z kodem błędu 0x8007064c
<!--- SMS 486973 -->

Podczas wdrażania klienta na komputerach z systemem Windows, instalacja nie powiedzie się. W pliku ccmsetup.log na zawiera wpis "plik"C:\WINDOWS\ccmsetup\Silverlight.exe"zwróciła kod zakończenia błędu 1612. Niepowodzenie instalacji"następuje"InstallFromManifest failed 0x8007064c".

**Obejście problemu** przyczyną jest uszkodzony, uprzednio zainstalowanych wersji programu Silverlight. Można spróbować uruchomić następujące narzędzia na zainfekowanym komputerze, aby rozwiązać ten problem: [https://support.microsoft.com/help/17588/fix-problems-that-block-programs-from-being-installed-or-removed](https://support.microsoft.com/help/17588/fix-problems-that-block-programs-from-being-installed-or-removed) 




## <a name="operating-system-deployment"></a>Wdrożenie systemu operacyjnego  

### <a name="issue-with-the-windows-adk-for-windows-10-version-1511"></a>Problem z zestawem Windows ADK dla systemu Windows 10 (wersja 1511)  
Po uruchomieniu sekwencji zadań w programie Software Center, który używa środowiska Windows PE obrazu rozruchowego v.10.0.10586 od 10 ADK systemu Windows, wersja 1511, po ponownym uruchomieniu komputera w środowisku Windows PE, zakończy się niepowodzeniem, gdy "Inicjowanie urządzenia" z powodu błędu: **Nie można zainicjować środowiska Windows PE z kodem błędu 0x80220014**  

**Obejście**: Użyj oryginalnej Windows ADK 10. Aby uzyskać więcej informacji zobacz następujące blogu zespołu programu Configuration Manager System Center: [Problem z systemem Windows ADK dla systemu Windows 10](http://blogs.technet.com/b/configmgrteam/archive/2015/11/20/issue-with-the-windows-adk-for-windows-10-version-1511.aspx)  

### <a name="dynamic-application-installation-fails-during-task-sequence-which-successfully-completes"></a>Występuje niepowodzenie instalacji aplikacji dynamicznej podczas sekwencji zadań, która kończy się pomyślnie  
Jeśli podczas wdrażania sekwencji zadań, która używa opcji **Zainstaluj aplikacje zgodnie z listą zmiennych dynamicznych**, instalacja jednej z aplikacji nie powiedzie się z jakiegokolwiek powodu, sekwencja zadań zgłosi powodzenie operacji. Dzieje się tak niezależnie od tego, jak zostały skonfigurowane następujące opcje:  

-   **Kontynuuj przy błędzie** (na karcie Opcje w kroku instalacji aplikacji)  

-   **Jeśli instalacja aplikacji nie powiedzie się, kontynuuj instalowanie pozostałych aplikacji z listy** (na karcie Właściwości w kroku instalowania aplikacji)  

Możesz wyświetlić plik smsts.log, aby ustalić, czy instalacja aplikacji zakończyła się niepowodzeniem.  

**Obejście**: Użyj **_TSAppInstallStatus** zmiennej jako warunek na kolejnych kroków w sekwencji zadań z warunkiem niepowodzenie sekwencji zadań wystąpił błąd przy użyciu jednego z dynamicznych aplikacji.  

### <a name="smb-might-not-work-properly-after-you-use-a-task-sequence-to-install-windows-10"></a>Protokół SMB może nie działać prawidłowo po instalacji systemu Windows 10 za pomocą sekwencji zadań  
W przypadku wykorzystania sekwencji zadań do instalacji obrazu systemu Windows 10 protokół SMB może nie działać poprawnie po zainstalowaniu klienta programu Configuration Manager. Na przykład następujące etapy sekwencji zadań mogą zakończyć się niepowodzeniem:  

-   Przywracanie stanu użytkownika, jeśli został użyty z punktem migracji stanu  

-   Łączenie z folderem sieciowym  

Z wiersza polecenia administratora (F8) możesz na przykład nadal wysyłać sygnał PING do komputera, ale dowolny ruch sieciowy SMB (taki jak polecenie NET USE z wiersza polecenia) może zakończyć się niepowodzeniem z błędem 1231 - nie można skontaktować się z lokacją sieciową.  

**Obejście**:  
dodaj etap sekwencji zadań Uruchom wiersz polecenia po etapie sekwencji zadań Zainstaluj system Windows i program ConfigMgr, aby zatrzymać, a następnie uruchomić usługę stacji roboczej w następujący sposób:    
**polecenie net stop stacji roboczej /y & net start stacji roboczej**  

### <a name="servicing-plans-create-a-lot-of-duplicate-software-update-groups-and-deployments-by-default"></a>Plany obsługi tworzą domyślnie wiele powielonych grup aktualizacji oprogramowania i wdrożeń  
Domyślnie kreator tworzenia planów obsługi jest uruchamiany obecnie po każdej synchronizacji aktualizacji oprogramowania. Przy każdym uruchomieniu tworzy on nową grupę aktualizacji oprogramowania i wdrożenia. W przypadku harmonogramu synchronizacji aktualizacji oprogramowania uruchamianego kilka razy dzienne kreator tworzenia planów obsługi każdego dnia będzie tworzył wiele prawdopodobnie identycznych grup aktualizacji oprogramowania i wdrożeń.  

**Obejście**:    
po utworzeniu planu obsługi otwórz właściwości planu, przejdź do karty **Harmonogram szacowania**, wybierz pozycję **Uruchom tę regułę według harmonogramu**, kliknij pozycję **Dostosuj** i utwórz harmonogram niestandardowy. Można na przykład określić uruchamianie planu obsługi co 60 dni.  

### <a name="when-a-high-risk-deployment-dialog-is-visible-to-a-user-subsequent-high-risk-dialogs-with-a-sooner-deadline-are-not-displayed"></a>Gdy okno dialogowe wdrożenie o wysokim ryzyku jest widoczny dla użytkownika, nie są wyświetlane kolejne o wysokim ryzyku okien dialogowych z terminem wcześniej
Po utworzeniu i wdrożyć wdrożenie o wysokim ryzyku zadań dla użytkowników do użytkownika zostanie wyświetlone okno dialogowe o wysokim ryzyku. Jeśli użytkownik nie zamknąć okno dialogowe, można utworzyć i wdrożyć inne wdrożenie o wysokim ryzyku na podstawie terminu wcześniej niż pierwszy, użytkownik nie otrzyma okno dialogowe zaktualizowane aż zamknięty oryginalny okno dialogowe. Wdrożenia będą nadal działać w skonfigurowanym terminy.

**Obejście**:  
Użytkownik należy zamknąć okno dialogowe pierwszy wdrożenie o wysokim ryzyku wyświetlić okno dialogowe dalej wdrożenie o wysokim ryzyku.

## <a name="mobile-device-management"></a>Zarządzanie urządzeniami przenośnymi  

### <a name="cannot-create-an-enrollment-profile-on-a-primary-site"></a>Nie można utworzyć profilu rejestracji w lokacji głównej  
Administrator nie może utworzyć profilu rejestracji w konsoli administracyjnej programu System Center Configuration Manager, która jest połączona z lokacją główną. Podczas próby zarejestrowania, administrator zostanie wyświetlony komunikat o błędzie "DEP token nie został zaktualizowany. Przekaż DEP token"w Kreatorze profilu rejestracji. Ten błąd występuje mimo tego, że prawidłowy token usługi DEP został przekazany do centralnej lokacji administracyjnej.  

**Obejście**: Utwórz profil rejestracji w konsoli programu System Center Configuration Manager, które łączy do witryny Administracja centralna.  

### <a name="dep-cannot-use-non-alpha-numeric-characters-in-enrollment-profiles"></a>W usłudze DEP nie można używać znaków innych niż alfanumeryczne w profilach rejestracji  
W profilach rejestracji skojarzonych z profilem rejestracji urządzeń (DEP) firmy Apple nie można używać znaków innych niż alfanumeryczne w polach **Nazwa**, **Opis**, **Dział** i **Numer telefonu** dla profilu rejestracji, gdy usługa DEP jest włączona. W przypadku użycia w tych polach znaków innych niż alfanumeryczne profil rejestracji zostanie utworzony, ale nie będzie można go przekazać do firmy Apple. Serwer firmy Apple nie przekaże żadnego komunikatu o błędzie ani ostrzeżenia, a profile nie zostaną wdrożone na urządzeniach zarządzanych przez usługę DEP.  

**Obejście**: Brak.

### <a name="full-wipe-disables-windows-10-devices-with-less-than-4-gb-ram"></a>Całkowite wyczyszczenie powoduje wyłączenie urządzeń z systemem Windows 10 z pamięcią RAM mniejszą niż 4 GB

Przeprowadzenie całkowitego czyszczenia danych w urządzeniu z systemem Windows 10 RTM (wersje starsze niż 1511) z pamięcią RAM mniejszą niż 4 GB sprawi, że urządzenie nie będzie nadawać się do użytku. Po podjęciu próby wyczyszczenia danych urządzenie nie reaguje i nie można go uruchomić.

**Obejście**: Upewnij się, że RTM komputery z systemem Windows 10 mają co najmniej 4 GB pamięci RAM dostępnej przed wykonaniem pełne czyszczenie danych na urządzeniu. Aby wyświetlić numer wersji systemu Windows 10 urządzenia, w wierszu polecenia wprowadź „winver”. Jeśli urządzenie już zostało wyczyszczone i nie odpowiada, możesz użyć rozruchowego dysku USB z systemem Windows 10 USB do uruchomienia urządzenia i przywrócenia dostępu do niego.

### <a name="when-a-user-belongs-to-two-or-more-user-collections-that-a-terms-and-conditions-policy-is-deployed-to-the-user-sees-multiple-sets-of-the-same-terms"></a>Jeśli użytkownik należy do co najmniej dwóch kolekcji użytkowników, w których są wdrożone zasady warunków i postanowień, użytkownikowi będzie wyświetlanych wiele zestawów tych samych warunków  

Gdy administrator wdraża zestaw warunków w wielu kolekcjach użytkowników, a użytkownik należy do więcej niż jednej z nich, dla tego użytkownika zostanie wyświetlonych wiele kopii identycznych warunków podczas otwierania Portalu firmy.  Na przykład, jeśli użytkownik o nazwie "SampleUser" jest elementem członkowskim dwóch kolekcji innego użytkownika, jeden o nazwie "CompanyEmployeesFTE" i "CompanyEmployeesNA", "i warunki i postanowienia o nazwie"CompanyTerms"jest wdrażana na CompanyEmployeesFTE i CompanyEmployeesNA, SampleUser zobaczą dwie identyczne zestawy CompanyTerms na stronie akceptacji warunków. Ponieważ użytkownicy mogą tylko zaakceptować lub odrzucić wszystkie warunki, nie ma ryzyka wystąpienia niejednoznacznej akceptacji, oznaczającej zarówno zaakceptowanie, jak i odrzucenie warunków przez użytkownika. Raport dotyczący akceptacji warunków i postanowień zawiera tylko jeden wiersz dla każdego zestawu warunków i każdego użytkownika, więc nie ma błędów w tym raporcie. Jedynym wynikiem jest to, że użytkownik będzie widział dwa zestawy warunków na stronie akceptacji.  

**Obejście**: Upewnij się, że każdy użytkownik jest dostępny tylko w jednej kolekcji, do której są wdrożone postanowienia.  

### <a name="android-for-work-email-profiles-that-use-certificate-authentication-are-not-applied-to-devices"></a>Android profili poczty e-mail pracy, które korzystają z certyfikatu uwierzytelniania nie są stosowane do urządzeń
<!--  487657 -->
Po utworzeniu Android dla profilu poczty e-mail pracy, istnieją dwie opcje uwierzytelniania. Jedna jest nazwa użytkownika i hasło, a drugi jest certyfikaty. W tej chwili nie działa opcja certyfikatów. Jeśli profil jest tworzony skonfigurowaną metodę uwierzytelniania za pomocą **certyfikaty**, profil nie zostanie zastosowane na urządzeniu i użytkownik jest monitowany ręczne wprowadzenie szczegóły konta poczty e-mail.

**OBEJŚCIE PROBLEMU**: Brak. Administratorzy muszą użyj **nazwy użytkownika i hasła** opcji lub poczekaj, aż ten problem został rozwiązany.

## <a name="reports-and-monitoring"></a>Raporty i monitorowanie  

### <a name="the-health-attestation-report-is-empty-even-though-health-attestation-data-was-previously-collected"></a>Raport zaświadczania o kondycji jest pusty mimo wcześniejszego zebrania danych zaświadczania o kondycji  
Jeśli użytkownik administracyjny z rolą zabezpieczeń obejmującą uprawnienie **Odczyt** dla grupy uprawnień **Zaświadczanie o kondycji** wyświetla raport zaświadczania o kondycji, raport ten jest pusty i dane nie są wyświetlane. Wynika to z faktu, że uprawnienia do wyświetlania danych w raporcie zaświadczania o kondycji są połączone z grupą uprawnień **Koligacja urządzenia użytkownika** zamiast z grupą uprawnień zaświadczania o kondycji.  

Ten problem ma wpływ na System Center Configuration Manager z aktualizacją 1602 i powinien być rozwiązane w przyszłych aktualizacji.  

**Obejście**: Przypisz grupę zabezpieczeń, która zawiera użytkownika administracyjnego **odczytu** uprawnienia do **koligacje urządzeń użytkowników** grupy uprawnień.  

### <a name="conditional-access"></a>Dostęp warunkowy  

#### <a name="the-same-user-collection-is-not-blocked-from-being-added-to-both-exempted-and-targeted-collections"></a>Jedną kolekcję użytkownika można dodać równocześnie do kolekcji wykluczonych i docelowych.  
Dzieje się to tylko w przypadku dodania jednego elementu **Kolekcja użytkownika** do strony **Kolekcja wykluczona** **przed** dodaniem jej do strony **Kolekcja docelowa**.  Jeśli element **Kolekcja użytkownika** zostanie dodana najpierw do strony **Kolekcje docelowe**, a następnie nastąpi próba dodania tego samego elementu **Kolekcja użytkownika** do strony **Kolekcja wykluczona**, powinien zostać wyświetlony normalny komunikat dotyczący blokowania.  

Ten problem dotyczy programu System Center Configuration Manager dostępu warunkowego dla **lokalnego programu Exchange** z aktualizacji 1602 i powinien być rozwiązane w przyszłych aktualizacji.  

**Obejście problemu:** Dodaj **kolekcji użytkowników** do **kolekcje docelowe** strony przed wybraniem **kolekcji użytkowników** na **wykluczone kolekcji** strony lub upewnij się, nie są takie same Dodawanie **kolekcji użytkowników** zarówno docelowa i kolekcje są zwalniane.

## <a name="endpoint-protection"></a>Program Endpoint Protection
<!--  Product Studio bug 485370 added by Nathbarn 04 19 2017 -->
### <a name="antimalware-policy-fails-to-apply-on-windows-server-2016-core"></a>Zasady ochrony przed złośliwym oprogramowaniem nie powiedzie się do zastosowania w systemie Windows Server Core 2016
Zasady ochrony przed złośliwym oprogramowaniem do zastosowania w systemie Windows Server Core 2016 kończy się niepowodzeniem.  Kod błędu to 0x80070002.  Brak zależności dla ConfigSecurityPolicy.exe nie istnieje.

**Obejście problemu:**  Ten problem można rozwiązać przez [artykuł bazy wiedzy 4019472](https://support.microsoft.com/help/4019472/windows-10-update-kb4019472) 9 maja 2017 rozproszonych. 

