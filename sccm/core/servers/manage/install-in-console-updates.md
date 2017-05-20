---
title: Aktualizacje konsoli | Dokumentacja firmy Microsoft
description: "Synchronizuje System Center Configuration Manager z chmurowych firmy Microsoft, aby pobrać aktualizacje, które można zainstalować w konsoli."
ms.custom: na
ms.date: 4/7/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c14a3607-253b-41fb-8381-ae2d534a9022
caps.latest.revision: 36
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.translationtype: Machine Translation
ms.sourcegitcommit: d94acac84f052a01de9d9c9f65f237c0006c45b8
ms.openlocfilehash: 29a55948a1897e1345ba14ec685b9288a844feaa
ms.contentlocale: pl-pl
ms.lasthandoff: 05/17/2017


---
# <a name="install-in-console-updates-for-system-center-configuration-manager"></a>Instalacja aktualizacji w konsoli programu System Center Configuration Manager

*Dotyczy: System Center Configuration Manager (bieżącej gałęzi)*

System Center Configuration Manager synchronizuje się z usługą w chmurze firmy Microsoft do pobierania aktualizacji. Następnie można zainstalować tych aktualizacji z poziomu konsoli programu Configuration Manager.

## <a name="get-available-updates"></a>Uzyskiwanie dostępnych aktualizacji
Pobierane i udostępniane hierarchii użytkownika są tylko aktualizacje mające zastosowanie do danej infrastruktury i wersji. Synchronizacja może być automatycznie lub ręcznie, w zależności od tego, jak skonfigurować punkt połączenia usługi dla hierarchii:

-   W **trybie online**punkt połączenia usługi automatycznie łączy się z usługą firmy Microsoft w chmurze i pobiera odpowiednie aktualizacje.  

     Domyślnie Configuration Manager sprawdza dostępność nowych aktualizacji co 24 godziny. Możesz również sprawdzić aktualizacje natychmiast, wybierając **Wyszukaj aktualizacje** w **Administracja** > **aktualizacji i obsługi** węzeł konsoli programu Configuration Manager. (Przed wersją 1702 ten węzeł był w obszarze **Administracja** > **usług w chmurze**.)

-   W **trybu offline**, punkt połączenia usługi nie łączy się usługa w chmurze firmy Microsoft. Należy ręcznie [użyć narzędzia połączenia usługi System Center Configuration Manager](../../../core/servers/manage/use-the-service-connection-tool.md) do pobrania, a następnie zaimportować dostępne aktualizacje.  

