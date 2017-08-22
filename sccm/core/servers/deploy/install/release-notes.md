---
title: "Informacje o wersji — programu Configuration Manager | Dokumentacja firmy Microsoft"
description: "Te informacje można uzyskać pilnych problemów, które nie zostały jeszcze rozwiązane w produkcie lub omówione w artykule bazy wiedzy Microsoft Knowledge Base."
ms.custom: na
ms.date: 08/21/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: 030947fd-f5e0-4185-8513-2397fb2ec96f
caps.latest.revision: "41"
caps.handback.revision: "0"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 24f30bddb345e3a08d4b655d89693c226005cb0e
ms.sourcegitcommit: 06aef618f72c700f8a716a43fb8eedf97c62a72b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2017
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
Po uruchomieniu aktualizacji w miejscu do konsoli przy użyciu ConsoleSetup.exe z folderu instalacji serwerów lokacji, ostatnio zainstalowanych pakietów językowych mogą nie być dostępne. W takim przypadku:
- Lokalizacji uruchomiono wersję 1610 lub 1702.
- Konsola jest aktualizowany w miejscu przy użyciu ConsoleSetup.exe z folderu instalacji serwera lokacji.

Gdy wystąpi ten problem, ponownie konsoli nie używa najnowszy zestaw pakietów językowych, które zostały skonfigurowane. Nie są zwracane nie błędy, ale nie ma zmieni pakiety językowe dostępne w konsoli.  

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


### <a name="an-update-is-stuck-with-a-state-of-downloading-in-the-updates-and-servicing-node-of-the-configuration-manager-console"></a>Aktualizacja jest wstrzymywana podczas pobierania w węźle Aktualizacje i obsługa konsoli programu Configuration Manager  
<!-- Source bug pending. Consider move to core content.  8/15 Seeking validation of issue from Dev.  -->
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
<!-- Source bug pending    8/15 Seeking validation of issue from Dev.   -->

W przypadku uruchamiania Instalatora z dysku CD. Najnowszy folder utworzona dla wersji 1606 i używać plików redystrybucyjnych dołączone do tego dysku CD. Najnowsze folderu, instalacja zakończy się niepowodzeniem z powodu następujących błędów w dzienniku instalacji programu Configuration Manager:

  - BŁĄD: Sprawdzenie skrótu pliku defaultcategories.dll nie powiodło się
  - BŁĄD: Nie można zweryfikować manifestu. Nieprawidłowa wersja manifestu?

**Obejście problemu:**  Użyj jednej z następujących czynności:
 - Podczas instalacji wybierz do pobrania najnowszych plików redystrybucyjnych przez firmę Microsoft do użycia zamiast uwzględnionych w dysku CD. Najnowszy folder.
 - Ręcznie usuń *cd.latest\redist\languagepack\zhh* folder, a następnie uruchom ponownie Instalatora.


### <a name="service-connection-tool-throws-an-exception-when-sql-server-is-remote-or-when-shared-memory-is-disabled"></a>Narzędzia połączenia z usługą zgłasza wyjątek w przypadku zdalnego programu SQL server lub po wyłączeniu pamięci Shared Memory
<!-- 479223   Fixed in 1702 and later   -->
Począwszy od wersji 1606 narzędzia połączenia z usługą generuje wyjątek, gdy spełniony jest jeden z następujących czynności:  
 -  Baza danych lokacji znajduje się zdalnie z komputera, który hostuje punkt połączenia usługi i używa niestandardowego portu (portu innego niż 1433)
 -  Baza danych lokacji znajduje się na tym samym serwerze co punkt połączenia usługi, ale protokół SQL **pamięci Shared Memory** jest wyłączona

Wyjątkiem jest podobny do następującego:
 - *Nieobsługiwany wyjątek: System.Data.SqlClient.SqlException: Wystąpił błąd związany z siecią lub wystąpieniem podczas ustanawiania połączenia z programem SQL Server. Serwer nie został znaleziony lub był niedostępny. Sprawdź, czy nazwa wystąpienia jest poprawna i czy programu SQL Server jest skonfigurowany do zezwalania na połączenia zdalne. (Dostawca: Dostawca nazwanych potoków, błąd: 40 - nie można otworzyć połączenia z programem SQL Server)--*

