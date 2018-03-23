---
title: Aktualizacje w konsoli
titleSuffix: Configuration Manager
description: Zainstaluj aktualizacje do programu Configuration Manager z firmy Microsoft w chmurze
ms.custom: na
ms.date: 03/22/2018
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology:
- configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c14a3607-253b-41fb-8381-ae2d534a9022
caps.latest.revision: ''
author: mestew
ms.author: mstewart
manager: dougeby
ms.openlocfilehash: 5d364e35c8777c782499da978f0d1a31694278cc
ms.sourcegitcommit: 11bf4ed40ed0cbb10500cc58bbecbd23c92bfe20
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/23/2018
---
# <a name="install-in-console-updates-for-system-center-configuration-manager"></a>Instalacja aktualizacji w konsoli programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Synchronizuje programu Configuration Manager z usługą w chmurze firmy Microsoft do pobierania aktualizacji. Następnie można zainstalować te aktualizacje z poziomu konsoli programu Configuration Manager.

## <a name="get-available-updates"></a>Uzyskiwanie dostępnych aktualizacji
Pobierane i udostępniane hierarchii użytkownika są tylko aktualizacje mające zastosowanie do danej infrastruktury i wersji. Synchronizacja ta może być automatycznie lub ręcznie, w zależności od sposobu skonfigurowania punktu połączenia usługi dla hierarchii:

-   W **trybie online**punkt połączenia usługi automatycznie łączy się z usługą firmy Microsoft w chmurze i pobiera odpowiednie aktualizacje.  

     Domyślnie program Configuration Manager sprawdza dostępność aktualizacji co 24 godziny. Możesz również sprawdzić aktualizacje od razu, wybierając **Sprawdź aktualizacje** w **administracji** > **aktualizacje i obsługa** węzła konsoli programu Configuration Manager. 

-   W **w trybie offline**, punkt połączenia usługi nie połączyć z usługą w chmurze firmy Microsoft. Aby pobierać i importować dostępne aktualizacje, [użyć narzędzia połączenia z usługą](../../../core/servers/manage/use-the-service-connection-tool.md).  

> [!NOTE]  
>   Poprawki poza pasmem można zaimportować do konsoli. Aby to zrobić, użyj [narzędzia rejestracji aktualizacji](/sccm/core/servers/manage/use-the-update-registration-tool-to-import-hotfixes). Niniejsze poprawki poza pasmem uzupełniają aktualizacje, które wystąpiły podczas synchronizacji z usługą w chmurze firmy Microsoft.


Po aktualizacji synchronizacji, można wyświetlić je w konsoli programu Configuration Manager, przechodząc do **administracji** > **aktualizacje i obsługa** węzła:  

-   Aktualizacje niezainstalowane są wyświetlane jako **Dostępne**.

-   Aktualizacje zainstalowane są wyświetlane jako **Zainstalowane**. Jest wyświetlana tylko ostatnią zainstalowaną aktualizację. Możesz wybrać **historii** na Wstążce, aby wyświetlić wcześniej zainstalowane aktualizacje.



Przed skonfigurowaniem punktu połączenia usługi, zrozumieć i zaplanuj jego dodatkowe funkcje. Następujące zastosowania mogą mieć wpływ na sposób konfigurowania tej roli systemu lokacji:  

-   Punkt połączenia z usługą służy do przekazywania informacji o użyciu lokacji. Informacje te pomagają usłudze firmy Microsoft w chmurze zidentyfikować aktualizacje dostępne dla bieżącej wersji infrastruktury. Aby uzyskać więcej informacji, zobacz [diagnostyczne i dane użycia](../../../core/plan-design/diagnostics/diagnostics-and-usage-data.md).  

-   Punkt połączenia usługi jest używany do zarządzania urządzeniami w usłudze Microsoft Intune i przy użyciu programu Configuration Manager na lokalnego zarządzania urządzeniami przenośnymi. Aby uzyskać więcej informacji, zobacz [Hybrydowe zarządzanie urządzeniami przenośnymi za pomocą programu System Center Configuration Manager i usługi Microsoft Intune](../../../mdm/understand/hybrid-mobile-device-management.md).  

Aby lepiej zrozumieć, co się stanie, jeśli aktualizacje zostaną pobrane, zobacz:  

-   [Schemat blokowy — pobieranie aktualizacji programu System Center Configuration Manager](../../../core/servers/manage/download-updates-flowchart.md)

-   [Schemat blokowy — replikacji aktualizacji dla programu System Center Configuration Manager](../../../core/servers/manage/update-replication-flowchart.md)  



