---
title: Uaktualnienie do programu System Center Configuration Manager | Dokumentacja firmy Microsoft
description: "Poznaj etapy uruchamiania pomyślnego uaktualnienia w miejscu z lokacji i hierarchii programu System Center 2012 Configuration Manager."
ms.custom: na
ms.date: 05/02/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: get-started-article
ms.assetid: c64e7483-b4bb-4738-95f4-ecdaeb6a2ba6
caps.latest.revision: 21
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d940fd1bbf96767d44f8c55315e814be55a83897
ms.openlocfilehash: 9e58ab8dd892adf25429564adfd6f86849ddcbdf
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="upgrade-to-system-center-configuration-manager"></a>Uaktualnianie do programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

Można uruchomić uaktualnienie w miejscu uaktualnienia do programu System Center Configuration Manager z lokacji i hierarchii programu System Center 2012 Configuration Manager.  

 Przed uaktualnieniem programu System Center 2012 Configuration Manager, należy przygotować witryn, które wymaga usunięcia określonej konfiguracji, które można zapobiec pomyślnego uaktualnienia, a następnie wykonaj sekwencji uaktualniania, gdy chodzi o więcej niż jednej lokacji.  

 > [!TIP]
 > Podczas zarządzania lokacji programu System Center Configuration Manager i infrastruktury hierarchii, warunki *uaktualnienia*, *aktualizacji*, i *zainstalować* są używane do opisywania trzy oddzielne pojęcia. Aby dowiedzieć się, jak używać każdego terminu, zobacz [o uaktualnienie, aktualizacji i instalacji](/sccm/core/understand/upgrade-update-install).

##  <a name="bkmk_path"></a> Ścieżki uaktualnienia w miejscu  

**Uaktualnij program do wersji 1702**   
Jeżeli wersja 1702 linii bazowej nośników, można uaktualnić do pełni licencjonowaną wersję programu System Center Configuration Manager wersji 1702 następujące:   
-      Instalowanie programu System Center Configuration Manager w wersji 1702 oceny
-      System Center 2012 Configuration Manager z dodatkiem Service Pack 1
-      System Center 2012 Configuration Manager z dodatkiem Service Pack 2
-      System Center 2012 R2 Configuration Manager
-      System Center 2012 R2 Configuration Manager z dodatkiem Service Pack 1

**Uaktualnij program do wersji 1606**  
Na 15 grudnia 2016 nośnika linii bazowej dla wersji 1606 wydano dodanie obsługi dodatkowych scenariuszy uaktualniania. To nowe wydanie obsługuje uaktualnienia następujące polecenie, aby w pełni licencjonowaną wersję programu System Center Configuration Manager wersji 1606:  
-   Instalowanie programu System Center Configuration Manager wersji 1606 oceny
-   W przypadku instalacji release candidate programu System Center Configuration Manager  
-   System Center 2012 Configuration Manager z dodatkiem Service Pack 1  
-   System Center 2012 Configuration Manager z dodatkiem Service Pack 2  
-   System Center 2012 R2 Configuration Manager  
-   System Center 2012 R2 Configuration Manager z dodatkiem Service Pack 1  

Jeśli za pomocą nośników linii bazowej 1606 wersji pobrane przed 15 grudnia 2016 można uaktualnić tylko następujące do w pełni licencjonowaną wersję programu System Center Configuration Manager wersji 1606:
-   Instalowanie programu System Center Configuration Manager wersji 1606 oceny
-   System Center 2012 Configuration Manager z dodatkiem Service Pack 2
-   System Center 2012 R2 Configuration Manager z dodatkiem Service Pack 1

<!-- Version 1511 has now dropped out of support
**Upgrade to version 1511**  
When you have version 1511 baseline media, you can upgrade the following to a fully licensed  version of System Center Configuration Manager version 1511:  
-   An evaluation install of System Center Configuration Manager version 1511
-   A release candidate install of System Center Configuration Manager  
-   System Center 2012 Configuration Manager with Service Pack 1  
-   System Center 2012 Configuration Manager with Service Pack 2  
-   System Center 2012 R2 Configuration Manager  
-   System Center 2012 R2 Configuration Manager with Service Pack 1  
-->


