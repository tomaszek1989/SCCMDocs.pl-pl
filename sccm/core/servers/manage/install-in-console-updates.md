---
title: Aktualizacje w konsoli | Dokumentacja firmy Microsoft
description: "System Center Configuration Manager synchronizuje się z usługą firmy Microsoft w chmurze do pobierania aktualizacji, które można zainstalować w konsoli."
ms.custom: na
ms.date: 09/14/2017
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: c14a3607-253b-41fb-8381-ae2d534a9022
caps.latest.revision: "36"
author: Brenduns
ms.author: brenduns
manager: angrobe
ms.openlocfilehash: 5302b5712e33c753d0193a32498bc02a2241428c
ms.sourcegitcommit: 474e6ddbaaeac4ba17d8172321e08deeb0140d0a
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2017
---
# <a name="install-in-console-updates-for-system-center-configuration-manager"></a>Instalacja aktualizacji w konsoli programu System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Synchronizuje System Center Configuration Manager z usługą w chmurze firmy Microsoft do pobierania aktualizacji. Następnie można zainstalować te aktualizacje z poziomu konsoli programu Configuration Manager.

## <a name="get-available-updates"></a>Uzyskiwanie dostępnych aktualizacji
Pobierane i udostępniane hierarchii użytkownika są tylko aktualizacje mające zastosowanie do danej infrastruktury i wersji. Synchronizacja ta może być automatycznie lub ręcznie, w zależności od sposobu skonfigurowania punktu połączenia usługi dla hierarchii:

-   W **trybie online**punkt połączenia usługi automatycznie łączy się z usługą firmy Microsoft w chmurze i pobiera odpowiednie aktualizacje.  

     Domyślnie program Configuration Manager sprawdza dostępność aktualizacji co 24 godziny. Możesz również sprawdzić aktualizacje od razu, wybierając **Sprawdź aktualizacje** w **administracji** > **aktualizacje i obsługa** węzła konsoli programu Configuration Manager. (Przed wersji 1702 ten węzeł został w obszarze **administracji** > **usługi w chmurze**.)

-   W **w trybie offline**, punkt połączenia usługi nie połączyć z usługą w chmurze firmy Microsoft. Aby pobierać i importować dostępne aktualizacje, [użyć narzędzia połączenia z usługą System Center Configuration Manager](../../../core/servers/manage/use-the-service-connection-tool.md).  

> [!NOTE]  
>   Poprawki poza pasmem można zaimportować do konsoli. Aby to zrobić, użyj [narzędzia rejestracji aktualizacji](/sccm/core/servers/manage/use-the-update-registration-tool-to-import-hotfixes). Niniejsze poprawki poza pasmem uzupełniają aktualizacje, które wystąpiły podczas synchronizacji z usługą Microsoft Cloud.


Po aktualizacji synchronizacji, można wyświetlić je w konsoli programu Configuration Manager, przechodząc do **administracji** > **aktualizacje i obsługa** węzła:  

-   Aktualizacje niezainstalowane są wyświetlane jako **Dostępne**.

-   Aktualizacje zainstalowane są wyświetlane jako **Zainstalowane**.  Jest wyświetlana tylko ostatnią zainstalowaną aktualizację. Możesz wybrać **historii** na Wstążce, aby wyświetlić wcześniej zainstalowane aktualizacje.



Przed skonfigurowaniem punktu połączenia usługi, zrozumieć i zaplanuj jego dodatkowe funkcje. Następujące zastosowania mogą mieć wpływ na sposób konfigurowania tej roli systemu lokacji:  

-   Punkt połączenia z usługą służy do przekazywania informacji o użyciu lokacji. Informacje te pomagają usłudze firmy Microsoft w chmurze zidentyfikować aktualizacje dostępne dla bieżącej wersji infrastruktury. Aby uzyskać więcej informacji, zobacz [diagnostycznych i danych użycia programu System Center Configuration Manager](../../../core/plan-design/diagnostics/diagnostics-and-usage-data.md).  

-   Punkt połączenia usługi jest używany do zarządzania urządzeniami w usłudze Microsoft Intune i przy użyciu programu Configuration Manager na lokalnego zarządzania urządzeniami przenośnymi. Aby uzyskać więcej informacji, zobacz [hybrydowego zarządzania urządzeniami przenośnymi (MDM) z programu System Center Configuration Manager i Microsoft Intune](../../../mdm/understand/hybrid-mobile-device-management.md).  

Aby lepiej zrozumieć, co się stanie, jeśli aktualizacje zostaną pobrane, zobacz:  

-   [Schemat blokowy — pobieranie aktualizacji programu System Center Configuration Manager](../../../core/servers/manage/download-updates-flowchart.md)

-   [Schemat blokowy — replikacji aktualizacji dla programu System Center Configuration Manager](../../../core/servers/manage/update-replication-flowchart.md)  