## <a name="assign-permissions-to-view-and-manage-updates-and-features"></a>Przypisywanie uprawnień do wyświetlania i zarządzania nimi, aktualizacje i funkcje
Aby wyświetlać aktualizacje w konsoli, użytkownik musi mieć rolę zabezpieczeń administracji opartej na rolach, który zawiera klasę zabezpieczeń **pakietów aktualizacji**. Ta klasa udziela dostępu do wyświetlania i zarządzania aktualizacjami w konsoli programu Configuration Manager.    

#### <a name="about-the-update-packages-class"></a>Informacje o klasie pakietów aktualizacji   
Domyślnie **pakietów aktualizacji** klasy (SMS_CM_Updatepackages) jest częścią następującego wbudowanych ról zabezpieczeń z listę uprawnień:
 -  **Administrator o pełnych uprawnieniach** z uprawnieniami **Modyfikacja** i **Odczyt** :
    -   Użytkownik z tej roli zabezpieczeń i dostępu do **wszystkie** zakres zabezpieczeń można wyświetlić i zainstalować aktualizacje. Użytkownika można również włączyć funkcje podczas instalacji i włączyć poszczególne funkcje, po zainstalowaniu tej aktualizacji.
    - Użytkownik z tej roli zabezpieczeń i dostępu do **domyślne** zakres zabezpieczeń można wyświetlić i zainstalować aktualizacje. Użytkownik może również włączyć funkcje podczas instalacji i wyświetlić funkcji po zainstalowaniu aktualizacji. Jednak ten użytkownik nie może włączyć funkcji po zainstalowaniu tej aktualizacji.

- **Analityk z uprawnieniami tylko do odczytu** z uprawnieniami **Odczyt** :
  -  Użytkownik z tej roli zabezpieczeń i dostępu do **domyślne** zakres można wyświetlić aktualizacje, ale nie można je zainstalować. Ten użytkownik może również wyświetlać funkcje po aktualizacja została zainstalowana, ale nie można włączyć je.

#### <a name="permissions-required-for-updates-and-servicing"></a>Uprawnienia wymagane dla aktualizacje i obsługa   
  - Użyj konta, któremu przypisano rolę zabezpieczeń zawierającą klasę **Pakiety aktualizacji** z uprawnieniami **Modyfikacja** i **Odczyt** .
  - Konto musi być przypisane do zakresu **Domyślne** .

#### <a name="permissions-to-only-view-updates"></a>Uprawnienia, aby wyświetlić tylko aktualizacje   
  - Użyj konta, które ma przypisaną rolę zabezpieczeń obejmującą **pakietów aktualizacji** tylko klasy z **odczytu** uprawnienia.
  - Konto musi być przypisane do zakresu **Domyślne** .

#### <a name="permissions-required-to-enable-features-after-updates-are-installed"></a>Uprawnienia wymagane do włączenia funkcji po zainstalowaniu aktualizacji   
  -  Użyj konta, któremu przypisano rolę zabezpieczeń zawierającą klasę **Pakiety aktualizacji** z uprawnieniami **Modyfikacja** i **Odczyt** .
  -  Konto musi być przypisane do zakresu **Wszystkie** .



##  <a name="bkmk_beforeinstall"></a> Przed zainstalowaniem aktualizacji w konsoli  
 Przejrzyj poniższe kroki przed zainstalowaniem aktualizacji z poziomu konsoli programu Configuration Manager.  

###  <a name="bkmk_step1"></a> Krok 1. Przejrzyj listę kontrolną aktualizacji  
Przejrzyj odpowiednią listę kontrolną aktualizacji czynności należy wykonać przed rozpoczęciem aktualizacji:

- [Lista kontrolna instalowania aktualizacji 1706](../../../core/servers/manage/checklist-for-installing-update-1706.md)  

- [Lista kontrolna instalowania aktualizacji 1710](../../../core/servers/manage/checklist-for-installing-update-1710.md)  

- [Lista kontrolna dotycząca instalowania aktualizacji 1802](../../../core/servers/manage/checklist-for-installing-update-1802.md)


###  <a name="step-2-run-the-prerequisite-checker-before-installing-an-update"></a>Krok 2. Uruchom narzędzie sprawdzania wymagań wstępnych przed instalacją aktualizacji  
Przed zainstalowaniem aktualizacji warto rozważyć uruchomienie narzędzie sprawdzania wymagań wstępnych dla tej aktualizacji. W przypadku uruchomienia sprawdzania wymagań wstępnych przed instalacją aktualizacji:  

-   Pliki aktualizacji są replikowane do innych lokacji przed zainstalowaniem aktualizacji.  

-   Sprawdzanie wymagań wstępnych automatycznie uruchomiony ponownie w przypadku zainstalowania aktualizacji.  