> [!NOTE]  
>  Oprócz aktualizacji, które pojawia się po synchronizacji z usługą w chmurze firmy Microsoft, poza pasmem poprawek zainstalowanych przy użyciu [narzędzie rejestracji aktualizacji](http://technet.microsoft.com/library/mt691544.aspx) również są importowane do konsoli gdzie następnie wybierz je, aby zainstalować.  

Po zsynchronizowaniu aktualizacji można je przeglądać w konsoli programu Configuration Manager przechodząc do **Administracja** > **aktualizacji i obsługi** węzła:  

-   Aktualizacje niezainstalowane są wyświetlane jako **Dostępne**.

-   Aktualizacje zainstalowane są wyświetlane jako **Zainstalowane**.  Jest wyświetlana tylko ostatnią zainstalowaną aktualizację. Można wybrać **historii** przycisk na Wstążce, aby wyświetlić wcześniej zainstalowane aktualizacje.



Przed skonfigurowaniem punktu połączenia usługi i planowaniu dla jego dodatkowych zastosowań. Następujące zastosowania mogą mieć wpływ na sposób konfigurowania roli systemu lokacji:  

-   Punkt połączenia z usługą służy do przekazywania informacji o użyciu lokacji. Informacje te pomagają usłudze firmy Microsoft w chmurze zidentyfikować aktualizacje dostępne dla bieżącej wersji infrastruktury. Aby uzyskać więcej informacji, zobacz [diagnostyki i danych użycia programu System Center Configuration Manager](../../../core/plan-design/diagnostics/diagnostics-and-usage-data.md).  

-   Punkt połączenia usługi jest używana do zarządzania urządzeniami z Microsoft Intune i przy użyciu programu Configuration Manager zarządzanie urządzeniami przenośnymi lokalnie. Aby uzyskać więcej informacji, zobacz [hybrydowego zarządzania urządzeniami przenośnymi (MDM) za pomocą programu System Center Configuration Manager i Microsoft Intune](../../../mdm/understand/hybrid-mobile-device-management.md).  

Aby lepiej zrozumieć, co się dzieje, gdy aktualizacje są pobrane, zobacz:  

-   [Schemat blokowy — pobierania aktualizacji dla programu System Center Configuration Manager](../../../core/servers/manage/download-updates-flowchart.md)

-   [Schemat blokowy — replikacja aktualizacji dla programu System Center Configuration Manager](../../../core/servers/manage/update-replication-flowchart.md)  

## <a name="assign-permissions-to-view-and-manage-updates-and-features"></a>Przypisywanie uprawnień do wyświetlania i zarządzania nimi, aktualizacji i funkcji
Aby wyświetlić aktualizacje w konsoli, należy przypisać użytkownika roli zabezpieczeń administracji opartej na rolach, która zawiera klasę zabezpieczeń o nazwie **pakietów aktualizacji**. Ta klasa udziela dostępu do wyświetlania i zarządzania aktualizacjami w konsoli programu Configuration Manager.    

**Informacje o klasie Pakiety aktualizacji:**  
Domyślnie klasa **Pakiety aktualizacji** (SMS_CM_Updatepackages) jest częścią następujących wbudowanych ról zabezpieczeń z następującymi uprawnieniami:
 -  **Administrator o pełnych uprawnieniach** z uprawnieniami **Modyfikacja** i **Odczyt** :
    -   Użytkownik z tą rolą zabezpieczeń i dostępu do **wszystkie** zakres zabezpieczeń można wyświetlić aktualizacje, zainstaluj aktualizacje włączania funkcji podczas instalacji i włączyć poszczególnych funkcji, po zainstalowaniu aktualizacji.
    - Użytkownik z tą rolą zabezpieczeń i dostępu do **domyślne** zakres zabezpieczeń można wyświetlić aktualizacje, zainstaluj aktualizacje włączania funkcji podczas instalacji i wyświetlić funkcje po zainstalowaniu aktualizacji. Jednak ten użytkownik nie może włączyć funkcji, po zainstalowaniu aktualizacji.

- **Analityk z uprawnieniami tylko do odczytu** z uprawnieniami **Odczyt** :
  -  Użytkownik z tą rolą zabezpieczeń i dostępu do **domyślne** zakres można wyświetlić aktualizacje, ale nie je zainstalować. Ten użytkownik można również wyświetlić funkcji po aktualizacji została zainstalowana, ale nie można włączyć je.

**Uprawnienia wymagane do aktualizacji i obsługi:**   
  - Użyj konta, któremu przypisano rolę zabezpieczeń zawierającą klasę **Pakiety aktualizacji** z uprawnieniami **Modyfikacja** i **Odczyt** .
  - Konto musi być przypisane do zakresu **Domyślne** .

**Permissoins, aby wyświetlić tylko aktualizacje**:
  - Użyj konta, któremu przypisano rolę zabezpieczeń zawierającą klasę **Pakiety aktualizacji** tylko z uprawnieniem **Odczyt** .
  - Konto musi być przypisane do zakresu **Domyślne** .

**Uprawnienia wymagane do włączenia funkcji, po zainstalowaniu aktualizacji:**
  -  Użyj konta, któremu przypisano rolę zabezpieczeń zawierającą klasę **Pakiety aktualizacji** z uprawnieniami **Modyfikacja** i **Odczyt** .
  -  Konto musi być przypisane do zakresu **Wszystkie** .






##  <a name="bkmk_beforeinstall"></a> Przed zainstalowaniem aktualizacji w konsoli  
 Przed zainstalowaniem aktualizacji z konsoli programu Configuration Manager, należy sprawdzić następujące kroki.  

###  <a name="bkmk_step1"></a>Krok 1: Przejrzyj listę kontrolną aktualizacji  
Sprawdź listę kontrolną aktualizacji odpowiednie akcje, które należy wykonać przed rozpoczęciem aktualizacji:

- 1606 aktualizacji: Zobacz [Lista kontrolna instalowania aktualizacji 1606](../../../core/servers/manage/checklist-for-installing-update-1606.md).  

- Aktualizacji 1610 z albo 1606: Zobacz [Lista kontrolna instalowania aktualizacji 1610](../../../core/servers/manage/checklist-for-installing-update-1610.md).  

- Aktualizacji 1702 1606 lub 1610: Zobacz [Lista kontrolna instalowania aktualizacji 1702](../../../core/servers/manage/checklist-for-installing-update-1702.md).

###  <a name="bkmk_step2"></a>Krok 2: Test uaktualnienia bazy danych przed zainstalowaniem aktualizacji  
Informacje przedstawione w tym kroku dotyczy tylko jeśli instalujesz *aktualizacji* dla lokacji programu System Center Configuration Manager. Jeśli jesteś *uaktualnianie* System Center 2012 Configuration Manager lokacji programu System Center Configuration Manager, zobacz [Test uaktualnienia bazy danych lokacji](/sccm/core/servers/deploy/install/upgrade-to-configuration-manager#a-namebkmktesta-test-the-site-database-upgrade).

Przed zainstalowaniem nowej aktualizacji w hierarchii, jak zaktualizować 1610 można sprawdzić uaktualnienie bazy danych lokacji. Nazwa opcji wiersza polecenia, używanej do testowania, instalowania aktualizacji na kopię zapasową bazy danych lokacji jest **testdbupgrade**.  

Jeśli po zainstalowaniu aktualizacji nie powiedzie się, nie należy do odzyskiwania lokacji. Zamiast tego można ponowić próbę instalacji aktualizacji. Tak mimo że testowego uaktualnienia bazy danych jest mniejsze znaczenie niż w poprzednich wersjach produktu, takich jak System Center 2012 Configuration Manager, nadal zalecamy jej.


#### <a name="to-run-testdbupgrade-before-installing-an-update"></a>Aby uruchomić polecenie testdbupgrade przed instalacją aktualizacji  

1.  Pobierz zestaw plików źródłowych z **dysku CD. Najnowsze** folder lokacji z uruchomionym wersja ma być zaktualizowana do. Może to wymagać do instalacji pierwszej lokacji w laboratorium lub testowym działającą w tej wersji programu System Center Configuration Manager.  

     **Dysku CD. Najnowsze** folderu dla lokacji zawiera pliki źródłowe dla danej wersji. Należy użyć tych plików źródłowych do uruchomienia aktualizacji testowej bazy danych lokacji. Aby uzyskać więcej informacji, zobacz [The CD.Latest folder for System Center Configuration Manager](../../../core/servers/manage/the-cd.latest-folder.md) (Folder CD.Latest dla programu System Center Configuration Manager).  

     Na przykład, jeśli chcesz zaktualizować 1610 witryny uruchamiana wersja 1606, należy uzyskać dysk CD. Najnowszy folder z lokacji, która już została zaktualizowana do wersji 1610. Zazwyczaj można zainstalować nowe i tymczasowego witryny w laboratorium i która uaktualnienia do wersji 1610 do utworzenia dysku CD. Najnowszy folder zawierający wymagane pliki.  

2.  Kopiowanie dysku CD. Najnowszy folder w lokalizacji w wystąpieniu programu SQL Server, które będzie używane do uruchamiania testów uaktualniania bazy danych.

3.  Utwórz kopię zapasową bazy danych lokacji, który chcesz przetestować uaktualnienie, a następnie przywrócić kopię bazy danych do wystąpienia programu SQL Server, który nie jest hostem lokacji programu Configuration Manager. Wystąpienia programu SQL Server, należy użyć tej samej wersji programu SQL Server jako bazy danych lokacji.  

4.  Po przywróceniu kopii bazy danych uruchom **instalacji** z dysku CD. Najnowszy folder skopiowany w środowisku laboratoryjnym lub testu. Podczas uruchamiania Instalatora użyj opcji wiersza polecenia **/TESTDBUPGRADE** . Jeśli wystąpienie programu SQL Server, które hostuje kopię bazy danych, nie jest wystąpieniem domyślnym, musisz także podać argumenty wiersza polecenia identyfikujące wystąpienie hostujące kopię bazy danych lokacji.  

     Na przykład załóżmy, że planowane jest uaktualnienie bazy danych lokacji z nazwą bazy danych SMS_ABC. Wykonano przywrócenie kopii bazy danych lokacji na obsługiwane wystąpienie serwera SQL Server o nazwie DBTest. Aby przetestować uaktualnienie kopii bazy danych lokacji, należy użyć następującego polecenia: **Setup.exe/testdbupgrade DBtest\CM_ABC**  

     Setup.exe można znaleźć w następującej lokalizacji na nośniku źródłowym programu System Center Configuration Manager: **SMSSETUP\BIN\X64**.  

5.  Na komputerze z wystąpieniem serwera SQL Server realizującym uaktualnienie testowe bazy danych otwórz zapisany w głównym folderze dysku plik ConfigMgrSetup.log i sprawdź zapisywane w nim informacje.  

     Jeśli testowe uaktualnienie nie powiedzie się, rozwiąż wszelkie problemy związane z awarią uaktualnienia bazy danych lokacji, Utwórz nową kopię zapasową bazy danych lokacji i przetestuj uaktualnienie nowej kopii bazy danych lokacji.  

     Gdy proces powiedzie się, możesz usunąć kopię bazy danych lokacji.  

    > [!NOTE]  
    >  Przywracanie kopii bazy danych lokacji użytej do testu uaktualnienia jako bazy danych dowolnej lokacji nie jest obsługiwane.  

###  <a name="bkmk_step3"></a>Krok 3: Uruchom narzędzie sprawdzania wymagań wstępnych przed instalacją aktualizacji  
Przed zainstalowaniem aktualizacji warto rozważyć uruchomienie narzędzie sprawdzania wymagań wstępnych dla tej aktualizacji. W przypadku uruchomienia sprawdzania wymagań wstępnych przed instalacją aktualizacji:  

-   Pliki aktualizacji są replikowane do innych witryn, przed zainstalowaniem aktualizacji.  

-   Sprawdzanie wymagań wstępnych automatycznie uruchomi ponownie w przypadku instalowania aktualizacji.  

Później po zainstalowaniu aktualizacji, istnieje możliwość konfigurowania aktualizacji Ignoruj ostrzeżenia dotyczące sprawdzania wymagań wstępnych.  

#### <a name="to-run-the-prerequisite-checker-before-installing-an-update"></a>Aby uruchomić narzędzie sprawdzania wymagań wstępnych przed instalacją aktualizacji  

1.  W konsoli programu Configuration Manager, przejdź do **Administracja** > **aktualizacji i obsługi**.   

2.  Kliknij prawym przyciskiem myszy pakiet aktualizacji, dla którego chcesz uruchomić sprawdzanie wymagań wstępnych.  

3.  Wybierz opcję **Uruchom sprawdzenie wymagań wstępnych**.  

     Po uruchomieniu sprawdzania wymagań wstępnych zawartość aktualizacji jest replikowana do lokacji podrzędnych.  Distmgr.log można wyświetlić w witrynie serwera, aby upewnić się, że zawartość replikuje pomyślnie.  

4.  Aby wyświetlić wyniki testu, w konsoli programu Configuration Manager przejdź do **monitorowanie** > **aktualizacji i obsługi stanu** i sprawdź stan wymagań wstępnych. Możesz również wyświetlić dziennik ConfigMgrPrereq.log na serwerze lokacji, aby uzyskać dodatkowe informacje.  



##  <a name="bkmk_install"></a> Instalacja aktualizacji w konsoli  
 Gdy wszystko będzie gotowe do zainstalowania aktualizacji z poziomu konsoli programu Configuration Manager możesz zaczynać się od lokacji najwyższego poziomu w hierarchii. Jest to centralna lokacja administracyjna lub autonomiczna lokacja główna.  

 Zaleca się zaplanowanie instalacji aktualizacji poza godzinach pracy dla każdej lokacji. Proces instalowania aktualizacji i jego akcji ponownego zainstalowania składników lokacji i ról systemu lokacji będą mieć co najmniej wpływ na operacje biznesowe.  

-   Podrzędne lokacje główne rozpoczynają aktualizację automatycznie po zakończeniu instalacji aktualizacji przez centralną lokację administracyjną. To jest ustawienie domyślne i zalecane procesu. Można jednak użyć [usługi systemu windows dla serwerów lokacji](/sccm/core/servers/manage/service-windows) do sterowania podczas instalowania aktualizacji w lokacji głównej.  

-   Po zakończeniu aktualizacji lokacji głównej nadrzędnej, należy ręcznie zaktualizować dodatkowej lokacji z konsoli programu Configuration Manager. Automatyczna aktualizacja serwerów lokacji dodatkowych nie jest obsługiwana.  

-   Korzystając z konsoli programu Configuration Manager po zaktualizowaniu witryny, wyświetlany jest monit o aktualizacji konsoli.  

-  Po pomyślnym zakończeniu instalowania aktualizacji serwera lokacji automatycznie aktualizuje wszystkich odpowiednich ról systemu lokacji.  Tylko zastrzeżenie: to jest dla punktów dystrybucji. Podczas instalowania aktualizacji, wszystkie punkty dystrybucji nie ponowna instalacja i przejdź do trybu offline, aby zaktualizować w tym samym czasie. Zamiast tego serwer lokacji używa ustawień dystrybucji zawartości witryny do dystrybucji aktualizacji do podzbioru punktów dystrybucji w czasie. Powoduje to, że niektóre punkty dystrybucji do trybu offline, aby zainstalować tę aktualizację. Dzięki temu punktów dystrybucji, które nie zostały jeszcze uruchomione zaktualizować lub które zostały ukończone aktualizacja, która ma pozostać online i zapewnia zawartości do klientów.


###  <a name="bkmk_overview"></a> Przegląd instalacji aktualizacji w konsoli  
**1. Podczas uruchamiania instalacji aktualizacji**  
Wyświetlany jest kreator aktualizacji z listą obszarów produktów, do których ma zastosowanie aktualizacja.  

-   Na stronie **Ogólne** kreatora można skonfigurować **Ostrzeżenia dotyczące wymagań wstępnych**.  
      -   Błędy wymagań wstępnych zawsze wstrzymują instalację aktualizacji. Należy naprawić błędy, aby pomyślnie ponowić próbę instalacji aktualizacji. Aby uzyskać więcej informacji, zobacz [Ponawianie nieudanej instalacji aktualizacji](#bkmk_retry) .  

    -   Ostrzeżenia dotyczące wymagań wstępnych mogą również wstrzymać instalację aktualizacji. Ostrzeżenia powinien rozwiązać przed ponowieniem instalacji aktualizacji. Aby uzyskać więcej informacji, zobacz [Ponawianie nieudanej instalacji aktualizacji](#bkmk_retry) .  
    -   Wybranie opcji **Ignoruj ostrzeżenia sprawdzania wymagań wstępnych i zainstalować tę aktualizację, niezależnie od wymagań Brak**, ustawia stan instalacji aktualizacji, które ignoruje ostrzeżenia dotyczące wymagań wstępnych. Dzięki temu instalacja aktualizacji kontynuować. Jeśli nie zaznaczysz tej opcji, instalacja aktualizacji zostanie zatrzymane po napotkaniu ostrzeżenie. O ile wcześniej uruchomieniu sprawdzania wymagań wstępnych i stałej ostrzeżenia dotyczące wymagań wstępnych dla lokacji, zaleca się użycie tej opcji.  

      W obu **Administracja** i **monitorowanie** obszarów roboczych, aktualizacji i obsługi węzeł zawiera przycisk na Wstążce o nazwie **Ignoruj ostrzeżenia dotyczące wymagań wstępnych**. Ten przycisk stają się dostępne po pakietu aktualizacji nie może ukończyć instalacji z powodu ostrzeżenia dotyczące sprawdzania wymagań wstępnych. Na przykład zainstalować aktualizację bez Ignoruj ostrzeżenia dotyczące wymagań wstępnych za pomocą opcji (z poziomu Kreatora aktualizacji), i aktualizacji, instalacja jest zatrzymywana ze stanem wymagań wstępnych ostrzeżenie, ale bez błędów można później **Ignoruj ostrzeżenia dotyczące wymagań wstępnych** na Wstążce, aby wyzwolić automatyczne kontynuacji tej instalacji aktualizacji, które następnie ignoruje ostrzeżenia dotyczące wymagań wstępnych. Tej opcji instalacji aktualizacji będzie automatycznie kontynuować działanie po kilku minutach.



-   Gdy aktualizacja dotyczy klienta programu Configuration Manager, zostanie wyświetlona z opcją do testowania aktualizacji klienta ograniczony zestaw klientów. Aby uzyskać więcej informacji, zobacz [jak przetestować uaktualnienia klienta w kolekcji przedprodukcyjnej w programie System Center Configuration Manager](../../../core/clients/manage/upgrade/test-client-upgrades.md).  

**2. Podczas instalacji aktualizacji**  
W ramach instalacji aktualizacji programu Configuration Manager:  

-   Instaluje ponownie wszystkie objętych składników, takich jak role systemu lokacji lub konsoli programu Configuration Manager.  

-   Zarządzanie aktualizacjami na klientach zgodnie z opcjami wprowadzone dla klienta pilotażowe i [automatyczne uaktualnienia klienta](https://technet.microsoft.com/library/mt627885.aspx).  

-   Nie będzie konieczne ponowne uruchomienie serwerów systemu lokacji w ramach aktualizacji (chyba że .NET jest instalowany jako część wymagania wstępne ról systemu lokacji).  

> [!TIP]  
>  Po zainstalowaniu aktualizacji programu Configuration Manager aktualizuje także dysku CD. Najnowszy folder. Ten folder jest używany podczas odzyskiwania lokacji.  

**3. Monitorować postęp aktualizacji podczas instalacji**  
Postęp można monitorować przy użyciu następujących elementów:  

-   W konsoli programu Configuration Manager: **Administracja** > **aktualizacji i obsługi** węzła. Ten węzeł wyświetla stan instalacji dla wszystkich pakietów aktualizacji.


-   W konsoli programu Configuration Manager: **Monitorowanie** > **Przegląd** > **aktualizacji i obsługi stanu** węzła. Ten węzeł zawiera stan instalacji pakietu aktualizacji, który jest obecnie zainstalowany.  

  Instalacja pakietu aktualizacji dzieli się z następujących faz w celu ułatwienia monitorowania. Dla każdej fazy dodatkowe szczegóły zawierają których plik dziennika, aby wyświetlić więcej informacji.:  
    -   **Pobierz** (faza dotyczy tylko do lokacji najwyższego poziomu, w którym zainstalowano rolę systemu lokacji punktu połączenia usługi).
    -   **Replikacja**
    -   **Sprawdzanie wymagań wstępnych**
    -   **Instalacja**
    -   **Po instalacji** (tej fazy jest dostępna począwszy od wersji 1610).

-   Można wyświetlić **CMUpdate.log** pliku w  **&lt;ConfigMgr_Installation_Directory > \Logs**  

**4. Po ukończeniu instalacji aktualizacji**  
Po zakończeniu instalacji aktualizacji pierwszej lokacji:  

-   Podrzędne lokacje główne instalują aktualizację automatycznie. Nie ma potrzeby wykonywania dalszych czynności.  

-   Lokacje dodatkowe należy ręcznie zaktualizować z w ramach konsoli programu Configuration Manager.
> [!TIP]
> Mimo że wersja lokacji dodatkowej nie są wyświetlane w konsoli, można użyć zestawu SDK programu Configuration Manager o potwierdzenie wersja lokacji. Zobacz [klasy WMI serwera SMS_Site](https://technet.microsoft.com/library/hh442832(CMSDK.16).aspx).


-   Do czasu zaktualizowania wszystkich lokacji w ramach hierarchii do nowej wersji hierarchia działa w trybie wersji mieszanej. Aby uzyskać więcej informacji, zobacz [Współdziałanie różnych wersji programu System Center Configuration Manager](../../../core/plan-design/hierarchy/interoperability-between-different-versions.md).  

**5.   Aktualizacja konsol programu Configuration Manager**  
Po centralnej lokacji administracyjnej lub lokacji głównej aktualizacji należy również zaktualizować Każda konsola programu Configuration Manager łączący się do tej lokacji. Monit o aktualizację konsoli zostanie wyświetlony:  

-   Po otwarciu konsoli.  

-   Po przejściu do nowego węzła w otwartej konsoli.  

Zaleca się natychmiast zainstalować tę aktualizację.  

Po zakończeniu aktualizacji konsoli możesz sprawdzić, czy wersje konsoli i lokacji są poprawne. Przejdź do **System Center Configuration Manager** w lewym górnym rogu konsoli.  

###  <a name="bkmk_toptier"></a> Aby rozpocząć instalację aktualizacji w lokacji najwyższego poziomu  
W lokacji najwyższego poziomu w hierarchii, w konsoli programu Configuration Manager przejdź do **Administracja** > **aktualizacji i obsługi**, wybierz opcję **dostępne** aktualizacji, a następnie kliknij przycisk **zainstalować pakiet aktualizacji**.  

###  <a name="bkmk_secondary"></a> Aby rozpocząć instalację aktualizacji w lokacji dodatkowej  
Po zaktualizowaniu dodatkowej lokacji nadrzędnej lokacji głównej można zaktualizować lokacji dodatkowej z konsoli programu Configuration Manager.  W tym celu należy użyć **Kreatora uaktualniania lokacji dodatkowej**.  

1.  W konsoli programu Configuration Manager przejdź do **Administracja** > **konfiguracja lokacji** > **witryny**, wybierz witryny, którą chcesz zaktualizować, a następnie na stronie głównej karcie w **witryny** grupy, wybierz **uaktualnienia**.  

2.  Kliknij przycisk **Tak** , aby rozpocząć aktualizację lokacji dodatkowej.  

Aby monitorować instalację aktualizacji w lokacji dodatkowej, wybierz serwer lokacji dodatkowej. Następnie na **Home** w karcie **witryny** grupy, wybierz **Pokaż stan instalacji**. Możesz również dodać kolumnę **Wersja** do wyświetlanej konsoli, co umożliwia wyświetlanie wersji poszczególnych lokacji dodatkowych.  

Po lokacji dodatkowej została pomyślnie zaktualizowana, jeśli stan w konsoli nie będzie odświeżana lub sugeruje aktualizacji nie powiodło się, można użyć **ponów próbę instalacji** opcji. Ta opcja nie ponownie zainstalować aktualizację lokacji dodatkowej pomyślnie zainstalowała aktualizacji, ale wymusi konsoli do aktualizowania stanu.


##  <a name="bkmk_retry"></a> Ponawianie nieudanej instalacji aktualizacji  
W przypadku niepowodzenia aktualizacji do zainstalowania, przejrzyj opinii w konsoli do identyfikowania rozwiązania dla ostrzeżeń i błędów. Możesz również wyświetlić dziennik ConfigMgrPrereq.log na serwerze lokacji, aby uzyskać dodatkowe informacje. Aby ponowić próbę wykonania instalacji aktualizacji, musisz naprawić błędy, a powinien rozwiązać ostrzeżenia.  

Gdy wszystko będzie gotowe ponowić próbę instalacji aktualizacji, wybierz aktualizacji nie powiodło się, a następnie wybierz odpowiednią opcję. Zachowanie ponów próbę instalacji aktualizacji zależy od węzła próby uruchomienia i używasz opcji ponów próbę.  

1.  **Ponów próbę instalacji hierarchii:**  
Możesz ponowić instalację aktualizacji całej hierarchii, jeśli aktualizacja ta ma jeden z następujących stanów:  

    -   Sprawdzanie wymagań wstępnych przekazywany z jednego lub więcej ostrzeżeń, a nie ustawiono opcję Ignoruj ostrzeżenia dotyczące sprawdzania wymagań wstępnych Kreatora aktualizacji. (Wartość aktualizacji **Ignoruj ostrzeżenia wstępnym** w **Obsługa** węzeł jest **nr**.)   
    -   Niepowodzenie wymagań wstępnych    
    -   Niepowodzenie instalacji
    -   Replikacja zawartości do lokacji nie powiodła się   

    Przejdź do **Administracja** > **aktualizacji i obsługi**wybierz aktualizację, a następnie wybierz jedną z następujących czynności:  

    -   **Spróbuj ponownie wykonać** — w przypadku uruchamiania **ponów** z tego węzła aktualizacja ponownie zainstalować rozpoczyna się i zostanie automatycznie Ignoruj ostrzeżenia dotyczące wymagań wstępnych. Zostanie również przeprowadzona ponowna replikacja zawartości aktualizacji, jeśli wcześniej replikacja zakończyła się niepowodzeniem.
    - **Ignoruj ostrzeżenia dotyczące wymagań wstępnych** — począwszy od wersji 1606, zatrzymuje się z powodu ostrzeżenie zainstalowania aktualizacji, można wybrać **Ignoruj ostrzeżenia dotyczące wymagań wstępnych**. Ta akcja umożliwia kontynuowanie instalacji aktualizacji (po kilku minutach) z użyciem opcji ignorowania ostrzeżeń dotyczących wymagań wstępnych.   

2.  **Ponów próbę instalacji lokacji:**  
 Możesz ponowić instalację aktualizacji w określonej lokacji, jeśli aktualizacja ma jeden z następujących stanów:  

    -   Sprawdzanie wymagań wstępnych przekazywany z jednego lub więcej ostrzeżeń, a nie ustawiono opcję Ignoruj ostrzeżenia dotyczące sprawdzania wymagań wstępnych Kreatora aktualizacji (aktualizacje wartość **Ignoruj ostrzeżenia wstępnym** w aktualizacji i obsługi węzła jest **nr**.)  
    -   Niepowodzenie wymagań wstępnych    
    -   Niepowodzenie instalacji    

    Przejdź do pozycji **Monitorowanie** > **Przegląd** > **Stan obsługi lokacji**, a następnie kliknij jedną z następujących opcji:

       - **Spróbuj ponownie wykonać** — w przypadku uruchamiania **ponów** z tego węzła po ponownym uruchomieniu instalacji aktualizacji tylko w tej lokacji. W przeciwieństwie do uruchomienia **ponów** z **aktualizacji i obsługi** węzła, to ponów próbę Ignoruj ostrzeżenia dotyczące wymagań wstępnych.
       -    **Ignoruj ostrzeżenia dotyczące wymagań wstępnych** — począwszy od wersji 1606, zatrzymuje się z powodu ostrzeżenie zainstalowania aktualizacji, po kliknięciu **Ignoruj ostrzeżenia dotyczące wymagań wstępnych**. Ta akcja umożliwia kontynuowanie instalacji aktualizacji (po kilku minutach) z użyciem opcji ignorowania ostrzeżeń dotyczących wymagań wstępnych.

##  <a name="bkmk_after"></a> Po zainstalowaniu aktualizacji lokacji  
Do wykonania typowych zadań i konfiguracji, które zostały wprowadzone po zaktualizowaniu witryny, należy użyć poniższej listy kontrolnej.   

**Potwierdź, że lokacja lokacja replikacji jest aktywne:** W konsoli programu Configuration Manager Przejdź w następujących lokalizacjach, aby wyświetlić stan i upewnij się, że replikacja jest aktywny:  

-   **Monitorowanie** > **Przegląd** > **Hierarchia lokacji**  

-   **Monitorowanie** > **Przegląd** > **Replikacja bazy danych**  

Aby uzyskać więcej informacji, zobacz [monitorowanie hierarchii i replikacji infrastruktury w programie System Center Configuration Manager](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md) i [o analizator łącza replikacji](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_RLA).  

 **Należy się upewnić, że serwery lokacji i serwery systemu lokacji zdalnej ponownym uruchomieniu (Jeśli wymagane):** Przejrzyj infrastrukturę lokacji i upewnij się, że serwery uaktualnianej lokacji i serwery systemu lokacji (zdalnie z serwera lokacji) mają została pomyślnie uruchomiona ponownie.  Zazwyczaj jest to oczekiwany tylko wtedy, gdy program Configuration Manager instaluje .NET jako warunek wstępny dla roli systemu lokacji.  

 **Aktualizacja autonomicznych konsol programu Configuration Manager:** Sprawdź, czy wszystkie zdalne konsole programu Configuration Manager są aktualizacji do tej samej wersji. Monit o aktualizację konsoli jest wyświetlany w następujących sytuacjach:  

-   Można przejść do nowego węzła w konsoli.  

-   Otwórz konsolę.

**Skonfiguruj ponownie repliki bazy danych dla punktów zarządzania w lokacjach głównych:** Jeśli są używane repliki bazy danych dla punktów zarządzania w lokacjach głównych, należy odinstalować repliki bazy danych przed aktualizacją lokacji. Po aktualizacji lokacji głównej skonfiguruj ponownie repliki bazy danych dla punktów zarządzania. Aby uzyskać więcej informacji, zobacz [Repliki bazy danych dla punktów zarządzania programu System Center Configuration Manager](../../../core/servers/deploy/configure/database-replicas-for-management-points.md).  

**Skonfiguruj ponownie wszystkie wyłączone przed uaktualnieniem zadania konserwacji bazy danych:** Wyłączenie bazy danych [zadania konserwacji programu System Center Configuration Manager](../../../core/servers/manage/maintenance-tasks.md) w witrynie wcześniejszych niż aktualizacja, skonfiguruj je ponownie w lokacji. Użyj tych samych ustawień stosowanych przed uaktualnieniem.  

**Uaktualnij klientów:** Aby uzyskać więcej informacji o sposobie uaktualniania istniejących klientów i instalowaniu nowych klientów, zobacz [Uaktualnianie klientów komputerów z systemem Windows w programie System Center Configuration Manager](../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md).  

**Dodatkowe konfiguracje:** Przejrzyj zmiany przed rozpoczęciem aktualizacji, a następnie przywrócić te konfiguracje lokacji i hierarchii.  

##  <a name="bkmk_options"></a> Włącz funkcje opcjonalne aktualizacji  
Po zainstalowaniu aktualizacji obejmującej co najmniej jedną funkcję opcjonalną dostępna jest możliwość włączenia tych funkcji w hierarchii.  Można więc razem, gdy aktualizacja jest zainstalowana albo można później powrócić do konsoli i włączają opcjonalne funkcje.

Aby wyświetlić dostępne funkcje i ich stan, w konsoli przejdź do **Administracja** > **aktualizacji i obsługi** > **funkcji**.

Gdy funkcja nie jest opcjonalne, jest instalowana automatycznie i nie jest widoczna w **funkcje** węzła.  


Po włączeniu nowych funkcji lub funkcji wersji wstępnej, Menedżer hierarchii programu Configuration Manager (HMAN) musi przetworzyć zmiany przed danej funkcji staje się dostępny. Często jest bezpośrednim przetwarzanie zmiany, ale może potrwać do 30 minut, w zależności od HMAN cykl przetwarzania. Po przetworzeniu zmiany należy ponownie uruchomić konsolę można było wyświetlić nowy interfejs użytkownika powiązanych z daną funkcją.


##  <a name="bkmk_prerelease"></a> Używanie funkcji w wersjach wstępnych z poziomu aktualizacji
Funkcje wersji wstępnej są funkcje, które znajdują się w bieżącej gałęzi dla wczesnych testowanie w środowisku produkcyjnym. Te funkcje nie należy traktować jako produkcji gotowe, ale mogą być używane w środowisku produkcyjnym. Aby dowiedzieć się więcej o wersji wstępnej funkcji, takich jak włączyć je w danym środowisku, zobacz [funkcji wersji wstępnej](/sccm/core/servers/manage/pre-release-features).             


## <a name="known-issues"></a>Znane problemy

###  <a name="bkmk_faq"></a>Dlaczego nie widzę niektórych aktualizacji w mojej konsoli?  
 Jeśli nie można odnaleźć określonej aktualizacji (lub wszystkie aktualizacje) w konsoli po pomyślnej synchronizacji z usługą w chmurze firmy Microsoft, może to być spowodowane:  

-   Aktualizacja wymaga konfiguracji, której nie używa dana infrastruktura lub też bieżąca wersja produktu nie spełnia wymagań wstępnych dotyczących pobierania aktualizacji.  

     Jeśli uważasz, że masz wymagane konfiguracje lub spełnia inne wymagania wstępne dotyczące brakującą aktualizację, upewnij się, że ten punkt połączenia usługi jest w trybie online. Następnie należy użyć **Wyszukaj aktualizacje** opcji w **aktualizacji i obsługi** węzła do wymuszenia sprawdzania.  Jeśli jesteś w trybie offline, musisz użyć narzędzia połączenia usługi, aby przeprowadzić ręczną synchronizację z usługą w chmurze.  

-   Twoje konto nie ma uprawnień poprawne administracji opartej na rolach do wyświetlania aktualizacji w konsoli programu Configuration Manager.

    Zobacz sekcję [Uprawnienia do zarządzania aktualizacjami](../../../core/servers/manage/install-in-console-updates.md#assign-permissions-to-view-and-manage-updates-and-features) w tym temacie, aby uzyskać informacje o uprawnieniach wymaganych do wyświetlania aktualizacji i włączania funkcji z poziomu konsoli.

### <a name="why-do-i-see-two-updates-for-version-1610"></a>Dlaczego widzę dwóch aktualizacji dla wersji 1610
Podczas wyświetlania aktualizacji w konsoli, można napotkać dwóch aktualizacji, aby zainstalować wersję 1610. Te aktualizacje mają różne dni. Dzieje się tak, gdy jest spełniony jeden z następujących czynności:   
-    Zainstalowana starsza wersja (na przykład 1606) po wersji 1610 stały się dostępne

-    Możesz hierarchii jest uruchomiona wersja 1511 lub 1602 i nie zostały jeszcze można pobrać wersji 1606

Istnieją dwie wersje dla wersji 1610, ponieważ ta aktualizacja została wydana ponownie po niektórych drobne zmiany do niektórych plików binarnych plików zostały wprowadzone aktualizacji. Te zmiany nie wpływają na funkcje programu Configuration Manager lub aktualizacji.

Gdy obie aktualizacje są dostępne w konsoli, zaleca się zainstalowanie aktualizacji z nowszą datę. Jednak ponieważ zarówno aktualizacje dostarczać funkcji, jeśli nie jest już zainstalowany jeden z nich nie należy podejmować dalszych czynności.
-    Jeśli wcześniej zainstalowane starsze aktualizacji, jest konieczne zainstalowanie aktualizacji z nowszej daty. Jednak po zainstalowaniu nowsza aktualizacja po o zainstalowanie aktualizacji pierwszy, zaktualizuje użyciu plików binarnych, ale nie dodatkowe zmiany i niezbędne żadnych dodatkowych czynności ze strony użytkownika.

-    Jeśli wcześniej zainstalowano nowszą aktualizację, a następnie zainstalować aktualizację starszych daty, jest konieczne żadne dodatkowe działania. Jest to spowodowane nowsze pliki binarne są już zainstalowane nie zostaną zastąpione przez wartości binarne tego samego z oryginalnej aktualizacji.