## <a name="assign-permissions-to-view-and-manage-updates-and-features"></a>Przypisywanie uprawnień do wyświetlania i zarządzania nimi, aktualizacje i funkcje
Aby wyświetlać aktualizacje w konsoli, użytkownik musi mieć rolę zabezpieczeń administracji opartej na rolach, który zawiera klasę zabezpieczeń **pakietów aktualizacji**. Ta klasa udziela dostępu do wyświetlania i zarządzania aktualizacjami w konsoli programu Configuration Manager.    

**Informacje o klasie Pakiety aktualizacji:**  
Domyślnie klasa **Pakiety aktualizacji** (SMS_CM_Updatepackages) jest częścią następujących wbudowanych ról zabezpieczeń z następującymi uprawnieniami:
 -  **Administrator o pełnych uprawnieniach** z uprawnieniami **Modyfikacja** i **Odczyt** :
    -   Użytkownik z tej roli zabezpieczeń i dostępu do **wszystkie** zakres zabezpieczeń można wyświetlić i zainstalować aktualizacje. Użytkownika można również włączyć funkcje podczas instalacji i włączyć poszczególne funkcje, po zainstalowaniu tej aktualizacji.
    - Użytkownik z tej roli zabezpieczeń i dostępu do **domyślne** zakres zabezpieczeń można wyświetlić i zainstalować aktualizacje. Użytkownik może również włączyć funkcje podczas instalacji i wyświetlić funkcji po zainstalowaniu aktualizacji. Jednak ten użytkownik nie może włączyć funkcji po zainstalowaniu tej aktualizacji.

- **Analityk z uprawnieniami tylko do odczytu** z uprawnieniami **Odczyt** :
  -  Użytkownik z tej roli zabezpieczeń i dostępu do **domyślne** zakres można wyświetlić aktualizacje, ale nie można je zainstalować. Ten użytkownik może również wyświetlać funkcje po aktualizacja została zainstalowana, ale nie można włączyć je.

**Uprawnienia wymagane do aktualizacji i obsługi:**   
  - Użyj konta, któremu przypisano rolę zabezpieczeń zawierającą klasę **Pakiety aktualizacji** z uprawnieniami **Modyfikacja** i **Odczyt** .
  - Konto musi być przypisane do zakresu **Domyślne** .

**Uprawnienia, aby wyświetlić tylko aktualizacje**:
  - Użyj konta, któremu przypisano rolę zabezpieczeń zawierającą klasę **Pakiety aktualizacji** tylko z uprawnieniem **Odczyt** .
  - Konto musi być przypisane do zakresu **Domyślne** .

**Uprawnienia wymagane do włączenia funkcji po zainstalowaniu aktualizacji:**
  -  Użyj konta, któremu przypisano rolę zabezpieczeń zawierającą klasę **Pakiety aktualizacji** z uprawnieniami **Modyfikacja** i **Odczyt** .
  -  Konto musi być przypisane do zakresu **Wszystkie** .



##  <a name="bkmk_beforeinstall"></a> Przed zainstalowaniem aktualizacji w konsoli  
 Przejrzyj poniższe kroki przed zainstalowaniem aktualizacji z poziomu konsoli programu Configuration Manager.  

###  <a name="bkmk_step1"></a>Krok 1. Przejrzyj listę kontrolną aktualizacji  
Przejrzyj odpowiednią listę kontrolną aktualizacji czynności należy wykonać przed rozpoczęciem aktualizacji:

- Aktualizacja do 1606: Zobacz [Lista kontrolna dotycząca instalowania aktualizacji 1606](../../../core/servers/manage/checklist-for-installing-update-1606.md).  

- Aktualizacja do 1610 z obu 1606: Zobacz [Lista kontrolna dotycząca instalowania aktualizacji 1610](../../../core/servers/manage/checklist-for-installing-update-1610.md).  

- Aktualizacja do 1702 1606 lub 1610: Zobacz [Lista kontrolna dotycząca instalowania aktualizacji 1702](../../../core/servers/manage/checklist-for-installing-update-1702.md).

<!-- Removed as update guidance 6/6/2017. The Test DB Upgrade details are no longer recommended nor required. They live on in a new topic for customers who still want to use them. -->

###  <a name="step-2-run-the-prerequisite-checker-before-installing-an-update"></a>Krok 2. Uruchom narzędzie sprawdzania wymagań wstępnych przed instalacją aktualizacji  
Przed zainstalowaniem aktualizacji warto rozważyć uruchomienie narzędzie sprawdzania wymagań wstępnych dla tej aktualizacji. W przypadku uruchomienia sprawdzania wymagań wstępnych przed instalacją aktualizacji:  

-   Pliki aktualizacji są replikowane do innych lokacji przed zainstalowaniem aktualizacji.  

-   Sprawdzanie wymagań wstępnych automatycznie uruchomiony ponownie w przypadku zainstalowania aktualizacji.  

> [!NOTE]   
> Po uruchomieniu sprawdzania wymagań wstępnych i następnie wyświetlić stan, **instalacji** fazy wydaje się być aktywne, jednak aktualizacja nie jest w rzeczywistości zainstalowano. Do sprawdzania wymagań wstępnych, proces aktualizacji wyodrębnia pakiet z biblioteki zawartości i umieszczenie go do folderu przemieszczania, gdzie można uzyskać dostęp do bieżącej Sprawdzanie wymagań wstępnych.  Ten sam proces jest uruchamiana po zainstalowaniu aktualizacji. Z tego powodu instalacja jest pokazywana jako "W toku". Tylko *pakiet aktualizacji wyodrębnij* kroku jest wyświetlany w kategorii instalacji.  

