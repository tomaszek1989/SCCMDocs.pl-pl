---
title: Monitor replikacji
titleSuffix: Configuration Manager
description: "Dowiedz się, jak monitorować infrastrukturę i operacje w programie Configuration Manager za pomocą obszaru roboczego monitorowania w konsoli."
ms.custom: na
ms.date: 10/06/2016
ms.prod: configuration-manager
ms.reviewer: na
ms.suite: na
ms.technology: configmgr-other
ms.tgt_pltfrm: na
ms.topic: article
ms.assetid: 3fab4d67-8d2a-45ce-8b06-471280102cf6
caps.latest.revision: "11"
caps.handback.revision: "0"
author: mestew
ms.author: mstewart
manager: angrobe
ms.openlocfilehash: 459a619d08a5d38c51301e2f6cff23a5d46a9464
ms.sourcegitcommit: daa080cf220835f157a23e8c8e2bd2781b869bb7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2017
---
# <a name="monitor-hierarchy-and-replication-infrastructure-in-system-center-configuration-manager"></a>Monitorowanie infrastruktury hierarchii i replikacji w programie System Center Configuration Manager

*Dotyczy: Program System Center Configuration Manager (Current Branch)*

Aby monitorować infrastrukturę i operacje w programie System Center Configuration Manager, należy użyć **monitorowanie** obszaru roboczego w konsoli programu Configuration Manager.  

> [!NOTE]  
>  Wyjątkiem od tej lokalizacji jest obszar Migracja, który monitoruje się bezpośrednio w węźle **Migracja** obszaru roboczego **Administracja** . Aby uzyskać więcej informacji, zobacz [Operacje migracji do programu System Center Configuration Manager](../../../core/migration/operations-for-migration.md).  

 Oprócz monitorowania przy użyciu konsoli programu Configuration Manager, możesz użyć raportów programu Configuration Manager lub Wyświetl pliki dziennika programu Configuration Manager składników programu Configuration Manager. Aby uzyskać informacje na temat raportów, zobacz [Raportowanie w programie System Center Configuration Manager](../../../core/servers/manage/reporting.md). Aby uzyskać informacje na temat plików dziennika, zobacz [Pliki dziennika w programie System Center Configuration Manager](../../../core/plan-design/hierarchy/log-files.md).  

 Podczas monitorowania lokacji należy znaleźć oznaki problemów, które wymagają podjęcia odpowiednich akcji. Na przykład:  

-   zaległość plików na serwerach lokacji i w systemach lokacji;  

-   komunikaty o stanie wskazujące błąd lub problem;  

-   nieprawidłowa komunikacja międzylokacyjna;  

-   komunikaty o błędach i komunikaty ostrzegawcze w dzienniku zdarzeń systemowych na serwerach;  

-   komunikaty o błędach i komunikaty ostrzegawcze w dzienniku błędów programu Microsoft SQL Server;  

-   lokacje lub klienci, którzy nie zgłosili się przez długi czas;  

-   wolna odpowiedź z bazy danych programu SQL Server;  

-   oznaki awarii sprzętowej.  

Aby ograniczyć ryzyko awarii lokacji, gdy w ramach zadań monitorowania zostaną wykryte jakiekolwiek oznaki problemów, należy jak najszybciej określić źródło problemu i usunąć go.  



