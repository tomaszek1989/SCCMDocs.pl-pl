---
title: "Informacje o wersji — programu Configuration Manager | Dokumentacja firmy Microsoft"
description: "Te informacje można uzyskać pilnych problemów, które nie zostały jeszcze rozwiązane w produkcie lub omówione w artykule bazy wiedzy Microsoft Knowledge Base."
ms.custom: na
ms.date: 05/31/2017
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
ms.sourcegitcommit: dc221ddf547c43ab1f25ff83c3c9bb603297ece6
ms.openlocfilehash: 6113576ca38da27e9e8732b3930deee96db4ae2c
ms.contentlocale: pl-pl
ms.lasthandoff: 06/01/2017


---
# <a name="release-notes-for-system-center-configuration-manager"></a>Informacje o wersji dla programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Z programem System Center Configuration Manager informacje o wersji produktu są ograniczone do pilnych problemów, które nie zostały jeszcze rozwiązane w produkcie (udostępnione za pośrednictwem aktualizacji w konsoli), lub szczegółowo opisane w artykule bazy wiedzy Microsoft Knowledge Base.  

 W przypadku znanych problemów wpływających na podstawowe scenariusze te informacje zamieszczono w dokumentacji online produktu w bibliotece dokumentacji programu System Center Configuration Manager.  

> [!TIP]  
>  Ten temat zawiera informacje o wersji dla bieżącej gałęzi programu System Center Configuration Manager. Technical Preview programu System Center Configuration Manager, zobacz [Technical Preview programu System Center Configuration Manager](../../../../core/get-started/technical-preview.md)  

## <a name="setup-and-upgrade"></a>Instalowanie i uaktualnianie  

### <a name="after-you-update-a-configuration-manager-console-using-consolesetupexe-from-the-site-server-folder-recent-language-pack-changes-are-not-available"></a>Po zaktualizowaniu konsoli programu Configuration Manager za pomocą ConsoleSetup.exe z folderu serwera lokacji najnowsze zmiany w pakiecie językowym nie są dostępne
<!--  SMS 486420  Applicability should be 1610 and 1702.  -->
Po uruchomieniu aktualizacji w miejscu do konsoli przy użyciu ConsoleSetup.exe z folderu instalacji serwerów lokacji langauge ostatnio zainstalowane pakiety może nie być dostępne. W takim przypadku:
- Lokalizacji uruchomiono wersję 1610 lub 1702.
- Konsola jest aktualizowany w miejscu przy użyciu ConsoleSetup.exe z folderu instalacji serwera lokacji.

Gdy wystąpi ten problem, ponownie konsoli nie używa najnowszy zestaw pakietów językowych, które zostały skonfigurowane. Nie są zwracane nie błędy, ale nie ma zmieni tym dostępną pakietów językowych do konsoli.  

**Obejście problemu:** Odinstaluj bieżącą konsolę, a następnie zainstalować ponownie jako nową instalację konsoli. Można użyć ConsoleSetup.exe z folderu instalacji serwerów lokacji. Podczas instalacji upewnij się wybrać pliki pakietu języka, który ma być używany.


### <a name="with-version-1702-the-default-site-boundary-group-is-configured-for-use-for-site-assignment"></a>Wersją 1702 domyślnej grupy granic lokacji jest skonfigurowana do użycia dla przypisania lokacji
<!--  SMS 486380   Applicability should only be to 1702. -->
Wersją 1702 karcie odwołania grupy granic lokacji domyślne ma sprawdzenia **Użyj tej grupy granic do przypisania lokacji**, wyświetla listę lokacji jako **przypisana lokacja**i jest niedostępne, tak aby konfiguracji nie można edytować ani usunąć.

**Obejście problemu:** Brak. Możesz zignorować to ustawienie. Mimo że grupy jest włączona dla przypisania lokacji, domyślna grupa granic lokacji nie jest używany do przypisania lokacji. Z 1702 ta konfiguracja zapewnia, że domyślna grupa granic lokacji jest skojarzony z odpowiedniej lokacji.



### <a name="when-installing-a-long-term-service-branch-site-using-version-1606-a-current-branch-site-is-installed"></a>Podczas instalowania lokacji oddziału usługi długoterminowe przy użyciu wersji 1606, Current Branch lokacji jest zainstalowany
<!-- Consider move to core content  -->
Użycie nośnika linii bazowej 1606 wersji z października 2016 wersji aby zainstalować lokację długoterminowe Servicing Branch (LTSB), instalacja lokacji bieżącej gałęzi zamiast tego. Dzieje się tak, ponieważ nie wybrano opcję zainstalowania punktu połączenia usługi w ramach instalacji lokacji.

 - Punkt połączenia usługi nie jest wymagany, musi ona zostać wybrana do zainstalowania podczas instalacji, aby zainstalować lokację LTSB.