Później po zainstalowaniu aktualizacji można skonfigurować aktualizacji do ignorowania ostrzeżeń sprawdzania wymagań wstępnych.  

#### <a name="to-run-the-prerequisite-checker-before-installing-an-update"></a>Aby uruchomić narzędzie sprawdzania wymagań wstępnych przed instalacją aktualizacji  

1.  W konsoli programu Configuration Manager, przejdź do **administracji** > **aktualizacje i obsługa**.   

2.  Kliknij prawym przyciskiem myszy na pakiet aktualizacji, który chcesz uruchomić sprawdzanie wymagań wstępnych.  

3.  Wybierz opcję **Uruchom sprawdzenie wymagań wstępnych**.  

     Po uruchomieniu sprawdzania wymagań wstępnych zawartość aktualizacji jest replikowana do lokacji podrzędnych.  Możesz wyświetlić plik distmgr.log w lokacji serwera, aby upewnić się, że zawartość replikuje pomyślnie.  

4.  Aby wyświetlić wyniki sprawdzania, w konsoli programu Configuration Manager przejdź do **monitorowanie** > **aktualizacji i obsługi stanu** i odszukaj stan wymagań wstępnych. Możesz również wyświetlić dziennik ConfigMgrPrereq.log na serwerze lokacji, aby uzyskać dodatkowe informacje.  



##  <a name="bkmk_install"></a> Instalacja aktualizacji w konsoli  
 Gdy wszystko będzie gotowe do zainstalowania aktualizacji z poziomu konsoli programu Configuration Manager można rozpoczynać się od lokacji najwyższego poziomu w hierarchii. Jest to centralna lokacja administracyjna lub autonomiczna lokacja główna.  

 Zaleca się zainstalowanie aktualizacji poza normalnymi godzinami pracy każdej lokacji zminimalizować wpływ na operacje biznesowe. Jest to spowodowane instalacji aktualizacji może obejmować akcje, takie jak ponowne zainstalowanie składników lokacji i ról systemu lokacji.  

-   Podrzędne lokacje główne rozpoczynają aktualizację automatycznie po zakończeniu instalacji aktualizacji przez centralną lokację administracyjną. To jest domyślna i zalecane procesu. Można jednak użyć [usługi systemu windows dla serwerów lokacji](/sccm/core/servers/manage/service-windows) do kontrolowania, kiedy w lokacji głównej instaluje aktualizacje.  

-   Ręcznie zaktualizować Lokacje dodatkowe przy użyciu konsoli programu Configuration Manager po zakończeniu aktualizacji lokacji głównej. Automatyczna aktualizacja serwerów lokacji dodatkowych nie jest obsługiwana.  

-   Użycie konsoli programu Configuration Manager po zaktualizowaniu lokacji wyświetlany jest monit o aktualizację konsoli.  

-  Po serwera lokacji pomyślnie ukończy instalację aktualizacji, automatycznie aktualizuje wszystkich odpowiednich ról systemu lokacji.  To ostrzeżenie tylko dla punktów dystrybucji. Podczas instalowania aktualizacji, wszystkie punkty dystrybucji nie ponownej instalacji i przejść do trybu offline, aby zaktualizować w tym samym czasie. Zamiast tego serwer lokacji używa witryny ustawienia dystrybucji zawartości do dystrybucji aktualizacji do podzbioru punktów dystrybucji w czasie. Wynik jest, że niektóre punkty dystrybucji Przejdź offline, aby zainstalować tę aktualizację. Punkty dystrybucji, który zaczęli nie można zaktualizować lub które zostały ukończone aktualizacji pozostają online i możliwość zapewnienia zawartości do klientów.


###  <a name="bkmk_overview"></a> Przegląd instalacji aktualizacji w konsoli  
**1. Po rozpoczęciu instalacji aktualizacji**  
Wyświetlany jest kreator aktualizacji z listą obszarów produktów, do których ma zastosowanie aktualizacja.  