> [!NOTE]   
> Po uruchomieniu sprawdzania wymagań wstępnych i następnie wyświetlić stan, **instalacji** fazy wydaje się być aktywne, jednak aktualizacja nie jest w rzeczywistości zainstalowano. Do sprawdzania wymagań wstępnych, proces aktualizacji wyodrębnia pakiet z biblioteki zawartości i umieszczenie go do folderu przemieszczania, gdzie można uzyskać dostęp do bieżącej Sprawdzanie wymagań wstępnych. Ten sam proces jest uruchamiana po zainstalowaniu aktualizacji. Z tego powodu instalacja jest pokazywana jako "W toku". Tylko *pakiet aktualizacji wyodrębnij* kroku jest wyświetlany w kategorii instalacji.  

Później po zainstalowaniu aktualizacji można skonfigurować aktualizacji do ignorowania ostrzeżeń sprawdzania wymagań wstępnych.  

#### <a name="to-run-the-prerequisite-checker-before-installing-an-update"></a>Aby uruchomić narzędzie sprawdzania wymagań wstępnych przed instalacją aktualizacji  

1.  W konsoli programu Configuration Manager, przejdź do **administracji** > **aktualizacje i obsługa**.   

2.  Kliknij prawym przyciskiem myszy na pakiet aktualizacji, który chcesz uruchomić sprawdzanie wymagań wstępnych.  

3.  Wybierz opcję **Uruchom sprawdzenie wymagań wstępnych**.  

     Po uruchomieniu sprawdzania wymagań wstępnych zawartość aktualizacji jest replikowana do lokacji podrzędnych. Możesz wyświetlić plik distmgr.log w lokacji serwera, aby upewnić się, że zawartość replikuje pomyślnie.  

4.  Aby wyświetlić wyniki sprawdzania, w konsoli programu Configuration Manager przejdź do **monitorowanie** > **aktualizacji i obsługi stanu** i odszukaj stan wymagań wstępnych. Możesz również wyświetlić dziennik ConfigMgrPrereq.log na serwerze lokacji, aby uzyskać dodatkowe informacje.  



##  <a name="bkmk_install"></a> Instalacja aktualizacji w konsoli  
 Gdy wszystko będzie gotowe do zainstalowania aktualizacji z poziomu konsoli programu Configuration Manager można rozpoczynać się od lokacji najwyższego poziomu w hierarchii. Ta lokacja jest centralną lokacją administracyjną lub autonomiczną lokację główną.  

 Zaleca się zainstalowanie aktualizacji poza normalnymi godzinami pracy każdej lokacji zminimalizować wpływ na operacje biznesowe. To zalecenie wynika instalacji aktualizacji może obejmować akcje, takie jak ponowne zainstalowanie składników lokacji i ról systemu lokacji.  

-   Podrzędne lokacje główne rozpoczynają aktualizację automatycznie po zakończeniu instalacji aktualizacji przez centralną lokację administracyjną. Ten proces jest domyślnie i zalecane. Można jednak użyć [usługi systemu windows dla serwerów lokacji](/sccm/core/servers/manage/service-windows) do kontrolowania, kiedy w lokacji głównej instaluje aktualizacje.  

-   Ręcznie zaktualizować Lokacje dodatkowe przy użyciu konsoli programu Configuration Manager po zakończeniu aktualizacji lokacji głównej. Automatyczna aktualizacja serwerów lokacji dodatkowych nie jest obsługiwana.  

-   Użycie konsoli programu Configuration Manager po zaktualizowaniu lokacji wyświetlany jest monit o aktualizację konsoli.  

-  Po serwera lokacji pomyślnie ukończy instalację aktualizacji, automatycznie aktualizuje wszystkich odpowiednich ról systemu lokacji. To ostrzeżenie tylko dla punktów dystrybucji. Podczas instalowania aktualizacji, wszystkie punkty dystrybucji nie ponownej instalacji i przejść do trybu offline, aby zaktualizować w tym samym czasie. Zamiast tego serwer lokacji używa witryny ustawienia dystrybucji zawartości do dystrybucji aktualizacji do podzbioru punktów dystrybucji w czasie. Wynik jest, że niektóre punkty dystrybucji Przejdź offline, aby zainstalować tę aktualizację. Punkty dystrybucji, który zaczęli nie można zaktualizować lub które zostały ukończone aktualizacji pozostają online i możliwość zapewnienia zawartości do klientów.


###  <a name="bkmk_overview"></a> Przegląd instalacji aktualizacji w konsoli  
#### <a name="1-when-the-update-installation-starts"></a>1. Po rozpoczęciu instalacji aktualizacji  
Wyświetlany jest kreator aktualizacji z listą obszarów produktów, do których ma zastosowanie aktualizacja.  