Po zakończeniu instalacji można odinstalować punkt połączenia usługi.  Jednak musi mieć połączenie usługi punktu w trybie offline lub online do przesyłania danych telemetrycznych i Pobierz aktualizacje zabezpieczeń dla bieżącej gałęzi i LTSB witryny.

Jeśli witryny zainstalowany w lokacji bieżącej gałęzi, ale trzeba zainstalować LTSB, należy odinstalować lokację i zainstaluj go ponownie. Alternatywnie możesz wywołać [Microsoft Help i pomocy technicznej](http://go.microsoft.com/fwlink/?LinkId=243064) Aby uzyskać pomoc.  

Aby upewnić się, która gałąź zainstalowane, w konsoli pod adresem **administracji** > **konfiguracja lokacji** > **witryny**i Otwórz **ustawienia hierarchii**. Opcja skonwertuje wówczas lokację do lokacji bieżącej gałęzi jest dostępna tylko w przypadku, gdy w lokacji działa LTSB.  

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

-   BŁĄD: Nie można pobrać pakietu redystrybucyjnego dla 037cd17e-4d7b-40e1-802b-14bb682364c7 za pomocą polecenia /RedistUrl http://go.microsoft.com/fwlink/?LinkID=724436 lnmanifesturl http://go.microsoft.com/fwlink/?LinkID=724434 redistversion 112015 / noui "D:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist"  

ConfigMgrSetup.log:  

-   Błąd: Nie można zweryfikować podpisu authenticode 'd:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist\sqlncli.msi'.  

-   Błąd: Sprawdzenie podpisu pliku nie powiodło się dla 'd:\ConfigMgr\EasySetupPayload\037cd17e-4d7b-40e1-802b-14bb682364c7\redist\sqlncli.msi  

**Obejście**: Na serwerze lokacji zmodyfikuj następujący klucz rejestru zgodnie z poniższym wzorem, a następnie uruchom ponownie usługę SMS_Executive lub poczekaj maksymalnie 24 godziny na następny cykl pobierania automatycznego.  

-   **Klucz do edycji**: HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\WinTrust\Trust Providers\Software publikowania  

-   **Wartość stanu**:  Ustaw **146944** dziesiętną lub **0x00023e00** szesnastkowe  


###  <a name="setup-fails-when-using-redist-files-from-the-cdlatest-folder-with-a-manifest-verification-error"></a>Instalacja nie powiedzie się, używając plików redystrybucyjnych z dysku CD. Najnowsze folderu z powodu błędu weryfikacji manifestu
<!-- Source bug pending  -->

W przypadku uruchamiania Instalatora z dysku CD. Najnowszy folder utworzona dla wersji 1606 i używać plików redystrybucyjnych dołączone do tego dysku CD. Najnowsze folderu, instalacja zakończy się niepowodzeniem z powodu następujących błędów w dzienniku instalacji programu Configuration Manager:

  - BŁĄD: Sprawdzenie skrótu pliku defaultcategories.dll nie powiodło się
  - BŁĄD: Nie można zweryfikować manifestu. Nieprawidłowa wersja manifestu?

**Obejście problemu:**  Użyj jednej z następujących czynności:
 - Podczas instalacji wybierz do pobrania najnowszych plików redystrybucyjnych przez firmę Microsoft do użycia zamiast uwzględnionych w dysku CD. Najnowszy folder.
 - Ręcznie usuń *cd.latest\redist\languagepack\zhh* folder, a następnie uruchom ponownie Instalatora.

### <a name="service-connection-tool-throws-an-exception-when-sql-server-is-remote-or-when-shared-memory-is-disabled"></a>Narzędzia połączenia z usługą zgłasza wyjątek w przypadku zdalnego programu SQL server lub po wyłączeniu pamięci Shared Memory
Począwszy od wersji 1606 narzędzia połączenia z usługą generuje wyjątek, gdy spełniony jest jeden z następujących czynności:  
 -    Baza danych lokacji znajduje się zdalnie z komputera, który hostuje punkt połączenia usługi i używa niestandardowego portu (portu innego niż 1433)
 -     Baza danych lokacji znajduje się na tym samym serwerze co punkt połączenia usługi, ale protokół SQL **pamięci Shared Memory** jest wyłączona

Wyjątkiem jest podobny do następującego:
 - *Nieobsługiwany wyjątek: System.Data.SqlClient.SqlException: Wystąpił błąd związany z siecią lub wystąpieniem podczas ustanawiania połączenia z programem SQL Server. Serwer nie został znaleziony lub był niedostępny. Sprawdź, czy nazwa wystąpienia jest poprawna i czy programu SQL Server jest skonfigurowany do zezwalania na połączenia zdalne. (Dostawca: Dostawca nazwanych potoków, błąd: 40 - nie można otworzyć połączenia z programem SQL Server)--*

**Obejście**: Podczas używania narzędzia należy zmodyfikować rejestr serwera, który hostuje punkt połączenia usługi, aby uwzględnić informacje o porcie programu SQL Server:

   1.    Przed użyciem tego narzędzia, należy edytować następujący klucz rejestru i dodać numer portu, który jest używany do nazwy programu SQL Server:
    - Klucz:   HKLM\Microsoft\SMS\COMPONENTS\SMS_DMP_UPLOADER\
      - Wartość: &lt;Nazwa programu SQL Server >
    - Dodaj: **,&lt;PORT >**

    Na przykład, aby dodać port *15001* z serwerem o nazwie *testserver.test.net*, wynikowy klucz będzie: ***HKLM\Software\Microsoft\SMS\COMPONENTS\SMS_DMP_UPLOADER\testserver.test.NET,15001***

   2.    Po dodaniu portu w rejestrze, narzędzie powinny działać normalnie.  

   3.    Po zakończeniu zarówno dla korzystanie z narzędzia **— Połącz** i **— importowanie** kroków, zmienić wartość klucza rejestru do oryginalnej wartości.  




<!-- No current Backup and Recovery relenotes
## Backup and recovery
-->



## <a name="client-deployment-and-upgrade"></a>Wdrażanie i uaktualnianie klientów  

### <a name="client-installation-fails-with-error-code-0x8007064c"></a>Instalacja klienta kończy się niepowodzeniem z kodem błędu 0x8007064c
<!--- SMS 486973 -->

Podczas wdrażania klienta na komputerach z systemem Windows, instalacja nie powiedzie się. Plik ccmsetup.log zawiera wpis "pliku"C:\WINDOWS\ccmsetup\Silverlight.exe"zwrócił kod zakończenia błędu 1612. Niepowodzenie instalacji"następuje"InstallFromManifest nie powiodło się 0x8007064c".

**Obejście** przyczyną jest uszkodzony, wcześniej zainstalowanej wersji programu Silverlight. Można spróbować uruchomić następujące narzędzia na danym komputerze, aby rozwiązać ten problem: [https://support.microsoft.com/help/17588/fix-problems-that-block-programs-from-being-installed-or-removed](https://support.microsoft.com/help/17588/fix-problems-that-block-programs-from-being-installed-or-removed)




## <a name="operating-system-deployment"></a>Wdrożenie systemu operacyjnego  

### <a name="issue-with-the-windows-adk-for-windows-10-version-1511"></a>Problem z zestawem Windows ADK dla systemu Windows 10 (wersja 1511)  
Po uruchomieniu sekwencji zadań w programie Software Center, który używa środowiska Windows PE obrazu rozruchowego wersji 10.0.10586 z systemu Windows 10 ADK w wersji 1511, po ponownym uruchomieniu komputera w środowisku Windows PE, zakończy się niepowodzeniem, gdy "Inicjowanie urządzeń sprzętowych" z powodu błędu: **Inicjalizacja środowiska Preinstalacyjnego systemu Windows nie powiodło się. kod błędu 0x80220014**  

**Obejście**: Użyj oryginalnego zestawu Windows 10 ADK. Aby uzyskać więcej informacji zobacz następujące blogu zespołu programu Configuration Manager System Center: [Problem z systemem Windows ADK dla systemu Windows 10](http://blogs.technet.com/b/configmgrteam/archive/2015/11/20/issue-with-the-windows-adk-for-windows-10-version-1511.aspx)  

### <a name="dynamic-application-installation-fails-during-task-sequence-which-successfully-completes"></a>Występuje niepowodzenie instalacji aplikacji dynamicznej podczas sekwencji zadań, która kończy się pomyślnie  
Jeśli podczas wdrażania sekwencji zadań, która używa opcji **Zainstaluj aplikacje zgodnie z listą zmiennych dynamicznych**, instalacja jednej z aplikacji nie powiedzie się z jakiegokolwiek powodu, sekwencja zadań zgłosi powodzenie operacji. Dzieje się tak niezależnie od tego, jak zostały skonfigurowane następujące opcje:  

-   **Kontynuuj przy błędzie** (na karcie Opcje w kroku instalacji aplikacji)  

-   **Jeśli instalacja aplikacji nie powiedzie się, kontynuuj instalowanie pozostałych aplikacji z listy** (na karcie Właściwości w kroku instalowania aplikacji)  

Możesz wyświetlić plik smsts.log, aby ustalić, czy instalacja aplikacji zakończyła się niepowodzeniem.  

**Obejście**: Użyj **_TSAppInstallStatus** zmiennej jako warunku w kolejnych krokach sekwencji zadań z warunkiem niepowodzenia sekwencji zadań, jeśli wystąpił błąd dotyczący jednej z aplikacji dynamicznych.  

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

### <a name="when-a-high-risk-deployment-dialog-is-visible-to-a-user-subsequent-high-risk-dialogs-with-a-sooner-deadline-are-not-displayed"></a>Jeśli okno dialogowe wdrożenie wysokiego ryzyka jest widoczny dla użytkownika, kolejne o wysokim ryzyku okien dialogowych z ostatecznym terminem przypadającym wcześniej nie są wyświetlane
Po utworzeniu i wdrożenia o wysokim ryzyku zadań do użytkowników o wysokim ryzyku okno dialogowe jest wyświetlany użytkownikowi. Jeśli użytkownik nie zamknąć okno dialogowe, tworzenie i wdrażanie inne wdrożenie o wysokim ryzyku z ostatecznym terminem przypadającym wcześniej niż pierwszy, użytkownik nie otrzyma okno dialogowe zaktualizowane dopóki zamknąć okno dialogowe oryginalnego. Wdrożenia będą nadal działać w skonfigurowanym terminów.

**Obejście**:  
Użytkownik należy zamknąć okno dialogowe dla pierwszego wdrożenia wysokiego ryzyka wyświetlić okno dialogowe dalej wdrożenia wysokiego ryzyka.

## <a name="software-updates"></a>Aktualizacje oprogramowania

### <a name="importing-an-office-365-client-settings-from-a-configuration-file-fails-when-it-contains-unsupported-languages"></a>Importowanie ustawień klienta usługi Office 365 z pliku konfiguracji nie powiedzie się, gdy zawiera nieobsługiwanych językach
Podczas importowania ustawień klienta usługi Office 365 z istniejący plik konfiguracyjny XML, a plik zawiera języki, które nie są obsługiwane przez klienta usługi Office 365 ProPlus, wystąpi błąd. Aby uzyskać więcej informacji, zobacz [wdrażania aplikacji usługi Office 365 na klientach z poziomu pulpitu nawigacyjnego zarządzania klienta usługi Office 365](/sccm/sum/deploy-use/manage-office-365-proplus-updates#to-deploy-office-365-apps-to-clients-from-the-office-365-client-management-dashboard).

**Obejście**:    
Użyj tylko [języki obsługiwane przez klienta usługi Office 365 ProPlus](https://technet.microsoft.com/library/cc179219&#40;v=office.16&#41;.aspx) w pliku konfiguracji XML.  

## <a name="mobile-device-management"></a>Zarządzanie urządzeniami przenośnymi  

### <a name="cannot-create-an-enrollment-profile-on-a-primary-site"></a>Nie można utworzyć profilu rejestracji w lokacji głównej  
Administrator nie może utworzyć profilu rejestracji w konsoli administracyjnej programu System Center Configuration Manager, która jest połączona z lokacją główną. Przy próbie zarejestrowania administratorowi jest wyświetlany błąd "token usługi DEP nie został zaktualizowany. Przekaż DEP token"w Kreatorze profilu rejestracji. Ten błąd występuje mimo tego, że prawidłowy token usługi DEP został przekazany do centralnej lokacji administracyjnej.  

**Obejście**: Utwórz profil rejestracji w konsoli programu System Center Configuration Manager, która jest połączona z lokacją administracji centralnej.  

### <a name="dep-cannot-use-non-alpha-numeric-characters-in-enrollment-profiles"></a>W usłudze DEP nie można używać znaków innych niż alfanumeryczne w profilach rejestracji  
W profilach rejestracji skojarzonych z profilem rejestracji urządzeń (DEP) firmy Apple nie można używać znaków innych niż alfanumeryczne w polach **Nazwa**, **Opis**, **Dział** i **Numer telefonu** dla profilu rejestracji, gdy usługa DEP jest włączona. W przypadku użycia w tych polach znaków innych niż alfanumeryczne profil rejestracji zostanie utworzony, ale nie będzie można go przekazać do firmy Apple. Serwer firmy Apple nie przekaże żadnego komunikatu o błędzie ani ostrzeżenia, a profile nie zostaną wdrożone na urządzeniach zarządzanych przez usługę DEP.  

**Obejście**: Brak.

### <a name="full-wipe-disables-windows-10-devices-with-less-than-4-gb-ram"></a>Całkowite wyczyszczenie powoduje wyłączenie urządzeń z systemem Windows 10 z pamięcią RAM mniejszą niż 4 GB

Przeprowadzenie całkowitego czyszczenia danych w urządzeniu z systemem Windows 10 RTM (wersje starsze niż 1511) z pamięcią RAM mniejszą niż 4 GB sprawi, że urządzenie nie będzie nadawać się do użytku. Po podjęciu próby wyczyszczenia danych urządzenie nie reaguje i nie można go uruchomić.

**Obejście**: Upewnij się, że RTM komputerów z systemem Windows 10 mają co najmniej 4 GB pamięci RAM dostępnej przed wykonaniem pełne czyszczenie danych na urządzeniu. Aby wyświetlić numer wersji systemu Windows 10 urządzenia, w wierszu polecenia wprowadź „winver”. Jeśli urządzenie już zostało wyczyszczone i nie odpowiada, możesz użyć rozruchowego dysku USB z systemem Windows 10 USB do uruchomienia urządzenia i przywrócenia dostępu do niego.

### <a name="when-a-user-belongs-to-two-or-more-user-collections-that-a-terms-and-conditions-policy-is-deployed-to-the-user-sees-multiple-sets-of-the-same-terms"></a>Jeśli użytkownik należy do co najmniej dwóch kolekcji użytkowników, w których są wdrożone zasady warunków i postanowień, użytkownikowi będzie wyświetlanych wiele zestawów tych samych warunków  

Gdy administrator wdraża zestaw warunków w wielu kolekcjach użytkowników, a użytkownik należy do więcej niż jednej z nich, dla tego użytkownika zostanie wyświetlonych wiele kopii identycznych warunków podczas otwierania Portalu firmy.  Na przykład, jeśli użytkownik o nazwie "To dla użytkownika Użytkownikprzykładowy" jest elementem członkowskim dwóch różnych kolekcji użytkowników, jeden o nazwie "Pracownicyfirmyfte" i "Kolekcji Pracownicyfirmyna," "i warunki i postanowienia o nazwie"W nazwie Warunkifirmy"jest wdrożony w kolekcji Pracownicyfirmyfte i w kolekcji Pracownicyfirmyna, to dla użytkownika Użytkownikprzykładowy zostaną wyświetlone dwa identyczne zestawy w o nazwie Warunkifirmy na stronie akceptacji warunków. Ponieważ użytkownicy mogą tylko zaakceptować lub odrzucić wszystkie warunki, nie ma ryzyka wystąpienia niejednoznacznej akceptacji, oznaczającej zarówno zaakceptowanie, jak i odrzucenie warunków przez użytkownika. Raport dotyczący akceptacji warunków i postanowień zawiera tylko jeden wiersz dla każdego zestawu warunków i każdego użytkownika, więc nie ma błędów w tym raporcie. Jedynym wynikiem jest to, że użytkownik będzie widział dwa zestawy warunków na stronie akceptacji.  

**Obejście**: Upewnij się, że każdy użytkownik znajduje się tylko do jednej kolekcji, do której są wdrożone warunki.  

### <a name="android-for-work-email-profiles-that-use-certificate-authentication-are-not-applied-to-devices"></a>Android pracy profilów poczty e-mail, które korzystają z certyfikatu uwierzytelniania nie są stosowane do urządzeń
<!--  487657 -->
Po utworzeniu systemu Android dla profilu poczty e-mail z pracy, dostępne są dwie opcje dla uwierzytelniania. Jeden z nich jest nazwa użytkownika i hasło, a drugi to certyfikaty. W tej chwili nie działa opcja certyfikatów. Jeśli profil jest tworzony przy użyciu metody uwierzytelniania ustawioną **certyfikaty**monitowany o ręczne wprowadzenie szczegóły konta poczty e-mail i profil nie ma zastosowania do urządzenia.

**OBEJŚCIE**: Brak. Administratorzy muszą użyj **nazwy użytkownika i hasła** opcji lub poczekaj, aż ten problem został rozwiązany.

## <a name="reports-and-monitoring"></a>Raporty i monitorowanie  

### <a name="the-health-attestation-report-is-empty-even-though-health-attestation-data-was-previously-collected"></a>Raport zaświadczania o kondycji jest pusty mimo wcześniejszego zebrania danych zaświadczania o kondycji  
Jeśli użytkownik administracyjny z rolą zabezpieczeń obejmującą uprawnienie **Odczyt** dla grupy uprawnień **Zaświadczanie o kondycji** wyświetla raport zaświadczania o kondycji, raport ten jest pusty i dane nie są wyświetlane. Wynika to z faktu, że uprawnienia do wyświetlania danych w raporcie zaświadczania o kondycji są połączone z grupą uprawnień **Koligacja urządzenia użytkownika** zamiast z grupą uprawnień zaświadczania o kondycji.  

Ten problem ma wpływ na System Center Configuration Manager z aktualizacją 1602 i powinien zostać rozwiązany w przyszłej aktualizacji.  

**Obejście**: Przypisz użytkownika administracyjnego z grupy zabezpieczeń, która zawiera **odczytu** uprawnienia do **koligacje urządzenia użytkownika** grupy uprawnień.  

### <a name="conditional-access"></a>Dostęp warunkowy  

#### <a name="the-same-user-collection-is-not-blocked-from-being-added-to-both-exempted-and-targeted-collections"></a>Jedną kolekcję użytkownika można dodać równocześnie do kolekcji wykluczonych i docelowych.  
Dzieje się to tylko w przypadku dodania jednego elementu **Kolekcja użytkownika** do strony **Kolekcja wykluczona** **przed** dodaniem jej do strony **Kolekcja docelowa**.  Jeśli element **Kolekcja użytkownika** zostanie dodana najpierw do strony **Kolekcje docelowe**, a następnie nastąpi próba dodania tego samego elementu **Kolekcja użytkownika** do strony **Kolekcja wykluczona**, powinien zostać wyświetlony normalny komunikat dotyczący blokowania.  

Ten problem dotyczy programu System Center Configuration Manager dostępu warunkowego dla **lokalnego programu Exchange** z aktualizacją 1602 i powinien zostać rozwiązany w przyszłej aktualizacji.  

**Obejście problemu:** Dodaj **kolekcji użytkowników** do **kolekcje docelowe** przed wybraniem **kolekcji użytkowników** na **kolekcja wykluczona** strony lub upewnij się, że nie są takie same Dodawanie **kolekcji użytkowników** zarówno docelowe i wykluczone kolekcje.

## <a name="endpoint-protection"></a>Program Endpoint Protection
<!--  Product Studio bug 485370 added 04 19 2017 -->
### <a name="antimalware-policy-fails-to-apply-on-windows-server-2016-core"></a>Zasady ochrony przed złośliwym kodem nie powiedzie się do zastosowania w systemie Windows Server 2016 Core
Zasady ochrony przed złośliwym oprogramowaniem nie powiodło się zastosować w systemie Windows Server 2016 Core.  Kod błędu to 0x80070002.  Brakująca zależność ConfigSecurityPolicy.exe nie istnieje.

**Obejście problemu:**  Ten problem został rozwiązany przez [artykułu bazy wiedzy 4019472](https://support.microsoft.com/help/4019472/windows-10-update-kb4019472) rozproszonych 9 maja 2017 r.

<!-- Product Studio bug 462286 added  05 25 2017 and valid until July 2017 GA release -->
### <a name="windows-defender-advanced-threat-protection-policies-fail-on-older-client-agents"></a>Zasady usługi Windows Defender Advanced Threat Protection zakończyć się niepowodzeniem na starszą agentów klientów

Zasady usługi Windows Defender Advanced Threat Protection utworzone na podstawie 1610 wersji programu Configuration Manager lub nowszego serwera lokacji nie dotyczą 1606 wersji programu Configuration Manager i starszych klientów.  Klienci są nie na dodawanej i oceny zasad zgłosi błąd. **Stan wdrożenia** w konfiguracji usługi Windows Defender Advanced Threat Protection zawiera **błąd**.

**OBEJŚCIE**: Uaktualnij klienta programu Configuration Manager do wersji 1610 lub nowszej.