-   Na stronie **Ogólne** kreatora można skonfigurować **Ostrzeżenia dotyczące wymagań wstępnych**.  
      -   Błędy wymagań wstępnych zawsze wstrzymują instalację aktualizacji. Napraw błędy, zanim mógł pomyślnie ponowić próbę instalacji aktualizacji. Aby uzyskać więcej informacji, zobacz [Ponawianie nieudanej instalacji aktualizacji](#bkmk_retry) .  

    -   Ostrzeżenia dotyczące wymagań wstępnych mogą również wstrzymać instalację aktualizacji. Napraw ostrzeżenia przed ponowieniem instalacji aktualizacji. Aby uzyskać więcej informacji, zobacz [ponawiania instalacji aktualizacji nie powiodło się](#bkmk_retry).  
    -   Opcja **Zignoruj wszelkie ostrzeżenia dotyczące sprawdzania wymagań wstępnych i zainstaluj tę aktualizację bez względu na niespełnione wymagania** określa warunek instalacji aktualizacji, który ignoruje ostrzeżenia dotyczące wymagań wstępnych. Dzięki temu w celu kontynuowania instalacji aktualizacji. Jeśli nie zaznaczysz tej opcji instalacji aktualizacji zatrzymuje w przypadku napotkania ostrzeżenia. Jeśli wcześniej nie przeprowadzono sprawdzania wymagań wstępnych i stałym ostrzeżenia dotyczące wymagań wstępnych dla lokacji, nie zaleca się użycie tej opcji.  

      W obu **administracji** i **monitorowanie** obszarów roboczych, aktualizacje i obsługa zawiera przycisk na Wstążce o nazwie **Ignoruj ostrzeżenia dotyczące wymagań wstępnych**. Ten przycisk jest dostępny, gdy pakiet aktualizacji nie powiedzie się ukończyć instalację z powodu ostrzeżenia dotyczące sprawdzania wymagań wstępnych. Na przykład zainstalować aktualizację bez użycia opcji ignorowania ostrzeżeń dotyczących wymagań wstępnych (z poziomu Kreatora aktualizacji). Instalacja aktualizacji zatrzymuje się ze stanem ostrzeżenia dotyczące wymagań wstępnych, ale żadne błędy. Później możesz **Ignoruj ostrzeżenia dotyczące wymagań wstępnych** na Wstążce, aby wyzwolić automatyczne kontynuacji tej instalacji aktualizacji, który następnie ignoruje ostrzeżenia dotyczące wymagań wstępnych. Tej opcji instalacji aktualizacji będzie automatycznie kontynuować działanie po kilku minutach.



-   Jeśli aktualizacja ma zastosowanie do klienta programu Configuration Manager, jest wyświetlana opcja przetestowania aktualizacji klienta na ograniczonym zestawie klientów. Aby uzyskać więcej informacji, zobacz [testowanie uaktualnień klienta w kolekcji przedprodukcyjnej w programie System Center Configuration Manager](../../../core/clients/manage/upgrade/test-client-upgrades.md).  

**2. Podczas instalacji aktualizacji**  
W ramach instalacji aktualizacji program Configuration Manager:  

-   Ponownie instaluje żadnych odpowiednich składników, takich jak role systemu lokacji lub konsoli programu Configuration Manager.  

-   Zarządza aktualizacjami klientów zgodnie z opcjami wprowadzone w przypadku wdrażania pilotażowego klienta oraz [automatycznych uaktualnień klienta](https://technet.microsoft.com/library/mt627885.aspx).  

-   Nie uruchomi ponownie serwery systemu lokacji jako część aktualizacji, chyba że w ramach wymagań wstępnych ról systemu lokacji instalowana jest platforma .NET.  

> [!TIP]  
>  Podczas instalowania aktualizacji programu Configuration Manager aktualizuje również dysku CD. Najnowszy folder. Ten folder jest używany podczas odzyskiwania lokacji.  

**3. Monitorowanie postępu aktualizacji podczas ich instalacji**  
Postęp można monitorować przy użyciu następujących elementów:  

-   W konsoli programu Configuration Manager: **Administracja** > **aktualizacje i obsługa** węzła. Ten węzeł wyświetla stan instalacji dla wszystkich pakietów aktualizacji.


-   W konsoli programu Configuration Manager: **Monitorowanie** > **omówienie** > **aktualizacji i obsługi stanu** węzła. Ten węzeł Wyświetla stan instalacji pakietu aktualizacji, które jest obecnie zainstalowane.  

    Instalacja pakietu aktualizacji jest podzielone na następujące etapy w celu ułatwienia monitorowania. Dla każdej fazy dodatkowe szczegóły zawierają który plik dziennika, aby wyświetlić więcej informacji:  
    -   **Pobierz** (Ta faza dotyczy tylko do lokacji najwyższego poziomu, w którym zainstalowano lokacji punktu połączenia usługi).   

    -   **Replikacja**   

    -   **Sprawdzanie wymagań wstępnych**   

    -   **Instalacja**    

    -   **Po zakończeniu instalacji** ([zadań po instalacji](#post-installation-tasks) są dostępne począwszy od wersji 1610.)  

-   Możesz wyświetlić **CMUpdate.log** w pliku  **&lt;Katalog_instalacyjny_programu_configmgr > \Logs**  

**4. Po zakończeniu instalacji aktualizacji**  
Po zakończeniu instalacji aktualizacji pierwszej lokacji:  

-   Podrzędne Lokacje główne instalują aktualizację automatycznie. Nie ma potrzeby wykonywania dalszych czynności.  

-   Lokacje dodatkowe należy zaktualizować ręcznie z poziomu konsoli programu Configuration Manager.
> [!TIP]
> Chociaż wersja lokacji dodatkowej nie zostanie wyświetlone w konsoli, za pomocą zestawu SDK programu Configuration Manager i potwierdzić wersja lokacji. Zobacz [klasy WMI serwera SMS_Site](https://technet.microsoft.com/library/hh442832(CMSDK.16).aspx).


-   Do czasu zaktualizowania wszystkich lokacji w ramach hierarchii do nowej wersji hierarchia działa w trybie wersji mieszanej. Aby uzyskać więcej informacji, zobacz [Współdziałanie różnych wersji programu System Center Configuration Manager](../../../core/plan-design/hierarchy/interoperability-between-different-versions.md).  

**5.   Aktualizacja konsol programu Configuration Manager**  
Po centralnej lokacji administracyjnej lub lokacji głównej aktualizacje należy również zaktualizować każdą konsolę programu Configuration Manager łączy do tej lokacji. Monit o aktualizację konsoli zostanie wyświetlony:  

-   Po otwarciu konsoli.  

-   Po przejściu do nowego węzła w otwartej konsoli.  

Zaleca się natychmiastową instalację aktualizacji.  

Po zakończeniu aktualizacji konsoli możesz sprawdzić, czy wersje konsoli i lokacji są poprawne. Przejdź do **System Center Configuration Manager** w lewym górnym rogu konsoli.  

###  <a name="bkmk_toptier"></a> Aby rozpocząć instalację aktualizacji w lokacji najwyższego poziomu  
W lokacji najwyższego poziomu w hierarchii, w konsoli programu Configuration Manager przejdź do **administracji** > **aktualizacje i obsługa**, wybierz pozycję **dostępne** aktualizacji, a następnie kliknij przycisk **Instaluj pakiet aktualizacji**.  

###  <a name="bkmk_secondary"></a> Aby rozpocząć instalację aktualizacji w lokacji dodatkowej  
Po aktualizacji lokacji głównej nadrzędnej lokacji dodatkowej należy zaktualizować lokację dodatkową z poziomu konsoli programu Configuration Manager.  W tym celu należy użyć **Kreatora uaktualniania lokacji dodatkowej**.  

1.  W konsoli programu Configuration Manager przejdź do **administracji** > **konfiguracja lokacji** > **witryny**, wybierz witryny, którą chcesz zaktualizować, a następnie na karcie Strona główna karcie w **lokacji** grupy, wybierz **uaktualnienia**.  

2.  Kliknij przycisk **Tak** , aby rozpocząć aktualizację lokacji dodatkowej.  

Aby monitorować instalację aktualizacji w lokacji dodatkowej, wybierz serwer lokacji dodatkowej. Następnie na **Home** karcie **lokacji** grupy, wybierz **Pokaż stan instalacji**. Możesz również dodać kolumnę **Wersja** do wyświetlanej konsoli, co umożliwia wyświetlanie wersji poszczególnych lokacji dodatkowych.  

Po lokacji dodatkowej pomyślnie aktualizacji, jeśli stan w konsoli nie powoduje odświeżenia lub sugeruje aktualizacji nie powiodła się, należy użyć **ponów próbę instalacji** opcji. Ta opcja nie ponownie aktualizację lokacji dodatkowej, która pomyślnie zainstalować aktualizację, ale wymusza konsolę, aby zaktualizować stan.

### <a name="post-installation-tasks"></a>Zadań po instalacji
Począwszy od wersji 1610, można wyświetlić informacji dotyczących zadań po instalacji.

Podczas instalowania aktualizacji w lokacji, istnieje kilka zadań, których nie można uruchomić dopiero po ukończeniu instalacji na serwerze lokacji. Poniżej przedstawiono listę zadań po instalacji, które są krytyczne dla operacji lokacji i hierarchii. Ponieważ są one krytycznych, są one aktywnie monitorowany. Dodatkowe zadania, które nie są monitorowane bezpośrednio zawierać ponownej instalacji ról systemu lokacji. Zaznacz, aby wyświetlić stan zadań instalacji po krytyczne **po instalacji** zadań podczas monitorowania instalacji aktualizacji dla lokacji.

Nie wszystkie zadania wykonaj natychmiast. Niektóre zadania nie są uruchamiane w każdej lokacji zakończenia instalacji aktualizacji. W związku z tym nowe funkcje, które mogą wymagać mogą poczekać do wykonania tych zadań. Na przykład ponieważ włączenie nowych funkcji nie zostanie uruchomiony, dopóki wszystkie lokacje ukończenie instalacji aktualizacji, nowe funkcje mogą nie być widoczne przez pewien czas.

Zadań po instalacji obejmują:

-   **Instalowanie usługi SMS_EXECUTIVE**
  -   Krytyczne usługa, która działa na serwerze lokacji.
  -   Ponowna instalacja tej usługi powinno zakończyć się szybko.


-   **Instaluje składnik SMS_DATABASE_NOTIFICATION_MONITOR**
  -   Wątek składnika krytyczne witryny usługi SMS_EXECUTIVE.
  -   Ponowna instalacja tej usługi powinno zakończyć się szybko.


-   **Instaluje składnik SMS_HIERARCHY_MANAGER**
  -   Składnik krytyczne lokacji, który działa na serwerze lokacji.
  -   Segment odpowiedzialny za ponownie zainstalować role systemu lokacji na serwerach systemu lokacji.  Stan do ponownej instalacji roli systemu lokacji poszczególnych nie są wyświetlane.
  -   Ponowna instalacja tej usługi powinno zakończyć się szybko.


-   **Instaluje składnik SMS_REPLICATION_CONFIGURATION_MONITOR**
  -   Składnik krytyczne lokacji, który działa na serwerze lokacji.
  -   Ponowna instalacja tej usługi powinno zakończyć się szybko.


-   **Instaluje składnik SMS_POLICY_PROVIDER**
  -   Składnik krytyczne lokacji, który działa tylko w lokacjach głównych.
  -   Ponowna instalacja tej usługi powinno zakończyć się szybko.


-   **Monitorowanie inicjowania replikacji**   
  -   Spowoduje to wyświetlenie w centralnej lokacji administracyjnej i podrzędne Lokacje główne.
  -   W zależności od SMS_REPLICATION_CONFIGURATION_MONITOR.
  -   Powinno zakończyć się szybko.


-   **Aktualizowanie pakietu przedprodukcyjnego klienta programu Configuration Manager**    
  -   Spowoduje to wyświetlenie, nawet gdy klient przedprodukcyjnego (nazywanych również wdrażania pilotażowego klienta) nie jest włączony do użytku.
  -   Nie można uruchomić do momentu zakończenia wszystkich lokacji w hierarchii, instalowania aktualizacji.


-   **Aktualizowanie folderu klienta na serwerze lokacji**
  -   To nie jest wyświetlany, jeśli używasz klienta w środowisku przedprodukcyjnym.  
  -   Powinno zakończyć się szybko.


-   **Aktualizowanie pakietu klienta programu Configuration Manager**
  -   To nie jest wyświetlany, jeśli używasz klienta w środowisku przedprodukcyjnym.  
  -   Zakończy się tylko wtedy, gdy we wszystkich lokacjach zainstalować aktualizację.  


-   **Włączanie funkcji**
  -   Spowoduje to wyświetlenie tylko w lokacji najwyższego poziomu w hierarchii.
  -   Nie można uruchomić do momentu zakończenia wszystkich lokacji w hierarchii, instalowania aktualizacji.
  -   Poszczególne funkcje nie są wyświetlane.


##  <a name="bkmk_retry"></a> Ponawianie nieudanej instalacji aktualizacji  
W przypadku niepowodzenia aktualizacji do zainstalowania, przejrzyj opinii w konsoli, by określić rozwiązania ostrzeżeń i błędów. Możesz również wyświetlić dziennik ConfigMgrPrereq.log na serwerze lokacji, aby uzyskać dodatkowe informacje. Przed ponowieniem instalacji aktualizacji należy naprawić błędy, a powinno rozwiązać ostrzeżenia.  

> [!TIP]  
> Jeśli aktualizacja ma problemów z pobieraniem lub replikację, można użyć [aktualizacji zresetuj narzędzie](/sccm/core/servers/manage/update-reset-tool). To narzędzie jest dostępne z lokacji, na których jest uruchomiona wersja 1706 lub nowszego.

Gdy wszystko będzie gotowe do ponowienia instalacji aktualizacji, wybierz aktualizację, nie powiodło się, a następnie wybierz odpowiednią opcję. Zachowania ponawiania instalacji aktualizacji zależy od węzła, gdzie uruchomić retry wraz z opcją ponownych prób, używanej.  

1.  **Ponów próbę instalacji hierarchii:**  
Możesz ponowić instalację aktualizacji całej hierarchii, jeśli aktualizacja ta ma jeden z następujących stanów:  

    -   Sprawdzanie wymagań wstępnych Zakończono pomyślnie z co najmniej jedno ostrzeżenie, a nie ustawiono opcji ignorowania ostrzeżeń dotyczących sprawdzania wymagań wstępnych w Kreatorze aktualizacji. (Wartość aktualizacji dla **Ignoruj ostrzeżenia dotyczące wymagań wstępnych** w **aktualizacje i obsługa** węzeł jest **nr**.)   
    -   Niepowodzenie wymagań wstępnych    
    -   Niepowodzenie instalacji
    -   Replikacja zawartości do lokacji nie powiodła się   

    Przejdź do **administracji** > **aktualizacje i obsługa**, wybierz aktualizację, a następnie wybierz jedną z następujących opcji:  

    -   **Spróbuj ponownie** — po uruchomieniu **ponów** z tego węzła, uruchamia ponownie instalacji aktualizacji i automatycznie ignoruje ostrzeżenia dotyczące wymagań wstępnych. Zawartość aktualizacji również ponownie replikuje Jeśli replikacja wcześniej nie powiodła się.
    - **Ignoruj ostrzeżenia dotyczące wymagań wstępnych** — począwszy od wersji 1606, zatrzymuje z powodu Ostrzeżenie instalacji aktualizacji, można wybrać **Ignoruj ostrzeżenia dotyczące wymagań wstępnych**. Ta akcja umożliwia kontynuowanie instalacji aktualizacji (po kilku minutach) z użyciem opcji ignorowania ostrzeżeń dotyczących wymagań wstępnych.   

2.  **Ponów próbę instalacji lokacji:**  
 Możesz ponowić instalację aktualizacji w określonej lokacji, jeśli aktualizacja ma jeden z następujących stanów:  

    -   Sprawdzanie wymagań wstępnych Zakończono pomyślnie z co najmniej jedno ostrzeżenie, a nie ustawiono opcji ignorowania ostrzeżeń sprawdzania wymagań wstępnych w Kreatorze aktualizacji. (Wartość aktualizacji dla **Ignoruj ostrzeżenia dotyczące wymagań wstępnych** w węźle aktualizacje i obsługa jest **nr**.)  
    -   Niepowodzenie wymagań wstępnych    
    -   Niepowodzenie instalacji    

    Przejdź do **monitorowanie** > **omówienie** > **stan obsługi lokacji**, wybierz aktualizację, a następnie kliknij jedną z następujących opcji:

       - **Spróbuj ponownie** — po uruchomieniu **ponów** z tego węzła, ponowne uruchomienie instalacji aktualizacji w tylko w tej lokacji. W przeciwieństwie do uruchamiania **ponów** z **aktualizacje i obsługa** węzła, ta ponowna próba nie ignoruje ostrzeżenia dotyczące wymagań wstępnych.
       -    **Ignoruj ostrzeżenia dotyczące wymagań wstępnych** — począwszy od wersji 1606, zatrzymuje z powodu Ostrzeżenie instalacji aktualizacji, należy kliknąć **Ignoruj ostrzeżenia dotyczące wymagań wstępnych**. Ta akcja umożliwia kontynuowanie instalacji aktualizacji (po kilku minutach) z użyciem opcji ignorowania ostrzeżeń dotyczących wymagań wstępnych.

##  <a name="bkmk_after"></a> Po zainstalowaniu aktualizacji lokacji  
Poniższa lista kontrolna umożliwia wykonać typowe zadania i konfiguracji wprowadzane po aktualizacji lokacji.   

**Upewnij się, że lokacja lokacja replikacji jest aktywna:** W konsoli programu Configuration Manager przejdź do następujących lokacji, aby wyświetlić stan i upewnij się, że replikacja jest aktywna:  

-   **Monitorowanie** > **Przegląd** > **Hierarchia lokacji**  

-   **Monitorowanie** > **Przegląd** > **Replikacja bazy danych**  

Aby uzyskać więcej informacji, zobacz [Monitorowanie infrastruktury hierarchii i replikacji w programie System Center Configuration Manager](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md) i [o analizator łącza replikacji](../../../core/servers/manage/monitor-hierarchy-and-replication-infrastructure.md#BKMK_RLA).  

 **Upewnij się, że serwery lokacji i serwery zdalnego systemu lokacji ponownym uruchomieniu (Jeśli to konieczne):** Sprawdź infrastrukturę lokacji i upewnij się, że odpowiednie serwery lokacji i serwery systemu lokacji przebiegło pomyślnie. Zazwyczaj serwerów lokacji ponownie tylko wtedy, gdy program Configuration Manager instaluje .NET jako wymaganie wstępne roli systemu lokacji.  

 **Zaktualizuj autonomiczne konsole programu Configuration Manager:** Upewnij się, że wszystkie zdalne konsole programu Configuration Manager są aktualizacji do tej samej wersji. Monit o aktualizację konsoli jest wyświetlany w następujących sytuacjach:  

-   Powoduje przejście do nowego węzła w konsoli.  

-   Możesz otworzyć konsolę.

**Skonfiguruj ponownie repliki bazy danych dla punktów zarządzania w lokacjach głównych:** W przypadku używania replik bazy danych dla punktów zarządzania w lokacjach głównych, należy odinstalować repliki bazy danych przed aktualizacją lokacji. Po aktualizacji lokacji głównej skonfiguruj ponownie repliki bazy danych dla punktów zarządzania. Aby uzyskać więcej informacji, zobacz [Repliki bazy danych dla punktów zarządzania programu System Center Configuration Manager](../../../core/servers/deploy/configure/database-replicas-for-management-points.md).  

**Skonfiguruj ponownie wszystkie wyłączone przed aktualizacją zadania konserwacji bazy danych:** W przypadku wyłączenia bazy danych [zadania konserwacji](../../../core/servers/manage/maintenance-tasks.md) w lokacji przed zainstalowaniem aktualizacji, skonfiguruj ponownie te zadania w lokacji. Użyj tych samych ustawień, które obowiązywały przed aktualizacją.  

**Uaktualnij klientów:** Aby uzyskać informacje, zobacz [uaktualnianie klientów komputerów z systemem Windows w programie System Center Configuration Manager](../../../core/clients/manage/upgrade/upgrade-clients-for-windows-computers.md).  

**Dodatkowe konfiguracje:** Przejrzyj zmiany wprowadzone przed rozpoczęciem aktualizacji, a następnie przywróć te konfiguracje lokacji i hierarchii.  

##  <a name="bkmk_options"></a> Włącz funkcje opcjonalne aktualizacji  
Gdy aktualizacja zawiera jeden lub więcej funkcji opcjonalnych, masz możliwość włączenia tych funkcji w hierarchii.  Można włączyć funkcji podczas instalacji aktualizacji lub później wrócić do konsoli i Włącz funkcje opcjonalne.

Aby wyświetlić dostępne funkcje i ich stan, w konsoli przejdź do **administracji** > **aktualizacje i obsługa** > **funkcji**.

Jeśli funkcja nie jest opcjonalne, jest instalowana automatycznie i nie ma **funkcje** węzła.  


Po włączeniu nowych funkcji i funkcji wersji wstępnej Menedżera hierarchii programu Configuration Manager (HMAN) musi przetworzyć zmiany, zanim ta funkcja stanie się dostępny. Przetwarzanie zmiana jest często natychmiastowe, ale może potrwać do 30 minut, w zależności od HMAN cykl przetwarzania. Po przetworzeniu zmiana wymaga ponownego uruchomienia konsoli można wyświetlić nowy interfejs użytkownika związane z tej funkcji.


##  <a name="bkmk_prerelease"></a> Używanie funkcji w wersjach wstępnych z poziomu aktualizacji
Funkcje wersji wstępnej znajdują się w bieżącej gałęzi do wczesnego testowania w środowisku produkcyjnym. Można użyć tych funkcji w środowisku produkcyjnym, ale ich nie są uznawane za produkcji gotowe. Dowiedz się więcej o [funkcje wersji wstępnej](/sccm/core/servers/manage/pre-release-features), łącznie ze sposobem je włączyć w danym środowisku.             


## <a name="known-issues"></a>Znane problemy

###  <a name="bkmk_faq"></a>Dlaczego nie widzę niektórych aktualizacji w mojej konsoli?  
 Jeśli nie możesz znaleźć w konsoli konkretnej aktualizacji po pomyślnej synchronizacji z usługą w chmurze firmy Microsoft, może to być spowodowane:  

-   Aktualizacja wymaga konfiguracji, której nie używa dana infrastruktura lub też bieżąca wersja produktu nie spełnia wymagań wstępnych dotyczących pobierania aktualizacji.  

     Jeśli uważasz, że masz wymagane konfiguracje i wymagania wstępne brakującej aktualizacji, upewnij się, że punkt połączenia usługi jest w trybie online. Następnie należy użyć **Sprawdź aktualizacje** opcji **aktualizacje i obsługa** węzeł, aby wymusić sprawdzenie.  Jeśli jesteś w trybie offline, musisz użyć narzędzia połączenia usługi, aby przeprowadzić ręczną synchronizację z usługą w chmurze.  

-   Twoje konto nie ma uprawnień poprawne administracji opartej na rolach, aby wyświetlać aktualizacje w konsoli programu Configuration Manager.

    Zobacz sekcję [Uprawnienia do zarządzania aktualizacjami](../../../core/servers/manage/install-in-console-updates.md#assign-permissions-to-view-and-manage-updates-and-features) w tym temacie, aby uzyskać informacje o uprawnieniach wymaganych do wyświetlania aktualizacji i włączania funkcji z poziomu konsoli.

### <a name="why-do-i-see-two-updates-for-version-1610"></a>Dlaczego widzę dwie aktualizacje dla wersji 1610?
Podczas wyświetlania aktualizacji w konsoli, można napotkać dwóch aktualizacji, aby zainstalować wersję 1610. Aktualizacje te mają różne dni. Zarówno są wyświetlane, gdy spełniony jest jeden z następujących warunków:   
-   Zainstalowana starsza wersja (na przykład 1606) po udostępnieniu wersji 1610

-   Hierarchii działa w wersji 1511 lub 1602 i nie zostały jeszcze można pobrać wersji 1606

Istnieją dwie wersje dla wersji 1610 ponieważ ta aktualizacja została wydana ponownie po niewielkimi zmianami do niektórych plików binarnych wprowadzono aktualizacji. Te zmiany nie wpływają na funkcji programu Configuration Manager lub aktualizacji.

Gdy zarówno aktualizacje są dostępne w konsoli, zaleca się zainstalowanie aktualizacji przy użyciu nowych danych. Jednak ponieważ obu aktualizacjach dostarczać te same funkcje, gdy użytkownik zainstalował już jeden z nich jest konieczne podjęcie dalszych kroków.
-   Jeśli wcześniej zainstalowano starszych aktualizacji, nie trzeba zainstalować aktualizację przy użyciu nowszych danych. Jednak po zainstalowaniu nowsza aktualizacja po zainstalowaniu pierwszej aktualizacji spowoduje zaktualizowanie użyciu plików binarnych. Brak dodatkowych zmian i nie są wymagane żadne dodatkowe działania ze strony użytkownika.

-   Jeśli wcześniej zainstalowano najnowszą aktualizację, a następnie zainstalować aktualizację przy użyciu starszych danych, jest potrzebne żadne dodatkowe działanie. Jest to spowodowane nowszych plików binarnych, nie jest już zainstalowany nie są zastępowane przez wartości binarne tej samej z oryginalnej aktualizacji.