**Obejście**: Podczas używania narzędzia należy zmodyfikować rejestr serwera, który hostuje punkt połączenia usługi, aby uwzględnić informacje o porcie programu SQL Server:

   1.   Przed użyciem tego narzędzia, należy edytować następujący klucz rejestru i dodać numer portu, który jest używany do nazwy programu SQL Server:
    - Klucz:   HKLM\Microsoft\SMS\COMPONENTS\SMS_DMP_UPLOADER\
      - Wartość: &lt;Nazwa programu SQL Server >
    - Dodaj: **,&lt;PORT >**

    Na przykład, aby dodać port *15001* z serwerem o nazwie *testserver.test.net*, wynikowy klucz będzie: ***HKLM\Software\Microsoft\SMS\COMPONENTS\SMS_DMP_UPLOADER\testserver.test.NET,15001***

   2.   Po dodaniu portu w rejestrze, narzędzie powinny działać normalnie.  

   3.   Po zakończeniu zarówno dla korzystanie z narzędzia **— Połącz** i **— importowanie** kroków, zmienić wartość klucza rejestru do oryginalnej wartości.  


<!-- ## Backup and recovery  -->


## <a name="client-deployment-and-upgrade"></a>Wdrażanie i uaktualnianie klientów  

### <a name="client-installation-fails-with-error-code-0x8007064c"></a>Instalacja klienta kończy się niepowodzeniem z kodem błędu 0x8007064c
<!--- SMS 486973 -->
Podczas wdrażania klienta na komputerach z systemem Windows, instalacja nie powiedzie się. Plik ccmsetup.log zawiera wpis "pliku"C:\WINDOWS\ccmsetup\Silverlight.exe"zwrócił kod zakończenia błędu 1612. Niepowodzenie instalacji"następuje"InstallFromManifest nie powiodło się 0x8007064c".