-   Na stronie **Ogólne** kreatora można skonfigurować **Ostrzeżenia dotyczące wymagań wstępnych**.  
    -   Błędy wymagań wstępnych zawsze wstrzymują instalację aktualizacji. Napraw błędy, zanim mógł pomyślnie ponowić próbę instalacji aktualizacji. Aby uzyskać więcej informacji, zobacz [ponawiania instalacji aktualizacji nie powiodło się](#bkmk_retry).  

    -   Ostrzeżenia dotyczące wymagań wstępnych mogą również wstrzymać instalację aktualizacji. Napraw ostrzeżenia przed ponowieniem instalacji aktualizacji. Aby uzyskać więcej informacji, zobacz [ponawiania instalacji aktualizacji nie powiodło się](#bkmk_retry).  
    -   **Zignoruj wszelkie ostrzeżenia dotyczące sprawdzania wymagań wstępnych i zainstaluj tę aktualizację bez względu na niespełnione wymagania**: Określa warunek instalacji aktualizacji ignoruje ostrzeżenia dotyczące wymagań wstępnych. Ta opcja umożliwia kontynuowanie instalacji aktualizacji. Jeśli nie zaznaczysz tej opcji instalacji aktualizacji zatrzymuje w przypadku napotkania ostrzeżenia. Jeśli wcześniej nie przeprowadzono sprawdzania wymagań wstępnych i stałym ostrzeżenia dotyczące wymagań wstępnych dla lokacji, nie zaleca się użycie tej opcji.  

      W obu **administracji** i **monitorowanie** obszarów roboczych, aktualizacje i obsługa zawiera przycisk na Wstążce o nazwie **Ignoruj ostrzeżenia dotyczące wymagań wstępnych**. Ten przycisk jest dostępny, gdy pakiet aktualizacji nie powiedzie się ukończyć instalację z powodu ostrzeżenia dotyczące sprawdzania wymagań wstępnych. Na przykład zainstalować aktualizację bez użycia opcji ignorowania ostrzeżeń dotyczących wymagań wstępnych (z poziomu Kreatora aktualizacji). Instalacja aktualizacji zatrzymuje się ze stanem ostrzeżenia dotyczące wymagań wstępnych, ale żadne błędy. Później możesz **Ignoruj ostrzeżenia dotyczące wymagań wstępnych** na Wstążce, aby wyzwolić automatyczne kontynuacji tej instalacji aktualizacji, który następnie ignoruje ostrzeżenia dotyczące wymagań wstępnych. Tej opcji instalacji aktualizacji będzie automatycznie kontynuować działanie po kilku minutach.



-   Jeśli aktualizacja ma zastosowanie do klienta programu Configuration Manager, jest wyświetlana opcja przetestowania aktualizacji klienta na ograniczonym zestawie klientów. Aby uzyskać więcej informacji, zobacz [testowanie uaktualnień klienta w kolekcji przedprodukcyjnej](../../../core/clients/manage/upgrade/test-client-upgrades.md).  


#### <a name="2-during-the-update-installation"></a>2. W trakcie instalacji aktualizacji  
W ramach instalacji aktualizacji program Configuration Manager:  

-   Ponownie instaluje żadnych odpowiednich składników, takich jak role systemu lokacji lub konsoli programu Configuration Manager.  

-   Zarządza aktualizacjami klientów zgodnie z opcjami wprowadzone w przypadku wdrażania pilotażowego klienta oraz [automatycznych uaktualnień klienta](/sccm/core/clients/manage/upgrade/upgrade-clients-for-windows-computers#use-automatic-client-upgrade).  

-   Nie ponowne uruchomienie serwerów systemu lokacji jako część aktualizacji w ramach wymagań wstępnych ról systemu lokacji instalowana jest platforma .NET.  

> [!TIP]  
>  Podczas instalowania aktualizacji programu Configuration Manager aktualizuje również dysku CD. Najnowszy folder. Ten folder jest używany podczas odzyskiwania lokacji.  


#### <a name="3-monitor-the-progress-of-updates-as-they-install"></a>3. Monitorowanie postępu aktualizacji podczas instalacji  
Postęp można monitorować przy użyciu następujących elementów:  

-   W konsoli programu Configuration Manager: **Administracja** > **aktualizacje i obsługa** węzła. Ten węzeł wyświetla stan instalacji dla wszystkich pakietów aktualizacji.


-   W konsoli programu Configuration Manager: **Monitorowanie** > **omówienie** > **aktualizacji i obsługi stanu** węzła. Ten węzeł Wyświetla stan instalacji pakietu aktualizacji, które jest obecnie zainstalowane.  

    Instalacja pakietu aktualizacji jest podzielone na następujące etapy w celu ułatwienia monitorowania. Dla każdej fazy dodatkowe szczegóły zawierają który plik dziennika, aby wyświetlić więcej informacji:  
    -   **Pobierz** (Ta faza dotyczy tylko do lokacji najwyższego poziomu, w którym zainstalowano lokacji punktu połączenia usługi).   

    -   **Replikacja**   

    -   **Sprawdzanie wymagań wstępnych**   

    -   **Instalacja**    

    -   **Po zakończeniu instalacji** — Aby uzyskać więcej informacji, zobacz [zadania instalacji po](#post-installation-tasks).  

-   Możesz wyświetlić **CMUpdate.log** w pliku  **&lt;Katalog_instalacyjny_programu_configmgr > \Logs**  


#### <a name="4-when-the-update-installation-completes"></a>4. Po zakończeniu instalacji aktualizacji  
Po zakończeniu instalacji aktualizacji pierwszej lokacji:  

-   Podrzędne Lokacje główne instalują aktualizację automatycznie. Nie ma potrzeby wykonywania dalszych czynności.  

-   Lokacje dodatkowe należy zaktualizować ręcznie z poziomu konsoli programu Configuration Manager.
> [!TIP]
> Chociaż wersja lokacji dodatkowej nie zostanie wyświetlone w konsoli, za pomocą zestawu SDK programu Configuration Manager i potwierdzić wersja lokacji. Zobacz [klasy WMI serwera SMS_Site](/sccm/develop/reference/core/servers/configure/sms_site-server-wmi-class).


-   Do czasu zaktualizowania wszystkich lokacji w ramach hierarchii do nowej wersji hierarchia działa w trybie wersji mieszanej. Aby uzyskać więcej informacji, zobacz [współdziałanie różnych wersji programu Configuration Manager](../../../core/plan-design/hierarchy/interoperability-between-different-versions.md).  


#### <a name="5-update-configuration-manager-consoles"></a>5. Aktualizacja konsol programu Configuration Manager  
Po centralnej lokacji administracyjnej lub lokacji głównej aktualizacje należy również zaktualizować każdą konsolę programu Configuration Manager łączy do tej lokacji. Monit o aktualizację konsoli zostanie wyświetlony:  

-   Po otwarciu konsoli

-   Po przejściu do nowego węzła w otwartej konsoli

Zaleca się natychmiastową instalację aktualizacji.  

Po zakończeniu aktualizacji konsoli możesz sprawdzić, czy wersje konsoli i lokacji są poprawne. Przejdź do **System Center Configuration Manager** w lewym górnym rogu konsoli.  


###  <a name="bkmk_toptier"></a> Aby rozpocząć instalację aktualizacji w lokacji najwyższego poziomu  
W lokacji najwyższego poziomu w hierarchii, w konsoli programu Configuration Manager przejdź do **administracji** > **aktualizacje i obsługa**, wybierz pozycję **dostępne** aktualizacji, a następnie kliknij przycisk **Instaluj pakiet aktualizacji**.  


###  <a name="bkmk_secondary"></a> Aby rozpocząć instalację aktualizacji w lokacji dodatkowej  
Po aktualizacji lokacji głównej nadrzędnej lokacji dodatkowej należy zaktualizować lokację dodatkową z poziomu konsoli programu Configuration Manager. W tym celu należy użyć **Kreatora uaktualniania lokacji dodatkowej**.  

1.  W konsoli programu Configuration Manager przejdź do **administracji** > **konfiguracja lokacji** > **witryny**, wybierz witryny, którą chcesz zaktualizować, a następnie na karcie Strona główna karcie w **lokacji** grupy, wybierz **uaktualnienia**.  

2.  Kliknij przycisk **Tak** , aby rozpocząć aktualizację lokacji dodatkowej.  

Aby monitorować instalację aktualizacji w lokacji dodatkowej, wybierz serwer lokacji dodatkowej. Następnie na **Home** karcie **lokacji** grupy, wybierz **Pokaż stan instalacji**. Możesz również dodać kolumnę **Wersja** do wyświetlanej konsoli, co umożliwia wyświetlanie wersji poszczególnych lokacji dodatkowych.  

Po lokacji dodatkowej pomyślnie aktualizacji, jeśli stan w konsoli nie powoduje odświeżenia lub sugeruje aktualizacji nie powiodła się, należy użyć **ponów próbę instalacji** opcji. Ta opcja nie ponownie aktualizację lokacji dodatkowej, która pomyślnie zainstalować aktualizację, ale wymusza konsolę, aby zaktualizować stan.


### <a name="post-installation-tasks"></a>Zadań po instalacji
Podczas instalowania aktualizacji w lokacji, istnieje kilka zadań, których nie można uruchomić dopiero po ukończeniu instalacji na serwerze lokacji. Poniżej przedstawiono listę zadań po instalacji, które są krytyczne dla operacji lokacji i hierarchii. Ponieważ są one krytycznych, są one aktywnie monitorowany. Dodatkowe zadania, które nie są monitorowane bezpośrednio zawierać ponownej instalacji ról systemu lokacji. Zaznacz, aby wyświetlić stan zadań instalacji po krytyczne **po instalacji** zadań podczas monitorowania instalacji aktualizacji dla lokacji.

Nie wszystkie zadania wykonaj natychmiast. Niektóre zadania nie uruchamiaj w każdej lokacji zakończenia instalacji aktualizacji. Nowe funkcje, które mogą wymagać mogą poczekać do wykonania tych zadań. Włączenie nowe funkcje nie uruchomić, dopóki wszystkie lokacje ukończenie instalacji aktualizacji, aby nowe funkcje mogą nie być widoczne przez pewien czas.

Zadań po instalacji obejmują:

-   **Instalowanie usługi SMS_EXECUTIVE**
  -   Krytyczne usługa, która działa na serwerze lokacji.
  -   Ponowna instalacja tej usługi powinno zakończyć się szybko.


-   **Instaluje składnik SMS_DATABASE_NOTIFICATION_MONITOR**
  -   Wątek składnika krytyczne witryny usługi SMS_EXECUTIVE.
  -   Ponowna instalacja tej usługi powinno zakończyć się szybko.


-   **Instaluje składnik SMS_HIERARCHY_MANAGER**
  -   Składnik krytyczne lokacji, który działa na serwerze lokacji.
  -   Segment odpowiedzialny za ponownie zainstalować role systemu lokacji na serwerach systemu lokacji. Stan do ponownej instalacji roli systemu lokacji poszczególnych nie są wyświetlane.
  -   Ponowna instalacja tej usługi powinno zakończyć się szybko.


-   **Instaluje składnik SMS_REPLICATION_CONFIGURATION_MONITOR**
  -   Składnik krytyczne lokacji, który działa na serwerze lokacji.
  -   Ponowna instalacja tej usługi powinno zakończyć się szybko.


-   **Instaluje składnik SMS_POLICY_PROVIDER**
  -   Składnik krytyczne lokacji, który działa tylko w lokacjach głównych.
  -   Ponowna instalacja tej usługi powinno zakończyć się szybko.


-   **Monitorowanie inicjowania replikacji**   
  -   To zadanie są wyświetlane tylko w centralnej lokacji administracyjnej i w podrzędnych lokacjach głównych.
  -   W zależności od SMS_REPLICATION_CONFIGURATION_MONITOR.
  -   Powinno zakończyć się szybko.


-   **Aktualizowanie pakietu przedprodukcyjnego klienta programu Configuration Manager**    
  -   To zadanie wyświetla nawet wtedy, gdy klienta przedprodukcyjnego (nazywanych również wdrażania pilotażowego klienta) nie jest włączony do użytku.
  -   Nie zaczyna się do momentu zakończenia wszystkich lokacji w hierarchii, instalowania aktualizacji.


-   **Aktualizowanie folderu klienta na serwerze lokacji**
  -   To zadanie nie jest wyświetlany w przypadku korzystania z klienta w środowisku przedprodukcyjnym.  
  -   Powinno zakończyć się szybko.


-   **Aktualizowanie pakietu klienta programu Configuration Manager**
  -   To zadanie nie jest wyświetlany w przypadku korzystania z klienta w środowisku przedprodukcyjnym.  
  -   Zakończy się tylko wtedy, gdy we wszystkich lokacjach zainstalować aktualizację.  


-   **Włączanie funkcji**
  -   To zadanie jest wyświetlany tylko w lokacji najwyższego poziomu w hierarchii.
  -   Nie zaczyna się do momentu zakończenia wszystkich lokacji w hierarchii, instalowania aktualizacji.
  -   Poszczególne funkcje nie są wyświetlane.



##  <a name="bkmk_retry"></a> Ponawianie nieudanej instalacji aktualizacji  
W przypadku niepowodzenia instalacji aktualizacji sprawdź informacje zwrotne w konsoli, by określić rozwiązania ostrzeżeń i błędów. Możesz również wyświetlić dziennik ConfigMgrPrereq.log na serwerze lokacji, aby uzyskać dodatkowe informacje. Przed ponowieniem instalacji aktualizacji należy naprawić błędy, a powinno rozwiązać ostrzeżenia.  

> [!TIP]  
> Jeśli aktualizacja ma problemów z pobieraniem lub replikację, można użyć [aktualizacji zresetuj narzędzie](/sccm/core/servers/manage/update-reset-tool). 

Gdy wszystko będzie gotowe do ponowienia instalacji aktualizacji, wybierz aktualizację, nie powiodło się, a następnie wybierz odpowiednią opcję. Zachowania ponawiania instalacji aktualizacji zależy od węzła, gdzie uruchomić retry wraz z opcją ponownych prób, używanej.  

#### <a name="retry-installation-for-the-hierarchy"></a>Ponów próbę instalacji hierarchii
Możesz ponowić instalację aktualizacji całej hierarchii, jeśli aktualizacja ta ma jeden z następujących stanów:  

  -   Sprawdzanie wymagań wstępnych Zakończono pomyślnie z co najmniej jedno ostrzeżenie, a nie ustawiono opcji ignorowania ostrzeżeń dotyczących sprawdzania wymagań wstępnych w Kreatorze aktualizacji. (Wartość aktualizacji dla **Ignoruj ostrzeżenia dotyczące wymagań wstępnych** w **aktualizacje i obsługa** węzeł jest **nr**.)   
  -   Niepowodzenie wymagań wstępnych    
  -   Niepowodzenie instalacji
  -   Replikacja zawartości do lokacji nie powiodła się   

Przejdź do **administracji** > **aktualizacje i obsługa**, wybierz aktualizację, a następnie wybierz jedną z następujących opcji:  

  -   **Spróbuj ponownie** — po uruchomieniu **ponów** z tego węzła, uruchamia ponownie instalacji aktualizacji i automatycznie ignoruje ostrzeżenia dotyczące wymagań wstępnych. Zawartość aktualizacji również ponownie replikuje Jeśli replikacja wcześniej nie powiodła się.
  - **Ignoruj ostrzeżenia dotyczące wymagań wstępnych** — w przypadku instalacji aktualizacji zatrzymuje ze względu na ostrzeżenie, można wybrać **Ignoruj ostrzeżenia dotyczące wymagań wstępnych**. Ta akcja umożliwia kontynuowanie instalacji aktualizacji (po kilku minutach) z użyciem opcji ignorowania ostrzeżeń dotyczących wymagań wstępnych.   

#### <a name="retry-installation-for-the-site"></a>Ponów próbę instalacji lokacji  
 Możesz ponowić instalację aktualizacji w określonej lokacji, jeśli aktualizacja ma jeden z następujących stanów:  

  -   Sprawdzanie wymagań wstępnych Zakończono pomyślnie z co najmniej jedno ostrzeżenie, a nie ustawiono opcji ignorowania ostrzeżeń sprawdzania wymagań wstępnych w Kreatorze aktualizacji. (Wartość aktualizacji dla **Ignoruj ostrzeżenia dotyczące wymagań wstępnych** w węźle aktualizacje i obsługa jest **nr**.)  
  -   Niepowodzenie wymagań wstępnych    
  -   Niepowodzenie instalacji    

Przejdź do **monitorowanie** > **omówienie** > **stan obsługi lokacji**, wybierz aktualizację, a następnie kliknij jedną z następujących opcji:

  - **Spróbuj ponownie** — po uruchomieniu **ponów** z tego węzła, ponowne uruchomienie instalacji aktualizacji w tylko w tej lokacji. W przeciwieństwie do uruchamiania **ponów** z **aktualizacje i obsługa** węzła, ta ponowna próba nie ignoruje ostrzeżenia dotyczące wymagań wstępnych.
  - **Ignoruj ostrzeżenia dotyczące wymagań wstępnych** -aktualizacji instalacji zatrzymuje ze względu na ostrzeżenie, należy kliknąć **Ignoruj ostrzeżenia dotyczące wymagań wstępnych**. Ta akcja umożliwia kontynuowanie instalacji aktualizacji (po kilku minutach) z użyciem opcji ignorowania ostrzeżeń dotyczących wymagań wstępnych.



##  <a name="bkmk_after"></a> Po zainstalowaniu aktualizacji lokacji  
Poniższa lista kontrolna umożliwia wykonać typowe zadania i konfiguracji wprowadzane po aktualizacji lokacji.   

**Upewnij się, że lokacja lokacja replikacji jest aktywna:** W konsoli programu Configuration Manager przejdź do następujących lokacji, aby wyświetlić stan i upewnij się, że replikacja jest aktywna:  

-   **Monitorowanie** > **Przegląd** > **Hierarchia lokacji**  

-   **Monitorowanie** > **Przegląd** > **Replikacja bazy danych**  

Aby uzyskać więcej informacji, zobacz [Monitorowanie infrastruktury hierarchii i replikacji](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md) i [o analizator łącza replikacji](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_RLA).  

 **Upewnij się, że serwery lokacji i serwery zdalnego systemu lokacji ponownym uruchomieniu (Jeśli to konieczne):** Sprawdź infrastrukturę lokacji i upewnij się, że odpowiednie serwery lokacji i serwery systemu lokacji przebiegło pomyślnie. Zazwyczaj serwerów lokacji ponownie tylko wtedy, gdy program Configuration Manager instaluje .NET jako wymaganie wstępne roli systemu lokacji.  

 **Zaktualizuj autonomiczne konsole programu Configuration Manager:** Upewnij się, że wszystkie zdalne konsole programu Configuration Manager są aktualizacji do tej samej wersji. Monit o aktualizację konsoli jest wyświetlany w następujących sytuacjach:  

-   Powoduje przejście do nowego węzła w konsoli.  

-   Możesz otworzyć konsolę.

**Skonfiguruj ponownie repliki bazy danych dla punktów zarządzania w lokacjach głównych:** W przypadku używania replik bazy danych dla punktów zarządzania w lokacjach głównych, należy odinstalować repliki bazy danych przed aktualizacją lokacji. Po aktualizacji lokacji głównej skonfiguruj ponownie repliki bazy danych dla punktów zarządzania. Aby uzyskać więcej informacji, zobacz [bazy danych repliki dla punktów zarządzania](../../../core/servers/deploy/configure/database-replicas-for-management-points.md).  

**Skonfiguruj ponownie wszystkie wyłączone przed aktualizacją zadania konserwacji bazy danych:** W przypadku wyłączenia bazy danych [zadania konserwacji](../../../core/servers/manage/maintenance-tasks.md) w lokacji przed zainstalowaniem aktualizacji, skonfiguruj ponownie te zadania w lokacji. Użyj tych samych ustawień, które obowiązywały przed aktualizacją.  

**Uaktualnij klientów:** Aby uzyskać informacje, zobacz [uaktualnianie klientów komputerów z systemem Windows](../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md).  

**Dodatkowe konfiguracje:** Przejrzyj zmiany wprowadzone przed rozpoczęciem aktualizacji, a następnie przywróć te konfiguracje lokacji i hierarchii.  



##  <a name="bkmk_options"></a> Włącz funkcje opcjonalne aktualizacji  
Gdy aktualizacja zawiera jeden lub więcej funkcji opcjonalnych, masz możliwość włączenia tych funkcji w hierarchii. Można włączyć funkcji podczas instalacji aktualizacji lub może wrócić do konsoli później, aby włączyć funkcje opcjonalne.

Aby wyświetlić dostępne funkcje i ich stan, w konsoli przejdź do **administracji** > **aktualizacje i obsługa** > **funkcji**.

Jeśli funkcja nie jest opcjonalne, jest instalowana automatycznie i nie ma **funkcje** węzła.  


Po włączeniu nowych funkcji i funkcji wersji wstępnej Menedżera hierarchii programu Configuration Manager (HMAN) musi przetworzyć zmiany, zanim ta funkcja stanie się dostępny. Przetwarzanie zmiana jest często natychmiastowe, ale może potrwać do 30 minut, w zależności od HMAN cykl przetwarzania. Po przetworzeniu zmiana wymaga ponownego uruchomienia konsoli można wyświetlić nowy interfejs użytkownika związane z tej funkcji.



##  <a name="bkmk_prerelease"></a> Używanie funkcji w wersjach wstępnych z poziomu aktualizacji
Funkcje wersji wstępnej znajdują się w bieżącej gałęzi do wczesnego testowania w środowisku produkcyjnym. Można użyć tych funkcji w środowisku produkcyjnym, ale ich nie są uznawane za produkcji gotowe. Dowiedz się więcej o [funkcje wersji wstępnej](/sccm/core/servers/manage/pre-release-features), łącznie ze sposobem je włączyć w danym środowisku.             



## <a name="frequently-asked-questions"></a>Często zadawane pytania

###  <a name="bkmk_faq"></a> Dlaczego nie widzę niektórych aktualizacji w mojej konsoli?  
 Jeśli nie możesz znaleźć w konsoli konkretnej aktualizacji po pomyślnej synchronizacji z usługą w chmurze firmy Microsoft, takie zachowanie może być spowodowane jedną z następujących powodów:  

-   Aktualizacja wymaga konfiguracji, której nie używa dana infrastruktura lub też bieżąca wersja produktu nie spełnia wymagań wstępnych dotyczących pobierania aktualizacji.  

     Jeśli uważasz, że masz wymagane konfiguracje i wymagania wstępne brakującej aktualizacji, upewnij się, że punkt połączenia usługi jest w trybie online. Następnie należy użyć **Sprawdź aktualizacje** opcji **aktualizacje i obsługa** węzeł, aby wymusić sprawdzenie. Jeśli jesteś w trybie offline, musisz użyć narzędzia połączenia usługi, aby przeprowadzić ręczną synchronizację z usługą w chmurze.  

-   Twoje konto nie ma uprawnień poprawne administracji opartej na rolach, aby wyświetlać aktualizacje w konsoli programu Configuration Manager.

    Zobacz sekcję [Uprawnienia do zarządzania aktualizacjami](../../../core/servers/manage/install-in-console-updates.md#assign-permissions-to-view-and-manage-updates-and-features) w tym temacie, aby uzyskać informacje o uprawnieniach wymaganych do wyświetlania aktualizacji i włączania funkcji z poziomu konsoli.