> [!TIP]  
>  Po uaktualnieniu z wersji programu System Center 2012 Configuration Manager do bieżącej gałęzi, można uprościć proces uaktualniania. Aby uzyskać więcej informacji, zobacz następujące tematy:  
>   
>  -   Sekcja [Wersje linii bazowej i aktualizacji](../../../../core/servers/manage/updates.md#bkmk_Baselines) w temacie [Aktualizacje programu System Center Configuration Manager](../../../../core/servers/manage/updates.md)  
>  -   [Dysk CD. Najnowsze folderu dla programu System Center Configuration Manager](../../../../core/servers/manage/the-cd.latest-folder.md)  

 **Nie są obsługiwane następujące scenariusze:**  
-   Uaktualnienie programu System Center Configuration Manager Technical Preview do w pełni licencjonowaną nie jest obsługiwane.  Wersja Technical Preview może zostać uaktualniona tylko do nowszej wersji Technical Preview.  

-   Migracja z Technical Preview do w pełni licencjonowaną wersję nie jest obsługiwane.  

##  <a name="bkmk_checklist"></a> Listy kontrolne uaktualniania  
 Następujące listy wyboru może pomóc w zaplanowaniu pomyślnego uaktualnienia programu System Center Configuration Manager.  

### <a name="before-you-upgrade"></a>Przed uaktualnieniem  

**Przegląd środowiska System Center 2012 Configuration Manager** i rozwiązywanie problemów, jak określono w KB4018655: [Klientów programu Configuration Manager ponownie zainstaluj co pięć godzin z powodu zadanie cykliczne ponawiania i może spowodować uaktualnienie klientów lub przypadkowego](https://support.microsoft.com/help/4018655).

**Upewnij się, że środowisko przetwarzania danych spełnia obsługiwane konfiguracje** są niezbędne do uaktualnienia programu System Center Configuration Manager:  

Sprawdź systemy operacyjne serwerów używane do hostowania ról systemu lokacji:  

-   Niektórych starszych systemów operacyjnych obsługiwanych przez System Center 2012 Configuration Manager nie są obsługiwane przez program System Center Configuration Manager, a role systemu lokacji w tych systemach operacyjnych musi być przeniesiony lub usunięty przed uaktualnieniem. Przegląd [obsługiwanych systemów operacyjnych dla serwerów systemu lokacji](../../../../core/plan-design/configs/supported-operating-systems-for-site-system-servers.md) dokumentacji.   
-   Narzędzie sprawdzania wymagań wstępnych dla programu Configuration Manager nie weryfikuje wymagań wstępnych dotyczących ról systemu lokacji na serwerze lokacji lub na zdalnych systemów lokacji  

Sprawdź wymagania wstępne dla wszystkich komputerów hostujących role systemu lokacji:  

-   Na przykład do wdrażania systemu operacyjnego, System Center Configuration Manager korzysta z systemu Windows 10 Assessment and Deployment Kit (Windows ADK). Przed uruchomieniem Instalatora należy pobrać zestaw Windows 10 ADK i zainstalować go na serwerze lokacji i na każdym komputerze, na którym jest uruchamiane wystąpienie dostawcy programu SMS.  

Ogólne informacje o obsługiwanych platformach i konfiguracjach wymagań wstępnych znajdują się w temacie [Obsługiwane konfiguracje programu System Center Configuration Manager](../../../../core/plan-design/configs/supported-configurations.md).  

Informacje dotyczące korzystania z zestawu Windows ADK z programem Configuration Manager, zobacz [wymagania dotyczące wdrażania systemu operacyjnego w programie System Center Configuration Manager infrastruktury](../../../../osd/plan-design/infrastructure-requirements-for-operating-system-deployment.md).  

**Sprawdź stan lokacji i hierarchii, a następnie sprawdź, czy nie występują żadne nierozwiązane problemy:**  
Przed uaktualnieniem lokacji należy rozwiązać wszystkie problemy z działaniem serwera lokacji, serwera bazy danych lokacji i ról systemu lokacji zainstalowanych na komputerach zdalnych. Problemy z działaniem mogą spowodować niepowodzenie uaktualniania lokacji.  

**Zainstaluj wszystkie odpowiednie aktualizacje krytyczne systemów operacyjnych na komputerach hostujących lokację, serwer bazy danych lokacji i role zdalnego systemu lokacji:**  
Przed uaktualnieniem lokacji zainstaluj wszystkie aktualizacje krytyczne przeznaczone do odpowiednich systemów lokacji. Instalowana aktualizacja może wymagać ponownego uruchomienia odpowiednich komputerów przed rozpoczęciem aktualizacji dodatku Service Pack.  

Aby uzyskać więcej informacji, zobacz [usługi Windows Update](http://go.microsoft.com/fwlink/p/?LinkId=105851).  

**Odinstaluj ról systemu lokacji nie obsługiwane przez program System Center Configuration Manager:**  
Następujące role systemu lokacji nie są już używane w programie System Center Configuration Manager i musi zostać odinstalowane przed uaktualnieniem programu System Center 2012 Configuration Manager:  

-   Punkt zarządzania poza pasmem  
-   Punkt modułu sprawdzania kondycji usługi  

**Wyłącz repliki bazy danych dla punktów zarządzania w lokacjach głównych:**  
Menedżer konfiguracji nie może pomyślnie uaktualnić lokacji głównej, z repliką bazy danych dla punktów zarządzania włączone. Wyłącz replikację bazy danych przed:  

-   Utworzeniem kopii zapasowej bazy danych lokacji w celu przetestowania uaktualnienia bazy danych  
-   Uaktualnienie lokacji produkcyjnej programu System Center Configuration Manager  

Aby uzyskać więcej informacji, zobacz następujące tematy:  
-   System Center 2012 Configuration Manager:  [Konfigurowanie replik bazy danych dla punktów zarządzania](https://technet.microsoft.com/library/hh846234.aspx)  
-   System Center Configuration Manager: [Repliki bazy danych dla punktów zarządzania programu System Center Configuration Manager](../../../../core/servers/deploy/configure/database-replicas-for-management-points.md)  

**Skonfiguruj ponownie punkty aktualizacji oprogramowania, które korzystają z usługi równoważenia obciążenia sieciowego:**  
Menedżer konfiguracji nie można uaktualnić lokacji przy użyciu klastra równoważenia obciążenia sieciowego (NLB), punkty aktualizacji oprogramowania hosta.  

W przypadku używania klastrów równoważenia obciążenia sieciowego w punktach aktualizacji oprogramowania należy usunąć te klastry za pomocą programu PowerShell. (Nie w programie System Center 2012 Configuration Manager z dodatkiem SP1, było możliwości w konsoli programu Configuration Manager do skonfigurowania klastra równoważenia obciążenia Sieciowego)  

**Wyłącz wszystkie zadania obsługi lokacji w każdej lokacji w czasie trwania uaktualnienia tej lokacji:**  
Przed rozpoczęciem uaktualniania programu System Center Configuration Manager, należy wyłączyć wszystkie zadania obsługi, które mogą zostać uruchomione w czasie, gdy jest aktywny proces uaktualniania. Dotyczy to m.in. następujących zadań:  

-   Wykonaj kopię zapasową serwera lokacji  
-   Usuń przedawnione operacje klienta  
-   Usuń przedawnione dane odnajdywania  

Proces uaktualniania lokacji może zakończyć się niepowodzeniem, jeżeli w czasie jego trwania zostanie uruchomione zadanie obsługi bazy danych lokacji.  

Przed wyłączeniem zadania zarejestruj jego harmonogram, aby przywrócić jego konfigurację po ukończeniu uaktualniania lokacji.  

Więcej informacji o zadaniach obsługi lokacji znajduje się w temacie:  

-   System Center 2012 Configuration Manager:  [Planowanie zadań obsługi programu Configuration Manager](https://technet.microsoft.com/library/gg712686.aspx)  
-   System Center Configuration Manager:  [Informacje dotyczące zadań konserwacji programu System Center Configuration Manager](../../../../core/servers/manage/reference-for-maintenance-tasks.md)  

**Uruchom Narzędzie sprawdzania wymagań wstępnych Instalatora**:  
Aby sprawdzić, czy lokacja spełnia wymagania wstępne, przed uaktualnieniem lokacji można uruchomić **Narzędzie sprawdzania wymagań wstępnych** niezależnie od Instalatora. Później podczas uaktualniania lokacji narzędzie sprawdzania wymagań wstępnych zostanie ponownie uruchomione.  

Jeśli używasz nośnika linii bazowej 1606 wersji z października 2016 wersji niezależnych Sprawdzanie wymagań wstępnych oblicza lokacji w celu uaktualnienia do bieżącej gałęzi i długoterminowe obsługi gałęzi (LTSB) programu System Center Configuration zarządzania. Ponieważ niektóre funkcje nie są obsługiwane przez LTSB, można napotkać wpisów w *ConfigMgrPrereq.log* które są podobne do następującego:
 - INFORMACJE: Witryna jest wersja LTSB.
 - Nieobsługiwana Rola systemu lokacji "Punkt synchronizacji analizy zasobów" dla wersji LTSB;    Błąd;    Menedżer konfiguracji wykrył, że zainstalowano punkt synchronizacji analizy zasobów. Analiza zasobów nie jest obsługiwana w wersji LTSB. Rola systemu lokacji punktu synchronizacji analizy zasobów należy odinstalować przed kontynuowaniem.

Jeśli planowane jest uaktualnienie do bieżącej gałęzi, błędy dla wersji LTSB można bezpiecznie zignorować. Mają one zastosowanie tylko wtedy, jeśli planowane jest uaktualnienie do LTSB.

Później po uruchomieniu Instalatora programu Configuration Manager, aby wykonać uaktualnienie, sprawdzanie wymagań wstępnych uruchomi się ponownie i ocenić witryny utworzonej w oddziale firmy programu System Center Configuration Manager zostanie zainstalowana (bieżącej gałęzi lub LTSB). Jeśli wybierzesz uaktualnienie do bieżącej gałęzi, wyboru dla funkcji, które nie są obsługiwane przez LTSB nie są uruchamiane.

Aby uzyskać więcej informacji, zobacz [narzędzie sprawdzania wymagań wstępnych](/sccm/core/servers/deploy/install/prerequisite-checker) i [listy z wymagań wstępnych sprawdza, czy dla programu System Center Configuration Manager](/sccm/core/servers/deploy/install/list-of-prerequisite-checks).  

**Pobierz pliki wymagań wstępnych oraz pliki redystrybucyjne programu System Center Configuration Manager:**    
Użyj **Narzędzie pobierania Instalatora** pobrać wymagane wstępnie pliki, pakiety językowe i najnowsze aktualizacje produktu System Center Configuration Manager.  

Aby uzyskać informacje, zobacz [Narzędzie pobierania Instalatora](/sccm/core/servers/deploy/install/setup-downloader).  

**Zaplanuj zarządzanie językami klienta i serwera**:  
W przypadku uaktualnienia lokacji uaktualnienie powoduje tylko zainstalowanie wersji pakietów językowych wybranych podczas uaktualniania.  

-   Instalator sprawdza bieżącą konfigurację języka w lokacji, a następnie identyfikuje pakiety językowe dostępne w folderze z zapisanymi wcześniej pobranymi plikami wymagań wstępnych.  
-   Następnie można potwierdzić wybór bieżących pakietów językowych klienta i serwera lub zmienić wybrane opcje w celu dodania albo usunięcia obsługi danych języków.  
-   Można wybrać tylko te pakiety językowe, które są dostępne po uruchomieniu Instalatora (uzyskane razem z pobranymi plikami wymaganymi).  

> [!NOTE]  
>  Pakiety językowe programu System Center 2012 Configuration Manager nie można użyć do włączenia obsługi języków w witrynie System Center Configuration Manager.  

Aby uzyskać więcej informacji o pakietach językowych, zobacz [pakietów językowych w programie System Center Configuration Manager](../../../../core/servers/deploy/install/language-packs.md).  

**Zapoznaj się z uwagami dotyczącymi uaktualniania lokacji**:  
Podczas uaktualniania lokacji programu w niektórych funkcjach i konfiguracjach jest przywracana konfiguracja domyślna. Aby ułatwić przygotowanie tych i powiązanych zmian, zapoznaj się z informacjami w temacie  [Zagadnienia dotyczące uaktualniania](#bkmk_considerations).  

**Utwórz kopię zapasową bazy danych lokacji w centralnej lokacji administracyjnej oraz lokacjach głównych:**  
Przed uaktualnieniem lokacji utwórz kopię zapasową bazy danych lokacji, której będzie można użyć do odzyskiwania awaryjnego.  

Zobacz [kopii zapasowych i odzyskiwania dla programu System Center Configuration Manager](../../../../protect/understand/backup-and-recovery.md).  

**Wykonaj kopię zapasową dostosowanego pliku Configuration.mof**:  
Jeśli dostosowany plik Configuration.mof jest używany do definiowania klas danych używanych w spisie sprzętu, utwórz kopię zapasową tego pliku przed uaktualnieniem lokacji. Następnie po uaktualnieniu odtwórz ten plik w lokacji. Aby uzyskać więcej informacji o korzystaniu z tego pliku, zobacz [sposobach rozszerzania zapasów sprzętu w programie System Center Configuration Manager](../../../../core/clients/manage/inventory/extend-hardware-inventory.md).  

**Testowanie procesu uaktualniania bazy danych na kopię najnowszej kopii zapasowej bazy danych lokacji:**  
Przetestuj proces uaktualnienia bazy danych za pomocą najnowszej kopii zapasowej bazy danych lokacji przed uaktualnieniem centralnej lokacji administracyjnej programu lub lokacji głównej programu Configuration Manager.  

-   Należy przetestować proces uaktualniania bazy danych lokacji, ponieważ uaktualnienie lokacji może spowodować modyfikację bazy danych  
-   Test uaktualnienia bazy danych nie jest wymagany, ale pozwala wykryć problemy z uaktualnieniem przed wdrożeniem w produkcyjnej bazie danych  
-   Nieudane uaktualnienie bazy danych lokacji może uniemożliwić korzystanie z bazy danych lokacji i może wymagać przeprowadzenia odzyskiwania lokacji w celu przywrócenia jej funkcjonalności  
-   Choć baza danych lokacji jest udostępniana między lokacjami hierarchii, warto zaplanować testowanie bazy danych oddzielnie w każdej uaktualnianej lokacji  
-   W przypadku używania replik bazy danych dla punktów zarządzania w lokacji głównej przed utworzeniem kopii zapasowej bazy danych lokacji należy wyłączyć replikację  

Menedżer konfiguracji nie obsługuje kopii zapasowych lokacji dodatkowych ani testowego uaktualniania bazy danych lokacji dodatkowej.  

Wykonanie testowego uaktualnienia bazy danych na produkcyjnych bazach danych lokacji nie jest obsługiwane. Wykonanie tej czynności powoduje uaktualnienie bazy danych lokacji, przez co lokacja może przestać działać.  

Aby uzyskać więcej informacji, zobacz [Test uaktualnienia bazy danych lokacji](#bkmk_test).  

**Uruchom ponownie serwer lokacji i każdy komputer, który jest hostem roli systemu lokacji**:  
Odbywa się to, aby upewnić się, że żadnych oczekujących działania z ostatnio instalowane aktualizacje lub realizowane wymagania wstępne i jest proces wewnętrzny specyficzny dla firmy.  

**Uaktualnianie lokacji**:  
Począwszy od lokacji najwyższego poziomu w hierarchii, uruchom Setup.exe z nośnika źródłowego programu System Center Configuration Manager.  

Po ukończeniu uaktualniania lokacji najwyższego poziomu możesz przystąpić do uaktualniania poszczególnych lokacji podrzędnych. Uaktualnienia poszczególnych lokacji należy wykonywać po kolei i nie realizować ich równolegle  

Do momentu uaktualnienia wszystkich lokacji w hierarchii programu System Center Configuration Manager, hierarchia działa w trybie mieszanej wersji.  

Aby uzyskać informacje dotyczące uaktualnienia, zobacz [uaktualnić Lokacje](#bkmk_upgrade).  

### <a name="after-you-upgrade"></a>Po uaktualnieniu  
**Uaktualnić autonomiczne konsole programu Configuration Manager**:  
Domyślnie podczas uaktualniania centralnej lokacji administracyjnej lub lokacji głównej program instalacyjny uaktualnia także konsolę programu Configuration Manager, który jest zainstalowany na serwerze lokacji. Jednak każdą konsolę zainstalowaną na komputerze innym niż serwer lokacji należy uaktualnić ręcznie.  

> [!TIP]  
>  Przed rozpoczęciem uaktualniania zamknij otwarte konsole.  

Aby uzyskać więcej informacji, zobacz [Instalowanie konsol programu System Center Configuration Manager](../../../../core/servers/deploy/install/install-consoles.md).  

**Skonfiguruj ponownie repliki bazy danych dla punktów zarządzania w lokacjach głównych:**  
W przypadku używania replik bazy danych dla punktów zarządzania w lokacjach głównych należy odinstalować te repliki przed uaktualnieniem lokacji. Po uaktualnieniu lokacji głównej skonfiguruj ponownie repliki bazy danych dla punktów zarządzania.   
Aby uzyskać więcej informacji, zobacz [Repliki bazy danych dla punktów zarządzania programu System Center Configuration Manager](../../../../core/servers/deploy/configure/database-replicas-for-management-points.md).  

**Skonfiguruj ponownie wszystkie wyłączone przed uaktualnieniem zadania konserwacji bazy danych:**  
Jeśli przed uaktualnieniem w lokacji wyłączono zadania obsługi bazy danych ([Informacje o zadaniach konserwacji programu System Center Configuration Manager](../../../../core/servers/manage/reference-for-maintenance-tasks.md)), skonfiguruj je ponownie w lokacji przy użyciu ustawień stosowanych wcześniej przed uaktualnieniem.  

**Uaktualnij klientów**:  
Wszystkie lokacje uaktualnienia programu System Center Configuration Manager, Zaplanuj uaktualnienie klientów.  

Podczas uaktualniania bieżące oprogramowanie klienta zostaje odinstalowane i zastąpione nową wersją oprogramowania. Aby uaktualnić klientów, można zastosować dowolną metodę obsługiwaną przez program Configuration Manager.  

> [!TIP]  
>  W przypadku uaktualniania lokacji najwyższego poziomu w hierarchii zostaje również zaktualizowany pakiet instalacyjny klienta w każdym punkcie dystrybucji w hierarchii. W ramach uaktualniania lokacji głównej zostaje zaktualizowany pakiet uaktualniający klienta dostępny w tej lokacji głównej.  

Aby uzyskać więcej informacji o sposobie uaktualniania istniejących klientów i instalowaniu nowych klientów, zobacz [Uaktualnianie klientów komputerów z systemem Windows w programie System Center Configuration Manager](../../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md).  

##  <a name="bkmk_considerations"></a> Zagadnienia dotyczące uaktualniania  
**Działania automatyczne**:  
Po uaktualnieniu programu System Center Configuration Manager, automatycznie wykonywane następujące działania:  

-   Lokacja samodzielnie się resetuje, jednocześnie instalując ponownie wszystkie role systemu lokacji.  
-   Lokacja najwyższego poziomu w hierarchii aktualizuje pakiet instalacyjny klienta w każdym punkcie dystrybucji w hierarchii. Lokacja aktualizuje także domyślne obrazy rozruchowe tak, aby była w nich używana nowa wersja systemu Windows PE dołączona do Zestawu do oceny i wdrażania systemu Windows 10. Jednak proces uaktualniania nie uaktualnia istniejących nośników służących do wdrażania obrazów.  
-   Lokacja główna aktualizuje pakiet uaktualniający klienta dla tej lokacji.  

**Ręczne działania wykonywane przez użytkownika administracyjnego po uaktualnieniu**   
Po uaktualnieniu lokacji należy upewnić się, że są wykonywane następujące czynności:  

-   Sprawdź, czy w przypadku klientów przypisanych do poszczególnych lokacji głównych zostało wykonane uaktualnienie i zainstaluj oprogramowanie klienta z nową wersją  
-   Uaktualnienia poszczególnych konsoli programu Configuration Manager nawiązujący połączenie z lokacją i uruchomione na komputerze sterowanym zdalnie z serwera lokacji  
-   W lokacjach głównych, w których są używane repliki bazy danych dla punktów zarządzania, skonfiguruj ponownie repliki bazy danych  
-   Po uaktualnieniu lokacji należy ręcznie uaktualnić nośniki fizyczne, takie jak pliki ISO dysków CD lub DVD, dyski flash USB lub wcześniej przygotowane nośniki używane do wdrożeń funkcji Windows To Go lub udostępniane dostawcom sprzętu. Chociaż proces uaktualniania lokacji aktualizuje domyślne obrazy rozruchowe nie może uaktualnić plików nośników lub używanych urządzeń zewnętrznych do programu Configuration Manager  
-   Aktualizowanie obrazów rozruchowych innych niż domyślne należy zaplanować, gdy oryginalne (starsze) wersje systemu Windows PE nie są potrzebne.  

**Działania wpływające na konfiguracje i ustawienia**   
Podczas uaktualniania lokacji programu System Center Configuration Manager, niektóre konfiguracje i ustawienia mogą zmienić się po uaktualnieniu lub są ustawione na nową konfigurację domyślną. Poniższa tabela zawiera ustawienia, które nie są trwałe i mogą ulec zmianie, a także szczegółowe informacje ułatwiające zaplanowanie ich podczas uaktualniania lokacji:  

-   **Software Center:**  
    Następujące elementy programu Software Center są resetowane do wartości domyślnych:  
    -   Wardości w pozycji**Informacje o pracy** zostają zresedowane do godzin pracy od **5:00** do **22:00** Monday do Friday.  
    -   W pozycji **Konserwacja komputera** zostaje ustawiona wartość **Wstrzymaj działania programu Software Center, jeżeli mój komputer jest w trybie prezentacji**.  
    -   W pozycji **Zdalne sterowanie** zostaje ustawiona wartość ustawień klienta przypisanych do komputera.  
-   **Harmonogramy podsumowania aktualizacji oprogramowania:**  
     Niestandardowe harmonogramy podsumowania aktualizacji oprogramowania lub grup aktualizacji oprogramowania zostają zresetowane do wartości domyślnej równej 1 godz. Po zakończeniu uaktualniania należy zresetować niestandardowe wartości podsumowania do wymaganej częstotliwości.  

##  <a name="bkmk_test"></a> Testowanie uaktualnienia bazy danych lokacji  
Poniższe informacje dotyczą tylko wtedy, gdy uaktualniasz wcześniejsze versoin, takich jak System Center 2012 Configuration Manager programu System Center Configuration Manager. Jeśli witryna już działa System Center Configuration Manager i instalowania nowych aktualizacji, zobacz [krok 2: Test uaktualnienia bazy danych przed zainstalowaniem aktualizacji](/sccm/core/servers/manage/install-in-console-updates#bkmk_step2) z **przed zainstalowaniem aktualizacji w konsoli**.

Przed uaktualnieniem lokacji należy przetestować kopię bazy danych tej lokacji do uaktualnienia.  

Aby przetestować bazę danych do uaktualnienia, należy najpierw przywrócić kopię bazy danych lokacji do wystąpienia programu SQL Server, który nie jest hostem lokacji programu Configuration Manager. Wersja programu SQL Server używanego do przechowywania kopii bazy danych musi być wersji programu SQL Server, czy wersja programu Configuration Manager obsługuje oznacza to kopia bazy danych.  

Następnie po przywróceniu bazy danych lokacji na komputerze programu SQL Server uruchom Instalatora programu Configuration Manager z folderu nośnika źródłowego programu System Center Configuration Manager z **/testdbupgrade** opcji wiersza polecenia.  

-   Informacje o sposobie tworzenia i przywracania kopii zapasowej bazy danych lokacji znajdują się w temacie [Opcje wiersza polecenia dla Instalatora](../../../../core/servers/deploy/install/command-line-options-for-setup.md).  
-   Informacje o używaniu opcji wiersza polecenia **/TESTDBUPGRADE** znajdują się w tabeli w temacie [Opcje wiersza polecenia dla Instalatora](../../../../core/servers/deploy/install/command-line-options-for-setup.md).  
-   Informacje o obsługiwanych wersjach programu SQL Server można znaleźć w temacie [Obsługiwane konfiguracje programu SQL Server dla programu System Center Configuration Manager](../../../../core/plan-design/configs/support-for-sql-server-versions.md).  

> [!TIP]  
>  Po zintegrowaniu programu Microsoft Intune z programem Configuration Manager:  
>   
>  Po uruchomieniu testu uaktualnienia bazy danych na kopii bazy danych lokacji utworzonej 5 dni temu lub wcześniej może zostać wyświetlony jeden z następujących komunikatów:  
>   
>  -   OSTRZEŻENIE: Uaktualnienie wymusi pełną synchronizację, aby w chmurze.  
>  -   BŁĄD: Uaktualnienie bazy danych wymusi pełną synchronizację, aby w chmurze.  
>   
> Jednocześnie można bezpiecznie zignorować podczas testowania uaktualnienia bazy danych, jak wskazuje błąd lub problem z testu uaktualnienia. Zamiast tego one wskazują, że podczas uaktualniania rzeczywistych danych z **chmury** grupy replikacji bazy danych może synchronizować w usłudze Microsoft Intune.  

W każdej centralnej lokacji administracyjnej i lokacji głównej, która ma zostać uaktualniona, wykonaj następującą procedurę.  

#### <a name="to-test-a-site-database-for-upgrade"></a>Aby przetestować bazę danych lokacji dla uaktualnienia  

1.  Utwórz kopię bazy danych lokacji, a następnie przywróć ją z wystąpieniem programu SQL Server, który używa tej samej wersji co w bazie danych lokacji i nie jest hostem lokacji programu Configuration Manager. Przykładowo kopia bazy danych lokacji uruchomionej w wystąpieniu programu SQL Server w wersji Enterprise musi być przywrócona w innym wystąpieniu programu SQL Server w wersji Enterprise.  

2.  Po przywróceniu kopii bazy danych, uruchom Instalatora z nośnika źródłowego programu System Center Configuration Manager. Podczas uruchamiania Instalatora użyj opcji wiersza polecenia **/TESTDBUPGRADE** . Jeśli wystąpienie programu SQL Server, które hostuje kopię bazy danych, nie jest wystąpieniem domyślnym, musisz także podać argumenty wiersza polecenia identyfikujące wystąpienie hostujące kopię bazy danych lokacji.  

     Przykładowo chcesz przeprowadzić uaktualnienie bazy danych lokacji z nazwą bazy danych SMS_ABC. Wykonano przywrócenie kopii bazy danych lokacji na obsługiwane wystąpienie serwera SQL Server o nazwie DBTest. Aby przetestować uaktualnienie kopii bazy danych lokacji, należy użyć następującego polecenia: **Setup.exe/testdbupgrade DBtest\CM_ABC**  

     Setup.exe można znaleźć w następującej lokalizacji na nośniku źródłowym programu System Center Configuration Manager: **SMSSETUP\BIN\X64**.  

3.  Na komputerze z wystąpieniem programu SQL Server realizującym test uaktualnienia bazy danych otwórz zapisany w głównym folderze dysku plik ConfigMgrSetup.log i sprawdź zapisywane w nim informacje:  

    -   Jeśli testowe uaktualnienie nie powiedzie się, usuń problemy związane z awarią uaktualnienia bazy danych lokacji, utwórz nową kopię zapasową bazy danych lokacji i przetestuj uaktualnienie nowej kopii bazy danych lokacji.  
    -   Gdy proces powiedzie się, możesz usunąć kopię bazy danych lokacji.  

        > [!NOTE]  
        >  Przywracanie kopii bazy danych lokacji użytej do testu uaktualnienia jako bazy danych dowolnej lokacji nie jest obsługiwane.  

Po pomyślnym uaktualnieniu kopii bazy danych lokacji, należy kontynuować proces uaktualniania lokacji programu Configuration Manager i jego bazy danych lokacji.  

##  <a name="bkmk_upgrade"></a> Uaktualnianie lokacji  
Po zakończeniu konfiguracji sprzed uaktualnienia lokacji należy sprawdzić uaktualnienie bazy danych lokacji na kopii bazy danych i pobrać wymagane pliki oraz pakiety językowe dla wersji dodatku service pack, który ma zostać zainstalowany można przystąpić do uaktualniania lokacji programu Configuration Manager.  

Uaktualniając lokację umieszczoną w hierarchii, należy najpierw uaktualnić lokację najwyższego poziomu. Lokacja najwyższego to centralna lokacja administracyjna lub autonomiczna lokacja główna. Po zakończeniu uaktualniania centralnej lokacji administracyjnej można uaktualnić w dowolnej kolejności podrzędne lokacje główne. Po uaktualnieniu lokacji głównej można uaktualnić tej lokacji podrzędnych lokacji dodatkowych lub Uaktualnij dodatkowe Lokacje główne, przed uaktualnieniem lokacji dodatkowych.  

Aby uaktualnić centralnej lokacji administracyjnej lub lokacji głównej, należy uruchomić Instalatora z nośnika źródłowego programu System Center Configuration Manager. Nie należy tego robić w celu uaktualnienia lokacji dodatkowych. Zamiast tego należy użyć konsoli programu Configuration Manager uaktualnienia lokacji dodatkowej, po zakończeniu uaktualnienia nadrzędnej lokacji głównej.  

Przed uaktualnieniem lokacji zamknij konsolę programu Configuration Manager, który jest zainstalowany na serwerze lokacji, aż do zakończenia uaktualnienia lokacji. Ponadto Zamknij każdego konsoli programu Configuration Manager, które jest uruchamiane na komputerach innych niż serwer lokacji. Ponowne nawiązanie połączenia z konsolą będzie możliwe po zakończeniu uaktualnienia lokacji. Jednakże aż do konsoli programu Configuration Manager jest uaktualniany do nowej wersji programu Configuration Manager, konsoli nie można wyświetlić niektórych obiektów i informacji dostępnych w nowej wersji programu Configuration Manager.  

Użyj poniższych procedur, aby uaktualnić lokacji programu Configuration Manager:  

#### <a name="to-upgrade-a-central-administration-site-or-primary-site"></a>Aby uaktualnić centralną lokację administracyjną lub lokację główną  

1.  Sprawdź, czy użytkownik, który uruchamia instalatora, ma następujące prawa zabezpieczeń:  

    -   Uprawnienia administratora lokalnego na komputerze serwera lokacji.  
    -   Uprawnienia administratora lokalnego na zdalnym serwerze bazy danych lokacji (jeśli jest zdalna).    </br></br>

2.  Na komputerze serwera lokacji, otwórz Eksploratora Windows i przejdź do  **&lt;ConfigMgSourceMedia\>\SMSSETUP\BIN\X64**.  

3.  Kliknij dwukrotnie plik **Setup.exe**. Zostanie otwarty Kreator instalacji programu Configuration Manager.  

4.  Na stronie **Zanim rozpoczniesz** kliknij przycisk **Dalej**.  

5.  Na stronie **Wprowadzenie** wybierz polecenie **Uaktualnij tę lokację programu Configuration Manager**i kliknij przycisk **Dalej**.  

6.  Na stronie **Klucz produktu** kliknij przycisk **Dalej**.  

     Jeśli wcześniej zainstalowano ewaluacyjna programu Configuration Manager, możesz wybrać **Instaluj licencjonowaną wersję tego produktu**, a następnie wprowadź klucz produktu do pełnej instalacji programu Configuration Manager skonwertuje wówczas lokację do wersji pełnej.  

     Począwszy od wersji 2016 października nośników linii bazowej 1606 wersji programu System Center Configuration Manager, można określić datę wygaśnięcia umowy Software Assurance. Istnieje również możliwość określenia **Data wygaśnięcia Software Assurance** umowy licencyjnej jako wygodny monitu dla Ciebie od tej daty. Jeśli nie podasz to podczas instalacji, można określić ją później za pomocą w konsoli programu Configuration Manager.

     >  [!NOTE]   
     >  Firma Microsoft nie obsługuje sprawdzania Data wygaśnięcia wpisana i nie używa tej daty w celu weryfikacji licencji.  W takim przypadku go użyć jako przypomnienie od daty wygaśnięcia. Jest to przydatne, ponieważ program Configuration Manager okresowo sprawdza, czy nowe aktualizacje oprogramowania oferowanych online i Twojego stanu licencji na oprogramowanie assurance powinna być bieżącym Aby kwalifikować się do korzystania z tych dodatkowych aktualizacji.    

     Aby uzyskać więcej informacji, zobacz [licencjonowania i gałęzie dla programu System Center Configuration Manager](/sccm/core/understand/learn-more-editions).

7.  Na stronie **Postanowienia licencyjne dotyczące oprogramowania firmy Microsoft** przeczytaj i zaakceptuj postanowienia licencyjne, a następnie kliknij przycisk **Dalej**.  

8.  Na stronie **Licencje wymagań wstępnych** przeczytaj i zaakceptuj postanowienia licencyjne wstępnie wymaganego oprogramowania, a następnie kliknij przycisk **Dalej**. Instalator pobiera i automatycznie instaluje oprogramowanie w systemach lokacji lub na klientach, gdy jest to wymagane. Przed kontynuowaniem do następnej strony należy zaznaczyć wszystkie pola wyboru.  

9. Na stronie **Pobieranie plików wymaganych wstępnie** określ, czy instalator ma pobrać najnowsze wymagane wstępnie pliki, pakiety językowe i aktualizacje produktów z Internetu, czy mają być użyte poprzednio pobrane pliki, i kliknij przycisk **Dalej**. Jeżeli pliki zostały wcześniej pobrane przy użyciu Narzędzia pobierania Instalatora, wybierz opcję **Użyj wcześniej pobranych plików** i określ folder pobierania. Aby uzyskać więcej informacji, zobacz [Narzędzie pobierania Instalatora](/sccm/core/servers/deploy/install/setup-downloader).

    > [!NOTE]  
    >  W przypadku używania wcześniej pobranych plików sprawdź, czy ścieżka do folderu pobierania zawiera najnowszą wersję plików.  

10. Na stronie **Wybór języka serwera** wyświetl listę języków zainstalowanych obecnie w tej lokacji. Wybierz dodatkowe języki, które są dostępne w tej lokacji dla konsoli programu Configuration Manager i raporty, lub wyczyść języki, które nie są już potrzebne w tej lokacji, a następnie kliknij przycisk **dalej**. Język angielski jest wybrany domyślnie i nie można go usunąć.  

    > [!IMPORTANT]  
    >  Każda wersja programu Configuration Manager nie można używać pakietów językowych z poprzednich wersji programu Configuration Manager. Aby włączyć obsługę języka w lokacji programu Configuration Manager, który można uaktualnić, należy użyć wersji pakietu językowego dla nowej wersji. Na przykład podczas uaktualniania programu System Center 2012 Configuration Manager programu System Center Configuration Manager, jeśli nie jest dostępna z plikami wymagań wstępnych, które możesz pobrać wersja programu System Center Configuration Manager pakietu językowego obsługę danego języka nie zostanie zainstalowane.  

11. Na stronie **Wybór języka klienta** wyświetl listę języków zainstalowanych obecnie w tej lokacji. Wybierz dodatkowe języki, które mają być dostępne w tej lokacji dla klientów, oraz usuń języki, które nie są już potrzebne w tej lokacji. Określ, czy w klientach urządzeń przenośnych mają zostać włączone wszystkie języki klienckie, i kliknij przycisk **Dalej**. Język angielski jest wybrany domyślnie i nie można go usunąć.  

    > [!IMPORTANT]  
    >  Każda wersja programu Configuration Manager nie można używać pakietów językowych z poprzednich wersji programu Configuration Manager. Aby włączyć obsługę języka w lokacji programu Configuration Manager, który można uaktualnić, należy użyć wersji pakietu językowego dla nowej wersji. Na przykład podczas uaktualniania programu System Center 2012 Configuration Manager programu System Center Configuration Manager, jeśli nie jest dostępna z plikami wymagań wstępnych, które możesz pobrać wersja programu System Center Configuration Manager pakietu językowego obsługę danego języka nie zostanie zainstalowane.  

12. Na stronie **Podsumowanie ustawień** kliknij przycisk **Dalej** . Zostanie uruchomione Narzędzie sprawdzania wymagań wstępnych, które potwierdzi gotowość serwera do uaktualnienia danej lokacji.  

13. Jeśli na stronie **Sprawdzenie instalacji wymagań wstępnych** nie zostały podane żadne problemy, kliknij przycisk **Dalej** , aby uaktualnić lokację i role systemu lokacji. Gdy Narzędzie sprawdzania wymagań wstępnych wykryje problem, kliknij element na liście w celu uzyskania szczegółów dotyczących sposobu rozwiązania problemu. Przed kontynuowaniem instalacji usuń przyczyny wszystkich pozycji o statusie **Błąd** . Po rozwiązaniu problemu kliknij przycisk **Uruchom sprawdzenie** , aby ponownie uruchomić sprawdzenie wymagań wstępnych. Aby przejrzeć wyniki zwrócone przez Narzędzie sprawdzania wymagań wstępnych, możesz również otworzyć plik ConfigMgrPrereq.log w katalogu głównym dysku systemowego. Plik dziennika może zawierać dodatkowe informacje, które nie są wyświetlane w interfejsie użytkownika. Lista reguł wymagań wstępnych instalacji oraz opisy, zobacz [narzędzie sprawdzania wymagań wstępnych](/sccm/core/servers/deploy/install/list-of-prerequisite-checks).  

Na stronie **Uaktualnienie** instalator wyświetli ogólny postęp całej procedury. Gdy Instalator ukończy instalację podstawowego serwera lokacji i systemu lokacji, możesz zamknąć kreatora. Konfiguracja lokacji odbywa się w tle.  

#### <a name="to-upgrade-a-secondary-site"></a>Aby uaktualnić lokację dodatkową  

1.  Sprawdź, czy użytkownik administracyjny uruchamiający Instalatora ma następujące prawa zabezpieczeń:  

    -   Uprawnienia administratora lokalnego na komputerze serwera lokacji dodatkowej  
    -   Administrator infrastruktury lub administrator o pełnych uprawnieniach w głównym elemencie nadrzędnym  
    -   Uprawnienia administratora systemu w bazie danych lokacji dodatkowej  
    </br>
2.  W konsoli programu Configuration Manager kliknij przycisk **Administracja**.  

3.  W obszarze roboczym **Administracja** rozwiń węzeł **Konfiguracja lokacji**, a następnie kliknij przycisk **Lokacje**.  

4.  Wybierz lokację dodatkową do uaktualnienia, a następnie na karcie **Narzędzia główne** w grupie **Lokacja** kliknij przycisk **Uaktualnij**.  

5.  Potwierdź decyzję, klikając przycisk **Tak** , i rozpocznij uaktualnienie lokacji dodatkowej.  

Uaktualnienie lokacji dodatkowej będzie realizowane w tle. Po zakończeniu uaktualniania można potwierdzić stan w konsoli programu Configuration Manager. Aby potwierdzić stan konsoli, wybierz serwer lokacji dodatkowej, a następnie na karcie **Narzędzia główne** w grupie **Lokacja** kliknij przycisk **Pokaż stan instalacji**.  

##  <a name="BKMK_PostUpgrade"></a> Wykonywanie zadań po uaktualnieniu  
Po uaktualnieniu lokacji do nowego dodatku Service Pack może być konieczne wykonanie dodatkowych zadań konfiguracyjnych wymaganych do skończenia uaktualnienia lub zmiany konfiguracji lokacji. Może to obejmować uaktualnienie klientów programu Configuration Manager lub konsoli programu Configuration Manager, ponowne włączenie replik baz danych dla punktów zarządzania i przywrócenie ustawień programu Configuration Manager funkcje, które można używać i które nie zostanie uwzględniona dodatku service pack.  

**Znane problemy dotyczące lokacji dodatkowych:**  
- **Podczas uaktualniania do wersji 1511:** Upewnij się, klienci w lokacjach dodatkowych można znaleźć punktu zarządzania z lokacji dodatkowej (punkt zarządzania proxy), ręcznie dodać punkt zarządzania do grupy granic, które również zawierać punkty dystrybucji w lokacji dodatkowej.  

- **Podczas uaktualniania do wersji 1606 lub nowszej:** Punkty zarządzania serwera proxy są automatycznie dodawane do grupy granic, które zawierają punkty dystrybucji w lokacji dodatkowej.