**Obejście** przyczyną jest uszkodzony, wcześniej zainstalowanej wersji programu Silverlight. Można spróbować uruchomić następujące narzędzia na danym komputerze, aby rozwiązać ten problem: [https://support.microsoft.com/help/17588/fix-problems-that-block-programs-from-being-installed-or-removed](https://support.microsoft.com/help/17588/fix-problems-that-block-programs-from-being-installed-or-removed)

## <a name="operating-system-deployment"></a>Wdrożenie systemu operacyjnego  

### <a name="if-the-boot-image-contains-drivers-the-image-fails-to-reload-the-current-windows-pe-version-from-the-windows-assessment-and-deployment-kit-adk"></a>Jeśli obraz rozruchowy zawiera sterowniki, obrazu nie powiodło się ponowne załadowanie bieżącą wersję środowiska Windows PE z systemu Windows Assessment and Deployment Kit (ADK)
<!-- 495087 -->
Kreator aktualizacji punktu dystrybucji służy do zaktualizowania punktów dystrybucji o obraz rozruchowy przechowywany za pomocą najnowszej wersji systemu Windows PE z katalogu instalacyjnego systemu Windows Assessment and Deployment Kit (ADK). Aby zaktualizować, otwórz Kreatora aktualizacji punktów dystrybucji i wybierz **ponownie załadować ten obraz rozruchowy z bieżącą wersją PE z zestawu Windows ADK**.

Jednak jeśli obraz rozruchowy zawiera sterowniki, aktualizacja nie powiedzie się. Zamiast tego kreatora ładuje obraz z zestawu ADK, wyświetla okno dialogowe wyjątek użytkownika można odrzucić, a następnie wyświetla ekran Powodzenie. Jednak najnowsze składniki klienta programu Configuration Manager nie można dodać do obrazu rozruchowego. Obraz rozruchowy nie będzie aktualizowana w punkcie dystrybucji

**Obejście**: Uruchom Kreatora aktualizacji punktów dystrybucji dwa razy.

1. Uruchom kreatora **ponownie załadować ten obraz rozruchowy z bieżącą wersją środowiska Preinstalacyjnego systemu Windows z zestawu Windows ADK** wybrane. Spowoduje to pobrać najnowszą wersję środowiska Windows PE.
2. Uruchom kreatora ponownie, podając **ponownie załadować ten obraz rozruchowy z bieżącą wersją środowiska Preinstalacyjnego systemu Windows z zestawu Windows ADK** niezaznaczone. Ten znacząco Pobierz najnowszego klienta pliki binarne i zaktualizować obraz wysięgnik w punkcie dystrybucji.

### <a name="servicing-plans-create-a-lot-of-duplicate-software-update-groups-and-deployments-by-default"></a>Plany obsługi tworzą domyślnie wiele powielonych grup aktualizacji oprogramowania i wdrożeń  
Domyślnie kreator tworzenia planów obsługi jest uruchamiany obecnie po każdej synchronizacji aktualizacji oprogramowania. Przy każdym uruchomieniu tworzy on nową grupę aktualizacji oprogramowania i wdrożenia. W przypadku harmonogramu synchronizacji aktualizacji oprogramowania uruchamianego kilka razy dzienne kreator tworzenia planów obsługi każdego dnia będzie tworzył wiele prawdopodobnie identycznych grup aktualizacji oprogramowania i wdrożeń.  

**Obejście**:    
po utworzeniu planu obsługi otwórz właściwości planu, przejdź do karty **Harmonogram szacowania**, wybierz pozycję **Uruchom tę regułę według harmonogramu**, kliknij pozycję **Dostosuj** i utwórz harmonogram niestandardowy. Można na przykład określić uruchamianie planu obsługi co 60 dni.  


### <a name="when-a-high-risk-deployment-dialog-is-visible-to-a-user-subsequent-high-risk-dialogs-with-a-sooner-deadline-are-not-displayed"></a>Jeśli okno dialogowe wdrożenie wysokiego ryzyka jest widoczny dla użytkownika, kolejne o wysokim ryzyku okien dialogowych z ostatecznym terminem przypadającym wcześniej nie są wyświetlane
<!-- Fixed in 1702 and later -->
Po utworzeniu i wdrożenia o wysokim ryzyku zadań do użytkowników o wysokim ryzyku okno dialogowe jest wyświetlany użytkownikowi. Jeśli użytkownik nie zamknąć okno dialogowe, tworzenie i wdrażanie inne wdrożenie o wysokim ryzyku z ostatecznym terminem przypadającym wcześniej niż pierwszy, użytkownik nie otrzyma okno dialogowe zaktualizowane dopóki zamknąć okno dialogowe oryginalnego. Wdrożenia będą nadal działać w skonfigurowanym terminów.

**Obejście**:  
Użytkownik należy zamknąć okno dialogowe dla pierwszego wdrożenia wysokiego ryzyka wyświetlić okno dialogowe dalej wdrożenia wysokiego ryzyka.



## <a name="software-updates"></a>Aktualizacje oprogramowania

### <a name="importing-an-office-365-client-settings-from-a-configuration-file-fails-when-it-contains-unsupported-languages"></a>Importowanie ustawień klienta usługi Office 365 z pliku konfiguracji nie powiedzie się, gdy zawiera nieobsługiwanych językach
<!-- 489258  Fixed in 1706  -->
Podczas importowania ustawień klienta usługi Office 365 z istniejący plik konfiguracyjny XML, a plik zawiera języki, które nie są obsługiwane przez klienta usługi Office 365 ProPlus, wystąpi błąd. Aby uzyskać więcej informacji, zobacz [wdrażania aplikacji usługi Office 365 na klientach z poziomu pulpitu nawigacyjnego zarządzania klienta usługi Office 365](/sccm/sum/deploy-use/manage-office-365-proplus-updates#to-deploy-office-365-apps-to-clients-from-the-office-365-client-management-dashboard).

**Obejście**:    
Użyj tylko [języki obsługiwane przez klienta usługi Office 365 ProPlus](https://technet.microsoft.com/library/cc179219&#40;v=office.16&#41;.aspx) w pliku konfiguracji XML.  



## <a name="mobile-device-management"></a>Zarządzanie urządzeniami przenośnymi  

### <a name="full-wipe-disables-windows-10-devices-with-less-than-4-gb-ram"></a>Całkowite wyczyszczenie powoduje wyłączenie urządzeń z systemem Windows 10 z pamięcią RAM mniejszą niż 4 GB
Przeprowadzenie całkowitego czyszczenia danych w urządzeniu z systemem Windows 10 RTM (wersje starsze niż 1511) z pamięcią RAM mniejszą niż 4 GB sprawi, że urządzenie nie będzie nadawać się do użytku. Po podjęciu próby wyczyszczenia danych urządzenie nie reaguje i nie można go uruchomić.

**Obejście**: Upewnij się, że RTM komputerów z systemem Windows 10 mają co najmniej 4 GB pamięci RAM dostępnej przed wykonaniem pełne czyszczenie danych na urządzeniu. Aby wyświetlić numer wersji systemu Windows 10 urządzenia, w wierszu polecenia wprowadź „winver”. Jeśli urządzenie już zostało wyczyszczone i nie odpowiada, możesz użyć rozruchowego dysku USB z systemem Windows 10 USB do uruchomienia urządzenia i przywrócenia dostępu do niego.


### <a name="when-a-user-belongs-to-two-or-more-user-collections-that-a-terms-and-conditions-policy-is-deployed-to-the-user-sees-multiple-sets-of-the-same-terms"></a>Jeśli użytkownik należy do co najmniej dwóch kolekcji użytkowników, w których są wdrożone zasady warunków i postanowień, użytkownikowi będzie wyświetlanych wiele zestawów tych samych warunków  
<!-- 454394    -->
Gdy administrator wdraża zestaw warunków w wielu kolekcjach użytkowników, a użytkownik należy do więcej niż jednej z nich, dla tego użytkownika zostanie wyświetlonych wiele kopii identycznych warunków podczas otwierania Portalu firmy.  Na przykład, jeśli użytkownik o nazwie "To dla użytkownika Użytkownikprzykładowy" jest elementem członkowskim dwóch różnych kolekcji użytkowników, jeden o nazwie "Pracownicyfirmyfte" i "Kolekcji Pracownicyfirmyna," "i warunki i postanowienia o nazwie"W nazwie Warunkifirmy"jest wdrożony w kolekcji Pracownicyfirmyfte i w kolekcji Pracownicyfirmyna, to dla użytkownika Użytkownikprzykładowy zostaną wyświetlone dwa identyczne zestawy w o nazwie Warunkifirmy na stronie akceptacji warunków. Ponieważ użytkownicy mogą tylko zaakceptować lub odrzucić wszystkie warunki, nie ma ryzyka wystąpienia niejednoznacznej akceptacji, oznaczającej zarówno zaakceptowanie, jak i odrzucenie warunków przez użytkownika. Raport dotyczący akceptacji warunków i postanowień zawiera tylko jeden wiersz dla każdego zestawu warunków i każdego użytkownika, więc nie ma błędów w tym raporcie. Jedynym wynikiem jest to, że użytkownik będzie widział dwa zestawy warunków na stronie akceptacji.  

**Obejście**: Upewnij się, że każdy użytkownik znajduje się tylko do jednej kolekcji, do której są wdrożone warunki.  


### <a name="android-for-work-email-profiles-that-use-certificate-authentication-are-not-applied-to-devices"></a>Android pracy profilów poczty e-mail, które korzystają z certyfikatu uwierzytelniania nie są stosowane do urządzeń
<!--  487657      -->
Po utworzeniu systemu Android dla profilu poczty e-mail z pracy, dostępne są dwie opcje dla uwierzytelniania. Jeden z nich jest nazwa użytkownika i hasło, a drugi to certyfikaty. W tej chwili nie działa opcja certyfikatów. Jeśli profil jest tworzony przy użyciu metody uwierzytelniania ustawioną **certyfikaty**monitowany o ręczne wprowadzenie szczegóły konta poczty e-mail i profil nie ma zastosowania do urządzenia.

**OBEJŚCIE**: Brak. Administratorzy muszą użyj **nazwy użytkownika i hasła** opcji lub poczekaj, aż ten problem został rozwiązany.



<!-- ## Reports and monitoring    -->
<!-- ## Conditional access   -->


## <a name="endpoint-protection"></a>Program Endpoint Protection

### <a name="antimalware-policy-fails-to-apply-on-windows-server-2016-core"></a>Zasady ochrony przed złośliwym kodem nie powiedzie się do zastosowania w systemie Windows Server 2016 Core
<!--  Product Studio bug 485370 added 04 19 2017   Fixed in 1702 -->
Zasady ochrony przed złośliwym oprogramowaniem nie powiodło się zastosować w systemie Windows Server 2016 Core.  Kod błędu to 0x80070002.  Brakująca zależność ConfigSecurityPolicy.exe nie istnieje.

**Obejście problemu:**  Ten problem został rozwiązany przez [artykułu bazy wiedzy 4019472](https://support.microsoft.com/help/4019472/windows-10-update-kb4019472) rozproszonych 9 maja 2017 r.


### <a name="windows-defender-advanced-threat-protection-policies-fail-on-older-client-agents"></a>Zasady usługi Windows Defender Advanced Threat Protection zakończyć się niepowodzeniem na starszą agentów klientów
<!-- Product Studio bug 462286 added  05 25 2017 and valid until July 2017 GA release      Fixed in 1610 -->
Zasady usługi Windows Defender Advanced Threat Protection utworzone na podstawie 1610 wersji programu Configuration Manager lub nowszego serwera lokacji nie dotyczą 1606 wersji programu Configuration Manager i starszych klientów.  Klienci są nie na dodawanej i oceny zasad zgłosi błąd. **Stan wdrożenia** w konfiguracji usługi Windows Defender Advanced Threat Protection zawiera **błąd**.

**OBEJŚCIE**: Uaktualnij klienta programu Configuration Manager do wersji 1610 lub nowszej.