##  <a name="BKMK_MonintorMgmtTasks"></a> Monitorowanie typowych zadań zarządzania programu Configuration Manager  
 Configuration Manager udostępnia wbudowaną funkcję monitorowania z poziomu konsoli programu Configuration Manager. Można monitorować różne zadania, w tym dotyczące aktualizacji oprogramowania, zarządzania energią i wdrażania zawartości w hierarchii.  

 Aby ułatwić sobie monitorowanie typowych zadań programu Configuration Manager, skorzystaj z poniższych informacji:  

 **Alerty**  
   Zobacz [Monitorowanie alertów](../../../core/servers/manage/use-alerts-and-the-status-system.md#BKMK_MonitorAlerts) w temacie [Korzystanie z alertów i systemu stanu w programie System Center Configuration Manager](../../../core/servers/manage/use-alerts-and-the-status-system.md).  

 **Ustawienia zgodności**  
   Zobacz [Jak monitorować ustawienia zgodności w programie System Center Configuration Manager](../../../compliance/deploy-use/monitor-compliance-settings.md).  

 **Wdrożenie zawartości**  
   Aby uzyskać ogólne informacje o monitorowaniu zawartości, zobacz [Zarządzanie zawartością i infrastrukturą zawartości programu System Center Configuration Manager](../../../core/servers/deploy/configure/manage-content-and-content-infrastructure.md).  

Informacje o monitorowaniu określonych typów wdrażania zawartości znajdują się w następujących sekcjach:
-   Aby uzyskać informacje o monitorowaniu aplikacji, zobacz [Monitorowanie aplikacji za pomocą programu System Center Configuration Manager](/sccm/apps/deploy-use/monitor-applications-from-the-console).  

-   Aby monitorować pakiety i programy, zapoznaj się z sekcją Jak zarządzać pakietami i programami w temacie [Pakiety i programy w programie System Center Configuration Manager](../../../apps/deploy-use/packages-and-programs.md).  

**Program Program Endpoint Protection**  
   Zobacz [Jak monitorować program Endpoint Protection w programie System Center Configuration Manager](../../../protect/deploy-use/monitor-endpoint-protection.md).  

**Monitorowanie zarządzania energią**  
 Zobacz [Jak monitorować i planować zarządzanie energią w programie System Center Configuration Manager](../../../core/clients/manage/power/monitor-and-plan-for-power-management.md).  

**Monitorowanie zliczania oprogramowania**  
Zobacz [Monitorowanie użycia aplikacji za pomocą funkcji pomiaru użytkowania oprogramowania w programie System Center Configuration Manager](../../../apps/deploy-use/monitor-app-usage-with-software-metering.md).  

**Monitorowanie aktualizacji oprogramowania**  
 Zobacz [monitorowanie aktualizacji oprogramowania w programie System Center Configuration Manager](../../../sum/deploy-use/monitor-software-updates.md).  


##  <a name="BKMK_MonitorInfrastructure"></a> Monitorowanie infrastruktury hierarchii w programie Configuration Manager  
Configuration Manager udostępnia kilka metod monitorowania stanu oraz operacji w hierarchii. Istnieje możliwość sprawdzenia stanu systemu lokacji w całej hierarchii, monitorowania replikacji międzylokacyjnej z poziomu hierarchii lokacji lub widoku geograficznego, monitorowania linków replikacji bazy danych między lokacjami oraz korygowania problemów dotyczących replikacji przy użyciu narzędzia Analizator linków replikacji.  

###  <a name="BKMK_SH_Node"></a> Informacje o węźle Hierarchia lokacji  
**Hierarchia lokacji** węzła **monitorowanie** obszar roboczy zawiera omówienie programu Menedżera konfiguracji hierarchii i łączy międzylokacyjnych. Dostępne są dwa widoki:  

-   **Diagram hierarchii**: Ten widok przedstawia hierarchię jako mapę topologii uproszczoną tak, aby pokazywała tylko najważniejsze informacje.  

-   **Widok geograficzny**: Wyświetla lokacje na mapie geograficznej, przedstawiając konfigurowane lokalizacje lokacji.  

W węźle **Hierarchia lokacji** można monitorować kondycję poszczególnych lokacji oraz linki replikacji międzylokacyjnej i ich związek z czynnikami zewnętrznymi, na przykład z lokalizacją geograficzną.  

Ponieważ stan lokacji i między lokacjami należy połączyć stan replikacji jako dane lokacji, a nie danych globalnych, podczas łączenia z konsolą programu Configuration Manager z podrzędnej lokacji głównej, nie można wyświetlić stanu lokacji ani łącza do innych lokacji głównych lub do nich podrzędnych lokacji dodatkowych. Na przykład w hierarchii wielu lokacji głównych, gdy konsola programu Configuration Manager łączy się z lokacją główną, można wyświetlić stan podrzędnych lokacji dodatkowych, lokacji głównej i centralnej lokacji administracyjnej, ale nie można wyświetlić stan innych węzłów hierarchii należących do centralnej lokacji administracyjnej.  

 Aby kontrolować sposób wyświetlania obiektów renderowania przez hierarchię lokacji, użyj polecenia **Skonfiguruj ustawienia** . Konfiguracje **hierarchia lokacji** węzła wprowadzone po podłączeniu konsoli programu Configuration Manager do jednej lokacji są replikowane do innych lokacji.  

#### <a name="hierarchy-diagram"></a>Diagram hierarchii  
 Lokacje są wyświetlane na diagramie hierarchicznym w formie mapy topologii. W tym widoku można wybrać lokację i wyświetlić jej podsumowanie komunikatów o stanie, przechodzić do szczegółów w celu wyświetlenia komunikatów o stanie i otworzyć okno dialogowe **Właściwości** poszczególnych lokacji.  

 Ponadto można Zatrzymaj wskaźnik myszy w lokacji lub łącza replikacji między lokacjami, aby wyświetlić stan wysokiego poziomu dla danego obiektu. Stan łącza replikacji nie jest replikowany globalnie, w hierarchii z wieloma lokacjami głównymi należy połączyć konsoli programu Configuration Manager do witryny Administracja centralna w celu wyświetlenia szczegółów łączy replikacji między wszystkimi lokacjami.  

 Diagram hierarchiczny można modyfikować przy użyciu następujących opcji:  

-   **Grupy**: Można skonfigurować liczbę lokacji głównych i dodatkowych wyzwalających zmianę sposobu wyświetlania diagramu hierarchicznego polegającą na łączeniu lokacji w jeden obiekt. Gdy lokacje są połączone w jeden obiekt, zobacz całkowita liczba lokacji oraz zestawienie wysokiego poziomu komunikatów o stanie i stanu lokacji. Konfiguracje grup nie wpływają na widok geograficzny.  

-   **Ulubione Lokacje**: Umożliwia określenie poszczególnych lokacji jako ulubionych lokacji. Ulubiona lokacja jest oznaczona na diagramie hierarchicznym ikoną gwiazdki. Ulubione lokacje nie są połączone z innymi lokacjami w przypadku używania grup i są zawsze wyświetlane pojedynczo.  

#### <a name="geographical-view"></a>Widok geograficzny  
 Widok geograficzny wyświetla lokalizacje poszczególnych lokacji na mapie geograficznej. Wyświetlane są tylko lokacje ze skonfigurowaną lokalizacją. Wybranie lokacji w tym widoku powoduje wyświetlenie łączy replikacji z lokacją nadrzędną lub podrzędną. W przeciwieństwie do widoku diagramu hierarchicznego w tym widoku nie można wyświetlać szczegółów dotyczących komunikatu o stanie lokacji lub łącza replikacji.  

> [!NOTE]  
>  Aby użyć widoku geograficznego, komputer Konsola łączy program Configuration Manager wymaga programu Internet Explorer zainstalowany i mieć dostęp do map Bing przy użyciu protokołu HTTP.  

Widok geograficzny można modyfikować przy użyciu poniższych opcji.  

-   **Lokalizacja lokacji**: Można określić lokalizacji geograficznych poszczególnych lokacji. Jako lokalizację można określić ulicę, nazwę miejsca (na przykład nazwę miejscowości) lub współrzędne geograficzne. Aby wybrać na przykład współrzędne geograficzne miejscowości Redmond w stanie Waszyngton, jako lokalizację lokacji należy określić wartość **N 47 40 26,3572 W 122 7 17,4432** . Wartość współrzędnych geograficznych nie musi zawierać symboli stopni, minut i sekund. Configuration Manager używa usługi mapy Bing Wyświetla lokalizację w widoku geograficznym. Pozwala to wyświetlić hierarchię w odniesieniu do lokalizacji geograficznej, a tym samym zapoznać się z regionalnymi problemami, które mogą mieć wpływ na określone lokacje lub replikację międzylokacyjną.  

     Podczas wybierania lokalizacji można wyszukać określoną lokację w hierarchii przy użyciu pola **Lokalizacja** . Po wybraniu lokacji wprowadź w kolumnie **Lokalizacja** nazwę miejscowości lub ulicę. Configuration Manager używa usługi mapy Bing można rozpoznać lokalizacji.  

###  <a name="BKMK_MonitorRepLinksAndStatuss"></a> Monitorowanie linków replikacji bazy danych i stanu replikacji  
 Oprócz szczegółów wysokiego poziomu, które są dostępne w węźle **Hierarchia lokacji** w obszarze roboczym **Monitorowanie** , możesz także monitorować szczegóły replikacji bazy danych, gdy używasz węzła **Replikacja bazy danych** w obszarze roboczym **Monitorowanie** . Z **replikacji bazy danych** można monitorować stan łączy replikacji między lokacjami oraz szczegóły dotyczące inicjalizacji i szczegóły replikacji dla grup replikacji w lokacji, do którego jest podłączony konsoli programu Configuration Manager.  

> [!TIP]  
>  Węzeł **Replikacja bazy danych** jest również dostępny w węźle **Konfiguracja hierarchii** w obszarze roboczym **Administracja** , ale z poziomu tej lokalizacji nie można zobaczyć stanu replikacji w ramach linków replikacji bazy danych.  

####  <a name="BKMK_MonitorReplicationLinks"></a> Stan linku replikacji  
Replikacja bazy danych między lokacjami obejmuje kilka zestawów informacji nazywanych grupami replikacji. Replikacja każdej z tych grup odbywa się przy użyciu różnych priorytetów replikacji. Domyślnie nie można modyfikować danych zawartych w grupie replikacji ani częstotliwości replikacji.  

 Gdy łącze replikacji jest aktywne i nie jest w stanie wskazującym uszkodzenie lub nieprawidłowe działanie, replikacja wszystkich grup odbywa się w ustalonym czasie. Jeżeli replikacja w co najmniej jednej grupie replikacji nie powiedzie się w oczekiwanym czasie, zostanie wskazany stan nieprawidłowego działania łącza. Takie linki mogą nadal działać, ale należy je monitorować w celu sprawdzenia, czy powróciły do aktywnego stanu, lub zbadać je, aby mieć pewność, że nieprawidłowe działanie ani błędy replikacji nie wystąpią ponownie.  

 Dla każdego linku replikacji i danej grupy replikacji możesz określić liczbę ponownych prób replikacji zakończonych niepowodzeniem, po osiągnięciu której dla linku zostanie ustawiony stan obniżonej sprawności lub uszkodzenia. Stan nieprawidłowego działania lub uszkodzenia linku zostanie wskazany nawet w przypadku, gdy replikacja zakończy się powodzeniem we wszystkich grupach z wyjątkiem jednej, która nie może przeprowadzić replikacji w ramach określonej liczby prób. Informacje o progach replikacji znajdują się w sekcji [Progi replikacji bazy danych](../../../core/servers/manage/data-transfers-between-sites.md#BKMK_DBRepThresholds) w temacie [Transfer danych między lokacjami w programie System Center Configuration Manager](../../../core/servers/manage/data-transfers-between-sites.md).  

 Aby poznać stany linków replikacji wskazujące konieczność przeprowadzenia dalszych badań, zapoznaj się z informacjami w poniższej tabeli.  

|Opis łącza|Więcej informacji|  
|----------------------|----------------------|  
|**Łącze jest aktywne**|Nie wykryto żadnych problemów i komunikacja za pośrednictwem łącza odbywa się prawidłowo.|  
|**Łącze działa nieprawidłowo**|Replikacja działa, ale w co najmniej jednym obiekcie lub grupie replikacja jest opóźniona. Łącza w tym stanie należy monitorować i zapoznać się z informacjami z obu lokacji objętych danych łączem, które mogą wskazywać jego uszkodzenie.<br /><br /> Nieprawidłowe działanie łącza może również zostać wskazane, gdy lokacja odbierająca replikowane dane nie może szybko przekazać ich do bazy danych. Taka sytuacja może wystąpić w przypadku replikacji dużych ilości danych. Na przykład podczas wdrażania aktualizacji oprogramowania na dużej liczbie komputerów przetworzenie replikowanych danych przez lokację nadrzędną objętą łączem może zająć dużo czasu. Zwłoka podczas przetwarzania w lokacji nadrzędnej może spowodować wskazywanie stanu nieprawidłowego działania łącza dopóki lokacja nadrzędna nie przetworzy pomyślnie zaległych danych.|  
|**Łącze jest uszkodzone**|Replikacja nie działa. Istnieje prawdopodobieństwo, że łącze replikacji odzyska sprawność bez podejmowania dalszych akcji. Łącze można zbadać i skorygować odbywającą się za jego pośrednictwem replikację przy użyciu Analizatora łącza replikacji.<br /><br /> Ten stan może również oznaczać problem związany z siecią fizyczną między lokacjami nadrzędną i podrzędną w ramach łącza replikacji.|  

 Podczas uaktualniania lokacji nadrzędnej do nowej wersji dodatku Service Pack stan łącza lokacji podrzędnej będzie wskazywany jako aktywny. Jeżeli po uaktualnieniu lokacja podrzędna ma taką samą wersję dodatku Service Pack jak lokacja nadrzędna, z poziomu lokacji nadrzędnej jest wskazywany stan aktywny linku, a z poziomu lokacji podrzędnej — stan trwającej konfiguracji.  

####  <a name="BKMK_MonitorReplicationStatus"></a> Stan replikacji  
 W węźle **Replikacja bazy danych** w obszarze roboczym **Monitorowanie** można wyświetlić stan replikacji za pośrednictwem linku oraz szczegóły dotyczące bazy danych w każdej lokacji objętej linkiem replikacji. Istnieje również możliwość wyświetlania szczegółów dotyczących grup replikacji. Aby wyświetlić szczegóły, wybierz łącze replikacji, a następnie otwórz kartę zawierającą odpowiedni stan replikacji. Poniżej przedstawiono szczegółowe informacje o różnych kartach zawierających stan replikacji.  

 **Podsumowanie**  
 Umożliwia wyświetlenie informacji wysokiego poziomu dotyczących replikacji danych lokacji oraz danych globalnych między dwiema lokacjami objętymi łączem.  

 Ponadto aby wyświetlić raport zawierający szczegółowe informacje o przepustowości sieci używanej w ramach replikacji za pośrednictwem linku, można kliknąć pozycję **Wyświetl raporty z historycznymi danymi o ruchu** .  

 **Lokacja nadrzędna**  
 W ramach lokacji nadrzędnej objętej łączem replikacji umożliwia wyświetlenie szczegółowych informacji o bazie danych, takich jak następujące:  

-   Porty zapory programu SQL Server  

-   Wolne miejsce na dysku  

-   Lokalizacje plików bazy danych  

-   Certyfikaty  

**Lokacja podrzędna**  
 W ramach lokacji podrzędnej objętej łączem replikacji umożliwia wyświetlenie szczegółowych informacji o bazie danych, takich jak następujące:  

-   Porty zapory programu SQL Server  

-   Wolne miejsce na dysku  

-   Lokalizacje plików bazy danych  

-   Certyfikaty  

**Szczegóły inicjalizacj**    
 Umożliwia wyświetlenie stanu inicjalizacji grup replikowanych za pośrednictwem łącza replikacji. Te informacje pozwalają ustalić, czy inicjalizacja danych replikacji jest w toku czy zakończyła się niepowodzeniem.  

 Ponadto za pomocą tych informacji można ustalić, kiedy lokacja jest w trybie współdziałania. Tryb współdziałania występuje, gdy w lokacji podrzędnej jest uruchomiona tej samej wersji programu Configuration Manager jako lokacji nadrzędnej.  

**Szczegóły replikacji**    
 Umożliwia wyświetlenie stanu replikacji każdej grupy replikacji, które wykonuje replikację za pośrednictwem łącza. Te informacje ułatwiają identyfikację problemów lub opóźnień replikacji określonych danych i określenie odpowiednich progów replikacji bazy danych dla tego linku. Informacje o progach replikacji bazy danych znajdują się w sekcji [Progi replikacji bazy danych](../../../core/servers/manage/data-transfers-between-sites.md#BKMK_DBRepThresholds) w temacie [Transfer danych między lokacjami w programie System Center Configuration Manager](../../../core/servers/manage/data-transfers-between-sites.md).  

> [!TIP]  
>  Grupy replikacji dla danych lokacji są wysyłane tylko z lokacji podrzędnej do nadrzędnej. Grupy replikacji danych globalnych są replikowane w obu kierunkach.  

###  <a name="BKMK_RLA"></a> Informacje o Analizatorze linków replikacji  
 Configuration Manager zawiera **analizator łącza replikacji** umożliwiający analizę i rozwiązywanie problemów z replikacją. Analizatora linków replikacji można użyć do usuwania błędów związanych z awarią linku replikacji, jeżeli replikacja nie powiodła się lub przestała działać, ale nie zaraportowano jeszcze jej błędu. Analizator łącza replikacji może służyć do rozwiązywania problemów z replikacją między następującymi komputerami w hierarchii programu Configuration Manager (kierunek błędu replikacji nie ma znaczenia):  

-   pomiędzy serwerem lokacji a serwerem bazy danych lokacji,  

-   Między serwerem bazy danych lokacji witryny innej lokacji komputera bazy danych lokacji (replikacja wewnątrz lokacyjna).  

Analizator łącza replikacji można uruchomić w konsoli programu Configuration Manager lub w wierszu polecenia:  

-   Aby uruchamiać w konsoli programu Configuration Manager: W **monitorowanie** obszaru roboczego kliknij **replikacji bazy danych** węzła, wybierz łącze replikacji, które mają być analizowane, a następnie w **replikacji bazy danych** na **Home** wybierz opcję **analizator łącza replikacji**.  

-   Aby uruchomić polecenie w wierszu polecenia, wpisz następujące polecenie: **%path%\Microsoft Configuration Manager\AdminConsole\bin\Microsoft.ConfigurationManager.ReplicationLinkAnalyzer.Wizard.exe &lt;nazwa_fqdn_źródłowego_serwera_lokacji\> &lt;FQDN docelowego serwera lokacji\>**  

Po uruchomieniu Analizator linków replikacji wykrywa problemy, używając szeregu zasad i sprawdzeń diagnostycznych. Podczas pracy narzędzia można wyświetlić zidentyfikowane przez nie problemy. Jeżeli znane są instrukcje rozwiązania problemu, zostaną one wyświetlone. Jeżeli Analizator łącza replikacji może automatycznie rozwiązać problem, zostanie wyświetlona odpowiednia opcja. Po zakończeniu pracy analizator łącza replikacji zapisuje wyniki w następujących raportów opartych na języku XML oraz pliku dziennika na pulpicie użytkownika, który uruchomił narzędzie:  

-   ReplicationAnalysis.xml  

-   ReplicationLinkAnalysis.log  

Podczas pracy Analizator łącza replikacji zatrzymuje następujące usługi w trakcie rozwiązywania problemów i uruchamia je ponownie po ukończeniu rozwiązywania:  

-   SMS_SITE_COMPONENT_MANAGER  

-   SMS_EXECUTIVE  

Jeżeli Analizator łącza replikacji nie ukończy rozwiązywania problemu, należy sprawdzić ustawienia serwera lokacji i ponownie uruchomić te usługi, jeżeli zostały zatrzymane.  

Zakończone powodzeniem i niepowodzeniem akcje sprawdzania i rozwiązywania problemów są rejestrowane, aby umożliwić uzyskanie dodatkowych szczegółowych informacji niedostępnych w interfejsie narzędzia.  

**Wymagania wstępne dotyczące korzystania z Analizatora linków replikacji:**  

-   Konto używane do uruchamiania Analizatora linków replikacji musi mieć prawa administratora lokalnego na każdym komputerze korzystającym z linku replikacji. Konto nie wymaga roli zabezpieczeń administracji opartej na rolach określone. Dlatego użytkownik administracyjny z dostępem do **replikacji bazy danych** węzła, można uruchomić narzędzie w konsoli programu Configuration Manager lub administrator systemu z wystarczającymi prawami do każdego komputera może uruchomić narzędzie z wiersza polecenia.  

-   Konto używane do uruchamiania Analizatora linków replikacji musi mieć prawa sysadmin w każdej bazie danych programu SQL Server korzystającej z linku replikacji.  

**Znane problemy dotyczące Analizatora linków replikacji:**  

-   Wraz z wydaniem programu System Center Configuration Manager w wersji 1511 analizator łącza replikacji generuje błędy certyfikatu brokera usług serwera SQL dla lokacji głównych uaktualnionych z programu System Center 2012 Configuration Manager. Jest to spowodowane zmianami w nazwach certyfikatów wprowadzonymi w wersji 1511, dla której analizator łącza replikacji nie został jeszcze zaktualizowany. Te błędy można zignorować.  

###  <a name="BKMK_ProcsforMonitoringReplication"></a> Procedury monitorowania replikacji bazy danych  

##### <a name="to-monitor-high-level-site-to-site-database-replication-status"></a>Aby monitorować stan replikacji wysokiego poziomu bazy danych lokacji do lokacji    
1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W obszarze roboczym **Monitorowanie** kliknij element **Hierarchia lokacji** , aby otworzyć widok **Diagram hierarchii** .  

3.  Umieść na krótko wskaźnik myszy na linii między dwiema lokacjami, aby wyświetlić stan globalnej i dotyczącej lokacji replikacji danych między tymi lokacjami.  

##### <a name="to-monitor-the-replication-status-for-a-replication-link"></a>Aby monitorować stan replikacji dla łącza replikacji    
1.  W konsoli programu Configuration Manager kliknij **monitorowanie**.  

2.  W obszarze roboczym **Monitorowanie** kliknij element **Replikacja bazy danych**, a następnie wybierz link replikacji dla monitorowanego linku. Następnie wybierz w obszarze roboczym odpowiednią kartę, aby wyświetlić różne szczegóły dotyczące stanu replikacji dla tego linku.  
